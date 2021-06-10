---
title: BoundsControl
description: Vue d’ensemble du contrôle de limites dans MRTK
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, contrôle des limites,
ms.openlocfilehash: 65558861955f782cf9d81a8bb4ec3a31dee03fde
ms.sourcegitcommit: 95ea5f3cf873acc93c4614fbccaa093e0f5186f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/26/2021
ms.locfileid: "110487726"
---
# <a name="bounds-control"></a><span data-ttu-id="4c697-104">Contrôle de limites</span><span class="sxs-lookup"><span data-stu-id="4c697-104">Bounds control</span></span>

![Contrôle de limites](../images/bounds-control/MRTK_BoundsControl_Main.png)

<span data-ttu-id="4c697-106">*BoundsControl* est le nouveau composant pour la manipulation du comportement, précédemment trouvé dans *BoundingBox*.</span><span class="sxs-lookup"><span data-stu-id="4c697-106">*BoundsControl* is the new component for manipulation behaviour, previously found in *BoundingBox*.</span></span> <span data-ttu-id="4c697-107">Le contrôle des limites effectue un certain nombre d’améliorations et de simplifications dans le programme d’installation et ajoute de nouvelles fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="4c697-107">Bounds control makes a number of improvements and simplifications in setup and adds new features.</span></span> <span data-ttu-id="4c697-108">Ce composant remplace le cadre englobant, qui est déconseillé.</span><span class="sxs-lookup"><span data-stu-id="4c697-108">This component is a replacement for the bounding box, which will be deprecated.</span></span>

