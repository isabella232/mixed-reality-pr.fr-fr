---
title: Didacticiels audio spatiaux-3. Spatialisation du contenu audio d’une vidéo
description: Importez un élément multimédia vidéo dans votre projet Unity et spatialez l’audio de la vidéo.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: réalité mixte, Unity, tutorial, hololens2, audio spatial, MRTK, boîte à outils de réalité mixte, UWP, Windows 10, HRTF, fonction de transfert liée aux têtes, réverbération, Microsoft Spatializer, importation de vidéos, lecteur vidéo
ms.openlocfilehash: 6474da522e650d23349a21c3deeac00222b8ce93
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2021
ms.locfileid: "98578571"
---
# <a name="3-spatializing-audio-from-a-video"></a><span data-ttu-id="8b990-105">3. Spatialisation du contenu audio d’une vidéo</span><span class="sxs-lookup"><span data-stu-id="8b990-105">3. Spatializing audio from a video</span></span>

## <a name="overview"></a><span data-ttu-id="8b990-106">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="8b990-106">Overview</span></span>

<span data-ttu-id="8b990-107">Dans ce didacticiel, vous allez apprendre à spatialiser l’audio à partir d’une source vidéo et à le tester dans l’éditeur Unity et dans HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8b990-107">In this tutorial, you will learn how to spatialize audio from an video source and test this in the unity editor and HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="8b990-108">Objectifs</span><span class="sxs-lookup"><span data-stu-id="8b990-108">Objectives</span></span>

* <span data-ttu-id="8b990-109">Importer une vidéo et ajouter un lecteur vidéo</span><span class="sxs-lookup"><span data-stu-id="8b990-109">Import a video and add a Video Player</span></span>
* <span data-ttu-id="8b990-110">Lire la vidéo sur un Quadrangle</span><span class="sxs-lookup"><span data-stu-id="8b990-110">Play the video onto a quadrangle</span></span>
* <span data-ttu-id="8b990-111">Acheminer l’audio de la vidéo vers le Quadrangle et spatialiser l’audio</span><span class="sxs-lookup"><span data-stu-id="8b990-111">Route audio from the video to the quadrangle, and spatialize the audio</span></span>

## <a name="import-a-video-and-add-a-video-player-to-the-scene"></a><span data-ttu-id="8b990-112">Importer une vidéo et ajouter un lecteur vidéo à la scène</span><span class="sxs-lookup"><span data-stu-id="8b990-112">Import a video and add a Video Player to the Scene</span></span>

<span data-ttu-id="8b990-113">Pour ce didacticiel, vous pouvez utiliser [cette vidéo](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) à partir de l’exemple de projet de son spatial.</span><span class="sxs-lookup"><span data-stu-id="8b990-113">For this tutorial use You can use [this video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) from the spatial audio sample project.</span></span>

<span data-ttu-id="8b990-114">Pour importer une vidéo dans le projet Unity.</span><span class="sxs-lookup"><span data-stu-id="8b990-114">To import Video into the unity project.</span></span> <span data-ttu-id="8b990-115">dans le menu Unity, sélectionnez **Asset**  >  **Importer un nouvel élément multimédia importer un** 
 élément multimédia ![](images/spatial-audio/spatial-audio-03-section1-step1-1.png)</span><span class="sxs-lookup"><span data-stu-id="8b990-115">in the Unity menu select **Asset** > **Import New Asset**
![Importing Asset](images/spatial-audio/spatial-audio-03-section1-step1-1.png)</span></span>

<span data-ttu-id="8b990-116">Dans la fenêtre **Importer une nouvelle ressource..** ., sélectionnez le fichier **Microsoft HoloLens-spatial Sound-PTPvx7mDon4** que vous avez téléchargé, puis cliquez sur le bouton **ouvrir** pour importer la ressource dans le projet :</span><span class="sxs-lookup"><span data-stu-id="8b990-116">In the **Import New Asset...** window, select the **Microsoft HoloLens - Spatial Sound-PTPvx7mDon4** file you downloaded and click the **Open** button to import the asset into the project:</span></span>

![Sélection de l’élément multimédia](images/spatial-audio/spatial-audio-03-section1-step1-2.png)

