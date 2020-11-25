---
title: 6. Empaquetage et déploiement sur un appareil ou un émulateur
description: Sixième tutoriel d’une série de six visant à créer une application de jeu d’échecs simple avec Unreal Engine 4 et le plug-in Mixed Reality Toolkit UX Tools
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, réalité mixte, tutoriel, bien démarrer, mrtk, uxt, UX Tools, documentation, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle
ms.openlocfilehash: cbdbf87d75dcfc56c8eea52f7dff4a646f3b6a5d
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679818"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a><span data-ttu-id="0460a-104">6. Empaquetage et déploiement sur un appareil ou un émulateur</span><span class="sxs-lookup"><span data-stu-id="0460a-104">6. Packaging & deploying to device or emulator</span></span>

## <a name="overview"></a><span data-ttu-id="0460a-105">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="0460a-105">Overview</span></span>

<span data-ttu-id="0460a-106">Dans le tutoriel précédent, vous avez ajouté un bouton simple qui rétablit la pièce de jeu d’échecs à sa position d’origine.</span><span class="sxs-lookup"><span data-stu-id="0460a-106">In the previous tutorial, you added a simple button that resets the chess piece to its original position.</span></span> <span data-ttu-id="0460a-107">Dans cette section finale, vous allez préparer l’application à être exécutée sur un appareil ou un émulateur HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0460a-107">In this final section, you'll get the app ready to run on a HoloLens 2 or an Emulator.</span></span> <span data-ttu-id="0460a-108">Si vous disposez d’un appareil HoloLens 2, vous pouvez effectuer un streaming depuis votre ordinateur ou empaqueter l’application pour qu’elle s’exécute directement sur l’appareil.</span><span class="sxs-lookup"><span data-stu-id="0460a-108">If you have a HoloLens 2, you can either stream from your computer or package the app to run directly on the device.</span></span> <span data-ttu-id="0460a-109">Si vous n’avez pas d’appareil, vous allez empaqueter l’application pour qu’elle s’exécute sur l’émulateur.</span><span class="sxs-lookup"><span data-stu-id="0460a-109">If you don't have a device, you'll be packaging the app to run on the Emulator.</span></span> <span data-ttu-id="0460a-110">À la fin de cette section, vous aurez une application de réalité mixte déployée que vous pourrez lire, complète avec des interactions et une interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0460a-110">By the end of this section, you'll have a deployed mixed reality app that you can play, complete with interactions and UI.</span></span>

## <a name="objectives"></a><span data-ttu-id="0460a-111">Objectifs</span><span class="sxs-lookup"><span data-stu-id="0460a-111">Objectives</span></span>

* <span data-ttu-id="0460a-112">[Appareil uniquement] Streaming sur HoloLens 2 avec communication à distance de l’application holographique</span><span class="sxs-lookup"><span data-stu-id="0460a-112">[Device only] Streaming to HoloLens 2 with holographic app remoting</span></span>
* <span data-ttu-id="0460a-113">Empaquetage et déploiement de l’application sur un appareil ou émulateur HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="0460a-113">Packaging and deploying the app to a HoloLens 2 device or emulator</span></span>

## <a name="device-only-streaming"></a><span data-ttu-id="0460a-114">[Appareil uniquement] Streaming</span><span class="sxs-lookup"><span data-stu-id="0460a-114">[Device Only] Streaming</span></span>
<span data-ttu-id="0460a-115">La [communication à distance holographique](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting) dans cet exemple signifie le streaming des données à partir d’un PC ou d’un appareil UWP autonome vers l’appareil HoloLens 2, sans basculer le canal.</span><span class="sxs-lookup"><span data-stu-id="0460a-115">[Holographic Remoting](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting) in this case means streaming data from a PC or standalone UWP device to the HoloLens 2, not switching the channel.</span></span> <span data-ttu-id="0460a-116">Son fonctionnement repose sur une application hôte de communication à distance qui reçoit un flux de données d’entrée de la part d’un appareil HoloLens, restitue le contenu dans une vue immersive virtuelle et rediffuse en streaming les images de contenu à l’appareil HoloLens par Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="0460a-116">The way this works is a remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens over Wi-Fi.</span></span> <span data-ttu-id="0460a-117">Le streaming vous permet d’ajouter des vues immersives distantes à des logiciels de PC de bureau existants et d’accéder à plus de ressources système.</span><span class="sxs-lookup"><span data-stu-id="0460a-117">Streaming allows you to add remote immersive views into existing desktop PC software and has access to more system resources.</span></span>

