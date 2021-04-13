---
title: Manipulation directe avec les mains
description: Apprenez-en davantage sur la manipulation directe, un modèle d’entrée dans lequel les utilisateurs touchent directement des hologrammes.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: Réalité mixte, regard, ciblage du regard, interaction, conception, mains de près, HoloLens, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, MRTK, Mixed Reality Toolkit, bouton, colliders, cadre englobant, 2D, gestes instinctifs
ms.openlocfilehash: 555b27764d077332a2d8618672e6aed7def1dd3f
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300094"
---
# <a name="direct-manipulation-with-hands"></a><span data-ttu-id="0f36d-104">Manipulation directe avec les mains</span><span class="sxs-lookup"><span data-stu-id="0f36d-104">Direct manipulation with hands</span></span>

![Bouton](images/UX_Hero_Manipulation.jpg)

<span data-ttu-id="0f36d-106">La manipulation directe est un modèle d’entrée qui consiste à toucher les hologrammes directement avec les mains.</span><span class="sxs-lookup"><span data-stu-id="0f36d-106">Direct manipulation is an input model that involves touching holograms directly with your hands.</span></span> <span data-ttu-id="0f36d-107">L’idée derrière ce concept est de faire en sorte que les objets se comportent exactement comme dans le monde réel.</span><span class="sxs-lookup"><span data-stu-id="0f36d-107">The idea behind this concept is that objects behave just as they would in the real world.</span></span> <span data-ttu-id="0f36d-108">Vous pouvez activer les boutons simplement en appuyant dessus, vous pouvez saisir les objets en les agrippant, et le contenu 2D se comporte comme un écran tactile virtuel.</span><span class="sxs-lookup"><span data-stu-id="0f36d-108">Buttons can be activated simply by pressing them, objects can be picked up by grabbing them, and 2D content behaves like a virtual touchscreen.</span></span> <span data-ttu-id="0f36d-109">La manipulation directe est basée sur l’affordance, ce qui la rend conviviale.</span><span class="sxs-lookup"><span data-stu-id="0f36d-109">Direct manipulation is affordance-based, meaning it's user-friendly.</span></span> <span data-ttu-id="0f36d-110">Les utilisateurs n’ont pas à apprendre de mouvements symboliques.</span><span class="sxs-lookup"><span data-stu-id="0f36d-110">There are no symbolic gestures to teach users.</span></span> <span data-ttu-id="0f36d-111">Toutes les interactions reposent sur un élément visuel que vous pouvez toucher ou saisir.</span><span class="sxs-lookup"><span data-stu-id="0f36d-111">All interactions are built around a visual element that you can touch or grab.</span></span> <span data-ttu-id="0f36d-112">Elle est considérée comme un modèle d’entrée « proche », car elle est utilisée de préférence pour interagir avec le contenu situé à portée de main.</span><span class="sxs-lookup"><span data-stu-id="0f36d-112">It's considered a "near" input model in that it's best used for interacting with content within arms reach.</span></span>

## <a name="device-support"></a><span data-ttu-id="0f36d-113">Prise en charge des appareils</span><span class="sxs-lookup"><span data-stu-id="0f36d-113">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="0f36d-114"><strong>Modèle d’entrée</strong></span><span class="sxs-lookup"><span data-stu-id="0f36d-114"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="0f36d-115"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1ère génération)</strong></a></span><span class="sxs-lookup"><span data-stu-id="0f36d-115"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="0f36d-116"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="0f36d-116"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span></span></td>
     <td><span data-ttu-id="0f36d-117"><a href="/windows/mixed-reality/immersive-headset-hardware-details"><strong>Casques immersifs</strong></a></span><span class="sxs-lookup"><span data-stu-id="0f36d-117"><a href="/windows/mixed-reality/immersive-headset-hardware-details"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="0f36d-118">Manipulation directe avec les mains</span><span class="sxs-lookup"><span data-stu-id="0f36d-118">Direct manipulation with hands</span></span></td>
     <td><span data-ttu-id="0f36d-119">❌ Non pris en charge</span><span class="sxs-lookup"><span data-stu-id="0f36d-119">❌ Not supported</span></span></td>
     <td><span data-ttu-id="0f36d-120">✔️ Recommandé</span><span class="sxs-lookup"><span data-stu-id="0f36d-120">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="0f36d-121">➕ Pris en charge.</span><span class="sxs-lookup"><span data-stu-id="0f36d-121">➕ Supported.</span></span>  <span data-ttu-id="0f36d-122">Pour l’IU, nous vous recommandons <a href="point-and-commit.md">de pointer et de valider avec les mains</a> à la place.</span><span class="sxs-lookup"><span data-stu-id="0f36d-122">For UI, we recommend <a href="point-and-commit.md">point and commit with hands</a> instead.</span></span></td>
    
</tr>
</table>


<span data-ttu-id="0f36d-123">La manipulation directe est l’un des principaux modèles d’entrée sur HoloLens 2. Elle utilise le nouveau système de suivi des mains articulé.</span><span class="sxs-lookup"><span data-stu-id="0f36d-123">Direct manipulation is a primary input model on HoloLens 2, which uses the new articulated hand-tracking system.</span></span> <span data-ttu-id="0f36d-124">Le modèle d’entrée est également disponible sur les casques immersifs par le biais de l’utilisation de contrôleurs de mouvement, mais il n’est pas recommandé en tant que mode principal d’interaction en dehors de la manipulation d’objets.</span><span class="sxs-lookup"><span data-stu-id="0f36d-124">The input model is also available on immersive headsets by using motion controllers, but isn't recommended as a primary means of interaction outside of object manipulation.</span></span> <span data-ttu-id="0f36d-125">La manipulation directe n’est pas disponible sur HoloLens (1re génération).</span><span class="sxs-lookup"><span data-stu-id="0f36d-125">Direct manipulation isn't available on HoloLens (1st gen).</span></span>

<br>

---

## <a name="collidable-fingertip"></a><span data-ttu-id="0f36d-126">Pointe de doigt avec détection de collision</span><span class="sxs-lookup"><span data-stu-id="0f36d-126">Collidable fingertip</span></span>

