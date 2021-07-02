---
title: Service de simulation d’entrée
description: Documentation sur le service de simulation d’entrée dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 66b79c14bbd0ea8c188aba684b9bd1034de31bf9
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176964"
---
# <a name="input-simulation-service"></a><span data-ttu-id="7e3ea-104">Service de simulation d’entrée</span><span class="sxs-lookup"><span data-stu-id="7e3ea-104">Input simulation service</span></span>

![Simulation d’entrée MRTK](../images/input-simulation/MRTK_InputSimulation_Hero.jpg)

<span data-ttu-id="7e3ea-106">Avec la simulation d’entrée de MRTK, vous pouvez tester divers types d’interactions dans l’éditeur Unity sans générer et déployer sur un appareil.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-106">With MRTK's input simulation, you can test various types of interactions in the Unity editor without building and deploying to a device.</span></span> <span data-ttu-id="7e3ea-107">Cela vous permet d’itérer rapidement vos idées dans le processus de conception et de développement.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-107">This allows you quickly iterate your ideas in the design and development process.</span></span> <span data-ttu-id="7e3ea-108">Utilisez les combinaisons clavier et souris pour contrôler les entrées simulées.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-108">Use keyboard and mouse combinations to control simulated inputs.</span></span>

<span data-ttu-id="7e3ea-109">Le service de simulation d’entrée émule le comportement des appareils et des plateformes qui peuvent ne pas être disponibles dans l’éditeur Unity.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-109">The Input Simulation Service emulates the behavior of devices and platforms that may not be available in the Unity editor.</span></span> <span data-ttu-id="7e3ea-110">Voici quelques exemples :</span><span class="sxs-lookup"><span data-stu-id="7e3ea-110">Examples include:</span></span>

* <span data-ttu-id="7e3ea-111">suivi des en-têtes d’appareil HoloLens ou VR</span><span class="sxs-lookup"><span data-stu-id="7e3ea-111">HoloLens or VR device head tracking</span></span>
* <span data-ttu-id="7e3ea-112">mouvements de la main HoloLens</span><span class="sxs-lookup"><span data-stu-id="7e3ea-112">HoloLens hand gestures</span></span>
* <span data-ttu-id="7e3ea-113">HoloLens 2 le suivi articulé</span><span class="sxs-lookup"><span data-stu-id="7e3ea-113">HoloLens 2 articulated hand tracking</span></span>
* <span data-ttu-id="7e3ea-114">suivi des yeux HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="7e3ea-114">HoloLens 2 eye tracking</span></span>
* <span data-ttu-id="7e3ea-115">Contrôleurs de périphérique VR</span><span class="sxs-lookup"><span data-stu-id="7e3ea-115">VR device controllers</span></span>

> [!WARNING]
> <span data-ttu-id="7e3ea-116">Cela ne fonctionne pas lors de l’utilisation de l’émulation holographique XR de Unity > de l’émulation mode = « simuler dans l’éditeur ».</span><span class="sxs-lookup"><span data-stu-id="7e3ea-116">This does not work when using Unity's XR Holographic Emulation > Emulation Mode = "Simulate in Editor".</span></span> <span data-ttu-id="7e3ea-117">La simulation in-Editor de Unity prend le contrôle à la suite de la simulation d’entrée de MRTK.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-117">Unity's in-editor simulation will take control away from MRTK's input simulation.</span></span> <span data-ttu-id="7e3ea-118">Pour utiliser le service de simulation d’entrée MRTK, vous devez définir l’émulation holographique XR sur émulation mode = *"none"*</span><span class="sxs-lookup"><span data-stu-id="7e3ea-118">In order to use the MRTK input simulation service, you will need to set XR Holographic Emulation to Emulation Mode = *"None"*</span></span>

## <a name="how-to-use-mrtk-input-simulation"></a><span data-ttu-id="7e3ea-119">Utilisation de la simulation d’entrée MRTK</span><span class="sxs-lookup"><span data-stu-id="7e3ea-119">How to use MRTK Input simulation</span></span> 

<span data-ttu-id="7e3ea-120">La simulation d’entrée est activée par défaut dans les profils fournis avec MRTK.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-120">Input simulation is enabled by default in the profiles that ship with MRTK.</span></span> <span data-ttu-id="7e3ea-121">Vous pouvez simplement cliquer sur le bouton de **lecture** pour exécuter la scène avec la prise en charge de la simulation d’entrée.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-121">You can simply click **Play** button to run the scene with input simulation support.</span></span>

