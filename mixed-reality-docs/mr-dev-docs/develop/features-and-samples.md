---
title: Exemples d’applications et de fonctionnalités
description: Restez informé de tous les exemples Microsoft et toutes les applications des fonctionnalités de réalité mixte disponibles pour HoloLens.
author: hferrone
ms.author: jemccull
ms.date: 6/7/2021
ms.topic: article
keywords: réalité mixte, Unity, tutoriel, HoloLens, formation, exemples, MRTK, mode de recherche, HoloLens 2, codes QR, WebRTC, Capture de Réalité Mixte, communication à distance holographique, outils d’expérience utilisateur
ms.localizationpriority: high
ms.openlocfilehash: 78a9e343fde4a6cbc23268f0be353577498d67b6
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906895"
---
# <a name="samples-and-feature-apps"></a><span data-ttu-id="1ac22-104">Exemples d’applications et de fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="1ac22-104">Samples and feature apps</span></span>

![Image d’un utilisateur portant un HoloLens et manipulant un hologramme en déplaçant les mains](unreal/images/unreal-developer.jpg)

<span data-ttu-id="1ac22-106">Chaque parcours de développement commence par un retour sur ce que les autres développeurs ont réussi à créer. De ce point de vue, la réalité mixte ne fait pas exception à la règle.</span><span class="sxs-lookup"><span data-stu-id="1ac22-106">Every development journey starts with a look back at what other developers have successfully built - mixed reality is no different.</span></span> <span data-ttu-id="1ac22-107">Tous nos tutoriels et exemples d’applications sont actuellement créés dans Unity ou Unreal.</span><span class="sxs-lookup"><span data-stu-id="1ac22-107">Currently, all of our tutorials and sample apps are built in Unity or Unreal.</span></span> <span data-ttu-id="1ac22-108">À mesure que nous développerons du contenu pour d’autres moteurs et plateformes, nous ajouterons des titres à la table des matières.</span><span class="sxs-lookup"><span data-stu-id="1ac22-108">As we develop content for other engines and platforms, you'll find them under the relevant heading in the Table of Contents.</span></span>

## <a name="sample-apps"></a><span data-ttu-id="1ac22-109">Exemples d’application</span><span class="sxs-lookup"><span data-stu-id="1ac22-109">Sample apps</span></span>

[!INCLUDE[](includes/tabs-samples.md)]

## <a name="feature-samples"></a><span data-ttu-id="1ac22-110">Exemples de fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="1ac22-110">Feature samples</span></span>

<span data-ttu-id="1ac22-111">Les exemples de fonctionnalités listés ci-dessous correspondent à des implémentations spécifiques traitées dans notre documentation. Ils couvrent tout un éventail de plateformes de développement et de périphériques matériels.</span><span class="sxs-lookup"><span data-stu-id="1ac22-111">The feature samples listed below correspond to specific implementations that are covered in our documentation and covers a range of development platforms and hardware devices.</span></span>

### <a name="openxr"></a><span data-ttu-id="1ac22-112">OpenXR</span><span class="sxs-lookup"><span data-stu-id="1ac22-112">OpenXR</span></span>

<span data-ttu-id="1ac22-113">Les développeurs ciblant Unity 2020 pour créer des applications HoloLens 2 ou de réalité mixte peuvent utiliser le plug-in OpenXR à la place du plug-in WindowsXR pour de meilleures compatibilités entre les plateformes.</span><span class="sxs-lookup"><span data-stu-id="1ac22-113">For developers targeting Unity 2020 to build HoloLens 2 or Mixed Reality applications, OpenXR plugin can be used instead of WindowsXR plugin for better cross platform compatibilities.</span></span> <span data-ttu-id="1ac22-114">Le plug-in Mixed Reality OpenXR fonctionne également bien avec la dernière version de Mixed Reality Toolkit 2.7.</span><span class="sxs-lookup"><span data-stu-id="1ac22-114">The Mixed Reality OpenXR Plugin also works well with latest Mixed Reality Toolkit 2.7.</span></span>

<br>

