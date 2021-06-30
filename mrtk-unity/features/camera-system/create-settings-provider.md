---
title: Créer un fournisseur de paramètres
description: Fournisseur de données pour les paramètres de l’appareil photo dans MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: d07b84c3cf550f9a235e58286b4cd239ac43b649
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121187"
---
# <a name="creating-a-camera-settings-provider"></a><span data-ttu-id="3d1d6-104">Création d’un fournisseur de paramètres d’appareil photo</span><span class="sxs-lookup"><span data-stu-id="3d1d6-104">Creating a camera settings provider</span></span>

<span data-ttu-id="3d1d6-105">Le système d’appareil photo est un système extensible qui fournit une prise en charge des configurations d’appareil photo spécifiques à la plateforme.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-105">The Camera system is an extensible system for providing support for platform specific camera configurations.</span></span> <span data-ttu-id="3d1d6-106">Pour ajouter la prise en charge d’une nouvelle configuration d’appareil photo, vous pouvez avoir besoin d’un fournisseur de paramètres personnalisé.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-106">To add support for a new camera configuration, a custom settings provider may be required.</span></span>

> [!NOTE]
> <span data-ttu-id="3d1d6-107">Le code source complet utilisé dans cet exemple se trouve dans le dossier **MRTK/Providers/Unity** .</span><span class="sxs-lookup"><span data-stu-id="3d1d6-107">The complete source code used in this example can be found in the **MRTK/Providers/UnityAR** folder.</span></span>

## <a name="namespace-and-folder-structure"></a><span data-ttu-id="3d1d6-108">Structure de l’espace de noms et du dossier</span><span class="sxs-lookup"><span data-stu-id="3d1d6-108">Namespace and folder structure</span></span>

<span data-ttu-id="3d1d6-109">Les fournisseurs de données peuvent être distribués de l’une des deux manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="3d1d6-109">Data providers can be distributed in one of two ways:</span></span>

1. <span data-ttu-id="3d1d6-110">Composants additionnels tiers</span><span class="sxs-lookup"><span data-stu-id="3d1d6-110">Third party add-ons</span></span>
1. <span data-ttu-id="3d1d6-111">Partie intégrante de Microsoft Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="3d1d6-111">Part of the Microsoft Mixed Reality Toolkit</span></span>

<span data-ttu-id="3d1d6-112">Le processus d’approbation pour les envois de nouveaux fournisseurs de données à l’MRTK varie au cas par cas et est communiqué au moment de la proposition initiale.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-112">The approval process for submissions of new data providers to the MRTK will vary on a case-by-case basis and will be communicated at the time of the initial proposal.</span></span> <span data-ttu-id="3d1d6-113">Les propositions peuvent être soumises en créant un nouveau type de [ *demande de fonctionnalité*](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span><span class="sxs-lookup"><span data-stu-id="3d1d6-113">Proposals can be submitted by creating a new [*Feature Request* type issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span></span>

### <a name="third-party-add-ons"></a><span data-ttu-id="3d1d6-114">Composants additionnels tiers</span><span class="sxs-lookup"><span data-stu-id="3d1d6-114">Third party add-ons</span></span>

<span data-ttu-id="3d1d6-115">**Espace de noms**</span><span class="sxs-lookup"><span data-stu-id="3d1d6-115">**Namespace**</span></span>

<span data-ttu-id="3d1d6-116">Les fournisseurs de données doivent disposer d’un espace de noms pour atténuer les conflits de noms potentiels.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-116">Data providers are required to have a namespace to mitigate potential name collisions.</span></span> <span data-ttu-id="3d1d6-117">Il est recommandé que l’espace de noms inclue les composants suivants.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-117">It is recommended that the namespace includes the following components.</span></span>

- <span data-ttu-id="3d1d6-118">Nom de la société qui produit le module complémentaire</span><span class="sxs-lookup"><span data-stu-id="3d1d6-118">Company name producing the add-on</span></span>
- <span data-ttu-id="3d1d6-119">Domaine de fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="3d1d6-119">Feature area</span></span>

<span data-ttu-id="3d1d6-120">Par exemple, un fournisseur de paramètres d’appareil photo créé et fourni par la société contoso peut être *« contoso. MixedReality. Toolkit. Camera »*.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-120">For example, a camera settings provider created and shipped by the Contoso company may be *"Contoso.MixedReality.Toolkit.Camera"*.</span></span>

<span data-ttu-id="3d1d6-121">**Structure de dossiers**</span><span class="sxs-lookup"><span data-stu-id="3d1d6-121">**Folder structure**</span></span>

