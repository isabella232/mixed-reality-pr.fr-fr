---
title: Vue d’ensemble des exemples de suivi oculaire
description: Exemple pour générer eyetracking dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, EyeTracking,
ms.openlocfilehash: 4cdeaa10725e00ac1a041c3692d64c1bd6488854
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175540"
---
# <a name="eye-tracking-examples-overview"></a><span data-ttu-id="1eb84-104">Vue d’ensemble des exemples de suivi oculaire</span><span class="sxs-lookup"><span data-stu-id="1eb84-104">Eye tracking examples overview</span></span>

<span data-ttu-id="1eb84-105">Cette rubrique explique comment prendre rapidement en main le suivi oculaire dans MRTK en vous appuyant sur les exemples de suivi oculaire MRTK (ressources/MRTK/exemples/démonstrations/EyeTracking).</span><span class="sxs-lookup"><span data-stu-id="1eb84-105">This topic describes how to quickly get started with eye tracking in MRTK by building on MRTK eye tracking examples (Assets/MRTK/Examples/Demos/EyeTracking).</span></span>
<span data-ttu-id="1eb84-106">Ces exemples vous permettent de découvrir l’une de nos nouvelles fonctionnalités de saisie magique : le **suivi oculaire**!</span><span class="sxs-lookup"><span data-stu-id="1eb84-106">These samples let you experience one of our new magical input capabilities: **Eye tracking**!</span></span>
<span data-ttu-id="1eb84-107">La démonstration comprend divers cas d’usage, allant des activations basées sur les yeux implicites à la manière de combiner en toute transparence les informations sur ce que vous examinez avec la **voix** et **les entrées.**</span><span class="sxs-lookup"><span data-stu-id="1eb84-107">The demo includes various use cases, ranging from implicit eye-based activations to how to seamlessly combine information about what you are looking at with **voice** and **hand** input.</span></span>
<span data-ttu-id="1eb84-108">Cela permet aux utilisateurs de sélectionner et de déplacer rapidement et facilement le contenu holographique dans leur vue simplement en regardant une cible et en disant _« Sélectionner »_ ou en effectuant un mouvement manuel.</span><span class="sxs-lookup"><span data-stu-id="1eb84-108">This enables users to quickly and effortlessly select and move holographic content across their view simply by looking at a target and saying _'Select'_ or performing a hand gesture.</span></span>
<span data-ttu-id="1eb84-109">Les démonstrations incluent également un exemple de défilement orienté vers le regard, panoramique et zoom du texte et des images sur un ardoise.</span><span class="sxs-lookup"><span data-stu-id="1eb84-109">The demos also include an example for eye-gaze-directed scroll, pan and zoom of text and images on a slate.</span></span>
<span data-ttu-id="1eb84-110">Enfin, un exemple est fourni pour l’enregistrement et la visualisation de l’attention visuelle de l’utilisateur sur un ardoise 2D.</span><span class="sxs-lookup"><span data-stu-id="1eb84-110">Finally, an example is provided for recording and visualizing the user's visual attention on a 2D slate.</span></span>
<span data-ttu-id="1eb84-111">Dans la section suivante, vous trouverez plus d’informations sur la façon dont chacun des différents exemples du package d’exemples de suivi oculaire MRTK (ressources/MRTK/examples/démos/EyeTracking) comprend :</span><span class="sxs-lookup"><span data-stu-id="1eb84-111">In the following section, you will find more details on what each of the different samples in the MRTK eye tracking example package (Assets/MRTK/Examples/Demos/EyeTracking) includes:</span></span>

![Liste des scènes de suivi oculaire](../images/eye-tracking/mrtk_et_list_et_scenes.jpg)

<span data-ttu-id="1eb84-113">La section suivante est une vue d’ensemble rapide des scènes de démonstration du suivi des yeux.</span><span class="sxs-lookup"><span data-stu-id="1eb84-113">The following section is a quick overview of what the individual eye tracking demo scenes are about.</span></span>
<span data-ttu-id="1eb84-114">Les scènes de démonstration de suivi oculaire MRTK sont [chargées](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)de manière additive, que nous expliquerons ci-dessous comment configurer.</span><span class="sxs-lookup"><span data-stu-id="1eb84-114">The MRTK eye tracking demo scenes are [loaded additively](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html), which we will explain below how to set up.</span></span>

