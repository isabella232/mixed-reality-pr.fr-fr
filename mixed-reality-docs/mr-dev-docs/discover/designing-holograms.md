---
title: Conception d’hologrammes
description: En savoir plus sur la réalité mixte grâce à la nouvelle application de conception d’hologrammes de Microsoft.
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: MRTK, boîte à outils de réalité mixte, hologrammes, conception d’hologrammes, apprentissage, exemple d’application, casque de réalité mixte, casque de réalité virtuelle, présentation de la réalité virtuelle
ms.openlocfilehash: bf904b319ed5b452f254b659315d9b531832a4d5
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002584"
---
# <a name="the-making-of-designing-holograms"></a>Création d’hologrammes

> [!NOTE]
> Veuillez tenir compte d’une petite fenêtre de chargement pour tenir compte de tous les gif et vidéos incorporées dans cette page.

L’apprentissage de la conception pour la réalité mixte peut être difficile, en particulier avec la manière dont le support est visuel, ce qui ne traduit pas toujours bien les processus de conception 2D. Chez Microsoft, nous avons créé une application gratuite que vous pouvez télécharger pour HoloLens 2, qui vous aide à apprendre les principes fondamentaux de la conception de l’expérience utilisateur de la réalité mixte en la faisant personnellement. L’approche unique de la conception d’une application d’hologrammes s’approche des comportements de réalité mixte, des conseils et des recommandations pour vous aider à créer vos propres applications HoloLens attrayantes et étonnantes. Téléchargez gratuitement l’application à partir de la Microsoft Store et apprenez de l’équipe de conception de la réalité mixte de Microsoft !

> [!div class="nextstepaction"]
> [Télécharger l’application conception d’hologrammes](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

<br>

![GIF animé de la scène de suivi des têtes dans le design de la salle de démonstration de l’hologramme](images/designing-holograms/demo-room.gif)

*Conception de la salle de démonstration de l’hologramme (également appelée maison de poupée)*

## <a name="designing-for-mixed-reality"></a>Conception pour la réalité mixte

Comme beaucoup d’entre vous, j’ai utilisé pour concevoir des applications mobiles. En provenance d’un monde de conception 2D, le saut dans le monde de l’informatique spatiale, où tout est présent dans le monde, était un changement significatif. En réalité mixte, les applications ne sont plus limitées à un écran 2D ; en fait, ils sont presque gratuits, placés dans le monde réel et interagissent avec les objets réels.

Pour moi, la connexion des expériences 3D aux processus de conception 2D conventionnels est l’aspect le plus difficile du développement de la réalité mixte. Dans les conversations avec les clients, j’entends des choses telles que «je sais quelles sont les fonctionnalités à inclure et comment les mettre en service. C’est le code, je peux suivre les documents et les didacticiels, mais l’expérience de l’utilisateur ? De nombreuses fonctionnalités, différentes options d’entrée, différents scénarios et environnements physiques, sont insurmontables.

![Image de l’atelier de conception HoloLens 2 de l’image San Francisco ](images/designing-holograms/workshop.jpeg)
 *de l’atelier de conception hololens 2 de San Francisco*

## <a name="an-opportunity-to-teach"></a>Une opportunité d’enseigner

Ce n’était pas évident dans un premier temps, mais une excellente opportunité était présentée pour utiliser la réalité mixte comme un support pour l’enseigner.

La conception d’hologrammes est une expérience visuelle qui explique les concepts et les recommandations en matière de conception de la réalité mixte. C’est juste vous et un enseignant qui démontre les concepts de conception de la réalité mixte. Tout est un point de vue de la troisième personne avec l’expérience dans votre propre espace.

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Designing-Holograms-app-trailer/player]

*Vidéo sur la conception d’hologrammes*

## <a name="exploring-the-doll-house"></a>Exploration de la maison de poupée

