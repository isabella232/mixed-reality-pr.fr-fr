---
title: Qu’est-ce qu’un hologramme ?
description: HoloLens vous permet d’afficher et d’interagir avec des hologrammes à trois dimensions, des objets composés de lumière et de son qui s’affichent dans le monde autour de vous.
author: hferrone
ms.author: v-hferrone
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, hologrammes, conception, interaction, casque de réalité mixte, casque Windows Mixed Reality, qu’est-ce que la réalité augmente
ms.openlocfilehash: cc6b4a4838e7a275b1ef3a45e54c4b894a04b9c2
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583341"
---
# <a name="what-is-a-hologram"></a><span data-ttu-id="a11a5-104">Qu’est-ce qu’un hologramme ?</span><span class="sxs-lookup"><span data-stu-id="a11a5-104">What is a hologram?</span></span>

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


<span data-ttu-id="a11a5-105">HoloLens vous permet de créer des **hologrammes**, qui sont des objets composés de lumière et de son qui s’affichent dans le monde autour des objets réels.</span><span class="sxs-lookup"><span data-stu-id="a11a5-105">HoloLens lets you create **holograms**, which are objects made of light and sound that appear in the world around you like real objects.</span></span> <span data-ttu-id="a11a5-106">Les hologrammes répondent à [votre point de vue](../design/gaze-and-commit.md), aux [gestes](../design/gaze-and-commit.md#composite-gestures)et aux [commandes vocales](../design/voice-input.md).</span><span class="sxs-lookup"><span data-stu-id="a11a5-106">Holograms respond to your [gaze](../design/gaze-and-commit.md), [gestures](../design/gaze-and-commit.md#composite-gestures), and [voice commands](../design/voice-input.md).</span></span> <span data-ttu-id="a11a5-107">Ils peuvent même interagir avec des [surfaces réelles autour de](../design/spatial-mapping.md) vous.</span><span class="sxs-lookup"><span data-stu-id="a11a5-107">They can even interact with [real-world surfaces](../design/spatial-mapping.md) around you.</span></span> <span data-ttu-id="a11a5-108">Avec les hologrammes, vous pouvez créer des objets numériques qui font partie de votre monde.</span><span class="sxs-lookup"><span data-stu-id="a11a5-108">With holograms, you can create digital objects that are part of your world.</span></span>

<br>

## <a name="device-support"></a><span data-ttu-id="a11a5-109">Prise en charge des appareils</span><span class="sxs-lookup"><span data-stu-id="a11a5-109">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a11a5-110"><strong>Fonctionnalité</strong></span><span class="sxs-lookup"><span data-stu-id="a11a5-110"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="a11a5-111"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1ère génération)</strong></a></span><span class="sxs-lookup"><span data-stu-id="a11a5-111"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="a11a5-112"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="a11a5-112"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="a11a5-113"><a href="../discover/immersive-headset-hardware-details.md"><strong>Casques immersifs</strong></a></span><span class="sxs-lookup"><span data-stu-id="a11a5-113"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a11a5-114">Hologrammes</span><span class="sxs-lookup"><span data-stu-id="a11a5-114">Holograms</span></span></td>
        <td><span data-ttu-id="a11a5-115">✔️</span><span class="sxs-lookup"><span data-stu-id="a11a5-115">✔️</span></span></td>
        <td><span data-ttu-id="a11a5-116">✔️</span><span class="sxs-lookup"><span data-stu-id="a11a5-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

<br>

---

## <a name="a-hologram-is-made-of-light-and-sound"></a><span data-ttu-id="a11a5-117">Un hologramme est composé de lumière et de son</span><span class="sxs-lookup"><span data-stu-id="a11a5-117">A hologram is made of light and sound</span></span>

<span data-ttu-id="a11a5-118">Les hologrammes que le [contrôle HoloLens affiche](../develop/platform-capabilities-and-apis/rendering.md) dans le cadre holographique directement devant les yeux de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a11a5-118">The holograms that HoloLens [renders](../develop/platform-capabilities-and-apis/rendering.md) appear in the holographic frame directly in front of the user's eyes.</span></span> <span data-ttu-id="a11a5-119">Les hologrammes ajoutent de la lumière à votre monde, ce qui signifie que vous voyez la lumière de l’écran et la lumière de votre environnement.</span><span class="sxs-lookup"><span data-stu-id="a11a5-119">Holograms add light to your world, which means that you see both the light from the display and the light from your surroundings.</span></span> <span data-ttu-id="a11a5-120">HoloLens ne disposant pas de lumière sur vos yeux, les hologrammes ne peuvent pas être rendus avec la couleur noire.</span><span class="sxs-lookup"><span data-stu-id="a11a5-120">HoloLens doesn't remove light from your eyes, so holograms can't be rendered with the color black.</span></span> <span data-ttu-id="a11a5-121">Au lieu de cela, le contenu noir apparaît comme transparent.</span><span class="sxs-lookup"><span data-stu-id="a11a5-121">Instead, black content appears as transparent.</span></span>

<span data-ttu-id="a11a5-122">Les hologrammes peuvent avoir de nombreuses apparences et comportements différents.</span><span class="sxs-lookup"><span data-stu-id="a11a5-122">Holograms can have many different appearances and behaviors.</span></span> <span data-ttu-id="a11a5-123">Certains sont réalistes et solides, tandis que d’autres sont animés et Ethereal.</span><span class="sxs-lookup"><span data-stu-id="a11a5-123">Some are realistic and solid, and others are cartoonish and ethereal.</span></span> <span data-ttu-id="a11a5-124">Vous pouvez utiliser des hologrammes pour mettre en évidence des fonctionnalités dans votre environnement ou les utiliser en tant qu’éléments dans l’interface utilisateur de votre application.</span><span class="sxs-lookup"><span data-stu-id="a11a5-124">You can use holograms to highlight features in your surroundings or use them as elements in your app's user interface.</span></span>

![Mains manipulation d’un hologramme](images/hologram-hands-940px.jpg)

<span data-ttu-id="a11a5-126">Les hologrammes peuvent également créer des [sons](../design/spatial-sound.md)qui semblent provenir d’un emplacement spécifique dans votre environnement.</span><span class="sxs-lookup"><span data-stu-id="a11a5-126">Holograms can also make [sounds](../design/spatial-sound.md), which will appear to come from a specific place in your surroundings.</span></span> <span data-ttu-id="a11a5-127">Sur HoloLens, le son provient de deux enceintes situées directement au-dessus de vos oreilles, sans les couvrir.</span><span class="sxs-lookup"><span data-stu-id="a11a5-127">On HoloLens, sound comes from two speakers that are located directly above your ears, without covering them.</span></span> <span data-ttu-id="a11a5-128">Comme pour les écrans, les haut-parleurs sont additifs, ce qui introduit de nouveaux sons sans bloquer les sons de votre environnement.</span><span class="sxs-lookup"><span data-stu-id="a11a5-128">Similar to the displays, the speakers are additive, introducing new sounds without blocking the sounds from your environment.</span></span>

<br>

---

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a><span data-ttu-id="a11a5-129">Un hologramme peut être placé dans le monde entier ou dans la balise avec vous</span><span class="sxs-lookup"><span data-stu-id="a11a5-129">A hologram can be placed in the world or tag along with you</span></span>

<span data-ttu-id="a11a5-130">Lorsque vous disposez d’un emplacement particulier pour un hologramme, vous pouvez le [Placer](../design/coordinate-systems.md) précisément à cet endroit dans le monde.</span><span class="sxs-lookup"><span data-stu-id="a11a5-130">When you have a particular location for a hologram, you can [place](../design/coordinate-systems.md) it precisely at that point in the world.</span></span> <span data-ttu-id="a11a5-131">Au fur et à mesure que vous parcourez, l’hologramme est stable en fonction du monde qui vous est autour.</span><span class="sxs-lookup"><span data-stu-id="a11a5-131">As you walk around, the hologram appears stable based on the world around you.</span></span> <span data-ttu-id="a11a5-132">Si vous utilisez une [ancre spatiale](../design/coordinate-systems.md#spatial-anchors) pour épingler l’objet, le système peut même vous rappeler où vous l’avez laissé lorsque vous revenez plus tard.</span><span class="sxs-lookup"><span data-stu-id="a11a5-132">If you use a [spatial anchor](../design/coordinate-systems.md#spatial-anchors) to pin the object, the system can even remember where you left it when you come back later.</span></span>

![Deux hommes utilisant la disposition Microsoft Dynamics 365 dans un espace de vente au détail](images/HLS19_retailLayoutHologram_001-940px.jpg)

<span data-ttu-id="a11a5-134">Certains hologrammes suivent l’utilisateur, et se positionnent sur la base de l’utilisateur, quel que soit l’endroit où ils se déplacent.</span><span class="sxs-lookup"><span data-stu-id="a11a5-134">Some holograms follow the user instead, positioning themselves based on the user no matter where they walk.</span></span> <span data-ttu-id="a11a5-135">Vous pouvez même choisir de placer un hologramme avec vous pendant un certain temps, puis le placer sur le mur une fois que vous êtes dans une autre pièce.</span><span class="sxs-lookup"><span data-stu-id="a11a5-135">You may even choose to bring a hologram with you for a while and then place it on the wall once you get to another room.</span></span>

<span data-ttu-id="a11a5-136">**Bonnes pratiques**</span><span class="sxs-lookup"><span data-stu-id="a11a5-136">**Best practices**</span></span>
* <span data-ttu-id="a11a5-137">Certains scénarios peuvent exiger que les hologrammes restent facilement détectables ou visibles tout au long de l’expérience.</span><span class="sxs-lookup"><span data-stu-id="a11a5-137">Some scenarios may demand that holograms remain easily discoverable or visible throughout the experience.</span></span> <span data-ttu-id="a11a5-138">Il existe deux approches de haut niveau pour ce type de positionnement.</span><span class="sxs-lookup"><span data-stu-id="a11a5-138">There are two high-level approaches to this kind of positioning.</span></span> <span data-ttu-id="a11a5-139">Appelons-les **« éléments verrouillés** » et **« verrouillés en corps »**.</span><span class="sxs-lookup"><span data-stu-id="a11a5-139">Let's call them **"display-locked"** and **"body-locked"**.</span></span>
   * <span data-ttu-id="a11a5-140">Le contenu verrouillé en affichage est positionné de façon « verrouillée » sur l’écran de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="a11a5-140">Display-locked content is positionally "locked" to the device display.</span></span> <span data-ttu-id="a11a5-141">Ce type de contenu est délicat pour plusieurs raisons, y compris une sensation innaturelle de « clingyness » qui rend beaucoup d’utilisateurs frustrés et souhaitant les « secouer ».</span><span class="sxs-lookup"><span data-stu-id="a11a5-141">This type of content is tricky for several reasons, including an unnatural feeling of "clingyness" that makes many users frustrated and wanting to "shake it off."</span></span> <span data-ttu-id="a11a5-142">En général, de nombreux concepteurs ont trouvé mieux qu’ils évitent le verrouillage du contenu.</span><span class="sxs-lookup"><span data-stu-id="a11a5-142">In general, many designers have found it better to avoid display-locking content.</span></span>
   * <span data-ttu-id="a11a5-143">L’approche verrouillée par le corps est beaucoup plus forgivable.</span><span class="sxs-lookup"><span data-stu-id="a11a5-143">The body-locked approach is far more forgivable.</span></span> <span data-ttu-id="a11a5-144">Le verrouillage du corps est lorsque vous attachez un hologramme au corps de l’utilisateur ou au point de regard dans l’espace 3D.</span><span class="sxs-lookup"><span data-stu-id="a11a5-144">Body-locking is when you tether a hologram to the user's body or gaze vector in 3d space.</span></span> <span data-ttu-id="a11a5-145">De nombreuses expériences ont adopté un comportement de verrouillage du corps où l’hologramme « suit » les utilisateurs pointant vers le regard, ce qui permet à l’utilisateur de faire pivoter son corps et de parcourir l’espace sans perdre l’hologramme.</span><span class="sxs-lookup"><span data-stu-id="a11a5-145">Many experiences have adopted a body-locking behavior where the hologram "follows" the users gaze, which allows the user to rotate their body and move through space without losing the hologram.</span></span> <span data-ttu-id="a11a5-146">L’incorporation d’un délai permet d’obtenir un mouvement d’hologramme plus naturel.</span><span class="sxs-lookup"><span data-stu-id="a11a5-146">Incorporating a delay helps the hologram movement feel more natural.</span></span> <span data-ttu-id="a11a5-147">Par exemple, une interface utilisateur principale du système d’exploitation Windows holographique utilise une variation sur le verrouillage du corps qui suit le point d’arrêt de l’utilisateur avec un délai léger et élastique, tandis que l’utilisateur change de tête.</span><span class="sxs-lookup"><span data-stu-id="a11a5-147">For example, some core UI of the Windows Holographic OS uses a variation on body-locking that follows the user's gaze with a gentle, elastic-like delay while the user turns their head.</span></span>
* <span data-ttu-id="a11a5-148">Placez l’hologramme à une distance confortable, généralement d’environ 1-2 mètres de l’en-tête.</span><span class="sxs-lookup"><span data-stu-id="a11a5-148">Place the hologram at a comfortable viewing distance typically about 1-2 meters away from the head.</span></span>
* <span data-ttu-id="a11a5-149">Indiquez une valeur de dérive pour les éléments qui doivent être continuellement dans le frame holographique ou envisagez d’animer votre contenu sur un côté de l’affichage lorsque l’utilisateur modifie son point de vue.</span><span class="sxs-lookup"><span data-stu-id="a11a5-149">Provide a drift amount for elements that must be continually in the holographic frame, or consider animating your content to one side of the display when the user changes their point of view.</span></span>

<span data-ttu-id="a11a5-150">**Placer des hologrammes dans la zone optimale (entre 1,25 m et 5 mètres)**</span><span class="sxs-lookup"><span data-stu-id="a11a5-150">**Place holograms in the optimal zone - between 1.25 m and 5 m**</span></span>

<span data-ttu-id="a11a5-151">Deux compteurs sont les plus optimaux et l’expérience dégradera la plus proche que vous obteniez de 1 mètre.</span><span class="sxs-lookup"><span data-stu-id="a11a5-151">Two meters is the most optimal, and the experience will degrade the closer you get from 1 meter.</span></span> <span data-ttu-id="a11a5-152">À des distances plus proches que 1 mètre, les hologrammes qui se déplacent régulièrement sont plus susceptibles d’être problématiques que les hologrammes fixes.</span><span class="sxs-lookup"><span data-stu-id="a11a5-152">At distances nearer than 1 meter, holograms that regularly move in depth are more likely to be problematic than stationary holograms.</span></span> <span data-ttu-id="a11a5-153">Envisagez de découper ou d’inverser correctement votre contenu quand celui-ci est trop proche, ce qui vous évite d’avoir à l’utilisateur une expérience inattendue.</span><span class="sxs-lookup"><span data-stu-id="a11a5-153">Consider gracefully clipping or fading out your content when it gets too close so you don't jar the user into an unexpected experience.</span></span>

![Distance optimale pour le placement des hologrammes de l’utilisateur.](images/distanceguiderendering-950px.png)

<br>

---

## <a name="a-hologram-interacts-with-you-and-your-world"></a><span data-ttu-id="a11a5-155">Un hologramme interagit avec vous et votre monde</span><span class="sxs-lookup"><span data-stu-id="a11a5-155">A hologram interacts with you and your world</span></span>

<span data-ttu-id="a11a5-156">Les hologrammes ne sont pas uniquement à l’égard du clair et du son. ils sont également une partie active de votre monde.</span><span class="sxs-lookup"><span data-stu-id="a11a5-156">Holograms aren't only about light and sound; they're also an active part of your world.</span></span> <span data-ttu-id="a11a5-157">Pointez le regard sur un hologramme et un geste avec votre main, et un hologramme peut commencer à vous suivre.</span><span class="sxs-lookup"><span data-stu-id="a11a5-157">Gaze at a hologram and gesture with your hand, and a hologram can start to follow you.</span></span> <span data-ttu-id="a11a5-158">Donnez une commande vocale à un hologramme, qui peut répondre.</span><span class="sxs-lookup"><span data-stu-id="a11a5-158">Give a voice command to a hologram, and it can reply.</span></span>

![Groupe de travailleurs utilitaires gouvernementaux utilisant Microsoft HoloLens 2 pour collaborer sur un projet de développement de batterie de serveurs vent](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

<span data-ttu-id="a11a5-160">Les hologrammes permettent des interactions personnelles qui ne sont pas possibles ailleurs.</span><span class="sxs-lookup"><span data-stu-id="a11a5-160">Holograms enable personal interactions that aren't possible elsewhere.</span></span> <span data-ttu-id="a11a5-161">Étant donné que le HoloLens sait où il se trouve dans le monde, un caractère holographique peut vous paraître directement dans les yeux à mesure que vous parcourez la salle.</span><span class="sxs-lookup"><span data-stu-id="a11a5-161">Because the HoloLens knows where it is in the world, a holographic character can look you directly in the eyes as you walk around the room.</span></span>

<span data-ttu-id="a11a5-162">Un hologramme peut également interagir avec votre environnement.</span><span class="sxs-lookup"><span data-stu-id="a11a5-162">A hologram can also interact with your surroundings.</span></span> <span data-ttu-id="a11a5-163">Par exemple, vous pouvez placer une boule de rebond holographique au-dessus d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="a11a5-163">For example, you can place a holographic bouncing ball above a table.</span></span> <span data-ttu-id="a11a5-164">Puis, avec le [robinet](../design/gaze-and-commit.md#composite-gestures), regardez la balle rebondir et émettez un son lorsqu’il atteint la table.</span><span class="sxs-lookup"><span data-stu-id="a11a5-164">Then, with an [air tap](../design/gaze-and-commit.md#composite-gestures), watch the ball bounce, and make sound when it hits the table.</span></span>

<span data-ttu-id="a11a5-165">Les hologrammes peuvent également être bloqués par des objets réels.</span><span class="sxs-lookup"><span data-stu-id="a11a5-165">Holograms can also be occluded by real-world objects.</span></span> <span data-ttu-id="a11a5-166">Par exemple, un caractère holographique peut parcourir une porte et derrière un mur, en dehors de votre vue.</span><span class="sxs-lookup"><span data-stu-id="a11a5-166">For example, a holographic character might walk through a door and behind a wall, out of your sight.</span></span>

<span data-ttu-id="a11a5-167">**Conseils pour l’intégration des hologrammes et du monde réel**</span><span class="sxs-lookup"><span data-stu-id="a11a5-167">**Tips for integrating holograms and the real world**</span></span>
* <span data-ttu-id="a11a5-168">L’alignement sur les règles gravitationnelles facilite la liaison des hologrammes à et plus crédible.</span><span class="sxs-lookup"><span data-stu-id="a11a5-168">Aligning to gravitational rules makes holograms easier to relate to and more believable.</span></span> <span data-ttu-id="a11a5-169">par exemple : Placez un chien holographique sur le sol & un vase sur la table au lieu de le faire flotter dans l’espace.</span><span class="sxs-lookup"><span data-stu-id="a11a5-169">for example: Place a holographic dog on the ground & a vase on the table rather than have them floating in space.</span></span>
* <span data-ttu-id="a11a5-170">De nombreux concepteurs ont découvert qu’ils peuvent intégrer des hologrammes plus incroyables en créant une « ombre négative » sur la surface sur laquelle l’hologramme est assis.</span><span class="sxs-lookup"><span data-stu-id="a11a5-170">Many designers have found that they can integrate more believable holograms by creating a "negative shadow" on the surface that the hologram is sitting on.</span></span> <span data-ttu-id="a11a5-171">Pour ce faire, ils créent une lueur douce sur le sol autour de l’hologramme, puis soustraient la « ombre » de la lueur.</span><span class="sxs-lookup"><span data-stu-id="a11a5-171">They do this by creating a soft glow on the ground around the hologram and then subtracting the "shadow" from the glow.</span></span> <span data-ttu-id="a11a5-172">La lueur douce s’intègre à la lumière du monde réel, qui utilise l’ombre pour refondre l’hologramme dans l’environnement.</span><span class="sxs-lookup"><span data-stu-id="a11a5-172">The soft glow integrates with the light from the real world, which uses the shadow to ground the hologram in the environment.</span></span>

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-whatever-bryou-can-dream-upbr"></a><span data-ttu-id="a11a5-173">Un hologramme est tout ce que</span><span class="sxs-lookup"><span data-stu-id="a11a5-173">A hologram is whatever</span></span> <br><span data-ttu-id="a11a5-174">vous pouvez rêver</span><span class="sxs-lookup"><span data-stu-id="a11a5-174">you can dream up</span></span><br>
        <span data-ttu-id="a11a5-175">En tant que développeur holographique, vous avez la possibilité de scinder votre créativité en écrans 2D et dans le monde entier.</span><span class="sxs-lookup"><span data-stu-id="a11a5-175">As a holographic developer, you have the power to break your creativity out of 2D screens and into the world around you.</span></span><br><br>
        <span data-ttu-id="a11a5-176">Que allez- *vous* générer ?</span><span class="sxs-lookup"><span data-stu-id="a11a5-176">What will *you* build?</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="a11a5-177">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="a11a5-177">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="a11a5-178">![Monde imaginaire imaginaire dans le salon](images/designoverview.jpg)</span><span class="sxs-lookup"><span data-stu-id="a11a5-178">![Holographic imaginary world in living room](images/designoverview.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="next-discovery-checkpoint"></a><span data-ttu-id="a11a5-179">Point de contrôle de découverte suivant</span><span class="sxs-lookup"><span data-stu-id="a11a5-179">Next Discovery Checkpoint</span></span>

<span data-ttu-id="a11a5-180">Si vous suivez le [parcours de découverte](get-started-with-mr.md) que nous avons établi, vous êtes au cœur de l’exploration des concepts de base de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="a11a5-180">If you're following the [discovery journey](get-started-with-mr.md) we've laid out, you're in the midst of exploring the basics of Mixed Reality.</span></span> <span data-ttu-id="a11a5-181">À partir de là, vous pouvez passer au sujet suivant :</span><span class="sxs-lookup"><span data-stu-id="a11a5-181">From here, you can continue to the next foundational topic:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="a11a5-182">Développer votre processus de conception</span><span class="sxs-lookup"><span data-stu-id="a11a5-182">Expand your design process</span></span>](case-study-expanding-the-design-process-for-mixed-reality.md)