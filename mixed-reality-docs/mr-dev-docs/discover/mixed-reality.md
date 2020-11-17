---
title: Qu’est-ce que la réalité mixte ?
description: Cet article définit ce qu’est la réalité mixte et montre où se situent les appareils AR et VR dans le spectre de la réalité mixte.
author: brandonbray
ms.author: branbray
ms.date: 08/26/2020
ms.topic: article
keywords: réalité mixte, holographique, AR, VR, MR, XR, réalité augmentée, réalité virtuelle, explication
ms.localizationpriority: high
ms.openlocfilehash: 44914decd9530a11d11127b43af527d995f6c252
ms.sourcegitcommit: cc27d31f0cebaf9fc4221a3300a9e3d73230b367
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2020
ms.locfileid: "94631487"
---
# <a name="what-is-mixed-reality"></a>Qu’est-ce que la réalité mixte ?

![Pointer et valider avec les mains sur HoloLens 2](images/02_MixedRealitySlashMixedReality.png)

Fusion des mondes physiques et numériques, la réalité mixte rend possible l’interaction entre l’homme, l’ordinateur et l’environnement. Cette nouvelle réalité est basée sur les progrès réalisés dans les domaines de la vision par ordinateur, du traitement graphique, de la technologie d’affichage et des systèmes d’entrée. Toutefois, le terme *réalité mixte* a été introduit en 1994 par Paul Milgram et Fumio Kishino dans un document intitulé « [A Taxonomy of Mixed Reality Visual Displays](https://search.ieice.org/bin/summary.php?id=e77-d_12_1321) ». Ce document explorait le concept de « *continuum de virtualité* » et l’application de la catégorisation taxonomique aux écrans. Depuis, l’application de la réalité mixte s’étend bien au-delà des écrans pour inclure les domaines suivants :
* Entrée environnementale
* Son spatial
* Localisations et positionnement dans les espaces réels et virtuels

![Image du spectre de la réalité mixte](images/mixedrealityspectrum-worlds.png)<br>
*Image : La réalité mixte est le résultat de la fusion du monde physique et du monde numérique.*

<br>

---

## <a name="environmental-input-and-perception"></a>Interactions avec l’environnement et perception de l’environnement

Au cours des dernières décennies, la relation entre les entrées humaines et celles des ordinateurs a continué, donnant lieu à une discipline appelée *interaction homme-machine* ou IHM. Les entrées humaines se font par divers moyens : clavier, souris, toucher, écriture manuscrite, voix et même suivi du squelette avec Kinect.

Les avancées dans les capteurs et le traitement ont donné naissance à un nouveau type d’entrée d’ordinateur qui vient de l’environnement. L’interaction entre un ordinateur et un environnement réside en fait dans la compréhension ou la *perception* de cet environnement. C’est pourquoi les API dans Windows qui révèlent des informations environnementales sont appelées [API de perception](https://docs.microsoft.com/uwp/api/Windows.Perception). Les entrées environnementales capturent des éléments tels que la position d’une personne dans le monde ([suivi de la tête](../design/coordinate-systems.md)), les surfaces et les limites ([cartographie spatiale](../design/spatial-mapping.md) et [compréhension des scènes](../design/scene-understanding.md)), l’éclairage ambiant, le son environnemental, la reconnaissance des objets et la localisation.

<br>

![Diagramme de Venn montrant les interactions entre les ordinateurs, les humains et les environnements](images/mixed-reality-venn-diagram-300px.png)<br> 
*Image : Interactions entre les ordinateurs, les humains et les environnements.*

<br>

La combinaison de ces trois éléments (**traitement informatique, entrées humaines et entrées environnementales**) permet la création de véritables expériences de réalité mixte. Un mouvement dans le monde physique peut se traduire par un mouvement dans le monde numérique. Les limites présentes dans le monde physique peuvent influencer des expériences applicatives, notamment la jouabilité, dans le monde numérique. Sans entrée environnementale, les expériences ne peuvent pas fusionner les réalités physique et numérique.<br>

<br>

---


## <a name="the-mixed-reality-spectrum"></a>Spectre de réalité mixte

Étant donné que la réalité mixte fusionne les mondes physique et numérique, ces deux réalités définissent les deux extrémités d’un spectre appelé « continuum de virtualité ». Pour désigner cet ensemble de réalités, nous parlons de *spectre de réalité mixte*. À gauche se trouve la réalité physique dans laquelle nous, humains, existons. À droite se trouve la réalité numérique correspondante.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a>Réalité augmentée et réalité virtuelle

Aujourd’hui, la plupart des téléphones portables du marché sont dotés de fonctionnalités de compréhension environnementale limitées voire inexistantes. Ils ne proposent pas d’expériences combinant réalité physique et réalité numérique. Les expériences qui superposent des graphiques sur des flux vidéo du monde physique sont du domaine de la *réalité augmentée*. Les expériences qui obstruent votre vue pour présenter une expérience numérique sont du domaine de la *réalité virtuelle*. Les expériences issues de la combinaisons de la réalité augmentée et de la réalité virtuelle forment la *réalité mixte* :
* À partir du monde physique, placer un objet numérique, comme un hologramme, et le faire apparaître comme s’il existait.
* À partir du monde physique, créer une représentation numérique d’une autre personne (avatar) et montrer son emplacement quand elle laisse des notes. En d’autres termes, des expériences qui représentent une collaboration asynchrone à différents moments.
* À partir d’un monde numérique, faire apparaître numériquement dans l’expérience les limites du monde physique, comme les murs et les meubles, pour aider les utilisateurs à éviter les objets physiques.


<br>

![Spectre de la réalité mixte](images/mixedrealityspectrum.png)<br>
*Image : Spectre de la réalité mixte*

<br>

La plupart des offres de réalité augmentée et de réalité virtuelle disponibles aujourd’hui représentent une petite partie de ce spectre et sont considérées comme des sous-ensembles du plus vaste spectre de réalité mixte. Windows 10 est conçu pour prendre en compte l’ensemble du spectre et fusionner les représentations numériques de personnes, de lieux et d’objets avec le monde réel.


## <a name="devices-and-experiences"></a>Appareils et expériences

Deux principaux types d’appareils proposent des expériences Windows Mixed Reality :
1. Les **appareils holographiques** se caractérisent par leur capacité à placer du contenu numérique dans le monde réel comme s’il existait.
2. Les **appareils immersifs** se caractérisent par leur capacité à créer un sens de « présence » en cachant le monde physique et en le remplaçant par une expérience numérique.

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
> Le fait qu’un appareil soit connecté ou attaché à un PC distinct (via un câble USB ou le Wi-Fi) ou autonome (non attaché) n’indique pas s’il est holographique ou immersif. Les fonctionnalités qui améliorent la mobilité donnent lieu à de meilleures expériences, mais les appareils holographiques et immersifs peuvent être attachés à un PC ou non.

Le progrès technologique est ce qui a permis de créer des expériences de réalité mixte. Aucun appareil n’est actuellement capable d’exécuter des expériences sur l’ensemble du spectre. Windows 10 offre une plateforme de réalité mixte commune pour les fabricants d’appareils et les développeurs. Aujourd’hui, les appareils peuvent prendre en charge une plage spécifique du spectre de réalité mixte. Au fil du temps, de nouveaux appareils prendront en charge une plage plus étendue. À l’avenir, les appareils holographiques deviendront plus immersifs et les appareils immersifs deviendront plus holographiques.

<br>

![Types d’appareils dans le spectre de réalité mixte](images/Final_WhatIsMixedReality07.png)<br>
*Image : Positionnement des appareils dans le spectre de réalité mixte*

Il est recommandé de réfléchir au type d’expérience qu’un développeur d’applications ou de jeux souhaite créer. Les expériences ciblent généralement un point ou une partie spécifique du spectre. Les développeurs doivent prendre en compte les fonctionnalités des appareils qu’ils souhaitent cibler. HoloLens est mieux adapté aux expériences qui s’appuient sur le monde physique.
* **Vers la gauche (près de la réalité physique).** Les utilisateurs restent présents dans leur environnement physique et ne sont jamais amenés à croire qu’ils ont quitté cet environnement.
* **Au milieu (réalité entièrement mixte).** Ces expériences fusionnent le monde réel et le monde numérique. Si vous avez vu le film [Jumanji](https://en.wikipedia.org/wiki/Jumanji), vous vous souvenez sans doute de la jungle qui fait son apparition dans la structure physique de la maison où se déroule l’histoire.
* **Vers la droite (près de la réalité numérique).** Les utilisateurs se retrouvent dans un environnement numérique et ignorent ce qui se passe dans l’environnement physique qui les entoure.

## <a name="next-discovery-checkpoint"></a>Point de contrôle de découverte suivant

Si vous suivez le [parcours de découverte](get-started-with-mr.md) que nous avons établi, vous êtes au cœur de l’exploration des concepts de base de la réalité mixte. À partir de là, vous pouvez passer au sujet suivant : 

> [!div class="nextstepaction"]
> [Qu’est-ce qu’un hologramme ?](hologram.md)


