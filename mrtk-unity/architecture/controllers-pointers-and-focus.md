---
title: Contrôleurs, pointeurs et Focus
description: Interaction avec les contrôleurs, les pointeurs et le focus.
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, pointeurs, contrôleurs
ms.openlocfilehash: b3e4438c1318abbc60606bcbca42854edae28167
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121617"
---
# <a name="controllers-pointers-and-focus"></a><span data-ttu-id="86a92-104">Contrôleurs, pointeurs et Focus</span><span class="sxs-lookup"><span data-stu-id="86a92-104">Controllers, pointers, and focus</span></span>

<span data-ttu-id="86a92-105">Les contrôleurs, les pointeurs et le focus sont des concepts de niveau supérieur qui s’appuient sur la fondation établie par le système d’entrée principal.</span><span class="sxs-lookup"><span data-stu-id="86a92-105">Controllers, pointers, and focus are higher-level concepts that build upon the foundation established by the core input system.</span></span> <span data-ttu-id="86a92-106">Ensemble, ils fournissent une grande partie du mécanisme pour l’interaction avec les objets dans la scène.</span><span class="sxs-lookup"><span data-stu-id="86a92-106">Together, they provide a large portion of the mechanism for interacting with objects in the scene.</span></span>

## <a name="controllers"></a><span data-ttu-id="86a92-107">Controllers</span><span class="sxs-lookup"><span data-stu-id="86a92-107">Controllers</span></span>

<span data-ttu-id="86a92-108">Les contrôleurs sont des représentations d’un contrôleur physique (6 degrés de liberté, articulés, etc.).</span><span class="sxs-lookup"><span data-stu-id="86a92-108">Controllers are representations of a physical controller (6-degrees of freedom, articulated hand, etc).</span></span> <span data-ttu-id="86a92-109">Ils sont créés par les gestionnaires d’appareils et sont responsables de la communication avec le système sous-jacent correspondant et de la traduction de ces données en données et événements en forme de MRTK. a</span><span class="sxs-lookup"><span data-stu-id="86a92-109">They are created by device managers and are responsible for communicating with the corresponding underlying system and translating that data into MRTK-shaped data and events.a</span></span>

<span data-ttu-id="86a92-110">Par exemple, sur la plateforme Windows Mixed Reality, [`WindowsMixedRealityArticulatedHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityArticulatedHand) est un contrôleur responsable de l’interfaçage avec les API de suivi des [Handles](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) Windows sous-jacentes pour obtenir des informations sur les jointures, les poses et d’autres propriétés de la main.</span><span class="sxs-lookup"><span data-stu-id="86a92-110">For example, on the Windows Mixed Reality platform, the [`WindowsMixedRealityArticulatedHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityArticulatedHand) is a controller that is responsible for interfacing with the underlying Windows [hand tracking APIs](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) to get information about the joints, pose, and other properties of the hand.</span></span> <span data-ttu-id="86a92-111">Il est chargé de convertir ces données en événements MRTK pertinents (par exemple, en appelant RaisePoseInputChanged ou RaiseHandJointsUpdated) et en mettant à jour son propre état interne afin que les requêtes pour [`TryGetJointPose`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils.TryGetJointPose%2A) renvoient des données correctes.</span><span class="sxs-lookup"><span data-stu-id="86a92-111">It is responsible for turning this data into relevant MRTK events (for example, by calling RaisePoseInputChanged or RaiseHandJointsUpdated) and by updating its own internal state so that queries for [`TryGetJointPose`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils.TryGetJointPose%2A) will return correct data.</span></span>

<span data-ttu-id="86a92-112">En règle générale, le cycle de vie d’un contrôleur implique ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="86a92-112">Generally, a controller's lifecycle will involve:</span></span>

1. <span data-ttu-id="86a92-113">Un contrôleur est créé par un gestionnaire de périphériques lors de la détection d’une nouvelle source (par exemple, le gestionnaire de périphériques détecte et démarre le suivi d’une main).</span><span class="sxs-lookup"><span data-stu-id="86a92-113">A controller gets created by a device manager upon detection of a new source (for example, the device manager detects and starts tracking a hand).</span></span>

2. <span data-ttu-id="86a92-114">Dans la boucle Update () du contrôleur, il appelle le système d’API sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="86a92-114">In the controller's Update() loop, it calls into its underlying API system.</span></span>

3. <span data-ttu-id="86a92-115">Dans la même boucle de mise à jour, elle déclenche des modifications d’événements d’entrée en appelant directement dans le système d’entrée principal lui-même (par exemple, en déclenchant HandMeshUpdated ou HandJointsUpdated).</span><span class="sxs-lookup"><span data-stu-id="86a92-115">In the same update loop, it raises input event changes by calling directly into the core input system itself (for example, raising HandMeshUpdated, or HandJointsUpdated).</span></span>

