---
title: Fournisseur d’extensions système
description: Extensions MRTK et fournisseurs de données
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, extensions système,
ms.openlocfilehash: 358294702971b7d9e8de1b842d3bc1844e5dc9bf
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121467"
---
# <a name="systems-extension-services-and-data-providers"></a>Systèmes, services d’extension et fournisseurs de données

Dans la boîte à outils de la réalité mixte, un grand nombre des fonctionnalités sont fournies sous la forme de services. Les services sont regroupés en trois catégories principales : les systèmes, les services d’extension et les fournisseurs de données.

## <a name="systems"></a>Systèmes

Les systèmes sont des services qui fournissent la fonctionnalité principale de la réalité mixte Toolkit. Tous les systèmes sont des implémentations de l' [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) interface.

- [BoundarySystem](../features/boundary/boundary-system-getting-started.md)
- [CameraSystem](../features/camera-system/camera-system-overview.md)
- [DiagnosticsSystem](../features/diagnostics/diagnostics-system-getting-started.md)
- [InputSystem](../features/input/overview.md)
- [SceneSystem](../features/scene-system/scene-system-getting-started.md)
- [SpatialAwarenessSystem](../features/spatial-awareness/spatial-awareness-getting-started.md)
- [TeleportSystem](../features/teleport-system/teleport-system.md)

Chacun des systèmes répertoriés est exposé dans le [Profil](../features/profiles/profiles.md)de configuration du composant MixedRealityToolkit.

## <a name="extensions"></a>Extensions

Les services d’extension sont des composants qui étendent les fonctionnalités du kit de développement de la réalité mixte. Tous les services d’extension doivent spécifier qu’ils implémentent l' [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) interface.

Pour plus d’informations sur la création de services d’extension, veuillez vous référer à l’article [services d’extension](../features/extensions/extension-services.md) .

Pour être accessible à MRTK, les services d’extension sont inscrits et configurés à l’aide de la section extensions du profil de configuration du composant MixedRealityToolkit.

![Configuration d’un service d’extension](../features/images/profiles/ConfiguredExtensionService.png)

## <a name="data-providers"></a>Fournisseurs de données

Les fournisseurs de données sont des composants qui, par leur nom, fournissent des données à un service de boîte à outils de réalité mixte. Tous les fournisseurs de données doivent spécifier qu’ils implémentent l' [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.

> [!NOTE]
> Tous les services ne requièrent pas de fournisseurs de données. Des systèmes de la boîte à outils de la réalité mixte, les systèmes d’entrée et de sensibilisation spatiale sont les seuls services à utiliser les fournisseurs de données.

Pour être accessible au service MRTK spécifique, les fournisseurs de données sont inscrits dans le profil de configuration du service.

Le code d’application accède aux fournisseurs de données via l' [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) interface. Pour simplifier l’accès, les fournisseurs de données peuvent également être récupérés par le biais de la `CoreServices` classe d’assistance.

```c#
var inputSimulationService = CoreServices.GetDataProvider<IInputSimulationService>(CoreServices.InputSystem);
```

> [!IMPORTANT]
> Bien que `IMixedRealityDataProvider` hérite de `IMixedRealityService` , les fournisseurs de données ne sont pas inscrits auprès du `MixedRealityServiceRegistry` . Pour accéder aux fournisseurs de données, le code d’application doit interroger l’instance de service pour laquelle elles ont été inscrites (par exemple, le système d’entrée).

### <a name="input"></a>Entrée

Le système d’entrée MRTK utilise uniquement les fournisseurs de données qui implémentent [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) .

![Fournisseurs de données du système d’entrée](../features/images/input/RegisteredServiceProviders.PNG)

L’exemple suivant illustre l’accès au fournisseur de simulation d’entrée et l’activation/désactivation de la propriété SmoothEyeTracking.

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

L’accès à un fournisseur de données pour le système d’entrée principal peut également être simplifié via l’utilisation de la `CoreServices` classe d’assistance.

```c#
var inputSimulationService = CoreServices.GetInputSystemDataProvider<IInputSimulationService>();
if (inputSimulationService != null)
{
    // do something here
}
```

> [!NOTE]
> Le système d’entrée retourne uniquement les fournisseurs de données pris en charge pour la plateforme sur laquelle l’application s’exécute.

Pour plus d’informations sur l’écriture d’un fournisseur de données pour le système d’entrée MRTK, consultez [création d’un fournisseur de données de système d’entrée](../features/input/create-data-provider.md).

### <a name="spatial-awareness"></a>Sensibilisation spatiale

Le système de sensibilisation spatiale MRTK utilise uniquement des fournisseurs de données qui implémentent l' [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface.

![Fournisseurs de données de système de sensibilisation spatiale](../features/images/spatial-awareness/SpatialAwarenessProfile.png)

L’exemple suivant illustre l’accès aux fournisseurs de données de maillage spatial inscrits et la modification de la visibilité des maillages.

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

L’accès à un fournisseur de données pour le système de sensibilisation spatiale fondamental peut également être simplifié à l’aide de la `CoreServices` classe d’assistance.

```c#
var dataProvider = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();
if (dataProvider != null)
{
    // do something here
}
```

> [!NOTE]
> Le système de sensibilisation spatiale retourne uniquement les fournisseurs de données pris en charge pour la plateforme sur laquelle l’application s’exécute.

Pour plus d’informations sur l’écriture d’un fournisseur de données pour le système de sensibilisation spatiale MRTK, consultez [création d’un fournisseur de données de détection spatiale](../features/spatial-awareness/create-data-provider.md).

## <a name="see-also"></a>Voir aussi

- [Services d’extension](../features/extensions/extension-services.md)
- [Création d’un fournisseur de données de système d’entrée](../features/input/create-data-provider.md)
- [Création d’un fournisseur de données de système de sensibilisation spatiale](../features/spatial-awareness/create-data-provider.md)
- [Interface IMixedRealityService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService)
- [Interface IMixedRealityDataProvider](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [Interface IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
