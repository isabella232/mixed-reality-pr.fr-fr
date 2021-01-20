---
title: Didacticiels audio spatiaux-2. Spatialisation des sons d’interaction avec les boutons
description: Ajoutez un bouton à votre projet et spatialez les sons d’interaction du bouton.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: réalité mixte, Unity, tutorial, hololens2, audio spatial, MRTK, boîte à outils de réalité mixte, UWP, Windows 10, HRTF, fonction de transfert liée aux têtes, réverbération, Microsoft Spatializer, prefabs, courbe de volume
ms.openlocfilehash: e4b2ed99f56fea82b1c72e4fce5205c14e1d3533
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2021
ms.locfileid: "98578486"
---
# <a name="2-spatializing-button-interaction-sounds"></a><span data-ttu-id="33c50-105">2. Spatialisation des sons d’interaction avec les boutons</span><span class="sxs-lookup"><span data-stu-id="33c50-105">2. Spatializing button interaction sounds</span></span>

## <a name="overview"></a><span data-ttu-id="33c50-106">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="33c50-106">Overview</span></span>

<span data-ttu-id="33c50-107">Dans ce didacticiel, vous allez apprendre à spatialiser les sons d’interaction du bouton et à utiliser un clip audio pour tester l’interaction de bouton spatiale.</span><span class="sxs-lookup"><span data-stu-id="33c50-107">In this tutorial, you will learn how to spatialize the button interaction sounds and also learn how to use an audio clip to test spatialized button interaction.</span></span>  

## <a name="objectives"></a><span data-ttu-id="33c50-108">Objectifs</span><span class="sxs-lookup"><span data-stu-id="33c50-108">Objectives</span></span>

* <span data-ttu-id="33c50-109">Ajouter et spatialiser le bouton de clic</span><span class="sxs-lookup"><span data-stu-id="33c50-109">Add and Spatialize the button click sounds</span></span>

## <a name="add-a-button"></a><span data-ttu-id="33c50-110">Ajouter un bouton</span><span class="sxs-lookup"><span data-stu-id="33c50-110">Add a button</span></span>

<span data-ttu-id="33c50-111">Pour ajouter le bouton Prefab, dans la fenêtre **projet** , sélectionnez **ressources** , puis tapez « PressableButtonHoloLens2 » dans la barre de recherche.</span><span class="sxs-lookup"><span data-stu-id="33c50-111">To add the Button prefab, in the **Project** window, select **Assets** and type "PressableButtonHoloLens2" in the search bar.</span></span>

![Bouton Prefab dans les ressources](images/spatial-audio/spatial-audio-02-section1-step1-1.png)

<span data-ttu-id="33c50-113">Le bouton Prefab est l’entrée représentée par une icône bleue.</span><span class="sxs-lookup"><span data-stu-id="33c50-113">The button prefab is the entry represented by a blue icon.</span></span> <span data-ttu-id="33c50-114">Cliquez et faites glisser le Prefab **PressableButtonHoloLens2** dans la hiérarchie.</span><span class="sxs-lookup"><span data-stu-id="33c50-114">Click and drag the **PressableButtonHoloLens2** prefab into the Hierarchy.</span></span> <span data-ttu-id="33c50-115">L’objet **PressableButtonHoloLens2** étant toujours sélectionné, dans la fenêtre de l’inspecteur, configurez le composant **transformer** comme suit :</span><span class="sxs-lookup"><span data-stu-id="33c50-115">With the **PressableButtonHoloLens2** object still selected, in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="33c50-116">**Position**: X = 0, Y =-0,4, Z = 2</span><span class="sxs-lookup"><span data-stu-id="33c50-116">**Position**: X = 0, Y = -0.4, Z = 2</span></span>
* <span data-ttu-id="33c50-117">**Rotation** : X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="33c50-117">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="33c50-118">**Scale** : X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="33c50-118">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Transformation de bouton](images/spatial-audio/spatial-audio-02-section1-step1-2.png)

