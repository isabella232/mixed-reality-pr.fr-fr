---
title: Bouton
description: Découvrez comment déclencher une action immédiate avec des boutons, qui est l’un des composants fondamentaux de la réalité mixte.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Réalité mixte, contrôles, interaction, interface utilisateur, expérience utilisateur, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, HoloLens, MRTK, boîte à outils de réalité mixte, bouton
ms.openlocfilehash: b4e8388c4e3ea855c191cbdfc06621018274ff86
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847591"
---
# <a name="button"></a><span data-ttu-id="5863d-104">Button</span><span class="sxs-lookup"><span data-stu-id="5863d-104">Button</span></span>

![Button](images/UX_Hero_Button.jpg)

<span data-ttu-id="5863d-106">Un bouton permet à vos utilisateurs de déclencher des actions immédiates dans une expérience de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="5863d-106">A button lets your users trigger immediate actions in a mixed reality experience.</span></span> <span data-ttu-id="5863d-107">Dans HoloLens 2, les boutons ont des signaux visuels et des intuitivité qui permettent d’accroître la confiance de l’interaction avec les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="5863d-107">In HoloLens 2, buttons have visual cues and affordances that help increase interaction confidence with users.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="5863d-108">![Bouton avec effet d’éclairage de proximité indiqué](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="5863d-108">![Button with proximity light effect shown](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="5863d-109">**Lumière de proximité**</span><span class="sxs-lookup"><span data-stu-id="5863d-109">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="5863d-110">![Bouton sélectionné avec l’effet de surbrillance Focus affiché](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="5863d-110">![Button selected with focus highlight effect shown](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="5863d-111">**Sélection du focus**</span><span class="sxs-lookup"><span data-stu-id="5863d-111">**Focus highlight**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="5863d-112">![Bouton enfoncé avec l’effet de bâti de compression affiché](images/UX_Button_Affordance_Compression.jpg)</span><span class="sxs-lookup"><span data-stu-id="5863d-112">![Button being pressed with compression cage effect shown](images/UX_Button_Affordance_Compression.jpg)</span></span><br>
       <span data-ttu-id="5863d-113">**Compression du boîtier**</span><span class="sxs-lookup"><span data-stu-id="5863d-113">**Compressing cage**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="5863d-114">![Bouton enfoncé avec l’effet d’impulsion de déclenchement affiché](images/UX_Button_Affordance_Pulse.jpg)</span><span class="sxs-lookup"><span data-stu-id="5863d-114">![Button being pressed with trigger pulse effect shown](images/UX_Button_Affordance_Pulse.jpg)</span></span><br>
        <span data-ttu-id="5863d-115">**Impulsion sur le déclencheur**</span><span class="sxs-lookup"><span data-stu-id="5863d-115">**Pulse on trigger**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="button-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="5863d-116">Bouton dans MRTK (ensemble d’outils de réalité mixte) pour Unity</span><span class="sxs-lookup"><span data-stu-id="5863d-116">Button in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="5863d-117">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fournit différents types de prefabs Button, y compris les boutons de style Shell pour hololens 2 et hololens (1re génération).</span><span class="sxs-lookup"><span data-stu-id="5863d-117">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides various types of button prefabs, including shell-style buttons for HoloLens 2 and HoloLens (1st gen).</span></span> <span data-ttu-id="5863d-118">Le bouton HoloLens 2 Prefab contient plusieurs intuitivité détaillés qui permettent d’améliorer la confiance de l’utilisateur :</span><span class="sxs-lookup"><span data-stu-id="5863d-118">The HoloLens 2 button prefab contains several detailed affordances that help improve user confidence:</span></span>

* <span data-ttu-id="5863d-119">Surbrillance basée sur la proximité</span><span class="sxs-lookup"><span data-stu-id="5863d-119">Proximity-based highlight</span></span>
* <span data-ttu-id="5863d-120">Compression de la cage avant</span><span class="sxs-lookup"><span data-stu-id="5863d-120">Compressing front cage</span></span>
* <span data-ttu-id="5863d-121">Effet d’impulsion sur le déclencheur.</span><span class="sxs-lookup"><span data-stu-id="5863d-121">Pulse effect on trigger.</span></span>

* <span data-ttu-id="5863d-122">Pour obtenir des instructions et des exemples personnalisés, consultez le [bouton MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) .</span><span class="sxs-lookup"><span data-stu-id="5863d-122">Check out the [MRTK - Button](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) for more instructions and customized examples.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="5863d-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5863d-123">See also</span></span>

* [<span data-ttu-id="5863d-124">Curseurs</span><span class="sxs-lookup"><span data-stu-id="5863d-124">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="5863d-125">Rayon émanant de la main</span><span class="sxs-lookup"><span data-stu-id="5863d-125">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="5863d-126">Button</span><span class="sxs-lookup"><span data-stu-id="5863d-126">Button</span></span>](button.md)
* [<span data-ttu-id="5863d-127">Objet avec interaction possible</span><span class="sxs-lookup"><span data-stu-id="5863d-127">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="5863d-128">Rectangle englobant et barre de l’application</span><span class="sxs-lookup"><span data-stu-id="5863d-128">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="5863d-129">Manipulation</span><span class="sxs-lookup"><span data-stu-id="5863d-129">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="5863d-130">Menu de la main</span><span class="sxs-lookup"><span data-stu-id="5863d-130">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="5863d-131">Menu proche</span><span class="sxs-lookup"><span data-stu-id="5863d-131">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="5863d-132">Collection d’objets</span><span class="sxs-lookup"><span data-stu-id="5863d-132">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="5863d-133">Commande vocale</span><span class="sxs-lookup"><span data-stu-id="5863d-133">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="5863d-134">Clavier</span><span class="sxs-lookup"><span data-stu-id="5863d-134">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="5863d-135">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="5863d-135">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="5863d-136">Tablette</span><span class="sxs-lookup"><span data-stu-id="5863d-136">Slate</span></span>](slate.md)
* [<span data-ttu-id="5863d-137">Curseur</span><span class="sxs-lookup"><span data-stu-id="5863d-137">Slider</span></span>](slider.md)
* [<span data-ttu-id="5863d-138">Nuanceur</span><span class="sxs-lookup"><span data-stu-id="5863d-138">Shader</span></span>](shader.md)
* [<span data-ttu-id="5863d-139">Billboarding et tag-along</span><span class="sxs-lookup"><span data-stu-id="5863d-139">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="5863d-140">Affichage de la progression</span><span class="sxs-lookup"><span data-stu-id="5863d-140">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="5863d-141">Aimantation de surface</span><span class="sxs-lookup"><span data-stu-id="5863d-141">Surface magnetism</span></span>](surface-magnetism.md)
