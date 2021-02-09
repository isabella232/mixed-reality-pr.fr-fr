---
title: Intégration d’Azure Spatial Anchors dans une expérience partagée
description: Suivez ce cours pour découvrir comment utiliser Azure Spatial Anchors pour ancrer des objets dans une application HoloLens 2 multi-utilisateur partagée.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, fonctionnalités multi-utilisateurs, Photon, MRTK, mixed reality toolkit, UWP, ancres spatiales Azure
ms.localizationpriority: high
ms.openlocfilehash: 4eb7470487a584ef820be82f651ed9bd16392395
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590221"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="356fe-104">5. Intégration d’Azure Spatial Anchors dans une expérience partagée</span><span class="sxs-lookup"><span data-stu-id="356fe-104">5. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="356fe-105">Dans ce tutoriel, vous allez apprendre à intégrer Azure Spatial Anchors (ASA) à l’expérience partagée.</span><span class="sxs-lookup"><span data-stu-id="356fe-105">In this tutorial, you will learn how to integrate Azure Spatial Anchors (ASA) into the shared experience.</span></span> <span data-ttu-id="356fe-106">ASA permet à plusieurs appareils d’avoir une référence commune au monde physique pour que les utilisateurs se voient à leur emplacement physique réel et voient l’expérience partagée au même endroit.</span><span class="sxs-lookup"><span data-stu-id="356fe-106">ASA allows multiple devices to have a common reference to the physical world so that the users see each other in their actual physical location and see the shared experience in the same place.</span></span>

## <a name="objectives"></a><span data-ttu-id="356fe-107">Objectifs</span><span class="sxs-lookup"><span data-stu-id="356fe-107">Objectives</span></span>

* <span data-ttu-id="356fe-108">Intégrer ASA à une expérience partagée pour l’alignement de plusieurs appareils</span><span class="sxs-lookup"><span data-stu-id="356fe-108">Integrate ASA into a shared experience for multi-device alignment</span></span>
* <span data-ttu-id="356fe-109">Découvrir les principes de base du fonctionnement d’ASA dans le contexte d’une expérience partagée locale</span><span class="sxs-lookup"><span data-stu-id="356fe-109">Learn the fundamentals of how ASA works in the context of a local shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="356fe-110">Préparation de la scène</span><span class="sxs-lookup"><span data-stu-id="356fe-110">Preparing the scene</span></span>

<span data-ttu-id="356fe-111">Dans la fenêtre Hierarchy, développez l’objet **SharedPlayground**, puis l’objet **TableAnchor** pour exposer ses objets enfants :</span><span class="sxs-lookup"><span data-stu-id="356fe-111">In the Hierarchy window, expand the **SharedPlayground** object, then expand the **TableAnchor** object to expose its child objects:</span></span>

![Unity avec les objets SharedPlayground et TableAnchor développés](images/mr-learning-sharing/sharing-05-section1-step1-1.png)

<span data-ttu-id="356fe-113">Dans la fenêtre Project, accédez au dossier **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs**, puis faites glisser le préfabriqué **Buttons** sur l’objet enfant **TableAnchor** afin de l’ajouter à votre scène en tant qu’enfant de l’objet TableAnchor :</span><span class="sxs-lookup"><span data-stu-id="356fe-113">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder and drag the **Buttons** prefab onto the **TableAnchor** child object to add it to your scene as a child of the TableAnchor object:</span></span>

![Unity avec le préfabriqué nouvellement ajouté Buttons sélectionné](images/mr-learning-sharing/sharing-05-section1-step1-2.png)

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="356fe-115">Configuration des boutons pour faire fonctionner la scène</span><span class="sxs-lookup"><span data-stu-id="356fe-115">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="356fe-116">Dans cette section, vous allez configurer une série d’événements de bouton qui illustrent les principes de base d’Azure Spatial Anchors pour obtenir un alignement spatial dans une expérience partagée.</span><span class="sxs-lookup"><span data-stu-id="356fe-116">In this section, you will configure a series of button events demonstrating the fundamentals of how Azure Spatial Anchors can be used to achieve spatial alignment in a shared experience.</span></span>

<span data-ttu-id="356fe-117">Dans la fenêtre Hierarchy, développez l’objet **Button** et sélectionnez le premier bouton enfant nommé **StartAzureSession** :</span><span class="sxs-lookup"><span data-stu-id="356fe-117">In the Hierarchy window, expand the **Button** object and select the first child button object named **StartAzureSession**:</span></span>

![Unity avec l’objet de bouton StartAzureSession sélectionné](images/mr-learning-sharing/sharing-05-section2-step1-1.png)

