---
title: Créer une application PC de communication à distance holographique
description: Suivez ce cours pour découvrir comment créer une application pour PC afin d’effectuer à distance une expérience de réalité mixte depuis votre PC vers HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: réalité mixte, unity, tutoriel, hololens, communication à distance holographique sur PC, Visual Studio
ms.localizationpriority: high
ms.openlocfilehash: ca0efe13acac4408a05ab89eb98b508e9993c5a4
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392496"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a><span data-ttu-id="9504e-104">2. Création d’une application PC de communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="9504e-104">2. Creating a Holographic Remoting PC application</span></span>

<span data-ttu-id="9504e-105">Dans ce tutoriel, vous allez apprendre à créer une application PC de communication à distance holographique et à la connecter à HoloLens 2 à tout moment pour visualiser du contenu 3D en réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="9504e-105">In this tutorial, you will learn how to create a PC app for Holographic Remoting and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span>

## <a name="objectives"></a><span data-ttu-id="9504e-106">Objectifs</span><span class="sxs-lookup"><span data-stu-id="9504e-106">Objectives</span></span>

* <span data-ttu-id="9504e-107">Configurer Unity pour la communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="9504e-107">Configure Unity for Holographic Remoting</span></span>
* <span data-ttu-id="9504e-108">Apprendre à créer et déployer l’application avec Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9504e-108">Learn how to build and deploy the application with Visual Studio</span></span>
* <span data-ttu-id="9504e-109">Développer une application de communication à distance holographique et la connecter à HoloLens</span><span class="sxs-lookup"><span data-stu-id="9504e-109">Developing Holographic Remoting application and connecting to HoloLens</span></span>

## <a name="configuring-the-capabilities"></a><span data-ttu-id="9504e-110">Configuration des fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="9504e-110">Configuring the capabilities</span></span>

<span data-ttu-id="9504e-111">Dans la fenêtre **Paramètres du projet**, développez les **Paramètres de publication**, faites défiler jusqu’à la section Fonctionnalités et cochez la case des fonctionnalités affichées ci-dessous en plus des fonctionnalités existantes.</span><span class="sxs-lookup"><span data-stu-id="9504e-111">In the **Project Settings** window, expand the **Publishing Settings**, scroll down to the Capabilities section and select the below-shown capability checkbox in addition to the existing capabilities.</span></span>

* <span data-ttu-id="9504e-112">Serveur client Internet</span><span class="sxs-lookup"><span data-stu-id="9504e-112">Internet Clint server</span></span>
* <span data-ttu-id="9504e-113">Serveur client de réseau privé</span><span class="sxs-lookup"><span data-stu-id="9504e-113">Private Network Client Server</span></span>

![activation des fonctionnalités](images/mrlearning-pc-holographic-remoting/tutorial2-section0-step1-1.png)

[!INCLUDE[](includes/configuring-scene-for-holographic-remoting.md)]

## <a name="build-your-application-to-pc"></a><span data-ttu-id="9504e-115">Générer votre application pour PC</span><span class="sxs-lookup"><span data-stu-id="9504e-115">Build your application to PC</span></span>

<span data-ttu-id="9504e-116">Vous pouvez à présent générer votre application de communication à distance holographique sur votre PC.</span><span class="sxs-lookup"><span data-stu-id="9504e-116">Your Holographic Remoting app is now ready to build on your PC.</span></span> <span data-ttu-id="9504e-117">Suivez les étapes ci-dessous et apportez ces modifications pour générer cette application sur votre PC.</span><span class="sxs-lookup"><span data-stu-id="9504e-117">Follow the below steps and make these changes to build this application on to your PC.</span></span>

[!INCLUDE[](includes/build-your-application-to-pc.md)]

## <a name="testing-holographic-remoting-remote-application"></a><span data-ttu-id="9504e-118">Test d’une application de communication à distance holographique</span><span class="sxs-lookup"><span data-stu-id="9504e-118">Testing Holographic Remoting remote application</span></span>

<span data-ttu-id="9504e-119">Pour connecter votre application PC à votre HoloLens 2, effectuez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="9504e-119">To connect your PC application to your HoloLens 2, follow the below process:</span></span>

### <a name="1-install-the-remoting-player-application-on-hololens-2-device"></a><span data-ttu-id="9504e-120">1. Installer l’application Remoting Player sur l’appareil HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="9504e-120">1. Install the Remoting Player application on HoloLens 2 device</span></span>

* <span data-ttu-id="9504e-121">Sur votre HoloLens 2, accédez à l’application Store et recherchez « **Remoting Player** ».</span><span class="sxs-lookup"><span data-stu-id="9504e-121">On your HoloLens 2, visit the Store app and search for "**Remoting Player**."</span></span>
* <span data-ttu-id="9504e-122">Sélectionnez l’application **Remoting Player**.</span><span class="sxs-lookup"><span data-stu-id="9504e-122">Select the **Remoting Player** app.</span></span>
* <span data-ttu-id="9504e-123">Appuyez sur **Install** pour télécharger et installer l’application.</span><span class="sxs-lookup"><span data-stu-id="9504e-123">Tap **Install** to download and install the app.</span></span>

### <a name="2-connect-the-holographic-remoting-pc-app-to-the-remoting-player"></a><span data-ttu-id="9504e-124">2. Connecter l’application PC de communication à distance holographique à Remoting Player</span><span class="sxs-lookup"><span data-stu-id="9504e-124">2. Connect the Holographic remoting PC app to the Remoting Player</span></span>

* <span data-ttu-id="9504e-125">Démarrez **Remoting Player** sur votre HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9504e-125">Start the **Remoting Player** on your HoloLens.</span></span>
* <span data-ttu-id="9504e-126">Notez l’**adresse IP** d’HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9504e-126">Take note of the HoloLens **IP address**.</span></span> <span data-ttu-id="9504e-127">Celle-ci apparaît sous la forme d’un hologramme dès le lancement de **Remoting Player**.</span><span class="sxs-lookup"><span data-stu-id="9504e-127">It will be displayed as a hologram by the **Remoting Player** as soon as it launches.</span></span>
* <span data-ttu-id="9504e-128">Ouvrez l’application PC de communication à distance holographique sur votre PC.</span><span class="sxs-lookup"><span data-stu-id="9504e-128">Open the Holographic Remoting PC application on your PC.</span></span>
* <span data-ttu-id="9504e-129">Une fois l’application lancée, entrez l’**adresse IP** , puis cliquez sur le bouton **Connect** pour vous connecter.</span><span class="sxs-lookup"><span data-stu-id="9504e-129">Once the application is launched, enter the **IP address** and click on the **Connect**  button to connect.</span></span>

## <a name="congratulations"></a><span data-ttu-id="9504e-130">Félicitations</span><span class="sxs-lookup"><span data-stu-id="9504e-130">Congratulations</span></span>

<span data-ttu-id="9504e-131">Dans ce tutoriel, vous avez appris à créer une application PC de communication à distance holographique et à la connecter à HoloLens 2 à tout moment pour visualiser du contenu 3D en réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="9504e-131">In this tutorial, you learned how to create a Holographic Remoting remote app and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span> <span data-ttu-id="9504e-132">Une fois l’application PC de communication à distance holographique connectée à HoloLens, l’expérience de réalité mixte est diffusée en streaming sur votre appareil HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9504e-132">Once the HoloLens connected to the Holographic Remoting PC application, you should see the mixed reality experience streaming into your HoloLens 2 device.</span></span>
