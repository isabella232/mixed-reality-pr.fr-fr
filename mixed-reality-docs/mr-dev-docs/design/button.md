---
title: Bouton
description: Découvrez comment déclencher une action immédiate avec des boutons, qui est l’un des composants fondamentaux de la réalité mixte.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: réalité mixte, contrôles, interaction, interface utilisateur, expérience utilisateur, casque de réalité mixte, casque de réalité windows mixte, casque de réalité virtuelle, HoloLens, MRTK, Shared Computer Toolkit de la réalité mixte, bouton
ms.openlocfilehash: 4b3a9bda852c7a83ee603c3f2340d44f4be89f4d
ms.sourcegitcommit: 4f1697b11e5638db9bbd0bd7a671d846d54c6389
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2021
ms.locfileid: "122682968"
---
# <a name="button"></a>Button

![Button](images/UX_Hero_Button.jpg)

Un bouton est l’un des éléments d’interface utilisateur les plus fondamentaux et cruciaux de la réalité mixte. Il permet à vos utilisateurs de déclencher des actions immédiates. Étant donné qu’il n’y a pas de commentaires physiques en réalité mixte, il est essentiel de fournir suffisamment de commentaires visuels et audio pour augmenter la confiance de l’utilisateur. 

dans HoloLens 2 conception de bouton, en fonction de nombreuses itérations de conception, prototypages et études de recherche d’utilisateurs, nous avons intégré plusieurs intuitivité visuelles et des signaux audio qui aident la perception de la profondeur de l’utilisateur et l’interaction dans un espace vide. 

## <a name="visual-affordances"></a>Intuitivité visuel

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWJHgW]


:::row:::
    :::column:::
       ![Bouton avec effet d’éclairage de proximité indiqué](images/UX_Button_Affordance_ProximityLight.jpg)<br>
       **Lumière proche**<br>
    :::column-end:::
    :::column:::
       ![Bouton sélectionné avec l’effet de surbrillance Focus affiché](images/UX_Button_Affordance_FocusHighlight.jpg)<br>
        **Sélection du focus**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       ![Bouton enfoncé avec l’effet de bâti de compression affiché](images/UX_Button_Affordance_Compression.jpg)<br>
       **Compression du boîtier**<br>
    :::column-end:::
    :::column:::
       ![Bouton enfoncé avec l’effet d’impulsion de déclenchement affiché](images/UX_Button_Affordance_Pulse.jpg)<br>
        **Impulsion sur le déclencheur**<br>
    :::column-end:::
:::row-end:::

<br>

## <a name="audio-cues"></a>Signaux audio

Des retours audio corrects peuvent améliorer considérablement l’expérience utilisateur. le bouton de HoloLens 2 fournit des commentaires audio pour communiquer les indications suivantes :
* **Début du contact**: émettre un signal sonore à la début de la saisie tactile (proche de l’interaction)
* **Fin du contact**: émettre un signal sonore à l’extrémité tactile (proche de l’interaction)
* Le **pincement commence**: émettre un son lors du pincement Select (interaction avec le regard ou les rayons)
* **Extrémités du pincement**: émettre un signal sonore sur une version de pincement (interaction lointaine avec du regard ou des rayons)

<br>

---

:::row:::
    :::column:::
        ## <a name="voice-commandingbr"></a>Commander avec la voix<br>
        Pour tous les boutons de la réalité mixte, il est important de prendre en charge d’autres options d’interaction. Par défaut, nous vous recommandons de prendre en charge les commandes vocales pour tous les boutons. dans la conception du bouton de HoloLens 2, nous fournissons une info-bulle au cours de l’état de survol pour améliorer la détectabilité.
    :::column-end:::
        :::column:::
       ![Entrée vocale](images/UX_Hero_VoiceCommand.jpg)<br>
        *Image : info-bulle pour la commande vocale*
    :::column-end:::
:::row-end:::


<br>

---

## <a name="sizing-recommendations"></a>Recommandations de dimensionnement

