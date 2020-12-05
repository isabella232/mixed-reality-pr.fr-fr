---
title: Suivi de la main dans Unreal
description: Explique comment utiliser le suivi des handles en mode inréel
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, suivi manuel, non réel, UE4, HoloLens, HoloLens 2, réalité mixte, développement, fonctionnalités, documentation, guides, hologrammes, développement de jeux, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle
ms.openlocfilehash: 4c66e2353c1e881c05541fd0fe9eafa553ea5c23
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609710"
---
# <a name="hand-tracking-in-unreal"></a><span data-ttu-id="82127-104">Suivi de la main dans Unreal</span><span class="sxs-lookup"><span data-stu-id="82127-104">Hand tracking in Unreal</span></span>

<span data-ttu-id="82127-105">Le système de suivi de la main utilise les paumes et les doigts d’une personne comme entrée.</span><span class="sxs-lookup"><span data-stu-id="82127-105">The hand tracking system uses a person’s palms and fingers as input.</span></span> <span data-ttu-id="82127-106">Les données sur la position et la rotation de chaque doigt, le Palm entier et les gestes manuel sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="82127-106">Data on position and rotation of every finger, the entire palm, and hand gestures is available.</span></span> 

## <a name="hand-pose"></a><span data-ttu-id="82127-107">Poser à la main</span><span class="sxs-lookup"><span data-stu-id="82127-107">Hand Pose</span></span>

<span data-ttu-id="82127-108">La pose de main vous permet de suivre et d’utiliser les mains et les doigts de vos utilisateurs comme entrée.</span><span class="sxs-lookup"><span data-stu-id="82127-108">Hand pose lets you track and use the hands and fingers of your users as input.</span></span> <span data-ttu-id="82127-109">Vous pouvez accéder aux données de suivi à la fois dans les plans et C++.</span><span class="sxs-lookup"><span data-stu-id="82127-109">You can access tracking data both in Blueprints and C++.</span></span> <span data-ttu-id="82127-110">Vous trouverez plus de détails techniques dans l’API [Windows. perception. People. HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) .</span><span class="sxs-lookup"><span data-stu-id="82127-110">You can find more technical details in Unreal's [Windows.Perception.People.HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) API.</span></span> <span data-ttu-id="82127-111">L’API inréelle envoie les données sous forme de système de coordonnées, avec les battements synchronisés avec le moteur inréel.</span><span class="sxs-lookup"><span data-stu-id="82127-111">The Unreal API sends the data as a coordinate system, with ticks synchronized with the Unreal Engine.</span></span>

### <a name="understanding-the-bone-hierarchy"></a><span data-ttu-id="82127-112">Fonctionnement de la hiérarchie osseuse</span><span class="sxs-lookup"><span data-stu-id="82127-112">Understanding the bone hierarchy</span></span>

<span data-ttu-id="82127-113">L' `EWMRHandKeypoint` énumération décrit la hiérarchie osseuse de la main.</span><span class="sxs-lookup"><span data-stu-id="82127-113">The `EWMRHandKeypoint` enum describes the Hand’s bone hierarchy.</span></span> <span data-ttu-id="82127-114">Chaque KEYpoint est indiqué dans vos projets :</span><span class="sxs-lookup"><span data-stu-id="82127-114">You can find each hand keypoint listed in your Blueprints:</span></span>

![Main KEYpoint BP](images/hand-keypoint-bp.png)

<span data-ttu-id="82127-116">L’énumération C++ complète est listée ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="82127-116">The full C++ enum is listed below:</span></span>
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

<span data-ttu-id="82127-117">Vous pouvez rechercher les valeurs numériques de chaque cas d’énumération dans la table [Windows. perception. People. HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) .</span><span class="sxs-lookup"><span data-stu-id="82127-117">You can find the numerical values for each enum case in the [Windows.Perception.People.HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) table.</span></span> <span data-ttu-id="82127-118">La disposition complète avec les cas d’énumération correspondants est illustrée dans l’image ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="82127-118">The entire hand pose layout with matching enum cases is shown in the image below:</span></span>

![Squelette de main](../native/images/hand-skeleton.png)
 
