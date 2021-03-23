---
title: Création de votre première application HoloLens Unreal
description: Découvrez comment configurer correctement un projet Unreal avec des objets de scène et des interactions d’entrée pour le développement de réalité mixte HoloLens.
author: hferrone
ms.author: safarooq
ms.date: 01/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, éditeur Unreal, UE4, HoloLens, HoloLens 2, réalité mixte, développement, documentation, guides, fonctionnalités, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, portage, mise à niveau
ms.openlocfilehash: 467987f69b50c0ec635c99899d6bcecab5a62af0
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "99421428"
---
# <a name="creating-your-first-hololens-unreal-application"></a><span data-ttu-id="d7e4b-104">Création de votre première application HoloLens Unreal</span><span class="sxs-lookup"><span data-stu-id="d7e4b-104">Creating your first HoloLens Unreal application</span></span>

<span data-ttu-id="d7e4b-105">Ce guide vous permet de créer votre première application de réalité mixte s’exécutant sur HoloLens dans Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-105">This guide will walk you through getting your first Mixed Reality app running on the HoloLens in Unreal Engine.</span></span> <span data-ttu-id="d7e4b-106">Dans la tradition de « Hello World », vous allez créer une application simple qui affiche un cube à l’écran.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-106">In the tradition of "Hello World", you'll create a simple app that displays a cube on the screen.</span></span> <span data-ttu-id="d7e4b-107">Pour la rendre plus utile, vous allez également créer votre premier geste pour faire pivoter le cube et pour quitter l’application.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-107">To make it more useful, you'll also create your first gesture to rotate the cube and quit the application.</span></span> 

## <a name="objectives"></a><span data-ttu-id="d7e4b-108">Objectifs</span><span class="sxs-lookup"><span data-stu-id="d7e4b-108">Objectives</span></span>

* <span data-ttu-id="d7e4b-109">Démarrer un projet HoloLens</span><span class="sxs-lookup"><span data-stu-id="d7e4b-109">Start a HoloLens Project</span></span>
* <span data-ttu-id="d7e4b-110">Activer les plug-ins corrects</span><span class="sxs-lookup"><span data-stu-id="d7e4b-110">Enable the correct plugins</span></span>
* <span data-ttu-id="d7e4b-111">Créer une ressource de données ARSessionConfig</span><span class="sxs-lookup"><span data-stu-id="d7e4b-111">Create an ARSessionConfig Data Asset</span></span>
* <span data-ttu-id="d7e4b-112">Configurer les entrées de geste</span><span class="sxs-lookup"><span data-stu-id="d7e4b-112">Set up gesture inputs</span></span>
* <span data-ttu-id="d7e4b-113">Créer un niveau de base</span><span class="sxs-lookup"><span data-stu-id="d7e4b-113">Build a basic level</span></span>
* <span data-ttu-id="d7e4b-114">Implémenter un geste de pincement</span><span class="sxs-lookup"><span data-stu-id="d7e4b-114">Implement a pinch gesture</span></span>

## <a name="creating-a-new-project"></a><span data-ttu-id="d7e4b-115">Création d’un projet</span><span class="sxs-lookup"><span data-stu-id="d7e4b-115">Creating a new project</span></span>

<span data-ttu-id="d7e4b-116">La première chose dont vous avez besoin est un projet avec lequel travailler.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-116">The first thing you need is a project to work with.</span></span> <span data-ttu-id="d7e4b-117">Si vous commencez juste à développer dans Unreal, vous devez [télécharger les fichiers de prise en charge](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) auprès d’Epic Launcher.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-117">If you're a first-time Unreal developer, you'll need to [download supporting files](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) from the Epic Launcher.</span></span>

1. <span data-ttu-id="d7e4b-118">Lancer Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="d7e4b-118">Launch Unreal Engine</span></span>
2. <span data-ttu-id="d7e4b-119">Dans **New Project Categories**, sélectionnez **Games**, puis cliquez sur **Next** :</span><span class="sxs-lookup"><span data-stu-id="d7e4b-119">In the **New Project Categories**, select **Games** and click **Next**:</span></span>

