---
title: Mouvements
description: Docummentation sur les gestes et ses événements dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, gestes,
ms.openlocfilehash: 7bbc97ab5e23a69356d523c463aa37c013d70337
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176879"
---
# <a name="gestures"></a>Mouvements

Les gestes sont des événements d’entrée basés sur des mains humaines. Il existe deux types d’appareils qui génèrent des événements d’entrée de mouvement dans MRTK :

- Windows Mixed Reality des appareils tels que HoloLens. Cela décrit le pincement des mouvements (« TAP Air ») et les gestes tap-and-hold.

  pour plus d’informations sur les gestes de HoloLens, consultez la documentation sur les [gestes de Windows Mixed Reality](/windows/mixed-reality/gestures).

  [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)encapsule le [XR Unity. WSA. Input. GestureRecognizer](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.GestureRecognizer.html) pour consommer les événements de mouvement unity à partir de HoloLens appareils.

- Appareils à écran tactile.

  [`UnityTouchController`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput) encapsule la [classe Touch Unity](https://docs.unity3d.com/ScriptReference/Touch.html) qui prend en charge les écrans tactiles physiques.

ces deux sources d’entrée utilisent le profil de _Paramètres de mouvement_ pour traduire les événements tactiles et de mouvement d’unity respectivement en [Actions d’entrée](input-actions.md)de MRTK. ce profil se trouve sous le profil de _Paramètres du système d’entrée_ .

<img src="../images/input/GestureProfile.png" alt="Gesture Profile" style="max-width:100%;">

## <a name="gesture-events"></a>Événements de mouvement

Les événements de mouvement sont reçus en implémentant l’une des interfaces du gestionnaire de mouvements : [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) ou [`IMixedRealityGestureHandler<TYPE>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) (consultez la table des [gestionnaires d’événements](input-events.md)).

Consultez [exemple de scène](#example-scene) pour obtenir un exemple d’implémentation d’un gestionnaire d’événements de mouvement.

Lors de l’implémentation de la version générique, les événements *OnGestureCompleted* et *OnGestureUpdated* peuvent recevoir des données typées des types suivants :

- `Vector2` -mouvement de position 2D. Produits par les écrans tactiles pour informer leurs [`deltaPosition`](https://docs.unity3d.com/ScriptReference/Touch-deltaPosition.html) .
- `Vector3` -mouvement de position 3D. produit par HoloLens pour informer :
  - [`cumulativeDelta`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.ManipulationUpdatedEventArgs-cumulativeDelta.html) d’un événement de manipulation
  - [`normalizedOffset`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.NavigationUpdatedEventArgs-normalizedOffset.html) d’un événement de navigation
- `Quaternion` -mouvement de rotation 3D. Disponible pour les sources d’entrée personnalisées, mais ne sont actuellement pas produites par les sources existantes.
- `MixedRealityPose` -Mouvement de position/rotation 3D combiné. Disponible pour les sources d’entrée personnalisées, mais ne sont actuellement pas produites par les sources existantes.

## <a name="order-of-events"></a>Ordre des événements

Il existe deux chaînes principales d’événements, en fonction de l’entrée utilisateur :

- « Hold » :
    1. Maintenir appuyé :
        - Démarrer la _manipulation_
    1. Maintenez appuyé sur [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):
        - Démarrer la _conservation_
    1. Appuyez sur la version :
        - terminer la _conservation_
        - _manipulation_ complète

- « Move » :
    1. Maintenir appuyé :
        - Démarrer la _manipulation_
    1. Maintenez appuyé sur [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):
        - Démarrer la _conservation_
    1. Déplacer vers la main au-delà de [NavigationStartThreshold](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.NavigationStartThreshold):
        - annuler la _conservation_
        - Démarrer la _navigation_
    1. Appuyez sur la version :
        - _manipulation_ complète
        - terminer la _navigation_

## <a name="example-scene"></a>Exemple de scène

La scène **HandInteractionGestureEventsExample** (éléments multimédias/MRTK/examples/démos/HandTracking/scènes) montre comment utiliser le résultat du pointeur pour générer un objet à l’emplacement de l’accès.

Le `GestureTester` script (ressources/MRTK/examples/démos/HandTracking/script) est un exemple d’implémentation permettant de visualiser des événements de mouvement via GameObjects. Les fonctions de gestionnaire modifient la couleur des objets indicateur et affichent le dernier événement enregistré dans les objets de texte de la scène.
