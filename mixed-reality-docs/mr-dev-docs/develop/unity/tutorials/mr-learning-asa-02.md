---
title: Tutoriels Azure Spatial Anchors - 2. Bien démarrer avec Azure Spatial Anchors
description: Suivez ce cours pour découvrir comment utiliser Azure Spatial Anchors pour ancrer des objets dans une application de réalité mixte.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens
ms.localizationpriority: high
ms.openlocfilehash: c73ddec2fc1be20a4a2c582948cd240be7fe23db
ms.sourcegitcommit: 63c228af55379810ab2ee4f09f20eded1bb76229
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2020
ms.locfileid: "93353447"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="a9d97-105">2. Bien démarrer avec Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="a9d97-105">2. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="a9d97-106">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="a9d97-106">Overview</span></span>

<span data-ttu-id="a9d97-107">Dans ce tutoriel, vous allez découvrir les différentes étapes nécessaires pour démarrer et arrêter une session Azure Spatial Anchors, et pour créer, charger et télécharger des ancres spatiales Azure sur un appareil.</span><span class="sxs-lookup"><span data-stu-id="a9d97-107">In this tutorial, you will explore the various steps required to start and stop an Azure Spatial Anchors session and to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

## <a name="objectives"></a><span data-ttu-id="a9d97-108">Objectifs</span><span class="sxs-lookup"><span data-stu-id="a9d97-108">Objectives</span></span>

* <span data-ttu-id="a9d97-109">Découvrir les principes de base du développement avec Azure Spatial Anchors pour HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="a9d97-109">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="a9d97-110">Apprendre à créer des ancres spatiales et à les récupérer à partir d’Azure</span><span class="sxs-lookup"><span data-stu-id="a9d97-110">Learn how to create spatial anchors and fetch them from Azure</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="a9d97-111">Création et préparation du projet Unity</span><span class="sxs-lookup"><span data-stu-id="a9d97-111">Creating and preparing the Unity project</span></span>

