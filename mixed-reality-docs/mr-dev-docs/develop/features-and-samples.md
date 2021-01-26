---
title: Exemples d’applications et de fonctionnalités
description: Restez informé de tous les exemples Microsoft et toutes les applications des fonctionnalités de réalité mixte disponibles pour HoloLens.
author: hferrone
ms.author: jemccull
ms.date: 12/3/2020
ms.topic: article
keywords: réalité mixte, Unity, tutoriel, HoloLens, formation, exemples, MRTK, mode de recherche, HoloLens 2, codes QR, WebRTC, Capture de Réalité Mixte, communication à distance holographique, outils d’expérience utilisateur
ms.localizationpriority: high
ms.openlocfilehash: 78cfc726bdffdb461a83bd1e9805d8f0e64b0f01
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583193"
---
# <a name="samples-and-feature-apps"></a><span data-ttu-id="57bf0-104">Exemples d’applications et de fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="57bf0-104">Samples and feature apps</span></span>

![Image d’un utilisateur portant un HoloLens et manipulant un hologramme en déplaçant les mains](unreal/images/unreal-developer.jpg)

<span data-ttu-id="57bf0-106">Chaque parcours de développement commence par un retour sur ce que les autres développeurs ont réussi à créer. De ce point de vue, la réalité mixte ne fait pas exception à la règle.</span><span class="sxs-lookup"><span data-stu-id="57bf0-106">Every development journey starts with a look back at what other developers have successfully built - mixed reality is no different.</span></span> <span data-ttu-id="57bf0-107">Tous nos tutoriels et exemples d’applications sont actuellement créés dans Unity ou Unreal.</span><span class="sxs-lookup"><span data-stu-id="57bf0-107">Currently, all of our tutorials and sample apps are built in Unity or Unreal.</span></span> <span data-ttu-id="57bf0-108">À mesure que nous développerons du contenu pour d’autres moteurs et plateformes, nous ajouterons des titres à la table des matières.</span><span class="sxs-lookup"><span data-stu-id="57bf0-108">As we develop content for other engines and platforms, you'll find them under the relevant heading in the Table of Contents.</span></span>

## <a name="sample-apps"></a><span data-ttu-id="57bf0-109">Exemples d’application</span><span class="sxs-lookup"><span data-stu-id="57bf0-109">Sample apps</span></span>

[!INCLUDE[](includes/tabs-samples.md)]

## <a name="feature-samples"></a><span data-ttu-id="57bf0-110">Exemples de fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="57bf0-110">Feature samples</span></span>

<span data-ttu-id="57bf0-111">Les exemples de fonctionnalités listés ci-dessous correspondent à des implémentations spécifiques traitées dans notre documentation. Ils couvrent tout un éventail de plateformes de développement et de périphériques matériels.</span><span class="sxs-lookup"><span data-stu-id="57bf0-111">The feature samples listed below correspond to specific implementations that are covered in our documentation and covers a range of development platforms and hardware devices.</span></span>

### <a name="research-mode"></a><span data-ttu-id="57bf0-112">Mode Recherche</span><span class="sxs-lookup"><span data-stu-id="57bf0-112">Research Mode</span></span>

<span data-ttu-id="57bf0-113">Le mode Recherche a été introduit dans la 1re génération des HoloLens afin de permettre l’accès aux capteurs clés de l’appareil, en particulier pour les applications de recherche qui ne sont pas destinées au déploiement.</span><span class="sxs-lookup"><span data-stu-id="57bf0-113">Research Mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span> <span data-ttu-id="57bf0-114">Les exemples d’applications ci-dessous sont des exemples d’accès et d’enregistrement des flux du mode Recherche. Ils correspondent également à des exemples d’utilisation des propriétés [intrinsèques et extrinsèques](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).</span><span class="sxs-lookup"><span data-stu-id="57bf0-114">The sample applications below are examples for accessing and recording Research Mode streams and using the [intrinsics and extrinsics](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).</span></span>

<br>

