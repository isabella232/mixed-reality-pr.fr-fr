---
title: Billboarding et tag-along
description: Les objets avec des panneaux s’orientent toujours pour être confrontés à l’utilisateur.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, l’intégration, le balisage, le casque de réalité mixte, le casque de réalité mixte, le casque de réalité virtuelle, HoloLens, MRTK, le kit de temps de réalité mixte
ms.openlocfilehash: 1f40e1b180eccd8b79da43a07f969375d5135508
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702885"
---
# <a name="billboarding-and-tag-along"></a><span data-ttu-id="ac464-104">Billboarding et tag-along</span><span class="sxs-lookup"><span data-stu-id="ac464-104">Billboarding and tag-along</span></span>

<br>

<img src="images/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a><span data-ttu-id="ac464-105">Qu’est-ce que le billboarding ?</span><span class="sxs-lookup"><span data-stu-id="ac464-105">What is billboarding?</span></span>

<span data-ttu-id="ac464-106">Le billboarding est un concept comportemental qui peut être appliqué aux objets en réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="ac464-106">Billboarding is a behavioral concept that can be applied to objects in mixed reality.</span></span> <span data-ttu-id="ac464-107">Les objets avec des panneaux s’orientent toujours pour être confrontés à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ac464-107">Objects with billboarding always orient themselves to face the user.</span></span> <span data-ttu-id="ac464-108">Cela s’avère particulièrement utile avec les systèmes de texte et de menu où les objets statiques placés dans l’environnement de l’utilisateur (verrouillé) seraient autrement masqués ou illisibles si un utilisateur se déplace.</span><span class="sxs-lookup"><span data-stu-id="ac464-108">This is especially helpful with text and menuing systems where static objects placed in the user's environment (world-locked) would be otherwise obscured or unreadable if a user were to move around.</span></span>

<span data-ttu-id="ac464-109">Les objets avec le billboarding activé peuvent pivoter librement dans l’environnement de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ac464-109">Objects with billboarding enabled can rotate freely in the user's environment.</span></span> <span data-ttu-id="ac464-110">Ils peuvent également être limités à un seul axe en fonction des considérations de conception.</span><span class="sxs-lookup"><span data-stu-id="ac464-110">They can also be constrained to a single axis depending on design considerations.</span></span> <span data-ttu-id="ac464-111">Gardez à l’esprit que les objets superposés peuvent découper ou occultait eux-mêmes s’ils sont placés trop près d’autres objets, ou dans HoloLens, trop proches des surfaces numérisées.</span><span class="sxs-lookup"><span data-stu-id="ac464-111">Keep in mind, billboarded objects may clip or occlude themselves if they are placed too close to other objects, or in HoloLens, too close scanned surfaces.</span></span> <span data-ttu-id="ac464-112">Pour éviter cela, réfléchissez à l’encombrement total qu’un objet peut produire en cas de rotation sur l’axe activé pour le billboarding.</span><span class="sxs-lookup"><span data-stu-id="ac464-112">To avoid this, think about the total footprint an object may produce when rotated on the axis enabled for billboarding.</span></span>

<br>

---
## <a name="what-is-a-tag-along"></a><span data-ttu-id="ac464-113">Qu’est-ce qu’une balise ?</span><span class="sxs-lookup"><span data-stu-id="ac464-113">What is a tag-along?</span></span>

<span data-ttu-id="ac464-114">La balise est un concept comportemental qui peut être ajouté à des hologrammes.</span><span class="sxs-lookup"><span data-stu-id="ac464-114">Tag-along is a behavioral concept that can be added to holograms.</span></span> <span data-ttu-id="ac464-115">Une balise associée à un objet tente de rester dans une plage qui permet à l’utilisateur d’interagir confortablement.</span><span class="sxs-lookup"><span data-stu-id="ac464-115">A tag-along object attempts to stay in a range that allows the user to interact comfortably.</span></span>

