---
title: étude de cas-3 HoloStudio l’interface utilisateur et les apprentissages de conception d’interaction
description: Conception de l’interface utilisateur et des interactions HoloStudio
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, HoloStudio Windows Mixed Reality
ms.openlocfilehash: 1b384a10d3fe53cf7e69c2e8437904040322dc213d9473d9ae9abf272c08ec5e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115195868"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a>étude de cas-3 HoloStudio l’interface utilisateur et les apprentissages de conception d’interaction

[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) était l’une des premières applications Microsoft pour HoloLens. Pour cette raison, nous avons dû créer de nouvelles pratiques pour l’interface utilisateur 3D et la conception d’interaction. Nous l’avons fait à travers un grand nombre de tests utilisateur, de prototypages, d’essais et d’erreurs.

nous savons que tous les utilisateurs n’ont pas les ressources nécessaires pour effectuer ce type de recherche. nous avions donc notre concepteur Sr. holographique, Marcus Ghaly, à partager trois choses que nous avons appris pendant le développement de HoloStudio sur la conception d’interface utilisateur et d’interaction pour les applications HoloLens.

## <a name="watch-the-video"></a>Regarder la vidéo

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a>Problème #1 : les gens ne veulent pas se déplacer dans leurs créations

nous avons initialement conçu le workbench dans HoloStudio comme un rectangle, comme vous le feriez dans le monde réel. Le problème est que les gens ont une durée de vie qui leur demande de rester quand ils sont assis sur un bureau ou qu’ils travaillent devant un ordinateur, de sorte qu’ils ne se déplacent pas dans l’atelier et explorent leur création en 3D de tous les côtés.

![la conception rectangulaire du workbench dans HoloStudio les utilisateurs dissuaded de se déplacer et de voir leurs créations de tous les côtés.](images/rectangular-workbench-500px.jpg)

Nous avons eu l’idée de faire en sorte que le banc d’essai fasse l’aller de l’avant, ce qui signifie qu’il n’y avait pas de « front » ou d’endroit évident que vous étiez supposé reposer. Lorsque nous avons testé cette solution, soudain, les utilisateurs ont commencé à se déplacer et à explorer leurs créations eux-mêmes.

![La conception circulaire Workbench encourage les utilisateurs à se familiariser avec leurs créations.](images/circular-workbench-500px.jpg)

**Nos enseignements**

Réfléchissez toujours à ce qui est confortable pour l’utilisateur. tirer parti de leur espace physique est une fonctionnalité utile de HoloLens et un élément que vous ne pouvez pas faire avec d’autres appareils.

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a>Problème #2 : les boîtes de dialogue modales sont parfois hors du frame holographique

Parfois, il se peut que votre utilisateur regarde dans une autre direction que celle qui nécessite une attention particulière dans votre application. Sur un PC, vous pouvez simplement afficher une boîte de dialogue, mais si vous effectuez cette opération dans un environnement 3D, il peut sembler que la boîte de dialogue s’affiche. Vous en avez besoin pour lire le message, mais leur instinct est de tenter de s’en éloigner. Cette réaction est intéressante si vous jouez à un jeu, mais dans un outil conçu pour le travail, il est moins que parfait.

Après avoir essayé plusieurs choses, nous avons finalement décidé d’utiliser un système de « bulles de pensée » pour nos boîtes de dialogue et d’ajouter des tendrils que les utilisateurs peuvent suivre à l’endroit où leur attention est nécessaire dans notre application. Nous avons également rendu l’impulsion tendrils, qui impliquait un sens de la direction afin que les utilisateurs connaissaient l’emplacement.

![Le système « bulle de pensée » comprenait des tendrilss d’impulsions qui offraient un sens de direction, les utilisateurs de premier plan à l’endroit où leur attention était nécessaire dans l’application.](images/thought-bubble-500px.jpg)

**Nos enseignements**

En 3D, il est beaucoup plus difficile d’alerter les utilisateurs en fonction de leurs besoins. L’utilisation de directeurs d’attention tels que le [son spatial](../design/spatial-sound.md), les rayons de lumière ou les bulles de pensée peut amener les utilisateurs à l’endroit où ils doivent être.

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a>#3 du problème : parfois, l’interface utilisateur peut être bloquée par d’autres hologrammes

Il peut arriver qu’un utilisateur souhaite interagir avec un hologramme et ses contrôles d’interface utilisateur associés, mais qu’il ne peut pas être affiché parce qu’un autre hologramme est devant eux. pendant que nous développions HoloStudio, nous avons utilisé la version d’évaluation et l’erreur pour nous trouver dans une solution.

![Un contrôle d’interface utilisateur associé à un hologramme peut être bloqué s’il existe un autre hologramme entre celui-ci et l’utilisateur qui porte HoloLens.](images/ui-blocked-500px.jpg)

Nous avons essayé de rapprocher le contrôle d’interface utilisateur de l’utilisateur afin qu’il n’ait pas pu être bloqué, mais il a été découvert qu’il n’était pas facile pour l’utilisateur d’examiner un contrôle qui était proche de vous en regardant simultanément un hologramme éloigné. Toutefois, si nous avons déplacé le contrôle devant l’hologramme le plus proche de l’utilisateur, il a pensé qu’il a été détaché de l’hologramme qu’il devrait affecter.

Nous avons finalement fini de dupliquer le contrôle de l’interface utilisateur et le placer à la même distance de l’utilisateur que l’hologramme auquel il est associé, de sorte qu’ils se sentent tous deux connectés. Cela permet à l’utilisateur d’interagir avec le contrôle même s’il est masqué.

![La solution : nous avons dupliqué le contrôle de l’interface utilisateur, qui permettait l’interaction avec le contrôle et a fait en sorte qu’il soit connecté à l’hologramme qu’il affectait.](images/ghosting-ui-500px.jpg)

**Nos enseignements**

Les utilisateurs doivent être en mesure d’accéder facilement aux contrôles d’interface utilisateur même s’ils ont été bloqués. par conséquent, déterminez les méthodes permettant de s’assurer que les utilisateurs peuvent effectuer leurs tâches, quel que soit l’endroit où leurs hologrammes se trouvent dans le monde réel.

## <a name="about-the-author"></a>À propos de l’auteur

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><b>Marcus Ghaly</b><br>Concepteur de SR. holographique @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Voir aussi
* [Interactions instinctuelles](../design/interaction-fundamentals.md)
