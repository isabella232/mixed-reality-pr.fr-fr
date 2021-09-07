---
ms.openlocfilehash: 2ab12da2da926d906a5ae57868f152ecc2b13d90
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2021
ms.locfileid: "123244293"
---
# <a name="world-locking-tools-recommended"></a>[Outils de verrouillage universel (recommandé)](#tab/wlt)

Par défaut, les outils de verrouillage universel restaurent le système de coordonnées de l’unité par rapport au monde physique entre les sessions sur les appareils qui prennent en charge la persistance des ancres spatiales locales. Pour que l’hologramme apparaisse au même endroit dans le monde physique après la sortie et la réexécution de l’application, l’hologramme n’a besoin que de la même pose.

![Composant de contexte de verrouillage universel dans l’inspecteur Unity](../../images/world-locking-tools-img-02.png)

Si l’application a besoin d’un contrôle plus fin, l' **enregistrement automatique** et le **chargement automatique** peuvent être désactivés dans l’inspecteur et la persistance gérée à partir d’un script, comme décrit dans la [section persistance de la documentation](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/Concepts/Advanced/Persistence.html).

la persistance d’ancrage locale est actuellement prise en charge uniquement sur la famille d’appareils HoloLens. toutefois, sur Android et iOS, ainsi que HoloLens, la persistance des espaces de coordonnées entre les sessions, ainsi que le partage des espaces de coordonnées entre les appareils, est prise en charge via une intégration avec les ancres spatiales Azure. Il existe une multitude d' [informations et d’exemples](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/WLT_ASA.html) sur l’utilisation des outils de verrouillage universel en tandem avec les ancres spatiales Azure.

# <a name="aranchormanager"></a>[ARAnchorManager](#tab/anchorstore)

Une API supplémentaire appelée **XRAnchorStore** permet aux ancres d’être rendues persistantes entre les sessions. Le XRAnchorStore est une représentation des ancres enregistrées sur un appareil. Les ancres peuvent être rendues persistantes à partir de **ARAnchors** dans la scène Unity, chargées à partir du stockage dans un nouveau **ARAnchors**, ou supprimées du stockage.

> [!NOTE]
> Ces ancres doivent être enregistrées et chargées sur le même appareil. Le stockage d’ancrage entre appareils sera pris en charge via les ancres spatiales Azure dans une version ultérieure.

### <a name="namespaces"></a>Espaces de noms

Pour **unity 2020 et OpenXR**: 

``` cs
using Microsoft.MixedReality.ARSubsystems.XRAnchorStore
```

ou **unity 2019/2020 + Windows plug-in XR**: 

```cs 
using UnityEngine.XR.WindowsMR.XRAnchorStore
```

### <a name="public-methods"></a>Méthodes publiques

```cs 
{
    // A list of all persisted anchors, which can be loaded.
    public IReadOnlyList<string> PersistedAnchorNames { get; }

    // Clear all persisted anchors
    public void Clear();

    // Load a single persisted anchor by name. The ARAnchorManager will create this new anchor and report it in
    // the ARAnchorManager.anchorsChanged event. The TrackableId returned here is the same TrackableId the
    // ARAnchor will have when it is instantiated.
    public TrackableId LoadAnchor(string name);

    // Attempts to persist an existing ARAnchor with the given TrackableId to the local store. Returns true if
    // the storage is successful, false otherwise.
    public bool TryPersistAnchor(TrackableId id, string name);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

### <a name="getting-an-anchor-store-reference"></a>Obtention d’une référence de magasin d’ancrage 

Pour charger le XRAnchorStore avec **unity 2020 et OpenXR**, utilisez la méthode d’extension sur XRAnchorSubsystem, le sous-système d’un ARAnchorManager :

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

pour charger le XRAnchorStore avec **unity 2019/2020 et le plug-in Windows XR**, utilisez la méthode d’extension sur XRReferencePointSubsystem (unity 2019) ou XRAnchorSubsystem (unity 2020), le sous-système d’un ARReferencePointManager/ARAnchorManager :

```cs
// Unity 2019 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem);

// Unity 2020 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem);
```

### <a name="loading-an-anchor-store"></a>Chargement d’un magasin d’ancrage

Pour charger un magasin d’ancrage dans **unity 2020 et OpenXR**, accédez à celui-ci à partir du sous-système d’un ARAnchorManager, comme suit :

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

ou avec **unity 2019/2020 et le plug-in XR Windows**:

``` cs
// Unity 2019
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();

// Unity 2020
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

