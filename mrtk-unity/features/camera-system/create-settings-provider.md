---
title: Créer un fournisseur de paramètres
description: fournisseur de données pour les paramètres de l’appareil photo dans MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 6ec3fc1c88c1a32334cb2869ad1994863e55bf9a
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144890"
---
# <a name="creating-a-camera-settings-provider"></a>Création d’un fournisseur de paramètres d’appareil photo

Le système d’appareil photo est un système extensible qui fournit une prise en charge des configurations d’appareil photo spécifiques à la plateforme. Pour ajouter la prise en charge d’une nouvelle configuration d’appareil photo, vous pouvez avoir besoin d’un fournisseur de paramètres personnalisé.

> [!NOTE]
> Le code source complet utilisé dans cet exemple se trouve dans le dossier **MRTK/Providers/Unity** .

## <a name="namespace-and-folder-structure"></a>Structure de l’espace de noms et du dossier

Les fournisseurs de données peuvent être distribués de l’une des deux manières suivantes :

1. Composants additionnels tiers
1. Partie intégrante de Microsoft Mixed Reality Toolkit

Le processus d’approbation pour les envois de nouveaux fournisseurs de données à l’MRTK varie au cas par cas et est communiqué au moment de la proposition initiale. Les propositions peuvent être soumises en créant un nouveau type de [ *demande de fonctionnalité*](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).

### <a name="third-party-add-ons"></a>Composants additionnels tiers

**Espace de noms**

Les fournisseurs de données doivent disposer d’un espace de noms pour atténuer les conflits de noms potentiels. Il est recommandé que l’espace de noms inclue les composants suivants.

- Nom de la société qui produit le module complémentaire
- Domaine de fonctionnalité

Par exemple, un fournisseur de paramètres d’appareil photo créé et fourni par la société contoso peut être *« contoso. MixedReality. Toolkit. Camera »*.

**Structure de dossiers**

Il est recommandé que le code source des fournisseurs de données soit disposé dans une hiérarchie de dossiers, comme indiqué dans l’image suivante.

![Exemple de structure de dossiers](../images/camera-system/ExampleProviderFolderStructure.png)

Lorsque le dossier *ContosoCamera* contient l’implémentation du fournisseur de données, le dossier *Editor* contient l’inspecteur (et tout autre code spécifique à l’éditeur Unity) et le dossier *profils* contient un ou plusieurs objets scriptables de profil prédéfinis.

### <a name="mrtk-submission"></a>Envoi MRTK

**Espace de noms**

Si un fournisseur de paramètres d’appareil photo est soumis au référentiel du kit de tâches de la [réalité mixte](https://github.com/Microsoft/MixedRealityToolkit-Unity), l’espace de noms **doit** commencer par Microsoft. MixedReality. Toolkit (ex : *Microsoft. MixedReality. Toolkit. CameraSystem*).

**Structure de dossiers**

Tout le code doit se trouver dans un dossier sous MRTK/Providers (ex : MRTK/Providers/Unity).

## <a name="define-the-camera-settings-object"></a>Définir l’objet paramètres de l’appareil photo

La première étape de la création d’un fournisseur de paramètres d’appareil photo consiste à déterminer le type de données (par exemple, des maillages ou des avions) qu’il fournira aux applications.

Tous les objets de données spatiales doivent implémenter l' [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) interface.

## <a name="implement-the-settings-provider"></a>Implémenter le fournisseur de paramètres

### <a name="specify-interface-andor-base-class-inheritance"></a>Spécifier l’héritage de l’interface et/ou de la classe de base

Tous les fournisseurs de paramètres d’appareil photo doivent implémenter l' [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) interface, qui spécifie les fonctionnalités minimales requises par le système de caméra. MRTK Foundation inclut la [`BaseCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider) classe qui fournit une implémentation par défaut des fonctionnalités requises.

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    public class UnityARCameraSettings : BaseCameraSettingsProvider
    { }
}
```

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a>Appliquer l’attribut MixedRealityDataProvider

Une étape clé de la création d’un fournisseur de paramètres d’appareil photo consiste à appliquer l' [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attribut à la classe. Cette étape permet de définir le profil et la ou les plateformes par défaut pour le fournisseur de données, lorsqu’il est sélectionné dans le profil du système de l’appareil photo, ainsi que le nom, le chemin d’accès au dossier et bien plus encore.

```c#
    [MixedRealityDataProvider(
        typeof(IMixedRealityCameraSystem),
        SupportedPlatforms.Android | SupportedPlatforms.IOS,
        "Unity AR Foundation Camera Settings",
        "UnityAR/Profiles/DefaultUnityARCameraSettingsProfile.asset",
        "MixedRealityToolkit.Providers")]
    public class UnityARCameraSettings : BaseCameraSettingsProvider
    { }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a>Implémenter les méthodes IMixedRealityDataProvider

Une fois que la classe a été définie, l’étape suivante consiste à fournir l’implémentation de l' [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.

