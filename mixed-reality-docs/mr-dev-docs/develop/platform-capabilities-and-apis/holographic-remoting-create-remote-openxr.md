---
title: Écriture d’une application distante holographique de communication à distance (OpenXR)
description: Découvrez comment diffuser du contenu distant rendu sur une machine distante à HoloLens 2 avec des applications de communication à distance holographique avec OpenXR.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, communication à distance, accès distant holographique, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle, NuGet
ms.openlocfilehash: da3114b2c8c4e04d8da9296687f92d0b23945281
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581232"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-openxr-api"></a><span data-ttu-id="28a56-104">Écriture d’une application distante holographique à distance à l’aide de l’API OpenXR</span><span class="sxs-lookup"><span data-stu-id="28a56-104">Writing a Holographic Remoting remote app using the OpenXR API</span></span>

>[!IMPORTANT]
><span data-ttu-id="28a56-105">Ce document décrit la création d’une application distante pour les casques HoloLens 2 et Windows Mixed Reality à l’aide de l' [API OpenXR](../native/openxr.md).</span><span class="sxs-lookup"><span data-stu-id="28a56-105">This document describes the creation of a remote application for HoloLens 2 and Windows Mixed Reality headsets using the [OpenXR API](../native/openxr.md).</span></span> <span data-ttu-id="28a56-106">Les applications distantes pour **HoloLens (1re génération)** doivent utiliser le package NuGet version **1. x. x**.</span><span class="sxs-lookup"><span data-stu-id="28a56-106">Remote applications for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="28a56-107">Cela implique que les applications distantes écrites pour HoloLens 2 ne sont pas compatibles avec HoloLens 1 et vice versa.</span><span class="sxs-lookup"><span data-stu-id="28a56-107">This implies that remote applications written for HoloLens 2 are not compatible with HoloLens 1 and vice versa.</span></span> <span data-ttu-id="28a56-108">La documentation de HoloLens 1 est disponible [ici](add-holographic-remoting.md).</span><span class="sxs-lookup"><span data-stu-id="28a56-108">The documentation for HoloLens 1 can be found [here](add-holographic-remoting.md).</span></span>