| <span data-ttu-id="1ac22-115">Article de référence</span><span class="sxs-lookup"><span data-stu-id="1ac22-115">Reference article</span></span> | <span data-ttu-id="1ac22-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="1ac22-116">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="1ac22-117">Utilisation du plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="1ac22-117">Using the OpenXR plugin</span></span>](./unity/xr-project-setup.md) | [<span data-ttu-id="1ac22-118">Exemples de Mixed Reality OpenXR avec Unity</span><span class="sxs-lookup"><span data-stu-id="1ac22-118">Mixed Reality OpenXR with Unity samples</span></span>](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) |
| <span data-ttu-id="1ac22-119">N/A</span><span class="sxs-lookup"><span data-stu-id="1ac22-119">N/A</span></span> | [<span data-ttu-id="1ac22-120">Projet Unity de base OpenXR MRTK</span><span class="sxs-lookup"><span data-stu-id="1ac22-120">OpenXR MRTK Base Unity project</span></span>](https://github.com/microsoft/UnityOpenXRMRTKBase) |

### <a name="research-mode"></a><span data-ttu-id="1ac22-121">Mode Recherche</span><span class="sxs-lookup"><span data-stu-id="1ac22-121">Research Mode</span></span>

<span data-ttu-id="1ac22-122">Le mode Recherche a été introduit dans la 1re génération des HoloLens afin de permettre l’accès aux capteurs clés de l’appareil, en particulier pour les applications de recherche qui ne sont pas destinées au déploiement.</span><span class="sxs-lookup"><span data-stu-id="1ac22-122">Research Mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span> <span data-ttu-id="1ac22-123">Les exemples d’applications ci-dessous sont des exemples d’accès et d’enregistrement des flux du mode Recherche. Ils correspondent également à des exemples d’utilisation des propriétés [intrinsèques et extrinsèques](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).</span><span class="sxs-lookup"><span data-stu-id="1ac22-123">The sample applications below are examples for accessing and recording Research Mode streams and using the [intrinsics and extrinsics](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).</span></span>

<br>

| <span data-ttu-id="1ac22-124">Article de référence</span><span class="sxs-lookup"><span data-stu-id="1ac22-124">Reference article</span></span> | <span data-ttu-id="1ac22-125">Exemple d’application</span><span class="sxs-lookup"><span data-stu-id="1ac22-125">Sample application</span></span> |
| --- | --- |
| [<span data-ttu-id="1ac22-126">Mode Recherche</span><span class="sxs-lookup"><span data-stu-id="1ac22-126">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="1ac22-127">HoloLens (1ère génération)</span><span class="sxs-lookup"><span data-stu-id="1ac22-127">HoloLens (1st gen)</span></span>](https://github.com/microsoft/HoloLensForCV/tree/master/Samples) |
| [<span data-ttu-id="1ac22-128">Mode Recherche</span><span class="sxs-lookup"><span data-stu-id="1ac22-128">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="1ac22-129">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="1ac22-129">HoloLens 2</span></span>](https://github.com/microsoft/HoloLens2ForCV/tree/main/Samples) |

### <a name="qr-codes"></a><span data-ttu-id="1ac22-130">Codes QR</span><span class="sxs-lookup"><span data-stu-id="1ac22-130">QR codes</span></span>

<span data-ttu-id="1ac22-131">HoloLens 2 peut détecter les codes QR dans l’environnement situé autour du casque, ce qui permet d’établir un système de coordonnées à l’emplacement réel de chaque code.</span><span class="sxs-lookup"><span data-stu-id="1ac22-131">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span>

<br>

| <span data-ttu-id="1ac22-132">Article de référence</span><span class="sxs-lookup"><span data-stu-id="1ac22-132">Reference article</span></span> | <span data-ttu-id="1ac22-133">Exemple</span><span class="sxs-lookup"><span data-stu-id="1ac22-133">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="1ac22-134">Codes QR</span><span class="sxs-lookup"><span data-stu-id="1ac22-134">QR codes</span></span>](platform-capabilities-and-apis/qr-code-tracking.md) | [<span data-ttu-id="1ac22-135">Suivi des codes QR dans Unity</span><span class="sxs-lookup"><span data-stu-id="1ac22-135">QR code tracking in Unity</span></span>](https://github.com/microsoft/MixedReality-QRCode-Sample) |

### <a name="scene-understanding"></a><span data-ttu-id="1ac22-136">Compréhension des scènes</span><span class="sxs-lookup"><span data-stu-id="1ac22-136">Scene understanding</span></span>

<span data-ttu-id="1ac22-137">La compréhension des scènes fournit aux développeurs de réalité mixte une représentation d’environnement structurée et de haut niveau, conçue pour rendre intuitif le développement pour les applications compatibles avec l’environnement.</span><span class="sxs-lookup"><span data-stu-id="1ac22-137">Scene understanding provides Mixed Reality developers with a structured, high-level environment representation designed to make developing for environmentally aware applications intuitive.</span></span> <span data-ttu-id="1ac22-138">Pour ce faire, la compréhension des scènes combine la puissance de runtimes de réalité mixte existants, tels que le mappage spatial très précis mais moins structuré, et de nouveaux runtimes reposant sur l’IA.</span><span class="sxs-lookup"><span data-stu-id="1ac22-138">Scene understanding does this by combining the power of existing mixed reality runtimes, like the highly accurate but less structured spatial mapping and new AI driven runtimes.</span></span>

<br>

| <span data-ttu-id="1ac22-139">Article de référence</span><span class="sxs-lookup"><span data-stu-id="1ac22-139">Reference article</span></span> | <span data-ttu-id="1ac22-140">Exemple</span><span class="sxs-lookup"><span data-stu-id="1ac22-140">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="1ac22-141">Compréhension des scènes</span><span class="sxs-lookup"><span data-stu-id="1ac22-141">Scene understanding</span></span>](../design/scene-understanding.md) | [<span data-ttu-id="1ac22-142">Exemples de compréhension de scènes de réalité mixte</span><span class="sxs-lookup"><span data-stu-id="1ac22-142">Mixed Reality Scene Understanding samples</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples) |

### <a name="webrtc"></a><span data-ttu-id="1ac22-143">WebRTC</span><span class="sxs-lookup"><span data-stu-id="1ac22-143">WebRTC</span></span>

<span data-ttu-id="1ac22-144">Le projet MixedReality-WebRTC est une collection de composants destinés à aider les développeurs d’applications de réalité mixte à intégrer les transmissions audio, vidéo et de données pair à pair ainsi que les communications en temps réel dans leurs applications. Les composants WebRTC sont basés sur le protocole WebRTC pour la communication en temps réel (RTC), qui est pris en charge par la plupart des navigateurs web modernes.</span><span class="sxs-lookup"><span data-stu-id="1ac22-144">The MixedReality-WebRTC project is a collection of components to help mixed reality app developers to integrate peer-to-peer audio, video, and data real-time communication into their applications WebRTC components are based on the WebRTC protocol for Real-Time Communication (RTC), which is supported by most modern web browsers.</span></span>

<br>

| <span data-ttu-id="1ac22-145">Article de référence</span><span class="sxs-lookup"><span data-stu-id="1ac22-145">Reference article</span></span> | <span data-ttu-id="1ac22-146">Exemple</span><span class="sxs-lookup"><span data-stu-id="1ac22-146">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="1ac22-147">WebRTC</span><span class="sxs-lookup"><span data-stu-id="1ac22-147">WebRTC</span></span>](https://microsoft.github.io/MixedReality-WebRTC) | [<span data-ttu-id="1ac22-148">Exemples d’applications WebRTC</span><span class="sxs-lookup"><span data-stu-id="1ac22-148">WebRTC sample apps</span></span>](https://github.com/microsoft/MixedReality-WebRTC/tree/master/examples) |

### <a name="holographic-mixed-reality-capture"></a><span data-ttu-id="1ac22-149">Capture de réalité mixte holographique</span><span class="sxs-lookup"><span data-stu-id="1ac22-149">Holographic Mixed Reality Capture</span></span>

<span data-ttu-id="1ac22-150">La capture de réalité mixte (MRC) permet de capturer une expérience utilisateur à la première personne, qui consiste à mélanger les mondes réel et numérique sous forme de photo ou de vidéo, et à partager ce que vous voyez avec les autres en temps réel.</span><span class="sxs-lookup"><span data-stu-id="1ac22-150">Mixed reality capture (MRC) captures the first-person experience of mixing real and digital worlds as a photo or video, sharing what you see with others in real-time.</span></span>

<br>

| <span data-ttu-id="1ac22-151">Article de référence</span><span class="sxs-lookup"><span data-stu-id="1ac22-151">Reference article</span></span> | <span data-ttu-id="1ac22-152">Exemple</span><span class="sxs-lookup"><span data-stu-id="1ac22-152">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="1ac22-153">Capture de réalité mixte</span><span class="sxs-lookup"><span data-stu-id="1ac22-153">Mixed Reality Capture</span></span>](platform-capabilities-and-apis/mixed-reality-capture-for-developers.md) | [<span data-ttu-id="1ac22-154">Exemples de captures de réalité mixte</span><span class="sxs-lookup"><span data-stu-id="1ac22-154">Mixed Reality Capture samples</span></span>](/samples/microsoft/windows-universal-samples/holographicmixedrealitycapture/) |

### <a name="holographic-remoting"></a><span data-ttu-id="1ac22-155">Communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="1ac22-155">Holographic Remoting</span></span>

<span data-ttu-id="1ac22-156">Holographic Remoting Player est un complément qui se connecte aux applications et aux jeux PC prenant en charge la communication à distance holographique.</span><span class="sxs-lookup"><span data-stu-id="1ac22-156">The Holographic Remoting Player is a companion app that connects to PC apps and games that support Holographic Remoting.</span></span> <span data-ttu-id="1ac22-157">Holographic Remoting transmet en streaming le contenu holographique d’un PC vers votre Microsoft HoloLens en temps réel, à l’aide d’une connexion Wi-Fi. Il est pris en charge par HoloLens (1re génération) et HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1ac22-157">Holographic Remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi connection, and is supported on HoloLens (1st gen) and HoloLens 2.</span></span>

<br>

| <span data-ttu-id="1ac22-158">Article de référence</span><span class="sxs-lookup"><span data-stu-id="1ac22-158">Reference article</span></span> | <span data-ttu-id="1ac22-159">Exemple</span><span class="sxs-lookup"><span data-stu-id="1ac22-159">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="1ac22-160">Communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="1ac22-160">Holographic Remoting</span></span>](platform-capabilities-and-apis/holographic-remoting-player.md) | [<span data-ttu-id="1ac22-161">Exemples de communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="1ac22-161">Holographic Remoting samples</span></span>](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples) |