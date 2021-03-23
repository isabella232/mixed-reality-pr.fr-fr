---
title: 2. Initialisation de votre projet et de votre première application
description: Partie 2 sur 6 d’une série de tutoriels visant à créer une application de jeu d’échecs simple avec Unreal Engine 4 et le plug-in Mixed Reality Toolkit UX Tools
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, réalité mixte, tutoriel, bien démarrer, mrtk, uxt, UX Tools, documentation, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle
ms.openlocfilehash: 9e02ea6cb2710b4661e97dc8b0d5f4f48ab09fa7
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "98583905"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="e5cba-104">2. Initialisation de votre projet et de votre première application</span><span class="sxs-lookup"><span data-stu-id="e5cba-104">2. Initializing your project and first application</span></span>

<span data-ttu-id="e5cba-105">Dans le premier tutoriel, vous allez commencer avec un nouveau projet Unreal et activer le plug-in HoloLens, créer et éclairer un niveau, et ajouter des pièces du jeu d’échecs.</span><span class="sxs-lookup"><span data-stu-id="e5cba-105">In the first tutorial, you'll start out with a new Unreal project and enable the HoloLens plugin, create and light a level, and add chess pieces.</span></span> <span data-ttu-id="e5cba-106">Vous allez utiliser des ressources prédéfinies pour tous les objets 3D et les matériaux : vous n’avez donc rien à modéliser vous-même.</span><span class="sxs-lookup"><span data-stu-id="e5cba-106">You'll be using our pre-made assets for all 3D objects and materials, so don't worry about modeling anything yourself.</span></span> <span data-ttu-id="e5cba-107">À la fin de ce tutoriel, vous disposerez d’un canevas vide prêt pour la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="e5cba-107">By the end of this tutorial, you'll have a blank canvas that's ready for mixed reality.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e5cba-108">Vérifiez que vous avez tous les prérequis mentionnés dans la page [Bien démarrer](/windows/mixed-reality/unreal-uxt-ch1).</span><span class="sxs-lookup"><span data-stu-id="e5cba-108">Make sure you have all the prerequisites from the [Getting Started](/windows/mixed-reality/unreal-uxt-ch1) page.</span></span>

## <a name="objectives"></a><span data-ttu-id="e5cba-109">Objectifs</span><span class="sxs-lookup"><span data-stu-id="e5cba-109">Objectives</span></span>

* <span data-ttu-id="e5cba-110">Configuration d’un projet Unreal pour le développement HoloLens</span><span class="sxs-lookup"><span data-stu-id="e5cba-110">Configuring an Unreal project for HoloLens development</span></span>
* <span data-ttu-id="e5cba-111">Importation de ressources et configuration d’une scène</span><span class="sxs-lookup"><span data-stu-id="e5cba-111">Importing assets and setting up a scene</span></span>
* <span data-ttu-id="e5cba-112">Création d’acteurs et d’événements au niveau du script avec des blueprints</span><span class="sxs-lookup"><span data-stu-id="e5cba-112">Creating Actors and script-level events with blueprints</span></span>

## <a name="creating-a-new-unreal-project"></a><span data-ttu-id="e5cba-113">Création d’un projet Unreal</span><span class="sxs-lookup"><span data-stu-id="e5cba-113">Creating a new Unreal project</span></span>

<span data-ttu-id="e5cba-114">La première chose dont vous avez besoin est un projet avec lequel travailler.</span><span class="sxs-lookup"><span data-stu-id="e5cba-114">The first thing you need is a project to work with.</span></span> <span data-ttu-id="e5cba-115">Si vous commencez juste à développer dans Unreal, vous devez [télécharger les fichiers de prise en charge](./unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) auprès d’Epic Launcher.</span><span class="sxs-lookup"><span data-stu-id="e5cba-115">If you're a first-time Unreal developer, you'll need to [download supporting files](./unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) from the Epic Launcher.</span></span>

1. <span data-ttu-id="e5cba-116">Lancer Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="e5cba-116">Launch Unreal Engine</span></span>

2. <span data-ttu-id="e5cba-117">Sélectionnez **Games** dans **New Project Categories**, puis cliquez sur **Next**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-117">Select **Games** in **New Project Categories** and click **Next**.</span></span> 

![Sélectionner le modèle de projet Games](images/unreal-uxt/2-gamestemplate.png)

3. <span data-ttu-id="e5cba-119">Sélectionnez le modèle **Blank**, puis cliquez sur **Next**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-119">Select the **Blank** Template and click **Next**.</span></span> 