![Fenêtre des projets récents ouverte avec Games mis en évidence](images/unreal-quickstart-img-01.png)

3. <span data-ttu-id="d7e4b-121">Sélectionnez le modèle **Blank**, puis cliquez sur **Next** :</span><span class="sxs-lookup"><span data-stu-id="d7e4b-121">Select the **Blank** template and click **Next**:</span></span>

![Fenêtre du navigateur de projet Unreal avec le modèle Blank mis en évidence](images/unreal-quickstart-img-02.png)

4. <span data-ttu-id="d7e4b-123">Dans **Project Settings**, définissez **C++, Scalable 3D or 2D, Mobile/Tablet** et **No Starter Content**, puis choisissez un emplacement d’enregistrement et cliquez sur **Create Project**.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-123">In the **Project Settings**, set **C++, Scalable 3D or 2D, Mobile/Tablet**, and **No Starter Content**, then choose a save location and click **Create Project**</span></span>

> [!NOTE] 
> <span data-ttu-id="d7e4b-124">Vous utilisez un projet C++ au lieu d’un projet Blueprint pour être prêt à utiliser le plug-in OpenXR ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-124">You're using a C++ rather than a Blueprint project in order to be ready to use the OpenXR plugin later.</span></span> <span data-ttu-id="d7e4b-125">Ce guide de démarrage rapide utilise le plug-in OpenXR par défaut qui est fourni avec Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-125">This QuickStart uses the default OpenXR plugin that comes with Unreal Engine.</span></span> <span data-ttu-id="d7e4b-126">Il est cependant recommandé de télécharger et d’utiliser le plug-in Microsoft OpenXR officiel.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-126">However, downloading and using the official Microsoft OpenXR plugin is recommended.</span></span> <span data-ttu-id="d7e4b-127">Cela nécessite que le projet soit un projet C++.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-127">That requires the project to be a C++ project.</span></span>

![Fenêtre des paramètres de projet avec les choix pour le projet, les performances, la plateforme cible et le contenu au démarrage mis en évidence](images/unreal-quickstart-img-03.png)

<span data-ttu-id="d7e4b-129">Votre nouveau projet doit s’ouvrir automatiquement dans l’éditeur Unreal, ce qui signifie que vous êtes prêt à passer à la section suivante.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-129">Your new project should open up automatically in the Unreal editor, which means you're ready for the next section.</span></span>

## <a name="enabling-required-plugins"></a><span data-ttu-id="d7e4b-130">Activation des plug-ins nécessaires</span><span class="sxs-lookup"><span data-stu-id="d7e4b-130">Enabling required plugins</span></span>

<span data-ttu-id="d7e4b-131">Vous devez activer deux plug-ins pour pouvoir commencer à ajouter des objets à la scène.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-131">You'll need to enable two plugins before you can start adding objects to the scene.</span></span>

1. <span data-ttu-id="d7e4b-132">Ouvrez **Edit > Plugins** et sélectionnez **Augmented Reality** dans la liste des options prédéfinies.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-132">Open **Edit > Plugins** and select **Augmented Reality** from the built-in options list.</span></span>
* <span data-ttu-id="d7e4b-133">Faites défiler vers le bas jusqu’à **HoloLens** et cochez la case **Enabled**.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-133">Scroll down to **HoloLens** and check **Enabled**</span></span>

![Fenêtre des plug-ins avec la section de la réalité augmentée ouverte et HoloLens mis en évidence](images/unreal-quickstart-img-04.png)

2. <span data-ttu-id="d7e4b-135">Tapez **OpenXR** dans la zone de recherche en haut à droite et activez les plug-ins **OpenXR** et **OpenXRMsftHandInteraction** :</span><span class="sxs-lookup"><span data-stu-id="d7e4b-135">Type **OpenXR** in the search box at the top right and enable the **OpenXR** and **OpenXRMsftHandInteraction** plugins:</span></span>

![Fenêtre des plug-ins avec OpenXR activé](images/unreal-quickstart-img-05.jpg)

