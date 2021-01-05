---
title: Billboarding et tag-along
description: Les objets avec des panneaux s’orientent toujours pour être confrontés à l’utilisateur.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, l’intégration, le balisage, le casque de réalité mixte, le casque de réalité mixte, le casque de réalité virtuelle, HoloLens, MRTK, le kit de temps de réalité mixte
ms.openlocfilehash: 44f2678fe2f8e4be071086f46037749d1df61ae4
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848028"
---
# <a name="billboarding-and-tag-along"></a><span data-ttu-id="d17ab-104">Billboarding et tag-along</span><span class="sxs-lookup"><span data-stu-id="d17ab-104">Billboarding and tag-along</span></span>

<br>

<img src="images/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a><span data-ttu-id="d17ab-105">Qu’est-ce que le billboarding ?</span><span class="sxs-lookup"><span data-stu-id="d17ab-105">What is billboarding?</span></span>

<span data-ttu-id="d17ab-106">Le billboarding est un concept comportemental qui peut être appliqué aux objets en réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="d17ab-106">Billboarding is a behavioral concept that can be applied to objects in mixed reality.</span></span> <span data-ttu-id="d17ab-107">Les objets avec des panneaux s’orientent toujours pour être confrontés à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d17ab-107">Objects with billboarding always orient themselves to face the user.</span></span> <span data-ttu-id="d17ab-108">Les systèmes de texte et de menu sont des cas d’utilisation courants, où les objets statiques placés dans l’environnement de l’utilisateur (verrouillé) seraient autrement masqués ou illisibles quand les utilisateurs se déplacent.</span><span class="sxs-lookup"><span data-stu-id="d17ab-108">Text and menu systems are common use cases, where static objects placed in the user's environment (world-locked) would be otherwise obscured or unreadable when users move around.</span></span>

<span data-ttu-id="d17ab-109">Les objets avec le billboarding activé peuvent pivoter librement dans l’environnement de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d17ab-109">Objects with billboarding enabled can rotate freely in the user's environment.</span></span> <span data-ttu-id="d17ab-110">Ils peuvent également être limités à un seul axe en fonction des considérations de conception.</span><span class="sxs-lookup"><span data-stu-id="d17ab-110">They can also be constrained to a single axis depending on design considerations.</span></span> <span data-ttu-id="d17ab-111">Gardez à l’esprit que les objets superposés peuvent découper ou occultait eux-mêmes lorsqu’ils sont placés trop près d’autres objets ou dans HoloLens, trop près de surfaces numérisées.</span><span class="sxs-lookup"><span data-stu-id="d17ab-111">Keep in mind, billboarded objects can clip or occlude themselves when placed too close to other objects, or in HoloLens, too close scanned surfaces.</span></span> <span data-ttu-id="d17ab-112">Pour éviter cela, réfléchissez à l’encombrement total qu’un objet peut produire en cas de rotation sur l’axe activé pour le billboarding.</span><span class="sxs-lookup"><span data-stu-id="d17ab-112">To avoid this, think about the total footprint an object may produce when rotated on the axis enabled for billboarding.</span></span>

<br>

---
## <a name="what-is-a-tag-along"></a><span data-ttu-id="d17ab-113">Qu’est-ce qu’une balise ?</span><span class="sxs-lookup"><span data-stu-id="d17ab-113">What is a tag-along?</span></span>

<span data-ttu-id="d17ab-114">La balise est un concept comportemental qui peut être ajouté à des hologrammes.</span><span class="sxs-lookup"><span data-stu-id="d17ab-114">Tag-along is a behavioral concept that can be added to holograms.</span></span> <span data-ttu-id="d17ab-115">Une balise associée à un objet tente de rester dans une plage qui permet à l’utilisateur d’interagir confortablement.</span><span class="sxs-lookup"><span data-stu-id="d17ab-115">A tag-along object attempts to stay in a range that allows the user to interact comfortably.</span></span>