La maison de poupée est l’environnement virtuel que nous utilisons dans toute l’application, une salle miniature 80 x 60 x 40 cm contenant les éléments de base que la plupart des chambres ont en commun, comme les murs, les lampes, le mobilier, une table et un téléviseur. La maison de poupée est le Protagonist principal de l’expérience de l’application. nous avons donc dû nous assurer qu’elle fonctionne bien dans n’importe quel environnement. Considérez-le comme une petite salle de démonstration pour visualiser toutes sortes de concepts de réalité mixte.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Dollhouse-adjustment-behavior-in-the-Designing-Holograms-app/player]
*Vidéo du comportement de réglage Dollhouse*

### <a name="11-vs-110-prototypes"></a>1:1 et prototypes 1:10

Notre hypothèse initiale était que les démonstrations 1:1 seraient étonnantes, presque comme en regardant un professeur réel. L’utilisateur verra tout ce que voit l’enseignant à une échelle réelle. Toutefois, nous avons immédiatement réalisé que quelques problèmes se produisaient :

- La plupart des développeurs exécutent leurs applications dans des bureaux ou des salles plus petites que la salle de démonstration, ce qui ne peut pas être le cas.
- Les affichages sont additifs, ce qui signifie que l’ensemble de l’environnement virtuel sera reporté sur la salle d’un utilisateur. Cela peut être confus avec deux tables, peut-être deux canapés et murs qui ne s’alignent pas.
- Et pire de tous les environnements virtuels sont fortement limités par un champ de vue.

Lors d’une tentative de mise à l’échelle de la mini-1:10, le résultat était une vue d’ensemble des oiseaux fantastique dans une salle réaliste dans laquelle vous pouviez voir tout ce qui se passait à partir de n’importe quel angle et en même temps. Ce qui était le plus surprenant, c’est que la plupart des testeurs ont trouvé qu’il s’agissait d’une plus grande immersion pour voir une petite version, alors ils n’ont jamais rétabli l’échelle 1:1. Nous avons donc décidé de mettre en fait la version 1:1 et d’éviter le travail supplémentaire requis pour adapter l’interface utilisateur et d’autres aspects de l’application.

![Champ de vue avec un champ d’affichage à l’échelle 1:1 ](images/designing-holograms/1-1-scale.png)
 *avec une échelle de 1:1*

![Champ de vue avec un champ d’affichage à l’échelle 1:10 ](images/designing-holograms/1-10-scale.png)
 *avec une échelle de 1:10*

## <a name="using-mixed-reality-capture"></a>Utilisation de la capture de réalité mixte

L’une des fonctionnalités les plus caractéristiques de cette application est l’utilisation de la capture de réalité mixte pour enseigner et démontrer les concepts de conception de la réalité mixte.

Microsoft dispose d’une réalité mixte de capture Studio à San Francisco. Microsoft concède également cette technologie à d’autres Studios, y compris la dimension d’avatar à Washington D.C., la réétape à Los Angeles, les Studios de dimension à Londres, SK Telecom à Séoul et Volucap à Berlin. Vous trouverez des informations supplémentaires sur nos [Studios de capture de réalité mixte ici](https://www.microsoft.com/mixed-reality/capture-studios).

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Raw-capture-footage-for-the-Designing-Holograms-app/player]
*Métrage brut de Daniel Escudero à partir de l’une des caméras 106 dans la réalité mixte capture Studio à San Francisco.*

Le processus de capture génère un maillage, des normales et une texture KeyFrame, qui peuvent être fournis sous la forme de fichiers OBJ/PNG pour une nouvelle publication, ou prêts pour la lecture en tant que fichier MP4 compressé H. 264. Ces fichiers peuvent être importés dans Unity, Unreal, native et WebXR et s’exécutent sur Windows, iOS, Mac, Android, Magic LEAP et PlayStation VR.

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Mixed-Reality-Capture-footage-for-the-Designing-Holograms-app/player]
*Lecteur de capture fourni pour analyser les fichiers MP4 à qui contiennent des vidéos avec des panneaux audio et incorporés.*

