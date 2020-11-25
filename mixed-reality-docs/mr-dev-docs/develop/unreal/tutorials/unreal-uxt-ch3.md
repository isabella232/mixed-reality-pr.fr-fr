---
title: 3. Configuration de votre projet pour la réalité mixte
description: Troisième tutoriel d’une série de six tutoriels, dans lequel vous apprenez à créer une application de jeu d’échecs simple avec Unreal Engine 4 et le plug-in UX Tools du Mixed Reality Toolkit
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, réalité mixte, tutoriel, bien démarrer, mrtk, uxt, UX Tools, documentation, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle
ms.openlocfilehash: 82e210aff35f1c41547f022b91114cbca1419830
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679878"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a><span data-ttu-id="1656e-104">3. Configuration de votre projet pour la réalité mixte</span><span class="sxs-lookup"><span data-stu-id="1656e-104">3. Setting up your project for mixed reality</span></span>

## <a name="overview"></a><span data-ttu-id="1656e-105">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="1656e-105">Overview</span></span>

<span data-ttu-id="1656e-106">Dans le tutoriel précédent, vous avez configuré le projet d’application de jeu d’échecs.</span><span class="sxs-lookup"><span data-stu-id="1656e-106">In the previous tutorial, you spent time setting up the chess app project.</span></span> <span data-ttu-id="1656e-107">Cette section va vous expliquer comment configurer l’application pour le développement de réalité mixte, ce qui implique l’ajout d’une session de réalité augmentée.</span><span class="sxs-lookup"><span data-stu-id="1656e-107">This section is going to walk you through setting up the app for mixed reality development, which means adding an AR session.</span></span> <span data-ttu-id="1656e-108">Pour cette tâche, vous allez utiliser une ressource de données ARSessionConfig, qui contient un grand nombre de paramètres pour la réalité augmentée, tels que le mappage spatial et l’occlusion.</span><span class="sxs-lookup"><span data-stu-id="1656e-108">You'll be using an ARSessionConfig data asset for this task, which has a lot of useful AR settings like spatial mapping and occlusion.</span></span> <span data-ttu-id="1656e-109">Si vous souhaitez approfondir le sujet, notez que la documentation Unreal Engine décrit en détail la ressource [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) et la classe [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html).</span><span class="sxs-lookup"><span data-stu-id="1656e-109">If you want to dive deeper, the Unreal Engine documentation has more details on the [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) asset and the [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) class.</span></span>

## <a name="objectives"></a><span data-ttu-id="1656e-110">Objectifs</span><span class="sxs-lookup"><span data-stu-id="1656e-110">Objectives</span></span>
* <span data-ttu-id="1656e-111">Utilisation des paramètres de réalité augmentée d’Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="1656e-111">Working with Unreal Engine's AR settings</span></span> 
* <span data-ttu-id="1656e-112">Utilisation d’une ressource de données ARSessionConfig</span><span class="sxs-lookup"><span data-stu-id="1656e-112">Using an ARSessionConfig data asset</span></span>
* <span data-ttu-id="1656e-113">Configuration d’un pion et du mode Jeu</span><span class="sxs-lookup"><span data-stu-id="1656e-113">Setting up a Pawn and game mode</span></span>

## <a name="adding-the-session-asset"></a><span data-ttu-id="1656e-114">Ajout de la ressource de session</span><span class="sxs-lookup"><span data-stu-id="1656e-114">Adding the session asset</span></span>
<span data-ttu-id="1656e-115">Les sessions de réalité augmentée n’arrivent pas toutes seules.</span><span class="sxs-lookup"><span data-stu-id="1656e-115">AR sessions in Unreal don't happen by themselves.</span></span> <span data-ttu-id="1656e-116">Pour utiliser une session, vous devez créer une ressource de données ARSessionConfig, ce qui est d’ailleurs votre prochaine tâche :</span><span class="sxs-lookup"><span data-stu-id="1656e-116">To use a session you need an ARSessionConfig data asset to work with, which is your next task:</span></span>

