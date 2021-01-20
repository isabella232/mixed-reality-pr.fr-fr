---
title: Scale
description: L’une des clés pour afficher du contenu qui semble réaliste sous forme holographique est de simuler les statistiques visuelles du monde réel aussi fidèlement que possible.
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, style, conception, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle, HoloLens, échelle, hologrammes
ms.openlocfilehash: 12b1c96146f76274831c9bc3427cef93bb326f70
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583312"
---
# <a name="scale"></a>Scale

La clé de l’affichage de contenu holographique réaliste est le plus proche possible des statistiques visuelles du monde réel. Incorporer des signaux visuels pour aider les utilisateurs du monde réel à comprendre où se trouvent les objets, quelle est leur taille et à quoi ils servent. L’échelle d’un objet est l’une des indications visuelles les plus importantes, car elle donne à la visionneuse une idée de la taille des objets et des piles à son emplacement. En outre, l’affichage des objets à l’échelle réelle est l’un des principaux facteurs de différenciation de la réalité mixte en général : ce qui n’a pas été possible dans le cas d’un affichage précédent basé sur l’écran.

<br>

---

## <a name="how-to-suggest-the-scale-of-objects-and-environments"></a>Comment suggérer l’échelle des objets et des environnements

Il existe de nombreuses façons de suggérer l’échelle d’un objet, certaines d’entre elles ayant des effets possibles sur d’autres facteurs de perception. La première consiste à afficher les objets à une taille réelle et à conserver une taille réaliste au fur et à mesure que les utilisateurs se déplacent. Les hologrammes occupent une quantité différente de l’angle visuel d’un utilisateur lorsqu’ils sont plus proches ou plus éloignés, de la même façon que les objets réels.

### <a name="use-the-distance-of-objects-as-theyre-presented-to-the-user"></a>Utiliser la distance des objets à mesure qu’ils sont présentés à l’utilisateur

Une méthode courante consiste à utiliser la distance des objets à mesure qu’ils sont présentés à l’utilisateur. Par exemple, considérez la visualisation d’une grande voiture de famille devant l’utilisateur. Si la voiture était directement devant les deux dans la longueur du bras, elle serait trop grande pour tenir dans le champ de vue de l’utilisateur. Les objets de fermeture obligent l’utilisateur à déplacer son en-tête et son corps pour comprendre l’intégralité de l’objet. Si la voiture est placée plus loin (à travers la pièce), l’utilisateur peut établir un sens de l’échelle en regardant l’objet entier dans son champ d’affichage. Les utilisateurs peuvent ensuite se rapprocher de l’objet pour une inspection plus détaillée.

:::row:::
    :::column:::
        **[Volvo a utilisé cette technique pour créer une](https://www.youtube.com/watch?v=DilzwF90vec)** expérience de salle de présentation pour une nouvelle voiture, à l’aide de la mise à l’échelle de la voiture holographique de manière à ce que l’utilisateur ait des performances réalistes et intuitives. L’expérience commence avec l’hologramme de voiture sur une table physique, ce qui permet à l’utilisateur de comprendre la taille totale et la forme du modèle. Plus tard dans l’expérience, la voiture se développe en une échelle au-delà de la taille du champ de vision de l’appareil. Étant donné que l’utilisateur a déjà acquis une image de référence à partir du modèle le plus petit, il peut naviguer correctement autour des fonctionnalités de la voiture.<br>
        <br>
        *Image : expérience Volvo Cars pour HoloLens*
    :::column-end:::
        :::column:::
       ![Expérience Volvo Cars pour HoloLens](images/volvo-cars-microsoft-hololens-experience01-640px.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

### <a name="use-holograms-to-modify-the-users-real-space"></a>Utiliser des hologrammes pour modifier l’espace réel de l’utilisateur

Une autre méthode consiste à utiliser des hologrammes pour modifier l’espace réel de l’utilisateur, en remplaçant les murs ou les plafonds existants par des environnements ou en ajoutant des « trous » ou des « fenêtres ». Cela permet aux objets de taille supérieure de se faire passer pour l’espace physique. Par exemple, une grande arborescence peut ne pas tenir dans la plupart des salles de vie des utilisateurs, mais en plaçant un ciel virtuel sur leur plafond, l’espace physique se développe dans le virtuel. Cela permet à l’utilisateur de parcourir la base de l’arborescence virtuelle et de recueillir un sens de la mise à l’échelle et de l’apparence du monde réel. Les utilisateurs peuvent ensuite Rechercher qu’ils s’étendent bien au-delà de l’espace physique de la salle.

:::row:::
    :::column:::
        **[Minecraft a développé un concept d’expériences](https://minecraft.net/)** à l’aide d’une technique similaire. En ajoutant une fenêtre virtuelle à une surface physique, les objets existants dans la salle sont placés dans le contexte d’un environnement largement plus grand, au-delà des limitations de l’échelle physique de la pièce.<br>
        <br>
        *Image : expérience du concept Minecraft pour HoloLens*
    :::column-end:::
        :::column:::
       ![Expérience Minecraft concept pour HoloLens](images/800px-minecraftwindow-640px.jpg)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="experimenting-with-scale"></a>Expérimentation avec l’échelle

Les concepteurs ont expérimenté la modification de l’échelle en modifiant la taille réelle affichée de l’objet. En même temps, ils conservent une position d’objet unique pour rapprocher un objet qui se déplace vers la visionneuse sans aucun mouvement réel. Cela a été testé dans certains cas comme un moyen de simuler un affichage plus étroit des éléments tout en respectant les limitations de confort potentielles liées à l’affichage du contenu virtuel plus près que la « zone de confort ».

Cela peut toutefois créer quelques artefacts possibles dans l’expérience :
* Pour les objets virtuels qui représentent un objet avec une taille « connue » pour la visionneuse, la modification de l’échelle sans modifier la position amène aux signaux visuels conflictuels. Les yeux peuvent toujours « voir » l’objet à une profondeur en raison des indications vergence. Pour plus d’informations, consultez l’article [Comfort](comfort.md) . La taille agit comme une indication monoculaire que l’objet peut se rapprocher. Ces signaux conflictuels conduisent à des perceptions confuses. les visionneuses voient souvent que l’objet reste en place (en raison de la profondeur constante) mais se multiplient rapidement.
* Dans certains cas, la modification de l’échelle est considérée comme un repère « à l’aise », alors que l’objet peut ou non être vu pour changer l’échelle par une visionneuse, mais semble bouger directement vers les yeux de la visionneuse (ce qui peut être une sensation inconfortable).
* Avec les surfaces de comparaison dans le monde réel, ces changements de mise à l’échelle sont parfois considérés comme la modification de la position le long de plusieurs axes. les objets semblent déplacés vers le bas au lieu de se rapprocher (comme dans une projection 2D de mouvement 3D dans certains cas).
* Enfin, pour les objets sans une taille « réelle » connue (par exemple, des formes arbitraires avec des tailles arbitraires, des éléments d’interface utilisateur, etc.), la modification de l’échelle peut agir de façon fonctionnelle pour imiter les modifications de distance. Les visionneuses n’ont pas autant de signaux descendants préexistants pour comprendre la taille réelle de l’objet ou l’emplacement. l’échelle peut donc être traitée comme un signal plus important.

<br>

---

## <a name="see-also"></a>Voir aussi
* [Couleurs, éclairage et matériaux](./color-light-and-materials.md)
* [Typographie](typography.md)
* [Conception du son spatial](spatial-sound-design.md)