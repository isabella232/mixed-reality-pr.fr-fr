---
title: Menu proche
description: Vue d’ensemble des types de menus proches dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, Menu proche,
ms.openlocfilehash: 15f53ad4e67a0b281750fd1df7f894c49f546531
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175649"
---
# <a name="near-menu"></a><span data-ttu-id="02781-104">Menu proche</span><span class="sxs-lookup"><span data-stu-id="02781-104">Near menu</span></span>

![Menu Proximité](../images/near-menu/MRTK_UX_NearMenu.png)

<span data-ttu-id="02781-106">Le menu proche est un contrôle d’expérience utilisateur qui fournit une collection de boutons ou d’autres composants d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="02781-106">Near Menu is a UX control which provides a collection of buttons or other UI components.</span></span> <span data-ttu-id="02781-107">Il est flottant autour du corps de l’utilisateur et facilement accessible à tout moment.</span><span class="sxs-lookup"><span data-stu-id="02781-107">It is floating around the user's body and easily accessible anytime.</span></span> <span data-ttu-id="02781-108">Étant donné qu’elle est faiblement couplée avec l’utilisateur, elle ne perturbe pas l’interaction de l’utilisateur avec le contenu cible.</span><span class="sxs-lookup"><span data-stu-id="02781-108">Since it is loosely coupled with the user, it does not disturb the user's interaction with the target content.</span></span> <span data-ttu-id="02781-109">L’utilisateur peut utiliser le bouton « épingler » pour verrouiller/déverrouiller le menu.</span><span class="sxs-lookup"><span data-stu-id="02781-109">The user can use the 'Pin' button to world-lock/unlock the menu.</span></span> <span data-ttu-id="02781-110">Le menu peut être retiré et placé à une position spécifique.</span><span class="sxs-lookup"><span data-stu-id="02781-110">The menu can be grabbed and placed at a specific position.</span></span>

## <a name="interaction-behavior"></a><span data-ttu-id="02781-111">Comportement d’interaction</span><span class="sxs-lookup"><span data-stu-id="02781-111">Interaction behavior</span></span>

- <span data-ttu-id="02781-112">**Balise**: le menu vous suit et reste dans la plage de 30 60cm de l’utilisateur pour les interactions proches.</span><span class="sxs-lookup"><span data-stu-id="02781-112">**Tag-along**: The menu follows you and stays within 30-60cm range from the user for the near interactions.</span></span>
- <span data-ttu-id="02781-113">**Pin**: à l’aide du bouton « épingler », le menu peut être verrouillé et relâché.</span><span class="sxs-lookup"><span data-stu-id="02781-113">**Pin**: Using the 'Pin' button, the menu can be world-locked and released.</span></span>
- <span data-ttu-id="02781-114">**Manipulation et déplacement**: le menu est toujours pouvant être retiré et déplaçable.</span><span class="sxs-lookup"><span data-stu-id="02781-114">**Grab and move**: The menu is always grabbable and movable.</span></span> <span data-ttu-id="02781-115">Quel que soit l’état précédent, le menu est épinglé (verrouillage universel) lorsqu’il est retiré et relâché.</span><span class="sxs-lookup"><span data-stu-id="02781-115">Regardless of the previous state, the menu will be pinned(world-locked) when grabbed and released.</span></span> <span data-ttu-id="02781-116">Il existe des signaux visuels pour la zone qui peut être saisie.</span><span class="sxs-lookup"><span data-stu-id="02781-116">There are visual cues for the grabbable area.</span></span> <span data-ttu-id="02781-117">Ils sont révélés à proximité.</span><span class="sxs-lookup"><span data-stu-id="02781-117">They are revealed on hand proximity.</span></span>

<img src="../images/near-menu/MRTK_UX_NearMenu_Grab.png" alt="Near Menu grab">

## <a name="prefabs"></a><span data-ttu-id="02781-118">Prefabs</span><span class="sxs-lookup"><span data-stu-id="02781-118">Prefabs</span></span>

<span data-ttu-id="02781-119">Le menu prefabs est conçu pour illustrer l’utilisation de divers composants de MRTK pour générer des menus pour les interactions proches.</span><span class="sxs-lookup"><span data-stu-id="02781-119">Near Menu prefabs are designed to demonstrate how to use MRTK's various components to build menus for near interactions.</span></span>

