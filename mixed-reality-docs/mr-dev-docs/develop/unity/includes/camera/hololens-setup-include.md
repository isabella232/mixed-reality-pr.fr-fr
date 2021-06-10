---
ms.openlocfilehash: 6e751f5376110ddc6ae92c75b4182fba8240a356
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748469"
---
# <a name="mrtk"></a>[<span data-ttu-id="f0de0-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="f0de0-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="f0de0-102">Suivez ce [didacticiel pas à pas](../../tutorials/mr-learning-base-01.md) pour ajouter et configurer automatiquement la boîte à outils de réalité mixte dans votre projet Unity.</span><span class="sxs-lookup"><span data-stu-id="f0de0-102">Follow this [step-by-step tutorial](../../tutorials/mr-learning-base-01.md) to add and automatically configure Mixed Reality Toolkit in your Unity project.</span></span> <span data-ttu-id="f0de0-103">Il est également possible de travailler directement avec la classe [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) à partir de MRTK pour Unity et de définir la mise à l' **échelle cible** sur le **monde**:</span><span class="sxs-lookup"><span data-stu-id="f0de0-103">It's also possible to work directly with the [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to **World**:</span></span>

![Fenêtre Paramètres MRTK](../../images/mrtk-target-scale.png)

<span data-ttu-id="f0de0-105">MRTK doit gérer automatiquement la position du PlaySpace et de l’appareil photo, mais il est préférable de vérifier :</span><span class="sxs-lookup"><span data-stu-id="f0de0-105">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![MRTK playspace](../../images/mrtk-playspace.png)

1. <span data-ttu-id="f0de0-107">Dans le volet **hiérarchie** , développez le gameobject **MixedRealityPlayspace** et recherchez l’objet enfant de l' **appareil photo principal** .</span><span class="sxs-lookup"><span data-stu-id="f0de0-107">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="f0de0-108">Dans le volet de l' **inspecteur** , recherchez le composant **transformer** et changez la **position** en **(X : 0, Y : 0, Z : 0)**</span><span class="sxs-lookup"><span data-stu-id="f0de0-108">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="f0de0-109">Kit de développement logiciel (SDK) XR</span><span class="sxs-lookup"><span data-stu-id="f0de0-109">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="f0de0-110">Définissez le mode d’origine du suivi sur [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span><span class="sxs-lookup"><span data-stu-id="f0de0-110">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="f0de0-111">Après avoir obtenu le sous-système, appelez [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span><span class="sxs-lookup"><span data-stu-id="f0de0-111">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Unbounded); // Recommendation for OpenXR
```

<span data-ttu-id="f0de0-112">Vous pouvez utiliser [ARSession](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) pour les applications HoloLens, ce qui fonctionne mieux avec les ancres et ARKit/ARCore.</span><span class="sxs-lookup"><span data-stu-id="f0de0-112">You can use [ARSession](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) for HoloLens applications, which works better with anchors and ARKit/ARCore.</span></span>

![Session AR dans la hiérarchie](../../images/xrsdk-arsession.png)

> [!IMPORTANT]
> <span data-ttu-id="f0de0-114">La session AR et les fonctionnalités associées nécessitent l’installation de la Fondation de base.</span><span class="sxs-lookup"><span data-stu-id="f0de0-114">AR Session and related features need AR Foundation installed.</span></span>

<span data-ttu-id="f0de0-115">Il est également possible d’appliquer les modifications de la caméra manuellement sans utiliser ARSession :</span><span class="sxs-lookup"><span data-stu-id="f0de0-115">It's also possible to apply the camera changes manually without using ARSession:</span></span>

1. <span data-ttu-id="f0de0-116">Sélectionner la **caméra principale** dans le volet de la **hiérarchie**</span><span class="sxs-lookup"><span data-stu-id="f0de0-116">Select **Main Camera** in the **Hierarchy** panel</span></span>
1. <span data-ttu-id="f0de0-117">Dans le volet de l' **inspecteur** , recherchez le composant **transformer** et changez la **position** en **(X : 0, Y : 0, Z : 0)**</span><span class="sxs-lookup"><span data-stu-id="f0de0-117">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

   <span data-ttu-id="f0de0-118">![Caméra dans le volet de l’inspecteur dans Unity](../../images/maincamera-350px.png)</span><span class="sxs-lookup"><span data-stu-id="f0de0-118">![Camera in the Inspector pane in Unity](../../images/maincamera-350px.png)</span></span>  
   <span data-ttu-id="f0de0-119">*Caméra dans le volet de l’inspecteur dans Unity*</span><span class="sxs-lookup"><span data-stu-id="f0de0-119">*Camera in the Inspector pane in Unity*</span></span>

1. <span data-ttu-id="f0de0-120">Ajouter un **TrackedPoseDriver** à l' **appareil photo principal**</span><span class="sxs-lookup"><span data-stu-id="f0de0-120">Add a **TrackedPoseDriver** to the **Main Camera**</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="f0de0-121">WSA hérité</span><span class="sxs-lookup"><span data-stu-id="f0de0-121">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="f0de0-122">Sélectionner la **caméra principale** dans le volet de la **hiérarchie**</span><span class="sxs-lookup"><span data-stu-id="f0de0-122">Select **Main Camera** in the **Hierarchy** panel</span></span>
1. <span data-ttu-id="f0de0-123">Dans le volet de l' **inspecteur** , recherchez le composant **transformer** et changez la **position** en **(X : 0, Y : 0, Z : 0)**</span><span class="sxs-lookup"><span data-stu-id="f0de0-123">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

   <span data-ttu-id="f0de0-124">![Caméra dans le volet de l’inspecteur dans Unity](../../images/maincamera-350px.png)</span><span class="sxs-lookup"><span data-stu-id="f0de0-124">![Camera in the Inspector pane in Unity](../../images/maincamera-350px.png)</span></span>  
   <span data-ttu-id="f0de0-125">*Caméra dans le volet de l’inspecteur dans Unity*</span><span class="sxs-lookup"><span data-stu-id="f0de0-125">*Camera in the Inspector pane in Unity*</span></span>

1. <span data-ttu-id="f0de0-126">Accéder à d' **autres paramètres** de la section paramètres du **lecteur Windows Store**</span><span class="sxs-lookup"><span data-stu-id="f0de0-126">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
1. <span data-ttu-id="f0de0-127">Choisissez **Windows Mixed realisation** comme périphérique, qui peut être listé comme **Windows holographique** dans les versions antérieures d’Unity</span><span class="sxs-lookup"><span data-stu-id="f0de0-127">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
1. <span data-ttu-id="f0de0-128">Sélectionner une **réalité virtuelle prise en charge**</span><span class="sxs-lookup"><span data-stu-id="f0de0-128">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="f0de0-129">Étant donné que l’objet Camera principal est automatiquement marqué comme caméra, Unity alimente tous les mouvements et les translations.</span><span class="sxs-lookup"><span data-stu-id="f0de0-129">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="f0de0-130">Ces paramètres doivent être appliqués à l’appareil photo dans chaque scène de votre application.</span><span class="sxs-lookup"><span data-stu-id="f0de0-130">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="f0de0-131">Par défaut, lorsque vous créez une nouvelle scène dans Unity, elle contient un GameObject d’appareil photo principal dans la hiérarchie qui comprend le composant d’appareil photo, mais peut ne pas avoir les paramètres correctement appliqués.</span><span class="sxs-lookup"><span data-stu-id="f0de0-131">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but may not have the settings properly applied.</span></span>