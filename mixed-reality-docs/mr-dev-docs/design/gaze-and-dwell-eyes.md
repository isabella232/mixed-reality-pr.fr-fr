---
title: Pointer du regard et fixer
description: Démarrez avec une vue d’ensemble du modèle d’entrée Pointer du regard et fixer, avec des modèles d’interaction, des guides pour la conception et des défis uniques.
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
ms.localizationpriority: high
keywords: Suivi oculaire, réalité mixte, entrée, suivi du regard, ciblage du regard, HoloLens 2, sélection basée sur le regard, fixer, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, HoloLens, MRTK, Mixed Reality Toolkit, conception
ms.openlocfilehash: dfe74ee1fe304cc63bb0c547d01ebadeb0469b171caa806671887817c17f92ef
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115201830"
---
# <a name="eye-gaze-and-dwell"></a>Pointer du regard et fixer

Le modèle d’interaction _« Pointer du regard et fixer »_ est un cas particulier du modèle d’interaction [Pointer du regard et valider](gaze-and-commit.md) :
1. Regardez une cible. 
2. Pour confirmer votre intention de sélectionner cette cible, utilisez une entrée explicite secondaire : _Continuez simplement de regarder la cible que vous voulez sélectionner_.

## <a name="advantages-of-the-eye-gaze-and-dwell-interaction-model"></a>Avantages du modèle d’interaction « Pointer du regard et fixer » 

Lorsque vos mains sont déjà occupées par une tâche ou chargées d’outils, vous ne pouvez probablement pas les utiliser pour interagir avec des hologrammes.
Une alternative d’interaction sans les mains pour sélectionner des hologrammes consiste à « pointer du regard et fixer », autrement dit, à _« regarder et maintenir son regard »_ . Avec cette approche, même les utilisateurs soumis à de fortes contraintes, dans l’incapacité de tourner complètement la tête ou le corps, peuvent interagir avec des hologrammes (par exemple, dans un environnement de travail très confiné).
L’utilisateur continue simplement de regarder la cible qu’il souhaite sélectionner et une rétroaction différente s’affiche pour indiquer le processus.

## <a name="challenges-of-the-eye-gaze-and-dwell-interaction-model"></a>Défis du modèle d’interaction « Pointer du regard et fixer »

En règle générale, nous vous recommandons de n’utiliser les activations par fixation du regard qu’en dernier recours si aucune entrée vocale ou manuelle n’est disponible. En effet, le choix de la durée de fixation du regard s’avère délicat. Alors que les utilisateurs débutants acceptent de fixer leur regard plus longtemps, les utilisateurs experts préfèrent un parcours rapide et efficace de leurs expériences. Cette différence rend difficile la manière d’ajuster la durée du regard selon les besoins spécifiques de l’utilisateur.
Si la durée de fixation du regard est trop courte : L’utilisateur peut finir par se sentir dépassé par tous les hologrammes qui réagissent constamment à son regard. Si la durée de fixation du regard est trop longue : L’expérience peut sembler trop lente et hachée, car l’utilisateur doit fixer les cibles pendant trop longtemps.

## <a name="design-recommendations"></a>Recommandations de conception

Nous vous recommandons d’utiliser une approche avec deux états pour la rétroaction d’un regard fixe :
1. *Délai initial* : Quand l’utilisateur commence à fixer une cible, rien ne doit se produire immédiatement, sans quoi l’expérience utilisateur risque de devenir désagréable et pesante. Lancez plutôt un minuteur pour détecter si l’utilisateur fixe délibérément son regard sur la cible ou s’il pose à peine son regard dessus.
Nous recommandons un délai initial compris entre 150 et 250 ms dans une proximité donnée (ce qui signifie que l’utilisateur pointe son regard et fixe précisément, plutôt qu’il ne regarde vaguement une cible plus large).  
2. *Lancement de la rétroaction du regard fixe :* Après vérification que l’utilisateur regarde délibérément la cible, commencez à faire apparaître la rétroaction du regard fixe pour informer l’utilisateur que l’activation par fixation du regard est lancée. 
3. *Rétroaction en continu :* Pendant que l’utilisateur regarde toujours la cible, faites apparaître un indicateur de progression pour que l’utilisateur sache qu’il doit continuer à fixer la cible. En particulier pour les entrées par pointage du regard, nous vous recommandons d’_attirer l’attention visuelle de l’utilisateur_ en commençant avec un cercle ou une sphère volumineuse qui rétrécit progressivement. L’utilisation d’un indicateur pour l’état final (petit cercle) vous aide à communiquer à l’utilisateur à quel moment la rétroaction est terminée. Vous trouverez ci-dessous un exemple d’illustration. 
4. *Fin :* Si l’utilisateur a continué de fixer la cible (pendant 650 à 850 ms supplémentaires), effectuez l’activation de la rétroaction et sélectionnez la cible fixée.

![États de rétroaction](images/eyes_dwellstate_recommendation.png)<br>

## <a name="see-also"></a>Voir aussi

* [Eye-tracking](eye-tracking.md)
* [Pointer du regard et valider](gaze-and-commit-eyes.md)
* [Pointer et valider](gaze-and-commit.md)
* [Pointer du regard et fixer](gaze-and-dwell.md)
* [Entrée vocale](../out-of-scope/voice-design.md)