<span data-ttu-id="d17ab-116">![Le panneau broches HoloLens est un bon exemple de la façon dont les balises se comportent](images/tagalong-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="d17ab-116">![The HoloLens pins panel is a great example of how tag-along behaves](images/tagalong-1000px.jpg)</span></span><br>
<span data-ttu-id="d17ab-117">*Le menu Démarrer HoloLens est un excellent exemple de comportement avec balises*</span><span class="sxs-lookup"><span data-stu-id="d17ab-117">*The HoloLens Start menu is a great example of tag-along behavior*</span></span>

<span data-ttu-id="d17ab-118">Les objets avec balise ont des paramètres, ce qui peut affiner la façon dont ils se comportent.</span><span class="sxs-lookup"><span data-stu-id="d17ab-118">Tag-along objects have parameters, which can fine-tune the way they behave.</span></span> <span data-ttu-id="d17ab-119">Le contenu peut être dans ou hors de la ligne de vue de l’utilisateur pendant que l’utilisateur se déplace dans son environnement.</span><span class="sxs-lookup"><span data-stu-id="d17ab-119">Content can be in or out of the user’s line of sight while the user moves around their environment.</span></span> <span data-ttu-id="d17ab-120">Au fur et à mesure que vous déplacez, le contenu tente de rester au sein de la périphérie de l’utilisateur en faisant glisser vers le bord de la vue.</span><span class="sxs-lookup"><span data-stu-id="d17ab-120">As you move, the content attempts to stay within the user’s periphery by sliding towards the edge of the view.</span></span> <span data-ttu-id="d17ab-121">Le contenu peut être temporairement hors de l’affichage en fonction de la vitesse de déplacement de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d17ab-121">The content might be temporarily out of view depending on how quickly the user is moving.</span></span> <span data-ttu-id="d17ab-122">Lorsque l’utilisateur fait un regard sur l’objet tag, il est plus complet à afficher.</span><span class="sxs-lookup"><span data-stu-id="d17ab-122">When the user gazes towards the tag-along object, it comes more fully into view.</span></span> <span data-ttu-id="d17ab-123">Imaginez que le contenu est toujours « un coup d’œil », de sorte que les utilisateurs n’oublient jamais de la direction dans laquelle ils se trouvent.</span><span class="sxs-lookup"><span data-stu-id="d17ab-123">Think of content always being "a glance away" so users never forget what direction their content is in.</span></span>

<span data-ttu-id="d17ab-124">Des paramètres supplémentaires peuvent faire en sorte que l’objet de la balise soit attaché à la tête de l’utilisateur par une bande de caoutchouc.</span><span class="sxs-lookup"><span data-stu-id="d17ab-124">Extra parameters can make the tag-along object feel attached to the user's head by a rubber band.</span></span> <span data-ttu-id="d17ab-125">Le blocage de l’accélération ou de la décélération donne du poids à l’objet, ce qui le rend plus physiquement présent.</span><span class="sxs-lookup"><span data-stu-id="d17ab-125">Dampening acceleration or deceleration gives weight to the object making it feel more physically present.</span></span> <span data-ttu-id="d17ab-126">Ce comportement de printemps est une offre qui permet à l’utilisateur de créer un modèle mental précis sur le fonctionnement de la balise.</span><span class="sxs-lookup"><span data-stu-id="d17ab-126">This spring behavior is an affordance that helps the user build an accurate mental model of how tag-along works.</span></span> <span data-ttu-id="d17ab-127">L’audio permet d’indiquer d’autres indications lorsque les utilisateurs disposent d’objets en mode balise.</span><span class="sxs-lookup"><span data-stu-id="d17ab-127">Audio helps provide other cues for when users have objects in tag-along mode.</span></span> <span data-ttu-id="d17ab-128">L’audio doit renforcer la vitesse de déplacement. une rotation rapide doit fournir un effet sonore plus notable, tandis que la marche à une vitesse naturelle doit avoir un impact minime ou aucun effet audio.</span><span class="sxs-lookup"><span data-stu-id="d17ab-128">Audio should reinforce the speed of movement; a fast head turn should provide a more noticeable sound effect, while walking at a natural speed should have minimal or no audio effects.</span></span>

<span data-ttu-id="d17ab-129">À l’instar du contenu véritablement verrouillé, les objets de balise peuvent se révéler insurmontables ou nauseating s’ils se déplacent de manière incomplète dans la vue de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d17ab-129">Just like truly head-locked content, tag-along objects can prove overwhelming or nauseating if they move wildly or spring too much in the user’s view.</span></span> <span data-ttu-id="d17ab-130">À mesure qu’un utilisateur regarde, puis s’arrête rapidement, son sens les indique qu’il s’est arrêté.</span><span class="sxs-lookup"><span data-stu-id="d17ab-130">As a user looks around, then quickly stops, their senses tell them they've stopped.</span></span> <span data-ttu-id="d17ab-131">Leur solde les informe que leur tête a cessé de tourner et que leur vision voit que le monde cesse de tourner.</span><span class="sxs-lookup"><span data-stu-id="d17ab-131">Their balance informs them that their head has stopped turning and their vision sees the world stop turning.</span></span> <span data-ttu-id="d17ab-132">Toutefois, si tag-with continue à se déplacer lorsque l’utilisateur s’est arrêté, il peut confondre leurs sens.</span><span class="sxs-lookup"><span data-stu-id="d17ab-132">However, if tag-along keeps on moving when the user has stopped, it may confuse their senses.</span></span>

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="d17ab-133">Superpointage et balise dans MRTK (kit de temps de réalité mixte) pour Unity</span><span class="sxs-lookup"><span data-stu-id="d17ab-133">Billboarding and Tag-along in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="d17ab-134">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fournit des scripts pour le comportement de l’analyseur et de la balise.</span><span class="sxs-lookup"><span data-stu-id="d17ab-134">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts for the Billboarding and tag-along behavior.</span></span> <span data-ttu-id="d17ab-135">Affectez le script Billboard.cs à n’importe quel objet pour ajouter un comportement d’emboutment et faire en sorte que l’objet soit toujours à votre Confront.</span><span class="sxs-lookup"><span data-stu-id="d17ab-135">Assign the Billboard.cs script onto any object to add billboarding behavior and make the object always face you.</span></span> <span data-ttu-id="d17ab-136">Pour ajouter un comportement avec balise, utilisez le script RadialView.cs.</span><span class="sxs-lookup"><span data-stu-id="d17ab-136">To add tag-along behavior, use the RadialView.cs script.</span></span> <span data-ttu-id="d17ab-137">Vous pouvez ajuster diverses options, telles que le temps de lerping, la distance et le degré.</span><span class="sxs-lookup"><span data-stu-id="d17ab-137">You can adjust various options such as lerping time, distance, and degree.</span></span>

* [<span data-ttu-id="d17ab-138">MRTK : solveur de vue radiale</span><span class="sxs-lookup"><span data-stu-id="d17ab-138">MRTK - Radial View Solver</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html#radialview)
* [<span data-ttu-id="d17ab-139">Script MRTK-Billboard</span><span class="sxs-lookup"><span data-stu-id="d17ab-139">MRTK - Billboard script</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


<br>

---

## <a name="see-also"></a><span data-ttu-id="d17ab-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d17ab-140">See also</span></span>

* [<span data-ttu-id="d17ab-141">Curseurs</span><span class="sxs-lookup"><span data-stu-id="d17ab-141">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="d17ab-142">Rayon émanant de la main</span><span class="sxs-lookup"><span data-stu-id="d17ab-142">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="d17ab-143">Button</span><span class="sxs-lookup"><span data-stu-id="d17ab-143">Button</span></span>](button.md)
* [<span data-ttu-id="d17ab-144">Objet avec interaction possible</span><span class="sxs-lookup"><span data-stu-id="d17ab-144">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="d17ab-145">Rectangle englobant et barre de l’application</span><span class="sxs-lookup"><span data-stu-id="d17ab-145">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="d17ab-146">Manipulation</span><span class="sxs-lookup"><span data-stu-id="d17ab-146">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="d17ab-147">Menu de la main</span><span class="sxs-lookup"><span data-stu-id="d17ab-147">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="d17ab-148">Menu proche</span><span class="sxs-lookup"><span data-stu-id="d17ab-148">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="d17ab-149">Collection d’objets</span><span class="sxs-lookup"><span data-stu-id="d17ab-149">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="d17ab-150">Commande vocale</span><span class="sxs-lookup"><span data-stu-id="d17ab-150">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="d17ab-151">Clavier</span><span class="sxs-lookup"><span data-stu-id="d17ab-151">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="d17ab-152">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="d17ab-152">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="d17ab-153">Tablette</span><span class="sxs-lookup"><span data-stu-id="d17ab-153">Slate</span></span>](slate.md)
* [<span data-ttu-id="d17ab-154">Curseur</span><span class="sxs-lookup"><span data-stu-id="d17ab-154">Slider</span></span>](slider.md)
* [<span data-ttu-id="d17ab-155">Nuanceur</span><span class="sxs-lookup"><span data-stu-id="d17ab-155">Shader</span></span>](shader.md)
* [<span data-ttu-id="d17ab-156">Billboarding et tag-along</span><span class="sxs-lookup"><span data-stu-id="d17ab-156">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="d17ab-157">Affichage de la progression</span><span class="sxs-lookup"><span data-stu-id="d17ab-157">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="d17ab-158">Aimantation de surface</span><span class="sxs-lookup"><span data-stu-id="d17ab-158">Surface magnetism</span></span>](surface-magnetism.md)