![Fenêtre des plug-ins avec Open XR Msft Hand Interaction activé](images/unreal-quickstart-img-06.jpg)

3. <span data-ttu-id="d7e4b-138">Redémarrer votre éditeur</span><span class="sxs-lookup"><span data-stu-id="d7e4b-138">Restart your editor</span></span>

> [!NOTE]
> <span data-ttu-id="d7e4b-139">Ce tutoriel utilise OpenXR, mais les deux plug-ins que vous avez installés ci-dessus ne fournissent actuellement pas l’ensemble complet de fonctionnalités pour le développement HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-139">This tutorial uses OpenXR, but the two plugins you've installed above don't currently provide the full feature set for HoloLens development.</span></span> <span data-ttu-id="d7e4b-140">Le plug-in HandInteraction sera suffisant pour le geste de pincement que vous allez utiliser plus tard, mais si vous voulez aller plus loin, vous devez [télécharger le plug-in OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span><span class="sxs-lookup"><span data-stu-id="d7e4b-140">The HandInteraction plugin will suffice for the "Pinch" gesture you'll use later, but if you want to go beyond the basics you'll need to [download the OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span></span>

<span data-ttu-id="d7e4b-141">Une fois les plug-ins activés, vous pouvez vous concentrer sur le remplissage du contenu.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-141">With the plugins enabled, you can focus on filling it with content.</span></span>

## <a name="creating-a-level"></a><span data-ttu-id="d7e4b-142">Création d’un niveau</span><span class="sxs-lookup"><span data-stu-id="d7e4b-142">Creating a level</span></span>

<span data-ttu-id="d7e4b-143">La tâche suivante consiste à créer une configuration de joueur avec un point de départ, et un cube pour la référence et la mise à l’échelle.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-143">Your next task is to create a player setup with a starting point and a cube for reference and scale.</span></span>

1. <span data-ttu-id="d7e4b-144">Sélectionnez **File > New Level**, puis choisissez **Empty Level**.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-144">Select **File > New Level** and choose **Empty Level**.</span></span> <span data-ttu-id="d7e4b-145">La scène par défaut dans la fenêtre d’affichage doit maintenant être vide.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-145">The default scene in the viewport should now be empty</span></span>
2. <span data-ttu-id="d7e4b-146">Sous l’onglet **Mode**, sélectionnez **Basic**, puis faites glisser **PlayerStart** dans la scène.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-146">From the **Modes** tab, select **Basic** and drag **PlayerStart** into the scene</span></span>
* <span data-ttu-id="d7e4b-147">Sous l’onglet **Details**, définissez **Location** sur **X = 0, Y = 0** et **Z = 0** pour placer l’utilisateur au centre de la scène lors du démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-147">In the **Details** tab, set **Location** to **X = 0, Y = 0,** and **Z = 0** to place the user at the center of the scene when the app starts</span></span>

![Scène de l’éditeur Unreal avec l’emplacement et le joueur ajoutés](images/unreal-quickstart-img-07.png)

3. <span data-ttu-id="d7e4b-149">Sous l’onglet **Basic**, faites glisser un **Cube** dans la scène.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-149">From the **Basic** tab, drag a **Cube** into the scene</span></span>
* <span data-ttu-id="d7e4b-150">Définissez **Location** pour le cube sur **X = 50, Y = 0** et **Z = 0** pour positionner le cube à 50 cm du joueur au démarrage.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-150">Set the cube's **Location** to **X = 50, Y = 0**, and **Z = 0** to position the cube 50 cm away from the player at start</span></span>
* <span data-ttu-id="d7e4b-151">Changez **Scale** pour le cube en **X = 0,2, Y = 0,2** et **Z = 0,2**.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-151">Change  the cube's **Scale** to **X = 0.2, Y = 0.2**, and **Z = 0.2**</span></span> 

<span data-ttu-id="d7e4b-152">Vous ne pouvez pas voir le cube, sauf si vous ajoutez une lumière à votre scène, ce qui constitue votre dernière tâche avant de tester la scène.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-152">You can't see the cube unless you add a light to your scene, which is your last task before testing the scene.</span></span>

