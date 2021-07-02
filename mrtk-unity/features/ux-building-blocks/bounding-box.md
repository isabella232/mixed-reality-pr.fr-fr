---
title: Rectangle englobant
description: Vue d’ensemble du cadre englobant dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, cadre englobant
ms.openlocfilehash: e8e3587ba871e127590a975b688a70db337daa19
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177545"
---
# <a name="bounding-box"></a><span data-ttu-id="d9e78-104">Rectangle englobant</span><span class="sxs-lookup"><span data-stu-id="d9e78-104">Bounding box</span></span>

![Rectangle englobant](../images/bounding-box/MRTK_BoundingBox_Main.png)

> [!NOTE]
> <span data-ttu-id="d9e78-106">Le cadre englobant est déconseillé et remplacé par son [contrôle de limites](bounds-control.md)de successeurs.</span><span class="sxs-lookup"><span data-stu-id="d9e78-106">Bounding box is deprecated and replaced by its successor [bounds control](bounds-control.md).</span></span> <span data-ttu-id="d9e78-107">Utilisez l' [une des options de migration](#migrating-to-bounds-control) pour mettre à niveau les objets de jeu existants.</span><span class="sxs-lookup"><span data-stu-id="d9e78-107">Use [one of the migration options](#migrating-to-bounds-control) to upgrade existing game objects.</span></span>

