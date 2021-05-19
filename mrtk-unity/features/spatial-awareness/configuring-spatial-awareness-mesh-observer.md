---
title: Configuration de l’observateur de maillage de reconnaissance spatiale
description: Comment configurer l’observateur de maillage spatial prêt à l’emploi dans MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 0d71a32d76624698e78b8123f427ddefc08f3d0b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144959"
---
# <a name="configuring-mesh-observers-for-device"></a><span data-ttu-id="5657f-104">Configuration des observateurs de maillage pour l’appareil</span><span class="sxs-lookup"><span data-stu-id="5657f-104">Configuring mesh observers for device</span></span>

<span data-ttu-id="5657f-105">Ce guide vous aidera à configurer l’observateur de maillage spatial prêt à l’emploi dans MRTK, qui prend en charge la plateforme Windows Mixed Reality (c.-à-d.</span><span class="sxs-lookup"><span data-stu-id="5657f-105">This guide will walk through configuring the out-of-box Spatial Mesh Observer in MRTK which supports the Windows Mixed Reality platform (i.e</span></span> <span data-ttu-id="5657f-106">HoloLens).</span><span class="sxs-lookup"><span data-stu-id="5657f-106">HoloLens).</span></span> <span data-ttu-id="5657f-107">L’implémentation par défaut fournie par le kit d’outils de réalité mixte est la classe [WindowsMixedRealitySpatialMeshObserver](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) .</span><span class="sxs-lookup"><span data-stu-id="5657f-107">The default implementation provided by the Mixed Reality Toolkit is the [WindowsMixedRealitySpatialMeshObserver](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) class.</span></span> <span data-ttu-id="5657f-108">La plupart des propriétés de cet article s’appliquent à d’autres [implémentations d’observateurs personnalisées](create-data-provider.md).</span><span class="sxs-lookup"><span data-stu-id="5657f-108">Many of the properties in this article though apply for other [custom Observer implementations](create-data-provider.md).</span></span>

## <a name="profile-settings"></a><span data-ttu-id="5657f-109">Paramètres du profil</span><span class="sxs-lookup"><span data-stu-id="5657f-109">Profile settings</span></span>

