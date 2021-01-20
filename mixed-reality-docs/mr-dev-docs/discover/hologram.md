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
# <a name="what-is-a-hologram"></a>Qu’est-ce qu’un hologramme ?

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


HoloLens vous permet de créer des **hologrammes**, qui sont des objets composés de lumière et de son qui s’affichent dans le monde autour des objets réels. Les hologrammes répondent à [votre point de vue](../design/gaze-and-commit.md), aux [gestes](../design/gaze-and-commit.md#composite-gestures)et aux [commandes vocales](../design/voice-input.md). Ils peuvent même interagir avec des [surfaces réelles autour de](../design/spatial-mapping.md) vous. Avec les hologrammes, vous pouvez créer des objets numériques qui font partie de votre monde.

<br>

## <a name="device-support"></a>Prise en charge des appareils

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Fonctionnalité</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1ère génération)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Casques immersifs</strong></a></td>
    </tr>
     <tr>
        <td>Hologrammes</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

<br>

---

## <a name="a-hologram-is-made-of-light-and-sound"></a>Un hologramme est composé de lumière et de son

Les hologrammes que le [contrôle HoloLens affiche](../develop/platform-capabilities-and-apis/rendering.md) dans le cadre holographique directement devant les yeux de l’utilisateur. Les hologrammes ajoutent de la lumière à votre monde, ce qui signifie que vous voyez la lumière de l’écran et la lumière de votre environnement. HoloLens ne disposant pas de lumière sur vos yeux, les hologrammes ne peuvent pas être rendus avec la couleur noire. Au lieu de cela, le contenu noir apparaît comme transparent.

Les hologrammes peuvent avoir de nombreuses apparences et comportements différents. Certains sont réalistes et solides, tandis que d’autres sont animés et Ethereal. Vous pouvez utiliser des hologrammes pour mettre en évidence des fonctionnalités dans votre environnement ou les utiliser en tant qu’éléments dans l’interface utilisateur de votre application.

![Mains manipulation d’un hologramme](images/hologram-hands-940px.jpg)

Les hologrammes peuvent également créer des [sons](../design/spatial-sound.md)qui semblent provenir d’un emplacement spécifique dans votre environnement. Sur HoloLens, le son provient de deux enceintes situées directement au-dessus de vos oreilles, sans les couvrir. Comme pour les écrans, les haut-parleurs sont additifs, ce qui introduit de nouveaux sons sans bloquer les sons de votre environnement.

<br>

---

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a>Un hologramme peut être placé dans le monde entier ou dans la balise avec vous

