---
title: Ajouter la communication à distance holographique
description: découvrez comment installer, configurer et utiliser la communication à distance holographique pour afficher des hologrammes sur un appareil HoloLens sur le réseau.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Windows Mixed Reality, hologrammes, accès distant holographique, rendu à distance, rendu réseau, HoloLens, hologrammes distants, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle
ms.openlocfilehash: 3f9d3d23d18f680ce1001310e4ce49089edaae6a
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184620"
---
# <a name="add-holographic-remoting-hololens-first-gen"></a>ajouter la communication à distance holographique (HoloLens (première génération))

>[!IMPORTANT]
> ce document décrit la création d’une application hôte pour HoloLens 1. l’application hôte pour **HoloLens (1re génération)** doit utiliser NuGet package version **1. x. x**. cela implique que les applications hôtes écrites pour HoloLens 1 ne sont pas compatibles avec HoloLens 2 et vice versa.

## <a name="hololens-2"></a>HoloLens 2

HoloLens les développeurs qui utilisent la communication à distance holographique doivent mettre à jour leurs applications pour les rendre compatibles avec HoloLens 2. cela nécessite une nouvelle version du package de NuGet de communication à distance holographique. veillez à utiliser la version 2.0.0.0 ou supérieure du package de NuGet de communication à distance holographique lors de la connexion au lecteur de communication à distance holographique sur HoloLens 2 ou la connexion échouera.

>[!NOTE]
> vous trouverez des conseils spécifiques à HoloLens 2 [ici](holographic-remoting-create-remote-wmr.md).


## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a>Ajout de la communication à distance holographique à votre application de bureau ou UWP

Cette page explique comment ajouter la communication à distance holographique à une application de bureau ou UWP.

la communication à distance holographique permet à votre application de cibler une HoloLens avec un contenu holographique hébergé sur un ordinateur de bureau ou sur un appareil UWP tel que le Xbox One. Vous avez également accès à davantage de ressources système, ce qui permet d’intégrer des [vues immersives](../../design/app-views.md) distantes dans des logiciels de poste de travail existants. une application hôte de communication à distance reçoit un flux de données d’entrée d’un HoloLens, restitue le contenu dans une vue immersive virtuelle et diffuse en continu des frames de contenu vers HoloLens. La connexion est établie à l’aide du Wi-Fi standard. pour utiliser la communication à distance, utilisez un package NuGet pour ajouter la communication à distance holographique à votre application de bureau ou UWP, puis écrivez le code pour gérer la connexion et restituer une vue immersive. Les bibliothèques d’assistance sont incluses dans l’exemple de code qui simplifie la tâche de gestion de la connexion de l’appareil.

Une connexion à distance classique aura une latence aussi faible que 50 ms de latence. L’application de lecteur peut signaler la latence en temps réel.

>[!NOTE]
>Les extraits de code de cet article illustrent actuellement l’utilisation de C++/CX au lieu des/WinRT C++ conformes à C + +17, tels qu’ils sont utilisés dans le [modèle de projet holographique c++](../native/creating-a-holographic-directx-project.md).  Les concepts sont équivalents pour un projet C++/WinRT, bien que vous deviez traduire le code.

### <a name="get-the-remoting-nuget-packages"></a>récupération des packages de NuGet de communication à distance

procédez comme suit pour obtenir le package NuGet pour la communication à distance holographique et ajouter une référence à partir de votre projet :
1. Accédez à votre projet dans Visual Studio.
2. cliquez avec le bouton droit sur le nœud du projet et sélectionnez **gérer les Packages NuGet...**
3. Dans le volet qui s’affiche, selecct **Parcourir** , puis recherchez « accès distant holographique ».
4. Sélectionnez **Microsoft. holographique. Remoting** et l' **installation** de selecct.
5. Si la boîte de dialogue **Aperçu** s’affiche, sélectionnez **OK**.
6. Sélectionnez **J’accepte** lorsque la boîte de dialogue contrat de licence s’affiche.

### <a name="create-the-holographicstreamerhelpers"></a>Créer le HolographicStreamerHelpers

Tout d’abord, nous devons ajouter une instance de HolographicStreamerHelpers à la classe qui gérera la communication à distance.

```cpp
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

Vous devez également suivre l’état de la connexion. Si vous souhaitez afficher l’aperçu, vous devez avoir une texture sur laquelle la copier. vous avez également besoin de quelques éléments comme un verrou d’état de connexion, un moyen de stocker l’adresse IP de HoloLens, etc.

```cpp
private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::SRWLock                   m_connectionStateLock;

       RemotingHostSample::AppView^                        m_appView;
       Platform::String^                                   m_ipAddress;
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::CriticalSection           m_deviceLock;
       Microsoft::WRL::ComPtr<IDXGISwapChain1>             m_swapChain;
       Microsoft::WRL::ComPtr<ID3D11Texture2D>             m_spTexture;
