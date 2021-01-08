---
title: Vue d’ensemble du développement natif
description: Apprenez à créer un moteur de réalité mixte DirectX à l’aide des API Windows Mixed Reality directement.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: DirectX, rendu holographique, native, application native, WinRT, application WinRT, API de plateforme, moteur personnalisé, intergiciel, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle
ms.openlocfilehash: 764cbe0a37501cc176e9bb05a9a7771b03666f0c
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006849"
---
# <a name="native-development-overview"></a><span data-ttu-id="e4911-104">Vue d’ensemble du développement natif</span><span class="sxs-lookup"><span data-stu-id="e4911-104">Native development overview</span></span>

![Logo de bannière Native](../images/native_logo_banner.png)

<span data-ttu-id="e4911-106">les moteurs 3D comme [Unity](../unity/unity-development-overview.md) ou [Unreal](../unreal/unreal-development-overview.md) ne sont pas les seuls chemins de développement de réalité mixte qui vous sont ouverts.</span><span class="sxs-lookup"><span data-stu-id="e4911-106">3D engines like [Unity](../unity/unity-development-overview.md) or [Unreal](../unreal/unreal-development-overview.md) aren't the only Mixed Reality development paths open to you.</span></span> <span data-ttu-id="e4911-107">Vous pouvez également créer des applications de réalité mixte à l’aide des API Windows Mixed Reality avec DirectX 11 ou DirectX 12.</span><span class="sxs-lookup"><span data-stu-id="e4911-107">You can also create Mixed Reality apps using the Windows Mixed Reality APIs with DirectX 11 or DirectX 12.</span></span> <span data-ttu-id="e4911-108">En accédant à la source de la plateforme, vous créez essentiellement votre propre infrastructure ou intergiciel.</span><span class="sxs-lookup"><span data-stu-id="e4911-108">By going to the platform source, you're essentially building your own middleware or framework.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="e4911-109">Si vous avez un projet WinRT existant que vous souhaitez conserver, accédez à notre [documentation WinRT](creating-a-holographic-directx-project.md)principale.</span><span class="sxs-lookup"><span data-stu-id="e4911-109">If you have an existing WinRT project that you'd like to maintain, head over to our main [WinRT documentation](creating-a-holographic-directx-project.md).</span></span> 

## <a name="development-checkpoints"></a><span data-ttu-id="e4911-110">Points de contrôle de développement</span><span class="sxs-lookup"><span data-stu-id="e4911-110">Development checkpoints</span></span>

<span data-ttu-id="e4911-111">Utilisez les points de contrôle suivants pour intégrer vos jeux et applications Unity dans le monde de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="e4911-111">Use the following checkpoints to bring your Unity games and applications into the world of mixed reality.</span></span>

### <a name="1-getting-started"></a><span data-ttu-id="e4911-112">1. Mise en route</span><span class="sxs-lookup"><span data-stu-id="e4911-112">1. Getting started</span></span>

