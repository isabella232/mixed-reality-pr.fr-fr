---
title: Suivi des articulations des mains
description: Le Chaser joint à la main dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: f9db1c4a2ca1959a35c541e87c9a4a01bc41637e
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144621"
---
# <a name="hand-joint-chaser-example"></a>Exemple de conjonction de handles

![Les appaireurs ](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) de jointures, cet exemple de scène montre comment utiliser le solveur pour attacher des objets aux jointures de la main.

## <a name="example-scene"></a>Exemple de scène

Vous pouvez trouver l’exemple de scène **HandJointChaserExample** Scene dans le `Assets/MRTK/Examples` dossier sous `Demos/Input/Scenes/` .

## <a name="solver-handler"></a>Gestionnaire du solveur

Cliquez sur **objet suivi pour référencer** , puis sélectionnez **la droite** **jointe à gauche** ou à droite. Vous serez en mesure d’afficher la liste déroulante **conjointe** . Dans la liste déroulante, vous pouvez sélectionner une jointure spécifique à suivre. Cet exemple de scène utilise le solveur de vue radiale pour rendre un objet conforme à l’objet cible. Pour plus d’informations, consultez la page du [Solveur](../ux-building-blocks/solvers/solver.md) .

![Solveur joint à la main](../images/hand-joint-chaser/MRTK_Solver_HandJoint.jpg)
