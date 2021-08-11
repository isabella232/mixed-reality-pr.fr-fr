---
title: Notes de publication de MRTK 2.7
description: Notes de publication pour MRTK version 2.7
author: RogPodge
ms.author: roliu
ms.date: 06/16/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK, XRSDK, Legacy XR, Leap Motion, Ultraleap, OpenXR
ms.localizationpriority: high
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 921cdb4d9643e55841bc7c979066c276f5fd80998ad97d19332c528cebe05c37
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203488"
---
# <a name="microsoft-mixed-reality-toolkit-27-release-notes"></a>Notes de publication de Microsoft Mixed Reality Toolkit 2.7

## <a name="whats-new-in-272"></a>Nouveautés de la version 2.7.2

### <a name="fixed-a-upm-package-dependency-issue"></a>Résolution d’un problème de dépendance de package UPM

En raison d’un problème lié aux packages UPM MRTK 2.7.1, les dépendances n’étaient pas configurées correctement. L’outil Mixed Reality Feature Tool ne pouvait donc pas importer correctement les packages MRTK 2.7.1. Ce problème a été résolu dans la version 2.7.2. Aucun changement de code n’est à signaler dans cette version par rapport à la version 2.7.1.


## <a name="whats-new-in-271"></a>Nouveautés de la version 2.7.1

### <a name="show-version"></a>Show version

Le menu `Mixed Reality` > `Toolkit` contient désormais une entrée `Show version...` qui examine le package Mixed Reality Toolkit Foundation pour déterminer la version de MRTK utilisée par le projet.

![Menu Show version](images/ShowVersionMenu.png)

![Boîte de dialogue indiquant la version de MRTK](images/VersionDialog.png)

