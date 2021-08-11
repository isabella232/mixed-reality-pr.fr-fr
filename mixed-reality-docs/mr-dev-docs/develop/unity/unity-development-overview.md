---
title: Développement Unity pour HoloLens
description: Commencez à créer des applications de réalité mixte dans Unity et HoloLens avec notre parcours de points de contrôle organisé.
author: hferrone
ms.author: kurtie
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, réalité mixte, développement, prise en main, nouveau projet, portage, fonctionnalité, caméra, simulation, émulation, documentation, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, qu’est-ce que la réalité virtuelle, qu’est-ce que la réalité augmentée, MRTK, mixed reality toolkit, mappage spatial, entrée vocale, caméra localisable, émulateur, Azure, tutoriels
ms.openlocfilehash: f47e37f56f203590a16ec804c4a36a6ac601ec61cb2f3b7dfb69987d411eef15
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202843"
---
# <a name="unity-development-for-hololens"></a>Développement Unity pour HoloLens

![Logo de bannière Unity](../images/unity_logo_banner.png)

Unity est l’une des principales plateformes de développement en temps réel du marché. Son code de runtime sous-jacent est écrit en C++ et tous les scripts de développement sont écrits en C# . Quel que soit le type de projet qui vous intéresse, qu’il s’agisse de créer des jeux, des films, des animations ou encore de restituer des concepts architecturaux ou d’ingénierie dans un monde virtuel, Unity a l’infrastructure qu’il vous faut. Lorsque vous êtes prêt à démarrer, passez en revue les points de contrôle de développement ci-dessous !

> [!IMPORTANT]
> Jetez un coup d’œil à nos **[guides de portage](../porting-apps/porting-overview.md)** si vous avez un projet Unity existant que vous souhaitez migrer vers HoloLens 2. Nous avons des guides pour les projets qui utilisent HTK, MRTK v1 ou SteamVR.

## <a name="development-checkpoints"></a>Points de contrôle de développement

Utilisez les points de contrôle suivants pour intégrer vos jeux et applications Unity dans le monde de la réalité mixte. Si vous n’avez pas encore exploré l’[exemple d’application Designing Holograms](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd), nous vous recommandons de le télécharger et de l’utiliser pour vous familiariser avec les bases de l’expérience utilisateur de la réalité mixte.

## <a name="1-getting-started"></a>1. Mise en route

Le moyen le plus simple de développer dans Unity consiste à utiliser le Mixed Reality Toolkit. MRTK vous aide à configurer automatiquement un projet pour la réalité mixte, et fournit un ensemble de fonctionnalités afin d’accélérer votre processus de développement. À la fin de cette section, vous aurez une compréhension de base de Mixed Reality Toolkit, un environnement de développement correctement configuré pour les applications de réalité mixte et un projet MRTK fonctionnel dans Unity que vous aurez créé vous-même.

|  Point de contrôle  |  Résultat  |
| --- | --- |
| [Présentation du Mixed Reality Toolkit](mrtk-getting-started.md) | Commencez votre parcours en vous familiarisant avec Mixed Reality Toolkit et ce qu’il peut offrir. |
| [Télécharger Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) | Un nouvel outil de développement pour la découverte, la mise à jour et l’ajout de packages de fonctionnalités Mixed Reality à vos projets Unity |
| [Configurer votre environnement de développement](../install-the-tools.md) | Téléchargez et installez le dernier package Unity et configurez votre projet pour la réalité mixte. |
| [Suivre la série de tutoriels HoloLens 2](tutorials/mr-learning-base-01.md) | Plongez-vous dans les tutoriels MRTK de niveau débutant pour le matériel HoloLens 2. |

> [!IMPORTANT]
> Si vous souhaitez créer un projet Unity sans importer le Mixed Reality Toolkit, vous devez changer manuellement quelques paramètres dans Unity pour Windows Mixed Reality. Pour plus d’informations, consultez notre [guide de configuration](choosing-unity-version.md).

> [!NOTE]
> Une fois que vous avez configuré MRTK dans votre projet, les objets de jeu Unity standard tels que la caméra s’illuminent immédiatement pour une expérience à l’échelle assise. Vous trouverez des instructions sur la modification de l’échelle de l’expérience de votre application dans la page sur les [systèmes de coordonnées](coordinate-systems-in-unity.md).

## <a name="2-core-building-blocks"></a>2. Fonctionnalités principales

Tous les composants principaux pour les applications de réalité mixte sont exposés de manière cohérente avec les autres API Unity. Ces composants sont disponibles en tant que fonctionnalités autonomes et par le biais de Mixed Reality Toolkit. Vous n’aurez peut-être pas besoin de tous les composants à la fois, mais nous vous recommandons de les explorer dès le départ. Après avoir exploré les composants de base listés ci-dessous, vous disposerez d’une boîte à outils remplie de fonctionnalités que vous pourrez intégrer dans un projet de réalité mixte de façon autonome ou par le biais de MRTK.

