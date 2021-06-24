---
title: Notes de publication de MRTK 2,5
description: Notes de publication pour MRTK version 2,5
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK,
ms.openlocfilehash: 536a37b56b4c7de9875ce1e1642922bd363fecb1
ms.sourcegitcommit: f7839221c9549e60a2c3ac2dbd39f07a6851dcd2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2021
ms.locfileid: "112562489"
---
# <a name="microsoft-mixed-reality-toolkit-25-release-notes"></a>Notes de publication de Microsoft Mixed Reality Toolkit 2,5

> [!IMPORTANT]
> Un problème connu du compilateur affecte les applications générées pour Microsoft HoloLens 2 à l’aide de ARM64. Ce problème est résolu par la mise à jour de Visual Studio 2019 vers la version 16,8 ou ultérieure. Si vous ne parvenez pas à mettre à jour Visual Studio, importez le `com.microsoft.mixedreality.toolkit.tools` package pour appliquer une solution de contournement.

## <a name="whats-new-in-254"></a>Nouveautés de 2.5.4

### <a name="fixes-a-bug-with-oculus-integration-when-using-upm"></a>Résout un bogue avec l’intégration de Oculus lors de l’utilisation de UPM

Lors de l’utilisation de UPM, les prefabs de OculusXRSDKDeviceManagerProfile auront toujours la [valeur None au démarrage](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9160). Cette version configure le Gestionnaire de périphériques pour qu’il pointe vers une plage de travail de prefabs au démarrage.

### <a name="fixes-an-issue-with-openxr-via-upm"></a>Résout un problème avec OpenXR via UPM

Résout un problème où les fournisseurs OpenXR n’ont pas été ajoutés au link.xml par défaut, provoquant l’échec de l’exécution de nouveaux projets sur l’appareil lors de l’utilisation de OpenXR et de MRTK via le gestionnaire de package Unity. Les projets existants qui sont mis à niveau auront toujours besoin d’être ajoutés manuellement.

## <a name="whats-new-in-253"></a>Nouveautés de 2.5.3

### <a name="fixes-a-regression-with-oculus-introduced-in-252"></a>Corrige une régression avec Oculus introduite dans 2.5.2

2.5.2 [a introduit un problème de génération lors de l’intégration du kit de développement logiciel (SDK) Oculus](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9083). Cette version annule ce problème.

## <a name="whats-new-in-252"></a>Nouveautés de 2.5.2

### <a name="add-support-for-openxr"></a>Ajouter la prise en charge de OpenXR

La prise en charge initiale du package OpenXR d’Unity Preview et du package OpenXR de la réalité mixte de Microsoft a été ajoutée. Pour plus d’informations, consultez [la page de prise en main de MRTK/XRSDK, la](../configuration/getting-started-with-mrtk-and-xrsdk.md) [publication du Forum Unity](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/)ou la [documentation de Microsoft](/windows/mixed-reality/develop/unity/openxr-getting-started) .

> [!IMPORTANT]
> OpenXR dans Unity est pris en charge uniquement sur Unity 2020,3 et les versions ultérieures.
> Il prend également en charge uniquement les versions x64, ARM et ARM64.

### <a name="boundary-visualization-errors-fixed"></a>Erreurs de visualisation des limites corrigées

Les visualisations de limites, comme le plancher ou les murs, sont désormais correctement configurées et visibles au moment de l’exécution en fonction du profil de limite.

### <a name="msbuild-for-unity-support"></a>Prise en charge de MSBuild pour Unity

La prise en charge de MSBuild pour Unity a été supprimée à partir de la version 2.5.2, afin de s’aligner avec les [nouvelles instructions du package Unity](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/).

## <a name="whats-new-in-251"></a>Nouveautés de la 2.5.1

### <a name="package-dependency-errors-fixed"></a>Erreurs de dépendance de package corrigées

Cette version corrige les dépendances de fichiers inter-packages incorrectes (par exemple, les fichiers des actifs standard ne référencent plus de manière incorrecte des fichiers en base). La version 2.5.1 ajoute également une dépendance explicite sur le texte de maille Pro.

### <a name="standard-assets-package-shaders-copied-to-assetsmrtkshaders"></a>Nuanciers de packages de ressources standard copiés dans ressources/MRTK/nuanceurs

