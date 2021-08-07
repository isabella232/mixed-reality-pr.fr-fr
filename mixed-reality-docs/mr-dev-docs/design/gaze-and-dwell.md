---
title: Pointer du regard et fixer
description: Découvrez une vue d’ensemble de l’œil et du modèle d’entrée de point d’entrée pour les applications de réalité mixte.
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: la réalité mixte, le regard, le logement, l’interaction, la conception, le suivi des yeux, le suivi des têtes, le casque de réalité mixte, le casque windows mixed reality, le casque de réalité virtuelle, le HoloLens, MRTK, la réalité mixte Shared Computer Toolkit
ms.openlocfilehash: c65c13b06df70ed5471b283ad349dd72e1575018a98913177983d7a13571d666
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213673"
---
# <a name="gaze-and-dwell"></a>Pointer du regard et fixer

Quand les mains sont occupées avec des outils et des pièces, les mouvements peuvent être fastidieux, voire impossibles.
Les commandes vocales peuvent également être peu fiables dans certains contextes, par exemple dans des conditions excessivement intenses.
Le point de regard et le point de vue offre un mécanisme familier et facile à maîtriser pour le fonctionnement des têtes et des mains-libres sur HoloLens.
En outre, le point de regard et le bruit est un excellent secours, qui est indépendant des contraintes de bruit ou de silence dans l’environnement d’exploitation.
Nous distingueons deux variantes de point de _regard_ et de [tête : le point](gaze-and-dwell-head.md) de regard et le point d’appui [.](gaze-and-dwell-eyes.md)

## <a name="scenarios"></a>Scénarios

Le point d’accès est très bien utilisé dans les scénarios où les mains d’une personne sont occupées par d’autres tâches, et la voix n’est pas 100% fiable ou disponible en raison de contraintes environnementales ou sociales.
Un bon exemple est une personne portant un appareil HoloLens pour superposer des informations de référence tout en réparant un moteur de voiture.
Ses mains sont occupées par des outils ou supportent son corps quand elle se penche dans le compartiment du moteur.
L’espace du garage est bruyant, les coups et bourdonnement constants des outils rendant difficile l’utilisation de commandes vocales.
le point de regard permet à la personne qui utilise le HoloLens de parcourir en toute confiance son document de référence sans interrompre son flux de travail.

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
        <td>Suivre de la tête et stabiliser</td>
        <td>✔️ Recommandé</td>
        <td>✔️ Recommandé</td>
        <td>✔️ Recommandé</td>
    </tr>
     <tr>
        <td>Pointer du regard et fixer</td>
        <td>❌ Non disponible</td>
        <td>✔️ Recommandé</td>
        <td>❌ Non disponible</td>
    </tr>
</table>


<br>

---

 ## <a name="see-also"></a>Voir aussi

* [Interaction basée sur le regard](eye-gaze-interaction.md)
* [Suivi oculaire sur HoloLens 2](eye-tracking.md)
* [Pointer et valider](gaze-and-commit.md)
* [Mains : Manipulation directe](direct-manipulation.md)
* [Mains : Mouvements](gaze-and-commit.md#composite-gestures)
* [Mains : Pointer et valider](point-and-commit.md)
* [Interactions instinctuelles](interaction-fundamentals.md)
* [Entrée vocale](voice-input.md)