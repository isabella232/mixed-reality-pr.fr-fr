---
title: Mise à niveau à partir de HoloToolkit
description: Migration de HoloLens Shared Computer Toolkit (HTK) vers la réalité mixte Shared Computer Toolkit (MRTK).
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, HTK,
ms.openlocfilehash: b54445dc5ca7a6c01c968929e243a1fc4ca2d107
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281752"
---
# <a name="upgrading-from-holotoolkit"></a>Mise à niveau à partir de HoloToolkit

guide pour vous aider à migrer à partir de HoloLens Shared Computer Toolkit (HTK) vers la réalité mixte Shared Computer Toolkit (MRTK).

## <a name="controller-and-hand-input"></a>Entrée du contrôleur et de la main

### <a name="setup-and-configuration"></a>Installation et configuration

|         Méthodes                  | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Type                      | Événements spécifiques pour les boutons, avec les informations de type d’entrée, le cas échéant. | Entrée basée sur des actions/mouvements, transmise via des événements. |
| Installation                     | Placez le InputManager dans la scène. | Activez le système d’entrée dans le [profil de configuration](../configuration/mixed-reality-configuration-guide.md) et spécifiez un type de système d’entrée concret. |
| Configuration             | Configuré dans l’inspecteur, sur chaque script individuel de la scène. | Configuré via le profil de système d’entrée de la réalité mixte et son profil associé, listés ci-dessous. |

Profils associés :

* Profil de mappage de contrôleur de réalité mixte
* Profil de visualisation du contrôleur de réalité mixte
* Profil de mouvements de réalité mixte
* Profil des actions d’entrée de réalité mixte
* Profil de règles d’action d’entrée de réalité mixte
* Profil de pointeur de réalité mixte

Les paramètres du [fournisseur de regard](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider) sont modifiés sur l’objet Camera principal de la scène.

les composants de prise en charge de plateforme (par exemple, Windows Mixed Reality Gestionnaire de périphériques) doivent être ajoutés aux fournisseurs de données du service correspondant.

### <a name="interface-and-event-mappings"></a>Mappages d’interfaces et d’événements

Certains événements n’ont plus d’événements uniques et contiennent maintenant un [MixedRealityInputAction](../features/input/input-actions.md). Ces actions sont spécifiées dans le profil des actions d’entrée et mappées à des contrôleurs et des plateformes spécifiques dans le profil de mappage du contrôleur. Les événements tels que `OnInputDown` doivent maintenant vérifier le type MixedRealityInputAction.

Systèmes d’entrée associés :

