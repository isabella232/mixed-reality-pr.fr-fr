---
title: À propos de ce guide de conception
description: Cette aide a été écrite par des concepteurs, des développeurs, des responsables de programme et les chercheurs de Microsoft, dont les travaux couvrent les appareils holographiques (par exemple HoloLens) et les appareils immersifs (par exemple les casques Windows Mixed Reality Acer et HP).
author: mrwied
ms.author: jonwie
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, conception, introduction, conseils, casque de réalité mixte, casque Windows Mixed reality, casque de réalité virtuelle, expérience utilisateur, ressources
ms.openlocfilehash: 0bd70e08d55f8d556ff3a612dbbc979dc895cebbfc9950f18d8d474ff347407b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198642"
---
# <a name="about-this-design-guidance"></a>À propos de ce guide de conception

## <a name="introduction"></a>Introduction

**Bonjour et Bienvenue dans vos conseils de conception pour la réalité mixte.**

Ce guide est rédigé par les concepteurs, les développeurs, les responsables de programme et les chercheurs de Microsoft. les travaux de nos rédacteurs s’étendent sur des appareils holographiques, notamment des HoloLens, des appareils immersifs, des andAcer et des casques HP Windows Mixed Reality. nous vous recommandons de considérer cet article comme un ensemble de rubriques relatives à la conception de Windows.

Nous avons introduit une nouvelle ère incroyablement passionnante de l’informatique avec vous. Des innovations dans les affichages montés en tête, les sons spatiaux, les capteurs, la sensibilisation de l’environnement, les entrées et les graphiques 3D, et nous permettent de définir de nouveaux types d’expériences. La nouvelle frontière est considérablement plus personnelle, intuitive, immersive et contextuelle.

Dans la mesure du possible, nous proposerons des conseils de conception actionnables avec le code associé sur GitHub. Cela dit, étant donné que nous nous familiarisons avec vous, nous ne pouvons pas toujours proposer des conseils pratiques spécifiques. Une partie de ce que nous partagerons sera à l’esprit des « leçons que nous avons apprises » et « évitez de faire tourner ce chemin d’accès ».

Et nous savons que de nombreuses innovations seront générées par la communauté de conception plus grande. Nous sommes donc impatients de vous faire part de vos commentaires, de vous apprendre et de travailler en étroite collaboration avec vous. Nous allons faire de notre mieux pour partager nos Insights, même s’ils sont exploratoires et précoces. Notre objectif est d’aider les développeurs et les concepteurs à réfléchir à la conception, les meilleures pratiques et les contrôles, modèles et exemples d’applications open source associés que vous pouvez utiliser directement dans votre propre travail.

## <a name="overview"></a>Vue d’ensemble

Voici une vue d’ensemble rapide de l’organisation de ce guide de conception :

