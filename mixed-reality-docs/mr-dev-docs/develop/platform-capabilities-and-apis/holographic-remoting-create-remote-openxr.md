---
title: Écriture d’une application distante holographique de communication à distance (OpenXR)
description: découvrez comment diffuser du contenu distant rendu sur une machine distante pour HoloLens 2 avec des applications de communication à distance holographique avec OpenXR.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, remoting, accès distant holographique, casque de réalité mixte, casque windows mixed realisation, casque de réalité virtuelle, NuGet
ms.openlocfilehash: 6cf44bd031aec4b475d7496a999a3c7d4d40cae7cc921ff39cfe61698f3dd532
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212067"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-openxr-api"></a>Écriture d’une application distante holographique à distance à l’aide de l’API OpenXR

>[!IMPORTANT]
>ce document décrit la création d’une application distante pour HoloLens 2 et Windows Mixed Reality des casques à l’aide de l' [API OpenXR](../native/openxr.md). les applications distantes pour **HoloLens (1re génération)** doivent utiliser NuGet package version **1. x. x**. cela implique que les applications distantes écrites pour HoloLens 2 ne sont pas compatibles avec HoloLens 1 et vice versa. vous trouverez la documentation relative à HoloLens 1 [ici](add-holographic-remoting.md).

les applications de communication à distance holographique peuvent diffuser du contenu à distance à HoloLens 2 et Windows Mixed Reality des casques immersifs. Vous pouvez également accéder à davantage de ressources système et intégrer des [vues immersives](../../design/app-views.md) distantes dans des logiciels de poste de travail existants. une application distante reçoit un flux de données d’entrée de HoloLens 2, restitue le contenu dans une vue immersive virtuelle et diffuse les trames de contenu à HoloLens 2. La connexion est établie à l’aide du Wi-Fi standard. la communication à distance holographique est ajoutée à une application de bureau ou UWP via un paquet NuGet. Du code supplémentaire est nécessaire pour gérer la connexion et le rendu dans une vue immersive. Une connexion à distance classique aura une latence aussi faible que 50 ms de latence. L’application de lecteur peut signaler la latence en temps réel.