![Sélectionner le modèle Blank](images/unreal-uxt/2-template.PNG)

4. <span data-ttu-id="e5cba-121">Définissez **C++** , **Scalable 3D or 2D, Mobile/Tablet** et **No Starter Content** dans **Project Settings**, puis choisissez un emplacement d’enregistrement et cliquez sur **Create Project**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-121">Set **C++**, **Scalable 3D or 2D, Mobile/Tablet**, and **No Starter Content** as your **Project Settings**, then choose a save location and click **Create Project**.</span></span> 

> [!NOTE]
> <span data-ttu-id="e5cba-122">Vous devez sélectionner un projet C++ plutôt qu’un projet Blueprint afin de générer le plug-in UX Tools, que vous configurerez plus loin dans la section 4.</span><span class="sxs-lookup"><span data-stu-id="e5cba-122">You must select a C++ project rather than a Blueprint project in order to build the UX Tools plugin, which you'll be setting up later on in section 4.</span></span>

![Paramètres du projet initial](images/unreal-uxt/2-project-settings.PNG)

<span data-ttu-id="e5cba-124">Le projet doit s’ouvrir automatiquement dans l’éditeur Unreal, ce qui signifie que vous êtes prêt à passer à la section suivante.</span><span class="sxs-lookup"><span data-stu-id="e5cba-124">The project should open up automatically in the Unreal editor, which means you're ready for the next section.</span></span>

## <a name="enabling-required-plugins"></a><span data-ttu-id="e5cba-125">Activation des plug-ins nécessaires</span><span class="sxs-lookup"><span data-stu-id="e5cba-125">Enabling required plugins</span></span>

<span data-ttu-id="e5cba-126">Vous devez activer deux plug-ins pour pouvoir commencer à ajouter des objets à la scène.</span><span class="sxs-lookup"><span data-stu-id="e5cba-126">You'll need to enable two plugins before you can start adding objects to the scene.</span></span>

1. <span data-ttu-id="e5cba-127">Ouvrez **Edit > Plugins** et sélectionnez **Augmented Reality** dans la liste des options prédéfinies.</span><span class="sxs-lookup"><span data-stu-id="e5cba-127">Open **Edit > Plugins** and select **Augmented Reality** from the built-in options list.</span></span> 
    * <span data-ttu-id="e5cba-128">Faites défiler la liste jusqu’à **HoloLens** et cochez la case **Enabled**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-128">Scroll down to **HoloLens** and check **Enabled**.</span></span> 

![Activation des plug-ins HoloLens](images/unreal-uxt/2-plugins.PNG)

2. <span data-ttu-id="e5cba-130">Sélectionnez **Virtual Reality** dans la liste des options prédéfinies.</span><span class="sxs-lookup"><span data-stu-id="e5cba-130">Select **Virtual Reality** from the built-in options list.</span></span> 
    * <span data-ttu-id="e5cba-131">Faites défiler la liste jusqu’à **Microsoft Windows Mixed Reality**, cochez la case **Enabled**, puis redémarrez votre éditeur.</span><span class="sxs-lookup"><span data-stu-id="e5cba-131">Scroll down to **Microsoft Windows Mixed Reality**, check **Enabled**, and restart your editor.</span></span> 

![Activation du plug-in Windows Mixed Reality](images/unreal-uxt/2-virtual-reality-plugin.PNG)

> [!NOTE]
> <span data-ttu-id="e5cba-133">Les deux plug-ins sont nécessaires pour le développement HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="e5cba-133">Both plugins are required for HoloLens 2 development.</span></span>

<span data-ttu-id="e5cba-134">Une fois les plug-ins activés, votre niveau vide est prêt à avoir de la compagnie.</span><span class="sxs-lookup"><span data-stu-id="e5cba-134">With the plugins enabled, your empty level is ready for company.</span></span>

## <a name="creating-a-level"></a><span data-ttu-id="e5cba-135">Création d’un niveau</span><span class="sxs-lookup"><span data-stu-id="e5cba-135">Creating a level</span></span>
<span data-ttu-id="e5cba-136">La tâche suivante consiste à créer une configuration de joueur avec un point de départ, et un cube pour la référence et la mise à l’échelle.</span><span class="sxs-lookup"><span data-stu-id="e5cba-136">Your next task is to create a player setup with a starting point and a cube for reference and scale.</span></span>

