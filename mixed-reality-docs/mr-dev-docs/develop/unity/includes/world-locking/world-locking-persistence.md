---
ms.openlocfilehash: 25e42ba872764a98d4cb966b5a4922cc1dea0dc9
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528774"
---
# <a name="world-locking-tools-recommended"></a>[<span data-ttu-id="031da-101">Outils de verrouillage universel (recommandé)</span><span class="sxs-lookup"><span data-stu-id="031da-101">World Locking Tools (Recommended)</span></span>](#tab/wlt)

<span data-ttu-id="031da-102">Par défaut, les outils de verrouillage universel restaurent le système de coordonnées de l’unité par rapport au monde physique entre les sessions.</span><span class="sxs-lookup"><span data-stu-id="031da-102">By default, World Locking Tools will restore Unity's coordinate system relative to the physical world across sessions.</span></span> <span data-ttu-id="031da-103">Cela signifie que pour qu’un hologramme apparaisse au même endroit dans le monde physique après la sortie et la réexécution de l’application, l’hologramme n’a besoin que de la même pose.</span><span class="sxs-lookup"><span data-stu-id="031da-103">This means that to have a hologram appear the same place in the physical world after quitting and re-running the application, the hologram only needs to have the same Pose again.</span></span>

![Composant de contexte de verrouillage universel dans l’inspecteur Unity](../../images/world-locking-tools-img-02.png)

<span data-ttu-id="031da-105">Si l’application a besoin d’un contrôle plus fin, l' **enregistrement automatique** et le **chargement automatique** peuvent être désactivés dans l’inspecteur et la persistance gérée à partir d’un script, comme décrit dans la [section persistance de la documentation](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/Concepts/Advanced/Persistence.html).</span><span class="sxs-lookup"><span data-stu-id="031da-105">If the application needs finer control, **Auto-Save** and **Auto-Load** may be disabled in the inspector, and persistence managed from a script as described in the [persistence section of the documentation](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/Concepts/Advanced/Persistence.html).</span></span>

# <a name="aranchormanager"></a>[<span data-ttu-id="031da-106">ARAnchorManager</span><span class="sxs-lookup"><span data-stu-id="031da-106">ARAnchorManager</span></span>](#tab/anchorstore)

<span data-ttu-id="031da-107">Une API supplémentaire appelée **XRAnchorStore** permet aux ancres d’être rendues persistantes entre les sessions.</span><span class="sxs-lookup"><span data-stu-id="031da-107">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="031da-108">Le XRAnchorStore est une représentation des ancres enregistrées sur un appareil.</span><span class="sxs-lookup"><span data-stu-id="031da-108">The XRAnchorStore is a representation of the saved anchors on a device.</span></span> <span data-ttu-id="031da-109">Les ancres peuvent être rendues persistantes à partir de **ARAnchors** dans la scène Unity, chargées à partir du stockage dans un nouveau **ARAnchors**, ou supprimées du stockage.</span><span class="sxs-lookup"><span data-stu-id="031da-109">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="031da-110">Ces ancres doivent être enregistrées et chargées sur le même appareil.</span><span class="sxs-lookup"><span data-stu-id="031da-110">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="031da-111">Le stockage d’ancrage entre appareils sera pris en charge via les ancres spatiales Azure dans une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="031da-111">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

### <a name="namespaces"></a><span data-ttu-id="031da-112">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="031da-112">Namespaces</span></span>

<span data-ttu-id="031da-113">Pour **unity 2020 et OpenXR**:</span><span class="sxs-lookup"><span data-stu-id="031da-113">For **Unity 2020 and OpenXR**:</span></span> 

``` cs
using Microsoft.MixedReality.ARSubsystems.XRAnchorStore
```

<span data-ttu-id="031da-114">ou **unity 2019/2020 + plug-in XR Windows**:</span><span class="sxs-lookup"><span data-stu-id="031da-114">or **Unity 2019/2020 + Windows XR Plugin**:</span></span> 

```cs 
using UnityEngine.XR.WindowsMR.XRAnchorStore
```

### <a name="public-methods"></a><span data-ttu-id="031da-115">Méthodes publiques</span><span class="sxs-lookup"><span data-stu-id="031da-115">Public methods</span></span>

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

### <a name="getting-an-anchor-store-reference"></a><span data-ttu-id="031da-116">Obtention d’une référence de magasin d’ancrage</span><span class="sxs-lookup"><span data-stu-id="031da-116">Getting an anchor store reference</span></span> 

