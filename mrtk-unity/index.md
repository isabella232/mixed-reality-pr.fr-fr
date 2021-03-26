---
title: Documentation sur le développement avec MRTK-Unity
description: Découvrez le Mixed Reality Toolkit (MRTK) pour Unity.
author: polar-kev
ms.author: kesemple
ms.date: 03/03/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 85a203f22c62871265f7775c364f5388194b53a1
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550969"
---
# <a name="what-is-the-mixed-reality-toolkit"></a><span data-ttu-id="b4794-104">Présentation du Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="b4794-104">What is the Mixed Reality Toolkit</span></span>

![Mixed Reality Toolkit](features/images/Logo_MRTK_Unity_Banner.png)

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/qfONlUCSWdg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<span data-ttu-id="b4794-106">MRTK-Unity est un projet Microsoft qui fournit un ensemble de composants et de fonctionnalités servant à accélérer le développement d’applications de réalité mixte interplateformes dans Unity.</span><span class="sxs-lookup"><span data-stu-id="b4794-106">MRTK-Unity is a Microsoft-driven project that provides a set of components and features, used to accelerate cross-platform MR app development in Unity.</span></span> <span data-ttu-id="b4794-107">Voici quelques-unes de ses fonctions :</span><span class="sxs-lookup"><span data-stu-id="b4794-107">Here are some of its functions:</span></span>

* <span data-ttu-id="b4794-108">Fournit **le système d’entrée multiplateforme et les composants pour les interactions spatiales et l’interface utilisateur**.</span><span class="sxs-lookup"><span data-stu-id="b4794-108">Provides the **cross-platform input system and building blocks for spatial interactions and UI**.</span></span>
* <span data-ttu-id="b4794-109">Active le **prototypage rapide** via la simulation dans l’éditeur qui vous permet de voir immédiatement les modifications.</span><span class="sxs-lookup"><span data-stu-id="b4794-109">Enables **rapid prototyping** via in-editor simulation that allows you to see changes immediately.</span></span>
* <span data-ttu-id="b4794-110">Fonctionne comme un **framework extensible** qui fournit aux développeurs la possibilité de permuter les composants de base.</span><span class="sxs-lookup"><span data-stu-id="b4794-110">Operates as an **extensible framework** that provides developers the ability to swap out core components.</span></span>
* <span data-ttu-id="b4794-111">**Prend en charge une large gamme de plateformes** dont</span><span class="sxs-lookup"><span data-stu-id="b4794-111">**Supports a wide range of platforms**, including</span></span>
  * <span data-ttu-id="b4794-112">OpenXR (Unity 2020.2 ou ultérieur)</span><span class="sxs-lookup"><span data-stu-id="b4794-112">OpenXR (Unity 2020.2 or newer)</span></span>
    * <span data-ttu-id="b4794-113">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="b4794-113">Microsoft HoloLens 2</span></span>
    * <span data-ttu-id="b4794-114">Casques Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b4794-114">Windows Mixed Reality headsets</span></span>
  * <span data-ttu-id="b4794-115">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b4794-115">Windows Mixed Reality</span></span>
    * <span data-ttu-id="b4794-116">Microsoft HoloLens</span><span class="sxs-lookup"><span data-stu-id="b4794-116">Microsoft HoloLens</span></span>
    * <span data-ttu-id="b4794-117">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="b4794-117">Microsoft HoloLens 2</span></span>
    * <span data-ttu-id="b4794-118">Casques Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b4794-118">Windows Mixed Reality headsets</span></span>
  * <span data-ttu-id="b4794-119">Oculus (Unity 2019.3 ou ultérieur)</span><span class="sxs-lookup"><span data-stu-id="b4794-119">Oculus (Unity 2019.3 or newer)</span></span>
    * <span data-ttu-id="b4794-120">Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="b4794-120">Oculus Quest</span></span>
  * <span data-ttu-id="b4794-121">OpenVR</span><span class="sxs-lookup"><span data-stu-id="b4794-121">OpenVR</span></span>
    * <span data-ttu-id="b4794-122">Casques Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="b4794-122">Windows Mixed Reality headsets</span></span>
    * <span data-ttu-id="b4794-123">HTC Vive</span><span class="sxs-lookup"><span data-stu-id="b4794-123">HTC Vive</span></span>
    * <span data-ttu-id="b4794-124">Oculus Rift</span><span class="sxs-lookup"><span data-stu-id="b4794-124">Oculus Rift</span></span>
  * <span data-ttu-id="b4794-125">Suivi de la main Ultraleap</span><span class="sxs-lookup"><span data-stu-id="b4794-125">Ultraleap Hand Tracking</span></span>
  * <span data-ttu-id="b4794-126">Appareils mobiles comme iOS et Android</span><span class="sxs-lookup"><span data-stu-id="b4794-126">Mobile devices such as iOS and Android</span></span>

## <a name="getting-started-with-mrtk"></a><span data-ttu-id="b4794-127">Bien démarrer avec MRTK</span><span class="sxs-lookup"><span data-stu-id="b4794-127">Getting started with MRTK</span></span>

<span data-ttu-id="b4794-128">Si vous débutez avec le développement MRTK ou Mixed Reality dans Unity, nous vous recommandons d’installer les outils nécessaires, puis de suivre la série de tutoriels HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b4794-128">If you're new to MRTK or Mixed Reality development in Unity, we recommend you install the necessary tools and then follow the HoloLens 2 tutorial series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b4794-129">Installer les outils</span><span class="sxs-lookup"><span data-stu-id="b4794-129">Install the Tools</span></span>](install-the-tools.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="b4794-130">Série de tutoriels HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="b4794-130">HoloLens 2 Tutorial Series</span></span>](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02)

<span data-ttu-id="b4794-131">Vous voulez voir ce qui se passe en coulisses ?</span><span class="sxs-lookup"><span data-stu-id="b4794-131">Want to see what's going on under the hood?</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="b4794-132">Explorez MRTK sur GitHub</span><span class="sxs-lookup"><span data-stu-id="b4794-132">Explore MRTK on GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)

## <a name="documentation"></a><span data-ttu-id="b4794-133">Documentation</span><span class="sxs-lookup"><span data-stu-id="b4794-133">Documentation</span></span>

