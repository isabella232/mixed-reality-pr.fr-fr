---
title: Spectator View
description: Visualisez des hologrammes à partir d’un appareil externe pour montrer ou enregistrer une expérience de réalité mixte sur un écran externe.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Spectator View, iPhone, iOS, iPad, OpenCV, caméra, ARKit, HoloLens, réalité mixte, MixedRealityToolkit, démonstration, enregistrement
ms.openlocfilehash: c344edea9b499bdff15d1d93e400b8be626a63b6
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530109"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a><span data-ttu-id="d81c1-104">Spectator View pour HoloLens et HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d81c1-104">Spectator View for HoloLens and HoloLens 2</span></span>

![Marqueur](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a><span data-ttu-id="d81c1-106">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="d81c1-106">Overview</span></span>

<span data-ttu-id="d81c1-107">Quand nous portons un appareil HoloLens, il est facile d’oublier qu’une personne qui n’en a pas est incapable de voir les merveilles qui s’offrent à nos yeux.</span><span class="sxs-lookup"><span data-stu-id="d81c1-107">When you're wearing a HoloLens, it's easy to forget a person without one can't experience the same wonders you're seeing.</span></span> <span data-ttu-id="d81c1-108">Spectator View permet à d’autres personnes de voir ce qu’un utilisateur HoloLens voit sur un écran 2D.</span><span class="sxs-lookup"><span data-stu-id="d81c1-108">Spectator View lets others see what a HoloLens user sees on a 2D screen.</span></span> <span data-ttu-id="d81c1-109">Il offre un moyen rapide et économique d’enregistrer des hologrammes en HD avec des appareils mobiles, et permet de créer des enregistrements d’hologrammes de qualité avec des caméras vidéo.</span><span class="sxs-lookup"><span data-stu-id="d81c1-109">It's also a fast and affordable approach to recording holograms in HD with mobile devices and getting great quality recordings of holograms with video cameras.</span></span>

## <a name="key-resources"></a><span data-ttu-id="d81c1-110">Ressources clés</span><span class="sxs-lookup"><span data-stu-id="d81c1-110">Key Resources</span></span>

* [<span data-ttu-id="d81c1-111">**Spectator View sur GitHub**</span><span class="sxs-lookup"><span data-stu-id="d81c1-111">**Spectator View on GitHub**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView)
* [<span data-ttu-id="d81c1-112">**Documentation sur Spectator View**</span><span class="sxs-lookup"><span data-stu-id="d81c1-112">**Spectator View Documentation**</span></span>](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [<span data-ttu-id="d81c1-113">**Exemples Spectator View**</span><span class="sxs-lookup"><span data-stu-id="d81c1-113">**Spectator View Samples**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a><span data-ttu-id="d81c1-114">Scénarios d’utilisation</span><span class="sxs-lookup"><span data-stu-id="d81c1-114">Use Cases</span></span>

* <span data-ttu-id="d81c1-115">Vous pouvez enregistrer une expérience de réalité mixte à l’aide d’un appareil iPhone ou Android.</span><span class="sxs-lookup"><span data-stu-id="d81c1-115">You can record a mixed reality experience using an iPhone or Android device.</span></span> <span data-ttu-id="d81c1-116">Enregistrez en Full HD et appliquez un anticrénelage aux hologrammes et aux ombres. Vous disposez d’une solution de capture de vidéos d’hologrammes économique et rapide.</span><span class="sxs-lookup"><span data-stu-id="d81c1-116">Record in full HD and apply anti-aliasing to holograms and shadow for a cost-effective and quick way to capture video of holograms.</span></span>
* <span data-ttu-id="d81c1-117">Diffusez en streaming des expériences de réalité mixte en direct sur un appareil Apple TV, directement à partir de votre iPhone ou iPad, sans aucun décalage !</span><span class="sxs-lookup"><span data-stu-id="d81c1-117">Stream live mixed reality experiences to an Apple TV directly from your iPhone or iPad, lag-free!</span></span>
* <span data-ttu-id="d81c1-118">Partagez l’expérience avec des invités : donnez aux personnes ne disposant pas d’un appareil HoloLens la possibilité de voir des hologrammes directement sur leur téléphone ou leur tablette.</span><span class="sxs-lookup"><span data-stu-id="d81c1-118">Share the experience with guests: Let non-HoloLens users experience holograms directly from their phones or tablets.</span></span>

## <a name="current-features"></a><span data-ttu-id="d81c1-119">Fonctionnalités actuelles</span><span class="sxs-lookup"><span data-stu-id="d81c1-119">Current Features</span></span>

* <span data-ttu-id="d81c1-120">Synchronisation spatiale des hologrammes pour permettre à tout le monde de voir les hologrammes exactement au même endroit.</span><span class="sxs-lookup"><span data-stu-id="d81c1-120">Spatial synchronization of Holograms, so everyone sees holograms in the exact same place.</span></span>
* <span data-ttu-id="d81c1-121">Prise en charge d’iOS (appareils compatibles ARKit) et d’Android (appareils compatibles ARCore).</span><span class="sxs-lookup"><span data-stu-id="d81c1-121">iOS (ARKit-enabled devices) and Android (ARCore-enabled devices) support.</span></span>
<span data-ttu-id="d81c1-122">Plusieurs invités iOS.</span><span class="sxs-lookup"><span data-stu-id="d81c1-122">Multiple iOS guests.</span></span>
<span data-ttu-id="d81c1-123">Enregistrement de vidéos + hologrammes + son ambiant + son des hologrammes.</span><span class="sxs-lookup"><span data-stu-id="d81c1-123">Recording of video + holograms + ambient sound + hologram sound.</span></span>
<span data-ttu-id="d81c1-124">Feuille de partage permettant d’enregistrer une vidéo, de l’envoyer par e-mail ou de la partager avec d’autres applications compatibles.</span><span class="sxs-lookup"><span data-stu-id="d81c1-124">Share sheet so you can save video, email it, or share with other supporting apps.</span></span>

<span data-ttu-id="d81c1-125">![Marker](images/SpecViewPhoneDemo.jpg)
![Marker](images/hololensspectatorview-500px.jpg) ![Marker](images/spectatorview-300px.png)</span><span class="sxs-lookup"><span data-stu-id="d81c1-125">![Marker](images/SpecViewPhoneDemo.jpg)
![Marker](images/hololensspectatorview-500px.jpg) ![Marker](images/spectatorview-300px.png)</span></span>

<span data-ttu-id="d81c1-126">Le tableau suivant liste différentes fonctionnalités de Spectator View.</span><span class="sxs-lookup"><span data-stu-id="d81c1-126">The following table shows different Spectator View functionality and their capabilities.</span></span> <span data-ttu-id="d81c1-127">Choisissez l’option qui correspond le mieux à vos besoins en matière d’enregistrement vidéo :</span><span class="sxs-lookup"><span data-stu-id="d81c1-127">Choose the option that best fits your video recording needs:</span></span>

|      <span data-ttu-id="d81c1-128">Fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="d81c1-128">Functionality</span></span>                                | <span data-ttu-id="d81c1-129">Mobile</span><span class="sxs-lookup"><span data-stu-id="d81c1-129">Mobile</span></span>                  |                    <span data-ttu-id="d81c1-130">Caméra vidéo</span><span class="sxs-lookup"><span data-stu-id="d81c1-130">Video Camera</span></span>              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| <span data-ttu-id="d81c1-131">Qualité HD</span><span class="sxs-lookup"><span data-stu-id="d81c1-131">HD quality</span></span>                           |         <span data-ttu-id="d81c1-132">Full HD</span><span class="sxs-lookup"><span data-stu-id="d81c1-132">Full HD</span></span>         |        <span data-ttu-id="d81c1-133">Enregistrement de qualité professionnelle (varie selon la caméra vidéo)</span><span class="sxs-lookup"><span data-stu-id="d81c1-133">Professional quality filming (as determined by video camera)</span></span>      |
| <span data-ttu-id="d81c1-134">Déplacement aisé de la caméra</span><span class="sxs-lookup"><span data-stu-id="d81c1-134">Easy camera movement</span></span>                 |            <span data-ttu-id="d81c1-135">✔</span><span class="sxs-lookup"><span data-stu-id="d81c1-135">✔</span></span>            |                      <span data-ttu-id="d81c1-136">✔</span><span class="sxs-lookup"><span data-stu-id="d81c1-136">✔</span></span>                      |
| <span data-ttu-id="d81c1-137">Vue externe</span><span class="sxs-lookup"><span data-stu-id="d81c1-137">Third-person view</span></span>                    |            <span data-ttu-id="d81c1-138">✔</span><span class="sxs-lookup"><span data-stu-id="d81c1-138">✔</span></span>            |                      <span data-ttu-id="d81c1-139">✔</span><span class="sxs-lookup"><span data-stu-id="d81c1-139">✔</span></span>                      |
| <span data-ttu-id="d81c1-140">Diffusion en streaming sur des écrans</span><span class="sxs-lookup"><span data-stu-id="d81c1-140">Can be streamed to screens</span></span>           |            <span data-ttu-id="d81c1-141">✔</span><span class="sxs-lookup"><span data-stu-id="d81c1-141">✔</span></span>            |                      <span data-ttu-id="d81c1-142">✔</span><span class="sxs-lookup"><span data-stu-id="d81c1-142">✔</span></span>                      |
| <span data-ttu-id="d81c1-143">Portable</span><span class="sxs-lookup"><span data-stu-id="d81c1-143">Portable</span></span>                             |            <span data-ttu-id="d81c1-144">✔</span><span class="sxs-lookup"><span data-stu-id="d81c1-144">✔</span></span>            |                                             |
| <span data-ttu-id="d81c1-145">Sans fil</span><span class="sxs-lookup"><span data-stu-id="d81c1-145">Wireless</span></span>                             |            <span data-ttu-id="d81c1-146">✔</span><span class="sxs-lookup"><span data-stu-id="d81c1-146">✔</span></span>            |                                             |
| <span data-ttu-id="d81c1-147">Matériel supplémentaire requis</span><span class="sxs-lookup"><span data-stu-id="d81c1-147">Additional required hardware</span></span>         |     <span data-ttu-id="d81c1-148">Téléphone Android, iPhone</span><span class="sxs-lookup"><span data-stu-id="d81c1-148">Android phone, iPhone</span></span>    | <span data-ttu-id="d81c1-149">HoloLens + plateforme + trépied + caméra vidéo + PC + Unity</span><span class="sxs-lookup"><span data-stu-id="d81c1-149">HoloLens + Rig + Tripod + Video Camera + PC + Unity</span></span> |
| <span data-ttu-id="d81c1-150">Investissement matériel</span><span class="sxs-lookup"><span data-stu-id="d81c1-150">Hardware investment</span></span>                  |           <span data-ttu-id="d81c1-151">Faible</span><span class="sxs-lookup"><span data-stu-id="d81c1-151">Low</span></span>            |                     <span data-ttu-id="d81c1-152">Élevé</span><span class="sxs-lookup"><span data-stu-id="d81c1-152">High</span></span>                    |
| <span data-ttu-id="d81c1-153">Système multiplateforme</span><span class="sxs-lookup"><span data-stu-id="d81c1-153">Cross-platform</span></span>                       |           <span data-ttu-id="d81c1-154">Android, iOS</span><span class="sxs-lookup"><span data-stu-id="d81c1-154">Android, iOS</span></span>   |                                             |
| <span data-ttu-id="d81c1-155">Contenu synchronisé</span><span class="sxs-lookup"><span data-stu-id="d81c1-155">Synchronized content</span></span>                 |            <span data-ttu-id="d81c1-156">✔</span><span class="sxs-lookup"><span data-stu-id="d81c1-156">✔</span></span>            |                      <span data-ttu-id="d81c1-157">✔</span><span class="sxs-lookup"><span data-stu-id="d81c1-157">✔</span></span>                      |
| <span data-ttu-id="d81c1-158">Durée d’installation du runtime</span><span class="sxs-lookup"><span data-stu-id="d81c1-158">Runtime setup duration</span></span>               |         <span data-ttu-id="d81c1-159">Instantané</span><span class="sxs-lookup"><span data-stu-id="d81c1-159">Instant</span></span>          |                     <span data-ttu-id="d81c1-160">Lente</span><span class="sxs-lookup"><span data-stu-id="d81c1-160">Slow</span></span>                    |
## <a name="see-also"></a><span data-ttu-id="d81c1-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d81c1-161">See also</span></span>

* [<span data-ttu-id="d81c1-162">MRC (Mixed Reality Capture)</span><span class="sxs-lookup"><span data-stu-id="d81c1-162">Mixed reality capture</span></span>](../../mixed-reality-capture.md) 
* [<span data-ttu-id="d81c1-163">Capture de Réalité Mixte pour les développeurs</span><span class="sxs-lookup"><span data-stu-id="d81c1-163">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="d81c1-164">Expériences partagées dans Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="d81c1-164">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
