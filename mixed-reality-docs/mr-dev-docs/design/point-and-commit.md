---
title: Pointer et valider avec les mains
description: Vue d’ensemble du modèle d’entrée Pointer et valider
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Réalité mixte, interaction, conception, HoloLens, mains, loin, pointer et valider, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, HoloLens, rayons émanant de la main, manipulation d’objets, MRTK, Mixed Reality Toolkit, DoF
ms.openlocfilehash: 13b692dada134f856ac6eed446cca45702030f67
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848288"
---
# <a name="point-and-commit-with-hands"></a><span data-ttu-id="b974b-104">Pointer et valider avec les mains</span><span class="sxs-lookup"><span data-stu-id="b974b-104">Point and commit with hands</span></span>

![Curseurs](images/UX_Hero_HandRay.jpg)

<span data-ttu-id="b974b-106">Le modèle d’entrée Pointer et valider avec les mains permet aux utilisateurs de cibler, sélectionner et manipuler du contenu 2D et 3D hors de portée.</span><span class="sxs-lookup"><span data-stu-id="b974b-106">Point and commit with hands is an input model that lets users target, select, and manipulate out of reach 2D and 3D content.</span></span> <span data-ttu-id="b974b-107">Cette technique d’interaction « éloignée » est propre à la réalité mixte car les humains n’interagissent pas naturellement de cette manière avec le monde réel.</span><span class="sxs-lookup"><span data-stu-id="b974b-107">This "far" interaction technique is unique to mixed reality because humans don't naturally interact with the real world that way.</span></span> <span data-ttu-id="b974b-108">Par exemple, dans le film de super-héros *X-Men*, le personnage [Magnéto](https://en.wikipedia.org/wiki/Magneto_(comics)) peut manipuler des objets éloignés avec les mains.</span><span class="sxs-lookup"><span data-stu-id="b974b-108">For example, in the super hero movie, *X-Men*, the character [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) can manipulate far objects in the distance with his hands.</span></span> <span data-ttu-id="b974b-109">Ce n’est pas quelque chose que les humains peuvent faire dans la réalité.</span><span class="sxs-lookup"><span data-stu-id="b974b-109">This isn't something humans can do in reality.</span></span> <span data-ttu-id="b974b-110">Dans HoloLens (réalité augmentée) et dans la réalité mixte, nous dotons les utilisateurs de ce pouvoir magique, éliminant ainsi les contraintes physiques du monde réel.</span><span class="sxs-lookup"><span data-stu-id="b974b-110">In both HoloLens (AR) and Mixed Reality (MR), we equip users with this magical power to break the physical constraint of the real world.</span></span> <span data-ttu-id="b974b-111">Cette expérience amusante avec le contenu holographique rend, en outre, les interactions des utilisateurs plus efficaces.</span><span class="sxs-lookup"><span data-stu-id="b974b-111">Not only is it a fun holographic experience, but it also makes user interactions more effective and efficient.</span></span>

## <a name="device-support"></a><span data-ttu-id="b974b-112">Prise en charge des appareils</span><span class="sxs-lookup"><span data-stu-id="b974b-112">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="b974b-113"><strong>Modèle d’entrée</strong></span><span class="sxs-lookup"><span data-stu-id="b974b-113"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="b974b-114"><a href="../hololens-hardware-details.md"><strong>HoloLens (1ère génération)</strong></a></span><span class="sxs-lookup"><span data-stu-id="b974b-114"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="b974b-115"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="b974b-115"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="b974b-116"><a href="../discover/immersive-headset-hardware-details.md"><strong>Casques immersifs</strong></a></span><span class="sxs-lookup"><span data-stu-id="b974b-116"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="b974b-117">Pointer et valider avec les mains</span><span class="sxs-lookup"><span data-stu-id="b974b-117">Point and commit with hands</span></span></td>
     <td><span data-ttu-id="b974b-118">❌ Non pris en charge</span><span class="sxs-lookup"><span data-stu-id="b974b-118">❌ Not supported</span></span></td>
     <td><span data-ttu-id="b974b-119">✔️ Recommandé</span><span class="sxs-lookup"><span data-stu-id="b974b-119">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="b974b-120">✔️ Recommandé</span><span class="sxs-lookup"><span data-stu-id="b974b-120">✔️ Recommended</span></span></td>
</tr>
</table>