<span data-ttu-id="33c50-120">Pour vous concentrer sur les objets de la scène, vous pouvez double-cliquer sur l’objet **PressableButtonHoloLens2** , puis effectuer un zoom légèrement en arrière :</span><span class="sxs-lookup"><span data-stu-id="33c50-120">To focus in on the objects in the scene, you can double-click on the **PressableButtonHoloLens2** object, and then zoom slightly in again:</span></span>

## <a name="spatialize-button-feedback"></a><span data-ttu-id="33c50-121">Commentaires sur le bouton spatial</span><span class="sxs-lookup"><span data-stu-id="33c50-121">Spatialize button feedback</span></span>

<span data-ttu-id="33c50-122">Dans cette étape, vous allez spatialiser les commentaires audio pour le bouton.</span><span class="sxs-lookup"><span data-stu-id="33c50-122">In this step, you'll spatialize the audio feedback for the button.</span></span> <span data-ttu-id="33c50-123">Pour obtenir des suggestions de conception associées, consultez [conception de son spatial](../../../design/spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="33c50-123">For related design suggestions, see [spatial sound design](../../../design/spatial-sound-design.md).</span></span>

<span data-ttu-id="33c50-124">Dans la fenêtre **mixage audio** , vous allez définir des destinations appelées **groupes de mixage**, pour la lecture audio à partir de composants **sources audio** .</span><span class="sxs-lookup"><span data-stu-id="33c50-124">In the **Audio Mixer** window you will define destinations called **Mixer Groups**, for audio playback from **Audio Source** components.</span></span>

<span data-ttu-id="33c50-125">Pour ouvrir la fenêtre **mixage audio** , dans le menu Unity, **Sélectionnez** mixer audio audio fenêtre  >    >  **mixer**: ouvrir la fenêtre de ![ mixage audio](images/spatial-audio/spatial-audio-02-section2-step1-1.png)</span><span class="sxs-lookup"><span data-stu-id="33c50-125">To open the **Audio Mixer** window, In the Unity menu, select **Window** > **Audio** > **Audio Mixer**: ![Open Audio Mixer Window](images/spatial-audio/spatial-audio-02-section2-step1-1.png)</span></span>

 <span data-ttu-id="33c50-126">Créez un **mélangeur** en cliquant sur le signe « + » en regard de **mixages** , puis entrez un nom approprié pour le mélangeur, par exemple, le _mixer audio spatial_.</span><span class="sxs-lookup"><span data-stu-id="33c50-126">Create a **Mixer** by clicking the '+' next to **Mixers** and enter a suitable name to the Mixer for example, _Spatial Audio Mixer_.</span></span> <span data-ttu-id="33c50-127">Le nouveau mélangeur inclura un **groupe** par défaut nommé **maître**.</span><span class="sxs-lookup"><span data-stu-id="33c50-127">The new mixer will include a default **Group** called **Master**.</span></span>

![Panneau de mixage avec le premier mélangeur](images/spatial-audio/spatial-audio-02-section2-step1-2.png)

> [!NOTE]
> <span data-ttu-id="33c50-129">Tant que la réverbération n’est pas activée dans le [cinquième chapitre : l’utilisation de la réverbération pour ajouter de la distance à l’audio spatial](unity-spatial-audio-ch5.md), le compteur de volume du mélangeur n’affiche pas l’activité des sons joués par Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="33c50-129">Until reverb is enabled in [5th Chapter: Using reverb to add distance to spatial audio](unity-spatial-audio-ch5.md), the mixer's volume meter doesn't show activity for sounds played through the Microsoft Spatializer</span></span>

<span data-ttu-id="33c50-130">Dans la fenêtre hiérarchie, sélectionnez le **PressableButtonHoloLens2** puis, dans la fenêtre de l’inspecteur, recherchez le composant **source audio** et configurez le composant audio source comme suit :</span><span class="sxs-lookup"><span data-stu-id="33c50-130">In the Hierarchy window, select the **PressableButtonHoloLens2** then in the Inspector window find the **Audio Source** component and Configure the Audio Source component as follows:</span></span>

