---
title: Vue d’ensemble du portage
description: Vue d’ensemble des différentes options de Portage pour intégrer vos applications existantes à la réalité mixte pour HoloLens et VR.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: Portage, Unity, intergiciel, Engine, UWP, Win32
ms.openlocfilehash: 268d98b45aa659614e0266bfd1add7c7ed2f684a
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583585"
---
# <a name="porting-overview"></a>Vue d’ensemble du portage

En ce qui concerne le portage ou la mise à niveau de vos projets existants pour la réalité mixte, le parcours de Portage varie selon que votre application est générée avec Unity ou un moteur inexistant, et cible HoloLens (1re génération) ou HoloLens 2, ou SteamVR. Cette page de vue d’ensemble contient les recommandations actuelles pour chaque plateforme et appareil : Veillez à vérifier que ces processus sont toujours en cours de modification.

Tout d’abord, configurez votre cible de projet en fonction de nos recommandations [Unity](#unity) et des recommandations [inréelless](#unreal) , puis suivez un ou plusieurs de nos scénarios de Portage :

- [HoloLens (1re génération) à HoloLens 2](#hololens-1st-gen-unity-apps-to-hololens-2)
- [Casques Windows Mixed Reality](#windows-mixed-reality-headsets)
- [Applications SteamVR](#steamvr-applications)
- [applications UWP 2D](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a>Cibles de projet recommandées

Il est important de tenir à jour vos projets, qu’il s’agisse du Portage d’une application vers un autre appareil cible. Reportez-vous aux ressources basées sur le moteur listées ci-dessous pour obtenir nos recommandations actuelles.

### <a name="unity"></a>Unity

Notre recommandation actuelle pour le développement Unity avec une réalité mixte est **unity 2019 LTS à l’aide du package XR hérité**. Si votre projet utilise la boîte à outils de réalité mixte, vérifiez que vous disposez de la dernière version, qui est actuellement **MRTK-unity 2,5**.

> [!CAUTION]
> Si le kit de développement logiciel (SDK) XR est disponible avec cette version Unity, les ancres spatiales Azure ne sont actuellement pas compatibles avec cette installation. Cette recommandation sera mise à jour avec une version ultérieure du package d’ancrages spatiaux Azure pour Unity. 
> 
> * Si vous n’avez pas besoin d’ancres spatiales Azure, vous pouvez [configurer votre projet Unity pour XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) et [prendre en main MRTK et le kit de développement logiciel (SDK) XR](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithMRTKAndXRSDK.html).
> 
> * Si vous utilisez actuellement le kit de développement logiciel (SDK) XR dans votre projet et souhaitez utiliser des ancres spatiales Azure, désinstallez le kit de développement logiciel (SDK) XR et réinstallez le package XR hérité pour rétablir les paramètres de votre projet.


### <a name="unreal"></a>Unreal 

Notre recommandation actuelle pour le développement non réel avec la réalité mixte est le **moteur 4,26**. Si votre projet utilise les outils d’expérience utilisateur du kit de test de réalité mixte, assurez-vous que vous utilisez la version la plus récente, qui est actuellement **UXT 0,10**.

## <a name="porting-scenarios"></a>Scénarios de Portage

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a>Applications HoloLens (1re génération) Unity vers HoloLens 2

Si vous avez une application HoloLens (1re génération) Unity existante que vous souhaitez porter sur un HoloLens 2, suivez les instructions de notre article sur le [Portage hololens](./porting-hl1-hl2.md).

### <a name="windows-mixed-reality-headsets"></a>Casques Windows Mixed Reality

Si vous avez créé du contenu pour d’autres appareils, tels que le rift Oculus ou la réverbération HP G2, vous devez recibler les kits de développement logiciel (SDK) de VR spécifiques au fournisseur et les API de mappage d’entrée potentielles. Vous trouverez des informations à la fois pour les scénarios Unity et les scénarios de Portage inréel dans notre [Guide de portage des applications immersifs](porting-guides.md).

### <a name="steamvr-applications"></a>Applications SteamVR

Pour toute expérience SteamVR que vous souhaitez mettre à jour pour les casques Windows mixtes, reportez-vous à notre [Guide de mise à jour SteamVR](updating-your-steamvr-application-for-windows-mixed-reality.md).

### <a name="2d-universal-windows-applications"></a>applications Windows universelles 2D

Si vous disposez d’une application UWP 2D existante que vous souhaitez porter vers un casque ou HoloLens Windows Mixed Reality, suivez nos instructions sur le [Portage d’applications UWP 2D pour Windows Mixed Reality](building-2d-apps.md) .