---
title: La création de l’échappement de kippy
description: nous nous contenterons de suivre la création de l’application de réalité mixte d’échappement de Kippy pour HoloLens 2 dans le moteur.
author: sw5813
ms.author: suwu
ms.date: 9/4/2020
ms.topic: article
keywords: le moteur UE4, le HoloLens, le HoloLens 2, la réalité mixte, le déploiement sur l’appareil, le PC, la documentation, le casque de la réalité mixte, le casque de réalité windows, le casque de la réalité virtuelle
appliesto:
- HoloLens 2
ms.openlocfilehash: 353df2f2f5bc9a1d70fc354fd3014f10c0ba95d9
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757110"
---
# <a name="the-making-of-kippys-escape"></a>La création de l’échappement de kippy
![Image de héros d’échappement de kippy](images/KippysEscape_1920.jpg)

Kippy le robot se réveille pour se retrouver sur un îlot. C’est à vous de faire en sorte que votre chapeau de résolution des problèmes permette de trouver un chemin d’accès à son fusée. connectez-vous à votre HoloLens 2 et [téléchargez l’application](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) à partir de la Microsoft Store ou clonez le [référentiel](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) à partir de GitHub et Kippy-main !  

> [!IMPORTANT]
> assurez-vous que vous utilisez un **moteur 4,25 ou ultérieur** , si vous générez l’échappement de Kippy à partir du référentiel GitHub.