<span data-ttu-id="8b990-118">L’ajustement des paramètres de qualité sur le clip vidéo peut garantir une lecture douce sur HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8b990-118">Adjusting the quality settings on the video clip can ensure smooth playback on HoloLens 2.</span></span> <span data-ttu-id="8b990-119">Sélectionnez le fichier vidéo dans la fenêtre **projet** et dans la fenêtre Inspecteur du fichier vidéo, **Remplacez** les paramètres pour les **applications du Windows Store** et :</span><span class="sxs-lookup"><span data-stu-id="8b990-119">Select the video file in the **Project** window and in the Inspector window of the video file, **override** the settings for **Windows Store Apps**, and:</span></span>

* <span data-ttu-id="8b990-120">Activer le **transcodage**</span><span class="sxs-lookup"><span data-stu-id="8b990-120">Enable **Transcode**</span></span>
* <span data-ttu-id="8b990-121">Définir le **codec** sur H264 –</span><span class="sxs-lookup"><span data-stu-id="8b990-121">Set **Codec** to H264</span></span>
* <span data-ttu-id="8b990-122">Définir le **Mode débit** sur faible</span><span class="sxs-lookup"><span data-stu-id="8b990-122">Set **Bitrate Mode** to Low</span></span>
* <span data-ttu-id="8b990-123">Définir la **qualité spatiale** sur une qualité spatiale moyenne</span><span class="sxs-lookup"><span data-stu-id="8b990-123">Set **Spatial Quality** to Medium Spatial Quality</span></span>

<span data-ttu-id="8b990-124">Après ces ajustements, cliquez sur appliquer pour modifier le paramètre de qualité du clip vidéo.</span><span class="sxs-lookup"><span data-stu-id="8b990-124">After these adjustments, click on Apply to change the quality setting on the video clip.</span></span>

![Modification des propriétés de la vidéo](images/spatial-audio/spatial-audio-03-section1-step1-3.png)

<span data-ttu-id="8b990-126">Cliquez avec le bouton droit sur la hiérarchie, **puis sélectionnez**  >  **lecteur** vidéo vidéo pour ajouter le composant lecteur vidéo.</span><span class="sxs-lookup"><span data-stu-id="8b990-126">Right click on the Hierarchy, Select **Video** > **Video Player** to add Video player component.</span></span>

![Ajouter un lecteur vidéo](images/spatial-audio/spatial-audio-03-section1-step1-4.png)

## <a name="play-video-onto-a-quadrangle"></a><span data-ttu-id="8b990-128">Lire une vidéo sur un Quadrangle</span><span class="sxs-lookup"><span data-stu-id="8b990-128">Play video onto a quadrangle</span></span>

<span data-ttu-id="8b990-129">L’objet **lecteur vidéo** a besoin d’un objet de jeu texturé pour afficher la vidéo.</span><span class="sxs-lookup"><span data-stu-id="8b990-129">The **Video Player** object needs a textured game object to render the video.</span></span>

<span data-ttu-id="8b990-130">Cliquez avec le bouton droit sur la hiérarchie, sélectionnez **objet 3D**  >  **quadruple** pour créer un Quad et configurer son composant **transformer** comme suit :</span><span class="sxs-lookup"><span data-stu-id="8b990-130">Right click the Hierarchy , Select **3D Object** > **Quad** to create a quad and configure its **Transform** component as follows:</span></span>

* <span data-ttu-id="8b990-131">**Position**: X = 0, Y = 0, Z = 2</span><span class="sxs-lookup"><span data-stu-id="8b990-131">**Position**: X = 0, Y = 0, Z = 2</span></span>
* <span data-ttu-id="8b990-132">**Rotation** : X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="8b990-132">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="8b990-133">**Échelle**: X = 1,28, Y = 0,72, Z = 1</span><span class="sxs-lookup"><span data-stu-id="8b990-133">**Scale**: X = 1.28, Y = 0.72, Z = 1</span></span>

![Ajouter un quadruple](images/spatial-audio/spatial-audio-03-section2-step1-1.png)

