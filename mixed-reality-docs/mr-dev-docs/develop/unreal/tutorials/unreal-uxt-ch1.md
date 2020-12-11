---
title: 1. Mise en route
description: Partie 1 sur 6 d’une série de tutoriels visant à créer une application de jeu d’échecs simple avec Unreal Engine 4 et le plug-in Mixed Reality Toolkit UX Tools
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, réalité mixte, tutoriel, bien démarrer, mrtk, uxt, UX Tools, documentation, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle
ms.openlocfilehash: 465215efd953c0acb9f2d80a2905ee06963c5f8c
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609720"
---
# <a name="1-getting-started"></a><span data-ttu-id="26ad9-104">1. Mise en route</span><span class="sxs-lookup"><span data-stu-id="26ad9-104">1. Getting started</span></span>

<span data-ttu-id="26ad9-105">Que vous soyez débutant ou expérimenté dans la réalité mixte, ce tutoriel est parfait pour démarrer votre parcours [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) et [Unreal Engine](https://www.unrealengine.com/en-US/).</span><span class="sxs-lookup"><span data-stu-id="26ad9-105">Whether you're new to mixed reality or a seasoned pro, you're in the right place to start your [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) and [Unreal Engine](https://www.unrealengine.com/en-US/) journey.</span></span> <span data-ttu-id="26ad9-106">Cette série de tutoriels vous guide dans la création d’une application interactive de jeu d’échecs en utilisant le [plug-in UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal), qui fait partie de [Mixed Reality Toolkit for Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal).</span><span class="sxs-lookup"><span data-stu-id="26ad9-106">This tutorial series will give you a step-by-step guide on how to build an interactive chess app with the [UX Tools plugin](https://github.com/microsoft/MixedReality-UXTools-Unreal) - part of the [Mixed Reality Toolkit for Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal).</span></span> <span data-ttu-id="26ad9-107">Ce plug-in vous permet d’ajouter des fonctionnalités d’expérience utilisateur courantes à vos projets à l’aide de code, de blueprints et d’exemples.</span><span class="sxs-lookup"><span data-stu-id="26ad9-107">The plugin will help you add common UX features to your projects with code, blueprints, and examples.</span></span> 

![Scène finale dans la fenêtre Viewport](images/unreal-uxt/5-endscene.PNG)

<span data-ttu-id="26ad9-109">À la fin de cette série, vous aurez une expérience des actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="26ad9-109">By the end of the series you'll have experience with:</span></span>
* <span data-ttu-id="26ad9-110">Création d’un nouveau projet</span><span class="sxs-lookup"><span data-stu-id="26ad9-110">Starting a new project</span></span>
* <span data-ttu-id="26ad9-111">La configuration de la réalité mixte</span><span class="sxs-lookup"><span data-stu-id="26ad9-111">Setting up for mixed reality</span></span>
* <span data-ttu-id="26ad9-112">L’utilisation des entrées utilisateur</span><span class="sxs-lookup"><span data-stu-id="26ad9-112">Working with user input</span></span>
* <span data-ttu-id="26ad9-113">L’ajout de boutons</span><span class="sxs-lookup"><span data-stu-id="26ad9-113">Adding buttons</span></span>
* <span data-ttu-id="26ad9-114">Le jeu sur un émulateur ou un appareil</span><span class="sxs-lookup"><span data-stu-id="26ad9-114">Playing on an emulator or device</span></span>

## <a name="prerequisites"></a><span data-ttu-id="26ad9-115">Prérequis</span><span class="sxs-lookup"><span data-stu-id="26ad9-115">Prerequisites</span></span>

<span data-ttu-id="26ad9-116">Avant de commencer, vérifiez que vous avez installé les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="26ad9-116">Make sure you've installed the following before jumping in:</span></span>
* <span data-ttu-id="26ad9-117">Windows 10 1809 ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="26ad9-117">Windows 10 1809 or later</span></span>
* <span data-ttu-id="26ad9-118">SDK Windows 10 (10.0.18362.0 ou version ultérieure)</span><span class="sxs-lookup"><span data-stu-id="26ad9-118">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="26ad9-119">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 ou ultérieur</span><span class="sxs-lookup"><span data-stu-id="26ad9-119">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 or later</span></span>
* <span data-ttu-id="26ad9-120">Appareil Microsoft HoloLens 2 [configuré pour le développement](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) ou l’émulateur</span><span class="sxs-lookup"><span data-stu-id="26ad9-120">Microsoft HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) or Emulator</span></span>
* <span data-ttu-id="26ad9-121">Visual Studio 2019 avec les charges de travail ci-dessous</span><span class="sxs-lookup"><span data-stu-id="26ad9-121">Visual Studio 2019 with the workloads below</span></span>

### <a name="installing-visual-studio-2019"></a><span data-ttu-id="26ad9-122">Installation de Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="26ad9-122">Installing Visual Studio 2019</span></span>

<span data-ttu-id="26ad9-123">Vérifiez d’abord que votre installation a tous les packages Visual Studio nécessaires :</span><span class="sxs-lookup"><span data-stu-id="26ad9-123">First, make sure your setup with all the required Visual Studio packages:</span></span>
1. <span data-ttu-id="26ad9-124">Installez la dernière version de [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/).</span><span class="sxs-lookup"><span data-stu-id="26ad9-124">Install the latest version of [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)</span></span>
2. <span data-ttu-id="26ad9-125">Installez les [charges de travail](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-workloads) suivantes :</span><span class="sxs-lookup"><span data-stu-id="26ad9-125">Install the following [workloads](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-workloads):</span></span>
    * <span data-ttu-id="26ad9-126">Développement Desktop en C++</span><span class="sxs-lookup"><span data-stu-id="26ad9-126">Desktop development with C++</span></span>
    * <span data-ttu-id="26ad9-127">Développement .NET Desktop</span><span class="sxs-lookup"><span data-stu-id="26ad9-127">.NET desktop development</span></span>
    * <span data-ttu-id="26ad9-128">Développement pour la plateforme Windows universelle</span><span class="sxs-lookup"><span data-stu-id="26ad9-128">Universal Windows Platform development</span></span>

3. <span data-ttu-id="26ad9-129">Installez les [composants](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-individual-components) suivants :</span><span class="sxs-lookup"><span data-stu-id="26ad9-129">Install the following [components](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-individual-components):</span></span>
    * <span data-ttu-id="26ad9-130">Compilateurs, outils de build et runtimes > MSVC v142 - VS 2019 C++ ARM64 Build Tools (dernière version)</span><span class="sxs-lookup"><span data-stu-id="26ad9-130">Compilers, build tools, and runtimes > MSVC v142 - VS 2019 C++ ARM64 build tools (latest version)</span></span>

<span data-ttu-id="26ad9-131">C’est tout !</span><span class="sxs-lookup"><span data-stu-id="26ad9-131">That's it!</span></span> <span data-ttu-id="26ad9-132">Vous êtes maintenant prêt à lancer le projet de jeu d’échecs.</span><span class="sxs-lookup"><span data-stu-id="26ad9-132">You're all set to move on to starting the chess project.</span></span>

[<span data-ttu-id="26ad9-133">Section suivante : 2. Initialisation de votre projet et première application</span><span class="sxs-lookup"><span data-stu-id="26ad9-133">Next section: 2. Initializing your project and first application</span></span>](unreal-uxt-ch2.md)