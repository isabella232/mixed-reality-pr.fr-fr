---
title: Création d’un projet HoloLens
description: Découvrez comment configurer correctement un projet Unreal avec des objets de scène et des interactions d’entrée pour le développement de réalité mixte HoloLens.
author: hferrone
ms.author: safarooq
ms.date: 01/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, éditeur Unreal, UE4, HoloLens, HoloLens 2, réalité mixte, développement, documentation, guides, fonctionnalités, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, portage, mise à niveau
ms.openlocfilehash: 3b2b88ac897a8791fec1ca2942d0db34efcee598
ms.sourcegitcommit: be33fcda10d1cb98df90b428a923289933d42c77
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98672736"
---
# <a name="creating-a-hololens-project"></a><span data-ttu-id="38dd7-104">Création d’un projet HoloLens</span><span class="sxs-lookup"><span data-stu-id="38dd7-104">Creating a HoloLens project</span></span>

<span data-ttu-id="38dd7-105">La première chose dont vous avez besoin est un projet avec lequel travailler.</span><span class="sxs-lookup"><span data-stu-id="38dd7-105">The first thing you need is a project to work with.</span></span> <span data-ttu-id="38dd7-106">Si vous commencez juste à développer dans Unreal, vous devez [télécharger les fichiers de prise en charge](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) auprès d’Epic Launcher.</span><span class="sxs-lookup"><span data-stu-id="38dd7-106">If you're a first-time Unreal developer, you'll need to [download supporting files](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) from the Epic Launcher.</span></span>

1. <span data-ttu-id="38dd7-107">Lancer Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="38dd7-107">Launch Unreal Engine</span></span>
2. <span data-ttu-id="38dd7-108">Dans **New Project Categories**, sélectionnez **Games**, puis cliquez sur **Next** :</span><span class="sxs-lookup"><span data-stu-id="38dd7-108">In the **New Project Categories**, select **Games** and click **Next**:</span></span>

![Fenêtre des projets récents ouverte avec Games mis en évidence](images/unreal-quickstart-img-01.png)

3. <span data-ttu-id="38dd7-110">Sélectionnez le modèle **Blank**, puis cliquez sur **Next** :</span><span class="sxs-lookup"><span data-stu-id="38dd7-110">Select the **Blank** template and click **Next**:</span></span>

![Fenêtre du navigateur de projet Unreal avec le modèle Blank mis en évidence](images/unreal-quickstart-img-02.png)

4. <span data-ttu-id="38dd7-112">Dans **Project Settings**, définissez **C++, Scalable 3D or 2D, Mobile/Tablet** et **No Starter Content**, puis choisissez un emplacement d’enregistrement et cliquez sur **Create Project**.</span><span class="sxs-lookup"><span data-stu-id="38dd7-112">In the **Project Settings**, set **C++, Scalable 3D or 2D, Mobile/Tablet**, and **No Starter Content**, then choose a save location and click **Create Project**</span></span>

> [!NOTE] <span data-ttu-id="38dd7-113">Vous utilisez un projet C++ au lieu d’un projet Blueprint pour être prêt à utiliser le plug-in OpenXR ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="38dd7-113">You're using a C++ rather than a Blueprint project in order to be ready to use the OpenXR plugin later.</span></span> <span data-ttu-id="38dd7-114">Ce guide de démarrage rapide utilise le plug-in OpenXR par défaut qui est fourni avec Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="38dd7-114">This QuickStart uses the default OpenXR plugin that comes with Unreal Engine.</span></span> <span data-ttu-id="38dd7-115">Il est cependant recommandé de télécharger et d’utiliser le plug-in Microsoft OpenXR officiel.</span><span class="sxs-lookup"><span data-stu-id="38dd7-115">However, downloading and using the official Microsoft OpenXR plugin is recommended.</span></span> <span data-ttu-id="38dd7-116">Cela nécessite que le projet soit un projet C++.</span><span class="sxs-lookup"><span data-stu-id="38dd7-116">That requires the project to be a C++ project.</span></span>

