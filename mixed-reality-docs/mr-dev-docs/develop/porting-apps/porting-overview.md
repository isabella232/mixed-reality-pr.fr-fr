---
title: Vue d’ensemble du portage
description: Vue d’ensemble des différentes options de Portage pour intégrer vos applications existantes à la réalité mixte pour HoloLens et VR.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: Portage, Unity, intergiciel, Engine, UWP, Win32
ms.openlocfilehash: 693891d67ae26098f0810a539059da8d34f4731c
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759110"
---
# <a name="porting-overview"></a><span data-ttu-id="f1041-104">Vue d’ensemble du portage</span><span class="sxs-lookup"><span data-stu-id="f1041-104">Porting overview</span></span>

<span data-ttu-id="f1041-105">En ce qui concerne le portage ou la mise à niveau de vos projets existants pour la réalité mixte, le parcours de Portage varie selon que votre application est générée avec Unity ou un moteur inexistant, et cible HoloLens (1re génération) ou HoloLens 2, ou SteamVR.</span><span class="sxs-lookup"><span data-stu-id="f1041-105">When it comes to porting or upgrading your existing projects for Mixed Reality, your porting journey depends on whether your app is built with Unity or Unreal Engine, and targets HoloLens (1st Gen) or HoloLens 2, or SteamVR.</span></span> <span data-ttu-id="f1041-106">Cette page de vue d’ensemble contient les recommandations actuelles pour chaque plateforme et appareil : Veillez à vérifier que ces processus sont toujours en cours de modification.</span><span class="sxs-lookup"><span data-stu-id="f1041-106">This overview page contains our current recommendations for each platform and device - be sure to check back as these processes are always changing.</span></span>

