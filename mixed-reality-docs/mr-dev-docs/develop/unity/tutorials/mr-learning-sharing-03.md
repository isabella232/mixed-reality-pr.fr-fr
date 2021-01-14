---
title: Connexion de plusieurs utilisateurs
description: Suivez ce cours pour découvrir comment connecter plusieurs utilisateurs dans une application de réalité mixte HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, fonctionnalités multi-utilisateurs, Photon, MRTK, mixed reality toolkit, UWP, ancres spatiales Azure
ms.localizationpriority: high
ms.openlocfilehash: 6cc77b32e9479bafeb53dcb99cba4f2f29865fd7
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007209"
---
# <a name="3-connecting-multiple-users"></a><span data-ttu-id="06d62-104">3. Connexion de plusieurs utilisateurs</span><span class="sxs-lookup"><span data-stu-id="06d62-104">3. Connecting multiple users</span></span>

<span data-ttu-id="06d62-105">Dans ce tutoriel, vous allez apprendre à connecter plusieurs utilisateurs dans le cadre d’une expérience partagée en direct.</span><span class="sxs-lookup"><span data-stu-id="06d62-105">In this tutorial, you will learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="06d62-106">À la fin du tutoriel, vous pourrez exécuter l’application sur plusieurs appareils et chaque utilisateur pourra voir l’avatar d’autres utilisateurs se déplacer en temps réel.</span><span class="sxs-lookup"><span data-stu-id="06d62-106">By the end of the tutorial, you will be able to run the app on multiple devices and have each user see the avatar of other users move in real-time.</span></span>

## <a name="objectives"></a><span data-ttu-id="06d62-107">Objectifs</span><span class="sxs-lookup"><span data-stu-id="06d62-107">Objectives</span></span>

* <span data-ttu-id="06d62-108">Découvrir comment connecter plusieurs utilisateurs dans un environnement partagé</span><span class="sxs-lookup"><span data-stu-id="06d62-108">Learn how to connect multiple users in a shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="06d62-109">Préparation de la scène</span><span class="sxs-lookup"><span data-stu-id="06d62-109">Preparing the scene</span></span>

<span data-ttu-id="06d62-110">Dans cette section, vous allez préparer la scène en ajoutant une partie des préfabriqués du tutoriel.</span><span class="sxs-lookup"><span data-stu-id="06d62-110">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="06d62-111">Dans la fenêtre Project, accédez au dossier **Assets** > **MRTK.Tutoriels.MultiUserCapabilities** > **Prefabs**, puis cliquez et faites glisser les préfabriqués suivants dans la fenêtre Hierarchy pour les ajouter à votre scène :</span><span class="sxs-lookup"><span data-stu-id="06d62-111">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="06d62-112">Préfabriqué **NetworkLobby**</span><span class="sxs-lookup"><span data-stu-id="06d62-112">**NetworkLobby** prefab</span></span>
* <span data-ttu-id="06d62-113">Préfabriqué **SharedPlayground**</span><span class="sxs-lookup"><span data-stu-id="06d62-113">**SharedPlayground** prefab</span></span>

![Unity avec les préfabriqués nouvellement ajoutés NetworkLobby et SharedPlayground sélectionnés](images/mr-learning-sharing/sharing-03-section1-step1-1.png)

<span data-ttu-id="06d62-115">Dans la fenêtre Project, accédez au dossier **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs**, puis faites glisser le préfabriqué suivant dans la fenêtre Hierarchy pour l’ajouter à votre scène :</span><span class="sxs-lookup"><span data-stu-id="06d62-115">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefab into the Hierarchy window to add it to your scene:</span></span>

* <span data-ttu-id="06d62-116">Préfabriqué **DebugWindow**</span><span class="sxs-lookup"><span data-stu-id="06d62-116">**DebugWindow** prefab</span></span>

![Unity avec le préfabriqué nouvellement ajouté DebugWindow sélectionné](images/mr-learning-sharing/sharing-03-section1-step1-2.png)

