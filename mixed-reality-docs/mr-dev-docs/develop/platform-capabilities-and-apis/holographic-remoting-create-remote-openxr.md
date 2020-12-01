---
title: Écriture d’une application distante holographique de communication à distance (OpenXR)
description: En créant une application distante de communication à distance holographique, le contenu distant, qui est affiché sur un ordinateur distant, peut être diffusé en continu vers HoloLens 2. Cet article explique comment procéder.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, communication à distance, accès distant holographique, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle, NuGet
ms.openlocfilehash: 7e46c67e7dac08759890fa66d540379991414aad
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96469496"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-openxr-api"></a><span data-ttu-id="1332d-105">Écriture d’une application distante holographique à distance à l’aide de l’API OpenXR</span><span class="sxs-lookup"><span data-stu-id="1332d-105">Writing a Holographic Remoting remote app using the OpenXR API</span></span>

>[!IMPORTANT]
><span data-ttu-id="1332d-106">Ce document décrit la création d’une application distante pour les casques HoloLens 2 et Windows Mixed Reality à l’aide de l' [API OpenXR](../native/openxr.md).</span><span class="sxs-lookup"><span data-stu-id="1332d-106">This document describes the creation of a remote application for HoloLens 2 and Windows Mixed Reality headsets using the [OpenXR API](../native/openxr.md).</span></span> <span data-ttu-id="1332d-107">Les applications distantes pour **HoloLens (1re génération)** doivent utiliser le package NuGet version **1. x. x**.</span><span class="sxs-lookup"><span data-stu-id="1332d-107">Remote applications for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="1332d-108">Cela implique que les applications distantes écrites pour HoloLens 2 ne sont pas compatibles avec HoloLens 1 et vice versa.</span><span class="sxs-lookup"><span data-stu-id="1332d-108">This implies that remote applications written for HoloLens 2 are not compatible with HoloLens 1 and vice versa.</span></span> <span data-ttu-id="1332d-109">La documentation de HoloLens 1 est disponible [ici](add-holographic-remoting.md).</span><span class="sxs-lookup"><span data-stu-id="1332d-109">The documentation for HoloLens 1 can be found [here](add-holographic-remoting.md).</span></span>

