---
title: Didacticiels audio spatial-1. Ajout de données audio spatiales à votre projet
description: Ajoutez le plug-in Microsoft Spatializer à votre projet Unity pour accéder au déchargement matériel HoloLens 2 HRTF.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: réalité mixte, Unity, tutorial, hololens2, audio spatial, MRTK, boîte à outils de réalité mixte, UWP, Windows 10, HRTF, fonction de transfert liée aux têtes, réverbération, Microsoft Spatializer
ms.openlocfilehash: 1eb2913f1953e334cfe75b786f96bb51a9852fc5
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2021
ms.locfileid: "98578444"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a><span data-ttu-id="96bb6-105">1. Ajout de l’audio spatial à votre projet Unity</span><span class="sxs-lookup"><span data-stu-id="96bb6-105">1. Adding Spatial audio to your Unity project</span></span>

## <a name="overview"></a><span data-ttu-id="96bb6-106">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="96bb6-106">Overview</span></span>

<span data-ttu-id="96bb6-107">Bienvenue dans le didacticiel sur l’audio spatial pour Unity sur HoloLens2.</span><span class="sxs-lookup"><span data-stu-id="96bb6-107">Welcome to the spatial audio tutorial for Unity on HoloLens2.</span></span> <span data-ttu-id="96bb6-108">Grâce à cette série de didacticiels, vous allez apprendre à utiliser le déchargement de la fonction de transfert HRTF (en anglais) sur HoloLens 2 et à activer la réaction lors de l’utilisation du déchargement HRTF.</span><span class="sxs-lookup"><span data-stu-id="96bb6-108">Through this tutorial series, you will learn how to use head-related transfer function (HRTF) offload on HoloLens 2 and How to enable reverb when using HRTF offload.</span></span>

<span data-ttu-id="96bb6-109">Le [dépôt github Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity) a un projet Unity terminé de cette séquence de didacticiels.</span><span class="sxs-lookup"><span data-stu-id="96bb6-109">The [Microsoft Spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity) has a completed Unity project of this tutorial sequence.</span></span>

