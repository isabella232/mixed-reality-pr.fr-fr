---
title: Écriture d’un lecteur de communication à distance holographique personnalisé (C++)
description: Créez une application de communication à distance hologaphic personnalisée pour afficher le contenu rendu sur une machine distante à votre HoloLens 2.
author: florianbagarmicrosoft
ms.author: v-vtieto
ms.date: 7/30/2021
ms.topic: article
keywords: HoloLens, communication à distance, accès distant holographique, NuGet, manifeste de l’application, contexte du lecteur, application distante, casque de la réalité mixte, casque windows mixed realisation, casque de la réalité virtuelle
ms.openlocfilehash: 37388dc9cbf70cb7fccd742fb45e1e29c0ceb971
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184730"
---
# <a name="writing-a-custom-holographic-remoting-player-app-c"></a>Écriture d’une application de lecteur de communication à distance holographique personnalisée (C++)

>[!IMPORTANT]
>Ce document décrit la création d’une application de lecteur personnalisée pour HoloLens 2. les lecteurs personnalisés écrits pour HoloLens 2 ne sont pas compatibles avec les applications distantes écrites pour HoloLens 1. cela implique que les deux applications doivent utiliser NuGet package version **2. x. x**.

En créant une application de lecteur de communication à distance holographique personnalisée, vous pouvez créer une application personnalisée capable d’afficher des [vues immersives](../../design/app-views.md) à partir d’un ordinateur distant sur votre HoloLens 2. Tout le code de cette page et des projets de travail se trouve dans le [référentiel GitHub d’exemples de communication à distance holographique](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

un lecteur de communication à distance holographique permet à votre application d’afficher le contenu holographique [rendu](rendering.md) sur un PC de bureau ou un appareil UWP, comme le Xbox One avec un accès à plus de ressources système. Une application de lecteur de communication à distance holographique diffuse des données d’entrée vers une application distante de communication à distance holographique et reçoit un affichage immersif en tant que flux vidéo et audio. La connexion est établie à l’aide du Wi-Fi standard. pour créer une application de lecteur, utilisez un package NuGet pour ajouter la communication à distance holographique à votre application UWP. Écrivez ensuite le code pour gérer la connexion et afficher une vue immersive. 

## <a name="prerequisites"></a>Prérequis

un bon point de départ est une application UWP DirectX fonctionnelle qui cible déjà l’API Windows Mixed Reality. Pour plus d’informations, consultez [vue d’ensemble du développement DirectX](../native/directx-development-overview.md). Si vous ne disposez pas d’une application existante et que vous souhaitez commencer à partir de zéro, le [modèle de projet holographique C++](../native/creating-a-holographic-directx-project.md) est un bon point de départ.

>[!IMPORTANT]
>Toute application utilisant la communication à distance holographique doit être créée pour utiliser un [cloisonnement](/windows/win32/com/multithreaded-apartments)multithread. L’utilisation d’un [cloisonnement à thread unique](/windows/win32/com/single-threaded-apartments) est prise en charge, mais entraîne des performances non optimales et éventuellement des interruptions pendant la lecture. Lors de l’utilisation de C++/WinRT [WinRT :: init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) un cloisonnement multithread est la valeur par défaut.

## <a name="get-the-holographic-remoting-nuget-package"></a>procurez-vous le package NuGet de communication à distance holographique

les étapes suivantes sont requises pour ajouter le package NuGet à un projet dans Visual Studio.
1. Ouvrez le projet dans Visual Studio.
2. cliquez avec le bouton droit sur le nœud du projet et sélectionnez **gérer les Packages NuGet...**
3. Dans le volet qui s’affiche, sélectionnez **Parcourir** , puis recherchez « accès à distance holographique ».
4. Sélectionnez **Microsoft. holographique. Remoting**, assurez-vous de choisir la version la plus récente de **2. x. x** , puis sélectionnez **installer**.
5. Si la boîte de dialogue **Aperçu** s’affiche, sélectionnez **OK**.
6. Sélectionnez **J’accepte** lorsque la boîte de dialogue contrat de licence s’affiche.

>[!IMPORTANT]
><a name="idl"></a>l' ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` intérieur du package NuGet contient une documentation détaillée sur l’API exposée par la communication à distance holographique.

## <a name="modify-the-packageappxmanifest-of-the-application"></a>Modifier le package. appxmanifest de l’application

pour que l’application prenne en charge l' Microsoft.Holographic.AppRemoting.dll ajoutée par le package NuGet, les étapes suivantes doivent être effectuées sur le projet :

1. Dans le Explorateur de solutions cliquez avec le bouton droit sur le fichier **Package. appxmanifest** , puis sélectionnez **Ouvrir avec...**
2. Sélectionnez **éditeur XML (texte)** , puis cliquez sur **OK**
3. Ajoutez les lignes suivantes au fichier et enregistrez
```xml
  </Capabilities>

  <!--Add lines below -->
  <Extensions>
    <Extension Category="windows.activatableClass.inProcessServer">
      <InProcessServer>
        <Path>Microsoft.Holographic.AppRemoting.dll</Path>
        <ActivatableClass ActivatableClassId="Microsoft.Holographic.AppRemoting.PlayerContext" ThreadingModel="both" />
      </InProcessServer>
    </Extension>
  </Extensions>
  <!--Add lines above -->

</Package>
```
## <a name="create-the-player-context"></a>Créer le contexte du joueur

En guise de première étape, l’application doit créer un contexte de joueur.

```cpp
// class declaration:

#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
// PlayerContext used to connect with a Holographic Remoting remote app and display remotely rendered frames
winrt::Microsoft::Holographic::AppRemoting::PlayerContext m_playerContext = nullptr;
```


```cpp
// class implementation:

// Create the player context
// IMPORTANT: This must be done before creating the HolographicSpace (or any other call to the Holographic API).
m_playerContext = winrt::Microsoft::Holographic::AppRemoting::PlayerContext::Create();

```

>[!WARNING]
>la communication à distance holographique fonctionne en remplaçant le runtime Windows Mixed Reality qui fait partie de Windows avec un runtime spécifique à distance. Cette opération est effectuée lors de la création du contexte du joueur. pour cette raison, tout appel sur une API de Windows Mixed Reality avant de créer le contexte du joueur peut entraîner un comportement inattendu. L’approche recommandée consiste à créer le contexte du joueur le plus tôt possible avant d’interagir avec une API de réalité mixte. ne combinez jamais des objets créés ou récupérés par le biais d’une API Windows Mixed Reality avant l’appel à ```PlayerContext::Create``` avec des objets créés ou récupérés par la suite.

Ensuite, vous pouvez créer le HolographicSpace en appelant [HolographicSpace. CreateForCoreWindow](/uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-remote-app"></a>Connecter à l’application distante

Une fois que l’application de lecteur est prête pour le rendu du contenu, une connexion à l’application distante peut être établie.

La connexion peut être établie de l’une des manières suivantes :
1) l’application de lecteur s’exécutant sur HoloLens 2 se connecte à l’application distante.
2) L’application distante se connecte à l’application du lecteur s’exécutant sur HoloLens 2.

