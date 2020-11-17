---
title: Persistance dans Unity
description: La persistance permet à vos utilisateurs d’épingler des hologrammes individuels ou un espace de travail où qu’ils le souhaitent, puis de les trouver plus tard là où ils s’attendent à plusieurs utilisations de votre application.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, persistance, Unity, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle
ms.openlocfilehash: cff7f05a5a5695ae8e379ed681c3b7320622968c
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678528"
---
# <a name="persistence-in-unity"></a><span data-ttu-id="5eecc-104">Persistance dans Unity</span><span class="sxs-lookup"><span data-stu-id="5eecc-104">Persistence in Unity</span></span>

<span data-ttu-id="5eecc-105">**Espace de noms :** *UnityEngine. XR. WSA. persistance*</span><span class="sxs-lookup"><span data-stu-id="5eecc-105">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="5eecc-106">**Classe :** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="5eecc-106">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="5eecc-107">Le WorldAnchorStore est la clé de la création d’expériences holographiques dans lesquelles les hologrammes restent dans des positions réelles spécifiques entre les instances de l’application.</span><span class="sxs-lookup"><span data-stu-id="5eecc-107">The WorldAnchorStore is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="5eecc-108">Cela permet à vos utilisateurs d’épingler des hologrammes individuels ou un espace de travail où qu’ils le souhaitent, puis de les trouver plus tard là où ils s’attendent à plusieurs utilisations de votre application.</span><span class="sxs-lookup"><span data-stu-id="5eecc-108">This lets your users pin individual holograms or a workspace wherever they want it, and then find it later where they expect over many uses of your app.</span></span>

## <a name="how-to-persist-holograms-across-sessions"></a><span data-ttu-id="5eecc-109">Comment conserver des hologrammes entre les sessions</span><span class="sxs-lookup"><span data-stu-id="5eecc-109">How to persist holograms across sessions</span></span>

<span data-ttu-id="5eecc-110">Le WorldAnchorStore vous permet de conserver l’emplacement des WorldAnchor entre les sessions.</span><span class="sxs-lookup"><span data-stu-id="5eecc-110">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="5eecc-111">Pour conserver les hologrammes entre les sessions, vous devez effectuer un suivi séparé de vos GameObjects qui utilisent une ancre mondiale particulière.</span><span class="sxs-lookup"><span data-stu-id="5eecc-111">To actually persist holograms across sessions, you will need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="5eecc-112">Il est souvent judicieux de créer une racine GameObject avec une ancre mondiale et de faire en sorte que les hologrammes enfants soient ancrés avec un décalage de position local.</span><span class="sxs-lookup"><span data-stu-id="5eecc-112">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="5eecc-113">Pour charger des hologrammes à partir de sessions précédentes :</span><span class="sxs-lookup"><span data-stu-id="5eecc-113">To load holograms from previous sessions:</span></span>
1. <span data-ttu-id="5eecc-114">Obtient le WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="5eecc-114">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="5eecc-115">Charger les données d’application relatives à l’ancre mondiale qui vous donne l’ID de l’ancre mondiale</span><span class="sxs-lookup"><span data-stu-id="5eecc-115">Load app data relating to the world anchor which gives you the id of the world anchor</span></span>
3. <span data-ttu-id="5eecc-116">Charger une ancre universelle à partir de son ID</span><span class="sxs-lookup"><span data-stu-id="5eecc-116">Load a world anchor from its id</span></span>

<span data-ttu-id="5eecc-117">Pour enregistrer des hologrammes pour les sessions à venir :</span><span class="sxs-lookup"><span data-stu-id="5eecc-117">To save holograms for future sessions:</span></span>
1. <span data-ttu-id="5eecc-118">Obtient le WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="5eecc-118">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="5eecc-119">Enregistrer une ancre mondiale en spécifiant un ID</span><span class="sxs-lookup"><span data-stu-id="5eecc-119">Save a world anchor specifying an id</span></span>
3. <span data-ttu-id="5eecc-120">Enregistrer les données d’application relatives à l’ancre mondiale avec un ID</span><span class="sxs-lookup"><span data-stu-id="5eecc-120">Save app data relating to the world anchor along with an id</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="5eecc-121">Obtention du WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="5eecc-121">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="5eecc-122">Nous souhaitons conserver une référence à WorldAnchorStore pour nous assurer que nous sommes prêts à travailler lorsque nous souhaitons effectuer une opération.</span><span class="sxs-lookup"><span data-stu-id="5eecc-122">We will want to keep a reference to the WorldAnchorStore around so we know we are ready to go when we want to perform an operation.</span></span> <span data-ttu-id="5eecc-123">Étant donné qu’il s’agit d’un appel asynchrone, éventuellement dès le démarrage, nous souhaitons appeler</span><span class="sxs-lookup"><span data-stu-id="5eecc-123">Since this is an async call, potentially as soon as start up, we want to call</span></span>

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="5eecc-124">Dans ce cas, StoreLoaded est notre gestionnaire pour la fin du chargement du WorldAnchorStore :</span><span class="sxs-lookup"><span data-stu-id="5eecc-124">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