## <a name="pointers-and-focus"></a><span data-ttu-id="86a92-116">Pointeurs et Focus</span><span class="sxs-lookup"><span data-stu-id="86a92-116">Pointers and focus</span></span>

<span data-ttu-id="86a92-117">Les pointeurs sont utilisés pour interagir avec les objets de jeu.</span><span class="sxs-lookup"><span data-stu-id="86a92-117">Pointers are used to interact with game objects.</span></span> <span data-ttu-id="86a92-118">Cette section décrit comment les pointeurs sont créés, comment ils sont mis à jour et comment ils déterminent le ou les objets qui sont activés.</span><span class="sxs-lookup"><span data-stu-id="86a92-118">This section describes how pointers are created, how they get updated, and how they determine the object(s) that are in focus.</span></span> <span data-ttu-id="86a92-119">Il couvre également les différents types de pointeurs qui existent et les scénarios dans lesquels ils sont actifs.</span><span class="sxs-lookup"><span data-stu-id="86a92-119">It will also cover the different types of pointers that exist and the scenarios in which they are active.</span></span>

### <a name="pointer-categories"></a><span data-ttu-id="86a92-120">Catégories de pointeurs</span><span class="sxs-lookup"><span data-stu-id="86a92-120">Pointer categories</span></span>

<span data-ttu-id="86a92-121">Les pointeurs appartiennent généralement à l’une des catégories suivantes :</span><span class="sxs-lookup"><span data-stu-id="86a92-121">Pointers generally fall into one of the following categories:</span></span>

- <span data-ttu-id="86a92-122">**Pointeurs Far**</span><span class="sxs-lookup"><span data-stu-id="86a92-122">**Far pointers**</span></span>

  <span data-ttu-id="86a92-123">Ces types de pointeurs sont utilisés pour interagir avec des objets éloignés de l’utilisateur (bien que loin soit défini comme simplement « pas près de »).</span><span class="sxs-lookup"><span data-stu-id="86a92-123">These types of pointers are used to interact with objects that are far away from the user (far away is defined as simply “not near”).</span></span> <span data-ttu-id="86a92-124">Ces types de pointeurs effectuent généralement un cast des lignes qui peuvent se trouver dans le monde entier et permettent à l’utilisateur d’interagir avec les objets qui ne sont pas immédiatement en regard de ceux-ci et de les manipuler.</span><span class="sxs-lookup"><span data-stu-id="86a92-124">These types of pointers generally cast lines that can go far into the world and allow the user to interact with and manipulate objects that are not immediately next to them.</span></span>

- <span data-ttu-id="86a92-125">**Pointeurs Near**</span><span class="sxs-lookup"><span data-stu-id="86a92-125">**Near pointers**</span></span>

  <span data-ttu-id="86a92-126">Ces types de pointeurs sont utilisés pour interagir avec des objets suffisamment proches de l’utilisateur pour les saisir, les toucher et les manipuler.</span><span class="sxs-lookup"><span data-stu-id="86a92-126">These types of pointers are used to interact with objects that are close enough to the user to grab, touch, and manipulate.</span></span> <span data-ttu-id="86a92-127">En règle générale, ces types de pointeurs interagissent avec les objets en recherchant des objets dans le voisinage voisin (en effectuant des Raycasting à de petites distances, en effectuant une conversion sphérique à la recherche d’objets dans le voisinage ou en énumérant des listes d’objets considérés comme pouvant être recherchés/touchable).</span><span class="sxs-lookup"><span data-stu-id="86a92-127">Generally, these types of pointers interact with objects by looking for objects in the nearby vicinity (either by doing raycasting at small distances, doing spherical casting looking for objects in the vicinity, or enumerating lists of objects that are considered grabbable/touchable).</span></span>

- <span data-ttu-id="86a92-128">**Pointeurs de téléversion**</span><span class="sxs-lookup"><span data-stu-id="86a92-128">**Teleport pointers**</span></span>

  <span data-ttu-id="86a92-129">Ces types de pointeurs se connectent au système de téléportage pour gérer le déplacement de l’utilisateur vers l’emplacement ciblé par le pointeur.</span><span class="sxs-lookup"><span data-stu-id="86a92-129">These types of pointers plug into the teleportation system to handle moving the user to the location targeted by the pointer.</span></span>

## <a name="pointer-mediation"></a><span data-ttu-id="86a92-130">Médiation du pointeur</span><span class="sxs-lookup"><span data-stu-id="86a92-130">Pointer mediation</span></span>

