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
# <a name="creating-a-spatial-awareness-system-data-provider"></a>Création d’un fournisseur de données système de sensibilisation spatiale

Le système de sensibilisation spatiale est un système extensible qui permet de fournir aux applications des données sur les environnements réels. Pour ajouter la prise en charge d’une nouvelle plateforme matérielle ou d’une nouvelle forme de données de sensibilisation spatiale, un fournisseur de données personnalisé peut être nécessaire.

Cet article explique comment créer des [fournisseurs de données personnalisés](../../architecture/systems-extensions-providers.md), également appelés observateurs spatiaux, pour le système de sensibilisation spatiale. L’exemple de code présenté ici provient de l' [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) implémentation de classe, qui est [utile pour le chargement des données de maillage 3D dans l’éditeur](spatial-object-mesh-observer.md).

> [!NOTE]
> Le code source complet utilisé dans cet exemple se trouve dans le `Assets/MRTK/Providers/ObjectMeshObserver` dossier.

## <a name="namespace-and-folder-structure"></a>Structure de l’espace de noms et du dossier

Les fournisseurs de données peuvent être distribués de l’une des deux manières suivantes :

1. Composants additionnels tiers
1. Partie intégrante de Microsoft Mixed Reality Toolkit

Le processus d’approbation pour les envois de nouveaux fournisseurs de données à l’MRTK varie au cas par cas et est communiqué au moment de la proposition initiale. Les propositions peuvent être soumises en créant un nouveau type de [ *demande de fonctionnalité*](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).

### <a name="third-party-add-on"></a>Module complémentaire tiers

**Espace de noms**

Les fournisseurs de données doivent disposer d’un espace de noms pour atténuer les conflits de noms potentiels. Il est recommandé que l’espace de noms inclue les composants suivants.

- Nom de la société qui produit le module complémentaire
- Domaine de fonctionnalité

Par exemple, un fournisseur de données de sensibilisation spatiale créé et fourni par la société contoso peut être *« contoso. MixedReality. Toolkit. SpatialAwareness »*.

**Structure de dossiers**

Il est recommandé que le code source des fournisseurs de données soit disposé dans une hiérarchie de dossiers, comme indiqué dans l’image suivante.

![Exemple de structure de dossiers](../images/spatial-awareness/ExampleProviderFolderStructure.png)

Lorsque le dossier *ContosoSpatialAwareness* contient l’implémentation du fournisseur de données, le dossier *Editor* contient l’inspecteur (et tout autre code spécifique à l’éditeur Unity) et le dossier *profils* contient un ou plusieurs objets scriptables de profil prédéfinis.

### <a name="mrtk-submission"></a>Envoi MRTK

**Espace de noms**

