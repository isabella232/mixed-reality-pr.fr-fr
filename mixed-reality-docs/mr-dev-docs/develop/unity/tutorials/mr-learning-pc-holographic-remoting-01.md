---
title: Bien démarrer avec la communication à distance holographique de PC
description: Suivez ce cours pour découvrir comment diffuser en continu à distance des applications de réalité mixte de votre PC vers HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, communication à distance holographique sur PC, info-bulles, suivi oculaire
ms.localizationpriority: high
ms.openlocfilehash: 05831ff19a998bd5e99ab5d20c3fb045a09c55e9
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175436"
---
# <a name="1-getting-started-with-pc-holographic-remoting"></a><span data-ttu-id="045f3-104">1. Bien démarrer avec la communication à distance holographique de PC</span><span class="sxs-lookup"><span data-stu-id="045f3-104">1. Getting started with PC Holographic Remoting</span></span>

<span data-ttu-id="045f3-105">Bienvenue dans les tutoriels HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="045f3-105">Welcome to the HoloLens 2 tutorials.</span></span> <span data-ttu-id="045f3-106">Dans cette série comprenant deux tutoriels, vous allez apprendre à créer une démonstration d’expérience de réalité mixte et à créer une application PC de communication à distance holographique.</span><span class="sxs-lookup"><span data-stu-id="045f3-106">In this two-part tutorial series, you will learn how to create a mixed reality experience demonstration and how to create a PC app for Holographic Remoting.</span></span>

<span data-ttu-id="045f3-107">Dans ce tutoriel, vous allez découvrir comment créer une expérience de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="045f3-107">In this tutorial, you'll learn how to create a mixed reality experience.</span></span> <span data-ttu-id="045f3-108">Il présente les éléments d’interface utilisateur, la manipulation de modèle 3D, le découpage de modèle et les fonctionnalités de suivi oculaire.</span><span class="sxs-lookup"><span data-stu-id="045f3-108">It will demonstrate UI elements, 3D model manipulation, model clipping, and eye-tracking features.</span></span>

<span data-ttu-id="045f3-109">Le deuxième tutoriel, [Créer une application de communication à distance holographique](mr-learning-pc-holographic-remoting-02.md), montre comment créer une application PC de communication à distance holographique.</span><span class="sxs-lookup"><span data-stu-id="045f3-109">In the second tutorial, [Create a Holographic Remoting application](mr-learning-pc-holographic-remoting-02.md), you will learn how to create a PC app for Holographic Remoting.</span></span> <span data-ttu-id="045f3-110">Il présente également comment connecter l’application à HoloLens 2 à tout moment pour visualiser du contenu 3D en réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="045f3-110">And connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span>

## <a name="objectives"></a><span data-ttu-id="045f3-111">Objectifs</span><span class="sxs-lookup"><span data-stu-id="045f3-111">Objectives</span></span>

* <span data-ttu-id="045f3-112">Importer les ressources et configurer la scène</span><span class="sxs-lookup"><span data-stu-id="045f3-112">Import assets and set up the scene</span></span>
* <span data-ttu-id="045f3-113">Interaction avec des hologrammes en utilisant des éléments d’interface utilisateur et des boutons</span><span class="sxs-lookup"><span data-stu-id="045f3-113">Interact with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="045f3-114">Configurer les objets 3D pour la fonctionnalité de découpage</span><span class="sxs-lookup"><span data-stu-id="045f3-114">Configure 3D objects for the clipping feature</span></span>
* <span data-ttu-id="045f3-115">Apprendre à activer des info-bulles avec le suivi oculaire</span><span class="sxs-lookup"><span data-stu-id="045f3-115">Learn about activating tooltips with eye-tracking</span></span>

## <a name="prerequisites"></a><span data-ttu-id="045f3-116">Prérequis</span><span class="sxs-lookup"><span data-stu-id="045f3-116">Prerequisites</span></span>