<span data-ttu-id="1332d-110">En créant une application distante holographique à distance, le contenu distant rendu sur une machine distante peut être transmis à HoloLens 2 et à des appareils immersifs comme des casques Windows mixtes.</span><span class="sxs-lookup"><span data-stu-id="1332d-110">By creating a Holographic Remoting remote app, remote content that is rendered on a remote machine can be streamed to HoloLens 2 and immersive devices like Windows Mixed Reality headsets.</span></span> <span data-ttu-id="1332d-111">Cet article explique comment procéder.</span><span class="sxs-lookup"><span data-stu-id="1332d-111">This article describes how this can be achieved.</span></span> <span data-ttu-id="1332d-112">Tout le code de cette page et des projets de travail se trouve dans le [référentiel GitHub d’exemples de communication à distance holographique](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span><span class="sxs-lookup"><span data-stu-id="1332d-112">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="1332d-113">La communication à distance holographique permet à une application de cibler des casques HoloLens 2 et Windows Mixed Reality avec un contenu holographique rendu sur un PC de bureau ou sur un appareil UWP tel que le Xbox, permettant d’accéder à davantage de ressources système et d’intégrer des [vues immersives](../../design/app-views.md) distantes à des logiciels de bureau existants.</span><span class="sxs-lookup"><span data-stu-id="1332d-113">Holographic remoting allows an app to target HoloLens 2 and Windows Mixed Reality headsets with holographic content rendered on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources and making it possible to integrate remote [immersive views](../../design/app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="1332d-114">Une application distante reçoit un flux de données d’entrée de HoloLens 2, restitue le contenu dans une vue immersive virtuelle et diffuse en continu des frames de contenu vers HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1332d-114">A remote app receives an input data stream from HoloLens 2, renders content in a virtual immersive view, and streams content frames back to HoloLens 2.</span></span> <span data-ttu-id="1332d-115">La connexion est établie à l’aide du Wi-Fi standard.</span><span class="sxs-lookup"><span data-stu-id="1332d-115">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="1332d-116">La communication à distance holographique est ajoutée à une application de bureau ou UWP via un paquet NuGet.</span><span class="sxs-lookup"><span data-stu-id="1332d-116">Holographic Remoting is added to a desktop or UWP app via a NuGet packet.</span></span> <span data-ttu-id="1332d-117">Du code supplémentaire est nécessaire pour gérer la connexion et le rendu dans une vue immersive.</span><span class="sxs-lookup"><span data-stu-id="1332d-117">Additional code is required which handles the connection and renders in an immersive view.</span></span>

<span data-ttu-id="1332d-118">Une connexion à distance classique aura une latence aussi faible que 50 ms de latence.</span><span class="sxs-lookup"><span data-stu-id="1332d-118">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="1332d-119">L’application de lecteur peut signaler la latence en temps réel.</span><span class="sxs-lookup"><span data-stu-id="1332d-119">The player app can report the latency in real-time.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1332d-120">Prérequis</span><span class="sxs-lookup"><span data-stu-id="1332d-120">Prerequisites</span></span>

<span data-ttu-id="1332d-121">Un bon point de départ est une application de bureau ou UWP basée sur un OpenXR fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="1332d-121">A good starting point is a working OpenXR based Desktop or UWP app.</span></span> <span data-ttu-id="1332d-122">Pour plus d’informations, consultez [prise en main de OpenXR](../native/openxr-getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="1332d-122">For details see [Getting started with OpenXR](../native/openxr-getting-started.md).</span></span>

>[!IMPORTANT]
><span data-ttu-id="1332d-123">Toute application utilisant la communication à distance holographique doit être créée pour utiliser un [cloisonnement](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)multithread.</span><span class="sxs-lookup"><span data-stu-id="1332d-123">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="1332d-124">L’utilisation d’un [cloisonnement à thread unique](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) est prise en charge, mais entraîne des performances non optimales et éventuellement des interruptions pendant la lecture.</span><span class="sxs-lookup"><span data-stu-id="1332d-124">The use of a [single-threaded apartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="1332d-125">Lors de l’utilisation de C++/WinRT [WinRT :: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) un cloisonnement multithread est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="1332d-125">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>

## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="1332d-126">Procurez-vous le package NuGet de communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="1332d-126">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="1332d-127">Les étapes suivantes sont requises pour ajouter le package NuGet à un projet dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1332d-127">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="1332d-128">Ouvrez le projet dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1332d-128">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="1332d-129">Cliquez avec le bouton droit sur le nœud du projet et sélectionnez **gérer les packages NuGet...**</span><span class="sxs-lookup"><span data-stu-id="1332d-129">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="1332d-130">Dans le volet qui s’affiche, cliquez sur **Parcourir** , puis recherchez « accès distant holographique ».</span><span class="sxs-lookup"><span data-stu-id="1332d-130">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="1332d-131">Sélectionnez **Microsoft. holographique. Remoting. OpenXr**, assurez-vous de choisir la version la plus récente de **2. x. x** , puis cliquez sur **installer**.</span><span class="sxs-lookup"><span data-stu-id="1332d-131">Select **Microsoft.Holographic.Remoting.OpenXr**, ensure to pick the latest **2.x.x** version and click **Install**.</span></span>
5. <span data-ttu-id="1332d-132">Si la boîte de dialogue **Aperçu** s’affiche, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="1332d-132">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="1332d-133">La boîte de dialogue suivante qui s’affiche est le contrat de licence.</span><span class="sxs-lookup"><span data-stu-id="1332d-133">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="1332d-134">Cliquez sur **J’accepte** pour accepter le contrat de licence.</span><span class="sxs-lookup"><span data-stu-id="1332d-134">Click on **I Accept** to accept the license agreement.</span></span>
7. <span data-ttu-id="1332d-135">Répétez les étapes 3 à 6 pour les packages NuGet suivants : OpenXR. Headers, OpenXR. Loader</span><span class="sxs-lookup"><span data-stu-id="1332d-135">Repeat the steps 3 to 6 for the following NuGet Packages: OpenXR.Headers, OpenXR.Loader</span></span>

>[!NOTE]
><span data-ttu-id="1332d-136">La version **1. x. x** du package NuGet est toujours disponible pour les développeurs qui souhaitent cibler HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="1332d-136">Version **1.x.x** of the NuGet package is still available for developers who want to target HoloLens 1.</span></span> <span data-ttu-id="1332d-137">Pour plus d’informations [, consultez Ajouter une communication à distance holographique (HoloLens (1re génération))](add-holographic-remoting.md).</span><span class="sxs-lookup"><span data-stu-id="1332d-137">For details see [Add Holographic Remoting (HoloLens (1st gen))](add-holographic-remoting.md).</span></span>

## <a name="select-the-holographic-remoting-openxr-runtime"></a><span data-ttu-id="1332d-138">Sélectionner le runtime OpenXR Remoting holographique</span><span class="sxs-lookup"><span data-stu-id="1332d-138">Select the Holographic Remoting OpenXR runtime</span></span>

<span data-ttu-id="1332d-139">La première étape que vous devez effectuer dans votre application distante consiste à sélectionner le runtime OpenXR de communication à distance holographique qui fait partie du package NuGet Microsoft. holographique. Remoting. OpenXr.</span><span class="sxs-lookup"><span data-stu-id="1332d-139">The first step you need to do in your remote app is to select the Holographic Remoting OpenXR runtime which is part of the Microsoft.Holographic.Remoting.OpenXr NuGet package.</span></span> <span data-ttu-id="1332d-140">Pour ce faire, vous pouvez définir la ```XR_RUNTIME_JSON``` variable d’environnement sur le chemin d’accès de l' RemotingXR.jssur le fichier dans votre application.</span><span class="sxs-lookup"><span data-stu-id="1332d-140">You can do this by setting the ```XR_RUNTIME_JSON``` environment variable to the path of the RemotingXR.json file within your app.</span></span> <span data-ttu-id="1332d-141">Cette variable d’environnement est utilisée par le chargeur OpenXR pour ne pas utiliser le runtime OpenXR par défaut du système, mais plutôt rediriger vers le runtime OpenXR de communication à distance holographique.</span><span class="sxs-lookup"><span data-stu-id="1332d-141">This environment variable is used by the OpenXR loader to not use the system default OpenXR runtime but instead redirect to the Holographic Remoting OpenXR runtime.</span></span> <span data-ttu-id="1332d-142">Lorsque vous utilisez le package NuGet Microsoft. holographique. Remoting. OpenXr, le fichier RemotingXR.jsest automatiquement copié pendant la compilation dans le dossier de sortie, de sorte que la sélection du runtime OpenXR ressemble généralement à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="1332d-142">When using the Microsoft.Holographic.Remoting.OpenXr NuGet package the RemotingXR.json file is automatically copied during compilation to the output folder, thus the OpenXR runtime selection typically looks as follows.</span></span>

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

## <a name="create-xrinstance-with-holographic-remoting-extension"></a><span data-ttu-id="1332d-143">Créer XrInstance avec l’extension de communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="1332d-143">Create XrInstance with Holographic Remoting Extension</span></span>

<span data-ttu-id="1332d-144">La première étape d’une application OpenXR classique est de sélectionner les extensions OpenXR et de créer un XrInstance.</span><span class="sxs-lookup"><span data-stu-id="1332d-144">The first step a typical OpenXR app is supposed to do is to select OpenXR extensions and create a XrInstance.</span></span> <span data-ttu-id="1332d-145">La spécification OpenXR Core ne fournit pas d’API spécifique à distance.</span><span class="sxs-lookup"><span data-stu-id="1332d-145">The OpenXR core specification does not provide any remoting specific API.</span></span> <span data-ttu-id="1332d-146">Pour cette raison, la communication à distance holographique introduit sa propre extension OpenXR nommée ```XR_MSFT_holographic_remoting``` .</span><span class="sxs-lookup"><span data-stu-id="1332d-146">For that reason Holographic Remoting introduces it's own OpenXR extension named ```XR_MSFT_holographic_remoting```.</span></span> <span data-ttu-id="1332d-147">Assurez-vous que lorsque vous appelez xrCreateInstance ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` , est inclus dans le XrInstanceCreateInfo.</span><span class="sxs-lookup"><span data-stu-id="1332d-147">Ensure that when you call xrCreateInstance the ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` is included in the XrInstanceCreateInfo.</span></span>

>[!TIP]
><span data-ttu-id="1332d-148">Par défaut, le contenu rendu de votre application est diffusé uniquement sur le lecteur de communication à distance holographique s’exécutant sur un HoloLens 2 ou sur un casque Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="1332d-148">By default the rendered content of your app is only streamed to the Holographic Remoting player either running on a HoloLens 2 or on a Windows Mixed Reality headsets.</span></span> <span data-ttu-id="1332d-149">Pour afficher également le contenu rendu sur l’ordinateur distant, par le biais d’une chaîne d’échange d’une fenêtre, par exemple, la communication à distance holographique fournit une deuxième extension OpenXR nommée ```XR_MSFT_holographic_remoting_frame_mirroring``` .</span><span class="sxs-lookup"><span data-stu-id="1332d-149">To also display the rendered content on the remote PC, via a swap-chain of a window for instance, Holographic Remoting provides a second OpenXR extension named ```XR_MSFT_holographic_remoting_frame_mirroring```.</span></span> <span data-ttu-id="1332d-150">Veillez également à activer cette extension ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME``` au cas où vous souhaiteriez utiliser cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="1332d-150">Ensure to also enable this extension using ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME``` in case you want to use that functionality.</span></span>

>[!IMPORTANT]
><span data-ttu-id="1332d-151">Pour en savoir plus sur l’API d’extension OpenXR de communication à distance holographique, consultez la [spécification](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) qui se trouve dans le [référentiel GitHub des exemples de communication à distance holographique](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span><span class="sxs-lookup"><span data-stu-id="1332d-151">To learn about the Holographic Remoting OpenXR extension API, check out the [specification](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) which can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

## <a name="connect-to-the-device"></a><span data-ttu-id="1332d-152">Se connecter à l’appareil</span><span class="sxs-lookup"><span data-stu-id="1332d-152">Connect to the device</span></span>

<span data-ttu-id="1332d-153">Une fois que votre application distante a créé les XrInstance et interrogé les XrSystemId via xrGetSystem, une connexion à l’appareil Player peut être établie.</span><span class="sxs-lookup"><span data-stu-id="1332d-153">After your remote app has created the XrInstance and queried the XrSystemId via xrGetSystem a connection to the player device can be established.</span></span>

>[!WARNING]
> <span data-ttu-id="1332d-154">Le runtime OpenXR de communication à distance holographique est uniquement en mesure de fournir des données spécifiques à l’appareil, telles que des configurations d’affichage ou des modes de fusion d’environnement, après l’établissement d’une connexion.</span><span class="sxs-lookup"><span data-stu-id="1332d-154">The Holographic Remoting OpenXR runtime is only able to provide device specific data such as view configurations or environment blend modes after a connection has been established.</span></span> <span data-ttu-id="1332d-155">```xrEnumerateViewConfigurations```, ```xrEnumerateViewConfigurationViews``` , ```xrGetViewConfigurationProperties``` , ```xrEnumerateEnvironmentBlendModes``` et ```xrGetSystemProperties``` fournissent les valeurs par défaut, en fonction de ce que vous obtiendriez en général si vous vous connectez à un joueur s’exécutant sur un HoloLens 2, avant d’être entièrement connecté.</span><span class="sxs-lookup"><span data-stu-id="1332d-155">```xrEnumerateViewConfigurations```, ```xrEnumerateViewConfigurationViews```, ```xrGetViewConfigurationProperties```, ```xrEnumerateEnvironmentBlendModes```, and ```xrGetSystemProperties``` will give you default values, matching what you would typically get if you connect to a player running on a HoloLens 2, before being fully connected.</span></span>
<span data-ttu-id="1332d-156">Il est fortement recommandé de ne pas appeler ces méthodes avant qu’une connexion ait été établie.</span><span class="sxs-lookup"><span data-stu-id="1332d-156">It is strongly recommended to not call these methods before a connection has been established.</span></span> <span data-ttu-id="1332d-157">La suggestion utilise ces méthodes une fois que le XrSession a été créé avec succès et que l’état de session est au moins XR_SESSION_STATE_READY.</span><span class="sxs-lookup"><span data-stu-id="1332d-157">The suggestion is use these methods after the XrSession has been successfully created and the session state is at least XR_SESSION_STATE_READY.</span></span>

<span data-ttu-id="1332d-158">Les propriétés générales telles que le débit maximal, l’audio activé, le codec vidéo ou la résolution de flux de mémoire tampon de profondeur peuvent être configurées via ```xrRemotingSetContextPropertiesMSFT``` comme suit.</span><span class="sxs-lookup"><span data-stu-id="1332d-158">General properties such as max bitrate, audio enabled, video codec, or depth buffer stream resolution can be configured via ```xrRemotingSetContextPropertiesMSFT``` as follows.</span></span>

```cpp
XrRemotingRemoteContextPropertiesMSFT contextProperties;
contextProperties = XrRemotingRemoteContextPropertiesMSFT{static_cast<XrStructureType>(XR_TYPE_REMOTING_REMOTE_CONTEXT_PROPERTIES_MSFT)};
contextProperties.enableAudio = false;
contextProperties.maxBitrateKbps = 20000;
contextProperties.videoCodec = XR_REMOTING_VIDEO_CODEC_H265_MSFT;
contextProperties.depthBufferStreamResolution = XR_REMOTING_DEPTH_BUFFER_STREAM_RESOLUTION_HALF_MSFT;
xrRemotingSetContextPropertiesMSFT(m_instance.Get(), m_systemId, &contextProperties);
```

<span data-ttu-id="1332d-159">La connexion peut être effectuée de deux manières.</span><span class="sxs-lookup"><span data-stu-id="1332d-159">The connection can be done in one of two ways.</span></span>
1) <span data-ttu-id="1332d-160">L’application distante se connecte au lecteur qui s’exécute sur l’appareil.</span><span class="sxs-lookup"><span data-stu-id="1332d-160">The remote app connects to the player running on the device.</span></span>
2) <span data-ttu-id="1332d-161">Le lecteur s’exécutant sur l’appareil se connecte à l’application distante.</span><span class="sxs-lookup"><span data-stu-id="1332d-161">The player running on the device connects to the remote app.</span></span>

<span data-ttu-id="1332d-162">Pour établir une connexion de l’application distante à l’appareil Player ```xrRemotingConnectMSFT``` , appelez la méthode en spécifiant le nom d’hôte et le port via la  ```XrRemotingConnectInfoMSFT``` structure.</span><span class="sxs-lookup"><span data-stu-id="1332d-162">To establish a connection from the remote app to the player device call the ```xrRemotingConnectMSFT``` method specifying the hostname and port via the  ```XrRemotingConnectInfoMSFT``` structure.</span></span> <span data-ttu-id="1332d-163">Le port utilisé par le lecteur de communication à distance holographique est **8265**.</span><span class="sxs-lookup"><span data-stu-id="1332d-163">The port used by the Holographic Remoting Player is **8265**.</span></span>

```cpp
XrRemotingConnectInfoMSFT connectInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_CONNECT_INFO_MSFT)};
connectInfo.remoteHostName = "192.168.x.x";
connectInfo.remotePort = 8265;
connectInfo.secureConnection = false;
xrRemotingConnectMSFT(m_instance.Get(), m_systemId, &connectInfo);
```

<span data-ttu-id="1332d-164">L’écoute des connexions entrantes sur l’application distante peut être effectuée en appelant la ```xrRemotingListenMSFT``` méthode.</span><span class="sxs-lookup"><span data-stu-id="1332d-164">Listening for incoming connections on the remote app can be done by calling the ```xrRemotingListenMSFT``` method.</span></span> <span data-ttu-id="1332d-165">Le port de liaison et le port de transport peuvent être spécifiés via la ```XrRemotingListenInfoMSFT``` structure.</span><span class="sxs-lookup"><span data-stu-id="1332d-165">Both the handshake port and transport port can be specified via the ```XrRemotingListenInfoMSFT``` structure.</span></span> <span data-ttu-id="1332d-166">Le port de négociation est utilisé pour le protocole de transfert initial.</span><span class="sxs-lookup"><span data-stu-id="1332d-166">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="1332d-167">Les données sont ensuite envoyées sur le port de transport.</span><span class="sxs-lookup"><span data-stu-id="1332d-167">The data is then send over the transport port.</span></span> <span data-ttu-id="1332d-168">Par défaut, **8265** et **8266** sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="1332d-168">By default **8265** and **8266** are used.</span></span>

```cpp
XrRemotingListenInfoMSFT listenInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_LISTEN_INFO_MSFT)};
listenInfo.listenInterface = "0.0.0.0";
listenInfo.handshakeListenPort = 8265;
listenInfo.transportListenPort = 8266;
listenInfo.secureConnection = false;
xrRemotingListenMSFT(m_instance.Get(), m_systemId, &listenInfo);
```

<span data-ttu-id="1332d-169">L’état de la connexion doit être déconnecté lorsque vous appelez ```xrRemotingConnectMSFT``` ou ```xrRemotingListenMSFT``` .</span><span class="sxs-lookup"><span data-stu-id="1332d-169">The connection state must be disconnected when you call ```xrRemotingConnectMSFT``` or ```xrRemotingListenMSFT```.</span></span> <span data-ttu-id="1332d-170">Vous pouvez obtenir l’état de la connexion à tout moment après avoir créé un XrInstance et interrogé pour XrSystemId via ```xrRemotingGetConnectionStateMSFT``` .</span><span class="sxs-lookup"><span data-stu-id="1332d-170">You can get the connection state at any point after you have created a XrInstance and queried for the XrSystemId via ```xrRemotingGetConnectionStateMSFT```.</span></span>

```cpp
XrRemotingConnectionStateMSFT connectionState;
xrRemotingGetConnectionStateMSFT(m_instance.Get(), m_systemId, &connectionState, nullptr);
```

<span data-ttu-id="1332d-171">Les États de connexion disponibles sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="1332d-171">Available connection states are:</span></span>
- <span data-ttu-id="1332d-172">XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT</span><span class="sxs-lookup"><span data-stu-id="1332d-172">XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT</span></span>
- <span data-ttu-id="1332d-173">XR_REMOTING_CONNECTION_STATE_CONNECTING_MSFT</span><span class="sxs-lookup"><span data-stu-id="1332d-173">XR_REMOTING_CONNECTION_STATE_CONNECTING_MSFT</span></span>
- <span data-ttu-id="1332d-174">XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT</span><span class="sxs-lookup"><span data-stu-id="1332d-174">XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT</span></span>

>[!IMPORTANT]
> <span data-ttu-id="1332d-175">```xrRemotingConnectMSFT``` ou ```xrRemotingListenMSFT``` doit être appelé avant d’essayer de créer un XrSession via xrCreateSession.</span><span class="sxs-lookup"><span data-stu-id="1332d-175">```xrRemotingConnectMSFT``` or ```xrRemotingListenMSFT``` must be called before trying to create a XrSession via xrCreateSession.</span></span> <span data-ttu-id="1332d-176">Si vous essayez de créer un XrSession alors que l’état de la connexion est ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` la création de la session réussie, mais que l’état de la session passera immédiatement à XR_SESSION_STATE_LOSS_PENDING.</span><span class="sxs-lookup"><span data-stu-id="1332d-176">If you try to create a XrSession while the connection state is ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` the session creation will succeed but the session state will immediately transition to XR_SESSION_STATE_LOSS_PENDING.</span></span>

<span data-ttu-id="1332d-177">L’implémentation de la communication à distance holographique de ```xrCreateSession``` prend en charge l’attente de l’établissement d’une connexion.</span><span class="sxs-lookup"><span data-stu-id="1332d-177">Holographic Remoting's implementation of ```xrCreateSession``` supports waiting for a connection to be established.</span></span> <span data-ttu-id="1332d-178">Vous pouvez appeler ```xrRemotingConnectMSFT``` ou ```xrRemotingListenMSFT``` immédiatement suivi d’un appel à ```xrCreateSession``` qui bloque et attend qu’une connexion soit établie.</span><span class="sxs-lookup"><span data-stu-id="1332d-178">You can call ```xrRemotingConnectMSFT``` or ```xrRemotingListenMSFT``` immediately followed by a call to ```xrCreateSession``` which will block and wait for a connection to be established.</span></span> <span data-ttu-id="1332d-179">Le délai d’attente est fixé à 10 secondes.</span><span class="sxs-lookup"><span data-stu-id="1332d-179">The timeout is fixed to 10 seconds.</span></span> <span data-ttu-id="1332d-180">Si une connexion peut être établie dans ce délai, la création de XrSession est effectuée et l’état de session passera à XR_SESSION_STATE_READY.</span><span class="sxs-lookup"><span data-stu-id="1332d-180">If a connection can be established within this time the XrSession creation will succeed and the session state will transition to XR_SESSION_STATE_READY.</span></span> <span data-ttu-id="1332d-181">Dans le cas où aucune connexion ne peut être établie, la création de session s’effectue également, mais passe immédiatement à XR_SESSION_STATE_LOSS_PENDING.</span><span class="sxs-lookup"><span data-stu-id="1332d-181">In case no connection can be established the session creation also succeeds but immediately transitions to XR_SESSION_STATE_LOSS_PENDING.</span></span>

<span data-ttu-id="1332d-182">En général, l’état de la connexion est couple à l’État XrSession.</span><span class="sxs-lookup"><span data-stu-id="1332d-182">In general the connection state is couple with the XrSession state.</span></span> <span data-ttu-id="1332d-183">Toute modification apportée à l’état de la connexion affecte également l’état de la session.</span><span class="sxs-lookup"><span data-stu-id="1332d-183">Any change to the connection state also affects the session state.</span></span> <span data-ttu-id="1332d-184">Par exemple, si l’état de la connexion passe de `XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT` à ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` l’état de session passera également à XR_SESSION_STATE_LOSS_PENDING.</span><span class="sxs-lookup"><span data-stu-id="1332d-184">For instance, if the connection state switches from `XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT` to ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` the session state will transition to XR_SESSION_STATE_LOSS_PENDING as well.</span></span>

## <a name="handling-remoting-specific-events"></a><span data-ttu-id="1332d-185">Gestion des événements de communication à distance spécifiques</span><span class="sxs-lookup"><span data-stu-id="1332d-185">Handling Remoting specific events</span></span>

<span data-ttu-id="1332d-186">Le runtime OpenXR de la communication à distance holographique expose trois événements qui sont importants pour surveiller l’état d’une connexion.</span><span class="sxs-lookup"><span data-stu-id="1332d-186">The Holographic Remoting OpenXR runtime exposes three events which are important to monitor the state of a connection.</span></span>
1) <span data-ttu-id="1332d-187">```XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT```: Déclenché lorsqu’une connexion à l’appareil a été établie avec succès.</span><span class="sxs-lookup"><span data-stu-id="1332d-187">```XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT```: Triggered when a connection to the device has been successfully established.</span></span>
2) <span data-ttu-id="1332d-188">```XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT```: Déclenché si une connexion établie est fermée ou si une connexion n’a pas pu être établie.</span><span class="sxs-lookup"><span data-stu-id="1332d-188">```XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT```: Triggered if an established connection is closed or a connection could not be established.</span></span>
3) <span data-ttu-id="1332d-189">```XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT```: Lors du démarrage de l’écoute des connexions entrantes.</span><span class="sxs-lookup"><span data-stu-id="1332d-189">```XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT```: When listening for incoming connections starts.</span></span>

