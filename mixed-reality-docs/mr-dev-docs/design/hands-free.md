---
title: Mains libres
description: En savoir plus sur les difficultés auxquelles les utilisateurs peuvent être confrontés avec une interface mains-et-contrôleurs et sur les différentes alternatives mains libres.
author: hferrone
ms.author: v-hferrone
ms.date: 04/20/2019
ms.topic: article
keywords: En réalité mixte, mains libres, point de présence, regards, interaction, conception, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, HoloLens, MRTK, kit de fonctionnalités de réalité mixte, entrée vocale, convivialité
ms.openlocfilehash: 2864e58fdd8a29ae8f981b42f50735eb13a50869
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847682"
---
# <a name="hands-free"></a><span data-ttu-id="f9383-104">Mains libres</span><span class="sxs-lookup"><span data-stu-id="f9383-104">Hands-free</span></span>

## <a name="scenarios"></a><span data-ttu-id="f9383-105">Scénarios</span><span class="sxs-lookup"><span data-stu-id="f9383-105">Scenarios</span></span>

<span data-ttu-id="f9383-106">Comme indiqué dans la [vue d’ensemble du modèle d’interaction](interaction-fundamentals.md), une fois que vous avez identifié vos utilisateurs et leurs objectifs, posez-vous les questions environnementales ou de situation auxquelles ils peuvent être confrontés lorsqu’ils travaillent pour accomplir leurs tâches.</span><span class="sxs-lookup"><span data-stu-id="f9383-106">As outlined in the [interaction model overview](interaction-fundamentals.md), once you've identified your users and their goals, ask yourself what environmental or situational challenges they might face as they work to accomplish their tasks.</span></span> <span data-ttu-id="f9383-107">Par exemple, de nombreux utilisateurs ont besoin d’utiliser leurs mains pour atteindre leurs objectifs réels, et ils auront des difficultés à interagir avec une interface de type mains et contrôleurs.</span><span class="sxs-lookup"><span data-stu-id="f9383-107">For example, many users need to use their hands to accomplish their real-world goals, and they'll have difficulty interacting with a hands-and-controllers based interface.</span></span>

<span data-ttu-id="f9383-108">Voici quelques scénarios spécifiques :</span><span class="sxs-lookup"><span data-stu-id="f9383-108">Some specific scenarios include:</span></span> 
* <span data-ttu-id="f9383-109">Guidage pour effectuer une tâche, pendant que les mains de l’utilisateur sont occupées</span><span class="sxs-lookup"><span data-stu-id="f9383-109">Being guided through a task, while the user's hands are busy</span></span>
* <span data-ttu-id="f9383-110">Référencement de matériaux lorsque les mains de l’utilisateur sont occupées</span><span class="sxs-lookup"><span data-stu-id="f9383-110">Referencing materials while the user's hands are busy</span></span>
* <span data-ttu-id="f9383-111">Fatigue de la main</span><span class="sxs-lookup"><span data-stu-id="f9383-111">Hand fatigue</span></span>
* <span data-ttu-id="f9383-112">Gants qui ne peuvent pas être suivis</span><span class="sxs-lookup"><span data-stu-id="f9383-112">Gloves that can't be tracked</span></span>
* <span data-ttu-id="f9383-113">Transport d’objet avec les mains</span><span class="sxs-lookup"><span data-stu-id="f9383-113">Carrying something in their hands</span></span>
* <span data-ttu-id="f9383-114">Maladroite sociale lors de l’utilisation de grands mouvements de main</span><span class="sxs-lookup"><span data-stu-id="f9383-114">Social awkwardness when using large hand gestures</span></span>
* <span data-ttu-id="f9383-115">Espaces étroits</span><span class="sxs-lookup"><span data-stu-id="f9383-115">Tight spaces</span></span>

## <a name="hands-free-modalities"></a><span data-ttu-id="f9383-116">Modalités des mains libres</span><span class="sxs-lookup"><span data-stu-id="f9383-116">Hands-free modalities</span></span>

### <a name="voice-input"></a>[<span data-ttu-id="f9383-117">Entrée vocale</span><span class="sxs-lookup"><span data-stu-id="f9383-117">Voice input</span></span>](voice-input.md)