<span data-ttu-id="3d1d6-122">Il est recommandé que le code source des fournisseurs de données soit disposé dans une hiérarchie de dossiers, comme indiqué dans l’image suivante.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-122">It is recommended that the source code for data providers be layed out in a folder hierarchy as shown in the following image.</span></span>

![Exemple de structure de dossiers](../images/camera-system/ExampleProviderFolderStructure.png)

<span data-ttu-id="3d1d6-124">Lorsque le dossier *ContosoCamera* contient l’implémentation du fournisseur de données, le dossier *Editor* contient l’inspecteur (et tout autre code spécifique à l’éditeur Unity) et le dossier *profils* contient un ou plusieurs objets scriptables de profil prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-124">Where the *ContosoCamera* folder contains the implementation of the data provider, the *Editor* folder contains the inspector (and any other Unity editor specific code), and the *Profiles* folder contains one or more pre-made profile scriptable objects.</span></span>

### <a name="mrtk-submission"></a><span data-ttu-id="3d1d6-125">Envoi MRTK</span><span class="sxs-lookup"><span data-stu-id="3d1d6-125">MRTK submission</span></span>

<span data-ttu-id="3d1d6-126">**Espace de noms**</span><span class="sxs-lookup"><span data-stu-id="3d1d6-126">**Namespace**</span></span>

<span data-ttu-id="3d1d6-127">Si un fournisseur de paramètres d’appareil photo est soumis au référentiel du kit de tâches de la [réalité mixte](https://github.com/Microsoft/MixedRealityToolkit-Unity), l’espace de noms **doit** commencer par Microsoft. MixedReality. Toolkit (ex : *Microsoft. MixedReality. Toolkit. CameraSystem*).</span><span class="sxs-lookup"><span data-stu-id="3d1d6-127">If a camera settings provider is being submitted to the [Mixed Reality Toolkit repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), the namespace **must** begin with Microsoft.MixedReality.Toolkit (ex: *Microsoft.MixedReality.Toolkit.CameraSystem*).</span></span>

<span data-ttu-id="3d1d6-128">**Structure de dossiers**</span><span class="sxs-lookup"><span data-stu-id="3d1d6-128">**Folder structure**</span></span>

<span data-ttu-id="3d1d6-129">Tout le code doit se trouver dans un dossier sous MRTK/Providers (ex : MRTK/Providers/Unity).</span><span class="sxs-lookup"><span data-stu-id="3d1d6-129">All code must be located in a folder beneath MRTK/Providers (ex: MRTK/Providers/UnityAR).</span></span>

## <a name="define-the-camera-settings-object"></a><span data-ttu-id="3d1d6-130">Définir l’objet paramètres de l’appareil photo</span><span class="sxs-lookup"><span data-stu-id="3d1d6-130">Define the camera settings object</span></span>

<span data-ttu-id="3d1d6-131">La première étape de la création d’un fournisseur de paramètres d’appareil photo consiste à déterminer le type de données (par exemple, des maillages ou des avions) qu’il fournira aux applications.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-131">The first step in creating a camera settings provider is determining the type of data (ex: meshes or planes) it will provide to applications.</span></span>

<span data-ttu-id="3d1d6-132">Tous les objets de données spatiales doivent implémenter l' [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) interface.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-132">All spatial data objects must implement the [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) interface.</span></span>

## <a name="implement-the-settings-provider"></a><span data-ttu-id="3d1d6-133">Implémenter le fournisseur de paramètres</span><span class="sxs-lookup"><span data-stu-id="3d1d6-133">Implement the settings provider</span></span>

### <a name="specify-interface-andor-base-class-inheritance"></a><span data-ttu-id="3d1d6-134">Spécifier l’héritage de l’interface et/ou de la classe de base</span><span class="sxs-lookup"><span data-stu-id="3d1d6-134">Specify interface and/or base class inheritance</span></span>

<span data-ttu-id="3d1d6-135">Tous les fournisseurs de paramètres d’appareil photo doivent implémenter l' [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) interface, qui spécifie les fonctionnalités minimales requises par le système de caméra.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-135">All camera settings providers must implement the [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) interface, which specifies the minimum functionality required by the camera system.</span></span> <span data-ttu-id="3d1d6-136">MRTK Foundation inclut la [`BaseCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider) classe qui fournit une implémentation par défaut des fonctionnalités requises.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-136">The MRTK foundation includes the [`BaseCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider) class which provides a default implementation of the required functionality.</span></span>

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    public class UnityARCameraSettings : BaseCameraSettingsProvider
    { }
}
```

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a><span data-ttu-id="3d1d6-137">Appliquer l’attribut MixedRealityDataProvider</span><span class="sxs-lookup"><span data-stu-id="3d1d6-137">Apply the MixedRealityDataProvider attribute</span></span>

<span data-ttu-id="3d1d6-138">Une étape clé de la création d’un fournisseur de paramètres d’appareil photo consiste à appliquer l' [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attribut à la classe.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-138">A key step in creating a camera settings provider is to apply the [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attribute to the class.</span></span> <span data-ttu-id="3d1d6-139">Cette étape permet de définir le profil et la ou les plateformes par défaut pour le fournisseur de données, lorsqu’il est sélectionné dans le profil du système de l’appareil photo, ainsi que le nom, le chemin d’accès au dossier et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-139">This step enables setting the default profile and platform(s) for the data provider, when selected in the Camera System profile as well as name, folder path, and more.</span></span>

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

### <a name="implement-the-imixedrealitydataprovider-methods"></a><span data-ttu-id="3d1d6-140">Implémenter les méthodes IMixedRealityDataProvider</span><span class="sxs-lookup"><span data-stu-id="3d1d6-140">Implement the IMixedRealityDataProvider methods</span></span>

<span data-ttu-id="3d1d6-141">Une fois que la classe a été définie, l’étape suivante consiste à fournir l’implémentation de l' [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-141">Once the class has been defined, the next step is to provide the implementation of the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!NOTE]
> <span data-ttu-id="3d1d6-142">La [`BaseDataProvider`](xref:Microsoft.MixedReality.Toolkit.BaseDataProvider`1) classe, via la [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) classe, fournit des implémentations vides pour les [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) méthodes.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-142">The [`BaseDataProvider`](xref:Microsoft.MixedReality.Toolkit.BaseDataProvider`1) class, via the [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) class, provides empty implementations for [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) methods.</span></span> <span data-ttu-id="3d1d6-143">Les détails de ces méthodes sont généralement spécifiques au fournisseur de données.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-143">The details of these methods are generally data provider specific.</span></span>

