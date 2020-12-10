---
ms.openlocfilehash: 50b56f6f081f682c3f3655e81aa492d84d254314
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002656"
---
# <a name="425"></a>[<span data-ttu-id="ce2c7-101">4.25</span><span class="sxs-lookup"><span data-stu-id="ce2c7-101">4.25</span></span>](#tab/425)

<span data-ttu-id="ce2c7-102">Vous pouvez trouver la fonction Blueprint dans sous **Windows Mixed Real Input spatial**, et la fonction C++ en ajoutant `WindowsMixedRealitySpatialInputFunctionLibrary.h` dans votre fichier de code appelant.</span><span class="sxs-lookup"><span data-stu-id="ce2c7-102">You can find the Blueprint function in under **Windows Mixed Reality Spatial Input**, and the C++ function by adding `WindowsMixedRealitySpatialInputFunctionLibrary.h` in your calling code file.</span></span>

![Capturer les gestes](../images/unreal/capture-gestures.png)

### <a name="enum"></a><span data-ttu-id="ce2c7-104">Enum</span><span class="sxs-lookup"><span data-stu-id="ce2c7-104">Enum</span></span>
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
<span data-ttu-id="ce2c7-105">Blueprint</span><span class="sxs-lookup"><span data-stu-id="ce2c7-105">Blueprint:</span></span>

![Type de mouvement](../images/unreal/gesture-type.png)

<span data-ttu-id="ce2c7-107">C++ :</span><span class="sxs-lookup"><span data-stu-id="ce2c7-107">C++:</span></span>
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a><span data-ttu-id="ce2c7-108">Fonction</span><span class="sxs-lookup"><span data-stu-id="ce2c7-108">Function</span></span>
<span data-ttu-id="ce2c7-109">Vous pouvez activer et désactiver la capture de mouvement avec la `CaptureGestures` fonction.</span><span class="sxs-lookup"><span data-stu-id="ce2c7-109">You can enable and disable gesture capture with the `CaptureGestures` function.</span></span> <span data-ttu-id="ce2c7-110">Lorsqu’un mouvement activé déclenche des événements d’entrée, la fonction retourne `true` si la capture de mouvement a réussi, et en `false` cas d’erreur.</span><span class="sxs-lookup"><span data-stu-id="ce2c7-110">When an enabled gesture fires input events, the function returns `true` if gesture capture succeeded, and `false` if there's an error.</span></span>

<span data-ttu-id="ce2c7-111">Blueprint</span><span class="sxs-lookup"><span data-stu-id="ce2c7-111">Blueprint:</span></span>

![Capturer les gestes BP](../images/unreal/capture-gestures-bp.png)

<span data-ttu-id="ce2c7-113">C++ :</span><span class="sxs-lookup"><span data-stu-id="ce2c7-113">C++:</span></span>
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false,
    bool Hold = false,
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None,
    bool NavigationAxisX = true,
    bool NavigationAxisY = true,
    bool NavigationAxisZ = true);
```

<span data-ttu-id="ce2c7-114">Voici quelques-uns des principaux événements que vous pouvez trouver dans les plans et C++ : ![ événements clés](../images/unreal/key-events.png)</span><span class="sxs-lookup"><span data-stu-id="ce2c7-114">The following are key events, which you can find in Blueprints and C++: ![Key Events](../images/unreal/key-events.png)</span></span>

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

# <a name="426"></a>[<span data-ttu-id="ce2c7-116">4.26</span><span class="sxs-lookup"><span data-stu-id="ce2c7-116">4.26</span></span>](#tab/426)

### <a name="windows-mixed-reality"></a><span data-ttu-id="ce2c7-117">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ce2c7-117">Windows Mixed Reality</span></span>

![Plan de la lecture de début d’événement connecté à la fonction de configuration des mouvements](../images/unreal-hand-tracking-img-09.png)

<span data-ttu-id="ce2c7-119">Vous devez ensuite ajouter du code pour vous abonner aux événements suivants :</span><span class="sxs-lookup"><span data-stu-id="ce2c7-119">Then you should add code to subscribe to the following events:</span></span>

<span data-ttu-id="ce2c7-120">![Plan de la conservation des entrées spatiales Windows, du robinet et des gestes de manipulation gauche ](../images/unreal/key-events.png)
 ![ capture d’écran des options de mouvement d’entrée spatiale Windows dans le volet d’informations](../images/unreal/key-events2.png)</span><span class="sxs-lookup"><span data-stu-id="ce2c7-120">![Blueprint of Windows spatial input hold, tap, and left manipulation gestures](../images/unreal/key-events.png)
![Screenshot of Windows spatial input tap gesture options in the details panel](../images/unreal/key-events2.png)</span></span>

### <a name="openxr"></a><span data-ttu-id="ce2c7-121">OpenXR</span><span class="sxs-lookup"><span data-stu-id="ce2c7-121">OpenXR</span></span>

<span data-ttu-id="ce2c7-122">Dans OpenXR, les événements de mouvement sont suivis via le pipeline d’entrée.</span><span class="sxs-lookup"><span data-stu-id="ce2c7-122">In OpenXR, gesture events are tracked through the input pipeline.</span></span> <span data-ttu-id="ce2c7-123">À l’aide de l’interaction manuelle, l’appareil peut reconnaître automatiquement les gestes TAP et Hold, mais pas les autres.</span><span class="sxs-lookup"><span data-stu-id="ce2c7-123">Using hand interaction, the device can automatically recognize Tap and Hold gestures, but not the others.</span></span> <span data-ttu-id="ce2c7-124">Elles sont nommées en tant que mappages de sélection et de préhension OpenXRMsftHandInteraction.</span><span class="sxs-lookup"><span data-stu-id="ce2c7-124">They are named as OpenXRMsftHandInteraction Select and Grip mappings.</span></span> <span data-ttu-id="ce2c7-125">Vous n’avez pas besoin d’activer l’abonnement, vous devez déclarer les événements dans paramètres du projet/moteur/entrée, comme suit :</span><span class="sxs-lookup"><span data-stu-id="ce2c7-125">You don’t need to enable subscription, you should declare the events in Project Settings/Engine/Input, just like this:</span></span>

![Capture d’écran des mappages d’actions OpenXR](../images/unreal-hand-tracking-img-12.png)
