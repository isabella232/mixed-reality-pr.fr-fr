---
title: Curseur
description: Vue d’ensemble des curseurs MRTK
author: RogPodge
ms.author: roliu
ms.date: 06/18/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, curseurs,
ms.openlocfilehash: be19806e0202f6cb3ddcea1a80c2c40811aff4f2
ms.sourcegitcommit: e9661d3bab061f9499134226ef3b87751ec56277
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/22/2021
ms.locfileid: "112426875"
---
# <a name="sliders"></a><span data-ttu-id="f960a-104">Curseurs</span><span class="sxs-lookup"><span data-stu-id="f960a-104">Sliders</span></span>

![Exemple de curseur](../images/slider/MRTK_UX_Slider_Main.jpg)

<span data-ttu-id="f960a-106">Les curseurs sont des composants d’interface utilisateur qui vous permettent de modifier continuellement une valeur en déplaçant un curseur sur une piste. Actuellement, le curseur de pincement peut être déplacé en saisissant directement le curseur, soit directement, soit à distance.</span><span class="sxs-lookup"><span data-stu-id="f960a-106">Sliders are UI components that allow you to continuously change a value by moving a slider on a track. Currently the Pinch Slider can be moved by directly grabbing the slider, either directly or at a distance.</span></span> <span data-ttu-id="f960a-107">Les curseurs fonctionnent sur AR et VR, à l’aide des contrôleurs de mouvement, des mains ou du geste + voix.</span><span class="sxs-lookup"><span data-stu-id="f960a-107">Sliders work on AR and VR, using motion controllers, hands, or Gesture + Voice.</span></span>

## <a name="example-scene"></a><span data-ttu-id="f960a-108">Exemple de scène</span><span class="sxs-lookup"><span data-stu-id="f960a-108">Example scene</span></span>

<span data-ttu-id="f960a-109">Vous trouverez des exemples dans la scène **SliderExample** sous `MRTK/Examples/Demos/UX/Slider/Scenes/` .</span><span class="sxs-lookup"><span data-stu-id="f960a-109">You can find examples in the **SliderExample** scene under `MRTK/Examples/Demos/UX/Slider/Scenes/`.</span></span>

## <a name="how-to-use-sliders"></a><span data-ttu-id="f960a-110">Comment utiliser des curseurs</span><span class="sxs-lookup"><span data-stu-id="f960a-110">How to use sliders</span></span>

<span data-ttu-id="f960a-111">Glissez-déplacez le Prefab **PinchSlider** dans la hiérarchie de la scène.</span><span class="sxs-lookup"><span data-stu-id="f960a-111">Drag and drop the **PinchSlider** prefab into the scene hierarchy.</span></span> <span data-ttu-id="f960a-112">Si vous souhaitez modifier ou créer votre propre curseur, n’oubliez pas d’effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="f960a-112">If you want to modify or create your own slider, remember to do the following:</span></span>

- <span data-ttu-id="f960a-113">Assurez-vous que votre objet Thumb comporte un conflit.</span><span class="sxs-lookup"><span data-stu-id="f960a-113">Make sure your that your thumb object has a collider on it.</span></span> <span data-ttu-id="f960a-114">Dans le Prefab PinchSlider, le conflit est activé `SliderThumb/Button_AnimationContainer/Slider_Button`</span><span class="sxs-lookup"><span data-stu-id="f960a-114">In the PinchSlider prefab, the collider is on `SliderThumb/Button_AnimationContainer/Slider_Button`</span></span>
- <span data-ttu-id="f960a-115">Assurez-vous que l’objet contenant l’élément de conflit comporte également un composant à proximité d’une interaction proche, si vous souhaitez être en mesure de saisir le curseur à proximité.</span><span class="sxs-lookup"><span data-stu-id="f960a-115">Make sure that the object containing the collider also has a Near Interaction Grabbable component on it, if you want to be able to grab the slider near.</span></span>

<span data-ttu-id="f960a-116">Nous vous recommandons également d’utiliser la hiérarchie suivante :</span><span class="sxs-lookup"><span data-stu-id="f960a-116">We also recommend using the following hierarchy</span></span>

