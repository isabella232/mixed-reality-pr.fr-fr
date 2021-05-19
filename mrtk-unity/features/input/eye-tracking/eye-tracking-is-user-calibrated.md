---
title: Étalonnage oculaire
description: Comment configurer l’étalonnage des yeux des utilisateurs dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, EyeTracking, étalonnage,
ms.openlocfilehash: d7ae9885b77798b44b3d63bb7f92283658e05411
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144001"
---
# <a name="eye-calibration"></a>Étalonnage oculaire

![Capture d’écran de la notification d’étalonnage oculaire](../../images/eye-tracking/mrtk_et_calibration_notification_example.jpg)

## <a name="overview"></a>Vue d’ensemble

Si le suivi oculaire est un élément fondamental de l’expérience de votre application, il est possible de s’assurer que l’étalonnage des yeux de l’utilisateur est valide.
La raison principale pour laquelle il est non valide est que l’utilisateur a choisi d’ignorer l’étalonnage du suivi oculaire lors de la création de l’appareil.

Cette page traite des sujets suivants :

- Décrit comment détecter qu’un utilisateur est étalonné par un œil
- Fournit un exemple illustrant comment déclencher une notification utilisateur pour indiquer à l’utilisateur de passer par l’étalonnage oculaire
  - Ignorer automatiquement la notification si l’étalonnage des yeux devient valide
  - Ignorer manuellement la notification si l’utilisateur choisit de continuer sans étalonnage

### <a name="how-to-detect-the-eye-calibration-state"></a>Comment détecter l’état d’étalonnage oculaire

La configuration du suivi des yeux dans MRTK est configurée via l' [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interface.

L’utilisation de [CoreServices. InputSystem. EyeGazeProvider](eye-tracking-eye-gaze-provider.md) fournit l’implémentation par défaut du fournisseur de regard inscrite dans la boîte à outils au moment de l’exécution. `IMixedRealityEyeGazeProvider.IsEyeGazeValid` retourne un `bool?` qui a la valeur null si aucune information du dispositif de suivi oculaire n’est encore disponible.
Une fois les données reçues, elles retournent la valeur true ou false pour indiquer que l’étalonnage du suivi des yeux de l’utilisateur est valide ou non valide.

### <a name="sample-eye-calibration-notification---step-by-step"></a>Exemple de notification d’étalonnage oculaire-étape par étape

1. Ouvrir l’exemple de package MRTK Eye Tracking (ressources/MRTK/examples/démos/EyeTracking)

2. Charger la scène _EyeTrackingDemo-00-RootScene. Unity_

3. Consultez _EyeCalibrationChecker_:
   - Dans cette scène, nous avons déjà un exemple permettant de détecter si l’utilisateur actuel est étalonné sous l' *objet de jeu _EyeCalibrationChecker_*.
Il se contente de créer des panneaux de texte et des déclencheurs supplémentaires pour la fusion et l’extraction de la notification. Cela implique une croissance lente de sa taille et de son opacité lors de l’activation.
Une fois la notification fermée, sa taille et son fondu diminuent lentement.

   - Attaché à l' *objet de jeu _EyeCalibrationChecker_* est le script [EyeCalibrationChecker](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker) qui expose deux événements Unity :
      - `OnEyeCalibrationDetected()`
      - `OnNoEyeCalibrationDetected()`

   - Ces événements se déclenchent uniquement si l’état de l’étalonnage change. Par conséquent, si un utilisateur choisit d’ignorer la notification, la notification ne s’affiche plus tant que
      - L’application est redémarrée
      - Un utilisateur valide a été détecté, puis un nouvel utilisateur non étalonné a mis l’appareil sur

   - Pour tester si les animations et les événements sont déclenchés correctement, le script EyeCalibrationChecker possède un `bool editorTestUserIsCalibrated` indicateur. Par exemple, lorsqu’il s’exécute dans l’éditeur Unity, vous pouvez tester :
      1. Si la notification s’affiche automatiquement lorsque l’état d’étalonnage passe de true à false
      1. S’il referme automatiquement la notification une fois que l’état passe de false à true.

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

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du suivi des yeux MRTK](eye-tracking-main.md)
- [Configuration du suivi des yeux MRTK](eye-tracking-basic-setup.md)
- [Suivi des yeux MRTK par code](eye-tracking-eye-gaze-provider.md)
- [Documentation sur le suivi oculaire HoloLens 2](/windows/mixed-reality/eye-tracking)