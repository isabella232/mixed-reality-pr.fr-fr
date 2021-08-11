---
title: Écriture d’une application distante holographique de communication à distance (WMR)
description: découvrez comment diffuser du contenu distant rendu sur une machine distante pour HoloLens 2 avec des applications de communication à distance holographique avec HolographicSpace.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, remoting, accès distant holographique, casque de réalité mixte, casque windows mixed realisation, casque de réalité virtuelle, NuGet
ms.openlocfilehash: 0d8f7149533de7f3f095761b13feeb91c319cda711c99b9101a13300a591fc2c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219213"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-holographicspace-api"></a>Écriture d’une application distante holographique à distance à l’aide de l’API HolographicSpace

>[!IMPORTANT]
>ce document décrit la création d’une application distante pour HoloLens 2 à l’aide de l' [API HolographicSpace](../native/getting-a-holographicspace.md). les applications distantes pour **HoloLens (1re génération)** doivent utiliser NuGet package version **1. x. x**. cela implique que les applications distantes écrites pour HoloLens 2 ne sont pas compatibles avec HoloLens 1 et vice versa. vous trouverez la documentation relative à HoloLens 1 [ici](add-holographic-remoting.md).

les applications de communication à distance holographique peuvent diffuser du contenu à distance à HoloLens 2 et Windows Mixed Reality des casques immersifs. Vous pouvez également accéder à davantage de ressources système et intégrer des [vues immersives](../../design/app-views.md) distantes dans des logiciels de poste de travail existants. une application distante reçoit un flux de données d’entrée de HoloLens 2, restitue le contenu dans une vue immersive virtuelle et diffuse les trames de contenu à HoloLens 2. La connexion est établie à l’aide du Wi-Fi standard. la communication à distance holographique est ajoutée à une application de bureau ou UWP via un paquet NuGet. Du code supplémentaire est nécessaire pour gérer la connexion et le rendu dans une vue immersive. Une connexion à distance classique aura une latence aussi faible que 50 ms de latence. L’application de lecteur peut signaler la latence en temps réel.

Tout le code de cette page et des projets de travail se trouve dans le [référentiel GitHub d’exemples de communication à distance holographique](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

## <a name="prerequisites"></a>Prérequis

Un bon point de départ est un bureau DirectX opérationnel ou une application UWP qui cible l' [API HolographicSpace](../native/getting-a-holographicspace.md). Pour plus d’informations, consultez [vue d’ensemble du développement DirectX](../native/directx-development-overview.md). Le [modèle de projet holographique C++](../native/creating-a-holographic-directx-project.md) est un bon point de départ.

>[!IMPORTANT]
>Toute application utilisant la communication à distance holographique doit être créée pour utiliser un [cloisonnement](/windows/win32/com/multithreaded-apartments)multithread. L’utilisation d’un [cloisonnement à thread unique](/windows/win32/com/single-threaded-apartments) est prise en charge, mais entraîne des performances non optimales et éventuellement des interruptions pendant la lecture. Lors de l’utilisation de C++/WinRT [WinRT :: init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) un cloisonnement multithread est la valeur par défaut.



## <a name="get-the-holographic-remoting-nuget-package"></a>procurez-vous le package NuGet de communication à distance holographique

les étapes suivantes sont requises pour ajouter le package NuGet à un projet dans Visual Studio.
1. Ouvrez le projet dans Visual Studio.
2. cliquez avec le bouton droit sur le nœud du projet et sélectionnez **gérer les Packages NuGet...**
3. Dans le volet qui s’affiche, sélectionnez **Parcourir** , puis recherchez « accès à distance holographique ».
4. Sélectionnez **Microsoft. holographique. Remoting**, assurez-vous de choisir la version la plus récente de **2. x. x** , puis sélectionnez **installer**.
5. Si la boîte de dialogue **Aperçu** s’affiche, sélectionnez **OK**.
6. Sélectionnez **J’accepte** quand la boîte de dialogue du contrat de licence s’affiche.

>[!NOTE]
>la Version **1. x. x** du package NuGet est toujours disponible pour les développeurs qui souhaitent cibler HoloLens 1. pour plus d’informations [, consultez ajouter une communication à distance holographique (HoloLens (1er génération))](add-holographic-remoting.md).

## <a name="create-the-remote-context"></a>Créer le contexte distant

En guise de première étape, l’application doit créer un contexte distant.

```cpp
// class declaration
#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
    // RemoteContext used to connect with a Holographic Remoting player and display rendered frames
    winrt::Microsoft::Holographic::AppRemoting::RemoteContext m_remoteContext = nullptr;
```


```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

```

>[!WARNING]
>la communication à distance holographique fonctionne en remplaçant le runtime Windows Mixed Reality qui fait partie de Windows avec un runtime spécifique à distance. Cette opération est effectuée lors de la création du contexte distant. pour cette raison, tout appel sur une API de Windows Mixed Reality avant de créer le contexte distant peut entraîner un comportement inattendu. L’approche recommandée consiste à créer le contexte distant le plus tôt possible avant d’interagir avec une API de réalité mixte. ne combinez jamais des objets créés ou récupérés par le biais d’une API Windows Mixed Reality avant l’appel à CreateRemoteContext avec des objets créés ou récupérés par la suite.

L’espace holographique doit ensuite être créé. La spécification d’un CoreWindow n’est pas obligatoire. Les applications de bureau qui n’ont pas de CoreWindow peuvent simplement passer un ```nullptr``` .

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a>Connecter à l’appareil

Lorsque l’application distante est prête pour le rendu du contenu, une connexion à l’appareil Player peut être établie.

La connexion peut être effectuée de deux manières.
1) L’application distante se connecte au lecteur qui s’exécute sur l’appareil.
2) Le lecteur s’exécutant sur l’appareil se connecte à l’application distante.

