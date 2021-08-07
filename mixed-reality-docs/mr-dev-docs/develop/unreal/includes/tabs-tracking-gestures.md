---
ms.openlocfilehash: fa21b1a5c3c89cf3c1c63c7ed8ebbdc3d8547661443853987ee3713e50c50e5c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187415"
---
# <a name="426"></a>[4.26](#tab/426)

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

![Plan de la lecture de début d’événement connecté à la fonction de configuration des mouvements](../images/unreal-hand-tracking-img-09.png)

Vous devez ensuite ajouter du code pour vous abonner aux événements suivants :

![plan de Windows les gestes d’entrée spatiale, de robinet et de manipulation ](../images/unreal/key-events.png)
 ![ de gauche capture d’écran de l’Windows options de mouvement d’entrée spatiale dans le volet d’informations](../images/unreal/key-events2.png)

### <a name="openxr"></a>OpenXR

Dans OpenXR, les événements de mouvement sont suivis via le pipeline d’entrée. À l’aide de l’interaction manuelle, l’appareil peut reconnaître automatiquement les gestes TAP et Hold, mais pas les autres. Elles sont nommées en tant que mappages de sélection et de préhension OpenXRMsftHandInteraction. vous n’avez pas besoin d’activer l’abonnement, vous devez déclarer les événements dans Project Paramètres/Engine/Input, comme suit :

![Capture d’écran des mappages d’actions OpenXR](../images/unreal-hand-tracking-img-12.png)

# <a name="425"></a>[4.25](#tab/425)

vous pouvez trouver la fonction Blueprint dans sous **Windows Mixed Reality entrée spatiale** et la fonction C++ en ajoutant `WindowsMixedRealitySpatialInputFunctionLibrary.h` dans votre fichier de code appelant.

![Capturer les gestes](../images/unreal/capture-gestures.png)

### <a name="enum"></a>Enum
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
Blueprint

![Type de mouvement](../images/unreal/gesture-type.png)

C++ :
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a>Fonction
Vous pouvez activer et désactiver la capture de mouvement avec la `CaptureGestures` fonction. Lorsqu’un mouvement activé déclenche des événements d’entrée, la fonction retourne `true` si la capture de mouvement a réussi, et en `false` cas d’erreur.

Blueprint

![Capturer les gestes BP](../images/unreal/capture-gestures-bp.png)

C++ :
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false,
    bool Hold = false,
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None,
    bool NavigationAxisX = true,
    bool NavigationAxisY = true,
    bool NavigationAxisZ = true);
```

Voici quelques-uns des principaux événements que vous pouvez trouver dans les plans et C++ : ![ événements clés](../images/unreal/key-events.png)

![Événements clés 2](../images/unreal/key-events2.png)
```cpp
const FKey FSpatialInputKeys::TapGesture(TapGestureName);
const FKey FSpatialInputKeys::DoubleTapGesture(DoubleTapGestureName);
const FKey FSpatialInputKeys::HoldGesture(HoldGestureName);

const FKey FSpatialInputKeys::LeftTapGesture(LeftTapGestureName);
const FKey FSpatialInputKeys::LeftDoubleTapGesture(LeftDoubleTapGestureName);
const FKey FSpatialInputKeys::LeftHoldGesture(LeftHoldGestureName);

const FKey FSpatialInputKeys::RightTapGesture(RightTapGestureName);
const FKey FSpatialInputKeys::RightDoubleTapGesture(RightDoubleTapGestureName);
const FKey FSpatialInputKeys::RightHoldGesture(RightHoldGestureName);

const FKey FSpatialInputKeys::LeftManipulationGesture(LeftManipulationGestureName);
const FKey FSpatialInputKeys::LeftManipulationXGesture(LeftManipulationXGestureName);
const FKey FSpatialInputKeys::LeftManipulationYGesture(LeftManipulationYGestureName);
const FKey FSpatialInputKeys::LeftManipulationZGesture(LeftManipulationZGestureName);

const FKey FSpatialInputKeys::LeftNavigationGesture(LeftNavigationGestureName);
const FKey FSpatialInputKeys::LeftNavigationXGesture(LeftNavigationXGestureName);
const FKey FSpatialInputKeys::LeftNavigationYGesture(LeftNavigationYGestureName);
const FKey FSpatialInputKeys::LeftNavigationZGesture(LeftNavigationZGestureName);


const FKey FSpatialInputKeys::RightManipulationGesture(RightManipulationGestureName);
const FKey FSpatialInputKeys::RightManipulationXGesture(RightManipulationXGestureName);
const FKey FSpatialInputKeys::RightManipulationYGesture(RightManipulationYGestureName);
const FKey FSpatialInputKeys::RightManipulationZGesture(RightManipulationZGestureName);

const FKey FSpatialInputKeys::RightNavigationGesture(RightNavigationGestureName);
const FKey FSpatialInputKeys::RightNavigationXGesture(RightNavigationXGestureName);
const FKey FSpatialInputKeys::RightNavigationYGesture(RightNavigationYGestureName);
const FKey FSpatialInputKeys::RightNavigationZGesture(RightNavigationZGestureName);
```