|  Fonctionnalité  |  Fonctions  |
| --- | --- |
| [Appareil photo](../unity/camera-in-unity.md) | Optimisez de manière exhaustive la qualité visuelle et la stabilité des hologrammes dans vos applications de réalité mixte |
| [Verrouillage du monde et ancres spatiales](spatial-anchors-in-unity.md) | Corrigez les problèmes de stabilisation, ajustez la caméra et intégrez une solution offrant un système de coordonnées stable |
| [Expériences partagées](shared-experiences-in-unity.md) | Affichez et interagissez de manière collective avec le même hologramme à un point fixe dans l’espace à l’aide du partage d’ancrage spatial. |
| [Pointage du regard](../unity/gaze-in-unity.md) | Autorisez des utilisateurs à cibler des hologrammes en les regardant |
| [Contrôleurs de mouvement](../unity/motion-controllers-in-unity.md) | Ajoutez des actions spatiales à vos applications de réalité mixte |
| [Mouvements](../unity/gestures-in-unity.md) | Utilisez les mouvements de la main comme entrée dans vos expériences de réalité mixte |
| [Suivi du regard et des mains](../unity/hand-eye-in-unity.md) | Intégrez une entrée de suivi du regard et des mains dans votre expérience utilisateur |
| [Mappage spatial](../unity/spatial-mapping-in-unity.md) | Mappez votre espace physique avec une superposition de maillage virtuel afin de marquer les limites de votre environnement |
| [Son spatial](../unity/spatial-sound-in-unity.md) | Améliorez vos applications avec un son immersif en 3D |
| [Text](../unity/text-in-unity.md) | Obtenez un texte clair et de haute qualité avec une taille et un rendu de qualité gérables |
| [Entrée vocale](../unity/voice-input-in-unity.md) | Capturez des mots clés, des expressions et une dictée à partir de vos utilisateurs|

## <a name="3-advanced-features"></a>3. Fonctionnalités avancées

D’autres fonctionnalités clés qui jouent un rôle dans les applications de réalité mixte sont disponibles par le biais des API Unity sans aucun package ou configuration supplémentaire. Ces fonctionnalités peuvent être ajoutées aux projets Unity même si MRTK n’est pas installé. Après avoir exploré les fonctionnalités avancées offertes par Unity, vous serez en mesure de créer des applications de réalité mixte complexes et plus approfondies.

|  Fonctionnalité  |  Fonctions  |
| --- | --- |
| [Caméra photo/vidéo](locatable-camera-in-unity.md) | Capturez des photos et du contenu vidéo dans votre application de réalité mixte. |
| [Point de focus](focus-point-in-unity.md) | Fournissez à HoloLens une indication concernant la meilleure façon d’effectuer la stabilisation sur les hologrammes actuellement affichés. |
| [Perte de suivi](tracking-loss-in-unity.md) | Gérez des scénarios dans lesquels votre appareil ne peut pas se trouver dans l’espace universel des applications. |
| [Saisie au clavier](keyboard-input-in-unity.md) | Bénéficiez d’une entrée à partir de claviers réels et de réalité mixte dans vos applications. |

## <a name="4-deploying-to-a-device-or-emulator"></a>4. Déploiement sur un appareil ou un émulateur

Une fois que votre projet Unity holographique est prêt à être testé, l’étape suivante consiste à exporter et à créer une solution Visual Studio Unity. Avec cette solution Visual Studio, vous pouvez exécuter votre application de l’une des trois manières suivantes, sur un appareil réel ou simulé. À la fin de cette section, vous serez en mesure de déployer votre application sur l’appareil ou l’émulateur adapté à vos besoins de développement.