<span data-ttu-id="1332d-190">Ces événements sont placés dans une file d’attente et votre application distante doit lire la file d’attente avec régularité via ```xrPollEvent``` .</span><span class="sxs-lookup"><span data-stu-id="1332d-190">These events are placed in a queue and your remote app must read from the queue with regularity via ```xrPollEvent```.</span></span>

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

## <a name="preview-streamed-content-locally"></a><span data-ttu-id="1332d-191">Afficher un aperçu du contenu diffusé en continu localement</span><span class="sxs-lookup"><span data-stu-id="1332d-191">Preview streamed content locally</span></span>

<span data-ttu-id="1332d-192">Pour afficher le même contenu dans l’application distante qui est envoyé à l’appareil, l' ```XR_MSFT_holographic_remoting_frame_mirroring``` extension peut être utilisée.</span><span class="sxs-lookup"><span data-stu-id="1332d-192">To display the same content in the remote app that is send to the device the ```XR_MSFT_holographic_remoting_frame_mirroring``` extension can be used.</span></span> <span data-ttu-id="1332d-193">Avec cette extension, vous pouvez soumettre une texture à xrEndFrame.</span><span class="sxs-lookup"><span data-stu-id="1332d-193">With this extension you can submit a texture to xrEndFrame.</span></span> <span data-ttu-id="1332d-194">Pour ce faire, utilisez la ```XrRemotingFrameMirrorImageInfoMSFT``` structure chaînée à XrFrameEndInfo comme suit.</span><span class="sxs-lookup"><span data-stu-id="1332d-194">This is done by using the ```XrRemotingFrameMirrorImageInfoMSFT``` structure which is chained to the XrFrameEndInfo as follows.</span></span>

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

