---
title: 6. Empaquetage et déploiement sur un appareil ou un émulateur
description: Partie 6 sur 6 d’une série de tutoriels visant à créer une application de jeu d’échecs simple avec Unreal Engine 4 et le plug-in Mixed Reality Toolkit UX Tools
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, réalité mixte, tutoriel, bien démarrer, mrtk, uxt, UX Tools, documentation, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle
ms.openlocfilehash: 83d8068ca8ce73f23edb85cf9044db5409105380
ms.sourcegitcommit: 9a93c9e9b3b088da942ac4386813ecf263c2e324
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97865394"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a><span data-ttu-id="ec02d-104">6. Empaquetage et déploiement sur un appareil ou un émulateur</span><span class="sxs-lookup"><span data-stu-id="ec02d-104">6. Packaging & deploying to device or emulator</span></span>

<span data-ttu-id="ec02d-105">Dans le tutoriel précédent, vous avez ajouté un bouton simple qui rétablit la pièce de jeu d’échecs à sa position d’origine.</span><span class="sxs-lookup"><span data-stu-id="ec02d-105">In the previous tutorial, you added a simple button that resets the chess piece to its original position.</span></span> <span data-ttu-id="ec02d-106">Dans cette section finale, vous allez préparer l’application à être exécutée sur un appareil ou un émulateur HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ec02d-106">In this final section, you'll get the app ready to run on a HoloLens 2 or an Emulator.</span></span> <span data-ttu-id="ec02d-107">Si vous disposez d’un appareil HoloLens 2, vous pouvez effectuer un streaming depuis votre ordinateur ou empaqueter l’application pour qu’elle s’exécute directement sur l’appareil.</span><span class="sxs-lookup"><span data-stu-id="ec02d-107">If you have a HoloLens 2, you can either stream from your computer or package the app to run directly on the device.</span></span> <span data-ttu-id="ec02d-108">Si vous n’avez pas d’appareil, vous allez empaqueter l’application pour qu’elle s’exécute sur l’émulateur.</span><span class="sxs-lookup"><span data-stu-id="ec02d-108">If you don't have a device, you'll be packaging the app to run on the Emulator.</span></span> <span data-ttu-id="ec02d-109">À la fin de cette section, vous aurez une application de réalité mixte déployée que vous pourrez lire, complète avec des interactions et une interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ec02d-109">By the end of this section, you'll have a deployed mixed reality app that you can play, complete with interactions and UI.</span></span>

## <a name="objectives"></a><span data-ttu-id="ec02d-110">Objectifs</span><span class="sxs-lookup"><span data-stu-id="ec02d-110">Objectives</span></span>

* <span data-ttu-id="ec02d-111">[Appareil uniquement] Streaming sur HoloLens 2 avec communication à distance de l’application holographique</span><span class="sxs-lookup"><span data-stu-id="ec02d-111">[Device only] Streaming to HoloLens 2 with holographic app remoting</span></span>
* <span data-ttu-id="ec02d-112">Empaquetage et déploiement de l’application sur un appareil ou émulateur HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="ec02d-112">Packaging and deploying the app to a HoloLens 2 device or emulator</span></span>

## <a name="device-only-streaming"></a><span data-ttu-id="ec02d-113">[Appareil uniquement] Streaming</span><span class="sxs-lookup"><span data-stu-id="ec02d-113">[Device Only] Streaming</span></span>

<span data-ttu-id="ec02d-114">La [communication à distance holographique](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting) signifie le streaming de données à partir d’un PC ou d’un appareil UWP autonome vers HoloLens 2, sans changer de canal.</span><span class="sxs-lookup"><span data-stu-id="ec02d-114">[Holographic Remoting](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting) means streaming data from a PC or standalone UWP device to the HoloLens 2, not switching the channel.</span></span> <span data-ttu-id="ec02d-115">Une application hôte de communication à distance reçoit un flux de données d’entrée d’un appareil HoloLens, rend le contenu dans une vue immersive virtuelle et rediffuse en streaming les images de contenu à HoloLens via Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="ec02d-115">A remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens over Wi-Fi.</span></span> <span data-ttu-id="ec02d-116">Le streaming vous permet d’ajouter des vues immersives distantes dans des logiciels de PC de bureau existants et d’accéder à plus de ressources système.</span><span class="sxs-lookup"><span data-stu-id="ec02d-116">Streaming lets you add remote immersive views into existing desktop PC software and has access to more system resources.</span></span>