1. <span data-ttu-id="1656e-117">Cliquez sur **Add New > Miscellaneous > Data Asset** (Ajouter > Divers > Ressource de données) dans le navigateur de contenu (**Content Browser**).</span><span class="sxs-lookup"><span data-stu-id="1656e-117">Click **Add New > Miscellaneous > Data Asset** in the **Content Browser**.</span></span> <span data-ttu-id="1656e-118">Vérifiez que vous vous trouvez au niveau du dossier **Content** racine.</span><span class="sxs-lookup"><span data-stu-id="1656e-118">Make sure you're at the root **Content** folder level.</span></span> 
    * <span data-ttu-id="1656e-119">Sélectionnez **ARSessionConfig**, cliquez sur **Select**, puis nommez la ressource **ARSessionConfig**.</span><span class="sxs-lookup"><span data-stu-id="1656e-119">Select **ARSessionConfig**, click **Select**, and name the asset **ARSessionConfig**.</span></span>

![Créer une ressource de données](images/unreal-uxt/3-createasset.PNG)

3. <span data-ttu-id="1656e-121">Double-cliquez sur **ARSessionConfig** pour l’ouvrir, conservez tous les paramètres par défaut, puis appuyez sur **Save** (Enregistrer).</span><span class="sxs-lookup"><span data-stu-id="1656e-121">Double-click **ARSessionConfig** to open it, leave all default settings and hit **Save**.</span></span> <span data-ttu-id="1656e-122">Revenez dans la fenêtre principale.</span><span class="sxs-lookup"><span data-stu-id="1656e-122">Return to the Main window.</span></span> 

![Configuration de la session AR](images/unreal-uxt/3-arsessionconfig.PNG)

<span data-ttu-id="1656e-124">Une fois cette opération effectuée, l’étape suivante consiste à faire en sorte que la session de réalité augmentée démarre quand le niveau se charge et s’arrête quand le niveau se termine.</span><span class="sxs-lookup"><span data-stu-id="1656e-124">With that done, your next step is to make sure that the AR session starts when the level loads and stops when the level ends.</span></span> <span data-ttu-id="1656e-125">Unreal comprend un blueprint spécial appelé **blueprint de niveau** (« Level Blueprint ») qui joue le rôle de graphe d’événements (« Event Graph ») à l’échelle du niveau.</span><span class="sxs-lookup"><span data-stu-id="1656e-125">Luckily, Unreal has a special kind of blueprint called a **Level Blueprint** that acts as a level-wide global event graph.</span></span> <span data-ttu-id="1656e-126">Le fait de connecter la ressource ARSessionConfig dans le **blueprint de niveau** garantit que la session de réalité augmentée se déclenchera juste au début du jeu.</span><span class="sxs-lookup"><span data-stu-id="1656e-126">Connecting the ARSessionConfig asset in the **Level Blueprint** guarantees the AR session will fire right when the game starts playing.</span></span>

1. <span data-ttu-id="1656e-127">Cliquez sur **Blueprints > Open Level Blueprint** (Blueprints > Ouvrir le blueprint de niveau) dans la barre d’outils de l’éditeur :</span><span class="sxs-lookup"><span data-stu-id="1656e-127">Click **Blueprints > Open Level Blueprint** from the editor toolbar:</span></span> 

![Ouverture du blueprint de niveau](images/unreal-uxt/3-level-blueprint.PNG)

