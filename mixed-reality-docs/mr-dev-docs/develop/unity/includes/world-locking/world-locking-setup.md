---
ms.openlocfilehash: 6229b258233f7a80ef6530edd6eb94774a0e54cf
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528760"
---
# <a name="world-locking-tools-recommended"></a>[<span data-ttu-id="7084b-101">Outils de verrouillage universel (recommandé)</span><span class="sxs-lookup"><span data-stu-id="7084b-101">World Locking Tools (Recommended)</span></span>](#tab/wlt)

<span data-ttu-id="7084b-102">Nous vous recommandons d’installer les outils de verrouillage du monde à l’aide de la nouvelle fonctionnalité de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="7084b-102">We recommend installing World Locking Tools using the new Mixed Reality Feature Tool.</span></span> <span data-ttu-id="7084b-103">Une fois que vous avez téléchargé l’outil Mixed Reality Feature à partir du lien ci-dessous, sélectionnez la dernière version de **WLT Core** dans la section **outils de verrouillage du monde** :</span><span class="sxs-lookup"><span data-stu-id="7084b-103">Once you've downloaded the Mixed Reality Feature Tool from the link below, select the latest version of **WLT Core** from the **World Locking Tools** section:</span></span>

![Fenêtre de sélection des fonctionnalités de l’outil de réalité mixte avec les outils de verrouillage du monde sélectionnés](../../images/spatial-anchors-setup-img-01.png)

> [!div class="nextstepaction"]
> [<span data-ttu-id="7084b-105">Installer les outils de verrouillage du monde avec l’outil de fonctionnalité MR</span><span class="sxs-lookup"><span data-stu-id="7084b-105">Install World Locking Tools with the MR Feature Tool</span></span>](../../welcome-to-mr-feature-tool.md)

### <a name="automated-setup"></a><span data-ttu-id="7084b-106">Installation automatisée</span><span class="sxs-lookup"><span data-stu-id="7084b-106">Automated setup</span></span>

<span data-ttu-id="7084b-107">Quand votre projet est prêt à l’emploi, exécutez l’utilitaire configurer la scène à partir du kit de tâches de la **réalité mixte > utilitaires > outils de verrouillage du monde**:</span><span class="sxs-lookup"><span data-stu-id="7084b-107">When your project is ready to go, run the configure scene utility from **Mixed Reality Toolkit > Utilities > World Locking Tools**:</span></span>

![Éditeur Unity avec le menu du kit d’outils de réalité mixte sélectionné](../../images/world-locking-configuration-img-01.jpeg)

> [!IMPORTANT]
> <span data-ttu-id="7084b-109">L’utilitaire de configuration de scène peut être réexécuté à tout moment.</span><span class="sxs-lookup"><span data-stu-id="7084b-109">The Configure scene utility can be rerun at any time.</span></span> <span data-ttu-id="7084b-110">Par exemple, elle doit être réexécutée si la cible AR a été remplacée par le kit de développement logiciel (SDK) XR.</span><span class="sxs-lookup"><span data-stu-id="7084b-110">For example, it should be rerun if the AR target has been changed from Legacy to XR SDK.</span></span> <span data-ttu-id="7084b-111">Si la scène est déjà configurée correctement, l’exécution de l’utilitaire n’a aucun effet.</span><span class="sxs-lookup"><span data-stu-id="7084b-111">If the scene is already properly configured, running the utility has no effect.</span></span>

### <a name="visualizers"></a><span data-ttu-id="7084b-112">Visualiseurs</span><span class="sxs-lookup"><span data-stu-id="7084b-112">Visualizers</span></span>