<span data-ttu-id="f9383-118">L’utilisation de votre voix pour commande et contrôle d’une interface offre un moyen pratique de travailler sans mains et d’utiliser des raccourcis pour ignorer plusieurs étapes si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="f9383-118">Using your voice to command and control an interface offers a convenient way to operate hands-free and to use shortcuts to skip multiple steps if you want.</span></span> <span data-ttu-id="f9383-119">Avec les entrées vocales, l’utilisateur peut lire le nom du bouton à haute voix pour l’activer _(le voir, le prononcer)_ et communiquer avec un agent numérique qui peut accomplir des tâches pour vous.</span><span class="sxs-lookup"><span data-stu-id="f9383-119">With voice input, the user can read any button's name out loud to activate it _("see it, say it")_ and converse with a digital agent who can accomplish tasks for you.</span></span>

### <a name="gaze-and-dwell"></a>[<span data-ttu-id="f9383-120">Pointer du regard et fixer</span><span class="sxs-lookup"><span data-stu-id="f9383-120">Gaze and dwell</span></span>](gaze-and-dwell.md)

<span data-ttu-id="f9383-121">Dans certaines situations mains libres, l’utilisation de votre voix n’est pas idéale, voire possible.</span><span class="sxs-lookup"><span data-stu-id="f9383-121">In some hands-free situations, using your voice isn't ideal or even possible.</span></span> <span data-ttu-id="f9383-122">Les environnements en usine bruyants, la confidentialité ou les normes sociales peuvent être des contraintes.</span><span class="sxs-lookup"><span data-stu-id="f9383-122">Loud factory environments, privacy, or social norms can all be constraints.</span></span> <span data-ttu-id="f9383-123">Le modèle de point de vue de l’utilisateur permet à l’utilisateur de naviguer dans une application sans aucune entrée supplémentaire, en dehors de son oeil ou de son point de vue : l’utilisateur garde tout simplement Gazing (avec son en-tête ou ses yeux) à la cible et attend un moment pour l’activer.</span><span class="sxs-lookup"><span data-stu-id="f9383-123">The gaze + dwell model allows the user to navigate an app without any extra input aside from their eye or head gaze: The user simply keeps gazing (with their head or eyes) at the target and lingers there for a moment to activate it.</span></span> <span data-ttu-id="f9383-124">Pour en savoir plus sur les considérations de conception individuelles pour le point de vue et le point de vue, consultez la section [œil-point](gaze-and-dwell-eyes.md) de vue et [tête](gaze-and-dwell-head.md)de regard.</span><span class="sxs-lookup"><span data-stu-id="f9383-124">To learn more about the individual design considerations for gaze + dwell, check out [eye-gaze + dwell](gaze-and-dwell-eyes.md) and [head-gaze + dwell](gaze-and-dwell-head.md).</span></span>

## <a name="transitioning-in-and-out-of-hands-free"></a><span data-ttu-id="f9383-125">Transition vers et à l’extérieur des mains libres</span><span class="sxs-lookup"><span data-stu-id="f9383-125">Transitioning in and out of hands-free</span></span>

<span data-ttu-id="f9383-126">Pour ces scénarios, le fait de libérer des mains de l’interaction avec les hologrammes pour l’exécution de commandes et la navigation peut aller de l’exigence absolue à l’exploitation de l’application, de bout en bout, à un confort supplémentaire que l’utilisateur peut passer à tout moment.</span><span class="sxs-lookup"><span data-stu-id="f9383-126">For these scenarios, freeing your hands from interacting with holograms for commanding and navigation can range from being an absolute requirement to operating the application, end-to-end, to an added convenience that the user can transition in and out of at any time.</span></span> 

<span data-ttu-id="f9383-127">Si l’application exige qu’elle soit toujours utilisée sans intervention, que ce soit à l’aide de son, de commandes vocales personnalisées ou de la commande vocale unique, « Select », veillez à effectuer les logements appropriés dans votre interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f9383-127">If the application requires that it will always be used hands-free, whether by using dwell, custom voice commands, or the single voice command, "select", then make sure to make the appropriate accommodations in your UI.</span></span> 

<span data-ttu-id="f9383-128">Si votre utilisateur cible doit passer des mains à la mains libres à sa discrétion, il est important de prendre en compte les principes suivants.</span><span class="sxs-lookup"><span data-stu-id="f9383-128">If your target user needs to switch from hands to hands-free at their discretion, then it's important to take the following principles into account.</span></span>

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a><span data-ttu-id="f9383-129">Supposons que l’utilisateur est déjà dans le mode vers lequel il souhaite passer</span><span class="sxs-lookup"><span data-stu-id="f9383-129">Assume the user is already in the mode that they want to switch to</span></span>
<span data-ttu-id="f9383-130">Par exemple, si l’utilisateur se trouve en usine, regarde une référence vidéo sur son HoloLens et décide de sélectionner une clé pour commencer à travailler, elle commence probablement à travailler sans avoir à appuyer sur un bouton pour commencer à travailler.</span><span class="sxs-lookup"><span data-stu-id="f9383-130">For instance, if the user is on the factory floor, watching a video reference on her HoloLens, and decides to pick up a wrench to start working, she most likely would start working in hands-free without having to put down the wrench to press a button.</span></span> <span data-ttu-id="f9383-131">Elle peut appeler une session vocale à l’aide d’une commande vocale, son logement sur une interface utilisateur déjà visible pour commencer son logement, ou prononcer le mot « Select » (sélectionner).</span><span class="sxs-lookup"><span data-stu-id="f9383-131">She can invoke a voice session with a voice command, dwell on an already-visible UI to begin dwell, or say the word "select".</span></span>

