---
title: MR Spatial 220 - Son spatial
description: Suivez cette procédure pas à pas de codage à l’aide de Unity, Visual Studio et HoloLens pour apprendre les concepts de son spatial.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academy, didacticiel, son spatial, HoloLens, Académie de la réalité mixte, Unity, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle, Windows 10
ms.openlocfilehash: da130a5a93ec261d2e767874faa31dbc50d51b12
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582768"
---
# <a name="mr-spatial-220-spatial-sound"></a><span data-ttu-id="44de6-104">Réalité mixte - Fonctionnalités spatiales - Cours 220 : Son spatial</span><span class="sxs-lookup"><span data-stu-id="44de6-104">MR Spatial 220: Spatial sound</span></span>

>[!NOTE]
><span data-ttu-id="44de6-105">Les tutoriels Mixed Reality Academy ont été conçus pour les appareils HoloLens (1re génération) et les casques immersifs de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="44de6-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="44de6-106">Nous estimons qu’il est important de laisser ces tutoriels à la disposition des développeurs qui recherchent encore des conseils pour développer des applications sur ces appareils.</span><span class="sxs-lookup"><span data-stu-id="44de6-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="44de6-107">Notez que ces tutoriels **_ne sont pas_** mis à jour avec les derniers ensembles d’outils ou interactions utilisés pour HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="44de6-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="44de6-108">Ils sont fournis dans le but de fonctionner sur les appareils pris en charge.</span><span class="sxs-lookup"><span data-stu-id="44de6-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="44de6-109">Une [nouvelle série de tutoriels](./mr-learning-base-01.md) a été publiée pour HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="44de6-109">[A new series of tutorials](./mr-learning-base-01.md) has been posted for HoloLens 2.</span></span>

<span data-ttu-id="44de6-110">Le [son spatial](../../../design/spatial-sound.md) passe par des hologrammes et leur donne la présence dans notre monde.</span><span class="sxs-lookup"><span data-stu-id="44de6-110">[Spatial sound](../../../design/spatial-sound.md) breathes life into holograms and gives them presence in our world.</span></span> <span data-ttu-id="44de6-111">Les hologrammes sont composés de la lumière et du son, et si vous perdez la vision de vos hologrammes, le son spatial peut vous aider à les trouver.</span><span class="sxs-lookup"><span data-stu-id="44de6-111">Holograms are composed of both light and sound, and if you happen to lose sight of your holograms, spatial sound can help you find them.</span></span> <span data-ttu-id="44de6-112">Le son spatial n’est pas comme le son classique que vous entendez sur la radio, il s’agit d’un son positionné dans l’espace 3D.</span><span class="sxs-lookup"><span data-stu-id="44de6-112">Spatial sound is not like the typical sound that you would hear on the radio, it is sound that is positioned in 3D space.</span></span> <span data-ttu-id="44de6-113">Avec un son spatial, vous pouvez faire en sorte que les hologrammes s’affichent derrière vous, en regard de vous ou même en tête.</span><span class="sxs-lookup"><span data-stu-id="44de6-113">With spatial sound, you can make holograms sound like they're behind you, next to you, or even on your head!</span></span> <span data-ttu-id="44de6-114">Dans ce cours, vous allez :</span><span class="sxs-lookup"><span data-stu-id="44de6-114">In this course, you will:</span></span>