<span data-ttu-id="86a92-131">Étant donné qu’un seul contrôleur peut avoir plusieurs pointeurs (par exemple, la main articulée peut avoir à la fois des pointeurs d’interaction near et FAR), il existe un composant qui est responsable de la médiation du pointeur qui doit être actif.</span><span class="sxs-lookup"><span data-stu-id="86a92-131">Because a single controller can have multiple pointers (for example, the articulated hand can have both near and far interaction pointers), there exists a component that is responsible for mediating which pointer should be active.</span></span>

<span data-ttu-id="86a92-132">Par exemple, comme l’utilisateur approche un bouton enfoncé, le [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) doit s’arrêter et le [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) doit être engagé.</span><span class="sxs-lookup"><span data-stu-id="86a92-132">For example, as the user’s hand approaches a pressable button, the [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) should stop showing, and the [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) should be engaged.</span></span>

<span data-ttu-id="86a92-133">Cela est géré par le [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) , qui est chargé de déterminer les pointeurs actifs, en fonction de l’état de tous les pointeurs.</span><span class="sxs-lookup"><span data-stu-id="86a92-133">This is handled by the [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator), which is responsible for determining which pointers are active, based on the state of all pointers.</span></span> <span data-ttu-id="86a92-134">L’une des principales choses à faire est de désactiver les pointeurs Far quand un pointeur near est proche d’un objet (consultez [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) ).</span><span class="sxs-lookup"><span data-stu-id="86a92-134">One of the key things this does is disable far pointers when a near pointer is close to an object (please see [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator)).</span></span>

<span data-ttu-id="86a92-135">Il est possible de fournir une autre implémentation du médiateur du pointeur en modifiant la [`PointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile.PointerMediator) propriété sur le profil de pointeur.</span><span class="sxs-lookup"><span data-stu-id="86a92-135">It's possible to provide an alternate implementation of the pointer mediator by changing the [`PointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile.PointerMediator) property on the pointer profile.</span></span>

### <a name="how-to-disable-pointers"></a><span data-ttu-id="86a92-136">Comment désactiver des pointeurs</span><span class="sxs-lookup"><span data-stu-id="86a92-136">How to disable pointers</span></span>

<span data-ttu-id="86a92-137">Étant donné que le médiateur du pointeur exécute chaque frame, il finit par contrôler l’état actif/inactif de tous les pointeurs.</span><span class="sxs-lookup"><span data-stu-id="86a92-137">Because the pointer mediator runs every frame, it ends up controlling the active / inactive state of all pointers.</span></span> <span data-ttu-id="86a92-138">Par conséquent, si vous définissez la propriété IsInteractionEnabled d’un pointeur dans le code, elle est remplacée par le médiateur du pointeur à chaque frame.</span><span class="sxs-lookup"><span data-stu-id="86a92-138">Therefore, if you set a pointer's IsInteractionEnabled property in code, it will get overwritten by the pointer mediator every frame.</span></span> <span data-ttu-id="86a92-139">Au lieu de cela, vous pouvez spécifier le [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) pour contrôler si les pointeurs doivent être activés ou désactivés.</span><span class="sxs-lookup"><span data-stu-id="86a92-139">Instead, you can specify the [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) to control whether pointers should be on or off yourself.</span></span> <span data-ttu-id="86a92-140">Notez que cela ne fonctionne que si vous utilisez la valeur par défaut [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) et [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) dans MRTK.</span><span class="sxs-lookup"><span data-stu-id="86a92-140">Note that this will only work if you are using the default [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) and [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) in MRTK.</span></span>

#### <a name="example-disable-hand-rays-in-mrtk"></a><span data-ttu-id="86a92-141">Exemple : désactiver les rayons de main dans MRTK</span><span class="sxs-lookup"><span data-stu-id="86a92-141">Example: Disable hand rays in MRTK</span></span>

<span data-ttu-id="86a92-142">Le code suivant permet de désactiver les rayons main dans MRTK :</span><span class="sxs-lookup"><span data-stu-id="86a92-142">The following code will turn off the hand rays in MRTK:</span></span>

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff);

// Turn off hand rays for the right hand only
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Right);
```

<span data-ttu-id="86a92-143">Le code suivant renverra des rayons de main à leur comportement par défaut dans MRTK :</span><span class="sxs-lookup"><span data-stu-id="86a92-143">The following code will return hand rays to their default behavior in MRTK:</span></span>

```c#
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.Default);
```

<span data-ttu-id="86a92-144">Le code suivant force les rayons de main à être activés, sans tenir compte du fait qu’ils sont à portée de main :</span><span class="sxs-lookup"><span data-stu-id="86a92-144">The following code will force hand rays to be on, regardless if near a grabbable:</span></span>

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOn);
```