4. <span data-ttu-id="d7e4b-153">Dans le panneau **Modes**, passez à l’onglet **Lights**, puis faites glisser une **Directional Light** dans la scène.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-153">In the **Modes** panel, switch to the **Lights** tab and drag a **Directional Light** into the scene</span></span>
* <span data-ttu-id="d7e4b-154">Positionnez la lumière au-dessus de **PlayerStart** pour pouvoir la voir.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-154">Position the light above **PlayerStart** so you can see it</span></span>

![Scène de l’éditeur Unreal avec le cube et la lumière directionnelle ajoutés](images/unreal-quickstart-img-08.png)

5. <span data-ttu-id="d7e4b-156">Accédez à **File > Save Current**, nommez votre niveau **Main**, puis sélectionnez **Save**.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-156">Go to **File > Save Current**, name your level **Main**, and select **Save**</span></span>

<span data-ttu-id="d7e4b-157">Une fois la scène définie, appuyez sur **Play** dans la barre d’outils pour voir votre cube en action !</span><span class="sxs-lookup"><span data-stu-id="d7e4b-157">With the scene set, press **Play** in the toolbar to see your cube in action!</span></span> <span data-ttu-id="d7e4b-158">Lorsque vous avez fini d’admirer votre travail, appuyez sur Échap pour arrêter l’application.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-158">When you're finished admiring your work, press Esc to stop the application.</span></span>

![Scène en mode lecture avec le cube au milieu de l’écran](images/unreal-quickstart-img-09.png)

<span data-ttu-id="d7e4b-160">Maintenant que la scène est configurée, préparons-la pour quelques interactions simples dans AR.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-160">Now that the scene is set up, lets get it ready for some basic interactions in AR.</span></span> <span data-ttu-id="d7e4b-161">Tout d’abord, vous devez créer une session AR, et vous pouvez aussi ajouter des blueprints pour permettre une interaction manuelle.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-161">First, you need to create an AR Session and can add blueprints to enable hand interaction.</span></span>

## <a name="adding-a-session-asset"></a><span data-ttu-id="d7e4b-162">Ajout d’une ressource de session</span><span class="sxs-lookup"><span data-stu-id="d7e4b-162">Adding a session asset</span></span>

<span data-ttu-id="d7e4b-163">Les sessions de réalité augmentée n’arrivent pas toutes seules.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-163">AR sessions in Unreal don't happen by themselves.</span></span> <span data-ttu-id="d7e4b-164">Pour utiliser une session, vous devez créer une ressource de données ARSessionConfig, ce qui est d’ailleurs votre tâche suivante :</span><span class="sxs-lookup"><span data-stu-id="d7e4b-164">To use a session, you need an ARSessionConfig data asset to work with, which is your next task:</span></span>

1. <span data-ttu-id="d7e4b-165">Dans le **Content Browser**, sélectionnez **Add New > Miscellaneous > Data Asset** et vérifiez que vous êtes au niveau du dossier Content racine.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-165">In the **Content Browser**, select **Add New > Miscellaneous > Data Asset** and make sure you're at the root Content folder level</span></span>
2. <span data-ttu-id="d7e4b-166">Sélectionnez **ARSessionConfig**, cliquez sur **Select**, puis nommez la ressource **ARSessionConfig** :</span><span class="sxs-lookup"><span data-stu-id="d7e4b-166">Select **ARSessionConfig**, click **Select**, and name the asset **ARSessionConfig**:</span></span>

![Fenêtre de sélection d’une classe de ressources de données ouverte avec la ressource de configuration de session AR mise en évidence](images/unreal-quickstart-img-10.png)

2. <span data-ttu-id="d7e4b-168">Double-cliquez sur **ARSessionConfig** pour l’ouvrir, choisissez **Save** avec toutes les valeurs par défaut, puis revenez à la fenêtre principale :</span><span class="sxs-lookup"><span data-stu-id="d7e4b-168">Double-click **ARSessionConfig** to open it, **Save** with all default settings, and return to the Main window:</span></span>

