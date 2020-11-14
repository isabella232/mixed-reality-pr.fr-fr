---
title: Bien démarrer avec le MRTK version 2
description: Pour les nouveaux développeurs qui souhaitent bien utiliser le MRTK
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, test, Mixed Reality Toolkit, MRTK version 2, MRTK, outils, SDK, HoloLens, HoloLens 2
ms.openlocfilehash: 4513185573003510e5a7cae97ecce4cb5d2552e0
ms.sourcegitcommit: 83c9373fe5b2e07cdab921b6cab3fdd418307003
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94386205"
---
# <a name="getting-started-with-mrtk-for-unity"></a>Bien démarrer avec le MRTK pour Unity
![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>Qu’est-ce que le MRTK (Mixed Reality Toolkit) ?
Le MRTK est un fantastique kit d’outils open source qui existe depuis le lancement d’HoloLens. Il ne serait pas ce qu’il est aujourd’hui sans le dur travail réalisé par notre communauté de développeurs qui y ont apporté leur contribution. Au cours des trois dernières années, nous avons écouté les commentaires de notre communauté de développeurs et nous avons créé MRTK v2 afin de prendre en compte les problèmes majeurs qui nous ont été remontés.  

MRTK pour Unity est un kit de développement multiplateforme open source pour les applications de réalité mixte. MRTK fournit un système d’entrée multiplateforme, des composants fondamentaux, ainsi que des modules communs pour les interactions spatiales. MRTK version 2 vise à accélérer le développement des applications qui ciblent Microsoft HoloLens, les casques immersifs Windows Mixed Reality (VR) et la plateforme OpenVR. Le projet a pour but de réduire le nombre d’obstacles qui gênent la création d’applications de réalité mixte et d’apporter une contribution à la Communauté de la réalité mixte.

<br>

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Setting-up-your-HoloLens-2-development-environment/player?format=ny]

Pour plus d’informations, consultez la [documentation MRTK sur GitHub](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html). Pour commencer, suivez les étapes de la page [Guide d’installation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html).


## <a name="new-with-mrtk-v2"></a>Nouveautés de MRTK v2
Nous souhaitons souligner notre engagement envers ces outils de plateforme.  En fait, nous avons optimisé MRTK version 2 pour développer nos expériences intégrées, comme l’expérience d’installation OOBE et notre application Mixed Reality Tips. Vous verrez également de nouvelles fonctionnalités d’HoloLens 2 exposées pour la première fois par le biais du MRTK, car selon nous, il s’agit de la meilleure méthode pour développer sur notre plateforme. 

### <a name="modular"></a>Modularité
Nous avons conçu ce kit d’une façon modulaire. Vous n’aurez donc pas besoin d’utiliser tous les composants de ce kit dans votre projet.  Cela présente plusieurs avantages.  Votre projet conserve une taille limitée et est plus facile à gérer.  De plus, comme le kit est conçu avec des objets scriptables et qu’il est basé sur une interface, vous pouvez remplacer ses composants par les vôtres, ce qui rend possible la prise en charge d’autres services, systèmes et plateformes.

### <a name="cross-platform"></a>Système multiplateforme
Justement, à propos des autres plateformes, le kit fournit une prise en charge multiplateforme.  Cela ne signifie pas pour autant que toutes les plateformes sont entièrement prises en charge, mais nous avons fait en sorte que tout le code existant dans le kit d’outils continue de s’exécuter correctement lorsque vous basculez votre cible de build vers d’autres plateformes.  La robustesse et l’extensibilité de la conception modulaire du kit faciliteront la prise en charge de multiples plateformes, parmi lesquelles ARCore, ARKit et OpenVR.

### <a name="performant"></a>Performance
Nous avons conçu le kit d’outils dans un souci de vous offrir des performances optimales sur les plateformes mobiles.  C’est un point très important, notre but étant que les outils vous facilitent la tâche, et pas qu’ils vous la compliquent.

## <a name="see-also"></a>Voir aussi
* [Installer les outils](../install-the-tools.md)
* [MRTK - Guide d’installation (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [Page d’accueil de la documentation MRTK (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [Portage de HoloToolkit/MRTK vers MRTK version 2 (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
