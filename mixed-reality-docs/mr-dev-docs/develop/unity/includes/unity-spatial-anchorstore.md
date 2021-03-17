---
ms.openlocfilehash: df8dbe19b0a93e2452a8e0b677145bed42b05010
ms.sourcegitcommit: e51e18e443d73a74a9c0b86b3ca5748652cd1b24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2021
ms.locfileid: "103603387"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="9a241-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="9a241-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

> [!NOTE]
> <span data-ttu-id="9a241-102">Ces ancres doivent être enregistrées et chargées sur le même appareil.</span><span class="sxs-lookup"><span data-stu-id="9a241-102">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="9a241-103">Le stockage d’ancrage entre appareils sera pris en charge via les ancres spatiales Azure dans une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="9a241-103">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

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

<span data-ttu-id="9a241-104">Pour charger XRAnchorStore, le plug-in fournit une méthode d’extension sur XRAnchorSubsystem, le sous-système d’un ARAnchorManager :</span><span class="sxs-lookup"><span data-stu-id="9a241-104">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="9a241-105">Pour utiliser cette méthode d’extension, accédez à celle-ci à partir du sous-système d’un ARAnchorManager, comme suit :</span><span class="sxs-lookup"><span data-stu-id="9a241-105">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="9a241-106">Pour voir un exemple complet d’ancres persistantes/non persistantes, consultez l’exemple d’ancres-> ancrages GameObject et AnchorsSample.cs script dans l' [exemple de scène de plug-in de réalité mixte OpenXR](../openxr-getting-started.md#hololens-2-samples):</span><span class="sxs-lookup"><span data-stu-id="9a241-106">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](../openxr-getting-started.md#hololens-2-samples):</span></span>

![Capture d’écran de l’ouverture du panneau de la hiérarchie dans l’éditeur Unity avec l’exemple ancres mis en surbrillance](../images/openxr-features-img-04.png)

![Capture d’écran du panneau Inspecteur ouvert dans l’éditeur Unity avec l’exemple de script Anchors mis en surbrillance](../images/openxr-features-img-05.png)

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="9a241-109">Plug-in Unity 2019/2020 + Windows XR</span><span class="sxs-lookup"><span data-stu-id="9a241-109">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

> [!NOTE]
> <span data-ttu-id="9a241-110">Ces ancres doivent être enregistrées et chargées sur le même appareil.</span><span class="sxs-lookup"><span data-stu-id="9a241-110">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="9a241-111">Le stockage d’ancrage entre appareils sera pris en charge via les ancres spatiales Azure dans une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="9a241-111">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

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

