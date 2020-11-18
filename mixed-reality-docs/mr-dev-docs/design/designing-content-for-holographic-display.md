---
title: Conception de contenu pour un affichage holographique
description: Directives de conception et meilleures pratiques pour l’affichage holographique
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Conception d’interface utilisateur, affichage holographique, conception de contenu, thème sombre, thème clair, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, HoloLens, MRTK, boîte à outils de la réalité mixte, conception, pixels
ms.openlocfilehash: ea3fbda7aff80f0878521deb433c88b16abeab19
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702635"
---
# <a name="designing-content-for-holographic-display"></a><span data-ttu-id="d07d0-104">Conception de contenu pour un affichage holographique</span><span class="sxs-lookup"><span data-stu-id="d07d0-104">Designing content for holographic display</span></span>

![Emplacement de la main ulnar](images/UX_Hero_DarkTheme.jpg)

<span data-ttu-id="d07d0-106">Lorsque vous concevez du contenu pour des affichages holographiques, vous devez prendre en compte plusieurs éléments pour obtenir une expérience optimale.</span><span class="sxs-lookup"><span data-stu-id="d07d0-106">When designing content for holographic displays, there are several elements that you need to consider for achieving the best experience.</span></span> <span data-ttu-id="d07d0-107">Nous avons listé certaines de nos recommandations ci-dessous et vous pouvez en savoir plus sur les caractéristiques des écrans holographiques sur la page [couleur, Light et Materials](color-light-and-materials.md) .</span><span class="sxs-lookup"><span data-stu-id="d07d0-107">We've listed some of our recommendations below and you can learn more about the characteristics of holographic displays at [Color, light and materials](color-light-and-materials.md) page.</span></span>

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a><span data-ttu-id="d07d0-108">Défis avec une couleur brillante sur une grande surface</span><span class="sxs-lookup"><span data-stu-id="d07d0-108">Challenges with bright color on a large surface</span></span> 
<span data-ttu-id="d07d0-109">En s’appuyant sur la recherche et les tests des utilisateurs sur différents types d’expériences HoloLens, nous avons constaté que l’utilisation de couleurs brillantes dans une grande partie de l’affichage peut entraîner plusieurs problèmes :</span><span class="sxs-lookup"><span data-stu-id="d07d0-109">Based on our user research and testing on various types of HoloLens experiences, we found that using bright colors in a large area of the display can cause several issues:</span></span> 

<span data-ttu-id="d07d0-110">**Fatigue oculaire**</span><span class="sxs-lookup"><span data-stu-id="d07d0-110">**Eye fatigue**</span></span> 

<span data-ttu-id="d07d0-111">Étant donné que l’affichage holographique est additif, la couleur brillante utilise plus de lumière pour afficher les hologrammes.</span><span class="sxs-lookup"><span data-stu-id="d07d0-111">Since holographic display is additive, bright color uses more light to display holograms.</span></span> <span data-ttu-id="d07d0-112">Une couleur unie et brillante dans une grande zone de l’affichage peut facilement entraîner une fatigue oculaire pour l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d07d0-112">Bright, solid color in a large area of the display can easily cause eye fatigue for the user.</span></span> 

<span data-ttu-id="d07d0-113">**Occlusion à la main**</span><span class="sxs-lookup"><span data-stu-id="d07d0-113">**Hand occlusion**</span></span> 

<span data-ttu-id="d07d0-114">La couleur brillante rend difficile à l’utilisateur de voir ses mains lorsqu’il interagit directement avec des objets.</span><span class="sxs-lookup"><span data-stu-id="d07d0-114">Bright color makes it difficult for the user to see their hands when directly interacting with objects.</span></span> <span data-ttu-id="d07d0-115">Étant donné que l’utilisateur ne peut pas voir ses mains, il devient difficile de percevoir la profondeur/distance entre la main/le doigt sur la surface cible.</span><span class="sxs-lookup"><span data-stu-id="d07d0-115">Since the user cannot see their hands, it becomes difficult to perceive the depth/distance between the hand/finger to the target surface.</span></span> <span data-ttu-id="d07d0-116">Le curseur Finger permet de compenser ce problème, mais il peut toujours être difficile sur une surface blanche.</span><span class="sxs-lookup"><span data-stu-id="d07d0-116">The Finger Cursor helps compensate for this issue, but it can still be challenging on a bright white surface.</span></span> 

