---
title: Collection d’objets
description: Vue d’ensemble de la collection d’objets dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, collection d’objets,
ms.openlocfilehash: 8390e9c4a7bd419f99a5c8c4af7e7a2eca1d8f3f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177049"
---
# <a name="object-collection"></a><span data-ttu-id="3daa1-104">Collection d’objets</span><span class="sxs-lookup"><span data-stu-id="3daa1-104">Object collection</span></span>

![Collection d’objets](../images/object-collection/MRTK_ObjectCollection_Main.jpg)

<span data-ttu-id="3daa1-106">La collection d’objets est un script qui permet de disposer un tableau d’objets dans des formes tridimensionnelles prédéfinies.</span><span class="sxs-lookup"><span data-stu-id="3daa1-106">Object collection is a script to help lay out an array of objects in predefined three-dimensional shapes.</span></span> <span data-ttu-id="3daa1-107">Il prend en charge divers styles de surface, y compris les plans, les cylindres, les sphères et les radiales.</span><span class="sxs-lookup"><span data-stu-id="3daa1-107">It supports various surface styles including plane, cylinder, sphere, and radial.</span></span> <span data-ttu-id="3daa1-108">Comme il prend en charge n’importe quel objet dans Unity, il peut être utilisé pour mettre en forme des objets 2D et 3D.</span><span class="sxs-lookup"><span data-stu-id="3daa1-108">Since it supports any object in Unity, it can be used to layout both 2D and 3D objects.</span></span>

## <a name="object-collection-scripts"></a><span data-ttu-id="3daa1-109">Scripts de collection d’objets</span><span class="sxs-lookup"><span data-stu-id="3daa1-109">Object collection scripts</span></span>

- <span data-ttu-id="3daa1-110">[`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) prend en charge les types de surface cylindrique, plan, sphère et radial</span><span class="sxs-lookup"><span data-stu-id="3daa1-110">[`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) supports Cylinder, Plane, Sphere, Radial surface types</span></span>
- <span data-ttu-id="3daa1-111">[`ScatterObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.ScatterObjectCollection) prend en charge la collection de styles éparpillés</span><span class="sxs-lookup"><span data-stu-id="3daa1-111">[`ScatterObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.ScatterObjectCollection) supports scattered style collection</span></span>  
- <span data-ttu-id="3daa1-112">[`TileGridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.TileGridObjectCollection) fournit des options supplémentaires à GridObjectCollection.</span><span class="sxs-lookup"><span data-stu-id="3daa1-112">[`TileGridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.TileGridObjectCollection) provides some additional options to GridObjectCollection.</span></span> <span data-ttu-id="3daa1-113">**Remarque :** TileGridObjectCollection ne s’étend pas [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) et a plusieurs bogues (voir le [problème 6237](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6237)).</span><span class="sxs-lookup"><span data-stu-id="3daa1-113">**Note:** TileGridObjectCollection does not extend [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection), and has several bugs (see [issue 6237](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6237)).</span></span> <span data-ttu-id="3daa1-114">Par conséquent, il est recommandé d’utiliser [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) .</span><span class="sxs-lookup"><span data-stu-id="3daa1-114">Therefore, it is recommended to use [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection).</span></span>

|![Collection d’objets Grid-Cylindre](../images/object-collection/MRTK_ObjectCollectionCylinder.png) <span data-ttu-id="3daa1-116">Collection d’objets Grid-Cylindre</span><span class="sxs-lookup"><span data-stu-id="3daa1-116">Grid Object Collection - Cylinder</span></span> | ![Collection d’objets GRID-SPHERE](../images/object-collection/MRTK_ObjectCollectionSphere.png) <span data-ttu-id="3daa1-118">Collection d’objets GRID-SPHERE</span><span class="sxs-lookup"><span data-stu-id="3daa1-118">Grid Object Collection - Sphere</span></span> |
|:--- | :--- |
|![Collection d’objets Grid-radial](../images/object-collection/MRTK_ObjectCollectionRadial.png) <span data-ttu-id="3daa1-120">Collection d’objets Grid-radial</span><span class="sxs-lookup"><span data-stu-id="3daa1-120">Grid Object Collection - Radial</span></span> | ![Collection d’objets Grid-plan](../images/object-collection/MRTK_ObjectCollectionPlane.png) <span data-ttu-id="3daa1-122">Collection d’objets Grid-plan</span><span class="sxs-lookup"><span data-stu-id="3daa1-122">Grid Object Collection - Plane</span></span> |
|![Collection d’objets éparpillés](../images/object-collection/MRTK_ObjectCollectionScattered.png) <span data-ttu-id="3daa1-124">Collection d’objets éparpillés</span><span class="sxs-lookup"><span data-stu-id="3daa1-124">Scattered Object Collection</span></span> | ![Collection d’objets de grille de mosaïques](../images/object-collection/MRTK_ObjectCollectionTileGrid.png) <span data-ttu-id="3daa1-126">Collection d’objets de grille de mosaïques</span><span class="sxs-lookup"><span data-stu-id="3daa1-126">Tile Grid Object Collection</span></span> |

