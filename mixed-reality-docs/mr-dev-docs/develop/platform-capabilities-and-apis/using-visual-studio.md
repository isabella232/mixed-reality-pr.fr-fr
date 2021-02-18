---
title: Utilisation de Visual Studio pour le déploiement et le débogage
description: Découvrez comment créer, déboguer et déployer des applications pour HoloLens et Windows Mixed Reality avec Visual Studio.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/13/2020
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, Mixed Reality, déboguer, déployer
ms.openlocfilehash: 2ab89311163a48ee3c14511446a1498ce883a232
ms.sourcegitcommit: 029f247a6c33068360d3a06f2a473a12586017e1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100496090"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a><span data-ttu-id="c8cd5-104">Utilisation de Visual Studio pour le déploiement et le débogage</span><span class="sxs-lookup"><span data-stu-id="c8cd5-104">Using Visual Studio to deploy and debug</span></span>

<span data-ttu-id="c8cd5-105">Que vous utilisiez DirectX ou Unity pour développer votre application de réalité mixte, Visual Studio est votre outil de prédilection pour la déboguer et la déployer.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-105">Whether you're using DirectX or Unity to develop your mixed reality app, Visual Studio is your go-to tool for debugging and deployment.</span></span> <span data-ttu-id="c8cd5-106">Dans cette section, vous allez découvrir comment :</span><span class="sxs-lookup"><span data-stu-id="c8cd5-106">In this section, you will learn how to:</span></span>
* <span data-ttu-id="c8cd5-107">Déployer des applications sur votre HoloLens ou un casque immersif Windows Mixed Reality à l’aide de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-107">Deploy applications to your HoloLens or Windows Mixed Reality immersive headset through Visual Studio.</span></span>
* <span data-ttu-id="c8cd5-108">Utiliser l’émulateur HoloLens intégré à Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-108">Use the HoloLens emulator built in to Visual Studio.</span></span>
* <span data-ttu-id="c8cd5-109">Déboguer des applications de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-109">Debug mixed reality apps.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c8cd5-110">Prérequis</span><span class="sxs-lookup"><span data-stu-id="c8cd5-110">Prerequisites</span></span>

