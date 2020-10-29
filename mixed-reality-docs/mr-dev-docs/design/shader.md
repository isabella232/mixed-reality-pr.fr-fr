---
title: Nuanceur
description: Le nuanceur standard MRTK fournit différents types d’effets visuels qui peuvent être utilisés avec des hologrammes.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Réalité mixte, contrôles, interaction, interface utilisateur, expérience utilisateur
ms.openlocfilehash: 86e56de93736c90f3b28467a0ecd6e18a1ba0146
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679414"
---
# <a name="shader"></a><span data-ttu-id="64e03-104">Nuanceur</span><span class="sxs-lookup"><span data-stu-id="64e03-104">Shader</span></span>

![Nuanceur](images/UX_Hero_StandardShader.jpg)

<span data-ttu-id="64e03-106">Étant donné que les objets holographiques sont mélangés à des objets physiques dans l’environnement réel, il est important de fournir des signaux visuels à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="64e03-106">Since holographic objects are mixed with physical ones in the real environment, it's important to provide visual cues to the user.</span></span> <span data-ttu-id="64e03-107">Le nuanceur standard MRTK fournit différents types d’effets visuels qui peuvent être utilisés avec des hologrammes.</span><span class="sxs-lookup"><span data-stu-id="64e03-107">The MRTK Standard shader provides various types of visual effects that can be used with holograms.</span></span> <span data-ttu-id="64e03-108">Le système d’ombrage standard MRTK utilise un nuanceur unique et flexible qui permet d’obtenir des éléments visuels similaires au nuanceur standard de Unity, d’implémenter des [principes de système de conception Fluent](https://www.microsoft.com/design/fluent/#/)et de rester performant sur des appareils de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="64e03-108">The MRTK Standard shading system utilizes a single, flexible shader that can achieve visuals similar to Unity's Standard Shader, implements [Fluent Design System principles](https://www.microsoft.com/design/fluent/#/), and remains performant on mixed reality devices.</span></span>
<br>

## <a name="examples-of-visual-effects-using-mrtk-standard-shader"></a><span data-ttu-id="64e03-109">Exemples d’effets visuels utilisant le nuanceur standard MRTK</span><span class="sxs-lookup"><span data-stu-id="64e03-109">Examples of visual effects using MRTK Standard shader</span></span> 
:::row:::
    :::column:::
       <span data-ttu-id="64e03-110">![Déplacer](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="64e03-110">![Move](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="64e03-111">**Lumière de proximité**</span><span class="sxs-lookup"><span data-stu-id="64e03-111">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="64e03-112">![Faire pivoter](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="64e03-112">![Rotate](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="64e03-113">**Bordure claire**</span><span class="sxs-lookup"><span data-stu-id="64e03-113">**Border light**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="mrtk-standard-shader-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="64e03-114">Nuanceur standard MRTK dans MRTK (Mixed Reality Toolkit) pour Unity</span><span class="sxs-lookup"><span data-stu-id="64e03-114">MRTK Standard shader in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="64e03-115">MRTK-nuanceur standard</span><span class="sxs-lookup"><span data-stu-id="64e03-115">MRTK - Standard shader</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)


<br>

---

## <a name="see-also"></a><span data-ttu-id="64e03-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="64e03-116">See also</span></span>

* [<span data-ttu-id="64e03-117">Curseurs</span><span class="sxs-lookup"><span data-stu-id="64e03-117">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="64e03-118">Rayon émanant de la main</span><span class="sxs-lookup"><span data-stu-id="64e03-118">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="64e03-119">Button</span><span class="sxs-lookup"><span data-stu-id="64e03-119">Button</span></span>](button.md)
* [<span data-ttu-id="64e03-120">Objet avec interaction possible</span><span class="sxs-lookup"><span data-stu-id="64e03-120">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="64e03-121">Rectangle englobant et barre de l’application</span><span class="sxs-lookup"><span data-stu-id="64e03-121">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="64e03-122">Manipulation</span><span class="sxs-lookup"><span data-stu-id="64e03-122">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="64e03-123">Menu de la main</span><span class="sxs-lookup"><span data-stu-id="64e03-123">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="64e03-124">Menu proche</span><span class="sxs-lookup"><span data-stu-id="64e03-124">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="64e03-125">Collection d’objets</span><span class="sxs-lookup"><span data-stu-id="64e03-125">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="64e03-126">Commande vocale</span><span class="sxs-lookup"><span data-stu-id="64e03-126">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="64e03-127">Clavier</span><span class="sxs-lookup"><span data-stu-id="64e03-127">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="64e03-128">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="64e03-128">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="64e03-129">Tablette</span><span class="sxs-lookup"><span data-stu-id="64e03-129">Slate</span></span>](slate.md)
* [<span data-ttu-id="64e03-130">Curseur</span><span class="sxs-lookup"><span data-stu-id="64e03-130">Slider</span></span>](slider.md)
* [<span data-ttu-id="64e03-131">Billboarding et tag-along</span><span class="sxs-lookup"><span data-stu-id="64e03-131">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="64e03-132">Affichage de la progression</span><span class="sxs-lookup"><span data-stu-id="64e03-132">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="64e03-133">Aimantation de surface</span><span class="sxs-lookup"><span data-stu-id="64e03-133">Surface magnetism</span></span>](surface-magnetism.md)
