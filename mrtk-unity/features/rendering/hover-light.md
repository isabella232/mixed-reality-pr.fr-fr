---
title: Lumière lointaine
description: Documentation sur HoverLight avec des exemples dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, lumière de survol,
ms.openlocfilehash: 948a0772cd2fad667984d8d5507664e4346a507e84b03c873eccf8d3f1e66532
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198581"
---
# <a name="hover-light"></a>Lumière lointaine

un [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) est un paradigme de [Système Fluent Design](https://www.microsoft.com/design/fluent/) qui imite une [lumière de pointage](https://docs.unity3d.com/Manual/Lighting.html) près de la surface d’un objet. Souvent utilisées pour les interactions éloignées, l’application peut contrôler les propriétés d’une lumière de survol via le [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) composant.

pour qu’une matière soit influencée par [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) une *réalité mixte Shared Computer Toolkit* nuanceur/d’doit être utilisé et la propriété *Light sensitive* doit être activée.

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
