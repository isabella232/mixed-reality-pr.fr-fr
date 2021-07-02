---
title: Étalonnage oculaire
description: Comment configurer l’étalonnage des yeux des utilisateurs dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, EyeTracking, étalonnage,
ms.openlocfilehash: a2023a2d7f6a0254e8fef32f4faf09def956e94f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177203"
---
# <a name="eye-calibration"></a><span data-ttu-id="ac91d-104">Étalonnage oculaire</span><span class="sxs-lookup"><span data-stu-id="ac91d-104">Eye calibration</span></span>

![Capture d’écran de la notification d’étalonnage oculaire](../../images/eye-tracking/mrtk_et_calibration_notification_example.jpg)

## <a name="overview"></a><span data-ttu-id="ac91d-106">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="ac91d-106">Overview</span></span>

<span data-ttu-id="ac91d-107">Si le suivi oculaire est un élément fondamental de l’expérience de votre application, il est possible de s’assurer que l’étalonnage des yeux de l’utilisateur est valide.</span><span class="sxs-lookup"><span data-stu-id="ac91d-107">If eye tracking is a fundamental part of your app experience, one may wish to ensure that the user's eye calibration is valid.</span></span>
<span data-ttu-id="ac91d-108">La raison principale pour laquelle il est non valide est que l’utilisateur a choisi d’ignorer l’étalonnage du suivi oculaire lors de la création de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="ac91d-108">The main reason for it to be invalid is that the user has chosen to skip the eye tracking calibration when putting on the device.</span></span>

<span data-ttu-id="ac91d-109">Cette page traite des sujets suivants :</span><span class="sxs-lookup"><span data-stu-id="ac91d-109">This page covers the following:</span></span>

- <span data-ttu-id="ac91d-110">Décrit comment détecter qu’un utilisateur est étalonné par un œil</span><span class="sxs-lookup"><span data-stu-id="ac91d-110">Describes how to detect that a user is eye calibrated</span></span>
- <span data-ttu-id="ac91d-111">Fournit un exemple illustrant comment déclencher une notification utilisateur pour indiquer à l’utilisateur de passer par l’étalonnage oculaire</span><span class="sxs-lookup"><span data-stu-id="ac91d-111">Provides a sample for how to trigger a user notification to instruct the user to go through the eye calibration</span></span>
  - <span data-ttu-id="ac91d-112">Ignorer automatiquement la notification si l’étalonnage des yeux devient valide</span><span class="sxs-lookup"><span data-stu-id="ac91d-112">Automatically dismiss notification if eye calibration becomes valid</span></span>
  - <span data-ttu-id="ac91d-113">Ignorer manuellement la notification si l’utilisateur choisit de continuer sans étalonnage</span><span class="sxs-lookup"><span data-stu-id="ac91d-113">Manually dismiss notification if user chooses to continue without calibration</span></span>

### <a name="how-to-detect-the-eye-calibration-state"></a><span data-ttu-id="ac91d-114">Comment détecter l’état d’étalonnage oculaire</span><span class="sxs-lookup"><span data-stu-id="ac91d-114">How to detect the eye calibration state</span></span>

<span data-ttu-id="ac91d-115">La configuration du suivi des yeux dans MRTK est configurée via l' [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interface.</span><span class="sxs-lookup"><span data-stu-id="ac91d-115">Eye tracking configuration in MRTK is configured via the [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interface.</span></span>

