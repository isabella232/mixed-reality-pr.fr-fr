---
title: Documentation sur le développement avec MRTK-Unity
description: Découvrez le Mixed Reality Toolkit (MRTK) pour Unity.
author: polar-kev
ms.author: kesemple
ms.date: 03/03/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 85a203f22c62871265f7775c364f5388194b53a1
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550969"
---
# <a name="what-is-the-mixed-reality-toolkit"></a>Présentation du Mixed Reality Toolkit

![Mixed Reality Toolkit](features/images/Logo_MRTK_Unity_Banner.png)

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/qfONlUCSWdg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

MRTK-Unity est un projet Microsoft qui fournit un ensemble de composants et de fonctionnalités servant à accélérer le développement d’applications de réalité mixte interplateformes dans Unity. Voici quelques-unes de ses fonctions :

* Fournit **le système d’entrée multiplateforme et les composants pour les interactions spatiales et l’interface utilisateur**.
* Active le **prototypage rapide** via la simulation dans l’éditeur qui vous permet de voir immédiatement les modifications.
* Fonctionne comme un **framework extensible** qui fournit aux développeurs la possibilité de permuter les composants de base.
* **Prend en charge une large gamme de plateformes** dont
  * OpenXR (Unity 2020.2 ou ultérieur)
    * Microsoft HoloLens 2
    * Casques Windows Mixed Reality
  * Windows Mixed Reality
    * Microsoft HoloLens
    * Microsoft HoloLens 2
    * Casques Windows Mixed Reality
  * Oculus (Unity 2019.3 ou ultérieur)
    * Oculus Quest
  * OpenVR
    * Casques Windows Mixed Reality
    * HTC Vive
    * Oculus Rift
  * Suivi de la main Ultraleap
  * Appareils mobiles comme iOS et Android

## <a name="getting-started-with-mrtk"></a>Bien démarrer avec MRTK

Si vous débutez avec le développement MRTK ou Mixed Reality dans Unity, nous vous recommandons d’installer les outils nécessaires, puis de suivre la série de tutoriels HoloLens 2.

> [!div class="nextstepaction"]
> [Installer les outils](install-the-tools.md)

> [!div class="nextstepaction"]
> [Série de tutoriels HoloLens 2](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02)

Vous voulez voir ce qui se passe en coulisses ?
> [!div class="nextstepaction"]
> [Explorez MRTK sur GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity)

## <a name="documentation"></a>Documentation

| [![Notes de publication](features/images/MRTK_Icon_ReleaseNotes.png)](release-notes/mrtk-26-release-notes.md)<br/>[Notes de publication](release-notes/mrtk-26-release-notes.md)| [![Présentation de MRTK](features/images/MRTK_Icon_ArchitectureOverview.png)](architecture/overview.md)<br/>[Présentation de MRTK](architecture/overview.md)|[![Informations de référence sur les API](features/images/MRTK_Icon_APIReference.png)](/dotnet/api/Microsoft.MixedReality.Toolkit)<br/>[Référence sur l’API](/dotnet/api/Microsoft.MixedReality.Toolkit)|
|:---|:---|:---|

## <a name="build-status"></a>État de la build

