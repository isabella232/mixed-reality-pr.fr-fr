---
title: Codes QR dans Unreal
description: Guide pour utiliser les codes QR dans Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, réalité mixte, développement, fonctionnalités, documentation, guides, hologrammes, codes qr
ms.openlocfilehash: 0f0507e2f726830cef27c190083363b3607379ee
ms.sourcegitcommit: 8e91ff47ef70e80a41137f80aa1093e711d27bf7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91957819"
---
# <a name="qr-codes-in-unreal"></a><span data-ttu-id="fac4e-104">Codes QR dans Unreal</span><span class="sxs-lookup"><span data-stu-id="fac4e-104">QR codes in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="fac4e-105">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="fac4e-105">Overview</span></span>

<span data-ttu-id="fac4e-106">HoloLens 2 peut voir les codes QR dans l’espace universel à travers la webcam, qui les affiche sous forme d’hologrammes en utilisant un système de coordonnées à la position réelle de chaque code.</span><span class="sxs-lookup"><span data-stu-id="fac4e-106">The HoloLens 2 can see QR codes in world space using the webcam, which renders them as holograms using a coordinate system at each code's real-world position.</span></span>  <span data-ttu-id="fac4e-107">En plus des codes QR uniques, HoloLens 2 peut aussi afficher des hologrammes sur plusieurs appareils à la même position pour créer une expérience partagée.</span><span class="sxs-lookup"><span data-stu-id="fac4e-107">In addition to single QR codes, HoloLens 2 can also render holograms in the same location on multiple devices to create a shared experience.</span></span> <span data-ttu-id="fac4e-108">Veillez à suivre les bonnes pratiques pour ajouter les codes QR à vos applications :</span><span class="sxs-lookup"><span data-stu-id="fac4e-108">Make sure you're following the best practices for adding QR codes to your applications:</span></span>

- <span data-ttu-id="fac4e-109">Zones calmes</span><span class="sxs-lookup"><span data-stu-id="fac4e-109">Quiet zones</span></span>
- <span data-ttu-id="fac4e-110">Éclairage et toile de fond</span><span class="sxs-lookup"><span data-stu-id="fac4e-110">Lighting and backdrop</span></span>
- <span data-ttu-id="fac4e-111">Taille, distance et position angulaire</span><span class="sxs-lookup"><span data-stu-id="fac4e-111">Size, distance, and angular position</span></span>

