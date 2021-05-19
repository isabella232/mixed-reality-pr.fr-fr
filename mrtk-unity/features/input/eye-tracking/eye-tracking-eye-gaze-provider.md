---
title: Suivi oculaire - Fournisseur de suivi du regard
description: Documentation sur le fournisseur de regard oculaire dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, EyeTracking, EyeGaze,
ms.openlocfilehash: ef50a55d52a5dad9f424c8af8139565e02542b6c
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144026"
---
# <a name="accessing-eye-tracking-data-in-your-unity-script"></a><span data-ttu-id="917b5-104">Accès aux données de suivi oculaire dans votre script Unity</span><span class="sxs-lookup"><span data-stu-id="917b5-104">Accessing eye tracking data in your Unity script</span></span>

<span data-ttu-id="917b5-105">Cet article suppose que vous disposez d’une compréhension de la configuration du suivi des yeux dans une scène MRTK (consultez [configuration de base MRTK pour utiliser le suivi oculaire](eye-tracking-basic-setup.md)).</span><span class="sxs-lookup"><span data-stu-id="917b5-105">This article assumes one has understanding for setting up eye tracking in an MRTK scene (see [Basic MRTK setup to use eye tracking](eye-tracking-basic-setup.md)).</span></span>
<span data-ttu-id="917b5-106">L’accès aux données de suivi oculaire dans un script monocomportement est simple !</span><span class="sxs-lookup"><span data-stu-id="917b5-106">Accessing eye tracking data in a MonoBehaviour script is easy!</span></span> <span data-ttu-id="917b5-107">Utilisez simplement *CoreServices. InputSystem. EyeGazeProvider*.</span><span class="sxs-lookup"><span data-stu-id="917b5-107">Simply use *CoreServices.InputSystem.EyeGazeProvider*.</span></span>

## <a name="imixedrealityeyegazeprovider"></a><span data-ttu-id="917b5-108">IMixedRealityEyeGazeProvider</span><span class="sxs-lookup"><span data-stu-id="917b5-108">IMixedRealityEyeGazeProvider</span></span>

<span data-ttu-id="917b5-109">La configuration du suivi des yeux dans MRTK est configurée via l' [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interface.</span><span class="sxs-lookup"><span data-stu-id="917b5-109">Eye tracking configuration in MRTK is configured via the [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interface.</span></span> <span data-ttu-id="917b5-110">L’utilisation de [CoreServices. InputSystem. EyeGazeProvider](eye-tracking-eye-gaze-provider.md) fournit l’implémentation par défaut du fournisseur de regard inscrite dans la boîte à outils au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="917b5-110">Using [CoreServices.InputSystem.EyeGazeProvider](eye-tracking-eye-gaze-provider.md) provides the default gaze provider implementation registered in the toolkit at runtime.</span></span>
<span data-ttu-id="917b5-111">Les propriétés utiles du `EyeGazeProvider` sont présentées ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="917b5-111">Useful properties of the `EyeGazeProvider` is outlined below.</span></span>

- <span data-ttu-id="917b5-112">**IsEyeTrackingEnabled**: true si l’utilisateur a choisi d’utiliser le suivi oculaire pour le point de vue du regard.</span><span class="sxs-lookup"><span data-stu-id="917b5-112">**IsEyeTrackingEnabled**: True if user has selected to use eye tracking for gaze.</span></span>

- <span data-ttu-id="917b5-113">**IsEyeCalibrationValid**: indique si l’étalonnage du suivi oculaire de l’utilisateur est valide ou non.</span><span class="sxs-lookup"><span data-stu-id="917b5-113">**IsEyeCalibrationValid**: Indicates whether the user's eye tracking calibration is valid or not.</span></span>
<span data-ttu-id="917b5-114">Elle retourne’null', si la valeur n’a pas encore reçu de données du système de suivi visuel.</span><span class="sxs-lookup"><span data-stu-id="917b5-114">It returns 'null', if the value has not yet received data from the eye tracking system.</span></span>
<span data-ttu-id="917b5-115">Elle n’est peut-être pas valide, car l’utilisateur a ignoré l’étalonnage du suivi oculaire.</span><span class="sxs-lookup"><span data-stu-id="917b5-115">It may be invalid, because the user skipped the eye tracking calibration.</span></span>

- <span data-ttu-id="917b5-116">**IsEyeTrackingEnabledAndValid**: indique si les données de suivi visuel en cours sont actuellement utilisées pour le point de regard.</span><span class="sxs-lookup"><span data-stu-id="917b5-116">**IsEyeTrackingEnabledAndValid**: Indicates whether the current eye tracking data is currently been used for gaze.</span></span>