<span data-ttu-id="b974b-121">Le modèle d’entrée _« Pointer et valider »_ est l’une des fonctionnalités récemment introduites qui exploitent le nouveau système de suivi des mains articulées.</span><span class="sxs-lookup"><span data-stu-id="b974b-121">_"Point and commit with hands"_ is one of the new features that use the new articulated hand-tracking system.</span></span> <span data-ttu-id="b974b-122">Il constitue également le principal modèle d’entrée sur les casques immersifs à l’aide de contrôleurs de mouvement.</span><span class="sxs-lookup"><span data-stu-id="b974b-122">This input model is also the primary input model on immersive headsets by using motion controllers.</span></span>

<br>

---

## <a name="hand-rays"></a><span data-ttu-id="b974b-123">Rayon émanant de la main</span><span class="sxs-lookup"><span data-stu-id="b974b-123">Hand rays</span></span>

<span data-ttu-id="b974b-124">Sur HoloLens 2, nous avons créé un rayon qui sort du centre de la paume de la main de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b974b-124">On HoloLens 2, we created a hand ray that shoots out from the center of the user's palm.</span></span> <span data-ttu-id="b974b-125">Ce rayon est traité comme une extension de la main.</span><span class="sxs-lookup"><span data-stu-id="b974b-125">This ray is treated as an extension of the hand.</span></span> <span data-ttu-id="b974b-126">Un curseur en forme d’anneau apparaît à l’extrémité du rayon pour indiquer à quel emplacement le rayon croise un objet cible.</span><span class="sxs-lookup"><span data-stu-id="b974b-126">A donut-shaped cursor is attached to the end of the ray to indicate the location where the ray intersects with a target object.</span></span> <span data-ttu-id="b974b-127">L’objet sur lequel le curseur atterrit peut alors recevoir des commandes gestuelles de la main.</span><span class="sxs-lookup"><span data-stu-id="b974b-127">The object that the cursor lands on can then receive gestural commands from the hand.</span></span>

<span data-ttu-id="b974b-128">Les commandes gestuelles de base sont déclenchées par un clic dans l’air, effectué avec le pouce et l’index.</span><span class="sxs-lookup"><span data-stu-id="b974b-128">This basic gestural command is triggered by using the thumb and index finger to do the air-tap action.</span></span> <span data-ttu-id="b974b-129">En utilisant le rayon émanant de la main pour pointer et un clic dans l’air pour valider, les utilisateurs peuvent activer un bouton ou un lien hypertexte.</span><span class="sxs-lookup"><span data-stu-id="b974b-129">By using the hand ray to point and air tap to commit, users can activate a button or a hyperlink.</span></span> <span data-ttu-id="b974b-130">Des mouvements plus composites permettent aux utilisateurs de naviguer dans le contenu web et de manipuler des objets 3D à distance.</span><span class="sxs-lookup"><span data-stu-id="b974b-130">With more composite gestures, users can navigating web content and manipulating 3D objects from a distance.</span></span> <span data-ttu-id="b974b-131">La conception visuelle du rayon doit également réagir aux états de pointage et de validation décrits et illustrés ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="b974b-131">The visual design of the hand ray should also react to these point and commit states, as described and shown below:</span></span> 

:::row:::
    :::column:::
        <span data-ttu-id="b974b-132">![rayons émanant de la main en pointage](images/hand-rays-pointing.jpg)</span><span class="sxs-lookup"><span data-stu-id="b974b-132">![hand rays pointing](images/hand-rays-pointing.jpg)</span></span><br>
        <span data-ttu-id="b974b-133">**État de pointage**</span><span class="sxs-lookup"><span data-stu-id="b974b-133">**Pointing state**</span></span><br>
        <span data-ttu-id="b974b-134">Dans l’état de *pointage*, le rayon est une ligne en pointillés et le curseur un anneau.</span><span class="sxs-lookup"><span data-stu-id="b974b-134">In the *pointing* state, the ray is a dash line and the cursor is a donut shape.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b974b-135">![rayons émanant de la main en validation](images/hand-rays-commit.jpg)</span><span class="sxs-lookup"><span data-stu-id="b974b-135">![hand rays commit](images/hand-rays-commit.jpg)</span></span><br>
        <span data-ttu-id="b974b-136">**État de validation**</span><span class="sxs-lookup"><span data-stu-id="b974b-136">**Commit state**</span></span><br>
        <span data-ttu-id="b974b-137">Dans l’état de *validation*, le rayon se transforme en ligne continue et le curseur est réduit à un point.</span><span class="sxs-lookup"><span data-stu-id="b974b-137">In the *commit* state, the ray turns into a solid line and the cursor shrinks to a dot.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="transition-between-near-and-far"></a><span data-ttu-id="b974b-138">Transition entre le contenu proche et éloigné</span><span class="sxs-lookup"><span data-stu-id="b974b-138">Transition between near and far</span></span>