![Fenêtre des paramètres de projet avec les choix pour le projet, les performances, la plateforme cible et le contenu au démarrage mis en évidence](images/unreal-quickstart-img-03.png)

<span data-ttu-id="38dd7-118">Votre nouveau projet doit s’ouvrir automatiquement dans l’éditeur Unreal, ce qui signifie que vous êtes prêt à passer à la section suivante.</span><span class="sxs-lookup"><span data-stu-id="38dd7-118">Your new project should open up automatically in the Unreal editor, which means you're ready for the next section.</span></span>

## <a name="enabling-required-plugins"></a><span data-ttu-id="38dd7-119">Activation des plug-ins nécessaires</span><span class="sxs-lookup"><span data-stu-id="38dd7-119">Enabling required plugins</span></span>

<span data-ttu-id="38dd7-120">Vous devez activer deux plug-ins pour pouvoir commencer à ajouter des objets à la scène.</span><span class="sxs-lookup"><span data-stu-id="38dd7-120">You'll need to enable two plugins before you can start adding objects to the scene.</span></span>

1. <span data-ttu-id="38dd7-121">Ouvrez **Edit > Plugins** et sélectionnez **Augmented Reality** dans la liste des options prédéfinies.</span><span class="sxs-lookup"><span data-stu-id="38dd7-121">Open **Edit > Plugins** and select **Augmented Reality** from the built-in options list.</span></span>
* <span data-ttu-id="38dd7-122">Faites défiler vers le bas jusqu’à **HoloLens** et cochez la case **Enabled**.</span><span class="sxs-lookup"><span data-stu-id="38dd7-122">Scroll down to **HoloLens** and check **Enabled**</span></span>

![Fenêtre des plug-ins avec la section de la réalité augmentée ouverte et HoloLens mis en évidence](images/unreal-quickstart-img-04.png)

2. <span data-ttu-id="38dd7-124">Tapez **OpenXR** dans la zone de recherche en haut à droite et activez les plug-ins **OpenXR** et **OpenXRMsftHandInteraction** :</span><span class="sxs-lookup"><span data-stu-id="38dd7-124">Type **OpenXR** in the search box at the top right and enable the **OpenXR** and **OpenXRMsftHandInteraction** plugins:</span></span>

![Fenêtre des plug-ins avec OpenXR activé](images/unreal-quickstart-img-05.jpg)

![Fenêtre des plug-ins avec Open XR Msft Hand Interaction activé](images/unreal-quickstart-img-06.jpg)

3. <span data-ttu-id="38dd7-127">Redémarrer votre éditeur</span><span class="sxs-lookup"><span data-stu-id="38dd7-127">Restart your editor</span></span>