5. <span data-ttu-id="1656e-129">Faites glisser le nœud d’exécution (la flèche pointant vers la gauche) en dehors de **Event BeginPlay** puis relâchez.</span><span class="sxs-lookup"><span data-stu-id="1656e-129">Drag the execution node (left-facing arrow icon) off **Event BeginPlay** and release.</span></span> <span data-ttu-id="1656e-130">Recherchez le nœud **Start AR Session** (Démarrer la session de réalité augmentée) et appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="1656e-130">Search for the **Start AR Session** node and hit enter.</span></span>  
    * <span data-ttu-id="1656e-131">Cliquez sur la liste déroulante **Select Asset** (Sélectionner une ressource) sous **Session Config** (Configuration de la session), puis sélectionnez la ressource **ARSessionConfig**.</span><span class="sxs-lookup"><span data-stu-id="1656e-131">Click the **Select Asset** dropdown under **Session Config** and choose the **ARSessionConfig** asset.</span></span> 

![Démarrer la session AR](images/unreal-uxt/3-start-ar-session.PNG)

6. <span data-ttu-id="1656e-133">Cliquez avec le bouton droit n’importe où dans l’EventGraph et créez un nœud **Event EndPlay**.</span><span class="sxs-lookup"><span data-stu-id="1656e-133">Right-click anywhere in the EventGraph and create a new **Event EndPlay** node.</span></span> <span data-ttu-id="1656e-134">Faites glisser le repère d’exécution et relâchez-le.</span><span class="sxs-lookup"><span data-stu-id="1656e-134">Drag the execution pin and release.</span></span> <span data-ttu-id="1656e-135">Recherchez un nœud **Stop AR Session** (Arrêter la session AR) et appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="1656e-135">Search for a **Stop AR Session** node and hit enter.</span></span> <span data-ttu-id="1656e-136">Si la session AR n’est pas arrêtée à la fin du niveau, certaines fonctionnalités peuvent cesser de fonctionner si vous redémarrez votre application lors du streaming sur un casque.</span><span class="sxs-lookup"><span data-stu-id="1656e-136">If the AR session isn't stopped when the level ends, certain features may stop working if you restart your app while streaming to a headset.</span></span> 
    * <span data-ttu-id="1656e-137">Cliquez sur **Compile**, puis sur **Save** pour revenir à la fenêtre principale.</span><span class="sxs-lookup"><span data-stu-id="1656e-137">Hit **Compile**, then **Save** and return to the Main window.</span></span>

![Arrêter la session AR](images/unreal-uxt/3-stoparsession.PNG)

## <a name="create-a-pawn"></a><span data-ttu-id="1656e-139">Créer un Pawn</span><span class="sxs-lookup"><span data-stu-id="1656e-139">Create a Pawn</span></span>
<span data-ttu-id="1656e-140">À ce stade, le projet a toujours besoin d’un objet de lecteur.</span><span class="sxs-lookup"><span data-stu-id="1656e-140">At this point, the project still needs a player object.</span></span> <span data-ttu-id="1656e-141">Dans Unreal, un pion (**Pawn**) représente l’utilisateur dans le jeu, mais ici, il s’agira de l’expérience HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1656e-141">In Unreal, a **Pawn** represents the user in the game, but in this case it's going to be the HoloLens 2 experience.</span></span>

1. <span data-ttu-id="1656e-142">Cliquez sur **Add New > Blueprint Class** (Ajouter > Classe de blueprint) dans le dossier **Content**, puis développez la section **All Classes** située en bas.</span><span class="sxs-lookup"><span data-stu-id="1656e-142">Click **Add New > Blueprint Class** in the **Content** folder and expand the **All Classes** section at the bottom.</span></span> 
    * <span data-ttu-id="1656e-143">Recherchez **DefaultPawn**, cliquez sur **Select**, nommez-le **MRPawn**, puis double-cliquez sur la ressource pour l’ouvrir.</span><span class="sxs-lookup"><span data-stu-id="1656e-143">Search for **DefaultPawn**, click **Select**, name it **MRPawn**, and double-click the asset to open.</span></span> 

![Créer un Pawn héritant de DefaultPawn](images/unreal-uxt/3-defaultpawn.PNG)