Pour vous connecter à partir de l’application du lecteur à l’application distante, appelez la ```Connect``` méthode sur le contexte du lecteur en spécifiant le nom d’hôte et le port. Le port par défaut est **8265**.

```cpp
try
{
    m_playerContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    // Failed to connect. Get an error details via e.code() and e.message()
}
```

>[!IMPORTANT]
>Comme pour toute API/WinRT C++ ```Connect``` peut lever une exception WinRT :: hresult_error qui doit être gérée.

L’écoute des connexions entrantes sur l’application de lecteur peut être effectuée en appelant la ```Listen``` méthode. Le port de liaison et le port de transport peuvent être spécifiés au cours de cet appel. Le port de négociation est utilisé pour le protocole de transfert initial. Les données sont ensuite envoyées sur le port de transport. Les numéros de port **8265** et **8266** sont utilisés par défaut.

```cpp
try
{
    m_playerContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    // Failed to listen. Get an error details via e.code() and e.message()
}
```


## <a name="handling-connection-related-events"></a>Gestion des événements liés à la connexion

Le ```PlayerContext``` expose trois événements pour surveiller l’état de la connexion.
1) OnConnected : déclenché lorsqu’une connexion à l’application distante a été établie avec succès.
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) OnDisconnected : déclenché si une connexion établie est terminée ou si une connexion n’a pas pu être établie.
```cpp
m_onDisconnectedEventToken = m_playerContext.OnDisconnected([](ConnectionFailureReason failureReason)
{
    switch (failureReason)
    {
        // Handle connection failed or terminated.
        // See ConnectionFailureReason for possible reasons.
    }
}
```
>[!NOTE]
>```ConnectionFailureReason```Les valeurs possibles sont documentées dans le ```Microsoft.Holographic.AppRemoting.idl``` [fichier](#idl).

3) OnListening : lors du démarrage de l’écoute des connexions entrantes.
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