## <a name="overview-of-the-eye-tracking-demo-samples"></a><span data-ttu-id="1eb84-115">Vue d’ensemble des exemples de démonstrations de suivi oculaire</span><span class="sxs-lookup"><span data-stu-id="1eb84-115">Overview of the eye tracking demo samples</span></span>

### <a name="eye-supported-target-selection"></a>[<span data-ttu-id="1eb84-116">**Sélection de la cible prise en charge par l’œil**</span><span class="sxs-lookup"><span data-stu-id="1eb84-116">**Eye-Supported Target Selection**</span></span>](../input/eye-tracking/eye-tracking-target-selection.md)

<span data-ttu-id="1eb84-117">Ce didacticiel présente la facilité d’accès aux données de regard oculaire pour sélectionner des cibles.</span><span class="sxs-lookup"><span data-stu-id="1eb84-117">This tutorial showcases the ease of accessing eye gaze data to select targets.</span></span>
<span data-ttu-id="1eb84-118">Il comprend un exemple de commentaires subtils et puissants pour fournir à l’utilisateur la certitude qu’une cible est ciblée sans être écrasante.</span><span class="sxs-lookup"><span data-stu-id="1eb84-118">It includes an example for subtle yet powerful feedback to provide the user with the confidence that a target is focused without being overwhelming.</span></span>
<span data-ttu-id="1eb84-119">En outre, il existe un exemple simple de notifications intelligentes qui disparaissent automatiquement après la lecture.</span><span class="sxs-lookup"><span data-stu-id="1eb84-119">In addition, there is a simple example of smart notifications that automatically disappear after being read.</span></span>

<span data-ttu-id="1eb84-120">**Résumé**: sélections de cibles rapides et faciles à l’aide d’une combinaison d’yeux, de voix et d’entrées de main.</span><span class="sxs-lookup"><span data-stu-id="1eb84-120">**Summary**: Fast and effortless target selections using a combination of eyes, voice and hand input.</span></span>

### <a name="eye-supported-navigation"></a>[<span data-ttu-id="1eb84-121">**Navigation prise en charge par l’œil**</span><span class="sxs-lookup"><span data-stu-id="1eb84-121">**Eye-Supported Navigation**</span></span>](../input/eye-tracking/eye-tracking-navigation.md)

<span data-ttu-id="1eb84-122">Imagine que vous lisez des informations sur un affichage distant ou sur un lecteur e-lecteur et que vous atteignez la fin du texte affiché, le texte défile automatiquement pour afficher davantage de contenu.</span><span class="sxs-lookup"><span data-stu-id="1eb84-122">Imagine that you are reading some information on a distant display or your e-reader and when you reach the end of the displayed text, the text automatically scrolls up to reveal more content.</span></span>
<span data-ttu-id="1eb84-123">Ou comment faire un zoom direct direct vers l’emplacement de votre recherche ?</span><span class="sxs-lookup"><span data-stu-id="1eb84-123">Or how about magically zooming directly toward where you were looking at?</span></span>
<span data-ttu-id="1eb84-124">Voici quelques-uns des exemples présentés dans ce didacticiel sur la navigation prise en charge par les yeux.</span><span class="sxs-lookup"><span data-stu-id="1eb84-124">These are some of the examples showcased in this tutorial regarding eye-supported navigation.</span></span>
<span data-ttu-id="1eb84-125">En outre, il existe un exemple de rotation mains libres d’hologrammes 3D en les faisant pivoter automatiquement en fonction de votre focus actuel.</span><span class="sxs-lookup"><span data-stu-id="1eb84-125">In addition, there is an example for hands-free rotation of 3D holograms by making them automatically rotate based on your current focus.</span></span>

<span data-ttu-id="1eb84-126">**Résumé**: défilement, panoramique, zoom, rotation 3D à l’aide d’une combinaison d’yeux, de voix et d’entrées de main.</span><span class="sxs-lookup"><span data-stu-id="1eb84-126">**Summary**: Scroll, pan, zoom, 3D rotation using a combination of eyes, voice and hand input.</span></span>

