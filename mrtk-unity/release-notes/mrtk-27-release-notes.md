---
title: Notes de publication de MRTK 2,7
description: Notes de publication de MRTK version 2,7
author: RogPodge
ms.author: roliu
ms.date: 05/27/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, XRSDK, XR hérité, mouvement LEAP, Ultraleap
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 92c8705c70a2a6c1e25f1ed6b1f87eac1e5726e0
ms.sourcegitcommit: 11d5d7c3fdd59c1ebcfca34dbb6d84c05b481e5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2021
ms.locfileid: "111897402"
---
# <a name="microsoft-mixed-reality-toolkit-27-release-notes"></a>Notes de publication de Microsoft Mixed Reality Toolkit 2,7

## <a name="whats-new-in-270"></a>Nouveautés de 2.7.0

### <a name="openxr-is-now-officially-supported-in-mrtk"></a>OpenXR est désormais officiellement pris en charge dans MRTK

À mesure que les nouveaux plug-ins OpenXR deviennent de plus en plus matures, MRTK prend officiellement en charge OpenXR. Par rapport aux versions précédentes, nous avons ajouté les fonctionnalités suivantes aux projets à l’aide de OpenXR :

- [Prise en charge du modèle de contrôleur de mouvement fourni par le système](#support-for-the-system-provided-motion-controller-model-on-openxr)
- Prise en charge des mouvements WinMR (sélection, maintien, manipulation et navigation) [#9843](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9843)
- [Prise en charge des haptiques de contrôleur](#support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr)
- [Prise en charge d’une maille articulée sur HoloLens 2](#support-for-hololens-2-articulated-hand-mesh-on-openxr)
- Prise en charge du mappage spatial sur HoloLens 2 [#9567](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9567), [#9827](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9827)
- Prise en charge de la compréhension des scènes sur HoloLens 2 [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)

### <a name="legacy-xr-and-xr-sdk-data-providers-can-now-be-used-within-the-same-profile"></a>Les fournisseurs de données XR et XR SDK hérités peuvent désormais être utilisés dans le même profil

Désormais, les fournisseurs de données sont également chargés uniquement lorsque le pipeline approprié est sélectionné, ce qui permet aux fournisseurs de données XR et XR SDK hérités de coexister dans le même profil. Pour ce faire, les fournisseurs de données XR et XR SDK hérités sont maintenant organisés sous différents onglets dans la vue du profil, ce qui permet aux utilisateurs de déterminer s’ils disposent du profil approprié pour le pipeline XR ciblé.

![Les fournisseurs de données SDK hérités et XR peuvent désormais être unifiés sous un profil unique](../features/images/xrsdk/LegacyAndXrsdkUnified.png)

Pour ce faire, les fournisseurs de données NULL ne sont plus chargés et affichés dans l’inspecteur de profil. Les utilisateurs peuvent basculer `Show null data providers in the profile inspector` sous **modifier > paramètres du projet-> boîte à outils de réalité mixte** pour déboguer les comportements inattendus avec les fournisseurs de données manquants.

![Les fournisseurs de données NULL sont maintenant masqués par défaut ](https://user-images.githubusercontent.com/39840334/115093658-ead24600-9ecf-11eb-91c2-486a37f69aba.png)
 ![ basculer afficher les fournisseurs de données null dans l’inspecteur de profil](https://user-images.githubusercontent.com/39840334/115093670-f6257180-9ecf-11eb-96ec-ffe44a225a55.png)

### <a name="added-experience-settings-and-an-associated-mixed-reality-scene-content-behavior"></a>Ajout de paramètres d’expérience et d’un comportement de contenu de scène de réalité mixte associé

Les utilisateurs peuvent désormais configurer les [paramètres d’expérience](../features/experience-settings/experience-settings.md), ce qui permettra à MRTK d’afficher le contenu de [scènes de réalité mixte](../features/experience-settings/scene-content.md) en fonction de l’expérience ciblée.

Si les paramètres de mise à l’échelle de l’expérience utilisateur précédents ne correspondent pas au nouveau profil de paramètres d’expérience, ils seront invités à le corriger dans l’inspecteur.

![Migration de l’évolution de l’expérience](https://user-images.githubusercontent.com/39840334/114946863-d70bde80-9e00-11eb-9859-fa40d40d2b36.gif)

### <a name="the-redesigned-configurator-now-guides-the-user-through-the-setup-process"></a>Le configurateur repensé guide maintenant l’utilisateur tout au long du processus d’installation

Le nouveau Configurateur MRTK fournit aux utilisateurs des instructions pas à pas pour configurer correctement le projet pour le développement XR et l’utiliser avec MRTK. Il couvre la sélection du pipeline XR, l’obtention des plug-ins spécifiques à la plateforme, l’importation de TextMeshPro, l’affichage des exemples (lors de l’utilisation de UPM) et d’autres paramètres recommandés précédemment pour le projet.

![Configurateur qui présente la liste des pipelines](images/Configurator.png)

### <a name="graduated-teleport-hotspot"></a>Point d’accès de télérelais gradué

Un nouveau [composant](../features/teleport-system/teleport-hotspot.md) de point d’accès à chaud a été gradué. Vous pouvez ajouter une zone réactive de télétentative à votre GameObject pour vous assurer que l’utilisateur est dans une certaine position et orientation lorsqu’il se téléporte à cet emplacement.

![Exemple de hotspot de téléchaud](images/TeleportHotspot.gif)

### <a name="graduated-dwell"></a>Logement gradué

La fonctionnalité de logement et l’exemple sont désormais gradués de l’expérimentation expérimentale. De nouveaux exemples de boutons de style HoloLens 2 volumétriques sont inclus dans l’exemple de scène.

![Héros du logement](../features/images/dwell/MRTK_UX_Dwell.png)

### <a name="added-support-for-leap-motion-unity-modules-version-460-470-471-and-480"></a>Ajout de la prise en charge des modules Unity LEAP, version 4.6.0, 4.7.0, 4.7.1 et 4.8.0

La prise en charge des versions les plus récentes des [modules Unity LEAP](https://developer.leapmotion.com/unity) est désormais compatible avec MRTK 2.7.0.  Pour plus d’informations, voir [How to configure MRTK for LEAP Motion](../supported-devices/leap-motion-mrtk.md) .

Big Merci à @jackyangzzh pour contribuer à la nouvelle scène LeapMotionOrientationExample !

### <a name="targeted-speech-events-raised-no-longer-restricted-to-gaze-pointers"></a>Les événements vocaux ciblés ne sont plus limités aux pointeurs de regard

Auparavant, les événements vocaux ciblés pouvaient uniquement être déclenchés sur des objets qui étaient concentrés avec le pointeur de pointage. Désormais, les objets peuvent recevoir des événements vocaux s’ils sont axés sur n’importe quel pointeur.

![Événements vocaux avec des pointeurs Far](https://user-images.githubusercontent.com/39840334/117516612-6fa00500-af4e-11eb-94ba-d5fb2ed4e7de.gif)

### <a name="ported-texttospeech-from-htk-to-mrtk"></a>TextToSpeech portées de HTK à MRTK

Le script aimée TextToSpeech est maintenant disponible dans MRTK pour vous aider à générer de la parole à partir du texte sur la plateforme UWP à l’aide de [`SpeechSynthesizer`](/uwp/api/windows.media.speechsynthesis.speechsynthesizer) . Ajout également d’un exemple de scène pour illustrer la fonctionnalité.

### <a name="support-for-the-system-provided-motion-controller-model-on-openxr"></a>Prise en charge du modèle de contrôleur de mouvement fourni par le système sur OpenXR

Ajout de la prise en charge, dans l’éditeur et au moment de l’exécution, pour le modèle de contrôleur de mouvement fourni par le système sur OpenXR.

![Fenêtre de l’éditeur avec deux modèles de contrôleur de mouvement](https://user-images.githubusercontent.com/3580640/116493405-89a55d80-a853-11eb-95ae-d430e6fdc8b4.png)

### <a name="support-for-hololens-2-articulated-hand-mesh-on-openxr"></a>Prise en charge de la maille articulée de HoloLens 2 sur OpenXR

![La maille de main exécutée sur l’appareil dans un exemple de scène MRTK](https://user-images.githubusercontent.com/3580640/112909923-32bb3580-90a7-11eb-925d-464b135edc61.png)

### <a name="support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr"></a>Prise en charge des haptiques de contrôleur sur les WMR hérités, le plug-in Windows XR et OpenXR

Ajout de la prise en charge des haptiques de contrôleur sur les WMR hérités, le plug-in XR Windows et OpenXR. [#9735](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9735)

### <a name="support-for-eye-tracking-on-windows-xr-plugin"></a>Prise en charge du suivi oculaire sur le plug-in XR Windows

Ajout de la prise en charge des yeux en cas d’utilisation des versions minimales du plug-in Windows XR de 2.7.0 (Unity 2019), 4.4.2 (Unity 2020) et 5.2.2 (Unity 2021). [#9609](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9609)

### <a name="notable-bugfixes-and-changes"></a>Correctifs et modifications notables

- Détection de pincement rendue plus lisse. Il est maintenant plus difficile de supprimer accidentellement le geste de pincement. [#9576](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9576)
- Les objets avec le composant manipulateur d’objets maintiennent désormais systématiquement la rapidité de mise en version lorsque l’indicateur est défini. [#9733](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9733)
- Back-strafing vérifie à présent un étage, ce qui permet d’éviter les situations où l’appareil photo peut être inséré dans l’environnement ou à l’endroit où l’utilisateur pointe sur un espace vide. [#9697](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9697)
- IsNearObject est désormais une propriété virtuelle, qui offre davantage de flexibilité lors de l’extension de la sphère ou du pointeur d’une autre façon. [#9803](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9803)
- Les boutons affichent désormais le mot clé approprié lors de l’affichage de la commande vocale disponible. [#9824](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9824)
- Les contrôleurs Oculus utilisent désormais son propre visualiseur autonome, ce qui empêche la visualisation MRTK d’entrer en conflit avec la visualisation du package d’intégration Oculus. [#9589](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9589)
- Les scripts liés au clavier ont été modifiés pour s’aligner sur le comportement des dernières versions Unity (2019.4.25 + & 2020.3.2 +). À partir de la version, il existe toujours un bogue de saisie semi-automatique et un bogue de champ d’entrée TMP (tous deux sont externes à MRTK) qui ont un impact sur HoloLens. Pour plus d’informations, consultez [#9056](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9056) et [#9724](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9724).
- Amélioration des performances de la collection d’objets de défilement. Correction d’un problème qui provoquait la perte de l’élément GameObject dans la collection en cas de doublon. [#9813](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9813), [#9718](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9718)
- Dans la scène présentation du script de démonstration, ajout de la `GetSceneObjectsOfType` fonction pour récupérer tous les objets de scène observés d’un certain type. [#9524](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9524), [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)
- Dans l’outil de génération de ligne de commande, seules les scènes spécifiées par les `sceneList` `sceneListFile` indicateurs ou (quand un indicateur est présent) sont incluses dans la Build. [#9695](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9695)
- Dans l’outil de génération, il existe une nouvelle option pour spécifier un chemin d’accès `nuget.exe` et l’utiliser pour effectuer la restauration du package au lieu d’utiliser `msbuild` (option par défaut). [#9556](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9556)
- Résolution d’un problème où l’utilisation du plug-in XR Windows pouvait entraîner des jointures de handles obsolètes et des maillages à double main. [#9890](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9890)
- Correction du problème où l’utilisation de la fonctionnalité de communication à distance automatique du plug-in Windows XR a entraîné l’absence d’entrées et d’interactions. [#9868](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9868)
- Correction du problème où le BuildDeployWindow essaiera d’interroger une clé de Registre non valide pour le chemin d’accès SDK Windows. [#9664](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9664)
- Les importateurs glTF de MRTK sont désormais facultatifs. Si plusieurs importateurs glTF sont présents, les MRTK peuvent être désactivés en ajoutant `MRTK_GLTF_IMPORTER_OFF` au script personnalisé définir des symboles. [#9658](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9658)
- Correction du problème où les contrôleurs Knuckles sur OpenVR n’ont pas été détectés correctement. [#9881](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9881)
- Réduisez le nombre d’allocations par image lors de la visualisation du maillage de la main [#9756](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9756)
- Ajout d’un élément de menu pour lancer le package d’exemples MRTK (dans le gestionnaire de package Unity) pour faciliter l’importation des exemples [#9798](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9798)
- Réduction du nombre d’avertissements au moment du chargement lors de l’utilisation d’Unity 2020,3.
- Ajout [de la documentation sur les fonctionnalités de la fenêtre de génération : visiter la page](/windows/mixed-reality/mrtk-unity/features/tools/build-window)

## <a name="known-issues"></a>Problèmes connus

### <a name="audio-demos-are-missing-an-asmdef-file-upm-package"></a>Un fichier asmdef est manquant dans les démonstrations audio (package UPM)

Lorsque vous importez des MRTK via l’outil de la fonctionnalité de réalité mixte, des exemples et des démonstrations sont ajoutés au projet à l’aide de l’interface utilisateur du gestionnaire de package Unity. Une fois les démonstrations audio importées, la `WindowsMicrophoneStreamDemo.unity` scène ne se comportera pas correctement. Il s’agit d’un fichier. asmdef manquant pour l’exemple.

Pour contourner ce [problème](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9908), procédez comme suit :

- Copier la bibliothèque/PackageCache/com.microsoft.mixedreality.toolkit.examples@ [...] /MRTK. Exemple. asmdef dans le dossier « ressources/échantillons/exemples de la boîte à outils de réalité mixte »
- Renommer le fichier copié en exemples
- Ouvrir le fichier d’exemples
- Dans la zone Nom, remplacez le contenu par des exemples
- Cliquez sur appliquer.
- Générer et déployer

Ce problème sera résolu dans une prochaine version de MRTK.

### <a name="mrtk-build-window-triggers-indefinite-importing-assets-dialog-in-unity-20203"></a>La fenêtre de génération MRTK déclenche une boîte de dialogue « importation de ressources » indéfinie dans Unity 2020,3

Il existe un [problème](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9723) connu avec la fenêtre de génération MRTK sur unity 2020,3 où, après l’exécution réussie d’une build UWP, la boîte de dialogue « importation de ressources » ne s’exécute pas. Ce problème est étudié en partenariat avec Unity.

### <a name="text-mesh-pro-canvas-renderer-warnings-in-unity-2020"></a>Avertissements du convertisseur de dessin de canevas Pro du texte dans Unity 2020

L’avertissement suivant est enregistré dans le plus grand nombre d’exemples de MRTK lors de l’utilisation d’Unity 2020 :

```txt
Please remove the CanvasRenderer component from the [TextMeshPro] GameObject as this component is no longer necessary.
```

L’avertissement du convertisseur de canevas a été ajouté dans [TextMeshPro version 3.0.3](https://docs.unity3d.com/Packages/com.unity.textmeshpro@3.0/changelog/CHANGELOG.html#changes-3).  Ces avertissements n’ont pas d’impact sur les exemples de scènes de MRTK et peuvent être effacés à partir de la console. Pour plus d’informations, consultez le [problème 9811](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9811) .