<span data-ttu-id="3d1d6-144">Les méthodes qui doivent être implémentées par le fournisseur de données sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="3d1d6-144">The methods that should be implemented by the data provider are:</span></span>

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

> [!NOTE]
> <span data-ttu-id="3d1d6-145">Tous les fournisseurs de paramètres ne nécessitent pas d’implémentations pour toutes ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-145">Not all settings providers will require implementations for all of these methods.</span></span> <span data-ttu-id="3d1d6-146">Il est vivement recommandé `Destroy()` `Initialize()` d’implémenter au minimum.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-146">It is highly recommended that `Destroy()` and `Initialize()` be implemented at a minimum.</span></span>

### <a name="implement-the-data-provider-logic"></a><span data-ttu-id="3d1d6-147">Implémenter la logique du fournisseur de données</span><span class="sxs-lookup"><span data-stu-id="3d1d6-147">Implement the data provider logic</span></span>

<span data-ttu-id="3d1d6-148">L’étape suivante consiste à ajouter la logique du fournisseur de paramètres en implémentant [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider) .</span><span class="sxs-lookup"><span data-stu-id="3d1d6-148">The next step is to add the logic of the settings provider by implementing [`IMixedRealityCameraSettingsProvider`](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider).</span></span> <span data-ttu-id="3d1d6-149">Cette partie du fournisseur de données est généralement spécifique à la configuration de l’appareil photo.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-149">This portion of the data provider will typically be camera configuration specific.</span></span>

## <a name="create-the-profile-and-inspector"></a><span data-ttu-id="3d1d6-150">Créer le profil et l’inspecteur</span><span class="sxs-lookup"><span data-stu-id="3d1d6-150">Create the profile and inspector</span></span>

<span data-ttu-id="3d1d6-151">Dans la boîte à outils de la réalité mixte, les fournisseurs de données sont configurés à l’aide de [profils](../profiles/profiles.md).</span><span class="sxs-lookup"><span data-stu-id="3d1d6-151">In the Mixed Reality Toolkit, data providers are configured using [profiles](../profiles/profiles.md).</span></span>

### <a name="define-the-profile"></a><span data-ttu-id="3d1d6-152">Définir le profil</span><span class="sxs-lookup"><span data-stu-id="3d1d6-152">Define the profile</span></span>

