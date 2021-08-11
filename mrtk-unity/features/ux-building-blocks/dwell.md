---
title: Fixer du regard
description: Interaction du logement
author: cre8ivepark
ms.author: dongpark
ms.date: 05/20/2021
keywords: logement, unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 8ac63ee723cdd524ee7abbad7fd2658b446156adbd5ddee06ae1795edb3b68d1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226902"
---
# <a name="dwell"></a>Fixer du regard

![Bannière de fixation du regard](../images/dwell/MRTK_UX_Dwell.png)

Le point de regard et le front-tête sont très utiles dans les scénarios où les mains d’une personne sont occupées par d’autres tâches. Cette fonctionnalité est également utile lorsque la voix n’est pas 100% fiable ou disponible en raison de contraintes environnementales ou sociales.
Les exemples de logements de MRTK illustrent différents types de composants de l’interface utilisateur avec un temps de réponse configurable et des commentaires visuels.

Pour connaître les recommandations en matière de conception, consultez la page des indications sur la [tête et le point d’intersection](/windows/mixed-reality/design/gaze-and-dwell-head) .

## <a name="dwell-scripts"></a>Scripts de logement

- **DwellHandler**: ajoute une modalité de logement à la cible de l’interface utilisateur.
- **DwellStateType**: États du gestionnaire de logements.
- **DwellUnityEvent**: événement Unity pour un événement de logement. Contient la référence du pointeur.
- **BaseDwellPressableButton. cs** : script qui déclenche l’événement OnClick () dans `Interactable` de PressableButtonHoloLens2 prefabs.
- **ToggleDwellPressableButton. cs** : ce script modifie `_BorderWidth` la propriété du `dwellVisualImage` qui utilise le nuanceur standard MRTK.

## <a name="dwell-profiles"></a>Profils de logement
Les profils de logement sont utilisés par le **Gestionnaire de logements** pour configurer les différents seuils.
- **ButtonDwellProfile. Asset**
- **InstandDwellProfile. Asset**
- **DwellProfileWithDecay. Asset**

## <a name="prefabs"></a>Prefabs

ces prefabs sont des variantes du bouton HoloLens 2 de style prefabs qui ont des composants supplémentaires pour prendre en charge les interactions de logements.

- **PressableButtonHoloLens2_Dwell. Prefab**
- **PressableButtonHoloLens2_32x96_Dwell. Prefab**
- **PressableButtonHoloLens2ToggleDwell. Prefab**
- **PressableButtonHoloLens2Toggle_32x96_Dwell. Prefab**

Ces prefabs ont un composant **QuadDwellVisual** supplémentaire pour visualiser l’état d’entrée du logement. Elle est assignée à **HolographicBackPlateDwellVisual. mat** . **ToggleDwellPressableButton. cs** met à jour la propriété **_BorderWidth** du nuanceur standard MRTK pour visualiser l’entrée du logement.

<img src="../images/dwell/MRTK_UX_Dwell_Prefabs_Structure.png" alt="Dwell prefabs structure" width="550px">
<img src="../images/dwell/MRTK_UX_Dwell_Prefabs.png" alt="Dwell prefabs" width="350px">

## <a name="example-scene"></a>Exemple de scène

Vous trouverez des exemples dans la `DwellExample` scène. L’exemple de scène montre à la fois des exemples volumétriques et des exemples d’interface utilisateur Unity.

<img src="../images/dwell/MRTK_UX_Dwell_Examples.png" alt="Near Menu Example">

## <a name="see-also"></a>Voir aussi

- [**Boutons**](button.md)
- [**Avec interaction**](interactable.md)
