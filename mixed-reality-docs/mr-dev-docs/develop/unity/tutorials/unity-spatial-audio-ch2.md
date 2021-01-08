---
title: Spatialisation des sons d’interaction avec les boutons
description: Apprenez à ajouter un bouton et à spatialiser les sons d’interaction du bouton dans une application de réalité mixte.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: réalité mixte, Unity, tutorial, hololens2, audio spatial, MRTK, boîte à outils de réalité mixte, UWP, Windows 10, HRTF, fonction de transfert liée aux têtes, réverbération, Microsoft Spatializer, prefabs, courbe de volume
ms.openlocfilehash: 1f54ba8cab55ba375a6b1499796761ae02b03a02
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007359"
---
# <a name="spatializing-button-interaction-sounds"></a><span data-ttu-id="64c83-104">Spatialisation des sons d’interaction avec les boutons</span><span class="sxs-lookup"><span data-stu-id="64c83-104">Spatializing button interaction sounds</span></span>

## <a name="objectives"></a><span data-ttu-id="64c83-105">Objectifs</span><span class="sxs-lookup"><span data-stu-id="64c83-105">Objectives</span></span>

<span data-ttu-id="64c83-106">Dans ce deuxième chapitre du module audio spatial des didacticiels HoloLens 2, vous allez :</span><span class="sxs-lookup"><span data-stu-id="64c83-106">In this second chapter of the spatial audio module of the HoloLens 2 tutorials, you'll:</span></span>
* <span data-ttu-id="64c83-107">Ajouter un bouton</span><span class="sxs-lookup"><span data-stu-id="64c83-107">Add a button</span></span>
* <span data-ttu-id="64c83-108">Spatialiser le clic sur le bouton</span><span class="sxs-lookup"><span data-stu-id="64c83-108">Spatialize the button click sounds</span></span>

## <a name="add-a-button"></a><span data-ttu-id="64c83-109">Ajouter un bouton</span><span class="sxs-lookup"><span data-stu-id="64c83-109">Add a button</span></span>

<span data-ttu-id="64c83-110">Dans le volet **projet** , sélectionnez **ressources** et tapez « PressableButtonHoloLens2 » dans la barre de recherche :</span><span class="sxs-lookup"><span data-stu-id="64c83-110">In the **Project** pane, select **Assets** and type "PressableButtonHoloLens2" in the search bar:</span></span>

![Bouton Prefab dans les ressources](images/spatial-audio/button-prefab-in-assets.png)

<span data-ttu-id="64c83-112">Le bouton Prefab est l’entrée représentée par une icône bleue, plutôt qu’une icône blanche.</span><span class="sxs-lookup"><span data-stu-id="64c83-112">The button prefab is the entry represented by a blue icon, rather than a white icon.</span></span> <span data-ttu-id="64c83-113">Faites glisser le Prefab nommé **PressableButtonHoloLens2** dans le volet **hiérarchie** .</span><span class="sxs-lookup"><span data-stu-id="64c83-113">Drag the prefab named **PressableButtonHoloLens2** into the **Hierarchy** pane.</span></span> <span data-ttu-id="64c83-114">Dans le volet de l' **inspecteur** de votre nouveau bouton, définissez la propriété **position** sur (0,-0,4, 2) afin qu’elle s’affiche devant l’utilisateur au démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="64c83-114">In the **Inspector** pane for your new button, set the **Position** property to (0, -0.4, 2) so that it will appear in front of the user when the application starts.</span></span> <span data-ttu-id="64c83-115">Le composant **transformer** du bouton se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="64c83-115">The **Transform** component of the button will look like this:</span></span>

![Transformation de bouton](images/spatial-audio/button-transform.png)

## <a name="spatialize-button-feedback"></a><span data-ttu-id="64c83-117">Commentaires sur le bouton spatial</span><span class="sxs-lookup"><span data-stu-id="64c83-117">Spatialize button feedback</span></span>

