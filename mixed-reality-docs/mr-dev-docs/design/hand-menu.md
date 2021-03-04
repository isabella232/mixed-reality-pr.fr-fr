---
title: Menu de la main
description: Les menus manuels permettent aux utilisateurs d’afficher rapidement une interface utilisateur attachée à la main pour les fonctions fréquemment utilisées.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: main, menu, bouton, accès rapide, disposition, casque de la réalité mixte, casque de la réalité mixte, casque de réalité virtuelle, HoloLens, MRTK, boîte à outils de réalité mixte
ms.openlocfilehash: 8a8b80843b7a107255a45b11868b0bd29a4e3108
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759455"
---
# <a name="hand-menu"></a><span data-ttu-id="5be8c-104">Menu de la main</span><span class="sxs-lookup"><span data-stu-id="5be8c-104">Hand menu</span></span>

![Emplacement de la main ulnar](images/UX_Hero_HandMenu.jpg)

<span data-ttu-id="5be8c-106">Le menu de la main est l’un des modèles d’expérience utilisateur les plus uniques dans HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5be8c-106">The hand menu is one of the most unique UX patterns in HoloLens 2.</span></span> <span data-ttu-id="5be8c-107">Elle vous permet d’accéder rapidement à une interface utilisateur jointe à la main.</span><span class="sxs-lookup"><span data-stu-id="5be8c-107">It allows you to quickly bring up hand-attached UI.</span></span> <span data-ttu-id="5be8c-108">Étant donné qu’il est accessible à tout moment et peut être affiché et masqué facilement, c’est parfait pour les actions rapides.</span><span class="sxs-lookup"><span data-stu-id="5be8c-108">Since it's accessible anytime and can be shown and hidden easily, it's great for quick actions.</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAg]

<span data-ttu-id="5be8c-109">Vous trouverez nos meilleures pratiques recommandées pour l’utilisation des menus manuels dans la liste ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="5be8c-109">You'll find our recommended best practices for working with hand menus in the list below.</span></span> <span data-ttu-id="5be8c-110">Vous trouverez également un exemple de scène illustrant le menu manuel dans [MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/hand-menu.md).</span><span class="sxs-lookup"><span data-stu-id="5be8c-110">You can also find an example scene demonstrating the hand menu in [MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/hand-menu.md).</span></span>

<br>

---

## <a name="best-practices"></a><span data-ttu-id="5be8c-111">Meilleures pratiques</span><span class="sxs-lookup"><span data-stu-id="5be8c-111">Best practices</span></span>

<span data-ttu-id="5be8c-112">**Conserver le nombre de boutons petit**</span><span class="sxs-lookup"><span data-stu-id="5be8c-112">**Keep the number of buttons small**</span></span> 

<span data-ttu-id="5be8c-113">En raison de la distance étroite entre un menu verrouillé et les yeux, et la tendance pour les utilisateurs à se concentrer sur une zone visuelle relativement petite à tout moment (le cône de vision est à peu près 10 degrés), nous vous recommandons de conserver le nombre de boutons petit.</span><span class="sxs-lookup"><span data-stu-id="5be8c-113">Because of the close distance between a hand-locked menu and the eyes, and the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), we recommend keeping the number of buttons small.</span></span> <span data-ttu-id="5be8c-114">Sur la base de notre exploration, une colonne avec trois boutons fonctionne bien en conservant tout le contenu dans le champ de vision (l’angle d’accès) même lorsqu’un utilisateur passe au centre de l’angle d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="5be8c-114">Based on our exploration, one column with three buttons works well by keeping all the content within the field of view (FOV) even when a user moves their hands to the center of the FOV.</span></span> 

<span data-ttu-id="5be8c-115">**Utiliser le menu manuellement pour une action rapide**</span><span class="sxs-lookup"><span data-stu-id="5be8c-115">**Use hand menu for quick action**</span></span> 

