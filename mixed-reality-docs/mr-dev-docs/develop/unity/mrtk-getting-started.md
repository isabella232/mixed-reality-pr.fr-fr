---
title: Présentation de MRTK pour Unity
description: Pour les nouveaux développeurs qui souhaitent utiliser le MRTK
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, test, Mixed Reality Toolkit, MRTK version 2, MRTK, outils, SDK, HoloLens, HoloLens 2, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, multiplateforme
ms.openlocfilehash: 6887d79d4a0737f3ed0f63af5686699fc7a1a2b6
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613443"
---
# <a name="introducing-mrtk-for-unity"></a>Présentation de MRTK pour Unity

![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>Qu’est-ce que le MRTK (Mixed Reality Toolkit) ?
Le MRTK est un fantastique kit d’outils open source qui existe depuis le lancement d’HoloLens. Il ne serait pas ce qu’il est aujourd’hui sans le dur travail réalisé par notre communauté de développeurs qui y ont apporté leur contribution. Au cours des trois dernières années, nous avons écouté les commentaires de notre communauté de développeurs et nous avons créé MRTK v2 afin de prendre en compte les problèmes majeurs qui nous ont été remontés.  

MRTK pour Unity est un kit de développement multiplateforme open source pour les applications de réalité mixte. Le kit d’outils fournit un système d’entrée multiplateforme, des composants fondamentaux ainsi que des modules communs pour les interactions spatiales. MRTK version 2 vise à accélérer le développement des applications qui ciblent Microsoft HoloLens, les casques immersifs Windows Mixed Reality (VR) et la plateforme OpenVR. Le projet a pour but de réduire le nombre d’obstacles qui gênent la création d’applications de réalité mixte et d’apporter une contribution à la Communauté de la réalité mixte.

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

Jetez un coup d’œil à la [documentation MRTK sur GitHub](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) et prenez en main le [Guide d’installation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html).


## <a name="new-with-mrtk-v2"></a>Nouveautés de MRTK v2
Nous souhaitons souligner notre engagement envers ces outils de plateforme.  En fait, nous avons utilisé MRTK version 2 pour développer nos expériences intégrées, comme l’expérience d’installation OOBE et notre application Mixed Reality Tips. Vous verrez également de nouvelles fonctionnalités d’HoloLens 2 exposées pour la première fois par le biais du MRTK, car selon nous, il s’agit de la meilleure méthode pour développer sur notre plateforme. 

### <a name="modular"></a>Modularité
Nous avons conçu ce kit d’une façon modulaire pour que vous n’ayez pas besoin d’en utiliser tous les composants dans votre projet.  Cela présente plusieurs avantages.  Votre projet conserve une taille limitée et est plus facile à gérer.  De plus, comme le kit est conçu avec des objets scriptables et qu’il est basé sur une interface, vous pouvez remplacer ses composants par les vôtres, ce qui rend possible la prise en charge d’autres services, systèmes et plateformes.

### <a name="cross-platform"></a>Système multiplateforme
Justement, à propos des autres plateformes, le kit fournit une prise en charge multiplateforme.  Cela ne signifie pas pour autant que toutes les plateformes sont prises en charge, mais nous avons fait en sorte que tout le code existant dans le kit d’outils continue de s’exécuter correctement lorsque vous basculez votre cible de build vers d’autres plateformes.  La robustesse et l’extensibilité de la conception modulaire permettent à vos applications de prendre en charge plusieurs plateformes, parmi lesquelles ARCore, ARKit et OpenVR.

### <a name="performant"></a>Performance
Nous avons conçu le kit d’outils dans un souci de vous offrir des performances optimales sur les plateformes mobiles.  C’est un point très important, notre but étant que les outils vous facilitent la tâche, et pas qu’ils vous la compliquent.

## <a name="see-also"></a>Voir aussi
* [Installer les outils](../install-the-tools.md)
* [MRTK - Guide d’installation (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [Page d’accueil de la documentation MRTK (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [Portage de HoloToolkit/MRTK vers MRTK version 2 (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
