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
# <a name="cursors"></a>Curseurs

![Curseurs](images/UX_Hero_Cursor.jpg)

Un curseur fournit des commentaires continus en fonction de l’endroit où le casque estime qu’un utilisateur a actuellement le focus à un moment donné. Le retour de curseur comprend la zone, l’hologramme ou le point de l’environnement virtuel qui répond à l’entrée. Même si le curseur est une représentation numérique de l’endroit où l’appareil comprend l’attention de l’utilisateur, ce n’est pas le même que de déterminer les intentions de l’utilisateur. Les commentaires des curseurs permettent également aux utilisateurs de connaître les réponses système à attendre. Vous pouvez utiliser les commentaires pour communiquer leur intention à l’appareil, ce qui augmente la confiance de l’utilisateur.

Il existe 3 types de curseurs : **Finger, Ray** et **point-regard**. Ces curseurs de pointage fonctionnent avec différentes modalités d’entrée sur HoloLens, HoloLens 2 et les casques immersifs. Vous trouverez ci-dessous des conseils sur le type de curseur à utiliser pour chaque type de casque et de modèle d’interaction. Dans la boîte à outils de la réalité mixte (MRTK), nous avons créé des modules de curseurs de glisser-déplacer pour vous aider à créer l’expérience de pointage appropriée.

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
        <td>Curseur Finger</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>Curseur Ray</td>
        <td>❌</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Curseur en tête</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="finger-cursor"></a>Curseur Finger

Le curseur Finger est uniquement disponible sur le HoloLens 2 pour améliorer le mode d’interaction «[manipulation directe avec mains](direct-manipulation.md)». Nous avons attaché des anneaux aux conseils des deux index pour mieux comprendre où le doigt pointe. La taille de la sonnerie est basée sur la proximité du doigt par rapport à la surface de l’interface utilisateur, qui se réduit à un petit point lorsque le doigt touche l’interface utilisateur. Plus le doigt est proche, plus l’anneau est petit. <br>

![curseur Finger](images/finger-cursor.png)<br>
**Commentaires visuels États de Finger Cursor** 1 : l’anneau se réduit à un point. 2 : l’anneau s’aligne sur la surface. 3 : l’anneau est perpendiculaire au vecteur Finger. 4 : aucune sonnerie.

## <a name="ray-cursor"></a>Curseur Ray

Les curseurs de rayon sont attachés à la fin des rayons de pointage éloignés pour permettre la manipulation des objets qui ne sont pas en contact avec la main. Dans les casques immersifs, les rayons se déplacent des contrôleurs de mouvement et se terminent par des points-curseurs. Dans HoloLens 2, nous appliquons le modèle mental de ces rayons de contrôleur de mouvement et des rayons de main qui proviennent des palmiers et se terminent par les curseurs en forme d’anneau qui sont cohérents avec les curseurs Finger utilisés dans la manipulation directe. <br>
:::row:::
    :::column:::
        ![Contrôleur de curseurs Ray](images/ray-cursor-controller.png)<br>
        **Curseurs de rayon de contrôleurs de mouvement**<br>
    :::column-end:::
    :::column:::
        ![Curseur de la main](images/ray-cursor-hand.png)<br>
        **Curseurs de Ray des mains**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="head-gaze-cursor"></a>Curseur en tête

Le curseur en tête est un point qui s’attache à la fin d’un vecteur de pointage de tête invisible qui utilise la position et la rotation de l’en-tête. Pour exécuter des actions, ce curseur de pointage est associé à diverses entrées de validation telles que le TAP-Air, les commandes vocales, le son et l’enfoncement de bouton. Dans HoloLens 2, le point de regard est le mieux associé à toute entrée de validation qui n’est pas de pression pneumatique, car il y aura un conflit d’interaction entre les rayons de toucher et les mains de l’air. <br>
:::row:::
    :::column:::
        ![Pointeur vers la droite de la tête](images/head-gaze-cursor-hand.png)<br>
        **Curseur en tête avec mouvement vers la main**<br>
    :::column-end:::
    :::column:::
        ![Voix du curseur en tête](images/head-gaze-cursor-voice.png)<br>
        **Curseur en tête avec commande vocale**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="cursor-customization-recommendations"></a>Recommandations sur la personnalisation des curseurs

Si vous souhaitez personnaliser les comportements et les apparences de commentaires des curseurs, voici quelques recommandations en matière de conception :

### <a name="cursor-scale"></a>Échelle du curseur

* Le curseur ne doit pas être plus grand que les cibles disponibles, ce qui permet aux utilisateurs d’interagir facilement avec et d’afficher le contenu.
* En fonction de l’expérience que vous créez, il est également important de mettre à l’échelle le curseur à mesure que l’utilisateur regarde. Par exemple, à mesure que l’utilisateur regarde plus loin dans votre expérience, le curseur ne doit pas être trop petit pour être perdu.
* Lors de la mise à l’échelle du curseur, envisagez d’appliquer une animation douce à celle-ci lorsqu’il est mis à l’échelle pour lui attribuer une sensation organique.
* Évitez d’obstruer le contenu. Les hologrammes sont ce qui rend l’expérience mémorable et le curseur ne doit pas être pris en charge.

### <a name="directionless-cursor-shape"></a>Forme de curseur dédirectionnelle

