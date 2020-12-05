---
title: UMG et clavier dans Unreal
description: Découvrez comment utiliser des graphiques de mouvement inréalistes pour créer un système d’interface utilisateur en dehors des widgets.
author: hferrone
ms.author: suwu
ms.date: 11/25/2020
ms.topic: article
keywords: Windows Mixed Reality, hologrammes, HoloLens 2, suivi des yeux, entrée de regard, affichage monté en tête, moteur non réel, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle, widgets, UI, UMG, graphiques de mouvement inréel, moteur inréel, UE, UE4
ms.openlocfilehash: 59ad108a0e27298256f4f0d1661381a4f1748777
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609760"
---
# <a name="umg-and-keyboard-in-unreal"></a>UMG et clavier dans Unreal

Les graphiques de mouvement inréel (UMG) sont des systèmes d’interface utilisateur intégrés au moteur, qui permettent de créer des interfaces telles que des menus et des zones de texte. Les interfaces utilisateur créées avec UMG consistent en des widgets. Nous allons vous guider tout au long de la création d’un widget, de son ajout à l’espace universel et de l’activation de l’interaction à l’aide du clavier système à titre d’exemple. Pour plus d’informations sur UMG, consultez la [documentation](https://docs.unrealengine.com/en-US/Engine/UMG/index.html)officielle sur le moteur. 

## <a name="create-a-new-widget"></a>Créer un widget

- Créez un modèle de widget pour disposer l’interface utilisateur du jeu :

![Capture d’écran de l’ajout d’un modèle de widget à partir du menu non réel](images/unreal-umg-img-01.png)

- Ouvrez le nouveau plan et ajoutez des composants de la palette au canevas.  Dans ce cas, nous avons ajouté deux composants de zone de texte à partir de la section « entrée » :

![Capture d’écran de la fenêtre de hiérarchie avec le composant widget de texte mis en surbrillance et développé](images/unreal-umg-img-02.png)

- Sélectionnez un widget dans la fenêtre hiérarchie ou concepteur et modifiez les paramètres dans le panneau détails.  Dans ce cas, nous avons ajouté un « texte d’indication » par défaut et une couleur de teinte qui s’affiche lorsque vous pointez sur la zone de texte.  Une zone de texte affiche un clavier virtuel sur HoloLens lorsqu’il est interagi avec :

![Capture d’écran des paramètres modifiés dans la fenêtre hiérarchie](images/unreal-umg-img-03.png)

- Les événements peuvent également être abonnés à dans le volet d’informations :

![Capture d’écran des événements dans le volet d’informations](images/unreal-umg-img-04.png)

## <a name="add-a-widget-to-world-space"></a>Ajouter un widget à l’espace universel

- Créez un acteur, ajoutez un composant widget et ajoutez l’acteur à la scène :

![Capture d’écran d’un acteur avec un widget attaché](images/unreal-umg-img-05.png)

- Dans le volet d’informations du widget, définissez la **classe widget** sur le modèle de widget créé précédemment :

![Capture d’écran du panneau Détails du plan avec la classe de widget définie](images/unreal-umg-img-06.png)

- Dans le cas d’un widget de texte, assurez-vous que l' **entrée de matériel Receive** est désactivée. nous mettons donc à jour uniquement son texte à partir du clavier virtuel :

![Capture d’écran de la section d’interaction avec l’entrée de matériel Receive désactivée](images/unreal-umg-img-07.png)

## <a name="widget-interaction"></a>Interaction du widget

Les widgets UMG reçoivent généralement une entrée à partir d’une souris.  Sur HoloLens ou VR, nous devons simuler une souris avec un composant d’interaction de widget pour obtenir les mêmes événements.

- Créez un acteur, ajoutez un composant d' **interaction du widget** et ajoutez l’acteur à votre scène :

![Capture d’écran d’un nouvel acteur avec un composant d’interaction de widget mis en surbrillance](images/unreal-umg-img-08.png)

- Dans le volet d’informations du composant interaction du widget :
    - Définissez la distance d’interaction sur la valeur de distance souhaitée
    - Définir la **source d’interaction** sur **personnalisé**
    - Pour le développement, définissez **Show Debug** sur **true**:

![Capture d’écran des propriétés du composant d’interaction et de débogage du widget](images/unreal-umg-img-09.png)

La valeur par défaut de la source d’interaction est « World », qui doit envoyer des raycasts en fonction de la position universelle du composant d’interaction du widget. Dans AR et VR, ce n’est pas le cas.  L’activation de l’option « Afficher le débogage » et l’ajout d’une teinte de survol aux widgets sont importantes pour vérifier que le composant interaction des widgets fait ce que vous attendez.  La solution consiste à utiliser une source personnalisée et à définir raycast dans le graphique d’événements à partir de la main Ray.  

Ici, nous appelons ce code à partir de l’événement :

![Plan du cycle des événements](images/unreal-umg-img-10.png)

Ajoutez ensuite des événements de pointeur de souris virtuelle au composant d’interaction du widget en réagissant à l’entrée HoloLens.  Dans ce cas, envoyez un événement d’enfoncement de la souris lorsque la main est prélevée et un événement de libération de la souris gauche lorsqu’il n’est pas saisi :

![Plan avec ajout d’événements de pointeur de souris virtuelle](images/unreal-umg-img-13.png)

Désormais, lorsque vous déployez l’application sur HoloLens 2, vous verrez un rayon de main qui s’étend de votre main droite. Si vous le dirigez vers l’une des zones de texte modifiables et appuyez sur air, le clavier système s’affiche devant vous et vous permet d’entrer du texte. 
 
> [!NOTE]
> Le clavier du système HoloLens requiert un moteur inréel 4,26 ou ultérieur. En outre, le clavier n’apparaît pas quand votre application est en train d’être diffusée à partir de l’éditeur non réel sur le casque, uniquement lorsque l’application s’exécute sur l’appareil.

## <a name="see-also"></a>Voir aussi :
* [Documentation UMG de la non-réalisation](https://docs.unrealengine.com/Engine/UMG/index.html)
* [Didacticiels UMG inréel](https://docs.unrealengine.com/Programming/Tutorials/UMG/index.html)
