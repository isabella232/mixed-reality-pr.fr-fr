---
title: Initialisation de votre projet et déploiement de votre première application
description: Ce cours vous montre comment configurer votre projet Unity pour le MRTK (Mixed Reality Toolkit) et comment le déployer sur votre HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, MRTK, mixed reality toolkit, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: 7124650a59271b48b763719063411765b5457768
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176023"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="2039c-104">2. Initialisation de votre projet et déploiement de votre première application</span><span class="sxs-lookup"><span data-stu-id="2039c-104">2. Initializing your project and deploying your first application</span></span>

<span data-ttu-id="2039c-105">Dans ce tutoriel, vous allez apprendre à créer un nouveau projet Unity, à le configurer pour le développement MRTK (Mixed Reality Toolkit) et à importer MRTK.</span><span class="sxs-lookup"><span data-stu-id="2039c-105">In this tutorial, you'll learn how to create a new Unity project, configure it for Mixed Reality Toolkit (MRTK) development, and import MRTK.</span></span> <span data-ttu-id="2039c-106">Vous allez également effectuer la configuration, la génération et le déploiement d’une scène Unity de base depuis Visual Studio sur votre HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="2039c-106">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="2039c-107">Une fois que l’avez déployée sur votre HoloLens 2, vous devez voir un maillage de mappage spatial couvrant les surfaces qui sont perçues par HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2039c-107">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="2039c-108">En outre, vous devez voir des indicateurs sur vos mains et doigts pour le suivi de la main et un compteur de fréquence d’images pour vous tenir informé des performances de l’application.</span><span class="sxs-lookup"><span data-stu-id="2039c-108">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

## <a name="objectives"></a><span data-ttu-id="2039c-109">Objectifs</span><span class="sxs-lookup"><span data-stu-id="2039c-109">Objectives</span></span>

* <span data-ttu-id="2039c-110">Apprendre à configurer Unity pour le développement HoloLens</span><span class="sxs-lookup"><span data-stu-id="2039c-110">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="2039c-111">Apprendre à créer et déployer votre application sur HoloLens</span><span class="sxs-lookup"><span data-stu-id="2039c-111">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="2039c-112">Expérimenter le maillage du mappage spatial, les maillages de la main et le compteur de fréquence d’images sur un appareil HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="2039c-112">Experience the spatial mapping mesh, hand meshes, and the framerate counter on HoloLens 2 device</span></span>

### <a name="steps-overview"></a><span data-ttu-id="2039c-113">Vue d’ensemble des étapes</span><span class="sxs-lookup"><span data-stu-id="2039c-113">Steps overview</span></span>
:::row:::
    :::column:::
       <span data-ttu-id="2039c-114">![Étape 1 de la vue d’ensemble](images/mr-learning-base/base-02-overview-step1.png) **1. Créer un nouveau projet Unity**</span><span class="sxs-lookup"><span data-stu-id="2039c-114">![Overview Step 1](images/mr-learning-base/base-02-overview-step1.png) **1. Create a new Unity project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="2039c-115">![Étape 2 de la vue d’ensemble](images/mr-learning-base/base-02-overview-step2.png) **2. Importer MRTK dans le projet**</span><span class="sxs-lookup"><span data-stu-id="2039c-115">![Overview Step 2](images/mr-learning-base/base-02-overview-step2.png) **2. Import MRTK into the project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="2039c-116">![Étape 3 de la vue d’ensemble](images/mr-learning-base/base-02-overview-step3.png) **3. Configurer une nouvelle scène avec MRTK**</span><span class="sxs-lookup"><span data-stu-id="2039c-116">![Overview Step 3](images/mr-learning-base/base-02-overview-step3.png) **3. Configure a new scene with MRTK**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
       <span data-ttu-id="2039c-117">![Étape 4 de la vue d’ensemble](images/mr-learning-base/base-02-overview-step4.png) **4. Créer un projet Unity**</span><span class="sxs-lookup"><span data-stu-id="2039c-117">![Overview Step 4](images/mr-learning-base/base-02-overview-step4.png) **4. Build Unity Project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="2039c-118">![Étape 5 de la vue d’ensemble](images/mr-learning-base/base-02-overview-step5.png) **5. Créer un projet UWP**</span><span class="sxs-lookup"><span data-stu-id="2039c-118">![Overview Step 5](images/mr-learning-base/base-02-overview-step5.png) **5. Build UWP Project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="2039c-119">![Étape 6 de la vue d’ensemble](images/mr-learning-base/base-02-overview-step6.png) **6. Exécuter un project sur l’appareil**</span><span class="sxs-lookup"><span data-stu-id="2039c-119">![Overview Step 6](images/mr-learning-base/base-02-overview-step6.png) **6. Run Project on the Device**</span></span>
    :::column-end:::