```

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a>Initialiser HolographicStreamerHelpers et se connecter à HoloLens

pour vous connecter à un appareil HoloLens, créez une instance de HolographicStreamerHelpers et connectez-vous à l’adresse IP cible. vous devez définir la taille de l’image vidéo pour qu’elle corresponde à la largeur et à la hauteur de l’HoloLens d’affichage, car la bibliothèque de communication à distance holographique s’attend à ce que les résolutions d’encodeur et de décodeur correspondent exactement.

```cpp
m_streamerHelpers = ref new HolographicStreamerHelpers();
       m_streamerHelpers->CreateStreamer(m_d3dDevice);

       // We currently need to stream at 720p because that's the resolution of our remote display.
       // There is a check in the holographic streamer that makes sure the remote and local
       // resolutions match. The default streamer resolution is 1080p.
       m_streamerHelpers->SetVideoFrameSize(1280, 720);

       try
       {
           m_streamerHelpers->Connect(m_ipAddress->Data(), 8001);
       }
       catch (Platform::Exception^ ex)
       {
           DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
       }
```

La connexion de l’appareil est asynchrone. Votre application doit fournir des gestionnaires d’événements pour les événements de connexion, de déconnexion et d’envoi de frame.

L’événement OnConnected peut mettre à jour l’interface utilisateur, démarrer le rendu, et ainsi de suite. Dans notre exemple de code de bureau, nous mettons à jour le titre de la fenêtre avec un message « connecté ».

```cpp
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

L’événement OnDisconnected peut gérer la reconnexion, les mises à jour de l’interface utilisateur, etc. Dans cet exemple, nous nous reconnectons en cas de défaillance temporaire.

```cpp
Platform::WeakReference streamerHelpersWeakRef = Platform::WeakReference(m_streamerHelpers);
       m_streamerHelpers->OnDisconnected += ref new DisconnectedEvent(
           [this, streamerHelpersWeakRef](_In_ HolographicStreamerConnectionFailureReason failureReason)
           {
               DebugLog(L"Disconnected with reason %d", failureReason);
               UpdateWindowTitle();

               // Reconnect if this is a transient failure.
               if (failureReason == HolographicStreamerConnectionFailureReason::Unreachable ||
                   failureReason == HolographicStreamerConnectionFailureReason::ConnectionLost)
               {
                   DebugLog(L"Reconnecting...");

                   try
                   {
                       auto helpersResolved = streamerHelpersWeakRef.Resolve<HolographicStreamerHelpers>();
                       if (helpersResolved)
                       {
                           helpersResolved->Connect(m_ipAddress->Data(), 8001);
                       }
                       else
                       {
                           DebugLog(L"Failed to reconnect because a disconnect has already occurred.\n");
                       }
                   }
                   catch (Platform::Exception^ ex)
                   {
                       DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
                   }
               }
               else
               {
                   DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
               }
           });
```

Lorsque le composant de communication à distance est prêt à envoyer un frame, votre application vous offre la possibilité d’en faire une copie dans le SendFrameEvent. Ici, nous copions le frame dans une chaîne de permutation afin que nous puissions l’afficher dans une fenêtre d’aperçu.

```cpp
m_streamerHelpers->OnSendFrame += ref new SendFrameEvent(
           [this](_In_ const ComPtr<ID3D11Texture2D>& spTexture, _In_ FrameMetadata metadata)
           {
               if (m_showPreview)
               {
                   ComPtr<ID3D11Device1> spDevice = m_appView->GetDeviceResources()->GetD3DDevice();
                   ComPtr<ID3D11DeviceContext> spContext = m_appView->GetDeviceResources()->GetD3DDeviceContext();

                   ComPtr<ID3D11Texture2D> spBackBuffer;
                   ThrowIfFailed(m_swapChain->GetBuffer(0, IID_PPV_ARGS(&spBackBuffer)));

                   spContext->CopySubresourceRegion(
                       spBackBuffer.Get(), // dest
                       0,                  // dest subresource
                       0, 0, 0,            // dest x, y, z
                       spTexture.Get(),    // source
                       0,                  // source subresource
                       nullptr);           // source box, null means the entire resource

                   DXGI_PRESENT_PARAMETERS parameters = { 0 };
                   ThrowIfFailed(m_swapChain->Present1(1, 0, &parameters));
               }
           });
```

### <a name="render-holographic-content"></a>Afficher le contenu holographique

