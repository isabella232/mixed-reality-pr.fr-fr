---
title: Commencer à concevoir et à créer des prototypes
description: Si vous êtes prêt à vous lancer, découvrez les concepts de base dont vous avez besoin pour commencer à concevoir et à créer des prototypes.
author: grbury
ms.author: grbury
ms.date: 08/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: réalité mixte, découvrir, distribuer, index, page d’accueil, conception, développement, tutoriels, exemples d’applications, principes fondamentaux, études de cas, ressources, procédures HoloLens, projets open source, concepts principaux, interaction
ms.openlocfilehash: 19a83a132cca08573f1066a2f7b87bd383ca79f4
ms.sourcegitcommit: 8a80613f025b05a83393845d4af4da26a7d3ea9c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94573273"
---
# <a name="start-designing-and-prototyping"></a>Commencer à concevoir et à créer des prototypes

![résumé de la conception en réalité mixte](images/design-hero-image.png)

Les applications de réalité mixte ne ressemblent à rien d’autre de ce qui se fait aujourd’hui, et leur conception est ardue. Vous devez prendre en compte non seulement les nouvelles combinaisons de mondes réels et virtuels que vous créez, mais également les nouveaux types d’expériences utilisateur qu’ils engendrent. La réalité mixte étant un vaste sujet, nous avons sélectionné quelques points importants de son spectre de conception, que nous présentons ci-dessous sous la forme d’une série de points de contrôle. Ces points de contrôle se veulent séquentiels, mais si vous avez déjà une expérience préalable, n’hésitez pas à passer directement à l’une des sections suivantes.

## <a name="design-checkpoints"></a>Points de contrôle de conception

Utilisez les points de contrôle suivants pour intégrer vos concepts et idées d’application dans le monde de la réalité mixte.

### <a name="1-getting-started"></a>1. Mise en route

Comme tout parcours, votre aventure dans la conception d’applications de réalité mixte commence par les notions de base. Nous vous recommandons de vous familiariser avec les articles [Qu’est-ce que la réalité mixte ?](../discover/mixed-reality.md) et [Qu’est-ce qu’un hologramme ?](../discover/hologram.md) pour vous aider à appréhender les concepts de conception immersive. Une fois la lecture terminée, vous serez prêt à entamer votre parcours de conception de réalité mixte !

![Gif Bien démarrer avec l’application Designing Holograms](images/HandTracking2.gif)

|  Point de contrôle  |  Résultat  |
| --- | --- |
| [Développer votre processus de conception](../discover/case-study-expanding-the-design-process-for-mixed-reality.md) | Découvrez un premier aperçu du processus de conception de réalité mixte, collecté auprès de concepteurs internes et externes à Microsoft. |
| [Types d’applications de réalité mixte](types-of-mixed-reality-apps.md) | Décidez de l’emplacement de votre application sur le spectre de la réalité mixte. |
| [Application Designing Holograms](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd) | Découvrez les bases de la conception d’une expérience utilisateur de réalité mixte en explorant comportements, conseils et recommandations en réalité mixte pour créer des applications HoloLens incroyables (disponibles en téléchargement sur le Microsoft Store dans HoloLens 2). |
| [Hub d’exemples MRTK](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4) | Découvrez les interactions spatiales et les composants de création UX courants pour la réalité mixte (disponibles en téléchargement sur le Microsoft Store dans HoloLens 2) |
### <a name="2-core-concepts"></a>2. Concepts principaux

Que vous développiez pour la réalité virtuelle (VR) ou la réalité augmentée (AR), plusieurs concepts de base s’appliquent à la conception d’expériences immersives et fluides. Comprendre le point de vue des utilisateurs, positionner les objets et s’assurer que tout le monde est à l’aise et en sécurité constituent vos priorités principales à ce stade de votre parcours. À la fin de cette section, vous disposerez d’une fondation solide pour passer à la conception de l’interaction.

![Image d’exemple de concepts principaux](images/fragments-750px.jpg)

|  Concept  |  Résultat  |
| --- | --- |
| [Image holographique](holographic-frame.md) | Comprenez comment les utilisateurs voient votre contenu superposé sur le monde réel lorsqu’ils portent leurs casques. |
| [Systèmes de coordonnées](coordinate-systems.md) | Découvrez comment positionner précisément des hologrammes à des endroits significatifs pour l’utilisateur, qu’il s’agisse d’une pièce physique ou d’un monde virtuel que vous avez créé. |
| [Mappage spatial](spatial-mapping.md) | Ancrez des objets dans l’environnement de l’utilisateur et tirez parti des surfaces physiques du monde réel. |
| [Considérations relatives au confort](comfort.md) | Garantissez la sécurité et le confort des utilisateurs en créant et en présentant un contenu immersif d’une manière qui imite le monde naturel. |

### <a name="3-interaction-design"></a>3. Conception des interactions

Quels que soient sa beauté et son caractère immersif, une expérience virtuelle est inutile sans interaction. Cette section décrit les modèles d’interaction de base, les contrôleurs de main et de mouvement, l’utilisation de l’entrée vocale et la collecte des données d’eye tracking à partir de vos utilisateurs. À la fin de cette section, vous serez prêt à aborder le dernier aspect majeur de votre parcours de conception : l’expérience utilisateur.

![Facteurs de conception des interactions](images/UX_Hero_Manipulation.jpg)

