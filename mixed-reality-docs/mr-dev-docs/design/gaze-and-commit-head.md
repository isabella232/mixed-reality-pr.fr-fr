---
title: Suivre de la tête et valider
description: Vue d’ensemble du modèle d’entrée de pointage en tête et de validation.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: La réalité mixte, le point de présence, le regard, l’interaction, la conception, le casque de la réalité mixte, le casque Windows Mixed Reality, le casque de la réalité virtuelle, HoloLens, MRTK, le kit de configuration de la réalité mixte, la cible, le lissage
ms.openlocfilehash: cc12c349704a63c5b95c9eede91d0486f56787a2
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847882"
---
# <a name="head-gaze-and-commit"></a><span data-ttu-id="d2e06-104">Suivre de la tête et valider</span><span class="sxs-lookup"><span data-stu-id="d2e06-104">Head-gaze and commit</span></span>

<span data-ttu-id="d2e06-105">Le _point de regard et la validation de tête_ est un cas particulier du modèle d’entrée de pointage et de [validation](gaze-and-commit.md) qui implique le ciblage d’un objet avec une direction de la tête des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="d2e06-105">_Head-gaze and commit_ is a special case of the [gaze and commit](gaze-and-commit.md) input model that involves targeting an object with a users head direction.</span></span> <span data-ttu-id="d2e06-106">Vous pouvez agir sur la cible à l’aide d’une entrée secondaire, telle que la commande vocale TAP ou Select de mouvement direct.</span><span class="sxs-lookup"><span data-stu-id="d2e06-106">You can act on the target with a secondary input, such as the hand gesture air tap or "Select" voice command.</span></span> 

## <a name="device-support"></a><span data-ttu-id="d2e06-107">Prise en charge des appareils</span><span class="sxs-lookup"><span data-stu-id="d2e06-107">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d2e06-108"><strong>Modèle d’entrée</strong></span><span class="sxs-lookup"><span data-stu-id="d2e06-108"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="d2e06-109"><a href="../hololens-hardware-details.md"><strong>HoloLens (1ère génération)</strong></a></span><span class="sxs-lookup"><span data-stu-id="d2e06-109"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="d2e06-110"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="d2e06-110"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="d2e06-111"><a href="../discover/immersive-headset-hardware-details.md"><strong>Casques immersifs</strong></a></span><span class="sxs-lookup"><span data-stu-id="d2e06-111"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d2e06-112">Suivre de la tête et valider</span><span class="sxs-lookup"><span data-stu-id="d2e06-112">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="d2e06-113">✔️ Recommandé</span><span class="sxs-lookup"><span data-stu-id="d2e06-113">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="d2e06-114">✔️ Recommandé (troisième choix ; <a href="interaction-fundamentals.md">voir les autres options</a>)</span><span class="sxs-lookup"><span data-stu-id="d2e06-114">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="d2e06-115">➕ Autre option</span><span class="sxs-lookup"><span data-stu-id="d2e06-115">➕ Alternate option</span></span></td>
    </tr>
</table>

---

## <a name="target-sizing-and-feedback"></a><span data-ttu-id="d2e06-116">Dimensionnement des cibles et retour</span><span class="sxs-lookup"><span data-stu-id="d2e06-116">Target sizing and feedback</span></span>

