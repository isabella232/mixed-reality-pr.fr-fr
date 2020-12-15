---
title: Écriture d’une application distante holographique de communication à distance (WMR)
description: En créant un contenu distant holographique de l’application distante, qui est affiché sur un ordinateur distant, peut être diffusé en continu vers HoloLens 2.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, communication à distance, accès distant holographique, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle, NuGet
ms.openlocfilehash: 5eddcc117008ebc54eac11965592099601880d3e
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530217"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-holographicspace-api"></a><span data-ttu-id="0f756-104">Écriture d’une application distante holographique à distance à l’aide de l’API HolographicSpace</span><span class="sxs-lookup"><span data-stu-id="0f756-104">Writing a Holographic Remoting remote app using the HolographicSpace API</span></span>

>[!IMPORTANT]
><span data-ttu-id="0f756-105">Ce document décrit la création d’une application distante pour HoloLens 2 à l’aide de l' [API HolographicSpace](../native/getting-a-holographicspace.md).</span><span class="sxs-lookup"><span data-stu-id="0f756-105">This document describes the creation of a remote application for HoloLens 2 using the [HolographicSpace API](../native/getting-a-holographicspace.md).</span></span> <span data-ttu-id="0f756-106">Les applications distantes pour **HoloLens (1re génération)** doivent utiliser le package NuGet version **1. x. x**.</span><span class="sxs-lookup"><span data-stu-id="0f756-106">Remote applications for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="0f756-107">Cela implique que les applications distantes écrites pour HoloLens 2 ne sont pas compatibles avec HoloLens 1 et vice versa.</span><span class="sxs-lookup"><span data-stu-id="0f756-107">This implies that remote applications written for HoloLens 2 are not compatible with HoloLens 1 and vice versa.</span></span> <span data-ttu-id="0f756-108">La documentation de HoloLens 1 est disponible [ici](add-holographic-remoting.md).</span><span class="sxs-lookup"><span data-stu-id="0f756-108">The documentation for HoloLens 1 can be found [here](add-holographic-remoting.md).</span></span>

