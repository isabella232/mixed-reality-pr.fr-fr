---
title: Qu’est-ce que la réalité mixte ?
description: Discussion sur la réalité mixte, présentation de l’utilisation des appareils AR et VR sur le spectre de réalité mixte.
author: qianw211
ms.author: v-qianwen
ms.date: 07/01/2021
ms.topic: article
keywords: Réalité mixte, holographique, RA, RV, RM, XR, réalité augmentée, réalité virtuelle, explication, étude de cas, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, qu’est-ce que la réalité virtuelle, qu’est-ce que la réalité augmentée
ms.localizationpriority: high
ms.openlocfilehash: 088bc9a978bd236069ddc1beab40387c607b906e
ms.sourcegitcommit: b0b49ad27a0d09eb0a3d5df0c766bb4b7bbd8208
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2021
ms.locfileid: "113634320"
---
# <a name="what-is-mixed-reality"></a>Qu’est-ce que la réalité mixte ?

La réalité mixte est la prochaine vague informatique suivie par les mainframes, les PC et les smartphones. La réalité mixte est de plus en plus répandue chez les consommateurs et au sein des entreprises.  Elle nous libère de l’écran, en proposant des interactions instinctives avec les données dans nos espaces de vie, entre nos objets et avec nos amis.  Les explorateurs en ligne, qui sont des centaines de millions dans le monde entier, ont expérimenté la réalité mixte sur leurs appareils portables.  La réalité augmentée sur mobile offre aujourd’hui les solutions de réalité mixte les plus courantes sur les réseaux sociaux. Les utilisateurs ne se rendent peut-être même pas compte que les filtres de réalité augmentée qu’ils utilisent sur Instagram sont des expériences de réalité mixte.  Microsoft Mixte Reality offre un tout autre niveau à toutes ces expériences utilisateur, avec une combinaison de représentations holographiques véritablement étonnantes de personnes, de modèles 3D holographiques haute fidélité et du monde concret qui les entoure.

![Pointer et valider avec les mains sur HoloLens 2](images/02_MixedRealitySlashMixedReality.png)