Pour vous assurer que tous les objets interactifs peuvent facilement être manipulés, nous vous recommandons de vous assurer que l’interaction est conforme à une taille minimale en fonction de la distance qu’elle place à l’utilisateur. L’angle visuel est souvent mesuré en degrés d’arc visuel. L’angle visuel est basé sur la distance entre les yeux de l’utilisateur et l’objet et reste constant, tandis que la taille physique de la cible peut changer en fonction de la distance entre les modifications de l’utilisateur. Pour déterminer la taille physique nécessaire d’un objet en fonction de la distance de l’utilisateur, essayez d’utiliser une calculatrice d’angle visuel telle que celle- [ci](https://elvers.us/perception/visualAngle/).

Vous trouverez ci-dessous les recommandations relatives aux tailles minimales de contenu exploitable.

### <a name="target-size-for-direct-hand-interaction"></a>Taille cible pour l’interaction directe

| Distance | Angle d’affichage | Taille |
|---------|---------|---------|
| 45 cm  | non inférieur à 2 ° | 1,6 x 1,6 cm |

![Taille cible pour l’interaction directe](images/TargetSizingNear.jpg)<br>
*Taille cible pour l’interaction directe*

<br>

### <a name="target-size-for-buttons"></a>Taille cible pour les boutons

Lorsque vous créez des boutons pour une interaction directe, nous vous recommandons d’utiliser une taille minimale de 3,2 x 3,2 cm pour garantir qu’il y a suffisamment d’espace pour contenir une icône et éventuellement du texte.

| Distance | Taille minimale |
|---------|---------|
| 45 cm  | 3,2 x 3,2 cm |

![Taille cible pour les boutons](images/TargetSizingButtons.png)<br>
*Taille cible pour les boutons*

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a>Taille cible pour un rayon de la main ou une interaction du regard
| Distance | Angle d’affichage | Taille |
|---------|---------|---------|
| 2 m  | inférieur à 1 ° | 3,5 x 3,5 cm |

![Taille cible pour un rayon de la main ou une interaction du regard](images/TargetSizingFar.jpg)<br>
*Taille cible pour un rayon de la main ou une interaction du regard*

<br>

---

## <a name="design-guidelines"></a>Instructions de conception

### <a name="avoid-transparent-backplate"></a>Éviter la plaque arrière transparente
Lors de la conception de l’interface utilisateur du menu avec des boutons, il est recommandé d’utiliser la plaque arrière opaque. Les plaques arrière transparentes ne sont pas recommandées pour les raisons suivantes :
* Interaction difficile avec, car il est difficile de comprendre la profondeur du bouton pour déclencher l’événement
* Problème de lisibilité sur un environnement physique complexe
* les Hologrammes affichées via la plaque transparente peuvent présenter un problème de natation lorsqu’elles sont utilisées avec la technologie de stabilisation LSR de profondeur.

Pour plus d’informations sur les choix de couleurs et les instructions pour l’affichage holographique, consultez [conception de contenu pour l’affichage holographique](designing-content-for-holographic-display.md) .

![Exemple d’interface utilisateur transparente ](images/color_transparent_examples.jpg)
 *exemples d’arrière-plaque d’interface utilisateur transparente*

<br>

### <a name="use-shared-backplate"></a>Utiliser un arrière partagé
Pour plusieurs boutons, il est recommandé d’utiliser la plaque arrière partagée plutôt que l’arrière-plaque du bouton individuel.

* Réduire le bruit et la complexité du visuel
* Effacer le regroupement  

![Exemples d’arrière-plaque partagés ](images/Button_Design_SharedBackplate.png
)
 *exemples d’arrière-plaque d’interface utilisateur partagée*

<br>

---

## <a name="button-in-mrtk-mixed-reality-toolkit"></a>bouton dans MRTK (Shared Computer Toolkit de la réalité mixte)
**[MRTK pour unity](/windows/mixed-reality/mrtk-unity/)** et **[MRTK pour unreal](/windows/mixed-reality/develop/unreal/unreal-mrtk-introduction)** fournissent différents types de prefabs button, y compris des boutons de style HoloLens 2. le composant bouton HoloLens 2 contient tous les détails de l’interaction et des commentaires visuels qui ont été introduits dans cette page. En l’utilisant, vous pouvez tirer parti du résultat de nombreuses itérations de conception et recherches utilisateur effectuées par nos concepteurs, développeurs et chercheurs.

Pour obtenir des instructions et des exemples personnalisés, consultez le [bouton MRTK](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) .

<br>

---

## <a name="see-also"></a>Voir aussi

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