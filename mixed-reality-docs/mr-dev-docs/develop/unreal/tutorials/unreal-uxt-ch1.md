---
title: 1. Mise en route
description: Partie 1 sur 6 d’une série de tutoriels visant à créer une application de jeu d’échecs simple avec Unreal Engine 4 et le plug-in Mixed Reality Toolkit UX Tools
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, réalité mixte, tutoriel, bien démarrer, mrtk, uxt, UX Tools, documentation, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle
ms.openlocfilehash: 762247f550a3471bbbb6d1004283c6f901346503
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009789"
---
# <a name="1-getting-started"></a><span data-ttu-id="a834b-104">1. Mise en route</span><span class="sxs-lookup"><span data-stu-id="a834b-104">1. Getting started</span></span>

<span data-ttu-id="a834b-105">Que vous soyez débutant ou expérimenté dans la réalité mixte, ce tutoriel est parfait pour démarrer votre parcours [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) et [Unreal Engine](https://www.unrealengine.com/en-US/).</span><span class="sxs-lookup"><span data-stu-id="a834b-105">Whether you're new to mixed reality or a seasoned pro, you're in the right place to start your [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) and [Unreal Engine](https://www.unrealengine.com/en-US/) journey.</span></span> <span data-ttu-id="a834b-106">Cette série de tutoriels vous guide dans la création d’une application interactive de jeu d’échecs en utilisant le [plug-in UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal), qui fait partie de [Mixed Reality Toolkit for Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal).</span><span class="sxs-lookup"><span data-stu-id="a834b-106">This tutorial series will give you a step-by-step guide on how to build an interactive chess app with the [UX Tools plugin](https://github.com/microsoft/MixedReality-UXTools-Unreal) - part of the [Mixed Reality Toolkit for Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal).</span></span> <span data-ttu-id="a834b-107">Ce plug-in vous permet d’ajouter des fonctionnalités d’expérience utilisateur courantes à vos projets à l’aide de code, de blueprints et d’exemples.</span><span class="sxs-lookup"><span data-stu-id="a834b-107">The plugin will help you add common UX features to your projects with code, blueprints, and examples.</span></span> 

![Scène finale dans la fenêtre Viewport](images/unreal-uxt/5-endscene.PNG)

<span data-ttu-id="a834b-109">À la fin de cette série, vous aurez une expérience des actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="a834b-109">By the end of the series you'll have experience with:</span></span>
* <span data-ttu-id="a834b-110">Création d’un nouveau projet</span><span class="sxs-lookup"><span data-stu-id="a834b-110">Starting a new project</span></span>
* <span data-ttu-id="a834b-111">La configuration de la réalité mixte</span><span class="sxs-lookup"><span data-stu-id="a834b-111">Setting up for mixed reality</span></span>
* <span data-ttu-id="a834b-112">L’utilisation des entrées utilisateur</span><span class="sxs-lookup"><span data-stu-id="a834b-112">Working with user input</span></span>
* <span data-ttu-id="a834b-113">L’ajout de boutons</span><span class="sxs-lookup"><span data-stu-id="a834b-113">Adding buttons</span></span>
* <span data-ttu-id="a834b-114">Le jeu sur un émulateur ou un appareil</span><span class="sxs-lookup"><span data-stu-id="a834b-114">Playing on an emulator or device</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a834b-115">Prérequis</span><span class="sxs-lookup"><span data-stu-id="a834b-115">Prerequisites</span></span>

<span data-ttu-id="a834b-116">Avant de commencer, vérifiez que vous avez installé les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="a834b-116">Make sure you've installed the following before jumping in:</span></span>
* <span data-ttu-id="a834b-117">Windows 10 1809 ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="a834b-117">Windows 10 1809 or later</span></span>
* <span data-ttu-id="a834b-118">SDK Windows 10 (10.0.18362.0 ou version ultérieure)</span><span class="sxs-lookup"><span data-stu-id="a834b-118">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="a834b-119">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 ou ultérieur</span><span class="sxs-lookup"><span data-stu-id="a834b-119">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 or later</span></span>
* <span data-ttu-id="a834b-120">Appareil Microsoft HoloLens 2 [configuré pour le développement](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) ou [émulateur](../../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-2-emulator-overview)</span><span class="sxs-lookup"><span data-stu-id="a834b-120">Microsoft HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) or [Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-2-emulator-overview)</span></span>
* <span data-ttu-id="a834b-121">Visual Studio 2019 avec les charges de travail ci-dessous</span><span class="sxs-lookup"><span data-stu-id="a834b-121">Visual Studio 2019 with the workloads below</span></span>