:::row-end:::

## <a name="creating-the-unity-project"></a><span data-ttu-id="2039c-120">Création du projet Unity</span><span class="sxs-lookup"><span data-stu-id="2039c-120">Creating the Unity project</span></span>

<span data-ttu-id="2039c-121">Lancez **Unity Hub**, sélectionnez l’onglet **Projets**, puis cliquez sur la **flèche bas** en regard du bouton **Nouveau** :</span><span class="sxs-lookup"><span data-stu-id="2039c-121">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-1.png" width="650px" alt="Unity Hub with New button highlighted">

<span data-ttu-id="2039c-122">Dans la liste déroulante, sélectionnez la **version** Unity spécifiée dans les [prérequis](mr-learning-base-01.md#prerequisites) :</span><span class="sxs-lookup"><span data-stu-id="2039c-122">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-2.png" width="650px" alt="Unity Hub with NEW version selector dropdown">


> [!TIP]
> <span data-ttu-id="2039c-123">Si cette version spécifique d’Unity n’est pas disponible dans Unity Hub, vous pouvez lancer l’installation à partir de la page <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Unity download archive</a>.</span><span class="sxs-lookup"><span data-stu-id="2039c-123">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="2039c-124">Dans la fenêtre Créer un projet :</span><span class="sxs-lookup"><span data-stu-id="2039c-124">In the Create a new project window:</span></span>

* <span data-ttu-id="2039c-125">Vérifiez que **Modèles** est défini sur **3D**</span><span class="sxs-lookup"><span data-stu-id="2039c-125">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="2039c-126">Entrez un **Nom du projet** approprié, par exemple _Tutoriels MRTK_</span><span class="sxs-lookup"><span data-stu-id="2039c-126">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="2039c-127">Choisissez un **Emplacement** approprié pour stocker votre projet, par exemple _D:\MixedRealityLearning_</span><span class="sxs-lookup"><span data-stu-id="2039c-127">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="2039c-128">Cliquez sur le bouton **Créer** pour créer et lancer votre nouveau projet Unity</span><span class="sxs-lookup"><span data-stu-id="2039c-128">Click the **Create** button to create and launch your new Unity project</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-3.png" width="650px" alt="Unity Hub with Create a new project window filled out">

> [!CAUTION]
> <span data-ttu-id="2039c-129">Quand vous utilisez Windows, il existe une limite de 255 caractères pour MAX_PATH.</span><span class="sxs-lookup"><span data-stu-id="2039c-129">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="2039c-130">Par conséquent, vous devez enregistrer le projet Unity près de la racine du lecteur.</span><span class="sxs-lookup"><span data-stu-id="2039c-130">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="2039c-131">Attendez qu’Unity crée le projet :</span><span class="sxs-lookup"><span data-stu-id="2039c-131">Wait for Unity to create the project:</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-4.png" width="650px" alt="Unity create new project in progress">

## <a name="switching-the-build-platform"></a><span data-ttu-id="2039c-132">Changement de plateforme de génération</span><span class="sxs-lookup"><span data-stu-id="2039c-132">Switching the build platform</span></span>

<span data-ttu-id="2039c-133">Dans le menu Unity, sélectionnez **Fichier** > **Paramètres de build...** pour ouvrir la fenêtre Paramètres de build :</span><span class="sxs-lookup"><span data-stu-id="2039c-133">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Unity - Build Settings... Chemin du menu](images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="2039c-135">Dans la fenêtre Build Settings, sélectionnez **Universal Windows Platform**, puis :</span><span class="sxs-lookup"><span data-stu-id="2039c-135">In the Build Settings window, select **Universal Windows Platform** and:</span></span>

1. <span data-ttu-id="2039c-136">Définissez **Target device** sur **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="2039c-136">Set **Target device** to **HoloLens**</span></span>
2. <span data-ttu-id="2039c-137">Définissez **Architecture** sur **ARM 64**.</span><span class="sxs-lookup"><span data-stu-id="2039c-137">Set **Architecture** to **ARM 64**</span></span> 
3. <span data-ttu-id="2039c-138">Définissez **Build Type** sur **D3D Project**.</span><span class="sxs-lookup"><span data-stu-id="2039c-138">Set **Build Type** to **D3D Project**</span></span>
4. <span data-ttu-id="2039c-139">Définissez **Target SDK Version** sur **Latest Installed**</span><span class="sxs-lookup"><span data-stu-id="2039c-139">Set **Target SDK Version** to **Latest Installed**</span></span>
5. <span data-ttu-id="2039c-140">Définissez **Minimum Platform Version** sur **10.0.1024.0**</span><span class="sxs-lookup"><span data-stu-id="2039c-140">Set **Minimum Platform Version** to **10.0.1024.0**</span></span>
6. <span data-ttu-id="2039c-141">Définissez **Visual Studio Version** sur **Latest Installed**</span><span class="sxs-lookup"><span data-stu-id="2039c-141">Set **Visual Studio Version** to **Latest installed**</span></span>
7. <span data-ttu-id="2039c-142">Définissez **Build and Run on** sur **USB Device**</span><span class="sxs-lookup"><span data-stu-id="2039c-142">Set **Build and Run on** to **USB Device**</span></span>
8. <span data-ttu-id="2039c-143">Définissez **Build configuration** sur **Release** en raison de problèmes de performances connus avec Debug.</span><span class="sxs-lookup"><span data-stu-id="2039c-143">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>
9. <span data-ttu-id="2039c-144">Appuyer sur le bouton Switch Platform</span><span class="sxs-lookup"><span data-stu-id="2039c-144">Click the Switch Platform button</span></span>

![Paramètres de build Unity avec les paramètres Universal Windows Platform définis](images/mr-learning-base/base-02-section2-step1-2-openxr.png)

<span data-ttu-id="2039c-146">Attendez qu’Unity termine le changement de plateforme :</span><span class="sxs-lookup"><span data-stu-id="2039c-146">Wait for Unity to finish switching the platform:</span></span>

![Unity - Changement de plateforme en cours](images/mr-learning-base/base-02-section2-step1-3-openxr.png)

<span data-ttu-id="2039c-148">Une fois qu’Unity a terminé le changement de plateforme, cliquez sur l’icône **x** pour fermer la fenêtre Paramètres de génération.</span><span class="sxs-lookup"><span data-stu-id="2039c-148">When Unity has finished switching the platform, click the  **x** icon to close the Build Settings window.</span></span>

## <a name="importing-the-mixed-reality-toolkit-and-configuring-the-unity-project"></a><span data-ttu-id="2039c-149">Importation de Mixed Reality Toolkit et configuration du projet Unity</span><span class="sxs-lookup"><span data-stu-id="2039c-149">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>

<span data-ttu-id="2039c-150">Pour importer le Mixed Reality Toolkit dans le projet Unity, vous devez utiliser [Mixed Reality Feature Tool](../welcome-to-mr-feature-tool.md) qui permet aux développeurs de découvrir, mettre à jour et ajouter des packages de fonctionnalités Mixed Reality dans des projets Unity.</span><span class="sxs-lookup"><span data-stu-id="2039c-150">To Import Mixed Reality Toolkit into the Unity Project you will have to use [Mixed Reality Feature Tool](../welcome-to-mr-feature-tool.md) which allows  developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="2039c-151">Vous pouvez rechercher des packages par nom ou par catégorie, voir leurs dépendances et même voir les changements proposés pour votre fichier manifeste de projets avant l’importation.</span><span class="sxs-lookup"><span data-stu-id="2039c-151">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span>

<span data-ttu-id="2039c-152">Téléchargez la dernière version du Mixed Reality Feature Tool dans le [Centre de téléchargement Microsoft](https://aka.ms/MRFeatureTool). Une fois le téléchargement terminé, décompressez le fichier et enregistrez-le sur votre Bureau.</span><span class="sxs-lookup"><span data-stu-id="2039c-152">Download the latest version of the Mixed Reality Feature Tool from the [Microsoft Download Center](https://aka.ms/MRFeatureTool), When the download is complete, unzip the file and save it to your desktop.</span></span>

> [!NOTE]
> <span data-ttu-id="2039c-153">Avant de pouvoir exécuter le Mixed Reality Feature Tool, vous devez installer le [runtime .NET 5.0](https://dotnet.microsoft.com/download/dotnet/thank-you/runtime-desktop-5.0.7-windows-x64-installer).</span><span class="sxs-lookup"><span data-stu-id="2039c-153">Before you can run the Mixed Reality Feature Tool please install [.NET 5.0 runtime](https://dotnet.microsoft.com/download/dotnet/thank-you/runtime-desktop-5.0.7-windows-x64-installer)</span></span>

<span data-ttu-id="2039c-154">Ouvrez le fichier exécutable **MixedRealityFeatureTool** dans le dossier téléchargé pour lancer le Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="2039c-154">Open the executable file **MixedRealityFeatureTool** from the downloaded folder to launch the Mixed Reality Feature Tool.</span></span>  


<img src="images/mr-learning-base/base-02-section4-step1-1.png" width="750px" alt="Opening MixedRealityFeatureTool">

[!INCLUDE[](includes/importing-mrtk.md)]

## <a name="creating-the-scene-and-configuring-mrtk"></a><span data-ttu-id="2039c-155">Création de la scène et configuration de MRTK</span><span class="sxs-lookup"><span data-stu-id="2039c-155">Creating the scene and configuring MRTK</span></span>

<span data-ttu-id="2039c-156">Dans le menu Unity, sélectionnez **Fichier** > **Nouvelle scène** :</span><span class="sxs-lookup"><span data-stu-id="2039c-156">In the Unity menu, select **File** > **New Scene**:</span></span>

![Unity - New Scene - Chemin du menu](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="2039c-158">Dans la fenêtre **Nouvelle scène**, sélectionnez **De base (intégré)** , puis cliquez sur **Créer** pour créer une scène :</span><span class="sxs-lookup"><span data-stu-id="2039c-158">In the **New Scene** window select **Basic (Built-in)** and click on **create** to create a new scene:</span></span>

![Nouvelle fenêtre de scène Unity](images/mr-learning-base/base-02-section6-step1-1-newscene.png)

> [!NOTE]
> <span data-ttu-id="2039c-160">La capture d’écran ci-dessus provient de Unity version 2020, si vous utilisez Unity 2019, lorsque vous cliquez sur **Créer**, une nouvelle scène vide sera créée.</span><span class="sxs-lookup"><span data-stu-id="2039c-160">Above screenshot is from Unity Version 2020, if you are using Unity 2019 when you click on **create** a new empty scene will be created.</span></span>

<span data-ttu-id="2039c-161">Dans le menu Unity, sélectionnez **Mixed Reality** > **Kit de ressources** > **Ajouter à la scène et configurer...** pour ajouter le MRTK à votre scène actuelle :</span><span class="sxs-lookup"><span data-stu-id="2039c-161">In the Unity menu, select **Mixed Reality** > **Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![Unity - Add to Scene and Configure... Chemin du menu](images/mr-learning-base/base-02-section6-step1-2.png)

<span data-ttu-id="2039c-163">Une fois l’objet **MixedRealityToolkit** sélectionné dans la fenêtre Hierarchy, dans la fenêtre Inspector, vérifiez que le profil de configuration **MixedRealityToolkit** est défini sur **DefaultMixedRealityToolkitConfigurationProfile** :</span><span class="sxs-lookup"><span data-stu-id="2039c-163">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, verify that the **MixedRealityToolkit** configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![Composant MixedRealityToolkit d’Unity avec DefaultMixedRealityTookitConfigurationProfile sélectionné](images/mr-learning-base/base-02-section6-step1-3.png)

<span data-ttu-id="2039c-165">Dans le menu Unity, sélectionnez **Fichier** > **Enregistrer sous...** pour ouvrir la fenêtre Save Scene (Enregistrer la scène) :</span><span class="sxs-lookup"><span data-stu-id="2039c-165">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![Unity - Save As... Chemin du menu](images/mr-learning-base/base-02-section6-step1-4.png)

<span data-ttu-id="2039c-167">Enregistrez la scène dans votre projet sous **Ressource** > **Scènes**.</span><span class="sxs-lookup"><span data-stu-id="2039c-167">Save the scene in you project under **Asset** > **Scenes**.</span></span>

![Fenêtre d’invite Save d’Unity pour enregistrer la scène](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="adding-hand-interaction-to-an-object"></a><span data-ttu-id="2039c-169">Ajout d’une interaction manuelle à un objet</span><span class="sxs-lookup"><span data-stu-id="2039c-169">Adding hand interaction to an object</span></span>

<span data-ttu-id="2039c-170">Dans le menu Unity, sélectionnez **GameObject** > **Objet 3D** > **Cube** pour ajouter un objet Cube à la scène.</span><span class="sxs-lookup"><span data-stu-id="2039c-170">In the Unity menu, select **GameObject** > **3D Object** > **Cube** to add a cube object to the scene.</span></span>

![Ajout d’un cube à la scène](images/mr-learning-base/base-02-section8-step1-1.png)

<span data-ttu-id="2039c-172">Cliquez sur l’objet **Cube** dans la fenêtre Hiérarchie, puis, dans la fenêtre de l’inspecteur, configurez son composant **Transform** comme suit</span><span class="sxs-lookup"><span data-stu-id="2039c-172">Click the **Cube** object in the Hierarchy window, then in the Inspector window configure its **Transform** component as follows</span></span>

* <span data-ttu-id="2039c-173">**Position** : X = 0, Y = 0,1, Z = 0,5</span><span class="sxs-lookup"><span data-stu-id="2039c-173">**Position**: X = 0, Y = -0.1, Z = 0.5</span></span>
* <span data-ttu-id="2039c-174">**Rotation** : X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="2039c-174">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="2039c-175">**Échelle** : X = 0,1, Y = 0,1, Z = 0,1</span><span class="sxs-lookup"><span data-stu-id="2039c-175">**Scale**: X = 0.1, Y = 0.1, Z = 0.1</span></span>

<span data-ttu-id="2039c-176">1 unité Unity équivaut à 1 mètre.</span><span class="sxs-lookup"><span data-stu-id="2039c-176">1 Unity unit is 1 meter.</span></span> <span data-ttu-id="2039c-177">Nous avons mis à jour la taille du cube pour qu’il fasse 10x10x10 cm, placé à 50 cm depuis la position du casque (0,0,0).</span><span class="sxs-lookup"><span data-stu-id="2039c-177">We have updated cube's size to 10x10x10 cm, placed at 50cm from the headset position (0,0,0).</span></span> <span data-ttu-id="2039c-178">10cm sous le niveau de l’œil pour une interaction confortable.</span><span class="sxs-lookup"><span data-stu-id="2039c-178">10cm below the eye level for comfortable interaction.</span></span> 

<span data-ttu-id="2039c-179">Si vous utilisez l’échelle par défaut (1,1,1), le cube est trop volumineux.</span><span class="sxs-lookup"><span data-stu-id="2039c-179">If you use the default scale (1,1,1), the cube will be too big.</span></span> <span data-ttu-id="2039c-180">Si vous utilisez la position par défaut (0,0,0), le cube est placé à la même position que votre casque et vous ne pouvez pas le voir tant que vous n’avez pas effectué un déplacement vers l’arrière.</span><span class="sxs-lookup"><span data-stu-id="2039c-180">If you use the default position (0,0,0), the cube will be placed at the same position as your headset and you won't be able to see it until you move backward.</span></span>

![Ajustement des informations de transformation](images/mr-learning-base/base-02-section8-step1-1b.png)

<span data-ttu-id="2039c-182">Pour vous concentrer sur les objets de la scène, vous pouvez double-cliquer sur l’objet **Cube**, puis faire un léger zoom avant.</span><span class="sxs-lookup"><span data-stu-id="2039c-182">To focus in on the objects in the scene, you can double-click on the **Cube** object, and then zoom slightly in again.</span></span> <span data-ttu-id="2039c-183">Vous pouvez utiliser la touche F pour effectuer un zoom et vous focaliser sur l’objet.</span><span class="sxs-lookup"><span data-stu-id="2039c-183">Or you can use F key to zoom and focus on the object.</span></span>

<span data-ttu-id="2039c-184">Pour interagir avec un objet et le saisir avec des mouvements captés des mains, l’objet doit comporter :</span><span class="sxs-lookup"><span data-stu-id="2039c-184">To interact and grab an object with tracked hands, the object must have:</span></span>
 * <span data-ttu-id="2039c-185">Composant Collider, tel que **Box Collider** (le cube de Unity a déjà un type de Collider par défaut)</span><span class="sxs-lookup"><span data-stu-id="2039c-185">Collider component such as **Box Collider** (Unity's cube already has a Box Collider by default)</span></span>
 * <span data-ttu-id="2039c-186">Le composant **Object Manipulator (Script)**</span><span class="sxs-lookup"><span data-stu-id="2039c-186">**Object Manipulator (Script)** component</span></span>
 * <span data-ttu-id="2039c-187">Composant **NearInteractionGrabbable(Script)**</span><span class="sxs-lookup"><span data-stu-id="2039c-187">**NearInteractionGrabbable(Script)** component</span></span>

<span data-ttu-id="2039c-188">Le script **ObjectManipulator** de MRTK permet de déplacer, de modifier et de faire pivoter un objet à l’aide d’une ou deux mains.</span><span class="sxs-lookup"><span data-stu-id="2039c-188">MRTK's **ObjectManipulator** script makes an object movable, scalable, and rotatable using one or two hands.</span></span> <span data-ttu-id="2039c-189">Ce script prend en charge le modèle d’entrée de manipulation directe, car il permet à l’utilisateur de toucher des hologrammes directement avec ses mains.</span><span class="sxs-lookup"><span data-stu-id="2039c-189">This script supports the direct manipulation input model as the script enables the user to touch holograms directly with their hands.</span></span>

<span data-ttu-id="2039c-190">Toujours avec le **cube** sélectionné dans la fenêtre Hierarchy, dans la fenêtre Inspector, cliquez sur le bouton **Add Component**, puis recherchez et sélectionnez le script **Object Manipulator** pour ajouter le script Object Manipulator à l’objet Cube.</span><span class="sxs-lookup"><span data-stu-id="2039c-190">With the **Cube** still selected in the Hierarchy window, in the Inspector window ,click on **Add Component** button, then search and select **Object Manipulator** script to add the Object Manipulator script to the cube object.</span></span>

![Ajout d’un manipulateur d’objet au cube](images/mr-learning-base/base-02-section8-step1-2.PNG)

<span data-ttu-id="2039c-192">Répétez la même procédure pour ajouter un **script Near Interaction Grabbable** au cube.</span><span class="sxs-lookup"><span data-stu-id="2039c-192">Repeat the same to add **Near Interaction Grabbable script** to the cube</span></span>

![Ajout d’un script Near Interaction Grabbable au cube](images/mr-learning-base/base-02-section8-step1-3.PNG)

> [!NOTE]
> <span data-ttu-id="2039c-194">Quand vous ajoutez un Object Manipulator (Script), dans ce cas, le Constraint Manager (Script) est ajouté automatiquement, car Object Manipulator (Script) en dépend.</span><span class="sxs-lookup"><span data-stu-id="2039c-194">When you add a Object Manipulator (Script), in this case, the Constraint Manager (Script) is automatically added because Object Manipulator (Script) depends on it.</span></span>

## <a name="testing-your-application-in-unity-editor-with-mrtk-input-simulation"></a><span data-ttu-id="2039c-195">Test de votre application dans l’éditeur Unity avec la simulation d’entrée MRTK</span><span class="sxs-lookup"><span data-stu-id="2039c-195">Testing your application in Unity editor with MRTK input simulation</span></span>

<span data-ttu-id="2039c-196">Avec la simulation d’entrée de MRTK, vous pouvez tester divers types d’interactions dans l’éditeur Unity sans développement ni déploiement sur un appareil.</span><span class="sxs-lookup"><span data-stu-id="2039c-196">With MRTK's input simulation, you can test various types of interactions in the Unity editor without building and deploying to a device.</span></span> <span data-ttu-id="2039c-197">Cela vous permet d’itérer rapidement vos idées dans le processus de conception et de développement.</span><span class="sxs-lookup"><span data-stu-id="2039c-197">This allows you quickly iterate your ideas in the design and development process.</span></span> <span data-ttu-id="2039c-198">Utilisez les raccourcis clavier et souris pour contrôler les entrées simulées.</span><span class="sxs-lookup"><span data-stu-id="2039c-198">Use keyboard and mouse combinations to control simulated inputs.</span></span>

<span data-ttu-id="2039c-199">Cliquez sur le bouton de lecture pour accéder au mode de lecture.</span><span class="sxs-lookup"><span data-stu-id="2039c-199">Click the play button and enter the play mode.</span></span> <span data-ttu-id="2039c-200">Maintenez la touche **Décalage vers la gauche** ou **Espace** pour faire apparaître le contrôleur (mains simulées), le déplacement de la souris déplace le contrôleur et peut également être déplacé plus ou moins près de la caméra à l’aide de la roulette de la souris.</span><span class="sxs-lookup"><span data-stu-id="2039c-200">Hold the **Left Shift** or **Space** key to bring up the controller (simulated hands), Mouse movement will move the controller and also it can be moved further or closer to the camera using the mouse wheel.</span></span> <span data-ttu-id="2039c-201">Une fois que le pointeur se trouve sur le cube, appuyez de façon prolongée sur le **bouton gauche de la souris** pour saisir l’objet Cube.</span><span class="sxs-lookup"><span data-stu-id="2039c-201">Once the pointer is on the Cube press and hold **Left Mouse Button** to grab the Cube object.</span></span>

* <span data-ttu-id="2039c-202">Appuyez sur les touches **W, A, S, D, Q, E** pour déplacer la caméra.</span><span class="sxs-lookup"><span data-stu-id="2039c-202">Press **W, A, S, D, Q, E** keys to move the camera.</span></span>
* <span data-ttu-id="2039c-203">Maintenez le **bouton droit de la souris** enfoncé et déplacez la souris pour regarder autour de vous.</span><span class="sxs-lookup"><span data-stu-id="2039c-203">Hold the **Right mouse button** and move the mouse to look around.</span></span>
* <span data-ttu-id="2039c-204">Pour faire apparaître les mains simulées, appuyez sur la **barre d’espace (droite)** ou sur la **touche Maj de gauche**</span><span class="sxs-lookup"><span data-stu-id="2039c-204">To bring up the simulated hands, press **Space bar(Right hand)** or **Left Shift key(Left hand)**</span></span>
* <span data-ttu-id="2039c-205">Appuyez sur les touches **T** ou **Y** pour que les mains simulées restent affichées</span><span class="sxs-lookup"><span data-stu-id="2039c-205">To keep simulated hands in the view, press **T** or **Y** key</span></span>
* <span data-ttu-id="2039c-206">Pour faire pivoter des mains simulées, maintenez la touche **Ctrl** enfoncée et déplacez la souris</span><span class="sxs-lookup"><span data-stu-id="2039c-206">To rotate simulated hands, press and hold **Ctrl** key and move mouse</span></span>

![Mode jeu](images/mr-learning-base/base-02-section8-step1-4.gif)


## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="2039c-208">Génération de votre application sur votre HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="2039c-208">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="2039c-209">1. Générer le projet Unity</span><span class="sxs-lookup"><span data-stu-id="2039c-209">1. Build the Unity project</span></span>

<span data-ttu-id="2039c-210">Dans le menu Unity, sélectionnez **Fichier** > **Paramètres de build...** pour ouvrir la fenêtre Paramètres de build.</span><span class="sxs-lookup"><span data-stu-id="2039c-210">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="2039c-211">Dans la fenêtre Paramètres de build, cliquez sur le bouton **Add Open Scenes** (Ajouter des scènes ouvertes) pour ajouter votre scène actuelle à la liste **Scenes In Build** (Scènes dans la génération), puis cliquez sur le bouton **Générer** pour ouvrir la fenêtre de génération d’applications de plateforme Windows universelle :</span><span class="sxs-lookup"><span data-stu-id="2039c-211">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![Fenêtre Build Settings d’Unity avec UWP sélectionné](images/mr-learning-base/base-02-section9-step1-1.png)

<span data-ttu-id="2039c-213">Dans la fenêtre de génération d’applications de plateforme Windows universelle, choisissez un emplacement approprié pour stocker votre build, par exemple _D:\MixedRealityLearning\Builds_, créez un dossier et attribuez-lui un nom pertinent, par exemple _GettingStarted_, puis cliquez sur le bouton **Sélectionner un dossier** pour démarrer le processus de génération :</span><span class="sxs-lookup"><span data-stu-id="2039c-213">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![Fenêtre Build Settings d’Unity avec la fenêtre d’invite Select Folder](images/mr-learning-base/base-02-section9-step1-2.png)

<span data-ttu-id="2039c-215">Attendez qu’Unity termine le processus de génération :</span><span class="sxs-lookup"><span data-stu-id="2039c-215">Wait for Unity to finish the build process:</span></span>

![Processus de génération Unity en cours](images/mr-learning-base/base-02-section9-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="2039c-217">2. Générer et déployer l’application</span><span class="sxs-lookup"><span data-stu-id="2039c-217">2. Build and deploy the application</span></span>

<span data-ttu-id="2039c-218">Une fois le processus de génération terminé, Unity invite l’Explorateur de fichiers Windows à ouvrir l’emplacement où vous avez stocké la build.</span><span class="sxs-lookup"><span data-stu-id="2039c-218">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="2039c-219">Naviguez dans le dossier, puis double-cliquez sur le fichier solution pour l’ouvrir dans Visual Studio :</span><span class="sxs-lookup"><span data-stu-id="2039c-219">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![Explorateur Windows avec la solution Visual Studio nouvellement créée sélectionnée](images/mr-learning-base/base-02-section10-step1-1.png)

> [!NOTE]
> <span data-ttu-id="2039c-221">Si Visual Studio vous demande d’installer de nouveaux composants, prenez un moment pour vérifier que vous avez tous les composants prérequis comme spécifié dans la documentation **[Installer les outils](../../install-the-tools.md)** .</span><span class="sxs-lookup"><span data-stu-id="2039c-221">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="2039c-222">Configurez Visual Studio pour HoloLens en sélectionnant la configuration **Master** ou **Release**, l’architecture **ARM64** et **Appareil** comme cible :</span><span class="sxs-lookup"><span data-stu-id="2039c-222">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![Visual Studio configuré pour le déploiement sur HoloLens 2](images/mr-learning-base/base-02-section10-step1-2.png)

> [!TIP]
> <span data-ttu-id="2039c-224">Si vous effectuez un déploiement sur HoloLens (1ère génération), sélectionnez l’architecture **x86**.</span><span class="sxs-lookup"><span data-stu-id="2039c-224">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="2039c-225">En général, pour HoloLens, vous allez générer pour l’architecture ARM.</span><span class="sxs-lookup"><span data-stu-id="2039c-225">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="2039c-226">Il y a cependant un <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>problème connu</strong></a> dans Unity 2019.3 qui provoque des erreurs lors de la sélection de ARM comme architecture de génération dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2039c-226">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="2039c-227">La solution de contournement recommandée est de générer pour ARM64.</span><span class="sxs-lookup"><span data-stu-id="2039c-227">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="2039c-228">Si ce n’est pas possible, accédez à **Modifier > Paramètres du projet > Lecteur > Autres paramètres** et désactivez **Travaux graphiques**.</span><span class="sxs-lookup"><span data-stu-id="2039c-228">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="2039c-229">Si vous ne voyez pas Appareil comme choix de cible, il peut être nécessaire de changer le projet de démarrage pour la solution Visual Studio de Projet IL2CPP en Projet UWP.</span><span class="sxs-lookup"><span data-stu-id="2039c-229">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="2039c-230">Pour cela, dans l’Explorateur de solutions, cliquez avec le bouton droit sur nom_de_votre_projet (Windows universel), puis sélectionnez **Définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="2039c-230">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="2039c-231">Connectez votre HoloLens à votre ordinateur, puis sélectionnez **Déboguer** > **Démarrer sans débogage** pour générer et déployer sur votre appareil :</span><span class="sxs-lookup"><span data-stu-id="2039c-231">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![Visual Studio - Chemin du menu Démarrer sans débogage](images/mr-learning-base/base-02-section10-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="2039c-233">Avant d’effectuer la génération sur votre appareil, celui-ci doit être en mode développeur et associé à votre ordinateur de développement.</span><span class="sxs-lookup"><span data-stu-id="2039c-233">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="2039c-234">Vous pouvez effectuer ces deux étapes en suivant [ces instructions](../../platform-capabilities-and-apis/using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="2039c-234">Both of these steps can be completed by following [these instructions](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="2039c-235">Vous pouvez aussi déployer sur l’[émulateur HoloLens](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) ou créer un [package d’application](/windows/uwp/packaging/packaging-uwp-apps) pour un chargement indépendant (sideloading).</span><span class="sxs-lookup"><span data-stu-id="2039c-235">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="2039c-236">L’utilisation de Démarrer sans débogage démarre automatiquement l’application sur votre appareil sans le débogueur Visual Studio attaché.</span><span class="sxs-lookup"><span data-stu-id="2039c-236">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="2039c-237">Sélectionnez **Générer > Déployer la solution** pour déployer sur votre appareil sans que l’application ne démarre automatiquement.</span><span class="sxs-lookup"><span data-stu-id="2039c-237">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="2039c-238">Vous remarquerez peut-être le profileur de diagnostics dans l’application, que vous pouvez activer ou désactiver avec la commande vocale **« Toggle Diagnostics »** .</span><span class="sxs-lookup"><span data-stu-id="2039c-238">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **"Toggle Diagnostics"**.</span></span> <span data-ttu-id="2039c-239">Il est recommandé de garder le profileur visible la plupart du temps pendant le développement, de façon à comprendre quand des modifications apportées à l’application peuvent avoir un impact sur les performances.</span><span class="sxs-lookup"><span data-stu-id="2039c-239">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="2039c-240">Par exemple, les applications HoloLens doivent [s’exécuter en continu à 60 images/s](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="2039c-240">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="2039c-241">Félicitations</span><span class="sxs-lookup"><span data-stu-id="2039c-241">Congratulations</span></span>

<span data-ttu-id="2039c-242">Vous avez maintenant déployé votre première application HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2039c-242">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="2039c-243">Une fois l’application ouverte, vous devez voir un objet Cube devant vous, et vous devez pouvoir interagir avec lui en le déplaçant. Lorsque vous vous déplacez, vous devez également voir un maillage de mappage spatial couvrant les surfaces perçues par le HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2039c-243">Once the app is opened you should see a Cube object in front of you and should be able to interact with the cube by moving it and also as you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="2039c-244">En outre, vous devez voir des indicateurs sur vos mains et doigts pour le suivi de la main et un compteur de fréquence d’images pour vous tenir informé des performances de l’application.</span><span class="sxs-lookup"><span data-stu-id="2039c-244">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="2039c-245">Ces fonctionnalités sont simplement quelques composants fondamentaux inclus avec MRTK.</span><span class="sxs-lookup"><span data-stu-id="2039c-245">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="2039c-246">Dans les tutoriels à venir, vous allez ajouter du contenu à votre scène pour explorer les fonctionnalités HoloLens et MRTK.</span><span class="sxs-lookup"><span data-stu-id="2039c-246">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2039c-247">Tutoriel suivant : 3. Configuration des profils MRTK</span><span class="sxs-lookup"><span data-stu-id="2039c-247">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