<span data-ttu-id="a9d97-112">Dans cette section, vous allez créer un projet Unity et le préparer au développement avec MRTK.</span><span class="sxs-lookup"><span data-stu-id="a9d97-112">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="a9d97-113">Pour cela, suivez d’abord [Initialisation de votre projet et déploiement de votre première application](mr-learning-base-02.md), en excluant les instructions données dans [Générer votre application sur votre appareil](mr-learning-base-02.md#building-your-application-to-your-hololens-2), ce qui inclut les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="a9d97-113">For this, first follow the [Initializing your project and deploying your first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="a9d97-114">[Création du projet Unity](mr-learning-base-02.md#creating-the-unity-project) et affectation d’un nom pertinent, par exemple *MRTK Tutorials*</span><span class="sxs-lookup"><span data-stu-id="a9d97-114">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
1. [<span data-ttu-id="a9d97-115">Changement de plateforme de génération</span><span class="sxs-lookup"><span data-stu-id="a9d97-115">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. [<span data-ttu-id="a9d97-116">Importation des ressources TextMeshPro Essential</span><span class="sxs-lookup"><span data-stu-id="a9d97-116">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
1. [<span data-ttu-id="a9d97-117">Importation du Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="a9d97-117">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
1. [<span data-ttu-id="a9d97-118">Configuration du projet Unity</span><span class="sxs-lookup"><span data-stu-id="a9d97-118">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. <span data-ttu-id="a9d97-119">[Création et configuration de la scène](mr-learning-base-02.md#creating-and-configuring-the-scene), et affectation d’un nom pertinent à la scène, par exemple *AzureSpatialAnchors*</span><span class="sxs-lookup"><span data-stu-id="a9d97-119">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="a9d97-120">Ensuite, suivez les instructions fournies dans [Changement de l’option d’affichage de la reconnaissance spatiale](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) pour :</span><span class="sxs-lookup"><span data-stu-id="a9d97-120">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to:</span></span>

1. <span data-ttu-id="a9d97-121">Remplacer le **profil de configuration MRTK** par **DefaultHoloLens2ConfigurationProfile**</span><span class="sxs-lookup"><span data-stu-id="a9d97-121">Change the **MRTK configuration profile** for to the **DefaultHoloLens2ConfigurationProfile**</span></span>
1. <span data-ttu-id="a9d97-122">Choisir **Occlusion** dans les **options d’affichage du maillage de la reconnaissance spatiale**.</span><span class="sxs-lookup"><span data-stu-id="a9d97-122">Change the **spatial awareness mesh display options** to **Occlusion**.</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="a9d97-123">Installation de packages Unity intégrés</span><span class="sxs-lookup"><span data-stu-id="a9d97-123">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="a9d97-124">Dans le menu Unity, sélectionnez **Window** > **Package Manager** pour ouvrir la fenêtre Package Manager, sélectionnez **AR Foundation** , puis cliquez sur le bouton **Install** pour installer le package :</span><span class="sxs-lookup"><span data-stu-id="a9d97-124">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![Package Manager d’Unity avec AR Foundation sélectionné](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="a9d97-126">Vous installez le package intégré AR Foundation, car il est nécessaire pour le SDK Azure Spatial Anchors que vous allez importer dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="a9d97-126">You are installing the AR Foundation package because the Azure Spatial Anchors SDK requires it, which you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="a9d97-127">Importation des ressources du tutoriel</span><span class="sxs-lookup"><span data-stu-id="a9d97-127">Importing the tutorial assets</span></span>

<span data-ttu-id="a9d97-128">Téléchargez et **importez** les packages personnalisés Unity suivants **dans l’ordre où ils sont listés**  :</span><span class="sxs-lookup"><span data-stu-id="a9d97-128">Download and **import** the following Unity custom packages **in the order they are listed** :</span></span>

* <span data-ttu-id="a9d97-129">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (version 2.2.1)</span><span class="sxs-lookup"><span data-stu-id="a9d97-129">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (version 2.2.1)</span></span>
* [<span data-ttu-id="a9d97-130">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="a9d97-130">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="a9d97-131">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="a9d97-131">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)

<span data-ttu-id="a9d97-132">Une fois que vous avez importé les ressources du tutoriel, votre fenêtre Project doit ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="a9d97-132">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Fenêtres Hierarchy, Scene et Project dans Unity, après l’importation des ressources du tutoriel](images/mr-learning-asa/asa-02-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="a9d97-134">Si vous voyez des avertissements CS0618 signalant que « WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr) » est obsolète, vous pouvez les ignorer.</span><span class="sxs-lookup"><span data-stu-id="a9d97-134">If you see any CS0618 warnings regarding 'WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)' is obsolete, you can ignore these warnings.</span></span>

> [!TIP]
> <span data-ttu-id="a9d97-135">Pour vous rappeler comment importer un package personnalisé Unity, reportez-vous aux instructions fournies dans [Importation du Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="a9d97-135">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="a9d97-136">Préparation de la scène</span><span class="sxs-lookup"><span data-stu-id="a9d97-136">Preparing the scene</span></span>

<span data-ttu-id="a9d97-137">Dans cette section, vous allez préparer la scène en ajoutant une partie des préfabriqués du tutoriel.</span><span class="sxs-lookup"><span data-stu-id="a9d97-137">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="a9d97-138">Dans la fenêtre Project, accédez au dossier **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** , puis cliquez sur les préfabriqués suivants et faites-les glisser dans la fenêtre Hierarchy pour les ajouter à votre scène :</span><span class="sxs-lookup"><span data-stu-id="a9d97-138">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="a9d97-139">Préfabriqués **ButtonParent**</span><span class="sxs-lookup"><span data-stu-id="a9d97-139">**ButtonParent** prefabs</span></span>
* <span data-ttu-id="a9d97-140">Préfabriqués **DebugWindow**</span><span class="sxs-lookup"><span data-stu-id="a9d97-140">**DebugWindow** prefabs</span></span>
* <span data-ttu-id="a9d97-141">Préfabriqués **Instructions**</span><span class="sxs-lookup"><span data-stu-id="a9d97-141">**Instructions** prefabs</span></span>
* <span data-ttu-id="a9d97-142">Préfabriqués **ParentAnchor**</span><span class="sxs-lookup"><span data-stu-id="a9d97-142">**ParentAnchor** prefabs</span></span>

![Unity avec des préfabriqués nouvellement ajoutés sélectionnés](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="a9d97-144">Si vous trouvez gênantes les grandes icônes de votre scène, par exemple les grandes icônes « T », vous pouvez les masquer en <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">basculant les gizmos</a> en position Off, comme le montre l’image ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="a9d97-144">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position, as shown in the image above.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="a9d97-145">Configuration des boutons pour faire fonctionner la scène</span><span class="sxs-lookup"><span data-stu-id="a9d97-145">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="a9d97-146">Dans cette section, vous allez ajouter des scripts à la scène pour créer une série d’événements de bouton qui montrent le comportement de base des ancres locales et des ancres spatiales Azure dans une application.</span><span class="sxs-lookup"><span data-stu-id="a9d97-146">In this section, you will add scripts to the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an app.</span></span>

<span data-ttu-id="a9d97-147">Dans la fenêtre Hierarchy, développez l’objet **ButtonParent** et sélectionnez le premier objet enfant nommé **StartAzureSession** , puis dans la fenêtre Inspector, configurez l’événement **On Click ()** du composant **Button Config Helper (Script)** comme ceci :</span><span class="sxs-lookup"><span data-stu-id="a9d97-147">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession** , in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="a9d97-148">Affectez l’objet **ParentAnchor** au champ **None (Object)** .</span><span class="sxs-lookup"><span data-stu-id="a9d97-148">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="a9d97-149">Dans la liste déroulante **No Function** , sélectionnez **AnchorModuleScript** > **StartAzureSession ()** pour définir cette fonction comme l’action à exécuter quand l’événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="a9d97-149">From the **No Function** dropdown, select **AnchorModuleScript** > **StartAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity avec l’événement OnClick du bouton StartAzureSession configuré](images/mr-learning-asa/asa-02-section5-step1-1.png)

<span data-ttu-id="a9d97-151">Dans la fenêtre Hierarchy, sélectionnez le bouton suivant nommé **StopAzureSession** , puis dans la fenêtre Inspector, configurez l’événement **On Click ()** du composant **Button Config Helper (Script)** comme ceci :</span><span class="sxs-lookup"><span data-stu-id="a9d97-151">In the Hierarchy window, select the next button named **StopAzureSession** , then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="a9d97-152">Affectez l’objet **ParentAnchor** au champ **None (Object)** .</span><span class="sxs-lookup"><span data-stu-id="a9d97-152">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="a9d97-153">Dans la liste déroulante **No Function** , sélectionnez **AnchorModuleScript** > **StopAzureSession ()** pour définir cette fonction comme l’action à exécuter quand l’événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="a9d97-153">From the **No Function** dropdown, select **AnchorModuleScript** > **StopAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity avec l’événement OnClick du bouton StopAzureSession configuré](images/mr-learning-asa/asa-02-section5-step1-2.png)

<span data-ttu-id="a9d97-155">Dans la fenêtre Hierarchy, sélectionnez le bouton suivant nommé **CreateAzureAnchor** , puis dans la fenêtre Inspector, configurez l’événement **On Click ()** du composant **Button Config Helper (Script)** comme ceci :</span><span class="sxs-lookup"><span data-stu-id="a9d97-155">In the Hierarchy window, select the next button named **CreateAzureAnchor** , then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="a9d97-156">Affectez l’objet **ParentAnchor** au champ **None (Object)** .</span><span class="sxs-lookup"><span data-stu-id="a9d97-156">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="a9d97-157">Dans la liste déroulante **No Function** , sélectionnez **AnchorModuleScript** > **CreateAzureAnchor ()** pour définir cette fonction comme l’action à exécuter quand l’événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="a9d97-157">From the **No Function** dropdown, select **AnchorModuleScript** > **CreateAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="a9d97-158">Affectez l’objet **ParentAnchor** au champ vide **None (Game Object)** pour en faire l’argument de la fonction CreateAzureAnchor ().</span><span class="sxs-lookup"><span data-stu-id="a9d97-158">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the CreateAzureAnchor () function</span></span>

![Unity avec l’événement OnClick du bouton CreateAzureAnchor configuré](images/mr-learning-asa/asa-02-section5-step1-3.png)

<span data-ttu-id="a9d97-160">Dans la fenêtre Hierarchy, sélectionnez le bouton suivant nommé **RemoveLocalAnchor** , puis dans la fenêtre Inspector, configurez l’événement **On Click ()** du composant **Button Config Helper (Script)** comme ceci :</span><span class="sxs-lookup"><span data-stu-id="a9d97-160">In the Hierarchy window, select the next button named **RemoveLocalAnchor** ,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="a9d97-161">Affectez l’objet **ParentAnchor** au champ **None (Object)** .</span><span class="sxs-lookup"><span data-stu-id="a9d97-161">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="a9d97-162">Dans la liste déroulante **No Function** , sélectionnez **AnchorModuleScript** > **RemoveLocalAnchor ()** pour définir cette fonction comme l’action à exécuter quand l’événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="a9d97-162">From the **No Function** dropdown, select **AnchorModuleScript** > **RemoveLocalAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="a9d97-163">Affectez l’objet **ParentAnchor** au champ vide **None (Game Object)** pour en faire l’argument de la fonction RemoveLocalAnchor ().</span><span class="sxs-lookup"><span data-stu-id="a9d97-163">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the RemoveLocalAnchor () function</span></span>

![Unity avec l’événement OnClick du bouton RemoveLocalAnchor configuré](images/mr-learning-asa/asa-02-section5-step1-4.png)

<span data-ttu-id="a9d97-165">Dans la fenêtre Hierarchy, sélectionnez le bouton suivant nommé **FindAzureAnchor** , puis dans la fenêtre Inspector, configurez l’événement **On Click ()** du composant **Button Config Helper (Script)** comme ceci :</span><span class="sxs-lookup"><span data-stu-id="a9d97-165">In the Hierarchy window, select the next button named **FindAzureAnchor** ,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="a9d97-166">Affectez l’objet **ParentAnchor** au champ **None (Object)** .</span><span class="sxs-lookup"><span data-stu-id="a9d97-166">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="a9d97-167">Dans la liste déroulante **No Function** , sélectionnez **AnchorModuleScript** > **FindAzureAnchor ()** pour définir cette fonction comme l’action à exécuter quand l’événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="a9d97-167">From the **No Function** dropdown, select **AnchorModuleScript** > **FindAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity avec l’événement OnClick du bouton FindAzureAnchor configuré](images/mr-learning-asa/asa-02-section5-step1-5.png)

<span data-ttu-id="a9d97-169">Dans la fenêtre Hierarchy, sélectionnez le bouton suivant nommé **DeleteAzureAnchor** , puis dans la fenêtre Inspector, configurez l’événement **On Click ()** du composant **Button Config Helper (Script)** comme ceci :</span><span class="sxs-lookup"><span data-stu-id="a9d97-169">In the Hierarchy window, select the next button named **DeleteAzureAnchor** , then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="a9d97-170">Affectez l’objet **DeleteAzureAnchor** au champ **None (Object)** .</span><span class="sxs-lookup"><span data-stu-id="a9d97-170">Assign the **DeleteAzureAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="a9d97-171">Dans la liste déroulante **No Function** , sélectionnez **AnchorModuleScript** > **DeleteAzureAnchor ()** pour définir cette fonction comme l’action à exécuter quand l’événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="a9d97-171">From the **No Function** dropdown, select **AnchorModuleScript** > **DeleteAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity avec l’événement OnClick du bouton DeleteAzureAnchor configuré](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="a9d97-173">Connexion de la scène à la ressource Azure</span><span class="sxs-lookup"><span data-stu-id="a9d97-173">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="a9d97-174">Dans la fenêtre Hierarchy, sélectionnez l’objet **ParentAnchor** , puis dans la fenêtre Inspector, recherchez le composant **Spatial Anchor Manager (Script)** .</span><span class="sxs-lookup"><span data-stu-id="a9d97-174">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, locate the **Spatial Anchor Manager (Script)** component.</span></span> <span data-ttu-id="a9d97-175">Configurez la section **Credentials** avec les informations d’identification du compte Azure Spatial Anchors créé dans le cadre des [prérequis](mr-learning-asa-01.md#prerequisites) pour cette série de tutoriels :</span><span class="sxs-lookup"><span data-stu-id="a9d97-175">Configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mr-learning-asa-01.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="a9d97-176">Dans le champ **Spatial Anchors Account ID** , collez la valeur **Account ID** de votre compte Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="a9d97-176">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="a9d97-177">Dans le champ **Spatial Anchors Account Key** , collez la valeur **Access Key** (primaire ou secondaire) de votre compte Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="a9d97-177">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>

![Unity avec Spatial Anchor Manager configuré](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="a9d97-179">Essai des comportements de base d’Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="a9d97-179">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="a9d97-180">Azure Spatial Anchors ne peut pas s’exécuter dans Unity : pour tester la fonctionnalité Azure Spatial Anchors, vous devez donc générer et déployer l’application sur votre appareil.</span><span class="sxs-lookup"><span data-stu-id="a9d97-180">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to build the project and deploy the app to your device.</span></span>

> [!TIP]
> <span data-ttu-id="a9d97-181">Pour vous rappeler comment générer et déployer votre projet Unity sur HoloLens 2, reportez-vous aux instructions fournies dans [Génération de votre application sur votre HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="a9d97-181">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your application to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

<span data-ttu-id="a9d97-182">Quand l’application s’exécute sur votre appareil, suivez les instructions à l’écran affichées dans le panneau des instructions du tutoriel Azure Spatial Anchors :</span><span class="sxs-lookup"><span data-stu-id="a9d97-182">When the app runs on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

1. <span data-ttu-id="a9d97-183">Déplacer le cube vers un autre emplacement</span><span class="sxs-lookup"><span data-stu-id="a9d97-183">Move the cube to a different location</span></span>
1. <span data-ttu-id="a9d97-184">Démarrer la session Azure</span><span class="sxs-lookup"><span data-stu-id="a9d97-184">Start Azure Session</span></span>
1. <span data-ttu-id="a9d97-185">Créer une ancre Azure (crée une ancre à l’emplacement du cube)</span><span class="sxs-lookup"><span data-stu-id="a9d97-185">Create Azure Anchor (creates an anchor at the location of the cube).</span></span>
1. <span data-ttu-id="a9d97-186">Arrêter la session Azure</span><span class="sxs-lookup"><span data-stu-id="a9d97-186">Stop Azure Session</span></span>
1. <span data-ttu-id="a9d97-187">Supprimer l’ancre locale (permet à l’utilisateur de déplacer le cube)</span><span class="sxs-lookup"><span data-stu-id="a9d97-187">Remove Local Anchor (allows the user to move the cube)</span></span>
1. <span data-ttu-id="a9d97-188">Déplacer le cube ailleurs</span><span class="sxs-lookup"><span data-stu-id="a9d97-188">Move the cube somewhere else</span></span>
1. <span data-ttu-id="a9d97-189">Démarrer la session Azure</span><span class="sxs-lookup"><span data-stu-id="a9d97-189">Start Azure Session</span></span>
1. <span data-ttu-id="a9d97-190">Rechercher l’ancre Azure (positionne le cube à l’emplacement de l’étape 3)</span><span class="sxs-lookup"><span data-stu-id="a9d97-190">Find Azure Anchor (positions the cube at the location from step 3)</span></span>
1. <span data-ttu-id="a9d97-191">Supprimer l’ancre Azure</span><span class="sxs-lookup"><span data-stu-id="a9d97-191">Delete Azure Anchor</span></span>
1. <span data-ttu-id="a9d97-192">Arrêter la session Azure</span><span class="sxs-lookup"><span data-stu-id="a9d97-192">Stop Azure session</span></span>

![Unity avec l’objet Instructions sélectionné](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> <span data-ttu-id="a9d97-194">Azure Spatial Anchors utilise Internet pour enregistrer et charger les données des ancres : veillez donc à ce que votre appareil soit connecté à Internet.</span><span class="sxs-lookup"><span data-stu-id="a9d97-194">Azure Spatial Anchors uses the internet to save and load the anchor data, so make sure your device is connected to the internet.</span></span>

## <a name="anchoring-an-experience"></a><span data-ttu-id="a9d97-195">Ancrage d’une expérience</span><span class="sxs-lookup"><span data-stu-id="a9d97-195">Anchoring an experience</span></span>

<span data-ttu-id="a9d97-196">Dans les sections précédentes, vous avez découverts les principes de base d’Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="a9d97-196">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="a9d97-197">Nous avons utilisé un cube pour représenter et visualiser l’objet de jeu parent avec l’ancre attachée.</span><span class="sxs-lookup"><span data-stu-id="a9d97-197">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="a9d97-198">Dans cette section, vous allez découvrir comment ancrer une expérience complète en la plaçant en tant qu’enfant de l’objet ParentAnchor.</span><span class="sxs-lookup"><span data-stu-id="a9d97-198">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

<span data-ttu-id="a9d97-199">Dans la fenêtre Hierarchy, sélectionnez l’objet **ParentAnchor** , puis dans la fenêtre Inspector, configurez les composants **Transform** comme ceci :</span><span class="sxs-lookup"><span data-stu-id="a9d97-199">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, configure the **Transform** components as follows:</span></span>

* <span data-ttu-id="a9d97-200">Affectez 1.1 à **Scale X**.</span><span class="sxs-lookup"><span data-stu-id="a9d97-200">Change **Scale X** to 1.1</span></span>
* <span data-ttu-id="a9d97-201">Affectez 1.1 à **Scale Z**.</span><span class="sxs-lookup"><span data-stu-id="a9d97-201">Change **Scale Z** to 1.1</span></span>

![Unity avec l’objet ParentAnchor sélectionné, positionné et mis à l’échelle](images/mr-learning-asa/asa-02-section8-step1-1.png)

<span data-ttu-id="a9d97-203">Dans la fenêtre Project, accédez au dossier **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** , puis cliquez sur le préfabriqué **RoverExplorer_Complete** et faites-le glisser dans la fenêtre Hierarchy pour l’ajouter à la scène :</span><span class="sxs-lookup"><span data-stu-id="a9d97-203">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** folder, then click-and-drag the **RoverExplorer_Complete** prefab into the Hierarchy window to add it to the scene:</span></span>

![Unity avec le préfabriqué nouvellement ajouté RoverExplorer_Complete sélectionné](images/mr-learning-asa/asa-02-section8-step1-2.png)

<span data-ttu-id="a9d97-205">L’objet RoverModule_Complete que vous venez d’ajouter étant toujours sélectionné dans la fenêtre Hierarchy, faites-le glisser sur l’objet **ParentAnchor** pour en faire un enfant de l’objet ParentAnchor :</span><span class="sxs-lookup"><span data-stu-id="a9d97-205">With the newly added RoverModule_Complete object still selected in the Hierarchy window, drag it onto the **ParentAnchor** object to make it a child of the ParentAnchor object:</span></span>

![Unity avec l’objet RoverExplorer_Complete défini comme enfant de ParentAnchor](images/mr-learning-asa/asa-02-section8-step1-3.png)

<span data-ttu-id="a9d97-207">Si vous regénérez le projet et déployez l’application sur votre appareil, vous pouvez à présent repositionner l’intégralité de l’expérience Rover Explorer en déplaçant le cube redimensionné.</span><span class="sxs-lookup"><span data-stu-id="a9d97-207">If you now rebuild the project and deploy the app to your device, you can now reposition the entire Rover Explorer experience by moving the resized cube.</span></span>

> [!TIP]
> <span data-ttu-id="a9d97-208">Il existe un grand nombre de flux d’expériences utilisateur pour repositionner les expériences, notamment l’utilisation d’un objet de repositionnement (comme le cube utilisé dans ce tutoriel), l’utilisation d’un bouton pour basculer un cadre englobant qui entoure l’expérience, l’utilisation de gizmos de position et de rotation, etc.</span><span class="sxs-lookup"><span data-stu-id="a9d97-208">A variety of user experience flows for repositioning experiences, including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="a9d97-209">Félicitations</span><span class="sxs-lookup"><span data-stu-id="a9d97-209">Congratulations</span></span>

<span data-ttu-id="a9d97-210">Dans ce tutoriel, vous avez découverts les principes de base d’Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="a9d97-210">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="a9d97-211">Ce tutoriel a introduit plusieurs boutons qui vous permettent d’explorer les différentes étapes nécessaires pour démarrer et arrêter une session Azure Spatial Anchors,</span><span class="sxs-lookup"><span data-stu-id="a9d97-211">This tutorial provided you with several buttons to let you explore the various steps required to start and stop an Azure Spatial Anchors session.</span></span> <span data-ttu-id="a9d97-212">et pour créer, charger et télécharger des ancres spatiales Azure sur un appareil.</span><span class="sxs-lookup"><span data-stu-id="a9d97-212">Also, to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="a9d97-213">Dans le tutoriel suivant, vous allez apprendre à enregistrer des ID d’ancre Azure dans votre HoloLens 2 pour pouvoir les récupérer même après le redémarrage de l’application, puis à transférer des ID d’ancre entre plusieurs appareils pour obtenir un alignement spatial.</span><span class="sxs-lookup"><span data-stu-id="a9d97-213">In the next tutorial, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the app is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a9d97-214">Tutoriel suivant : 3. Enregistrement, récupération et partage d’ancres spatiales Azure</span><span class="sxs-lookup"><span data-stu-id="a9d97-214">Next Tutorial: 3. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)
