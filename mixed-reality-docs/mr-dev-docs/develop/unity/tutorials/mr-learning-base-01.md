---
title: Présentation des tutoriels MRTK
description: Ce cours montre comment utiliser Mixed Reality Toolkit (MRTK) pour créer une application de réalité mixte à partir de rien.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, MRTK, mixed reality toolkit, solveurs, suivi oculaire, commandes vocales
ms.localizationpriority: high
ms.openlocfilehash: 8bae8b821e7ffe67b745bbbab763193612a58485
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590411"
---
# <a name="1-introduction-to-the-mrtk-tutorials"></a><span data-ttu-id="09c91-104">1. Présentation des tutoriels MRTK</span><span class="sxs-lookup"><span data-stu-id="09c91-104">1. Introduction to the MRTK tutorials</span></span>

<span data-ttu-id="09c91-105">Bienvenue dans la série des tutoriels de démarrage !</span><span class="sxs-lookup"><span data-stu-id="09c91-105">Welcome to the Getting Started tutorial series!</span></span> <span data-ttu-id="09c91-106">Dans ces tutoriels, vous allez découvrir Mixed Reality Toolkit (MRTK), ainsi que les fonctionnalités qu’il propose.</span><span class="sxs-lookup"><span data-stu-id="09c91-106">Over the course of these tutorials, you'll learn about the Mixed Reality Toolkit (MRTK) and some of the features it has to offer.</span></span> <span data-ttu-id="09c91-107">Vous allez également créer une expérience de réalité mixte dans laquelle l’utilisateur pourra explorer un hologramme modélisé d’après le rover Curiosity de la NASA.</span><span class="sxs-lookup"><span data-stu-id="09c91-107">You'll also build a mixed reality experience where the user can explore a hologram modeled after NASA's Mars Curiosity Rover.</span></span> <span data-ttu-id="09c91-108">À la fin de cette série, vous aurez une vision claire de MRTK et de la façon dont il peut accélérer votre processus de développement.</span><span class="sxs-lookup"><span data-stu-id="09c91-108">By the end of this series, you'll have a firm grasp of MRTK and how it can speed up your development process.</span></span>

<span data-ttu-id="09c91-109">Les tutoriels de cette série se suivent, il est donc important de respecter l’ordre indiqué :</span><span class="sxs-lookup"><span data-stu-id="09c91-109">Tutorials in this series are meant to be sequential, so please go through them in the correct order:</span></span>

1. <span data-ttu-id="09c91-110">[Introduction](mr-learning-base-01.md) (vous êtes déjà ici)</span><span class="sxs-lookup"><span data-stu-id="09c91-110">[Introduction](mr-learning-base-01.md) (You're already here)</span></span>
2. [<span data-ttu-id="09c91-111">Initialisation de votre projet et déploiement de votre première application</span><span class="sxs-lookup"><span data-stu-id="09c91-111">Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)
3. [<span data-ttu-id="09c91-112">Configuration des profils MRTK</span><span class="sxs-lookup"><span data-stu-id="09c91-112">Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
4. [<span data-ttu-id="09c91-113">Positionnement des objets dans la scène</span><span class="sxs-lookup"><span data-stu-id="09c91-113">Positioning objects in the scene</span></span>](mr-learning-base-04.md)
5. [<span data-ttu-id="09c91-114">Création de contenu dynamique avec des solveurs</span><span class="sxs-lookup"><span data-stu-id="09c91-114">Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)
6. [<span data-ttu-id="09c91-115">Création d’interfaces utilisateur</span><span class="sxs-lookup"><span data-stu-id="09c91-115">Creating user interfaces</span></span>](mr-learning-base-06.md)
7. [<span data-ttu-id="09c91-116">Interaction avec les objets 3D</span><span class="sxs-lookup"><span data-stu-id="09c91-116">Interacting with 3D objects</span></span>](mr-learning-base-07.md)
8. [<span data-ttu-id="09c91-117">Utilisation du suivi oculaire</span><span class="sxs-lookup"><span data-stu-id="09c91-117">Using eye-tracking</span></span>](mr-learning-base-08.md)
9. [<span data-ttu-id="09c91-118">Utilisation des commandes vocales</span><span class="sxs-lookup"><span data-stu-id="09c91-118">Using voice commands</span></span>](mr-learning-base-09.md)

## <a name="objectives"></a><span data-ttu-id="09c91-119">Objectifs</span><span class="sxs-lookup"><span data-stu-id="09c91-119">Objectives</span></span>

* <span data-ttu-id="09c91-120">Apprendre à configurer Unity pour MRTK</span><span class="sxs-lookup"><span data-stu-id="09c91-120">Learn how to configure Unity for MRTK</span></span>
* <span data-ttu-id="09c91-121">Apprendre à créer et à déployer des applications sur votre appareil</span><span class="sxs-lookup"><span data-stu-id="09c91-121">Learn how to build and deploy to your device</span></span>
* <span data-ttu-id="09c91-122">Apprendre à utiliser certaines des fonctionnalités clés de MRTK</span><span class="sxs-lookup"><span data-stu-id="09c91-122">Learn how to use some of MRTK's key features</span></span>
* <span data-ttu-id="09c91-123">Créer une expérience de réalité mixte complète</span><span class="sxs-lookup"><span data-stu-id="09c91-123">Create a complete mixed reality experience</span></span>

## <a name="prerequisites"></a><span data-ttu-id="09c91-124">Prérequis</span><span class="sxs-lookup"><span data-stu-id="09c91-124">Prerequisites</span></span>

* <span data-ttu-id="09c91-125">PC Windows 10 configuré avec les [outils appropriés installés](../../install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="09c91-125">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="09c91-126">[SDK Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 ou ultérieur</span><span class="sxs-lookup"><span data-stu-id="09c91-126">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 or later</span></span>
* <span data-ttu-id="09c91-127">Appareil HoloLens 2 [configuré pour le développement](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="09c91-127">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>

* <span data-ttu-id="09c91-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> avec Unity 2019 LTS installé et le module de prise en charge de la build d’applications de plateforme Windows universelle ajouté</span><span class="sxs-lookup"><span data-stu-id="09c91-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the Universal Windows Platform Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="09c91-129">La version de MRTK recommandée pour cette série de tutoriels est MRTK 2.5.3.</span><span class="sxs-lookup"><span data-stu-id="09c91-129">The recommended MRTK version for this tutorial series is MRTK 2.5.3.</span></span>

> [!CAUTION]
> <span data-ttu-id="09c91-130">La version d’Unity recommandée pour cette série de tutoriels est Unity 2019 LTS.</span><span class="sxs-lookup"><span data-stu-id="09c91-130">The recommended Unity version for this tutorial series is Unity 2019 LTS.</span></span> <span data-ttu-id="09c91-131">Elle remplace toutes les versions Unity requises qui sont indiquées dans les prérequis ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="09c91-131">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="09c91-132">Tutoriel suivant : 2. Initialisation de votre projet et déploiement de votre première application</span><span class="sxs-lookup"><span data-stu-id="09c91-132">Next Tutorial: 2. Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)