Pour établir une connexion de l’application distante à l’appareil Player ```Connect``` , appelez la méthode sur le contexte distant en spécifiant le nom d’hôte et le port. Le port utilisé par le lecteur de communication à distance holographique est **8265**.

```cpp
try
{
    m_remoteContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Connect failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
>Comme pour toute API/WinRT C++ ```Connect``` peut lever une exception WinRT :: hresult_error qui doit être gérée.

>[!TIP]
>pour éviter d’utiliser la projection du langage [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/) ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` , vous pouvez inclure le fichier situé dans le package NuGet de communication à distance holographique. Il contient les déclarations des interfaces COM sous-jacentes. L’utilisation de C++/WinRT est toutefois recommandée.

L’écoute des connexions entrantes sur l’application distante peut être effectuée en appelant la ```Listen``` méthode. Le port de liaison et le port de transport peuvent être spécifiés au cours de cet appel. Le port de négociation est utilisé pour le protocole de transfert initial. Les données sont ensuite envoyées sur le port de transport. Par défaut, **8265** et **8266** sont utilisés.

```cpp
try
{
    m_remoteContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Listen failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
>l' ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` intérieur du package NuGet contient une documentation détaillée sur l’API exposée par la communication à distance holographique.

## <a name="handling-remoting-specific-events"></a>Gestion des événements de communication à distance spécifiques

Le contexte distant expose trois événements, qui sont importants pour surveiller l’état d’une connexion.
1) OnConnected : déclenché lorsqu’une connexion à l’appareil a été établie avec succès.
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) OnDisconnected : déclenché si une connexion établie est fermée ou si une connexion n’a pas pu être établie.
```cpp
m_onDisconnectedEventRevoker =
    m_remoteContext.OnDisconnected(winrt::auto_revoke, [this, remoteContextWeakRef](ConnectionFailureReason failureReason) {
        if (auto remoteContext = remoteContextWeakRef.get())
        {
            DebugLog(L"Disconnected with reason %d", failureReason);
            // Update UI

            // Reconnect if this is a transient failure.
            if (failureReason == ConnectionFailureReason::HandshakeUnreachable ||
                failureReason == ConnectionFailureReason::TransportUnreachable ||
                failureReason == ConnectionFailureReason::ConnectionLost)
            {
                DebugLog(L"Reconnecting...");

                ConnectOrListen();
            }
            // Failure reason None indicates a normal disconnect.
            else if (failureReason != ConnectionFailureReason::None)
            {
                DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
            }
        }
    });
```
3) OnListening : lors du démarrage de l’écoute des connexions entrantes.
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

En outre, l’état de la connexion peut être interrogé à l’aide de la ```ConnectionState``` propriété sur le contexte distant.
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a>Gestion des événements vocaux

à l’aide de l’interface de reconnaissance vocale à distance, il est possible d’inscrire les déclencheurs vocaux avec HoloLens 2 et de les faire distants à l’application distante.

