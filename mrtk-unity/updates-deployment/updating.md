---
title: Mise à jour à partir de versions antérieures
description: Documentation à migrer à partir d’une version antérieure de MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 04/19/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 5a914d6408d346dac0bf6c683f401564e875f4d8
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175107"
---
# <a name="updating-from-earlier-versions"></a>Mise à jour à partir de versions antérieures

- [Mise à niveau vers une nouvelle version de MRTK](#upgrading-to-a-new-version-of-mrtk)
- [2.3.0 à 2.4.0](#updating-230-to-240)
- [2.2.0 à 2.3.0](#updating-220-to-230)
- [2.1.0 à 2.2.0](#updating-210-to-220)
- [2.0.0 à 2.1.0](#updating-200-to-210)
- [RC2 à 2.0.0](#updating-rc2-to-200)

## <a name="finding-the-current-version"></a>Recherche de la version actuelle 

Suivez ces instructions pour déterminer quelle version du MRTK vous utilisez actuellement :

1. Ouvrez votre projet MRTK dans Unity
2. accédez au dossier « MixedRealityToolkit » dans la fenêtre de Project
3. Ouvrez le fichier appelé « version ».

Si le fichier et le dossier ci-dessus n’existent pas, c’est que vous utilisez une version plus récente de MRTK. Dans ce cas, essayez ce qui suit :

1. accédez au dossier « Mixed reality Shared Computer Toolkit Foundation ».
2. Cliquez sur l' package.jspour afficher un aperçu dans Unity ou l’ouvrir avec un éditeur de texte.
3. Recherchez la ligne avec le mot « version : » 

## <a name="upgrading-to-a-new-version-of-mrtk"></a>Mise à niveau vers une nouvelle version de MRTK

*Il est vivement recommandé d’exécuter l' [outil de migration](../features/tools/migration-window.md) après avoir mis à jour la mise à jour MRTK pour qu’il soit* mis à niveau et mis à niveau à partir de composants déconseillés et ajusté en modifications avec rupture. L’outil de migration fait partie du package d' **Outils** .

Les instructions ci-dessous décrivent le chemin de mise à niveau de 2.4.0 vers 2.5.0. Si votre projet se trouve sur 2.3.0 ou une version antérieure, prenez connaissance des modifications apportées [entre les versions](#updating-230-to-240) pour comprendre le chemin de mise à niveau, ou lisez les [instructions de la version](https://microsoft.github.io/MixedRealityToolkit-Unity/version/releases/2.4.0/Documentation/Updating.html) précédente pour effectuer une mise à niveau de version par version.

### <a name="mixed-reality-feature-tool"></a>Mixed Reality Feature Tool
Le moyen le plus simple de mettre à niveau MRTK vers une version plus récente MRTK consiste à utiliser l’outil de la [fonctionnalité de réalité mixte](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) pour télécharger les packages les plus récents et les charger directement dans votre projet Unity.

Si le projet utilisait précédemment des fichiers de ressources Unity (. pour Unity), veuillez consulter [ces instructions](#switching-from-unity-asset-files-to-mixed-reality-feature-tool). 

### <a name="unity-asset-unitypackage-files"></a>Fichiers de ressources Unity (. pour Unity)

Un autre chemin de mise à niveau consiste à télécharger manuellement les packages MRTK Unity et à les appliquer à votre projet. Consultez les étapes ci-dessous,

1. Enregistrez une copie de votre projet actuel, au cas où vous atteigniez des vigilant à tout moment dans les étapes de mise à niveau.
1. Fermer Unity
1. Dans le dossier *composants* , supprimez les dossiers **MRTK** suivants, ainsi que leurs fichiers. meta (le projet n’a peut-être pas tous les dossiers listés)
    - MRTK/noyau
    - MRTK/exemples
    - MRTK/extensions
    - MRTK/fournisseurs
    - MRTK/SDK
    - MRTK/services
    - MRTK/StandardAssets
    > [!IMPORTANT]
    > Si des modifications ont été apportées aux nuanceurs MRTK, créez une sauvegarde locale avant de supprimer le dossier MRTK/StandardAssets
    - MRTK/outils
    > [!IMPORTANT]
    > Ne supprimez pas le dossier **MixedRealityToolkit. generated** , ni son fichier. meta.
1. Supprimer le dossier de **bibliothèque**
    > [!IMPORTANT]
    > Certains outils Unity, comme Unity collab, enregistrent les informations de configuration dans le dossier de bibliothèque. Si vous utilisez un outil qui effectue cette opération, commencez par copier le dossier de données de l’outil à partir de la bibliothèque avant de le supprimer, puis restaurez-le après la régénération de la bibliothèque.
1. Rouvrir le projet dans Unity
1. Importer les nouveaux packages Unity
    - Fondation- _importer ce package en premier_
    - Outils
    - Facultatif Extensions
    > [!NOTE]
    > Si des extensions supplémentaires ont été installées, elles devront peut-être être réimportées.
    - Facultatif Illustre
1. Fermez Unity et supprimez le dossier de **bibliothèque** (lisez la remarque ci-dessous !). Cette étape est nécessaire pour forcer Unity à actualiser sa base de données de ressources et à harmoniser les profils personnalisés existants.
1. Lancer Unity et pour chaque scène du projet
    - Supprime **MixedRealityToolkit** et **MixedRealityPlayspace**, le cas échéant, de la hiérarchie. Cette opération supprimera la caméra principale, mais elle sera recréée à l’étape suivante. Si des propriétés de la caméra principale ont été modifiées manuellement, elles devront être réappliquées manuellement une fois la nouvelle caméra créée.
    - Sélectionnez **MixedRealityToolkit-> ajouter à la scène et configurer**
    - Sélectionnez **MixedRealityToolkit-> Utilities-> mettre à jour-> les profils de mappage de contrôleur** (ne doit être effectué qu’une seule fois). cela permet de mettre à jour tous les profils de mappage de contrôleur personnalisés avec les données et les axes mis à jour, tout en laissant vos actions d’entrée personnalisées intactes.
1. exécutez l' [outil de migration](../features/tools/migration-window.md) et exécutez l’outil sur la *Project complète* pour vous assurer que l’ensemble de votre code est mis à jour vers la dernière version.
   La fenêtre de migration contient un certain nombre de gestionnaires de migration différents, qui doivent chacun être exécutés eux-mêmes. Cette étape implique les opérations suivantes :
   - Sélectionnez le premier gestionnaire de migration dans la liste déroulante **Gestionnaire de migration** .
   - cliquez sur le bouton « Project complet ».
   - Cliquez sur le bouton « Ajouter le projet complet pour la migration » (cela permet d’analyser l’ensemble du projet pour rechercher les objets à migrer).
   - Cliquez sur le bouton « migrer » qui doit être activé si des objets pouvant être migrés ont été trouvés.
   - Répétez les trois étapes précédentes pour chacun des gestionnaires de migration dans la liste déroulante.
     (Consultez [ce problème](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8552) qui couvre le travail qui peut être effectué pour simplifier ce processus de migration dans une version ultérieure)

### <a name="switching-from-unity-asset-files-to-mixed-reality-feature-tool"></a>Basculement depuis les fichiers de ressources Unity vers l’outil de la fonctionnalité de réalité mixte

Passer des fichiers de ressources Unity aux packages d’outils de la fonctionnalité de réalité mixte offre un certain nombre d’avantages :

- Mise à jour plus facile
- Temps de compilation plus rapides
- moins de projets dans la solution Visual Studio

La modification de l’outil de la fonctionnalité de réalité mixte nécessite un ensemble d’étapes manuelles à usage unique.

1. Enregistrez une copie de votre projet actuel.
1. Fermer Unity
1. Dans le dossier *composants* , supprimez les dossiers **MRTK** suivants, ainsi que leurs fichiers. meta (le projet n’a peut-être pas tous les dossiers listés)
    - MRTK/noyau
    - MRTK/exemples
    - MRTK/extensions
    - MRTK/fournisseurs
    - MRTK/SDK
    - MRTK/services
    - MRTK/StandardAssets
    > [!IMPORTANT]
    > Si des modifications ont été apportées aux nuanceurs MRTK, créez une sauvegarde locale avant de supprimer le dossier MRTK/StandardAssets
    - MRTK/outils
    > [!IMPORTANT]
    > Ne supprimez pas le dossier **MixedRealityToolkit. generated** , ni son fichier. meta.
1. Supprimer le dossier de **bibliothèque**
    > [!IMPORTANT]
    > Certains outils Unity, comme Unity collab, enregistrent les informations de configuration dans le dossier de bibliothèque. Si vous utilisez un outil qui effectue cette opération, commencez par copier le dossier de données de l’outil à partir de la bibliothèque avant de le supprimer, puis restaurez-le après la régénération de la bibliothèque.
1. Rouvrir le projet dans Unity

une fois les étapes précédentes effectuées, exécutez l’outil de la [fonctionnalité de réalité mixte](#mixed-reality-feature-tool) et importez la version souhaitée de la réalité mixte Shared Computer Toolkit.

## <a name="updating-230-to-240"></a>Mise à jour de 2.3.0 vers 2.4.0

[Renommages](#folder-renames-in-240) 
 de dossiers [Modifications](#api-changes-in-240) de l’API

### <a name="folder-renames-in-240"></a>Renommages de dossiers dans 2.4.0

Les dossiers MixedRealityToolkit ont été renommés et déplacés dans une hiérarchie commune dans la version 2,4. Si une application utilise des chemins d’accès codés en dur pour MRTK ressources, elle doit être mise à jour selon le tableau suivant.

| Dossier précédent | Nouveau dossier |
| --- | --- |
| MixedRealityToolkit | MRTK/noyau |
| MixedRealityToolkit. exemples | MRTK/exemples |
| MixedRealityToolkit. extensions | MRTK/extensions |
| MixedRealityToolkit. Providers | MRTK/fournisseurs |
| MixedRealityToolkit. SDK | MRTK/SDK |
| MixedRealityToolkit. services | MRTK/services |
| MixedRealityToolkit. tests | MRTK/tests |
| MixedRealityToolkit. Tools | MRTK/outils |

> [!IMPORTANT]
> `MixedRealityToolkit.Generated`Contient les fichiers générés par le client et reste inchangé.

### <a name="eye-gaze-setup-in-240"></a>Paramétrage des yeux dans 2.4.0

Cette version de MRTK modifie les étapes requises pour la configuration des regards oculaires. La case à cocher _« IsEyeTrackingEnabled »_ se trouve dans les paramètres de pointage du profil de pointeur d’entrée. L’activation de cette case à cocher activera le point de présence oculaire, et non le point de regard par défaut.

Pour plus d’informations sur ces modifications et pour obtenir des instructions complètes pour la configuration du suivi des yeux, consultez l’article [suivi des yeux](../features/input/eye-tracking/eye-tracking-basic-setup.md) .

### <a name="eye-gaze-pointer-behavior-in-240"></a>Comportement du pointeur en forme d’oeil dans 2.4.0

Le comportement du pointeur par défaut de l’œil oculaire a été modifié pour correspondre au comportement du pointeur par défaut de l’en-tête. Un pointeur en forme d’oeil est automatiquement supprimé une fois qu’une main est détectée. Le pointeur vers le regard de l’œil redevient visible après avoir dit « Select ».

Pour plus d’informations sur les configurations en regard et sur la main, consultez l’article sur les [yeux et les mains](../features/input/eye-tracking/eye-tracking-eyes-and-hands.md#how-to-keep-gaze-pointer-always-on) .

### <a name="api-changes-in-240"></a>Modifications de l’API dans 2.4.0

**Classes de contrôleur personnalisé**

Les classes de contrôleur personnalisé devaient auparavant définir `SetupDefaultInteractions(Handedness)` . Cette méthode a été rendue obsolète dans 2,4, car le paramètre de port était redondant avec la main propre à la classe de contrôleur. La nouvelle méthode n’a aucun paramètre. De plus, de nombreuses classes de contrôleur ont défini cela de la même façon ( `AssignControllerMappings(DefaultInteractions);` ), de sorte que l’appel complet a été refactorisé en `BaseController` et a fait une substitution facultative au lieu de required.

**Propriétés de regard de l’œil**

La `UseEyeTracking` propriété de l' `GazeProvider` implémentation de `IMixedRealityEyeGazeProvider` a été renommée en `IsEyeTrackingEnabled` .

Si vous l’avez fait précédemment...

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.UseEyeTracking = true;
}
```

Procédez maintenant...

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.IsEyeTrackingEnabled = true;
}
```

**Propriétés WindowsApiChecker**

Les propriétés WindowsApiChecker suivantes ont été marquées comme obsolètes. Utilisez `IsMethodAvailable` `IsPropertyAvailable` ou `IsTypeAvailable` .

- UniversalApiContractV8_IsAvailable
- UniversalApiContractV7_IsAvailable
- UniversalApiContractV6_IsAvailable
- UniversalApiContractV5_IsAvailable
- UniversalApiContractV4_IsAvailable
- UniversalApiContractV3_IsAvailable

Il n’est pas prévu d’ajouter des propriétés à WindowsApiChecker pour les futures versions de contrat d’API.

**GltfMeshPrimitiveAttributes en lecture seule**

Les attributs primitifs de maillage gltf utilisés pour être définissables, ils sont désormais en lecture seule. Leurs valeurs seront définies une fois lors de la désérialisation.

### <a name="custom-button-icon-migration"></a>Icône de bouton personnalisé migration

Les icônes de bouton personnalisées précédemment nécessitaient l’attribution d’un nouveau matériau au convertisseur Quad du bouton. Cela n’est plus nécessaire et nous vous recommandons de déplacer les textures d’icône personnalisées dans un IconSet. Les matériaux et les icônes personnalisés existants sont conservés. Toutefois, elles seront moins optimales jusqu’à leur mise à niveau.
Pour mettre à niveau les ressources sur tous les boutons du projet au nouveau format recommandé, utilisez ButtonConfigHelperMigrationHandler.
(Shared Computer Toolkit de la réalité mixte-> utilitaires-> la fenêtre de migration-> sélection du gestionnaire de migration-> Microsoft. MixedReality. Shared Computer Toolkit. Utilities. ButtonConfigHelperMigrationHandler)

![Boîte de dialogue mettre à niveau la fenêtre](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

Si aucune icône n’est trouvée dans le jeu d’icônes par défaut lors de la migration, un jeu d’icônes personnalisé est créé dans MixedRealityToolkit. generated/CustomIconSets. Une boîte de dialogue indiquera que cette opération a eu lieu.

![Notification d’icône personnalisée](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

## <a name="updating-220-to-230"></a>Mise à jour de 2.2.0 vers 2.3.0

- [Modifications d'API](#api-changes-in-230)

### <a name="api-changes-in-230"></a>Modifications de l’API dans 2.3.0

**ControllerPoseSynchronizer**

Le champ privé ControllerPoseSynchronizer. droitier a été marqué comme obsolète. Cela doit avoir un impact minimal sur les applications, car le champ n’est pas visible en dehors de sa classe.

La méthode setter de la propriété ControllerPoseSynchronizer. de la main publique a été supprimée ([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)).

**MSBuild pour unity**

cette version de MRTK utilise une version plus récente de MSBuild pour unity que les versions précédentes. pendant le chargement du projet, si la version antérieure est répertoriée dans le manifeste du gestionnaire de packages unity, la boîte de dialogue de configuration s’affiche, avec l’option activer MSBuild pour unity activée. L’application effectue une mise à niveau.

**ScriptingUtilities**

La classe ScriptingUtilities a été marquée comme obsolète et a été remplacée par ScriptUtilities, dans Microsoft. MixedReality. Shared Computer Toolkit. Éditeur. Utilities assembly. La nouvelle classe affine le comportement précédent et ajoute la prise en charge de la suppression des définitions de script.

Bien que le code existant continue à fonctionner dans la version 2.3.0, il est recommandé de mettre à jour vers la nouvelle classe.

**ShellHandRayPointer**

Les membres lineRendererSelected et lineRendererNoTarget de la classe ShellHandRayPointer ont été remplacés par lineMaterialSelected et lineMaterialNoTarget, respectivement ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)).

Remplacez lineRendererSelected par lineMaterialSelected et/ou lineRendererNoTarget par lineMaterialNoTarget pour résoudre les erreurs de compilation.

**Startupbehavior lui faisants de l’observateur spatial**

Les observateurs spatiaux basés sur la `BaseSpatialObserver` classe honorent désormais la valeur de startupbehavior lui faisant lorsqu’ils sont réactivés ([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)).

Aucune modification n’est requise pour tirer parti de ce correctif.

**Prefabs de contrôle d’expérience utilisateur mis à jour pour utiliser PressableButton**

Les prefabs suivants utilisent désormais le composant PressableButton au lieu de TouchHandler pour une interaction proche ([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070))

- AnimationButton
- Bouton
- ButtonHoloLens1
- ButtonHoloLens1Toggle
- Case à cocher
- RadialSet
- ToggleButton
- Bouton bascule
- UnityUIButton
- UnityUICheckboxButton
- UnityUIRadialButton
- UnityUIToggleButton

Le code d’application peut nécessiter une mise à jour en raison de cette modification.

**Espace de noms WindowsMixedRealityUtilities**

L’espace de noms de WindowsMixedRealityUtilities a été modifié à partir de Microsoft. MixedReality. Shared Computer Toolkit. WindowsMixedReality. Input vers Microsoft. MixedReality. Shared Computer Toolkit. WindowsMixedReality ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989)).

Mettez à jour les instructions #using pour résoudre les erreurs de compilation.

## <a name="updating-210-to-220"></a>Mise à jour de 2.1.0 vers 2.2.0

- [Modifications d'API](#api-changes-in-220)

### <a name="api-changes-in-220"></a>Modifications de l’API dans 2.2.0

**IMixedRealityBoundarySystem. Contains**

Cette méthode prenait auparavant un enum expérimental défini par Unity spécifique. Elle prend désormais une énumération définie par MRTK qui est identique à l’énumération Unity. Cette modification permet de préparer le MRTK pour les API de limite futures d’Unity.

**MixedRealityServiceProfileAttribute**

Pour mieux décrire les conditions requises pour la prise en charge d’un profil, MixedRealityServiceProfileAttribute a été mis à jour pour ajouter une collection facultative de types exclus. Dans le cadre de cette modification, la propriété ServiceType a été modifiée de type en type [] et renommée en RequiredTypes.

Une deuxième propriété, ExcludedTypes a également été ajoutée.

## <a name="updating-200-to-210"></a>Mise à jour de 2.0.0 vers 2.1.0

- [Modifications d'API](#api-changes-in-210)
- [Modifications de profil](#profile-changes-in-210)

### <a name="api-changes-in-210"></a>Modifications de l’API dans 2.1.0

**BaseNearInteractionTouchable**

Le `BaseNearInteractionTouchable` a été modifié pour marquer la `OnValidate` méthode comme étant virtuelle. Les classes qui étendent `BaseNearInteractionTouchable` (p. ex. `NearInteractionTouchableUnityUI` ) ont été mises à jour pour refléter cette modification.

**ColliderNearInteractionTouchable**

La classe `ColliderNearInteractionTouchable` a été déconseillée. Mettez à jour les références de code à utiliser `BaseNearInteractionTouchable` .

**IMixedRealityMouseDeviceManager**

**_Ajoute_**

`IMixedRealityMouseDeviceManager` a été ajouté `CursorSpeed` et les `WheelSpeed` Propriétés. Ces propriétés permettent aux applications de spécifier une valeur de multiplicateur par laquelle la vitesse du curseur et de la roue, respectivement, sera mise à l’échelle.

Il s’agit d’une modification avec rupture qui requiert la modification des implémentations existantes du gestionnaire de périphériques de la souris.

>[!NOTE]
>Cette modification n’est pas à compatibilité descendante avec la version 2.0.0.

**_Déprécié_**

la `MouseInputProfile` propriété a été marquée comme obsolète et sera supprimée d’une future version de la Shared Computer Toolkit de réalité mixte Microsoft. Il est recommandé que le code d’application n’utilise plus cette propriété.

**Avec interaction**

les méthodes et propriétés suivantes sont dépréciées et seront supprimées d’une version future de la Shared Computer Toolkit de réalité mixte Microsoft. Il est recommandé de mettre à jour le code d’application conformément aux instructions contenues dans l’attribut Obsolete et affiché dans la console.

- `public bool Enabled`
- `public bool FocusEnabled`
- `public void ForceUpdateThemes()`
- `public bool IsDisabled`
- `public bool IsToggleButton`
- `public int GetDimensionIndex()`
- `public State[] GetStates()`
- `public bool RequiresFocus`
- `public void ResetBaseStates()`
- `public virtual void SetCollision(bool collision)`
- `public virtual void SetCustom(bool custom)`
- `public void SetDimensionIndex(int index)`
- `public virtual void SetDisabled(bool disabled)`
- `public virtual void SetFocus(bool focus)`
- `public virtual void SetGesture(bool gesture)`
- `public virtual void SetGestureMax(bool gesture)`
- `public virtual void SetGrab(bool grab)`
- `public virtual void SetInteractive(bool interactive)`
- `public virtual void SetObservation(bool observation)`
- `public virtual void SetObservationTargeted(bool targeted)`
- `public virtual void SetPhysicalTouch(bool touch)`
- `public virtual void SetPress(bool press)`
- `public virtual void SetTargeted(bool targeted)`
- `public virtual void SetToggled(bool toggled)`
- `public virtual void SetVisited(bool visited)`
- `public virtual void SetVoiceCommand(bool voice)`

**NearInteractionTouchableSurface**

La `NearInteractionTouchableSurface` classe a été ajoutée et sert à présent de classe de base pour `NearInteractionTouchable` et `NearInteractionTouchableUnityUI` .

### <a name="profile-changes-in-210"></a>Modifications de profil dans 2.1.0

**Profil de suivi de la main**

Les visualisations de la maille et de la jointure de la main disposent désormais d’un éditeur et de paramètres de lecteur distincts. Le profil de suivi de la main a été mis à jour pour permettre la définition de ces visualisations sur ; Rien, tout, éditeur ou joueur.

![Modes de visualisation manuelle](../release-notes/images/HandTrackingVisualizationModes.png)

Vous devrez peut-être mettre à jour les profils de suivi de main personnalisés pour qu’ils fonctionnent correctement avec la version 2.1.0.

>[!NOTE]
>Cette modification n’est pas à compatibilité descendante avec la version 2.0.0.

**Profil de simulation d’entrée**

Le système de simulation d’entrée a été mis à niveau, ce qui modifie certains paramètres dans le profil de simulation d’entrée. Certaines modifications ne peuvent pas être migrées automatiquement et les utilisateurs peuvent trouver que les profils utilisent des valeurs par défaut.

1. Toutes les liaisons de bouton de clavier et de bouton de la souris dans le profil ont été remplacées par une `KeyBinding` structure générique, qui stocke le type de liaison (clé ou souris), ainsi que le code de liaison réel (respectivement le numéro de code ou de bouton de la souris). La structure a son propre inspecteur, qui autorise l’affichage unifié et offre un outil de liaison automatique pour définir rapidement des combinaisons de touches en appuyant sur la touche correspondante au lieu de sélectionner dans une liste déroulante très volumineuse.

    - FastControlKey
    - ToggleLeftHandKey
    - ToggleRightHandKey
    - LeftHandManipulationKey
    - RightHandManipulationKey

1. `MouseLookToggle` était précédemment inclus dans l' `MouseLookButton` enum en tant que `InputSimulationMouseButton.Focused` , il s’agit maintenant d’une option distincte. Quand cette option est activée, l’appareil photo continue de pivoter avec la souris après avoir relâché le bouton, jusqu’à ce que la touche Échap est enfoncée.
1. `HandDepthMultiplier` la valeur par défaut a été abaissée de 0,1 à 0,03 pour tenir compte de certaines modifications apportées à la simulation d’entrée. Si l’appareil photo bouge trop rapidement lors du défilement, essayez de réduire cette valeur.
1. Les touches de rotation des mains ont été supprimées, la rotation manuelle est désormais contrôlée par la souris. Le maintien de `HandRotateButton` (Ctrl) avec la clé de manipulation gauche/droite (lshift/Space) permet la rotation manuelle.
1. Un nouvel axe « UpDown » a été introduit dans la liste des axes d’entrée. Cela contrôle le mouvement de l’appareil photo dans la verticale et les valeurs par défaut pour les touches Q/E, ainsi que pour les boutons de déclenchement du contrôleur.

Pour plus d’informations sur ces modifications, consultez l’article [service de simulation d’entrée](../features/input-simulation/input-simulation-service.md) .

**Profil du fournisseur de données de souris**

Le profil du fournisseur de données de la souris a été mis à jour pour exposer les nouvelles `CursorSpeed` `WheelSpeed` Propriétés et. Les profils personnalisés existants auront automatiquement les valeurs par défaut fournies. Lorsque le profil est enregistré, ces nouvelles valeurs sont conservées.

**Profil de mappage du contrôleur**

Certains axes et types d’entrée ont été mis à jour dans 2.1.0, en particulier autour de la plateforme OpenVR. Veillez à sélectionner **MixedRealityToolkit-> Utilities-> mise à jour-> les profils de mappage de contrôleur lors de** la mise à niveau. Cela permet de mettre à jour tous les profils de mappage de contrôleur personnalisés avec les données et les axes mis à jour, tout en conservant les actions d’entrée personnalisées qui leur sont affectées.

## <a name="updating-rc2-to-200"></a>Mise à jour de RC2 vers 2.0.0

entre les versions RC2 et 2.0.0 de la Shared Computer Toolkit de réalité mixte Microsoft, des modifications peuvent avoir un impact sur les projets existants. Ce document décrit ces modifications et explique comment mettre à jour des projets vers la version 2.0.0.

- [Modifications d'API](#api-changes-in-200)
- [Modifications du nom de l’assembly](#assembly-name-changes-in-200)

### <a name="api-changes-in-200"></a>Modifications de l’API dans 2.0.0

Depuis la version RC2, un certain nombre de modifications de l’API ont été apportées, notamment certaines qui peuvent altérer des projets existants. Les sections suivantes décrivent les modifications qui se sont produites entre les versions RC2 et 2.0.0.

**MixedRealityToolkit**

Les propriétés publiques suivantes sur l’objet MixedRealityToolkit ont été dépréciées.

- `RegisteredMixedRealityServices` ne contient plus la collection de fournisseurs de données et de services d’extensions inscrits.

Pour accéder aux services d’extension, utilisez `MixedRealityServiceRegistry.TryGetService<T>` . Pour accéder aux fournisseurs de données, effectuez un cast de l’instance de service vers [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) et utilisez `GetDataProvider<T>` .

Utilisez [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) ou [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) à la place pour les propriétés déconseillées suivantes

- `ActiveSystems`
- `InputSystem`
- `BoundarySystem`
- `CameraSystem`
- `SpatialAwarenessSystem`
- `TeleportSystem`
- `DiagnosticsSystem`
- `SceneSystem`

**CoreServices**

La [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) classe est le remplacement des accesseurs système statiques (ex : BoundarySystem) trouvés dans l' `MixedRealityToolkit` objet.

>[!IMPORTANT]
>Les `MixedRealityToolkit` accesseurs système ont été dépréciés dans la version 2.0.0 et seront supprimés dans une prochaine version de MRTK.

L’exemple de code suivant illustre l’ancien et le nouveau modèle.

``` c#
// Old
GameObject playAreaVisualization = MixedRealityToolkit.BoundarySystem?.GetPlayAreaVisualization();

// New
GameObject playAreaVisualization = CoreServices.BoundarySystem?.GetPlayAreaVisualization();
```

L’utilisation de la nouvelle classe CoreSystem garantit que le code de votre application n’aura pas besoin d’être mis à jour si vous modifiez l’application pour utiliser un autre bureau d’enregistrement de service (par exemple, l’un des gestionnaires de service expérimentaux).

**IMixedRealityRaycastProvider**

Avec l’ajout de IMixedRealityRaycastProvider, le profil de configuration du système d’entrée a été modifié. Si vous avez un profil personnalisé, vous pouvez recevoir les erreurs dans l’image suivante lorsque vous exécutez votre application.

![Sélection du fournisseur Raycast 1](../release-notes/images/UnableToRegisterRaycastProvider.png)

Pour résoudre ces problème, ajoutez une instance IMixedRealityRaycastProvider à votre profil de système d’entrée.

![Sélection du fournisseur Raycast 2](../release-notes/images/SelectRaycastProvider.png)

**Système d’événements**

- Les `IMixedRealityEventSystem` anciennes méthodes API `Register` et `Unregister` ont été marquées comme obsolètes. Ils sont conservés à des fins de compatibilité descendante.
- `InputSystemGlobalListener` a été marqué comme obsolète. Ses fonctionnalités n’ont pas changé.
- `BaseInputHandler` la classe de base est passée de `InputSystemGlobalListener` à `InputSystemGlobalHandlerListener` . Il s’agit d’une modification avec rupture pour tous les descendants de `BaseInputHandler` .

**_Motivation derrière la modification_**

L’ancienne API du système `Register` d’événement et `Unregister` peut potentiellement provoquer plusieurs problèmes dans le runtime, main étant :

- Si un composant s’inscrit pour des événements globaux, il recevrait des événements d’entrée globaux de *tous les* types.
- Si l’un des composants d’un objet s’inscrit pour les événements d’entrée globaux, tous les composants de cet objet recevront les événements d’entrée globaux de *tous les* types.
- Si deux composants sur le même objet s’inscrivent à des événements globaux, puis que l’un d’eux est désactivé dans le runtime, le deuxième cesse de recevoir des événements globaux.

Nouvelle API `RegisterHandler` et `UnregisterHandler` :

- Fournit un contrôle explicite et granulaire sur les événements d’entrée qui doivent être écoutés globalement et qui doivent être axés sur le focus.
- Permet à plusieurs composants sur le même objet d’écouter les événements globaux indépendamment l’un de l’autre.

**_Procédure de migration_**

- Si vous avez déjà appelé l' `Register` / `Unregister` API directement, remplacez ces appels par des appels à `RegisterHandler` / `UnregisterHandler` . Utilisez les interfaces de gestionnaire que vous implémentez en tant que paramètres génériques. Si vous implémentez plusieurs interfaces et que plusieurs d’entre elles écoutent les événements d’entrée globaux, appelez `RegisterHandler` plusieurs fois.
- Si vous héritez de `InputSystemGlobalListener` , remplacez héritage par `InputSystemGlobalHandlerListener` . Implémentez `RegisterHandlers` les `UnregisterHandlers` méthodes abstraites et. Dans l’appel `inputSystem.RegisterHandler` d’implémentation ( `inputSystem.UnregisterHandler` ) à inscrire sur toutes les interfaces de gestionnaire pour lesquelles vous souhaitez écouter des événements globaux.
- Si vous héritez de `BaseInputHandler` , implémentez `RegisterHandlers` et des `UnregisterHandlers` méthodes abstraites (comme pour `InputSystemGlobalListener` ).

**_Exemples de migration_**

```c#
// Old
class SampleHandler : MonoBehaviour, IMixedRealitySourceStateHandler, IMixedRealityHandJointHandler
{
    private void OnEnable()
    {
        InputSystem?.Register(gameObject);
    }

    private void OnDisable()
    {
        InputSystem?.Unregister(gameObject);
    }
}

// Migrated
class SampleHandler : MonoBehaviour, IMixedRealitySourceStateHandler, IMixedRealityHandJointHandler
{
    private void OnEnable()
    {
        InputSystem?.RegisterHandler<IMixedRealitySourceStateHandler>(this);
        InputSystem?.RegisterHandler<IMixedRealityHandJointHandler>(this);
    }

    private void OnDisable()
    {
        InputSystem?.UnregisterHandler<IMixedRealitySourceStateHandler>(this);
        InputSystem?.UnregisterHandler<IMixedRealityHandJointHandler>(this);
    }
}
```

```c#
// Old
class SampleHandler2 : InputSystemGlobalListener, IMixedRealitySpeechHandler
{
}

// Migrated
class SampleHandler2 : InputSystemGlobalHandlerListener, IMixedRealitySpeechHandler
{
    private void RegisterHandlers()
    {
        InputSystem?.RegisterHandler<IMixedRealitySpeechHandler>(this);
    }

    private void UnregisterHandlers()
    {
        InputSystem?.UnregisterHandler<IMixedRealitySpeechHandler>(this);
    }
}

// Alternative migration
class SampleHandler2 : MonoBehaviour, IMixedRealitySpeechHandler
{
    private void OnEnable()
    {
        IMixedRealityInputSystem inputSystem;
        if (MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
        {
            inputSystem?.RegisterHandler<IMixedRealitySpeechHandler>(this);
        }
    }

    private void OnDisable()
    {
        IMixedRealityInputSystem inputSystem;
        if (MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
        {
            inputSystem?.UnregisterHandler<IMixedRealitySpeechHandler>(this);
        }
    }
}
```

**Sensibilisation spatiale**

Les interfaces IMixedRealitySpatialAwarenessSystem et IMixedRealitySpatialAwarenessObserver ont pris en considération plusieurs modifications avec rupture, comme décrit ci-dessous.

**_Modifications_**

La ou les méthodes suivantes ont été renommées pour mieux décrire leur utilisation.

- `IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` a été renommé pour `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` clarifier son utilisation.

**_Ajouts_**

En fonction des commentaires des clients, la prise en charge de la suppression aisée des données de sensibilisation spatiale précédemment observées a été ajoutée.

- `IMixedRealitySpatialAwarenessSystem.ClearObservations()`
- `IMixedRealitySpatialAwarenessSystem.ClearObservations<T>(string name)`
- `IMixedRealitySpatialAwarenessObserver.ClearObservations()`

**Solveurs**

Certains composants du solveur et la classe SolverHandler Manager ont été modifiés pour résoudre divers bogues et pour une utilisation plus intuitive.

**_SolverHandler_**

- La classe ne s’étend plus de `ControllerFinder`
- `TrackedObjectToReference` propriété publique dépréciée et renommée en `TrackedTargetType`
- `TrackedObjectType` déprécie les valeurs de contrôleur gauche & droit. Utilisez plutôt `MotionController` `HandJoint` les valeurs ou et mettez à jour la nouvelle `TrackedHandedness` propriété pour limiter le suivi à gauche ou à droite du contrôleur

**_Entre_**

- `TrackedObjectForSecondTransform` propriété publique dépréciée et renommée en `SecondTrackedObjectType`
- `AttachSecondTransformToNewTrackedObject()` a été supprimé. Pour mettre à jour le solveur, modifiez les propriétés publiques (par exemple, `SecondTrackedObjectType`)

**_SurfaceMagnetism_**

- `MaxDistance` propriété publique dépréciée et renommée en `MaxRaycastDistance`
- `CloseDistance` propriété publique dépréciée et renommée en `ClosestDistance`
- La valeur par défaut pour `RaycastDirectionMode` est maintenant le `TrackedTargetForward` raycasts dans la direction de la transformation cible suivie
- `OrientationMode` les valeurs enum, `Vertical` et `Full` , ont été renommées en `TrackedTarget` et `SurfaceNormal` respectivement
- `KeepOrientationVertical` une propriété publique a été ajoutée pour contrôler si l’orientation du GameObject associé reste verticale

**Boutons**

- [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) a maintenant la `DistanceSpaceMode` valeur par défaut pour la propriété `Local` . Cela permet de mettre à l’échelle les boutons tout en les conservant

**Découpage sphère**

L’interface ClippingSphere a été modifiée pour refléter les API trouvées dans ClippingBox et ClippingPlane.

La propriété RADIUS de ClippingSphere est maintenant calculée implicitement en fonction de l’échelle de transformation. Pour que les développeurs doivent spécifier le rayon du ClippingSphere dans l’inspecteur. Si vous souhaitez modifier le rayon, il vous suffit de mettre à jour l’échelle de transformation de la transformation comme vous le feriez normalement.

**NearInteractionTouchable et PokePointer**

- NearInteractionTouchable ne gère pas Unity Canvas qui se touchent plus tard. La classe NearInteractionTouchableUnityUI doit être utilisée pour l’interface utilisateur touchables à l’heure actuelle.
- ColliderNearInteractionTouchable est la nouvelle classe de base pour touchables basée sur les conflits, c’est-à-dire tous les touchable, à l’exception de NearInteractionTouchableUnityUI.
- BaseNearInteractionTouchable. DistFront a été déplacé et renommé en PokePointer. TouchableDistance il s’agit de la distance et de laquelle le PokePointer peut interagir avec touchables. Précédemment, chaque touchable avait sa propre distance d’interaction maximale, mais maintenant elle est définie dans le PokePointer, ce qui permet une meilleure optimisation.
- BaseNearInteractionTouchable. DistBack a été renommé en PokeThreshold, ce qui indique clairement que PokeThreshold est l’équivalent de DebounceThreshold. Un touchable est activé lorsque le PokeThreshold est franchi et libéré lorsque DebounceThreshold est franchi.

**ReadOnlyAttribute**

L' `Microsoft.MixedReality.Toolkit` espace de noms a été ajouté à `ReadOnlyAttribute` , `BeginReadOnlyGroupAttribute` et `EndReadOnlyGroupAttribute` .

**PointerClickHandler**

La classe `PointerClickHandler` a été déconseillée. Le `PointerHandler` doit être utilisé à la place, il fournit les mêmes fonctionnalités.

**prise en charge des clickers HoloLens**

les mappages de contrôleur de l’un des HoloLens de l’utilisateur n’ont pas été déplacés [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) pour être non mis en mains [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand) . Pour tenir compte de cela, un programme de mise à jour automatique s’exécute la première fois que vous ouvrez votre profil ControllerMapping. Ouvrez un profil personnalisé au moins une fois après la mise à niveau vers 2.0.0 afin de déclencher cette étape de migration ponctuelle.

**InteractableHighlight**

La classe `InteractableHighlight` a été déconseillée. La `InteractableOnFocus` classe et l' `FocusInteractableStates` élément multimédia doivent être utilisés à la place. pour créer un `Theme` élément multimédia pour le `InteractableOnFocus` , cliquez avec le bouton droit dans la fenêtre projet et sélectionnez *créer* une  >  *réalité mixte Shared Computer Toolkit*  >    >  *thème* exploitable.

**HandInteractionPanZoom**

`HandInteractionPanZoom` a été déplacé vers l’espace de noms de l’interface utilisateur, car il ne s’agissait pas d’un composant d’entrée. `HandPanEventData` a également été déplacé dans cet espace de noms et simplifié pour correspondre à d’autres données d’événement d’interface utilisateur.

### <a name="assembly-name-changes-in-200"></a>Modifications du nom de l’assembly dans 2.0.0

dans la version 2.0.0, toute la réalité mixte Shared Computer Toolkit les noms d’assembly et les fichiers de définition d’assembly (. asmdef) associés ont été mis à jour pour s’adapter au modèle suivant.

```c#
Microsoft.MixedReality.Toolkit[.<name>]
```

Dans certains cas, plusieurs assemblys ont été fusionnés pour créer une meilleure Unity de leur contenu. Si votre projet utilise des fichiers. asmdef personnalisés, ceux-ci peuvent nécessiter une mise à jour.

Les tableaux suivants décrivent comment les noms de fichiers RC2. asmdef sont mappés à la version 2.0.0. Tous les noms d’assemblys correspondent au nom de fichier. asmdef.

**MixedRealityToolkit**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit.asmdef | Microsoft. MixedReality. Shared Computer Toolkit. asmdef |
| MixedRealityToolkit. Core. BuildAndDeploy. asmdef | Microsoft. MixedReality. Shared Computer Toolkit. Éditeur. BuildAndDeploy. asmdef |
| MixedRealityToolkit. Core. Definitions. Utilities. Editor. asmdef | Supprimé, utilisez Microsoft. MixedReality. Shared Computer Toolkit. Éditeur. Utilities. asmdef |
| MixedRealityToolkit. Core. extensions. EditorClassExtensions. asmdef | Microsoft. MixedReality. Shared Computer Toolkit. Éditeur. ClassExtensions. asmdef
| MixedRealityToolkit. Core. Inspectors. asmdef | Microsoft. MixedReality. Shared Computer Toolkit. Editor. Inspectors. asmdef |
| MixedRealityToolkit. Core. Inspectors. ServiceInspectors. asmdef | Microsoft. MixedReality. Shared Computer Toolkit. Éditeur. ServiceInspectors. asmdef |
| MixedRealityToolkit. Core. UtilitiesAsync. asmdef | Microsoft. MixedReality. Shared Computer Toolkit. Async. asmdef |
| MixedRealityToolkit. Core. Utilities. Editor. asmdef | Microsoft. MixedReality. Shared Computer Toolkit. Éditeur. Utilities. asmdef |
| MixedRealityToolkit. Utilities. Gltf. asmdef | Microsoft. MixedReality. Shared Computer Toolkit. Gltf.asmdef |
| MixedRealityToolkit. Utilities. Gltf. importateurs. asmdef | Microsoft. MixedReality. Shared Computer Toolkit. Gltf. importateurs. asmdef |

**MixedRealityToolkit. Providers**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit. Providers. OpenVR. asmdef | Microsoft. MixedReality. Shared Computer Toolkit. Providers. OpenVR. asmdef |
| MixedRealityToolkit. Providers. WindowsMixedReality. asmdef | Microsoft. MixedReality. Shared Computer Toolkit. Providers. WindowsMixedReality. asmdef |
| MixedRealityToolkit. Providers. WindowsVoiceInput. asmdef | Microsoft. MixedReality. Shared Computer Toolkit. Providers. WindowsVoiceInput. asmdef |

**MixedRealityToolkit. services**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit. services. BoundarySystem. asmdef | Microsoft. MixedReality. Shared Computer Toolkit. Services. BoundarySystem. asmdef |
| MixedRealityToolkit. services. CameraSystem. asmdef | Microsoft. MixedReality. Shared Computer Toolkit. Services. CameraSystem. asmdef |
| MixedRealityToolkit. services. DiagnosticsSystem. asmdef | Microsoft. MixedReality. Shared Computer Toolkit. Services. DiagnosticsSystem. asmdef |
| MixedRealityToolkit. services. InputSimulation. asmdef | Microsoft. MixedReality. Shared Computer Toolkit. Services. InputSimulation. asmdef |
| MixedRealityToolkit. services. InputSimulation. Editor. asmdef | Microsoft. MixedReality. Shared Computer Toolkit. Services. InputSimulation. Editor. asmdef |
| MixedRealityToolkit. services. InputSystem. asmdef | Microsoft. MixedReality. Shared Computer Toolkit. Services. InputSystem. asmdef |
| MixedRealityToolkit. services. Inspectors. asmdef | Microsoft. MixedReality. Shared Computer Toolkit. Services. InputSystem. Editor. asmdef |
| MixedRealityToolkit. services. SceneSystem. asmdef | Microsoft. MixedReality. Shared Computer Toolkit. Services. SceneSystem. asmdef |
| MixedRealityToolkit. services. SpatialAwarenessSystem. asmdef | Microsoft. MixedReality. Shared Computer Toolkit. Services. SpatialAwarenessSystem. asmdef |
| MixedRealityToolkit. services. TeleportSystem. asmdef | Microsoft. MixedReality. Shared Computer Toolkit. Services. TeleportSystem. asmdef |

**MixedRealityToolkit. SDK**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit. SDK. asmdef | Microsoft. MixedReality. Shared Computer Toolkit. SDK. asmdef |
| MixedRealityToolkit. SDK. Inspectors. asmdef | Microsoft. MixedReality. Shared Computer Toolkit. SDK. Inspectors. asmdef |

**MixedRealityToolkit. exemples**

| RC2 | 2.0.0 |
| --- | --- |
| MixedRealityToolkit. examples. asmdef | Microsoft. MixedReality. Shared Computer Toolkit. Exemples. asmdef |
| MixedRealityToolkit. examples. démonstrations. Gltf. asmdef | Microsoft. MixedReality. Shared Computer Toolkit. Démonstrations. Gltf. asmdef |
| MixedRealityToolkit. examples. démonstrations. StandardShader. Inspectors. asmdef | Microsoft. MixedReality. Shared Computer Toolkit. Démonstrations. StandardShader. Inspectors. asmdef |
| MixedRealityToolkit. examples. issues. Utilities. InspectorFields. asmdef | Microsoft. MixedReality. Shared Computer Toolkit. Démonstrations. InspectorFields. asmdef |
| MixedRealityToolkit. examples. issues. Utilities. InspectorFields. Inspectors. asmdef | Microsoft. MixedReality. Shared Computer Toolkit. Démonstrations. InspectorFields. Inspectors. asmdef |
| MixedRealityToolkit. examples. démos. UX. Interactables. asmdef | Microsoft. MixedReality. Shared Computer Toolkit. Démonstrations. UX. Interactables. asmdef |
