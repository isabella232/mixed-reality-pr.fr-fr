---
title: Codes QR dans Unreal
description: Découvrez comment configurer, utiliser et faire le suivi des codes QR dans des applications de réalité mixte Unreal.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, réalité mixte, développement, fonctionnalités, documentation, guides, hologrammes, qr codes, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle
ms.openlocfilehash: d9f23bacf31b310da6d49e74de2153b50e642c7d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "98582664"
---
# <a name="qr-codes-in-unreal"></a><span data-ttu-id="ad114-104">Codes QR dans Unreal</span><span class="sxs-lookup"><span data-stu-id="ad114-104">QR codes in Unreal</span></span>

<span data-ttu-id="ad114-105">HoloLens 2 peut voir les codes QR dans l’espace universel à travers la webcam, qui les rend sous forme d’hologrammes à la position réelle de chaque code.</span><span class="sxs-lookup"><span data-stu-id="ad114-105">The HoloLens 2 can see QR codes in world space using the webcam, which renders them as holograms at each code's real-world position.</span></span> <span data-ttu-id="ad114-106">HoloLens 2 peut aussi rendre des hologrammes sur plusieurs appareils à la même position pour créer une expérience partagée.</span><span class="sxs-lookup"><span data-stu-id="ad114-106">HoloLens 2 can also render holograms in the same location on multiple devices to create a shared experience.</span></span> <span data-ttu-id="ad114-107">Veillez à suivre les bonnes pratiques pour ajouter les codes QR à vos applications :</span><span class="sxs-lookup"><span data-stu-id="ad114-107">Make sure you're following the best practices for adding QR codes to your applications:</span></span>

- <span data-ttu-id="ad114-108">Zones calmes</span><span class="sxs-lookup"><span data-stu-id="ad114-108">Quiet zones</span></span>
- <span data-ttu-id="ad114-109">Éclairage et toile de fond</span><span class="sxs-lookup"><span data-stu-id="ad114-109">Lighting and backdrop</span></span>
- <span data-ttu-id="ad114-110">Taille, distance et position angulaire</span><span class="sxs-lookup"><span data-stu-id="ad114-110">Size, distance, and angular position</span></span>

