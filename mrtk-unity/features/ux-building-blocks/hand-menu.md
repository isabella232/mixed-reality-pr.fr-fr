---
title: Menu de la main
description: Exemple de scène de menu manuel dans MRTK
author: cre8ivepark
ms.author: dongpark
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, HandMenu,
ms.openlocfilehash: 9bb0276c048912b4f463dd93d3303c9a3af8fe29
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177523"
---
# <a name="hand-menu"></a>Menu de la main

![Exemple d’expérience utilisateur du menu manuel](../images/solver/MRTK_UX_HandMenu.png)

Les menus manuels permettent aux utilisateurs d’afficher rapidement une interface utilisateur attachée à la main pour les fonctions fréquemment utilisées. Pour empêcher toute fausse activation lors de l’interaction avec d’autres objets, le menu manuel fournit des options telles que « exiger une main » et « utiliser l’activation en regard ». Il est recommandé d’utiliser ces options pour empêcher l’activation indésirable.

## <a name="hand-menu-examples"></a>Exemples de menus manuels

La scène **HandMenuExamples. Unity** se trouve sous le ``MRTK/Examples/Demos/HandTracking/Scenes`` dossier. Lorsqu’il est en cours d’exécution, la scène n’active que le type de menu actuellement sélectionné.
<br/><img src="../images/hand-menu/MRTK_HandMenu_ExampleScene.png" width="600px" alt="HandMenu_ExampleScene">

Vous trouverez ces prefabs dans le menu contextuel sous ``MRTK/Examples/Demos/HandTracking/Prefabs`` dossier.

### <a name="handmenu_small_hideonhanddrop-and-handmenu_medium_hideonhanddrop"></a>HandMenu_Small_HideOnHandDrop et HandMenu_Medium_HideOnHandDrop

Ces deux exemples activent et désactivent simplement l’objet MenuContent pour afficher et masquer le menu sur les événements **OnFirstHandDetected ()** et **OnLastHandLost ()** .
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example1.png" width="600" alt="HandMenu_ExampleScene 1">
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example2.png" width="600" alt="HandMenu_ExampleScene 2">

### <a name="handmenu_large_worldlock_on_grabandpull"></a>HandMenu_Large_WorldLock_On_GrabAndPull

Pour les menus plus complexes qui nécessitent une durée d’interaction plus longue, il est recommandé de verrouiller le menu. Dans cet exemple, l’utilisateur peut saisir et tirer dans le monde entier, en plus de l’activation et de la désactivation des événements MenuContent sur **OnFirstHandDetected ()** et **OnLastHandLost ()** .
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example3.png" width="600" alt="HandMenu_ExampleScene 3">

La plaque de l’arrière `ManipulationHandler` -parfait peut être saisie et déplaçable. **Lors du démarrage de la manipulation** , **SolverHandler. UpdateSolvers** est désactivé pour verrouiller le menu. En outre, il affiche le **bouton Fermer** pour permettre à l’utilisateur de fermer le menu lorsque la tâche est terminée. Dans le cas d’un événement **de fin de manipulation** , il appelle **HandConstraintPalmUp. StartWorldLockReattachCheckCoroutine** pour permettre à l’utilisateur de ramener le menu à la main en déclenchant et en regardant la paume.
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example4.png" width="600" alt="HandMenu_ExampleScene 4">

Le bouton **Fermer** réactive **SolverHandler. UpdateSolvers** et masque le **MenuContent**.
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example5.png" alt="HandMenu_ExampleScene 5">

### <a name="handmenu_large_autoworldlock_on_handdrop"></a>HandMenu_Large_AutoWorldLock_On_HandDrop

Cet exemple est similaire à HandMenu_Large_WorldLock_On_GrabAndPull. La seule différence est que le menu sera automatiquement verrouillé à la main. Pour ce faire, il suffit de masquer l’événement MenuContent sur **OnLastHandLost ()** . Le comportement d’extraction de capture & est identique à celui de HandMenu_Large_WorldLock_On_GrabAndPull exemple.

## <a name="scripts"></a>scripts ;

Le [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) comportement fournit un solveur qui limite l’objet suivi à une région sécurisée pour le contenu à la main (par exemple, l’interface utilisateur de la main, les menus, etc.). Coffre régions sont considérées comme des zones qui ne se croisent pas avec la main. Une classe dérivée de [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) appelée [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) est également incluse pour illustrer un comportement courant de l’activation de l’objet suivi du solveur lorsque le Palm est orienté vers l’utilisateur.

