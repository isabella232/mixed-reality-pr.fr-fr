---
title: Présentation du service physique de la main
description: documentation relative à l’utilisation du service d’extension physique de main dans MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 751aec148d3a40da4728d2fdd60a60402b59a4de
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145085"
---
# <a name="hand-physics-extension-service"></a><span data-ttu-id="3277e-104">Main service extension physique</span><span class="sxs-lookup"><span data-stu-id="3277e-104">Hand physics extension service</span></span>

![Main service extension physique](../images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)

<span data-ttu-id="3277e-106">La main physique service Active les événements de collision de corps rigides et les interactions avec les mains articulées.</span><span class="sxs-lookup"><span data-stu-id="3277e-106">The hand physics service enables rigid body collision events and interactions with articulated hands.</span></span>

## <a name="enabling-the-extension"></a><span data-ttu-id="3277e-107">Activation de l’extension</span><span class="sxs-lookup"><span data-stu-id="3277e-107">Enabling the extension</span></span>

<span data-ttu-id="3277e-108">Pour activer l’extension, ouvrez votre profil RegisteredServiceProvider.</span><span class="sxs-lookup"><span data-stu-id="3277e-108">To enable the extension, open your RegisteredServiceProvider profile.</span></span> <span data-ttu-id="3277e-109">Cliquez `Register a new Service Provider` pour ajouter une nouvelle configuration.</span><span class="sxs-lookup"><span data-stu-id="3277e-109">Click `Register a new Service Provider` to add a new configuration.</span></span> <span data-ttu-id="3277e-110">Dans le champ type de composant, sélectionnez HandPhysicsService.</span><span class="sxs-lookup"><span data-stu-id="3277e-110">In the component type field, select HandPhysicsService.</span></span> <span data-ttu-id="3277e-111">Dans le champ Profil de configuration, sélectionnez le profil physique de la main par défaut inclus avec l’extension.</span><span class="sxs-lookup"><span data-stu-id="3277e-111">In the configuration Profile field, select the default hand physics profile included with the extension.</span></span>

## <a name="profile-options"></a><span data-ttu-id="3277e-112">Options de profil</span><span class="sxs-lookup"><span data-stu-id="3277e-112">Profile options</span></span>

### <a name="hand-physics-layer"></a><span data-ttu-id="3277e-113">Couche physique de la main</span><span class="sxs-lookup"><span data-stu-id="3277e-113">Hand physics layer</span></span>

<span data-ttu-id="3277e-114">Contrôle la couche à laquelle les jointures de la main instanciée vont.</span><span class="sxs-lookup"><span data-stu-id="3277e-114">Controls the layer the instantiated hand joints will go to.</span></span>

<span data-ttu-id="3277e-115">Si le service utilise par défaut la couche « par défaut » (0), il est recommandé d’utiliser une couche distincte pour les objets physique de la main.</span><span class="sxs-lookup"><span data-stu-id="3277e-115">While the service defaults to the "default" layer (0), it is recommended to use a separate layer for hand physics objects.</span></span> <span data-ttu-id="3277e-116">Dans le cas contraire, il peut y avoir des conflits indésirables et/ou des raycasts inexacts.</span><span class="sxs-lookup"><span data-stu-id="3277e-116">Otherwise there may be unwanted collisions and/or inaccurate raycasts.</span></span>

### <a name="finger-tip-kinematic-body-prefab"></a><span data-ttu-id="3277e-117">Corps cinématique de l’info-bulle Prefab</span><span class="sxs-lookup"><span data-stu-id="3277e-117">Finger tip kinematic body prefab</span></span>

<span data-ttu-id="3277e-118">Contrôle quel Prefab est instancié à portée de main.</span><span class="sxs-lookup"><span data-stu-id="3277e-118">Controls which prefab is instantiated on fingertips.</span></span> <span data-ttu-id="3277e-119">Pour que le service fonctionne comme prévu, Prefab nécessite les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="3277e-119">In order for the service to work as expected, the prefab requires:</span></span>

- <span data-ttu-id="3277e-120">Un composant RigidBody, avec isKinematic activé</span><span class="sxs-lookup"><span data-stu-id="3277e-120">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="3277e-121">Un conflit</span><span class="sxs-lookup"><span data-stu-id="3277e-121">A collider</span></span>
- <span data-ttu-id="3277e-122">Composant `JointKinematicBody`</span><span class="sxs-lookup"><span data-stu-id="3277e-122">`JointKinematicBody` component</span></span>

### <a name="use-palm-kinematic-body"></a><span data-ttu-id="3277e-123">Utiliser le corps cinématique Palm</span><span class="sxs-lookup"><span data-stu-id="3277e-123">Use palm kinematic body</span></span>

<span data-ttu-id="3277e-124">Contrôle si le service tente d’instancier un Prefab sur l’articulation Palm.</span><span class="sxs-lookup"><span data-stu-id="3277e-124">Controls whether the service will attempt to instantiate a prefab on the palm joint.</span></span>

### <a name="palm-kinematic-body-prefab"></a><span data-ttu-id="3277e-125">Corps cinématique Palm Prefab</span><span class="sxs-lookup"><span data-stu-id="3277e-125">Palm kinematic body prefab</span></span>

<span data-ttu-id="3277e-126">Lorsque `UsePalmKinematicBody` est activé, il s’agit du Prefab qu’il instanciera.</span><span class="sxs-lookup"><span data-stu-id="3277e-126">When `UsePalmKinematicBody` is enabled, this is the prefab it will instantiate.</span></span> <span data-ttu-id="3277e-127">À l’instar `FingerTipKinematicBodyPrefab` de, ce Prefab requiert :</span><span class="sxs-lookup"><span data-stu-id="3277e-127">Just like `FingerTipKinematicBodyPrefab`, this prefab requires:</span></span>

- <span data-ttu-id="3277e-128">Un composant RigidBody, avec isKinematic activé</span><span class="sxs-lookup"><span data-stu-id="3277e-128">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="3277e-129">Un conflit</span><span class="sxs-lookup"><span data-stu-id="3277e-129">A collider</span></span>
- <span data-ttu-id="3277e-130">Composant `JointKinematicBody`</span><span class="sxs-lookup"><span data-stu-id="3277e-130">`JointKinematicBody` component</span></span>

## <a name="how-to-use-the-service"></a><span data-ttu-id="3277e-131">Comment utiliser le service</span><span class="sxs-lookup"><span data-stu-id="3277e-131">How to use the service</span></span>

<span data-ttu-id="3277e-132">Une fois activé, utilisez la propriété de tout conflit `IsTrigger` pour recevoir les événements de collision des 10 chiffres (et des palmiers s’ils sont activés).</span><span class="sxs-lookup"><span data-stu-id="3277e-132">Once enabled, use any collider's `IsTrigger` property to receive collision events from all 10 digits (and palms if they're enabled).</span></span>
