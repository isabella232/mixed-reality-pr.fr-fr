---
title: Contrôleurs de reréverbérations de HP G2 inréel
description: Découvrez comment utiliser les nouveaux contrôleurs de reréverbérations de HP G2 dans OpenXR et SteamVR pour les applications de réalité mixte non réelles.
author: hferrone
ms.author: jacksonf
ms.date: 10/9/2020
ms.topic: article
keywords: Le moteur non réel, les UE4, les réverbérations, les réverbérations G2, les régressions G2, la réalité mixte, le développement, les contrôleurs de mouvement, les entrées utilisateur, les fonctionnalités, le nouveau projet, l’émulateur, la documentation, les guides, les fonctionnalités, les hologrammes, le développement de jeux, le casque de la réalité mixte, le casque de réalité
ms.openlocfilehash: 006c70208ec0eaa45447caecf39f799c4be1bfeb
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582681"
---
# <a name="hp-reverb-g2-controllers-in-unreal"></a>Contrôleurs de reréverbérations de HP G2 inréel 

## <a name="getting-started"></a>Prise en main

> [!IMPORTANT]
> Le moteur 4,26 et OpenXR ou SteamVR est requis pour accéder au plug-in du contrôleur de mouvement HP. vous devez utiliser les contrôleurs de réverbération de HP G2.

[!INCLUDE[](includes/tabs-g2-controllers-in-unreal.md)]

## <a name="porting-an-existing-openxr-app"></a>Portage d’une application OpenXR existante 

Si aucune liaison de contrôleur n’existe dans le jeu pour le contrôleur de réalité mixte HP, le runtime OpenXR essaiera de remapper les liaisons existantes au contrôleur actif.  Dans ce cas, le jeu présente des liaisons tactiles Oculus et aucune liaison de contrôleur de réalité mixte HP.

![Remappage des liaisons existantes lorsqu’il n’existe aucune liaison de contrôleur](images/reverb-g2-img-04.png)

Les événements sont toujours déclenchés, mais si le jeu doit utiliser des liaisons spécifiques au contrôleur, comme le bouton de menu droit, le profil d’interaction de la réalité mixte HP doit être utilisé.  Plusieurs liaisons de contrôleur peuvent être spécifiées par action pour mieux prendre en charge différents appareils.
   
![Utilisation de plusieurs liaisons de contrôleur](images/reverb-g2-img-05.png)

## <a name="adding-input-action-mappings"></a>Ajout de mappages d’actions d’entrée 

Définissez une nouvelle action et mappez à l’une des combinaisons de touches dans la section HP Mixed Reality Controller.

![Définition de nouvelles actions et mappages](images/reverb-g2-img-02.png)

Le contrôleur de réverbération HP G2 a également une poignée analogique, qui peut être utilisée dans les mappages d’axe avec la liaison « axe de l’axe ».  Il existe une liaison serrée distincte, qui doit être utilisée pour les mappages d’action lorsque le bouton de la poignée est entièrement enfoncé. 

![Utilisation des liaisons d’axe Press](images/reverb-g2-img-03.png)

## <a name="adding-input-events"></a>Ajout d’événements d’entrée

Cliquez avec le bouton droit sur un plan et recherchez les nouveaux noms d’action à partir du système d’entrée pour ajouter des événements pour ces actions.  Ici, le plan répond aux événements avec une chaîne d’impression déplaçant le bouton actuel et l’état de l’axe.

![Blueprint répondant aux événements et générant l’état actuel du bouton et de l’axe](images/reverb-g2-img-06.png)

### <a name="using-input"></a>Utilisation de l’entrée 

[!INCLUDE[](includes/tabs-g2-controller-mapping-in-unreal.md)]

## <a name="see-also"></a>Voir aussi
* [Entrée SteamVR](https://docs.unrealengine.com/Platforms/VR/SteamVR/HowTo/SteamVRInput/index.html)
* [Utilisation de SteamVR avec Windows Mixed Reality](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)
* [Appareil photo à lecteur non réel](https://docs.unrealengine.com/Programming/Tutorials/PlayerCamera/3/index.html)