Tout le code de cette page et des projets de travail se trouve dans le [référentiel GitHub d’exemples de communication à distance holographique](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

## <a name="prerequisites"></a>Prérequis

Un bon point de départ est une application de bureau ou UWP basée sur un OpenXR fonctionnel. Pour plus d’informations, consultez [prise en main de OpenXR](../native/openxr-getting-started.md).

>[!IMPORTANT]
>Toute application utilisant la communication à distance holographique doit être créée pour utiliser un [cloisonnement](/windows/win32/com/multithreaded-apartments)multithread. L’utilisation d’un [cloisonnement à thread unique](/windows/win32/com/single-threaded-apartments) est prise en charge, mais entraîne des performances non optimales et éventuellement des interruptions pendant la lecture. Lors de l’utilisation de C++/WinRT [WinRT :: init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) un cloisonnement multithread est la valeur par défaut.

## <a name="get-the-holographic-remoting-nuget-package"></a>procurez-vous le package NuGet de communication à distance holographique

les étapes suivantes sont requises pour ajouter le package NuGet à un projet dans Visual Studio.
1. Ouvrez le projet dans Visual Studio.
2. cliquez avec le bouton droit sur le nœud du projet et sélectionnez **gérer les Packages NuGet...**
3. Dans le volet qui s’affiche, sélectionnez **Parcourir** , puis recherchez « accès à distance holographique ».
4. Sélectionnez **Microsoft. holographique. Remoting. OpenXr**, assurez-vous de choisir la version la plus récente de **2. x. x** , puis sélectionnez **installer**.
5. Si la boîte de dialogue **Aperçu** s’affiche, sélectionnez **OK**.
6. Sélectionnez **J’accepte** quand la boîte de dialogue du contrat de licence s’affiche.
7. répétez les étapes 3 à 6 pour les Packages NuGet suivants : OpenXR. headers, OpenXR. loader

>[!NOTE]
>la Version **1. x. x** du package NuGet est toujours disponible pour les développeurs qui souhaitent cibler HoloLens 1. pour plus d’informations [, consultez ajouter une communication à distance holographique (HoloLens (1er génération))](add-holographic-remoting.md).

## <a name="select-the-holographic-remoting-openxr-runtime"></a>Sélectionner le runtime OpenXR Remoting holographique

la première étape que vous devez effectuer dans votre application distante consiste à sélectionner le runtime OpenXR de communication à distance holographique, qui fait partie du package Microsoft. holographique. remoting. OpenXR NuGet. Pour ce faire, vous pouvez définir la ```XR_RUNTIME_JSON``` variable d’environnement sur le chemin d’accès de l' RemotingXR.jssur le fichier dans votre application. Cette variable d’environnement est utilisée par le chargeur OpenXR pour ne pas utiliser le runtime OpenXR par défaut du système, mais plutôt rediriger vers le runtime OpenXR de communication à distance holographique. lors de l’utilisation du package de NuGet Microsoft. holographique. remoting. OpenXr, le RemotingXR.jsfichier est automatiquement copié pendant la compilation dans le dossier de sortie. la sélection du runtime OpenXr se présente généralement comme suit.

```cpp
bool EnableRemotingXR() {
    wchar_t executablePath[MAX_PATH];
    if (GetModuleFileNameW(NULL, executablePath, ARRAYSIZE(executablePath)) == 0) {
        return false;
    }
    
    std::filesystem::path filename(executablePath);
    filename = filename.replace_filename("RemotingXR.json");

    if (std::filesystem::exists(filename)) {
        SetEnvironmentVariableW(L"XR_RUNTIME_JSON", filename.c_str());
            return true;
        }

    return false;
}
```

## <a name="create-xrinstance-with-holographic-remoting-extension"></a>Créer XrInstance avec l’extension de communication à distance holographique

La première étape d’une application OpenXR classique est de sélectionner les extensions OpenXR et de créer un XrInstance. La spécification OpenXR Core ne fournit pas d’API spécifique à distance. Pour cette raison, la communication à distance holographique introduit sa propre extension OpenXR nommée ```XR_MSFT_holographic_remoting``` . Assurez-vous que lorsque vous appelez xrCreateInstance ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` , est inclus dans le XrInstanceCreateInfo.

>[!TIP]
>par défaut, le contenu rendu de votre application est diffusé uniquement sur le lecteur de communication à distance holographique s’exécutant sur un HoloLens 2 ou sur un Windows Mixed Reality casques. Pour afficher également le contenu rendu sur l’ordinateur distant, par le biais d’une chaîne d’échange d’une fenêtre, par exemple, la communication à distance holographique fournit une deuxième extension OpenXR nommée ```XR_MSFT_holographic_remoting_frame_mirroring``` . Veillez également à activer cette extension ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME``` au cas où vous souhaiteriez utiliser cette fonctionnalité.

>[!IMPORTANT]
>Pour en savoir plus sur l’API d’extension OpenXR de communication à distance holographique, consultez la [spécification](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) qui se trouve dans le [référentiel GitHub des exemples de communication à distance holographique](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

## <a name="connect-to-the-device"></a>Connecter à l’appareil

Une fois que votre application distante a créé les XrInstance et interrogé les XrSystemId via xrGetSystem, une connexion à l’appareil Player peut être établie.

>[!WARNING]
> Le runtime OpenXR de communication à distance holographique est uniquement en mesure de fournir des données spécifiques à l’appareil, telles que des configurations d’affichage ou des modes de fusion d’environnement, après l’établissement d’une connexion. ```xrEnumerateViewConfigurations```, ```xrEnumerateViewConfigurationViews``` , ```xrGetViewConfigurationProperties``` , ```xrEnumerateEnvironmentBlendModes``` et ```xrGetSystemProperties``` fournissent les valeurs par défaut, en fonction de ce que vous obtiendriez en général si vous vous connectez à un joueur s’exécutant sur un HoloLens 2, avant d’être entièrement connecté.
Il est fortement recommandé de ne pas appeler ces méthodes avant qu’une connexion ait été établie. La suggestion est utilisée par ces méthodes une fois que le XrSession a été créé avec succès et que l’état de session est au moins XR_SESSION_STATE_READY.

Les propriétés générales telles que le débit maximal, l’audio activé, le codec vidéo ou la résolution de flux de mémoire tampon de profondeur peuvent être configurées via ```xrRemotingSetContextPropertiesMSFT``` comme suit.

```cpp
XrRemotingRemoteContextPropertiesMSFT contextProperties;
contextProperties = XrRemotingRemoteContextPropertiesMSFT{static_cast<XrStructureType>(XR_TYPE_REMOTING_REMOTE_CONTEXT_PROPERTIES_MSFT)};
contextProperties.enableAudio = false;
contextProperties.maxBitrateKbps = 20000;
contextProperties.videoCodec = XR_REMOTING_VIDEO_CODEC_H265_MSFT;
contextProperties.depthBufferStreamResolution = XR_REMOTING_DEPTH_BUFFER_STREAM_RESOLUTION_HALF_MSFT;
xrRemotingSetContextPropertiesMSFT(m_instance.Get(), m_systemId, &contextProperties);
```

La connexion peut être effectuée de deux manières.
1) L’application distante se connecte au lecteur qui s’exécute sur l’appareil.
2) Le lecteur s’exécutant sur l’appareil se connecte à l’application distante.