<span data-ttu-id="0f756-109">Les applications de communication à distance holographique peuvent diffuser du contenu diffusé à distance sur des casques immersifs HoloLens 2 et Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="0f756-109">Holographic Remoting apps can stream remotely rendered content to HoloLens 2 and Windows Mixed Reality immersive headsets.</span></span> <span data-ttu-id="0f756-110">Vous pouvez également accéder à davantage de ressources système et intégrer des [vues immersives](../../design/app-views.md) distantes dans des logiciels de poste de travail existants.</span><span class="sxs-lookup"><span data-stu-id="0f756-110">You can also access more system resources and integrate remote [immersive views](../../design/app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="0f756-111">Une application distante reçoit un flux de données d’entrée de HoloLens 2, restitue le contenu dans une vue immersive virtuelle et diffuse en continu des frames de contenu vers HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0f756-111">A remote app receives an input data stream from HoloLens 2, renders content in a virtual immersive view, and streams content frames back to HoloLens 2.</span></span> <span data-ttu-id="0f756-112">La connexion est établie à l’aide du Wi-Fi standard.</span><span class="sxs-lookup"><span data-stu-id="0f756-112">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="0f756-113">La communication à distance holographique est ajoutée à une application de bureau ou UWP via un paquet NuGet.</span><span class="sxs-lookup"><span data-stu-id="0f756-113">Holographic Remoting is added to a desktop or UWP app via a NuGet packet.</span></span> <span data-ttu-id="0f756-114">Du code supplémentaire est nécessaire pour gérer la connexion et le rendu dans une vue immersive.</span><span class="sxs-lookup"><span data-stu-id="0f756-114">Additional code is required which handles the connection and renders in an immersive view.</span></span> <span data-ttu-id="0f756-115">Une connexion à distance classique aura une latence aussi faible que 50 ms de latence.</span><span class="sxs-lookup"><span data-stu-id="0f756-115">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="0f756-116">L’application de lecteur peut signaler la latence en temps réel.</span><span class="sxs-lookup"><span data-stu-id="0f756-116">The player app can report the latency in real time.</span></span>

<span data-ttu-id="0f756-117">Tout le code de cette page et des projets de travail se trouve dans le [référentiel GitHub d’exemples de communication à distance holographique](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span><span class="sxs-lookup"><span data-stu-id="0f756-117">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0f756-118">Prérequis</span><span class="sxs-lookup"><span data-stu-id="0f756-118">Prerequisites</span></span>

<span data-ttu-id="0f756-119">Un bon point de départ est un bureau DirectX opérationnel ou une application UWP qui cible l' [API HolographicSpace](../native/getting-a-holographicspace.md).</span><span class="sxs-lookup"><span data-stu-id="0f756-119">A good starting point is a working DirectX based Desktop or UWP app, which targets the [HolographicSpace API](../native/getting-a-holographicspace.md).</span></span> <span data-ttu-id="0f756-120">Pour plus d’informations, consultez [vue d’ensemble du développement DirectX](../native/directx-development-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0f756-120">For details see [DirectX development overview](../native/directx-development-overview.md).</span></span> <span data-ttu-id="0f756-121">Le [modèle de projet holographique C++](../native/creating-a-holographic-directx-project.md) est un bon point de départ.</span><span class="sxs-lookup"><span data-stu-id="0f756-121">The [C++ holographic project template](../native/creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="0f756-122">Toute application utilisant la communication à distance holographique doit être créée pour utiliser un [cloisonnement](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)multithread.</span><span class="sxs-lookup"><span data-stu-id="0f756-122">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="0f756-123">L’utilisation d’un [cloisonnement à thread unique](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) est prise en charge, mais entraîne des performances non optimales et éventuellement des interruptions pendant la lecture.</span><span class="sxs-lookup"><span data-stu-id="0f756-123">The use of a [single-threaded apartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="0f756-124">Lors de l’utilisation de C++/WinRT [WinRT :: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) un cloisonnement multithread est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="0f756-124">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>



## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="0f756-125">Procurez-vous le package NuGet de communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="0f756-125">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="0f756-126">Les étapes suivantes sont requises pour ajouter le package NuGet à un projet dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0f756-126">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="0f756-127">Ouvrez le projet dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0f756-127">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="0f756-128">Cliquez avec le bouton droit sur le nœud du projet et sélectionnez **gérer les packages NuGet...**</span><span class="sxs-lookup"><span data-stu-id="0f756-128">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="0f756-129">Dans le volet qui s’affiche, sélectionnez **Parcourir** , puis recherchez « accès à distance holographique ».</span><span class="sxs-lookup"><span data-stu-id="0f756-129">In the panel that appears, select **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="0f756-130">Sélectionnez **Microsoft. holographique. Remoting**, assurez-vous de choisir la version la plus récente de **2. x. x** , puis sélectionnez **installer**.</span><span class="sxs-lookup"><span data-stu-id="0f756-130">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and select **Install**.</span></span>
5. <span data-ttu-id="0f756-131">Si la boîte de dialogue **Aperçu** s’affiche, sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="0f756-131">If the **Preview** dialog appears, select **OK**.</span></span>
6. <span data-ttu-id="0f756-132">Sélectionnez **J’accepte** quand la boîte de dialogue du contrat de licence s’affiche.</span><span class="sxs-lookup"><span data-stu-id="0f756-132">Select **I Accept** when the license agreement dialog pops up.</span></span>

>[!NOTE]
><span data-ttu-id="0f756-133">La version **1. x. x** du package NuGet est toujours disponible pour les développeurs qui souhaitent cibler HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="0f756-133">Version **1.x.x** of the NuGet package is still available for developers who want to target HoloLens 1.</span></span> <span data-ttu-id="0f756-134">Pour plus d’informations [, consultez Ajouter une communication à distance holographique (HoloLens (1re génération))](add-holographic-remoting.md).</span><span class="sxs-lookup"><span data-stu-id="0f756-134">For details see [Add Holographic Remoting (HoloLens (1st gen))](add-holographic-remoting.md).</span></span>

## <a name="create-the-remote-context"></a><span data-ttu-id="0f756-135">Créer le contexte distant</span><span class="sxs-lookup"><span data-stu-id="0f756-135">Create the remote context</span></span>

<span data-ttu-id="0f756-136">En guise de première étape, l’application doit créer un contexte distant.</span><span class="sxs-lookup"><span data-stu-id="0f756-136">As a first step the application should create a remote context.</span></span>

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
><span data-ttu-id="0f756-137">La communication à distance holographique fonctionne en remplaçant le runtime Windows Mixed Reality qui fait partie de Windows par un Runtime spécifique à distance.</span><span class="sxs-lookup"><span data-stu-id="0f756-137">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="0f756-138">Cette opération est effectuée lors de la création du contexte distant.</span><span class="sxs-lookup"><span data-stu-id="0f756-138">This is done during the creation of the remote context.</span></span> <span data-ttu-id="0f756-139">Pour cette raison, tout appel sur une API de réalité mixte Windows avant de créer le contexte distant peut entraîner un comportement inattendu.</span><span class="sxs-lookup"><span data-stu-id="0f756-139">For that reason any call on any Windows Mixed Reality API before creating the remote context can result in unexpected behavior.</span></span> <span data-ttu-id="0f756-140">L’approche recommandée consiste à créer le contexte distant le plus tôt possible avant d’interagir avec une API de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="0f756-140">The recommended approach is to create the remote context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="0f756-141">Ne combinez jamais des objets créés ou récupérés par le biais d’une API Windows Mixed Reality avant l’appel à CreateRemoteContext avec des objets créés ou récupérés par la suite.</span><span class="sxs-lookup"><span data-stu-id="0f756-141">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to CreateRemoteContext with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="0f756-142">L’espace holographique doit ensuite être créé.</span><span class="sxs-lookup"><span data-stu-id="0f756-142">Next the holographic space needs to be created.</span></span> <span data-ttu-id="0f756-143">La spécification d’un CoreWindow n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="0f756-143">Specifying a CoreWindow isn't required.</span></span> <span data-ttu-id="0f756-144">Les applications de bureau qui n’ont pas de CoreWindow peuvent simplement passer un ```nullptr``` .</span><span class="sxs-lookup"><span data-stu-id="0f756-144">Desktop apps that don't have a CoreWindow can just pass a ```nullptr```.</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a><span data-ttu-id="0f756-145">Se connecter à l’appareil</span><span class="sxs-lookup"><span data-stu-id="0f756-145">Connect to the device</span></span>

<span data-ttu-id="0f756-146">Lorsque l’application distante est prête pour le rendu du contenu, une connexion à l’appareil Player peut être établie.</span><span class="sxs-lookup"><span data-stu-id="0f756-146">When the remote app is ready for rendering content a connection to the player device can be established.</span></span>

<span data-ttu-id="0f756-147">La connexion peut être effectuée de deux manières.</span><span class="sxs-lookup"><span data-stu-id="0f756-147">Connection can be done in one of two ways.</span></span>
1) <span data-ttu-id="0f756-148">L’application distante se connecte au lecteur qui s’exécute sur l’appareil.</span><span class="sxs-lookup"><span data-stu-id="0f756-148">The remote app connects to the player running on the device.</span></span>
2) <span data-ttu-id="0f756-149">Le lecteur s’exécutant sur l’appareil se connecte à l’application distante.</span><span class="sxs-lookup"><span data-stu-id="0f756-149">The player running on the device connects to the remote app.</span></span>

