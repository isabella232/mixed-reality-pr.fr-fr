---
ms.openlocfilehash: 23bba22801f61f6b4814991c8b3bde68d2c5f6b7
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002696"
---
# <a name="425"></a>[<span data-ttu-id="31ab2-101">4.25</span><span class="sxs-lookup"><span data-stu-id="31ab2-101">4.25</span></span>](#tab/425)

<span data-ttu-id="31ab2-102">Pour utiliser des rayons de main dans des plans, recherchez l’une des actions sous **Windows Mixed Reality HMD**:</span><span class="sxs-lookup"><span data-stu-id="31ab2-102">To use Hand Rays in Blueprints, search for any of the actions under **Windows Mixed Reality HMD**:</span></span>

![Rayons main BP](../images/unreal/hand-rays-bp.png)

<span data-ttu-id="31ab2-104">Pour y accéder en C++, incluez- `WindowsMixedRealityFunctionLibrary.h` le au début de votre fichier de code appelant.</span><span class="sxs-lookup"><span data-stu-id="31ab2-104">To access them in C++, include `WindowsMixedRealityFunctionLibrary.h` to the top of your calling code file.</span></span>

### <a name="enum"></a><span data-ttu-id="31ab2-105">Enum</span><span class="sxs-lookup"><span data-stu-id="31ab2-105">Enum</span></span>

<span data-ttu-id="31ab2-106">Vous avez également accès aux cas d’entrée sous **EHMDInputControllerButtons**, qui peuvent être utilisés dans les projets :</span><span class="sxs-lookup"><span data-stu-id="31ab2-106">You also have access to input cases under **EHMDInputControllerButtons**, which can be used in Blueprints:</span></span>

![Boutons du contrôleur d’entrée](../images/unreal/input-controller-buttons.png)

<span data-ttu-id="31ab2-108">Pour accéder en C++, utilisez la `EHMDInputControllerButtons` classe enum :</span><span class="sxs-lookup"><span data-stu-id="31ab2-108">For access in C++, use the `EHMDInputControllerButtons` enum class:</span></span>
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

<span data-ttu-id="31ab2-109">Voici une répartition des deux cas d’énumération applicables :</span><span class="sxs-lookup"><span data-stu-id="31ab2-109">Below is a breakdown of the two applicable enum cases:</span></span>

* <span data-ttu-id="31ab2-110">**Select** -User a déclenché l’événement Select.</span><span class="sxs-lookup"><span data-stu-id="31ab2-110">**Select** - User triggered Select event.</span></span>
    * <span data-ttu-id="31ab2-111">Déclenché dans HoloLens 2 par l’air-TAP, le point de regard et la validation, ou en disant « SELECT » avec l' [entrée vocale](../unreal-voice-input.md) activée.</span><span class="sxs-lookup"><span data-stu-id="31ab2-111">Triggered in HoloLens 2 by air-tap, gaze, and commit, or by saying “Select” with [voice input](../unreal-voice-input.md) enabled.</span></span>
* <span data-ttu-id="31ab2-112">Événement **de préhension déclenché** par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="31ab2-112">**Grasp** - User triggered Grasp event.</span></span>
    * <span data-ttu-id="31ab2-113">Déclenché dans HoloLens 2 en fermant les doigts de l’utilisateur sur un hologramme.</span><span class="sxs-lookup"><span data-stu-id="31ab2-113">Triggered in HoloLens 2 by closing the user’s fingers on a hologram.</span></span>

<span data-ttu-id="31ab2-114">Vous pouvez accéder à l’état de suivi de votre maille de main en C++ via l' `EHMDTrackingStatus` énumération illustrée ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="31ab2-114">You can access the tracking status of your hand mesh in C++ through the `EHMDTrackingStatus` enum shown below:</span></span>

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

<span data-ttu-id="31ab2-115">Voici une répartition des deux cas d’énumération applicables :</span><span class="sxs-lookup"><span data-stu-id="31ab2-115">Below is a breakdown of the two applicable enum cases:</span></span>

