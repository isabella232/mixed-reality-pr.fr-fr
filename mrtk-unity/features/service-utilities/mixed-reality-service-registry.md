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
# <a name="what-are-the-mixedrealityserviceregistry-and-imixedrealityserviceregistrar"></a><span data-ttu-id="260c3-104">Qu’est-ce que MixedRealityServiceRegistry et IMixedRealityServiceRegistrar ?</span><span class="sxs-lookup"><span data-stu-id="260c3-104">What are the MixedRealityServiceRegistry and IMixedRealityServiceRegistrar?</span></span>

<span data-ttu-id="260c3-105">La boîte à outils de réalité mixte comporte deux composants portant le même nom qui effectuent des tâches connexes : MixedRealityServiceRegistry et IMixedRealityServiceRegistrar.</span><span class="sxs-lookup"><span data-stu-id="260c3-105">The Mixed Reality Toolkit has two very similarly named components that perform related tasks: MixedRealityServiceRegistry and IMixedRealityServiceRegistrar.</span></span>

## <a name="mixedrealityserviceregistry"></a><span data-ttu-id="260c3-106">MixedRealityServiceRegistry</span><span class="sxs-lookup"><span data-stu-id="260c3-106">MixedRealityServiceRegistry</span></span>

<span data-ttu-id="260c3-107">Le [MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) est le composant qui contient des instances de chaque service inscrit (Core Systems and extension services).</span><span class="sxs-lookup"><span data-stu-id="260c3-107">The [MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) is the component that contains instances of each registered service (core systems and extension services).</span></span>

> [!NOTE]
> <span data-ttu-id="260c3-108">Le MixedRealityServiceRegistry contient des instances d’objets qui implémentent l’interface [IMixedRealityService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) , y compris [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService).</span><span class="sxs-lookup"><span data-stu-id="260c3-108">The MixedRealityServiceRegistry contains instances of objects that implement [IMixedRealityService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) interface, including [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService).</span></span>
>
><span data-ttu-id="260c3-109">Les objets qui implémentent [IMixedRealityDataProvider](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) (une sous-classe de IMixedRealityService) ne sont pas inscrits explicitement dans le MixedRealityServiceRegistry.</span><span class="sxs-lookup"><span data-stu-id="260c3-109">Objects implementing the [IMixedRealityDataProvider](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) (a subclass of IMixedRealityService) are explicitly not registered in the MixedRealityServiceRegistry.</span></span> <span data-ttu-id="260c3-110">Ces objets sont gérés par les services individuels (par ex., la sensibilisation spatiale).</span><span class="sxs-lookup"><span data-stu-id="260c3-110">These objects are managed by the individual services (ex: Spatial Awareness).</span></span>

<span data-ttu-id="260c3-111">Le MixedRealityServiceRegistry est implémenté en tant que classe C# statique et est le modèle recommandé à utiliser pour acquérir des instances de service dans le code d’application.</span><span class="sxs-lookup"><span data-stu-id="260c3-111">The MixedRealityServiceRegistry is implemented as a static C# class and is the recommended pattern to use to acquire service instances in application code.</span></span>

<span data-ttu-id="260c3-112">L’extrait de code suivant illustre l’acquisition d’une instance IMixedRealityInputSystem.</span><span class="sxs-lookup"><span data-stu-id="260c3-112">The following snippet demonstrates acquiring an IMixedRealityInputSystem instance.</span></span>

```c#
IMixedRealityInputSystem inputSystem = null;

if (!MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
{
    // Failed to acquire the input system. It may not have been registered
}
```

## <a name="imixedrealityserviceregistrar"></a><span data-ttu-id="260c3-113">IMixedRealityServiceRegistrar</span><span class="sxs-lookup"><span data-stu-id="260c3-113">IMixedRealityServiceRegistrar</span></span>

<span data-ttu-id="260c3-114">[IMixedRealityServiceRegistrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) est l’interface qui définit les fonctionnalités implémentées par les composants qui gèrent l’inscription d’un ou de plusieurs services.</span><span class="sxs-lookup"><span data-stu-id="260c3-114">The [IMixedRealityServiceRegistrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) is the interface that defines the functionality implemented by components that manage the registration of one or more services.</span></span> <span data-ttu-id="260c3-115">Les composants qui implémentent IMixedRealityServiceRegistrar sont responsables de l’ajout et de la suppression des données dans le MixedRealityServiceRegistry.</span><span class="sxs-lookup"><span data-stu-id="260c3-115">Components that implement IMixedRealityServiceRegistrar are responsible for adding and removing the data within the MixedRealityServiceRegistry.</span></span> <span data-ttu-id="260c3-116">L’objet [MixedRealityToolkit](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) est un composant de ce type.</span><span class="sxs-lookup"><span data-stu-id="260c3-116">The [MixedRealityToolkit](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) object is one such component.</span></span>

