---
title: Vue d’ensemble du système de limites
description: Page d’accueil du système de limites dans MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, système de limite,
ms.openlocfilehash: 405a2d06be5d929d5c276fc8cd7ab36b6b3cf68c
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121357"
---
# <a name="boundary-system"></a><span data-ttu-id="77293-104">Système de limites</span><span class="sxs-lookup"><span data-stu-id="77293-104">Boundary system</span></span>

<span data-ttu-id="77293-105">Le système de limites prend en charge la visualisation des composants limite de réalité virtuelle dans les applications de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="77293-105">The Boundary system provides support for visualizing Virtual Reality boundary components in mixed reality applications.</span></span> <span data-ttu-id="77293-106">Les limites définissent la zone dans laquelle les utilisateurs peuvent se déplacer en toute sécurité tout en portant un casque VR.</span><span class="sxs-lookup"><span data-stu-id="77293-106">Boundaries define the area in which users can safely move around while wearing a VR headset.</span></span> <span data-ttu-id="77293-107">Les limites sont un composant important d’une expérience de réalité mixte qui permet aux utilisateurs d’éviter les obstacles non visibles tout en portant un casque VR.</span><span class="sxs-lookup"><span data-stu-id="77293-107">Boundaries are an important component of a mixed reality experience to help users avoid unseen obstacles while wearing a VR headset.</span></span>

<span data-ttu-id="77293-108">De nombreuses plates-formes de réalité virtuelle fournissent un affichage automatique, par exemple un contour blanc superposé sur le monde virtuel lorsque l’utilisateur ou le contrôleur approche de la limite.</span><span class="sxs-lookup"><span data-stu-id="77293-108">Many Virtual Reality platforms provide an automatic display, for example a white outline superimposed on the virtual world as the user or their controller nears the boundary.</span></span> <span data-ttu-id="77293-109">Le système de limite du Toolkit de réalité mixte étend cette fonctionnalité pour permettre l’affichage d’un plan de la zone suivie, d’un plan de plancher et d’autres fonctionnalités qui peuvent être utilisées pour fournir des informations supplémentaires aux utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="77293-109">The Mixed Reality Toolkit's Boundary System extends this feature to enable the display of an outline of the tracked area, a floor plane and other features that can be used to provide additional information to users.</span></span>

## <a name="getting-started"></a><span data-ttu-id="77293-110">Prise en main</span><span class="sxs-lookup"><span data-stu-id="77293-110">Getting started</span></span>

<span data-ttu-id="77293-111">L’ajout de la prise en charge des limites requiert deux composants clés du kit de tâches de la réalité mixte : le système de limites et une plateforme de réalité virtuelle configurée avec une limite.</span><span class="sxs-lookup"><span data-stu-id="77293-111">Adding support for boundaries requires two key components of the Mixed Reality Toolkit: the Boundary System and a Virtual Reality platform configured with a boundary.</span></span>