<span data-ttu-id="031da-117">Pour charger le XRAnchorStore avec **unity 2020 et OpenXR**, utilisez la méthode d’extension sur XRAnchorSubsystem, le sous-système d’un ARAnchorManager :</span><span class="sxs-lookup"><span data-stu-id="031da-117">To load the XRAnchorStore with **Unity 2020 and OpenXR**, use extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="031da-118">Pour charger le XRAnchorStore avec **unity 2019/2020 et le plug-in Windows XR**, utilisez la méthode d’extension sur XRReferencePointSubsystem (unity 2019) ou XRAnchorSubsystem (unity 2020), le sous-système d’un ARReferencePointManager/ARAnchorManager :</span><span class="sxs-lookup"><span data-stu-id="031da-118">To load the XRAnchorStore with **Unity 2019/2020 and the Windows XR Plugin**, use the extension method on the XRReferencePointSubsystem (Unity 2019) or XRAnchorSubsystem (Unity 2020), the subsystem of an ARReferencePointManager/ARAnchorManager:</span></span>

```cs
// Unity 2019 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem);

// Unity 2020 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem);
```

### <a name="loading-an-anchor-store"></a><span data-ttu-id="031da-119">Chargement d’un magasin d’ancrage</span><span class="sxs-lookup"><span data-stu-id="031da-119">Loading an anchor store</span></span>

<span data-ttu-id="031da-120">Pour charger un magasin d’ancrage dans **unity 2020 et OpenXR**, accédez à celui-ci à partir du sous-système d’un ARAnchorManager, comme suit :</span><span class="sxs-lookup"><span data-stu-id="031da-120">To load an anchor store in **Unity 2020 and OpenXR**, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="031da-121">ou avec **unity 2019/2020 et le plug-in XR de Windows**:</span><span class="sxs-lookup"><span data-stu-id="031da-121">or with **Unity 2019/2020 and the Windows XR Plugin**:</span></span>

