---
title: Suivre de la tête et stabiliser
description: Vue d’ensemble du modèle d’entrée Suivre de la tête et stabiliser
author: hferrone
ms.author: v-hferrone
ms.date: 05/13/2019
ms.topic: article
keywords: La réalité mixte, le point de vue, l’interaction, la conception, le casque de la réalité mixte, le casque Windows Mixed Reality, le casque de la réalité virtuelle, HoloLens, MRTK, le kit de conditions de la réalité mixte, l’expérience utilisateur, les instructions, le mode liste
ms.openlocfilehash: 060d78ec629905ac9f2134851998ec131d85f0cd
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847372"
---
# <a name="head-gaze-and-dwell"></a><span data-ttu-id="f80c0-104">Suivre de la tête et stabiliser</span><span class="sxs-lookup"><span data-stu-id="f80c0-104">Head-gaze and dwell</span></span>

<span data-ttu-id="f80c0-105">Quand les mains sont occupées avec des outils et des pièces, les mouvements peuvent être fastidieux, voire impossibles.</span><span class="sxs-lookup"><span data-stu-id="f80c0-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span> <span data-ttu-id="f80c0-106">Les commandes vocales, à l’image des mouvements, peuvent être incertaines dans des contextes donnés, par exemple dans des conditions très bruyantes.</span><span class="sxs-lookup"><span data-stu-id="f80c0-106">Voice commands, like gestures, can be unreliable in certain contexts, for example under excessively loud conditions.</span></span> <span data-ttu-id="f80c0-107">En outre, l’utilisation de la voix pour contrôler les ordinateurs n’est pas universellement courante, mais elle est certainement en train de s’intensifier !</span><span class="sxs-lookup"><span data-stu-id="f80c0-107">Additionally, using voice to control computers isn't universally common, but it certainly is gaining steam!</span></span> <span data-ttu-id="f80c0-108">Le modèle Suivre de la tête et stabiliser offre le mécanisme le plus familier et le plus facile à maîtriser pour travailler sur HoloLens tête relevée et mains libres.</span><span class="sxs-lookup"><span data-stu-id="f80c0-108">Head-gaze and dwell offers the most familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span> <span data-ttu-id="f80c0-109">De plus, ce modèle est fiable à 100 % ; il n’est pas sensible aux interférences sonores et ne demande pas le silence dans l’environnement.</span><span class="sxs-lookup"><span data-stu-id="f80c0-109">Additionally, head-gaze and dwell is 100% reliable independent of noise interference nor silence constraints in the operating environment.</span></span>

## <a name="scenarios"></a><span data-ttu-id="f80c0-110">Scénarios</span><span class="sxs-lookup"><span data-stu-id="f80c0-110">Scenarios</span></span>

<span data-ttu-id="f80c0-111">Le point de regard et le front-tête est parfait dans les scénarios où les mains d’une personne sont occupées par d’autres tâches.</span><span class="sxs-lookup"><span data-stu-id="f80c0-111">Head-gaze and dwell is great in scenarios where a person's hands are busy with other tasks.</span></span> <span data-ttu-id="f80c0-112">Cette fonctionnalité est également utile lorsque la voix n’est pas 100% fiable ou disponible en raison de contraintes environnementales ou sociales.</span><span class="sxs-lookup"><span data-stu-id="f80c0-112">The feature is also useful when voice isn't 100% reliable or available because of environmental or social constraints.</span></span> <span data-ttu-id="f80c0-113">Un bon exemple est une personne portant un appareil HoloLens pour superposer des informations de référence tout en réparant un moteur de voiture.</span><span class="sxs-lookup"><span data-stu-id="f80c0-113">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span> <span data-ttu-id="f80c0-114">Ses mains sont occupées par des outils ou supportent son corps quand elle se penche dans le compartiment du moteur.</span><span class="sxs-lookup"><span data-stu-id="f80c0-114">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span> <span data-ttu-id="f80c0-115">L’espace du garage est bruyant, les coups et bourdonnement constants des outils rendant difficile l’utilisation de commandes vocales.</span><span class="sxs-lookup"><span data-stu-id="f80c0-115">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span> <span data-ttu-id="f80c0-116">Le point de regard et l’arrière-plan permet à la personne utilisant HoloLens de parcourir en toute confiance son document de référence sans interrompre son flux de travail.</span><span class="sxs-lookup"><span data-stu-id="f80c0-116">Head-gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span> 