Lorsque vous disposez d’un emplacement particulier pour un hologramme, vous pouvez le [Placer](../design/coordinate-systems.md) précisément à cet endroit dans le monde. Au fur et à mesure que vous parcourez, l’hologramme est stable en fonction du monde qui vous est autour. Si vous utilisez une [ancre spatiale](../design/coordinate-systems.md#spatial-anchors) pour épingler l’objet, le système peut même vous rappeler où vous l’avez laissé lorsque vous revenez plus tard.

![Deux hommes utilisant la disposition Microsoft Dynamics 365 dans un espace de vente au détail](images/HLS19_retailLayoutHologram_001-940px.jpg)

Certains hologrammes suivent l’utilisateur, et se positionnent sur la base de l’utilisateur, quel que soit l’endroit où ils se déplacent. Vous pouvez même choisir de placer un hologramme avec vous pendant un certain temps, puis le placer sur le mur une fois que vous êtes dans une autre pièce.

**Bonnes pratiques**
* Certains scénarios peuvent exiger que les hologrammes restent facilement détectables ou visibles tout au long de l’expérience. Il existe deux approches de haut niveau pour ce type de positionnement. Appelons-les **« éléments verrouillés** » et **« verrouillés en corps »**.
   * Le contenu verrouillé en affichage est positionné de façon « verrouillée » sur l’écran de l’appareil. Ce type de contenu est délicat pour plusieurs raisons, y compris une sensation innaturelle de « clingyness » qui rend beaucoup d’utilisateurs frustrés et souhaitant les « secouer ». En général, de nombreux concepteurs ont trouvé mieux qu’ils évitent le verrouillage du contenu.
   * L’approche verrouillée par le corps est beaucoup plus forgivable. Le verrouillage du corps est lorsque vous attachez un hologramme au corps de l’utilisateur ou au point de regard dans l’espace 3D. De nombreuses expériences ont adopté un comportement de verrouillage du corps où l’hologramme « suit » les utilisateurs pointant vers le regard, ce qui permet à l’utilisateur de faire pivoter son corps et de parcourir l’espace sans perdre l’hologramme. L’incorporation d’un délai permet d’obtenir un mouvement d’hologramme plus naturel. Par exemple, une interface utilisateur principale du système d’exploitation Windows holographique utilise une variation sur le verrouillage du corps qui suit le point d’arrêt de l’utilisateur avec un délai léger et élastique, tandis que l’utilisateur change de tête.
* Placez l’hologramme à une distance confortable, généralement d’environ 1-2 mètres de l’en-tête.
* Indiquez une valeur de dérive pour les éléments qui doivent être continuellement dans le frame holographique ou envisagez d’animer votre contenu sur un côté de l’affichage lorsque l’utilisateur modifie son point de vue.

**Placer des hologrammes dans la zone optimale (entre 1,25 m et 5 mètres)**

Deux compteurs sont les plus optimaux et l’expérience dégradera la plus proche que vous obteniez de 1 mètre. À des distances plus proches que 1 mètre, les hologrammes qui se déplacent régulièrement sont plus susceptibles d’être problématiques que les hologrammes fixes. Envisagez de découper ou d’inverser correctement votre contenu quand celui-ci est trop proche, ce qui vous évite d’avoir à l’utilisateur une expérience inattendue.

![Distance optimale pour le placement des hologrammes de l’utilisateur.](images/distanceguiderendering-950px.png)

<br>

---

## <a name="a-hologram-interacts-with-you-and-your-world"></a>Un hologramme interagit avec vous et votre monde

Les hologrammes ne sont pas uniquement à l’égard du clair et du son. ils sont également une partie active de votre monde. Pointez le regard sur un hologramme et un geste avec votre main, et un hologramme peut commencer à vous suivre. Donnez une commande vocale à un hologramme, qui peut répondre.

![Groupe de travailleurs utilitaires gouvernementaux utilisant Microsoft HoloLens 2 pour collaborer sur un projet de développement de batterie de serveurs vent](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

Les hologrammes permettent des interactions personnelles qui ne sont pas possibles ailleurs. Étant donné que le HoloLens sait où il se trouve dans le monde, un caractère holographique peut vous paraître directement dans les yeux à mesure que vous parcourez la salle.

Un hologramme peut également interagir avec votre environnement. Par exemple, vous pouvez placer une boule de rebond holographique au-dessus d’un tableau. Puis, avec le [robinet](../design/gaze-and-commit.md#composite-gestures), regardez la balle rebondir et émettez un son lorsqu’il atteint la table.

Les hologrammes peuvent également être bloqués par des objets réels. Par exemple, un caractère holographique peut parcourir une porte et derrière un mur, en dehors de votre vue.

**Conseils pour l’intégration des hologrammes et du monde réel**
* L’alignement sur les règles gravitationnelles facilite la liaison des hologrammes à et plus crédible. par exemple : Placez un chien holographique sur le sol & un vase sur la table au lieu de le faire flotter dans l’espace.
* De nombreux concepteurs ont découvert qu’ils peuvent intégrer des hologrammes plus incroyables en créant une « ombre négative » sur la surface sur laquelle l’hologramme est assis. Pour ce faire, ils créent une lueur douce sur le sol autour de l’hologramme, puis soustraient la « ombre » de la lueur. La lueur douce s’intègre à la lumière du monde réel, qui utilise l’ombre pour refondre l’hologramme dans l’environnement.

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-whatever-bryou-can-dream-upbr"></a>Un hologramme est tout ce que <br>vous pouvez rêver<br>
        En tant que développeur holographique, vous avez la possibilité de scinder votre créativité en écrans 2D et dans le monde entier.<br><br>
        Que allez- *vous* générer ?
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Monde imaginaire imaginaire dans le salon](images/designoverview.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="next-discovery-checkpoint"></a>Point de contrôle de découverte suivant

Si vous suivez le [parcours de découverte](get-started-with-mr.md) que nous avons établi, vous êtes au cœur de l’exploration des concepts de base de la réalité mixte. À partir de là, vous pouvez passer au sujet suivant : 

> [!div class="nextstepaction"]
> [Développer votre processus de conception](case-study-expanding-the-design-process-for-mixed-reality.md)