<span data-ttu-id="8b990-135">À présent, vous devez texturer le **Quad** avec la vidéo, dans la fenêtre du **projet** , cliquer avec le bouton droit et choisir **créer**  >  une **texture** de rendu pour créer un composant de texture de rendu, entrer un nom approprié pour la texture de rendu, par exemple _texture audio spatiale_:</span><span class="sxs-lookup"><span data-stu-id="8b990-135">Now you need to texture the **Quad** with the video, In the **Project** window, right-click and choose **Create** > **Render Texture** to create a Render Texture component, enter a suitable name to the Render Texture for example, _Spatial Audio Texture_:</span></span>

![Créer une texture de rendu](images/spatial-audio/spatial-audio-03-section2-step1-2.png)

<span data-ttu-id="8b990-137">Sélectionnez la **texture de rendu** et, dans la fenêtre de l’inspecteur, définissez la propriété **Size** pour qu’elle corresponde à la résolution native de la vidéo de 1280 x 720.</span><span class="sxs-lookup"><span data-stu-id="8b990-137">Select the **Render Texture** and in the Inspector window set the **Size** property to match the video's native resolution of 1280x720.</span></span> <span data-ttu-id="8b990-138">Ensuite, pour garantir de bonnes performances de rendu sur HoloLens 2, affectez à la propriété de la **mémoire tampon de profondeur** une **profondeur d’au moins 16 bits**.</span><span class="sxs-lookup"><span data-stu-id="8b990-138">Then, to ensure good rendering performance on HoloLens 2, set the **Depth Buffer** property to **At least 16 bits depth**.</span></span>

![Propriétés de texture de rendu](images/spatial-audio/spatial-audio-03-section2-step1-3.png)

<span data-ttu-id="8b990-140">Ensuite, utilisez la texture **audio spatiale** de rendu créée comme texture pour le **Quad**:</span><span class="sxs-lookup"><span data-stu-id="8b990-140">Next, use the created Render Texture **Spatial Audio Texture** as the texture for the **Quad**:</span></span>

1. <span data-ttu-id="8b990-141">Faites glisser la **texture audio spatiale** de la fenêtre **projet** sur le **quadruple** dans la hiérarchie pour ajouter la texture de rendu au quadruple</span><span class="sxs-lookup"><span data-stu-id="8b990-141">Drag the **Spatial Audio Texture** from the **Project** window onto the **Quad** in the Hierarchy to add the Render Texture to the Quad</span></span>
2. <span data-ttu-id="8b990-142">Pour garantir de bonnes performances sur HoloLens 2, sélectionnez Quad dans la hiérarchie, puis dans la fenêtre Inspector du nuanceur, sélectionnez le nuanceur standard de la **réalité mixte**  >   .</span><span class="sxs-lookup"><span data-stu-id="8b990-142">To ensure good performance on HoloLens 2, select Quad in the Hierarchy and in the Inspector window for shader select the **Mixed Reality Toolkit** > **Standard** Shader.</span></span>

![Propriétés de texture Quad](images/spatial-audio/spatial-audio-03-section2-step1-4.png)

<span data-ttu-id="8b990-144">Pour définir le **lecteur vidéo** et **afficher la texture** pour lire le clip vidéo, sélectionnez le **lecteur vidéo** dans la **hiérarchie** et dans la fenêtre **inspecteur** .</span><span class="sxs-lookup"><span data-stu-id="8b990-144">To set **Video Player** and **Render Texture** to play the video clip, select the **Video Player** in the **Hierarchy** and in the **Inspector** window,</span></span>

* <span data-ttu-id="8b990-145">Définissez la propriété **clip vidéo** sur le fichier vidéo téléchargé « Microsoft HoloLens-spatial Sound-PTPvx7mDon4 »</span><span class="sxs-lookup"><span data-stu-id="8b990-145">Set the **Video Clip** property to the downloaded video file 'Microsoft HoloLens - Spatial Sound-PTPvx7mDon4'</span></span>
* <span data-ttu-id="8b990-146">Cochez la case **boucle**</span><span class="sxs-lookup"><span data-stu-id="8b990-146">Check the **Loop** checkbox</span></span>
* <span data-ttu-id="8b990-147">Définir la **texture cible** sur la nouvelle texture **audio spatiale** de rendu</span><span class="sxs-lookup"><span data-stu-id="8b990-147">Set **Target Texture** to your new render texture **Spatial Audio Texture**</span></span>

![Propriétés du lecteur vidéo](images/spatial-audio/spatial-audio-03-section2-step1-5.png)

