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
# <a name="proximity-light"></a>Lumière proche

Un [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) est un paradigme de [système de conception Fluent](https://www.microsoft.com/design/fluent/) qui imite une « lumière de point inverse de dégradé » en pointant près de la surface d’un objet. Souvent utilisé pour les interactions proches, l’application peut contrôler les propriétés d’une lumière de proximité via le [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) composant.

Pour qu’un matériau soit influencé par un [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) nuanceur de *réalité mixte* , le nuanceur standard doit être utilisé et la propriété de *lumière de proximité* doit être activée.

> [!NOTE]
> Jusqu’à deux [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) sont pris en charge par défaut.

## <a name="examples"></a>Exemples

La plupart des scènes dans le MRTK utilisent un [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) . Le cas d’utilisation le plus courant se trouve dans MRTK/SDK/features/UX/Prefabs/Cursors/FingerCursor. Prefab

## <a name="advanced-usage"></a>Utilisation avancée

Par défaut, seuls deux [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) peuvent illuminer un [matériau](https://docs.unity3d.com/ScriptReference/Material.html) à la fois. Si votre projet nécessite plus de deux [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) pour influencer un [matériau](https://docs.unity3d.com/ScriptReference/Material.html) , l’exemple de code ci-dessous montre comment y parvenir.

> [!NOTE]
> Si vous avez beaucoup [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) d’éclairage, un [matériau](https://docs.unity3d.com/ScriptReference/Material.html) augmentera les instructions de nuanceur de pixels et aura un impact sur les performances. Profilez ces modifications dans votre projet.

*Comment augmenter le nombre de disponible de [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) deux à quatre.*

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
> Si Unity enregistre un avertissement similaire à celui ci-dessous, vous devez redémarrer Unity pour que vos modifications soient prises en compte.
>
>`Property (_ProximityLightData) exceeds previous array size (24 vs 12). Cap to previous size.`

## <a name="see-also"></a>Voir aussi

* [Nuanceur standard MRTK](mrtk-standard-shader.md)
