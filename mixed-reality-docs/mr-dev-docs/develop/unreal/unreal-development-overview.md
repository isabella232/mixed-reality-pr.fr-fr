---
title: Vue d’ensemble du développement Unreal
description: Vue d’ensemble du développement en réalité mixte avec Unreal Engine 4
author: hferrone
ms.author: v-hferrone
ms.date: 08/04/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, streaming, communication à distance, réalité mixte, développement, démarrage, fonctionnalités, nouveau projet, émulateur, documentation, guides, fonctionnalités, hologrammes, développement de jeux, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle
ms.openlocfilehash: b810ad7500f8bb2a70ef18ad29fb32df8801a2de
ms.sourcegitcommit: 2759aba06e643d70004023b105ed26b33ce3dbfa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94810445"
---
# <a name="unreal-development-overview"></a>Vue d’ensemble du développement Unreal

![Logo de bannière Unreal](../images/unreal_logo_banner.png)

Démarrer avec les <a href="https://docs.microsoft.com/windows/mixed-reality" target="_blank" title="Documentation Mixed Reality"> applications de réalité mixte</a> n’est pas chose aisée. Nouveaux concepts, nouvelles plateformes, matériel de pointe : tout cela peut être vu comme un obstacle. Toutefois, si vous êtes développeur Unreal, vous avez de la chance. La prise en charge de <a href="https://www.microsoft.com/windows/windows-mixed-reality" target="_blank" title="Documentation Windows Mixed Reality">Windows Mixed Reality</a> (VR) et de <a href="https://www.microsoft.com/hololens/hardware" target="_blank" title="Documentation HoloLens 2">HoloLens 2</a> (réalité augmentée) est maintenant incluse dans la dernière <a href="https://docs.unrealengine.com/Support/Builds/ReleaseNotes/4_25/index.html" target="_blank" title="Notes de publication Unreal Engine 4.25">version</a> d’Unreal Engine. Voici ce que cette mise à jour comprend :
* Prise en charge du plug-in Mixed Reality UX Tools
* Prise en charge d’OpenXR
* Communication à distance d’application à partir d’une application de bureau
* Meilleures performances
* MRC (Mixed Reality Capture)
* Prise en charge initiale pour Azure Spatial Anchors

Si vous n’avez aucune expérience du développement Unreal, ne vous lancez pas tête baissée. Explorez la <a href="https://docs.unrealengine.com/GettingStarted/index.html" target="_blank">série de tutoriels</a> Unreal pour devenir rapidement opérationnel en recherchant des ressources sur la <a href="https://www.unrealengine.com/marketplace/store" target="_blank">place de marché</a> Unreal et de l’aide sur les <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">forums</a> de réalité mixte. Ces ressources constituent vos liens avec la communauté de concepteurs et de solutionneurs de problèmes sur le marché de la réalité mixte d’aujourd’hui.

> [!IMPORTANT]
> Jetez un coup d’œil à nos **[guides de portage](unreal-reverb-g2-controllers.md)** si vous avez un projet Unreal existant que vous voulez passer sur des casques immersifs, comme le Reverb G2.

## <a name="development-checkpoints"></a>Points de contrôle de développement

Utilisez les points de contrôle suivants pour amener vos jeux et applications Unreal dans le monde de la réalité mixte. Si vous n’avez pas encore exploré l’[exemple d’application Designing Holograms](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd), nous vous recommandons de le télécharger et de l’utiliser pour vous familiariser avec les bases de l’expérience utilisateur de la réalité mixte.

### <a name="1-getting-started"></a>1. Mise en route

[Mixed Reality Toolkit for Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal) est un ensemble de composants conçus pour accélérer votre développement dans Unreal. Chaque composant comprend des plug-ins, des exemples et une documentation pour configurer des expériences immersives.

* [UX Tools for Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal) est le premier composant à être publié et n’est actuellement pris en charge que sur HoloLens 2. Le plug-in de composant comprend du code, des blueprints et des exemples de ressources de fonctionnalités d’expérience utilisateur courantes pour la simulation d’entrée, les acteurs d’interaction manuelle, les composants de bouton actionnable, les composants de manipulateur et les composants de comportement suiveur.

À la fin de cette section, vous aurez des connaissances de base du Mixed Reality Toolkit, un environnement de développement correctement configuré pour les applications de réalité mixte et un projet MRTK opérationnel dans Unreal.

|  Point de contrôle  |  Résultat  |
| --- | --- |
| [Installer les outils les plus récents](../install-the-tools.md) | Télécharger et installer la dernière version d’Unreal Engine, et configurer votre projet pour la réalité mixte |
| [Série de tutoriels HoloLens 2](tutorials/unreal-uxt-ch1.md) | Plongez-vous dans les tutoriels MRTK de niveau débutant pour le matériel HoloLens 2. |

### <a name="2-core-building-blocks"></a>2. Fonctionnalités principales

Notre série de tutoriels n’aborde pas certaines caractéristiques clés du développement en réalité mixte. Ces modules sont disponibles en tant que fonctionnalités autonomes et par le biais du Mixed Reality Toolkit. Vous n’aurez peut-être pas besoin de tous ces modules à la fois, mais nous vous recommandons de les explorer au plus tôt. Après avoir exploré les modules de base listés ci-dessous, vous disposerez d’une boîte à outils remplie de fonctionnalités que vous pourrez intégrer dans vos projets de réalité mixte.

[!INCLUDE[](../includes/unreal-building-blocks.md)]