* <span data-ttu-id="31ab2-116">**NotTracked** – la main n’est pas visible</span><span class="sxs-lookup"><span data-stu-id="31ab2-116">**NotTracked** –- the hand isn’t visible</span></span>
* <span data-ttu-id="31ab2-117">**Suivi** : la main est entièrement suivie</span><span class="sxs-lookup"><span data-stu-id="31ab2-117">**Tracked** –- the hand is fully tracked</span></span>

### <a name="struct"></a><span data-ttu-id="31ab2-118">Structure</span><span class="sxs-lookup"><span data-stu-id="31ab2-118">Struct</span></span>

<span data-ttu-id="31ab2-119">Le struct PointerPoseInfo peut vous donner des informations sur les données suivantes :</span><span class="sxs-lookup"><span data-stu-id="31ab2-119">The PointerPoseInfo struct can give you information on the following hand data:</span></span>

* <span data-ttu-id="31ab2-120">**Origin** : origine de la main</span><span class="sxs-lookup"><span data-stu-id="31ab2-120">**Origin** – origin of the hand</span></span>
* <span data-ttu-id="31ab2-121">**Direction** : direction de la main</span><span class="sxs-lookup"><span data-stu-id="31ab2-121">**Direction** – direction of the hand</span></span>
* <span data-ttu-id="31ab2-122">**Haut** -vecteur de la main</span><span class="sxs-lookup"><span data-stu-id="31ab2-122">**Up** – up vector of the hand</span></span>
* <span data-ttu-id="31ab2-123">**Orientation** -Quaternion d’orientation</span><span class="sxs-lookup"><span data-stu-id="31ab2-123">**Orientation** – orientation quaternion</span></span>
* <span data-ttu-id="31ab2-124">**État du suivi** – État du suivi actuel</span><span class="sxs-lookup"><span data-stu-id="31ab2-124">**Tracking Status** – current tracking status</span></span>

<span data-ttu-id="31ab2-125">Vous pouvez accéder au struct PointerPoseInfo par le biais de plans, comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="31ab2-125">You can access the PointerPoseInfo struct through Blueprints, as shown below:</span></span>

![Informations de pose du pointeur BP](../images/unreal/pointer-pose-info-bp.png)

<span data-ttu-id="31ab2-127">Ou avec C++ :</span><span class="sxs-lookup"><span data-stu-id="31ab2-127">Or with C++:</span></span>

```cpp
struct FPointerPoseInfo
{
    FVector Origin;
    FVector Direction;
    FVector Up;
    FQuat Orientation;
    EHMDTrackingStatus TrackingStatus;
};
```

### <a name="functions"></a><span data-ttu-id="31ab2-128">Fonctions</span><span class="sxs-lookup"><span data-stu-id="31ab2-128">Functions</span></span>

<span data-ttu-id="31ab2-129">Toutes les fonctions listées ci-dessous peuvent être appelées sur chaque trame, ce qui permet une surveillance continue.</span><span class="sxs-lookup"><span data-stu-id="31ab2-129">All of the functions listed below can be called on every frame, which allows continuous monitoring.</span></span>

1. <span data-ttu-id="31ab2-130">Obtenir les informations sur les **poses du pointeur** retourne des informations complètes sur la direction du rayon de la main dans le frame actuel.</span><span class="sxs-lookup"><span data-stu-id="31ab2-130">**Get Pointer Pose Info** returns complete information about the hand ray direction in the current frame.</span></span>

<span data-ttu-id="31ab2-131">Blueprint</span><span class="sxs-lookup"><span data-stu-id="31ab2-131">Blueprint:</span></span>

![Obtient les informations de pose du pointeur](../images/unreal/get-pointer-pose-info.png)

<span data-ttu-id="31ab2-133">C++ :</span><span class="sxs-lookup"><span data-stu-id="31ab2-133">C++:</span></span>
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. <span data-ttu-id="31ab2-134">**Est saisi** retourne la valeur true si la main est prélevée dans le frame actuel.</span><span class="sxs-lookup"><span data-stu-id="31ab2-134">**Is Grasped** returns true if the hand is grasped in the current frame.</span></span>

<span data-ttu-id="31ab2-135">Blueprint</span><span class="sxs-lookup"><span data-stu-id="31ab2-135">Blueprint:</span></span>

