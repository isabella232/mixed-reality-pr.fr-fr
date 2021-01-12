---
title: Créer une application PC de communication à distance holographique
description: Suivez ce cours pour découvrir comment créer une application pour PC afin d’effectuer à distance une expérience de réalité mixte depuis votre PC vers HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, communication à distance holographique sur PC, Visual Studio
ms.localizationpriority: high
ms.openlocfilehash: fd357b0b487b948afb6ae15c9e84362e2bc1ef90
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007329"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a><span data-ttu-id="4b18b-104">2. Création d’une application PC de communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="4b18b-104">2. Creating a Holographic Remoting PC application</span></span>

<span data-ttu-id="4b18b-105">Dans ce tutoriel, vous allez apprendre à créer une application PC de communication à distance holographique et à la connecter à HoloLens 2 à tout moment pour visualiser du contenu 3D en réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="4b18b-105">In this tutorial, you will learn how to create a PC app for Holographic Remoting and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span>

## <a name="objectives"></a><span data-ttu-id="4b18b-106">Objectifs</span><span class="sxs-lookup"><span data-stu-id="4b18b-106">Objectives</span></span>

* <span data-ttu-id="4b18b-107">Configurer Unity pour la communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="4b18b-107">Configure Unity for Holographic Remoting</span></span>
* <span data-ttu-id="4b18b-108">Apprendre à créer et déployer l’application avec Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4b18b-108">Learn how to build and deploy the application with Visual Studio</span></span>
* <span data-ttu-id="4b18b-109">Développer une application de communication à distance holographique et la connecter à HoloLens</span><span class="sxs-lookup"><span data-stu-id="4b18b-109">Developing Holographic Remoting application and connecting to HoloLens</span></span>

## <a name="configuring-your-scene-for-holographic-remoting"></a><span data-ttu-id="4b18b-110">Configuration de votre scène pour la communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="4b18b-110">Configuring your scene for Holographic Remoting</span></span>

<span data-ttu-id="4b18b-111">Dans cette section, vous allez configurer votre projet pour diffuser en streaming et en temps réel une expérience de réalité mixte de votre PC sur votre appareil HoloLens 2 au moyen d’une connexion Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="4b18b-111">In this section, you will configure your project to stream your Mixed Reality experience to your HoloLens 2 device from your PC in real-time over a Wi-Fi connection.</span></span>

<span data-ttu-id="4b18b-112">Dans la fenêtre Project, accédez au dossier **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs**, puis cliquez sur le préfabriqué **HolographicRemoting** et faites-le glisser dans votre scène.</span><span class="sxs-lookup"><span data-stu-id="4b18b-112">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs** folder, and click and drag **HolographicRemoting** prefab into your scene.</span></span>

![Unity avec le préfabriqué HolographicRemoting nouvellement ajouté toujours sélectionné](images/mrlearning-pc-holographic-remoting/Tutorial2-Section1-Step1-1.png)

## <a name="build-your-application-to-pc"></a><span data-ttu-id="4b18b-114">Générer votre application pour PC</span><span class="sxs-lookup"><span data-stu-id="4b18b-114">Build your application to PC</span></span>

<span data-ttu-id="4b18b-115">Vous pouvez à présent générer votre application de communication à distance holographique sur votre PC.</span><span class="sxs-lookup"><span data-stu-id="4b18b-115">Your Holographic Remoting app is now ready to build on your PC.</span></span> <span data-ttu-id="4b18b-116">Suivez les étapes ci-dessous et apportez ces modifications pour générer cette application sur votre PC.</span><span class="sxs-lookup"><span data-stu-id="4b18b-116">Follow the below steps and make these changes to build this application on to your PC.</span></span>

### <a name="1-set-the-player-settings"></a><span data-ttu-id="4b18b-117">1. Définir les paramètres du lecteur</span><span class="sxs-lookup"><span data-stu-id="4b18b-117">1. Set the player settings</span></span>

<span data-ttu-id="4b18b-118">Dans le menu Unity, sélectionnez Edit > Project Settings pour ouvrir la fenêtre Player Settings.</span><span class="sxs-lookup"><span data-stu-id="4b18b-118">In the Unity menu, select Edit > Project Settings to open the Player Settings window.</span></span>

<span data-ttu-id="4b18b-119">Dans la fenêtre Paramètres du projet, développez **Paramètres de publication**, faites défiler jusqu’à la section **Fonctionnalités** et cochez la case des fonctionnalités affichées ci-dessous en plus des fonctionnalités existantes.</span><span class="sxs-lookup"><span data-stu-id="4b18b-119">In the Project Settings window, expand the **Publishing Settings**, scroll down to the **Capabilities** section and select the below-shown capability checkbox in addition to the existing capabilities.</span></span>

