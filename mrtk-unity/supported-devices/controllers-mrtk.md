---
title: Contrôleurs dans MRTK
description: Documentation sur l’utilisation de différents contrôleurs avec MRTK
author: RogPodge
ms.author: roliu
ms.date: 05/13/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, contrôleurs, réverbération HP, Oculus, HTC vive, mains
ms.openlocfilehash: 953b1cd56dbf7d7a548a3aba8da07ce5875fec74
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145469"
---
# <a name="controllers-in-mrtk"></a><span data-ttu-id="5978b-104">Contrôleurs dans MRTK</span><span class="sxs-lookup"><span data-stu-id="5978b-104">Controllers in MRTK</span></span>

<span data-ttu-id="5978b-105">MRTK prend en charge de nombreux contrôleurs différents.</span><span class="sxs-lookup"><span data-stu-id="5978b-105">MRTK has support for many different controllers.</span></span> <span data-ttu-id="5978b-106">De nombreux contrôleurs, tels que les baguettes de type HTC vive Knuckles et HTC vive, fonctionnent en mode natif une fois qu’une application générée avec MRTK est lancée sur l’appareil compatible.</span><span class="sxs-lookup"><span data-stu-id="5978b-106">Many controllers, such as HTC Vive Knuckles and HTC Vive Wands, will work natively once an application built with MRTK is launched on the compatible device.</span></span> <span data-ttu-id="5978b-107">D’autres contrôleurs, tels que les mains articulées sur la Oculus Quest et les contrôleurs de réverbération HP, requièrent des packages supplémentaires avant d’être reconnus par MRTK.</span><span class="sxs-lookup"><span data-stu-id="5978b-107">Other controllers, such as articulated hands on the Oculus Quest and the HP Reverb G2 Controllers, require additional packages before they are recognized by MRTK.</span></span>

<span data-ttu-id="5978b-108">Ce document décrit les scénarios courants dans lesquels des packages supplémentaires doivent être installés.</span><span class="sxs-lookup"><span data-stu-id="5978b-108">This document will describe the common scenarios where extra packages need to be installed.</span></span> <span data-ttu-id="5978b-109">Pour plus d’informations sur les contrôleurs, consultez la [**page fonctionnalités**](../features/input/controllers.md).</span><span class="sxs-lookup"><span data-stu-id="5978b-109">For additional information about controllers, visit the [**features page**](../features/input/controllers.md).</span></span> <span data-ttu-id="5978b-110">Pour déboguer les problèmes liés aux contrôleurs, consultez l' [ **outil de mappage de contrôleur** .](../features/tools/controller-mapping-tool.md)</span><span class="sxs-lookup"><span data-stu-id="5978b-110">To debug issues with controllers, see the [**Controller mapping tool**](../features/tools/controller-mapping-tool.md)</span></span>

## <a name="hp-reverb-g2-controllers"></a><span data-ttu-id="5978b-111">Contrôleurs de réverbération HP G2</span><span class="sxs-lookup"><span data-stu-id="5978b-111">HP Reverb G2 Controllers</span></span>

<span data-ttu-id="5978b-112">Pour détecter et afficher les contrôleurs de réverbération de HP G2 lors de l’utilisation de MRTK, procédez comme suit pour installer le package [**Microsoft. MixedReality. Input**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) .</span><span class="sxs-lookup"><span data-stu-id="5978b-112">To detect and show the HP Reverb G2 controllers when using MRTK, follow these steps to install the [**Microsoft.MixedReality.Input**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) package.</span></span> <span data-ttu-id="5978b-113">Une fois ce package installé, aucune autre modification des profils par défaut ne doit être apportée pour que les contrôleurs s’affichent sur la réverbération HP.</span><span class="sxs-lookup"><span data-stu-id="5978b-113">Once this package is installed, no other changes to the default profiles need to be made to have the controllers show up on the HP Reverb.</span></span> 

<span data-ttu-id="5978b-114">Pour afficher les contrôleurs dans l’éditeur, vous devez vous assurer que vous utilisez le à l’aide du [**plug-in OpenXR**](/windows/mixed-reality/develop/unity/openxr-getting-started).</span><span class="sxs-lookup"><span data-stu-id="5978b-114">In order to display the controllers in editor, you need to ensure that you are using the using the [**OpenXR Plugin**](/windows/mixed-reality/develop/unity/openxr-getting-started).</span></span>

## <a name="oculus-controllers"></a><span data-ttu-id="5978b-115">Contrôleurs Oculus</span><span class="sxs-lookup"><span data-stu-id="5978b-115">Oculus Controllers</span></span> 

<span data-ttu-id="5978b-116">Pour visualiser les modèles de contrôleur Oculus, suivez les instructions de déploiement de Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="5978b-116">To visualize Oculus controller models, follow the Oculus Quest deployment instructions.</span></span> <span data-ttu-id="5978b-117">Si vous souhaitez afficher les mains virtuelles lors de l’utilisation des contrôleurs, assurez-vous que l’option **afficher les mains de l’avatar au lieu des contrôleurs** est cochée sous le gestionnaire de périphériques Oculus SDK XR.</span><span class="sxs-lookup"><span data-stu-id="5978b-117">If you wish to show virtual hands when using the controllers, make sure that **Render Avatar Hands Instead Of Controllers** is checked under the XR SDK Oculus Device Manager.</span></span> <span data-ttu-id="5978b-118">Dans le cas contraire, décochez cette option.</span><span class="sxs-lookup"><span data-stu-id="5978b-118">Otherwise, uncheck this option.</span></span>

![OculusDeviceManagerVisualizationSettings](../images/cross-platform/oculus-quest/OculusDeviceManager.png)
