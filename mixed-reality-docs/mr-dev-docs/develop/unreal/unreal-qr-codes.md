---
title: Codes QR dans Unreal
description: Guide pour utiliser les codes QR dans Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, réalité mixte, développement, fonctionnalités, documentation, guides, hologrammes, qr codes, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle
ms.openlocfilehash: f2f06e9aa8d458d58dc8551ab6cd726622c30d4c
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354406"
---
# <a name="qr-codes-in-unreal"></a><span data-ttu-id="e66ce-104">Codes QR dans Unreal</span><span class="sxs-lookup"><span data-stu-id="e66ce-104">QR codes in Unreal</span></span>

<span data-ttu-id="e66ce-105">HoloLens 2 peut voir les codes QR dans l’espace universel à travers la webcam, qui les affiche sous forme d’hologrammes en utilisant un système de coordonnées à la position réelle de chaque code.</span><span class="sxs-lookup"><span data-stu-id="e66ce-105">The HoloLens 2 can see QR codes in world space using the webcam, which renders them as holograms using a coordinate system at each code's real-world position.</span></span>  <span data-ttu-id="e66ce-106">En plus des codes QR uniques, HoloLens 2 peut aussi afficher des hologrammes sur plusieurs appareils à la même position pour créer une expérience partagée.</span><span class="sxs-lookup"><span data-stu-id="e66ce-106">In addition to single QR codes, HoloLens 2 can also render holograms in the same location on multiple devices to create a shared experience.</span></span> <span data-ttu-id="e66ce-107">Veillez à suivre les bonnes pratiques pour ajouter les codes QR à vos applications :</span><span class="sxs-lookup"><span data-stu-id="e66ce-107">Make sure you're following the best practices for adding QR codes to your applications:</span></span>

- <span data-ttu-id="e66ce-108">Zones calmes</span><span class="sxs-lookup"><span data-stu-id="e66ce-108">Quiet zones</span></span>
- <span data-ttu-id="e66ce-109">Éclairage et toile de fond</span><span class="sxs-lookup"><span data-stu-id="e66ce-109">Lighting and backdrop</span></span>
- <span data-ttu-id="e66ce-110">Taille, distance et position angulaire</span><span class="sxs-lookup"><span data-stu-id="e66ce-110">Size, distance, and angular position</span></span>

<span data-ttu-id="e66ce-111">Au moment de placer les codes QR dans votre application, portez une attention particulière aux [considérations liées à l’environnement](../../environment-considerations-for-hololens.md).</span><span class="sxs-lookup"><span data-stu-id="e66ce-111">Pay special attention to the [environment considerations](../../environment-considerations-for-hololens.md) when QR codes are being placed in your app.</span></span> <span data-ttu-id="e66ce-112">Vous trouverez des informations complémentaires sur chacun de ces sujets ainsi que des instructions sur la façon de télécharger le package NuGet nécessaire dans le document [Suivi des codes QR](../platform-capabilities-and-apis/qr-code-tracking.md).</span><span class="sxs-lookup"><span data-stu-id="e66ce-112">You can find more information on each of these topics and instructions on how to download the required NuGet package in the main [QR code tracking](../platform-capabilities-and-apis/qr-code-tracking.md) document.</span></span>

> [!CAUTION]
> <span data-ttu-id="e66ce-113">Les codes QR sont les seuls types d’images qui peuvent être suivies de façon native par HoloLens ; le module intégré **UARTrackedImage** module n’est pas pris en charge sur HoloLens.</span><span class="sxs-lookup"><span data-stu-id="e66ce-113">QR codes are the only type of images that can be tracked by HoloLens out of the box - Unreal's **UARTrackedImage** module isn't supported on HoloLens.</span></span> <span data-ttu-id="e66ce-114">Si vous avez besoin de suivre des images personnalisées, vous pouvez accéder à la [webcam](unreal-hololens-camera.md) de l’appareil et traiter les images en utilisant une bibliothèque de reconnaissance d’images de tiers.</span><span class="sxs-lookup"><span data-stu-id="e66ce-114">If you need to track custom images, you can access the device's [webcam](unreal-hololens-camera.md) and process images using a third party image recognition library.</span></span> 