* <span data-ttu-id="4b18b-120">Serveur client Internet</span><span class="sxs-lookup"><span data-stu-id="4b18b-120">Internet Clint server</span></span>
* <span data-ttu-id="4b18b-121">Serveur client de réseau privé</span><span class="sxs-lookup"><span data-stu-id="4b18b-121">Private Network Client Server</span></span>

<span data-ttu-id="4b18b-122">Dans la section **XR Settings**, cochez la case **WSA Holographic Remoting Supported** et activez la communication à distance holographique.</span><span class="sxs-lookup"><span data-stu-id="4b18b-122">In the **XR Settings** section, select the **WSA Holographic Remoting Supported** checkbox and enable the Holographic Remoting.</span></span>

![Fenêtre XR Settings d’Unity avec WSA Holographic Remoting Supported activé](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a><span data-ttu-id="4b18b-124">2. Générer le projet Unity</span><span class="sxs-lookup"><span data-stu-id="4b18b-124">2. Build the Unity Project</span></span>

<span data-ttu-id="4b18b-125">Dans le menu Unity, sélectionnez File > Build Settings pour ouvrir la fenêtre Build Settings.</span><span class="sxs-lookup"><span data-stu-id="4b18b-125">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="4b18b-126">Dans la fenêtre Build Settings, cliquez sur le bouton \**_Add Open Scenes_* _ pour ajouter votre scène actuelle aux scènes.</span><span class="sxs-lookup"><span data-stu-id="4b18b-126">In the Build Settings window, click the \**_Add Open Scenes_* _ button to add your current scene to the Scenes.</span></span> <span data-ttu-id="4b18b-127">Dans la liste Build, cliquez sur le _*_bouton Build_*_ pour ouvrir la fenêtre Build Universal Windows Platform :</span><span class="sxs-lookup"><span data-stu-id="4b18b-127">In the Build list, then click the _*_Build button_*_ to open the Build Universal Windows Platform window:</span></span>

![Fenêtre Build Settings d’Unity avec une scène ajoutée](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

<span data-ttu-id="4b18b-129">Dans la fenêtre Build Universal Windows Platform, choisissez un emplacement pour stocker votre build, par exemple Documents\MixedRealityLearning.</span><span class="sxs-lookup"><span data-stu-id="4b18b-129">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, Documents\MixedRealityLearning.</span></span> <span data-ttu-id="4b18b-130">Créez un dossier et donnez-lui un nom approprié, par exemple PCHolographicRemoting.</span><span class="sxs-lookup"><span data-stu-id="4b18b-130">Create a new folder and give it a suitable name, for example, PCHolographicRemoting.</span></span> <span data-ttu-id="4b18b-131">Cliquez ensuite sur le bouton _*_Select Folder_*_ pour démarrer le processus de génération :</span><span class="sxs-lookup"><span data-stu-id="4b18b-131">Then click the _*_Select Folder_*_ button to start the build process:</span></span>

![Fenêtre Build Settings d’Unity avec la fenêtre d’invite Select Folder](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

<span data-ttu-id="4b18b-133">Attendez qu’Unity termine le processus de génération.</span><span class="sxs-lookup"><span data-stu-id="4b18b-133">Wait for Unity to finish the build process.</span></span>

![Processus de génération Unity en cours](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a><span data-ttu-id="4b18b-135">3. Générer et déployer l’application</span><span class="sxs-lookup"><span data-stu-id="4b18b-135">3. Build and deploy the application</span></span>

<span data-ttu-id="4b18b-136">Une fois le processus de génération terminé, Unity invite l’Explorateur de fichiers Windows à ouvrir l’emplacement où vous avez stocké la build.</span><span class="sxs-lookup"><span data-stu-id="4b18b-136">When the build process is completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="4b18b-137">Naviguez dans le dossier, puis double-cliquez sur le fichier .sln pour l’ouvrir dans Visual Studio :</span><span class="sxs-lookup"><span data-stu-id="4b18b-137">Navigate inside the folder, and double-click the .sln file to open it in Visual Studio:</span></span>

![Explorateur Windows avec la solution Visual Studio nouvellement créée sélectionnée](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> <span data-ttu-id="4b18b-139">Si Visual Studio vous invite à installer de nouveaux composants, prenez un moment pour vérifier que tous les composants prérequis sont installés comme spécifié dans la documentation Installer les outils.</span><span class="sxs-lookup"><span data-stu-id="4b18b-139">If Visual Studio asks you to install new components, take a moment to ensure that all prerequisite components are installed as specified in the Install the Tools documentation.</span></span>

<span data-ttu-id="4b18b-140">Configurez Visual Studio pour PC en sélectionnant la configuration Release, l’architecture x64 et Ordinateur local comme cible :</span><span class="sxs-lookup"><span data-stu-id="4b18b-140">Configure Visual Studio for PC by selecting the Release configuration, the x64 architecture, and Local Machine as target:</span></span>

![Visual Studio configuré pour la machine locale](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

<span data-ttu-id="4b18b-142">Cliquez sur le bouton indiquant _*_Machine locale_*_.</span><span class="sxs-lookup"><span data-stu-id="4b18b-142">Click the button that says _*_Local Machine_*_.</span></span> <span data-ttu-id="4b18b-143">La procédure de génération et de déploiement de l’application sur votre PC démarre.</span><span class="sxs-lookup"><span data-stu-id="4b18b-143">It starts to build and deploy the application on to your PC.</span></span> <span data-ttu-id="4b18b-144">L’application est installée sur votre PC par défaut.</span><span class="sxs-lookup"><span data-stu-id="4b18b-144">The application will be installed in your PC by default.</span></span>

## <a name="testing-holographic-remoting-remote-application"></a><span data-ttu-id="4b18b-145">Test d’une application de communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="4b18b-145">Testing Holographic Remoting remote application</span></span>

<span data-ttu-id="4b18b-146">Pour connecter votre application PC à votre HoloLens 2, effectuez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="4b18b-146">To connect your PC application to your HoloLens 2, follow the below process:</span></span>

### <a name="1-install-the-remoting-player-application-on-hololens-2-device"></a><span data-ttu-id="4b18b-147">1. Installer l’application Remoting Player sur l’appareil HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="4b18b-147">1. Install the Remoting Player application on HoloLens 2 device</span></span>

<span data-ttu-id="4b18b-148">_ Sur votre HoloLens 2, accédez à l’application Store et recherchez « **Remoting Player** ».</span><span class="sxs-lookup"><span data-stu-id="4b18b-148">_ On your HoloLens 2, visit the Store app and search for "**Remoting Player**."</span></span>
* <span data-ttu-id="4b18b-149">Sélectionnez l’application **Remoting Player**.</span><span class="sxs-lookup"><span data-stu-id="4b18b-149">Select the **Remoting Player** app.</span></span>
* <span data-ttu-id="4b18b-150">Appuyez sur **Install** pour télécharger et installer l’application.</span><span class="sxs-lookup"><span data-stu-id="4b18b-150">Tap **Install** to download and install the app.</span></span>

### <a name="2-connect-the-holographic-remoting-pc-app-to-the-remoting-player"></a><span data-ttu-id="4b18b-151">2. Connecter l’application PC de communication à distance holographique à Remoting Player</span><span class="sxs-lookup"><span data-stu-id="4b18b-151">2. Connect the Holographic remoting PC app to the Remoting Player</span></span>

* <span data-ttu-id="4b18b-152">Démarrez **Remoting Player** sur votre HoloLens.</span><span class="sxs-lookup"><span data-stu-id="4b18b-152">Start the **Remoting Player** on your HoloLens.</span></span>
* <span data-ttu-id="4b18b-153">Notez l’**adresse IP** d’HoloLens.</span><span class="sxs-lookup"><span data-stu-id="4b18b-153">Take note of the HoloLens **IP address**.</span></span> <span data-ttu-id="4b18b-154">Celle-ci apparaît sous la forme d’un hologramme dès le lancement de **Remoting Player**.</span><span class="sxs-lookup"><span data-stu-id="4b18b-154">It will be displayed as a hologram by the **Remoting Player** as soon as it launches.</span></span>
* <span data-ttu-id="4b18b-155">Ouvrez l’application PC de communication à distance holographique sur votre PC.</span><span class="sxs-lookup"><span data-stu-id="4b18b-155">Open the Holographic Remoting PC application on your PC.</span></span>
* <span data-ttu-id="4b18b-156">Une fois l’application lancée, entrez l’**adresse IP** , puis cliquez sur le bouton **Connect** pour vous connecter.</span><span class="sxs-lookup"><span data-stu-id="4b18b-156">Once the application is launched, enter the **IP address** and click on the **Connect**  button to connect.</span></span>

## <a name="congratulations"></a><span data-ttu-id="4b18b-157">Félicitations</span><span class="sxs-lookup"><span data-stu-id="4b18b-157">Congratulations</span></span>

<span data-ttu-id="4b18b-158">Dans ce tutoriel, vous avez appris à créer une application PC de communication à distance holographique et à la connecter à HoloLens 2 à tout moment pour visualiser du contenu 3D en réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="4b18b-158">In this tutorial, you learned how to create a Holographic Remoting remote app and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span> <span data-ttu-id="4b18b-159">Une fois l’application PC de communication à distance holographique connectée à HoloLens, l’expérience de réalité mixte est diffusée en streaming sur votre appareil HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="4b18b-159">Once the HoloLens connected to the Holographic Remoting PC application, you should see the mixed reality experience streaming into your HoloLens 2 device.</span></span>
