---
title: Vue d'ensemble des entrées
description: Vue d’ensemble du système d’entrée dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: b175b16e2004fb00cef430335751c3aabc8c59fdd4ae78a2fc78c959a92240fb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219758"
---
# <a name="input-overview"></a>Vue d’ensemble de l’entrée

Le système d’entrée de MRTK vous permet d’effectuer les opérations suivantes :

- Consommez les entrées de diverses sources d’entrée, telles que 6 contrôleurs DDL, mains articulées ou discours, via des événements d’entrée.
- Définissez des actions abstraites, telles que *Select* ou *menu*, et associez-les à différentes entrées.
- Des pointeurs d’installation attachés aux contrôleurs pour piloter les composants de l’interface utilisateur via des événements Focus et pointeur.

<img src="../images/input/MRTK_InputSystem.png" alt="Input System" style="display:block;margin-left:auto;margin-right:auto;">
<sup>Vue d’ensemble du système d’entrée MRTK</sup>

Les entrées sont produites par les [**fournisseurs de données d’entrée (gestionnaire de périphériques)**](input-providers.md). chaque fournisseur correspond à une source particulière d’entrée : Open VR, Windows Mixed Reality (WMR), Joystick unity, Windows Speech, etc. les fournisseurs sont ajoutés à votre projet par le biais du **profil des fournisseurs de services inscrits** dans le composant Shared Computer Toolkit de la *réalité mixte* et produisent automatiquement des [**événements d’entrée**](input-events.md) lorsque les sources d’entrée correspondantes sont disponibles (par exemple, lorsqu’un contrôleur WMR est détecté ou qu’un boîtier de commande est connecté).

Les [**actions d’entrée**](input-actions.md) sont des abstractions sur les entrées brutes destinées à aider à isoler la logique d’application des sources d’entrée spécifiques produisant une entrée. Il peut être utile, par exemple, de définir une action *Select* et de la mapper au bouton gauche de la souris, un bouton dans un boîtier de commande et un déclencheur dans un contrôleur 6 DDL. Vous pouvez ensuite faire en sorte que la logique de votre application écoute les événements de l’action d’entrée *Select* au lieu d’avoir à connaître toutes les différentes entrées pouvant la produire. les actions d’entrée sont définies dans le **profil actions d’entrée**, situé dans le *profil de système d’entrée* dans le composant Shared Computer Toolkit de la *réalité mixte* .

Les [**contrôleurs**](controllers.md) sont créés par des *fournisseurs d’entrée* lorsque des appareils d’entrée sont détectés et détruits lorsqu’ils sont perdus ou déconnectés. Le fournisseur d’entrée WMR, par exemple, va créer des *contrôleurs WMR* pour 6 appareils DDL et des *contrôleurs de main WMR articulés* pour les mains articulées. Les entrées de contrôleur peuvent être mappées à des actions d’entrée via le **profil de mappage du contrôleur**, à l’intérieur du profil de *système d’entrée*. Les événements d’entrée déclenchés par les contrôleurs incluent l’action d’entrée associée, le cas échéant.

Les contrôleurs peuvent avoir des [**pointeurs**](pointers.md) attachés qui interrogent la scène pour déterminer l’objet de jeu actif et déclencher des [**événements de pointeur**](pointers.md#pointer-event-interfaces) dessus. À titre d’exemple, notre *pointeur de ligne* effectue un raycast par rapport à la scène à l’aide de la pose du contrôleur pour calculer l’origine et la direction du rayon. Les pointeurs créés pour chaque contrôleur sont configurés dans le **profil de pointeur**, sous le *profil de système d’entrée*.

<img src="../images/input/MRTK_Input_EventFlow.png" width="200px" alt="Event Flow" style="display:block;margin-left:auto;margin-right:auto;">
<sup>Workflow d’événement.</sup>

Bien que vous puissiez gérer des [événements d’entrée directement dans des composants de l’interface utilisateur](input-events.md), il est recommandé d’utiliser des [événements de pointeur](pointers.md#pointer-event-interfaces) pour conserver l’implémentation indépendamment du périphérique.

MRTK fournit également plusieurs méthodes pratiques pour interroger l’état d’entrée directement d’une manière indépendante du périphérique. Pour plus d’informations, consultez accès à l' [État d’entrée dans MRTK](input-state.md) .