### <a name="eye-supported-positioning"></a>[<span data-ttu-id="1eb84-127">**Positionnement de la prise en charge oculaire**</span><span class="sxs-lookup"><span data-stu-id="1eb84-127">**Eye-Supported Positioning**</span></span>](../input/eye-tracking/eye-tracking-eyes-and-hands.md)

<span data-ttu-id="1eb84-128">Ce didacticiel présente un scénario d’entrée appelé [Put-It-](https://youtu.be/CbIn8p4_4CQ) le retour à la recherche à partir du MIT Media Lab au début des années 1980, avec les entrées de l’œil, de la main et de la voix.</span><span class="sxs-lookup"><span data-stu-id="1eb84-128">This tutorial shows an input scenario called [Put-That-There](https://youtu.be/CbIn8p4_4CQ) dating back to research from the MIT Media Lab in the early 1980's with eye, hand and voice input.</span></span>
<span data-ttu-id="1eb84-129">L’idée est simple : Tirez parti de vos yeux pour la sélection et le positionnement rapides des cibles.</span><span class="sxs-lookup"><span data-stu-id="1eb84-129">The idea is simple: Benefit from your eyes for fast target selection and positioning.</span></span>
<span data-ttu-id="1eb84-130">Examinez simplement un hologramme et dites « _Placer_», regardez où vous souhaitez le placer et dites-le _« là ! »_.</span><span class="sxs-lookup"><span data-stu-id="1eb84-130">Simply look at a hologram and say _'put this'_, look over where you want to place it and say _'there!'_.</span></span>
<span data-ttu-id="1eb84-131">Pour un positionnement plus précis de votre hologramme, vous pouvez utiliser des entrées supplémentaires de vos mains, de vos voix ou de vos contrôleurs.</span><span class="sxs-lookup"><span data-stu-id="1eb84-131">For more precisely positioning your hologram, you can use additional input from your hands, voice or controllers.</span></span>

<span data-ttu-id="1eb84-132">**Résumé**: positionnement des hologrammes à l’aide des yeux, des entrées vocales et de la main (*glisser-déplacer*).</span><span class="sxs-lookup"><span data-stu-id="1eb84-132">**Summary**: Positioning holograms using eyes, voice and hand input (*drag-and-drop*).</span></span> <span data-ttu-id="1eb84-133">Curseurs pris en charge par l’œil utilisant des yeux et des mains.</span><span class="sxs-lookup"><span data-stu-id="1eb84-133">Eye-supported sliders using eyes + hands.</span></span>

### <a name="visualization-of-visual-attention"></a><span data-ttu-id="1eb84-134">**Visualisation de l’attention visuelle**</span><span class="sxs-lookup"><span data-stu-id="1eb84-134">**Visualization of visual attention**</span></span>

<span data-ttu-id="1eb84-135">Les données basées sur l’emplacement des utilisateurs constituent un outil très puissant pour évaluer l’utilisation d’une conception et identifier les problèmes dans les flux de travail efficaces.</span><span class="sxs-lookup"><span data-stu-id="1eb84-135">Data based on where users look makes an immensely powerful tool to assess usability of a design and to identify problems in efficient work streams.</span></span>
<span data-ttu-id="1eb84-136">Ce didacticiel présente les différentes visualisations de suivi oculaire et la façon dont elles s’adaptent aux différents besoins.</span><span class="sxs-lookup"><span data-stu-id="1eb84-136">This tutorial discusses different eye tracking visualizations and how they fit different needs.</span></span>
<span data-ttu-id="1eb84-137">Nous fournissons des exemples de base pour la journalisation et le chargement des données de suivi visuel et des exemples pour la visualisation.</span><span class="sxs-lookup"><span data-stu-id="1eb84-137">We provide basic examples for logging and loading eye tracking data and examples for how to visualize them.</span></span>

<span data-ttu-id="1eb84-138">**Résumé**: carte à attention à deux dimensions (cartes thermiques) sur les ardoises.</span><span class="sxs-lookup"><span data-stu-id="1eb84-138">**Summary**: Two-dimensional attention map (heatmaps) on slates.</span></span> <span data-ttu-id="1eb84-139">Enregistrement & relecture des données de suivi oculaire.</span><span class="sxs-lookup"><span data-stu-id="1eb84-139">Recording & replaying eye tracking data.</span></span>

## <a name="setting-up-the-mrtk-eye-tracking-samples"></a><span data-ttu-id="1eb84-140">Configuration des exemples de suivi oculaire MRTK</span><span class="sxs-lookup"><span data-stu-id="1eb84-140">Setting up the MRTK eye tracking samples</span></span>

### <a name="prerequisites"></a><span data-ttu-id="1eb84-141">Prérequis</span><span class="sxs-lookup"><span data-stu-id="1eb84-141">Prerequisites</span></span>

<span data-ttu-id="1eb84-142">notez que l’utilisation des exemples de suivi oculaire sur l’appareil requiert une HoloLens 2 et un exemple de package d’application généré avec la fonctionnalité « en entrée de regard » sur le AppXManifest du package.</span><span class="sxs-lookup"><span data-stu-id="1eb84-142">Note that using the eye tracking samples on device requires a HoloLens 2 and a sample app package that is built with the "Gaze Input" capability on the package's AppXManifest.</span></span>

<span data-ttu-id="1eb84-143">Pour pouvoir utiliser ces exemples de suivi oculaire sur un appareil, veillez à suivre [ces étapes](../input/eye-tracking/eye-tracking-basic-setup.md#testing-your-unity-app-on-a-hololens-2) avant de créer l’application dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1eb84-143">In order to use these eye tracking samples on device, make sure to follow [these steps](../input/eye-tracking/eye-tracking-basic-setup.md#testing-your-unity-app-on-a-hololens-2) prior to building the app in Visual Studio.</span></span>

### <a name="1-load-eyetrackingdemo-00-rootsceneunity"></a><span data-ttu-id="1eb84-144">1. Chargez EyeTrackingDemo-00-RootScene. Unity</span><span class="sxs-lookup"><span data-stu-id="1eb84-144">1. Load EyeTrackingDemo-00-RootScene.unity</span></span>

<span data-ttu-id="1eb84-145">*EyeTrackingDemo-00-RootScene* est la scène de base (_racine_) qui contient tous les composants MRTK principaux.</span><span class="sxs-lookup"><span data-stu-id="1eb84-145">The *EyeTrackingDemo-00-RootScene* is the base (_root_) scene that has all the core MRTK components included.</span></span>
<span data-ttu-id="1eb84-146">Il s’agit de la scène que vous devez charger en premier et à partir de laquelle vous allez exécuter les démonstrations de suivi oculaire.</span><span class="sxs-lookup"><span data-stu-id="1eb84-146">This is the scene that you need to load first and from which you will run the eye tracking demos.</span></span>
<span data-ttu-id="1eb84-147">Il comprend un menu de scène graphique qui vous permet de basculer facilement entre les différents exemples de suivi oculaire qui seront chargés de manière [additive](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html).</span><span class="sxs-lookup"><span data-stu-id="1eb84-147">It features a graphical scene menu that allows you to easily switch between the different eye tracking samples which will be [loaded additively](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html).</span></span>

![Menu Scene dans l’exemple de suivi oculaire](../images/eye-tracking/mrtk_et_scenemenu.jpg)

<span data-ttu-id="1eb84-149">La scène racine comprend quelques composants principaux qui sont conservés dans les scènes chargées de manière additive, telles que les profils configurés par MRTK et l’appareil photo de scène.</span><span class="sxs-lookup"><span data-stu-id="1eb84-149">The root scene includes a few core components that will persist across the additively loaded scenes, such as the MRTK configured profiles and scene camera.</span></span>
<span data-ttu-id="1eb84-150">Le _MixedRealityBasicSceneSetup_ (voir la capture d’écran ci-dessous) comprend un script qui chargera automatiquement la scène référencée au démarrage.</span><span class="sxs-lookup"><span data-stu-id="1eb84-150">The _MixedRealityBasicSceneSetup_ (see screenshot below) includes a script that will automatically load the referenced scene on startup.</span></span>
<span data-ttu-id="1eb84-151">Par défaut, il s’agit de _EyeTrackingDemo-02-TargetSelection_.</span><span class="sxs-lookup"><span data-stu-id="1eb84-151">By default, this is _EyeTrackingDemo-02-TargetSelection_.</span></span>  

![Exemple de script OnLoadStartScene](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

### <a name="2-adding-scenes-to-the-build-menu"></a><span data-ttu-id="1eb84-153">2. Ajout de scènes au menu Générer</span><span class="sxs-lookup"><span data-stu-id="1eb84-153">2. Adding scenes to the build menu</span></span>

<span data-ttu-id="1eb84-154">pour charger des scènes additives pendant l’exécution, vous devez d’abord ajouter ces scènes à votre _Paramètres de build-> scènes dans_ le menu générer.</span><span class="sxs-lookup"><span data-stu-id="1eb84-154">To load additive scenes during runtime, you must add these scenes to your _Build Settings -> Scenes in Build_ menu first.</span></span>
<span data-ttu-id="1eb84-155">Il est important que la scène racine s’affiche comme la première scène de la liste :</span><span class="sxs-lookup"><span data-stu-id="1eb84-155">It is important that the root scene is shown as the first scene in the list:</span></span>

![menu générer Paramètres scène pour les exemples de suivi oculaire](../images/eye-tracking/mrtk_et_build_settings.jpg)

### <a name="3-play-the-eye-tracking-samples-in-the-unity-editor"></a><span data-ttu-id="1eb84-157">3. lire les exemples de suivi oculaire dans l’éditeur Unity</span><span class="sxs-lookup"><span data-stu-id="1eb84-157">3. Play the eye tracking samples in the Unity editor</span></span>

<span data-ttu-id="1eb84-158">après avoir ajouté les scènes de suivi oculaire à la Paramètres de génération et à charger _EyeTrackingDemo-00-RootScene_, il y a une dernière chose à vérifier : le script _« OnLoadStartScene »_ attaché au _MixedRealityBasicSceneSetup_ GameObject est-il activé ?</span><span class="sxs-lookup"><span data-stu-id="1eb84-158">After adding the eye tracking scenes to the Build Settings and loading the _EyeTrackingDemo-00-RootScene_, there is one last thing you may want to check: Is the _'OnLoadStartScene'_ script that is attached to the _MixedRealityBasicSceneSetup_ GameObject enabled?</span></span> <span data-ttu-id="1eb84-159">Cela permet d’informer la scène racine de la scène de démonstration à charger en premier.</span><span class="sxs-lookup"><span data-stu-id="1eb84-159">This is to let the root scene know which demo scene to load first.</span></span>

![Exemple pour le script OnLoad_StartScene](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

<span data-ttu-id="1eb84-161">Allons-y !</span><span class="sxs-lookup"><span data-stu-id="1eb84-161">Let's roll!</span></span> <span data-ttu-id="1eb84-162">Appuyez sur _« Play »_!</span><span class="sxs-lookup"><span data-stu-id="1eb84-162">Hit _"Play"_!</span></span>
<span data-ttu-id="1eb84-163">Vous devriez voir plusieurs gemmes apparaître et le menu scène en haut.</span><span class="sxs-lookup"><span data-stu-id="1eb84-163">You should see several gems appear and the scene menu at the top.</span></span>

![Exemple de capture d’écran de la cible ET sélectionner une scène](../images/eye-tracking/mrtk_et_targetselect.png)

<span data-ttu-id="1eb84-165">Vous devez également noter un petit cercle translucide au centre de votre vue de jeu.</span><span class="sxs-lookup"><span data-stu-id="1eb84-165">You should also notice a small semitransparent circle at the center of your game view.</span></span>
<span data-ttu-id="1eb84-166">Cela agit comme un indicateur (curseur) de la _simulation de regard_: appuyez simplement sur le _bouton droit_ de la souris et déplacez la souris pour modifier sa position.</span><span class="sxs-lookup"><span data-stu-id="1eb84-166">This acts as an indicator (cursor) of your _simulated eye gaze_: Simply press down the _right mouse button_ and move the mouse to change its position.</span></span>
<span data-ttu-id="1eb84-167">Quand le curseur pointe sur les gemmes, vous remarquerez qu’il sera aligné sur le centre de la gemme actuellement affichée.</span><span class="sxs-lookup"><span data-stu-id="1eb84-167">When the cursor is hovering over the gems, you will notice that it will snap to the center of the currently viewed gem.</span></span>
<span data-ttu-id="1eb84-168">C’est un excellent moyen de tester si des événements sont déclenchés comme prévu lors de la _« recherche »_ sur une cible.</span><span class="sxs-lookup"><span data-stu-id="1eb84-168">This is a great way to test if events are triggered as expected when _"looking"_ at a target.</span></span>
<span data-ttu-id="1eb84-169">Sachez _que le point de contrôle_ de la souris est un complément plutôt médiocre à nos mouvements d’oeil rapides et involontaires.</span><span class="sxs-lookup"><span data-stu-id="1eb84-169">Be aware that the _simulated eye gaze_ via mouse control is a rather poor supplement to our rapid and unintentional eye movements.</span></span>
<span data-ttu-id="1eb84-170">toutefois, il est parfait pour tester les fonctionnalités de base avant d’effectuer une itération sur la conception en la déployant sur l’appareil HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1eb84-170">However, it is great for testing the basic functionality before iterating on the design by deploying it to the HoloLens 2 device.</span></span>
<span data-ttu-id="1eb84-171">Retour à notre exemple de scène de suivi oculaire : la gemme pivote tant qu’elle est examinée et peut être détruite en « regardant » sur celle-ci et...</span><span class="sxs-lookup"><span data-stu-id="1eb84-171">Returning to our eye tracking sample scene: The gem rotates as long as being looked at and can be destroyed by "looking" at it and ...</span></span>

- <span data-ttu-id="1eb84-172">En appuyant sur _entrée_ (ce qui simule « Select »)</span><span class="sxs-lookup"><span data-stu-id="1eb84-172">Pressing _Enter_ (which simulates saying "select")</span></span>
- <span data-ttu-id="1eb84-173">Dire _« Select »_ dans votre microphone</span><span class="sxs-lookup"><span data-stu-id="1eb84-173">Saying _"select"_ into your microphone</span></span>
- <span data-ttu-id="1eb84-174">Tout en appuyant sur l' _espace_ pour afficher l’entrée simulée, cliquez sur le bouton gauche de la souris pour effectuer un pincement simulé</span><span class="sxs-lookup"><span data-stu-id="1eb84-174">While pressing _Space_ to show the simulated hand input, click the left mouse button to perform a simulated pinch</span></span>

<span data-ttu-id="1eb84-175">Nous décrivons plus en détail comment vous pouvez obtenir ces interactions dans notre didacticiel sur la [**sélection de cibles prises en charge**](../input/eye-tracking/eye-tracking-target-selection.md) par les yeux.</span><span class="sxs-lookup"><span data-stu-id="1eb84-175">We describe in more detail how you can achieve these interactions in our [**Eye-Supported Target Selection**](../input/eye-tracking/eye-tracking-target-selection.md) tutorial.</span></span>

<span data-ttu-id="1eb84-176">Lorsque vous déplacez le curseur vers la barre de menus supérieure de la scène, vous remarquerez que l’élément actuellement mis en surbrillance sera légèrement surligné.</span><span class="sxs-lookup"><span data-stu-id="1eb84-176">When moving the cursor up to the top menu bar in the scene, you will notice that the currently hovered item will highlight subtly.</span></span>
<span data-ttu-id="1eb84-177">Vous pouvez sélectionner l’élément actuellement mis en surbrillance à l’aide de l’une des méthodes de validation décrites ci-dessus (par exemple, en appuyant sur _entrée_).</span><span class="sxs-lookup"><span data-stu-id="1eb84-177">You can select the currently highlighted item by using one of the above described commit methods (e.g., pressing _Enter_).</span></span>
<span data-ttu-id="1eb84-178">De cette façon, vous pouvez basculer entre les différents exemples de scènes de suivi oculaire.</span><span class="sxs-lookup"><span data-stu-id="1eb84-178">This way you can switch between the different eye tracking sample scenes.</span></span>

### <a name="4-how-to-test-specific-sub-scenes"></a><span data-ttu-id="1eb84-179">4. Comment tester des sous-scènes spécifiques</span><span class="sxs-lookup"><span data-stu-id="1eb84-179">4. How to test specific sub scenes</span></span>

<span data-ttu-id="1eb84-180">Lorsque vous travaillez sur un scénario spécifique, vous pouvez ne pas souhaiter parcourir le menu scène à chaque fois.</span><span class="sxs-lookup"><span data-stu-id="1eb84-180">When working on a specific scenario, you may not want to go through the scene menu every time.</span></span>
<span data-ttu-id="1eb84-181">Au lieu de cela, vous souhaiterez peut-être commencer directement à partir de la scène sur laquelle vous travaillez quand vous appuyez sur le bouton de _lecture_ .</span><span class="sxs-lookup"><span data-stu-id="1eb84-181">Instead, you may want to start directly from the scene that you are currently working on when pressing the _Play_ button.</span></span>
<span data-ttu-id="1eb84-182">Aucun problème non plus !</span><span class="sxs-lookup"><span data-stu-id="1eb84-182">No problem!</span></span> <span data-ttu-id="1eb84-183">Voici ce que vous pouvez faire :</span><span class="sxs-lookup"><span data-stu-id="1eb84-183">Here is what you can do:</span></span>

1. <span data-ttu-id="1eb84-184">Charger la scène _racine_</span><span class="sxs-lookup"><span data-stu-id="1eb84-184">Load the _root_ scene</span></span>
2. <span data-ttu-id="1eb84-185">Dans la scène _racine_ , désactivez le script _'OnLoadStartScene'_</span><span class="sxs-lookup"><span data-stu-id="1eb84-185">In the _root_ scene, disable the _'OnLoadStartScene'_ script</span></span>
3. <span data-ttu-id="1eb84-186">_Glissez_ -déplacez une des scènes de test de suivi oculaire décrites ci-dessous (ou toute autre scène) dans votre affichage _hiérarchique_ , comme indiqué dans la capture d’écran ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="1eb84-186">_Drag and drop_ one of the eye tracking test scenes that are described below (or any other scene) into your _Hierarchy_ view as shown in the screenshot below.</span></span>

    ![Exemple de scène additive](../images/eye-tracking/mrtk_et_additivescene.jpg)

4. <span data-ttu-id="1eb84-188">Appuyez sur _Play_</span><span class="sxs-lookup"><span data-stu-id="1eb84-188">Press _Play_</span></span>

<span data-ttu-id="1eb84-189">notez que le chargement de la sous-scène comme celle-ci n’est pas persistant : cela signifie que si vous déployez votre application sur l’appareil HoloLens 2, elle ne chargera que la scène racine (en supposant qu’elle apparaît en haut de votre Paramètres de Build).</span><span class="sxs-lookup"><span data-stu-id="1eb84-189">Please note that loading the sub scene like this is not persistent: This means that if you deploy your app to the HoloLens 2 device, it will only load the root scene (assuming it appears at the top of your Build Settings).</span></span>
<span data-ttu-id="1eb84-190">En outre, lorsque vous partagez votre projet avec d’autres personnes, les sous-scènes ne sont pas chargées automatiquement.</span><span class="sxs-lookup"><span data-stu-id="1eb84-190">Also, when you share your project with others, the sub scenes are not automatically loaded.</span></span>

---

<span data-ttu-id="1eb84-191">Maintenant que vous savez comment faire fonctionner les exemples de suivi oculaire MRTK, commençons par examiner plus en détail comment sélectionner des hologrammes avec vos yeux : [sélection de cible prise en charge](../input/eye-tracking/eye-tracking-target-selection.md)par l’œil.</span><span class="sxs-lookup"><span data-stu-id="1eb84-191">Now that you know how to get the MRTK eye tracking example scenes to work, let's continue with diving deeper into how to select holograms with your eyes: [Eye-supported target selection](../input/eye-tracking/eye-tracking-target-selection.md).</span></span>

---
[<span data-ttu-id="1eb84-192">Retour à « suivi oculaire dans le MixedRealityToolkit »</span><span class="sxs-lookup"><span data-stu-id="1eb84-192">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](../input/eye-tracking/eye-tracking-Main.md)
