---
title: Typographie
description: Le texte est un élément important pour la diffusion d’informations dans votre expérience d’application.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality, conception, style, police, typographie, UI, UX, texte, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle, HoloLens
ms.openlocfilehash: 09e0e6029011fdd7fda793f6b6645cb3744baa3b
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848143"
---
# <a name="typography"></a>Typographie

![Exemple de typographie dans HoloLens](images/typography-cover.png)<br>


Le texte est un élément important pour la diffusion d’informations dans votre expérience d’application. Tout comme la typographie sur les écrans 2D, l’objectif est d’être clair et lisible. Avec l’aspect à trois dimensions de la réalité mixte, il est possible d’affecter le texte et l’expérience utilisateur globale d’une manière encore plus importante.

Lorsque nous parlerons du type en 3D, nous avons tendance à penser que le texte 3D est extrudé et jaugé. À l’exception de certaines conceptions logotype et de quelques autres applications limitées, le texte extrudé a tendance à dégrader la lisibilité du texte. Même si nous concevons des expériences en 3D, nous utilisons un 2D pour le type, car il est plus lisible et plus facile à lire.

Dans HoloLens, le type est construit avec des hologrammes à l’aide de la lumière basée sur le système de couleurs additif. Tout comme les autres hologrammes, le type peut être placé dans l’environnement réel où il peut être verrouillé et observé à partir de n’importe quel angle. L’effet de [parallaxe](https://en.wikipedia.org/wiki/Parallax) entre le type et l’environnement ajoute également une profondeur à l’expérience.

## <a name="typography-in-mixed-reality"></a>Typographie dans une réalité mixte

Les règles typographiques en réalité mixte ne sont pas différentes de n’importe où ailleurs. Le texte à la fois dans le monde physique et dans le monde virtuel doit être lisible et lisible. Le texte peut être situé sur un mur ou superposé sur un objet physique. Il peut être flottant avec une interface utilisateur numérique. Quel que soit le contexte, nous appliquons les mêmes règles typographiques pour la lecture et la reconnaissance.

### <a name="create-clear-hierarchy"></a>Créer une hiérarchie claire

Générez le contraste et la hiérarchie en utilisant des tailles et des poids différents. Le fait de définir une rampe de type et de la suivre tout au long de l’expérience de l’application offre une expérience utilisateur exceptionnelle avec une hiérarchie d’informations cohérente.

![Exemples de rampe de type](images/typography-ramp-1000px.jpg)<br>
*Définir votre rampe de type et la suivre tout au long de l’expérience de l’application*

### <a name="limit-your-fonts"></a>Limiter vos polices

Évitez d’utiliser plus de deux familles de polices différentes dans un seul contexte. Un trop grand nombre de polices rompt l’harmonie et la cohérence de votre expérience et complique la consommation d’informations. Dans HoloLens, étant donné que les informations sont superposées en plus de l’environnement physique, l’utilisation d’un trop grand nombre de styles de police dégradera l’expérience. Segoe UI est la police de toutes les conceptions numériques Microsoft. Il est utilisé de manière cohérente dans le shell Windows Mixed Reality. Vous pouvez télécharger le fichier de police Segoe UI à partir de la page de la [boîte à outils de conception Windows](https://docs.microsoft.com/windows/uwp/design-downloads/).

[Plus d’informations sur la police Segoe UI](https://docs.microsoft.com/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a>Évitez les poids des polices fines

Évitez d’utiliser des pondérations de police légère ou semilight pour les tailles de type inférieures à 42 PT, car les traits verticaux fins vibreront et dégradent la lisibilité. Les polices modernes avec suffisamment d’épaisseur de trait fonctionnent bien. Par exemple, Helvetica et Arial sont lisibles dans HoloLens en utilisant des pondérations standard ou en gras.

### <a name="color"></a>Color

Dans HoloLens, étant donné que les hologrammes sont construits avec un système d’éclairage additif, le texte blanc est très lisible. Vous trouverez des exemples de texte blanc dans le menu Démarrer et la barre des applications. Même si le texte blanc fonctionne bien sans une plaque arrière sur HoloLens, un arrière-plan physique complexe peut rendre le type difficile à lire. Nous vous recommandons d’utiliser du texte blanc sur une plaque de fond sombre ou coloré pour améliorer le focus de l’utilisateur et réduire la distraction d’un arrière-plan physique.

<br>


![Nous vous recommandons d’utiliser du texte blanc sur une plaque d’arrière-plan sombre ou colorée. ](images/typography-whiteonblack2-1000px.jpg)
 *Exemples de texte blanc sur une plaque d’arrière-plan foncée ou colorée.*
<br>

Pour utiliser du texte foncé, vous devez utiliser une plaque de retour brillant pour la rendre lisible. Dans les systèmes de couleurs additives, le noir est affiché comme transparent. Cela signifie que vous ne verrez pas le texte noir sans plaque arrière colorée.

:::row:::
    :::column:::
        ![Exemples de blanc sur noir et noir sur du texte blanc](images/typography-whiteonblack.png)<br>
        *Exemples de blanc sur noir et noir sur du texte blanc*<br>
    :::column-end:::
    :::column:::
        ![Exemples de texte noir dans les applications système-magasin et paramètres](images/640px-typography-blackonwhite.jpg)<br>
        *Exemples de texte noir dans les applications système-magasin et paramètres*<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="recommended-font-size"></a>Taille de police recommandée

Comme vous pouvez vous y attendre, les tailles de type que nous utilisons sur un PC ou un appareil tablette (généralement entre 12 et 32 points) semblent petite à une distance de 2 mètres. Elle dépend des caractéristiques de chaque police, mais en général, l’angle de visualisation minimal recommandé et la hauteur de police pour la lisibilité sont autour de 0.35 °-0,4 °/12.21-13.97 mm en fonction de nos études de recherche des utilisateurs. Il s’agit d’environ 35-40 PT avec le facteur de mise à l’échelle introduit dans le [texte de la page Unity](../develop/unity/text-in-unity.md) . 

Pour l’interaction proche à 0,45 m (45 cm), l’angle d’affichage de la police à la hauteur minimale et la hauteur sont de 0,4 °-0,5 °/3.14 – 3,9 mm. Il s’agit d’environ 9-12 PT avec le facteur de mise à l’échelle introduit dans le [texte dans Unity](../develop/unity/text-in-unity.md).

![Contenu de plage d’interaction near et Far ](images/typography-distance-1000px.jpg)
 *dans une plage d’interaction proche et éloignée*

### <a name="the-minimum-legible-font-size"></a>Taille de police minimale lisible

| Distance | Angle d’affichage | Hauteur du texte | Taille de police * * |
|---------|---------|---------|---------|
| 45 cm (distance de manipulation directe) | 0,4 °-0,5 ° | 3.14 – 3,9 mm | 8,9 – 11.13 PT |
| 2 m | 0.35 °-0,4 ° | 12.21 – 13.97 mm | 34.63-39.58 PT |

### <a name="the-comfortably-legible-font-size"></a>Taille de police lisible

| Distance | Angle d’affichage | Hauteur du texte | Taille de police * * |
|---------|---------|---------|---------|
| 45 cm (distance de manipulation directe) | 0,65 °-0,8 ° | 5.1-6.3 mm | 14.47-17.8 PT |
| 2 m | 0,6 °-0,75 ° | 20.9-26.2 mm | 59.4-74.2 PT |


Segoe UI (police par défaut pour Windows) fonctionne bien dans la plupart des cas. Évitez d’utiliser des familles de polices légères ou semi-claires dans une petite taille, car les traits verticaux fins vibreront et la lisibilité sera dégradée. Les polices modernes avec suffisamment d’épaisseur de trait fonctionnent bien. Par exemple, Helvetica et Arial semblent exceptionnels et sont lisibles dans HoloLens avec des pondérations standard ou en gras.

**Pour plus d’informations sur le calcul de la taille du texte dans Unity, reportez-vous à [texte dans Unity](../develop/unity/text-in-unity.md)**

![Affichage de la ](images/Text_In_Unity_ViewingAngle.jpg)
 *distance d’affichage de l’angle, angle et hauteur du texte*

<br>

---

## <a name="resources"></a>Ressources

:::row:::
    :::column:::
    ### <a name="segoe-fontsbr"></a>[Polices Segoe](https://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)<br>
    (Fichier zip)<br>
    ### <a name="hololens-fontbr"></a>[Police HoloLens](https://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)<br>
    (Fichier zip)<br>
    <br>
    *Image : la police HoloLens vous donne les glyphes de symboles utilisés dans Windows Mixed Reality.*
    :::column-end:::
        :::column:::
        ![La police HoloLens vous donne les glyphes de symboles utilisés dans Windows Mixed Reality](images/hololensmdl2symbols.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

## <a name="see-also"></a>Voir aussi

* [Texte dans Unity](../develop/unity/text-in-unity.md)
* [Couleurs, éclairage et matériaux](../color,-light-and-materials.md)