## <a name="manipulating-captures-and-virtual-objects"></a>Manipulation des captures et des objets virtuels

Les captures de réalité mixte produisent des représentations virtuelles de personnes ou d’animaux, mais il peut arriver que vous ayez besoin de ces caractères pour interagir avec d’autres objets virtuels. Les deux exemples suivants illustrent les différentes façons dont nous avons manipulé les scènes pour atteindre cet effet.

### <a name="head-gaze-adjustment"></a>Réglage du pointage de la tête

L’ajustement de Headgaze vous permet de déplacer la tête d’une personne capturée au moment de l’exécution, ce qui signifie que vous pouvez avoir un visage de capture pour un utilisateur. Dans notre cas, nous l’avons utilisé pour afficher le champ de vue et le champ d’intérêt. Ce que vous voyez ci-dessous est un gameobject de déplacement qui joue le rôle de cible pour le regard de la tête. À mesure que nous déplaçons la cible d’un côté à l’autre, l’en-tête de la capture suit.

Nous avons utilisé cette astuce pour s’assurer que la capture inactive serait toujours dirigée vers des hologrammes placés dans des parties différentes de la maison de poupée. 

![La tête de capture qui est déplacée au moment de l’exécution après un gameobject cible dans Unity](images/designing-holograms/head-adjustment.gif)

*La tête de capture qui est déplacée au moment de l’exécution après un gameobject cible dans Unity.*

### <a name="syncing-animated-objects"></a>Synchronisation d’objets animés

Le deuxième, qui consistait à animer des objets à synchroniser avec le mouvement d’une capture. Dans les différentes parties de l’application, nous avons importé des ne comportaient séquentielles d’une capture spécifique toutes les cinq frames. Les ne comportaient ont ensuite été animés dans la scène pour s’assurer qu’ils correspondent au frame correspondant de la capture. Il s’agit d’un processus fastidieux d’animation et de keyencadrement, mais le résultat est parfait. vous pouvez maintenant voir une capture de réalité mixte qui interagit avec des objets non capturés.

![Animation synchronisée entre une capture de réalité mixte et un panneau d’interface utilisateur](images/designing-holograms/synced-objects.gif)

*Animation synchronisée entre une capture de réalité mixte et un panneau d’interface utilisateur*

### <a name="ui-creative-process"></a>Processus créatif de l’interface utilisateur

Lorsque nous avons commencé à ideating la conception de l’interface utilisateur, outre le transport des informations, nous souhaitons également montrer une partie de la magie et les possibilités offertes par les hologrammes. Le simple fait d’afficher des fenêtres 2D statiques et des zones de texte n’a pas de sens dans le monde 3D et n’affiche pas la plupart des possibilités en main. donc, dès le début, nous avons décidé de ne plus en sortir et d’utiliser pleinement l’espace 3D holographique.

Dans un premier temps, nous avons commencé à ajouter de l’épaisseur aux panneaux et aux icônes en plus des informations de texte. Toutefois, en tant qu’utilisateur, ce que je vois est une zone de texte. Les zones de texte avec des images, mais ce n’est pas le cas. Nous sommes allés plus loin en utilisant les nuanceurs MRTK (Mixed Reality Toolkit). Les nuanceurs MRTK sont devenus un outil puissant et nous avons utilisé les fonctionnalités de leurs stencils, certaines peuvent le savoir comme l’effet du portail, afin d’ajouter une profondeur négative aux panneaux. Cela signifie qu’au lieu d’ajouter des éléments devant une zone de texte, les icônes s’affichent désormais derrière un panneau transparent. Ce que je vois maintenant en tant qu’utilisateur, c’est qu’il n’est plus possible de répliquer plus dans le monde réel, et c’est là où holographique magique a commencé à se produire. En outre, comme un utilisateur que je n’aime pas lire, je fais beaucoup de choses dans le monde physique.