<span data-ttu-id="d07d0-117">![Occlusion des couleurs et des mains ](images/color_handocclusion.jpg)
 *difficile pour voir la main sur le plateau de contenu de couleur brillante*</span><span class="sxs-lookup"><span data-stu-id="d07d0-117">![Color and hand occlusion](images/color_handocclusion.jpg)
*Difficult to see the hand on the bright colored content backplate*</span></span>

<span data-ttu-id="d07d0-118">**Uniformité des couleurs**</span><span class="sxs-lookup"><span data-stu-id="d07d0-118">**Color uniformity**</span></span>

<span data-ttu-id="d07d0-119">En raison des caractéristiques des affichages holographiques, une grande surface lumineuse sur l’écran peut devenir brillante.</span><span class="sxs-lookup"><span data-stu-id="d07d0-119">Because of the characteristics of holographic displays, a large bright area on the display can become blotchy.</span></span> <span data-ttu-id="d07d0-120">En utilisant des modèles de couleurs sombres, vous pouvez réduire ce problème.</span><span class="sxs-lookup"><span data-stu-id="d07d0-120">By using dark color schemes, you can minimize this issue.</span></span> 

## <a name="design-guidelines"></a><span data-ttu-id="d07d0-121">Instructions de conception</span><span class="sxs-lookup"><span data-stu-id="d07d0-121">Design guidelines</span></span>

<span data-ttu-id="d07d0-122">**Utiliser la couleur sombre pour l’arrière-plan de l’interface utilisateur**</span><span class="sxs-lookup"><span data-stu-id="d07d0-122">**Use dark color for the UI background**</span></span>

<span data-ttu-id="d07d0-123">En utilisant le jeu de couleurs sombres, vous pouvez réduire la fatigue oculaire et améliorer la confiance dans les interactions directes.</span><span class="sxs-lookup"><span data-stu-id="d07d0-123">By using the dark color scheme, you can minimize eye fatigue and improve the confidence on direct hand interactions.</span></span> 

<span data-ttu-id="d07d0-124">![Exemple d’interface utilisateur sombre ](images/color_dark_examples.jpg)
 *exemples de couleurs sombres utilisées pour l’arrière-plan du contenu*</span><span class="sxs-lookup"><span data-stu-id="d07d0-124">![Dark UI examples](images/color_dark_examples.jpg)
*Examples of dark color used for the content background*</span></span>

<span data-ttu-id="d07d0-125">**Utiliser l’épaisseur de police SemiBold ou gras**</span><span class="sxs-lookup"><span data-stu-id="d07d0-125">**Use semibold or bold font weight**</span></span>

<span data-ttu-id="d07d0-126">HoloLens vous permet d’afficher un texte très haute résolution.</span><span class="sxs-lookup"><span data-stu-id="d07d0-126">HoloLens allows your experience to show beautiful high-resolution text.</span></span> <span data-ttu-id="d07d0-127">Toutefois, il est recommandé d’éviter des poids de police minces, tels que la lumière ou le semi-éclairage, car les traits verticaux peuvent être instables dans une petite taille de police.</span><span class="sxs-lookup"><span data-stu-id="d07d0-127">However, it is recommended that you avoid thin font weights such as light or semi-light because the vertical strokes can jitter in small font size.</span></span> 

<span data-ttu-id="d07d0-128">![Les exemples d’IU sombres en ](images/color_font_examples.jpg)
 *gras ou en caractères semi-gras (panneau supérieur) améliorent la lisibilité*</span><span class="sxs-lookup"><span data-stu-id="d07d0-128">![Dark UI examples](images/color_font_examples.jpg)
*Bold or semi-bold font weight (upper panel) improves the legibility*</span></span>

<span data-ttu-id="d07d0-129">**Utiliser le matériel HolographicBackplate de MRTK**</span><span class="sxs-lookup"><span data-stu-id="d07d0-129">**Use MRTK’s HolographicBackplate material**</span></span>

