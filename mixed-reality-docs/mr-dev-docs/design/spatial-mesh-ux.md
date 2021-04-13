---
title: Visualisation de maillage spatial
description: Découvrez les instructions de conception et la compréhension de l’environnement physique avec la visualisation de maillage spatial dans MRTK.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Réalité mixte, HoloLens, contrôles d’interface utilisateur, interaction, interface utilisateur, expérience utilisateur, conception UX, interface utilisateur spatiale, interaction spatiale, interface utilisateur 3D, expérience utilisateur 3D, casque de la réalité mixte, casque de réalité mixte, casque de réalité virtuelle, HoloLens, MRTK, kit de mise en réalité mixte
ms.openlocfilehash: 0d8d2811c2fae96f679eeb1df2f1053e7ecf5def
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300344"
---
# <a name="spatial-mesh"></a><span data-ttu-id="1d45c-104">Maillage spatial</span><span class="sxs-lookup"><span data-stu-id="1d45c-104">Spatial mesh</span></span>

![Maillage spatial](images/MRTK_PulseShader_SpatialMesh.gif)

<span data-ttu-id="1d45c-106">Les utilisateurs apprennent comment un appareil perçoit et comprend l’environnement physique grâce à la visualisation de maillage spatial.</span><span class="sxs-lookup"><span data-stu-id="1d45c-106">Users learn how a device perceives and understands the physical environment through spatial mesh visualization.</span></span> <span data-ttu-id="1d45c-107">Une visualisation de maillage spatial appropriée peut créer une expérience délicieuse et magique tout en fournissant un contexte spatial.</span><span class="sxs-lookup"><span data-stu-id="1d45c-107">Proper spatial mesh visualization can create a delightful and magical experience while providing spatial context.</span></span>  

## <a name="design-guideline"></a><span data-ttu-id="1d45c-108">Directives de conception</span><span class="sxs-lookup"><span data-stu-id="1d45c-108">Design guideline</span></span>

<span data-ttu-id="1d45c-109">Il est important d’autoriser l’utilisateur à se concentrer et à interagir avec le contenu.</span><span class="sxs-lookup"><span data-stu-id="1d45c-109">It's important to allow the user to focus and interact with content.</span></span> <span data-ttu-id="1d45c-110">La visualisation continue du maillage spatial en arrière-plan peut être gênante.</span><span class="sxs-lookup"><span data-stu-id="1d45c-110">Continuous visualization of the spatial mesh in the background can be distracting.</span></span> <span data-ttu-id="1d45c-111">Nous vous recommandons de visualiser l’environnement avec modération, qu’une seule fois au lancement initial ou lorsque l’utilisateur montre clairement qu’il souhaite voir la maille environnementale en ciblant et en appuyant sur de l’air.</span><span class="sxs-lookup"><span data-stu-id="1d45c-111">We recommend visualizing the environment sparingly, either only once in the initial launch or when the user clearly shows they want to see the environmental mesh by targeting and air-tapping space.</span></span> <span data-ttu-id="1d45c-112">Vous pouvez observer ce comportement dans le portail de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="1d45c-112">You can observe this behavior in the Mixed Reality Portal.</span></span>
<br>

## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="1d45c-113">Visualisation de maillage spatial dans MRTK (ensemble d’outils de réalité mixte) pour Unity</span><span class="sxs-lookup"><span data-stu-id="1d45c-113">Spatial mesh visualization in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="1d45c-114">MRTK fournit plusieurs documents pour la visualisation de maillage spatial.</span><span class="sxs-lookup"><span data-stu-id="1d45c-114">MRTK provides several materials for the spatial mesh visualization.</span></span>