### <a name="supporting-hand-tracking"></a><span data-ttu-id="82127-120">Prise en charge du suivi des mains</span><span class="sxs-lookup"><span data-stu-id="82127-120">Supporting Hand Tracking</span></span>

<span data-ttu-id="82127-121">Vous pouvez utiliser le suivi des mains dans les plans **en ajoutant le suivi de** la main à partir de la **> Windows Mixed Reality**:</span><span class="sxs-lookup"><span data-stu-id="82127-121">You can use hand tracking in Blueprints by adding **Supports Hand Tracking** from **Hand Tracking > Windows Mixed Reality**:</span></span>

![Suivi de main BP](images/unreal/hand-tracking-bp.png)

<span data-ttu-id="82127-123">Cette fonction retourne `true` si le suivi manuel est pris en charge sur l’appareil et `false` si le suivi manuel n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="82127-123">This function returns `true` if hand tracking is supported on the device and `false` if hand tracking isn't available.</span></span>

![Prend en charge le BP de suivi de main](images/unreal/supports-hand-tracking-bp.png)

<span data-ttu-id="82127-125">C++ :</span><span class="sxs-lookup"><span data-stu-id="82127-125">C++:</span></span> 

<span data-ttu-id="82127-126">Incluez `WindowsMixedRealityHandTrackingFunctionLibrary.h`.</span><span class="sxs-lookup"><span data-stu-id="82127-126">Include `WindowsMixedRealityHandTrackingFunctionLibrary.h`.</span></span>

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a><span data-ttu-id="82127-127">Obtenir le suivi de la main</span><span class="sxs-lookup"><span data-stu-id="82127-127">Getting Hand Tracking</span></span>

<span data-ttu-id="82127-128">Vous pouvez utiliser **GetHandJointTransform** pour retourner des données spatiales à partir de la main.</span><span class="sxs-lookup"><span data-stu-id="82127-128">You can use **GetHandJointTransform** to return spatial data from the hand.</span></span> <span data-ttu-id="82127-129">Les données sont mises à jour chaque trame, mais si vous vous trouvez à l’intérieur d’un frame, les valeurs retournées sont mises en cache.</span><span class="sxs-lookup"><span data-stu-id="82127-129">The data updates every frame, but if you're inside a frame the returned values are cached.</span></span> <span data-ttu-id="82127-130">Il n’est pas recommandé d’avoir une logique importante dans cette fonction pour des raisons de performances.</span><span class="sxs-lookup"><span data-stu-id="82127-130">It's not recommended to have heavy logic in this function for performance reasons.</span></span> 

![Faire une transformation conjointe de la main](images/unreal/get-hand-joint-transform.png)
 
<span data-ttu-id="82127-132">C++ :</span><span class="sxs-lookup"><span data-stu-id="82127-132">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

<span data-ttu-id="82127-133">Voici une répartition des paramètres de fonction de GetHandJointTransform :</span><span class="sxs-lookup"><span data-stu-id="82127-133">Here's a breakdown of GetHandJointTransform's function parameters:</span></span>

* <span data-ttu-id="82127-134">**Main** : peut être l’utilisateur à gauche ou à droite.</span><span class="sxs-lookup"><span data-stu-id="82127-134">**Hand** – can be the users left or right hand.</span></span>
* <span data-ttu-id="82127-135">**KEYpoint** : le segment de la main.</span><span class="sxs-lookup"><span data-stu-id="82127-135">**Keypoint** – the bone of the hand.</span></span> 
* <span data-ttu-id="82127-136">**Transform** : coordonnées et orientation de la base du segment.</span><span class="sxs-lookup"><span data-stu-id="82127-136">**Transform** – coordinates and orientation of bone’s base.</span></span> <span data-ttu-id="82127-137">Vous pouvez demander la base du segment suivant pour obtenir les données de transformation pour la fin d’un segment.</span><span class="sxs-lookup"><span data-stu-id="82127-137">You can request the base of the next bone to get the transform data for the end of a bone.</span></span> <span data-ttu-id="82127-138">Un segment de pourboire spécial offre une terminaison de distribution.</span><span class="sxs-lookup"><span data-stu-id="82127-138">A special Tip bone gives end of distal.</span></span> 
* <span data-ttu-id="82127-139">**Rayon** : rayon de la base du segment.</span><span class="sxs-lookup"><span data-stu-id="82127-139">**Radius** — radius of the base of the bone.</span></span>
* <span data-ttu-id="82127-140">**Valeur de retour** : true si le segment est suivi dans ce frame, false si le segment n’est pas suivi.</span><span class="sxs-lookup"><span data-stu-id="82127-140">**Return Value** — true if the bone is tracked this frame, false if the bone isn't tracked.</span></span>

