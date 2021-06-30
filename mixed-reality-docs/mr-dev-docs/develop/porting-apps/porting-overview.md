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
# <a name="porting-overview"></a><span data-ttu-id="4bd65-104">Vue d’ensemble du portage</span><span class="sxs-lookup"><span data-stu-id="4bd65-104">Porting overview</span></span>

<span data-ttu-id="4bd65-105">En ce qui concerne le portage ou la mise à niveau de vos projets existants pour la réalité mixte, le parcours de Portage varie selon que votre application est générée avec Unity ou un moteur inexistant, et cible HoloLens (1re génération) ou HoloLens 2, ou SteamVR.</span><span class="sxs-lookup"><span data-stu-id="4bd65-105">When it comes to porting or upgrading your existing projects for Mixed Reality, your porting journey depends on whether your app is built with Unity or Unreal Engine, and targets HoloLens (1st Gen) or HoloLens 2, or SteamVR.</span></span> <span data-ttu-id="4bd65-106">Cette page de vue d’ensemble contient les recommandations actuelles pour chaque plateforme et appareil : Veillez à vérifier que ces processus sont toujours en cours de modification.</span><span class="sxs-lookup"><span data-stu-id="4bd65-106">This overview page contains our current recommendations for each platform and device - be sure to check back as these processes are always changing.</span></span>

<span data-ttu-id="4bd65-107">Tout d’abord, configurez votre cible de projet en fonction de nos recommandations [Unity](#unity) et des recommandations [inréelless](#unreal) , puis suivez un ou plusieurs de nos scénarios de Portage :</span><span class="sxs-lookup"><span data-stu-id="4bd65-107">First, set up your project target based on either our [Unity](#unity) and [Unreal](#unreal) recommendations, then follow one or more of our porting scenarios:</span></span>

- [<span data-ttu-id="4bd65-108">HoloLens (1re génération) à HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="4bd65-108">HoloLens (1st Gen) to HoloLens 2</span></span>](#hololens-1st-gen-unity-apps-to-hololens-2)
- [<span data-ttu-id="4bd65-109">Casques VR immersifs</span><span class="sxs-lookup"><span data-stu-id="4bd65-109">Immersive VR headsets</span></span>](#immersive-vr-headsets)
- [<span data-ttu-id="4bd65-110">applications UWP 2D</span><span class="sxs-lookup"><span data-stu-id="4bd65-110">2D UWP apps</span></span>](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a><span data-ttu-id="4bd65-111">Cibles de projet recommandées</span><span class="sxs-lookup"><span data-stu-id="4bd65-111">Recommended project targets</span></span>

<span data-ttu-id="4bd65-112">Il est important de tenir à jour vos projets, qu’il s’agisse du Portage d’une application vers un autre appareil cible.</span><span class="sxs-lookup"><span data-stu-id="4bd65-112">It's important to keep your projects up to date, whether your porting an app to another target device.</span></span> <span data-ttu-id="4bd65-113">Reportez-vous aux ressources basées sur le moteur listées ci-dessous pour obtenir nos recommandations actuelles.</span><span class="sxs-lookup"><span data-stu-id="4bd65-113">Refer to the engine-based resources listed below for our current recommendations.</span></span>

### <a name="unity"></a><span data-ttu-id="4bd65-114">Unity</span><span class="sxs-lookup"><span data-stu-id="4bd65-114">Unity</span></span>

<span data-ttu-id="4bd65-115">Consultez la page [choisir une version Unity](../unity/choosing-unity-version.md) pour obtenir des conseils à jour sur les versions Unity et MRTK recommandées.</span><span class="sxs-lookup"><span data-stu-id="4bd65-115">See the [Choosing a Unity version](../unity/choosing-unity-version.md) page for up-to-date guidance on the recommended Unity and MRTK versions.</span></span>

### <a name="unreal"></a><span data-ttu-id="4bd65-116">Unreal</span><span class="sxs-lookup"><span data-stu-id="4bd65-116">Unreal</span></span>

<span data-ttu-id="4bd65-117">Consultez la page [configuration de votre projet inréaliste](../unreal/unreal-project-setup.md) pour obtenir des conseils à jour sur les versions de MRTK et inréelles recommandées.</span><span class="sxs-lookup"><span data-stu-id="4bd65-117">See the [Setting up your Unreal project](../unreal/unreal-project-setup.md) page for up-to-date guidance on the recommended Unreal and MRTK versions.</span></span>

## <a name="porting-scenarios"></a><span data-ttu-id="4bd65-118">Scénarios de Portage</span><span class="sxs-lookup"><span data-stu-id="4bd65-118">Porting scenarios</span></span>

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a><span data-ttu-id="4bd65-119">Applications HoloLens (1re génération) Unity vers HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="4bd65-119">HoloLens (1st Gen) Unity apps to HoloLens 2</span></span>

<span data-ttu-id="4bd65-120">Si vous avez une application HoloLens (1re génération) Unity existante que vous souhaitez porter sur un HoloLens 2, suivez les instructions de notre article sur le [Portage hololens](./porting-hl1-hl2.md).</span><span class="sxs-lookup"><span data-stu-id="4bd65-120">If you have an existing HoloLens (1st Gen) Unity application that you'd like to port over to a HoloLens 2, follow the instructions in our [HoloLens porting article](./porting-hl1-hl2.md).</span></span>

### <a name="immersive-vr-headsets"></a><span data-ttu-id="4bd65-121">Casques VR immersifs</span><span class="sxs-lookup"><span data-stu-id="4bd65-121">Immersive VR headsets</span></span>

<span data-ttu-id="4bd65-122">Si vous avez créé du contenu pour d’autres appareils VR, vous devez recibler les kits de développement logiciel (SDK) de VR spécifiques au fournisseur et les API de mappage d’entrée potentielles.</span><span class="sxs-lookup"><span data-stu-id="4bd65-122">If you've built content for other VR devices, you'll need to retarget any vendor-specific VR SDKs and potentially input-mapping APIs.</span></span> <span data-ttu-id="4bd65-123">Vous trouverez des informations à la fois pour les scénarios Unity et les scénarios de Portage inréel dans notre [Guide de portage des applications immersifs](porting-guides.md).</span><span class="sxs-lookup"><span data-stu-id="4bd65-123">You can find information for both Unity and Unreal porting scenarios in our [immersive apps porting guide](porting-guides.md).</span></span>

<span data-ttu-id="4bd65-124">Pour les expériences SteamVR que vous souhaitez mettre à jour pour les casques Windows mixtes, reportez-vous à notre [Guide de mise à jour SteamVR](updating-your-steamvr-application-for-windows-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="4bd65-124">For SteamVR experiences that you want to update for Windows Mixed Reality headsets, refer to our [SteamVR updating guide](updating-your-steamvr-application-for-windows-mixed-reality.md).</span></span>

### <a name="2d-universal-windows-applications"></a><span data-ttu-id="4bd65-125">applications Windows universelles 2D</span><span class="sxs-lookup"><span data-stu-id="4bd65-125">2D Universal Windows applications</span></span>

<span data-ttu-id="4bd65-126">Si vous disposez d’une application UWP 2D existante que vous souhaitez porter vers un casque ou HoloLens Windows Mixed Reality, suivez nos instructions sur le [Portage d’applications UWP 2D pour Windows Mixed Reality](building-2d-apps.md) .</span><span class="sxs-lookup"><span data-stu-id="4bd65-126">If you have an existing 2D UWP app that you'd like to port to either a Windows Mixed Reality immersive headset or HoloLens, follow our [porting 2D UWP apps for Windows Mixed Reality](building-2d-apps.md) instructions.</span></span>