---
title: État d’entrée
description: Documentation sur les États d’entrée dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, InputState,
ms.openlocfilehash: 7d5e008ae3e43d227b90a563dd74e65a89527bd7ddf1720e26577042ce0d545f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228359"
---
# <a name="accessing-input-state-in-mrtk"></a>Accès à l’état d’entrée dans MRTK

Il est possible d’interroger directement l’état de toutes les entrées dans MRTK en effectuant une itération sur les contrôleurs attachés aux sources d’entrée. MRTK fournit également des méthodes pratiques pour accéder à la position et à la rotation des yeux, mains, tête et contrôleur de mouvement.

Pour obtenir un exemple d’interrogation d’entrée via l’itération sur les contrôleurs et l’utilisation de la classe, consultez la scène InputDataExample [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) .

## <a name="example-access-position-rotation-of-head-hands-eyes-in-mrtk"></a>Exemple : position d’accès, rotation de l’en-tête, mains, yeux dans MRTK

[`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils)La classe de MRTK fournit des méthodes pratiques pour accéder aux rayons de la main, aux rayons de tête, aux rayons de regard oculaire et aux rayons de contrôleur de mouvement.

```c#
// Get the head ray
var headRay = InputRayUtils.GetHeadGazeRay();

// Get the right hand ray
Ray rightHandRay;
if(InputRayUtils.TryGetHandRay(Handedness.right, rightHandRay))
{
    // Right hand ray is available
}
else
{
    // Right hand ray is not available
}
```

## <a name="example-access-position-rotation-of-all-6dof-controllers-active-in-scene"></a>Exemple : position d’accès, rotation de tous les contrôleurs 6DOF actifs dans la scène

```c#
foreach(var controller in CoreServices.InputSystem.DetectedControllers)
{
    // Interactions for a controller is the list of inputs that this controller exposes
    foreach(MixedRealityInteractionMapping inputMapping in controller.Interactions)
    {
        // 6DOF controllers support the "SpatialPointer" type (pointing direction)
        // or "GripPointer" type (direction of the 6DOF controller)
        if (inputMapping.InputType == DeviceInputType.SpatialPointer)
        {
            Debug.Log("spatial pointer PositionData: " + inputMapping.PositionData);
            Debug.Log("spatial pointer RotationData: " + inputMapping.RotationData);
        }

        if (inputMapping.InputType == DeviceInputType.SpatialGrip)
        {
            Debug.Log("spatial grip PositionData: " + inputMapping.PositionData);
            Debug.Log("spatial grip RotationData: " + inputMapping.RotationData);
        }
    }
}
```

## <a name="see-also"></a>Voir aussi

- [InputEvents](input-events.md)
- [Pointeurs](pointers.md)
- [HandTracking](hand-tracking.md)