|  Concept  |  Résultat  |
| --- | --- |
| [Modèles d’interaction](interaction-fundamentals.md) | Fournissez à vos utilisateurs des interactions instinctives par le biais d’entrées manuelles, oculaires et vocales. |
| [Mains et contrôleurs de mouvement](hands-and-tools.md) | Découvrez comment les hologrammes peuvent être touchés et manipulés à proximité avec les mains d’un utilisateur ou à distance avec des interactions précises. |
| [Entrée vocale](voice-input.md) | Utilisez des commandes vocales comme entrée dans vos applications immersives afin de contrôler les environnements et les hologrammes environnants.  |
| [Eye tracking](eye-tracking.md) | Ajoutez un nouveau niveau de contexte et de compréhension humaine dans une expérience holographique en utilisant des informations sur ce que vos utilisateurs regardent. |

### <a name="4-user-experience-elements"></a>4. Éléments de l’expérience utilisateur

Maintenant que vous maîtrisez les interactions de base, vous pouvez vous concentrer sur les points plus fins des éléments de l’expérience utilisateur et sur la manière de les adapter aux environnements uniques de la réalité mixte. Vous aborderez les comportements courants, la conception des actifs, la mise à l’échelle des objets et la typographie, tout ceci en veillant à rendre vos applications le plus intuitives possible pour les utilisateurs. Cette section marque la fin du parcours de conception officiel de la réalité mixte, mais vous trouverez davantage de ressources dans la section [Prochaine étape](#whats-next) si vous voulez poursuivre l’aventure.

![Éléments de l’expérience utilisateur](images/UX_Hero_BoundingBox.jpg)

|  Concept  |  Résultat  |
| --- | --- |
| [Contrôles et comportements communs](app-patterns-landingpage.md) | Découvrez les modules d’interface utilisateur et les interactions spatiales fréquemment utilisés. |
| [Couleurs, éclairage et matériaux](color-light-and-materials.md) | Concevez des actifs de qualité pour la réalité mixte qui prennent en compte la couleur, l’éclairage et les matériaux. |
| [Mise à l’échelle des objets](scale.md) | Incorporez autant d’indicateurs visuels réels que possible pour aider vos utilisateurs à comprendre où se trouvent les objets, quelle est leur taille et à quoi ils servent. |
| [Typographie](typography.md) | Utilisez du texte clair et lisible dans un espace tridimensionnel afin de fournir aux utilisateurs les informations importantes dont ils ont besoin. |

## <a name="whats-next"></a>Quelle est l’étape suivante ?

Le travail d’un concepteur n’est jamais terminé, surtout lorsqu’il s’agit d’apprendre à créer des expériences immersives dans un nouveau paradigme. Les sections suivantes vous permettront d’aller au-delà de la documentation de conception de niveau débutant que vous avez déjà consultée, et de vous plonger dans le monde du développement de la réalité mixte. Ces rubriques et ressources ne sont pas listées dans un ordre séquentiel particulier. N’hésitez donc pas à les explorer !

### <a name="choose-a-prototyping-option"></a>Choisir une option de prototypage  

:::row:::   
    :::column:::    
       [![Découvrir Unity](images/logo-unity.png)](https://learn.unity.com/)<br>
        **[Découvrir Unity](https://learn.unity.com/)**<br>
        Découvrez comment créer des expériences interactives avec Unity. Apprenez par la pratique, du début à la fin.
    :::column-end:::    
    :::column:::    
        [![Mixed Reality Toolkit (MRTK)](images/74-12.png)](https://github.com/Microsoft/MixedRealityToolkit-Unity)<br>
        **[Mixed Reality Toolkit (MRTK)](https://github.com/Microsoft/MixedRealityToolkit-Unity)**<br>  
        Avec l’interaction spatiale et les composants d’interface utilisateur, démarrez la conception et le développement de votre réalité mixte avec Unity.   
    :::column-end:::
    :::column:::    
        [![Mixed Reality Design Labs](images/74-13.png)](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)<br>
        **[Mixed Reality Design Labs](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)**<br>  
        Obtenez des exemples d’applications qui vous montrent comment utiliser les composants de MRTK pour créer de superbes expériences de réalité mixte.
    :::column-end:::        
    :::column:::    
        [![Microsoft Maquette](images/74-14.png)](https://www.maquette.ms/)<br>
        **[Microsoft Maquette](https://www.maquette.ms/)**<br>  
        Conception de réalité virtuelle. Microsoft maquette rend le prototypage spatial facile, rapide et immersif. 
    :::column-end:::    
:::row-end:::

<br>

---

### <a name="additional-resources"></a>Ressources supplémentaires

:::row:::
    :::column:::
       [![Comprendre les principes de base](images/74-15.png)](../discover/get-started-with-mr.md#understand-the-basics)<br>
        **[Comprendre les principes de base](../discover/get-started-with-mr.md#understand-the-basics)**<br>
        Approfondissez votre compréhension de ce qui définit la réalité mixte et de la manière de l’utiliser.
    :::column-end:::
    :::column:::
        [![Participer à un événement](images/74-16.png)](../whats-new/sf-academy-events.md)<br>
         **[Participer à un événement](../whats-new/sf-academy-events.md)**<br>
        Venez voir le matériel et participer à un atelier pratique pour créer votre première application HoloLens 2.
    :::column-end:::
    :::column:::
        [![Installer les outils](images/74-17.png)](../develop/install-the-tools.md)<br>
         **[Installer les outils](../develop/install-the-tools.md)**<br>
        Utilisez la liste de vérification de l’installation pour obtenir les outils dont vous avez besoin pour créer des applications pour HoloLens et la réalité mixte.
    :::column-end:::
    :::column:::
        [![Commencer à développer](images/74-18.png)](../develop/development.md)<br>
        **[Commencer à développer](../develop/development.md)**<br>
        Choisissez un chemin de développement en fonction de votre niveau de compétence, de votre méthode de travail ou de la plateforme qui vous intéresse.
    :::column-end:::
:::row-end:::

<br>

<br>