## <a name="enabling-qr-detection"></a><span data-ttu-id="e66ce-115">Activation de la détection QR</span><span class="sxs-lookup"><span data-stu-id="e66ce-115">Enabling QR detection</span></span>
<span data-ttu-id="e66ce-116">Étant donné que HoloLens 2 doit utiliser la webcam pour voir les codes QR, vous devez l’activer dans les paramètres du projet :</span><span class="sxs-lookup"><span data-stu-id="e66ce-116">Since the HoloLens 2 needs to use the webcam to see QR codes, you'll need to enable it in the project settings:</span></span>
- <span data-ttu-id="e66ce-117">Ouvrez **Edit > Project Settings**, accédez à la section **Platforms**, puis cliquez sur **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="e66ce-117">Open **Edit > Project Settings**, scroll to the **Platforms** section and click **HoloLens**.</span></span>
    + <span data-ttu-id="e66ce-118">Développez la section **Capabilities** et cochez **Webcam**.</span><span class="sxs-lookup"><span data-stu-id="e66ce-118">Expand the **Capabilities** section and check **Webcam**.</span></span>  
- <span data-ttu-id="e66ce-119">Vous devez aussi opter pour le suivi des codes QR en [ajoutant une ressource ARSessionConfig](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span><span class="sxs-lookup"><span data-stu-id="e66ce-119">You'll also need to opt into QR code tracking by [adding an ARSessionConfig asset](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>

[!INCLUDE[](includes/tabs-qr-codes.md)]

## <a name="setting-up-a-tracked-qr-code"></a><span data-ttu-id="e66ce-120">Configuration d’un code QR suivi</span><span class="sxs-lookup"><span data-stu-id="e66ce-120">Setting up a tracked QR code</span></span>

<span data-ttu-id="e66ce-121">Les codes QR sont exposés sous forme d’image suivie par le biais du système de géométrie suivie de réalité augmentée d’Unreal.</span><span class="sxs-lookup"><span data-stu-id="e66ce-121">QR codes are surfaced through Unreal’s AR tracked geometry system as a tracked image.</span></span> <span data-ttu-id="e66ce-122">Pour que cela fonctionne, vous devez :</span><span class="sxs-lookup"><span data-stu-id="e66ce-122">To get this working, you'll need to:</span></span>
1. <span data-ttu-id="e66ce-123">Créer un blueprint d’acteur et ajouter un composant **ARTrackableNotify** :</span><span class="sxs-lookup"><span data-stu-id="e66ce-123">Create an Actor Blueprint and add an **ARTrackableNotify** component:</span></span>

![Composant ARTrackableNotify QR](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="e66ce-125">Sélectionnez **ARTrackableNotify** et développez la section **Events** dans le panneau **Details** :</span><span class="sxs-lookup"><span data-stu-id="e66ce-125">Select **ARTrackableNotify** and expand the **Events** section in the **Details** panel:</span></span>

![Événements QR](images/unreal-spatialmapping-events.PNG)

3. <span data-ttu-id="e66ce-127">Cliquez sur **+** à côté de **On Add Tracked Geometry** pour ajouter le nœud au graphique d’événements.</span><span class="sxs-lookup"><span data-stu-id="e66ce-127">Click **+** next to **On Add Tracked Geometry** to add the node to the Event Graph.</span></span>
    - <span data-ttu-id="e66ce-128">Vous trouverez la liste complète des événements dans l’API du composant [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).</span><span class="sxs-lookup"><span data-stu-id="e66ce-128">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span>

![Ajouter un nœud à On Add Tracked Geometry](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-qr-code"></a><span data-ttu-id="e66ce-130">Utilisation d’un code QR suivi</span><span class="sxs-lookup"><span data-stu-id="e66ce-130">Using a tracked QR code</span></span>
<span data-ttu-id="e66ce-131">Le graphique d’événements dans l’image suivante présente l’événement **OnUpdateTrackedImage** qui est utilisé pour afficher un point au centre d’un code QR et imprimer ses données.</span><span class="sxs-lookup"><span data-stu-id="e66ce-131">The Event Graph in the following image shows the **OnUpdateTrackedImage** event being used to render a point in the center of a QR code and print out its data.</span></span>

![Exemple d’affichage QR](images/unreal-qr-render.PNG)

<span data-ttu-id="e66ce-133">Voici ce qui se passe :</span><span class="sxs-lookup"><span data-stu-id="e66ce-133">Here's what's going on:</span></span>
1. <span data-ttu-id="e66ce-134">Tout d’abord, l’image suivie est castée en **ARTrackedQRCode** pour vérifier que l’image mise à jour actuelle est un code QR.</span><span class="sxs-lookup"><span data-stu-id="e66ce-134">First, the tracked image is cast to an **ARTrackedQRCode** to check that the current updated image is a QR code.</span></span>  
2. <span data-ttu-id="e66ce-135">Les données encodées sont récupérées à partir de la variable **QRCode**.</span><span class="sxs-lookup"><span data-stu-id="e66ce-135">The encoded data is retrieved from the **QRCode** variable.</span></span> <span data-ttu-id="e66ce-136">Vous pouvez obtenir l’angle supérieur gauche du code QR à partir de l’emplacement de **GetLocalToWorldTransform** et les dimensions avec **GetEstimateSize**.</span><span class="sxs-lookup"><span data-stu-id="e66ce-136">You can get the top-left of the QR code from the location of **GetLocalToWorldTransform** and the dimensions with **GetEstimateSize**.</span></span>

<span data-ttu-id="e66ce-137">Vous pouvez aussi [obtenir le système de coordonnées pour un code QR](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) dans le code.</span><span class="sxs-lookup"><span data-stu-id="e66ce-137">You can also [get the coordinate system for a QR code](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) in code.</span></span>

## <a name="finding-the-unique-id"></a><span data-ttu-id="e66ce-138">Recherche de l’ID unique</span><span class="sxs-lookup"><span data-stu-id="e66ce-138">Finding the unique ID</span></span>
<span data-ttu-id="e66ce-139">À chaque code QR correspond un ID guid unique, que vous pouvez trouver comme ceci :</span><span class="sxs-lookup"><span data-stu-id="e66ce-139">Every QR code has a unique guid ID, which you can find by:</span></span>
- <span data-ttu-id="e66ce-140">Glissez-déposez le repère **As ARTracked QRCode** et effectuez une recherche sur l’ID unique (**Unique ID**).</span><span class="sxs-lookup"><span data-stu-id="e66ce-140">Dragging and dropping the **As ARTracked QRCode**  pin and searching for **Get Unique ID**.</span></span>

![GUID QR](images/unreal-qr-guid.PNG)

<span data-ttu-id="e66ce-142">Il se passe beaucoup de choses en coulisse avec les codes QR ; ce n’est donc pas terminé.</span><span class="sxs-lookup"><span data-stu-id="e66ce-142">There's a lot going on behind the scenes with QR codes, so this isn't the end of the road.</span></span> <span data-ttu-id="e66ce-143">N’hésitez pas à consulter les liens ci-dessous pour en savoir plus sur la mécanique interne.</span><span class="sxs-lookup"><span data-stu-id="e66ce-143">Be sure to check out the following links for more details on what's under the hood.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="e66ce-144">Point de contrôle de développement suivant</span><span class="sxs-lookup"><span data-stu-id="e66ce-144">Next Development Checkpoint</span></span>

<span data-ttu-id="e66ce-145">Si vous suivez le parcours des points de contrôle de développement Unreal que nous avons mis en place, vous explorez actuellement les API et fonctionnalités de la plateforme Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="e66ce-145">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="e66ce-146">À partir de là, vous pouvez passer à la rubrique suivante :</span><span class="sxs-lookup"><span data-stu-id="e66ce-146">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e66ce-147">WinRT</span><span class="sxs-lookup"><span data-stu-id="e66ce-147">WinRT</span></span>](unreal-winRT.md)

<span data-ttu-id="e66ce-148">Ou accéder directement au déploiement de votre application sur un appareil ou un émulateur :</span><span class="sxs-lookup"><span data-stu-id="e66ce-148">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e66ce-149">Déploiement sur un appareil</span><span class="sxs-lookup"><span data-stu-id="e66ce-149">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="e66ce-150">Vous pouvez revenir aux [points de contrôle de développement Unreal](unreal-development-overview.md#3-platform-capabilities-and-apis) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="e66ce-150">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="e66ce-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e66ce-151">See also</span></span>
* [<span data-ttu-id="e66ce-152">Mappage spatial</span><span class="sxs-lookup"><span data-stu-id="e66ce-152">Spatial mapping</span></span>](../../design/spatial-mapping.md)
* [<span data-ttu-id="e66ce-153">Hologrammes</span><span class="sxs-lookup"><span data-stu-id="e66ce-153">Holograms</span></span>](../../discover/hologram.md)
* [<span data-ttu-id="e66ce-154">Systèmes de coordonnées</span><span class="sxs-lookup"><span data-stu-id="e66ce-154">Coordinate systems</span></span>](../../design/coordinate-systems.md)
