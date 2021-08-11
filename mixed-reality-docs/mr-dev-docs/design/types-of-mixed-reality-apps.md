---
title: Types d’applications de réalité mixte
description: Découvrez les expériences prises en charge par la plateforme de réalité mixte, des environnements immersifs à la couche d’informations légère sur l’environnement d’un utilisateur.
author: rwinj
ms.author: willyang
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, conception, modèles d’application, casque de réalité mixte, casque Windows Mixed reality, casque de réalité virtuelle, HoloLens
ms.openlocfilehash: 13d4f538148b2c6b6f4df422c6c423f2b2710ca1ba2d98fe4f952c14284035f8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115218920"
---
# <a name="types-of-mixed-reality-apps"></a>Types d’applications de réalité mixte

l’un des avantages du développement d’applications pour Windows Mixed Reality est le spectre des expériences que la plateforme peut prendre en charge. Des environnements virtuels entièrement immersifs à la couche d’informations légère sur l’environnement actuel d’un utilisateur, Windows Mixed Reality fournit un ensemble d’outils robustes pour donner vie à toute expérience. Il est important pour un concepteur d’applications de comprendre au plus tôt son processus de développement quant à la position de son expérience sur ce spectre. Cette décision aura un impact sur la conception de la conception d’application et le chemin d’accès technologique pour le développement.

## <a name="enhanced-environment-apps-hololens-only"></a>applications d’environnement améliorées (HoloLens uniquement)

L’un des moyens les plus puissants dont la réalité mixte peut apporter de la valeur est de permettre aux développeurs de placer des informations ou du contenu numériques dans l’environnement actuel d’un utilisateur. Cette approche est populaire pour les applications où le positionnement contextuel du contenu numérique dans le monde réel est primordial et que l’environnement réel de l’utilisateur est « présent » pendant que son expérience est essentielle. Les utilisateurs peuvent également se déplacer entre les tâches numériques réelles en toute simplicité. Cela prête encore plus de certaine crédibilité à la promesse que les applications de réalité mixte que l’utilisateur voit font véritablement partie de leur environnement.

![Applications d’environnement améliorées](images/enhancedenvironmentapps-640px.jpg)<br>
*Applications d’environnement améliorées*

**Exemples d’utilisation**
* Application de style Notepad de réalité mixte qui permet aux utilisateurs de créer et de placer des notes dans leur environnement
* Une application de télévision de réalité mixte placée dans un endroit confortable pour l’affichage
* Application de cuisine à la réalité mixte placée au-dessus de l’île de cuisine pour faciliter la tâche de cuisson
* Application de réalité mixte qui donne aux utilisateurs le sentiment de « x-ray vision » (autrement dit, un hologramme placé par-dessus et imite un objet réel, tout en permettant à l’utilisateur de voir « dedans » de façon holographique)
* Annotations de réalité mixte placées dans une fabrique pour fournir les informations nécessaires pour le travail
* Détection mixte de la réalité dans un espace de travail
* Expériences de bureau de la réalité mixte (autrement dit, des expériences de style de jeu)
* Applications de communication de réalité mixte comme Skype

## <a name="blended-environment-apps"></a>Applications d’environnement fusionné

étant donné Windows Mixed Reality capacité de reconnaître et de mapper l’environnement de l’utilisateur, il est en mesure de créer une couche numérique qui peut être superposée à l’espace de l’utilisateur. La couche mince respecte la forme et les limites de l’environnement de l’utilisateur, mais l’application peut choisir de transformer certains éléments qui conviennent le mieux pour plonger l’utilisateur dans l’application. C’est ce que l’on appelle une application d’environnement fusionné. Contrairement à une application d’environnement améliorée, les applications de l’environnement fusionné peuvent uniquement s’occuper de l’environnement pour mieux utiliser son composition pour encourager un comportement spécifique de l’utilisateur (par exemple, encourager le déplacement ou l’exploration) ou remplacer des éléments par des modifications (un compteur de cuisine est dépouillé pour afficher un modèle de mosaïque différent). Ce type d’expérience peut même transformer un élément en un objet complètement différent, tout en conservant les dimensions approximatives de l’objet en tant que base (un îlot de cuisine est transformé en benne pour un jeu de criminalité plus excitant).

![Applications d’environnement fusionné](images/blendedenvironmentapps-640px.jpg)<br>
*Applications d’environnement fusionné*

**Exemples d’utilisation**
* Une application de conception intérieure de réalité mixte qui peut peindre des murs, des plans de plan ou des planchers dans des couleurs et des modèles différents
* Application de réalité mixte permettant à un concepteur automobile de coucher de nouvelles itérations de conception pour une prochaine actualisation de la voiture sur une voiture existante
* Une vitre est « couverte » et remplacée par un peuplement de réalité mixte dans le jeu des enfants
* Un bureau est « couvert » et remplacé par une benne de réalité mixte dans un jeu plus excitant du crime
* Une lanterne en suspens est « couverte » et remplacée par un poteau à l’aide de la même forme et de la même dimension
* Application qui permet aux utilisateurs d’éclater des trous dans leurs murs réels ou immersifs, qui révèlent un monde magique

## <a name="immersive-environment-apps"></a>Applications d’environnement immersif

Les applications d’environnement immersif sont centrées autour d’un environnement qui modifie complètement le monde de l’utilisateur et peut les placer dans un autre temps et dans un autre espace. Ces environnements peuvent sembler réels, créant des expériences immersifs et excitantes qui ne sont limitées que par l’imagination de l’auteur de l’application. contrairement aux applications d’environnement fusionné, une fois que Windows Mixed Reality identifie l’espace de l’utilisateur, une application d’environnement immersif peut ignorer totalement l’environnement actuel de l’utilisateur et la remplacer par l’un de ses propres actions. Ces expériences peuvent également séparer le temps et l’espace, ce qui signifie qu’un utilisateur peut parcourir les rues de Rome dans une expérience immersive, tout en restant relativement toujours dans son espace réaliste. Le contexte de l’environnement réel peut ne pas être important pour une application d’environnement immersif.

![Applications d’environnement immersif](images/windows-mixed-reality-640px.jpg)<br>
*Applications d’environnement immersif*

**Exemples d’utilisation**
* Une application immersif qui permet à un utilisateur de se séparer de son propre espace (en d’autres termes, suivez un célèbre bâtiment, Musée, ville populaire)
* Application immersif qui orchestre un événement ou un scénario autour de l’utilisateur (autrement dit, une bataille ou une performance)

## <a name="see-also"></a>Voir aussi

* [Vue d’ensemble du développement](../develop/development.md)
* [Modèle d’application](app-model.md)
* [Vues d’applications](app-views.md)
