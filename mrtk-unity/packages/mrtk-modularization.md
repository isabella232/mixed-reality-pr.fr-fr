---
title: Modularisation MRTK
description: Décrit la Componentisation dans MRTK.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: eac96e309afc21f9a2b6efe9c3aef5975e4f0dff
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177009"
---
# <a name="mrtk-modularization"></a><span data-ttu-id="1faee-104">Modularisation MRTK</span><span class="sxs-lookup"><span data-stu-id="1faee-104">MRTK modularization</span></span>

<span data-ttu-id="1faee-105">l’une des nombreuses nouvelles fonctionnalités de la réalité mixte Shared Computer Toolkit v2 est l’amélioration de la création de composants.</span><span class="sxs-lookup"><span data-stu-id="1faee-105">One of the great new features of Mixed Reality Toolkit v2 is improved componentization.</span></span> <span data-ttu-id="1faee-106">Chaque fois que cela est possible, les composants individuels sont isolés de la couche principale de la Fondation.</span><span class="sxs-lookup"><span data-stu-id="1faee-106">Wherever possible, individual components are isolated from all but the core layer of the foundation.</span></span>

## <a name="minimized-dependencies"></a><span data-ttu-id="1faee-107">Dépendances réduites</span><span class="sxs-lookup"><span data-stu-id="1faee-107">Minimized dependencies</span></span>

<span data-ttu-id="1faee-108">MRTK V2 a été intentionnellement développé pour être modulaire et pour réduire les dépendances entre les services système (par ex., la sensibilisation spatiale).</span><span class="sxs-lookup"><span data-stu-id="1faee-108">MRTK v2 was intentionally developed to be modular and to minimize dependencies between system services (ex: spatial awareness).</span></span>

<span data-ttu-id="1faee-109">En raison de la nature de certains services système (par ex., les entrées et les téléportions), il existe un petit nombre de dépendances.</span><span class="sxs-lookup"><span data-stu-id="1faee-109">Due to the nature of some system services (ex: input and teleportation), a small number of dependencies exist.</span></span>

<span data-ttu-id="1faee-110">S’il est prévu que les services requièrent un ou plusieurs composants de fournisseur de données, il n’existe aucun lien direct entre eux.</span><span class="sxs-lookup"><span data-stu-id="1faee-110">While it is expected that services will need one or more data provider components, there are no direct links between them.</span></span> <span data-ttu-id="1faee-111">Il en va de même pour les fonctionnalités du kit de développement logiciel (par exemple, les composants de l’interface utilisateur).</span><span class="sxs-lookup"><span data-stu-id="1faee-111">The same is true for SDK features (ex: User Interface components).</span></span>

## <a name="component-communication"></a><span data-ttu-id="1faee-112">Communication des composants</span><span class="sxs-lookup"><span data-stu-id="1faee-112">Component communication</span></span>

<span data-ttu-id="1faee-113">Pour s’assurer qu’il n’existe aucun lien direct entre les composants, MRTK v2 utilise des interfaces pour la communication entre les services, les fournisseurs de données et le code d’application.</span><span class="sxs-lookup"><span data-stu-id="1faee-113">To ensure that there are no direct links between components, MRTK v2 utilizes interfaces to communicate between services, data providers and application code.</span></span> <span data-ttu-id="1faee-114">ces interfaces sont définies dans et toutes les communications sont routées via la réalité mixte Shared Computer Toolkit composant principal.</span><span class="sxs-lookup"><span data-stu-id="1faee-114">These interfaces are defined in and all communication is routed through the Mixed Reality Toolkit core component.</span></span>

![Utilisation du système de sensibilisation spatiale via des interfaces](../features/images/packaging/AccessingViaInterfaces.png)

## <a name="minimizing-mrtk-import-footprint"></a><span data-ttu-id="1faee-116">Minimisation de l’encombrement de l’importation MRTK</span><span class="sxs-lookup"><span data-stu-id="1faee-116">Minimizing MRTK import footprint</span></span>

<span data-ttu-id="1faee-117">À ce stade, le MRTK est importé en tant que package de base unique (en ignorant pour un moment l’existence du package d’exemples, qui est un package entièrement facultatif).</span><span class="sxs-lookup"><span data-stu-id="1faee-117">At this moment, the MRTK is imported as a single foundation package (ignoring for a moment the existence of the examples package, which is a completely optional package).</span></span> <span data-ttu-id="1faee-118">Il est possible de réduire l’encombrement en réduisant manuellement les fichiers importés, bien qu’il s’agisse d’un processus très manuel qui ne dispose pas d’un guide bien défini.</span><span class="sxs-lookup"><span data-stu-id="1faee-118">It is possible to make this footprint smaller by manually cutting down on the files imported, though this is a highly manual process which doesn't have a well-defined guide.</span></span>