<span data-ttu-id="0f756-150">Pour établir une connexion de l’application distante à l’appareil Player ```Connect``` , appelez la méthode sur le contexte distant en spécifiant le nom d’hôte et le port.</span><span class="sxs-lookup"><span data-stu-id="0f756-150">To establish a connection from the remote app to the player device call the ```Connect``` method on the remote context specifying the hostname and port.</span></span> <span data-ttu-id="0f756-151">Le port utilisé par le lecteur de communication à distance holographique est **8265**.</span><span class="sxs-lookup"><span data-stu-id="0f756-151">The port used by the Holographic Remoting Player is **8265**.</span></span>

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
><span data-ttu-id="0f756-152">Comme pour toute API/WinRT C++ ```Connect``` peut lever une exception WinRT :: hresult_error qui doit être gérée.</span><span class="sxs-lookup"><span data-stu-id="0f756-152">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

>[!TIP]
><span data-ttu-id="0f756-153">Pour éviter d’utiliser la projection du langage [C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/) ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` , vous pouvez inclure le fichier situé dans le package NuGet de communication à distance holographique.</span><span class="sxs-lookup"><span data-stu-id="0f756-153">To avoid using [C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/) language projection the file ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` located inside the Holographic Remoting NuGet package can be included.</span></span> <span data-ttu-id="0f756-154">Il contient les déclarations des interfaces COM sous-jacentes.</span><span class="sxs-lookup"><span data-stu-id="0f756-154">It contains declarations of the underlying COM interfaces.</span></span> <span data-ttu-id="0f756-155">L’utilisation de C++/WinRT est toutefois recommandée.</span><span class="sxs-lookup"><span data-stu-id="0f756-155">The use of C++/WinRT is recommended though.</span></span>

