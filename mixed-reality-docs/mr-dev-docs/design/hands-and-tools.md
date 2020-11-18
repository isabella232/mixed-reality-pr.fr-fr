---
title: Mains et contrôleurs de mouvement
description: En savoir plus sur les modèles d’interaction mains et Motion contrôleurs, qui peuvent supprimer la limite entre le virtuel et le physique.
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: La réalité mixte, les mains, les contrôleurs de mouvement, l’interaction, la conception, le casque de réalité mixte, le casque de réalité mixte, le casque de réalité virtuelle, HoloLens, MRTK et la réalité mixte Toolkit
ms.openlocfilehash: e931e5ec11548d9aab0d1dd7f8921dbc7554abab
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702155"
---
# <a name="hands-and-motion-controllers"></a>Mains et contrôleurs de mouvement
## <a name="scenarios"></a>Scénarios
Si vous choisissez d’adopter ce modèle d’interaction après avoir lu la [vue d’ensemble](interaction-fundamentals.md)de l’interaction, cela signifie que vous développez une application nécessitant que les utilisateurs utilisent deux mains pour interagir avec le monde holographique. Votre application va atteindre l’objectif de supprimer la limite entre les serveurs virtuel et physique.

Certains scénarios spécifiques peuvent être :
* Fournir aux travailleurs de l’information des écrans virtuels 2D avec affordances d’UI pour afficher et contrôler le contenu
* Mise à disposition des didacticiels et des guides des travailleurs de première ligne pour les lignes d’assemblage usine
* Développer des outils professionnels pour assister et former des professionnels de la santé  
* Utiliser des objets virtuels 3D pour décorer le monde réel ou créer un deuxième monde 
* Créer des services et des jeux basés sur l’emplacement en utilisant le monde réel comme arrière-plan

<br>

---

## <a name="hands-and-motion-controllers-modalities"></a>Modalités de contrôle des mains et des contrôleurs de mouvement

:::row:::
    :::column:::
       [![Manipulation directe avec les mains](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)<br>
       ### <a name="direct-manipulation-with-handsbr"></a>[Manipulation directe avec les mains](direct-manipulation.md)<br>
       Il s’agit d’une modalité tirant parti de la puissance des mains, avec laquelle les utilisateurs peuvent toucher et manipuler les hologrammes directement. En tirant parti de l’expérience de vie quotidienne et en fournissant un intuitivité visuel approprié, les utilisateurs peuvent utiliser la même méthode de manipulation d’objets réels pour interagir avec des objets virtuels.
    :::column-end:::
    :::column:::
       [![Pointer et valider avec les mains](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)<br>
        ### <a name="point-and-commit-with-handsbr"></a>[Pointer et valider avec les mains](point-and-commit.md)<br>
        Cette modalité permet aux utilisateurs d’interagir avec des hologrammes à distance. Il permet aux utilisateurs de tirer le meilleur parti de l’environnement. Les utilisateurs peuvent placer des hologrammes n’importe où et toujours y accéder à partir de n’importe quelle distance. Les modèles et les gestes mentals pour le contrôle et la manipulation des hologrammes 2D et 3D sont hautement synchronisés avec ceux de manipulation directe.
    :::column-end:::
    :::column:::
       [![Contrôleurs de mouvement](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)<br>
       ### <a name="motion-controllersbr"></a>[Contrôleurs de mouvement](motion-controllers.md)<br>
       Les contrôleurs de mouvement sont des outils qui étendent les capacités physiques de l’utilisateur en fournissant des interactions précises sur une grande variété de distances tout en utilisant l’une ou l’autre des mains. Ces accessoires de matériel fournissent des raccourcis vers de nombreuses interactions couramment utilisées et fournissent des commentaires surefooted et tactiles pour diverses actions. Actuellement, les contrôleurs de mouvement sont uniquement disponibles pour les scénarios Windows Mixed Reality (WMR). 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>Voir aussi
* [Suivre de la tête et valider](gaze-and-commit.md)
* [Suivre de la tête et stabiliser](gaze-and-dwell.md)
* [Manipulation directe avec les mains](direct-manipulation.md)
* [Pointer et valider avec les mains](point-and-commit.md)
* [Mains-libres](hands-free.md)
