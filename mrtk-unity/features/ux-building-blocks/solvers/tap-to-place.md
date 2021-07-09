---
title: Appuyer pour placer
description: Documentation de TapToPlace MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK, Appuyer pour placer,
ms.openlocfilehash: 1664509a08c2d589d22b71df580328f3f3655c61
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176399"
---
# <a name="tap-to-place"></a>Appuyer pour placer

![TapToPlace](../../images/solver/tap-to-place/TapToPlaceIntroGif.gif)

Appuyez pour placer est un composant d’interaction à distance qui permet de placer un objet de jeu sur une surface. Ce composant est utile pour placer des objets sur un maillage spatial. Appuyez pour placer utilise une combinaison de deux clics et de mouvement de tête pour placer un objet. Un premier clic permet de démarrer le placement, un mouvement de la tête, de contrôler la position de l’objet et un deuxième clic, de placer l’objet dans la scène.

## <a name="using-tap-to-place"></a>Utilisation d’Appuyer pour placer

1. Configurer la scène
    - Créer une nouvelle scène Unity
    - Pour ajouter MRTK à la scène, accédez à **Mixed Reality Toolkit** > **Ajouter à la scène et configurer**
    > [!NOTE]
    > Appuyer pour placer utilise des clics pilotés par le système d’entrée MRTK, mais peut également être contrôlé sans clic. Consultez la section Configurabilité du code Appuyer pour placer ci-dessous.
    - Ajoutez un cube à la scène, remplacez l’échelle par 0,2 et modifiez la position en (0, 0, 0,7).
