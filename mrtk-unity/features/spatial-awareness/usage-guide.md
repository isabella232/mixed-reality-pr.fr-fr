---
title: UsingGuide
description: décrit les mécanismes et les API clés pour configurer par programme le système de sensibilisation spatiale
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 3a4b6ce17b87dba6155a9e020e41c800fd8ab86bc1b507e77e680fe9ec9a6687
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204121"
---
# <a name="configuring-mesh-observers-via-code"></a>Configuration des observateurs de maillage par le biais de code

Cet article présente quelques-uns des principaux mécanismes et API permettant de configurer par programme le [système de sensibilisation spatiale](spatial-awareness-getting-started.md) et les fournisseurs de données d' *Observateur de maillage* associés.

## <a name="accessing-mesh-observers"></a>Accès aux observateurs de maillage

Les classes d’observateur de maillage qui implémentent l' [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) interface fournissent des données de maillage spécifiques à la plateforme au système de sensibilisation spatiale. Plusieurs observateurs peuvent être configurés dans le profil de sensibilisation spatiale.

l’accès aux fournisseurs de données du système de sensibilisation spatiale est essentiellement le même que pour toute autre réalité mixte Shared Computer Toolkit service. Le service de sensibilisation spatiale doit être converti vers l' [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) interface pour accéder via les `GetDataProvider<T>` API, qui peut ensuite être utilisé pour accéder directement aux objets de l’observateur de maillage au moment de l’exécution.

```c#
// Use CoreServices to quickly get access to the IMixedRealitySpatialAwarenessSystem
var spatialAwarenessService = CoreServices.SpatialAwarenessSystem;

// Cast to the IMixedRealityDataProviderAccess to get access to the data providers
var dataProviderAccess = spatialAwarenessService as IMixedRealityDataProviderAccess;

var meshObserver = dataProviderAccess.GetDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();
```

L' `CoreServices.GetSpatialAwarenessSystemDataProvider<T>()` application d’assistance simplifie ce modèle d’accès comme illustré ci-dessous.

```c#
// Get the first Mesh Observer available, generally we have only one registered
var meshObserver = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Get the SpatialObjectMeshObserver specifically
var meshObserverName = "Spatial Object Mesh Observer";
var spatialObjectMeshObserver = dataProviderAccess.GetDataProvider<IMixedRealitySpatialAwarenessMeshObserver>(meshObserverName);
```

## <a name="starting-and-stopping-mesh-observation"></a>Démarrage et arrêt de l’observation de maillage

L’une des tâches les plus courantes lors du traitement du système de sensibilisation spatiale consiste à activer la fonctionnalité de manière dynamique au moment de l’exécution. Cette opération est effectuée par observateur via [`IMixedRealitySpatialAwarenessObserver.Resume`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) les [`IMixedRealitySpatialAwarenessObserver.Suspend`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Suspend) API et.

```c#
// Get the first Mesh Observer available, generally we have only one registered
var observer = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Suspends observation of spatial mesh data
observer.Suspend();

// Resumes observation of spatial mesh data
observer.Resume();
```

Cette fonctionnalité de code peut également être simplifiée via l’accès direct au système de sensibilisation spatiale.

```c#
var meshObserverName = "Spatial Object Mesh Observer";
CoreServices.SpatialAwarenessSystem.ResumeObserver<IMixedRealitySpatialAwarenessMeshObserver>(meshObserverName);
```

### <a name="starting-and-stopping-all-mesh-observation"></a>Démarrage et arrêt de toutes les observation de maillage

Il est généralement commode de démarrer/d’arrêter toute observation de maille dans l’application. Pour ce faire, vous pouvez utiliser les API système de sensibilisation spatiale utiles [`ResumeObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.ResumeObservers) et [`SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers) .

```c#
// Resume Mesh Observation from all Observers
CoreServices.SpatialAwarenessSystem.ResumeObservers();

// Suspend Mesh Observation from all Observers
CoreServices.SpatialAwarenessSystem.SuspendObservers();
```

## <a name="enumerating-and-accessing-the-meshes"></a>Énumération et accès aux mailles

L’accès aux maillages peut être effectué par observateur, puis par l’énumération des mailles connues de cet observateur de maillage via l' [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) API.

Si vous exécutez dans l’éditeur, vous pouvez l’utiliser [`AssetDatabase.CreateAsset()`](https://docs.unity3d.com/ScriptReference/AssetDatabase.CreateAsset.html) pour enregistrer l' `Mesh` objet dans un fichier de ressources.

En cas d’exécution sur un appareil, de nombreux plug-ins de la communauté et du magasin sont disponibles pour sérialiser les `MeshFilter` données dans un type de fichier de modèle ([exemple obj](http://wiki.unity3d.com/index.php/ObjExporter)).

```c#
// Get the first Mesh Observer available, generally we have only one registered
var observer = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Loop through all known Meshes
foreach (SpatialAwarenessMeshObject meshObject in observer.Meshes.Values)
{
    Mesh mesh = meshObject.Filter.mesh;
    // Do something with the Mesh object
}
```

## <a name="showing-and-hiding-the-spatial-mesh"></a>Représentation et masquage du maillage spatial

Il est possible de masquer/afficher les maillages par programmation à l’aide de l’exemple de code ci-dessous :

```c#
// Get the first Mesh Observer available, generally we have only one registered
var observer = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Set to not visible
observer.DisplayOption = SpatialAwarenessMeshDisplayOptions.None;

// Set to visible and the Occlusion material
observer.DisplayOption = SpatialAwarenessMeshDisplayOptions.Occlusion;
```

## <a name="registering-for-mesh-observation-events"></a>Inscription pour les événements d’observation de maillage

Les composants peuvent implémenter le `IMixedRealitySpatialAwarenessObservationHandler<SpatialAwarenessMeshObject>` , puis s’inscrire auprès du système de sensibilisation spatiale pour recevoir des événements d’observation de maillage.

Le `DemoSpatialMeshHandler` script (ressources/MRTK/examples/démonstrations/SpatialAwareness/scripts) est un exemple utile et un point de départ pour écouter les événements de l’observateur de maillage.

Il s’agit d’un exemple simplifié de script *DemoSpatialMeshHandler* et d’événement d’observation de maillage à l’écoute.

```c#
// Simplify type
using SpatialAwarenessHandler = IMixedRealitySpatialAwarenessObservationHandler<SpatialAwarenessMeshObject>;

public class MyMeshObservationExample : MonoBehaviour, SpatialAwarenessHandler
{
    private void OnEnable()
    {
        // Register component to listen for Mesh Observation events, typically done in OnEnable()
        CoreServices.SpatialAwarenessSystem.RegisterHandler<SpatialAwarenessHandler>(this);
    }

    private void OnDisable()
    {
        // Unregister component from Mesh Observation events, typically done in OnDisable()
        CoreServices.SpatialAwarenessSystem.UnregisterHandler<SpatialAwarenessHandler>(this);
    }

    public virtual void OnObservationAdded(MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> eventData)
    {
        // Do stuff
    }

    public virtual void OnObservationUpdated(MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> eventData)
    {
        // Do stuff
    }

    public virtual void OnObservationRemoved(MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> eventData)
    {
        // Do stuff
    }
}
```

## <a name="see-also"></a>Voir aussi

- [Prise en main de la sensibilisation spatiale](spatial-awareness-getting-started.md)
- [Configuration de l’observateur de maillage de la sensibilisation spatiale](configuring-spatial-awareness-mesh-observer.md)
- [Documentation sur l’API de sensibilisation spatiale](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)