![Fenêtre des détails des ressources de configuration de session AR](images/unreal-quickstart-img-11.png)

<span data-ttu-id="d7e4b-170">Une fois cette opération effectuée, l’étape suivante consiste à faire en sorte que la session de réalité augmentée démarre et s’arrête quand le niveau se charge et se termine.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-170">With that done, your next step is to make sure the AR session starts and stops when the level loads and ends.</span></span> <span data-ttu-id="d7e4b-171">Unreal comprend un blueprint spécial appelé **Level Blueprint** (« Blueprint de niveau ») qui joue le rôle de graphe d’événements global à l’échelle du niveau.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-171">Luckily, Unreal has a special blueprint called a **Level Blueprint** that acts as a level-wide global event graph.</span></span> <span data-ttu-id="d7e4b-172">Le fait de connecter la ressource ARSessionConfig dans le blueprint de niveau garantit que la session de réalité augmentée se déclenchera juste au début du jeu.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-172">Connecting the ARSessionConfig asset in the Level Blueprint guarantees the AR session will fire right when the game starts playing.</span></span>

3. <span data-ttu-id="d7e4b-173">Dans la barre d’outils de l’éditeur, sélectionnez **Blueprints > Open Level Blueprint** :</span><span class="sxs-lookup"><span data-stu-id="d7e4b-173">From the editor toolbar, select **Blueprints > Open Level Blueprint**:</span></span>

![Menu Blueprint ouvert avec l’option Open Level Blueprint en évidence](images/unreal-quickstart-img-12.png)

4. <span data-ttu-id="d7e4b-175">Faites glisser le nœud d’exécution (la flèche pointant vers la gauche) en dehors de **Event BeginPlay**, puis relâchez.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-175">Drag the execution node (left-facing arrow icon) off **Event BeginPlay** and release</span></span>
* <span data-ttu-id="d7e4b-176">Recherchez le **nœud Start AR Session**, puis appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-176">Search for the **Start AR Session node** and hit enter</span></span>
* <span data-ttu-id="d7e4b-177">Cliquez sur la liste déroulante **Select Asset** sous **Session Config**, puis sélectionnez la ressource **ARSessionConfig**.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-177">Click the **Select Asset** dropdown under **Session Config** and choose the **ARSessionConfig** asset</span></span>

![Graphique de blueprint avec Event BeginPlay connecté à la fonction Start AR Session](images/unreal-quickstart-img-13.png)

5. <span data-ttu-id="d7e4b-179">Cliquez avec le bouton droit n’importe où dans l’EventGraph et créez un nœud **Event EndPlay**.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-179">Right-click anywhere in the EventGraph and create a new **Event EndPlay** node.</span></span> 
* <span data-ttu-id="d7e4b-180">Faites glisser la broche d’exécution et relâchez le bouton, puis recherchez le nœud **Stop AR Session** et appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-180">Drag the execution pin and release, then search for a **Stop AR Session** node and hit enter</span></span> 
* <span data-ttu-id="d7e4b-181">Cliquez sur **Compile**, puis sur **Save**, et revenez à la fenêtre principale.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-181">Hit **Compile**, then **Save** and return to the Main window</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d7e4b-182">Si la session de réalité augmentée est toujours en cours quand le niveau se termine, certaines fonctionnalités peuvent cesser de fonctionner si vous redémarrez votre application lors du streaming sur un casque.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-182">If the AR session is still running when the level ends, certain features may stop working if you restart your app while streaming to a headset.</span></span>

![Nœud Event EndPlay attaché à la fonction Stop AR Session](images/unreal-quickstart-img-14.png)

## <a name="setting-up-inputs"></a><span data-ttu-id="d7e4b-184">Configuration des entrées</span><span class="sxs-lookup"><span data-stu-id="d7e4b-184">Setting up inputs</span></span>

