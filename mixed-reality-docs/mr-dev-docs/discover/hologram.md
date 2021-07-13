---
title: Qu’est-ce qu’un hologramme ?
description: HoloLens vous permet d’afficher et d’interagir avec des hologrammes à trois dimensions, des objets composés de lumière et de son qui s’affichent dans le monde autour de vous.
author: qianw211
ms.author: v-qianwen
ms.date: 07/09/2021
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, hologrammes, conception, interaction, casque de réalité mixte, casque Windows mixed reality, qu’est-ce que la réalité augmente
ms.openlocfilehash: bef2c378dcba54d3ed3da33262153f35d72c3cba
ms.sourcegitcommit: b0b49ad27a0d09eb0a3d5df0c766bb4b7bbd8208
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2021
ms.locfileid: "113634330"
---
# <a name="what-is-a-hologram"></a><span data-ttu-id="ed104-104">Qu’est-ce qu’un hologramme ?</span><span class="sxs-lookup"><span data-stu-id="ed104-104">What is a hologram?</span></span>

<span data-ttu-id="ed104-105">HoloLens vous permet d’afficher des **hologrammes**, qui sont des objets composés de lumière et de son qui s’affichent dans le monde autour des objets réels.</span><span class="sxs-lookup"><span data-stu-id="ed104-105">HoloLens lets you view **holograms**, which are objects made of light and sound that appear in the world around you like real objects.</span></span> <span data-ttu-id="ed104-106">Hologrammes pouvez répondre [à vos](../design/gaze-and-commit.md)commandes de pointage, de [mouvement](../design/gaze-and-commit.md#composite-gestures)et de [voix](../design/voice-input.md).</span><span class="sxs-lookup"><span data-stu-id="ed104-106">Holograms can respond to your [gaze](../design/gaze-and-commit.md), [gestures](../design/gaze-and-commit.md#composite-gestures), and [voice commands](../design/voice-input.md).</span></span> <span data-ttu-id="ed104-107">Ils peuvent même interagir avec des [surfaces réelles autour de](../design/spatial-mapping.md) vous.</span><span class="sxs-lookup"><span data-stu-id="ed104-107">They can even interact with [real-world surfaces](../design/spatial-mapping.md) around you.</span></span> <span data-ttu-id="ed104-108">Hologrammes sont des objets numériques qui font partie de votre monde.</span><span class="sxs-lookup"><span data-stu-id="ed104-108">Holograms are digital objects that are part of your world.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

## <a name="device-support"></a><span data-ttu-id="ed104-109">Prise en charge des appareils</span><span class="sxs-lookup"><span data-stu-id="ed104-109">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="ed104-110"><strong>Fonctionnalité</strong></span><span class="sxs-lookup"><span data-stu-id="ed104-110"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="ed104-111"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1ère génération)</strong></a></span><span class="sxs-lookup"><span data-stu-id="ed104-111"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="ed104-112"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="ed104-112"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="ed104-113"><a href="../discover/immersive-headset-hardware-details.md"><strong>Casques immersifs</strong></a></span><span class="sxs-lookup"><span data-stu-id="ed104-113"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="ed104-114">Hologrammes</span><span class="sxs-lookup"><span data-stu-id="ed104-114">Holograms</span></span></td>
        <td><span data-ttu-id="ed104-115">✔️</span><span class="sxs-lookup"><span data-stu-id="ed104-115">✔️</span></span></td>
        <td><span data-ttu-id="ed104-116">✔️</span><span class="sxs-lookup"><span data-stu-id="ed104-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

<br>

---

## <a name="a-hologram-is-made-of-light-and-sound"></a><span data-ttu-id="ed104-117">Un hologramme est composé de lumière et de son</span><span class="sxs-lookup"><span data-stu-id="ed104-117">A hologram is made of light and sound</span></span>

### <a name="light"></a><span data-ttu-id="ed104-118">Clair</span><span class="sxs-lookup"><span data-stu-id="ed104-118">Light</span></span>

<span data-ttu-id="ed104-119">les hologrammes [que HoloLens](../develop/platform-capabilities-and-apis/rendering.md) affichent dans le cadre holographique directement devant les yeux des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="ed104-119">The holograms that HoloLens [renders](../develop/platform-capabilities-and-apis/rendering.md) appear in the holographic frame directly in front of users' eyes.</span></span> <span data-ttu-id="ed104-120">Hologrammes ajouter de la lumière à votre monde, ce qui signifie que vous voyez la lumière de l’écran et la lumière de votre monde environnant.</span><span class="sxs-lookup"><span data-stu-id="ed104-120">Holograms add light to your world, which means that you see both the light from the display and the light from your surrounding world.</span></span> <span data-ttu-id="ed104-121">étant donné que HoloLens utilise un affichage additif qui ajoute de la lumière, la couleur noire est rendue transparente.</span><span class="sxs-lookup"><span data-stu-id="ed104-121">Since HoloLens uses an additive display that adds light, the black color will be rendered transparent.</span></span> 

<span data-ttu-id="ed104-122">Hologrammes peut avoir des apparences et des comportements très différents.</span><span class="sxs-lookup"><span data-stu-id="ed104-122">Holograms can have very different appearances and behaviors.</span></span> <span data-ttu-id="ed104-123">Certains sont réalistes et solides, tandis que d’autres sont animés et Ethereal.</span><span class="sxs-lookup"><span data-stu-id="ed104-123">Some are realistic and solid, and others are cartoonish and ethereal.</span></span> <span data-ttu-id="ed104-124">Vous pouvez utiliser des hologrammes pour mettre en évidence les fonctionnalités de votre environnement ou les utiliser en tant qu’éléments dans l’interface utilisateur de votre application.</span><span class="sxs-lookup"><span data-stu-id="ed104-124">You can use holograms to highlight features in your environment or use them as elements in your app's user interface.</span></span>

![Mains manipulation d’un hologramme](images/hologram-hands-940px.jpg)

### <a name="sound"></a><span data-ttu-id="ed104-126">Son</span><span class="sxs-lookup"><span data-stu-id="ed104-126">Sound</span></span>

<span data-ttu-id="ed104-127">Hologrammes pouvez également produire des [sons](../design/spatial-sound.md), qui semblent provenir d’un emplacement spécifique dans votre environnement.</span><span class="sxs-lookup"><span data-stu-id="ed104-127">Holograms can also produce [sounds](../design/spatial-sound.md), which appear to come from a specific place in your environment.</span></span> <span data-ttu-id="ed104-128">sur HoloLens, le son provient de deux haut-parleurs situés directement au-dessus de vos oreilles.</span><span class="sxs-lookup"><span data-stu-id="ed104-128">On HoloLens, sound comes from two speakers that are located directly above your ears.</span></span> <span data-ttu-id="ed104-129">Comme les écrans holographiques, les haut-parleurs sont additifs, ce qui introduit de nouveaux sons sans bloquer les sons de votre environnement.</span><span class="sxs-lookup"><span data-stu-id="ed104-129">Same as the holographic displays, the speakers are additive, introducing new sounds without blocking the sounds from your environment.</span></span>

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a><span data-ttu-id="ed104-130">Un hologramme peut être placé dans le monde entier ou dans la balise avec vous</span><span class="sxs-lookup"><span data-stu-id="ed104-130">A hologram can be placed in the world or tag along with you</span></span>

<span data-ttu-id="ed104-131">Lorsque vous disposez d’un emplacement fixe pour un hologramme, vous pouvez le [Placer](../design/coordinate-systems.md) précisément à cet endroit dans le monde.</span><span class="sxs-lookup"><span data-stu-id="ed104-131">When you have a fixed location for a hologram, you can [place](../design/coordinate-systems.md) it precisely at that point in the world.</span></span> <span data-ttu-id="ed104-132">Au fur et à mesure que vous parcourez, l’hologramme s’affiche à l’aide du monde entier, tout comme un objet physique.</span><span class="sxs-lookup"><span data-stu-id="ed104-132">As you walk around, the hologram appears stationary based on the world around you, just like a physical object.</span></span> <span data-ttu-id="ed104-133">Si vous utilisez une [ancre spatiale](../design/coordinate-systems.md#spatial-anchors) pour épingler l’objet, le système peut même vous rappeler où vous l’avez laissé lorsque vous revenez plus tard.</span><span class="sxs-lookup"><span data-stu-id="ed104-133">If you use a [spatial anchor](../design/coordinate-systems.md#spatial-anchors) to pin the object, the system can even remember where you left it when you come back later.</span></span>

![Deux hommes utilisant la disposition Microsoft Dynamics 365 dans un espace de vente au détail](images/HLS19_retailLayoutHologram_001-940px.jpg)

<span data-ttu-id="ed104-135">Certains hologrammes suivent l’utilisateur à la place.</span><span class="sxs-lookup"><span data-stu-id="ed104-135">Some holograms follow the user instead.</span></span> <span data-ttu-id="ed104-136">Ils se positionnent sur la base de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ed104-136">They position themselves based on the user.</span></span> <span data-ttu-id="ed104-137">Vous pouvez choisir de placer un hologramme avec vous, puis le placer sur le mur une fois que vous êtes dans une autre pièce.</span><span class="sxs-lookup"><span data-stu-id="ed104-137">You can choose to bring a hologram with you, and then place it on the wall once you get to another room.</span></span>

<span data-ttu-id="ed104-138">**Bonnes pratiques**</span><span class="sxs-lookup"><span data-stu-id="ed104-138">**Best practices**</span></span>

* <span data-ttu-id="ed104-139">Certains scénarios exigent que les hologrammes restent facilement détectables ou visibles tout au long de l’expérience.</span><span class="sxs-lookup"><span data-stu-id="ed104-139">Some scenarios demand that holograms remain easily discoverable or visible throughout the experience.</span></span> <span data-ttu-id="ed104-140">Il existe deux approches de haut niveau pour ce type de positionnement.</span><span class="sxs-lookup"><span data-stu-id="ed104-140">There are two high-level approaches to this kind of positioning.</span></span> <span data-ttu-id="ed104-141">Appelons-les **en mode verrouillé** et **verrouillé**.</span><span class="sxs-lookup"><span data-stu-id="ed104-141">Let's call them **display-locked** and **body-locked**.</span></span>
   * <span data-ttu-id="ed104-142">Le contenu **verrouillé** est verrouillé sur le périphérique d’affichage.</span><span class="sxs-lookup"><span data-stu-id="ed104-142">**Display-locked** content is locked to the display device.</span></span> <span data-ttu-id="ed104-143">Ce type de contenu est délicat pour plusieurs raisons, y compris une sensation innaturelle de « clingyness » qui rend beaucoup d’utilisateurs frustrés et souhaitant les « secouer ».</span><span class="sxs-lookup"><span data-stu-id="ed104-143">This type of content is tricky for several reasons, including an unnatural feeling of "clingyness" that makes many users frustrated and wanting to "shake it off."</span></span> <span data-ttu-id="ed104-144">En général, les concepteurs ont trouvé qu’il est préférable d’éviter le verrouillage de l’affichage du contenu.</span><span class="sxs-lookup"><span data-stu-id="ed104-144">In general, designers have found it better to avoid display-locking content.</span></span>
   * <span data-ttu-id="ed104-145">**Le contenu verrouillé** peut être beaucoup plus indulgent avec.</span><span class="sxs-lookup"><span data-stu-id="ed104-145">**Body-locked** content can be far more forgiving.</span></span> <span data-ttu-id="ed104-146">Le verrouillage du corps est lorsque vous attachez un hologramme au corps de l’utilisateur ou au point de regard dans l’espace 3D.</span><span class="sxs-lookup"><span data-stu-id="ed104-146">Body-locking is when you tether a hologram to the user's body or gaze vector in 3D space.</span></span> <span data-ttu-id="ed104-147">De nombreuses expériences ont adopté un comportement de verrouillage du corps où l’hologramme suit le regard de l’utilisateur, ce qui permet à l’utilisateur de faire pivoter son corps et de se déplacer dans l’espace sans perdre l’hologramme.</span><span class="sxs-lookup"><span data-stu-id="ed104-147">Many experiences have adopted a body-locking behavior where the hologram follows the user's gaze, which allows the user to rotate their body and move through space without losing the hologram.</span></span> <span data-ttu-id="ed104-148">L’incorporation d’un délai permet aux mouvements d’hologramme de se sentir plus naturels.</span><span class="sxs-lookup"><span data-stu-id="ed104-148">Incorporating a delay helps the hologram movements to feel more natural.</span></span> <span data-ttu-id="ed104-149">par exemple, une interface utilisateur principale du système d’exploitation holographique Windows utilise une variation sur le verrouillage du corps qui suit le point de regard de l’utilisateur avec un délai léger et élastique, tandis que l’utilisateur change de tête.</span><span class="sxs-lookup"><span data-stu-id="ed104-149">For example, some core UI of the Windows Holographic OS uses a variation on body-locking that follows the user's gaze with a gentle, elastic-like delay while the user turns their head.</span></span>
* <span data-ttu-id="ed104-150">Placez l’hologramme à une distance confortable, généralement d’environ 1-2 mètres de l’en-tête.</span><span class="sxs-lookup"><span data-stu-id="ed104-150">Place the hologram at a comfortable viewing distance typically about 1-2 meters away from the head.</span></span>
* <span data-ttu-id="ed104-151">Autorisez la dérive des éléments si elles doivent être continuellement dans le frame holographique ou si vous envisagez de déplacer votre contenu vers l’un des côtés de l’affichage lorsque l’utilisateur modifie son point de vue.</span><span class="sxs-lookup"><span data-stu-id="ed104-151">Allow elements to drift if they must be continually in the holographic frame, or consider moving your content to one side of the display when the user changes their point of view.</span></span> <span data-ttu-id="ed104-152">Pour plus d’informations, consultez la page relative aux [panneaux et aux balises](../design/billboarding-and-tag-along.md) Artilce.</span><span class="sxs-lookup"><span data-stu-id="ed104-152">For more information, see the [billboarding and tag-along](../design/billboarding-and-tag-along.md) artilce.</span></span>

<span data-ttu-id="ed104-153">**Placer des hologrammes dans la zone optimale (entre 1,25 m et 5 mètres)**</span><span class="sxs-lookup"><span data-stu-id="ed104-153">**Place holograms in the optimal zone - between 1.25 m and 5 m**</span></span>

<span data-ttu-id="ed104-154">La distance d’affichage la plus optimale est de deux mètres.</span><span class="sxs-lookup"><span data-stu-id="ed104-154">Two meters is the most optimal viewing distance.</span></span> <span data-ttu-id="ed104-155">L’expérience commence à se dégrader à mesure que vous vous rapprochez de 1 mètre.</span><span class="sxs-lookup"><span data-stu-id="ed104-155">The experience will start to degrade as you get closer than 1 meter.</span></span> <span data-ttu-id="ed104-156">À des distances inférieures à 1 mètre, les hologrammes qui se déplacent régulièrement sont plus susceptibles d’être problématiques que les hologrammes fixes.</span><span class="sxs-lookup"><span data-stu-id="ed104-156">At distances less than 1 meter, holograms that regularly move in depth are more likely to be problematic than stationary holograms.</span></span> <span data-ttu-id="ed104-157">Envisagez de découper ou d’inverser correctement votre contenu quand il est trop proche. vous ne devez donc pas l’utiliser dans une expérience de visualisation désagréable.</span><span class="sxs-lookup"><span data-stu-id="ed104-157">Consider gracefully clipping or fading out your content when it gets too close, so you don't jar the user into an unpleasant viewing experience.</span></span>

![Distance optimale pour le placement des hologrammes de l’utilisateur.](images/distanceguiderendering-950px.png)

<br>

---

## <a name="a-hologram-interacts-with-you-and-your-world"></a><span data-ttu-id="ed104-159">Un hologramme interagit avec vous et votre monde</span><span class="sxs-lookup"><span data-stu-id="ed104-159">A hologram interacts with you and your world</span></span>

<span data-ttu-id="ed104-160">Hologrammes ne sont pas uniquement à l’égard du clair et du son. ils sont également une partie active de votre monde.</span><span class="sxs-lookup"><span data-stu-id="ed104-160">Holograms aren't only about light and sound; they're also an active part of your world.</span></span> <span data-ttu-id="ed104-161">Pointez le regard sur un hologramme et un geste avec votre main, et un hologramme peut commencer à vous suivre.</span><span class="sxs-lookup"><span data-stu-id="ed104-161">Gaze at a hologram and gesture with your hand, and a hologram can start to follow you.</span></span> <span data-ttu-id="ed104-162">Donnez une commande vocale et l’hologramme peut répondre.</span><span class="sxs-lookup"><span data-stu-id="ed104-162">Give a voice command, and the hologram can reply.</span></span>

![groupe de travailleurs de l’utilitaire gouvernemental utilisant Microsoft HoloLens 2 pour collaborer sur un projet de développement de batterie de serveurs vent](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

<span data-ttu-id="ed104-164">Hologrammes activer les interactions personnelles qui ne sont pas possibles ailleurs.</span><span class="sxs-lookup"><span data-stu-id="ed104-164">Holograms enable personal interactions that aren't possible elsewhere.</span></span> <span data-ttu-id="ed104-165">étant donné que le HoloLens sait où il se trouve dans le monde, un caractère holographique peut vous regarder directement dans les yeux et démarrer une conversation avec vous.</span><span class="sxs-lookup"><span data-stu-id="ed104-165">Because the HoloLens knows where it is in the world, a holographic character can look at you directly in the eyes and start a conversation with you.</span></span>

<span data-ttu-id="ed104-166">Un hologramme peut également interagir avec votre environnement.</span><span class="sxs-lookup"><span data-stu-id="ed104-166">A hologram can also interact with your surroundings.</span></span> <span data-ttu-id="ed104-167">Par exemple, vous pouvez placer une boule de rebond holographique au-dessus d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="ed104-167">For example, you can place a holographic bouncing ball above a table.</span></span> <span data-ttu-id="ed104-168">Ensuite, à l’aide d’un [robinet](../design/gaze-and-commit.md#composite-gestures), regardez la balle rebondir et faites sonner le son au fur et à mesure qu’elle touche le tableau.</span><span class="sxs-lookup"><span data-stu-id="ed104-168">Then, with an [air tap](../design/gaze-and-commit.md#composite-gestures), watch the ball bounce, and make sound as it hits the table.</span></span>

<span data-ttu-id="ed104-169">Hologrammes peut également être bloqués par des objets réels.</span><span class="sxs-lookup"><span data-stu-id="ed104-169">Holograms can also be occluded by real-world objects.</span></span> <span data-ttu-id="ed104-170">Par exemple, un caractère holographique peut parcourir une porte et derrière un mur, en dehors de votre vue.</span><span class="sxs-lookup"><span data-stu-id="ed104-170">For example, a holographic character might walk through a door and behind a wall, out of your sight.</span></span>

<span data-ttu-id="ed104-171">**Astuces pour l’intégration des hologrammes et du monde réel**</span><span class="sxs-lookup"><span data-stu-id="ed104-171">**Tips for integrating holograms and the real world**</span></span>

* <span data-ttu-id="ed104-172">L’alignement sur les règles gravitationnelles facilite la liaison des hologrammes à et plus crédible.</span><span class="sxs-lookup"><span data-stu-id="ed104-172">Aligning to gravitational rules makes holograms easier to relate to and more believable.</span></span> <span data-ttu-id="ed104-173">Par exemple : Placez un chien holographique sur le sol & un vase sur la table au lieu de le faire flotter dans l’espace.</span><span class="sxs-lookup"><span data-stu-id="ed104-173">For example: Place a holographic dog on the ground & a vase on the table rather than have them floating in space.</span></span>
* <span data-ttu-id="ed104-174">De nombreux concepteurs ont découvert qu’ils peuvent intégrer des hologrammes plus incroyables en créant une « ombre négative » sur la surface sur laquelle l’hologramme est assis.</span><span class="sxs-lookup"><span data-stu-id="ed104-174">Many designers have found that they can integrate more believable holograms by creating a "negative shadow" on the surface that the hologram is sitting on.</span></span> <span data-ttu-id="ed104-175">Pour ce faire, ils créent une lueur douce sur le sol autour de l’hologramme, puis soustraient la « ombre » de la lueur.</span><span class="sxs-lookup"><span data-stu-id="ed104-175">They do this by creating a soft glow on the ground around the hologram and then subtracting the "shadow" from the glow.</span></span> <span data-ttu-id="ed104-176">La lueur douce s’intègre à la lumière du monde réel.</span><span class="sxs-lookup"><span data-stu-id="ed104-176">The soft glow integrates with the light from the real world.</span></span> <span data-ttu-id="ed104-177">L’ombre est utilisée pour reconstituer l’hologramme dans l’environnement.</span><span class="sxs-lookup"><span data-stu-id="ed104-177">The shadow is used to ground the hologram in the environment.</span></span>

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-what-bryou-can-dream-upbr"></a><span data-ttu-id="ed104-178">Un hologramme est ce que</span><span class="sxs-lookup"><span data-stu-id="ed104-178">A hologram is what</span></span> <br><span data-ttu-id="ed104-179">vous pouvez rêver</span><span class="sxs-lookup"><span data-stu-id="ed104-179">you can dream up</span></span><br>
        <span data-ttu-id="ed104-180">En tant que développeur holographique, vous avez la possibilité de scinder votre créativité en écrans 2D et dans le monde entier.</span><span class="sxs-lookup"><span data-stu-id="ed104-180">As a holographic developer, you have the power to break your creativity out of 2D screens and into the world around you.</span></span><br><br>
        <span data-ttu-id="ed104-181">Que allez- *vous* générer ?</span><span class="sxs-lookup"><span data-stu-id="ed104-181">What will *you* build?</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="ed104-182">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="ed104-182">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="ed104-183">![Monde imaginaire imaginaire dans le salon](images/designoverview.jpg)</span><span class="sxs-lookup"><span data-stu-id="ed104-183">![Holographic imaginary world in living room](images/designoverview.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="next-discovery-checkpoint"></a><span data-ttu-id="ed104-184">Point de contrôle de découverte suivant</span><span class="sxs-lookup"><span data-stu-id="ed104-184">Next Discovery Checkpoint</span></span>

<span data-ttu-id="ed104-185">Vous êtes sur le [parcours de découverte](get-started-with-mr.md) que nous avons disposé et explorant les principes fondamentaux de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="ed104-185">You're on the [discovery journey](get-started-with-mr.md) we've laid out, and exploring the basics of Mixed Reality.</span></span> <span data-ttu-id="ed104-186">À partir de là, vous pouvez passer au sujet suivant :</span><span class="sxs-lookup"><span data-stu-id="ed104-186">From here, you can continue to the next foundational topic:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="ed104-187">Développer votre processus de conception</span><span class="sxs-lookup"><span data-stu-id="ed104-187">Expand your design process</span></span>](case-study-expanding-the-design-process-for-mixed-reality.md)