<span data-ttu-id="3d1d6-153">Le contenu des profils doit refléter les options de configuration du développeur sélectionnables.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-153">Profile contents should mirror the developer selectable configuration options.</span></span> <span data-ttu-id="3d1d6-154">Toutes les propriétés configurables par l’utilisateur définies dans chaque interface doivent également être contenues dans le profil.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-154">Any user configurable properties defined in each interface should also be contained with the profile.</span></span>

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

<span data-ttu-id="3d1d6-155">L' `CreateAssetMenu` attribut peut être appliqué à la classe de profil pour permettre aux clients de créer une instance de profil à l’aide du menu des profils du kit de ressources de **création** de composants de la  >    >  **réalité mixte**  >   .</span><span class="sxs-lookup"><span data-stu-id="3d1d6-155">The `CreateAssetMenu` attribute can be applied to the profile class to enable customers to create a profile instance using the **Create** > **Assets** > **Mixed Reality Toolkit** > **Profiles** menu.</span></span>

### <a name="implement-the-inspector"></a><span data-ttu-id="3d1d6-156">Implémenter l’inspecteur</span><span class="sxs-lookup"><span data-stu-id="3d1d6-156">Implement the inspector</span></span>

<span data-ttu-id="3d1d6-157">Les inspecteurs de profil sont l’interface utilisateur permettant de configurer et d’afficher le contenu des profils.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-157">Profile inspectors are the user interface for configuring and viewing profile contents.</span></span> <span data-ttu-id="3d1d6-158">Chaque inspecteur de profil doit étendre la [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) classe.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-158">Each profile inspector should extend the [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) class.</span></span>

<span data-ttu-id="3d1d6-159">L' `CustomEditor` attribut indique à Unity le type de ressource auquel s’applique l’inspecteur.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-159">The `CustomEditor` attribute informs Unity the type of asset to which the inspector applies.</span></span>

```c#
namespace namespace Microsoft.MixedReality.Toolkit.Experimental.UnityAR
{
    [CustomEditor(typeof(UnityARCameraSettingsProfile))]
    public class UnityARCameraSettingsProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
    { }
}
```

## <a name="create-assembly-definitions"></a><span data-ttu-id="3d1d6-160">Créer une ou plusieurs définitions d’assembly</span><span class="sxs-lookup"><span data-stu-id="3d1d6-160">Create assembly definition(s)</span></span>

