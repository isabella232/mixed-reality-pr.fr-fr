---
title: Suivre de la tête et valider
description: Prise en main du modèle d’entrée point-Orient et validation, y compris le dimensionnement, le positionnement et la stabilisation cibles.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: La réalité mixte, le point de présence, le regard, l’interaction, la conception, le casque de la réalité mixte, le casque Windows Mixed Reality, le casque de la réalité virtuelle, HoloLens, MRTK, le kit de configuration de la réalité mixte, la cible, le lissage
ms.openlocfilehash: 74f963a6b450d1fb7f1302886a01c12cf79ce28a
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196514"
---
# <a name="head-gaze-and-commit"></a>Suivre de la tête et valider

Le _point de regard et la validation de tête_ est un cas particulier du modèle d’entrée de pointage et de [validation](gaze-and-commit.md) qui implique le ciblage d’un objet avec une direction de la tête des utilisateurs. Vous pouvez agir sur la cible à l’aide d’une entrée secondaire, telle que la commande vocale TAP ou Select de mouvement direct. 

## <a name="device-support"></a>Prise en charge des appareils

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Modèle d’entrée</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1ère génération)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Casques immersifs</strong></a></td>
    </tr>
     <tr>
        <td>Suivre de la tête et valider</td>
        <td>✔️ Recommandé</td>
        <td>✔️ Recommandé (troisième choix ; <a href="interaction-fundamentals.md">voir les autres options</a>)</td>
        <td>➕ Autre option</td>
    </tr>
</table>

---

## <a name="head-and-eye-tracking-design-concepts-demo"></a>Démonstration des concepts de conception du suivi des têtes et des yeux

Si vous souhaitez voir les concepts de conception des suivis des yeux et des yeux en action, consultez notre démonstration **conception d’hologrammes-TETE Tracking and Eye Tracking (** en anglais) ci-dessous. Une fois que vous avez terminé, poursuivez sur pour obtenir une présentation plus détaillée des rubriques spécifiques.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

