---
title: Chase joint à la main
description: Le Chaser joint à la main dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 0beac2dae5aa12cf07f193dab9a6db7bc7ddf2e5
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175362"
---
# <a name="hand-joint-chaser"></a><span data-ttu-id="82a39-104">Chase joint à la main</span><span class="sxs-lookup"><span data-stu-id="82a39-104">Hand joint chaser</span></span>

<span data-ttu-id="82a39-105">![Les appaireurs ](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) de jointures, cet exemple de scène montre comment utiliser le solveur pour attacher des objets aux jointures de la main.</span><span class="sxs-lookup"><span data-stu-id="82a39-105">![Hand joint chasers](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) This example scene demonstrates how to use Solver to attach objects to the hand joints.</span></span>

## <a name="example-scene"></a><span data-ttu-id="82a39-106">Exemple de scène</span><span class="sxs-lookup"><span data-stu-id="82a39-106">Example scene</span></span>

<span data-ttu-id="82a39-107">Vous pouvez trouver l’exemple de scène **HandJointChaserExample** Scene dans le `Assets/MRTK/Examples` dossier sous `Demos/Input/Scenes/` .</span><span class="sxs-lookup"><span data-stu-id="82a39-107">You can find the example scene **HandJointChaserExample** scene in the `Assets/MRTK/Examples` folder under `Demos/Input/Scenes/`.</span></span>

## <a name="solver-handler"></a><span data-ttu-id="82a39-108">Gestionnaire du solveur</span><span class="sxs-lookup"><span data-stu-id="82a39-108">Solver handler</span></span>

<span data-ttu-id="82a39-109">Cliquez sur **objet suivi pour référencer** , puis sélectionnez **la droite** **jointe à gauche** ou à droite.</span><span class="sxs-lookup"><span data-stu-id="82a39-109">Click **Tracked Object To Reference** and select **Hand Joint Left** or **Hand Joint Right**.</span></span> <span data-ttu-id="82a39-110">Vous serez en mesure d’afficher la liste déroulante **conjointe** .</span><span class="sxs-lookup"><span data-stu-id="82a39-110">You will be able to see **Tracked Hand Joint** drop down.</span></span> <span data-ttu-id="82a39-111">Dans la liste déroulante, vous pouvez sélectionner une jointure spécifique à suivre. Cet exemple de scène utilise le solveur de vue radiale pour rendre un objet conforme à l’objet cible.</span><span class="sxs-lookup"><span data-stu-id="82a39-111">From the drop down list, you can select specific joint to track. This example scene uses Radial View Solver to make an object follow the target object.</span></span> <span data-ttu-id="82a39-112">Pour plus d’informations, consultez la page du [Solveur](../ux-building-blocks/solvers/solver.md) .</span><span class="sxs-lookup"><span data-stu-id="82a39-112">See [Solver](../ux-building-blocks/solvers/solver.md) page for more details.</span></span>

![Solveur joint à la main](../images/hand-joint-chaser/MRTK_Solver_HandJoint.jpg)
