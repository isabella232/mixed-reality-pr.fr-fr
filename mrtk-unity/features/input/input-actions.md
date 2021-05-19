---
title: Actions d’entrée
description: Documentation pour créer des actions d’entrée dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, InputActions,
ms.openlocfilehash: 071d4bc8bb4193a3d60cb53852c192ae975d79df
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144153"
---
# <a name="input-actions"></a><span data-ttu-id="3cb90-104">Actions d’entrée</span><span class="sxs-lookup"><span data-stu-id="3cb90-104">Input actions</span></span>

<span data-ttu-id="3cb90-105">Les [**actions d’entrée**](input-actions.md) sont des abstractions sur les entrées brutes destinées à aider à isoler la logique d’application des sources d’entrée spécifiques produisant une entrée.</span><span class="sxs-lookup"><span data-stu-id="3cb90-105">[**Input Actions**](input-actions.md) are abstractions over raw inputs meant to help isolating application logic from the specific input sources producing an input.</span></span> <span data-ttu-id="3cb90-106">Il peut être utile, par exemple, de définir une action *Select* et de la mapper au bouton gauche de la souris, un bouton dans un boîtier de commande et un déclencheur dans un contrôleur 6 DDL.</span><span class="sxs-lookup"><span data-stu-id="3cb90-106">It can be useful, for example, to define a *Select* action and map it to the left mouse button, a button in a gamepad and a trigger in a 6 DOF controller.</span></span> <span data-ttu-id="3cb90-107">Vous pouvez ensuite faire en sorte que la logique de votre application écoute les événements de l’action d’entrée *Select* au lieu d’avoir à connaître toutes les différentes entrées pouvant la produire.</span><span class="sxs-lookup"><span data-stu-id="3cb90-107">You can then have your application logic listen for *Select* input action events instead of having to be aware of all the different inputs that can produce it.</span></span>

## <a name="creating-an-input-action"></a><span data-ttu-id="3cb90-108">Création d’une action d’entrée</span><span class="sxs-lookup"><span data-stu-id="3cb90-108">Creating an input action</span></span>

<span data-ttu-id="3cb90-109">Les actions d’entrée sont configurées dans le **Profil actions d’entrée**, à l’intérieur du *profil de système d’entrée* dans le composant d’outils de réalité mixte, en spécifiant un nom pour l’action et le type d’entrées (*contrainte d’axe*) qu’elle peut être mappée à :</span><span class="sxs-lookup"><span data-stu-id="3cb90-109">Input actions are configured in the **Input Actions Profile**, inside the *Input System Profile* in the Mixed Reality Toolkit component, specifying a name for the action and the type of inputs (*Axis Constraint*) it can be mapped to:</span></span>

<img src="../images/input/InputActions.png" alt="Input Action" style="max-width:100%;">

<span data-ttu-id="3cb90-110">Il s’agit des valeurs les plus couramment utilisées pour la **contrainte d’axe**:</span><span class="sxs-lookup"><span data-stu-id="3cb90-110">These are the most mostly commonly used values for **Axis Constraint**:</span></span>

<span data-ttu-id="3cb90-111">Contrainte d’axe</span><span class="sxs-lookup"><span data-stu-id="3cb90-111">Axis Constraint</span></span> | <span data-ttu-id="3cb90-112">Description</span><span class="sxs-lookup"><span data-stu-id="3cb90-112">Description</span></span>
--- | ---
<span data-ttu-id="3cb90-113">Digital</span><span class="sxs-lookup"><span data-stu-id="3cb90-113">Digital</span></span> | <span data-ttu-id="3cb90-114">Entrée on/off comme un bouton binaire dans un boîtier de connexion ou une souris.</span><span class="sxs-lookup"><span data-stu-id="3cb90-114">On/off input like a binary button in a gamepad or mouse.</span></span>
<span data-ttu-id="3cb90-115">Axe unique</span><span class="sxs-lookup"><span data-stu-id="3cb90-115">Single Axis</span></span> | <span data-ttu-id="3cb90-116">Entrée analogique à un seul axe comme un déclencheur analogique dans un boîtier de souformement.</span><span class="sxs-lookup"><span data-stu-id="3cb90-116">Single axis analogue input like an analog trigger in a gamepad.</span></span>
<span data-ttu-id="3cb90-117">Axe double</span><span class="sxs-lookup"><span data-stu-id="3cb90-117">Dual Axis</span></span> | <span data-ttu-id="3cb90-118">Entrée analogique à deux axes comme un stick analogique.</span><span class="sxs-lookup"><span data-stu-id="3cb90-118">Dual axis analogue input like a thumbstick.</span></span>
<span data-ttu-id="3cb90-119">Six DDL</span><span class="sxs-lookup"><span data-stu-id="3cb90-119">Six Dof</span></span> | <span data-ttu-id="3cb90-120">composition 3D avec traduction et rotation comme celle produite par 6 contrôleurs DDL.</span><span class="sxs-lookup"><span data-stu-id="3cb90-120">3D pose with translation and rotation like the one produced by 6 DOF controllers.</span></span>

