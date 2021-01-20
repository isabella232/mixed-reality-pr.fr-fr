---
title: Curseurs
description: Un curseur, ou un indicateur de votre vecteur de ciblage, fournit des commentaires continus permettant à l’utilisateur de comprendre ce que HoloLens comprend pour ses intentions.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (1re génération), HoloLens 2, réalité mixte, curseurs, ciblage, point de regard, mouvements, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, HoloLens, MRTK, boîte à outils de réalité mixte, rayons, entrée
ms.openlocfilehash: 0525bb9b30dfe71fba7b8ebf2afd2c87a8c97a27
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582402"
---
# <a name="cursors"></a><span data-ttu-id="2b9ab-104">Curseurs</span><span class="sxs-lookup"><span data-stu-id="2b9ab-104">Cursors</span></span>

![Curseurs](images/UX_Hero_Cursor.jpg)

<span data-ttu-id="2b9ab-106">Un curseur fournit des commentaires continus en fonction de l’endroit où le casque estime qu’un utilisateur a actuellement le focus à un moment donné.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-106">A cursor provides continuous feedback based on where the headset believes a users current focus is at a given time.</span></span> <span data-ttu-id="2b9ab-107">Le retour de curseur comprend la zone, l’hologramme ou le point de l’environnement virtuel qui répond à l’entrée.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-107">Cursor feedback includes what area, hologram, or point in the virtual environment responds to input.</span></span> <span data-ttu-id="2b9ab-108">Même si le curseur est une représentation numérique de l’endroit où l’appareil comprend l’attention de l’utilisateur, ce n’est pas le même que de déterminer les intentions de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-108">Even though the cursor is a digital representation of where the device understands the user's attention to be, that's not the same as determining the user's intentions.</span></span> <span data-ttu-id="2b9ab-109">Les commentaires des curseurs permettent également aux utilisateurs de connaître les réponses système à attendre.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-109">The cursor feedback also lets users know what system responses to expect.</span></span> <span data-ttu-id="2b9ab-110">Vous pouvez utiliser les commentaires pour communiquer leur intention à l’appareil, ce qui augmente la confiance de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-110">You can use the feedback to communicate their intention to the device, which increases user confidence.</span></span>

<span data-ttu-id="2b9ab-111">Il existe 3 types de curseurs : **Finger, Ray** et **point-regard**.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-111">There are 3 kinds of cursors: **finger, ray**, and **head-gaze**.</span></span> <span data-ttu-id="2b9ab-112">Ces curseurs de pointage fonctionnent avec différentes modalités d’entrée sur HoloLens, HoloLens 2 et les casques immersifs.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-112">These pointing cursors work with different input modalities on HoloLens, HoloLens 2, and immersive headsets.</span></span> <span data-ttu-id="2b9ab-113">Vous trouverez ci-dessous des conseils sur le type de curseur à utiliser pour chaque type de casque et de modèle d’interaction.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-113">Below is guidance on which type of cursor to use for each type of headset and interaction model.</span></span> <span data-ttu-id="2b9ab-114">Dans la boîte à outils de la réalité mixte (MRTK), nous avons créé des modules de curseurs de glisser-déplacer pour vous aider à créer l’expérience de pointage appropriée.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-114">In the Mixed Reality Toolkit (MRTK), we've created drag-and-drop cursors modules to help you build the right pointing experience.</span></span>

