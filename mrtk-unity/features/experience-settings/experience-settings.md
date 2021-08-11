---
title: Paramètres d’expérience
description: Documentation sur les différents paramètres d’expérience pour MRTK
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 19d812ccfa9c0317e40dee2b7d03220848782cef955ba859a150b4f4adc8aa99
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203244"
---
# <a name="experience-settings"></a>Paramètres d’expérience

L’un des défis liés à la création d’une interface utilisateur pour la réalité mixte est l’alignement sur différentes expériences. Avec MRTK, vous pouvez définir le `Target Experience Scale` et le `Content Offset` pour votre scène, configurer les éléments suivants pour qu’ils se comportent correctement pour l’échelle cible.

- Contenu de scène de réalité mixte
- Système de limites

  ![expérience Paramètres dans le profil de Configuration MRTK](../images/experience-settings/ExperienceSettings.png)

## <a name="target-experience-scale"></a>Mise à l’échelle de l’expérience cible

L' **échelle de l’expérience cible** spécifie l’environnement pour lequel l’expérience est conçue. Elle peut prendre les valeurs suivantes.

* *OrientationOnly* : expérience qui utilise uniquement l’orientation du casque et qui est alignée sur la gravité. L’origine du système de coordonnées est au niveau de la tête.
* *Assis* -expérience conçue pour une utilisation assise. L’origine du système de coordonnées est au niveau du plancher.
* En *position permanente* , une expérience conçue pour une utilisation stationnaire. L’origine du système de coordonnées est au niveau du plancher.
* *Salle* -expérience conçue pour prendre en charge le mouvement dans une salle. L’origine du système de coordonnées est au niveau du plancher.
* Une expérience *mondiale* conçue pour utiliser et se déplacer dans le monde physique. L’origine du système de coordonnées est au niveau de la tête.

## <a name="content-offset"></a>Décalage du contenu

Ce paramètre spécifie la hauteur au-dessus du plancher pour décaler le [contenu de scènes de réalité mixte](scene-content.md) quand le **type d’alignement** est défini pour s' **aligner avec l’échelle de l’expérience**