Lorsque le package de ressources standard est installé via UPM, les nuanceurs sont copiés dans le dossier Assets/MRTK/shaders afin qu’ils ne soient plus immuables. Cela résout le problème des nuanceurs mis à jour pour le pipeline de rendu universel (URP) en rétablissant le comportement hérité lors du prochain chargement du projet.

### <a name="fixed-teleport-cursor-sticking-to-hands"></a>Correction du curseur de télétentative en mains

Cette version corrige un [problème](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8755) où le curseur de destination de télétransmission peut coller des éléments visuels.

## <a name="whats-new-in-250"></a>Nouveautés de 2.5.0

### <a name="unity-package-manager-upm-support"></a>Prise en charge du gestionnaire de package Unity (UPM)

La boîte à outils de réalité mixte peut désormais être gérée à l’aide du gestionnaire de package Unity.

![Package UPM MRTK Foundation](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> Certaines étapes manuelles sont nécessaires pour importer les packages UPM MRTK. Pour plus d’informations, consultez la [boîte à outils de réalité mixte et le gestionnaire de package Unity](../configuration/usingupm.md) .

### <a name="oculus-quest-xr-sdk-support"></a>Prise en charge du kit SDK Oculus Quest XR

MRTK prend désormais en charge l’exécution de contrôleurs et de contrôleurs Oculus Quest à l’aide du pipeline du kit SDK XR natif. Le suivi de la main est également pris en charge avec le [package Unity d’intégration Oculus](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) grâce au travail de [Eric Provencher](https://twitter.com/prvncher) sur MRTK-Quest !

Pour obtenir des instructions sur le déploiement de votre appareil sur Oculus Quest à l’aide du nouveau pipeline, consultez le [Guide d’installation de Oculus Quest](../supported-devices/oculus-quest-mrtk.md) .

### <a name="scrolling-object-collection"></a>Défilement de la collection d’objets

Le composant MRTK UX a été mis à niveau à partir d’une fonctionnalité expérimentale et offre plus de liberté pour la mise en page du contenu 3D de tailles différentes avec une prise en charge supplémentaire des objets auxquels aucun conflit n’est attaché. Une nouvelle option de désactivation du masquage du contenu a également été ajoutée, ce qui facilite le prototypage.

Pour plus d’informations, consultez défilement de la [collection d’objets](../features/ux-building-blocks/scrolling-object-collection.md) .

![Défilement de la collection d’objets](https://user-images.githubusercontent.com/16922045/94465118-51537900-01b7-11eb-8f8b-bf864a8fee03.gif)

### <a name="teleport-pointer-animation-handling-and-sound-improvements"></a>Animation du pointeur de téléchargement, gestion et améliorations du son

Le pointeur de téléaction a désormais amélioré les animations et les commentaires audio. Nous avons également amélioré la gestion du pointeur de téléchargement pour qu’il gère le lissage lors du passage du point de vue des surfaces avoisinantes à des surfaces plus éloignées.

### <a name="input-simulation-cheat-sheet"></a>Aide-mémoire pour la simulation d’entrée

La scène HandInteractionExamples a maintenant un raccourci configurable pour afficher une page d’aide pour la simulation d’entrée

![Aide-mémoire pour la simulation d’entrée](https://user-images.githubusercontent.com/13754172/93232433-dea8cd80-f7b4-11ea-8500-eaee202f606f.png)

### <a name="input-simulation-eye-gaze-with-mouse"></a>Yeux de simulation d’entrée avec la souris

Les utilisateurs peuvent maintenant utiliser la souris pour simuler le suivi oculaire. Consultez le `Eye Simulation Mode` champ dans le profil de simulation d’entrée et affectez-lui la valeur Mouse. Cela remplace le `Simulate Eye Position` champ précédent.

![Curseur de la souris](https://user-images.githubusercontent.com/39840334/87720928-892b5280-c76a-11ea-9411-73ab69fc756c.gif)

### <a name="input-simulation-motion-controller-in-editor-play-mode"></a>Contrôleur de mouvement de simulation d’entrée en mode de lecture de l’éditeur

Les utilisateurs peuvent désormais simuler le contrôleur de mouvement comme les mains en mode de lecture de l’éditeur. Le déclencheur, les boutons de manipulation et de menu sont actuellement pris en charge.

### <a name="conical-grab-pointer"></a>Pointeur de manipulation conique

Les pointeurs de manipulation peuvent maintenant être configurés pour interroger des objets avoisinants à l’aide d’un cône à partir du point de manipulation plutôt que d’une sphère. Cela ressemble davantage au comportement de l’interface HoloLens 2 par défaut, qui interroge les objets les plus proches à l’aide d’un cône. Le DefaultHoloLens2InputSystemProfile a également été ajusté pour utiliser le nouveau `ConicalGrabPointer` .

![Pointeur de manipulation conique](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

### <a name="testutilities-package"></a>Package TestUtilities

Il existe maintenant un package (Microsoft. MixedReality. Toolkit. Unity. TestUtilities. 2.5.0. pour Unity) qui contient l’infrastructure de test PlayMode et TestMode que le MRTK utilise pour créer des tests de bout en bout. Cette infrastructure est extrêmement pratique pour l’équipe MRTK elle-même et nous sommes ravis de faire en sorte que les consommateurs l’utilisent pour ajouter la couverture des tests à leurs propres projets.

Le code suivant montre comment créer une main test, l’afficher à un certain emplacement, la déplacer, puis la pincer et l’ouvrir.

```csharp
TestHand leftHand = new TestHand(Handedness.Left);
yield return leftHand.Show(new Vector3(-0.1f, -0.1f, 0.5f));
yield return leftHand.SetGesture(ArticulatedHandPose.GestureId.Pinch);
yield return leftHand.Move(new Vector3(0.2f, 0.2f, 0));
yield return leftHand.SetGesture(ArticulatedHandPose.GestureId.Open);
```

Pour obtenir des instructions sur l’écriture d’un test à l’aide de ces TestUtilities, consultez cette section sur l' [écriture de tests](../contributing/unit-tests.md#writing-tests).

Pour obtenir des exemples de tests existants qui utilisent cette infrastructure, consultez [PlayModeTests](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Tests/PlayModeTests)de MRTK.

### <a name="support-for-the-leap-motion-451-unity-modules"></a>Prise en charge des modules Unity avec LEAP Motion 4.5.1

La prise en charge des modules Unity LEAP version 4.5.1 a été ajoutée et la prise en charge des ressources 4.4.0 a été supprimée. Les versions actuelles prises en charge des modules Unity LEAP sont 4.5.0 et 4.5.1.

Il existe également une étape supplémentaire pour l’intégration des mouvements LEAP initiaux. pour plus d’informations, consultez [Comment configurer le suivi de la main des mouvements LEAP dans MRTK](../supported-devices/leap-motion-mrtk.md) .

### <a name="spatial-awareness-mesh-observer-better-handles-customization-of-materials"></a>L’observateur de maillage de la sensibilisation spatiale gère mieux la personnalisation des matériaux

Avec cette version, le `Windows Mixed Reality Spatial Mesh Observer` et les `Generic XR SDK Spatial Mesh Observer` composants ont amélioré la gestion des éléments visuels. Les documents sont désormais conservés lorsqu’un maillage a été mis à jour par l’observateur, dans lequel ils ont été réinitialisés à la valeur par défaut VisibleMaterial comme configuré dans le profil.

Cela permet aux développeurs de modifier le matériel de maillage et de ne pas avoir à remplacer les modifications de manière inattendue.

### <a name="linkxml-created-in-the-mixedrealitytoolkitgenerated-folder"></a>Link.xml créé dans le dossier MixedRealityToolkit. generated

Avec l’introduction du gestionnaire de package Unity MRTK, MRTK écrit maintenant un `link.xml` fichier dans le `Assets/MixedRealityToolkit.Generated` dossier, si aucun n’est présent. Il est recommandé d’ajouter ce fichier (et `link.xml.meta` ) au contrôle de code source. Link.xml est utilisé pour influencer la fonctionnalité de [suppression du code managé](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML) de l’éditeur Unity.

Vous trouverez plus d’informations sur le fichier de link.xml MRTK dans l’article [MRTK et suppression de code managé](../updates-deployment/mrtk-and-managed-code-stripping.md) .

### <a name="unity-20193-mrtk-configuration-dialog-no-longer-attempts-to-enable-legacy-xr-support"></a>Unity 2019.3 + : la boîte de dialogue de configuration MRTK ne tente plus d’activer la prise en charge des XR héritées

Pour éviter les conflits potentiels lors de l’utilisation de la plateforme XR d’Unity, l’option permettant d’activer la prise en charge des XR hérités a été supprimée de la boîte de dialogue de configuration MRTK. Si vous le souhaitez, la prise en charge de XR héritée peut être activée, dans Unity 2019, à l’aide de **modifier** les  >  **paramètres du projet**  >
 **lecteur**  >  **XR paramètres**  >  **réalité virtuelle prise en charge**.

### <a name="reduction-in-initializeonload-overhead"></a>Réduction de la surcharge de InitializeOnLoad

Nous avons effectué un travail visant à réduire la quantité de travail qui s’exécute dans les gestionnaires InitializeOnLoad, ce qui devrait entraîner des améliorations de la vitesse de développement de la boucle interne. Les gestionnaires InitializeOnLoad s’exécutent chaque fois qu’un script est compilé, avant d’entrer en mode lecture, et également au lancement de l’éditeur. Ces gestionnaires s’exécutent désormais dans beaucoup moins de cas, ce qui entraîne des améliorations générales de la réactivité des Unity.

Dans certains cas, il y a eu un compromis à effectuer :

- Consultez [configuration du suivi de la main des mouvements LEAP](../supported-devices/leap-motion-mrtk.md) pour l’étape d’intégration supplémentaire.
- Pour ceux qui utilisent ARFoundation, il y a maintenant une étape manuelle supplémentaire dans les étapes de prise en main.
  Consultez [ARFoundation](../supported-devices/using-ar-foundation.md#install-required-packages) pour connaître les nouvelles étapes.
- Pour ceux qui utiliseront la [communication à distance holographique avec le pipeline XR hérité](../features/tools/holographic-remoting.md#legacy-xr-setup-instructions) sur HoloLens 2, il y a maintenant une [étape manuelle](../features/tools/holographic-remoting.md#dotnetwinrt_present-define-written-into-player-settings) à effectuer.

### <a name="bounds-control-graduated"></a>Contrôle des limites gradué

![Contrôle de limites](../features/images/bounds-control/MRTK_BoundsControl_Main.png)

[Le contrôle des limites](../features/ux-building-blocks/bounds-control.md) est sorti de l’expérimental et est fourni avec un ensemble de nouvelles fonctionnalités et de nombreux correctifs de bogues.
Voici une liste des principales caractéristiques de cette mise à jour :

- les propriétés sont fractionnées en configurations, ce qui facilite la configuration du contrôle des limites.
- les configurations peuvent être partagées par le biais d’objets scriptables
- chaque propriété propriété/scriptable est configurable par l’exécution
- la plate-forme de contrôle des limites n’est plus recréée sur les modifications de propriété
- prise en charge des handles de traduction
- prise en charge des contraintes complètes via le gestionnaire de contraintes
- intégration du système élastique (expérimental)

L’ancien cadre englobant est maintenant déconseillé et les objets de jeu existants utilisant un cadre englobant peuvent être [mis à niveau à l’aide de l’outil de migration](../features/tools/migration-window.md) ou de l' [inspecteur de rectangle englobant](../features/ux-building-blocks/bounding-box.md#migrating-to-bounds-control).

### <a name="constraint-manager-component"></a>Composant Gestionnaire de contraintes

Les contraintes peuvent désormais être utilisées par le contrôle des limites et le manipulateur d’objets via le nouveau [composant Gestionnaire de contraintes](../features/ux-building-blocks/constraint-manager.md). Les deux composants créent un gestionnaire de contraintes par défaut et traitent automatiquement les contraintes attachées.

En outre, le gestionnaire de contraintes de comportement automatique est également fourni avec un mode manuel qui permet aux utilisateurs de choisir la contrainte à traiter.
Pour cette raison, la façon dont nous affichons les contraintes dans l’inspecteur de propriété a modifié un peu.

<img src="../features/images/constraint-manager/ManualSelection.png" width="600" alt="Inspector view showing manual constraint manager selection">

Les contraintes appliquées au composant apparaissent maintenant sous la forme d’une liste dans le composant Gestionnaire de contraintes, tandis que le composant qui utilise le gestionnaire de contraintes ( [contrôle de limites](../features/ux-building-blocks/bounds-control.md#constraint-system) ou [manipulateur d’objets](../features/ux-building-blocks/object-manipulator.md#constraint-manager)) affiche désormais le gestionnaire de contraintes et le mode sélectionnés (auto ou manuel).
Pour plus d’informations, consultez la section [Gestionnaire de contraintes](../features/ux-building-blocks/constraint-manager.md) dans notre document.

### <a name="hololens-2-button-material-update"></a>Mise à jour matérielle du bouton HoloLens 2

Mise à jour du matériel de la cage avant du bouton HoloLens 2 pour supprimer la couleur noire dans MRC.

![Mise à jour matérielle du bouton HoloLens 2](https://user-images.githubusercontent.com/13754172/94341269-dcf7c900-0042-11eb-9028-e55abd2ead67.png)

### <a name="description-panel-update-movable-example-scene"></a>Écran de Description mise à jour, exemple de scène mobile

Panneau de description mis à jour. (SceneDescriptionPanelRev. Prefab) la nouvelle conception fournit une barre supérieure pouvant être saisie qui permet à l’utilisateur d’ajuster/déplacer l’intégralité de la scène.

![Mise à jour du panneau de description](https://user-images.githubusercontent.com/13754172/91176366-28a21480-e71d-11ea-9e80-7e219595de9c.png)

### <a name="spatial-mesh-visualization---pulse-on-air-tap"></a>Visualisation de maillage spatial-impulsions sur pression pneumatique

Exemple de nuanceur d’impulsions mis à jour pour le maillage spatial pour correspondre au comportement de l’interpréteur de commandes HoloLens 2.

![Impulsion à l’air](https://user-images.githubusercontent.com/13754172/90310153-d0536180-df29-11ea-939a-e9572d4f5670.gif)

### <a name="elastic-system-experimental"></a>Système élastique (expérimental)

![System2 élastique](../features/images/elastics/Elastics_Main.gif)

MRTK est désormais fourni avec un [système de simulation élastique](../features/elastics/elastic-system.md) qui inclut une large gamme de sous-classes extensibles et flexibles, qui offre des liaisons pour les ressorts de Quaternion à quatre dimensions, les ressorts de volume 3D et les systèmes à ressort linéaires simples.

Actuellement, les composants MRTK suivants prenant en charge le [Gestionnaire élastique](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) peuvent tirer parti des fonctionnalités élastiques :

- [Contrôle de limites](../features/ux-building-blocks/bounds-control.md#elastics-experimental)
- [Manipulateur d’objets](../features/ux-building-blocks/object-manipulator.md#elastics-experimental)

<img src="https://user-images.githubusercontent.com/5544935/88151572-568cba00-cbaf-11ea-91c2-d6b51829b638.gif" width="38%" alt="Expanding an elastic menu">
<img src="https://user-images.githubusercontent.com/5544935/88151578-58567d80-cbaf-11ea-8f96-d24f2cf0d6e9.gif" width="45.7%" alt="Grabbing an elastic coffee cup">

### <a name="joystick-experimental"></a>Manette de jeu (expérimental)

Exemple d’interface de manette de jeu qui peut contrôler un objet cible volumineux.

![Croix](https://user-images.githubusercontent.com/43013191/86156887-769ef100-babb-11ea-85be-ed6a6aed89d2.png)

### <a name="color-picker-experimental"></a>Sélecteur de couleurs (expérimental)

Contrôle expérimental qui facilite la modification des couleurs matérielles sur un objet au moment de l’exécution.

![Trois méthodes différentes de contrôle de sélecteur de couleurs](https://user-images.githubusercontent.com/43013191/85468370-3b536e00-b561-11ea-812c-b3f7d43dd999.png)

![Quatre méthodes différentes de contrôle de sélecteur de couleurs](https://user-images.githubusercontent.com/43013191/85468994-fa0f8e00-b561-11ea-89f2-0810d1998518.png)

## <a name="breaking-changes"></a>Changements cassants

### <a name="assembly-definition-files-changes"></a>Modifications des fichiers de définition d’assembly

Certains fichiers asmdef sont modifiés et prennent désormais en charge uniquement Unity 2018.4.13 F1 ou version ultérieure. Les erreurs de compilation s’affichent lors de la mise à jour vers MRTK 2,5 dans les versions antérieures d’Unity. Vous pouvez résoudre ce problème en accédant à `Assets\MRTK\Providers\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.asmdef` dans la fenêtre projet et en supprimant la référence manquante dans l’inspecteur. Répétez ces étapes avec `Assets\MRTK\Providers\Oculus\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.Oculus.asmdef` et `Assets\MRTK\Providers\WindowsMixedReality\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.WMR.asmdef` . Remarque : vous devez annuler les modifications en remplaçant ces trois fichiers asmdef par les fichiers d’origine (c’est-à-dire non modifiés) lors de la mise à niveau vers Unity 2019.

### <a name="imixedrealitypointermediator"></a>IMixedRealityPointerMediator

Cette interface a été mise à jour pour avoir une nouvelle fonction :

```csharp
void SetPointerPreferences(IPointerPreferences pointerPreferences);
```

Si vous avez un médiateur de pointeur personnalisé qui n’est pas sous-classé DefaultPointerMediator, vous devez implémenter cette nouvelle fonction. Pour plus d’informations sur les raisons de cet ajout, consultez [ce problème](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8243) . Cela a été ajouté pour s’assurer que les préférences de pointeur soient passées explicitement au Médiateur, au lieu d’être effectuées implicitement en fonction de la présence d’un constructeur qui prenait un IPointerPreferences.

### <a name="rest--device-portal-api"></a>API du portail Rest/Device

La `UseSSL` propriété statique a été déplacée de `Rest` vers `DevicePortal` .

Si vous l’avez fait précédemment...

```csharp
Rest.UseSSL = true
```

Procédez maintenant...

```csharp
DevicePortal.UseSSL = true
```

### <a name="linkxml"></a>Link.xml

Si une application utilisait précédemment la distribution NuGet de MRTK, le `link.xml` fichier a été supprimé du package de base. Pour restaurer les règles de conservation du code, l’ouverture du projet dans Unity une fois crée un fichier par défaut `link.xml` dans `Assets/MixedRealityToolkit.Generated` . Il est recommandé d’ajouter ce fichier (et `link.xml.meta` ) au contrôle de code source.

### <a name="transform-constraint-changes"></a>Transformer les modifications de contrainte

La propriété TargetTransform a été marquée comme obsolète, car elle n’était pas utilisée par le système de contraintes. La logique de contrainte est basée sur la transformation transmise dans les méthodes Initialize et apply. Les contraintes utilisateur dérivées qui reposent sur cette propriété peuvent mettre en cache les TargetTransform dans leur implémentation en stockant la transformation du composant de contrainte pour obtenir le même comportement.

Le type de données de la pose du monde stocké `worldPoseOnManipulationStart` est passé de MixedRealityPose à MixedRealityTransform, ce qui inclut la valeur de l’échelle locale de l’objet manipulé. Avec cette modification, il n’est pas nécessaire de mettre en cache séparément les valeurs de mise à l’échelle initiales.

### <a name="new-property-in-imixedrealitydictationsystem"></a>Nouvelle propriété dans IMixedRealityDictationSystem

Une nouvelle propriété `AudioClip` a été ajoutée à l’interface IMixedRealityDictationSystem. La `AudioClip` propriété permet d’accéder au clip audio associé à la session de dictée actuelle. Les utilisateurs doivent implémenter la propriété dans leurs scripts qui implémentent l’interface.

### <a name="service-facades-turn-down"></a>Les façades de service deviennent inactives

Les façades de services sont retournées dans 2,5. Cette fonctionnalité a été ajoutée à l’origine pour faciliter la configuration des profils MRTK (en créant des GameObjects factices in-Scene qui représentaient chacun des services de MRTK). À long terme, nous voulons éviter de créer des objets factices dans le jeu et tenter de les maintenir synchronisés (la synchronisation des données et les problèmes de « source de vérité » sont notoirement difficiles à mettre à l’échelle et à se trouver à droite).

Dans 2,5, les gestionnaires de façade de service sont conservés pour s’assurer que la mise à niveau du projet s’effectue correctement : les façades qui existent dans le projet seront supprimées par le gestionnaire de façade de service pour s’assurer que les scènes ouvertes dans 2,5 soient automatiquement corrigées.

Le code restant associé à la fonctionnalité de façade de service sera supprimé dans une version ultérieure.

### <a name="addition-of-motion-controller-to-input-simulation-service"></a>Ajout d’un contrôleur de mouvement au service de simulation d’entrée

La simulation du contrôleur de mouvement est désormais proposée en mode de lecture de l’éditeur, en même temps que la simulation existante. Pour activer cette modification, de nombreuses fonctions/champs/propriétés en cours sont désormais marqués comme obsolètes, avec `InputSimulationService.cs` et `MixedRealityInputSimulationProfile.cs` obtenant les modifications les plus importantes. La logique et le comportement du code pertinent restent en grande partie identiques et la majorité des fonctions obsolètes, etc., sont liées au remplacement de la référence « main » par le terme « Controller » plus générique (par exemple, de `DefaultHandSimulationMode` à `DefaultControllerSimulationMode` ). Outre l’obtention de nouveaux noms, le type de retour de certaines nouvelles fonctions est mis à jour pour correspondre à la modification du nom/du comportement (par exemple, `GetControllerDevice` en fonction des retours d’origine à la `GetHandDevice` `BaseController` place de `SimulatedHand` ).

`IInputSimulationService` a maintenant de nouvelles propriétés `MotionControllerDataLeft` et `MotionControllerDataRight` . `MixedRealityInputSimulationProfile` comprend désormais de nouveaux champs pour le mappage du clavier de certains boutons du contrôleur de mouvement.

## <a name="known-issues"></a>Problèmes connus

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a>CameraCache peut créer un nouvel appareil photo à l’arrêt

Dans certains cas (par exemple, lorsque vous utilisez le fournisseur LeapMotion dans l’éditeur Unity), CameraCache peut recréer MainCamera lors de l’arrêt. Pour plus d’informations, consultez [ce problème](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) .

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a>FileNotFoundException quand des exemples sont importés via le gestionnaire de package Unity

Selon la longueur du chemin d’accès au projet, l’importation d’exemples par le biais du gestionnaire de package Unity peut générer des messages FileNotFoundException dans la console Unity. La cause est le chemin d’accès au fichier « manquant » qui est plus long que MAX_PATH (256 caractères). Pour résoudre le, raccourcissez la longueur du chemin d’accès au projet.

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a>Aucun Spatializer n’a été spécifié. L’application ne prend pas en charge le son spatial

Un avertissement « aucun Spatializer n’a été spécifié » s’affiche si un Spatializer audio n’est pas configuré. Cela peut se produire si aucun package XR n’est installé, car Unity comprend spatializers dans ces packages.

Pour résoudre le, vérifiez les éléments suivants :

- **Fenêtre**  >  Un ou plusieurs packages XR sont installés sur le **Gestionnaire de package**
- **Boîte à outils**  >  de réalité mixte **Utilitaires**  >  **Configurer un projet Unity** et faire une sélection pour l' **audio Spatializer**

  ![Sélectionner les Spatializer audio](images/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a>NullReferenceException : la référence d’objet n’est pas définie sur une instance d’un objet (SceneTransitionService.Initialize)

Dans certains cas, l’ouverture `EyeTrackingDemo-00-RootScene` de peut provoquer une exception NullReferenceException dans la méthode Initialize de la classe SceneTransitionService.
Cette erreur est due au fait que le profil de configuration du service de transition de scène est désactivé. Pour résoudre le, procédez comme suit :

- Accéder à l' `MixedRealityToolkit` objet dans la hiérarchie
- Dans la fenêtre de l’inspecteur, sélectionnez `Extensions`
- S’il n’est pas développé, développez `Scene Transition Service`
- Définir la valeur de `Configuration Profile` sur **MRTKExamplesHubSceneTransitionServiceProfile**

![Corriger la transition de la scène](images/FixSceneTransitionProfile.png)

### <a name="oculus-quest"></a>Oculus Quest

Il existe actuellement un problème connu lié à l’utilisation du [plug-in Oculus XR avec pour cibler des plateformes autonomes](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/). Consultez le suivi des bogues/forums/notes de publication Oculus pour les mises à jour.

Le bogue est signalé par cet ensemble de 3 erreurs :

![Erreur du plug-in Oculus XR](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a>UnityUI et TextMeshPro

Il existe un problème connu pour les versions plus récentes de TextMeshPro (1.5.0 + ou 2.1.1 +), où la taille de police par défaut pour les listes déroulantes et l’espacement des caractères de police gras ont été modifiés.

![Image TMP](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

Pour ce faire, vous pouvez passer à une version antérieure de TextMeshPro. Pour plus d’informations, consultez [#8556 de problèmes](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) .