<span data-ttu-id="356fe-119">Dans la fenêtre Inspector, localisez le composant **Interactable (Script)** et configurez l’événement **OnClick ()** comme suit :</span><span class="sxs-lookup"><span data-stu-id="356fe-119">In the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="356fe-120">Affectez au champ **None (Object)** l’objet **TableAnchor**.</span><span class="sxs-lookup"><span data-stu-id="356fe-120">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="356fe-121">Dans la liste déroulante **No Function**, sélectionnez la fonction **AnchorModuleScript** > **StartAzureSession ()** .</span><span class="sxs-lookup"><span data-stu-id="356fe-121">From the **No Function** dropdown, select the **AnchorModuleScript** > **StartAzureSession ()** function</span></span>

![Unity avec l’événement OnClick du bouton StartAzureSession configuré](images/mr-learning-sharing/sharing-05-section2-step1-2.png)

<span data-ttu-id="356fe-123">Dans la fenêtre Hierarchy, sélectionnez le deuxième objet bouton enfant nommé **CreateAzureAnchor**. Ensuite, dans la fenêtre Inspector, localisez le composant **Interactable (Script)** et configurez l’événement **OnClick ()** comme suit :</span><span class="sxs-lookup"><span data-stu-id="356fe-123">In the Hierarchy window, select the second child button object named **CreateAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="356fe-124">Affectez au champ **None (Object)** l’objet **TableAnchor**.</span><span class="sxs-lookup"><span data-stu-id="356fe-124">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="356fe-125">Dans la liste déroulante **No Function**, sélectionnez la fonction **AnchorModuleScript** > **CreateAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="356fe-125">From the **No Function** dropdown, select the **AnchorModuleScript** > **CreateAzureAnchor ()** function</span></span>
* <span data-ttu-id="356fe-126">Affectez au nouveau champ **None (Game Object)** qui apparaît l’objet **TableAnchor**.</span><span class="sxs-lookup"><span data-stu-id="356fe-126">To the new **None (Game Object)** field that appears, assign the **TableAnchor** object</span></span>

![Unity avec l’événement OnClick du bouton CreateAzureAnchor configuré](images/mr-learning-sharing/sharing-05-section2-step1-3.png)

<span data-ttu-id="356fe-128">Dans la fenêtre Hierarchy, sélectionnez le troisième objet bouton enfant nommé **ShareAzureAnchor**. Ensuite, dans la fenêtre Inspector, localisez le composant **Interactable (Script)** et configurez l’événement **OnClick ()** comme suit :</span><span class="sxs-lookup"><span data-stu-id="356fe-128">In the Hierarchy window, select the third child button object named **ShareAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="356fe-129">Affectez au champ **None (Object)** l’objet **TableAnchor**.</span><span class="sxs-lookup"><span data-stu-id="356fe-129">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="356fe-130">Dans la liste déroulante **No Function**, sélectionnez la fonction **SharingModuleScript** > **ShareAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="356fe-130">From the **No Function** dropdown, select the **SharingModuleScript** > **ShareAzureAnchor ()** function</span></span>

![Unity avec l’événement OnClick du bouton ShareAzureAnchor configuré](images/mr-learning-sharing/sharing-05-section2-step1-4.png)

<span data-ttu-id="356fe-132">Dans la fenêtre Hierarchy, sélectionnez le quatrième objet bouton enfant nommé **GetAzureAnchor**. Ensuite, dans la fenêtre Inspector, localisez le composant **Interactable (Script)** et configurez l’événement **OnClick ()** de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="356fe-132">In the Hierarchy window, select the fourth child button object named **GetAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="356fe-133">Affectez au champ **None (Object)** l’objet **TableAnchor**.</span><span class="sxs-lookup"><span data-stu-id="356fe-133">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="356fe-134">Dans la liste déroulante **No Function**, sélectionnez la fonction **SharingModuleScript** > **GetAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="356fe-134">From the **No Function** dropdown, select the **SharingModuleScript** > **GetAzureAnchor ()** function</span></span>

