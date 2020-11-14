---
title: Tutoriel sur le cloud Azure - 1. Azure Cloud Services pour HoloLens 2
description: Suivez ce cours pour découvrir comment implémenter différents services Azure dans une application HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: azure, réalité mixte, Unity, tutoriel, hololens, hololens 2, stockage blob azure, stockage table Azure, ancres spatiales azure, azure bot framework
ms.localizationpriority: high
ms.openlocfilehash: 878fd92a946b70ba3b0a867722f86ab801a79032
ms.sourcegitcommit: 8fd127aff85b77778bd7a75c5ec5215d27ecf21a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2020
ms.locfileid: "93416975"
---
# <a name="1-azure-cloud-services-for-hololens-2"></a><span data-ttu-id="356f9-105">1. Azure Cloud Services pour HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="356f9-105">1. Azure Cloud Services for HoloLens 2</span></span>

## <a name="overview"></a><span data-ttu-id="356f9-106">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="356f9-106">Overview</span></span>

<span data-ttu-id="356f9-107">Bienvenue dans cette série de tutoriels consacrés à l’intégration de services **cloud Azure** dans une application **HoloLens 2**.</span><span class="sxs-lookup"><span data-stu-id="356f9-107">Welcome to this series of tutorials focused on bringing **Azure Cloud** services into a **HoloLens 2** application.</span></span> <span data-ttu-id="356f9-108">Dans cette série de cinq tutoriels, vous allez apprendre à intégrer plusieurs services **cloud Azure** dans un projet **Unity** pour **HoloLens 2**.</span><span class="sxs-lookup"><span data-stu-id="356f9-108">In this five-part tutorial series, you will learn how to integrate several **Azure Cloud** services into a **Unity** project for **HoloLens 2**.</span></span> <span data-ttu-id="356f9-109">Avec chaque chapitre consécutif, vous ajouterez de nouveaux services **cloud Azure** pour étendre les fonctionnalités de l’application et l’expérience utilisateur, tout en apprenant les principes fondamentaux de chaque service **cloud Azure**.</span><span class="sxs-lookup"><span data-stu-id="356f9-109">With each consecutive chapter, you will add new **Azure Cloud** services to expand the application features and user experience, while teaching you the fundamentals of each **Azure Cloud** service.</span></span>

> [!NOTE]
> <span data-ttu-id="356f9-110">Cette série de tutoriels se concentrera sur **HoloLens 2** , mais en raison de la nature multiplateforme de Unity, la plus grande partie de ce que vous allez apprendre s’appliquera aussi aux applications pour poste de travail et pour smartphone.</span><span class="sxs-lookup"><span data-stu-id="356f9-110">This tutorial series will focus on the **HoloLens 2** but due the cross-platform nature of Unity, most of your learnings will also apply for Desktop and Smartphone applications.</span></span>

<span data-ttu-id="356f9-111">Dans ce premier tutoriel, vous allez découvrir les objectifs de la série et de chaque service cloud Azure que vous utiliserez, ainsi que la configuration du projet Unity initial.</span><span class="sxs-lookup"><span data-stu-id="356f9-111">In this first tutorial, you'll be introduced to the goals of the series and each Azure Cloud service you'll be using, as well as setting up the initial Unity project.</span></span>

<span data-ttu-id="356f9-112">Dans le deuxième tutoriel, [Intégration du Stockage Azure](mr-learning-azure-02.md), vous commencerez par intégrer Stockage Azure comme solution de persistance pour l’application de démonstration.</span><span class="sxs-lookup"><span data-stu-id="356f9-112">In the second tutorial, [Integrating Azure Storage](mr-learning-azure-02.md), you'll start off by integrating Azure Storage as the persistence solution for the demo application.</span></span> <span data-ttu-id="356f9-113">Vous découvrirez également les différences entre le stockage Blob et le stockage Table, vous préparerez les ressources de projet nécessaires et configurerez la scène.</span><span class="sxs-lookup"><span data-stu-id="356f9-113">You'll also learn the differences between Blob Storage and Table Storage, prepare the needed project resources, setup the scene.</span></span> <span data-ttu-id="356f9-114">Pour finir, vous apprendrez à vérifier les opérations de lecture, de mise à jour et de suppression de données.</span><span class="sxs-lookup"><span data-stu-id="356f9-114">Finally, you'll learn how to verify the read, update, and delete data operations.</span></span>

