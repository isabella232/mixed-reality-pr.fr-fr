---
ms.openlocfilehash: 61fe8754192c1fbd0634fd9d1e1994327599321b
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748524"
---
# <a name="mrtk"></a>[<span data-ttu-id="68de8-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="68de8-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="68de8-102">Utilisez la classe [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) à partir de MRTK pour Unity et définissez l' **échelle cible** sur **Room** ou **debout**:</span><span class="sxs-lookup"><span data-stu-id="68de8-102">Use the [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to either **Room** or **Standing**:</span></span>

![Fenêtre Paramètres MRTK](../../images/mrtk-target-scale.png)

<span data-ttu-id="68de8-104">MRTK doit gérer automatiquement la position du PlaySpace et de l’appareil photo, mais il est préférable de vérifier :</span><span class="sxs-lookup"><span data-stu-id="68de8-104">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![MRTK playspace](../../images/mrtk-playspace.png)

1. <span data-ttu-id="68de8-106">Dans le volet **hiérarchie** , développez le gameobject **MixedRealityPlayspace** et recherchez l’objet enfant de l' **appareil photo principal** .</span><span class="sxs-lookup"><span data-stu-id="68de8-106">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="68de8-107">Dans le volet de l' **inspecteur** , recherchez le composant **transformer** et changez la **position** en **(X : 0, Y : 0, Z : 0)**</span><span class="sxs-lookup"><span data-stu-id="68de8-107">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="68de8-108">Kit de développement logiciel (SDK) XR</span><span class="sxs-lookup"><span data-stu-id="68de8-108">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="68de8-109">Définissez le mode d’origine du suivi sur [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span><span class="sxs-lookup"><span data-stu-id="68de8-109">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="68de8-110">Après avoir obtenu le sous-système, appelez [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span><span class="sxs-lookup"><span data-stu-id="68de8-110">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Floor);
```

<span data-ttu-id="68de8-111">Et fonctionnent avec [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)d’Unity.</span><span class="sxs-lookup"><span data-stu-id="68de8-111">And work with Unity's [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html).</span></span>

![XR de la plate-forme dans la hiérarchie](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="68de8-113">WSA hérité</span><span class="sxs-lookup"><span data-stu-id="68de8-113">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="68de8-114">Accéder à d' **autres paramètres** de la section paramètres du **lecteur Windows Store**</span><span class="sxs-lookup"><span data-stu-id="68de8-114">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
2. <span data-ttu-id="68de8-115">Choisissez **Windows Mixed realisation** comme périphérique, qui peut être listé comme **Windows holographique** dans les versions antérieures d’Unity</span><span class="sxs-lookup"><span data-stu-id="68de8-115">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
3. <span data-ttu-id="68de8-116">Sélectionner une **réalité virtuelle prise en charge**</span><span class="sxs-lookup"><span data-stu-id="68de8-116">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="68de8-117">Étant donné que l’objet Camera principal est automatiquement marqué comme caméra, Unity alimente tous les mouvements et les translations.</span><span class="sxs-lookup"><span data-stu-id="68de8-117">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="68de8-118">Ces paramètres doivent être appliqués à l’appareil photo dans chaque scène de votre application.</span><span class="sxs-lookup"><span data-stu-id="68de8-118">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="68de8-119">Par défaut, lorsque vous créez une nouvelle scène dans Unity, elle contient un GameObject d’appareil photo principal dans la hiérarchie qui comprend le composant Camera, mais les paramètres ci-dessous ne sont pas correctement appliqués.</span><span class="sxs-lookup"><span data-stu-id="68de8-119">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but does not have the settings below properly applied.</span></span>

<span data-ttu-id="68de8-120">**Espace de noms :** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="68de8-120">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="68de8-121">**Type :** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="68de8-121">**Type:** *XRDevice*</span></span>

<span data-ttu-id="68de8-122">Pour une expérience à l’échelle **permanente** ou à l’échelle de l' **espace**, vous devez placer du contenu par rapport à l’étage.</span><span class="sxs-lookup"><span data-stu-id="68de8-122">For a **standing-scale** or **room-scale experience**, you'll need to place content relative to the floor.</span></span> <span data-ttu-id="68de8-123">Vous avez raison de l’étage de l’utilisateur à l’aide de la **[Phase spatiale](../../../../design/coordinate-systems.md#spatial-coordinate-systems)**, qui représente l’origine de l’utilisateur et la limite facultative de l’espace, configurées lors de la première exécution.</span><span class="sxs-lookup"><span data-stu-id="68de8-123">You reason about the user's floor using the **[spatial stage](../../../../design/coordinate-systems.md#spatial-coordinate-systems)**, which represents the user's defined floor-level origin and optional room boundary, set up during first run.</span></span>

<span data-ttu-id="68de8-124">Pour vous assurer que Unity fonctionne avec son système de coordonnées universel à l’étage, vous pouvez définir et tester qu’Unity utilise le type d’espace de suivi RoomScale :</span><span class="sxs-lookup"><span data-stu-id="68de8-124">To ensure that Unity is operating with its world coordinate system at floor-level, you can set and test that Unity is using the RoomScale tracking space type:</span></span>

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```

* <span data-ttu-id="68de8-125">Si SetTrackingSpaceType retourne la valeur true, Unity a correctement basculé son système de coordonnées universel pour suivre le [cadre de la phase de référence](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span><span class="sxs-lookup"><span data-stu-id="68de8-125">If SetTrackingSpaceType returns true, Unity has successfully switched its world coordinate system to track the [stage frame of reference](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span></span>
* <span data-ttu-id="68de8-126">Si SetTrackingSpaceType retourne la valeur false, Unity n’a pas pu basculer vers le cadre de la phase de référence, probablement parce que l’utilisateur n’a pas configuré d’étage dans son environnement.</span><span class="sxs-lookup"><span data-stu-id="68de8-126">If SetTrackingSpaceType returns false, Unity was unable to switch to the stage frame of reference, likely because the user has not set up a floor in their environment.</span></span> <span data-ttu-id="68de8-127">Bien qu’une valeur de retour false ne soit pas courante, elle peut se produire si l’étape est configurée dans une salle différente et que l’appareil est déplacé dans la salle actuelle sans que l’utilisateur ne configure une nouvelle étape.</span><span class="sxs-lookup"><span data-stu-id="68de8-127">While a false return value isn't common, it can happen if the stage is set up in a different room and the device is moved to the current room without the user setting up a new stage.</span></span>

<span data-ttu-id="68de8-128">Une fois que votre application a correctement défini le type d’espace de suivi RoomScale, le contenu placé sur le plan y = 0 s’affiche sur le plancher.</span><span class="sxs-lookup"><span data-stu-id="68de8-128">Once your app successfully sets the RoomScale tracking space type, content placed on the y=0 plane will appear on the floor.</span></span> <span data-ttu-id="68de8-129">L’origine à 0, 0 correspond à l’emplacement spécifique sur le plancher où l’utilisateur a pris la main pendant la configuration de la salle, avec-Z représentant la direction vers l’avant pendant la configuration.</span><span class="sxs-lookup"><span data-stu-id="68de8-129">The origin at 0, 0, 0 will be the specific place on the floor where the user stood during room setup, with -Z representing the forward direction they were facing during setup.</span></span>