* **[Vue d’ensemble](design.md)** : en savoir plus sur le processus de conception, les concepts de base et les facteurs d’interaction à prendre en compte.
* **[Concepts de base](core-concepts-landingpage.md)** : en savoir plus sur le confort, le cadre holographique, le mappage spatial et d’autres concepts de base à prendre en compte.
* **[Modèles d’interaction](interaction-fundamentals.md)** : ce guide est structuré autour de trois modèles d’interaction principaux.
* **[Éléments UX](app-patterns-landingpage.md)** : utilisez les contrôles et les comportements comme des blocs de construction pour créer votre propre expérience d’application.
* **[Ressources](design.md#choose-a-prototyping-option)** -démarrez votre projet avec des outils de conception et des options de création de prototypes.

Pour tous les éléments ci-dessus, nous avons l’intention de fournir la combinaison de texte, d’illustrations et de vidéos. Nous verrons que nous expérimentons avec différents formats et techniques, le tout avec l’intention de vous communiquer ce dont vous avez besoin. Et dans les mois à venir, nous développerons cette taxonomie pour inclure un ensemble plus large de rubriques de conception. Dans la mesure du possible, nous vous ferons découvrir ce qui se passe à l’étape suivante. par conséquent, continuez à vérifier.

## <a name="objectives"></a>Objectifs

Voici un aperçu rapide de certains objectifs de haut niveau qui guident ce travail pour vous permettre de comprendre où nous sommes issus

### <a name="help-solve-customer-challenges"></a>Aider à résoudre les problèmes des clients

![Aider à résoudre les problèmes des clients](images/500px-fix-a-broken-switch-with-hololens.jpg) <br>

Nous prenons en charge un grand nombre des problèmes que vous rencontrez et nous comprenons la difficulté de votre travail. Il est intéressant d’explorer et de définir une nouvelle frontière... et il peut également s’avérer décourageant. Les anciens paradigmes et pratiques sont en cours de réactivité, les clients ont besoin de nouvelles expériences et le potentiel d’innovation est tellement grand. Étant donné que nous souhaitons que ce travail soit aussi complet que possible, en passant au-delà d’un guide de style. Nous avons l’intention de fournir un ensemble complet de conseils de conception qui traitent de l’interaction de la réalité mixte, de l’action, de la navigation, de l’entrée et du style, tout cela dans le comportement humain et les scénarios. 

### <a name="point-the-way-towards-a-new-more-human-way-of-computing"></a>Pointez vers un nouveau moyen de calcul plus humain

![Pointez vers un nouveau moyen de calcul plus humain](images/500px-man-and-women-with-holograph-on-table.png)<br>

Bien qu’il soit important de se concentrer sur des problèmes spécifiques aux clients, nous souhaitons également nous envoyer des informations supplémentaires. Nous pensons que la conception n’est pas « juste », mais également un moyen d’activer l’évolution humaine de manière significative. Les nouvelles méthodes de comportement humain, les relations interpersonnes, les activités et les environnements alimentent notre innovation. Nous souhaitons que nos conseils reflètent l’ensemble de ces méthodes de réflexion. 

### <a name="meet-creators-where-they-are"></a>Rencontrez les créateurs où ils sont

![Rencontrez les créateurs où ils sont](images/500px-creators.jpg) <br>

Nous espérons que de nombreux publics trouvent ces conseils pour être utiles. vous avez différents compétences (début, intermédiaire, avancé), utilisez différents outils (unity, DirectX, C++, C#, etc.), vous connaissez les différentes plateformes (Windows, iOS, Android), qui proviennent de différents arrière-plans (mobile, entreprise, jeux) et qui travaillent sur différentes équipes de taille (solo, petite, moyenne, grande). Ce guide peut donc être consulté avec différentes perspectives et besoins. Dans la mesure du possible, nous essaierons de garder cette diversité à l’esprit et de faire en sorte que nos conseils soient les plus pertinents possible pour autant de personnes que possible. Nous savons que beaucoup d’entre vous sont déjà sur GitHub. nous allons donc vous connecter directement à GitHub les et aux forums pour vous répondre là où vous êtes déjà. 

### <a name="share-as-much-as-possible-from-experimental-to-explicit"></a>Partager le plus possible, de l’expérimentation à la valeur explicite

![Partager le plus possible, de l’expérimentation à la valeur explicite](images/500px-man-playinggame.jpg) <br>

L’un des défis liés à l’offre de conseils en matière de conception dans ce nouveau support 3D est que nous n’avons pas toujours de conseils définitifs à proposer. Comme vous le feriez, nous vous envoyons, expérimentons, prototypages, résolution des problèmes et nous réglons à mesure que nous rencontrons des obstacles. Au lieu d’attendre un futur moment où nous l’avons fait, nous souhaitons partager notre pensée avec vous en temps réel, même s’il n’est pas concluant. Notre objectif final est de clarifier partout où nous pouvons, en fournissant des conseils de conception clairs et flexibles, liés au code open source et actionnables dans les outils de développement et de conception Microsoft. Toutefois, l’accès à ce point prend de nombreuses séries d’itérations et d’apprentissage. Nous souhaitons vous contacter et vous apprendre avec vous, en cours de route. Nous faisons de notre mieux pour nous partager au fur et à mesure, même avec nos produits expérimentaux. 

### <a name="the-right-balance-of-global-and-local-design"></a>Le juste équilibre entre la conception globale et la conception locale

![Le juste équilibre entre la conception globale et la conception locale](images/500px-fluentdesign.jpg) <br>

Nous proposons deux niveaux de conseils de conception : global et local. notre guide de conception « global » est inclus dans le [Système Fluent Design](https://fluent.microsoft.com). Fluent explique en détail comment nous pensons aux notions de base, telles que la lumière, la profondeur, le mouvement, le matériau et la mise à l’échelle dans l’ensemble de la conception Microsoft, nos appareils, produits, outils et services. Cela dit, des différences significatives spécifiques aux appareils existent sur ce système plus volumineux. Ainsi, notre guide de conception « local » pour les affichages montés en tête décrit la conception d’appareils holographiques et immersifs qui ont souvent des méthodes d’entrée et de sortie différentes, ainsi que des besoins et des scénarios d’utilisateur différents. Le Guide de conception local couvre les rubriques propres à HMDs. Par exemple : environnements 3D et objets ; environnements partagés ; l’utilisation de capteurs, le suivi des yeux et le mappage spatial ; et les opportunités de l’audio spatial. Dans le cadre de nos recommandations, vous verrez probablement que ces deux aspects sont des aspects globaux et locaux. Nous espérons que cela vous aidera à mettre votre travail en œuvre dans un grand nombre de conceptions tout en tirant parti des différences de conception entre les appareils spécifiques.

### <a name="have-a-discussion"></a>Avoir une discussion

![Avoir une discussion](images/500px-share.jpg) <br>

Plus important encore, nous souhaitons faire appel à vous, à la communauté de concepteurs et de développeurs de systèmes holographiques et immersifs, afin de définir cette nouvelle ère passionnante de conception. Comme indiqué ci-dessus, nous savons que nous n’avons pas toutes les réponses. C’est la raison pour laquelle nous pensons que de nombreuses solutions et innovations passionnantes vous seront fournies. Nous souhaitons être ouverts et disponibles pour en savoir plus à leur sujet, et discuter avec vous en ligne et aux événements, et ajouter de la valeur partout où nous le pouvons. Nous sommes ravis de faire partie de cette communauté de conception incroyable, en vous regroupant sur une aventure. 

## <a name="dive-in"></a>Plongez dans

Nous espérons que cet article de présentation fournit un contexte explicite lorsque vous explorez nos conseils de conception. plongez-vous et faites-nous part de vos commentaires sur les forums de GitHub que vous trouverez liés dans nos articles ou sur la conception Microsoft sur [Twitter](https://twitter.com/MicrosoftDesign) et [Facebook](https://www.facebook.com/microsoftdesign/). Nous allons concevoir l’avenir en collaboration.