* <span data-ttu-id="44de6-115">Configurez votre environnement de développement pour utiliser le son spatial Microsoft.</span><span class="sxs-lookup"><span data-stu-id="44de6-115">Configure your development environment to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="44de6-116">Utilisez le son spatial pour améliorer les interactions.</span><span class="sxs-lookup"><span data-stu-id="44de6-116">Use Spatial Sound to enhance interactions.</span></span>
* <span data-ttu-id="44de6-117">Utilisez le son spatial conjointement avec le [mappage spatial](../../../design/spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="44de6-117">Use Spatial Sound in conjunction with [Spatial Mapping](../../../design/spatial-mapping.md).</span></span>
* <span data-ttu-id="44de6-118">Comprendre la conception et la combinaison des meilleures pratiques.</span><span class="sxs-lookup"><span data-stu-id="44de6-118">Understand sound design and mixing best practices.</span></span>
* <span data-ttu-id="44de6-119">Utilisez le son pour améliorer les effets spéciaux et amener l’utilisateur dans le monde de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="44de6-119">Use sound to enhance special effects and bring the user into the Mixed Reality world.</span></span>

## <a name="device-support"></a><span data-ttu-id="44de6-120">Prise en charge des appareils</span><span class="sxs-lookup"><span data-stu-id="44de6-120">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="44de6-121">Cours</span><span class="sxs-lookup"><span data-stu-id="44de6-121">Course</span></span></th><th style="width:150px"> <span data-ttu-id="44de6-122"><a href="/hololens/hololens1-hardware">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="44de6-122"><a href="/hololens/hololens1-hardware">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="44de6-123"><a href="../../../discover/immersive-headset-hardware-details.md">Casques immersifs</a></span><span class="sxs-lookup"><span data-stu-id="44de6-123"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="44de6-124">Réalité mixte - Fonctionnalités spatiales - Cours 220 : Son spatial</span><span class="sxs-lookup"><span data-stu-id="44de6-124">MR Spatial 220: Spatial sound</span></span></td><td style="text-align: center;"> <span data-ttu-id="44de6-125">✔️</span><span class="sxs-lookup"><span data-stu-id="44de6-125">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="44de6-126">✔️</span><span class="sxs-lookup"><span data-stu-id="44de6-126">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="44de6-127">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="44de6-127">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="44de6-128">Prérequis</span><span class="sxs-lookup"><span data-stu-id="44de6-128">Prerequisites</span></span>

* <span data-ttu-id="44de6-129">Un PC Windows 10 configuré avec les [outils appropriés installés](../../../develop/install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="44de6-129">A Windows 10 PC configured with the correct [tools installed](../../../develop/install-the-tools.md).</span></span>
* <span data-ttu-id="44de6-130">Certaines fonctionnalités de base de la programmation C#.</span><span class="sxs-lookup"><span data-stu-id="44de6-130">Some basic C# programming ability.</span></span>
* <span data-ttu-id="44de6-131">Vous devez avoir terminé les [notions de base de m. 101](../../../develop/unity/tutorials/holograms-101.md).</span><span class="sxs-lookup"><span data-stu-id="44de6-131">You should have completed [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md).</span></span>
* <span data-ttu-id="44de6-132">Un appareil HoloLens [configuré pour le développement](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="44de6-132">A HoloLens device [configured for development](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="44de6-133">Fichiers projet</span><span class="sxs-lookup"><span data-stu-id="44de6-133">Project files</span></span>

* <span data-ttu-id="44de6-134">Téléchargez les [fichiers](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) requis par le projet.</span><span class="sxs-lookup"><span data-stu-id="44de6-134">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) required by the project.</span></span> <span data-ttu-id="44de6-135">Requiert Unity 2017,2 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="44de6-135">Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="44de6-136">Si vous avez encore besoin de la prise en charge d’Unity 5,6, utilisez [cette version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span><span class="sxs-lookup"><span data-stu-id="44de6-136">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span></span> <span data-ttu-id="44de6-137">Cette version n’est peut-être plus à jour.</span><span class="sxs-lookup"><span data-stu-id="44de6-137">This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="44de6-138">Si vous avez encore besoin de la prise en charge d’Unity 5,5, utilisez [cette version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span><span class="sxs-lookup"><span data-stu-id="44de6-138">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span></span> <span data-ttu-id="44de6-139">Cette version n’est peut-être plus à jour.</span><span class="sxs-lookup"><span data-stu-id="44de6-139">This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="44de6-140">Si vous avez encore besoin de la prise en charge d’Unity 5,4, utilisez [cette version](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span><span class="sxs-lookup"><span data-stu-id="44de6-140">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span></span> <span data-ttu-id="44de6-141">Cette version n’est peut-être plus à jour.</span><span class="sxs-lookup"><span data-stu-id="44de6-141">This release may no longer be up-to-date.</span></span>
* <span data-ttu-id="44de6-142">Désarchivez les fichiers sur votre bureau ou un autre emplacement facile à atteindre.</span><span class="sxs-lookup"><span data-stu-id="44de6-142">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="44de6-143">Si vous souhaitez examiner le code source avant le téléchargement, il est [disponible sur GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span><span class="sxs-lookup"><span data-stu-id="44de6-143">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="44de6-144">Errata et notes</span><span class="sxs-lookup"><span data-stu-id="44de6-144">Errata and Notes</span></span>

* <span data-ttu-id="44de6-145">L’option « Activer Uniquement mon code » doit être désactivée (*décochée*) dans Visual Studio sous outils->Options->le débogage pour atteindre les points d’arrêt dans votre code.</span><span class="sxs-lookup"><span data-stu-id="44de6-145">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="44de6-146">Chapitre 1-Configuration Unity</span><span class="sxs-lookup"><span data-stu-id="44de6-146">Chapter 1 - Unity Setup</span></span>

### <a name="objectives"></a><span data-ttu-id="44de6-147">Objectifs</span><span class="sxs-lookup"><span data-stu-id="44de6-147">Objectives</span></span>

* <span data-ttu-id="44de6-148">Modifiez la configuration du son de l’unité pour utiliser un son spatial Microsoft.</span><span class="sxs-lookup"><span data-stu-id="44de6-148">Change Unity's sound configuration to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="44de6-149">Ajoutez du son 3D à un objet dans Unity.</span><span class="sxs-lookup"><span data-stu-id="44de6-149">Add 3D sound to an object in Unity.</span></span>

### <a name="instructions"></a><span data-ttu-id="44de6-150">Instructions</span><span class="sxs-lookup"><span data-stu-id="44de6-150">Instructions</span></span>

* <span data-ttu-id="44de6-151">Démarrez Unity.</span><span class="sxs-lookup"><span data-stu-id="44de6-151">Start Unity.</span></span>
* <span data-ttu-id="44de6-152">Sélectionnez **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="44de6-152">Select **Open**.</span></span>
* <span data-ttu-id="44de6-153">Accédez à votre bureau et recherchez le dossier que vous avez précédemment désinstallé.</span><span class="sxs-lookup"><span data-stu-id="44de6-153">Navigate to your Desktop and find the folder you previously un-archived.</span></span>
* <span data-ttu-id="44de6-154">Cliquez sur le dossier **Starting\Decibel** , puis appuyez sur le bouton **Sélectionner un dossier** .</span><span class="sxs-lookup"><span data-stu-id="44de6-154">Click on the **Starting\Decibel** folder and then press the **Select Folder** button.</span></span>
* <span data-ttu-id="44de6-155">Attendez que le projet se charge dans Unity.</span><span class="sxs-lookup"><span data-stu-id="44de6-155">Wait for the project to load in Unity.</span></span>
* <span data-ttu-id="44de6-156">Dans le panneau **projet** , ouvrez **Scenes\Decibel.Unity**.</span><span class="sxs-lookup"><span data-stu-id="44de6-156">In the **Project** panel, open **Scenes\Decibel.unity**.</span></span>
* <span data-ttu-id="44de6-157">Dans le volet **hiérarchie** , développez **HologramCollection** , puis sélectionnez **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="44de6-157">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="44de6-158">Dans l’inspecteur, développez **audiosource** et Notez qu’il n’y a pas de case à cocher **spatialiser** .</span><span class="sxs-lookup"><span data-stu-id="44de6-158">In the Inspector, expand **AudioSource** and notice that there is no **Spatialize** check box.</span></span>

<span data-ttu-id="44de6-159">Par défaut, Unity ne charge pas de plug-in Spatializer.</span><span class="sxs-lookup"><span data-stu-id="44de6-159">By default, Unity does not load a spatializer plugin.</span></span> <span data-ttu-id="44de6-160">Les étapes suivantes permettent d’activer le son spatial dans le projet.</span><span class="sxs-lookup"><span data-stu-id="44de6-160">The following steps will enable Spatial Sound in the project.</span></span>

* <span data-ttu-id="44de6-161">Dans le menu supérieur de Unity, accédez à **modifier > paramètres du projet > audio**.</span><span class="sxs-lookup"><span data-stu-id="44de6-161">In Unity's top menu, go to **Edit > Project Settings > Audio**.</span></span>
* <span data-ttu-id="44de6-162">Recherchez la liste déroulante du **plug-in Spatializer** , puis sélectionnez **MS HRTF Spatializer**.</span><span class="sxs-lookup"><span data-stu-id="44de6-162">Find the **Spatializer Plugin** dropdown, and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="44de6-163">Dans le volet **hiérarchie** , sélectionnez **HologramCollection > P0LY**.</span><span class="sxs-lookup"><span data-stu-id="44de6-163">In the **Hierarchy** panel, select **HologramCollection > P0LY**.</span></span>
* <span data-ttu-id="44de6-164">Dans le panneau **inspecteur** , recherchez le composant **audio source** .</span><span class="sxs-lookup"><span data-stu-id="44de6-164">In the **Inspector** panel, find the **Audio Source** component.</span></span>
* <span data-ttu-id="44de6-165">Cochez la case **spatialiser** .</span><span class="sxs-lookup"><span data-stu-id="44de6-165">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="44de6-166">Faites glisser le curseur de **lissage spatial** jusqu’à la forme **3D**, ou entrez **1** dans la zone d’édition.</span><span class="sxs-lookup"><span data-stu-id="44de6-166">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>

<span data-ttu-id="44de6-167">Nous allons maintenant générer le projet dans Unity et configurer la solution dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="44de6-167">We will now build the project in Unity and configure the solution in Visual Studio.</span></span>

1. <span data-ttu-id="44de6-168">Dans Unity, sélectionnez **fichier > paramètres de build**.</span><span class="sxs-lookup"><span data-stu-id="44de6-168">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="44de6-169">Cliquez sur **Ajouter des scènes ouvertes** pour ajouter la scène.</span><span class="sxs-lookup"><span data-stu-id="44de6-169">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="44de6-170">Sélectionnez **plateforme Windows universelle** dans la liste **plateforme** , puis cliquez sur **basculer la plateforme**.</span><span class="sxs-lookup"><span data-stu-id="44de6-170">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="44de6-171">Si vous développez spécifiquement pour HoloLens, définissez **appareil cible** sur **hololens**.</span><span class="sxs-lookup"><span data-stu-id="44de6-171">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="44de6-172">Dans le cas contraire, laissez-le sur **un appareil**.</span><span class="sxs-lookup"><span data-stu-id="44de6-172">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="44de6-173">Vérifiez que le **type de build** est défini sur **D3D** et que le **Kit de développement logiciel (SDK** ) est défini sur le **dernier installé** (qui doit être le SDK 16299 ou une version ultérieure).</span><span class="sxs-lookup"><span data-stu-id="44de6-173">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="44de6-174">Cliquez sur **Générer**.</span><span class="sxs-lookup"><span data-stu-id="44de6-174">Click **Build**.</span></span>
7. <span data-ttu-id="44de6-175">Créez un **dossier** nommé « App ».</span><span class="sxs-lookup"><span data-stu-id="44de6-175">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="44de6-176">Cliquez sur le dossier de l' **application** .</span><span class="sxs-lookup"><span data-stu-id="44de6-176">Single click the **App** folder.</span></span>
9. <span data-ttu-id="44de6-177">Appuyez sur **Sélectionner un dossier**.</span><span class="sxs-lookup"><span data-stu-id="44de6-177">Press **Select Folder**.</span></span>

<span data-ttu-id="44de6-178">Lorsque Unity est terminé, une fenêtre de l’Explorateur de fichiers s’affiche.</span><span class="sxs-lookup"><span data-stu-id="44de6-178">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="44de6-179">Ouvrez le dossier de l' **application** .</span><span class="sxs-lookup"><span data-stu-id="44de6-179">Open the **App** folder.</span></span>
2. <span data-ttu-id="44de6-180">Ouvrez la **solution Visual Studio décibels**.</span><span class="sxs-lookup"><span data-stu-id="44de6-180">Open the **Decibel Visual Studio Solution**.</span></span>

<span data-ttu-id="44de6-181">En cas de déploiement dans HoloLens :</span><span class="sxs-lookup"><span data-stu-id="44de6-181">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="44de6-182">À l’aide de la barre d’outils supérieure dans Visual Studio, remplacez la cible Debug par **Release** et de ARM par **x86**.</span><span class="sxs-lookup"><span data-stu-id="44de6-182">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="44de6-183">Cliquez sur la flèche déroulante en regard du bouton ordinateur local, puis sélectionnez **ordinateur distant**.</span><span class="sxs-lookup"><span data-stu-id="44de6-183">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="44de6-184">Entrez **l’adresse IP de votre appareil HoloLens** et définissez le mode d’authentification sur **universel (protocole non chiffré)**.</span><span class="sxs-lookup"><span data-stu-id="44de6-184">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="44de6-185">Cliquez sur **Sélectionner**.</span><span class="sxs-lookup"><span data-stu-id="44de6-185">Click **Select**.</span></span> <span data-ttu-id="44de6-186">Si vous ne connaissez pas l’adresse IP de votre appareil, accédez à **paramètres > réseau & Internet > options avancées**.</span><span class="sxs-lookup"><span data-stu-id="44de6-186">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="44de6-187">Dans la barre de menus supérieure, cliquez sur **Déboguer-> exécuter sans débogage** ou appuyez sur **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="44de6-187">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="44de6-188">S’il s’agit de la première fois que vous déployez sur votre appareil, vous devrez le [coupler à Visual Studio](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).</span><span class="sxs-lookup"><span data-stu-id="44de6-188">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).</span></span>

<span data-ttu-id="44de6-189">En cas de déploiement sur un casque immersif :</span><span class="sxs-lookup"><span data-stu-id="44de6-189">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="44de6-190">À l’aide de la barre d’outils supérieure dans Visual Studio, remplacez la cible Debug par **Release** et de ARM par **x64**.</span><span class="sxs-lookup"><span data-stu-id="44de6-190">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="44de6-191">Assurez-vous que la cible de déploiement est définie sur **ordinateur local**.</span><span class="sxs-lookup"><span data-stu-id="44de6-191">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="44de6-192">Dans la barre de menus supérieure, cliquez sur **Déboguer-> exécuter sans débogage** ou appuyez sur **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="44de6-192">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>

## <a name="chapter-2---spatial-sound-and-interaction"></a><span data-ttu-id="44de6-193">Chapitre 2-sons spatiaux et interaction</span><span class="sxs-lookup"><span data-stu-id="44de6-193">Chapter 2 - Spatial Sound and Interaction</span></span>

### <a name="objectives"></a><span data-ttu-id="44de6-194">Objectifs</span><span class="sxs-lookup"><span data-stu-id="44de6-194">Objectives</span></span>

* <span data-ttu-id="44de6-195">Améliorez le réalisme des hologrammes à l’aide du son.</span><span class="sxs-lookup"><span data-stu-id="44de6-195">Enhance hologram realism using sound.</span></span>
* <span data-ttu-id="44de6-196">Dirigez le point de regard de l’utilisateur à l’aide du son.</span><span class="sxs-lookup"><span data-stu-id="44de6-196">Direct the user's gaze using sound.</span></span>
* <span data-ttu-id="44de6-197">Fournir des commentaires de mouvement en utilisant le son.</span><span class="sxs-lookup"><span data-stu-id="44de6-197">Provide gesture feedback using sound.</span></span>

### <a name="part-1---enhancing-realism"></a><span data-ttu-id="44de6-198">Partie 1-amélioration du réalisme</span><span class="sxs-lookup"><span data-stu-id="44de6-198">Part 1 - Enhancing Realism</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="44de6-199">Concepts clés</span><span class="sxs-lookup"><span data-stu-id="44de6-199">Key Concepts</span></span>

* <span data-ttu-id="44de6-200">Spatialer les sons hologrammes.</span><span class="sxs-lookup"><span data-stu-id="44de6-200">Spatialize hologram sounds.</span></span>
* <span data-ttu-id="44de6-201">Les sources audio doivent être placées à un emplacement approprié sur l’hologramme.</span><span class="sxs-lookup"><span data-stu-id="44de6-201">Sound sources should be placed at an appropriate location on the hologram.</span></span>

<span data-ttu-id="44de6-202">L’emplacement approprié pour le son va dépendre de l’hologramme.</span><span class="sxs-lookup"><span data-stu-id="44de6-202">The appropriate location for the sound is going to depend on the hologram.</span></span> <span data-ttu-id="44de6-203">Par exemple, si l’hologramme est un homme, la source du son doit être située près de la bouche et non pas des pieds.</span><span class="sxs-lookup"><span data-stu-id="44de6-203">For example, if the hologram is of a human, the sound source should be located near the mouth and not the feet.</span></span>

#### <a name="instructions"></a><span data-ttu-id="44de6-204">Instructions</span><span class="sxs-lookup"><span data-stu-id="44de6-204">Instructions</span></span>

<span data-ttu-id="44de6-205">Les instructions suivantes attachent un son spatial à un hologramme.</span><span class="sxs-lookup"><span data-stu-id="44de6-205">The following instructions will attach a spatialized sound to a hologram.</span></span>

* <span data-ttu-id="44de6-206">Dans le volet **hiérarchie** , développez **HologramCollection** , puis sélectionnez **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="44de6-206">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="44de6-207">Dans le volet de l' **inspecteur** , dans le **audiosource**, cliquez sur le cercle en regard de **Audioclip** et sélectionnez **polypointer** dans la fenêtre contextuelle.</span><span class="sxs-lookup"><span data-stu-id="44de6-207">In the **Inspector** panel, in the **AudioSource**, click the circle next to **AudioClip** and select **PolyHover** from the pop-up.</span></span>
* <span data-ttu-id="44de6-208">Cliquez sur le cercle en regard de **sortie** et sélectionnez **SoundEffects** dans la fenêtre contextuelle.</span><span class="sxs-lookup"><span data-stu-id="44de6-208">Click the circle next to **Output** and select **SoundEffects** from the pop-up.</span></span>

<span data-ttu-id="44de6-209">Project décibel utilise un composant Unity **audiomixer** pour permettre l’ajustement des niveaux sonores pour les groupes de sons.</span><span class="sxs-lookup"><span data-stu-id="44de6-209">Project Decibel uses a Unity **AudioMixer** component to enable adjusting sound levels for groups of sounds.</span></span> <span data-ttu-id="44de6-210">En regroupant les sons de cette manière, le volume global peut être ajusté tout en conservant le volume relatif de chaque son.</span><span class="sxs-lookup"><span data-stu-id="44de6-210">By grouping sounds this way, the overall volume can be adjusted while maintaining the relative volume of each sound.</span></span>

* <span data-ttu-id="44de6-211">Dans le **audiosource**, développez **paramètres audio 3D**.</span><span class="sxs-lookup"><span data-stu-id="44de6-211">In the **AudioSource**, expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="44de6-212">Affectez au **niveau Doppler** la valeur **0**.</span><span class="sxs-lookup"><span data-stu-id="44de6-212">Set **Doppler Level** to **0**.</span></span>

<span data-ttu-id="44de6-213">Le fait de définir le niveau Doppler sur zéro désactive les modifications du pas en raison du mouvement (de l’hologramme ou de l’utilisateur).</span><span class="sxs-lookup"><span data-stu-id="44de6-213">Setting Doppler level to zero disables changes in pitch caused by motion (either of the hologram or the user).</span></span> <span data-ttu-id="44de6-214">Un exemple classique de Doppler est un véhicule à déplacement rapide.</span><span class="sxs-lookup"><span data-stu-id="44de6-214">A classic example of Doppler is a fast-moving car.</span></span> <span data-ttu-id="44de6-215">À mesure que la voiture approche un écouteur stationnaire, la hauteur du moteur augmente.</span><span class="sxs-lookup"><span data-stu-id="44de6-215">As the car approaches a stationary listener, the pitch of the engine rises.</span></span> <span data-ttu-id="44de6-216">Lorsqu’il passe l’écouteur, le pas à pas est inférieur à la distance.</span><span class="sxs-lookup"><span data-stu-id="44de6-216">When it passes the listener, the pitch lowers with distance.</span></span>

### <a name="part-2---directing-the-users-gaze"></a><span data-ttu-id="44de6-217">Partie 2 : diriger le regard de l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="44de6-217">Part 2 - Directing the User's Gaze</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="44de6-218">Concepts clés</span><span class="sxs-lookup"><span data-stu-id="44de6-218">Key Concepts</span></span>

* <span data-ttu-id="44de6-219">Utilisez le son pour attirer l’attention sur des hologrammes importants.</span><span class="sxs-lookup"><span data-stu-id="44de6-219">Use sound to call attention to important holograms.</span></span>
* <span data-ttu-id="44de6-220">Les oreilles vous aident directement là où les yeux doivent ressembler.</span><span class="sxs-lookup"><span data-stu-id="44de6-220">The ears help direct where the eyes should look.</span></span>
* <span data-ttu-id="44de6-221">Le cerveau a des attentes apprises.</span><span class="sxs-lookup"><span data-stu-id="44de6-221">The brain has some learned expectations.</span></span>

<span data-ttu-id="44de6-222">Un exemple de l’expérience acquise est que les oiseaux sont généralement au-dessus des têtes des êtres humains.</span><span class="sxs-lookup"><span data-stu-id="44de6-222">One example of learned expectations is that birds are generally above the heads of humans.</span></span> <span data-ttu-id="44de6-223">Si un utilisateur entend un son oiseau, sa réaction initiale est de rechercher.</span><span class="sxs-lookup"><span data-stu-id="44de6-223">If a user hears a bird sound, their initial reaction is to look up.</span></span> <span data-ttu-id="44de6-224">Le fait de placer un oiseau au-dessous de l’utilisateur peut entraîner une direction correcte du son, mais ne parvient pas à trouver l’hologramme en raison de la nécessité d’effectuer des recherches.</span><span class="sxs-lookup"><span data-stu-id="44de6-224">Placing a bird below the user can lead to them facing the correct direction of the sound, but being unable to find the hologram based on the expectation of needing to look up.</span></span>

#### <a name="instructions"></a><span data-ttu-id="44de6-225">Instructions</span><span class="sxs-lookup"><span data-stu-id="44de6-225">Instructions</span></span>

<span data-ttu-id="44de6-226">Les instructions suivantes permettent à P0LY de se masquer derrière vous, afin que vous puissiez utiliser le son pour localiser l’hologramme.</span><span class="sxs-lookup"><span data-stu-id="44de6-226">The following instructions enable P0LY to hide behind you, so that you can use sound to locate the hologram.</span></span>

* <span data-ttu-id="44de6-227">Dans le volet **hiérarchie** , sélectionnez **gestionnaires**.</span><span class="sxs-lookup"><span data-stu-id="44de6-227">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="44de6-228">Dans le panneau **inspecteur** , recherchez **Gestionnaire d’entrée vocale**.</span><span class="sxs-lookup"><span data-stu-id="44de6-228">In the **Inspector** panel, find **Speech Input Handler**.</span></span>
* <span data-ttu-id="44de6-229">Dans le **Gestionnaire d’entrée vocal**, développez **Go Hide**.</span><span class="sxs-lookup"><span data-stu-id="44de6-229">In **Speech Input Handler**, expand **Go Hide**.</span></span>
* <span data-ttu-id="44de6-230">**Ne modifiez aucune fonction** en **polyactions. GoHide**.</span><span class="sxs-lookup"><span data-stu-id="44de6-230">Change **No Function** to **PolyActions.GoHide**.</span></span>

![Mot clé : go Hide](images/gohide.png)

### <a name="part-3---gesture-feedback"></a><span data-ttu-id="44de6-232">Partie 3 : commentaires sur les mouvements</span><span class="sxs-lookup"><span data-stu-id="44de6-232">Part 3 - Gesture Feedback</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="44de6-233">Concepts clés</span><span class="sxs-lookup"><span data-stu-id="44de6-233">Key Concepts</span></span>

* <span data-ttu-id="44de6-234">Fournir à l’utilisateur une confirmation de mouvement positive à l’aide du son</span><span class="sxs-lookup"><span data-stu-id="44de6-234">Provide the user with positive gesture confirmation using sound</span></span>
* <span data-ttu-id="44de6-235">N’encombrez pas les sons trop bruyants de l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="44de6-235">Do not overwhelm the user - overly loud sounds get in the way</span></span>
* <span data-ttu-id="44de6-236">Les sons subtils fonctionnent mieux : ne assombrissent pas l’expérience</span><span class="sxs-lookup"><span data-stu-id="44de6-236">Subtle sounds work best - do not overshadow the experience</span></span>

#### <a name="instructions"></a><span data-ttu-id="44de6-237">Instructions</span><span class="sxs-lookup"><span data-stu-id="44de6-237">Instructions</span></span>

* <span data-ttu-id="44de6-238">Dans le volet **hiérarchie** , développez **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="44de6-238">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="44de6-239">Développez **EnergyHub** et sélectionnez **base**.</span><span class="sxs-lookup"><span data-stu-id="44de6-239">Expand **EnergyHub** and select **Base**.</span></span>
* <span data-ttu-id="44de6-240">Dans le panneau **inspecteur** , cliquez sur **Ajouter un composant** et ajouter un gestionnaire de sons de **geste**.</span><span class="sxs-lookup"><span data-stu-id="44de6-240">In the **Inspector** panel, click **Add Component** and add **Gesture Sound Handler**.</span></span>
* <span data-ttu-id="44de6-241">Dans **Gestionnaire de sons de geste**, cliquez sur le cercle en regard de l' **élément de navigation démarré** et de la **navigation mise à jour** , puis sélectionnez **RotateClick** dans la fenêtre contextuelle pour les deux.</span><span class="sxs-lookup"><span data-stu-id="44de6-241">In **Gesture Sound Handler**, click the circle next to **Navigation Started Clip** and **Navigation Updated Clip** and select **RotateClick** from the pop-up for both.</span></span>
* <span data-ttu-id="44de6-242">Double-cliquez sur « GestureSoundHandler » pour charger dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="44de6-242">Double click on "GestureSoundHandler" to load in Visual Studio.</span></span>

<span data-ttu-id="44de6-243">Le gestionnaire de son geste effectue les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="44de6-243">Gesture Sound Handler performs the following tasks:</span></span>

* <span data-ttu-id="44de6-244">Créez et configurez un **audiosource**.</span><span class="sxs-lookup"><span data-stu-id="44de6-244">Create and configure an **AudioSource**.</span></span>
* <span data-ttu-id="44de6-245">Placez le **audiosource** à l’emplacement du **gameobject** approprié.</span><span class="sxs-lookup"><span data-stu-id="44de6-245">Place the **AudioSource** at the location of the appropriate **GameObject**.</span></span>
* <span data-ttu-id="44de6-246">Lit le **Audioclip** associé au geste.</span><span class="sxs-lookup"><span data-stu-id="44de6-246">Plays the **AudioClip** associated with the gesture.</span></span>

#### <a name="build-and-deploy"></a><span data-ttu-id="44de6-247">Génération et déploiement</span><span class="sxs-lookup"><span data-stu-id="44de6-247">Build and Deploy</span></span>

1. <span data-ttu-id="44de6-248">Dans Unity, sélectionnez **fichier > paramètres de build**.</span><span class="sxs-lookup"><span data-stu-id="44de6-248">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="44de6-249">Cliquez sur **Générer**.</span><span class="sxs-lookup"><span data-stu-id="44de6-249">Click **Build**.</span></span>
3. <span data-ttu-id="44de6-250">Cliquez sur le dossier de l' **application** .</span><span class="sxs-lookup"><span data-stu-id="44de6-250">Single click the **App** folder.</span></span>
4. <span data-ttu-id="44de6-251">Appuyez sur **Sélectionner un dossier**.</span><span class="sxs-lookup"><span data-stu-id="44de6-251">Press **Select Folder**.</span></span>

<span data-ttu-id="44de6-252">Vérifiez que la barre d’outils indique « version finale », « x86 » ou « x64 », et « périphérique distant ».</span><span class="sxs-lookup"><span data-stu-id="44de6-252">Check that the Toolbar says "Release", "x86" or "x64", and "Remote Device".</span></span> <span data-ttu-id="44de6-253">Dans le cas contraire, il s’agit de l’instance de codage de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="44de6-253">If not, this is the coding instance of Visual Studio.</span></span> <span data-ttu-id="44de6-254">Vous devrez peut-être rouvrir la solution à partir du dossier de l’application.</span><span class="sxs-lookup"><span data-stu-id="44de6-254">You may need to re-open the solution from the App folder.</span></span>

* <span data-ttu-id="44de6-255">Si vous y êtes invité, rechargez les fichiers projet.</span><span class="sxs-lookup"><span data-stu-id="44de6-255">If prompted, reload the project files.</span></span>
* <span data-ttu-id="44de6-256">Comme précédemment, déployez à partir de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="44de6-256">As before, deploy from Visual Studio.</span></span>

<span data-ttu-id="44de6-257">Une fois l’application déployée :</span><span class="sxs-lookup"><span data-stu-id="44de6-257">After the application is deployed:</span></span>

* <span data-ttu-id="44de6-258">Observez la façon dont le son change au fur et à mesure que vous vous déplacez autour de P0LY.</span><span class="sxs-lookup"><span data-stu-id="44de6-258">Observe how the sound changes as you move around P0LY.</span></span>
* <span data-ttu-id="44de6-259">Dites *« Go Hide »* pour faire en sorte que P0LY se déplace vers un emplacement derrière vous.</span><span class="sxs-lookup"><span data-stu-id="44de6-259">Say *"Go Hide"* to make P0LY move to a location behind you.</span></span> <span data-ttu-id="44de6-260">Recherchez-le par le son.</span><span class="sxs-lookup"><span data-stu-id="44de6-260">Find it by the sound.</span></span>
* <span data-ttu-id="44de6-261">Pointez le regard de la base du hub d’énergie.</span><span class="sxs-lookup"><span data-stu-id="44de6-261">Gaze at the base of the Energy Hub.</span></span> <span data-ttu-id="44de6-262">Appuyez et faites glisser vers la gauche ou vers la droite pour faire pivoter l’hologramme et notez la façon dont le bruit de clic confirme le mouvement.</span><span class="sxs-lookup"><span data-stu-id="44de6-262">Tap and drag left or right to rotate the hologram and notice how the clicking sound confirms the gesture.</span></span>

<span data-ttu-id="44de6-263">Remarque : il existe un volet de texte qui s’étiquette avec vous.</span><span class="sxs-lookup"><span data-stu-id="44de6-263">Note: There is a text panel that will tag-along with you.</span></span> <span data-ttu-id="44de6-264">Elle contient les commandes vocales disponibles que vous pouvez utiliser tout au long de ce cours.</span><span class="sxs-lookup"><span data-stu-id="44de6-264">This will contain the available voice commands that you can use throughout this course.</span></span>

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a><span data-ttu-id="44de6-265">Chapitre 3-sons spatiaux et mappage spatial</span><span class="sxs-lookup"><span data-stu-id="44de6-265">Chapter 3 - Spatial Sound and Spatial Mapping</span></span>

### <a name="objectives"></a><span data-ttu-id="44de6-266">Objectifs</span><span class="sxs-lookup"><span data-stu-id="44de6-266">Objectives</span></span>

* <span data-ttu-id="44de6-267">Confirmez l’interaction entre les hologrammes et le monde réel à l’aide du son.</span><span class="sxs-lookup"><span data-stu-id="44de6-267">Confirm interaction between holograms and the real world using sound.</span></span>
* <span data-ttu-id="44de6-268">Occultait le son à l’aide du monde physique.</span><span class="sxs-lookup"><span data-stu-id="44de6-268">Occlude sound using the physical world.</span></span>

### <a name="part-1---physical-world-interaction"></a><span data-ttu-id="44de6-269">Partie 1-interaction du monde physique</span><span class="sxs-lookup"><span data-stu-id="44de6-269">Part 1 - Physical World Interaction</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="44de6-270">Concepts clés</span><span class="sxs-lookup"><span data-stu-id="44de6-270">Key Concepts</span></span>

* <span data-ttu-id="44de6-271">En général, les objets physiques font l’objet d’un bruit lorsqu’ils rencontrent une surface ou un autre objet.</span><span class="sxs-lookup"><span data-stu-id="44de6-271">Physical objects generally make a sound when encountering a surface or another object.</span></span>
* <span data-ttu-id="44de6-272">Les sons doivent être contextuels dans l’expérience.</span><span class="sxs-lookup"><span data-stu-id="44de6-272">Sounds should be context appropriate within the experience.</span></span>

<span data-ttu-id="44de6-273">Par exemple, la définition d’une tasse sur une table doit rendre un son plus calme que la suppression d’un Boulder sur un morceau de métal.</span><span class="sxs-lookup"><span data-stu-id="44de6-273">For example, setting a cup on a table should make a quieter sound than dropping a boulder on a piece of metal.</span></span>

#### <a name="instructions"></a><span data-ttu-id="44de6-274">Instructions</span><span class="sxs-lookup"><span data-stu-id="44de6-274">Instructions</span></span>

* <span data-ttu-id="44de6-275">Dans le volet **hiérarchie** , développez **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="44de6-275">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="44de6-276">Développez **EnergyHub**, sélectionnez **base**.</span><span class="sxs-lookup"><span data-stu-id="44de6-276">Expand **EnergyHub**, select **Base**.</span></span>
* <span data-ttu-id="44de6-277">Dans le panneau **inspecteur** , cliquez sur **Ajouter un composant** et ajoutez **TAP pour placer le son et l’action**.</span><span class="sxs-lookup"><span data-stu-id="44de6-277">In the **Inspector** panel, click **Add Component** and add **Tap To Place With Sound and Action**.</span></span>
* <span data-ttu-id="44de6-278">**Appuyez pour placer le son et l’action**:</span><span class="sxs-lookup"><span data-stu-id="44de6-278">In **Tap To Place With Sound and Action**:</span></span>
  * <span data-ttu-id="44de6-279">Cochez **Placer le parent sur TAP**.</span><span class="sxs-lookup"><span data-stu-id="44de6-279">Check **Place Parent On Tap**.</span></span>
  * <span data-ttu-id="44de6-280">Définissez **son** emplacement sur **place**.</span><span class="sxs-lookup"><span data-stu-id="44de6-280">Set **Placement Sound** to **Place**.</span></span>
  * <span data-ttu-id="44de6-281">Définissez le **son de collecte** sur **Pick**.</span><span class="sxs-lookup"><span data-stu-id="44de6-281">Set **Pickup Sound** to **Pickup**.</span></span>
  * <span data-ttu-id="44de6-282">Appuyez sur le signe + dans le coin inférieur droit, sous à la fois **action de collecte** et **action de placement**.</span><span class="sxs-lookup"><span data-stu-id="44de6-282">Press the + in the bottom right under both **On Pickup Action** and **On Placement Action**.</span></span> <span data-ttu-id="44de6-283">Faites glisser EnergyHub à partir de la scène dans les champs **aucun (objet)** .</span><span class="sxs-lookup"><span data-stu-id="44de6-283">Drag EnergyHub from the scene into the **None (Object)** fields.</span></span>
    * <span data-ttu-id="44de6-284">Sous **action de cueillette**, cliquez sur **aucune fonction**  ->  **EnergyHubBase**  ->  **ResetAnimation**.</span><span class="sxs-lookup"><span data-stu-id="44de6-284">Under **On Pickup Action**, click on **No Function** -> **EnergyHubBase** -> **ResetAnimation**.</span></span>
    * <span data-ttu-id="44de6-285">Sous **action de placement**, cliquez sur **no Function**  ->  **EnergyHubBase**  ->  **onselect**.</span><span class="sxs-lookup"><span data-stu-id="44de6-285">Under **On Placement Action**, click on **No Function** -> **EnergyHubBase** -> **OnSelect**.</span></span>

![Appuyez pour placer le son et l’action](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a><span data-ttu-id="44de6-287">Partie 2-occlusion sonore</span><span class="sxs-lookup"><span data-stu-id="44de6-287">Part 2 - Sound Occlusion</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="44de6-288">Concepts clés</span><span class="sxs-lookup"><span data-stu-id="44de6-288">Key Concepts</span></span>

* <span data-ttu-id="44de6-289">Un son, comme Light, peut être bloqués.</span><span class="sxs-lookup"><span data-stu-id="44de6-289">Sound, like light, can be occluded.</span></span>

<span data-ttu-id="44de6-290">Un exemple classique est un hall de concert.</span><span class="sxs-lookup"><span data-stu-id="44de6-290">A classic example is a concert hall.</span></span> <span data-ttu-id="44de6-291">Lorsqu’un écouteur se trouve en dehors du Hall et que la porte est fermée, la musique est atténuée.</span><span class="sxs-lookup"><span data-stu-id="44de6-291">When a listener is standing outside of the hall and the door is closed, the music sounds muffled.</span></span> <span data-ttu-id="44de6-292">Il y a également généralement une réduction du volume.</span><span class="sxs-lookup"><span data-stu-id="44de6-292">There is also typically a reduction in volume.</span></span> <span data-ttu-id="44de6-293">Lorsque la porte est ouverte, le spectre complet du son est audible sur le volume réel.</span><span class="sxs-lookup"><span data-stu-id="44de6-293">When the door is opened, the full spectrum of the sound is heard at the actual volume.</span></span> <span data-ttu-id="44de6-294">Les sons à fréquence élevée sont généralement absorbés plus que les fréquences basses.</span><span class="sxs-lookup"><span data-stu-id="44de6-294">High frequency sounds are generally absorbed more than low frequencies.</span></span>

#### <a name="instructions"></a><span data-ttu-id="44de6-295">Instructions</span><span class="sxs-lookup"><span data-stu-id="44de6-295">Instructions</span></span>

* <span data-ttu-id="44de6-296">Dans le volet **hiérarchie** , développez **HologramCollection** , puis sélectionnez **P0LY**.</span><span class="sxs-lookup"><span data-stu-id="44de6-296">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="44de6-297">Dans le panneau **inspecteur** , cliquez sur **Ajouter un composant** et ajouter un **émetteur audio**.</span><span class="sxs-lookup"><span data-stu-id="44de6-297">In the **Inspector** panel, click **Add Component** and add **Audio Emitter**.</span></span>

<span data-ttu-id="44de6-298">La classe d’émetteur audio fournit les fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="44de6-298">The Audio Emitter class provides the following features:</span></span>

* <span data-ttu-id="44de6-299">Restaure toutes les modifications apportées au volume du **audiosource**.</span><span class="sxs-lookup"><span data-stu-id="44de6-299">Restores any changes to the volume of the **AudioSource**.</span></span>
* <span data-ttu-id="44de6-300">Exécute un **physique. RaycastNonAlloc** à partir de la position de l’utilisateur dans la direction du **gameobject** auquel le **AudioEmitter** est attaché.</span><span class="sxs-lookup"><span data-stu-id="44de6-300">Performs a **Physics.RaycastNonAlloc** from the user's position in the direction of the **GameObject** to which the **AudioEmitter** is attached.</span></span>

<span data-ttu-id="44de6-301">La méthode RaycastNonAlloc est utilisée comme optimisation des performances pour limiter les allocations, ainsi que le nombre de résultats retournés.</span><span class="sxs-lookup"><span data-stu-id="44de6-301">The RaycastNonAlloc method is used as a performance optimization to limit allocations as well as the number of results returned.</span></span>

* <span data-ttu-id="44de6-302">Pour chaque **IAudioInfluencer** rencontré, appelle la méthode **ApplyEffect** .</span><span class="sxs-lookup"><span data-stu-id="44de6-302">For each **IAudioInfluencer** encountered, calls the **ApplyEffect** method.</span></span>
* <span data-ttu-id="44de6-303">Pour chaque **IAudioInfluencer** précédent qui n’est plus rencontré, appelez la méthode **RemoveEffect** .</span><span class="sxs-lookup"><span data-stu-id="44de6-303">For each previous **IAudioInfluencer** that is no longer encountered, call the **RemoveEffect** method.</span></span>

<span data-ttu-id="44de6-304">Notez que AudioEmitter met à jour les échelles de temps humaines, par opposition à des mises à jour par image.</span><span class="sxs-lookup"><span data-stu-id="44de6-304">Note that AudioEmitter updates on human time scales, as opposed to on a per frame basis.</span></span> <span data-ttu-id="44de6-305">Cela est dû au fait que les êtres humains ne se déplacent pas suffisamment rapidement pour que l’effet doive être mis à jour plus fréquemment que chaque trimestre ou moitié de seconde.</span><span class="sxs-lookup"><span data-stu-id="44de6-305">This is done because humans generally do not move fast enough for the effect to need to be updated more frequently than every quarter or half of a second.</span></span> <span data-ttu-id="44de6-306">Les hologrammes qui se téléportent rapidement d’un emplacement à un autre peuvent briser l’illusion.</span><span class="sxs-lookup"><span data-stu-id="44de6-306">Holograms that teleport rapidly from one location to another can break the illusion.</span></span>

* <span data-ttu-id="44de6-307">Dans le volet **hiérarchie** , développez **HologramCollection**.</span><span class="sxs-lookup"><span data-stu-id="44de6-307">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="44de6-308">Développez **EnergyHub** , puis sélectionnez **BlobOutside**.</span><span class="sxs-lookup"><span data-stu-id="44de6-308">Expand **EnergyHub** and select **BlobOutside**.</span></span>
* <span data-ttu-id="44de6-309">Dans le panneau **inspecteur** , cliquez sur **Ajouter un composant** et ajouter des **OCCLUDER audio**.</span><span class="sxs-lookup"><span data-stu-id="44de6-309">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="44de6-310">Dans **OCCLUDER audio**, définissez la **fréquence de coupure** sur **1500**.</span><span class="sxs-lookup"><span data-stu-id="44de6-310">In **Audio Occluder**, set **Cutoff Frequency** to **1500**.</span></span>

<span data-ttu-id="44de6-311">Ce paramètre limite les fréquences AudioSource à 1500 Hz et inférieures.</span><span class="sxs-lookup"><span data-stu-id="44de6-311">This setting limits the AudioSource frequencies to 1500 Hz and below.</span></span>

* <span data-ttu-id="44de6-312">Définissez **passage du volume** à **0,9**.</span><span class="sxs-lookup"><span data-stu-id="44de6-312">Set **Volume Pass Through** to **0.9**.</span></span>

<span data-ttu-id="44de6-313">Ce paramètre réduit le volume du AudioSource à 90% de son niveau actuel.</span><span class="sxs-lookup"><span data-stu-id="44de6-313">This setting reduces the volume of the AudioSource to 90% of it's current level.</span></span>

<span data-ttu-id="44de6-314">L’audio OCCLUDER implémente IAudioInfluencer pour :</span><span class="sxs-lookup"><span data-stu-id="44de6-314">Audio Occluder implements IAudioInfluencer to:</span></span>

* <span data-ttu-id="44de6-315">Appliquez un effet d’occlusion à l’aide d’un **AudioLowPassFilter** qui est attaché à **audiosource** Managed buy the **AudioEmitter**.</span><span class="sxs-lookup"><span data-stu-id="44de6-315">Apply an occlusion effect using an **AudioLowPassFilter** which gets attached to the **AudioSource** managed buy the **AudioEmitter**.</span></span>
* <span data-ttu-id="44de6-316">Applique l’atténuation du volume à AudioSource.</span><span class="sxs-lookup"><span data-stu-id="44de6-316">Applies volume attenuation to the AudioSource.</span></span>
* <span data-ttu-id="44de6-317">Désactive l’effet en définissant une fréquence de coupure neutre et en désactivant le filtre.</span><span class="sxs-lookup"><span data-stu-id="44de6-317">Disables the effect by setting a neutral cutoff frequency and disabling the filter.</span></span>

<span data-ttu-id="44de6-318">La fréquence utilisée est neutre est 22 kHz (22000 Hz).</span><span class="sxs-lookup"><span data-stu-id="44de6-318">The frequency used as neutral is 22 kHz (22000 Hz).</span></span> <span data-ttu-id="44de6-319">Cette fréquence a été choisie car elle se trouve au-dessus de la fréquence maximale nominale pouvant être entendue par l’oreille humaine, ce qui n’a aucun impact perceptible sur le son.</span><span class="sxs-lookup"><span data-stu-id="44de6-319">This frequency was chosen due to it being above the nominal maximum frequency that can be heard by the human ear, this making no discernable impact to the sound.</span></span>

* <span data-ttu-id="44de6-320">Dans le volet **hiérarchie** , sélectionnez **SpatialMapping**.</span><span class="sxs-lookup"><span data-stu-id="44de6-320">In the **Hierarchy** panel, select **SpatialMapping**.</span></span>
* <span data-ttu-id="44de6-321">Dans le panneau **inspecteur** , cliquez sur **Ajouter un composant** et ajouter des **OCCLUDER audio**.</span><span class="sxs-lookup"><span data-stu-id="44de6-321">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="44de6-322">Dans **OCCLUDER audio**, définissez la **fréquence de coupure** sur **750**.</span><span class="sxs-lookup"><span data-stu-id="44de6-322">In **Audio Occluder**, set **Cutoff Frequency** to **750**.</span></span>

<span data-ttu-id="44de6-323">Lorsque plusieurs Occluders se trouvent dans le chemin d’accès entre l’utilisateur et le **AudioEmitter**, la fréquence la plus faible est appliquée au filtre.</span><span class="sxs-lookup"><span data-stu-id="44de6-323">When multiple occluders are in the path between the user and the **AudioEmitter**, the lowest frequency is applied to the filter.</span></span>

* <span data-ttu-id="44de6-324">Définissez **passage du volume** à **0,75**.</span><span class="sxs-lookup"><span data-stu-id="44de6-324">Set **Volume Pass Through** to **0.75**.</span></span>

<span data-ttu-id="44de6-325">Lorsque plusieurs Occluders se trouvent dans le chemin d’accès entre l’utilisateur et le **AudioEmitter**, le transfert de volume est appliqué de façon additive.</span><span class="sxs-lookup"><span data-stu-id="44de6-325">When multiple occluders are in the path between the user and the **AudioEmitter**, the volume pass through is applied additively.</span></span>

* <span data-ttu-id="44de6-326">Dans le volet **hiérarchie** , sélectionnez **gestionnaires**.</span><span class="sxs-lookup"><span data-stu-id="44de6-326">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="44de6-327">Dans le panneau **inspecteur** , développez **Gestionnaire d’entrée vocal**.</span><span class="sxs-lookup"><span data-stu-id="44de6-327">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="44de6-328">Dans le **Gestionnaire d’entrée vocal**, développez **frais Go**.</span><span class="sxs-lookup"><span data-stu-id="44de6-328">In **Speech Input Handler**, expand **Go Charge**.</span></span>
* <span data-ttu-id="44de6-329">**Ne modifiez aucune fonction** en **polyactions. GoCharge**.</span><span class="sxs-lookup"><span data-stu-id="44de6-329">Change **No Function** to **PolyActions.GoCharge**.</span></span>

![Mot clé : facturation](images/gocharge.png)

* <span data-ttu-id="44de6-331">Développez-le **ici**.</span><span class="sxs-lookup"><span data-stu-id="44de6-331">Expand **Come Here**.</span></span>
* <span data-ttu-id="44de6-332">**Ne modifiez aucune fonction** en **polyactions. Comeback**.</span><span class="sxs-lookup"><span data-stu-id="44de6-332">Change **No Function** to **PolyActions.ComeBack**.</span></span>

![Mot clé : ici](images/comehere.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="44de6-334">Génération et déploiement</span><span class="sxs-lookup"><span data-stu-id="44de6-334">Build and Deploy</span></span>

* <span data-ttu-id="44de6-335">Comme précédemment, générez le projet dans Unity et déployez-le dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="44de6-335">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="44de6-336">Une fois l’application déployée :</span><span class="sxs-lookup"><span data-stu-id="44de6-336">After the application is deployed:</span></span>

* <span data-ttu-id="44de6-337">Dites *« Go Fact »* pour que P0LY entre dans le hub d’énergie.</span><span class="sxs-lookup"><span data-stu-id="44de6-337">Say *"Go Charge"* to have P0LY enter the Energy Hub.</span></span>

<span data-ttu-id="44de6-338">Notez la modification du son.</span><span class="sxs-lookup"><span data-stu-id="44de6-338">Note the change in the sound.</span></span> <span data-ttu-id="44de6-339">Le bruit doit être atténué et un peu plus calme.</span><span class="sxs-lookup"><span data-stu-id="44de6-339">It should sound muffled and a little quieter.</span></span> <span data-ttu-id="44de6-340">Si vous êtes en mesure de vous positionner avec un mur ou un autre objet entre vous et le hub d’énergie, vous remarquerez un Muffling supplémentaire du son en raison de l’occlusion par le monde réel.</span><span class="sxs-lookup"><span data-stu-id="44de6-340">If you are able to position yourself with a wall or other object between you and the Energy Hub, you should notice a further muffling of the sound due to the occlusion by the real world.</span></span>

* <span data-ttu-id="44de6-341">Dites *« venez ici »* pour que P0LY laisse le hub d’énergie et se positionne en face de vous.</span><span class="sxs-lookup"><span data-stu-id="44de6-341">Say *"Come Here"* to have P0LY leave the Energy Hub and position itself in front of you.</span></span>

<span data-ttu-id="44de6-342">Notez que l’occlusion sonore est supprimée une fois que P0LY a quitté le hub d’énergie.</span><span class="sxs-lookup"><span data-stu-id="44de6-342">Note that the sound occlusion is removed once P0LY exits the Energy Hub.</span></span> <span data-ttu-id="44de6-343">Si vous entendez encore des occlusions, P0LY peut être bloqués par le monde réel.</span><span class="sxs-lookup"><span data-stu-id="44de6-343">If you are still hearing occlusion, P0LY may be occluded by the real world.</span></span> <span data-ttu-id="44de6-344">Essayez de vous assurer que vous disposez d’une ligne de vue claire sur P0LY.</span><span class="sxs-lookup"><span data-stu-id="44de6-344">Try moving to ensure you have a clear line of sight to P0LY.</span></span>

### <a name="part-3---room-models"></a><span data-ttu-id="44de6-345">Partie 3-modèles Room</span><span class="sxs-lookup"><span data-stu-id="44de6-345">Part 3 - Room Models</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="44de6-346">Concepts clés</span><span class="sxs-lookup"><span data-stu-id="44de6-346">Key Concepts</span></span>

* <span data-ttu-id="44de6-347">La taille de l’espace fournit des files d’attente subliminal qui contribuent à la localisation du son.</span><span class="sxs-lookup"><span data-stu-id="44de6-347">The size of the space provides subliminal queues that contribute to sound localization.</span></span>
* <span data-ttu-id="44de6-348">Les modèles de salle sont définis par **audiosource**.</span><span class="sxs-lookup"><span data-stu-id="44de6-348">Room models are set per-**AudioSource**.</span></span>
* <span data-ttu-id="44de6-349">Le [MixedRealityToolkit pour Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) fournit du code pour définir le modèle de salle.</span><span class="sxs-lookup"><span data-stu-id="44de6-349">The [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides code for setting the room model.</span></span>
* <span data-ttu-id="44de6-350">Pour les expériences de réalité mixte, sélectionnez le modèle de salle qui correspond le mieux à l’espace de monde réel.</span><span class="sxs-lookup"><span data-stu-id="44de6-350">For Mixed Reality experiences, select the room model that best fits the real world space.</span></span>

<span data-ttu-id="44de6-351">Si vous créez un scénario de réalité virtuelle, sélectionnez le modèle de salle qui correspond le mieux à l’environnement virtuel.</span><span class="sxs-lookup"><span data-stu-id="44de6-351">If you are creating a Virtual Reality scenario, select the room model that best fits the virtual environment.</span></span>

## <a name="chapter-4---sound-design"></a><span data-ttu-id="44de6-352">Chapitre 4-conception du son</span><span class="sxs-lookup"><span data-stu-id="44de6-352">Chapter 4 - Sound Design</span></span>

### <a name="objectives"></a><span data-ttu-id="44de6-353">Objectifs</span><span class="sxs-lookup"><span data-stu-id="44de6-353">Objectives</span></span>

* <span data-ttu-id="44de6-354">Comprendre les considérations relatives à la conception d’un son efficace.</span><span class="sxs-lookup"><span data-stu-id="44de6-354">Understand considerations for effective sound design.</span></span>
* <span data-ttu-id="44de6-355">Apprenez à mélanger les techniques et les recommandations.</span><span class="sxs-lookup"><span data-stu-id="44de6-355">Learn mixing techniques and guidelines.</span></span>

### <a name="part-1---sound-and-experience-design"></a><span data-ttu-id="44de6-356">Partie 1 : conception du son et de l’expérience</span><span class="sxs-lookup"><span data-stu-id="44de6-356">Part 1 - Sound and Experience Design</span></span>

<span data-ttu-id="44de6-357">Cette section décrit les considérations et les recommandations relatives à la conception du son et de l’expérience.</span><span class="sxs-lookup"><span data-stu-id="44de6-357">This section discusses key sound and experience design considerations and guidelines.</span></span>

#### <a name="normalize-all-sounds"></a><span data-ttu-id="44de6-358">Normaliser tous les sons</span><span class="sxs-lookup"><span data-stu-id="44de6-358">Normalize all sounds</span></span>

<span data-ttu-id="44de6-359">Cela évite d’avoir à utiliser un code de cas particulier pour ajuster les niveaux de volume par son, ce qui peut prendre du temps et limiter la possibilité de mettre à jour facilement des fichiers audio.</span><span class="sxs-lookup"><span data-stu-id="44de6-359">This avoids the need for special case code to adjust volume levels per sound, which can be time consuming and limits the ability to easily update sound files.</span></span>

#### <a name="design-for-an-untethered-experience"></a><span data-ttu-id="44de6-360">Conception pour une expérience non attachée</span><span class="sxs-lookup"><span data-stu-id="44de6-360">Design for an untethered experience</span></span>

<span data-ttu-id="44de6-361">HoloLens est un ordinateur holographique entièrement contenu et non attaché.</span><span class="sxs-lookup"><span data-stu-id="44de6-361">HoloLens is a fully contained, untethered holographic computer.</span></span> <span data-ttu-id="44de6-362">Vos utilisateurs peuvent et utiliseront vos expériences pendant le déplacement.</span><span class="sxs-lookup"><span data-stu-id="44de6-362">Your users can and will use your experiences while moving.</span></span> <span data-ttu-id="44de6-363">Veillez à tester votre combinaison audio en vous.</span><span class="sxs-lookup"><span data-stu-id="44de6-363">Be sure to test your audio mix by walking around.</span></span>

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a><span data-ttu-id="44de6-364">Émettre du son à partir d’emplacements logiques sur vos hologrammes</span><span class="sxs-lookup"><span data-stu-id="44de6-364">Emit sound from logical locations on your holograms</span></span>

<span data-ttu-id="44de6-365">Dans le monde réel, un chien n’est pas à l’écorce de sa queue et la voix d’un homme ne provient pas de ses pieds.</span><span class="sxs-lookup"><span data-stu-id="44de6-365">In the real world, a dog does not bark from its tail and a human's voice does not come from his/her feet.</span></span> <span data-ttu-id="44de6-366">Évitez que vos sons émettent des parties inattendues de vos hologrammes.</span><span class="sxs-lookup"><span data-stu-id="44de6-366">Avoid having your sounds emit from unexpected portions of your holograms.</span></span>

<span data-ttu-id="44de6-367">Pour les petits hologrammes, il est raisonnable d’émettre un son à partir du centre de la géométrie.</span><span class="sxs-lookup"><span data-stu-id="44de6-367">For small holograms, it is reasonable to have sound emit from the center of the geometry.</span></span>

#### <a name="familiar-sounds-are-most-localizable"></a><span data-ttu-id="44de6-368">Les sons habituels sont plus localisables</span><span class="sxs-lookup"><span data-stu-id="44de6-368">Familiar sounds are most localizable</span></span>

<span data-ttu-id="44de6-369">La voix humaine et la musique sont très faciles à localiser.</span><span class="sxs-lookup"><span data-stu-id="44de6-369">The human voice and music are very easy to localize.</span></span> <span data-ttu-id="44de6-370">Si quelqu’un appelle votre nom, vous pouvez déterminer très précisément le sens de la voix et à quel moment.</span><span class="sxs-lookup"><span data-stu-id="44de6-370">If someone calls your name, you are able to very accurately determine from what direction the voice came and from how far away.</span></span> <span data-ttu-id="44de6-371">Les sons peu familiers sont plus difficiles à localiser.</span><span class="sxs-lookup"><span data-stu-id="44de6-371">Short, unfamiliar sounds are harder to localize.</span></span>

#### <a name="be-cognizant-of-user-expectations"></a><span data-ttu-id="44de6-372">Être Cognizant des attentes de l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="44de6-372">Be cognizant of user expectations</span></span>

<span data-ttu-id="44de6-373">L’expérience de vie joue un rôle dans notre capacité à identifier l’emplacement d’un son.</span><span class="sxs-lookup"><span data-stu-id="44de6-373">Life experience plays a part in our ability to identify the location of a sound.</span></span> <span data-ttu-id="44de6-374">C’est l’une des raisons pour lesquelles la voix humaine est particulièrement facile à localiser.</span><span class="sxs-lookup"><span data-stu-id="44de6-374">This is one reason why the human voice is particularly easy to localize.</span></span> <span data-ttu-id="44de6-375">Il est important de connaître les attentes de vos utilisateurs lors de la mise en place de vos sons.</span><span class="sxs-lookup"><span data-stu-id="44de6-375">It is important to be aware of your user's learned expectations when placing your sounds.</span></span>

<span data-ttu-id="44de6-376">Par exemple, quand quelqu’un entend un morceau d’oiseau, il recherche généralement des oiseaux au-dessus de la ligne de vue (volant ou dans une arborescence).</span><span class="sxs-lookup"><span data-stu-id="44de6-376">For example, when someone hears a bird song they generally look up, as birds tend to be above the line of sight (flying or in a tree).</span></span> <span data-ttu-id="44de6-377">Il n’est pas rare pour un utilisateur d’activer la direction correcte d’un son, mais de regarder dans une mauvaise direction verticale et de devenir confus ou frustré lorsqu’ils ne parviennent pas à trouver l’hologramme.</span><span class="sxs-lookup"><span data-stu-id="44de6-377">It is not uncommon for a user to turn in the correct direction of a sound, but look in the wrong vertical direction and become confused or frustrated when they are unable to find the hologram.</span></span>

#### <a name="avoid-hidden-emitters"></a><span data-ttu-id="44de6-378">Éviter les émetteurs masqués</span><span class="sxs-lookup"><span data-stu-id="44de6-378">Avoid hidden emitters</span></span>

<span data-ttu-id="44de6-379">Dans le monde réel, si nous entendons un son, nous pouvons généralement identifier l’objet qui émet le son.</span><span class="sxs-lookup"><span data-stu-id="44de6-379">In the real world, if we hear a sound, we can generally identify the object that is emitting the sound.</span></span> <span data-ttu-id="44de6-380">Cela doit également être vrai dans vos expériences.</span><span class="sxs-lookup"><span data-stu-id="44de6-380">This should also hold true in your experiences.</span></span> <span data-ttu-id="44de6-381">Il peut être très difficile pour les utilisateurs d’entendre un son, de savoir à quel endroit le son provient et de ne pas voir un objet.</span><span class="sxs-lookup"><span data-stu-id="44de6-381">It can be very disconcerting for users to hear a sound, know from where the sound originates and be unable to see an object.</span></span>

<span data-ttu-id="44de6-382">Il existe quelques exceptions à cette règle.</span><span class="sxs-lookup"><span data-stu-id="44de6-382">There are some exceptions to this guideline.</span></span> <span data-ttu-id="44de6-383">Par exemple, les sons ambiants tels que les crickets dans un champ n’ont pas besoin d’être visibles.</span><span class="sxs-lookup"><span data-stu-id="44de6-383">For example, ambient sounds such as crickets in a field need not be visible.</span></span> <span data-ttu-id="44de6-384">L’expérience de vie nous permet de vous familiariser avec la source de ces sons sans avoir à le voir.</span><span class="sxs-lookup"><span data-stu-id="44de6-384">Life experience gives us familiarity with the source of these sounds without the need to see it.</span></span>

### <a name="part-2---sound-mixing"></a><span data-ttu-id="44de6-385">Partie 2-mixage audio</span><span class="sxs-lookup"><span data-stu-id="44de6-385">Part 2 - Sound Mixing</span></span>

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a><span data-ttu-id="44de6-386">Ciblez votre combinaison pour 70% du volume sur le HoloLens</span><span class="sxs-lookup"><span data-stu-id="44de6-386">Target your mix for 70% volume on the HoloLens</span></span>

<span data-ttu-id="44de6-387">Les expériences de réalité mixte permettent de voir les hologrammes dans le monde réel.</span><span class="sxs-lookup"><span data-stu-id="44de6-387">Mixed Reality experiences allow holograms to be seen in the real world.</span></span> <span data-ttu-id="44de6-388">Ils doivent également permettre l’entendre des sons réels.</span><span class="sxs-lookup"><span data-stu-id="44de6-388">They should also allow real world sounds to be heard.</span></span> <span data-ttu-id="44de6-389">Une cible de volume de 70% permet à l’utilisateur d’entendre le monde autour de lui et du son de votre expérience.</span><span class="sxs-lookup"><span data-stu-id="44de6-389">A 70% volume target enables the user to hear the world around them along with the sound of your experience.</span></span>

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a><span data-ttu-id="44de6-390">HoloLens à 100% du volume doit être submergé de sons externes</span><span class="sxs-lookup"><span data-stu-id="44de6-390">HoloLens at 100% volume should drown out external sounds</span></span>

<span data-ttu-id="44de6-391">Un niveau de volume de 100% est similaire à une expérience de réalité virtuelle.</span><span class="sxs-lookup"><span data-stu-id="44de6-391">A volume level of 100% is akin to a Virtual Reality experience.</span></span> <span data-ttu-id="44de6-392">Visuellement, l’utilisateur est transporté vers un autre monde.</span><span class="sxs-lookup"><span data-stu-id="44de6-392">Visually, the user is transported to a different world.</span></span> <span data-ttu-id="44de6-393">Il en va de même de la même façon audible.</span><span class="sxs-lookup"><span data-stu-id="44de6-393">The same should hold true audibly.</span></span>

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a><span data-ttu-id="44de6-394">Utiliser Unity AudioMixer pour ajuster les catégories de sons</span><span class="sxs-lookup"><span data-stu-id="44de6-394">Use the Unity AudioMixer to adjust categories of sounds</span></span>

<span data-ttu-id="44de6-395">Lors de la conception de votre combinaison, il est souvent utile de créer des catégories de son et d’augmenter ou de réduire leur volume en tant qu’unité.</span><span class="sxs-lookup"><span data-stu-id="44de6-395">When designing your mix, it is often helpful to create sound categories and have the ability to increase or decrease their volume as a unit.</span></span> <span data-ttu-id="44de6-396">Cela permet de conserver les niveaux relatifs de chaque son tout en permettant de modifier rapidement et facilement la combinaison globale.</span><span class="sxs-lookup"><span data-stu-id="44de6-396">This retains the relative levels of each sound while enabling quick and easy changes to the overall mix.</span></span> <span data-ttu-id="44de6-397">Les catégories courantes incluent ; effets sonores, ambiance, voix et musique en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="44de6-397">Common categories include; sound effects, ambience, voice overs and background music.</span></span>

#### <a name="mix-sounds-based-on-the-users-gaze"></a><span data-ttu-id="44de6-398">Mélanger des sons en fonction du point de regard de l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="44de6-398">Mix sounds based on the user's gaze</span></span>

<span data-ttu-id="44de6-399">Il peut souvent être utile de modifier la combinaison de sons dans votre expérience en fonction de l’endroit où un utilisateur est (ou n’est pas) à l’origine de la recherche.</span><span class="sxs-lookup"><span data-stu-id="44de6-399">It can often be useful to change the sound mix in your experience based on where a user is (or is not) looking.</span></span> <span data-ttu-id="44de6-400">Une utilisation courante de cette technique consiste à réduire le volume des hologrammes qui se trouvent en dehors du cadre holographique pour permettre à l’utilisateur de se concentrer plus facilement sur les informations qu’il contient.</span><span class="sxs-lookup"><span data-stu-id="44de6-400">One common use for this technique are to reduce the volume level for holograms that are outside of the Holographic Frame to make it easier for the user to focus on the information in front of them.</span></span> <span data-ttu-id="44de6-401">Une autre utilisation consiste à augmenter le volume d’un son pour attirer l’attention de l’utilisateur sur un événement important.</span><span class="sxs-lookup"><span data-stu-id="44de6-401">Another use is to increase the volume of a sound to draw the user's attention to an important event.</span></span>

#### <a name="building-your-mix"></a><span data-ttu-id="44de6-402">Conception de votre combinaison</span><span class="sxs-lookup"><span data-stu-id="44de6-402">Building your mix</span></span>

<span data-ttu-id="44de6-403">Lors de la création de votre combinaison, il est recommandé de commencer par l’audio d’arrière-plan de votre expérience et d’ajouter des couches en fonction de leur importance.</span><span class="sxs-lookup"><span data-stu-id="44de6-403">When building your mix, it is recommended to start with your experience's background audio and add layers based on importance.</span></span> <span data-ttu-id="44de6-404">Souvent, cela entraîne une couche plus forte que la précédente.</span><span class="sxs-lookup"><span data-stu-id="44de6-404">Often, this results in each layer being louder than the previous.</span></span>

<span data-ttu-id="44de6-405">En imaginant votre combinaison comme un entonnoir inversé, avec les moins importants (et généralement les plus calmes) en bas, il est recommandé de structurer votre combinaison comme dans le diagramme suivant.</span><span class="sxs-lookup"><span data-stu-id="44de6-405">Imagining your mix as an inverted funnel, with the least important (and generally quietest sounds) at the bottom, it is recommended to structure your mix similar to the following diagram.</span></span>

![Structure de combinaison de sons](images/soundlevels.png)

<span data-ttu-id="44de6-407">Les fonctionnalités vocales sont un scénario intéressant.</span><span class="sxs-lookup"><span data-stu-id="44de6-407">Voice overs are an interesting scenario.</span></span> <span data-ttu-id="44de6-408">En fonction de l’expérience que vous créez, vous souhaiterez peut-être avoir un son stéréo (non localisé) ou pour spatialer votre voix.</span><span class="sxs-lookup"><span data-stu-id="44de6-408">Based on the experience you are creating you may wish to have a stereo (not localized) sound or to spatialize your voice overs.</span></span> <span data-ttu-id="44de6-409">Deux expériences Microsoft publiées illustrent des exemples excellents de chaque scénario.</span><span class="sxs-lookup"><span data-stu-id="44de6-409">Two Microsoft published experiences illustrate excellent examples of each scenario.</span></span>

<span data-ttu-id="44de6-410">[HoloTour](https://www.microsoft.com/store/p/holotour/9nblggh5pj87) utilise une voix stéréo.</span><span class="sxs-lookup"><span data-stu-id="44de6-410">[HoloTour](https://www.microsoft.com/store/p/holotour/9nblggh5pj87) uses a stereo voice over.</span></span> <span data-ttu-id="44de6-411">Lorsque le narrateur décrit l’emplacement affiché, le son est cohérent et ne varie pas en fonction de la position de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="44de6-411">When the narrator is describing the location being viewed, the sound is consistent and does not vary based on the user's position.</span></span> <span data-ttu-id="44de6-412">Cela permet au narrateur de décrire la scène sans sortir des sons spatiaux de l’environnement.</span><span class="sxs-lookup"><span data-stu-id="44de6-412">This enables the narrator to describe the scene without taking away from the spatialized sounds of the environment.</span></span>

<span data-ttu-id="44de6-413">Les [fragments](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilisent une voix spatiale sous la forme d’un détective.</span><span class="sxs-lookup"><span data-stu-id="44de6-413">[Fragments](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizes a spatialized voice over in the form of a detective.</span></span> <span data-ttu-id="44de6-414">La voix du détective est utilisée pour attirer l’attention de l’utilisateur sur un indice important comme si un humain réel était dans la pièce.</span><span class="sxs-lookup"><span data-stu-id="44de6-414">The detective's voice is used to help bring the user's attention to an important clue as if an actual human was in the room.</span></span> <span data-ttu-id="44de6-415">Cela permet un sens encore plus important de l’immersion dans l’expérience de résolution du mystère.</span><span class="sxs-lookup"><span data-stu-id="44de6-415">This enables an even greater sense of immersion into the experience of solving the mystery.</span></span>

### <a name="part-3--performance"></a><span data-ttu-id="44de6-416">Partie 3-performances</span><span class="sxs-lookup"><span data-stu-id="44de6-416">Part 3 -Performance</span></span>

#### <a name="cpu-usage"></a><span data-ttu-id="44de6-417">Utilisation de l’UC</span><span class="sxs-lookup"><span data-stu-id="44de6-417">CPU usage</span></span>

<span data-ttu-id="44de6-418">Lorsque vous utilisez un son spatial, 10-12 émetteurs consomment environ 12% du processeur.</span><span class="sxs-lookup"><span data-stu-id="44de6-418">When using Spatial Sound, 10 - 12 emitters will consume approximately 12% of the CPU.</span></span>

#### <a name="stream-long-audio-files"></a><span data-ttu-id="44de6-419">Diffuser des fichiers audio longs</span><span class="sxs-lookup"><span data-stu-id="44de6-419">Stream long audio files</span></span>

<span data-ttu-id="44de6-420">Les données audio peuvent être volumineuses, en particulier aux taux d’échantillonnage courants (44,1 et 48 kHz).</span><span class="sxs-lookup"><span data-stu-id="44de6-420">Audio data can be large, especially at common sample rates (44.1 and 48 kHz).</span></span> <span data-ttu-id="44de6-421">Une règle générale est que les fichiers audio d’une durée supérieure à 5-10 secondes doivent être diffusés en continu pour réduire l’utilisation de la mémoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="44de6-421">A general rule is that audio files longer than 5 - 10 seconds should be streamed to reduce application memory usage.</span></span>

<span data-ttu-id="44de6-422">Dans Unity, vous pouvez marquer un fichier audio pour la diffusion en continu dans les paramètres d’importation du fichier.</span><span class="sxs-lookup"><span data-stu-id="44de6-422">In Unity, you can mark an audio file for streaming in the file's import settings.</span></span>

![Paramètres d’importation audio](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a><span data-ttu-id="44de6-424">Chapitre 5-effets spéciaux</span><span class="sxs-lookup"><span data-stu-id="44de6-424">Chapter 5 - Special Effects</span></span>

### <a name="objectives"></a><span data-ttu-id="44de6-425">Objectifs</span><span class="sxs-lookup"><span data-stu-id="44de6-425">Objectives</span></span>

* <span data-ttu-id="44de6-426">Ajoutez une profondeur à « Magic Windows ».</span><span class="sxs-lookup"><span data-stu-id="44de6-426">Add depth to "Magic Windows".</span></span>
* <span data-ttu-id="44de6-427">Mettez l’utilisateur dans le monde virtuel.</span><span class="sxs-lookup"><span data-stu-id="44de6-427">Bring the user into the virtual world.</span></span>

### <a name="magic-windows"></a><span data-ttu-id="44de6-428">Magic Windows</span><span class="sxs-lookup"><span data-stu-id="44de6-428">Magic Windows</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="44de6-429">Concepts clés</span><span class="sxs-lookup"><span data-stu-id="44de6-429">Key Concepts</span></span>

* <span data-ttu-id="44de6-430">La création d’affichages dans un monde masqué, est visuellement attrayante.</span><span class="sxs-lookup"><span data-stu-id="44de6-430">Creating views into a hidden world, is visually compelling.</span></span>
* <span data-ttu-id="44de6-431">Améliorez le réalisme en ajoutant des effets audio quand un hologramme ou l’utilisateur est proche du monde masqué.</span><span class="sxs-lookup"><span data-stu-id="44de6-431">Enhance realism by adding audio effects when a hologram or the user is near the hidden world.</span></span>

#### <a name="instructions"></a><span data-ttu-id="44de6-432">Instructions</span><span class="sxs-lookup"><span data-stu-id="44de6-432">Instructions</span></span>

* <span data-ttu-id="44de6-433">Dans le volet **hiérarchie** , développez **HologramCollection** , puis sélectionnez **subworld**.</span><span class="sxs-lookup"><span data-stu-id="44de6-433">In the **Hierarchy** panel, expand **HologramCollection** and select **Underworld**.</span></span>
* <span data-ttu-id="44de6-434">Développez le sous- **monde** et sélectionnez **VoiceSource**.</span><span class="sxs-lookup"><span data-stu-id="44de6-434">Expand **Underworld** and select **VoiceSource**.</span></span>
* <span data-ttu-id="44de6-435">Dans le panneau **inspecteur** , cliquez sur **Ajouter un composant** et ajouter un **effet utilisateur vocal**.</span><span class="sxs-lookup"><span data-stu-id="44de6-435">In the **Inspector** panel, click **Add Component** and add **User Voice Effect**.</span></span>

<span data-ttu-id="44de6-436">Un composant **audiosource** sera ajouté à **VoiceSource**.</span><span class="sxs-lookup"><span data-stu-id="44de6-436">An **AudioSource** component will be added to **VoiceSource**.</span></span>

* <span data-ttu-id="44de6-437">Dans **audiosource**, définissez **sortie** sur **UserVoice (Mixer)**.</span><span class="sxs-lookup"><span data-stu-id="44de6-437">In **AudioSource**, set **Output** to **UserVoice (Mixer)**.</span></span>
* <span data-ttu-id="44de6-438">Cochez la case **spatialiser** .</span><span class="sxs-lookup"><span data-stu-id="44de6-438">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="44de6-439">Faites glisser le curseur de **lissage spatial** jusqu’à la forme **3D**, ou entrez **1** dans la zone d’édition.</span><span class="sxs-lookup"><span data-stu-id="44de6-439">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>
* <span data-ttu-id="44de6-440">Développez **paramètres audio 3D**.</span><span class="sxs-lookup"><span data-stu-id="44de6-440">Expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="44de6-441">Affectez au **niveau Doppler** la valeur **0**.</span><span class="sxs-lookup"><span data-stu-id="44de6-441">Set **Doppler Level** to **0**.</span></span>
* <span data-ttu-id="44de6-442">Dans l' **effet utilisateur vocal**, définissez l' **objet parent** sur le sous- **monde** à partir de la scène.</span><span class="sxs-lookup"><span data-stu-id="44de6-442">In **User Voice Effect**, set **Parent Object** to the **Underworld** from the scene.</span></span>
* <span data-ttu-id="44de6-443">Définissez **distance maximale** sur **1**.</span><span class="sxs-lookup"><span data-stu-id="44de6-443">Set **Max Distance** to **1**.</span></span>

<span data-ttu-id="44de6-444">La définition de la **distance maximale** indique à l' **utilisateur** qu’il doit être l’objet parent avant l’activation de l’effet.</span><span class="sxs-lookup"><span data-stu-id="44de6-444">Setting **Max Distance** tells **User Voice Effect** how close the user must be to the parent object before the effect is enabled.</span></span>

* <span data-ttu-id="44de6-445">Dans **effet vocal** de l’utilisateur, développez **paramètres de chœur**.</span><span class="sxs-lookup"><span data-stu-id="44de6-445">In **User Voice Effect**, expand **Chorus Parameters**.</span></span>
* <span data-ttu-id="44de6-446">Définissez **profondeur** sur **0,1**.</span><span class="sxs-lookup"><span data-stu-id="44de6-446">Set **Depth** to **0.1**.</span></span>
* <span data-ttu-id="44de6-447">Définissez **Tap 1 volume**, **Appuyez sur 2 volume** , puis **sur 3 volumes** jusqu’à **0,8**.</span><span class="sxs-lookup"><span data-stu-id="44de6-447">Set **Tap 1 Volume**, **Tap 2 Volume** and **Tap 3 Volume** to **0.8**.</span></span>
* <span data-ttu-id="44de6-448">Définissez le **volume de son original** sur **0,5**.</span><span class="sxs-lookup"><span data-stu-id="44de6-448">Set **Original Sound Volume** to **0.5**.</span></span>

<span data-ttu-id="44de6-449">Les paramètres précédents configurent les paramètres du **AudioChorusFilter** Unity utilisé pour ajouter la richesse à la voix de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="44de6-449">The previous settings configure the parameters of the Unity **AudioChorusFilter** used to add richness to the user's voice.</span></span>

* <span data-ttu-id="44de6-450">Dans l' **effet utilisateur vocal**, développez **paramètres Echo**.</span><span class="sxs-lookup"><span data-stu-id="44de6-450">In **User Voice Effect**, expand **Echo Parameters**.</span></span>
* <span data-ttu-id="44de6-451">Définir le **délai** sur **300**</span><span class="sxs-lookup"><span data-stu-id="44de6-451">Set **Delay** to **300**</span></span>
* <span data-ttu-id="44de6-452">Définissez le **taux d’atténuation** sur **0,2**.</span><span class="sxs-lookup"><span data-stu-id="44de6-452">Set **Decay Ratio** to **0.2**.</span></span>
* <span data-ttu-id="44de6-453">Définissez le **volume de son original** sur **0**.</span><span class="sxs-lookup"><span data-stu-id="44de6-453">Set **Original Sound Volume** to **0**.</span></span>

<span data-ttu-id="44de6-454">Les paramètres précédents configurent les paramètres du **AudioEchoFilter** Unity utilisé pour faire écho à la voix de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="44de6-454">The previous settings configure the parameters of the Unity **AudioEchoFilter** used to cause the user's voice to echo.</span></span>

<span data-ttu-id="44de6-455">Le script de l’effet utilisateur vocal est chargé des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="44de6-455">The User Voice Effect script is responsible for:</span></span>

* <span data-ttu-id="44de6-456">Mesure de la distance entre l’utilisateur et le **gameobject** auquel le script est attaché.</span><span class="sxs-lookup"><span data-stu-id="44de6-456">Measuring the distance between the user and the **GameObject** to which the script is attached.</span></span>
* <span data-ttu-id="44de6-457">Déterminer si l’utilisateur est confronté au **gameobject**.</span><span class="sxs-lookup"><span data-stu-id="44de6-457">Determining whether or not the user is facing the **GameObject**.</span></span>

<span data-ttu-id="44de6-458">L’utilisateur doit être orienté GameObject, quelle que soit la distance, pour que l’effet soit activé.</span><span class="sxs-lookup"><span data-stu-id="44de6-458">The user must be facing the GameObject, regardless of distance, for the effect to be enabled.</span></span>

* <span data-ttu-id="44de6-459">Application et configuration d’un **AudioChorusFilter** et d’un **AudioEchoFilter** à **audiosource**.</span><span class="sxs-lookup"><span data-stu-id="44de6-459">Applying and configuring an **AudioChorusFilter** and an **AudioEchoFilter** to the **AudioSource**.</span></span>
* <span data-ttu-id="44de6-460">La désactivation de l’effet en désactivant les filtres.</span><span class="sxs-lookup"><span data-stu-id="44de6-460">Disabling the effect by disabling the filters.</span></span>

<span data-ttu-id="44de6-461">L’effet User Voice utilise le composant sélecteur de flux MIC, à partir du [MixedRealityToolkit pour Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), pour sélectionner le flux vocal de haute qualité et l’acheminer dans le système audio Unity.</span><span class="sxs-lookup"><span data-stu-id="44de6-461">User Voice Effect uses the Mic Stream Selector component, from the [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), to select the high quality voice stream and route it into Unity's audio system.</span></span>

* <span data-ttu-id="44de6-462">Dans le volet **hiérarchie** , sélectionnez **gestionnaires**.</span><span class="sxs-lookup"><span data-stu-id="44de6-462">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="44de6-463">Dans le panneau **inspecteur** , développez **Gestionnaire d’entrée vocal**.</span><span class="sxs-lookup"><span data-stu-id="44de6-463">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="44de6-464">Dans le **Gestionnaire d’entrée vocal**, développez afficher le sous- **monde**.</span><span class="sxs-lookup"><span data-stu-id="44de6-464">In **Speech Input Handler**, expand **Show Underworld**.</span></span>
* <span data-ttu-id="44de6-465">**Ne modifiez aucune fonction** en **UnderworldBase. OnEnable**.</span><span class="sxs-lookup"><span data-stu-id="44de6-465">Change **No Function** to **UnderworldBase.OnEnable**.</span></span>

![Mot clé : afficher le sous-monde](images/showunderworld.png)

* <span data-ttu-id="44de6-467">Développez masquer le sous- **monde**.</span><span class="sxs-lookup"><span data-stu-id="44de6-467">Expand **Hide Underworld**.</span></span>
* <span data-ttu-id="44de6-468">**Ne modifiez aucune fonction** en **UnderworldBase. OnDisable**.</span><span class="sxs-lookup"><span data-stu-id="44de6-468">Change **No Function** to **UnderworldBase.OnDisable**.</span></span>

![Mot clé : masquer le sous-monde](images/hideunderworld.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="44de6-470">Génération et déploiement</span><span class="sxs-lookup"><span data-stu-id="44de6-470">Build and Deploy</span></span>

* <span data-ttu-id="44de6-471">Comme précédemment, générez le projet dans Unity et déployez-le dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="44de6-471">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="44de6-472">Une fois l’application déployée :</span><span class="sxs-lookup"><span data-stu-id="44de6-472">After the application is deployed:</span></span>

* <span data-ttu-id="44de6-473">Face à une surface (mur, plancher, table) et dites *« afficher le monde »*.</span><span class="sxs-lookup"><span data-stu-id="44de6-473">Face a surface (wall, floor, table) and say *"Show Underworld"*.</span></span>

<span data-ttu-id="44de6-474">Le sous-monde s’affiche et tous les autres hologrammes sont masqués.</span><span class="sxs-lookup"><span data-stu-id="44de6-474">The underworld will be shown and all other holograms will be hidden.</span></span> <span data-ttu-id="44de6-475">Si vous ne voyez pas le sous-monde, assurez-vous que vous êtes face à une surface réaliste.</span><span class="sxs-lookup"><span data-stu-id="44de6-475">If you do not see the underworld, ensure that you are facing a real-world surface.</span></span>

* <span data-ttu-id="44de6-476">Approche à l’intérieur d’un compteur de l’hologramme de la planète et commencer à parler.</span><span class="sxs-lookup"><span data-stu-id="44de6-476">Approach within 1 meter of the underworld hologram and start talking.</span></span>

<span data-ttu-id="44de6-477">Des effets audio sont désormais appliqués à votre voix.</span><span class="sxs-lookup"><span data-stu-id="44de6-477">There are now audio effects applied to your voice!</span></span>

* <span data-ttu-id="44de6-478">Quittez le sous-monde et notez la façon dont l’effet n’est plus appliqué.</span><span class="sxs-lookup"><span data-stu-id="44de6-478">Turn away from the underworld and notice how the effect is no longer applied.</span></span>
* <span data-ttu-id="44de6-479">Dites *« masquer le monde »* pour masquer le sous-monde.</span><span class="sxs-lookup"><span data-stu-id="44de6-479">Say *"Hide Underworld"* to hide the underworld.</span></span>

<span data-ttu-id="44de6-480">Le sous-monde est masqué et les hologrammes précédemment masqués réapparaissent.</span><span class="sxs-lookup"><span data-stu-id="44de6-480">The underworld will be hidden and the previously hidden holograms will reappear.</span></span>

## <a name="the-end"></a><span data-ttu-id="44de6-481">La fin</span><span class="sxs-lookup"><span data-stu-id="44de6-481">The End</span></span>

<span data-ttu-id="44de6-482">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="44de6-482">Congratulations!</span></span> <span data-ttu-id="44de6-483">Vous avez maintenant terminé le **son spatial 220 : spatial**.</span><span class="sxs-lookup"><span data-stu-id="44de6-483">You have now completed **MR Spatial 220: Spatial sound**.</span></span>

<span data-ttu-id="44de6-484">Écoutez l’univers et donnez vie à vos expériences !</span><span class="sxs-lookup"><span data-stu-id="44de6-484">Listen to the world and bring your experiences to life with sound!</span></span>