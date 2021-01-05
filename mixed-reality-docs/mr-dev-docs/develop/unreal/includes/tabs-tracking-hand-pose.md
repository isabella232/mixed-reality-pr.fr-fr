---
ms.openlocfilehash: c5a13798ca6a73f1a6410abe310c2166b67f4626
ms.sourcegitcommit: 13ef9f89ee61fbfe547ecf5fdfdb97560a0de833
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2020
ms.locfileid: "97717515"
---
# <a name="426"></a>[<span data-ttu-id="4a401-101">4.26</span><span class="sxs-lookup"><span data-stu-id="4a401-101">4.26</span></span>](#tab/426)

<span data-ttu-id="4a401-102">La hiérarchie est décrite par `EHandKeypoint` enum :</span><span class="sxs-lookup"><span data-stu-id="4a401-102">The hierarchy is described by `EHandKeypoint` enum:</span></span>

![Image des options bluprint de KEYpoint de la main](../images/hand-keypoint-bp.png)

<span data-ttu-id="4a401-104">Vous pouvez obtenir toutes ces données à partir de la main d’un utilisateur à l’aide de la fonction de **données obtenir le contrôleur de mouvement** .</span><span class="sxs-lookup"><span data-stu-id="4a401-104">You can get all this data from a user’s hands using the **Get Motion Controller Data** function.</span></span> <span data-ttu-id="4a401-105">Cette fonction retourne une structure **XRMotionControllerData** .</span><span class="sxs-lookup"><span data-stu-id="4a401-105">That function returns an **XRMotionControllerData** structure.</span></span> <span data-ttu-id="4a401-106">Vous trouverez ci-dessous un exemple de script Blueprint qui analyse la structure XRMotionControllerData pour obtenir les emplacements joints et dessine un système de coordonnées de débogage à chaque emplacement de la jointure.</span><span class="sxs-lookup"><span data-stu-id="4a401-106">Below is a sample Blueprint script that parses the XRMotionControllerData structure to get hand joint locations and draws a debug coordinate system at each joint’s location.</span></span>

![Plan de la fonction d’extraction de données de regard connectée à la trace de ligne par fonction de canal](../images/unreal-hand-tracking-img-03.png)

<span data-ttu-id="4a401-108">Il est important de vérifier si la structure est valide et qu’elle est une main.</span><span class="sxs-lookup"><span data-stu-id="4a401-108">It's important to check if the structure is valid and that it's a hand.</span></span> <span data-ttu-id="4a401-109">Dans le cas contraire, vous risquez d’avoir un comportement indéfini dans l’accès aux positions, aux rotations et aux rayons.</span><span class="sxs-lookup"><span data-stu-id="4a401-109">Otherwise, you may get undefined behavior in access to positions, rotations, and radii arrays.</span></span>

# <a name="425"></a>[<span data-ttu-id="4a401-110">4.25</span><span class="sxs-lookup"><span data-stu-id="4a401-110">4.25</span></span>](#tab/425)

<span data-ttu-id="4a401-111">L' `EWMRHandKeypoint` énumération décrit la hiérarchie osseuse de la main.</span><span class="sxs-lookup"><span data-stu-id="4a401-111">The `EWMRHandKeypoint` enum describes the Hand’s bone hierarchy.</span></span> <span data-ttu-id="4a401-112">Chaque KEYpoint est indiqué dans vos projets :</span><span class="sxs-lookup"><span data-stu-id="4a401-112">You can find each hand keypoint listed in your Blueprints:</span></span>

![Main KEYpoint BP](../images/hand-keypoint-bp.png)

<span data-ttu-id="4a401-114">L’énumération C++ complète est listée ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="4a401-114">The full C++ enum is listed below:</span></span>
```cpp
enum class EWMRHandKeypoint : uint8
{
    Palm,
    Wrist,
    ThumbMetacarpal,
    ThumbProximal,
    ThumbDistal,
    ThumbTip,
    IndexMetacarpal,
    IndexProximal,
    IndexIntermediate,
    IndexDistal,
    IndexTip,
    MiddleMetacarpal,
    MiddleProximal,
    MiddleIntermediate,
    MiddleDistal,
    MiddleTip,
    RingMetacarpal,
    RingProximal,
    RingIntermediate,
    RingDistal,
    RingTip,
    LittleMetacarpal,
    LittleProximal,
    LittleIntermediate,
    LittleDistal,
    LittleTip
};
```

<span data-ttu-id="4a401-115">Vous pouvez rechercher les valeurs numériques de chaque cas d’énumération dans la table [Windows. perception. People. HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) .</span><span class="sxs-lookup"><span data-stu-id="4a401-115">You can find the numerical values for each enum case in the [Windows.Perception.People.HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) table.</span></span>