- <span data-ttu-id="f960a-117">PinchSlider-contient sliderComponent</span><span class="sxs-lookup"><span data-stu-id="f960a-117">PinchSlider - Contains the sliderComponent</span></span>
  - <span data-ttu-id="f960a-118">TouchCollider-conflit contenant l’intégralité de la zone sélectionnable du curseur.</span><span class="sxs-lookup"><span data-stu-id="f960a-118">TouchCollider - Collider containing the entire selectable area of the slider.</span></span> <span data-ttu-id="f960a-119">Active le comportement de l’alignement sur la position.</span><span class="sxs-lookup"><span data-stu-id="f960a-119">Enables the Snap To Position behavior.</span></span>
  - <span data-ttu-id="f960a-120">SliderThumb : contient le curseur amovible</span><span class="sxs-lookup"><span data-stu-id="f960a-120">SliderThumb - Contains the movable thumb</span></span>
  - <span data-ttu-id="f960a-121">TrackVisuals-contenant la piste et tous les autres éléments visuels</span><span class="sxs-lookup"><span data-stu-id="f960a-121">TrackVisuals - Containing the track and any other visuals</span></span>
  - <span data-ttu-id="f960a-122">OtherVisuals-contenant tout autre visuel</span><span class="sxs-lookup"><span data-stu-id="f960a-122">OtherVisuals - Containing any other visuals</span></span>

## <a name="slider-events"></a><span data-ttu-id="f960a-123">Événements Slider</span><span class="sxs-lookup"><span data-stu-id="f960a-123">Slider events</span></span>

<span data-ttu-id="f960a-124">Les curseurs exposent les événements suivants :</span><span class="sxs-lookup"><span data-stu-id="f960a-124">Sliders expose the following events:</span></span>

- <span data-ttu-id="f960a-125">OnValueUpdated-appelée chaque fois que la valeur du curseur change</span><span class="sxs-lookup"><span data-stu-id="f960a-125">OnValueUpdated - Called whenever the slider value changes</span></span>
- <span data-ttu-id="f960a-126">OnInteractionStarted : appelé lorsque l’utilisateur récupère le curseur</span><span class="sxs-lookup"><span data-stu-id="f960a-126">OnInteractionStarted - Called when the user grabs the slider</span></span>
- <span data-ttu-id="f960a-127">OnInteractionEnded : appelé lorsque l’utilisateur relâche le curseur</span><span class="sxs-lookup"><span data-stu-id="f960a-127">OnInteractionEnded - Called when the user releases the slider</span></span>
- <span data-ttu-id="f960a-128">OnHoverEntered : appelée lorsque la main/le contrôleur de l’utilisateur pointe sur le curseur, à l’aide d’une interaction proche ou éloignée.</span><span class="sxs-lookup"><span data-stu-id="f960a-128">OnHoverEntered - Called when the user's hand / controller hovers over the slider, using either near or far interaction.</span></span>
- <span data-ttu-id="f960a-129">OnHoverExited : appelée lorsque la main/le contrôleur de l’utilisateur n’est plus près du curseur.</span><span class="sxs-lookup"><span data-stu-id="f960a-129">OnHoverExited - Called when the user's hand / controller is no longer near the slider.</span></span>

## <a name="configuring-slider-bound-and-axis"></a><span data-ttu-id="f960a-130">Configuration du curseur lié et axe</span><span class="sxs-lookup"><span data-stu-id="f960a-130">Configuring slider bound and axis</span></span>

<span data-ttu-id="f960a-131">Vous pouvez déplacer directement les points de début et de fin du curseur en déplaçant les poignées dans la scène :</span><span class="sxs-lookup"><span data-stu-id="f960a-131">You can directly move the starting and end points of the slider by moving the handles in the Scene:</span></span>

![Configuration des curseurs](../images/sliders/MRTK_Sliders_Setup.png)

<span data-ttu-id="f960a-133">Vous pouvez également spécifier l’axe (dans l’espace local) du curseur à l’aide du champ de l' _axe du curseur_ .</span><span class="sxs-lookup"><span data-stu-id="f960a-133">You can also specify the axis (in local space) of the slider via the _Slider Axis_ field</span></span>