<span data-ttu-id="b974b-139">Au lieu d’utiliser des mouvements spécifiques comme « pointer avec l’index » pour diriger le rayon, nous avons conçu celui-ci pour sortir du centre de la paume de la main.</span><span class="sxs-lookup"><span data-stu-id="b974b-139">Instead of using specific gestures like "pointing with index finger" to direct the ray, we designed the ray to comout out from the center of the users' palm.</span></span> <span data-ttu-id="b974b-140">Nous libérons ainsi les cinq doigts qui peuvent être utilisés pour effectuer d’autres mouvements, comme pincer et saisir.</span><span class="sxs-lookup"><span data-stu-id="b974b-140">This way, we've released and reserved the Five Fingers for more manipulative gestures like pinch and grab.</span></span> <span data-ttu-id="b974b-141">Cette conception nous permet de créer un seul modèle mental. Le même ensemble de mouvements de la main est utilisé pour les interactions avec du contenu proche ou éloigné.</span><span class="sxs-lookup"><span data-stu-id="b974b-141">With this design, we create only one mental model - the same set of hand gestures are used for both near and far interaction.</span></span> <span data-ttu-id="b974b-142">Vous pouvez utiliser le même mouvement de saisie pour manipuler des objets à différentes distances.</span><span class="sxs-lookup"><span data-stu-id="b974b-142">You can use the same grab gesture to manipulate objects at different distances.</span></span> <span data-ttu-id="b974b-143">L’appel des rayons est automatique et basé sur la proximité comme suit :</span><span class="sxs-lookup"><span data-stu-id="b974b-143">The invocation of the rays is automatic and proximity-based as follows:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="b974b-144">![Manipulation proche](images/transition-near-manipulation.jpg)</span><span class="sxs-lookup"><span data-stu-id="b974b-144">![Near manipulation](images/transition-near-manipulation.jpg)</span></span><br>
        <span data-ttu-id="b974b-145">**Manipulation proche**</span><span class="sxs-lookup"><span data-stu-id="b974b-145">**Near manipulation**</span></span><br>
        <span data-ttu-id="b974b-146">Quand un objet est à portée de main (environ 50 cm), les rayons sont automatiquement désactivés pour encourager l’interaction proche.</span><span class="sxs-lookup"><span data-stu-id="b974b-146">When an object is within arm's length (roughly 50 cm), the rays are turned off automatically, encouraging near interaction.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b974b-147">![Manipulation éloignée](images/transition-far-manipulation.jpg)</span><span class="sxs-lookup"><span data-stu-id="b974b-147">![Far manipulation](images/transition-far-manipulation.jpg)</span></span><br>
        <span data-ttu-id="b974b-148">**Manipulation éloignée**</span><span class="sxs-lookup"><span data-stu-id="b974b-148">**Far manipulation**</span></span><br>
        <span data-ttu-id="b974b-149">Si l’objet se trouve à plus de 50 cm, les rayons sont activés.</span><span class="sxs-lookup"><span data-stu-id="b974b-149">When the object is farther than 50 cm, the rays are turned on.</span></span> <span data-ttu-id="b974b-150">La transition doit être fluide et transparente.</span><span class="sxs-lookup"><span data-stu-id="b974b-150">The transition should be smooth and seamless.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="b974b-151">Interaction avec une ardoise 2D</span><span class="sxs-lookup"><span data-stu-id="b974b-151">2D slate interaction</span></span>