<span data-ttu-id="5be8c-116">L’élévation d’un bras et la maintenance de la position peuvent facilement entraîner une fatigue du bras.</span><span class="sxs-lookup"><span data-stu-id="5be8c-116">Raising an arm and maintaining the position could easily cause arm fatigue.</span></span> <span data-ttu-id="5be8c-117">Utilisez une méthode verrouillée à la main pour le menu nécessitant une faible interaction.</span><span class="sxs-lookup"><span data-stu-id="5be8c-117">Use a hand-locked method for the menu requiring a short interaction.</span></span> <span data-ttu-id="5be8c-118">Si votre menu est complexe et nécessite des temps d’interaction étendus, envisagez d’utiliser à la place un verrou universel ou verrouillé.</span><span class="sxs-lookup"><span data-stu-id="5be8c-118">If your menu is complex and requires extended interaction times, consider using world-locked or body-locked instead.</span></span> 

<span data-ttu-id="5be8c-119">**Angle du bouton/du panneau**</span><span class="sxs-lookup"><span data-stu-id="5be8c-119">**Button / Panel angle**</span></span>

<span data-ttu-id="5be8c-120">Les menus doivent s’afficher à l’épaule opposé et au milieu de la tête : cela permet à une main naturelle d’interagir avec le menu avec la main opposée et évite les positions difficiles ou inconfortables quand vous touchez des boutons.</span><span class="sxs-lookup"><span data-stu-id="5be8c-120">Menus should billboard towards the opposite shoulder and middle of the head: This allows a natural hand move to interact with the menu with the opposite hand and avoids any awkward or uncomfortable hand positions when touching buttons.</span></span> 

<span data-ttu-id="5be8c-121">**Envisagez de prendre en charge une opération à la main ou mains libres**</span><span class="sxs-lookup"><span data-stu-id="5be8c-121">**Consider supporting one-handed or hands-free operation**</span></span>

<span data-ttu-id="5be8c-122">Ne partez pas du principe que les deux mains de l’utilisateur sont toujours disponibles.</span><span class="sxs-lookup"><span data-stu-id="5be8c-122">Don't assume both of the user's hands are always available.</span></span> <span data-ttu-id="5be8c-123">Considérez un large éventail de contextes lorsque l’un ou l’autre des mains n’est pas disponible et assurez-vous que votre conception compte pour ces situations.</span><span class="sxs-lookup"><span data-stu-id="5be8c-123">Consider a wide range of contexts when one or both hands aren't available, and make sure your design accounts for those situations.</span></span> <span data-ttu-id="5be8c-124">Pour prendre en charge un menu contextuel à un seul mains, vous pouvez essayer de passer le positionnement du menu de façon à ce qu’il passe à l’état verrouillé à l’extérieur lorsque la main est tournée (s’affiche à l’écran).</span><span class="sxs-lookup"><span data-stu-id="5be8c-124">To support a one-handed hand menu, you can try transitioning the menu placement from hand-locked to world-locked when the hand flips (goes palm down).</span></span> <span data-ttu-id="5be8c-125">Pour les scénarios mains libres, envisagez d’utiliser une commande vocale pour appeler le menu de la main.</span><span class="sxs-lookup"><span data-stu-id="5be8c-125">For hands-free scenarios, consider using a voice command to invoke the hand menu.</span></span>

<span data-ttu-id="5be8c-126">**Évitez d’ajouter des boutons près du poignet (bouton de démarrage du système)**</span><span class="sxs-lookup"><span data-stu-id="5be8c-126">**Avoid adding buttons near the wrist (system home button)**</span></span>

<span data-ttu-id="5be8c-127">Si les boutons de menu de la main sont placés trop près du bouton d’origine, ils peuvent se déclencher accidentellement lors de l’interaction avec le menu de la main.</span><span class="sxs-lookup"><span data-stu-id="5be8c-127">If the hand menu buttons are placed too close to the home button, it may accidentally trigger while interacting with the hand menu.</span></span>

<br>

## <a name="hand-menu-with-large-and-complex-ui-controls"></a><span data-ttu-id="5be8c-128">Menu manuel avec des contrôles d’interface utilisateur volumineux et complexes</span><span class="sxs-lookup"><span data-stu-id="5be8c-128">Hand menu with large and complex UI controls</span></span>

