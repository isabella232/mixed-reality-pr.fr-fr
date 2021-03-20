---
ms.openlocfilehash: bb2df8c85dd05981c1438bdb076b0aad16c7efd7
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104719894"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="0bc31-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="0bc31-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="0bc31-102">Une API supplémentaire appelée **XRAnchorStore** permet aux ancres d’être rendues persistantes entre les sessions.</span><span class="sxs-lookup"><span data-stu-id="0bc31-102">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="0bc31-103">Le XRAnchorStore est une représentation des ancres enregistrées sur un appareil.</span><span class="sxs-lookup"><span data-stu-id="0bc31-103">The XRAnchorStore is a representation of the saved anchors on a device.</span></span> <span data-ttu-id="0bc31-104">Les ancres peuvent être rendues persistantes à partir de **ARAnchors** dans la scène Unity, chargées à partir du stockage dans un nouveau **ARAnchors**, ou supprimées du stockage.</span><span class="sxs-lookup"><span data-stu-id="0bc31-104">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="0bc31-105">Ces ancres doivent être enregistrées et chargées sur le même appareil.</span><span class="sxs-lookup"><span data-stu-id="0bc31-105">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="0bc31-106">Le stockage d’ancrage entre appareils sera pris en charge via les ancres spatiales Azure dans une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="0bc31-106">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

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