<span data-ttu-id="b974b-152">Une tablette 2D est un conteneur holographique hébergeant le contenu d’applications 2D comme un navigateur web.</span><span class="sxs-lookup"><span data-stu-id="b974b-152">A 2D slate is a holographic container hosting 2D app contents, such as a web browser.</span></span> <span data-ttu-id="b974b-153">Le concept de l’interaction éloignée avec une ardoise 2D est le suivant : les utilisateurs se servent du rayon émanant de la main pour cibler un objet et effectuent un clic dans l’air pour le sélectionner.</span><span class="sxs-lookup"><span data-stu-id="b974b-153">The design concept for far interacting with a 2D slate is to use hand rays to target and air tap to select.</span></span> <span data-ttu-id="b974b-154">Après avoir ciblé un élément à l’aide du rayon, ils peuvent cliquer dans l’air pour déclencher un lien hypertexte ou un bouton.</span><span class="sxs-lookup"><span data-stu-id="b974b-154">After targeting with a hand ray, users can air tap to trigger a hyperlink or a button.</span></span> <span data-ttu-id="b974b-155">D’une main, ils peuvent « cliquer dans l’air et faire glisser » pour faire défiler le contenu de la tablette vers le haut et vers le bas.</span><span class="sxs-lookup"><span data-stu-id="b974b-155">They can use one hand to "air tap and drag" to scroll slate content up and down.</span></span> <span data-ttu-id="b974b-156">Le mouvement relatif des deux mains pour cliquer dans l’air et faire glisser permet de faire un zoom avant ou arrière sur le contenu de l’ardoise.</span><span class="sxs-lookup"><span data-stu-id="b974b-156">The relative motion of using two hands to air tap and drag can zoom in and out the slate content.</span></span>

<span data-ttu-id="b974b-157">Le fait de cibler le rayon émanant de la main au niveau des coins et des bords permet de révéler l’affordance de manipulation la plus proche.</span><span class="sxs-lookup"><span data-stu-id="b974b-157">Targeting the hand ray at the corners and edges reveals the closest manipulation affordance.</span></span> <span data-ttu-id="b974b-158">En « saisissant et en faisant glisser » des affordances de manipulation, les utilisateurs peuvent effectuer une montée en charge uniforme (affordances de coin) et ajuster dynamiquement la tablette (affordances de bord).</span><span class="sxs-lookup"><span data-stu-id="b974b-158">By "grab and drag" manipulation affordances, users can do uniform scaling through the corner affordances, and can reflow the slate via the edge affordances.</span></span> <span data-ttu-id="b974b-159">Saisir la barre holographique située en haut de la tablette 2D et la faire glisser permet aux utilisateurs de déplacer toute la tablette.</span><span class="sxs-lookup"><span data-stu-id="b974b-159">Grabbing and dragging the holobar at the top of the 2D slate lets users move the entire slate.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="b974b-160">![Clic d’interaction avec une tablette 2D](images/2d-slate-interaction-click.jpg)</span><span class="sxs-lookup"><span data-stu-id="b974b-160">![2d slate interaction click](images/2d-slate-interaction-click.jpg)</span></span><br>
       <span data-ttu-id="b974b-161">**Clic**</span><span class="sxs-lookup"><span data-stu-id="b974b-161">**Click**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="b974b-162">![Défilement d’interaction avec une tablette 2D](images/2d-slate-interaction-scroll.jpg)</span><span class="sxs-lookup"><span data-stu-id="b974b-162">![2d slate interaction scroll](images/2d-slate-interaction-scroll.jpg)</span></span><br>
        <span data-ttu-id="b974b-163">**Faire défiler**</span><span class="sxs-lookup"><span data-stu-id="b974b-163">**Scroll**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="b974b-164">![Zoom d’interaction avec une tablette 2D](images/2d-slate-interaction-zoom.jpg)</span><span class="sxs-lookup"><span data-stu-id="b974b-164">![2d slate interaction zoom](images/2d-slate-interaction-zoom.jpg)</span></span><br>
       <span data-ttu-id="b974b-165">**Zoom**</span><span class="sxs-lookup"><span data-stu-id="b974b-165">**Zoom**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="b974b-166">**Pour manipuler la tablette 2D**</span><span class="sxs-lookup"><span data-stu-id="b974b-166">**For manipulating the 2D slate**</span></span><br>

* <span data-ttu-id="b974b-167">Les utilisateurs pointent le rayon émanant de la main au niveau des coins ou des bords pour révéler l’affordance de manipulation la plus proche.</span><span class="sxs-lookup"><span data-stu-id="b974b-167">Users point the hand ray at the corners or edges to reveal the closest manipulation affordance.</span></span> 
* <span data-ttu-id="b974b-168">En appliquant un mouvement de manipulation sur l’affordance, les utilisateurs peuvent effectuer une montée en charge uniforme (affordance de coin) et ajuster dynamiquement l’ardoise (affordance de bord).</span><span class="sxs-lookup"><span data-stu-id="b974b-168">By applying a manipulation gesture on the affordance, users can do uniform scaling through the corner affordance, and can reflow the slate via the edge affordance.</span></span> 
* <span data-ttu-id="b974b-169">En appliquant un mouvement de manipulation sur la barre holographique située en haut de la tablette 2D, les utilisateurs peuvent déplacer la tablette entière.</span><span class="sxs-lookup"><span data-stu-id="b974b-169">By applying a manipulation gesture on the holobar at the top of the 2D slate, users can move the entire slate.</span></span><br>