<img src="images/HandMenu_SizeExample.png" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<span data-ttu-id="5be8c-129">Il est recommandé de limiter le nombre de boutons ou de contrôles d’interface utilisateur dans les menus attachés à la main.</span><span class="sxs-lookup"><span data-stu-id="5be8c-129">It's recommended to limit the number of buttons or UI controls on hand-attached menus.</span></span> <span data-ttu-id="5be8c-130">Cela est dû au fait que l’interaction étendue avec un grand nombre d’éléments d’interface utilisateur peut entraîner une fatigue ARM.</span><span class="sxs-lookup"><span data-stu-id="5be8c-130">This is because extended interaction with a large number of UI elements can cause arm fatigue.</span></span> <span data-ttu-id="5be8c-131">Si votre expérience requiert un grand menu, fournissez un moyen facile pour l’utilisateur de verrouiller le menu.</span><span class="sxs-lookup"><span data-stu-id="5be8c-131">If your experience requires a large menu, provide an easy way for the user to world lock the menu.</span></span> <span data-ttu-id="5be8c-132">L’une des techniques recommandées est l’utilisation de l’option de verrouillage universel lorsque la main chute ou s’éloigne de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5be8c-132">One technique we recommend is to world-lock then menu when the hand drops or flips away from the user.</span></span> <span data-ttu-id="5be8c-133">Une seconde technique consiste à autoriser l’utilisateur à saisir directement le menu en revanche.</span><span class="sxs-lookup"><span data-stu-id="5be8c-133">A second technique is to allow the user to directly grab the menu with the other hand.</span></span> <span data-ttu-id="5be8c-134">Quand l’utilisateur relâche le menu, le menu doit être un verrou universel.</span><span class="sxs-lookup"><span data-stu-id="5be8c-134">When the user releases the menu, the menu should world lock.</span></span> <span data-ttu-id="5be8c-135">De cette façon, un utilisateur peut interagir avec les différents éléments de l’interface utilisateur de manière conviviale et en toute confiance sur une période prolongée.</span><span class="sxs-lookup"><span data-stu-id="5be8c-135">This way, a user can interact with various UI elements comfortably and confidently over an extended period of time.</span></span> 

<span data-ttu-id="5be8c-136">Lorsque le menu est verrouillé dans le monde entier, veillez à fournir un moyen de déplacer le menu, puis fermez le menu lorsqu’il n’est plus nécessaire.</span><span class="sxs-lookup"><span data-stu-id="5be8c-136">When the menu is world-locked, make sure to provide a way to move the menu, and close the menu when it's no longer needed.</span></span> <span data-ttu-id="5be8c-137">Rendez le menu déplaçable en fournissant des poignées sur les côtés ou en haut du menu.</span><span class="sxs-lookup"><span data-stu-id="5be8c-137">Make the menu movable by providing handles on the sides or top of menu.</span></span> <span data-ttu-id="5be8c-138">Ajoutez un bouton Fermer pour permettre au menu de se fermer.</span><span class="sxs-lookup"><span data-stu-id="5be8c-138">Add a close button to allow the menu to close.</span></span> <span data-ttu-id="5be8c-139">Autorise le rattachement du menu à la main lorsque l’utilisateur est confronté à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5be8c-139">Allow for the menu to reattach to the hand when the user hand faces the user.</span></span> <span data-ttu-id="5be8c-140">Nous vous recommandons également de demander à ce que les utilisateurs pointent à la main pour empêcher les fausses activations (voir ci-dessous).</span><span class="sxs-lookup"><span data-stu-id="5be8c-140">We also recommend requiring that the users gaze at their hand to prevent false activations (see below).</span></span>

<span data-ttu-id="5be8c-141">**Grand menu présentant un problème d’utilisation**</span><span class="sxs-lookup"><span data-stu-id="5be8c-141">**Large menu that shows a usability issue**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AOPx]

<span data-ttu-id="5be8c-142">**Menu déroulant à la main**</span><span class="sxs-lookup"><span data-stu-id="5be8c-142">**World-locked menu on hand drop**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AGZi]

<span data-ttu-id="5be8c-143">**Récupération manuelle & de l’extraction dans le monde entier-verrouiller le menu**</span><span class="sxs-lookup"><span data-stu-id="5be8c-143">**Manual grab & pull to world-lock the menu**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAf]

## <a name="how-to-prevent-false-activation"></a><span data-ttu-id="5be8c-144">Comment empêcher une fausse activation</span><span class="sxs-lookup"><span data-stu-id="5be8c-144">How to prevent false activation</span></span>

