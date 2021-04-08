---
title: Initialisation de votre projet et déploiement de votre première application
description: Ce cours vous montre comment configurer votre projet Unity pour le MRTK (Mixed Reality Toolkit) et comment le déployer sur votre HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, MRTK, mixed reality toolkit, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: 4363d3280036ef2cd93e75233005c00db17eb59b
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106088615"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="9838a-104">2. Initialisation de votre projet et déploiement de votre première application</span><span class="sxs-lookup"><span data-stu-id="9838a-104">2. Initializing your project and deploying your first application</span></span>

<span data-ttu-id="9838a-105">Dans ce tutoriel, vous allez apprendre à créer un nouveau projet Unity, à le configurer pour le développement <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/" target="_blank">MRTK (Mixed Reality Toolkit)</a> et à importer MRTK.</span><span class="sxs-lookup"><span data-stu-id="9838a-105">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="9838a-106">Vous allez également effectuer la configuration, la génération et le déploiement d’une scène Unity de base depuis Visual Studio sur votre HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9838a-106">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="9838a-107">Une fois que l’avez déployée sur votre HoloLens 2, vous devez voir un maillage de mappage spatial couvrant les surfaces qui sont perçues par HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9838a-107">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="9838a-108">En outre, vous devez voir des indicateurs sur vos mains et doigts pour le suivi de la main et un compteur de fréquence d’images pour vous tenir informé des performances de l’application.</span><span class="sxs-lookup"><span data-stu-id="9838a-108">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

![MRTK](../../../develop/images/Unity_MRTK_MRFT_Flow.png)

## <a name="objectives"></a><span data-ttu-id="9838a-110">Objectifs</span><span class="sxs-lookup"><span data-stu-id="9838a-110">Objectives</span></span>

* <span data-ttu-id="9838a-111">Apprendre à configurer Unity pour le développement HoloLens</span><span class="sxs-lookup"><span data-stu-id="9838a-111">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="9838a-112">Apprendre à créer et déployer votre application sur HoloLens</span><span class="sxs-lookup"><span data-stu-id="9838a-112">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="9838a-113">Expérimenter le maillage du mappage spatial, les maillages de la main et le compteur de fréquence d’images sur un appareil HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="9838a-113">Experience the spatial mapping mesh, hand meshes, and the framerate counter on HoloLens 2 device</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="9838a-114">Création du projet Unity</span><span class="sxs-lookup"><span data-stu-id="9838a-114">Creating the Unity project</span></span>

<span data-ttu-id="9838a-115">Lancez **Unity Hub**, sélectionnez l’onglet **Projets**, puis cliquez sur la **flèche bas** en regard du bouton **Nouveau** :</span><span class="sxs-lookup"><span data-stu-id="9838a-115">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![Unity Hub avec le bouton New mis en évidence](images/mr-learning-base/base-02-section1-step1-1.png)