<span data-ttu-id="ac91d-116">L’utilisation de [CoreServices. InputSystem. EyeGazeProvider](eye-tracking-eye-gaze-provider.md) fournit l’implémentation par défaut du fournisseur de regard inscrite dans la boîte à outils au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="ac91d-116">Using [CoreServices.InputSystem.EyeGazeProvider](eye-tracking-eye-gaze-provider.md) provides the default gaze provider implementation registered in the toolkit at runtime.</span></span> <span data-ttu-id="ac91d-117">`IMixedRealityEyeGazeProvider.IsEyeGazeValid` retourne un `bool?` qui a la valeur null si aucune information du dispositif de suivi oculaire n’est encore disponible.</span><span class="sxs-lookup"><span data-stu-id="ac91d-117">`IMixedRealityEyeGazeProvider.IsEyeGazeValid` returns a `bool?` which is null if no information from the eye tracker is available yet.</span></span>
<span data-ttu-id="ac91d-118">Une fois les données reçues, elles retournent la valeur true ou false pour indiquer que l’étalonnage du suivi des yeux de l’utilisateur est valide ou non valide.</span><span class="sxs-lookup"><span data-stu-id="ac91d-118">Once data has been received, it will either return true or false to indicate that the user's eye tracking calibration is valid or invalid.</span></span>

### <a name="sample-eye-calibration-notification---step-by-step"></a><span data-ttu-id="ac91d-119">Exemple de notification d’étalonnage oculaire-étape par étape</span><span class="sxs-lookup"><span data-stu-id="ac91d-119">Sample eye calibration notification - step-by-step</span></span>

1. <span data-ttu-id="ac91d-120">Ouvrir l’exemple de package MRTK Eye Tracking (ressources/MRTK/examples/démos/EyeTracking)</span><span class="sxs-lookup"><span data-stu-id="ac91d-120">Open the MRTK eye tracking example package (Assets/MRTK/Examples/Demos/EyeTracking)</span></span>

2. <span data-ttu-id="ac91d-121">Charger la scène _EyeTrackingDemo-00-RootScene. Unity_</span><span class="sxs-lookup"><span data-stu-id="ac91d-121">Load _EyeTrackingDemo-00-RootScene.unity_ scene</span></span>

3. <span data-ttu-id="ac91d-122">Consultez _EyeCalibrationChecker_:</span><span class="sxs-lookup"><span data-stu-id="ac91d-122">Check out _EyeCalibrationChecker_:</span></span>
   - <span data-ttu-id="ac91d-123">Dans cette scène, nous avons déjà un exemple permettant de détecter si l’utilisateur actuel est étalonné sous l' *objet de jeu _EyeCalibrationChecker_*.</span><span class="sxs-lookup"><span data-stu-id="ac91d-123">In this scene, we have already a sample for detecting whether the current user is calibrated under the *_EyeCalibrationChecker_ game object*.</span></span>