<span data-ttu-id="96bb6-110">Pour comprendre ce que signifie l’aménagement des sons à l’aide des technologies Spatialization basées sur HRTF et des recommandations sur le moment où elles peuvent être utiles, consultez [conception spatiale du son](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span><span class="sxs-lookup"><span data-stu-id="96bb6-110">For an understanding of what it means to spatialize sounds using HRTF-based spatialization technologies and recommendations for when it can be helpful, see [spatial sound design](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span></span>

## <a name="what-is-hrtf-offload"></a><span data-ttu-id="96bb6-111">Qu’est-ce que le déchargement HRTF ?</span><span class="sxs-lookup"><span data-stu-id="96bb6-111">What is HRTF offload?</span></span>

<span data-ttu-id="96bb6-112">Le traitement de l’audio à l’aide d’algorithmes basés sur HRTF nécessite une grande quantité de calcul spécialisé.</span><span class="sxs-lookup"><span data-stu-id="96bb6-112">Processing audio using HRTF-based algorithms requires a large amount of specialized computation.</span></span> <span data-ttu-id="96bb6-113">HoloLens 2 comprend un matériel dédié qui peut être utilisé pour éviter la charge du processeur d’application, ce qui « décharge » le traitement des algorithmes basés sur HRTF.</span><span class="sxs-lookup"><span data-stu-id="96bb6-113">HoloLens 2 includes dedicated hardware that can be utilized to avoid burdening the application processor, thus "offloading" the processing of HRTF-based algorithms.</span></span>  <span data-ttu-id="96bb6-114">Le plug-in Microsoft Spatializer offre un moyen simple pour votre application de tirer parti du matériel HRTF dédié afin que votre application puisse utiliser davantage de processeurs d’applications pour les opérations autres que l’audio spatial.</span><span class="sxs-lookup"><span data-stu-id="96bb6-114">The Microsoft spatializer plugin provides an easy way for your application to take advantage of the dedicated HRTF hardware so your application can use more of the application processor for operations other than spatial audio.</span></span>

## <a name="objectives"></a><span data-ttu-id="96bb6-115">Objectifs</span><span class="sxs-lookup"><span data-stu-id="96bb6-115">Objectives</span></span>

* <span data-ttu-id="96bb6-116">Importation et activation du plug-in Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="96bb6-116">Importing and Enabling Microsoft spatializer plugin</span></span>
* <span data-ttu-id="96bb6-117">Activation de l’audio spatial sur votre station de travail de développeur</span><span class="sxs-lookup"><span data-stu-id="96bb6-117">Enabling Spatial audio on your developer workstation</span></span>

## <a name="prerequisites"></a><span data-ttu-id="96bb6-118">Prérequis</span><span class="sxs-lookup"><span data-stu-id="96bb6-118">Prerequisites</span></span>

* <span data-ttu-id="96bb6-119">PC Windows 10 configuré avec les [outils appropriés installés](../../install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="96bb6-119">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="96bb6-120">Connaissances de base de la programmation en C++</span><span class="sxs-lookup"><span data-stu-id="96bb6-120">Basic c# programming knowledge</span></span>
* <span data-ttu-id="96bb6-121">Appareil HoloLens 2 [configuré pour le développement](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="96bb6-121">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="96bb6-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> avec Unity 2019 LTS monté et le module Universal Windows Platform Build Support ajouté</span><span class="sxs-lookup"><span data-stu-id="96bb6-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS mounted, and the Universal Windows Platform Build Support module added</span></span>

<span data-ttu-id="96bb6-123">Nous **vous recommandons vivement** de suivre la série des didacticiels de [prise](mr-learning-base-01.md) en main ou de bénéficier d’une expérience de base avec Unity et MRTK avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="96bb6-123">We **strongly recommend** completing the [Getting started](mr-learning-base-01.md) tutorials series or having some basic prior experience with Unity and MRTK before continuing.</span></span>

> [!IMPORTANT]
>
> * <span data-ttu-id="96bb6-124">La version d’Unity recommandée pour cette série de tutoriels est Unity 2019 LTS.</span><span class="sxs-lookup"><span data-stu-id="96bb6-124">The recommended Unity version for this tutorial series is Unity 2019 LTS.</span></span> <span data-ttu-id="96bb6-125">Elle remplace toutes les versions Unity requises ou recommandées qui sont indiquées dans les prérequis ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="96bb6-125">It supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="96bb6-126">Création et préparation du projet Unity</span><span class="sxs-lookup"><span data-stu-id="96bb6-126">Creating and preparing the Unity project</span></span>

<span data-ttu-id="96bb6-127">Dans cette section, vous allez créer un projet Unity et le préparer au développement avec MRTK.</span><span class="sxs-lookup"><span data-stu-id="96bb6-127">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="96bb6-128">Pour cela, suivez d’abord [Initialisation de votre projet et de votre première application](mr-learning-base-02.md), en excluant les instructions données dans [Générer votre application sur votre appareil](mr-learning-base-02.md#building-your-application-to-your-hololens-2), ce qui inclut les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="96bb6-128">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="96bb6-129">[Création du projet Unity](mr-learning-base-02.md#creating-the-unity-project) et affectation d’un nom pertinent, par exemple *MRTK Tutorials*</span><span class="sxs-lookup"><span data-stu-id="96bb6-129">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

1. [<span data-ttu-id="96bb6-130">Changement de plateforme de génération</span><span class="sxs-lookup"><span data-stu-id="96bb6-130">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. [<span data-ttu-id="96bb6-131">Importation des ressources TextMeshPro Essential</span><span class="sxs-lookup"><span data-stu-id="96bb6-131">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [<span data-ttu-id="96bb6-132">Importation du Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="96bb6-132">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)

1. [<span data-ttu-id="96bb6-133">Configuration du projet Unity</span><span class="sxs-lookup"><span data-stu-id="96bb6-133">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. <span data-ttu-id="96bb6-134">[Création et définition de la scène](mr-learning-base-02.md#creating-and-configuring-the-scene) et attribution d’un nom approprié à la scène, par exemple, *SpatialAudio*</span><span class="sxs-lookup"><span data-stu-id="96bb6-134">[Creating and setting the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *SpatialAudio*</span></span>

<span data-ttu-id="96bb6-135">Suivez ensuite les instructions relatives à la modification des options d’affichage de la [sensibilisation spatiale](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) pour vous assurer que le profil de configuration MRTK pour votre scène est **DefaultXRSDKConfigurationProfile** et modifiez les options d’affichage du maillage de la sensibilisation spatiale à **occlusion**.</span><span class="sxs-lookup"><span data-stu-id="96bb6-135">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to ensure the MRTK configuration profile for your scene is **DefaultXRSDKConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="adding-microsoft-spatializer-to-the-project"></a><span data-ttu-id="96bb6-136">Ajout de Microsoft Spatializer au projet</span><span class="sxs-lookup"><span data-stu-id="96bb6-136">Adding Microsoft Spatializer to the Project</span></span>

<span data-ttu-id="96bb6-137">Téléchargez et importez Microsoft Spatializer  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft. SpatialAudio. Spatializer. Unity. 1.0.18. pour Unity </a></span><span class="sxs-lookup"><span data-stu-id="96bb6-137">Download and import the Microsoft Spatializer  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage </a></span></span>

>[!TIP]
> <span data-ttu-id="96bb6-138">Pour un rappel de la façon d’importer un package personnalisé Unity, vous pouvez vous référer aux instructions de [Importer le Kit de ressources de réalité mixte](../../../mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="96bb6-138">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](../../../mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="enable-the-microsoft-spatializer-plugin"></a><span data-ttu-id="96bb6-139">Activer le plug-in Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="96bb6-139">Enable the Microsoft Spatializer plugin</span></span>

<span data-ttu-id="96bb6-140">Après l’importation de **Microsoft Spatializer** , vous devez l’activer.</span><span class="sxs-lookup"><span data-stu-id="96bb6-140">After importing the **Microsoft Spatializer** you need to enable it.</span></span> <span data-ttu-id="96bb6-141">Ouvrez les **paramètres de projet Edit->-> audio**, puis remplacez le **plug-in Spatializer** par "Microsoft Spatializer".</span><span class="sxs-lookup"><span data-stu-id="96bb6-141">Open **Edit -> Project Settings -> Audio**, and change **Spatializer Plugin** to "Microsoft Spatializer".</span></span>

![Paramètres du projet présentant le plug-in Spatializer](images/spatial-audio/spatial-audio-01-section3-step1-1.png)

## <a name="enable-spatial-audio-on-your-workstation"></a><span data-ttu-id="96bb6-143">Activer l’audio spatial sur votre station de travail</span><span class="sxs-lookup"><span data-stu-id="96bb6-143">Enable spatial audio on your workstation</span></span>

<span data-ttu-id="96bb6-144">Sur les versions de bureau de Windows, l’audio spatial est désactivé par défaut.</span><span class="sxs-lookup"><span data-stu-id="96bb6-144">On desktop versions of Windows, spatial audio is disabled by default.</span></span> <span data-ttu-id="96bb6-145">Pour l’activer, cliquez avec le bouton droit sur l’icône de volume dans la barre des tâches.</span><span class="sxs-lookup"><span data-stu-id="96bb6-145">Enable it by right-clicking on the volume icon in the task bar.</span></span> <span data-ttu-id="96bb6-146">Pour obtenir la meilleure représentation de ce que vous entendez sur HoloLens 2, choisissez **son Spatial > Windows Sonic pour casque**.</span><span class="sxs-lookup"><span data-stu-id="96bb6-146">To get the best representation of what you'll hear on HoloLens 2, choose **Spatial sound -> Windows Sonic for Headphones**.</span></span>

![Paramètres audio spatiaux du Bureau](images/spatial-audio/spatial-audio-01-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="96bb6-148">Ce paramètre est requis uniquement si vous envisagez de tester votre projet dans l’éditeur Unity.</span><span class="sxs-lookup"><span data-stu-id="96bb6-148">This setting is only required if you plan to test your project in the Unity editor.</span></span>

## <a name="congratulations"></a><span data-ttu-id="96bb6-149">Félicitations</span><span class="sxs-lookup"><span data-stu-id="96bb6-149">Congratulations</span></span>

<span data-ttu-id="96bb6-150">Dans ce didacticiel, vous avez appris à importer et à activer le plug-in Microsoft Spatializer et à activer le son spatial sur votre station de travail.</span><span class="sxs-lookup"><span data-stu-id="96bb6-150">In this tutorial you have learnt how to Import and enable the Microsoft Spatializer plugin and also to enable the spatial audio on your workstation.</span></span>
<span data-ttu-id="96bb6-151">Dans le didacticiel suivant, vous allez apprendre à ajouter de l’audio spatial dans le projet Unity.</span><span class="sxs-lookup"><span data-stu-id="96bb6-151">In the next tutorial you will learn how to add spatial audio in the unity project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="96bb6-152">Didacticiel suivant : 2. sons d’interaction du bouton spatial</span><span class="sxs-lookup"><span data-stu-id="96bb6-152">Next Tutorial: 2. Spatializing button interaction sounds</span></span>](unity-spatial-audio-ch2.md)
