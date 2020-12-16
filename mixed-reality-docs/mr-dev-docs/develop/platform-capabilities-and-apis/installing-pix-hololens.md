---
title: Installation de PIX pour HoloLens 2
description: Découvrez comment installer PIX pour les appareils HoloLens 2.
author: hferrone
ms.author: flbagar
ms.date: 12/02/2020
ms.topic: article
keywords: HoloLens, HoloLens 2, PIX, capture, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle
ms.openlocfilehash: 5dfc16f97790b47af3c24ca44c060a9a2495a320
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530451"
---
# <a name="installing-pix-for-hololens-2"></a><span data-ttu-id="f4dd1-104">Installation de PIX pour HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="f4dd1-104">Installing PIX for HoloLens 2</span></span>

<span data-ttu-id="f4dd1-105">[Pix](https://devblogs.microsoft.com/pix) est un outil de réglage et de débogage des performances pour les applications DirectX 12 sur Windows.</span><span class="sxs-lookup"><span data-stu-id="f4dd1-105">[PIX](https://devblogs.microsoft.com/pix) is a performance tuning and debugging tool for DirectX 12 applications on Windows.</span></span> 

## <a name="setup"></a><span data-ttu-id="f4dd1-106">Installation</span><span class="sxs-lookup"><span data-stu-id="f4dd1-106">Setup</span></span>

1. <span data-ttu-id="f4dd1-107">Prenez la version la plus récente de la [version]( https://devblogs.microsoft.com/pix/download) pix de votre ordinateur hôte et connectez votre HoloLens 2 à votre PC via un câble USB.</span><span class="sxs-lookup"><span data-stu-id="f4dd1-107">Grab the latest PIX [release]( https://devblogs.microsoft.com/pix/download) from your host PC and connect your HoloLens 2 to your PC via a USB cable.</span></span>

2. <span data-ttu-id="f4dd1-108">Si votre HoloLens 2 est sur une [version de Windows Insider](https://insider.windows.com) ou si elle a une configuration qui interrompt pix,  [reflashez votre appareil](https://docs.microsoft.com/hololens/hololens-recovery) pour effacer toutes les données.</span><span class="sxs-lookup"><span data-stu-id="f4dd1-108">If your HoloLens 2 is on a [Windows Insider build](https://insider.windows.com) or has a configuration that breaks PIX,  [reflash your device](https://docs.microsoft.com/hololens/hololens-recovery) to erase all data.</span></span>

3. <span data-ttu-id="f4dd1-109">Activer le **mode développeur** et le **portail des appareils**:</span><span class="sxs-lookup"><span data-stu-id="f4dd1-109">Enable **Developer Mode** and **Device Portal**:</span></span>

* <span data-ttu-id="f4dd1-110">Ouvrir les **paramètres** à partir de l’interpréteur de commandes :</span><span class="sxs-lookup"><span data-stu-id="f4dd1-110">Open **Settings** from Shell:</span></span>

![Capture d’écran du menu HoloLens avec le bouton paramètres mis en surbrillance](images/pix-img-01.jpg)

* <span data-ttu-id="f4dd1-112">Sélectionnez **mettre à jour la sécurité &**:</span><span class="sxs-lookup"><span data-stu-id="f4dd1-112">Select **Update & Security**:</span></span>

![Capture d’écran de la fenêtre Paramètres ouverte sur HoloLens avec le bouton mettre à jour et sécurité mis en surbrillance](images/pix-img-02.jpg)

* <span data-ttu-id="f4dd1-114">Sélectionnez **pour les développeurs**:</span><span class="sxs-lookup"><span data-stu-id="f4dd1-114">Select **For Developers**:</span></span>

![Capture d’écran de la fenêtre sécurité et mises à jour ouverte avec le bouton pour les développeurs mis en surbrillance](images/pix-img-03.jpg)

* <span data-ttu-id="f4dd1-116">Activer l' **utilisation des fonctionnalités de développement** et **activer le portail des appareils**</span><span class="sxs-lookup"><span data-stu-id="f4dd1-116">Turn on **Use Developer Features** and **Enable Device Portal**</span></span>

![Capture d’écran de la fenêtre pour les développeurs ouverte dans paramètres avec le bouton Activer le portail pour appareils mis en surbrillance](images/pix-img-04.jpg)

![Capture d’écran de la fenêtre pour les développeurs ouverte dans les paramètres avec l’activation de l’utilisation du développement des fonctionnalités en surbrillance](images/pix-img-05.jpg)

* <span data-ttu-id="f4dd1-119">Lorsque l’appareil est toujours connecté, en éveil et avec l’utilisateur connecté, lancez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f4dd1-119">With the device still connected, awake, and with the user logged in, launch Visual Studio.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f4dd1-120">Assurez-vous que votre appareil n’est pas en mode veille ou en veille.</span><span class="sxs-lookup"><span data-stu-id="f4dd1-120">Make sure your device isn't in standby mode or asleep.</span></span> <span data-ttu-id="f4dd1-121">Si vous rencontrez des problèmes avec cette étape, reportez-vous aux [instructions du portail d’appareils Windows](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal).</span><span class="sxs-lookup"><span data-stu-id="f4dd1-121">If you're having trouble with this step, refer to the [Windows Device Portal instructions](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal).</span></span>

## <a name="preparing-for-deployment"></a><span data-ttu-id="f4dd1-122">Préparation du déploiement</span><span class="sxs-lookup"><span data-stu-id="f4dd1-122">Preparing for deployment</span></span>

1. <span data-ttu-id="f4dd1-123">Dans Visual Studio, définissez **ARM64** en tant que plateforme et **appareil** comme périphérique :</span><span class="sxs-lookup"><span data-stu-id="f4dd1-123">In Visual Studio, set **ARM64** as the platform and **Device** as the device:</span></span>

![Capture d’écran de la solution Visual Studio avec les paramètres de plateforme et d’appareil mis en surbrillance](images/pix-img-06.png)

2. <span data-ttu-id="f4dd1-125">Lorsque Visual Studio vous invite à entrer un **code confidentiel** sur l’appareil :</span><span class="sxs-lookup"><span data-stu-id="f4dd1-125">When Visual Studio prompts you for a **PIN** from the device:</span></span>

![Capture d’écran de la fenêtre contextuelle de Visual Studio demandant le code confidentiel](images/pix-img-07.png)

* <span data-ttu-id="f4dd1-127">Sélectionner des **paramètres** à partir de l’interpréteur de commandes</span><span class="sxs-lookup"><span data-stu-id="f4dd1-127">Select **Settings** from Shell</span></span>
* <span data-ttu-id="f4dd1-128">Sélectionner **mettre à jour la sécurité &**</span><span class="sxs-lookup"><span data-stu-id="f4dd1-128">Select **Update & Security**</span></span>
* <span data-ttu-id="f4dd1-129">Sélectionnez **pour les développeurs** et appuyez sur paire sous **découverte d’appareil**</span><span class="sxs-lookup"><span data-stu-id="f4dd1-129">Select **For Developers** and press Pair under **Device Discovery**</span></span> 

![Capture d’écran de la fenêtre pour les développeurs ouverte dans paramètres avec la découverte de périphérique mise en surbrillance](images/pix-img-08.jpg)

![Capture d’écran de la fenêtre contextuelle de l’appareil payant avec le code d’inscription mis en surbrillance](images/pix-img-09.jpg)

* <span data-ttu-id="f4dd1-132">Entrer le numéro de code confidentiel généré dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f4dd1-132">Enter the generated PIN number in Visual Studio</span></span>

3. <span data-ttu-id="f4dd1-133">Visual Studio déploie l’application sur le HoloLens 2 connecté, ce qui peut prendre quelques minutes en fonction de l’application.</span><span class="sxs-lookup"><span data-stu-id="f4dd1-133">Visual Studio will deploy the app to the connected HoloLens 2, which may take a few minutes depending on the app.</span></span>

## <a name="launching-pix"></a><span data-ttu-id="f4dd1-134">Lancement de PIX</span><span class="sxs-lookup"><span data-stu-id="f4dd1-134">Launching PIX</span></span>

<span data-ttu-id="f4dd1-135">Tout d’abord, utilisez le portail de l’appareil pour vérifier que l’application n’est pas en cours d’exécution sur HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f4dd1-135">First, use Device Portal to verify the app isn't running on the HoloLens 2.</span></span> <span data-ttu-id="f4dd1-136">Ensuite, lancez PIX, connectez-vous à votre appareil, puis sélectionnez **page d’hébergement**:</span><span class="sxs-lookup"><span data-stu-id="f4dd1-136">Then, launch PIX, connect to your device, and select **Home**:</span></span>

![Capture d’écran de l’écran d’accueil de l’application PIX](images/pix-img-10.png)

* <span data-ttu-id="f4dd1-138">Sélectionnez **se connecter** dans le menu de gauche :</span><span class="sxs-lookup"><span data-stu-id="f4dd1-138">Select **Connect** from the left-side menu:</span></span>

![Capture d’écran du menu de gauche de l’application PIX avec le bouton de connexion mis en surbrillance](images/pix-img-11.png)

2. <span data-ttu-id="f4dd1-140">Dans l’onglet **ordinateur** , sélectionnez **Ajouter**, puis entrez les informations d’identification suivantes :</span><span class="sxs-lookup"><span data-stu-id="f4dd1-140">From the **Computer** tab, select **Add**, and enter the following credentials:</span></span>
    * <span data-ttu-id="f4dd1-141">Alias : jusqu’à la discrétion de l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="f4dd1-141">Alias: Up to user’s discretion</span></span>
    * <span data-ttu-id="f4dd1-142">Nom d’hôte ou adresse IP : 127.0.0.1</span><span class="sxs-lookup"><span data-stu-id="f4dd1-142">Host Name or IP Address: 127.0.0.1</span></span>

3. <span data-ttu-id="f4dd1-143">Sélectionnez **se connecter** dans le coin inférieur droit de l’onglet **ordinateur** :</span><span class="sxs-lookup"><span data-stu-id="f4dd1-143">Select **Connect** in the lower right of the **Computer** tab:</span></span>

![Capture d’écran de la fenêtre de connexion d’application PIX avec l’alias, le nom d’hôte, l’adresse IP et le bouton Ajouter mis en surbrillance](images/pix-img-12.png)

> [!NOTE]
> <span data-ttu-id="f4dd1-145">La première connexion est toujours plus lente en raison de la copie des fichiers binaires.</span><span class="sxs-lookup"><span data-stu-id="f4dd1-145">The first connection is always slower because binaries are being copied.</span></span>

4. <span data-ttu-id="f4dd1-146">Quand PIX s’est connecté à HoloLens 2, recherchez votre application dans la section **Sélectionner le processus cible** de l’onglet lancer UWP, puis sélectionnez **lancer**:</span><span class="sxs-lookup"><span data-stu-id="f4dd1-146">When PIX has connected to the HoloLens 2, find your app in the **Select Target Process** section in the Launch UWP tab, and select **Launch**:</span></span>

![Capture d’écran de l’application PIX avec la fenêtre Sélectionner le processus cible et le bouton de lancement mis en surbrillance](images/pix-img-13.png)

## <a name="gpu-captured"></a><span data-ttu-id="f4dd1-148">GPU capturé</span><span class="sxs-lookup"><span data-stu-id="f4dd1-148">GPU captured</span></span>

1. <span data-ttu-id="f4dd1-149">Démarrez la capture GPU en cliquant sur **photo** dans la section **capture GPU** :</span><span class="sxs-lookup"><span data-stu-id="f4dd1-149">Start the GPU capture by clicking **Photo** in the **GPU Capture** section:</span></span>

![Capture d’écran de l’application PIX avec le panneau de connexion du PC ouvert avec la capture GPU mise en surbrillance](images/pix-img-14.png)

2. <span data-ttu-id="f4dd1-151">Ouvrez la capture pour l’analyse en cliquant sur la capture d’écran générée dans le panneau **capture GPU** :</span><span class="sxs-lookup"><span data-stu-id="f4dd1-151">Open the capture for analysis by clicking on the generated screenshot in the **GPU Capture** panel:</span></span>

![Capture d’écran de l’application PIX avec la section de capture GPU ouverte avec le panneau de capture GPU mis en surbrillance](images/pix-img-15.png)

3. <span data-ttu-id="f4dd1-153">Appuyez sur **Démarrer** pour commencer l’analyse :</span><span class="sxs-lookup"><span data-stu-id="f4dd1-153">Press **Start** to begin the analysis:</span></span>

![Capture d’écran de l’application PIX bouton Démarrer mis en surbrillance](images/pix-img-16.png)

> [!IMPORTANT]
> <span data-ttu-id="f4dd1-155">Si vous collectez des données de minutage après avoir effectué une capture GPU, vous devrez redémarrer le casque.</span><span class="sxs-lookup"><span data-stu-id="f4dd1-155">If you collect timing data after taking a GPU capture, you'll be required to reboot the headset.</span></span> <span data-ttu-id="f4dd1-156">Il s’agit d’un redémarrage unique de l’appareil, qui est requis pour la collecte des données de minutage.</span><span class="sxs-lookup"><span data-stu-id="f4dd1-156">This is a one-time restart of the device and is required for timing data collection.</span></span>

<span data-ttu-id="f4dd1-157">PIX est maintenant prêt à être utilisé.</span><span class="sxs-lookup"><span data-stu-id="f4dd1-157">PIX is now ready for use!</span></span>

## <a name="see-also"></a><span data-ttu-id="f4dd1-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f4dd1-158">See also</span></span>
* [<span data-ttu-id="f4dd1-159">Page d’accueil PIX</span><span class="sxs-lookup"><span data-stu-id="f4dd1-159">PIX homepage</span></span>](https://devblogs.microsoft.com/pix)