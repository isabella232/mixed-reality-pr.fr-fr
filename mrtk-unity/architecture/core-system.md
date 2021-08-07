---
title: Système principal
description: Système d’entrée, gestionnaires d’appareils et fournisseurs de données dans MRTK
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, événements
ms.openlocfilehash: ff4c23b796374940de1a1de6b72e08702d6fd24f79234e8ef80dc1210d13d103
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190179"
---
# <a name="core-system"></a>Système principal

Au cœur du système d’entrée se trouve le [InputSystem](../features/input/overview.md), qui est un service responsable de l’initialisation et de l’utilisation de toutes les fonctionnalités d’entrée associées à MRTK.

> [!NOTE]
> Il est supposé que les lecteurs ont déjà lu et ont une compréhension de base de la section [terminologie](terminology.md) .

Ce service est responsable des tâches suivantes :

- Lecture du [profil de système d’entrée](../configuration/mixed-reality-configuration-guide.md#input-system-settings)
- Démarrage des [fournisseurs de données](../features/input/input-providers.md) configurés (par exemple, `Windows Mixed Reality Device Manager` et `OpenVR Device Manager` ).
- instanciation de [GazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider), qui est un composant qui est chargé de fournir des informations de point de vue de l’en-tête de style HoloLens (1re génération) en plus des informations sur le regard de style HoloLens 2.
- Instanciation de [FocusProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusProvider), qui est un composant responsable de la détermination des objets qui ont le focus. Cela est décrit plus en détail dans la section [pointeurs et Focus](controllers-pointers-and-focus.md#pointers-and-focus) de la documentation.
- Fourniture de points d’enregistrement pour tous les événements d’entrée (en tant qu' [écouteurs globaux](#global-listeners)).
- Fournir des fonctionnalités de répartition des événements pour ces événements d’entrée.

## <a name="input-events"></a>Événements d’entrée

Les événements d’entrée sont généralement déclenchés sur deux canaux différents :

### <a name="objects-in-focus"></a>Objets en focus

Les événements peuvent être envoyés directement à un GameObject qui a le focus. Par exemple, un objet peut avoir un script qui implémente [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) .
Cet objet recevrait des événements tactiles lorsqu’il était ciblé par une main qui lui est proche. Ces types d’événements vont « remonter » la hiérarchie GameObject jusqu’à ce qu’elle trouve un GameObject capable de gérer l’événement.

Pour ce faire, utilisez [ExecuteHierarchy](https://docs.unity3d.com/ScriptReference/EventSystems.ExecuteEvents.ExecuteHierarchy.html) à partir de l’implémentation du système d’entrée par défaut.

### <a name="global-listeners"></a>Écouteurs globaux

Les événements peuvent être envoyés à des écouteurs globaux. Il est possible de s’inscrire pour tous les événements d’entrée à l’aide de l’interface du système d’entrée [`IMixedRealityEventSystem`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityEventSystem) . Il est recommandé d’utiliser la méthode [RegisterHandler](xref:Microsoft.MixedReality.Toolkit.IMixedRealityEventSystem.RegisterHandler%2A) pour l’inscription pour les événements globaux-la fonction déconseillée `Register` entraîne la notification de tous les événements d’entrée par les écouteurs, plutôt que simplement les événements d’entrée d’un type particulier (où le type est défini par l’interface d’événement).

Notez que les [écouteurs de secours](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSystem.PushFallbackInputHandler%2A) sont un autre type d’écouteurs globaux qui sont également déconseillés, car ils recevront chaque événement d’entrée unique qui n’a pas été traité ailleurs dans la scène.

### <a name="order-of-event-dispatch"></a>Ordre de répartition des événements

En règle générale, les événements sont envoyés aux écouteurs de la manière suivante. Notez que si l’une des étapes ci-dessous marque l’événement comme [géré](https://docs.unity3d.com/ScriptReference/EventSystems.AbstractEventData-used.html), le processus de distribution d’événements s’arrête.

1. L’événement est envoyé aux écouteurs globaux.
2. L’événement est envoyé aux boîtes de dialogue modales de l’objet ayant le focus.
3. L’événement est envoyé à l’objet ayant le focus.
4. L’événement est envoyé aux écouteurs de secours.

## <a name="device-managers-and-data-providers"></a>Gestionnaires d’appareils et fournisseurs de données

ces entités sont chargées d’interfaçage avec les api de niveau inférieur (par exemple, les api Windows Mixed Reality ou les api OpenVR) et de traduire les données de ces systèmes dans celles qui correspondent aux abstractions d’entrée de niveau supérieur de MRTK. Ils sont chargés de la détection, de la création et de la gestion de la durée de vie des [contrôleurs](controllers-pointers-and-focus.md#controllers).

Le workflow de base d’un gestionnaire de périphériques implique les opérations suivantes :

1. Le gestionnaire de périphériques est instancié par le service du système d’entrée.
2. le gestionnaire de périphériques s’inscrit auprès de son système sous-jacent (par exemple, le gestionnaire de périphériques Windows Mixed Reality s’inscrit pour les événements [d’entrée](../features/input/input-events.md) et de [mouvement](../features/input/gestures.md#gesture-events) .
3. Elle crée des contrôleurs qu’elle découvre à partir du système sous-jacent (par exemple, le fournisseur peut détecter la présence de mains articulées).
4. Dans sa boucle Update (), appelez UpdateController () pour interroger le nouvel État du système sous-jacent et mettre à jour sa représentation de contrôleur.