* Bien qu’il n’y ait pas de forme de curseur droite, nous vous recommandons d’utiliser une forme sans direction comme un tore. Un curseur qui pointe dans une certaine direction (par exemple, un curseur en forme de flèche traditionnel) peut dérouter l’utilisateur pour qu’il se présente toujours de cette façon.
* Une exception est lors de l’utilisation du curseur pour communiquer des instructions d’interaction à l’utilisateur. Par exemple, lors de la mise à l’échelle d’hologrammes dans le système d’exploitation de réalité mixte, le curseur comprend temporairement des flèches qui indiquent à l’utilisateur comment déplacer sa main pour mettre l’hologramme à l’échelle.

### <a name="look-and-feel"></a>Apparence

* Un curseur en forme de bouée ou de Tore fonctionne pour de nombreuses applications.
* Choisissez une couleur et une forme qui correspond le mieux à l’expérience que vous créez.
* Les curseurs sont particulièrement sujets à la [séparation des couleurs](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation).
* Un petit curseur avec une opacité équilibrée conserve l’information, sans qui prennent la hiérarchie visuelle.
* Soyez Cognizant de l’utilisation des ombres ou des surbrillances derrière votre curseur, car elles peuvent entraver le contenu et nuire à la tâche en cours.
* Les curseurs doivent s’aligner sur les surfaces et les étreinter dans votre application. Les utilisateurs ont le sentiment que le système peut voir où ils regardent, mais également que le système est conscient de leur environnement. Par exemple, le curseur dans le système d’exploitation de réalité mixte s’aligne sur les surfaces du monde de l’utilisateur, ce qui crée un sentiment de conscience du monde même lorsque l’utilisateur n’regarde pas directement sur un hologramme.
* Le verrouillage magnétique du curseur sur un élément interactif lorsqu’il est proche de l’utilisateur peut contribuer à améliorer la confiance que l’utilisateur interagit avec cet élément lorsqu’il utilise une action de sélection.

### <a name="visual-cues"></a>Signaux visuels

* Si votre expérience est axée sur un seul hologramme, votre curseur doit s’aligner sur cet hologramme et changer de forme lorsque vous examinez l’hologramme. Cela peut indiquer à l’utilisateur que l’hologramme est actionnable et qu’il peut interagir avec lui.
* Si votre application utilise le mappage spatial, votre curseur peut s’aligner sur chaque surface visible. Ainsi, les utilisateurs peuvent voir que HoloLens et votre application peuvent voir leur espace. Cela renforce le fait que les hologrammes sont réels et dans notre monde et permet de combler le fossé entre les véritables et les virtuels.
* Avoir une idée de ce que le curseur doit faire lorsqu’il n’y a pas d’hologrammes ou de surfaces en vue. La placer à une distance prédéterminée devant l’utilisateur est une option.

### <a name="possible-actions"></a>Actions possibles

* Le curseur peut être représenté par différentes icônes pour acheminer les actions possibles d’un hologramme, par exemple la mise à l’échelle ou la rotation.
* Ajoutez uniquement des informations supplémentaires sur le curseur si cela revient à l’utilisateur. Dans le cas contraire, les utilisateurs peuvent ne pas remarquer les modifications d’État ou être confondus par le curseur.

### <a name="input-state"></a>État d’entrée

* Nous pourrions utiliser le curseur pour afficher l’état d’entrée ou l’intention de l’utilisateur. Par exemple, nous pourrions afficher une icône indiquant à l’utilisateur que le système voit son état main et que l’application sait qu’il est prêt à agir.
* Nous pourrions également utiliser le curseur pour montrer aux utilisateurs que des commandes vocales ont été entendues par le système par le biais d’une modification de couleur momentanée

* Les États de curseur suivants peuvent être implémentés de différentes façons. Vous pouvez implémenter ces différents États en modélisant le curseur comme une machine à États. Par exemple :
    * L’état inactif est l’endroit où vous affichez le curseur par défaut.
    * L’état prêt est lorsque vous avez détecté la main de l’utilisateur en position prête.
    * L’état de l’interaction est lorsque l’utilisateur fait une interaction particulière.
    * L’état des actions possibles ou l’état de survol est lorsque vous transmettent des actions possibles qui peuvent être effectuées sur un hologramme.

Vous pouvez également implémenter ces États en vue d’une apparence pour afficher différentes ressources d’art lorsque vous détectez des États différents.

<br>

---

## <a name="going-cursor-free"></a>Passage en « sans curseur »

La conception sans curseur est recommandée lorsque le sens de l’immersion est un composant clé d’une expérience et lorsque les interactions de pointage (par le point de regard et le mouvement) ne nécessitent pas de précision. Le système doit toujours répondre aux exigences normales d’un curseur : fournir aux utilisateurs des commentaires continus sur la compréhension de leur point de vue par le système et les aider à communiquer leurs intentions au système. Cela peut être réalisable par d’autres changements d’État perceptibles.

<br>

---

## <a name="cursor-in-mrtk-mixed-reality-toolkit-for-unity"></a>Curseur dans MRTK (ensemble d’outils de réalité mixte) pour Unity

Par défaut, [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) fournit un Prefab de curseur ([DefaultCursor. Prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) qui a le même état visuel que le curseur système de l’interpréteur de commandes. Il est attribué dans le profil d’entrée de MRTK, sous Pointeurs. Vous pouvez remplacer/personnaliser ce curseur pour votre expérience. Pour l’expérience avec l’entrée de suivi oculaire, MRTK fournit également EyeGazeCursor, qui a un visuel subtil pour réduire la distraction.

* [MRTK - Profil de pointeur](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html#pointer-configuration)
* [MRTK - Système d’entrée](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)
* [MRTK - Pointeurs](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html)

---

## <a name="see-also"></a>Voir également

* [Mouvements](gaze-and-commit.md#composite-gestures)
* [Suivre de la tête et valider](gaze-and-commit.md)