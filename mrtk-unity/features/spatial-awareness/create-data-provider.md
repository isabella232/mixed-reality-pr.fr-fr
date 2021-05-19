---
title: Créer une Fournisseur de données de sensibilisation spatiale
description: décrit comment créer des fournisseurs de données personnalisés dans MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 04a0cdbd18f666b6a99c120eb28966234cc8c92d
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145155"
---
# <a name="creating-a-spatial-awareness-system-data-provider"></a><span data-ttu-id="99b51-104">Création d’un fournisseur de données système de sensibilisation spatiale</span><span class="sxs-lookup"><span data-stu-id="99b51-104">Creating a spatial awareness system data provider</span></span>

<span data-ttu-id="99b51-105">Le système de sensibilisation spatiale est un système extensible qui permet de fournir aux applications des données sur les environnements réels.</span><span class="sxs-lookup"><span data-stu-id="99b51-105">The Spatial Awareness system is an extensible system for providing applications with data about real world environments.</span></span> <span data-ttu-id="99b51-106">Pour ajouter la prise en charge d’une nouvelle plateforme matérielle ou d’une nouvelle forme de données de sensibilisation spatiale, un fournisseur de données personnalisé peut être nécessaire.</span><span class="sxs-lookup"><span data-stu-id="99b51-106">To add support for a new hardware platform or a new form of Spatial Awareness data, a custom data provider may be required.</span></span>

<span data-ttu-id="99b51-107">Cet article explique comment créer des [fournisseurs de données personnalisés](../../architecture/systems-extensions-providers.md), également appelés observateurs spatiaux, pour le système de sensibilisation spatiale.</span><span class="sxs-lookup"><span data-stu-id="99b51-107">This article describes how to create [custom data providers](../../architecture/systems-extensions-providers.md), also called Spatial Observers, for the Spatial Awareness system.</span></span> <span data-ttu-id="99b51-108">L’exemple de code présenté ici provient de l' [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) implémentation de classe, qui est [utile pour le chargement des données de maillage 3D dans l’éditeur](spatial-object-mesh-observer.md).</span><span class="sxs-lookup"><span data-stu-id="99b51-108">The example code shown here is from the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class implementation which is [useful for loading 3D mesh data in-editor](spatial-object-mesh-observer.md).</span></span>

> [!NOTE]
> <span data-ttu-id="99b51-109">Le code source complet utilisé dans cet exemple se trouve dans le `Assets/MRTK/Providers/ObjectMeshObserver` dossier.</span><span class="sxs-lookup"><span data-stu-id="99b51-109">The complete source code used in this example can be found in the `Assets/MRTK/Providers/ObjectMeshObserver` folder.</span></span>

## <a name="namespace-and-folder-structure"></a><span data-ttu-id="99b51-110">Structure de l’espace de noms et du dossier</span><span class="sxs-lookup"><span data-stu-id="99b51-110">Namespace and folder structure</span></span>

<span data-ttu-id="99b51-111">Les fournisseurs de données peuvent être distribués de l’une des deux manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="99b51-111">Data providers can be distributed in one of two ways:</span></span>

1. <span data-ttu-id="99b51-112">Composants additionnels tiers</span><span class="sxs-lookup"><span data-stu-id="99b51-112">Third party add-ons</span></span>
1. <span data-ttu-id="99b51-113">Partie intégrante de Microsoft Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="99b51-113">Part of the Microsoft Mixed Reality Toolkit</span></span>