<span data-ttu-id="7084b-113">Lors du développement anticipé, l’ajout de visualiseurs peut être utile pour s’assurer que WLT est configuré et fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="7084b-113">During early development, adding visualizers can be helpful to ensure WLT is setup and working properly.</span></span> <span data-ttu-id="7084b-114">Elles peuvent être supprimées pour des performances de production, ou si, pour une raison quelconque, elles ne sont plus nécessaires, à l’aide de l’utilitaire Remove visualisers.</span><span class="sxs-lookup"><span data-stu-id="7084b-114">They can be removed for production performance, or if for any reason are no longer needed, using the Remove visualizers utility.</span></span> <span data-ttu-id="7084b-115">Vous trouverez plus d’informations sur les visualiseurs dans la [documentation des outils](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/Tools.html#visualizers).</span><span class="sxs-lookup"><span data-stu-id="7084b-115">More details on the visualizers can be found in the [Tools documentation](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/Tools.html#visualizers).</span></span>

# <a name="aranchormanager"></a>[<span data-ttu-id="7084b-116">ARAnchorManager</span><span class="sxs-lookup"><span data-stu-id="7084b-116">ARAnchorManager</span></span>](#tab/anchorstore)

<span data-ttu-id="7084b-117">Le plug-in OpenXR de réalité mixte fournit des fonctionnalités d’ancre de base via une implémentation du **ARAnchorManager** ARFoundation d’Unity.</span><span class="sxs-lookup"><span data-stu-id="7084b-117">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="7084b-118">Pour connaître les principes de base de ARAnchors dans ARFoundation, consultez le [Manuel ARFoundation du gestionnaire d’ancrage AR](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span><span class="sxs-lookup"><span data-stu-id="7084b-118">To learn the basics on ARAnchors in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> 

# <a name="worldanchor"></a>[<span data-ttu-id="7084b-119">WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="7084b-119">WorldAnchor</span></span>](#tab/worldanchor)

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="7084b-120">Création d’une expérience à l’échelle mondiale</span><span class="sxs-lookup"><span data-stu-id="7084b-120">Building a world-scale experience</span></span>

<span data-ttu-id="7084b-121">**Espace de noms :** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="7084b-121">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="7084b-122">**Type :** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="7084b-122">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="7084b-123">Pour les expériences réelles à l' **échelle mondiale** sur HoloLens qui permettent aux utilisateurs d’aller au-delà de 5 mètres, vous aurez besoin de nouvelles techniques au-delà de celles utilisées pour les expériences à l’échelle de la place.</span><span class="sxs-lookup"><span data-stu-id="7084b-123">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="7084b-124">Une technique clé que vous allez utiliser consiste à créer une [ancre spatiale](../../../../design/coordinate-systems.md#spatial-anchors) pour verrouiller un cluster d’hologrammes précisément en place dans le monde physique, quel que soit le degré d’itinérance de l’utilisateur, puis [retrouvez ces hologrammes dans les sessions ultérieures](../../../../design/coordinate-systems.md#spatial-anchor-persistence).</span><span class="sxs-lookup"><span data-stu-id="7084b-124">One key technique you'll use is to create a [spatial anchor](../../../../design/coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, no matter how far the user has roamed, and then [find those holograms again in later sessions](../../../../design/coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="7084b-125">Dans Unity, vous créez une ancre spatiale en ajoutant le composant **WorldAnchor** Unity à un GameObject.</span><span class="sxs-lookup"><span data-stu-id="7084b-125">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="7084b-126">Ajout d’une ancre mondiale</span><span class="sxs-lookup"><span data-stu-id="7084b-126">Adding a World Anchor</span></span>

<span data-ttu-id="7084b-127">Pour ajouter une ancre universelle, appelez `AddComponent<WorldAnchor>()` sur l’objet de jeu avec la transformation que vous souhaitez ancrer dans le monde réel.</span><span class="sxs-lookup"><span data-stu-id="7084b-127">To add a world anchor, call `AddComponent<WorldAnchor>()` on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="7084b-128">Et c’est tout !</span><span class="sxs-lookup"><span data-stu-id="7084b-128">That's it!</span></span> <span data-ttu-id="7084b-129">Cet objet de jeu sera désormais ancré à son emplacement actuel dans le monde physique : vous pouvez constater que ses coordonnées universelles s’ajustent légèrement au fil du temps pour garantir l’alignement physique.</span><span class="sxs-lookup"><span data-stu-id="7084b-129">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="7084b-130">Reportez-vous à [chargement d’une ancre mondiale](#loading-a-worldanchor) pour rechercher cet emplacement d’ancrage dans une session d’application future.</span><span class="sxs-lookup"><span data-stu-id="7084b-130">Refer to [loading a world anchor](#loading-a-worldanchor) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="7084b-131">Suppression d’une ancre mondiale</span><span class="sxs-lookup"><span data-stu-id="7084b-131">Removing a World Anchor</span></span>

<span data-ttu-id="7084b-132">Si vous ne souhaitez plus que les GameObject soient verrouillés sur un emplacement géographique physique et que vous n’envisagez pas de déplacer ce cadre, vous pouvez simplement appeler Destroy sur le composant d’ancrage du monde.</span><span class="sxs-lookup"><span data-stu-id="7084b-132">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="7084b-133">Si vous souhaitez déplacer le GameObject ce frame, vous devez appeler DestroyImmediate à la place.</span><span class="sxs-lookup"><span data-stu-id="7084b-133">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="7084b-134">Déplacement d’un GameObject ancré dans le monde</span><span class="sxs-lookup"><span data-stu-id="7084b-134">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="7084b-135">Les GameObject ne peuvent pas être déplacées pendant qu’une ancre mondiale y est.</span><span class="sxs-lookup"><span data-stu-id="7084b-135">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="7084b-136">Si vous devez déplacer le GameObject ce frame, vous devez :</span><span class="sxs-lookup"><span data-stu-id="7084b-136">If you need to move the GameObject this frame, you need to:</span></span>

1. <span data-ttu-id="7084b-137">DestroyImmediate le composant d’ancrage universel</span><span class="sxs-lookup"><span data-stu-id="7084b-137">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="7084b-138">Déplacer le GameObject</span><span class="sxs-lookup"><span data-stu-id="7084b-138">Move the GameObject</span></span>
3. <span data-ttu-id="7084b-139">Ajoutez un nouveau composant d’ancrage du monde au GameObject.</span><span class="sxs-lookup"><span data-stu-id="7084b-139">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="7084b-140">Gestion des modifications de localisabilité</span><span class="sxs-lookup"><span data-stu-id="7084b-140">Handling Locatability Changes</span></span>

<span data-ttu-id="7084b-141">Un WorldAnchor peut ne pas être localisable dans le monde physique à un moment donné.</span><span class="sxs-lookup"><span data-stu-id="7084b-141">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="7084b-142">Si cela se produit, Unity ne met pas à jour la transformation de l’objet ancré.</span><span class="sxs-lookup"><span data-stu-id="7084b-142">If that occurs, Unity won't be updating the transform of the anchored object.</span></span> <span data-ttu-id="7084b-143">Cela peut également changer pendant l’exécution d’une application.</span><span class="sxs-lookup"><span data-stu-id="7084b-143">This also can change while an app is running.</span></span> <span data-ttu-id="7084b-144">Si la modification de la localisation n’est pas prise en charge, l’objet n’apparaîtra pas à l’emplacement physique approprié dans le monde.</span><span class="sxs-lookup"><span data-stu-id="7084b-144">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="7084b-145">Pour être informé des changements de localisation :</span><span class="sxs-lookup"><span data-stu-id="7084b-145">To be notified about locatability changes:</span></span>

1. <span data-ttu-id="7084b-146">S’abonner à l’événement OnTrackingChanged</span><span class="sxs-lookup"><span data-stu-id="7084b-146">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="7084b-147">Gérer l’événement</span><span class="sxs-lookup"><span data-stu-id="7084b-147">Handle the event</span></span>

<span data-ttu-id="7084b-148">L’événement **OnTrackingChanged** est appelé chaque fois que l’ancrage spatial sous-jacent change entre un État localisable et n’est pas localisable.</span><span class="sxs-lookup"><span data-stu-id="7084b-148">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="7084b-149">Ensuite, gérez l’événement :</span><span class="sxs-lookup"><span data-stu-id="7084b-149">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="7084b-150">Parfois, les ancres se trouvent immédiatement.</span><span class="sxs-lookup"><span data-stu-id="7084b-150">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="7084b-151">Dans ce cas, cette propriété isLocated de l’ancre sera définie sur true lorsque AddComponent <WorldAnchor> () retourne.</span><span class="sxs-lookup"><span data-stu-id="7084b-151">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="7084b-152">Par conséquent, l’événement OnTrackingChanged n’est pas déclenché.</span><span class="sxs-lookup"><span data-stu-id="7084b-152">As a result, the OnTrackingChanged event won't be triggered.</span></span> <span data-ttu-id="7084b-153">Un modèle propre serait d’appeler votre gestionnaire OnTrackingChanged avec l’état initial de IsLocated après avoir attaché une ancre.</span><span class="sxs-lookup"><span data-stu-id="7084b-153">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```