<span data-ttu-id="4c697-109">Le [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script fournit des fonctionnalités de base pour transformer des objets en réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="4c697-109">The [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script provides basic functionality for transforming objects in mixed reality.</span></span> <span data-ttu-id="4c697-110">Un contrôle de limites affiche une zone autour de l’hologramme pour indiquer qu’il est possible d’interagir avec.</span><span class="sxs-lookup"><span data-stu-id="4c697-110">A bounds control will show a box around the hologram to indicate that it can be interacted with.</span></span> <span data-ttu-id="4c697-111">Les poignées sur les angles et les bords de la zone permettent la mise à l’échelle, la rotation ou la traduction de l’objet.</span><span class="sxs-lookup"><span data-stu-id="4c697-111">Handles on the corners and edges of the box allow scaling, rotating or translating the object.</span></span> <span data-ttu-id="4c697-112">Le contrôle de limites réagit également aux entrées d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4c697-112">The bounds control also reacts to user input.</span></span> <span data-ttu-id="4c697-113">Sur HoloLens 2, par exemple, le contrôle de limites répond à la proximité d’un doigt, en fournissant un retour visuel pour aider à percevoir la distance par rapport à l’objet.</span><span class="sxs-lookup"><span data-stu-id="4c697-113">On HoloLens 2, for example, the bounds control responds to finger proximity, providing visual feedback to help perceive the distance from the object.</span></span> <span data-ttu-id="4c697-114">Toutes les interactions et tous les visuels peuvent être facilement personnalisés.</span><span class="sxs-lookup"><span data-stu-id="4c697-114">All interactions and visuals can be easily customized.</span></span>

## <a name="example-scene"></a><span data-ttu-id="4c697-115">Exemple de scène</span><span class="sxs-lookup"><span data-stu-id="4c697-115">Example scene</span></span>

<span data-ttu-id="4c697-116">Vous trouverez des exemples de configurations de contrôle de limites dans la `BoundsControlExamples` scène.</span><span class="sxs-lookup"><span data-stu-id="4c697-116">You can find examples of bounds control configurations in the `BoundsControlExamples` scene.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Examples.png" alt="Bounds control Example">

## <a name="inspector-properties"></a><span data-ttu-id="4c697-117">Propriétés de l’inspecteur</span><span class="sxs-lookup"><span data-stu-id="4c697-117">Inspector properties</span></span>

### <a name="target-object"></a><span data-ttu-id="4c697-118">Objet cible</span><span class="sxs-lookup"><span data-stu-id="4c697-118">Target object</span></span>

<span data-ttu-id="4c697-119">Cette propriété spécifie quel objet sera transformé par la manipulation de contrôle de limites.</span><span class="sxs-lookup"><span data-stu-id="4c697-119">This property specifies which object will get transformed by the bounds control manipulation.</span></span> <span data-ttu-id="4c697-120">Si aucun objet n’est défini, la valeur par défaut est l’objet propriétaire.</span><span class="sxs-lookup"><span data-stu-id="4c697-120">If no object is set, it defaults to the owner object.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="4c697-121">Comportement d’activation</span><span class="sxs-lookup"><span data-stu-id="4c697-121">Activation behavior</span></span>

<span data-ttu-id="4c697-122">Il existe plusieurs options pour activer l’interface de contrôle des limites.</span><span class="sxs-lookup"><span data-stu-id="4c697-122">There are several options to activate the bounds control interface.</span></span>

* <span data-ttu-id="4c697-123">*Activer sur Start*: le contrôle des limites devient visible une fois la scène démarrée.</span><span class="sxs-lookup"><span data-stu-id="4c697-123">*Activate On Start*: Bounds control becomes visible once the scene is started.</span></span>
* <span data-ttu-id="4c697-124">*Activer par proximité*: le contrôle des limites devient visible quand une main articulée est proche de l’objet.</span><span class="sxs-lookup"><span data-stu-id="4c697-124">*Activate By Proximity*: Bounds control becomes visible when an articulated hand is close to the object.</span></span>
* <span data-ttu-id="4c697-125">*Activer par pointeur*: le contrôle de limites devient visible lorsqu’il est ciblé par un pointeur de rayon.</span><span class="sxs-lookup"><span data-stu-id="4c697-125">*Activate By Pointer*: Bounds control becomes visible when it is targeted by a hand-ray pointer.</span></span>
* <span data-ttu-id="4c697-126">*Activer par proximité et pointeur*: le contrôle des limites devient visible lorsqu’il est ciblé par un pointeur de rayon de la main ou une main articulée est proche de l’objet.</span><span class="sxs-lookup"><span data-stu-id="4c697-126">*Activate By Proximity and Pointer*: Bounds control becomes visible when it is targeted by a hand-ray pointer or an articulated hand is close to the object.</span></span>
* <span data-ttu-id="4c697-127">*Activer manuellement*: le contrôle de limites ne devient pas visible automatiquement.</span><span class="sxs-lookup"><span data-stu-id="4c697-127">*Activate Manually*: Bounds control does not become visible automatically.</span></span> <span data-ttu-id="4c697-128">Vous pouvez l’activer manuellement par le biais d’un script en accédant à la propriété boundsControl. active.</span><span class="sxs-lookup"><span data-stu-id="4c697-128">You can manually activate it through a script by accessing the boundsControl.Active property.</span></span>

### <a name="bounds-override"></a><span data-ttu-id="4c697-129">Substitutions de limites</span><span class="sxs-lookup"><span data-stu-id="4c697-129">Bounds override</span></span>

<span data-ttu-id="4c697-130">Définit un conflit de cases à partir de l’objet pour le calcul de limites.</span><span class="sxs-lookup"><span data-stu-id="4c697-130">Sets a box collider from the object for bounds computation.</span></span>

### <a name="box-padding"></a><span data-ttu-id="4c697-131">Remplissage de zone</span><span class="sxs-lookup"><span data-stu-id="4c697-131">Box padding</span></span>

<span data-ttu-id="4c697-132">Ajoute une marge intérieure aux limites du conflit utilisées pour calculer les étendues du contrôle.</span><span class="sxs-lookup"><span data-stu-id="4c697-132">Adds a padding to the collider bounds used to calculate the extents of the control.</span></span> <span data-ttu-id="4c697-133">Cela influence non seulement l’interaction, mais également l’impact sur les visuels.</span><span class="sxs-lookup"><span data-stu-id="4c697-133">This will influence not only interaction but also impact the visuals.</span></span>

### <a name="flatten-axis"></a><span data-ttu-id="4c697-134">Aplatir l’axe</span><span class="sxs-lookup"><span data-stu-id="4c697-134">Flatten axis</span></span>

<span data-ttu-id="4c697-135">Indique si le contrôle est aplati dans l’un des axes, en le rendant en deux dimensions et en interautorisant la manipulation le long de cet axe.</span><span class="sxs-lookup"><span data-stu-id="4c697-135">Indicates whether the control is flattened in one of the axes, making it 2 dimensional and disallowing manipulation along that axis.</span></span> <span data-ttu-id="4c697-136">Cette fonctionnalité peut être utilisée pour les objets fins comme les ardoises.</span><span class="sxs-lookup"><span data-stu-id="4c697-136">This feature can be used for thin objects like slates.</span></span>
<span data-ttu-id="4c697-137">Si l’option aplatir l’axe est définie sur *aplatir* automatiquement, le script sélectionne automatiquement l’axe avec l’étendue la plus petite comme axe aplati.</span><span class="sxs-lookup"><span data-stu-id="4c697-137">If flatten axis is set to *Flatten Auto* the script will automatically pick the axis with the smallest extent as flatten axis.</span></span>

### <a name="smoothing"></a><span data-ttu-id="4c697-138">Adoucissage</span><span class="sxs-lookup"><span data-stu-id="4c697-138">Smoothing</span></span>

<span data-ttu-id="4c697-139">La section lissage permet de configurer le comportement de lissage pour la mise à l’échelle et la rotation du contrôle.</span><span class="sxs-lookup"><span data-stu-id="4c697-139">The smoothing section allows to configure smoothing behavior for scale and rotate of the control.</span></span>

### <a name="visuals"></a><span data-ttu-id="4c697-140">Visuels</span><span class="sxs-lookup"><span data-stu-id="4c697-140">Visuals</span></span>

<span data-ttu-id="4c697-141">L’apparence du contrôle des limites peut être configurée en modifiant l’une des configurations de visuels correspondantes.</span><span class="sxs-lookup"><span data-stu-id="4c697-141">The appearance of bounds control can be configured by modifying one of the corresponding visuals configurations.</span></span>
<span data-ttu-id="4c697-142">Les configurations visuelles sont des objets scriptables liés ou incorporés et sont décrites plus en détail dans la [section relative](#configuration-objects)à l’objet de configuration.</span><span class="sxs-lookup"><span data-stu-id="4c697-142">Visual configurations are either linked or inlined scriptable objects and are described in more detail in the [configuration object section](#configuration-objects).</span></span>

## <a name="configuration-objects"></a><span data-ttu-id="4c697-143">Objets de configuration</span><span class="sxs-lookup"><span data-stu-id="4c697-143">Configuration Objects</span></span>

<span data-ttu-id="4c697-144">Le contrôle est fourni avec un ensemble d’objets de configuration qui peuvent être stockés en tant qu’objets pouvant faire l’objet d’un script et partagés entre différentes instances ou prefabs.</span><span class="sxs-lookup"><span data-stu-id="4c697-144">The control comes with a set of configuration objects that can be stored as scriptable objects and shared between different instances or prefabs.</span></span> <span data-ttu-id="4c697-145">Les configurations peuvent être partagées et liées en tant que fichiers de ressources pouvant faire l’élément d’un script ou imbriqués dans prefabs.</span><span class="sxs-lookup"><span data-stu-id="4c697-145">Configurations can be shared and linked either as individual scriptable asset files or nested scriptable assets inside of prefabs.</span></span> <span data-ttu-id="4c697-146">D’autres configurations peuvent également être définies directement sur l’instance sans liaison à une ressource scriptable externe ou imbriquée.</span><span class="sxs-lookup"><span data-stu-id="4c697-146">Further configurations can also be defined directly on the instance without linking to an external or nested scriptable asset.</span></span>

<span data-ttu-id="4c697-147">L’inspecteur de contrôle des limites indique si une configuration est partagée ou inline dans le cadre de l’instance actuelle en indiquant un message dans l’inspecteur de propriété.</span><span class="sxs-lookup"><span data-stu-id="4c697-147">The bounds control inspector will indicate whether a configuration is shared or inlined as part of the current instance by showing a message in the property inspector.</span></span> <span data-ttu-id="4c697-148">En outre, les instances partagées ne peuvent pas être modifiées directement dans la fenêtre des propriétés du contrôle de limites lui-même, mais au lieu de cela, la ressource à laquelle elle est liée doit être directement modification pour éviter toute modification accidentelle des configurations partagées.</span><span class="sxs-lookup"><span data-stu-id="4c697-148">In addition shared instances won't be editable directly in the bounds control property window itself, but instead the asset it's linking to has to be directly modfied to avoid any accidental changes on shared configurations.</span></span>

<span data-ttu-id="4c697-149">Le contrôle des limites actuelles offre des options d’objets de configuration pour les fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="4c697-149">Currently bounds control offers configuration objects options for the following features:</span></span>

* <span data-ttu-id="4c697-150">Poignées</span><span class="sxs-lookup"><span data-stu-id="4c697-150">Handles</span></span>
  * [<span data-ttu-id="4c697-151">Poignées d’échelle</span><span class="sxs-lookup"><span data-stu-id="4c697-151">Scale handles</span></span>](#scale-handles-configuration)
  * [<span data-ttu-id="4c697-152">Poignées de rotation</span><span class="sxs-lookup"><span data-stu-id="4c697-152">Rotation handles</span></span>](#rotation-handles-configuration)
  * [<span data-ttu-id="4c697-153">Descripteurs de traduction</span><span class="sxs-lookup"><span data-stu-id="4c697-153">Translation handles</span></span>](#translation-handles-configuration)
* [<span data-ttu-id="4c697-154">Liens/filaire</span><span class="sxs-lookup"><span data-stu-id="4c697-154">Links / Wireframe</span></span>](#links-configuration-wireframe)
* [<span data-ttu-id="4c697-155">Affichage de zone</span><span class="sxs-lookup"><span data-stu-id="4c697-155">Box display</span></span>](#box-configuration)
* [<span data-ttu-id="4c697-156">Effet de proximité</span><span class="sxs-lookup"><span data-stu-id="4c697-156">Proximity effect</span></span>](#proximity-effect-configuration)

### <a name="box-configuration"></a><span data-ttu-id="4c697-157">Configuration de Box</span><span class="sxs-lookup"><span data-stu-id="4c697-157">Box configuration</span></span>

<span data-ttu-id="4c697-158">La configuration Box est responsable du rendu d’un rectangle plein avec les limites définies par la taille du conflit et la marge intérieure.</span><span class="sxs-lookup"><span data-stu-id="4c697-158">The box configuration is responsible for rendering a solid box with bounds defined via collider size and box padding.</span></span> <span data-ttu-id="4c697-159">Les propriétés suivantes peuvent être définies :</span><span class="sxs-lookup"><span data-stu-id="4c697-159">The following properties can be set up:</span></span>

* <span data-ttu-id="4c697-160">**Box Material**: définit la matière appliquée à la zone rendue quand aucune interaction n’a lieu.</span><span class="sxs-lookup"><span data-stu-id="4c697-160">**Box material**: defines the material applied to the rendered box when no interaction takes place.</span></span> <span data-ttu-id="4c697-161">Une zone s’affiche uniquement si ce matériau est défini.</span><span class="sxs-lookup"><span data-stu-id="4c697-161">A box will only be rendered if this material is set.</span></span>
* <span data-ttu-id="4c697-162">**Matériau à boîte de Box**: matériau pour la zone lorsque l’utilisateur interagit avec le contrôle en saisissant via une interaction proche ou éloignée.</span><span class="sxs-lookup"><span data-stu-id="4c697-162">**Box grabbed material**: material for the box when the user interacts with the control by grabbing via near or far interaction.</span></span>
* <span data-ttu-id="4c697-163">**Échelle d’affichage de l’axe aplati**: échelle appliquée à la zone affichée si l’un des axes est [aplati](#flatten-axis).</span><span class="sxs-lookup"><span data-stu-id="4c697-163">**Flatten axis display scale**: a scale that is applied to the box display if one of the axes is [flattened](#flatten-axis).</span></span>

### <a name="scale-handles-configuration"></a><span data-ttu-id="4c697-164">Configuration des poignées d’échelle</span><span class="sxs-lookup"><span data-stu-id="4c697-164">Scale handles configuration</span></span>

<span data-ttu-id="4c697-165">Ce tiroir de propriété permet de modifier le comportement et la visualisation des poignées d’échelle du contrôle des limites.</span><span class="sxs-lookup"><span data-stu-id="4c697-165">This property drawer allows to modify behavior and visualization of scale handles of bounds control.</span></span>

* <span data-ttu-id="4c697-166">**Matériau de gestion**: matériau appliqué aux descripteurs.</span><span class="sxs-lookup"><span data-stu-id="4c697-166">**Handle material**: material applied to the handles.</span></span>
* <span data-ttu-id="4c697-167">**Gérer un matériau retiré**: matériau appliqué à la poignée saisie.</span><span class="sxs-lookup"><span data-stu-id="4c697-167">**Handle grabbed material**: material applied to the grabbed handle.</span></span>
* <span data-ttu-id="4c697-168">**Handle Prefab**: Prefab facultatif pour le descripteur de mise à l’échelle.</span><span class="sxs-lookup"><span data-stu-id="4c697-168">**Handle prefab**: optional prefab for the scale handle.</span></span> <span data-ttu-id="4c697-169">Si la valeur n’est pas définie, MRTK utilise un cube comme valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="4c697-169">If non is set MRTK will use a cube as default.</span></span>
* <span data-ttu-id="4c697-170">**Taille du handle**: taille du handle d’échelle.</span><span class="sxs-lookup"><span data-stu-id="4c697-170">**Handle size**: size of the scale handle.</span></span>
* <span data-ttu-id="4c697-171">**Remplissage du conflit**: remplissage à ajouter au conflit de handles.</span><span class="sxs-lookup"><span data-stu-id="4c697-171">**Collider padding**: padding to add to the handle collider.</span></span>
* <span data-ttu-id="4c697-172">**Dessiner** la connexion lors de la manipulation : lorsqu’Active dessine une ligne de connexion du point de début de l’interaction à la position actuelle ou du pointeur.</span><span class="sxs-lookup"><span data-stu-id="4c697-172">**Draw tether when manipulating**: when active will draw a tether line from point of start of interaction to current hand or pointer position.</span></span>
* <span data-ttu-id="4c697-173">**Handles ignore le conflit**: si un conflit est lié ici, les handles ignorent toute collision avec ce conflit.</span><span class="sxs-lookup"><span data-stu-id="4c697-173">**Handles ignore collider**: if a collider gets linked here, handles will ignore any collision with this collider.</span></span>
* <span data-ttu-id="4c697-174">**Handle ardoise Prefab**: Prefab à utiliser pour le handle lorsque le contrôle est aplati.</span><span class="sxs-lookup"><span data-stu-id="4c697-174">**Handle slate prefab**: prefab to use for the handle when the control is flattened.</span></span>
* <span data-ttu-id="4c697-175">**Afficher les poignées d’échelle**: contrôle la visibilité du handle.</span><span class="sxs-lookup"><span data-stu-id="4c697-175">**Show scale handles**: controls visibility of the handle.</span></span>
* <span data-ttu-id="4c697-176">**Comportement** de mise à l’échelle : peut être défini avec une mise à l’échelle uniforme ou non uniforme.</span><span class="sxs-lookup"><span data-stu-id="4c697-176">**Scale behavior**: can be set to uniform or non-uniform scaling.</span></span>

### <a name="rotation-handles-configuration"></a><span data-ttu-id="4c697-177">Configuration des poignées de rotation</span><span class="sxs-lookup"><span data-stu-id="4c697-177">Rotation handles configuration</span></span>

<span data-ttu-id="4c697-178">Cette configuration définit le comportement de la poignée de rotation.</span><span class="sxs-lookup"><span data-stu-id="4c697-178">This configuration defines the rotation handle behavior.</span></span>

* <span data-ttu-id="4c697-179">**Matériau de gestion**: matériau appliqué aux descripteurs.</span><span class="sxs-lookup"><span data-stu-id="4c697-179">**Handle material**: material applied to the handles.</span></span>
* <span data-ttu-id="4c697-180">**Gérer un matériau retiré**: matériau appliqué à la poignée saisie.</span><span class="sxs-lookup"><span data-stu-id="4c697-180">**Handle grabbed material**: material applied to the grabbed handle.</span></span>
* <span data-ttu-id="4c697-181">**Handle Prefab**: Prefab facultatif pour le descripteur.</span><span class="sxs-lookup"><span data-stu-id="4c697-181">**Handle prefab**: optional prefab for the handle.</span></span> <span data-ttu-id="4c697-182">Si la valeur n’est pas définie, MRTK utilise une sphère comme valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="4c697-182">If non is set MRTK will use a sphere as default.</span></span>
* <span data-ttu-id="4c697-183">**Taille du handle**: taille du handle.</span><span class="sxs-lookup"><span data-stu-id="4c697-183">**Handle size**: size of the handle.</span></span>
* <span data-ttu-id="4c697-184">**Remplissage du conflit**: remplissage à ajouter au conflit de handles.</span><span class="sxs-lookup"><span data-stu-id="4c697-184">**Collider padding**: padding to add to the handle collider.</span></span>
* <span data-ttu-id="4c697-185">**Dessiner** la connexion lors de la manipulation : lorsqu’Active dessine une ligne de connexion du point de début de l’interaction à la position actuelle ou du pointeur.</span><span class="sxs-lookup"><span data-stu-id="4c697-185">**Draw tether when manipulating**: when active will draw a tether line from point of start of interaction to current hand or pointer position.</span></span>
* <span data-ttu-id="4c697-186">**Handles ignore le conflit**: si un conflit est lié ici, les handles ignorent toute collision avec ce conflit.</span><span class="sxs-lookup"><span data-stu-id="4c697-186">**Handles ignore collider**: if a collider gets linked here, handles will ignore any collision with this collider.</span></span>
* <span data-ttu-id="4c697-187">**Handle Prefab type de conflit**: type de conflit à utiliser avec le handle créé.</span><span class="sxs-lookup"><span data-stu-id="4c697-187">**Handle prefab collider type**: collider type to be used with the created handle.</span></span>
* <span data-ttu-id="4c697-188">**Afficher le handle pour x**: contrôle la visibilité du handle pour l’axe x.</span><span class="sxs-lookup"><span data-stu-id="4c697-188">**Show handle for X**: controls visibility of the handle for X axis.</span></span>
* <span data-ttu-id="4c697-189">**Afficher le handle pour y**: contrôle la visibilité du handle pour l’axe y.</span><span class="sxs-lookup"><span data-stu-id="4c697-189">**Show handle for Y**: controls visibility of the handle for Y axis.</span></span>
* <span data-ttu-id="4c697-190">**Afficher le handle pour z**: contrôle la visibilité du handle pour l’axe z.</span><span class="sxs-lookup"><span data-stu-id="4c697-190">**Show handle for Z**: controls visibility of the handle for Z axis.</span></span>

### <a name="translation-handles-configuration"></a><span data-ttu-id="4c697-191">Configuration des handles de traduction</span><span class="sxs-lookup"><span data-stu-id="4c697-191">Translation handles configuration</span></span>

<span data-ttu-id="4c697-192">Permet d’activer et de configurer des handles de traduction pour le contrôle des limites.</span><span class="sxs-lookup"><span data-stu-id="4c697-192">Allows enabling and configuring translation handles for bounds control.</span></span> <span data-ttu-id="4c697-193">Notez que les descripteurs de traduction sont désactivés par défaut.</span><span class="sxs-lookup"><span data-stu-id="4c697-193">Note that translation handles are disabled per default.</span></span>

* <span data-ttu-id="4c697-194">**Matériau de gestion**: matériau appliqué aux descripteurs.</span><span class="sxs-lookup"><span data-stu-id="4c697-194">**Handle material**: material applied to the handles.</span></span>
* <span data-ttu-id="4c697-195">**Gérer un matériau retiré**: matériau appliqué à la poignée saisie.</span><span class="sxs-lookup"><span data-stu-id="4c697-195">**Handle grabbed material**: material applied to the grabbed handle.</span></span>
* <span data-ttu-id="4c697-196">**Handle Prefab**: Prefab facultatif pour le descripteur.</span><span class="sxs-lookup"><span data-stu-id="4c697-196">**Handle prefab**: optional prefab for the handle.</span></span> <span data-ttu-id="4c697-197">Si la valeur n’est pas définie, MRTK utilise une sphère comme valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="4c697-197">If non is set MRTK will use a sphere as default.</span></span>
* <span data-ttu-id="4c697-198">**Taille du handle**: taille du handle.</span><span class="sxs-lookup"><span data-stu-id="4c697-198">**Handle size**: size of the handle.</span></span>
* <span data-ttu-id="4c697-199">**Remplissage du conflit**: remplissage à ajouter au conflit de handles.</span><span class="sxs-lookup"><span data-stu-id="4c697-199">**Collider padding**: padding to add to the handle collider.</span></span>
* <span data-ttu-id="4c697-200">**Dessiner** la connexion lors de la manipulation : lorsqu’Active dessine une ligne de connexion du point de début de l’interaction à la position actuelle ou du pointeur.</span><span class="sxs-lookup"><span data-stu-id="4c697-200">**Draw tether when manipulating**: when active will draw a tether line from point of start of interaction to current hand or pointer position.</span></span>
* <span data-ttu-id="4c697-201">**Handles ignore le conflit**: si un conflit est lié ici, les handles ignorent toute collision avec ce conflit.</span><span class="sxs-lookup"><span data-stu-id="4c697-201">**Handles ignore collider**: if a collider gets linked here, handles will ignore any collision with this collider.</span></span>
* <span data-ttu-id="4c697-202">**Handle Prefab type de conflit**: type de conflit à utiliser avec le handle créé.</span><span class="sxs-lookup"><span data-stu-id="4c697-202">**Handle prefab collider type**: collider type to be used with the created handle.</span></span>
* <span data-ttu-id="4c697-203">**Afficher le handle pour x**: contrôle la visibilité du handle pour l’axe x.</span><span class="sxs-lookup"><span data-stu-id="4c697-203">**Show handle for X**: controls visibility of the handle for X axis.</span></span>
* <span data-ttu-id="4c697-204">**Afficher le handle pour y**: contrôle la visibilité du handle pour l’axe y.</span><span class="sxs-lookup"><span data-stu-id="4c697-204">**Show handle for Y**: controls visibility of the handle for Y axis.</span></span>
* <span data-ttu-id="4c697-205">**Afficher le handle pour z**: contrôle la visibilité du handle pour l’axe z.</span><span class="sxs-lookup"><span data-stu-id="4c697-205">**Show handle for Z**: controls visibility of the handle for Z axis.</span></span>

### <a name="links-configuration-wireframe"></a><span data-ttu-id="4c697-206">Configuration des liens (filaire)</span><span class="sxs-lookup"><span data-stu-id="4c697-206">Links configuration (wireframe)</span></span>

<span data-ttu-id="4c697-207">La configuration des liens active la fonctionnalité filaire du contrôle des limites.</span><span class="sxs-lookup"><span data-stu-id="4c697-207">The links configuration enables the wireframe feature of bounds control.</span></span> <span data-ttu-id="4c697-208">Les propriétés suivantes peuvent être configurées :</span><span class="sxs-lookup"><span data-stu-id="4c697-208">The following properties can be configured:</span></span>

* <span data-ttu-id="4c697-209">**Matériau filaire**: matériau appliqué à la maille filaire.</span><span class="sxs-lookup"><span data-stu-id="4c697-209">**Wireframe material**: the material applied to the wireframe mesh.</span></span>
* <span data-ttu-id="4c697-210">**Rayon de périphérie filaire**: épaisseur du filaire.</span><span class="sxs-lookup"><span data-stu-id="4c697-210">**Wireframe edge radius**: the thickness of the wireframe.</span></span>
* <span data-ttu-id="4c697-211">**Forme filaire**: la forme du filaire peut être cubique ou cylindrique.</span><span class="sxs-lookup"><span data-stu-id="4c697-211">**Wireframe shape**: shape of the wireframe can by either cubic or cylindrical.</span></span>
* <span data-ttu-id="4c697-212">**Afficher le filaire**: contrôle la visibilité du filaire.</span><span class="sxs-lookup"><span data-stu-id="4c697-212">**Show wireframe**: controls visibility of the wireframe.</span></span>

### <a name="proximity-effect-configuration"></a><span data-ttu-id="4c697-213">Configuration de l’effet de proximité</span><span class="sxs-lookup"><span data-stu-id="4c697-213">Proximity effect configuration</span></span>

<span data-ttu-id="4c697-214">Affichez et masquez les poignées avec l’animation en fonction de la distance des mains.</span><span class="sxs-lookup"><span data-stu-id="4c697-214">Show and hide the handles with animation based on the distance to the hands.</span></span> <span data-ttu-id="4c697-215">Il a une animation de mise à l’échelle en deux étapes.</span><span class="sxs-lookup"><span data-stu-id="4c697-215">It has two-step scaling animation.</span></span> <span data-ttu-id="4c697-216">Les valeurs par défaut sont définies sur le comportement de style HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="4c697-216">Defaults are set to HoloLens 2 style behavior.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Proximity.png" alt="Bounds control Proximity">

* <span data-ttu-id="4c697-217">**Effet de proximité actif**: activer l’activation du handle basé sur la proximité</span><span class="sxs-lookup"><span data-stu-id="4c697-217">**Proximity Effect Active**: Enable proximity-based handle activation</span></span>
* <span data-ttu-id="4c697-218">**Proximité** de l’objet : distance pour la mise à l’échelle du 1er échelon</span><span class="sxs-lookup"><span data-stu-id="4c697-218">**Object Medium Proximity**: Distance for the 1st step scaling</span></span>
* <span data-ttu-id="4c697-219">**Proximité** de l’objet : distance pour la mise à l’échelle du 2e échelon</span><span class="sxs-lookup"><span data-stu-id="4c697-219">**Object Close Proximity**: Distance for the 2nd step scaling</span></span>
* <span data-ttu-id="4c697-220">Mise à l' **échelle lointaine**: valeur de mise à l’échelle par défaut de la ressource de poignée lorsque les mains sont hors limites de l’interaction de contrôle des limites (distance définie ci-dessus par « gérer la proximité moyenne ».</span><span class="sxs-lookup"><span data-stu-id="4c697-220">**Far Scale**: Default scale value of the handle asset when the hands are out of range of the bounds control interaction (distance defined above by 'Handle Medium Proximity'.</span></span> <span data-ttu-id="4c697-221">Utilisez 0 pour masquer le descripteur par défaut)</span><span class="sxs-lookup"><span data-stu-id="4c697-221">Use 0 to hide handle by default)</span></span>
* <span data-ttu-id="4c697-222">**Échelle moyenne**: valeur de mise à l’échelle de la ressource de poignée lorsque les mains sont dans la plage de l’interaction de contrôle des limites (distance définie ci-dessus par « gérer la proximité ».</span><span class="sxs-lookup"><span data-stu-id="4c697-222">**Medium Scale**: Scale value of the handle asset when the hands are within range of the bounds control interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="4c697-223">Utiliser 1 pour afficher la taille normale</span><span class="sxs-lookup"><span data-stu-id="4c697-223">Use 1 to show normal size)</span></span>
* <span data-ttu-id="4c697-224">**Clôture** de l’échelle : valeur de mise à l’échelle de la ressource de poignée lorsque les mains sont dans la plage de l’interaction de manipulation (distance définie ci-dessus par « poignée de proximité ».</span><span class="sxs-lookup"><span data-stu-id="4c697-224">**Close Scale**: Scale value of the handle asset when the hands are within range of the grab interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="4c697-225">Utiliser 1. x pour afficher une taille supérieure)</span><span class="sxs-lookup"><span data-stu-id="4c697-225">Use 1.x to show bigger size)</span></span>
* <span data-ttu-id="4c697-226">**Taux de croissance lointaine**: évalue l’échelle d’un objet à l’échelle de proximité lorsque la main passe d’une distance moyenne à l’extrême.</span><span class="sxs-lookup"><span data-stu-id="4c697-226">**Far Grow Rate**: Rate a proximity scaled object scales when the hand moves from medium to far proximity.</span></span>
* <span data-ttu-id="4c697-227">**Taux d’augmentation moyenne**: calcul de l’échelle d’un objet mis à l’échelle lorsque la main passe d’une valeur moyenne à une proximité proche.</span><span class="sxs-lookup"><span data-stu-id="4c697-227">**Medium Grow Rate**: Rate a proximity scaled object scales when the hand moves from medium to close proximity.</span></span>
* <span data-ttu-id="4c697-228">**Taux de croissance proche**: taux d’échelle d’un objet à l’échelle de proximité lorsque la main passe de proximité au centre de l’objet.</span><span class="sxs-lookup"><span data-stu-id="4c697-228">**Close Grow Rate**: Rate a proximity scaled object scales when the hand moves from close proximity to object center.</span></span>

## <a name="constraint-system"></a><span data-ttu-id="4c697-229">Système de contrainte</span><span class="sxs-lookup"><span data-stu-id="4c697-229">Constraint System</span></span>

<span data-ttu-id="4c697-230">Le contrôle de limites prend en charge l’utilisation du [Gestionnaire de contraintes](constraint-manager.md) pour limiter ou modifier le comportement de translation, de rotation ou de mise à l’échelle lors de l’utilisation de handles de contrôle de limites.</span><span class="sxs-lookup"><span data-stu-id="4c697-230">Bounds control supports using the [constraint manager](constraint-manager.md) to limit or modify translation, rotation or scaling behavior while using bounds control handles.</span></span>

<span data-ttu-id="4c697-231">L’inspecteur de propriété affiche tous les gestionnaires de contraintes disponibles attachés au même objet de jeu dans une liste déroulante avec une option permettant de faire défiler et de mettre en surbrillance le gestionnaire de contraintes sélectionné.</span><span class="sxs-lookup"><span data-stu-id="4c697-231">The property inspector will show all available constraint managers attached to the same game object in a dropdown with an option to scroll and highlight the selected constraint manager.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Constraints.png" width="450" alt="Bounds control Constraints">

## <a name="events"></a><span data-ttu-id="4c697-232">Événements</span><span class="sxs-lookup"><span data-stu-id="4c697-232">Events</span></span>

<span data-ttu-id="4c697-233">Le contrôle de limites fournit les événements suivants.</span><span class="sxs-lookup"><span data-stu-id="4c697-233">Bounds control provides the following events.</span></span> <span data-ttu-id="4c697-234">Cet exemple utilise ces événements pour lire les commentaires audio.</span><span class="sxs-lookup"><span data-stu-id="4c697-234">This example uses these events to play audio feedback.</span></span>

* <span data-ttu-id="4c697-235">**Rotate Started**: déclenché au début de la rotation.</span><span class="sxs-lookup"><span data-stu-id="4c697-235">**Rotate Started**: Fired when rotation starts.</span></span>
* <span data-ttu-id="4c697-236">**Rotation arrêtée**: déclenché lorsque la rotation s’arrête.</span><span class="sxs-lookup"><span data-stu-id="4c697-236">**Rotate Stopped**: Fired when rotation stops.</span></span>
* <span data-ttu-id="4c697-237">Mise à l' **échelle démarrée**: se déclenche lors du démarrage de la mise à l’échelle.</span><span class="sxs-lookup"><span data-stu-id="4c697-237">**Scale Started**: Fires when scaling starts.</span></span>
* <span data-ttu-id="4c697-238">**Arrêt** de l’échelle : se déclenche lorsque la mise à l’échelle s’arrête.</span><span class="sxs-lookup"><span data-stu-id="4c697-238">**Scale Stopped**: Fires when scaling stops.</span></span>
* <span data-ttu-id="4c697-239">**Conversion démarrée**: se déclenche au démarrage de la traduction.</span><span class="sxs-lookup"><span data-stu-id="4c697-239">**Translate Started**: Fires when translation starts.</span></span>
* <span data-ttu-id="4c697-240">**Translate Stopped**: se déclenche lorsque la traduction s’arrête.</span><span class="sxs-lookup"><span data-stu-id="4c697-240">**Translate Stopped**: Fires when translation stops.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Events.png" width="450" alt="Bounds control Events">

## <a name="elastics-experimental"></a><span data-ttu-id="4c697-241">Élastiques (expérimental)</span><span class="sxs-lookup"><span data-stu-id="4c697-241">Elastics (Experimental)</span></span>

<span data-ttu-id="4c697-242">Les élastiques peuvent être utilisés lors de la manipulation d’objets via le contrôle des limites.</span><span class="sxs-lookup"><span data-stu-id="4c697-242">Elastics can be used when manipulating objects via bounds control.</span></span> <span data-ttu-id="4c697-243">Notez que le [système élastiques](../elastics/elastic-system.md) est toujours dans un État expérimental.</span><span class="sxs-lookup"><span data-stu-id="4c697-243">Note that the [elastics system](../elastics/elastic-system.md) is still in experimental state.</span></span> <span data-ttu-id="4c697-244">Pour activer les élastiques, liez un composant Gestionnaire élastique existant ou créez et liez un nouveau gestionnaire élastiques à l’aide du `Add Elastics Manager` bouton.</span><span class="sxs-lookup"><span data-stu-id="4c697-244">To enable elastics either link an existing elastics manager component or create and link a new elastics manager via the `Add Elastics Manager` button.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds control Elastics">

## <a name="handle-styles"></a><span data-ttu-id="4c697-245">Gérer les styles</span><span class="sxs-lookup"><span data-stu-id="4c697-245">Handle styles</span></span>

<span data-ttu-id="4c697-246">Par défaut, lorsque vous affectez simplement le [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script, il affiche le descripteur du style HoloLens 1re génération.</span><span class="sxs-lookup"><span data-stu-id="4c697-246">By default, when you just assign the [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script, it will show the handle of the HoloLens 1st gen style.</span></span> <span data-ttu-id="4c697-247">Pour utiliser les descripteurs de style HoloLens 2, vous devez affecter les prefabs et les matériaux de handle appropriés.</span><span class="sxs-lookup"><span data-stu-id="4c697-247">To use HoloLens 2 style handles, you need to assign proper handle prefabs and materials.</span></span>

![Styles de handle de contrôle des limites 2](../images/bounds-control/MRTK_BoundsControl_HandleStyles1.png)

<span data-ttu-id="4c697-249">Vous trouverez ci-dessous les prefabs, les matériaux et les valeurs de mise à l’échelle pour les poignées de contrôle des limites de style HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="4c697-249">Below are the prefabs, materials, and the scaling values for the HoloLens 2 style bounds control handles.</span></span> <span data-ttu-id="4c697-250">Cet exemple se trouve dans la `BoundsControlExamples` scène.</span><span class="sxs-lookup"><span data-stu-id="4c697-250">You can find this example in the `BoundsControlExamples` scene.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_HandleStyles2.png" width="450" alt="Bounds control HandleStyles">

### <a name="handles-setup-for-hololens-2-style"></a><span data-ttu-id="4c697-251">Handles (programme d’installation du style HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="4c697-251">Handles (Setup for HoloLens 2 style)</span></span>

* <span data-ttu-id="4c697-252">**Matériau de gestion**: BoundingBoxHandleWhite. mat</span><span class="sxs-lookup"><span data-stu-id="4c697-252">**Handle Material**: BoundingBoxHandleWhite.mat</span></span>
* <span data-ttu-id="4c697-253">**Gérer un matériau retiré**: BoundingBoxHandleBlueGrabbed. mat</span><span class="sxs-lookup"><span data-stu-id="4c697-253">**Handle Grabbed Material**: BoundingBoxHandleBlueGrabbed.mat</span></span>
* <span data-ttu-id="4c697-254">Descripteur de mise à l' **échelle Prefab**: MRTK_BoundingBox_ScaleHandle. Prefab</span><span class="sxs-lookup"><span data-stu-id="4c697-254">**Scale Handle Prefab**: MRTK_BoundingBox_ScaleHandle.prefab</span></span>
* <span data-ttu-id="4c697-255">**Poignée d’échelle ardoise Prefab**: MRTK_BoundingBox_ScaleHandle_Slate. Prefab</span><span class="sxs-lookup"><span data-stu-id="4c697-255">**Scale Handle Slate Prefab**: MRTK_BoundingBox_ScaleHandle_Slate.prefab</span></span>
* <span data-ttu-id="4c697-256">**Taille du handle** de l’échelle : 0,016 (1,6 cm)</span><span class="sxs-lookup"><span data-stu-id="4c697-256">**Scale Handle Size**: 0.016 (1.6cm)</span></span>
* <span data-ttu-id="4c697-257">Mise à l' **échelle du remplissage du conflit**: 0,016 (rend le conflit de manipulation légèrement plus grand que le visuel de la poignée)</span><span class="sxs-lookup"><span data-stu-id="4c697-257">**Scale Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>
* <span data-ttu-id="4c697-258">**Handle de rotation Prefab**: MRTK_BoundingBox_RotateHandle. Prefab</span><span class="sxs-lookup"><span data-stu-id="4c697-258">**Rotation Handle Prefab**: MRTK_BoundingBox_RotateHandle.prefab</span></span>
* <span data-ttu-id="4c697-259">**Taille du handle de rotation**: 0,016</span><span class="sxs-lookup"><span data-stu-id="4c697-259">**Rotation Handle Size**: 0.016</span></span>
* <span data-ttu-id="4c697-260">La **poignée de rotation marge intérieure du conflit**: 0,016 (rend le conflit de manipulation légèrement plus grand que le visuel de la poignée)</span><span class="sxs-lookup"><span data-stu-id="4c697-260">**Rotation Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>

## <a name="transformation-changes-with-object-manipulator"></a><span data-ttu-id="4c697-261">Modifications de transformation avec manipulateur d’objets</span><span class="sxs-lookup"><span data-stu-id="4c697-261">Transformation changes with object manipulator</span></span>

<span data-ttu-id="4c697-262">Un contrôle de limites peut être utilisé conjointement avec [`ObjectManipulator.cs`](object-manipulator.md) pour autoriser certains types de manipulations (par exemple,</span><span class="sxs-lookup"><span data-stu-id="4c697-262">A bounds control can be used in combination with [`ObjectManipulator.cs`](object-manipulator.md) to allow for certain types of manipulation (eg.</span></span> <span data-ttu-id="4c697-263">déplacement de l’objet) sans utiliser de handles.</span><span class="sxs-lookup"><span data-stu-id="4c697-263">moving the object) without using handles.</span></span> <span data-ttu-id="4c697-264">Le gestionnaire de manipulation prend en charge les interactions une et deux.</span><span class="sxs-lookup"><span data-stu-id="4c697-264">The manipulation handler supports both one and two-handed interactions.</span></span> <span data-ttu-id="4c697-265">Le suivi de la [main](../input/hand-tracking.md) peut être utilisé pour interagir avec un objet plus proche.</span><span class="sxs-lookup"><span data-stu-id="4c697-265">[Hand tracking](../input/hand-tracking.md) can be used to interact with an object up close.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_ObjectManipulator.png" width="450" alt="Bounds control Object Manipulator">

<span data-ttu-id="4c697-266">Pour que les bords du contrôle des limites se comportent de la même façon lors de leur déplacement à l’aide [`ObjectManipulator`](object-manipulator.md) de l’interaction Far, il est recommandé de connecter ses événements pour la *manipulation démarrée*  /  *sur la manipulation terminée* `BoundsControl.HighlightWires`  /  `BoundsControl.UnhighlightWires` respectivement, comme illustré dans la capture d’écran ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="4c697-266">In order for the bounds control edges to behave the same way when moving it using [`ObjectManipulator`](object-manipulator.md)'s far interaction, it is advised to connect its events for *On Manipulation Started* / *On Manipulation Ended* to `BoundsControl.HighlightWires` / `BoundsControl.UnhighlightWires` respectively, as shown in the screenshot above.</span></span>

## <a name="how-to-add-and-configure-a-bounds-control-using-unity-inspector"></a><span data-ttu-id="4c697-267">Comment ajouter et configurer un contrôle de limites à l’aide de l’inspecteur Unity</span><span class="sxs-lookup"><span data-stu-id="4c697-267">How to add and configure a bounds control using Unity Inspector</span></span>

1. <span data-ttu-id="4c697-268">Ajouter un conflit de zone à un objet</span><span class="sxs-lookup"><span data-stu-id="4c697-268">Add Box Collider to an object</span></span>
2. <span data-ttu-id="4c697-269">Affecter `BoundsControl` un script à un objet</span><span class="sxs-lookup"><span data-stu-id="4c697-269">Assign `BoundsControl` script to an object</span></span>
3. <span data-ttu-id="4c697-270">Configurer des options, telles que les méthodes « activation » (voir la section Propriétés de l' [inspecteur](#inspector-properties) ci-dessous)</span><span class="sxs-lookup"><span data-stu-id="4c697-270">Configure options, such as 'Activation' methods (see [Inspector properties](#inspector-properties) section below)</span></span>
4. <span data-ttu-id="4c697-271">Facultatif Assigner des prefabs et des matériaux pour un contrôle de limites de style HoloLens 2 (consultez la section relative aux [styles de handle](#handle-styles) ci-dessous)</span><span class="sxs-lookup"><span data-stu-id="4c697-271">(Optional) Assign prefabs and materials for a HoloLens 2 style bounds control (see [Handle styles](#handle-styles) section below)</span></span>

> [!NOTE]
> <span data-ttu-id="4c697-272">Utilisez l' *objet cible* et le champ de *remplacement de limites* dans l’inspecteur pour assigner un objet et un conflit spécifiques dans l’objet avec plusieurs composants enfants.</span><span class="sxs-lookup"><span data-stu-id="4c697-272">Use *Target Object* and *Bounds Override* field in the inspector to assign specific object and collider in the object with multiple child components.</span></span>

![Contrôle des limites](../images/bounds-control/MRTK_BoundsControl_Assign.png)

## <a name="how-to-add-and-configure-a-bounds-control-in-the-code"></a><span data-ttu-id="4c697-274">Comment ajouter et configurer un contrôle de limites dans le code</span><span class="sxs-lookup"><span data-stu-id="4c697-274">How to add and configure a bounds control in the code</span></span>

1. <span data-ttu-id="4c697-275">Instancier le cube GameObject</span><span class="sxs-lookup"><span data-stu-id="4c697-275">Instantiate cube GameObject</span></span>

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. <span data-ttu-id="4c697-276">Assigner `BoundsControl` un script à un objet avec un conflit à l’aide de AddComponent<> ()</span><span class="sxs-lookup"><span data-stu-id="4c697-276">Assign `BoundsControl` script to an object with collider, using AddComponent<>()</span></span>

    ```c#
    private BoundsControl boundsControl;
    boundsControl = cube.AddComponent<BoundsControl>();
    ```

1. <span data-ttu-id="4c697-277">Configurez les options soit directement sur le contrôle, soit par le biais de l’une des configurations scriptables (voir la section Propriétés et [configurations](#configuration-objects) de l' [inspecteur](#inspector-properties) ci-dessous).</span><span class="sxs-lookup"><span data-stu-id="4c697-277">Configure options either directly on the control or via one of the scriptable configurations (see [Inspector properties](#inspector-properties) and [Configurations](#configuration-objects) section below)</span></span>

    ```c#
    // Change activation method
    boundsControl.BoundsControlActivation = BoundsControlActivationType.ActivateByProximityAndPointer;
    // Make the scale handles large
    boundsControl.ScaleHandlesConfig.HandleSize = 0.1f;
    // Hide rotation handles for x axis
    boundsControl.RotationHandlesConfig.ShowRotationHandleForX = false;
    ```

1. <span data-ttu-id="4c697-278">Facultatif Assignez des prefabs et des matériaux pour un contrôle de limites de style HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="4c697-278">(Optional) Assign prefabs and materials for a HoloLens 2 style bounds control.</span></span> <span data-ttu-id="4c697-279">Cela nécessite toujours des affectations via l’inspecteur, car les matériaux et les prefabs doivent être chargés dynamiquement.</span><span class="sxs-lookup"><span data-stu-id="4c697-279">This still requires assignments through the inspector since the materials and prefabs should be dynamically loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="4c697-280">Utilisation du dossier « Resources » ou du [nuanceur Unity. Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) pour le chargement dynamique des nuanceurs n’est pas recommandé, car les permutations de nuanceur peuvent être manquantes au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="4c697-280">Using Unity's 'Resources' folder or [Shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) for dynamically loading shaders is not recommended since shader permutations may be missing at runtime.</span></span>

```c#
BoxDisplayConfiguration boxConfiguration = boundsControl.BoxDisplayConfig;
boxConfiguration.BoxMaterial = [Assign BoundingBox.mat]
boxConfiguration.BoxGrabbedMaterial = [Assign BoundingBoxGrabbed.mat]
ScaleHandlesConfiguration scaleHandleConfiguration = boundsControl.ScaleHandlesConfig;
scaleHandleConfiguration.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
scaleHandleConfiguration.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
scaleHandleConfiguration.HandlePrefab = [Assign MRTK_BoundingBox_ScaleHandle.prefab]
scaleHandleConfiguration.HandleSlatePrefab = [Assign MRTK_BoundingBox_ScaleHandle_Slate.prefab]
scaleHandleConfiguration.HandleSize = 0.016f;
scaleHandleConfiguration.ColliderPadding = 0.016f;
RotationHandlesConfiguration rotationHandleConfiguration = boundsControl.RotationHandlesConfig;
rotationHandleConfiguration.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
rotationHandleConfiguration.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
rotationHandleConfiguration.HandlePrefab = [Assign MRTK_BoundingBox_RotateHandle.prefab]
rotationHandleConfiguration.HandleSize = 0.016f;
rotationHandleConfiguration.ColliderPadding = 0.016f;
```

### <a name="example-set-minimum-maximum-bounds-control-scale-using-minmaxscaleconstraint"></a><span data-ttu-id="4c697-281">Exemple : définir l’échelle de contrôle des limites maximales et minimales à l’aide de MinMaxScaleConstraint</span><span class="sxs-lookup"><span data-stu-id="4c697-281">Example: Set minimum, maximum bounds control scale using MinMaxScaleConstraint</span></span>

<span data-ttu-id="4c697-282">Pour définir l’échelle minimale et maximale, attachez un [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) à votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="4c697-282">To set the minimum and maximum scale, attach a [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) to your control.</span></span> <span data-ttu-id="4c697-283">Comme le contrôle de limites As associe et active automatiquement le gestionnaire de contraintes, le MinMaxScaleConstraint est appliqué automatiquement à la transformation change une fois qu’elle est attachée et configurée.</span><span class="sxs-lookup"><span data-stu-id="4c697-283">As bounds control automatically attaches and activates constraint manager the MinMaxScaleConstraint will be automatically applied to the transformation changes once it's attached and configured.</span></span>

<span data-ttu-id="4c697-284">Vous pouvez également utiliser MinMaxScaleConstraint pour définir une échelle minimale et maximale pour [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) .</span><span class="sxs-lookup"><span data-stu-id="4c697-284">You can also use MinMaxScaleConstraint to set minimum and maximum scale for [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator).</span></span>

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bcontrol = cube.AddComponent<BoundsControl>();
// Important: BoundsControl creates a constraint manager on start if one does not exist.
// There's no need to manually attach a constraint manager.
MinMaxScaleConstraint scaleConstraint = bcontrol.gameObject.AddComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounds-control-around-a-game-object"></a><span data-ttu-id="4c697-285">Exemple : ajouter un contrôle de limites autour d’un objet de jeu</span><span class="sxs-lookup"><span data-stu-id="4c697-285">Example: Add bounds control around a game object</span></span>

<span data-ttu-id="4c697-286">Pour ajouter un contrôle de limites autour d’un objet, ajoutez simplement un `BoundsControl` composant à ce dernier :</span><span class="sxs-lookup"><span data-stu-id="4c697-286">To add a bounds control around an object, simply add a `BoundsControl` component to it:</span></span>

```c#
private void PutABoundsControlAroundIt(GameObject target)
{
   target.AddComponent<BoundsControl>();
}
```

## <a name="migrating-from-bounding-box"></a><span data-ttu-id="4c697-287">Migration à partir d’un cadre englobant</span><span class="sxs-lookup"><span data-stu-id="4c697-287">Migrating from Bounding Box</span></span>

<span data-ttu-id="4c697-288">Les prefabs et les instances existantes qui utilisent le [cadre englobant](bounding-box.md) peuvent être mis à niveau vers le nouveau contrôle des limites via la [fenêtre de migration](../tools/migration-window.md) qui fait partie du package d’outils MRTK.</span><span class="sxs-lookup"><span data-stu-id="4c697-288">Existing prefabs and instances using [bounding box](bounding-box.md) can be upgraded to the new bounds control via the [migration window](../tools/migration-window.md) which is part of the MRTK tools package.</span></span>

<span data-ttu-id="4c697-289">Pour mettre à niveau des instances individuelles du cadre englobant, il existe également une option de migration à l’intérieur de l’inspecteur de propriété du composant.</span><span class="sxs-lookup"><span data-stu-id="4c697-289">For upgrading individual instances of bounding box there's also an a migration option inside the property inspector of the component.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds control Migrate">

## <a name="see-also"></a><span data-ttu-id="4c697-290">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c697-290">See also</span></span>

* [<span data-ttu-id="4c697-291">Manipulateur d’objets</span><span class="sxs-lookup"><span data-stu-id="4c697-291">Object manipulator</span></span>](object-manipulator.md)
* [<span data-ttu-id="4c697-292">Gestionnaire de contraintes</span><span class="sxs-lookup"><span data-stu-id="4c697-292">Constraint manager</span></span>](constraint-manager.md)
* [<span data-ttu-id="4c697-293">Fenêtre de migration</span><span class="sxs-lookup"><span data-stu-id="4c697-293">Migration window</span></span>](../tools/migration-window.md)
* [<span data-ttu-id="4c697-294">Système élastique (expérimental)</span><span class="sxs-lookup"><span data-stu-id="4c697-294">Elastics system (Experimental)</span></span>](../elastics/elastic-system.md)
