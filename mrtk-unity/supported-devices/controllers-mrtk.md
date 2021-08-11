---
title: Détection des contrôleurs dans MRTK
description: Documentation sur l’utilisation de différents contrôleurs avec MRTK
author: RogPodge
ms.author: roliu
ms.date: 05/13/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, contrôleurs HP, réverbération, Oculus, HTC Vive, mains
ms.openlocfilehash: 04afcf75fc11c1c3b4c6fb9f244172c0960e8943bd469bc6424465b376ceaf53
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226404"
---
# <a name="detecting-controllers-in-mrtk"></a>Détection des contrôleurs dans MRTK

MRTK prend en charge de nombreux contrôleurs différents. De nombreux contrôleurs, tels que les baguettes de type HTC vive Knuckles et HTC vive, fonctionnent en mode natif une fois qu’une application générée avec MRTK est lancée sur l’appareil compatible. D’autres contrôleurs, tels que les mains articulées sur la Oculus Quest et les contrôleurs de réverbération HP, requièrent des packages supplémentaires avant d’être reconnus par MRTK.

Ce document décrit les scénarios courants dans lesquels des packages supplémentaires doivent être installés. Pour obtenir des instructions sur le déploiement sur votre appareil, consultez les pages de déploiement [**Hololens/WMR**](./wmr-mrtk.md) ou [**Oculus Quest**](/windows/mixed-reality/mrtk-unity/supported-devices/oclus-quest-mrtk) . Pour plus d’informations sur les contrôleurs, consultez la [**page fonctionnalités**](../features/input/controllers.md). Pour déboguer les problèmes liés aux contrôleurs, consultez l' [ **outil de mappage de contrôleur** .](../features/tools/controller-mapping-tool.md)

## <a name="hp-reverb-g2-controllers"></a>Contrôleurs de réverbération HP G2

Pour détecter et afficher les contrôleurs de réverbération de HP G2 lors de l’utilisation de MRTK, procédez comme suit pour installer le package [**Microsoft. MixedReality. Input**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) . Une fois ce package installé, aucune autre modification des profils par défaut ne doit être apportée pour que les contrôleurs s’affichent sur la réverbération HP. 

Pour afficher les contrôleurs dans l’éditeur, vous devez vous assurer que vous utilisez le à l’aide du [**plug-in OpenXR**](/windows/mixed-reality/develop/unity/openxr-getting-started).

## <a name="oculus-controllers"></a>Contrôleurs Oculus 

Pour visualiser les modèles de contrôleur Oculus, suivez les instructions de déploiement de Oculus Quest. Si vous souhaitez afficher les mains virtuelles lors de l’utilisation des contrôleurs, assurez-vous que l’option **afficher les mains de l’avatar au lieu des contrôleurs** est cochée sous le gestionnaire de périphériques Oculus SDK XR. Dans le cas contraire, décochez cette option.

![OculusDeviceManagerVisualizationSettings](../images/cross-platform/oculus-quest/OculusDeviceManager.png)