<span data-ttu-id="ac91d-124">Il se contente de créer des panneaux de texte et des déclencheurs supplémentaires pour la fusion et l’extraction de la notification. Cela implique une croissance lente de sa taille et de son opacité lors de l’activation.</span><span class="sxs-lookup"><span data-stu-id="ac91d-124">It simply parents a few text meshes and has some additional triggers for blending the notification in and out. This includes slowly increasing its size and opacity on activation.</span></span>
<span data-ttu-id="ac91d-125">Une fois la notification fermée, sa taille et son fondu diminuent lentement.</span><span class="sxs-lookup"><span data-stu-id="ac91d-125">Once the notification is dismissed, it will slowly decrease its size and fade out.</span></span>

   - <span data-ttu-id="ac91d-126">Attaché à l' *objet de jeu _EyeCalibrationChecker_* est le script [EyeCalibrationChecker](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker) qui expose deux événements Unity :</span><span class="sxs-lookup"><span data-stu-id="ac91d-126">Attached to the *_EyeCalibrationChecker_ game object* is the [EyeCalibrationChecker](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker) script which exposes two Unity Events:</span></span>
      - `OnEyeCalibrationDetected()`
      - `OnNoEyeCalibrationDetected()`

   - <span data-ttu-id="ac91d-127">Ces événements se déclenchent uniquement si l’état de l’étalonnage change.</span><span class="sxs-lookup"><span data-stu-id="ac91d-127">These events will only trigger if the calibration status changes.</span></span> <span data-ttu-id="ac91d-128">Par conséquent, si un utilisateur choisit d’ignorer la notification, la notification ne s’affiche plus tant que</span><span class="sxs-lookup"><span data-stu-id="ac91d-128">Hence, if a user chooses to dismiss the notification, the notification will not show up again until</span></span>
      - <span data-ttu-id="ac91d-129">L’application est redémarrée</span><span class="sxs-lookup"><span data-stu-id="ac91d-129">The app gets restarted</span></span>
      - <span data-ttu-id="ac91d-130">Un utilisateur valide a été détecté, puis un nouvel utilisateur non étalonné a mis l’appareil sur</span><span class="sxs-lookup"><span data-stu-id="ac91d-130">A valid user has been detected and then a new uncalibrated user has put the device on</span></span>

   - <span data-ttu-id="ac91d-131">Pour tester si les animations et les événements sont déclenchés correctement, le script EyeCalibrationChecker possède un `bool editorTestUserIsCalibrated` indicateur.</span><span class="sxs-lookup"><span data-stu-id="ac91d-131">For testing whether the animations and events are triggered correctly, the EyeCalibrationChecker script possesses a `bool editorTestUserIsCalibrated` flag.</span></span> <span data-ttu-id="ac91d-132">Par exemple, lorsqu’il s’exécute dans l’éditeur Unity, vous pouvez tester :</span><span class="sxs-lookup"><span data-stu-id="ac91d-132">For example, when running in the Unity Editor, one can test:</span></span>
      1. <span data-ttu-id="ac91d-133">Si la notification s’affiche automatiquement lorsque l’état d’étalonnage passe de true à false</span><span class="sxs-lookup"><span data-stu-id="ac91d-133">Whether the notification automatically pops up once the calibration status changes from true to false</span></span>
      1. <span data-ttu-id="ac91d-134">S’il referme automatiquement la notification une fois que l’état passe de false à true.</span><span class="sxs-lookup"><span data-stu-id="ac91d-134">Whether it automatically dismisses the notification again once the status changes from false to true.</span></span>

```c#
    private bool? prevCalibrationStatus = null;
    ...

   void Update()
   {
      // Get the latest calibration state from the EyeGazeProvider
      bool? calibrationStatus = CoreServices.InputSystem?.EyeGazeProvider?.IsEyeCalibrationValid;

      ...

      if (calibrationStatus != null)
      {
         if (prevCalibrationStatus != calibrationStatus)
         {
            if (calibrationStatus == false)
            {
               OnNoEyeCalibrationDetected.Invoke();
            }
         else
         {
            OnEyeCalibrationDetected.Invoke();
         }

         prevCalibrationStatus = calibrationStatus;
      }
   }
```

## <a name="see-also"></a><span data-ttu-id="ac91d-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac91d-135">See also</span></span>

- [<span data-ttu-id="ac91d-136">Vue d’ensemble du suivi des yeux MRTK</span><span class="sxs-lookup"><span data-stu-id="ac91d-136">MRTK Eye Tracking Overview</span></span>](eye-tracking-main.md)
- [<span data-ttu-id="ac91d-137">Configuration du suivi des yeux MRTK</span><span class="sxs-lookup"><span data-stu-id="ac91d-137">MRTK Eye Tracking setup</span></span>](eye-tracking-basic-setup.md)
- [<span data-ttu-id="ac91d-138">Suivi des yeux MRTK par code</span><span class="sxs-lookup"><span data-stu-id="ac91d-138">MRTK Eye Tracking via Code</span></span>](eye-tracking-eye-gaze-provider.md)
- [<span data-ttu-id="ac91d-139">HoloLens 2 Documentation sur le suivi oculaire</span><span class="sxs-lookup"><span data-stu-id="ac91d-139">HoloLens 2 Eye Tracking Documentation</span></span>](/windows/mixed-reality/eye-tracking)