<span data-ttu-id="99b51-114">Le processus d’approbation pour les envois de nouveaux fournisseurs de données à l’MRTK varie au cas par cas et est communiqué au moment de la proposition initiale.</span><span class="sxs-lookup"><span data-stu-id="99b51-114">The approval process for submissions of new data providers to the MRTK will vary on a case-by-case basis and will be communicated at the time of the initial proposal.</span></span> <span data-ttu-id="99b51-115">Les propositions peuvent être soumises en créant un nouveau type de [ *demande de fonctionnalité*](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span><span class="sxs-lookup"><span data-stu-id="99b51-115">Proposals can be submitted by creating a new [*Feature Request* type issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span></span>

### <a name="third-party-add-on"></a><span data-ttu-id="99b51-116">Module complémentaire tiers</span><span class="sxs-lookup"><span data-stu-id="99b51-116">Third party add-on</span></span>

<span data-ttu-id="99b51-117">**Espace de noms**</span><span class="sxs-lookup"><span data-stu-id="99b51-117">**Namespace**</span></span>

<span data-ttu-id="99b51-118">Les fournisseurs de données doivent disposer d’un espace de noms pour atténuer les conflits de noms potentiels.</span><span class="sxs-lookup"><span data-stu-id="99b51-118">Data providers are required to have a namespace to mitigate potential name collisions.</span></span> <span data-ttu-id="99b51-119">Il est recommandé que l’espace de noms inclue les composants suivants.</span><span class="sxs-lookup"><span data-stu-id="99b51-119">It is recommended that the namespace includes the following components.</span></span>

- <span data-ttu-id="99b51-120">Nom de la société qui produit le module complémentaire</span><span class="sxs-lookup"><span data-stu-id="99b51-120">Company name producing the add-on</span></span>
- <span data-ttu-id="99b51-121">Domaine de fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="99b51-121">Feature area</span></span>

<span data-ttu-id="99b51-122">Par exemple, un fournisseur de données de sensibilisation spatiale créé et fourni par la société contoso peut être *« contoso. MixedReality. Toolkit. SpatialAwareness »*.</span><span class="sxs-lookup"><span data-stu-id="99b51-122">For example, a Spatial Awareness data provider created and shipped by the Contoso company may be *"Contoso.MixedReality.Toolkit.SpatialAwareness"*.</span></span>

<span data-ttu-id="99b51-123">**Structure de dossiers**</span><span class="sxs-lookup"><span data-stu-id="99b51-123">**Folder structure**</span></span>

<span data-ttu-id="99b51-124">Il est recommandé que le code source des fournisseurs de données soit disposé dans une hiérarchie de dossiers, comme indiqué dans l’image suivante.</span><span class="sxs-lookup"><span data-stu-id="99b51-124">It is recommended that the source code for data providers be layed out in a folder hierarchy as shown in the following image.</span></span>

![Exemple de structure de dossiers](../images/spatial-awareness/ExampleProviderFolderStructure.png)

<span data-ttu-id="99b51-126">Lorsque le dossier *ContosoSpatialAwareness* contient l’implémentation du fournisseur de données, le dossier *Editor* contient l’inspecteur (et tout autre code spécifique à l’éditeur Unity) et le dossier *profils* contient un ou plusieurs objets scriptables de profil prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="99b51-126">Where the *ContosoSpatialAwareness* folder contains the implementation of the data provider, the *Editor* folder contains the inspector (and any other Unity editor specific code), and the *Profiles* folder contains one or more pre-made profile scriptable objects.</span></span>

### <a name="mrtk-submission"></a><span data-ttu-id="99b51-127">Envoi MRTK</span><span class="sxs-lookup"><span data-stu-id="99b51-127">MRTK submission</span></span>

<span data-ttu-id="99b51-128">**Espace de noms**</span><span class="sxs-lookup"><span data-stu-id="99b51-128">**Namespace**</span></span>

<span data-ttu-id="99b51-129">Si un fournisseur de données système de sensibilisation spatiale est soumis au référentiel de la boîte à outils de la [réalité mixte](https://github.com/Microsoft/MixedRealityToolkit-Unity), l’espace de noms **doit** commencer par Microsoft. MixedReality. Toolkit (ex : *Microsoft. MixedReality. Toolkit. SpatialObjectMeshObserver*)</span><span class="sxs-lookup"><span data-stu-id="99b51-129">If a spatial awareness system data provider is being submitted to the [Mixed Reality Toolkit repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), the namespace **must** begin with Microsoft.MixedReality.Toolkit (ex: *Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver*)</span></span>

 <span data-ttu-id="99b51-130">et le code doit se trouver dans un dossier sous MRTK/Providers (ex : *MRTK/Providers/ObjectMeshObserver*).</span><span class="sxs-lookup"><span data-stu-id="99b51-130">and the code should be located in a folder beneath MRTK/Providers (ex: *MRTK/Providers/ObjectMeshObserver*).</span></span>

<span data-ttu-id="99b51-131">**Structure de dossiers**</span><span class="sxs-lookup"><span data-stu-id="99b51-131">**Folder structure**</span></span>

<span data-ttu-id="99b51-132">Tout le code doit se trouver dans un dossier sous MRTK/Providers (ex : MRTK/Providers/ObjectMeshObserver).</span><span class="sxs-lookup"><span data-stu-id="99b51-132">All code should be located in a folder beneath MRTK/Providers (ex: MRTK/Providers/ObjectMeshObserver).</span></span>

## <a name="define-the-spatial-data-object"></a><span data-ttu-id="99b51-133">Définir l’objet de données spatiales</span><span class="sxs-lookup"><span data-stu-id="99b51-133">Define the spatial data object</span></span>

<span data-ttu-id="99b51-134">La première étape de la création d’un fournisseur de données de sensibilisation spatiale consiste à déterminer le type de données (par exemple, des maillages ou des avions) qu’il fournira aux applications.</span><span class="sxs-lookup"><span data-stu-id="99b51-134">The first step in creating a Spatial Awareness data provider is determining the type of data (ex: meshes or planes) it will provide to applications.</span></span>

<span data-ttu-id="99b51-135">Tous les objets de données spatiales doivent implémenter l' [`IMixedRealitySpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject) interface.</span><span class="sxs-lookup"><span data-stu-id="99b51-135">All spatial data objects must implement the [`IMixedRealitySpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject) interface.</span></span>

<span data-ttu-id="99b51-136">La Fondation de la réalité de la réalité fournit les objets spatiaux suivants qui peuvent être utilisés ou étendus dans de nouveaux fournisseurs de données.</span><span class="sxs-lookup"><span data-stu-id="99b51-136">The Mixed Reality Toolkit foundation provides the following spatial objects that can be used or extended in new data providers.</span></span>

- [`BaseSpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [`SpatialAwarenessMeshObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [`SpatialAwarenessPlanarObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)

## <a name="implement-the-data-provider"></a><span data-ttu-id="99b51-137">Implémenter le fournisseur de données</span><span class="sxs-lookup"><span data-stu-id="99b51-137">Implement the data provider</span></span>

### <a name="specify-interface-andor-base-class-inheritance"></a><span data-ttu-id="99b51-138">Spécifier l’héritage de l’interface et/ou de la classe de base</span><span class="sxs-lookup"><span data-stu-id="99b51-138">Specify interface and/or base class inheritance</span></span>

<span data-ttu-id="99b51-139">Tous les fournisseurs de données de sensibilisation spatiale doivent implémenter l' [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface, qui spécifie les fonctionnalités minimales requises par le système de sensibilisation spatiale.</span><span class="sxs-lookup"><span data-stu-id="99b51-139">All Spatial Awareness data providers must implement the [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface, which specifies the minimum functionality required by the Spatial Awareness system.</span></span> <span data-ttu-id="99b51-140">MRTK Foundation inclut la [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) classe qui fournit une implémentation par défaut de cette fonctionnalité requise.</span><span class="sxs-lookup"><span data-stu-id="99b51-140">The MRTK foundation includes the [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) class which provides a default implementation of this required functionality.</span></span>

```c#
public class SpatialObjectMeshObserver :
    BaseSpatialObserver,
    IMixedRealitySpatialAwarenessMeshObserver,
    IMixedRealityCapabilityCheck
{ }
```

> [!NOTE]
> <span data-ttu-id="99b51-141">L' [`IMixedRealityCapabilityCheck`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck) interface est utilisée par la [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) classe pour indiquer qu’elle prend en charge la fonctionnalité SpatialAwarenessMesh.</span><span class="sxs-lookup"><span data-stu-id="99b51-141">The [`IMixedRealityCapabilityCheck`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck) interface is used by the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class to indicate that it provides support for the SpatialAwarenessMesh capability.</span></span>

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a><span data-ttu-id="99b51-142">Appliquer l’attribut MixedRealityDataProvider</span><span class="sxs-lookup"><span data-stu-id="99b51-142">Apply the MixedRealityDataProvider attribute</span></span>

<span data-ttu-id="99b51-143">Une étape clé de la création d’un fournisseur de données de sensibilisation spatiale consiste à appliquer l' [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attribut à la classe.</span><span class="sxs-lookup"><span data-stu-id="99b51-143">A key step in creating a Spatial Awareness data provider is to apply the [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attribute to the class.</span></span> <span data-ttu-id="99b51-144">Cette étape permet de définir le profil et la ou les plateformes par défaut pour le fournisseur de données, lorsqu’il est sélectionné dans le profil de sensibilisation spatiale, ainsi que le nom, le chemin d’accès au dossier et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="99b51-144">This step enables setting the default profile and platform(s) for the data provider, when selected in the Spatial Awareness profile as well as Name, folder path, and more.</span></span>

```c#
[MixedRealityDataProvider(
    typeof(IMixedRealitySpatialAwarenessSystem),
    SupportedPlatforms.WindowsEditor | SupportedPlatforms.MacEditor | SupportedPlatforms.LinuxEditor,
    "Spatial Object Mesh Observer",
    "ObjectMeshObserver/Profiles/DefaultObjectMeshObserverProfile.asset",
    "MixedRealityToolkit.Providers")]
public class SpatialObjectMeshObserver :
    BaseSpatialObserver,
    IMixedRealitySpatialAwarenessMeshObserver,
    IMixedRealityCapabilityCheck
{ }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a><span data-ttu-id="99b51-145">Implémenter les méthodes IMixedRealityDataProvider</span><span class="sxs-lookup"><span data-stu-id="99b51-145">Implement the IMixedRealityDataProvider methods</span></span>

<span data-ttu-id="99b51-146">Une fois que la classe a été définie, l’étape suivante consiste à fournir l’implémentation de l' [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span><span class="sxs-lookup"><span data-stu-id="99b51-146">Once the class has been defined, the next step is to provide the implementation of the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!NOTE]
> <span data-ttu-id="99b51-147">La [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) classe, via la [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) classe, fournit uniquement des implémentations vides pour les [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) méthodes.</span><span class="sxs-lookup"><span data-stu-id="99b51-147">The [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) class, via the [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) class, provides only an empty implementations for [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) methods.</span></span> <span data-ttu-id="99b51-148">Les détails de ces méthodes sont généralement spécifiques au fournisseur de données.</span><span class="sxs-lookup"><span data-stu-id="99b51-148">The details of these methods are generally data provider specific.</span></span>

<span data-ttu-id="99b51-149">Les méthodes qui doivent être implémentées par le fournisseur de données sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="99b51-149">The methods that should be implemented by the data provider are:</span></span>

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a><span data-ttu-id="99b51-150">Implémenter la logique du fournisseur de données</span><span class="sxs-lookup"><span data-stu-id="99b51-150">Implement the data provider logic</span></span>

<span data-ttu-id="99b51-151">L’étape suivante consiste à ajouter la logique du fournisseur de données en implémentant l’interface du fournisseur de données spécifique, par exemple [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) .</span><span class="sxs-lookup"><span data-stu-id="99b51-151">The next step is to add the logic of the data provider by implementing the specific data provider interface, for example [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver).</span></span> <span data-ttu-id="99b51-152">Cette partie du fournisseur de données est généralement spécifique à la plateforme.</span><span class="sxs-lookup"><span data-stu-id="99b51-152">This portion of the data provider will typically be platform specific.</span></span>

### <a name="observation-change-notifications"></a><span data-ttu-id="99b51-153">Notifications de modification d’observation</span><span class="sxs-lookup"><span data-stu-id="99b51-153">Observation change notifications</span></span>

<span data-ttu-id="99b51-154">Pour permettre aux applications de répondre aux modifications apportées à la compréhension de l’environnement par l’appareil, le fournisseur de données déclenche des événements de notification tels que définis dans l' [`IMixedRealitySpatialAwarenessObservationtHandler<T>`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObservationHandler`1) interface.</span><span class="sxs-lookup"><span data-stu-id="99b51-154">To allow applications to respond to changes in the device's understanding of the environment, the data provider raises notification events as defined in the [`IMixedRealitySpatialAwarenessObservationtHandler<T>`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObservationHandler`1) interface.</span></span>

- `OnObservationAdded()`
- `OnObservationRemoved()`
- `OnObservationUpdated()`

 <span data-ttu-id="99b51-155">Le code suivant des [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) exemples illustre le déclenchement et l’événement lors de l’ajout de données de maillage.</span><span class="sxs-lookup"><span data-stu-id="99b51-155">The following code from the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) examples demonstrates raising and event when mesh data is added.</span></span>

```c#
// The data to be sent when mesh observation events occur.
// This member variable is initialized as part of the Initialize() method.
private MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> meshEventData = null;

/// <summary>
/// Sends the observations using the mesh data contained within the configured 3D model.
/// </summary>
private void SendMeshObjects()
{
    if (!sendObservations) { return; }

    if (spatialMeshObject != null)
    {
        MeshFilter[] meshFilters = spatialMeshObject.GetComponentsInChildren<MeshFilter>();
        for (int i = 0; i < meshFilters.Length; i++)
        {
            SpatialAwarenessMeshObject meshObject = SpatialAwarenessMeshObject.Create(
                meshFilters[i].sharedMesh,
                MeshPhysicsLayer,
                $"Spatial Object Mesh {currentMeshId}",
                currentMeshId,
                ObservedObjectParent);

            meshObject.GameObject.transform.localPosition = meshFilters[i].transform.position;
            meshObject.GameObject.transform.localRotation = meshFilters[i].transform.rotation;

            ApplyMeshMaterial(meshObject);

            meshes.Add(currentMeshId, meshObject);

            // Initialize the meshEventData variable with data for the added event.
            meshEventData.Initialize(this, currentMeshId, meshObject);
            // Raise the event via the spatial awareness system.
            SpatialAwarenessSystem?.HandleEvent(meshEventData, OnMeshAdded);

            currentMeshId++;
        }
    }

    sendObservations = false;
}
```

> [!NOTE]
> <span data-ttu-id="99b51-156">La [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) classe ne déclenche pas d' `OnObservationUpdated` événements, car le modèle 3D n’est chargé qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="99b51-156">The [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class does not raise `OnObservationUpdated` events since the 3D model is only loaded once.</span></span> <span data-ttu-id="99b51-157">L’implémentation dans la [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) classe fournit un exemple de déclenchement d’un `OnObservationUpdated` événement pour un maillage observé.</span><span class="sxs-lookup"><span data-stu-id="99b51-157">The implementation in the [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) class provides an example of raising an `OnObservationUpdated` event for an observed mesh.</span></span>

### <a name="add-unity-profiler-instrumentation"></a><span data-ttu-id="99b51-158">Ajouter l’instrumentation du profileur Unity</span><span class="sxs-lookup"><span data-stu-id="99b51-158">Add Unity Profiler instrumentation</span></span>

<span data-ttu-id="99b51-159">Les performances sont essentielles dans les applications de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="99b51-159">Performance is critical in mixed reality applications.</span></span> <span data-ttu-id="99b51-160">Chaque composant ajoute une quantité de surcharge pour laquelle les applications doivent tenir compte.</span><span class="sxs-lookup"><span data-stu-id="99b51-160">Every component adds some amount of overhead for which applications must account.</span></span> <span data-ttu-id="99b51-161">À cette fin, il est important que tous les fournisseurs de données de sensibilisation spatiale contiennent l’instrumentation du profileur Unity dans la boucle interne et les chemins de code fréquemment utilisés.</span><span class="sxs-lookup"><span data-stu-id="99b51-161">To this end, it is important that all spatial awareness data providers contain Unity Profiler instrumentation in inner loop and frequently utilized code paths.</span></span>

<span data-ttu-id="99b51-162">Il est recommandé d’implémenter le modèle utilisé par MRTK lors de l’instrumentation de fournisseurs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="99b51-162">It is recommended to implement the pattern utilized by the MRTK when instrumenting custom providers.</span></span>

```c#
        private static readonly ProfilerMarker UpdateObserverPerfMarker = new ProfilerMarker("[MRTK] WindowsMixedRealitySpatialMeshObserver.UpdateObserver");

        /// <summary>
        /// Requests updates from the surface observer.
        /// </summary>
        private void UpdateObserver()
        {
            using (UpdateObserverPerfMarker.Auto())
            {
                // Code to be measured.
            }
        }
```

> [!Note]
> <span data-ttu-id="99b51-163">Le nom utilisé pour identifier le marqueur du profileur est arbitraire.</span><span class="sxs-lookup"><span data-stu-id="99b51-163">The name used to identify the profiler marker is arbitrary.</span></span> <span data-ttu-id="99b51-164">MRTK utilise le modèle suivant.</span><span class="sxs-lookup"><span data-stu-id="99b51-164">The MRTK uses the following pattern.</span></span>
>
> <span data-ttu-id="99b51-165">"[Product] className. methodName-Optional note"</span><span class="sxs-lookup"><span data-stu-id="99b51-165">"[product] className.methodName - optional note"</span></span>
>
> <span data-ttu-id="99b51-166">Il est recommandé que les fournisseurs de données personnalisés suivent un modèle similaire pour simplifier l’identification des composants et des méthodes spécifiques lors de l’analyse des traces.</span><span class="sxs-lookup"><span data-stu-id="99b51-166">It is recommended that custom data providers follow a similar pattern to help simplify identification of specific components and methods when analyzing traces.</span></span>

## <a name="create-the-profile-and-inspector"></a><span data-ttu-id="99b51-167">Créer le profil et l’inspecteur</span><span class="sxs-lookup"><span data-stu-id="99b51-167">Create the profile and inspector</span></span>

<span data-ttu-id="99b51-168">Dans la boîte à outils de la réalité mixte, les fournisseurs de données sont configurés à l’aide de [profils](../profiles/profiles.md).</span><span class="sxs-lookup"><span data-stu-id="99b51-168">In the Mixed Reality Toolkit, data providers are configured using [profiles](../profiles/profiles.md).</span></span>

### <a name="define-the-profile"></a><span data-ttu-id="99b51-169">Définir le profil</span><span class="sxs-lookup"><span data-stu-id="99b51-169">Define the profile</span></span>

<span data-ttu-id="99b51-170">Le contenu du profil doit refléter les propriétés accessibles du fournisseur de données (par ex., intervalle de mise à jour).</span><span class="sxs-lookup"><span data-stu-id="99b51-170">Profile contents should mirror the accessible properties of the data provider (ex: update interval).</span></span> <span data-ttu-id="99b51-171">Toutes les propriétés configurables par l’utilisateur définies dans chaque interface doivent être contenues dans le profil.</span><span class="sxs-lookup"><span data-stu-id="99b51-171">All of the user configurable properties defined in each interface should be contained with the profile.</span></span>

<span data-ttu-id="99b51-172">Les classes de base sont encouragées si un nouveau fournisseur de données étend un fournisseur existant.</span><span class="sxs-lookup"><span data-stu-id="99b51-172">Base classes are encouraged if a new data provider extends an existing provider.</span></span> <span data-ttu-id="99b51-173">Par exemple, le [`SpatialObjectMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserverProfile) étend le [`MixedRealitySpatialAwarenessMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessMeshObserverProfile) pour permettre aux clients de fournir un modèle 3D à utiliser comme données d’environnement.</span><span class="sxs-lookup"><span data-stu-id="99b51-173">For example, the [`SpatialObjectMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserverProfile) extends the [`MixedRealitySpatialAwarenessMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessMeshObserverProfile) to enable customers to provide a 3D model to be used as the environment data.</span></span>

```c#
[CreateAssetMenu(
    menuName = "Mixed Reality Toolkit/Profiles/Spatial Object Mesh Observer Profile",
    fileName = "SpatialObjectMeshObserverProfile",
    order = 100)]
public class SpatialObjectMeshObserverProfile : MixedRealitySpatialAwarenessMeshObserverProfile
{
    [SerializeField]
    [Tooltip("The model containing the desired mesh data.")]
    private GameObject spatialMeshObject = null;

    /// <summary>
    /// The model containing the desired mesh data.
    /// </summary>
    public GameObject SpatialMeshObject => spatialMeshObject;
}
```

<span data-ttu-id="99b51-174">L' `CreateAssetMenu` attribut peut être appliqué à la classe de profil pour permettre aux clients de créer une instance de profil à l’aide du menu des profils du kit de ressources de **création** de composants de la  >    >  **réalité mixte**  >   .</span><span class="sxs-lookup"><span data-stu-id="99b51-174">The `CreateAssetMenu` attribute can be applied to the profile class to enable customers to create a profile instance using the **Create** > **Assets** > **Mixed Reality Toolkit** > **Profiles** menu.</span></span>

### <a name="implement-the-inspector"></a><span data-ttu-id="99b51-175">Implémenter l’inspecteur</span><span class="sxs-lookup"><span data-stu-id="99b51-175">Implement the inspector</span></span>

<span data-ttu-id="99b51-176">Les inspecteurs de profil sont l’interface utilisateur permettant de configurer et d’afficher le contenu des profils.</span><span class="sxs-lookup"><span data-stu-id="99b51-176">Profile inspectors are the user interface for configuring and viewing profile contents.</span></span> <span data-ttu-id="99b51-177">Chaque inspecteur de profil doit étendre la [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) classe.</span><span class="sxs-lookup"><span data-stu-id="99b51-177">Each profile inspector should extend the [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) class.</span></span>

<span data-ttu-id="99b51-178">L' `CustomEditor` attribut indique à Unity le type de ressource auquel s’applique l’inspecteur.</span><span class="sxs-lookup"><span data-stu-id="99b51-178">The `CustomEditor` attribute informs Unity the type of asset to which the inspector applies.</span></span>

```c#
[CustomEditor(typeof(SpatialObjectMeshObserverProfile))]
public class SpatialObjectMeshObserverProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

## <a name="create-assembly-definitions"></a><span data-ttu-id="99b51-179">Créer une ou plusieurs définitions d’assembly</span><span class="sxs-lookup"><span data-stu-id="99b51-179">Create assembly definition(s)</span></span>

<span data-ttu-id="99b51-180">La boîte à outils de réalité mixte utilise des fichiers de définition d’assembly ([. asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) pour spécifier les dépendances entre les composants, ainsi que pour aider Unity à réduire le temps de compilation.</span><span class="sxs-lookup"><span data-stu-id="99b51-180">The Mixed Reality Toolkit uses assembly definition ([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) files to specify dependencies between components as well as to assist Unity in reducing compilation time.</span></span>

<span data-ttu-id="99b51-181">Il est recommandé de créer des fichiers de définition d’assembly pour tous les fournisseurs de données et leurs composants d’éditeur.</span><span class="sxs-lookup"><span data-stu-id="99b51-181">It is recommended that assembly definition files are created for all data providers and their editor components.</span></span>

<span data-ttu-id="99b51-182">À l’aide de la [structure de dossiers](#namespace-and-folder-structure) dans l’exemple précédent, il existe deux fichiers. asmdef pour le fournisseur de données ContosoSpatialAwareness.</span><span class="sxs-lookup"><span data-stu-id="99b51-182">Using the [folder structure](#namespace-and-folder-structure) in the earlier example, there would be two .asmdef files for the ContosoSpatialAwareness data provider.</span></span>

<span data-ttu-id="99b51-183">La première définition d’assembly est pour le fournisseur de données.</span><span class="sxs-lookup"><span data-stu-id="99b51-183">The first assembly definition is for the data provider.</span></span> <span data-ttu-id="99b51-184">Pour cet exemple, il est appelé ContosoSpatialAwareness et se trouve dans le dossier *ContosoSpatialAwareness* de l’exemple.</span><span class="sxs-lookup"><span data-stu-id="99b51-184">For this example, it will be called ContosoSpatialAwareness and will be located in the example's *ContosoSpatialAwareness* folder.</span></span> <span data-ttu-id="99b51-185">Cette définition d’assembly doit spécifier une dépendance sur Microsoft. MixedReality. Toolkit et tout autre assembly dont elle dépend.</span><span class="sxs-lookup"><span data-stu-id="99b51-185">This assembly definition must specify a dependency on Microsoft.MixedReality.Toolkit and any other assemblies upon which it depends.</span></span>

<span data-ttu-id="99b51-186">La définition de l’assembly ContosoInputEditor spécifie l’inspecteur de profil et tout code spécifique à l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="99b51-186">The ContosoInputEditor assembly definition will specify the profile inspector and any editor specific code.</span></span> <span data-ttu-id="99b51-187">Ce fichier doit se trouver dans le dossier racine du code de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="99b51-187">This file must be located in the root folder of the editor code.</span></span> <span data-ttu-id="99b51-188">Dans cet exemple, le fichier se trouve dans le dossier *ContosoSpatialAwareness\Editor*</span><span class="sxs-lookup"><span data-stu-id="99b51-188">In this example, the file will be located in the *ContosoSpatialAwareness\Editor* folder.</span></span> <span data-ttu-id="99b51-189">Cette définition d’assembly contient une référence à l’assembly ContosoSpatialAwareness, ainsi que les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="99b51-189">This assembly definition will contain a reference to the ContosoSpatialAwareness assembly as well as:</span></span>

- <span data-ttu-id="99b51-190">Microsoft. MixedReality. Toolkit</span><span class="sxs-lookup"><span data-stu-id="99b51-190">Microsoft.MixedReality.Toolkit</span></span>
- <span data-ttu-id="99b51-191">Microsoft. MixedReality. Toolkit. Editor. Inspectors</span><span class="sxs-lookup"><span data-stu-id="99b51-191">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span></span>
- <span data-ttu-id="99b51-192">Microsoft. MixedReality. Toolkit. Editor. Utilities</span><span class="sxs-lookup"><span data-stu-id="99b51-192">Microsoft.MixedReality.Toolkit.Editor.Utilities</span></span>

## <a name="register-the-data-provider"></a><span data-ttu-id="99b51-193">Inscrire le fournisseur de données</span><span class="sxs-lookup"><span data-stu-id="99b51-193">Register the data provider</span></span>

<span data-ttu-id="99b51-194">Une fois créé, le fournisseur de données peut être inscrit avec le système de sensibilisation spatiale à utiliser dans l’application.</span><span class="sxs-lookup"><span data-stu-id="99b51-194">Once created, the data provider can be registered with the Spatial Awareness system to be used in the application.</span></span>

![Sélection de l’observateur de maillage d’objets spatiaux](../images/spatial-awareness/SelectObjectObserver.png)

## <a name="packaging-and-distribution"></a><span data-ttu-id="99b51-196">Packaging et distribution</span><span class="sxs-lookup"><span data-stu-id="99b51-196">Packaging and distribution</span></span>

<span data-ttu-id="99b51-197">Les fournisseurs de données qui sont distribués en tant que composants tiers ont les détails spécifiques de l’empaquetage et de la distribution laissés à la préférence du développeur.</span><span class="sxs-lookup"><span data-stu-id="99b51-197">Data providers that are distributed as third party components have the specific details of packaging and distribution left to the preference of the developer.</span></span> <span data-ttu-id="99b51-198">Il est probable que la solution la plus courante consiste à générer un. pour Unity et à le distribuer via le magasin d’actifs Unity.</span><span class="sxs-lookup"><span data-stu-id="99b51-198">Likely, the most common solution will be to generate a .unitypackage and distribute via the Unity Asset Store.</span></span>

<span data-ttu-id="99b51-199">Si un fournisseur de données est soumis et accepté dans le cadre du package Microsoft Mixed Reality Toolkit, l’équipe Microsoft MRTK l’empaqueter et la distribuer dans le cadre des offres MRTK.</span><span class="sxs-lookup"><span data-stu-id="99b51-199">If a data provider is submitted and accepted as a part of the Microsoft Mixed Reality Toolkit package, the Microsoft MRTK team will package and distribute it as part of the MRTK offerings.</span></span>

## <a name="see-also"></a><span data-ttu-id="99b51-200">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99b51-200">See also</span></span>

- [<span data-ttu-id="99b51-201">Système de reconnaissance spatiale</span><span class="sxs-lookup"><span data-stu-id="99b51-201">Spatial awareness system</span></span>](spatial-awareness-getting-started.md)
- [<span data-ttu-id="99b51-202">`IMixedRealitySpatialAwarenessObject` interface</span><span class="sxs-lookup"><span data-stu-id="99b51-202">`IMixedRealitySpatialAwarenessObject` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject)
- [<span data-ttu-id="99b51-203">Classe `BaseSpatialAwarenessObject`</span><span class="sxs-lookup"><span data-stu-id="99b51-203">`BaseSpatialAwarenessObject` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [<span data-ttu-id="99b51-204">Classe `SpatialAwarenessMeshObject`</span><span class="sxs-lookup"><span data-stu-id="99b51-204">`SpatialAwarenessMeshObject` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [<span data-ttu-id="99b51-205">Classe `SpatialAwarenessPlanarObject`</span><span class="sxs-lookup"><span data-stu-id="99b51-205">`SpatialAwarenessPlanarObject` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)
- [<span data-ttu-id="99b51-206">`IMixedRealitySpatialAwarenessObserver` interface</span><span class="sxs-lookup"><span data-stu-id="99b51-206">`IMixedRealitySpatialAwarenessObserver` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
- [<span data-ttu-id="99b51-207">Classe `BaseSpatialObserver`</span><span class="sxs-lookup"><span data-stu-id="99b51-207">`BaseSpatialObserver` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
- [<span data-ttu-id="99b51-208">`IMixedRealitySpatialAwarenessMeshObserver` interface</span><span class="sxs-lookup"><span data-stu-id="99b51-208">`IMixedRealitySpatialAwarenessMeshObserver` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
- [<span data-ttu-id="99b51-209">`IMixedRealityDataProvider` interface</span><span class="sxs-lookup"><span data-stu-id="99b51-209">`IMixedRealityDataProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [<span data-ttu-id="99b51-210">`IMixedRealityCapabilityCheck` interface</span><span class="sxs-lookup"><span data-stu-id="99b51-210">`IMixedRealityCapabilityCheck` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