<span data-ttu-id="64c83-118">Dans cette étape, vous allez spatialiser les commentaires audio pour le bouton.</span><span class="sxs-lookup"><span data-stu-id="64c83-118">In this step, you'll spatialize the audio feedback for the button.</span></span> <span data-ttu-id="64c83-119">Pour obtenir des suggestions de conception associées, consultez [conception de son spatial](../../../design/spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="64c83-119">For related design suggestions, see [spatial sound design](../../../design/spatial-sound-design.md).</span></span> 

<span data-ttu-id="64c83-120">Le volet **mixage audio** vous permet de définir des destinations, appelées **groupes de mixage**, pour la lecture audio à partir de composants **sources audio** .</span><span class="sxs-lookup"><span data-stu-id="64c83-120">The **Audio Mixer** pane is where you'll define destinations, called **Mixer Groups**, for audio playback from **Audio Source** components.</span></span> 
* <span data-ttu-id="64c83-121">Ouvrez le volet **mixage audio** à partir de la barre de menus à l’aide de la **fenêtre > audio-> mixage audio**</span><span class="sxs-lookup"><span data-stu-id="64c83-121">Open the **Audio Mixer** pane from the menu bar using **Window -> Audio -> Audio Mixer**</span></span>
* <span data-ttu-id="64c83-122">Créez un **mélangeur** en cliquant sur le signe « + » en regard de **mixages**.</span><span class="sxs-lookup"><span data-stu-id="64c83-122">Create a **Mixer** by clicking the '+' next to **Mixers**.</span></span> <span data-ttu-id="64c83-123">Le nouveau mélangeur inclura un **groupe** par défaut nommé **maître**.</span><span class="sxs-lookup"><span data-stu-id="64c83-123">The new mixer will include a default **Group** called **Master**.</span></span>

<span data-ttu-id="64c83-124">Le volet de **mixage** ressemble à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="64c83-124">Your **Mixer** pane will now look like this:</span></span>

![Panneau de mixage avec le premier mélangeur](images/spatial-audio/mixer-panel-with-first-mixer.png)

> [!NOTE]
> <span data-ttu-id="64c83-126">Jusqu’à ce que la réverbération soit activée dans le [Chapitre 5](unity-spatial-audio-ch5.md), le compteur de volume du mélangeur n’affiche pas l’activité des sons joués par Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="64c83-126">Until reverb is enabled in [Chapter 5](unity-spatial-audio-ch5.md), the mixer's volume meter doesn't show activity for sounds played through the Microsoft Spatializer</span></span>

<span data-ttu-id="64c83-127">Dans le volet **hiérarchie** , cliquez sur **PressableButtonHoloLens2** .</span><span class="sxs-lookup"><span data-stu-id="64c83-127">Click the **PressableButtonHoloLens2** in the **Hierarchy** pane.</span></span> <span data-ttu-id="64c83-128">Dans le volet **inspecteur** :</span><span class="sxs-lookup"><span data-stu-id="64c83-128">In the **Inspector** pane:</span></span>
1. <span data-ttu-id="64c83-129">Rechercher le composant **source audio**</span><span class="sxs-lookup"><span data-stu-id="64c83-129">Find the **Audio Source** component</span></span>
2. <span data-ttu-id="64c83-130">Pour la propriété **sortie** , cliquez sur le sélecteur et choisissez votre mélangeur</span><span class="sxs-lookup"><span data-stu-id="64c83-130">For the **Output** property, click the selector and choose your mixer</span></span>
3. <span data-ttu-id="64c83-131">Cochez la case **spatialiser**</span><span class="sxs-lookup"><span data-stu-id="64c83-131">Check the **Spatialize** checkbox</span></span>
4. <span data-ttu-id="64c83-132">Déplacez le curseur de **lissage spatial** vers 3D (1).</span><span class="sxs-lookup"><span data-stu-id="64c83-132">Move the **Spatial Blend** slider to 3D (1).</span></span>

