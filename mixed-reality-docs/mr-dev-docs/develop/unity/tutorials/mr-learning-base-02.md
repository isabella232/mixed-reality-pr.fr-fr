---
title: Initialisation de votre projet et déploiement de votre première application
description: Ce cours vous montre comment configurer votre projet Unity pour le MRTK (Mixed Reality Toolkit) et comment le déployer sur votre HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, MRTK, mixed reality toolkit, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: 82551257339d41940075ee06a6e6937624b83900
ms.sourcegitcommit: 08503cada8a29a34bcbd9fd955cb23adfe9b60a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99627850"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="91222-104">2. Initialisation de votre projet et déploiement de votre première application</span><span class="sxs-lookup"><span data-stu-id="91222-104">2. Initializing your project and deploying your first application</span></span>

<span data-ttu-id="91222-105">Dans ce tutoriel, vous allez apprendre à créer un nouveau projet Unity, à le configurer pour le développement <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">MRTK (Mixed Reality Toolkit)</a> et à importer MRTK.</span><span class="sxs-lookup"><span data-stu-id="91222-105">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="91222-106">Vous allez également effectuer la configuration, la génération et le déploiement d’une scène Unity de base depuis Visual Studio sur votre HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="91222-106">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="91222-107">Une fois que l’avez déployée sur votre HoloLens 2, vous devez voir un maillage de mappage spatial couvrant les surfaces qui sont perçues par HoloLens.</span><span class="sxs-lookup"><span data-stu-id="91222-107">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="91222-108">En outre, vous devez voir des indicateurs sur vos mains et doigts pour le suivi de la main et un compteur de fréquence d’images pour vous tenir informé des performances de l’application.</span><span class="sxs-lookup"><span data-stu-id="91222-108">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

## <a name="objectives"></a><span data-ttu-id="91222-109">Objectifs</span><span class="sxs-lookup"><span data-stu-id="91222-109">Objectives</span></span>

* <span data-ttu-id="91222-110">Apprendre à configurer Unity pour le développement HoloLens</span><span class="sxs-lookup"><span data-stu-id="91222-110">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="91222-111">Apprendre à créer et déployer votre application sur HoloLens</span><span class="sxs-lookup"><span data-stu-id="91222-111">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="91222-112">Expérimenter le maillage du mappage spatial, les maillages de la main et le compteur de fréquence d’images sur un appareil HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="91222-112">Experience the spatial mapping mesh, hand meshes, and the framerate counter on HoloLens 2 device</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="91222-113">Création du projet Unity</span><span class="sxs-lookup"><span data-stu-id="91222-113">Creating the Unity project</span></span>

<span data-ttu-id="91222-114">Lancez **Unity Hub**, sélectionnez l’onglet **Projets**, puis cliquez sur la **flèche bas** en regard du bouton **Nouveau** :</span><span class="sxs-lookup"><span data-stu-id="91222-114">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![Unity Hub avec le bouton New mis en évidence](images/mr-learning-base/base-02-section1-step1-1.png)

