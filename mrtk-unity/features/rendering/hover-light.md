---
title: Pointage
description: Documentation sur HoverLight avec des exemples dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, lumière de survol,
ms.openlocfilehash: ed45d3345931376283cfca2372ac57459c777f6e
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176731"
---
# <a name="hover-light"></a><span data-ttu-id="2f8e5-104">Pointage</span><span class="sxs-lookup"><span data-stu-id="2f8e5-104">Hover light</span></span>

<span data-ttu-id="2f8e5-105">un [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) est un paradigme de [Système Fluent Design](https://www.microsoft.com/design/fluent/) qui imite une [lumière de pointage](https://docs.unity3d.com/Manual/Lighting.html) près de la surface d’un objet.</span><span class="sxs-lookup"><span data-stu-id="2f8e5-105">A [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) is a [Fluent Design System](https://www.microsoft.com/design/fluent/) paradigm that mimics a [point light](https://docs.unity3d.com/Manual/Lighting.html) hovering near the surface of an object.</span></span> <span data-ttu-id="2f8e5-106">Souvent utilisées pour les interactions éloignées, l’application peut contrôler les propriétés d’une lumière de survol via le [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) composant.</span><span class="sxs-lookup"><span data-stu-id="2f8e5-106">Often used for far away interactions, the application can control the properties of a Hover Light via the [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) component.</span></span>

<span data-ttu-id="2f8e5-107">pour qu’une matière soit influencée par [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) une *réalité mixte Shared Computer Toolkit* nuanceur/d’doit être utilisé et la propriété *Light sensitive* doit être activée.</span><span class="sxs-lookup"><span data-stu-id="2f8e5-107">For a material to be influenced by a [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) the *Mixed Reality Toolkit/Standard* shader must be used and the *Hover Light* property must be enabled.</span></span>

> [!Note]
> <span data-ttu-id="2f8e5-108">Le nuanceur MRTK/standard prend en charge un maximum de deux [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) par défaut, mais il est mis à l’échelle pour prendre en charge quatre, puis 10 à mesure que d’autres lumières sont ajoutées à la scène.</span><span class="sxs-lookup"><span data-stu-id="2f8e5-108">The MRTK/Standard shader supports up to two [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) by default, but will scale to support four and then ten as more lights are added to the scene.</span></span>

## <a name="examples"></a><span data-ttu-id="2f8e5-109">Exemples</span><span class="sxs-lookup"><span data-stu-id="2f8e5-109">Examples</span></span>

<span data-ttu-id="2f8e5-110">La plupart des scènes dans le MRTK utilisent un [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) .</span><span class="sxs-lookup"><span data-stu-id="2f8e5-110">Most scenes within the MRTK utilize a [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight).</span></span> <span data-ttu-id="2f8e5-111">Le cas d’utilisation le plus courant se trouve dans MRTK/SDK/features/UX/Prefabs/Cursors/DefaultCursor. Prefab</span><span class="sxs-lookup"><span data-stu-id="2f8e5-111">The most common use case can be found on the MRTK/SDK/Features/UX/Prefabs/Cursors/DefaultCursor.prefab</span></span>

<span data-ttu-id="2f8e5-112">La scène **HoverLightExamples** illustre également l’utilisation des [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) comportements et se trouve à l’adresse suivante : MRTK/examples/démos/StandardShader/scènes/</span><span class="sxs-lookup"><span data-stu-id="2f8e5-112">The **HoverLightExamples** scene also demonstrates usage of [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) behaviors, and can be found at: MRTK/Examples/Demos/StandardShader/Scenes/</span></span>

## <a name="advanced-usage"></a><span data-ttu-id="2f8e5-113">Utilisation avancée</span><span class="sxs-lookup"><span data-stu-id="2f8e5-113">Advanced Usage</span></span>

<span data-ttu-id="2f8e5-114">Seules dix [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) peuvent éclairer un [matériau](https://docs.unity3d.com/ScriptReference/Material.html) à la fois.</span><span class="sxs-lookup"><span data-stu-id="2f8e5-114">Only ten [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) can illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) at a time.</span></span> <span data-ttu-id="2f8e5-115">Si votre projet nécessite plus de dix [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) pour influencer un [matériau](https://docs.unity3d.com/ScriptReference/Material.html) , l’exemple de code ci-dessous montre comment y parvenir.</span><span class="sxs-lookup"><span data-stu-id="2f8e5-115">If your project requires more than ten [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) to influence a [material](https://docs.unity3d.com/ScriptReference/Material.html) the sample code below demonstrates how to achieve this.</span></span>

> [!Note]
> <span data-ttu-id="2f8e5-116">Si vous avez beaucoup [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) d’éclairage, un [matériau](https://docs.unity3d.com/ScriptReference/Material.html) augmentera les instructions de nuanceur de pixels et aura un impact sur les performances.</span><span class="sxs-lookup"><span data-stu-id="2f8e5-116">Having many [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) will increase pixel shader instructions and will impact performance.</span></span> <span data-ttu-id="2f8e5-117">**Profilez ces modifications dans votre projet.**</span><span class="sxs-lookup"><span data-stu-id="2f8e5-117">**Please profile these changes within your project.**</span></span>

<span data-ttu-id="2f8e5-118">*Comment augmenter le nombre de disponibles [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) de 10 à 12.*</span><span class="sxs-lookup"><span data-stu-id="2f8e5-118">*How to increase the number of available [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) from ten to twelve.*</span></span>

```C#
// 1) Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader change:

#if defined(_HOVER_LIGHT_HIGH)
#define HOVER_LIGHT_COUNT 10

// to:

#if defined(_HOVER_LIGHT_HIGH)
#define HOVER_LIGHT_COUNT 12

// 2) Within MRTK/Core/Utilities/StandardShader/HoverLight.cs change:

private const int hoverLightCountHigh = 10;

// to:

private const int hoverLightCountHigh = 12;
```

> [!NOTE]
> <span data-ttu-id="2f8e5-119">Si Unity enregistre un avertissement similaire à celui ci-dessous, vous devez redémarrer Unity pour que vos modifications soient prises en compte.</span><span class="sxs-lookup"><span data-stu-id="2f8e5-119">If Unity logs a warning similar to below then you must restart Unity before your changes will take effect.</span></span>
>
> `Property (_HoverLightData) exceeds previous array size (24 vs 20). Cap to previous >size.`

## <a name="see-also"></a><span data-ttu-id="2f8e5-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f8e5-120">See also</span></span>

* [<span data-ttu-id="2f8e5-121">Nuanceur standard MRTK</span><span class="sxs-lookup"><span data-stu-id="2f8e5-121">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)
