---
title: Suivi des mains et des yeux dans Unity
description: En savoir plus sur les deux méthodes clés pour prendre des mesures sur le point d’intergression, les gestes manuels et les contrôleurs de mouvement.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: gestes, contrôleurs de mouvement, unity, point d’entrée, point d’entrée, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, MRTK, Shared Computer Toolkit de la réalité mixte
ms.openlocfilehash: 005b817574e6d3600b9c43e443432203418b58a2258e2938614cc549ab7539c2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223797"
---
# <a name="articulated-hand-and-eye-tracking-in-unity"></a>Suivi des mains et des yeux dans Unity

HoloLens 2 a introduit des fonctionnalités nouvelles et passionnantes, telles que la main articulée et le suivi oculaire.

Le moyen le plus simple de tirer parti de la nouvelle fonctionnalité dans Unity est d’utiliser MRTK. Il existe également des exemples de scènes pour vous aider à commencer.

* [Prise en main de la main articulée dans MRTK](/windows/mixed-reality/mrtk-unity/features/input/hand-tracking)
* [Prise en main du suivi oculaire dans MRTK](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main)

## <a name="building-blocks-supporting-hands-eyes-and-others-in-mrtk"></a>Blocs de construction prenant en charge les mains, les yeux et autres dans MRTK

MRTK v2 fournit un ensemble de contrôles d’interface utilisateur et de blocs de construction pour vous aider à accélérer votre développement.

|  [![Bouton](images/MRTK_Button_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) [Bouton](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) | Cadre englobant [du cadre](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box) [ ![ englobant](images/MRTK_BoundingBox_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box) | [Gestionnaire](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/manipulation-handler) de manipulation du [ ![ Gestionnaire de manipulation](images/MRTK_Manipulation_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/manipulation-handler) |
|:--- | :--- | :--- |
| Un contrôle Button, qui prend en charge différentes méthodes d’entrée, y compris HoloLens2's articulée | Interface utilisateur standard pour manipuler des objets dans l’espace 3D | Script pour manipuler des objets avec une ou deux mains |
|  [![Tablette](images/MRTK_Slate_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/slate) [Tablette](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/slate) | [![Clavier système](images/MRTK_SystemKeyboard_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/system-keyboard) [Clavier système](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/system-keyboard) | [![Interaction](images/InteractableExamples.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable) [Interaction](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable) |
| plan de style 2D, qui prend en charge le défilement avec une entrée articulée | Exemple de script d’utilisation du clavier système dans Unity  | Script pour rendre les objets interactifs avec les états visuels et la prise en charge des thèmes |
|  [![Solveur](images/MRTK_Solver_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver) [Solveur](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver) | [![Collection d’objets](images/MRTK_ObjectCollection_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection) [Collection d’objets](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection) | [![Info-bulle](images/MRTK_Tooltip_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/tooltip) [Info-bulle](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/tooltip) |
| Différents comportements de positionnement des objets, tels que balise, verrouillage de corps, taille de vue constante et magnétisme de surface | Script pour disposer un tableau d’objets dans une forme en trois dimensions | Interface utilisateur d’annotation avec un système d’ancrage/pivot flexible, qui peut être utilisé pour étiqueter les contrôleurs de mouvement et l’objet. |
|  [![Barre d’application](images/MRTK_AppBar_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/app-bar) [Barre d’application](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/app-bar) | [![Pointeurs](images/MRTK_Pointer_Main.png)](/windows/mixed-reality/mrtk-unity/features/input/pointers) [Pointeurs](/windows/mixed-reality/mrtk-unity/features/input/pointers) | [![Visualisation du bout des doigts](images/MRTK_FingertipVisualization_Main.png)](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/fingertip-visualization) [Visualisation du bout des doigts](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/fingertip-visualization) |
| Interface utilisateur pour l’activation manuelle du cadre englobant | Découvrez les différents types de pointeurs | Visuel à portée de main, ce qui améliore la confiance pour l’interaction directe |
|  [![Suivi oculaire : Sélection de la cible](images/mrtk_et_targetselect.png)](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-target-selection) [Suivi oculaire : Sélection de la cible](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-target-selection) | [![Suivi oculaire : Navigation](images/mrtk_et_navigation.png)](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-navigation) [Suivi oculaire : Navigation](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-navigation) |
| Combiner les yeux, la voix et la main pour sélectionner rapidement et facilement des hologrammes sur votre scène | Découvrez comment faire défiler automatiquement le texte ou zoomer sur le contenu ciblé en fonction de ce que vous cherchez| Exemples de journalisation, de chargement et de visualisation de ce que les utilisateurs ont examiné dans votre application |

## <a name="example-scenes"></a>Exemples de scène

Explorez les différents types d’interactions et de contrôles d’interface utilisateur du MRTK dans [cet exemple de scène](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples).

vous trouverez d’autres exemples de scènes dans la [réalité mixte Shared Computer Toolkit GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity) sous **ressources/MixedRealityToolkit. exemples/dossiers de démonstrations**.

[![Exemple de scène](images/MRTK_Examples.png)](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples)

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours de développement Unity que nous avons disposé, vous êtes au cœur de l’exploration des blocs de construction MRTK Core. À partir d’ici, vous pouvez passer au composant suivant :

> [!div class="nextstepaction"]
> [Mappage spatial](spatial-mapping-in-unity.md)

Ou accéder aux API et fonctionnalités de la plateforme Mixed Reality :

> [!div class="nextstepaction"]
> [Expériences partagées](shared-experiences-in-unity.md)

Vous pouvez revenir aux [points de contrôle de développement Unity](unity-development-overview.md#2-core-building-blocks) à tout moment.

## <a name="see-also"></a>Voir aussi

* [Interaction basée sur le regard](../../design/eye-gaze-interaction.md)
* [Suivi oculaire sur HoloLens 2](../../design/eye-tracking.md)
* [Pointer et valider](../../design/gaze-and-commit.md)
* [Mains : Manipulation directe](../../design/direct-manipulation.md)
* [Mains : Mouvements](../../design/gaze-and-commit.md#composite-gestures)
* [Mains : Pointer et valider](../../design/point-and-commit.md)
* [Interactions instinctuelles](../../design/interaction-fundamentals.md)
* [Contrôleurs de mouvement](../../design/motion-controllers.md)
* [UnityEngine. XR. WSA. Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)