<span data-ttu-id="1faee-119">Il est possible de désactiver les éléments arbitraires pendant l’importation du package de Fondation.</span><span class="sxs-lookup"><span data-stu-id="1faee-119">It is possible to uncheck arbitrary items during the import of the Foundation package.</span></span> <span data-ttu-id="1faee-120">Toutefois, il n’est pas recommandé de le faire à une étape précoce du développement, car cela peut perturber les fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="1faee-120">However, it's not recommended to do this at an early stage in development as it might break functionality.</span></span> <span data-ttu-id="1faee-121">Après avoir déterminé le dernier ensemble de fonctionnalités d’une application, le nettoyage des fournisseurs et des services inutiles peut être effectué sur les dossiers suivants :</span><span class="sxs-lookup"><span data-stu-id="1faee-121">After having figured out the final feature set of an app, pruning unneeded providers and services can be done on the following folders:</span></span>

- <span data-ttu-id="1faee-122">MRTK/services</span><span class="sxs-lookup"><span data-stu-id="1faee-122">MRTK/Services</span></span>
- <span data-ttu-id="1faee-123">MRTK/fournisseurs</span><span class="sxs-lookup"><span data-stu-id="1faee-123">MRTK/Providers</span></span>
- <span data-ttu-id="1faee-124">MRTK/Kit de développement logiciel (SDK)/fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="1faee-124">MRTK/SDK/Features</span></span>

> [!NOTE]
> <span data-ttu-id="1faee-125">MRTK v2. x **_requiert_** le contenu du dossier Assets/MRTK/Core.</span><span class="sxs-lookup"><span data-stu-id="1faee-125">MRTK v2.x **_requires_** the contents of the Assets/MRTK/Core folder.</span></span>

## <a name="upcoming-features"></a><span data-ttu-id="1faee-126">Fonctionnalités à venir</span><span class="sxs-lookup"><span data-stu-id="1faee-126">Upcoming features</span></span>

### <a name="application-architecture"></a><span data-ttu-id="1faee-127">Architecture de l’application</span><span class="sxs-lookup"><span data-stu-id="1faee-127">Application architecture</span></span>

<span data-ttu-id="1faee-128">Le MRTK prend en charge l’activation des applications à l’aide d’une variété d’architectures, notamment :</span><span class="sxs-lookup"><span data-stu-id="1faee-128">The MRTK will have support to enable applications to be built with a variety of architectures, including:</span></span>

