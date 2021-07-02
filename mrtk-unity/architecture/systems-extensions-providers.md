---
title: Systèmes, services d’extension et fournisseurs de données
description: Extensions MRTK et fournisseurs de données
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, Extensions système,
ms.openlocfilehash: 668df40cec9b9443b37f63d80fcf8a1ca2e0bcbc
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177419"
---
# <a name="systems-extension-services-and-data-providers"></a><span data-ttu-id="41589-104">Systèmes, services d’extension et fournisseurs de données</span><span class="sxs-lookup"><span data-stu-id="41589-104">Systems, extension services, and data providers</span></span>

<span data-ttu-id="41589-105">dans la Shared Computer Toolkit de la réalité mixte, un grand nombre des fonctionnalités sont fournies sous la forme de services.</span><span class="sxs-lookup"><span data-stu-id="41589-105">In the Mixed Reality Toolkit, many of the features are delivered in the form of services.</span></span> <span data-ttu-id="41589-106">Les services sont regroupés en trois catégories principales : les systèmes, les services d’extension et les fournisseurs de données.</span><span class="sxs-lookup"><span data-stu-id="41589-106">Services are grouped into three primary categories: systems, extension services and data providers.</span></span>

## <a name="systems"></a><span data-ttu-id="41589-107">Systèmes</span><span class="sxs-lookup"><span data-stu-id="41589-107">Systems</span></span>

<span data-ttu-id="41589-108">les systèmes sont des services qui fournissent la fonctionnalité principale de la réalité mixte Shared Computer Toolkit.</span><span class="sxs-lookup"><span data-stu-id="41589-108">Systems are services that provide the core functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="41589-109">Tous les systèmes sont des implémentations de l' [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) interface.</span><span class="sxs-lookup"><span data-stu-id="41589-109">All systems are implementations of the [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) interface.</span></span>

- [<span data-ttu-id="41589-110">BoundarySystem</span><span class="sxs-lookup"><span data-stu-id="41589-110">BoundarySystem</span></span>](../features/boundary/boundary-system-getting-started.md)
- [<span data-ttu-id="41589-111">CameraSystem</span><span class="sxs-lookup"><span data-stu-id="41589-111">CameraSystem</span></span>](../features/camera-system/camera-system-overview.md)
- [<span data-ttu-id="41589-112">DiagnosticsSystem</span><span class="sxs-lookup"><span data-stu-id="41589-112">DiagnosticsSystem</span></span>](../features/diagnostics/diagnostics-system-getting-started.md)
- [<span data-ttu-id="41589-113">InputSystem</span><span class="sxs-lookup"><span data-stu-id="41589-113">InputSystem</span></span>](../features/input/overview.md)
- [<span data-ttu-id="41589-114">SceneSystem</span><span class="sxs-lookup"><span data-stu-id="41589-114">SceneSystem</span></span>](../features/scene-system/scene-system-getting-started.md)
- [<span data-ttu-id="41589-115">SpatialAwarenessSystem</span><span class="sxs-lookup"><span data-stu-id="41589-115">SpatialAwarenessSystem</span></span>](../features/spatial-awareness/spatial-awareness-getting-started.md)
- [<span data-ttu-id="41589-116">TeleportSystem</span><span class="sxs-lookup"><span data-stu-id="41589-116">TeleportSystem</span></span>](../features/teleport-system/teleport-system.md)

<span data-ttu-id="41589-117">Chacun des systèmes répertoriés est exposé dans le [Profil](../features/profiles/profiles.md)de configuration du composant MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="41589-117">Each of the listed systems are surfaced in the MixedRealityToolkit component's configuration [profile](../features/profiles/profiles.md).</span></span>

## <a name="extensions"></a><span data-ttu-id="41589-118">Extensions</span><span class="sxs-lookup"><span data-stu-id="41589-118">Extensions</span></span>

<span data-ttu-id="41589-119">les services d’Extension sont des composants qui étendent les fonctionnalités de la réalité mixte Shared Computer Toolkit.</span><span class="sxs-lookup"><span data-stu-id="41589-119">Extension services are components that extend the functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="41589-120">Tous les services d’extension doivent spécifier qu’ils implémentent l' [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) interface.</span><span class="sxs-lookup"><span data-stu-id="41589-120">All extension services must specify that they implement the [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) interface.</span></span>

<span data-ttu-id="41589-121">Pour plus d’informations sur la création de services d’extension, veuillez vous référer à l’article [services d’extension](../features/extensions/extension-services.md) .</span><span class="sxs-lookup"><span data-stu-id="41589-121">For information on creating extension services, please reference the [Extension services](../features/extensions/extension-services.md) article.</span></span>

<span data-ttu-id="41589-122">Pour être accessible à MRTK, les services d’extension sont inscrits et configurés à l’aide de la section extensions du profil de configuration du composant MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="41589-122">To be accessible to the MRTK, extension services are registered and configured using the Extensions section of the MixedRealityToolkit component's configuration profile.</span></span>

![Configuration d’un service d’extension](../features/images/profiles/ConfiguredExtensionService.png)