<span data-ttu-id="356f9-115">En poursuivant avec le troisième tutoriel, [Intégration d’Azure Custom Vision](mr-learning-azure-03.md), vous allez utiliser Azure Custom Vision pour entraîner et détecter des images dans l’application HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="356f9-115">Continuing with the third tutorial, [Integrating Azure Custom Vision](mr-learning-azure-03.md), you will use Azure Custom Vision to train and detect images in the HoloLens 2 application.</span></span> <span data-ttu-id="356f9-116">Le chapitre commence par la configuration de votre propre ressource Azure Custom Vision, la préparation des composants de la scène, et la mise en œuvre de l’entraînement et de la détection de vos propres images à partir de l’application.</span><span class="sxs-lookup"><span data-stu-id="356f9-116">The chapter starts off with setting up your own Azure Custom Vision resource, preparing the scene components and getting into action by training and detecting your own images from inside the application.</span></span>

<span data-ttu-id="356f9-117">Ensuite, vous passez au quatrième tutoriel, [Intégration d’Azure Spatial Anchors](mr-learning-azure-04.md), avec l’exploration du service Azure Spatial Anchors pour enregistrer et rechercher des emplacements, découvrir les concepts fondamentaux, préparer les ressources nécessaires, configurer la scène et commencer à utiliser la nouvelle fonctionnalité dans l’application.</span><span class="sxs-lookup"><span data-stu-id="356f9-117">Next you advance in the fourth tutorial, [Integrating Azure Spatial Anchors](mr-learning-azure-04.md), with exploring Azure Spatial Anchors service to save and find locations, learn the core concepts, prepare necessary resources, setup the scene and start using the new feature in the application.</span></span>

<span data-ttu-id="356f9-118">Avec le cinquième tutoriel, [Intégration d’Azure Bot Service avec LUIS](mr-learning-azure-05.md), vous terminez en ajoutant à l’application une nouvelle méthode d’interaction utilisateur : le langage naturel !</span><span class="sxs-lookup"><span data-stu-id="356f9-118">With the fifth tutorial, [Integrating Azure Bot Service with LUIS](mr-learning-azure-05.md), you finalize by giving the application a new method of user interaction: natural language!</span></span> <span data-ttu-id="356f9-119">Cette fonctionnalité sera réalisée avec Azure Bot Framework et LUIS (Language Understanding).</span><span class="sxs-lookup"><span data-stu-id="356f9-119">This feature will be realized by using the Azure Bot Framework together with Language Understanding (LUIS).</span></span> <span data-ttu-id="356f9-120">Ce chapitre final vous fait découvrir les bases d’Azure Bot Service et, pour accélérer le processus, vous allez utiliser le composeur Bot Framework comme solution avec zéro code.</span><span class="sxs-lookup"><span data-stu-id="356f9-120">This final chapter teaches you the basics of Azure Bot Service and to speed up the process you will be using the Bot Framework Composer as a zero code solution.</span></span> <span data-ttu-id="356f9-121">Une fois le bot créé, vous allez l’intégrer dans la scène et l’exécuter avec l’application HoloLens 2 dans sa dernière version.</span><span class="sxs-lookup"><span data-stu-id="356f9-121">Once the bot is created, you will integrate it into the scene and give it a run with the final stage of the HoloLens 2 application.</span></span>

## <a name="application-goals"></a><span data-ttu-id="356f9-122">Objectifs de l’application</span><span class="sxs-lookup"><span data-stu-id="356f9-122">Application goals</span></span>

<span data-ttu-id="356f9-123">Dans cette série de tutoriels, vous allez créer une application **HoloLens 2** capable de détecter des objets à partir d’images et de trouver leur emplacement spatial.</span><span class="sxs-lookup"><span data-stu-id="356f9-123">In this tutorial series, you will build a **HoloLens 2** application that can detect objects from images and find its spatial location.</span></span> <span data-ttu-id="356f9-124">Pour définir une terminologie du domaine, vous appelez à partir de maintenant ces entités des **objets suivis**.</span><span class="sxs-lookup"><span data-stu-id="356f9-124">To set a domain language, you call such entities from now **Tracked Object**.</span></span>
<span data-ttu-id="356f9-125">L’utilisateur peut créer un **objet suivi** pour associer un ensemble d’images via la vision par ordinateur et/ou un emplacement spatial.</span><span class="sxs-lookup"><span data-stu-id="356f9-125">The user can create a **Tracked Object** to either or both associate a set of images via computer vision and/or a spatial location.</span></span> <span data-ttu-id="356f9-126">Toutes les données doivent être conservées dans le cloud.</span><span class="sxs-lookup"><span data-stu-id="356f9-126">All data must be persisted into the cloud.</span></span> <span data-ttu-id="356f9-127">De plus, certains aspects de l’application seront éventuellement contrôlés par le langage naturel via un bot.</span><span class="sxs-lookup"><span data-stu-id="356f9-127">Furthermore some aspects of the application will be optionally controlled by natural language assisted through a bot.</span></span>