<span data-ttu-id="d07d0-130">Le matériel HolographicBackplate est appliqué à plusieurs panneaux d’interface utilisateur dans l’interpréteur de commandes HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d07d0-130">The HolographicBackplate material is applied to several UI panels in the HoloLens shell.</span></span> <span data-ttu-id="d07d0-131">L’une de ses fonctionnalités est un effet iridescence qui est visible pour les utilisateurs lorsqu’ils décalent leur position par rapport au panneau.</span><span class="sxs-lookup"><span data-stu-id="d07d0-131">One of its features is an iridescence effect that is visible to users as they shift their position in relation to the panel.</span></span> <span data-ttu-id="d07d0-132">Les couleurs de la plaque arrière décalent légèrement sur un spectre prédéfini, créant ainsi un effet visuel attrayant et dynamique sans interférer avec la lisibilité du contenu.</span><span class="sxs-lookup"><span data-stu-id="d07d0-132">The backplate color shifts subtly across a predefined spectrum, creating an engaging and dynamic visual effect without interfering with content readability.</span></span> <span data-ttu-id="d07d0-133">Ce petit décalage de couleur sert également à compenser les irrégularités de couleur mineure.</span><span class="sxs-lookup"><span data-stu-id="d07d0-133">This subtle shift in color also serves to compensate for any minor color irregularities.</span></span> 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a><span data-ttu-id="d07d0-134">Défis avec la plaque d’interface utilisateur transparente ou translucide</span><span class="sxs-lookup"><span data-stu-id="d07d0-134">Challenges with transparent or translucent UI backplate</span></span> 
<span data-ttu-id="d07d0-135">![Exemple d’interface utilisateur transparente ](images/color_transparent_examples.jpg)
 *exemples d’arrière-plaque d’interface utilisateur transparente*</span><span class="sxs-lookup"><span data-stu-id="d07d0-135">![Transparent UI examples](images/color_transparent_examples.jpg)
*Examples of transparent UI backplate*</span></span>

<span data-ttu-id="d07d0-136">**Complexité visuelle et accessibilité**</span><span class="sxs-lookup"><span data-stu-id="d07d0-136">**Visual complexity and accessibility**</span></span>

<span data-ttu-id="d07d0-137">Étant donné que les objets holographiques sont mélangés à l’environnement physique, la lisibilité du contenu ou de l’interface utilisateur sur la fenêtre transparente ou translucide peut être dégradée.</span><span class="sxs-lookup"><span data-stu-id="d07d0-137">Since holographic objects are blended with the physical environment, the legibility of the content or UI on the transparent or translucent window could be degraded.</span></span> <span data-ttu-id="d07d0-138">En outre, lorsque des objets holographiques transparents sont superposés les uns aux autres, il peut être difficile pour l’utilisateur d’interagir en raison de la profondeur de confusion.</span><span class="sxs-lookup"><span data-stu-id="d07d0-138">Additionally, when transparent holographic objects are overlaid on top of each other, it could make it difficult for the user to interact because of the confusing depth.</span></span>

<span data-ttu-id="d07d0-139">**Performances**</span><span class="sxs-lookup"><span data-stu-id="d07d0-139">**Performance**</span></span>

<span data-ttu-id="d07d0-140">Pour que les objets transparents ou translucides s’affichent correctement, ils doivent être triés et fusionnés avec tous les objets qui existent en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="d07d0-140">For transparent or translucent objects to render correctly they must be sorted and blended with any objects which exist in the background.</span></span> <span data-ttu-id="d07d0-141">Le tri des objets transparents a un coût d’UC modeste, la fusion présente un coût considérable du GPU, car elle ne permet pas au GPU d’effectuer une suppression de surface cachée via l’élimination z (c.-à-d.</span><span class="sxs-lookup"><span data-stu-id="d07d0-141">Sorting of transparent objects has a modest CPU cost, blending has considerable GPU cost because it does not allow the GPU to perform hidden surface removal via z-culling (i.e</span></span> <span data-ttu-id="d07d0-142">test de profondeur).</span><span class="sxs-lookup"><span data-stu-id="d07d0-142">depth testing).</span></span> <span data-ttu-id="d07d0-143">Si vous n’autorisez pas la suppression de la surface masquée, vous augmentez le nombre d’opérations qui doivent être calculées pour le pixel final rendu, ce qui augmente la pression sur les contraintes de taux de remplissage.</span><span class="sxs-lookup"><span data-stu-id="d07d0-143">Not allowing hidden surface removal increases the number of operations that need to be computed for the final rendered pixel, and thus puts more pressure on fill rate constraints.</span></span>

<span data-ttu-id="d07d0-144">**Problème de stabilité d’hologramme avec la technologie Depth LSR**</span><span class="sxs-lookup"><span data-stu-id="d07d0-144">**Hologram stability issue with Depth LSR technology**</span></span>