<span data-ttu-id="ec02d-117">Si vous suivez ce chemin avec l’application de jeu d’échecs, vous aurez besoin de quelques éléments :</span><span class="sxs-lookup"><span data-stu-id="ec02d-117">If you're going this route with the chess app, you'll need a few things:</span></span>

1.  <span data-ttu-id="ec02d-118">Installez **Holographic Remoting Player** à partir du Microsoft Store sur votre HoloLens 2 et exécutez l’application.</span><span class="sxs-lookup"><span data-stu-id="ec02d-118">Install the **Holographic Remoting Player** from the Microsoft Store on your HoloLens 2 and run the app.</span></span> <span data-ttu-id="ec02d-119">Notez votre adresse IP affichée dans l’application.</span><span class="sxs-lookup"><span data-stu-id="ec02d-119">Note your IP address displayed in the app.</span></span>
    * <span data-ttu-id="ec02d-120">Accédez à **Modifier > Paramètres du projet** et vérifiez que la **valeur de RHI par défaut** Windows est définie sur **Valeur par défaut** ou sur **D3D11** :</span><span class="sxs-lookup"><span data-stu-id="ec02d-120">Go to **Edit > Project Settings** and sure the Windows **Default RHI** is set to **Default** or **D3D11**:</span></span>

![RHI par défaut](../images/unreal/performance-recommendations-img-09.png)

2.  <span data-ttu-id="ec02d-122">De retour dans l’éditeur Unreal, accédez à **Edit > Project Settings** et cochez la case **Enable Remoting** dans la section **Holographic Remoting**.</span><span class="sxs-lookup"><span data-stu-id="ec02d-122">Back in the Unreal editor, go to **Edit > Project Settings** and check **Enable Remoting** in the **Holographic Remoting** section.</span></span>

3.  <span data-ttu-id="ec02d-123">Redémarrez l’éditeur, entrez l’adresse IP de votre appareil (qui figure dans l’application Holographic Remoting Player), puis cliquez sur **Connect**.</span><span class="sxs-lookup"><span data-stu-id="ec02d-123">Restart the editor, then enter your device's IP address (as displayed in the Holographic Remoting Player app), then click **Connect**.</span></span>

<span data-ttu-id="ec02d-124">Une fois que vous êtes connecté, cliquez sur la flèche déroulante à droite du bouton **Play** et sélectionnez **VR Preview**.</span><span class="sxs-lookup"><span data-stu-id="ec02d-124">Once you’re connected, click the drop-down arrow to the right of the **Play** button and select **VR Preview**.</span></span> <span data-ttu-id="ec02d-125">L’application est exécutée dans la fenêtre VR Preview, qui est diffusée en streaming sur le casque HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ec02d-125">The app will run in the VR Preview window, which is streamed to the HoloLens headset.</span></span>

## <a name="packaging-and-deploying-the-app-via-device-portal"></a><span data-ttu-id="ec02d-126">Empaquetage et déploiement de l’application par le biais du portail de l’appareil</span><span class="sxs-lookup"><span data-stu-id="ec02d-126">Packaging and deploying the app via device portal</span></span>