* <span data-ttu-id="7e3ea-122">Appuyez sur les touches **W, A, S, D, Q, E** pour déplacer l’appareil photo.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-122">Press **W, A, S, D, Q, E** keys to move the camera.</span></span>
* <span data-ttu-id="7e3ea-123">Maintenez le **bouton droit** de la souris et déplacez la souris pour regarder.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-123">Hold the **Right mouse button** and move the mouse to look around.</span></span>
* <span data-ttu-id="7e3ea-124">Pour afficher les mains simulées, appuyez sur la **barre d’espace (à droite)** ou sur la **touche Maj de gauche (gauche)**</span><span class="sxs-lookup"><span data-stu-id="7e3ea-124">To bring up the simulated hands, press **Space bar(Right hand)** or **Left Shift key(Left hand)**</span></span>
* <span data-ttu-id="7e3ea-125">Pour conserver les mains simulées dans la vue, appuyez sur la touche **T** ou **Y**</span><span class="sxs-lookup"><span data-stu-id="7e3ea-125">To keep simulated hands in the view, press **T** or **Y** key</span></span>
* <span data-ttu-id="7e3ea-126">Pour faire pivoter des mains simulées, maintenez la **touche Ctrl** enfoncée et déplacez la souris</span><span class="sxs-lookup"><span data-stu-id="7e3ea-126">To rotate simulated hands, press and hold **Ctrl key** and move mouse</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4OYrm]

## <a name="in-editor-input-simulation-cheat-sheet"></a><span data-ttu-id="7e3ea-127">Aide-mémoire de simulation d’entrée de l’éditeur</span><span class="sxs-lookup"><span data-stu-id="7e3ea-127">In editor input simulation cheat sheet</span></span>

<span data-ttu-id="7e3ea-128">Appuyez sur **Ctrl + H gauche** dans la scène HandInteractionExamples pour afficher une aide-mémoire avec les contrôles de simulation d’entrée.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-128">Press **Left Ctrl + H** in the HandInteractionExamples scene to bring up a cheat sheet with Input simulation controls.</span></span>

> ![Aide-mémoire pour la simulation d’entrée MRTK](../images/input-simulation/MRTK_InputSimulation_CheatSheet.png)


## <a name="enabling-the-input-simulation-service"></a><span data-ttu-id="7e3ea-130">Activation du service de simulation d’entrée</span><span class="sxs-lookup"><span data-stu-id="7e3ea-130">Enabling the input simulation service</span></span>

<span data-ttu-id="7e3ea-131">Dans le cadre de la configuration du fournisseur de données de système d’entrée, le service de simulation d’entrée peut être configuré comme suit.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-131">Under the Input System Data provider configuration, the Input Simulation service can be configured with the following.</span></span>

* <span data-ttu-id="7e3ea-132">le **Type** doit être *Microsoft. MixedReality. Shared Computer Toolkit. > d’entrée InputSimulationService*.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-132">**Type** must be *Microsoft.MixedReality.Toolkit.Input > InputSimulationService*.</span></span>
* <span data-ttu-id="7e3ea-133">Les **plateformes prises en charge** incluent par défaut toutes les plateformes d' *éditeur* , car le service utilise le clavier et l’entrée de souris.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-133">**Supported Platform(s)** by default includes all *Editor* platforms, since the service uses keyboard and mouse input.</span></span>

> [!NOTE]
> <span data-ttu-id="7e3ea-134">Le service de simulation d’entrée peut être utilisé sur d’autres points de terminaison de plateforme tels que standalone en modifiant la propriété **plateformes prises en charge** pour inclure les cibles souhaitées.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-134">The Input Simulation service can be used on other platform endpoints such as standalone by changing the **Supported Platform(s)** property to include the desired targets.</span></span>
> <br/><img src="../images/input-simulation/InputSimulationSupportedPlatforms.gif" alt="Input Simulation Supported Platforms" width="550px">

## <a name="camera-control"></a><span data-ttu-id="7e3ea-135">Contrôle Camera</span><span class="sxs-lookup"><span data-stu-id="7e3ea-135">Camera control</span></span>

<span data-ttu-id="7e3ea-136">Le mouvement de la tête peut être émulé par le service de simulation d’entrée.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-136">Head movement can be emulated by the Input Simulation Service.</span></span>

### <a name="rotating-the-camera"></a><span data-ttu-id="7e3ea-137">Rotation de l’appareil photo</span><span class="sxs-lookup"><span data-stu-id="7e3ea-137">Rotating the camera</span></span>

1. <span data-ttu-id="7e3ea-138">Pointez sur la fenêtre de l’éditeur de fenêtre d’affichage.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-138">Hover over the viewport editor window.</span></span>
    <span data-ttu-id="7e3ea-139">*Vous devrez peut-être cliquer sur la fenêtre pour lui attribuer le focus si l’appui sur les boutons ne fonctionne pas.*</span><span class="sxs-lookup"><span data-stu-id="7e3ea-139">*You may need to click the window to give it input focus if button presses don't work.*</span></span>
1. <span data-ttu-id="7e3ea-140">Maintenez le bouton de la **souris** enfoncé (par défaut : bouton droit de la souris).</span><span class="sxs-lookup"><span data-stu-id="7e3ea-140">Press and hold the **Mouse Look Button** (default: Right mouse button).</span></span>
1. <span data-ttu-id="7e3ea-141">Déplacez la souris dans la fenêtre de la fenêtre d’affichage pour faire pivoter l’appareil photo.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-141">Move the mouse in the viewport window to rotate the camera.</span></span>
1. <span data-ttu-id="7e3ea-142">Utilisez la roulette de défilement pour faire rouler l’appareil photo autour de la direction de l’affichage.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-142">Use the scroll wheel to roll the camera around the view direction.</span></span>

