---
ms.openlocfilehash: c7e5be36420ef14fe5aaeaafb49c0a990942339f
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636296"
---
# <a name="mrtk"></a>[<span data-ttu-id="aac91-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="aac91-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="aac91-102">Utilisez la classe [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) à partir de MRTK pour Unity et définissez l' **échelle cible** sur **assis**:</span><span class="sxs-lookup"><span data-stu-id="aac91-102">Use the [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to **Seated**:</span></span>

![Fenêtre Paramètres MRTK](../../images/mrtk-target-scale.png)

<span data-ttu-id="aac91-104">MRTK doit gérer automatiquement la position du PlaySpace et de l’appareil photo, mais il est préférable de vérifier :</span><span class="sxs-lookup"><span data-stu-id="aac91-104">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![MRTK playspace](../../images/mrtk-playspace.png)

1. <span data-ttu-id="aac91-106">Dans le volet **hiérarchie** , développez le gameobject **MixedRealityPlayspace** et recherchez l’objet enfant de l' **appareil photo principal** .</span><span class="sxs-lookup"><span data-stu-id="aac91-106">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="aac91-107">Dans le volet de l' **inspecteur** , recherchez le composant **transformer** et changez la **position** en **(X : 0, Y : 0, Z : 0)**</span><span class="sxs-lookup"><span data-stu-id="aac91-107">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="aac91-108">Kit de développement logiciel (SDK) XR</span><span class="sxs-lookup"><span data-stu-id="aac91-108">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="aac91-109">Définissez le mode d’origine du suivi sur [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span><span class="sxs-lookup"><span data-stu-id="aac91-109">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="aac91-110">Après avoir obtenu le sous-système, appelez [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span><span class="sxs-lookup"><span data-stu-id="aac91-110">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
```

<span data-ttu-id="aac91-111">Et fonctionnent avec [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)d’Unity.</span><span class="sxs-lookup"><span data-stu-id="aac91-111">And work with Unity's [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html).</span></span>

![XR de la plate-forme dans la hiérarchie](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="aac91-113">WSA hérité</span><span class="sxs-lookup"><span data-stu-id="aac91-113">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="aac91-114">Accéder à d' **autres paramètres** de la section paramètres du **lecteur Windows Store**</span><span class="sxs-lookup"><span data-stu-id="aac91-114">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
2. <span data-ttu-id="aac91-115">Choisissez **Windows Mixed realisation** comme périphérique, qui peut être listé comme **Windows holographique** dans les versions antérieures d’Unity</span><span class="sxs-lookup"><span data-stu-id="aac91-115">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
3. <span data-ttu-id="aac91-116">Sélectionner une **réalité virtuelle prise en charge**</span><span class="sxs-lookup"><span data-stu-id="aac91-116">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="aac91-117">Étant donné que l’objet Camera principal est automatiquement marqué comme caméra, Unity alimente tous les mouvements et les translations.</span><span class="sxs-lookup"><span data-stu-id="aac91-117">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="aac91-118">Ces paramètres doivent être appliqués à l’appareil photo dans chaque scène de votre application.</span><span class="sxs-lookup"><span data-stu-id="aac91-118">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="aac91-119">Par défaut, lorsque vous créez une nouvelle scène dans Unity, elle contient un GameObject d’appareil photo principal dans la hiérarchie qui comprend le composant Camera, mais les paramètres ci-dessous ne sont pas correctement appliqués.</span><span class="sxs-lookup"><span data-stu-id="aac91-119">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but does not have the settings below properly applied.</span></span>

<span data-ttu-id="aac91-120">**Espace de noms :** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="aac91-120">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="aac91-121">**Type :** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="aac91-121">**Type:** *XRDevice*</span></span>

<span data-ttu-id="aac91-122">Pour créer une expérience d' **orientation uniquement** ou de mise à l' **échelle assise**, vous devez définir Unity sur le type d’espace de suivi fixe.</span><span class="sxs-lookup"><span data-stu-id="aac91-122">To build an **orientation-only** or **seated-scale experience**, you need to set Unity to the Stationary tracking space type.</span></span> <span data-ttu-id="aac91-123">Espace de suivi fixe définit le système de coordonnées universelles de l’unité pour suivre le [cadre stationnaire de référence](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span><span class="sxs-lookup"><span data-stu-id="aac91-123">Stationary tracking space sets Unity's world coordinate system to track the [stationary frame of reference](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span></span> <span data-ttu-id="aac91-124">Dans le mode de suivi fixe, le contenu placé dans l’éditeur juste devant l’emplacement par défaut de l’appareil photo (Forward is-Z) s’affiche devant l’utilisateur au lancement de l’application.</span><span class="sxs-lookup"><span data-stu-id="aac91-124">In the Stationary tracking mode, content placed in the editor just in front of the camera's default location (forward is -Z) will appear in front of the user when the app launches.</span></span>

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

<span data-ttu-id="aac91-125">**Espace de noms :** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="aac91-125">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="aac91-126">**Type :** *InputTracking*</span><span class="sxs-lookup"><span data-stu-id="aac91-126">**Type:** *InputTracking*</span></span>

<span data-ttu-id="aac91-127">Pour une expérience purement en **orientation uniquement** telle qu’une visionneuse vidéo de 360 degrés (où les mises à jour de la tête de position dépasseraient l’illusion), vous pouvez définir [XR. InputTracking. disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) sur true :</span><span class="sxs-lookup"><span data-stu-id="aac91-127">For a pure **orientation-only experience** such as a 360-degree video viewer (where positional head updates would ruin the illusion), you can then set [XR.InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) to true:</span></span>

```cs
InputTracking.disablePositionalTracking = true;
```

<span data-ttu-id="aac91-128">Pour une expérience de mise à l' **échelle assiste**, pour permettre à l’utilisateur de recentrer plus tard l’origine assise, vous pouvez appeler [XR. Méthode InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) :</span><span class="sxs-lookup"><span data-stu-id="aac91-128">For a **seated-scale experience**, to let the user later recenter the seated origin, you can call the [XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) method:</span></span>

```cs
InputTracking.Recenter();
```

<span data-ttu-id="aac91-129">Si vous créez une [expérience à l’échelle assise](../../../../design/coordinate-systems.md), vous pouvez recentrer l’origine du monde de l’unité à la position de la tête actuelle de l’utilisateur en appelant **[XR. Méthode InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** .</span><span class="sxs-lookup"><span data-stu-id="aac91-129">If you're building a [seated-scale experience](../../../../design/coordinate-systems.md), you can recenter Unity's world origin at the user's current head position by calling the **[XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** method.</span></span>