---
title: Mouvements
description: Docummentation sur les gestes et ses événements dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, gestes,
ms.openlocfilehash: 7bbc97ab5e23a69356d523c463aa37c013d70337
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176879"
---
# <a name="gestures"></a><span data-ttu-id="31c01-104">Mouvements</span><span class="sxs-lookup"><span data-stu-id="31c01-104">Gestures</span></span>

<span data-ttu-id="31c01-105">Les gestes sont des événements d’entrée basés sur des mains humaines.</span><span class="sxs-lookup"><span data-stu-id="31c01-105">Gestures are input events based on human hands.</span></span> <span data-ttu-id="31c01-106">Il existe deux types d’appareils qui génèrent des événements d’entrée de mouvement dans MRTK :</span><span class="sxs-lookup"><span data-stu-id="31c01-106">There are two types of devices that raise gesture input events in MRTK:</span></span>

- <span data-ttu-id="31c01-107">Windows Mixed Reality des appareils tels que HoloLens.</span><span class="sxs-lookup"><span data-stu-id="31c01-107">Windows Mixed Reality devices such as HoloLens.</span></span> <span data-ttu-id="31c01-108">Cela décrit le pincement des mouvements (« TAP Air ») et les gestes tap-and-hold.</span><span class="sxs-lookup"><span data-stu-id="31c01-108">This describes pinching motions ("Air Tap") and tap-and-hold gestures.</span></span>

  <span data-ttu-id="31c01-109">pour plus d’informations sur les gestes de HoloLens, consultez la documentation sur les [gestes de Windows Mixed Reality](/windows/mixed-reality/gestures).</span><span class="sxs-lookup"><span data-stu-id="31c01-109">For more information on HoloLens gestures see the [Windows Mixed Reality Gestures documentation](/windows/mixed-reality/gestures).</span></span>

  <span data-ttu-id="31c01-110">[`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)encapsule le [XR Unity. WSA. Input. GestureRecognizer](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.GestureRecognizer.html) pour consommer les événements de mouvement unity à partir de HoloLens appareils.</span><span class="sxs-lookup"><span data-stu-id="31c01-110">[`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) wraps the [Unity XR.WSA.Input.GestureRecognizer](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.GestureRecognizer.html) to consume Unity's gesture events from HoloLens devices.</span></span>

