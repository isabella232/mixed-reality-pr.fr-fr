---
title: Ajouter la communication à distance holographique
description: Découvrez comment installer, configurer et utiliser la communication à distance holographique pour afficher des hologrammes sur un appareil HoloLens sur le réseau.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Windows Mixed Reality, hologrammes, accès distant holographique, rendu à distance, rendu réseau, HoloLens, hologrammes distants, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle
ms.openlocfilehash: 68c1dd43dac4830da061d4900ce768692057e781
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006669"
---
# <a name="add-holographic-remoting-hololens-first-gen"></a><span data-ttu-id="c73fc-104">Ajouter la communication à distance holographique (HoloLens (First Gen))</span><span class="sxs-lookup"><span data-stu-id="c73fc-104">Add Holographic Remoting (HoloLens (first gen))</span></span>

>[!IMPORTANT]
> <span data-ttu-id="c73fc-105">Ce document décrit la création d’une application hôte pour HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="c73fc-105">This document describes the creation of a host application for HoloLens 1.</span></span> <span data-ttu-id="c73fc-106">L’application hôte pour **HoloLens (1re génération)** doit utiliser le package NuGet version **1. x. x**.</span><span class="sxs-lookup"><span data-stu-id="c73fc-106">Host application for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="c73fc-107">Cela implique que les applications hôtes écrites pour HoloLens 1 ne sont pas compatibles avec HoloLens 2 et vice versa.</span><span class="sxs-lookup"><span data-stu-id="c73fc-107">This implies that host applications written for HoloLens 1 are not compatible with HoloLens 2 and vice versa.</span></span>

## <a name="hololens-2"></a><span data-ttu-id="c73fc-108">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="c73fc-108">HoloLens 2</span></span>

<span data-ttu-id="c73fc-109">Les développeurs HoloLens qui utilisent la communication à distance holographique doivent mettre à jour leurs applications pour les rendre compatibles avec HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c73fc-109">HoloLens developers using Holographic Remoting will need to update their apps to make them compatible with HoloLens 2.</span></span> <span data-ttu-id="c73fc-110">Cela nécessite une nouvelle version du package NuGet de communication à distance holographique.</span><span class="sxs-lookup"><span data-stu-id="c73fc-110">This requires a new version of the Holographic Remoting NuGet package.</span></span> <span data-ttu-id="c73fc-111">Veillez à utiliser la version 2.0.0.0 ou ultérieure du package NuGet de communication à distance holographique lors de la connexion au lecteur de communication à distance holographique sur HoloLens 2, sans quoi la connexion échouera.</span><span class="sxs-lookup"><span data-stu-id="c73fc-111">Be sure to use version 2.0.0.0 or above of the Holographic Remoting NuGet package when connecting to the Holographic Remoting Player on HoloLens 2 or the connection will fail.</span></span>

>[!NOTE]
> <span data-ttu-id="c73fc-112">Vous trouverez des conseils spécifiques à HoloLens 2 [ici](holographic-remoting-create-remote-wmr.md).</span><span class="sxs-lookup"><span data-stu-id="c73fc-112">Guidance specific to HoloLens 2 can be found [here](holographic-remoting-create-remote-wmr.md).</span></span>


## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a><span data-ttu-id="c73fc-113">Ajout de la communication à distance holographique à votre application de bureau ou UWP</span><span class="sxs-lookup"><span data-stu-id="c73fc-113">Add holographic remoting to your desktop or UWP app</span></span>

<span data-ttu-id="c73fc-114">Cette page explique comment ajouter la communication à distance holographique à une application de bureau ou UWP.</span><span class="sxs-lookup"><span data-stu-id="c73fc-114">This page describes how to add Holographic Remoting to a desktop or UWP app.</span></span>

