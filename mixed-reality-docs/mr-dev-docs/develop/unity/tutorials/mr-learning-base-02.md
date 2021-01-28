---
title: Initialisation de votre projet et déploiement de votre première application
description: Ce cours vous montre comment configurer votre projet Unity pour le MRTK (Mixed Reality Toolkit) et comment le déployer sur votre HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, MRTK, mixed reality toolkit, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: 4d82d0974a0a797e7f8d2de2d4943666f7d32a4f
ms.sourcegitcommit: 04927427226928bd9178da0049d4cef626a6b0bf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98635494"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="cd114-104">2. Initialisation de votre projet et déploiement de votre première application</span><span class="sxs-lookup"><span data-stu-id="cd114-104">2. Initializing your project and deploying your first application</span></span>

<span data-ttu-id="cd114-105">Dans ce tutoriel, vous allez apprendre à créer un nouveau projet Unity, à le configurer pour le développement <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">MRTK (Mixed Reality Toolkit)</a> et à importer MRTK.</span><span class="sxs-lookup"><span data-stu-id="cd114-105">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="cd114-106">Vous allez également effectuer la configuration, la génération et le déploiement d’une scène Unity de base depuis Visual Studio sur votre HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="cd114-106">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="cd114-107">Une fois que l’avez déployée sur votre HoloLens 2, vous devez voir un maillage de mappage spatial couvrant les surfaces qui sont perçues par HoloLens.</span><span class="sxs-lookup"><span data-stu-id="cd114-107">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="cd114-108">En outre, vous devez voir des indicateurs sur vos mains et doigts pour le suivi de la main et un compteur de fréquence d’images pour vous tenir informé des performances de l’application.</span><span class="sxs-lookup"><span data-stu-id="cd114-108">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

## <a name="objectives"></a><span data-ttu-id="cd114-109">Objectifs</span><span class="sxs-lookup"><span data-stu-id="cd114-109">Objectives</span></span>

* <span data-ttu-id="cd114-110">Apprendre à configurer Unity pour le développement HoloLens</span><span class="sxs-lookup"><span data-stu-id="cd114-110">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="cd114-111">Apprendre à créer et déployer votre application sur HoloLens</span><span class="sxs-lookup"><span data-stu-id="cd114-111">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="cd114-112">Expérimenter le maillage du mappage spatial, les maillages de la main et le compteur de fréquence d’images sur un appareil HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="cd114-112">Experience the spatial mapping mesh, hand meshes, and the framerate counter on HoloLens 2 device</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="cd114-113">Création du projet Unity</span><span class="sxs-lookup"><span data-stu-id="cd114-113">Creating the Unity project</span></span>

<span data-ttu-id="cd114-114">Lancez **Unity Hub**, sélectionnez l’onglet **Projets**, puis cliquez sur la **flèche bas** en regard du bouton **Nouveau** :</span><span class="sxs-lookup"><span data-stu-id="cd114-114">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![Unity Hub avec le bouton New mis en évidence](images/mr-learning-base/base-02-section1-step1-1.png)

