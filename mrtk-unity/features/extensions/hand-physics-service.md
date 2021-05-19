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
# <a name="hand-physics-extension-service"></a>Main service extension physique

![Main service extension physique](../images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)

La main physique service Active les événements de collision de corps rigides et les interactions avec les mains articulées.

## <a name="enabling-the-extension"></a>Activation de l’extension

Pour activer l’extension, ouvrez votre profil RegisteredServiceProvider. Cliquez `Register a new Service Provider` pour ajouter une nouvelle configuration. Dans le champ type de composant, sélectionnez HandPhysicsService. Dans le champ Profil de configuration, sélectionnez le profil physique de la main par défaut inclus avec l’extension.

## <a name="profile-options"></a>Options de profil

### <a name="hand-physics-layer"></a>Couche physique de la main

Contrôle la couche à laquelle les jointures de la main instanciée vont.

Si le service utilise par défaut la couche « par défaut » (0), il est recommandé d’utiliser une couche distincte pour les objets physique de la main. Dans le cas contraire, il peut y avoir des conflits indésirables et/ou des raycasts inexacts.

### <a name="finger-tip-kinematic-body-prefab"></a>Corps cinématique de l’info-bulle Prefab

Contrôle quel Prefab est instancié à portée de main. Pour que le service fonctionne comme prévu, Prefab nécessite les éléments suivants :

- Un composant RigidBody, avec isKinematic activé
- Un conflit
- Composant `JointKinematicBody`

### <a name="use-palm-kinematic-body"></a>Utiliser le corps cinématique Palm

Contrôle si le service tente d’instancier un Prefab sur l’articulation Palm.

### <a name="palm-kinematic-body-prefab"></a>Corps cinématique Palm Prefab

Lorsque `UsePalmKinematicBody` est activé, il s’agit du Prefab qu’il instanciera. À l’instar `FingerTipKinematicBodyPrefab` de, ce Prefab requiert :

- Un composant RigidBody, avec isKinematic activé
- Un conflit
- Composant `JointKinematicBody`

## <a name="how-to-use-the-service"></a>Comment utiliser le service

Une fois activé, utilisez la propriété de tout conflit `IsTrigger` pour recevoir les événements de collision des 10 chiffres (et des palmiers s’ils sont activés).
