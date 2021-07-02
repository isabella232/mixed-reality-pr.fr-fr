---
title: Curseurs
description: Vue d’ensemble des curseurs MRTK
author: RogPodge
ms.author: roliu
ms.date: 06/18/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, curseurs,
ms.openlocfilehash: c8a2b6c377762918bfff79008ab34d3dfe4e20bb
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177505"
---
# <a name="sliders"></a>Curseurs

![Exemple de curseur](../images/slider/MRTK_UX_Slider_Main.jpg)

Les curseurs sont des composants d’interface utilisateur qui vous permettent de modifier continuellement une valeur en déplaçant un curseur sur une piste. Actuellement, le curseur de pincement peut être déplacé en saisissant directement le curseur, soit directement, soit à distance. Les curseurs fonctionnent sur AR et VR, à l’aide des contrôleurs de mouvement, des mains ou du geste + voix.

## <a name="example-scene"></a>Exemple de scène

Vous trouverez des exemples dans la scène **SliderExample** sous `MRTK/Examples/Demos/UX/Slider/Scenes/` .

## <a name="how-to-use-sliders"></a>Comment utiliser des curseurs

Glissez-déplacez le Prefab **PinchSlider** dans la hiérarchie de la scène. Si vous souhaitez modifier ou créer votre propre curseur, n’oubliez pas d’effectuer les opérations suivantes :

- Assurez-vous que votre objet Thumb comporte un conflit. Dans le Prefab PinchSlider, le conflit est activé `SliderThumb/Button_AnimationContainer/Slider_Button`
- Assurez-vous que l’objet contenant l’élément de conflit comporte également un composant à proximité d’une interaction proche, si vous souhaitez être en mesure de saisir le curseur à proximité.

Nous vous recommandons également d’utiliser la hiérarchie suivante :

- PinchSlider-contient sliderComponent
  - TouchCollider-conflit contenant l’intégralité de la zone sélectionnable du curseur. Active le comportement de l’alignement sur la position.
  - SliderThumb : contient le curseur amovible
  - TrackVisuals-contenant la piste et tous les autres éléments visuels
  - OtherVisuals-contenant tout autre visuel

## <a name="slider-events"></a>Événements Slider

Les curseurs exposent les événements suivants :

- OnValueUpdated-appelée chaque fois que la valeur du curseur change
- OnInteractionStarted : appelé lorsque l’utilisateur récupère le curseur
- OnInteractionEnded : appelé lorsque l’utilisateur relâche le curseur
- OnHoverEntered : appelée lorsque la main/le contrôleur de l’utilisateur pointe sur le curseur, à l’aide d’une interaction proche ou éloignée.
- OnHoverExited : appelée lorsque la main/le contrôleur de l’utilisateur n’est plus près du curseur.

## <a name="configuring-slider-bound-and-axis"></a>Configuration du curseur lié et axe

Vous pouvez déplacer directement les points de début et de fin du curseur en déplaçant les poignées dans la scène :

![Configuration des curseurs](../images/sliders/MRTK_Sliders_Setup.png)

Vous pouvez également spécifier l’axe (dans l’espace local) du curseur à l’aide du champ de l' _axe du curseur_ .

Si vous ne pouvez pas utiliser les descripteurs, vous pouvez spécifier à la place les points de début et de fin du curseur à l’aide des champs _distance de début du curseur_ et distance de fin du _curseur_ . Celles-ci spécifient la position de début/fin du curseur sous la forme d’une distance par rapport au centre du curseur, en coordonnées locales. Cela signifie qu’une fois que vous avez défini les distances de début et de fin du curseur comme vous le souhaitez, vous pouvez mettre le curseur à l’échelle de façon à ce qu’il soit plus petit ou plus grand sans avoir besoin de mettre à jour les distances de début et de fin.

## <a name="inspector-properties"></a>Propriétés de l’inspecteur

**Racine Thumb** Gameobject qui contient le curseur de curseur.

**Aligner sur la position** Indique si ce curseur s’aligne à la position désignée sur le curseur

**Est touchable** Indique si ce curseur est contrôlable via des événements tactiles

**Conflit Thumb** Conflit qui contrôle le curseur de curseur

**Touchable** Zone du curseur qui peut être touchée ou sélectionnée quand l’option accrocher à la position a la valeur true.

**Valeur du curseur** Valeur du curseur.

**Utiliser les divisions** de l’étape de curseur Contrôle si ce curseur est incrémenté en étapes ou en continu.

**Étapes de curseur des divisions** Nombre de sous-divisions où le curseur est divisé quand l’option utiliser le curseur est désactivée.

**Suivre** les éléments visuels Gameobject qui contient les éléments visuels de piste souhaités qui se trouvent le long du curseur.

**Graduations** Gameobject qui contient les graduations souhaitées qui se déplacent sur le curseur.

Éléments **visuels Thumb** Gameobject qui contient le visuel Thumb souhaité qui se déplace le long du curseur.

**Axe du curseur** Axe sur lequel se déplace le curseur.

**Distance de début du curseur** Où la piste du curseur démarre, par rapport à la distance entre le centre et l’axe du curseur, dans les unités d’espace locales.

**Distance de fin du curseur** Où la piste du curseur se termine, en tant que distance par rapport au centre sur l’axe du curseur, dans les unités d’espace locales.

Quand l’utilisateur met à jour la valeur de l’axe du curseur dans l’éditeur, alors si les éléments visuels de suivi ou les éléments visuels de suivi sont spécifiés, leur transformation est mise à jour.
Plus précisément, leur position locale est réinitialisée et leur rotation locale est définie pour correspondre à l’orientation de l’axe du curseur.
Leur échelle n’est pas modifiée.
Si les graduations comportent un composant de collection d’objets grille, les éléments layout et CellWidth ou CellHeight sont mis à jour en conséquence pour correspondre à l’axe du curseur.

## <a name="example-slider-configurations"></a>Exemples de configurations de curseur

Curseurs continus avec les ![ curseurs continus de position de magnétisme](https://user-images.githubusercontent.com/39840334/122488212-d410a400-cf91-11eb-8d31-fc7584ddc465.gif)

Curseurs d’étape avec alignement sur la position

![Curseurs d’étape](https://user-images.githubusercontent.com/39840334/122488226-dc68df00-cf91-11eb-9459-89655bbb054d.gif)

Curseurs tactiles

![Curseurs tactiles](https://user-images.githubusercontent.com/39840334/122488221-d8d55800-cf91-11eb-91a1-bb12debe2797.gif)