>[!NOTE]
><span data-ttu-id="ec02d-127">S’il s’agit de la première fois que vous empaquetez une application Unreal pour HoloLens, vous devrez télécharger les fichiers de prise en charge à partir de l’Epic Launcher.</span><span class="sxs-lookup"><span data-stu-id="ec02d-127">If this is your first time packaging an Unreal app for HoloLens, you'll need to download supporting files from the Epic Launcher.</span></span>
>- <span data-ttu-id="ec02d-128">Accédez à **Préférences de l’éditeur > Général > Code source > Éditeur de code source** et vérifiez que Visual Studio 2019 est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="ec02d-128">Go to **Editor Preferences > General > Source Code > Source Code Editor** and check that Visual Studio 2019 is selected.</span></span>
>- <span data-ttu-id="ec02d-129">Accédez à l’onglet **Library** dans Epic Games Launcher, sélectionnez la flèche déroulante à côté de **Launch**, puis cliquez sur **Options**.</span><span class="sxs-lookup"><span data-stu-id="ec02d-129">Go to the **Library** tab in the Epic Games Launcher, select the dropdown arrow next to **Launch** >and click **Options**.</span></span>
>- <span data-ttu-id="ec02d-130">Sous **Target Platforms**, sélectionnez **HoloLens 2** et cliquez sur **Apply**.</span><span class="sxs-lookup"><span data-stu-id="ec02d-130">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span>
><span data-ttu-id="ec02d-131">![Changer de plateforme cible dans les paramètres du projet](images/unreal-uxt/6-installationoptions.PNG)</span><span class="sxs-lookup"><span data-stu-id="ec02d-131">![Change target platform in project settings](images/unreal-uxt/6-installationoptions.PNG)</span></span>

