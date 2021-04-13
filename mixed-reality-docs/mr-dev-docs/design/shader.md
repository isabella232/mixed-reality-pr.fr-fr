---
title: Nuanceur
description: Découvrez comment le nuanceur de la norme mixte de la réalité fournit différents types d’effets visuels qui peuvent être utilisés avec des hologrammes dans vos applications de réalité mixte.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Réalité mixte, contrôles, interaction, interface utilisateur, expérience utilisateur, nuanceur, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, HoloLens, MRTK, boîte à outils de réalité mixte, effets visuels
ms.openlocfilehash: 4bf8205ac9dfbd22a0deb9ffe796fd4e33a96f89
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300384"
---
# <a name="shader"></a><span data-ttu-id="5c51f-104">Nuanceur</span><span class="sxs-lookup"><span data-stu-id="5c51f-104">Shader</span></span>

![Nuanceur](images/UX_Hero_StandardShader.jpg)

<span data-ttu-id="5c51f-106">Étant donné que les objets holographiques sont mélangés à des objets physiques dans l’environnement réel, il est important de fournir des signaux visuels à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5c51f-106">Since holographic objects are mixed with physical ones in the real environment, it's important to provide visual cues to the user.</span></span> <span data-ttu-id="5c51f-107">Le nuanceur de la réalité mixte standard fournit différents types d’effets visuels pour une utilisation avec des hologrammes.</span><span class="sxs-lookup"><span data-stu-id="5c51f-107">The Mixed Reality Toolkit Standard shader provides various types of visual effects for use with holograms.</span></span> <span data-ttu-id="5c51f-108">Le système d’ombrage utilise un nuanceur unique et flexible pour obtenir des éléments visuels similaires au nuanceur standard Unity.</span><span class="sxs-lookup"><span data-stu-id="5c51f-108">The shading system uses a single, flexible shader to achieve visuals similar to Unity's Standard Shader.</span></span> <span data-ttu-id="5c51f-109">Le nuanceur implémente les [principes du système de conception Fluent](https://www.microsoft.com/design/fluent/#/) et reste performant sur les appareils de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="5c51f-109">The shader implements [Fluent Design System principles](https://www.microsoft.com/design/fluent/#/) and remains performant on mixed reality devices.</span></span>
<br>

## <a name="examples-of-visual-effects-using-mrtk-mixed-reality-toolkit-standard-shader"></a><span data-ttu-id="5c51f-110">Exemples d’effets visuels à l’aide du nuanceur standard MRTK (Mixed Reality Toolkit)</span><span class="sxs-lookup"><span data-stu-id="5c51f-110">Examples of visual effects using MRTK (Mixed Reality Toolkit) Standard shader</span></span> 
:::row:::
    :::column:::
       <span data-ttu-id="5c51f-111">![Déplacer](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="5c51f-111">![Move](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="5c51f-112">**Lumière de proximité**</span><span class="sxs-lookup"><span data-stu-id="5c51f-112">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="5c51f-113">![Faire pivoter](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="5c51f-113">![Rotate](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="5c51f-114">**Bordure claire**</span><span class="sxs-lookup"><span data-stu-id="5c51f-114">**Border light**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="standard-shader-in-mrtk-for-unity"></a><span data-ttu-id="5c51f-115">Nuanceur standard dans MRTK pour Unity</span><span class="sxs-lookup"><span data-stu-id="5c51f-115">Standard shader in MRTK for Unity</span></span>

* [<span data-ttu-id="5c51f-116">MRTK-nuanceur standard</span><span class="sxs-lookup"><span data-stu-id="5c51f-116">MRTK - Standard shader</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)

<br>

---

## <a name="see-also"></a><span data-ttu-id="5c51f-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c51f-117">See also</span></span>

* [<span data-ttu-id="5c51f-118">Curseurs</span><span class="sxs-lookup"><span data-stu-id="5c51f-118">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="5c51f-119">Rayon émanant de la main</span><span class="sxs-lookup"><span data-stu-id="5c51f-119">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="5c51f-120">Button</span><span class="sxs-lookup"><span data-stu-id="5c51f-120">Button</span></span>](button.md)
* [<span data-ttu-id="5c51f-121">Objet avec interaction possible</span><span class="sxs-lookup"><span data-stu-id="5c51f-121">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="5c51f-122">Rectangle englobant et barre de l’application</span><span class="sxs-lookup"><span data-stu-id="5c51f-122">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="5c51f-123">Manipulation</span><span class="sxs-lookup"><span data-stu-id="5c51f-123">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="5c51f-124">Menu de la main</span><span class="sxs-lookup"><span data-stu-id="5c51f-124">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="5c51f-125">Menu proche</span><span class="sxs-lookup"><span data-stu-id="5c51f-125">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="5c51f-126">Collection d’objets</span><span class="sxs-lookup"><span data-stu-id="5c51f-126">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="5c51f-127">Commande vocale</span><span class="sxs-lookup"><span data-stu-id="5c51f-127">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="5c51f-128">Clavier</span><span class="sxs-lookup"><span data-stu-id="5c51f-128">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="5c51f-129">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="5c51f-129">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="5c51f-130">Tablette</span><span class="sxs-lookup"><span data-stu-id="5c51f-130">Slate</span></span>](slate.md)
* [<span data-ttu-id="5c51f-131">Curseur</span><span class="sxs-lookup"><span data-stu-id="5c51f-131">Slider</span></span>](slider.md)
* [<span data-ttu-id="5c51f-132">Billboarding et tag-along</span><span class="sxs-lookup"><span data-stu-id="5c51f-132">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="5c51f-133">Affichage de la progression</span><span class="sxs-lookup"><span data-stu-id="5c51f-133">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="5c51f-134">Aimantation de surface</span><span class="sxs-lookup"><span data-stu-id="5c51f-134">Surface magnetism</span></span>](surface-magnetism.md)
