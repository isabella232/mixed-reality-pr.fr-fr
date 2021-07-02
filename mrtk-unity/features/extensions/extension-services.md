---
title: Services d’extension
description: documentation sur les fonctionnalités étendues dans MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: f8f7b8dbac0355c226e4bbfae39246e5c1c58f69
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176268"
---
# <a name="extension-services"></a><span data-ttu-id="a2574-104">Services d’extension</span><span class="sxs-lookup"><span data-stu-id="a2574-104">Extension services</span></span>

<span data-ttu-id="a2574-105">les services d’Extension sont des composants qui étendent les fonctionnalités de la réalité mixte Shared Computer Toolkit.</span><span class="sxs-lookup"><span data-stu-id="a2574-105">Extension services are components that extend the functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="a2574-106">Ces services peuvent être fournis par le MRTK ou par d’autres parties.</span><span class="sxs-lookup"><span data-stu-id="a2574-106">These services may be provided by the MRTK or by other parties.</span></span>

## <a name="creating-an-extension-service"></a><span data-ttu-id="a2574-107">Création d’un service d’extension</span><span class="sxs-lookup"><span data-stu-id="a2574-107">Creating an extension service</span></span>

<span data-ttu-id="a2574-108">La méthode la plus efficace pour créer un service d’extension consiste à utiliser l' [Assistant Création de service d’extension](../tools/extension-service-creation-wizard.md).</span><span class="sxs-lookup"><span data-stu-id="a2574-108">The most efficient way to create an extension service is to use the [extension service creation wizard](../tools/extension-service-creation-wizard.md).</span></span>
<span data-ttu-id="a2574-109">pour démarrer l’assistant création de service d’extension, sélectionnez Shared Computer Toolkit de la **réalité mixte > utilitaires > créer un service d’extension**.</span><span class="sxs-lookup"><span data-stu-id="a2574-109">To start the extension service creation wizard, select **Mixed Reality Toolkit > Utilities > Create Extension Service**.</span></span>

![Assistant Création de service d’extension](../images/extension-wizard/ExtensionServiceCreationWizard.png)

<span data-ttu-id="a2574-111">L’Assistant automatise la création des composants du service et garantit l’héritage approprié de l’interface.</span><span class="sxs-lookup"><span data-stu-id="a2574-111">The wizard automates the creation of the service components and ensures the proper interface inheritance.</span></span>

![Composants créés par l’Assistant Création de service d’extension](../images/extension-wizard/ExtensionServiceComponents.png)

> [!Note]
> <span data-ttu-id="a2574-113">Dans MRTK version 2.0.0, l’Assistant service d’extension présente un problème où l’inspecteur de service et le profil de service doivent être générés.</span><span class="sxs-lookup"><span data-stu-id="a2574-113">In MRTK version 2.0.0, there is an issue in the extension service wizard where the service inspector and service profile are required to be generated.</span></span> <span data-ttu-id="a2574-114">Pour plus d’informations, consultez le problème [5654](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654) .</span><span class="sxs-lookup"><span data-stu-id="a2574-114">Please see issue [5654](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654) for more information.</span></span>

<span data-ttu-id="a2574-115">Une fois l’Assistant terminé, les fonctionnalités du service peuvent être implémentées.</span><span class="sxs-lookup"><span data-stu-id="a2574-115">When the wizard completes, the service functionality can be implemented.</span></span>

## <a name="registering-an-extension-service"></a><span data-ttu-id="a2574-116">Inscription d’un service d’extension</span><span class="sxs-lookup"><span data-stu-id="a2574-116">Registering an extension service</span></span>

<span data-ttu-id="a2574-117">pour être accessible par une application, le nouveau service d’extension doit être inscrit avec la réalité mixte Shared Computer Toolkit.</span><span class="sxs-lookup"><span data-stu-id="a2574-117">To be accessible by an application, the new extension service needs to be registered with the Mixed Reality Toolkit.</span></span>

<span data-ttu-id="a2574-118">L’Assistant Création d’un service d’extension peut être utilisé pour inscrire le service.</span><span class="sxs-lookup"><span data-stu-id="a2574-118">The extension service creation wizard can be used to register the service.</span></span>

![Inscription de l’Assistant Création de service d’extension](../images/extension-wizard/ExtensionServiceWizardRegister.png)

<span data-ttu-id="a2574-120">le service peut également être enregistré manuellement à l’aide de la réalité mixte Shared Computer Toolkit l’inspecteur de configuration.</span><span class="sxs-lookup"><span data-stu-id="a2574-120">The service can also be manually registered using the Mixed Reality Toolkit configuration inspector.</span></span>

![Inscription manuelle du service d’extension](../images/profiles/RegisterExtensionService.png)

<span data-ttu-id="a2574-122">Si le service d’extension utilise un profil, vérifiez qu’il est spécifié dans l’inspecteur.</span><span class="sxs-lookup"><span data-stu-id="a2574-122">If the extension service uses a profile, please ensure that it is specified in the inspector.</span></span>

![Service d’extension configuré](../images/profiles/ConfiguredExtensionService.png)

<span data-ttu-id="a2574-124">Le nom et la priorité du composant peuvent également être ajustés.</span><span class="sxs-lookup"><span data-stu-id="a2574-124">The component name and priority can also be adjusted.</span></span>

## <a name="accessing-an-extension-service"></a><span data-ttu-id="a2574-125">Accès à un service d’extension</span><span class="sxs-lookup"><span data-stu-id="a2574-125">Accessing an extension service</span></span>

<span data-ttu-id="a2574-126">Les services d’extension sont accessibles, dans le code, à l’aide de, [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) comme indiqué dans l’exemple ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="a2574-126">Extension services are accessed, in code, using the [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) as shown in the example below.</span></span>

```c#
INewService service = null;
if (MixedRealityServiceRegistry.TryGetService<INewService>(out service))
{
    // Succeeded in getting the service,  perform any desired tasks.
}
```

## <a name="see-also"></a><span data-ttu-id="a2574-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2574-127">See also</span></span>

- [<span data-ttu-id="a2574-128">Systèmes, services d’extension et fournisseurs de données</span><span class="sxs-lookup"><span data-stu-id="a2574-128">Systems, extension services and data providers</span></span>](../../architecture/systems-extensions-providers.md)
- [<span data-ttu-id="a2574-129">Assistant Création de service d’extension</span><span class="sxs-lookup"><span data-stu-id="a2574-129">Extension service creation wizard</span></span>](../tools/extension-service-creation-wizard.md)
- [<span data-ttu-id="a2574-130">IMixedRealityExtensionService</span><span class="sxs-lookup"><span data-stu-id="a2574-130">IMixedRealityExtensionService</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
- [<span data-ttu-id="a2574-131">MixedRealityServiceRegistry</span><span class="sxs-lookup"><span data-stu-id="a2574-131">MixedRealityServiceRegistry</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