<span data-ttu-id="1332d-195">L’exemple ci-dessus utilise une texture de chaîne d’échange DX11 et présente la fenêtre immédiatement après l’appel à xrEndFrame.</span><span class="sxs-lookup"><span data-stu-id="1332d-195">The example above uses a DX11 swap-chain texture and presents the window immediately after the call to xrEndFrame.</span></span> <span data-ttu-id="1332d-196">L’utilisation n’est pas limitée aux textures de chaîne de swap et aucune synchronisation GPU supplémentaire n’est requise.</span><span class="sxs-lookup"><span data-stu-id="1332d-196">The usage is not restricted to swap-chain textures and no additional GPU synchronization is required.</span></span> <span data-ttu-id="1332d-197">Pour plus d’informations sur l’utilisation et les contraintes, consultez la [spécification d’extension](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring).</span><span class="sxs-lookup"><span data-stu-id="1332d-197">For details on usage and constraints check out the [extension specification](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring).</span></span>
<span data-ttu-id="1332d-198">Si votre application distante utilise DX12, utilisez XrRemotingFrameMirrorImageD3D12MSFT au lieu de XrRemotingFrameMirrorImageD3D11MSFT.</span><span class="sxs-lookup"><span data-stu-id="1332d-198">If your remote app is using DX12 use XrRemotingFrameMirrorImageD3D12MSFT instead of XrRemotingFrameMirrorImageD3D11MSFT.</span></span>

## <a name="see-also"></a><span data-ttu-id="1332d-199">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1332d-199">See Also</span></span>
* [<span data-ttu-id="1332d-200">Écriture d’une application de lecteur de communication à distance holographique personnalisée</span><span class="sxs-lookup"><span data-stu-id="1332d-200">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="1332d-201">Établissement d’une connexion sécurisée avec la communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="1332d-201">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="1332d-202">Résolution des problèmes et limitations de la communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="1332d-202">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="1332d-203">Termes du contrat de licence de la communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="1332d-203">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="1332d-204">Déclaration de confidentialité Microsoft</span><span class="sxs-lookup"><span data-stu-id="1332d-204">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