la séquence d’échappement de Kippy est un exemple d’application open source [HoloLens 2](/hololens/hololens2-hardware) générée avec des outils inréalistes de moteur 4 et [d’expérience utilisateur mixte de réalité](https://github.com/microsoft/MixedReality-UXTools-Unreal). Dans ce billet, nous allons vous guider tout au long de notre processus, de la conception visuelle à la mise en œuvre et à l’optimisation de l’expérience. Vous trouverez plus d’informations sur le développement d’applications de réalité mixte avec les outils MRTK UX dans la [vue d’ensemble du développement inréel](unreal-development-overview.md).

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>téléchargez l’application à partir de Microsoft Store dans HoloLens 2
si vous avez HoloLens 2 appareil, vous pouvez télécharger et installer directement l’application sur votre appareil.

<a href='//www.microsoft.com/store/apps/9nbd7gl86vkd?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>


## <a name="first-principles"></a>Premiers principes 

dans le cadre du paramétrage de la création d’une séquence d’échappement de Kippy, notre objectif était de créer une expérience qui met en évidence la [prise en charge du HoloLens 2 du moteur](https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html), les fonctionnalités de HoloLens 2 et la réalité mixte Shared Computer Toolkit. Nous souhaitions inspirer les développeurs à imaginer ce qu’ils pouvaient créer avec des HoloLens 2 et inréels.  

Nous avons obtenu trois principes directeurs pour l’expérience : ils devaient être amusants, interactifs et ont une barrière faible à l’entrée. Nous souhaitons que l’expérience soit suffisamment intuitive, même si un utilisateur de la réalité mixte n’a pas besoin d’un didacticiel pour y accéder.  

## <a name="designing-the-game"></a>Conception du jeu 

la HoloLens 2 a accès à des fonctionnalités de conception qui ne se trouvent nulle part ailleurs dans le jeu. Les objets peuvent être directement poussés ou manipulés à l’aide de vos mains ou avec le suivi oculaire. Ces fonctionnalités clés se trouvent derrière les moments amusants que nous avons intégrés à l’échappement de kippy.  

en utilisant les fonctionnalités de HoloLens 2 uniques en guise d’aide pour notre conception de jeu, nous avons limité quelques scénarios d’environnement. Les îlots ont un sens, car ils peuvent être ajustés en fonction des différentes hauteurs de joueurs et fournir des idées de pont divertissantes. Nous sommes parvenus sur le thème de l’ancien civilisation, qui répond à la technologie Sci-Fi, avec l’idée que quelqu’un avait créé des machines sur Ruins en exploitant une énergie étrange fournie par chaque île. Les îles ont chacune leur propre apparence, un détail qui nous a aidé à créer un intérêt visuel. Un bon équilibre entre la modélisation et la texturation permet de réduire les appels de dessin pour les performances de rendu, donc un look stylisé a été conçu en tenant compte de cela à l’esprit. 

![La conception de jeux précoces ébauche ](images/kippys-escape/kippys-escape-img-01.png)
 *des croquis précoces pour ce que l’expérience peut ressembler*

![Rendu des rendus des deuxièmes îlots ](images/kippys-escape/kippys-escape-img-02.png)
 *du second îlot*

Pour rester dans le cadre de notre planification de production, nous avons convenu qu’un caractère flottant pouvait capturer l’intention et l’émotion sans cycles d’animation rigoureux. Et kippy est né ! Il emotes quelques expressions différentes par le biais de ses yeux et de ses effets de son vocal minimal pour guider le joueur tout au long de l’expérience. 

![Kippy présentant différentes expressions par le biais de ses yeux](images/kippys-escape/kippys-escape-img-03.gif)

*Kippy présentant différentes expressions par le biais de ses yeux*

![Si l’utilisateur met trop de temps à résoudre un puzzle, kippy donne une indication à l’utilisateur](images/kippys-escape/kippys-escape-img-04.gif)

*Si l’utilisateur met trop de temps à résoudre un puzzle, kippy donne une indication à l’utilisateur*

Au-delà de la conception de caractères et d’environnements, nous avons fait un effort concerté pour que le jeu se sent amusant. Le suivi oculaire nous permettait de déclencher des attributs de matériau et de son, ce qui a mis en surbrillance les éléments clés du jeu. L’audio spatial a aidé les niveaux à la racine de l’environnement du joueur. La possibilité de récupérer des objets, des boutons de commande et de manipuler des curseurs permet d’effectuer des missions de joueurs innovantes. Il était important de s’assurer que ces points de connexion sont naturels. 

![La fin du câble de pont s’illumine lorsque l’utilisateur l’approche à la main](images/kippys-escape/kippys-escape-img-05.gif)

*La fin du câble de pont s’illumine lorsque l’utilisateur l’approche à la main*

## <a name="building-the-game-mechanics"></a>Création de la mécanique du jeu 

L’échappement de kippy s’appuie fortement sur les composants d’outils d’expérience de réalité mixte pour rendre le jeu interactif, à savoir les acteurs d’interaction main, les contrôles de limites, les manipulateurs, les curseurs et les boutons.   

L' [acteur d’interaction manuelle](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/HandInteraction.html) permet une manipulation directe et éloignée des hologrammes. Au début de l’échappement de kippy, l’utilisateur a la possibilité de définir l’emplacement du jeu. Les poutres de main qui s’étendent à partir du Palm de l’utilisateur facilitent la manipulation d’hologrammes volumineux éloignés, comme illustré dans le GIF ci-dessous.  

![GIF d’acteur d’interaction de la main](images/kippys-escape/kippys-escape-img-06.gif)

La scène d’espace réservé peut être glissée et pivotée à l’aide du composant de [contrôle des limites](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/BoundsControl.html) des outils UX.  

Sur le second îlot, l’utilisateur doit sélectionner des gemmes et les placer dans leurs emplacements correspondants. Les gemmes sont associées à des [manipulateurs](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Manipulator.html) qui permettent à l’utilisateur de les sélectionner et de les placer. 

![Exemple de fichier GIF de manipulateur](images/kippys-escape/kippys-escape-img-07.gif)

Un [bouton enfoncé](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PressableButton.html) est la clé de l’utilisation de bombes pour le troisième îlot.  

![Image GIF de l’exemple de bouton enfoncé](images/kippys-escape/kippys-escape-img-08.gif)

Un composant [Slider](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PinchSlider.html) apparaît sur le quatrième îlot, déclenchant ainsi le déclenchement du dernier pont.  

![Image GIF de l’exemple de composant Slider](images/kippys-escape/kippys-escape-img-09.gif) 

## <a name="optimizing-for-hololens-2"></a>Optimisation pour HoloLens 2 

Avec une expérience conçue pour s’exécuter sur un appareil mobile, il est essentiel de garder un œil sur les performances. Unreal 4,25 comprend une mise à jour majeure de la prise en charge de la fonctionnalité multi-View mobile, ce qui réduit considérablement la charge de rendu et augmente la fréquence des trames. nous vous recommandons de consulter nos autres [paramètres de performances recommandés](performance-recommendations-for-unreal.md) pour le développement de HoloLens 2 avec unréaliste lorsque vous optimisez.  

Les objets physiques restent toujours coûteux pour les performances. par conséquent, deux solutions de contournement astucieuses ont été utilisées. Par exemple, le troisième « pont » exige que certains débris bloquent l’escalier. Au lieu d’avoir un impact sur les pions en tant qu’objets physiques, la détonation de bombe déclenche un échange, en basculant les pierres statiques pour un effet de particule éclatée. 

![exemple optimisé pour HoloLens 2 gif](images/kippys-escape/kippys-escape-img-10.gif) 

Nous avons également réduit les appels de dessin de plus de 400 à ~ 260 par : 
* Réduction de la complexité du maillage
* Combinaison de maillages
* Suppression de certains de nos éléments d’éclairage dynamique initiaux

Bien qu’il y ait probablement plus de résultats, nous avons pensé qu’il s’agissait d’un bon équilibre entre les performances et la qualité visuelle.  

## <a name="try-it-out"></a>Essayez ! 

démarrez votre HoloLens 2 et [téléchargez](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) l’application à partir de la Microsoft Store ou clonez le [référentiel](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) à partir de GitHub et générez l’application vous-même !  

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

Merci à nos amis sur [Framestore](https://www.framestore.com/) pour nous aider à donner à l’échappement de kippy. Du développement de caractères à la conception de ressources, à la programmation de jeux, leur collaboration sur ce projet était Pivotal.