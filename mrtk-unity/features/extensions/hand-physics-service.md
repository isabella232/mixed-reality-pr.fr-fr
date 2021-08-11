---
title: Service de physique des mains
description: documentation relative à l’utilisation du service d’extension physique de main dans MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: f54f8dabddba03bc279a090bf1c62b25656e64109b3b5671a4ed50d070445f14
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221725"
---
# <a name="hand-physics-service"></a>Service de physique des mains

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
