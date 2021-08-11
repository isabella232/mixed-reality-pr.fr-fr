---
title: Rectangle englobant et barre de l’application
description: La barre de l’application est un menu de niveau objet qui contient une série de boutons qui s’affichent sur le bord inférieur des limites d’un hologramme.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, barre de l’application, cadre englobant, casque de réalité mixte, casque Windows Mixed reality, casque de réalité virtuelle, HoloLens, MRTK, réalité mixte Shared Computer Toolkit
ms.openlocfilehash: d7cacdcffeb552595e4ffd5ea5d1a734efb0451e03c5b6d5d39e5ea8caf3bd94
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198707"
---
# <a name="bounding-box-and-app-bar"></a>Rectangle englobant et barre de l’application
![La délimitation est l’interface standard pour la manipulation d’objets en réalité mixte.](images/UX_Hero_BoundingBox.jpg)<br>
<br>

## <a name="what-is-the-bounding-box"></a>Qu’est-ce que le cadre englobant ?

La délimitation est l’interface standard pour la manipulation d’objets en réalité mixte. Cette fonctionnalité fournit à l’utilisateur un signal visuel indiquant que l’objet est actuellement réglable. sur HoloLens 2, le cadre englobant fonctionne avec la manipulation directe de la main et répond à la proximité de l’utilisateur finger’s. Il affiche des commentaires visuels pour aider l’utilisateur à percevoir la distance par rapport à l’objet.

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a>Mise à l’échelle d’un objet<br>
        Les angles du rectangle englobant indiquent à l’utilisateur que l’objet peut être mis à l’échelle. Les poignées suivent un modèle largement compréhensible pour ajuster l’échelle. Cet indicateur visuel montre aux utilisateurs la zone totale de l’objet, même s’il n’est pas visible en dehors d’un mode de réglage. Sans cette fonctionnalité, un objet aligné sur un autre objet ou surface peut sembler se comporter comme il y avait un espace qui ne devrait pas y figurer.<br>
        <br>
        *Boucle vidéo : mise à l’échelle d’un objet via un cadre englobant*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![HoloLens point de vue de la mise à l’échelle d’un objet à l’aide du cadre englobant](images/HoloLens2_BoundingBox.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a>Rotation d’un objet<br>
        Les intuitivité rectangulaires verticaux sur les bords du cadre englobant sont des indicateurs de rotation. Cela permet à l’utilisateur d’effectuer des ajustements plus précis sur les hologrammes placés. Ils peuvent non seulement les ajuster et les mettre à l’échelle, mais également faire pivoter.<br>
        <br>
        *Boucle vidéo : rotation d’un objet à l’aide du cadre englobant*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![HoloLens point de vue de la rotation d’un objet à l’aide du cadre englobant](images/HoloLens2_BoundingBox_Rotate.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a>Commentaires visuels à proximité sur HoloLens 2<br>
        sur HoloLens 2, il existe un indice visuel supplémentaire qui peut aider la perception de l’utilisateur en profondeur. Un anneau proche de son doigt s’affiche et s’adapte à mesure que l’approche est plus proche de l’objet. L’anneau se convergera en un point lorsque l’état appuyé est atteint. Cet accord visuel aide l’utilisateur à comprendre à quel moment il s’agit de l’objet.<br>
        <br>
        *Boucle vidéo : exemple de retour visuel basé sur la proximité d’un cadre englobant*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Commentaires visuels à proximité](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::

<br>

**pour le développement d’applications unity, consultez cadre [englobant dans la réalité mixte Shared Computer Toolkit-unity.](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)**

<br>

---

## <a name="what-is-the-app-bar"></a>Qu’est-ce que la barre d’application ?

La barre de l’application est un menu de niveau objet, qui contient une série de boutons affichés sur le bord inférieur des limites d’un hologramme. Ce modèle est couramment utilisé pour permettre aux utilisateurs de supprimer et d’ajuster des hologrammes. La barre de l’application a été conçue principalement comme un moyen de gérer les objets placés dans l’environnement d’un utilisateur. Couplée avec le cadre englobant, un utilisateur dispose d’un contrôle total sur l’emplacement et la manière dont les objets sont orientés en réalité mixte.

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a>La barre de l’application suit l’utilisateur<br>
        Étant donné que ce modèle est utilisé avec les objets qui sont verrouillés au monde, lorsqu’un utilisateur se déplace autour de l’objet, la barre de l’application s’affichera toujours sur le côté objets le plus proche de l’utilisateur. Bien qu’il ne s’agit pas d’un billboarding techniquement, cette fonctionnalité permet d’obtenir le même résultat. Empêcher la position d’un utilisateur pour occultait ou bloquer les fonctionnalités qui seraient autrement disponibles à partir d’un autre emplacement dans son environnement. <br>
        <br>
        *Boucle vidéo : à travers un hologramme, la barre de l’application suit*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Parcours d’un hologramme. La barre de l’application suit.](images/HoloLens2_AppBarFollowing.gif)<br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtk-mixed-reality-toolkit-for-unity"></a>cadre englobant dans MRTK (Shared Computer Toolkit de la réalité mixte) pour unity
**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fournit des scripts et des prefabs pour le cadre englobant et la barre de l’application. Vous pouvez ajouter un cadre englobant en affectant le script BoundingBox. cs à n’importe quel objet.

* [MRTK-zone englobante](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)


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