<span data-ttu-id="3d1d6-161">La boîte à outils de réalité mixte utilise des fichiers de définition d’assembly ([. asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) pour spécifier les dépendances entre les composants, ainsi que pour aider Unity à réduire le temps de compilation.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-161">The Mixed Reality Toolkit uses assembly definition ([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) files to specify dependencies between components as well as to assist Unity in reducing compilation time.</span></span>

<span data-ttu-id="3d1d6-162">Il est recommandé de créer des fichiers de définition d’assembly pour tous les fournisseurs de données et leurs composants d’éditeur.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-162">It is recommended that assembly definition files are created for all data providers and their editor components.</span></span>

<span data-ttu-id="3d1d6-163">À l’aide de la [structure de dossiers](#namespace-and-folder-structure) dans l’exemple précédent, il existe deux fichiers. asmdef pour le fournisseur de données ContosoCamera.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-163">Using the [folder structure](#namespace-and-folder-structure) in the earlier example, there would be two .asmdef files for the ContosoCamera data provider.</span></span>

<span data-ttu-id="3d1d6-164">La première définition d’assembly est pour le fournisseur de données.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-164">The first assembly definition is for the data provider.</span></span> <span data-ttu-id="3d1d6-165">Pour cet exemple, il est appelé ContosoCamera et se trouve dans le dossier *ContosoCamera* de l’exemple.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-165">For this example, it will be called ContosoCamera and will be located in the example's *ContosoCamera* folder.</span></span> <span data-ttu-id="3d1d6-166">Cette définition d’assembly doit spécifier une dépendance sur Microsoft. MixedReality. Toolkit et tout autre assembly dont elle dépend.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-166">This assembly definition must specify a dependency on Microsoft.MixedReality.Toolkit and any other assemblies upon which it depends.</span></span>

<span data-ttu-id="3d1d6-167">La définition de l’assembly ContosoCameraEditor spécifie l’inspecteur de profil et tout code spécifique à l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-167">The ContosoCameraEditor assembly definition will specify the profile inspector and any editor specific code.</span></span> <span data-ttu-id="3d1d6-168">Ce fichier doit se trouver dans le dossier racine du code de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-168">This file must be located in the root folder of the editor code.</span></span> <span data-ttu-id="3d1d6-169">Dans cet exemple, le fichier se trouve dans le dossier *ContosoCamera\Editor*</span><span class="sxs-lookup"><span data-stu-id="3d1d6-169">In this example, the file will be located in the *ContosoCamera\Editor* folder.</span></span> <span data-ttu-id="3d1d6-170">Cette définition d’assembly contient une référence à l’assembly ContosoCamera, ainsi que les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="3d1d6-170">This assembly definition will contain a reference to the ContosoCamera assembly as well as:</span></span>

- <span data-ttu-id="3d1d6-171">Microsoft. MixedReality. Toolkit</span><span class="sxs-lookup"><span data-stu-id="3d1d6-171">Microsoft.MixedReality.Toolkit</span></span>
- <span data-ttu-id="3d1d6-172">Microsoft. MixedReality. Toolkit. Editor. Inspectors</span><span class="sxs-lookup"><span data-stu-id="3d1d6-172">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span></span>
- <span data-ttu-id="3d1d6-173">Microsoft. MixedReality. Toolkit. Editor. Utilities</span><span class="sxs-lookup"><span data-stu-id="3d1d6-173">Microsoft.MixedReality.Toolkit.Editor.Utilities</span></span>

## <a name="register-the-data-provider"></a><span data-ttu-id="3d1d6-174">Inscrire le fournisseur de données</span><span class="sxs-lookup"><span data-stu-id="3d1d6-174">Register the data provider</span></span>

<span data-ttu-id="3d1d6-175">Une fois créé, le fournisseur de données peut être inscrit auprès du système de caméra pour être utilisé dans l’application.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-175">Once created, the data provider can be registered with the Camera system to be used in the application.</span></span>

![Sélection du fournisseur de paramètres de l’appareil photo](../images/camera-system/SelectUnityArSettings.png)

## <a name="packaging-and-distribution"></a><span data-ttu-id="3d1d6-177">Packaging et distribution</span><span class="sxs-lookup"><span data-stu-id="3d1d6-177">Packaging and distribution</span></span>

<span data-ttu-id="3d1d6-178">Les fournisseurs de données qui sont distribués en tant que composants tiers ont les détails spécifiques de l’empaquetage et de la distribution laissés à la préférence du développeur.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-178">Data providers that are distributed as third party components have the specific details of packaging and distribution left to the preference of the developer.</span></span> <span data-ttu-id="3d1d6-179">Il est probable que la solution la plus courante consiste à générer un. pour Unity et à le distribuer via le magasin d’actifs Unity.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-179">Likely, the most common solution will be to generate a .unitypackage and distribute via the Unity Asset Store.</span></span>

<span data-ttu-id="3d1d6-180">Si un fournisseur de données est soumis et accepté dans le cadre du package Microsoft Mixed Reality Toolkit, l’équipe Microsoft MRTK l’empaqueter et la distribuer dans le cadre des offres MRTK.</span><span class="sxs-lookup"><span data-stu-id="3d1d6-180">If a data provider is submitted and accepted as a part of the Microsoft Mixed Reality Toolkit package, the Microsoft MRTK team will package and distribute it as part of the MRTK offerings.</span></span>

## <a name="see-also"></a><span data-ttu-id="3d1d6-181">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d1d6-181">See also</span></span>

- [<span data-ttu-id="3d1d6-182">Vue d’ensemble du système de caméras</span><span class="sxs-lookup"><span data-stu-id="3d1d6-182">Camera System Overview</span></span>](camera-system-overview.md)
- [<span data-ttu-id="3d1d6-183">Classe `BaseCameraSettingsProvider`</span><span class="sxs-lookup"><span data-stu-id="3d1d6-183">`BaseCameraSettingsProvider` class</span></span>](xref:Microsoft.MixedReality.Toolkit.CameraSystem.BaseCameraSettingsProvider)
- [<span data-ttu-id="3d1d6-184">`IMixedRealityCameraSettingsProvider` interface</span><span class="sxs-lookup"><span data-stu-id="3d1d6-184">`IMixedRealityCameraSettingsProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.CameraSystem.IMixedRealityCameraSettingsProvider)
- [<span data-ttu-id="3d1d6-185">`IMixedRealityDataProvider` interface</span><span class="sxs-lookup"><span data-stu-id="3d1d6-185">`IMixedRealityDataProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
