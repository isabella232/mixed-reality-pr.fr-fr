---
title: Tutoriels de démarrage - 1. Introduction
description: Ce cours montre comment utiliser Mixed Reality Toolkit (MRTK) pour créer une application de réalité mixte à partir de rien.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens
ms.localizationpriority: high
ms.openlocfilehash: 6d6be08aa532de22a30e70274859eda466a78204
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91697764"
---
# <a name="1-introduction"></a><span data-ttu-id="f436f-105">1. Introduction</span><span class="sxs-lookup"><span data-stu-id="f436f-105">1. Introduction</span></span>

## <a name="overview"></a><span data-ttu-id="f436f-106">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="f436f-106">Overview</span></span>

<span data-ttu-id="f436f-107">Bienvenue dans la série des tutoriels de démarrage !</span><span class="sxs-lookup"><span data-stu-id="f436f-107">Welcome to the Getting Started tutorial series!</span></span> <span data-ttu-id="f436f-108">Dans ces tutoriels, vous allez découvrir Mixed Reality Toolkit (MRTK), ainsi que les fonctionnalités qu’il propose.</span><span class="sxs-lookup"><span data-stu-id="f436f-108">Over the course of these tutorials, you'll learn about the Mixed Reality Toolkit (MRTK) and some of the features it has to offer.</span></span> <span data-ttu-id="f436f-109">Vous allez également créer une expérience de réalité mixte dans laquelle l’utilisateur pourra explorer un hologramme modélisé d’après le rover Curiosity de la NASA.</span><span class="sxs-lookup"><span data-stu-id="f436f-109">You'll also build a mixed reality experience where the user can explore a hologram modeled after NASA's Mars Curiosity Rover.</span></span> <span data-ttu-id="f436f-110">À la fin de cette série, vous aurez une vision claire de MRTK et de la façon dont il peut accélérer votre processus de développement.</span><span class="sxs-lookup"><span data-stu-id="f436f-110">By the end of this series, you'll have a firm grasp of MRTK and how it can speed up your development process.</span></span>

<span data-ttu-id="f436f-111">Les tutoriels de cette série se suivent, il est donc important de respecter l’ordre indiqué :</span><span class="sxs-lookup"><span data-stu-id="f436f-111">Tutorials in this series are meant to be sequential, so please go through them in the correct order:</span></span>

1. <span data-ttu-id="f436f-112">[Introduction](mr-learning-base-01.md) (vous êtes déjà ici)</span><span class="sxs-lookup"><span data-stu-id="f436f-112">[Introduction](mr-learning-base-01.md) (You're already here)</span></span>
2. [<span data-ttu-id="f436f-113">Initialisation de votre projet et déploiement de votre première application</span><span class="sxs-lookup"><span data-stu-id="f436f-113">Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)
3. [<span data-ttu-id="f436f-114">Configuration des profils MRTK</span><span class="sxs-lookup"><span data-stu-id="f436f-114">Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
4. [<span data-ttu-id="f436f-115">Positionnement des objets dans la scène</span><span class="sxs-lookup"><span data-stu-id="f436f-115">Positioning objects in the scene</span></span>](mr-learning-base-04.md)
5. [<span data-ttu-id="f436f-116">Création de contenu dynamique avec des solveurs</span><span class="sxs-lookup"><span data-stu-id="f436f-116">Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)
6. [<span data-ttu-id="f436f-117">Création d’interfaces utilisateur</span><span class="sxs-lookup"><span data-stu-id="f436f-117">Creating user interfaces</span></span>](mr-learning-base-06.md)
7. [<span data-ttu-id="f436f-118">Interaction avec les objets 3D</span><span class="sxs-lookup"><span data-stu-id="f436f-118">Interacting with 3D objects</span></span>](mr-learning-base-07.md)
8. [<span data-ttu-id="f436f-119">Utilisation du suivi oculaire</span><span class="sxs-lookup"><span data-stu-id="f436f-119">Using eye-tracking</span></span>](mr-learning-base-08.md)
9. [<span data-ttu-id="f436f-120">Utilisation des commandes vocales</span><span class="sxs-lookup"><span data-stu-id="f436f-120">Using voice commands</span></span>](mr-learning-base-09.md)

## <a name="objectives"></a><span data-ttu-id="f436f-121">Objectifs</span><span class="sxs-lookup"><span data-stu-id="f436f-121">Objectives</span></span>

* <span data-ttu-id="f436f-122">Apprendre à configurer Unity pour MRTK</span><span class="sxs-lookup"><span data-stu-id="f436f-122">Learn how to configure Unity for MRTK</span></span>
* <span data-ttu-id="f436f-123">Apprendre à créer et à déployer des applications sur votre appareil</span><span class="sxs-lookup"><span data-stu-id="f436f-123">Learn how to build and deploy to your device</span></span>
* <span data-ttu-id="f436f-124">Apprendre à utiliser certaines des fonctionnalités clés de MRTK</span><span class="sxs-lookup"><span data-stu-id="f436f-124">Learn how to use some of MRTK's key features</span></span>
* <span data-ttu-id="f436f-125">Créer une expérience de réalité mixte complète</span><span class="sxs-lookup"><span data-stu-id="f436f-125">Create a complete mixed reality experience</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f436f-126">Prérequis</span><span class="sxs-lookup"><span data-stu-id="f436f-126">Prerequisites</span></span>

* <span data-ttu-id="f436f-127">PC Windows 10 configuré avec les [outils appropriés installés](../../install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="f436f-127">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="f436f-128">[SDK Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 ou ultérieur</span><span class="sxs-lookup"><span data-stu-id="f436f-128">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 or later</span></span>
* <span data-ttu-id="f436f-129">Appareil HoloLens 2 [configuré pour le développement](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="f436f-129">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="f436f-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> avec Unity 2019.3.15 installé et le module de prise en charge de la build d’applications de plateforme Windows universelle ajouté</span><span class="sxs-lookup"><span data-stu-id="f436f-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Universal Windows Platform Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="f436f-131">La version MRTK recommandée pour cette série de tutoriels est MRTK 2.4.0.</span><span class="sxs-lookup"><span data-stu-id="f436f-131">The recommended MRTK version for this tutorial series is MRTK 2.4.0.</span></span>

> [!CAUTION]
> <span data-ttu-id="f436f-132">La version Unity recommandée pour cette série de tutoriels est Unity 2019.3.15.</span><span class="sxs-lookup"><span data-stu-id="f436f-132">The recommended Unity version for this tutorial series is Unity 2019.3.15.</span></span> <span data-ttu-id="f436f-133">Elle remplace toutes les versions Unity requises qui sont indiquées dans les prérequis ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="f436f-133">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f436f-134">Tutoriel suivant : 2. Initialisation de votre projet et déploiement de votre première application</span><span class="sxs-lookup"><span data-stu-id="f436f-134">Next Tutorial: 2. Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)

