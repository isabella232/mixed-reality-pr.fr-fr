---
title: Objet avec interaction possible
description: Découvrez comment déclencher des événements, fournir des signaux visuels et interagir avec des objets dans vos applications de réalité mixte.
author: cre8ivepark
ms.author: v-hferrone
ms.date: 06/06/2019
ms.topic: article
keywords: Réalité mixte, contrôles, interaction, signaux, interface utilisateur, expérience utilisateur, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, HoloLens, MRTK, boîte à outils de réalité mixte, audio
ms.openlocfilehash: d0dc8ce6425d597d04b47a6c8b08f72534488594
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007199"
---
# <a name="interactable-object"></a><span data-ttu-id="01635-104">Objet avec interaction possible</span><span class="sxs-lookup"><span data-stu-id="01635-104">Interactable object</span></span>

![Objets Interactible](images/UX_Hero_Interactable.jpg)

<span data-ttu-id="01635-106">Un bouton a longtemps été une métaphore utilisée pour déclencher un événement dans le monde abstrait en 2D.</span><span class="sxs-lookup"><span data-stu-id="01635-106">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="01635-107">Dans le monde de la réalité mixte en trois dimensions, nous n’avons plus à limiter le monde de l’abstraction.</span><span class="sxs-lookup"><span data-stu-id="01635-107">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="01635-108">Tout peut être un **objet** pouvant être utilisé qui déclenche un événement.</span><span class="sxs-lookup"><span data-stu-id="01635-108">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="01635-109">Un objet pouvant être interagi peut être n’importe quoi, d’une tasse de café sur une table, à une bulle dans Midair.</span><span class="sxs-lookup"><span data-stu-id="01635-109">An interactable object can be anything from a coffee cup on a table to a balloon in midair.</span></span> <span data-ttu-id="01635-110">Nous utilisons toujours les boutons traditionnels dans certaines situations, par exemple dans l’interface utilisateur du dialogue.</span><span class="sxs-lookup"><span data-stu-id="01635-110">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="01635-111">La représentation visuelle du bouton dépend du contexte.</span><span class="sxs-lookup"><span data-stu-id="01635-111">The visual representation of the button depends on the context.</span></span>

<br>

---

## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="01635-112">Propriétés importantes de l’objet interagiable</span><span class="sxs-lookup"><span data-stu-id="01635-112">Important properties of the interactable object</span></span>

### <a name="visual-cues"></a><span data-ttu-id="01635-113">Signaux visuels</span><span class="sxs-lookup"><span data-stu-id="01635-113">Visual cues</span></span>

<span data-ttu-id="01635-114">Les signaux visuels sont des signaux sensorielles de la lumière, reçus par l’oeil, et traités par le système visuel lors de la perception visuelle.</span><span class="sxs-lookup"><span data-stu-id="01635-114">Visual cues are sensory cues from light, received by the eye, and processed by the visual system during visual perception.</span></span> <span data-ttu-id="01635-115">Étant donné que le système visuel est dominant dans de nombreuses espèces, en particulier les êtres humains, les signaux visuels constituent une source d’informations importante dans la manière dont le monde est perçu.</span><span class="sxs-lookup"><span data-stu-id="01635-115">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="01635-116">Étant donné que les objets holographiques sont mélangés à l’environnement réel dans la réalité mixte, il peut être difficile de comprendre les objets avec lesquels vous pouvez interagir.</span><span class="sxs-lookup"><span data-stu-id="01635-116">Since the holographic objects are blended with the real-world environment in mixed reality, it could be difficult to understand which objects you can interact with.</span></span> <span data-ttu-id="01635-117">Pour tous les objets interactifs dans votre expérience, il est important de fournir des signaux visuels différenciés pour chaque État d’entrée.</span><span class="sxs-lookup"><span data-stu-id="01635-117">For any interactable objects in your experience, it's important to provide differentiated visual cues for each input state.</span></span> <span data-ttu-id="01635-118">Cela permet à l’utilisateur de comprendre quelle partie de votre expérience est interactive et de rendre l’utilisateur confiant en utilisant une méthode d’interaction cohérente.</span><span class="sxs-lookup"><span data-stu-id="01635-118">This helps the user understand which part of your experience is interactable and makes the user confident by using a consistent interaction method.</span></span>

