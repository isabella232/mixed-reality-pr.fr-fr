---
title: Services de simulation d’entrée
description: Documentation sur le service de simulation d’entrée dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 81e7dcab7e0f349d05521f93d75bba6927761fd1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145089"
---
# <a name="input-simulation-service"></a>Service de simulation d’entrée

Le service de simulation d’entrée émule le comportement des appareils et des plateformes qui peuvent ne pas être disponibles dans l’éditeur Unity. Voici quelques exemples :

* Suivi de la tête de périphérique HoloLens ou VR
* Gestes de main HoloLens
* Suivi de la main articulé 2
* Suivi oculaire HoloLens 2
* Contrôleurs de périphérique VR

Les utilisateurs peuvent utiliser une combinaison de clavier et de souris conventionnels pour contrôler les appareils simulés au moment de l’exécution. Cette approche permet de tester les interactions dans l’éditeur Unity sans déployer au préalable sur un appareil.

> [!WARNING]
> Cela ne fonctionne pas lors de l’utilisation de l’émulation holographique XR de Unity > de l’émulation mode = « simuler dans l’éditeur ». La simulation in-Editor de Unity prend le contrôle à la suite de la simulation d’entrée de MRTK. Pour utiliser le service de simulation d’entrée MRTK, vous devez définir l’émulation holographique XR sur émulation mode = *"none"*

## <a name="enabling-the-input-simulation-service"></a>Activation du service de simulation d’entrée

La simulation d’entrée est activée par défaut dans les profils fournis avec MRTK.

Dans le cadre de la configuration du fournisseur de données de système d’entrée, le service de simulation d’entrée peut être configuré comme suit.

* Le **type** doit être *Microsoft. MixedReality. Toolkit. Input > InputSimulationService*.
* Les **plateformes prises en charge** incluent par défaut toutes les plateformes d' *éditeur* , car le service utilise le clavier et l’entrée de souris.

> [!NOTE]
> Le service de simulation d’entrée peut être utilisé sur d’autres points de terminaison de plateforme tels que standalone en modifiant la propriété **plateformes prises en charge** pour inclure les cibles souhaitées.
> ![Plateformes d’entrée prises en charge](../images/input-simulation/InputSimulationSupportedPlatforms.gif)

## <a name="input-simulation-tools-window"></a>Fenêtre outils de simulation d’entrée

Activez la fenêtre outils de simulation d’entrée à partir du  >    >  menu **simulation d’entrée** des utilitaires de la boîte à outils de la réalité mixte. Cette fenêtre permet d’accéder à l’état de la simulation d’entrée en mode lecture.

## <a name="viewport-buttons"></a>Boutons de la fenêtre d’affichage