Fusion des mondes physiques et numériques, la réalité mixte rend possible les interactions 3D intuitives et naturelles entre l’humain, l’ordinateur et l’environnement. Cette nouvelle réalité est basée sur les progrès réalisés dans les domaines de la vision par ordinateur, du traitement graphique, des technologies d’affichage, des systèmes de saisie et du cloud computing. Le terme Réalité mixte a été introduit en 1994 par Paul Milgram et Fumio Kishino dans un document intitulé « [A Taxonomy of Mixed Reality Visual Displays](https://search.ieice.org/bin/summary.php?id=e77-d_12_1321) ». Leur document explore le concept d’un *continuum de virtualité* et la taxonomie des affichages visuels. Depuis, l’application de la réalité mixte s’étend bien au-delà des écrans pour inclure les domaines suivants :

* Compréhension de l’environnement : mappage et ancrages spatiaux.
* Compréhension de l’humain : suivi manuel, suivi oculaire et saisie vocale.
* Son spatial.
* Localisations et positionnement dans les espaces physiques et virtuels.
* Collaboration sur des ressources 3D dans les espaces de réalité mixte.

![Image du spectre de la réalité mixte](images/mixedrealityspectrum-worlds.png)<br>
*Image : La réalité mixte est le résultat de la fusion du monde physique et du monde numérique.*

<br>

---

## <a name="environmental-input-and-perception"></a>Interactions avec l’environnement et perception de l’environnement

Au cours des dernières décennies, la relation entre les êtres humains et les ordinateurs a continué à évoluer par le biais des méthodes d’entrée.  Une nouvelle discipline est apparue, appelée interaction humain-machine, ou IHM. L’entrée humaine peut à présent inclure les claviers, les souris, le tactile, l’entrée manuscrite, la voix et le suivi du squelette Kinect.

Les avancées dans les capteurs et la puissance de traitement créent de nouvelles perceptions informatiques des environnements en fonction de méthodes d’entrée avancées. C’est pourquoi les noms d’API dans Windows qui révèlent des informations environnementales sont appelées « [API de perception](/uwp/api/Windows.Perception) ». Les entrées environnementales peuvent capturer : 

* Position du corps d’une personne dans le monde physique ([suivi du visage ou du crâne](../design/coordinate-systems.md)) 
* Objets, surfaces et limites ([mappage spatial](../design/spatial-mapping.md) et [compréhension des scènes](../design/scene-understanding.md)) 
* Éclairage ambiant et son
* Reconnaissance d’objets
* Emplacements physiques

<br>

![Diagramme de Venn montrant les interactions entre les ordinateurs, les humains et les environnements](images/mixed-reality-venn-diagram-300px.png)<br> 
*Image : Interactions entre les ordinateurs, les humains et les environnements.*

<br>

Une combinaison des trois éléments essentiels prépare le terrain pour la création de véritables expériences de réalité mixte :

* Traitement informatique alimenté par le cloud
* Méthodes d’entrée avancées
* Perceptions de l’environnement

Lorsque nous bougeons dans le monde physique, nos mouvements sont mappés dans une réalité numérique. Les limites physiques influencent les expériences de réalité mixte dans le monde numérique, telles que les jeux ou les instructions basées sur les tâches dans une usine de fabrication. Avec les entrées environnementales et les perceptions, les expériences commencent à se mélanger entre les réalités physiques et numériques.

<br>

---

## <a name="the-mixed-reality-spectrum"></a>Spectre de réalité mixte

La réalité mixte fusionne les mondes physiques et numériques.  Ces deux réalités marquent les extrémités polaires d’un spectre appelé *continuum de la virtualité*. Pour désigner ce spectre de réalités, nous parlons de *spectre de réalité mixte*.  À une extrémité du spectre se trouve la réalité physique dans laquelle nous, humains, existons. À l’autre extrémité du spectre se trouve la réalité numérique correspondante.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a>Réalité augmentée et réalité virtuelle

Aujourd’hui, la plupart des téléphones portables du marché sont dotés de fonctionnalités de perception environnementale limitées voire inexistantes. Ils ne proposent pas d’expériences combinant réalité physique et réalité numérique. 

Les expériences qui superposent des graphiques, des flux vidéo ou des hologrammes du monde physique sont du domaine de la réalité augmentée. Les expériences qui obstruent votre vue pour présenter une expérience numérique totalement immersive sont du domaine de la réalité virtuelle. Les expériences qui peuvent passer entre des réalités virtuelles et enrichies forment une réalité mixte, où vous pouvez :

* Placer un objet numérique, tel qu’un hologramme, dans le monde physique, comme s’il était physiquement présent.
* Être personnellement et numériquement présent dans le monde physique, sous la forme d’un avatar, pour collaborer de façon asynchrone avec d’autres personnes à des moments différents dans le temps.
* En réalité virtuelle, les limites physiques, telles que les murs et les meubles, s’affichent numériquement au sein de l’expérience pour que les utilisateurs soient en mesure d’éviter les obstacles physiques.

<br>

![Spectre de la réalité mixte](images/mixedrealityspectrum.png)<br>
*Image : Spectre de la réalité mixte*

<br>

La plupart des expériences de réalité augmentée et de réalité virtuelle disponibles aujourd’hui représentent un petit sous-ensemble du plus vaste spectre de la réalité mixte. Windows 10 est conçu pour prendre en compte l’ensemble du spectre et fusionner les représentations numériques de personnes, de lieux et d’objets avec le monde réel.

## <a name="devices-and-experiences"></a>Appareils et expériences

Deux principaux types d’appareils proposent des expériences Windows Mixed Reality :
1. Les **appareils holographiques** se caractérisent par leur capacité à placer du contenu numérique dans le monde réel comme s’il existait.
2. Les **appareils de réalité virtuelle immersifs** se caractérisent par leur capacité à créer un sens de présence en cachant le monde physique et en le remplaçant par une expérience numérique totalement immersive.

<table>
<tr>
<th width="30%"> Caractéristique</th><th width="35%"> Appareils holographiques</th><th width="35%"> Appareils immersifs</th>
</tr><tr>
<td><strong>Exemple d’appareil</strong></td><td> Microsoft HoloLens<br><br> <img alt="Microsoft HoloLens 2 image" width="300" height="169" src="images/HoloLens2.jpg" /></td><td> Samsung HMD Odyssey+<br><br> <img alt="Samsung HMD Odyssey+ image" width="300" height="169" src="images/Samsung-HMD-Odyssey.jpg" /></td>
</tr><tr>
<td><strong>Affichage</strong></td><td> Écran transparent. Permet à l’utilisateur de voir l’environnement physique tout en portant le casque.</td><td> Écran opaque. Bloque l’environnement physique de l’utilisateur portant le casque.</td>
</tr><tr>
<td><strong>Movement</strong></td><td> Mouvement complet avec six degrés de liberté (6DoF), en rotation et translation.</td><td> Mouvement complet avec six degrés de liberté (6DoF), en rotation et translation.</td>
</tr>
</table> 

> [!NOTE]
> Le fait qu’un appareil soit connecté à un PC distinct (via un câble USB ou le Wi-Fi) ou non attaché n’indique pas s’il est holographique ou immersif. Les fonctionnalités qui améliorent la mobilité offrent souvent de meilleures expériences. Les appareils holographiques et immersifs peuvent être attachés ou non attachés.

Les expériences de réalité mixte sont le résultat des avancées technologiques. Aucun appareil n’est actuellement capable d’exécuter des expériences sur l’ensemble du spectre. Windows 10 offre une plateforme de réalité mixte commune pour les fabricants d’appareils et les développeurs. Aujourd’hui, un appareil donné peut prendre en charge une plage spécifique du spectre de réalité mixte. À l’avenir, de nouveaux appareils avec une plus grande étendue sont attendus : les appareils holographiques seront plus immersifs et les appareils immersifs seront plus holographiques.

<br>

![Types d’appareils dans le spectre de réalité mixte](images/Final_WhatIsMixedReality07.png)<br>
*Image : Positionnement des appareils dans le spectre de réalité mixte*

En tant que développeur d’applications ou de jeux, quel type d’expérience voulez-vous créer ? Les expériences ciblent généralement un point ou une partie spécifique du spectre. Vous devez prendre en compte les fonctionnalités des appareils à cibler. HoloLens est mieux adapté aux expériences qui s’appuient sur le monde physique.

* **Vers la gauche (près de la réalité physique).** Les utilisateurs restent présents dans leur réalité physique et ne sont jamais amenés à croire qu’ils ont quitté cette réalité.
* **Au milieu (réalité entièrement mixte).** Ces expériences fusionnent le monde réel et le monde numérique. Par exemple, dans le film [Jumanji](https://en.wikipedia.org/wiki/Jumanji), la jungle fait son apparition dans la structure physique de la maison où se déroule l’histoire.
* **Vers la droite (près de la réalité numérique).** Les utilisateurs font l’expérience d’une réalité numérique et ne sont pas conscients de la réalité physique qui les entoure.

## <a name="next-discovery-checkpoint"></a>Point de contrôle de découverte suivant

Vous êtes au début du [parcours de découverte](get-started-with-mr.md) que nous avons disposé pour vous et de l’exploration des principes de base de la réalité mixte. À partir de là, vous pouvez passer au sujet suivant : 

> [!div class="nextstepaction"]
> [Qu’est-ce qu’un hologramme ?](hologram.md)