<span data-ttu-id="d2e06-117">Le point de regard de l’en-tête a été affiché à plusieurs reprises pour être utilisable pour un ciblage précis, mais il fonctionne souvent mieux pour le ciblage brut, en acquérant des cibles plus volumineuses.</span><span class="sxs-lookup"><span data-stu-id="d2e06-117">The head gaze vector has been shown repeatedly to be usable for fine targeting, but often works best for gross targeting--acquiring larger targets.</span></span> <span data-ttu-id="d2e06-118">Les tailles cibles minimales de 1 degré à 1,5 degrés permettent des actions utilisateur réussies dans la plupart des scénarios, bien que les cibles de 3 degrés offrent souvent une vitesse supérieure.</span><span class="sxs-lookup"><span data-stu-id="d2e06-118">Minimum target sizes of 1 degree to 1.5 degrees allow successful user actions in most scenarios, though targets of 3 degrees often allow for greater speed.</span></span> <span data-ttu-id="d2e06-119">La taille ciblée par l’utilisateur est en fait une zone 2D, même pour les éléments 3D, quelle que soit la projection vers laquelle elle doit être la zone cible.</span><span class="sxs-lookup"><span data-stu-id="d2e06-119">The size that the user targets is effectively a 2D area even for 3D elements--whichever projection is facing them should be the targetable area.</span></span> <span data-ttu-id="d2e06-120">Il est utile de fournir une indication intéressante indiquant qu’un élément est « actif » (que l’utilisateur cible).</span><span class="sxs-lookup"><span data-stu-id="d2e06-120">Providing some salient cue that an element is "active" (that the user is targeting it) is helpful.</span></span> <span data-ttu-id="d2e06-121">Cela peut inclure des traitements tels que des effets de « survol » visibles, des surbrillances audio ou des clics, ou l’alignement clair d’un curseur avec un élément.</span><span class="sxs-lookup"><span data-stu-id="d2e06-121">This can include treatments like visible "hover" effects, audio highlights or clicks, or clear alignment of a cursor with an element.</span></span>

