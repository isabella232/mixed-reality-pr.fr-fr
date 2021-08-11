---
title: Yeux et mains
description: Comment utiliser le ciblage oculaire comme pointeur principal en combinaison avec les mouvements de main dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, EyeTracking,
ms.openlocfilehash: 37411eb344b4efae03a00bb06a31ce56182cc724d96b2cdcc008f10a66d56011
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224754"
---
# <a name="eyes-and-hands"></a>Yeux et mains

## <a name="how-to-support-_look--hand-motions_-eye-gaze--hand-gestures"></a>Prise en charge des mouvements de la & _main_ et des mouvements

Cette page explique comment utiliser le ciblage oculaire comme pointeur principal en combinaison avec les mouvements de main.
Dans nos [démonstrations de suivi oculaire MRTK](../../example-scenes/eye-tracking-examples-overview.md), nous décrivons plusieurs exemples d’utilisation des yeux et des mains, par exemple :

- [Sélection](eye-tracking-target-selection.md): en regardant le bouton holographique distant et en effectuant simplement un geste de pincement pour le sélectionner rapidement.
- **Positionnement (cet article)**: pour déplacer de façon Fluent un hologramme sur votre scène, il vous suffit de le regarder, en pinceant le doigt et le pouce de votre index pour le saisir et le déplacer à l’aide de votre main.
- [Navigation](eye-tracking-navigation.md): il vous suffit de regarder l’emplacement dans lequel vous souhaitez effectuer un zoom, de pincer le doigt et le pouce _de votre index et de_ vous faire avancer pour effectuer un zoom avant.

Notez que MRTK est actuellement conçu de manière à ce que les rayons de distance agissent comme les pointeurs de focus prioritaires.
Cela signifie que l’en-tête et les pointeurs pointent vers l’œil seront automatiquement supprimés une fois qu’une main sera détectée et redevient visible après avoir dit « Select ».
Toutefois, cela peut ne pas être la manière dont vous aimeriez interagir à distance et privilégier une simple interaction « point de vue _et validation »_ indépendante de la présence de mains dans votre affichage.

### <a name="how-to-disable-the-hand-ray"></a>Comment désactiver le rayon de la main

Pour désactiver le pointeur de rayon, supprimez simplement le _« DefaultControllerPointer »_ dans le paramètre de configuration MRTK du _pointeur d' > d’entrée_ .
Pour utiliser les yeux et les mains comme décrit ci-dessus dans votre application, assurez-vous également que vous respectez toutes les [conditions requises pour l’utilisation du suivi oculaire](eye-tracking-basic-setup.md).

![Comment supprimer le rayon de la main](../../images/eye-tracking/mrtk_setup_removehandray.jpg)

Vous pouvez également consulter, comment le profil d’entrée _EyeTrackingDemoPointerProfile_ de l’exemple de package de suivi oculaire est configuré en tant que référence.

### <a name="how-to-keep-gaze-pointer-always-on"></a>Comment garder le pointeur de point de regard sur Always on

Pour éviter de supprimer automatiquement les pointeurs pointus vers l’en-tête ou l’œil, une fois qu’une main est détectée, [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) vous pouvez spécifier le point de regard pour déterminer s’il doit être activé ou désactivé.

```c#
// Turn on gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOn);
```

Consultez [`Controllers Pointers and Focus`](../../../architecture/controllers-pointers-and-focus.md)

---
[Retour à « suivi oculaire dans le MixedRealityToolkit »](eye-tracking-main.md)