## <a name="device-support"></a><span data-ttu-id="f80c0-117">Prise en charge des appareils</span><span class="sxs-lookup"><span data-stu-id="f80c0-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f80c0-118"><strong>Modèle d’entrée</strong></span><span class="sxs-lookup"><span data-stu-id="f80c0-118"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="f80c0-119"><a href="../hololens-hardware-details.md"><strong>HoloLens (1ère génération)</strong></a></span><span class="sxs-lookup"><span data-stu-id="f80c0-119"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="f80c0-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="f80c0-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="f80c0-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>Casques immersifs</strong></a></span><span class="sxs-lookup"><span data-stu-id="f80c0-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f80c0-122">Suivre de la tête et stabiliser</span><span class="sxs-lookup"><span data-stu-id="f80c0-122">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="f80c0-123">✔️ Recommandé</span><span class="sxs-lookup"><span data-stu-id="f80c0-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="f80c0-124">✔️ Recommandé</span><span class="sxs-lookup"><span data-stu-id="f80c0-124">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="f80c0-125">✔️ Recommandé</span><span class="sxs-lookup"><span data-stu-id="f80c0-125">✔️ Recommended</span></span></td>
    </tr>
</table>


## <a name="design-principles"></a><span data-ttu-id="f80c0-126">Principes de conception</span><span class="sxs-lookup"><span data-stu-id="f80c0-126">Design principles</span></span>

<span data-ttu-id="f80c0-127">**Éviter le « pointage du regard comme une arme »**</span><span class="sxs-lookup"><span data-stu-id="f80c0-127">**Avoid "Gaze as a weapon"**</span></span>

<span data-ttu-id="f80c0-128">Pour être intuitif, le modèle Suivre de la tête et stabiliser nécessite un retour visuel, mais trop de retour peut engendrer de l’anxiété.</span><span class="sxs-lookup"><span data-stu-id="f80c0-128">Head-gaze and dwell requires visual feedback to be intuitive, but too much feedback can induce anxiety.</span></span> <span data-ttu-id="f80c0-129">Les commentaires doivent permettre à un utilisateur de savoir ce qu’il cible, mais pas de le sélectionner à son intention.</span><span class="sxs-lookup"><span data-stu-id="f80c0-129">The feedback should help a user know what they're targeting, but not autoselect it against their intent.</span></span> <span data-ttu-id="f80c0-130">Lors de la lecture de texte, d’icônes et d’étiquettes, vous devez fournir aux utilisateurs l’heure d’absorber les informations avant de les sélectionner.</span><span class="sxs-lookup"><span data-stu-id="f80c0-130">When reading text, icons, and labels, you need to provide users time to absorb the information before selecting.</span></span>
    
<span data-ttu-id="f80c0-131">**Rechercher la vitesse idéale**</span><span class="sxs-lookup"><span data-stu-id="f80c0-131">**Seek Goldilocks speed**</span></span>
    
<span data-ttu-id="f80c0-132">Les interactions avec stabilisation peuvent avoir différentes durées en fonction de l’impact de la navigation : les fonctions plus fréquemment utilisées bénéficient généralement de temps de remplissage plus rapides, tandis que les fonctions plus conséquentes peuvent bénéficier de temps de remplissage plus longs.</span><span class="sxs-lookup"><span data-stu-id="f80c0-132">Dwell interactions can have different timers based on impact of navigation - more frequently used functions will generally benefit from faster fill times, while more consequential functions may benefit from longer fill times.</span></span> <span data-ttu-id="f80c0-133">Quand vous utilisez un effet de remplissage pour afficher ces durées, les courbes d’animation de la couleur de remplissage peuvent engendrer un sentiment positif de temps de remplissage plus rapides.</span><span class="sxs-lookup"><span data-stu-id="f80c0-133">When using a fill-effect to show these timers, animation curves of the fill color can positively influence a feeling of faster fill times.</span></span> <span data-ttu-id="f80c0-134">Vous devez envisager de laisser à l’utilisateur la possibilité de choisir la vitesse de remplissage (rapide, moyenne, lente).</span><span class="sxs-lookup"><span data-stu-id="f80c0-134">Consideration should be taken to enable user decision from fast/medium/slow fill speed overrides.</span></span>
    
<span data-ttu-id="f80c0-135">**Éviter l’effet yo-yo**</span><span class="sxs-lookup"><span data-stu-id="f80c0-135">**Say no-no to yo-yo effect**</span></span>

