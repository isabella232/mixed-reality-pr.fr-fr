---
title: Étude de cas-leçons de la cuisine de Lowe
description: l’équipe HoloLens souhaite partager certaines des meilleures pratiques qui ont été dérivées du projet de HoloLens du Lowe.
author: brandonbray
ms.author: kevincol
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Lowe, HoloLens, cuisine, étude de cas
ms.openlocfilehash: f2428a23e07d62156d38f43dfd5d6ddda20d57340d17908cf326ca9f37d223b9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210389"
---
# <a name="case-study---lessons-from-the-lowes-kitchen"></a>Étude de cas-leçons de la cuisine de Lowe

l’équipe HoloLens souhaite partager certaines des meilleures pratiques qui ont été dérivées du projet de HoloLens du Lowe. vous trouverez ci-dessous une vidéo de la HoloLens Lowe projetée, présentée dans le discours 2016 de Satya.
<br>
>[!VIDEO https://www.youtube.com/embed/gC_4JxF0e_k]

## <a name="lowes-hololens-best-practices"></a>meilleures pratiques pour le HoloLens de Lowe

les deux vidéos couvrent les meilleures pratiques qui ont été dérivées du pilote HoloLens de la Lowe, qui se trouvait dans deux magasins Lowe depuis avril 2016. Les principales rubriques sont les suivantes :
* Optimiser les performances d’un appareil mobile
* Créer des méthodes d’expérience utilisateur avec une image holographique complète (2e contact)
* Alignement de précision (2e contact)
* Expériences holographiques partagées (2e contact)
* Interaction avec les clients (2e Conférence)

## <a name="video-1"></a>Vidéo 1

**optimiser les performances d’un appareil mobile** HoloLens est un appareil non attaché avec tout le traitement effectué sur l’appareil. Cela nécessite une plate-forme mobile et requiert un mentalités similaire à la création d’applications mobiles. Microsoft recommande que votre HoloLens application maintienne 60FPS pour fournir une expérience délicieuse à vos utilisateurs. Une faible FPS peut entraîner des hologrammes instables.

voici quelques-uns des éléments les plus importants à examiner lors du développement sur HoloLens est l’optimisation/la décimalisation des ressources, à l’aide de nuanceurs personnalisés (disponibles gratuitement dans la [Shared Computer Toolkit HoloLens](https://github.com/Microsoft/HoloToolkit-Unity)). Une autre considération importante consiste à mesurer la fréquence d’images à partir du début de votre projet. Selon le projet, l’ordre d’affichage de vos ressources peut également être un grand contributeur
<br>
>[!VIDEO https://www.youtube.com/embed/o0QIPwgiP9A]

## <a name="video-2"></a>Vidéo 2

**Créer des méthodes d’expérience utilisateur avec une image holographique complète** Il est important de comprendre le positionnement des hologrammes dans un monde physique. Avec Lowe, nous parlerons des différentes méthodes d’expérience utilisateur qui permettent aux utilisateurs d’expérimenter leurs hologrammes tout en continuant à voir l’environnement plus grand des hologrammes.

**Alignement de précision** Pour le scénario de Lowe, il était primordial d’avoir un alignement précis des hologrammes sur la cuisine physique. Nous nous penchons sur les techniques pour garantir une expérience qui convainc les utilisateurs que leur environnement physique a changé.

**Expériences holographiques partagées** Les couples sont le principal moyen de consommer l’expérience du Lowe. Une personne peut modifier le plan de plan et l’autre personne verra les modifications. Nous avons appelé « expériences partagées ».

**Interaction avec les clients** les concepteurs de Lowe n’utilisent pas de HoloLens, mais ils ont besoin de voir ce que les clients voient. Nous montrons comment capturer ce que le client voit sur une application UWP.
<br>
>[!VIDEO https://www.youtube.com/embed/LceMdyKZ4PI]
