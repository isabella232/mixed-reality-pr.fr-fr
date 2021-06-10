---
title: Guide de configuration de la réalité mixte
description: Documentation pour configurer MRTK dans Unity.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK,
ms.openlocfilehash: b714e01a0969b88a4ca7a3a5047bc5d61516e3f3
ms.sourcegitcommit: bb9f54f3e872a5464a5d9ba88b7ab5b8896efd82
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/25/2021
ms.locfileid: "110345142"
---
# <a name="mixed-reality-toolkit-profile-configuration-guide"></a>Guide de configuration du profil du Toolkit de réalité mixte

![Logo MRTK](../features/images/MRTK_Logo_Rev.png)

La boîte à outils de réalité mixte centralise la plus grande partie de la configuration requise pour gérer le kit de tâches (à l’exception des « choses » du véritable Runtime).

Ce guide est une procédure pas à pas simple pour chacun des écrans de profil de configuration actuellement disponibles pour la boîte à outils.

## <a name="the-main-mixed-reality-toolkit-configuration-profile"></a>Profil de configuration principal de la réalité mixte

Le profil de configuration principal, qui est attaché au gameobject *MixedRealityToolkit* dans votre scène, fournit le point d’entrée principal de la boîte à outils dans votre projet.

> [!NOTE]
> La boîte à outils de réalité mixte « verrouille » les écrans de configuration par défaut pour s’assurer que vous avez toujours un point de départ commun pour votre projet et il est recommandé de commencer à définir vos propres paramètres à mesure que votre projet évolue. La configuration MRTK n’est pas modifiable en mode lecture.

![Profil de configuration MRTK](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ActiveConfiguration.png)

Tous les profils « par défaut » pour la réalité mixte Toolkit se trouvent dans le projet SDK dans le dossier ressources/MRTK/Kit de développement logiciel (SDK)/profils.

> [!IMPORTANT]
> DefaultHoloLens2ConfigurationProfile est optimisé pour HoloLens 2. Pour plus d’informations, consultez [profils](../features/profiles/profiles.md) .

Lorsque vous ouvrez le profil de configuration principal de la réalité mixte, l’écran suivant s’affiche dans l’inspecteur :

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_MixedRealityToolkitConfigurationScreen.png" width="650px" alt="MRTK configuration scene" style="display:block;">

Si vous sélectionnez un élément multimédia MixedRealityToolkitConfigurationProfile sans MixedRealityToolkit dans la scène, vous êtes invité à indiquer si vous souhaitez que le MRTK configure automatiquement la scène pour vous. Toutefois, cette option est facultative, mais un objet MixedRealityToolkit actif doit être présent dans la scène pour accéder à tous les écrans de configuration.

Cela abrite la configuration active Runtime actuelle pour le projet.

À partir de là, vous pouvez accéder à tous les profils de configuration pour le MRTK, notamment :