## <a name="device-support"></a><span data-ttu-id="2b9ab-115">Prise en charge des appareils</span><span class="sxs-lookup"><span data-stu-id="2b9ab-115">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="2b9ab-116"><strong>Fonctionnalité</strong></span><span class="sxs-lookup"><span data-stu-id="2b9ab-116"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="2b9ab-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1ère génération)</strong></a></span><span class="sxs-lookup"><span data-stu-id="2b9ab-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="2b9ab-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="2b9ab-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="2b9ab-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>Casques immersifs</strong></a></span><span class="sxs-lookup"><span data-stu-id="2b9ab-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="2b9ab-120">Curseur Finger</span><span class="sxs-lookup"><span data-stu-id="2b9ab-120">Finger cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="2b9ab-121">✔️</span><span class="sxs-lookup"><span data-stu-id="2b9ab-121">✔️</span></span></td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="2b9ab-122">Curseur Ray</span><span class="sxs-lookup"><span data-stu-id="2b9ab-122">Ray cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="2b9ab-123">✔️</span><span class="sxs-lookup"><span data-stu-id="2b9ab-123">✔️</span></span></td>
        <td><span data-ttu-id="2b9ab-124">✔️</span><span class="sxs-lookup"><span data-stu-id="2b9ab-124">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="2b9ab-125">Curseur en tête</span><span class="sxs-lookup"><span data-stu-id="2b9ab-125">Head-gaze cursor</span></span></td>
        <td><span data-ttu-id="2b9ab-126">✔️</span><span class="sxs-lookup"><span data-stu-id="2b9ab-126">✔️</span></span></td>
        <td><span data-ttu-id="2b9ab-127">✔️</span><span class="sxs-lookup"><span data-stu-id="2b9ab-127">✔️</span></span></td>
        <td><span data-ttu-id="2b9ab-128">✔️</span><span class="sxs-lookup"><span data-stu-id="2b9ab-128">✔️</span></span></td>
    </tr>
</table>

## <a name="finger-cursor"></a><span data-ttu-id="2b9ab-129">Curseur Finger</span><span class="sxs-lookup"><span data-stu-id="2b9ab-129">Finger cursor</span></span>

<span data-ttu-id="2b9ab-130">Le curseur Finger est uniquement disponible sur le HoloLens 2 pour améliorer le mode d’interaction «[manipulation directe avec mains](direct-manipulation.md)».</span><span class="sxs-lookup"><span data-stu-id="2b9ab-130">The finger cursor is only available on the HoloLens 2 to enhance the "[direct manipulation with hands](direct-manipulation.md)" interaction mode.</span></span> <span data-ttu-id="2b9ab-131">Nous avons attaché des anneaux aux conseils des deux index pour mieux comprendre où le doigt pointe.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-131">We've attached rings to the tips of both index fingers to better understand where the finger is pointing.</span></span> <span data-ttu-id="2b9ab-132">La taille de la sonnerie est basée sur la proximité du doigt par rapport à la surface de l’interface utilisateur, qui se réduit à un petit point lorsque le doigt touche l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-132">The ring size is based on the proximity of the finger to the UI surface, which shrinks to a small dot when the finger touches the UI.</span></span> <span data-ttu-id="2b9ab-133">Plus le doigt est proche, plus l’anneau est petit.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-133">The closer the finger, the smaller the ring.</span></span> <br>

<span data-ttu-id="2b9ab-134">![curseur Finger](images/finger-cursor.png)</span><span class="sxs-lookup"><span data-stu-id="2b9ab-134">![finger cursor](images/finger-cursor.png)</span></span><br>
<span data-ttu-id="2b9ab-135">**Commentaires visuels États de Finger Cursor** 1 : l’anneau se réduit à un point.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-135">**Visual feedback states of finger cursor** 1: The ring shrinks to a dot.</span></span> <span data-ttu-id="2b9ab-136">2 : l’anneau s’aligne sur la surface.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-136">2: The ring aligns with surface.</span></span> <span data-ttu-id="2b9ab-137">3 : l’anneau est perpendiculaire au vecteur Finger.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-137">3: The ring is perpendicular to finger vector.</span></span> <span data-ttu-id="2b9ab-138">4 : aucune sonnerie.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-138">4: No ring.</span></span>

## <a name="ray-cursor"></a><span data-ttu-id="2b9ab-139">Curseur Ray</span><span class="sxs-lookup"><span data-stu-id="2b9ab-139">Ray cursor</span></span>