- <span data-ttu-id="917b5-117">**IsEyeTrackingDataValid**: true si les données de suivi visuel sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="917b5-117">**IsEyeTrackingDataValid**: True if eye tracking data is available.</span></span>
<span data-ttu-id="917b5-118">Il est possible qu’il ne soit pas disponible en raison d’un dépassement du délai d’attente (doit être robuste pour le clignotement de l’utilisateur) ou d’un manque de matériel ou d’autorisations de suivi.</span><span class="sxs-lookup"><span data-stu-id="917b5-118">It may be unavailable due to exceeded timeout (should be robust to the user blinking though) or lack of tracking hardware or permissions.</span></span>
<span data-ttu-id="917b5-119">Consultez notre [exemple de notification d’étalonnage oculaire manquant](eye-tracking-is-user-calibrated.md) qui explique comment détecter si un utilisateur est étalonné par un œil et pour afficher une notification appropriée.</span><span class="sxs-lookup"><span data-stu-id="917b5-119">Check out our [Missing eye calibration notification sample](eye-tracking-is-user-calibrated.md) that explains how to detect whether a user is eye calibrated and to show an appropriate notification.</span></span>

- <span data-ttu-id="917b5-120">**GazeOrigin**: origine du point de regard.</span><span class="sxs-lookup"><span data-stu-id="917b5-120">**GazeOrigin**: Origin of the gaze ray.</span></span>
<span data-ttu-id="917b5-121">Notez que cette opération renvoie l’origine du point d’entrée de la *tête* si « IsEyeGazeValid » a la valeur false.</span><span class="sxs-lookup"><span data-stu-id="917b5-121">Please note that this will return the *head* gaze origin if 'IsEyeGazeValid' is false.</span></span>

- <span data-ttu-id="917b5-122">**GazeDirection**: direction du point de regard.</span><span class="sxs-lookup"><span data-stu-id="917b5-122">**GazeDirection**: Direction of the gaze ray.</span></span>
<span data-ttu-id="917b5-123">Le sens du regard de la *tête* est retourné si « IsEyeGazeValid » a la valeur false.</span><span class="sxs-lookup"><span data-stu-id="917b5-123">This will return the *head* gaze direction if 'IsEyeGazeValid' is false.</span></span>

- <span data-ttu-id="917b5-124">**HitInfo**, **HitPosition**, **HitNormal**, etc. : informations sur la cible actuellement en regard.</span><span class="sxs-lookup"><span data-stu-id="917b5-124">**HitInfo**, **HitPosition**, **HitNormal**, etc.: Information about the currently gazed at target.</span></span>
<span data-ttu-id="917b5-125">Là encore, si `IsEyeGazeValid` a la valeur false, il sera basé sur  le point de regard de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="917b5-125">Again, if `IsEyeGazeValid` is false, this will be based on the user's *head* gaze.</span></span>

## <a name="examples-for-using-coreservicesinputsystemeyegazeprovider"></a><span data-ttu-id="917b5-126">Exemples d’utilisation de CoreServices. InputSystem. EyeGazeProvider</span><span class="sxs-lookup"><span data-stu-id="917b5-126">Examples for using CoreServices.InputSystem.EyeGazeProvider</span></span>

<span data-ttu-id="917b5-127">Voici un exemple de [FollowEyeGaze. cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FollowEyeGaze):</span><span class="sxs-lookup"><span data-stu-id="917b5-127">Here is an example from the [FollowEyeGaze.cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FollowEyeGaze):</span></span>

- <span data-ttu-id="917b5-128">Obtenir le point d’un hologramme que l’utilisateur examine :</span><span class="sxs-lookup"><span data-stu-id="917b5-128">Get the point of a hologram that the user is looking at:</span></span>

```c#
// Show the object at the hit position of the user's eye gaze ray with the target.
gameObject.transform.position = CoreServices.InputSystem.EyeGazeProvider.HitPosition;
```

- <span data-ttu-id="917b5-129">Montrer une ressource visuelle à une distance fixe à partir de laquelle l’utilisateur recherche actuellement :</span><span class="sxs-lookup"><span data-stu-id="917b5-129">Showing a visual asset at a fixed distance from where the user is currently looking:</span></span>

```c#
// If no target is hit, show the object at a default distance along the gaze ray.
gameObject.transform.position =
CoreServices.InputSystem.EyeGazeProvider.GazeOrigin +
CoreServices.InputSystem.EyeGazeProvider.GazeDirection.normalized * defaultDistanceInMeters;
```

## <a name="see-also"></a><span data-ttu-id="917b5-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="917b5-130">See also</span></span>

- [<span data-ttu-id="917b5-131">Vue d’ensemble du suivi des yeux MRTK</span><span class="sxs-lookup"><span data-stu-id="917b5-131">MRTK Eye Tracking Overview</span></span>](eye-tracking-main.md)
- [<span data-ttu-id="917b5-132">Configuration du suivi des yeux MRTK</span><span class="sxs-lookup"><span data-stu-id="917b5-132">MRTK Eye Tracking setup</span></span>](eye-tracking-basic-setup.md)
- [<span data-ttu-id="917b5-133">Étalonnage du suivi des yeux MRTK</span><span class="sxs-lookup"><span data-stu-id="917b5-133">MRTK Eye Tracking Calibration</span></span>](eye-tracking-is-user-calibrated.md)
- [<span data-ttu-id="917b5-134">Documentation sur le suivi oculaire HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="917b5-134">HoloLens 2 Eye Tracking Documentation</span></span>](/windows/mixed-reality/eye-tracking)