Pour établir une connexion de l’application distante à l’appareil Player ```xrRemotingConnectMSFT``` , appelez la méthode en spécifiant le nom d’hôte et le port via la  ```XrRemotingConnectInfoMSFT``` structure. Le port utilisé par le lecteur de communication à distance holographique est **8265**.

```cpp
XrRemotingConnectInfoMSFT connectInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_CONNECT_INFO_MSFT)};
connectInfo.remoteHostName = "192.168.x.x";
connectInfo.remotePort = 8265;
connectInfo.secureConnection = false;
xrRemotingConnectMSFT(m_instance.Get(), m_systemId, &connectInfo);
```

L’écoute des connexions entrantes sur l’application distante peut être effectuée en appelant la ```xrRemotingListenMSFT``` méthode. Le port de liaison et le port de transport peuvent être spécifiés via la ```XrRemotingListenInfoMSFT``` structure. Le port de négociation est utilisé pour le protocole de transfert initial. Les données sont ensuite envoyées sur le port de transport. Par défaut, **8265** et **8266** sont utilisés.

```cpp
XrRemotingListenInfoMSFT listenInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_LISTEN_INFO_MSFT)};
listenInfo.listenInterface = "0.0.0.0";
listenInfo.handshakeListenPort = 8265;
listenInfo.transportListenPort = 8266;
listenInfo.secureConnection = false;
xrRemotingListenMSFT(m_instance.Get(), m_systemId, &listenInfo);
```

L’état de la connexion doit être déconnecté lorsque vous appelez ```xrRemotingConnectMSFT``` ou ```xrRemotingListenMSFT``` . Vous pouvez obtenir l’état de la connexion à tout moment après avoir créé un XrInstance et interrogé pour XrSystemId via ```xrRemotingGetConnectionStateMSFT``` .

```cpp
XrRemotingConnectionStateMSFT connectionState;
xrRemotingGetConnectionStateMSFT(m_instance.Get(), m_systemId, &connectionState, nullptr);
```

Les États de connexion disponibles sont les suivants :
- XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT
- XR_REMOTING_CONNECTION_STATE_CONNECTING_MSFT
- XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT

>[!IMPORTANT]
> ```xrRemotingConnectMSFT``` ou ```xrRemotingListenMSFT``` doit être appelé avant d’essayer de créer un XrSession via xrCreateSession. Si vous essayez de créer un XrSession alors que l’état de la connexion est ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` la création de la session réussie, mais que l’état de la session passera immédiatement à XR_SESSION_STATE_LOSS_PENDING.

L’implémentation de la communication à distance holographique de ```xrCreateSession``` prend en charge l’attente de l’établissement d’une connexion. Vous pouvez appeler ```xrRemotingConnectMSFT``` ou ```xrRemotingListenMSFT``` immédiatement suivi d’un appel à, qui bloque et attend qu’une connexion soit établie. Le délai d’attente est fixé à 10 secondes. Si une connexion peut être établie dans ce délai, la création de XrSession est effectuée et l’état de session passera à XR_SESSION_STATE_READY. Dans le cas où aucune connexion ne peut être établie, la création de session s’effectue également, mais passe immédiatement à XR_SESSION_STATE_LOSS_PENDING.

En général, l’état de la connexion est couple à l’État XrSession. Toute modification apportée à l’état de la connexion affecte également l’état de la session. Par exemple, si l’état de la connexion passe de `XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT` à ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` l’état de session passera également à XR_SESSION_STATE_LOSS_PENDING.