<span data-ttu-id="86a92-145">[`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) Pour plus d’exemples, consultez et.</span><span class="sxs-lookup"><span data-stu-id="86a92-145">See [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) and [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) for more examples.</span></span>

### <a name="focusprovider"></a><span data-ttu-id="86a92-146">FocusProvider</span><span class="sxs-lookup"><span data-stu-id="86a92-146">FocusProvider</span></span>

<span data-ttu-id="86a92-147">Le [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) est le principal responsable de l’itération au sein de la liste de tous les pointeurs et de la définition de l’objet ayant le focus pour chaque pointeur.</span><span class="sxs-lookup"><span data-stu-id="86a92-147">The [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) is the workhorse that is responsible for iterating over the list of all pointers and figuring out what the focused object is for each pointer.</span></span>

<span data-ttu-id="86a92-148">Dans chaque `Update()` appel, ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="86a92-148">In each `Update()` call, this will:</span></span>

1. <span data-ttu-id="86a92-149">Mettez à jour tous les pointeurs, par Raycasting et en procédant à la détection d’atteinte configurée par le pointeur lui-même (par exemple, le pointeur Sphere pourrait spécifier le raycastMode SphereOverlap, de sorte que FocusProvider effectue une collision basée sur les sphères)</span><span class="sxs-lookup"><span data-stu-id="86a92-149">Update all of the pointers, by raycasting and doing hit detection as-configured by the pointer itself (for example, the sphere pointer could specify the SphereOverlap raycastMode, so FocusProvider will do a sphere-based collision)</span></span>

2. <span data-ttu-id="86a92-150">Mettre à jour l’objet ayant le focus en fonction du pointeur (par exemple, si un objet a acquis le focus, il déclenche également des événements pour ces objets, si un objet a perdu le focus, il déclenche le focus, etc.).</span><span class="sxs-lookup"><span data-stu-id="86a92-150">Update the focused object on a per-pointer basis (i.e. if an object gained focus, it would also trigger events to those object, if an object lost focus, it would trigger focus lost, etc).</span></span>

### <a name="pointer-configuration-and-lifecycle"></a><span data-ttu-id="86a92-151">Configuration du pointeur et cycle de vie</span><span class="sxs-lookup"><span data-stu-id="86a92-151">Pointer configuration and lifecycle</span></span>

<span data-ttu-id="86a92-152">Les [pointeurs peuvent être configurés](../features/input/pointers.md) dans la section *pointeurs* du profil de système d’entrée.</span><span class="sxs-lookup"><span data-stu-id="86a92-152">[Pointers can be configured](../features/input/pointers.md) in the *Pointers* section of the input system profile.</span></span>

<span data-ttu-id="86a92-153">La durée de vie d’un pointeur est généralement la suivante :</span><span class="sxs-lookup"><span data-stu-id="86a92-153">The lifetime of a pointer is generally the following:</span></span>

1. <span data-ttu-id="86a92-154">Un gestionnaire de périphériques détectera la présence d’un contrôleur.</span><span class="sxs-lookup"><span data-stu-id="86a92-154">A device manager will detect the presence of a controller.</span></span> <span data-ttu-id="86a92-155">Ce gestionnaire de périphériques créera ensuite le jeu de pointeurs associé au contrôleur via un appel à [`RequestPointers`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) .</span><span class="sxs-lookup"><span data-stu-id="86a92-155">This device manager will then create the set of pointers associated with the controller via a call to [`RequestPointers`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager).</span></span>

2. <span data-ttu-id="86a92-156">Le FocusProvider, dans sa boucle Update (), effectue une itération sur tous les pointeurs valides et effectue la logique de détection d’accès raycast ou associée.</span><span class="sxs-lookup"><span data-stu-id="86a92-156">The FocusProvider, in its Update() loop, will iterate over all of the valid pointers and do the associated raycast or hit detection logic.</span></span> <span data-ttu-id="86a92-157">Utilisé pour déterminer l’objet qui est axé sur chaque pointeur particulier.</span><span class="sxs-lookup"><span data-stu-id="86a92-157">This is used to determine the object that is focused by each particular pointer.</span></span>

    - <span data-ttu-id="86a92-158">Étant donné qu’il est possible d’avoir plusieurs sources d’entrée actives en même temps (par exemple, deux mains actives), il est également possible d’avoir plusieurs objets qui ont le focus en même temps.</span><span class="sxs-lookup"><span data-stu-id="86a92-158">Because it's possible to have multiple sources of input active at the same time (for example, two hands active present), it's also possible to have multiple objects that have focus at the same time.</span></span>

3. <span data-ttu-id="86a92-159">Lors de la découverte de la perte d’une source de contrôleur, le gestionnaire de périphériques détruit les pointeurs associés au contrôleur perdu.</span><span class="sxs-lookup"><span data-stu-id="86a92-159">The device manager, upon discovering that a controller source was lost, will tear down the pointers associated with the lost controller.</span></span>