<span data-ttu-id="28a56-109">Les applications de communication à distance holographique peuvent diffuser du contenu diffusé à distance sur des casques immersifs HoloLens 2 et Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="28a56-109">Holographic Remoting apps can stream remotely rendered content to HoloLens 2 and Windows Mixed Reality immersive headsets.</span></span> <span data-ttu-id="28a56-110">Vous pouvez également accéder à davantage de ressources système et intégrer des [vues immersives](../../design/app-views.md) distantes dans des logiciels de poste de travail existants.</span><span class="sxs-lookup"><span data-stu-id="28a56-110">You can also access more system resources and integrate remote [immersive views](../../design/app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="28a56-111">Une application distante reçoit un flux de données d’entrée de HoloLens 2, restitue le contenu dans une vue immersive virtuelle et diffuse en continu des frames de contenu vers HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="28a56-111">A remote app receives an input data stream from HoloLens 2, renders content in a virtual immersive view, and streams content frames back to HoloLens 2.</span></span> <span data-ttu-id="28a56-112">La connexion est établie à l’aide du Wi-Fi standard.</span><span class="sxs-lookup"><span data-stu-id="28a56-112">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="28a56-113">La communication à distance holographique est ajoutée à une application de bureau ou UWP via un paquet NuGet.</span><span class="sxs-lookup"><span data-stu-id="28a56-113">Holographic Remoting is added to a desktop or UWP app via a NuGet packet.</span></span> <span data-ttu-id="28a56-114">Du code supplémentaire est nécessaire pour gérer la connexion et le rendu dans une vue immersive.</span><span class="sxs-lookup"><span data-stu-id="28a56-114">Additional code is required which handles the connection and renders in an immersive view.</span></span> <span data-ttu-id="28a56-115">Une connexion à distance classique aura une latence aussi faible que 50 ms de latence.</span><span class="sxs-lookup"><span data-stu-id="28a56-115">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="28a56-116">L’application de lecteur peut signaler la latence en temps réel.</span><span class="sxs-lookup"><span data-stu-id="28a56-116">The player app can report the latency in real time.</span></span>

<span data-ttu-id="28a56-117">Tout le code de cette page et des projets de travail se trouve dans le [référentiel GitHub d’exemples de communication à distance holographique](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span><span class="sxs-lookup"><span data-stu-id="28a56-117">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="28a56-118">Prérequis</span><span class="sxs-lookup"><span data-stu-id="28a56-118">Prerequisites</span></span>

<span data-ttu-id="28a56-119">Un bon point de départ est une application de bureau ou UWP basée sur un OpenXR fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="28a56-119">A good starting point is a working OpenXR based Desktop or UWP app.</span></span> <span data-ttu-id="28a56-120">Pour plus d’informations, consultez [prise en main de OpenXR](../native/openxr-getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="28a56-120">For details see [Getting started with OpenXR](../native/openxr-getting-started.md).</span></span>

>[!IMPORTANT]
><span data-ttu-id="28a56-121">Toute application utilisant la communication à distance holographique doit être créée pour utiliser un [cloisonnement](//windows/win32/com/multithreaded-apartments)multithread.</span><span class="sxs-lookup"><span data-stu-id="28a56-121">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](//windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="28a56-122">L’utilisation d’un [cloisonnement à thread unique](//windows/win32/com/single-threaded-apartments) est prise en charge, mais entraîne des performances non optimales et éventuellement des interruptions pendant la lecture.</span><span class="sxs-lookup"><span data-stu-id="28a56-122">The use of a [single-threaded apartment](//windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="28a56-123">Lors de l’utilisation de C++/WinRT [WinRT :: init_apartment](//windows/uwp/cpp-and-winrt-apis/get-started) un cloisonnement multithread est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="28a56-123">When using C++/WinRT [winrt::init_apartment](//windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>

## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="28a56-124">Procurez-vous le package NuGet de communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="28a56-124">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="28a56-125">Les étapes suivantes sont requises pour ajouter le package NuGet à un projet dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="28a56-125">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="28a56-126">Ouvrez le projet dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="28a56-126">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="28a56-127">Cliquez avec le bouton droit sur le nœud du projet et sélectionnez **gérer les packages NuGet...**</span><span class="sxs-lookup"><span data-stu-id="28a56-127">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="28a56-128">Dans le volet qui s’affiche, sélectionnez **Parcourir** , puis recherchez « accès à distance holographique ».</span><span class="sxs-lookup"><span data-stu-id="28a56-128">In the panel that appears, select **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="28a56-129">Sélectionnez **Microsoft. holographique. Remoting. OpenXr**, assurez-vous de choisir la version la plus récente de **2. x. x** , puis sélectionnez **installer**.</span><span class="sxs-lookup"><span data-stu-id="28a56-129">Select **Microsoft.Holographic.Remoting.OpenXr**, ensure to pick the latest **2.x.x** version and select **Install**.</span></span>
5. <span data-ttu-id="28a56-130">Si la boîte de dialogue **Aperçu** s’affiche, sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="28a56-130">If the **Preview** dialog appears, select **OK**.</span></span>
6. <span data-ttu-id="28a56-131">Sélectionnez **J’accepte** quand la boîte de dialogue du contrat de licence s’affiche.</span><span class="sxs-lookup"><span data-stu-id="28a56-131">Select **I Accept** when the license agreement dialog pops up.</span></span>
7. <span data-ttu-id="28a56-132">Répétez les étapes 3 à 6 pour les packages NuGet suivants : OpenXR. Headers, OpenXR. Loader</span><span class="sxs-lookup"><span data-stu-id="28a56-132">Repeat the steps 3 to 6 for the following NuGet Packages: OpenXR.Headers, OpenXR.Loader</span></span>

>[!NOTE]
><span data-ttu-id="28a56-133">La version **1. x. x** du package NuGet est toujours disponible pour les développeurs qui souhaitent cibler HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="28a56-133">Version **1.x.x** of the NuGet package is still available for developers who want to target HoloLens 1.</span></span> <span data-ttu-id="28a56-134">Pour plus d’informations [, consultez Ajouter une communication à distance holographique (HoloLens (1re génération))](add-holographic-remoting.md).</span><span class="sxs-lookup"><span data-stu-id="28a56-134">For details see [Add Holographic Remoting (HoloLens (1st gen))](add-holographic-remoting.md).</span></span>

## <a name="select-the-holographic-remoting-openxr-runtime"></a><span data-ttu-id="28a56-135">Sélectionner le runtime OpenXR Remoting holographique</span><span class="sxs-lookup"><span data-stu-id="28a56-135">Select the Holographic Remoting OpenXR runtime</span></span>

<span data-ttu-id="28a56-136">La première étape que vous devez effectuer dans votre application distante consiste à sélectionner le runtime OpenXR de communication à distance holographique, qui fait partie du package NuGet Microsoft. holographique. Remoting. OpenXr.</span><span class="sxs-lookup"><span data-stu-id="28a56-136">The first step you need to do in your remote app is to select the Holographic Remoting OpenXR runtime, which is part of the Microsoft.Holographic.Remoting.OpenXr NuGet package.</span></span> <span data-ttu-id="28a56-137">Pour ce faire, vous pouvez définir la ```XR_RUNTIME_JSON``` variable d’environnement sur le chemin d’accès de l' RemotingXR.jssur le fichier dans votre application.</span><span class="sxs-lookup"><span data-stu-id="28a56-137">You can do this by setting the ```XR_RUNTIME_JSON``` environment variable to the path of the RemotingXR.json file within your app.</span></span> <span data-ttu-id="28a56-138">Cette variable d’environnement est utilisée par le chargeur OpenXR pour ne pas utiliser le runtime OpenXR par défaut du système, mais plutôt rediriger vers le runtime OpenXR de communication à distance holographique.</span><span class="sxs-lookup"><span data-stu-id="28a56-138">This environment variable is used by the OpenXR loader to not use the system default OpenXR runtime but instead redirect to the Holographic Remoting OpenXR runtime.</span></span> <span data-ttu-id="28a56-139">Lorsque vous utilisez le package NuGet Microsoft. holographique. Remoting. OpenXr, le fichier RemotingXR.jsest automatiquement copié pendant la compilation dans le dossier de sortie. la sélection du runtime OpenXR se présente généralement comme suit.</span><span class="sxs-lookup"><span data-stu-id="28a56-139">When using the Microsoft.Holographic.Remoting.OpenXr NuGet package the RemotingXR.json file is automatically copied during compilation to the output folder, the OpenXR runtime selection typically looks as follows.</span></span>

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

## <a name="create-xrinstance-with-holographic-remoting-extension"></a><span data-ttu-id="28a56-140">Créer XrInstance avec l’extension de communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="28a56-140">Create XrInstance with Holographic Remoting Extension</span></span>

<span data-ttu-id="28a56-141">La première étape d’une application OpenXR classique est de sélectionner les extensions OpenXR et de créer un XrInstance.</span><span class="sxs-lookup"><span data-stu-id="28a56-141">The first step a typical OpenXR app is supposed to do is to select OpenXR extensions and create an XrInstance.</span></span> <span data-ttu-id="28a56-142">La spécification OpenXR Core ne fournit pas d’API spécifique à distance.</span><span class="sxs-lookup"><span data-stu-id="28a56-142">The OpenXR core specification doesn't provide any remoting specific API.</span></span> <span data-ttu-id="28a56-143">Pour cette raison, la communication à distance holographique introduit sa propre extension OpenXR nommée ```XR_MSFT_holographic_remoting``` .</span><span class="sxs-lookup"><span data-stu-id="28a56-143">For that reason Holographic Remoting introduces its own OpenXR extension named ```XR_MSFT_holographic_remoting```.</span></span> <span data-ttu-id="28a56-144">Assurez-vous que lorsque vous appelez xrCreateInstance ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` , est inclus dans le XrInstanceCreateInfo.</span><span class="sxs-lookup"><span data-stu-id="28a56-144">Ensure that when you call xrCreateInstance the ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` is included in the XrInstanceCreateInfo.</span></span>

>[!TIP]
><span data-ttu-id="28a56-145">Par défaut, le contenu rendu de votre application est diffusé uniquement sur le lecteur de communication à distance holographique s’exécutant sur un HoloLens 2 ou sur un casque Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="28a56-145">By default the rendered content of your app is only streamed to the Holographic Remoting player either running on a HoloLens 2 or on a Windows Mixed Reality headsets.</span></span> <span data-ttu-id="28a56-146">Pour afficher également le contenu rendu sur l’ordinateur distant, par le biais d’une chaîne d’échange d’une fenêtre, par exemple, la communication à distance holographique fournit une deuxième extension OpenXR nommée ```XR_MSFT_holographic_remoting_frame_mirroring``` .</span><span class="sxs-lookup"><span data-stu-id="28a56-146">To also display the rendered content on the remote PC, via a swap-chain of a window for instance, Holographic Remoting provides a second OpenXR extension named ```XR_MSFT_holographic_remoting_frame_mirroring```.</span></span> <span data-ttu-id="28a56-147">Veillez également à activer cette extension ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME``` au cas où vous souhaiteriez utiliser cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="28a56-147">Ensure to also enable this extension using ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME``` in case you want to use that functionality.</span></span>

>[!IMPORTANT]
><span data-ttu-id="28a56-148">Pour en savoir plus sur l’API d’extension OpenXR de communication à distance holographique, consultez la [spécification](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) qui se trouve dans le [référentiel GitHub des exemples de communication à distance holographique](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span><span class="sxs-lookup"><span data-stu-id="28a56-148">To learn about the Holographic Remoting OpenXR extension API, check out the [specification](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) which can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

## <a name="connect-to-the-device"></a><span data-ttu-id="28a56-149">Se connecter à l’appareil</span><span class="sxs-lookup"><span data-stu-id="28a56-149">Connect to the device</span></span>

<span data-ttu-id="28a56-150">Une fois que votre application distante a créé les XrInstance et interrogé les XrSystemId via xrGetSystem, une connexion à l’appareil Player peut être établie.</span><span class="sxs-lookup"><span data-stu-id="28a56-150">After your remote app has created the XrInstance and queried the XrSystemId via xrGetSystem a connection to the player device can be established.</span></span>

>[!WARNING]
> <span data-ttu-id="28a56-151">Le runtime OpenXR de communication à distance holographique est uniquement en mesure de fournir des données spécifiques à l’appareil, telles que des configurations d’affichage ou des modes de fusion d’environnement, après l’établissement d’une connexion.</span><span class="sxs-lookup"><span data-stu-id="28a56-151">The Holographic Remoting OpenXR runtime is only able to provide device specific data such as view configurations or environment blend modes after a connection has been established.</span></span> <span data-ttu-id="28a56-152">```xrEnumerateViewConfigurations```, ```xrEnumerateViewConfigurationViews``` , ```xrGetViewConfigurationProperties``` , ```xrEnumerateEnvironmentBlendModes``` et ```xrGetSystemProperties``` fournissent les valeurs par défaut, en fonction de ce que vous obtiendriez en général si vous vous connectez à un joueur s’exécutant sur un HoloLens 2, avant d’être entièrement connecté.</span><span class="sxs-lookup"><span data-stu-id="28a56-152">```xrEnumerateViewConfigurations```, ```xrEnumerateViewConfigurationViews```, ```xrGetViewConfigurationProperties```, ```xrEnumerateEnvironmentBlendModes```, and ```xrGetSystemProperties``` will give you default values, matching what you would typically get if you connect to a player running on a HoloLens 2, before being fully connected.</span></span>
<span data-ttu-id="28a56-153">Il est fortement recommandé de ne pas appeler ces méthodes avant qu’une connexion ait été établie.</span><span class="sxs-lookup"><span data-stu-id="28a56-153">It is strongly recommended to not call these methods before a connection has been established.</span></span> <span data-ttu-id="28a56-154">La suggestion est utilisée par ces méthodes une fois que le XrSession a été créé avec succès et que l’état de session est au moins XR_SESSION_STATE_READY.</span><span class="sxs-lookup"><span data-stu-id="28a56-154">The suggestion is used these methods after the XrSession has been successfully created and the session state is at least XR_SESSION_STATE_READY.</span></span>

<span data-ttu-id="28a56-155">Les propriétés générales telles que le débit maximal, l’audio activé, le codec vidéo ou la résolution de flux de mémoire tampon de profondeur peuvent être configurées via ```xrRemotingSetContextPropertiesMSFT``` comme suit.</span><span class="sxs-lookup"><span data-stu-id="28a56-155">General properties such as max bitrate, audio enabled, video codec, or depth buffer stream resolution can be configured via ```xrRemotingSetContextPropertiesMSFT``` as follows.</span></span>

```cpp
XrRemotingRemoteContextPropertiesMSFT contextProperties;
contextProperties = XrRemotingRemoteContextPropertiesMSFT{static_cast<XrStructureType>(XR_TYPE_REMOTING_REMOTE_CONTEXT_PROPERTIES_MSFT)};
contextProperties.enableAudio = false;
contextProperties.maxBitrateKbps = 20000;
contextProperties.videoCodec = XR_REMOTING_VIDEO_CODEC_H265_MSFT;
contextProperties.depthBufferStreamResolution = XR_REMOTING_DEPTH_BUFFER_STREAM_RESOLUTION_HALF_MSFT;
xrRemotingSetContextPropertiesMSFT(m_instance.Get(), m_systemId, &contextProperties);
```

<span data-ttu-id="28a56-156">La connexion peut être effectuée de deux manières.</span><span class="sxs-lookup"><span data-stu-id="28a56-156">The connection can be done in one of two ways.</span></span>
1) <span data-ttu-id="28a56-157">L’application distante se connecte au lecteur qui s’exécute sur l’appareil.</span><span class="sxs-lookup"><span data-stu-id="28a56-157">The remote app connects to the player running on the device.</span></span>
2) <span data-ttu-id="28a56-158">Le lecteur s’exécutant sur l’appareil se connecte à l’application distante.</span><span class="sxs-lookup"><span data-stu-id="28a56-158">The player running on the device connects to the remote app.</span></span>

<span data-ttu-id="28a56-159">Pour établir une connexion de l’application distante à l’appareil Player ```xrRemotingConnectMSFT``` , appelez la méthode en spécifiant le nom d’hôte et le port via la  ```XrRemotingConnectInfoMSFT``` structure.</span><span class="sxs-lookup"><span data-stu-id="28a56-159">To establish a connection from the remote app to the player device call the ```xrRemotingConnectMSFT``` method specifying the hostname and port via the  ```XrRemotingConnectInfoMSFT``` structure.</span></span> <span data-ttu-id="28a56-160">Le port utilisé par le lecteur de communication à distance holographique est **8265**.</span><span class="sxs-lookup"><span data-stu-id="28a56-160">The port used by the Holographic Remoting Player is **8265**.</span></span>

```cpp
XrRemotingConnectInfoMSFT connectInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_CONNECT_INFO_MSFT)};
connectInfo.remoteHostName = "192.168.x.x";
connectInfo.remotePort = 8265;
connectInfo.secureConnection = false;
xrRemotingConnectMSFT(m_instance.Get(), m_systemId, &connectInfo);
```

<span data-ttu-id="28a56-161">L’écoute des connexions entrantes sur l’application distante peut être effectuée en appelant la ```xrRemotingListenMSFT``` méthode.</span><span class="sxs-lookup"><span data-stu-id="28a56-161">Listening for incoming connections on the remote app can be done by calling the ```xrRemotingListenMSFT``` method.</span></span> <span data-ttu-id="28a56-162">Le port de liaison et le port de transport peuvent être spécifiés via la ```XrRemotingListenInfoMSFT``` structure.</span><span class="sxs-lookup"><span data-stu-id="28a56-162">Both the handshake port and transport port can be specified via the ```XrRemotingListenInfoMSFT``` structure.</span></span> <span data-ttu-id="28a56-163">Le port de négociation est utilisé pour le protocole de transfert initial.</span><span class="sxs-lookup"><span data-stu-id="28a56-163">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="28a56-164">Les données sont ensuite envoyées sur le port de transport.</span><span class="sxs-lookup"><span data-stu-id="28a56-164">The data is then sent over the transport port.</span></span> <span data-ttu-id="28a56-165">Par défaut, **8265** et **8266** sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="28a56-165">By default **8265** and **8266** are used.</span></span>

```cpp
XrRemotingListenInfoMSFT listenInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_LISTEN_INFO_MSFT)};
listenInfo.listenInterface = "0.0.0.0";
listenInfo.handshakeListenPort = 8265;
listenInfo.transportListenPort = 8266;
listenInfo.secureConnection = false;
xrRemotingListenMSFT(m_instance.Get(), m_systemId, &listenInfo);
```

<span data-ttu-id="28a56-166">L’état de la connexion doit être déconnecté lorsque vous appelez ```xrRemotingConnectMSFT``` ou ```xrRemotingListenMSFT``` .</span><span class="sxs-lookup"><span data-stu-id="28a56-166">The connection state must be disconnected when you call ```xrRemotingConnectMSFT``` or ```xrRemotingListenMSFT```.</span></span> <span data-ttu-id="28a56-167">Vous pouvez obtenir l’état de la connexion à tout moment après avoir créé un XrInstance et interrogé pour XrSystemId via ```xrRemotingGetConnectionStateMSFT``` .</span><span class="sxs-lookup"><span data-stu-id="28a56-167">You can get the connection state at any point after you have created an XrInstance and queried for the XrSystemId via ```xrRemotingGetConnectionStateMSFT```.</span></span>

```cpp
XrRemotingConnectionStateMSFT connectionState;
xrRemotingGetConnectionStateMSFT(m_instance.Get(), m_systemId, &connectionState, nullptr);
```

<span data-ttu-id="28a56-168">Les États de connexion disponibles sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="28a56-168">Available connection states are:</span></span>
- <span data-ttu-id="28a56-169">XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT</span><span class="sxs-lookup"><span data-stu-id="28a56-169">XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT</span></span>
- <span data-ttu-id="28a56-170">XR_REMOTING_CONNECTION_STATE_CONNECTING_MSFT</span><span class="sxs-lookup"><span data-stu-id="28a56-170">XR_REMOTING_CONNECTION_STATE_CONNECTING_MSFT</span></span>
- <span data-ttu-id="28a56-171">XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT</span><span class="sxs-lookup"><span data-stu-id="28a56-171">XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT</span></span>

>[!IMPORTANT]
> <span data-ttu-id="28a56-172">```xrRemotingConnectMSFT``` ou ```xrRemotingListenMSFT``` doit être appelé avant d’essayer de créer un XrSession via xrCreateSession.</span><span class="sxs-lookup"><span data-stu-id="28a56-172">```xrRemotingConnectMSFT``` or ```xrRemotingListenMSFT``` must be called before trying to create a XrSession via xrCreateSession.</span></span> <span data-ttu-id="28a56-173">Si vous essayez de créer un XrSession alors que l’état de la connexion est ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` la création de la session réussie, mais que l’état de la session passera immédiatement à XR_SESSION_STATE_LOSS_PENDING.</span><span class="sxs-lookup"><span data-stu-id="28a56-173">If you try to create a XrSession while the connection state is ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` the session creation will succeed but the session state will immediately transition to XR_SESSION_STATE_LOSS_PENDING.</span></span>

<span data-ttu-id="28a56-174">L’implémentation de la communication à distance holographique de ```xrCreateSession``` prend en charge l’attente de l’établissement d’une connexion.</span><span class="sxs-lookup"><span data-stu-id="28a56-174">Holographic Remoting's implementation of ```xrCreateSession``` supports waiting for a connection to be established.</span></span> <span data-ttu-id="28a56-175">Vous pouvez appeler ```xrRemotingConnectMSFT``` ou ```xrRemotingListenMSFT``` immédiatement suivi d’un appel à, qui bloque et attend qu’une connexion soit établie.</span><span class="sxs-lookup"><span data-stu-id="28a56-175">You can call ```xrRemotingConnectMSFT``` or ```xrRemotingListenMSFT``` immediately followed by a call to, which will block and wait for a connection to be established.</span></span> <span data-ttu-id="28a56-176">Le délai d’attente est fixé à 10 secondes.</span><span class="sxs-lookup"><span data-stu-id="28a56-176">The timeout is fixed to 10 seconds.</span></span> <span data-ttu-id="28a56-177">Si une connexion peut être établie dans ce délai, la création de XrSession est effectuée et l’état de session passera à XR_SESSION_STATE_READY.</span><span class="sxs-lookup"><span data-stu-id="28a56-177">If a connection can be established within this time the XrSession creation will succeed and the session state will transition to XR_SESSION_STATE_READY.</span></span> <span data-ttu-id="28a56-178">Dans le cas où aucune connexion ne peut être établie, la création de session s’effectue également, mais passe immédiatement à XR_SESSION_STATE_LOSS_PENDING.</span><span class="sxs-lookup"><span data-stu-id="28a56-178">In case no connection can be established the session creation also succeeds but immediately transitions to XR_SESSION_STATE_LOSS_PENDING.</span></span>

<span data-ttu-id="28a56-179">En général, l’état de la connexion est couple à l’État XrSession.</span><span class="sxs-lookup"><span data-stu-id="28a56-179">In general, the connection state is couple with the XrSession state.</span></span> <span data-ttu-id="28a56-180">Toute modification apportée à l’état de la connexion affecte également l’état de la session.</span><span class="sxs-lookup"><span data-stu-id="28a56-180">Any change to the connection state also affects the session state.</span></span> <span data-ttu-id="28a56-181">Par exemple, si l’état de la connexion passe de `XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT` à ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` l’état de session passera également à XR_SESSION_STATE_LOSS_PENDING.</span><span class="sxs-lookup"><span data-stu-id="28a56-181">For instance, if the connection state switches from `XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT` to ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` the session state will transition to XR_SESSION_STATE_LOSS_PENDING as well.</span></span>

## <a name="handling-remoting-specific-events"></a><span data-ttu-id="28a56-182">Gestion des événements de communication à distance spécifiques</span><span class="sxs-lookup"><span data-stu-id="28a56-182">Handling Remoting specific events</span></span>

<span data-ttu-id="28a56-183">Le runtime OpenXR de la communication à distance holographique expose trois événements, qui sont importants pour surveiller l’état d’une connexion.</span><span class="sxs-lookup"><span data-stu-id="28a56-183">The Holographic Remoting OpenXR runtime exposes three events, which are important to monitor the state of a connection.</span></span>
1) <span data-ttu-id="28a56-184">```XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT```: Déclenché lorsqu’une connexion à l’appareil a été établie avec succès.</span><span class="sxs-lookup"><span data-stu-id="28a56-184">```XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT```: Triggered when a connection to the device has been successfully established.</span></span>
2) <span data-ttu-id="28a56-185">```XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT```: Déclenché si une connexion établie est fermée ou si une connexion n’a pas pu être établie.</span><span class="sxs-lookup"><span data-stu-id="28a56-185">```XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT```: Triggered if an established connection is closed or a connection couldn't be established.</span></span>
3) <span data-ttu-id="28a56-186">```XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT```: Lors du démarrage de l’écoute des connexions entrantes.</span><span class="sxs-lookup"><span data-stu-id="28a56-186">```XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT```: When listening for incoming connections starts.</span></span>