*Cette vidéo a été extraite de l’application HoloLens 2 « Designing hologrammes ». Téléchargez et profitez de l’expérience complète [ici](https://aka.ms/dhapp).*

## <a name="target-sizing-and-feedback"></a>Dimensionnement des cibles et retour

Le point de regard de l’en-tête a été affiché à plusieurs reprises pour être utilisable pour un ciblage précis, mais il fonctionne souvent mieux pour le ciblage brut, en acquérant des cibles plus volumineuses. Les tailles cibles minimales de 1 degré à 1,5 degrés permettent des actions utilisateur réussies dans la plupart des scénarios, bien que les cibles de 3 degrés offrent souvent une vitesse supérieure. La taille ciblée par l’utilisateur est en fait une zone 2D, même pour les éléments 3D, quelle que soit la projection vers laquelle elle doit être la zone cible. Il est utile de fournir une indication intéressante indiquant qu’un élément est « actif » (que l’utilisateur cible). Cela peut inclure des traitements tels que des effets de « survol » visibles, des surbrillances audio ou des clics, ou l’alignement clair d’un curseur avec un élément.

![Taille optimale de la cible à une distance de 2 mètres](images/gazetargeting-size-1000px.jpg)<br>
*Taille de cible optimale à une distance de 2 mètres*

<br>

![Exemple de mise en surbrillance d’un objet ciblé avec le regard](images/gazetargeting-highlighting-940px.jpg)<br>
*Exemple de mise en surbrillance d’un objet ciblé avec le regard*

## <a name="target-placement"></a>Placement de la cible

Souvent, les utilisateurs ne parviennent pas à trouver les éléments d’interface utilisateur situés trop hauts ou faibles dans leur champ d’affichage. La plus grande partie de leur attention se termine sur des points autour de leur objectif principal, ce qui est approximativement au niveau oculaire. Le fait de placer la plupart des cibles dans une bande raisonnable autour des yeux peut s’avérer utile. Étant donné la tendance pour les utilisateurs à se concentrer sur une petite zone visuelle à tout moment (le cône de vision est à peu près 10 degrés), le regroupement des éléments de l’interface utilisateur en fonction de leur degré de lien peut utiliser les comportements de chaînage de l’élément jusqu’à l’élément lorsqu’un utilisateur déplace le regard sur une zone. Quand vous concevez l’interface utilisateur, gardez à l’esprit les grandes variations potentielles du champ de vision entre les casques immersifs et HoloLens.

![Exemple d’éléments d’interface utilisateur groupés pour faciliter le ciblage avec le regard dans Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)<br>
*Exemple d’éléments d’interface utilisateur groupés pour faciliter le ciblage avec le regard dans Galaxy Explorer*

## <a name="improving-targeting-behaviors"></a>Amélioration des comportements de ciblage

Si l’intention de l’utilisateur de cibler un événement peut être déterminée ou rapprochée, il peut être utile d’accepter les tentatives d’interaction presque manquées comme si elles étaient ciblées correctement. Voici quelques-unes des méthodes qui peuvent être incorporées dans les expériences de réalité mixte :

### <a name="head-gaze-stabilization-gravity-wells"></a>Stabilisation avec suivi de la tête (« stabilisation de la gravité »)

Cette fonction doit être activée le plus ou la totalité du temps. Cette technique supprime les instabilités de tête et de cou naturelles que les utilisateurs peuvent avoir en mouvement en raison des comportements de recherche et de dictée.

### <a name="closest-link-algorithms"></a>Algorithmes du lien le plus proche

Ces algorithmes fonctionnent mieux dans des domaines avec du contenu interactif fragmenté. S’il y a une forte probabilité que vous puissiez déterminer ce à quoi un utilisateur tente d’interagir, vous pouvez compléter ses capacités de ciblage en supposant un certain niveau d’intention.

### <a name="backdating-and-postdating-actions"></a>Actions d’postdating et de mise à jour

Ce mécanisme est utile dans les tâches nécessitant de la vitesse. Lorsqu’un utilisateur parcourt une série de manoeuvres de ciblage et d’activation à la vitesse, il est utile de supposer une certaine intention. Il est également utile d’autoriser les étapes manquées à agir sur les cibles dont l’utilisateur avait le focus légèrement avant ou légèrement après le TAP (50 ms avant/après).

### <a name="smoothing"></a>Adoucissage

Ce mécanisme est utile pour le tracé des mouvements, en réduisant les légères gigues et les tremblements en raison des caractéristiques naturelles de mouvement de la tête. En cas de lissage sur les mouvements de tracés, lisse par la taille et la distance des mouvements plutôt qu’au fil du temps.

### <a name="magnetism"></a>Magnétisme

Ce mécanisme peut être considéré comme une version plus générale des algorithmes de lien les plus proches : le fait de dessiner un curseur vers une cible ou d’augmenter simplement hitboxes, de façon visible ou non, à mesure que les utilisateurs approchent les cibles probables à l’aide d’une connaissance de la disposition interactive pour une meilleure approche de l’intention de l’utilisateur. Cela peut être puissant pour les petites cibles.

### <a name="focus-stickiness"></a>Adhérence du focus

Lors de la détermination des éléments interactifs proches à donner, le focus sur, l’adhérence au focus fournit un décalage à l’élément qui est actuellement concentré. Cela permet de réduire les comportements de changement de focus erratiques lorsqu’ils flottent à un point médian entre deux éléments avec un bruit naturel.

## <a name="see-also"></a>Voir aussi

* [Interaction basée sur le regard](eye-gaze-interaction.md)
* [Pointer du regard et fixer](gaze-and-dwell.md)
* [Mains : Manipulation directe](direct-manipulation.md)
* [Mains : Mouvements](gaze-and-commit.md#composite-gestures)
* [Mains : Pointer et valider](point-and-commit.md)
* [Interactions instinctuelles](interaction-fundamentals.md)
* [Entrée vocale](voice-input.md)