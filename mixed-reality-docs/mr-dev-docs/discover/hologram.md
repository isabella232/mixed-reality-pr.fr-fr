---
title: Qu’est-ce qu’un hologramme ?
description: HoloLens vous permet d’afficher et d’interagir avec des hologrammes à trois dimensions, des objets composés de lumière et de son qui s’affichent dans le monde autour de vous.
author: qianw211
ms.author: v-qianwen
ms.date: 07/09/2021
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, hologrammes, conception, interaction, casque de réalité mixte, casque Windows mixed reality, qu’est-ce que la réalité augmente
ms.openlocfilehash: e028fe6180bded26263fa47feb5acefc94570222e43f10fe85db5adf90307844
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202114"
---
# <a name="what-is-a-hologram"></a>Qu’est-ce qu’un hologramme ?

HoloLens vous permet d’afficher des **hologrammes**, qui sont des objets composés de lumière et de son qui s’affichent dans le monde autour des objets réels. Hologrammes pouvez répondre [à vos](../design/gaze-and-commit.md)commandes de pointage, de [mouvement](../design/gaze-and-commit.md#composite-gestures)et de [voix](../design/voice-input.md). Ils peuvent même interagir avec des [surfaces réelles autour de](../design/spatial-mapping.md) vous. Hologrammes sont des objets numériques qui font partie de votre monde.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

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
        <td><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
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

### <a name="light"></a>Clair

les hologrammes [que HoloLens](../develop/platform-capabilities-and-apis/rendering.md) affichent dans le cadre holographique directement devant les yeux des utilisateurs. Hologrammes ajouter de la lumière à votre monde, ce qui signifie que vous voyez la lumière de l’écran et la lumière de votre monde environnant. étant donné que HoloLens utilise un affichage additif qui ajoute de la lumière, la couleur noire est rendue transparente. 

Hologrammes peut avoir des apparences et des comportements très différents. Certains sont réalistes et solides, tandis que d’autres sont animés et Ethereal. Vous pouvez utiliser des hologrammes pour mettre en évidence les fonctionnalités de votre environnement ou les utiliser en tant qu’éléments dans l’interface utilisateur de votre application.

![Mains manipulation d’un hologramme](images/hologram-hands-940px.jpg)

### <a name="sound"></a>Son

Hologrammes pouvez également produire des [sons](../design/spatial-sound.md), qui semblent provenir d’un emplacement spécifique dans votre environnement. sur HoloLens, le son provient de deux haut-parleurs situés directement au-dessus de vos oreilles. Comme les écrans holographiques, les haut-parleurs sont additifs, ce qui introduit de nouveaux sons sans bloquer les sons de votre environnement.

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a>Un hologramme peut être placé dans le monde entier ou dans la balise avec vous

Lorsque vous disposez d’un emplacement fixe pour un hologramme, vous pouvez le [Placer](../design/coordinate-systems.md) précisément à cet endroit dans le monde. Au fur et à mesure que vous parcourez, l’hologramme s’affiche à l’aide du monde entier, tout comme un objet physique. Si vous utilisez une [ancre spatiale](../design/coordinate-systems.md#spatial-anchors) pour épingler l’objet, le système peut même vous rappeler où vous l’avez laissé lorsque vous revenez plus tard.

![Deux hommes utilisant la disposition Microsoft Dynamics 365 dans un espace de vente au détail](images/HLS19_retailLayoutHologram_001-940px.jpg)

Certains hologrammes suivent l’utilisateur à la place. Ils se positionnent sur la base de l’utilisateur. Vous pouvez choisir de placer un hologramme avec vous, puis le placer sur le mur une fois que vous êtes dans une autre pièce.

**Bonnes pratiques**

* Certains scénarios exigent que les hologrammes restent facilement détectables ou visibles tout au long de l’expérience. Il existe deux approches de haut niveau pour ce type de positionnement. Appelons-les **en mode verrouillé** et **verrouillé**.
   * Le contenu **verrouillé** est verrouillé sur le périphérique d’affichage. Ce type de contenu est délicat pour plusieurs raisons, y compris une sensation innaturelle de « clingyness » qui rend beaucoup d’utilisateurs frustrés et souhaitant les « secouer ». En général, les concepteurs ont trouvé qu’il est préférable d’éviter le verrouillage de l’affichage du contenu.
   * **Le contenu verrouillé** peut être beaucoup plus indulgent avec. Le verrouillage du corps est lorsque vous attachez un hologramme au corps de l’utilisateur ou au point de regard dans l’espace 3D. De nombreuses expériences ont adopté un comportement de verrouillage du corps où l’hologramme suit le regard de l’utilisateur, ce qui permet à l’utilisateur de faire pivoter son corps et de se déplacer dans l’espace sans perdre l’hologramme. L’incorporation d’un délai permet aux mouvements d’hologramme de se sentir plus naturels. par exemple, une interface utilisateur principale du système d’exploitation holographique Windows utilise une variation sur le verrouillage du corps qui suit le point de regard de l’utilisateur avec un délai léger et élastique, tandis que l’utilisateur change de tête.
* Placez l’hologramme à une distance confortable, généralement d’environ 1-2 mètres de l’en-tête.
* Autorisez la dérive des éléments si elles doivent être continuellement dans le frame holographique ou si vous envisagez de déplacer votre contenu vers l’un des côtés de l’affichage lorsque l’utilisateur modifie son point de vue. Pour plus d’informations, consultez la page relative aux [panneaux et aux balises](../design/billboarding-and-tag-along.md) Artilce.

**Placer des hologrammes dans la zone optimale (entre 1,25 m et 5 mètres)**

La distance d’affichage la plus optimale est de deux mètres. L’expérience commence à se dégrader à mesure que vous vous rapprochez de 1 mètre. À des distances inférieures à 1 mètre, les hologrammes qui se déplacent régulièrement sont plus susceptibles d’être problématiques que les hologrammes fixes. Envisagez de découper ou d’inverser correctement votre contenu quand il est trop proche. vous ne devez donc pas l’utiliser dans une expérience de visualisation désagréable.

![Distance optimale pour le placement des hologrammes de l’utilisateur.](images/distanceguiderendering-950px.png)

<br>

---

## <a name="a-hologram-interacts-with-you-and-your-world"></a>Un hologramme interagit avec vous et votre monde

Hologrammes ne sont pas uniquement à l’égard du clair et du son. ils sont également une partie active de votre monde. Pointez le regard sur un hologramme et un geste avec votre main, et un hologramme peut commencer à vous suivre. Donnez une commande vocale et l’hologramme peut répondre.

![groupe de travailleurs de l’utilitaire gouvernemental utilisant Microsoft HoloLens 2 pour collaborer sur un projet de développement de batterie de serveurs vent](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

Hologrammes activer les interactions personnelles qui ne sont pas possibles ailleurs. étant donné que le HoloLens sait où il se trouve dans le monde, un caractère holographique peut vous regarder directement dans les yeux et démarrer une conversation avec vous.

Un hologramme peut également interagir avec votre environnement. Par exemple, vous pouvez placer une boule de rebond holographique au-dessus d’un tableau. Ensuite, à l’aide d’un [robinet](../design/gaze-and-commit.md#composite-gestures), regardez la balle rebondir et faites sonner le son au fur et à mesure qu’elle touche le tableau.

Hologrammes peut également être bloqués par des objets réels. Par exemple, un caractère holographique peut parcourir une porte et derrière un mur, en dehors de votre vue.

**Astuces pour l’intégration des hologrammes et du monde réel**

* L’alignement sur les règles gravitationnelles facilite la liaison des hologrammes à et plus crédible. Par exemple : Placez un chien holographique sur le sol & un vase sur la table au lieu de le faire flotter dans l’espace.
* De nombreux concepteurs ont découvert qu’ils peuvent intégrer des hologrammes plus incroyables en créant une « ombre négative » sur la surface sur laquelle l’hologramme est assis. Pour ce faire, ils créent une lueur douce sur le sol autour de l’hologramme, puis soustraient la « ombre » de la lueur. La lueur douce s’intègre à la lumière du monde réel. L’ombre est utilisée pour reconstituer l’hologramme dans l’environnement.

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-what-bryou-can-dream-upbr"></a>Un hologramme est ce que <br>vous pouvez rêver<br>
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

Vous êtes sur le [parcours de découverte](get-started-with-mr.md) que nous avons disposé et explorant les principes fondamentaux de la réalité mixte. À partir de là, vous pouvez passer au sujet suivant : 

> [!div class="nextstepaction"]
> [Développer votre processus de conception](case-study-expanding-the-design-process-for-mixed-reality.md)