<span data-ttu-id="3cb90-121">Vous trouverez la liste complète dans [`AxisType`](xref:Microsoft.MixedReality.Toolkit.Utilities.AxisType) .</span><span class="sxs-lookup"><span data-stu-id="3cb90-121">You can find the full list in [`AxisType`](xref:Microsoft.MixedReality.Toolkit.Utilities.AxisType).</span></span>

## <a name="mapping-input-to-actions"></a><span data-ttu-id="3cb90-122">Mappage de l’entrée aux actions</span><span class="sxs-lookup"><span data-stu-id="3cb90-122">Mapping input to actions</span></span>

<span data-ttu-id="3cb90-123">La façon dont vous mappez une entrée à et l’action dépend du type de la source d’entrée :</span><span class="sxs-lookup"><span data-stu-id="3cb90-123">The way you map an input to and action depends on the type of the input source:</span></span>

### <a name="controller-input"></a><span data-ttu-id="3cb90-124">Entrée du contrôleur</span><span class="sxs-lookup"><span data-stu-id="3cb90-124">Controller input</span></span>

<span data-ttu-id="3cb90-125">Accédez au **profil de mappage d’entrée du contrôleur**, sous le profil de *système d’entrée*.</span><span class="sxs-lookup"><span data-stu-id="3cb90-125">Go to the **Controller Input Mapping Profile**, under the *Input System Profile*.</span></span> <span data-ttu-id="3cb90-126">Vous y trouverez une liste de tous les contrôleurs pris en charge :</span><span class="sxs-lookup"><span data-stu-id="3cb90-126">There you will find a list of all supported controllers:</span></span>

<img src="../images/input/ControllerInputMappingProfile.PNG" alt="Input maping profile" style="max-width:100%;">

<span data-ttu-id="3cb90-127">Sélectionnez celui que vous souhaitez configurer et une fenêtre de dialogue s’affiche avec toutes les entrées du contrôleur, ce qui vous permet de définir une action pour chacun d’entre eux :</span><span class="sxs-lookup"><span data-stu-id="3cb90-127">Select the one you want to configure and a dialog window will appear with all the controller inputs, allowing you to set an action for each of them:</span></span>

<img src="../images/input/InputActionAssignment.PNG" alt="Input Action Assignment" style="max-width:100%;">

### <a name="speech-input"></a><span data-ttu-id="3cb90-128">SpeechInput</span><span class="sxs-lookup"><span data-stu-id="3cb90-128">Speech input</span></span>

<span data-ttu-id="3cb90-129">Dans le **profil de commande Speech**, sous le *profil de système d’entrée*, vous trouverez la liste des commandes vocales actuellement définies.</span><span class="sxs-lookup"><span data-stu-id="3cb90-129">In the **Speech Command Profile**, under the *Input System Profile*, you'll find the list of currently defined speech commands.</span></span> <span data-ttu-id="3cb90-130">Pour mapper l’une d’entre elles à une action, sélectionnez-la dans la liste déroulante *action* .</span><span class="sxs-lookup"><span data-stu-id="3cb90-130">To map one of them to an action, just select it in the *Action* drop down.</span></span>

<img src="../images/input/SpeechCommandsProfile.png" alt="Speech Commands profile" style="max-width:100%;">

### <a name="gesture-input"></a><span data-ttu-id="3cb90-131">Entrée de mouvement</span><span class="sxs-lookup"><span data-stu-id="3cb90-131">Gesture input</span></span>

