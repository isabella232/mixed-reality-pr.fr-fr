---
title: Notes de publication de MRTK 2,6
description: Notes de publication pour MRTK version 2,6
author: polar-kev
ms.author: kesemple
ms.date: 05/27/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK,
ms.openlocfilehash: 452f0f352443620dea70b1680859bab4e2b3a0818de5f130accdb84c2798cfe0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115206702"
---
# <a name="microsoft-mixed-reality-toolkit-26-release-notes"></a>notes de publication de Microsoft Mixed reality Shared Computer Toolkit 2,6

> [!IMPORTANT]
> un problème connu du compilateur affecte les applications générées pour Microsoft HoloLens 2 à l’aide de ARM64. ce problème est résolu par la mise à jour de Visual Studio 2019 vers la version 16,8 ou ultérieure. si vous ne parvenez pas à mettre à jour Visual Studio, importez le `com.microsoft.mixedreality.toolkit.tools` package pour appliquer une solution de contournement.

## <a name="whats-new-in-262"></a>Nouveautés de 2.6.2

### <a name="corrects-parenting-of-the-spatial-mesh"></a>Corrige le parent du maillage spatial

Résout le [problème](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9819) où les maillages spatiaux ne se trouvaient pas correctement après le déplacement de l’objet PlaySpace de la réalité mixte (par exemple, via une téléporte).

## <a name="whats-new-in-261"></a>Nouveautés de 2.6.1

### <a name="fixes-openxr-not-running-on-hololens-2--uwp"></a>résout OpenXR ne s’exécutant pas sur HoloLens 2/UWP

Résout une régression qui a empêché l’exécution de la prise en charge OpenXR de MRTK sur UWP.

### <a name="fixes-leap-motion-objectmanipulator-not-rotating"></a>Résout le mouvement LEAP ObjectManipulator pas de rotation

Corrige une régression dans laquelle la rotation d’une main de mouvement LEAP n’a pas été prise en compte par le script ObjectManipulator.

### <a name="sample-scene-updates"></a>Exemples de mises à jour de scènes

Met à jour l’exemple de scène de compréhension de scène pour refléter correctement l’état de livraison du plug-in Unity. Met également à jour l’exemple pour qu’il n’y ait plus de dépendance sur l’exemple de scène de sensibilisation spatiale en cours d’importation. Avant de procéder à la mise à jour vers la vue 2.6.1, vous devez supprimer les exemples de compréhension des scènes et de sensibilisation spatiales importés s’ils sont présents dans votre projet pour éviter les conflits éventuels. Si vous n’avez pas supprimé ces exemples et que vous voyez des conflits liés à ceux-ci dans la console, supprimez les deux exemples (ou le `Assets/Samples/Mixed Reality Toolkit Examples` dossier), puis recommencez l’importation.

Met à jour la scène de l’exemple de boîte de dialogue pour décrire correctement les scénarios de dialogue en cours.

## <a name="whats-new-in-260"></a>Nouveautés de 2.6.0

<iframe width="940" height="530" src="https://www.youtube.com/embed/qfONlUCSWdg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<br>

### <a name="add-support-for-openxr"></a>Ajouter la prise en charge de OpenXR

La prise en charge initiale du package OpenXR d’Unity Preview et du package OpenXR de la réalité mixte de Microsoft a été ajoutée. Pour plus d’informations, consultez [la page de prise en main de MRTK/XRSDK, la](../configuration/getting-started-with-mrtk-and-xrsdk.md) [publication du Forum Unity](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/)ou la [documentation de Microsoft](/windows/mixed-reality/develop/unity/openxr-getting-started) .

> [!IMPORTANT]
> OpenXR dans Unity est pris en charge uniquement sur Unity 2020,2 et les versions ultérieures.
>
> Actuellement, il prend également en charge uniquement les versions x64 et ARM64.

### <a name="asset-swap-utility"></a>Utilitaire d’échange de ressources

Échangez plusieurs éléments multimédias dans une scène Unity avec le nouvel [utilitaire d’échange de ressources](../features/tools/asset-swap-utility.md).

### <a name="hp-motion-controllers-now-supported-with-mrtk"></a>Contrôleurs de mouvement HP désormais pris en charge avec MRTK

