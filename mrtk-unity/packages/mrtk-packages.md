---
title: Packages MRTK
description: Les packages dans MRTK prennent en charge le matériel et les plateformes de réalité mixte.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, unity Gestionnaire de package,
ms.openlocfilehash: 13f18c0a43d8b0cf6cc8eb66949b506c51ca9bbaa733e74cd38de110f70d8ee1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212562"
---
# <a name="mrtk-packages"></a>Packages MRTK

la Shared Computer Toolkit de la réalité mixte (MRTK) est une collection de packages qui permettent le développement d’applications de réalité mixte multiplateforme en fournissant une prise en charge du matériel et des plateformes de réalité mixte.

MRTK est disponible en tant que packages [asset](#asset-packages) (. pour unity) et par le biais du [Gestionnaire de package unity](#unity-package-manager).

## <a name="asset-packages"></a>Packages de composants

La ressource MRTK (. pour Unity) peut être téléchargée à partir de [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases).

Voici quelques-uns des avantages de l’utilisation des packages de ressources :

- Disponible pour Unity 2018,4 et versions ultérieures
- Modifications faciles à apporter à MRTK
  - MRTK se trouve dans le dossier composants

Voici quelques-unes des difficultés :

- MRTK fait partie du dossier de ressources du projet, qui mène à
  - Grands projets
  - Temps de compilation plus lents
- Aucune gestion des dépendances
  - Les clients doivent résoudre les dépendances de package manuellement
- Processus de mise à jour manuelle
  - Étapes multiples
  - Mises à jour de contrôle de code source volumineuses (3 000 fichiers)
  - Risque de perte des modifications apportées à MRTK
- L’importation du package d’exemples signifie généralement que tous les exemples

Les packages disponibles sont les suivants :

- [Pierre](#foundation-package)
- [Extensions](#extensions-package)
- [outils](#tools-package)
- [Utilitaires de test](#test-utilities-package)
- [Exemples](#examples-package)

Ces packages sont publiés et pris en charge par Microsoft à partir du code source dans la branche [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) sur GitHub.

### <a name="foundation-package"></a>Package de base

la réalité mixte Shared Computer Toolkit Foundation est l’ensemble de code qui permet à votre application de tirer parti des fonctionnalités communes sur les plateformes de réalité mixte.

<img src="../features/images/input/MRTK_Package_Foundation.png" width="350px" alt="Pakage foundation" style="display:block;">  
<sup>Package MRTK Foundation</sup>

Le package MRTK Foundation contient les éléments suivants.

| Dossier | Composant | Description |
| --- | --- | --- |
| MRTK/noyau | | Définitions d’interface et de type, classes de base, nuanceur standard. |
| MRTK/Core/Providers | | Fournisseurs de données agnostiques de la plateforme |
| | Leçon | Prise en charge et services de la classe de base pour le suivi de la main. |
| | [InputAnimation](../features/input-simulation/input-animation-recording.md) | Prise en charge du déplacement des têtes d’enregistrement et des données de suivi de la main. |
| | [InputSimulation](../features/input-simulation/input-simulation-service.md) | Prise en charge de la simulation et de l’entrée oculaire dans l’éditeur. |
| | [ObjectMeshObserver](../features/spatial-awareness/spatial-object-mesh-observer.md) | Observateur de sensibilisation spatiale utilisant un modèle 3D en tant que données. |
| | UnityInput | Périphériques d’entrée courants (joystick, souris, etc.) implémentés via l’API d’entrée Unity. |
| MRTK/fournisseurs | | Fournisseurs de données spécifiques à la plateforme |
| | LeapMotion | Prise en charge du contrôleur de mouvement LEAP UltraLeap. |
| | OpenVR | Prise en charge des appareils OpenVR. |
| | Oculus | Prise en charge des appareils Oculus, tels que Quest. |
| | [Unity](../features/camera-system/unity-ar-camera-settings.md) | Pratiqué Fournisseur de paramètres d’appareil photo permettant l’utilisation de MRTK avec des appareils mobiles. |
| | WindowsMixedReality | prise en charge des appareils Windows Mixed Reality, y compris les Microsoft HoloLens et les casques immersifs. |
| | Windows | la prise en charge de Microsoft Windows des api spécifiques, par exemple la reconnaissance vocale et la dictée. |
| | Kit de développement logiciel (SDK) XR | Pratiqué Prise en charge de [New XR Framework pour unity](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) 2019,3 et versions ultérieures. |
| MRTK/SDK | | |
| | Expérimental | Fonctionnalités expérimentales, notamment les nuanceurs, les contrôles d’interface utilisateur et les gestionnaires de système individuels. |
| | Fonctionnalités | Fonctionnalité qui s’appuie sur le package de base. |
| | Profils | profils par défaut pour les systèmes et services Shared Computer Toolkit de la réalité mixte Microsoft. |
| | StandardAssets | Ressources communes ; modèles, textures, matériaux, etc. |
| MRTK/SceneSystemResources | | Ressources et ressources utilisées par le système de scène |
| MRTK/services | | |
| | [BoundarySystem](../features/boundary/boundary-system-getting-started.md) | Système mettant en œuvre la prise en charge de la limite VR. |
| | [CameraSystem](../features/camera-system/camera-system-overview.md) | Le système implémente la configuration et la gestion de l’appareil photo. |
| | [DiagnosticsSystem](../features/diagnostics/diagnostics-system-getting-started.md) | Système implémentant dans application Diagnostics, par exemple un profileur Visual. |
| | [InputSystem](../features/input/overview.md) | Système assurant la prise en charge de l’accès et de la gestion des entrées utilisateur. |
| | [SceneSystem](../features/scene-system/scene-system-getting-started.md) | Système fournissant une prise en charge d’applications à plusieurs scènes. |
| | [SpatialAwarenessSystem](../features/spatial-awareness/spatial-awareness-getting-started.md) | Système assurant la prise en charge de l’environnement de l’utilisateur. |
| | [TeleportSystem](../features/teleport-system/teleport-system.md) | Système assurant la prise en charge du téléportage (en se sur l’expérience des sauts). |
| MRTK/StandardAssets | | Nuanceur standard MRTK, matériel de base et autres ressources standard pour les expériences de réalité mixte |

### <a name="extensions-package"></a>Package d’extensions

le package facultatif microsoft. MixedRealityToolkit. unity. Extensions comprend des services supplémentaires qui étendent les fonctionnalités de la Shared Computer Toolkit de réalité mixte microsoft.

> [!NOTE]
> Le package d’extensions requiert Microsoft. MixedRealityToolkit. Unity. Foundation.

| Dossier | Composant | Description |
| --- | --- | --- |
| MRTK/extensions | |
| | [HandPhysicsService](../features/extensions/hand-physics-service.md) | Service qui ajoute la prise en charge physique aux mains articulées. |
| | LostTrackingService | Service qui simplifie la gestion de la perte de suivi sur les appareils Microsoft HoloLens. |
| | [SceneTransitionService](../features/extensions/scene-transition-service.md) | Service qui simplifie l’ajout de transitions de scène lisses. |

### <a name="tools-package"></a>Package d’outils

le package facultatif microsoft. MixedRealityToolkit. unity. tools comprend des outils utiles qui améliorent l’expérience de développement de la réalité mixte à l’aide de la Shared Computer Toolkit de la réalité mixte Microsoft.
ces outils se trouvent dans le menu **Shared Computer Toolkit > utilitaires de la réalité mixte** de l’éditeur unity.

> [!NOTE]
> Le package d’outils requiert Microsoft. MixedRealityToolkit. Unity. Foundation.

| Dossier | Composant | Description |
| --- | --- | --- |
| MRTK/outils | |
| | BuildWindow | Outil qui permet de simplifier le processus de création et de déploiement d’applications UWP. |
| | [DependencyWindow](../features/tools/dependency-window.md) | Outil qui crée un graphique de dépendance des ressources dans un projet. |
| | [ExtensionServiceCreator](../features/tools/extension-service-creation-wizard.md) | Assistant pour faciliter la création de services d’extension. |
| | [MigrationWindow](../features/tools/migration-window.md) | Outil qui facilite la mise à jour du code qui utilise des composants MRTK déconseillés.  |
| | [OptimizeWindow](../features/tools/optimize-window.md) | Utilitaire permettant d’automatiser la configuration d’un projet de réalité mixte pour des performances optimales dans Unity. |
| | ReserializeAssetsUtility | Prend en charge la resérialisation de fichiers Unity spécifiques. |
| | [RuntimeTools/Tools/ControllerMappingTool](../features/tools/controller-mapping-tool.md) | Utilitaire permettant aux développeurs de déterminer rapidement les mappages Unity pour les contrôleurs de matériel. |
| | ScreenshotUtility | Permet de capturer des images d’application dans l’éditeur Unity. |
| | TextureCombinerWindow | Utilitaire pour combiner les textures de graphiques. |
| | [Boîte à outils](../features/ux-building-blocks/toolbox.md) | Interface utilisateur qui facilite la découverte et l’utilisation des composants MRTK UX. |

### <a name="test-utilities-package"></a>Package d’utilitaires de test

Le package facultatif Microsoft. MixedRealityToolkit. TestUtilities est une collection de scripts d’assistance qui permettent aux développeurs de [créer facilement des tests en mode lecture](../contributing/unit-tests.md#play-mode-tests). Ces utilitaires sont particulièrement utiles pour les développeurs qui créent des composants MRTK.

| Dossier | Composant | Description |
| --- | --- | --- |
| MRTK/tests | |
| | TestUtilities | Méthodes permettant de simplifier la création de tests en mode lecture, y compris les utilitaires de simulation manuelle. |

### <a name="examples-package"></a>Exemple de package

Le package d’exemples contient des démonstrations, des exemples de scripts et des exemples de scènes qui exercent des fonctionnalités dans le package de base. Ce package contient la [scène HandInteractionExample](../features/example-scenes/hand-interaction-examples.md) (illustrée ci-dessous) qui contient des exemples d’objets qui répondent à différents types d’entrée (articulée et non articulée).

![HandInteractionExample scène](../features/images/MRTK_Examples.png)

Ce package contient également des démonstrations de suivi oculaire, qui sont [documentées ici](../features/example-scenes/eye-tracking-examples-overview.md)

Plus généralement, toute nouvelle fonctionnalité de MRTK doit contenir un exemple correspondant dans le package d’exemples, en suivant à peu près la même structure de dossiers et l’emplacement.

> [!NOTE]
> Le package d’exemples requiert Microsoft. MixedRealityToolkit. Unity. Foundation.

| Dossier | Composant | Description |
| --- | --- | --- |
| MRTK/exemples | | |
| | Démonstrations | Scènes simples illustrant une ou deux fonctionnalités associées. |
| | Expérimental | Démonstrations illustrant des fonctionnalités expérimentales. |
| | StandardAssets | Ressources communes partagées par plusieurs scènes de démonstration. |

## <a name="unity-package-manager"></a>Gestionnaire de package unity

pour les expériences créées à l’aide d’unity 2019,4 et versions ultérieures, MRTK est disponible via [unity Gestionnaire de package](https://docs.unity3d.com/Manual/Packages.html).

Voici quelques-uns des avantages de l’utilisation des packages de ressources :

- Projets plus petits
  - solutions de Visual Studio de nettoyage
  - Moins de fichiers à archiver (MRTK est une référence simple dans le `Packages/manifest.json` fichier)
- Compilation plus rapide
  - Unity n’a pas besoin de recompiler MRTK pendant la génération
- Résolution des dépendances
  - Les packages MRTK requis sont installés automatiquement lors de la spécification des packages avec des dépendances
- Mise à jour facile vers les nouvelles versions de MRTK
  - Modifier la version dans le `Packages/manifest.json` fichier

Voici quelques-unes des difficultés :

- MRTK est immuable
  - Impossible d’apporter des modifications sans qu’elles soient supprimées pendant la résolution du package
- MRTK ne prend pas en charge les packages UPM avec Unity 2018,4

### <a name="foundation-package"></a>Package de base

le package de base ( `com.microsoft.mixedreality.toolkit.foundation` ) constitue la base de la réalité mixte Shared Computer Toolkit.

| Dossier | Composant | Description |
| --- | --- | --- |
| MRTK/noyau | | Définitions d’interface et de type, classes de base, nuanceur standard. |
| MRTK/Core/Providers | | Fournisseurs de données agnostiques de la plateforme |
| | Leçon | Prise en charge et services de la classe de base pour le suivi de la main. |
| | [InputAnimation](../features/input-simulation/input-animation-recording.md) | Prise en charge du déplacement des têtes d’enregistrement et des données de suivi de la main. |
| | [InputSimulation](../features/input-simulation/input-simulation-service.md) | Prise en charge de la simulation et de l’entrée oculaire dans l’éditeur. |
| | [ObjectMeshObserver](../features/spatial-awareness/spatial-object-mesh-observer.md) | Observateur de sensibilisation spatiale utilisant un modèle 3D en tant que données. |
| | UnityInput | Périphériques d’entrée courants (joystick, souris, etc.) implémentés via l’API d’entrée Unity. |
| MRTK/fournisseurs | | Fournisseurs de données spécifiques à la plateforme |
| | LeapMotion | Prise en charge du contrôleur de mouvement LEAP UltraLeap. |
| | OpenVR | Prise en charge des appareils OpenVR. |
| | Oculus | Prise en charge des appareils Oculus, tels que Quest. |
| | [Unity](../features/camera-system/unity-ar-camera-settings.md) | Pratiqué Fournisseur de paramètres d’appareil photo permettant l’utilisation de MRTK avec des appareils mobiles. |
| | WindowsMixedReality | prise en charge des appareils Windows Mixed Reality, y compris les Microsoft HoloLens et les casques immersifs. |
| | Windows | la prise en charge de Microsoft Windows des api spécifiques, par exemple la reconnaissance vocale et la dictée. |
| | Kit de développement logiciel (SDK) XR | Pratiqué Prise en charge de [New XR Framework pour unity](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) 2019,3 et versions ultérieures. |
| MRTK/SDK | | |
| | Expérimental | Fonctionnalités expérimentales, notamment les nuanceurs, les contrôles d’interface utilisateur et les gestionnaires de système individuels. |
| | Fonctionnalités | Fonctionnalité qui s’appuie sur le package de base. |
| | Profils | profils par défaut pour les systèmes et services Shared Computer Toolkit de la réalité mixte Microsoft. |
| | StandardAssets | Ressources communes ; modèles, textures, matériaux, etc. |
| MRTK/services | | |
| | [BoundarySystem](../features/boundary/boundary-system-getting-started.md) | Système mettant en œuvre la prise en charge de la limite VR. |
| | [CameraSystem](../features/camera-system/camera-system-overview.md) | Le système implémente la configuration et la gestion de l’appareil photo. |
| | [DiagnosticsSystem](../features/diagnostics/diagnostics-system-getting-started.md) | Système implémentant dans application Diagnostics, par exemple un profileur Visual. |
| | [InputSystem](../features/input/overview.md) | Système assurant la prise en charge de l’accès et de la gestion des entrées utilisateur. |
| | [SceneSystem](../features/scene-system/scene-system-getting-started.md) | Système fournissant une prise en charge d’applications à plusieurs scènes. |
| | [SpatialAwarenessSystem](../features/spatial-awareness/spatial-awareness-getting-started.md) | Système assurant la prise en charge de l’environnement de l’utilisateur. |
| | [TeleportSystem](../features/teleport-system/teleport-system.md) | Système assurant la prise en charge du téléportage (en se sur l’expérience des sauts). |

Dépendances :

- Ressources standard ( `com.microsoft.mixedreality.toolkit.standardassets` )

### <a name="standard-assets"></a>Ressources standard

Le package de ressources standard ( `com.microsoft.mixedreality.toolkit.standardassets)` est un ensemble de composants recommandés pour toutes les expériences de réalité mixte, y compris :

- Nuanceur standard MRTK
- Matériaux de base à l’aide du nuanceur standard MRTK
- Fichiers audio
- Polices
- Textures
- Icônes

> [!Note]
> Pour éviter toute modification avec rupture basée sur les définitions d’assembly, les scripts utilisés pour contrôler certaines fonctionnalités du nuanceur standard MRTK ne sont pas inclus dans le package de ressources standard. Ces scripts se trouvent dans le package de base dans le `MRTK/Core/Utilities/StandardShader` dossier.

Dépendances : aucune

### <a name="extension-packages"></a>Packages d'extension

Le package d’extensions facultatives ( `com.microsoft.mixedreality.toolkit.extensions)` contient des composants supplémentaires qui étendent les fonctionnalités de MRTK.

| Dossier | Composant | Description |
| --- | --- | --- |
| MRTK/extensions | |
| | [HandPhysicsService](../features/extensions/hand-physics-service.md) | Service qui ajoute la prise en charge physique aux mains articulées. |
| | LostTrackingService | Service qui simplifie le transfert des pertes de suivi sur les appareils Microsoft HoloLens. |
| | [SceneTransitionService](../features/extensions/scene-transition-service.md) | Service qui simplifie l’ajout de transitions de scène lisses. |
| | Échantillons ~ | Dossier caché (dans l’éditeur Unity) qui contient les scènes et les éléments multimédias de l’exemple. |

pour plus d’informations sur le processus d’utilisation des packages contenant des exemples de projets, consultez l’article Shared Computer Toolkit de la [réalité mixte et Gestionnaire de package unity](../configuration/usingupm.md#using-mixed-reality-toolkit-examples) .

Dépendances :

- Fondation ( `com.microsoft.mixedreality.toolkit.foundation` )

### <a name="tools-package"></a>Package d’outils

Le package d’outils facultatifs ( `com.microsoft.mixedreality.toolkit.tools)` contient des outils utiles pour créer des expériences de réalité mixte. En général, ces outils sont des composants d’éditeur et leur code n’est pas fourni dans le cadre d’une application.

| Dossier | Composant | Description |
| --- | --- | --- |
| MRTK/outils | |
| | BuildWindow | Outil qui permet de simplifier le processus de création et de déploiement d’applications UWP. |
| | [DependencyWindow](../features/tools/dependency-window.md) | Outil qui crée un graphique de dépendance des ressources dans un projet. |
| | [ExtensionServiceCreator](../features/tools/extension-service-creation-wizard.md) | Assistant pour faciliter la création de services d’extension. |
| | [MigrationWindow](../features/tools/migration-window.md) | Outil qui facilite la mise à jour du code qui utilise des composants MRTK déconseillés.  |
| | [OptimizeWindow](../features/tools/optimize-window.md) | Utilitaire permettant d’automatiser la configuration d’un projet de réalité mixte pour des performances optimales dans Unity. |
| | ReserializeAssetsUtility | Prend en charge la resérialisation de fichiers Unity spécifiques. |
| | [RuntimeTools/Tools/ControllerMappingTool](../features/tools/controller-mapping-tool.md) | Utilitaire permettant aux développeurs de déterminer rapidement les mappages Unity pour les contrôleurs de matériel. |
| | ScreenshotUtility | Permet de capturer des images d’application dans l’éditeur Unity. |
| | TextureCombinerWindow | Utilitaire pour combiner les textures de graphiques. |
| | [Boîte à outils](../features/ux-building-blocks/toolbox.md) | Interface utilisateur qui facilite la découverte et l’utilisation des composants MRTK UX. |

Dépendances :

- Fondation ( `com.microsoft.mixedreality.toolkit.foundation` )

### <a name="test-utilities-package"></a>Package d’utilitaires de test

Le package d’utilitaires de test facultatif ( `com.microsoft.mixedreality.toolkit.testutilities` ) contient une collection de scripts d’assistance qui permettent aux développeurs de créer facilement des tests en mode lecture. Ces utilitaires sont particulièrement utiles pour les développeurs qui créent des composants MRTK.

| Dossier | Composant | Description |
| --- | --- | --- |
| MRTK/tests | |
| | TestUtilities | Méthodes permettant de simplifier la création de tests en mode lecture, y compris les utilitaires de simulation manuelle. |

Dépendances :

- Fondation ( `com.microsoft.mixedreality.toolkit.foundation` )

### <a name="examples-package"></a>Exemple de package

Le package d’exemples ( `com.microsoft.mixedreality.toolkit.examples` ), est structuré pour permettre aux développeurs d’importer uniquement les exemples intéressants.

pour plus d’informations sur le processus d’utilisation des packages contenant des exemples de projets, consultez l’article Shared Computer Toolkit de la [réalité mixte et Gestionnaire de package unity](../configuration/usingupm.md#using-mixed-reality-toolkit-examples) .

| Dossier | Composant | Description |
| --- | --- | --- |
| MRTK/exemples | | |
| | Échantillons ~ | Dossier caché (dans l’éditeur Unity) qui contient les scènes et les éléments multimédias de l’exemple. |
| | StandardAssets | Ressources communes partagées par plusieurs scènes de démonstration. |

Dépendances :

- Fondation ( `com.microsoft.mixedreality.toolkit.foundation` )
- Extensions (`com.microsoft.mixedreality.toolkit.extensions`)

## <a name="see-also"></a>Voir aussi

- [Présentation de l'architecture](../architecture/overview.md)
- [Systèmes, services d’extension et fournisseurs de données](../architecture/systems-extensions-providers.md)
- [Shared Computer Toolkit de réalité mixte et Gestionnaire de package unity](../configuration/usingupm.md)