## <a name="hand-live-link-animation"></a><span data-ttu-id="82127-141">Animation de lien dynamique à la main</span><span class="sxs-lookup"><span data-stu-id="82127-141">Hand Live Link Animation</span></span>

<span data-ttu-id="82127-142">Les poses de main sont exposées à l’animation à l’aide du [plug-in Live Link](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).</span><span class="sxs-lookup"><span data-stu-id="82127-142">Hand poses are exposed to Animation using the [Live Link plugin](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).</span></span>

<span data-ttu-id="82127-143">Si les plug-ins Windows Mixed Reality et Live Link sont activés :</span><span class="sxs-lookup"><span data-stu-id="82127-143">If the Windows Mixed Reality and Live Link plugins are enabled:</span></span> 
1. <span data-ttu-id="82127-144">Sélectionnez **fenêtre > lien dynamique** pour ouvrir la fenêtre de l’éditeur de liens actifs.</span><span class="sxs-lookup"><span data-stu-id="82127-144">Select **Window > Live Link** to open the Live Link editor window.</span></span> 
2. <span data-ttu-id="82127-145">Sélectionner la **source** et activer la source de suivi de la **main Windows Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="82127-145">Select **Source** and enable **Windows Mixed Reality Hand Tracking Source**</span></span>

![Source de la liaison dynamique](images/unreal/live-link-source.png)
 
<span data-ttu-id="82127-147">Une fois que vous avez activé la source et ouvert une ressource d’animation, développez la section **animation** sous l’onglet Aperçu de la **scène** . vous pouvez également voir d’autres options.</span><span class="sxs-lookup"><span data-stu-id="82127-147">After you enable the source and open an animation asset, expand the **Animation** section in the **Preview Scene** tab too see additional options.</span></span>

![Animation des liens dynamiques](images/unreal/live-link-animation.png)
 
<span data-ttu-id="82127-149">La hiérarchie d’animation manuelle est la même que dans `EWMRHandKeypoint` .</span><span class="sxs-lookup"><span data-stu-id="82127-149">The hand animation hierarchy is the same as in `EWMRHandKeypoint`.</span></span> <span data-ttu-id="82127-150">L’animation peut être reciblée à l’aide de **WindowsMixedRealityHandTrackingLiveLinkRemapAsset**:</span><span class="sxs-lookup"><span data-stu-id="82127-150">Animation can be retargeted using **WindowsMixedRealityHandTrackingLiveLinkRemapAsset**:</span></span>

![Animation de lien dynamique 2](images/unreal/live-link-animation2.png)
 
<span data-ttu-id="82127-152">Elle peut également être sous-classée dans l’éditeur :</span><span class="sxs-lookup"><span data-stu-id="82127-152">It can also be subclassed in the editor:</span></span>

![Remappage de liaison dynamique](images/unreal/live-link-remap.png)
 
## <a name="accessing-hand-mesh-data"></a><span data-ttu-id="82127-154">Accès aux données de maillage de la main</span><span class="sxs-lookup"><span data-stu-id="82127-154">Accessing Hand Mesh Data</span></span>

![Maille manuelle](images/unreal/hand-mesh.png)

<span data-ttu-id="82127-156">Avant de pouvoir accéder aux données de maillage manuel, vous devez :</span><span class="sxs-lookup"><span data-stu-id="82127-156">Before you can access hand mesh data, you'll need to:</span></span>
- <span data-ttu-id="82127-157">Sélectionnez votre ressource **ARSessionConfig** , développez les **paramètres AR-> World Mapping** Settings, puis cochez la case **générer des données de maillage à partir de la géométrie suivie**.</span><span class="sxs-lookup"><span data-stu-id="82127-157">Select your **ARSessionConfig** asset, expand the **AR Settings -> World Mapping** settings, and check **Generate Mesh Data from Tracked Geometry**.</span></span> 