<span data-ttu-id="ac464-116">![Le panneau broches HoloLens est un bon exemple de la façon dont les balises se comportent](images/tagalong-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="ac464-116">![The HoloLens pins panel is a great example of how tag-along behaves](images/tagalong-1000px.jpg)</span></span><br>
<span data-ttu-id="ac464-117">*Le menu Démarrer HoloLens est un excellent exemple de comportement avec balises*</span><span class="sxs-lookup"><span data-stu-id="ac464-117">*The HoloLens Start menu is a great example of tag-along behavior*</span></span>

<span data-ttu-id="ac464-118">Les objets avec balise ont des paramètres qui peuvent affiner la façon dont ils se comportent.</span><span class="sxs-lookup"><span data-stu-id="ac464-118">Tag-along objects have parameters which can fine-tune the way they behave.</span></span> <span data-ttu-id="ac464-119">Le contenu peut être dans ou en dehors de la ligne de vue de l’utilisateur, au fur et à mesure que l’utilisateur se déplace dans son environnement.</span><span class="sxs-lookup"><span data-stu-id="ac464-119">Content can be in or out of the user’s line of sight as desired while the user moves around their environment.</span></span> <span data-ttu-id="ac464-120">Au fur et à mesure que l’utilisateur se déplace, le contenu tente de rester au sein de la périphérie de l’utilisateur en faisant glisser vers le bord de la vue, en fonction de la vitesse à laquelle un utilisateur se déplace, en laissant le contenu temporairement hors de l’affichage.</span><span class="sxs-lookup"><span data-stu-id="ac464-120">As the user moves, the content will attempt to stay within the user’s periphery by sliding towards the edge of the view, depending on how quickly a user moves may leave the content temporarily out of view.</span></span> <span data-ttu-id="ac464-121">Lorsque l’utilisateur fait un regard sur l’objet tag, il est plus complet à afficher.</span><span class="sxs-lookup"><span data-stu-id="ac464-121">When the user gazes towards the tag-along object, it comes more fully into view.</span></span> <span data-ttu-id="ac464-122">Imaginez que le contenu est toujours « un coup d’œil », de sorte que les utilisateurs n’oublient jamais de la direction dans laquelle ils se trouvent.</span><span class="sxs-lookup"><span data-stu-id="ac464-122">Think of content always being "a glance away" so users never forget what direction their content is in.</span></span>

<span data-ttu-id="ac464-123">Des paramètres supplémentaires peuvent faire en sorte que l’objet de la balise soit attaché à la tête de l’utilisateur par une bande de caoutchouc.</span><span class="sxs-lookup"><span data-stu-id="ac464-123">Additional parameters can make the tag-along object feel attached to the user's head by a rubber band.</span></span> <span data-ttu-id="ac464-124">Le blocage de l’accélération ou de la décélération donne du poids à l’objet, ce qui le rend plus physiquement présent.</span><span class="sxs-lookup"><span data-stu-id="ac464-124">Dampening acceleration or deceleration gives weight to the object making it feel more physically present.</span></span> <span data-ttu-id="ac464-125">Ce comportement de printemps est une offre qui permet à l’utilisateur de créer un modèle mental précis sur le fonctionnement de la balise.</span><span class="sxs-lookup"><span data-stu-id="ac464-125">This spring behavior is an affordance that helps the user build an accurate mental model of how tag-along works.</span></span> <span data-ttu-id="ac464-126">L’audio aide à fournir des intuitivité supplémentaires quand les utilisateurs disposent d’objets en mode balise.</span><span class="sxs-lookup"><span data-stu-id="ac464-126">Audio helps provide additional affordances for when users have objects in tag-along mode.</span></span> <span data-ttu-id="ac464-127">L’audio doit renforcer la vitesse de déplacement. un tour rapide doit fournir un effet sonore plus notable tout en passant à une vitesse naturelle, en cas de tout effet.</span><span class="sxs-lookup"><span data-stu-id="ac464-127">Audio should reinforce the speed of movement; a fast head turn should provide a more noticeable sound effect while walking at a natural speed should have minimal audio if any effects at all.</span></span>

<span data-ttu-id="ac464-128">À l’instar du contenu véritablement verrouillé, les objets de balise peuvent se révéler insurmontables ou nauseating s’ils se déplacent de manière incomplète dans la vue de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ac464-128">Just like truly head-locked content, tag-along objects can prove overwhelming or nauseating if they move wildly or spring too much in the user’s view.</span></span> <span data-ttu-id="ac464-129">À mesure qu’un utilisateur regarde et s’arrête rapidement, ses sens les indiquent qu’il a cessé.</span><span class="sxs-lookup"><span data-stu-id="ac464-129">As a user looks around and then quickly stop, their senses tell them they have stopped.</span></span> <span data-ttu-id="ac464-130">Leur solde les informe que leur tête a cessé de tourner et que leur vision voit que le monde cesse de tourner.</span><span class="sxs-lookup"><span data-stu-id="ac464-130">Their balance informs them that their head has stopped turning as well as their vision sees the world stop turning.</span></span> <span data-ttu-id="ac464-131">Toutefois, si tag-with continue à se déplacer lorsque l’utilisateur s’est arrêté, il peut confondre leurs sens.</span><span class="sxs-lookup"><span data-stu-id="ac464-131">However, if tag-along keeps on moving when the user has stopped, it may confuse their senses.</span></span>

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="ac464-132">Superpointage et balise dans MRTK (kit de temps de réalité mixte) pour Unity</span><span class="sxs-lookup"><span data-stu-id="ac464-132">Billboarding and Tag-along in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="ac464-133">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fournit des scripts pour le comportement de l’analyseur et de la balise.</span><span class="sxs-lookup"><span data-stu-id="ac464-133">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts for the Billboarding and tag-along behavior.</span></span> <span data-ttu-id="ac464-134">Il vous suffit d’affecter le script Billboard.cs à n’importe quel objet pour ajouter le comportement de l’analyseur et de faire en sorte que l’objet soit toujours présent.</span><span class="sxs-lookup"><span data-stu-id="ac464-134">Simply assign the Billboard.cs script onto any object to add billboarding behavior and make the object always face you.</span></span> <span data-ttu-id="ac464-135">Pour ajouter un comportement avec balise, utilisez le script RadialView.cs.</span><span class="sxs-lookup"><span data-stu-id="ac464-135">To add tag-along behavior, use the RadialView.cs script.</span></span> <span data-ttu-id="ac464-136">Vous pouvez ajuster diverses options, telles que le temps de lerping, la distance et le degré.</span><span class="sxs-lookup"><span data-stu-id="ac464-136">You can adjust various options such as lerping time, distance, and degree.</span></span>

* [<span data-ttu-id="ac464-137">MRTK : solveur de vue radiale</span><span class="sxs-lookup"><span data-stu-id="ac464-137">MRTK - Radial View Solver</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html#radialview)
* [<span data-ttu-id="ac464-138">Script MRTK-Billboard</span><span class="sxs-lookup"><span data-stu-id="ac464-138">MRTK - Billboard script</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


<br>

---

## <a name="see-also"></a><span data-ttu-id="ac464-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac464-139">See also</span></span>

* [<span data-ttu-id="ac464-140">Curseurs</span><span class="sxs-lookup"><span data-stu-id="ac464-140">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="ac464-141">Rayon émanant de la main</span><span class="sxs-lookup"><span data-stu-id="ac464-141">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="ac464-142">Button</span><span class="sxs-lookup"><span data-stu-id="ac464-142">Button</span></span>](button.md)
* [<span data-ttu-id="ac464-143">Objet avec interaction possible</span><span class="sxs-lookup"><span data-stu-id="ac464-143">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="ac464-144">Rectangle englobant et barre de l’application</span><span class="sxs-lookup"><span data-stu-id="ac464-144">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="ac464-145">Manipulation</span><span class="sxs-lookup"><span data-stu-id="ac464-145">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="ac464-146">Menu de la main</span><span class="sxs-lookup"><span data-stu-id="ac464-146">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="ac464-147">Menu proche</span><span class="sxs-lookup"><span data-stu-id="ac464-147">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="ac464-148">Collection d’objets</span><span class="sxs-lookup"><span data-stu-id="ac464-148">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="ac464-149">Commande vocale</span><span class="sxs-lookup"><span data-stu-id="ac464-149">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="ac464-150">Clavier</span><span class="sxs-lookup"><span data-stu-id="ac464-150">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="ac464-151">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="ac464-151">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="ac464-152">Tablette</span><span class="sxs-lookup"><span data-stu-id="ac464-152">Slate</span></span>](slate.md)
* [<span data-ttu-id="ac464-153">Curseur</span><span class="sxs-lookup"><span data-stu-id="ac464-153">Slider</span></span>](slider.md)
* [<span data-ttu-id="ac464-154">Nuanceur</span><span class="sxs-lookup"><span data-stu-id="ac464-154">Shader</span></span>](shader.md)
* [<span data-ttu-id="ac464-155">Billboarding et tag-along</span><span class="sxs-lookup"><span data-stu-id="ac464-155">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="ac464-156">Affichage de la progression</span><span class="sxs-lookup"><span data-stu-id="ac464-156">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="ac464-157">Aimantation de surface</span><span class="sxs-lookup"><span data-stu-id="ac464-157">Surface magnetism</span></span>](surface-magnetism.md)