- <span data-ttu-id="02781-120">**NearMenu2x4. Prefab**</span><span class="sxs-lookup"><span data-stu-id="02781-120">**NearMenu2x4.prefab**</span></span>
- <span data-ttu-id="02781-121">**NearMenu3x1. Prefab**</span><span class="sxs-lookup"><span data-stu-id="02781-121">**NearMenu3x1.prefab**</span></span>
- <span data-ttu-id="02781-122">**NearMenu3x2. Prefab**</span><span class="sxs-lookup"><span data-stu-id="02781-122">**NearMenu3x2.prefab**</span></span>
- <span data-ttu-id="02781-123">**NearMenu3x3. Prefab**</span><span class="sxs-lookup"><span data-stu-id="02781-123">**NearMenu3x3.prefab**</span></span>
- <span data-ttu-id="02781-124">**NearMenu4x1. Prefab**</span><span class="sxs-lookup"><span data-stu-id="02781-124">**NearMenu4x1.prefab**</span></span>
- <span data-ttu-id="02781-125">**NearMenu4x2. Prefab**</span><span class="sxs-lookup"><span data-stu-id="02781-125">**NearMenu4x2.prefab**</span></span>

## <a name="example-scene"></a><span data-ttu-id="02781-126">Exemple de scène</span><span class="sxs-lookup"><span data-stu-id="02781-126">Example scene</span></span>

<span data-ttu-id="02781-127">Vous trouverez des exemples de prefabs dans la `NearMenuExamples` scène.</span><span class="sxs-lookup"><span data-stu-id="02781-127">You can find examples of Near Menu prefabs in the `NearMenuExamples` scene.</span></span>

<img src="../images/near-menu/MRTK_UX_NearMenu_Examples.png" alt="Near Menu Example">

## <a name="structure"></a><span data-ttu-id="02781-128">Structure</span><span class="sxs-lookup"><span data-stu-id="02781-128">Structure</span></span>

<span data-ttu-id="02781-129">Les prefabs des menus proches sont créés avec les composants MRTK suivants.</span><span class="sxs-lookup"><span data-stu-id="02781-129">Near Menu prefabs are made with following MRTK components.</span></span>

- <span data-ttu-id="02781-130">[**PressableButtonHoloLens2**](button.md) Prefab</span><span class="sxs-lookup"><span data-stu-id="02781-130">[**PressableButtonHoloLens2**](button.md) prefab</span></span>
- <span data-ttu-id="02781-131">[**Collection d’objets Grid**](object-collection.md): disposition à plusieurs boutons dans la grille</span><span class="sxs-lookup"><span data-stu-id="02781-131">[**Grid Object Collection**](object-collection.md): Multiple button layout in grid</span></span>
- <span data-ttu-id="02781-132">[**Gestionnaire de manipulation**](manipulation-handler.md): récupérer et déplacer le menu</span><span class="sxs-lookup"><span data-stu-id="02781-132">[**Manipulation Handler**](manipulation-handler.md): Grab and move the menu</span></span>
- <span data-ttu-id="02781-133">[**Solveur RadialView**](solvers/solver.md): suivre le comportement (balise)</span><span class="sxs-lookup"><span data-stu-id="02781-133">[**RadialView Solver**](solvers/solver.md): Follow Me(tag-along) behavior</span></span>

![Près du menu Prefab](../images/near-menu/MRTK_UX_NearMenu_Structure.png)

## <a name="how-to-customize"></a><span data-ttu-id="02781-135">Comment personnaliser</span><span class="sxs-lookup"><span data-stu-id="02781-135">How to customize</span></span>

<span data-ttu-id="02781-136">**1. Ajouter/supprimer des boutons**</span><span class="sxs-lookup"><span data-stu-id="02781-136">**1. Add/Remove Buttons**</span></span>

<span data-ttu-id="02781-137">Sous `ButtonCollection` objet, ajoutez ou supprimez des boutons.</span><span class="sxs-lookup"><span data-stu-id="02781-137">Under `ButtonCollection` object, add or remove buttons.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom0.png" width="450" alt="Near Menu Custome 0">

