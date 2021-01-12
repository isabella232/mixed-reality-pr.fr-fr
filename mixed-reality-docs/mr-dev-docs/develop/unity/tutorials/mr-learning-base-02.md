---
title: Initialisation de votre projet et déploiement de votre première application
description: Ce cours vous montre comment configurer votre projet Unity pour le MRTK (Mixed Reality Toolkit) et comment le déployer sur votre HoloLens 2.
author: jessemcculloch
ms.author: v-vtieto
ms.date: 12/30/2020
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, MRTK, mixed reality toolkit, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: 2ce119e1dd18eacf02088d00e99fb70d06bf956e
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008219"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="2597a-104">2. Initialisation de votre projet et déploiement de votre première application</span><span class="sxs-lookup"><span data-stu-id="2597a-104">2. Initializing your project and deploying your first application</span></span>

<span data-ttu-id="2597a-105">Dans ce tutoriel, vous allez apprendre à créer un nouveau projet Unity, à le configurer pour le développement <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">MRTK (Mixed Reality Toolkit)</a> et à importer MRTK.</span><span class="sxs-lookup"><span data-stu-id="2597a-105">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="2597a-106">Vous allez également effectuer la configuration, la génération et le déploiement d’une scène Unity de base depuis Visual Studio sur votre HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="2597a-106">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="2597a-107">Une fois que l’avez déployée sur votre HoloLens 2, vous devez voir un maillage de mappage spatial couvrant les surfaces qui sont perçues par HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2597a-107">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="2597a-108">En outre, vous devez voir des indicateurs sur vos mains et doigts pour le suivi de la main et un compteur de fréquence d’images pour vous tenir informé des performances de l’application.</span><span class="sxs-lookup"><span data-stu-id="2597a-108">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

## <a name="objectives"></a><span data-ttu-id="2597a-109">Objectifs</span><span class="sxs-lookup"><span data-stu-id="2597a-109">Objectives</span></span>

* <span data-ttu-id="2597a-110">Apprendre à configurer Unity pour le développement HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2597a-110">Learn how to configure Unity for HoloLens development.</span></span>
* <span data-ttu-id="2597a-111">Apprendre à créer et déployer votre application sur HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2597a-111">Learn how to build and deploy your app to HoloLens.</span></span>
* <span data-ttu-id="2597a-112">Expérimenter le maillage du mappage spatial, les maillages de la main et le compteur de fréquence d’images sur votre appareil HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="2597a-112">Experience the spatial mapping mesh, hand meshes, and  framerate counter on your HoloLens 2 device.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="2597a-113">Création du projet Unity</span><span class="sxs-lookup"><span data-stu-id="2597a-113">Creating the Unity project</span></span>

1. <span data-ttu-id="2597a-114">Lancez **Unity Hub**, sélectionnez l’onglet **Projets**, puis cliquez sur la **flèche bas** en regard du bouton **Nouveau** :</span><span class="sxs-lookup"><span data-stu-id="2597a-114">Launch **Unity Hub**, select the **Projects** tab, and then click the **down arrow** next to the **New** button:</span></span>

![Unity Hub avec la flèche bas du bouton « Nouveau » en surbrillance](images/mr-learning-base/base-02-section1-step1-1.png)