1. <span data-ttu-id="e5cba-137">Sélectionnez **File > New Level**, puis choisissez **Empty Level**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-137">Select **File > New Level** and choose **Empty Level**.</span></span> <span data-ttu-id="e5cba-138">La scène par défaut dans la fenêtre d’affichage doit maintenant être vide.</span><span class="sxs-lookup"><span data-stu-id="e5cba-138">The default scene in the viewport should now be empty.</span></span>

2. <span data-ttu-id="e5cba-139">Sélectionnez **Basic** sous l’onglet **Modes**, puis faites glisser **PlayerStart** dans la scène.</span><span class="sxs-lookup"><span data-stu-id="e5cba-139">Select **Basic** from the **Modes** tab and drag **PlayerStart** into the scene.</span></span> 
    * <span data-ttu-id="e5cba-140">Définissez **Location** sur **X = 0**, **Y = 0** et **Z = 0** dans l’onglet **Details** pour définir l’utilisateur au centre de la scène lors du démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="e5cba-140">Set **Location** to **X = 0**, **Y = 0**, and **Z = 0** in the **Details** tab to set the user at the center of the scene when the app starts up.</span></span>

![Fenêtre d’affichage avec PlayerStart](images/unreal-uxt/2-playerstart.PNG)

3. <span data-ttu-id="e5cba-142">Faites glisser un **cube** à partir de l’onglet **Basic** dans la scène.</span><span class="sxs-lookup"><span data-stu-id="e5cba-142">Drag a **Cube** from the **Basic** tab into the scene.</span></span> 
    * <span data-ttu-id="e5cba-143">Affectez à **Location** les valeurs **X = 50**, **Y = 0** et **Z = 0**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-143">Set **Location** to **X = 50**, **Y = 0**, and **Z = 0**.</span></span> <span data-ttu-id="e5cba-144">pour placer le cube à 50 cm du joueur au moment du démarrage.</span><span class="sxs-lookup"><span data-stu-id="e5cba-144">to position the cube 50 cm away from the player at start time.</span></span> 
    * <span data-ttu-id="e5cba-145">Affectez à **Scale** les valeurs **X = 0,2**, **Y = 0,2** et **Z = 0,2** pour réduire le cube.</span><span class="sxs-lookup"><span data-stu-id="e5cba-145">Change **Scale** to **X = 0.2**, **Y = 0.2**, and **Z = 0.2** to shrink the cube down.</span></span> 

<span data-ttu-id="e5cba-146">Vous ne pouvez pas voir le cube, sauf si vous ajoutez une lumière à votre scène, ce qui constitue votre dernière tâche avant de tester la scène.</span><span class="sxs-lookup"><span data-stu-id="e5cba-146">You can't see the cube unless you add a light to your scene, which is your last task before testing the scene.</span></span>

4. <span data-ttu-id="e5cba-147">Passez à l’onglet **Lights** dans le panneau **Modes**, puis faites glisser un **Directional Light** dans la scène.</span><span class="sxs-lookup"><span data-stu-id="e5cba-147">Switch to the **Lights** tab in the **Modes** panel and drag a **Directional Light** into the scene.</span></span> <span data-ttu-id="e5cba-148">Placez la lumière au-dessus de **PlayerStart** pour pouvoir la voir.</span><span class="sxs-lookup"><span data-stu-id="e5cba-148">Position the light above **PlayerStart** so you can see it.</span></span>

![Fenêtre d’affichage avec une lumière ajoutée](images/unreal-uxt/2-light.PNG)

5. <span data-ttu-id="e5cba-150">Accédez à **File > Save Current**, nommez votre niveau **Main**, puis sélectionnez **Save**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-150">Go to **File > Save Current**, name your level **Main**, and select **Save**.</span></span> 

<span data-ttu-id="e5cba-151">Une fois la scène définie, appuyez sur **Play** dans la barre d’outils pour voir votre cube en action !</span><span class="sxs-lookup"><span data-stu-id="e5cba-151">With the scene set, press **Play** in the toolbar to see your cube in action!</span></span> <span data-ttu-id="e5cba-152">Lorsque vous avez fini d’admirer votre travail, appuyez sur **Échap** pour arrêter l’application.</span><span class="sxs-lookup"><span data-stu-id="e5cba-152">When you're finished admiring your work, press **Esc** to stop the application.</span></span>

![Un cube dans la fenêtre d’affichage](images/unreal-uxt/2-cube.PNG)

