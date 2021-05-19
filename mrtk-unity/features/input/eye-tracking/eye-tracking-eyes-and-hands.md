---
title: Suivi oculaire - Yeux et mains
description: Comment utiliser le ciblage oculaire comme pointeur principal en combinaison avec les mouvements de main dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, EyeTracking,
ms.openlocfilehash: c9d5f23610d821aa1e50a3217a4be736601dc14d
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143990"
---
# <a name="eyes--hand-interaction"></a><span data-ttu-id="6709a-104">Yeux + interaction main</span><span class="sxs-lookup"><span data-stu-id="6709a-104">Eyes + hand interaction</span></span>

## <a name="how-to-support-_look--hand-motions_-eye-gaze--hand-gestures"></a><span data-ttu-id="6709a-105">Prise en charge des mouvements de la & _main_ et des mouvements</span><span class="sxs-lookup"><span data-stu-id="6709a-105">How to support _look + hand motions_ (eye gaze & hand gestures)</span></span>

<span data-ttu-id="6709a-106">Cette page explique comment utiliser le ciblage oculaire comme pointeur principal en combinaison avec les mouvements de main.</span><span class="sxs-lookup"><span data-stu-id="6709a-106">This page explains how to use eye targeting as a primary pointer in combination with hand motions.</span></span>
<span data-ttu-id="6709a-107">Dans nos [démonstrations de suivi oculaire MRTK](../../example-scenes/eye-tracking-examples-overview.md), nous décrivons plusieurs exemples d’utilisation des yeux et des mains, par exemple :</span><span class="sxs-lookup"><span data-stu-id="6709a-107">In our [MRTK eye tracking demos](../../example-scenes/eye-tracking-examples-overview.md), we describe several examples for using eyes + hands, for example:</span></span>

- <span data-ttu-id="6709a-108">[Sélection](eye-tracking-target-selection.md): en regardant le bouton holographique distant et en effectuant simplement un geste de pincement pour le sélectionner rapidement.</span><span class="sxs-lookup"><span data-stu-id="6709a-108">[Selection](eye-tracking-target-selection.md): Looking at distant holographic button and simply performing a pinch gesture to quickly select it.</span></span>
- <span data-ttu-id="6709a-109">**Positionnement (cet article)**: pour déplacer de façon Fluent un hologramme sur votre scène, il vous suffit de le regarder, en pinceant le doigt et le pouce de votre index pour le saisir et le déplacer à l’aide de votre main.</span><span class="sxs-lookup"><span data-stu-id="6709a-109">**Positioning (this article)**: Fluently move a hologram across your scene by simply looking at it, pinching your index finger and thumb together to grab it and then move it around using your hand.</span></span>
- <span data-ttu-id="6709a-110">[Navigation](eye-tracking-navigation.md): il vous suffit de regarder l’emplacement dans lequel vous souhaitez effectuer un zoom, de pincer le doigt et le pouce _de votre index et de_ vous faire avancer pour effectuer un zoom avant.</span><span class="sxs-lookup"><span data-stu-id="6709a-110">[Navigation](eye-tracking-navigation.md): Simply look at a location you want to zoom in, pinch your index finger and thumb together and _pull_ your hand toward you to zoom in.</span></span>

<span data-ttu-id="6709a-111">Notez que MRTK est actuellement conçu de manière à ce que les rayons de distance agissent comme les pointeurs de focus prioritaires.</span><span class="sxs-lookup"><span data-stu-id="6709a-111">Please note that MRTK is currently designed in a way that at a distance hand rays act as the prioritized focus pointers.</span></span>
<span data-ttu-id="6709a-112">Cela signifie que l’en-tête et les pointeurs pointent vers l’œil seront automatiquement supprimés une fois qu’une main sera détectée et redevient visible après avoir dit « Select ».</span><span class="sxs-lookup"><span data-stu-id="6709a-112">This means that the head and eye gaze pointers will automatically be suppressed once a hand is detected and will become visible again after saying "Select".</span></span>
<span data-ttu-id="6709a-113">Toutefois, cela peut ne pas être la manière dont vous aimeriez interagir à distance et privilégier une simple interaction « point de vue _et validation »_ indépendante de la présence de mains dans votre affichage.</span><span class="sxs-lookup"><span data-stu-id="6709a-113">However, this may not be the way you would like to interact at a distance and rather favor a simple _'gaze and commit'_ interaction independent of the presence of hands in your view.</span></span>

### <a name="how-to-disable-the-hand-ray"></a><span data-ttu-id="6709a-114">Comment désactiver le rayon de la main</span><span class="sxs-lookup"><span data-stu-id="6709a-114">How to disable the hand ray</span></span>

<span data-ttu-id="6709a-115">Pour désactiver le pointeur de rayon, supprimez simplement le _« DefaultControllerPointer »_ dans le paramètre de configuration MRTK du _pointeur d' > d’entrée_ .</span><span class="sxs-lookup"><span data-stu-id="6709a-115">To disable the hand ray pointer, simply remove the _'DefaultControllerPointer'_ in your _Input -> Pointer_ MRTK configuration setting.</span></span>
<span data-ttu-id="6709a-116">Pour utiliser les yeux et les mains comme décrit ci-dessus dans votre application, assurez-vous également que vous respectez toutes les [conditions requises pour l’utilisation du suivi oculaire](eye-tracking-basic-setup.md).</span><span class="sxs-lookup"><span data-stu-id="6709a-116">To use eyes and hands as described above in your app, please also make sure that you meet all of the [requirements for using eye tracking](eye-tracking-basic-setup.md).</span></span>

![Comment supprimer le rayon de la main](../../images/eye-tracking/mrtk_setup_removehandray.jpg)

<span data-ttu-id="6709a-118">Vous pouvez également consulter, comment le profil d’entrée _EyeTrackingDemoPointerProfile_ de l’exemple de package de suivi oculaire est configuré en tant que référence.</span><span class="sxs-lookup"><span data-stu-id="6709a-118">You can also check out, how the input profile _EyeTrackingDemoPointerProfile_ from the eye tracking sample package is set up as a reference.</span></span>

### <a name="how-to-keep-gaze-pointer-always-on"></a><span data-ttu-id="6709a-119">Comment garder le pointeur de point de regard sur Always on</span><span class="sxs-lookup"><span data-stu-id="6709a-119">How to keep gaze pointer always on</span></span>

<span data-ttu-id="6709a-120">Pour éviter de supprimer automatiquement les pointeurs pointus vers l’en-tête ou l’œil, une fois qu’une main est détectée, [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) vous pouvez spécifier le point de regard pour déterminer s’il doit être activé ou désactivé.</span><span class="sxs-lookup"><span data-stu-id="6709a-120">To avoid having the head or eye gaze pointers automatically suppressed once a hand is detected, the gaze [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) can be specified to control whether it should be on or off.</span></span>

```c#
// Turn on gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOn);
```

<span data-ttu-id="6709a-121">Consultez [`Controllers Pointers and Focus`](../../../architecture/controllers-pointers-and-focus.md)</span><span class="sxs-lookup"><span data-stu-id="6709a-121">See [`Controllers Pointers and Focus`](../../../architecture/controllers-pointers-and-focus.md)</span></span>

---
[<span data-ttu-id="6709a-122">Retour à « suivi oculaire dans le MixedRealityToolkit »</span><span class="sxs-lookup"><span data-stu-id="6709a-122">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](eye-tracking-main.md)