<span data-ttu-id="0460a-118">Si vous suivez ce chemin avec l’application de jeu d’échecs, vous aurez besoin de quelques éléments :</span><span class="sxs-lookup"><span data-stu-id="0460a-118">If you're going this route with the chess app, you'll need a few things:</span></span>

1.  <span data-ttu-id="0460a-119">Installez **Holographic Remoting Player** à partir du Microsoft Store sur votre HoloLens 2 et exécutez l’application.</span><span class="sxs-lookup"><span data-stu-id="0460a-119">Install the **Holographic Remoting Player** from the Microsoft Store on your HoloLens 2 and run the app.</span></span> <span data-ttu-id="0460a-120">Notez votre adresse IP affichée dans l’application.</span><span class="sxs-lookup"><span data-stu-id="0460a-120">Note your IP address displayed in the app.</span></span>

2.  <span data-ttu-id="0460a-121">De retour dans l’éditeur Unreal, accédez à **Edit > Project Settings** et cochez la case **Enable Remoting** dans la section **Holographic Remoting**.</span><span class="sxs-lookup"><span data-stu-id="0460a-121">Back in the Unreal editor, go to **Edit > Project Settings** and check **Enable Remoting** in the **Holographic Remoting** section.</span></span>

3.  <span data-ttu-id="0460a-122">Redémarrez l’éditeur, entrez l’adresse IP de votre appareil (qui figure dans l’application Holographic Remoting Player), puis cliquez sur **Connect**.</span><span class="sxs-lookup"><span data-stu-id="0460a-122">Restart the editor, then enter your device's IP address (as displayed in the Holographic Remoting Player app), then click **Connect**.</span></span>

<span data-ttu-id="0460a-123">Une fois que vous êtes connecté, cliquez sur la flèche déroulante à droite du bouton **Play** et sélectionnez **VR Preview**.</span><span class="sxs-lookup"><span data-stu-id="0460a-123">Once you’re connected, click the drop-down arrow to the right of the **Play** button and select **VR Preview**.</span></span> <span data-ttu-id="0460a-124">L’application est alors exécutée dans la fenêtre VR Preview, qui est diffusée en streaming sur le casque HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0460a-124">This will run the app in the VR Preview window, which is streamed to the HoloLens headset.</span></span>

## <a name="packaging-and-deploying-the-app-via-device-portal"></a><span data-ttu-id="0460a-125">Empaquetage et déploiement de l’application par le biais du portail de l’appareil</span><span class="sxs-lookup"><span data-stu-id="0460a-125">Packaging and deploying the app via device portal</span></span>

>[!NOTE]
><span data-ttu-id="0460a-126">S’il s’agit de la première fois que vous empaquetez une application Unreal pour HoloLens, vous devrez télécharger les fichiers de prise en charge à partir de l’Epic Launcher.</span><span class="sxs-lookup"><span data-stu-id="0460a-126">If this is your first time packaging an Unreal app for HoloLens, you'll need to download supporting files from the Epic Launcher.</span></span>
>- <span data-ttu-id="0460a-127">Accédez à **Préférences de l’éditeur > Général > Code source > Éditeur de code source** et vérifiez que Visual Studio 2019 est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="0460a-127">Go to **Editor Preferences > General > Source Code > Source Code Editor** and check that Visual Studio 2019 is selected.</span></span>
>- <span data-ttu-id="0460a-128">Accédez à l’onglet **Library** dans Epic Games Launcher, sélectionnez la flèche déroulante à côté de **Launch**, puis cliquez sur **Options**.</span><span class="sxs-lookup"><span data-stu-id="0460a-128">Go to the **Library** tab in the Epic Games Launcher, select the dropdown arrow next to **Launch** >and click **Options**.</span></span>
>- <span data-ttu-id="0460a-129">Sous **Target Platforms**, sélectionnez **HoloLens 2** et cliquez sur **Apply**.</span><span class="sxs-lookup"><span data-stu-id="0460a-129">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span>
><span data-ttu-id="0460a-130">![Changer de plateforme cible dans les paramètres du projet](images/unreal-uxt/6-installationoptions.PNG)</span><span class="sxs-lookup"><span data-stu-id="0460a-130">![Change target platform in project settings](images/unreal-uxt/6-installationoptions.PNG)</span></span>

