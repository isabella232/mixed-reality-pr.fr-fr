---
title: Développement Unity pour VR
description: Prise en main de la création d’applications de réalité mixte dans Unity pour les casques immersifs VR et Windows Mixed Reality.
author: hferrone
ms.author: kurtie
ms.date: 12/11/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, réalité mixte, développement, prise en main, nouveau projet, portage, fonctionnalité, caméra, simulation, émulation, documentation, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, qu’est-ce que la réalité virtuelle, qu’est-ce que la réalité augmentée, MRTK, mixed reality toolkit, entrée vocale, caméra localisable, émulateur, Azure, tutoriels
ms.openlocfilehash: 50300ff08dd06c5fc250bc93979d537e10b38044
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528714"
---
# <a name="unity-development-for-vr-and-windows-mixed-reality"></a>Développement Unity pour VR et Windows Mixed Reality

![Logo de bannière Unity](../images/unity_logo_banner.png)

Si vous débutez avec Unity, nous vous recommandons d’explorer les [tutoriels](https://unity3d.com/learn/tutorials) de niveau débutant sur la plateforme Unity Learn avant de continuer. Vous pouvez également consulter les [forums de réalité mixte Unity](https://forum.unity3d.com/forums/hololens.102/) afin d’entrer en contact avec la communauté en ligne qui crée des applications de réalité mixte. Vous pourriez y trouver des ressources ou solutions très intéressantes. Quand vous êtes prêt à prendre en main MRTK, passez en revue les points de contrôle de développement ci-dessous.

> [!IMPORTANT]
> Consultez nos **[guides de portage](../porting-apps/porting-overview.md)** si vous avez un projet Unity existant que vous voulez porter sur un casque immersif Windows Mixed Reality. 

## <a name="development-checkpoints"></a>Points de contrôle de développement

Utilisez les points de contrôle suivants pour intégrer vos jeux et applications Unity dans le monde de la réalité mixte. 

### <a name="1-getting-started"></a>1. Mise en route

Vous devrez modifier manuellement un petit ensemble de paramètres Unity pour le développement Windows Mixed Reality et VR. Ceux-ci sont divisés en deux catégories : par projet et par scène. À la fin de cette section, vous disposerez des outils et des paramètres de projet pour commencer à créer vos propres applications.

|  Point de contrôle  |  Résultat  |
| --- | --- |
| [Installer les outils les plus récents](../install-the-tools.md) | Téléchargez et installez le dernier package Unity et configurez votre projet pour la réalité mixte. |
| [Configuration de votre projet pour WMR](windows-xr-plugin.md) | Découvrez comment créer des applications qui restituent du contenu numérique sur des périphériques d‘affichage holographiques et VR |

> [!IMPORTANT]
> Pour plus d’informations sur la configuration de vos projets, consultez notre [guide de configuration](choosing-unity-version.md) des projets Unity.

### <a name="2-core-building-blocks"></a>2. Fonctionnalités principales

Après avoir démarré un nouveau projet immersif, vous aurez besoin de quelques composants de base pour développer des applications immersives. Tous les composants principaux pour les applications de réalité mixte sont exposés de manière cohérente avec les autres API Unity. Vous n’aurez peut-être pas besoin de tous les composants à la fois, mais nous vous recommandons de les explorer dès le départ. Après avoir exploré les composants de base listés ci-dessous, vous disposerez d’une boîte à outils riche en fonctionnalités, que vous pourrez intégrer dans un projet VR.

|  Fonctionnalité  |  Fonctions  |
| --- | --- |
| [Appareil photo](../unity/camera-in-unity.md) | Optimisez de manière exhaustive la qualité visuelle et la stabilité des hologrammes dans vos applications de réalité mixte |
| [Verrouillage du monde et ancres spatiales](spatial-anchors-in-unity.md) | Corrigez les problèmes de stabilisation, ajustez la caméra et intégrez une solution offrant un système de coordonnées stable || [Contrôleurs de mouvement](../unity/motion-controllers-in-unity.md) | Ajoutez des actions spatiales à vos applications de réalité mixte |
| [Mouvements](../unity/gestures-in-unity.md) | Utilisez les mouvements de la main comme entrée dans vos expériences de réalité mixte |
| [Son spatial](../unity/spatial-sound-in-unity.md) | Améliorez vos applications avec un son immersif en 3D |
| [Text](../unity/text-in-unity.md) | Obtenez un texte clair et de haute qualité avec une taille et un rendu de qualité gérables |
| [Entrée vocale](../unity/voice-input-in-unity.md) | Capturez des mots clés, des expressions et une dictée à partir de vos utilisateurs|

### <a name="3-advanced-features"></a>3. Fonctionnalités avancées

D’autres fonctionnalités clés jouant un rôle dans les applications immersives sont disponibles via des API Unity sans aucun package ou configuration supplémentaire. Après avoir exploré les fonctionnalités plus avancées offertes par Unity, vous serez en mesure de créer des applications VR complexes et plus approfondies.

|  Fonctionnalité  |  Fonctions  |
| --- | --- |
| [Perte de suivi](tracking-loss-in-unity.md) | Gérez des scénarios dans lesquels votre appareil ne peut pas se trouver dans l’espace universel des applications. |
| [Saisie au clavier](keyboard-input-in-unity.md) | Bénéficiez d’une entrée à partir de claviers réels et de réalité mixte dans vos applications. |

### <a name="4-deploying-to-a-device-or-emulator"></a>4. Déploiement sur un appareil ou un émulateur

Une fois que votre projet Unity holographique est prêt à être testé, l’étape suivante consiste à exporter et à créer une solution Visual Studio Unity. Avec cette solution Visual Studio, vous pouvez exécuter votre application sur des appareils réels ou simulés. À la fin de cette section, vous serez en mesure de déployer votre application sur un appareil ou un émulateur adapté à vos besoins de développement.

* [Casque immersif Windows Mixed Reality](../platform-capabilities-and-apis/using-visual-studio.md)
* [Simulateur de casque immersif Windows Mixed Reality](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="whats-next"></a>Quelle est l’étape suivante ?

Le travail d’un développeur n’est jamais terminé, en particulier lorsqu’il s’agit d’apprendre un nouvel outil ou kit SDK. Les sections suivantes peuvent vous amener dans des domaines qui vont au-delà de la documentation niveau débutant que vous connaissez déjà, et vous fournir des ressources utiles si vous êtes bloqué. Notez que ces rubriques et ressources ne sont pas listées dans un ordre séquentiel particulier. N’hésitez donc pas à vous y plonger et à les explorer !

### <a name="porting"></a>Portage

Si vous voulez effectuer le portage d’applications existantes, consultez les articles ci-dessous :

* [Portage d’applications VR sur Windows Mixed Reality](../porting-apps/porting-guides.md?tabs=project)
* [Mise à jour des applications SteamVR pour Windows Mixed Reality](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)

### <a name="additional-resources"></a>Ressources supplémentaires

Avant de vous lancer dans le monde de la réalité mixte, nous vous recommandons de consulter la documentation supplémentaire ci-dessous. 

* [Guide pour les passionnés de RV](/windows/mixed-reality/enthusiast-guide/vr-journey)
* [Magasin de ressources Unity](https://assetstore.unity.com)

## <a name="see-also"></a>Voir aussi 

* [Paramètres recommandés pour Unity](recommended-settings-for-unity.md)
* [Recommandations de performances pour Unity](performance-recommendations-for-unity.md)
* [Exportation et création de solutions Unity Visual Studio](exporting-and-building-a-unity-visual-studio-solution.md)
* [Bonnes pratiques sur l’utilisation d’Unity et de Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)