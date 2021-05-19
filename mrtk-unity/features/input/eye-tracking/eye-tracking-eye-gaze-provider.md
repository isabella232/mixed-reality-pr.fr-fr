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
# <a name="accessing-eye-tracking-data-in-your-unity-script"></a>Accès aux données de suivi oculaire dans votre script Unity

Cet article suppose que vous disposez d’une compréhension de la configuration du suivi des yeux dans une scène MRTK (consultez [configuration de base MRTK pour utiliser le suivi oculaire](eye-tracking-basic-setup.md)).
L’accès aux données de suivi oculaire dans un script monocomportement est simple ! Utilisez simplement *CoreServices. InputSystem. EyeGazeProvider*.

## <a name="imixedrealityeyegazeprovider"></a>IMixedRealityEyeGazeProvider

La configuration du suivi des yeux dans MRTK est configurée via l' [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interface. L’utilisation de [CoreServices. InputSystem. EyeGazeProvider](eye-tracking-eye-gaze-provider.md) fournit l’implémentation par défaut du fournisseur de regard inscrite dans la boîte à outils au moment de l’exécution.
Les propriétés utiles du `EyeGazeProvider` sont présentées ci-dessous.

- **IsEyeTrackingEnabled**: true si l’utilisateur a choisi d’utiliser le suivi oculaire pour le point de vue du regard.

- **IsEyeCalibrationValid**: indique si l’étalonnage du suivi oculaire de l’utilisateur est valide ou non.
Elle retourne’null', si la valeur n’a pas encore reçu de données du système de suivi visuel.
Elle n’est peut-être pas valide, car l’utilisateur a ignoré l’étalonnage du suivi oculaire.

- **IsEyeTrackingEnabledAndValid**: indique si les données de suivi visuel en cours sont actuellement utilisées pour le point de regard.

- **IsEyeTrackingDataValid**: true si les données de suivi visuel sont disponibles.
Il est possible qu’il ne soit pas disponible en raison d’un dépassement du délai d’attente (doit être robuste pour le clignotement de l’utilisateur) ou d’un manque de matériel ou d’autorisations de suivi.
Consultez notre [exemple de notification d’étalonnage oculaire manquant](eye-tracking-is-user-calibrated.md) qui explique comment détecter si un utilisateur est étalonné par un œil et pour afficher une notification appropriée.

- **GazeOrigin**: origine du point de regard.
Notez que cette opération renvoie l’origine du point d’entrée de la *tête* si « IsEyeGazeValid » a la valeur false.

- **GazeDirection**: direction du point de regard.
Le sens du regard de la *tête* est retourné si « IsEyeGazeValid » a la valeur false.

- **HitInfo**, **HitPosition**, **HitNormal**, etc. : informations sur la cible actuellement en regard.
Là encore, si `IsEyeGazeValid` a la valeur false, il sera basé sur  le point de regard de l’utilisateur.

## <a name="examples-for-using-coreservicesinputsystemeyegazeprovider"></a>Exemples d’utilisation de CoreServices. InputSystem. EyeGazeProvider

Voici un exemple de [FollowEyeGaze. cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FollowEyeGaze):

- Obtenir le point d’un hologramme que l’utilisateur examine :

```c#
// Show the object at the hit position of the user's eye gaze ray with the target.
gameObject.transform.position = CoreServices.InputSystem.EyeGazeProvider.HitPosition;
```

- Montrer une ressource visuelle à une distance fixe à partir de laquelle l’utilisateur recherche actuellement :

```c#
// If no target is hit, show the object at a default distance along the gaze ray.
gameObject.transform.position =
CoreServices.InputSystem.EyeGazeProvider.GazeOrigin +
CoreServices.InputSystem.EyeGazeProvider.GazeDirection.normalized * defaultDistanceInMeters;
```

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du suivi des yeux MRTK](eye-tracking-main.md)
- [Configuration du suivi des yeux MRTK](eye-tracking-basic-setup.md)
- [Étalonnage du suivi des yeux MRTK](eye-tracking-is-user-calibrated.md)
- [Documentation sur le suivi oculaire HoloLens 2](/windows/mixed-reality/eye-tracking)