---
title: Billboarding et tag-along
description: Apprenez à utiliser des objets avec des panneaux d’affichage, qui s’orientent toujours pour les faire face à l’utilisateur dans des applications de réalité mixte.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, le billboarding, la balise, le casque de la réalité mixte, le casque Windows mixed reality, le casque de réalité virtuelle, HoloLens, MRTK, la réalité mixte Shared Computer Toolkit
ms.openlocfilehash: 7ffcbe1d3401601e92eb1ac81dfd84f2af9e8e79eeea809b01a1e943a85f0db9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214159"
---
# <a name="billboarding-and-tag-along"></a>Billboarding et tag-along

<br>

<img src="images/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a>Qu’est-ce que le billboarding ?

Le billboarding est un concept comportemental qui peut être appliqué aux objets en réalité mixte. Les objets avec des panneaux s’orientent toujours pour être confrontés à l’utilisateur. Les systèmes de texte et de menu sont des cas d’utilisation courants, où les objets statiques placés dans l’environnement de l’utilisateur (verrouillé) seraient autrement masqués ou illisibles quand les utilisateurs se déplacent.

Les objets avec le billboarding activé peuvent pivoter librement dans l’environnement de l’utilisateur. Ils peuvent également être limités à un seul axe en fonction des considérations de conception. gardez à l’esprit que les objets superposés peuvent découper ou occultait eux-mêmes lorsqu’ils sont placés trop près d’autres objets, ou dans HoloLens, trop fermer les surfaces numérisées. Pour éviter cela, réfléchissez à l’encombrement total qu’un objet peut produire en cas de rotation sur l’axe activé pour le billboarding.

<br>

---
## <a name="what-is-a-tag-along"></a>Qu’est-ce qu’une balise ?

La balise est un concept comportemental qui peut être ajouté à des hologrammes. Une balise associée à un objet tente de rester dans une plage qui permet à l’utilisateur d’interagir confortablement.

![le panneau HoloLens broches est un bon exemple de la façon dont les balises se comportent](images/tagalong-1000px.jpg)<br>
*le menu Démarrer HoloLens est un excellent exemple de comportement avec balise*

Les objets avec balise ont des paramètres, ce qui peut affiner la façon dont ils se comportent. Le contenu peut être dans ou hors de la ligne de vue de l’utilisateur pendant que l’utilisateur se déplace dans son environnement. Au fur et à mesure que vous déplacez, le contenu tente de rester au sein de la périphérie de l’utilisateur en faisant glisser vers le bord de la vue. Le contenu peut être temporairement hors de l’affichage en fonction de la vitesse de déplacement de l’utilisateur. Lorsque l’utilisateur fait un regard sur l’objet tag, il est plus complet à afficher. Imaginez que le contenu est toujours « un coup d’œil », de sorte que les utilisateurs n’oublient jamais de la direction dans laquelle ils se trouvent.

Des paramètres supplémentaires peuvent faire en sorte que l’objet de la balise soit attaché à la tête de l’utilisateur par une bande de caoutchouc. Le blocage de l’accélération ou de la décélération donne du poids à l’objet, ce qui le rend plus physiquement présent. Ce comportement de printemps est une offre qui permet à l’utilisateur de créer un modèle mental précis sur le fonctionnement de la balise. L’audio permet d’indiquer d’autres indications lorsque les utilisateurs disposent d’objets en mode balise. L’audio doit renforcer la vitesse de déplacement. une rotation rapide doit fournir un effet sonore plus notable, tandis que la marche à une vitesse naturelle doit avoir un impact minime ou aucun effet audio.

À l’instar du contenu véritablement verrouillé, les objets de balise peuvent se révéler insurmontables ou nauseating s’ils se déplacent de manière incomplète dans la vue de l’utilisateur. À mesure qu’un utilisateur regarde, puis s’arrête rapidement, son sens les indique qu’il s’est arrêté. Leur solde les informe que leur tête a cessé de tourner et que leur vision voit que le monde cesse de tourner. Toutefois, si tag-with continue à se déplacer lorsque l’utilisateur s’est arrêté, il peut confondre leurs sens.

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a>billboarding et Tag-en MRTK (Shared Computer Toolkit de la réalité mixte) pour unity
**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fournit des scripts pour le comportement de l’analyseur et de la balise. Assignez le script Billboard. cs à n’importe quel objet pour ajouter un comportement d’emboutment et faire en sorte que l’objet soit toujours à votre Confront. Pour ajouter un comportement avec balise, utilisez le script RadialView. cs. Vous pouvez ajuster diverses options, telles que le temps de lerping, la distance et le degré.

* [MRTK : solveur de vue radiale](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver#radialview)
* [Script MRTK-Billboard](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


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