![Unity avec l’événement OnClick du bouton GetAzureAnchor configuré](images/mr-learning-sharing/sharing-05-section2-step1-5.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="356fe-136">Connexion de la scène à la ressource Azure</span><span class="sxs-lookup"><span data-stu-id="356fe-136">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="356fe-137">Dans la fenêtre Hierarchy, développez l’objet **SharedPlayground**, puis sélectionnez l’objet **TableAnchor**.</span><span class="sxs-lookup"><span data-stu-id="356fe-137">In the Hierarchy window, expand the **SharedPlayground** object and select the **TableAnchor** object.</span></span>

<span data-ttu-id="356fe-138">Dans la fenêtre Inspector, localisez le composant **Spatial Anchor Manager (Script)** et configurez la section **Credentials** avec les informations d’identification du compte Azure Spatial Anchors créé dans le cadre des [prérequis](mr-learning-sharing-01.md#prerequisites) pour cette série de tutoriels :</span><span class="sxs-lookup"><span data-stu-id="356fe-138">In the Inspector window, locate the **Spatial Anchor Manager (Script)** component and configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mr-learning-sharing-01.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="356fe-139">Dans le champ **Spatial Anchors Account ID**, collez la valeur **Account ID** de votre compte Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="356fe-139">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="356fe-140">Dans le champ **Spatial Anchors Account Key**, collez la valeur **Access Key** (primaire ou secondaire) de votre compte Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="356fe-140">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>

![Unity avec Spatial Anchor Manager configuré](images/mr-learning-sharing/sharing-05-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="356fe-142">Au lieu de définir l’ID et la clé du compte Spatial Anchors dans la scène, vous pouvez les définir pour l’ensemble du projet, ce qui peut être avantageux si plusieurs de vos scènes utilisent Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="356fe-142">Instead of setting the Spatial Anchors Account ID and Key in the scene, you can set it for your entire project, this can be advantageous if you have multiple scenes using ASA.</span></span> <span data-ttu-id="356fe-143">Pour ce faire, dans la fenêtre Project, accédez à la ressource Assets > AzureSpatialAnchors.SDK > Resources > **SpatialAnchorConfig**, puis définissez les valeurs dans la fenêtre Inspector.</span><span class="sxs-lookup"><span data-stu-id="356fe-143">To do this, in the Project window, navigate to the Assets > AzureSpatialAnchors.SDK > Resources > **SpatialAnchorConfig** asset, then set the values in the Inspector window.</span></span>

<span data-ttu-id="356fe-144">Dans la fenêtre Hierarchy, sélectionnez l’objet **TableAnchor** puis, dans la fenêtre Inspector, localisez le composant **Anchor Module (Script)** et configurez-le de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="356fe-144">In the Hierarchy window, select the **TableAnchor** object, then in the Inspector window, locate the **Anchor Module (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="356fe-145">Dans le champ **Public Sharing Pin** (Code secret du partage public), modifiez quelques chiffres afin que le code secret devienne unique pour votre projet.</span><span class="sxs-lookup"><span data-stu-id="356fe-145">In the **Public Sharing Pin** field, change a few digits, so the pin becomes unique to your project</span></span>

![Unity avec Anchor Module Script configuré](images/mr-learning-sharing/sharing-05-section3-step1-2.png)

<span data-ttu-id="356fe-147">L’objet **TableAnchor** étant toujours sélectionné, vérifiez que tous les composants de script sont activés (**enabled**) dans la fenêtre Inspector :</span><span class="sxs-lookup"><span data-stu-id="356fe-147">With the **TableAnchor** object still selected, in the Inspector window, make sure all the script components are **enabled**:</span></span>

* <span data-ttu-id="356fe-148">Cochez la case en regard du composant **Spatial Anchor Manager (Script)** pour l’activer.</span><span class="sxs-lookup"><span data-stu-id="356fe-148">Check the checkbox next to the **Spatial Anchor Manager (Script)** components to enable it</span></span>
* <span data-ttu-id="356fe-149">Cochez la case en regard du composant **Anchor Module Script (Script)** pour l’activer.</span><span class="sxs-lookup"><span data-stu-id="356fe-149">Check the checkbox next to the **Anchor Module Script (Script)** components to enable it</span></span>
* <span data-ttu-id="356fe-150">Cochez la case en regard du composant **Sharing Module Script (Script)** pour l’activer.</span><span class="sxs-lookup"><span data-stu-id="356fe-150">Check the checkbox next to the **Sharing Module Script (Script)** components to enable it</span></span>

![Unity avec tous les composants du script TableAnchor activés](images/mr-learning-sharing/sharing-05-section3-step1-3.png)

## <a name="trying-the-experience-with-spatial-alignment"></a><span data-ttu-id="356fe-152">Essai de l’expérience avec l’alignement spatial</span><span class="sxs-lookup"><span data-stu-id="356fe-152">Trying the experience with spatial alignment</span></span>

> [!NOTE]
> <span data-ttu-id="356fe-153">Azure Spatial Anchors ne peut pas s’exécuter dans Unity.</span><span class="sxs-lookup"><span data-stu-id="356fe-153">Azure Spatial Anchors can not run in Unity.</span></span> <span data-ttu-id="356fe-154">Pour tester la fonctionnalité Azure Spatial Anchors, vous devez donc déployer le projet sur au moins deux appareils.</span><span class="sxs-lookup"><span data-stu-id="356fe-154">Consequently, to test the Azure Spatial Anchors functionality, you need to deploy the project to a minimum of two devices.</span></span>

<span data-ttu-id="356fe-155">Si vous générez et déployez le projet Unity sur deux appareils, vous pouvez obtenir un alignement spatial entre eux en partageant l’ID d’ancre Azure.</span><span class="sxs-lookup"><span data-stu-id="356fe-155">If you now build and deploy the Unity project to two devices, you can achieve spatial alignment between the devices by sharing the Azure Anchor ID.</span></span> <span data-ttu-id="356fe-156">Pour le tester, vous pouvez effectuer ces étapes :</span><span class="sxs-lookup"><span data-stu-id="356fe-156">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="356fe-157">Sur l’appareil 1 : **Démarrez l’application** (le Rover Explorer est instancié et placé dans la table).</span><span class="sxs-lookup"><span data-stu-id="356fe-157">On device 1: **Start the app** (the Rover Explorer is instantiated and placed on the table)</span></span>
2. <span data-ttu-id="356fe-158">Sur l’appareil 2 : **Démarrez l’application** (les deux utilisateurs voient la table avec le Rover Explorer, mais la table ne s’affiche pas au même endroit et les avatars des utilisateurs ne s’affichent pas là où se trouvent les utilisateurs).</span><span class="sxs-lookup"><span data-stu-id="356fe-158">On device 2: **Start the app** (both users see the table with the Rover Explorer, but the table does not appear in the same place, and the user avatars do not appear where the users are)</span></span>
3. <span data-ttu-id="356fe-159">Sur l’appareil 1 : Appuyez sur le bouton **Start Azure Session**.</span><span class="sxs-lookup"><span data-stu-id="356fe-159">On device 1: Press the **Start Azure Session** button</span></span>
4. <span data-ttu-id="356fe-160">Sur l’appareil 1 : Appuyez sur le bouton **Create Azure Anchor** (crée une ancre à l’emplacement de l’objet TableAnchor et stocke les informations d’ancrage dans la ressource Azure).</span><span class="sxs-lookup"><span data-stu-id="356fe-160">On device 1: Press the **Create Azure Anchor** button (creates anchor at the location of the TableAnchor object and stores the anchor information in the Azure resource).</span></span>
5. <span data-ttu-id="356fe-161">Sur l’appareil 1 : Appuyez sur le bouton **Share Azure Anchor** (partage l’ID d’ancre avec d’autres utilisateurs en temps réel).</span><span class="sxs-lookup"><span data-stu-id="356fe-161">On device 1: Press the **Share Azure Anchor** button (shares the anchor ID with other users in real-time)</span></span>
6. <span data-ttu-id="356fe-162">Sur l’appareil 2 : Appuyez sur le bouton **Start Azure Session**.</span><span class="sxs-lookup"><span data-stu-id="356fe-162">On device 2: Press the **Start Azure Session** button</span></span>
7. <span data-ttu-id="356fe-163">Sur l’appareil 2 : Appuyez sur le bouton **Get Azure Anchor** (se connecte à la ressource Azure pour récupérer les informations d’ancrage de l’ID d’ancre partagé, puis déplace l’objet TableAnchor à l’emplacement où l’ancre a été créée avec l’appareil 1).</span><span class="sxs-lookup"><span data-stu-id="356fe-163">On device 2: Press the **Get Azure Anchor** button (connects to the Azure resource to retrieve the anchor information for the shared anchor ID, then moves the TableAnchor object to the location where the anchor was created with the device 1)</span></span>

> [!TIP]
> <span data-ttu-id="356fe-164">Si vous n’avez pas accès à deux appareils HoloLens, suivez les instructions fournies dans [Création d’ancres spatiales Azure pour les appareils mobiles](mr-learning-asa-05.md) afin de déployer le projet sur votre appareil mobile.</span><span class="sxs-lookup"><span data-stu-id="356fe-164">If you don't have access to two HoloLens devices, you may follow the [Building Azure Spatial Anchors for mobile devices](mr-learning-asa-05.md) to deploy the project to your mobile device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="356fe-165">Félicitations</span><span class="sxs-lookup"><span data-stu-id="356fe-165">Congratulations</span></span>

<span data-ttu-id="356fe-166">Dans ce tutoriel, vous avez appris à intégrer des ancres spatiales, une fonctionnalité puissante d’Azure, pour aligner des appareils dans une expérience partagée.</span><span class="sxs-lookup"><span data-stu-id="356fe-166">In this tutorial, you learned how to integrate Azure's powerful Spatial Anchors to align devices in a shared experience.</span></span>

<span data-ttu-id="356fe-167">Ainsi se conclut cette série de tutoriels où vous avez appris à configurer un compte Photon, à créer une application PUN, à intégrer PUN dans une application Unity, à configurer des avatars d’utilisateurs et des objets partagés, et enfin à aligner plusieurs participants à l’aide d’Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="356fe-167">This also concludes this tutorial series where you learned how to set up a Photon account, create a PUN app, integrate PUN into the Unity project, configure user avatars and shared objects, and finally align multiple participants using Azure Spatial Anchors.</span></span>