## <a name="how-to-use-an-object-collection"></a><span data-ttu-id="3daa1-127">Utilisation d’une collection d’objets</span><span class="sxs-lookup"><span data-stu-id="3daa1-127">How to use an object collection</span></span>

<span data-ttu-id="3daa1-128">Pour créer un regroupement, créez un GameObject vide et affectez-lui l’un des scripts de collection d’objets.</span><span class="sxs-lookup"><span data-stu-id="3daa1-128">To create a collection, create an empty GameObject and assign one of the Object Collection scripts to it.</span></span> <span data-ttu-id="3daa1-129">Un ou plusieurs objets peuvent être ajoutés en tant qu’enfant de GameObject.</span><span class="sxs-lookup"><span data-stu-id="3daa1-129">Any object(s) can be added as a child of the GameObject.</span></span> <span data-ttu-id="3daa1-130">Une fois que vous avez fini d’ajouter des objets enfants, cliquez sur le bouton *mettre à jour la collection* dans le panneau Inspecteur pour générer la collection d’objets.</span><span class="sxs-lookup"><span data-stu-id="3daa1-130">Once finished adding child objects, click the *Update Collection* button in the inspector panel to generate the object collection.</span></span> <span data-ttu-id="3daa1-131">Les objets sont disposés dans la scène conformément aux paramètres de la collection.</span><span class="sxs-lookup"><span data-stu-id="3daa1-131">The objects will be laid out in the scene according to the collection parameters.</span></span> <span data-ttu-id="3daa1-132">La mise à jour de la collection est également accessible par le biais du code.</span><span class="sxs-lookup"><span data-stu-id="3daa1-132">Update Collection can be accessed through the code too.</span></span>

![Script de collection d’objets](../images/object-collection/MRTK_ObjectCollectionScript.png)

## <a name="gridobjectcollection-content-alignment"></a><span data-ttu-id="3daa1-134">`GridObjectCollection` alignement du contenu</span><span class="sxs-lookup"><span data-stu-id="3daa1-134">`GridObjectCollection` content alignment</span></span>

<span data-ttu-id="3daa1-135">Le contenu d’un GridObjectCollection peut être aligné pour que l’objet parent soit ancré aux sommets, au milieu et à la gauche/au centre/à droite de la collection.</span><span class="sxs-lookup"><span data-stu-id="3daa1-135">The content in a GridObjectCollection can be aligned so that the parent object is anchored to the top/middle/bottom and left/center/right of the collection.</span></span> <span data-ttu-id="3daa1-136">Utilisez la propriété **Anchor** pour spécifier l’alignement du contenu.</span><span class="sxs-lookup"><span data-stu-id="3daa1-136">Use the **anchor** property to specify content alignment.</span></span>

## <a name="gridobjectcollection-layout-order"></a><span data-ttu-id="3daa1-137">`GridObjectCollection` ordre de la disposition</span><span class="sxs-lookup"><span data-stu-id="3daa1-137">`GridObjectCollection` layout order</span></span>

<span data-ttu-id="3daa1-138">Utilisez le champ **disposition** pour spécifier l’ordre des lignes/colonnes que les enfants sont disposés :</span><span class="sxs-lookup"><span data-stu-id="3daa1-138">Use the **Layout** field to specify the row / column order that children are laid out:</span></span>

<span data-ttu-id="3daa1-139">**Colonne Then** les enfants de ligne sont d’abord disposés horizontalement (par colonne), puis verticalement (par ligne).</span><span class="sxs-lookup"><span data-stu-id="3daa1-139">**Column Then Row** - Children are first laid out by horizontally (by column), then vertically (by row).</span></span> <span data-ttu-id="3daa1-140">Utilisez la propriété **num Columns** (ou la propriété Columns dans le code) pour spécifier le nombre de colonnes dans la grille.</span><span class="sxs-lookup"><span data-stu-id="3daa1-140">Use **Num Columns** (or Columns property in code) to specify the number of columns in the grid.</span></span>