- <span data-ttu-id="31c01-111">Appareils à écran tactile.</span><span class="sxs-lookup"><span data-stu-id="31c01-111">Touch screen devices.</span></span>

  <span data-ttu-id="31c01-112">[`UnityTouchController`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput) encapsule la [classe Touch Unity](https://docs.unity3d.com/ScriptReference/Touch.html) qui prend en charge les écrans tactiles physiques.</span><span class="sxs-lookup"><span data-stu-id="31c01-112">[`UnityTouchController`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput) wraps the [Unity Touch class](https://docs.unity3d.com/ScriptReference/Touch.html) that supports physical touch screens.</span></span>

<span data-ttu-id="31c01-113">ces deux sources d’entrée utilisent le profil de _Paramètres de mouvement_ pour traduire les événements tactiles et de mouvement d’unity respectivement en [Actions d’entrée](input-actions.md)de MRTK.</span><span class="sxs-lookup"><span data-stu-id="31c01-113">Both of these input sources use the _Gesture Settings_ profile to translate Unity's Touch and Gesture events respectively into MRTK's [Input Actions](input-actions.md).</span></span> <span data-ttu-id="31c01-114">ce profil se trouve sous le profil de _Paramètres du système d’entrée_ .</span><span class="sxs-lookup"><span data-stu-id="31c01-114">This profile can be found under the _Input System Settings_ profile.</span></span>

<img src="../images/input/GestureProfile.png" alt="Gesture Profile" style="max-width:100%;">

## <a name="gesture-events"></a><span data-ttu-id="31c01-115">Événements de mouvement</span><span class="sxs-lookup"><span data-stu-id="31c01-115">Gesture events</span></span>

<span data-ttu-id="31c01-116">Les événements de mouvement sont reçus en implémentant l’une des interfaces du gestionnaire de mouvements : [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) ou [`IMixedRealityGestureHandler<TYPE>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) (consultez la table des [gestionnaires d’événements](input-events.md)).</span><span class="sxs-lookup"><span data-stu-id="31c01-116">Gesture events are received by implementing one of the gesture handler interfaces: [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) or [`IMixedRealityGestureHandler<TYPE>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) (see table of [event handlers](input-events.md)).</span></span>

<span data-ttu-id="31c01-117">Consultez [exemple de scène](#example-scene) pour obtenir un exemple d’implémentation d’un gestionnaire d’événements de mouvement.</span><span class="sxs-lookup"><span data-stu-id="31c01-117">See [Example Scene](#example-scene) for an example implementation of a gesture event handler.</span></span>

<span data-ttu-id="31c01-118">Lors de l’implémentation de la version générique, les événements *OnGestureCompleted* et *OnGestureUpdated* peuvent recevoir des données typées des types suivants :</span><span class="sxs-lookup"><span data-stu-id="31c01-118">When implementing the generic version, the *OnGestureCompleted* and *OnGestureUpdated* events can receive typed data of the following types:</span></span>

- <span data-ttu-id="31c01-119">`Vector2` -mouvement de position 2D.</span><span class="sxs-lookup"><span data-stu-id="31c01-119">`Vector2` - 2D position gesture.</span></span> <span data-ttu-id="31c01-120">Produits par les écrans tactiles pour informer leurs [`deltaPosition`](https://docs.unity3d.com/ScriptReference/Touch-deltaPosition.html) .</span><span class="sxs-lookup"><span data-stu-id="31c01-120">Produced by touch screens to inform of their [`deltaPosition`](https://docs.unity3d.com/ScriptReference/Touch-deltaPosition.html).</span></span>
- <span data-ttu-id="31c01-121">`Vector3` -mouvement de position 3D.</span><span class="sxs-lookup"><span data-stu-id="31c01-121">`Vector3` - 3D position gesture.</span></span> <span data-ttu-id="31c01-122">produit par HoloLens pour informer :</span><span class="sxs-lookup"><span data-stu-id="31c01-122">Produced by HoloLens to inform of:</span></span>
  - <span data-ttu-id="31c01-123">[`cumulativeDelta`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.ManipulationUpdatedEventArgs-cumulativeDelta.html) d’un événement de manipulation</span><span class="sxs-lookup"><span data-stu-id="31c01-123">[`cumulativeDelta`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.ManipulationUpdatedEventArgs-cumulativeDelta.html) of a manipulation event</span></span>
  - <span data-ttu-id="31c01-124">[`normalizedOffset`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.NavigationUpdatedEventArgs-normalizedOffset.html) d’un événement de navigation</span><span class="sxs-lookup"><span data-stu-id="31c01-124">[`normalizedOffset`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.NavigationUpdatedEventArgs-normalizedOffset.html) of a navigation event</span></span>
- <span data-ttu-id="31c01-125">`Quaternion` -mouvement de rotation 3D.</span><span class="sxs-lookup"><span data-stu-id="31c01-125">`Quaternion` - 3D rotation gesture.</span></span> <span data-ttu-id="31c01-126">Disponible pour les sources d’entrée personnalisées, mais ne sont actuellement pas produites par les sources existantes.</span><span class="sxs-lookup"><span data-stu-id="31c01-126">Available to custom input sources but not currently produced by any of the existing ones.</span></span>
- <span data-ttu-id="31c01-127">`MixedRealityPose` -Mouvement de position/rotation 3D combiné.</span><span class="sxs-lookup"><span data-stu-id="31c01-127">`MixedRealityPose` - Combined 3D position/rotation gesture.</span></span> <span data-ttu-id="31c01-128">Disponible pour les sources d’entrée personnalisées, mais ne sont actuellement pas produites par les sources existantes.</span><span class="sxs-lookup"><span data-stu-id="31c01-128">Available to custom input sources but not currently produced by any of the existing ones.</span></span>

## <a name="order-of-events"></a><span data-ttu-id="31c01-129">Ordre des événements</span><span class="sxs-lookup"><span data-stu-id="31c01-129">Order of events</span></span>

<span data-ttu-id="31c01-130">Il existe deux chaînes principales d’événements, en fonction de l’entrée utilisateur :</span><span class="sxs-lookup"><span data-stu-id="31c01-130">There are two principal chains of events, depending on user input:</span></span>

- <span data-ttu-id="31c01-131">« Hold » :</span><span class="sxs-lookup"><span data-stu-id="31c01-131">"Hold":</span></span>
    1. <span data-ttu-id="31c01-132">Maintenir appuyé :</span><span class="sxs-lookup"><span data-stu-id="31c01-132">Hold tap:</span></span>
        - <span data-ttu-id="31c01-133">Démarrer la _manipulation_</span><span class="sxs-lookup"><span data-stu-id="31c01-133">start _Manipulation_</span></span>
    1. <span data-ttu-id="31c01-134">Maintenez appuyé sur [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):</span><span class="sxs-lookup"><span data-stu-id="31c01-134">Hold tap beyond [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):</span></span>
        - <span data-ttu-id="31c01-135">Démarrer la _conservation_</span><span class="sxs-lookup"><span data-stu-id="31c01-135">start _Hold_</span></span>
    1. <span data-ttu-id="31c01-136">Appuyez sur la version :</span><span class="sxs-lookup"><span data-stu-id="31c01-136">Release tap:</span></span>
        - <span data-ttu-id="31c01-137">terminer la _conservation_</span><span class="sxs-lookup"><span data-stu-id="31c01-137">complete _Hold_</span></span>
        - <span data-ttu-id="31c01-138">_manipulation_ complète</span><span class="sxs-lookup"><span data-stu-id="31c01-138">complete _Manipulation_</span></span>

- <span data-ttu-id="31c01-139">« Move » :</span><span class="sxs-lookup"><span data-stu-id="31c01-139">"Move":</span></span>
    1. <span data-ttu-id="31c01-140">Maintenir appuyé :</span><span class="sxs-lookup"><span data-stu-id="31c01-140">Hold tap:</span></span>
        - <span data-ttu-id="31c01-141">Démarrer la _manipulation_</span><span class="sxs-lookup"><span data-stu-id="31c01-141">start _Manipulation_</span></span>
    1. <span data-ttu-id="31c01-142">Maintenez appuyé sur [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):</span><span class="sxs-lookup"><span data-stu-id="31c01-142">Hold tap beyond [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):</span></span>
        - <span data-ttu-id="31c01-143">Démarrer la _conservation_</span><span class="sxs-lookup"><span data-stu-id="31c01-143">start _Hold_</span></span>
    1. <span data-ttu-id="31c01-144">Déplacer vers la main au-delà de [NavigationStartThreshold](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.NavigationStartThreshold):</span><span class="sxs-lookup"><span data-stu-id="31c01-144">Move hand beyond [NavigationStartThreshold](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.NavigationStartThreshold):</span></span>
        - <span data-ttu-id="31c01-145">annuler la _conservation_</span><span class="sxs-lookup"><span data-stu-id="31c01-145">cancel _Hold_</span></span>
        - <span data-ttu-id="31c01-146">Démarrer la _navigation_</span><span class="sxs-lookup"><span data-stu-id="31c01-146">start _Navigation_</span></span>
    1. <span data-ttu-id="31c01-147">Appuyez sur la version :</span><span class="sxs-lookup"><span data-stu-id="31c01-147">Release tap:</span></span>
        - <span data-ttu-id="31c01-148">_manipulation_ complète</span><span class="sxs-lookup"><span data-stu-id="31c01-148">complete _Manipulation_</span></span>
        - <span data-ttu-id="31c01-149">terminer la _navigation_</span><span class="sxs-lookup"><span data-stu-id="31c01-149">complete _Navigation_</span></span>

## <a name="example-scene"></a><span data-ttu-id="31c01-150">Exemple de scène</span><span class="sxs-lookup"><span data-stu-id="31c01-150">Example scene</span></span>

<span data-ttu-id="31c01-151">La scène **HandInteractionGestureEventsExample** (éléments multimédias/MRTK/examples/démos/HandTracking/scènes) montre comment utiliser le résultat du pointeur pour générer un objet à l’emplacement de l’accès.</span><span class="sxs-lookup"><span data-stu-id="31c01-151">The **HandInteractionGestureEventsExample** (Assets/MRTK/Examples/Demos/HandTracking/Scenes) scene shows how to use the pointer Result to spawn an object at the hit location.</span></span>

<span data-ttu-id="31c01-152">Le `GestureTester` script (ressources/MRTK/examples/démos/HandTracking/script) est un exemple d’implémentation permettant de visualiser des événements de mouvement via GameObjects.</span><span class="sxs-lookup"><span data-stu-id="31c01-152">The `GestureTester` (Assets/MRTK/Examples/Demos/HandTracking/Script) script is an example implementation to visualize gesture events via GameObjects.</span></span> <span data-ttu-id="31c01-153">Les fonctions de gestionnaire modifient la couleur des objets indicateur et affichent le dernier événement enregistré dans les objets de texte de la scène.</span><span class="sxs-lookup"><span data-stu-id="31c01-153">The handler functions change the color of indicator objects and display the last recorded event in text objects in the scene.</span></span>
