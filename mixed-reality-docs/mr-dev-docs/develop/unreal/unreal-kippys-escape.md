---
title: La création de l’échappement de kippy
description: Nous nous contenterons de suivre la création de l’échappement de kippy pour HoloLens 2 dans un moteur non réel.
author: sw5813
ms.author: suwu
ms.date: 9/4/2020
ms.topic: article
keywords: Non réel, moteur 4, UE4, HoloLens, HoloLens 2, réalité mixte, déployer sur un appareil, PC, documentation
appliesto:
- HoloLens 2
ms.openlocfilehash: 5c029e91bb33192b02dd32aca224a23fc4b5289d
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91679686"
---
# <a name="the-making-of-kippys-escape"></a>La création de l’échappement de kippy

Kippy le robot se réveille pour se retrouver sur un îlot. C’est à vous de faire en sorte que votre chapeau de résolution des problèmes permette de trouver un chemin d’accès à son fusée. Connectez-vous à votre HoloLens 2 et [Téléchargez l’application](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) à partir de la Microsoft Store ou clonez le [référentiel](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) à partir de GitHub et procurez-vous kippy-safe.  

> [!IMPORTANT]
> Assurez-vous que vous utilisez un **moteur 4,25 ou ultérieur** , si vous générez l’échappement de kippy à partir du référentiel github.

## <a name="overview"></a>Vue d’ensemble