<span data-ttu-id="0f756-156">L’écoute des connexions entrantes sur l’application distante peut être effectuée en appelant la ```Listen``` méthode.</span><span class="sxs-lookup"><span data-stu-id="0f756-156">Listening for incoming connections on the remote app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="0f756-157">Le port de liaison et le port de transport peuvent être spécifiés au cours de cet appel.</span><span class="sxs-lookup"><span data-stu-id="0f756-157">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="0f756-158">Le port de négociation est utilisé pour le protocole de transfert initial.</span><span class="sxs-lookup"><span data-stu-id="0f756-158">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="0f756-159">Les données sont ensuite envoyées sur le port de transport.</span><span class="sxs-lookup"><span data-stu-id="0f756-159">The data is then sent over the transport port.</span></span> <span data-ttu-id="0f756-160">Par défaut, **8265** et **8266** sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="0f756-160">By default **8265** and **8266** are used.</span></span>

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
><span data-ttu-id="0f756-161">L' ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` intérieur du package NuGet contient une documentation détaillée sur l’API exposée par la communication à distance holographique.</span><span class="sxs-lookup"><span data-stu-id="0f756-161">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="handling-remoting-specific-events"></a><span data-ttu-id="0f756-162">Gestion des événements de communication à distance spécifiques</span><span class="sxs-lookup"><span data-stu-id="0f756-162">Handling Remoting specific events</span></span>

<span data-ttu-id="0f756-163">Le contexte distant expose trois événements, qui sont importants pour surveiller l’état d’une connexion.</span><span class="sxs-lookup"><span data-stu-id="0f756-163">The remote context exposes three events, which are important to monitor the state of a connection.</span></span>
1) <span data-ttu-id="0f756-164">OnConnected : déclenché lorsqu’une connexion à l’appareil a été établie avec succès.</span><span class="sxs-lookup"><span data-stu-id="0f756-164">OnConnected: Triggered when a connection to the device has been successfully established.</span></span>
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) <span data-ttu-id="0f756-165">OnDisconnected : déclenché si une connexion établie est fermée ou si une connexion n’a pas pu être établie.</span><span class="sxs-lookup"><span data-stu-id="0f756-165">OnDisconnected: Triggered if an established connection is closed or a connection couldn't be established.</span></span>
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
3) <span data-ttu-id="0f756-166">OnListening : lors du démarrage de l’écoute des connexions entrantes.</span><span class="sxs-lookup"><span data-stu-id="0f756-166">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

