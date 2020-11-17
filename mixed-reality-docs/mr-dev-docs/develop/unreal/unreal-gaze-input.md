---
title: Entrée en pointage en regard
description: Didacticiel sur la configuration de l’entrée de regard pour HoloLens et le moteur inréel
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, hologrammes, HoloLens 2, suivi des yeux, entrée de regard, affichage monté en tête, moteur non réel, casque de réalité mixte, casque de réalité mixte, casque de réalité virtuelle
ms.openlocfilehash: 2ea55e3c53275f6150ca7f2def10d71634119e2e
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679048"
---
# <a name="gaze-input"></a>Entrée en regard

## <a name="overview"></a>Vue d’ensemble

Le [plug-in Windows Mixed Reality](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) ne fournit pas de fonctions intégrées pour l’entrée en regard, mais HoloLens 2 prend en charge le suivi oculaire. Les fonctionnalités de suivi réelles sont fournies par les API d' **affichage** et de **suivi oculaire** non réelles et incluent :

- Informations sur l'appareil
- Capteurs de suivi
- Orientation et position
- Volets de découpage
- Données de regard et informations de suivi

Vous trouverez la liste complète des fonctionnalités dans la documentation sur l' [affichage](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) et le [suivi des yeux](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) de l’inréel.

En plus des API inréelless, consultez la documentation sur l' [interaction](../../design/eye-gaze-interaction.md) avec le regard sur les yeux pour hololens 2 et découvrez comment fonctionne le [suivi oculaire sur hololens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) .

> [!IMPORTANT]
> Le suivi oculaire est pris en charge uniquement sur HoloLens 2.

## <a name="enabling-eye-tracking"></a>Activation du suivi oculaire
L’entrée en regard doit être activée dans les paramètres du projet HoloLens avant que vous puissiez utiliser l’une des API inréelles. Lorsque l’application démarre, une invite de consentement s’affiche dans la capture d’écran ci-dessous.

- Sélectionnez **Oui** pour définir l’autorisation et accéder à l’entrée en regard. Si vous avez besoin de modifier ce paramètre à tout moment, il se trouve dans l’application **paramètres** .

![Autorisations d’entrée oculaire](images/unreal/eye-input-permissions.png)

> [!NOTE] 
> Le suivi oculaire HoloLens en non réel a un seul rayon de regard pour les yeux au lieu des deux rayons nécessaires pour le suivi STEREOSCOPIQUE, ce qui n’est pas pris en charge.

C’est tout ce dont vous avez besoin pour commencer à ajouter des entrées de regard à vos applications HoloLens 2 en toute réalité. Pour plus d’informations sur l’entrée en regard et la façon dont elle affecte les utilisateurs en réalité mixte, consultez les liens ci-dessous. Pensez à les utiliser lors de la création de vos expériences interactives.

## <a name="next-development-checkpoint"></a>Point de contrôle de développement suivant

Si vous suivez le parcours des points de contrôle de développement Unreal que nous avons mis en place, vous explorez actuellement les modules de base du MRTK. À partir de là, vous pouvez passer au module suivant : 

> [!div class="nextstepaction"]
> [Suivi de la main](unreal-hand-tracking.md)

Ou accéder aux API et fonctionnalités de la plateforme Mixed Reality :

> [!div class="nextstepaction"]
> [Caméra HoloLens](unreal-hololens-camera.md)

Vous pouvez revenir aux [points de contrôle de développement Unreal](unreal-development-overview.md#2-core-building-blocks) à tout moment.

## <a name="see-also"></a>Voir aussi
* [Étalonnage](../../calibration.md)
* [Confort](../../design/comfort.md)
* [Pointer et valider](../../design/gaze-and-commit.md)
* [Entrée vocale](../../out-of-scope/voice-design.md)