1.  <span data-ttu-id="ec02d-132">Accédez à **Edit > Project Settings**.</span><span class="sxs-lookup"><span data-stu-id="ec02d-132">Go to **Edit > Project Settings**.</span></span>
    * <span data-ttu-id="ec02d-133">Ajoutez un nom de projet sous **Project > Description > About > Project Name**.</span><span class="sxs-lookup"><span data-stu-id="ec02d-133">Add a project name under **Project > Description > About > Project Name**.</span></span>
    * <span data-ttu-id="ec02d-134">Ajoutez **CN=NomVotreSociété** sous **Project > Description > Publisher > Company Distinguished Name**.</span><span class="sxs-lookup"><span data-stu-id="ec02d-134">Add **CN=YourCompanyName** under **Project > Description > Publisher > Company Distinguished Name**.</span></span>
    * <span data-ttu-id="ec02d-135">Sélectionnez **Start in VR** sous **Project > Description > Settings**.</span><span class="sxs-lookup"><span data-stu-id="ec02d-135">Select **Start in VR** under **Project > Description > Settings**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec02d-136">Si vous laissez l’un de ces champs vide, une erreur se produit quand vous tentez de générer un nouveau certificat à l’étape 3.</span><span class="sxs-lookup"><span data-stu-id="ec02d-136">Leaving either of these fields blank will result in an error when you try and generate a new certificate in step 3.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec02d-137">Le nom de l’éditeur doit être au [format de nom unique LADPv3](https://www.ietf.org/rfc/rfc2253.txt).</span><span class="sxs-lookup"><span data-stu-id="ec02d-137">The publisher's name must be in [LADPv3 Distinguished Names Format](https://www.ietf.org/rfc/rfc2253.txt).</span></span> <span data-ttu-id="ec02d-138">Un nom d’éditeur incorrect provoque l’affichage du message d’erreur « Clé de signature introuvable.</span><span class="sxs-lookup"><span data-stu-id="ec02d-138">A malformed publisher's name leads to the "Signing key not found.</span></span> <span data-ttu-id="ec02d-139">L’application n’a pas pu être signée numériquement. »</span><span class="sxs-lookup"><span data-stu-id="ec02d-139">The app could not be digitally signed."</span></span> <span data-ttu-id="ec02d-140">lors de l’empaquetage.</span><span class="sxs-lookup"><span data-stu-id="ec02d-140">error upon packaging.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec02d-141">Si vous ne sélectionnez pas « Start in VR », votre application essaie de démarrer dans une ardoise</span><span class="sxs-lookup"><span data-stu-id="ec02d-141">Not selecting "Start in VR" will lead your application trying to start in a slate</span></span>

![Paramètres du projet - Description](images/unreal-uxt/6-cn-new.PNG)

2.  <span data-ttu-id="ec02d-143">Cochez les cases **Build for HoloLens Emulation** et/ou **Build for HoloLens Device** sous **Platforms > HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="ec02d-143">Enable **Build for HoloLens Emulation** and/or **Build for HoloLens Device** under **Platforms > HoloLens**.</span></span>

3.  <span data-ttu-id="ec02d-144">Cliquez sur **Generate new** dans la section **Packaging** (en regard de **Signing Certificate**).</span><span class="sxs-lookup"><span data-stu-id="ec02d-144">Click **Generate new** in the **Packaging** section (next to **Signing Certificate**).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec02d-145">Si vous utilisez un certificat déjà généré, le nom de l’éditeur du certificat doit être identique au nom de l’éditeur de l’application.</span><span class="sxs-lookup"><span data-stu-id="ec02d-145">If you're using an already generated certificate, then the certificate's publisher name must be the same as the application's publisher name.</span></span> <span data-ttu-id="ec02d-146">Sinon, le message d’erreur « Clé de signature introuvable.</span><span class="sxs-lookup"><span data-stu-id="ec02d-146">Otherwise it leads to the "Signing key not found.</span></span> <span data-ttu-id="ec02d-147">L’application n’a pas pu être signée numériquement. »</span><span class="sxs-lookup"><span data-stu-id="ec02d-147">The app could not be digitally signed."</span></span> <span data-ttu-id="ec02d-148">erreur.</span><span class="sxs-lookup"><span data-stu-id="ec02d-148">error.</span></span>

![Paramètres du projet - Plateformes - HoloLens](images/unreal-uxt/6-packaging.PNG)

4. <span data-ttu-id="ec02d-150">Cliquez sur **None** à des fins de test quand vous êtes invité à créer un mot de passe de clé privée.</span><span class="sxs-lookup"><span data-stu-id="ec02d-150">Click **None** for testing purposes when you're prompted to create a Private Key Password.</span></span>

![Génération du nouveau certificat](images/unreal-uxt/6-private-key-testing.png)

5. <span data-ttu-id="ec02d-152">Accédez à **File > Package Project** et sélectionnez **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="ec02d-152">Go to **File > Package Project** and select **HoloLens**.</span></span>
    * <span data-ttu-id="ec02d-153">Créez un dossier où enregistrer votre package, puis cliquez sur **Select Folder**.</span><span class="sxs-lookup"><span data-stu-id="ec02d-153">Create a new folder to save your package in and click **Select Folder**.</span></span>

6.  <span data-ttu-id="ec02d-154">Ouvrez le [Portail d’appareil Windows](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal) une fois l’application empaquetée, accédez à **Views > Apps** et recherchez la section **Deploy apps**.</span><span class="sxs-lookup"><span data-stu-id="ec02d-154">Open the [Windows Device Portal](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal) once the app is packaged, go to **Views > Apps** and find the **Deploy apps** section.</span></span>

7.  <span data-ttu-id="ec02d-155">Cliquez sur **Browse...** , accédez à votre fichier **ChessApp.appxbundle**, puis cliquez sur **Open**.</span><span class="sxs-lookup"><span data-stu-id="ec02d-155">Click **Browse...**, go to your **ChessApp.appxbundle** file and click **Open**.</span></span>

    * <span data-ttu-id="ec02d-156">Cochez la case en regard de **Allow me to select framework packages** si vous installez l’application sur votre appareil pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="ec02d-156">Check the box next to **Allow me to select framework packages** if you're installing the app on your device for the first time.</span></span>
    * <span data-ttu-id="ec02d-157">Dans la boîte de dialogue suivante, incluez les fichiers **VCLibs** et **appx** appropriés, **arm64** pour l’appareil et **x64** pour l’émulateur.</span><span class="sxs-lookup"><span data-stu-id="ec02d-157">In the next dialogue, include the appropriate **VCLibs** and **appx** files, **arm64** for device and **x64** for emulator.</span></span> <span data-ttu-id="ec02d-158">Vous trouverez les fichiers sous **HoloLens** dans le dossier où vous avez enregistré votre package.</span><span class="sxs-lookup"><span data-stu-id="ec02d-158">You can find the files under **HoloLens** inside the folder where you saved your package.</span></span>

8.  <span data-ttu-id="ec02d-159">Cliquez sur **Install**.</span><span class="sxs-lookup"><span data-stu-id="ec02d-159">Click **Install**</span></span>
    * <span data-ttu-id="ec02d-160">Vous pouvez maintenant accéder à **All Apps** et appuyer sur l’application que vous venez d’installer pour l’exécuter, ou démarrer l’application directement à partir du **Portail d’appareil Windows**.</span><span class="sxs-lookup"><span data-stu-id="ec02d-160">You can now go to **All Apps** and tap the newly installed app to run it, or start the app directly from the **Windows Device Portal**.</span></span> 

<span data-ttu-id="ec02d-161">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="ec02d-161">Congratulations!</span></span> <span data-ttu-id="ec02d-162">Votre application de réalité mixte HoloLens est terminée et prête à l’emploi.</span><span class="sxs-lookup"><span data-stu-id="ec02d-162">Your HoloLens mixed reality application is finished and ready to go.</span></span> <span data-ttu-id="ec02d-163">Vous n’en avez cependant pas terminé.</span><span class="sxs-lookup"><span data-stu-id="ec02d-163">However, you're not at the end of the road.</span></span> <span data-ttu-id="ec02d-164">MRTK comporte un grand nombre de fonctionnalités autonomes que vous pouvez ajouter à vos projets, notamment le mappage spatial, le pointage du regard et l’entrée vocale, voire même les codes QR.</span><span class="sxs-lookup"><span data-stu-id="ec02d-164">MRTK has lots of standalone features that you can add to your projects, including spatial mapping, gaze and voice input, and even QR codes.</span></span> <span data-ttu-id="ec02d-165">Pour plus d’informations sur ces fonctionnalités, consultez la [vue d’ensemble du développement Unreal](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).</span><span class="sxs-lookup"><span data-stu-id="ec02d-165">More information on these features can be found in the [Unreal development overview](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="ec02d-166">Point de contrôle de développement suivant</span><span class="sxs-lookup"><span data-stu-id="ec02d-166">Next Development Checkpoint</span></span>

<span data-ttu-id="ec02d-167">Si vous suivez le parcours de développement Unreal que nous avons mis en place, vous êtes en train d’explorer les modules de base du MRTK.</span><span class="sxs-lookup"><span data-stu-id="ec02d-167">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="ec02d-168">À partir d’ici, vous pouvez passer au composant suivant :</span><span class="sxs-lookup"><span data-stu-id="ec02d-168">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ec02d-169">Entrée avec le pointage du regard</span><span class="sxs-lookup"><span data-stu-id="ec02d-169">Gaze input</span></span>](../unreal-gaze-input.md)

<span data-ttu-id="ec02d-170">Ou accéder aux API et fonctionnalités de la plateforme Mixed Reality :</span><span class="sxs-lookup"><span data-stu-id="ec02d-170">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ec02d-171">Caméra HoloLens</span><span class="sxs-lookup"><span data-stu-id="ec02d-171">HoloLens camera</span></span>](../unreal-hololens-camera.md)

<span data-ttu-id="ec02d-172">Vous pouvez revenir aux [points de contrôle de développement Unreal](../unreal-development-overview.md#2-core-building-blocks) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="ec02d-172">You can always go back to the [Unreal development checkpoints](../unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>