<span data-ttu-id="0f756-167">En outre, l’état de la connexion peut être interrogé à l’aide de la ```ConnectionState``` propriété sur le contexte distant.</span><span class="sxs-lookup"><span data-stu-id="0f756-167">Additionally the connection state can be queried using the ```ConnectionState``` property on the remote context.</span></span>
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a><span data-ttu-id="0f756-168">Gestion des événements vocaux</span><span class="sxs-lookup"><span data-stu-id="0f756-168">Handling speech events</span></span>

<span data-ttu-id="0f756-169">À l’aide de l’interface de reconnaissance vocale à distance, il est possible d’inscrire les déclencheurs vocaux avec HoloLens 2 et de les faire distants à l’application distante.</span><span class="sxs-lookup"><span data-stu-id="0f756-169">Using the remote speech interface it's possible to register speech triggers with HoloLens 2 and have them remoted to the remote application.</span></span>

<span data-ttu-id="0f756-170">Ce membre supplémentaire est requis pour effectuer le suivi de l’état de la voix à distance.</span><span class="sxs-lookup"><span data-stu-id="0f756-170">This additional member is required to track the state of the remote speech.</span></span>

```cpp
winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker m_onRecognizedSpeechRevoker;

```

<span data-ttu-id="0f756-171">Tout d’abord, l’interface de reconnaissance vocale à distance doit être récupérée.</span><span class="sxs-lookup"><span data-stu-id="0f756-171">First the remote speech interface needs to be retrieved.</span></span>

```cpp
if (auto remoteSpeech = m_remoteContext.GetRemoteSpeech())
{
    InitializeSpeechAsync(remoteSpeech, m_onRecognizedSpeechRevoker, weak_from_this());
}
```

<span data-ttu-id="0f756-172">À l’aide d’une méthode d’assistance asynchrone, vous pouvez initialiser la reconnaissance vocale à distance.</span><span class="sxs-lookup"><span data-stu-id="0f756-172">Using an asynchronous helper method you can then initialize the remote speech.</span></span> <span data-ttu-id="0f756-173">Cette opération doit être effectuée de façon asynchrone, car l’initialisation peut prendre beaucoup de temps.</span><span class="sxs-lookup"><span data-stu-id="0f756-173">This should be done asynchronously as initializing might take a considerable amount of time.</span></span> <span data-ttu-id="0f756-174">[Opérations d’accès concurrentiel et asynchrones avec c++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) explique comment créer des fonctions asynchrones avec c++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="0f756-174">[Concurrency and asynchronous operations with C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) explains how to author asynchronous functions with C++/WinRT.</span></span>

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

<span data-ttu-id="0f756-175">Il existe deux façons de spécifier des expressions à reconnaître.</span><span class="sxs-lookup"><span data-stu-id="0f756-175">There are two ways of specifying phrases to be recognized.</span></span>
1) <span data-ttu-id="0f756-176">Spécification à l’intérieur d’un fichier XML de grammaire vocale.</span><span class="sxs-lookup"><span data-stu-id="0f756-176">Specification inside a speech grammar xml file.</span></span> <span data-ttu-id="0f756-177">Pour plus d’informations, consultez [comment créer une grammaire XML de base](https://docs.microsoft.com//previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) .</span><span class="sxs-lookup"><span data-stu-id="0f756-177">See [How to create a basic XML Grammar](https://docs.microsoft.com//previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) for details.</span></span>
2) <span data-ttu-id="0f756-178">Spécifiez en les passant dans le vecteur du dictionnaire à ```ApplyParameters``` .</span><span class="sxs-lookup"><span data-stu-id="0f756-178">Specify by passing them inside the dictionary vector to ```ApplyParameters```.</span></span>