<span data-ttu-id="2b9ab-140">Les curseurs de rayon sont attachés à la fin des rayons de pointage éloignés pour permettre la manipulation des objets qui ne sont pas en contact avec la main.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-140">Ray cursors attach to the end of far pointing rays to allow manipulation of objects that are out of hands-reach.</span></span> <span data-ttu-id="2b9ab-141">Dans les casques immersifs, les rayons se déplacent des contrôleurs de mouvement et se terminent par des points-curseurs.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-141">In immersive headsets, the rays shoot out from motion controllers and end in dot cursors.</span></span> <span data-ttu-id="2b9ab-142">Dans HoloLens 2, nous appliquons le modèle mental de ces rayons de contrôleur de mouvement et des rayons de main qui proviennent des palmiers et se terminent par les curseurs en forme d’anneau qui sont cohérents avec les curseurs Finger utilisés dans la manipulation directe.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-142">In HoloLens 2, we apply the mental model of these motion controller rays and designed hand rays that originate from the palms and end in ring-shaped cursors that are consistent with finger cursors used in direct manipulation.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="2b9ab-143">![Contrôleur de curseurs Ray](images/ray-cursor-controller.png)</span><span class="sxs-lookup"><span data-stu-id="2b9ab-143">![Ray cursor controller](images/ray-cursor-controller.png)</span></span><br>
        <span data-ttu-id="2b9ab-144">**Curseurs de rayon de contrôleurs de mouvement**</span><span class="sxs-lookup"><span data-stu-id="2b9ab-144">**Ray cursors of motion controllers**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2b9ab-145">![Curseur de la main](images/ray-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="2b9ab-145">![Ray cursor hand](images/ray-cursor-hand.png)</span></span><br>
        <span data-ttu-id="2b9ab-146">**Curseurs de Ray des mains**</span><span class="sxs-lookup"><span data-stu-id="2b9ab-146">**Ray cursors of hands**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="head-gaze-cursor"></a><span data-ttu-id="2b9ab-147">Curseur en tête</span><span class="sxs-lookup"><span data-stu-id="2b9ab-147">Head-gaze cursor</span></span>

<span data-ttu-id="2b9ab-148">Le curseur en tête est un point qui s’attache à la fin d’un vecteur de pointage de tête invisible qui utilise la position et la rotation de l’en-tête.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-148">The head-gaze cursor is a dot that attaches to the end of an invisible head-gaze vector that uses the position and rotation of the head to point.</span></span> <span data-ttu-id="2b9ab-149">Pour exécuter des actions, ce curseur de pointage est associé à diverses entrées de validation telles que le TAP-Air, les commandes vocales, le son et l’enfoncement de bouton.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-149">To execute actions, this pointing cursor is paired with various commit inputs such as air tap, voice commands, dwell, and button press.</span></span> <span data-ttu-id="2b9ab-150">Dans HoloLens 2, le point de regard est le mieux associé à toute entrée de validation qui n’est pas de pression pneumatique, car il y aura un conflit d’interaction entre les rayons de toucher et les mains de l’air.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-150">In HoloLens 2, head-gaze is best paired with any commit input that isn't air tap, as there will be interaction conflict between air tap and far hand rays.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="2b9ab-151">![Pointeur vers la droite de la tête](images/head-gaze-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="2b9ab-151">![Head gaze cursor hand](images/head-gaze-cursor-hand.png)</span></span><br>
        <span data-ttu-id="2b9ab-152">**Curseur en tête avec mouvement vers la main**</span><span class="sxs-lookup"><span data-stu-id="2b9ab-152">**Head-gaze cursor with hand gesture**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2b9ab-153">![Voix du curseur en tête](images/head-gaze-cursor-voice.png)</span><span class="sxs-lookup"><span data-stu-id="2b9ab-153">![Head gaze cursor voice](images/head-gaze-cursor-voice.png)</span></span><br>
        <span data-ttu-id="2b9ab-154">**Curseur en tête avec commande vocale**</span><span class="sxs-lookup"><span data-stu-id="2b9ab-154">**Head-gaze cursor with voice command**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="cursor-customization-recommendations"></a><span data-ttu-id="2b9ab-155">Recommandations sur la personnalisation des curseurs</span><span class="sxs-lookup"><span data-stu-id="2b9ab-155">Cursor customization recommendations</span></span>

