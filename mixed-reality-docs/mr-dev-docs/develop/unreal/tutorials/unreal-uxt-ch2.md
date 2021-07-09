---
title: 2. Initialisation de votre projet et de votre première application
description: Partie 2 sur 6 d’une série de tutoriels visant à créer une application de jeu d’échecs simple avec Unreal Engine 4 et le plug-in Mixed Reality Toolkit UX Tools
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, réalité mixte, tutoriel, bien démarrer, mrtk, uxt, UX Tools, documentation, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle
ms.openlocfilehash: f7cf43e8f1c040660b6a2688e234a271bc071b00
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712644"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="5fab6-104">2. Initialisation de votre projet et de votre première application</span><span class="sxs-lookup"><span data-stu-id="5fab6-104">2. Initializing your project and first application</span></span>

<span data-ttu-id="5fab6-105">Dans le premier tutoriel, vous allez commencer avec un nouveau projet Unreal et activer le plug-in HoloLens, créer et éclairer un niveau, et ajouter des pièces du jeu d’échecs.</span><span class="sxs-lookup"><span data-stu-id="5fab6-105">In the first tutorial, you'll start out with a new Unreal project and enable the HoloLens plugin, create and light a level, and add chess pieces.</span></span> <span data-ttu-id="5fab6-106">Vous allez utiliser des ressources prédéfinies pour tous les objets 3D et les matériaux : vous n’avez donc rien à modéliser vous-même.</span><span class="sxs-lookup"><span data-stu-id="5fab6-106">You'll be using our pre-made assets for all 3D objects and materials, so don't worry about modeling anything yourself.</span></span> <span data-ttu-id="5fab6-107">À la fin de ce tutoriel, vous disposerez d’un canevas vide prêt pour la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="5fab6-107">By the end of this tutorial, you'll have a blank canvas that's ready for mixed reality.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5fab6-108">Vérifiez que vous avez tous les prérequis mentionnés dans la page [Bien démarrer](/windows/mixed-reality/unreal-uxt-ch1).</span><span class="sxs-lookup"><span data-stu-id="5fab6-108">Make sure you have all the prerequisites from the [Getting Started](/windows/mixed-reality/unreal-uxt-ch1) page.</span></span>

## <a name="objectives"></a><span data-ttu-id="5fab6-109">Objectifs</span><span class="sxs-lookup"><span data-stu-id="5fab6-109">Objectives</span></span>

* <span data-ttu-id="5fab6-110">Configuration d’un projet Unreal pour le développement HoloLens</span><span class="sxs-lookup"><span data-stu-id="5fab6-110">Configuring an Unreal project for HoloLens development</span></span>
* <span data-ttu-id="5fab6-111">Importation de ressources et configuration d’une scène</span><span class="sxs-lookup"><span data-stu-id="5fab6-111">Importing assets and setting up a scene</span></span>
* <span data-ttu-id="5fab6-112">Création d’acteurs et d’événements au niveau du script avec des blueprints</span><span class="sxs-lookup"><span data-stu-id="5fab6-112">Creating Actors and script-level events with blueprints</span></span>

## <a name="creating-a-new-unreal-project"></a><span data-ttu-id="5fab6-113">Création d’un projet Unreal</span><span class="sxs-lookup"><span data-stu-id="5fab6-113">Creating a new Unreal project</span></span>

<span data-ttu-id="5fab6-114">La première chose dont vous avez besoin est un projet avec lequel travailler.</span><span class="sxs-lookup"><span data-stu-id="5fab6-114">The first thing you need is a project to work with.</span></span> <span data-ttu-id="5fab6-115">Si vous commencez juste à développer dans Unreal, vous devez [télécharger les fichiers de prise en charge](./unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) auprès d’Epic Launcher.</span><span class="sxs-lookup"><span data-stu-id="5fab6-115">If you're a first-time Unreal developer, you'll need to [download supporting files](./unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) from the Epic Launcher.</span></span>

1. <span data-ttu-id="5fab6-116">Lancer Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="5fab6-116">Launch Unreal Engine</span></span>

2. <span data-ttu-id="5fab6-117">Sélectionnez **Games** dans **New Project Categories**, puis cliquez sur **Next**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-117">Select **Games** in **New Project Categories** and click **Next**.</span></span> 

![Sélectionner le modèle de projet Games](images/unreal-uxt/2-gamestemplate.png)

3. <span data-ttu-id="5fab6-119">Sélectionnez le modèle **Blank**, puis cliquez sur **Next**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-119">Select the **Blank** Template and click **Next**.</span></span> 