> [!NOTE]
> <span data-ttu-id="38dd7-128">Ce tutoriel utilise OpenXR, mais les deux plug-ins que vous avez installés ci-dessus ne fournissent actuellement pas l’ensemble complet de fonctionnalités pour le développement HoloLens.</span><span class="sxs-lookup"><span data-stu-id="38dd7-128">This tutorial uses OpenXR, but the two plugins you've installed above don't currently provide the full feature set for HoloLens development.</span></span> <span data-ttu-id="38dd7-129">Le plug-in HandInteraction sera suffisant pour le geste de pincement que vous allez utiliser plus tard, mais si vous voulez aller plus loin, vous devez [télécharger le plug-in OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span><span class="sxs-lookup"><span data-stu-id="38dd7-129">The HandInteraction plugin will suffice for the "Pinch" gesture you'll use later, but if you want to go beyond the basics you'll need to [download the OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span></span>

<span data-ttu-id="38dd7-130">Une fois les plug-ins activés, vous pouvez vous concentrer sur le remplissage du contenu.</span><span class="sxs-lookup"><span data-stu-id="38dd7-130">With the plugins enabled, you can focus on filling it with content.</span></span>

## <a name="creating-a-level"></a><span data-ttu-id="38dd7-131">Création d’un niveau</span><span class="sxs-lookup"><span data-stu-id="38dd7-131">Creating a level</span></span>

<span data-ttu-id="38dd7-132">La tâche suivante consiste à créer une configuration de joueur avec un point de départ, et un cube pour la référence et la mise à l’échelle.</span><span class="sxs-lookup"><span data-stu-id="38dd7-132">Your next task is to create a player setup with a starting point and a cube for reference and scale.</span></span>

1. <span data-ttu-id="38dd7-133">Sélectionnez **File > New Level**, puis choisissez **Empty Level**.</span><span class="sxs-lookup"><span data-stu-id="38dd7-133">Select **File > New Level** and choose **Empty Level**.</span></span> <span data-ttu-id="38dd7-134">La scène par défaut dans la fenêtre d’affichage doit maintenant être vide.</span><span class="sxs-lookup"><span data-stu-id="38dd7-134">The default scene in the viewport should now be empty</span></span>
2. <span data-ttu-id="38dd7-135">Sous l’onglet **Mode**, sélectionnez **Basic**, puis faites glisser **PlayerStart** dans la scène.</span><span class="sxs-lookup"><span data-stu-id="38dd7-135">From the **Modes** tab, select **Basic** and drag **PlayerStart** into the scene</span></span>
* <span data-ttu-id="38dd7-136">Sous l’onglet **Details**, définissez **Location** sur **X = 0, Y = 0** et **Z = 0** pour placer l’utilisateur au centre de la scène lors du démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="38dd7-136">In the **Details** tab, set **Location** to **X = 0, Y = 0,** and **Z = 0** to place the user at the center of the scene when the app starts</span></span>

![Scène de l’éditeur Unreal avec l’emplacement et le joueur ajoutés](images/unreal-quickstart-img-07.png)

3. <span data-ttu-id="38dd7-138">Sous l’onglet **Basic**, faites glisser un **Cube** dans la scène.</span><span class="sxs-lookup"><span data-stu-id="38dd7-138">From the **Basic** tab, drag a **Cube** into the scene</span></span>
* <span data-ttu-id="38dd7-139">Définissez **Location** pour le cube sur **X = 50, Y = 0** et **Z = 0** pour positionner le cube à 50 cm du joueur au démarrage.</span><span class="sxs-lookup"><span data-stu-id="38dd7-139">Set the cube's **Location** to **X = 50, Y = 0**, and **Z = 0** to position the cube 50 cm away from the player at start</span></span>
* <span data-ttu-id="38dd7-140">Changez **Scale** pour le cube en **X = 0,2, Y = 0,2** et **Z = 0,2**.</span><span class="sxs-lookup"><span data-stu-id="38dd7-140">Change  the cube's **Scale** to **X = 0.2, Y = 0.2**, and **Z = 0.2**</span></span> 

<span data-ttu-id="38dd7-141">Vous ne pouvez pas voir le cube, sauf si vous ajoutez une lumière à votre scène, ce qui constitue votre dernière tâche avant de tester la scène.</span><span class="sxs-lookup"><span data-stu-id="38dd7-141">You can't see the cube unless you add a light to your scene, which is your last task before testing the scene.</span></span>

4. <span data-ttu-id="38dd7-142">Dans le panneau **Modes**, passez à l’onglet **Lights**, puis faites glisser une **Directional Light** dans la scène.</span><span class="sxs-lookup"><span data-stu-id="38dd7-142">In the **Modes** panel, switch to the **Lights** tab and drag a **Directional Light** into the scene</span></span>
* <span data-ttu-id="38dd7-143">Positionnez la lumière au-dessus de **PlayerStart** pour pouvoir la voir.</span><span class="sxs-lookup"><span data-stu-id="38dd7-143">Position the light above **PlayerStart** so you can see it</span></span>

![Scène de l’éditeur Unreal avec le cube et la lumière directionnelle ajoutés](images/unreal-quickstart-img-08.png)

5. <span data-ttu-id="38dd7-145">Accédez à **File > Save Current**, nommez votre niveau **Main**, puis sélectionnez **Save**.</span><span class="sxs-lookup"><span data-stu-id="38dd7-145">Go to **File > Save Current**, name your level **Main**, and select **Save**</span></span>

<span data-ttu-id="38dd7-146">Une fois la scène définie, appuyez sur **Play** dans la barre d’outils pour voir votre cube en action !</span><span class="sxs-lookup"><span data-stu-id="38dd7-146">With the scene set, press **Play** in the toolbar to see your cube in action!</span></span> <span data-ttu-id="38dd7-147">Lorsque vous avez fini d’admirer votre travail, appuyez sur Échap pour arrêter l’application.</span><span class="sxs-lookup"><span data-stu-id="38dd7-147">When you're finished admiring your work, press Esc to stop the application.</span></span>

![Scène en mode lecture avec le cube au milieu de l’écran](images/unreal-quickstart-img-09.png)

<span data-ttu-id="38dd7-149">Maintenant que la scène est configurée, préparons-la pour quelques interactions simples dans AR.</span><span class="sxs-lookup"><span data-stu-id="38dd7-149">Now that the scene is set up, lets get it ready for some basic interactions in AR.</span></span> <span data-ttu-id="38dd7-150">Tout d’abord, vous devez créer une session AR, et vous pouvez aussi ajouter des blueprints pour permettre une interaction manuelle.</span><span class="sxs-lookup"><span data-stu-id="38dd7-150">First, you need to create an AR Session and can add blueprints to enable hand interaction.</span></span>

## <a name="adding-a-session-asset"></a><span data-ttu-id="38dd7-151">Ajout d’une ressource de session</span><span class="sxs-lookup"><span data-stu-id="38dd7-151">Adding a session asset</span></span>

<span data-ttu-id="38dd7-152">Les sessions de réalité augmentée n’arrivent pas toutes seules.</span><span class="sxs-lookup"><span data-stu-id="38dd7-152">AR sessions in Unreal don't happen by themselves.</span></span> <span data-ttu-id="38dd7-153">Pour utiliser une session, vous devez créer une ressource de données ARSessionConfig, ce qui est d’ailleurs votre tâche suivante :</span><span class="sxs-lookup"><span data-stu-id="38dd7-153">To use a session, you need an ARSessionConfig data asset to work with, which is your next task:</span></span>

1. <span data-ttu-id="38dd7-154">Dans le **Content Browser**, sélectionnez **Add New > Miscellaneous > Data Asset** et vérifiez que vous êtes au niveau du dossier Content racine.</span><span class="sxs-lookup"><span data-stu-id="38dd7-154">In the **Content Browser**, select **Add New > Miscellaneous > Data Asset** and make sure you're at the root Content folder level</span></span>
2. <span data-ttu-id="38dd7-155">Sélectionnez **ARSessionConfig**, cliquez sur **Select**, puis nommez la ressource **ARSessionConfig** :</span><span class="sxs-lookup"><span data-stu-id="38dd7-155">Select **ARSessionConfig**, click **Select**, and name the asset **ARSessionConfig**:</span></span>

![Fenêtre de sélection d’une classe de ressources de données ouverte avec la ressource de configuration de session AR mise en évidence](images/unreal-quickstart-img-10.png)

2. <span data-ttu-id="38dd7-157">Double-cliquez sur **ARSessionConfig** pour l’ouvrir, choisissez **Save** avec toutes les valeurs par défaut, puis revenez à la fenêtre principale :</span><span class="sxs-lookup"><span data-stu-id="38dd7-157">Double-click **ARSessionConfig** to open it, **Save** with all default settings, and return to the Main window:</span></span>

![Fenêtre des détails des ressources de configuration de session AR](images/unreal-quickstart-img-11.png)

<span data-ttu-id="38dd7-159">Une fois cette opération effectuée, l’étape suivante consiste à faire en sorte que la session de réalité augmentée démarre et s’arrête quand le niveau se charge et se termine.</span><span class="sxs-lookup"><span data-stu-id="38dd7-159">With that done, your next step is to make sure the AR session starts and stops when the level loads and ends.</span></span> <span data-ttu-id="38dd7-160">Unreal comprend un blueprint spécial appelé **Level Blueprint** (« Blueprint de niveau ») qui joue le rôle de graphe d’événements global à l’échelle du niveau.</span><span class="sxs-lookup"><span data-stu-id="38dd7-160">Luckily, Unreal has a special blueprint called a **Level Blueprint** that acts as a level-wide global event graph.</span></span> <span data-ttu-id="38dd7-161">Le fait de connecter la ressource ARSessionConfig dans le blueprint de niveau garantit que la session de réalité augmentée se déclenchera juste au début du jeu.</span><span class="sxs-lookup"><span data-stu-id="38dd7-161">Connecting the ARSessionConfig asset in the Level Blueprint guarantees the AR session will fire right when the game starts playing.</span></span>

3. <span data-ttu-id="38dd7-162">Dans la barre d’outils de l’éditeur, sélectionnez **Blueprints > Open Level Blueprint** :</span><span class="sxs-lookup"><span data-stu-id="38dd7-162">From the editor toolbar, select **Blueprints > Open Level Blueprint**:</span></span>

![Menu Blueprint ouvert avec l’option Open Level Blueprint en évidence](images/unreal-quickstart-img-12.png)

4. <span data-ttu-id="38dd7-164">Faites glisser le nœud d’exécution (la flèche pointant vers la gauche) en dehors de **Event BeginPlay**, puis relâchez.</span><span class="sxs-lookup"><span data-stu-id="38dd7-164">Drag the execution node (left-facing arrow icon) off **Event BeginPlay** and release</span></span>
* <span data-ttu-id="38dd7-165">Recherchez le **nœud Start AR Session**, puis appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="38dd7-165">Search for the **Start AR Session node** and hit enter</span></span>
* <span data-ttu-id="38dd7-166">Cliquez sur la liste déroulante **Select Asset** sous **Session Config**, puis sélectionnez la ressource **ARSessionConfig**.</span><span class="sxs-lookup"><span data-stu-id="38dd7-166">Click the **Select Asset** dropdown under **Session Config** and choose the **ARSessionConfig** asset</span></span>

![Graphique de blueprint avec Event BeginPlay connecté à la fonction Start AR Session](images/unreal-quickstart-img-13.png)

5. <span data-ttu-id="38dd7-168">Cliquez avec le bouton droit n’importe où dans l’EventGraph et créez un nœud **Event EndPlay**.</span><span class="sxs-lookup"><span data-stu-id="38dd7-168">Right-click anywhere in the EventGraph and create a new **Event EndPlay** node.</span></span> 
* <span data-ttu-id="38dd7-169">Faites glisser la broche d’exécution et relâchez le bouton, puis recherchez le nœud **Stop AR Session** et appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="38dd7-169">Drag the execution pin and release, then search for a **Stop AR Session** node and hit enter</span></span> 
* <span data-ttu-id="38dd7-170">Cliquez sur **Compile**, puis sur **Save**, et revenez à la fenêtre principale.</span><span class="sxs-lookup"><span data-stu-id="38dd7-170">Hit **Compile**, then **Save** and return to the Main window</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38dd7-171">Si la session de réalité augmentée est toujours en cours quand le niveau se termine, certaines fonctionnalités peuvent cesser de fonctionner si vous redémarrez votre application lors du streaming sur un casque.</span><span class="sxs-lookup"><span data-stu-id="38dd7-171">If the AR session is still running when the level ends, certain features may stop working if you restart your app while streaming to a headset.</span></span>

![Nœud Event EndPlay attaché à la fonction Stop AR Session](images/unreal-quickstart-img-14.png)

## <a name="setting-up-inputs"></a><span data-ttu-id="38dd7-173">Configuration des entrées</span><span class="sxs-lookup"><span data-stu-id="38dd7-173">Setting up inputs</span></span>

1. <span data-ttu-id="38dd7-174">Sélectionnez **Edit > Project Settings**, puis accédez à **Engine > Input**.</span><span class="sxs-lookup"><span data-stu-id="38dd7-174">Select **Edit > Project Settings** and go to the **Engine > Input**</span></span>
2. <span data-ttu-id="38dd7-175">Sélectionnez l’icône **+** à côté de **Action Mappings**, puis créez des actions **RightPinch** et **LeftPinch** :</span><span class="sxs-lookup"><span data-stu-id="38dd7-175">Select the **+** icon next to **Action Mappings** and create **RightPinch** and **LeftPinch** actions:</span></span>

![Liaison des paramètres d’entrée avec les mappages des actions de pincement droit et gauche mis en évidence](images/unreal-quickstart-img-15.jpg)

3. <span data-ttu-id="38dd7-177">Mappez les actions **RightPinch** et **LeftPinch** aux actions **OpenXR Msft Hand Interaction** correspondantes :</span><span class="sxs-lookup"><span data-stu-id="38dd7-177">Map the **RightPinch** and **LeftPinch** actions the to the respective **OpenXR Msft Hand Interaction** actions:</span></span>

![Mappages d’actions avec les options Open XR Msft Hand Interaction en évidence](images/unreal-quickstart-img-16.jpg)

4. <span data-ttu-id="38dd7-179">Ouvrez le **Level Blueprint** et ajoutez un **InputAction RightPinch** et un **InputAction LeftPinch**.</span><span class="sxs-lookup"><span data-stu-id="38dd7-179">Open the **Level Blueprint** and add an **InputAction RightPinch** and **InputAction LeftPinch**</span></span>
* <span data-ttu-id="38dd7-180">Connectez l’événement pincement droit à une **AddActorLocalRotation** avec votre **Cube**  comme cible, et **Delta Rotation** défini sur **X = 0, Y = 0** et **Z = 20**.</span><span class="sxs-lookup"><span data-stu-id="38dd7-180">Connect the right pinch event to an **AddActorLocalRotation** with your **Cube** as the target and **Delta Rotation** set to **X = 0, Y = 0**, and **Z = 20**.</span></span> <span data-ttu-id="38dd7-181">Le cube va maintenant pivoter de 20 degrés chaque fois que vous pincez.</span><span class="sxs-lookup"><span data-stu-id="38dd7-181">The cube will now rotate by 20 degrees every time you pinch</span></span>
* <span data-ttu-id="38dd7-182">Connectez l’événement de pincement gauche à **Quit Game**.</span><span class="sxs-lookup"><span data-stu-id="38dd7-182">Connect the left pinch event to **Quit Game**</span></span>

![Blueprint de niveau ouvert avec des actions d’entrée pour les événements de pincement droit et gauche](images/unreal-quickstart-img-17.jpg)

5. <span data-ttu-id="38dd7-184">Dans les paramètres **Transform** du cube, définissez **Mobility** sur **Movable** pour qu’il puisse se déplacer dynamiquement :</span><span class="sxs-lookup"><span data-stu-id="38dd7-184">In the cube's **Transform** settings, set **Mobility** to **Movable** so it can move dynamically:</span></span>

![Paramètres de transformation avec la propriété de mobilité mis en évidence](images/unreal-quickstart-img-18.jpg)

<span data-ttu-id="38dd7-186">À ce stade, vous êtes prêt à déployer et à tester l’application !</span><span class="sxs-lookup"><span data-stu-id="38dd7-186">At this point, you're ready to deply and test the application!</span></span>