<span data-ttu-id="2b9ab-156">Si vous souhaitez personnaliser les comportements et les apparences de commentaires des curseurs, voici quelques recommandations en matière de conception :</span><span class="sxs-lookup"><span data-stu-id="2b9ab-156">If you would like to customize the cursor feedback behaviors and appearances, here are some design recommendations:</span></span>

### <a name="cursor-scale"></a><span data-ttu-id="2b9ab-157">Échelle du curseur</span><span class="sxs-lookup"><span data-stu-id="2b9ab-157">Cursor scale</span></span>

* <span data-ttu-id="2b9ab-158">Le curseur ne doit pas être plus grand que les cibles disponibles, ce qui permet aux utilisateurs d’interagir facilement avec et d’afficher le contenu.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-158">The cursor should be no larger than the available targets, allowing users to easily interact with and view the content.</span></span>
* <span data-ttu-id="2b9ab-159">En fonction de l’expérience que vous créez, il est également important de mettre à l’échelle le curseur à mesure que l’utilisateur regarde.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-159">Depending on the experience you create, scaling the cursor as the user looks around is also an important consideration.</span></span> <span data-ttu-id="2b9ab-160">Par exemple, à mesure que l’utilisateur regarde plus loin dans votre expérience, le curseur ne doit pas être trop petit pour être perdu.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-160">For example, as the user looks further away in your experience, the cursor shouldn't become too small such that it's lost.</span></span>
* <span data-ttu-id="2b9ab-161">Lors de la mise à l’échelle du curseur, envisagez d’appliquer une animation douce à celle-ci lorsqu’il est mis à l’échelle pour lui attribuer une sensation organique.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-161">When scaling the cursor, consider applying a soft animation to it as it scales to give it an organic feeling.</span></span>
* <span data-ttu-id="2b9ab-162">Évitez d’obstruer le contenu.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-162">Avoid obstructing content.</span></span> <span data-ttu-id="2b9ab-163">Les hologrammes sont ce qui rend l’expérience mémorable et le curseur ne doit pas être pris en charge.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-163">Holograms are what make the experience memorable and the cursor shouldn't be taking away from them.</span></span>

### <a name="directionless-cursor-shape"></a><span data-ttu-id="2b9ab-164">Forme de curseur dédirectionnelle</span><span class="sxs-lookup"><span data-stu-id="2b9ab-164">Directionless cursor shape</span></span>

* <span data-ttu-id="2b9ab-165">Bien qu’il n’y ait pas de forme de curseur droite, nous vous recommandons d’utiliser une forme sans direction comme un tore.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-165">Although there's no one right cursor shape, we recommend that you use a directionless shape like a torus.</span></span> <span data-ttu-id="2b9ab-166">Un curseur qui pointe dans une certaine direction (par exemple, un curseur en forme de flèche traditionnel) peut dérouter l’utilisateur pour qu’il se présente toujours de cette façon.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-166">A cursor that points in some direction (For example, a traditional arrow cursor) might confuse the user to always look that way.</span></span>
* <span data-ttu-id="2b9ab-167">Une exception est lors de l’utilisation du curseur pour communiquer des instructions d’interaction à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-167">An exception to this is when using the cursor to communicate interaction instruction to the user.</span></span> <span data-ttu-id="2b9ab-168">Par exemple, lors de la mise à l’échelle d’hologrammes dans le système d’exploitation de réalité mixte, le curseur comprend temporairement des flèches qui indiquent à l’utilisateur comment déplacer sa main pour mettre l’hologramme à l’échelle.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-168">For example, when scaling holograms in the Mixed Reality OS, the cursor temporarily includes arrows that instructs the user on how to move their hand to scale the hologram.</span></span>

### <a name="look-and-feel"></a><span data-ttu-id="2b9ab-169">Apparence</span><span class="sxs-lookup"><span data-stu-id="2b9ab-169">Look and feel</span></span>