En outre, l’état de la connexion peut être interrogé à l’aide de la ```ConnectionState``` propriété du contexte du lecteur.
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a>Afficher le frame rendu à distance

Pour afficher le contenu rendu à distance, appelez ```PlayerContext::BlitRemoteFrame``` lors du rendu d’un [HolographicFrame](/uwp/api/windows.graphics.holographic.holographicframe). 

```BlitRemoteFrame``` requiert que la mémoire tampon d’arrière-plan pour le HolographicFrame actuel soit liée en tant que cible de rendu. La mémoire tampon d’arrière-plan peut être reçue à partir du [HolographicCameraRenderingParameters](/uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) via la propriété [Direct3D11BackBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) .

En cas d’appel, ```BlitRemoteFrame``` copie la dernière trame reçue de l’application distante dans la mémoire tampon de la mémoire tampon de HolographicFrame. En outre, l’ensemble de points de focalisation est défini, si l’application distante a spécifié un point de focus pendant le rendu du frame distant.

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
>```PlayerContext::BlitRemoteFrame``` remplace potentiellement le point de focus du frame actuel. 
>- Pour spécifier un point de focus de secours, appelez [HolographicCameraRenderingParameters :: SetFocusPoint](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) avant ```PlayerContext::BlitRemoteFrame``` . 
>- Pour remplacer le point de focus distant, appelez [HolographicCameraRenderingParameters :: SetFocusPoint](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)  après ```PlayerContext::BlitRemoteFrame``` .

En cas de réussite, ```BlitRemoteFrame``` retourne ```BlitResult::Success_Color``` . Dans le cas contraire, elle retourne la raison de l’échec :
- ```BlitResult::Failed_NoRemoteFrameAvailable```: Échec, car aucun frame distant n’est disponible.
- ```BlitResult::Failed_NoCamera```: Échec, car aucun appareil photo n’est présent.
- ```BlitResult::Failed_RemoteFrameTooOld```: Échec, car le frame distant est trop ancien (consultez la propriété PlayerContext :: BlitRemoteFrameTimeout).