<span data-ttu-id="0f756-179">À l’intérieur du rappel OnRecognizedSpeech, les événements vocaux peuvent ensuite être traités :</span><span class="sxs-lookup"><span data-stu-id="0f756-179">Inside the OnRecognizedSpeech callback, the speech events can then be processed:</span></span>

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

## <a name="preview-streamed-content-locally"></a><span data-ttu-id="0f756-180">Afficher un aperçu du contenu diffusé en continu localement</span><span class="sxs-lookup"><span data-stu-id="0f756-180">Preview streamed content locally</span></span>

<span data-ttu-id="0f756-181">Pour afficher le même contenu dans l’application distante qui est envoyé à l’appareil, l' ```OnSendFrame``` événement du contexte distant peut être utilisé.</span><span class="sxs-lookup"><span data-stu-id="0f756-181">To display the same content in the remote app that is sent to the device the ```OnSendFrame``` event of the remote context can be used.</span></span> <span data-ttu-id="0f756-182">L' ```OnSendFrame``` événement est déclenché chaque fois que la bibliothèque de communication à distance holographique envoie le frame actuel au périphérique distant.</span><span class="sxs-lookup"><span data-stu-id="0f756-182">The ```OnSendFrame``` event is triggered every time the Holographic Remoting library sends the current frame to the remote device.</span></span> <span data-ttu-id="0f756-183">C’est le moment idéal pour prendre le contenu et le configurer dans la fenêtre du bureau ou UWP.</span><span class="sxs-lookup"><span data-stu-id="0f756-183">This is the ideal time to take the content and also blit it into the desktop or UWP window.</span></span>

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

## <a name="depth-reprojection"></a><span data-ttu-id="0f756-184">Reprojection de profondeur</span><span class="sxs-lookup"><span data-stu-id="0f756-184">Depth Reprojection</span></span>