<span data-ttu-id="0f36d-127">Sur HoloLens 2, les mains de l’utilisateur sont reconnues et interprétées en tant que modèles du squelette des mains gauche et droite.</span><span class="sxs-lookup"><span data-stu-id="0f36d-127">On HoloLens 2, the user's hands are recognized and interpreted as left and right-hand skeletal models.</span></span> <span data-ttu-id="0f36d-128">Pour implémenter l’idée consistant à toucher les hologrammes directement avec les mains, l’idéal serait d’attacher cinq colliders (détecteurs de collision) aux cinq pointes de doigt de chaque modèle du squelette de la main.</span><span class="sxs-lookup"><span data-stu-id="0f36d-128">To implement the idea of touching holograms directly with hands, ideally, five colliders could be attached to the five fingertips of each hand skeletal model.</span></span> <span data-ttu-id="0f36d-129">Toutefois, en raison de l’absence de rétroaction tactile, 10 bouts de doigts avec détection de collision donnent lieu à des collisions inattendues et imprévisibles avec les hologrammes.</span><span class="sxs-lookup"><span data-stu-id="0f36d-129">However, because of the lack of tactile feedback, 10 collidable fingertips can cause unexpected and unpredictable collisions with holograms.</span></span> 

<span data-ttu-id="0f36d-130">Nous suggérons de placer uniquement un collider sur chaque index.</span><span class="sxs-lookup"><span data-stu-id="0f36d-130">We suggest only putting a collider on each index finger.</span></span> <span data-ttu-id="0f36d-131">Les pointes d’index avec détection de collision peuvent toujours servir de points tactiles actifs pour les divers mouvements tactiles impliquant d’autres doigts.</span><span class="sxs-lookup"><span data-stu-id="0f36d-131">The collidable index fingertips can still serve as active touch points for diverse touch gestures involving other fingers.</span></span> <span data-ttu-id="0f36d-132">Les mouvements tactiles incluent la pression à 1 doigt, le clic à 1 doigt, la pression à 2 doigts et la pression à 5 doigts, comme illustré ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="0f36d-132">Touch gestures include One-finger press, One-finger tap, Two-finger press, and Five-finger press, as shown below:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="0f36d-133">![Pointe de doigt avec détection de collision](images/Collidable-Fingertip.jpg)</span><span class="sxs-lookup"><span data-stu-id="0f36d-133">![collidable fingertip](images/Collidable-Fingertip.jpg)</span></span><br>
       <span data-ttu-id="0f36d-134">**Pointe de doigt avec détection de collision**</span><span class="sxs-lookup"><span data-stu-id="0f36d-134">**Collidable fingertip**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0f36d-135">![Appui avec un doigt](images/Collidable-Fingertip-1-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="0f36d-135">![One-finger press](images/Collidable-Fingertip-1-finger-press.jpg)</span></span><br>
        <span data-ttu-id="0f36d-136">**Appui avec un doigt**</span><span class="sxs-lookup"><span data-stu-id="0f36d-136">**One-finger press**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0f36d-137">![Clic à un doigt](images/Collidable-Fingertip-1-finger-tap.jpg)</span><span class="sxs-lookup"><span data-stu-id="0f36d-137">![One-finger tap](images/Collidable-Fingertip-1-finger-tap.jpg)</span></span><br>
       <span data-ttu-id="0f36d-138">**Clic à un doigt**</span><span class="sxs-lookup"><span data-stu-id="0f36d-138">**One-finger tap**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0f36d-139">![Appui avec cinq doigts](images/Collidable-Fingertip-5-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="0f36d-139">![Five-finger press](images/Collidable-Fingertip-5-finger-press.jpg)</span></span><br>
       <span data-ttu-id="0f36d-140">**Appui avec cinq doigts**</span><span class="sxs-lookup"><span data-stu-id="0f36d-140">**Five-finger press**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="sphere-collider"></a><span data-ttu-id="0f36d-141">Collider sphérique</span><span class="sxs-lookup"><span data-stu-id="0f36d-141">Sphere collider</span></span>

<span data-ttu-id="0f36d-142">Au lieu d’utiliser une forme générique aléatoire, nous vous suggérons d’utiliser un collider de sphère.</span><span class="sxs-lookup"><span data-stu-id="0f36d-142">Instead of using a random generic shape, we suggest you use a sphere collider.</span></span> <span data-ttu-id="0f36d-143">Ensuite, vous pouvez l’afficher visuellement pour fournir de meilleures indications de ciblage proche.</span><span class="sxs-lookup"><span data-stu-id="0f36d-143">Then you can visually render it to provide better cues for near targeting.</span></span> <span data-ttu-id="0f36d-144">Le diamètre de la sphère doit correspondre à l’épaisseur de l’index pour augmenter la précision tactile.</span><span class="sxs-lookup"><span data-stu-id="0f36d-144">The sphere's diameter should match the thickness of the index finger to increase touch accuracy.</span></span> <span data-ttu-id="0f36d-145">Il est plus facile de récupérer la variable de l’épaisseur du doigt en appelant l’API relative à la main.</span><span class="sxs-lookup"><span data-stu-id="0f36d-145">It's easier to retrieve the variable of finger thickness by calling the hand API.</span></span>

### <a name="fingertip-cursor"></a><span data-ttu-id="0f36d-146">Curseur à la pointe du doigt</span><span class="sxs-lookup"><span data-stu-id="0f36d-146">Fingertip cursor</span></span>

<span data-ttu-id="0f36d-147">En plus du rendu d’une sphère avec détection de collision à la pointe de l’index, nous avons créé un curseur à la pointe du doigt pour vivre une meilleure expérience de ciblage proche.</span><span class="sxs-lookup"><span data-stu-id="0f36d-147">In addition to rendering a collidable sphere on the index fingertip, we've created an advanced fingertip cursor to achieve a better near-targeting experience.</span></span> <span data-ttu-id="0f36d-148">Il s’agit d’un curseur en forme d’anneau attaché à la pointe de l’index.</span><span class="sxs-lookup"><span data-stu-id="0f36d-148">It's a donut-shaped cursor attached to the index fingertip.</span></span> <span data-ttu-id="0f36d-149">En fonction de la proximité, il réagit de manière dynamique à l’orientation et à la taille d’une cible, comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="0f36d-149">According to proximity, it dynamically reacts to a target for orientation and size as detailed below:</span></span>

