---
title: Feuille de route
description: documentation pour le plan de la feuille de route de MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 03/03/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK
ms.openlocfilehash: b591d3ed7bd3c470bdf5b9598864f35963fb99a9957c5ceefdd1417372a3b97e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203231"
---
# <a name="roadmap"></a>Feuille de route

ce document décrit la feuille de route de la réalité mixte Shared Computer Toolkit. Notez que les éléments suivants reflètent le travail qui se trouve dans le développement et les dates cibles reflètent les estimations.

## <a name="current-release"></a>Version actuelle

Microsoft Mixed reality Shared Computer Toolkit v 2.6

## <a name="upcoming-releases"></a>Versions à venir

| Produit | Description | Durée | tableau de Project |
| --- | --- | --- | --- |
| [MRTK V 2.7](#270) | Itération suivante de MRTK | Mai 2021 | https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/14 |

Les mises en production sont centrées autour des thèmes (par ex., des fonctionnalités de grande taille) et sont planifiées pour s’exécuter environ toutes les 8-12 semaines.

les détails de la version, y compris les éléments du backlog, se trouvent sur les [pages de jalons GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/milestones). Le jeu complet de problèmes ouverts est également disponible sur [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).

## <a name="mixed-reality-toolkit-mrtk-roadmap"></a>feuille de route MRTK (Mixed reality Shared Computer Toolkit)

la Shared Computer Toolkit de la réalité mixte est conçue pour être transmise par conception à l’aide de la plate-forme XR. La boîte à outils prend actuellement en charge Unity 2019.4. x et Unity 2018.4. x.

> quand unity libère un produit LTS (Support à Long terme), la réalité mixte Shared Computer Toolkit est mise à jour vers la version LTS. bien que la réalité mixte Shared Computer Toolkit s’exécute sur la toute dernière version de la branche tech non bêta (ex : 2020,1) de unity, elle n’est pas officiellement prise en charge.

### <a name="270"></a>2.7.0

Nous sommes en train de planifier la version de 2.7.0 et vous aurez bientôt plus de mises à jour.
Pour obtenir l’état le plus récent de la version, consultez la [page jalon](https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/14).

État : planification

Chronologie cible : mai 2021

Thèmes :

- Stability 
- Expansion de la plateforme : OpenXR
- Expérience de l'utilisateur
- Formation pour développeurs
- Packaging

**Stabilité**

la qualité et la stabilité sont la priorité la plus haute pour cette version et toutes les versions Shared Computer Toolkit de la réalité mixte de Microsoft. Nous continuons à hiérarchiser les problèmes des clients et des partenaires qui ont un impact sur la stabilité des composants MRTK.

**Expansion de la plateforme : OpenXR**

L’équipe MRTK prend en charge l’avenir de la réalité mixte via [OpenXR](https://techcommunity.microsoft.com/t5/mixed-reality-blog/moving-forward-to-openxr/ba-p/1825672). La prise en charge de OpenXR est actuellement en cours de développement, avec la prise en charge de la version préliminaire initiale publiée dans MRTK 2.5.2.

**Expérience utilisateur**

Nous écoutons vos commentaires sur MRTK et vous recherchons des plans pour :

- Résolution des bogues
- Rendre les contrôles MRTK UX plus faciles à comprendre
- HoloLens Parité de l’interpréteur de commandes
- Tests pour vérifier que les fonctionnalités ne régressent pas

**Formation pour développeurs**

Nous avons migré notre documentation pour développeurs de GitHub vers une nouvelle plateforme de documentation ! Nous souhaitons connaître vos commentaires afin que nous puissions continuer à améliorer notre expérience de documentation pour les développeurs.
Nous disposons actuellement de [didacticiels MRTK](/windows/mixed-reality/develop/unity/tutorials) qui se trouvent dans une autre section de documents de réalité mixte. Nous allons migrer ces didacticiels en direct avec le reste de la documentation MRTK. 

**Packaging**

L' [outil Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) est un nouveau moyen pour les développeurs de découvrir, de mettre à jour et d’ajouter des packages de fonctionnalités de réalité mixte dans des projets Unity. Vous pouvez rechercher des packages par nom ou par catégorie, voir leurs dépendances et même voir les changements proposés pour votre fichier manifeste de projets avant l’importation. Nous avons l’intention de mettre à jour l’outil de la fonctionnalité de réalité mixte, car nous répondons aux demandes de fonctionnalités et aux bogues.

## <a name="backlog"></a>Backlog

La liste suivante met en évidence certains des investissements clés que l’équipe MRTK envisage de poursuivre.

- Expansion de la plateforme
- Extensibilité
- Modularité
- Fonctionnalités d’accessibilité
- Améliorations de la globalisation
- Support du service Cloud
- Outils
