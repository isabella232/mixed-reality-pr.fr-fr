---
title: Fonctionnalités prises en charge par le plug-in OpenXR dans Unity
description: Découvrez les fonctionnalités prises en charge par OpenXR pour le développement de réalité mixte dans Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, réalité mixte, MRTK, boîte à outils de réalité mixte, réalité augmentée, réalité virtuelle, casques de réalité mixte, apprentissage, didacticiel, prise en main
ms.openlocfilehash: d65bab65bcb06f7ccba522461e04062458e7400c
ms.sourcegitcommit: aa29b68603721e909f08f352feed24c65d2e505e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98108842"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a><span data-ttu-id="cf3db-104">OpenXR en réalité mixte fonctionnalités prises en charge dans Unity</span><span class="sxs-lookup"><span data-stu-id="cf3db-104">Mixed Reality OpenXR supported features in Unity</span></span>

<span data-ttu-id="cf3db-105">Le package de **plug-in OpenXR de réalité mixte** est une extension du **plug-in OpenXR** d’Unity et prend en charge une suite de fonctionnalités pour les casques HoloLens 2 et Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="cf3db-105">The **Mixed Reality OpenXR Plugin** package is an extension of Unity's **OpenXR Plugin** and supports a suite of features for HoloLens 2 and Windows Mixed Reality headsets.</span></span> <span data-ttu-id="cf3db-106">Avant de continuer, vérifiez que vous avez installé **unity 2020,2** ou une version ultérieure, le **plug-in OpenXR version 0.1.2** ou ultérieure et votre projet Unity est [configuré pour OpenXR](openxr-getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="cf3db-106">Before continuing, make sure that you've installed **Unity 2020.2** or later, **OpenXR Plugin version 0.1.2** or later, and your Unity project is [configured for OpenXR](openxr-getting-started.md).</span></span>

## <a name="whats-supported"></a><span data-ttu-id="cf3db-107">Opérations prises en charge</span><span class="sxs-lookup"><span data-stu-id="cf3db-107">What's supported</span></span>

<span data-ttu-id="cf3db-108">Les fonctionnalités suivantes sont actuellement prises en charge :</span><span class="sxs-lookup"><span data-stu-id="cf3db-108">The following features are currently supported:</span></span>

