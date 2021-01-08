---
title: Pointer du regard et fixer
description: Découvrez une vue d’ensemble de l’œil et du modèle d’entrée de point d’entrée pour les applications de réalité mixte.
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: La réalité mixte, le point de présence, l’interaction, la conception, le suivi des yeux, le suivi des têtes, le casque de la réalité mixte, le casque Windows Mixed Reality, le casque de réalité virtuelle, le HoloLens, le MRTK, la réalité mixte Toolkit
ms.openlocfilehash: 2daeea996251b1220ee4753567b42117fbb2126c
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007639"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="fdcb7-104">Pointer du regard et fixer</span><span class="sxs-lookup"><span data-stu-id="fdcb7-104">Gaze and dwell</span></span>

<span data-ttu-id="fdcb7-105">Quand les mains sont occupées avec des outils et des pièces, les mouvements peuvent être fastidieux, voire impossibles.</span><span class="sxs-lookup"><span data-stu-id="fdcb7-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span>
<span data-ttu-id="fdcb7-106">Les commandes vocales peuvent également être peu fiables dans certains contextes, par exemple dans des conditions excessivement intenses.</span><span class="sxs-lookup"><span data-stu-id="fdcb7-106">Voice commands may also be unreliable in certain contexts, for example under excessively loud conditions.</span></span>
<span data-ttu-id="fdcb7-107">Le point de regard et le point de vue offre un mécanisme familier et facile à maîtriser pour le fonctionnement des têtes et des mains libres sur HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fdcb7-107">Gaze and dwell offers a familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span>
<span data-ttu-id="fdcb7-108">En outre, le point de regard et le bruit est un excellent secours, qui est indépendant des contraintes de bruit ou de silence dans l’environnement d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="fdcb7-108">Additionally, gaze and dwell is a great fallback, which is independent of noise interference or silence constraints in the operating environment.</span></span>
<span data-ttu-id="fdcb7-109">Nous distingueons deux variantes de point de _regard_ et de [tête : le point](gaze-and-dwell-head.md) de regard et le point d’appui [.](gaze-and-dwell-eyes.md)</span><span class="sxs-lookup"><span data-stu-id="fdcb7-109">We distinguish two variants of _gaze and dwell_: [Head-gaze and dwell](gaze-and-dwell-head.md) and [Eye-gaze and dwell](gaze-and-dwell-eyes.md).</span></span>

## <a name="scenarios"></a><span data-ttu-id="fdcb7-110">Scénarios</span><span class="sxs-lookup"><span data-stu-id="fdcb7-110">Scenarios</span></span>

<span data-ttu-id="fdcb7-111">Le point d’accès est très bien utilisé dans les scénarios où les mains d’une personne sont occupées par d’autres tâches, et la voix n’est pas 100% fiable ou disponible en raison de contraintes environnementales ou sociales.</span><span class="sxs-lookup"><span data-stu-id="fdcb7-111">Gaze and dwell excels in scenarios where a person's hands are busy with other tasks, and voice isn't 100% reliable or available because of environmental or social constraints.</span></span>
<span data-ttu-id="fdcb7-112">Un bon exemple est une personne portant un appareil HoloLens pour superposer des informations de référence tout en réparant un moteur de voiture.</span><span class="sxs-lookup"><span data-stu-id="fdcb7-112">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span>
<span data-ttu-id="fdcb7-113">Ses mains sont occupées par des outils ou supportent son corps quand elle se penche dans le compartiment du moteur.</span><span class="sxs-lookup"><span data-stu-id="fdcb7-113">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span>
<span data-ttu-id="fdcb7-114">L’espace du garage est bruyant, les coups et bourdonnement constants des outils rendant difficile l’utilisation de commandes vocales.</span><span class="sxs-lookup"><span data-stu-id="fdcb7-114">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span>
<span data-ttu-id="fdcb7-115">Le point de regard permet à la personne utilisant HoloLens de parcourir en toute confiance son document de référence sans interrompre son flux de travail.</span><span class="sxs-lookup"><span data-stu-id="fdcb7-115">Gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span>

## <a name="device-support"></a><span data-ttu-id="fdcb7-116">Prise en charge des appareils</span><span class="sxs-lookup"><span data-stu-id="fdcb7-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="fdcb7-117"><strong>Modèle d’entrée</strong></span><span class="sxs-lookup"><span data-stu-id="fdcb7-117"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="fdcb7-118"><a href="../hololens-hardware-details.md"><strong>HoloLens (1ère génération)</strong></a></span><span class="sxs-lookup"><span data-stu-id="fdcb7-118"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="fdcb7-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="fdcb7-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="fdcb7-120"><a href="../discover/immersive-headset-hardware-details.md"><strong>Casques immersifs</strong></a></span><span class="sxs-lookup"><span data-stu-id="fdcb7-120"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="fdcb7-121">Suivre de la tête et stabiliser</span><span class="sxs-lookup"><span data-stu-id="fdcb7-121">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="fdcb7-122">✔️ Recommandé</span><span class="sxs-lookup"><span data-stu-id="fdcb7-122">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="fdcb7-123">✔️ Recommandé</span><span class="sxs-lookup"><span data-stu-id="fdcb7-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="fdcb7-124">✔️ Recommandé</span><span class="sxs-lookup"><span data-stu-id="fdcb7-124">✔️ Recommended</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="fdcb7-125">Pointer du regard et fixer</span><span class="sxs-lookup"><span data-stu-id="fdcb7-125">Eye-gaze and dwell</span></span></td>
        <td><span data-ttu-id="fdcb7-126">❌ Non disponible</span><span class="sxs-lookup"><span data-stu-id="fdcb7-126">❌ Not available</span></span></td>
        <td><span data-ttu-id="fdcb7-127">✔️ Recommandé</span><span class="sxs-lookup"><span data-stu-id="fdcb7-127">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="fdcb7-128">❌ Non disponible</span><span class="sxs-lookup"><span data-stu-id="fdcb7-128">❌ Not available</span></span></td>
    </tr>
</table>


<br>

---

 ## <a name="see-also"></a><span data-ttu-id="fdcb7-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fdcb7-129">See also</span></span>

* [<span data-ttu-id="fdcb7-130">Interaction basée sur le regard</span><span class="sxs-lookup"><span data-stu-id="fdcb7-130">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="fdcb7-131">Suivi oculaire sur HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="fdcb7-131">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="fdcb7-132">Pointer et valider</span><span class="sxs-lookup"><span data-stu-id="fdcb7-132">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="fdcb7-133">Mains : Manipulation directe</span><span class="sxs-lookup"><span data-stu-id="fdcb7-133">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="fdcb7-134">Mains : Mouvements</span><span class="sxs-lookup"><span data-stu-id="fdcb7-134">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="fdcb7-135">Mains : Pointer et valider</span><span class="sxs-lookup"><span data-stu-id="fdcb7-135">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="fdcb7-136">Interactions instinctuelles</span><span class="sxs-lookup"><span data-stu-id="fdcb7-136">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="fdcb7-137">Entrée vocale</span><span class="sxs-lookup"><span data-stu-id="fdcb7-137">Voice input</span></span>](voice-input.md)