<span data-ttu-id="f9383-132">L’utilisateur peut :</span><span class="sxs-lookup"><span data-stu-id="f9383-132">The user can:</span></span> 
* <span data-ttu-id="f9383-133">Passez à l’option mains libres pendant les mains libres</span><span class="sxs-lookup"><span data-stu-id="f9383-133">Switch to hands-free while hands-free</span></span>
* <span data-ttu-id="f9383-134">Passez aux mains avec vos mains</span><span class="sxs-lookup"><span data-stu-id="f9383-134">Switch to hands with your hands</span></span>
* <span data-ttu-id="f9383-135">Basculer vers le contrôleur à l’aide d’un contrôleur</span><span class="sxs-lookup"><span data-stu-id="f9383-135">Switch to the controller using a controller</span></span> 

### <a name="create-redundant-ways-to-switch-modes"></a><span data-ttu-id="f9383-136">Créer des méthodes redondantes pour basculer entre les modes</span><span class="sxs-lookup"><span data-stu-id="f9383-136">Create redundant ways to switch modes</span></span>

<span data-ttu-id="f9383-137">Tandis que le premier principe concerne l’accès, la seconde concerne la disponibilité.</span><span class="sxs-lookup"><span data-stu-id="f9383-137">While the first principle is about access, the second one is about availability.</span></span> <span data-ttu-id="f9383-138">Il ne s’agit pas d’un moyen unique de passer d’un mode à un autre.</span><span class="sxs-lookup"><span data-stu-id="f9383-138">There shouldn't just be a single way to transition in and out of a mode.</span></span> 

<span data-ttu-id="f9383-139">Voici quelques exemples :</span><span class="sxs-lookup"><span data-stu-id="f9383-139">Some examples would be:</span></span> 
* <span data-ttu-id="f9383-140">Un bouton pour commencer les interactions vocales</span><span class="sxs-lookup"><span data-stu-id="f9383-140">A button to begin voice interactions</span></span>
* <span data-ttu-id="f9383-141">Commande vocale à utiliser pour la transition, en utilisant le point d’interposition</span><span class="sxs-lookup"><span data-stu-id="f9383-141">A voice command to transition to, using head-gaze and dwell</span></span>

### <a name="add-a-dash-of-drama"></a><span data-ttu-id="f9383-142">Ajouter un tiret de la fiction</span><span class="sxs-lookup"><span data-stu-id="f9383-142">Add a dash of drama</span></span>

<span data-ttu-id="f9383-143">Un changement de mode est une affaire importante.</span><span class="sxs-lookup"><span data-stu-id="f9383-143">A mode switch is a big deal.</span></span> <span data-ttu-id="f9383-144">Il est important que lorsque ces transitions se produisent, il s’agit d’un commutateur explicite, même d’un commutateur spectaculaire, pour permettre à l’utilisateur de savoir ce qui s’est passé.</span><span class="sxs-lookup"><span data-stu-id="f9383-144">It's important that when these transitions happen that they be an explicit, even a dramatic switch, to let the user know what happened.</span></span> 

## <a name="usability-checklist"></a><span data-ttu-id="f9383-145">Liste de vérification de l’utilisation</span><span class="sxs-lookup"><span data-stu-id="f9383-145">Usability checklist</span></span>