1. <span data-ttu-id="33c50-131">Pour la propriété **sortie** , cliquez sur le sélecteur, puis choisissez le **mélangeur** que vous avez créé.</span><span class="sxs-lookup"><span data-stu-id="33c50-131">For the **Output** property, click the selector and choose the **Mixer** that you created.</span></span>
2. <span data-ttu-id="33c50-132">Cochez la case **spatialiser** .</span><span class="sxs-lookup"><span data-stu-id="33c50-132">Check the **Spatialize** checkbox.</span></span>
3. <span data-ttu-id="33c50-133">Déplacez le curseur de **lissage spatial** vers 3D (1).</span><span class="sxs-lookup"><span data-stu-id="33c50-133">Move the **Spatial Blend** slider to 3D (1).</span></span>

![Source audio du bouton](images/spatial-audio/spatial-audio-02-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="33c50-135">Si vous déplacez le **lissage spatial** sur 1 (3d) sans activer la case à cocher **spatialiser** , Unity utilise son Spatializer panoramique, au lieu du **Spatializer Microsoft** avec HRTFs.</span><span class="sxs-lookup"><span data-stu-id="33c50-135">If you move **Spatial Blend** to 1 (3D) without checking the **Spatialize** checkbox, Unity will use its panning spatializer, instead of the **Microsoft Spatializer** with HRTFs.</span></span>

## <a name="adjust-the-volume-curve"></a><span data-ttu-id="33c50-136">Ajuster la courbe du volume</span><span class="sxs-lookup"><span data-stu-id="33c50-136">Adjust the Volume curve</span></span>

<span data-ttu-id="33c50-137">Par défaut, Unity atténue les sons spatiaux au fur et à mesure qu’ils s’éloignent de l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="33c50-137">By default, Unity will attenuate spatialized sounds as they get farther from the listener.</span></span> <span data-ttu-id="33c50-138">Lorsque cette atténuation est appliquée à des sons d’interaction, l’interface peut devenir plus difficile à utiliser.</span><span class="sxs-lookup"><span data-stu-id="33c50-138">When this attenuation is applied to interaction feedback sounds, the interface can become more difficult to use.</span></span>

<span data-ttu-id="33c50-139">Pour désactiver cette atténuation, vous devez ajuster la courbe de **volume** dans le composant **source audio** .</span><span class="sxs-lookup"><span data-stu-id="33c50-139">To disable this attenuation, you need to adjust the **Volume** curve In the **Audio Source** component.</span></span>

<span data-ttu-id="33c50-140">Dans la fenêtre hiérarchie, sélectionnez le **PressableButtonHoloLens2** puis, dans la fenêtre de l’inspecteur, accédez à **source audio**  >  **paramètres audio 3D** et configurez comme suit :</span><span class="sxs-lookup"><span data-stu-id="33c50-140">In the Hierarchy window, select the **PressableButtonHoloLens2** then in the Inspector window navigate to  **Audio Source** > **3D Sound Settings** and Configure as follows:</span></span>

1. <span data-ttu-id="33c50-141">Définissez la propriété **volume Rolloff** sur Linear Rolloff</span><span class="sxs-lookup"><span data-stu-id="33c50-141">Set the **Volume Rolloff** property to Linear Rolloff</span></span>
2. <span data-ttu-id="33c50-142">Faites glisser le point de terminaison sur la courbe de **volume** (la courbe rouge) de « 0 » sur l’axe y jusqu’à « 1 »</span><span class="sxs-lookup"><span data-stu-id="33c50-142">Drag the endpoint on the **Volume** curve (the red curve) from '0' on the y axis up to '1'</span></span>
3. <span data-ttu-id="33c50-143">Pour ajuster la forme de la courbe de **volume** à plat, faites glisser le contrôle de forme de courbe blanche pour qu’il soit parallèle à l’axe X.</span><span class="sxs-lookup"><span data-stu-id="33c50-143">To adjust the shape of the **Volume** curve to be flat, drag the white curve shape control to be parallel to the X axis</span></span>

![Paramètres audio de bouton 3D](images/spatial-audio/spatial-audio-02-section3-step1-1.png)

## <a name="testing-the-spatialize-audio"></a><span data-ttu-id="33c50-145">Test du son spatial</span><span class="sxs-lookup"><span data-stu-id="33c50-145">Testing the spatialize audio</span></span>

<span data-ttu-id="33c50-146">Pour tester le son spatial dans l’éditeur Unity, vous devez ajouter un clip audio dans le composant **source audio** avec l’option de **boucle** archivée sur l’objet **PressableButtonHoloLens2** .</span><span class="sxs-lookup"><span data-stu-id="33c50-146">To test the spatialize audio in the unity editor you have to add an audio clip in the **Audio Source** component with **Loop** option checked in on **PressableButtonHoloLens2** object.</span></span>

<span data-ttu-id="33c50-147">En mode lecture, déplacez l’objet **PressableButtonHoloLens2** de gauche à droite et comparez avec et sans audio spatial activé sur votre station de travail.</span><span class="sxs-lookup"><span data-stu-id="33c50-147">In the play mode move the **PressableButtonHoloLens2** object from left to right and compare with and without spatial audio enabled on your workstation.</span></span> <span data-ttu-id="33c50-148">Vous pouvez également modifier les paramètres de la source audio pour les tests en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="33c50-148">You can also change the Audio Source settings for testing by:</span></span>

* <span data-ttu-id="33c50-149">Déplacement de la propriété de **lissage spatial** entre 0-1 (2D non spatial et 3D spatialic)</span><span class="sxs-lookup"><span data-stu-id="33c50-149">Moving the **Spatial Blend** property between 0 - 1 (2D non-spatialized and 3D spatialized sound)</span></span>
* <span data-ttu-id="33c50-150">Vérification et désactivation de la propriété **spatial**</span><span class="sxs-lookup"><span data-stu-id="33c50-150">Checking and unchecking the **Spatialize** property</span></span>

<span data-ttu-id="33c50-151">Essayez l’application sur HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="33c50-151">Try out the app on HoloLens 2.</span></span> <span data-ttu-id="33c50-152">Dans l’application, vous pouvez cliquer sur le bouton et entendre les sons d’interaction du bouton spatial.</span><span class="sxs-lookup"><span data-stu-id="33c50-152">In the app, you can click the button and hear the spatialized button interaction sounds.</span></span>

> [!TIP]
> <span data-ttu-id="33c50-153">Pour vous rappeler comment générer et déployer votre projet Unity sur HoloLens 2, vous pouvez vous référer aux instructions de [Génération de votre application sur votre HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="33c50-153">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="33c50-154">Félicitations</span><span class="sxs-lookup"><span data-stu-id="33c50-154">Congratulations</span></span>

<span data-ttu-id="33c50-155">Dans ce didacticiel, vous avez appris à spatialiser les sons d’interaction du bouton et à utiliser un clip audio pour tester l’interaction des boutons spatiales.</span><span class="sxs-lookup"><span data-stu-id="33c50-155">In this tutorial you have learnt to spatialize the button interaction sounds and to use an audio clip to test spatialized button interaction.</span></span> <span data-ttu-id="33c50-156">Dans le didacticiel suivant, vous allez apprendre à spatialiser l’audio à partir d’une source vidéo.</span><span class="sxs-lookup"><span data-stu-id="33c50-156">In the next tutorial you will learn how to spatialize audio from an video source.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="33c50-157">Didacticiel suivant : 3. Universion audio à partir d’une vidéo</span><span class="sxs-lookup"><span data-stu-id="33c50-157">Next Tutorial: 3. Spatializing audio from a video</span></span>](unity-spatial-audio-ch3.md)