``` cs
// Unity 2019
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();

// Unity 2020
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

<span data-ttu-id="031da-122">Pour voir un exemple complet d’ancres persistantes/non persistantes, consultez l’exemple d’ancres-> ancres GameObject et AnchorsSample. cs dans la [scène exemple de plug-in de réalité mixte OpenXR](../../openxr-getting-started.md#hololens-2-samples):</span><span class="sxs-lookup"><span data-stu-id="031da-122">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](../../openxr-getting-started.md#hololens-2-samples):</span></span>

![Capture d’écran de l’ouverture du panneau de la hiérarchie dans l’éditeur Unity avec l’exemple ancres mis en surbrillance](../../images/openxr-features-img-04.png)

![Capture d’écran du panneau Inspecteur ouvert dans l’éditeur Unity avec l’exemple de script Anchors mis en surbrillance](../../images/openxr-features-img-05.png)

# <a name="worldanchor"></a>[<span data-ttu-id="031da-125">WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="031da-125">WorldAnchor</span></span>](#tab/worldanchor)

<span data-ttu-id="031da-126">Le **WorldAnchorStore** est la clé de la création d’expériences holographiques dans lesquelles les hologrammes restent dans des positions réelles spécifiques entre les instances de l’application.</span><span class="sxs-lookup"><span data-stu-id="031da-126">The **WorldAnchorStore** is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="031da-127">Les utilisateurs peuvent ensuite épingler des hologrammes individuels où ils le souhaitent, et les trouver plus tard dans les mêmes cas sur de nombreuses utilisations de votre application.</span><span class="sxs-lookup"><span data-stu-id="031da-127">Users can then pin individual holograms wherever they want, and find them later in the same spot over many uses of your app.</span></span>

<span data-ttu-id="031da-128">**Espace de noms :** *UnityEngine. XR. WSA. persistance*</span><span class="sxs-lookup"><span data-stu-id="031da-128">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="031da-129">**Classe :** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="031da-129">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="031da-130">Le WorldAnchorStore vous permet de conserver l’emplacement des WorldAnchor entre les sessions.</span><span class="sxs-lookup"><span data-stu-id="031da-130">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="031da-131">Pour conserver les hologrammes entre les sessions, vous devez effectuer un suivi séparé de vos GameObjects qui utilisent une ancre mondiale particulière.</span><span class="sxs-lookup"><span data-stu-id="031da-131">To actually persist holograms across sessions, you'll need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="031da-132">Il est souvent judicieux de créer une racine GameObject avec une ancre mondiale et de faire en sorte que les hologrammes enfants soient ancrés avec un décalage de position local.</span><span class="sxs-lookup"><span data-stu-id="031da-132">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="031da-133">Pour charger des hologrammes à partir de sessions précédentes :</span><span class="sxs-lookup"><span data-stu-id="031da-133">To load holograms from previous sessions:</span></span>

1. <span data-ttu-id="031da-134">Obtient le WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="031da-134">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="031da-135">Charger les données d’application relatives à l’ancre mondiale, qui vous donne l’ID du point d’ancrage</span><span class="sxs-lookup"><span data-stu-id="031da-135">Load app data relating to the world anchor, which gives you the ID of the world anchor</span></span>
3. <span data-ttu-id="031da-136">Charger une ancre universelle à partir de son ID</span><span class="sxs-lookup"><span data-stu-id="031da-136">Load a world anchor from its ID</span></span>

<span data-ttu-id="031da-137">Pour enregistrer des hologrammes pour les sessions à venir :</span><span class="sxs-lookup"><span data-stu-id="031da-137">To save holograms for future sessions:</span></span>

1. <span data-ttu-id="031da-138">Obtient le WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="031da-138">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="031da-139">Enregistrer une ancre mondiale en spécifiant un ID</span><span class="sxs-lookup"><span data-stu-id="031da-139">Save a world anchor specifying an ID</span></span>
3. <span data-ttu-id="031da-140">Enregistrer les données d’application relatives à l’ancre mondiale avec un ID</span><span class="sxs-lookup"><span data-stu-id="031da-140">Save app data relating to the world anchor along with an ID</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="031da-141">Obtention du WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="031da-141">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="031da-142">Il est préférable de conserver une référence à WorldAnchorStore afin de savoir quand il est prêt à effectuer une opération.</span><span class="sxs-lookup"><span data-stu-id="031da-142">You'll want to keep a reference to the WorldAnchorStore so you know when it's ready to perform an operation.</span></span> <span data-ttu-id="031da-143">Étant donné qu’il s’agit d’un appel asynchrone, éventuellement dès le démarrage, vous souhaitez appeler :</span><span class="sxs-lookup"><span data-stu-id="031da-143">Since this is an async call, potentially as soon as start up, you want to call:</span></span>

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="031da-144">Dans ce cas, StoreLoaded est notre gestionnaire pour la fin du chargement du WorldAnchorStore :</span><span class="sxs-lookup"><span data-stu-id="031da-144">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

<span data-ttu-id="031da-145">Nous avons maintenant une référence à WorldAnchorStore, que nous allons utiliser pour enregistrer et charger des ancres universelles spécifiques.</span><span class="sxs-lookup"><span data-stu-id="031da-145">We now have a reference to the WorldAnchorStore, which we'll use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="031da-146">Enregistrement d’un WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="031da-146">Saving a WorldAnchor</span></span>

<span data-ttu-id="031da-147">Pour ce faire, nous devons simplement nommer ce que nous enregistrons et le transférer dans le WorldAnchor que nous avons reçu avant l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="031da-147">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="031da-148">Remarque : la tentative d’enregistrement de deux ancres dans la même chaîne échoue (Store. L’enregistrement retourne la valeur false).</span><span class="sxs-lookup"><span data-stu-id="031da-148">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="031da-149">Supprimer le précédent enregistrement avant d’en enregistrer un nouveau :</span><span class="sxs-lookup"><span data-stu-id="031da-149">Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="031da-150">Chargement d’un WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="031da-150">Loading a WorldAnchor</span></span>

<span data-ttu-id="031da-151">Et pour charger :</span><span class="sxs-lookup"><span data-stu-id="031da-151">And to load:</span></span>

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

<span data-ttu-id="031da-152">Nous pouvons également utiliser le Store. Delete () pour supprimer une ancre précédemment enregistrée et stockée. Clear () pour supprimer toutes les données précédemment enregistrées.</span><span class="sxs-lookup"><span data-stu-id="031da-152">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="031da-153">Énumération des ancres existantes</span><span class="sxs-lookup"><span data-stu-id="031da-153">Enumerating Existing Anchors</span></span>

<span data-ttu-id="031da-154">Pour découvrir les ancres précédemment stockées, appelez GetAllIds.</span><span class="sxs-lookup"><span data-stu-id="031da-154">To discover previously stored anchors, call GetAllIds.</span></span>

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="031da-155">Persistance des hologrammes pour plusieurs appareils</span><span class="sxs-lookup"><span data-stu-id="031da-155">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="031da-156">Vous pouvez utiliser des <a href="/azure/spatial-anchors/overview" target="_blank">ancres spatiales Azure</a> pour créer une ancre Cloud durable à partir d’un WorldAnchor local, que votre application peut ensuite localiser sur plusieurs appareils HoloLens, iOS et Android, même si ces appareils ne sont pas présents simultanément.</span><span class="sxs-lookup"><span data-stu-id="031da-156">You can use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices aren't present together at the same time.</span></span>  <span data-ttu-id="031da-157">Étant donné que les ancres Cloud sont persistantes, plusieurs périphériques peuvent voir le contenu affiché par rapport à cette ancre dans le même emplacement physique.</span><span class="sxs-lookup"><span data-stu-id="031da-157">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="031da-158">Pour commencer à créer des expériences partagées dans Unity, essayez les Démarrages rapides de 5 minutes d' <a href="/azure/spatial-anchors/unity-overview" target="_blank">Unity spatiales Azure Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="031da-158">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="031da-159">Une fois que vous êtes opérationnel avec les ancres spatiales Azure, vous pouvez <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">créer et localiser des ancres dans Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="031da-159">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>