### <a name="installing-visual-studio-2019"></a><span data-ttu-id="a834b-122">Installation de Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="a834b-122">Installing Visual Studio 2019</span></span>

<span data-ttu-id="a834b-123">Vérifiez d’abord que votre installation a tous les packages Visual Studio nécessaires :</span><span class="sxs-lookup"><span data-stu-id="a834b-123">First, make sure your setup with all the required Visual Studio packages:</span></span>
1. <span data-ttu-id="a834b-124">Installez la dernière version de [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/).</span><span class="sxs-lookup"><span data-stu-id="a834b-124">Install the latest version of [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)</span></span>
1. <span data-ttu-id="a834b-125">Installez les [charges de travail](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-workloads) suivantes :</span><span class="sxs-lookup"><span data-stu-id="a834b-125">Install the following [workloads](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-workloads):</span></span>
    * <span data-ttu-id="a834b-126">Développement Desktop en C++</span><span class="sxs-lookup"><span data-stu-id="a834b-126">Desktop development with C++</span></span>
    * <span data-ttu-id="a834b-127">Développement .NET Desktop</span><span class="sxs-lookup"><span data-stu-id="a834b-127">.NET desktop development</span></span>
    * <span data-ttu-id="a834b-128">Développement pour la plateforme Windows universelle</span><span class="sxs-lookup"><span data-stu-id="a834b-128">Universal Windows Platform development</span></span>
1. <span data-ttu-id="a834b-129">Dans Développement pour la plateforme Windows universelle, sélectionnez :</span><span class="sxs-lookup"><span data-stu-id="a834b-129">Expand Universal Windows Platform development and select:</span></span> 
    * <span data-ttu-id="a834b-130">Connectivité des périphériques USB</span><span class="sxs-lookup"><span data-stu-id="a834b-130">USB Device Connectivity</span></span>
    * <span data-ttu-id="a834b-131">Outils de plateforme Windows universelle C++ (v142)</span><span class="sxs-lookup"><span data-stu-id="a834b-131">C++ (v142) Universal Windows Platform tools</span></span>

1. <span data-ttu-id="a834b-132">Installez les [composants](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-individual-components) suivants :</span><span class="sxs-lookup"><span data-stu-id="a834b-132">Install the following [components](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-individual-components):</span></span>
    * <span data-ttu-id="a834b-133">Compilateurs, outils de build et runtimes > MSVC v142 - VS 2019 C++ ARM64 Build Tools (dernière version)</span><span class="sxs-lookup"><span data-stu-id="a834b-133">Compilers, build tools, and runtimes > MSVC v142 - VS 2019 C++ ARM64 build tools (latest version)</span></span>

<span data-ttu-id="a834b-134">Vous pouvez confirmer l’installation avec l’image suivante</span><span class="sxs-lookup"><span data-stu-id="a834b-134">You can confirm the installation with the following picture</span></span>

![Cycles importants dans le programme d’installation de Visual Studio](images/unreal-uxt/1-install-the-tools.png)

<span data-ttu-id="a834b-136">C’est tout !</span><span class="sxs-lookup"><span data-stu-id="a834b-136">That's it!</span></span> <span data-ttu-id="a834b-137">Vous êtes maintenant prêt à lancer le projet de jeu d’échecs.</span><span class="sxs-lookup"><span data-stu-id="a834b-137">You're all set to move on to starting the chess project.</span></span>

[<span data-ttu-id="a834b-138">Section suivante : 2. Initialisation de votre projet et première application</span><span class="sxs-lookup"><span data-stu-id="a834b-138">Next section: 2. Initializing your project and first application</span></span>](unreal-uxt-ch2.md)