1. <span data-ttu-id="d7e4b-185">Sélectionnez **Edit > Project Settings**, puis accédez à **Engine > Input**.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-185">Select **Edit > Project Settings** and go to the **Engine > Input**</span></span>
2. <span data-ttu-id="d7e4b-186">Sélectionnez l’icône **+** à côté de **Action Mappings**, puis créez des actions **RightPinch** et **LeftPinch** :</span><span class="sxs-lookup"><span data-stu-id="d7e4b-186">Select the **+** icon next to **Action Mappings** and create **RightPinch** and **LeftPinch** actions:</span></span>

![Liaison des paramètres d’entrée avec les mappages des actions de pincement droit et gauche mis en évidence](images/unreal-quickstart-img-15.jpg)

3. <span data-ttu-id="d7e4b-188">Mappez les actions **RightPinch** et **LeftPinch** aux actions **OpenXR Msft Hand Interaction** correspondantes :</span><span class="sxs-lookup"><span data-stu-id="d7e4b-188">Map the **RightPinch** and **LeftPinch** actions the to the respective **OpenXR Msft Hand Interaction** actions:</span></span>

![Mappages d’actions avec les options Open XR Msft Hand Interaction en évidence](images/unreal-quickstart-img-16.jpg)

## <a name="setting-up-gestures"></a><span data-ttu-id="d7e4b-190">Configuration des gestes</span><span class="sxs-lookup"><span data-stu-id="d7e4b-190">Setting up gestures</span></span>

<span data-ttu-id="d7e4b-191">Maintenant que nous avons configuré les entrées, nous pouvons accéder à la partie intéressante : L’ajout de gestes !</span><span class="sxs-lookup"><span data-stu-id="d7e4b-191">Now that we have setup the inputs, we can get to the exciting part: Adding gestures!</span></span> <span data-ttu-id="d7e4b-192">Faisons pivoter le cube sur le pincement à droite et quitter l’application sur le pincement à gauche.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-192">Lets rotate the cube on the right pinch and quit the application on left pinch.</span></span>

1. <span data-ttu-id="d7e4b-193">Ouvrez le **Level Blueprint** et ajoutez un **InputAction RightPinch** et un **InputAction LeftPinch**.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-193">Open the **Level Blueprint** and add an **InputAction RightPinch** and **InputAction LeftPinch**</span></span>
* <span data-ttu-id="d7e4b-194">Connectez l’événement pincement droit à une **AddActorLocalRotation** avec votre **Cube**  comme cible, et **Delta Rotation** défini sur **X = 0, Y = 0** et **Z = 20**.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-194">Connect the right pinch event to an **AddActorLocalRotation** with your **Cube** as the target and **Delta Rotation** set to **X = 0, Y = 0**, and **Z = 20**.</span></span> <span data-ttu-id="d7e4b-195">Le cube va maintenant pivoter de 20 degrés chaque fois que vous pincez.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-195">The cube will now rotate by 20 degrees every time you pinch</span></span>
* <span data-ttu-id="d7e4b-196">Connectez l’événement de pincement gauche à **Quit Game**.</span><span class="sxs-lookup"><span data-stu-id="d7e4b-196">Connect the left pinch event to **Quit Game**</span></span>

![Blueprint de niveau ouvert avec des actions d’entrée pour les événements de pincement droit et gauche](images/unreal-quickstart-img-17.jpg)

2. <span data-ttu-id="d7e4b-198">Dans les paramètres **Transform** du cube, définissez **Mobility** sur **Movable** pour qu’il puisse se déplacer dynamiquement :</span><span class="sxs-lookup"><span data-stu-id="d7e4b-198">In the cube's **Transform** settings, set **Mobility** to **Movable** so it can move dynamically:</span></span>

![Paramètres de transformation avec la propriété de mobilité mis en évidence](images/unreal-quickstart-img-18.jpg)

<span data-ttu-id="d7e4b-200">À ce stade, vous êtes prêt à déployer et à tester l’application !</span><span class="sxs-lookup"><span data-stu-id="d7e4b-200">At this point, you're ready to deploy and test the application!</span></span>