| Branche | État CI | État de la documentation |
|---|---|---|
| `mrtk_development` |[![État CI](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)|[![État de la documentation](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)

## <a name="feature-areas"></a>Zones de fonctionnalité

:::row:::
    :::column:::
       [![Système d’entrée](features/images/MRTK_Icon_InputSystem.png)](features/input/overview.md)<br>
        **[Système d’entrée](features/input/overview.md)**<br>
    :::column-end:::
    :::column:::
        [![Suivi de la main (HoloLens 2)](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md)<br>
        **[Suivi de la main <br> (HoloLens 2)](features/input/hand-tracking.md)**<br>
    :::column-end:::
    :::column:::
        [![Suivi du regard (HoloLens 2)](features/images/MRTK_Icon_EyeTracking.png)](features/input/eye-tracking/eye-tracking-Main.md)<br>
        **[Suivi du regard <br/> (HoloLens 2)](features/input/eye-tracking/eye-tracking-Main.md)**<br>
    :::column-end:::
    :::column:::
        [![Profils](features/images/MRTK_Icon_Profiles.png)](configuration/mixed-reality-configuration-guide.md)<br>
        **[Profils](configuration/mixed-reality-configuration-guide.md)**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Suivi de la main (Ultraleap)](features/images/MRTK_Icon_HandTracking.png)](features/cross-platform/leap-motion-mrtk.md)<br>
        **[Suivi de la main <br/> (Ultraleap)](features/cross-platform/leap-motion-mrtk.md)**<br>
    :::column-end:::
    :::column:::
        [![Contrôles d’interface utilisateur](features/images/MRTK_Icon_UIControls.png)](#ux-building-blocks)<br>
        **[Contrôles d’interface utilisateur](#ux-building-blocks)**<br>
    :::column-end:::
    :::column:::
        [![Solveurs](features/images/MRTK_Icon_Solver.png)](features/ux-building-blocks/solvers/solver.md)<br>
        **[Solveurs](features/ux-building-blocks/solvers/solver.md)**<br>
    :::column-end:::
    :::column:::
        [![Gestionnaire multiscène](features/images/MRTK_Icon_SceneSystem.png)](features/scene-system/scene-system-getting-started.md)<br>
        **[Gestionnaire<br/> multiscène](features/scene-system/scene-system-getting-started.md)**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Reconnaissance spatiale](features/images/MRTK_Icon_SpatialUnderstanding.png)](features/spatial-awareness/spatial-awareness-getting-started.md)<br>
        **[Reconnaissance <br/> spatiale](features/spatial-awareness/spatial-awareness-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![Outil de diagnostic](features/images/MRTK_Icon_Diagnostics.png)](features/diagnostics/diagnostics-system-getting-started.md)<br>
        **[Outil de <br/> diagnostic](features/diagnostics/diagnostics-system-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![Nuanceur standard MRTK](features/images/MRTK_Icon_StandardShader.png)](features/rendering/mrtk-standard-shader.md?q=shader)<br>
        **[Exemple de vue du nuanceur standard MRTK](features/rendering/mrtk-standard-shader.md?q=shader)**<br>
    :::column-end:::
    :::column:::
        [![Voix & dictée](features/images/MRTK_Icon_VoiceCommand.png)](features/scene-system/scene-system-getting-started.md)<br>
        **[Voix](features/input/speech.md)<br/> & [dictée](features/input/dictation.md)**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Système de limites](features/images/MRTK_Icon_Boundary.png)](features/boundary/boundary-system-getting-started.md)<br>
        **[Système de <br/>limites](features/boundary/boundary-system-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![Simulation dans l’éditeur](features/images/MRTK_Icon_InputSystem.png)](features/diagnostics/diagnostics-system-getting-started.md)<br>
        **[Simulation <br/> dans l’éditeur](features/diagnostics/diagnostics-system-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![Fonctionnalités expérimentales](features/images/MRTK_Icon_Experimental.png)](contributing/experimental-features.md)<br>
        **[Fonctionnalités <br/> expérimentales](contributing/experimental-features.md)**<br>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

## <a name="ux-building-blocks"></a>Composants de l’interface utilisateur