* <span data-ttu-id="0f36d-150">Quand un index se déplace vers un hologramme, le curseur est toujours parallèle à la surface de l’hologramme et réduit progressivement sa taille.</span><span class="sxs-lookup"><span data-stu-id="0f36d-150">When an index finger moves toward a hologram, the cursor is always parallel to the hologram's surface and gradually shrinks its size.</span></span>
* <span data-ttu-id="0f36d-151">Dès que le doigt touche la surface, le curseur se réduit en un point et émet un événement tactile.</span><span class="sxs-lookup"><span data-stu-id="0f36d-151">As soon as the finger touches the surface, the cursor shrinks into a dot and emits a touch event.</span></span>

<span data-ttu-id="0f36d-152">Grâce à une rétroaction interactive, les utilisateurs disposent d’une haute précision pour les tâches de ciblage proche, par exemple le déclenchement d’un lien hypertexte ou la pression sur un bouton, comme illustré ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="0f36d-152">With interactive feedback, users can achieve high precision near-targeting tasks, such as triggering a hyperlink or pressing a button as shown below.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="0f36d-153">![Curseur à la pointe du doigt éloigné](images/Fingertip-cursor-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="0f36d-153">![Fingertip cursor far](images/Fingertip-cursor-far.jpg)</span></span><br>
       <span data-ttu-id="0f36d-154">**Curseur à la pointe du doigt éloigné**</span><span class="sxs-lookup"><span data-stu-id="0f36d-154">**Fingertip cursor far**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0f36d-155">![Curseur à la pointe du doigt proche](images/Fingertip-cursor-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="0f36d-155">![Fingertip cursor near](images/Fingertip-cursor-near.jpg)</span></span><br>
        <span data-ttu-id="0f36d-156">**Curseur à la pointe du doigt proche**</span><span class="sxs-lookup"><span data-stu-id="0f36d-156">**Fingertip cursor near**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0f36d-157">![Curseur à la pointe du doigt en contact](images/Fingertip-cursor-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="0f36d-157">![Fingertip cursor contact](images/Fingertip-cursor-contact.jpg)</span></span><br>
       <span data-ttu-id="0f36d-158">**Curseur à la pointe du doigt en contact**</span><span class="sxs-lookup"><span data-stu-id="0f36d-158">**Fingertip cursor contact**</span></span><br>
    :::column-end:::
:::row-end:::

<br>



## <a name="bounding-box-with-proximity-shader"></a><span data-ttu-id="0f36d-159">Rectangle englobant avec nuanceur de proximité</span><span class="sxs-lookup"><span data-stu-id="0f36d-159">Bounding box with proximity shader</span></span>

<span data-ttu-id="0f36d-160">L’hologramme lui-même doit également pouvoir fournir une rétroaction visuelle et audio pour compenser le manque de rétroaction tactile.</span><span class="sxs-lookup"><span data-stu-id="0f36d-160">The hologram itself also requires the ability to provide both visual and audio feedback to compensate the lack of tactile feedback.</span></span> <span data-ttu-id="0f36d-161">Pour cela, nous générons le concept de rectangle englobant avec un nuanceur de proximité.</span><span class="sxs-lookup"><span data-stu-id="0f36d-161">For that, we generate the concept of a bounding box with a proximity shader.</span></span> <span data-ttu-id="0f36d-162">Un rectangle englobant est une zone volumétrique minimale qui entoure un objet 3D.</span><span class="sxs-lookup"><span data-stu-id="0f36d-162">A bounding box is a minimum volumetric area that encloses a 3D object.</span></span> <span data-ttu-id="0f36d-163">Le rectangle englobant comporte un mécanisme de rendu interactif appelé nuanceur de proximité.</span><span class="sxs-lookup"><span data-stu-id="0f36d-163">The bounding box has an interactive rendering mechanism called a proximity shader.</span></span> <span data-ttu-id="0f36d-164">Le nuanceur de proximité se comporte comme suit :</span><span class="sxs-lookup"><span data-stu-id="0f36d-164">The proximity shader behaves:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="0f36d-165">![Pointage (éloigné) avec retour visuel](images/bounding-box-with-proximity-shader-hover-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="0f36d-165">![Hover (far) with visual feedback](images/bounding-box-with-proximity-shader-hover-far.jpg)</span></span><br>
       <span data-ttu-id="0f36d-166">**Pointage (éloigné)**</span><span class="sxs-lookup"><span data-stu-id="0f36d-166">**Hover (far)**</span></span><br>
       <span data-ttu-id="0f36d-167">Quand l’index se trouve dans la plage appropriée, un faisceau lumineux situé à la pointe du doigt est projeté à la surface du rectangle englobant.</span><span class="sxs-lookup"><span data-stu-id="0f36d-167">When the index finger is within a range, a fingertip spotlight is cast on the surface of the bounding box.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0f36d-168">![Pointage (proche) avec retour visuel](images/bounding-box-with-proximity-shader-hover-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="0f36d-168">![Hover (near) with visual feedback](images/bounding-box-with-proximity-shader-hover-near.jpg)</span></span><br>
        <span data-ttu-id="0f36d-169">**Pointage (proche)**</span><span class="sxs-lookup"><span data-stu-id="0f36d-169">**Hover (near)**</span></span><br>
        <span data-ttu-id="0f36d-170">Plus la pointe du doigt se rapproche de la surface, plus le faisceau lumineux projeté est réduit.</span><span class="sxs-lookup"><span data-stu-id="0f36d-170">When the fingertip gets closer to the surface, the spotlight shrinks.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0f36d-171">![Début du contact](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="0f36d-171">![Contact begins](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span></span><br>
       <span data-ttu-id="0f36d-172">**Début du contact**</span><span class="sxs-lookup"><span data-stu-id="0f36d-172">**Contact begins**</span></span><br>
       <span data-ttu-id="0f36d-173">Dès que la pointe du doigt touche la surface, tout le rectangle englobant change de couleur ou génère des effets visuels pour refléter l’état tactile.</span><span class="sxs-lookup"><span data-stu-id="0f36d-173">As soon as the fingertip touches the surface, the entire bounding box changes color or generates visual effects to reflect the touch state.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0f36d-174">![Fin du contact](images/bounding-box-with-proximity-shader-end-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="0f36d-174">![Contact ends](images/bounding-box-with-proximity-shader-end-contact.jpg)</span></span><br>
       <span data-ttu-id="0f36d-175">**Fin du contact**</span><span class="sxs-lookup"><span data-stu-id="0f36d-175">**Contact ends**</span></span><br>
       <span data-ttu-id="0f36d-176">Il est également possible d’activer un effet sonore pour améliorer la rétroaction tactile visuelle.</span><span class="sxs-lookup"><span data-stu-id="0f36d-176">A sound effect can also be activated to enhance the visual touch feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="pressable-button"></a><span data-ttu-id="0f36d-177">Bouton sur lequel appuyer</span><span class="sxs-lookup"><span data-stu-id="0f36d-177">Pressable button</span></span>

<span data-ttu-id="0f36d-178">Avec une pointe de doigt pourvue de la détection de collision, les utilisateurs sont désormais prêts à interagir avec un composant d’IU holographique fondamental, à savoir un bouton sur lequel appuyer.</span><span class="sxs-lookup"><span data-stu-id="0f36d-178">With a collidable fingertip, users are now ready to interact with a fundamental holographic UI component, such as a pressable button.</span></span> <span data-ttu-id="0f36d-179">Ce type de bouton est un composant holographique conçu pour une pression directe à l’aide du doigt.</span><span class="sxs-lookup"><span data-stu-id="0f36d-179">A pressable button is a holographic button tailored for a direct finger press.</span></span> <span data-ttu-id="0f36d-180">Là encore, en raison du manque de rétroaction tactile, un bouton sur lequel il est possible d’appuyer associe deux mécanismes pour traiter les problèmes de rétroaction tactile.</span><span class="sxs-lookup"><span data-stu-id="0f36d-180">Again, because of the lack of tactile feedback, a pressable button equips a couple mechanisms to tackle tactile feedback-related issues.</span></span>

* <span data-ttu-id="0f36d-181">Le premier mécanisme est un rectangle englobant avec nuanceur de proximité, détaillé dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="0f36d-181">The first mechanism is a bounding box with a proximity shader, which is detailed in the previous section.</span></span> <span data-ttu-id="0f36d-182">Il offre aux utilisateurs une meilleure sensation de proximité lors de l’approche et du contact avec un bouton.</span><span class="sxs-lookup"><span data-stu-id="0f36d-182">It gives users a better sense of proximity when they approach and make contact with a button.</span></span>
* <span data-ttu-id="0f36d-183">Le second mécanisme est une dépression.</span><span class="sxs-lookup"><span data-stu-id="0f36d-183">The second mechanism is depression.</span></span> <span data-ttu-id="0f36d-184">La dépression crée une sensation de pression lorsque le doigt entre en contact avec un bouton.</span><span class="sxs-lookup"><span data-stu-id="0f36d-184">Depression creates a sense of pressing down after a fingertip contacts a button.</span></span> <span data-ttu-id="0f36d-185">Ce mécanisme permet de veiller à ce que le bouton se déplace étroitement avec la pointe du doigt dans l’axe de profondeur.</span><span class="sxs-lookup"><span data-stu-id="0f36d-185">The mechanism ensures that the button tightly moves with the fingertip along the depth axis.</span></span> <span data-ttu-id="0f36d-186">Le bouton peut se déclencher quand il atteint une profondeur choisie (l’utilisateur appuie sur le bouton) ou quand il quitte cette profondeur (l’utilisateur relâche le bouton).</span><span class="sxs-lookup"><span data-stu-id="0f36d-186">The button can be triggered when it reaches a chosen depth (on press) or leaves the depth (on release) after passing through it.</span></span>
* <span data-ttu-id="0f36d-187">Il est possible d’ajouter un effet sonore pour améliorer la rétroaction quand le bouton se déclenche.</span><span class="sxs-lookup"><span data-stu-id="0f36d-187">The sound effect should be added to enhance feedback when the button is triggered.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="0f36d-188">![Bouton sur lequel appuyer éloigné](images/pressable-button-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="0f36d-188">![pressable button far](images/pressable-button-far.jpg)</span></span><br>
       <span data-ttu-id="0f36d-189">**Doigt éloigné**</span><span class="sxs-lookup"><span data-stu-id="0f36d-189">**Finger is far away**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0f36d-190">![Bouton sur lequel appuyer proche](images/pressable-button-approach.jpg)</span><span class="sxs-lookup"><span data-stu-id="0f36d-190">![pressable button near](images/pressable-button-approach.jpg)</span></span><br>
        <span data-ttu-id="0f36d-191">**Doigt en approche**</span><span class="sxs-lookup"><span data-stu-id="0f36d-191">**Finger approaches**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0f36d-192">![Début du contact avec le bouton sur lequel appuyer](images/pressable-button-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="0f36d-192">![pressable button contact begins](images/pressable-button-contact.jpg)</span></span><br>
       <span data-ttu-id="0f36d-193">**Début du contact**</span><span class="sxs-lookup"><span data-stu-id="0f36d-193">**Contact begins**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0f36d-194">![Appui sur le bouton sur lequel appuyer](images/pressable-button-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="0f36d-194">![pressable button press](images/pressable-button-press.jpg)</span></span><br>
       <span data-ttu-id="0f36d-195">**Appui**</span><span class="sxs-lookup"><span data-stu-id="0f36d-195">**Press down**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="0f36d-196">Interaction avec une tablette 2D</span><span class="sxs-lookup"><span data-stu-id="0f36d-196">2D slate interaction</span></span>

<span data-ttu-id="0f36d-197">Une [tablette](slate.md) 2D est un conteneur holographique utilisé pour héberger le contenu d’applications 2D comme un navigateur web.</span><span class="sxs-lookup"><span data-stu-id="0f36d-197">A 2D [slate](slate.md) is a holographic container used to host 2D app content, such as a web browser.</span></span> <span data-ttu-id="0f36d-198">L’interaction avec une tablette 2D par manipulation directe est la même chose que l’interaction avec un écran tactile physique.</span><span class="sxs-lookup"><span data-stu-id="0f36d-198">The design concept for interacting with a 2D slate via direct manipulation is the same as interacting with a physical touch screen.</span></span>

### <a name="to-interact-with-the-slate-contact"></a><span data-ttu-id="0f36d-199">Pour interagir avec la tablette par contact</span><span class="sxs-lookup"><span data-stu-id="0f36d-199">To interact with the slate contact</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="0f36d-200">![Interface tactile](images/2d-slate-interaction-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="0f36d-200">![Touch](images/2d-slate-interaction-touch.jpg)</span></span><br>
       <span data-ttu-id="0f36d-201">**Interface tactile**</span><span class="sxs-lookup"><span data-stu-id="0f36d-201">**Touch**</span></span><br>
       <span data-ttu-id="0f36d-202">Utilisez l’index pour appuyer sur un lien hypertexte ou un bouton.</span><span class="sxs-lookup"><span data-stu-id="0f36d-202">Use an index finger to press a hyperlink or a button.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0f36d-203">![Faire défiler](images/2d-slate-interaction-scroll2.jpg)</span><span class="sxs-lookup"><span data-stu-id="0f36d-203">![Scroll](images/2d-slate-interaction-scroll2.jpg)</span></span><br>
        <span data-ttu-id="0f36d-204">**Faire défiler**</span><span class="sxs-lookup"><span data-stu-id="0f36d-204">**Scroll**</span></span><br>
        <span data-ttu-id="0f36d-205">Utilisez l’index pour faire défiler le contenu de la tablette vers le haut et vers le bas.</span><span class="sxs-lookup"><span data-stu-id="0f36d-205">Use an index finger to scroll a slate content up and down.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0f36d-206">![Zoom](images/2d-slate-interaction-zoom2.jpg)</span><span class="sxs-lookup"><span data-stu-id="0f36d-206">![Zoom](images/2d-slate-interaction-zoom2.jpg)</span></span><br>
       <span data-ttu-id="0f36d-207">**Zoom**</span><span class="sxs-lookup"><span data-stu-id="0f36d-207">**Zoom**</span></span><br>
       <span data-ttu-id="0f36d-208">Les deux index de l’utilisateur sont utilisés pour effectuer un zoom avant ou arrière sur le contenu de la tablette en fonction du mouvement relatif des doigts.</span><span class="sxs-lookup"><span data-stu-id="0f36d-208">The user's two index fingers are used to zoom in and out of the slate content, according to the relative motion of the fingers.</span></span>
    :::column-end:::
:::row-end:::


### <a name="for-manipulating-the-2d-slate-itself"></a><span data-ttu-id="0f36d-209">Pour manipuler la tablette 2D</span><span class="sxs-lookup"><span data-stu-id="0f36d-209">For manipulating the 2D slate itself</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="0f36d-210">![Graphique présentant la fonctionnalité de saisie et de déplacement](images/manipulate-2d-slate-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="0f36d-210">![Graphic showing grab and drag feature](images/manipulate-2d-slate-move.jpg)</span></span><br>
       <span data-ttu-id="0f36d-211">**Déplacer**</span><span class="sxs-lookup"><span data-stu-id="0f36d-211">**Move**</span></span><br>
       <span data-ttu-id="0f36d-212">Déplacez vos mains vers les coins et les bords pour faire apparaître les affordances de manipulation les plus proches.</span><span class="sxs-lookup"><span data-stu-id="0f36d-212">Move your hands toward corners and edges to reveal the closest manipulation affordances.</span></span> <span data-ttu-id="0f36d-213">Saisissez la barre holographique en haut de la tablette 2D pour pouvoir déplacer la tablette entière.</span><span class="sxs-lookup"><span data-stu-id="0f36d-213">Grab the Holobar at the top of the 2D slate, which lets you move the whole slate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0f36d-214">![Graphique présentant la fonctionnalité de mise à l’échelle](images/manipulate-2d-slate-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="0f36d-214">![Graphic showing scale feature](images/manipulate-2d-slate-scale.jpg)</span></span><br>
        <span data-ttu-id="0f36d-215">**Mettre à l’échelle**</span><span class="sxs-lookup"><span data-stu-id="0f36d-215">**Scale**</span></span><br>
        <span data-ttu-id="0f36d-216">Saisissez les affordances de manipulation, puis effectuez une mise à l’échelle uniforme par le biais des affordances d’angle.</span><span class="sxs-lookup"><span data-stu-id="0f36d-216">Grab the manipulation affordances and do uniform scaling through the corner affordances.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0f36d-217">![Ajuster dynamiquement](images/manipulate-2d-slate-reflow.jpg)</span><span class="sxs-lookup"><span data-stu-id="0f36d-217">![Reflow](images/manipulate-2d-slate-reflow.jpg)</span></span><br>
       <span data-ttu-id="0f36d-218">**Ajuster dynamiquement**</span><span class="sxs-lookup"><span data-stu-id="0f36d-218">**Reflow**</span></span><br>
       <span data-ttu-id="0f36d-219">Saisissez les affordances de manipulation, puis effectuez un ajustement dynamique par le biais des affordances de bord.</span><span class="sxs-lookup"><span data-stu-id="0f36d-219">Grab the manipulation affordances and do reflow via the edge affordances.</span></span>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="3d-object-manipulation"></a><span data-ttu-id="0f36d-220">Manipulation d’objet 3D</span><span class="sxs-lookup"><span data-stu-id="0f36d-220">3D object manipulation</span></span>

<span data-ttu-id="0f36d-221">HoloLens 2 permet aux utilisateurs de diriger et manipuler des objets holographiques 3D en appliquant un rectangle englobant à chaque objet 3D.</span><span class="sxs-lookup"><span data-stu-id="0f36d-221">HoloLens 2 lets users enable their hands to direct and manipulate 3D holographic objects by applying a bounding box to each 3D object.</span></span> <span data-ttu-id="0f36d-222">La rectangle englobant offre une meilleure perception de la profondeur grâce à son nuanceur de proximité.</span><span class="sxs-lookup"><span data-stu-id="0f36d-222">The bounding box provides better depth perception through its proximity shader.</span></span> <span data-ttu-id="0f36d-223">Avec le rectangle englobant, il existe deux approches de conception pour la manipulation d’objets 3D.</span><span class="sxs-lookup"><span data-stu-id="0f36d-223">With the bounding box, there are two design approaches for 3D object manipulation.</span></span>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="0f36d-224">Manipulation basée sur l’affordance</span><span class="sxs-lookup"><span data-stu-id="0f36d-224">Affordance-based manipulation</span></span>

<span data-ttu-id="0f36d-225">La manipulation basée sur l’affordance vous permet de manipuler l’objet 3D via un rectangle englobant avec les affordances de manipulation qui l’entourent.</span><span class="sxs-lookup"><span data-stu-id="0f36d-225">Affordance-base manipulation lets you manipulate the 3D object through a bounding box along with the manipulation affordances around it.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="0f36d-226">![Graphique présentant le rectangle englobant d’un objet et la fonctionnalité de déplacement](images/3d-object-manipulation-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="0f36d-226">![Graphic showing an objects bounding box and move feature](images/3d-object-manipulation-move.jpg)</span></span><br>
       <span data-ttu-id="0f36d-227">**Déplacer**</span><span class="sxs-lookup"><span data-stu-id="0f36d-227">**Move**</span></span><br>
       <span data-ttu-id="0f36d-228">Dès que la main d’un utilisateur est proche d’un objet 3D, le rectangle englobant et l’affordance la plus proche apparaissent.</span><span class="sxs-lookup"><span data-stu-id="0f36d-228">As soon as a user's hand is close to a 3D object, the bounding box, and the nearest affordance are revealed.</span></span> <span data-ttu-id="0f36d-229">Les utilisateurs peuvent saisir le rectangle englobant pour déplacer l’objet entier.</span><span class="sxs-lookup"><span data-stu-id="0f36d-229">Users can grab the bounding box to move the whole object.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0f36d-230">![Graphique montrant l’utilisateur saisissant le bord d’un objet pour effectuer une rotation](images/3d-object-manipulation-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="0f36d-230">![Graphic showing user grabbing an objects edge to rotate](images/3d-object-manipulation-rotate.jpg)</span></span><br>
        <span data-ttu-id="0f36d-231">**Faire pivoter**</span><span class="sxs-lookup"><span data-stu-id="0f36d-231">**Rotate**</span></span><br>
        <span data-ttu-id="0f36d-232">Les utilisateurs peuvent saisir les affordances de bord pour effectuer une rotation.</span><span class="sxs-lookup"><span data-stu-id="0f36d-232">Users can grab the edge affordances to rotate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0f36d-233">![Graphique montrant l’utilisateur saisissant l’angle d’un objet pour effectuer une mise à l’échelle](images/3d-object-manipulation-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="0f36d-233">![Graphic showing user grabbing an objects corner to scale](images/3d-object-manipulation-scale.jpg)</span></span><br>
       <span data-ttu-id="0f36d-234">**Mettre à l’échelle**</span><span class="sxs-lookup"><span data-stu-id="0f36d-234">**Scale**</span></span><br>
       <span data-ttu-id="0f36d-235">Les utilisateurs peuvent saisir les affordances d’angle pour effectuer une mise à l’échelle uniforme.</span><span class="sxs-lookup"><span data-stu-id="0f36d-235">Users can grab the corner affordances to scale uniformly.</span></span>
    :::column-end:::
:::row-end:::

<br>


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="0f36d-236">Manipulation non basée sur l’affordance</span><span class="sxs-lookup"><span data-stu-id="0f36d-236">Non-affordance-based manipulation</span></span>

<span data-ttu-id="0f36d-237">La manipulation sans affordance n’attache pas l’affordance au cadre englobant.</span><span class="sxs-lookup"><span data-stu-id="0f36d-237">Non-affordance-based manipulation doesn't attach affordance to the bounding box.</span></span> <span data-ttu-id="0f36d-238">Les utilisateurs peuvent uniquement faire apparaître le rectangle englobant, puis interagir directement avec celui-ci.</span><span class="sxs-lookup"><span data-stu-id="0f36d-238">Users can only reveal the bounding box, then directly interact with it.</span></span> <span data-ttu-id="0f36d-239">Si les utilisateurs se saisissent du rectangle englobant à une seule main, la translation et la rotation de l’objet sont associées au mouvement et à l’orientation de la main.</span><span class="sxs-lookup"><span data-stu-id="0f36d-239">If the bounding box is grabbed with one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="0f36d-240">Quand les utilisateurs se saisissent de l’objet à deux mains, ils peuvent le translater, le mettre à l’échelle et le faire pivoter en fonction des mouvements relatifs des deux mains.</span><span class="sxs-lookup"><span data-stu-id="0f36d-240">When the object is grabbed with two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span>

<span data-ttu-id="0f36d-241">Une manipulation spécifique nécessite de la précision.</span><span class="sxs-lookup"><span data-stu-id="0f36d-241">Specific manipulation requires precision.</span></span> <span data-ttu-id="0f36d-242">Nous vous recommandons d’utiliser la **manipulation basée sur l’affordance**, car elle offre un haut niveau de granularité.</span><span class="sxs-lookup"><span data-stu-id="0f36d-242">We recommend that you use **affordance-based manipulation** because it provides a high level of granularity.</span></span> <span data-ttu-id="0f36d-243">Pour une manipulation flexible, nous vous recommandons d’utiliser la **manipulation sans affordance**, car elle offre une approche instantanée et ludique.</span><span class="sxs-lookup"><span data-stu-id="0f36d-243">For flexible manipulation, we recommend you use **non-affordance manipulation** as it allows for instant and playful experiences.</span></span>

<br>

---


## <a name="instinctual-gestures"></a><span data-ttu-id="0f36d-244">Mouvements instinctifs</span><span class="sxs-lookup"><span data-stu-id="0f36d-244">Instinctual gestures</span></span>

<span data-ttu-id="0f36d-245">Avec HoloLens (1re génération), nous avons montré aux utilisateurs quelques mouvements prédéfinis, tels qu’écarter les doigts paume vers le haut et cliquer dans l’air.</span><span class="sxs-lookup"><span data-stu-id="0f36d-245">With HoloLens (1st gen), we taught users a couple of predefined gestures, such as bloom and air tap.</span></span> <span data-ttu-id="0f36d-246">Avec HoloLens 2, nous ne demandons pas aux utilisateurs de mémoriser des mouvements symboliques.</span><span class="sxs-lookup"><span data-stu-id="0f36d-246">For HoloLens 2, we don't ask users to memorize any symbolic gestures.</span></span> <span data-ttu-id="0f36d-247">Tous les mouvements nécessaires à l’utilisateur qui lui permettent d’interagir avec les hologrammes et le contenu sont instinctifs.</span><span class="sxs-lookup"><span data-stu-id="0f36d-247">All required user gestures, where users need to interact with holograms and content, are instinctual.</span></span> <span data-ttu-id="0f36d-248">Les mouvements instinctifs doivent aider les utilisateurs à effectuer des mouvements via les affordances d’IU conçues à cet effet.</span><span class="sxs-lookup"><span data-stu-id="0f36d-248">The way to achieve instinctual gestures is to help users perform gestures through the design of UI affordances.</span></span>

<span data-ttu-id="0f36d-249">Par exemple, si nous encourageons l’utilisateur à saisir un objet ou un point de contrôle en le pinçant avec deux doigts, l’objet ou le point de contrôle doit être petit.</span><span class="sxs-lookup"><span data-stu-id="0f36d-249">For example, if we encourage the user to grab an object or a control point with a two finger pinch, the object or the control point should be small.</span></span> <span data-ttu-id="0f36d-250">Si nous souhaitons que l’utilisateur le saisisse avec cinq doigts, l’objet ou le point de contrôle doit être relativement grand.</span><span class="sxs-lookup"><span data-stu-id="0f36d-250">If we want the user to do a five finger grab, the object or the control point should be relatively large.</span></span> <span data-ttu-id="0f36d-251">Si nous prenons l’exemple des boutons, un tout petit bouton oblige les utilisateurs à appuyer dessus avec un seul doigt.</span><span class="sxs-lookup"><span data-stu-id="0f36d-251">Similar to buttons, a tiny button would limit users to press it with a single finger.</span></span> <span data-ttu-id="0f36d-252">Un gros bouton incite les utilisateurs à appuyer dessus avec la paume de la main.</span><span class="sxs-lookup"><span data-stu-id="0f36d-252">A large button would encourage users to press it with their palms.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="0f36d-253">![Graphique montrant l’utilisateur saisissant un petit objet afin de le déplacer](images/instinctual-gestures-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="0f36d-253">![Graphic showing user grabbing small object to move](images/instinctual-gestures-smallobject.jpg)</span></span><br>
       <span data-ttu-id="0f36d-254">**Petit objet**</span><span class="sxs-lookup"><span data-stu-id="0f36d-254">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0f36d-255">![Graphique montrant l’utilisateur saisissant un objet de taille moyenne afin de le déplacer](images/instinctual-gestures-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="0f36d-255">![Graphic showing user grabbing medium object to move](images/instinctual-gestures-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="0f36d-256">**Objet de taille moyenne**</span><span class="sxs-lookup"><span data-stu-id="0f36d-256">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="0f36d-257">![Graphique montrant l’utilisateur saisissant un objet volumineux afin de le déplacer](images/instinctual-gestures-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="0f36d-257">![Graphic showing user grabbing large object to move](images/instinctual-gestures-largeobject.jpg)</span></span><br>
       <span data-ttu-id="0f36d-258">**Objet volumineux**</span><span class="sxs-lookup"><span data-stu-id="0f36d-258">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---

<br>

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a><span data-ttu-id="0f36d-259">Conception symétrique entre les mains et les contrôleurs 6DoF</span><span class="sxs-lookup"><span data-stu-id="0f36d-259">Symmetric design between hands and 6 DoF controllers</span></span>

<span data-ttu-id="0f36d-260">Vous avez peut-être remarqué que nous pouvons établir des parallèles au niveau de l’interaction entre les mains en environnement AR (réalité augmentée) et les contrôleurs de mouvement en environnement VR (réalité virtuelle).</span><span class="sxs-lookup"><span data-stu-id="0f36d-260">You may have noticed that there are interaction parallels we can draw between hands in AR and motion controllers in VR.</span></span> <span data-ttu-id="0f36d-261">Les deux entrées peuvent être utilisées pour déclencher des manipulations directes dans leurs environnements respectifs.</span><span class="sxs-lookup"><span data-stu-id="0f36d-261">Both inputs can be used to trigger direct manipulations in their respective environments.</span></span> <span data-ttu-id="0f36d-262">Avec HoloLens 2, la saisie et le déplacement à l’aide des mains à courte distance fonctionnent de la même manière que le bouton de saisie des contrôleurs de mouvement WMR.</span><span class="sxs-lookup"><span data-stu-id="0f36d-262">In HoloLens 2, grabbing and dragging with hands at a close distance works much the same way as the grab button does on WMR motion controllers.</span></span> <span data-ttu-id="0f36d-263">Cela permet aux utilisateurs d’accéder à des interactions familières sur les deux plateformes. De plus, cela peut s’avérer utile si vous décidez de porter votre application d’une plateforme à l’autre.</span><span class="sxs-lookup"><span data-stu-id="0f36d-263">This provides users with interaction familiarity between the two platforms, which might prove useful if you ever decide to port your application between platforms.</span></span>

<br>

---

## <a name="optimize-with-eye-tracking"></a><span data-ttu-id="0f36d-264">Optimiser avec l’eye-tracking</span><span class="sxs-lookup"><span data-stu-id="0f36d-264">Optimize with eye tracking</span></span>

<span data-ttu-id="0f36d-265">La manipulation directe peut paraître magique si elle fonctionne comme prévu.</span><span class="sxs-lookup"><span data-stu-id="0f36d-265">Direct manipulation can feel magical if it works as intended.</span></span> <span data-ttu-id="0f36d-266">Mais elle peut également devenir frustrante si vous ne pouvez pas bouger votre main sans déclencher involontairement un hologramme.</span><span class="sxs-lookup"><span data-stu-id="0f36d-266">But it can also become frustrating if you can’t move your hand anywhere without unintentionally triggering a hologram.</span></span> <span data-ttu-id="0f36d-267">Le suivi oculaire peut vous aider à mieux identifier l’intention de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0f36d-267">Eye tracking potentially helps to better identify what the user’s intent is.</span></span>

* <span data-ttu-id="0f36d-268">**Quand** : Réduisez le déclenchements par inadvertance d’une réponse à une manipulation.</span><span class="sxs-lookup"><span data-stu-id="0f36d-268">**When**: Reduce unintentionally triggering a manipulation response.</span></span> <span data-ttu-id="0f36d-269">L’eye-tracking permet de mieux comprendre l’engagement de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0f36d-269">Eye tracking allows for better understanding what a user is currently engaged with.</span></span>
<span data-ttu-id="0f36d-270">Par exemple, supposons que vous lisiez un texte holographique (instructions) quand vous tendez la main pour saisir votre outil de travail réel.</span><span class="sxs-lookup"><span data-stu-id="0f36d-270">For example, imagine you're reading through a holographic (instructional) text when reaching over to grab you real-world work tool.</span></span>

<span data-ttu-id="0f36d-271">En procédant ainsi, vous passez accidentellement votre main sur des boutons holographiques interactifs que vous n’aviez même pas remarqués.</span><span class="sxs-lookup"><span data-stu-id="0f36d-271">By doing so, you accidentally move your hand across some interactive holographic buttons that you hadn't even noticed before.</span></span> <span data-ttu-id="0f36d-272">Par exemple, ils peuvent être situés en dehors du champ de vision de l’utilisateur (FoV).</span><span class="sxs-lookup"><span data-stu-id="0f36d-272">For example, it  may be outside the user's field-of-view (FoV).</span></span>

<span data-ttu-id="0f36d-273">Si l’utilisateur n’a pas regardé un hologramme depuis un certain temps et si un événement tactile ou de saisie a été détecté, l’interaction est probablement involontaire.</span><span class="sxs-lookup"><span data-stu-id="0f36d-273">If the user hasn't looked at a hologram for a while, yet a touch or grasp event has been detected for it, the interaction is likely unintentional.</span></span>

* <span data-ttu-id="0f36d-274">**Lequel** :  En plus du traitement des activations correspondant à des faux positifs, il est également possible d’améliorer l’identification des hologrammes à saisir ou à pousser, car le point d’intersection n’est pas forcément clair selon votre perspective, surtout si plusieurs hologrammes sont proches les uns des autres.</span><span class="sxs-lookup"><span data-stu-id="0f36d-274">**Which one**:  Aside from addressing false positive activations, another example includes better identifying which holograms to grab or poke as the precise intersection point may not be clear from your perspective, especially if several holograms are positioned close to each other.</span></span>

  <span data-ttu-id="0f36d-275">Bien que l’eye-tracking sur HoloLens 2 soit parfois limité au niveau de la précision avec laquelle il évalue votre regard, il peut être utile pour les interactions rapprochées en raison de la disparité de la profondeur quand vous interagissez avec la saisie manuelle.</span><span class="sxs-lookup"><span data-stu-id="0f36d-275">While eye tracking on HoloLens 2 has limitations based on how accurately it can determine your eye gaze, this can still be helpful for near interactions because of depth disparity when interacting with hand input.</span></span> <span data-ttu-id="0f36d-276">Cela signifie qu’il est parfois difficile de déterminer si votre main est placée derrière ou devant un hologramme pour saisir avec précision un widget de manipulation, par exemple.</span><span class="sxs-lookup"><span data-stu-id="0f36d-276">This means it's sometimes difficult to determine whether your hand is behind or in front of a hologram to precisely grab a manipulation widget, for example.</span></span>

* <span data-ttu-id="0f36d-277">**Où** : Utilisez les informations relatives à ce qu’un utilisateur regarde avec des mouvements rapides.</span><span class="sxs-lookup"><span data-stu-id="0f36d-277">**Where to**: Use information about what a user is looking at with quick-throwing gestures.</span></span> <span data-ttu-id="0f36d-278">Saisissez un hologramme et lancez-le à peu près vers l’emplacement souhaité.</span><span class="sxs-lookup"><span data-stu-id="0f36d-278">Grab a hologram and roughly toss it toward your intended destination.</span></span>  

    <span data-ttu-id="0f36d-279">Bien que cela fonctionne parfois, les mouvements rapides de la main peuvent cibler des emplacements très imprécis.</span><span class="sxs-lookup"><span data-stu-id="0f36d-279">While this sometimes works, quickly doing hand gestures may result in highly inaccurate destinations.</span></span> <span data-ttu-id="0f36d-280">Toutefois, le suivi oculaire peut améliorer la précision du mouvement.</span><span class="sxs-lookup"><span data-stu-id="0f36d-280">However, eye tracking could improve the accuracy of the gesture.</span></span>

<br>

---

## <a name="manipulation-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="0f36d-281">Manipulation dans MRTK (Mixed Reality Toolkit) pour Unity</span><span class="sxs-lookup"><span data-stu-id="0f36d-281">Manipulation in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="0f36d-282">Avec **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** , vous pouvez facilement obtenir un comportement de manipulation courant à l’aide du script **ObjectManipulator**.</span><span class="sxs-lookup"><span data-stu-id="0f36d-282">With **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can easily achieve common manipulation behavior using the script **ObjectManipulator**.</span></span> <span data-ttu-id="0f36d-283">Avec ObjectManipulator, vous pouvez saisir et déplacer les objets directement avec les mains ou avec un rayon émanant de la main.</span><span class="sxs-lookup"><span data-stu-id="0f36d-283">With ObjectManipulator, you can grab and move objects directly with hands or with hand ray.</span></span> <span data-ttu-id="0f36d-284">Il prend également en charge les manipulations à deux mains pour la mise à l’échelle et la rotation des objets.</span><span class="sxs-lookup"><span data-stu-id="0f36d-284">It also supports two-handed manipulation for scaling and rotating an object.</span></span>

* [<span data-ttu-id="0f36d-285">MRTK - Manipulation</span><span class="sxs-lookup"><span data-stu-id="0f36d-285">MRTK - Manipulation</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-manipulator)

---

## <a name="see-also"></a><span data-ttu-id="0f36d-286">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f36d-286">See also</span></span>

* [<span data-ttu-id="0f36d-287">Suivre de la tête et valider</span><span class="sxs-lookup"><span data-stu-id="0f36d-287">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="0f36d-288">Pointer et valider avec les mains</span><span class="sxs-lookup"><span data-stu-id="0f36d-288">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="0f36d-289">Interactions instinctuelles</span><span class="sxs-lookup"><span data-stu-id="0f36d-289">Instinctual interactions</span></span>](interaction-fundamentals.md)