<span data-ttu-id="f80c0-136">L’effet yo-yo est un modèle de déplacement de la tête qui se produit lorsque les contrôles placement du contenu et point-Orient/logement forcent les utilisateurs à effectuer des recherches à plusieurs reprises.</span><span class="sxs-lookup"><span data-stu-id="f80c0-136">The yo-yo effect is an uncomfortable head movement pattern that happens when the content placement and head-gaze/dwell controls forces people to look up and down repeatedly.</span></span> <span data-ttu-id="f80c0-137">Par exemple, un point de la liste avec le bouton de tête et de pointage en haut en bas de la liste donne une boucle de-regarde vers le bas, recherche les résultats, regarde jusqu’à l’arrière, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="f80c0-137">For example, a list nav with the head-gaze and dwell button at the bottom induces a loop of - look down to dwell, look up at results, look down to dwell, and so on.</span></span> <span data-ttu-id="f80c0-138">Le modèle résultant n’est pas à l’aise. nous vous recommandons donc de placer les contrôles de navigation dans un emplacement centralisé qui nécessite moins d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="f80c0-138">The resulting pattern is uncomfortable, so we recommend placing navigation controls in a centralized location that requires less back-and-forth.</span></span> <span data-ttu-id="f80c0-139">Le positionnement des boutons de logement en fonction de leurs effets devient important pour le confort.</span><span class="sxs-lookup"><span data-stu-id="f80c0-139">Placement of dwell buttons based on their effects becomes important for comfort.</span></span>
<span data-ttu-id="f80c0-140">s</span><span class="sxs-lookup"><span data-stu-id="f80c0-140">s</span></span>
<br>

---

## <a name="ux-guidelines-and-best-practices"></a><span data-ttu-id="f80c0-141">Recommandations et bonnes pratiques pour l’expérience utilisateur</span><span class="sxs-lookup"><span data-stu-id="f80c0-141">UX Guidelines and best practices</span></span>

### <a name="target-sizes"></a><span data-ttu-id="f80c0-142">Taille des cibles</span><span class="sxs-lookup"><span data-stu-id="f80c0-142">Target sizes</span></span>

<span data-ttu-id="f80c0-143">Pour être facilement accessibles, les cibles du point de vue et du regard doivent être suffisamment grandes pour regarder confortablement et maintenir une tête stable sur la cible pour le temps imparti.</span><span class="sxs-lookup"><span data-stu-id="f80c0-143">To be easily accessible, head-gaze and dwell targets need to be large enough to look at comfortably, and hold one's head stable on the target for the prescribed time.</span></span> <span data-ttu-id="f80c0-144">Nous vous recommandons une taille de cible minimale de 2 degrés pour obtenir l’expérience la plus confortable.</span><span class="sxs-lookup"><span data-stu-id="f80c0-144">We recommend a minimum target size of 2 degrees to achieve the most comfortable experience.</span></span> 

### <a name="visual-feedback"></a><span data-ttu-id="f80c0-145">Retour visuel</span><span class="sxs-lookup"><span data-stu-id="f80c0-145">Visual feedback</span></span>

<span data-ttu-id="f80c0-146">Quand vous utilisez un remplissage radial pour représenter la durée de stabilisation, démarrez à partir du centre du bouton.</span><span class="sxs-lookup"><span data-stu-id="f80c0-146">When using a radial fill to represent the dwell timer, start from the center of button.</span></span> <span data-ttu-id="f80c0-147">Une réponse cohérente est plus claire que toutes les directions différentes sur les différents boutons.</span><span class="sxs-lookup"><span data-stu-id="f80c0-147">A consistent response is less confusing than all different directions on different buttons.</span></span> 

  * <span data-ttu-id="f80c0-148">Toutefois, cette règle peut être interrompue pour les interactions directionnelles (par exemple, navigation vers le haut/vers le haut/gauche/droite, etc.).</span><span class="sxs-lookup"><span data-stu-id="f80c0-148">This rule can be broken though for directional interactions (for example, nav up/down/left/right, and so on).</span></span> <span data-ttu-id="f80c0-149">Par exemple, Microsoft Dynamics 365 Guides fait une exception pour SUIVANT/PRECEDENT qui correspond aux remplissages gauche et droite.</span><span class="sxs-lookup"><span data-stu-id="f80c0-149">For example, Microsoft Dynamics 365 Guides makes an exception on NEXT/BACK being left right fills.</span></span>
  * <span data-ttu-id="f80c0-150">Envisagez d’inverser le remplissage radial à partir de l’extérieur, pour des scénarios tels que le basculement d’un bouton.</span><span class="sxs-lookup"><span data-stu-id="f80c0-150">Consider inverting radial fill from outside, for scenarios like toggling off a button.</span></span> <span data-ttu-id="f80c0-151">Le sentiment inverse d’appui sur un bouton est un schéma visuel agréable à conserver.</span><span class="sxs-lookup"><span data-stu-id="f80c0-151">The inverse feeling of pushing a button is a nice visual pattern to maintain.</span></span> 