| <span data-ttu-id="57bf0-115">Article de référence</span><span class="sxs-lookup"><span data-stu-id="57bf0-115">Reference article</span></span> | <span data-ttu-id="57bf0-116">Exemple d’application</span><span class="sxs-lookup"><span data-stu-id="57bf0-116">Sample application</span></span> |
| --- | --- |
| [<span data-ttu-id="57bf0-117">Mode Recherche</span><span class="sxs-lookup"><span data-stu-id="57bf0-117">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="57bf0-118">HoloLens (1ère génération)</span><span class="sxs-lookup"><span data-stu-id="57bf0-118">HoloLens (1st gen)</span></span>](https://github.com/microsoft/HoloLensForCV/tree/master/Samples) |
| [<span data-ttu-id="57bf0-119">Mode Recherche</span><span class="sxs-lookup"><span data-stu-id="57bf0-119">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="57bf0-120">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="57bf0-120">HoloLens 2</span></span>](https://github.com/microsoft/HoloLens2ForCV/tree/main/Samples) |

### <a name="qr-codes"></a><span data-ttu-id="57bf0-121">Codes QR</span><span class="sxs-lookup"><span data-stu-id="57bf0-121">QR codes</span></span>

<span data-ttu-id="57bf0-122">HoloLens 2 peut détecter les codes QR dans l’environnement situé autour du casque, ce qui permet d’établir un système de coordonnées à l’emplacement réel de chaque code.</span><span class="sxs-lookup"><span data-stu-id="57bf0-122">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span>

<br>

| <span data-ttu-id="57bf0-123">Article de référence</span><span class="sxs-lookup"><span data-stu-id="57bf0-123">Reference article</span></span> | <span data-ttu-id="57bf0-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="57bf0-124">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="57bf0-125">Codes QR</span><span class="sxs-lookup"><span data-stu-id="57bf0-125">QR codes</span></span>](platform-capabilities-and-apis/qr-code-tracking.md) | [<span data-ttu-id="57bf0-126">Suivi des codes QR dans Unity</span><span class="sxs-lookup"><span data-stu-id="57bf0-126">QR code tracking in Unity</span></span>](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes) |

### <a name="webrtc"></a><span data-ttu-id="57bf0-127">WebRTC</span><span class="sxs-lookup"><span data-stu-id="57bf0-127">WebRTC</span></span>

<span data-ttu-id="57bf0-128">Le projet MixedReality-WebRTC est une collection de composants destinés à aider les développeurs d’applications de réalité mixte à intégrer les transmissions audio, vidéo et de données pair à pair ainsi que les communications en temps réel dans leurs applications. Les composants WebRTC sont basés sur le protocole WebRTC pour la communication en temps réel (RTC), qui est pris en charge par la plupart des navigateurs web modernes.</span><span class="sxs-lookup"><span data-stu-id="57bf0-128">The MixedReality-WebRTC project is a collection of components to help mixed reality app developers to integrate peer-to-peer audio, video, and data real-time communication into their applications WebRTC components are based on the WebRTC protocol for Real-Time Communication (RTC), which is supported by most modern web browsers.</span></span>

<br>

| <span data-ttu-id="57bf0-129">Article de référence</span><span class="sxs-lookup"><span data-stu-id="57bf0-129">Reference article</span></span> | <span data-ttu-id="57bf0-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="57bf0-130">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="57bf0-131">WebRTC</span><span class="sxs-lookup"><span data-stu-id="57bf0-131">WebRTC</span></span>](https://microsoft.github.io/MixedReality-WebRTC) | [<span data-ttu-id="57bf0-132">Exemples d’applications WebRTC</span><span class="sxs-lookup"><span data-stu-id="57bf0-132">WebRTC sample apps</span></span>](https://github.com/microsoft/MixedReality-WebRTC/tree/master/examples) |

### <a name="holographic-mixed-reality-capture"></a><span data-ttu-id="57bf0-133">Capture de réalité mixte holographique</span><span class="sxs-lookup"><span data-stu-id="57bf0-133">Holographic Mixed Reality Capture</span></span>

<span data-ttu-id="57bf0-134">La capture de réalité mixte (MRC) permet de capturer une expérience utilisateur à la première personne, qui consiste à mélanger les mondes réel et numérique sous forme de photo ou de vidéo, et à partager ce que vous voyez avec les autres en temps réel.</span><span class="sxs-lookup"><span data-stu-id="57bf0-134">Mixed reality capture (MRC) captures the first-person experience of mixing real and digital worlds as a photo or video, sharing what you see with others in real-time.</span></span>

<br>

| <span data-ttu-id="57bf0-135">Article de référence</span><span class="sxs-lookup"><span data-stu-id="57bf0-135">Reference article</span></span> | <span data-ttu-id="57bf0-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="57bf0-136">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="57bf0-137">Capture de réalité mixte</span><span class="sxs-lookup"><span data-stu-id="57bf0-137">Mixed Reality Capture</span></span>](platform-capabilities-and-apis/mixed-reality-capture-for-developers.md) | [<span data-ttu-id="57bf0-138">Exemples de captures de réalité mixte</span><span class="sxs-lookup"><span data-stu-id="57bf0-138">Mixed Reality Capture samples</span></span>](/samples/microsoft/windows-universal-samples/holographicmixedrealitycapture/) |

### <a name="holographic-remoting"></a><span data-ttu-id="57bf0-139">Communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="57bf0-139">Holographic Remoting</span></span>

<span data-ttu-id="57bf0-140">Holographic Remoting Player est un complément qui se connecte aux applications et aux jeux PC prenant en charge la communication à distance holographique.</span><span class="sxs-lookup"><span data-stu-id="57bf0-140">The Holographic Remoting Player is a companion app that connects to PC apps and games that support Holographic Remoting.</span></span> <span data-ttu-id="57bf0-141">Holographic Remoting transmet en streaming le contenu holographique d’un PC vers votre Microsoft HoloLens en temps réel, à l’aide d’une connexion Wi-Fi. Il est pris en charge par HoloLens (1re génération) et HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="57bf0-141">Holographic Remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi connection, and is supported on HoloLens (1st gen) and HoloLens 2.</span></span>

<br>

| <span data-ttu-id="57bf0-142">Article de référence</span><span class="sxs-lookup"><span data-stu-id="57bf0-142">Reference article</span></span> | <span data-ttu-id="57bf0-143">Exemple</span><span class="sxs-lookup"><span data-stu-id="57bf0-143">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="57bf0-144">Communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="57bf0-144">Holographic Remoting</span></span>](platform-capabilities-and-apis/holographic-remoting-player.md) | [<span data-ttu-id="57bf0-145">Exemples de communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="57bf0-145">Holographic Remoting samples</span></span>](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples) |