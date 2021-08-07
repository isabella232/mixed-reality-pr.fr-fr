---
title: Vue d’ensemble du portage
description: vue d’ensemble des différentes options de portage pour intégrer vos applications existantes à la réalité mixte pour HoloLens et VR.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: Portage, Unity, intergiciel, Engine, UWP, Win32
ms.openlocfilehash: 519dae088e689e0a6e617bf5e2b34f81cc2e265256c4844df7dd34e99172d536
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189419"
---
# <a name="porting-overview"></a>Vue d’ensemble du portage

en ce qui concerne le portage ou la mise à niveau de vos projets existants pour la réalité mixte, le parcours de portage varie selon que votre application est générée avec unity ou un moteur inréel, et qu’elle cible HoloLens (1er génération) ou HoloLens 2 ou SteamVR. Cette page de vue d’ensemble contient les recommandations actuelles pour chaque plateforme et appareil : Veillez à vérifier que ces processus sont toujours en cours de modification.

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

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a>HoloLens (1ère génération) applications unity à HoloLens 2

si vous disposez d’une application HoloLens (1re génération) unity que vous souhaitez porter sur un HoloLens 2, suivez les instructions de notre article sur le [portage des HoloLens](./porting-hl1-hl2.md).

### <a name="immersive-vr-headsets"></a>Casques VR immersifs

Si vous avez créé du contenu pour d’autres appareils VR, vous devez recibler les kits de développement logiciel (SDK) de VR spécifiques au fournisseur et les API de mappage d’entrée potentielles. Vous trouverez des informations à la fois pour les scénarios Unity et les scénarios de Portage inréel dans notre [Guide de portage des applications immersifs](porting-guides.md).

pour les expériences SteamVR que vous souhaitez mettre à jour pour Windows Mixed Reality casques, reportez-vous à notre [guide de mise à jour SteamVR](updating-your-steamvr-application-for-windows-mixed-reality.md).

### <a name="2d-universal-windows-applications"></a>applications de Windows universelles 2d

si vous disposez d’une application uwp 2d existante que vous souhaitez porter vers un Windows Mixed Reality casque ou HoloLens, suivez nos instructions sur le [portage des applications uwp 2d pour](building-2d-apps.md) obtenir des instructions Windows Mixed Reality.