- [<span data-ttu-id="1faee-129">Localisateur de service MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="1faee-129">MixedRealityToolkit service locator</span></span>](#mixedrealitytoolkit-service-locator)
- [<span data-ttu-id="1faee-130">Services individuels</span><span class="sxs-lookup"><span data-stu-id="1faee-130">Individual services</span></span>](#individual-service-components)
- [<span data-ttu-id="1faee-131">Localisateur de service personnalisé</span><span class="sxs-lookup"><span data-stu-id="1faee-131">Custom service locator</span></span>](#custom-service-locator)
- [<span data-ttu-id="1faee-132">Architecture hybride</span><span class="sxs-lookup"><span data-stu-id="1faee-132">Hybrid architecture</span></span>](#hybrid-architecture)

<span data-ttu-id="1faee-133">Lors de la sélection d’une architecture d’application, il est important de prendre en compte la flexibilité de conception et les performances des applications.</span><span class="sxs-lookup"><span data-stu-id="1faee-133">When selecting an application architecture, it is important to consider design flexibility and application performance.</span></span> <span data-ttu-id="1faee-134">Les architectures décrites ici ne sont pas censées être adaptées à chaque application.</span><span class="sxs-lookup"><span data-stu-id="1faee-134">The architectures described here are not expected to be suitable for every application.</span></span>

#### <a name="mixedrealitytoolkit-service-locator"></a><span data-ttu-id="1faee-135">Localisateur de service MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="1faee-135">MixedRealityToolkit service locator</span></span>

<span data-ttu-id="1faee-136">Le MRTK permet (et configure automatiquement) des scènes d’application pour utiliser le [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) composant localisateur de service par défaut.</span><span class="sxs-lookup"><span data-stu-id="1faee-136">The MRTK enables (and automatically configures) application scenes to use the default [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) service locator component.</span></span> <span data-ttu-id="1faee-137">Ce composant prend en charge la configuration des systèmes MRTK et des fournisseurs de données par le biais des inspecteurs de configuration et gère les durées de vie des composants et les comportements de base (par exemple, quand mettre à jour).</span><span class="sxs-lookup"><span data-stu-id="1faee-137">This component includes support for configuring MRTK systems and data providers via configuration inspectors and manages component lifespans and core behaviors (ex: when to update).</span></span>

<span data-ttu-id="1faee-138">Tous les systèmes sont représentés dans l’inspecteur de configuration principal, qu’ils soient présents ou activés dans le projet.</span><span class="sxs-lookup"><span data-stu-id="1faee-138">All systems are represented in the core configuration inspector, regardless of whether or not they are present or enabled in the project.</span></span> <span data-ttu-id="1faee-139">Pour plus d’informations, consultez le Guide de configuration de la [réalité mixte](../configuration/mixed-reality-configuration-guide.md) .</span><span class="sxs-lookup"><span data-stu-id="1faee-139">Please see the [Mixed Reality Configuration Guide](../configuration/mixed-reality-configuration-guide.md) for more information.</span></span>

#### <a name="individual-service-components"></a><span data-ttu-id="1faee-140">Composants de service individuels</span><span class="sxs-lookup"><span data-stu-id="1faee-140">Individual service components</span></span>

<span data-ttu-id="1faee-141">Certains développeurs ont exprimé un souhait d’inclure des composants de service individuels dans la hiérarchie des scènes de l’application.</span><span class="sxs-lookup"><span data-stu-id="1faee-141">Some developers have expressed a desire to include individual service components into the application scene hierarchy.</span></span> <span data-ttu-id="1faee-142">Pour activer cette utilisation, les services doivent être encapsulés dans un bureau d’enregistrement personnalisé ou être auto-inscrits/auto-géré.</span><span class="sxs-lookup"><span data-stu-id="1faee-142">To enable this usage, services will either need to be encapsulated in a custom registrar or be self-registering / self-managing.</span></span>

<span data-ttu-id="1faee-143">Un service à inscription automatique implémenterait [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) et s’inscrit lui-même afin que le code de l’application puisse découvrir l’instance de service par le biais d’un registre.</span><span class="sxs-lookup"><span data-stu-id="1faee-143">A self-registering service would implement the [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) and register itself so that application code could discover the service instance via a registry.</span></span>

<span data-ttu-id="1faee-144">Un service de gestion automatique peut être implémenté en tant qu’objet singleton dans la hiérarchie de la scène.</span><span class="sxs-lookup"><span data-stu-id="1faee-144">A self-managing service could be implemented as a singleton object in the scene hierarchy.</span></span> <span data-ttu-id="1faee-145">Cet objet fournit une propriété d’instance que le code de l’application pourrait utiliser pour accéder directement aux fonctionnalités du service.</span><span class="sxs-lookup"><span data-stu-id="1faee-145">This object would provide and instance property which application code could use to directly access service functionality.</span></span>

#### <a name="custom-service-locator"></a><span data-ttu-id="1faee-146">Localisateur de service personnalisé</span><span class="sxs-lookup"><span data-stu-id="1faee-146">Custom service locator</span></span>

<span data-ttu-id="1faee-147">Certains développeurs ont demandé la possibilité de créer un composant de localisateur de service personnalisé.</span><span class="sxs-lookup"><span data-stu-id="1faee-147">Some developers have requested the ability to create a custom service locator component.</span></span> <span data-ttu-id="1faee-148">Les localisateurs de service personnalisés implémentent l' [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) interface et gèrent les comportements de cycle de vie et de base des services actifs.</span><span class="sxs-lookup"><span data-stu-id="1faee-148">Custom service locators would implement the [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) interface and manage the life cycle and core behaviors of active services.</span></span>

#### <a name="hybrid-architecture"></a><span data-ttu-id="1faee-149">Architecture hybride</span><span class="sxs-lookup"><span data-stu-id="1faee-149">Hybrid architecture</span></span>

<span data-ttu-id="1faee-150">Le MRTK prend en charge une architecture hybride dans laquelle les développeurs peuvent combiner les approches précédentes si nécessaire ou souhaité.</span><span class="sxs-lookup"><span data-stu-id="1faee-150">The MRTK will support a hybrid architecture in which developers can combine the previous approaches as needed or desired.</span></span> <span data-ttu-id="1faee-151">Par exemple, un développeur peut commencer par le [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) localisateur de service et ajouter un service à inscription automatique.</span><span class="sxs-lookup"><span data-stu-id="1faee-151">For example, a developer could start with the [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) service locator and add a self-registering service.</span></span>

> [!NOTE]
> <span data-ttu-id="1faee-152">Lorsque vous optez pour une architecture hybride, il est important d’être attentif à toute duplication de travail (par exemple, acquisition de données de contrôleur à partir de plusieurs composants).</span><span class="sxs-lookup"><span data-stu-id="1faee-152">When opting for a hybrid architecture, it is important to be mindful of any duplication of work (ex: acquiring controller data from multiple components).</span></span>
