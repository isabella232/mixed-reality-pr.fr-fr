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
# <a name="hand-joint-chaser-example"></a><span data-ttu-id="c560d-104">Exemple de conjonction de handles</span><span class="sxs-lookup"><span data-stu-id="c560d-104">Hand joint chaser example</span></span>

<span data-ttu-id="c560d-105">![Les appaireurs ](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) de jointures, cet exemple de scène montre comment utiliser le solveur pour attacher des objets aux jointures de la main.</span><span class="sxs-lookup"><span data-stu-id="c560d-105">![Hand joint chasers](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) This example scene demonstrates how to use Solver to attach objects to the hand joints.</span></span>

## <a name="example-scene"></a><span data-ttu-id="c560d-106">Exemple de scène</span><span class="sxs-lookup"><span data-stu-id="c560d-106">Example scene</span></span>

<span data-ttu-id="c560d-107">Vous pouvez trouver l’exemple de scène **HandJointChaserExample** Scene dans le `Assets/MRTK/Examples` dossier sous `Demos/Input/Scenes/` .</span><span class="sxs-lookup"><span data-stu-id="c560d-107">You can find the example scene **HandJointChaserExample** scene in the `Assets/MRTK/Examples` folder under `Demos/Input/Scenes/`.</span></span>

## <a name="solver-handler"></a><span data-ttu-id="c560d-108">Gestionnaire du solveur</span><span class="sxs-lookup"><span data-stu-id="c560d-108">Solver handler</span></span>

<span data-ttu-id="c560d-109">Cliquez sur **objet suivi pour référencer** , puis sélectionnez **la droite** **jointe à gauche** ou à droite.</span><span class="sxs-lookup"><span data-stu-id="c560d-109">Click **Tracked Object To Reference** and select **Hand Joint Left** or **Hand Joint Right**.</span></span> <span data-ttu-id="c560d-110">Vous serez en mesure d’afficher la liste déroulante **conjointe** .</span><span class="sxs-lookup"><span data-stu-id="c560d-110">You will be able to see **Tracked Hand Joint** drop down.</span></span> <span data-ttu-id="c560d-111">Dans la liste déroulante, vous pouvez sélectionner une jointure spécifique à suivre. Cet exemple de scène utilise le solveur de vue radiale pour rendre un objet conforme à l’objet cible.</span><span class="sxs-lookup"><span data-stu-id="c560d-111">From the drop down list, you can select specific joint to track. This example scene uses Radial View Solver to make an object follow the target object.</span></span> <span data-ttu-id="c560d-112">Pour plus d’informations, consultez la page du [Solveur](../ux-building-blocks/solvers/solver.md) .</span><span class="sxs-lookup"><span data-stu-id="c560d-112">See [Solver](../ux-building-blocks/solvers/solver.md) page for more details.</span></span>

![Solveur joint à la main](../images/hand-joint-chaser/MRTK_Solver_HandJoint.jpg)