| <span data-ttu-id="b4794-134">[![Notes de publication](features/images/MRTK_Icon_ReleaseNotes.png)](release-notes/mrtk-26-release-notes.md)</span><span class="sxs-lookup"><span data-stu-id="b4794-134">[![Release notes](features/images/MRTK_Icon_ReleaseNotes.png)](release-notes/mrtk-26-release-notes.md)</span></span><br/>[<span data-ttu-id="b4794-135">Notes de publication</span><span class="sxs-lookup"><span data-stu-id="b4794-135">Release Notes</span></span>](release-notes/mrtk-26-release-notes.md)| <span data-ttu-id="b4794-136">[![Présentation de MRTK](features/images/MRTK_Icon_ArchitectureOverview.png)](architecture/overview.md)</span><span class="sxs-lookup"><span data-stu-id="b4794-136">[![MRTK Overview](features/images/MRTK_Icon_ArchitectureOverview.png)](architecture/overview.md)</span></span><br/>[<span data-ttu-id="b4794-137">Présentation de MRTK</span><span class="sxs-lookup"><span data-stu-id="b4794-137">MRTK Overview</span></span>](architecture/overview.md)|<span data-ttu-id="b4794-138">[![Informations de référence sur les API](features/images/MRTK_Icon_APIReference.png)](/dotnet/api/Microsoft.MixedReality.Toolkit)</span><span class="sxs-lookup"><span data-stu-id="b4794-138">[![API Reference](features/images/MRTK_Icon_APIReference.png)](/dotnet/api/Microsoft.MixedReality.Toolkit)</span></span><br/>[<span data-ttu-id="b4794-139">Référence sur l’API</span><span class="sxs-lookup"><span data-stu-id="b4794-139">API Reference</span></span>](/dotnet/api/Microsoft.MixedReality.Toolkit)|
|:---|:---|:---|

## <a name="build-status"></a><span data-ttu-id="b4794-140">État de la build</span><span class="sxs-lookup"><span data-stu-id="b4794-140">Build status</span></span>