<span data-ttu-id="5657f-110">Les deux éléments suivants doivent être définis en premier lors de la configuration d’un profil d’observateur de maillage spatial pour le [système de sensibilisation spatiale](spatial-awareness-getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="5657f-110">The following two items must be defined first when configuring a Spatial Mesh Observer profile for the [Spatial Awareness system](spatial-awareness-getting-started.md).</span></span>

1. <span data-ttu-id="5657f-111">Implémentation concrète du type observer</span><span class="sxs-lookup"><span data-stu-id="5657f-111">The concrete observer type implementation</span></span>
1. <span data-ttu-id="5657f-112">Liste des plateformes prises en charge pour l’exécution de cet observateur</span><span class="sxs-lookup"><span data-stu-id="5657f-112">list of supported platform(s) to run this observer</span></span>

> [!NOTE]
> <span data-ttu-id="5657f-113">Tous les observateurs doivent étendre l’interface [IMixedRealitySpatialAwarenessObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) .</span><span class="sxs-lookup"><span data-stu-id="5657f-113">All observers must extend the [IMixedRealitySpatialAwarenessObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface.</span></span>

![Types de plateforme des paramètres généraux de l’observateur de maillage](../images/spatial-awareness/SpatialAwarenessMeshObserverProfile_TypesPlatforms.png)

### <a name="general-settings"></a><span data-ttu-id="5657f-115">Paramètres généraux :</span><span class="sxs-lookup"><span data-stu-id="5657f-115">General settings</span></span>

![Paramètres généraux de l’observateur de maille-paramètres documents](../images/spatial-awareness/MeshObserverGeneralSettings.png)

<span data-ttu-id="5657f-117">**Comportement de démarrage**</span><span class="sxs-lookup"><span data-stu-id="5657f-117">**Startup Behavior**</span></span>

<span data-ttu-id="5657f-118">Le comportement de démarrage spécifie si l’observateur doit commencer à s’exécuter lors de sa première instanciation.</span><span class="sxs-lookup"><span data-stu-id="5657f-118">The startup behavior specifies whether the observer will begin running when first instantiated.</span></span> <span data-ttu-id="5657f-119">Les deux options sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="5657f-119">The two options are:</span></span>

* <span data-ttu-id="5657f-120">*Démarrage automatique* -la valeur par défaut à laquelle l’observateur doit commencer l’opération après l’initialisation</span><span class="sxs-lookup"><span data-stu-id="5657f-120">*Auto Start* - The default value whereby the observer will begin operation after initialization</span></span>
* <span data-ttu-id="5657f-121">*Démarrage manuel* -l’observateur attend d’être redirigé vers le démarrage</span><span class="sxs-lookup"><span data-stu-id="5657f-121">*Manual Start* - The Observer will wait to be directed to start</span></span>

<span data-ttu-id="5657f-122">Si vous utilisez le *démarrage manuel*, l’un d’eux doit [reprendre et le suspendre au moment de l’exécution par le biais du code](usage-guide.md#starting-and-stopping-mesh-observation).</span><span class="sxs-lookup"><span data-stu-id="5657f-122">If using *Manual Start*, one must [resume and suspend them at runtime via code](usage-guide.md#starting-and-stopping-mesh-observation).</span></span>

<span data-ttu-id="5657f-123">**Intervalle de mise à jour**</span><span class="sxs-lookup"><span data-stu-id="5657f-123">**Update Interval**</span></span>

<span data-ttu-id="5657f-124">Durée, en secondes, entre les demandes à la plateforme pour mettre à jour les données de maillage spatiale.</span><span class="sxs-lookup"><span data-stu-id="5657f-124">The time, in seconds, between requests to the platform to update spatial mesh data.</span></span> <span data-ttu-id="5657f-125">Les valeurs standard sont comprises dans la plage de 0,1 et 5,0 secondes.</span><span class="sxs-lookup"><span data-stu-id="5657f-125">Typical values fall in the range of 0.1 and 5.0 seconds.</span></span>

<span data-ttu-id="5657f-126">**Est un observateur stationnaire**</span><span class="sxs-lookup"><span data-stu-id="5657f-126">**Is Stationary Observer**</span></span>

<span data-ttu-id="5657f-127">Indique si l’observateur doit rester stationnaire ou s’il doit être déplacé et mis à jour avec l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5657f-127">Indicates whether or not the observer is to remain stationary or to move and update with the user.</span></span> <span data-ttu-id="5657f-128">Si la valeur est true, la *forme observateur* avec le volume défini par les *étendues d’observation* reste à l’origine au démarrage.</span><span class="sxs-lookup"><span data-stu-id="5657f-128">If true, the *Observer Shape* with volume defined by *Observation Extents* will remain at the origin on startup.</span></span> <span data-ttu-id="5657f-129">Si la valeur est false, l’espace de l’observateur suivra la tête de l’utilisateur en tant qu’origine de la forme.</span><span class="sxs-lookup"><span data-stu-id="5657f-129">If false, the Observer space will follow the user's head as the shape's origin.</span></span>

<span data-ttu-id="5657f-130">Aucune donnée de maillage n’est calculée pour toute zone physique en dehors de l’espace de l’observateur, comme défini par les propriétés suivantes : *est un observateur stationnaire*, \* forme observateur \* \* et les *extensions d’observation*.</span><span class="sxs-lookup"><span data-stu-id="5657f-130">There will be no mesh data calculated for any physical area outside of the Observer space as defined by these properties: *Is Stationary Observer*, \*Observer Shape\*\*, and *Observation Extents*.</span></span>

<span data-ttu-id="5657f-131">**Forme observateur**</span><span class="sxs-lookup"><span data-stu-id="5657f-131">**Observer Shape**</span></span>

<span data-ttu-id="5657f-132">La forme observateur définit le type de volume que l’observateur de maille utilisera lors de l’observation de maillages.</span><span class="sxs-lookup"><span data-stu-id="5657f-132">The observer shape defines the type of volume that the mesh observer will use when observing meshes.</span></span> <span data-ttu-id="5657f-133">Les options prises en charge sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="5657f-133">The supported options are:</span></span>

* <span data-ttu-id="5657f-134">*Cube aligné* sur l’axe-forme rectangulaire qui reste alignée sur les axes du système de coordonnées universelles, tel que déterminé au démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="5657f-134">*Axis Aligned Cube* - Rectangular shape that stays aligned with the axes of the world coordinate system, as determined at application startup.</span></span>
* <span data-ttu-id="5657f-135">*Cube aligné* par l’utilisateur-forme rectangulaire qui pivote pour s’aligner avec le système de coordonnées local des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="5657f-135">*User Aligned Cube* - Rectangular shape that rotates to align with the users local coordinate system.</span></span>
* <span data-ttu-id="5657f-136">*Sphere* : un volume sphérique avec un centre à l’origine de l’espace universel.</span><span class="sxs-lookup"><span data-stu-id="5657f-136">*Sphere* - A spherical volume with a center at the world space origin.</span></span> <span data-ttu-id="5657f-137">La valeur X de la propriété d' *étendues d’observation* sera utilisée comme rayon de la sphère.</span><span class="sxs-lookup"><span data-stu-id="5657f-137">The X value of the *Observation Extents* property will be used as the radius of the sphere.</span></span>

<span data-ttu-id="5657f-138">**Étendues d’observation**</span><span class="sxs-lookup"><span data-stu-id="5657f-138">**Observation Extents**</span></span>

<span data-ttu-id="5657f-139">Les extensions d’observation définissent la distance à partir du point d’observation que les mailles seront observées.</span><span class="sxs-lookup"><span data-stu-id="5657f-139">The observation extents define the distance from the observation point that meshes will be observed.</span></span>

### <a name="physics-settings"></a><span data-ttu-id="5657f-140">Paramètres physiques</span><span class="sxs-lookup"><span data-stu-id="5657f-140">Physics settings</span></span>

![Paramètres physiques de l’observateur de maillage](../images/spatial-awareness/MeshObserverPhysicsSettings.png)

<span data-ttu-id="5657f-142">**Couche physique**</span><span class="sxs-lookup"><span data-stu-id="5657f-142">**Physics Layer**</span></span>

<span data-ttu-id="5657f-143">Couche physique sur laquelle les objets de maillage spatial seront placés pour interagir avec les systèmes physique et RayCast Unity.</span><span class="sxs-lookup"><span data-stu-id="5657f-143">The physics layer on which spatial mesh objects will be placed in order to interact with the Unity Physics and RayCast systems.</span></span>

> [!NOTE]
> <span data-ttu-id="5657f-144">La boîte à outils de réalité mixte réserve la *couche 31* par défaut pour une utilisation par les observateurs de sensibilisation spatiale.</span><span class="sxs-lookup"><span data-stu-id="5657f-144">The Mixed Reality Toolkit reserves *layer 31* by default for use by Spatial Awareness observers.</span></span>

<span data-ttu-id="5657f-145">**Recalculer les normales**</span><span class="sxs-lookup"><span data-stu-id="5657f-145">**Recalculate Normals**</span></span>

<span data-ttu-id="5657f-146">Spécifie si l’observateur de maillage recalcule les normales de la maille qui suit l’observation.</span><span class="sxs-lookup"><span data-stu-id="5657f-146">Specifies whether or not the mesh observer will recalculate the normals of the mesh following observation.</span></span> <span data-ttu-id="5657f-147">Ce paramètre est disponible pour garantir que les applications reçoivent des maillages qui contiennent des données normales valides sur les plateformes qui ne les retournent pas avec des mailles.</span><span class="sxs-lookup"><span data-stu-id="5657f-147">This setting is available to ensure applications receive meshes that contain valid normals data on platforms that do not return them with meshes.</span></span>

### <a name="level-of-detail-settings"></a><span data-ttu-id="5657f-148">Niveau de paramètres de détail</span><span class="sxs-lookup"><span data-stu-id="5657f-148">Level of detail settings</span></span>

![Niveau d’observateur de maillage des paramètres de détail](../images/spatial-awareness/MeshObserverLevelOfDetailSettings.png)

<span data-ttu-id="5657f-150">**Niveau de détail**</span><span class="sxs-lookup"><span data-stu-id="5657f-150">**Level of Detail**</span></span>

<span data-ttu-id="5657f-151">Spécifie le niveau de détail (LOD) des données de maillage spatiale.</span><span class="sxs-lookup"><span data-stu-id="5657f-151">Specifies the level of detail (LOD) of the spatial mesh data.</span></span> <span data-ttu-id="5657f-152">Les valeurs actuellement définies sont grossistes, fine et Custom.</span><span class="sxs-lookup"><span data-stu-id="5657f-152">Currently defined values are Coarse, Fine and Custom.</span></span>

* <span data-ttu-id="5657f-153">*Grossière* -place un impact plus faible sur les performances de l’application et constitue un excellent choix pour la recherche de plans/de navigation.</span><span class="sxs-lookup"><span data-stu-id="5657f-153">*Coarse* - Places a smaller impact on application performance and is an excellent choice for navigation/plane finding.</span></span>

* <span data-ttu-id="5657f-154">Les paramètres à *moyennement* équilibrés sont souvent utiles pour les expériences qui analysent continuellement l’environnement à la fois pour les grandes fonctionnalités, les étages et les murs, ainsi que pour les détails d’occlusion.</span><span class="sxs-lookup"><span data-stu-id="5657f-154">*Medium* - Balanced setting often useful for experiences that continually scan the environment for both large features, floors and walls, as well as occlusion details.</span></span>

* <span data-ttu-id="5657f-155">*En règle* générale, l’impact sur les performances de l’application est plus important et constitue une option intéressante pour les mailles d’occlusion.</span><span class="sxs-lookup"><span data-stu-id="5657f-155">*Fine* - Generally exacts a higher impact on application performance and is a great option for occlusion meshes.</span></span>

* <span data-ttu-id="5657f-156">*Personnalisé* : nécessite que l’application spécifie la propriété de *compteur triangle/cubique* et permet aux applications de régler la précision par rapport à l’impact sur les performances de l’observateur de maillage spatial.</span><span class="sxs-lookup"><span data-stu-id="5657f-156">*Custom* - Requires the application to specify the *Triangles / Cubic Meter* property and allows applications to tune the accuracy vs. performance impact of the spatial mesh observer.</span></span>

> [!NOTE]
> <span data-ttu-id="5657f-157">Il n’est pas garanti que tous les *triangles/valeurs des compteurs cubes* soient honorés par toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="5657f-157">It is not guaranteed that all *Triangles/Cubic Meter* values are honored by all platforms.</span></span> <span data-ttu-id="5657f-158">L’expérimentation et le profilage sont fortement recommandés lors de l’utilisation d’un LOD personnalisé.</span><span class="sxs-lookup"><span data-stu-id="5657f-158">Experimentation and profiling is highly recommended when using a custom LOD.</span></span>

<span data-ttu-id="5657f-159">**Triangles par mètre cube**</span><span class="sxs-lookup"><span data-stu-id="5657f-159">**Triangles per Cubic Meter**</span></span>

<span data-ttu-id="5657f-160">Valide lors de l’utilisation du paramètre *personnalisé* pour la propriété **niveau de détail** et spécifie la densité du triangle pour le maillage spatial.</span><span class="sxs-lookup"><span data-stu-id="5657f-160">Valid when using the *Custom* setting for the **Level of Detail** property and specifies the triangle density for the spatial mesh.</span></span>

### <a name="display-settings"></a><span data-ttu-id="5657f-161">Paramètres d'affichage</span><span class="sxs-lookup"><span data-stu-id="5657f-161">Display settings</span></span>

![Paramètres d’affichage de l’observateur de maillage](../images/spatial-awareness/MeshObserverDisplaySettings.png)

<span data-ttu-id="5657f-163">**Option d’affichage**</span><span class="sxs-lookup"><span data-stu-id="5657f-163">**Display Option**</span></span>

<span data-ttu-id="5657f-164">Spécifie le mode d’affichage des maillages spatiaux par l’observateur.</span><span class="sxs-lookup"><span data-stu-id="5657f-164">Specifies how spatial meshes are to be displayed by the observer.</span></span> <span data-ttu-id="5657f-165">Les valeurs prises en charge sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="5657f-165">Supported values are:</span></span>

* <span data-ttu-id="5657f-166">*None* -l’observateur ne rend pas le maillage</span><span class="sxs-lookup"><span data-stu-id="5657f-166">*None* - Observer will not render the mesh</span></span>
* <span data-ttu-id="5657f-167">*Visible* : les données du maillage sont visibles à l’aide du *matériau visible*</span><span class="sxs-lookup"><span data-stu-id="5657f-167">*Visible* - Mesh data will be visible using the *Visible Material*</span></span>
* <span data-ttu-id="5657f-168">*Occlusion* : les données de maillage seront des éléments de occultait dans la scène à l’aide du *matériau d’occlusion*</span><span class="sxs-lookup"><span data-stu-id="5657f-168">*Occlusion* - Mesh data will be occlude items in scene using the *Occlusion Material*</span></span>

![Sélectionner l’implémentation du système de sensibilisation spatiale](../images/spatial-awareness/MRTK_SpatialAwareness_DisplayOptions.jpg)

<span data-ttu-id="5657f-170">Les observateurs spatiaux peuvent être [repris/suspendus au moment de l’exécution via du code.](usage-guide.md#starting-and-stopping-mesh-observation)</span><span class="sxs-lookup"><span data-stu-id="5657f-170">Spatial Observers can be [resumed/suspended at runtime via code.](usage-guide.md#starting-and-stopping-mesh-observation)</span></span>

> [!WARNING]
> <span data-ttu-id="5657f-171">Si vous affectez la valeur *None* à l' *option Display* , l’exécution de l’observateur n’est **pas** interrompue.</span><span class="sxs-lookup"><span data-stu-id="5657f-171">Setting *Display Option* to *None* does **NOT** stop the observer from running.</span></span> <span data-ttu-id="5657f-172">Si vous souhaitez arrêter tous les observateurs, les applications doivent suspendre tous les observateurs via [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)</span><span class="sxs-lookup"><span data-stu-id="5657f-172">If you wish to stop all observers, applications will need to suspend all observers via [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)</span></span>

<span data-ttu-id="5657f-173">**Matériau visible**</span><span class="sxs-lookup"><span data-stu-id="5657f-173">**Visible Material**</span></span>

<span data-ttu-id="5657f-174">Indique la matière à utiliser lors de la visualisation du maillage spatial.</span><span class="sxs-lookup"><span data-stu-id="5657f-174">Indicates the material to be used when visualizing the spatial mesh.</span></span>

<span data-ttu-id="5657f-175">**Matériau d’occlusion**</span><span class="sxs-lookup"><span data-stu-id="5657f-175">**Occlusion Material**</span></span>

<span data-ttu-id="5657f-176">Indique la matière à utiliser pour faire en sorte que le maillage spatial occultait les hologrammes.</span><span class="sxs-lookup"><span data-stu-id="5657f-176">Indicates the material to be used to cause the spatial mesh to occlude holograms.</span></span>

## <a name="see-also"></a><span data-ttu-id="5657f-177">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5657f-177">See also</span></span>

* [<span data-ttu-id="5657f-178">Système de sensibilisation spatiale</span><span class="sxs-lookup"><span data-stu-id="5657f-178">Spatial Awareness System</span></span>](spatial-awareness-getting-started.md)
* [<span data-ttu-id="5657f-179">Configuration du système de sensibilisation spatiale par le biais du code</span><span class="sxs-lookup"><span data-stu-id="5657f-179">Configuring Spatial Awareness system via Code</span></span>](usage-guide.md)
* [<span data-ttu-id="5657f-180">Documentation de l’API IMixedRealitySpatialAwarenessObserver</span><span class="sxs-lookup"><span data-stu-id="5657f-180">IMixedRealitySpatialAwarenessObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
* [<span data-ttu-id="5657f-181">Documentation de l’API IMixedRealitySpatialAwarenessMeshObserver</span><span class="sxs-lookup"><span data-stu-id="5657f-181">IMixedRealitySpatialAwarenessMeshObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
* [<span data-ttu-id="5657f-182">Documentation de l’API BaseSpatialObserver</span><span class="sxs-lookup"><span data-stu-id="5657f-182">BaseSpatialObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