> [!NOTE]
> La [`BaseDataProvider`](xref:Microsoft.MixedReality.Toolkit.BaseDataProvider`1) classe, via la [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) classe, fournit des implémentations vides pour les [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) méthodes. Les détails de ces méthodes sont généralement spécifiques au fournisseur de données.

Les méthodes qui doivent être implémentées par le fournisseur de données sont les suivantes :

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

> [!NOTE]
> Tous les fournisseurs de paramètres ne nécessitent pas d’implémentations pour toutes ces méthodes. Il est vivement recommandé `Destroy()` `Initialize()` d’implémenter au minimum.

### <a name="implement-the-data-provider-logic"></a>Implémenter la logique du fournisseur de données

L’étape suivante consiste à ajouter la logique du fournisseur de paramètres en implémentant [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) . Cette partie du fournisseur de données est généralement spécifique à la configuration de l’appareil photo.

## <a name="create-the-profile-and-inspector"></a>Créer le profil et l’inspecteur

Dans la boîte à outils de la réalité mixte, les fournisseurs de données sont configurés à l’aide de [profils](../profiles/profiles.md).

### <a name="define-the-profile"></a>Définir le profil

Le contenu des profils doit refléter les options de configuration du développeur sélectionnables. Toutes les propriétés configurables par l’utilisateur définies dans chaque interface doivent également être contenues dans le profil.

```c#
using UnityEngine.SpatialTracking;

namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    [CreateAssetMenu(
        menuName = "Mixed Reality Toolkit/Profiles/Unity AR Camera Settings Profile",
        fileName = "UnityARCameraSettingsProfile",
        order = 100)]
    public class UnityARCameraSettingsProfile : BaseCameraSettingsProfile
    {
        [SerializeField]
        [Tooltip("The portion of the device (ex: color camera) from which to read the pose.")]
        private ArTrackedPose poseSource = TrackedPoseDriver.TrackedPose.ColorCamera;

        /// <summary>
        /// The portion of the device (ex: color camera) from which to read the pose.
        /// </summary>
        public ArTrackedPose PoseSource => poseSource;

        [SerializeField]
        [Tooltip("The type of tracking (position and/or rotation) to apply.")]
        private ArTrackingType trackingType = TrackedPoseDriver.TrackingType.RotationAndPosition;

        /// <summary>
        /// The type of tracking (position and/or rotation) to apply.
        /// </summary>
        public ArTrackingType TrackingType => trackingType;

        [SerializeField]
        [Tooltip("Specifies when (during Update and/or just before rendering) to update the tracking of the pose.")]
        private ArUpdateType updateType = TrackedPoseDriver.UpdateType.UpdateAndBeforeRender;

        /// <summary>
        /// Specifies when (during Update and/or just before rendering) to update the tracking of the pose.
        /// </summary>
        public ArUpdateType UpdateType => updateType;
    }
}
```

L' `CreateAssetMenu` attribut peut être appliqué à la classe de profil pour permettre aux clients de créer une instance de profil à l’aide du menu des profils du kit de ressources de **création** de composants de la  >    >  **réalité mixte**  >   .

### <a name="implement-the-inspector"></a>Implémenter l’inspecteur

Les inspecteurs de profil sont l’interface utilisateur permettant de configurer et d’afficher le contenu des profils. Chaque inspecteur de profil doit étendre la [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) classe.

L' `CustomEditor` attribut indique à Unity le type de ressource auquel s’applique l’inspecteur.

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    [CustomEditor(typeof(UnityARCameraSettingsProfile))]
    public class UnityARCameraSettingsProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
    { }
}
```

## <a name="create-assembly-definitions"></a>Créer une ou plusieurs définitions d’assembly

La boîte à outils de réalité mixte utilise des fichiers de définition d’assembly ([. asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) pour spécifier les dépendances entre les composants, ainsi que pour aider Unity à réduire le temps de compilation.

Il est recommandé de créer des fichiers de définition d’assembly pour tous les fournisseurs de données et leurs composants d’éditeur.

À l’aide de la [structure de dossiers](#namespace-and-folder-structure) dans l’exemple précédent, il existe deux fichiers. asmdef pour le fournisseur de données ContosoCamera.

La première définition d’assembly est pour le fournisseur de données. Pour cet exemple, il est appelé ContosoCamera et se trouve dans le dossier *ContosoCamera* de l’exemple. Cette définition d’assembly doit spécifier une dépendance sur Microsoft. MixedReality. Toolkit et tout autre assembly dont elle dépend.

La définition de l’assembly ContosoCameraEditor spécifie l’inspecteur de profil et tout code spécifique à l’éditeur. Ce fichier doit se trouver dans le dossier racine du code de l’éditeur. Dans cet exemple, le fichier se trouve dans le dossier *ContosoCamera\Editor* Cette définition d’assembly contient une référence à l’assembly ContosoCamera, ainsi que les éléments suivants :

- Microsoft. MixedReality. Toolkit
- Microsoft. MixedReality. Toolkit. Editor. Inspectors
- Microsoft. MixedReality. Toolkit. Editor. Utilities

## <a name="register-the-data-provider"></a>Inscrire le fournisseur de données

Une fois créé, le fournisseur de données peut être inscrit auprès du système de caméra pour être utilisé dans l’application.

![Sélection du fournisseur de paramètres de l’appareil photo](../images/camera-system/SelectUnityArSettings.png)

## <a name="packaging-and-distribution"></a>Packaging et distribution

Les fournisseurs de données qui sont distribués en tant que composants tiers ont les détails spécifiques de l’empaquetage et de la distribution laissés à la préférence du développeur. Il est probable que la solution la plus courante consiste à générer un. pour Unity et à le distribuer via le magasin d’actifs Unity.

Si un fournisseur de données est soumis et accepté dans le cadre du package Microsoft Mixed Reality Toolkit, l’équipe Microsoft MRTK l’empaqueter et la distribuer dans le cadre des offres MRTK.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du système de caméras](camera-system-overview.md)
- [Classe `BaseCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider)
- [`IMixedRealityCameraSettingsProvider` interface](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider)
- [`IMixedRealityDataProvider` interface](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