<span data-ttu-id="91222-116">Dans la liste déroulante, sélectionnez la **version** Unity spécifiée dans les [prérequis](mr-learning-base-01.md#prerequisites) :</span><span class="sxs-lookup"><span data-stu-id="91222-116">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![Unity Hub avec la liste déroulante du sélecteur de version NEW](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="91222-118">Si cette version spécifique d’Unity n’est pas disponible dans Unity Hub, vous pouvez lancer l’installation à partir de la page <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Unity download archive</a>.</span><span class="sxs-lookup"><span data-stu-id="91222-118">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="91222-119">Dans la fenêtre Créer un projet :</span><span class="sxs-lookup"><span data-stu-id="91222-119">In the Create a new project window:</span></span>

* <span data-ttu-id="91222-120">Vérifiez que **Modèles** est défini sur **3D**</span><span class="sxs-lookup"><span data-stu-id="91222-120">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="91222-121">Entrez un **Nom du projet** approprié, par exemple _Tutoriels MRTK_</span><span class="sxs-lookup"><span data-stu-id="91222-121">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="91222-122">Choisissez un **Emplacement** approprié pour stocker votre projet, par exemple _D:\MixedRealityLearning_</span><span class="sxs-lookup"><span data-stu-id="91222-122">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="91222-123">Cliquez sur le bouton **Créer** pour créer et lancer votre nouveau projet Unity</span><span class="sxs-lookup"><span data-stu-id="91222-123">Click the **Create** button to create and launch your new Unity project</span></span>

![Unity Hub avec la fenêtre Create a new project renseignée](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="91222-125">Quand vous utilisez Windows, il existe une limite de 255 caractères pour MAX_PATH.</span><span class="sxs-lookup"><span data-stu-id="91222-125">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="91222-126">Par conséquent, vous devez enregistrer le projet Unity près de la racine du lecteur.</span><span class="sxs-lookup"><span data-stu-id="91222-126">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="91222-127">Attendez qu’Unity crée le projet :</span><span class="sxs-lookup"><span data-stu-id="91222-127">Wait for Unity to create the project:</span></span>

![Création du nouveau projet Unity en cours](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="91222-129">Changement de plateforme de génération</span><span class="sxs-lookup"><span data-stu-id="91222-129">Switching the build platform</span></span>

<span data-ttu-id="91222-130">Dans le menu Unity, sélectionnez **Fichier** > **Paramètres de build...** pour ouvrir la fenêtre Paramètres de build :</span><span class="sxs-lookup"><span data-stu-id="91222-130">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Unity - Build Settings... Chemin du menu](images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="91222-132">Dans la fenêtre Paramètres de build, sélectionnez **Plateforme Windows universelle** , puis cliquez sur le bouton **Switch Platform** (Changer de plateforme) :</span><span class="sxs-lookup"><span data-stu-id="91222-132">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![Fenêtre Build Setting d’Unity avec UWP sélectionné comme nouvelle plateforme, qui était auparavant Standalone](images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="91222-134">Attendez qu’Unity termine le changement de plateforme :</span><span class="sxs-lookup"><span data-stu-id="91222-134">Wait for Unity to finish switching the platform:</span></span>

![Unity - Changement de plateforme en cours](images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="91222-136">Quand Unity a terminé le changement de plateforme, cliquez sur l’icône **x** rouge pour fermer la fenêtre Paramètres de build :</span><span class="sxs-lookup"><span data-stu-id="91222-136">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![Fenêtre Build d’Unity avec l’icône Fermer mise en évidence](images/mr-learning-base/base-02-section2-step1-4.png)

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="91222-138">Importation des ressources TextMeshPro Essential</span><span class="sxs-lookup"><span data-stu-id="91222-138">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="91222-139">Dans le menu Unity, sélectionnez **Window** > **TextMeshPro** > **Import TMP Essential Resources** pour ouvrir la fenêtre Import Unity Package :</span><span class="sxs-lookup"><span data-stu-id="91222-139">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources** to open the Import Unity Package window:</span></span>

![Chemin du menu Import TMP Essential Resources d’Unity](images/mr-learning-base/base-02-section3-step1-1.png)

<span data-ttu-id="91222-141">Dans la fenêtre Import Unity Package (Importer un package Unity), cliquez sur le bouton **Tous** pour vous assurer que toutes les ressources sont sélectionnées, puis sur le bouton **Importer** pour importer les ressources :</span><span class="sxs-lookup"><span data-stu-id="91222-141">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Fenêtre d’importation des ressources essentielles TMP d’Unity](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="91222-143">Les ressources TextMeshPro Essential sont requises par les éléments de l’interface utilisateur de MRTK.</span><span class="sxs-lookup"><span data-stu-id="91222-143">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="91222-144">Vous pouvez ignorer cette étape si vous ne prévoyez pas d’utiliser des éléments de l’interface utilisateur de MRTK dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="91222-144">You can skip this step if you are not planning to use MRTK's UI elements in your project.</span></span>

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="91222-145">Importation du Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="91222-145">Importing the Mixed Reality Toolkit</span></span>

<span data-ttu-id="91222-146">Pour importer le Mixed Reality Toolkit dans le projet Unity, vous devez utiliser [Mixed Reality Feature Tool](https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) qui permet aux développeurs de découvrir, mettre à jour et ajouter des packages de fonctionnalités Mixed Reality dans des projets Unity.</span><span class="sxs-lookup"><span data-stu-id="91222-146">To Import Mixed Reality Toolkit into the Unity Project you will have to use [Mixed Reality Feature Tool](https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) which allows  developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="91222-147">Vous pouvez rechercher des packages par nom ou par catégorie, voir leurs dépendances et même voir les changements proposés pour votre fichier manifeste de projets avant l’importation.</span><span class="sxs-lookup"><span data-stu-id="91222-147">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span>

<span data-ttu-id="91222-148">Téléchargez la dernière version du Mixed Reality Feature Tool dans le [Centre de téléchargement Microsoft](https://aka.ms/MRFeatureTool). Une fois le téléchargement terminé, décompressez le fichier et enregistrez-le sur votre Bureau.</span><span class="sxs-lookup"><span data-stu-id="91222-148">Download the latest version of the Mixed Reality Feature Tool from the [Microsoft Download Center](https://aka.ms/MRFeatureTool), When the download is complete, unzip the file and save it to your desktop.</span></span>

> [!NOTE]
> <span data-ttu-id="91222-149">Avant de pouvoir exécuter le Mixed Reality Feature Tool, installez le [runtime .NET 5.0](https://dotnet.microsoft.com/download/dotnet/5.0).</span><span class="sxs-lookup"><span data-stu-id="91222-149">Before you can run the Mixed Reality Feature Tool please instal [.NET 5.0 runtime](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>

> [!NOTE]
> <span data-ttu-id="91222-150">Actuellement, le Mixed Reality Feature Tool s’exécute uniquement sur Windows. Pour MacOS, suivez la [procédure](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html#1-get-the-latest-mrtk-unity-packages) pour télécharger et importer le Mixed Reality Toolkit dans le projet Unity.</span><span class="sxs-lookup"><span data-stu-id="91222-150">The Mixed Reality Feature Tool currently only runs on Windows, For MacOS please follow this [procedure](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html#1-get-the-latest-mrtk-unity-packages) to download and import the Mixed Reality Toolkit into the unity project.</span></span>

<span data-ttu-id="91222-151">Ouvrez le fichier exécutable **MixedRealityFeatureTool** dans le dossier téléchargé pour lancer le Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="91222-151">Open the executable file **MixedRealityFeatureTool** from the downloaded folder to launch the Mixed Reality Feature Tool.</span></span>  

![Ouverture de MixedRealityFeatureTool](images/mr-learning-base/base-02-section4-step1-1.png)

<span data-ttu-id="91222-153">Une fois que vous avez ouvert **MixedRealityFeatureTool**, cliquez sur Start pour commencer à utiliser l’outil.</span><span class="sxs-lookup"><span data-stu-id="91222-153">Once **MixedRealityFeatureTool** is opened click on start to get started with Mixed Reality Feature Tool.</span></span>

![MixedRealityFeatureTool](images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="91222-155">Les fonctionnalités sont regroupées par catégorie pour faciliter leur recherche. Cliquez sur la liste déroulante **Mixed Reality Toolkit** pour trouver les packages qui lui sont associés.</span><span class="sxs-lookup"><span data-stu-id="91222-155">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>

![Fenêtre MixedRealityFeatureTool](images/mr-learning-base/base-02-section4-step1-3.png)

<span data-ttu-id="91222-157">Cochez la case correspondant à **Mixed Reality Toolkit Foundation**, puis cliquez sur la liste déroulante à côté pour sélectionner la version MRTK requise. Pour cette série de tutoriels, sélectionnez **2.5.3**.</span><span class="sxs-lookup"><span data-stu-id="91222-157">check the **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select the required MRTK version, for this tutorial series please select **2.5.3**.</span></span> <span data-ttu-id="91222-158">Cliquez ensuite sur le bouton **Get features** pour télécharger les packages sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="91222-158">then click on **Get features** button to download the selected packages.</span></span>

![Sélection de Mixed Reality Foundation](images/mr-learning-base/base-02-section4-step1-4.png)

<span data-ttu-id="91222-160">Le package sélectionné **Mixed Reality Toolkit Foundation 2.5.3** est présenté, ainsi que son package de dépendance **Mixed Reality Toolkit Standard Assets 2.5.3** dans la fenêtre **Import Features**.</span><span class="sxs-lookup"><span data-stu-id="91222-160">Selected package **Mixed Reality Toolkit Foundation 2.5.3** is presented, along with its dependence package **Mixed Reality Toolkit Standard Assets 2.5.3** in the **Import Features** window.</span></span>

<span data-ttu-id="91222-161">Vous devez également définir l’emplacement du projet Unity cible pour fournir le **chemin du projet**. Cliquez sur les **trois points** à côté du chemin du projet et accédez à votre dossier de projet dans l’Explorateur, par exemple _D:\MixedRealityLearning\Tutoriels MRTK_.</span><span class="sxs-lookup"><span data-stu-id="91222-161">You also need to set the location of the target unity project to provide the **Project path**, click on the **Three dots** next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

> [!NOTE]
> <span data-ttu-id="91222-162">La boîte de dialogue qui s’affiche quand vous recherchez le dossier du projet Unity contient « _ » comme nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="91222-162">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="91222-163">Une valeur doit être présente pour le nom de fichier pour permettre la sélection du dossier.</span><span class="sxs-lookup"><span data-stu-id="91222-163">There must be a value for the file name to enable the folder to be selected.</span></span>

<span data-ttu-id="91222-164">Cliquez ensuite sur le bouton **Validate** pour valider le package sélectionné. Vous voyez une fenêtre contextuelle avec le message **No validation issues were detected** (Aucun problème de validation détecté). Cliquez sur **OK** pour fermer la fenêtre contextuelle, puis cliquez sur le bouton **Import**.</span><span class="sxs-lookup"><span data-stu-id="91222-164">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

![Validation de Mixed Reality Foundation](images/mr-learning-base/base-02-section4-step1-5.png)

<span data-ttu-id="91222-166">Cliquez sur le bouton **Approve** pour ajouter **Mixed Reality Toolkit** au projet.</span><span class="sxs-lookup"><span data-stu-id="91222-166">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

![Approbation de Mixed Reality Foundation](images/mr-learning-base/base-02-section4-step1-6.png)

## <a name="configuring-the-unity-project"></a><span data-ttu-id="91222-168">Configuration du projet Unity</span><span class="sxs-lookup"><span data-stu-id="91222-168">Configuring the Unity project</span></span>

### <a name="1-apply-the-mrtk-project-configurator-settings"></a><span data-ttu-id="91222-169">1. Appliquer les paramètres du configurateur de projet MRTK</span><span class="sxs-lookup"><span data-stu-id="91222-169">1. Apply the MRTK Project Configurator settings</span></span>

<span data-ttu-id="91222-170">Une fois que Unity a fini d’importer le package de la section précédente, la fenêtre MRTK Project Configurator doit s’afficher.</span><span class="sxs-lookup"><span data-stu-id="91222-170">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="91222-171">Si ce n’est pas le cas, vous pouvez ouvrir manuellement en accédant à **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** :</span><span class="sxs-lookup"><span data-stu-id="91222-171">If it doesn't, you can manually open it by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**:</span></span>

![Chemin du menu Configure Unity Project d’Unity](images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="91222-173">Dans la fenêtre MRTK Project Configurator, développez la section **Modify Configurations**, vérifiez que toutes les options sont cochées, puis cliquez sur le bouton **Apply** pour appliquer les paramètres :</span><span class="sxs-lookup"><span data-stu-id="91222-173">In the MRTK Project Configurator window, expand the **Modify Configurations** section, ensure all options are checked, and click the **Apply** button to apply the settings:</span></span>

![Fenêtre MRTK Project Configurator d’Unity](images/mr-learning-base/base-02-section5-step1-2.png)

> [!TIP]
> <span data-ttu-id="91222-175">L’application des paramètres par défaut de MRTK est facultative mais fortement recommandée, car elle permet de configurer certains paramètres Unity recommandés :</span><span class="sxs-lookup"><span data-stu-id="91222-175">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="91222-176">Set Single Pass Instanced rendering path : Améliore les performances graphiques en exécutant le pipeline de rendu pour les deux yeux dans le même appel de dessin.</span><span class="sxs-lookup"><span data-stu-id="91222-176">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="91222-177">Pour plus d’informations à ce sujet, vous pouvez vous reporter à la section [Single-Pass Instanced rendering](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) de la documentation sur les [performances](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) de MRTK.</span><span class="sxs-lookup"><span data-stu-id="91222-177">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) section of MRTK's [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) documentation.</span></span>
> * <span data-ttu-id="91222-178">Définissez la couche de reconnaissance spatiale par défaut : Crée une couche Unity nommée Spatial Awareness et configure MRTK afin qu’il utilise cette couche pour le maillage de reconnaissance spatiale.</span><span class="sxs-lookup"><span data-stu-id="91222-178">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="91222-179">Pour plus d’informations sur les couches d’Unity, consultez la documentation <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Personnalisation de votre espace de travail</a>.</span><span class="sxs-lookup"><span data-stu-id="91222-179">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

### <a name="2-configure-additional-project-settings"></a><span data-ttu-id="91222-180">2. Configurer des paramètres de projet supplémentaires</span><span class="sxs-lookup"><span data-stu-id="91222-180">2. Configure additional project settings</span></span>

<span data-ttu-id="91222-181">Dans le menu Unity, sélectionnez **Modifier** > **Paramètres du projet...** pour ouvrir la fenêtre Paramètres du projet :</span><span class="sxs-lookup"><span data-stu-id="91222-181">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

<span data-ttu-id="91222-182">Dans la fenêtre Project Settings, sélectionnez **Player** > **XR Settings**, cochez la case **Virtual Reality Supported**, cliquez sur l’icône **+** et sélectionnez Windows Mixed Reality pour ajouter le SDK Windows Mixed Reality :</span><span class="sxs-lookup"><span data-stu-id="91222-182">In the Project Settings window, select **Player** > **XR Settings** and check the **Virual Reality Supported** checkbox then click the **+** icon, and select Windows Mixed Reality to add the Windows Mixed Reality SDK:</span></span>

![Paramètres XR d’Unity avec l’option d’ajout du SDK Windows Mixed Reality sélectionnée](images/mr-learning-base/base-02-section5-step2-4.png)

<span data-ttu-id="91222-184">Une fois que Unity a fini d’importer le SDK Windows Mixed Reality, la fenêtre MRTK Project Configurator doit réapparaître.</span><span class="sxs-lookup"><span data-stu-id="91222-184">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="91222-185">Si ce n’est pas le cas, vous pouvez l’ouvrir manuellement dans le menu Unity en accédant à **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**.</span><span class="sxs-lookup"><span data-stu-id="91222-185">If it doesn't, you can manually open it from the Unity menu by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**</span></span>

<span data-ttu-id="91222-186">Dans la fenêtre MRTK Project Configurator, utilisez la liste déroulante **Audio Spatializer** pour sélectionner le **MS HRTF Spatializer**, puis cliquez sur le bouton **Apply** pour appliquer le paramètre :</span><span class="sxs-lookup"><span data-stu-id="91222-186">In the MRTK Project Configurator window, use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![Paramètres XR d’Unity avec l’option d’ajout du SDK Windows Mixed Reality sélectionnée](images/mr-learning-base/base-02-section5-step2-5.png)

> [!TIP]
><span data-ttu-id="91222-188">La définition de la propriété Audio Spatializer est facultative mais peut améliorer l’expérience audio dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="91222-188">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="91222-189">Si vous la définissez sur MS HRTF Spatializer, ce plug-in Spatializer sera utilisé quand la propriété AudioSource.spatialize d’Unity est activée.</span><span class="sxs-lookup"><span data-stu-id="91222-189">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="91222-190">Pour plus d’informations sur ce sujet, vous pouvez consulter les <a href="https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">tutoriels d’audio spatiale</a>.</span><span class="sxs-lookup"><span data-stu-id="91222-190">To learn more about this topic, you can refer to the  <a href="https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="91222-191">Dans la fenêtre Project Settings, sélectionnez **Player** > **XR Settings**, puis utilisez la liste déroulante **Depth Format** pour sélectionner **16-bit depth** :</span><span class="sxs-lookup"><span data-stu-id="91222-191">In the Project Settings window, select **Player** > **XR Settings**, then use the **Depth Format** dropdown to select **16-bit depth**:</span></span>

![Unity - 16 Depth activé](images/mr-learning-base/base-02-section5-step2-6.png)

> [!TIP]
> <span data-ttu-id="91222-193">La réduction du format de la profondeur à 16 bits est facultative, mais peut aider à améliorer les performances graphiques dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="91222-193">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="91222-194">Pour plus d’informations à ce sujet, vous pouvez vous reporter à la section <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens" target="_blank">Depth buffer sharing (HoloLens)</a> de la documentation sur les <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html" target="_blank">performances</a> de MRTK.</span><span class="sxs-lookup"><span data-stu-id="91222-194">To learn more about this topic, you can refer to the   <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens" target="_blank">  Depth buffer sharing (HoloLens) </a> section of MRTK's  <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html" target="_blank"> Performance </a> documentation.</span></span>

<span data-ttu-id="91222-195">Dans la fenêtre Project Settings, sélectionnez **Player** > **Publishing Settings** puis, dans le champ **Package name**, entrez un nom approprié, par exemple _MRTKTutorials-GettingStarted_ :</span><span class="sxs-lookup"><span data-stu-id="91222-195">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Fenêtre Publishing Settings d’Unity avec le nom du package configuré](images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> <span data-ttu-id="91222-197">Le « Package name » est l’identificateur unique de l’application.</span><span class="sxs-lookup"><span data-stu-id="91222-197">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="91222-198">Vous devez changer cet identificateur avant de déployer l’application afin d’éviter de remplacer des applications déjà installées.</span><span class="sxs-lookup"><span data-stu-id="91222-198">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="91222-199">« Product Name » est le nom affiché dans le menu Démarrer de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="91222-199">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="91222-200">Pour faciliter la localisation de l’application pendant le développement, ajoutez un trait de soulignement devant le nom pour qu’il apparaisse en haut du classement.</span><span class="sxs-lookup"><span data-stu-id="91222-200">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

## <a name="creating-and-configuring-the-scene"></a><span data-ttu-id="91222-201">Création et configuration de la scène</span><span class="sxs-lookup"><span data-stu-id="91222-201">Creating and configuring the scene</span></span>

<span data-ttu-id="91222-202">Dans le menu Unity, sélectionnez **File** > **New Scene** pour créer une scène :</span><span class="sxs-lookup"><span data-stu-id="91222-202">In the Unity menu, select **File** > **New Scene** to create a new scene:</span></span>

![Unity - New Scene - Chemin du menu](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="91222-204">Dans le menu Unity, sélectionnez **Mixed Reality Toolkit** > **Add to Scene and Configure...** pour ajouter le MRTK à votre scène actuelle :</span><span class="sxs-lookup"><span data-stu-id="91222-204">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![Unity - Add to Scene and Configure... Chemin du menu](images/mr-learning-base/base-02-section6-step1-2.png)

<span data-ttu-id="91222-206">Une fois l’objet **MixedRealityToolkit** sélectionné dans la fenêtre Hierarchy, dans la fenêtre Inspector, vérifiez que le profil de configuration **MixedRealityToolkit** est défini sur **DefaultMixedRealityToolkitConfigurationProfile** :</span><span class="sxs-lookup"><span data-stu-id="91222-206">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, verify that the **MixedRealityToolkit** configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![Composant MixedRealityToolkit d’Unity avec DefaultMixedRealityTookitConfigurationProfile sélectionné](images/mr-learning-base/base-02-section6-step1-3.png)

<span data-ttu-id="91222-208">Dans le menu Unity, sélectionnez **Fichier** > **Enregistrer sous...** pour ouvrir la fenêtre Save Scene (Enregistrer la scène) :</span><span class="sxs-lookup"><span data-stu-id="91222-208">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![Unity - Save As... Chemin du menu](images/mr-learning-base/base-02-section6-step1-4.png)

<span data-ttu-id="91222-210">Dans la fenêtre Enregistrer la scène, accédez au dossier **Scènes** de votre projet, donnez à votre scène un nom approprié, par exemple _Démarrage_, puis cliquez sur le bouton **Enregistrer** pour enregistrer la scène :</span><span class="sxs-lookup"><span data-stu-id="91222-210">In the Save Scene window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _GettingStarted_, and click the **Save** button to save the scene:</span></span>

![Fenêtre d’invite Save d’Unity pour enregistrer la scène](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="91222-212">Génération de votre application sur votre HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="91222-212">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="91222-213">1. Générer le projet Unity</span><span class="sxs-lookup"><span data-stu-id="91222-213">1. Build the Unity project</span></span>

<span data-ttu-id="91222-214">Dans le menu Unity, sélectionnez **Fichier** > **Paramètres de build...** pour ouvrir la fenêtre Paramètres de build.</span><span class="sxs-lookup"><span data-stu-id="91222-214">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="91222-215">Dans la fenêtre Paramètres de build, cliquez sur le bouton **Add Open Scenes** (Ajouter des scènes ouvertes) pour ajouter votre scène actuelle à la liste **Scenes In Build** (Scènes dans la génération), puis cliquez sur le bouton **Générer** pour ouvrir la fenêtre de génération d’applications de plateforme Windows universelle :</span><span class="sxs-lookup"><span data-stu-id="91222-215">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![Fenêtre Build Settings d’Unity avec UWP sélectionné](images/mr-learning-base/base-02-section7-step1-1.png)

<span data-ttu-id="91222-217">Dans la fenêtre de génération d’applications de plateforme Windows universelle, choisissez un emplacement approprié pour stocker votre build, par exemple _D:\MixedRealityLearning\Builds_, créez un dossier et attribuez-lui un nom pertinent, par exemple _GettingStarted_, puis cliquez sur le bouton **Sélectionner un dossier** pour démarrer le processus de génération :</span><span class="sxs-lookup"><span data-stu-id="91222-217">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![Fenêtre Build Settings d’Unity avec la fenêtre d’invite Select Folder](images/mr-learning-base/base-02-section7-step1-2.png)

<span data-ttu-id="91222-219">Attendez qu’Unity termine le processus de génération :</span><span class="sxs-lookup"><span data-stu-id="91222-219">Wait for Unity to finish the build process:</span></span>

![Processus de génération Unity en cours](images/mr-learning-base/base-02-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="91222-221">2. Générer et déployer l’application</span><span class="sxs-lookup"><span data-stu-id="91222-221">2. Build and deploy the application</span></span>

<span data-ttu-id="91222-222">Une fois le processus de génération terminé, Unity invite l’Explorateur de fichiers Windows à ouvrir l’emplacement où vous avez stocké la build.</span><span class="sxs-lookup"><span data-stu-id="91222-222">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="91222-223">Naviguez dans le dossier, puis double-cliquez sur le fichier solution pour l’ouvrir dans Visual Studio :</span><span class="sxs-lookup"><span data-stu-id="91222-223">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![Explorateur Windows avec la solution Visual Studio nouvellement créée sélectionnée](images/mr-learning-base/base-02-section8-step1-1.png)

> [!NOTE]
> <span data-ttu-id="91222-225">Si Visual Studio vous demande d’installer de nouveaux composants, prenez un moment pour vérifier que vous avez tous les composants prérequis comme spécifié dans la documentation **[Installer les outils](../../install-the-tools.md)** .</span><span class="sxs-lookup"><span data-stu-id="91222-225">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="91222-226">Configurez Visual Studio pour HoloLens en sélectionnant la configuration **Master** ou **Release**, l’architecture **ARM64** et **Appareil** comme cible :</span><span class="sxs-lookup"><span data-stu-id="91222-226">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![Visual Studio configuré pour le déploiement sur HoloLens 2](images/mr-learning-base/base-02-section8-step1-2.png)

> [!TIP]
> <span data-ttu-id="91222-228">Si vous effectuez un déploiement sur HoloLens (1ère génération), sélectionnez l’architecture **x86**.</span><span class="sxs-lookup"><span data-stu-id="91222-228">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="91222-229">En général, pour HoloLens, vous allez générer pour l’architecture ARM.</span><span class="sxs-lookup"><span data-stu-id="91222-229">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="91222-230">Il y a cependant un <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>problème connu</strong></a> dans Unity 2019.3 qui provoque des erreurs lors de la sélection de ARM comme architecture de génération dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="91222-230">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="91222-231">La solution de contournement recommandée est de générer pour ARM64.</span><span class="sxs-lookup"><span data-stu-id="91222-231">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="91222-232">Si ce n’est pas possible, accédez à **Modifier > Paramètres du projet > Lecteur > Autres paramètres** et désactivez **Travaux graphiques**.</span><span class="sxs-lookup"><span data-stu-id="91222-232">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="91222-233">Si vous ne voyez pas Appareil comme choix de cible, il peut être nécessaire de changer le projet de démarrage pour la solution Visual Studio de Projet IL2CPP en Projet UWP.</span><span class="sxs-lookup"><span data-stu-id="91222-233">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="91222-234">Pour cela, dans l’Explorateur de solutions, cliquez avec le bouton droit sur nom_de_votre_projet (Windows universel), puis sélectionnez **Définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="91222-234">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="91222-235">Connectez votre HoloLens à votre ordinateur, puis sélectionnez **Déboguer** > **Démarrer sans débogage** pour générer et déployer sur votre appareil :</span><span class="sxs-lookup"><span data-stu-id="91222-235">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![Visual Studio - Chemin du menu Démarrer sans débogage](images/mr-learning-base/base-02-section8-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="91222-237">Avant d’effectuer la génération sur votre appareil, celui-ci doit être en mode développeur et associé à votre ordinateur de développement.</span><span class="sxs-lookup"><span data-stu-id="91222-237">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="91222-238">Vous pouvez effectuer ces deux étapes en suivant [ces instructions](../../platform-capabilities-and-apis/using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="91222-238">Both of these steps can be completed by following [these instructions](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="91222-239">Vous pouvez aussi déployer sur l’[émulateur HoloLens](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) ou créer un [package d’application](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) pour un chargement indépendant (sideloading).</span><span class="sxs-lookup"><span data-stu-id="91222-239">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="91222-240">L’utilisation de Démarrer sans débogage démarre automatiquement l’application sur votre appareil sans le débogueur Visual Studio attaché.</span><span class="sxs-lookup"><span data-stu-id="91222-240">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="91222-241">Sélectionnez **Générer > Déployer la solution** pour déployer sur votre appareil sans que l’application ne démarre automatiquement.</span><span class="sxs-lookup"><span data-stu-id="91222-241">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="91222-242">Vous remarquerez peut-être le profileur de diagnostics dans l’application, que vous pouvez activer ou désactiver avec la commande vocale **Toggle Diagnostics**.</span><span class="sxs-lookup"><span data-stu-id="91222-242">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="91222-243">Il est recommandé de garder le profileur visible la plupart du temps pendant le développement, de façon à comprendre quand des modifications apportées à l’application peuvent avoir un impact sur les performances.</span><span class="sxs-lookup"><span data-stu-id="91222-243">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="91222-244">Par exemple, les applications HoloLens doivent [s’exécuter en continu à 60 images/s](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="91222-244">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="91222-245">Félicitations</span><span class="sxs-lookup"><span data-stu-id="91222-245">Congratulations</span></span>

<span data-ttu-id="91222-246">Vous avez maintenant déployé votre première application HoloLens.</span><span class="sxs-lookup"><span data-stu-id="91222-246">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="91222-247">À mesure que vous vous déplacez, vous devez voir un maillage de mappage spatial couvrant les surfaces qui sont perçues par HoloLens.</span><span class="sxs-lookup"><span data-stu-id="91222-247">As you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="91222-248">En outre, vous devez voir des indicateurs sur vos mains et doigts pour le suivi de la main et un compteur de fréquence d’images pour vous tenir informé des performances de l’application.</span><span class="sxs-lookup"><span data-stu-id="91222-248">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="91222-249">Ces fonctionnalités sont simplement quelques composants fondamentaux inclus avec MRTK.</span><span class="sxs-lookup"><span data-stu-id="91222-249">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="91222-250">Dans les tutoriels à venir, vous allez ajouter du contenu à votre scène pour explorer les fonctionnalités HoloLens et MRTK.</span><span class="sxs-lookup"><span data-stu-id="91222-250">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="91222-251">Tutoriel suivant : 3. Configuration des profils MRTK</span><span class="sxs-lookup"><span data-stu-id="91222-251">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