<span data-ttu-id="d2e06-122">![Taille optimale de la cible à une distance de 2 mètres](images/gazetargeting-size-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="d2e06-122">![Optimal target size at 2 meter distance](images/gazetargeting-size-1000px.jpg)</span></span><br>
<span data-ttu-id="d2e06-123">*Taille de cible optimale à une distance de 2 mètres*</span><span class="sxs-lookup"><span data-stu-id="d2e06-123">*Optimal target size at 2-meter distance*</span></span>

<br>

<span data-ttu-id="d2e06-124">![Exemple de mise en surbrillance d’un objet ciblé avec le regard](images/gazetargeting-highlighting-940px.jpg)</span><span class="sxs-lookup"><span data-stu-id="d2e06-124">![An example of highlighting a gaze targeted object](images/gazetargeting-highlighting-940px.jpg)</span></span><br>
<span data-ttu-id="d2e06-125">*Exemple de mise en surbrillance d’un objet ciblé avec le regard*</span><span class="sxs-lookup"><span data-stu-id="d2e06-125">*An example of highlighting a gaze targeted object*</span></span>

## <a name="target-placement"></a><span data-ttu-id="d2e06-126">Placement de la cible</span><span class="sxs-lookup"><span data-stu-id="d2e06-126">Target placement</span></span>

<span data-ttu-id="d2e06-127">Souvent, les utilisateurs ne parviennent pas à trouver les éléments d’interface utilisateur situés trop hauts ou faibles dans leur champ d’affichage.</span><span class="sxs-lookup"><span data-stu-id="d2e06-127">Users often fail to find UI elements located either too high or low in their field of view.</span></span> <span data-ttu-id="d2e06-128">La plus grande partie de leur attention se termine sur des points autour de leur objectif principal, ce qui est approximativement au niveau oculaire.</span><span class="sxs-lookup"><span data-stu-id="d2e06-128">Most of their attention ends up on areas around their main focus, which is approximately at eye level.</span></span> <span data-ttu-id="d2e06-129">Le fait de placer la plupart des cibles dans une bande raisonnable autour des yeux peut s’avérer utile.</span><span class="sxs-lookup"><span data-stu-id="d2e06-129">Placing most targets in some reasonable band around eye level can help.</span></span> <span data-ttu-id="d2e06-130">Étant donné la tendance pour les utilisateurs à se concentrer sur une petite zone visuelle à tout moment (le cône de vision est à peu près 10 degrés), le regroupement des éléments de l’interface utilisateur en fonction de leur degré de lien peut utiliser les comportements de chaînage de l’élément jusqu’à l’élément lorsqu’un utilisateur déplace le regard sur une zone.</span><span class="sxs-lookup"><span data-stu-id="d2e06-130">Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree they're related conceptually can use attention-chaining behaviors from item to item as a user moves their gaze through an area.</span></span> <span data-ttu-id="d2e06-131">Quand vous concevez l’interface utilisateur, gardez à l’esprit les grandes variations potentielles du champ de vision entre les casques immersifs et HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d2e06-131">When designing UI, keep in mind the potential large variation in field of view between HoloLens and immersive headsets.</span></span>

<span data-ttu-id="d2e06-132">![Exemple d’éléments d’interface utilisateur groupés pour faciliter le ciblage avec le regard dans Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="d2e06-132">![An example of grouped UI elements for easier gaze targeting in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span></span><br>
<span data-ttu-id="d2e06-133">*Exemple d’éléments d’interface utilisateur groupés pour faciliter le ciblage avec le regard dans Galaxy Explorer*</span><span class="sxs-lookup"><span data-stu-id="d2e06-133">*An example of grouped UI elements for easier gaze targeting in Galaxy Explorer*</span></span>

## <a name="improving-targeting-behaviors"></a><span data-ttu-id="d2e06-134">Amélioration des comportements de ciblage</span><span class="sxs-lookup"><span data-stu-id="d2e06-134">Improving targeting behaviors</span></span>

<span data-ttu-id="d2e06-135">Si l’intention de l’utilisateur de cibler un événement peut être déterminée ou rapprochée, il peut être utile d’accepter les tentatives d’interaction presque manquées comme si elles étaient ciblées correctement.</span><span class="sxs-lookup"><span data-stu-id="d2e06-135">If user intent to target something can be determined or closely approximated, it can be helpful to accept near miss interaction attempts as though they were targeted correctly.</span></span> <span data-ttu-id="d2e06-136">Voici quelques-unes des méthodes qui peuvent être incorporées dans les expériences de réalité mixte :</span><span class="sxs-lookup"><span data-stu-id="d2e06-136">Here's a handful of successful methods that can be incorporated in mixed reality experiences:</span></span>

### <a name="head-gaze-stabilization-gravity-wells"></a><span data-ttu-id="d2e06-137">Stabilisation avec suivi de la tête (« stabilisation de la gravité »)</span><span class="sxs-lookup"><span data-stu-id="d2e06-137">Head-gaze stabilization ("gravity wells")</span></span>

<span data-ttu-id="d2e06-138">Cette fonction doit être activée le plus ou la totalité du temps.</span><span class="sxs-lookup"><span data-stu-id="d2e06-138">This should be turned on most or all of the time.</span></span> <span data-ttu-id="d2e06-139">Cette technique supprime les instabilités de tête et de cou naturelles que les utilisateurs peuvent avoir en mouvement en raison des comportements de recherche et de dictée.</span><span class="sxs-lookup"><span data-stu-id="d2e06-139">This technique removes the natural head and neck jitters that users might have as well movement because of looking and speaking behaviors.</span></span>

### <a name="closest-link-algorithms"></a><span data-ttu-id="d2e06-140">Algorithmes du lien le plus proche</span><span class="sxs-lookup"><span data-stu-id="d2e06-140">Closest link algorithms</span></span>

<span data-ttu-id="d2e06-141">Ces algorithmes fonctionnent mieux dans des domaines avec du contenu interactif fragmenté.</span><span class="sxs-lookup"><span data-stu-id="d2e06-141">These algorithms work best in areas with sparse interactive content.</span></span> <span data-ttu-id="d2e06-142">S’il y a une forte probabilité que vous puissiez déterminer ce à quoi un utilisateur tente d’interagir, vous pouvez compléter ses capacités de ciblage en supposant un certain niveau d’intention.</span><span class="sxs-lookup"><span data-stu-id="d2e06-142">If there's a high probability that you can determine what a user was attempting to interact with, you can supplement their targeting abilities by assuming some level of intent.</span></span>

### <a name="backdating-and-postdating-actions"></a><span data-ttu-id="d2e06-143">Actions d’postdating et de mise à jour</span><span class="sxs-lookup"><span data-stu-id="d2e06-143">Backdating and postdating actions</span></span>

<span data-ttu-id="d2e06-144">Ce mécanisme est utile dans les tâches nécessitant de la vitesse.</span><span class="sxs-lookup"><span data-stu-id="d2e06-144">This mechanism is useful in tasks requiring speed.</span></span> <span data-ttu-id="d2e06-145">Lorsqu’un utilisateur parcourt une série de manoeuvres de ciblage et d’activation à la vitesse, il est utile de supposer une certaine intention.</span><span class="sxs-lookup"><span data-stu-id="d2e06-145">When a user is moving through a series of targeting and activation maneuvers at speed, it's useful to assume some intent.</span></span> <span data-ttu-id="d2e06-146">Il est également utile d’autoriser les étapes manquées à agir sur les cibles dont l’utilisateur avait le focus légèrement avant ou légèrement après le TAP (50 ms avant/après).</span><span class="sxs-lookup"><span data-stu-id="d2e06-146">It's also useful to allow missed steps to act on targets that the user had in focus slightly before or slightly after the tap (50 ms before/after was effective in early testing).</span></span>

### <a name="smoothing"></a><span data-ttu-id="d2e06-147">Adoucissage</span><span class="sxs-lookup"><span data-stu-id="d2e06-147">Smoothing</span></span>

<span data-ttu-id="d2e06-148">Ce mécanisme est utile pour le tracé des mouvements, en réduisant les légères gigues et les tremblements en raison des caractéristiques naturelles de mouvement de la tête.</span><span class="sxs-lookup"><span data-stu-id="d2e06-148">This mechanism is useful for pathing movements, reducing the slight jitter and wobbles because of natural head movement characteristics.</span></span> <span data-ttu-id="d2e06-149">En cas de lissage sur les mouvements de tracés, lisse par la taille et la distance des mouvements plutôt qu’au fil du temps.</span><span class="sxs-lookup"><span data-stu-id="d2e06-149">When smoothing over pathing motions, smooth by the size and distance of movements rather than over time.</span></span>

### <a name="magnetism"></a><span data-ttu-id="d2e06-150">Magnétisme</span><span class="sxs-lookup"><span data-stu-id="d2e06-150">Magnetism</span></span>

<span data-ttu-id="d2e06-151">Ce mécanisme peut être considéré comme une version plus générale des algorithmes de lien les plus proches : le fait de dessiner un curseur vers une cible ou d’augmenter simplement hitboxes, de façon visible ou non, à mesure que les utilisateurs approchent les cibles probables à l’aide d’une connaissance de la disposition interactive pour une meilleure approche de l’intention de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d2e06-151">This mechanism can be thought of as a more general version of closest link algorithms--drawing a cursor toward a target or simply increasing hitboxes, whether visibly or not, as users approach likely targets by using some knowledge of the interactive layout to better approach user intent.</span></span> <span data-ttu-id="d2e06-152">Cela peut être puissant pour les petites cibles.</span><span class="sxs-lookup"><span data-stu-id="d2e06-152">This can be powerful for small targets.</span></span>

### <a name="focus-stickiness"></a><span data-ttu-id="d2e06-153">Adhérence du focus</span><span class="sxs-lookup"><span data-stu-id="d2e06-153">Focus stickiness</span></span>

<span data-ttu-id="d2e06-154">Lors de la détermination des éléments interactifs proches à donner, le focus sur, l’adhérence au focus fournit un décalage à l’élément qui est actuellement concentré.</span><span class="sxs-lookup"><span data-stu-id="d2e06-154">When determining which nearby interactive elements to give,  focus to, focus stickiness provides a bias to the element that is currently focused.</span></span> <span data-ttu-id="d2e06-155">Cela permet de réduire les comportements de changement de focus erratiques lorsqu’ils flottent à un point médian entre deux éléments avec un bruit naturel.</span><span class="sxs-lookup"><span data-stu-id="d2e06-155">This helps reduce erratic focus switching behaviors when floating at a midpoint between two elements with natural noise.</span></span>

## <a name="see-also"></a><span data-ttu-id="d2e06-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2e06-156">See also</span></span>

* [<span data-ttu-id="d2e06-157">Interaction basée sur le regard</span><span class="sxs-lookup"><span data-stu-id="d2e06-157">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="d2e06-158">Pointer du regard et fixer</span><span class="sxs-lookup"><span data-stu-id="d2e06-158">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="d2e06-159">Mains : Manipulation directe</span><span class="sxs-lookup"><span data-stu-id="d2e06-159">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="d2e06-160">Mains : Mouvements</span><span class="sxs-lookup"><span data-stu-id="d2e06-160">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="d2e06-161">Mains : Pointer et valider</span><span class="sxs-lookup"><span data-stu-id="d2e06-161">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="d2e06-162">Interactions instinctuelles</span><span class="sxs-lookup"><span data-stu-id="d2e06-162">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="d2e06-163">Entrée vocale</span><span class="sxs-lookup"><span data-stu-id="d2e06-163">Voice input</span></span>](voice-input.md)



