---
title: Sélection de la cible de suivi oculaire
description: Comment accéder aux données de regard visuel et aux événements spécifiques du regard pour sélectionner des cibles dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, EyeTracking,
ms.openlocfilehash: 229903e01c597aefbb3fc29de8a49d79cbbd42d0
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144192"
---
# <a name="eye-supported-target-selection"></a><span data-ttu-id="d7fcc-104">Sélection de la cible prise en charge par l’œil</span><span class="sxs-lookup"><span data-stu-id="d7fcc-104">Eye-supported target selection</span></span>

![MRTK](../../images/eye-tracking/mrtk_et_targetselect.png)

<span data-ttu-id="d7fcc-106">Cette page présente les différentes options permettant d’accéder aux données de regard oculaire et aux événements spécifiques du regard pour sélectionner des cibles dans MRTK.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-106">This page discusses different options for accessing eye gaze data and eye gaze specific events to select targets in MRTK.</span></span> <span data-ttu-id="d7fcc-107">Le suivi oculaire permet des sélections de cibles rapides et sans effort à l’aide d’une combinaison d’informations sur ce qu’un utilisateur examine avec d’autres entrées, telles que le suivi de la _main_ et les _commandes vocales_:</span><span class="sxs-lookup"><span data-stu-id="d7fcc-107">Eye tracking allows for fast and effortless target selections using a combination of information about what a user is looking at with additional inputs such as _hand tracking_ and _voice commands_:</span></span>

- <span data-ttu-id="d7fcc-108">Regardez & dites _« Sélectionner »_ (commande vocale par défaut)</span><span class="sxs-lookup"><span data-stu-id="d7fcc-108">Look & Say _"Select"_ (default voice command)</span></span>
- <span data-ttu-id="d7fcc-109">Regardez & dites _« Eclater »_ ou _« pop »_ (commandes vocales personnalisées)</span><span class="sxs-lookup"><span data-stu-id="d7fcc-109">Look & Say _"Explode"_ or _"Pop"_ (custom voice commands)</span></span>
- <span data-ttu-id="d7fcc-110">Bouton regarder & Bluetooth</span><span class="sxs-lookup"><span data-stu-id="d7fcc-110">Look & Bluetooth button</span></span>
- <span data-ttu-id="d7fcc-111">Regardez & pincez-vous (par exemple, maintenez votre main à l’avant et apportez votre doigt et votre index ensemble)</span><span class="sxs-lookup"><span data-stu-id="d7fcc-111">Look & Pinch (i.e., hold up your hand in front of you and bring your thumb and index finger together)</span></span>
  - <span data-ttu-id="d7fcc-112">Notez que pour que cela fonctionne, les [rayons manuels doivent être désactivés](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray)</span><span class="sxs-lookup"><span data-stu-id="d7fcc-112">Please note that for this to work, the [hand rays need to be disabled](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray)</span></span>

<span data-ttu-id="d7fcc-113">Pour sélectionner un contenu holographique à l’aide d’un point de vue oculaire, vous avez le choix entre plusieurs options :</span><span class="sxs-lookup"><span data-stu-id="d7fcc-113">To select holographic content using eye gaze, there are several options:</span></span>

