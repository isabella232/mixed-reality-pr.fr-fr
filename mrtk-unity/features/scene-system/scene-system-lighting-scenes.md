---
title: Système de scène - Éclairage de scènes
description: Documentation sur l’éclairage dans la scène.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: fa7442bc968710a31ce3ca379c7fd73928e6e324
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144414"
---
# <a name="lighting-scene-operations"></a>Opérations de scène d’éclairage

La scène d’éclairage par défaut définie dans votre profil est chargée au démarrage. Cette scène d’éclairage reste chargée jusqu’à ce que `SetLightingScene` soit appelé.

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MorningLighting");
```

## <a name="lighting-setting-transitions"></a>Transitions de paramètres d’éclairage

`transitionType` contrôle le style de la transition vers la nouvelle scène d’éclairage.

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MiddayLighting", LightingSceneTransitionType.CrossFade);
```

Les styles disponibles sont les suivants :

Type | Description | Duration
--- | --- | ---
None | La scène d’éclairage précédente est déchargée, la nouvelle scène d’éclairage est chargée. Aucune transition. | Ignoré
FadeToBlack | La scène d’éclairage précédente disparaît en noir. Une nouvelle scène d’éclairage est chargée, puis grisée du noir. Utile pour les transitions lisses entre les emplacements. | Utilisé
Fondu enchaîné | La scène d’éclairage précédente apparaît en fondu quand de nouvelles scènes d’éclairage sont en fondu. Utile pour les transitions douces entre les configurations d’éclairage au même emplacement. | Utilisé

Notez que certains paramètres d’éclairage ne peuvent pas être interpolés pendant les transitions. Si vous souhaitez une transition visuelle lisse, ces paramètres devront rester cohérents entre les scènes d’éclairage.

Paramètre | Transition Smooth FadeToBlack | Transition Smooth fondu
--- | --- | ---
Skybox | Non | Non
Réflexions personnalisées | Non | Non
Ombres en temps réel Sun | Oui | Non
