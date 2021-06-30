---
title: Vue d’ensemble du portage
description: Vue d’ensemble des différentes options de Portage pour intégrer vos applications existantes à la réalité mixte pour HoloLens et VR.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: Portage, Unity, intergiciel, Engine, UWP, Win32
ms.openlocfilehash: 167559d69cc4e65f971a8970b56e41e6e3ca8b22
ms.sourcegitcommit: 12ea3fb2df4664c5efd07dcbb9040c2ff173afb6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2021
ms.locfileid: "113042270"
---
# <a name="porting-overview"></a>Vue d’ensemble du portage

En ce qui concerne le portage ou la mise à niveau de vos projets existants pour la réalité mixte, le parcours de Portage varie selon que votre application est générée avec Unity ou un moteur inexistant, et cible HoloLens (1re génération) ou HoloLens 2, ou SteamVR. Cette page de vue d’ensemble contient les recommandations actuelles pour chaque plateforme et appareil : Veillez à vérifier que ces processus sont toujours en cours de modification.

Tout d’abord, configurez votre cible de projet en fonction de nos recommandations [Unity](#unity) et des recommandations [inréelless](#unreal) , puis suivez un ou plusieurs de nos scénarios de Portage :

- [HoloLens (1re génération) à HoloLens 2](#hololens-1st-gen-unity-apps-to-hololens-2)
- [Casques VR immersifs](#immersive-vr-headsets)
- [applications UWP 2D](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a>Cibles de projet recommandées

Il est important de tenir à jour vos projets, qu’il s’agisse du Portage d’une application vers un autre appareil cible. Reportez-vous aux ressources basées sur le moteur listées ci-dessous pour obtenir nos recommandations actuelles.

### <a name="unity"></a>Unity

Consultez la page [choisir une version Unity](../unity/choosing-unity-version.md) pour obtenir des conseils à jour sur les versions Unity et MRTK recommandées.

### <a name="unreal"></a>Unreal

Consultez la page [configuration de votre projet inréaliste](../unreal/unreal-project-setup.md) pour obtenir des conseils à jour sur les versions de MRTK et inréelles recommandées.

## <a name="porting-scenarios"></a>Scénarios de Portage

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a>Applications HoloLens (1re génération) Unity vers HoloLens 2

Si vous avez une application HoloLens (1re génération) Unity existante que vous souhaitez porter sur un HoloLens 2, suivez les instructions de notre article sur le [Portage hololens](./porting-hl1-hl2.md).

### <a name="immersive-vr-headsets"></a>Casques VR immersifs

Si vous avez créé du contenu pour d’autres appareils VR, vous devez recibler les kits de développement logiciel (SDK) de VR spécifiques au fournisseur et les API de mappage d’entrée potentielles. Vous trouverez des informations à la fois pour les scénarios Unity et les scénarios de Portage inréel dans notre [Guide de portage des applications immersifs](porting-guides.md).

Pour les expériences SteamVR que vous souhaitez mettre à jour pour les casques Windows mixtes, reportez-vous à notre [Guide de mise à jour SteamVR](updating-your-steamvr-application-for-windows-mixed-reality.md).

### <a name="2d-universal-windows-applications"></a>applications Windows universelles 2D

Si vous disposez d’une application UWP 2D existante que vous souhaitez porter vers un casque ou HoloLens Windows Mixed Reality, suivez nos instructions sur le [Portage d’applications UWP 2D pour Windows Mixed Reality](building-2d-apps.md) .