> [!NOTE]
> <span data-ttu-id="64c83-133">Dans les versions de Unity antérieures à 2019, la case à cocher « spatialiser » se trouve en bas du volet de l' **inspecteur** pour la **source audio**.</span><span class="sxs-lookup"><span data-stu-id="64c83-133">In versions of Unity prior to 2019, the 'Spatialize' checkbox is at the bottom of the **Inspector** pane for the **Audio Source**.</span></span>

<span data-ttu-id="64c83-134">Une fois ces modifications effectuées, le composant **source audio** de votre **PressableButtonHoloLens2** se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="64c83-134">After these changes, the **Audio Source** component of your **PressableButtonHoloLens2** will look like this:</span></span>

![Source audio du bouton](images/spatial-audio/button-audio-source.png)

> [!NOTE]
> <span data-ttu-id="64c83-136">Si vous déplacez le **lissage spatial** sur 1 (3d) sans activer la case à cocher **spatialiser** , Unity utilise son Spatializer panoramique, au lieu du **Spatializer Microsoft** avec HRTFs.</span><span class="sxs-lookup"><span data-stu-id="64c83-136">If you move **Spatial Blend** to 1 (3D) without checking the **Spatialize** checkbox, Unity will use its panning spatializer, instead of the **Microsoft Spatializer** with HRTFs.</span></span>

## <a name="adjust-the-volume-curve"></a><span data-ttu-id="64c83-137">Ajuster la courbe du volume</span><span class="sxs-lookup"><span data-stu-id="64c83-137">Adjust the Volume curve</span></span>

<span data-ttu-id="64c83-138">Par défaut, Unity atténue les sons spatiaux au fur et à mesure qu’ils s’éloignent de l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="64c83-138">By default, Unity will attenuate spatialized sounds as they get farther from the listener.</span></span> <span data-ttu-id="64c83-139">Lorsque cette atténuation est appliquée à des sons d’interaction, l’interface peut devenir plus difficile à utiliser.</span><span class="sxs-lookup"><span data-stu-id="64c83-139">When this attenuation is applied to interaction feedback sounds, the interface can become more difficult to use.</span></span>

<span data-ttu-id="64c83-140">Pour désactiver cette atténuation, ajustez la courbe du **volume** .</span><span class="sxs-lookup"><span data-stu-id="64c83-140">To disable this attenuation, adjust the **Volume** curve.</span></span> <span data-ttu-id="64c83-141">Dans le composant **source audio** du volet de l' **inspecteur** pour **PressableButtonHoloLens2**, il existe une section intitulée **paramètres audio 3D**.</span><span class="sxs-lookup"><span data-stu-id="64c83-141">In the **Audio Source** component of the **Inspector** pane for the **PressableButtonHoloLens2**, there is a section called **3D Sound Settings**.</span></span> <span data-ttu-id="64c83-142">Dans cette section :</span><span class="sxs-lookup"><span data-stu-id="64c83-142">In that section:</span></span>
1. <span data-ttu-id="64c83-143">Définir la propriété **volume Rolloff** sur Linear</span><span class="sxs-lookup"><span data-stu-id="64c83-143">Set the **Volume Rolloff** property to Linear</span></span>
2. <span data-ttu-id="64c83-144">Faites glisser le point de terminaison sur la courbe de **volume** (la courbe rouge) de « 0 » sur l’axe y jusqu’à « 1 »</span><span class="sxs-lookup"><span data-stu-id="64c83-144">Drag the endpoint on the **Volume** curve (the red curve) from '0' on the y axis up to '1'</span></span>
3. <span data-ttu-id="64c83-145">Pour ajuster la forme de la courbe de **volume** à plat, faites glisser le contrôle de forme de courbe blanche pour qu’il soit parallèle à l’axe X.</span><span class="sxs-lookup"><span data-stu-id="64c83-145">To adjust the shape of the **Volume** curve to be flat, drag the white curve shape control to be parallel to the X axis</span></span>

