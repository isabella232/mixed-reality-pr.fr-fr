---
title: Vue d’ensemble du Portage
description: Vue d’ensemble des différentes options de Portage pour ramener les applications existantes à la réalité mixte.
author: hferrone
ms.author: v-hferrone
ms.date: 10/02/2020
ms.topic: article
keywords: Portage, Unity, intergiciel, Engine, UWP, Win32
ms.openlocfilehash: 074e0792a5ed43bb56b8f337613234efbd166eb7
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96443541"
---
# <a name="porting-overview"></a><span data-ttu-id="f8c8a-104">Vue d’ensemble du Portage</span><span class="sxs-lookup"><span data-stu-id="f8c8a-104">Porting overview</span></span>

<span data-ttu-id="f8c8a-105">En ce qui concerne le portage ou la mise à niveau de vos projets existants pour la réalité mixte, plusieurs scénarios peuvent s’appliquer selon que votre application a été créée avec Unity ou un moteur inréel, HoloLens (1re génération) ou HoloLens 2, ou SteamVR.</span><span class="sxs-lookup"><span data-stu-id="f8c8a-105">When it comes to porting or upgrading your existing projects for Mixed Reality, several scenarios may apply depending on whether your app was built with Unity or Unreal Engine, HoloLens (1st Gen) or HoloLens 2, or SteamVR.</span></span> <span data-ttu-id="f8c8a-106">Cette page de vue d’ensemble contient les recommandations actuelles pour chaque plateforme et appareil : Veillez à vérifier que ces processus sont toujours en cours de modification.</span><span class="sxs-lookup"><span data-stu-id="f8c8a-106">This overview page contains our current recommendations for each platform and device - be sure to check back as these processes are always changing.</span></span>

