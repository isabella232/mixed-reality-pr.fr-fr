---
title: Conception de contenu pour l’affichage holographique
description: Directives de conception et meilleures pratiques pour l’affichage holographique
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Conception d’interface utilisateur, affichage holographique, conception de contenu, thème sombre, thème clair
ms.openlocfilehash: 627ffdd0a413ad3140c29e9b1c7bb69c9dc249cf
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91680475"
---
# <a name="designing-content-for-holographic-display"></a>Conception de contenu pour l’affichage holographique

![Emplacement de la main ulnar](images/UX_Hero_DarkTheme.jpg)

Lorsque vous concevez du contenu pour des affichages holographiques, vous devez prendre en compte plusieurs éléments pour obtenir une expérience optimale. Nous avons listé certaines de nos recommandations ci-dessous et vous pouvez en savoir plus sur les caractéristiques des écrans holographiques sur la page [couleur, Light et Materials](color-light-and-materials.md) .

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a>Défis avec une couleur brillante sur une grande surface 
En s’appuyant sur la recherche et les tests des utilisateurs sur différents types d’expériences HoloLens, nous avons constaté que l’utilisation de couleurs brillantes dans une grande partie de l’affichage peut entraîner plusieurs problèmes : 

**Fatigue oculaire** 

Étant donné que l’affichage holographique est additif, la couleur brillante utilise plus de lumière pour afficher les hologrammes. Une couleur unie et brillante dans une grande zone de l’affichage peut facilement entraîner une fatigue oculaire pour l’utilisateur. 

**Occlusion à la main** 

La couleur brillante rend difficile à l’utilisateur de voir ses mains lorsqu’il interagit directement avec des objets. Étant donné que l’utilisateur ne peut pas voir ses mains, il devient difficile de percevoir la profondeur/distance entre la main/le doigt sur la surface cible. Le curseur Finger permet de compenser ce problème, mais il peut toujours être difficile sur une surface blanche. 

![Occlusion des couleurs et des mains ](images/color_handocclusion.jpg)
 *difficile pour voir la main sur le plateau de contenu de couleur brillante*

**Uniformité des couleurs**

En raison des caractéristiques des affichages holographiques, une grande surface lumineuse sur l’écran peut devenir brillante. En utilisant des modèles de couleurs sombres, vous pouvez réduire ce problème. 

## <a name="design-guidelines"></a>Instructions de conception

**Utiliser la couleur sombre pour l’arrière-plan de l’interface utilisateur**

En utilisant le jeu de couleurs sombres, vous pouvez réduire la fatigue oculaire et améliorer la confiance dans les interactions directes. 

![Exemple d’interface utilisateur sombre ](images/color_dark_examples.jpg)
 *exemples de couleurs sombres utilisées pour l’arrière-plan du contenu*

**Utiliser l’épaisseur de police SemiBold ou gras**

HoloLens vous permet d’afficher un texte très haute résolution. Toutefois, il est recommandé d’éviter des poids de police minces, tels que la lumière ou le semi-éclairage, car les traits verticaux peuvent être instables dans une petite taille de police. 

![Les exemples d’IU sombres en ](images/color_font_examples.jpg)
 *gras ou en caractères semi-gras (panneau supérieur) améliorent la lisibilité*

**Utiliser le matériel HolographicBackplate de MRTK**

Le matériel HolographicBackplate est appliqué à plusieurs panneaux d’interface utilisateur dans l’interpréteur de commandes HoloLens. L’une de ses fonctionnalités est un effet iridescence qui est visible pour les utilisateurs lorsqu’ils décalent leur position par rapport au panneau. Les couleurs de la plaque arrière décalent légèrement sur un spectre prédéfini, créant ainsi un effet visuel attrayant et dynamique sans interférer avec la lisibilité du contenu. Ce petit décalage de couleur sert également à compenser les irrégularités de couleur mineure. 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a>Défis avec la plaque d’interface utilisateur transparente ou translucide 
![Exemple d’interface utilisateur transparente ](images/color_transparent_examples.jpg)
 *exemples d’arrière-plaque d’interface utilisateur transparente*

**Complexité visuelle et accessibilité**