### <a name="features"></a><span data-ttu-id="356f9-128">Fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="356f9-128">Features</span></span>

* <span data-ttu-id="356f9-129">Gestion de base des données et des images</span><span class="sxs-lookup"><span data-stu-id="356f9-129">Basic managing of data and images</span></span>
* <span data-ttu-id="356f9-130">Entraînement et détection d’images</span><span class="sxs-lookup"><span data-stu-id="356f9-130">Image training and detection</span></span>
* <span data-ttu-id="356f9-131">Stockage d’un emplacement spatial et conseils pour ce stockage</span><span class="sxs-lookup"><span data-stu-id="356f9-131">Storing a spatial location and guidance to it</span></span>
* <span data-ttu-id="356f9-132">Assistant bot pour utiliser certaines fonctionnalités via le langage naturel</span><span class="sxs-lookup"><span data-stu-id="356f9-132">Bot assistant to use some features via natural language</span></span>

## <a name="azure-cloud-services"></a><span data-ttu-id="356f9-133">Services cloud Azure</span><span class="sxs-lookup"><span data-stu-id="356f9-133">Azure Cloud services</span></span>

<span data-ttu-id="356f9-134">Pour implémenter les fonctionnalités ci-dessus, vous utiliserez les services **cloud Azure** suivants :</span><span class="sxs-lookup"><span data-stu-id="356f9-134">You'll use the following **Azure Cloud** services to implement the above features:</span></span>

### <a name="azure-storage"></a><span data-ttu-id="356f9-135">Stockage Azure</span><span class="sxs-lookup"><span data-stu-id="356f9-135">Azure Storage</span></span>