<br>

---

### <a name="far-interactions"></a><span data-ttu-id="01635-119">Interactions lointaines</span><span class="sxs-lookup"><span data-stu-id="01635-119">Far interactions</span></span>

<span data-ttu-id="01635-120">Pour tous les objets que l’utilisateur peut interagir avec le point de vue du point de vue du regard, du rayon de la main et du contrôleur de mouvement, nous vous recommandons d’avoir un signal visuel différent pour ces trois États d’entrée :</span><span class="sxs-lookup"><span data-stu-id="01635-120">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend having different visual cue for these three input states:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="01635-121">![interactibleobject-États-par défaut](images/interactibleobject-states-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="01635-121">![interactibleobject-states-default](images/interactibleobject-states-default.jpg)</span></span><br>
       <span data-ttu-id="01635-122">**État par défaut (observation)**</span><span class="sxs-lookup"><span data-stu-id="01635-122">**Default (Observation) state**</span></span><br>
        <span data-ttu-id="01635-123">État d’inactivité par défaut de l’objet.</span><span class="sxs-lookup"><span data-stu-id="01635-123">Default idle state of the object.</span></span>
    <span data-ttu-id="01635-124">Le curseur ne se trouve pas sur l’objet.</span><span class="sxs-lookup"><span data-stu-id="01635-124">The cursor isn't on the object.</span></span> <span data-ttu-id="01635-125">La main n’est pas détectée.</span><span class="sxs-lookup"><span data-stu-id="01635-125">Hand isn't detected.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="01635-126">![interactibleobject-États-ciblés](images/interactibleobject-states-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="01635-126">![interactibleobject-states-targeted](images/interactibleobject-states-targeted.jpg)</span></span><br>
        <span data-ttu-id="01635-127">**État ciblé (survol)**</span><span class="sxs-lookup"><span data-stu-id="01635-127">**Targeted (Hover) state**</span></span><br>
        <span data-ttu-id="01635-128">Lorsque l’objet est ciblé avec un curseur en forme de pointage, le pointeur de proximité d’un doigt ou d’un contrôleur de mouvement.</span><span class="sxs-lookup"><span data-stu-id="01635-128">When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
    <span data-ttu-id="01635-129">Le curseur se trouve sur l’objet.</span><span class="sxs-lookup"><span data-stu-id="01635-129">The cursor is on the object.</span></span> <span data-ttu-id="01635-130">La main est détectée, prête.</span><span class="sxs-lookup"><span data-stu-id="01635-130">Hand is detected, ready.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="01635-131">![interactibleobject-États activés](images/interactibleobject-states-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="01635-131">![interactibleobject-states-pressed](images/interactibleobject-states-pressed.jpg)</span></span><br>
       <span data-ttu-id="01635-132">**État appuyé**</span><span class="sxs-lookup"><span data-stu-id="01635-132">**Pressed state**</span></span><br>
        <span data-ttu-id="01635-133">Quand l’objet est enfoncé avec un mouvement d’appui sur l’air, appuyez sur le bouton de sélection du contrôleur de mouvement ou du doigt.</span><span class="sxs-lookup"><span data-stu-id="01635-133">When the object is pressed with an air tap gesture, finger press or motion controller's select button.</span></span>
    <span data-ttu-id="01635-134">Le curseur se trouve sur l’objet.</span><span class="sxs-lookup"><span data-stu-id="01635-134">The cursor is on the object.</span></span> <span data-ttu-id="01635-135">La main est détectée, frappée d’air.</span><span class="sxs-lookup"><span data-stu-id="01635-135">Hand is detected, air tapped.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

<span data-ttu-id="01635-136">Vous pouvez utiliser des techniques telles que la mise en surbrillance ou la mise à l’échelle pour fournir des signaux visuels pour l’état d’entrée de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="01635-136">You can use techniques such as highlighting or scaling to provide visual cues for the user’s input state.</span></span> <span data-ttu-id="01635-137">En réalité mixte, vous trouverez des exemples de visualisation de différents États d’entrée dans le menu Démarrer et avec les boutons de la barre d’application.</span><span class="sxs-lookup"><span data-stu-id="01635-137">In mixed reality, you can find examples of visualizing different input states on the Start menu and with app bar buttons.</span></span> 

<span data-ttu-id="01635-138">Voici à quoi ressemblent ces États sur un **bouton holographique**:</span><span class="sxs-lookup"><span data-stu-id="01635-138">Here's what these states look like on a **holographic button**:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="01635-139">![interactibleobject-États-par défaut](images/MRTK_InteractableState-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="01635-139">![interactibleobject-states-default](images/MRTK_InteractableState-default.jpg)</span></span><br>
       <span data-ttu-id="01635-140">**État par défaut (observation)**</span><span class="sxs-lookup"><span data-stu-id="01635-140">**Default (Observation) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="01635-141">![interactibleobject-États-ciblés](images/MRTK_InteractableState-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="01635-141">![interactibleobject-states-targeted](images/MRTK_InteractableState-targeted.jpg)</span></span><br>
        <span data-ttu-id="01635-142">**État ciblé (survol)**</span><span class="sxs-lookup"><span data-stu-id="01635-142">**Targeted (Hover) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="01635-143">![interactibleobject-États activés](images/MRTK_InteractableState-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="01635-143">![interactibleobject-states-pressed](images/MRTK_InteractableState-pressed.jpg)</span></span><br>
       <span data-ttu-id="01635-144">**État appuyé**</span><span class="sxs-lookup"><span data-stu-id="01635-144">**Pressed state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a><span data-ttu-id="01635-145">Interactions proches (direct)</span><span class="sxs-lookup"><span data-stu-id="01635-145">Near interactions (direct)</span></span> 

<span data-ttu-id="01635-146">HoloLens 2 prend en charge l’entrée de suivi articulé, qui vous permet d’interagir avec les objets.</span><span class="sxs-lookup"><span data-stu-id="01635-146">HoloLens 2 supports articulated hand tracking input, which allows you to interact with objects.</span></span> <span data-ttu-id="01635-147">Sans commentaires haptique et perception parfaite de la profondeur, il peut être difficile de savoir à quel moment votre main provient d’un objet ou si vous le touchez.</span><span class="sxs-lookup"><span data-stu-id="01635-147">Without haptic feedback and perfect depth perception, it can be hard to tell how far away your hand is from an object or whether you're touching it.</span></span> <span data-ttu-id="01635-148">Il est important de fournir suffisamment de signaux visuels pour communiquer l’état de l’objet, en particulier l’état de vos mains en fonction de cet objet.</span><span class="sxs-lookup"><span data-stu-id="01635-148">It's important to provide enough visual cues to communicate the state of the object, in particular the state of your hands based on that object.</span></span>

<span data-ttu-id="01635-149">Utilisez les commentaires visuels pour communiquer les États suivants :</span><span class="sxs-lookup"><span data-stu-id="01635-149">Use visual feedback to communicate the following states:</span></span>
* <span data-ttu-id="01635-150">**Valeur par défaut (observation)**: état inactif par défaut de l’objet.</span><span class="sxs-lookup"><span data-stu-id="01635-150">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="01635-151">**Survol**: quand une main est proche d’un hologramme, modifiez les éléments visuels pour indiquer que la main cible l’hologramme.</span><span class="sxs-lookup"><span data-stu-id="01635-151">**Hover**: When a hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="01635-152">**Distance et point d’interaction**: à l’approche d’un hologramme, concevoir des commentaires pour communiquer le point d’interaction projeté et jusqu’à partir de l’objet le doigt</span><span class="sxs-lookup"><span data-stu-id="01635-152">**Distance and point of interaction**: As the hand approaches a hologram, design feedback to communicate the projected point of interaction, and how far from the object the finger is</span></span>
* <span data-ttu-id="01635-153">**Début du contact**: modifiez les éléments visuels (Light, Color) pour signaler qu’une pression tactile s’est produite.</span><span class="sxs-lookup"><span data-stu-id="01635-153">**Contact begins**: Change visuals (light, color) to communicate that a touch has occurred</span></span>
* <span data-ttu-id="01635-154">**Saisi**: modifier les éléments visuels (clair, couleur) quand l’objet est saisi</span><span class="sxs-lookup"><span data-stu-id="01635-154">**Grasped**: Change visuals (light, color) when the object is grasped</span></span>
* <span data-ttu-id="01635-155">**Fin du contact**: modifier les éléments visuels (Light, Color) quand Touch est terminé</span><span class="sxs-lookup"><span data-stu-id="01635-155">**Contact ends**: Change visuals (light, color) when touch has ended</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="01635-156">![Pointage (FAR)](images/640px-interactibleobject-states-near-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="01635-156">![Hover (Far)](images/640px-interactibleobject-states-near-hover.jpg)</span></span><br>
        <span data-ttu-id="01635-157">**Pointage (FAR)**</span><span class="sxs-lookup"><span data-stu-id="01635-157">**Hover (Far)**</span></span><br>
        <span data-ttu-id="01635-158">Mise en surbrillance en fonction de la proximité de la main.</span><span class="sxs-lookup"><span data-stu-id="01635-158">Highlighting based on the proximity of the hand.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="01635-159">![Pointage (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span><span class="sxs-lookup"><span data-stu-id="01635-159">![Hover (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span></span><br>
        <span data-ttu-id="01635-160">**Pointage (Near)**</span><span class="sxs-lookup"><span data-stu-id="01635-160">**Hover (Near)**</span></span><br>
        <span data-ttu-id="01635-161">Mettez en surbrillance les changements de taille en fonction de la distance à la main.</span><span class="sxs-lookup"><span data-stu-id="01635-161">Highlight size changes based on the distance to the hand.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="01635-162">![Toucher/appuyer](images/640px-interactibleobject-states-near-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="01635-162">![Touch / press](images/640px-interactibleobject-states-near-press.jpg)</span></span><br>
        <span data-ttu-id="01635-163">**Toucher/appuyer**</span><span class="sxs-lookup"><span data-stu-id="01635-163">**Touch / press**</span></span><br>
        <span data-ttu-id="01635-164">Commentaires Audio Visual plus.</span><span class="sxs-lookup"><span data-stu-id="01635-164">Visual plus audio feedback.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="01635-165">![Maîtriser](images/640px-interactibleobject-states-near-grasp.jpg)</span><span class="sxs-lookup"><span data-stu-id="01635-165">![Grasp](images/640px-interactibleobject-states-near-grasp.jpg)</span></span><br>
        <span data-ttu-id="01635-166">**Maîtriser**</span><span class="sxs-lookup"><span data-stu-id="01635-166">**Grasp**</span></span><br>
        <span data-ttu-id="01635-167">Commentaires Audio Visual plus.</span><span class="sxs-lookup"><span data-stu-id="01635-167">Visual plus audio feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

<br>

---

<span data-ttu-id="01635-168">Un [bouton sur HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) est un exemple de la façon dont les différents États d’interaction d’entrée sont visualisés :</span><span class="sxs-lookup"><span data-stu-id="01635-168">A [button on HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) is an example of how the different input interaction states are visualized:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="01635-169">![Par défaut](images/640px-interactibleobject-pressablebutton-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="01635-169">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span></span><br>
        <span data-ttu-id="01635-170">**Par défaut**</span><span class="sxs-lookup"><span data-stu-id="01635-170">**Default**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="01635-171">![Pointage](images/640px-interactibleobject-pressablebutton-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="01635-171">![Hover](images/640px-interactibleobject-pressablebutton-hover.jpg)</span></span><br>
        <span data-ttu-id="01635-172">**Pointage**</span><span class="sxs-lookup"><span data-stu-id="01635-172">**Hover**</span></span><br>
        <span data-ttu-id="01635-173">Révélez un effet d’éclairage basé sur la proximité.</span><span class="sxs-lookup"><span data-stu-id="01635-173">Reveal a proximity-based lighting effect.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="01635-174">![Interface tactile](images/640px-interactibleobject-pressablebutton-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="01635-174">![Touch](images/640px-interactibleobject-pressablebutton-touch.jpg)</span></span><br>
        <span data-ttu-id="01635-175">**Interface tactile**</span><span class="sxs-lookup"><span data-stu-id="01635-175">**Touch**</span></span><br>
        <span data-ttu-id="01635-176">Afficher l’effet de l’ondulation.</span><span class="sxs-lookup"><span data-stu-id="01635-176">Show ripple effect.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="01635-177">![Appuyez sur](images/640px-interactibleobject-pressablebutton-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="01635-177">![Press](images/640px-interactibleobject-pressablebutton-press.jpg)</span></span><br>
        <span data-ttu-id="01635-178">**Appuyez sur**</span><span class="sxs-lookup"><span data-stu-id="01635-178">**Press**</span></span><br>
        <span data-ttu-id="01635-179">Déplacez la plaque avant.</span><span class="sxs-lookup"><span data-stu-id="01635-179">Move the front plate.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a><span data-ttu-id="01635-180">Le signal visuel « Ring » sur HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="01635-180">The "ring" visual cue on HoloLens 2</span></span><br>
        <span data-ttu-id="01635-181">Sur HoloLens 2, il existe un indice visuel supplémentaire qui peut aider la perception de l’utilisateur en profondeur.</span><span class="sxs-lookup"><span data-stu-id="01635-181">On HoloLens 2, there's an extra visual cue, which can help the user's perception of depth.</span></span> <span data-ttu-id="01635-182">Un anneau proche de son doigt s’affiche et s’adapte à mesure que l’approche est plus proche de l’objet.</span><span class="sxs-lookup"><span data-stu-id="01635-182">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="01635-183">L’anneau se convergera en un point lorsque l’état appuyé est atteint.</span><span class="sxs-lookup"><span data-stu-id="01635-183">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="01635-184">Cet accord visuel aide l’utilisateur à comprendre à quel moment il s’agit de l’objet.</span><span class="sxs-lookup"><span data-stu-id="01635-184">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="01635-185">*Boucle vidéo : exemple de retour visuel basé sur la proximité d’un cadre englobant*</span><span class="sxs-lookup"><span data-stu-id="01635-185">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="01635-186">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="01635-186">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="01635-187">![Commentaires visuels à proximité](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="01635-187">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a><span data-ttu-id="01635-188">Signaux audio</span><span class="sxs-lookup"><span data-stu-id="01635-188">Audio cues</span></span>

<span data-ttu-id="01635-189">Pour les interactions directes, les retours audio corrects peuvent améliorer considérablement l’expérience utilisateur.</span><span class="sxs-lookup"><span data-stu-id="01635-189">For direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="01635-190">Utilisez des commentaires audio pour communiquer les signaux suivants :</span><span class="sxs-lookup"><span data-stu-id="01635-190">Use audio feedback to communicate the following cues:</span></span>
* <span data-ttu-id="01635-191">**Début du contact**: émettre un signal sonore à la début de la saisie tactile</span><span class="sxs-lookup"><span data-stu-id="01635-191">**Contact begins**: Play sound when touch begins</span></span>
* <span data-ttu-id="01635-192">Fin du **contact**: émettre un signal sonore à l’extrémité tactile</span><span class="sxs-lookup"><span data-stu-id="01635-192">**Contact ends**: Play sound on touch end</span></span>
* <span data-ttu-id="01635-193">**Début** de la manipulation : émettre un signal sonore lors du démarrage de la manipulation</span><span class="sxs-lookup"><span data-stu-id="01635-193">**Grab begins**: Play sound when grab starts</span></span>
* <span data-ttu-id="01635-194">Opérations de **manipulation**: émettre un signal sonore lorsque la sélection est terminée</span><span class="sxs-lookup"><span data-stu-id="01635-194">**Grab ends**: Play sound when grab ends</span></span>

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a><span data-ttu-id="01635-195">Commander avec la voix</span><span class="sxs-lookup"><span data-stu-id="01635-195">Voice commanding</span></span><br>
        <span data-ttu-id="01635-196">Pour tous les objets interactifs, il est important de prendre en charge d’autres options d’interaction.</span><span class="sxs-lookup"><span data-stu-id="01635-196">For any interactable objects, it's important to support alternative interaction options.</span></span> <span data-ttu-id="01635-197">Par défaut, nous vous recommandons de prendre en charge les [commandes vocales](../out-of-scope/voice-design.md) pour tous les objets qui sont interactifs.</span><span class="sxs-lookup"><span data-stu-id="01635-197">By default, we recommend that [voice commanding](../out-of-scope/voice-design.md) be supported for any objects that are interactable.</span></span> <span data-ttu-id="01635-198">Pour améliorer la détectabilité, vous pouvez également fournir une info-bulle pendant l’état de survol.</span><span class="sxs-lookup"><span data-stu-id="01635-198">To improve discoverability, you can also provide a tooltip during the hover state.</span></span><br>
        <br>
        <span data-ttu-id="01635-199">*Image : info-bulle pour la commande vocale*</span><span class="sxs-lookup"><span data-stu-id="01635-199">*Image: Tooltip for the voice command*</span></span>
    :::column-end:::
        :::column:::
       ![commandes vocales](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="sizing-recommendations"></a><span data-ttu-id="01635-201">Recommandations de dimensionnement</span><span class="sxs-lookup"><span data-stu-id="01635-201">Sizing recommendations</span></span> 

<span data-ttu-id="01635-202">Pour vous assurer que tous les objets interactifs peuvent facilement être manipulés, nous vous recommandons de vous assurer que l’interaction est conforme à une taille minimale en fonction de la distance qu’elle place à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="01635-202">To ensure all interactable objects can easily be touched, we recommend making sure the interactable meets a minimum size based on the distance it's placed from the user.</span></span> <span data-ttu-id="01635-203">L’angle visuel est souvent mesuré en degrés d’arc visuel. L’angle visuel est basé sur la distance entre les yeux de l’utilisateur et l’objet et reste constant, tandis que la taille physique de la cible peut changer en fonction de la distance entre les modifications de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="01635-203">The visual angle is often measured in degrees of visual arc. Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span></span> <span data-ttu-id="01635-204">Pour déterminer la taille physique nécessaire d’un objet en fonction de la distance de l’utilisateur, essayez d’utiliser une calculatrice d’angle visuel telle que celle- [ci](https://elvers.us/perception/visualAngle/).</span><span class="sxs-lookup"><span data-stu-id="01635-204">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](https://elvers.us/perception/visualAngle/).</span></span>

<span data-ttu-id="01635-205">Vous trouverez ci-dessous les recommandations relatives aux tailles minimales de contenu exploitable.</span><span class="sxs-lookup"><span data-stu-id="01635-205">Below are the recommendations for minimum sizes of interactable content.</span></span>


### <a name="target-size-for-direct-hand-interaction"></a><span data-ttu-id="01635-206">Taille cible pour l’interaction directe</span><span class="sxs-lookup"><span data-stu-id="01635-206">Target size for direct hand interaction</span></span>

| <span data-ttu-id="01635-207">Distance</span><span class="sxs-lookup"><span data-stu-id="01635-207">Distance</span></span> | <span data-ttu-id="01635-208">Angle d’affichage</span><span class="sxs-lookup"><span data-stu-id="01635-208">Viewing angle</span></span> | <span data-ttu-id="01635-209">Taille</span><span class="sxs-lookup"><span data-stu-id="01635-209">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="01635-210">45 cm</span><span class="sxs-lookup"><span data-stu-id="01635-210">45 cm</span></span>  | <span data-ttu-id="01635-211">non inférieur à 2 °</span><span class="sxs-lookup"><span data-stu-id="01635-211">no smaller than 2°</span></span> | <span data-ttu-id="01635-212">1,6 x 1,6 cm</span><span class="sxs-lookup"><span data-stu-id="01635-212">1.6 x 1.6 cm</span></span> |

<span data-ttu-id="01635-213">![Taille cible pour l’interaction directe](images/TargetSizingNear.jpg)</span><span class="sxs-lookup"><span data-stu-id="01635-213">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span></span><br>
<span data-ttu-id="01635-214">*Taille cible pour l’interaction directe*</span><span class="sxs-lookup"><span data-stu-id="01635-214">*Target size for direct hand interaction*</span></span>

<br>

### <a name="target-size-for-buttons"></a><span data-ttu-id="01635-215">Taille cible pour les boutons</span><span class="sxs-lookup"><span data-stu-id="01635-215">Target size for buttons</span></span>

<span data-ttu-id="01635-216">Lorsque vous créez des boutons pour une interaction directe, nous vous recommandons d’utiliser une taille minimale de 3,2 x 3,2 cm pour garantir qu’il y a suffisamment d’espace pour contenir une icône et éventuellement du texte.</span><span class="sxs-lookup"><span data-stu-id="01635-216">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there's enough space to contain an icon and potentially some text.</span></span>

| <span data-ttu-id="01635-217">Distance</span><span class="sxs-lookup"><span data-stu-id="01635-217">Distance</span></span> | <span data-ttu-id="01635-218">Taille minimale</span><span class="sxs-lookup"><span data-stu-id="01635-218">Minimum size</span></span> |
|---------|---------|
| <span data-ttu-id="01635-219">45 cm</span><span class="sxs-lookup"><span data-stu-id="01635-219">45 cm</span></span>  | <span data-ttu-id="01635-220">3,2 x 3,2 cm</span><span class="sxs-lookup"><span data-stu-id="01635-220">3.2 x 3.2 cm</span></span> |

<span data-ttu-id="01635-221">![Taille cible pour les boutons](images/TargetSizingButtons.png)</span><span class="sxs-lookup"><span data-stu-id="01635-221">![Target size for the buttons](images/TargetSizingButtons.png)</span></span><br>
<span data-ttu-id="01635-222">*Taille cible pour les boutons*</span><span class="sxs-lookup"><span data-stu-id="01635-222">*Target size for the buttons*</span></span>

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a><span data-ttu-id="01635-223">Taille cible pour un rayon de la main ou une interaction du regard</span><span class="sxs-lookup"><span data-stu-id="01635-223">Target size for hand ray or gaze interaction</span></span>
| <span data-ttu-id="01635-224">Distance</span><span class="sxs-lookup"><span data-stu-id="01635-224">Distance</span></span> | <span data-ttu-id="01635-225">Angle d’affichage</span><span class="sxs-lookup"><span data-stu-id="01635-225">Viewing angle</span></span> | <span data-ttu-id="01635-226">Taille</span><span class="sxs-lookup"><span data-stu-id="01635-226">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="01635-227">2 m</span><span class="sxs-lookup"><span data-stu-id="01635-227">2 m</span></span>  | <span data-ttu-id="01635-228">inférieur à 1 °</span><span class="sxs-lookup"><span data-stu-id="01635-228">no smaller than 1°</span></span> | <span data-ttu-id="01635-229">3,5 x 3,5 cm</span><span class="sxs-lookup"><span data-stu-id="01635-229">3.5 x 3.5 cm</span></span> |

<span data-ttu-id="01635-230">![Taille cible pour un rayon de la main ou une interaction du regard](images/TargetSizingFar.jpg)</span><span class="sxs-lookup"><span data-stu-id="01635-230">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span></span><br>
<span data-ttu-id="01635-231">*Taille cible pour un rayon de la main ou une interaction du regard*</span><span class="sxs-lookup"><span data-stu-id="01635-231">*Target size for hand ray or gaze interaction*</span></span>


<br>

---


## <a name="interactable-object-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="01635-232">Objet interactif dans MRTK (ensemble d’outils de réalité mixte) pour Unity</span><span class="sxs-lookup"><span data-stu-id="01635-232">Interactable object in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="01635-233">Dans **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, vous pouvez utiliser le script en [**interaction**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) pour faire en sorte que les objets répondent à différents types d’États d’interaction d’entrée.</span><span class="sxs-lookup"><span data-stu-id="01635-233">In **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can use the script [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) to make objects respond to various types of input interaction states.</span></span> <span data-ttu-id="01635-234">Il prend en charge différents types de thèmes qui vous permettent de définir des États visuels en contrôlant des propriétés d’objet telles que la couleur, la taille, le matériau et le nuanceur.</span><span class="sxs-lookup"><span data-stu-id="01635-234">It supports various types of themes that allow you define visual states by controlling object properties such as color, size, material, and shader.</span></span>

* [<span data-ttu-id="01635-235">Sur</span><span class="sxs-lookup"><span data-stu-id="01635-235">Interactable</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [<span data-ttu-id="01635-236">Button</span><span class="sxs-lookup"><span data-stu-id="01635-236">Button</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [<span data-ttu-id="01635-237">Scène d’exemples d’interaction manuelle</span><span class="sxs-lookup"><span data-stu-id="01635-237">Hand interaction examples scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

<span data-ttu-id="01635-238">Le nuanceur standard de MixedRealityToolkit fournit diverses options telles que la **lumière de proximité** qui vous aide à créer des signaux visuels et audio.</span><span class="sxs-lookup"><span data-stu-id="01635-238">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>
* [<span data-ttu-id="01635-239">Nuanceur standard MRTK</span><span class="sxs-lookup"><span data-stu-id="01635-239">MRTK Standard Shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


<br>

---


## <a name="see-also"></a><span data-ttu-id="01635-240">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01635-240">See also</span></span>

* [<span data-ttu-id="01635-241">Curseurs</span><span class="sxs-lookup"><span data-stu-id="01635-241">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="01635-242">Rayon émanant de la main</span><span class="sxs-lookup"><span data-stu-id="01635-242">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="01635-243">Button</span><span class="sxs-lookup"><span data-stu-id="01635-243">Button</span></span>](button.md)
* [<span data-ttu-id="01635-244">Objet avec interaction possible</span><span class="sxs-lookup"><span data-stu-id="01635-244">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="01635-245">Rectangle englobant et barre de l’application</span><span class="sxs-lookup"><span data-stu-id="01635-245">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="01635-246">Manipulation</span><span class="sxs-lookup"><span data-stu-id="01635-246">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="01635-247">Menu de la main</span><span class="sxs-lookup"><span data-stu-id="01635-247">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="01635-248">Menu proche</span><span class="sxs-lookup"><span data-stu-id="01635-248">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="01635-249">Collection d’objets</span><span class="sxs-lookup"><span data-stu-id="01635-249">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="01635-250">Commande vocale</span><span class="sxs-lookup"><span data-stu-id="01635-250">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="01635-251">Clavier</span><span class="sxs-lookup"><span data-stu-id="01635-251">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="01635-252">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="01635-252">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="01635-253">Tablette</span><span class="sxs-lookup"><span data-stu-id="01635-253">Slate</span></span>](slate.md)
* [<span data-ttu-id="01635-254">Curseur</span><span class="sxs-lookup"><span data-stu-id="01635-254">Slider</span></span>](slider.md)
* [<span data-ttu-id="01635-255">Nuanceur</span><span class="sxs-lookup"><span data-stu-id="01635-255">Shader</span></span>](shader.md)
* [<span data-ttu-id="01635-256">Billboarding et tag-along</span><span class="sxs-lookup"><span data-stu-id="01635-256">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="01635-257">Affichage de la progression</span><span class="sxs-lookup"><span data-stu-id="01635-257">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="01635-258">Aimantation de surface</span><span class="sxs-lookup"><span data-stu-id="01635-258">Surface magnetism</span></span>](surface-magnetism.md)