[<span data-ttu-id="d7fcc-114">**1. Utilisez le pointeur de focus principal :**</span><span class="sxs-lookup"><span data-stu-id="d7fcc-114">**1. Use the primary focus pointer:**</span></span>](#1-use-generic-focus-and-pointer-handlers)

<span data-ttu-id="d7fcc-115">Cela peut être assimilé à votre curseur par ordre de priorité.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-115">This can be understood as your prioritized cursor.</span></span>
<span data-ttu-id="d7fcc-116">Par défaut, si les mains sont en vue, il s’agit de rayons de main.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-116">By default, if the hands are in view, then this would be hand rays.</span></span>
<span data-ttu-id="d7fcc-117">Si aucun mains n’est en cours d’affichage, le pointeur de priorité est en tête ou en regard.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-117">If no hands are in view, then the prioritized pointer would be head or eye gaze.</span></span>
<span data-ttu-id="d7fcc-118">Par conséquent, veuillez noter que, en fonction de l’en-tête de conception actuel ou de l’œil, le point de regard est supprimé en tant qu’entrée de curseur si des rayons de main sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-118">Thus, please note that based on the current design head or eye gaze is suppressed as a cursor input if hand rays are used.</span></span>

<span data-ttu-id="d7fcc-119">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="d7fcc-119">For example:</span></span>

<span data-ttu-id="d7fcc-120">Un utilisateur souhaite sélectionner un bouton holographique distant.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-120">A user wants to select a distant holographic button.</span></span>
<span data-ttu-id="d7fcc-121">En tant que développeur, vous souhaitez fournir une solution flexible qui permet à l’utilisateur d’accomplir ces tâches dans diverses conditions :</span><span class="sxs-lookup"><span data-stu-id="d7fcc-121">As a developer, you want to provide a flexible solution that allows the user to achieve this tasks in various conditions:</span></span>

- <span data-ttu-id="d7fcc-122">Parcourez le bouton et surmontez-le</span><span class="sxs-lookup"><span data-stu-id="d7fcc-122">Walk up to the button and poke it</span></span>
- <span data-ttu-id="d7fcc-123">Examinez-la à partir d’une distance et dites « sélectionner »</span><span class="sxs-lookup"><span data-stu-id="d7fcc-123">Look at it from a distance and say "select"</span></span>
- <span data-ttu-id="d7fcc-124">Ciblez le bouton à l’aide d’un rayon et effectuez un pincement. dans ce cas, la solution la plus souple consiste à utiliser le gestionnaire de focus principal, car il vous avertit chaque fois que le pointeur principal actuellement prioritaire déclenche un événement.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-124">Target the button using a hand ray and performing a pinch In this case, the most flexible solution is to use the primary focus handler as it will notify you whenever the currently prioritized primary focus pointer triggers an event.</span></span> <span data-ttu-id="d7fcc-125">Notez que si les rayons de main sont activés, le pointeur du point de vue de la tête ou de l’œil est désactivé dès l’apparition des mains.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-125">Please note that if hand rays are enabled, the head or eye gaze focus pointer are disabled as soon as the hands come into view.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d7fcc-126">Notez que si les rayons de main sont activés, le pointeur du point de vue de la tête ou de l’œil est désactivé dès l’apparition des mains.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-126">Please note that if hand rays are enabled, the head or eye gaze focus pointer are disabled as soon as the hands come into view.</span></span> <span data-ttu-id="d7fcc-127">Si vous souhaitez prendre en charge une [interaction _« look et pince »_ , vous devez désactiver le rayon de la main](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray).</span><span class="sxs-lookup"><span data-stu-id="d7fcc-127">If you want to support a [_'look and pinch'_ interaction, you need to disable the hand ray](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray).</span></span> <span data-ttu-id="d7fcc-128">Dans nos exemples de suivi oculaire, nous avons désactivé le rayon de la main pour permettre la présentation des interactions plus riches à l’aide des yeux et des mouvements [manuels. pour plus d’exemples,](eye-tracking-eyes-and-hands.md)consultez la rubrique.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-128">In our eye tracking sample scenes, we have disabled the hand ray to allow for showcasing richer interactions using eyes + hand motions - see for example [Eye-Supported Positioning](eye-tracking-eyes-and-hands.md).</span></span>

[<span data-ttu-id="d7fcc-129">**2. Utilisez à la fois le focus visuel et les rayons main :**</span><span class="sxs-lookup"><span data-stu-id="d7fcc-129">**2. Use both eye focus and hand rays at the same time:**</span></span>](#2-independent-eye-gaze-specific-eyetrackingtarget)

<span data-ttu-id="d7fcc-130">Il peut y avoir des cas où vous souhaitez être plus précis que le type de pointeurs de Focus peut déclencher certains événements et permettre l’utilisation simultanée de plusieurs techniques d’interaction Far.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-130">There might be instances where you want to be more specific which type of focus pointers can trigger certain events and allow for simultaneously using multiple far interaction techniques.</span></span>

<span data-ttu-id="d7fcc-131">Par exemple : dans votre application, un utilisateur peut utiliser des rayons de loin pour manipuler des configurations mécaniques holographiques, par exemple, saisir et maintenir des éléments de moteur holographique distants et les maintenir en place.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-131">For example: In your app, a user can use far hand rays to manipulate some holographic mechanical setup - e.g., grab and hold some distant holographic engine parts and hold them in place.</span></span> <span data-ttu-id="d7fcc-132">Dans ce cas, l’utilisateur doit suivre un certain nombre d’instructions et enregistrer sa progression en marquant certaines cases à cocher.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-132">While doing so, the user has to go through a number of instructions and record her/his progress by marking off some check boxes.</span></span> <span data-ttu-id="d7fcc-133">Si l’utilisateur a ses mains _non occupées_, il serait instinctual de simplement toucher à la case à cocher ou de la sélectionner à l’aide d’un rayon de la main.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-133">If the user has her/his hands _not busy_, it would be instinctual to simply touch the check box or select it using a hand ray.</span></span> <span data-ttu-id="d7fcc-134">Toutefois, si l’utilisateur a ses mains occupées, comme dans le cas où des parties de moteur holographique sont en place, vous souhaitez permettre à l’utilisateur de faire défiler en toute transparence les instructions à l’aide de leur point de regard, et de simplement regarder une case à cocher et de « vérifier ».</span><span class="sxs-lookup"><span data-stu-id="d7fcc-134">However, if the user has her/his hands busy, as in our case holding some holographic engine parts in place, you want to enable the user to seamlessly scroll through the instructions using their eye gaze and to simply look at a check box and say "check it!".</span></span>

<span data-ttu-id="d7fcc-135">Pour ce faire, vous devez utiliser un script EyeTrackingTarget spécifique à l’oeil qui est indépendant du MRTK principal FocusHandlers et qui sera abordé plus loin ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-135">To enable this, you need to use eye-specific EyeTrackingTarget script that is independent from the core MRTK FocusHandlers and will be discussed further below.</span></span>

## <a name="1-use-generic-focus-and-pointer-handlers"></a><span data-ttu-id="d7fcc-136">1. utiliser le focus générique et les gestionnaires de pointeurs</span><span class="sxs-lookup"><span data-stu-id="d7fcc-136">1. Use generic focus and pointer handlers</span></span>

<span data-ttu-id="d7fcc-137">Si le suivi des yeux est correctement configuré (voir [le programme d’installation de base MRTK pour utiliser le suivi oculaire](eye-tracking-basic-setup.md)), permettre aux utilisateurs de sélectionner des hologrammes à l’aide de leurs yeux est le même que pour toute autre entrée de focus (par exemple, point de regard ou rayon de la tête). Vous bénéficiez ainsi d’un moyen flexible d’interagir avec vos hologrammes en définissant le type de focus principal dans votre profil de pointeur d’entrée MRTK en fonction des besoins de votre utilisateur, tout en laissant votre code intact.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-137">If eye tracking is set up correctly (see [Basic MRTK setup to use eye tracking](eye-tracking-basic-setup.md)), enabling users to select holograms using their eyes is the same as for any other focus input (e.g., head gaze or hand ray).This provides the great advantage of a flexible way to interact with your holograms by defining the main focus type in your MRTK Input Pointer Profile depending on your user's needs, while leaving your code untouched.</span></span> <span data-ttu-id="d7fcc-138">Cela permet de basculer entre le point de regard d’une tête ou d’un œil sans modifier une ligne de code ou de remplacer les rayons de main avec le ciblage oculaire pour les interactions lointaines.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-138">This allows for switching between head or eye gaze without changing a line of code or replace hand rays with eye targeting for far interactions.</span></span>

### <a name="focusing-on-a-hologram"></a><span data-ttu-id="d7fcc-139">Se concentrer sur un hologramme</span><span class="sxs-lookup"><span data-stu-id="d7fcc-139">Focusing on a hologram</span></span>

<span data-ttu-id="d7fcc-140">Pour détecter le moment auquel un hologramme est concentré, utilisez l’interface _« IMixedRealityFocusHandler »_ qui vous fournit deux membres de l’interface : _OnFocusEnter_ et _OnFocusExit_.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-140">To detect when a hologram is focused, use the _'IMixedRealityFocusHandler'_ interface that provides you with two interface members: _OnFocusEnter_ and _OnFocusExit_.</span></span>

<span data-ttu-id="d7fcc-141">Voici un exemple simple de [ColorTap. cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ColorTap) permettant de modifier la couleur d’un hologramme lors de la consultation.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-141">Here is a simple example from [ColorTap.cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ColorTap) to change a hologram's color when being looked at.</span></span>

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler
{
    void IMixedRealityFocusHandler.OnFocusEnter(FocusEventData eventData)
    {
        material.color = color_OnHover;
    }

    void IMixedRealityFocusHandler.OnFocusExit(FocusEventData eventData)
    {
        material.color = color_IdleState;
    }
    ...
}
```

### <a name="selecting-a-focused-hologram"></a><span data-ttu-id="d7fcc-142">Sélection d’un hologramme concentré</span><span class="sxs-lookup"><span data-stu-id="d7fcc-142">Selecting a focused hologram</span></span>

<span data-ttu-id="d7fcc-143">Pour sélectionner un hologramme concentré, utilisez _PointerHandler_ pour écouter les événements d’entrée et confirmer une sélection.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-143">To select a focused hologram, use _PointerHandler_ to listen for input events to confirm a selection.</span></span>
<span data-ttu-id="d7fcc-144">Par exemple, l’ajout de _IMixedRealityPointerHandler_ fait réagir à une entrée de pointeur simple.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-144">For example, adding the _IMixedRealityPointerHandler_ will make them react to simple pointer input.</span></span>
<span data-ttu-id="d7fcc-145">L’interface _IMixedRealityPointerHandler_ nécessite l’implémentation des trois membres d’interface suivants : _OnPointerUp_, _OnPointerDown_ et _OnPointerClicked_.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-145">The _IMixedRealityPointerHandler_ interface requires implementing the following three interface members: _OnPointerUp_, _OnPointerDown_, and _OnPointerClicked_.</span></span>

<span data-ttu-id="d7fcc-146">Dans l’exemple ci-dessous, nous modifions la couleur d’un hologramme en regardant et en pinceant ou en disant « sélectionner ».</span><span class="sxs-lookup"><span data-stu-id="d7fcc-146">In the example below, we change the color of a hologram by looking at it and pinching or saying "select".</span></span>
<span data-ttu-id="d7fcc-147">L’action requise pour déclencher l’événement est définie par le fait `eventData.MixedRealityInputAction == selectAction` que nous pouvons définir le type de `selectAction` dans l’éditeur Unity : par défaut, il s’agit de l’action « sélectionner ».</span><span class="sxs-lookup"><span data-stu-id="d7fcc-147">The required action to trigger the event is defined by `eventData.MixedRealityInputAction == selectAction` whereby we can set the type of `selectAction` in the Unity Editor - by default it's the "Select" action.</span></span> <span data-ttu-id="d7fcc-148">Les types de [MixedRealityInputActions](../input-actions.md) disponibles peuvent être configurés dans le profil MRTK via des   ->    ->  _actions d'_ entrée de profil de configuration de MRTK.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-148">The types of available [MixedRealityInputActions](../input-actions.md) can be configured in the MRTK Profile via _MRTK Configuration Profile_ -> _Input_ -> _Input Actions_.</span></span>

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler, IMixedRealityPointerHandler
{
    // Allow for editing the type of select action in the Unity Editor.
    [SerializeField]
    private MixedRealityInputAction selectAction = MixedRealityInputAction.None;
    ...

    void IMixedRealityPointerHandler.OnPointerUp(MixedRealityPointerEventData eventData)
    {
        if (eventData.MixedRealityInputAction == selectAction)
        {
            material.color = color_OnHover;
        }
    }

    void IMixedRealityPointerHandler.OnPointerDown(MixedRealityPointerEventData eventData)
    {
        if (eventData.MixedRealityInputAction == selectAction)
        {
            material.color = color_OnSelect;
        }
    }

    void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData) { }
}
```

### <a name="eye-gaze-specific-baseeyefocushandler"></a><span data-ttu-id="d7fcc-149">Yeux-BaseEyeFocusHandler spécifiques</span><span class="sxs-lookup"><span data-stu-id="d7fcc-149">Eye-gaze-specific BaseEyeFocusHandler</span></span>

<span data-ttu-id="d7fcc-150">Étant donné que le point de vue de l’œil peut être très différent des autres entrées de pointeur, vous souhaiterez peut-être vous assurer de réagir uniquement à l’entrée de focus s’il s’agit d’un point de vue _oculaire_ et qu’il s’agit actuellement du pointeur d’entrée principal.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-150">Given that eye gaze can be very different to other pointer inputs, you may want to make sure to only react to the focus input if it is _eye gaze_ and it is currently the primary input pointer.</span></span>
<span data-ttu-id="d7fcc-151">À cet effet, vous utiliseriez le [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) qui est spécifique au suivi oculaire et qui dérive de [`BaseFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseFocusHandler) .</span><span class="sxs-lookup"><span data-stu-id="d7fcc-151">For this purpose, you would use the [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) which is specific to eye tracking and which derives from the [`BaseFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseFocusHandler).</span></span>
<span data-ttu-id="d7fcc-152">Comme mentionné précédemment, il se déclenchera uniquement si la cible du point de regard de l’œil est actuellement l’entrée du pointeur principal (c’est-à-dire qu’aucun rayon de la main n’est actif).</span><span class="sxs-lookup"><span data-stu-id="d7fcc-152">As mentioned before, it will only trigger if eye gaze targeting is currently the primary pointer input (i.e., no hand ray is active).</span></span> <span data-ttu-id="d7fcc-153">Pour plus d’informations, consultez Guide pratique [pour prendre en charge les gestes oculaires + main](eye-tracking-eyes-and-hands.md).</span><span class="sxs-lookup"><span data-stu-id="d7fcc-153">For more information, see [How to support eye gaze + hand gestures](eye-tracking-eyes-and-hands.md).</span></span>

<span data-ttu-id="d7fcc-154">Voici un exemple de `EyeTrackingDemo-03-Navigation` (ressources/MRTK/examples/démonstrations/EyeTracking/scènes).</span><span class="sxs-lookup"><span data-stu-id="d7fcc-154">Here is an example from `EyeTrackingDemo-03-Navigation` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes).</span></span>
<span data-ttu-id="d7fcc-155">Dans cette démonstration, il y a deux hologrammes 3D qui s’affichent en fonction de la partie de l’objet qui est recherchée : si l’utilisateur regarde à gauche de l’hologramme, cette partie se déplacera lentement vers l’avant de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-155">In this demo, there are two 3D holograms that will turn depending on which part of the object is looked at: If the user looks at the left side of the hologram, then that part will slowly move towards the front facing the user.</span></span>
<span data-ttu-id="d7fcc-156">Si le côté droit est examiné, cette partie se déplace lentement vers l’avant.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-156">If the right side is looked at, then that part will slowly move to the front.</span></span>
<span data-ttu-id="d7fcc-157">Il s’agit d’un comportement que vous ne souhaitez peut-être pas activer à tout moment et que vous ne souhaitez peut-être pas déclencher accidentellement par un rayon de main ou un point de vue de tête.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-157">This is a behavior that you may not want to have active at all times and also something that you may not want to accidentally trigger by a hand ray or head gaze.</span></span>
<span data-ttu-id="d7fcc-158">[`OnLookAtRotateByEyeGaze`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze)Une fois attaché, un gameobject pivote en cours de recherche.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-158">Having the [`OnLookAtRotateByEyeGaze`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) attached, a GameObject will rotate while being looked at.</span></span>

```c#
public class OnLookAtRotateByEyeGaze : BaseEyeFocusHandler
{
    ...

    protected override void OnEyeFocusStay()
    {
        // Update target rotation
        RotateHitTarget();
    }

    ...

    ///
    /// This function computes the rotation of the target to move the currently
    /// looked at aspect slowly to the front.
    ///
    private void RotateHitTarget()
    {
        // Example for querying the hit position of the eye gaze ray using EyeGazeProvider
        Vector3 TargetToHit = (this.gameObject.transform.position - InputSystem.EyeGazeProvider.HitPosition).normalized;

        ...
    }
}
```

<span data-ttu-id="d7fcc-159">Consultez la documentation de l’API pour obtenir une liste complète des événements disponibles du [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) :</span><span class="sxs-lookup"><span data-stu-id="d7fcc-159">Check the API documentation for a complete list of available events of the [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler):</span></span>

- <span data-ttu-id="d7fcc-160">**OnEyeFocusStart :** Déclenché une fois que le point de regard oculaire *commence* à se croiser avec le conflit de cette cible.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-160">**OnEyeFocusStart:** Triggered once the eye gaze ray *starts* intersecting with this target's collider.</span></span>
- <span data-ttu-id="d7fcc-161">**OnEyeFocusStay :** Déclenché *lorsque* le point de regard de l’oeil est en intersection avec le conflit de cette cible.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-161">**OnEyeFocusStay:** Triggered *while* the eye gaze ray is intersecting with this target's collider.</span></span>
- <span data-ttu-id="d7fcc-162">**OnEyeFocusStop :** Déclenché une fois que le point de regard oculaire *arrête* l’intersection avec le conflit de cette cible.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-162">**OnEyeFocusStop:** Triggered once the eye gaze ray *stops* intersecting with this target's collider.</span></span>
- <span data-ttu-id="d7fcc-163">**OnEyeFocusDwell :** Déclenché une fois que le point de regard de l’œil a croisé avec le conflit de cette cible pendant un laps de temps spécifié.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-163">**OnEyeFocusDwell:** Triggered once the eye gaze ray has intersected with this target's collider for a specified amount of time.</span></span>

## <a name="2-independent-eye-gaze-specific-eyetrackingtarget"></a><span data-ttu-id="d7fcc-164">2. œil indépendant-EyeTrackingTarget spécifique au point de regard</span><span class="sxs-lookup"><span data-stu-id="d7fcc-164">2. Independent eye-gaze-specific EyeTrackingTarget</span></span>

<span data-ttu-id="d7fcc-165">Enfin, nous vous proposons une solution qui vous permet de traiter les entrées basées sur les yeux entièrement indépendantes des autres pointeurs de focalisation via le [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-165">Finally, we provide you with a solution that let's you treat eye-based input completely independent from other focus pointers via the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script.</span></span>

<span data-ttu-id="d7fcc-166">Cela présente trois _avantages_:</span><span class="sxs-lookup"><span data-stu-id="d7fcc-166">This has three _advantages_:</span></span>

- <span data-ttu-id="d7fcc-167">Vous pouvez vous assurer que l’hologramme réagit uniquement au regard de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-167">You can make sure that the hologram is only reacting to the user's eye gaze.</span></span>
- <span data-ttu-id="d7fcc-168">Cela est indépendant de l’entrée principale actuellement active.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-168">This is independent from the currently active primary input.</span></span> <span data-ttu-id="d7fcc-169">Par conséquent, vous pouvez traiter plusieurs entrées en même temps, par exemple, en combinant rapidement le ciblage oculaire avec les gestes manuels.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-169">Hence, you can process multiple inputs at once - for example, combining fast eye targeting with hand gestures.</span></span>
- <span data-ttu-id="d7fcc-170">Plusieurs événements Unity ont déjà été configurés pour accélérer et faciliter la gestion et la réutilisation des comportements existants à partir de l’éditeur Unity ou à l’aide de code.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-170">Several Unity events have already been set up to make it fast and convenient to handle and reuse existing behaviors from within the Unity Editor or via code.</span></span>

<span data-ttu-id="d7fcc-171">Il existe également quelques _inconvénients :_</span><span class="sxs-lookup"><span data-stu-id="d7fcc-171">There are also some _disadvantages:_</span></span>

- <span data-ttu-id="d7fcc-172">Plus d’effort pour gérer individuellement les entrées distinctes.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-172">More effort to handle separate inputs individually.</span></span>
- <span data-ttu-id="d7fcc-173">Aucune dégradation élégante : elle ne prend en charge que le ciblage oculaire.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-173">No elegant degradation: It only supports eye targeting.</span></span> <span data-ttu-id="d7fcc-174">Si le suivi oculaire ne fonctionne pas, vous avez besoin de secours supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-174">If eye tracking is not working, you require some additional fallback.</span></span>

<span data-ttu-id="d7fcc-175">À l’instar de _BaseFocusHandler_, le _EyeTrackingTarget_ est prêt avec plusieurs événements Unity spécifiques aux regards, que vous pouvez écouter facilement à l’aide de l’éditeur Unity (Voir l’exemple ci-dessous) ou en utilisant _AddListener ()_ dans le code :</span><span class="sxs-lookup"><span data-stu-id="d7fcc-175">Similar to the _BaseFocusHandler_, the _EyeTrackingTarget_ comes ready with several eye-gaze-specific Unity events that you can conveniently listen to either via the Unity Editor (see example below) or by using _AddListener()_ in code:</span></span>

- <span data-ttu-id="d7fcc-176">OnLookAtStart()</span><span class="sxs-lookup"><span data-stu-id="d7fcc-176">OnLookAtStart()</span></span>
- <span data-ttu-id="d7fcc-177">WhileLookingAtTarget()</span><span class="sxs-lookup"><span data-stu-id="d7fcc-177">WhileLookingAtTarget()</span></span>
- <span data-ttu-id="d7fcc-178">OnLookAway()</span><span class="sxs-lookup"><span data-stu-id="d7fcc-178">OnLookAway()</span></span>
- <span data-ttu-id="d7fcc-179">OnDwell()</span><span class="sxs-lookup"><span data-stu-id="d7fcc-179">OnDwell()</span></span>
- <span data-ttu-id="d7fcc-180">OnSelected()</span><span class="sxs-lookup"><span data-stu-id="d7fcc-180">OnSelected()</span></span>

<span data-ttu-id="d7fcc-181">Dans ce qui suit, nous vous guidons à travers quelques exemples d’utilisation de _EyeTrackingTarget_.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-181">In the following, we walk you through a few examples for how to use _EyeTrackingTarget_.</span></span>

### <a name="example-1-eye-supported-smart-notifications"></a><span data-ttu-id="d7fcc-182">Exemple #1 : notifications intelligentes prises en charge par l’œil</span><span class="sxs-lookup"><span data-stu-id="d7fcc-182">Example #1: Eye-supported smart notifications</span></span>

<span data-ttu-id="d7fcc-183">Dans `EyeTrackingDemo-02-TargetSelection` (ressources/MRTK/examples/démonstrations/EyeTracking/Scenes), vous pouvez trouver un exemple pour les _« notifications Smart précis »_ qui réagissent à votre regard.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-183">In `EyeTrackingDemo-02-TargetSelection` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes), you can find an example for _'smart attentive notifications'_ that react to your eye gaze.</span></span>
<span data-ttu-id="d7fcc-184">Il s’agit de zones de texte en 3D qui peuvent être placées dans la scène et qui s’agrandissent et s’allument vers l’utilisateur pour faciliter la lisibilité.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-184">These are 3D text boxes that can be placed in the scene and that will smoothly enlarge and turn toward the user when being looked at to ease legibility.</span></span> <span data-ttu-id="d7fcc-185">Pendant que l’utilisateur lit la notification, les informations s’affichent de façon claire et claire.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-185">While the user is reading the notification, the information keeps getting displayed crisp and clear.</span></span> <span data-ttu-id="d7fcc-186">Après l’avoir lu et extrait de la notification, la notification est automatiquement ignorée et disparaît en fondu. Pour ce faire, il existe quelques scripts de comportement génériques qui ne sont pas spécifiques au suivi oculaire, par exemple :</span><span class="sxs-lookup"><span data-stu-id="d7fcc-186">After reading it and looking away from the notification, the notification will automatically be dismissed and fades out. To achieve all this, there are a few generic behavior scripts that are not specific to eye tracking at all, such as:</span></span>

- [`FaceUser`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FaceUser)
- [`ChangeSize`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ChangeSize)
- [`BlendOut`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.BlendOut)

<span data-ttu-id="d7fcc-187">L’avantage de cette approche est que les mêmes scripts peuvent être réutilisés par différents événements.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-187">The advantage of this approach is that the same scripts can be reused by various events.</span></span> <span data-ttu-id="d7fcc-188">Par exemple, un hologramme peut commencer à faire face à l’utilisateur en fonction de commandes vocales ou après avoir appuyé sur un bouton virtuel.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-188">For example, a hologram may start facing the user based on a voice commands or after pressing a virtual button.</span></span> <span data-ttu-id="d7fcc-189">Pour déclencher ces événements, vous pouvez simplement référencer les méthodes qui doivent être exécutées dans le [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script attaché à votre GameObject.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-189">To trigger these events, you can simply reference the methods that should be executed in the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script that is attached to your GameObject.</span></span>

<span data-ttu-id="d7fcc-190">Pour l’exemple des _« notifications Smart précis »_, voici ce qui se produit :</span><span class="sxs-lookup"><span data-stu-id="d7fcc-190">For the example of the _'smart attentive notifications'_, the following happens:</span></span>

- <span data-ttu-id="d7fcc-191">**OnLookAtStart ()**: la notification commence à...</span><span class="sxs-lookup"><span data-stu-id="d7fcc-191">**OnLookAtStart()**: The notification starts to...</span></span>
  - <span data-ttu-id="d7fcc-192">*FaceUser. engagement :* ... tourner vers l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-192">*FaceUser.Engage:* ... turn toward the user.</span></span>
  - <span data-ttu-id="d7fcc-193">*Change. engagement :* ... augmentation de _la taille (jusqu’à une échelle maximale spécifiée)_.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-193">*ChangeSize.Engage:* ... increase in size _(up to a specified maximum scale)_.</span></span>
  - <span data-ttu-id="d7fcc-194">*BlendOut. engagement :* ... commence à fusionner en plus _(après avoir été à un état d’inactivité plus subtil)_.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-194">*BlendOut.Engage:* ... starts to blend in more _(after being at a more subtle idle state)_.</span></span>  

- <span data-ttu-id="d7fcc-195">**OnDwell ()**: informe le script _BlendOut_ que la notification a été examinée suffisamment.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-195">**OnDwell()**: Informs the _BlendOut_ script that the notification has been looked at sufficiently.</span></span>

- <span data-ttu-id="d7fcc-196">**OnLookAway ()**: la notification commence à...</span><span class="sxs-lookup"><span data-stu-id="d7fcc-196">**OnLookAway()**: The notification starts to...</span></span>
  - <span data-ttu-id="d7fcc-197">*FaceUser. DEBRAYAGE :* ... rétablir l’orientation d’origine.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-197">*FaceUser.Disengage:* ... turn back to its original orientation.</span></span>
  - <span data-ttu-id="d7fcc-198">*Change. Debray :* ... Diminuez sa taille d’origine.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-198">*ChangeSize.Disengage:* ... decrease back to its original size.</span></span>
  - <span data-ttu-id="d7fcc-199">*BlendOut. DEBRAYAGE :* ... commence à mélanger-si _OnDwell ()_ a été déclenché, est entièrement fusionné et détruit, sinon revient à son état inactif.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-199">*BlendOut.Disengage:* ... starts to blend out - If _OnDwell()_ was triggered, blend out completely and destroy, otherwise back to its idle state.</span></span>

<span data-ttu-id="d7fcc-200">Considérations relatives à la **conception :** La clé d’une expérience agréable consiste à régler avec soin la vitesse de l’un de ces comportements afin d’éviter de provoquer une gêne en réagissant à l’oeil de l’utilisateur trop rapidement tout le temps.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-200">**Design consideration:** The key to an enjoyable experience here is to carefully tune the speed of any of these behaviors to avoid causing discomfort by reacting to the user’s eye gaze too quickly all the time.</span></span>
<span data-ttu-id="d7fcc-201">Dans le cas contraire, cela peut rapidement sembler extrêmement écrasant.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-201">Otherwise this can quickly feel extremely overwhelming.</span></span>

<img src="../../images/eye-tracking/mrtk_et_EyeTrackingTarget_Notification.jpg" width="750" alt="Target Notification">

### <a name="example-2-holographic-gem-rotates-slowly-when-looking-at-it"></a><span data-ttu-id="d7fcc-202">Exemple #2 : la marque de gemme holographique pivote lentement lorsqu’elle est examinée</span><span class="sxs-lookup"><span data-stu-id="d7fcc-202">Example #2: Holographic gem rotates slowly when looking at it</span></span>

<span data-ttu-id="d7fcc-203">Comme pour les exemples de #1, nous pouvons facilement créer des commentaires sur le pointage pour nos gemmes holographiques dans `EyeTrackingDemo-02-TargetSelection` une scène (ressources/MRTK/examples/démonstrations/EyeTracking/scènes) qui se tournera lentement dans une direction constante et à une vitesse constante (par opposition à l’exemple de rotation ci-dessus) lors de la consultation.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-203">Similar to Example #1, we can easily create a hover feedback for our holographic gems in `EyeTrackingDemo-02-TargetSelection` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes) scene that will slowly rotate in a constant direction and at a constant speed (in contrast to the rotation example from above) when being looked at.</span></span> <span data-ttu-id="d7fcc-204">Tout ce dont vous avez besoin, c’est de déclencher la rotation de la gemme holographique à partir de l’événement _WhileLookingAtTarget ()_ de _EyeTrackingTarget_.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-204">All you need is to trigger the rotation of the holographic gem from the _EyeTrackingTarget_'s _WhileLookingAtTarget()_ event.</span></span> <span data-ttu-id="d7fcc-205">Voici quelques informations supplémentaires :</span><span class="sxs-lookup"><span data-stu-id="d7fcc-205">Here are a few more details:</span></span>

1. <span data-ttu-id="d7fcc-206">Créez un script générique qui comprend une fonction publique pour faire pivoter le GameObject auquel il est attaché.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-206">Create a generic script that includes a public function to rotate the GameObject it is attached to.</span></span> <span data-ttu-id="d7fcc-207">Vous trouverez ci-dessous un exemple de _RotateWithConstSpeedDir. cs_ dans lequel nous pouvons ajuster le sens et la vitesse de rotation à partir de l’éditeur Unity.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-207">Below is an example from _RotateWithConstSpeedDir.cs_ where we can tweak the rotation direction and speed from the Unity Editor.</span></span>

    ```c#
    using UnityEngine;

    namespace Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking
    {
        /// <summary>
        /// The associated GameObject will rotate when RotateTarget() is called based on a given direction and speed.
        /// </summary>
        public class RotateWithConstSpeedDir : MonoBehaviour
        {
            [Tooltip("Euler angles by which the object should be rotated by.")]
            [SerializeField]
            private Vector3 RotateByEulerAngles = Vector3.zero;

            [Tooltip("Rotation speed factor.")]
            [SerializeField]
            private float speed = 1f;

            /// <summary>
            /// Rotate game object based on specified rotation speed and Euler angles.
            /// </summary>
            public void RotateTarget()
            {
                transform.eulerAngles = transform.eulerAngles + RotateByEulerAngles * speed;
            }
        }
    }
    ```

1. <span data-ttu-id="d7fcc-208">Ajoutez le [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script à votre gameobject cible et référencez la fonction _RotateTarget ()_ dans le déclencheur UnityEvent, comme illustré dans la capture d’écran ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="d7fcc-208">Add the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script to your target GameObject and reference the _RotateTarget()_ function in the UnityEvent trigger as shown the screenshot below:</span></span>

    ![Exemple EyeTrackingTarget](../../images/eye-tracking/mrtk_et_EyeTrackingTargetSample.jpg)

### <a name="example-3-pop-those-gems-aka-_multi-modal-eye-gaze-supported-target-selection_"></a><span data-ttu-id="d7fcc-210">Exemple de #3 : dépiler ces gemmes alias _sélection multimodale_ de la cible avec pointage en regard</span><span class="sxs-lookup"><span data-stu-id="d7fcc-210">Example #3: Pop those gems aka _multi-modal eye-gaze-supported target selection_</span></span>

<span data-ttu-id="d7fcc-211">Dans l’exemple précédent, nous avons montré combien il est facile de détecter si une cible est examinée et comment déclencher une réaction.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-211">In the previous example, we have shown how easy it is to detect whether a target is looked at and how to trigger a reaction to that.</span></span> <span data-ttu-id="d7fcc-212">Ensuite, nous allons faire exploser les gemmes à l’aide de l’événement _OnSelected ()_ de [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) .</span><span class="sxs-lookup"><span data-stu-id="d7fcc-212">Next, let's make the gems explode using the _OnSelected()_ event from the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget).</span></span> <span data-ttu-id="d7fcc-213">La partie intéressante est la *façon dont* la sélection est déclenchée.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-213">The interesting part is *how* the selection is triggered.</span></span> <span data-ttu-id="d7fcc-214">[`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget)Permet d’assigner rapidement différentes façons d’appeler une sélection :</span><span class="sxs-lookup"><span data-stu-id="d7fcc-214">The [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) allows for quickly assigning different ways to invoke a selection:</span></span>

- <span data-ttu-id="d7fcc-215">_Mouvement de pincement_: l’affectation de la valeur « SELECT » à « SELECT » utilise le mouvement de main par défaut pour déclencher la sélection.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-215">_Pinch gesture_: Setting the 'Select Action' to 'Select' uses the default hand gesture to trigger the selection.</span></span>
<span data-ttu-id="d7fcc-216">Cela signifie que l’utilisateur peut simplement soulever sa main et pincer son doigt et son index ensemble pour confirmer la sélection.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-216">This means that the user can simply raise their hand and pinch their thumb and index finger together to confirm the selection.</span></span>

- <span data-ttu-id="d7fcc-217">Dites _« Sélectionner »_: utilisez la commande vocale par défaut _« Select »_ pour sélectionner un hologramme.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-217">Say _"Select"_: Use the default voice command _"Select"_ for selecting a hologram.</span></span>

- <span data-ttu-id="d7fcc-218">Dites _« Eclater »_ ou _« pop »_: pour utiliser des commandes vocales personnalisées, vous devez suivre deux étapes :</span><span class="sxs-lookup"><span data-stu-id="d7fcc-218">Say _"Explode"_ or _"Pop"_: To use custom voice commands, you need to follow two steps:</span></span>
    1. <span data-ttu-id="d7fcc-219">Configurer une action personnalisée comme _« DestroyTarget »_</span><span class="sxs-lookup"><span data-stu-id="d7fcc-219">Set up a custom action such as _"DestroyTarget"_</span></span>
        - <span data-ttu-id="d7fcc-220">Accéder aux _actions d’entrée de > d’entrée MRTK->_</span><span class="sxs-lookup"><span data-stu-id="d7fcc-220">Navigate to _MRTK -> Input -> Input Actions_</span></span>
        - <span data-ttu-id="d7fcc-221">Cliquez sur « Ajouter une nouvelle action ».</span><span class="sxs-lookup"><span data-stu-id="d7fcc-221">Click "Add a new action"</span></span>

    2. <span data-ttu-id="d7fcc-222">Configurer les commandes vocales qui déclenchent cette action, telles que _« Eclater »_ ou _« pop »_</span><span class="sxs-lookup"><span data-stu-id="d7fcc-222">Set up the voice commands that trigger this action such as _"Explode"_ or _"Pop"_</span></span>
        - <span data-ttu-id="d7fcc-223">Accédez à _MRTK-> entrée-> Speech_</span><span class="sxs-lookup"><span data-stu-id="d7fcc-223">Navigate to _MRTK -> Input -> Speech_</span></span>
        - <span data-ttu-id="d7fcc-224">Cliquez sur « Ajouter une nouvelle commande vocale ».</span><span class="sxs-lookup"><span data-stu-id="d7fcc-224">Click "Add a new speech command"</span></span>
            - <span data-ttu-id="d7fcc-225">Associer l’action que vous venez de créer</span><span class="sxs-lookup"><span data-stu-id="d7fcc-225">Associate the action you just created</span></span>
            - <span data-ttu-id="d7fcc-226">Assigner un _keyCode_ pour permettre le déclenchement de l’action via une pression sur un bouton</span><span class="sxs-lookup"><span data-stu-id="d7fcc-226">Assign a _KeyCode_ to allow for triggering the action via a button press</span></span>

![Exemple de commandes vocales EyeTrackingTarget](../../images/eye-tracking/mrtk_et_voicecmdsample.jpg)

<span data-ttu-id="d7fcc-228">Lorsqu’une gemme est sélectionnée, elle explose, ce qui crée un son et disparaît.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-228">When a gem is selected it will explode, making a sound and disappear.</span></span> <span data-ttu-id="d7fcc-229">Cela est géré par le [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-229">This is handled by the [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script.</span></span> <span data-ttu-id="d7fcc-230">Deux options s'offrent à vous :</span><span class="sxs-lookup"><span data-stu-id="d7fcc-230">You have two options:</span></span>

- <span data-ttu-id="d7fcc-231">**Dans l’éditeur Unity :** Vous pouvez simplement lier le script attaché à chacun de nos modèles GEM à l’événement OnSelected () Unity dans l’éditeur Unity.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-231">**In the Unity Editor:** You could simply link the script that is attached to each of our gem templates to the OnSelected() Unity event in the Unity Editor.</span></span>
- <span data-ttu-id="d7fcc-232">**Dans le code :** Si vous ne souhaitez pas faire glisser et déposer GameObjects, vous pouvez également simplement ajouter un écouteur d’événements directement à votre script.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-232">**In code:** If you don't want to drag and drop GameObjects around, you can also simply add a event listener directly to your script.</span></span>  
<span data-ttu-id="d7fcc-233">Voici un exemple de la façon dont nous l’avons fait dans le [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script :</span><span class="sxs-lookup"><span data-stu-id="d7fcc-233">Here's an example from how we did it in the [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script:</span></span>

```c#
/// <summary>
/// Destroys the game object when selected and optionally plays a sound or animation when destroyed.
/// </summary>
[RequireComponent(typeof(EyeTrackingTarget))] // This helps to ensure that the EyeTrackingTarget is attached
public class HitBehaviorDestroyOnSelect : MonoBehaviour
{
    ...
    private EyeTrackingTarget myEyeTrackingTarget = null;

    private void Start()
    {
        myEyeTrackingTarget = this.GetComponent<EyeTrackingTarget>();

        if (myEyeTrackingTarget != null)
        {
            myEyeTrackingTarget.OnSelected.AddListener(TargetSelected);
        }
    }

    ...

    ///
    /// This is called once the EyeTrackingTarget detected a selection.
    ///
    public void TargetSelected()
    {
        // Play some animation
        // Play some audio effect
        // Handle destroying the target appropriately
    }
}
```

### <a name="example-4-use-hand-rays-and-eye-gaze-input-together"></a><span data-ttu-id="d7fcc-234">Exemple #4 : utiliser des rayons de main et des entrées de regard oculaire ensemble</span><span class="sxs-lookup"><span data-stu-id="d7fcc-234">Example #4: Use hand rays and eye gaze input together</span></span>

<span data-ttu-id="d7fcc-235">Les rayons de main sont prioritaires par rapport au point de contrôle du regard.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-235">Hand rays take priority over head and eye gaze targeting.</span></span> <span data-ttu-id="d7fcc-236">Cela signifie que si les rayons de main sont activés, le moment où les mains entrent en vue, le rayon de la main agit comme pointeur principal.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-236">This means, if hand rays are enabled, the moment the hands come into view, the hand ray will act as the primary pointer.</span></span>
<span data-ttu-id="d7fcc-237">Toutefois, il peut arriver que vous souhaitiez utiliser des rayons de main tout en détectant si un utilisateur Regarde un certain hologramme.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-237">However, there might be situations in which you want to use hand rays while still detecting whether a user is looking at a certain hologram.</span></span> <span data-ttu-id="d7fcc-238">Facile !</span><span class="sxs-lookup"><span data-stu-id="d7fcc-238">Easy!</span></span> <span data-ttu-id="d7fcc-239">Pour l’essentiel, vous avez besoin de deux étapes :</span><span class="sxs-lookup"><span data-stu-id="d7fcc-239">Essentially you require two steps:</span></span>

<span data-ttu-id="d7fcc-240">**1. activer le rayon de la main :** pour activer le rayon de la main, accédez à la boîte à outils de la _réalité mixte-> pointeurs d’entrée->_.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-240">**1. Enable the hand ray:** To enable the hand ray, go to _Mixed Reality Toolkit -> Input -> Pointers_.</span></span>
<span data-ttu-id="d7fcc-241">Dans le _EyeTrackingDemo-00-RootScene_ où la boîte à outils de réalité mixte est configurée une seule fois pour toutes les scènes de démonstration du suivi oculaire, vous devez voir le _EyeTrackingDemoPointerProfile_.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-241">In the _EyeTrackingDemo-00-RootScene_ where the Mixed Reality Toolkit is configured once for all of the eye tracking demo scenes, you should see the _EyeTrackingDemoPointerProfile_.</span></span>
<span data-ttu-id="d7fcc-242">Vous pouvez créer un nouveau _profil d’entrée_ à partir de zéro ou adapter le suivi visuel actuel :</span><span class="sxs-lookup"><span data-stu-id="d7fcc-242">You can either create a new _Input Profile_ from scratch or adapt the current eye tracking one:</span></span>

- <span data-ttu-id="d7fcc-243">**À partir de zéro :** Dans l’onglet _pointeurs_ , sélectionnez _DefaultMixedRealityInputPointerProfile_ dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-243">**From scratch:** In the _Pointers_ tab, select the _DefaultMixedRealityInputPointerProfile_ from the context menu.</span></span>
<span data-ttu-id="d7fcc-244">Il s’agit du profil de pointeur par défaut pour lequel le rayon de la main est déjà activé.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-244">This is the default pointer profile that already has the hand ray enabled!</span></span>
<span data-ttu-id="d7fcc-245">Pour modifier le curseur par défaut (un point blanc opaque), clonez simplement le profil et créez votre propre profil de pointeur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-245">To change the default cursor (an opaque white dot), simply clone the profile and create your own custom pointer profile.</span></span>
<span data-ttu-id="d7fcc-246">Ensuite, remplacez _DefaultCursor_ par _EyeGazeCursor_ sous le _curseur en regard Prefab_.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-246">Then replace _DefaultCursor_ with _EyeGazeCursor_ under _Gaze Cursor Prefab_.</span></span>  
- <span data-ttu-id="d7fcc-247">**Selon le _EyeTrackingDemoPointerProfile_ existant :** double-cliquez sur _EyeTrackingDemoPointerProfile_ et ajoutez l’entrée suivante sous _Options du pointeur_:</span><span class="sxs-lookup"><span data-stu-id="d7fcc-247">**Based on the existing _EyeTrackingDemoPointerProfile_:** Double-click the _EyeTrackingDemoPointerProfile_ and add the following entry under _Pointer Options_:</span></span>
  - <span data-ttu-id="d7fcc-248">**Type de contrôleur :** « Articulée », « Windows Mixed Reality »</span><span class="sxs-lookup"><span data-stu-id="d7fcc-248">**Controller Type:** 'Articulated Hand', 'Windows Mixed Reality'</span></span>
  - <span data-ttu-id="d7fcc-249">La **main :** Aux</span><span class="sxs-lookup"><span data-stu-id="d7fcc-249">**Handedness:** Any</span></span>
  - <span data-ttu-id="d7fcc-250">**Pointeur Prefab :** DefaultControllerPointer</span><span class="sxs-lookup"><span data-stu-id="d7fcc-250">**Pointer Prefab:** DefaultControllerPointer</span></span>

<span data-ttu-id="d7fcc-251">**2. détecter qu’un hologramme est examiné :** utilisez le [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script pour activer la détection d’un hologramme comme décrit ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-251">**2. Detect that a hologram is looked at:** Use the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script to enable detecting that a hologram is looked at as described above.</span></span> <span data-ttu-id="d7fcc-252">Vous pouvez également jeter un coup d’œil à l' `FollowEyeGaze` exemple de script, car il montre un hologramme à la suite de votre point de regard (par exemple, un curseur) si les rayons de main sont activés ou non.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-252">You can also take a look at the `FollowEyeGaze` sample script for inspiration as this is showing a hologram following your eye gaze (e.g., a cursor) whether hand rays are enabled or not.</span></span>

<span data-ttu-id="d7fcc-253">À présent, lorsque vous démarrez les scènes de démonstration du suivi oculaire, vous devriez voir un rayon venant de vos mains.</span><span class="sxs-lookup"><span data-stu-id="d7fcc-253">Now, when you start the eye tracking demo scenes, you should see a ray coming from your hands.</span></span>
<span data-ttu-id="d7fcc-254">Par exemple, dans la démonstration de sélection de la cible de suivi oculaire, le cercle semi-transparent est toujours à la suite de votre point de vue et les gemmes répondent à la présence ou à la non-utilisation du pointeur d’entrée principal (vos mains).</span><span class="sxs-lookup"><span data-stu-id="d7fcc-254">For example, in the eye tracking target selection demo, the semi-transparent circle is still following your eye gaze and the gems respond to whether they are looked at or not, while the top scene menu buttons use the primary input pointer (your hands) instead.</span></span>

---
[<span data-ttu-id="d7fcc-255">Retour à « suivi oculaire dans le MixedRealityToolkit »</span><span class="sxs-lookup"><span data-stu-id="d7fcc-255">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](eye-tracking-main.md)
