---
title: Guide de portage de HTK vers MRTK
description: Migration de HoloLens Toolkit (HTK) vers Mixed Reality Toolkit (MRTK).
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, HTK,
ms.openlocfilehash: fbcb2863c894a4e4c1529e19112b33712f69e99f
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143764"
---
# <a name="porting-guide"></a>Guide sur le portage

Guide pour vous aider à migrer à partir de la boîte à outils HoloLens (HTK) vers le kit de MRTK (Mixed Reality Toolkit).

## <a name="controller-and-hand-input"></a>Entrée du contrôleur et de la main

### <a name="setup-and-configuration"></a>Installation et configuration

|         Méthodes                  | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Type                      | Événements spécifiques pour les boutons, avec les informations de type d’entrée, le cas échéant. | Entrée basée sur des actions/mouvements, transmise via des événements. |
| Programme d’installation                     | Placez le InputManager dans la scène. | Activez le système d’entrée dans le [profil de configuration](../configuration/mixed-reality-configuration-guide.md) et spécifiez un type de système d’entrée concret. |
| Configuration             | Configuré dans l’inspecteur, sur chaque script individuel de la scène. | Configuré via le profil de système d’entrée de la réalité mixte et son profil associé, listés ci-dessous. |

Profils associés :

* Profil de mappage de contrôleur de réalité mixte
* Profil de visualisation du contrôleur de réalité mixte
* Profil de mouvements de réalité mixte
* Profil des actions d’entrée de réalité mixte
* Profil de règles d’action d’entrée de réalité mixte
* Profil de pointeur de réalité mixte

Les paramètres du [fournisseur de regard](xref:Microsoft.MixedReality.Toolkit.Input.GazeProvider) sont modifiés sur l’objet Camera principal de la scène.

Les composants de prise en charge de plateforme (par exemple, Windows Mixed Reality Gestionnaire de périphériques) doivent être ajoutés aux fournisseurs de données du service correspondant.

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
| Programme d’installation                     | Supprimez MainCamera, ajoutez MixedRealityCameraParent/MixedRealityCamera/HoloLensCamera Prefab à Scene ou utilisez la boîte à outils de réalité mixte > configurer > élément de menu appliquer les paramètres de scène **de** la réalité mixte. | MainCamera apparenté sous MixedRealityPlayspace via la boîte à outils de réalité mixte > ajouter à la scène et configurer... |
| Configuration             | Configuration des paramètres de l’appareil photo effectuée sur l’instance Prefab. | Paramètres d’appareil photo configurés dans le [profil d’appareil photo de la réalité mixte](xref:Microsoft.MixedReality.Toolkit.MixedRealityCameraProfile). |

## <a name="speech"></a>Speech

### <a name="keyword-recognition"></a>Reconnaissance de mot clé

|         Méthodes                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Programme d’installation                     | Ajoutez un SpeechInputSource à votre scène. | Le service de mot clé (par exemple, le gestionnaire d’entrée Windows Speech) doit être ajouté aux fournisseurs de données du système d’entrée. |
| Configuration             | Les mots clés reconnus sont configurés dans l’inspecteur de SpeechInputSource. | Les mots clés sont configurés dans le [profil de commandes vocales de réalité mixte](../features/input/speech.md). |
| Gestionnaires d’événements            | `ISpeechHandler` | [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) |

### <a name="dictation"></a>Dictation

|         Méthodes                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Programme d’installation                     | Ajoutez un DictationInputManager à votre scène. | La prise en charge de la dictée nécessite que le service (par exemple, le gestionnaire d’entrée de dictée Windows) soit ajouté aux fournisseurs de données du système d’entrée. |
| Gestionnaires d’événements            | `IDictationHandler` | `IMixedRealityDictationHandler`[`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) |

## <a name="spatial-awareness--mapping"></a>Sensibilisation spatiale/mappage

### <a name="mesh"></a>Maillage

|         Méthodes                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Programme d’installation                     | Ajoutez le Prefab SpatialMapping à la scène. | Activez le système de sensibilisation spatiale dans le profil de configuration et ajoutez un observateur spatial (par exemple, l’observateur de maillage spatial Windows Mixed Reality) aux fournisseurs de données du système de sensibilisation spatiale. |
| Configuration             | Configurez l’instance de scène dans l’inspecteur. | Configurez les paramètres sur le profil de chaque observateur spatial. |

### <a name="planes"></a>Appareils

|         Méthodes                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Programme d’installation                     | Utilisez le `SurfaceMeshesToPlanes` script. | Pas encore implémenté. |

### <a name="spatial-understanding"></a>Compréhension spatiale

|       Méthodes                      | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Programme d’installation                     | Ajoutez le Prefab SpatialUnderstanding à la scène. | Pas encore implémenté. |
| Configuration             | Configurez l’instance de scène dans l’inspecteur. | Pas encore implémenté. |

## <a name="boundary"></a>Limite

|         Méthodes                   | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Programme d’installation                     | Ajoutez le `BoundaryManager` script à la scène. | Activez le système de limites dans le profil de configuration. |
| Configuration             | Configurez l’instance de scène dans l’inspecteur. | Configurez les paramètres dans le profil de visualisation des limites. |

## <a name="sharing"></a>Partage

|             Méthodes               | HTK 2017 |  MRTK v2  |
|---------------------------|----------|-----------|
| Programme d’installation                     | Service de partage : ajoutez des Prefab de partage à la scène. UNet : utilisez l’exemple SharingWithUNET. | En cours |
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

## <a name="utilities"></a>Services

Certains utilitaires ont été conciliés en tant que doublons avec le système du solveur. Veuillez envoyer un problème si l’un des scripts dont vous avez besoin est manquant.

| HTK 2017 |  MRTK v2  |
|----------|-----------|
| Blanc | [`Billboard`](xref:Microsoft.MixedReality.Toolkit.UI.Billboard) |
| Accompagnent | [`RadialView`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.RadialView) ou le [`Orbital`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Orbital) [Solveur](../features/ux-building-blocks/solvers/Solver.md) |
| FixedAngularSize | [`ConstantViewSize`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.ConstantViewSize)[Solveur](../features/ux-building-blocks/solvers/solver.md) |
| FpsDisplay | [Système de diagnostic](../features/diagnostics/diagnostics-system-getting-started.md) (dans le profil de configuration) |
| NearFade | [Nuanceur standard intégré au nuanceur de la réalité mixte](../features/rendering/mrtk-standard-shader.md) |