- <span data-ttu-id="1d45c-115">**MRTK_Wireframe. mat, MRTK_Wireframe. mat**: matériau de maillage spatial statique par défaut, qui affiche les contours de maillage sans animation.</span><span class="sxs-lookup"><span data-stu-id="1d45c-115">**MRTK_Wireframe.mat, MRTK_Wireframe.mat**: Default static spatial mesh material, which shows the mesh outlines without animation.</span></span> <span data-ttu-id="1d45c-116">Ce document est utile à des fins de débogage, car il affiche les géométries entières du maillage spatial.</span><span class="sxs-lookup"><span data-stu-id="1d45c-116">This material is useful for debugging purposes since it shows the entire spatial mesh geometries.</span></span> <span data-ttu-id="1d45c-117">Toutefois, il n’est pas recommandé pour la production.</span><span class="sxs-lookup"><span data-stu-id="1d45c-117">However, it isn't recommended for production.</span></span>
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- <span data-ttu-id="1d45c-118">**MRTK_SurfaceReconstruction. mat**: ce matériau vous donne un effet d’impulsion animée sur le maillage spatial.</span><span class="sxs-lookup"><span data-stu-id="1d45c-118">**MRTK_SurfaceReconstruction.mat**: This material gives you an animated pulse effect on the spatial mesh.</span></span> <span data-ttu-id="1d45c-119">Vous pouvez utiliser ce document pour visualiser l’environnement à un moment donné ou sur l’entrée d’air de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1d45c-119">You can use this material to visualize the environment at a specific moment or on the user's air-tap input.</span></span> <span data-ttu-id="1d45c-120">Consultez la scène **PulseShaderExamples. Unity** pour obtenir des exemples.</span><span class="sxs-lookup"><span data-stu-id="1d45c-120">See **PulseShaderExamples.unity** scene for the examples.</span></span>
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">

* <span data-ttu-id="1d45c-121">Pour plus d’informations, consultez [MRTK-spatial Awareness](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) et [MRTK-Pulse Shader](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/experimental/pulse-shader).</span><span class="sxs-lookup"><span data-stu-id="1d45c-121">For more information, see [MRTK - Spatial Awareness](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) and [MRTK - Pulse Shader](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/experimental/pulse-shader).</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="1d45c-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d45c-122">See also</span></span>

* [<span data-ttu-id="1d45c-123">Curseurs</span><span class="sxs-lookup"><span data-stu-id="1d45c-123">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="1d45c-124">Rayon émanant de la main</span><span class="sxs-lookup"><span data-stu-id="1d45c-124">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="1d45c-125">Button</span><span class="sxs-lookup"><span data-stu-id="1d45c-125">Button</span></span>](button.md)
* [<span data-ttu-id="1d45c-126">Objet avec interaction possible</span><span class="sxs-lookup"><span data-stu-id="1d45c-126">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="1d45c-127">Rectangle englobant et barre de l’application</span><span class="sxs-lookup"><span data-stu-id="1d45c-127">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="1d45c-128">Manipulation</span><span class="sxs-lookup"><span data-stu-id="1d45c-128">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="1d45c-129">Menu de la main</span><span class="sxs-lookup"><span data-stu-id="1d45c-129">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="1d45c-130">Menu proche</span><span class="sxs-lookup"><span data-stu-id="1d45c-130">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="1d45c-131">Collection d’objets</span><span class="sxs-lookup"><span data-stu-id="1d45c-131">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="1d45c-132">Commande vocale</span><span class="sxs-lookup"><span data-stu-id="1d45c-132">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="1d45c-133">Clavier</span><span class="sxs-lookup"><span data-stu-id="1d45c-133">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="1d45c-134">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="1d45c-134">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="1d45c-135">Tablette</span><span class="sxs-lookup"><span data-stu-id="1d45c-135">Slate</span></span>](slate.md)
* [<span data-ttu-id="1d45c-136">Curseur</span><span class="sxs-lookup"><span data-stu-id="1d45c-136">Slider</span></span>](slider.md)
* [<span data-ttu-id="1d45c-137">Nuanceur</span><span class="sxs-lookup"><span data-stu-id="1d45c-137">Shader</span></span>](shader.md)
* [<span data-ttu-id="1d45c-138">Billboarding et tag-along</span><span class="sxs-lookup"><span data-stu-id="1d45c-138">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="1d45c-139">Affichage de la progression</span><span class="sxs-lookup"><span data-stu-id="1d45c-139">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="1d45c-140">Aimantation de surface</span><span class="sxs-lookup"><span data-stu-id="1d45c-140">Surface magnetism</span></span>](surface-magnetism.md)