<span data-ttu-id="7e3ea-143">La vitesse de rotation de la caméra peut être configurée en modifiant le paramètre de vitesse de la **souris** dans le profil de simulation d’entrée.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-143">Camera rotation speed can be configured by changing the **Mouse Look Speed** setting in the input simulation profile.</span></span>

<span data-ttu-id="7e3ea-144">Vous pouvez également utiliser les axes verticaux regarder **horizontales** /  pour faire pivoter l’appareil photo (par défaut : joystick droit du contrôleur de jeu).</span><span class="sxs-lookup"><span data-stu-id="7e3ea-144">Alternatively, use the **Look Horizontal**/**Look Vertical** axes to rotate the camera (default: game controller right thumbstick).</span></span>

### <a name="moving-the-camera"></a><span data-ttu-id="7e3ea-145">Déplacement de la caméra</span><span class="sxs-lookup"><span data-stu-id="7e3ea-145">Moving the camera</span></span>

<span data-ttu-id="7e3ea-146">Utilisez les axes verticaux déplacer vers le déplacement **horizontal** /  pour déplacer l’appareil photo (valeur par défaut : clés WASD ou joystick gauche du contrôleur de jeu).</span><span class="sxs-lookup"><span data-stu-id="7e3ea-146">Use the **Move Horizontal**/**Move Vertical** axes to move the camera (default: WASD keys or game controller left thumbstick).</span></span>

<span data-ttu-id="7e3ea-147">Les angles de position et de rotation de la caméra peuvent également être définis explicitement dans la fenêtre outils.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-147">Camera position and rotation angles can be set explicitly in the tools window, as well.</span></span> <span data-ttu-id="7e3ea-148">La caméra peut être réinitialisée à sa valeur par défaut à l’aide du bouton **Réinitialiser** .</span><span class="sxs-lookup"><span data-stu-id="7e3ea-148">The camera can be reset to its default using the **Reset** button.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/Z7L4I1ET7GU" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="controller-simulation"></a><span data-ttu-id="7e3ea-149">Simulation de contrôleur</span><span class="sxs-lookup"><span data-stu-id="7e3ea-149">Controller simulation</span></span>

<span data-ttu-id="7e3ea-150">La simulation d’entrée prend en charge les périphériques de contrôleur émulés (c’est-à-dire les contrôleurs de mouvement et les aiguilles).</span><span class="sxs-lookup"><span data-stu-id="7e3ea-150">The input simulation supports emulated controller devices (i.e. motion controllers and hands).</span></span> <span data-ttu-id="7e3ea-151">Ces contrôleurs virtuels peuvent interagir avec n’importe quel objet qui prend en charge des contrôleurs normaux, tels que des boutons ou des objets pouvant être pris en charge.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-151">These virtual controllers can interact with any object that supports regular controllers, such as buttons or grabbable objects.</span></span>

### <a name="controller-simulation-mode"></a><span data-ttu-id="7e3ea-152">Mode de simulation du contrôleur</span><span class="sxs-lookup"><span data-stu-id="7e3ea-152">Controller simulation mode</span></span>