<span data-ttu-id="3cb90-132">Le **profil de mouvements**, sous le *profil de système d’entrée*, contient tous les mouvements définis.</span><span class="sxs-lookup"><span data-stu-id="3cb90-132">The **Gestures Profile**, under the *Input System Profile*, contains all defined gestures.</span></span> <span data-ttu-id="3cb90-133">Vous pouvez mapper chacune d’elles à une action en la sélectionnant dans la liste déroulante *action* .</span><span class="sxs-lookup"><span data-stu-id="3cb90-133">You can map each of them to an action by selecting it in the *Action* drop down.</span></span>

<img src="../images/input/GestureProfile.png" alt="Gesture profile" style="max-width:100%;">

## <a name="handling-input-actions"></a><span data-ttu-id="3cb90-134">Gestion des actions d’entrée</span><span class="sxs-lookup"><span data-stu-id="3cb90-134">Handling input actions</span></span>

> [!WARNING]
> <span data-ttu-id="3cb90-135">Actuellement, seules les actions d’entrée de type *numérique* peuvent être gérées à l’aide des méthodes décrites dans cette section.</span><span class="sxs-lookup"><span data-stu-id="3cb90-135">Currently only input actions of *Digital* type can be handled using the methods described in this section.</span></span> <span data-ttu-id="3cb90-136">Pour les autres types d’action, vous devez gérer directement les événements pour les entrées correspondantes.</span><span class="sxs-lookup"><span data-stu-id="3cb90-136">For other action types, you'll have to handle directly the events for the corresponding inputs instead.</span></span> <span data-ttu-id="3cb90-137">Par exemple, pour gérer une action de 6 DDL mappée aux entrées du contrôleur, vous devez utiliser [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) avec T = [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) .</span><span class="sxs-lookup"><span data-stu-id="3cb90-137">For example, to handle a 6 DOF action mapped to controller inputs, you'll have to use [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) with T = [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose).</span></span>

<span data-ttu-id="3cb90-138">Le moyen le plus simple de gérer les actions d’entrée consiste à utiliser le [`InputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.InputActionHandler) script.</span><span class="sxs-lookup"><span data-stu-id="3cb90-138">The easiest way to handle input actions is to make use of the [`InputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.InputActionHandler) script.</span></span> <span data-ttu-id="3cb90-139">Cela vous permet de définir l’action que vous souhaitez écouter et de réagir aux événements d’action démarrés et terminés à l’aide d’événements Unity.</span><span class="sxs-lookup"><span data-stu-id="3cb90-139">This allows you to define the action you want to listen to and react to action started and ended events using Unity Events.</span></span>

<img src="../images/input/InputActionHandler.PNG" alt="Acton Handler" style="max-width:100%;">

<span data-ttu-id="3cb90-140">Si vous souhaitez davantage de contrôle, vous pouvez implémenter l' [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) interface directement dans votre script.</span><span class="sxs-lookup"><span data-stu-id="3cb90-140">If you want more control, you can implement the [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) interface directly in your script.</span></span> <span data-ttu-id="3cb90-141">Pour plus d’informations sur la gestion des événements via des interfaces de gestionnaire, consultez la section [**événements d’entrée**](input-events.md) .</span><span class="sxs-lookup"><span data-stu-id="3cb90-141">See the [**Input Events**](input-events.md) section for more details on event handling via handler interfaces.</span></span>

## <a name="examples"></a><span data-ttu-id="3cb90-142">Exemples</span><span class="sxs-lookup"><span data-stu-id="3cb90-142">Examples</span></span>

<span data-ttu-id="3cb90-143">`MRTK/Examples/Demos/Input/Scenes/InputActions`Pour obtenir un exemple de scène illustrant comment créer une action, mappez-la à des entrées de contrôleur, de voix et de mouvement et utilisez-la pour faire pivoter un objet sur une commande.</span><span class="sxs-lookup"><span data-stu-id="3cb90-143">See `MRTK/Examples/Demos/Input/Scenes/InputActions` for an example scene showing how to create an action, map it to controller, speech and gesture inputs and use it to rotate an object on command.</span></span>

<img src="../images/input/InputActionsExample.PNG" alt="Input action example" style="max-width:100%;">