<span data-ttu-id="260c3-117">D’autres bureaux d’enregistrement se trouvent dans le dossier MRTK/SDK/expérimental/Features.</span><span class="sxs-lookup"><span data-stu-id="260c3-117">Other registrars can be found in the MRTK/SDK/Experimental/Features folder.</span></span> <span data-ttu-id="260c3-118">Ces composants peuvent être utilisés pour ajouter la prise en charge d’un service unique (par ex., la prise de conscience spatiale) à une application.</span><span class="sxs-lookup"><span data-stu-id="260c3-118">These components can be used to add single service (ex: Spatial Awareness) support to an application.</span></span> <span data-ttu-id="260c3-119">Ces gestionnaires de service sont répertoriés ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="260c3-119">These single service managers are listed below.</span></span>

- [<span data-ttu-id="260c3-120">BoundarySystemManager</span><span class="sxs-lookup"><span data-stu-id="260c3-120">BoundarySystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Boundary.BoundarySystemManager)
- [<span data-ttu-id="260c3-121">CameraSystemManager</span><span class="sxs-lookup"><span data-stu-id="260c3-121">CameraSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.CameraSystem.CameraSystemManager)
- [<span data-ttu-id="260c3-122">DiagnosticsSystemManager</span><span class="sxs-lookup"><span data-stu-id="260c3-122">DiagnosticsSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Diagnostics.DiagnosticsSystemManager)
- [<span data-ttu-id="260c3-123">InputSystemManager</span><span class="sxs-lookup"><span data-stu-id="260c3-123">InputSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Input.InputSystemManager)
- [<span data-ttu-id="260c3-124">SpatialAwarenessSystemManager</span><span class="sxs-lookup"><span data-stu-id="260c3-124">SpatialAwarenessSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSystemManager)
- [<span data-ttu-id="260c3-125">TeleportSystemManager</span><span class="sxs-lookup"><span data-stu-id="260c3-125">TeleportSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Teleport.TeleportSystemManager)

<span data-ttu-id="260c3-126">Chacun des composants ci-dessus, à l’exception de InputSystemManager, est responsable de la gestion de l’inscription et de l’état d’un type de service unique.</span><span class="sxs-lookup"><span data-stu-id="260c3-126">Each of the above components, with the exception of the InputSystemManager, are responsible for managing the registration and status of a single service type.</span></span> <span data-ttu-id="260c3-127">InputSystem requiert des services de support supplémentaires (ex : FocusProvider) qui sont également gérés par le InputSystemManager.</span><span class="sxs-lookup"><span data-stu-id="260c3-127">The InputSystem requires some additional support services (ex: FocusProvider) that are also managed by the InputSystemManager.</span></span>

<span data-ttu-id="260c3-128">En général, les méthodes définies par IMixedRealityServiceRegistrar sont appelées en interne par les composants de gestion de service ou appelées par les services qui requièrent des composants de service supplémentaires pour fonctionner correctement.</span><span class="sxs-lookup"><span data-stu-id="260c3-128">In general, the methods defined by IMixedRealityServiceRegistrar are called internally by service management components or called by services that require additional service components to function correctly.</span></span> <span data-ttu-id="260c3-129">Le code d’application ne doit généralement pas appeler ces méthodes, car cela peut entraîner un comportement imprévisible de l’application (par exemple, une instance de service mise en cache peut devenir non valide).</span><span class="sxs-lookup"><span data-stu-id="260c3-129">Application code should, generally, not call these methods as doing so may cause the application to behave unpredictably (ex: a cached service instance may become invalid).</span></span>

## <a name="see-also"></a><span data-ttu-id="260c3-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="260c3-130">See also</span></span>

- [<span data-ttu-id="260c3-131">Documentation de l’API IMixedRealityServiceRegistrar</span><span class="sxs-lookup"><span data-stu-id="260c3-131">IMixedRealityServiceRegistrar API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar)
- [<span data-ttu-id="260c3-132">Documentation de l’API MixedRealityServiceRegistry</span><span class="sxs-lookup"><span data-stu-id="260c3-132">MixedRealityServiceRegistry API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