2. <span data-ttu-id="2597a-116">Dans le menu déroulant, sélectionnez la version Unity spécifiée dans les [Prérequis](mr-learning-base-01.md#prerequisites) :</span><span class="sxs-lookup"><span data-stu-id="2597a-116">In the dropdown menu, select the Unity version specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![Sélectionner la version Unity](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="2597a-118">Si cette version spécifique d’Unity n’est pas disponible dans Unity Hub, vous pouvez lancer l’installation à partir de la page <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Unity download archive</a>.</span><span class="sxs-lookup"><span data-stu-id="2597a-118">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

3. <span data-ttu-id="2597a-119">Dans la fenêtre **Créer un projet**, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="2597a-119">In the **Create a new project** window, do the following:</span></span>

    * <span data-ttu-id="2597a-120">Vérifiez que **Modèles** est défini sur **3D**.</span><span class="sxs-lookup"><span data-stu-id="2597a-120">Ensure **Templates** is set to **3D**.</span></span>
    * <span data-ttu-id="2597a-121">Dans la zone **Nom du projet** , entrez un nom approprié pour votre projet (par exemple, « Tutoriels MRTK »).</span><span class="sxs-lookup"><span data-stu-id="2597a-121">In the **Project Name** box, enter a suitable name for your project (for example, "MRTK Tutorials").</span></span>
    * <span data-ttu-id="2597a-122">Cliquez sur le bouton à trois points en regard d’**Emplacement**, puis accédez au dossier dans lequel vous souhaitez enregistrer votre projet.</span><span class="sxs-lookup"><span data-stu-id="2597a-122">Click the three-dot button next to **Location**, and then navigate to the folder where you want to save your project.</span></span>

> [!CAUTION]
> <span data-ttu-id="2597a-123">Lorsque vous travaillez sur Windows, il existe une limite MAX_PATH de 255 caractères.</span><span class="sxs-lookup"><span data-stu-id="2597a-123">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="2597a-124">Dès lors, vous devez enregistrer le projet Unity près de la racine du lecteur.</span><span class="sxs-lookup"><span data-stu-id="2597a-124">Because of this, you should save the Unity project close to the root of the drive.</span></span>

    * <span data-ttu-id="2597a-125">Cliquez sur le bouton **Créer**.</span><span class="sxs-lookup"><span data-stu-id="2597a-125">Click the **Create** button.</span></span> <span data-ttu-id="2597a-126">Cela permet de créer et de lancer votre nouveau projet Unity.</span><span class="sxs-lookup"><span data-stu-id="2597a-126">This creates and launches your new Unity project.</span></span>

![Unity Hub avec la fenêtre « Créer un projet » renseignée](images/mr-learning-base/base-02-section1-step1-3.png)

<span data-ttu-id="2597a-128">La barre d’état vous renseigne sur votre progression.</span><span class="sxs-lookup"><span data-stu-id="2597a-128">The status bar keeps you updated on your progress.</span></span>

![La barre de progression Unity vous renseigne sur l’état de création de votre projet.](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="2597a-130">Changement de plateforme de génération</span><span class="sxs-lookup"><span data-stu-id="2597a-130">Switching the build platform</span></span>

1. <span data-ttu-id="2597a-131">Dans la barre de menus, sélectionnez **Fichier** > **Paramètres de build...**</span><span class="sxs-lookup"><span data-stu-id="2597a-131">On the menu bar, select **File** > **Build Settings...**</span></span>

![Unity - Build Settings... Chemin du menu](images/mr-learning-base/base-02-section2-step1-1.png)

2. <span data-ttu-id="2597a-133">Dans la fenêtre **Paramètres de build**, sélectionnez **Plateforme Windows universelle**, puis cliquez sur le bouton **Changer de plateforme** :</span><span class="sxs-lookup"><span data-stu-id="2597a-133">In the **Build Settings** window, select **Universal Windows Platform** and then click the **Switch Platform** button:</span></span>

![Fenêtre Build Setting d’Unity avec UWP sélectionné comme nouvelle plateforme, qui était auparavant Standalone](images/mr-learning-base/base-02-section2-step1-2.png)

3. <span data-ttu-id="2597a-135">Attendez qu’Unity termine le changement de plateforme, puis fermez la fenêtre **Paramètres de build**.</span><span class="sxs-lookup"><span data-stu-id="2597a-135">Wait for Unity to finish switching the platform, and then close the **Build Settings** window.</span></span>

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="2597a-136">Importation des ressources TextMeshPro Essential</span><span class="sxs-lookup"><span data-stu-id="2597a-136">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="2597a-137">Les ressources TextMeshPro Essential sont requises par les éléments de l’interface utilisateur de MRTK.</span><span class="sxs-lookup"><span data-stu-id="2597a-137">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="2597a-138">Si vous ne prévoyez pas d’utiliser des éléments de l’interface utilisateur de MRTK dans votre projet, vous pouvez ignorer cette étape.</span><span class="sxs-lookup"><span data-stu-id="2597a-138">If you are not planning to use MRTK's UI elements in your project, you can skip this step.</span></span>

1. <span data-ttu-id="2597a-139">Dans la barre de menus, sélectionnez **Fenêtre** > **TextMeshPro** > **Importer les ressources essentielles TMP**.</span><span class="sxs-lookup"><span data-stu-id="2597a-139">On the menu bar, select **Window** > **TextMeshPro** > **Import TMP Essential Resources**.</span></span>

![Chemin du menu Import TMP Essential Resources d’Unity](images/mr-learning-base/base-02-section3-step1-1.png)

2. <span data-ttu-id="2597a-141">Dans la fenêtre **Importer un package Unity**, cliquez sur le bouton **Tous** pour vous assurer que toutes les ressources sont sélectionnées, puis sur le bouton **Importer** pour importer les ressources :</span><span class="sxs-lookup"><span data-stu-id="2597a-141">In the **Import Unity Package** window, click the **All** button to ensure that all the assets are selected, and then click the **Import** button to import the assets:</span></span>

![Fenêtre d’importation des ressources essentielles TMP d’Unity](images/mr-learning-base/base-02-section3-step1-2.png)

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="2597a-143">Importation du Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="2597a-143">Importing the Mixed Reality Toolkit</span></span>

1. <span data-ttu-id="2597a-144">Téléchargez le package personnalisé Unity :</span><span class="sxs-lookup"><span data-stu-id="2597a-144">Download the Unity custom package:</span></span>

    [<span data-ttu-id="2597a-145">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="2597a-145">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)

2. <span data-ttu-id="2597a-146">Dans la barre de menus, sélectionnez **Ressources** > **Importer un package** > **Package personnalisé...** .</span><span class="sxs-lookup"><span data-stu-id="2597a-146">On the menu bar, select **Assets** > **Import Package** > **Custom Package...**.</span></span>
3. <span data-ttu-id="2597a-147">Dans la boîte de dialogue **Importer un package...** , accédez à l’emplacement du package que vous venez de télécharger, sélectionnez-le, puis cliquez sur le bouton **Ouvrir** .</span><span class="sxs-lookup"><span data-stu-id="2597a-147">In the **Import package...** dialog, navigate to the location of the package you just downloaded, then select it, and then click the **Open** button.</span></span>
4. <span data-ttu-id="2597a-148">Dans la fenêtre **Importer un package Unity**, cliquez sur le bouton **Tous** pour vous assurer que toutes les ressources sont sélectionnées, puis sur le bouton **Importer** pour importer les ressources.</span><span class="sxs-lookup"><span data-stu-id="2597a-148">In the **Import Unity Package** window, click the **All** button to ensure that all the assets are selected, and then click the **Import** button to import the assets.</span></span>

## <a name="selecting-mrtk-and-project-settings"></a><span data-ttu-id="2597a-149">Sélection de MRTK et des paramètres de projet</span><span class="sxs-lookup"><span data-stu-id="2597a-149">Selecting MRTK and project settings</span></span>

<span data-ttu-id="2597a-150">Une fois qu’Unity a fini d’importer le package de la section précédente, la fenêtre **MRTK Project Configurator** doit s’afficher.</span><span class="sxs-lookup"><span data-stu-id="2597a-150">After Unity has finished importing the package from the previous section, the **MRTK Project Configurator** window should appear.</span></span> <span data-ttu-id="2597a-151">Si ce n’est pas le cas, vous pouvez ouvrir manuellement en accédant à **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** :</span><span class="sxs-lookup"><span data-stu-id="2597a-151">If it doesn't, you can manually open it by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**:</span></span>

![Chemin du menu Configure Unity Project d’Unity](images/mr-learning-base/base-02-section5-step1-1.png)

1. <span data-ttu-id="2597a-153">Dans la fenêtre **MRTK Project Configurator**, développez la section **Modifier les configurations**, si nécessaire, puis vérifiez que toutes les options sont sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="2597a-153">In the **MRTK Project Configurator** window, expand the **Modify Configurations** section, if necessary, and then ensure that all options are selected.</span></span>

![Fenêtre Unity MRTK Project Configurator avec la section Modifier les configurations affichée](images/mr-learning-base/base-02-section5-step1-2.png)

2. <span data-ttu-id="2597a-155">Pour appliquer les paramètres, cliquez sur le bouton **Appliquer**.</span><span class="sxs-lookup"><span data-stu-id="2597a-155">To apply the settings, click the **Apply** button.</span></span>

![Bouton Appliquer de MRTK](images/mr-learning-base/apply.png)

> [!NOTE]
> <span data-ttu-id="2597a-157">Vous utilisez le XR hérité intégré à Unity au lieu du nouveau système de plug-ins XR, car le nouveau système n’est pas entièrement compatible avec les [versions recommandées d’Unity et de MRTK](mr-learning-base-01.md#prerequisites) pour cette série de tutoriels.</span><span class="sxs-lookup"><span data-stu-id="2597a-157">You are using Unity's built-in legacy XR instead of the new XR Plugin System because the new system is not fully compatible with the [recommended Unity and MRTK versions](mr-learning-base-01.md#prerequisites) for this tutorial series.</span></span> <span data-ttu-id="2597a-158">Si des avertissements relatifs au XR intégré déconseillé s’affichent, vous pouvez les ignorer.</span><span class="sxs-lookup"><span data-stu-id="2597a-158">If you see any warnings about built-in XR being deprecated, you can ignore them.</span></span>

> [!TIP]
> <span data-ttu-id="2597a-159">L’application des paramètres par défaut de MRTK est facultative mais fortement recommandée, car elle permet de configurer certains paramètres Unity recommandés :</span><span class="sxs-lookup"><span data-stu-id="2597a-159">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>
>
> * <span data-ttu-id="2597a-160">Enable legacy XR : Active VR pour le projet.</span><span class="sxs-lookup"><span data-stu-id="2597a-160">Enable legacy XR: Enables VR for the project.</span></span>
> * <span data-ttu-id="2597a-161">Set Single Pass Instanced rendering path : Améliore les performances graphiques en exécutant le pipeline de rendu pour les deux yeux dans le même appel de dessin.</span><span class="sxs-lookup"><span data-stu-id="2597a-161">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="2597a-162">Pour plus d’informations à ce sujet, vous pouvez vous reporter à la section [Single-Pass Instanced rendering](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) de la documentation sur les [performances](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) de MRTK.</span><span class="sxs-lookup"><span data-stu-id="2597a-162">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) section of MRTK's [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) documentation.</span></span>
> * <span data-ttu-id="2597a-163">Définissez la couche de reconnaissance spatiale par défaut : Crée une couche Unity nommée Spatial Awareness et configure MRTK afin qu’il utilise cette couche pour le maillage de reconnaissance spatiale.</span><span class="sxs-lookup"><span data-stu-id="2597a-163">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="2597a-164">Pour plus d’informations sur les couches d’Unity, consultez la documentation <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Personnalisation de votre espace de travail</a>.</span><span class="sxs-lookup"><span data-stu-id="2597a-164">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

3. <span data-ttu-id="2597a-165">Dans la barre de menus, sélectionnez **Modifier** > **Paramètres du projet...** .</span><span class="sxs-lookup"><span data-stu-id="2597a-165">On the menu bar, select **Edit** > **Project Settings...** .</span></span>

4. <span data-ttu-id="2597a-166">Dans la fenêtre **Paramètres du projet**, sélectionnez **Lecteur**, cliquez sur la liste déroulante **Paramètres XR**, puis activez la case à cocher en regard de **Réalité virtuelle prise en charge** :</span><span class="sxs-lookup"><span data-stu-id="2597a-166">In the **Project Settings** window, select **Player**, then click the **XR Settings** dropdown, and then select the box next to **Virtual Reality Supported**:</span></span>

![Paramètres XR Unity avec l’option Réalité virtuelle prise en charge affichée](images/mr-learning-base/base-02-section5-step2-2.png)

<span data-ttu-id="2597a-168">Cela importe le kit de développement logiciel (SDK) Windows Mixed Reality :</span><span class="sxs-lookup"><span data-stu-id="2597a-168">This imports the Windows Mixed Reality SDK:</span></span>

![Paramètres XR Unity avec les kits de développement logiciel (SDK) de réalité virtuelle affichés](images/mr-learning-base/mixed-reality-sdk.png)

<span data-ttu-id="2597a-170">Une fois qu’Unity a fini d’importer le SDK Windows Mixed Reality, la fenêtre **MRTK Project Configurator** doit réapparaître.</span><span class="sxs-lookup"><span data-stu-id="2597a-170">After Unity has finished importing the Windows Mixed Reality SDK, the **MRTK Project Configurator** window should appear again.</span></span> <span data-ttu-id="2597a-171">Si ce n’est pas le cas, sélectionnez **Mixed Reality Toolkit** > **Utilitaires** > **Configurer un projet Unity** pour l’ouvrir.</span><span class="sxs-lookup"><span data-stu-id="2597a-171">If it doesn't, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** to open it.</span></span>

5. <span data-ttu-id="2597a-172">Dans la fenêtre **MRTK Project Configurator**, cliquez sur la liste déroulante **Audio Spatializer**, puis sélectionnez **MS HRTF Spatializer**.</span><span class="sxs-lookup"><span data-stu-id="2597a-172">In the **MRTK Project Configurator** window, click the **Audio spatializer** dropdown, and then select **MS HRTF Spatializer**.</span></span>

![Paramètres du projet avec les options Audio Spatializer affichées](images/mr-learning-base/base-02-section5-step2-3.png)

6. <span data-ttu-id="2597a-174">Cliquez sur le bouton **Appliquer**.</span><span class="sxs-lookup"><span data-stu-id="2597a-174">Click the **Apply** button.</span></span> <span data-ttu-id="2597a-175">La fenêtre **MRTK Project Configurator** se ferme.</span><span class="sxs-lookup"><span data-stu-id="2597a-175">This closes the **MRTK Project Configurator** window.</span></span>

    > [!TIP]
    > <span data-ttu-id="2597a-176">La définition de la propriété Audio Spatializer est facultative mais peut améliorer l’expérience audio dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="2597a-176">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="2597a-177">Si vous la définissez sur MS HRTF Spatializer, ce plug-in Spatializer sera utilisé quand la propriété AudioSource.spatialize d’Unity est activée.</span><span class="sxs-lookup"><span data-stu-id="2597a-177">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="2597a-178">Pour plus d’informations sur ce sujet, vous pouvez consulter les tutoriels d’audio spatiale.</span><span class="sxs-lookup"><span data-stu-id="2597a-178">To learn more about this topic, you can refer to the Spatial audio tutorials.</span></span>

7. <span data-ttu-id="2597a-179">Dans la fenêtre **Paramètre du projet**, cliquez sur la liste déroulante **Format de profondeur**, puis sélectionnez **Profondeur de 16 bits** :</span><span class="sxs-lookup"><span data-stu-id="2597a-179">In the **Project Settings** window, click the **Depth Format** dropdown, and then select **16-bit depth**:</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-4.png" alt-text="Paramètres XR d’Unity avec une profondeur de 16 bits sélectionnée.":::

    > [!TIP]
    > <span data-ttu-id="2597a-181">La réduction du format de profondeur à 16 bits est facultative, mais peut contribuer à améliorer les performances graphiques dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="2597a-181">Reducing the Depth Format to 16-bit is optional but may help improve graphics performance in your project.</span></span> <span data-ttu-id="2597a-182">Pour plus d’informations à ce sujet, vous pouvez vous reporter à la section [Depth buffer sharing (HoloLens)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens) de la documentation sur les [performances](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) de MRTK.</span><span class="sxs-lookup"><span data-stu-id="2597a-182">To learn more about this topic, you can refer to the [Depth buffer sharing (HoloLens)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens) section of MRTK's [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) documentation.</span></span>

8. <span data-ttu-id="2597a-183">Cliquez sur la liste déroulante **Paramètres de publication** puis, dans la zone **Nom du package**, entrez un nom approprié (par exemple, « MRTK-Tutorials-Getting-Started »).</span><span class="sxs-lookup"><span data-stu-id="2597a-183">Click the **Publishing Settings** drop-down, and then in the **Package name** box, enter a suitable name (for example, "MRTK-Tutorials-Getting-Started").</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-5.png" alt-text="Fenêtre Paramètres de publication d’Unity avec le nom du package configuré.":::

    <span data-ttu-id="2597a-185">**Nom du package et nom du produit**</span><span class="sxs-lookup"><span data-stu-id="2597a-185">**Package Name and Product Name**</span></span>

    - <span data-ttu-id="2597a-186">Le « Package name » est l’identificateur unique de l’application.</span><span class="sxs-lookup"><span data-stu-id="2597a-186">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="2597a-187">Vous devez créer cet identificateur avant de déployer l’application afin d’éviter de remplacer des applications déjà installées.</span><span class="sxs-lookup"><span data-stu-id="2597a-187">You should create this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>
    - <span data-ttu-id="2597a-188">« Product Name » est le nom affiché dans le menu Démarrer de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2597a-188">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="2597a-189">Pour faciliter la localisation de l’application pendant le développement, vous pouvez ajouter un trait de soulignement devant le nom afin qu’il apparaisse en haut du classement.</span><span class="sxs-lookup"><span data-stu-id="2597a-189">To make the app easier to locate during development, you can add an underscore in front of the name to sort it to the top.</span></span>

    :::image type="content" source="images/mr-learning-base/product-name.png" alt-text="Paramètres du projet Unity avec le nom du produit configuré.":::

9. <span data-ttu-id="2597a-191">Fermez la fenêtre **Paramètres du projet**.</span><span class="sxs-lookup"><span data-stu-id="2597a-191">Close the **Project Settings** window.</span></span>

## <a name="creating-and-configuring-the-scene"></a><span data-ttu-id="2597a-192">Création et configuration de la scène</span><span class="sxs-lookup"><span data-stu-id="2597a-192">Creating and configuring the scene</span></span>

1. <span data-ttu-id="2597a-193">Dans la barre de menus, sélectionnez **Fichier** > **Nouvelle scène**.</span><span class="sxs-lookup"><span data-stu-id="2597a-193">On the menu bar, select **File** > **New Scene**.</span></span>
2. <span data-ttu-id="2597a-194">Pour ajouter le MRTK à la scène, dans la barre de menus, sélectionnez **Mixed Reality Toolkit** > **Ajouter à la scène et configurer...** .</span><span class="sxs-lookup"><span data-stu-id="2597a-194">To add the MRTK to the scene, on the menu bar, select **Mixed Reality Toolkit** > **Add to Scene and Configure...**.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-2.png" alt-text="Unity - Ajouter à la scène et configurer... Chemin du menu.":::

3. <span data-ttu-id="2597a-196">Dans la fenêtre **Hiérarchie**, vérifiez que **MixedRealityToolkit** est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="2597a-196">In the **Hierarchy** window, ensure that **MixedRealityToolkit** is selected.</span></span>

    :::image type="content" source="images/mr-learning-base/select-mixed-reality-toolkit.png" alt-text="Vérifiez que MixedRealityTookit est sélectionné.":::

4. <span data-ttu-id="2597a-198">Dans la section **MixedRealityToolkit** de la fenêtre **Inspector**, vérifiez que le profil de configuration est définir sur **DefaultMixedRealityToolkitConfigurationProfile** :</span><span class="sxs-lookup"><span data-stu-id="2597a-198">In the **Inspector** window's **MixedRealityToolkit** section, verify that the configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-3.png" alt-text="Composant MixedRealityToolkit d’Unity avec DefaultMixedRealityTookitConfigurationProfile sélectionné.":::

    > [!IMPORTANT]
    > <span data-ttu-id="2597a-200">En général, vous allez utiliser DefaultHoloLens2ConfigurationProfile lors du développement pour HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2597a-200">Typically, you will use the DefaultHoloLens2ConfigurationProfile when developing for HoloLens.</span></span> <span data-ttu-id="2597a-201">Toutefois, pour ce tutoriel, vous utiliserez DefaultMixedRealityToolkitConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="2597a-201">However, for this tutorial, you will use the DefaultMixedRealityToolkitConfigurationProfile.</span></span> <span data-ttu-id="2597a-202">Dans le tutoriel suivant, [Configuration des profils MRTK](mr-learning-base-03.md), vous utiliserez DefaultHoloLens2ConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="2597a-202">In the next tutorial, [Configuring the MRTK profiles](mr-learning-base-03.md), you will change to the DefaultHoloLens2ConfigurationProfile.</span></span>

5. <span data-ttu-id="2597a-203">Dans la barre de menus, sélectionnez **Fichier** > **Enregistrer sous...** .</span><span class="sxs-lookup"><span data-stu-id="2597a-203">On the menu bar, select **File** > **Save As...**</span></span>
6. <span data-ttu-id="2597a-204">Dans la boîte de dialogue **Enregistrer la scène**, accédez au dossier **Scènes** de votre projet.</span><span class="sxs-lookup"><span data-stu-id="2597a-204">In the **Save Scene** dialog, navigate to your project's **Scenes** folder.</span></span> <span data-ttu-id="2597a-205">Dans la zone **Nom du fichier**, donnez à votre scène un nom approprié (par exemple, « \_GettingStarted\_ »), puis cliquez sur le bouton **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="2597a-205">In the **File name** box, give your scene a suitable name (for example, "\_GettingStarted\_"), and then click the **Save** button.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-5.png" alt-text="Fenêtre d’invite Enregistrer d’Unity pour enregistrer la scène.":::

## <a name="building-and-deploying-to-your-hololens-2"></a><span data-ttu-id="2597a-207">Génération et déploiement sur votre HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="2597a-207">Building and deploying to your HoloLens 2</span></span>

> <span data-ttu-id="2597a-208">Avant toute génération sur votre appareil, vérifiez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="2597a-208">Before building to your device, confirm the following:</span></span>
- <span data-ttu-id="2597a-209">Votre appareil est en mode développeur.</span><span class="sxs-lookup"><span data-stu-id="2597a-209">Your device is in Developer Mode.</span></span>
- <span data-ttu-id="2597a-210">Votre appareil est couplé à votre ordinateur de développement.</span><span class="sxs-lookup"><span data-stu-id="2597a-210">Your device is paired with your development computer.</span></span> <span data-ttu-id="2597a-211">Si ce n’est pas le cas, la boîte de dialogue suivante s’affiche dans Visual Studio lors du processus de génération :</span><span class="sxs-lookup"><span data-stu-id="2597a-211">If it's not, you will see the following dialog box in Visual Studio during the build process:</span></span>

![Entrée du code PIN pour le couplage d’appareils](images/mr-learning-base/pin-request.png)

 <span data-ttu-id="2597a-213">Pour en savoir plus sur ces deux étapes, consultez [Utilisation de Visual Studio pour le déploiement et le débogage](../../platform-capabilities-and-apis/using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="2597a-213">To learn more about both of these steps, see [Using Visual Studio to deploy and debug](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

1. <span data-ttu-id="2597a-214">Dans la barre de menus, sélectionnez **Fichier** > **Paramètres de build...** .</span><span class="sxs-lookup"><span data-stu-id="2597a-214">On the menu bar, select **File** > **Build Settings...**.</span></span>
2. <span data-ttu-id="2597a-215">Dans la fenêtre **Paramètres de build**, cliquez sur le bouton **Ajouter des scènes ouvertes** pour ajouter votre scène actuelle à la liste **Scènes de la build**.</span><span class="sxs-lookup"><span data-stu-id="2597a-215">In the **Build Settings** window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list.</span></span>

![Ajouter votre scène actuelle à la liste « Scènes de la build »](images/mr-learning-base/base-02-section7-step1-1.png)

3. <span data-ttu-id="2597a-217">Cliquez sur le bouton **Créer**.</span><span class="sxs-lookup"><span data-stu-id="2597a-217">Click the **Build** button.</span></span>

    :::image type="content" source="images/mr-learning-base/build-button.png" alt-text="Cliquez sur le bouton Créer.":::

4. <span data-ttu-id="2597a-219">Dans la boîte de dialogue **Build - Plateforme Windows universelle**, sélectionnez un emplacement approprié où stocker votre build (vous pouvez, par exemple, créer un dossier « Builds » dans votre dossier « Tutoriels MRTK »).</span><span class="sxs-lookup"><span data-stu-id="2597a-219">In the **Build Universal Windows Platform** dialog, choose a suitable location to store your build (for example, you may want to create a "Builds" folder in your "MRTK Tutorials" folder).</span></span> <span data-ttu-id="2597a-220">Créez un dossier et attribuez-lui un nom approprié (par exemple, « GettingStarted »), sélectionnez le dossier, puis cliquez sur le bouton **Sélectionner un dossier** pour démarrer le processus de génération.</span><span class="sxs-lookup"><span data-stu-id="2597a-220">Create a new folder and give it a suitable name (for example, "GettingStarted"), then select the folder, and then click the **Select Folder** button to start the build process.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-2.png" alt-text="Fenêtre de génération Unity avec votre dossier de build affiché.":::

    <span data-ttu-id="2597a-222">Une barre d’état s’affiche pour vous informer de la progression de la génération.</span><span class="sxs-lookup"><span data-stu-id="2597a-222">A status bar appears and keeps you updated on your build progress.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-3.png" alt-text="Processus de génération Unity en cours.":::

    > [!TIP]
    > <span data-ttu-id="2597a-224">Vous pouvez aussi déployer sur l’[émulateur HoloLens](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) ou créer un [package d’application](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) pour un chargement indépendant (sideloading).</span><span class="sxs-lookup"><span data-stu-id="2597a-224">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

5. <span data-ttu-id="2597a-225">Une fois le processus de génération terminé, dans l’Explorateur de fichiers, accédez à l’emplacement où vous avez stocké la build, puis double-cliquez sur le fichier de solution pour l’ouvrir dans Visual Studio :</span><span class="sxs-lookup"><span data-stu-id="2597a-225">When the build process has completed, in File Explorer, navigate to the location where you stored the build, and then double-click the solution file to open it in Visual Studio:</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-1.png" alt-text="Explorateur Windows avec le fichier de solution Visual Studio nouvellement créé sélectionné.":::

    > [!NOTE]
    > <span data-ttu-id="2597a-227">Si Visual Studio vous demande d’installer de nouveaux composants, prenez un moment pour vérifier que vous avez tous les composants prérequis comme spécifié dans la documentation **[Installer les outils](../../install-the-tools.md)** .</span><span class="sxs-lookup"><span data-stu-id="2597a-227">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

6. <span data-ttu-id="2597a-228">Configurez Visual Studio pour HoloLens en sélectionnant la configuration **Master** ou **Release**, l’architecture **ARM64** et **Appareil** comme cible.</span><span class="sxs-lookup"><span data-stu-id="2597a-228">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as the target.</span></span>

    > [!TIP]
    > <span data-ttu-id="2597a-229">Si vous effectuez un déploiement sur HoloLens (1ère génération), sélectionnez l’architecture **x86**.</span><span class="sxs-lookup"><span data-stu-id="2597a-229">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-2.png" alt-text="Visual Studio configuré pour le déploiement sur HoloLens 2.":::

    > [!NOTE]
    > <span data-ttu-id="2597a-231">En général, pour HoloLens, vous allez générer pour l’architecture ARM.</span><span class="sxs-lookup"><span data-stu-id="2597a-231">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="2597a-232">Il y a cependant un <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>problème connu</strong></a> dans Unity 2019.3 qui provoque des erreurs lors de la sélection de ARM comme architecture de génération dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2597a-232">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="2597a-233">La solution de contournement recommandée est de générer pour ARM64.</span><span class="sxs-lookup"><span data-stu-id="2597a-233">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="2597a-234">Si ce n’est pas possible, accédez à **Modifier > Paramètres du projet > Lecteur > Autres paramètres** et désactivez **Travaux graphiques**.</span><span class="sxs-lookup"><span data-stu-id="2597a-234">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2597a-235">Si vous ne voyez pas Appareil comme choix de cible, il peut être nécessaire de changer le projet de démarrage pour la solution Visual Studio de Projet IL2CPP en Projet UWP.</span><span class="sxs-lookup"><span data-stu-id="2597a-235">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="2597a-236">Pour ce faire, dans l’Explorateur de solutions, cliquez avec le bouton droit sur nom_de_votre_projet (Windows universel), puis sélectionnez **Définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="2597a-236">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows), and then select **Set as StartUp Project**.</span></span>

7. <span data-ttu-id="2597a-237">Connectez votre HoloLens à votre ordinateur, puis effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="2597a-237">Connect your HoloLens to your computer, and then do one of the following:</span></span>
- <span data-ttu-id="2597a-238">Pour générer l’application, déployez-la dans votre HoloLens et démarrez-la automatiquement sans que le débogueur Visual Studio ne soit attaché. Dans la barre de menus, sélectionnez **Débogage** > **Exécuter sans débogage**.</span><span class="sxs-lookup"><span data-stu-id="2597a-238">To build the app, deploy it to your HoloLens, and start it automatically without the Visual Studio debugger attached, on the menu bar, select **Debug** > **Start Without Debugging**.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-3.png" alt-text="Visual Studio - Chemin du menu Démarrer sans débogage.":::

- <span data-ttu-id="2597a-240">Pour générer et déployer l’application dans votre HoloLens sans qu’elle démarre automatiquement, dans la barre de menus, sélectionnez **Build > Déployer la solution**.</span><span class="sxs-lookup"><span data-stu-id="2597a-240">To build and deploy the app to your HoloLens but not have it start automatically, on the menu bar, select **Build > Deploy Solution**.</span></span>

    > [!NOTE]
    ><span data-ttu-id="2597a-241">Vous remarquerez peut-être le profileur de diagnostics dans l’application, que vous pouvez activer ou désactiver avec la commande vocale **Toggle Diagnostics**.</span><span class="sxs-lookup"><span data-stu-id="2597a-241">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="2597a-242">Il est recommandé de garder le profileur visible la plupart du temps pendant le développement, de façon à comprendre quand des modifications apportées à l’application peuvent avoir un impact sur les performances.</span><span class="sxs-lookup"><span data-stu-id="2597a-242">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="2597a-243">Par exemple, les applications HoloLens doivent [s’exécuter en continu à 60 images/s](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="2597a-243">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="2597a-244">Félicitations</span><span class="sxs-lookup"><span data-stu-id="2597a-244">Congratulations</span></span>

<span data-ttu-id="2597a-245">Vous avez maintenant déployé votre première application HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2597a-245">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="2597a-246">À mesure que vous vous déplacez, vous devez voir un maillage de mappage spatial couvrant les surfaces qui sont perçues par HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2597a-246">As you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="2597a-247">En outre, vous devez voir des indicateurs sur vos mains et doigts pour le suivi de la main et un compteur de fréquence d’images pour vous tenir informé des performances de l’application.</span><span class="sxs-lookup"><span data-stu-id="2597a-247">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="2597a-248">Ces fonctionnalités sont simplement quelques composants fondamentaux inclus avec MRTK.</span><span class="sxs-lookup"><span data-stu-id="2597a-248">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="2597a-249">Dans les tutoriels à venir, vous allez ajouter du contenu à votre scène pour explorer les fonctionnalités HoloLens et MRTK.</span><span class="sxs-lookup"><span data-stu-id="2597a-249">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2597a-250">Tutoriel suivant : 3. Configuration des profils MRTK</span><span class="sxs-lookup"><span data-stu-id="2597a-250">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