Étant donné que les objets holographiques sont mélangés à l’environnement physique, la lisibilité du contenu ou de l’interface utilisateur sur la fenêtre transparente ou translucide peut être dégradée. En outre, lorsque des objets holographiques transparents sont superposés les uns aux autres, il peut être difficile pour l’utilisateur d’interagir en raison de la profondeur de confusion.

**Performances**

Pour que les objets transparents ou translucides s’affichent correctement, ils doivent être triés et fusionnés avec tous les objets qui existent en arrière-plan. Le tri des objets transparents a un coût d’UC modeste, la fusion présente un coût considérable du GPU, car elle ne permet pas au GPU d’effectuer une suppression de surface cachée via l’élimination z (c.-à-d. test de profondeur). Si vous n’autorisez pas la suppression de la surface masquée, vous augmentez le nombre d’opérations qui doivent être calculées pour le pixel final rendu, ce qui augmente la pression sur les contraintes de taux de remplissage.

**Problème de stabilité d’hologramme avec la technologie Depth LSR**

Pour améliorer la reprojection holographique ou la stabilité de l’hologramme, une application peut envoyer une mémoire tampon de profondeur au système pour chaque cadre rendu. Lors de l’utilisation de la mémoire tampon de profondeur pour la reprojection, une règle est que, pour chaque pixel de couleur rendu, une valeur de profondeur correspondante doit être écrite dans la mémoire tampon de profondeur (et tout pixel avec une valeur de profondeur doit également avoir une valeur de couleur). Si les recommandations ci-dessus ne sont pas suivies, les zones de l’image rendue qui ne possèdent pas d’informations de profondeur valides peuvent être reprojetées de manière à produire des artefacts (souvent visibles sous forme de distorsions de type « Wave »).


## <a name="design-guidelines"></a>Instructions de conception
**Utiliser l’arrière-plan de l’interface utilisateur opaque**

Par défaut, les objets transparents ou translucides n’écrivent pas de profondeur pour permettre une fusion correcte. Pour atténuer ce problème, vous pouvez utiliser des objets opaques, en veillant à ce que les objets translucides apparaissent près des objets opaques (tels qu’un bouton translucide devant une plaque arrière opaque), en forçant les objets translucides à écrire une profondeur (non applicable dans tous les scénarios), ou en rendant des objets proxy qui contribuent uniquement des valeurs de profondeur à

Solutions dans MRTK-Unity : https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/hologram-stabilization.html#depth-buffer-sharing-in-unity  

En utilisant une plaque arrière solide et opaque, nous pouvons sécuriser la lisibilité et la confiance de l’interaction.

**Réduire le nombre de pixels affectés**

Si votre projet doit utiliser des objets transparents, essayez de réduire le nombre de pixels affectés. Par exemple, si un objet est visible uniquement sous certaines conditions (comme un effet d’éclat additif), désactivez l’objet lorsqu’il est complètement invisible (au lieu de définir la couleur additive sur noir). Pour les formes 2D simples créées à l’aide d’un quadruple avec un masque Alpha, envisagez de créer une représentation de maillage de la forme avec un nuanceur opaque à la place. 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a>Exemples d’interfaces utilisateur sombres dans MRTK (kit de préversion de réalité mixte) pour Unity
**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fournit de nombreux exemples de blocs de construction d’interface utilisateur basés sur les modèles de couleurs sombres.

* [Menu proche](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_NearMenu.html)
* [Dialogue](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/Dialog/README_Dialog.html)
* [Menu de la main](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)


<br>

---


## <a name="see-also"></a>Voir aussi
* [Couleurs, éclairage et matériaux](color-light-and-materials.md)
* [Curseurs](cursors.md)
* [Rayon émanant de la main](point-and-commit.md)
* [Button](button.md)
* [Objet avec interaction possible](interactable-object.md)
* [Rectangle englobant et barre de l’application](app-bar-and-bounding-box.md)
* [Manipulation](direct-manipulation.md)
* [Menu de la main](hand-menu.md)
* [Menu proche](near-menu.md)
* [Collection d’objets](object-collection.md)
* [Commande vocale](voice-input.md)
* [Clavier](keyboard.md)
* [Info-bulle](tooltip.md)
* [Tablette](slate.md)
* [Curseur](slider.md)
* [Nuanceur](shader.md)
* [Billboarding et tag-along](billboarding-and-tag-along.md)
* [Affichage de la progression](progress.md)
* [Aimantation de surface](surface-magnetism.md)