<span data-ttu-id="f960a-134">Si vous ne pouvez pas utiliser les descripteurs, vous pouvez spécifier à la place les points de début et de fin du curseur à l’aide des champs _distance de début du curseur_ et distance de fin du _curseur_ .</span><span class="sxs-lookup"><span data-stu-id="f960a-134">If you cannot use the handles, you can instead specify the start and end points of the slider via the _Slider Start Distance_ and _Slider End Distance_ fields.</span></span> <span data-ttu-id="f960a-135">Celles-ci spécifient la position de début/fin du curseur sous la forme d’une distance par rapport au centre du curseur, en coordonnées locales.</span><span class="sxs-lookup"><span data-stu-id="f960a-135">These specify start / end position of slider as a distance from the slider's center, in local coordinates.</span></span> <span data-ttu-id="f960a-136">Cela signifie qu’une fois que vous avez défini les distances de début et de fin du curseur comme vous le souhaitez, vous pouvez mettre le curseur à l’échelle de façon à ce qu’il soit plus petit ou plus grand sans avoir besoin de mettre à jour les distances de début et de fin.</span><span class="sxs-lookup"><span data-stu-id="f960a-136">This means that once you set the slider start and end distances as you want them, you can scale the slider to be smaller or larger without needing to update the start and end distances.</span></span>

## <a name="inspector-properties"></a><span data-ttu-id="f960a-137">Propriétés de l’inspecteur</span><span class="sxs-lookup"><span data-stu-id="f960a-137">Inspector properties</span></span>

<span data-ttu-id="f960a-138">**Racine Thumb** Gameobject qui contient le curseur de curseur.</span><span class="sxs-lookup"><span data-stu-id="f960a-138">**Thumb Root** The gameobject that contains the slider thumb.</span></span>

<span data-ttu-id="f960a-139">**Aligner sur la position** Indique si ce curseur s’aligne à la position désignée sur le curseur</span><span class="sxs-lookup"><span data-stu-id="f960a-139">**Snap To Position** Whether or not this slider snaps to the designated position on the slider</span></span>

<span data-ttu-id="f960a-140">**Est touchable** Indique si ce curseur est contrôlable via des événements tactiles</span><span class="sxs-lookup"><span data-stu-id="f960a-140">**Is Touchable** Whether or not this slider is controllable via touch events</span></span>

<span data-ttu-id="f960a-141">**Conflit Thumb** Conflit qui contrôle le curseur de curseur</span><span class="sxs-lookup"><span data-stu-id="f960a-141">**Thumb Collider** The collider that controls the slider thumb</span></span>

<span data-ttu-id="f960a-142">**Touchable** Zone du curseur qui peut être touchée ou sélectionnée quand l’option accrocher à la position a la valeur true.</span><span class="sxs-lookup"><span data-stu-id="f960a-142">**Touchable Collider** The area of the slider that can be touched or selected when Snap To Position is true.</span></span>

<span data-ttu-id="f960a-143">**Valeur du curseur** Valeur du curseur.</span><span class="sxs-lookup"><span data-stu-id="f960a-143">**Slider Value** The value of the slider.</span></span>

<span data-ttu-id="f960a-144">**Utiliser les divisions** de l’étape de curseur Contrôle si ce curseur est incrémenté en étapes ou en continu.</span><span class="sxs-lookup"><span data-stu-id="f960a-144">**Use Slider Step Divisions** Controls whether this slider is increments in steps or continuously.</span></span>

<span data-ttu-id="f960a-145">**Étapes de curseur des divisions** Nombre de sous-divisions où le curseur est divisé quand l’option utiliser le curseur est désactivée.</span><span class="sxs-lookup"><span data-stu-id="f960a-145">**Slider Step Divisions** Number of subdivisions the slider is split into when Use Slider Step Divisions is enabled.</span></span>

<span data-ttu-id="f960a-146">**Suivre** les éléments visuels Gameobject qui contient les éléments visuels de piste souhaités qui se trouvent le long du curseur.</span><span class="sxs-lookup"><span data-stu-id="f960a-146">**Track Visuals** The gameobject that contains the desired track visuals that goes along the slider.</span></span>

<span data-ttu-id="f960a-147">**Graduations** Gameobject qui contient les graduations souhaitées qui se déplacent sur le curseur.</span><span class="sxs-lookup"><span data-stu-id="f960a-147">**Tick Marks** The gameobject that contains the desired tick marks that goes along the slider.</span></span>

