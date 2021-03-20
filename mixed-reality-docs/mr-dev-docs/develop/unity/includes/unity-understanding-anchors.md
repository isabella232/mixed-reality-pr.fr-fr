---
ms.openlocfilehash: 05e2b87383bbc91b7fd8785230152e3549f4b22d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104719977"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="8cea2-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="8cea2-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="8cea2-102">Le plug-in OpenXR de réalité mixte fournit des fonctionnalités d’ancre de base via une implémentation du **ARAnchorManager** ARFoundation d’Unity.</span><span class="sxs-lookup"><span data-stu-id="8cea2-102">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="8cea2-103">Pour connaître les principes de base de ARAnchors dans ARFoundation, consultez le [Manuel ARFoundation du gestionnaire d’ancrage AR](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span><span class="sxs-lookup"><span data-stu-id="8cea2-103">To learn the basics on ARAnchors in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> 

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="8cea2-104">Plug-in Unity 2019/2020 + Windows XR</span><span class="sxs-lookup"><span data-stu-id="8cea2-104">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="8cea2-105">Le plug-in OpenXR de réalité mixte fournit des fonctionnalités d’ancre de base via une implémentation du **ARAnchorManager** ARFoundation d’Unity.</span><span class="sxs-lookup"><span data-stu-id="8cea2-105">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="8cea2-106">Pour connaître les principes de base de ARAnchors dans ARFoundation, consultez le [Manuel ARFoundation du gestionnaire d’ancrage AR](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span><span class="sxs-lookup"><span data-stu-id="8cea2-106">To learn the basics on ARAnchors in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="8cea2-107">WSA hérité</span><span class="sxs-lookup"><span data-stu-id="8cea2-107">Legacy WSA</span></span>](#tab/wsa)

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="8cea2-108">Création d’une expérience à l’échelle mondiale</span><span class="sxs-lookup"><span data-stu-id="8cea2-108">Building a world-scale experience</span></span>

<span data-ttu-id="8cea2-109">**Espace de noms :** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="8cea2-109">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="8cea2-110">**Type :** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="8cea2-110">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="8cea2-111">Pour les expériences réelles à l' **échelle mondiale** sur HoloLens qui permettent aux utilisateurs d’aller au-delà de 5 mètres, vous aurez besoin de nouvelles techniques au-delà de celles utilisées pour les expériences à l’échelle de la place.</span><span class="sxs-lookup"><span data-stu-id="8cea2-111">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="8cea2-112">Une technique clé que vous allez utiliser consiste à créer une [ancre spatiale](../../../design/coordinate-systems.md#spatial-anchors) pour verrouiller un cluster d’hologrammes précisément en place dans le monde physique, quel que soit le degré d’itinérance de l’utilisateur, puis [retrouvez ces hologrammes dans les sessions ultérieures](../../../design/coordinate-systems.md#spatial-anchor-persistence).</span><span class="sxs-lookup"><span data-stu-id="8cea2-112">One key technique you'll use is to create a [spatial anchor](../../../design/coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, no matter how far the user has roamed, and then [find those holograms again in later sessions](../../../design/coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="8cea2-113">Dans Unity, vous créez une ancre spatiale en ajoutant le composant **WorldAnchor** Unity à un GameObject.</span><span class="sxs-lookup"><span data-stu-id="8cea2-113">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="8cea2-114">Ajout d’une ancre mondiale</span><span class="sxs-lookup"><span data-stu-id="8cea2-114">Adding a World Anchor</span></span>

<span data-ttu-id="8cea2-115">Pour ajouter une ancre universelle, appelez `AddComponent<WorldAnchor>()` sur l’objet de jeu avec la transformation que vous souhaitez ancrer dans le monde réel.</span><span class="sxs-lookup"><span data-stu-id="8cea2-115">To add a world anchor, call `AddComponent<WorldAnchor>()` on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="8cea2-116">Et voilà !</span><span class="sxs-lookup"><span data-stu-id="8cea2-116">That's it!</span></span> <span data-ttu-id="8cea2-117">Cet objet de jeu sera désormais ancré à son emplacement actuel dans le monde physique : vous pouvez constater que ses coordonnées universelles s’ajustent légèrement au fil du temps pour garantir l’alignement physique.</span><span class="sxs-lookup"><span data-stu-id="8cea2-117">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="8cea2-118">Reportez-vous à [chargement d’une ancre mondiale](#loading-a-worldanchor) pour rechercher cet emplacement d’ancrage dans une session d’application future.</span><span class="sxs-lookup"><span data-stu-id="8cea2-118">Refer to [loading a world anchor](#loading-a-worldanchor) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="8cea2-119">Suppression d’une ancre mondiale</span><span class="sxs-lookup"><span data-stu-id="8cea2-119">Removing a World Anchor</span></span>

<span data-ttu-id="8cea2-120">Si vous ne souhaitez plus que les GameObject soient verrouillés sur un emplacement géographique physique et que vous n’envisagez pas de déplacer ce cadre, vous pouvez simplement appeler Destroy sur le composant d’ancrage du monde.</span><span class="sxs-lookup"><span data-stu-id="8cea2-120">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="8cea2-121">Si vous souhaitez déplacer le GameObject ce frame, vous devez appeler DestroyImmediate à la place.</span><span class="sxs-lookup"><span data-stu-id="8cea2-121">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="8cea2-122">Déplacement d’un GameObject ancré dans le monde</span><span class="sxs-lookup"><span data-stu-id="8cea2-122">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="8cea2-123">Les GameObject ne peuvent pas être déplacées pendant qu’une ancre mondiale y est.</span><span class="sxs-lookup"><span data-stu-id="8cea2-123">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="8cea2-124">Si vous devez déplacer le GameObject ce frame, vous devez :</span><span class="sxs-lookup"><span data-stu-id="8cea2-124">If you need to move the GameObject this frame, you need to:</span></span>

1. <span data-ttu-id="8cea2-125">DestroyImmediate le composant d’ancrage universel</span><span class="sxs-lookup"><span data-stu-id="8cea2-125">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="8cea2-126">Déplacer le GameObject</span><span class="sxs-lookup"><span data-stu-id="8cea2-126">Move the GameObject</span></span>
3. <span data-ttu-id="8cea2-127">Ajoutez un nouveau composant d’ancrage du monde au GameObject.</span><span class="sxs-lookup"><span data-stu-id="8cea2-127">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="8cea2-128">Gestion des modifications de localisabilité</span><span class="sxs-lookup"><span data-stu-id="8cea2-128">Handling Locatability Changes</span></span>

<span data-ttu-id="8cea2-129">Un WorldAnchor peut ne pas être localisable dans le monde physique à un moment donné.</span><span class="sxs-lookup"><span data-stu-id="8cea2-129">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="8cea2-130">Si cela se produit, Unity ne met pas à jour la transformation de l’objet ancré.</span><span class="sxs-lookup"><span data-stu-id="8cea2-130">If that occurs, Unity won't be updating the transform of the anchored object.</span></span> <span data-ttu-id="8cea2-131">Cela peut également changer pendant l’exécution d’une application.</span><span class="sxs-lookup"><span data-stu-id="8cea2-131">This also can change while an app is running.</span></span> <span data-ttu-id="8cea2-132">Si la modification de la localisation n’est pas prise en charge, l’objet n’apparaîtra pas à l’emplacement physique approprié dans le monde.</span><span class="sxs-lookup"><span data-stu-id="8cea2-132">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="8cea2-133">Pour être informé des changements de localisation :</span><span class="sxs-lookup"><span data-stu-id="8cea2-133">To be notified about locatability changes:</span></span>

1. <span data-ttu-id="8cea2-134">S’abonner à l’événement OnTrackingChanged</span><span class="sxs-lookup"><span data-stu-id="8cea2-134">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="8cea2-135">Gérer l’événement</span><span class="sxs-lookup"><span data-stu-id="8cea2-135">Handle the event</span></span>

<span data-ttu-id="8cea2-136">L’événement **OnTrackingChanged** est appelé chaque fois que l’ancrage spatial sous-jacent change entre un État localisable et n’est pas localisable.</span><span class="sxs-lookup"><span data-stu-id="8cea2-136">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="8cea2-137">Ensuite, gérez l’événement :</span><span class="sxs-lookup"><span data-stu-id="8cea2-137">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="8cea2-138">Parfois, les ancres se trouvent immédiatement.</span><span class="sxs-lookup"><span data-stu-id="8cea2-138">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="8cea2-139">Dans ce cas, cette propriété isLocated de l’ancre sera définie sur true lorsque AddComponent <WorldAnchor> () retourne.</span><span class="sxs-lookup"><span data-stu-id="8cea2-139">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="8cea2-140">Par conséquent, l’événement OnTrackingChanged n’est pas déclenché.</span><span class="sxs-lookup"><span data-stu-id="8cea2-140">As a result, the OnTrackingChanged event won't be triggered.</span></span> <span data-ttu-id="8cea2-141">Un modèle propre serait d’appeler votre gestionnaire OnTrackingChanged avec l’état initial de IsLocated après avoir attaché une ancre.</span><span class="sxs-lookup"><span data-stu-id="8cea2-141">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```