![Sélectionner le modèle Blank](images/unreal-uxt/2-template.PNG)

4. <span data-ttu-id="5fab6-121">Définissez **C++** , **Scalable 3D or 2D, Mobile/Tablet** et **No Starter Content** dans **Project Settings**, puis choisissez un emplacement d’enregistrement et cliquez sur **Create Project**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-121">Set **C++**, **Scalable 3D or 2D, Mobile/Tablet**, and **No Starter Content** as your **Project Settings**, then choose a save location and click **Create Project**.</span></span> 

> [!NOTE]
> <span data-ttu-id="5fab6-122">Vous devez sélectionner un projet C++ plutôt qu’un projet Blueprint afin de générer le plug-in UX Tools, que vous configurerez plus loin dans la section 4.</span><span class="sxs-lookup"><span data-stu-id="5fab6-122">You must select a C++ project rather than a Blueprint project in order to build the UX Tools plugin, which you'll be setting up later on in section 4.</span></span>

![Paramètres du projet initial](images/unreal-uxt/2-project-settings.PNG)

<span data-ttu-id="5fab6-124">Le projet doit s’ouvrir automatiquement dans l’éditeur Unreal, ce qui signifie que vous êtes prêt à passer à la section suivante.</span><span class="sxs-lookup"><span data-stu-id="5fab6-124">The project should open up automatically in the Unreal editor, which means you're ready for the next section.</span></span>

## <a name="enabling-required-plugins"></a><span data-ttu-id="5fab6-125">Activation des plug-ins nécessaires</span><span class="sxs-lookup"><span data-stu-id="5fab6-125">Enabling required plugins</span></span>