<span data-ttu-id="e5cba-154">Maintenant que la scène est configurée, vous pouvez commencer à y ajouter l’échiquier et la pièce pour compléter l’environnement de l’application.</span><span class="sxs-lookup"><span data-stu-id="e5cba-154">Now that the scene is set up, you can start adding in the chess board and piece to round out the application environment.</span></span>

## <a name="importing-assets"></a><span data-ttu-id="e5cba-155">Importation de ressources</span><span class="sxs-lookup"><span data-stu-id="e5cba-155">Importing assets</span></span>
<span data-ttu-id="e5cba-156">La scène a l’air un peu vide pour le moment, mais vous allez y remédier en important les ressources prêtes à l’emploi dans le projet.</span><span class="sxs-lookup"><span data-stu-id="e5cba-156">The scene is looking a bit empty at the moment, but you'll fix that by importing the ready-made assets into the project.</span></span>

1. <span data-ttu-id="e5cba-157">Téléchargez et décompressez le dossier des ressources [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) avec [7-zip](https://www.7-zip.org/).</span><span class="sxs-lookup"><span data-stu-id="e5cba-157">Download and unzip the [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) assets folder using [7-zip](https://www.7-zip.org/).</span></span>

2. <span data-ttu-id="e5cba-158">Sélectionnez **Add New > New Folder** à partir du **Content Browser** et nommez ce dossier **ChessAssets**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-158">Select **Add New > New Folder** from the **Content Browser** and name it **ChessAssets**.</span></span> 
    * <span data-ttu-id="e5cba-159">Double-cliquez sur le nouveau dossier où vous allez importer les ressources 3D.</span><span class="sxs-lookup"><span data-stu-id="e5cba-159">Double-click the new folder where you'll import the 3D assets.</span></span>

![Afficher ou masquer le panneau des sources](images/unreal-uxt/2-showhidesources.PNG)

3. <span data-ttu-id="e5cba-161">Sélectionnez **Import** à partir du **Content Browser**, sélectionnez tous les éléments inclus dans le dossier des ressources décompressé, puis cliquez sur **Open**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-161">Select **Import** from the **Content Browser**, select all the items in the unzipped assets folder and click **Open**.</span></span> 
    * <span data-ttu-id="e5cba-162">Les ressources incluent les maillages d’objets 3D pour l’échiquier et les pièces au format FBX ainsi que les cartes de texture au format TGA que vous allez utiliser pour les matériaux.</span><span class="sxs-lookup"><span data-stu-id="e5cba-162">Assets include the 3D object meshes for the chess board and pieces in FBX format and texture maps in TGA format that you'll use to for materials.</span></span>  

4. <span data-ttu-id="e5cba-163">Lorsque la fenêtre FBX Import Options s’affiche, développez la section **Material** et affectez à **Material Import Method** la valeur **Do Not Create Material**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-163">When the FBX Import Options window pops up, expand the **Material** section and change **Material Import Method** to **Do Not Create Material**.</span></span>
    * <span data-ttu-id="e5cba-164">Sélectionnez **Import All**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-164">Select **Import All**.</span></span>

![Options d’importation FBX](images/unreal-uxt/2-nocreatemat.PNG)

<span data-ttu-id="e5cba-166">C’est tout ce que vous devez faire pour les ressources.</span><span class="sxs-lookup"><span data-stu-id="e5cba-166">That's all you need to do for the assets.</span></span> <span data-ttu-id="e5cba-167">Votre prochaine série de tâches consiste à créer les composants de l’application avec des blueprints.</span><span class="sxs-lookup"><span data-stu-id="e5cba-167">Your next set of tasks is to create the building blocks of the application with blueprints.</span></span>

## <a name="adding-blueprints"></a><span data-ttu-id="e5cba-168">Ajout de blueprints</span><span class="sxs-lookup"><span data-stu-id="e5cba-168">Adding blueprints</span></span>

1. <span data-ttu-id="e5cba-169">Sélectionnez **Add New > New Folder** dans le **Content Browser** et nommez ce dossier **Blueprints**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-169">Select **Add New > New Folder** in the **Content Browser** and name it **Blueprints**.</span></span> 

> [!NOTE]
> <span data-ttu-id="e5cba-170">Si vous ne connaissez pas les [blueprints](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html), il s’agit de ressources spéciales qui fournissent une interface basée sur des nœuds pour créer des types d’acteurs et d’événements au niveau des scripts.</span><span class="sxs-lookup"><span data-stu-id="e5cba-170">If you're new to [blueprints](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html), they're special assets that provide a node-based interface for creating new types of Actors and script level events.</span></span> 

2. <span data-ttu-id="e5cba-171">Double-cliquez dans le dossier **Blueprints**, puis cliquez avec le bouton droit et sélectionnez **Blueprint Class**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-171">Double-click into the **Blueprints** folder, then right-click and select **Blueprint Class**.</span></span>         
    * <span data-ttu-id="e5cba-172">Sélectionnez **Actor** et nommez le blueprint **Board**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-172">Select **Actor** and name the blueprint **Board**.</span></span> 

![Sélectionner une classe parente pour votre blueprint](images/unreal-uxt/2-bpparent.PNG)

<span data-ttu-id="e5cba-174">Le nouveau blueprint **Board** apparaît maintenant dans le dossier **Blueprints**, comme l’illustre la capture d’écran suivante.</span><span class="sxs-lookup"><span data-stu-id="e5cba-174">The new **Board** blueprint now shows up in the **Blueprints** folder as seen in the following screenshot.</span></span> 

![Le nouveau blueprint Board](images/unreal-uxt/2-bpboard.PNG)

<span data-ttu-id="e5cba-176">Vous êtes fin prêt pour commencer à ajouter des matériaux aux objets créés.</span><span class="sxs-lookup"><span data-stu-id="e5cba-176">You're all set to start adding materials to the created objects.</span></span>

## <a name="working-with-materials"></a><span data-ttu-id="e5cba-177">Utilisation de matériaux</span><span class="sxs-lookup"><span data-stu-id="e5cba-177">Working with materials</span></span>
<span data-ttu-id="e5cba-178">Les objets que vous avez créés sont gris par défaut, ce qui n’est pas très agréable à regarder.</span><span class="sxs-lookup"><span data-stu-id="e5cba-178">The objects you've created are default grey, which isn't much fun to look at.</span></span> <span data-ttu-id="e5cba-179">L’ajout de matériaux et de maillages à vos objets constitue la dernière série de tâches de ce tutoriel.</span><span class="sxs-lookup"><span data-stu-id="e5cba-179">Adding materials and meshes to your objects is the last set of tasks in this tutorial.</span></span>

1. <span data-ttu-id="e5cba-180">Double-cliquez sur **Board** pour ouvrir l’éditeur de blueprint.</span><span class="sxs-lookup"><span data-stu-id="e5cba-180">Double-click **Board** to open the blueprint editor.</span></span> 

2. <span data-ttu-id="e5cba-181">Sélectionnez **Add Component > Scene** dans le panneau **Components** et nommez-le composant **Root**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-181">Select **Add Component > Scene** from the **Components** panel and name it **Root**.</span></span> <span data-ttu-id="e5cba-182">Notez que **Root** apparaît en tant qu’enfant de **DefaultSceneRoot** dans la capture d’écran ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="e5cba-182">Notice that **Root** shows up as a child of **DefaultSceneRoot** in the screenshot below:</span></span>

![Remplacement de root dans le blueprint](images/unreal-uxt/2-root-blueprint.PNG)


3. <span data-ttu-id="e5cba-184">Cliquez et faites glisser **Root** sur **DefaultSceneRoot** pour le remplacer et vous débarrasser de la sphère dans la fenêtre d’affichage.</span><span class="sxs-lookup"><span data-stu-id="e5cba-184">Click-and-drag **Root** onto **DefaultSceneRoot** to replace it and get rid of the sphere in the viewport.</span></span> 

![Remplacement de la racine](images/unreal-uxt/2-root.PNG)


4. <span data-ttu-id="e5cba-186">Sélectionnez **Add Component > Static Mesh** dans le panneau **Components** et nommez le composant **SM_Board**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-186">Select **Add Component > Static Mesh** from the **Components** panel and name it **SM_Board**.</span></span> <span data-ttu-id="e5cba-187">Il apparaît en tant qu’objet enfant sous **Root**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-187">It will appear as a child object under **Root**.</span></span>

![Ajout d’un maillage statique](images/unreal-uxt/2-sm-board.PNG)

4. <span data-ttu-id="e5cba-189">Sélectionnez **SM_Board**, faites défiler vers le bas jusqu’à la section **Static Mesh** du panneau **Details**, puis sélectionnez **ChessBoard** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="e5cba-189">Select **SM_Board**, scroll down to the **Static Mesh** section of the **Details** panel, and select **ChessBoard** from the dropdown.</span></span> 

![Le maillage de l’échiquier dans la fenêtre d’affichage](images/unreal-uxt/2-sm-board-view.PNG)

5.  <span data-ttu-id="e5cba-191">Toujours dans le panneau **Details**, développez la section **Materials**, puis sélectionnez **Create New Asset > Material** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="e5cba-191">Still in the **Details** panel, expand the **Materials** section and select **Create New Asset > Material** from the dropdown.</span></span> 
    * <span data-ttu-id="e5cba-192">Nommez le matériau **M_ChessBoard** et enregistrez-le dans le dossier **ChessAssets**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-192">Name the material **M_ChessBoard** and save it to the **ChessAssets** folder.</span></span> 

![Créer un matériau](images/unreal-uxt/2-newmat.PNG)

6.  <span data-ttu-id="e5cba-194">Double-cliquez sur l’image du matériau **M_ChessBoard** pour ouvrir l’éditeur de matériau.</span><span class="sxs-lookup"><span data-stu-id="e5cba-194">Double-click the **M_ChessBoard** material imaged to open the Material Editor.</span></span> 

![Ouvrir l’éditeur de matériau](images/unreal-uxt/2-material-editor.PNG)

7. <span data-ttu-id="e5cba-196">Dans l’éditeur de matériau, cliquez avec le bouton droit et recherchez **Texture Sample**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-196">In the Material Editor, right-click and search for **Texture Sample**.</span></span> 
    * <span data-ttu-id="e5cba-197">Développez la section **Material Expression Texture Base** dans le panneau **Details** et affectez à **Texture** la valeur **ChessBoard_Albedo**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-197">Expand the **Material Expression Texture Base** section in the **Details** panel and set **Texture** to **ChessBoard_Albedo**.</span></span> 
    * <span data-ttu-id="e5cba-198">Faites glisser le repère de sortie **RGB** vers le repère Base Color de **M_ChessBoard**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-198">Drag the **RGB** output pin to the Base Color pin of **M_ChessBoard**.</span></span> 

![Définir la couleur de base](images/unreal-uxt/2-boardalbedomat.PNG)

8.  <span data-ttu-id="e5cba-200">Répétez l’étape précédente 4 fois de plus pour créer quatre autres nœuds **Texture Sample** avec les paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="e5cba-200">Repeat the previous step 4 more times to create four more **Texture Sample** nodes with the following settings:</span></span>
    * <span data-ttu-id="e5cba-201">Affectez à **Texture** la valeur **ChessBoard_AO** et liez le repère **RGB** au repère **Ambient Occlusion**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-201">Set **Texture** to **ChessBoard_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="e5cba-202">Affectez à **Texture** la valeur **ChessBoard_Metal** et liez le repère **RGB** au repère **Metallic**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-202">Set **Texture** to **ChessBoard_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="e5cba-203">Affectez à **Texture** la valeur **ChessBoard_Normal** et liez le repère **RGB** au repère **Normal**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-203">Set **Texture** to **ChessBoard_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="e5cba-204">Affectez à **Texture** la valeur **ChessBoard_Rough** et liez le repère **RGB** au repère **Roughness**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-204">Set **Texture** to **ChessBoard_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="e5cba-205">Cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-205">Click **Save**.</span></span> 

![Raccorder les textures restantes](images/unreal-uxt/2-boardmat.PNG)

<span data-ttu-id="e5cba-207">Vérifiez que la configuration de votre matériau ressemble à la capture d’écran ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="e5cba-207">Make sure your material setup looks like the above screenshot before continuing.</span></span>

## <a name="populating-the-scene"></a><span data-ttu-id="e5cba-208">Remplissage de la scène</span><span class="sxs-lookup"><span data-stu-id="e5cba-208">Populating the scene</span></span>
<span data-ttu-id="e5cba-209">Si vous revenez au blueprint **Board**, vous voyez que le matériau que vous venez de créer a été appliqué.</span><span class="sxs-lookup"><span data-stu-id="e5cba-209">If you go back to the **Board** blueprint, you'll see that the material you just created has been applied.</span></span> <span data-ttu-id="e5cba-210">Il ne vous reste plus qu’à installer la scène !</span><span class="sxs-lookup"><span data-stu-id="e5cba-210">All that's left is setting up the scene!</span></span> <span data-ttu-id="e5cba-211">Pour commencer, modifiez les propriétés suivantes pour vous assurer que l’échiquier est de taille raisonnable et qu’il est correctement incliné lorsqu’il est placé dans la scène :</span><span class="sxs-lookup"><span data-stu-id="e5cba-211">First, change the following properties to make sure the board is a reasonable size and angled correctly when it's placed in the scene:</span></span>
1.  <span data-ttu-id="e5cba-212">Affectez à **Scale** la valeur **(0,05, 0,05, 0,05)** et à **Z Rotation** la valeur **90**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-212">Set **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span> 
    * <span data-ttu-id="e5cba-213">Cliquez sur **Compile** dans la barre d’outils supérieure, puis sur **Save** pour revenir à la fenêtre Main.</span><span class="sxs-lookup"><span data-stu-id="e5cba-213">Click **Compile** in the top toolbar, then **Save** and return to the Main window.</span></span> 

![Échiquier avec un matériau appliqué](images/unreal-uxt/2-chessboard.PNG)

2.  <span data-ttu-id="e5cba-215">Cliquez avec le bouton droit sur **Cube > Edit > Delete**, puis faites glisser **Board** depuis le **Content Browser** dans la fenêtre d’affichage.</span><span class="sxs-lookup"><span data-stu-id="e5cba-215">Right-click **Cube > Edit > Delete** and drag **Board** from the **Content Browser** into the viewport.</span></span> 
    * <span data-ttu-id="e5cba-216">Affectez à **Location** les valeurs **X = 80**, **Y = 0** et **Z = -20**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-216">Set **Location** to **X = 80**, **Y = 0**, and **Z = -20**.</span></span> 

3.  <span data-ttu-id="e5cba-217">Sélectionnez le bouton **Play** pour visualiser votre nouvel échiquier dans le niveau.</span><span class="sxs-lookup"><span data-stu-id="e5cba-217">Select the **Play** button to view your new board in the level.</span></span> <span data-ttu-id="e5cba-218">Appuyez sur **Échap** pour revenir à l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="e5cba-218">Press **Esc** to return to the editor.</span></span> 

<span data-ttu-id="e5cba-219">À présent, vous allez suivre les mêmes étapes pour créer une pièce de jeu d’échecs que celles que vous avez effectuées pour l’échiquier :</span><span class="sxs-lookup"><span data-stu-id="e5cba-219">Now you'll follow the same steps to create a chess piece as you did with the board:</span></span>

1. <span data-ttu-id="e5cba-220">Accédez au dossier **Blueprints**, cliquez avec le bouton droit et sélectionnez **Blueprint Class**, puis choisissez **Actor**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-220">Go to the **Blueprints** folder, right-click, and select **Blueprint Class** and choose **Actor**.</span></span> <span data-ttu-id="e5cba-221">Nommez cet acteur **WhiteKing**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-221">Name the actor **WhiteKing**.</span></span>

2. <span data-ttu-id="e5cba-222">Double-cliquez sur **WhiteKing** pour l’ouvrir dans l’éditeur de blueprint, sélectionnez **Add Component > Scene** et nommez-le **Root**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-222">Double-click **WhiteKing** to open it in the Blueprint Editor, select **Add Component > Scene** and name it **Root**.</span></span> 
    * <span data-ttu-id="e5cba-223">Glissez-déposez **Root** dans **DefaultSceneRoot** pour le remplacer.</span><span class="sxs-lookup"><span data-stu-id="e5cba-223">Drag-and-drop **Root** onto **DefaultSceneRoot** to replace it.</span></span> 

3. <span data-ttu-id="e5cba-224">Cliquez sur **Add Component > Static Mesh** et nommez ce composant **SM_King**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-224">Click **Add Component > Static Mesh** and name it **SM_King**.</span></span> 
    * <span data-ttu-id="e5cba-225">Affectez à **Static Mesh** la valeur **Chess_King** et à **Material** la valeur d’un nouveau matériau appelé **M_ChessWhite** dans le panneau Details.</span><span class="sxs-lookup"><span data-stu-id="e5cba-225">Set **Static Mesh** to **Chess_King** and **Material** to a new Material called **M_ChessWhite** in the Details panel.</span></span> 

4. <span data-ttu-id="e5cba-226">Ouvrez **M_ChessWhite** dans l’éditeur de matériau et raccordez les nœuds **Texture Sample** suivants aux éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="e5cba-226">Open **M_ChessWhite** in the Material editor and hook up the following **Texture Sample** nodes to the following:</span></span>
   * <span data-ttu-id="e5cba-227">Affectez à **Texture** la valeur **ChessWhite_Albedo** et liez le repère **RGB** au repère **Base Color**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-227">Set **Texture** to **ChessWhite_Albedo** and link the **RGB** to the **Base Color** pin.</span></span>
    * <span data-ttu-id="e5cba-228">Affectez à **Texture** la valeur **ChessWhite_AO** et liez le repère **RGB** au repère **Ambient Occlusion**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-228">Set **Texture** to **ChessWhite_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="e5cba-229">Affectez à **Texture** la valeur **ChessWhite_Metal** et liez le repère **RGB** au repère **Metallic**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-229">Set **Texture** to **ChessWhite_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="e5cba-230">Affectez à **Texture** la valeur **ChessWhite_Normal** et liez le repère **RGB** au repère **Normal**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-230">Set **Texture** to **ChessWhite_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="e5cba-231">Affectez à **Texture** la valeur **ChessWhite_Rough** et liez le repère **RGB** au repère **Roughness**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-231">Set **Texture** to **ChessWhite_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="e5cba-232">Cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-232">Click **Save**.</span></span> 

<span data-ttu-id="e5cba-233">Votre matériau **M_ChessKing** doit ressembler à l’image suivante avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="e5cba-233">Your **M_ChessKing** material should look like the following image before continuing.</span></span>

![Créer le matériau pour le roi](images/unreal-uxt/2-chesskingmat.PNG)

<span data-ttu-id="e5cba-235">Vous y êtes presque, il vous suffit d’ajouter la nouvelle pièce à la scène :</span><span class="sxs-lookup"><span data-stu-id="e5cba-235">You're almost there, just need to add the new chess piece into the scene:</span></span> 

1. <span data-ttu-id="e5cba-236">Ouvrez le blueprint **WhiteKing** et affectez à **Scale** la valeur **(0,05, 0,05, 0,05)** et à **Z Rotation** la valeur **90**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-236">Open the **WhiteKing** blueprint and change the **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span>
    * <span data-ttu-id="e5cba-237">Compilez et enregistrez votre blueprint, puis revenez à la fenêtre principale.</span><span class="sxs-lookup"><span data-stu-id="e5cba-237">Compile and save your blueprint, then head back to the main window.</span></span> 

2.  <span data-ttu-id="e5cba-238">Faites glisser **WhiteKing** dans la fenêtre d’affichage, basculez vers le panneau **World Outliner**, faites glisser **WhiteKing** sur **Board** pour en faire un objet enfant.</span><span class="sxs-lookup"><span data-stu-id="e5cba-238">Drag **WhiteKing** into the viewport, switch to the **World Outliner** panel drag **WhiteKing** onto **Board** to make it a child object.</span></span>

![World Outliner](images/unreal-uxt/2-child.PNG)

3.  <span data-ttu-id="e5cba-240">Dans le panneau **Details** sous **Transform**, affectez au paramètre **Location** de **WhiteKing** les valeurs **X = -26**, **Y = 4** et **Z = 0**.</span><span class="sxs-lookup"><span data-stu-id="e5cba-240">In the **Details** panel under **Transform**, set **WhiteKing**'s **Location** to **X = -26**, **Y = 4**, and **Z = 0**.</span></span>

<span data-ttu-id="e5cba-241">C’est terminé !</span><span class="sxs-lookup"><span data-stu-id="e5cba-241">That's a wrap!</span></span> <span data-ttu-id="e5cba-242">Sélectionnez **Play** pour voir votre niveau rempli en action, puis appuyez sur **Échap** quand vous êtes prêt à quitter.</span><span class="sxs-lookup"><span data-stu-id="e5cba-242">Select **Play** to see your populated level in action, and press **Esc** when you're ready to exit.</span></span> <span data-ttu-id="e5cba-243">Vous avez abordé de nombreux points liés à la création d’un projet simple, mais vous êtes maintenant prêt à passer à la partie suivante de la série : la configuration pour la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="e5cba-243">You covered a lot of ground just creating a simple project, but now you're ready to move on to the next part of the series: setting up for mixed reality.</span></span> 

[<span data-ttu-id="e5cba-244">Section suivante : 3. Configurer votre projet pour la réalité mixte</span><span class="sxs-lookup"><span data-stu-id="e5cba-244">Next Section: 3. Set up your project for mixed reality</span></span>](unreal-uxt-ch3.md)