> [!NOTE]
> <span data-ttu-id="1656e-145">Par défaut, les pions (Pawns) ont des composants de maillage et de collision.</span><span class="sxs-lookup"><span data-stu-id="1656e-145">By default, Pawns have mesh and collision components.</span></span> <span data-ttu-id="1656e-146">Dans la plupart des projets Unreal, les pions sont des objets solides qui peuvent entrer en collision avec d’autres composants.</span><span class="sxs-lookup"><span data-stu-id="1656e-146">In most Unreal projects, Pawns are solid objects that can collide with other components.</span></span> <span data-ttu-id="1656e-147">Étant donné que le pion et l’utilisateur sont une seule et même entité dans la réalité mixte, vous devez pouvoir passer par des hologrammes sans aucune collision.</span><span class="sxs-lookup"><span data-stu-id="1656e-147">Since the Pawn and user are the same in mixed reality, you want to be able to pass through holograms without any collisions.</span></span> 

2. <span data-ttu-id="1656e-148">Sélectionnez **CollisionComponent** dans le panneau **Components**, puis faites défiler jusqu’à la section **Collision** du panneau **Details**.</span><span class="sxs-lookup"><span data-stu-id="1656e-148">Select **CollisionComponent** from the **Components** panel and scroll down to the **Collision** section of the **Details** panel.</span></span> 
    * <span data-ttu-id="1656e-149">Cliquez sur la liste déroulante **Collision Presets** (Valeurs prédéfinies de collision), puis remplacez la valeur par **NoCollision**.</span><span class="sxs-lookup"><span data-stu-id="1656e-149">Click the **Collision Presets** dropdown and change the value to **NoCollision**.</span></span> 
    * <span data-ttu-id="1656e-150">Répétez cette opération pour **MeshComponent**.</span><span class="sxs-lookup"><span data-stu-id="1656e-150">Do the same for the **MeshComponent**</span></span>

![Changer la valeur Pawn dans Collision Presets](images/unreal-uxt/3-nocollision.PNG)

3. <span data-ttu-id="1656e-152">Cliquez sur **Add Component > Camera** dans le panneau **Components** et nommez le composant **Camera**.</span><span class="sxs-lookup"><span data-stu-id="1656e-152">Click **Add Component > Camera** from the **Components** panel and name it **Camera**.</span></span> <span data-ttu-id="1656e-153">Cela permet à la caméra du joueur de se déplacer avec l’appareil HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1656e-153">This allows the player camera to move with the HoloLens 2 device.</span></span>

> [!NOTE]
> <span data-ttu-id="1656e-154">Vérifiez que le composant **Camera** est un enfant direct de la racine (**CollisionComponent**).</span><span class="sxs-lookup"><span data-stu-id="1656e-154">Make sure that the **Camera** component is a direct child of the root (**CollisionComponent**).</span></span>

4. <span data-ttu-id="1656e-155">**Compilez** et **enregistrez** le blueprint.</span><span class="sxs-lookup"><span data-stu-id="1656e-155">**Compile** and **Save** the Blueprint.</span></span>

<span data-ttu-id="1656e-156">Une fois votre travail terminé, revenez à la fenêtre principale.</span><span class="sxs-lookup"><span data-stu-id="1656e-156">With your work here done, return to the Main Window.</span></span>

## <a name="create-a-game-mode"></a><span data-ttu-id="1656e-157">Créer un mode de jeu</span><span class="sxs-lookup"><span data-stu-id="1656e-157">Create a Game Mode</span></span>
<span data-ttu-id="1656e-158">La dernière étape de configuration de la réalité mixte est le mode Jeu.</span><span class="sxs-lookup"><span data-stu-id="1656e-158">The last puzzle piece of the mixed reality setup is the Game Mode.</span></span> <span data-ttu-id="1656e-159">Le mode Jeu (Game Mode) définit plusieurs paramètres du jeu ou de l’expérience, y compris le pion par défaut à utiliser.</span><span class="sxs-lookup"><span data-stu-id="1656e-159">The Game Mode determines a number of settings for the game or experience, including the default pawn to use.</span></span>