1. <span data-ttu-id="c8cd5-111">Consultez [Installer les outils](../../develop/install-the-tools.md#installation-checklist) pour obtenir des instructions d’installation.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-111">See [Install the Tools](../../develop/install-the-tools.md#installation-checklist) for installation instructions.</span></span>
2. <span data-ttu-id="c8cd5-112">Créez un projet d’application Windows universelle dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-112">Create a new Universal Windows app project in Visual Studio.</span></span>  <span data-ttu-id="c8cd5-113">Pour HoloLens (1re génération), utilisez Visual Studio 2017 ou une version plus récente.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-113">For HoloLens (1st gen), use Visual Studio 2017 or newer.</span></span>  <span data-ttu-id="c8cd5-114">Pour HoloLens 2, utilisez Visual Studio 2019 16.2 ou ultérieur.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-114">For HoloLens 2, use Visual Studio 2019 16.2 or newer.</span></span> <span data-ttu-id="c8cd5-115">Les langages C# et C++ sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-115">C# and C++ are supported.</span></span> <span data-ttu-id="c8cd5-116">(Ou suivez les instructions pour [créer une application dans Unity](../../develop/unity/tutorials/holograms-100.md).)</span><span class="sxs-lookup"><span data-stu-id="c8cd5-116">(Or follow the instructions to [create an app in Unity](../../develop/unity/tutorials/holograms-100.md).)</span></span>

## <a name="enabling-developer-mode"></a><span data-ttu-id="c8cd5-117">Activation du mode développeur</span><span class="sxs-lookup"><span data-stu-id="c8cd5-117">Enabling Developer Mode</span></span>

<span data-ttu-id="c8cd5-118">Commencez par activer le **mode développeur** sur votre appareil afin que Visual Studio puisse s’y connecter.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-118">Start by enabling **Developer Mode** on your device, so Visual Studio can connect to it.</span></span>

### <a name="hololens"></a><span data-ttu-id="c8cd5-119">HoloLens</span><span class="sxs-lookup"><span data-stu-id="c8cd5-119">HoloLens</span></span>

1. <span data-ttu-id="c8cd5-120">Mettez HoloLens sous tension et allumez l’appareil.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-120">Turn on your HoloLens and put on the device.</span></span>
2. <span data-ttu-id="c8cd5-121">Utilisez le [mouvement associé au menu Démarrer](../../design/system-gesture.md) pour lancer le menu principal.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-121">Use the [start gesture](../../design/system-gesture.md) to launch the main menu.</span></span>
3. <span data-ttu-id="c8cd5-122">Sélectionnez la vignette **Settings** pour lancer l’application dans votre environnement.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-122">Select the **Settings** tile to launch the app in your environment.</span></span>
4. <span data-ttu-id="c8cd5-123">Sélectionnez l’élément de menu **Mettre à jour**.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-123">Select the **Update** menu item.</span></span>
5. <span data-ttu-id="c8cd5-124">Sélectionnez l’élément de menu **Pour les développeurs**.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-124">Select the **For developers** menu item.</span></span>
6. <span data-ttu-id="c8cd5-125">Activez le **Mode développeur** pour déployer des applications à partir de Visual Studio sur votre HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-125">Enable **Developer Mode** to deploy apps from Visual Studio to your HoloLens.</span></span>
7. <span data-ttu-id="c8cd5-126">Facultatif : Faites défiler et activez également **Portail d’appareil**, ce qui vous permet de vous connecter au [Portail d’appareil Windows](using-the-windows-device-portal.md) sur votre HoloLens à partir d’un navigateur web.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-126">Optional: Scroll down and also enable **Device Portal**, which lets you connect to the [Windows Device Portal](using-the-windows-device-portal.md) on your HoloLens from a web browser.</span></span>

### <a name="windows-pc"></a><span data-ttu-id="c8cd5-127">PC Windows</span><span class="sxs-lookup"><span data-stu-id="c8cd5-127">Windows PC</span></span>

<span data-ttu-id="c8cd5-128">Si vous travaillez avec un casque Windows Mixed Reality connecté à votre PC, vous devez activer le **Mode développeur** sur ce PC.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-128">If you're working with a Windows Mixed Reality headset connected to your PC, you must enable **Developer Mode** on the PC.</span></span>
1. <span data-ttu-id="c8cd5-129">Accédez à **Paramètres**</span><span class="sxs-lookup"><span data-stu-id="c8cd5-129">Go to **Settings**</span></span>
2. <span data-ttu-id="c8cd5-130">Sélectionnez **Mise à jour et sécurité**</span><span class="sxs-lookup"><span data-stu-id="c8cd5-130">Select **Update and Security**</span></span>
3. <span data-ttu-id="c8cd5-131">Sélectionnez **Pour les développeurs**</span><span class="sxs-lookup"><span data-stu-id="c8cd5-131">Select **For developers**</span></span>
4. <span data-ttu-id="c8cd5-132">Activez le **Mode développeur**, lisez la clause d’exclusion de responsabilité pour le paramètre que vous avez choisi, puis sélectionnez Oui pour accepter la modification.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-132">Enable **Developer Mode**, read the disclaimer for the setting you chose, then select Yes to accept the change.</span></span>

## <a name="deploying-a-hololens-app-over-wi-fi"></a><span data-ttu-id="c8cd5-133">Déploiement d’une application HoloLens via une connexion Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="c8cd5-133">Deploying a HoloLens app over Wi-Fi</span></span> 

<span data-ttu-id="c8cd5-134">Configurez votre projet Visual Studio avec les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="c8cd5-134">Configure your Visual Studio project with the following properties:</span></span>

1. <span data-ttu-id="c8cd5-135">Sélectionner vos options de compilation d’applications</span><span class="sxs-lookup"><span data-stu-id="c8cd5-135">Select your apps compilation options</span></span>
    * <span data-ttu-id="c8cd5-136">Pour les projets Unity, choisissez **Release** ou **Master**</span><span class="sxs-lookup"><span data-stu-id="c8cd5-136">For Unity projects, choose either **Release** or **Master**</span></span> 
    * <span data-ttu-id="c8cd5-137">Pour tous les autres projets, choisissez **Release**</span><span class="sxs-lookup"><span data-stu-id="c8cd5-137">For all other projects, choose **Release**</span></span>

> [!NOTE]
> <span data-ttu-id="c8cd5-138">Vous trouverez les définitions complètes de chaque option de compilation dans [Exportation et génération de solutions Visual Studio](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span><span class="sxs-lookup"><span data-stu-id="c8cd5-138">You can find complete definitions for each compilation option in [exporting and building Visual Studio solutions](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span></span>

2. <span data-ttu-id="c8cd5-139">Sélectionner votre configuration de build en fonction de votre appareil</span><span class="sxs-lookup"><span data-stu-id="c8cd5-139">Select your build configuration based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="c8cd5-140">Sélectionnez **Machine distante** dans le menu déroulant de la cible de déploiement</span><span class="sxs-lookup"><span data-stu-id="c8cd5-140">Select **Remote Machine** in the deployment target drop-down menu</span></span>

![Cible de déploiement de machine distante dans Visual Studio](images/remotemachinesetting_arm64.png)

<span data-ttu-id="c8cd5-142">Ensuite, vous devez définir votre connexion à distance.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-142">Next, you need to set your remote connection.</span></span> <span data-ttu-id="c8cd5-143">Pour les projets C++ et JavaScript, accédez à **Projet > Propriétés > Propriétés de configuration > Débogage**.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-143">For C++ and JavaScript projects, go to **Project > Properties > Configuration Properties > Debugging**.</span></span> <span data-ttu-id="c8cd5-144">Si vous travaillez sur un projet C#, une boîte de dialogue doit s’afficher automatiquement.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-144">If you're working in a C# project, a dialog should automatically appear.</span></span>

> [!NOTE]
> <span data-ttu-id="c8cd5-145">Si la boîte de dialogue de connexion distante n’apparaît pas dans votre projet C#, vous pouvez l’ouvrir manuellement à partir de **Propriétés > Déboguer**.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-145">If the remote connection dialog doesn't appear in your C# project, you can open it manually from **Properties > Debug**.</span></span>

1. <span data-ttu-id="c8cd5-146">Entrez l’adresse IP de votre appareil dans le champ **Adresse** ou **Nom de la machine**.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-146">Enter the IP address of your device in the **Address** or **Machine Name** field.</span></span> 
    * <span data-ttu-id="c8cd5-147">Vous pouvez rechercher l’adresse IP sur votre HoloLens sous **Paramètres > Réseau et Internet > Options avancées**.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-147">You can find the IP address on your HoloLens under **Settings > Network & Internet > Advanced Options**</span></span>
    * <span data-ttu-id="c8cd5-148">Nous recommandons toujours d’entrer manuellement votre adresse IP plutôt que de dépendre de la fonctionnalité Détection automatique.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-148">We always recommend manually entering your IP address rather than depending on the Auto Detected feature</span></span>

2. <span data-ttu-id="c8cd5-149">Définissez le **Mode d’authentification** sur **Universel (protocole non chiffré)**</span><span class="sxs-lookup"><span data-stu-id="c8cd5-149">Set the **Authentication Mode** to **Universal (Unencrypted protocol)**</span></span>

  ![Boîte de dialogue Connexion à distance dans Visual Studio](images/remotedeploy.png)

3. <span data-ttu-id="c8cd5-151">Créer, déployer et déboguer votre application en fonction de vos besoins</span><span class="sxs-lookup"><span data-stu-id="c8cd5-151">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="c8cd5-152">Sélectionnez **Déboguer > Démarrer le débogage** pour déployer votre application et commencer le débogage</span><span class="sxs-lookup"><span data-stu-id="c8cd5-152">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="c8cd5-153">Sélectionnez **Générer > Déployer** pour générer et déployer sans déboguer</span><span class="sxs-lookup"><span data-stu-id="c8cd5-153">Select **Build > Deploy** to build and deploy without debugging</span></span>

![Démarrer sans débogage dans Visual Studio](images/deploywithdebugging.png)

4. <span data-ttu-id="c8cd5-155">La première fois que vous déployez une application sur votre HoloLens à partir de votre PC, vous êtes invité à entrer un code PIN.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-155">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="c8cd5-156">Suivez les instructions de la section **Appairer votre appareil**, plus loin dans cet article.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-156">Follow the **Pairing your device** instructions below.</span></span>

## <a name="deploying-a-hololens-app-over-usb"></a><span data-ttu-id="c8cd5-157">Déploiement d’une application HoloLens via une connexion USB</span><span class="sxs-lookup"><span data-stu-id="c8cd5-157">Deploying a HoloLens app over USB</span></span> 

<br>

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Deploying-your-HoloLens-2-application/player?format=ny]

1. <span data-ttu-id="c8cd5-158">Sélectionner vos options de compilation d’applications</span><span class="sxs-lookup"><span data-stu-id="c8cd5-158">Select your apps compilation options</span></span>
    * <span data-ttu-id="c8cd5-159">Pour les projets Unity, choisissez **Release** ou **Master**</span><span class="sxs-lookup"><span data-stu-id="c8cd5-159">For Unity projects, choose either **Release** or **Master**</span></span> 
    * <span data-ttu-id="c8cd5-160">Pour tous les autres projets, choisissez **Release**</span><span class="sxs-lookup"><span data-stu-id="c8cd5-160">For all other projects, choose **Release**</span></span>

> [!NOTE]
> <span data-ttu-id="c8cd5-161">Vous trouverez les définitions complètes de chaque option de compilation dans [Exportation et génération de solutions Visual Studio](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span><span class="sxs-lookup"><span data-stu-id="c8cd5-161">You can find complete definitions for each compilation option in [exporting and building Visual Studio solutions](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span></span>

2. <span data-ttu-id="c8cd5-162">Sélectionner votre configuration de build en fonction de votre appareil</span><span class="sxs-lookup"><span data-stu-id="c8cd5-162">Select your build configuration based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="c8cd5-163">Sélectionnez **Appareil** dans le menu déroulant de la cible de déploiement</span><span class="sxs-lookup"><span data-stu-id="c8cd5-163">Select **Device** in the deployment target drop-down menu</span></span>

![Déploiement d’appareils dans Visual Studio](images/buildsettingsusbdeploy_arm64.png)

4. <span data-ttu-id="c8cd5-165">Créer, déployer et déboguer votre application en fonction de vos besoins</span><span class="sxs-lookup"><span data-stu-id="c8cd5-165">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="c8cd5-166">Sélectionnez **Déboguer > Démarrer le débogage** pour déployer votre application et commencer le débogage</span><span class="sxs-lookup"><span data-stu-id="c8cd5-166">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="c8cd5-167">Sélectionnez **Générer > Déployer** pour générer et déployer sans déboguer</span><span class="sxs-lookup"><span data-stu-id="c8cd5-167">Select **Build > Deploy** to build and deploy without debugging</span></span>

![Démarrer sans débogage dans Visual Studio](images/deploywithdebugging.png)</br>

5. <span data-ttu-id="c8cd5-169">La première fois que vous déployez une application sur votre HoloLens à partir de votre PC, vous êtes invité à entrer un code PIN.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-169">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="c8cd5-170">Suivez les instructions de la section **Appairer votre appareil**, plus loin dans cet article.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-170">Follow the **Pairing your device** instructions below.</span></span>

> [!NOTE]
> <span data-ttu-id="c8cd5-171">Si vous constatez beaucoup de temps d’attente lors du déploiement de vos applications via une connexion USB, nous vous recommandons d’utiliser les [instructions sur la connexion à distance](#deploying-a-hololens-app-over-wi-fi) dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-171">If you're seeing considerable lag time with your apps deployment over USB, we recommend using the [remote machine instructions](#deploying-a-hololens-app-over-wi-fi) in the previous section.</span></span>

## <a name="deploying-an-app-to-the-hololens-emulator"></a><span data-ttu-id="c8cd5-172">Déploiement d’une application sur l’émulateur HoloLens</span><span class="sxs-lookup"><span data-stu-id="c8cd5-172">Deploying an app to the HoloLens Emulator</span></span>

1. <span data-ttu-id="c8cd5-173">Assurez-vous d’avoir **[installé l’émulateur HoloLens 2 ou HoloLens (1ère génération)](../install-the-tools.md#installation-checklist)**</span><span class="sxs-lookup"><span data-stu-id="c8cd5-173">Make sure you've **[installed either the HoloLens 2 or HoloLens (1st gen) Emulator](../install-the-tools.md#installation-checklist)**</span></span>
2. <span data-ttu-id="c8cd5-174">Sélectionner votre configuration de build et l’émulateur en fonction de votre appareil</span><span class="sxs-lookup"><span data-stu-id="c8cd5-174">Select your build configuration and emulator based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="c8cd5-175">Créer, déployer et déboguer votre application en fonction de vos besoins</span><span class="sxs-lookup"><span data-stu-id="c8cd5-175">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="c8cd5-176">Sélectionnez **Déboguer > Démarrer le débogage** pour déployer votre application et commencer le débogage</span><span class="sxs-lookup"><span data-stu-id="c8cd5-176">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="c8cd5-177">Sélectionnez **Générer > Déployer** pour générer et déployer sans déboguer</span><span class="sxs-lookup"><span data-stu-id="c8cd5-177">Select **Build > Deploy** to build and deploy without debuggingg</span></span>

![Démarrer sans débogage dans Visual Studio](images/deploywithdebugging.png)

## <a name="deploying-a-vr-app-to-your-local-pc"></a><span data-ttu-id="c8cd5-179">Déploiement d’une application VR sur votre PC local</span><span class="sxs-lookup"><span data-stu-id="c8cd5-179">Deploying a VR app to your Local PC</span></span> 

<span data-ttu-id="c8cd5-180">Pour utiliser un casque immersif Windows Mixed Reality qui se connecte à votre PC ou au [simulateur Mixed Reality](using-the-windows-mixed-reality-simulator.md) :</span><span class="sxs-lookup"><span data-stu-id="c8cd5-180">To use a Windows Mixed Reality immersive headset that connects to your PC or the [Mixed Reality simulator](using-the-windows-mixed-reality-simulator.md):</span></span>
1. <span data-ttu-id="c8cd5-181">Sélectionnez une configuration de build **x86** ou **x64** pour votre application</span><span class="sxs-lookup"><span data-stu-id="c8cd5-181">Select an **x86** or **x64** build configuration for your app</span></span>
2. <span data-ttu-id="c8cd5-182">Sélectionnez **Machine locale** dans le menu déroulant de la cible de déploiement</span><span class="sxs-lookup"><span data-stu-id="c8cd5-182">Select **Local Machine** in the deployment target drop-down menu</span></span>
3. <span data-ttu-id="c8cd5-183">Créer, déployer et déboguer votre application en fonction de vos besoins</span><span class="sxs-lookup"><span data-stu-id="c8cd5-183">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="c8cd5-184">Sélectionnez **Déboguer > Démarrer le débogage** pour déployer votre application et commencer le débogage</span><span class="sxs-lookup"><span data-stu-id="c8cd5-184">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="c8cd5-185">Sélectionnez **Générer > Déployer** pour générer et déployer sans déboguer</span><span class="sxs-lookup"><span data-stu-id="c8cd5-185">Select **Build > Deploy** to build and deploy without debugging</span></span>

## <a name="pairing-your-device"></a><span data-ttu-id="c8cd5-186">Appairage de votre appareil</span><span class="sxs-lookup"><span data-stu-id="c8cd5-186">Pairing your device</span></span>

<span data-ttu-id="c8cd5-187">La première fois que vous déployez une application sur votre HoloLens à partir de Visual Studio, vous êtes invité à entrer un code PIN.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-187">The first time you deploy an app from Visual Studio to your HoloLens, you'll be prompted for a PIN.</span></span> <span data-ttu-id="c8cd5-188">Sur votre HoloLens, générez un code PIN. Pour cela, lancez l’application Paramètres, accédez à **Mise à jour > Pour les développeurs**, puis appuyez sur **Coupler**.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-188">On the HoloLens, generate a PIN by launching the Settings app, go to **Update > For Developers**, and tap on **Pair**.</span></span> <span data-ttu-id="c8cd5-189">Tapez le code PIN qui apparaît sur votre HoloLens dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-189">When the PIN is displayed on your HoloLens, type it into Visual Studio.</span></span> <span data-ttu-id="c8cd5-190">Une fois l’appairage terminé, appuyez sur **Terminé** sur votre HoloLens pour fermer la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-190">After pairing is complete, tap **Done** on your HoloLens to dismiss the dialog.</span></span> <span data-ttu-id="c8cd5-191">Ce PC étant maintenant appairé avec votre HoloLens, vous pouvez y déployer des applications automatiquement.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-191">This PC is now paired with the HoloLens and you can deploy apps automatically.</span></span> <span data-ttu-id="c8cd5-192">Répétez ces étapes pour chaque PC utilisé pour déployer des applications sur votre HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-192">Repeat these steps for every PC that's used to deploy apps to your HoloLens.</span></span>

<span data-ttu-id="c8cd5-193">Pour découpler votre HoloLens de tous les ordinateurs appairés :</span><span class="sxs-lookup"><span data-stu-id="c8cd5-193">To unpair your HoloLens from all paired computers:</span></span>
* <span data-ttu-id="c8cd5-194">Lancez l’application **Paramètres**, accédez à **Mise à jour > Pour les développeurs**, puis appuyez sur **Effacer**.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-194">Launch the **Settings** app, go to **Update > For Developers**, and tap on **Clear**.</span></span>

## <a name="graphics-debugger-for-hololens-1st-gen"></a><span data-ttu-id="c8cd5-195">Débogueur Graphics pour HoloLens (1re génération)</span><span class="sxs-lookup"><span data-stu-id="c8cd5-195">Graphics Debugger for HoloLens (1st gen)</span></span>

<span data-ttu-id="c8cd5-196">Les outils Graphics Diagnostics de Visual Studio sont utiles quand vous écrivez et optimisez une application holographique.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-196">The Visual Studio Graphics Diagnostics tools are helpful when writing and optimizing a Holographic app.</span></span> <span data-ttu-id="c8cd5-197">Pour plus d’informations, consultez [Visual Studio Graphics Diagnostics sur MSDN](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics).</span><span class="sxs-lookup"><span data-stu-id="c8cd5-197">See [Visual Studio Graphics Diagnostics on MSDN](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics) for full details.</span></span>

<span data-ttu-id="c8cd5-198">**Pour démarrer le débogueur Graphics**</span><span class="sxs-lookup"><span data-stu-id="c8cd5-198">**To Start the Graphics Debugger**</span></span>
1. <span data-ttu-id="c8cd5-199">Suivez les instructions données plus haut pour cibler un appareil ou un émulateur</span><span class="sxs-lookup"><span data-stu-id="c8cd5-199">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="c8cd5-200">Accédez à **Déboguer > Graphics > Démarrer les diagnostics**</span><span class="sxs-lookup"><span data-stu-id="c8cd5-200">Go to **Debug > Graphics > Start Diagnostics**</span></span>
3. <span data-ttu-id="c8cd5-201">La première fois que vous démarrez les diagnostics avec un HoloLens, vous pouvez obtenir une erreur « Accès refusé ».</span><span class="sxs-lookup"><span data-stu-id="c8cd5-201">The first time you start diagnostics with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="c8cd5-202">Redémarrez votre HoloLens pour que les autorisations mises à jour prennent effet, puis réessayez.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-202">Reboot your HoloLens to let the updated permissions take effect and try again.</span></span>

## <a name="profiling"></a><span data-ttu-id="c8cd5-203">Profilage</span><span class="sxs-lookup"><span data-stu-id="c8cd5-203">Profiling</span></span>

<span data-ttu-id="c8cd5-204">Les outils de profilage dans Visual Studio vous permettent d’analyser l’utilisation des ressources et les performances de votre application.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-204">The Visual Studio profiling tools allow you to analyze your app's performance and resource use.</span></span> <span data-ttu-id="c8cd5-205">Ces outils comprennent des outils pour optimiser l’utilisation du processeur, de la mémoire, des graphiques et du réseau.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-205">This includes tools to optimize CPU, memory, graphics, and network use.</span></span> <span data-ttu-id="c8cd5-206">Pour plus d’informations, consultez [Exécuter les outils de diagnostic sans débogage sur MSDN](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools).</span><span class="sxs-lookup"><span data-stu-id="c8cd5-206">See [Run diagnostic tools without debugging on MSDN](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools) for full details.</span></span>

<span data-ttu-id="c8cd5-207">**Pour démarrer les outils de profilage avec HoloLens**</span><span class="sxs-lookup"><span data-stu-id="c8cd5-207">**To Start the Profiling Tools with HoloLens**</span></span>
1. <span data-ttu-id="c8cd5-208">Suivez les instructions données plus haut pour cibler un appareil ou un émulateur</span><span class="sxs-lookup"><span data-stu-id="c8cd5-208">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="c8cd5-209">Accédez à **Déboguer > Démarrer les outils de diagnostic sans débogage...**</span><span class="sxs-lookup"><span data-stu-id="c8cd5-209">Go to **Debug > Start Diagnostic Tools Without Debugging...**</span></span>
3. <span data-ttu-id="c8cd5-210">Sélectionnez les outils que vous souhaitez utiliser</span><span class="sxs-lookup"><span data-stu-id="c8cd5-210">Select the tools you want to use</span></span>
4. <span data-ttu-id="c8cd5-211">Sélectionnez **Démarrer**</span><span class="sxs-lookup"><span data-stu-id="c8cd5-211">Select **Start**</span></span>
5. <span data-ttu-id="c8cd5-212">La première fois que vous démarrez les diagnostics sans débogage avec un HoloLens, vous pouvez obtenir une erreur « Accès refusé ».</span><span class="sxs-lookup"><span data-stu-id="c8cd5-212">The first time you start diagnostics without debugging with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="c8cd5-213">Redémarrez votre HoloLens pour que les autorisations mises à jour prennent effet, puis réessayez.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-213">Reboot your HoloLens to let the updated permissions take effect and try again.</span></span>

## <a name="debugging-an-installed-or-running-app"></a><span data-ttu-id="c8cd5-214">Débogage d’une application installée ou en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="c8cd5-214">Debugging an installed or running app</span></span>

<span data-ttu-id="c8cd5-215">Vous pouvez utiliser Visual Studio pour déboguer une application Windows universelle installée sans déploiement à partir d’un projet Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-215">You can use Visual Studio to debug an installed Universal Windows app without deploying from a Visual Studio project.</span></span> <span data-ttu-id="c8cd5-216">Cela est utile si vous souhaitez déboguer un package d’application installé ou une application en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-216">This is useful if you want to debug an installed app package or debug an app that's already running.</span></span>
1. <span data-ttu-id="c8cd5-217">Accédez à **Déboguer -> Autres cibles de débogage -> Déboguer le package d’application installé**</span><span class="sxs-lookup"><span data-stu-id="c8cd5-217">Go to **Debug -> Other Debug Targets -> Debug Installed App Package**</span></span>
2. <span data-ttu-id="c8cd5-218">Sélectionnez la cible **Machine distante** pour HoloLens ou **Machine locale** pour les casques immersifs</span><span class="sxs-lookup"><span data-stu-id="c8cd5-218">Select the **Remote Machine** target for HoloLens or **Local Machine** for immersive headsets.</span></span>
3. <span data-ttu-id="c8cd5-219">Entrez l’**adresse IP** de votre appareil</span><span class="sxs-lookup"><span data-stu-id="c8cd5-219">Enter your device’s **IP address**</span></span>
4. <span data-ttu-id="c8cd5-220">Choisissez le mode d’authentification **Universel**</span><span class="sxs-lookup"><span data-stu-id="c8cd5-220">Choose the **Universal** Authentication Mode</span></span>
5. <span data-ttu-id="c8cd5-221">La fenêtre affiche les applications en cours d’exécution et les applications inactives.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-221">The window shows both running and inactive apps.</span></span> <span data-ttu-id="c8cd5-222">Sélectionnez celle que vous voulez déboguer.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-222">Pick the one what you’d like to debug.</span></span>
6. <span data-ttu-id="c8cd5-223">Choisissez le type de code à déboguer (managé, natif, mixte)</span><span class="sxs-lookup"><span data-stu-id="c8cd5-223">Choose the type of code to debug (Managed, Native, Mixed)</span></span>
7. <span data-ttu-id="c8cd5-224">Sélectionnez **Attacher** ou **Démarrer**</span><span class="sxs-lookup"><span data-stu-id="c8cd5-224">Select **Attach** or **Start**</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="c8cd5-225">Point de contrôle de développement suivant</span><span class="sxs-lookup"><span data-stu-id="c8cd5-225">Next Development Checkpoint</span></span>

<span data-ttu-id="c8cd5-226">Si vous suivez le parcours de points de contrôle de développement Unreal que nous avons élaboré, vous êtes actuellement au cœur de la phase de déploiement.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-226">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="c8cd5-227">À partir d’ici, vous pouvez passer au sujet suivant :</span><span class="sxs-lookup"><span data-stu-id="c8cd5-227">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c8cd5-228">Déploiement sur l’émulateur HoloLens</span><span class="sxs-lookup"><span data-stu-id="c8cd5-228">Deploying to HoloLens emulator</span></span>](using-the-hololens-emulator.md)

<span data-ttu-id="c8cd5-229">Ou accéder directement à l’ajout de services avancés :</span><span class="sxs-lookup"><span data-stu-id="c8cd5-229">Or jump directly to adding advanced services:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c8cd5-230">Services avancés</span><span class="sxs-lookup"><span data-stu-id="c8cd5-230">Advanced services</span></span>](../../develop/unity/unity-development-overview.md#5-adding-services)

<span data-ttu-id="c8cd5-231">Vous pouvez revenir aux [points de contrôle de développement Unity](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="c8cd5-231">You can always go back to the [Unity development checkpoints](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="c8cd5-232">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c8cd5-232">See also</span></span>
* [<span data-ttu-id="c8cd5-233">Installer les outils</span><span class="sxs-lookup"><span data-stu-id="c8cd5-233">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="c8cd5-234">Utilisation de l’émulateur HoloLens</span><span class="sxs-lookup"><span data-stu-id="c8cd5-234">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="c8cd5-235">Déploiement et débogage d’applications de plateforme Windows universelle (UWP)</span><span class="sxs-lookup"><span data-stu-id="c8cd5-235">Deploying and debugging Universal Windows Platform (UWP) apps</span></span>](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps)
* [<span data-ttu-id="c8cd5-236">Activer votre appareil pour le développement</span><span class="sxs-lookup"><span data-stu-id="c8cd5-236">Enable your device for development</span></span>](/windows/uwp/get-started/enable-your-device-for-development)