<span data-ttu-id="f1041-107">Tout d’abord, configurez votre cible de projet en fonction de nos recommandations [Unity](#unity) et des recommandations [inréelless](#unreal) , puis suivez un ou plusieurs de nos scénarios de Portage :</span><span class="sxs-lookup"><span data-stu-id="f1041-107">First, set up your project target based on either our [Unity](#unity) and [Unreal](#unreal) recommendations, then follow one or more of our porting scenarios:</span></span>

- [<span data-ttu-id="f1041-108">HoloLens (1re génération) à HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="f1041-108">HoloLens (1st Gen) to HoloLens 2</span></span>](#hololens-1st-gen-unity-apps-to-hololens-2)
- [<span data-ttu-id="f1041-109">Casques Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f1041-109">Windows Mixed Reality headsets</span></span>](#windows-mixed-reality-headsets)
- [<span data-ttu-id="f1041-110">Applications SteamVR</span><span class="sxs-lookup"><span data-stu-id="f1041-110">SteamVR apps</span></span>](#steamvr-applications)
- [<span data-ttu-id="f1041-111">applications UWP 2D</span><span class="sxs-lookup"><span data-stu-id="f1041-111">2D UWP apps</span></span>](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a><span data-ttu-id="f1041-112">Cibles de projet recommandées</span><span class="sxs-lookup"><span data-stu-id="f1041-112">Recommended project targets</span></span>

<span data-ttu-id="f1041-113">Il est important de tenir à jour vos projets, qu’il s’agisse du Portage d’une application vers un autre appareil cible.</span><span class="sxs-lookup"><span data-stu-id="f1041-113">It's important to keep your projects up to date, whether your porting an app to another target device.</span></span> <span data-ttu-id="f1041-114">Reportez-vous aux ressources basées sur le moteur listées ci-dessous pour obtenir nos recommandations actuelles.</span><span class="sxs-lookup"><span data-stu-id="f1041-114">Refer to the engine-based resources listed below for our current recommendations.</span></span>

### <a name="unity"></a><span data-ttu-id="f1041-115">Unity</span><span class="sxs-lookup"><span data-stu-id="f1041-115">Unity</span></span>

<span data-ttu-id="f1041-116">Notre recommandation actuelle pour le développement Unity avec une réalité mixte est **unity 2019 LTS à l’aide du package XR hérité**.</span><span class="sxs-lookup"><span data-stu-id="f1041-116">Our current recommendation for Unity development with Mixed Reality is **Unity 2019 LTS using the Legacy XR package**.</span></span> <span data-ttu-id="f1041-117">Si votre projet utilise la boîte à outils de réalité mixte, vérifiez que vous disposez de la dernière version, qui est actuellement **MRTK-unity 2,5**.</span><span class="sxs-lookup"><span data-stu-id="f1041-117">If your project uses the Mixed Reality Toolkit, double-check that you're on the latest version, which is currently **MRTK-Unity 2.5**.</span></span>

> [!CAUTION]
> <span data-ttu-id="f1041-118">Si le kit de développement logiciel (SDK) XR est disponible avec cette version Unity, les ancres spatiales Azure ne sont actuellement pas compatibles avec cette installation.</span><span class="sxs-lookup"><span data-stu-id="f1041-118">While the XR SDK is available with this version of Unity, Azure Spatial Anchors is not currently compatible with this setup.</span></span> <span data-ttu-id="f1041-119">Cette recommandation sera mise à jour avec une version ultérieure du package d’ancrages spatiaux Azure pour Unity.</span><span class="sxs-lookup"><span data-stu-id="f1041-119">This recommendation will be updated with a future release of the Azure Spatial Anchors package for Unity.</span></span> 
> 
> * <span data-ttu-id="f1041-120">Si vous n’avez pas besoin d’ancres spatiales Azure, vous pouvez [configurer votre projet Unity pour XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) et [prendre en main MRTK et le kit de développement logiciel (SDK) XR](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/configuration/getting-started-with-mrtk-and-xrsdk.md).</span><span class="sxs-lookup"><span data-stu-id="f1041-120">If you don't need Azure Spatial Anchors, you can [configure your Unity project for XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) and [get started with MRTK and XR SDK](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/configuration/getting-started-with-mrtk-and-xrsdk.md).</span></span>
> 
> * <span data-ttu-id="f1041-121">Si vous utilisez actuellement le kit de développement logiciel (SDK) XR dans votre projet et souhaitez utiliser des ancres spatiales Azure, désinstallez le kit de développement logiciel (SDK) XR et réinstallez le package XR hérité pour rétablir les paramètres de votre projet.</span><span class="sxs-lookup"><span data-stu-id="f1041-121">If you're currently using the XR SDK in your project and want to use Azure Spatial Anchors, uninstall XR SDK and reinstall the Legacy XR package to revert your project settings.</span></span>


### <a name="unreal"></a><span data-ttu-id="f1041-122">Unreal</span><span class="sxs-lookup"><span data-stu-id="f1041-122">Unreal</span></span> 

<span data-ttu-id="f1041-123">Notre recommandation actuelle pour le développement non réel avec la réalité mixte est le **moteur 4,26**.</span><span class="sxs-lookup"><span data-stu-id="f1041-123">Our current recommendation for Unreal development with Mixed Reality is **Unreal Engine 4.26**.</span></span> <span data-ttu-id="f1041-124">Si votre projet utilise les outils d’expérience utilisateur du kit de test de réalité mixte, assurez-vous que vous utilisez la version la plus récente, qui est actuellement **UXT 0,10**.</span><span class="sxs-lookup"><span data-stu-id="f1041-124">If your project uses the Mixed Reality Toolkit UX Tools, make sure you're using the latest version, which is currently **UXT 0.10**.</span></span>

## <a name="porting-scenarios"></a><span data-ttu-id="f1041-125">Scénarios de Portage</span><span class="sxs-lookup"><span data-stu-id="f1041-125">Porting scenarios</span></span>

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a><span data-ttu-id="f1041-126">Applications HoloLens (1re génération) Unity vers HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="f1041-126">HoloLens (1st Gen) Unity apps to HoloLens 2</span></span>

<span data-ttu-id="f1041-127">Si vous avez une application HoloLens (1re génération) Unity existante que vous souhaitez porter sur un HoloLens 2, suivez les instructions de notre article sur le [Portage hololens](./porting-hl1-hl2.md).</span><span class="sxs-lookup"><span data-stu-id="f1041-127">If you have an existing HoloLens (1st Gen) Unity application that you'd like to port over to a HoloLens 2, follow the instructions in our [HoloLens porting article](./porting-hl1-hl2.md).</span></span>

### <a name="windows-mixed-reality-headsets"></a><span data-ttu-id="f1041-128">Casques Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f1041-128">Windows Mixed Reality headsets</span></span>

<span data-ttu-id="f1041-129">Si vous avez créé du contenu pour d’autres appareils, tels que le rift Oculus ou la réverbération HP G2, vous devez recibler les kits de développement logiciel (SDK) de VR spécifiques au fournisseur et les API de mappage d’entrée potentielles.</span><span class="sxs-lookup"><span data-stu-id="f1041-129">If you've built content for other devices, such as the Oculus Rift or HP Reverb G2, you'll need to retarget vendor-specific VR SDKs and potentially input-mapping APIs.</span></span> <span data-ttu-id="f1041-130">Vous trouverez des informations à la fois pour les scénarios Unity et les scénarios de Portage inréel dans notre [Guide de portage des applications immersifs](porting-guides.md).</span><span class="sxs-lookup"><span data-stu-id="f1041-130">You can find information for both Unity and Unreal porting scenarios in our [immersive apps porting guide](porting-guides.md).</span></span>

### <a name="steamvr-applications"></a><span data-ttu-id="f1041-131">Applications SteamVR</span><span class="sxs-lookup"><span data-stu-id="f1041-131">SteamVR applications</span></span>

<span data-ttu-id="f1041-132">Pour toute expérience SteamVR que vous souhaitez mettre à jour pour les casques Windows mixtes, reportez-vous à notre [Guide de mise à jour SteamVR](updating-your-steamvr-application-for-windows-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="f1041-132">For any SteamVR experiences that you want to update for Windows Mixed Reality headsets, refer to our [SteamVR updating guide](updating-your-steamvr-application-for-windows-mixed-reality.md).</span></span>

### <a name="2d-universal-windows-applications"></a><span data-ttu-id="f1041-133">applications Windows universelles 2D</span><span class="sxs-lookup"><span data-stu-id="f1041-133">2D Universal Windows applications</span></span>

<span data-ttu-id="f1041-134">Si vous disposez d’une application UWP 2D existante que vous souhaitez porter vers un casque ou HoloLens Windows Mixed Reality, suivez nos instructions sur le [Portage d’applications UWP 2D pour Windows Mixed Reality](building-2d-apps.md) .</span><span class="sxs-lookup"><span data-stu-id="f1041-134">If you have an existing 2D UWP app that you'd like to port to either a Windows Mixed Reality immersive headset or HoloLens, follow our [porting 2D UWP apps for Windows Mixed Reality](building-2d-apps.md) instructions.</span></span>