<span data-ttu-id="28a56-187">Ces événements sont placés dans une file d’attente et votre application distante doit lire la file d’attente avec régularité via ```xrPollEvent``` .</span><span class="sxs-lookup"><span data-stu-id="28a56-187">These events are placed in a queue and your remote app must read from the queue with regularity via ```xrPollEvent```.</span></span>

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

## <a name="preview-streamed-content-locally"></a><span data-ttu-id="28a56-188">Afficher un aperçu du contenu diffusé en continu localement</span><span class="sxs-lookup"><span data-stu-id="28a56-188">Preview streamed content locally</span></span>

<span data-ttu-id="28a56-189">Pour afficher le même contenu dans l’application distante qui est envoyé à l’appareil, l' ```XR_MSFT_holographic_remoting_frame_mirroring``` extension peut être utilisée.</span><span class="sxs-lookup"><span data-stu-id="28a56-189">To display the same content in the remote app that is sent to the device the ```XR_MSFT_holographic_remoting_frame_mirroring``` extension can be used.</span></span> <span data-ttu-id="28a56-190">Avec cette extension, vous pouvez soumettre une texture à xrEndFrame en utilisant le ```XrRemotingFrameMirrorImageInfoMSFT``` qui n’est pas chaîné au XrFrameEndInfo comme suit.</span><span class="sxs-lookup"><span data-stu-id="28a56-190">With this extension, you can submit a texture to xrEndFrame by using the ```XrRemotingFrameMirrorImageInfoMSFT``` that isn't chained to the XrFrameEndInfo as follows.</span></span>

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