| <span data-ttu-id="b4794-141">Branche</span><span class="sxs-lookup"><span data-stu-id="b4794-141">Branch</span></span> | <span data-ttu-id="b4794-142">État CI</span><span class="sxs-lookup"><span data-stu-id="b4794-142">CI Status</span></span> | <span data-ttu-id="b4794-143">État de la documentation</span><span class="sxs-lookup"><span data-stu-id="b4794-143">Docs Status</span></span> |
|---|---|---|
| `mrtk_development` |<span data-ttu-id="b4794-144">[![État CI](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)</span><span class="sxs-lookup"><span data-stu-id="b4794-144">[![CI Status](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)</span></span>|<span data-ttu-id="b4794-145">[![État de la documentation](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)</span><span class="sxs-lookup"><span data-stu-id="b4794-145">[![Docs Status](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)</span></span>

## <a name="feature-areas"></a><span data-ttu-id="b4794-146">Zones de fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="b4794-146">Feature areas</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="b4794-147">[![Système d’entrée](features/images/MRTK_Icon_InputSystem.png)](features/input/overview.md)</span><span class="sxs-lookup"><span data-stu-id="b4794-147">[![Input System](features/images/MRTK_Icon_InputSystem.png)](features/input/overview.md)</span></span><br>
        <span data-ttu-id="b4794-148">**[Système d’entrée](features/input/overview.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-148">**[Input System](features/input/overview.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b4794-149">[![Suivi de la main (HoloLens 2)](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md)</span><span class="sxs-lookup"><span data-stu-id="b4794-149">[![Hand Tracking (HoloLens 2)](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md)</span></span><br>
        <span data-ttu-id="b4794-150">**[Suivi de la main <br> (HoloLens 2)](features/input/hand-tracking.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-150">**[Hand Tracking <br> (HoloLens 2)](features/input/hand-tracking.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b4794-151">[![Suivi du regard (HoloLens 2)](features/images/MRTK_Icon_EyeTracking.png)](features/input/eye-tracking/eye-tracking-Main.md)</span><span class="sxs-lookup"><span data-stu-id="b4794-151">[![Eye Tracking (HoloLens 2)](features/images/MRTK_Icon_EyeTracking.png)](features/input/eye-tracking/eye-tracking-Main.md)</span></span><br>
        <span data-ttu-id="b4794-152">**[Suivi du regard <br/> (HoloLens 2)](features/input/eye-tracking/eye-tracking-Main.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-152">**[Eye Tracking <br/> (HoloLens 2)](features/input/eye-tracking/eye-tracking-Main.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b4794-153">[![Profils](features/images/MRTK_Icon_Profiles.png)](configuration/mixed-reality-configuration-guide.md)</span><span class="sxs-lookup"><span data-stu-id="b4794-153">[![Profiles](features/images/MRTK_Icon_Profiles.png)](configuration/mixed-reality-configuration-guide.md)</span></span><br>
        <span data-ttu-id="b4794-154">**[Profils](configuration/mixed-reality-configuration-guide.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-154">**[Profiles](configuration/mixed-reality-configuration-guide.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="b4794-155">[![Suivi de la main (Ultraleap)](features/images/MRTK_Icon_HandTracking.png)](features/cross-platform/leap-motion-mrtk.md)</span><span class="sxs-lookup"><span data-stu-id="b4794-155">[![Hand Tracking (Ultraleap)](features/images/MRTK_Icon_HandTracking.png)](features/cross-platform/leap-motion-mrtk.md)</span></span><br>
        <span data-ttu-id="b4794-156">**[Suivi de la main <br/> (Ultraleap)](features/cross-platform/leap-motion-mrtk.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-156">**[Hand Tracking <br/> (Ultraleap)](features/cross-platform/leap-motion-mrtk.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b4794-157">[![Contrôles d’interface utilisateur](features/images/MRTK_Icon_UIControls.png)](#ux-building-blocks)</span><span class="sxs-lookup"><span data-stu-id="b4794-157">[![UI Controls](features/images/MRTK_Icon_UIControls.png)](#ux-building-blocks)</span></span><br>
        <span data-ttu-id="b4794-158">**[Contrôles d’interface utilisateur](#ux-building-blocks)**</span><span class="sxs-lookup"><span data-stu-id="b4794-158">**[UI Controls](#ux-building-blocks)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b4794-159">[![Solveurs](features/images/MRTK_Icon_Solver.png)](features/ux-building-blocks/solvers/solver.md)</span><span class="sxs-lookup"><span data-stu-id="b4794-159">[![Solvers](features/images/MRTK_Icon_Solver.png)](features/ux-building-blocks/solvers/solver.md)</span></span><br>
        <span data-ttu-id="b4794-160">**[Solveurs](features/ux-building-blocks/solvers/solver.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-160">**[Solvers](features/ux-building-blocks/solvers/solver.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b4794-161">[![Gestionnaire multiscène](features/images/MRTK_Icon_SceneSystem.png)](features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="b4794-161">[![Multi-Scene Manager](features/images/MRTK_Icon_SceneSystem.png)](features/scene-system/scene-system-getting-started.md)</span></span><br>
        <span data-ttu-id="b4794-162">**[Gestionnaire<br/> multiscène](features/scene-system/scene-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-162">**[Multi-Scene<br/> Manager](features/scene-system/scene-system-getting-started.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="b4794-163">[![Reconnaissance spatiale](features/images/MRTK_Icon_SpatialUnderstanding.png)](features/spatial-awareness/spatial-awareness-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="b4794-163">[![Spatial Awareness](features/images/MRTK_Icon_SpatialUnderstanding.png)](features/spatial-awareness/spatial-awareness-getting-started.md)</span></span><br>
        <span data-ttu-id="b4794-164">**[Reconnaissance <br/> spatiale](features/spatial-awareness/spatial-awareness-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-164">**[Spatial <br/> Awareness](features/spatial-awareness/spatial-awareness-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b4794-165">[![Outil de diagnostic](features/images/MRTK_Icon_Diagnostics.png)](features/diagnostics/diagnostics-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="b4794-165">[![Diagnostic Tool](features/images/MRTK_Icon_Diagnostics.png)](features/diagnostics/diagnostics-system-getting-started.md)</span></span><br>
        <span data-ttu-id="b4794-166">**[Outil de <br/> diagnostic](features/diagnostics/diagnostics-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-166">**[Diagnostic <br/> Tool](features/diagnostics/diagnostics-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b4794-167">[![Nuanceur standard MRTK](features/images/MRTK_Icon_StandardShader.png)](features/rendering/mrtk-standard-shader.md?q=shader)</span><span class="sxs-lookup"><span data-stu-id="b4794-167">[![MRTK Standard Shader View](features/images/MRTK_Icon_StandardShader.png)](features/rendering/mrtk-standard-shader.md?q=shader)</span></span><br>
        <span data-ttu-id="b4794-168">**[Exemple de vue du nuanceur standard MRTK](features/rendering/mrtk-standard-shader.md?q=shader)**</span><span class="sxs-lookup"><span data-stu-id="b4794-168">**[MRTK Standard Shader Example View](features/rendering/mrtk-standard-shader.md?q=shader)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b4794-169">[![Voix & dictée](features/images/MRTK_Icon_VoiceCommand.png)](features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="b4794-169">[![Speech & Dictation](features/images/MRTK_Icon_VoiceCommand.png)](features/scene-system/scene-system-getting-started.md)</span></span><br>
        <span data-ttu-id="b4794-170">**[Voix](features/input/speech.md)<br/> & [dictée](features/input/dictation.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-170">**[Speech](features/input/speech.md)<br/> & [Dictation](features/input/dictation.md)**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="b4794-171">[![Système de limites](features/images/MRTK_Icon_Boundary.png)](features/boundary/boundary-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="b4794-171">[![Boundary System](features/images/MRTK_Icon_Boundary.png)](features/boundary/boundary-system-getting-started.md)</span></span><br>
        <span data-ttu-id="b4794-172">**[Système de <br/>limites](features/boundary/boundary-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-172">**[Boundary <br/>System](features/boundary/boundary-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b4794-173">[![Simulation dans l’éditeur](features/images/MRTK_Icon_InputSystem.png)](features/diagnostics/diagnostics-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="b4794-173">[![In-Editor Simulation](features/images/MRTK_Icon_InputSystem.png)](features/diagnostics/diagnostics-system-getting-started.md)</span></span><br>
        <span data-ttu-id="b4794-174">**[Simulation <br/> dans l’éditeur](features/diagnostics/diagnostics-system-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-174">**[In-Editor <br/> Simulation](features/diagnostics/diagnostics-system-getting-started.md)**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b4794-175">[![Fonctionnalités expérimentales](features/images/MRTK_Icon_Experimental.png)](contributing/experimental-features.md)</span><span class="sxs-lookup"><span data-stu-id="b4794-175">[![Experimental Features](features/images/MRTK_Icon_Experimental.png)](contributing/experimental-features.md)</span></span><br>
        <span data-ttu-id="b4794-176">**[Fonctionnalités <br/> expérimentales](contributing/experimental-features.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-176">**[Experimental <br/> Features](contributing/experimental-features.md)**</span></span><br>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

## <a name="ux-building-blocks"></a><span data-ttu-id="b4794-177">Composants de l’interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="b4794-177">UX building blocks</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="b4794-178">[![Bouton](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) **[Bouton](features/ux-building-blocks/button.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-178">[![Button](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) **[Button](features/ux-building-blocks/button.md)**</span></span><br>
        <span data-ttu-id="b4794-179">Contrôle bouton qui prend en charge différentes méthodes d’entrée, y compris la main articulée d’HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="b4794-179">A button control which supports various input methods, including HoloLens 2's articulated hand</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b4794-180">[![Contrôle des limites](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) **[Contrôle des limites](features/ux-building-blocks/bounds-control.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-180">[![Bounds Control](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) **[Bounds Control](features/ux-building-blocks/bounds-control.md)**</span></span><br>
        <span data-ttu-id="b4794-181">Interface utilisateur standard pour manipuler des objets dans l’espace 3D</span><span class="sxs-lookup"><span data-stu-id="b4794-181">Standard UI for manipulating objects in 3D space</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b4794-182">[![Manipulateur d’objets](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md) **[Manipulateur d’objets](features/ux-building-blocks/object-manipulator.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-182">[![Object Manipulator](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md) **[Object Manipulator](features/ux-building-blocks/object-manipulator.md)**</span></span><br>
        <span data-ttu-id="b4794-183">Script pour manipuler des objets avec une ou deux mains</span><span class="sxs-lookup"><span data-stu-id="b4794-183">Script for manipulating objects with one or two hands</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="b4794-184">[![Tablette](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) **[Tablette](features/ux-building-blocks/slate.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-184">[![Slate](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) **[Slate](features/ux-building-blocks/slate.md)**</span></span><br>
        <span data-ttu-id="b4794-185">Plan de style 2D qui prend en charge le défilement avec des entrées par la main articulée</span><span class="sxs-lookup"><span data-stu-id="b4794-185">2D style plane which supports scrolling with articulated hand input</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b4794-186">[![Clavier système](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) **[Clavier système](features/ux-building-blocks/system-keyboard.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-186">[![System Keyboard](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) **[System Keyboard](features/ux-building-blocks/system-keyboard.md)**</span></span><br>
        <span data-ttu-id="b4794-187">Exemple de script d’utilisation du clavier système dans Unity</span><span class="sxs-lookup"><span data-stu-id="b4794-187">Example script of using the system keyboard in Unity</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b4794-188">[![Interaction](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) **[Interaction](features/ux-building-blocks/interactable.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-188">[![Interactable](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) **[Interactable](features/ux-building-blocks/interactable.md)**</span></span><br>
        <span data-ttu-id="b4794-189">Script pour rendre les objets interactifs avec les états visuels et la prise en charge des thèmes</span><span class="sxs-lookup"><span data-stu-id="b4794-189">A script for making objects interactable with visual states and theme support</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="b4794-190">[![Solveur](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md) **[Solveur](features/ux-building-blocks/solvers/solver.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-190">[![Solver](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md) **[Solver](features/ux-building-blocks/solvers/solver.md)**</span></span><br>
        <span data-ttu-id="b4794-191">Différents comportements de positionnement des objets, comme les menus qui restent à proximité (tag-along), le rattachement au corps (body-lock), la taille de vue constante et l’aimantation de surface</span><span class="sxs-lookup"><span data-stu-id="b4794-191">Various object positioning behaviors such as tag-along, body-lock, constant view size and surface magnetism</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b4794-192">[![Collection d’objets](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) **[Collection d’objets](features/ux-building-blocks/object-collection.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-192">[![Object Collection](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) **[Object Collection](features/ux-building-blocks/object-collection.md)**</span></span><br>
        <span data-ttu-id="b4794-193">Script pour disposer un tableau d’objets dans une forme en trois dimensions</span><span class="sxs-lookup"><span data-stu-id="b4794-193">Script for laying out an array of objects in a three-dimensional shape</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b4794-194">[![Info-bulle](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md) **[Info-bulle](features/ux-building-blocks/tooltip.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-194">[![Tooltip](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md) **[Tooltip](features/ux-building-blocks/tooltip.md)**</span></span><br>
        <span data-ttu-id="b4794-195">Interface utilisateur Annotation avec un système d’ancrage/de pivot flexible, qui peut être utilisé pour étiqueter les contrôleurs de mouvement et les objets</span><span class="sxs-lookup"><span data-stu-id="b4794-195">Annotation UI with a flexible anchor/pivot system, which can be used for labeling motion controllers and objects</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="b4794-196">[![Curseur](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) **[Curseur](features/ux-building-blocks/sliders.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-196">[![Slider](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) **[Slider](features/ux-building-blocks/sliders.md)**</span></span><br>
        <span data-ttu-id="b4794-197">Interface utilisateur Curseur pour ajuster des valeurs prenant en charge l’interaction de suivi de la main direct</span><span class="sxs-lookup"><span data-stu-id="b4794-197">Slider UI for adjusting values supporting direct hand tracking interaction</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b4794-198">[![Nuanceur standard du MRTK](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) **[Nuanceur standard du MRTK](features/rendering/mrtk-standard-shader.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-198">[![MRTK Standard Shader](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) **[MRTK Standard Shader](features/rendering/mrtk-standard-shader.md)**</span></span><br>
        <span data-ttu-id="b4794-199">Le nuanceur standard du MRTK prend en charge différents éléments Fluent Design performants</span><span class="sxs-lookup"><span data-stu-id="b4794-199">MRTK's Standard shader supports various Fluent design elements with performance</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b4794-200">[![Menu de la main](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) **[Menu de la main](features/ux-building-blocks/hand-menu.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-200">[![Hand Menu](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) **[Hand Menu](features/ux-building-blocks/hand-menu.md)**</span></span><br>
        <span data-ttu-id="b4794-201">Interface utilisateur rattachée à la main pour un accès rapide, à l’aide du solveur de contraintes de la main</span><span class="sxs-lookup"><span data-stu-id="b4794-201">Hand-locked UI for quick access, using the Hand Constraint Solver</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="b4794-202">[![Barre d’application](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) **[Barre d’application](features/ux-building-blocks/app-bar.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-202">[![App Bar](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) **[App Bar](features/ux-building-blocks/app-bar.md)**</span></span><br>
        <span data-ttu-id="b4794-203">Interface utilisateur pour l’activation manuelle du contrôle des limites</span><span class="sxs-lookup"><span data-stu-id="b4794-203">UI for Bounds Control's manual activation</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b4794-204">[![Pointeurs](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[Pointeurs](features/input/pointers.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-204">[![Pointers](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[Pointers](features/input/pointers.md)**</span></span><br>
        <span data-ttu-id="b4794-205">Découvrez les différents types de pointeurs</span><span class="sxs-lookup"><span data-stu-id="b4794-205">Learn about various types of pointers</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b4794-206">[![Visualisation du bout des doigts](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) **[Visualisation du bout des doigts](features/ux-building-blocks/fingertip-visualization.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-206">[![Fingertip Visualization](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) **[Fingertip Visualization](features/ux-building-blocks/fingertip-visualization.md)**</span></span><br>
        <span data-ttu-id="b4794-207">Affordance visuelle du bout des doigts, qui améliore la confiance dans l’interaction directe</span><span class="sxs-lookup"><span data-stu-id="b4794-207">Visual affordance on the fingertip which improves the confidence for the direct interaction</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="b4794-208">[![Menu proche](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) **[Menu proche](features/ux-building-blocks/near-menu.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-208">[![Near Menu](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) **[Near Menu](features/ux-building-blocks/near-menu.md)**</span></span><br>
        <span data-ttu-id="b4794-209">Interface utilisateur du menu flottant pour les interactions proches</span><span class="sxs-lookup"><span data-stu-id="b4794-209">Floating menu UI for the near interactions</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b4794-210">[![Bien démarrer avec la reconnaissance spatiale](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[Vue de la reconnaissance spatiale](features/spatial-awareness/spatial-awareness-getting-started.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-210">[![Spatial Awareness Getting started](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[Spatial Awareness View](features/spatial-awareness/spatial-awareness-getting-started.md)**</span></span><br>
        <span data-ttu-id="b4794-211">Faire interagir vos objets holographiques avec les environnements physiques</span><span class="sxs-lookup"><span data-stu-id="b4794-211">Make your holographic objects interact with the physical environments</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b4794-212">[![Commande vocale](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) **[Commande vocale](features/input/speech.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-212">[![Voice Command](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) **[Voice Command](features/input/speech.md)**</span></span><br>
        <span data-ttu-id="b4794-213">Scripts et exemples pour intégrer des entrées vocales</span><span class="sxs-lookup"><span data-stu-id="b4794-213">Scripts and examples for integrating speech input</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="b4794-214">[![Indicateur de progression](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) **[Indicateur de progression](features/ux-building-blocks/progress-indicator.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-214">[![Progress Indicator](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) **[Progress Indicator](features/ux-building-blocks/progress-indicator.md)**</span></span><br>
        <span data-ttu-id="b4794-215">Indicateur visuel qui renseigne sur un processus ou une opération de données</span><span class="sxs-lookup"><span data-stu-id="b4794-215">Visual indicator for communicating data process or operation</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b4794-216">[![Boîte de dialogue](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) **[Boîte de dialogue](features/ux-building-blocks/dialog.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-216">[![Dialog](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) **[Dialog](features/ux-building-blocks/dialog.md)**</span></span><br>
        <span data-ttu-id="b4794-217">Interface utilisateur pour demander à l’utilisateur une confirmation ou son accord</span><span class="sxs-lookup"><span data-stu-id="b4794-217">UI for asking for user's confirmation or acknowledgement</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b4794-218">[![Coach de main](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) **[Coach de main](features/ux-building-blocks/hand-coach.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-218">[![Hand Coach](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) **[Hand Coach](features/ux-building-blocks/hand-coach.md)**</span></span><br>
        <span data-ttu-id="b4794-219">Composant qui guide l’utilisateur quand le mouvement n’a pas été appris</span><span class="sxs-lookup"><span data-stu-id="b4794-219">Component that helps guide the user when the gesture has not been taught</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="b4794-220">[![Service de la physique des mains](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/experimental/hand-physics-service.md) **[Service de la physique des mains [expérimental]](features/experimental/hand-physics-service.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-220">[![Hand Physics Service](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/experimental/hand-physics-service.md) **[Hand Physics Service [Experimental]](features/experimental/hand-physics-service.md)**</span></span><br>
        <span data-ttu-id="b4794-221">Le service de la physique des mains rend possible les événements et interactions de collision de corps rigides avec les mains articulées</span><span class="sxs-lookup"><span data-stu-id="b4794-221">The hand physics service enables rigid body collision events and interactions with articulated hands</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b4794-222">[![Défilement de la collection](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) **[Défilement de la collection](features/ux-building-blocks/scrolling-object-collection.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-222">[![Scrolling Collection](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) **[Scrolling Collection](features/ux-building-blocks/scrolling-object-collection.md)**</span></span><br>
        <span data-ttu-id="b4794-223">Collection d’objets qui défile en mode natif pour exposer les objets 3D</span><span class="sxs-lookup"><span data-stu-id="b4794-223">An Object Collection that natively scrolls 3D objects</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b4794-224">[![Ancrage](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md) **[Ancrage [expérimental]](features/experimental/dock.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-224">[![Dock](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md) **[Dock [Experimental]](features/experimental/dock.md)**</span></span><br>
        <span data-ttu-id="b4794-225">L’ancrage permet de placer des objets dans ou en dehors de positions prédéterminées</span><span class="sxs-lookup"><span data-stu-id="b4794-225">The Dock allows objects to be moved in and out of predetermined positions</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="b4794-226">[![Suivi oculaire : Sélection de la cible](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) **[Suivi oculaire : Sélection de la cible](features/input/eye-tracking/eye-tracking-target-selection.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-226">[![Eye Tracking: Target Selection](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) **[Eye Tracking: Target Selection](features/input/eye-tracking/eye-tracking-target-selection.md)**</span></span><br>
        <span data-ttu-id="b4794-227">Combinez les entrées oculaires, vocales et manuelles pour sélectionner rapidement et facilement des hologrammes sur votre scène</span><span class="sxs-lookup"><span data-stu-id="b4794-227">Combine eyes, voice and hand input to quickly and effortlessly select holograms across your scene</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b4794-228">[![Suivi oculaire : Navigation](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) **[Suivi oculaire : Navigation](features/input/eye-tracking/eye-tracking-navigation.md)**</span><span class="sxs-lookup"><span data-stu-id="b4794-228">[![Eye Tracking: Navigation](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) **[Eye Tracking: Navigation](features/input/eye-tracking/eye-tracking-navigation.md)**</span></span><br>
        <span data-ttu-id="b4794-229">Apprenez à faire défiler le texte automatiquement ou à faire facilement un zoom sur le contenu ciblé en fonction de ce que vous regardez</span><span class="sxs-lookup"><span data-stu-id="b4794-229">Learn how to auto-scroll text or fluently zoom into focused content based on what you are looking at</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b4794-230">[![Suivi oculaire : Carte thermique](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) **[Suivi oculaire : Carte thermique](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)**</span><span class="sxs-lookup"><span data-stu-id="b4794-230">[![Eye Tracking: Heat Map](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) **[Eye Tracking: Heat Map](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)**</span></span><br>
        <span data-ttu-id="b4794-231">Exemples de journalisation, de chargement et de visualisation de ce que les utilisateurs ont regardé dans votre application</span><span class="sxs-lookup"><span data-stu-id="b4794-231">Examples for logging, loading and visualizing what users have been looking at in your app</span></span>
    :::column-end:::
:::row-end:::

## <a name="tools"></a><span data-ttu-id="b4794-232">Outils</span><span class="sxs-lookup"><span data-stu-id="b4794-232">Tools</span></span>

|  <span data-ttu-id="b4794-233">[![Fenêtre d’optimisation](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md) [Fenêtre d’optimisation](features/tools/optimize-window.md)</span><span class="sxs-lookup"><span data-stu-id="b4794-233">[![Optimize Window](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md) [Optimize Window](features/tools/optimize-window.md)</span></span> | <span data-ttu-id="b4794-234">[![Fenêtre de dépendance](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md) [Fenêtre de dépendance](features/tools/dependency-window.md)</span><span class="sxs-lookup"><span data-stu-id="b4794-234">[![Dependency Window](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md) [Dependency Window](features/tools/dependency-window.md)</span></span> | ![Fenêtre de build](features/images/MRTK_Icon_BuildWindow.png) <span data-ttu-id="b4794-236">Fenêtre de build</span><span class="sxs-lookup"><span data-stu-id="b4794-236">Build Window</span></span> | <span data-ttu-id="b4794-237">[![Enregistrement des entrées](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md) [Enregistrement des entrées](features/input-simulation/input-animation-recording.md)</span><span class="sxs-lookup"><span data-stu-id="b4794-237">[![Input recording](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md) [Input recording](features/input-simulation/input-animation-recording.md)</span></span> |
|:--- | :--- | :--- | :--- |
| <span data-ttu-id="b4794-238">Automatiser la configuration des projets de réalité mixte pour les optimisations de performances</span><span class="sxs-lookup"><span data-stu-id="b4794-238">Automate configuration of Mixed Reality projects for performance optimizations</span></span> | <span data-ttu-id="b4794-239">Analyser les dépendances entre les ressources et identifier les ressources inutilisées</span><span class="sxs-lookup"><span data-stu-id="b4794-239">Analyze dependencies between assets and identify unused assets</span></span> |  <span data-ttu-id="b4794-240">Configurer et exécuter un processus de build de bout en bout pour les applications de réalité mixte</span><span class="sxs-lookup"><span data-stu-id="b4794-240">Configure and execute an end-to-end build process for Mixed Reality applications</span></span> | <span data-ttu-id="b4794-241">Enregistrer et lire les données de suivi de la main et des mouvements de tête dans l’éditeur</span><span class="sxs-lookup"><span data-stu-id="b4794-241">Record and playback head movement and hand tracking data in editor</span></span> |

## <a name="example-scenes"></a><span data-ttu-id="b4794-242">Exemples de scènes</span><span class="sxs-lookup"><span data-stu-id="b4794-242">Example scenes</span></span>

<span data-ttu-id="b4794-243">Explorez les différents types d’interactions et de contrôles d’interface utilisateur du MRTK dans [cet exemple de scène](features/example-scenes/hand-interaction-examples.md).</span><span class="sxs-lookup"><span data-stu-id="b4794-243">Explore MRTK's various types of interactions and UI controls in [this example scene](features/example-scenes/hand-interaction-examples.md).</span></span>

<span data-ttu-id="b4794-244">[![Exemple de scène 2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)</span><span class="sxs-lookup"><span data-stu-id="b4794-244">[![Example Scene 2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)</span></span>

## <a name="mrtk-examples-hub"></a><span data-ttu-id="b4794-245">Hub d’exemples MRTK</span><span class="sxs-lookup"><span data-stu-id="b4794-245">MRTK examples hub</span></span>

<span data-ttu-id="b4794-246">Avec le hub d’exemples MRTK, vous pouvez essayer divers exemples de scènes dans MRTK.</span><span class="sxs-lookup"><span data-stu-id="b4794-246">With the MRTK Examples Hub, you can try various example scenes in MRTK.</span></span>
<span data-ttu-id="b4794-247">Vous pouvez télécharger des packages d’applications prédéfinis pour HoloLens (x86), HoloLens 2 (ARM) et les casques immersifs Windows Mixed Reality (x64) en sélectionnant le package « Exemples du Mixed Reality Toolkit » dans [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool).</span><span class="sxs-lookup"><span data-stu-id="b4794-247">You can download pre-built app packages for HoloLens(x86), HoloLens 2(ARM), and Windows Mixed Reality immersive headsets(x64) by selecting the "Mixed Reality Toolkit Examples" package in the [MR Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool).</span></span> <span data-ttu-id="b4794-248">Veillez à [utiliser le portail d’appareil Windows pour installer des applications sur HoloLens (1ère génération)](/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens).</span><span class="sxs-lookup"><span data-stu-id="b4794-248">Make sure to [use the Windows Device Portal to install apps on HoloLens (1st gen)](/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens).</span></span> <span data-ttu-id="b4794-249">Sur HoloLens 2, vous pouvez télécharger et installer le [Hub d’exemples MRTK à partir de l’application Microsoft Store](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4).</span><span class="sxs-lookup"><span data-stu-id="b4794-249">On HoloLens 2, you can download and install [MRTK Examples Hub through the Microsoft Store app](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4).</span></span>

<span data-ttu-id="b4794-250">Consultez la [page README du hub d’exemples](features/example-scenes/example-hub.md) pour en savoir plus sur la création d’un hub multiscène avec le système de scène et le service de transition de scène de MRTK.</span><span class="sxs-lookup"><span data-stu-id="b4794-250">See [Examples Hub README page](features/example-scenes/example-hub.md) to learn about the details on creating a multi-scene hub with MRTK's scene system and scene transition service.</span></span>

<span data-ttu-id="b4794-251">[![Hub d’exemples de scènes](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)</span><span class="sxs-lookup"><span data-stu-id="b4794-251">[![Example Scene Hub](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)</span></span>

## <a name="sample-apps-made-with-mrtk"></a><span data-ttu-id="b4794-252">Exemples d’applications créées avec MRTK</span><span class="sxs-lookup"><span data-stu-id="b4794-252">Sample apps made with MRTK</span></span>

| <span data-ttu-id="b4794-253">[![Tableau périodique des éléments](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span><span class="sxs-lookup"><span data-stu-id="b4794-253">[![Periodic Table of the Elements](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span></span>| <span data-ttu-id="b4794-254">[![Galaxy Explorer](features/images/MRTK_GalaxyExplorer.jpg)](/windows/mixed-reality/galaxy-explorer-update)</span><span class="sxs-lookup"><span data-stu-id="b4794-254">[![Galaxy Explorer](features/images/MRTK_GalaxyExplorer.jpg)](/windows/mixed-reality/galaxy-explorer-update)</span></span>| <span data-ttu-id="b4794-255">[![Exemple d’application Surfaces](features/images/MRDL_Surfaces.jpg)](/windows/mixed-reality/sampleapp-surfaces)</span><span class="sxs-lookup"><span data-stu-id="b4794-255">[![Surfaces sample app](features/images/MRDL_Surfaces.jpg)](/windows/mixed-reality/sampleapp-surfaces)</span></span>|
|:--- | :--- | :--- |
| <span data-ttu-id="b4794-256">[Tableau périodique des éléments](https://github.com/Microsoft/MRDL_Unity_PeriodicTable) est un exemple d’application open source qui montre comment utiliser le système d’entrée et les composants du MRTK afin de créer une expérience d’application pour les casques immersifs et HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b4794-256">[Periodic Table of the Elements](https://github.com/Microsoft/MRDL_Unity_PeriodicTable) is an open-source sample app which demonstrates how to use MRTK's input system and building blocks to create an app experience for HoloLens and Immersive headsets.</span></span> <span data-ttu-id="b4794-257">Lisez le récit sur le portage qui raconte comment [importer l’application Tableau périodique des éléments vers HoloLens 2 avec MRTK v2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span><span class="sxs-lookup"><span data-stu-id="b4794-257">Read the porting story: [Bringing the Periodic Table of the Elements app to HoloLens 2 with MRTK v2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)</span></span> |<span data-ttu-id="b4794-258">[Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer) est un exemple d’application open source qui a été initialement développé en mars 2016 dans le cadre de la campagne HoloLens « Partagez vos idées ».</span><span class="sxs-lookup"><span data-stu-id="b4794-258">[Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer) is an open-source sample app that was originally developed in March 2016 as part of the HoloLens 'Share Your Idea' campaign.</span></span> <span data-ttu-id="b4794-259">L’application Galaxy Explorer a été mise à jour avec de nouvelles fonctionnalités pour HoloLens 2, avec MRTK v2.</span><span class="sxs-lookup"><span data-stu-id="b4794-259">Galaxy Explorer has been updated with new features for HoloLens 2, using MRTK v2.</span></span> <span data-ttu-id="b4794-260">Lisez le récit sur la [conception de Galaxy Explorer pour HoloLens 2](/windows/mixed-reality/galaxy-explorer-update)</span><span class="sxs-lookup"><span data-stu-id="b4794-260">Read the story: [The Making of Galaxy Explorer for HoloLens 2](/windows/mixed-reality/galaxy-explorer-update)</span></span> |<span data-ttu-id="b4794-261">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces) est un exemple d’application open source pour HoloLens 2, qui explore la manière dont nous pouvons créer une sensation tactile en utilisant le suivi oculaire, audio et avec la main entièrement articulée.</span><span class="sxs-lookup"><span data-stu-id="b4794-261">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces) is an open-source sample app for HoloLens 2 which explores how we can create a tactile sensation with visual, audio, and fully articulated hand-tracking.</span></span> <span data-ttu-id="b4794-262">Regardez la session Microsoft MR Dev Days [Enseignements tirés de l’application Surfaces](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App) pour lire le récit détaillé de la conception et du développement.</span><span class="sxs-lookup"><span data-stu-id="b4794-262">Check out Microsoft MR Dev Days session [Learnings from the Surfaces app](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App) for the detailed design and development story.</span></span> |

## <a name="session-videos-from-mixed-reality-dev-days-2020"></a><span data-ttu-id="b4794-263">Vidéos de la session Mixed Reality Dev Days 2020</span><span class="sxs-lookup"><span data-stu-id="b4794-263">Session videos from Mixed Reality Dev Days 2020</span></span>

| <span data-ttu-id="b4794-264">[![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)</span><span class="sxs-lookup"><span data-stu-id="b4794-264">[![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)</span></span>| <span data-ttu-id="b4794-265">[![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)</span><span class="sxs-lookup"><span data-stu-id="b4794-265">[![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)</span></span>| <span data-ttu-id="b4794-266">[![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)</span><span class="sxs-lookup"><span data-stu-id="b4794-266">[![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)</span></span>|
|:--- | :--- | :--- |
| <span data-ttu-id="b4794-267">Tutoriel sur la création d’une application MRTK simple, du début à la fin.</span><span class="sxs-lookup"><span data-stu-id="b4794-267">Tutorial on how to create a simple MRTK app from start to finish.</span></span> <span data-ttu-id="b4794-268">Découvrez les concepts de l’interaction et les fonctionnalités multiplateformes de MRTK.</span><span class="sxs-lookup"><span data-stu-id="b4794-268">Learn about interaction concepts and MRTK’s multi-platform capabilities.</span></span> | <span data-ttu-id="b4794-269">Présentation approfondie des composants UX de MRTK qui vous aident à créer de belles expériences de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="b4794-269">Deep dive on the MRTK’s UX building blocks that help you build beautiful mixed reality experiences.</span></span> | <span data-ttu-id="b4794-270">Présentation des outils de performances, intégrés à MRTK ou externes, et vue d’ensemble du nuanceur standard de MRTK.</span><span class="sxs-lookup"><span data-stu-id="b4794-270">An introduction to performance tools, both in MRTK and external, as well as an overview of the MRTK Standard Shader.</span></span> |

<span data-ttu-id="b4794-271">Consultez [Mixed Reality Dev Days](/windows/mixed-reality/mr-dev-days-sessions) pour explorer d’autres vidéos de session.</span><span class="sxs-lookup"><span data-stu-id="b4794-271">See [Mixed Reality Dev Days](/windows/mixed-reality/mr-dev-days-sessions) to explore more session videos.</span></span>

## <a name="engage-with-the-community"></a><span data-ttu-id="b4794-272">Impliquez-vous dans la communauté</span><span class="sxs-lookup"><span data-stu-id="b4794-272">Engage with the community</span></span>

* <span data-ttu-id="b4794-273">Participez aux conversations autour de MRTK sur [Slack](https://holodevelopers.slack.com/).</span><span class="sxs-lookup"><span data-stu-id="b4794-273">Join the conversation around MRTK on [Slack](https://holodevelopers.slack.com/).</span></span> <span data-ttu-id="b4794-274">Vous pouvez rejoindre la communauté Slack par le biais de l’[envoi d’invitation automatique](https://holodevelopersslack.azurewebsites.net/).</span><span class="sxs-lookup"><span data-stu-id="b4794-274">You can join the Slack community via the [automatic invitation sender](https://holodevelopersslack.azurewebsites.net/).</span></span>

* <span data-ttu-id="b4794-275">Posez vos questions au sujet de l’utilisation de MRTK sur le site [Stack Overflow](https://stackoverflow.com/questions/tagged/mrtk) en choisissant l’étiquette **MRTK**.</span><span class="sxs-lookup"><span data-stu-id="b4794-275">Ask questions about using MRTK on [Stack Overflow](https://stackoverflow.com/questions/tagged/mrtk) using the **MRTK** tag.</span></span>

* <span data-ttu-id="b4794-276">Faites une recherche sur les [problèmes connus](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) ou signalez un [nouveau problème](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) si vous détectez quelque chose qui ne va pas dans le code MRTK.</span><span class="sxs-lookup"><span data-stu-id="b4794-276">Search for [known issues](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) or file a [new issue](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) if you find something broken in MRTK code.</span></span>

* <span data-ttu-id="b4794-277">Pour toute question sur la contribution à MRTK, accédez au canal [mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) sur Slack.</span><span class="sxs-lookup"><span data-stu-id="b4794-277">For questions about contributing to MRTK, go to the [mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) channel on slack.</span></span>

<span data-ttu-id="b4794-278">Ce projet a adopté le [Code de conduite Open Source de Microsoft](https://opensource.microsoft.com/codeofconduct/).</span><span class="sxs-lookup"><span data-stu-id="b4794-278">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span>
<span data-ttu-id="b4794-279">Pour plus d'informations, voir la [FAQ sur le Code de conduite ](https://opensource.microsoft.com/codeofconduct/faq/) ou contacter [opencode@microsoft.com](mailto:opencode@microsoft.com) pour toute question ou commentaire supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="b4794-279">For more information, see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>

## <a name="useful-resources-on-the-mixed-reality-dev-center"></a><span data-ttu-id="b4794-280">Ressources utiles dans le Centre de développement Réalité mixte</span><span class="sxs-lookup"><span data-stu-id="b4794-280">Useful resources on the Mixed Reality Dev Center</span></span>

| <span data-ttu-id="b4794-281">![Découvrir](features/images/mrdevcenter/icon-discover.png) [Découvrir](/windows/mixed-reality/)</span><span class="sxs-lookup"><span data-stu-id="b4794-281">![Discover](features/images/mrdevcenter/icon-discover.png) [Discover](/windows/mixed-reality/)</span></span>| <span data-ttu-id="b4794-282">![Concevoir](features/images/mrdevcenter/icon-design.png) [Concevoir](/windows/mixed-reality/design)</span><span class="sxs-lookup"><span data-stu-id="b4794-282">![Design](features/images/mrdevcenter/icon-design.png) [Design](/windows/mixed-reality/design)</span></span>| <span data-ttu-id="b4794-283">![Développer](features/images/mrdevcenter/icon-develop.png) [Développer](/windows/mixed-reality/development)</span><span class="sxs-lookup"><span data-stu-id="b4794-283">![Develop](features/images/mrdevcenter/icon-develop.png) [Develop](/windows/mixed-reality/development)</span></span>| <span data-ttu-id="b4794-284">![Distribuer](features/images/mrdevcenter/icon-distribute.png) [Distribuer](/windows/mixed-reality/implementing-3d-app-launchers)</span><span class="sxs-lookup"><span data-stu-id="b4794-284">![Distribute)](features/images/mrdevcenter/icon-distribute.png) [Distribute](/windows/mixed-reality/implementing-3d-app-launchers)</span></span>|
| :--------------------- | :----------------- | :------------------ | :------------------------ |
| <span data-ttu-id="b4794-285">Découvrez comment créer des expériences de réalité mixte pour HoloLens et les casques immersifs (VR).</span><span class="sxs-lookup"><span data-stu-id="b4794-285">Learn to build mixed reality experiences for HoloLens and immersive headsets (VR).</span></span>          | <span data-ttu-id="b4794-286">Procurez-vous les guides de conception.</span><span class="sxs-lookup"><span data-stu-id="b4794-286">Get design guides.</span></span> <span data-ttu-id="b4794-287">Créez une interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b4794-287">Build user interface.</span></span> <span data-ttu-id="b4794-288">Découvrez les interactions et les entrées.</span><span class="sxs-lookup"><span data-stu-id="b4794-288">Learn interactions and input.</span></span>     | <span data-ttu-id="b4794-289">Procurez-vous les guides de développement.</span><span class="sxs-lookup"><span data-stu-id="b4794-289">Get development guides.</span></span> <span data-ttu-id="b4794-290">Découvrez la technologie.</span><span class="sxs-lookup"><span data-stu-id="b4794-290">Learn the technology.</span></span> <span data-ttu-id="b4794-291">Comprenez la science.</span><span class="sxs-lookup"><span data-stu-id="b4794-291">Understand the science.</span></span>       | <span data-ttu-id="b4794-292">Préparez votre application pour les utilisateurs et créez un lanceur 3D.</span><span class="sxs-lookup"><span data-stu-id="b4794-292">Get your app ready for others and consider creating a 3D launcher.</span></span> |

## <a name="useful-resources-on-azure"></a><span data-ttu-id="b4794-293">Ressources utiles sur Azure</span><span class="sxs-lookup"><span data-stu-id="b4794-293">Useful resources on Azure</span></span>

| <span data-ttu-id="b4794-294">![Spatial Anchors](features/images/mrdevcenter/icon-azurespatialanchors.png)</span><span class="sxs-lookup"><span data-stu-id="b4794-294">![Spatial Anchors](features/images/mrdevcenter/icon-azurespatialanchors.png)</span></span><br> [<span data-ttu-id="b4794-295">Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="b4794-295">Spatial Anchors</span></span>](/azure/spatial-anchors/)| <span data-ttu-id="b4794-296">![Services Speech](features/images/mrdevcenter/icon-azurespeechservices.png) [Services Speech](/azure/cognitive-services/speech-service/)</span><span class="sxs-lookup"><span data-stu-id="b4794-296">![Speech Services](features/images/mrdevcenter/icon-azurespeechservices.png) [Speech Services](/azure/cognitive-services/speech-service/)</span></span>| <span data-ttu-id="b4794-297">![Services Vision](features/images/mrdevcenter/icon-azurevisionservices.png) [Services Vision](/azure/cognitive-services/computer-vision/)</span><span class="sxs-lookup"><span data-stu-id="b4794-297">![Vision Services](features/images/mrdevcenter/icon-azurevisionservices.png) [Vision Services](/azure/cognitive-services/computer-vision/)</span></span>|
| :------------------------| :--------------------- | :---------------------- |
| <span data-ttu-id="b4794-298">Spatial Anchors est un service multiplateforme qui vous permet de créer des expériences de réalité mixte à l’aide d’objets qui restent au même endroit sur tous les appareils.</span><span class="sxs-lookup"><span data-stu-id="b4794-298">Spatial Anchors is a cross-platform service that allows you to create Mixed Reality experiences using objects that persist their location across devices over time.</span></span>| <span data-ttu-id="b4794-299">Découvrez les fonctionnalités vocales Azure, telles que la reconnaissance vocale, la reconnaissance de l’orateur ou la traduction vocale, que vous pouvez intégrer à votre application.</span><span class="sxs-lookup"><span data-stu-id="b4794-299">Discover and integrate Azure powered speech capabilities like speech to text, speaker recognition or speech translation into your application.</span></span>| <span data-ttu-id="b4794-300">Identifiez et analysez le contenu de vos images et de vos vidéos à l’aide des services de vision, tels que la vision par ordinateur, la détection des visages, la reconnaissance des émotions ou l’indexeur de vidéos.</span><span class="sxs-lookup"><span data-stu-id="b4794-300">Identify and analyze your image or video content using Vision Services like computer vision, face detection, emotion recognition or video indexer.</span></span> |

## <a name="how-to-contribute"></a><span data-ttu-id="b4794-301">Marche à suivre pour contribuer</span><span class="sxs-lookup"><span data-stu-id="b4794-301">How to contribute</span></span>

<span data-ttu-id="b4794-302">Découvrez comment vous pouvez contribuer à MRTK sur [Contribution](contributing/contributing.md).</span><span class="sxs-lookup"><span data-stu-id="b4794-302">Learn how you can contribute to MRTK at [Contributing](contributing/contributing.md).</span></span>

## <a name="getting-help"></a><span data-ttu-id="b4794-303">Obtenir de l’aide</span><span class="sxs-lookup"><span data-stu-id="b4794-303">Getting help</span></span>

<span data-ttu-id="b4794-304">Si vous rencontrez des problèmes dus à l’utilisation de MRTK ou si vous avez des questions sur la façon d’effectuer une opération, vous pouvez vous aider des différentes ressources disponibles :</span><span class="sxs-lookup"><span data-stu-id="b4794-304">If you run into issues caused by MRTK or otherwise have questions about how to do something, there are a few resources that can help:</span></span>

* <span data-ttu-id="b4794-305">Pour signaler un bogue, veuillez [créer un incident](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) dans le dépôt GitHub.</span><span class="sxs-lookup"><span data-stu-id="b4794-305">For bug reports, please [file an issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) on the GitHub repo.</span></span>
* <span data-ttu-id="b4794-306">Pour toute question, veuillez consulter [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) ou le [canal mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) sur Slack.</span><span class="sxs-lookup"><span data-stu-id="b4794-306">For questions, please reach out on either [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) or the [mixed-reality-toolkit channel](https://holodevelopers.slack.com/messages/C2H4HT858) on Slack.</span></span> <span data-ttu-id="b4794-307">Vous pouvez rejoindre la communauté Slack par le biais de l’[envoi d’invitation automatique](https://holodevelopersslack.azurewebsites.net/).</span><span class="sxs-lookup"><span data-stu-id="b4794-307">You can join the Slack community via the [automatic invitation sender](https://holodevelopersslack.azurewebsites.net/).</span></span>