1. Joindre [Appuyer pour placer](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.TapToPlace) à un objet de jeu avec un collider

    ![TapToPlaceInspector](../../images/solver/tap-to-place/TapToPlaceInspector2.png)

    - Lorsque le composant Appuyer pour placer est ajouté, un gestionnaire de solveur est également joint. Appuyez pour placer dérive de la classe [Solver](solver.md), qui requiert un gestionnaire de solveur. La position d’un objet Appuyer pour placer est calculée en fonction de `TrackedTargetType` dans le gestionnaire de solveur. Par défaut, la tête est `TrackedTargetType`, cela veut dire que lorsque la tête se déplace, l’objet suit s’il est sélectionné.  Le `TrackedTargetType` peut également être réglé sur Rayon de contrôleur, ce qui fait que l’objet suit le contrôleur. Le premier groupe de propriétés de l’inspecteur Appuyer pour placer comprend les [Propriétés courantes du solveur](solver.md#common-solver-properties).  
    > [!IMPORTANT]
    > Appuyez pour placer est un solveur autonome ne pouvant pas être chaîné avec d’autres solveurs. Il ne peut pas être chaîné, car SolverHandler.UpdateSolvers est utilisé pour mettre à jour la position de l’objet lorsqu’il est placé.
    - Propriétés d’Appuyer pour placer :
        - `Auto Start` : si la valeur est True, le solveur Appuyer pour placer commence à contrôler la position de l’objet de jeu à placer. L’objet commence immédiatement à suivre le TrackedTargetType (Tête ou Rayon de contrôleur). Afin d’avoir un effet quelconque, cette valeur doit être modifiée avant l’invocation de Start().
        - `Default Placement Distance` : distance par défaut (en mètres) à laquelle un objet est placé par rapport au TrackedTargetType dans le SolverHandler. L’objet de jeu est placé à une distance de placement par défaut si une surface n’est pas atteinte par le raycast.
        - `Max Raycast Distance` : distance maximale (en mètres) pour le raycast en fonction de l’origine de « TrackedTargetType ». Ce raycast recherche une surface pour placer un objet sélectionné.
        - `UseDefaultSurfaceNormalOffset` : cette propriété est définie sur True par défaut, ce qui garantit que l’objet placé est aligné sur une surface. Si cette propriété est définie sur True, le décalage normal de la surface par défaut est appliqué à la place de toute valeur spécifiée pour la propriété `SurfaceNormalOffset`. Si la valeur est définie sur False, la valeur de `SurfaceNormalOffset` est appliquée. Le décalage normal de la surface par défaut est celui des étendues du collider sur l’axe z.
        - `Surface Normal Offset` : distance entre le centre de l’objet de jeu à placer et une surface sur la surface normale si le raycast atteint une surface. Cette propriété est appliquée uniquement à un objet si `UseDefaultSurfaceNormalOffset` est défini sur False.
        - `Keep Orientation Vertical` : si la valeur est définie sur True, l’objet de jeu doit rester debout et aligné sur Vector3.up.
        - `Rotate According to Surface` : si la valeur est définie sur false, l’objet de jeu à placer ne change pas sa rotation en fonction de l’accès à la surface.  Tant que IsBeingPlaced est défini sur True, l’objet reste face à la caméra.
        - `Magnetic Surfaces` : tableau de LayerMasks à exécuter, de la priorité la plus élevée à la plus faible. Le premier masque de calque pour fournir un accès raycast est utilisé pour les calculs de position.
        - `Debug Enabled` : si la valeur est définie sur True dans l’éditeur Unity, la normale de l’accès raycast est dessinée en jaune. Le débogage activé est utile lorsque `RotateAccordingToSurface` est True, puisqu’elle dessine la normale de l’accès à la surface qui explique visuellement la raison pour laquelle l’objet est défini sur son orientation actuelle.
        - `On Placing Started` : cet événement est déclenché une fois lorsque l’objet de jeu à placer est sélectionné.
        - `On Placing Stopped` : cet événement est déclenché une fois lorsque l’objet de jeu à placer est désélectionné et placé.

1. Test du comportement d’Appuyer pour placer dans l’éditeur
    - Appuyez sur Lire et maintenez la barre Espace enfoncée pour afficher une main de simulation d’entrée.
    - Déplacez la main jusqu’à ce que le cube soit en mode focus et simulez un clic avec la main de simulation d’entrée en cliquant avec le bouton gauche de la souris.
        - Si les colliders ne sont pas présents dans la scène, l’objet suit le `TrackedTargetType` au niveau du `Default Placement Distance` défini.
    - L’objet suit le mouvement de `TrackedTargetType` après sélection. Pour simuler le mouvement de tête dans l’éditeur, appuyez sur les touches WASD. Modifiez la rotation de tête en cliquant et en maintenant le bouton droit de la souris enfoncé.
    - Pour arrêter le placement de l’objet, cliquez de nouveau.  L’objet n’a pas besoin d’être en mode focus pour activer le clic d’arrêt de positionnement. Le focus est uniquement requis pour le clic initial qui démarre le processus de placement.

    `TrackedTargetType` : tête (par défaut) |  `TrackedTargetType` : rayon de contrôleur
    :-------------------------:|:-------------------------:
    ![Appuyer pour placer - Rayon de contrôle de la tête de simulation d’entrée](../../images/solver/tap-to-place/TapToPlaceInputSimulationHead.gif)  |  ![Appuyer pour placer - Rayon de contrôleur de simulation d’entrée 2](../../images/solver/tap-to-place/TapToPlaceInputSimulationControllerRay.gif)

## <a name="tap-to-place-code-configurability"></a>Configurabilité du code Appuyer pour placer

Le minutage de la sélection d’objet Appuyer pour placer peut également être contrôlé via `StartPlacement()` et `StopPlacement()` au lieu de demander un événement de clic. Cette fonctionnalité est utile pour écrire des tests et fournit une autre méthode pour placer un objet dans l’éditeur sans utiliser le système d’entrée MRTK.

1. Créer un objet de jeu vide
1. Créer et joindre l’exemple de script suivant à l’objet de jeu vide

    ```c#
    using UnityEngine;
    using Microsoft.MixedReality.Toolkit.Utilities.Solvers;

    public class TapToPlaceInputExample : MonoBehaviour
    {
        private GameObject cube;
        private TapToPlace tapToPlace;

        void Start()
        {
            cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
            cube.transform.localScale = Vector3.one * 0.2f;
            cube.transform.position = Vector3.forward * 0.7f;

            tapToPlace = cube.AddComponent<TapToPlace>();
        }

        void Update()
        {
            if (Input.GetKeyDown(KeyCode.U))
            {
                tapToPlace.StartPlacement();
            }
            if (Input.GetKeyDown(KeyCode.I))
            {
                tapToPlace.StopPlacement();
            }
        }
    }
    ```

1. En mode de lecture, appuyer sur la *touche U* pour commencer à placer le cube
1. Appuyer sur la *touche I* pour arrêter le placement

## <a name="tap-to-place-example-scene"></a>Exemple de scène Appuyer pour placer

L’exemple de scène Appuyer pour placer est constitué de 4 objets positionnables, chacun avec une configuration différente. L’exemple de scène contient des murs pour montrer le comportement de placement de la surface qui est désactivé par défaut dans la hiérarchie. Vous pouvez accéder à l’exemple de scène dans le package Unity Microsoft.MixedReality.Toolkit.Unity.Examples qui se trouve sur la [Page des versions](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases). L’emplacement de la scène est : *MRTK.Examples/Demos/Solvers/Scenes/TapToPlaceExample.unity*

![Exemple d’Appuyer pour placer](../../images/solver/tap-to-place/TapToPlaceExampleScene.gif)

## <a name="see-also"></a>Voir aussi

- [Solveurs](solver.md)
- [Reconnaissance spatiale](../../spatial-awareness/spatial-awareness-getting-started.md)
- [Simulation d’entrée](../../input-simulation/input-simulation-service.md)
- [Suivi de la main](../../input/hand-tracking.md)
- [Pointage du regard](../../input/gaze.md)