1.  <span data-ttu-id="0460a-131">Accédez à **Edit > Project Settings**.</span><span class="sxs-lookup"><span data-stu-id="0460a-131">Go to **Edit > Project Settings**.</span></span>
    * <span data-ttu-id="0460a-132">Ajoutez un nom de projet sous **Project > Description > About > Project Name**.</span><span class="sxs-lookup"><span data-stu-id="0460a-132">Add a project name under **Project > Description > About > Project Name**.</span></span>
    * <span data-ttu-id="0460a-133">Ajoutez **CN=NomVotreSociété** sous **Project > Description > Publisher > Company Distinguished Name**.</span><span class="sxs-lookup"><span data-stu-id="0460a-133">Add **CN=YourCompanyName** under **Project > Description > Publisher > Company Distinguished Name**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0460a-134">Si vous laissez l’un de ces champs vide, une erreur se produit quand vous tentez de générer un nouveau certificat à l’étape 3.</span><span class="sxs-lookup"><span data-stu-id="0460a-134">Leaving either of these fields blank will result in an error when you try and generate a new certificate in step 3.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0460a-135">Le nom de l’éditeur doit être au [format de nom unique LADPv3](https://www.ietf.org/rfc/rfc2253.txt).</span><span class="sxs-lookup"><span data-stu-id="0460a-135">The publisher's name must be in [LADPv3 Distinguished Names Format](https://www.ietf.org/rfc/rfc2253.txt).</span></span> <span data-ttu-id="0460a-136">Un nom d’éditeur incorrect provoque l’affichage du message d’erreur « Clé de signature introuvable.</span><span class="sxs-lookup"><span data-stu-id="0460a-136">A malformed publisher's name leads to the "Signing key not found.</span></span> <span data-ttu-id="0460a-137">L’application n’a pas pu être signée numériquement. »</span><span class="sxs-lookup"><span data-stu-id="0460a-137">The app could not be digitally signed."</span></span> <span data-ttu-id="0460a-138">lors de l’empaquetage.</span><span class="sxs-lookup"><span data-stu-id="0460a-138">error upon packaging.</span></span>

![Paramètres du projet - Description](images/unreal-uxt/6-cn.PNG)

2.  <span data-ttu-id="0460a-140">Cochez les cases **Build for HoloLens Emulation** et/ou **Build for HoloLens Device** sous **Platforms > HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="0460a-140">Enable **Build for HoloLens Emulation** and/or **Build for HoloLens Device** under **Platforms > HoloLens**.</span></span>

3.  <span data-ttu-id="0460a-141">Cliquez sur **Generate new** dans la section **Packaging** (en regard de **Signing Certificate**).</span><span class="sxs-lookup"><span data-stu-id="0460a-141">Click **Generate new** in the **Packaging** section (next to **Signing Certificate**).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0460a-142">Si vous utilisez un certificat déjà généré, le nom de l’éditeur du certificat doit être identique au nom de l’éditeur de l’application.</span><span class="sxs-lookup"><span data-stu-id="0460a-142">If you're using an already generated certificate, then the certificate's publisher name must be the same as the application's publisher name.</span></span> <span data-ttu-id="0460a-143">Sinon, le message d’erreur « Clé de signature introuvable.</span><span class="sxs-lookup"><span data-stu-id="0460a-143">Otherwise it leads to the "Signing key not found.</span></span> <span data-ttu-id="0460a-144">L’application n’a pas pu être signée numériquement. »</span><span class="sxs-lookup"><span data-stu-id="0460a-144">The app could not be digitally signed."</span></span> <span data-ttu-id="0460a-145">erreur.</span><span class="sxs-lookup"><span data-stu-id="0460a-145">error.</span></span>

![Paramètres du projet - Plateformes - HoloLens](images/unreal-uxt/6-packaging.PNG)

4. <span data-ttu-id="0460a-147">Cliquez sur **None** à des fins de test quand vous êtes invité à créer un mot de passe de clé privée.</span><span class="sxs-lookup"><span data-stu-id="0460a-147">Click **None** for testing purposes when you're prompted to create a Private Key Password.</span></span>

![Génération du nouveau certificat](images/unreal-uxt/6-private-key-testing.png)

5. <span data-ttu-id="0460a-149">Accédez à **File > Package Project** et sélectionnez **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="0460a-149">Go to **File > Package Project** and select **HoloLens**.</span></span>
    * <span data-ttu-id="0460a-150">Créez un dossier où enregistrer votre package, puis cliquez sur **Select Folder**.</span><span class="sxs-lookup"><span data-stu-id="0460a-150">Create a new folder to save your package in and click **Select Folder**.</span></span>

6.  <span data-ttu-id="0460a-151">Ouvrez le [Portail d’appareil Windows](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal) une fois l’application empaquetée, accédez à **Views > Apps** et recherchez la section **Deploy apps**.</span><span class="sxs-lookup"><span data-stu-id="0460a-151">Open the [Windows Device Portal](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal) once the app is packaged, go to **Views > Apps** and find the **Deploy apps** section.</span></span>

7.  <span data-ttu-id="0460a-152">Cliquez sur **Browse...** , accédez à votre fichier **ChessApp.appxbundle**, puis cliquez sur **Open**.</span><span class="sxs-lookup"><span data-stu-id="0460a-152">Click **Browse...**, go to your **ChessApp.appxbundle** file and click **Open**.</span></span>

    * <span data-ttu-id="0460a-153">Cochez la case **Allow me to select framework packages** si c’est la première fois que vous installez l’application sur votre appareil.</span><span class="sxs-lookup"><span data-stu-id="0460a-153">Check the box next to **Allow me to select framework packages** if this is the first time you're installing the app on your device.</span></span>
    * <span data-ttu-id="0460a-154">Dans le dialogue suivant, incluez les fichiers **VCLibs** et **appx** appropriés (arm64 pour l’appareil, x64 pour l’émulateur).</span><span class="sxs-lookup"><span data-stu-id="0460a-154">In the next dialogue, include the appropriate **VCLibs** and **appx** files (arm64 for device, x64 for emulator).</span></span> <span data-ttu-id="0460a-155">Vous les trouverez sous **HoloLens** dans le dossier où vous avez enregistré votre package.</span><span class="sxs-lookup"><span data-stu-id="0460a-155">You can find these under **HoloLens** inside the folder where you saved your package.</span></span>

8.  <span data-ttu-id="0460a-156">Cliquez sur **Install**.</span><span class="sxs-lookup"><span data-stu-id="0460a-156">Click **Install**</span></span>
    * <span data-ttu-id="0460a-157">Vous pouvez maintenant accéder à **All Apps** et appuyer sur l’application que vous venez d’installer pour l’exécuter, ou vous pouvez démarrer l’application directement à partir du **Portail d’appareil Windows**.</span><span class="sxs-lookup"><span data-stu-id="0460a-157">You can now go to **All Apps** and tap the newly installed app to run it, or you can start the app directly from the **Windows Device Portal**.</span></span> 

<span data-ttu-id="0460a-158">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="0460a-158">Congratulations!</span></span> <span data-ttu-id="0460a-159">Votre application de réalité mixte HoloLens est terminée et prête à l’emploi.</span><span class="sxs-lookup"><span data-stu-id="0460a-159">Your HoloLens mixed reality application is finished and ready to go.</span></span> <span data-ttu-id="0460a-160">En revanche, vous n’avez pas encore tout vu.</span><span class="sxs-lookup"><span data-stu-id="0460a-160">However, this isn't the end of the road.</span></span> <span data-ttu-id="0460a-161">MRTK comporte un grand nombre de fonctionnalités autonomes que vous pouvez ajouter à vos projets, notamment le mappage spatial, le pointage du regard et l’entrée vocale, voire même les codes QR.</span><span class="sxs-lookup"><span data-stu-id="0460a-161">MRTK has lots of standalone features that you can add to your projects, including spatial mapping, gaze and voice input, and even QR codes.</span></span> <span data-ttu-id="0460a-162">Pour plus d’informations sur ces fonctionnalités, consultez la [vue d’ensemble du développement Unreal](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).</span><span class="sxs-lookup"><span data-stu-id="0460a-162">More information on these features can be found in the [Unreal development overview](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="0460a-163">Point de contrôle de développement suivant</span><span class="sxs-lookup"><span data-stu-id="0460a-163">Next Development Checkpoint</span></span>

<span data-ttu-id="0460a-164">Si vous suivez le parcours des points de contrôle de développement Unreal que nous avons mis en place, vous explorez actuellement les modules de base du MRTK.</span><span class="sxs-lookup"><span data-stu-id="0460a-164">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="0460a-165">À partir de là, vous pouvez passer au module suivant :</span><span class="sxs-lookup"><span data-stu-id="0460a-165">From here, you can proceed to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0460a-166">Entrée avec le pointage du regard</span><span class="sxs-lookup"><span data-stu-id="0460a-166">Gaze input</span></span>](../unreal-gaze-input.md)

<span data-ttu-id="0460a-167">Ou accéder aux API et fonctionnalités de la plateforme Mixed Reality :</span><span class="sxs-lookup"><span data-stu-id="0460a-167">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0460a-168">Caméra HoloLens</span><span class="sxs-lookup"><span data-stu-id="0460a-168">HoloLens camera</span></span>](../unreal-hololens-camera.md)

<span data-ttu-id="0460a-169">Vous pouvez revenir aux [points de contrôle de développement Unreal](../unreal-development-overview.md#2-core-building-blocks) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="0460a-169">You can always go back to the [Unreal development checkpoints](../unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>