* [Vue d'ensemble des entrées](../features/input/overview.md)
* [Événements d’entrée](../features/input/input-events.md)
* [Pointeurs d’entrée](../features/input/pointers.md)

| HTK 2017 |  MRTK v2  | Mappage d’action |
|----------|-----------|----------------|
| `IControllerInputHandler` | [`IMixedRealityInputHandler<Vector2>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Mappé au pavé tactile ou au stick analogique |
| `IControllerTouchpadHandler` | [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | Mappé au pavé tactile |
| `IFocusable` | [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler) | |
| `IGamePadHandler` | [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | |
| `IHoldHandler` | [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) | Mappé à la conservation dans le profil des mouvements |
| `IInputClickHandler` | [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) |
| `IInputHandler` | [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | Mappé sur les boutons du contrôleur ou sur la main |
| `IManipulationHandler` | [`IMixedRealityGestureHandler<Vector3>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | Mappé à la manipulation dans le profil de mouvements |
| `INavigationHandler` | [`IMixedRealityGestureHandler<Vector3>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | Mappé à la navigation dans le profil des mouvements |
| `IPointerSpecificFocusable` | [`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) | |
| `ISelectHandler` | [`IMixedRealityInputHandler<float>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Mappé à la position du déclencheur |
| `ISourcePositionHandler` | [`IMixedRealityInputHandler<Vector3>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) ou [`IMixedRealityInputHandler<MixedRealityPose>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Mappé à la position du pointeur ou à la position de la poignée |
| `ISourceRotationHandler` | [`IMixedRealityInputHandler<Quaternion>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) ou [`IMixedRealityInputHandler<MixedRealityPose>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Mappé à la position du pointeur ou à la position de la poignée |
| `ISourceStateHandler` | [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | |
| `IXboxControllerHandler` | [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) les [`IMixedRealityInputHandler<Vector2>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Mappé aux différents boutons de contrôleur et Thumbsticks |

## <a name="camera"></a>Appareil photo

|        Méthodes                    | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Installation                     | supprimez MainCamera, ajoutez MixedRealityCameraParent/MixedRealityCamera/HoloLensCamera prefab à scene ou utilisez la réalité mixte Shared Computer Toolkit > configurez > élément de menu appliquer une séquence **de** réalité mixte Paramètres. | MainCamera apparenté sous MixedRealityPlayspace via la réalité mixte Shared Computer Toolkit > ajouter à la scène et configurer... |
| Configuration             | Configuration des paramètres de l’appareil photo effectuée sur l’instance Prefab. | Paramètres d’appareil photo configurés dans le [profil d’appareil photo de la réalité mixte](xref:Microsoft.MixedReality.Toolkit.MixedRealityCameraProfile). |

## <a name="speech"></a>Voix

### <a name="keyword-recognition"></a>Reconnaissance de mot clé

|         Méthodes                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Installation                     | Ajoutez un SpeechInputSource à votre scène. | le service de mot clé (par exemple, Windows gestionnaire d’entrée vocale) doit être ajouté aux fournisseurs de données du système d’entrée. |
| Configuration             | Les mots clés reconnus sont configurés dans l’inspecteur de SpeechInputSource. | Les mots clés sont configurés dans le [profil de commandes vocales de réalité mixte](../features/input/speech.md). |
| Gestionnaires d’événements            | `ISpeechHandler` | [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) |

### <a name="dictation"></a>Dictation

|         Méthodes                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Installation                     | Ajoutez un DictationInputManager à votre scène. | la prise en charge de la dictée nécessite que le service (par exemple, Windows gestionnaire d’entrée de dictée) soit ajouté aux fournisseurs de données du système d’entrée. |
| Gestionnaires d’événements            | `IDictationHandler` | `IMixedRealityDictationHandler`[`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) |

## <a name="spatial-awareness--mapping"></a>Sensibilisation spatiale/mappage

### <a name="mesh"></a>Maillage

|         Méthodes                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Installation                     | Ajoutez le Prefab SpatialMapping à la scène. | activez le système de sensibilisation spatiale dans le profil de Configuration et ajoutez un observateur spatial (par exemple, Windows Mixed Reality observateur de maillage spatial) aux fournisseurs de données du système de sensibilisation spatiale. |
| Configuration             | Configurez l’instance de scène dans l’inspecteur. | Configurez les paramètres sur le profil de chaque observateur spatial. |

### <a name="planes"></a>Appareils

|         Méthodes                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Installation                     | Utilisez le `SurfaceMeshesToPlanes` script. | Pas encore implémenté. |

### <a name="spatial-understanding"></a>Compréhension spatiale

|       Méthodes                      | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Installation                     | Ajoutez le Prefab SpatialUnderstanding à la scène. | Pas encore implémenté. |
| Configuration             | Configurez l’instance de scène dans l’inspecteur. | Pas encore implémenté. |

## <a name="boundary"></a>Limite

|         Méthodes                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Installation                     | Ajoutez le `BoundaryManager` script à la scène. | Activez le système de limites dans le profil de configuration. |
| Configuration             | Configurez l’instance de scène dans l’inspecteur. | Configurez les paramètres dans le profil de visualisation des limites. |

## <a name="sharing"></a>Partage

|             Méthodes               | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Installation                     | Service de partage : ajoutez des Prefab de partage à la scène. UNet : utilisez l’exemple SharingWithUNET. | En cours |
| Configuration             | Configurez les instances de scène dans l’inspecteur. | En cours |

## <a name="ux"></a>UX

|         Méthodes                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Bouton                     | [Objets interactifs](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_InteractableObjectExample.md) | [Button](../features/ux-building-blocks/Button.md) |
| Avec interaction                     | [Objets interactifs](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_InteractableObjectExample.md) | [Avec interaction](../features/ux-building-blocks/Interactable.md) |
| Cadre englobant             | [Cadre englobant](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_BoundingBoxGizmoExample.md) | [Cadre englobant](../features/ux-building-blocks/bounding-box.md) |
| Barre d’application             | [Barre de l’application](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_BoundingBoxGizmoExample.md) | [Barre de l’application](../features/ux-building-blocks/app-bar.md) |
| Manipulation d’une seule main (GRB et Move)   | [HandDraggable](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/Interactions/HandDraggable.cs) | [Gestionnaire de manipulation](../features/ux-building-blocks/manipulation-handler.md) |
| Manipulation en deux mains (manipulation/déplacement/rotation/mise à l’échelle)             | [TwoHandManipulatable](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/Interactions/TwoHandManipulatable.cs) | [Gestionnaire de manipulation](../features/ux-building-blocks/manipulation-handler.md) |
| Clavier             | [Prefab clavier]() | [Clavier système](../features/ux-building-blocks/system-keyboard.md) |
| Info-bulle             | [Info-bulle](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_TooltipExample.md) | [Info-bulle](../features/ux-building-blocks/tooltip.md) |
| Collection d’objets             | [Collection d’objets](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/UX/Readme/README_ObjectCollection.md) | [Collection d’objets](../features/ux-building-blocks/object-collection.md) |
| Solver             | [Solver](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Utilities/Readme/README_SolverSystem.md) | [Solver](../features/ux-building-blocks/solvers/solver.md) |

## <a name="utilities"></a>Outils

Certains utilitaires ont été conciliés en tant que doublons avec le système du solveur. Veuillez envoyer un problème si l’un des scripts dont vous avez besoin est manquant.

| HTK 2017 |  MRTK v2  |
|----------|-----------|
| Blanc | [`Billboard`](xref:Microsoft.MixedReality.Toolkit.UI.Billboard) |
| Accompagnent | [`RadialView`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.RadialView) ou le [`Orbital`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Orbital) [Solveur](../features/ux-building-blocks/solvers/Solver.md) |
| FixedAngularSize | [`ConstantViewSize`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.ConstantViewSize)[Solveur](../features/ux-building-blocks/solvers/solver.md) |
| FpsDisplay | [Système de diagnostic](../features/diagnostics/diagnostics-system-getting-started.md) (dans le profil de configuration) |
| NearFade | nuanceur intégré à la [réalité mixte Shared Computer Toolkit nuanceur Standard](../features/rendering/mrtk-standard-shader.md) |
