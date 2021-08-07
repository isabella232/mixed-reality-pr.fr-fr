---
title: Vue d’ensemble de l’architecture
description: Vue d’ensemble de l’architecture de MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, Architecture MRTK,
ms.openlocfilehash: 7113ee68a3d8bae016236996725a879c95e31f410cb273184ddcc255ae7a0685
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186598"
---
# <a name="architecture-overview"></a>Vue d’ensemble de l’architecture

Pour une introduction générale au contenu de MRTK, les informations d’architecture contenues dans ce document vous aideront à comprendre les éléments suivants :

- Grandes parties de MRTK et leur mode de connexion
- Les concepts introduits par MRTK peuvent ne pas exister dans vanille Unity
- Fonctionnement de certains des systèmes plus grands (tels que l’entrée)

Cette section n’est pas destinée à vous apprendre à effectuer des tâches, mais plutôt à la façon dont ces tâches sont structurées et pourquoi.

## <a name="many-audiences-one-toolkit"></a>Nombreux publics, un seul Toolkit

MRTK n’a pas d’audience unique et uniforme. Elle a été écrite pour prendre en charge des cas d’utilisation allant de la première hackathons à des individus développant des expériences complexes et partagées pour l’entreprise. Du code et des API ont peut-être été écrits et optimisés pour l’un des autres (par exemple, certaines parties du MRTK semblent plus optimisées pour une « configuration en un clic »), mais il est important de noter que certaines d’entre elles sont plus nombreuses pour des raisons d’historique et de réapprovisionnement. À mesure que MRTK évolue, les fonctionnalités générées doivent être conçues pour être mises à l’échelle pour prendre en charge la plage de cas d’usage.

MRTK a également besoin d’une mise à l’échelle normale pour les expériences VR et AR. il devrait être facile de créer des applications qui se déploient correctement dans un comportement lors du déploiement sur un HoloLens 2 ou un HoloLens 1, et il est préférable de créer des applications ciblant OpenVR et WMR (et d’autres plateformes). Alors que l’équipe peut parfois concentrer une itération particulière sur un système ou une plateforme spécifique, l’objectif à long terme est de créer un large éventail de prise en charge pour chaque fois que des utilisateurs créent des expériences de réalité mixte.

## <a name="high-level-breakdown"></a>Répartition générale

Le MRTK est à la fois un ensemble d’outils permettant d’obtenir rapidement les expériences de la réalité mixte (MR), ainsi qu’une infrastructure d’application avec des opinions sur son propre Runtime, sur la façon dont il doit être étendu et sur la façon dont il doit être configuré.

À un niveau élevé, les MRTK peuvent être décomposées des manières suivantes :

![Diagramme de vue d’ensemble de l’architecture](../features/images/architecture/MRTK_Architecture.png)

Le MRTK contient également un autre ensemble d’utilitaires de poche qui n’ont pas de dépendances au reste du MRTK (pour en répertorier quelques-uns : outils de génération, solveurs, influenceurs audio, utilitaires de lissage et convertisseurs de ligne).

Le reste de la documentation sur l’architecture sera créé de bas en haut, en partant de l’infrastructure et du runtime, en progressant vers des systèmes plus intéressants et complexes, tels que l’entrée. Consultez la table des matières pour continuer avec la vue d’ensemble de l’architecture.