:::row:::
    :::column:::
       [![Bouton](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) **[Bouton](features/ux-building-blocks/button.md)**<br>
        Contrôle bouton qui prend en charge différentes méthodes d’entrée, y compris la main articulée d’HoloLens 2
    :::column-end:::
    :::column:::
        [![Contrôle des limites](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) **[Contrôle des limites](features/ux-building-blocks/bounds-control.md)**<br>
        Interface utilisateur standard pour manipuler des objets dans l’espace 3D
    :::column-end:::
    :::column:::
        [![Manipulateur d’objets](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md) **[Manipulateur d’objets](features/ux-building-blocks/object-manipulator.md)**<br>
        Script pour manipuler des objets avec une ou deux mains
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Tablette](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) **[Tablette](features/ux-building-blocks/slate.md)**<br>
        Plan de style 2D qui prend en charge le défilement avec des entrées par la main articulée
    :::column-end:::
    :::column:::
        [![Clavier système](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) **[Clavier système](features/ux-building-blocks/system-keyboard.md)**<br>
        Exemple de script d’utilisation du clavier système dans Unity
    :::column-end:::
    :::column:::
        [![Interaction](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) **[Interaction](features/ux-building-blocks/interactable.md)**<br>
        Script pour rendre les objets interactifs avec les états visuels et la prise en charge des thèmes
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Solveur](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md) **[Solveur](features/ux-building-blocks/solvers/solver.md)**<br>
        Différents comportements de positionnement des objets, comme les menus qui restent à proximité (tag-along), le rattachement au corps (body-lock), la taille de vue constante et l’aimantation de surface
    :::column-end:::
    :::column:::
        [![Collection d’objets](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) **[Collection d’objets](features/ux-building-blocks/object-collection.md)**<br>
        Script pour disposer un tableau d’objets dans une forme en trois dimensions
    :::column-end:::
    :::column:::
        [![Info-bulle](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md) **[Info-bulle](features/ux-building-blocks/tooltip.md)**<br>
        Interface utilisateur Annotation avec un système d’ancrage/de pivot flexible, qui peut être utilisé pour étiqueter les contrôleurs de mouvement et les objets
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Curseur](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) **[Curseur](features/ux-building-blocks/sliders.md)**<br>
        Interface utilisateur Curseur pour ajuster des valeurs prenant en charge l’interaction de suivi de la main direct
    :::column-end:::
    :::column:::
        [![Nuanceur standard du MRTK](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) **[Nuanceur standard du MRTK](features/rendering/mrtk-standard-shader.md)**<br>
        Le nuanceur standard du MRTK prend en charge différents éléments Fluent Design performants
    :::column-end:::
    :::column:::
        [![Menu de la main](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) **[Menu de la main](features/ux-building-blocks/hand-menu.md)**<br>
        Interface utilisateur rattachée à la main pour un accès rapide, à l’aide du solveur de contraintes de la main
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Barre d’application](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) **[Barre d’application](features/ux-building-blocks/app-bar.md)**<br>
        Interface utilisateur pour l’activation manuelle du contrôle des limites
    :::column-end:::
    :::column:::
        [![Pointeurs](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[Pointeurs](features/input/pointers.md)**<br>
        Découvrez les différents types de pointeurs
    :::column-end:::
    :::column:::
        [![Visualisation du bout des doigts](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) **[Visualisation du bout des doigts](features/ux-building-blocks/fingertip-visualization.md)**<br>
        Affordance visuelle du bout des doigts, qui améliore la confiance dans l’interaction directe
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Menu proche](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) **[Menu proche](features/ux-building-blocks/near-menu.md)**<br>
        Interface utilisateur du menu flottant pour les interactions proches
    :::column-end:::
    :::column:::
        [![Bien démarrer avec la reconnaissance spatiale](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[Vue de la reconnaissance spatiale](features/spatial-awareness/spatial-awareness-getting-started.md)**<br>
        Faire interagir vos objets holographiques avec les environnements physiques
    :::column-end:::
    :::column:::
        [![Commande vocale](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) **[Commande vocale](features/input/speech.md)**<br>
        Scripts et exemples pour intégrer des entrées vocales
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Indicateur de progression](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) **[Indicateur de progression](features/ux-building-blocks/progress-indicator.md)**<br>
        Indicateur visuel qui renseigne sur un processus ou une opération de données
    :::column-end:::
    :::column:::
        [![Boîte de dialogue](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) **[Boîte de dialogue](features/ux-building-blocks/dialog.md)**<br>
        Interface utilisateur pour demander à l’utilisateur une confirmation ou son accord
    :::column-end:::
    :::column:::
        [![Coach de main](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) **[Coach de main](features/ux-building-blocks/hand-coach.md)**<br>
        Composant qui guide l’utilisateur quand le mouvement n’a pas été appris
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Service de la physique des mains](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/experimental/hand-physics-service.md) **[Service de la physique des mains [expérimental]](features/experimental/hand-physics-service.md)**<br>
        Le service de la physique des mains rend possible les événements et interactions de collision de corps rigides avec les mains articulées
    :::column-end:::
    :::column:::
        [![Défilement de la collection](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) **[Défilement de la collection](features/ux-building-blocks/scrolling-object-collection.md)**<br>
        Collection d’objets qui défile en mode natif pour exposer les objets 3D
    :::column-end:::
    :::column:::
        [![Ancrage](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md) **[Ancrage [expérimental]](features/experimental/dock.md)**<br>
        L’ancrage permet de placer des objets dans ou en dehors de positions prédéterminées
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Suivi oculaire : Sélection de la cible](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) **[Suivi oculaire : Sélection de la cible](features/input/eye-tracking/eye-tracking-target-selection.md)**<br>
        Combinez les entrées oculaires, vocales et manuelles pour sélectionner rapidement et facilement des hologrammes sur votre scène
    :::column-end:::
    :::column:::
        [![Suivi oculaire : Navigation](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) **[Suivi oculaire : Navigation](features/input/eye-tracking/eye-tracking-navigation.md)**<br>
        Apprenez à faire défiler le texte automatiquement ou à faire facilement un zoom sur le contenu ciblé en fonction de ce que vous regardez
    :::column-end:::
    :::column:::
        [![Suivi oculaire : Carte thermique](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) **[Suivi oculaire : Carte thermique](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)**<br>
        Exemples de journalisation, de chargement et de visualisation de ce que les utilisateurs ont regardé dans votre application
    :::column-end:::
:::row-end:::

## <a name="tools"></a>Outils

|  [![Fenêtre d’optimisation](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md) [Fenêtre d’optimisation](features/tools/optimize-window.md) | [![Fenêtre de dépendance](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md) [Fenêtre de dépendance](features/tools/dependency-window.md) | ![Fenêtre de build](features/images/MRTK_Icon_BuildWindow.png) Fenêtre de build | [![Enregistrement des entrées](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md) [Enregistrement des entrées](features/input-simulation/input-animation-recording.md) |
|:--- | :--- | :--- | :--- |
| Automatiser la configuration des projets de réalité mixte pour les optimisations de performances | Analyser les dépendances entre les ressources et identifier les ressources inutilisées |  Configurer et exécuter un processus de build de bout en bout pour les applications de réalité mixte | Enregistrer et lire les données de suivi de la main et des mouvements de tête dans l’éditeur |

## <a name="example-scenes"></a>Exemples de scènes

Explorez les différents types d’interactions et de contrôles d’interface utilisateur du MRTK dans [cet exemple de scène](features/example-scenes/hand-interaction-examples.md).

[![Exemple de scène 2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)

## <a name="mrtk-examples-hub"></a>Hub d’exemples MRTK

Avec le hub d’exemples MRTK, vous pouvez essayer divers exemples de scènes dans MRTK.
Vous pouvez télécharger des packages d’applications prédéfinis pour HoloLens (x86), HoloLens 2 (ARM) et les casques immersifs Windows Mixed Reality (x64) en sélectionnant le package « Exemples du Mixed Reality Toolkit » dans [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool). Veillez à [utiliser le portail d’appareil Windows pour installer des applications sur HoloLens (1ère génération)](/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens). Sur HoloLens 2, vous pouvez télécharger et installer le [Hub d’exemples MRTK à partir de l’application Microsoft Store](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4).

Consultez la [page README du hub d’exemples](features/example-scenes/example-hub.md) pour en savoir plus sur la création d’un hub multiscène avec le système de scène et le service de transition de scène de MRTK.

[![Hub d’exemples de scènes](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)

## <a name="sample-apps-made-with-mrtk"></a>Exemples d’applications créées avec MRTK

| [![Tableau périodique des éléments](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)| [![Galaxy Explorer](features/images/MRTK_GalaxyExplorer.jpg)](/windows/mixed-reality/galaxy-explorer-update)| [![Exemple d’application Surfaces](features/images/MRDL_Surfaces.jpg)](/windows/mixed-reality/sampleapp-surfaces)|
|:--- | :--- | :--- |
| [Tableau périodique des éléments](https://github.com/Microsoft/MRDL_Unity_PeriodicTable) est un exemple d’application open source qui montre comment utiliser le système d’entrée et les composants du MRTK afin de créer une expérience d’application pour les casques immersifs et HoloLens. Lisez le récit sur le portage qui raconte comment [importer l’application Tableau périodique des éléments vers HoloLens 2 avec MRTK v2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158) |[Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer) est un exemple d’application open source qui a été initialement développé en mars 2016 dans le cadre de la campagne HoloLens « Partagez vos idées ». L’application Galaxy Explorer a été mise à jour avec de nouvelles fonctionnalités pour HoloLens 2, avec MRTK v2. Lisez le récit sur la [conception de Galaxy Explorer pour HoloLens 2](/windows/mixed-reality/galaxy-explorer-update) |[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces) est un exemple d’application open source pour HoloLens 2, qui explore la manière dont nous pouvons créer une sensation tactile en utilisant le suivi oculaire, audio et avec la main entièrement articulée. Regardez la session Microsoft MR Dev Days [Enseignements tirés de l’application Surfaces](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App) pour lire le récit détaillé de la conception et du développement. |

## <a name="session-videos-from-mixed-reality-dev-days-2020"></a>Vidéos de la session Mixed Reality Dev Days 2020

| [![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)| [![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)| [![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)|
|:--- | :--- | :--- |
| Tutoriel sur la création d’une application MRTK simple, du début à la fin. Découvrez les concepts de l’interaction et les fonctionnalités multiplateformes de MRTK. | Présentation approfondie des composants UX de MRTK qui vous aident à créer de belles expériences de réalité mixte. | Présentation des outils de performances, intégrés à MRTK ou externes, et vue d’ensemble du nuanceur standard de MRTK. |

Consultez [Mixed Reality Dev Days](/windows/mixed-reality/mr-dev-days-sessions) pour explorer d’autres vidéos de session.

## <a name="engage-with-the-community"></a>Impliquez-vous dans la communauté

* Participez aux conversations autour de MRTK sur [Slack](https://holodevelopers.slack.com/). Vous pouvez rejoindre la communauté Slack par le biais de l’[envoi d’invitation automatique](https://holodevelopersslack.azurewebsites.net/).

* Posez vos questions au sujet de l’utilisation de MRTK sur le site [Stack Overflow](https://stackoverflow.com/questions/tagged/mrtk) en choisissant l’étiquette **MRTK**.

* Faites une recherche sur les [problèmes connus](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) ou signalez un [nouveau problème](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) si vous détectez quelque chose qui ne va pas dans le code MRTK.

* Pour toute question sur la contribution à MRTK, accédez au canal [mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) sur Slack.

Ce projet a adopté le [Code de conduite Open Source de Microsoft](https://opensource.microsoft.com/codeofconduct/).
Pour plus d'informations, voir la [FAQ sur le Code de conduite ](https://opensource.microsoft.com/codeofconduct/faq/) ou contacter [opencode@microsoft.com](mailto:opencode@microsoft.com) pour toute question ou commentaire supplémentaire.

## <a name="useful-resources-on-the-mixed-reality-dev-center"></a>Ressources utiles dans le Centre de développement Réalité mixte

| ![Découvrir](features/images/mrdevcenter/icon-discover.png) [Découvrir](/windows/mixed-reality/)| ![Concevoir](features/images/mrdevcenter/icon-design.png) [Concevoir](/windows/mixed-reality/design)| ![Développer](features/images/mrdevcenter/icon-develop.png) [Développer](/windows/mixed-reality/development)| ![Distribuer](features/images/mrdevcenter/icon-distribute.png) [Distribuer](/windows/mixed-reality/implementing-3d-app-launchers)|
| :--------------------- | :----------------- | :------------------ | :------------------------ |
| Découvrez comment créer des expériences de réalité mixte pour HoloLens et les casques immersifs (VR).          | Procurez-vous les guides de conception. Créez une interface utilisateur. Découvrez les interactions et les entrées.     | Procurez-vous les guides de développement. Découvrez la technologie. Comprenez la science.       | Préparez votre application pour les utilisateurs et créez un lanceur 3D. |

## <a name="useful-resources-on-azure"></a>Ressources utiles sur Azure

| ![Spatial Anchors](features/images/mrdevcenter/icon-azurespatialanchors.png)<br> [Spatial Anchors](/azure/spatial-anchors/)| ![Services Speech](features/images/mrdevcenter/icon-azurespeechservices.png) [Services Speech](/azure/cognitive-services/speech-service/)| ![Services Vision](features/images/mrdevcenter/icon-azurevisionservices.png) [Services Vision](/azure/cognitive-services/computer-vision/)|
| :------------------------| :--------------------- | :---------------------- |
| Spatial Anchors est un service multiplateforme qui vous permet de créer des expériences de réalité mixte à l’aide d’objets qui restent au même endroit sur tous les appareils.| Découvrez les fonctionnalités vocales Azure, telles que la reconnaissance vocale, la reconnaissance de l’orateur ou la traduction vocale, que vous pouvez intégrer à votre application.| Identifiez et analysez le contenu de vos images et de vos vidéos à l’aide des services de vision, tels que la vision par ordinateur, la détection des visages, la reconnaissance des émotions ou l’indexeur de vidéos. |

## <a name="how-to-contribute"></a>Marche à suivre pour contribuer

Découvrez comment vous pouvez contribuer à MRTK sur [Contribution](contributing/contributing.md).

## <a name="getting-help"></a>Obtenir de l’aide

Si vous rencontrez des problèmes dus à l’utilisation de MRTK ou si vous avez des questions sur la façon d’effectuer une opération, vous pouvez vous aider des différentes ressources disponibles :

* Pour signaler un bogue, veuillez [créer un incident](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) dans le dépôt GitHub.
* Pour toute question, veuillez consulter [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) ou le [canal mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) sur Slack. Vous pouvez rejoindre la communauté Slack par le biais de l’[envoi d’invitation automatique](https://holodevelopersslack.azurewebsites.net/).