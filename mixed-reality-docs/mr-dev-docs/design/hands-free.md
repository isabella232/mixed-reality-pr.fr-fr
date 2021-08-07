---
title: Mains libres
description: En savoir plus sur les difficultés auxquelles les utilisateurs peuvent être confrontés avec une interface mains-et-contrôleurs et sur les différentes alternatives mains libres.
author: hferrone
ms.author: v-hferrone
ms.date: 04/20/2019
ms.topic: article
keywords: en réalité mixte, mains libres, point de présence, regards, interaction, conception, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, HoloLens, MRTK, Shared Computer Toolkit de réalité mixte, entrée vocale, convivialité
ms.openlocfilehash: 725d8886d21b42ee4643680c0dc91c1d29c25f8409b0ed0828256564dde7545c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213533"
---
# <a name="hands-free"></a>Mains libres

## <a name="scenarios"></a>Scénarios

Comme indiqué dans la [vue d’ensemble du modèle d’interaction](interaction-fundamentals.md), une fois que vous avez identifié vos utilisateurs et leurs objectifs, posez-vous les questions environnementales ou de situation auxquelles ils peuvent être confrontés lorsqu’ils travaillent pour accomplir leurs tâches. Par exemple, de nombreux utilisateurs ont besoin d’utiliser leurs mains pour atteindre leurs objectifs réels, et ils auront des difficultés à interagir avec une interface de type mains et contrôleurs.

Voici quelques scénarios spécifiques : 
* Guidage pour effectuer une tâche, pendant que les mains de l’utilisateur sont occupées
* Référencement de matériaux lorsque les mains de l’utilisateur sont occupées
* Fatigue de la main
* Gants qui ne peuvent pas être suivis
* Transport d’objet avec les mains
* Maladroite sociale lors de l’utilisation de grands mouvements de main
* Espaces étroits

## <a name="hands-free-modalities"></a>Modalités des mains libres

### <a name="voice-input"></a>[Entrée vocale](voice-input.md)

L’utilisation de votre voix pour commande et contrôle d’une interface offre un moyen pratique de travailler sans mains et d’utiliser des raccourcis pour ignorer plusieurs étapes si vous le souhaitez. Avec les entrées vocales, l’utilisateur peut lire le nom du bouton à haute voix pour l’activer _(le voir, le prononcer)_ et communiquer avec un agent numérique qui peut accomplir des tâches pour vous.

### <a name="gaze-and-dwell"></a>[Pointer du regard et fixer](gaze-and-dwell.md)

Dans certaines situations mains libres, l’utilisation de votre voix n’est pas idéale, voire possible. Les environnements en usine bruyants, la confidentialité ou les normes sociales peuvent être des contraintes. Le modèle de point de vue de l’utilisateur permet à l’utilisateur de naviguer dans une application sans aucune entrée supplémentaire, en dehors de son oeil ou de son point de vue : l’utilisateur garde tout simplement Gazing (avec son en-tête ou ses yeux) à la cible et attend un moment pour l’activer. Pour en savoir plus sur les considérations de conception individuelles pour le point de vue et le point de vue, consultez la section [œil-point](gaze-and-dwell-eyes.md) de vue et [tête](gaze-and-dwell-head.md)de regard.

## <a name="transitioning-in-and-out-of-hands-free"></a>Transition vers et à l’extérieur des mains libres

Pour ces scénarios, le fait de libérer des mains de l’interaction avec les hologrammes pour l’exécution de commandes et la navigation peut aller de l’exigence absolue à l’exploitation de l’application, de bout en bout, à un confort supplémentaire que l’utilisateur peut passer à tout moment. 

Si l’application exige qu’elle soit toujours utilisée sans intervention, que ce soit à l’aide de son, de commandes vocales personnalisées ou de la commande vocale unique, « Select », veillez à effectuer les logements appropriés dans votre interface utilisateur. 

Si votre utilisateur cible doit passer des mains à la mains libres à sa discrétion, il est important de prendre en compte les principes suivants.

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a>Supposons que l’utilisateur est déjà dans le mode vers lequel il souhaite passer
par exemple, si l’utilisateur se trouve à l’usine, regarde une référence vidéo sur son HoloLens et décide de choisir une clé pour commencer à travailler, elle commence probablement à travailler sans qu’il soit nécessaire de cliquer sur un bouton. Elle peut appeler une session vocale à l’aide d’une commande vocale, son logement sur une interface utilisateur déjà visible pour commencer son logement, ou prononcer le mot « Select » (sélectionner).

L’utilisateur peut : 
* Passez à l’option mains libres pendant les mains libres
* Passez aux mains avec vos mains
* Basculer vers le contrôleur à l’aide d’un contrôleur 

### <a name="create-redundant-ways-to-switch-modes"></a>Créer des méthodes redondantes pour basculer entre les modes

Tandis que le premier principe concerne l’accès, la seconde concerne la disponibilité. Il ne s’agit pas d’un moyen unique de passer d’un mode à un autre. 

Voici quelques exemples : 
* Un bouton pour commencer les interactions vocales
* Commande vocale à utiliser pour la transition, en utilisant le point d’interposition

### <a name="add-a-dash-of-drama"></a>Ajouter un tiret de la fiction

Un changement de mode est une affaire importante. Il est important que lorsque ces transitions se produisent, il s’agit d’un commutateur explicite, même d’un commutateur spectaculaire, pour permettre à l’utilisateur de savoir ce qui s’est passé. 

## <a name="usability-checklist"></a>Liste de vérification de l’utilisation

**L’utilisateur peut-il faire tout et tout ce qui est mains libres, de bout en bout ?**
* Chaque interaction peut être accessible mains libres
* Assurez-vous qu’il existe un remplacement de tous les mouvements personnalisés, tels que le redimensionnement, le placement, les balayages, les robinets, etc.
* Veillez à ce que l’utilisateur ait toujours le contrôle de la présence, de l’emplacement et des commentaires de l’interface utilisateur.
    * Récupération de l’interface utilisateur
    * Adressage de l’interface utilisateur en dehors de l’affichage (angle de vue)
    * Combien je vois, où, quand

**Les mécanismes de l’interaction sont-ils enseignés et armés avec le bon intuitivité ?**

L’utilisateur a-t-il compris...
* ... Dans quel mode ils se trouvent-ils ?
* ... Qu’est-ce qu’il est possible de faire dans ce mode ?
* ... Quel est l’état actuel ?
* ... Comment elles peuvent être transférées ?
    
**L’interface utilisateur est-elle optimisée pour les mains libres ?**   

* Exemple : les intuitivité de logement ne sont pas intégrés aux modèles 2D typiques
* Exemple : le ciblage vocal est mieux adapté à la mise en surbrillance des objets
* Exemple : les interactions vocales sont meilleures avec les légendes qui doivent être activées

## <a name="see-also"></a>Voir aussi

* [Suivi oculaire sur HoloLens 2](eye-tracking.md)
* [Pointer et valider](gaze-and-commit.md)
* [Pointer du regard et fixer](gaze-and-dwell.md)
* [Mains : Manipulation directe](direct-manipulation.md)
* [Mains : Mouvements](gaze-and-commit.md#composite-gestures)
* [Mains : Pointer et valider](point-and-commit.md)
* [Interactions instinctuelles](interaction-fundamentals.md)
* [Entrée vocale](voice-input.md)