## <a name="data-providers"></a><span data-ttu-id="41589-124">Fournisseurs de données</span><span class="sxs-lookup"><span data-stu-id="41589-124">Data providers</span></span>

<span data-ttu-id="41589-125">les fournisseurs de données sont des composants qui, par leur nom, fournissent des données à une réalité mixte Shared Computer Toolkit service.</span><span class="sxs-lookup"><span data-stu-id="41589-125">Data providers are components that, per their name, provide data to a Mixed Reality Toolkit service.</span></span> <span data-ttu-id="41589-126">Tous les fournisseurs de données doivent spécifier qu’ils implémentent l' [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span><span class="sxs-lookup"><span data-stu-id="41589-126">All data providers must specify that they implement the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!NOTE]
> <span data-ttu-id="41589-127">Tous les services ne requièrent pas de fournisseurs de données.</span><span class="sxs-lookup"><span data-stu-id="41589-127">Not all services will require data providers.</span></span> <span data-ttu-id="41589-128">parmi les systèmes de Shared Computer Toolkit de la réalité mixte, les systèmes d’entrée et de sensibilisation spatiale sont les seuls services à utiliser les fournisseurs de données.</span><span class="sxs-lookup"><span data-stu-id="41589-128">Of the Mixed Reality Toolkit's systems, the Input and Spatial Awareness systems are the only services to utilize data providers.</span></span>

<span data-ttu-id="41589-129">Pour être accessible au service MRTK spécifique, les fournisseurs de données sont inscrits dans le profil de configuration du service.</span><span class="sxs-lookup"><span data-stu-id="41589-129">To be accessible to the specific MRTK service, data providers are registered in the service's configuration profile.</span></span>

<span data-ttu-id="41589-130">Le code d’application accède aux fournisseurs de données via l' [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) interface.</span><span class="sxs-lookup"><span data-stu-id="41589-130">Application code accesses data providers via the [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) interface.</span></span> <span data-ttu-id="41589-131">Pour simplifier l’accès, les fournisseurs de données peuvent également être récupérés par le biais de la `CoreServices` classe d’assistance.</span><span class="sxs-lookup"><span data-stu-id="41589-131">To simplify access, data providers can also be retrieved via the `CoreServices` helper class.</span></span>

```c#
var inputSimulationService = CoreServices.GetDataProvider<IInputSimulationService>(CoreServices.InputSystem);
```

> [!IMPORTANT]
> <span data-ttu-id="41589-132">Bien que `IMixedRealityDataProvider` hérite de `IMixedRealityService` , les fournisseurs de données ne sont pas inscrits auprès du `MixedRealityServiceRegistry` .</span><span class="sxs-lookup"><span data-stu-id="41589-132">Although `IMixedRealityDataProvider` inherits from `IMixedRealityService`, data providers are not registered with the `MixedRealityServiceRegistry`.</span></span> <span data-ttu-id="41589-133">Pour accéder aux fournisseurs de données, le code d’application doit interroger l’instance de service pour laquelle elles ont été inscrites (par exemple, le système d’entrée).</span><span class="sxs-lookup"><span data-stu-id="41589-133">To access data providers, application code must query the service instance for which they were registered (ex: input system).</span></span>

### <a name="input"></a><span data-ttu-id="41589-134">Entrée</span><span class="sxs-lookup"><span data-stu-id="41589-134">Input</span></span>

<span data-ttu-id="41589-135">Le système d’entrée MRTK utilise uniquement les fournisseurs de données qui implémentent [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) .</span><span class="sxs-lookup"><span data-stu-id="41589-135">The MRTK input system utilizes only data providers that implement the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager).</span></span>

![Fournisseurs de données du système d’entrée](../features/images/input/RegisteredServiceProviders.PNG)

<span data-ttu-id="41589-137">L’exemple suivant illustre l’accès au fournisseur de simulation d’entrée et l’activation/désactivation de la propriété SmoothEyeTracking.</span><span class="sxs-lookup"><span data-stu-id="41589-137">The following example demonstrates accessing the input simulation provider and toggle the SmoothEyeTracking property.</span></span>

```c#
IMixedRealityDataProviderAccess dataProviderAccess = CoreServices.InputSystem as IMixedRealityDataProviderAccess;

if (dataProviderAccess != null)
{
    IInputSimulationService inputSimulation =
        dataProviderAccess.GetDataProvider<IInputSimulationService>();

    if (inputSimulation != null)
    {
        inputSimulation.SmoothEyeTracking = !inputSimulation.SmoothEyeTracking;
    }
}
```

<span data-ttu-id="41589-138">L’accès à un fournisseur de données pour le système d’entrée principal peut également être simplifié via l’utilisation de la `CoreServices` classe d’assistance.</span><span class="sxs-lookup"><span data-stu-id="41589-138">Accessing a data provider for the core input system can also be simplified via use of the `CoreServices` helper class.</span></span>

```c#
var inputSimulationService = CoreServices.GetInputSystemDataProvider<IInputSimulationService>();
if (inputSimulationService != null)
{
    // do something here
}
```