<span data-ttu-id="5be8c-145">Si vous utilisez simplement Palm-up comme événement pour déclencher le menu de la main, il peut s’afficher accidentellement quand vous n’en avez pas besoin (faux positif), car les gens déplacent leurs mains intentionnellement (pour la communication et la manipulation d’objets) et involontairement.</span><span class="sxs-lookup"><span data-stu-id="5be8c-145">If you use just palm-up as an event to trigger the hand menu, it may accidentally appear when you don't need it (false-positive), because people move their hands both intentionally (for communication and object manipulation) and unintentionally.</span></span> <span data-ttu-id="5be8c-146">Pour réduire les fausses activations, ajoutez une étape supplémentaire en plus de l’événement Palm-up pour appeler le menu de la main (par exemple, des doigts entièrement ouverts ou l’utilisateur intentionnellement Gazing à la main).</span><span class="sxs-lookup"><span data-stu-id="5be8c-146">To reduce false activations, add an extra step besides the palm-up event to invoke the hand menu (such as fully opened fingers, or the user intentionally gazing at their hand).</span></span>

<span data-ttu-id="5be8c-147">**Exiger un Palm plat**</span><span class="sxs-lookup"><span data-stu-id="5be8c-147">**Require Flat Palm**</span></span>

<span data-ttu-id="5be8c-148">En exigeant une main ouverte, vous pouvez empêcher une fausse activation qui peut se produire lorsque l’utilisateur manipule des objets ou des gestes tout en communiquant au sein d’un environnement.</span><span class="sxs-lookup"><span data-stu-id="5be8c-148">By requiring a flat open hand, you can prevent false activation that might occur as the user manipulates objects or gestures while communicating within an environment.</span></span> 

<span data-ttu-id="5be8c-149">**Exiger le point de regard**</span><span class="sxs-lookup"><span data-stu-id="5be8c-149">**Require Gaze**</span></span>

<span data-ttu-id="5be8c-150">En demandant à l’utilisateur de pointer à sa main (avec le regard ou le point de vue de la tête), il empêche les fausses activations, car l’utilisateur doit faire attention à la main en tant qu’étape d’activation secondaire (avec un seuil de distance réglable pour permettre l’utilisation du confort de l’utilisateur).</span><span class="sxs-lookup"><span data-stu-id="5be8c-150">By requiring the user to gaze at their hand (either with eye gaze or head gaze), it prevents false activations because of the user having to direct their attention to the hand as a secondary activation step (with a tunable distance threshold used to allow for user comfort).</span></span>  

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Asn4]

---

## <a name="hand-menu-placement-best-practices"></a><span data-ttu-id="5be8c-151">Meilleures pratiques relatives à l’emplacement des menus manuels</span><span class="sxs-lookup"><span data-stu-id="5be8c-151">Hand menu placement best practices</span></span>

<span data-ttu-id="5be8c-152">Dans l’anatomie humaine, le nerf ulnar est un nerf qui s’exécute près du segment ulna.</span><span class="sxs-lookup"><span data-stu-id="5be8c-152">In human anatomy, the ulnar nerve is a nerve that runs near the ulna bone.</span></span> <span data-ttu-id="5be8c-153">Le ulna est un long segment trouvé dans le bras qui s’étend du coud au doigt le plus petit.</span><span class="sxs-lookup"><span data-stu-id="5be8c-153">The ulna is a long bone found in the forearm that stretches from the elbow to the smallest finger.</span></span>