![Colonne, puis disposition de ligne](../images/object-collection/MRTK_ColumnThenRow.png)

<span data-ttu-id="3daa1-142">La **ligne Then** , les enfants de colonne sont d’abord disposés verticalement (par ligne), puis horizontalement (par colonnes).</span><span class="sxs-lookup"><span data-stu-id="3daa1-142">**Row Then Column** - Children are first laid out vertically (by row), then horizontally (by columns).</span></span> <span data-ttu-id="3daa1-143">Utilisez la propriété **num Rows** (ou la propriété Rows dans le code) pour spécifier le nombre de lignes dans la grille.</span><span class="sxs-lookup"><span data-stu-id="3daa1-143">Use **Num Rows** (or Rows property in code) to specify the number of rows in the grid.</span></span>

![Ligne, puis disposition des colonnes](../images/object-collection/MRTK_RowThenColumn.png)

<span data-ttu-id="3daa1-145">Les enfants **horizontaux** sont disposés sur une seule ligne à l’aide de colonnes uniquement</span><span class="sxs-lookup"><span data-stu-id="3daa1-145">**Horizontal** - Children are laid out in a single row using columns only</span></span>

<span data-ttu-id="3daa1-146">**Vertical** -les enfants sont disposés dans une seule colonne à l’aide de lignes uniquement.</span><span class="sxs-lookup"><span data-stu-id="3daa1-146">**Vertical** - Children are laid out in a single column using rows only.</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="3daa1-147">Exemples de collection d’objets</span><span class="sxs-lookup"><span data-stu-id="3daa1-147">Object collection examples</span></span>

<span data-ttu-id="3daa1-148">L' `ObjectCollectionExamples` exemple de scène (ressources/MRTK/exemples/démonstrations/UX/Collections/scènes/ObjectCollectionExamples. Unity) contient plusieurs exemples de types de collections d’objets.</span><span class="sxs-lookup"><span data-stu-id="3daa1-148">The `ObjectCollectionExamples` (Assets/MRTK/Examples/Demos/UX/Collections/Scenes/ObjectCollectionExamples.unity) example scene contains various examples of object collection types.</span></span>

<span data-ttu-id="3daa1-149">[La table périodique des éléments](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) est un exemple d’application qui illustre le fonctionnement des collections d’objets.</span><span class="sxs-lookup"><span data-stu-id="3daa1-149">[Periodic table of the elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is an example app that demonstrates how object collections work.</span></span> <span data-ttu-id="3daa1-150">Elle utilise la collection d’objets pour mettre en forme les zones d’élément 3D dans différentes formes.</span><span class="sxs-lookup"><span data-stu-id="3daa1-150">It uses object collection to layout the 3D element boxes in different shapes.</span></span>

## <a name="object-collection-types"></a><span data-ttu-id="3daa1-151">Types de collections d’objets</span><span class="sxs-lookup"><span data-stu-id="3daa1-151">Object collection types</span></span>

<span data-ttu-id="3daa1-152">**objets 3D**</span><span class="sxs-lookup"><span data-stu-id="3daa1-152">**3D objects**</span></span>

<span data-ttu-id="3daa1-153">Une collection d’objets peut être utilisée pour mettre en forme des objets 3D importés.</span><span class="sxs-lookup"><span data-stu-id="3daa1-153">An object collection can be used to layout imported 3D objects.</span></span> <span data-ttu-id="3daa1-154">L’exemple ci-dessous montre les dispositions planes et cylindriques des objets du modèle de chaise 3D à l’aide d’une collection.</span><span class="sxs-lookup"><span data-stu-id="3daa1-154">The example below shows the plane and cylindrical layouts of 3D chair model objects using a collection.</span></span>

![Collection d’objets 3D](../images/object-collection/MRTK_ObjectCollection_3DObjects.jpg)

<span data-ttu-id="3daa1-156">**Objets 2D**</span><span class="sxs-lookup"><span data-stu-id="3daa1-156">**2D Objects**</span></span>

<span data-ttu-id="3daa1-157">Une collection d’objets peut également être créé à partir d’images 2D.</span><span class="sxs-lookup"><span data-stu-id="3daa1-157">An object collection can also be crated from 2D images.</span></span> <span data-ttu-id="3daa1-158">Par exemple, plusieurs images peuvent être placées dans un style de grille.</span><span class="sxs-lookup"><span data-stu-id="3daa1-158">For example, multiple images can be placed in a grid style.</span></span>

![Collection d’objets 2D](../images/object-collection/MRTK_ObjectCollection_Layout_2DImages.jpg)