* <span data-ttu-id="2b9ab-170">Un curseur en forme de bouée ou de Tore fonctionne pour de nombreuses applications.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-170">A donut or torus shaped cursor works for many applications.</span></span>
* <span data-ttu-id="2b9ab-171">Choisissez une couleur et une forme qui correspond le mieux à l’expérience que vous créez.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-171">Pick a color and shape that best represents the experience you're creating.</span></span>
* <span data-ttu-id="2b9ab-172">Les curseurs sont particulièrement sujets à la [séparation des couleurs](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation).</span><span class="sxs-lookup"><span data-stu-id="2b9ab-172">Cursors are especially prone to [color separation](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation).</span></span>
* <span data-ttu-id="2b9ab-173">Un petit curseur avec une opacité équilibrée conserve l’information, sans qui prennent la hiérarchie visuelle.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-173">A small cursor with balanced opacity keeps it informative without dominating the visual hierarchy.</span></span>
* <span data-ttu-id="2b9ab-174">Soyez Cognizant de l’utilisation des ombres ou des surbrillances derrière votre curseur, car elles peuvent entraver le contenu et nuire à la tâche en cours.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-174">Be cognizant of using shadows or highlights behind your cursor as they might obstruct content and distract from the task at hand.</span></span>
* <span data-ttu-id="2b9ab-175">Les curseurs doivent s’aligner sur les surfaces et les étreinter dans votre application.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-175">Cursors should align to and hug the surfaces in your app.</span></span> <span data-ttu-id="2b9ab-176">Les utilisateurs ont le sentiment que le système peut voir où ils regardent, mais également que le système est conscient de leur environnement.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-176">Users will have a feeling that the system can see where they're looking, but also that the system is aware of their surroundings.</span></span> <span data-ttu-id="2b9ab-177">Par exemple, le curseur dans le système d’exploitation de réalité mixte s’aligne sur les surfaces du monde de l’utilisateur, ce qui crée un sentiment de conscience du monde même lorsque l’utilisateur n’regarde pas directement sur un hologramme.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-177">For example, the cursor in the Mixed Reality OS aligns to the surfaces of the user's world, creating a feeling of awareness of the world even when the user isn't looking directly at a hologram.</span></span>
* <span data-ttu-id="2b9ab-178">Le verrouillage magnétique du curseur sur un élément interactif lorsqu’il est proche de l’utilisateur peut contribuer à améliorer la confiance que l’utilisateur interagit avec cet élément lorsqu’il utilise une action de sélection.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-178">Magnetically locking the cursor to an interactive element when it's close to the user can help improve confidence that user will interact with that element when they use a selection action.</span></span>

### <a name="visual-cues"></a><span data-ttu-id="2b9ab-179">Signaux visuels</span><span class="sxs-lookup"><span data-stu-id="2b9ab-179">Visual cues</span></span>

* <span data-ttu-id="2b9ab-180">Si votre expérience est axée sur un seul hologramme, votre curseur doit s’aligner sur cet hologramme et changer de forme lorsque vous examinez l’hologramme.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-180">If your experience is focused on a single hologram, your cursor should align and hug only that hologram and change shape when you look away from that hologram.</span></span> <span data-ttu-id="2b9ab-181">Cela peut indiquer à l’utilisateur que l’hologramme est actionnable et qu’il peut interagir avec lui.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-181">This can convey to the user that the hologram is actionable and they can interact with it.</span></span>
* <span data-ttu-id="2b9ab-182">Si votre application utilise le mappage spatial, votre curseur peut s’aligner sur chaque surface visible.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-182">If your application uses spatial mapping, then your cursor could align and hug every surface it sees.</span></span> <span data-ttu-id="2b9ab-183">Ainsi, les utilisateurs peuvent voir que HoloLens et votre application peuvent voir leur espace.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-183">This gives feedback to the users that HoloLens and your application can see their space.</span></span> <span data-ttu-id="2b9ab-184">Cela renforce le fait que les hologrammes sont réels et dans notre monde et permet de combler le fossé entre les véritables et les virtuels.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-184">This reinforces the fact that holograms are real and in our world and helps bridge the gap between real and virtual.</span></span>
* <span data-ttu-id="2b9ab-185">Avoir une idée de ce que le curseur doit faire lorsqu’il n’y a pas d’hologrammes ou de surfaces en vue.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-185">Have an idea of what the cursor should do when there are no holograms or surfaces in view.</span></span> <span data-ttu-id="2b9ab-186">La placer à une distance prédéterminée devant l’utilisateur est une option.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-186">Placing it at a predetermined distance in front of the user is one option.</span></span>

