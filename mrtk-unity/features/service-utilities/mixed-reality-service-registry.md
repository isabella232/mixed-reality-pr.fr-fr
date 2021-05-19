---
title: Registre de service de réalité mixte et IMixedRealityServiceRegistrar
description: Documentation sur MixedRealityServiceRegistry et IMixedRealityServiceRegistrar
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 09b20537824af42d241b6c33496cedcb4f530bc7
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145234"
---
# <a name="what-are-the-mixedrealityserviceregistry-and-imixedrealityserviceregistrar"></a>Qu’est-ce que MixedRealityServiceRegistry et IMixedRealityServiceRegistrar ?

La boîte à outils de réalité mixte comporte deux composants portant le même nom qui effectuent des tâches connexes : MixedRealityServiceRegistry et IMixedRealityServiceRegistrar.

## <a name="mixedrealityserviceregistry"></a>MixedRealityServiceRegistry

Le [MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) est le composant qui contient des instances de chaque service inscrit (Core Systems and extension services).

> [!NOTE]
> Le MixedRealityServiceRegistry contient des instances d’objets qui implémentent l’interface [IMixedRealityService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) , y compris [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService).
>
>Les objets qui implémentent [IMixedRealityDataProvider](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) (une sous-classe de IMixedRealityService) ne sont pas inscrits explicitement dans le MixedRealityServiceRegistry. Ces objets sont gérés par les services individuels (par ex., la sensibilisation spatiale).

Le MixedRealityServiceRegistry est implémenté en tant que classe C# statique et est le modèle recommandé à utiliser pour acquérir des instances de service dans le code d’application.

L’extrait de code suivant illustre l’acquisition d’une instance IMixedRealityInputSystem.

```c#
IMixedRealityInputSystem inputSystem = null;

if (!MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
{
    // Failed to acquire the input system. It may not have been registered
}
```

## <a name="imixedrealityserviceregistrar"></a>IMixedRealityServiceRegistrar

[IMixedRealityServiceRegistrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) est l’interface qui définit les fonctionnalités implémentées par les composants qui gèrent l’inscription d’un ou de plusieurs services. Les composants qui implémentent IMixedRealityServiceRegistrar sont responsables de l’ajout et de la suppression des données dans le MixedRealityServiceRegistry. L’objet [MixedRealityToolkit](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) est un composant de ce type.

D’autres bureaux d’enregistrement se trouvent dans le dossier MRTK/SDK/expérimental/Features. Ces composants peuvent être utilisés pour ajouter la prise en charge d’un service unique (par ex., la prise de conscience spatiale) à une application. Ces gestionnaires de service sont répertoriés ci-dessous.

- [BoundarySystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Boundary.BoundarySystemManager)
- [CameraSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.CameraSystem.CameraSystemManager)
- [DiagnosticsSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Diagnostics.DiagnosticsSystemManager)
- [InputSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Input.InputSystemManager)
- [SpatialAwarenessSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSystemManager)
- [TeleportSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Teleport.TeleportSystemManager)

Chacun des composants ci-dessus, à l’exception de InputSystemManager, est responsable de la gestion de l’inscription et de l’état d’un type de service unique. InputSystem requiert des services de support supplémentaires (ex : FocusProvider) qui sont également gérés par le InputSystemManager.

En général, les méthodes définies par IMixedRealityServiceRegistrar sont appelées en interne par les composants de gestion de service ou appelées par les services qui requièrent des composants de service supplémentaires pour fonctionner correctement. Le code d’application ne doit généralement pas appeler ces méthodes, car cela peut entraîner un comportement imprévisible de l’application (par exemple, une instance de service mise en cache peut devenir non valide).

## <a name="see-also"></a>Voir aussi

- [Documentation de l’API IMixedRealityServiceRegistrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar)
- [Documentation de l’API MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
