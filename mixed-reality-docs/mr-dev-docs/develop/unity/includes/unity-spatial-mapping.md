---
ms.openlocfilehash: 271116683c94e051f61b78c0db3974ee843afdbd
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905715"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)

## <a name="spatial-awareness-system"></a>Système de reconnaissance spatiale

Dans MRTK, consultez le Guide de prise en main de la [sensibilisation spatiale](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) pour plus d’informations sur la configuration de divers observateurs de maillage spatial.

Pour plus d’informations sur les observateurs d’appareils, consultez le guide [de configuration des observateurs de maillage pour les appareils](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/configuring-spatial-awareness-mesh-observer) .

Pour plus d’informations sur les observateurs de scène, consultez le Guide d’observation de la [scène](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/scene-understanding) .

# <a name="xr-sdk"></a>[Kit de développement logiciel (SDK) XR](#tab/xr)

## <a name="armeshmanager"></a>ARMeshManager

Le ARFoundation Unity fournit un composant ARMeshManager pour la visualisation intégrée des maillages spatiaux. Pour plus d’informations sur l’utilisation, consultez la [documentation de Unity](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/mesh-manager.html) .

## <a name="xrmeshsubsystem"></a>XRMeshSubsystem

Si vous préférez travailler directement avec les [XRMeshSubsystem](https://docs.unity3d.com/ScriptReference/XR.XRMeshSubsystem.html) Unity, consultez la [documentation de Unity](https://docs.unity3d.com/Manual/xrsdk-meshing.html) pour plus d’informations sur l’utilisation.

## <a name="windows-xr-plugin"></a>Windows Plug-in XR

Windows Le plug-in XR fournit des méthodes d’extension supplémentaires pour la configuration du XRMeshSubsystem, telles que la définition d’une sphère englobante ou l’accès à la représentation sous-jacente du maillage de la plateforme. Toutes ces autres extensions sont disponibles [dans la documentation d’Unity](https://docs.unity3d.com/Packages/com.unity.xr.windowsmr@5.3/api/UnityEngine.XR.WindowsMR.WindowsMRExtensions.html).

# <a name="legacy-wsa"></a>[WSA hérité](#tab/wsa)

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a>Prise en main des composants de mappage spatial intégrés à Unity

Unity offre deux composants pour ajouter facilement le mappage spatial à votre application, le **convertisseur de mappage spatial** et le **conflit de mappage spatial**.

### <a name="spatial-mapping-renderer"></a>Convertisseur de mappage spatial

Le convertisseur de mappage spatial permet la visualisation du maillage de mappage spatial.

![Convertisseur de mappage spatial dans Unity](../images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a>Conflit de mappage spatial

Le conflit de mappage spatial permet l’interaction entre le contenu holographique (ou le caractère), tel que la physique, avec le maillage de mappage spatial.

![Conflit de mappage spatial dans Unity](../images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a>Utilisation des composants de mappage spatial intégrés

Vous pouvez ajouter les deux composants à votre application si vous souhaitez visualiser et interagir avec les surfaces physiques.

Pour utiliser ces deux composants dans votre application Unity :

1. Sélectionnez un GameObject au centre de la zone dans laquelle vous souhaitez détecter les maillages de surface spatiale.
2. Dans la fenêtre de l’inspecteur, **Ajoutez le composant**  >  **XR**  >  **mappage spatial de conflit**   ou le **convertisseur de mappage spatial**.

Vous trouverez plus d’informations sur l’utilisation de ces composants sur le <a href="https://docs.unity3d.com/2018.4/Documentation/Manual/SpatialMappingComponents.html" target="_blank">site de documentation Unity</a>.

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a>Aller au-delà des composants de mappage spatial intégrés

Ces composants facilitent le glisser-déplacer pour la prise en main du mappage spatial. Lorsque vous souhaitez aller plus loin, il existe deux chemins principaux à explorer :

* Pour effectuer votre propre traitement de maillage de niveau inférieur, consultez la section ci-dessous sur l’API de script de mappage spatial de bas niveau.
* Pour effectuer une analyse de maillage de niveau supérieur, consultez la section ci-dessous sur la bibliothèque SpatialUnderstanding dans [MixedRealityToolkit](https://github.com/microsoft/MixedRealityToolkit/tree/master/SpatialUnderstanding).

## <a name="using-the-low-level-unity-spatial-mapping-api"></a>Utilisation de l’API de mappage spatial de bas niveau

Si vous avez besoin de plus de contrôle que le convertisseur de mappage spatial et les composants de conflit de mappage spatial offrent, utilisez les API de mappage spatial de bas niveau.

**Espace de noms :** *UnityEngine. XR. WSA*<br>
**Types**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*

Nous avons décrit le déroulement suggéré pour une application qui utilise les API de mappage spatial dans les sections ci-dessous.

### <a name="set-up-the-surfaceobservers"></a>Configurer le (s) SurfaceObserver (s)

Instanciez un objet SurfaceObserver pour chaque région d’espace définie par l’application dont vous avez besoin pour les données de mappage spatiale.

```cs
SurfaceObserver surfaceObserver;

private void Start()
{
    surfaceObserver = new SurfaceObserver();
}
```

Spécifiez la région d’espace pour laquelle chaque objet SurfaceObserver fournit des données en appelant SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox ou SetVolumeAsFrustum. Vous pouvez redéfinir la région de l’espace à l’avenir en appelant à nouveau l’une de ces méthodes.

```cs
private void Start()
{
    surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

Quand vous appelez SurfaceObserver. Update (), vous devez fournir un gestionnaire pour chaque surface spatiale de la région du SurfaceObserver d’espace pour lequel le système de mappage spatial a de nouvelles informations. Le gestionnaire reçoit, pour une surface spatiale :

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
{
    // see Handling Surface Changes
}
```

### <a name="handling-surface-changes"></a>Gestion des modifications de surface

Il existe plusieurs cas principaux à gérer : ajouté et mis à jour, qui peuvent utiliser le même chemin d’accès de code et être supprimés.

* Dans les cas ajoutés et mis à jour, nous ajoutons ou obtenons le GameObject représentant ce maillage du dictionnaire. Nous créons un struct SurfaceData avec les composants nécessaires, puis appelons RequestMeshDataAsync pour remplir le GameObject avec les données de maillage, puis le positionner dans la scène.
* Dans le cas supprimé, nous supprimons le GameObject représentant ce maillage du dictionnaire et le détruisons.

```cs
System.Collections.Generic.Dictionary<SurfaceId, GameObject> spatialMeshObjects =
    new System.Collections.Generic.Dictionary<SurfaceId, GameObject>();

private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
{
    switch (changeType)
    {
        case SurfaceChange.Added:
        case SurfaceChange.Updated:
            if (!spatialMeshObjects.ContainsKey(surfaceId))
            {
                spatialMeshObjects[surfaceId] = new GameObject("spatial-mapping-" + surfaceId);
                spatialMeshObjects[surfaceId].transform.parent = this.transform;
                spatialMeshObjects[surfaceId].AddComponent<MeshRenderer>();
            }
            GameObject target = spatialMeshObjects[surfaceId];
            SurfaceData sd = new SurfaceData(
                // the surface id returned from the system
                surfaceId,
                // the mesh filter that is populated with the spatial mapping data for this mesh
                target.GetComponent<MeshFilter>() ?? target.AddComponent<MeshFilter>(),
                // the world anchor used to position the spatial mapping mesh in the world
                target.GetComponent<WorldAnchor>() ?? target.AddComponent<WorldAnchor>(),
                // the mesh collider that is populated with collider data for this mesh, if true is passed to bakeMeshes below
                target.GetComponent<MeshCollider>() ?? target.AddComponent<MeshCollider>(),
                // triangles per cubic meter requested for this mesh
                1000,
                // bakeMeshes - if true, the mesh collider is populated, if false, the mesh collider is empty.
                true
            );

            SurfaceObserver.RequestMeshAsync(sd, OnDataReady);
            break;
        case SurfaceChange.Removed:
            var obj = spatialMeshObjects[surfaceId];
            spatialMeshObjects.Remove(surfaceId);
            if (obj != null)
            {
                GameObject.Destroy(obj);
            }
            break;
        default:
            break;
    }
}
```

### <a name="handling-data-ready"></a>Gestion des données prêtes

Le gestionnaire OnDataReady reçoit un objet SurfaceData. Les objets WorldAnchor, MeshFilter et (éventuellement) MeshCollider qu’il contient reflètent l’état le plus récent de la surface spatiale associée. Si vous le souhaitez, analysez et/ou [traitez](../../../design/spatial-mapping.md#mesh-processing) les données de maillage en accédant au membre de maillage de l’objet MeshFilter. Affichez la surface spatiale avec la dernière maille et (éventuellement) utilisez-la pour les collisions physiques et les raycasts. Il est important de vérifier que le contenu du SurfaceData n’est pas null.

### <a name="start-processing-on-updates"></a>Démarrer le traitement des mises à jour

SurfaceObserver. Update () doit être appelé sur un délai, et non sur tous les frames.

```cs
void Start ()
{
    StartCoroutine(UpdateLoop());
}

IEnumerator UpdateLoop()
{
    var wait = new WaitForSeconds(2.5f);
    while (true)
    {
        surfaceObserver.Update(OnSurfaceChanged);
        yield return wait;
    }
}
```