<span data-ttu-id="9a241-112">Pour charger le XRAnchorStore, le plug-in fournit une méthode d’extension sur le XRReferencePointSubsystem (Unity 2019) ou XRAnchorSubsystem (Unity 2020), le sous-système d’un ARReferencePointManager/ARAnchorManager :</span><span class="sxs-lookup"><span data-stu-id="9a241-112">To load the XRAnchorStore, the plugin provides an extension method on the XRReferencePointSubsystem (Unity 2019) or XRAnchorSubsystem (Unity 2020), the subsystem of an ARReferencePointManager/ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem); // Unity 2019
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem); // Unity 2020
```

<span data-ttu-id="9a241-113">Pour utiliser cette méthode d’extension, accédez à celle-ci à partir du sous-système d’un ARAnchorManager comme suit pour Unity 2019 :</span><span class="sxs-lookup"><span data-stu-id="9a241-113">To use this extension method, access it from an ARAnchorManager's subsystem as follows for Unity 2019:</span></span>

``` cs
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();
```

<span data-ttu-id="9a241-114">ou pour Unity 2020 :</span><span class="sxs-lookup"><span data-stu-id="9a241-114">or for Unity 2020:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

# <a name="legacy-wsa"></a>[<span data-ttu-id="9a241-115">WSA hérité</span><span class="sxs-lookup"><span data-stu-id="9a241-115">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="9a241-116">**Espace de noms :** *UnityEngine. XR. WSA. persistance*</span><span class="sxs-lookup"><span data-stu-id="9a241-116">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="9a241-117">**Classe :** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="9a241-117">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="9a241-118">Le WorldAnchorStore vous permet de conserver l’emplacement des WorldAnchor entre les sessions.</span><span class="sxs-lookup"><span data-stu-id="9a241-118">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="9a241-119">Pour conserver les hologrammes entre les sessions, vous devez effectuer un suivi séparé de vos GameObjects qui utilisent une ancre mondiale particulière.</span><span class="sxs-lookup"><span data-stu-id="9a241-119">To actually persist holograms across sessions, you'll need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="9a241-120">Il est souvent judicieux de créer une racine GameObject avec une ancre mondiale et de faire en sorte que les hologrammes enfants soient ancrés avec un décalage de position local.</span><span class="sxs-lookup"><span data-stu-id="9a241-120">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="9a241-121">Pour charger des hologrammes à partir de sessions précédentes :</span><span class="sxs-lookup"><span data-stu-id="9a241-121">To load holograms from previous sessions:</span></span>

1. <span data-ttu-id="9a241-122">Obtient le WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="9a241-122">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="9a241-123">Charger les données d’application relatives à l’ancre mondiale, qui vous donne l’ID du point d’ancrage</span><span class="sxs-lookup"><span data-stu-id="9a241-123">Load app data relating to the world anchor, which gives you the ID of the world anchor</span></span>
3. <span data-ttu-id="9a241-124">Charger une ancre universelle à partir de son ID</span><span class="sxs-lookup"><span data-stu-id="9a241-124">Load a world anchor from its ID</span></span>

<span data-ttu-id="9a241-125">Pour enregistrer des hologrammes pour les sessions à venir :</span><span class="sxs-lookup"><span data-stu-id="9a241-125">To save holograms for future sessions:</span></span>

1. <span data-ttu-id="9a241-126">Obtient le WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="9a241-126">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="9a241-127">Enregistrer une ancre mondiale en spécifiant un ID</span><span class="sxs-lookup"><span data-stu-id="9a241-127">Save a world anchor specifying an ID</span></span>
3. <span data-ttu-id="9a241-128">Enregistrer les données d’application relatives à l’ancre mondiale avec un ID</span><span class="sxs-lookup"><span data-stu-id="9a241-128">Save app data relating to the world anchor along with an ID</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="9a241-129">Obtention du WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="9a241-129">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="9a241-130">Il est préférable de conserver une référence à WorldAnchorStore afin de savoir quand il est prêt à effectuer une opération.</span><span class="sxs-lookup"><span data-stu-id="9a241-130">You'll want to keep a reference to the WorldAnchorStore so you know when it's ready to perform an operation.</span></span> <span data-ttu-id="9a241-131">Étant donné qu’il s’agit d’un appel asynchrone, éventuellement dès le démarrage, vous souhaitez appeler :</span><span class="sxs-lookup"><span data-stu-id="9a241-131">Since this is an async call, potentially as soon as start up, you want to call:</span></span>

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="9a241-132">Dans ce cas, StoreLoaded est notre gestionnaire pour la fin du chargement du WorldAnchorStore :</span><span class="sxs-lookup"><span data-stu-id="9a241-132">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

<span data-ttu-id="9a241-133">Nous avons maintenant une référence à WorldAnchorStore, que nous allons utiliser pour enregistrer et charger des ancres universelles spécifiques.</span><span class="sxs-lookup"><span data-stu-id="9a241-133">We now have a reference to the WorldAnchorStore, which we'll use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="9a241-134">Enregistrement d’un WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="9a241-134">Saving a WorldAnchor</span></span>

<span data-ttu-id="9a241-135">Pour ce faire, nous devons simplement nommer ce que nous enregistrons et le transférer dans le WorldAnchor que nous avons reçu avant l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="9a241-135">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="9a241-136">Remarque : la tentative d’enregistrement de deux ancres dans la même chaîne échoue (Store. L’enregistrement retourne la valeur false).</span><span class="sxs-lookup"><span data-stu-id="9a241-136">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="9a241-137">Supprimer le précédent enregistrement avant d’en enregistrer un nouveau :</span><span class="sxs-lookup"><span data-stu-id="9a241-137">Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="9a241-138">Chargement d’un WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="9a241-138">Loading a WorldAnchor</span></span>

<span data-ttu-id="9a241-139">Et pour charger :</span><span class="sxs-lookup"><span data-stu-id="9a241-139">And to load:</span></span>

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

<span data-ttu-id="9a241-140">Nous pouvons également utiliser le Store. Delete () pour supprimer une ancre précédemment enregistrée et stockée. Clear () pour supprimer toutes les données précédemment enregistrées.</span><span class="sxs-lookup"><span data-stu-id="9a241-140">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="9a241-141">Énumération des ancres existantes</span><span class="sxs-lookup"><span data-stu-id="9a241-141">Enumerating Existing Anchors</span></span>

<span data-ttu-id="9a241-142">Pour découvrir les ancres précédemment stockées, appelez GetAllIds.</span><span class="sxs-lookup"><span data-stu-id="9a241-142">To discover previously stored anchors, call GetAllIds.</span></span>

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="9a241-143">Création d’une expérience à l’échelle mondiale</span><span class="sxs-lookup"><span data-stu-id="9a241-143">Building a world-scale experience</span></span>

<span data-ttu-id="9a241-144">**Espace de noms :** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="9a241-144">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="9a241-145">**Type :** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="9a241-145">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="9a241-146">Pour les expériences réelles à l' **échelle mondiale** sur HoloLens qui permettent aux utilisateurs d’aller au-delà de 5 mètres, vous aurez besoin de nouvelles techniques au-delà de celles utilisées pour les expériences à l’échelle de la place.</span><span class="sxs-lookup"><span data-stu-id="9a241-146">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="9a241-147">Une technique clé que vous allez utiliser consiste à créer une [ancre spatiale](../../../design/coordinate-systems.md#spatial-anchors) pour verrouiller un cluster d’hologrammes précisément en place dans le monde physique, quel que soit le degré d’itinérance de l’utilisateur, puis [retrouvez ces hologrammes dans les sessions ultérieures](../../../design/coordinate-systems.md#spatial-anchor-persistence).</span><span class="sxs-lookup"><span data-stu-id="9a241-147">One key technique you'll use is to create a [spatial anchor](../../../design/coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, no matter how far the user has roamed, and then [find those holograms again in later sessions](../../../design/coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="9a241-148">Dans Unity, vous créez une ancre spatiale en ajoutant le composant **WorldAnchor** Unity à un GameObject.</span><span class="sxs-lookup"><span data-stu-id="9a241-148">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="9a241-149">Ajout d’une ancre mondiale</span><span class="sxs-lookup"><span data-stu-id="9a241-149">Adding a World Anchor</span></span>

<span data-ttu-id="9a241-150">Pour ajouter une ancre universelle, appelez `AddComponent<WorldAnchor>()` sur l’objet de jeu avec la transformation que vous souhaitez ancrer dans le monde réel.</span><span class="sxs-lookup"><span data-stu-id="9a241-150">To add a world anchor, call `AddComponent<WorldAnchor>()` on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="9a241-151">Et voilà !</span><span class="sxs-lookup"><span data-stu-id="9a241-151">That's it!</span></span> <span data-ttu-id="9a241-152">Cet objet de jeu sera désormais ancré à son emplacement actuel dans le monde physique : vous pouvez constater que ses coordonnées universelles s’ajustent légèrement au fil du temps pour garantir l’alignement physique.</span><span class="sxs-lookup"><span data-stu-id="9a241-152">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="9a241-153">Reportez-vous à [chargement d’une ancre mondiale](#loading-a-worldanchor) pour rechercher cet emplacement d’ancrage dans une session d’application future.</span><span class="sxs-lookup"><span data-stu-id="9a241-153">Refer to [loading a world anchor](#loading-a-worldanchor) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="9a241-154">Suppression d’une ancre mondiale</span><span class="sxs-lookup"><span data-stu-id="9a241-154">Removing a World Anchor</span></span>

<span data-ttu-id="9a241-155">Si vous ne souhaitez plus que les GameObject soient verrouillés sur un emplacement géographique physique et que vous n’envisagez pas de déplacer ce cadre, vous pouvez simplement appeler Destroy sur le composant d’ancrage du monde.</span><span class="sxs-lookup"><span data-stu-id="9a241-155">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="9a241-156">Si vous souhaitez déplacer le GameObject ce frame, vous devez appeler DestroyImmediate à la place.</span><span class="sxs-lookup"><span data-stu-id="9a241-156">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="9a241-157">Déplacement d’un GameObject ancré dans le monde</span><span class="sxs-lookup"><span data-stu-id="9a241-157">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="9a241-158">Les GameObject ne peuvent pas être déplacées pendant qu’une ancre mondiale y est.</span><span class="sxs-lookup"><span data-stu-id="9a241-158">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="9a241-159">Si vous devez déplacer le GameObject ce frame, vous devez :</span><span class="sxs-lookup"><span data-stu-id="9a241-159">If you need to move the GameObject this frame, you need to:</span></span>

1. <span data-ttu-id="9a241-160">DestroyImmediate le composant d’ancrage universel</span><span class="sxs-lookup"><span data-stu-id="9a241-160">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="9a241-161">Déplacer le GameObject</span><span class="sxs-lookup"><span data-stu-id="9a241-161">Move the GameObject</span></span>
3. <span data-ttu-id="9a241-162">Ajoutez un nouveau composant d’ancrage du monde au GameObject.</span><span class="sxs-lookup"><span data-stu-id="9a241-162">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="9a241-163">Gestion des modifications de localisabilité</span><span class="sxs-lookup"><span data-stu-id="9a241-163">Handling Locatability Changes</span></span>

<span data-ttu-id="9a241-164">Un WorldAnchor peut ne pas être localisable dans le monde physique à un moment donné.</span><span class="sxs-lookup"><span data-stu-id="9a241-164">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="9a241-165">Si cela se produit, Unity ne met pas à jour la transformation de l’objet ancré.</span><span class="sxs-lookup"><span data-stu-id="9a241-165">If that occurs, Unity won't be updating the transform of the anchored object.</span></span> <span data-ttu-id="9a241-166">Cela peut également changer pendant l’exécution d’une application.</span><span class="sxs-lookup"><span data-stu-id="9a241-166">This also can change while an app is running.</span></span> <span data-ttu-id="9a241-167">Si la modification de la localisation n’est pas prise en charge, l’objet n’apparaîtra pas à l’emplacement physique approprié dans le monde.</span><span class="sxs-lookup"><span data-stu-id="9a241-167">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="9a241-168">Pour être informé des changements de localisation :</span><span class="sxs-lookup"><span data-stu-id="9a241-168">To be notified about locatability changes:</span></span>

1. <span data-ttu-id="9a241-169">S’abonner à l’événement OnTrackingChanged</span><span class="sxs-lookup"><span data-stu-id="9a241-169">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="9a241-170">Gérer l’événement</span><span class="sxs-lookup"><span data-stu-id="9a241-170">Handle the event</span></span>

<span data-ttu-id="9a241-171">L’événement **OnTrackingChanged** est appelé chaque fois que l’ancrage spatial sous-jacent change entre un État localisable et n’est pas localisable.</span><span class="sxs-lookup"><span data-stu-id="9a241-171">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="9a241-172">Ensuite, gérez l’événement :</span><span class="sxs-lookup"><span data-stu-id="9a241-172">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="9a241-173">Parfois, les ancres se trouvent immédiatement.</span><span class="sxs-lookup"><span data-stu-id="9a241-173">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="9a241-174">Dans ce cas, cette propriété isLocated de l’ancre sera définie sur true lorsque AddComponent <WorldAnchor> () retourne.</span><span class="sxs-lookup"><span data-stu-id="9a241-174">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="9a241-175">Par conséquent, l’événement OnTrackingChanged n’est pas déclenché.</span><span class="sxs-lookup"><span data-stu-id="9a241-175">As a result, the OnTrackingChanged event won't be triggered.</span></span> <span data-ttu-id="9a241-176">Un modèle propre serait d’appeler votre gestionnaire OnTrackingChanged avec l’état initial de IsLocated après avoir attaché une ancre.</span><span class="sxs-lookup"><span data-stu-id="9a241-176">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="9a241-177">Persistance des hologrammes pour plusieurs appareils</span><span class="sxs-lookup"><span data-stu-id="9a241-177">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="9a241-178">Vous pouvez utiliser des <a href="/azure/spatial-anchors/overview" target="_blank">ancres spatiales Azure</a> pour créer une ancre Cloud durable à partir d’un WorldAnchor local, que votre application peut ensuite localiser sur plusieurs appareils HoloLens, iOS et Android, même si ces appareils ne sont pas présents simultanément.</span><span class="sxs-lookup"><span data-stu-id="9a241-178">You can use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices aren't present together at the same time.</span></span>  <span data-ttu-id="9a241-179">Étant donné que les ancres Cloud sont persistantes, plusieurs périphériques peuvent voir le contenu affiché par rapport à cette ancre dans le même emplacement physique.</span><span class="sxs-lookup"><span data-stu-id="9a241-179">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="9a241-180">Pour commencer à créer des expériences partagées dans Unity, essayez les Démarrages rapides de 5 minutes d' <a href="/azure/spatial-anchors/unity-overview" target="_blank">Unity spatiales Azure Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="9a241-180">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="9a241-181">Une fois que vous êtes opérationnel avec les ancres spatiales Azure, vous pouvez <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">créer et localiser des ancres dans Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="9a241-181">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>