### <a name="supporting-hand-tracking"></a><span data-ttu-id="4a401-116">Prise en charge du suivi des mains</span><span class="sxs-lookup"><span data-stu-id="4a401-116">Supporting Hand Tracking</span></span>

<span data-ttu-id="4a401-117">Vous pouvez utiliser le suivi des mains dans les plans **en ajoutant le suivi de** la main à partir de la **> Windows Mixed Reality**:</span><span class="sxs-lookup"><span data-stu-id="4a401-117">You can use hand tracking in Blueprints by adding **Supports Hand Tracking** from **Hand Tracking > Windows Mixed Reality**:</span></span>

![Suivi de main BP](../images/unreal/hand-tracking-bp.png)

<span data-ttu-id="4a401-119">Cette fonction retourne `true` si le suivi manuel est pris en charge sur l’appareil et `false` si le suivi manuel n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="4a401-119">This function returns `true` if hand tracking is supported on the device and `false` if hand tracking isn't available.</span></span>

![Prend en charge le BP de suivi de main](../images/unreal/supports-hand-tracking-bp.png)

<span data-ttu-id="4a401-121">C++ :</span><span class="sxs-lookup"><span data-stu-id="4a401-121">C++:</span></span>

<span data-ttu-id="4a401-122">Incluez `WindowsMixedRealityHandTrackingFunctionLibrary.h`.</span><span class="sxs-lookup"><span data-stu-id="4a401-122">Include `WindowsMixedRealityHandTrackingFunctionLibrary.h`.</span></span>

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a><span data-ttu-id="4a401-123">Obtenir le suivi de la main</span><span class="sxs-lookup"><span data-stu-id="4a401-123">Getting Hand Tracking</span></span>

<span data-ttu-id="4a401-124">Vous pouvez utiliser **GetHandJointTransform** pour retourner des données spatiales à partir de la main.</span><span class="sxs-lookup"><span data-stu-id="4a401-124">You can use **GetHandJointTransform** to return spatial data from the hand.</span></span> <span data-ttu-id="4a401-125">Les données sont mises à jour chaque trame, mais si vous vous trouvez à l’intérieur d’un frame, les valeurs retournées sont mises en cache.</span><span class="sxs-lookup"><span data-stu-id="4a401-125">The data updates every frame, but if you're inside a frame the returned values are cached.</span></span> <span data-ttu-id="4a401-126">Il n’est pas recommandé d’avoir une logique importante dans cette fonction pour des raisons de performances.</span><span class="sxs-lookup"><span data-stu-id="4a401-126">It's not recommended to have heavy logic in this function for performance reasons.</span></span>

![Faire une transformation conjointe de la main](../images/unreal/get-hand-joint-transform.png)

<span data-ttu-id="4a401-128">C++ :</span><span class="sxs-lookup"><span data-stu-id="4a401-128">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

<span data-ttu-id="4a401-129">Voici une répartition des paramètres de fonction de GetHandJointTransform :</span><span class="sxs-lookup"><span data-stu-id="4a401-129">Here's a breakdown of GetHandJointTransform's function parameters:</span></span>

* <span data-ttu-id="4a401-130">**Main** : peut être l’utilisateur à gauche ou à droite.</span><span class="sxs-lookup"><span data-stu-id="4a401-130">**Hand** – can be the users left or right hand.</span></span>
* <span data-ttu-id="4a401-131">**KEYpoint** : le segment de la main.</span><span class="sxs-lookup"><span data-stu-id="4a401-131">**Keypoint** – the bone of the hand.</span></span>
* <span data-ttu-id="4a401-132">**Transform** : coordonnées et orientation de la base du segment.</span><span class="sxs-lookup"><span data-stu-id="4a401-132">**Transform** – coordinates and orientation of bone’s base.</span></span> <span data-ttu-id="4a401-133">Vous pouvez demander la base du segment suivant pour obtenir les données de transformation pour la fin d’un segment.</span><span class="sxs-lookup"><span data-stu-id="4a401-133">You can request the base of the next bone to get the transform data for the end of a bone.</span></span> <span data-ttu-id="4a401-134">Un segment de pourboire spécial offre une terminaison de distribution.</span><span class="sxs-lookup"><span data-stu-id="4a401-134">A special Tip bone gives end of distal.</span></span>
* <span data-ttu-id="4a401-135">\* \* Rayon : rayon de la base du segment.</span><span class="sxs-lookup"><span data-stu-id="4a401-135">\*\*Radius—radius of the base of the bone.</span></span>
* <span data-ttu-id="4a401-136">\* \* Valeur de retour : true si le segment est suivi dans ce frame, false si le segment n’est pas suivi.</span><span class="sxs-lookup"><span data-stu-id="4a401-136">\*\*Return Value—true if the bone is tracked this frame, false if the bone isn't tracked.</span></span>