> [!NOTE]
> <span data-ttu-id="41589-139">Le système d’entrée retourne uniquement les fournisseurs de données pris en charge pour la plateforme sur laquelle l’application s’exécute.</span><span class="sxs-lookup"><span data-stu-id="41589-139">The input system returns only data providers that are supported for the platform on which the application is running.</span></span>

<span data-ttu-id="41589-140">Pour plus d’informations sur l’écriture d’un fournisseur de données pour le système d’entrée MRTK, consultez [création d’un fournisseur de données de système d’entrée](../features/input/create-data-provider.md).</span><span class="sxs-lookup"><span data-stu-id="41589-140">For information on writing a data provider for the MRTK input system, please see [creating an input system data provider](../features/input/create-data-provider.md).</span></span>

### <a name="spatial-awareness"></a><span data-ttu-id="41589-141">Sensibilisation spatiale</span><span class="sxs-lookup"><span data-stu-id="41589-141">Spatial awareness</span></span>

<span data-ttu-id="41589-142">Le système de sensibilisation spatiale MRTK utilise uniquement des fournisseurs de données qui implémentent l' [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface.</span><span class="sxs-lookup"><span data-stu-id="41589-142">The MRTK spatial awareness system utilizes only data providers that implement the [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface.</span></span>

![Fournisseurs de données de système de sensibilisation spatiale](../features/images/spatial-awareness/SpatialAwarenessProfile.png)

<span data-ttu-id="41589-144">L’exemple suivant illustre l’accès aux fournisseurs de données de maillage spatial inscrits et la modification de la visibilité des maillages.</span><span class="sxs-lookup"><span data-stu-id="41589-144">The following example demonstrates accessing the registered spatial mesh data providers and changing the visibility of the meshes.</span></span>

```c#
IMixedRealityDataProviderAccess dataProviderAccess =
    CoreServices.SpatialAwarenessSystem as IMixedRealityDataProviderAccess;

if (dataProviderAccess != null)
{
    IReadOnlyList<IMixedRealitySpatialAwarenessMeshObserver> observers =
        dataProviderAccess.GetDataProviders<IMixedRealitySpatialAwarenessMeshObserver>();

    foreach (IMixedRealitySpatialAwarenessMeshObserver observer in observers)
    {
        // Set the mesh to use the occlusion material
        observer.DisplayOption = SpatialMeshDisplayOptions.Occlusion;
    }
}
```

<span data-ttu-id="41589-145">L’accès à un fournisseur de données pour le système de sensibilisation spatiale fondamental peut également être simplifié à l’aide de la `CoreServices` classe d’assistance.</span><span class="sxs-lookup"><span data-stu-id="41589-145">Accessing a data provider for the core spatial awareness system can also be simplified via use of the `CoreServices` helper class.</span></span>

```c#
var dataProvider = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();
if (dataProvider != null)
{
    // do something here
}
```

> [!NOTE]
> <span data-ttu-id="41589-146">Le système de sensibilisation spatiale retourne uniquement les fournisseurs de données pris en charge pour la plateforme sur laquelle l’application s’exécute.</span><span class="sxs-lookup"><span data-stu-id="41589-146">The spatial awareness system returns only data providers that are supported for the platform on which the application is running.</span></span>

<span data-ttu-id="41589-147">Pour plus d’informations sur l’écriture d’un fournisseur de données pour le système de sensibilisation spatiale MRTK, consultez [création d’un fournisseur de données de détection spatiale](../features/spatial-awareness/create-data-provider.md).</span><span class="sxs-lookup"><span data-stu-id="41589-147">For information on writing a data provider for the MRTK spatial awareness system, please see [creating a spatial awareness system data provider](../features/spatial-awareness/create-data-provider.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="41589-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41589-148">See also</span></span>

- [<span data-ttu-id="41589-149">Services d’extension</span><span class="sxs-lookup"><span data-stu-id="41589-149">Extension services</span></span>](../features/extensions/extension-services.md)
- [<span data-ttu-id="41589-150">Création d’un fournisseur de données de système d’entrée</span><span class="sxs-lookup"><span data-stu-id="41589-150">Creating an input system data provider</span></span>](../features/input/create-data-provider.md)
- [<span data-ttu-id="41589-151">Création d’un fournisseur de données de système de sensibilisation spatiale</span><span class="sxs-lookup"><span data-stu-id="41589-151">Creating a spatial awareness system system data provider</span></span>](../features/spatial-awareness/create-data-provider.md)
- [<span data-ttu-id="41589-152">Interface IMixedRealityService</span><span class="sxs-lookup"><span data-stu-id="41589-152">IMixedRealityService interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService)
- [<span data-ttu-id="41589-153">Interface IMixedRealityDataProvider</span><span class="sxs-lookup"><span data-stu-id="41589-153">IMixedRealityDataProvider interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [<span data-ttu-id="41589-154">Interface IMixedRealityExtensionService</span><span class="sxs-lookup"><span data-stu-id="41589-154">IMixedRealityExtensionService interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