1. <span data-ttu-id="77293-112">[Activer](#enable-boundary-system) le système de limites</span><span class="sxs-lookup"><span data-stu-id="77293-112">[Enable](#enable-boundary-system) the boundary system</span></span>
2. <span data-ttu-id="77293-113">[Configurer](#configure-boundary-visualization) la visualisation des limites</span><span class="sxs-lookup"><span data-stu-id="77293-113">[Configure](#configure-boundary-visualization) the boundary visualization</span></span>
3. <span data-ttu-id="77293-114">[Créez et déployez](#build-and-deploy) sur une plateforme VR avec une limite configurée</span><span class="sxs-lookup"><span data-stu-id="77293-114">[Build and deploy](#build-and-deploy) to a VR platform with a configured boundary</span></span>

## <a name="enable-boundary-system"></a><span data-ttu-id="77293-115">Activer le système de limite</span><span class="sxs-lookup"><span data-stu-id="77293-115">Enable boundary system</span></span>

<span data-ttu-id="77293-116">Le système de limites est géré par l’objet MixedRealityToolkit (ou un autre composant d' [inscription de service](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) ).</span><span class="sxs-lookup"><span data-stu-id="77293-116">The Boundary System is managed by the MixedRealityToolkit object (or another [service registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) component).</span></span>

<span data-ttu-id="77293-117">Les étapes suivantes supposent l’utilisation de l’objet MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="77293-117">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="77293-118">Les étapes requises pour les autres bureaux d’enregistrement de services peuvent être différentes.</span><span class="sxs-lookup"><span data-stu-id="77293-118">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="77293-119">Sélectionnez l’objet MixedRealityToolkit dans la hiérarchie de la scène.</span><span class="sxs-lookup"><span data-stu-id="77293-119">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![Hiérarchie de scène configurée par MRTK](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="77293-121">Naviguez dans le panneau de l’inspecteur jusqu’à la section système de limite et cochez Activer</span><span class="sxs-lookup"><span data-stu-id="77293-121">Navigate the Inspector panel to the Boundary System section and check Enable</span></span>

    ![Activer le système de limites](../images/boundary/MRTKConfig_Boundary.png)

1. <span data-ttu-id="77293-123">Sélectionnez l’implémentation du système de limites.</span><span class="sxs-lookup"><span data-stu-id="77293-123">Select the Boundary System implementation.</span></span> <span data-ttu-id="77293-124">L’implémentation de classe par défaut fournie par MRTK est le [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="77293-124">The default class implementation provided by the MRTK is the [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)</span></span>

    ![Sélectionner l’implémentation du système de limites](../images/boundary/BoundarySelectSystemType.png)

> [!NOTE]
> <span data-ttu-id="77293-126">Toutes les implémentations du système de limites doivent étendre [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)</span><span class="sxs-lookup"><span data-stu-id="77293-126">All Boundary System implementation must extend the [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)</span></span>

## <a name="configure-boundary-visualization"></a><span data-ttu-id="77293-127">Configurer la visualisation des limites</span><span class="sxs-lookup"><span data-stu-id="77293-127">Configure boundary visualization</span></span>

<span data-ttu-id="77293-128">Le [système de limites utilise un profil de configuration](configuring-boundary-visualization.md) pour spécifier les composants de limite à afficher et pour configurer leur apparence.</span><span class="sxs-lookup"><span data-stu-id="77293-128">The [Boundary System uses a configuration profile](configuring-boundary-visualization.md) to specify which boundary components are to be displayed and to configure their appearance.</span></span>

![Options de visualisation des limites](../images/boundary/BoundaryVisualizationProfile.png)

> [!NOTE]
> <span data-ttu-id="77293-130">Le système de limite est préconfiguré pour les utilisateurs du profil par défaut `DefaultMixedRealityBoundaryVisualizationProfile` (ressources/MRTK/Kit de développement logiciel (SDK)/profils) pour afficher un plan d’étage, la zone de lecture et la zone suivie.</span><span class="sxs-lookup"><span data-stu-id="77293-130">Users of the default profile, `DefaultMixedRealityBoundaryVisualizationProfile` (Assets/MRTK/SDK/Profiles) will have the boundary system pre-configured to display a floor plane, the play area and the tracked area.</span></span>

## <a name="build-and-deploy"></a><span data-ttu-id="77293-131">Générer et déployer</span><span class="sxs-lookup"><span data-stu-id="77293-131">Build and deploy</span></span>

<span data-ttu-id="77293-132">Une fois que le système de limites est configuré avec les options de visualisation souhaitées, le projet peut être créé sur la plateforme cible.</span><span class="sxs-lookup"><span data-stu-id="77293-132">Once the boundary system is configured with the desired visualization options, the project can be built deployed to the target platform.</span></span>

> [!NOTE]
> <span data-ttu-id="77293-133">Le mode de lecture Unity permet la visualisation dans l’éditeur de la limite configurée.</span><span class="sxs-lookup"><span data-stu-id="77293-133">Unity Play Mode enables in-editor visualization of the configured boundary.</span></span> <span data-ttu-id="77293-134">Cette fonctionnalité permet un développement et des tests rapides sans nécessiter l’étape de création et de déploiement.</span><span class="sxs-lookup"><span data-stu-id="77293-134">This feature enables rapid development and testing without requiring the build and deploy step.</span></span> <span data-ttu-id="77293-135">Veillez à effectuer des tests d’acceptation finaux à l’aide d’une version générée et déployée de l’application, qui s’exécute sur le matériel et la plateforme cibles.</span><span class="sxs-lookup"><span data-stu-id="77293-135">Be sure to do final acceptance testing using an built and deployed version of the application, running on the target hardware and platform.</span></span>

## <a name="accessing-boundary-system-via-code"></a><span data-ttu-id="77293-136">Accès au système de limites par le biais du code</span><span class="sxs-lookup"><span data-stu-id="77293-136">Accessing boundary system via code</span></span>

<span data-ttu-id="77293-137">S’il est activé et configuré, le système de limite est accessible via la classe d’assistance statique CoreServices.</span><span class="sxs-lookup"><span data-stu-id="77293-137">If enabled and configured, the Boundary System can be accessed via the CoreServices static helper class.</span></span> <span data-ttu-id="77293-138">La référence peut ensuite être utilisée pour modifier dynamiquement les paramètres de limite et accéder aux GameObjectss associés gérés par le système.</span><span class="sxs-lookup"><span data-stu-id="77293-138">The reference can then be used to dynamically change the Boundary parameters and access related GameObjects managed by the system.</span></span>

```c#
// Hide Boundary Walls at runtime
CoreServices.BoundarySystem.ShowBoundaryWalls = false;

// Get Unity GameObject for the floor visualization in scene
GameObject floorVisual = CoreServices.BoundarySystem.GetFloorVisualization();
```

## <a name="see-also"></a><span data-ttu-id="77293-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="77293-139">See also</span></span>

- [<span data-ttu-id="77293-140">Documentation sur l’API de limite</span><span class="sxs-lookup"><span data-stu-id="77293-140">Boundary API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [<span data-ttu-id="77293-141">Configuration de la visualisation des limites</span><span class="sxs-lookup"><span data-stu-id="77293-141">Configuring the Boundary Visualization</span></span>](configuring-boundary-visualization.md)
