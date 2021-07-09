---
title: Présentation des tutoriels MRTK
description: Ce cours montre comment utiliser Mixed Reality Toolkit (MRTK) pour créer une application de réalité mixte à partir de rien.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, MRTK, mixed reality toolkit, solveurs, suivi oculaire, commandes vocales
ms.localizationpriority: high
ms.openlocfilehash: abee2163c3b92897396ea35cc43ae025e8e7b804
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175504"
---
# <a name="1-introduction-to-the-mrtk-tutorials"></a><span data-ttu-id="de7b8-104">1. Présentation des tutoriels MRTK</span><span class="sxs-lookup"><span data-stu-id="de7b8-104">1. Introduction to the MRTK tutorials</span></span>

<span data-ttu-id="de7b8-105">Bienvenue dans la série des tutoriels de démarrage !</span><span class="sxs-lookup"><span data-stu-id="de7b8-105">Welcome to the Getting Started tutorial series!</span></span> <span data-ttu-id="de7b8-106">Dans ces tutoriels, vous allez découvrir Mixed Reality Toolkit (MRTK), ainsi que les fonctionnalités qu’il propose.</span><span class="sxs-lookup"><span data-stu-id="de7b8-106">Over the course of these tutorials, you'll learn about the Mixed Reality Toolkit (MRTK) and some of the features it has to offer.</span></span> <span data-ttu-id="de7b8-107">Vous allez également créer une expérience de réalité mixte dans laquelle l’utilisateur pourra explorer un hologramme modélisé d’après le rover Curiosity de la NASA.</span><span class="sxs-lookup"><span data-stu-id="de7b8-107">You'll also build a mixed reality experience where the user can explore a hologram modeled after NASA's Mars Curiosity Rover.</span></span> <span data-ttu-id="de7b8-108">À la fin de cette série, vous aurez une vision claire de MRTK et de la façon dont il peut accélérer votre processus de développement.</span><span class="sxs-lookup"><span data-stu-id="de7b8-108">By the end of this series, you'll have a firm grasp of MRTK and how it can speed up your development process.</span></span>

<span data-ttu-id="de7b8-109">Les tutoriels de cette série se suivent, il est donc important de respecter l’ordre indiqué :</span><span class="sxs-lookup"><span data-stu-id="de7b8-109">Tutorials in this series are meant to be sequential, so please go through them in the correct order:</span></span>