<span data-ttu-id="f960a-148">Éléments **visuels Thumb** Gameobject qui contient le visuel Thumb souhaité qui se déplace le long du curseur.</span><span class="sxs-lookup"><span data-stu-id="f960a-148">**Thumb Visuals** The gameobject that contains the desired thumb visual that goes along the slider.</span></span>

<span data-ttu-id="f960a-149">**Axe du curseur** Axe sur lequel se déplace le curseur.</span><span class="sxs-lookup"><span data-stu-id="f960a-149">**Slider Axis** The axis the slider moves along.</span></span>

<span data-ttu-id="f960a-150">**Distance de début du curseur** Où la piste du curseur démarre, par rapport à la distance entre le centre et l’axe du curseur, dans les unités d’espace locales.</span><span class="sxs-lookup"><span data-stu-id="f960a-150">**Slider Start Distance** Where the slider track starts, as distance from center along slider axis, in local space units.</span></span>

<span data-ttu-id="f960a-151">**Distance de fin du curseur** Où la piste du curseur se termine, en tant que distance par rapport au centre sur l’axe du curseur, dans les unités d’espace locales.</span><span class="sxs-lookup"><span data-stu-id="f960a-151">**Slider End Distance** Where the slider track ends, as distance from center along slider axis, in local space units.</span></span>

<span data-ttu-id="f960a-152">Quand l’utilisateur met à jour la valeur de l’axe du curseur dans l’éditeur, alors si les éléments visuels de suivi ou les éléments visuels de suivi sont spécifiés, leur transformation est mise à jour.</span><span class="sxs-lookup"><span data-stu-id="f960a-152">When user updates the slider axis value in editor then if Track Visuals or Tick Visuals are specified then their transform is updated.</span></span>
<span data-ttu-id="f960a-153">Plus précisément, leur position locale est réinitialisée et leur rotation locale est définie pour correspondre à l’orientation de l’axe du curseur.</span><span class="sxs-lookup"><span data-stu-id="f960a-153">Specifically, their local position is reset and their local rotation is set to match the Slider Axis orientation.</span></span>
<span data-ttu-id="f960a-154">Leur échelle n’est pas modifiée.</span><span class="sxs-lookup"><span data-stu-id="f960a-154">Their scale isn't modified.</span></span>
<span data-ttu-id="f960a-155">Si les graduations comportent un composant de collection d’objets grille, les éléments layout et CellWidth ou CellHeight sont mis à jour en conséquence pour correspondre à l’axe du curseur.</span><span class="sxs-lookup"><span data-stu-id="f960a-155">If Tick Marks have a Grid Object Collection component then the Layout and CellWidth or CellHeight is updated accordingly to match the Slider Axis.</span></span>

## <a name="example-slider-configurations"></a><span data-ttu-id="f960a-156">Exemples de configurations de curseur</span><span class="sxs-lookup"><span data-stu-id="f960a-156">Example Slider Configurations</span></span>

<span data-ttu-id="f960a-157">Curseurs continus avec les ![ curseurs continus de position de magnétisme](https://user-images.githubusercontent.com/39840334/122488212-d410a400-cf91-11eb-8d31-fc7584ddc465.gif)</span><span class="sxs-lookup"><span data-stu-id="f960a-157">Continuous Sliders with Snap To Position ![Continuous Sliders](https://user-images.githubusercontent.com/39840334/122488212-d410a400-cf91-11eb-8d31-fc7584ddc465.gif)</span></span>

<span data-ttu-id="f960a-158">Curseurs d’étape avec alignement sur la position</span><span class="sxs-lookup"><span data-stu-id="f960a-158">Step Sliders with Snap To Position</span></span>

![Curseurs d’étape](https://user-images.githubusercontent.com/39840334/122488226-dc68df00-cf91-11eb-9459-89655bbb054d.gif)

<span data-ttu-id="f960a-160">Curseurs tactiles</span><span class="sxs-lookup"><span data-stu-id="f960a-160">Touch Sliders</span></span>

![Curseurs tactiles](https://user-images.githubusercontent.com/39840334/122488221-d8d55800-cf91-11eb-91a1-bb12debe2797.gif)