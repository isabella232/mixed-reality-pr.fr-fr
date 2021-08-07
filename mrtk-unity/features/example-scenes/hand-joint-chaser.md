---
title: Suivi des articulations des mains
description: Le Chaser joint à la main dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 376dcd0e1ff01d6e9020aedf35ed2bb2b7b39fa8a119d125aa8c3a96bf0024fe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189559"
---
# <a name="hand-joint-chaser"></a>Suivi des articulations des mains

![Les appaireurs ](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) de jointures, cet exemple de scène montre comment utiliser le solveur pour attacher des objets aux jointures de la main.

## <a name="example-scene"></a>Exemple de scène

Vous pouvez trouver l’exemple de scène **HandJointChaserExample** Scene dans le `Assets/MRTK/Examples` dossier sous `Demos/Input/Scenes/` .

## <a name="solver-handler"></a>Gestionnaire du solveur

Cliquez sur **objet suivi pour référencer** , puis sélectionnez **la droite** **jointe à gauche** ou à droite. Vous serez en mesure d’afficher la liste déroulante **conjointe** . Dans la liste déroulante, vous pouvez sélectionner une jointure spécifique à suivre. Cet exemple de scène utilise le solveur de vue radiale pour rendre un objet conforme à l’objet cible. Pour plus d’informations, consultez la page du [Solveur](../ux-building-blocks/solvers/solver.md) .

![Solveur joint à la main](../images/hand-joint-chaser/MRTK_Solver_HandJoint.jpg)