<br>

---

## <a name="3d-object-manipulation"></a><span data-ttu-id="b974b-170">Manipulation d’objets 3D</span><span class="sxs-lookup"><span data-stu-id="b974b-170">3D object manipulation</span></span>

<span data-ttu-id="b974b-171">En manipulation directe, les utilisateurs ont le choix entre deux méthodes pour manipuler des objets 3D : la manipulation basée sur l’affordance et la manipulation non basée sur l’affordance.</span><span class="sxs-lookup"><span data-stu-id="b974b-171">In direct manipulation, there are two ways for users to manipulate 3D objects: affordance-based manipulation and non-affordance based manipulation.</span></span> <span data-ttu-id="b974b-172">Dans le modèle Pointer et valider, les utilisateurs peuvent accomplir exactement les mêmes tâches à l’aide du rayon émanant de la main.</span><span class="sxs-lookup"><span data-stu-id="b974b-172">In the point and commit model, users can achieve exactly the same tasks through the hand rays.</span></span> <span data-ttu-id="b974b-173">Aucune formation supplémentaire n’est requise.</span><span class="sxs-lookup"><span data-stu-id="b974b-173">No extra learning is needed.</span></span><br>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="b974b-174">Manipulation basée sur l’affordance</span><span class="sxs-lookup"><span data-stu-id="b974b-174">Affordance-based manipulation</span></span>

<span data-ttu-id="b974b-175">Les utilisateurs utilisent le rayon émanant de la main pour pointer sur un objet et faire apparaître le cadre englobant et les affordances de manipulation.</span><span class="sxs-lookup"><span data-stu-id="b974b-175">Users use hand rays to point and reveal the bounding box and manipulation affordances.</span></span> <span data-ttu-id="b974b-176">Les utilisateurs peuvent appliquer le mouvement de manipulation sur le cadre englobant pour déplacer l’objet entier, sur les affordances de bord pour faire pivoter l’objet et sur les affordances de coin pour effectuer une mise à l’échelle uniforme.</span><span class="sxs-lookup"><span data-stu-id="b974b-176">Users can apply the manipulation gesture on the bounding box to move the whole object, on the edge affordances to rotate, and on the corner affordances to scale uniformly.</span></span> <br>

