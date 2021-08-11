---
title: Présentation de MRTK pour Unity
description: Démarrez avec tout ce que le kit Mixed Reality Toolkit multiplateforme offre aux nouveaux développeurs de réalité mixte.
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, test, Mixed Reality Toolkit, MRTK version 2, MRTK, outils, SDK, HoloLens, HoloLens 2, casque de réalité mixte, casque windows mixed reality, casque de réalité virtuelle, multiplateforme
ms.openlocfilehash: 6d9e43a3e5ef59226dc6396de46d1295181c07f950ab9255eaf8503f973a2f43
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187643"
---
# <a name="introducing-mrtk-for-unity"></a>Présentation de MRTK pour Unity

![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>Qu’est-ce que le MRTK (Mixed Reality Toolkit) ?

Le MRTK est un fantastique kit d’outils open source qui existe depuis le lancement d’HoloLens. Il ne serait pas ce qu’il est aujourd’hui sans le dur travail réalisé par notre communauté de développeurs qui y ont apporté leur contribution. Au cours des trois dernières années, nous avons écouté les commentaires de notre communauté de développeurs et nous avons créé MRTK v2 afin de prendre en compte les problèmes majeurs qui nous ont été remontés.  

MRTK pour Unity est un kit de développement multiplateforme open source pour les applications de réalité mixte. Le moyen le plus simple d’installer la boîte à outils est d’utiliser notre nouvelle application Mixed Reality Feature Tool. Suivez nos [instructions d’installation et d’utilisation](welcome-to-mr-feature-tool.md) et sélectionnez le package **Mixed Reality Toolkit Foundation** dans la catégorie Mixed Reality Toolkit.

MRTK pour Unity fournit un système d’entrée multiplateforme, des composants fondamentaux et des modules courants pour les interactions spatiales. MRTK version 2 vise à accélérer le développement des applications qui ciblent Microsoft HoloLens, les casques immersifs Windows Mixed Reality (VR) et la plateforme OpenVR. Le projet a pour but de réduire le nombre d’obstacles qui gênent la création d’applications de réalité mixte et d’apporter une contribution à la Communauté de la réalité mixte.

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

> [!div class="nextstepaction"]
> [Essayer nos tutoriels MRTK](tutorials/mr-learning-base-01.md)

Pour plus d’informations sur les fonctionnalités, consultez la [documentation de MRTK](/windows/mixed-reality/mrtk-unity).

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
* [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md)
* [Développement avec MRTK pour Unity](unity-development-overview.md)
* [Page d’accueil Documentation MRTK](/windows/mixed-reality/mrtk-unity/)
* [Portage de HoloToolkit/MRTK sur MRTK version 2](/windows/mixed-reality/mrtk-unity/updates-deployment/htk-to-mrtk-porting-guide)