Pour obtenir une documentation supplémentaire, consultez les conseils d’outils disponibles pour chaque [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) propriété. Certaines propriétés sont définies plus en détail ci-dessous.

<img src="../images/solver/MRTK_Solver_HandConstraintPalmUp.png" width="450" alt="HandMenu_ExampleScene Palm up">

* **zone de Coffre**: la zone sécurisée spécifie l’emplacement de la main pour contraindre le contenu. Il est recommandé de placer le contenu du côté ulnar pour éviter tout chevauchement avec la main et une meilleure qualité d’interaction. les zones de Coffre sont calculées en adoptant l’orientation des mains projetée dans un plan orthogonal à la vue de la caméra et raycasting par rapport à un cadre englobant autour des mains. les zones de Coffre sont définies pour fonctionner avec [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) , mais elles fonctionnent également avec d’autres types de contrôleur. Nous vous recommandons d’explorer ce que chaque zone sécurisée représente sur différents types de contrôleurs.

* **Suivre la main jusqu’à la caméra** Avec cette option active, le solveur suivra la rotation de la main jusqu’à ce que le menu soit suffisamment aligné avec le point de regard, à partir duquel il est confronté à l’appareil photo. Cela fonctionne en modifiant le SolverRotationBehavior dans le HandConstraintSolver, de LookAtTrackedObject à LookAtMainCamera, car l’angle GazeAlignment avec le solveur varie.

<img src="../images/solver/MRTK_Solver_HandConstraintSafeZones.png" width="450" alt="HandMenu Safe Zones">

* **Événements d’activation**: actuellement [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) , le déclenche quatre événements d’activation. Ces événements peuvent être utilisés dans de nombreuses combinaisons différentes pour créer des [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) comportements uniques. consultez la scène HandBasedMenuExample sous `MRTK/Examples/Demos/HandTracking/Scenes/` pour obtenir des exemples de ces comportements.

  * *OnHandActivate*: déclenche une main lorsque la méthode IsHandActive est conforme à la méthode.
  * *OnHandDeactivate*: déclenche une lorsque la méthode IsHandActive n’est plus satisfaite.
  * *OnFirstHandDetected*: se produit lorsque l’état du suivi de la main passe de la vue sans mains, à la première main de la vue.
  * *OnLastHandLost*: se produit lorsque l’état de suivi de la main passe d’au moins une main dans la vue, à aucun mains dans la vue.

* **Logique d’activation/de désactivation du solveur**: actuellement, la recommandation d’activation et de désactivation de la [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) logique consiste à utiliser la valeur UpdateSolver de SolverHandler, plutôt que de désactiver/activer l’objet. Cela peut être observé dans l’exemple de scène via les hooks basés sur l’éditeur déclenchés après les événements ManipulationHandler « OnManipulationStarted/Closed » du menu attaché.

  * *Arrêt de la logique de contrainte de main*: lors de la tentative de définition de l’objet à contrainte d’arrêt (et non de l’exécution de la logique d’activation/de désactivation), affectez à UpdateSolver la valeur false au lieu de désactiver HandConstraintPalmUp.
    * Si vous souhaitez activer la logique de réassociation en regard (ou même non basée sur le pointage), vous devez appeler la fonction HandConstraintPalmUp. StartWorldLockReattachCheckCoroutine (). Cela déclenche une Coroutine qui continue à vérifier si les critères « IsValidController » sont satisfaits et définit UpdateSolver sur true une fois qu’il est (ou que l’objet est désactivé).
  * *Démarrage de la logique de contrainte de main*: lors de la tentative de définition de l’objet à contrainte pour qu’il commence à suivre à nouveau votre main (selon qu’il répond aux critères d’activation), affectez la valeur true au UpdateSolver de SolverHandler.

* **Logique de rattachement**: actuellement [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) , le est en mesure de rattacher automatiquement l’objet cible au point suivi, que le UpdateSolver de l’SolverHandler soit true ou non. Cela s’effectue par le biais de l’appel de la fonction StartWorldLockReattachCheckCoroutine () de HandConstraintPalmUp, une fois qu’elle a été verrouillée dans le monde entier (dans ce cas, le UpdateSolver de SolverHandler est effectivement défini sur false).

## <a name="see-also"></a>Voir aussi

* [Button](button.md)
* [Menu proche](near-menu.md)
