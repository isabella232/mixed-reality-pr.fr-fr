---
ms.openlocfilehash: df8dbe19b0a93e2452a8e0b677145bed42b05010
ms.sourcegitcommit: e51e18e443d73a74a9c0b86b3ca5748652cd1b24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103603387"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

> [!NOTE]
> Ces ancres doivent être enregistrées et chargées sur le même appareil. Le stockage d’ancrage entre appareils sera pris en charge via les ancres spatiales Azure dans une version ultérieure.

``` cs
public class Microsoft.MixedReality.ARSubsystems.XRAnchorStore
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
    public bool TryPersistAnchor(string name, TrackableId trackableId);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

Pour charger XRAnchorStore, le plug-in fournit une méthode d’extension sur XRAnchorSubsystem, le sous-système d’un ARAnchorManager :

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

Pour utiliser cette méthode d’extension, accédez à celle-ci à partir du sous-système d’un ARAnchorManager, comme suit :

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

Pour voir un exemple complet d’ancres persistantes/non persistantes, consultez l’exemple d’ancres-> ancrages GameObject et AnchorsSample.cs script dans l' [exemple de scène de plug-in de réalité mixte OpenXR](../openxr-getting-started.md#hololens-2-samples):

![Capture d’écran de l’ouverture du panneau de la hiérarchie dans l’éditeur Unity avec l’exemple ancres mis en surbrillance](../images/openxr-features-img-04.png)

![Capture d’écran du panneau Inspecteur ouvert dans l’éditeur Unity avec l’exemple de script Anchors mis en surbrillance](../images/openxr-features-img-05.png)

# <a name="unity-20192020--windows-xr-plugin"></a>[Plug-in Unity 2019/2020 + Windows XR](#tab/winxr)

> [!NOTE]
> Ces ancres doivent être enregistrées et chargées sur le même appareil. Le stockage d’ancrage entre appareils sera pris en charge via les ancres spatiales Azure dans une version ultérieure.

``` cs
public class UnityEngine.XR.WindowsMR.XRAnchorStore
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

Pour charger le XRAnchorStore, le plug-in fournit une méthode d’extension sur le XRReferencePointSubsystem (Unity 2019) ou XRAnchorSubsystem (Unity 2020), le sous-système d’un ARReferencePointManager/ARAnchorManager :

``` cs
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem); // Unity 2019
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem); // Unity 2020
```

Pour utiliser cette méthode d’extension, accédez à celle-ci à partir du sous-système d’un ARAnchorManager comme suit pour Unity 2019 :

``` cs
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();
```

ou pour Unity 2020 :

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

# <a name="legacy-wsa"></a>[WSA hérité](#tab/wsa)

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

## <a name="building-a-world-scale-experience"></a>Création d’une expérience à l’échelle mondiale

**Espace de noms :** *UnityEngine. XR. WSA*<br>
**Type :** *WorldAnchor*

Pour les expériences réelles à l' **échelle mondiale** sur HoloLens qui permettent aux utilisateurs d’aller au-delà de 5 mètres, vous aurez besoin de nouvelles techniques au-delà de celles utilisées pour les expériences à l’échelle de la place. Une technique clé que vous allez utiliser consiste à créer une [ancre spatiale](../../../design/coordinate-systems.md#spatial-anchors) pour verrouiller un cluster d’hologrammes précisément en place dans le monde physique, quel que soit le degré d’itinérance de l’utilisateur, puis [retrouvez ces hologrammes dans les sessions ultérieures](../../../design/coordinate-systems.md#spatial-anchor-persistence).

Dans Unity, vous créez une ancre spatiale en ajoutant le composant **WorldAnchor** Unity à un GameObject.

### <a name="adding-a-world-anchor"></a>Ajout d’une ancre mondiale

Pour ajouter une ancre universelle, appelez `AddComponent<WorldAnchor>()` sur l’objet de jeu avec la transformation que vous souhaitez ancrer dans le monde réel.

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

Et voilà ! Cet objet de jeu sera désormais ancré à son emplacement actuel dans le monde physique : vous pouvez constater que ses coordonnées universelles s’ajustent légèrement au fil du temps pour garantir l’alignement physique. Reportez-vous à [chargement d’une ancre mondiale](#loading-a-worldanchor) pour rechercher cet emplacement d’ancrage dans une session d’application future.

### <a name="removing-a-world-anchor"></a>Suppression d’une ancre mondiale

Si vous ne souhaitez plus que les GameObject soient verrouillés sur un emplacement géographique physique et que vous n’envisagez pas de déplacer ce cadre, vous pouvez simplement appeler Destroy sur le composant d’ancrage du monde.

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

Si vous souhaitez déplacer le GameObject ce frame, vous devez appeler DestroyImmediate à la place.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>Déplacement d’un GameObject ancré dans le monde

Les GameObject ne peuvent pas être déplacées pendant qu’une ancre mondiale y est. Si vous devez déplacer le GameObject ce frame, vous devez :

1. DestroyImmediate le composant d’ancrage universel
2. Déplacer le GameObject
3. Ajoutez un nouveau composant d’ancrage du monde au GameObject.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>Gestion des modifications de localisabilité

Un WorldAnchor peut ne pas être localisable dans le monde physique à un moment donné. Si cela se produit, Unity ne met pas à jour la transformation de l’objet ancré. Cela peut également changer pendant l’exécution d’une application. Si la modification de la localisation n’est pas prise en charge, l’objet n’apparaîtra pas à l’emplacement physique approprié dans le monde.

Pour être informé des changements de localisation :

1. S’abonner à l’événement OnTrackingChanged
2. Gérer l’événement

L’événement **OnTrackingChanged** est appelé chaque fois que l’ancrage spatial sous-jacent change entre un État localisable et n’est pas localisable.

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

Ensuite, gérez l’événement :

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

Parfois, les ancres se trouvent immédiatement. Dans ce cas, cette propriété isLocated de l’ancre sera définie sur true lorsque AddComponent <WorldAnchor> () retourne. Par conséquent, l’événement OnTrackingChanged n’est pas déclenché. Un modèle propre serait d’appeler votre gestionnaire OnTrackingChanged avec l’état initial de IsLocated après avoir attaché une ancre.

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="persisting-holograms-for-multiple-devices"></a>Persistance des hologrammes pour plusieurs appareils

Vous pouvez utiliser des <a href="/azure/spatial-anchors/overview" target="_blank">ancres spatiales Azure</a> pour créer une ancre Cloud durable à partir d’un WorldAnchor local, que votre application peut ensuite localiser sur plusieurs appareils HoloLens, iOS et Android, même si ces appareils ne sont pas présents simultanément.  Étant donné que les ancres Cloud sont persistantes, plusieurs périphériques peuvent voir le contenu affiché par rapport à cette ancre dans le même emplacement physique.

Pour commencer à créer des expériences partagées dans Unity, essayez les Démarrages rapides de 5 minutes d' <a href="/azure/spatial-anchors/unity-overview" target="_blank">Unity spatiales Azure Unity</a>.

Une fois que vous êtes opérationnel avec les ancres spatiales Azure, vous pouvez <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">créer et localiser des ancres dans Unity</a>.