## <a name="spatialize-the-audio-from-the-video"></a><span data-ttu-id="8b990-149">Spatialiser l’audio à partir de la vidéo</span><span class="sxs-lookup"><span data-stu-id="8b990-149">Spatialize the audio from the video</span></span>

<span data-ttu-id="8b990-150">Dans la fenêtre hiérarchie, sélectionnez objet **quadruple** , puis dans la fenêtre de l’inspecteur, utilisez le bouton **Ajouter un composant** pour ajouter une **source audio** dans laquelle vous allez acheminer l’audio à partir de la vidéo.</span><span class="sxs-lookup"><span data-stu-id="8b990-150">In the Hierarchy window, select **Quad** object, then in the Inspector window, use the **Add Component** button to add **Audio Source** to which you'll route the audio from the video.</span></span>

<span data-ttu-id="8b990-151">Dans la **source audio**:</span><span class="sxs-lookup"><span data-stu-id="8b990-151">In the **Audio Source**:</span></span>

* <span data-ttu-id="8b990-152">Définir la **sortie** dans le **mélangeur audio spatial**</span><span class="sxs-lookup"><span data-stu-id="8b990-152">Set **Output** to the **Spatial Audio Mixer**</span></span>
* <span data-ttu-id="8b990-153">Vérifier la zone **spatiale**</span><span class="sxs-lookup"><span data-stu-id="8b990-153">Check the **Spatialize** box</span></span>
* <span data-ttu-id="8b990-154">Déplacez le curseur de **lissage spatial** sur 1 (3d)</span><span class="sxs-lookup"><span data-stu-id="8b990-154">Move the **Spatial Blend** slider to 1 (3D)</span></span>

![Inspecteur de source audio quadruple](images/spatial-audio/spatial-audio-03-section3-step1-1.png)

<span data-ttu-id="8b990-156">Pour configurer le lecteur vidéo de façon à acheminer son audio vers la **source audio**, sélectionnez le **lecteur vidéo** dans la fenêtre hiérarchie et, dans l’objet lecteur vidéo de l’inspecteur, effectuez les modifications suivantes.</span><span class="sxs-lookup"><span data-stu-id="8b990-156">To set the Video Player to route its audio to the **Audio Source**, select the **Video Player** In the Hierarchy window, and in Video Player object in the Inspector do the following changes.</span></span>

* <span data-ttu-id="8b990-157">Définir le **mode de sortie audio** sur la **source audio**</span><span class="sxs-lookup"><span data-stu-id="8b990-157">Set the **Audio Output Mode** to **Audio Source**</span></span>
* <span data-ttu-id="8b990-158">Définir la propriété de la **source audio** sur le **quadruple**</span><span class="sxs-lookup"><span data-stu-id="8b990-158">Set the **Audio Source** property to the **Quad**</span></span>

![Source du jeu de lecteurs vidéo](images/spatial-audio/spatial-audio-03-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="8b990-160">Pour vous rappeler comment générer et déployer votre projet Unity sur HoloLens 2, vous pouvez vous référer aux instructions de [Génération de votre application sur votre HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="8b990-160">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="8b990-161">Félicitations</span><span class="sxs-lookup"><span data-stu-id="8b990-161">Congratulations</span></span>

<span data-ttu-id="8b990-162">Dans ce didacticiel, vous avez appris à spatialiser l’audio à partir d’une source vidéo essayer votre application sur un HoloLens 2 ou dans l’éditeur Unity.</span><span class="sxs-lookup"><span data-stu-id="8b990-162">In this tutorial, you have learned how to spatialize audio from an video source Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="8b990-163">Vous verrez et entendez la vidéo, et l’audio de la vidéo est spatial.</span><span class="sxs-lookup"><span data-stu-id="8b990-163">You'll see and hear the video, and the audio from the video is spatialized.</span></span>

<span data-ttu-id="8b990-164">Dans le didacticiel suivant, vous allez apprendre à activer et désactiver des Spatialization au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="8b990-164">In the next tutorial you will learn how to Enable and disable spatialization at run time</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8b990-165">Didacticiel suivant : 4. activation et désactivation de Spatialization au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="8b990-165">Next Tutorial: 4. Enabling and disabling spatialization at run time</span></span>](unity-spatial-audio-ch4.md)