<span data-ttu-id="fac4e-112">Au moment de placer les codes QR dans votre application, portez une attention particulière aux [considérations liées à l’environnement](../../environment-considerations-for-hololens.md).</span><span class="sxs-lookup"><span data-stu-id="fac4e-112">Pay special attention to the [environment considerations](../../environment-considerations-for-hololens.md) when QR codes are being placed in your app.</span></span> <span data-ttu-id="fac4e-113">Vous trouverez des informations complémentaires sur chacun de ces sujets ainsi que des instructions sur la façon de télécharger le package NuGet nécessaire dans le document [Suivi des codes QR](../platform-capabilities-and-apis/qr-code-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="fac4e-113">You can find more information on each of these topics and instructions on how to download the required NuGet package in the main [QR code tracking](../platform-capabilities-and-apis/qr-code-tracking.md) document.</span></span>

## <a name="enabling-qr-detection"></a><span data-ttu-id="fac4e-114">Activation de la détection QR</span><span class="sxs-lookup"><span data-stu-id="fac4e-114">Enabling QR detection</span></span>
<span data-ttu-id="fac4e-115">Étant donné que HoloLens 2 doit utiliser la webcam pour voir les codes QR, vous devez l’activer dans les paramètres du projet :</span><span class="sxs-lookup"><span data-stu-id="fac4e-115">Since the HoloLens 2 needs to use the webcam to see QR codes, you'll need to enable it in the project settings:</span></span>
- <span data-ttu-id="fac4e-116">Ouvrez **Edit > Project Settings**, accédez à la section **Platforms**, puis cliquez sur **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="fac4e-116">Open **Edit > Project Settings**, scroll to the **Platforms** section and click **HoloLens**.</span></span>
    + <span data-ttu-id="fac4e-117">Développez la section **Capabilities** et cochez **Webcam**.</span><span class="sxs-lookup"><span data-stu-id="fac4e-117">Expand the **Capabilities** section and check **Webcam**.</span></span>  

<span data-ttu-id="fac4e-118">Vous devez aussi opter pour le suivi des codes QR en [ajoutant une ressource ARSessionConfig](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span><span class="sxs-lookup"><span data-stu-id="fac4e-118">You'll also need to opt into QR code tracking by [adding an ARSessionConfig asset](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>

<span data-ttu-id="fac4e-119">Juste avant l’utilisation, vous devez activer manuellement le suivi en appelant `UHoloLensARFunctionLibrary::StartCameraCapture()`.</span><span class="sxs-lookup"><span data-stu-id="fac4e-119">Right before the usage, you should manually enable the tracking by calling `UHoloLensARFunctionLibrary::StartCameraCapture()`.</span></span> <span data-ttu-id="fac4e-120">Après avoir mis fin au suivi de code QR, vous devez le désactiver avec `UHoloLensARFunctionLibrary::StopCameraCapture()` pour enregistrer les ressources de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="fac4e-120">After ending the QR code tracking, you should disable it by `UHoloLensARFunctionLibrary::StopCameraCapture()` to save the device resources.</span></span>

## <a name="setting-up-a-tracked-image"></a><span data-ttu-id="fac4e-121">Configuration d’une image suivie</span><span class="sxs-lookup"><span data-stu-id="fac4e-121">Setting up a tracked image</span></span>

<span data-ttu-id="fac4e-122">Les codes QR sont exposés sous forme d’image suivie par le biais du système de géométrie suivie de réalité augmentée d’Unreal.</span><span class="sxs-lookup"><span data-stu-id="fac4e-122">QR codes are surfaced through Unreal’s AR tracked geometry system as a tracked image.</span></span> <span data-ttu-id="fac4e-123">Pour que cela fonctionne, vous devez :</span><span class="sxs-lookup"><span data-stu-id="fac4e-123">To get this working, you'll need to:</span></span>
1. <span data-ttu-id="fac4e-124">Créer un blueprint et ajouter un composant **ARTrackableNotify**.</span><span class="sxs-lookup"><span data-stu-id="fac4e-124">Create a Blueprint and add an **ARTrackableNotify** component.</span></span>

![Composant ARTrackableNotify QR](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="fac4e-126">Sélectionnez **ARTrackableNotify** et développez la section **Events** dans le panneau **Details**.</span><span class="sxs-lookup"><span data-stu-id="fac4e-126">Select **ARTrackableNotify** and expand the **Events** section in the **Details** panel.</span></span>

![Événements QR](images/unreal-spatialmapping-events.PNG)

3. <span data-ttu-id="fac4e-128">Cliquez sur **+** à côté de **On Add Tracked Geometry** pour ajouter le nœud au graphique d’événements.</span><span class="sxs-lookup"><span data-stu-id="fac4e-128">Click **+** next to **On Add Tracked Geometry** to add the node to the Event Graph.</span></span>
    - <span data-ttu-id="fac4e-129">Vous trouverez la liste complète des événements dans l’API du composant [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).</span><span class="sxs-lookup"><span data-stu-id="fac4e-129">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span>

![Ajouter un nœud à On Add Tracked Geometry](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-image"></a><span data-ttu-id="fac4e-131">Utilisation d’une image suivie</span><span class="sxs-lookup"><span data-stu-id="fac4e-131">Using a tracked image</span></span>
<span data-ttu-id="fac4e-132">Le graphique d’événements dans l’image suivante présente l’événement **OnUpdateTrackedImage** qui est utilisé pour afficher un point au centre d’un code QR et imprimer ses données.</span><span class="sxs-lookup"><span data-stu-id="fac4e-132">The Event Graph in the following image shows the **OnUpdateTrackedImage** event being used to render a point in the center of a QR code and print out its data.</span></span>

![Exemple d’affichage QR](images/unreal-qr-render.PNG)

<span data-ttu-id="fac4e-134">Voici ce qui se passe :</span><span class="sxs-lookup"><span data-stu-id="fac4e-134">Here's what's going on:</span></span>
1. <span data-ttu-id="fac4e-135">Tout d’abord, l’image suivie est castée en **ARTrackedQRCode** pour vérifier que l’image mise à jour actuelle est un code QR.</span><span class="sxs-lookup"><span data-stu-id="fac4e-135">First, the tracked image is cast to an **ARTrackedQRCode** to check that the current updated image is a QR code.</span></span>  
2. <span data-ttu-id="fac4e-136">Les données encodées sont récupérées à partir de la variable **QRCode**.</span><span class="sxs-lookup"><span data-stu-id="fac4e-136">The encoded data is retrieved from the **QRCode** variable.</span></span> <span data-ttu-id="fac4e-137">Vous pouvez obtenir l’angle supérieur gauche du code QR à partir de l’emplacement de **GetLocalToWorldTransform** et les dimensions avec **GetEstimateSize**.</span><span class="sxs-lookup"><span data-stu-id="fac4e-137">You can get the top-left of the QR code from the location of **GetLocalToWorldTransform** and the dimensions with **GetEstimateSize**.</span></span>

<span data-ttu-id="fac4e-138">Vous pouvez aussi [obtenir le système de coordonnées pour un code QR](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) dans le code.</span><span class="sxs-lookup"><span data-stu-id="fac4e-138">You can also [get the coordinate system for a QR code](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) in code.</span></span>

## <a name="finding-the-unique-id"></a><span data-ttu-id="fac4e-139">Recherche de l’ID unique</span><span class="sxs-lookup"><span data-stu-id="fac4e-139">Finding the unique ID</span></span>
<span data-ttu-id="fac4e-140">À chaque code QR correspond un ID guid unique, que vous pouvez trouver comme ceci :</span><span class="sxs-lookup"><span data-stu-id="fac4e-140">Every QR code has a unique guid ID, which you can find by:</span></span>
- <span data-ttu-id="fac4e-141">Glissez-déposez le repère **As ARTracked QRCode** et effectuez une recherche sur l’ID unique (**Unique ID**).</span><span class="sxs-lookup"><span data-stu-id="fac4e-141">Dragging and dropping the **As ARTracked QRCode**  pin and searching for **Get Unique ID**.</span></span>

![GUID QR](images/unreal-qr-guid.PNG)

<span data-ttu-id="fac4e-143">Il se passe beaucoup de choses en coulisse avec les codes QR ; ce n’est donc pas terminé.</span><span class="sxs-lookup"><span data-stu-id="fac4e-143">There's a lot going on behind the scenes with QR codes, so this isn't the end of the road.</span></span> <span data-ttu-id="fac4e-144">N’hésitez pas à consulter les liens ci-dessous pour en savoir plus sur la mécanique interne.</span><span class="sxs-lookup"><span data-stu-id="fac4e-144">Be sure to check out the following links for more details on what's under the hood.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="fac4e-145">Point de contrôle de développement suivant</span><span class="sxs-lookup"><span data-stu-id="fac4e-145">Next Development Checkpoint</span></span>

<span data-ttu-id="fac4e-146">Si vous suivez le parcours des points de contrôle de développement Unreal que nous avons mis en place, vous explorez actuellement les API et fonctionnalités de la plateforme Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="fac4e-146">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="fac4e-147">À partir de là, vous pouvez passer à la rubrique suivante :</span><span class="sxs-lookup"><span data-stu-id="fac4e-147">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fac4e-148">WinRT</span><span class="sxs-lookup"><span data-stu-id="fac4e-148">WinRT</span></span>](unreal-winRT.md)

<span data-ttu-id="fac4e-149">Ou accéder directement au déploiement de votre application sur un appareil ou un émulateur :</span><span class="sxs-lookup"><span data-stu-id="fac4e-149">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fac4e-150">Déploiement sur un appareil</span><span class="sxs-lookup"><span data-stu-id="fac4e-150">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="fac4e-151">Vous pouvez revenir aux [points de contrôle de développement Unreal](unreal-development-overview.md#3-platform-capabilities-and-apis) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="fac4e-151">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="fac4e-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fac4e-152">See also</span></span>
* [<span data-ttu-id="fac4e-153">Mappage spatial</span><span class="sxs-lookup"><span data-stu-id="fac4e-153">Spatial mapping</span></span>](../../design/spatial-mapping.md)
* [<span data-ttu-id="fac4e-154">Hologrammes</span><span class="sxs-lookup"><span data-stu-id="fac4e-154">Holograms</span></span>](../../discover/hologram.md)
* [<span data-ttu-id="fac4e-155">Systèmes de coordonnées</span><span class="sxs-lookup"><span data-stu-id="fac4e-155">Coordinate systems</span></span>](../../design/coordinate-systems.md)