<span data-ttu-id="e4911-113">Windows Mixed Reality prend en charge [deux types d’applications](../../design/app-views.md):</span><span class="sxs-lookup"><span data-stu-id="e4911-113">Windows Mixed Reality supports [two kinds of apps](../../design/app-views.md):</span></span>
* <span data-ttu-id="e4911-114">Applications UWP ou de **réalité mixte** Win32 qui utilisent l' [API HOLOGRAPHICSPACE](getting-a-holographicspace.md) ou l' [API OpenXR](openxr.md) pour afficher un [affichage immersif](../../design/app-views.md) qui remplit l’affichage du casque</span><span class="sxs-lookup"><span data-stu-id="e4911-114">UWP or Win32 **Mixed Reality applications** that use the [HolographicSpace API](getting-a-holographicspace.md) or [OpenXR API](openxr.md) to render an [immersive view](../../design/app-views.md) that fills the headset display</span></span>
* <span data-ttu-id="e4911-115">**applications 2D** (UWP) qui utilisent DirectX, XAML ou une autre infrastructure pour restituer des [vues 2D](../../design/app-views.md#2d-views) sur des ardoises dans la page d’hébergement de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="e4911-115">**2D apps** (UWP) that use DirectX, XAML, or another framework to render [2D views](../../design/app-views.md#2d-views) on slates in the Windows Mixed Reality home</span></span>

<span data-ttu-id="e4911-116">Les différences entre le développement DirectX pour les [vues 2D et les vues immersives](../../design/app-views.md) concernent principalement le rendu holographique et l’entrée spatiale.</span><span class="sxs-lookup"><span data-stu-id="e4911-116">The differences between DirectX development for [2D views and immersive views](../../design/app-views.md) primarily concern holographic rendering and spatial input.</span></span> <span data-ttu-id="e4911-117">Le [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) de votre application UWP ou le HWND de votre application Win32 sont requis et restent en grande partie les mêmes.</span><span class="sxs-lookup"><span data-stu-id="e4911-117">Your UWP application's [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) or your Win32 application's HWND are required and remain largely the same.</span></span> <span data-ttu-id="e4911-118">Il en va de même pour les API WinRT qui sont disponibles pour votre application.</span><span class="sxs-lookup"><span data-stu-id="e4911-118">The same is true for the WinRT APIs that are available to your app.</span></span> <span data-ttu-id="e4911-119">Toutefois, vous devez utiliser un sous-ensemble différent de ces API pour tirer parti des fonctionnalités holographiques.</span><span class="sxs-lookup"><span data-stu-id="e4911-119">But you must use a different subset of these APIs to take advantage of holographic features.</span></span> <span data-ttu-id="e4911-120">Par exemple, le système pour les applications holographiques gère le utilise permutation et le frame présent pour activer une boucle de frames prédite.</span><span class="sxs-lookup"><span data-stu-id="e4911-120">For example, the system for holographic applications manages the swapchain and frame present to enable a pose-predicted frame loop.</span></span>

[!INCLUDE[](../includes/native-getting-started.md)]

### <a name="2-core-building-blocks"></a><span data-ttu-id="e4911-121">2. Fonctionnalités principales</span><span class="sxs-lookup"><span data-stu-id="e4911-121">2. Core building blocks</span></span>

<span data-ttu-id="e4911-122">Les applications Windows Mixed Reality utilisent les API suivantes pour créer des expériences de [réalité mixte](../../discover/mixed-reality.md) pour HoloLens et d’autres casques immersifs :</span><span class="sxs-lookup"><span data-stu-id="e4911-122">Windows Mixed Reality applications use the following APIs to build [mixed-reality](../../discover/mixed-reality.md) experiences for HoloLens and other immersive headsets:</span></span>

|  <span data-ttu-id="e4911-123">Fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="e4911-123">Feature</span></span>  |  <span data-ttu-id="e4911-124">Utilité</span><span class="sxs-lookup"><span data-stu-id="e4911-124">Capability</span></span>  |
| --- | --- |
| [<span data-ttu-id="e4911-125">Pointage du regard</span><span class="sxs-lookup"><span data-stu-id="e4911-125">Gaze</span></span>](../../design/gaze-and-commit.md) | <span data-ttu-id="e4911-126">Autorisez des utilisateurs à cibler des hologrammes en les regardant</span><span class="sxs-lookup"><span data-stu-id="e4911-126">Let users target holograms with by looking at them</span></span> |
| [<span data-ttu-id="e4911-127">Mouvement</span><span class="sxs-lookup"><span data-stu-id="e4911-127">Gesture</span></span>](../../design/gaze-and-commit.md#composite-gestures) | <span data-ttu-id="e4911-128">Ajouter des actions spatiales à vos applications</span><span class="sxs-lookup"><span data-stu-id="e4911-128">Add spatial actions to your apps</span></span> |
| [<span data-ttu-id="e4911-129">Rendu holographique</span><span class="sxs-lookup"><span data-stu-id="e4911-129">Holographic rendering</span></span>](../platform-capabilities-and-apis/rendering.md) | <span data-ttu-id="e4911-130">Dessinez un hologramme à un endroit précis dans le monde autour de vos utilisateurs</span><span class="sxs-lookup"><span data-stu-id="e4911-130">Draw a hologram at a precise location in the world around your users</span></span> |
| [<span data-ttu-id="e4911-131">Contrôleur de mouvement</span><span class="sxs-lookup"><span data-stu-id="e4911-131">Motion controller</span></span>](../../design/motion-controllers.md) | <span data-ttu-id="e4911-132">Permettez aux utilisateurs de prendre des mesures dans vos environnements de réalité mixte</span><span class="sxs-lookup"><span data-stu-id="e4911-132">Let your users take action in your Mixed Reality environments</span></span> |
| [<span data-ttu-id="e4911-133">Mappage spatial</span><span class="sxs-lookup"><span data-stu-id="e4911-133">Spatial mapping</span></span>](../../design/spatial-mapping.md) | <span data-ttu-id="e4911-134">Mappez votre espace physique avec une superposition de maillage virtuel afin de marquer les limites de votre environnement</span><span class="sxs-lookup"><span data-stu-id="e4911-134">Map your physical space with a virtual mesh overlay to mark the boundaries of your environment</span></span> |
| [<span data-ttu-id="e4911-135">Voice</span><span class="sxs-lookup"><span data-stu-id="e4911-135">Voice</span></span>](../../design/voice-input.md) | <span data-ttu-id="e4911-136">Capturez des mots clés, des expressions et une dictée à partir de vos utilisateurs</span><span class="sxs-lookup"><span data-stu-id="e4911-136">Capture spoken keywords, phrases, and dictation from your users</span></span> |
 
> [!NOTE]
> <span data-ttu-id="e4911-137">Vous trouverez des fonctionnalités de base à venir et en développement dans la documentation de la feuille de [route](openxr.md#roadmap) OpenXR.</span><span class="sxs-lookup"><span data-stu-id="e4911-137">You can find upcoming and in-development core features in the OpenXR [roadmap](openxr.md#roadmap) documentation.</span></span>

### <a name="3-deploying-and-testing"></a><span data-ttu-id="e4911-138">3. déploiement et test</span><span class="sxs-lookup"><span data-stu-id="e4911-138">3. Deploying and testing</span></span>

<span data-ttu-id="e4911-139">Vous pouvez développer sur un ordinateur de bureau à l’aide de OpenXR sur un casque d’architecture HoloLens 2 ou Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="e4911-139">You can develop on a desktop using OpenXR on a HoloLens 2 or Windows Mixed Reality immersive headset.</span></span>  <span data-ttu-id="e4911-140">Si vous n’avez pas accès à un casque, vous pouvez utiliser l' [émulateur HoloLens 2](../platform-capabilities-and-apis/using-the-hololens-emulator.md) ou [Windows Mixed Reality Simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="e4911-140">If you don't have access to a headset, you can use the [HoloLens 2 Emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md) or the [Windows Mixed Reality Simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) instead.</span></span>

## <a name="whats-next"></a><span data-ttu-id="e4911-141">Quelle est l’étape suivante ?</span><span class="sxs-lookup"><span data-stu-id="e4911-141">What's next?</span></span>

<span data-ttu-id="e4911-142">Le travail d’un développeur n’est jamais terminé, en particulier lorsqu’il s’agit d’apprendre un nouvel outil ou SDK.</span><span class="sxs-lookup"><span data-stu-id="e4911-142">A developer's job is never done, especially when learning a new tool or SDK.</span></span> <span data-ttu-id="e4911-143">Les sections suivantes peuvent vous permettre d’aller au-delà des éléments de niveau débutant que vous avez déjà effectués.</span><span class="sxs-lookup"><span data-stu-id="e4911-143">The following sections can take you into areas beyond the beginner level material you've already completed.</span></span> <span data-ttu-id="e4911-144">Ces rubriques et ressources ne sont pas dans un ordre séquentiel. n’hésitez pas à vous plonger dans l’exploration.</span><span class="sxs-lookup"><span data-stu-id="e4911-144">These topics and resources aren't in any sequential order, so feel free to jump around and explore!</span></span>

### <a name="additional-resources"></a><span data-ttu-id="e4911-145">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="e4911-145">Additional resources</span></span>

<span data-ttu-id="e4911-146">Si vous envisagez de monter en charge votre jeu OpenXR, consultez les liens ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="e4911-146">If you're looking to level up your OpenXR game, check out the links below:</span></span>

* [<span data-ttu-id="e4911-147">Bonnes pratiques sur OpenXR</span><span class="sxs-lookup"><span data-stu-id="e4911-147">OpenXR best practices</span></span>](openxr-best-practices.md)
* [<span data-ttu-id="e4911-148">Performances OpenXR</span><span class="sxs-lookup"><span data-stu-id="e4911-148">OpenXR performance</span></span>](openxr-performance.md)
* [<span data-ttu-id="e4911-149">Résolution des problèmes OpenXR</span><span class="sxs-lookup"><span data-stu-id="e4911-149">OpenXR troubleshooting</span></span>](openxr-troubleshooting.md)

## <a name="see-also"></a><span data-ttu-id="e4911-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4911-150">See also</span></span>
* [<span data-ttu-id="e4911-151">Modèle d’application</span><span class="sxs-lookup"><span data-stu-id="e4911-151">App model</span></span>](../../design/app-model.md)
* [<span data-ttu-id="e4911-152">Vues d’applications</span><span class="sxs-lookup"><span data-stu-id="e4911-152">App views</span></span>](../../design/app-views.md)