<span data-ttu-id="5eecc-125">Nous disposons maintenant d’une référence au WorldAnchorStore que nous allons utiliser pour enregistrer et charger des ancres universelles spécifiques.</span><span class="sxs-lookup"><span data-stu-id="5eecc-125">We now have a reference to the WorldAnchorStore which we will use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="5eecc-126">Enregistrement d’un WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="5eecc-126">Saving a WorldAnchor</span></span>

<span data-ttu-id="5eecc-127">Pour ce faire, nous devons simplement nommer ce que nous enregistrons et le transférer dans le WorldAnchor que nous avons reçu avant l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="5eecc-127">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="5eecc-128">Remarque : la tentative d’enregistrement de deux ancres dans la même chaîne échoue (Store. L’enregistrement retourne la valeur false).</span><span class="sxs-lookup"><span data-stu-id="5eecc-128">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="5eecc-129">Vous devez supprimer le précédent enregistrement avant d’enregistrer le nouveau fichier :</span><span class="sxs-lookup"><span data-stu-id="5eecc-129">You need to Delete the previous save before saving the new one:</span></span>

```
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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="5eecc-130">Chargement d’un WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="5eecc-130">Loading a WorldAnchor</span></span>

<span data-ttu-id="5eecc-131">Et pour charger :</span><span class="sxs-lookup"><span data-stu-id="5eecc-131">And to load:</span></span>

```
private void LoadGame()
{
       // Save data about holograms positioned by this world anchor
       this.savedRoot = this.store.Load("rootGameObject", rootGameObject);
       if (!this.savedRoot)
       {
              // We didn't actually have the game root saved! We have to re-place our objects or start over
       }
}
```

<span data-ttu-id="5eecc-132">Nous pouvons également utiliser le Store. Delete () pour supprimer une ancre précédemment enregistrée et stockée. Clear () pour supprimer toutes les données précédemment enregistrées.</span><span class="sxs-lookup"><span data-stu-id="5eecc-132">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="5eecc-133">Énumération des ancres existantes</span><span class="sxs-lookup"><span data-stu-id="5eecc-133">Enumerating Existing Anchors</span></span>

<span data-ttu-id="5eecc-134">Pour découvrir les ancres précédemment stockées, appelez GetAllIds.</span><span class="sxs-lookup"><span data-stu-id="5eecc-134">To discover previously stored anchors, call GetAllIds.</span></span>

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="5eecc-135">Persistance des hologrammes pour plusieurs appareils</span><span class="sxs-lookup"><span data-stu-id="5eecc-135">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="5eecc-136">Vous pouvez utiliser des <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">ancres spatiales Azure</a> pour créer une ancre Cloud durable à partir d’un WorldAnchor local, que votre application peut ensuite localiser sur plusieurs appareils HoloLens, iOS et Android, même si ces appareils ne sont pas présents simultanément.</span><span class="sxs-lookup"><span data-stu-id="5eecc-136">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices are not present together at the same time.</span></span>  <span data-ttu-id="5eecc-137">Étant donné que les ancres Cloud sont persistantes, plusieurs périphériques peuvent voir le contenu affiché par rapport à cette ancre dans le même emplacement physique.</span><span class="sxs-lookup"><span data-stu-id="5eecc-137">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="5eecc-138">Pour commencer à créer des expériences partagées dans Unity, essayez les Démarrages rapides de 5 minutes d' <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Unity spatiales Azure Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="5eecc-138">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="5eecc-139">Une fois que vous êtes opérationnel avec les ancres spatiales Azure, vous pouvez <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">créer et localiser des ancres dans Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="5eecc-139">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="5eecc-140">Point de contrôle de développement suivant</span><span class="sxs-lookup"><span data-stu-id="5eecc-140">Next Development Checkpoint</span></span>

<span data-ttu-id="5eecc-141">Si vous suivez le parcours du point de contrôle de développement Unity que nous avons mis en place, vous êtes au cœur de l’exploration des blocs de construction de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="5eecc-141">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="5eecc-142">À partir de là, vous pouvez passer au module suivant :</span><span class="sxs-lookup"><span data-stu-id="5eecc-142">From here, you can proceed to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5eecc-143">Mappage spatial</span><span class="sxs-lookup"><span data-stu-id="5eecc-143">Spatial mapping</span></span>](spatial-mapping-in-unity.md)

<span data-ttu-id="5eecc-144">Ou accéder aux API et fonctionnalités de la plateforme Mixed Reality :</span><span class="sxs-lookup"><span data-stu-id="5eecc-144">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5eecc-145">Expériences partagées</span><span class="sxs-lookup"><span data-stu-id="5eecc-145">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="5eecc-146">Vous pouvez revenir aux [points de contrôle de développement Unity](unity-development-overview.md#2-core-building-blocks) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="5eecc-146">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="5eecc-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5eecc-147">See Also</span></span>
* [<span data-ttu-id="5eecc-148">Persistance d’ancrage spatial</span><span class="sxs-lookup"><span data-stu-id="5eecc-148">Spatial anchor persistence</span></span>](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <span data-ttu-id="5eecc-149"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="5eecc-149"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="5eecc-150"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Kit de développement logiciel (SDK) d’ancre spatiale Azure pour Unity</a></span><span class="sxs-lookup"><span data-stu-id="5eecc-150"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