- [Guide de configuration du profil du Toolkit de réalité mixte](#mixed-reality-toolkit-profile-configuration-guide)
  - [Profil de configuration principal de la réalité mixte](#the-main-mixed-reality-toolkit-configuration-profile)
  - [Paramètres d’expérience](#experience-settings)
  - [Paramètres de l’appareil photo](#camera-settings)
  - [Paramètres du système d’entrée](#input-system-settings)
  - [Paramètres de visualisation des limites](#boundary-visualization-settings)
  - [Sélection du système de téléporting](#teleportation-system-selection)
  - [Paramètres de sensibilisation spatiale](#spatial-awareness-settings)
  - [Paramètres de diagnostic](#diagnostics-settings)
  - [Paramètres système de la scène](#scene-system-settings)
  - [Paramètres des services supplémentaires](#additional-services-settings)
  - [Paramètres des actions d’entrée](#input-actions-settings)
  - [Règles d’actions d’entrée](#input-actions-rules)
  - [Configuration du pointeur](#pointer-configuration)
  - [Configuration des mouvements](#gestures-configuration)
  - [Commandes vocales](#speech-commands)
  - [Configuration du mappage du contrôleur](#controller-mapping-configuration)
  - [Paramètres de visualisation du contrôleur](#controller-visualization-settings)
  - [Utilitaires de l’éditeur](#editor-utilities)
    - [Inspecteurs de service](#service-inspectors)
    - [Convertisseur de mémoire tampon de profondeur](#depth-buffer-renderer)
  - [Modification des profils au moment de l’exécution](#changing-profiles-at-runtime)
    - [Commutateur de profil d’initialisation de pré MRTK](#pre-mrtk-initialization-profile-switch)
    - [Commutateur de profil actif](#active-profile-switch)
  - [Voir aussi](#see-also)

Ces profils de configuration sont détaillés ci-dessous dans les sections qui s’y rapportent :

---
<a name="experience"></a>

## <a name="experience-settings"></a>Paramètres d’expérience

Situé sur la page de configuration principale de l’ensemble d’outils de réalité mixte, ce paramètre définit l’opération par défaut de l’échelle de l’environnement de la [réalité mixte](/windows/mixed-reality/coordinate-systems-in-unity) pour votre projet.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ExperienceSettings.png" width="650px" alt="Experiance settings" style="display:block;">

---
<a name="camera"></a>

## <a name="camera-settings"></a>Paramètres de caméra

Les paramètres de l’appareil photo définissent la façon dont l’appareil photo sera configuré pour votre projet de réalité mixte, définissant les paramètres génériques de découpage, de qualité et de transparence.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_CameraProfile.png" width="650px" alt="Camera Profile" style="display:block;">

---
<a name="inputsystem"></a>

## <a name="input-system-settings"></a>Paramètres du système d’entrée

Le projet de réalité mixte fournit un système d’entrée robuste et bien formé pour le routage de tous les événements d’entrée dans le projet, qui est sélectionné par défaut.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemSelection.png" width="650px" alt="Input System settings 1" style="display:block;">

Derrière le système d’entrée fourni par le MRTK sont plusieurs autres systèmes, ils aident à piloter et à gérer les intertissages complexes nécessaires à l’abstraction de la complexité d’une infrastructure de réalité multiplateforme/de réalité mixte.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemProfile.png" width="650px" alt="Input System settings 2" style="display:block;">

Chacun des profils individuels est détaillé ci-dessous :

- Paramètres de focus
- [Paramètres des actions d’entrée](#input-actions-settings)
- [Règles d’actions d’entrée](#input-actions-rules)
- [Configuration du pointeur](#pointer-configuration)
- [Configuration des mouvements](#gestures-configuration)
- [Commandes vocales](#speech-commands)
- [Configuration du mappage du contrôleur](#controller-mapping-configuration)
- [Paramètres de visualisation du contrôleur](#controller-visualization-settings)

---
<a name="boundary"></a>

## <a name="boundary-visualization-settings"></a>Paramètres de visualisation des limites

Le système de limites traduit la limite perçue signalée par le système de limite/Guardian des plateformes sous-jacentes. La configuration du visualiseur de limites vous donne la possibilité d’afficher automatiquement la limite enregistrée dans votre scène, en fonction de la position de l’utilisateur. La limite réagit également/met à jour en fonction de l’endroit où l’utilisateur téléporte dans la scène.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_BoundaryVisualizationProfile.png" width="650px" alt="Boundry Visualization Settings" style="display:block;">

---
<a name="teleportation"></a>

## <a name="teleportation-system-selection"></a>Sélection du système de téléporting

Le projet de réalité mixte fournit un système de téléportage complet pour la gestion des événements de téléportage dans le projet, qui est sélectionné par défaut.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_TeleportationSystemSelection.png" width="650px" alt="Teleport System settings" style="display:block;">

---
<a name="spatialawareness"></a>

## <a name="spatial-awareness-settings"></a>Paramètres de sensibilisation spatiale

Le projet de réalité mixte fournit un système de sensibilisation spatiale reconstruit pour travailler avec des systèmes d’analyse spatiale dans le projet, qui est sélectionné par défaut.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessSystemSelection.png" width="650px" alt="Spatial Awareness settings 1" style="display:block;">

La configuration de la sensibilisation spatiale de la réalité mixte vous permet de personnaliser le mode de démarrage du système, s’il est exécuté automatiquement au démarrage de l’application ou par la suite, et de définir les étendues du champ de la vue.

Il vous permet également de configurer les paramètres de maillage et de surface, de personnaliser davantage la façon dont votre projet comprend l’environnement qui vous est autour.

Cela s’applique uniquement aux appareils qui peuvent fournir un environnement analysé.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessProfile.png" width="650px" alt="Spatial Awareness settings 2" style="display:block;">

---
<a name="diagnostic"></a>

## <a name="diagnostics-settings"></a>Paramètres de diagnostic

Une fonctionnalité facultative mais très utile du MRTK est la fonctionnalité de diagnostics de plug-in.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsSystemSelection.png" width="650px" alt="Diagnostics settings" style="display:block;">

Le profil de diagnostic fournit plusieurs systèmes simples à surveiller pendant l’exécution du projet, y compris un commutateur d’activation/désactivation pratique pour activer/désactiver le panneau d’affichage dans la scène.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsProfile.png" width="650px" alt="Diagnostics settings System settings 2" style="display:block;">

---
<a name="scenesystem"></a>

## <a name="scene-system-settings"></a>Paramètres système de la scène

Le MRTK fournit ce service facultatif pour vous aider à gérer le chargement/déchargement complexe des scènes. Pour déterminer si le système de scène est adapté à votre projet, lisez le Guide de [prise en main du système de scène.](../features/scene-system/scene-system-getting-started.md)

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SceneSystemProfile.png" width="650px" alt="Scene System settings 1" style="display:block;">

---
<a name="services"></a>

## <a name="additional-services-settings"></a>Paramètres des services supplémentaires

L’une des zones les plus avancées du kit d’outils de réalité mixte est son implémentation de [modèle de localisateur de service](https://en.wikipedia.org/wiki/Service_locator_pattern) qui permet d’inscrire n’importe quel « service » avec l’infrastructure. Cela permet d’étendre facilement le Framework avec de nouvelles fonctionnalités et de nouveaux systèmes, mais permet également aux projets de tirer parti de ces fonctionnalités pour inscrire leurs propres composants d’exécution.

Tout service inscrit obtient toujours l’avantage total de tous les événements Unity, sans la surcharge et le coût de l’implémentation d’un monocomportement ou de modèles de singletons sourds. Cela permet aux composants C# purs sans surcharge de scène d’exécuter à la fois les processus de premier plan et d’arrière-plan, par exemple les systèmes de génération, la logique du jeu d’exécution ou pratiquement tout autre.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_RegisteredServiceProvidersProfile.png" width="650px" alt="additional System settings" style="display:block;">

---
<a name="inputactions"></a>

## <a name="input-actions-settings"></a>Paramètres des actions d’entrée

Les actions d’entrée permettent d’extraire les interactions physiques et les entrées d’un projet d’exécution. Toutes les entrées physiques (des contrôleurs/mains/souris, etc.) sont traduites en une action d’entrée logique pour une utilisation dans votre projet d’exécution. Cela garantit quel que soit l’emplacement d’origine de l’entrée, votre projet implémente simplement ces actions comme « choses à faire » ou « interagir avec » dans vos scènes.

Pour créer une nouvelle action d’entrée, cliquez simplement sur le bouton « Ajouter une nouvelle action », puis entrez un nom convivial pour ce qu’elle représente. Vous devez alors uniquement sélectionner un axe (le type de données) que l’action doit transmettre, ou, dans le cas de contrôleurs physiques, le type d’entrée physique auquel elle peut être jointe, par exemple :

| Contrainte d’axe | Type de données | Description | Exemple d’utilisation |
| :--- | :--- | :--- | :--- |
| Aucun | Pas de données | Utilisé pour une action ou un événement vide | Déclencheur d’événement |
| Brut (réservé) | object | Paramètres réservés pour un usage ultérieur | N/A |
| Digital | bool | Données de type Boolean on ou OFF | Bouton de contrôleur |
| Axe unique | float | Une valeur de données de précision unique | Une entrée étendue, par exemple un déclencheur |
| Axe double | Vector2 | Une date de type float double pour plusieurs axes | Un dpad ou un stick analogique |
| Trois positions DDL | Vector3 | Données de type positionnel de à l’aide de l’axe 3 flottant | contrôleur de style de position 3D uniquement |
| Rotation à trois DDL | Quaternion | Entrée de rotation uniquement avec 4 axes à virgule flottante | Un contrôleur de style à trois degrés, par exemple Oculus Go Controller |
| Six DDL | Pose de réalité mixte (Vector3, Quaternion) | Entrée de style de position et de rotation avec les composants Vector3 et Quaternion | Contrôleur de mouvement ou pointeur |

Les événements qui utilisent des actions d’entrée ne sont pas limités aux contrôleurs physiques et peuvent toujours être utilisés dans le projet pour que les effets de Runtime génèrent de nouvelles actions.

> [!NOTE]
> Les actions d’entrée sont l’un des quelques composants qui ne peuvent pas être modifiés au moment de l’exécution ; ils ne sont qu’une configuration au moment du Design. Ce profil ne doit pas être échangé pendant que le projet est en cours d’exécution en raison de la dépendance entre l’infrastructure (et vos projets) et l’ID généré pour chaque action.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionsProfile.png" width="650px" alt="Configuration Profile" style="display:block;">

---
<a name="inputactionrules"></a>

## <a name="input-actions-rules"></a>Règles d’actions d’entrée

Les règles d’action d’entrée permettent de traduire automatiquement un événement déclenché pour une action d’entrée en différentes actions en fonction de sa valeur de données. Celles-ci sont gérées en toute transparence dans le cadre et n’entraînent pas de coûts de performances.

Par exemple, la conversion de l’événement d’entrée d’un seul axe double à partir d’un DPad dans en 4 actions « dpad up »/« DPad OFF »/« dpad Left »/« dpad Right » correspondantes (comme indiqué dans l’image ci-dessous).

Cela peut également se faire dans votre propre code. Toutefois, comme il s’agit d’un modèle très courant, le Framework fournit un mécanisme permettant d’effectuer cette opération « prête à l’emploi »

Les règles d’action d’entrée peuvent être configurées pour l’un des axes d’entrée disponibles. Toutefois, les actions d’entrée d’un type d’axe peuvent être traduites en une autre action d’entrée du même type d’axe. Vous pouvez mapper une action à deux axes sur une autre action d’axe double, mais pas sur une action numérique ou aucune.

![Profil des règles d’action d’entrée](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionRulesProfile.png)

---
<a name="pointer"></a>

## <a name="pointer-configuration"></a>Configuration du pointeur

Les pointeurs sont utilisés pour piloter l’interactivité dans la scène à partir de n’importe quel appareil d’entrée, ce qui donne à la fois une direction et un test de positionnement avec n’importe quel objet dans une scène (qui a un conflit attaché ou est un composant d’interface utilisateur). Les pointeurs sont configurés automatiquement par défaut pour les contrôleurs, les casques (en regard/Focus) et l’entrée de souris/toucher.

Les pointeurs peuvent également être visualisés dans la scène active à l’aide de l’un des nombreux composants de ligne fournis par le Toolkit de réalité mixte, ou de l’un de vos propres composants s’ils implémentent l’interface MRTK IMixedRealityPointer.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputPointerProfile.png" width="650px" alt="Input Pointer Profile" style="display:block;">

- Étendue de pointage : détermine l’étendue de pointage globale pour tous les pointeurs, y compris le point de regard.
- Pointer les masques de couche Raycast : détermine les pointeurs de couches à Raycast.
- Déboguer les rayons de pointage : un programme d’assistance de débogage pour visualiser les rayons utilisés pour Raycasting.
- Déboguer les rayons de pointage de couleur : un ensemble de couleurs à utiliser pour la visualisation.
- Curseur en regard Prefab : permet de spécifier facilement un curseur en forme de pointage global pour une scène.

Il existe un autre bouton d’assistance pour accéder rapidement au fournisseur de regard pour remplacer des valeurs spécifiques pour le point de regard, si nécessaire.

---
<a name="gestures"></a>

## <a name="gestures-configuration"></a>Configuration des mouvements

Les gestes sont une implémentation spécifique au système qui vous permet d’affecter des actions d’entrée aux diverses méthodes d’entrée de « geste » fournies par divers kits de développement logiciel (par exemple, HoloLens).

> [!NOTE]
> L’implémentation des mouvements actuels concerne le HoloLens uniquement et sera améliorée pour les autres systèmes, car ils seront ajoutés à la boîte à outils à l’avenir (aucune date pour le moment).

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_GesturesProfile.png" width="650px" alt="Gesture configuration" style="display:block;">

---
<a name="speech"></a>

## <a name="speech-commands"></a>Commandes vocales

À l’instar des gestes, certaines plateformes Runtime fournissent également une fonctionnalité de « parole à texte » intelligente, avec la possibilité de générer des commandes qui peuvent être reçues par un projet Unity. Ce profil de configuration vous permet de configurer les éléments suivants :

1. Paramètres généraux : « comportement de démarrage » défini sur démarrage automatique ou démarrage manuel détermine s’il faut initialiser KeywordRecognizer au démarrage du système d’entrée ou laisser le projet décider quand initialiser le KeywordRecognizer. « Niveau de confiance de reconnaissance » est utilisé pour initialiser l' [API KeywordRecognizer](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html) de l’unité
2. Commandes vocales : enregistre les « mots » et les convertit en actions d’entrée qui peuvent être reçues par votre projet. Ils peuvent également être joints aux actions du clavier, si nécessaire.

> [!IMPORTANT]
> Actuellement, le système ne prend en charge que la reconnaissance vocale sur les plateformes Windows 10, par exemple HoloLens et Windows 10 Desktop. il sera amélioré pour les autres systèmes tels qu’ils sont ajoutés à MRTK à l’avenir (aucune date n’est encore).

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpeechCommandsProfile.png" width="650px" alt="Configuration Profile screens" style="display:block;">

---
<a name="mapping"></a>

## <a name="controller-mapping-configuration"></a>Configuration du mappage du contrôleur

L’un des écrans de configuration principaux pour la réalité mixte Toolkit est la possibilité de configurer et de mapper les différents types de contrôleurs qui peuvent être utilisés par votre projet.

L’écran de configuration ci-dessous vous permet de configurer les contrôleurs actuellement reconnus par la boîte à outils.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerMappingProfile.png" width="650px" alt="Controller Mapping" style="display:block;">

MRTK fournit une configuration par défaut pour les contrôleurs/systèmes suivants :

- Souris (y compris la prise en charge de la souris spatiale 3D)
- Touch Screen
- Manettes Xbox
- Contrôleurs de réalité mixte Windows
- Gestes HoloLens
- Contrôleurs à baguettes vives HTC
- Contrôleurs tactiles Oculus
- Contrôleur distant Oculus
- Appareils OpenVR génériques (utilisateurs expérimentés uniquement)

En cliquant sur l’image de l’un des systèmes de contrôleur prédéfinis, vous pouvez configurer une seule action d’entrée pour toutes les entrées correspondantes. par exemple, consultez l’écran de configuration du contrôleur tactile Oculus ci-dessous :

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_WindowsMixedRealityControllerConfigScreen.png" width="650px" alt="Controller config screen" style="display:block;">

Il existe également un écran avancé pour la configuration d’autres contrôleurs d’entrée OpenVR ou Unity qui ne sont pas identifiés ci-dessus.

---
<a name="visualization"></a>

## <a name="controller-visualization-settings"></a>Paramètres de visualisation du contrôleur

En plus du mappage de contrôleur, un profil de configuration distinct est fourni pour personnaliser la façon dont vos contrôleurs sont présentés dans vos scènes.

Cela peut être configuré à un « global » (toutes les instances d’un contrôleur pour une main spécifique) ou spécifique à un type ou à une main de contrôleur individuel.

MRTK prend également en charge les modèles de contrôleur SDK natifs pour Windows Mixed Reality et OpenVR. Ceux-ci sont chargés en tant que GameObjects dans votre scène et positionnés à l’aide du suivi du contrôleur de la plateforme.

Si la représentation de votre contrôleur dans la scène doit être décalée à partir de la position du contrôleur physique, il suffit de définir ce décalage par rapport à l’Prefab du modèle de contrôleur (par exemple, en définissant la position de la transformation du Prefab du contrôleur avec une position de décalage).

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerVisualizationProfile.png" width="650px" alt="Visualization profile" style="display:block;">

<a name="editor-utilities"></a>

## <a name="editor-utilities"></a>Utilitaires de l’éditeur

Les utilitaires suivants fonctionnent uniquement dans l’éditeur et sont utiles pour améliorer la productivité du développement.

![Utilitaires de configuration de l’éditeur MRTK](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_EditorConfiguration.png)

### <a name="service-inspectors"></a>Inspecteurs de service

Les inspecteurs de service sont une fonctionnalité d’éditeur uniquement qui génère des objets dans la scène représentant des services actifs. La sélection de ces objets permet d’afficher les inspecteurs qui proposent des liens vers la documentation, de contrôler les visualisations de l’éditeur et de comprendre l’état du service.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ServiceInspectors.PNG" width="350px" alt="Service Inspectors" style="display:block;">

Vous pouvez activer les inspecteurs de service en cochant la case *utiliser les inspecteurs de service* sous paramètres de l' *éditeur* dans le profil de configuration.

### <a name="depth-buffer-renderer"></a>Convertisseur de mémoire tampon de profondeur

Le partage de la mémoire tampon de profondeur avec certaines plateformes de réalité mixte peut améliorer la [stabilisation des hologrammes](../performance/hologram-stabilization.md). Par exemple, la plateforme Windows Mixed Reality peut modifier la scène rendue par pixel pour tenir compte des mouvements de têtes subtiles pendant le temps nécessaire pour afficher un frame. Toutefois, ces techniques requièrent des tampons de profondeur avec des données précises pour savoir où et dans quelle mesure la géométrie provient de l’utilisateur.

Pour s’assurer qu’une scène effectue le rendu de toutes les données nécessaires dans le tampon de profondeur, les développeurs peuvent basculer la fonctionnalité de *tampon de profondeur de rendu* sous les paramètres de l' *éditeur* dans le profil de configuration. Cela prend la mémoire tampon de profondeur actuelle et l’affiche en couleur dans l’affichage scène en appliquant un effet de suivi, [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer) à l’appareil photo principal.

![Utilitaire de tampon ](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
 <sup>de profondeur de rendu le cylindre bleu dans la scène a un matériau avec ZWrite désactivé, donc aucune donnée de profondeur n’est écrite</sup>

## <a name="changing-profiles-at-runtime"></a>Modification des profils au moment de l’exécution

Il est possible de mettre à jour les profils au moment de l’exécution, et il y a généralement deux scénarios et périodes différents dans lesquels cela est utile :

1. **Commutateur de configuration d’initialisation avant MRTK**: au démarrage, avant l’initialisation du MRTK, le profil devient actif, en remplaçant le profil qui n’est pas encore utilisé pour activer ou désactiver les différentes fonctionnalités en fonction des fonctionnalités de l’appareil. Par exemple, si l’expérience s’exécute en VR qui n’a pas de matériel de mappage spatial, il n’est probablement pas judicieux d’activer le composant de mappage spatial.
1. **Commutateur de profil actif**: après le démarrage, une fois que le MRTK est initialisé et qu’un profil est devenu actif, échangez le profil actuellement utilisé pour modifier la façon dont certaines fonctionnalités se comportent. Par exemple, il peut y avoir une sous-expérience spécifique dans l’application qui souhaite que les pointeurs les plus éloignés soient complètement supprimés.

### <a name="pre-mrtk-initialization-profile-switch"></a>Commutateur de profil d’initialisation de pré MRTK

Pour ce faire, vous pouvez attacher un monocomportement (exemple ci-dessous) qui s’exécute avant l’initialisation MRTK (c.-à-d. éveillé ()). Notez que le script (c’est-à-dire l’appel à `SetProfileBeforeInitialization` ) doit être exécuté avant le `MixedRealityToolkit` script, ce qui peut être effectué en définissant des paramètres d’ordre d’exécution de [script](https://docs.unity3d.com/Manual/class-MonoManager.html).

```csharp
using Microsoft.MixedReality.Toolkit;
using UnityEngine;

/// <summary>
/// Sample MonoBehaviour that will run before the MixedRealityToolkit object, and change
/// the profile, so that when the MRTK initializes it uses the profile specified below
/// rather than the one that is saved in its scene.
/// </summary>
/// <remarks>
/// Note that this script must have a higher priority in the script execution order compared
/// to that of MixedRealityToolkit.cs. See https://docs.unity3d.com/Manual/class-MonoManager.html
/// for more information on script execution order.
/// </remarks>
public class PreInitProfileSwapper : MonoBehaviour
{

    [SerializeField]
    private MixedRealityToolkitConfigurationProfile profileToUse = null;

    private void Awake()
    {
        // Here you could choose any arbitrary MixedRealityToolkitConfigurationProfile (for example, you could
        // add some platform checking code here to determine which profile to load).
        MixedRealityToolkit.SetProfileBeforeInitialization(profileToUse);
    }
}
```

Au lieu de « profileToUse », il est possible d’avoir un ensemble arbitraire de profils qui s’appliquent à des plateformes spécifiques (par exemple, une pour HoloLens 1, une pour VR, une pour HoloLens 2, etc.). Il est possible d’utiliser d’autres indicateurs (par exemple https://docs.unity3d.com/ScriptReference/SystemInfo.html , ou si l’appareil photo est opaque/transparent), pour déterminer le profil à charger.

### <a name="active-profile-switch"></a>Commutateur de profil actif

Pour ce faire, vous pouvez affecter `MixedRealityToolkit.Instance.ActiveProfile` à la propriété un nouveau profil qui remplace le profil actif.

```csharp
MixedRealityToolkit.Instance.ActiveProfile = profileToUse;
```

Remarque Lorsque vous définissez au moment de l' `ActiveProfile` exécution, la destruction des services en cours d’exécution se produit après le dernier LateUpdate () de tous les services, et l’instanciation et l’initialisation des services associés au nouveau profil se produisent avant la première mise à jour () de tous les services.

Une hésitation d’application notable peut se produire au cours de ce processus. En outre, tout script avec une priorité plus élevée que le `MixedRealityToolkit` script peut entrer dans sa mise à jour avant que le nouveau profil soit correctement configuré. Pour plus d’informations sur la priorité de script, consultez [paramètres de l’ordre d’exécution des scripts](https://docs.unity3d.com/Manual/class-MonoManager.html) .

Dans le processus de basculement de profil, l’appareil photo de l’interface utilisateur existante reste inchangé, ce qui garantit que les composants de l’interface utilisateur Unity qui nécessitent un canevas fonctionnent toujours après le commutateur.

## <a name="see-also"></a>Voir aussi

- [Stabilisation d’hologramme](../performance/hologram-stabilization.md)