<span data-ttu-id="0f756-185">À partir de la version [2.1.0](holographic-remoting-version-history.md#v2.1.0), la communication à distance holographique prend en charge la [reprojection de profondeur](hologram-stability.md#reprojection).</span><span class="sxs-lookup"><span data-stu-id="0f756-185">Starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0), Holographic Remoting supports [Depth Reprojection](hologram-stability.md#reprojection).</span></span> <span data-ttu-id="0f756-186">Cela requiert que la mémoire tampon de couleur et la mémoire tampon de profondeur soient diffusées de l’application distante vers HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0f756-186">This requires both the color buffer and depth buffer to be streamed from the Remote application to the HoloLens 2.</span></span> <span data-ttu-id="0f756-187">Par défaut, la diffusion en continu de la mémoire tampon est activée et configurée pour utiliser la moitié de la résolution de la mémoire tampon de couleur.</span><span class="sxs-lookup"><span data-stu-id="0f756-187">By default depth buffer streaming is enabled and configured to use half the resolution of the color buffer.</span></span> <span data-ttu-id="0f756-188">Vous pouvez modifier cette valeur comme suit :</span><span class="sxs-lookup"><span data-stu-id="0f756-188">This can be changed as follows:</span></span>

```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

// Configure for half-resolution depth.
m_remoteContext.ConfigureDepthVideoStream(DepthBufferStreamResolution::Half_Resolution);

```

<span data-ttu-id="0f756-189">Notez que, si les valeurs par défaut ne doivent pas être utilisées, ```ConfigureDepthVideoStream``` doivent être appelées avant d’établir une connexion à HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0f756-189">Note, if default values should not be used ```ConfigureDepthVideoStream``` must be called before establishing a connection to the HoloLens 2.</span></span> <span data-ttu-id="0f756-190">Le meilleur emplacement est juste après avoir créé le contexte distant.</span><span class="sxs-lookup"><span data-stu-id="0f756-190">The best place is right after you have created the remote context.</span></span> <span data-ttu-id="0f756-191">Les valeurs possibles pour DepthBufferStreamResolution sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="0f756-191">Possible values for DepthBufferStreamResolution are:</span></span>

* <span data-ttu-id="0f756-192">Full_Resolution</span><span class="sxs-lookup"><span data-stu-id="0f756-192">Full_Resolution</span></span>
* <span data-ttu-id="0f756-193">Half_Resolution</span><span class="sxs-lookup"><span data-stu-id="0f756-193">Half_Resolution</span></span>
* <span data-ttu-id="0f756-194">Quarter_Resolution</span><span class="sxs-lookup"><span data-stu-id="0f756-194">Quarter_Resolution</span></span>
* <span data-ttu-id="0f756-195">Désactivé (ajouté avec la version [2.1.3](holographic-remoting-version-history.md#v2.1.3) et, s’il n’est utilisé, aucun flux vidéo de profondeur supplémentaire n’est créé)</span><span class="sxs-lookup"><span data-stu-id="0f756-195">Disabled (added with version [2.1.3](holographic-remoting-version-history.md#v2.1.3) and if used no additional depth video stream is created)</span></span>

<span data-ttu-id="0f756-196">Gardez à l’esprit que l’utilisation d’une mémoire tampon de profondeur de résolution complète affecte également les besoins en bande passante et doit être comptabilisée dans la valeur de bande passante maximale que vous fournissez à ```CreateRemoteContext``` .</span><span class="sxs-lookup"><span data-stu-id="0f756-196">Keep in mind that using a full resolution depth buffer also affects bandwidth requirements and needs to be accounted for in the maximum bandwidth value you provide to ```CreateRemoteContext```.</span></span>

<span data-ttu-id="0f756-197">À côté de la configuration de la résolution, vous devez également valider un tampon de profondeur à l’aide de [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span><span class="sxs-lookup"><span data-stu-id="0f756-197">Beside configuring the resolution, you also have to commit a depth buffer via [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span></span>

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

<span data-ttu-id="0f756-198">Pour vérifier si la reprojection de profondeur fonctionne correctement sur HoloLens 2, vous pouvez activer un visualiseur de profondeur via le portail de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="0f756-198">To verify if depth reprojection is correctly working on HoloLens 2, you can enable a depth visualizer via the Device Portal.</span></span> <span data-ttu-id="0f756-199">Pour plus d’informations, voir vérification de la [profondeur définie correctement](hologram-stability.md#verifying-depth-is-set-correctly) .</span><span class="sxs-lookup"><span data-stu-id="0f756-199">See [Verifying Depth is Set Correctly](hologram-stability.md#verifying-depth-is-set-correctly) for details.</span></span>

## <a name="optional-custom-data-channels"></a><span data-ttu-id="0f756-200">Facultatif : canaux de données personnalisés</span><span class="sxs-lookup"><span data-stu-id="0f756-200">Optional: Custom data channels</span></span>

<span data-ttu-id="0f756-201">Les canaux de données personnalisés peuvent être utilisés pour envoyer des données utilisateur sur la connexion de communication à distance déjà établie.</span><span class="sxs-lookup"><span data-stu-id="0f756-201">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="0f756-202">Pour plus d’informations, consultez [canaux de données personnalisés](holographic-remoting-custom-data-channels.md) .</span><span class="sxs-lookup"><span data-stu-id="0f756-202">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="0f756-203">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f756-203">See Also</span></span>
* [<span data-ttu-id="0f756-204">Écriture d’une application de lecteur de communication à distance holographique personnalisée</span><span class="sxs-lookup"><span data-stu-id="0f756-204">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="0f756-205">Canaux de données de communication à distance holographique personnalisés</span><span class="sxs-lookup"><span data-stu-id="0f756-205">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="0f756-206">Établissement d’une connexion sécurisée avec la communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="0f756-206">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="0f756-207">Résolution des problèmes et limitations de la communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="0f756-207">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="0f756-208">Termes du contrat de licence de la communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="0f756-208">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="0f756-209">Déclaration de confidentialité Microsoft</span><span class="sxs-lookup"><span data-stu-id="0f756-209">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