> [!NOTE]
> Si MRTK a été cloné à partir du [dépôt GitHub](https://aka.ms/mrtk), les informations sur la version ne sont pas définies.
>
> ![Impossible de déterminer la version](images/CannotDetermineVersion.png)

### <a name="authors-list"></a>Liste des auteurs

À compter de MRTK 2.7.1, le fichier de liste des auteurs est inclus dans le package Mixed Reality Toolkit Foundation.

### <a name="integrated-openxr-project-setup-into-the-configurator-setup-flow"></a>Configuration du projet OpenXR intégrée au flux de configuration du configurateur

À compter de MRTK 2.7.1, les utilisateurs du plug-in OpenXR Mixed Reality reçoivent des instructions sur la façon de configurer ce plug-in avec MRTK. Une option permet aux utilisateurs ciblant HoloLens 2 d’appliquer automatiquement les paramètres recommandés.

![Fenêtre du configurateur avec instructions de configuration d’OpenXR](images/configuratorMROpenXR.png)

### <a name="notable-bugfixes-and-changes"></a>Correctifs et changements notables

- Unity Joystick Manager marqué comme pris en charge sur le pipeline du SDK XR [#9954](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9954), [#9994](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9994)
- Ajout de vérifications au code de l’inspecteur Interactable pour éviter les erreurs null [#9943](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9943)
- Ajout d’un fournisseur de maillage OpenXR à l’exemple de scène du nuanceur animé [#9902](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9902)
- Restauration du profil de physique des mains dans un exemple de scène [#9915](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9915)
- Nettoyage des scripts HandConstraint* [#9935](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9935)
- Correction de bogues affectant la création et le clonage de profils [#9982](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9982)


## <a name="whats-new-in-270"></a>Nouveautés de la version 2.7.0

### <a name="openxr-is-now-officially-supported-in-mrtk"></a>OpenXR est désormais officiellement pris en charge dans MRTK

Les nouveaux plug-ins OpenXR gagnant en maturité, MRTK prend désormais officiellement en charge OpenXR. Par rapport aux versions précédentes, nous avons ajouté les fonctionnalités suivantes aux projets utilisant OpenXR :

- [Prise en charge du modèle de contrôleur de mouvement fourni par le système](#support-for-the-system-provided-motion-controller-model-on-openxr)
- Prise en charge des mouvements WinMR (sélection, maintien, manipulation et navigation) [#9843](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9843)
- [Prise en charge du retour haptique de contrôleur](#support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr)
- [Prise en charge du maillage de la main sur HoloLens 2](#support-for-hololens-2-articulated-hand-mesh-on-openxr)
- Prise en charge du mappage spatial sur HoloLens 2 [#9567](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9567), [#9827](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9827)
- Prise en charge de la compréhension des scènes sur HoloLens 2 [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)

Si vous ciblez des casques HoloLens 2 ou Windows Mixed Reality par le biais d’OpenXR, veillez à installer la **version 0.9.5 ou ultérieure du plug-in OpenXR Mixed Reality** ou à effectuer la mise à jour vers cette version à l’aide de l’outil [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool). Sinon, vous risquez de ne pas bénéficier de certaines des améliorations indiquées plus haut.

### <a name="legacy-xr-and-xr-sdk-data-providers-can-now-be-used-within-the-same-profile"></a>Les fournisseurs de données Legacy XR et XR SDK peuvent désormais être utilisés dans le même profil

Désormais, les fournisseurs de données sont uniquement chargés quand le pipeline approprié est sélectionné, ce qui permet aux fournisseurs de données Legacy XR et XR SDK de coexister dans le même profil. Pour ce faire, les fournisseurs de données Legacy XR et XR SDK sont maintenant organisés sous différents onglets dans la vue du profil, ce qui permet aux utilisateurs de déterminer s’ils disposent du profil approprié pour leur pipeline XR ciblé.

![Les fournisseurs de données Legacy XR et XR SDK peuvent à présent être unifiés sous un profil unique](../features/images/xrsdk/LegacyAndXrsdkUnified.png)

Pour ce faire, les fournisseurs de données null ne sont désormais ni chargés ni affichés dans l’inspecteur de profil. Les utilisateurs peuvent basculer `Show null data providers in the profile inspector` sous **Edit -> Project Settings -> Mixed Reality Toolkit** pour déboguer les comportements inattendus causés par des fournisseurs de données manquants.

![Les fournisseurs de données null sont désormais masqués par défaut](https://user-images.githubusercontent.com/39840334/115093658-ead24600-9ecf-11eb-91c2-486a37f69aba.png)
![Basculer l’affichage des fournisseurs de données null dans l’inspecteur de profil](https://user-images.githubusercontent.com/39840334/115093670-f6257180-9ecf-11eb-96ec-ffe44a225a55.png)

### <a name="added-experience-settings-and-an-associated-mixed-reality-scene-content-behavior"></a>Ajout de paramètres d’expérience et d’un comportement de contenu de scène de réalité mixte associé

Les utilisateurs peuvent désormais configurer des [paramètres d’expérience](../features/experience-settings/experience-settings.md) (Experience Settings), ce qui permet à MRTK d’afficher le [contenu d’une scène de réalité mixte](../features/experience-settings/scene-content.md) en fonction de l’expérience ciblée.

Si les paramètres Experience Scale définis précédemment ne correspondent pas au nouveau profil Experience Settings, l’utilisateur est invité à apporter des corrections dans l’inspecteur.

![Migration des paramètres Experience Scale](https://user-images.githubusercontent.com/39840334/114946863-d70bde80-9e00-11eb-9859-fa40d40d2b36.gif)

### <a name="the-redesigned-configurator-now-guides-the-user-through-the-setup-process"></a>Configurateur repensé pour guider l’utilisateur tout au long du processus de configuration

Le nouveau configurateur MRTK fournit aux utilisateurs des instructions pas à pas pour bien configurer le projet dans le cadre du développement XR et l’utiliser avec MRTK. Il couvre la sélection du pipeline XR, l’obtention des plug-ins spécifiques à la plateforme, l’importation de TextMeshPro, l’affichage des exemples (lors de l’utilisation d’UPM) et d’autres paramètres recommandés précédemment inclus pour le projet.

![Configurateur montrant la liste des pipelines](images/Configurator.png)

### <a name="graduated-teleport-hotspot"></a>TeleportHotspot disponible

Un nouveau [composant TeleportHotspot ](../features/teleport-system/teleport-hotspot.md) est disponible. Vous pouvez ajouter une zone réactive de téléportation à votre GameObject pour vérifier que l’utilisateur se trouve dans une position et une orientation données lorsqu’il se téléporte à cet emplacement.

![Exemple de zone réactive de téléportation](images/TeleportHotspot.gif)

### <a name="graduated-dwell"></a>Fixation du regard disponible

La fonctionnalité et l’exemple de fixation du regard ont quitté la phase expérimentale. De nouveaux exemples de boutons de style HoloLens 2 volumétriques sont inclus dans l’exemple de scène.

![Bannière de fixation du regard](../features/images/dwell/MRTK_UX_Dwell.png)

### <a name="added-support-for-leap-motion-unity-modules-version-460-470-471-and-480"></a>Prise en charge des modules Leap Motion Unity versions 4.6.0, 4.7.0, 4.7.1 et 4.8.0

Les dernières versions des [modules Leap Motion Unity](https://developer.leapmotion.com/unity) sont désormais compatibles avec MRTK 2.7.0. Pour plus d’informations, consultez le [guide pratique pour configurer MRTK pour LEAP Motion](../supported-devices/leap-motion-mrtk.md).

Un grand merci à @jackyangzzh pour sa contribution à la nouvelle scène LeapMotionOrientationExample !

### <a name="targeted-speech-events-raised-no-longer-restricted-to-gaze-pointers"></a>Les événements vocaux ciblés déclenchés ne sont plus limités aux pointeurs du regard

Auparavant, les événements vocaux ciblés pouvaient uniquement être déclenchés sur des objets sélectionnés par le pointeur du regard. Désormais, des objets peuvent recevoir des événements vocaux s’ils sont sélectionnés par n’importe quel pointeur.

![Événements vocaux avec des pointeurs far](https://user-images.githubusercontent.com/39840334/117516612-6fa00500-af4e-11eb-94ba-d5fb2ed4e7de.gif)

### <a name="ported-texttospeech-from-htk-to-mrtk"></a>TextToSpeech porté de HTK à MRTK

Le script TextToSpeech particulièrement apprécié des utilisateurs est maintenant disponible dans MRTK pour générer une synthèse vocale sur la plateforme UWP avec [`SpeechSynthesizer`](/uwp/api/windows.media.speechsynthesis.speechsynthesizer). Un exemple de scène a également été ajouté pour illustrer la fonctionnalité.

### <a name="support-for-the-system-provided-motion-controller-model-on-openxr"></a>Prise en charge du modèle de contrôleur de mouvement fourni par le système sur OpenXR

Le modèle de contrôleur de mouvement fourni par le système sur OpenXR est désormais pris en charge, à la fois dans l’éditeur et au moment de l’exécution.

![Fenêtre de l’éditeur avec deux modèles de contrôleur de mouvement](https://user-images.githubusercontent.com/3580640/116493405-89a55d80-a853-11eb-95ae-d430e6fdc8b4.png)

### <a name="support-for-hololens-2-articulated-hand-mesh-on-openxr"></a>Prise en charge du maillage de main articulée HoloLens 2 sur OpenXR

![Maillage de la main exécuté sur l’appareil dans un exemple de scène MRTK](https://user-images.githubusercontent.com/3580640/112909923-32bb3580-90a7-11eb-925d-464b135edc61.png)

### <a name="support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr"></a>Prise en charge du retour haptique de contrôleur sur WMR hérité, le plug-in Windows XR et OpenXR

Prise en charge du retour haptique de contrôleur sur WMR hérité, le plug-in Windows XR et OpenXR. [#9735](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9735)

### <a name="support-for-eye-tracking-on-windows-xr-plugin"></a>Prise en charge du suivi oculaire dans le plug-in Windows XR

Prise en charge du suivi du regard avec les versions minimales du plug-in Windows XR : 2.7.0 (Unity 2019), 4.4.2 (Unity 2020) et 5.2.2 (Unity 2021). [#9609](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9609)

### <a name="notable-bugfixes-and-changes"></a>Correctifs et changements notables

- Détection des pincements plus fluide. Il est maintenant plus difficile de sortir accidentellement du mouvement de pincement. [#9576](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9576)
- Les objets avec le composant Object Manipulator maintiennent désormais systématiquement la vélocité après relâchement quand l’indicateur est défini. [#9733](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9733)
- Le déplacement en arrière vérifie à présent la présence d’un sol, ce qui permet d’éviter que l’appareil photo se retrouve découpé dans l’environnement (clipping) ou que l’utilisateur pointe sur un espace vide.[#9697](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9697)
- IsNearObject est désormais une propriété virtuelle, ce qui offre plus de flexibilité lors de l’extension du SpherePointer ou du PokePointer. [#9803](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9803)
- Les boutons affichent désormais le mot clé approprié lors de l’affichage de la commande vocale disponible. [#9824](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9824)
- Les contrôleurs Oculus utilisent désormais leur propre visualiseur autonome, ce qui empêche la visualisation MRTK d’entrer en conflit avec la visualisation du package d’intégration Oculus. [#9589](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9589)
- Les scripts liés au clavier ont été modifiés pour s’aligner sur le comportement des dernières versions d’Unity (2019.4.25+ et 2020.3.2+). À l’heure de la publication, un bogue lié à la saisie semi-automatique et un bogue lié au champ d’entrée TMP (tous deux externes à MRTK) impactent HoloLens. Pour plus d’informations, consultez [#9056](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9056) et [#9724](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9724).
- Amélioration des performances du défilement de la collection d’objets. Correction d’un problème entraînant la perte d’éléments dans GameObject au sein de la collection en cas de duplication. [#9813](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9813), [#9718](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9718)
- Dans le script de démonstration de compréhension de la scène, la fonction `GetSceneObjectsOfType` a été ajoutée pour récupérer tous les objets de scène observés d’un certain type. [#9524](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9524), [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)
- Dans l’outil de build en ligne de commande, seules les scènes spécifiées par les indicateurs `sceneList` et `sceneListFile` (quand un indicateur est présent) sont incluses dans la build. [#9695](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9695)
- Dans l’outil de build, une nouvelle option permet de spécifier un chemin à `nuget.exe` et de l’utiliser pour effectuer la restauration de package à la place de `msbuild` (option par défaut). [#9556](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9556)
- Résolution d’un problème pouvant entraîner des jointures de main obsolètes et des maillages de main en double lors de l’utilisation du plug-in Windows XR. [#9890](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9890)
- Résolution d’un problème entraînant l’absence d’entrées et d’interactions lors de l’utilisation de la fonctionnalité de communication à distance automatique du plug-in Windows XR. [#9868](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9868)
- Résolution d’un problème lors duquel BuildDeployWindow tente d’interroger une clé de Registre non valide pour le chemin du SDK Windows. [#9664](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9664)
- Les importateurs glTF de MRTK sont désormais facultatifs. Si plusieurs importateurs glTF sont présents, vous pouvez désactiver ceux de MRTK en ajoutant `MRTK_GLTF_IMPORTER_OFF` aux entrées personnalisées de Scripting Define Symbols. [#9658](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9658)
- Résolution d’un problème empêchant la bonne détection des contrôleurs Knuckles sur OpenVR. [#9881](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9881)
- Réduction du nombre d’allocations par image lors de la visualisation du maillage de la main [#9756](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9756)
- Ajout d’un élément de menu pour lancer le package MRTK Examples (dans Unity Package Manager) afin de faciliter l’importation d’exemples [#9798](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9798)
- Réduction du nombre d’avertissements au moment du chargement lors de l’utilisation d’Unity 2020.3.
- Ajout de la documentation sur les fonctionnalités de la fenêtre de build : [visiter la page](../features/tools/build-window.md)

## <a name="known-issues"></a>Problèmes connus

### <a name="audio-demos-are-missing-an-asmdef-file-upm-package"></a>Fichier asmdef manquant dans les démonstrations audio (package UPM)

Quand vous importez MRTK par le biais de l’outil Mixed Reality Feature Tool, des exemples et des démonstrations sont ajoutés au projet avec Unity Package Manager UI. Une fois les démonstrations audio importées, la scène `WindowsMicrophoneStreamDemo.unity` ne se comporte pas correctement. Cela est dû à l’absence d’un fichier .asmdef dans l’exemple.

Pour contourner ce [problème](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9908), effectuez les étapes suivantes :

- Copier Library/PackageCache/com.microsoft.mixedreality.toolkit.examples@[...]/MRTK.Examples.asmdef dans le dossier Assets/Samples/Mixed Reality Toolkit Examples
- Renommer le fichier copié Examples
- Ouvrir le fichier Examples
- Dans la zone Name, remplacer le contenu par Examples
- Cliquer sur Apply
- Générer et déployer

Ce problème sera résolu dans une version future de MRTK.

### <a name="mrtk-build-window-triggers-indefinite-importing-assets-dialog-in-unity-20203"></a>La fenêtre de build MRTK déclenche une boîte de dialogue « Importing assets » indéfinie dans Unity 2020.3

Un [problème](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9723) connu lié la fenêtre de build MRTK sur Unity 2020.3 empêche l’exécution de la boîte de dialogue d’importation de ressources après l’exécution réussie d’une build UWP. Ce problème est actuellement examiné en partenariat avec Unity.

### <a name="text-mesh-pro-canvas-renderer-warnings-in-unity-2020"></a>Avertissements du CanvasRenderer TextMeshPro dans Unity 2020

L’avertissement suivant est journalisé dans la plupart des exemples de scènes MRTK avec Unity 2020 :

```txt
Please remove the CanvasRenderer component from the [TextMeshPro] GameObject as this component is no longer necessary.
```

L’avertissement du CanvasRenderer a été ajouté dans [TextMeshPro version 3.0.3](https://docs.unity3d.com/Packages/com.unity.textmeshpro@3.0/changelog/CHANGELOG.html#changes-3). Ces avertissements n’ont pas d’impact sur les exemples de scènes de MRTK et peuvent être effacés de la console. Pour plus d’informations, consultez le [problème 9811](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9811).