La séquence d’échappement de kippy est une application de l’exemple [HoloLens 2](https://docs.microsoft.com/hololens/hololens2-hardware) Open source générée avec des outils inréalistes pour le moteur 4 et la [réalité mixte](https://github.com/microsoft/MixedReality-UXTools-Unreal). Dans ce billet, nous allons vous guider tout au long de notre processus de mise en œuvre de l’échappement de kippy, des premiers principes et de la conception visuelle à l’implémentation et à l’optimisation de l’expérience. Vous trouverez plus d’informations sur le développement d’applications de réalité mixte avec les outils MRTK UX dans la [vue d’ensemble du développement inréel](unreal-development-overview.md).

## <a name="first-principles"></a>Premiers principes 

Dans le cadre du paramétrage de la création de l’échappement de kippy, notre objectif était de créer une expérience qui mettre en évidence la [prise en charge de l’outil hololens 2 d’un moteur inréel](https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html), les fonctionnalités de hololens 2 et la boîte à outils de réalité mixte. Nous voulions inspirer les développeurs pour imaginer ce qu’ils pouvaient créer avec les fonctionnalités non réelles et HoloLens 2.  

Nous avons obtenu trois principes directeurs pour l’expérience : ils devaient être amusants, interactifs et ont une barrière faible à l’entrée. Nous souhaitons que l’expérience soit suffisamment intuitive, même si un utilisateur de la réalité mixte n’a pas besoin d’un didacticiel pour y accéder.  

## <a name="designing-the-game"></a>Conception du jeu 

Le HoloLens 2 a accès aux fonctionnalités de conception qui ne se trouvent nulle part ailleurs dans le jeu. Les objets peuvent être directement poussés ou manipulés à l’aide de vos mains ou avec le suivi oculaire. Ces fonctionnalités clés se trouvent derrière les moments amusants que nous avons intégrés à l’échappement de kippy.  

À l’aide des fonctionnalités HoloLens 2 uniques en guise d’aide pour notre conception de jeu, nous avons limité quelques scénarios d’environnement. Les îlots ont beaucoup de sens, car ils peuvent être ajustés en fonction des différentes hauteurs de joueurs et fournir des idées de pont divertissantes. À partir de là, nous sommes parvenus au thème de l’ancien civilisation, qui répond à la technologie Sci-Fi, avec l’idée que quelqu’un avait créé des machines sur Ruins en exploitant une énergie étrange fournie par chaque île. Les îles ont chacune leur propre apparence, un détail qui nous a aidé à créer un intérêt visuel. Un bon équilibre entre la modélisation et les texturages était de garder les appels de dessin faible pour les performances de rendu, donc un look stylisé a été conçu en tenant compte de cela à l’esprit. 

![La conception de jeux précoces ébauche ](images/kippys-escape/kippys-escape-img-01.png)
 *des croquis précoces pour ce que l’expérience peut ressembler*

![Rendu des rendus des deuxièmes îlots ](images/kippys-escape/kippys-escape-img-02.png)
 *du second îlot*

Pour rester dans le cadre de notre planification de production, nous avons convenu qu’un caractère flottant pouvait capturer l’intention et l’émotion sans cycles d’animation rigoureux. Et kippy est né ! Il emotes quelques expressions différentes par le biais de ses yeux et de ses effets de son vocal minimal pour guider le joueur tout au long de l’expérience. 

![Kippy présentant différentes expressions par le biais de ses yeux](images/kippys-escape/kippys-escape-img-03.gif)

*Kippy présentant différentes expressions par le biais de ses yeux*

![Si l’utilisateur met trop de temps à résoudre un puzzle, kippy donne une indication à l’utilisateur](images/kippys-escape/kippys-escape-img-04.gif)

*Si l’utilisateur met trop de temps à résoudre un puzzle, kippy donne une indication à l’utilisateur*

Au-delà de la conception de caractères et d’environnements, nous avons fait un effort concerté pour que le jeu se sent amusant. Le suivi oculaire nous permettait de déclencher des attributs de matériau et de son, ce qui a mis en surbrillance les éléments clés du jeu. L’audio spatial a aidé les niveaux à la racine de l’environnement du joueur. La possibilité de capturer des objets, de pousser des boutons et de manipuler des curseurs permet d’effectuer des missions de joueurs innovantes. il est donc important de s’assurer que ces points de connexion sont naturels. 

![La fin du câble de pont s’illumine lorsque l’utilisateur l’approche à la main](images/kippys-escape/kippys-escape-img-05.gif)

*La fin du câble de pont s’illumine lorsque l’utilisateur l’approche à la main*

## <a name="building-the-game-mechanics"></a>Création de la mécanique du jeu 

L’échappement de kippy s’appuie fortement sur les composants d’outils d’expérience de réalité mixte pour rendre le jeu interactif, à savoir les acteurs d’interaction main, les contrôles de limites, les manipulateurs, les curseurs et les boutons.   

L' [acteur d’interaction manuelle](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/HandInteraction.html) permet une manipulation directe et éloignée des hologrammes. Au début de l’échappement de kippy, l’utilisateur a la possibilité de définir l’emplacement du jeu. Les poutres de main qui s’étendent à partir du Palm de l’utilisateur facilitent la manipulation d’hologrammes volumineux éloignés, comme illustré dans le GIF ci-dessous.  

![GIF d’acteur d’interaction de la main](images/kippys-escape/kippys-escape-img-06.gif)

La scène d’espace réservé peut être glissée et pivotée à l’aide du composant de [contrôle des limites](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/BoundsControl.html) des outils UX.  

Sur le second îlot, l’utilisateur doit sélectionner des gemmes et les placer dans leurs emplacements correspondants. Les gemmes sont associées à des [manipulateurs](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/Manipulator.html) qui permettent à l’utilisateur de les sélectionner et de les placer. 

![Exemple de fichier GIF de manipulateur](images/kippys-escape/kippys-escape-img-07.gif)

Un [bouton enfoncé](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PressableButton.html) est la clé de l’utilisation de bombes pour le troisième îlot.  

![Image GIF de l’exemple de bouton enfoncé](images/kippys-escape/kippys-escape-img-08.gif)

Un composant [Slider](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PinchSlider.html) apparaît sur le quatrième îlot, déclenchant ainsi le déclenchement du dernier pont.  

![Image GIF de l’exemple de composant Slider](images/kippys-escape/kippys-escape-img-09.gif) 

## <a name="optimizing-for-hololens-2"></a>Optimisation pour HoloLens 2 

Avec une expérience conçue pour s’exécuter sur un appareil mobile, il est essentiel de garder un œil sur les performances. Unreal 4,25 comprend une mise à jour majeure de la prise en charge de la fonctionnalité multi-View mobile, ce qui réduit considérablement la charge de rendu et augmente la fréquence des trames. Nous vous recommandons de consulter nos autres [paramètres de performances recommandés](performance-recommendations-for-unreal.md) pour le développement de HoloLens 2 avec des conditions d’optimisation.  

Les objets physiques restent toujours coûteux pour les performances. par conséquent, deux solutions de contournement astucieuses ont été utilisées. Par exemple, le troisième « pont » exige que certains débris bloquent l’escalier. Au lieu d’avoir un impact sur les pions en tant qu’objets physiques, la détonation de bombe déclenche un échange, en basculant les pierres statiques pour un effet de particule éclatée. 

![Exemple optimisé pour le GIF HoloLens 2](images/kippys-escape/kippys-escape-img-10.gif) 

Nous avons également réduit les appels de dessin de plus de 400 à ~ 260 par : 
* Réduction de la complexité du maillage
* Combinaison de maillages
* Suppression de certains de nos éléments d’éclairage dynamique initiaux

Bien qu’il y ait probablement plus de résultats, nous avons pensé qu’il s’agissait d’un bon équilibre entre les performances et la qualité visuelle.  

## <a name="try-it-out"></a>Essayez ! 

Démarrez votre HoloLens 2 et [Téléchargez](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) l’application à partir de la Microsoft Store, ou clonez le [référentiel](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) à partir de GitHub et générez l’application vous-même !  

## <a name="about-the-team"></a>À propos de l’équipe

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Jack Caron" width="60" height="60" src="images/kippys-escape/jack-caron.jpg"></td>
<td style="border-style: none"><b>Jack Caron</b><br><i>Concepteur de jeux de leads</i><br>Jack travaille actuellement sur les expériences de réalité mixte pour Microsoft, y compris les projets HoloLens 2 et AltspaceVR, et était auparavant un concepteur de l’équipe de la plateforme HoloLens.</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Summer Wu" width="60" height="60" src="images/kippys-escape/summer-wu.jpg"></td>
<td style="border-style: none"><b>Wu été</b><br><i>Producer</i><br>L’été travaille sur la plateforme de développement de la réalité mixte et dirige les efforts liés au moteur inréel de l’équipe.</td>
</tr>
</table>

Merci à nos amis sur [Framestore](https://www.framestore.com/) pour nous aider à passer le kippy au niveau supérieur. Du développement de caractères à la conception de ressources, à la programmation de jeux, leur collaboration sur ce projet était Pivotal.  