---
title: Détection des fonctionnalités de la plateforme
description: Détails des différentes fonctionnalités prises en charge par MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, fonctionnalités,
ms.openlocfilehash: 70d320e178f4635d74b5be6a1874eb4254801719
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175522"
---
# <a name="detecting-platform-capabilities"></a>Détection des fonctionnalités de la plateforme

une question courante posée sur le MRTK consiste à savoir quel périphérique spécifique (par exemple, Microsoft HoloLens 2) est utilisé pour exécuter une application. L’identification du matériel exact peut être difficile sur différentes plateformes. Au lieu de cela, le MRTK offre un moyen d’identifier des fonctionnalités spécifiques au moment de l’exécution (par exemple, si le point de terminaison de l’appareil actuel prend en charge les mains articulées).

## <a name="capabilities"></a>Fonctionnalités

la Shared Computer Toolkit de réalité mixte fournit l' [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) énumération, qui définit un ensemble de fonctionnalités pour lesquelles une application peut interroger au moment de l’exécution.

### <a name="input-system-capabilities"></a>Fonctionnalités du système d’entrée

Le système d’entrée par défaut MRTK prend en charge l’interrogation des fonctionnalités suivantes :

| Fonctionnalité | Description |
|---|---|
| ArticulatedHand | Entrée articulée |
| Suivi oculaire | Ciblage en regard des yeux |
| GGVHand | Entrée de mouvement de regard |
| MotionController | Entrée du contrôleur de mouvement |
| VoiceCommand | Commandes vocales utilisant des mots clés définis par l’application |
| VoiceDictation | Dictée de voix et de texte |

L’exemple de code ci-dessous vérifie si le système d’entrée a chargé un fournisseur de données avec prise en charge des mains articulées.

```c#
bool supportsArticulatedHands = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.InputSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsArticulatedHands = capabilityCheck.CheckCapability(MixedRealityCapability.ArticulatedHand);
}
```

### <a name="spatial-awareness-capabilities"></a>Fonctionnalités de sensibilisation spatiale

Le système de sensibilisation spatiale par défaut MRTK prend en charge l’interrogation des fonctionnalités suivantes :

| Fonctionnalité | Description |
|---|---|
| SpatialAwarenessMesh | Maillages spatiaux |
| SpatialAwarenessPlane | Plans spatiaux |
| SpatialAwarenessPoint | Points spatiaux |

Cet exemple vérifie si le système de sensibilisation spatiale a chargé un fournisseur de données avec prise en charge des maillages spatiaux.

```c#
bool supportsSpatialMesh = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.SpatialAwarenessSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsSpatialMesh = capabilityCheck.CheckCapability(MixedRealityCapability.SpatialAwarenessMesh);
}
```

## <a name="see-also"></a>Voir aussi

- [Documentation de l’API IMixedRealityCapabilityCheck](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [Documentation de l’énumération MixedRealityCapability](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability)
