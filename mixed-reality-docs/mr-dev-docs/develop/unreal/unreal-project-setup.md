---
title: Configuration de votre projet Unreal
description: Découvrez comment configurer votre projet avec la dernière version d’Unreal Engine et de Mixed Reality Feature Tool.
author: hferrone
ms.author: v-hferrone
ms.date: 4/28/2021
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, réalité mixte, développement, fonctionnalités, nouveau projet, émulateur, documentation, guides, hologrammes, développement de jeux, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle
ms.openlocfilehash: 8201e97ed35d11404928c1dfe94ad9b7e626e51b
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394612"
---
# <a name="setting-up-your-unreal-project"></a><span data-ttu-id="25f93-104">Configuration de votre projet Unreal</span><span class="sxs-lookup"><span data-stu-id="25f93-104">Setting up your Unreal project</span></span>

<span data-ttu-id="25f93-105">Nous vous recommandons d’installer [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) ou ultérieure pour tirer pleinement parti de la prise en charge intégrée d’HoloLens.</span><span class="sxs-lookup"><span data-stu-id="25f93-105">We recommend installing [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) or later to take full advantage of built-in HoloLens support.</span></span>

<span data-ttu-id="25f93-106">Accédez à l’onglet **Library** dans Epic Games Launcher, sélectionnez la flèche déroulante à côté de **Launch**, puis cliquez sur **Options**.</span><span class="sxs-lookup"><span data-stu-id="25f93-106">Go to the **Library** tab in the Epic Games Launcher, select the dropdown arrow next to **Launch** and click **Options**.</span></span> <span data-ttu-id="25f93-107">Sous **Target Platforms**, sélectionnez **HoloLens 2** et cliquez sur **Apply**.</span><span class="sxs-lookup"><span data-stu-id="25f93-107">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span>
<span data-ttu-id="25f93-108">![Option HoloLens 2 dans l’installation d’Unreal](../images/Unreal_Install_Option_HoloLens2.png)</span><span class="sxs-lookup"><span data-stu-id="25f93-108">![Unreal Install Option HoloLens 2](../images/Unreal_Install_Option_HoloLens2.png)</span></span>

## <a name="import-mixed-reality-toolkit-for-unreal"></a><span data-ttu-id="25f93-109">Importer Mixed Reality Toolkit pour Unreal</span><span class="sxs-lookup"><span data-stu-id="25f93-109">Import Mixed Reality Toolkit for Unreal</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="25f93-111">Mixed Reality Toolkit (MRTK) est un kit de développement multiplateforme open source pour les applications de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="25f93-111">Mixed Reality Toolkit (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="25f93-112">MRTK fournit un système d’entrée multiplateforme, des composants fondamentaux, ainsi que des modules communs pour les interactions spatiales.</span><span class="sxs-lookup"><span data-stu-id="25f93-112">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="25f93-113">Le toolkit vise à accélérer le développement des applications qui ciblent Microsoft HoloLens, les casques immersifs Windows Mixed Reality (VR) et la plateforme OpenVR.</span><span class="sxs-lookup"><span data-stu-id="25f93-113">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="25f93-114">Pour l’installation, nous vous recommandons de suivre la [section Bien démarrer](unreal-development-overview.md#1-getting-started) de notre [parcours de développement Unreal](unreal-development-overview.md).</span><span class="sxs-lookup"><span data-stu-id="25f93-114">For installation, we recommend completing the [Getting Started section](unreal-development-overview.md#1-getting-started) of our curated [Unreal development journey](unreal-development-overview.md).</span></span> <span data-ttu-id="25f93-115">Si vous suivez déjà le parcours de développement Unreal, terminez le reste des étapes de configuration ci-dessous et passez aux [tutoriels Bien démarrer avec HoloLens 2](tutorials/unreal-uxt-ch1.md).</span><span class="sxs-lookup"><span data-stu-id="25f93-115">If you're already following the Unreal development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](tutorials/unreal-uxt-ch1.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="25f93-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Image du logo Unity](../images/MRTK-Unreal-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="25f93-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity logo image](../images/MRTK-Unreal-Banner.png)</span></span><br><span data-ttu-id="25f93-117">**Mixed Reality Toolkit-Unreal (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="25f93-117">**Mixed Reality Toolkit-Unreal (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="25f93-118">Si vous ne souhaitez pas utiliser le MRTK pour Unreal, vous devrez générer un script pour toutes les interactions et tous les comportements.</span><span class="sxs-lookup"><span data-stu-id="25f93-118">If you don't want to use MRTK for Unreal, you'll need to script all interactions and behaviors yourself.</span></span>