## <a name="handling-remoting-specific-events"></a>Gestion des événements de communication à distance spécifiques

Le runtime OpenXR de la communication à distance holographique expose trois événements, qui sont importants pour surveiller l’état d’une connexion.
1) ```XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT```: Déclenché lorsqu’une connexion à l’appareil a été établie avec succès.
2) ```XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT```: Déclenché si une connexion établie est fermée ou si une connexion n’a pas pu être établie.
3) ```XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT```: Lors du démarrage de l’écoute des connexions entrantes.

Ces événements sont placés dans une file d’attente et votre application distante doit lire la file d’attente avec régularité via ```xrPollEvent``` .

```cpp
auto pollEvent = [&](XrEventDataBuffer& eventData) -> bool {
    eventData.type = XR_TYPE_EVENT_DATA_BUFFER;
    eventData.next = nullptr;
    return CHECK_XRCMD(xrPollEvent(m_instance.Get(), &eventData)) == XR_SUCCESS;
};

XrEventDataBuffer eventData{};
while (pollEvent(eventData)) {
    switch (eventData.type) {
    
    ...
    
    case XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Listening on port %d",
                    reinterpret_cast<const XrRemotingEventDataListeningMSFT*>(&eventData)->listeningPort);
        break;
    }
    case XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Connected.");
        break;
    }
    case XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Disconnected - Reason: %d",
                    reinterpret_cast<const XrRemotingEventDataDisconnectedMSFT*>(&eventData)->disconnectReason);
        break;
    }
}
```

## <a name="preview-streamed-content-locally"></a>Afficher un aperçu du contenu diffusé en continu localement

Pour afficher le même contenu dans l’application distante qui est envoyé à l’appareil, l' ```XR_MSFT_holographic_remoting_frame_mirroring``` extension peut être utilisée. Avec cette extension, vous pouvez soumettre une texture à xrEndFrame en utilisant le ```XrRemotingFrameMirrorImageInfoMSFT``` qui n’est pas chaîné au XrFrameEndInfo comme suit.

```cpp
XrFrameEndInfo frameEndInfo{XR_TYPE_FRAME_END_INFO};
...

XrRemotingFrameMirrorImageD3D11MSFT mirrorImageD3D11{
    static_cast<XrStructureType>(XR_TYPE_REMOTING_FRAME_MIRROR_IMAGE_D3D11_MSFT)};
mirrorImageD3D11.texture = m_window->GetNextSwapchainTexture();

XrRemotingFrameMirrorImageInfoMSFT mirrorImageEndInfo{
    static_cast<XrStructureType>(XR_TYPE_REMOTING_FRAME_MIRROR_IMAGE_INFO_MSFT)};
mirrorImageEndInfo.image = reinterpret_cast<const XrRemotingFrameMirrorImageBaseHeaderMSFT*>(&mirrorImageD3D11);

frameEndInfo.next = &mirrorImageEndInfo;

xrEndFrame(m_session.Get(), &frameEndInfo);

m_window->PresentSwapchain();
```

L’exemple ci-dessus utilise une texture de chaîne d’échange DX11 et présente la fenêtre immédiatement après l’appel à xrEndFrame. L’utilisation n’est pas limitée aux textures de chaîne de swap et aucune synchronisation GPU supplémentaire n’est requise. Pour plus d’informations sur l’utilisation et les contraintes, consultez la [spécification d’extension](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring).
Si votre application distante utilise DX12, utilisez XrRemotingFrameMirrorImageD3D12MSFT au lieu de XrRemotingFrameMirrorImageD3D11MSFT.

## <a name="see-also"></a>Voir aussi
* [Écriture d’une application de lecteur de communication à distance holographique personnalisée](holographic-remoting-create-player.md)
* [Établissement d’une connexion sécurisée avec la communication à distance holographique](holographic-remoting-secure-connection.md)
* [Résolution des problèmes et limitations de la communication à distance holographique](holographic-remoting-troubleshooting.md)
* [Termes du contrat de licence de la communication à distance holographique](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Déclaration de confidentialité Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)