1.  <span data-ttu-id="1656e-160">Cliquez sur **Add New > Blueprint Class** (Ajouter > Classe de blueprint) dans le dossier **Content**, puis développez la section **All Classes** située en bas.</span><span class="sxs-lookup"><span data-stu-id="1656e-160">Click **Add New > Blueprint Class** in the **Content** folder and expand the **All Classes** section at the bottom.</span></span> 
    * <span data-ttu-id="1656e-161">Recherchez **Game Mode Base** (Base du mode Jeu), nommez-le **MRGameMode**, puis double-cliquez dessus pour l’ouvrir.</span><span class="sxs-lookup"><span data-stu-id="1656e-161">Search for **Game Mode Base**, name it **MRGameMode** and double-click to open.</span></span> 

![MRGameMode dans le navigateur de contenu](images/unreal-uxt/3-gamemode.PNG)

2.  <span data-ttu-id="1656e-163">Accédez à la section **Classes** dans le panneau **Details**, puis définissez **Default Pawn Class** (Classe du pion par défaut) sur **MRPawn**.</span><span class="sxs-lookup"><span data-stu-id="1656e-163">Go to the **Classes** section in the **Details** panel and change the **Default Pawn Class** to **MRPawn**.</span></span> 
    * <span data-ttu-id="1656e-164">Cliquez sur **Compile**, puis sur **Save** pour revenir à la fenêtre principale.</span><span class="sxs-lookup"><span data-stu-id="1656e-164">Hit **Compile**, then **Save** and return to the Main window.</span></span> 

![Définir l’option Default Pawn Class](images/unreal-uxt/3-setpawn.PNG)

3.  <span data-ttu-id="1656e-166">Sélectionnez **Edit > Projects Settings** (Modifier > Paramètres du projet), puis cliquez sur **Maps & Modes** (Cartes et modes) dans la liste de gauche.</span><span class="sxs-lookup"><span data-stu-id="1656e-166">Select **Edit > Projects Settings** and click **Maps & Modes** in the left-hand list.</span></span> 
    * <span data-ttu-id="1656e-167">Développez **Default Modes** (Modes par défaut), puis définissez **Default Game Mode** (Mode Jeu par défaut) sur **MRGameMode**.</span><span class="sxs-lookup"><span data-stu-id="1656e-167">Expand **Default Modes** and change **Default Game Mode** to **MRGameMode**.</span></span> 
    * <span data-ttu-id="1656e-168">Développez **Default Maps** (Cartes par défaut), puis définissez **EditorStartupMap** et **GameDefaultMap** sur **Main**.</span><span class="sxs-lookup"><span data-stu-id="1656e-168">Expand **Default Maps** and change both **EditorStartupMap** and **GameDefaultMap** to **Main**.</span></span> <span data-ttu-id="1656e-169">De cette façon, quand vous fermerez puis rouvrirez l’éditeur, ou quand vous ferez une partie, la carte principale (Main) sera sélectionnée par défaut.</span><span class="sxs-lookup"><span data-stu-id="1656e-169">This way when you close and reopen the editor, or play the game, the Main map will be selected by default.</span></span>

![Project Settings - Maps & Modes](images/unreal-uxt/3-mapsandmodes.PNG)

<span data-ttu-id="1656e-171">Une fois le projet entièrement configuré pour la réalité mixte, vous êtes prêt à passer au tutoriel suivant et à ajouter une entrée d’utilisateur à la scène.</span><span class="sxs-lookup"><span data-stu-id="1656e-171">With the project fully setup for mixed reality, you're ready to move on to the next tutorial and start adding user input to the scene.</span></span> 

[<span data-ttu-id="1656e-172">Section suivante : 4. Rendre votre scène interactive</span><span class="sxs-lookup"><span data-stu-id="1656e-172">Next Section: 4. Making your scene interactive</span></span>](unreal-uxt-ch4.md)