Un Prefab pour les boutons de l’éditeur pour contrôler le placement de base peut être spécifié dans le profil de simulation d’entrée sous **indicateurs Prefab**. Il s’agit d’un utilitaire facultatif qui permet d’accéder aux mêmes fonctionnalités dans la [fenêtre outils de simulation d’entrée](#input-simulation-tools-window).

> [!NOTE]
> Les indicateurs de la fenêtre d’affichage sont désactivés par défaut, car ils peuvent parfois interférer avec les interactions de l’interface utilisateur Unity. Consultez [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106)de problèmes. Pour activer, ajoutez le Prefab InputSimulationIndicators à **indicateurs Prefab**.

Les icônes de main affichent l’état des mains simulées :

* ![Icône de main non suivie](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Untracked.png) La main n’effectue pas de suivi. Cliquez pour activer la main.
* ![Icône de main](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png "Icône de main") La main est suivie, mais n’est pas contrôlée par l’utilisateur. Cliquez pour masquer la main.
* ![Icône de main contrôlée](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "Icône de main contrôlée") La main est suivie et contrôlée par l’utilisateur. Cliquez pour masquer la main.
* ![Icône réinitialiser la main](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "Icône réinitialiser la main") Cliquez pour rétablir la position par défaut de la main.

## <a name="in-editor-input-simulation-cheat-sheet"></a>Aide-mémoire de simulation d’entrée de l’éditeur

Appuyez sur Ctrl + H gauche dans la scène HandInteractionExamples pour afficher une aide-mémoire avec les contrôles de simulation d’entrée.

![Aide-mémoire pour la simulation d’entrée](https://user-images.githubusercontent.com/39840334/86066480-13637f00-ba27-11ea-8814-d222d548f684.gif)

## <a name="camera-control"></a>Contrôle Camera

Le mouvement de la tête peut être émulé par le service de simulation d’entrée.

### <a name="rotating-the-camera"></a>Rotation de l’appareil photo

1. Pointez sur la fenêtre de l’éditeur de fenêtre d’affichage.
    *Vous devrez peut-être cliquer sur la fenêtre pour lui attribuer le focus si l’appui sur les boutons ne fonctionne pas.*
1. Maintenez le bouton de la **souris** enfoncé (par défaut : bouton droit de la souris).
1. Déplacez la souris dans la fenêtre de la fenêtre d’affichage pour faire pivoter l’appareil photo.
1. Utilisez la roulette de défilement pour faire rouler l’appareil photo autour de la direction de l’affichage.

La vitesse de rotation de la caméra peut être configurée en modifiant le paramètre de vitesse de la **souris** dans le profil de simulation d’entrée.

Vous pouvez également utiliser les axes verticaux regarder **horizontales** /  pour faire pivoter l’appareil photo (par défaut : joystick droit du contrôleur de jeu).

### <a name="moving-the-camera"></a>Déplacement de la caméra

Utilisez les axes verticaux déplacer vers le déplacement **horizontal** /  pour déplacer l’appareil photo (valeur par défaut : clés WASD ou joystick gauche du contrôleur de jeu).

Les angles de position et de rotation de la caméra peuvent également être définis explicitement dans la fenêtre outils. La caméra peut être réinitialisée à sa valeur par défaut à l’aide du bouton **Réinitialiser** .

<iframe width="560" height="315" src="https://www.youtube.com/embed/Z7L4I1ET7GU" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="controller-simulation"></a>Simulation de contrôleur

La simulation d’entrée prend en charge les périphériques de contrôleur émulés (c’est-à-dire les contrôleurs de mouvement et les aiguilles). Ces contrôleurs virtuels peuvent interagir avec n’importe quel objet qui prend en charge des contrôleurs normaux, tels que des boutons ou des objets pouvant être pris en charge.

### <a name="controller-simulation-mode"></a>Mode de simulation du contrôleur

Dans la [fenêtre outils de simulation d’entrée](#input-simulation-tools-window) , le paramètre de **mode de simulation du contrôleur par défaut** bascule entre trois modèles d’entrée distincts. Ce mode par défaut peut également être défini dans le profil de simulation d’entrée.

* *Mains articulées*: simule un appareil manuel entièrement articulé avec des données de position conjointe.

   Émule le modèle d’interaction HoloLens 2.

   Les interactions basées sur le positionnement précis de la main ou sur l’utilisation du toucher peuvent être simulées dans ce mode.

* *Mouvements manuels*: simule un modèle de main simplifié avec robinet d’air et les gestes de base.

   Émule le [modèle d’interaction HoloLens](/windows/mixed-reality/gestures).

   Le focus est contrôlé à l’aide du pointeur en forme de pointage. Le mouvement d' *appui sur l’air* est utilisé pour interagir avec les boutons.

* *Contrôleur de mouvement*: simule un contrôleur de mouvement utilisé avec des casques VR qui fonctionne de la même manière que les interactions beaucoup avec les mains articulées.

   Émule le casque VR avec le modèle d’interaction de contrôleurs.

   Le déclencheur, les touches de manipulation et de menu sont simulés via l’entrée du clavier et de la souris.

### <a name="simulating-controller-movement"></a>Simulation du mouvement du contrôleur

Maintenez enfoncée la **touche de manipulation du contrôleur gauche/droite** (par défaut : *décalage vers* la gauche pour le contrôleur gauche et *espace* pour le contrôleur droit) afin de prendre le contrôle de l’un des deux contrôleurs. Pendant que la touche manipulation est enfoncée, le contrôleur s’affiche dans la fenêtre d’affichage. Une fois la clé de manipulation libérée, les contrôleurs disparaissent après une réduction **du délai d’expiration du contrôleur**.

Les contrôleurs peuvent être activés ou désactivés par rapport à l’appareil photo dans la [fenêtre outils de simulation d’entrée](#input-simulation-tools-window) ou en appuyant sur la **touche basculer vers la gauche/droite du contrôleur** (par défaut : *T* pour gauche et *Y* pour droite). Appuyez de nouveau sur la touche bascule pour masquer à nouveau les contrôleurs. Pour manipuler les contrôleurs, la **clé de manipulation du contrôleur gauche/droite** doit être maintenue. Si vous double-Appuyez sur la **touche de manipulation du contrôleur gauche/droite** , vous pouvez également activer/désactiver les contrôleurs.

Le déplacement de la souris déplace le contrôleur dans le plan d’affichage. Les contrôleurs peuvent être déplacés davantage ou plus près de l’appareil photo à l’aide de la roulette de la **souris**.

Pour faire pivoter les contrôleurs à l’aide de la souris, maintenez la **touche de manipulation du contrôleur gauche/droite** (*décalage vers la gauche* ou *espace*) *et* le bouton de **rotation du contrôleur** (par défaut : bouton *CTRL gauche* ), puis déplacez la souris pour faire pivoter le contrôleur. La vitesse de rotation du contrôleur peut être configurée en modifiant le paramètre **vitesse de rotation du contrôleur** de la souris dans le profil de simulation d’entrée.

Tout le positionnement manuel peut également être modifié dans la [fenêtre outils de simulation d’entrée](#input-simulation-tools-window), y compris la réinitialisation des mains par défaut.

### <a name="additional-profile-settings"></a>Paramètres de profil supplémentaires

* Le **multiplicateur de profondeur du contrôleur** contrôle la sensibilité du déplacement de la profondeur de la roulette de défilement de la souris. Un nombre plus élevé accélère le zoom du contrôleur.
* La **distance de contrôleur par défaut** est la distance initiale des contrôleurs de l’appareil photo. En cliquant sur les contrôleurs de bouton de **réinitialisation** , vous placez également les contrôleurs à cette distance.
* Le **volume d’instabilité du contrôleur** ajoute un mouvement aléatoire aux contrôleurs. Cette fonctionnalité peut être utilisée pour simuler un suivi des contrôleurs inexacts sur l’appareil et garantir que les interactions fonctionnent bien avec les entrées bruyantes.

<iframe width="560" height="315" src="https://www.youtube.com/embed/uRYfwuqsjBQ" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="hand-gestures"></a>Mouvements des mains

Les gestes manuels, tels que le pincement, la saisie, l’percer, etc., peuvent également être simulés.

1. Activer le contrôle de main à l’aide de la **clé de manipulation du contrôleur gauche/droite** (*décalage vers la gauche* ou *espace*)

2. Lors de la manipulation, appuyez et maintenez enfoncé un bouton de la souris pour effectuer un mouvement manuel.

Chacun des boutons de la souris peut être mappé pour transformer la forme main en un geste différent en utilisant les paramètres de mouvement de la *souris à gauche/au milieu/à droite* . Le *mouvement de main par défaut* est la forme de la main quand aucun bouton n’est enfoncé.

> [!NOTE]
> Le geste de *pincement* est le seul mouvement qui exécute l’action « Select » à ce stade.

### <a name="one-hand-manipulation"></a>Manipulation en une seule main

1. Appuyez et maintenez enfoncée la **touche de manipulation du contrôleur gauche/droite** (*décalage vers la gauche* ou *espace*)
2. Pointer sur l’objet
3. Maintenir le bouton de la souris enfoncé
4. Utilisez la souris pour déplacer l’objet
5. Relâchez le bouton de la souris pour arrêter l’interaction

<iframe width="560" height="315" src="https://www.youtube.com/embed/rM0xaHam6wM" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="two-hand-manipulation"></a>Manipulation à deux mains

Pour manipuler des objets avec deux mains en même temps, le mode de main permanent est recommandé.

1. Activez les deux mains en appuyant sur les touches bascule (*T/Y*).
1. Manipuler une seule main à la fois :
    1. Conserver de l' **espace** pour contrôler la main droite
    1. Déplacer la main vers l’emplacement où vous souhaitez récupérer l’objet
    1. Appuyez sur le **bouton gauche** de la souris pour activer le mouvement de *pincement* .
    1. Libérez de l' **espace** pour arrêter le contrôle de la main droite. La main sera figée en place et sera verrouillée dans le geste de *pincement* , car elle n’est plus manipulée.
1. Répétez le processus en faisant glisser le même objet en une seconde.
1. Maintenant que les deux mains attirent le même objet, vous pouvez les déplacer pour effectuer une manipulation à deux mains.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qol5OFNfN14" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="ggv-gaze-gesture-and-voice-interaction"></a>Interaction GGV (point de regard, geste et voix)

Par défaut, l’interaction avec GGV est activée dans l’éditeur, alors qu’il n’y a aucune mains articulées dans la scène.

1. Faire pivoter l’appareil photo pour pointer le curseur en regard de l’objet interagi (bouton droit de la souris)
1. Cliquez et maintenez le **bouton gauche de la souris** enfoncé pour interagir
1. Faites pivoter à nouveau l’appareil pour manipuler l’objet

Vous pouvez désactiver ce mode en basculant sur l’option est disponible en *entrée libre* à l’intérieur du profil de simulation d’entrée.

En outre, vous pouvez utiliser des mains simulées pour l’interaction GGV

1. Activer la simulation GGV en basculant en **mode de simulation manuelle** sur les *gestes* dans le [profil de simulation d’entrée](#enabling-the-input-simulation-service)
1. Faire pivoter l’appareil photo pour pointer le curseur en regard de l’objet interagi (bouton droit de la souris)
1. Conserver de l' **espace** pour contrôler la main droite
1. Cliquez et maintenez le **bouton gauche de la souris** enfoncé pour interagir
1. Utilisez la souris pour déplacer l’objet
1. Relâchez le bouton de la souris pour arrêter l’interaction

<iframe width="560" height="315" src="https://www.youtube.com/embed/6841rRMdqWw" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="raising-teleport-events"></a>Déclenchement d’événements de télégénération

Pour déclencher l’événement de télétransmission dans la simulation d’entrée, configurez les paramètres de mouvement de main dans le profil de simulation d’entrée de sorte que l’un effectue le mouvement de **démarrage** de la télétransmission pendant que l’autre effectue **le geste de** télétransmission. Le geste de **démarrage** de la téléscripteur affiche le pointeur de téléaction, tandis que **le gesure de** téléscription termine l’action de téléscription et déplace l’utilisateur.

La position y de la téléchargement résultante dépend du déplacement de la caméra le long de l’axe y. Dans l’éditeur, il s’agit de 0 par défaut. Utilisez donc les touches **Q** et **E** pour l’ajuster à la hauteur appropriée.

![Paramètres de reversions de simulation d’entrée](../images/input-simulation/InputSimulationTeleport.gif)

### <a name="motion-controller-interaction"></a>Interaction du contrôleur de mouvement

Les contrôleurs de mouvement simulés peuvent être manipulés de la même façon que les mains articulées. Le modèle d’interaction est semblable à l’interaction Far de la main, tandis que le déclencheur, les touches de manipulation et de menu sont mappées respectivement au *bouton gauche de la souris*, à la clé *G* et *M* .

### <a name="eye-tracking"></a>Eye-tracking

Vous pouvez activer la [simulation du suivi des yeux](../input/eye-tracking/eye-tracking-basic-setup.md#simulating-eye-tracking-in-the-unity-editor) en activant l’option **simuler la position des yeux** dans le profil de [simulation d’entrée](#enabling-the-input-simulation-service). Cela ne doit pas être utilisé avec les interactions de style de contrôleur de mouvement ou GGV (Vérifiez que le **mode de simulation du contrôleur par défaut** est défini sur *main*).

## <a name="see-also"></a>Voir aussi

* [Profil du système d’entrée](../input/input-providers.md).