<span data-ttu-id="f9383-146">**L’utilisateur peut-il faire tout et tout ce qui est mains libres, de bout en bout ?**</span><span class="sxs-lookup"><span data-stu-id="f9383-146">**Can the user do everything and anything hands-free, end-to-end?**</span></span>
* <span data-ttu-id="f9383-147">Chaque interaction peut être accessible mains libres</span><span class="sxs-lookup"><span data-stu-id="f9383-147">Every interactable should be accessible hands-free</span></span>
* <span data-ttu-id="f9383-148">Assurez-vous qu’il existe un remplacement de tous les mouvements personnalisés, tels que le redimensionnement, le placement, les balayages, les robinets, etc.</span><span class="sxs-lookup"><span data-stu-id="f9383-148">Ensure that there's a replacement for all custom gestures, such as resizing, placing, swipes, taps, and so on.</span></span>
* <span data-ttu-id="f9383-149">Veillez à ce que l’utilisateur ait toujours le contrôle de la présence, de l’emplacement et des commentaires de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f9383-149">Ensure that the user has confident control of UI presence, placement, and verbosity always</span></span>
    * <span data-ttu-id="f9383-150">Récupération de l’interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="f9383-150">Getting UI out of the way</span></span>
    * <span data-ttu-id="f9383-151">Adressage de l’interface utilisateur en dehors de l’affichage (angle de vue)</span><span class="sxs-lookup"><span data-stu-id="f9383-151">Addressing UI that is out of field of view (FOV)</span></span>
    * <span data-ttu-id="f9383-152">Combien je vois, où, quand</span><span class="sxs-lookup"><span data-stu-id="f9383-152">How much I see, where, when</span></span>

<span data-ttu-id="f9383-153">**Les mécanismes de l’interaction sont-ils enseignés et armés avec le bon intuitivité ?**</span><span class="sxs-lookup"><span data-stu-id="f9383-153">**Are the mechanics of the interaction being taught and reinforced with the right affordances?**</span></span>

<span data-ttu-id="f9383-154">L’utilisateur a-t-il compris...</span><span class="sxs-lookup"><span data-stu-id="f9383-154">Does the user understand ...</span></span>
* <span data-ttu-id="f9383-155">... Dans quel mode ils se trouvent-ils ?</span><span class="sxs-lookup"><span data-stu-id="f9383-155">... What mode they are in?</span></span>
* <span data-ttu-id="f9383-156">... Qu’est-ce qu’il est possible de faire dans ce mode ?</span><span class="sxs-lookup"><span data-stu-id="f9383-156">... What they can do in this mode?</span></span>
* <span data-ttu-id="f9383-157">... Quel est l’état actuel ?</span><span class="sxs-lookup"><span data-stu-id="f9383-157">... What is the current state?</span></span>
* <span data-ttu-id="f9383-158">... Comment elles peuvent être transférées ?</span><span class="sxs-lookup"><span data-stu-id="f9383-158">... How they can transition out?</span></span>
    
<span data-ttu-id="f9383-159">**L’interface utilisateur est-elle optimisée pour les mains libres ?**</span><span class="sxs-lookup"><span data-stu-id="f9383-159">**Is the UI optimized for hands-free?**</span></span>   

* <span data-ttu-id="f9383-160">Exemple : les intuitivité de logement ne sont pas intégrés aux modèles 2D typiques</span><span class="sxs-lookup"><span data-stu-id="f9383-160">Example: Dwell affordances aren't built in to typical 2D patterns</span></span>
* <span data-ttu-id="f9383-161">Exemple : le ciblage vocal est mieux adapté à la mise en surbrillance des objets</span><span class="sxs-lookup"><span data-stu-id="f9383-161">Example: Voice targeting is better with object highlighting</span></span>
* <span data-ttu-id="f9383-162">Exemple : les interactions vocales sont meilleures avec les légendes qui doivent être activées</span><span class="sxs-lookup"><span data-stu-id="f9383-162">Example: Voice interactions are better with captions that need to be turned on</span></span>

## <a name="see-also"></a><span data-ttu-id="f9383-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9383-163">See also</span></span>

* [<span data-ttu-id="f9383-164">Suivi oculaire sur HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="f9383-164">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="f9383-165">Pointer et valider</span><span class="sxs-lookup"><span data-stu-id="f9383-165">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="f9383-166">Pointer du regard et fixer</span><span class="sxs-lookup"><span data-stu-id="f9383-166">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="f9383-167">Mains : Manipulation directe</span><span class="sxs-lookup"><span data-stu-id="f9383-167">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="f9383-168">Mains : Mouvements</span><span class="sxs-lookup"><span data-stu-id="f9383-168">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="f9383-169">Mains : Pointer et valider</span><span class="sxs-lookup"><span data-stu-id="f9383-169">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="f9383-170">Interactions instinctuelles</span><span class="sxs-lookup"><span data-stu-id="f9383-170">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="f9383-171">Entrée vocale</span><span class="sxs-lookup"><span data-stu-id="f9383-171">Voice input</span></span>](voice-input.md)