Les contrôleurs de la réverbération HP G2 fonctionnent à présent en mode natif avec MRTK.

### <a name="experimental-interactive-element--state-visualizer"></a>Visualiseur d’État et d’élément interactif expérimental

L’élément interactif est un point d’entrée centralisé simplifié dans le système d’entrée MRTK. Elle contient des méthodes de gestion d’État, la gestion des événements et la logique de paramétrage d’État pour les États d’interaction de base. Pour plus d’informations, consultez [la documentation sur les éléments interactifs](../features/experimental/interactive-element.md).

![InteractiveElementAddCoreState](../features/images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

Le visualiseur d’État est un composant d’animation qui dépend d’un élément interactif. Ce composant crée des clips d’animation, définit les images clés et génère une machine à États d’animation. Pour plus d’informations, consultez [la documentation relative au visualiseur d’État](../features/experimental/interactive-element.md#state-visualizer-experimental)

![StateVisualizerColorChangeOnFocus](../features/images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="teleportation-with-the-teleport-gesture-now-supported-on-all-platforms"></a>Téléportage avec le geste de téléchargement pris en charge sur toutes les plateformes

Les utilisateurs peuvent désormais utiliser le geste de télédiffusion pour se déplacer dans leur espace de lecture sur toutes les plateformes. Pour vous téléporter avec un contrôleur sur des appareils MR avec des configurations par défaut, utilisez le stick analogique. Pour vous téléporter avec des mains articulées, rendez un geste avec votre paume face à l’index et faites-le pointer vers l’extérieur, en effectuant la télétentative en faisant évoluer le doigt de l’index. Pour vous téléporter avec la simulation d’entrée, consultez notre documentation sur le [service de simulation d’entrée](../features/input-simulation/input-simulation-service.md)mis à jour.

![Geste de](../features/images/teleport/handteleport.gif)

### <a name="scene-understanding-now-available-in-mrtk-as-an-experimental-spatial-awareness-observer"></a>Compréhension de scène désormais disponible dans MRTK comme observateur expérimental de sensibilisation spatiale

La prise en charge expérimentale de la [compréhension des scènes](/windows/mixed-reality/scene-understanding) est introduite dans MRTK 2,6. les utilisateurs peuvent intégrer les fonctionnalités de HoloLens 2 comme un observateur de sensibilisation spatiale dans des projets basés sur MRTK. Pour plus d’informations, consultez la documentation sur la compréhension de la [scène](../features/spatial-awareness/scene-understanding.md) .

> [!IMPORTANT]
> la compréhension des scènes est uniquement prise en charge sur les HoloLens 2 et unity 2019,4 et versions ultérieures.
>
> Cette fonctionnalité nécessite le package de compréhension de scène, qui est désormais disponible via l’outil de la [fonctionnalité de réalité mixte](https://aka.ms/MRFeatureTool).
> Lors de l’utilisation de l’outil de fonctionnalité de réalité mixte ou de l’importation via UPM, importez l’exemple de démonstrations-SpatialAwareness avant d’importer l’exemple expérimental-SceneUnderstanding en raison d’un problème de dépendance. pour plus d’informations, consultez [ce GitHub problème](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) .

![Compréhension des scènes](images/SceneUnderstanding.gif)

### <a name="runtime-profile-switching-support"></a>Prise en charge du changement de profil d’exécution

MRTK permet maintenant le basculement de profil avant l’initialisation de l’instance MRTK (par exemple, le commutateur de configuration d’initialisation MRTK) et une fois qu’un profil est en cours d’utilisation (par exemple, le commutateur de profil actif). Le commutateur précédent peut être utilisé pour activer les composants sélectionnés en fonction des capacités du matériel, tandis que le second peut être utilisé pour modifier l’expérience lorsque l’utilisateur entre une sous-partie de l’application. Pour plus d’informations et d’exemples de code, consultez la [documentation relative au basculement de profil](../configuration/mixed-reality-configuration-guide.md#changing-profiles-at-runtime) .

### <a name="directional-indicator-and-follow-solvers-graduated-from-experimental"></a>Indicateur directionnel et solveurs de suivi gradués de l’expérimentation

Deux nouveaux solveurs sont prêts à être utilisés avec la MRTK principale.

![Solveur d’indicateur directionnel](images/DirectionalIndicatorExampleScene.gif)

### <a name="hand-coach-graduated-from-experimental"></a>Autocar en mains progressif d’expérimentation

La fonctionnalité de autocar à main est maintenant prête à être utilisée avec la MRTK principale.

![Exemple de autocar](/windows/mixed-reality/design/images/handcoach/airtap.gif)

### <a name="dialog-controls-graduated-from-experimental"></a>Contrôles de boîte de dialogue gradués de l’expérimentation

Les contrôles de boîte de dialogue sont désormais prêts à être utilisés avec la MRTK principale.

![Contrôles de boîte de dialogue](https://user-images.githubusercontent.com/13754172/101927792-3326e200-3c18-11eb-88d3-44b4b50c7f7d.png)

### <a name="pulse-shader-graduated-from-experimental"></a>Nuanceur d’impulsions gradué de l’expérimentation

Les scripts du nuanceur d’impulsions ont été dégradés par expérimentation. Pour plus d’informations, consultez [la documentation d’Pulse Shader](../features/rendering/pulse-shader.md) .

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

### <a name="input-recording-service-improvements"></a>Améliorations du service d’enregistrement d’entrée

`InputRecordingService` et `InputPlaybackService` peuvent maintenant enregistrer et lire des entrées de regard oculaire. L’enregistrement a été optimisé pour garantir une fréquence d’images cohérente tout au long de la période d’enregistrement, tandis que la taille du fichier d’enregistrement et la durée de l’enregistrement sont également réduites d’environ 50%. L’enregistrement et le chargement des fichiers d’enregistrement peuvent maintenant être exécutés de façon asynchrone. Notez que le format de fichier de l’enregistrement a été modifié dans cette version de MRTK. pour plus d’informations sur les nouvelles spécifications de version 1,1, consultez cette [page](../features/input-simulation/input-animation-file-format.md) .

### <a name="reading-mode"></a>Mode lecture

Ajout de la prise en charge du [mode lecture](/hololens/hololens2-display#what-improvements-are-coming-that-will-improve-hololens-2-image-quality) sur HoloLens 2. Le mode de lecture réduit le champ de vue du système, mais élimine la mise à l’échelle de la sortie d’Unity. Un pixel rendu par Unity correspond à un pixel projeté sur HoloLens 2. Les auteurs d’applications doivent effectuer des tests avec plusieurs personnes pour s’assurer qu’il s’agit d’un compromis qu’ils souhaitent dans leur application.

![mode de lecture Windows Mixed Reality](images/WMRReadingMode.gif)

### <a name="support-for-3d-app-launchers-on-uwp"></a>Prise en charge des lanceurs d’applications en 3D sur UWP

Ajoute la possibilité de définir un [lanceur d’applications 3D](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) pour UWP. ce paramètre est exposé à la fois dans la fenêtre de génération MRTK et dans le Paramètres de Project MRTK, sous Paramètres de build. Il est automatiquement écrit dans le projet pendant la génération dans Unity.

![Paramètres de build](images/ProjectBuildSettings.png)

## <a name="breaking-changes"></a>Changements cassants

### <a name="certain-fields-of-imported-gltf-objects-are-now-capitalized"></a>Certains champs des objets GLTF importés sont désormais en majuscules

En raison des problèmes liés à la désérialisation, certains champs des objets GLTF importés commencent à commencer par des lettres majuscules. Les champs affectés sont (dans leurs nouveaux noms) : `ComponentType` , `Path` , `Interpolation` , `Target` , `Type` , `Mode` , `MagFilter` , `MinFilter` , `WrapS` , `WrapT` .

### <a name="input-animation-binary-file-has-an-updated-version-11-format"></a>Le fichier binaire d’animation d’entrée a une mise à jour au format 1,1

Le fichier binaire d’animation d’entrée, utilisé par `InputRecordingService` et `InputPlaybackService` , dispose désormais d’un format de fichier mis à jour pour activer les optimisations effectuées sur ces deux services. Pour plus d’informations sur les nouvelles spécifications de version 1,1, consultez [cette page](../features/input-simulation/input-animation-file-format.md) .

### <a name="msbuild-for-unity-support"></a>MSBuild pour la prise en charge d’unity

la prise en charge de MSBuild pour unity a été supprimée à partir de la version 2.5.2, afin de s’aligner avec les [nouvelles instructions du package unity](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/).

## <a name="known-issues"></a>Problèmes connus

### <a name="openxr"></a>OpenXR

Il existe actuellement un problème connu avec la communication à distance holographique et OpenXR, où les jointures manuelles ne sont pas constamment disponibles.
En outre, les scènes des exemples de suivi oculaire ne sont pas compatibles actuellement, bien que le suivi _visuel fonctionne._

### <a name="some-mixed-reality-toolkit-standard-shader-features-require-the-foundation-package"></a>une réalité mixte Shared Computer Toolkit fonctionnalités de nuanceur Standard nécessitent le package de base

lors de l’importation via unity Gestionnaire de package, les scripts d’utilitaires de nuanceur standard MRTK (ex : HoverLight. cs) ne sont pas colocalisés avec le nuanceur dans le package de ressources standard. Pour accéder à cette fonctionnalité, les applications doivent importer le package de Fondation.

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a>CameraCache peut créer un nouvel appareil photo à l’arrêt

Dans certains cas (par exemple, lorsque vous utilisez le fournisseur LeapMotion dans l’éditeur Unity), CameraCache peut recréer MainCamera lors de l’arrêt. Pour plus d’informations, consultez [ce problème](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) .

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a>FileNotFoundException quand des exemples sont importés via unity Gestionnaire de package

en fonction de la longueur du chemin d’accès au projet, l’importation d’exemples via unity Gestionnaire de package peut générer des messages FileNotFoundException dans la Console unity. La cause est le chemin d’accès au fichier « manquant » qui est plus long que MAX_PATH (256 caractères). Pour résoudre le, raccourcissez la longueur du chemin d’accès au projet.

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a>Aucun Spatializer n’a été spécifié. L’application ne prend pas en charge le son spatial

Un avertissement « aucun Spatializer n’a été spécifié » s’affiche si un Spatializer audio n’est pas configuré. Cela peut se produire si aucun package XR n’est installé, car Unity comprend spatializers dans ces packages.

Pour résoudre le, vérifiez les éléments suivants :

- **Fenêtre**  >  **Gestionnaire de package** a un ou plusieurs packages XR installés
- Shared Computer Toolkit de la **réalité mixte**  >  **Utilitaires**  >  **configurer unity Project** et faire une sélection pour l' **Audio Spatializer**

  ![Sélectionner les Spatializer audio](images/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a>NullReferenceException : la référence d’objet n’est pas définie sur une instance d’un objet (SceneTransitionService.Initialize)

Dans certains cas, l’ouverture `EyeTrackingDemo-00-RootScene` de peut provoquer une exception NullReferenceException dans la méthode Initialize de la classe SceneTransitionService.
Cette erreur est due au fait que le profil de configuration du service de transition de scène est désactivé. Pour résoudre le, procédez comme suit :

- Accéder à l' `MixedRealityToolkit` objet dans la hiérarchie
- Dans la fenêtre de l’inspecteur, sélectionnez `Extensions`
- S’il n’est pas développé, développez `Scene Transition Service`
- Définir la valeur de `Configuration Profile` sur **MRTKExamplesHubSceneTransitionServiceProfile**

![Corriger le profil de transition de scène](images/FixSceneTransitionProfile.png)

### <a name="oculus-quest"></a>Oculus Quest

Il existe actuellement un problème connu lié à l’utilisation du [plug-in Oculus XR avec pour cibler des plateformes autonomes](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/). Consultez le suivi des bogues/forums/notes de publication Oculus pour les mises à jour.

Le bogue est signalé par cet ensemble de 3 erreurs :

![Erreur du plug-in Oculus XR](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a>UnityUI et TextMeshPro

Il existe un problème connu pour les versions plus récentes de TextMeshPro (1.5.0 + ou 2.1.1 +), où la taille de police par défaut pour les listes déroulantes et l’espacement des caractères de police gras ont été modifiés.

![Image TMP](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

Pour ce faire, vous pouvez passer à une version antérieure de TextMeshPro. Pour plus d’informations, consultez [#8556 de problèmes](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) .