## <a name="creating-the-user-prefab"></a><span data-ttu-id="06d62-118">Création du préfabriqué utilisateur</span><span class="sxs-lookup"><span data-stu-id="06d62-118">Creating the user prefab</span></span>

<span data-ttu-id="06d62-119">Dans cette section, vous allez créer un préfabriqué qui sera utilisé pour représenter les utilisateurs dans l’expérience partagée.</span><span class="sxs-lookup"><span data-stu-id="06d62-119">In this section, you will create a prefab that will be used to represent the users in the shared experience.</span></span>

### <a name="1-create-and-configure-the-user"></a><span data-ttu-id="06d62-120">1. Créer et configurer l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="06d62-120">1. Create and configure the user</span></span>

<span data-ttu-id="06d62-121">Dans la fenêtre Hierarchy, cliquez avec le bouton droit sur une zone vide et sélectionnez **Create Empty** pour ajouter un objet vide à votre scène, nommez l’objet **PhotonUser**, puis configurez-le comme suit :</span><span class="sxs-lookup"><span data-stu-id="06d62-121">In the Hierarchy window, right-click on an empty area and select **Create Empty** to add an empty object to your scene, name the object **PhotonUser**, and configure it as follows:</span></span>

* <span data-ttu-id="06d62-122">Vérifiez que le paramètre **Position** de Transform a les valeurs X = 0, Y = 0, Z = 0 :</span><span class="sxs-lookup"><span data-stu-id="06d62-122">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0:</span></span>

![Unity avec l’objet PhotonUser nouvellement créé sélectionné](images/mr-learning-sharing/sharing-03-section2-step1-1.png)

<span data-ttu-id="06d62-124">Dans la fenêtre Hierarchy, sélectionnez l’objet **PhotonUser** puis, dans la fenêtre Inspector, utilisez le bouton **Add Component** pour ajouter le composant **Photon User (Script)** à l’objet PhotonUser :</span><span class="sxs-lookup"><span data-stu-id="06d62-124">In the Hierarchy window, select the **PhotonUser** object, then in the Inspector window, use the **Add Component** button to add the **Photon User (Script)** component to the PhotonUser object:</span></span>

![Unity avec le composant Photon User ajouté](images/mr-learning-sharing/sharing-03-section2-step1-2.png)