>[!IMPORTANT]
> À partir de la version [2.1.0](holographic-remoting-version-history.md#v2.1.0) , un joueur personnalisé peut utiliser la reprojection de profondeur via la communication à distance holographique.

```BlitResult``` peut également retourner ```BlitResult::Success_Color_Depth``` dans les conditions suivantes :

- L’application distante a validé un tampon de profondeur par le biais de [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).
- L’application de joueur personnalisée a lié une mémoire tampon de profondeur valide avant d’appeler ```BlitRemoteFrame``` .

Si ces conditions sont remplies ```BlitRemoteFrame``` , blit la profondeur à distance dans la mémoire tampon de profondeur locale actuellement liée. Vous pouvez ensuite restituer du contenu local supplémentaire, qui aura une intersection de profondeur avec le contenu rendu distant. En outre, vous pouvez valider le tampon de profondeur local à l’aide de [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) dans votre lecteur personnalisé pour effectuer une reprojection de profondeur pour le contenu rendu local et distant. Pour plus d’informations, consultez [reprojection de profondeur](hologram-stability.md#reprojection) .

### <a name="projection-transform-mode"></a>Mode de transformation de projection

L’un des problèmes, qui s’affiche lors de l’utilisation de la reprojection de profondeur via la communication à distance holographique, est que le contenu distant peut être rendu avec une transformation de projection différente de celle du contenu local affiché directement par votre application de lecteur personnalisée. Un cas d’usage courant consiste à spécifier des valeurs différentes pour le plan near et Far (via [HolographicCamera :: SetNearPlaneDistance](/uwp/api/windows.graphics.holographic.holographiccamera.setnearplanedistance) et [HolographicCamera :: SetFarPlaneDistance](/uwp/api/windows.graphics.holographic.holographiccamera.setfarplanedistance)) du côté joueur et du côté distant. Dans ce cas, il n’est pas évident que la transformation de projection côté joueur doit refléter les distances à distance de plan proche/lointain ou celles locales.

À partir de la version [2.1.0](holographic-remoting-version-history.md#v2.1.0) , vous pouvez contrôler le mode de transformation de projection via ```PlayerContext::ProjectionTransformConfig``` . Les valeurs prises en charge sont les suivantes :

- ```Local``` - [HolographicCameraPose ::P rojectiontransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.projectiontransform) retourne une transformation de projection, qui reflète les distances du plan proche/Far définies par votre application de lecteur personnalisée sur le HolographicCamera.
- ```Remote``` -La transformation de projection reflète les distances de plan proches/éloignées spécifiées par l’application distante.
- ```Merged``` -Les distances proches/éloignées de votre application distante et de votre application de lecteur personnalisé sont fusionnées. Par défaut, cette opération s’effectue en tenant au minimum les distances proches du plan et le maximum des distances du plan lointain. Si le côté distant ou local est inversé, disons < près, les distances à proximité du plan distant sont retournées.

## <a name="optional-set-blitremoteframetimeout"></a>Facultatif : Set BlitRemoteFrameTimeout <a name="BlitRemoteFrameTimeout"></a>
>[!IMPORTANT]
> ```PlayerContext::BlitRemoteFrameTimeout``` est pris en charge à partir de la version [2.0.9](holographic-remoting-version-history.md#v2.0.9). 

La ```PlayerContext::BlitRemoteFrameTimeout``` propriété spécifie la durée pendant laquelle un frame distant est réutilisé si aucune nouvelle trame distante n’est reçue. 

Un cas d’usage courant consiste à permettre au délai d’attente de BlitRemoteFrame d’afficher un écran vide si aucun nouveau Frame n’est reçu pendant un certain laps de temps. Quand cette option est activée, le type de retour de la ```BlitRemoteFrame``` méthode peut également être utilisé pour basculer vers un contenu de secours rendu localement. 

Pour activer le délai d’expiration, définissez la valeur de la propriété sur une durée égale ou supérieure à 100 ms. Pour désactiver le délai d’attente, affectez la valeur zéro à la propriété. Si le délai d’expiration est activé et qu’aucun frame distant n’est reçu pour la durée définie, BlitRemoteFrame échoue et retourne ```Failed_RemoteFrameTooOld``` jusqu’à la réception d’une nouvelle trame distante.

```cpp
using namespace std::chrono_literals;

// Set the BlitRemoteFrame timeout to 0.5s
m_playerContext.BlitRemoteFrameTimeout(500ms);
```

## <a name="optional-get-statistics-about-the-last-remote-frame"></a>Facultatif : obtenir des statistiques sur le dernier frame distant

Pour diagnostiquer les problèmes de performances ou de réseau, les statistiques relatives au dernier frame distant peuvent être récupérées via la ```PlayerContext::LastFrameStatistics``` propriété. Les statistiques sont mises à jour lors de l’appel à [HolographicFrame ::P resentusingcurrentprediction](/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

Pour plus d’informations, consultez la ```PlayerFrameStatistics``` documentation du ```Microsoft.Holographic.AppRemoting.idl``` [fichier](#idl).

## <a name="optional-custom-data-channels"></a>Facultatif : canaux de données personnalisés

Les canaux de données personnalisés peuvent être utilisés pour envoyer des données utilisateur sur la connexion de communication à distance déjà établie. Pour plus d’informations, consultez [canaux de données personnalisés](holographic-remoting-custom-data-channels.md) .

## <a name="see-also"></a>Voir aussi
* [Vue d’ensemble de la communication à distance holographique](holographic-remoting-overview.md)
* [écriture d’une application distante de communication à distance holographique à l’aide d’api Windows Mixed Reality](holographic-remoting-create-remote-wmr.md)
* [Écriture d’une application distante de communication à distance holographique à l’aide d’API OpenXR](holographic-remoting-create-remote-openxr.md)
* [Canaux de données de communication à distance holographique personnalisés](holographic-remoting-custom-data-channels.md)
* [Établissement d’une connexion sécurisée avec la communication à distance holographique](holographic-remoting-secure-connection.md)
* [Résolution des problèmes et limitations de la communication à distance holographique](holographic-remoting-troubleshooting.md)
* [Termes du contrat de licence de la communication à distance holographique](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Déclaration de confidentialité Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)