<span data-ttu-id="82127-158">Voici les paramètres de maillage par défaut :</span><span class="sxs-lookup"><span data-stu-id="82127-158">Below are the default mesh parameters:</span></span>

1.  <span data-ttu-id="82127-159">Utiliser les données de maillage pour l’occlusion</span><span class="sxs-lookup"><span data-stu-id="82127-159">Use Mesh Data for Occlusion</span></span>
2.  <span data-ttu-id="82127-160">Générer une collision pour les données de maillage</span><span class="sxs-lookup"><span data-stu-id="82127-160">Generate Collision for Mesh Data</span></span>
3.  <span data-ttu-id="82127-161">Générer un maillage de navigation pour les données de maillage</span><span class="sxs-lookup"><span data-stu-id="82127-161">Generate Nav Mesh for Mesh Data</span></span>
4.  <span data-ttu-id="82127-162">Rendu des données de maillage dans le paramètre filaire – débogage qui affiche le maillage généré</span><span class="sxs-lookup"><span data-stu-id="82127-162">Render Mesh Data in Wireframe – debug parameter that shows generated mesh</span></span>

<span data-ttu-id="82127-163">Ces valeurs de paramètre sont utilisées comme maillage de mappage spatial et par défaut.</span><span class="sxs-lookup"><span data-stu-id="82127-163">These parameter values are used as the spatial mapping mesh and hand mesh defaults.</span></span> <span data-ttu-id="82127-164">Vous pouvez les modifier à tout moment dans des plans ou du code pour n’importe quelle maille.</span><span class="sxs-lookup"><span data-stu-id="82127-164">You can change them at any time in Blueprints or code for any mesh.</span></span>

### <a name="c-api-reference"></a><span data-ttu-id="82127-165">Informations de référence sur l’API C++</span><span class="sxs-lookup"><span data-stu-id="82127-165">C++ API Reference</span></span> 
<span data-ttu-id="82127-166">Utilisez `EEARObjectClassification` pour rechercher des valeurs de maillage de main dans tous les objets suivis.</span><span class="sxs-lookup"><span data-stu-id="82127-166">Use `EEARObjectClassification` to find hand mesh values in all trackable objects.</span></span>
```cpp
enum class EARObjectClassification : uint8
{
    // Other types 
    HandMesh,
};
```

<span data-ttu-id="82127-167">Les délégués suivants sont appelés lorsque le système détecte tout objet suivi, y compris un maillage de main.</span><span class="sxs-lookup"><span data-stu-id="82127-167">The following delegates are called when the system detects any trackable object, including a hand mesh.</span></span> 

```cpp
class FARSupportInterface 
{
    public:
    // Other params 
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

<span data-ttu-id="82127-168">Assurez-vous que vos gestionnaires de délégués suivent la signature de la fonction ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="82127-168">Make sure your delegate handlers follow the function signature below:</span></span>

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

<span data-ttu-id="82127-169">Vous pouvez accéder aux données de maillage par le biais des  `UARTrackedGeometry::GetUnderlyingMesh` éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="82127-169">You can access mesh data through the  `UARTrackedGeometry::GetUnderlyingMesh`:</span></span>

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```


### <a name="blueprint-api-reference"></a><span data-ttu-id="82127-170">Informations de référence sur l’API Blueprint</span><span class="sxs-lookup"><span data-stu-id="82127-170">Blueprint API Reference</span></span>

<span data-ttu-id="82127-171">Pour travailler avec des maillages de main dans des plans :</span><span class="sxs-lookup"><span data-stu-id="82127-171">To work with Hand Meshes in Blueprints:</span></span>
1. <span data-ttu-id="82127-172">Ajouter un composant **ARTrackableNotify** à un acteur Blueprint</span><span class="sxs-lookup"><span data-stu-id="82127-172">Add an **ARTrackableNotify** Component to a Blueprint actor</span></span>

![Notification ARTrackable](images/unreal/ar-trackable-notify.png)
 
