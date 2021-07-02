---
title: Main physique service
description: documentation relative à l’utilisation du service d’extension physique de main dans MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: af7ea753d52b5e478c54ca19d6d8e391401eea6d
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176251"
---
# <a name="hand-physics-service"></a><span data-ttu-id="609e2-104">Main physique service</span><span class="sxs-lookup"><span data-stu-id="609e2-104">Hand physics service</span></span>

![Main service extension physique](../images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)

<span data-ttu-id="609e2-106">La main physique service Active les événements de collision de corps rigides et les interactions avec les mains articulées.</span><span class="sxs-lookup"><span data-stu-id="609e2-106">The hand physics service enables rigid body collision events and interactions with articulated hands.</span></span>

## <a name="enabling-the-extension"></a><span data-ttu-id="609e2-107">Activation de l’extension</span><span class="sxs-lookup"><span data-stu-id="609e2-107">Enabling the extension</span></span>

<span data-ttu-id="609e2-108">Pour activer l’extension, ouvrez votre profil RegisteredServiceProvider.</span><span class="sxs-lookup"><span data-stu-id="609e2-108">To enable the extension, open your RegisteredServiceProvider profile.</span></span> <span data-ttu-id="609e2-109">Cliquez `Register a new Service Provider` pour ajouter une nouvelle configuration.</span><span class="sxs-lookup"><span data-stu-id="609e2-109">Click `Register a new Service Provider` to add a new configuration.</span></span> <span data-ttu-id="609e2-110">Dans le champ type de composant, sélectionnez HandPhysicsService.</span><span class="sxs-lookup"><span data-stu-id="609e2-110">In the component type field, select HandPhysicsService.</span></span> <span data-ttu-id="609e2-111">Dans le champ Profil de configuration, sélectionnez le profil physique de la main par défaut inclus avec l’extension.</span><span class="sxs-lookup"><span data-stu-id="609e2-111">In the configuration Profile field, select the default hand physics profile included with the extension.</span></span>

## <a name="profile-options"></a><span data-ttu-id="609e2-112">Options de profil</span><span class="sxs-lookup"><span data-stu-id="609e2-112">Profile options</span></span>

### <a name="hand-physics-layer"></a><span data-ttu-id="609e2-113">Couche physique de la main</span><span class="sxs-lookup"><span data-stu-id="609e2-113">Hand physics layer</span></span>

<span data-ttu-id="609e2-114">Contrôle la couche à laquelle les jointures de la main instanciée vont.</span><span class="sxs-lookup"><span data-stu-id="609e2-114">Controls the layer the instantiated hand joints will go to.</span></span>

<span data-ttu-id="609e2-115">Si le service utilise par défaut la couche « par défaut » (0), il est recommandé d’utiliser une couche distincte pour les objets physique de la main.</span><span class="sxs-lookup"><span data-stu-id="609e2-115">While the service defaults to the "default" layer (0), it is recommended to use a separate layer for hand physics objects.</span></span> <span data-ttu-id="609e2-116">Dans le cas contraire, il peut y avoir des conflits indésirables et/ou des raycasts inexacts.</span><span class="sxs-lookup"><span data-stu-id="609e2-116">Otherwise there may be unwanted collisions and/or inaccurate raycasts.</span></span>

### <a name="finger-tip-kinematic-body-prefab"></a><span data-ttu-id="609e2-117">Corps cinématique de l’info-bulle Prefab</span><span class="sxs-lookup"><span data-stu-id="609e2-117">Finger tip kinematic body prefab</span></span>

<span data-ttu-id="609e2-118">Contrôle quel Prefab est instancié à portée de main.</span><span class="sxs-lookup"><span data-stu-id="609e2-118">Controls which prefab is instantiated on fingertips.</span></span> <span data-ttu-id="609e2-119">Pour que le service fonctionne comme prévu, Prefab nécessite les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="609e2-119">In order for the service to work as expected, the prefab requires:</span></span>

- <span data-ttu-id="609e2-120">Un composant RigidBody, avec isKinematic activé</span><span class="sxs-lookup"><span data-stu-id="609e2-120">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="609e2-121">Un conflit</span><span class="sxs-lookup"><span data-stu-id="609e2-121">A collider</span></span>
- <span data-ttu-id="609e2-122">Composant `JointKinematicBody`</span><span class="sxs-lookup"><span data-stu-id="609e2-122">`JointKinematicBody` component</span></span>

### <a name="use-palm-kinematic-body"></a><span data-ttu-id="609e2-123">Utiliser le corps cinématique Palm</span><span class="sxs-lookup"><span data-stu-id="609e2-123">Use palm kinematic body</span></span>

<span data-ttu-id="609e2-124">Contrôle si le service tente d’instancier un Prefab sur l’articulation Palm.</span><span class="sxs-lookup"><span data-stu-id="609e2-124">Controls whether the service will attempt to instantiate a prefab on the palm joint.</span></span>

### <a name="palm-kinematic-body-prefab"></a><span data-ttu-id="609e2-125">Corps cinématique Palm Prefab</span><span class="sxs-lookup"><span data-stu-id="609e2-125">Palm kinematic body prefab</span></span>

<span data-ttu-id="609e2-126">Lorsque `UsePalmKinematicBody` est activé, il s’agit du Prefab qu’il instanciera.</span><span class="sxs-lookup"><span data-stu-id="609e2-126">When `UsePalmKinematicBody` is enabled, this is the prefab it will instantiate.</span></span> <span data-ttu-id="609e2-127">À l’instar `FingerTipKinematicBodyPrefab` de, ce Prefab requiert :</span><span class="sxs-lookup"><span data-stu-id="609e2-127">Just like `FingerTipKinematicBodyPrefab`, this prefab requires:</span></span>

- <span data-ttu-id="609e2-128">Un composant RigidBody, avec isKinematic activé</span><span class="sxs-lookup"><span data-stu-id="609e2-128">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="609e2-129">Un conflit</span><span class="sxs-lookup"><span data-stu-id="609e2-129">A collider</span></span>
- <span data-ttu-id="609e2-130">Composant `JointKinematicBody`</span><span class="sxs-lookup"><span data-stu-id="609e2-130">`JointKinematicBody` component</span></span>

## <a name="how-to-use-the-service"></a><span data-ttu-id="609e2-131">Comment utiliser le service</span><span class="sxs-lookup"><span data-stu-id="609e2-131">How to use the service</span></span>

<span data-ttu-id="609e2-132">Une fois activé, utilisez la propriété de tout conflit `IsTrigger` pour recevoir les événements de collision des 10 chiffres (et des palmiers s’ils sont activés).</span><span class="sxs-lookup"><span data-stu-id="609e2-132">Once enabled, use any collider's `IsTrigger` property to receive collision events from all 10 digits (and palms if they're enabled).</span></span>