Ce membre supplémentaire est requis pour effectuer le suivi de l’état de la voix à distance.

```cpp
winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker m_onRecognizedSpeechRevoker;

```

Tout d’abord, l’interface de reconnaissance vocale à distance doit être récupérée.

```cpp
if (auto remoteSpeech = m_remoteContext.GetRemoteSpeech())
{
    InitializeSpeechAsync(remoteSpeech, m_onRecognizedSpeechRevoker, weak_from_this());
}
```

À l’aide d’une méthode d’assistance asynchrone, vous pouvez initialiser la reconnaissance vocale à distance. Cette opération doit être effectuée de façon asynchrone, car l’initialisation peut prendre beaucoup de temps. [Opérations d’accès concurrentiel et asynchrones avec c++/WinRT](/windows/uwp/cpp-and-winrt-apis/concurrency) explique comment créer des fonctions asynchrones avec c++/WinRT.

```cpp
winrt::Windows::Foundation::IAsyncOperation<winrt::Windows::Storage::StorageFile> LoadGrammarFileAsync()
{
    const wchar_t* speechGrammarFile = L"SpeechGrammar.xml";
    auto rootFolder = winrt::Windows::ApplicationModel::Package::Current().InstalledLocation();
    return rootFolder.GetFileAsync(speechGrammarFile);
}

winrt::fire_and_forget InitializeSpeechAsync(
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech remoteSpeech,
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker& onRecognizedSpeechRevoker,
    std::weak_ptr<SampleRemoteMain> sampleRemoteMainWeak)
{
    onRecognizedSpeechRevoker = remoteSpeech.OnRecognizedSpeech(
        winrt::auto_revoke, [sampleRemoteMainWeak](const winrt::Microsoft::Holographic::AppRemoting::RecognizedSpeech& recognizedSpeech) {
            if (auto sampleRemoteMain = sampleRemoteMainWeak.lock())
            {
                sampleRemoteMain->OnRecognizedSpeech(recognizedSpeech.RecognizedText);
            }
        });

    auto grammarFile = co_await LoadGrammarFileAsync();

    std::vector<winrt::hstring> dictionary;
    dictionary.push_back(L"Red");
    dictionary.push_back(L"Blue");
    dictionary.push_back(L"Green");
    dictionary.push_back(L"Default");
    dictionary.push_back(L"Aquamarine");

    remoteSpeech.ApplyParameters(L"", grammarFile, dictionary);
}
```

Il existe deux façons de spécifier des expressions à reconnaître.
1) Spécification à l’intérieur d’un fichier XML de grammaire vocale. Pour plus d’informations, consultez [comment créer une grammaire XML de base](/previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) .
2) Spécifiez en les passant dans le vecteur du dictionnaire à ```ApplyParameters``` .

À l’intérieur du rappel OnRecognizedSpeech, les événements vocaux peuvent ensuite être traités :

```cpp
void SampleRemoteMain::OnRecognizedSpeech(const winrt::hstring& recognizedText)
{
    bool changedColor = false;
    DirectX::XMFLOAT4 color = {1, 1, 1, 1};

    if (recognizedText == L"Red")
    {
        color = {1, 0, 0, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Blue")
    {
        color = {0, 0, 1, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Green")
    {
        ...
    }

    ...
}
```

## <a name="preview-streamed-content-locally"></a>Afficher un aperçu du contenu diffusé en continu localement

Pour afficher le même contenu dans l’application distante qui est envoyé à l’appareil, l' ```OnSendFrame``` événement du contexte distant peut être utilisé. L' ```OnSendFrame``` événement est déclenché chaque fois que la bibliothèque de communication à distance holographique envoie le frame actuel au périphérique distant. C’est le moment idéal pour prendre le contenu et le configurer dans la fenêtre du bureau ou UWP.