<span data-ttu-id="c73fc-115">La communication à distance holographique permet à votre application de cibler un HoloLens avec un contenu holographique hébergé sur un ordinateur de bureau ou sur un appareil UWP tel que le Xbox.</span><span class="sxs-lookup"><span data-stu-id="c73fc-115">Holographic remoting lets your app target a HoloLens with holographic content hosted on a desktop PC or on a UWP device such as the Xbox One.</span></span> <span data-ttu-id="c73fc-116">Vous avez également accès à davantage de ressources système, ce qui permet d’intégrer des [vues immersives](../../design/app-views.md) distantes dans des logiciels de poste de travail existants.</span><span class="sxs-lookup"><span data-stu-id="c73fc-116">You also have access to more system resources, making it possible to integrate remote [immersive views](../../design/app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="c73fc-117">Une application hôte de communication à distance reçoit un flux de données d’entrée d’un HoloLens, restitue le contenu dans une vue immersive virtuelle et diffuse en continu des frames de contenu vers HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c73fc-117">A remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens.</span></span> <span data-ttu-id="c73fc-118">La connexion est établie à l’aide du Wi-Fi standard.</span><span class="sxs-lookup"><span data-stu-id="c73fc-118">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="c73fc-119">Pour utiliser la communication à distance, utilisez un package NuGet pour ajouter la communication à distance holographique à votre application de bureau ou UWP, puis écrivez le code pour gérer la connexion et restituer une vue immersive.</span><span class="sxs-lookup"><span data-stu-id="c73fc-119">To use remoting, use a NuGet package to add holographic remoting to your desktop or UWP app, then write code to handle the connection and render an immersive view.</span></span> <span data-ttu-id="c73fc-120">Les bibliothèques d’assistance sont incluses dans l’exemple de code qui simplifie la tâche de gestion de la connexion de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="c73fc-120">Helper libraries are included in the code sample that simplify the task of handling the device connection.</span></span>

<span data-ttu-id="c73fc-121">Une connexion à distance classique aura une latence aussi faible que 50 ms de latence.</span><span class="sxs-lookup"><span data-stu-id="c73fc-121">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="c73fc-122">L’application de lecteur peut signaler la latence en temps réel.</span><span class="sxs-lookup"><span data-stu-id="c73fc-122">The player app can report the latency in real time.</span></span>

>[!NOTE]
><span data-ttu-id="c73fc-123">Les extraits de code de cet article illustrent actuellement l’utilisation de C++/CX au lieu des/WinRT C++ conformes à C + +17, tels qu’ils sont utilisés dans le [modèle de projet holographique c++](../native/creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="c73fc-123">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](../native/creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="c73fc-124">Les concepts sont équivalents pour un projet C++/WinRT, bien que vous deviez traduire le code.</span><span class="sxs-lookup"><span data-stu-id="c73fc-124">The concepts are equivalent for a C++/WinRT project, though you'll need to translate the code.</span></span>

### <a name="get-the-remoting-nuget-packages"></a><span data-ttu-id="c73fc-125">Récupération des packages NuGet de communication à distance</span><span class="sxs-lookup"><span data-stu-id="c73fc-125">Get the remoting NuGet packages</span></span>

<span data-ttu-id="c73fc-126">Procédez comme suit pour obtenir le package NuGet pour la communication à distance holographique et ajouter une référence à partir de votre projet :</span><span class="sxs-lookup"><span data-stu-id="c73fc-126">Follow these steps to get the NuGet package for holographic remoting, and add a reference from your project:</span></span>
1. <span data-ttu-id="c73fc-127">Accédez à votre projet dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c73fc-127">Go to your project in Visual Studio.</span></span>
2. <span data-ttu-id="c73fc-128">Cliquez avec le bouton droit sur le nœud du projet et sélectionnez **gérer les packages NuGet...**</span><span class="sxs-lookup"><span data-stu-id="c73fc-128">Right-click on the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="c73fc-129">Dans le volet qui s’affiche, selecct **Parcourir** , puis recherchez « accès distant holographique ».</span><span class="sxs-lookup"><span data-stu-id="c73fc-129">In the panel that appears, selecct **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="c73fc-130">Sélectionnez **Microsoft. holographique. Remoting** et l' **installation** de selecct.</span><span class="sxs-lookup"><span data-stu-id="c73fc-130">Select **Microsoft.Holographic.Remoting** and selecct **Install**.</span></span>
5. <span data-ttu-id="c73fc-131">Si la boîte de dialogue **Aperçu** s’affiche, sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="c73fc-131">If the **Preview** dialog appears, select **OK**.</span></span>
6. <span data-ttu-id="c73fc-132">Sélectionnez **J’accepte** lorsque la boîte de dialogue contrat de licence s’affiche.</span><span class="sxs-lookup"><span data-stu-id="c73fc-132">Select **I Accept** when the license agreement dialog appears.</span></span>

### <a name="create-the-holographicstreamerhelpers"></a><span data-ttu-id="c73fc-133">Créer le HolographicStreamerHelpers</span><span class="sxs-lookup"><span data-stu-id="c73fc-133">Create the HolographicStreamerHelpers</span></span>

<span data-ttu-id="c73fc-134">Tout d’abord, nous devons ajouter une instance de HolographicStreamerHelpers à la classe qui gérera la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="c73fc-134">First, we need to add an instance of HolographicStreamerHelpers to the class that will handle remoting.</span></span>

```cpp
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

<span data-ttu-id="c73fc-135">Vous devez également suivre l’état de la connexion.</span><span class="sxs-lookup"><span data-stu-id="c73fc-135">You'll also need to track connection state.</span></span> <span data-ttu-id="c73fc-136">Si vous souhaitez afficher l’aperçu, vous devez avoir une texture sur laquelle la copier.</span><span class="sxs-lookup"><span data-stu-id="c73fc-136">If you want to render the preview, you need to have a texture to copy it to.</span></span> <span data-ttu-id="c73fc-137">Vous avez également besoin de quelques éléments comme un verrou d’état de connexion, un moyen de stocker l’adresse IP de HoloLens, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="c73fc-137">You also need a few things like a connection state lock, some way of storing the IP address of HoloLens, and so on.</span></span>

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

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a><span data-ttu-id="c73fc-138">Initialiser HolographicStreamerHelpers et se connecter à HoloLens</span><span class="sxs-lookup"><span data-stu-id="c73fc-138">Initialize HolographicStreamerHelpers and connect to HoloLens</span></span>

<span data-ttu-id="c73fc-139">Pour vous connecter à un appareil HoloLens, créez une instance de HolographicStreamerHelpers et connectez-vous à l’adresse IP cible.</span><span class="sxs-lookup"><span data-stu-id="c73fc-139">To connect to a HoloLens device, create an instance of HolographicStreamerHelpers and connect to the target IP address.</span></span> <span data-ttu-id="c73fc-140">Vous devez définir la taille de l’image vidéo pour qu’elle corresponde à la largeur et à la hauteur de l’affichage HoloLens, car la bibliothèque de communication à distance holographique s’attend à ce que les résolutions d’encodeur et de décodeur correspondent exactement.</span><span class="sxs-lookup"><span data-stu-id="c73fc-140">You'll need to set the video frame size to match the HoloLens display width and height, because the Holographic Remoting library expects the encoder and decoder resolutions to match exactly.</span></span>

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

<span data-ttu-id="c73fc-141">La connexion de l’appareil est asynchrone.</span><span class="sxs-lookup"><span data-stu-id="c73fc-141">The device connection is asynchronous.</span></span> <span data-ttu-id="c73fc-142">Votre application doit fournir des gestionnaires d’événements pour les événements de connexion, de déconnexion et d’envoi de frame.</span><span class="sxs-lookup"><span data-stu-id="c73fc-142">Your app needs to provide event handlers for connect, disconnect, and frame send events.</span></span>

<span data-ttu-id="c73fc-143">L’événement OnConnected peut mettre à jour l’interface utilisateur, démarrer le rendu, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="c73fc-143">The OnConnected event can update the UI, start rendering, and so on.</span></span> <span data-ttu-id="c73fc-144">Dans notre exemple de code de bureau, nous mettons à jour le titre de la fenêtre avec un message « connecté ».</span><span class="sxs-lookup"><span data-stu-id="c73fc-144">In our desktop code sample, we update the window title with a "connected" message.</span></span>

```cpp
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

<span data-ttu-id="c73fc-145">L’événement OnDisconnected peut gérer la reconnexion, les mises à jour de l’interface utilisateur, etc.</span><span class="sxs-lookup"><span data-stu-id="c73fc-145">The OnDisconnected event can handle reconnection, UI updates, and so on.</span></span> <span data-ttu-id="c73fc-146">Dans cet exemple, nous nous reconnectons en cas de défaillance temporaire.</span><span class="sxs-lookup"><span data-stu-id="c73fc-146">In this example, we reconnect if there's a transient failure.</span></span>

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

<span data-ttu-id="c73fc-147">Lorsque le composant de communication à distance est prêt à envoyer un frame, votre application vous offre la possibilité d’en faire une copie dans le SendFrameEvent.</span><span class="sxs-lookup"><span data-stu-id="c73fc-147">When the remoting component is ready to send a frame, your app is provided an opportunity to make a copy of it in the SendFrameEvent.</span></span> <span data-ttu-id="c73fc-148">Ici, nous copions le frame dans une chaîne de permutation afin que nous puissions l’afficher dans une fenêtre d’aperçu.</span><span class="sxs-lookup"><span data-stu-id="c73fc-148">Here, we copy the frame to a swap chain so that we can display it in a preview window.</span></span>

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

### <a name="render-holographic-content"></a><span data-ttu-id="c73fc-149">Afficher le contenu holographique</span><span class="sxs-lookup"><span data-stu-id="c73fc-149">Render holographic content</span></span>

<span data-ttu-id="c73fc-150">Pour afficher le contenu à l’aide de la communication à distance, vous devez configurer un IFrameworkView virtuel dans votre application de bureau ou UWP et traiter des frames holographiques à partir de la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="c73fc-150">To render content using remoting, you set up a virtual IFrameworkView within your desktop or UWP app and process holographic frames from remoting.</span></span> <span data-ttu-id="c73fc-151">Toutes les API Windows holographiques sont utilisées de la même façon par cette vue, mais elles sont configurées légèrement différemment.</span><span class="sxs-lookup"><span data-stu-id="c73fc-151">All of the Windows Holographic APIs are used the same way by this view, but it's set up slightly differently.</span></span>

<span data-ttu-id="c73fc-152">Au lieu de les créer vous-même, les composants d’espace et de parole holographiques proviennent de votre classe HolographicRemotingHelpers :</span><span class="sxs-lookup"><span data-stu-id="c73fc-152">Instead of creating them yourself, the holographic space and speech components come from your HolographicRemotingHelpers class:</span></span>

```cpp
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

<span data-ttu-id="c73fc-153">Au lieu d’utiliser une boucle de mise à jour dans une méthode Run, vous fournissez des mises à jour de graduations à partir de la boucle principale de votre application de bureau ou UWP.</span><span class="sxs-lookup"><span data-stu-id="c73fc-153">Instead of using an update loop in a Run method, you provide tick updates from the main loop of your desktop or UWP app.</span></span> <span data-ttu-id="c73fc-154">Cela permet à votre application de bureau ou UWP de rester dans le contrôle du traitement des messages.</span><span class="sxs-lookup"><span data-stu-id="c73fc-154">This allows your desktop or UWP app to remain in control of message processing.</span></span>

```cpp
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

<span data-ttu-id="c73fc-155">La méthode Tick () de la vue de l’application holographique termine une itération de la boucle Update, Draw et present.</span><span class="sxs-lookup"><span data-stu-id="c73fc-155">The holographic app view's Tick() method completes one iteration of the update, draw, present loop.</span></span>

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

<span data-ttu-id="c73fc-156">La vue de mise à jour, le rendu et la boucle d’affichage des applications holographiques sont exactement les mêmes que lorsqu’elles s’exécutent sur HoloLens, sauf que vous avez accès à une quantité beaucoup plus importante de ressources système sur votre ordinateur de bureau.</span><span class="sxs-lookup"><span data-stu-id="c73fc-156">The holographic app view update, render, and present loop are exactly the same as it is when running on HoloLens - except that you have access to a much greater amount of system resources on your desktop PC.</span></span> <span data-ttu-id="c73fc-157">Vous pouvez restituer beaucoup plus de triangles, avoir plus de passes de dessin, faire plus de physique et utiliser des processus x64 pour charger le contenu qui nécessite plus de 2 Go de RAM.</span><span class="sxs-lookup"><span data-stu-id="c73fc-157">You can render many more triangles, have more drawing passes, do more physics, and use x64 processes to load content that requires more than 2 GB of RAM.</span></span>

### <a name="disconnect-and-end-the-remote-session"></a><span data-ttu-id="c73fc-158">Déconnecter et mettre fin à la session à distance</span><span class="sxs-lookup"><span data-stu-id="c73fc-158">Disconnect and end the remote session</span></span>

<span data-ttu-id="c73fc-159">Pour se déconnecter : par exemple, quand l’utilisateur clique sur un bouton de l’interface utilisateur pour déconnecter-appeler Disconnect () sur HolographicStreamerHelpers, puis libérer l’objet.</span><span class="sxs-lookup"><span data-stu-id="c73fc-159">To disconnect - for example, when the user clicks a UI button to disconnect - call Disconnect() on the HolographicStreamerHelpers, and then release the object.</span></span>

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

## <a name="get-the-remoting-player"></a><span data-ttu-id="c73fc-160">Procurez-vous le lecteur de communication à distance</span><span class="sxs-lookup"><span data-stu-id="c73fc-160">Get the remoting player</span></span>

<span data-ttu-id="c73fc-161">Le lecteur Windows holographique Remoting est proposé dans le magasin d’applications Windows sous la forme d’un point de terminaison pour la connexion des applications hôtes à distance.</span><span class="sxs-lookup"><span data-stu-id="c73fc-161">The Windows Holographic remoting player is offered in the Windows app store as an endpoint for remoting host apps to connect to.</span></span> <span data-ttu-id="c73fc-162">Pour obtenir le lecteur Windows holographique Remoting, visitez le Windows App Store à partir de votre HoloLens, recherchez la communication à distance et téléchargez l’application.</span><span class="sxs-lookup"><span data-stu-id="c73fc-162">To get the Windows Holographic remoting player, visit the Windows app store from your HoloLens, search for Remoting, and download the app.</span></span> <span data-ttu-id="c73fc-163">Le lecteur de communication à distance comprend une fonctionnalité permettant d’afficher les statistiques à l’écran, ce qui peut être utile lors du débogage des applications hôtes de communication à distance.</span><span class="sxs-lookup"><span data-stu-id="c73fc-163">The remoting player includes a feature to display statistics on-screen, which can be useful when debugging remoting host apps.</span></span>

## <a name="notes-and-resources"></a><span data-ttu-id="c73fc-164">Remarques et ressources</span><span class="sxs-lookup"><span data-stu-id="c73fc-164">Notes and resources</span></span>

<span data-ttu-id="c73fc-165">La vue de l’application holographique a besoin d’un moyen de fournir à votre application l’appareil Direct3D, qui doit être utilisé pour initialiser l’espace holographique.</span><span class="sxs-lookup"><span data-stu-id="c73fc-165">The holographic app view will need a way to provide your app with the Direct3D device, which must be used to initialize the holographic space.</span></span> <span data-ttu-id="c73fc-166">Votre application doit utiliser ce périphérique Direct3D pour copier et afficher le frame d’aperçu.</span><span class="sxs-lookup"><span data-stu-id="c73fc-166">Your app should use this Direct3D device to copy and display the preview frame.</span></span>

```cpp
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

<span data-ttu-id="c73fc-167">**Exemple de code :** Un exemple complet de [Code de communication à distance holographique](https://github.com/Microsoft/HoloLensCompanionKit) est disponible, qui comprend une vue d’application holographique compatible avec la communication à distance et les projets hôtes de communication à distance pour les ordinateurs de bureau Win32, UWP DirectX et UWP avec XAML.</span><span class="sxs-lookup"><span data-stu-id="c73fc-167">**Code sample:** A complete [Holographic Remoting code sample](https://github.com/Microsoft/HoloLensCompanionKit) is available, which includes a holographic application view that is compatible with remoting and remoting host projects for desktop Win32, UWP DirectX, and UWP with XAML.</span></span> 

<span data-ttu-id="c73fc-168">**Remarque sur le débogage :** La bibliothèque de communication à distance holographique peut lever des exceptions de première chance.</span><span class="sxs-lookup"><span data-stu-id="c73fc-168">**Debugging note:** The Holographic Remoting library can throw first-chance exceptions.</span></span> <span data-ttu-id="c73fc-169">Ces exceptions peuvent être visibles dans les sessions de débogage, en fonction des paramètres d’exception de Visual Studio qui sont actifs à ce moment-là.</span><span class="sxs-lookup"><span data-stu-id="c73fc-169">These exceptions may be visible in debugging sessions, depending on the Visual Studio exception settings that are active at the time.</span></span> <span data-ttu-id="c73fc-170">Ces exceptions sont interceptées en interne par la bibliothèque de communication à distance holographique et peuvent être ignorées.</span><span class="sxs-lookup"><span data-stu-id="c73fc-170">These exceptions are caught internally by the Holographic Remoting library and can be ignored.</span></span>