### <a name="possible-actions"></a><span data-ttu-id="2b9ab-187">Actions possibles</span><span class="sxs-lookup"><span data-stu-id="2b9ab-187">Possible actions</span></span>

* <span data-ttu-id="2b9ab-188">Le curseur peut être représenté par différentes icônes pour acheminer les actions possibles d’un hologramme, par exemple la mise à l’échelle ou la rotation.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-188">The cursor can be represented by different icons to convey possible actions a hologram can do, such as scaling or rotation.</span></span>
* <span data-ttu-id="2b9ab-189">Ajoutez uniquement des informations supplémentaires sur le curseur si cela revient à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-189">Only add extra information on the cursor if it means something to the user.</span></span> <span data-ttu-id="2b9ab-190">Dans le cas contraire, les utilisateurs peuvent ne pas remarquer les modifications d’État ou être confondus par le curseur.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-190">Otherwise, users might either not notice the state changes or get confused by the cursor.</span></span>

### <a name="input-state"></a><span data-ttu-id="2b9ab-191">État d’entrée</span><span class="sxs-lookup"><span data-stu-id="2b9ab-191">Input state</span></span>

* <span data-ttu-id="2b9ab-192">Nous pourrions utiliser le curseur pour afficher l’état d’entrée ou l’intention de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-192">We could use the cursor to display the user's input state or intent.</span></span> <span data-ttu-id="2b9ab-193">Par exemple, nous pourrions afficher une icône indiquant à l’utilisateur que le système voit son état main et que l’application sait qu’il est prêt à agir.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-193">For example, we could display an icon telling the user the system sees their hand state and that the application knows they're ready to take action.</span></span>
* <span data-ttu-id="2b9ab-194">Nous pourrions également utiliser le curseur pour montrer aux utilisateurs que des commandes vocales ont été entendues par le système par le biais d’une modification de couleur momentanée</span><span class="sxs-lookup"><span data-stu-id="2b9ab-194">We could also use the cursor to show users that voice commands have been heard by the system via a momentary color change</span></span>

* <span data-ttu-id="2b9ab-195">Les États de curseur suivants peuvent être implémentés de différentes façons.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-195">The following cursor states can be implemented in different ways.</span></span> <span data-ttu-id="2b9ab-196">Vous pouvez implémenter ces différents États en modélisant le curseur comme une machine à États.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-196">You might implement these different states by modeling the cursor like a state machine.</span></span> <span data-ttu-id="2b9ab-197">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="2b9ab-197">For example:</span></span>
    * <span data-ttu-id="2b9ab-198">L’état inactif est l’endroit où vous affichez le curseur par défaut.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-198">Idle state is where you show the default cursor.</span></span>
    * <span data-ttu-id="2b9ab-199">L’état prêt est lorsque vous avez détecté la main de l’utilisateur en position prête.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-199">Ready state is when you've detected the user's hand in the ready position.</span></span>
    * <span data-ttu-id="2b9ab-200">L’état de l’interaction est lorsque l’utilisateur fait une interaction particulière.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-200">Interaction state is when the user is doing a particular interaction.</span></span>
    * <span data-ttu-id="2b9ab-201">L’état des actions possibles ou l’état de survol est lorsque vous transmettent des actions possibles qui peuvent être effectuées sur un hologramme.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-201">Possible Actions state or hover state is when you convey possible actions that can be performed on a hologram.</span></span>