<span data-ttu-id="d07d0-145">Pour améliorer la reprojection holographique ou la stabilité de l’hologramme, une application peut envoyer une mémoire tampon de profondeur au système pour chaque cadre rendu.</span><span class="sxs-lookup"><span data-stu-id="d07d0-145">To improve holographic reprojection, or hologram stability, an application can submit a depth buffer to the system for every rendered frame.</span></span> <span data-ttu-id="d07d0-146">Lors de l’utilisation de la mémoire tampon de profondeur pour la reprojection, une règle est que, pour chaque pixel de couleur rendu, une valeur de profondeur correspondante doit être écrite dans la mémoire tampon de profondeur (et tout pixel avec une valeur de profondeur doit également avoir une valeur de couleur).</span><span class="sxs-lookup"><span data-stu-id="d07d0-146">When using the depth buffer for reprojection one rule is that for every color pixel rendered a corresponding depth value must be written to the depth buffer (and any pixel with a depth value should also have color value).</span></span> <span data-ttu-id="d07d0-147">Si les recommandations ci-dessus ne sont pas suivies, les zones de l’image rendue qui ne possèdent pas d’informations de profondeur valides peuvent être reprojetées de manière à produire des artefacts (souvent visibles sous forme de distorsions de type « Wave »).</span><span class="sxs-lookup"><span data-stu-id="d07d0-147">If the above guidance is not followed, areas of the rendered image that lack valid depth information may be reprojected in a way that produces artifacts (often visible as a wave-like distortion).</span></span>


## <a name="design-guidelines"></a><span data-ttu-id="d07d0-148">Instructions de conception</span><span class="sxs-lookup"><span data-stu-id="d07d0-148">Design guidelines</span></span>
<span data-ttu-id="d07d0-149">**Utiliser l’arrière-plan de l’interface utilisateur opaque**</span><span class="sxs-lookup"><span data-stu-id="d07d0-149">**Use opaque UI background**</span></span>

<span data-ttu-id="d07d0-150">Par défaut, les objets transparents ou translucides n’écrivent pas de profondeur pour permettre une fusion correcte.</span><span class="sxs-lookup"><span data-stu-id="d07d0-150">By default, transparent or translucent objects do not write depth to allow for proper blending.</span></span> <span data-ttu-id="d07d0-151">Pour atténuer ce problème, vous pouvez utiliser des objets opaques, en veillant à ce que les objets translucides apparaissent près des objets opaques (tels qu’un bouton translucide devant une plaque arrière opaque), en forçant les objets translucides à écrire une profondeur (non applicable dans tous les scénarios), ou en rendant des objets proxy qui contribuent uniquement des valeurs de profondeur à</span><span class="sxs-lookup"><span data-stu-id="d07d0-151">Ways to mitigate this issue include, using opaque objects, ensuring translucent objects appear close to opaque objects (such as a translucent button in front of an opaque backplate), forcing translucent objects to write depth (not applicable in all scenarios), or rendering proxy objects which only contribute depth values at the end of the frame.</span></span>

<span data-ttu-id="d07d0-152">Solutions dans MRTK-Unity : https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/hologram-stabilization.html#depth-buffer-sharing-in-unity</span><span class="sxs-lookup"><span data-stu-id="d07d0-152">Solutions within MRTK-Unity: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/hologram-stabilization.html#depth-buffer-sharing-in-unity</span></span>  

<span data-ttu-id="d07d0-153">En utilisant une plaque arrière solide et opaque, nous pouvons sécuriser la lisibilité et la confiance de l’interaction.</span><span class="sxs-lookup"><span data-stu-id="d07d0-153">By using a solid and opaque backplate, we can secure legibility and interaction confidence.</span></span>

<span data-ttu-id="d07d0-154">**Réduire le nombre de pixels affectés**</span><span class="sxs-lookup"><span data-stu-id="d07d0-154">**Minimize the number of pixels affected**</span></span>