* [Casque immersif HoloLens ou Windows Mixed Reality](../platform-capabilities-and-apis/using-visual-studio.md)
* [Émulateur HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
* [Simulateur de casque immersif Windows Mixed Reality](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="5-adding-services"></a>5. Ajout de services

À ce stade de votre parcours de développement, vous souhaiterez peut-être ajouter des services ou bénéficier d’une aide au déploiement commercial. L’intégration des [services cloud Azure](../mixed-reality-cloud-services.md) peut constituer un atout majeur pour vos projets. Nous avons compilé quelques points de départ qui vous permettront de découvrir et d’étendre vos connaissances en réalité mixte.

[!INCLUDE[](../includes/unity-cloud-services-d365.md)]

Nous avons également une [liste complète de documentation de support pour les services Azure supplémentaires](../mixed-reality-cloud-services.md#standalone-unity-services) que vous pouvez ajouter à vos projets Unity en libre-service.

## <a name="6-low-code-alternatives"></a>6. Alternatives avec peu de code

[!INCLUDE[](../includes/unity-low-code.md)]

## <a name="whats-next"></a>Quelle est l’étape suivante ?

Le travail d’un développeur n’est jamais terminé, en particulier lorsqu’il s’agit d’apprendre un nouvel outil ou kit SDK. Les sections suivantes peuvent vous amener dans des domaines qui vont au-delà de la documentation niveau débutant que vous connaissez déjà, et vous fournir des ressources utiles si vous êtes bloqué. Notez que ces rubriques et ressources ne sont pas listées dans un ordre séquentiel particulier. N’hésitez donc pas à vous y plonger et à les explorer !

### <a name="porting"></a>Portage

Si vous voulez effectuer le portage d’applications existantes, consultez les articles ci-dessous :

* [HoloToolkit/MRTK vers MRTK v2](../porting-apps/porting-hl1-hl2.md)
* [Guide de portage pour les applications immersives](../porting-apps/porting-guides.md)
* [Guide de portage d’entrée](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

### <a name="tutorials"></a>Tutoriels

Si vous souhaitez ajouter des fonctionnalités de réalité mixte spécifiques à vos applications, nous proposons plusieurs tutoriels qui peuvent vous guider dans le processus de bout en bout. Notre contenu HoloLens 2 et HoloLens (1re génération) le plus connu est listé ci-dessous, mais vous pouvez accéder à l’intégralité de la collection en consultant la vue d’ensemble des tutoriels.

[!INCLUDE[](../includes/unity-tutorials.md)]

### <a name="additional-resources"></a>Ressources supplémentaires

Avant de vous lancer dans le monde de la réalité mixte, nous vous recommandons de consulter la documentation relative à MRTK indiquée ci-dessous. Ces articles constituent un excellent point de départ pour comprendre le fonctionnement détaillé de MRTK, et offrent de précieux conseils sur la façon de rendre votre application plus performante.

|  Rubrique  |  Description  |
| --- | --- |
| [Vue d’ensemble de l’architecture de MRTK](/windows/mixed-reality/mrtk-unity/architecture/overview) | Découvrez en détail comment MRTK opère dans vos projets. |
| [Paramètres et performances](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started) | Profilez votre application, mettez à jour vos paramètres Unity et bénéficiez des meilleures performances de stabilisation d’hologrammes disponibles. |
| [Bien démarrer avec MRTK + XR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk) | Effectuez le transfert vers l’autre pipeline XR fourni par Unity. |

### <a name="unity-resources"></a>Ressources Unity

En plus de cette documentation disponible sur docs.microsoft.com, Unity installe la documentation sur la fonctionnalité Windows Mixed Reality avec l’éditeur Unity. La documentation fournie par Unity comprend deux sections distinctes.

|  Ressource  |  Description  |
| --- | --- |
| [Référence des scripts](https://docs.unity3d.com/ScriptReference/) | Cette section de la documentation contient des détails sur l’API de script fournie par Unity, et est accessible en ligne à partir de l’éditeur Unity en cliquant sur **Help > Scripting Reference**. |
| [Manuel](https://docs.unity3d.com/Manual/index.html) | Ce manuel a pour but de vous aider à apprendre à utiliser Unity, des techniques de base aux techniques avancées. Il est accessible en ligne ou à partir de l’éditeur Unity en cliquant sur **Help > Manual**. |

> [!div class="nextstepaction"]
> [Explorer MRTK](mrtk-getting-started.md)

## <a name="have-feedback"></a>Vous voulez donner votre avis ?

Vous nous trouverez sur les [forums Unity](https://aka.ms/unityforums) en utilisant l’étiquette **Microsoft** et une combinaison des étiquettes suivantes pour nous aider à comprendre pour quel plug-in vous fournissez un feedback :

* HoloLens 2 
* Windows Mixed Reality
* OpenXR
* XRSDK
* XR antérieur

## <a name="see-also"></a>Voir également

* [Mixed Reality Toolkit v2](mrtk-getting-started.md)
* [Réalité mixte - Principes fondamentaux - Cours 100 : Bien démarrer avec Unity](tutorials/holograms-100.md)
* [Paramètres recommandés pour Unity](recommended-settings-for-unity.md)
* [Recommandations de performances pour Unity](performance-recommendations-for-unity.md)
* [Exportation et création de solutions Unity Visual Studio](exporting-and-building-a-unity-visual-studio-solution.md)
* [Utilisation de l’espace de noms Windows avec les applications Unity pour HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [Bonnes pratiques sur l’utilisation d’Unity et de Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)
* [Mode Lecture Unity](unity-play-mode.md)
* [Guides de portage](../porting-apps/porting-guides.md)