### <a name="progressive-disclosure"></a><span data-ttu-id="f80c0-152">Affichage progressif</span><span class="sxs-lookup"><span data-stu-id="f80c0-152">Progressive disclosure</span></span>

<span data-ttu-id="f80c0-153">L’affichage progressif consiste à n’afficher que les informations pertinentes à chaque étape d’une interaction.</span><span class="sxs-lookup"><span data-stu-id="f80c0-153">Progressive disclosure means only showing as much detail as is relevant at each stage of an interaction.</span></span> <span data-ttu-id="f80c0-154">Pour le son, cela signifie que la cible du logement est révélée en surbrillance (par exemple, dans un contrôle de liste).</span><span class="sxs-lookup"><span data-stu-id="f80c0-154">For dwell, that means the dwell target is revealed on highlight (for example, in a list control).</span></span>

 ### <a name="oversized-targets"></a><span data-ttu-id="f80c0-155">Cibles trop grandes</span><span class="sxs-lookup"><span data-stu-id="f80c0-155">Oversized targets</span></span>

<span data-ttu-id="f80c0-156">La région de stabilisation peut être plus grande que l’icône à l’état inactif pour faciliter son utilisation, comme le bouton Précédent dans Microsoft Dynamics 365 Guides.</span><span class="sxs-lookup"><span data-stu-id="f80c0-156">Dwell region can be larger than inactive icon to make it easier to use, like the Back button in Microsoft Dynamics 365 Guides.</span></span>

### <a name="prevent-flickering-with-delayed-feedback"></a><span data-ttu-id="f80c0-157">Éviter le scintillement avec un retour décalé</span><span class="sxs-lookup"><span data-stu-id="f80c0-157">Prevent flickering with delayed feedback</span></span>

<span data-ttu-id="f80c0-158">Utilisez un court délai avant de démarrer le retour visuel afin d’éviter le scintillement quand l’utilisateur passe au-dessus d’une cible de stabilisation.</span><span class="sxs-lookup"><span data-stu-id="f80c0-158">Use a short delay before starting visual feedback to avoid flickering when someone passes over a dwell target.</span></span>
* <span data-ttu-id="f80c0-159">Pour les boutons qui sont interactifs fréquemment, conservez le délai pour que l’application soit réactive.</span><span class="sxs-lookup"><span data-stu-id="f80c0-159">For buttons interacted with frequently, keep the delay short so the application feels reactive.</span></span>
* <span data-ttu-id="f80c0-160">Pour les boutons qui sont interactifs rarement, un délai plus long peut être approprié pour éviter que l’interface twitchy.</span><span class="sxs-lookup"><span data-stu-id="f80c0-160">For buttons that are interacted with infrequently, a longer delay can be appropriate to avoid the interface feeling twitchy.</span></span>

<br>

---

## <a name="ui-patterns"></a><span data-ttu-id="f80c0-161">Schémas de l’interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="f80c0-161">UI patterns</span></span>

### <a name="high-frequency-buttons"></a><span data-ttu-id="f80c0-162">Boutons à haute fréquence</span><span class="sxs-lookup"><span data-stu-id="f80c0-162">High frequency buttons</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="f80c0-163">Les boutons à fréquence élevée sont des boutons utilisés couramment dans une application.</span><span class="sxs-lookup"><span data-stu-id="f80c0-163">High frequency buttons are buttons that are used commonly throughout an application.</span></span> <span data-ttu-id="f80c0-164">Les boutons Suivant et Précédent dans Microsoft Dynamics 365 Guides constituent un bon exemple.</span><span class="sxs-lookup"><span data-stu-id="f80c0-164">A good example of these are the next and back buttons in Microsoft Dynamics 365 Guides.</span></span><br>
        <br>
        <span data-ttu-id="f80c0-165">**Recommandations**</span><span class="sxs-lookup"><span data-stu-id="f80c0-165">**Recommendations**</span></span><br>
  * <span data-ttu-id="f80c0-166">Les boutons à fréquence élevée doivent être volumineux, plus faciles à toucher avec le regard</span><span class="sxs-lookup"><span data-stu-id="f80c0-166">High frequency buttons should be large, easier to hit with head-gaze</span></span>
  * <span data-ttu-id="f80c0-167">Restez près de la hauteur pour éviter les tensions ergonomiques.</span><span class="sxs-lookup"><span data-stu-id="f80c0-167">Stay near eye height to avoid ergonomic straining.</span></span><br>
        <br>