<span data-ttu-id="cd114-116">Dans la liste déroulante, sélectionnez la **version** Unity spécifiée dans les [prérequis](mr-learning-base-01.md#prerequisites) :</span><span class="sxs-lookup"><span data-stu-id="cd114-116">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![Unity Hub avec la liste déroulante du sélecteur de version NEW](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="cd114-118">Si cette version spécifique d’Unity n’est pas disponible dans Unity Hub, vous pouvez lancer l’installation à partir de la page <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Unity download archive</a>.</span><span class="sxs-lookup"><span data-stu-id="cd114-118">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="cd114-119">Dans la fenêtre Créer un projet :</span><span class="sxs-lookup"><span data-stu-id="cd114-119">In the Create a new project window:</span></span>

* <span data-ttu-id="cd114-120">Vérifiez que **Modèles** est défini sur **3D**</span><span class="sxs-lookup"><span data-stu-id="cd114-120">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="cd114-121">Entrez un **Nom du projet** approprié, par exemple _Tutoriels MRTK_</span><span class="sxs-lookup"><span data-stu-id="cd114-121">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="cd114-122">Choisissez un **Emplacement** approprié pour stocker votre projet, par exemple _D:\MixedRealityLearning_</span><span class="sxs-lookup"><span data-stu-id="cd114-122">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="cd114-123">Cliquez sur le bouton **Créer** pour créer et lancer votre nouveau projet Unity</span><span class="sxs-lookup"><span data-stu-id="cd114-123">Click the **Create** button to create and launch your new Unity project</span></span>

![Unity Hub avec la fenêtre Create a new project renseignée](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="cd114-125">Quand vous utilisez Windows, il existe une limite de 255 caractères pour MAX_PATH.</span><span class="sxs-lookup"><span data-stu-id="cd114-125">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="cd114-126">Par conséquent, vous devez enregistrer le projet Unity près de la racine du lecteur.</span><span class="sxs-lookup"><span data-stu-id="cd114-126">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="cd114-127">Attendez qu’Unity crée le projet :</span><span class="sxs-lookup"><span data-stu-id="cd114-127">Wait for Unity to create the project:</span></span>

![Création du nouveau projet Unity en cours](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="cd114-129">Changement de plateforme de génération</span><span class="sxs-lookup"><span data-stu-id="cd114-129">Switching the build platform</span></span>

<span data-ttu-id="cd114-130">Dans le menu Unity, sélectionnez **Fichier** > **Paramètres de build...** pour ouvrir la fenêtre Paramètres de build :</span><span class="sxs-lookup"><span data-stu-id="cd114-130">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Unity - Build Settings... Chemin du menu](images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="cd114-132">Dans la fenêtre Paramètres de build, sélectionnez **Plateforme Windows universelle** , puis cliquez sur le bouton **Switch Platform** (Changer de plateforme) :</span><span class="sxs-lookup"><span data-stu-id="cd114-132">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![Fenêtre Build Setting d’Unity avec UWP sélectionné comme nouvelle plateforme, qui était auparavant Standalone](images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="cd114-134">Attendez qu’Unity termine le changement de plateforme :</span><span class="sxs-lookup"><span data-stu-id="cd114-134">Wait for Unity to finish switching the platform:</span></span>

![Unity - Changement de plateforme en cours](images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="cd114-136">Quand Unity a terminé le changement de plateforme, cliquez sur l’icône **x** rouge pour fermer la fenêtre Paramètres de build :</span><span class="sxs-lookup"><span data-stu-id="cd114-136">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![Fenêtre Build d’Unity avec l’icône Fermer mise en évidence](images/mr-learning-base/base-02-section2-step1-4.png)

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="cd114-138">Importation des ressources TextMeshPro Essential</span><span class="sxs-lookup"><span data-stu-id="cd114-138">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="cd114-139">Dans le menu Unity, sélectionnez **Window** > **TextMeshPro** > **Import TMP Essential Resources** pour ouvrir la fenêtre Import Unity Package :</span><span class="sxs-lookup"><span data-stu-id="cd114-139">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources** to open the Import Unity Package window:</span></span>

![Chemin du menu Import TMP Essential Resources d’Unity](images/mr-learning-base/base-02-section3-step1-1.png)

<span data-ttu-id="cd114-141">Dans la fenêtre Import Unity Package (Importer un package Unity), cliquez sur le bouton **Tous** pour vous assurer que toutes les ressources sont sélectionnées, puis sur le bouton **Importer** pour importer les ressources :</span><span class="sxs-lookup"><span data-stu-id="cd114-141">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Fenêtre d’importation des ressources essentielles TMP d’Unity](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="cd114-143">Les ressources TextMeshPro Essential sont requises par les éléments de l’interface utilisateur de MRTK.</span><span class="sxs-lookup"><span data-stu-id="cd114-143">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="cd114-144">Vous pouvez ignorer cette étape si vous ne prévoyez pas d’utiliser des éléments de l’interface utilisateur de MRTK dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="cd114-144">You can skip this step if you are not planning to use MRTK's UI elements in your project.</span></span>

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="cd114-145">Importation du Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="cd114-145">Importing the Mixed Reality Toolkit</span></span>

<span data-ttu-id="cd114-146">Téléchargez le package personnalisé Unity :</span><span class="sxs-lookup"><span data-stu-id="cd114-146">Download the Unity custom package:</span></span>

* [<span data-ttu-id="cd114-147">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="cd114-147">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.5.1/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage)

<span data-ttu-id="cd114-148">Dans le menu Unity, sélectionnez **Ressources** > **Importer un package** > **Custom Package...** (Package personnalisé) pour ouvrir la fenêtre Importer un package... :</span><span class="sxs-lookup"><span data-stu-id="cd114-148">In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![Unity - Importation - Custom Package... Chemin du menu](images/mr-learning-base/base-02-section4-step1-1.png)

<span data-ttu-id="cd114-150">Dans la fenêtre Import package..., sélectionnez le package **osoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage** que vous avez téléchargé, puis cliquez sur le bouton **Open** :</span><span class="sxs-lookup"><span data-stu-id="cd114-150">In the Import package... window, select the **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage** you downloaded and click the **Open** button:</span></span>

![Unity - Importation - Custom Package avec une fenêtre d’invite Open](images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="cd114-152">Dans la fenêtre Import Unity Package (Importer un package Unity), cliquez sur le bouton **Tous** pour vous assurer que toutes les ressources sont sélectionnées, puis sur le bouton **Importer** pour importer les ressources :</span><span class="sxs-lookup"><span data-stu-id="cd114-152">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Fenêtre d’importation MRTK Foundation d’Unity](images/mr-learning-base/base-02-section4-step1-3.png)

## <a name="configuring-the-unity-project"></a><span data-ttu-id="cd114-154">Configuration du projet Unity</span><span class="sxs-lookup"><span data-stu-id="cd114-154">Configuring the Unity project</span></span>

### <a name="1-apply-the-mrtk-project-configurator-settings"></a><span data-ttu-id="cd114-155">1. Appliquer les paramètres du configurateur de projet MRTK</span><span class="sxs-lookup"><span data-stu-id="cd114-155">1. Apply the MRTK Project Configurator settings</span></span>

<span data-ttu-id="cd114-156">Une fois que Unity a fini d’importer le package de la section précédente, la fenêtre MRTK Project Configurator doit s’afficher.</span><span class="sxs-lookup"><span data-stu-id="cd114-156">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="cd114-157">Si ce n’est pas le cas, vous pouvez ouvrir manuellement en accédant à **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** :</span><span class="sxs-lookup"><span data-stu-id="cd114-157">If it doesn't, you can manually open it by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**:</span></span>

![Chemin du menu Configure Unity Project d’Unity](images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="cd114-159">Dans la fenêtre MRTK Project Configurator, développez la section **Modify Configurations**, vérifiez que toutes les options sont cochées, puis cliquez sur le bouton **Apply** pour appliquer les paramètres :</span><span class="sxs-lookup"><span data-stu-id="cd114-159">In the MRTK Project Configurator window, expand the **Modify Configurations** section, ensure all options are checked, and click the **Apply** button to apply the settings:</span></span>

![Fenêtre MRTK Project Configurator d’Unity](images/mr-learning-base/base-02-section5-step1-2.png)

> [!TIP]
> <span data-ttu-id="cd114-161">L’application des paramètres par défaut de MRTK est facultative mais fortement recommandée, car elle permet de configurer certains paramètres Unity recommandés :</span><span class="sxs-lookup"><span data-stu-id="cd114-161">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="cd114-162">Set Single Pass Instanced rendering path : Améliore les performances graphiques en exécutant le pipeline de rendu pour les deux yeux dans le même appel de dessin.</span><span class="sxs-lookup"><span data-stu-id="cd114-162">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="cd114-163">Pour plus d’informations à ce sujet, vous pouvez vous reporter à la section [Single-Pass Instanced rendering](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) de la documentation sur les [performances](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) de MRTK.</span><span class="sxs-lookup"><span data-stu-id="cd114-163">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) section of MRTK's [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) documentation.</span></span>
> * <span data-ttu-id="cd114-164">Définissez la couche de reconnaissance spatiale par défaut : Crée une couche Unity nommée Spatial Awareness et configure MRTK afin qu’il utilise cette couche pour le maillage de reconnaissance spatiale.</span><span class="sxs-lookup"><span data-stu-id="cd114-164">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="cd114-165">Pour plus d’informations sur les couches d’Unity, consultez la documentation <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Personnalisation de votre espace de travail</a>.</span><span class="sxs-lookup"><span data-stu-id="cd114-165">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

### <a name="2-configure-additional-project-settings"></a><span data-ttu-id="cd114-166">2. Configurer des paramètres de projet supplémentaires</span><span class="sxs-lookup"><span data-stu-id="cd114-166">2. Configure additional project settings</span></span>

<span data-ttu-id="cd114-167">Dans le menu Unity, sélectionnez **Modifier** > **Paramètres du projet...** pour ouvrir la fenêtre Paramètres du projet :</span><span class="sxs-lookup"><span data-stu-id="cd114-167">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![Unity - Project Settings... Chemin du menu](images/mr-learning-base/base-02-section5-step2-1.png)

<span data-ttu-id="cd114-169">Dans la fenêtre Project Settings, sélectionnez **XR Plug-in Managemen** > **Install XR Plug-in Management** pour installer XR Plug-in Management :</span><span class="sxs-lookup"><span data-stu-id="cd114-169">In the Project Settings window, select **XR Plug-in Management** > **Install XR Plug-in Management**, to install XR Plug-in Management:</span></span>

![Fenêtre Publishing Settings d’Unity avec le nom du package configuré](images/mr-learning-base/base-02-section5-step2-2.png)

<span data-ttu-id="cd114-171">quand Unity a terminé l’installation de XR Plug-in Management.</span><span class="sxs-lookup"><span data-stu-id="cd114-171">after Unity has finished installing the XR Plug-in Management.</span></span> <span data-ttu-id="cd114-172">Vérifiez que vous êtes dans les paramètres de Plateforme Windows universelle et cochez la case Initialize XR on Startup.</span><span class="sxs-lookup"><span data-stu-id="cd114-172">Ensure that you are in Universal Windows Platform settings and Check the Initialize XR on Startup.</span></span>

![Unity configurant XR Plug-in Management](images/mr-learning-base/base-02-section5-step2-3.png)

<span data-ttu-id="cd114-174">Dans la fenêtre Project Settings, sélectionnez **Player** > **XR Settings**, cliquez sur l’icône **+** et sélectionnez Windows Mixed Reality pour ajouter le SDK Windows Mixed Reality :</span><span class="sxs-lookup"><span data-stu-id="cd114-174">In the Project Settings window, select **Player** > **XR Settings**, click the **+** icon, and select Windows Mixed Reality to add the Windows Mixed Reality SDK:</span></span>

![Paramètres XR d’Unity avec l’option d’ajout du SDK Windows Mixed Reality sélectionnée](images/mr-learning-base/base-02-section5-step2-4.png)

<span data-ttu-id="cd114-176">Une fois que Unity a fini d’importer le SDK Windows Mixed Reality, la fenêtre MRTK Project Configurator doit réapparaître.</span><span class="sxs-lookup"><span data-stu-id="cd114-176">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="cd114-177">Si ce n’est pas le cas, utilisez le menu Unity pour l’ouvrir.</span><span class="sxs-lookup"><span data-stu-id="cd114-177">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="cd114-178">Dans la fenêtre MRTK Project Configurator, utilisez la liste déroulante **Audio Spatializer** pour sélectionner le **MS HRTF Spatializer**, puis cliquez sur le bouton **Apply** pour appliquer le paramètre :</span><span class="sxs-lookup"><span data-stu-id="cd114-178">In the MRTK Project Configurator window, use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![Paramètres XR d’Unity avec l’option d’ajout du SDK Windows Mixed Reality sélectionnée](images/mr-learning-base/base-02-section5-step2-5.png)

> [!TIP]
><span data-ttu-id="cd114-180">La définition de la propriété Audio Spatializer est facultative mais peut améliorer l’expérience audio dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="cd114-180">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="cd114-181">Si vous la définissez sur MS HRTF Spatializer, ce plug-in Spatializer sera utilisé quand la propriété AudioSource.spatialize d’Unity est activée.</span><span class="sxs-lookup"><span data-stu-id="cd114-181">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="cd114-182">Pour plus d’informations sur ce sujet, vous pouvez consulter les <a href="https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">tutoriels d’audio spatiale</a>.</span><span class="sxs-lookup"><span data-stu-id="cd114-182">To learn more about this topic, you can refer to the  <a href="https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="cd114-183">Dans la fenêtre Project Settings, sélectionnez **Player** > **XR Settings**, puis utilisez la liste déroulante **Depth Format** pour sélectionner **16-bit depth** :</span><span class="sxs-lookup"><span data-stu-id="cd114-183">In the Project Settings window, select **Player** > **XR Settings**, then use the **Depth Format** dropdown to select **16-bit depth**:</span></span>

![Unity - 16 Depth activé](images/mr-learning-base/base-02-section5-step2-6.png)

> [!TIP]
> <span data-ttu-id="cd114-185">La réduction du format de la profondeur à 16 bits est facultative, mais peut aider à améliorer les performances graphiques dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="cd114-185">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="cd114-186">Pour plus d’informations à ce sujet, vous pouvez vous reporter à la section <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens" target="_blank">Depth buffer sharing (HoloLens)</a> de la documentation sur les <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html" target="_blank">performances</a> de MRTK.</span><span class="sxs-lookup"><span data-stu-id="cd114-186">To learn more about this topic, you can refer to the   <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens" target="_blank">  Depth buffer sharing (HoloLens) </a> section of MRTK's  <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html" target="_blank"> Performance </a> documentation.</span></span>

<span data-ttu-id="cd114-187">Dans la fenêtre Project Settings, sélectionnez **Player** > **Publishing Settings** puis, dans le champ **Package name**, entrez un nom approprié, par exemple _MRTKTutorials-GettingStarted_ :</span><span class="sxs-lookup"><span data-stu-id="cd114-187">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Fenêtre Publishing Settings d’Unity avec le nom du package configuré](images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> <span data-ttu-id="cd114-189">Le « Package name » est l’identificateur unique de l’application.</span><span class="sxs-lookup"><span data-stu-id="cd114-189">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="cd114-190">Vous devez changer cet identificateur avant de déployer l’application afin d’éviter de remplacer des applications déjà installées.</span><span class="sxs-lookup"><span data-stu-id="cd114-190">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="cd114-191">« Product Name » est le nom affiché dans le menu Démarrer de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="cd114-191">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="cd114-192">Pour faciliter la localisation de l’application pendant le développement, ajoutez un trait de soulignement devant le nom pour qu’il apparaisse en haut du classement.</span><span class="sxs-lookup"><span data-stu-id="cd114-192">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

## <a name="creating-and-configuring-the-scene"></a><span data-ttu-id="cd114-193">Création et configuration de la scène</span><span class="sxs-lookup"><span data-stu-id="cd114-193">Creating and configuring the scene</span></span>

<span data-ttu-id="cd114-194">Dans le menu Unity, sélectionnez **File** > **New Scene** pour créer une scène :</span><span class="sxs-lookup"><span data-stu-id="cd114-194">In the Unity menu, select **File** > **New Scene** to create a new scene:</span></span>

![Unity - New Scene - Chemin du menu](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="cd114-196">Dans le menu Unity, sélectionnez **Mixed Reality Toolkit** > **Add to Scene and Configure...** pour ajouter le MRTK à votre scène actuelle :</span><span class="sxs-lookup"><span data-stu-id="cd114-196">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![Unity - Add to Scene and Configure... Chemin du menu](images/mr-learning-base/base-02-section6-step1-2.png)

<span data-ttu-id="cd114-198">Une fois l’objet **MixedRealityToolkit** sélectionné dans la fenêtre Hierarchy, dans la fenêtre Inspector, vérifiez que le profil de configuration **MixedRealityToolkit** est défini sur **DefaultMixedRealityToolkitConfigurationProfile** :</span><span class="sxs-lookup"><span data-stu-id="cd114-198">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, verify that the **MixedRealityToolkit** configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![Composant MixedRealityToolkit d’Unity avec DefaultMixedRealityTookitConfigurationProfile sélectionné](images/mr-learning-base/base-02-section6-step1-3.png)

<span data-ttu-id="cd114-200">Dans le menu Unity, sélectionnez **Fichier** > **Enregistrer sous...** pour ouvrir la fenêtre Save Scene (Enregistrer la scène) :</span><span class="sxs-lookup"><span data-stu-id="cd114-200">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![Unity - Save As... Chemin du menu](images/mr-learning-base/base-02-section6-step1-4.png)

<span data-ttu-id="cd114-202">Dans la fenêtre Enregistrer la scène, accédez au dossier **Scènes** de votre projet, donnez à votre scène un nom approprié, par exemple _Démarrage_, puis cliquez sur le bouton **Enregistrer** pour enregistrer la scène :</span><span class="sxs-lookup"><span data-stu-id="cd114-202">In the Save Scene window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _GettingStarted_, and click the **Save** button to save the scene:</span></span>

![Fenêtre d’invite Save d’Unity pour enregistrer la scène](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="cd114-204">Génération de votre application sur votre HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="cd114-204">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="cd114-205">1. Générer le projet Unity</span><span class="sxs-lookup"><span data-stu-id="cd114-205">1. Build the Unity project</span></span>

<span data-ttu-id="cd114-206">Dans le menu Unity, sélectionnez **Fichier** > **Paramètres de build...** pour ouvrir la fenêtre Paramètres de build.</span><span class="sxs-lookup"><span data-stu-id="cd114-206">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="cd114-207">Dans la fenêtre Paramètres de build, cliquez sur le bouton **Add Open Scenes** (Ajouter des scènes ouvertes) pour ajouter votre scène actuelle à la liste **Scenes In Build** (Scènes dans la génération), puis cliquez sur le bouton **Générer** pour ouvrir la fenêtre de génération d’applications de plateforme Windows universelle :</span><span class="sxs-lookup"><span data-stu-id="cd114-207">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![Fenêtre Build Settings d’Unity avec UWP sélectionné](images/mr-learning-base/base-02-section7-step1-1.png)

<span data-ttu-id="cd114-209">Dans la fenêtre de génération d’applications de plateforme Windows universelle, choisissez un emplacement approprié pour stocker votre build, par exemple _D:\MixedRealityLearning\Builds_, créez un dossier et attribuez-lui un nom pertinent, par exemple _GettingStarted_, puis cliquez sur le bouton **Sélectionner un dossier** pour démarrer le processus de génération :</span><span class="sxs-lookup"><span data-stu-id="cd114-209">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![Fenêtre Build Settings d’Unity avec la fenêtre d’invite Select Folder](images/mr-learning-base/base-02-section7-step1-2.png)

<span data-ttu-id="cd114-211">Attendez qu’Unity termine le processus de génération :</span><span class="sxs-lookup"><span data-stu-id="cd114-211">Wait for Unity to finish the build process:</span></span>

![Processus de génération Unity en cours](images/mr-learning-base/base-02-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="cd114-213">2. Générer et déployer l’application</span><span class="sxs-lookup"><span data-stu-id="cd114-213">2. Build and deploy the application</span></span>

<span data-ttu-id="cd114-214">Une fois le processus de génération terminé, Unity invite l’Explorateur de fichiers Windows à ouvrir l’emplacement où vous avez stocké la build.</span><span class="sxs-lookup"><span data-stu-id="cd114-214">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="cd114-215">Naviguez dans le dossier, puis double-cliquez sur le fichier solution pour l’ouvrir dans Visual Studio :</span><span class="sxs-lookup"><span data-stu-id="cd114-215">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![Explorateur Windows avec la solution Visual Studio nouvellement créée sélectionnée](images/mr-learning-base/base-02-section8-step1-1.png)

> [!NOTE]
> <span data-ttu-id="cd114-217">Si Visual Studio vous demande d’installer de nouveaux composants, prenez un moment pour vérifier que vous avez tous les composants prérequis comme spécifié dans la documentation **[Installer les outils](../../install-the-tools.md)** .</span><span class="sxs-lookup"><span data-stu-id="cd114-217">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="cd114-218">Configurez Visual Studio pour HoloLens en sélectionnant la configuration **Master** ou **Release**, l’architecture **ARM64** et **Appareil** comme cible :</span><span class="sxs-lookup"><span data-stu-id="cd114-218">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![Visual Studio configuré pour le déploiement sur HoloLens 2](images/mr-learning-base/base-02-section8-step1-2.png)

> [!TIP]
> <span data-ttu-id="cd114-220">Si vous effectuez un déploiement sur HoloLens (1ère génération), sélectionnez l’architecture **x86**.</span><span class="sxs-lookup"><span data-stu-id="cd114-220">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="cd114-221">En général, pour HoloLens, vous allez générer pour l’architecture ARM.</span><span class="sxs-lookup"><span data-stu-id="cd114-221">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="cd114-222">Il y a cependant un <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>problème connu</strong></a> dans Unity 2019.3 qui provoque des erreurs lors de la sélection de ARM comme architecture de génération dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cd114-222">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="cd114-223">La solution de contournement recommandée est de générer pour ARM64.</span><span class="sxs-lookup"><span data-stu-id="cd114-223">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="cd114-224">Si ce n’est pas possible, accédez à **Modifier > Paramètres du projet > Lecteur > Autres paramètres** et désactivez **Travaux graphiques**.</span><span class="sxs-lookup"><span data-stu-id="cd114-224">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="cd114-225">Si vous ne voyez pas Appareil comme choix de cible, il peut être nécessaire de changer le projet de démarrage pour la solution Visual Studio de Projet IL2CPP en Projet UWP.</span><span class="sxs-lookup"><span data-stu-id="cd114-225">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="cd114-226">Pour cela, dans l’Explorateur de solutions, cliquez avec le bouton droit sur nom_de_votre_projet (Windows universel), puis sélectionnez **Définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="cd114-226">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="cd114-227">Connectez votre HoloLens à votre ordinateur, puis sélectionnez **Déboguer** > **Démarrer sans débogage** pour générer et déployer sur votre appareil :</span><span class="sxs-lookup"><span data-stu-id="cd114-227">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![Visual Studio - Chemin du menu Démarrer sans débogage](images/mr-learning-base/base-02-section8-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="cd114-229">Avant d’effectuer la génération sur votre appareil, celui-ci doit être en mode développeur et associé à votre ordinateur de développement.</span><span class="sxs-lookup"><span data-stu-id="cd114-229">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="cd114-230">Vous pouvez effectuer ces deux étapes en suivant [ces instructions](../../platform-capabilities-and-apis/using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="cd114-230">Both of these steps can be completed by following [these instructions](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="cd114-231">Vous pouvez aussi déployer sur l’[émulateur HoloLens](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) ou créer un [package d’application](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) pour un chargement indépendant (sideloading).</span><span class="sxs-lookup"><span data-stu-id="cd114-231">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="cd114-232">L’utilisation de Démarrer sans débogage démarre automatiquement l’application sur votre appareil sans le débogueur Visual Studio attaché.</span><span class="sxs-lookup"><span data-stu-id="cd114-232">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="cd114-233">Sélectionnez **Générer > Déployer la solution** pour déployer sur votre appareil sans que l’application ne démarre automatiquement.</span><span class="sxs-lookup"><span data-stu-id="cd114-233">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="cd114-234">Vous remarquerez peut-être le profileur de diagnostics dans l’application, que vous pouvez activer ou désactiver avec la commande vocale **Toggle Diagnostics**.</span><span class="sxs-lookup"><span data-stu-id="cd114-234">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="cd114-235">Il est recommandé de garder le profileur visible la plupart du temps pendant le développement, de façon à comprendre quand des modifications apportées à l’application peuvent avoir un impact sur les performances.</span><span class="sxs-lookup"><span data-stu-id="cd114-235">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="cd114-236">Par exemple, les applications HoloLens doivent [s’exécuter en continu à 60 images/s](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="cd114-236">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="cd114-237">Félicitations</span><span class="sxs-lookup"><span data-stu-id="cd114-237">Congratulations</span></span>

<span data-ttu-id="cd114-238">Vous avez maintenant déployé votre première application HoloLens.</span><span class="sxs-lookup"><span data-stu-id="cd114-238">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="cd114-239">À mesure que vous vous déplacez, vous devez voir un maillage de mappage spatial couvrant les surfaces qui sont perçues par HoloLens.</span><span class="sxs-lookup"><span data-stu-id="cd114-239">As you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="cd114-240">En outre, vous devez voir des indicateurs sur vos mains et doigts pour le suivi de la main et un compteur de fréquence d’images pour vous tenir informé des performances de l’application.</span><span class="sxs-lookup"><span data-stu-id="cd114-240">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="cd114-241">Ces fonctionnalités sont simplement quelques composants fondamentaux inclus avec MRTK.</span><span class="sxs-lookup"><span data-stu-id="cd114-241">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="cd114-242">Dans les tutoriels à venir, vous allez ajouter du contenu à votre scène pour explorer les fonctionnalités HoloLens et MRTK.</span><span class="sxs-lookup"><span data-stu-id="cd114-242">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cd114-243">Tutoriel suivant : 3. Configuration des profils MRTK</span><span class="sxs-lookup"><span data-stu-id="cd114-243">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)