<span data-ttu-id="06d62-126">Dans la fenêtre Inspector, utilisez le bouton **Add Component** pour ajouter le composant **Generic Net Sync (Script)** à l’objet PhotonUser et configurez-le comme suit :</span><span class="sxs-lookup"><span data-stu-id="06d62-126">In the Inspector window, use the **Add Component** button to add the **Generic Net Sync (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="06d62-127">Cochez la case **Is User**.</span><span class="sxs-lookup"><span data-stu-id="06d62-127">Check the **Is User** checkbox</span></span>

![Unity avec le composant Generic Net Sync ajouté et configuré](images/mr-learning-sharing/sharing-03-section2-step1-3.png)

<span data-ttu-id="06d62-129">Dans la fenêtre Inspector, utilisez le bouton **Add Component** pour ajouter le composant **Photon View (Script)** à l’objet PhotonUser et configurez-le comme suit :</span><span class="sxs-lookup"><span data-stu-id="06d62-129">In the Inspector window, use the **Add Component** button to add the **Photon View (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="06d62-130">Affectez au champ **Observed Components** le composant **Generic Net Sync (Script)** .</span><span class="sxs-lookup"><span data-stu-id="06d62-130">To the **Observed Components** field, assign the **Generic Net Sync (Script)** component</span></span>

![Unity avec le composant Photon View ajouté et configuré](images/mr-learning-sharing/sharing-03-section2-step1-4.png)

### <a name="2-create-the-avatar"></a><span data-ttu-id="06d62-132">2. Créer l’avatar</span><span class="sxs-lookup"><span data-stu-id="06d62-132">2. Create the avatar</span></span>

<span data-ttu-id="06d62-133">Dans la fenêtre Project, accédez au dossier **Assets** > **MRTK** > **SDK** > **StandardAssets** > **Materials** pour rechercher les matériaux MRTK.</span><span class="sxs-lookup"><span data-stu-id="06d62-133">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **StandardAssets** > **Materials** folder to locate the MRTK materials.</span></span>

<span data-ttu-id="06d62-134">Ensuite, dans la fenêtre Hierarchy, cliquez avec le bouton droit sur l’objet **PhotonUser**, puis sélectionnez **3D Object** > **Sphere** pour créer un objet Sphere en tant qu’enfant de l’objet PhotonUser et configurez-le comme suit :</span><span class="sxs-lookup"><span data-stu-id="06d62-134">Then, in the Hierarchy window, right-click on the **PhotonUser** object and select **3D Object** > **Sphere** to create a sphere object as a child of the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="06d62-135">Vérifiez que le paramètre **Position** de Transform a les valeurs X = 0, Y = 0, Z = 0.</span><span class="sxs-lookup"><span data-stu-id="06d62-135">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="06d62-136">Changez le paramètre **Scale** de Transform en une taille appropriée, par exemple X = 0,15, Y = 0,15, Z = 0,15.</span><span class="sxs-lookup"><span data-stu-id="06d62-136">Change the Transform **Scale** to a suitable size, for example, X = 0.15, Y = 0.15, Z = 0.15</span></span>
* <span data-ttu-id="06d62-137">Affectez au champ MeshRenderer > Materials > **Element 0** le matériau **MRTK_Standard_White**</span><span class="sxs-lookup"><span data-stu-id="06d62-137">To the MeshRenderer > Materials > **Element 0** field, assign the **MRTK_Standard_White** material</span></span>

![Unity avec la sphère d’avatar nouvellement créée et configurée](images/mr-learning-sharing/sharing-03-section2-step2-1.png)

### <a name="3-create-the-prefab"></a><span data-ttu-id="06d62-139">3. Créer le préfabriqué</span><span class="sxs-lookup"><span data-stu-id="06d62-139">3. Create the prefab</span></span>

<span data-ttu-id="06d62-140">Dans la fenêtre Project, accédez au dossier **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** :</span><span class="sxs-lookup"><span data-stu-id="06d62-140">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder:</span></span>

![Fenêtre de projet Unity avec le dossier Resource sélectionné](images/mr-learning-sharing/sharing-03-section2-step3-1.png)

<span data-ttu-id="06d62-142">Le dossier Resources étant toujours sélectionné, **cliquez et faites glisser** l’objet **PhotonUser** de la fenêtre Hierarchy vers le dossier **Resources** pour transformer l’objet PhotonUser en préfabriqué :</span><span class="sxs-lookup"><span data-stu-id="06d62-142">With the Resources folder still selected, **click-and-drag** the **PhotonUser** object from the Hierarchy window into the **Resources** folder to make the PhotonUser object a prefab:</span></span>

![Unity avec le préfabriqué PhotonUser nouvellement créé sélectionné](images/mr-learning-sharing/sharing-03-section2-step3-2.png)

<span data-ttu-id="06d62-144">Dans la fenêtre Hierarchy, cliquez avec le bouton droit sur l’objet **PhotonUser** et sélectionnez **Delete** pour le supprimer de la scène :</span><span class="sxs-lookup"><span data-stu-id="06d62-144">In the Hierarchy window, right-click on the **PhotonUser** object and select **Delete** to remove it from the scene:</span></span>

![Unity avec l’objet préfabriqué nouvellement créé PhotonUser supprimé de la scène](images/mr-learning-sharing/sharing-03-section2-step3-3.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a><span data-ttu-id="06d62-146">Configuration de PUN pour instancier le préfabriqué utilisateur</span><span class="sxs-lookup"><span data-stu-id="06d62-146">Configuring PUN to instantiate the user prefab</span></span>

<span data-ttu-id="06d62-147">Dans cette section, vous allez configurer le projet pour qu’il utilise le préfabriqué PhotonUser créé dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="06d62-147">In this section, you will configure the project to use the PhotonUser prefab you created in the previous section.</span></span>

<span data-ttu-id="06d62-148">Dans la fenêtre Project, accédez au dossier **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources**.</span><span class="sxs-lookup"><span data-stu-id="06d62-148">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="06d62-149">Dans la fenêtre Hierarchy, développez l’objet **NetworkLobby** et sélectionnez l’objet enfant **NetworkRoom**. Ensuite, dans la fenêtre Inspector, localisez le composant **Photon Room (Script)** et configurez-le comme suit :</span><span class="sxs-lookup"><span data-stu-id="06d62-149">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="06d62-150">Affectez au champ **Photon User Prefab** le préfabriqué **PhotonUser** du dossier Resources.</span><span class="sxs-lookup"><span data-stu-id="06d62-150">To the **Photon User Prefab** field, assign the **PhotonUser** prefab from the Resources folder</span></span>

![Unity avec le composant Photon Room partiellement configuré](images/mr-learning-sharing/sharing-03-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a><span data-ttu-id="06d62-152">Essai de l’expérience avec plusieurs utilisateurs</span><span class="sxs-lookup"><span data-stu-id="06d62-152">Trying the experience with multiple users</span></span>

<span data-ttu-id="06d62-153">Vous pouvez à présent générer le projet Unity et le déployer sur votre HoloLens. De retour dans Unity, passez au mode Game pendant que l’application s’exécute sur votre HoloLens : vous voyez l’avatar de l’utilisateur HoloLens se déplacer quand vous bougez la tête (HoloLens) :</span><span class="sxs-lookup"><span data-stu-id="06d62-153">If you now build and deploy the Unity project to your HoloLens, then, back in Unity, enter Game mode while the app is running on your HoloLens, you will see the HoloLens user avatar move when you move your head (HoloLens) around:</span></span>

![Animation montrant Unity avec des utilisateurs en réseau](images/mr-learning-sharing/sharing-03-section4-step1-1.gif)

> [!TIP]
> <span data-ttu-id="06d62-155">Pour vous rappeler comment générer et déployer votre projet Unity sur HoloLens 2, vous pouvez vous référer aux instructions de [Génération de votre application sur votre HoloLens 2](mr-learning-base-02.md#building-and-deploying-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="06d62-155">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-and-deploying-to-your-hololens-2) instructions.</span></span>

> [!CAUTION]
> <span data-ttu-id="06d62-156">L’application doit se connecter à Photon : vérifiez donc que votre ordinateur/appareil est connecté à Internet.</span><span class="sxs-lookup"><span data-stu-id="06d62-156">The app needs to connect to Photon, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="06d62-157">Félicitations</span><span class="sxs-lookup"><span data-stu-id="06d62-157">Congratulations</span></span>

<span data-ttu-id="06d62-158">Votre projet est désormais configuré pour permettre à plusieurs utilisateurs de se connecter à la même expérience et de voir leurs mouvements.</span><span class="sxs-lookup"><span data-stu-id="06d62-158">You have successfully configured your project to allow multiple users to connect to the same experience and see each other's movements.</span></span> <span data-ttu-id="06d62-159">Dans le tutoriel suivant, vous allez implémenter des fonctionnalités pour partager les mouvements d’objets avec plusieurs appareils.</span><span class="sxs-lookup"><span data-stu-id="06d62-159">In the next tutorial, you will implement functionality so that the movements of objects are also shared across multiple devices.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="06d62-160">Tutoriel suivant : 4. Partage de mouvements d’objet avec plusieurs utilisateurs</span><span class="sxs-lookup"><span data-stu-id="06d62-160">Next Tutorial: 4. Sharing object movements with multiple users</span></span>](mr-learning-sharing-04.md)