<span data-ttu-id="d9e78-108">Le [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script fournit des fonctionnalités de base pour transformer des objets en réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="d9e78-108">The [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script provides basic functionality for transforming objects in mixed reality.</span></span> <span data-ttu-id="d9e78-109">Un cadre englobant affiche un cube autour de l’hologramme pour indiquer qu’il peut être utilisé avec.</span><span class="sxs-lookup"><span data-stu-id="d9e78-109">A bounding box will show a cube around the hologram to indicate that it can be interacted with.</span></span> <span data-ttu-id="d9e78-110">Les poignées sur les angles et les bords du cube autorisent la mise à l’échelle ou la rotation de l’objet.</span><span class="sxs-lookup"><span data-stu-id="d9e78-110">Handles on the corners and edges of the cube allow scaling or rotating the object.</span></span> <span data-ttu-id="d9e78-111">Le cadre englobant réagit également aux entrées d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d9e78-111">The bounding box also reacts to user input.</span></span> <span data-ttu-id="d9e78-112">sur HoloLens 2, par exemple, le cadre englobant répond à la proximité d’un doigt, en fournissant un retour visuel pour aider à percevoir la distance par rapport à l’objet.</span><span class="sxs-lookup"><span data-stu-id="d9e78-112">On HoloLens 2, for example, the bounding box responds to finger proximity, providing visual feedback to help perceive the distance from the object.</span></span> <span data-ttu-id="d9e78-113">Toutes les interactions et tous les visuels peuvent être facilement personnalisés.</span><span class="sxs-lookup"><span data-stu-id="d9e78-113">All interactions and visuals can be easily customized.</span></span>

<span data-ttu-id="d9e78-114">pour plus d’informations, consultez [zone englobante et barre d’application](/windows/mixed-reality/app-bar-and-bounding-box) dans le Centre de développement Windows.</span><span class="sxs-lookup"><span data-stu-id="d9e78-114">For more information, see [Bounding box and App bar](/windows/mixed-reality/app-bar-and-bounding-box) in the Windows Dev Center.</span></span>

## <a name="example-scene"></a><span data-ttu-id="d9e78-115">Exemple de scène</span><span class="sxs-lookup"><span data-stu-id="d9e78-115">Example scene</span></span>

<span data-ttu-id="d9e78-116">Vous trouverez des exemples de configurations de cadre englobant dans la `BoundingBoxExamples` scène.</span><span class="sxs-lookup"><span data-stu-id="d9e78-116">You can find examples of bounding box configurations in the `BoundingBoxExamples` scene.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_Examples.png" alt="Bounding Box Examples">

## <a name="how-to-add-and-configure-a-bounding-box-using-unity-inspector"></a><span data-ttu-id="d9e78-117">Comment ajouter et configurer un cadre englobant à l’aide de l’inspecteur Unity</span><span class="sxs-lookup"><span data-stu-id="d9e78-117">How to add and configure a bounding box using Unity Inspector</span></span>

1. <span data-ttu-id="d9e78-118">Ajouter un conflit de zone à un objet</span><span class="sxs-lookup"><span data-stu-id="d9e78-118">Add Box Collider to an object</span></span>
2. <span data-ttu-id="d9e78-119">Affecter `BoundingBox` un script à un objet</span><span class="sxs-lookup"><span data-stu-id="d9e78-119">Assign `BoundingBox` script to an object</span></span>
3. <span data-ttu-id="d9e78-120">Configurer des options, telles que les méthodes « activation » (voir la section Propriétés de l' [inspecteur](#inspector-properties) ci-dessous)</span><span class="sxs-lookup"><span data-stu-id="d9e78-120">Configure options, such as 'Activation' methods (see [Inspector properties](#inspector-properties) section below)</span></span>
4. <span data-ttu-id="d9e78-121">Facultatif assigner des prefabs et des matériaux pour un cadre englobant de style HoloLens 2 (consultez la section relative aux [styles de Handle](#handle-styles) ci-dessous)</span><span class="sxs-lookup"><span data-stu-id="d9e78-121">(Optional) Assign prefabs and materials for a HoloLens 2 style bounding box (see [Handle styles](#handle-styles) section below)</span></span>

> [!NOTE]
> <span data-ttu-id="d9e78-122">Utilisez l' *objet cible* et le champ de *remplacement de limites* dans l’inspecteur pour assigner un objet et un conflit spécifiques dans l’objet avec plusieurs composants enfants.</span><span class="sxs-lookup"><span data-stu-id="d9e78-122">Use *Target Object* and *Bounds Override* field in the inspector to assign specific object and collider in the object with multiple child components.</span></span>

![Cadre englobant 1](../images/bounding-box/MRTK_BoundingBox_Assign.png)

## <a name="how-to-add-and-configure-a-bounding-box-in-the-code"></a><span data-ttu-id="d9e78-124">Comment ajouter et configurer un cadre englobant dans le code</span><span class="sxs-lookup"><span data-stu-id="d9e78-124">How to add and configure a bounding box in the code</span></span>

1. <span data-ttu-id="d9e78-125">Instancier le cube GameObject</span><span class="sxs-lookup"><span data-stu-id="d9e78-125">Instantiate cube GameObject</span></span>

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. <span data-ttu-id="d9e78-126">Assigner `BoundingBox` un script à un objet avec un conflit à l’aide de AddComponent<> ()</span><span class="sxs-lookup"><span data-stu-id="d9e78-126">Assign `BoundingBox` script to an object with collider, using AddComponent<>()</span></span>

    ```c#
    private BoundingBox bbox;
    bbox = cube.AddComponent<BoundingBox>();
    ```

1. <span data-ttu-id="d9e78-127">Configurer les options (voir la section Propriétés de l' [inspecteur](#inspector-properties) ci-dessous)</span><span class="sxs-lookup"><span data-stu-id="d9e78-127">Configure options (see [Inspector properties](#inspector-properties) section below)</span></span>

    ```c#
    // Make the scale handles large
    bbox.ScaleHandleSize = 0.1f;
    // Hide rotation handles
    bbox.ShowRotationHandleForX = false;
    bbox.ShowRotationHandleForY = false;
    bbox.ShowRotationHandleForZ = false;
    ```

1. <span data-ttu-id="d9e78-128">Facultatif affectez prefabs et materials pour un cadre englobant de style HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="d9e78-128">(Optional) Assign prefabs and materials for a HoloLens 2 style bounding box.</span></span> <span data-ttu-id="d9e78-129">Cela nécessite toujours des affectations via l’inspecteur, car les matériaux et les prefabs doivent être chargés dynamiquement.</span><span class="sxs-lookup"><span data-stu-id="d9e78-129">This still requires assignments through the inspector since the materials and prefabs should be dynamically loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="d9e78-130">Utilisation du dossier « Resources » ou du [nuanceur Unity. Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) pour le chargement dynamique des nuanceurs n’est pas recommandé, car les permutations de nuanceur peuvent être manquantes au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="d9e78-130">Using Unity's 'Resources' folder or [Shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) for dynamically loading shaders is not recommended since shader permutations may be missing at runtime.</span></span>

```c#
bbox.BoxMaterial = [Assign BoundingBox.mat]
bbox.BoxGrabbedMaterial = [Assign BoundingBoxGrabbed.mat]
bbox.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
bbox.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
bbox.ScaleHandlePrefab = [Assign MRTK_BoundingBox_ScaleHandle.prefab]
bbox.ScaleHandleSlatePrefab = [Assign MRTK_BoundingBox_ScaleHandle_Slate.prefab]
bbox.ScaleHandleSize = 0.016f;
bbox.ScaleHandleColliderPadding = 0.016f;
bbox.RotationHandleSlatePrefab = [Assign MRTK_BoundingBox_RotateHandle.prefab]
bbox.RotationHandleSize = 0.016f;
bbox.RotateHandleColliderPadding = 0.016f;
```

### <a name="example-set-minimum-maximum-bounding-box-scale-using-minmaxscaleconstraint"></a><span data-ttu-id="d9e78-131">Exemple : définir la mise à l’échelle du cadre englobant maximal à l’aide de MinMaxScaleConstraint</span><span class="sxs-lookup"><span data-stu-id="d9e78-131">Example: Set minimum, maximum bounding box scale using MinMaxScaleConstraint</span></span>

<span data-ttu-id="d9e78-132">Pour définir l’échelle minimale et maximale, utilisez [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) .</span><span class="sxs-lookup"><span data-stu-id="d9e78-132">To set the minimum and maximum scale, use the [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint).</span></span> <span data-ttu-id="d9e78-133">Vous pouvez également utiliser MinMaxScaleConstraint pour définir une échelle minimale et maximale pour [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) .</span><span class="sxs-lookup"><span data-stu-id="d9e78-133">You can also use MinMaxScaleConstraint to set minimum and maximum scale for [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler).</span></span>

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bbox = cube.AddComponent<BoundingBox>();
// Important: BoundingBox creates a scale handler on start if one does not exist
// do not use AddComponent, as that will create a  duplicate handler that will not be used
MinMaxScaleConstraint scaleConstraint = bbox.gameObject.GetComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounding-box-around-a-game-object"></a><span data-ttu-id="d9e78-134">Exemple : ajouter un cadre englobant autour d’un objet de jeu</span><span class="sxs-lookup"><span data-stu-id="d9e78-134">Example: Add bounding box around a game object</span></span>

<span data-ttu-id="d9e78-135">Pour ajouter un cadre englobant autour d’un objet, ajoutez simplement un `BoundingBox` composant à ce dernier :</span><span class="sxs-lookup"><span data-stu-id="d9e78-135">To add a bounding box around an object, simply add a `BoundingBox` component to it:</span></span>

```c#
private void PutABoxAroundIt(GameObject target)
{
   target.AddComponent<BoundingBox>();
}
```

## <a name="inspector-properties"></a><span data-ttu-id="d9e78-136">Propriétés de l’inspecteur</span><span class="sxs-lookup"><span data-stu-id="d9e78-136">Inspector properties</span></span>

### <a name="target-object"></a><span data-ttu-id="d9e78-137">Objet cible</span><span class="sxs-lookup"><span data-stu-id="d9e78-137">Target object</span></span>

<span data-ttu-id="d9e78-138">Cette propriété spécifie l’objet qui sera transformé par la manipulation de cadre englobant.</span><span class="sxs-lookup"><span data-stu-id="d9e78-138">This property specifies which object will get transformed by the bounding box manipulation.</span></span> <span data-ttu-id="d9e78-139">Si aucun objet n’est défini, la zone englobante prend par défaut la valeur de l’objet propriétaire.</span><span class="sxs-lookup"><span data-stu-id="d9e78-139">If no object is set, the bounding box defaults to the owner object.</span></span>

### <a name="bounds-override"></a><span data-ttu-id="d9e78-140">Substitutions de limites</span><span class="sxs-lookup"><span data-stu-id="d9e78-140">Bounds override</span></span>

<span data-ttu-id="d9e78-141">Définit un conflit de cases à partir de l’objet pour le calcul de limites.</span><span class="sxs-lookup"><span data-stu-id="d9e78-141">Sets a box collider from the object for bounds computation.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="d9e78-142">Comportement d’activation</span><span class="sxs-lookup"><span data-stu-id="d9e78-142">Activation behavior</span></span>

<span data-ttu-id="d9e78-143">Il existe plusieurs options pour activer l’interface de cadre englobant.</span><span class="sxs-lookup"><span data-stu-id="d9e78-143">There are several options to activate the bounding box interface.</span></span>

* <span data-ttu-id="d9e78-144">*Activer sur Start*: le cadre englobant devient visible une fois la scène démarrée.</span><span class="sxs-lookup"><span data-stu-id="d9e78-144">*Activate On Start*: Bounding box becomes visible once the scene is started.</span></span>
* <span data-ttu-id="d9e78-145">*Activer par proximité*: le cadre englobant devient visible quand une main articulée est proche de l’objet.</span><span class="sxs-lookup"><span data-stu-id="d9e78-145">*Activate By Proximity*: Bounding box becomes visible when an articulated hand is close to the object.</span></span>
* <span data-ttu-id="d9e78-146">*Activer par pointeur*: le cadre englobant devient visible lorsqu’il est ciblé par un pointeur de rayon.</span><span class="sxs-lookup"><span data-stu-id="d9e78-146">*Activate By Pointer*: Bounding box becomes visible when it is targeted by a hand-ray pointer.</span></span>
* <span data-ttu-id="d9e78-147">*Activer manuellement*: le cadre englobant ne devient pas visible automatiquement.</span><span class="sxs-lookup"><span data-stu-id="d9e78-147">*Activate Manually*: Bounding box does not become visible automatically.</span></span> <span data-ttu-id="d9e78-148">Vous pouvez l’activer manuellement par le biais d’un script en accédant à la propriété boundingBox. active.</span><span class="sxs-lookup"><span data-stu-id="d9e78-148">You can manually activate it through a script by accessing the boundingBox.Active property.</span></span>

### <a name="scale-minimum"></a><span data-ttu-id="d9e78-149">Échelle minimale</span><span class="sxs-lookup"><span data-stu-id="d9e78-149">Scale minimum</span></span>

<span data-ttu-id="d9e78-150">Échelle minimale autorisée.</span><span class="sxs-lookup"><span data-stu-id="d9e78-150">The minimum allowed scale.</span></span> <span data-ttu-id="d9e78-151">Cette propriété est déconseillée et il est préférable d’ajouter un [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script.</span><span class="sxs-lookup"><span data-stu-id="d9e78-151">This property is deprecated and it is preferable to add a [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script.</span></span> <span data-ttu-id="d9e78-152">Si ce script est ajouté, l’échelle minimale est prise à partir de celle-ci plutôt que du rectangle englobant.</span><span class="sxs-lookup"><span data-stu-id="d9e78-152">If this script is added, the minimum scale will be taken from it instead of from the bounding box.</span></span>

### <a name="scale-maximum"></a><span data-ttu-id="d9e78-153">Échelle maximale</span><span class="sxs-lookup"><span data-stu-id="d9e78-153">Scale maximum</span></span>

<span data-ttu-id="d9e78-154">Échelle maximale autorisée.</span><span class="sxs-lookup"><span data-stu-id="d9e78-154">The maximum allowed scale.</span></span> <span data-ttu-id="d9e78-155">Cette propriété est déconseillée et il est préférable d’ajouter un [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script.</span><span class="sxs-lookup"><span data-stu-id="d9e78-155">This property is deprecated and it is preferable to add a [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script.</span></span> <span data-ttu-id="d9e78-156">Si ce script est ajouté, la mise à l’échelle maximale est prise à partir de celle-ci plutôt que du rectangle englobant.</span><span class="sxs-lookup"><span data-stu-id="d9e78-156">If this script is added, the maximum scale will be taken from it instead of from the bounding box.</span></span>

### <a name="box-display"></a><span data-ttu-id="d9e78-157">Affichage de zone</span><span class="sxs-lookup"><span data-stu-id="d9e78-157">Box display</span></span>

<span data-ttu-id="d9e78-158">Diverses options de visualisation de cadre englobant.</span><span class="sxs-lookup"><span data-stu-id="d9e78-158">Various bounding box visualization options.</span></span>

<span data-ttu-id="d9e78-159">Si l’option aplatir l’axe est définie sur *aplatir automatiquement*, le script interdit la manipulation le long de l’axe avec la plus petite étendue.</span><span class="sxs-lookup"><span data-stu-id="d9e78-159">If Flatten Axis is set to *Flatten Auto*, the script will disallow manipulation along the axis with the smallest extent.</span></span> <span data-ttu-id="d9e78-160">Il en résulte une zone englobante 2D, qui est généralement utilisée pour les objets légers.</span><span class="sxs-lookup"><span data-stu-id="d9e78-160">This results in a 2D bounding box, which is usually used for thin objects.</span></span>

### <a name="handles"></a><span data-ttu-id="d9e78-161">Poignées</span><span class="sxs-lookup"><span data-stu-id="d9e78-161">Handles</span></span>

<span data-ttu-id="d9e78-162">Vous pouvez assigner les éléments Material et Prefab pour remplacer le style de handle.</span><span class="sxs-lookup"><span data-stu-id="d9e78-162">You can assign the material and prefab to override the handle style.</span></span> <span data-ttu-id="d9e78-163">Si aucun handle n’est affecté, ils sont affichés dans le style par défaut.</span><span class="sxs-lookup"><span data-stu-id="d9e78-163">If no handles are assigned, they will be displayed in the default style.</span></span>

## <a name="events"></a><span data-ttu-id="d9e78-164">Événements</span><span class="sxs-lookup"><span data-stu-id="d9e78-164">Events</span></span>

<span data-ttu-id="d9e78-165">Le cadre englobant fournit les événements suivants.</span><span class="sxs-lookup"><span data-stu-id="d9e78-165">Bounding box provides the following events.</span></span> <span data-ttu-id="d9e78-166">Cet exemple utilise ces événements pour lire les commentaires audio.</span><span class="sxs-lookup"><span data-stu-id="d9e78-166">This example uses these events to play audio feedback.</span></span>

* <span data-ttu-id="d9e78-167">**Rotate Started**: déclenché au début de la rotation.</span><span class="sxs-lookup"><span data-stu-id="d9e78-167">**Rotate Started**: Fired when rotation starts.</span></span>
* <span data-ttu-id="d9e78-168">**Rotation terminée**: déclenché à la fin de la rotation.</span><span class="sxs-lookup"><span data-stu-id="d9e78-168">**Rotate Ended**: Fired when rotation ends.</span></span>
* <span data-ttu-id="d9e78-169">Mise à l' **échelle démarrée**: se déclenche lors du démarrage de la mise à l’échelle.</span><span class="sxs-lookup"><span data-stu-id="d9e78-169">**Scale Started**: Fires when scaling starts.</span></span>
* <span data-ttu-id="d9e78-170">Mise à l' **échelle terminée**: se déclenche lorsque la mise à l’échelle se termine.</span><span class="sxs-lookup"><span data-stu-id="d9e78-170">**Scale Ended**: Fires when scaling ends.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_Events.png" width="450" alt="Events">

## <a name="handle-styles"></a><span data-ttu-id="d9e78-171">Gérer les styles</span><span class="sxs-lookup"><span data-stu-id="d9e78-171">Handle styles</span></span>

<span data-ttu-id="d9e78-172">par défaut, lorsque vous affectez simplement le [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script, il affiche le descripteur de la HoloLens premier style gen.</span><span class="sxs-lookup"><span data-stu-id="d9e78-172">By default, when you just assign the [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script, it will show the handle of the HoloLens 1st gen style.</span></span> <span data-ttu-id="d9e78-173">pour utiliser HoloLens 2 poignées de style, vous devez assigner les prefabs et les matériaux de handle appropriés.</span><span class="sxs-lookup"><span data-stu-id="d9e78-173">To use HoloLens 2 style handles, you need to assign proper handle prefabs and materials.</span></span>

![Styles de handle de cadre englobant](../images/bounding-box/MRTK_BoundingBox_HandleStyles1.png)

<span data-ttu-id="d9e78-175">vous trouverez ci-dessous les prefabs, les matériaux et les valeurs de mise à l’échelle pour les poignées de cadre englobant de style HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="d9e78-175">Below are the prefabs, materials, and the scaling values for the HoloLens 2 style bounding box handles.</span></span> <span data-ttu-id="d9e78-176">Cet exemple se trouve dans la `BoundingBoxExamples` scène.</span><span class="sxs-lookup"><span data-stu-id="d9e78-176">You can find this example in the `BoundingBoxExamples` scene.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_HandleStyles2.png" width="450" alt="HandStyles 2">

### <a name="handles-setup-for-hololens-2-style"></a><span data-ttu-id="d9e78-177">handles (programme d’installation de HoloLens 2 style)</span><span class="sxs-lookup"><span data-stu-id="d9e78-177">Handles (Setup for HoloLens 2 style)</span></span>

* <span data-ttu-id="d9e78-178">**Matériau de gestion**: BoundingBoxHandleWhite. mat</span><span class="sxs-lookup"><span data-stu-id="d9e78-178">**Handle Material**: BoundingBoxHandleWhite.mat</span></span>
* <span data-ttu-id="d9e78-179">**Gérer un matériau retiré**: BoundingBoxHandleBlueGrabbed. mat</span><span class="sxs-lookup"><span data-stu-id="d9e78-179">**Handle Grabbed Material**: BoundingBoxHandleBlueGrabbed.mat</span></span>
* <span data-ttu-id="d9e78-180">Descripteur de mise à l' **échelle Prefab**: MRTK_BoundingBox_ScaleHandle. Prefab</span><span class="sxs-lookup"><span data-stu-id="d9e78-180">**Scale Handle Prefab**: MRTK_BoundingBox_ScaleHandle.prefab</span></span>
* <span data-ttu-id="d9e78-181">**Poignée d’échelle ardoise Prefab**: MRTK_BoundingBox_ScaleHandle_Slate. Prefab</span><span class="sxs-lookup"><span data-stu-id="d9e78-181">**Scale Handle Slate Prefab**: MRTK_BoundingBox_ScaleHandle_Slate.prefab</span></span>
* <span data-ttu-id="d9e78-182">**Taille du handle** de l’échelle : 0,016 (1,6 cm)</span><span class="sxs-lookup"><span data-stu-id="d9e78-182">**Scale Handle Size**: 0.016 (1.6cm)</span></span>
* <span data-ttu-id="d9e78-183">Mise à l' **échelle du remplissage du conflit**: 0,016 (rend le conflit de manipulation légèrement plus grand que le visuel de la poignée)</span><span class="sxs-lookup"><span data-stu-id="d9e78-183">**Scale Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>
* <span data-ttu-id="d9e78-184">**Handle de rotation Prefab**: MRTK_BoundingBox_RotateHandle. Prefab</span><span class="sxs-lookup"><span data-stu-id="d9e78-184">**Rotation Handle Prefab**: MRTK_BoundingBox_RotateHandle.prefab</span></span>
* <span data-ttu-id="d9e78-185">**Taille du handle de rotation**: 0,016</span><span class="sxs-lookup"><span data-stu-id="d9e78-185">**Rotation Handle Size**: 0.016</span></span>
* <span data-ttu-id="d9e78-186">La **poignée de rotation marge intérieure du conflit**: 0,016 (rend le conflit de manipulation légèrement plus grand que le visuel de la poignée)</span><span class="sxs-lookup"><span data-stu-id="d9e78-186">**Rotation Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>

### <a name="proximity-setup-for-hololens-2-style"></a><span data-ttu-id="d9e78-187">proximité (configuration du style de HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="d9e78-187">Proximity (Setup for HoloLens 2 style)</span></span>

<span data-ttu-id="d9e78-188">Affichez et masquez les poignées avec l’animation en fonction de la distance des mains.</span><span class="sxs-lookup"><span data-stu-id="d9e78-188">Show and hide the handles with animation based on the distance to the hands.</span></span> <span data-ttu-id="d9e78-189">Il a une animation de mise à l’échelle en deux étapes.</span><span class="sxs-lookup"><span data-stu-id="d9e78-189">It has two-step scaling animation.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_Proximity.png" alt="Proximity">

* <span data-ttu-id="d9e78-190">**Effet de proximité actif**: activer l’activation du handle basé sur la proximité</span><span class="sxs-lookup"><span data-stu-id="d9e78-190">**Proximity Effect Active**: Enable proximity-based handle activation</span></span>
* <span data-ttu-id="d9e78-191">**Gérer la proximité moyenne**: distance pour la mise à l’échelle des premières étapes</span><span class="sxs-lookup"><span data-stu-id="d9e78-191">**Handle Medium Proximity**: Distance for the 1st step scaling</span></span>
* <span data-ttu-id="d9e78-192">**Approche de proximité**: distance pour la mise à l’échelle de la deuxième étape</span><span class="sxs-lookup"><span data-stu-id="d9e78-192">**Handle Close Proximity**: Distance for the 2nd step scaling</span></span>
* <span data-ttu-id="d9e78-193">**Échelle lointaine**: valeur de mise à l’échelle par défaut de la ressource de descripteur lorsque les mains sont hors de portée de l’interaction du cadre englobant (distance définie ci-dessus par « handle la proximité moyenne ».</span><span class="sxs-lookup"><span data-stu-id="d9e78-193">**Far Scale**: Default scale value of the handle asset when the hands are out of range of the bounding box interaction (distance defined above by 'Handle Medium Proximity'.</span></span> <span data-ttu-id="d9e78-194">Utilisez 0 pour masquer le descripteur par défaut)</span><span class="sxs-lookup"><span data-stu-id="d9e78-194">Use 0 to hide handle by default)</span></span>
* <span data-ttu-id="d9e78-195">**Échelle moyenne**: valeur de mise à l’échelle de la ressource de poignée lorsque les mains sont dans la plage de l’interaction du cadre englobant (distance définie ci-dessus par « gérer la proximité ».</span><span class="sxs-lookup"><span data-stu-id="d9e78-195">**Medium Scale**: Scale value of the handle asset when the hands are within range of the bounding box interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="d9e78-196">Utiliser 1 pour afficher la taille normale</span><span class="sxs-lookup"><span data-stu-id="d9e78-196">Use 1 to show normal size)</span></span>
* <span data-ttu-id="d9e78-197">**Clôture** de l’échelle : valeur de mise à l’échelle de la ressource de poignée lorsque les mains sont dans la plage de l’interaction de manipulation (distance définie ci-dessus par « poignée de proximité ».</span><span class="sxs-lookup"><span data-stu-id="d9e78-197">**Close Scale**: Scale value of the handle asset when the hands are within range of the grab interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="d9e78-198">Utiliser 1. x pour afficher une taille supérieure)</span><span class="sxs-lookup"><span data-stu-id="d9e78-198">Use 1.x to show bigger size)</span></span>

## <a name="making-an-object-movable-with-manipulation-handler"></a><span data-ttu-id="d9e78-199">Rendre un objet déplaçable avec le gestionnaire de manipulation</span><span class="sxs-lookup"><span data-stu-id="d9e78-199">Making an object movable with manipulation handler</span></span>

<span data-ttu-id="d9e78-200">Un cadre englobant peut être combiné avec [`ManipulationHandler.cs`](manipulation-handler.md) pour rendre l’objet déplaçable à l’aide de l’interaction Far.</span><span class="sxs-lookup"><span data-stu-id="d9e78-200">A bounding box can be combined with [`ManipulationHandler.cs`](manipulation-handler.md) to make the object movable using far interaction.</span></span> <span data-ttu-id="d9e78-201">Le gestionnaire de manipulation prend en charge les interactions une et deux.</span><span class="sxs-lookup"><span data-stu-id="d9e78-201">The manipulation handler supports both one and two-handed interactions.</span></span> <span data-ttu-id="d9e78-202">Le suivi de la [main](../input/hand-tracking.md) peut être utilisé pour interagir avec un objet plus proche.</span><span class="sxs-lookup"><span data-stu-id="d9e78-202">[Hand tracking](../input/hand-tracking.md) can be used to interact with an object up close.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_ManipulationHandler.png" width="450" alt="Manipulation Handler">

<span data-ttu-id="d9e78-203">Pour que les bords du cadre englobant se comportent de la même façon lors de leur déplacement à l’aide [`ManipulationHandler`](manipulation-handler.md) de l’interaction Far, il est recommandé de connecter ses événements pour la *manipulation démarrée*  /  *sur la manipulation terminée* `BoundingBox.HighlightWires`  /  `BoundingBox.UnhighlightWires` , comme illustré dans la capture d’écran ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="d9e78-203">In order for the bounding box edges to behave the same way when moving it using [`ManipulationHandler`](manipulation-handler.md)'s far interaction, it is advised to connect its events for *On Manipulation Started* / *On Manipulation Ended* to `BoundingBox.HighlightWires` / `BoundingBox.UnhighlightWires` respectively, as shown in the screenshot above.</span></span>

## <a name="migrating-to-bounds-control"></a><span data-ttu-id="d9e78-204">Migrer vers le contrôle de limites</span><span class="sxs-lookup"><span data-stu-id="d9e78-204">Migrating to bounds control</span></span>

<span data-ttu-id="d9e78-205">Les prefabs et les instances existantes qui utilisent le [cadre englobant](bounding-box.md) peuvent être mis à niveau vers le nouveau contrôle des limites via la [fenêtre de migration](../tools/migration-window.md) qui fait partie du package d’outils MRTK.</span><span class="sxs-lookup"><span data-stu-id="d9e78-205">Existing prefabs and instances using [bounding box](bounding-box.md) can be upgraded to the new bounds control via the [migration window](../tools/migration-window.md) which is part of the MRTK tools package.</span></span>

<span data-ttu-id="d9e78-206">Pour mettre à niveau des instances individuelles du cadre englobant, il existe également une option de migration à l’intérieur de l’inspecteur de propriété du composant.</span><span class="sxs-lookup"><span data-stu-id="d9e78-206">For upgrading individual instances of bounding box there's also an a migration option inside the property inspector of the component.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds Control Migrate">
