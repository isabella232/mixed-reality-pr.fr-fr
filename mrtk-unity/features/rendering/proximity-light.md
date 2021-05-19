---
title: Lumière proche
description: Documentation sur la lumière de proximité avec des exemples dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 1adf4d1d70313c917d63224b91a14d995d1888c1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145000"
---
# <a name="proximity-light"></a><span data-ttu-id="7a445-104">Lumière proche</span><span class="sxs-lookup"><span data-stu-id="7a445-104">Proximity Light</span></span>

<span data-ttu-id="7a445-105">Un [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) est un paradigme de [système de conception Fluent](https://www.microsoft.com/design/fluent/) qui imite une « lumière de point inverse de dégradé » en pointant près de la surface d’un objet.</span><span class="sxs-lookup"><span data-stu-id="7a445-105">A [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) is a [Fluent Design System](https://www.microsoft.com/design/fluent/) paradigm that mimics a "gradient inverse point light" hovering near the surface of an object.</span></span> <span data-ttu-id="7a445-106">Souvent utilisé pour les interactions proches, l’application peut contrôler les propriétés d’une lumière de proximité via le [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) composant.</span><span class="sxs-lookup"><span data-stu-id="7a445-106">Often used for near interactions, the application can control the properties of a Proximity Light via the [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) component.</span></span>

<span data-ttu-id="7a445-107">Pour qu’un matériau soit influencé par un [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) nuanceur de *réalité mixte* , le nuanceur standard doit être utilisé et la propriété de *lumière de proximité* doit être activée.</span><span class="sxs-lookup"><span data-stu-id="7a445-107">For a material to be influenced by a [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) the *Mixed Reality Toolkit/Standard* shader must be used and the *Proximity Light* property must be enabled.</span></span>

> [!NOTE]
> <span data-ttu-id="7a445-108">Jusqu’à deux [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) sont pris en charge par défaut.</span><span class="sxs-lookup"><span data-stu-id="7a445-108">Up to two [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) are supported by default.</span></span>

## <a name="examples"></a><span data-ttu-id="7a445-109">Exemples</span><span class="sxs-lookup"><span data-stu-id="7a445-109">Examples</span></span>

<span data-ttu-id="7a445-110">La plupart des scènes dans le MRTK utilisent un [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) .</span><span class="sxs-lookup"><span data-stu-id="7a445-110">Most scenes within the MRTK utilize a [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight).</span></span> <span data-ttu-id="7a445-111">Le cas d’utilisation le plus courant se trouve dans MRTK/SDK/features/UX/Prefabs/Cursors/FingerCursor. Prefab</span><span class="sxs-lookup"><span data-stu-id="7a445-111">The most common use case can be found on the MRTK/SDK/Features/UX/Prefabs/Cursors/FingerCursor.prefab</span></span>

## <a name="advanced-usage"></a><span data-ttu-id="7a445-112">Utilisation avancée</span><span class="sxs-lookup"><span data-stu-id="7a445-112">Advanced Usage</span></span>

<span data-ttu-id="7a445-113">Par défaut, seuls deux [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) peuvent illuminer un [matériau](https://docs.unity3d.com/ScriptReference/Material.html) à la fois.</span><span class="sxs-lookup"><span data-stu-id="7a445-113">By default only two [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) can illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) at a time.</span></span> <span data-ttu-id="7a445-114">Si votre projet nécessite plus de deux [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) pour influencer un [matériau](https://docs.unity3d.com/ScriptReference/Material.html) , l’exemple de code ci-dessous montre comment y parvenir.</span><span class="sxs-lookup"><span data-stu-id="7a445-114">If your project requires more than two [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) to influence a [material](https://docs.unity3d.com/ScriptReference/Material.html) the sample code below demonstrates how to achieve this.</span></span>

> [!NOTE]
> <span data-ttu-id="7a445-115">Si vous avez beaucoup [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) d’éclairage, un [matériau](https://docs.unity3d.com/ScriptReference/Material.html) augmentera les instructions de nuanceur de pixels et aura un impact sur les performances.</span><span class="sxs-lookup"><span data-stu-id="7a445-115">Having many [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) will increase pixel shader instructions and will impact performance.</span></span> <span data-ttu-id="7a445-116">Profilez ces modifications dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="7a445-116">Please profile these changes within your project.</span></span>

<span data-ttu-id="7a445-117">*Comment augmenter le nombre de disponible de [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) deux à quatre.*</span><span class="sxs-lookup"><span data-stu-id="7a445-117">*How to increase the number of available [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) from two to four.*</span></span>

```C#
// 1) Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader change:

#define PROXIMITY_LIGHT_COUNT 2

// to:

#define PROXIMITY_LIGHT_COUNT 4

// 2) Within MRTK/Core/Utilities/StandardShader/ProximityLight.cs change:

private const int proximityLightCount = 2;

// to:

private const int proximityLightCount = 4;
```

> [!NOTE]
> <span data-ttu-id="7a445-118">Si Unity enregistre un avertissement similaire à celui ci-dessous, vous devez redémarrer Unity pour que vos modifications soient prises en compte.</span><span class="sxs-lookup"><span data-stu-id="7a445-118">If Unity logs a warning similar to below then you must restart Unity before your changes will take effect.</span></span>
>
>`Property (_ProximityLightData) exceeds previous array size (24 vs 12). Cap to previous size.`

## <a name="see-also"></a><span data-ttu-id="7a445-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7a445-119">See also</span></span>

* [<span data-ttu-id="7a445-120">Nuanceur standard MRTK</span><span class="sxs-lookup"><span data-stu-id="7a445-120">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)