:::row:::
    :::column:::
       <span data-ttu-id="b974b-177">![Déplacement éloigné lors d’une manipulation d’objet 3D](images/3d-object-manipulation-far-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="b974b-177">![3d object manipulation far move](images/3d-object-manipulation-far-move.jpg)</span></span><br>
       <span data-ttu-id="b974b-178">**Déplacer**</span><span class="sxs-lookup"><span data-stu-id="b974b-178">**Move**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="b974b-179">![Rotation éloignée lors d’une manipulation d’objet 3D](images/3d-object-manipulation-far-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="b974b-179">![3d object manipulation far rotate](images/3d-object-manipulation-far-rotate.jpg)</span></span><br>
        <span data-ttu-id="b974b-180">**Faire pivoter**</span><span class="sxs-lookup"><span data-stu-id="b974b-180">**Rotate**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="b974b-181">![Mise à l’échelle éloignée lors d’une manipulation d’objet 3D](images/3d-object-manipulation-far-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="b974b-181">![3d object manipulation far scale](images/3d-object-manipulation-far-scale.jpg)</span></span><br>
       <span data-ttu-id="b974b-182">**Mettre à l’échelle**</span><span class="sxs-lookup"><span data-stu-id="b974b-182">**Scale**</span></span><br>
    :::column-end:::
:::row-end:::

### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="b974b-183">Manipulation non basée sur l’affordance</span><span class="sxs-lookup"><span data-stu-id="b974b-183">Non-affordance-based manipulation</span></span>

<span data-ttu-id="b974b-184">Les utilisateurs pointent sur un objet à l’aide du rayon émanant de la main pour faire apparaître le cadre englobant, puis appliquent directement des mouvements de manipulation à cet objet.</span><span class="sxs-lookup"><span data-stu-id="b974b-184">Users point with hand rays to reveal the bounding box then directly apply manipulation gestures on it.</span></span> <span data-ttu-id="b974b-185">Avec une main, la translation et la rotation de l’objet sont associées au mouvement et à l’orientation de la main.</span><span class="sxs-lookup"><span data-stu-id="b974b-185">With one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="b974b-186">Avec les deux mains, les utilisateurs peuvent translater, mettre à l’échelle et faire pivoter l’objet selon les mouvements relatifs des deux mains.</span><span class="sxs-lookup"><span data-stu-id="b974b-186">With two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span><br>

<br>

---

## <a name="instinctual-gestures"></a><span data-ttu-id="b974b-187">Mouvements instinctifs</span><span class="sxs-lookup"><span data-stu-id="b974b-187">Instinctual gestures</span></span>

<span data-ttu-id="b974b-188">Le concept de mouvements instinctifs pour pointer et valider est similaire à celui de la [manipulation directe avec les mains](direct-manipulation.md).</span><span class="sxs-lookup"><span data-stu-id="b974b-188">The concept of instinctual gestures for point and commit is similar to that for [direct manipulation with hands](direct-manipulation.md).</span></span> <span data-ttu-id="b974b-189">Les mouvements que les utilisateurs effectuent sur un objet 3D sont guidés par la conception des affordances de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b974b-189">The gestures users do on a 3D object are guided by the design of UI affordances.</span></span> <span data-ttu-id="b974b-190">Par exemple, un petit point de contrôle peut inciter les utilisateurs à le pincer avec le pouce et l’index, tandis qu’un utilisateur peut souhaiter utiliser ses cinq doigts pour saisir un objet plus volumineux.</span><span class="sxs-lookup"><span data-stu-id="b974b-190">For example, a small control point might motivate users to pinch with their thumb and index finger, while a user might want to use all Five Fingers to grab a larger object.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="b974b-191">![Mouvements instinctifs sur objet éloigné de petite taille](images/instinctual-gestures-far-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="b974b-191">![instinctual gestures far small object](images/instinctual-gestures-far-smallobject.jpg)</span></span><br>
       <span data-ttu-id="b974b-192">**Petit objet**</span><span class="sxs-lookup"><span data-stu-id="b974b-192">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="b974b-193">![Mouvements instinctifs sur objet éloigné de taille moyenne](images/instinctual-gestures-far-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="b974b-193">![instinctual gestures far medium object](images/instinctual-gestures-far-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="b974b-194">**Objet de taille moyenne**</span><span class="sxs-lookup"><span data-stu-id="b974b-194">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="b974b-195">![Mouvements instinctifs sur objet éloigné volumineux](images/instinctual-gestures-far-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="b974b-195">![instinctual gestures far large object](images/instinctual-gestures-far-largeobject.jpg)</span></span><br>
       <span data-ttu-id="b974b-196">**Objet volumineux**</span><span class="sxs-lookup"><span data-stu-id="b974b-196">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a><span data-ttu-id="b974b-197">Conception symétrique entre les mains et le contrôleur 6DoF</span><span class="sxs-lookup"><span data-stu-id="b974b-197">Symmetric design between hands and 6 DoF controller</span></span> 

<span data-ttu-id="b974b-198">Le concept Pointer et valider pour l’interaction éloignée a été initialement créé et défini pour le portail de réalité mixte (MRP).</span><span class="sxs-lookup"><span data-stu-id="b974b-198">The concept of point and commit for far interaction was created and defined for the Mixed Reality Portal (MRP).</span></span> <span data-ttu-id="b974b-199">Dans ce scénario, un utilisateur porte un casque immersif et interagit avec des objets 3D à l’aide de contrôleurs de mouvement.</span><span class="sxs-lookup"><span data-stu-id="b974b-199">In this scenario, a user wears an immersive headset and interacts with 3D objects via motion controllers.</span></span> <span data-ttu-id="b974b-200">Les contrôleurs de mouvement émettent des rayons pour pointer et manipuler des objets éloignés.</span><span class="sxs-lookup"><span data-stu-id="b974b-200">The motion controllers shoot out rays for pointing and manipulating far objects.</span></span> <span data-ttu-id="b974b-201">Les contrôleurs sont équipés de boutons pour valider différentes actions.</span><span class="sxs-lookup"><span data-stu-id="b974b-201">There are buttons on the controllers for further committing different actions.</span></span> <span data-ttu-id="b974b-202">Nous appliquons le modèle d’interaction des rayons et les fixons aux deux mains.</span><span class="sxs-lookup"><span data-stu-id="b974b-202">We apply the interaction model of rays and attached them to both hands.</span></span> <span data-ttu-id="b974b-203">Grâce à cette conception symétrique, les utilisateurs qui sont familiarisés avec MRP ne sont pas contraints d’apprendre un autre modèle d’interaction pour pointer sur un objet éloigné et le manipuler quand ils utilisent HoloLens 2, et inversement.</span><span class="sxs-lookup"><span data-stu-id="b974b-203">With this symmetric design, users who are familiar with MRP won't need to learn another interaction model for far pointing and manipulation when they use HoloLens 2, and the other way around.</span></span>    

:::row:::
    :::column:::
        <span data-ttu-id="b974b-204">![Conception symétrique pour les rayons avec des contrôleurs](images/symmetric-design-for-rays-controllers.jpg)</span><span class="sxs-lookup"><span data-stu-id="b974b-204">![symmetric design for rays with controllers](images/symmetric-design-for-rays-controllers.jpg)</span></span><br>
        <span data-ttu-id="b974b-205">**Rayons de contrôleur**</span><span class="sxs-lookup"><span data-stu-id="b974b-205">**Controller rays**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="b974b-206">![Conception symétrique pour les rayons avec les mains](images/symmetric-design-for-rays-hands.jpg)</span><span class="sxs-lookup"><span data-stu-id="b974b-206">![symmetric design for rays with hands](images/symmetric-design-for-rays-hands.jpg)</span></span><br>
        <span data-ttu-id="b974b-207">**Rayons émanant de la main**</span><span class="sxs-lookup"><span data-stu-id="b974b-207">**Hand rays**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-ray-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="b974b-208">Rayon émanant de la main dans MRTK (Mixed Reality Toolkit) pour Unity</span><span class="sxs-lookup"><span data-stu-id="b974b-208">Hand ray in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="b974b-209">Par défaut, MRTK fournit un préfabriqué de rayon émanant de la main ([DefaultControllerPointer.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Pointers)) qui a le même état visuel que le rayon système du shell.</span><span class="sxs-lookup"><span data-stu-id="b974b-209">By default, MRTK provides a hand ray prefab ([DefaultControllerPointer.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Pointers)) which has the same visual state as the shell's system hand ray.</span></span> <span data-ttu-id="b974b-210">Il est attribué dans le profil d’entrée de MRTK, sous Pointeurs.</span><span class="sxs-lookup"><span data-stu-id="b974b-210">It's assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="b974b-211">Dans le casque immersif, les mêmes rayons sont utilisés pour les contrôleurs de mouvement.</span><span class="sxs-lookup"><span data-stu-id="b974b-211">In an immersive headset, the same rays are used for the motion controllers.</span></span>

* [<span data-ttu-id="b974b-212">MRTK - Profil de pointeur</span><span class="sxs-lookup"><span data-stu-id="b974b-212">MRTK - Pointer profile</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html#pointer-configuration)
* [<span data-ttu-id="b974b-213">MRTK - Système d’entrée</span><span class="sxs-lookup"><span data-stu-id="b974b-213">MRTK - Input system</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)
* [<span data-ttu-id="b974b-214">MRTK - Pointeurs</span><span class="sxs-lookup"><span data-stu-id="b974b-214">MRTK - Pointers</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html)

---

## <a name="see-also"></a><span data-ttu-id="b974b-215">Voir également</span><span class="sxs-lookup"><span data-stu-id="b974b-215">See also</span></span>
* [<span data-ttu-id="b974b-216">Manipulation directe avec les mains</span><span class="sxs-lookup"><span data-stu-id="b974b-216">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="b974b-217">Pointer et valider</span><span class="sxs-lookup"><span data-stu-id="b974b-217">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="b974b-218">Mains : Manipulation directe</span><span class="sxs-lookup"><span data-stu-id="b974b-218">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="b974b-219">Mains : Mouvements</span><span class="sxs-lookup"><span data-stu-id="b974b-219">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="b974b-220">Interactions instinctuelles</span><span class="sxs-lookup"><span data-stu-id="b974b-220">Instinctual interactions</span></span>](interaction-fundamentals.md)