<span data-ttu-id="64c83-146">Une fois ces modifications effectuées, la section **paramètres audio 3D** des propriétés de la **source audio** de l' **PressableButtonHoloLens2** se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="64c83-146">After these changes, the **3D Sound Settings** section of the **Audio Source** properties of the **PressableButtonHoloLens2** will look like this:</span></span>

![Paramètres audio de bouton 3D](images/spatial-audio/button-3d-sound-settings.png)

## <a name="testing-the-spatialize-audio"></a><span data-ttu-id="64c83-148">Test du son spatial</span><span class="sxs-lookup"><span data-stu-id="64c83-148">Testing the spatialize audio</span></span>

<span data-ttu-id="64c83-149">N’hésitez pas à tester les nouveaux sons d’interaction du bouton spatial :</span><span class="sxs-lookup"><span data-stu-id="64c83-149">Feel free to test out the new spatialized button interaction sounds:</span></span>

* <span data-ttu-id="64c83-150">Entrer en mode jeu dans l’éditeur Unity, idéalement avec un échantillon audio en boucle dans la scène</span><span class="sxs-lookup"><span data-stu-id="64c83-150">Enter game mode in the Unity editor, ideally with a looped audio sample in the scene</span></span>
* <span data-ttu-id="64c83-151">Déplacez l’objet avec la source audio de gauche à droite et comparez avec et sans audio spatial activé.</span><span class="sxs-lookup"><span data-stu-id="64c83-151">Move the object with the audio source from left to right and compare with and without spatial audio enabled.</span></span> <span data-ttu-id="64c83-152">Vous pouvez modifier les paramètres de la source audio pour le test en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="64c83-152">You can change the Audio Source settings for testing by:</span></span>
    * <span data-ttu-id="64c83-153">Déplacement de la propriété de lissage spatial entre 0-1 (2D non spatial et 3D spatialic)</span><span class="sxs-lookup"><span data-stu-id="64c83-153">Moving the Spatial Blend property between 0 - 1 (2D non-spatialized and 3D spatialized sound)</span></span>
    * <span data-ttu-id="64c83-154">Vérification et désactivation de la propriété spatial</span><span class="sxs-lookup"><span data-stu-id="64c83-154">Checking and unchecking the Spatialize property</span></span>

## <a name="next-steps"></a><span data-ttu-id="64c83-155">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="64c83-155">Next steps</span></span>

<span data-ttu-id="64c83-156">Essayez votre application sur un HoloLens 2 ou dans l’éditeur Unity.</span><span class="sxs-lookup"><span data-stu-id="64c83-156">Try out your app on a HoloLens 2, or in the Unity editor.</span></span> <span data-ttu-id="64c83-157">Dans l’application, vous pouvez toucher le bouton et entendre les sons d’interaction du bouton spatial.</span><span class="sxs-lookup"><span data-stu-id="64c83-157">In the app, you can touch the button and hear the spatialized button interaction sounds.</span></span>

<span data-ttu-id="64c83-158">Lors du test dans l’éditeur Unity, appuyez sur la barre d’espace et faites défiler la molette pour activer la simulation manuelle.</span><span class="sxs-lookup"><span data-stu-id="64c83-158">When testing in the Unity editor, press the space bar and scroll with the scroll wheel to activate hand simulation.</span></span> <span data-ttu-id="64c83-159">Pour plus d’informations, consultez la [documentation MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene).</span><span class="sxs-lookup"><span data-stu-id="64c83-159">For more info, see the [MRTK documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene).</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="64c83-160">Chapitre 3</span><span class="sxs-lookup"><span data-stu-id="64c83-160">Chapter 3</span></span>](unity-spatial-audio-ch3.md)