<span data-ttu-id="f80c0-168">*Image : Microsoft Dynamics 365 guides Next Button*</span><span class="sxs-lookup"><span data-stu-id="f80c0-168">*Image: Microsoft Dynamics 365 Guides next button*</span></span>
    :::column-end:::
        :::column:::
       ![Bouton suivant de Microsoft Dynamics 365 guides](images/GuideNextButton.png)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="low-frequency-buttons"></a><span data-ttu-id="f80c0-170">Boutons à fréquence faible</span><span class="sxs-lookup"><span data-stu-id="f80c0-170">Low frequency buttons</span></span>

<span data-ttu-id="f80c0-171">Les boutons à basse fréquence sont des boutons qui ne sont pas interactifs avec comme régulièrement dans l’application.</span><span class="sxs-lookup"><span data-stu-id="f80c0-171">Low frequency buttons are buttons that aren't interacted with as regularly throughout the application.</span></span> <span data-ttu-id="f80c0-172">À titre d’exemple, citons un bouton permettant d’accéder à un menu de paramètres ou d’effacer la totalité du travail.</span><span class="sxs-lookup"><span data-stu-id="f80c0-172">A good example might be a button to access the settings menu, or a button to clear all work.</span></span>

* <span data-ttu-id="f80c0-173">Dans la mesure du possible, maintenez ces boutons hors du chemin emprunté par les suivis de la tête afin d’éviter une activation accidentelle.</span><span class="sxs-lookup"><span data-stu-id="f80c0-173">Try to keep these buttons out of the way of frequent head-gaze paths to avoid accidental activation.</span></span> 

<br>

---

### <a name="confirmations"></a><span data-ttu-id="f80c0-174">Confirmations</span><span class="sxs-lookup"><span data-stu-id="f80c0-174">Confirmations</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="f80c0-175">Lorsqu’une action a un impact significatif, comme le chargement de l’argent, la suppression d’un travail ou le démarrage d’un processus long, il est utile de confirmer qu’une personne est censée sélectionner un bouton.</span><span class="sxs-lookup"><span data-stu-id="f80c0-175">When an action has significant impact, like charging money, deleting work, or starting a long process, it's useful to confirm that a person meant to select a button.</span></span><br>
        <br>
        <span data-ttu-id="f80c0-176">**Recommandations**</span><span class="sxs-lookup"><span data-stu-id="f80c0-176">**Recommendations**</span></span><br>
  * <span data-ttu-id="f80c0-177">Afficher la surbrillance de la sélection sur le bouton principal</span><span class="sxs-lookup"><span data-stu-id="f80c0-177">Show selection highlight on main button.</span></span>
  * <span data-ttu-id="f80c0-178">Révéler la cible de stabilisation en même temps que la surbrillance de la sélection</span><span class="sxs-lookup"><span data-stu-id="f80c0-178">Reveal dwell target at same time as selection highlight.</span></span>
  * <span data-ttu-id="f80c0-179">Pour le bouton secondaire, révéler la cible de stabilisation en fonction du suivi de la tête</span><span class="sxs-lookup"><span data-stu-id="f80c0-179">For the secondary button, reveal the dwell target on head-gaze.</span></span><br>
        <br>
<span data-ttu-id="f80c0-180">*Image : boîte de dialogue de confirmation des guides Microsoft Dynamics 365*</span><span class="sxs-lookup"><span data-stu-id="f80c0-180">*Image: Microsoft Dynamics 365 Guides confirmation dialog*</span></span>
    :::column-end:::
        :::column:::
       ![Boîte de dialogue de confirmation des guides Microsoft Dynamics 365](images/GuidesConfirmation.png)<br>
    :::column-end:::
:::row-end:::
        
<br>

---

### <a name="toggle-buttons"></a><span data-ttu-id="f80c0-182">Boutons bascule</span><span class="sxs-lookup"><span data-stu-id="f80c0-182">Toggle buttons</span></span>