<span data-ttu-id="2b9ab-202">Vous pouvez également implémenter ces États en vue d’une apparence pour afficher différentes ressources d’art lorsque vous détectez des États différents.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-202">You could also implement these states in a skin-able manner to display different art assets when you detect different states.</span></span>

<br>

---

## <a name="going-cursor-free"></a><span data-ttu-id="2b9ab-203">Passage en « sans curseur »</span><span class="sxs-lookup"><span data-stu-id="2b9ab-203">Going "cursor-free"</span></span>

<span data-ttu-id="2b9ab-204">La conception sans curseur est recommandée lorsque le sens de l’immersion est un composant clé d’une expérience et lorsque les interactions de pointage (par le point de regard et le mouvement) ne nécessitent pas de précision.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-204">Designing without a cursor is recommended when the sense of immersion is a key component of an experience and when pointing interactions (through gaze and gesture) don't require great precision.</span></span> <span data-ttu-id="2b9ab-205">Le système doit toujours répondre aux exigences normales d’un curseur : fournir aux utilisateurs des commentaires continus sur la compréhension de leur point de vue par le système et les aider à communiquer leurs intentions au système.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-205">The system still needs to meet the normal requirements of a cursor: providing users with continuous feedback on the system's understanding of their pointing, and helping them to communicate their intentions to the system.</span></span> <span data-ttu-id="2b9ab-206">Cela peut être réalisable par d’autres changements d’État perceptibles.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-206">This may be achievable through other noticeable state changes.</span></span>

<br>

---

## <a name="cursor-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="2b9ab-207">Curseur dans MRTK (ensemble d’outils de réalité mixte) pour Unity</span><span class="sxs-lookup"><span data-stu-id="2b9ab-207">Cursor in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="2b9ab-208">Par défaut, [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) fournit un Prefab de curseur ([DefaultCursor. Prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) qui a le même état visuel que le curseur système de l’interpréteur de commandes.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-208">By default, [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides a cursor prefab([DefaultCursor.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) which has the same visual state as the shell's system cursor.</span></span> <span data-ttu-id="2b9ab-209">Il est attribué dans le profil d’entrée de MRTK, sous Pointeurs.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-209">It's assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="2b9ab-210">Vous pouvez remplacer/personnaliser ce curseur pour votre expérience.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-210">You can replace/customize this cursor for your experience.</span></span> <span data-ttu-id="2b9ab-211">Pour l’expérience avec l’entrée de suivi oculaire, MRTK fournit également EyeGazeCursor, qui a un visuel subtil pour réduire la distraction.</span><span class="sxs-lookup"><span data-stu-id="2b9ab-211">For the experience with eye-tracking input, MRTK also provides EyeGazeCursor, which has subtle visual to minimize the distraction.</span></span>

* [<span data-ttu-id="2b9ab-212">MRTK - Profil de pointeur</span><span class="sxs-lookup"><span data-stu-id="2b9ab-212">MRTK - Pointer profile</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html#pointer-configuration)
* [<span data-ttu-id="2b9ab-213">MRTK - Système d’entrée</span><span class="sxs-lookup"><span data-stu-id="2b9ab-213">MRTK - Input system</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)
* [<span data-ttu-id="2b9ab-214">MRTK - Pointeurs</span><span class="sxs-lookup"><span data-stu-id="2b9ab-214">MRTK - Pointers</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html)

---

## <a name="see-also"></a><span data-ttu-id="2b9ab-215">Voir également</span><span class="sxs-lookup"><span data-stu-id="2b9ab-215">See also</span></span>

* [<span data-ttu-id="2b9ab-216">Mouvements</span><span class="sxs-lookup"><span data-stu-id="2b9ab-216">Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="2b9ab-217">Suivre de la tête et valider</span><span class="sxs-lookup"><span data-stu-id="2b9ab-217">Head-gaze and commit</span></span>](gaze-and-commit.md)