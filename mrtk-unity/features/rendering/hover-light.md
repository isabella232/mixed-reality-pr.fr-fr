---
title: Lumière lointaine
description: Documentation sur HoverLight avec des exemples dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, Light sensitive,
ms.openlocfilehash: b98dff0dd3ff0312f6ce607a5fb8a26f94959ff2
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145169"
---
# <a name="hover-light"></a>Lumière lointaine

Un [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) est un paradigme de [système de conception Fluent](https://www.microsoft.com/design/fluent/) qui imite une [lumière de pointage](https://docs.unity3d.com/Manual/Lighting.html) près de la surface d’un objet. Souvent utilisées pour les interactions éloignées, l’application peut contrôler les propriétés d’une lumière de survol via le [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) composant.

Pour qu’un matériau soit influencé par un [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) nuanceur de *réalité mixte* , le nuanceur standard doit être utilisé et la propriété de *lumière de survol* doit être activée.

> [!Note]
> Le nuanceur MRTK/standard prend en charge un maximum de deux [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) par défaut, mais il est mis à l’échelle pour prendre en charge quatre, puis 10 à mesure que d’autres lumières sont ajoutées à la scène.

## <a name="examples"></a>Exemples

La plupart des scènes dans le MRTK utilisent un [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) . Le cas d’utilisation le plus courant se trouve dans MRTK/SDK/features/UX/Prefabs/Cursors/DefaultCursor. Prefab

La scène **HoverLightExamples** illustre également l’utilisation des [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) comportements et se trouve à l’adresse suivante : MRTK/examples/démos/StandardShader/scènes/

## <a name="advanced-usage"></a>Utilisation avancée

Seules dix [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) peuvent éclairer un [matériau](https://docs.unity3d.com/ScriptReference/Material.html) à la fois. Si votre projet nécessite plus de dix [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) pour influencer un [matériau](https://docs.unity3d.com/ScriptReference/Material.html) , l’exemple de code ci-dessous montre comment y parvenir.

> [!Note]
> Si vous avez beaucoup [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) d’éclairage, un [matériau](https://docs.unity3d.com/ScriptReference/Material.html) augmentera les instructions de nuanceur de pixels et aura un impact sur les performances. **Profilez ces modifications dans votre projet.**

*Comment augmenter le nombre de disponibles [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) de 10 à 12.*

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
> Si Unity enregistre un avertissement similaire à celui ci-dessous, vous devez redémarrer Unity pour que vos modifications soient prises en compte.
>
> `Property (_HoverLightData) exceeds previous array size (24 vs 20). Cap to previous >size.`

## <a name="see-also"></a>Voir aussi

* [Nuanceur standard MRTK](mrtk-standard-shader.md)