<span data-ttu-id="f8c8a-107">Tout d’abord, configurez votre projet cible en vous basant sur nos recommandations [Unity](#unity) et [inréelles](#unreal) , puis suivez un ou plusieurs de nos scénarios de Portage :</span><span class="sxs-lookup"><span data-stu-id="f8c8a-107">First, setup your project target based on either our [Unity](#unity) and [Unreal](#unreal) recommendations, then follow one or more of our porting scenarios:</span></span>

- [<span data-ttu-id="f8c8a-108">HoloLens (1re génération) à HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="f8c8a-108">HoloLens (1st Gen) to HoloLens 2</span></span>](#hololens-1st-gen-unity-apps-to-hololens-2)
- [<span data-ttu-id="f8c8a-109">Casques Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f8c8a-109">Windows Mixed Reality headsets</span></span>](#windows-mixed-reality-headsets)
- [<span data-ttu-id="f8c8a-110">Applications SteamVR</span><span class="sxs-lookup"><span data-stu-id="f8c8a-110">SteamVR apps</span></span>](#steamvr-applications)
- [<span data-ttu-id="f8c8a-111">applications UWP 2D</span><span class="sxs-lookup"><span data-stu-id="f8c8a-111">2D UWP apps</span></span>](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a><span data-ttu-id="f8c8a-112">Cibles de projet recommandées</span><span class="sxs-lookup"><span data-stu-id="f8c8a-112">Recommended project targets</span></span>

<span data-ttu-id="f8c8a-113">Il est important de maintenir à jour vos projets, que vous portiez ou non une application vers un autre appareil cible.</span><span class="sxs-lookup"><span data-stu-id="f8c8a-113">It's important to keep your projects up-to-date, whether or not your porting an app to another target device.</span></span> <span data-ttu-id="f8c8a-114">Reportez-vous aux ressources basées sur le moteur listées ci-dessous pour obtenir nos recommandations actuelles.</span><span class="sxs-lookup"><span data-stu-id="f8c8a-114">Refer to the engine-based resources listed below for our current recommendations.</span></span>

### <a name="unity"></a><span data-ttu-id="f8c8a-115">Unity</span><span class="sxs-lookup"><span data-stu-id="f8c8a-115">Unity</span></span>

<span data-ttu-id="f8c8a-116">Notre recommandation actuelle pour le développement Unity avec une réalité mixte est **unity 2019 LTS à l’aide du package XR hérité**.</span><span class="sxs-lookup"><span data-stu-id="f8c8a-116">Our current recommendation for Unity development with Mixed Reality is **Unity 2019 LTS using the Legacy XR package**.</span></span> <span data-ttu-id="f8c8a-117">Si votre projet utilise la boîte à outils de réalité mixte, vérifiez que vous disposez de la dernière version, qui est actuellement **MRTK-unity 2,5**.</span><span class="sxs-lookup"><span data-stu-id="f8c8a-117">If your project uses the Mixed Reality Toolkit, double-check that you're on the latest version, which is currently **MRTK-Unity 2.5**.</span></span>

> [!CAUTION]
> <span data-ttu-id="f8c8a-118">Si le kit de développement logiciel (SDK) XR est disponible avec cette version Unity, les ancres spatiales Azure ne sont actuellement pas compatibles avec cette installation.</span><span class="sxs-lookup"><span data-stu-id="f8c8a-118">While the XR SDK is available with this version of Unity, Azure Spatial Anchors is not currently compatible with this setup.</span></span> <span data-ttu-id="f8c8a-119">Cette recommandation sera mise à jour avec une version ultérieure du package d’ancrages spatiaux Azure pour Unity.</span><span class="sxs-lookup"><span data-stu-id="f8c8a-119">This recommendation will be updated with a future release of the Azure Spatial Anchors package for Unity.</span></span> 
> 
> * <span data-ttu-id="f8c8a-120">Si vous n’avez pas besoin d’ancres spatiales Azure, vous pouvez [configurer votre projet Unity pour XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) et [prendre en main MRTK et le kit de développement logiciel (SDK) XR](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithMRTKAndXRSDK.html).</span><span class="sxs-lookup"><span data-stu-id="f8c8a-120">If you don't need Azure Spatial Anchors, you can [configure your Unity project for XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) and [get started with MRTK and XR SDK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithMRTKAndXRSDK.html).</span></span>
> 
> * <span data-ttu-id="f8c8a-121">Si vous utilisez actuellement le kit de développement logiciel (SDK) XR dans votre projet et souhaitez utiliser des ancres spatiales Azure, désinstallez le kit de développement logiciel (SDK) XR et réinstallez le package XR hérité pour rétablir les paramètres de votre projet.</span><span class="sxs-lookup"><span data-stu-id="f8c8a-121">If you're currently using the XR SDK in your project and want to use Azure Spatial Anchors, uninstall XR SDK and reinstall the Legacy XR package to revert your project settings.</span></span>


### <a name="unreal"></a><span data-ttu-id="f8c8a-122">Unreal</span><span class="sxs-lookup"><span data-stu-id="f8c8a-122">Unreal</span></span> 

<span data-ttu-id="f8c8a-123">Notre recommandation actuelle pour le développement non réel avec la réalité mixte est le **moteur 4,26**.</span><span class="sxs-lookup"><span data-stu-id="f8c8a-123">Our current recommendation for Unreal development with Mixed Reality is **Unreal Engine 4.26**.</span></span> <span data-ttu-id="f8c8a-124">Si votre projet utilise les outils d’expérience utilisateur du kit de test de réalité mixte, assurez-vous que vous utilisez la version la plus récente, qui est actuellement **UXT 0,10**.</span><span class="sxs-lookup"><span data-stu-id="f8c8a-124">If your project uses the Mixed Reality Toolkit UX Tools, make sure you're using the latest version, which is currently **UXT 0.10**.</span></span>

## <a name="porting-scenarios"></a><span data-ttu-id="f8c8a-125">Scénarios de Portage</span><span class="sxs-lookup"><span data-stu-id="f8c8a-125">Porting scenarios</span></span>

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a><span data-ttu-id="f8c8a-126">Applications HoloLens (1re génération) Unity vers HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="f8c8a-126">HoloLens (1st Gen) Unity apps to HoloLens 2</span></span>

<span data-ttu-id="f8c8a-127">Si vous avez une application HoloLens (1re génération) Unity existante que vous souhaitez porter sur un HoloLens 2, suivez les instructions de notre article sur le [Portage hololens](../unity/mrtk-porting-guide.md).</span><span class="sxs-lookup"><span data-stu-id="f8c8a-127">If you have an existing HoloLens (1st Gen) Unity application that you'd like to port over to a HoloLens 2, follow the instructions in our [HoloLens porting article](../unity/mrtk-porting-guide.md).</span></span>

### <a name="windows-mixed-reality-headsets"></a><span data-ttu-id="f8c8a-128">Casques Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f8c8a-128">Windows Mixed Reality headsets</span></span>

<span data-ttu-id="f8c8a-129">Si vous avez créé du contenu pour d’autres appareils, tels que le rift Oculus ou la réverbération HP G2, vous devez recibler les kits de développement logiciel (SDK) de VR spécifiques au fournisseur et les API de mappage potentiellement entrant.</span><span class="sxs-lookup"><span data-stu-id="f8c8a-129">If you've built content for other devices, such as the Oculus Rift or HP Reverb G2, you'll need to re-target vendor-specific VR SDKs and potentially input mapping APIs.</span></span> <span data-ttu-id="f8c8a-130">Vous trouverez des informations à la fois pour les scénarios Unity et les scénarios de Portage inréel dans notre [Guide de portage des applications immersifs](porting-guides.md).</span><span class="sxs-lookup"><span data-stu-id="f8c8a-130">You can find information for both Unity and Unreal porting scenarios in our [immersive apps porting guide](porting-guides.md).</span></span>

### <a name="steamvr-applications"></a><span data-ttu-id="f8c8a-131">Applications SteamVR</span><span class="sxs-lookup"><span data-stu-id="f8c8a-131">SteamVR applications</span></span>

<span data-ttu-id="f8c8a-132">Pour toute expérience SteamVR que vous souhaitez mettre à jour pour les casques Windows mixtes, reportez-vous à notre [Guide de mise à jour SteamVR](updating-your-steamvr-application-for-windows-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="f8c8a-132">For any SteamVR experiences that you want to update for Windows Mixed Reality headsets, refer to our [SteamVR updating guide](updating-your-steamvr-application-for-windows-mixed-reality.md).</span></span>

### <a name="2d-universal-windows-applications"></a><span data-ttu-id="f8c8a-133">applications Windows universelles 2D</span><span class="sxs-lookup"><span data-stu-id="f8c8a-133">2D Universal Windows applications</span></span>

<span data-ttu-id="f8c8a-134">Si vous disposez d’une application UWP 2D existante que vous souhaitez porter vers un casque ou HoloLens Windows Mixed Reality, suivez les instructions de notre article Portage d' [applications UWP 2D pour Windows Mixed Reality](building-2d-apps.md) .</span><span class="sxs-lookup"><span data-stu-id="f8c8a-134">If you have an existing 2D UWP app that you'd like to port to either a Windows Mixed Reality immersive headset or HoloLens, follow the instructions in our [porting 2D UWP apps for Windows Mixed Reality](building-2d-apps.md) article.</span></span>