<span data-ttu-id="0bc31-107">Pour charger XRAnchorStore, le plug-in fournit une méthode d’extension sur XRAnchorSubsystem, le sous-système d’un ARAnchorManager :</span><span class="sxs-lookup"><span data-stu-id="0bc31-107">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="0bc31-108">Pour utiliser cette méthode d’extension, accédez à celle-ci à partir du sous-système d’un ARAnchorManager, comme suit :</span><span class="sxs-lookup"><span data-stu-id="0bc31-108">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="0bc31-109">Pour voir un exemple complet d’ancres persistantes/non persistantes, consultez l’exemple d’ancres-> ancres GameObject et AnchorsSample. cs dans la [scène exemple de plug-in de réalité mixte OpenXR](../openxr-getting-started.md#hololens-2-samples):</span><span class="sxs-lookup"><span data-stu-id="0bc31-109">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](../openxr-getting-started.md#hololens-2-samples):</span></span>

![Capture d’écran de l’ouverture du panneau de la hiérarchie dans l’éditeur Unity avec l’exemple ancres mis en surbrillance](../images/openxr-features-img-04.png)

![Capture d’écran du panneau Inspecteur ouvert dans l’éditeur Unity avec l’exemple de script Anchors mis en surbrillance](../images/openxr-features-img-05.png)

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="0bc31-112">Plug-in Unity 2019/2020 + Windows XR</span><span class="sxs-lookup"><span data-stu-id="0bc31-112">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="0bc31-113">Une API appelée **XRAnchorStore** permet aux ancres d’être conservées entre les sessions.</span><span class="sxs-lookup"><span data-stu-id="0bc31-113">An API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="0bc31-114">Le XRAnchorStore est une représentation des ancres enregistrées sur un appareil.</span><span class="sxs-lookup"><span data-stu-id="0bc31-114">The XRAnchorStore is a representation of the saved anchors on a device.</span></span> <span data-ttu-id="0bc31-115">Les ancres peuvent être rendues persistantes à partir de **ARAnchors** dans la scène Unity, chargées à partir du stockage dans un nouveau **ARAnchors**, ou supprimées du stockage.</span><span class="sxs-lookup"><span data-stu-id="0bc31-115">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="0bc31-116">Ces ancres doivent être enregistrées et chargées sur le même appareil.</span><span class="sxs-lookup"><span data-stu-id="0bc31-116">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="0bc31-117">Le stockage d’ancrage entre appareils sera pris en charge via les ancres spatiales Azure dans une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="0bc31-117">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

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

<span data-ttu-id="0bc31-118">Pour charger le XRAnchorStore, le plug-in fournit une méthode d’extension sur le XRReferencePointSubsystem (Unity 2019) ou XRAnchorSubsystem (Unity 2020), le sous-système d’un ARReferencePointManager/ARAnchorManager :</span><span class="sxs-lookup"><span data-stu-id="0bc31-118">To load the XRAnchorStore, the plugin provides an extension method on the XRReferencePointSubsystem (Unity 2019) or XRAnchorSubsystem (Unity 2020), the subsystem of an ARReferencePointManager/ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem); // Unity 2019
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem); // Unity 2020
```

<span data-ttu-id="0bc31-119">Pour utiliser cette méthode d’extension, accédez à celle-ci à partir du sous-système d’un ARAnchorManager comme suit pour Unity 2019 :</span><span class="sxs-lookup"><span data-stu-id="0bc31-119">To use this extension method, access it from an ARAnchorManager's subsystem as follows for Unity 2019:</span></span>

``` cs
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();
```

<span data-ttu-id="0bc31-120">ou pour Unity 2020 :</span><span class="sxs-lookup"><span data-stu-id="0bc31-120">or for Unity 2020:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

# <a name="legacy-wsa"></a>[<span data-ttu-id="0bc31-121">WSA hérité</span><span class="sxs-lookup"><span data-stu-id="0bc31-121">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="0bc31-122">Le **WorldAnchorStore** est la clé de la création d’expériences holographiques dans lesquelles les hologrammes restent dans des positions réelles spécifiques entre les instances de l’application.</span><span class="sxs-lookup"><span data-stu-id="0bc31-122">The **WorldAnchorStore** is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="0bc31-123">Les utilisateurs peuvent ensuite épingler des hologrammes individuels où ils le souhaitent, et les trouver plus tard dans les mêmes cas sur de nombreuses utilisations de votre application.</span><span class="sxs-lookup"><span data-stu-id="0bc31-123">Users can then pin individual holograms wherever they want, and find them later in the same spot over many uses of your app.</span></span>

<span data-ttu-id="0bc31-124">**Espace de noms :** *UnityEngine. XR. WSA. persistance*</span><span class="sxs-lookup"><span data-stu-id="0bc31-124">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="0bc31-125">**Classe :** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="0bc31-125">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="0bc31-126">Le WorldAnchorStore vous permet de conserver l’emplacement des WorldAnchor entre les sessions.</span><span class="sxs-lookup"><span data-stu-id="0bc31-126">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="0bc31-127">Pour conserver les hologrammes entre les sessions, vous devez effectuer un suivi séparé de vos GameObjects qui utilisent une ancre mondiale particulière.</span><span class="sxs-lookup"><span data-stu-id="0bc31-127">To actually persist holograms across sessions, you'll need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="0bc31-128">Il est souvent judicieux de créer une racine GameObject avec une ancre mondiale et de faire en sorte que les hologrammes enfants soient ancrés avec un décalage de position local.</span><span class="sxs-lookup"><span data-stu-id="0bc31-128">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="0bc31-129">Pour charger des hologrammes à partir de sessions précédentes :</span><span class="sxs-lookup"><span data-stu-id="0bc31-129">To load holograms from previous sessions:</span></span>

1. <span data-ttu-id="0bc31-130">Obtient le WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="0bc31-130">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="0bc31-131">Charger les données d’application relatives à l’ancre mondiale, qui vous donne l’ID du point d’ancrage</span><span class="sxs-lookup"><span data-stu-id="0bc31-131">Load app data relating to the world anchor, which gives you the ID of the world anchor</span></span>
3. <span data-ttu-id="0bc31-132">Charger une ancre universelle à partir de son ID</span><span class="sxs-lookup"><span data-stu-id="0bc31-132">Load a world anchor from its ID</span></span>

<span data-ttu-id="0bc31-133">Pour enregistrer des hologrammes pour les sessions à venir :</span><span class="sxs-lookup"><span data-stu-id="0bc31-133">To save holograms for future sessions:</span></span>

1. <span data-ttu-id="0bc31-134">Obtient le WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="0bc31-134">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="0bc31-135">Enregistrer une ancre mondiale en spécifiant un ID</span><span class="sxs-lookup"><span data-stu-id="0bc31-135">Save a world anchor specifying an ID</span></span>
3. <span data-ttu-id="0bc31-136">Enregistrer les données d’application relatives à l’ancre mondiale avec un ID</span><span class="sxs-lookup"><span data-stu-id="0bc31-136">Save app data relating to the world anchor along with an ID</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="0bc31-137">Obtention du WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="0bc31-137">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="0bc31-138">Il est préférable de conserver une référence à WorldAnchorStore afin de savoir quand il est prêt à effectuer une opération.</span><span class="sxs-lookup"><span data-stu-id="0bc31-138">You'll want to keep a reference to the WorldAnchorStore so you know when it's ready to perform an operation.</span></span> <span data-ttu-id="0bc31-139">Étant donné qu’il s’agit d’un appel asynchrone, éventuellement dès le démarrage, vous souhaitez appeler :</span><span class="sxs-lookup"><span data-stu-id="0bc31-139">Since this is an async call, potentially as soon as start up, you want to call:</span></span>

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="0bc31-140">Dans ce cas, StoreLoaded est notre gestionnaire pour la fin du chargement du WorldAnchorStore :</span><span class="sxs-lookup"><span data-stu-id="0bc31-140">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

<span data-ttu-id="0bc31-141">Nous avons maintenant une référence à WorldAnchorStore, que nous allons utiliser pour enregistrer et charger des ancres universelles spécifiques.</span><span class="sxs-lookup"><span data-stu-id="0bc31-141">We now have a reference to the WorldAnchorStore, which we'll use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="0bc31-142">Enregistrement d’un WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="0bc31-142">Saving a WorldAnchor</span></span>

<span data-ttu-id="0bc31-143">Pour ce faire, nous devons simplement nommer ce que nous enregistrons et le transférer dans le WorldAnchor que nous avons reçu avant l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="0bc31-143">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="0bc31-144">Remarque : la tentative d’enregistrement de deux ancres dans la même chaîne échoue (Store. L’enregistrement retourne la valeur false).</span><span class="sxs-lookup"><span data-stu-id="0bc31-144">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="0bc31-145">Supprimer le précédent enregistrement avant d’en enregistrer un nouveau :</span><span class="sxs-lookup"><span data-stu-id="0bc31-145">Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="0bc31-146">Chargement d’un WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="0bc31-146">Loading a WorldAnchor</span></span>

<span data-ttu-id="0bc31-147">Et pour charger :</span><span class="sxs-lookup"><span data-stu-id="0bc31-147">And to load:</span></span>

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

<span data-ttu-id="0bc31-148">Nous pouvons également utiliser le Store. Delete () pour supprimer une ancre précédemment enregistrée et stockée. Clear () pour supprimer toutes les données précédemment enregistrées.</span><span class="sxs-lookup"><span data-stu-id="0bc31-148">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="0bc31-149">Énumération des ancres existantes</span><span class="sxs-lookup"><span data-stu-id="0bc31-149">Enumerating Existing Anchors</span></span>

<span data-ttu-id="0bc31-150">Pour découvrir les ancres précédemment stockées, appelez GetAllIds.</span><span class="sxs-lookup"><span data-stu-id="0bc31-150">To discover previously stored anchors, call GetAllIds.</span></span>

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="0bc31-151">Persistance des hologrammes pour plusieurs appareils</span><span class="sxs-lookup"><span data-stu-id="0bc31-151">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="0bc31-152">Vous pouvez utiliser des <a href="/azure/spatial-anchors/overview" target="_blank">ancres spatiales Azure</a> pour créer une ancre Cloud durable à partir d’un WorldAnchor local, que votre application peut ensuite localiser sur plusieurs appareils HoloLens, iOS et Android, même si ces appareils ne sont pas présents simultanément.</span><span class="sxs-lookup"><span data-stu-id="0bc31-152">You can use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices aren't present together at the same time.</span></span>  <span data-ttu-id="0bc31-153">Étant donné que les ancres Cloud sont persistantes, plusieurs périphériques peuvent voir le contenu affiché par rapport à cette ancre dans le même emplacement physique.</span><span class="sxs-lookup"><span data-stu-id="0bc31-153">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="0bc31-154">Pour commencer à créer des expériences partagées dans Unity, essayez les Démarrages rapides de 5 minutes d' <a href="/azure/spatial-anchors/unity-overview" target="_blank">Unity spatiales Azure Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="0bc31-154">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="0bc31-155">Une fois que vous êtes opérationnel avec les ancres spatiales Azure, vous pouvez <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">créer et localiser des ancres dans Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="0bc31-155">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>