<span data-ttu-id="f80c0-183">Les boutons bascule nécessitent une logique nuancée pour fonctionner correctement.</span><span class="sxs-lookup"><span data-stu-id="f80c0-183">Toggle buttons require some nuanced logic to work properly.</span></span> <span data-ttu-id="f80c0-184">Quand une personne se trouve sur un bouton bascule et l’active, elle doit quitter le bouton, puis revenir au redémarrage de la logique du logement.</span><span class="sxs-lookup"><span data-stu-id="f80c0-184">When a person dwells on a toggle button and activates it, they need to exit the button and then return to restart the dwell logic.</span></span> <span data-ttu-id="f80c0-185">Il est important que les boutons bascule présentent l’état actif et inactif.</span><span class="sxs-lookup"><span data-stu-id="f80c0-185">It's important that togglable buttons have a clear active versus inactive state.</span></span> 

<br>

---

### <a name="list-views"></a><span data-ttu-id="f80c0-186">Affichages de liste</span><span class="sxs-lookup"><span data-stu-id="f80c0-186">List views</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="f80c0-187">Les affichages de liste présentent un défi particulier pour les entrées de point de vue et de point d’entrée.</span><span class="sxs-lookup"><span data-stu-id="f80c0-187">List views present a particular challenge for head-gaze and dwell input.</span></span> <span data-ttu-id="f80c0-188">Les utilisateurs peuvent analyser le contenu sans avoir à vous Tiptoe autour des cibles du logement.</span><span class="sxs-lookup"><span data-stu-id="f80c0-188">People can scan the content without feeling like that have to tiptoe around the dwell targets.</span></span><br>
        <br>
<span data-ttu-id="f80c0-189">**Recommandations**</span><span class="sxs-lookup"><span data-stu-id="f80c0-189">**Recommendations**</span></span><br>
  * <span data-ttu-id="f80c0-190">Faites en sorte que la totalité de la ligne surbrille quand la tête est en regard, mais ne commence pas, sauf si le point de regard se trouve sur la cible d’un logement spécifique.</span><span class="sxs-lookup"><span data-stu-id="f80c0-190">Have the entire row highlight when head-gazed but doesn’t begin dwell unless head-gaze is on the specific dwell target.</span></span>
  * <span data-ttu-id="f80c0-191">Affichez uniquement la cible d’un logement lorsque la ligne est mise en surbrillance pour réduire le bruit visuel.</span><span class="sxs-lookup"><span data-stu-id="f80c0-191">Only show the dwell target when the row is highlighted to cut down on visual noise.</span></span>
  * <span data-ttu-id="f80c0-192">Soyez clair et cohérent avec la position des cibles du logement.</span><span class="sxs-lookup"><span data-stu-id="f80c0-192">Be clear and consistent with the position of dwell targets.</span></span>
  * <span data-ttu-id="f80c0-193">N’affichez pas toutes les cibles de logement à la fois pour éviter l’interface utilisateur répétitive.</span><span class="sxs-lookup"><span data-stu-id="f80c0-193">Don't show all dwell targets at once to avoid repetitive UI.</span></span>
  * <span data-ttu-id="f80c0-194">Réutilisez le même modèle aussi souvent que possible pour établir une familiarité avec l’expérience utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f80c0-194">Reuse the same pattern as often as possible to establish UX familiarity.</span></span><br>
        <br>
<span data-ttu-id="f80c0-195">*Image : liste des guides Microsoft Dynamics 365*</span><span class="sxs-lookup"><span data-stu-id="f80c0-195">*Image: Microsoft Dynamics 365 Guides list*</span></span>
    :::column-end:::
        :::column:::
       ![Liste des guides Microsoft Dynamics 365](images/GuidesListView.png)<br>
    :::column-end:::
:::row-end:::

<br>

---
 
 ## <a name="see-also"></a><span data-ttu-id="f80c0-197">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f80c0-197">See also</span></span>

* [<span data-ttu-id="f80c0-198">Pointer et valider</span><span class="sxs-lookup"><span data-stu-id="f80c0-198">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="f80c0-199">Mains : Manipulation directe</span><span class="sxs-lookup"><span data-stu-id="f80c0-199">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="f80c0-200">Mains : Mouvements</span><span class="sxs-lookup"><span data-stu-id="f80c0-200">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="f80c0-201">Mains : Pointer et valider</span><span class="sxs-lookup"><span data-stu-id="f80c0-201">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="f80c0-202">Interactions instinctuelles</span><span class="sxs-lookup"><span data-stu-id="f80c0-202">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="f80c0-203">Entrée vocale</span><span class="sxs-lookup"><span data-stu-id="f80c0-203">Voice input</span></span>](voice-input.md)