<span data-ttu-id="9838a-117">Dans la liste déroulante, sélectionnez la **version** Unity spécifiée dans les [prérequis](mr-learning-base-01.md#prerequisites) :</span><span class="sxs-lookup"><span data-stu-id="9838a-117">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![Unity Hub avec la liste déroulante du sélecteur de version NEW](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="9838a-119">Si cette version spécifique d’Unity n’est pas disponible dans Unity Hub, vous pouvez lancer l’installation à partir de la page <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Unity download archive</a>.</span><span class="sxs-lookup"><span data-stu-id="9838a-119">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="9838a-120">Dans la fenêtre Créer un projet :</span><span class="sxs-lookup"><span data-stu-id="9838a-120">In the Create a new project window:</span></span>

* <span data-ttu-id="9838a-121">Vérifiez que **Modèles** est défini sur **3D**</span><span class="sxs-lookup"><span data-stu-id="9838a-121">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="9838a-122">Entrez un **Nom du projet** approprié, par exemple _Tutoriels MRTK_</span><span class="sxs-lookup"><span data-stu-id="9838a-122">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="9838a-123">Choisissez un **Emplacement** approprié pour stocker votre projet, par exemple _D:\MixedRealityLearning_</span><span class="sxs-lookup"><span data-stu-id="9838a-123">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="9838a-124">Cliquez sur le bouton **Créer** pour créer et lancer votre nouveau projet Unity</span><span class="sxs-lookup"><span data-stu-id="9838a-124">Click the **Create** button to create and launch your new Unity project</span></span>

![Unity Hub avec la fenêtre Create a new project renseignée](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="9838a-126">Quand vous utilisez Windows, il existe une limite de 255 caractères pour MAX_PATH.</span><span class="sxs-lookup"><span data-stu-id="9838a-126">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="9838a-127">Par conséquent, vous devez enregistrer le projet Unity près de la racine du lecteur.</span><span class="sxs-lookup"><span data-stu-id="9838a-127">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="9838a-128">Attendez qu’Unity crée le projet :</span><span class="sxs-lookup"><span data-stu-id="9838a-128">Wait for Unity to create the project:</span></span>

![Création du nouveau projet Unity en cours](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="9838a-130">Changement de plateforme de génération</span><span class="sxs-lookup"><span data-stu-id="9838a-130">Switching the build platform</span></span>

[!INCLUDE[](includes/switching-build-platform.md)]

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="9838a-131">Importation des ressources TextMeshPro Essential</span><span class="sxs-lookup"><span data-stu-id="9838a-131">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="9838a-132">Dans le menu Unity, sélectionnez **Window** > **TextMeshPro** > **Import TMP Essential Resources** pour ouvrir la fenêtre Import Unity Package :</span><span class="sxs-lookup"><span data-stu-id="9838a-132">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources** to open the Import Unity Package window:</span></span>

![Chemin du menu Import TMP Essential Resources d’Unity](images/mr-learning-base/base-02-section3-step1-1.png)

<span data-ttu-id="9838a-134">Dans la fenêtre Import Unity Package (Importer un package Unity), cliquez sur le bouton **Tous** pour vous assurer que toutes les ressources sont sélectionnées, puis sur le bouton **Importer** pour importer les ressources :</span><span class="sxs-lookup"><span data-stu-id="9838a-134">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Fenêtre d’importation des ressources essentielles TMP d’Unity](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="9838a-136">Les ressources TextMeshPro Essential sont requises par les éléments de l’interface utilisateur de MRTK.</span><span class="sxs-lookup"><span data-stu-id="9838a-136">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="9838a-137">Vous pouvez ignorer cette étape si vous ne prévoyez pas d’utiliser des éléments de l’interface utilisateur de MRTK dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="9838a-137">You can skip this step if you are not planning to use MRTK's UI elements in your project.</span></span>

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="9838a-138">Importation du Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="9838a-138">Importing the Mixed Reality Toolkit</span></span>

<span data-ttu-id="9838a-139">Pour importer le Mixed Reality Toolkit dans le projet Unity, vous devez utiliser [Mixed Reality Feature Tool](../welcome-to-mr-feature-tool.md) qui permet aux développeurs de découvrir, mettre à jour et ajouter des packages de fonctionnalités Mixed Reality dans des projets Unity.</span><span class="sxs-lookup"><span data-stu-id="9838a-139">To Import Mixed Reality Toolkit into the Unity Project you will have to use [Mixed Reality Feature Tool](../welcome-to-mr-feature-tool.md) which allows  developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="9838a-140">Vous pouvez rechercher des packages par nom ou par catégorie, voir leurs dépendances et même voir les changements proposés pour votre fichier manifeste de projets avant l’importation.</span><span class="sxs-lookup"><span data-stu-id="9838a-140">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span>

<span data-ttu-id="9838a-141">Téléchargez la dernière version du Mixed Reality Feature Tool dans le [Centre de téléchargement Microsoft](https://aka.ms/MRFeatureTool). Une fois le téléchargement terminé, décompressez le fichier et enregistrez-le sur votre Bureau.</span><span class="sxs-lookup"><span data-stu-id="9838a-141">Download the latest version of the Mixed Reality Feature Tool from the [Microsoft Download Center](https://aka.ms/MRFeatureTool), When the download is complete, unzip the file and save it to your desktop.</span></span>

> [!NOTE]
> <span data-ttu-id="9838a-142">Avant de pouvoir exécuter le Mixed Reality Feature Tool, vous devez installer le [runtime .NET 5.0](https://dotnet.microsoft.com/download/dotnet/5.0).</span><span class="sxs-lookup"><span data-stu-id="9838a-142">Before you can run the Mixed Reality Feature Tool please install [.NET 5.0 runtime](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>

> [!NOTE]
> <span data-ttu-id="9838a-143">Actuellement, le Mixed Reality Feature Tool s’exécute uniquement sur Windows. Pour MacOS, suivez la [procédure](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html#1-get-the-latest-mrtk-unity-packages) pour télécharger et importer le Mixed Reality Toolkit dans le projet Unity.</span><span class="sxs-lookup"><span data-stu-id="9838a-143">The Mixed Reality Feature Tool currently only runs on Windows, For MacOS please follow this [procedure](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html#1-get-the-latest-mrtk-unity-packages) to download and import the Mixed Reality Toolkit into the unity project.</span></span>

<span data-ttu-id="9838a-144">Ouvrez le fichier exécutable **MixedRealityFeatureTool** dans le dossier téléchargé pour lancer le Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="9838a-144">Open the executable file **MixedRealityFeatureTool** from the downloaded folder to launch the Mixed Reality Feature Tool.</span></span>  

![Ouverture de MixedRealityFeatureTool](images/mr-learning-base/base-02-section4-step1-1.png)


[!INCLUDE[](includes/importing-mrtk.md)]

## <a name="configuring-the-unity-project"></a><span data-ttu-id="9838a-146">Configuration du projet Unity</span><span class="sxs-lookup"><span data-stu-id="9838a-146">Configuring the Unity project</span></span>

### <a name="1-apply-the-mrtk-project-configurator-settings"></a><span data-ttu-id="9838a-147">1. Appliquer les paramètres du configurateur de projet MRTK</span><span class="sxs-lookup"><span data-stu-id="9838a-147">1. Apply the MRTK Project Configurator settings</span></span>

<span data-ttu-id="9838a-148">Une fois que Unity a fini d’importer le package de la section précédente, la fenêtre MRTK Project Configurator doit s’afficher.</span><span class="sxs-lookup"><span data-stu-id="9838a-148">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="9838a-149">Si ce n’est pas le cas, vous pouvez ouvrir manuellement en accédant à **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** :</span><span class="sxs-lookup"><span data-stu-id="9838a-149">If it doesn't, you can manually open it by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**:</span></span>

![Chemin du menu Configure Unity Project d’Unity](images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="9838a-151">Dans la fenêtre MRTK Project Configurator, développez la section **Modify Configurations**, vérifiez que toutes les options sont cochées, puis cliquez sur le bouton **Apply** pour appliquer les paramètres :</span><span class="sxs-lookup"><span data-stu-id="9838a-151">In the MRTK Project Configurator window, expand the **Modify Configurations** section, ensure all options are checked, and click the **Apply** button to apply the settings:</span></span>

![Fenêtre MRTK Project Configurator d’Unity](images/mr-learning-base/base-02-section5-step1-2.png)

> [!TIP]
> <span data-ttu-id="9838a-153">L’application des paramètres par défaut de MRTK est facultative mais fortement recommandée, car elle permet de configurer certains paramètres Unity recommandés :</span><span class="sxs-lookup"><span data-stu-id="9838a-153">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="9838a-154">Set Single Pass Instanced rendering path : Améliore les performances graphiques en exécutant le pipeline de rendu pour les deux yeux dans le même appel de dessin.</span><span class="sxs-lookup"><span data-stu-id="9838a-154">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="9838a-155">Pour plus d’informations à ce sujet, vous pouvez vous reporter à la section [Single-Pass Instanced rendering](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) de la documentation sur les [performances](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) de MRTK.</span><span class="sxs-lookup"><span data-stu-id="9838a-155">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) section of MRTK's [Performance](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) documentation.</span></span>
> * <span data-ttu-id="9838a-156">Définissez la couche de reconnaissance spatiale par défaut : Crée une couche Unity nommée Spatial Awareness et configure MRTK afin qu’il utilise cette couche pour le maillage de reconnaissance spatiale.</span><span class="sxs-lookup"><span data-stu-id="9838a-156">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="9838a-157">Pour plus d’informations sur les couches d’Unity, consultez la documentation <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Personnalisation de votre espace de travail</a>.</span><span class="sxs-lookup"><span data-stu-id="9838a-157">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

### <a name="2-configure-additional-project-settings"></a><span data-ttu-id="9838a-158">2. Configurer des paramètres de projet supplémentaires</span><span class="sxs-lookup"><span data-stu-id="9838a-158">2. Configure additional project settings</span></span>

[!INCLUDE[](includes/configuring-additional-project-settings.md)]

## <a name="creating-the-scene-and-configuring-mrtk"></a><span data-ttu-id="9838a-159">Création de la scène et configuration de MRTK</span><span class="sxs-lookup"><span data-stu-id="9838a-159">Creating the scene and configuring MRTK</span></span>

<span data-ttu-id="9838a-160">Dans le menu Unity, sélectionnez **File** > **New Scene** pour créer une scène :</span><span class="sxs-lookup"><span data-stu-id="9838a-160">In the Unity menu, select **File** > **New Scene** to create a new scene:</span></span>

![Unity - New Scene - Chemin du menu](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="9838a-162">Dans le menu Unity, sélectionnez **Mixed Reality Toolkit** > **Add to Scene and Configure...** pour ajouter le MRTK à votre scène actuelle :</span><span class="sxs-lookup"><span data-stu-id="9838a-162">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![Unity - Add to Scene and Configure... Chemin du menu](images/mr-learning-base/base-02-section6-step1-2.png)

[!INCLUDE[](includes/changing-profile.md)]

<span data-ttu-id="9838a-164">Dans le menu Unity, sélectionnez **Fichier** > **Enregistrer sous...** pour ouvrir la fenêtre Save Scene (Enregistrer la scène) :</span><span class="sxs-lookup"><span data-stu-id="9838a-164">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![Unity - Save As... Chemin du menu](images/mr-learning-base/base-02-section6-step1-4.png)

> [!TIP]
> <span data-ttu-id="9838a-166">La réduction du format de la profondeur à 16 bits est facultative, mais peut aider à améliorer les performances graphiques dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="9838a-166">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="9838a-167">Pour plus d’informations à ce sujet, vous pouvez vous reporter à la section <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">Depth buffer sharing (HoloLens)</a> de la documentation sur les <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">performances</a> de MRTK.</span><span class="sxs-lookup"><span data-stu-id="9838a-167">To learn more about this topic, you can refer to the   <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">  Depth buffer sharing (HoloLens) </a> section of MRTK's  <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank"> Performance </a> documentation.</span></span>

![Fenêtre d’invite Save d’Unity pour enregistrer la scène](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="9838a-169">Importation des ressources du tutoriel</span><span class="sxs-lookup"><span data-stu-id="9838a-169">Importing the tutorial assets</span></span>

<span data-ttu-id="9838a-170">Téléchargez le package personnalisé Unity suivant :</span><span class="sxs-lookup"><span data-stu-id="9838a-170">Download the following Unity custom package:</span></span>

* [<span data-ttu-id="9838a-171">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="9838a-171">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.5.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage)

<span data-ttu-id="9838a-172">Pour importer un package personnalisé Unity, dans le menu Unity, sélectionnez **Assets** > **Import Package** > **Custom Package...** pour ouvrir la fenêtre Import package :</span><span class="sxs-lookup"><span data-stu-id="9838a-172">To Import a Unity custom package, In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![Importation d’un package personnalisé](images/mr-learning-base/base-02-section7-step1-1.png)

<span data-ttu-id="9838a-174">Dans la fenêtre Import package, sélectionnez le package **MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage** que vous avez téléchargé, puis cliquez sur le bouton Open :</span><span class="sxs-lookup"><span data-stu-id="9838a-174">In the Import package... window, select the **MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage** you downloaded and click the Open button:</span></span>

![Sélection d’un package de ressources](images/mr-learning-base/base-02-section7-step1-2.png)

<span data-ttu-id="9838a-176">Dans la fenêtre Import Unity Package (Importer un package Unity), cliquez sur le bouton Tous pour vous assurer que toutes les ressources sont sélectionnées, puis sur le bouton Importer pour importer les ressources :</span><span class="sxs-lookup"><span data-stu-id="9838a-176">In the Import Unity Package window, click the All button to ensure all the assets are selected, then click the Import button to import the assets:</span></span>

![Sélection de toutes les ressources à importer](images/mr-learning-base/base-02-section7-step1-3.png)

<span data-ttu-id="9838a-178">Une fois que vous avez importé les ressources du tutoriel, votre fenêtre Project doit ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="9838a-178">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Fenêtre de projet Unity après l’importation de ressources](images/mr-learning-base/base-02-section7-step1-4.png)

## <a name="configuring-the-scene"></a><span data-ttu-id="9838a-180">Configuration de la scène</span><span class="sxs-lookup"><span data-stu-id="9838a-180">Configuring the Scene</span></span>

<span data-ttu-id="9838a-181">Dans la fenêtre Project, accédez au dossier Assets > MRTK.Tutorials.GettingStarted > Prefabs :</span><span class="sxs-lookup"><span data-stu-id="9838a-181">In the Project window, navigate to the Assets > MRTK.Tutorials.GettingStarted > Prefabs folder:</span></span>

<span data-ttu-id="9838a-182">Dans la fenêtre Project, cliquez sur le préfabriqué **Cube** et faites-le glisser sur la fenêtre Hierarchy puis, dans la fenêtre Inspector, configurez son composant **Transform** comme suit :</span><span class="sxs-lookup"><span data-stu-id="9838a-182">From the Project window, click-and-drag the **Cube** prefab on to the Hierarchy window, then in the Inspector window configure its **Transform** component as follows</span></span>

* <span data-ttu-id="9838a-183">**Position** : X = 0, Y = 0, Z = 0.5</span><span class="sxs-lookup"><span data-stu-id="9838a-183">**Position**: X = 0, Y = 0, Z = 0.5</span></span>
* <span data-ttu-id="9838a-184">**Rotation** : X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="9838a-184">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="9838a-185">**Scale** : X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="9838a-185">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Ajout d’un cube à la scène](images/mr-learning-base/base-02-section8-step1-1.png)

<span data-ttu-id="9838a-187">Pour vous concentrer sur les objets de la scène, vous pouvez double-cliquer sur l’objet **Cube**, puis faire un léger zoom avant :</span><span class="sxs-lookup"><span data-stu-id="9838a-187">To focus in on the objects in the scene, you can double-click on the **Cube** object, and then zoom slightly in again:</span></span>

<span data-ttu-id="9838a-188">Pour interagir et saisir un objet avec les mains, il faut que l’objet ait un composant Collider, par exemple un **Box Collider**, un composant **Object Manipulator (Script)** et un composant **NearInteractionGrabbable(Script)** .</span><span class="sxs-lookup"><span data-stu-id="9838a-188">To interact and grab an object with tracked hands, the object must have Collider component for example a **Box Collider**,  **Object Manipulator (Script)** component and **NearInteractionGrabbable(Script)** component.</span></span>

<span data-ttu-id="9838a-189">Toujours avec le **cube** sélectionné dans la fenêtre Hierarchy, dans la fenêtre Inspector, cliquez sur le bouton **Add Component**, puis recherchez et sélectionnez le script **Object Manipulator** pour ajouter le script Object Manipulator à l’objet Cube.</span><span class="sxs-lookup"><span data-stu-id="9838a-189">With the **Cube** still selected in the Hierarchy window, in the Inspector window ,click on **Add Component** button, then search and select **Object Manipulator** script to add the Object Manipulator script to the cube object.</span></span>

![Ajout d’un manipulateur d’objet au cube](images/mr-learning-base/base-02-section8-step1-2.png)

<span data-ttu-id="9838a-191">Répétez la même procédure pour ajouter un **script Near Interaction Grabbable** au cube.</span><span class="sxs-lookup"><span data-stu-id="9838a-191">Repeat the same to add **Near Interaction Grabbable script** to the cube</span></span>

![Ajout d’un script Near Interaction Grabbable au cube](images/mr-learning-base/base-02-section8-step1-3.png)

> [!NOTE]
> <span data-ttu-id="9838a-193">Quand vous ajoutez un Object Manipulator (Script), dans ce cas, le Constraint Manager (Script) est ajouté automatiquement, car Object Manipulator (Script) en dépend.</span><span class="sxs-lookup"><span data-stu-id="9838a-193">When you add a Object Manipulator (Script), in this case, the Constraint Manager (Script) is automatically added because Object Manipulator (Script) depends on it.</span></span>

> [!NOTE]
> <span data-ttu-id="9838a-194">Dans le cadre de ce tutoriel, les colliders ont déjà été ajoutés à l’objet Cube.</span><span class="sxs-lookup"><span data-stu-id="9838a-194">For the purpose of this tutorial, colliders have already been added to the Cube Object.</span></span> <span data-ttu-id="9838a-195">Pour plus d’informations sur les colliders, vous pouvez consulter la documentation <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> d’Unity.</span><span class="sxs-lookup"><span data-stu-id="9838a-195">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

<span data-ttu-id="9838a-196">Pour tester cela dans l’éditeur Unity, vous pouvez entrer en mode lecture et maintenir la touche **Maj gauche** ou **Espace** enfoncée pour activer le contrôleur. Un déplacement de la souris permet de déplacer le contrôleur, et vous pouvez également le rapprocher ou l’éloigner de la caméra à l’aide de la roulette de la souris.</span><span class="sxs-lookup"><span data-stu-id="9838a-196">To test this in the Unity editor, you can enter the play mode and hold the **LeftShift** or **Space** key to enable the controller, Mouse movement will move the controller and also it can be moved further or closer to the camera using the mouse wheel.</span></span> <span data-ttu-id="9838a-197">Une fois que le pointeur se trouve sur le cube, appuyez sur le **bouton droit de la souris** pour déplacer l’objet Cube.</span><span class="sxs-lookup"><span data-stu-id="9838a-197">Once the pointer is on the Cube  press and hold **Right Mouse Button** to move the the Cube object.</span></span>

![Mode jeu](images/mr-learning-base/base-02-section8-step1-4.png)

## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="9838a-199">Génération de votre application sur votre HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="9838a-199">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="9838a-200">1. Générer le projet Unity</span><span class="sxs-lookup"><span data-stu-id="9838a-200">1. Build the Unity project</span></span>

<span data-ttu-id="9838a-201">Dans le menu Unity, sélectionnez **Fichier** > **Paramètres de build...** pour ouvrir la fenêtre Paramètres de build.</span><span class="sxs-lookup"><span data-stu-id="9838a-201">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="9838a-202">Dans la fenêtre Paramètres de build, cliquez sur le bouton **Add Open Scenes** (Ajouter des scènes ouvertes) pour ajouter votre scène actuelle à la liste **Scenes In Build** (Scènes dans la génération), puis cliquez sur le bouton **Générer** pour ouvrir la fenêtre de génération d’applications de plateforme Windows universelle :</span><span class="sxs-lookup"><span data-stu-id="9838a-202">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![Fenêtre Build Settings d’Unity avec UWP sélectionné](images/mr-learning-base/base-02-section9-step1-1.png)

<span data-ttu-id="9838a-204">Dans la fenêtre de génération d’applications de plateforme Windows universelle, choisissez un emplacement approprié pour stocker votre build, par exemple _D:\MixedRealityLearning\Builds_, créez un dossier et attribuez-lui un nom pertinent, par exemple _GettingStarted_, puis cliquez sur le bouton **Sélectionner un dossier** pour démarrer le processus de génération :</span><span class="sxs-lookup"><span data-stu-id="9838a-204">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![Fenêtre Build Settings d’Unity avec la fenêtre d’invite Select Folder](images/mr-learning-base/base-02-section9-step1-2.png)

<span data-ttu-id="9838a-206">Attendez qu’Unity termine le processus de génération :</span><span class="sxs-lookup"><span data-stu-id="9838a-206">Wait for Unity to finish the build process:</span></span>

![Processus de génération Unity en cours](images/mr-learning-base/base-02-section9-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="9838a-208">2. Générer et déployer l’application</span><span class="sxs-lookup"><span data-stu-id="9838a-208">2. Build and deploy the application</span></span>

<span data-ttu-id="9838a-209">Une fois le processus de génération terminé, Unity invite l’Explorateur de fichiers Windows à ouvrir l’emplacement où vous avez stocké la build.</span><span class="sxs-lookup"><span data-stu-id="9838a-209">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="9838a-210">Naviguez dans le dossier, puis double-cliquez sur le fichier solution pour l’ouvrir dans Visual Studio :</span><span class="sxs-lookup"><span data-stu-id="9838a-210">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![Explorateur Windows avec la solution Visual Studio nouvellement créée sélectionnée](images/mr-learning-base/base-02-section10-step1-1.png)

> [!NOTE]
> <span data-ttu-id="9838a-212">Si Visual Studio vous demande d’installer de nouveaux composants, prenez un moment pour vérifier que vous avez tous les composants prérequis comme spécifié dans la documentation **[Installer les outils](../../install-the-tools.md)** .</span><span class="sxs-lookup"><span data-stu-id="9838a-212">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="9838a-213">Configurez Visual Studio pour HoloLens en sélectionnant la configuration **Master** ou **Release**, l’architecture **ARM64** et **Appareil** comme cible :</span><span class="sxs-lookup"><span data-stu-id="9838a-213">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![Visual Studio configuré pour le déploiement sur HoloLens 2](images/mr-learning-base/base-02-section10-step1-2.png)

> [!TIP]
> <span data-ttu-id="9838a-215">Si vous effectuez un déploiement sur HoloLens (1ère génération), sélectionnez l’architecture **x86**.</span><span class="sxs-lookup"><span data-stu-id="9838a-215">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="9838a-216">En général, pour HoloLens, vous allez générer pour l’architecture ARM.</span><span class="sxs-lookup"><span data-stu-id="9838a-216">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="9838a-217">Il y a cependant un <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>problème connu</strong></a> dans Unity 2019.3 qui provoque des erreurs lors de la sélection de ARM comme architecture de génération dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9838a-217">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="9838a-218">La solution de contournement recommandée est de générer pour ARM64.</span><span class="sxs-lookup"><span data-stu-id="9838a-218">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="9838a-219">Si ce n’est pas possible, accédez à **Modifier > Paramètres du projet > Lecteur > Autres paramètres** et désactivez **Travaux graphiques**.</span><span class="sxs-lookup"><span data-stu-id="9838a-219">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="9838a-220">Si vous ne voyez pas Appareil comme choix de cible, il peut être nécessaire de changer le projet de démarrage pour la solution Visual Studio de Projet IL2CPP en Projet UWP.</span><span class="sxs-lookup"><span data-stu-id="9838a-220">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="9838a-221">Pour cela, dans l’Explorateur de solutions, cliquez avec le bouton droit sur nom_de_votre_projet (Windows universel), puis sélectionnez **Définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="9838a-221">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="9838a-222">Connectez votre HoloLens à votre ordinateur, puis sélectionnez **Déboguer** > **Démarrer sans débogage** pour générer et déployer sur votre appareil :</span><span class="sxs-lookup"><span data-stu-id="9838a-222">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![Visual Studio - Chemin du menu Démarrer sans débogage](images/mr-learning-base/base-02-section10-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="9838a-224">Avant d’effectuer la génération sur votre appareil, celui-ci doit être en mode développeur et associé à votre ordinateur de développement.</span><span class="sxs-lookup"><span data-stu-id="9838a-224">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="9838a-225">Vous pouvez effectuer ces deux étapes en suivant [ces instructions](../../platform-capabilities-and-apis/using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="9838a-225">Both of these steps can be completed by following [these instructions](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="9838a-226">Vous pouvez aussi déployer sur l’[émulateur HoloLens](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) ou créer un [package d’application](/windows/uwp/packaging/packaging-uwp-apps) pour un chargement indépendant (sideloading).</span><span class="sxs-lookup"><span data-stu-id="9838a-226">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="9838a-227">L’utilisation de Démarrer sans débogage démarre automatiquement l’application sur votre appareil sans le débogueur Visual Studio attaché.</span><span class="sxs-lookup"><span data-stu-id="9838a-227">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="9838a-228">Sélectionnez **Générer > Déployer la solution** pour déployer sur votre appareil sans que l’application ne démarre automatiquement.</span><span class="sxs-lookup"><span data-stu-id="9838a-228">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="9838a-229">Vous remarquerez peut-être le profileur de diagnostics dans l’application, que vous pouvez activer ou désactiver avec la commande vocale **Toggle Diagnostics**.</span><span class="sxs-lookup"><span data-stu-id="9838a-229">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="9838a-230">Il est recommandé de garder le profileur visible la plupart du temps pendant le développement, de façon à comprendre quand des modifications apportées à l’application peuvent avoir un impact sur les performances.</span><span class="sxs-lookup"><span data-stu-id="9838a-230">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="9838a-231">Par exemple, les applications HoloLens doivent [s’exécuter en continu à 60 images/s](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="9838a-231">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="9838a-232">Félicitations</span><span class="sxs-lookup"><span data-stu-id="9838a-232">Congratulations</span></span>

<span data-ttu-id="9838a-233">Vous avez maintenant déployé votre première application HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9838a-233">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="9838a-234">Une fois l’application ouverte, vous devez voir un objet Cube devant vous, et vous devez pouvoir interagir avec lui en le déplaçant. Lorsque vous vous déplacez, vous devez également voir un maillage de mappage spatial couvrant les surfaces perçues par le HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9838a-234">Once the app is opened you should see a Cube object in front of you and should be able to interact with the cube by moving it and also as you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="9838a-235">En outre, vous devez voir des indicateurs sur vos mains et doigts pour le suivi de la main et un compteur de fréquence d’images pour vous tenir informé des performances de l’application.</span><span class="sxs-lookup"><span data-stu-id="9838a-235">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="9838a-236">Ces fonctionnalités sont simplement quelques composants fondamentaux inclus avec MRTK.</span><span class="sxs-lookup"><span data-stu-id="9838a-236">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="9838a-237">Dans les tutoriels à venir, vous allez ajouter du contenu à votre scène pour explorer les fonctionnalités HoloLens et MRTK.</span><span class="sxs-lookup"><span data-stu-id="9838a-237">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9838a-238">Tutoriel suivant : 3. Configuration des profils MRTK</span><span class="sxs-lookup"><span data-stu-id="9838a-238">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)