1. <span data-ttu-id="de7b8-110">[Introduction](mr-learning-base-01.md) (vous êtes déjà ici)</span><span class="sxs-lookup"><span data-stu-id="de7b8-110">[Introduction](mr-learning-base-01.md) (You're already here)</span></span>
2. [<span data-ttu-id="de7b8-111">Initialisation de votre projet et déploiement de votre première application</span><span class="sxs-lookup"><span data-stu-id="de7b8-111">Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)
3. [<span data-ttu-id="de7b8-112">Configuration des profils MRTK</span><span class="sxs-lookup"><span data-stu-id="de7b8-112">Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
4. [<span data-ttu-id="de7b8-113">Positionnement des objets dans la scène</span><span class="sxs-lookup"><span data-stu-id="de7b8-113">Positioning objects in the scene</span></span>](mr-learning-base-04.md)
5. [<span data-ttu-id="de7b8-114">Création de contenu dynamique avec des solveurs</span><span class="sxs-lookup"><span data-stu-id="de7b8-114">Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)
6. [<span data-ttu-id="de7b8-115">Création d’interfaces utilisateur</span><span class="sxs-lookup"><span data-stu-id="de7b8-115">Creating user interfaces</span></span>](mr-learning-base-06.md)
7. [<span data-ttu-id="de7b8-116">Interaction avec les objets 3D</span><span class="sxs-lookup"><span data-stu-id="de7b8-116">Interacting with 3D objects</span></span>](mr-learning-base-07.md)
8. [<span data-ttu-id="de7b8-117">Utilisation du suivi oculaire</span><span class="sxs-lookup"><span data-stu-id="de7b8-117">Using eye-tracking</span></span>](mr-learning-base-08.md)
9. [<span data-ttu-id="de7b8-118">Utilisation des commandes vocales</span><span class="sxs-lookup"><span data-stu-id="de7b8-118">Using voice commands</span></span>](mr-learning-base-09.md)

## <a name="objectives"></a><span data-ttu-id="de7b8-119">Objectifs</span><span class="sxs-lookup"><span data-stu-id="de7b8-119">Objectives</span></span>

* <span data-ttu-id="de7b8-120">Apprendre à configurer Unity pour MRTK</span><span class="sxs-lookup"><span data-stu-id="de7b8-120">Learn how to configure Unity for MRTK</span></span>
* <span data-ttu-id="de7b8-121">Apprendre à créer et à déployer des applications sur votre appareil</span><span class="sxs-lookup"><span data-stu-id="de7b8-121">Learn how to build and deploy to your device</span></span>
* <span data-ttu-id="de7b8-122">Apprendre à utiliser certaines des fonctionnalités clés de MRTK</span><span class="sxs-lookup"><span data-stu-id="de7b8-122">Learn how to use some of MRTK's key features</span></span>
* <span data-ttu-id="de7b8-123">Créer une expérience de réalité mixte complète</span><span class="sxs-lookup"><span data-stu-id="de7b8-123">Create a complete mixed reality experience</span></span>

## <a name="prerequisites"></a><span data-ttu-id="de7b8-124">Prérequis</span><span class="sxs-lookup"><span data-stu-id="de7b8-124">Prerequisites</span></span>

* <span data-ttu-id="de7b8-125">PC Windows 10 configuré avec les [outils appropriés installés](../../install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="de7b8-125">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="de7b8-126">[SDK Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 ou ultérieur</span><span class="sxs-lookup"><span data-stu-id="de7b8-126">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 or later</span></span>
* <span data-ttu-id="de7b8-127">Appareil HoloLens 2 [configuré pour le développement](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="de7b8-127">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>

* <span data-ttu-id="de7b8-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> avec Unity 2020.3 LTS ou Unity 2019.4 LTS installé (**OpenXR requiert la version 2020.3.8 ou une version ultérieure pour éviter les bogues**)</span><span class="sxs-lookup"><span data-stu-id="de7b8-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2020.3 LTS or Unity 2019.4 LTS installed (**OpenXR requires 2020.3.8 or later to prevent bugs**)</span></span>

<span data-ttu-id="de7b8-129">Quand vous installez Unity, vérifiez les composants suivants sous **Platforms**.</span><span class="sxs-lookup"><span data-stu-id="de7b8-129">When installing Unity, please make sure to check following components under **'Platforms'**.</span></span>

* <span data-ttu-id="de7b8-130">**Universal Windows Platform Build Support**</span><span class="sxs-lookup"><span data-stu-id="de7b8-130">**Universal Windows Platform Build Support**</span></span>
* <span data-ttu-id="de7b8-131">**Windows Build Support (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="de7b8-131">**Windows Build Support (IL2CPP)**</span></span>

<img src="../../../develop/images/Unity_Install_Option_UWP.png" alt="Unity Universal Windows Platform Build Support option" width="600px">

<span data-ttu-id="de7b8-132">Si vous avez installé Unity sans ces options, vous pouvez les ajouter par le biais du menu **Add Modules** dans Unity Hub.</span><span class="sxs-lookup"><span data-stu-id="de7b8-132">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub.</span></span>

<img src="../../../develop/images/Unity_Install_Option_UWP2.png" alt="Unity Hub - Add Module" width="600px">

> [!Important]
> <span data-ttu-id="de7b8-133">La version de MRTK recommandée pour cette série de tutoriels est MRTK 2.7.2</span><span class="sxs-lookup"><span data-stu-id="de7b8-133">The recommended MRTK version for this tutorial series is MRTK 2.7.2</span></span>

> [!Important]
> <span data-ttu-id="de7b8-134">Cette série de tutoriels prend en charge Unity 2020 LTS (actuellement 2020.3.x) si vous utilisez Open XR ou le plug-in Windows XR, ainsi qu’Unity 2019 LTS (actuellement 2019.4.x) si vous utilisez WSA hérité ou le plug-in Windows XR.</span><span class="sxs-lookup"><span data-stu-id="de7b8-134">This tutorial series supports Unity 2020 LTS(currently 2020.3.x) if you are using Open XR or Windows XR Plugin and also Unity 2019 LTS (currently 2019.4.x) if you are using Legacy WSA or Windows XR Plugin.</span></span> <span data-ttu-id="de7b8-135">Elle remplace toutes les versions Unity requises qui sont indiquées dans les prérequis ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="de7b8-135">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="de7b8-136">Tutoriel suivant : 2. Initialisation de votre projet et déploiement de votre première application</span><span class="sxs-lookup"><span data-stu-id="de7b8-136">Next Tutorial: 2. Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)
