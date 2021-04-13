---
title: Collection d’objets
description: La collection d’objets est un contrôle de disposition qui vous permet de disposer un tableau d’objets dans une forme à trois dimensions prédéfinie.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, contrôles, conception, casque de la réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle, HoloLens, collection d’objets, 2D, 3D, MRTK, kit de pratiques de réalité mixte
ms.openlocfilehash: 109dcd59a2b52a8eec82096c5aa88cd1070f5649
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107299724"
---
# <a name="object-collection"></a><span data-ttu-id="17ae0-104">Collection d’objets</span><span class="sxs-lookup"><span data-stu-id="17ae0-104">Object collection</span></span>

![Collection d’objets utilisée dans la table périodique de l’application d’éléments](images/UX_Hero_ObjectCollection.jpg)<br>

<span data-ttu-id="17ae0-106">La collection d’objets est un contrôle de disposition qui vous permet de disposer un tableau d’objets dans une forme à trois dimensions prédéfinie.</span><span class="sxs-lookup"><span data-stu-id="17ae0-106">Object collection is a layout control, which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="17ae0-107">Il prend en charge différents styles de surface-\* \* plan, cylindre, sphère et **radial**.</span><span class="sxs-lookup"><span data-stu-id="17ae0-107">It supports various surface styles - \*\*plane, cylinder, sphere, and **radial**.</span></span> <span data-ttu-id="17ae0-108">Vous pouvez ajuster le rayon et la taille des objets, ainsi que l’espace entre eux.</span><span class="sxs-lookup"><span data-stu-id="17ae0-108">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="17ae0-109">La collection d’objets prend en charge n’importe quel objet d’Unity, à la fois 2D et 3D.</span><span class="sxs-lookup"><span data-stu-id="17ae0-109">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="17ae0-110">Dans la **[boîte à outils de la réalité mixte](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, nous avons créé un script Unity et des exemples qui vous aideront à créer une collection d’objets.</span><span class="sxs-lookup"><span data-stu-id="17ae0-110">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, we have created Unity script and examples that will help you create an object collection.</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="17ae0-111">Exemples de collection d’objets</span><span class="sxs-lookup"><span data-stu-id="17ae0-111">Object collection examples</span></span>

<span data-ttu-id="17ae0-112">[La table périodique des éléments](../develop/unity/periodic-table-of-the-elements.md) est un exemple d’application qui illustre le fonctionnement de la collection d’objets.</span><span class="sxs-lookup"><span data-stu-id="17ae0-112">[Periodic Table of the Elements](../develop/unity/periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="17ae0-113">Elle utilise la collection d’objets pour disposer les zones d’éléments chimiques 3D dans différentes formes.</span><span class="sxs-lookup"><span data-stu-id="17ae0-113">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="17ae0-114">![Exemples de collection d’objets affichés dans la table periode de l’application Elements](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="17ae0-114">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="17ae0-115">*Exemples de collection d’objets affichés dans la table periode de l’exemple d’application d’éléments*</span><span class="sxs-lookup"><span data-stu-id="17ae0-115">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="17ae0-116">objets 3D</span><span class="sxs-lookup"><span data-stu-id="17ae0-116">3D objects</span></span>

<span data-ttu-id="17ae0-117">Vous pouvez utiliser la collection d’objets pour disposer les objets 3D importés.</span><span class="sxs-lookup"><span data-stu-id="17ae0-117">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="17ae0-118">L’exemple ci-dessous montre un plan et une disposition cylindrique de certains objets de chaise 3D.</span><span class="sxs-lookup"><span data-stu-id="17ae0-118">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="17ae0-119">![Exemples de dispositions planes et cylindriques d’objets 3D](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="17ae0-119">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="17ae0-120">*Exemples de dispositions planes et cylindriques d’objets 3D*</span><span class="sxs-lookup"><span data-stu-id="17ae0-120">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="17ae0-121">objets 2D</span><span class="sxs-lookup"><span data-stu-id="17ae0-121">2D objects</span></span>

<span data-ttu-id="17ae0-122">Vous pouvez également utiliser des images 2D avec la collection d’objets.</span><span class="sxs-lookup"><span data-stu-id="17ae0-122">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="17ae0-123">Les exemples ci-dessous montrent comment les images 2D peuvent être affichées dans une grille.</span><span class="sxs-lookup"><span data-stu-id="17ae0-123">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![Exemple d’images 2D avec la collection d’objets](images/940px-layout-3dobjects-3.jpg)

<span data-ttu-id="17ae0-125">![Exemples d’utilisation de la collection d’objets avec des images 2D](images/940px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="17ae0-125">![Examples of using object collection with 2D images](images/940px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="17ae0-126">*Exemples d’utilisation de la collection d’objets avec des images 2D*</span><span class="sxs-lookup"><span data-stu-id="17ae0-126">*Examples of using object collection with 2D images*</span></span>

<br>

---

## <a name="object-collection-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="17ae0-127">Collection d’objets dans MRTK (Mixed Reality Toolkit) pour Unity</span><span class="sxs-lookup"><span data-stu-id="17ae0-127">Object collection in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="17ae0-128">MRTK-collection d’objets</span><span class="sxs-lookup"><span data-stu-id="17ae0-128">MRTK - Object collection</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection)

<br>

---

## <a name="see-also"></a><span data-ttu-id="17ae0-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17ae0-129">See also</span></span>

* [<span data-ttu-id="17ae0-130">Curseurs</span><span class="sxs-lookup"><span data-stu-id="17ae0-130">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="17ae0-131">Rayon émanant de la main</span><span class="sxs-lookup"><span data-stu-id="17ae0-131">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="17ae0-132">Button</span><span class="sxs-lookup"><span data-stu-id="17ae0-132">Button</span></span>](button.md)
* [<span data-ttu-id="17ae0-133">Objet avec interaction possible</span><span class="sxs-lookup"><span data-stu-id="17ae0-133">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="17ae0-134">Rectangle englobant et barre de l’application</span><span class="sxs-lookup"><span data-stu-id="17ae0-134">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="17ae0-135">Manipulation</span><span class="sxs-lookup"><span data-stu-id="17ae0-135">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="17ae0-136">Menu de la main</span><span class="sxs-lookup"><span data-stu-id="17ae0-136">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="17ae0-137">Menu proche</span><span class="sxs-lookup"><span data-stu-id="17ae0-137">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="17ae0-138">Collection d’objets</span><span class="sxs-lookup"><span data-stu-id="17ae0-138">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="17ae0-139">Commande vocale</span><span class="sxs-lookup"><span data-stu-id="17ae0-139">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="17ae0-140">Clavier</span><span class="sxs-lookup"><span data-stu-id="17ae0-140">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="17ae0-141">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="17ae0-141">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="17ae0-142">Tablette</span><span class="sxs-lookup"><span data-stu-id="17ae0-142">Slate</span></span>](slate.md)
* [<span data-ttu-id="17ae0-143">Curseur</span><span class="sxs-lookup"><span data-stu-id="17ae0-143">Slider</span></span>](slider.md)
* [<span data-ttu-id="17ae0-144">Nuanceur</span><span class="sxs-lookup"><span data-stu-id="17ae0-144">Shader</span></span>](shader.md)
* [<span data-ttu-id="17ae0-145">Billboarding et tag-along</span><span class="sxs-lookup"><span data-stu-id="17ae0-145">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="17ae0-146">Affichage de la progression</span><span class="sxs-lookup"><span data-stu-id="17ae0-146">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="17ae0-147">Aimantation de surface</span><span class="sxs-lookup"><span data-stu-id="17ae0-147">Surface magnetism</span></span>](surface-magnetism.md)