<span data-ttu-id="02781-138">**2. mettre à jour la collection d’objets Grid**</span><span class="sxs-lookup"><span data-stu-id="02781-138">**2. Update the Grid Object Collection**</span></span>

<span data-ttu-id="02781-139">Cliquez sur `Update Collection` le bouton dans l’inspecteur de l' `ButtonCollection` objet.</span><span class="sxs-lookup"><span data-stu-id="02781-139">Click `Update Collection` button in the Inspector of the `ButtonCollection` object.</span></span> <span data-ttu-id="02781-140">Elle met à jour la disposition de grille.</span><span class="sxs-lookup"><span data-stu-id="02781-140">It will update the grid layout.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom1.png" alt="Near Menu Custome 1">

<span data-ttu-id="02781-141">Vous pouvez configurer le nombre de lignes à l’aide `Rows` de la propriété de la collection d’objets Grid.</span><span class="sxs-lookup"><span data-stu-id="02781-141">You can configure the number of rows using `Rows` property of the Grid Object Collection.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom2.png" alt="Near Menu Custome 2">

<span data-ttu-id="02781-142">**3. ajuster la taille de la plaque**</span><span class="sxs-lookup"><span data-stu-id="02781-142">**3. Adjust the backplate size**</span></span>

<span data-ttu-id="02781-143">Ajustez la taille du `Quad` sous- `Backplate` objet.</span><span class="sxs-lookup"><span data-stu-id="02781-143">Adjust the size of the `Quad` under `Backplate` object.</span></span> <span data-ttu-id="02781-144">La largeur et la hauteur de l’arrière-plaque doivent être `0.032 * [Number of the buttons + 1]` .</span><span class="sxs-lookup"><span data-stu-id="02781-144">The width and height of the backplate should be `0.032 * [Number of the buttons + 1]`.</span></span> <span data-ttu-id="02781-145">Par exemple, si vous avez 3 boutons x 2, la largeur de l’arrière-plaque est `0.032 * 4` et la hauteur est `0.032 * 3` .</span><span class="sxs-lookup"><span data-stu-id="02781-145">For example, if you have 3 x 2 buttons, the width of the backplate is `0.032 * 4` and the height is `0.032 * 3`.</span></span> <span data-ttu-id="02781-146">Vous pouvez placer cette expression directement dans le champ Unity.</span><span class="sxs-lookup"><span data-stu-id="02781-146">You can directly put this expression into the Unity's field.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom3.png" width="450" alt="Near Menu Custome 3">

- <span data-ttu-id="02781-147">la taille par défaut du bouton HoloLens 2 est 3,2 x 3,2 cm (0.032 m)</span><span class="sxs-lookup"><span data-stu-id="02781-147">Default size of the HoloLens 2 button is 3.2x3.2 cm (0.032m)</span></span>

## <a name="see-also"></a><span data-ttu-id="02781-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02781-148">See also</span></span>

- [<span data-ttu-id="02781-149">**Boutons**</span><span class="sxs-lookup"><span data-stu-id="02781-149">**Buttons**</span></span>](button.md)
- [<span data-ttu-id="02781-150">**Contrôle des limites**</span><span class="sxs-lookup"><span data-stu-id="02781-150">**Bounds Control**</span></span>](bounds-control.md)
- [<span data-ttu-id="02781-151">**Curseur**</span><span class="sxs-lookup"><span data-stu-id="02781-151">**Slider**</span></span>](sliders.md)
- [<span data-ttu-id="02781-152">**Collection d’objets Grid**</span><span class="sxs-lookup"><span data-stu-id="02781-152">**Grid Object Collection**</span></span>](object-collection.md)
- [<span data-ttu-id="02781-153">**Gestionnaire de manipulation**</span><span class="sxs-lookup"><span data-stu-id="02781-153">**Manipulation Handler**</span></span>](manipulation-handler.md)
- [<span data-ttu-id="02781-154">**Solveur RadialView**</span><span class="sxs-lookup"><span data-stu-id="02781-154">**RadialView Solver**</span></span>](solvers/solver.md)