* <span data-ttu-id="cf3db-109">Prend en charge les applications UWP pour HoloLens 2 et optimise le modèle d’application HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="cf3db-109">Supports UWP applications for HoloLens 2, and optimize for HoloLens 2 application model.</span></span>
* <span data-ttu-id="cf3db-110">Prend en charge les applications Win32 VR pour le casque Windows Mixed Reality avec les derniers profils de contrôleur et la communication à distance des applications holographiques.</span><span class="sxs-lookup"><span data-stu-id="cf3db-110">Supports Win32 VR applications for Windows Mixed Reality headset with latest controller profiles and holographic app remoting.</span></span>
* <span data-ttu-id="cf3db-111">Suivi de la mise à l’échelle mondiale utilisant les ancres et l’espace non limité.</span><span class="sxs-lookup"><span data-stu-id="cf3db-111">World scale tracking using Anchors and Unbounded space.</span></span>
* <span data-ttu-id="cf3db-112">[API de stockage d’ancrage pour rendre les ancres persistantes](#anchors-and-anchor-persistence) dans le stockage local HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="cf3db-112">[Anchor storage API to persist anchors](#anchors-and-anchor-persistence) to HoloLens 2 local storage.</span></span>
* <span data-ttu-id="cf3db-113">[Interactions entre le contrôleur de mouvement et la main](#motion-controller-and-hand-interactions), y compris le nouveau contrôleur de réverbération HP G2.</span><span class="sxs-lookup"><span data-stu-id="cf3db-113">[Motion controller and hand interactions](#motion-controller-and-hand-interactions), including the new HP Reverb G2 controller.</span></span>
* <span data-ttu-id="cf3db-114">Suivi articulé à l’aide de 26 jointures et d’entrées RADIUS jointes.</span><span class="sxs-lookup"><span data-stu-id="cf3db-114">Articulated hand tracking using 26 joints and joint radius inputs.</span></span>
* <span data-ttu-id="cf3db-115">Interaction de regard sur HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="cf3db-115">Eye gaze interaction on HoloLens 2.</span></span>
* <span data-ttu-id="cf3db-116">Recherche de l’appareil photo/vidéo (PV) sur HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="cf3db-116">Locating photo/video (PV) camera on HoloLens 2.</span></span>
* <span data-ttu-id="cf3db-117">Capture de la réalité mixte à l’aide d’un rendu de 3e œil via l’appareil photo PV.</span><span class="sxs-lookup"><span data-stu-id="cf3db-117">Mixed Reality Capture using 3rd eye rendering through PV camera.</span></span>
* <span data-ttu-id="cf3db-118">Prend en charge [la « lecture » dans HoloLens 2 avec l’application de communication à distance holographique](#holographic-remoting-in-unity-editor-play-mode), ce qui permet aux développeurs de déboguer les scripts sans les générer et les déployer sur l’appareil.</span><span class="sxs-lookup"><span data-stu-id="cf3db-118">Supports ["Play" to HoloLens 2 with the Holographic Remoting app](#holographic-remoting-in-unity-editor-play-mode), allowing developers to debug scripts without building and deploying to the device.</span></span>
* <span data-ttu-id="cf3db-119">Compatible avec MRTK Unity 2.5.3 et versions ultérieures via la [prise en charge des fournisseurs MRTK OpenXR](openxr-getting-started.md#using-mrtk-with-openxr-support).</span><span class="sxs-lookup"><span data-stu-id="cf3db-119">Compatible with MRTK Unity 2.5.3 and newer through [MRTK OpenXR provider support](openxr-getting-started.md#using-mrtk-with-openxr-support).</span></span>
* <span data-ttu-id="cf3db-120">Compatible avec Unity [ARFoundation 4,0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="cf3db-120">Compatible with Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) or later</span></span>

## <a name="holographic-remoting-in-unity-editor-play-mode"></a><span data-ttu-id="cf3db-121">Communication à distance holographique en mode de lecture de l’éditeur Unity</span><span class="sxs-lookup"><span data-stu-id="cf3db-121">Holographic Remoting in Unity Editor play mode</span></span>

<span data-ttu-id="cf3db-122">La création d’un projet Unity UWP dans Visual Studio Project et son empaquetage et son déploiement sur un appareil HoloLens 2 peuvent prendre un certain temps.</span><span class="sxs-lookup"><span data-stu-id="cf3db-122">Building a UWP Unity project in Visual Studio project and then packaging and deploying it to a HoloLens 2 device can take some time.</span></span> <span data-ttu-id="cf3db-123">Une solution consiste à activer la communication à distance de l’éditeur holographique, qui vous permet de déboguer votre script C# en mode « lecture » directement sur un appareil HoloLens 2 sur votre réseau.</span><span class="sxs-lookup"><span data-stu-id="cf3db-123">One solution is to enable the Holographic Editor Remoting, which lets you debug your C# script using “Play” mode directly to a HoloLens 2 device over your network.</span></span> <span data-ttu-id="cf3db-124">Ce scénario évite la surcharge liée à la création et au déploiement d’un package UWP sur un appareil distant.</span><span class="sxs-lookup"><span data-stu-id="cf3db-124">This scenario avoids the overhead of building and deploying a UWP package to remote device.</span></span>

1. <span data-ttu-id="cf3db-125">Tout d’abord, vous devez [installer l’application de lecteur de communication à distance holographique](https://www.microsoft.com/store/productId/9NBLGGH4SV40) à partir du Store sur votre HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="cf3db-125">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from Store on your HoloLens 2</span></span>
2. <span data-ttu-id="cf3db-126">Exécutez l’application de lecteur de communication à distance holographique sur HoloLens 2 et vous verrez le numéro de version et l’adresse IP à laquelle se connecter.</span><span class="sxs-lookup"><span data-stu-id="cf3db-126">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="cf3db-127">V 2.4 ou version ultérieure est nécessaire pour fonctionner avec le plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="cf3db-127">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![Capture d’écran du lecteur de communication à distance holographique s’exécutant dans HoloLens](images/openxr-features-img-01.png)

3. <span data-ttu-id="cf3db-129">Ouvrez les **paramètres du projet de modification >**, accédez à **gestion du plug-in XR**, puis cochez la case **Windows Mixed Reality Feature Set** :</span><span class="sxs-lookup"><span data-stu-id="cf3db-129">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box:</span></span>

    ![Capture d’écran du panneau Paramètres du projet ouvert dans l’éditeur Unity avec la gestion du plug-in XR mise en surbrillance](images/openxr-features-img-02.png)

4. <span data-ttu-id="cf3db-131">Développez la section **fonctionnalités** sous **OpenXR** et sélectionnez **Afficher tout** .</span><span class="sxs-lookup"><span data-stu-id="cf3db-131">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
5. <span data-ttu-id="cf3db-132">Cochez la case **accès distant de l’éditeur holographique** et entrez l’adresse IP obtenue à partir de l’application de communication à distance holographique :</span><span class="sxs-lookup"><span data-stu-id="cf3db-132">Check the **Holographic Editor Remoting** checkbox and input the IP address you get from the Holographic Remoting app:</span></span>

    ![Capture d’écran du panneau Paramètres du projet ouvert dans l’éditeur Unity avec les fonctionnalités mises en surbrillance](images/openxr-features-img-03.png)

<span data-ttu-id="cf3db-134">Vous pouvez maintenant cliquer sur le bouton « lecture » pour lire votre application Unity dans l’application de communication à distance holographique sur votre HoloLens.</span><span class="sxs-lookup"><span data-stu-id="cf3db-134">Now you can click the “Play” button to play your Unity app into the Holographic Remoting app on your HoloLens.</span></span> <span data-ttu-id="cf3db-135">Vous pouvez également [attacher Visual Studio à Unity](https://docs.microsoft.com/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) pour déboguer des scripts C# en mode lecture.</span><span class="sxs-lookup"><span data-stu-id="cf3db-135">You can also [attach Visual Studio to Unity](https://docs.microsoft.com/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) to debug C# scripts in the play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="cf3db-136">À partir de la version 0.1.0, le runtime de communication à distance holographique ne prend pas en charge les ancres, et les fonctionnalités ARAnchorManager ne fonctionnent pas via la communication à distance.</span><span class="sxs-lookup"><span data-stu-id="cf3db-136">As of version 0.1.0, the Holographic Remoting runtime doesn’t support Anchors, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="cf3db-137">Cette fonctionnalité est disponible dans les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="cf3db-137">This feature is coming in future releases.</span></span>

## <a name="anchors-and-anchor-persistence"></a><span data-ttu-id="cf3db-138">Ancres et persistance d’ancrage</span><span class="sxs-lookup"><span data-stu-id="cf3db-138">Anchors and Anchor Persistence</span></span>

<span data-ttu-id="cf3db-139">Le plug-in OpenXR de réalité mixte fournit des fonctionnalités d’ancre de base via une implémentation du **ARAnchorManager** ARFoundation d’Unity.</span><span class="sxs-lookup"><span data-stu-id="cf3db-139">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="cf3db-140">Pour en savoir plus sur les principes de base de **ARAnchor** dans ARFoundation, consultez le [Manuel ARFoundation du gestionnaire d’ancrage AR](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span><span class="sxs-lookup"><span data-stu-id="cf3db-140">To learn the basics on **ARAnchor** s in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> <span data-ttu-id="cf3db-141">À partir de la version 0.1.0, ce plug-in prend en charge toutes les fonctionnalités ARAnchorManager, à l’exception de la création d’ancres attachées à un plan, qui est disponible dans une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="cf3db-141">As of version 0.1.0, this plugin supports all ARAnchorManager functionality except creating anchors attached to a plane, which is coming in a future release.</span></span>

### <a name="anchor-persistence-and-the-xranchorstore"></a><span data-ttu-id="cf3db-142">Persistance d’ancrage et XRAnchorStore</span><span class="sxs-lookup"><span data-stu-id="cf3db-142">Anchor Persistence and the XRAnchorStore</span></span>

<span data-ttu-id="cf3db-143">Une API supplémentaire appelée **XRAnchorStore** permet aux ancres d’être rendues persistantes entre les sessions.</span><span class="sxs-lookup"><span data-stu-id="cf3db-143">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="cf3db-144">Le XRAnchorStore est une représentation des ancres enregistrées sur votre appareil.</span><span class="sxs-lookup"><span data-stu-id="cf3db-144">The XRAnchorStore is a representation of the saved anchors on your device.</span></span> <span data-ttu-id="cf3db-145">Les ancres peuvent être rendues persistantes à partir de **ARAnchors** dans la scène Unity, chargées à partir du stockage dans un nouveau **ARAnchors**, ou supprimées du stockage.</span><span class="sxs-lookup"><span data-stu-id="cf3db-145">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="cf3db-146">Ces ancres doivent être enregistrées et chargées sur le même appareil.</span><span class="sxs-lookup"><span data-stu-id="cf3db-146">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="cf3db-147">Le stockage d’ancrage entre appareils sera pris en charge via les ancres spatiales Azure dans une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="cf3db-147">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

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

<span data-ttu-id="cf3db-148">Pour charger XRAnchorStore, le plug-in fournit une méthode d’extension sur XRAnchorSubsystem, le sous-système d’un ARAnchorManager :</span><span class="sxs-lookup"><span data-stu-id="cf3db-148">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="cf3db-149">Pour utiliser cette méthode d’extension, accédez à celle-ci à partir du sous-système d’un ARAnchorManager, comme suit :</span><span class="sxs-lookup"><span data-stu-id="cf3db-149">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="cf3db-150">Pour voir un exemple complet d’ancres persistantes/non persistantes, consultez l’exemple d’ancres-> ancrages GameObject et AnchorsSample.cs script dans l' [exemple de scène de plug-in de réalité mixte OpenXR](openxr-getting-started.md#hololens-2-samples):</span><span class="sxs-lookup"><span data-stu-id="cf3db-150">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](openxr-getting-started.md#hololens-2-samples):</span></span>

![Capture d’écran de l’ouverture du panneau de la hiérarchie dans l’éditeur Unity avec l’exemple ancres mis en surbrillance](images/openxr-features-img-04.png)

![Capture d’écran du panneau Inspecteur ouvert dans l’éditeur Unity avec l’exemple de script Anchors mis en surbrillance](images/openxr-features-img-05.png)

## <a name="motion-controller-and-hand-interactions"></a><span data-ttu-id="cf3db-153">Interactions entre le contrôleur de mouvement et la main</span><span class="sxs-lookup"><span data-stu-id="cf3db-153">Motion controller and hand interactions</span></span>

<span data-ttu-id="cf3db-154">Pour connaître les principes de base des interactions de réalité mixte dans Unity, visitez le [Manuel Unity pour l’entrée Unity XR](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span><span class="sxs-lookup"><span data-stu-id="cf3db-154">To learn the basics about mixed reality interactions in Unity, visit the [Unity Manual for Unity XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span></span> <span data-ttu-id="cf3db-155">Cette documentation Unity couvre les mappages entre les entrées spécifiques au contrôleur et les **InputFeatureUsages** plus généralisables, la manière dont les entrées XR disponibles peuvent être identifiées et catégorisées, comment lire les données à partir de ces entrées, et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="cf3db-155">This Unity documentation covers the mappings from controller-specific inputs to more generalizable **InputFeatureUsage** s, how available XR inputs can be identified and categorized, how to read data from these inputs, and more.</span></span>

<span data-ttu-id="cf3db-156">Le plug-in OpenXR de réalité mixte fournit des profils d’interaction d’entrée supplémentaires, mappés à des **InputFeatureUsage** standard, comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="cf3db-156">The Mixed Reality OpenXR Plugin provides additional input interaction profiles, mapped to standard **InputFeatureUsage** s as detailed below:</span></span>

| <span data-ttu-id="cf3db-157">InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="cf3db-157">InputFeatureUsage</span></span> | <span data-ttu-id="cf3db-158">Contrôleur de réverbération HP G2 (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="cf3db-158">HP Reverb G2 Controller (OpenXR)</span></span> | <span data-ttu-id="cf3db-159">Manuel HoloLens (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="cf3db-159">HoloLens Hand (OpenXR)</span></span> |
| ---- | ---- | ---- |
| <span data-ttu-id="cf3db-160">primary2DAxis</span><span class="sxs-lookup"><span data-stu-id="cf3db-160">primary2DAxis</span></span> | <span data-ttu-id="cf3db-161">Croix</span><span class="sxs-lookup"><span data-stu-id="cf3db-161">Joystick</span></span> | |
| <span data-ttu-id="cf3db-162">primary2DAxisClick</span><span class="sxs-lookup"><span data-stu-id="cf3db-162">primary2DAxisClick</span></span> | <span data-ttu-id="cf3db-163">Manette de jeu-clic</span><span class="sxs-lookup"><span data-stu-id="cf3db-163">Joystick - Click</span></span> | |
| <span data-ttu-id="cf3db-164">déclencheur</span><span class="sxs-lookup"><span data-stu-id="cf3db-164">trigger</span></span> | <span data-ttu-id="cf3db-165">Déclencheur</span><span class="sxs-lookup"><span data-stu-id="cf3db-165">Trigger</span></span>  | |
| <span data-ttu-id="cf3db-166">délicat</span><span class="sxs-lookup"><span data-stu-id="cf3db-166">grip</span></span> | <span data-ttu-id="cf3db-167">Délicat</span><span class="sxs-lookup"><span data-stu-id="cf3db-167">Grip</span></span> | <span data-ttu-id="cf3db-168">Appuyez ou appuyez sur l’air</span><span class="sxs-lookup"><span data-stu-id="cf3db-168">Air tap or squeeze</span></span> |
| <span data-ttu-id="cf3db-169">primaryButton</span><span class="sxs-lookup"><span data-stu-id="cf3db-169">primaryButton</span></span> | <span data-ttu-id="cf3db-170">[X/A]-Appuyez sur</span><span class="sxs-lookup"><span data-stu-id="cf3db-170">[X/A] - Press</span></span> | <span data-ttu-id="cf3db-171">Clic aérien</span><span class="sxs-lookup"><span data-stu-id="cf3db-171">Air tap</span></span> |
| <span data-ttu-id="cf3db-172">secondaryButton</span><span class="sxs-lookup"><span data-stu-id="cf3db-172">secondaryButton</span></span> | <span data-ttu-id="cf3db-173">[Y/B]-Appuyez sur</span><span class="sxs-lookup"><span data-stu-id="cf3db-173">[Y/B] - Press</span></span> | |
| <span data-ttu-id="cf3db-174">gripButton</span><span class="sxs-lookup"><span data-stu-id="cf3db-174">gripButton</span></span> | <span data-ttu-id="cf3db-175">Appuyez sur la poignée</span><span class="sxs-lookup"><span data-stu-id="cf3db-175">Grip - Press</span></span> | |
| <span data-ttu-id="cf3db-176">triggerButton</span><span class="sxs-lookup"><span data-stu-id="cf3db-176">triggerButton</span></span> | <span data-ttu-id="cf3db-177">Déclencher-appuyer sur</span><span class="sxs-lookup"><span data-stu-id="cf3db-177">Trigger - Press</span></span> | |
| <span data-ttu-id="cf3db-178">menuButton</span><span class="sxs-lookup"><span data-stu-id="cf3db-178">menuButton</span></span> | <span data-ttu-id="cf3db-179">Menu</span><span class="sxs-lookup"><span data-stu-id="cf3db-179">Menu</span></span> | |

### <a name="aim-and-grip-poses"></a><span data-ttu-id="cf3db-180">Poses de la AIM et de la poignée</span><span class="sxs-lookup"><span data-stu-id="cf3db-180">Aim and Grip Poses</span></span>

<span data-ttu-id="cf3db-181">Vous avez accès à deux ensembles de poses via des interactions d’entrée OpenXR :</span><span class="sxs-lookup"><span data-stu-id="cf3db-181">You have access to two sets of poses through OpenXR input interactions:</span></span>

* <span data-ttu-id="cf3db-182">La poignée pose le rendu des objets de la main</span><span class="sxs-lookup"><span data-stu-id="cf3db-182">The grip poses for rendering objects in the hand</span></span>
* <span data-ttu-id="cf3db-183">L’objectif est de pointer dans le monde.</span><span class="sxs-lookup"><span data-stu-id="cf3db-183">The aim poses for pointing into the world.</span></span>

<span data-ttu-id="cf3db-184">Pour plus d’informations sur cette conception et les différences entre les deux poses, consultez la [spécification OpenXR-sous-chemins d’entrée](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span><span class="sxs-lookup"><span data-stu-id="cf3db-184">More information on this design and the differences between the two poses can be found in the [OpenXR Specification - Input Subpaths](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span></span>

<span data-ttu-id="cf3db-185">Les poses fournies par les InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity** et **DeviceAngularVelocity** représentent toutes la pose de la **poignée** OpenXR.</span><span class="sxs-lookup"><span data-stu-id="cf3db-185">Poses supplied by the InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity**, and **DeviceAngularVelocity** all represent the OpenXR **grip** pose.</span></span> <span data-ttu-id="cf3db-186">Les InputFeatureUsages relatives aux poses de poignée sont définis dans les [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)d’Unity.</span><span class="sxs-lookup"><span data-stu-id="cf3db-186">InputFeatureUsages related to grip poses are defined in Unity’s [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html).</span></span>

<span data-ttu-id="cf3db-187">Les poses fournies par les InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity** et **PointerAngularVelocity** représentent toutes **la pose du** OpenXR.</span><span class="sxs-lookup"><span data-stu-id="cf3db-187">Poses supplied by the InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity**, and **PointerAngularVelocity** all represent the OpenXR **aim** pose.</span></span> <span data-ttu-id="cf3db-188">Ces InputFeatureUsages ne sont pas définis dans les fichiers C# inclus. vous devez donc définir votre propre InputFeatureUsages comme suit :</span><span class="sxs-lookup"><span data-stu-id="cf3db-188">These InputFeatureUsages aren't defined in any included C# files, so you'll need to define your own InputFeatureUsages as follows:</span></span>

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a><span data-ttu-id="cf3db-189">Haptique</span><span class="sxs-lookup"><span data-stu-id="cf3db-189">Haptics</span></span>

<span data-ttu-id="cf3db-190">Pour plus d’informations sur l’utilisation des haptique dans le système d’entrée XR Unity, consultez le [Manuel Unity pour Unity XR Input-haptiques](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span><span class="sxs-lookup"><span data-stu-id="cf3db-190">For information on using haptics in Unity’s XR Input system, documentation can be found at the [Unity Manual for Unity XR Input - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span></span>

## <a name="whats-coming-soon"></a><span data-ttu-id="cf3db-191">Bientôt disponible</span><span class="sxs-lookup"><span data-stu-id="cf3db-191">What's coming soon</span></span>

<span data-ttu-id="cf3db-192">Les problèmes suivants et les fonctionnalités manquantes sont connus avec le plug-in OpenXR de réalité mixte **version 0.1.0**.</span><span class="sxs-lookup"><span data-stu-id="cf3db-192">The following issues and missing features are known with Mixed Reality OpenXR plugin **version 0.1.0**.</span></span> <span data-ttu-id="cf3db-193">Nous travaillons sur ces versions et publierons des correctifs et de nouvelles fonctionnalités dans les versions à venir.</span><span class="sxs-lookup"><span data-stu-id="cf3db-193">We're working on these and will release fixes and new features in upcoming releases.</span></span>

* <span data-ttu-id="cf3db-194">**ARPlaneSubsystem** n’est pas encore pris en charge.</span><span class="sxs-lookup"><span data-stu-id="cf3db-194">**ARPlaneSubsystem** is not supported yet.</span></span> <span data-ttu-id="cf3db-195">**ARPlaneManager**, **ARRAYCASTMANAGER** et l’API associée comme **ARAnchorManager. AttachAnchor** ne sont pas non plus prises en charge sur HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="cf3db-195">**ARPlaneManager**, **ARRaycastManager**, and related API like **ARAnchorManager.AttachAnchor** are also not supported on HoloLens 2.</span></span>
* <span data-ttu-id="cf3db-196">Le **point d’ancrage** n’est pas encore pris en charge par la communication à distance holographique, mais dans un avenir proche.</span><span class="sxs-lookup"><span data-stu-id="cf3db-196">**Anchor** isn't supported by Holographic Remoting yet, but it's coming in the near future.</span></span>
* <span data-ttu-id="cf3db-197">Le suivi du maillage de la **main** , les **codes QR** et les **XRMeshSubsystem** ne sont pas encore pris en charge.</span><span class="sxs-lookup"><span data-stu-id="cf3db-197">**Hand Mesh** tracking, **QR Codes**, and **XRMeshSubsystem** aren't supported yet.</span></span>
* <span data-ttu-id="cf3db-198">La prise en charge des **ancres spatiales Azure** est disponible dans une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="cf3db-198">**Azure Spatial Anchors** support is coming in a future release.</span></span>
* <span data-ttu-id="cf3db-199">**ARM64** est la seule plateforme prise en charge pour les applications HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="cf3db-199">**ARM64** is the only supported platform for HoloLens 2 apps.</span></span> <span data-ttu-id="cf3db-200">La plateforme **ARM** est disponible dans une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="cf3db-200">The **ARM** platform is coming in a future release.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="cf3db-201">Résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="cf3db-201">Troubleshooting</span></span>

<span data-ttu-id="cf3db-202">Lorsque vous suspendez et reprenez une application Unity sur HoloLens 2, l’application ne peut pas reprendre correctement, ce qui a pour conséquence 4 points de rotation dans la vue HoloLens.</span><span class="sxs-lookup"><span data-stu-id="cf3db-202">When you suspend and resume a Unity app on HoloLens 2, the app can't correctly resume, which leads to 4 spinning dots in the HoloLens view.</span></span>
* <span data-ttu-id="cf3db-203">Définir le **mode d’envoi de profondeur** sur **aucun** dans les paramètres du projet OpenXR comme solution de contournement</span><span class="sxs-lookup"><span data-stu-id="cf3db-203">Set **Depth submission Mode** to **None** in the OpenXR project settings as a workaround</span></span>
