---
title: À propos de Maquette
description: Présentation de maquette et de ses fonctionnalités.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, Maquette, prototypage, réalité mixte, réalité virtuelle, VR, MR, commentaires, Hub de commentaires, bogues
ms.openlocfilehash: 81c09bf22ea531a76156c9264e127593b6302ad5d0bcb248de9518bfb647717b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197886"
---
# <a name="about-maquette"></a>À propos de Maquette

<!-- TODO(Harrison): Need consolidated logo with text -->
![Présentation du logo ](../images/MaquetteIcon.png) MaquetteScript

<!-- TODO(Harrison/Stefan): Add more high level, less technical explanation of what Maquette is and why it's useful in MR development. 
          - Differentiate between Maquette and MaquetteScript
          - Separate out each of Maquette's main parts and add content
          - Give brief explanations of use case or examples
-->
Maquette intègre le JavaScript standard ECMA 5,1 pour permettre l’investissement de l’interactivité dans les scènes maquette et les objets qui peuvent être modifiés et exécutés à partir de VSCode. Les propriétés des objets sont exposées pour la lecture et le paramétrage à partir d’un script, de méthodes d’objet appelées, ainsi que d’événements système et d’objets. Le script peut également interagir avec maquette lui-même par le biais d’objets système accessibles via le script. Les différents contrôles d’interface utilisateur avec lesquels l’utilisateur peut interagir font partie du système. Ils peuvent être ajoutés lors de la création dans maquette ou créés et gérés à partir d’un script. Les événements d’interaction utilisateur avec ces éléments (entrée de données, clics, etc.) sont également exposés au script en tant qu’événements. Grâce à ces ajouts, il est possible de créer des scènes simples ou complexes, des expériences à la visualisation des données à des explorations de scénarios utilisateur de réalité mixte pour réaliser des expériences complètes dans AR ou VR.

<p align="center">
  <img src="images/ScriptingOverview.png" alt="Scripting overview video screenshot">
</p>

<!-- TODO(Harrison/Stefan): Get this video recorded or create the content in text form until it's available. -->
vidéo 60 second’ish
* Carte de titre d’entrée
  * Création d’un contenu de réalité mixte interactif dans maquette
  * Script/interactivité/système d’interface utilisateur
* Les écrans de bienvenue de VO d’équipe ou de vidéo ?  raisons
  * raisonnement derrière l’écriture de scripts pour permettre la création de contenu RM interactif
  * toucher sur la façon dont il peut être utilisé dans les traits de pinceau très larges
* Scripting des Vingette en action
  * Composition, boîte de dialogue
  * Création d’une application à partir du plan (démonstration de l’application de cuisine)
  * Composer dans le modèle Photogrammetry
  * Interaction avec le Guide de dépannage
  * Vue d’écran du débogage des scripts dans VSCode
  * Obtention de l’accès au script à partir d’un objet dans la scène
  * Etc...
* Carte de titre résumé à la fin
  * Lien vers maquette
  * Où accéder à la prise en main des scripts
  * Annonces/État/communauté
  * Regardez par avance pour voir ce que vous pouvez faire/soumissions ( ?)
  * Commentaires et comment nous pouvons vous servir mieux

<!-- TODO(Harrison): Consider breaking this out into a Maquette journey doc or section as applicable. -->
* [Prise en main](installation.md)
* [Exemples et exemples d’applications](../samples/overview.md)
* [Support technique](../resources/support.md)

<!-- TODO(Harrison): Need to find out why docs feedback footer isn't appearing. -->
## <a name="send-us-feedback"></a>Envoyez-nous des commentaires

Nous sommes impatients de vous entendre sur vos expériences et résultats. Les commentaires, suggestions et rapports de bogues sont toujours les bienvenus !
<lien ? >