<span data-ttu-id="28a56-191">L’exemple ci-dessus utilise une texture de chaîne d’échange DX11 et présente la fenêtre immédiatement après l’appel à xrEndFrame.</span><span class="sxs-lookup"><span data-stu-id="28a56-191">The example above uses a DX11 swap-chain texture and presents the window immediately after the call to xrEndFrame.</span></span> <span data-ttu-id="28a56-192">L’utilisation n’est pas limitée aux textures de chaîne de swap et aucune synchronisation GPU supplémentaire n’est requise.</span><span class="sxs-lookup"><span data-stu-id="28a56-192">The usage isn't restricted to swap-chain textures and no additional GPU synchronization is required.</span></span> <span data-ttu-id="28a56-193">Pour plus d’informations sur l’utilisation et les contraintes, consultez la [spécification d’extension](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring).</span><span class="sxs-lookup"><span data-stu-id="28a56-193">For details on usage and constraints check out the [extension specification](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring).</span></span>
<span data-ttu-id="28a56-194">Si votre application distante utilise DX12, utilisez XrRemotingFrameMirrorImageD3D12MSFT au lieu de XrRemotingFrameMirrorImageD3D11MSFT.</span><span class="sxs-lookup"><span data-stu-id="28a56-194">If your remote app is using DX12 use XrRemotingFrameMirrorImageD3D12MSFT instead of XrRemotingFrameMirrorImageD3D11MSFT.</span></span>

## <a name="see-also"></a><span data-ttu-id="28a56-195">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28a56-195">See Also</span></span>
* [<span data-ttu-id="28a56-196">Écriture d’une application de lecteur de communication à distance holographique personnalisée</span><span class="sxs-lookup"><span data-stu-id="28a56-196">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="28a56-197">Établissement d’une connexion sécurisée avec la communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="28a56-197">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="28a56-198">Résolution des problèmes et limitations de la communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="28a56-198">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="28a56-199">Termes du contrat de licence de la communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="28a56-199">Holographic Remoting software license terms</span></span>](//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="28a56-200">Déclaration de confidentialité Microsoft</span><span class="sxs-lookup"><span data-stu-id="28a56-200">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)