Évidemment, les icônes fonctionnent beaucoup mieux que le simple texte. par conséquent, afin de fournir une aide encore plus puissante, j’ai commencé à créer un ensemble d’objets animés et d’avatars, chacun d’entre eux indiquant un petit récit sur ce qui est fait dans le scénario respectif et sur la manière dont il est utilisé.

![GIF animé d’un système de menu holographique interactif](images/designing-holograms/creative-process.gif)

## <a name="core-concepts"></a>Principaux concepts

**Image holographique**

![GIF animé d’un utilisateur qui regarde le Dollhouse avec le cadre holographique mis en surbrillance](images/designing-holograms/FOVandFOI.gif)

**Systèmes de coordonnées**

![GIF animé d’un utilisateur qui regarde le Dollhouse avec les systèmes de coordonnées mis en surbrillance](images/designing-holograms/CoordinateSystems.gif)

**Eye-tracking**

![GIF animé d’un utilisateur cherchant des hologrammes stationnaires avec le point de regard de l’oeil en surbrillance](images/designing-holograms/EyeTracking.gif)

**Visualisation de l’analyse de la salle et mappage spatial**

![GIF animé de toutes les surfaces à l’intérieur du Dollhouse mappé](images/designing-holograms/SpatialMapping.gif)

**Compréhension des scènes**

![GIF animé d’objets dans le Dollhouse qui est reconnu](images/designing-holograms/SceneUnderstanding.gif)

**Pointer et valider avec des rayons de main**

![GIF animé d’un utilisateur qui soulève sa main avec un rayon de la main mis en surbrillance](images/designing-holograms/HandRays.gif)

## <a name="try-it-out-moments"></a>« Essayer » les moments

La conception d’hologrammes enseigne les concepts de réalité mixte, mais vous permet également de les essayer dans votre salle. Après quelques-unes de ces explications, nous suspendons et vous revenons à la maison de poupée et à un moment interactif. Voici quelques exemples de ces moments interactifs :

![GIF animé du frame de suivi de la main montrant quand les mains sont détectées et quand elles entrent dans le champ de la vue](images/designing-holograms/try-out-1.gif)

*Frame de suivi de la main qui indique quand les mains sont détectées et quand elles entrent dans le champ de la vue.*

![GIF animé de l’interaction avec les cristaux en collision via une interaction lointaine](images/designing-holograms/try-out-2.gif)

*Interaction avec les cristaux en collision via une interaction lointaine*

![GIF animé de l’exploration des intuitivité near interaction](images/designing-holograms/try-out-3.gif)

*Exploration des intuitivité near interaction*

## <a name="about-the-team"></a>À propos de l’équipe

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Daniel Escudero" width="60" height="60" src="images/designing-holograms/daniel-escudero.jpeg"></td>
<td style="border-style: none"><b>Daniel Escudero</b><br><i>Concepteur technique du prospect</i><br>Dan est le directeur créatif de la conception d’hologrammes et travaille actuellement en tant que responsable de la conception de l’Académie de la réalité mixte de Microsoft à San Francisco, et était auparavant un concepteur dans l’un des Studios de réalité mixte de Microsoft à Londres.</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Martin Wettig" width="60" height="60" src="images/designing-holograms/martin-wettig.jpeg"></td>
<td style="border-style: none"><b>Martin Wettig</b><br><i>Artiste 3D Senior</i><br>Martin domine la conception de l’interface utilisateur et de l’art 3D sur la conception d’hologrammes et était auparavant un artiste en 3D senior dans l’un des Studios de réalité mixte de Microsoft à Berlin.</td>
</tr>
</table>

Nous vous remercions de l’équipe de conception de la réalité mixte à partager de nombreuses connaissances et, bien sûr, aux gens étonnants de la [théorie des objets](https://objecttheory.com/) qui sont devenus des coéquipiers essentiels à chaque étape de ce projet. Nous vous remercions tout pour vos talents exceptionnels, pour votre passion et vos yeux de la conception.

> [!div class="nextstepaction"]
> [Télécharger l’application conception d’hologrammes](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)