2. <span data-ttu-id="82127-174">Accédez au panneau des **Détails** et développez la section **événements** .</span><span class="sxs-lookup"><span data-stu-id="82127-174">Go to the **Details** panel and expand the **Events** section.</span></span> 

![ARTrackable Notify 2](images/unreal/ar-trackable-notify2.png)
 
3. <span data-ttu-id="82127-176">Remplacer sur l’ajout/la mise à jour/suppression de la géométrie suivie avec les nœuds suivants dans votre graphique d’événements :</span><span class="sxs-lookup"><span data-stu-id="82127-176">Overwrite On Add/Update/Remove Tracked Geometry with the following nodes in your Event Graph:</span></span>

![Sur ARTrackable Notify](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a><span data-ttu-id="82127-178">Rayons de main</span><span class="sxs-lookup"><span data-stu-id="82127-178">Hand Rays</span></span>

<span data-ttu-id="82127-179">Vous pouvez utiliser un Ray comme dispositif de pointage à la fois dans le C++ et dans les plans, ce qui expose l’API [Windows. UI. Input. spatial. SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) .</span><span class="sxs-lookup"><span data-stu-id="82127-179">You can use a hand ray as a pointing device in both C++ and Blueprints, which exposes the [Windows.UI.Input.Spatial.SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) API.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="82127-180">Étant donné que tous les résultats de fonction changent chaque frame, ils sont tous rendus accessibles.</span><span class="sxs-lookup"><span data-stu-id="82127-180">Since all function results change every frame, they're all made callable.</span></span> <span data-ttu-id="82127-181">Pour plus d’informations sur les fonctions pures et impures ou pouvant être appelées, consultez le Guide de l’utilisateur Blueprint sur les [fonctions](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure).</span><span class="sxs-lookup"><span data-stu-id="82127-181">For more information about pure and impure or callable functions, see the Blueprint user guid on [functions](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure).</span></span>

<span data-ttu-id="82127-182">Pour utiliser des rayons de main dans des plans, recherchez l’une des actions sous **Windows Mixed Reality HMD**:</span><span class="sxs-lookup"><span data-stu-id="82127-182">To use Hand Rays in Blueprints, search for any of the actions under **Windows Mixed Reality HMD**:</span></span>

![Rayons main BP](images/unreal/hand-rays-bp.png)
 
<span data-ttu-id="82127-184">Pour y accéder en C++, incluez- `WindowsMixedRealityFunctionLibrary.h` le au début de votre fichier de code appelant.</span><span class="sxs-lookup"><span data-stu-id="82127-184">To access them in C++, include `WindowsMixedRealityFunctionLibrary.h` to the top of your calling code file.</span></span>

### <a name="enum"></a><span data-ttu-id="82127-185">Énumération</span><span class="sxs-lookup"><span data-stu-id="82127-185">Enum</span></span>

<span data-ttu-id="82127-186">Vous avez également accès aux cas d’entrée sous **EHMDInputControllerButtons**, qui peuvent être utilisés dans les projets :</span><span class="sxs-lookup"><span data-stu-id="82127-186">You also have access to input cases under **EHMDInputControllerButtons**, which can be used in Blueprints:</span></span>

![Boutons du contrôleur d’entrée](images/unreal/input-controller-buttons.png)

<span data-ttu-id="82127-188">Pour accéder en C++, utilisez la `EHMDInputControllerButtons` classe enum :</span><span class="sxs-lookup"><span data-stu-id="82127-188">For access in C++, use the `EHMDInputControllerButtons` enum class:</span></span>
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

<span data-ttu-id="82127-189">Voici une répartition des deux cas d’énumération applicables :</span><span class="sxs-lookup"><span data-stu-id="82127-189">Below is a breakdown of the two applicable enum cases:</span></span>

* <span data-ttu-id="82127-190">**Select** -User a déclenché l’événement Select.</span><span class="sxs-lookup"><span data-stu-id="82127-190">**Select** - User triggered Select event.</span></span> 
    * <span data-ttu-id="82127-191">Déclenché dans HoloLens 2 par l’air-TAP, le point de regard et la validation, ou en disant « SELECT » avec l' [entrée vocale](unreal-voice-input.md) activée.</span><span class="sxs-lookup"><span data-stu-id="82127-191">Triggered in HoloLens 2 by air-tap, gaze, and commit, or by saying “Select” with [voice input](unreal-voice-input.md) enabled.</span></span> 
* <span data-ttu-id="82127-192">Événement **de préhension déclenché** par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="82127-192">**Grasp** - User triggered Grasp event.</span></span> 
    * <span data-ttu-id="82127-193">Déclenché dans HoloLens 2 en fermant les doigts de l’utilisateur sur un hologramme.</span><span class="sxs-lookup"><span data-stu-id="82127-193">Triggered in HoloLens 2 by closing the user’s fingers on a hologram.</span></span> 

<span data-ttu-id="82127-194">Vous pouvez accéder à l’état de suivi de votre maille de main en C++ via l' `EHMDTrackingStatus` énumération illustrée ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="82127-194">You can access the tracking status of your hand mesh in C++ through the `EHMDTrackingStatus` enum shown below:</span></span>

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

<span data-ttu-id="82127-195">Voici une répartition des deux cas d’énumération applicables :</span><span class="sxs-lookup"><span data-stu-id="82127-195">Below is a breakdown of the two applicable enum cases:</span></span>

* <span data-ttu-id="82127-196">**NotTracked** – la main n’est pas visible</span><span class="sxs-lookup"><span data-stu-id="82127-196">**NotTracked** –- the hand isn’t visible</span></span>
* <span data-ttu-id="82127-197">**Suivi** : la main est entièrement suivie</span><span class="sxs-lookup"><span data-stu-id="82127-197">**Tracked** –- the hand is fully tracked</span></span>

### <a name="struct"></a><span data-ttu-id="82127-198">Structure</span><span class="sxs-lookup"><span data-stu-id="82127-198">Struct</span></span>

<span data-ttu-id="82127-199">Le struct PointerPoseInfo peut vous donner des informations sur les données suivantes :</span><span class="sxs-lookup"><span data-stu-id="82127-199">The PointerPoseInfo struct can give you information on the following hand data:</span></span>

* <span data-ttu-id="82127-200">**Origin** : origine de la main</span><span class="sxs-lookup"><span data-stu-id="82127-200">**Origin** – origin of the hand</span></span>
* <span data-ttu-id="82127-201">**Direction** : direction de la main</span><span class="sxs-lookup"><span data-stu-id="82127-201">**Direction** – direction of the hand</span></span>
* <span data-ttu-id="82127-202">**Haut** -vecteur de la main</span><span class="sxs-lookup"><span data-stu-id="82127-202">**Up** – up vector of the hand</span></span>
* <span data-ttu-id="82127-203">**Orientation** -Quaternion d’orientation</span><span class="sxs-lookup"><span data-stu-id="82127-203">**Orientation** – orientation quaternion</span></span> 
* <span data-ttu-id="82127-204">**État du suivi** – État du suivi actuel</span><span class="sxs-lookup"><span data-stu-id="82127-204">**Tracking Status** – current tracking status</span></span>

<span data-ttu-id="82127-205">Vous pouvez accéder au struct PointerPoseInfo par le biais de plans, comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="82127-205">You can access the PointerPoseInfo struct through Blueprints, as shown below:</span></span>

![Informations de pose du pointeur BP](images/unreal/pointer-pose-info-bp.png)

<span data-ttu-id="82127-207">Ou avec C++ :</span><span class="sxs-lookup"><span data-stu-id="82127-207">Or with C++:</span></span>

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

### <a name="functions"></a><span data-ttu-id="82127-208">Fonctions</span><span class="sxs-lookup"><span data-stu-id="82127-208">Functions</span></span>

<span data-ttu-id="82127-209">Toutes les fonctions listées ci-dessous peuvent être appelées sur chaque trame, ce qui permet une surveillance continue.</span><span class="sxs-lookup"><span data-stu-id="82127-209">All of the functions listed below can be called on every frame, which allows continuous monitoring.</span></span> 

1. <span data-ttu-id="82127-210">Obtenir les informations sur les **poses du pointeur** retourne des informations complètes sur la direction du rayon de la main dans le frame actuel.</span><span class="sxs-lookup"><span data-stu-id="82127-210">**Get Pointer Pose Info** returns complete information about the hand ray direction in the current frame.</span></span> 

<span data-ttu-id="82127-211">Blueprint</span><span class="sxs-lookup"><span data-stu-id="82127-211">Blueprint:</span></span>

![Obtient les informations de pose du pointeur](images/unreal/get-pointer-pose-info.png)

<span data-ttu-id="82127-213">C++ :</span><span class="sxs-lookup"><span data-stu-id="82127-213">C++:</span></span> 
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. <span data-ttu-id="82127-214">**Est saisi** retourne la valeur true si la main est prélevée dans le frame actuel.</span><span class="sxs-lookup"><span data-stu-id="82127-214">**Is Grasped** returns true if the hand is grasped in the current frame.</span></span>

<span data-ttu-id="82127-215">Blueprint</span><span class="sxs-lookup"><span data-stu-id="82127-215">Blueprint:</span></span>

![Est saisi BP](images/unreal/is-grasped-bp.png)

<span data-ttu-id="82127-217">C++ :</span><span class="sxs-lookup"><span data-stu-id="82127-217">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
 
3. <span data-ttu-id="82127-218">**Select enfoncée** retourne la valeur true si l’utilisateur a déclenché SELECT dans le frame actuel.</span><span class="sxs-lookup"><span data-stu-id="82127-218">**Is Select Pressed** returns true if the user triggered Select in the current frame.</span></span>

<span data-ttu-id="82127-219">Blueprint</span><span class="sxs-lookup"><span data-stu-id="82127-219">Blueprint:</span></span>

![Est sélectionner un fond de panier appuyé](images/unreal/is-select-pressed-bp.png)

<span data-ttu-id="82127-221">C++ :</span><span class="sxs-lookup"><span data-stu-id="82127-221">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. <span data-ttu-id="82127-222">L' **utilisateur clique sur un bouton** retourne la valeur true si l’événement ou le bouton est déclenché dans le frame actuel.</span><span class="sxs-lookup"><span data-stu-id="82127-222">**Is Button Clicked** returns true if the event or button is triggered in the current frame.</span></span>

<span data-ttu-id="82127-223">Blueprint</span><span class="sxs-lookup"><span data-stu-id="82127-223">Blueprint:</span></span>

![Clic sur le bouton de la BP](images/unreal/is-button-clicked-bp.png)

<span data-ttu-id="82127-225">C++ :</span><span class="sxs-lookup"><span data-stu-id="82127-225">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. <span data-ttu-id="82127-226">L' **État du suivi des contrôleurs** retourne l’état de suivi dans le frame actuel.</span><span class="sxs-lookup"><span data-stu-id="82127-226">**Get Controller Tracking Status** returns the tracking status in the current frame.</span></span>

<span data-ttu-id="82127-227">Blueprint</span><span class="sxs-lookup"><span data-stu-id="82127-227">Blueprint:</span></span>

![Obtient l’état du suivi du contrôleur BP](images/unreal/get-controller-tracking-status-bp.png)

<span data-ttu-id="82127-229">C++ :</span><span class="sxs-lookup"><span data-stu-id="82127-229">C++:</span></span>
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```

## <a name="gestures"></a><span data-ttu-id="82127-230">Mouvements</span><span class="sxs-lookup"><span data-stu-id="82127-230">Gestures</span></span>

<span data-ttu-id="82127-231">HoloLens 2 effectue le suivi des mouvements spatiaux, ce qui signifie que vous pouvez capturer ces mouvements comme entrée.</span><span class="sxs-lookup"><span data-stu-id="82127-231">The HoloLens 2 tracks spatial gestures, which means you can capture those gestures as input.</span></span> <span data-ttu-id="82127-232">Vous trouverez plus d’informations sur les gestes dans le document sur l' [utilisation de base de HoloLens 2](https://docs.microsoft.com/hololens/hololens2-basic-usage) .</span><span class="sxs-lookup"><span data-stu-id="82127-232">You can find more details about gestures are the [HoloLens 2 Basic Usage](https://docs.microsoft.com/hololens/hololens2-basic-usage) document.</span></span>

<span data-ttu-id="82127-233">Vous pouvez trouver la fonction Blueprint dans sous **Windows Mixed Real Input spatial**, et la fonction C++ en ajoutant `WindowsMixedRealitySpatialInputFunctionLibrary.h` dans votre fichier de code appelant.</span><span class="sxs-lookup"><span data-stu-id="82127-233">You can find the Blueprint function in under **Windows Mixed Reality Spatial Input**, and the C++ function by adding `WindowsMixedRealitySpatialInputFunctionLibrary.h` in your calling code file.</span></span>

![Capturer les gestes](images/unreal/capture-gestures.png)

### <a name="enum"></a><span data-ttu-id="82127-235">Énumération</span><span class="sxs-lookup"><span data-stu-id="82127-235">Enum</span></span>
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
<span data-ttu-id="82127-236">Blueprint</span><span class="sxs-lookup"><span data-stu-id="82127-236">Blueprint:</span></span> 

![Type de mouvement](images/unreal/gesture-type.png)

<span data-ttu-id="82127-238">C++ :</span><span class="sxs-lookup"><span data-stu-id="82127-238">C++:</span></span>
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a><span data-ttu-id="82127-239">Fonction</span><span class="sxs-lookup"><span data-stu-id="82127-239">Function</span></span>
<span data-ttu-id="82127-240">Vous pouvez activer et désactiver la capture de mouvement avec la `CaptureGestures` fonction.</span><span class="sxs-lookup"><span data-stu-id="82127-240">You can enable and disable gesture capture with the `CaptureGestures` function.</span></span> <span data-ttu-id="82127-241">Lorsqu’un mouvement activé déclenche des événements d’entrée, la fonction retourne `true` si la capture de mouvement a réussi, et en `false` cas d’erreur.</span><span class="sxs-lookup"><span data-stu-id="82127-241">When an enabled gesture fires input events, the function returns `true` if gesture capture succeeded, and `false` if there's an error.</span></span>

<span data-ttu-id="82127-242">Blueprint</span><span class="sxs-lookup"><span data-stu-id="82127-242">Blueprint:</span></span>

![Capturer les gestes BP](images/unreal/capture-gestures-bp.png)

<span data-ttu-id="82127-244">C++ :</span><span class="sxs-lookup"><span data-stu-id="82127-244">C++:</span></span>
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false, 
    bool Hold = false, 
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None, 
    bool NavigationAxisX = true, 
    bool NavigationAxisY = true, 
    bool NavigationAxisZ = true);
```

<span data-ttu-id="82127-245">Voici quelques-uns des principaux événements que vous pouvez trouver dans les plans et C++ : ![ événements clés](images/unreal/key-events.png)</span><span class="sxs-lookup"><span data-stu-id="82127-245">The following are key events, which you can find in Blueprints and C++: ![Key Events](images/unreal/key-events.png)</span></span>

![Événements clés 2](images/unreal/key-events2.png)
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

## <a name="next-development-checkpoint"></a><span data-ttu-id="82127-247">Point de contrôle de développement suivant</span><span class="sxs-lookup"><span data-stu-id="82127-247">Next Development Checkpoint</span></span>

<span data-ttu-id="82127-248">Si vous suivez le parcours de développement inréel que nous avons mis à disposition, vous êtes au cœur de l’exploration des blocs de construction MRTK Core.</span><span class="sxs-lookup"><span data-stu-id="82127-248">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="82127-249">À partir de là, vous pouvez passer au bloc de construction suivant :</span><span class="sxs-lookup"><span data-stu-id="82127-249">From here, you can continue to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="82127-250">Ancres spatiales locales</span><span class="sxs-lookup"><span data-stu-id="82127-250">Local Spatial Anchors</span></span>](unreal-spatial-anchors.md)

<span data-ttu-id="82127-251">Ou accéder aux API et fonctionnalités de la plateforme Mixed Reality :</span><span class="sxs-lookup"><span data-stu-id="82127-251">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="82127-252">Caméra HoloLens</span><span class="sxs-lookup"><span data-stu-id="82127-252">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="82127-253">Vous pouvez revenir aux [points de contrôle de développement Unreal](unreal-development-overview.md#2-core-building-blocks) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="82127-253">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>