<span data-ttu-id="7e3ea-153">Dans la [fenêtre outils de simulation d’entrée](#input-simulation-tools-window) , le paramètre de **mode de simulation du contrôleur par défaut** bascule entre trois modèles d’entrée distincts.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-153">In the [input simulation tools window](#input-simulation-tools-window) the **Default Controller Simulation Mode** setting switches between three distinct input models.</span></span> <span data-ttu-id="7e3ea-154">Ce mode par défaut peut également être défini dans le profil de simulation d’entrée.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-154">This default mode can also be set in the input simulation profile.</span></span>

* <span data-ttu-id="7e3ea-155">*Mains articulées*: simule un appareil manuel entièrement articulé avec des données de position conjointe.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-155">*Articulated Hands*: Simulates a fully articulated hand device with joint position data.</span></span>

   <span data-ttu-id="7e3ea-156">émule HoloLens 2 modèle d’interaction.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-156">Emulates HoloLens 2 interaction model.</span></span>

   <span data-ttu-id="7e3ea-157">Les interactions basées sur le positionnement précis de la main ou sur l’utilisation du toucher peuvent être simulées dans ce mode.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-157">Interactions that are based on the precise positioning of the hand or use touching can be simulated in this mode.</span></span>

* <span data-ttu-id="7e3ea-158">*Mouvements manuels*: simule un modèle de main simplifié avec robinet d’air et les gestes de base.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-158">*Hand Gestures*: Simulates a simplified hand model with air tap and basic gestures.</span></span>

   <span data-ttu-id="7e3ea-159">émule [HoloLens modèle d’interaction](/windows/mixed-reality/gestures).</span><span class="sxs-lookup"><span data-stu-id="7e3ea-159">Emulates [HoloLens interaction model](/windows/mixed-reality/gestures).</span></span>

   <span data-ttu-id="7e3ea-160">Le focus est contrôlé à l’aide du pointeur en forme de pointage.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-160">Focus is controlled using the Gaze pointer.</span></span> <span data-ttu-id="7e3ea-161">Le mouvement d' *appui sur l’air* est utilisé pour interagir avec les boutons.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-161">The *Air Tap* gesture is used to interact with buttons.</span></span>

* <span data-ttu-id="7e3ea-162">*Contrôleur de mouvement*: simule un contrôleur de mouvement utilisé avec des casques VR qui fonctionne de la même manière que les interactions beaucoup avec les mains articulées.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-162">*Motion Controller*: Simulates a motion controller used with VR headsets that works similarly to far interactions with Articulated Hands.</span></span>

   <span data-ttu-id="7e3ea-163">Émule le casque VR avec le modèle d’interaction de contrôleurs.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-163">Emulates VR headset with controllers interaction model.</span></span>

   <span data-ttu-id="7e3ea-164">Le déclencheur, les touches de manipulation et de menu sont simulés via l’entrée du clavier et de la souris.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-164">The trigger, grab and menu keys are simulated via keyboard and mouse input.</span></span>

### <a name="simulating-controller-movement"></a><span data-ttu-id="7e3ea-165">Simulation du mouvement du contrôleur</span><span class="sxs-lookup"><span data-stu-id="7e3ea-165">Simulating controller movement</span></span>

<span data-ttu-id="7e3ea-166">Maintenez enfoncée la **touche de manipulation du contrôleur gauche/droite** (par défaut : *décalage vers* la gauche pour le contrôleur gauche et *espace* pour le contrôleur droit) afin de prendre le contrôle de l’un des deux contrôleurs.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-166">Press and hold the **Left/Right Controller Manipulation Key** (default: *Left Shift* for left controller and *Space* for right controller) to gain control of either controller.</span></span> <span data-ttu-id="7e3ea-167">Pendant que la touche manipulation est enfoncée, le contrôleur s’affiche dans la fenêtre d’affichage.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-167">While the manipulation key is pressed, the controller will appear in the viewport.</span></span> <span data-ttu-id="7e3ea-168">Une fois la clé de manipulation libérée, les contrôleurs disparaissent après une réduction **du délai d’expiration du contrôleur**.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-168">Once the manipulation key is released, the controllers will disappear after a short **Controller Hide Timeout**.</span></span>

<span data-ttu-id="7e3ea-169">Les contrôleurs peuvent être activés ou désactivés par rapport à l’appareil photo dans la [fenêtre outils de simulation d’entrée](#input-simulation-tools-window) ou en appuyant sur la **touche basculer vers la gauche/droite du contrôleur** (par défaut : *T* pour gauche et *Y* pour droite).</span><span class="sxs-lookup"><span data-stu-id="7e3ea-169">Controllers can be toggled on and frozen relative to the camera in the [input simulation tools window](#input-simulation-tools-window) or by pressing the **Toggle Left/Right Controller Key** (default: *T* for left and *Y* for right).</span></span> <span data-ttu-id="7e3ea-170">Appuyez de nouveau sur la touche bascule pour masquer à nouveau les contrôleurs.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-170">Press the toggle key again to hide the controllers again.</span></span> <span data-ttu-id="7e3ea-171">Pour manipuler les contrôleurs, la **clé de manipulation du contrôleur gauche/droite** doit être maintenue.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-171">To manipulate the controllers, the **Left/Right Controller Manipulation Key** needs to be held.</span></span> <span data-ttu-id="7e3ea-172">Si vous double-Appuyez sur la **touche de manipulation du contrôleur gauche/droite** , vous pouvez également activer/désactiver les contrôleurs.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-172">Double tapping the **Left/Right Controller Manipulation Key** can also toggle the controllers on/off.</span></span>

<span data-ttu-id="7e3ea-173">Le déplacement de la souris déplace le contrôleur dans le plan d’affichage.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-173">Mouse movement will move the controller in the view plane.</span></span> <span data-ttu-id="7e3ea-174">Les contrôleurs peuvent être déplacés davantage ou plus près de l’appareil photo à l’aide de la roulette de la **souris**.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-174">Controllers can be moved further or closer to the camera using the **mouse wheel**.</span></span>

<span data-ttu-id="7e3ea-175">Pour faire pivoter les contrôleurs à l’aide de la souris, maintenez la **touche de manipulation du contrôleur gauche/droite** (*décalage vers la gauche* ou *espace*) *et* le bouton de **rotation du contrôleur** (par défaut : bouton *CTRL gauche* ), puis déplacez la souris pour faire pivoter le contrôleur.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-175">To rotate controllers using the mouse, hold both the **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*) *and* the **Controller Rotate Button** (default: *Left Ctrl* button) and then move the mouse to rotate the controller.</span></span> <span data-ttu-id="7e3ea-176">La vitesse de rotation du contrôleur peut être configurée en modifiant le paramètre **vitesse de rotation du contrôleur** de la souris dans le profil de simulation d’entrée.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-176">Controller rotation speed can be configured by changing the **Mouse Controller Rotation Speed** setting in the input simulation profile.</span></span>

<span data-ttu-id="7e3ea-177">Tout le positionnement manuel peut également être modifié dans la [fenêtre outils de simulation d’entrée](#input-simulation-tools-window), y compris la réinitialisation des mains par défaut.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-177">All hand placement can also changed in the [input simulation tools window](#input-simulation-tools-window), including resetting hands to default.</span></span>

### <a name="additional-profile-settings"></a><span data-ttu-id="7e3ea-178">Paramètres de profil supplémentaires</span><span class="sxs-lookup"><span data-stu-id="7e3ea-178">Additional profile settings</span></span>

* <span data-ttu-id="7e3ea-179">Le **multiplicateur de profondeur du contrôleur** contrôle la sensibilité du déplacement de la profondeur de la roulette de défilement de la souris.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-179">**Controller Depth Multiplier** controls the sensitivity of the mouse scroll wheel depth movement.</span></span> <span data-ttu-id="7e3ea-180">Un nombre plus élevé accélère le zoom du contrôleur.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-180">A larger number will speed up controller zoom.</span></span>
* <span data-ttu-id="7e3ea-181">La **distance de contrôleur par défaut** est la distance initiale des contrôleurs de l’appareil photo.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-181">**Default Controller Distance** is the initial distance of controllers from the camera.</span></span> <span data-ttu-id="7e3ea-182">En cliquant sur les contrôleurs de bouton de **réinitialisation** , vous placez également les contrôleurs à cette distance.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-182">Clicking the **Reset** button controllers will also place controllers at this distance.</span></span>
* <span data-ttu-id="7e3ea-183">Le **volume d’instabilité du contrôleur** ajoute un mouvement aléatoire aux contrôleurs.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-183">**Controller Jitter Amount** adds random motion to controllers.</span></span> <span data-ttu-id="7e3ea-184">Cette fonctionnalité peut être utilisée pour simuler un suivi des contrôleurs inexacts sur l’appareil et garantir que les interactions fonctionnent bien avec les entrées bruyantes.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-184">This feature can be used to simulate inaccurate controller tracking on the device, and ensure that interactions work well with noisy input.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/uRYfwuqsjBQ" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="hand-gestures"></a><span data-ttu-id="7e3ea-185">Mouvements des mains</span><span class="sxs-lookup"><span data-stu-id="7e3ea-185">Hand gestures</span></span>

<span data-ttu-id="7e3ea-186">Les gestes manuels, tels que le pincement, la saisie, l’percer, etc., peuvent également être simulés.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-186">Hand gestures such as pinching, grabbing, poking, etc. can also be simulated.</span></span>

1. <span data-ttu-id="7e3ea-187">Activer le contrôle de main à l’aide de la **clé de manipulation du contrôleur gauche/droite** (*décalage vers la gauche* ou *espace*)</span><span class="sxs-lookup"><span data-stu-id="7e3ea-187">Enable hand control using the **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*)</span></span>

2. <span data-ttu-id="7e3ea-188">Lors de la manipulation, appuyez et maintenez enfoncé un bouton de la souris pour effectuer un mouvement manuel.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-188">While manipulating, press and hold a mouse button to perform a hand gesture.</span></span>

<span data-ttu-id="7e3ea-189">Chacun des boutons de la souris peut être mappé pour transformer la forme main en un geste différent en utilisant les paramètres de mouvement de la *souris à gauche/au milieu/à droite* .</span><span class="sxs-lookup"><span data-stu-id="7e3ea-189">Each of the mouse buttons can be mapped to transform the hand shape into a different gesture using the *Left/Middle/Right Mouse Hand Gesture* settings.</span></span> <span data-ttu-id="7e3ea-190">Le *mouvement de main par défaut* est la forme de la main quand aucun bouton n’est enfoncé.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-190">The *Default Hand Gesture* is the shape of the hand when no button is pressed.</span></span>

> [!NOTE]
> <span data-ttu-id="7e3ea-191">Le geste de *pincement* est le seul mouvement qui exécute l’action « Select » à ce stade.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-191">The *Pinch* gesture is the only gesture that performs the "Select" action at this point.</span></span>

### <a name="one-hand-manipulation"></a><span data-ttu-id="7e3ea-192">Manipulation en une seule main</span><span class="sxs-lookup"><span data-stu-id="7e3ea-192">One-hand manipulation</span></span>

1. <span data-ttu-id="7e3ea-193">Appuyez et maintenez enfoncée la **touche de manipulation du contrôleur gauche/droite** (*décalage vers la gauche* ou *espace*)</span><span class="sxs-lookup"><span data-stu-id="7e3ea-193">Press and hold **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*)</span></span>
2. <span data-ttu-id="7e3ea-194">Pointer sur l’objet</span><span class="sxs-lookup"><span data-stu-id="7e3ea-194">Point at object</span></span>
3. <span data-ttu-id="7e3ea-195">Maintenir le bouton de la souris enfoncé</span><span class="sxs-lookup"><span data-stu-id="7e3ea-195">Hold mouse button to pinch</span></span>
4. <span data-ttu-id="7e3ea-196">Utilisez la souris pour déplacer l’objet</span><span class="sxs-lookup"><span data-stu-id="7e3ea-196">Use your mouse to move the object</span></span>
5. <span data-ttu-id="7e3ea-197">Relâchez le bouton de la souris pour arrêter l’interaction</span><span class="sxs-lookup"><span data-stu-id="7e3ea-197">Release the mouse button to stop interaction</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/rM0xaHam6wM" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="two-hand-manipulation"></a><span data-ttu-id="7e3ea-198">Manipulation à deux mains</span><span class="sxs-lookup"><span data-stu-id="7e3ea-198">Two-hand manipulation</span></span>

<span data-ttu-id="7e3ea-199">Pour manipuler des objets avec deux mains en même temps, le mode de main permanent est recommandé.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-199">For manipulating objects with two hands at the same time, the persistent hand mode is recommended.</span></span>

1. <span data-ttu-id="7e3ea-200">Activez les deux mains en appuyant sur les touches bascule (*T/Y*).</span><span class="sxs-lookup"><span data-stu-id="7e3ea-200">Toggle on both hands by pressing the toggle keys (*T/Y*).</span></span>
1. <span data-ttu-id="7e3ea-201">Manipuler une seule main à la fois :</span><span class="sxs-lookup"><span data-stu-id="7e3ea-201">Manipulate one hand at a time:</span></span>
    1. <span data-ttu-id="7e3ea-202">Conserver de l' **espace** pour contrôler la main droite</span><span class="sxs-lookup"><span data-stu-id="7e3ea-202">Hold **Space** to control the right hand</span></span>
    1. <span data-ttu-id="7e3ea-203">Déplacer la main vers l’emplacement où vous souhaitez récupérer l’objet</span><span class="sxs-lookup"><span data-stu-id="7e3ea-203">Move the hand to where you want to grab the object</span></span>
    1. <span data-ttu-id="7e3ea-204">Appuyez sur le **bouton gauche** de la souris pour activer le mouvement de *pincement* .</span><span class="sxs-lookup"><span data-stu-id="7e3ea-204">Press the **left mouse button** to activate the *Pinch* gesture.</span></span>
    1. <span data-ttu-id="7e3ea-205">Libérez de l' **espace** pour arrêter le contrôle de la main droite.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-205">Release **Space** to stop controlling the right hand.</span></span> <span data-ttu-id="7e3ea-206">La main sera figée en place et sera verrouillée dans le geste de *pincement* , car elle n’est plus manipulée.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-206">The hand will be frozen in place and be locked into the *Pinch* gesture since it is no longer being manipulated.</span></span>
1. <span data-ttu-id="7e3ea-207">Répétez le processus en faisant glisser le même objet en une seconde.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-207">Repeat the process with the other hand, grabbing the same object in a second spot.</span></span>
1. <span data-ttu-id="7e3ea-208">Maintenant que les deux mains attirent le même objet, vous pouvez les déplacer pour effectuer une manipulation à deux mains.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-208">Now that both hands are grabbing the same object, you can move either of them to perform two-handed manipulation.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qol5OFNfN14" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="ggv-gaze-gesture-and-voice-interaction"></a><span data-ttu-id="7e3ea-209">Interaction GGV (point de regard, geste et voix)</span><span class="sxs-lookup"><span data-stu-id="7e3ea-209">GGV (Gaze, Gesture, and Voice) interaction</span></span>

<span data-ttu-id="7e3ea-210">Par défaut, l’interaction avec GGV est activée dans l’éditeur, alors qu’il n’y a aucune mains articulées dans la scène.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-210">By default, GGV interaction is enabled in-editor while there are no articulated hands present in the scene.</span></span>

1. <span data-ttu-id="7e3ea-211">Faire pivoter l’appareil photo pour pointer le curseur en regard de l’objet interagi (bouton droit de la souris)</span><span class="sxs-lookup"><span data-stu-id="7e3ea-211">Rotate the camera to point the gaze cursor at the interactable object (right mouse button)</span></span>
1. <span data-ttu-id="7e3ea-212">Cliquez et maintenez le **bouton gauche de la souris** enfoncé pour interagir</span><span class="sxs-lookup"><span data-stu-id="7e3ea-212">Click and hold **left mouse button** to interact</span></span>
1. <span data-ttu-id="7e3ea-213">Faites pivoter à nouveau l’appareil pour manipuler l’objet</span><span class="sxs-lookup"><span data-stu-id="7e3ea-213">Rotate the camera again to manipulate the object</span></span>

<span data-ttu-id="7e3ea-214">Vous pouvez désactiver ce mode en basculant sur l’option est disponible en *entrée libre* à l’intérieur du profil de simulation d’entrée.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-214">You can turn this off by toggling the *Is Hand Free Input Enabled* option inside the Input Simulation Profile.</span></span>

<span data-ttu-id="7e3ea-215">En outre, vous pouvez utiliser des mains simulées pour l’interaction GGV</span><span class="sxs-lookup"><span data-stu-id="7e3ea-215">In addition, you can use simulated hands for GGV interaction</span></span>

1. <span data-ttu-id="7e3ea-216">Activer la simulation GGV en basculant en **mode de simulation manuelle** sur les *gestes* dans le [profil de simulation d’entrée](#enabling-the-input-simulation-service)</span><span class="sxs-lookup"><span data-stu-id="7e3ea-216">Enable GGV simulation by switching **Hand Simulation Mode** to *Gestures* in the [Input Simulation Profile](#enabling-the-input-simulation-service)</span></span>
1. <span data-ttu-id="7e3ea-217">Faire pivoter l’appareil photo pour pointer le curseur en regard de l’objet interagi (bouton droit de la souris)</span><span class="sxs-lookup"><span data-stu-id="7e3ea-217">Rotate the camera to point the gaze cursor at the interactable object (right mouse button)</span></span>
1. <span data-ttu-id="7e3ea-218">Conserver de l' **espace** pour contrôler la main droite</span><span class="sxs-lookup"><span data-stu-id="7e3ea-218">Hold **Space** to control the right hand</span></span>
1. <span data-ttu-id="7e3ea-219">Cliquez et maintenez le **bouton gauche de la souris** enfoncé pour interagir</span><span class="sxs-lookup"><span data-stu-id="7e3ea-219">Click and hold **left mouse button** to interact</span></span>
1. <span data-ttu-id="7e3ea-220">Utilisez la souris pour déplacer l’objet</span><span class="sxs-lookup"><span data-stu-id="7e3ea-220">Use your mouse to move the object</span></span>
1. <span data-ttu-id="7e3ea-221">Relâchez le bouton de la souris pour arrêter l’interaction</span><span class="sxs-lookup"><span data-stu-id="7e3ea-221">Release the mouse button to stop interaction</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/6841rRMdqWw" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="raising-teleport-events"></a><span data-ttu-id="7e3ea-222">Déclenchement d’événements de télégénération</span><span class="sxs-lookup"><span data-stu-id="7e3ea-222">Raising Teleport Events</span></span>

<span data-ttu-id="7e3ea-223">pour déclencher l’événement de télétransmission dans la simulation d’entrée, configurez le mouvement de la main Paramètres dans le profil de simulation d’entrée de sorte que l’un effectue le mouvement de **démarrage** de la télétransmission pendant que l’autre effectue **le geste de** télétransmission.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-223">To raise the teleport event in input simulation, configure the Hand Gesture Settings in the Input Simulation Profile so that one performs the **Teleport Start** Gesture while the other performs the **Teleport End** Gesture.</span></span> <span data-ttu-id="7e3ea-224">Le geste de **démarrage** de la téléscripteur affiche le pointeur de téléaction, tandis que **le gesure de** téléscription termine l’action de téléscription et déplace l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-224">The **Teleport Start** gesture will bring up the Teleport Pointer, while the **Teleport End** gesure will complete the teleport action and move the user.</span></span>

<span data-ttu-id="7e3ea-225">La position y de la téléchargement résultante dépend du déplacement de la caméra le long de l’axe y.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-225">The y-position of your resulting teleport is dependent on the camera's displacement along the y-axis.</span></span> <span data-ttu-id="7e3ea-226">Dans l’éditeur, il s’agit de 0 par défaut. Utilisez donc les touches **Q** et **E** pour l’ajuster à la hauteur appropriée.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-226">In editor, this is 0 by default, so use the **Q** and **E** keys to adjust it to the appropriate height.</span></span>

![téléParamètres de la Simulation d’entrée](../images/input-simulation/InputSimulationTeleport.gif)

### <a name="motion-controller-interaction"></a><span data-ttu-id="7e3ea-228">Interaction du contrôleur de mouvement</span><span class="sxs-lookup"><span data-stu-id="7e3ea-228">Motion controller interaction</span></span>

<span data-ttu-id="7e3ea-229">Les contrôleurs de mouvement simulés peuvent être manipulés de la même façon que les mains articulées.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-229">The simulated motion controllers can be manipulated the same way articulated hands are.</span></span> <span data-ttu-id="7e3ea-230">Le modèle d’interaction est semblable à l’interaction Far de la main, tandis que le déclencheur, les touches de manipulation et de menu sont mappées respectivement au *bouton gauche de la souris*, à la clé *G* et *M* .</span><span class="sxs-lookup"><span data-stu-id="7e3ea-230">The interaction model is similar to far interaction of articulated hand while the trigger, grab and menu keys are mapped to *left mouse button*, *G* and *M* key respectively.</span></span>

### <a name="eye-tracking"></a><span data-ttu-id="7e3ea-231">Eye-tracking</span><span class="sxs-lookup"><span data-stu-id="7e3ea-231">Eye tracking</span></span>

<span data-ttu-id="7e3ea-232">Vous pouvez activer la [simulation du suivi des yeux](../input/eye-tracking/eye-tracking-basic-setup.md#simulating-eye-tracking-in-the-unity-editor) en activant l’option **simuler la position des yeux** dans le profil de [simulation d’entrée](#enabling-the-input-simulation-service).</span><span class="sxs-lookup"><span data-stu-id="7e3ea-232">[Eye tracking simulation](../input/eye-tracking/eye-tracking-basic-setup.md#simulating-eye-tracking-in-the-unity-editor) can be enabled by checking the **Simulate Eye Position** option in the [Input Simulation Profile](#enabling-the-input-simulation-service).</span></span> <span data-ttu-id="7e3ea-233">Cela ne doit pas être utilisé avec les interactions de style de contrôleur de mouvement ou GGV (Vérifiez que le **mode de simulation du contrôleur par défaut** est défini sur *main*).</span><span class="sxs-lookup"><span data-stu-id="7e3ea-233">This should not be used with GGV or motion controller style interactions (so ensure that **Default Controller Simulation Mode** is set to *Articulated Hand*).</span></span>

## <a name="input-simulation-tools-window"></a><span data-ttu-id="7e3ea-234">Fenêtre outils de simulation d’entrée</span><span class="sxs-lookup"><span data-stu-id="7e3ea-234">Input simulation tools window</span></span>

<span data-ttu-id="7e3ea-235">activez la fenêtre outils de simulation d’entrée à partir du  >    >    >  menu **simulation d’entrée** de la réalité mixte Shared Computer Toolkit utilitaires.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-235">Enable the input simulation tools window from the  **Mixed Reality** > **Toolkit** > **Utilities** > **Input Simulation** menu.</span></span> <span data-ttu-id="7e3ea-236">Cette fenêtre permet d’accéder à l’état de la simulation d’entrée en mode lecture.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-236">This window provides access to the state of input simulation during play mode.</span></span>

## <a name="viewport-buttons-optional"></a><span data-ttu-id="7e3ea-237">Boutons de la fenêtre d’affichage (facultatif)</span><span class="sxs-lookup"><span data-stu-id="7e3ea-237">Viewport buttons (optional)</span></span>

<span data-ttu-id="7e3ea-238">Un Prefab pour les boutons de l’éditeur pour contrôler le placement de base peut être spécifié dans le profil de simulation d’entrée sous **indicateurs Prefab**.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-238">A prefab for in-editor buttons to control basic hand placement can be specified in the input simulation profile under **Indicators Prefab**.</span></span> <span data-ttu-id="7e3ea-239">Il s’agit d’un utilitaire facultatif qui permet d’accéder aux mêmes fonctionnalités dans la [fenêtre outils de simulation d’entrée](#input-simulation-tools-window).</span><span class="sxs-lookup"><span data-stu-id="7e3ea-239">This is an optional utility, the same features can be accessed in the [input simulation tools window](#input-simulation-tools-window).</span></span>

> [!NOTE]
> <span data-ttu-id="7e3ea-240">Les indicateurs de la fenêtre d’affichage sont désactivés par défaut, car ils peuvent parfois interférer avec les interactions de l’interface utilisateur Unity.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-240">The viewport indicators are disabled by default, as they currently can sometimes interfere with Unity UI interactions.</span></span> <span data-ttu-id="7e3ea-241">Consultez [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106)de problèmes.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-241">See issue [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106).</span></span> <span data-ttu-id="7e3ea-242">Pour activer, ajoutez le Prefab InputSimulationIndicators à **indicateurs Prefab**.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-242">To enable, add the InputSimulationIndicators prefab to **Indicators Prefab**.</span></span>

<span data-ttu-id="7e3ea-243">Les icônes de main affichent l’état des mains simulées :</span><span class="sxs-lookup"><span data-stu-id="7e3ea-243">Hand icons show the state of the simulated hands:</span></span>

* ![Icône de main non suivie](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Untracked.png) <span data-ttu-id="7e3ea-245&quot;>La main n’effectue pas de suivi.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;7e3ea-245&quot;>The hand is not tracking.</span></span> <span data-ttu-id=&quot;7e3ea-246&quot;>Cliquez pour activer la main.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;7e3ea-246&quot;>Click to enable the hand.</span></span>
* <span data-ttu-id=&quot;7e3ea-247&quot;>![Icône de main](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png &quot;Icône de main") La main est suivie, mais n’est pas contrôlée par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-247">![Tracked hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png "Tracked hand icon") The hand is tracked, but not controlled by the user.</span></span> <span data-ttu-id="7e3ea-248">Cliquez pour masquer la main.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-248">Click to hide the hand.</span></span>
* <span data-ttu-id="7e3ea-249">![Icône de main contrôlée](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "Icône de main contrôlée") La main est suivie et contrôlée par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-249">![Controlled hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "Controlled hand icon") The hand is tracked and controlled by the user.</span></span> <span data-ttu-id="7e3ea-250">Cliquez pour masquer la main.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-250">Click to hide the hand.</span></span>
* <span data-ttu-id="7e3ea-251">![Icône réinitialiser la main](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "Icône réinitialiser la main") Cliquez pour rétablir la position par défaut de la main.</span><span class="sxs-lookup"><span data-stu-id="7e3ea-251">![Reset hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "Reset hand icon") Click to reset the hand to default position.</span></span>


## <a name="see-also"></a><span data-ttu-id="7e3ea-252">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7e3ea-252">See also</span></span>

* <span data-ttu-id="7e3ea-253">[Profil du système d’entrée](../input/input-providers.md).</span><span class="sxs-lookup"><span data-stu-id="7e3ea-253">[Input System profile](../input/input-providers.md).</span></span>