<span data-ttu-id="ad114-111">Au moment de placer les codes QR dans votre application, portez une attention particulière aux [considérations liées à l’environnement](/hololens/hololens-environment-considerations).</span><span class="sxs-lookup"><span data-stu-id="ad114-111">Pay special attention to the [environment considerations](/hololens/hololens-environment-considerations) when QR codes are being placed in your app.</span></span> <span data-ttu-id="ad114-112">Vous trouverez des informations complémentaires sur chacun de ces sujets ainsi que des instructions sur la façon de télécharger le package NuGet nécessaire dans le document [Suivi des codes QR](../platform-capabilities-and-apis/qr-code-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="ad114-112">You can find more information on each of these topics and instructions on how to download the required NuGet package in the main [QR code tracking](../platform-capabilities-and-apis/qr-code-tracking.md) document.</span></span>

> [!CAUTION]
> <span data-ttu-id="ad114-113">Les codes QR sont les seuls types d’images qui peuvent être suivies de façon native par HoloLens ; le module intégré **UARTrackedImage** module n’est pas pris en charge sur HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ad114-113">QR codes are the only type of images that can be tracked by HoloLens out of the box - Unreal's **UARTrackedImage** module isn't supported on HoloLens.</span></span> <span data-ttu-id="ad114-114">Si vous avez besoin de suivre des images personnalisées, vous pouvez accéder à la [webcam](unreal-hololens-camera.md) de l’appareil et traiter les images en utilisant une bibliothèque de reconnaissance d’images de tiers.</span><span class="sxs-lookup"><span data-stu-id="ad114-114">If you need to track custom images, you can access the device's [webcam](unreal-hololens-camera.md) and process images using a third party image recognition library.</span></span> 

## <a name="enabling-qr-detection"></a><span data-ttu-id="ad114-115">Activation de la détection QR</span><span class="sxs-lookup"><span data-stu-id="ad114-115">Enabling QR detection</span></span>

<span data-ttu-id="ad114-116">Étant donné que HoloLens 2 doit utiliser la webcam pour voir les codes QR, vous devez l’activer dans les paramètres du projet :</span><span class="sxs-lookup"><span data-stu-id="ad114-116">Since the HoloLens 2 needs to use the webcam to see QR codes, you'll need to enable it in the project settings:</span></span>
- <span data-ttu-id="ad114-117">Ouvrez **Edit > Project Settings**, accédez à la section **Platforms**, puis sélectionnez **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="ad114-117">Open **Edit > Project Settings**, scroll to the **Platforms** section, and select **HoloLens**.</span></span>
    + <span data-ttu-id="ad114-118">Développez la section **Capabilities** et cochez **Webcam**.</span><span class="sxs-lookup"><span data-stu-id="ad114-118">Expand the **Capabilities** section and check **Webcam**.</span></span>  
- <span data-ttu-id="ad114-119">Vous devez aussi opter pour le suivi des codes QR en [ajoutant une ressource ARSessionConfig](/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span><span class="sxs-lookup"><span data-stu-id="ad114-119">You'll also need to opt into QR code tracking by [adding an ARSessionConfig asset](/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>

[!INCLUDE[](includes/tabs-qr-codes-1.md)]

## <a name="setting-up-a-tracked-qr-code"></a><span data-ttu-id="ad114-120">Configuration d’un code QR suivi</span><span class="sxs-lookup"><span data-stu-id="ad114-120">Setting up a tracked QR code</span></span>

<span data-ttu-id="ad114-121">Les codes QR sont exposés sous forme d’image suivie par le biais du système de géométrie suivie de réalité augmentée d’Unreal.</span><span class="sxs-lookup"><span data-stu-id="ad114-121">QR codes are surfaced through Unreal’s AR tracked geometry system as a tracked image.</span></span> <span data-ttu-id="ad114-122">Pour que cela fonctionne, vous devez :</span><span class="sxs-lookup"><span data-stu-id="ad114-122">To get this working, you'll need to:</span></span>
1. <span data-ttu-id="ad114-123">Créer un blueprint d’acteur et ajouter un composant **ARTrackableNotify** :</span><span class="sxs-lookup"><span data-stu-id="ad114-123">Create an Actor Blueprint and add an **ARTrackableNotify** component:</span></span>

![Composant ARTrackableNotify QR](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="ad114-125">Sélectionnez **ARTrackableNotify** et développez la section **Events** dans le panneau **Details** :</span><span class="sxs-lookup"><span data-stu-id="ad114-125">Select **ARTrackableNotify** and expand the **Events** section in the **Details** panel:</span></span>

![Événements QR](images/unreal-spatialmapping-events.PNG)

3. <span data-ttu-id="ad114-127">Cliquez sur **+** à côté de **On Add Tracked Geometry** pour ajouter le nœud au graphique d’événements.</span><span class="sxs-lookup"><span data-stu-id="ad114-127">Click **+** next to **On Add Tracked Geometry** to add the node to the Event Graph.</span></span>
    - <span data-ttu-id="ad114-128">Vous trouverez la liste complète des événements dans l’API du composant [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).</span><span class="sxs-lookup"><span data-stu-id="ad114-128">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span>

![Ajouter un nœud à On Add Tracked Geometry](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-qr-code"></a><span data-ttu-id="ad114-130">Utilisation d’un code QR suivi</span><span class="sxs-lookup"><span data-stu-id="ad114-130">Using a tracked QR code</span></span>

<span data-ttu-id="ad114-131">Le graphique d’événements dans l’image suivante présente l’événement **OnUpdateTrackedImage** qui est utilisé pour afficher un point au centre d’un code QR et imprimer ses données.</span><span class="sxs-lookup"><span data-stu-id="ad114-131">The Event Graph in the following image shows the **OnUpdateTrackedImage** event being used to render a point in the center of a QR code and print out its data.</span></span>

[!INCLUDE[](includes/tabs-qr-codes-2.md)]

<span data-ttu-id="ad114-132">Voici ce qui se passe :</span><span class="sxs-lookup"><span data-stu-id="ad114-132">Here's what's going on:</span></span>
1. <span data-ttu-id="ad114-133">Tout d’abord, l’image suivie est castée en **ARTrackedQRCode** pour vérifier que l’image mise à jour actuelle est un code QR.</span><span class="sxs-lookup"><span data-stu-id="ad114-133">First, the tracked image is cast to an **ARTrackedQRCode** to check that the current updated image is a QR code.</span></span>  
2. <span data-ttu-id="ad114-134">Les données encodées sont récupérées à partir de la variable **QRCode**.</span><span class="sxs-lookup"><span data-stu-id="ad114-134">The encoded data is retrieved from the **QRCode** variable.</span></span> <span data-ttu-id="ad114-135">Vous pouvez obtenir l’angle supérieur gauche du code QR à partir de l’emplacement de **GetLocalToWorldTransform** et les dimensions avec **GetEstimateSize**.</span><span class="sxs-lookup"><span data-stu-id="ad114-135">You can get the top-left of the QR code from the location of **GetLocalToWorldTransform** and the dimensions with **GetEstimateSize**.</span></span>

<span data-ttu-id="ad114-136">Vous pouvez aussi [obtenir le système de coordonnées pour un code QR](/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) dans le code.</span><span class="sxs-lookup"><span data-stu-id="ad114-136">You can also [get the coordinate system for a QR code](/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) in code.</span></span>

## <a name="finding-the-unique-id"></a><span data-ttu-id="ad114-137">Recherche de l’ID unique</span><span class="sxs-lookup"><span data-stu-id="ad114-137">Finding the unique ID</span></span>

<span data-ttu-id="ad114-138">À chaque code QR correspond un ID guid unique, que vous pouvez trouver comme ceci :</span><span class="sxs-lookup"><span data-stu-id="ad114-138">Every QR code has a unique guid ID, which you can find by:</span></span>
- <span data-ttu-id="ad114-139">Glissez-déposez le repère **As ARTracked QRCode** et effectuez une recherche sur l’ID unique (**Unique ID**).</span><span class="sxs-lookup"><span data-stu-id="ad114-139">Dragging and dropping the **As ARTracked QRCode**  pin and searching for **Get Unique ID**.</span></span>

![GUID QR](images/unreal-qr-guid.PNG)

<span data-ttu-id="ad114-141">Il se passe beaucoup de choses en coulisse avec les codes QR : vous n’en avez donc pas terminé.</span><span class="sxs-lookup"><span data-stu-id="ad114-141">There's a lot going on behind the scenes with QR codes, so you're not at the end of the road.</span></span> <span data-ttu-id="ad114-142">N’hésitez pas à consulter les liens ci-dessous pour en savoir plus sur la mécanique interne.</span><span class="sxs-lookup"><span data-stu-id="ad114-142">Be sure to check out the following links for more details on what's under the hood.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="ad114-143">Point de contrôle de développement suivant</span><span class="sxs-lookup"><span data-stu-id="ad114-143">Next Development Checkpoint</span></span>

<span data-ttu-id="ad114-144">Si vous suivez le parcours des points de contrôle de développement Unreal que nous avons mis en place, vous explorez actuellement les API et fonctionnalités de la plateforme Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="ad114-144">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="ad114-145">À partir de là, vous pouvez passer à la rubrique suivante :</span><span class="sxs-lookup"><span data-stu-id="ad114-145">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ad114-146">WinRT</span><span class="sxs-lookup"><span data-stu-id="ad114-146">WinRT</span></span>](unreal-winRT.md)

<span data-ttu-id="ad114-147">Ou accéder directement au déploiement de votre application sur un appareil ou un émulateur :</span><span class="sxs-lookup"><span data-stu-id="ad114-147">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ad114-148">Déploiement sur un appareil</span><span class="sxs-lookup"><span data-stu-id="ad114-148">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="ad114-149">Vous pouvez revenir aux [points de contrôle de développement Unreal](unreal-development-overview.md#3-advanced-features) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="ad114-149">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-advanced-features) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="ad114-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad114-150">See also</span></span>
* [<span data-ttu-id="ad114-151">Mappage spatial</span><span class="sxs-lookup"><span data-stu-id="ad114-151">Spatial mapping</span></span>](../../design/spatial-mapping.md)
* [<span data-ttu-id="ad114-152">Hologrammes</span><span class="sxs-lookup"><span data-stu-id="ad114-152">Holograms</span></span>](../../discover/hologram.md)
* [<span data-ttu-id="ad114-153">Systèmes de coordonnées</span><span class="sxs-lookup"><span data-stu-id="ad114-153">Coordinate systems</span></span>](../../design/coordinate-systems.md)