<span data-ttu-id="356f9-136">Vous allez utiliser [Stockage Azure](https://azure.microsoft.com/services/storage/) pour la solution de persistance.</span><span class="sxs-lookup"><span data-stu-id="356f9-136">You will use [Azure Storage](https://azure.microsoft.com/services/storage/) for the persistence solution.</span></span> <span data-ttu-id="356f9-137">Il vous permet de stocker des données sur une table et de charger des données binaires volumineuses, comme des images.</span><span class="sxs-lookup"><span data-stu-id="356f9-137">It allows you to store data on a table and upload large binaries like images.</span></span>

### <a name="azure-custom-vision"></a><span data-ttu-id="356f9-138">Azure Custom Vision</span><span class="sxs-lookup"><span data-stu-id="356f9-138">Azure Custom Vision</span></span>

<span data-ttu-id="356f9-139">Avec [Azure Custom Vision](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/) (qui fait partie d’ [Azure Cognitive Services](https://azure.microsoft.com/services/cognitive-services/)), vous pouvez associer à des *objets suivis* un ensemble d’images, entraîner un modèle Machine Learning sur l’ensemble d’images et détecter l’ *objet suivi*.</span><span class="sxs-lookup"><span data-stu-id="356f9-139">With [Azure Custom Vision](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/) (part of the [Azure Cognitive Services](https://azure.microsoft.com/services/cognitive-services/)) you can associate to *Tracked Objects* a set of images, train a machine learning model on the set and detect the *Tracked Object*.</span></span>

### <a name="azure-spatial-anchors"></a><span data-ttu-id="356f9-140">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="356f9-140">Azure Spatial Anchors</span></span>

<span data-ttu-id="356f9-141">Pour stocker un emplacement d’ *objet suivi* et donner des directions guidées pour le trouver, vous utilisez [Azure Spatial Anchors](https://azure.microsoft.com/services/spatial-anchors/).</span><span class="sxs-lookup"><span data-stu-id="356f9-141">To store a *Tracked Object* location and give a guided directions to find it, you use [Azure Spatial Anchors](https://azure.microsoft.com/services/spatial-anchors/).</span></span>

### <a name="azure-bot-service"></a><span data-ttu-id="356f9-142">Azure Bot Service</span><span class="sxs-lookup"><span data-stu-id="356f9-142">Azure Bot Service</span></span>

<span data-ttu-id="356f9-143">L’application est pilotée principalement par une interface utilisateur traditionnelle : vous utilisez donc [Azure Bot Service](https://azure.microsoft.com/services/bot-service/) pour ajouter une personnalité et faire office de nouvelle méthode d’interaction.</span><span class="sxs-lookup"><span data-stu-id="356f9-143">The application is mainly driven by traditional UI, so you use the [Azure Bot Service](https://azure.microsoft.com/services/bot-service/) to add some personality and act as a new interaction method.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="356f9-144">Prérequis</span><span class="sxs-lookup"><span data-stu-id="356f9-144">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="356f9-145">Si vous n’avez pas encore terminé la série de [tutoriels de démarrage](mr-learning-base-01.md), nous vous conseillons de le faire avant d’aller plus loin.</span><span class="sxs-lookup"><span data-stu-id="356f9-145">If you have not completed the [Getting started tutorials](mr-learning-base-01.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="356f9-146">PC Windows 10 configuré avec les [outils appropriés installés](../../install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="356f9-146">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="356f9-147">SDK Windows 10 (10.0.18362.0 ou version ultérieure)</span><span class="sxs-lookup"><span data-stu-id="356f9-147">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="356f9-148">Capacité de programmation C# de base</span><span class="sxs-lookup"><span data-stu-id="356f9-148">Some basic C# programming ability</span></span>
* <span data-ttu-id="356f9-149">Appareil HoloLens 2 [configuré pour le développement](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="356f9-149">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="356f9-150">Une webcam connectée si vous voulez tester depuis l’éditeur Unity</span><span class="sxs-lookup"><span data-stu-id="356f9-150">A connected webcam if you like to test from Unity editor</span></span>
* <span data-ttu-id="356f9-151"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> avec Unity 2019 LTS installé et le module de prise en charge de la build d’applications de plateforme Windows universelle ajouté</span><span class="sxs-lookup"><span data-stu-id="356f9-151"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the Universal Windows Platform Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="356f9-152">La version d’Unity recommandée pour cette série de tutoriels est Unity 2019 LTS.</span><span class="sxs-lookup"><span data-stu-id="356f9-152">The recommended Unity version for this tutorial series is Unity 2019 LTS.</span></span> <span data-ttu-id="356f9-153">Elle remplace toutes les versions Unity requises ou recommandées qui sont indiquées dans les prérequis ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="356f9-153">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="356f9-154">Création et préparation du projet Unity</span><span class="sxs-lookup"><span data-stu-id="356f9-154">Creating and preparing the Unity project</span></span>

<span data-ttu-id="356f9-155">Dans cette section, vous allez créer un projet Unity et le préparer au développement avec MRTK.</span><span class="sxs-lookup"><span data-stu-id="356f9-155">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="356f9-156">Pour cela, suivez d’abord [Initialisation de votre projet et de votre première application](mr-learning-base-02.md), en excluant les instructions données dans [Générer votre application sur votre appareil](mr-learning-base-02.md#building-your-application-to-your-hololens-2), ce qui inclut les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="356f9-156">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="356f9-157">[Création du projet Unity](mr-learning-base-02.md#creating-the-unity-project) et affectation d’un nom pertinent, par exemple *Azure Cloud Tutorials*</span><span class="sxs-lookup"><span data-stu-id="356f9-157">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *Azure Cloud Tutorials*</span></span>
2. [<span data-ttu-id="356f9-158">Changement de plateforme de génération</span><span class="sxs-lookup"><span data-stu-id="356f9-158">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
3. [<span data-ttu-id="356f9-159">Importation des ressources TextMeshPro Essential</span><span class="sxs-lookup"><span data-stu-id="356f9-159">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="356f9-160">Importation du Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="356f9-160">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [<span data-ttu-id="356f9-161">Configuration du projet Unity</span><span class="sxs-lookup"><span data-stu-id="356f9-161">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
6. <span data-ttu-id="356f9-162">[Création et configuration de la scène](mr-learning-base-02.md#creating-and-configuring-the-scene), et affectation d’un nom pertinent à la scène, par exemple *AzureCloudServices*</span><span class="sxs-lookup"><span data-stu-id="356f9-162">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *AzureCloudServices*</span></span>

<span data-ttu-id="356f9-163">Ensuite, suivez les instructions de [Changer l’option d’affichage de la reconnaissance spatiale](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) pour remplacer le profil de configuration MRTK de votre scène par **DefaultHoloLens2ConfigurationProfile** et remplacer les options d’affichage du maillage de la reconnaissance spatiale par **Occlusion**.</span><span class="sxs-lookup"><span data-stu-id="356f9-163">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="356f9-164">Installation de packages Unity intégrés</span><span class="sxs-lookup"><span data-stu-id="356f9-164">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="356f9-165">Dans le menu Unity, sélectionnez **Window** > **Package Manager** pour ouvrir la fenêtre Package Manager, sélectionnez **AR Foundation** , puis cliquez sur le bouton **Install** pour installer le package :</span><span class="sxs-lookup"><span data-stu-id="356f9-165">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![Fenêtre Unity - Package Manager, avec AR Foundation sélectionné](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="356f9-167">Vous installez le package intégré AR Foundation, car il est nécessaire pour le SDK Azure Spatial Anchors que vous allez importer dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="356f9-167">You are installing the AR Foundation package because the Azure Spatial Anchors SDK requires it, which you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="356f9-168">Importation des ressources du tutoriel</span><span class="sxs-lookup"><span data-stu-id="356f9-168">Importing the tutorial assets</span></span>

<span data-ttu-id="356f9-169">Téléchargez et **importez** les packages personnalisés Unity suivants **dans l’ordre où ils sont listés**  :</span><span class="sxs-lookup"><span data-stu-id="356f9-169">Download and **import** the following Unity custom packages **in the order they are listed** :</span></span>

* [<span data-ttu-id="356f9-170">AzureSpatialAnchors.unitypackage</span><span class="sxs-lookup"><span data-stu-id="356f9-170">AzureSpatialAnchors.unitypackage</span></span>](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage)
* [<span data-ttu-id="356f9-171">AzureStorageForUnity.unitypackage</span><span class="sxs-lookup"><span data-stu-id="356f9-171">AzureStorageForUnity.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureStorageForUnity.unitypackage)
* [<span data-ttu-id="356f9-172">MRTK.Tutorials.AzureCloudServices.unitypackage</span><span class="sxs-lookup"><span data-stu-id="356f9-172">MRTK.Tutorials.AzureCloudServices.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/MRTK.Tutorials.AzureCloudServices.unitypackage)

> [!TIP]
> <span data-ttu-id="356f9-173">Pour un rappel de la façon d’importer un package personnalisé Unity, vous pouvez vous référer aux instructions de [Importer le Kit de ressources de réalité mixte](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="356f9-173">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="356f9-174">Une fois que vous avez importé les ressources du tutoriel, votre fenêtre Project doit ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="356f9-174">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Fenêtres Hierarchy, Scene et Project dans Unity, après l’importation des ressources du tutoriel](images/mr-learning-azure/tutorial1-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="356f9-176">Si vous voyez des avertissements CS0618 signalant que « WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr) » et « WorldAnchor.GetNativeSpatialAnchorPtr() » sont obsolètes, vous pouvez les ignorer.</span><span class="sxs-lookup"><span data-stu-id="356f9-176">If you see any CS0618 warnings regarding 'WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)' and 'WorldAnchor.GetNativeSpatialAnchorPtr()' being obsolete, you can ignore these warnings.</span></span>

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="356f9-177">Création et préparation de la scène</span><span class="sxs-lookup"><span data-stu-id="356f9-177">Creating and preparing the scene</span></span>
<!-- TODO: Consider renaming to 'Preparing the scene' -->

<span data-ttu-id="356f9-178">Dans cette section, vous allez préparer la scène en ajoutant une partie des préfabriqués du tutoriel.</span><span class="sxs-lookup"><span data-stu-id="356f9-178">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="356f9-179">Dans la fenêtre Project, accédez au dossier **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager**.</span><span class="sxs-lookup"><span data-stu-id="356f9-179">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span> <span data-ttu-id="356f9-180">Tout en maintenant le bouton Ctrl enfoncé, cliquez sur **SceneController** , **RootMenu** et **DataManager** pour sélectionner les trois préfabriqués :</span><span class="sxs-lookup"><span data-stu-id="356f9-180">While holding down the CTRL button, click on **SceneController** , **RootMenu** and **DataManager** to select the three prefabs:</span></span>

![Unity avec les préfabriqués SceneController, RootMenu et DataManager sélectionnés](images/mr-learning-azure/tutorial1-section5-step1-1.png)

<span data-ttu-id="356f9-182">**SceneController (prefab)** contient deux scripts, **SceneController (script)** et **UnityDispatcher (script)** .</span><span class="sxs-lookup"><span data-stu-id="356f9-182">The **SceneController (prefab)** contains two scripts, **SceneController (script)** and **UnityDispatcher (script)**.</span></span> <span data-ttu-id="356f9-183">Le composant de script **SceneController** contient plusieurs fonctions d’expérience utilisateur et facilite la fonctionnalité de capture de photos, **UnityDispatcher** étant une classe helper pour autoriser les actions d’exécution sur le thread Unity principal.</span><span class="sxs-lookup"><span data-stu-id="356f9-183">The **SceneController** script component contains several UX functions and facilitates the photo capture functionality while **UnityDispatcher** is a helper class to allow execute actions on the Unity main thread.</span></span>

<span data-ttu-id="356f9-184">**RootMenu (prefab)** est le préfabriqué d’interface utilisateur principal qui contient toutes les fenêtres d’interface utilisateur qui sont connectées l’une à l’autre via différents petits composants de script et qui contrôlent le flux général de l’interface utilisateur de l’application.</span><span class="sxs-lookup"><span data-stu-id="356f9-184">The **RootMenu (prefab)** is the primary UI prefab that holds all UI windows that are connected to each other through various small script components and control the general UX flow of the application.</span></span>

<span data-ttu-id="356f9-185">**DataManager (prefab)** est responsable de la communication avec le stockage Azure et il sera expliqué plus en détail dans le tutoriel suivant.</span><span class="sxs-lookup"><span data-stu-id="356f9-185">The **DataManager (prefab)** is responsible for talking to Azure storage and will be explained further in the next tutorial.</span></span>

<span data-ttu-id="356f9-186">Les trois préfabriqués étant sélectionnés, faites-les maintenant glisser dans la fenêtre Hierarchy pour les ajouter à la scène :</span><span class="sxs-lookup"><span data-stu-id="356f9-186">Now with the three prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![Unity avec les préfabriqués SceneController, RootMenu et DataManager nouvellement ajoutés toujours sélectionnés](images/mr-learning-azure/tutorial1-section5-step1-2.png)

<span data-ttu-id="356f9-188">Pour vous concentrer sur les objets de la scène, vous pouvez double-cliquer sur l’objet **RootMenu** , puis effectuer à nouveau un léger zoom arrière :</span><span class="sxs-lookup"><span data-stu-id="356f9-188">To focus in on the objects in the scene, you can double-click on the **RootMenu** object, and then zoom slightly out again:</span></span>

![Unity avec l’objet RootMenu sélectionné](images/mr-learning-azure/tutorial1-section5-step1-3.png)

> [!TIP]
> <span data-ttu-id="356f9-190">Si vous trouvez gênantes les grandes icônes de votre scène, par exemple les grandes icônes « T », vous pouvez les masquer en <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">basculant le gizmos</a> sur la position Off.</span><span class="sxs-lookup"><span data-stu-id="356f9-190">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-scene"></a><span data-ttu-id="356f9-191">Configuration de la scène</span><span class="sxs-lookup"><span data-stu-id="356f9-191">Configuring the scene</span></span>

<span data-ttu-id="356f9-192">Dans cette section, vous allez connecter ensemble *SceneManager* , *DataManager* et *RootMenu* pour avoir une scène de travail prête pour le tutoriel suivant, [Intégration de Stockage Azure](mr-learning-azure-01.md).</span><span class="sxs-lookup"><span data-stu-id="356f9-192">In this section, you will connect *SceneManager* , *DataManager* and *RootMenu* together to have a working scene to be ready for the following [Integrating Azure storage](mr-learning-azure-01.md) tutorial.</span></span>

### <a name="connect-the-objects"></a><span data-ttu-id="356f9-193">Connecter les objets</span><span class="sxs-lookup"><span data-stu-id="356f9-193">Connect the objects</span></span>

<span data-ttu-id="356f9-194">Dans la fenêtre Hierarchy, sélectionnez l’objet **DataManager**  :</span><span class="sxs-lookup"><span data-stu-id="356f9-194">In the Hierarchy window, select the **DataManager** object:</span></span>

![Unity avec l’objet DataManager sélectionné](images/mr-learning-azure/tutorial1-section6-step1-1.png)

<span data-ttu-id="356f9-196">Dans la fenêtre Inspector, recherchez le composant **DataManager (Script)**  : vous verrez un emplacement vide sur l’événement **On Data Manager Ready ()** .</span><span class="sxs-lookup"><span data-stu-id="356f9-196">In the Inspector window, locate the **DataManager (Script)** component and you will see an empty slot on the **On Data Manager Ready ()** event.</span></span> <span data-ttu-id="356f9-197">À présent, dans la fenêtre Hierarchy, faites glisser l’objet **SceneController** dans l’événement **On Data Manager Ready ()** .</span><span class="sxs-lookup"><span data-stu-id="356f9-197">Now from the Hierarchy window drag the **SceneController** object into the **On Data Manager Ready ()** event.</span></span>

![Unity avec l’écouteur d’événements DataManager ajouté](images/mr-learning-azure/tutorial1-section6-step1-2.png)

<span data-ttu-id="356f9-199">Vous remarquerez que le menu déroulant de l’événement est devenu actif. Cliquez sur le menu déroulant et accédez à **SceneController** puis, dans le sous-menu, sélectionnez l’option **Init ()**  :</span><span class="sxs-lookup"><span data-stu-id="356f9-199">You will notice that the dropdown menu of the event became active, click on the dropdown menu and navigate to **SceneController** and in the sub menu select the **Init ()** option:</span></span>

![Unity avec l’action d’événement DataManager ajoutée](images/mr-learning-azure/tutorial1-section6-step1-3.png)

<span data-ttu-id="356f9-201">Dans la fenêtre Hierarchy, sélectionnez l’objet **SceneController**  ; dans l’inspecteur, vous trouvez le composant **SceneController** (script).</span><span class="sxs-lookup"><span data-stu-id="356f9-201">From the Hierarchy window, select the **SceneController** object, there in the Inspector you will find the **SceneController** (script) component.</span></span>

![Unity avec SceneController sélectionné](images/mr-learning-azure/tutorial1-section6-step1-4.png)

<span data-ttu-id="356f9-203">Vous voyez que plusieurs champs ne sont pas remplis : nous allons changer cela.</span><span class="sxs-lookup"><span data-stu-id="356f9-203">You will see that there are several unpopulated fields, let's change that.</span></span> <span data-ttu-id="356f9-204">Déplacez l’objet **DataManager** depuis la hiérarchie vers le champ *Data Manager* et déplacez le GameObject **RootMenu** depuis la hiérarchie vers le champ *Main Menu*.</span><span class="sxs-lookup"><span data-stu-id="356f9-204">Move the **DataManager** object from the Hierarchy into the *Data Manager* field and move the **RootMenu** GameObject from the Hierarchy into the *Main Menu* field.</span></span>

![Unity avec SceneController configuré](images/mr-learning-azure/tutorial1-section6-step1-5.png)

<span data-ttu-id="356f9-206">Votre scène est maintenant prête pour les tutoriels suivants.</span><span class="sxs-lookup"><span data-stu-id="356f9-206">Now your scene is ready for the upcoming tutorials.</span></span> <span data-ttu-id="356f9-207">N’oubliez pas de l’enregistrer dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="356f9-207">Don't forget to save it into your project.</span></span>

## <a name="prepare-project-build-pipeline"></a><span data-ttu-id="356f9-208">Préparer le pipeline de génération du projet</span><span class="sxs-lookup"><span data-stu-id="356f9-208">Prepare project build pipeline</span></span>

<span data-ttu-id="356f9-209">Alors que le projet doit encore être rempli avec du contenu, vous devez effectuer certaines préparations pour que le projet soit prêt à être généré pour **HoloLens 2**.</span><span class="sxs-lookup"><span data-stu-id="356f9-209">While the project yet has to be filled with content, you have to perform some preparations, so the project is ready for building for **HoloLens 2**.</span></span>

### <a name="1-add-additional-required-capabilities"></a><span data-ttu-id="356f9-210">1. Ajouter des fonctionnalités supplémentaires nécessaires</span><span class="sxs-lookup"><span data-stu-id="356f9-210">1. Add additional required capabilities</span></span>

<span data-ttu-id="356f9-211">Dans le menu Unity, sélectionnez **Modifier** > **Paramètres du projet...** pour ouvrir la fenêtre Paramètres du projet :</span><span class="sxs-lookup"><span data-stu-id="356f9-211">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![Ouverture des paramètres du projet dans Unity](images/mr-learning-azure/tutorial1-section7-step1-1.png)

<span data-ttu-id="356f9-213">Dans la fenêtre Project Settings, sélectionnez **Player** , puis **Publishing Settings**  :</span><span class="sxs-lookup"><span data-stu-id="356f9-213">In the Project Settings window, select **Player** and then **Publishing Settings** :</span></span>

![Paramètres de publication Unity](images/mr-learning-azure/tutorial1-section7-step1-2.png)

<span data-ttu-id="356f9-215">Dans **Publishing Settings** , accédez à la section **Capabilities** et vérifiez bien que les fonctionnalités **InternetClient** , **Microphone** et **SpatialPerception** , que vous avez activées lors de la création du projet au début de ce tutoriel, sont activées.</span><span class="sxs-lookup"><span data-stu-id="356f9-215">In the  **Publishing Settings** , scroll down to the **Capabilities** section and double-check that the **InternetClient** , **Microphone** and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="356f9-216">Activez ensuite les fonctionnalités **InternetClientServer** , **PrivateNetworkClientServer** et **Webcam**  :</span><span class="sxs-lookup"><span data-stu-id="356f9-216">Then, enable the **InternetClientServer** , **PrivateNetworkClientServer** , and **Webcam** capabilities:</span></span>

![Fonctionnalités Unity](images/mr-learning-azure/tutorial1-section7-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="356f9-218">2. Déployer l’application sur votre HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="356f9-218">2. Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="356f9-219">Certaines des fonctionnalités que vous allez utiliser dans cette série de tutoriels ne peuvent pas s’exécuter dans l’éditeur Unity : cela signifie que vous devez être familiarisé avec le déploiement de l’application sur votre appareil HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="356f9-219">Not all features that you will use in this tutorial series can run inside the Unity editor, this means that you need to be familiar with deploying the application to your HoloLens 2 device.</span></span>

> [!TIP]
> <span data-ttu-id="356f9-220">Pour vous rappeler comment générer et déployer votre projet Unity sur HoloLens 2, vous pouvez vous référer aux instructions de [Tutoriels de démarrage - Générer votre application sur votre appareil](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="356f9-220">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Getting started tutorials - Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="356f9-221">3. Exécuter l’application sur votre HoloLens 2 et suivre les instructions dans l’application</span><span class="sxs-lookup"><span data-stu-id="356f9-221">3. Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

> [!CAUTION]
> <span data-ttu-id="356f9-222">Comme tous les services Azure utilisent Internet, vérifiez que votre appareil y est connecté.</span><span class="sxs-lookup"><span data-stu-id="356f9-222">All Azure Services uses the internet, so make sure your device is connected to the internet.</span></span>

<span data-ttu-id="356f9-223">Quand l’application s’exécute sur votre appareil, acceptez l’accès aux fonctionnalités demandées suivantes :</span><span class="sxs-lookup"><span data-stu-id="356f9-223">When the application is running on your device, accept access to the following requested capabilities:</span></span>

* <span data-ttu-id="356f9-224">Microphone</span><span class="sxs-lookup"><span data-stu-id="356f9-224">Microphone</span></span>
* <span data-ttu-id="356f9-225">Appareil photo</span><span class="sxs-lookup"><span data-stu-id="356f9-225">Camera</span></span>

<span data-ttu-id="356f9-226">Ces fonctionnalités sont nécessaires pour que des services comme *Chat Bot* et *Custom Vision* fonctionnent correctement.</span><span class="sxs-lookup"><span data-stu-id="356f9-226">These capabilities are required for services like *Chat Bot* and *Custom Vision* to function properly.</span></span>

## <a name="congratulations"></a><span data-ttu-id="356f9-227">Félicitations</span><span class="sxs-lookup"><span data-stu-id="356f9-227">Congratulations</span></span>

<span data-ttu-id="356f9-228">Dans ce tutoriel, vous avez découvert la série de tutoriels, les fonctionnalités que vous allez implémenter et la façon dont les services **cloud Azure** permettent la réalisation de votre application *HoloLens 2*.</span><span class="sxs-lookup"><span data-stu-id="356f9-228">In this tutorial, you were introduced to the tutorial series, learned about the features you will implement and how **Azure Cloud** services tie in to making your *HoloLens 2* application happen.</span></span> <span data-ttu-id="356f9-229">Vous avez ajouté les composants nécessaires dans le projet et préparé la scène pour cette série de tutoriels.</span><span class="sxs-lookup"><span data-stu-id="356f9-229">You added the required components into the project and prepared the scene for this tutorial series.</span></span>

<span data-ttu-id="356f9-230">Dans la leçon suivante, vous allez utiliser Stockage Azure comme solution de persistance cloud pour stocker des données et des images.</span><span class="sxs-lookup"><span data-stu-id="356f9-230">In the next lesson, you will use Azure storage as a cloud based persistence solution for storing data and images.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="356f9-231">Tutoriel suivant : 2. Intégration de Stockage Azure</span><span class="sxs-lookup"><span data-stu-id="356f9-231">Next tutorial: 2. Integrating Azure storage</span></span>](mr-learning-azure-02.md)