Si un fournisseur de données système de sensibilisation spatiale est soumis au référentiel de la boîte à outils de la [réalité mixte](https://github.com/Microsoft/MixedRealityToolkit-Unity), l’espace de noms **doit** commencer par Microsoft. MixedReality. Toolkit (ex : *Microsoft. MixedReality. Toolkit. SpatialObjectMeshObserver*)

 et le code doit se trouver dans un dossier sous MRTK/Providers (ex : *MRTK/Providers/ObjectMeshObserver*).

**Structure de dossiers**

Tout le code doit se trouver dans un dossier sous MRTK/Providers (ex : MRTK/Providers/ObjectMeshObserver).

## <a name="define-the-spatial-data-object"></a>Définir l’objet de données spatiales

La première étape de la création d’un fournisseur de données de sensibilisation spatiale consiste à déterminer le type de données (par exemple, des maillages ou des avions) qu’il fournira aux applications.

Tous les objets de données spatiales doivent implémenter l' [`IMixedRealitySpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject) interface.

La Fondation de la réalité de la réalité fournit les objets spatiaux suivants qui peuvent être utilisés ou étendus dans de nouveaux fournisseurs de données.

- [`BaseSpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [`SpatialAwarenessMeshObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [`SpatialAwarenessPlanarObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)

## <a name="implement-the-data-provider"></a>Implémenter le fournisseur de données

### <a name="specify-interface-andor-base-class-inheritance"></a>Spécifier l’héritage de l’interface et/ou de la classe de base

Tous les fournisseurs de données de sensibilisation spatiale doivent implémenter l' [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface, qui spécifie les fonctionnalités minimales requises par le système de sensibilisation spatiale. MRTK Foundation inclut la [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) classe qui fournit une implémentation par défaut de cette fonctionnalité requise.

```c#
public class SpatialObjectMeshObserver :
    BaseSpatialObserver,
    IMixedRealitySpatialAwarenessMeshObserver,
    IMixedRealityCapabilityCheck
{ }
```

> [!NOTE]
> L' [`IMixedRealityCapabilityCheck`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck) interface est utilisée par la [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) classe pour indiquer qu’elle prend en charge la fonctionnalité SpatialAwarenessMesh.

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a>Appliquer l’attribut MixedRealityDataProvider

Une étape clé de la création d’un fournisseur de données de sensibilisation spatiale consiste à appliquer l' [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attribut à la classe. Cette étape permet de définir le profil et la ou les plateformes par défaut pour le fournisseur de données, lorsqu’il est sélectionné dans le profil de sensibilisation spatiale, ainsi que le nom, le chemin d’accès au dossier et bien plus encore.

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

### <a name="implement-the-imixedrealitydataprovider-methods"></a>Implémenter les méthodes IMixedRealityDataProvider

Une fois que la classe a été définie, l’étape suivante consiste à fournir l’implémentation de l' [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.

> [!NOTE]
> La [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) classe, via la [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) classe, fournit uniquement des implémentations vides pour les [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) méthodes. Les détails de ces méthodes sont généralement spécifiques au fournisseur de données.

Les méthodes qui doivent être implémentées par le fournisseur de données sont les suivantes :

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a>Implémenter la logique du fournisseur de données

L’étape suivante consiste à ajouter la logique du fournisseur de données en implémentant l’interface du fournisseur de données spécifique, par exemple [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) . Cette partie du fournisseur de données est généralement spécifique à la plateforme.

### <a name="observation-change-notifications"></a>Notifications de modification d’observation

Pour permettre aux applications de répondre aux modifications apportées à la compréhension de l’environnement par l’appareil, le fournisseur de données déclenche des événements de notification tels que définis dans l' [`IMixedRealitySpatialAwarenessObservationtHandler<T>`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObservationHandler`1) interface.

- `OnObservationAdded()`
- `OnObservationRemoved()`
- `OnObservationUpdated()`

 Le code suivant des [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) exemples illustre le déclenchement et l’événement lors de l’ajout de données de maillage.

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
> La [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) classe ne déclenche pas d' `OnObservationUpdated` événements, car le modèle 3D n’est chargé qu’une seule fois. L’implémentation dans la [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) classe fournit un exemple de déclenchement d’un `OnObservationUpdated` événement pour un maillage observé.

### <a name="add-unity-profiler-instrumentation"></a>Ajouter l’instrumentation du profileur Unity

Les performances sont essentielles dans les applications de réalité mixte. Chaque composant ajoute une quantité de surcharge pour laquelle les applications doivent tenir compte. À cette fin, il est important que tous les fournisseurs de données de sensibilisation spatiale contiennent l’instrumentation du profileur Unity dans la boucle interne et les chemins de code fréquemment utilisés.

Il est recommandé d’implémenter le modèle utilisé par MRTK lors de l’instrumentation de fournisseurs personnalisés.

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
> Le nom utilisé pour identifier le marqueur du profileur est arbitraire. MRTK utilise le modèle suivant.
>
> "[Product] className. methodName-Optional note"
>
> Il est recommandé que les fournisseurs de données personnalisés suivent un modèle similaire pour simplifier l’identification des composants et des méthodes spécifiques lors de l’analyse des traces.

## <a name="create-the-profile-and-inspector"></a>Créer le profil et l’inspecteur

Dans la boîte à outils de la réalité mixte, les fournisseurs de données sont configurés à l’aide de [profils](../profiles/profiles.md).

### <a name="define-the-profile"></a>Définir le profil

Le contenu du profil doit refléter les propriétés accessibles du fournisseur de données (par ex., intervalle de mise à jour). Toutes les propriétés configurables par l’utilisateur définies dans chaque interface doivent être contenues dans le profil.

Les classes de base sont encouragées si un nouveau fournisseur de données étend un fournisseur existant. Par exemple, le [`SpatialObjectMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserverProfile) étend le [`MixedRealitySpatialAwarenessMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessMeshObserverProfile) pour permettre aux clients de fournir un modèle 3D à utiliser comme données d’environnement.

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

L' `CreateAssetMenu` attribut peut être appliqué à la classe de profil pour permettre aux clients de créer une instance de profil à l’aide du menu des profils du kit de ressources de **création** de composants de la  >    >  **réalité mixte**  >   .

### <a name="implement-the-inspector"></a>Implémenter l’inspecteur

Les inspecteurs de profil sont l’interface utilisateur permettant de configurer et d’afficher le contenu des profils. Chaque inspecteur de profil doit étendre la [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) classe.

L' `CustomEditor` attribut indique à Unity le type de ressource auquel s’applique l’inspecteur.

```c#
[CustomEditor(typeof(SpatialObjectMeshObserverProfile))]
public class SpatialObjectMeshObserverProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

## <a name="create-assembly-definitions"></a>Créer une ou plusieurs définitions d’assembly

La boîte à outils de réalité mixte utilise des fichiers de définition d’assembly ([. asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) pour spécifier les dépendances entre les composants, ainsi que pour aider Unity à réduire le temps de compilation.

Il est recommandé de créer des fichiers de définition d’assembly pour tous les fournisseurs de données et leurs composants d’éditeur.

À l’aide de la [structure de dossiers](#namespace-and-folder-structure) dans l’exemple précédent, il existe deux fichiers. asmdef pour le fournisseur de données ContosoSpatialAwareness.

La première définition d’assembly est pour le fournisseur de données. Pour cet exemple, il est appelé ContosoSpatialAwareness et se trouve dans le dossier *ContosoSpatialAwareness* de l’exemple. Cette définition d’assembly doit spécifier une dépendance sur Microsoft. MixedReality. Toolkit et tout autre assembly dont elle dépend.

La définition de l’assembly ContosoInputEditor spécifie l’inspecteur de profil et tout code spécifique à l’éditeur. Ce fichier doit se trouver dans le dossier racine du code de l’éditeur. Dans cet exemple, le fichier se trouve dans le dossier *ContosoSpatialAwareness\Editor* Cette définition d’assembly contient une référence à l’assembly ContosoSpatialAwareness, ainsi que les éléments suivants :

- Microsoft. MixedReality. Toolkit
- Microsoft. MixedReality. Toolkit. Editor. Inspectors
- Microsoft. MixedReality. Toolkit. Editor. Utilities

## <a name="register-the-data-provider"></a>Inscrire le fournisseur de données

Une fois créé, le fournisseur de données peut être inscrit avec le système de sensibilisation spatiale à utiliser dans l’application.

![Sélection de l’observateur de maillage d’objets spatiaux](../images/spatial-awareness/SelectObjectObserver.png)

## <a name="packaging-and-distribution"></a>Packaging et distribution

Les fournisseurs de données qui sont distribués en tant que composants tiers ont les détails spécifiques de l’empaquetage et de la distribution laissés à la préférence du développeur. Il est probable que la solution la plus courante consiste à générer un. pour Unity et à le distribuer via le magasin d’actifs Unity.

Si un fournisseur de données est soumis et accepté dans le cadre du package Microsoft Mixed Reality Toolkit, l’équipe Microsoft MRTK l’empaqueter et la distribuer dans le cadre des offres MRTK.

## <a name="see-also"></a>Voir aussi

- [Système de reconnaissance spatiale](spatial-awareness-getting-started.md)
- [`IMixedRealitySpatialAwarenessObject` interface](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject)
- [Classe `BaseSpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [Classe `SpatialAwarenessMeshObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [Classe `SpatialAwarenessPlanarObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)
- [`IMixedRealitySpatialAwarenessObserver` interface](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
- [Classe `BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
- [`IMixedRealitySpatialAwarenessMeshObserver` interface](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
- [`IMixedRealityDataProvider` interface](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [`IMixedRealityCapabilityCheck` interface](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