Pour afficher le contenu à l’aide de la communication à distance, vous devez configurer un IFrameworkView virtuel dans votre application de bureau ou UWP et traiter des frames holographiques à partir de la communication à distance. toutes les api holographiques Windows sont utilisées de la même façon par cette vue, mais elles sont configurées légèrement différemment.

Au lieu de les créer vous-même, les composants d’espace et de parole holographiques proviennent de votre classe HolographicRemotingHelpers :

```cpp
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

Au lieu d’utiliser une boucle de mise à jour dans une méthode Run, vous fournissez des mises à jour de graduations à partir de la boucle principale de votre application de bureau ou UWP. Cela permet à votre application de bureau ou UWP de rester dans le contrôle du traitement des messages.

```cpp
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

La méthode Tick () de la vue de l’application holographique termine une itération de la boucle Update, Draw et present.

```cpp
void AppView::Tick()
   {
       if (m_main)
       {
           // When running on Windows Holographic, we can use the holographic rendering system.
           HolographicFrame^ holographicFrame = m_main->Update();

           if (holographicFrame && m_main->Render(holographicFrame))
           {
               // The holographic frame has an API that presents the swap chain for each
               // holographic camera.
               m_deviceResources->Present(holographicFrame);
           }
       }
   }
```

la vue de mise à jour, le rendu et la boucle d’affichage des applications holographiques sont exactement les mêmes que lorsqu’elles s’exécutent sur HoloLens, sauf que vous avez accès à une quantité beaucoup plus importante de ressources système sur votre ordinateur de bureau. Vous pouvez restituer beaucoup plus de triangles, avoir plus de passes de dessin, faire plus de physique et utiliser des processus x64 pour charger le contenu qui nécessite plus de 2 Go de RAM.

### <a name="disconnect-and-end-the-remote-session"></a>Déconnecter et mettre fin à la session à distance

Pour se déconnecter : par exemple, quand l’utilisateur clique sur un bouton de l’interface utilisateur pour déconnecter-appeler Disconnect () sur HolographicStreamerHelpers, puis libérer l’objet.

```cpp
void DesktopWindow::DisconnectFromRemoteDevice()
   {
       // Disconnecting from the remote device can change the connection state.
       auto exclusiveLock = m_connectionStateLock.LockExclusive();

       if (m_streamerHelpers != nullptr)
       {
           m_streamerHelpers->Disconnect();

           // Reset state
           m_streamerHelpers = nullptr;
       }
   }
```

## <a name="get-the-remoting-player"></a>Procurez-vous le lecteur de communication à distance

le Windows lecteur de communication à distance holographique est proposé dans le Windows app store en tant que point de terminaison pour que les applications hôtes de communication à distance se connectent à. pour obtenir le Windows lecteur de communication à distance holographique, visitez le Windows app store à partir de votre HoloLens, recherchez la communication à distance et téléchargez l’application. Le lecteur de communication à distance comprend une fonctionnalité permettant d’afficher les statistiques à l’écran, ce qui peut être utile lors du débogage des applications hôtes de communication à distance.

## <a name="notes-and-resources"></a>Remarques et ressources

La vue de l’application holographique a besoin d’un moyen de fournir à votre application l’appareil Direct3D, qui doit être utilisé pour initialiser l’espace holographique. Votre application doit utiliser ce périphérique Direct3D pour copier et afficher le frame d’aperçu.

```cpp
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

**Exemple de code :** Un exemple complet de [Code de communication à distance holographique](https://github.com/Microsoft/HoloLensCompanionKit) est disponible, qui comprend une vue d’application holographique compatible avec la communication à distance et les projets hôtes de communication à distance pour les ordinateurs de bureau Win32, UWP DirectX et UWP avec XAML. 

**Remarque sur le débogage :** La bibliothèque de communication à distance holographique peut lever des exceptions de première chance. ces exceptions peuvent être visibles dans les sessions de débogage, en fonction de la Visual Studio paramètres d’exception qui sont actifs à ce moment-là. Ces exceptions sont interceptées en interne par la bibliothèque de communication à distance holographique et peuvent être ignorées.

## <a name="see-also"></a>Voir aussi
* [Vue d’ensemble de la communication à distance holographique](holographic-remoting-overview.md)
* [Écriture d’une application de lecteur de communication à distance holographique personnalisée](holographic-remoting-create-player.md)
* [Établissement d’une connexion sécurisée avec la communication à distance holographique](holographic-remoting-secure-connection.md)
* [Résolution des problèmes et limitations de la communication à distance holographique](holographic-remoting-troubleshooting.md)
* [Termes du contrat de licence de la communication à distance holographique](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Déclaration de confidentialité Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)