> [!NOTE]
> Pour plus d’informations, explorez le dépôt **[UX Tools pour Unreal sur GitHub](https://github.com/microsoft/MixedReality-UXTools-Unreal)** .

### <a name="3-platform-capabilities-and-apis"></a>3. API et fonctionnalités de la plateforme

D’autres fonctionnalités clés qui jouent un rôle dans les applications de réalité mixte sont disponibles sans aucun package ou configuration supplémentaire. Ces fonctionnalités peuvent être ajoutées aux projets Unreal même si MRTK n’est pas installé. Après avoir exploré ces fonctionnalités avancées, vous pourrez créer des applications de réalité mixte plus complexes.

|  Fonctionnalité  |  Fonctions  |
| --- | --- |
| [Caméra HoloLens](unreal-hololens-camera.md) | Capturez la réalité mixte et le contenu visuel du monde réel à partir de votre application exécutée sur un appareil HoloLens. |
| [Codes QR](unreal-qr-codes.md) | Affichez les codes QR sous la forme d’hologrammes à l’aide d’un système de coordonnées à la position de chaque code dans le monde réel. |
| [WinRT](unreal-winrt.md) | Créez un binaire distinct avec du code WinRT pouvant être consommé par le système de génération d’Unreal. |

### <a name="4-deploying-to-a-device"></a>4. Déploiement sur un appareil

S’il s’agit de la première fois que vous empaquetez ou déployez une application Unreal pour HoloLens, vous devrez [télécharger les fichiers de prise en charge](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) à partir de l’Epic Launcher. Une fois que ces fichiers sont installés, vous pouvez effectuer le déploiement à partir de l’[éditeur Unreal](unreal-deploying.md) ou du [portail de l’appareil](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal).

### <a name="5-adding-services"></a>5. Ajout de services

À ce stade de votre parcours de développement, vous souhaiterez peut-être ajouter des services ou bénéficier d’une aide au déploiement commercial. L’intégration de [services cloud Azure](../mixed-reality-cloud-services.md) et de fonctionnalités Dynamics 365 peut constituer un atout majeur pour vos projets. Nous avons compilé quelques points de départ qui vous permettront de découvrir et d’étendre vos connaissances en réalité mixte.

[!INCLUDE[](../includes/unreal-cloud-services-d365.md)]

## <a name="whats-next"></a>Quelle est l’étape suivante ?

Le travail d’un développeur n’est jamais terminé, en particulier lorsqu’il s’agit d’apprendre un nouvel outil ou kit SDK. Les sections suivantes peuvent vous amener dans des domaines qui vont au-delà de la documentation niveau débutant que vous connaissez déjà, et vous fournir des ressources utiles si vous êtes bloqué. Notez que ces rubriques et ressources ne sont pas listées dans un ordre séquentiel particulier. N’hésitez donc pas à vous y plonger et à les explorer !

### <a name="streaming--debugging"></a>Diffusion en streaming et débogage

Si vous souhaitez tester votre application en cours de développement sur un appareil HoloLens, vous pouvez [la diffuser en streaming directement à partir de votre PC](unreal-streaming.md) à l’aide de l’éditeur Unreal ou d’un fichier exécutable Windows empaqueté.

Si vous envisagez de déboguer l’application avec Visual Studio, suivez ces [instructions](https://docs.microsoft.com/visualstudio/debugger/debug-installed-app-package#remote).

### <a name="performance"></a>Performances

Le développement pour la réalité mixte s’accompagne de points de contrôle de performances qui varient en fonction de la plateforme. Une application HoloLens 2 doit s’exécuter à 60 images par seconde pour que les hologrammes apparaissent stables et réactifs. Heureusement, nous avons des [recommandations sur les performances](performance-recommendations-for-unreal.md) pour y parvenir dans vos applications Unreal.

## <a name="supported-features"></a>Fonctionnalités prises en charge

| Fonctionnalité HoloLens 2 | Version la plus ancienne d’Unreal Engine prise en charge |
| ----------- | ----------- |
| Prise en charge d’ARM64 | 4.23 |
| Streaming depuis un PC | 4.23 |
| Mappage spatial | 4.23 |
| Suivi des mains et des articulations | 4.23 |
| Eye-tracking | 4.23 |
| Entrée vocale | 4.23 |
| Ancres spatiales | 4.23 |
| Accès à la caméra | 4.23 |
| Codes QR | 4.23 |
| Audio spatial | 4.23 |
| Prise en charge d’un écran de spectateur pour le streaming | 4.24 |
| LSR plan en streaming | 4.24 |
| Exemples d’applications ([HoloLens2Example](https://github.com/microsoft/MixedReality-Unreal-Samples) et [Mission AR](https://docs.unrealengine.com/Resources/Showcases/MissionAR/index.html)) | 4.24 |
| Multivue mobile : Les performances atteignent 60 i/s | 4.25 |
| Rendu 3ème caméra | 4.25 |
| Streaming partir d’une application de poste de travail empaquetée | 4.25.1 |
| Azure Spatial Anchors pour HoloLens 2 (bêta) | 4.25 |
| Prise en charge d’OpenXR (bêta) | 4.25 |
| Prise en charge d’UX Tools (0.8) | 4.25 |
| Documentation et tutoriels pour les développeurs | 4.25 |

> [!div class="nextstepaction"]
> [Installer les outils](../install-the-tools.md)

## <a name="see-also"></a>Voir aussi
* <a href="https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html" target="_blank">Documents Unreal pour le streaming, le déploiement sur l’émulateur et l’appareil</a>
* <a href="https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html" target="_blank">Conseils d’optimisation des performances sur les appareils mobiles avec Unreal</a>