<span data-ttu-id="5fab6-126">Pour utiliser les fonctionnalités disponibles via la plateforme de réalité mixte de Microsoft, vous devez d’abord installer et activer le plug-in Microsoft OpenXR.</span><span class="sxs-lookup"><span data-stu-id="5fab6-126">In order to use the features available via Microsoft's mixed reality platform, you'll first need to install and enable the Microsoft OpenXR plugin.</span></span> <span data-ttu-id="5fab6-127">Pour en savoir plus sur le plug-in, consultez le projet sur [GitHub](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span><span class="sxs-lookup"><span data-stu-id="5fab6-127">To learn more about the plugin, you can check out the project on [GitHub](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span></span>

1. <span data-ttu-id="5fab6-128">Ouvrez le lanceur Epic Games.</span><span class="sxs-lookup"><span data-stu-id="5fab6-128">Open the Epic Games Launcher.</span></span> <span data-ttu-id="5fab6-129">Accédez à la marketplace Unreal Engine et recherchez « [Microsoft OpenXR](https://www.unrealengine.com/marketplace/product/ef8930ca860148c498b46887da196239) ».</span><span class="sxs-lookup"><span data-stu-id="5fab6-129">Navigate to Unreal Engine Marketplace and search for "[Microsoft OpenXR](https://www.unrealengine.com/marketplace/product/ef8930ca860148c498b46887da196239)".</span></span> <span data-ttu-id="5fab6-130">Installez le plug-in sur votre moteur.</span><span class="sxs-lookup"><span data-stu-id="5fab6-130">Install the plugin to your engine.</span></span>

![Marketplace Unreal](images/unreal-uxt/2-openxr-plugin.PNG)

2. <span data-ttu-id="5fab6-132">De retour dans l’éditeur Unreal, accédez à **Paramètres du projet** > **Plug-ins** et recherchez « Microsoft OpenXR ».</span><span class="sxs-lookup"><span data-stu-id="5fab6-132">Back in the Unreal editor, go to **Project Settings** > **Plugins** and search for "Microsoft OpenXR".</span></span> <span data-ttu-id="5fab6-133">Vérifiez que le plug-in est activé et redémarrez l’éditeur si vous y êtes invité.</span><span class="sxs-lookup"><span data-stu-id="5fab6-133">Ensure the plugin is enabled and restart the editor if prompted.</span></span>

![Activation du plug-in Microsoft OpenXR](images/unreal-uxt/2-enable-plugin.PNG)

<span data-ttu-id="5fab6-135">L’activation du plug-in Microsoft OpenXR active automatiquement tous les autres plug-ins requis pour le développement de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="5fab6-135">Enabling the Microsoft OpenXR plugin will automatically enable all the other plugins required for mixed reality development.</span></span> <span data-ttu-id="5fab6-136">Notez que le plug-in « Microsoft Windows Mixed Reality » doit être désactivé pour pouvoir utiliser OpenXR.</span><span class="sxs-lookup"><span data-stu-id="5fab6-136">Note that the "Microsoft Windows Mixed Reality" plugin must be disabled in order to use OpenXR.</span></span> 

## <a name="creating-a-level"></a><span data-ttu-id="5fab6-137">Création d’un niveau</span><span class="sxs-lookup"><span data-stu-id="5fab6-137">Creating a level</span></span>
<span data-ttu-id="5fab6-138">La tâche suivante consiste à créer une configuration de joueur avec un point de départ, et un cube pour la référence et la mise à l’échelle.</span><span class="sxs-lookup"><span data-stu-id="5fab6-138">Your next task is to create a player setup with a starting point and a cube for reference and scale.</span></span>

1. <span data-ttu-id="5fab6-139">Sélectionnez **File > New Level**, puis choisissez **Empty Level**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-139">Select **File > New Level** and choose **Empty Level**.</span></span> <span data-ttu-id="5fab6-140">La scène par défaut dans la fenêtre d’affichage doit maintenant être vide.</span><span class="sxs-lookup"><span data-stu-id="5fab6-140">The default scene in the viewport should now be empty.</span></span>

2. <span data-ttu-id="5fab6-141">Sélectionnez **Basic** sous l’onglet **Modes**, puis faites glisser **PlayerStart** dans la scène.</span><span class="sxs-lookup"><span data-stu-id="5fab6-141">Select **Basic** from the **Modes** tab and drag **PlayerStart** into the scene.</span></span> 
    * <span data-ttu-id="5fab6-142">Définissez **Location** sur **X = 0**, **Y = 0** et **Z = 0** dans l’onglet **Details** pour définir l’utilisateur au centre de la scène lors du démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="5fab6-142">Set **Location** to **X = 0**, **Y = 0**, and **Z = 0** in the **Details** tab to set the user at the center of the scene when the app starts up.</span></span>

![Fenêtre d’affichage avec PlayerStart](images/unreal-uxt/2-playerstart.PNG)

3. <span data-ttu-id="5fab6-144">Faites glisser un **cube** à partir de l’onglet **Basic** dans la scène.</span><span class="sxs-lookup"><span data-stu-id="5fab6-144">Drag a **Cube** from the **Basic** tab into the scene.</span></span> 
    * <span data-ttu-id="5fab6-145">Affectez à **Location** les valeurs **X = 50**, **Y = 0** et **Z = 0**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-145">Set **Location** to **X = 50**, **Y = 0**, and **Z = 0**.</span></span> <span data-ttu-id="5fab6-146">pour placer le cube à 50 cm du joueur au moment du démarrage.</span><span class="sxs-lookup"><span data-stu-id="5fab6-146">to position the cube 50 cm away from the player at start time.</span></span> 
    * <span data-ttu-id="5fab6-147">Affectez à **Scale** les valeurs **X = 0,2**, **Y = 0,2** et **Z = 0,2** pour réduire le cube.</span><span class="sxs-lookup"><span data-stu-id="5fab6-147">Change **Scale** to **X = 0.2**, **Y = 0.2**, and **Z = 0.2** to shrink the cube down.</span></span> 

<span data-ttu-id="5fab6-148">Vous ne pouvez pas voir le cube, sauf si vous ajoutez une lumière à votre scène, ce qui constitue votre dernière tâche avant de tester la scène.</span><span class="sxs-lookup"><span data-stu-id="5fab6-148">You can't see the cube unless you add a light to your scene, which is your last task before testing the scene.</span></span>

4. <span data-ttu-id="5fab6-149">Passez à l’onglet **Lights** dans le panneau **Modes**, puis faites glisser un **Directional Light** dans la scène.</span><span class="sxs-lookup"><span data-stu-id="5fab6-149">Switch to the **Lights** tab in the **Modes** panel and drag a **Directional Light** into the scene.</span></span> <span data-ttu-id="5fab6-150">Placez la lumière au-dessus de **PlayerStart** pour pouvoir la voir.</span><span class="sxs-lookup"><span data-stu-id="5fab6-150">Position the light above **PlayerStart** so you can see it.</span></span>

![Fenêtre d’affichage avec une lumière ajoutée](images/unreal-uxt/2-light.PNG)

5. <span data-ttu-id="5fab6-152">Accédez à **File > Save Current**, nommez votre niveau **Main**, puis sélectionnez **Save**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-152">Go to **File > Save Current**, name your level **Main**, and select **Save**.</span></span> 

<span data-ttu-id="5fab6-153">Une fois la scène définie, appuyez sur **Play** dans la barre d’outils pour voir votre cube en action !</span><span class="sxs-lookup"><span data-stu-id="5fab6-153">With the scene set, press **Play** in the toolbar to see your cube in action!</span></span> <span data-ttu-id="5fab6-154">Lorsque vous avez fini d’admirer votre travail, appuyez sur **Échap** pour arrêter l’application.</span><span class="sxs-lookup"><span data-stu-id="5fab6-154">When you're finished admiring your work, press **Esc** to stop the application.</span></span>

![Un cube dans la fenêtre d’affichage](images/unreal-uxt/2-cube.PNG)

<span data-ttu-id="5fab6-156">Maintenant que la scène est configurée, vous pouvez commencer à y ajouter l’échiquier et la pièce pour compléter l’environnement de l’application.</span><span class="sxs-lookup"><span data-stu-id="5fab6-156">Now that the scene is set up, you can start adding in the chess board and piece to round out the application environment.</span></span>

## <a name="importing-assets"></a><span data-ttu-id="5fab6-157">Importation de ressources</span><span class="sxs-lookup"><span data-stu-id="5fab6-157">Importing assets</span></span>
<span data-ttu-id="5fab6-158">La scène a l’air un peu vide pour le moment, mais vous allez y remédier en important les ressources prêtes à l’emploi dans le projet.</span><span class="sxs-lookup"><span data-stu-id="5fab6-158">The scene is looking a bit empty at the moment, but you'll fix that by importing the ready-made assets into the project.</span></span>

1. <span data-ttu-id="5fab6-159">Téléchargez et décompressez le dossier des ressources [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) avec [7-zip](https://www.7-zip.org/).</span><span class="sxs-lookup"><span data-stu-id="5fab6-159">Download and unzip the [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) assets folder using [7-zip](https://www.7-zip.org/).</span></span>

2. <span data-ttu-id="5fab6-160">Sélectionnez **Add New > New Folder** à partir du **Content Browser** et nommez ce dossier **ChessAssets**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-160">Select **Add New > New Folder** from the **Content Browser** and name it **ChessAssets**.</span></span> 
    * <span data-ttu-id="5fab6-161">Double-cliquez sur le nouveau dossier où vous allez importer les ressources 3D.</span><span class="sxs-lookup"><span data-stu-id="5fab6-161">Double-click the new folder where you'll import the 3D assets.</span></span>

![Afficher ou masquer le panneau des sources](images/unreal-uxt/2-showhidesources.PNG)

3. <span data-ttu-id="5fab6-163">Sélectionnez **Import** à partir du **Content Browser**, sélectionnez tous les éléments inclus dans le dossier des ressources décompressé, puis cliquez sur **Open**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-163">Select **Import** from the **Content Browser**, select all the items in the unzipped assets folder and click **Open**.</span></span> 
    * <span data-ttu-id="5fab6-164">Les ressources incluent les maillages d’objets 3D pour l’échiquier et les pièces au format FBX ainsi que les cartes de texture au format TGA que vous allez utiliser pour les matériaux.</span><span class="sxs-lookup"><span data-stu-id="5fab6-164">Assets include the 3D object meshes for the chess board and pieces in FBX format and texture maps in TGA format that you'll use to for materials.</span></span>  

4. <span data-ttu-id="5fab6-165">Lorsque la fenêtre FBX Import Options s’affiche, développez la section **Material** et affectez à **Material Import Method** la valeur **Do Not Create Material**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-165">When the FBX Import Options window pops up, expand the **Material** section and change **Material Import Method** to **Do Not Create Material**.</span></span>
    * <span data-ttu-id="5fab6-166">Sélectionnez **Import All**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-166">Select **Import All**.</span></span>

![Options d’importation FBX](images/unreal-uxt/2-nocreatemat.PNG)

<span data-ttu-id="5fab6-168">C’est tout ce que vous devez faire pour les ressources.</span><span class="sxs-lookup"><span data-stu-id="5fab6-168">That's all you need to do for the assets.</span></span> <span data-ttu-id="5fab6-169">Votre prochaine série de tâches consiste à créer les composants de l’application avec des blueprints.</span><span class="sxs-lookup"><span data-stu-id="5fab6-169">Your next set of tasks is to create the building blocks of the application with blueprints.</span></span>

## <a name="adding-blueprints"></a><span data-ttu-id="5fab6-170">Ajout de blueprints</span><span class="sxs-lookup"><span data-stu-id="5fab6-170">Adding blueprints</span></span>

1. <span data-ttu-id="5fab6-171">Sélectionnez **Add New > New Folder** dans le **Content Browser** et nommez ce dossier **Blueprints**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-171">Select **Add New > New Folder** in the **Content Browser** and name it **Blueprints**.</span></span> 

> [!NOTE]
> <span data-ttu-id="5fab6-172">Si vous ne connaissez pas les [blueprints](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html), il s’agit de ressources spéciales qui fournissent une interface basée sur des nœuds pour créer des types d’acteurs et d’événements au niveau des scripts.</span><span class="sxs-lookup"><span data-stu-id="5fab6-172">If you're new to [blueprints](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html), they're special assets that provide a node-based interface for creating new types of Actors and script level events.</span></span> 

2. <span data-ttu-id="5fab6-173">Double-cliquez dans le dossier **Blueprints**, puis cliquez avec le bouton droit et sélectionnez **Blueprint Class**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-173">Double-click into the **Blueprints** folder, then right-click and select **Blueprint Class**.</span></span>         
    * <span data-ttu-id="5fab6-174">Sélectionnez **Actor** et nommez le blueprint **Board**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-174">Select **Actor** and name the blueprint **Board**.</span></span> 

![Sélectionner une classe parente pour votre blueprint](images/unreal-uxt/2-bpparent.PNG)

<span data-ttu-id="5fab6-176">Le nouveau blueprint **Board** apparaît maintenant dans le dossier **Blueprints**, comme l’illustre la capture d’écran suivante.</span><span class="sxs-lookup"><span data-stu-id="5fab6-176">The new **Board** blueprint now shows up in the **Blueprints** folder as seen in the following screenshot.</span></span> 

![Le nouveau blueprint Board](images/unreal-uxt/2-bpboard.PNG)

<span data-ttu-id="5fab6-178">Vous êtes fin prêt pour commencer à ajouter des matériaux aux objets créés.</span><span class="sxs-lookup"><span data-stu-id="5fab6-178">You're all set to start adding materials to the created objects.</span></span>

## <a name="working-with-materials"></a><span data-ttu-id="5fab6-179">Utilisation de matériaux</span><span class="sxs-lookup"><span data-stu-id="5fab6-179">Working with materials</span></span>
<span data-ttu-id="5fab6-180">Les objets que vous avez créés sont gris par défaut, ce qui n’est pas très agréable à regarder.</span><span class="sxs-lookup"><span data-stu-id="5fab6-180">The objects you've created are default grey, which isn't much fun to look at.</span></span> <span data-ttu-id="5fab6-181">L’ajout de matériaux et de maillages à vos objets constitue la dernière série de tâches de ce tutoriel.</span><span class="sxs-lookup"><span data-stu-id="5fab6-181">Adding materials and meshes to your objects is the last set of tasks in this tutorial.</span></span>

1. <span data-ttu-id="5fab6-182">Double-cliquez sur **Board** pour ouvrir l’éditeur de blueprint.</span><span class="sxs-lookup"><span data-stu-id="5fab6-182">Double-click **Board** to open the blueprint editor.</span></span> 

2. <span data-ttu-id="5fab6-183">Sélectionnez **Add Component > Scene** dans le panneau **Components** et nommez-le composant **Root**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-183">Select **Add Component > Scene** from the **Components** panel and name it **Root**.</span></span> <span data-ttu-id="5fab6-184">Notez que **Root** apparaît en tant qu’enfant de **DefaultSceneRoot** dans la capture d’écran ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="5fab6-184">Notice that **Root** shows up as a child of **DefaultSceneRoot** in the screenshot below:</span></span>

![Remplacement de root dans le blueprint](images/unreal-uxt/2-root-blueprint.PNG)


3. <span data-ttu-id="5fab6-186">Cliquez et faites glisser **Root** sur **DefaultSceneRoot** pour le remplacer et vous débarrasser de la sphère dans la fenêtre d’affichage.</span><span class="sxs-lookup"><span data-stu-id="5fab6-186">Click-and-drag **Root** onto **DefaultSceneRoot** to replace it and get rid of the sphere in the viewport.</span></span> 

![Remplacement de la racine](images/unreal-uxt/2-root.PNG)


4. <span data-ttu-id="5fab6-188">Sélectionnez **Add Component > Static Mesh** dans le panneau **Components** et nommez le composant **SM_Board**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-188">Select **Add Component > Static Mesh** from the **Components** panel and name it **SM_Board**.</span></span> <span data-ttu-id="5fab6-189">Il apparaît en tant qu’objet enfant sous **Root**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-189">It will appear as a child object under **Root**.</span></span>

![Ajout d’un maillage statique](images/unreal-uxt/2-sm-board.PNG)

4. <span data-ttu-id="5fab6-191">Sélectionnez **SM_Board**, faites défiler vers le bas jusqu’à la section **Static Mesh** du panneau **Details**, puis sélectionnez **ChessBoard** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="5fab6-191">Select **SM_Board**, scroll down to the **Static Mesh** section of the **Details** panel, and select **ChessBoard** from the dropdown.</span></span> 

![Le maillage de l’échiquier dans la fenêtre d’affichage](images/unreal-uxt/2-sm-board-view.PNG)

5.  <span data-ttu-id="5fab6-193">Toujours dans le panneau **Details**, développez la section **Materials**, puis sélectionnez **Create New Asset > Material** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="5fab6-193">Still in the **Details** panel, expand the **Materials** section and select **Create New Asset > Material** from the dropdown.</span></span> 
    * <span data-ttu-id="5fab6-194">Nommez le matériau **M_ChessBoard** et enregistrez-le dans le dossier **ChessAssets**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-194">Name the material **M_ChessBoard** and save it to the **ChessAssets** folder.</span></span> 

![Créer un matériau](images/unreal-uxt/2-newmat.PNG)

6.  <span data-ttu-id="5fab6-196">Double-cliquez sur l’image du matériau **M_ChessBoard** pour ouvrir l’éditeur de matériau.</span><span class="sxs-lookup"><span data-stu-id="5fab6-196">Double-click the **M_ChessBoard** material imaged to open the Material Editor.</span></span> 

![Ouvrir l’éditeur de matériau](images/unreal-uxt/2-material-editor.PNG)

7. <span data-ttu-id="5fab6-198">Dans l’éditeur de matériau, cliquez avec le bouton droit et recherchez **Texture Sample**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-198">In the Material Editor, right-click and search for **Texture Sample**.</span></span> 
    * <span data-ttu-id="5fab6-199">Développez la section **Material Expression Texture Base** dans le panneau **Details** et affectez à **Texture** la valeur **ChessBoard_Albedo**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-199">Expand the **Material Expression Texture Base** section in the **Details** panel and set **Texture** to **ChessBoard_Albedo**.</span></span> 
    * <span data-ttu-id="5fab6-200">Faites glisser le repère de sortie **RGB** vers le repère Base Color de **M_ChessBoard**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-200">Drag the **RGB** output pin to the Base Color pin of **M_ChessBoard**.</span></span> 

![Définir la couleur de base](images/unreal-uxt/2-boardalbedomat.PNG)

8.  <span data-ttu-id="5fab6-202">Répétez l’étape précédente 4 fois de plus pour créer quatre autres nœuds **Texture Sample** avec les paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="5fab6-202">Repeat the previous step 4 more times to create four more **Texture Sample** nodes with the following settings:</span></span>
    * <span data-ttu-id="5fab6-203">Affectez à **Texture** la valeur **ChessBoard_AO** et liez le repère **RGB** au repère **Ambient Occlusion**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-203">Set **Texture** to **ChessBoard_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="5fab6-204">Affectez à **Texture** la valeur **ChessBoard_Metal** et liez le repère **RGB** au repère **Metallic**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-204">Set **Texture** to **ChessBoard_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="5fab6-205">Affectez à **Texture** la valeur **ChessBoard_Normal** et liez le repère **RGB** au repère **Normal**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-205">Set **Texture** to **ChessBoard_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="5fab6-206">Affectez à **Texture** la valeur **ChessBoard_Rough** et liez le repère **RGB** au repère **Roughness**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-206">Set **Texture** to **ChessBoard_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="5fab6-207">Cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-207">Click **Save**.</span></span> 

![Raccorder les textures restantes](images/unreal-uxt/2-boardmat.PNG)

<span data-ttu-id="5fab6-209">Vérifiez que la configuration de votre matériau ressemble à la capture d’écran ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="5fab6-209">Make sure your material setup looks like the above screenshot before continuing.</span></span>

## <a name="populating-the-scene"></a><span data-ttu-id="5fab6-210">Remplissage de la scène</span><span class="sxs-lookup"><span data-stu-id="5fab6-210">Populating the scene</span></span>
<span data-ttu-id="5fab6-211">Si vous revenez au blueprint **Board**, vous voyez que le matériau que vous venez de créer a été appliqué.</span><span class="sxs-lookup"><span data-stu-id="5fab6-211">If you go back to the **Board** blueprint, you'll see that the material you just created has been applied.</span></span> <span data-ttu-id="5fab6-212">Il ne vous reste plus qu’à installer la scène !</span><span class="sxs-lookup"><span data-stu-id="5fab6-212">All that's left is setting up the scene!</span></span> <span data-ttu-id="5fab6-213">Pour commencer, modifiez les propriétés suivantes pour vous assurer que l’échiquier est de taille raisonnable et qu’il est correctement incliné lorsqu’il est placé dans la scène :</span><span class="sxs-lookup"><span data-stu-id="5fab6-213">First, change the following properties to make sure the board is a reasonable size and angled correctly when it's placed in the scene:</span></span>
1.  <span data-ttu-id="5fab6-214">Affectez à **Scale** la valeur **(0,05, 0,05, 0,05)** et à **Z Rotation** la valeur **90**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-214">Set **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span> 
    * <span data-ttu-id="5fab6-215">Cliquez sur **Compile** dans la barre d’outils supérieure, puis sur **Save** pour revenir à la fenêtre Main.</span><span class="sxs-lookup"><span data-stu-id="5fab6-215">Click **Compile** in the top toolbar, then **Save** and return to the Main window.</span></span> 

![Échiquier avec un matériau appliqué](images/unreal-uxt/2-chessboard.PNG)

2.  <span data-ttu-id="5fab6-217">Cliquez avec le bouton droit sur **Cube > Edit > Delete**, puis faites glisser **Board** depuis le **Content Browser** dans la fenêtre d’affichage.</span><span class="sxs-lookup"><span data-stu-id="5fab6-217">Right-click **Cube > Edit > Delete** and drag **Board** from the **Content Browser** into the viewport.</span></span> 
    * <span data-ttu-id="5fab6-218">Affectez à **Location** les valeurs **X = 80**, **Y = 0** et **Z = -20**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-218">Set **Location** to **X = 80**, **Y = 0**, and **Z = -20**.</span></span> 

3.  <span data-ttu-id="5fab6-219">Sélectionnez le bouton **Play** pour visualiser votre nouvel échiquier dans le niveau.</span><span class="sxs-lookup"><span data-stu-id="5fab6-219">Select the **Play** button to view your new board in the level.</span></span> <span data-ttu-id="5fab6-220">Appuyez sur **Échap** pour revenir à l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="5fab6-220">Press **Esc** to return to the editor.</span></span> 

<span data-ttu-id="5fab6-221">À présent, vous allez suivre les mêmes étapes pour créer une pièce de jeu d’échecs que celles que vous avez effectuées pour l’échiquier :</span><span class="sxs-lookup"><span data-stu-id="5fab6-221">Now you'll follow the same steps to create a chess piece as you did with the board:</span></span>

1. <span data-ttu-id="5fab6-222">Accédez au dossier **Blueprints**, cliquez avec le bouton droit et sélectionnez **Blueprint Class**, puis choisissez **Actor**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-222">Go to the **Blueprints** folder, right-click, and select **Blueprint Class** and choose **Actor**.</span></span> <span data-ttu-id="5fab6-223">Nommez cet acteur **WhiteKing**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-223">Name the actor **WhiteKing**.</span></span>

2. <span data-ttu-id="5fab6-224">Double-cliquez sur **WhiteKing** pour l’ouvrir dans l’éditeur de blueprint, sélectionnez **Add Component > Scene** et nommez-le **Root**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-224">Double-click **WhiteKing** to open it in the Blueprint Editor, select **Add Component > Scene** and name it **Root**.</span></span> 
    * <span data-ttu-id="5fab6-225">Glissez-déposez **Root** dans **DefaultSceneRoot** pour le remplacer.</span><span class="sxs-lookup"><span data-stu-id="5fab6-225">Drag-and-drop **Root** onto **DefaultSceneRoot** to replace it.</span></span> 

3. <span data-ttu-id="5fab6-226">Cliquez sur **Add Component > Static Mesh** et nommez ce composant **SM_King**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-226">Click **Add Component > Static Mesh** and name it **SM_King**.</span></span> 
    * <span data-ttu-id="5fab6-227">Affectez à **Static Mesh** la valeur **Chess_King** et à **Material** la valeur d’un nouveau matériau appelé **M_ChessWhite** dans le panneau Details.</span><span class="sxs-lookup"><span data-stu-id="5fab6-227">Set **Static Mesh** to **Chess_King** and **Material** to a new Material called **M_ChessWhite** in the Details panel.</span></span> 

4. <span data-ttu-id="5fab6-228">Ouvrez **M_ChessWhite** dans l’éditeur de matériau et raccordez les nœuds **Texture Sample** suivants aux éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="5fab6-228">Open **M_ChessWhite** in the Material editor and hook up the following **Texture Sample** nodes to the following:</span></span>
   * <span data-ttu-id="5fab6-229">Affectez à **Texture** la valeur **ChessWhite_Albedo** et liez le repère **RGB** au repère **Base Color**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-229">Set **Texture** to **ChessWhite_Albedo** and link the **RGB** to the **Base Color** pin.</span></span>
    * <span data-ttu-id="5fab6-230">Affectez à **Texture** la valeur **ChessWhite_AO** et liez le repère **RGB** au repère **Ambient Occlusion**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-230">Set **Texture** to **ChessWhite_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="5fab6-231">Affectez à **Texture** la valeur **ChessWhite_Metal** et liez le repère **RGB** au repère **Metallic**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-231">Set **Texture** to **ChessWhite_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="5fab6-232">Affectez à **Texture** la valeur **ChessWhite_Normal** et liez le repère **RGB** au repère **Normal**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-232">Set **Texture** to **ChessWhite_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="5fab6-233">Affectez à **Texture** la valeur **ChessWhite_Rough** et liez le repère **RGB** au repère **Roughness**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-233">Set **Texture** to **ChessWhite_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="5fab6-234">Cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-234">Click **Save**.</span></span> 

<span data-ttu-id="5fab6-235">Votre matériau **M_ChessKing** doit ressembler à l’image suivante avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="5fab6-235">Your **M_ChessKing** material should look like the following image before continuing.</span></span>

![Créer le matériau pour le roi](images/unreal-uxt/2-chesskingmat.PNG)

<span data-ttu-id="5fab6-237">Vous y êtes presque, il vous suffit d’ajouter la nouvelle pièce à la scène :</span><span class="sxs-lookup"><span data-stu-id="5fab6-237">You're almost there, just need to add the new chess piece into the scene:</span></span> 

1. <span data-ttu-id="5fab6-238">Ouvrez le blueprint **WhiteKing** et affectez à **Scale** la valeur **(0,05, 0,05, 0,05)** et à **Z Rotation** la valeur **90**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-238">Open the **WhiteKing** blueprint and change the **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span>
    * <span data-ttu-id="5fab6-239">Compilez et enregistrez votre blueprint, puis revenez à la fenêtre principale.</span><span class="sxs-lookup"><span data-stu-id="5fab6-239">Compile and save your blueprint, then head back to the main window.</span></span> 

2.  <span data-ttu-id="5fab6-240">Faites glisser **WhiteKing** dans la fenêtre d’affichage, basculez vers le panneau **World Outliner**, faites glisser **WhiteKing** sur **Board** pour en faire un objet enfant.</span><span class="sxs-lookup"><span data-stu-id="5fab6-240">Drag **WhiteKing** into the viewport, switch to the **World Outliner** panel drag **WhiteKing** onto **Board** to make it a child object.</span></span>

![World Outliner](images/unreal-uxt/2-child.PNG)

3.  <span data-ttu-id="5fab6-242">Dans le panneau **Details** sous **Transform**, affectez au paramètre **Location** de **WhiteKing** les valeurs **X = -26**, **Y = 4** et **Z = 0**.</span><span class="sxs-lookup"><span data-stu-id="5fab6-242">In the **Details** panel under **Transform**, set **WhiteKing**'s **Location** to **X = -26**, **Y = 4**, and **Z = 0**.</span></span>

<span data-ttu-id="5fab6-243">C’est terminé !</span><span class="sxs-lookup"><span data-stu-id="5fab6-243">That's a wrap!</span></span> <span data-ttu-id="5fab6-244">Sélectionnez **Play** pour voir votre niveau rempli en action, puis appuyez sur **Échap** quand vous êtes prêt à quitter.</span><span class="sxs-lookup"><span data-stu-id="5fab6-244">Select **Play** to see your populated level in action, and press **Esc** when you're ready to exit.</span></span> <span data-ttu-id="5fab6-245">Vous avez abordé de nombreux points liés à la création d’un projet simple, mais vous êtes maintenant prêt à passer à la partie suivante de la série : la configuration pour la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="5fab6-245">You covered a lot of ground just creating a simple project, but now you're ready to move on to the next part of the series: setting up for mixed reality.</span></span> 

[<span data-ttu-id="5fab6-246">Section suivante : 3. Configurer votre projet pour la réalité mixte</span><span class="sxs-lookup"><span data-stu-id="5fab6-246">Next Section: 3. Set up your project for mixed reality</span></span>](unreal-uxt-ch3.md)