<span data-ttu-id="5be8c-154">Vous trouverez ci-dessous deux placements recommandés en fonction de nos explorations :</span><span class="sxs-lookup"><span data-stu-id="5be8c-154">Below are two recommended placements based on our explorations:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="5be8c-155">![Ulnar l’emplacement des mains dans Palm](images/UlnarSideHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="5be8c-155">![Ulnar side hand location inside palm](images/UlnarSideHandMenu.gif)</span></span><br>
        <span data-ttu-id="5be8c-156">**A. ulnar dans Palm**</span><span class="sxs-lookup"><span data-stu-id="5be8c-156">**A. Ulnar inside palm**</span></span><br>
        <span data-ttu-id="5be8c-157">Cette position est fiable, car les mains ne se chevauchent pas mutuellement.</span><span class="sxs-lookup"><span data-stu-id="5be8c-157">This position is reliable because the hands don't overlap each other.</span></span> <span data-ttu-id="5be8c-158">Cela est essentiel pour une détection et un suivi précis des mains.</span><span class="sxs-lookup"><span data-stu-id="5be8c-158">This is critical for accurate hand detection and tracking.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="5be8c-159">![Ulnar à l’emplacement du côté supérieur à la main](images/UlnarAboveHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="5be8c-159">![Ulnar side hand location above hand](images/UlnarAboveHandMenu.gif)</span></span><br>
        <span data-ttu-id="5be8c-160">**B. ulnar au-dessus de la main**</span><span class="sxs-lookup"><span data-stu-id="5be8c-160">**B. Ulnar above hand**</span></span><br>
        <span data-ttu-id="5be8c-161">Cet emplacement est à l’aise pour les utilisateurs, car ils n’ont pas besoin d’augmenter trop le bras pour interagir avec le menu de la main.</span><span class="sxs-lookup"><span data-stu-id="5be8c-161">This location is comfortable for users because they don't need to raise their arm too much to interact with the hand menu.</span></span> <span data-ttu-id="5be8c-162">Nous vous recommandons de placer les menus **13 cm** au-dessus du Palm et d’aligner les boutons à l’intérieur du Palm ulnar.</span><span class="sxs-lookup"><span data-stu-id="5be8c-162">We recommend placing menus **13 cm** above the palm and align the buttons inside the ulnar palm.</span></span> [<span data-ttu-id="5be8c-163">En savoir plus sur la taille optimale du bouton</span><span class="sxs-lookup"><span data-stu-id="5be8c-163">Read more about the optimal button size</span></span>](interactable-object.md)<br>
        <br>
        <span data-ttu-id="5be8c-164">Pour des raisons techniques, nous recommandons cet emplacement avec une implémentation obligatoire : le développeur devra geler le menu une fois que la main opposée de l’utilisateur est proche de son interaction.</span><span class="sxs-lookup"><span data-stu-id="5be8c-164">For technical reasons, we recommend this location with one required implementation: the developer will need to freeze the menu once the user's opposite hand gets close to interacting with it.</span></span> <span data-ttu-id="5be8c-165">Cela évite à jitteriness de se chevaucher les mains et permet également de cibler plus rapidement les boutons.</span><span class="sxs-lookup"><span data-stu-id="5be8c-165">This will avoid jitteriness from overlapping hands and also allows for a faster targeting of the buttons.</span></span><br>
        <br>
        <span data-ttu-id="5be8c-166">Les caméras HoloLens 2 identifient les mains avec précision lorsqu’elles sont séparées les unes des autres.</span><span class="sxs-lookup"><span data-stu-id="5be8c-166">HoloLens 2 cameras identify hands accurately when they're separate from each other.</span></span> <span data-ttu-id="5be8c-167">Les mains qui se chevauchent peuvent entraîner un déplacement des menus manuels hors de l’emplacement d’ancrage.</span><span class="sxs-lookup"><span data-stu-id="5be8c-167">Any overlapping hands can cause hand menus move away from the anchor location.</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="menu-positions-that-arent-recommended"></a><span data-ttu-id="5be8c-168">Positions de menu non recommandées</span><span class="sxs-lookup"><span data-stu-id="5be8c-168">Menu positions that aren't recommended</span></span>

<span data-ttu-id="5be8c-169">Nous avons fait des recherches utilisateur avec différents emplacements et dispositions de menus, les emplacements de menu suivants ne sont **pas recommandés**, recherchez les inconvénients de chaque étude ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="5be8c-169">We have done user research with different menus layouts and locations, the following menu locations are **NOT recommended**, find the cons of each study below:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="5be8c-170">![Au-dessus du bras](images/AboveArm.gif)</span><span class="sxs-lookup"><span data-stu-id="5be8c-170">![Above arm](images/AboveArm.gif)</span></span><br>
        <span data-ttu-id="5be8c-171">**Au-dessus du bras**</span><span class="sxs-lookup"><span data-stu-id="5be8c-171">**Above the arm**</span></span><br>
        <span data-ttu-id="5be8c-172">1-difficulté à entretenir un bon suivi des mains</span><span class="sxs-lookup"><span data-stu-id="5be8c-172">1 - Difficult to maintain good hand tracking</span></span><br>
        <span data-ttu-id="5be8c-173">2-provoque une fatigue utilisateur en raison d’une position non naturelle</span><span class="sxs-lookup"><span data-stu-id="5be8c-173">2 - Causes user fatigue because of unnatural position</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="5be8c-174">![Les doigts ci-dessus](images/AboveFingers.gif)</span><span class="sxs-lookup"><span data-stu-id="5be8c-174">![Above fingers](images/AboveFingers.gif)</span></span><br>
        <span data-ttu-id="5be8c-175">**Les doigts ci-dessus**</span><span class="sxs-lookup"><span data-stu-id="5be8c-175">**Above fingers**</span></span><br>
        <span data-ttu-id="5be8c-176">fatigue à 1 main en raison de la main pendant une longue période</span><span class="sxs-lookup"><span data-stu-id="5be8c-176">1 - Hand fatigue because of holding out hand for a long time</span></span><br>
        <span data-ttu-id="5be8c-177">2 problèmes de suivi sur l’index et les doigts centraux</span><span class="sxs-lookup"><span data-stu-id="5be8c-177">2 - Hand tracking issues on index and middle fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="5be8c-178">![Au-dessus de Center Palm](images/handCenter.gif)</span><span class="sxs-lookup"><span data-stu-id="5be8c-178">![Above center palm](images/handCenter.gif)</span></span><br>
        <span data-ttu-id="5be8c-179">**Au-dessus-Centre Palm**</span><span class="sxs-lookup"><span data-stu-id="5be8c-179">**Above-center palm**</span></span><br>
        <span data-ttu-id="5be8c-180">problèmes de suivi de 1 main en raison du chevauchement des mains</span><span class="sxs-lookup"><span data-stu-id="5be8c-180">1 - Hand tracking issues because of overlapping hands</span></span><br>
        <span data-ttu-id="5be8c-181">fatigue à deux mains en raison de l’interrogation de longue durée pour interagir avec les menus</span><span class="sxs-lookup"><span data-stu-id="5be8c-181">2 - Hand fatigue because of holding hands for long time to interact with menus</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="5be8c-182">![Le haut ](images/TopFingerTip.gif) de **la main**</span><span class="sxs-lookup"><span data-stu-id="5be8c-182">![Top Fingertip](images/TopFingerTip.gif) **Top fingertip**</span></span><br>
        <span data-ttu-id="5be8c-183">1-problèmes de suivi de la main</span><span class="sxs-lookup"><span data-stu-id="5be8c-183">1 - Hand tracking issues</span></span><br>
        <span data-ttu-id="5be8c-184">2-la fatigue de la main au-dessus de la position normale</span><span class="sxs-lookup"><span data-stu-id="5be8c-184">2 - Hand fatigue from holding hand above normal posture</span></span><br>
        <span data-ttu-id="5be8c-185">3-problèmes de pression sur les boutons avec d’autres doigts par accident en raison d’un espace limité entre les doigts</span><span class="sxs-lookup"><span data-stu-id="5be8c-185">3 - Issues pressing buttons with other fingers by accident because of limited space between fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="5be8c-186">![Arrière du bras](images/BackOfTheArm.gif)</span><span class="sxs-lookup"><span data-stu-id="5be8c-186">![Back of the Arm](images/BackOfTheArm.gif)</span></span><br>
        <span data-ttu-id="5be8c-187">**Arrière du bras**</span><span class="sxs-lookup"><span data-stu-id="5be8c-187">**Back of the arm**</span></span><br>
        <span data-ttu-id="5be8c-188">1-peut déclencher le bouton d’origine par accident</span><span class="sxs-lookup"><span data-stu-id="5be8c-188">1 - Can trigger home button by accident</span></span><br>
        <span data-ttu-id="5be8c-189">2-n’est pas une position naturelle ou confortable</span><span class="sxs-lookup"><span data-stu-id="5be8c-189">2 - Not a natural or comfortable position</span></span>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="5be8c-190">Menu de la main dans MRTK (ensemble d’outils de réalité mixte) pour Unity</span><span class="sxs-lookup"><span data-stu-id="5be8c-190">Hand menu in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="5be8c-191">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fournit des scripts et des exemples de scènes pour le menu de la main.</span><span class="sxs-lookup"><span data-stu-id="5be8c-191">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and example scenes for the hand menu.</span></span> <span data-ttu-id="5be8c-192">Le script du solveur HandConstraintPalmUp vous permet de joindre des objets aux mains avec différentes options configurables.</span><span class="sxs-lookup"><span data-stu-id="5be8c-192">The HandConstraintPalmUp solver script allows you to attach any objects to the hands with various configurable options.</span></span> <span data-ttu-id="5be8c-193">Les exemples de menu manuel de MRTK incluent des options utiles, telles que le Palm plat et le point de vue du regard pour empêcher l’activation erronée.</span><span class="sxs-lookup"><span data-stu-id="5be8c-193">MRTK's hand menu examples include useful options such as flat palm and gaze requirement for preventing false activation.</span></span>

* [<span data-ttu-id="5be8c-194">Documentation des menus contextuels</span><span class="sxs-lookup"><span data-stu-id="5be8c-194">Hand Menu Documentations</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/hand-menu.md)
* [<span data-ttu-id="5be8c-195">Exemple de scène de menu manuel</span><span class="sxs-lookup"><span data-stu-id="5be8c-195">Hand Menu Example Scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandMenuExamples.unity)

<span data-ttu-id="5be8c-196">Vous pouvez essayer des exemples de menu manuel dans HoloLens 2 avec l’application MRTK d’exemples de Hub.</span><span class="sxs-lookup"><span data-stu-id="5be8c-196">You can try hand menu examples in HoloLens 2 with MRTK Examples Hub app.</span></span> 
* [<span data-ttu-id="5be8c-197">Scène du menu manuel dans MRTK exemples Hub</span><span class="sxs-lookup"><span data-stu-id="5be8c-197">Hand Menu Scene in MRTK Examples Hub</span></span>](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4?activetab=pivot:overviewtab)

<br>

---

## <a name="see-also"></a><span data-ttu-id="5be8c-198">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5be8c-198">See also</span></span>

* [<span data-ttu-id="5be8c-199">Curseurs</span><span class="sxs-lookup"><span data-stu-id="5be8c-199">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="5be8c-200">Rayon émanant de la main</span><span class="sxs-lookup"><span data-stu-id="5be8c-200">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="5be8c-201">Button</span><span class="sxs-lookup"><span data-stu-id="5be8c-201">Button</span></span>](button.md)
* [<span data-ttu-id="5be8c-202">Objet avec interaction possible</span><span class="sxs-lookup"><span data-stu-id="5be8c-202">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="5be8c-203">Rectangle englobant et barre de l’application</span><span class="sxs-lookup"><span data-stu-id="5be8c-203">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="5be8c-204">Manipulation</span><span class="sxs-lookup"><span data-stu-id="5be8c-204">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="5be8c-205">Menu de la main</span><span class="sxs-lookup"><span data-stu-id="5be8c-205">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="5be8c-206">Menu proche</span><span class="sxs-lookup"><span data-stu-id="5be8c-206">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="5be8c-207">Collection d’objets</span><span class="sxs-lookup"><span data-stu-id="5be8c-207">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="5be8c-208">Commande vocale</span><span class="sxs-lookup"><span data-stu-id="5be8c-208">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="5be8c-209">Clavier</span><span class="sxs-lookup"><span data-stu-id="5be8c-209">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="5be8c-210">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="5be8c-210">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="5be8c-211">Tablette</span><span class="sxs-lookup"><span data-stu-id="5be8c-211">Slate</span></span>](slate.md)
* [<span data-ttu-id="5be8c-212">Curseur</span><span class="sxs-lookup"><span data-stu-id="5be8c-212">Slider</span></span>](slider.md)
* [<span data-ttu-id="5be8c-213">Nuanceur</span><span class="sxs-lookup"><span data-stu-id="5be8c-213">Shader</span></span>](shader.md)
* [<span data-ttu-id="5be8c-214">Billboarding et tag-along</span><span class="sxs-lookup"><span data-stu-id="5be8c-214">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="5be8c-215">Affichage de la progression</span><span class="sxs-lookup"><span data-stu-id="5be8c-215">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="5be8c-216">Aimantation de surface</span><span class="sxs-lookup"><span data-stu-id="5be8c-216">Surface magnetism</span></span>](surface-magnetism.md)