![Est saisi BP](../images/unreal/is-grasped-bp.png)

<span data-ttu-id="31ab2-137">C++ :</span><span class="sxs-lookup"><span data-stu-id="31ab2-137">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```

3. <span data-ttu-id="31ab2-138">**Select enfoncée** retourne la valeur true si l’utilisateur a déclenché SELECT dans le frame actuel.</span><span class="sxs-lookup"><span data-stu-id="31ab2-138">**Is Select Pressed** returns true if the user triggered Select in the current frame.</span></span>

<span data-ttu-id="31ab2-139">Blueprint</span><span class="sxs-lookup"><span data-stu-id="31ab2-139">Blueprint:</span></span>

![Est sélectionner un fond de panier appuyé](../images/unreal/is-select-pressed-bp.png)

<span data-ttu-id="31ab2-141">C++ :</span><span class="sxs-lookup"><span data-stu-id="31ab2-141">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. <span data-ttu-id="31ab2-142">L' **utilisateur clique sur un bouton** retourne la valeur true si l’événement ou le bouton est déclenché dans le frame actuel.</span><span class="sxs-lookup"><span data-stu-id="31ab2-142">**Is Button Clicked** returns true if the event or button is triggered in the current frame.</span></span>

<span data-ttu-id="31ab2-143">Blueprint</span><span class="sxs-lookup"><span data-stu-id="31ab2-143">Blueprint:</span></span>

![Clic sur le bouton de la BP](../images/unreal/is-button-clicked-bp.png)

<span data-ttu-id="31ab2-145">C++ :</span><span class="sxs-lookup"><span data-stu-id="31ab2-145">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. <span data-ttu-id="31ab2-146">L' **État du suivi des contrôleurs** retourne l’état de suivi dans le frame actuel.</span><span class="sxs-lookup"><span data-stu-id="31ab2-146">**Get Controller Tracking Status** returns the tracking status in the current frame.</span></span>

<span data-ttu-id="31ab2-147">Blueprint</span><span class="sxs-lookup"><span data-stu-id="31ab2-147">Blueprint:</span></span>

![Obtient l’état du suivi du contrôleur BP](../images/unreal/get-controller-tracking-status-bp.png)

<span data-ttu-id="31ab2-149">C++ :</span><span class="sxs-lookup"><span data-stu-id="31ab2-149">C++:</span></span>
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```
# <a name="426"></a>[<span data-ttu-id="31ab2-150">4.26</span><span class="sxs-lookup"><span data-stu-id="31ab2-150">4.26</span></span>](#tab/426)

<span data-ttu-id="31ab2-151">Pour obtenir les données des rayons de la main, vous devez utiliser la fonction de données obtenir le contrôleur de mouvement de la section précédente.</span><span class="sxs-lookup"><span data-stu-id="31ab2-151">To get the data for the hand rays, you should use the Get Motion Controller Data function from the previous section.</span></span> <span data-ttu-id="31ab2-152">La structure retournée contient deux paramètres que vous pouvez utiliser pour créer un rayon **et une** **rotation AIM**.</span><span class="sxs-lookup"><span data-stu-id="31ab2-152">The returned structure contains two parameters you can use to create a hand ray – **Aim Position** and **Aim Rotation**.</span></span> <span data-ttu-id="31ab2-153">Ces paramètres forment un rayon dirigé par votre coude.</span><span class="sxs-lookup"><span data-stu-id="31ab2-153">These parameters form a ray directed by your elbow.</span></span> <span data-ttu-id="31ab2-154">Vous devez les prendre et trouver un hologramme pointé par.</span><span class="sxs-lookup"><span data-stu-id="31ab2-154">You should take them and find a hologram being pointed by.</span></span>

<span data-ttu-id="31ab2-155">Voici un exemple qui montre comment déterminer si un rayon de main atteint un widget et comment définir un résultat d’accès personnalisé :</span><span class="sxs-lookup"><span data-stu-id="31ab2-155">Below is an example of determining whether a hand ray hits a Widget and setting a custom hit result:</span></span>

![Plan de la fonction de données de l’extraction de contrôle de mouvement](../images/unreal-hand-tracking-img-04.png) 