* <span data-ttu-id="045f3-117">PC Windows 10 configuré avec les [outils appropriés installés](../../install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="045f3-117">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="045f3-118">Connaissances de base de la programmation en C++</span><span class="sxs-lookup"><span data-stu-id="045f3-118">Basic c# programming knowledge</span></span>
* <span data-ttu-id="045f3-119">Appareil HoloLens 2 [configuré pour le développement](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="045f3-119">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="045f3-120"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> avec Unity 2020/2019 LTS monté et le module Universal Windows Platform Build Support ajouté</span><span class="sxs-lookup"><span data-stu-id="045f3-120"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2020/2019 LTS mounted, and the Universal Windows Platform Build Support module added</span></span>

<span data-ttu-id="045f3-121">Si vous n’avez pas une expérience de base avec Unity et MRTK, nous vous **recommandons vivement** de suivre la série de tutoriels [Bien démarrer](mr-learning-base-01.md) avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="045f3-121">We **strongly recommend** completing the [Getting started](mr-learning-base-01.md) tutorials series or some basic prior experience with Unity and MRTK before continuing.</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="045f3-122">Cette série de didacticiels prend en charge Unity 2020 LTS (actuellement 2020.3.x), si vous utilisez Open XR et Unity 2019 LTS (actuellement 2019.4.x), si vous utilisez le WSA hérité. Cela remplace toutes les exigences de version de Unity mentionnées dans les conditions préalables référencées ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="045f3-122">This tutorial series supports Unity 2020 LTS(currently 2020.3.x) if you are using Open XR and Unity 2019 LTS (currently 2019.4.x) if you are using Legacy WSA This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="045f3-123">Création et préparation du projet Unity</span><span class="sxs-lookup"><span data-stu-id="045f3-123">Creating and preparing the Unity project</span></span>

<span data-ttu-id="045f3-124">Dans cette section, vous allez créer un projet Unity et le préparer au développement avec MRTK.</span><span class="sxs-lookup"><span data-stu-id="045f3-124">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="045f3-125">Pour cela, suivez d’abord [Initialisation de votre projet et de votre première application](mr-learning-base-02.md), en excluant les instructions données dans [Générer votre application sur votre appareil](mr-learning-base-02.md#building-your-application-to-your-hololens-2), ce qui inclut les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="045f3-125">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="045f3-126">[Création du projet Unity](mr-learning-base-02.md#creating-the-unity-project) et affectation d’un nom pertinent, par exemple *MRTK Tutorials*</span><span class="sxs-lookup"><span data-stu-id="045f3-126">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
2. [<span data-ttu-id="045f3-127">Changement de plateforme de génération</span><span class="sxs-lookup"><span data-stu-id="045f3-127">Switching the build platform</span></span>](mr-learning-base-02.md#switching-the-build-platform)
3. [<span data-ttu-id="045f3-128">Importation des ressources TextMeshPro Essential</span><span class="sxs-lookup"><span data-stu-id="045f3-128">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="045f3-129">Importation de Mixed Reality Toolkit et configuration du projet Unity</span><span class="sxs-lookup"><span data-stu-id="045f3-129">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. <span data-ttu-id="045f3-130">[Création et définition de la scène](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk), et affectation d’un nom pertinent à la scène, par exemple **PC Holographic Remoting**</span><span class="sxs-lookup"><span data-stu-id="045f3-130">[Creating and setting the scene](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) and give the scene a suitable name, for example, **PC Holographic Remoting**</span></span>

<span data-ttu-id="045f3-131">Ensuite, suivez les instructions fournies dans [Changement de l’option d’affichage de la reconnaissance spatiale](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) pour remplacer le profil de configuration MRTK de votre scène par **DefaultHoloLens2ConfigurationProfile**.</span><span class="sxs-lookup"><span data-stu-id="045f3-131">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile**.</span></span> <span data-ttu-id="045f3-132">Choisissez **Occlusion** dans les options d’affichage du maillage de la reconnaissance spatiale.</span><span class="sxs-lookup"><span data-stu-id="045f3-132">Change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="045f3-133">Importation des ressources du tutoriel</span><span class="sxs-lookup"><span data-stu-id="045f3-133">Importing the tutorial assets</span></span>

[!INCLUDE[](includes/importing-tutorial-assets-pc-holographic-remoting.md)]

## <a name="configuring-and-preparing-the-scene"></a><span data-ttu-id="045f3-134">Création et préparation de la scène</span><span class="sxs-lookup"><span data-stu-id="045f3-134">Configuring and preparing the scene</span></span>

<span data-ttu-id="045f3-135">Dans cette section, vous allez préparer la scène en ajoutant une partie des préfabriqués du tutoriel.</span><span class="sxs-lookup"><span data-stu-id="045f3-135">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="045f3-136">Dans la fenêtre Project, accédez au dossier **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs**.</span><span class="sxs-lookup"><span data-stu-id="045f3-136">In the Project window, navigate to **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs** folder.</span></span> <span data-ttu-id="045f3-137">Tout en maintenant la touche Ctrl enfoncée, cliquez sur les six préfabriqués ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="045f3-137">While holding down the CTRL button, click on the below six prefabs.</span></span>

* <span data-ttu-id="045f3-138">ButtonParent</span><span class="sxs-lookup"><span data-stu-id="045f3-138">ButtonParent</span></span>
* <span data-ttu-id="045f3-139">ClippingObjects</span><span class="sxs-lookup"><span data-stu-id="045f3-139">ClippingObjects</span></span>
* <span data-ttu-id="045f3-140">HandSpatialMapButton</span><span class="sxs-lookup"><span data-stu-id="045f3-140">HandSpatialMapButton</span></span>
* <span data-ttu-id="045f3-141">Instructions</span><span class="sxs-lookup"><span data-stu-id="045f3-141">Instructions</span></span>
* <span data-ttu-id="045f3-142">ModelParent</span><span class="sxs-lookup"><span data-stu-id="045f3-142">ModelParent</span></span>
* <span data-ttu-id="045f3-143">Plate-forme</span><span class="sxs-lookup"><span data-stu-id="045f3-143">Platform</span></span>

![Unity avec des préfabriqués à ajouter à la scène sélectionnée](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-1.png)

<span data-ttu-id="045f3-145">Faites glisser-déposer ces modèles du dossier Prefabs vers la **fenêtre Hierarchy**.</span><span class="sxs-lookup"><span data-stu-id="045f3-145">Drag-and-drop these models from the prefabs folder into the **Hierarchy window**.</span></span>

![Unity avec des préfabriqués nouvellement ajoutés encore sélectionnés](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-2.png)

<span data-ttu-id="045f3-147">Pour vous concentrer sur les objets de la scène, vous pouvez double-cliquer sur l’objet **ModelParent**, puis faire un léger zoom avant :</span><span class="sxs-lookup"><span data-stu-id="045f3-147">To focus in on the objects in the scene, you can double-click on the **ModelParent** object, and then zoom slightly in again:</span></span>

![Unity avec l’objet ModelParent dans le focus](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-3.png)

> [!TIP]
> <span data-ttu-id="045f3-149">Si vous trouvez gênantes les grandes icônes de votre scène, par exemple les grandes icônes « T », vous pouvez les masquer en <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">basculant les gizmos</a> en position Off.</span><span class="sxs-lookup"><span data-stu-id="045f3-149">If you find the large icons in your scene, such as, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="045f3-150">Configuration des boutons pour faire fonctionner la scène</span><span class="sxs-lookup"><span data-stu-id="045f3-150">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="045f3-151">Dans cette section, vous allez ajouter des scripts dans la scène pour créer des événements de bouton illustrant les notions de base des fonctionnalités de changement et de découpage de modèle.</span><span class="sxs-lookup"><span data-stu-id="045f3-151">In this section, you will add scripts into the scene to create button events demonstrating the fundamentals of model switching and clipping functionality.</span></span>

### <a name="1-configuring-the-interactable-script-component"></a><span data-ttu-id="045f3-152">1. Configuration du composant Interactable (Script)</span><span class="sxs-lookup"><span data-stu-id="045f3-152">1. Configuring the Interactable (Script) component</span></span>

<span data-ttu-id="045f3-153">Dans la fenêtre Hierarchy, développez l’objet **ButtonParent**, puis sélectionnez **NextButton**.</span><span class="sxs-lookup"><span data-stu-id="045f3-153">In the Hierarchy window, expand the **ButtonParent** object and select the **NextButton**.</span></span> <span data-ttu-id="045f3-154">Dans la fenêtre Inspector, localisez le composant **Interactable (Script)** , puis cliquez sur l’icône **+** sous l’événement **OnClick ()** .</span><span class="sxs-lookup"><span data-stu-id="045f3-154">In the Inspector window, locate the **Interactable (Script)** component and click on **+** icon under **OnClick ()** event.</span></span>

![Unity avec l’événement OnClick de NextButton ajouté](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-1.png)

<span data-ttu-id="045f3-156">L’objet **NextButton** étant toujours sélectionné dans la fenêtre Hierarchy, cliquez sur l’objet **ButtonParent** et faites-le glisser de la fenêtre Hierarchy vers le champ vide **None (Object)** de l’événement que vous venez d’ajouter pour que l’objet ButtonParent soit à l’écoute des événements de type « clic sur un bouton » provenant de ce bouton :</span><span class="sxs-lookup"><span data-stu-id="045f3-156">With the **NextButton** object still selected in the Hierarchy window, click-and-drag the **ButtonParent** object from the Hierarchy window into the empty **None (Object)** field of the event you just added to make the ButtonParent object listen for button click event from this button:</span></span>

![Unity avec l’écouteur d’événements OnClick de NextButton configuré](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-2.png)

<span data-ttu-id="045f3-158">Cliquez sur la liste déroulante **No Function** du même événement.</span><span class="sxs-lookup"><span data-stu-id="045f3-158">Click the **No Function** dropdown of the same event.</span></span> <span data-ttu-id="045f3-159">Sélectionnez ensuite **ViewButtonControl** > **NextModel ()** pour définir la fonction **NextModel ()** comme l’action à déclencher quand l’événement d’appui sur un bouton est déclenché par ce bouton :</span><span class="sxs-lookup"><span data-stu-id="045f3-159">Then select **ViewButtonControl** > **NextModel ()** to set the **NextModel ()** function as the action that is triggered when the button pressed events is fired from this button:</span></span>

![Unity avec le chemin de sélection d’action de l’événement OnClick de NextButton](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-3.png)

### <a name="2-configuring-the-remaining-buttons"></a><span data-ttu-id="045f3-161">2. Configuration des boutons restants</span><span class="sxs-lookup"><span data-stu-id="045f3-161">2. Configuring the remaining buttons</span></span>

<span data-ttu-id="045f3-162">Pour chacun des boutons restants, effectuez le processus décrit ci-dessus pour affecter des fonctions aux événements **OnClick ()**  :</span><span class="sxs-lookup"><span data-stu-id="045f3-162">For each of the remaining buttons, complete the process outlined above to assign functions to the **OnClick ()** events:</span></span>

* <span data-ttu-id="045f3-163">Pour l’objet PreviousButton, affectez la fonction **ViewButtonControl** > **PreviousModel ()** .</span><span class="sxs-lookup"><span data-stu-id="045f3-163">For PreviousButton object, assign the **ViewButtonContro** l > **PreviousModel ()** function.</span></span>

* <span data-ttu-id="045f3-164">Pour ClippingButton, sélectionnez la fonction **ToggleButton** > **ToggleClipping ()** .</span><span class="sxs-lookup"><span data-stu-id="045f3-164">For ClippingButton select **ToggleButton** > **ToggleClipping ()** function.</span></span>

### <a name="3-configuring-the-view-button-control-script--and-toggle-button-script-components"></a><span data-ttu-id="045f3-165">3. Configuration des composants View Button Control (Script) et Toggle Button (Script)</span><span class="sxs-lookup"><span data-stu-id="045f3-165">3. Configuring the View Button Control (Script)  and Toggle Button (Script) components</span></span>

<span data-ttu-id="045f3-166">Vos boutons sont maintenant configurés pour illustrer les fonctionnalités de changement et de découpage de modèle.</span><span class="sxs-lookup"><span data-stu-id="045f3-166">Now your buttons are configured to demonstrate the model switching and clipping functionality.</span></span> <span data-ttu-id="045f3-167">Il est temps d’ajouter des modèles 3D et des objets de découpage au script.</span><span class="sxs-lookup"><span data-stu-id="045f3-167">It is time to add 3D models and the clipping objects to the script.</span></span>

<span data-ttu-id="045f3-168">Six modèles 3D différents sont fournis à des fins de démonstration. Pour les exposer, développez ***ModelParentobject***.</span><span class="sxs-lookup"><span data-stu-id="045f3-168">We have provided six different 3D models for demonstration, expand the ***ModelParentobject*** to expose these 3D models.</span></span>

<span data-ttu-id="045f3-169">L’objet ButtonParent étant toujours sélectionné dans la fenêtre Hierarchy, dans la fenêtre Inspector, recherchez le composant **View Button Control (Script)** , puis développez la variable **Models**.</span><span class="sxs-lookup"><span data-stu-id="045f3-169">With the ButtonParent object still selected in the Hierarchy window, in the Inspector window, locate the **View Button Control (Script)** component and expand the **Models** variable.</span></span>

<span data-ttu-id="045f3-170">Dans le champ **Size**, entrez le nombre de modèles 3D que vous aimeriez avoir dans votre scène.</span><span class="sxs-lookup"><span data-stu-id="045f3-170">In the **Size** field, enter the number of 3D models you would like to have in your scene.</span></span> <span data-ttu-id="045f3-171">Dans ce cas, indiquez six.</span><span class="sxs-lookup"><span data-stu-id="045f3-171">In this case, it would be six.</span></span> <span data-ttu-id="045f3-172">Des champs permettant d’ajouter de nouveaux modèles 3D sont créés.</span><span class="sxs-lookup"><span data-stu-id="045f3-172">It will create fields for adding new 3D models.</span></span>

![Unity avec les champs du composant de script ViewButtonControl](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-1.png)

<span data-ttu-id="045f3-174">Faites glisser-déposer chaque objet enfant de l’objet ModelParent sur ces champs.</span><span class="sxs-lookup"><span data-stu-id="045f3-174">Drag and drop each child object of ModelParent Object into these fields.</span></span>

![Unity avec les champs du composant de script ViewButtonControl configurés](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-2.png)

<span data-ttu-id="045f3-176">Faites glisser-déposer l’objet **ClippingObjects** de la fenêtre Hierarchy sur le champ **Clipping Object** du composant **Toggle Button (Script)**</span><span class="sxs-lookup"><span data-stu-id="045f3-176">Drag and drop the  **ClippingObjects** object from the Hierarchy window to the  **Toggle Button (Script)** component **Clipping Object** field.</span></span>
>[!NOTE]
><span data-ttu-id="045f3-177">Restez dans l’objet ButtonParent.</span><span class="sxs-lookup"><span data-stu-id="045f3-177">Stay in button parent object only.</span></span>

![Unity avec les champs du composant de script ToggleButton configurés](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-3.png)

<span data-ttu-id="045f3-179">Dans la fenêtre Hierarchy, sélectionnez le préfabriqué **ClippingObjects** et activez-le dans la fenêtre Inspector pour activer les objets de découpage.</span><span class="sxs-lookup"><span data-stu-id="045f3-179">In the Hierarchy window, select the **ClippingObjects** prefab and enable it in the Inspector window to turn on the Clipping objects.</span></span>

## <a name="configuring-the-clipping-objects-to-enable-clipping-feature"></a><span data-ttu-id="045f3-180">Configuration des objets de découpage pour activer la fonctionnalité de découpage</span><span class="sxs-lookup"><span data-stu-id="045f3-180">Configuring the clipping objects to enable clipping feature</span></span>

<span data-ttu-id="045f3-181">Dans cette section, vous allez ajouter le renderer d’objets enfants de l’objet MarsCuriosityRover dans un objet de découpage individuel pour illustrer le découpage du modèle MarsCuriosityRover.</span><span class="sxs-lookup"><span data-stu-id="045f3-181">In this section, you will add MarsCuriosityRover object's child objects renderer into an individual clipping object to demonstrate the clipping of the MarsCuriosityRover model.</span></span>

<span data-ttu-id="045f3-182">Dans la fenêtre Hierarchy, développez l’objet **ClippingObjects** pour exposer les trois objets de découpage que vous allez utiliser dans ce projet.</span><span class="sxs-lookup"><span data-stu-id="045f3-182">In the Hierarchy window, expand the **ClippingObjects** object to expose the three different clipping objects that you will be using in this project.</span></span>

<span data-ttu-id="045f3-183">Pour configurer l’objet **ClippingSphere**, cliquez dessus, puis dans la fenêtre Inspector, recherchez le composant **Clipping Sphere (Script)** .</span><span class="sxs-lookup"><span data-stu-id="045f3-183">To configure the **ClippingSphere** object, click on it, and in the Inspector window, locate the **Clipping Sphere (Script)** component.</span></span> <span data-ttu-id="045f3-184">Dans le champ Size, entrez le nombre de renderers à ajouter pour votre modèle 3D.</span><span class="sxs-lookup"><span data-stu-id="045f3-184">Enter the number of renderers in the size field that you need to add for your 3D model.</span></span> <span data-ttu-id="045f3-185">Dans ce cas, entrez 10 pour les objets enfants de MarsCuriosityRover.</span><span class="sxs-lookup"><span data-stu-id="045f3-185">In this case, add 10 for MarsCuriosityRover child objects.</span></span> <span data-ttu-id="045f3-186">Des champs permettant d’ajouter des renderers sont créés. Glissez-déposez les objets enfants du modèle MarsCuriosityRover sur ces champs.</span><span class="sxs-lookup"><span data-stu-id="045f3-186">It will create fields for adding renderers, drag and drop MarsCuriosityRover Object's child model objects into these fields.</span></span>

![Unity avec les champs du composant de script ClippingSphere configurés](images/mrlearning-pc-holographic-remoting/Tutorial1-Section5-Step1-1.png)

<span data-ttu-id="045f3-188">Suivez le même processus et ajoutez les renderers d’objets enfants de MarsCuriosityRover aux objets **ClippingBox** et **ClippingPlane**.</span><span class="sxs-lookup"><span data-stu-id="045f3-188">Follow the same process and add MarsCuriosityRover's child objects renderers to the **ClippingBox** and **ClippingPlane** objects.</span></span>

<span data-ttu-id="045f3-189">Dans ce tutoriel, seul le modèle MarsCuriosityRover est utilisé pour illustrer la fonctionnalité de découpage.</span><span class="sxs-lookup"><span data-stu-id="045f3-189">In this tutorial, only the MarsCuriosityRover model will be used for demonstrating the clipping feature.</span></span> <span data-ttu-id="045f3-190">Il est possible d’ajouter des fonctionnalités de découpage à d’autres modèles, d’augmenter la taille du renderer et d’ajouter des renderers de maillage individuels.</span><span class="sxs-lookup"><span data-stu-id="045f3-190">They were adding clipping features to more models, increasing the size of the renderer, and adding their individual mesh renderers.</span></span>

## <a name="configuring-eye-tracking-to-highlight-tooltips"></a><span data-ttu-id="045f3-191">Configuration du suivi oculaire pour mettre en évidence les info-bulles</span><span class="sxs-lookup"><span data-stu-id="045f3-191">Configuring eye-tracking to highlight tooltips</span></span>

<span data-ttu-id="045f3-192">Dans cette section, nous allons examiner comment activer l’eye-tracking dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="045f3-192">In this section, you will explore how to enable eye tracking in your project.</span></span> <span data-ttu-id="045f3-193">Par exemple, vous allez implémenter les fonctionnalités nécessaires pour mettre en évidence les info-bulles attachées aux éléments de MarsCuriosityRover quand vous les regardez et les masquer quand vous détournez votre regard.</span><span class="sxs-lookup"><span data-stu-id="045f3-193">For example, you will implement the functionality to highlight tooltips attached to MarsCuriosityRover's parts while looking at them and hiding them, while you are looking away from them.</span></span>

### <a name="1-identify-target-objects-and-associated-tooltips"></a><span data-ttu-id="045f3-194">1. Identifier les objets cibles et les info-bulles associées</span><span class="sxs-lookup"><span data-stu-id="045f3-194">1. Identify target objects and associated tooltips</span></span>

<span data-ttu-id="045f3-195">Dans la fenêtre Hierarchy, sélectionnez l’objet ModelParent.</span><span class="sxs-lookup"><span data-stu-id="045f3-195">In the Hierarchy window, select the ModelParent object.</span></span> <span data-ttu-id="045f3-196">Développez ***MarsCuriosity -> Rover** _ pour trouver les cinq éléments principaux du MarsCuriosityRover: _*POI-Camera\*\*, **POI-Wheels**, **POI-Antena**, **POI-Spectrometer**, **POI-RUHF Antenna**.</span><span class="sxs-lookup"><span data-stu-id="045f3-196">Expand the ***MarsCuriosity -> Rover** _ to find five main parts of the MarsCuriosityRover: _*POI-Camera\*\*, **POI-Wheels**, **POI-Antena**, **POI-Spectrometer**, **POI-RUHF Antenna**.</span></span>

* <span data-ttu-id="045f3-197">Observez les cinq objets info-bulles associés aux éléments de MarsCuriosityRover dans la fenêtre Hierarchy.</span><span class="sxs-lookup"><span data-stu-id="045f3-197">Observe five corresponding tooltip objects associated with MarsCuriosityRover parts in the Hierarchy window.</span></span>
* <span data-ttu-id="045f3-198">Vous allez configurer ces objets pour les mettre en évidence quand vous regardez les éléments MarsCuriosityRover correspondants.</span><span class="sxs-lookup"><span data-stu-id="045f3-198">You will be configuring these objects to highlight the experience when you look at the MarsCuriosityRover parts.</span></span>

![Unity avec l’objet Rover sélectionné et développé](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step1-1.png)

### <a name="2-implement-while-looking-at-target-----on-look-away--events"></a><span data-ttu-id="045f3-200">2. Implémenter les événements While Looking At Target () et On Look Away ()</span><span class="sxs-lookup"><span data-stu-id="045f3-200">2. Implement While Looking At Target ()  &  On Look Away () events</span></span>

<span data-ttu-id="045f3-201">Dans la fenêtre Hierarchy, sélectionnez l’objet **POI-Camera** _.</span><span class="sxs-lookup"><span data-stu-id="045f3-201">In the Hierarchy window, select the \***POI-Camera** _ object.</span></span> <span data-ttu-id="045f3-202">Dans la fenêtre Inspector, recherchez le composant *Eye Tracking Target (Script)* , puis configurez les événements **While Looking At Target ()**  & **On Look Away ()** comme suit :</span><span class="sxs-lookup"><span data-stu-id="045f3-202">In the Inspector window, locate the _ *Eye Tracking Target (Script)*\* component and configure the **While Looking At Target ()** & **On Look Away ()** events as follows:</span></span>

* <span data-ttu-id="045f3-203">Affectez au champ **None (Object)** l’objet **POI-Camera ToolTip**.</span><span class="sxs-lookup"><span data-stu-id="045f3-203">To **None (Object)** field, assign the **POI-Camera ToolTip** object</span></span>
* <span data-ttu-id="045f3-204">Dans la liste déroulante **No Function** de l’événement **While Looking At Target ()** , sélectionnez **GameObject** > **SetActive (bool)** .</span><span class="sxs-lookup"><span data-stu-id="045f3-204">From **No Function** dropdown of **While Looking At Target ()** event, select **GameObject** > **SetActive (bool).**</span></span> <span data-ttu-id="045f3-205">Cochez la **case** située en dessous pour définir la mise en évidence de l’info-bulle comme l’action à déclencher quand vous regardez l’objet cible.</span><span class="sxs-lookup"><span data-stu-id="045f3-205">Select the **Checkbox** under it to highlight the tooltip as the action that is triggered when you look at the target object.</span></span>

![Unity avec la configuration de l’événement EyeTrackingTarget WhileLookingAtTarget en cours](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-1.png)

* <span data-ttu-id="045f3-207">Suivez le même processus et cliquez sur la liste déroulante **No Function** du détecteur d’événements **On Look Away ()** .</span><span class="sxs-lookup"><span data-stu-id="045f3-207">Follow the same process and click on the **No Function** dropdown of the **On Look Away ()** event listener.</span></span> <span data-ttu-id="045f3-208">Sélectionnez ensuite **GameObject** > **SetActive (bool**), mais ne cochez pas la **case** pour définir le masquage de l’info-bulle comme l’action à déclencher quand vous détournez votre regard de l’objet cible.</span><span class="sxs-lookup"><span data-stu-id="045f3-208">Then select **GameObject** > **SetActive (bool**) and leave the **Checkbox** empty to hide the tooltip as the action that is triggered when you look away from the target object.</span></span>

![Unity avec l’événement EyeTrackingTarget OnLookAway configuré](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-2.png)

<span data-ttu-id="045f3-210">Suivez le même processus et affectez aux événements **While Looking At Target ()**  & **On Look Away ()** les objets info-bulles qui correspondent aux éléments de **MarsCuriosityRover**.</span><span class="sxs-lookup"><span data-stu-id="045f3-210">Follow the same process and assign respective tooltip objects to their same **MarsCuriosityRover** parts **While Looking At Target ()** & **On Look Away ()** events.</span></span>

<span data-ttu-id="045f3-211">Pour activer le suivi oculaire, suivez ces [instructions](/windows/mixed-reality/mrlearning-base-ch5#5-enable-simulated-eye-tracking-for-in-editor-simulations).</span><span class="sxs-lookup"><span data-stu-id="045f3-211">To enable eye tracking, please follow these [guidelines](/windows/mixed-reality/mrlearning-base-ch5#5-enable-simulated-eye-tracking-for-in-editor-simulations).</span></span>

## <a name="congratulations"></a><span data-ttu-id="045f3-212">Félicitations</span><span class="sxs-lookup"><span data-stu-id="045f3-212">Congratulations</span></span>

<span data-ttu-id="045f3-213">Dans ce tutoriel, vous avez appris à créer une expérience de réalité mixte illustrant les éléments d’interface utilisateur, la manipulation de modèle 3D, le découpage de modèle et les fonctionnalités de suivi oculaire.</span><span class="sxs-lookup"><span data-stu-id="045f3-213">In this tutorial, you learned to build a mixed reality experience demonstrating UI elements, 3D model manipulation, model clipping, and eye-tracking features.</span></span> <span data-ttu-id="045f3-214">Les objets NextButton et PreviousButton introduits dans ce tutoriel vous ont permis d’explorer la visionneuse de modèle 3D.</span><span class="sxs-lookup"><span data-stu-id="045f3-214">The tutorial provided you with NextButton and PreviousButton that let you explore the 3D model viewer experience.</span></span> <span data-ttu-id="045f3-215">L’objet ClippingObjectButton vous a quant a lui permis d’activer des objets de découpage et de vous familiariser avec la fonctionnalité de découpage.</span><span class="sxs-lookup"><span data-stu-id="045f3-215">The ClippingObjectButton made you turn on clipping objects and experience clipping feature.</span></span> <span data-ttu-id="045f3-216">Dans ce tutoriel, vous avez également examiné un élément de suivi oculaire pour activer la mise en évidence des info-bulles dans l’expérience.</span><span class="sxs-lookup"><span data-stu-id="045f3-216">The tutorial also provided you with an eye-tracking element to enable highlighting the tooltips in the experience.</span></span>

<span data-ttu-id="045f3-217">Dans la leçon suivante, vous allez découvrir comment créer une application de communication à distance holographique pour PC et comment la connecter à HoloLens 2 à tout moment pour visualiser du contenu 3D en réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="045f3-217">In the next lesson, you will learn how to create a Holographic Remoting application for PC to connect HoloLens 2 at any point, providing a way to Visualize 3D content in mixed reality.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="045f3-218">Leçon suivante : 2. Créer une application de communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="045f3-218">Next Lesson: 2. Create Holographic Remoting application</span></span>](mr-learning-pc-holographic-remoting-02.md)