```cpp
#include <windows.graphics.directx.direct3d11.interop.h>

...

m_onSendFrameEventRevoker = m_remoteContext.OnSendFrame(
    winrt::auto_revoke, [this](const winrt::Windows::Graphics::DirectX::Direct3D11::IDirect3DSurface& texture) {
        winrt::com_ptr<ID3D11Texture2D> texturePtr;
        {
            winrt::com_ptr<ID3D11Resource> resource;
            winrt::com_ptr<::IInspectable> inspectable = texture.as<::IInspectable>();
            winrt::com_ptr<Windows::Graphics::DirectX::Direct3D11::IDirect3DDxgiInterfaceAccess> dxgiInterfaceAccess;
            winrt::check_hresult(inspectable->QueryInterface(__uuidof(dxgiInterfaceAccess), dxgiInterfaceAccess.put_void()));
            winrt::check_hresult(dxgiInterfaceAccess->GetInterface(__uuidof(resource), resource.put_void()));
            resource.as(texturePtr);
        }

        // Copy / blit texturePtr into the back buffer here.
    });
```

## <a name="depth-reprojection"></a>Reprojection de profondeur

À partir de la version [2.1.0](holographic-remoting-version-history.md#v2.1.0), la communication à distance holographique prend en charge la [reprojection de profondeur](hologram-stability.md#reprojection). Cela nécessite que la mémoire tampon de couleur et la mémoire tampon de profondeur soient diffusées de l’application distante vers le HoloLens 2. Par défaut, la diffusion en continu de la mémoire tampon est activée et configurée pour utiliser la moitié de la résolution de la mémoire tampon de couleur. Vous pouvez modifier cette valeur comme suit :

```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

// Configure for half-resolution depth.
m_remoteContext.ConfigureDepthVideoStream(DepthBufferStreamResolution::Half_Resolution);

```

Notez que, si les valeurs par défaut ne doivent pas être utilisées, ```ConfigureDepthVideoStream``` doivent être appelées avant d’établir une connexion au HoloLens 2. Le meilleur emplacement est juste après avoir créé le contexte distant. Les valeurs possibles pour DepthBufferStreamResolution sont les suivantes :

* Full_Resolution
* Half_Resolution
* Quarter_Resolution
* Désactivé (ajouté avec la version [2.1.3](holographic-remoting-version-history.md#v2.1.3) et, s’il n’est utilisé, aucun flux vidéo de profondeur supplémentaire n’est créé)

Gardez à l’esprit que l’utilisation d’une mémoire tampon de profondeur de résolution complète affecte également les besoins en bande passante et doit être comptabilisée dans la valeur de bande passante maximale que vous fournissez à ```CreateRemoteContext``` .

À côté de la configuration de la résolution, vous devez également valider un tampon de profondeur à l’aide de [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).

```cpp

void SampleRemoteMain::Render(HolographicFrame holographicFrame)
{
    ...

    m_deviceResources->UseHolographicCameraResources([this, holographicFrame](auto& cameraResourceMap) {
        
        ...

        for (auto cameraPose : prediction.CameraPoses())
        {
            DXHelper::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

            ...

            m_deviceResources->UseD3DDeviceContext([&](ID3D11DeviceContext3* context) {
                
                ...

                // Commit depth buffer if available and enabled.
                if (m_canCommitDirect3D11DepthBuffer && m_commitDirect3D11DepthBuffer)
                {
                    auto interopSurface = pCameraResources->GetDepthStencilTextureInteropObject();
                    HolographicCameraRenderingParameters renderingParameters = holographicFrame.GetRenderingParameters(cameraPose);
                    renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
                }
            });
        }
    });
}

```

pour vérifier si la reprojection de profondeur fonctionne correctement sur HoloLens 2, vous pouvez activer un visualiseur de profondeur via le portail de l’appareil. Pour plus d’informations, voir vérification de la [profondeur définie correctement](hologram-stability.md#verifying-depth-is-set-correctly) .

## <a name="optional-custom-data-channels"></a>Facultatif : canaux de données personnalisés

Les canaux de données personnalisés peuvent être utilisés pour envoyer des données utilisateur sur la connexion de communication à distance déjà établie. Pour plus d’informations, consultez [canaux de données personnalisés](holographic-remoting-custom-data-channels.md) .

## <a name="see-also"></a>Voir aussi
* [Écriture d’une application de lecteur de communication à distance holographique personnalisée](holographic-remoting-create-player.md)
* [Canaux de données de communication à distance holographique personnalisés](holographic-remoting-custom-data-channels.md)
* [Établissement d’une connexion sécurisée avec la communication à distance holographique](holographic-remoting-secure-connection.md)
* [Résolution des problèmes et limitations de la communication à distance holographique](holographic-remoting-troubleshooting.md)
* [Termes du contrat de licence de la communication à distance holographique](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Déclaration de confidentialité Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)