Pour voir un exemple complet d’ancres persistantes/non persistantes, consultez l’exemple d’ancres-> ancres GameObject et AnchorsSample. cs dans la [scène exemple de plug-in de réalité mixte OpenXR](../../xr-project-setup.md#unity-sample-projects-for-openxr-and-hololens-2):

![Capture d’écran de l’ouverture du panneau de la hiérarchie dans l’éditeur Unity avec l’exemple ancres mis en surbrillance](../../images/openxr-features-img-04.png)

![Capture d’écran du panneau Inspecteur ouvert dans l’éditeur Unity avec l’exemple de script Anchors mis en surbrillance](../../images/openxr-features-img-05.png)

# <a name="worldanchor"></a>[WorldAnchor](#tab/worldanchor)

Le **WorldAnchorStore** est la clé de la création d’expériences holographiques dans lesquelles les hologrammes restent dans des positions réelles spécifiques entre les instances de l’application. Les utilisateurs peuvent ensuite épingler des hologrammes individuels où ils le souhaitent, et les trouver plus tard dans les mêmes cas sur de nombreuses utilisations de votre application.

**Espace de noms :** *UnityEngine. XR. WSA. persistance*<br>
**Classe :** *WorldAnchorStore*

Le WorldAnchorStore vous permet de conserver l’emplacement des WorldAnchor entre les sessions. Pour conserver les hologrammes entre les sessions, vous devez effectuer un suivi séparé de vos GameObjects qui utilisent une ancre mondiale particulière. Il est souvent judicieux de créer une racine GameObject avec une ancre mondiale et de faire en sorte que les hologrammes enfants soient ancrés avec un décalage de position local.

Pour charger des hologrammes à partir de sessions précédentes :

1. Obtient le WorldAnchorStore
2. Charger les données d’application relatives à l’ancre mondiale, qui vous donne l’ID du point d’ancrage
3. Charger une ancre universelle à partir de son ID

Pour enregistrer des hologrammes pour les sessions à venir :

1. Obtient le WorldAnchorStore
2. Enregistrer une ancre mondiale en spécifiant un ID
3. Enregistrer les données d’application relatives à l’ancre mondiale avec un ID

### <a name="getting-the-worldanchorstore"></a>Obtention du WorldAnchorStore

Il est préférable de conserver une référence à WorldAnchorStore afin de savoir quand il est prêt à effectuer une opération. Étant donné qu’il s’agit d’un appel asynchrone, éventuellement dès le démarrage, vous souhaitez appeler :

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

Dans ce cas, StoreLoaded est notre gestionnaire pour la fin du chargement du WorldAnchorStore :

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

Nous avons maintenant une référence à WorldAnchorStore, que nous allons utiliser pour enregistrer et charger des ancres universelles spécifiques.

### <a name="saving-a-worldanchor"></a>Enregistrement d’un WorldAnchor

Pour ce faire, nous devons simplement nommer ce que nous enregistrons et le transférer dans le WorldAnchor que nous avons reçu avant l’enregistrement. Remarque : la tentative d’enregistrement de deux ancres dans la même chaîne échoue (Store. L’enregistrement retourne la valeur false). Supprimer le précédent enregistrement avant d’en enregistrer un nouveau :

```cs
private void SaveGame()
{
    // Save data about holograms positioned by this world anchor
    if (!this.savedRoot) // Only Save the root once
    {
           this.savedRoot = this.store.Save("rootGameObject", anchor);
           Assert(this.savedRoot);
    }
}
```

### <a name="loading-a-worldanchor"></a>Chargement d’un WorldAnchor

Et pour charger :

```cs
private void LoadGame()
{
    // Save data about holograms positioned by this world anchor
    this.savedRoot = this.store.Load("rootGameObject", rootGameObject);
    if (!this.savedRoot)
    {
        s// We didn't actually have the game root saved! We have to re-place our objects or start over
    }
}
```

Nous pouvons également utiliser le Store. Delete () pour supprimer une ancre précédemment enregistrée et stockée. Clear () pour supprimer toutes les données précédemment enregistrées.

### <a name="enumerating-existing-anchors"></a>Énumération des ancres existantes

Pour découvrir les ancres précédemment stockées, appelez GetAllIds.

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>Persistance des hologrammes pour plusieurs appareils

vous pouvez utiliser des <a href="/azure/spatial-anchors/overview" target="_blank">ancres spatiales Azure</a> pour créer une ancre cloud durable à partir d’un WorldAnchor local, que votre application peut ensuite localiser sur plusieurs HoloLens, iOS et Android, même si ces appareils ne sont pas présents simultanément.  Étant donné que les ancres Cloud sont persistantes, plusieurs périphériques peuvent voir le contenu affiché par rapport à cette ancre dans le même emplacement physique.

Pour commencer à créer des expériences partagées dans Unity, essayez les Démarrages rapides de 5 minutes d' <a href="/azure/spatial-anchors/unity-overview" target="_blank">Unity spatiales Azure Unity</a>.

Une fois que vous êtes opérationnel avec les ancres spatiales Azure, vous pouvez <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">créer et localiser des ancres dans Unity</a>.