<span data-ttu-id="d07d0-155">Si votre projet doit utiliser des objets transparents, essayez de réduire le nombre de pixels affectés.</span><span class="sxs-lookup"><span data-stu-id="d07d0-155">If your project must use transparent objects, try to minimize the number of pixels affected.</span></span> <span data-ttu-id="d07d0-156">Par exemple, si un objet est visible uniquement sous certaines conditions (comme un effet d’éclat additif), désactivez l’objet lorsqu’il est complètement invisible (au lieu de définir la couleur additive sur noir).</span><span class="sxs-lookup"><span data-stu-id="d07d0-156">For example, if an object is only visible under certain conditions (like an additive glow effect), disable the object when it is fully invisible (instead of setting the additive color to black).</span></span> <span data-ttu-id="d07d0-157">Pour les formes 2D simples créées à l’aide d’un quadruple avec un masque Alpha, envisagez de créer une représentation de maillage de la forme avec un nuanceur opaque à la place.</span><span class="sxs-lookup"><span data-stu-id="d07d0-157">For simple 2D shapes created using a quad with an alpha mask, consider creating a mesh representation of the shape with an opaque shader instead.</span></span> 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="d07d0-158">Exemples d’interfaces utilisateur sombres dans MRTK (kit de préversion de réalité mixte) pour Unity</span><span class="sxs-lookup"><span data-stu-id="d07d0-158">Dark UI examples in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="d07d0-159">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fournit de nombreux exemples de blocs de construction d’interface utilisateur basés sur les modèles de couleurs sombres.</span><span class="sxs-lookup"><span data-stu-id="d07d0-159">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides many UI building block examples based on the dark color schemes.</span></span>

* [<span data-ttu-id="d07d0-160">Menu proche</span><span class="sxs-lookup"><span data-stu-id="d07d0-160">Near Menu</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_NearMenu.html)
* [<span data-ttu-id="d07d0-161">Dialogue</span><span class="sxs-lookup"><span data-stu-id="d07d0-161">Dialog</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/Dialog/README_Dialog.html)
* [<span data-ttu-id="d07d0-162">Menu de la main</span><span class="sxs-lookup"><span data-stu-id="d07d0-162">Hand Menu</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)


<br>

---


## <a name="see-also"></a><span data-ttu-id="d07d0-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d07d0-163">See also</span></span>
* [<span data-ttu-id="d07d0-164">Couleurs, éclairage et matériaux</span><span class="sxs-lookup"><span data-stu-id="d07d0-164">Color, light and materials</span></span>](color-light-and-materials.md)
* [<span data-ttu-id="d07d0-165">Curseurs</span><span class="sxs-lookup"><span data-stu-id="d07d0-165">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="d07d0-166">Rayon émanant de la main</span><span class="sxs-lookup"><span data-stu-id="d07d0-166">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="d07d0-167">Button</span><span class="sxs-lookup"><span data-stu-id="d07d0-167">Button</span></span>](button.md)
* [<span data-ttu-id="d07d0-168">Objet avec interaction possible</span><span class="sxs-lookup"><span data-stu-id="d07d0-168">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="d07d0-169">Rectangle englobant et barre de l’application</span><span class="sxs-lookup"><span data-stu-id="d07d0-169">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="d07d0-170">Manipulation</span><span class="sxs-lookup"><span data-stu-id="d07d0-170">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="d07d0-171">Menu de la main</span><span class="sxs-lookup"><span data-stu-id="d07d0-171">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="d07d0-172">Menu proche</span><span class="sxs-lookup"><span data-stu-id="d07d0-172">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="d07d0-173">Collection d’objets</span><span class="sxs-lookup"><span data-stu-id="d07d0-173">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="d07d0-174">Commande vocale</span><span class="sxs-lookup"><span data-stu-id="d07d0-174">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="d07d0-175">Clavier</span><span class="sxs-lookup"><span data-stu-id="d07d0-175">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="d07d0-176">Info-bulle</span><span class="sxs-lookup"><span data-stu-id="d07d0-176">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="d07d0-177">Tablette</span><span class="sxs-lookup"><span data-stu-id="d07d0-177">Slate</span></span>](slate.md)
* [<span data-ttu-id="d07d0-178">Curseur</span><span class="sxs-lookup"><span data-stu-id="d07d0-178">Slider</span></span>](slider.md)
* [<span data-ttu-id="d07d0-179">Nuanceur</span><span class="sxs-lookup"><span data-stu-id="d07d0-179">Shader</span></span>](shader.md)
* [<span data-ttu-id="d07d0-180">Billboarding et tag-along</span><span class="sxs-lookup"><span data-stu-id="d07d0-180">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="d07d0-181">Affichage de la progression</span><span class="sxs-lookup"><span data-stu-id="d07d0-181">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="d07d0-182">Aimantation de surface</span><span class="sxs-lookup"><span data-stu-id="d07d0-182">Surface magnetism</span></span>](surface-magnetism.md)
