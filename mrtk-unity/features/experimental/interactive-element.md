---
title: Élément interactif
description: Documentation de InteractiveElement MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 02/22/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, élément interactif, interactif
ms.openlocfilehash: 65f518c53414d68d3a9d2093cb427140cc65560b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144759"
---
# <a name="interactive-element-experimental"></a><span data-ttu-id="2e4a0-104">Élément interactif [expérimental]</span><span class="sxs-lookup"><span data-stu-id="2e4a0-104">Interactive Element [Experimental]</span></span>

<span data-ttu-id="2e4a0-105">Point d’entrée centralisé simplifié dans le système d’entrée MRTK.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-105">A simplified centralized entry point to the MRTK input system.</span></span> <span data-ttu-id="2e4a0-106">Contient les méthodes de gestion d’État, la gestion des événements et la logique de paramétrage d’État pour les États d’interaction de base.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-106">Contains state management methods, event management and the state setting logic for Core Interaction States.</span></span>

<span data-ttu-id="2e4a0-107">L’élément interactif est une fonctionnalité expérimentale prise en charge dans Unity 2019,3 et up, car elle utilise une fonctionnalité nouvelle dans Unity 2019,3 : [Serialize Reference](https://docs.unity3d.com/ScriptReference/SerializeReference.html).</span><span class="sxs-lookup"><span data-stu-id="2e4a0-107">Interactive Element is an experimental feature supported in Unity 2019.3 and up as it utilizes a capability new to Unity 2019.3: [Serialize Reference](https://docs.unity3d.com/ScriptReference/SerializeReference.html).</span></span>

### <a name="interactive-element-inspector"></a><span data-ttu-id="2e4a0-108">Inspecteur d’élément interactif</span><span class="sxs-lookup"><span data-stu-id="2e4a0-108">Interactive Element Inspector</span></span>

<span data-ttu-id="2e4a0-109">En mode lecture, l’inspecteur d’élément interactif fournit un retour visuel qui indique si l’état actuel est actif ou non.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-109">During play mode, the Interactive Element inspector provides visual feedback that indicates whether or not the current state is active.</span></span> <span data-ttu-id="2e4a0-110">Si un État est actif, il est mis en surbrillance avec une couleur cyan.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-110">If a state is active, it will be highlighted with a cyan color.</span></span>  <span data-ttu-id="2e4a0-111">Si l’État n’est pas actif, la couleur n’est pas modifiée.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-111">If the state is not active, the color is not changed.</span></span> <span data-ttu-id="2e4a0-112">Les nombres situés à côté des États dans l’inspecteur sont les valeurs d’État, si l’État est actif, alors la valeur est 1, si l’État n’est pas actif, la valeur est 0.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-112">The numbers next to the states in the inspector are the state values, if the state is active then the value is 1, if the state is not active the value is 0.</span></span>

![Élément interactif avec interaction de la main virtuelle](../images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

## <a name="core-states"></a><span data-ttu-id="2e4a0-114">États de base</span><span class="sxs-lookup"><span data-stu-id="2e4a0-114">Core States</span></span>

<span data-ttu-id="2e4a0-115">L’élément interactif contient les États principaux et prend en charge l’ajout d' [États personnalisés](#custom-states).</span><span class="sxs-lookup"><span data-stu-id="2e4a0-115">Interactive Element contains core states and supports the addition of [custom states](#custom-states).</span></span>  <span data-ttu-id="2e4a0-116">Un état de base est un État qui possède déjà la logique du paramètre d’état définie dans `BaseInteractiveElement` .</span><span class="sxs-lookup"><span data-stu-id="2e4a0-116">A core state is one that already has the state setting logic defined in `BaseInteractiveElement`.</span></span> <span data-ttu-id="2e4a0-117">La liste suivante répertorie les États de base d’entrée actuels :</span><span class="sxs-lookup"><span data-stu-id="2e4a0-117">The following is a list of the current input-driven core states:</span></span> 

### <a name="current-core-states"></a><span data-ttu-id="2e4a0-118">États de base actuels</span><span class="sxs-lookup"><span data-stu-id="2e4a0-118">Current Core States</span></span>

- [<span data-ttu-id="2e4a0-119">Par défaut</span><span class="sxs-lookup"><span data-stu-id="2e4a0-119">Default</span></span>](#default-state) 

<span data-ttu-id="2e4a0-120">États de base de l’interaction near et Far :</span><span class="sxs-lookup"><span data-stu-id="2e4a0-120">Near and Far Interaction Core States:</span></span>
- [<span data-ttu-id="2e4a0-121">Priorité</span><span class="sxs-lookup"><span data-stu-id="2e4a0-121">Focus</span></span>](#focus-state) 

<span data-ttu-id="2e4a0-122">États de base near interaction :</span><span class="sxs-lookup"><span data-stu-id="2e4a0-122">Near Interaction Core States:</span></span>

- [<span data-ttu-id="2e4a0-123">Focus près</span><span class="sxs-lookup"><span data-stu-id="2e4a0-123">Focus Near</span></span>](#focus-near-state)
- [<span data-ttu-id="2e4a0-124">Interface tactile</span><span class="sxs-lookup"><span data-stu-id="2e4a0-124">Touch</span></span>](#touch-state)

<span data-ttu-id="2e4a0-125">États des cœurs d’interaction Far :</span><span class="sxs-lookup"><span data-stu-id="2e4a0-125">Far Interaction Core States:</span></span>
- [<span data-ttu-id="2e4a0-126">Focus à l’extrême</span><span class="sxs-lookup"><span data-stu-id="2e4a0-126">Focus Far</span></span>](#focus-far-state)
- [<span data-ttu-id="2e4a0-127">Sélectionnez Far</span><span class="sxs-lookup"><span data-stu-id="2e4a0-127">Select Far</span></span>](#select-far-state)

<span data-ttu-id="2e4a0-128">Autres États de base :</span><span class="sxs-lookup"><span data-stu-id="2e4a0-128">Other Core States:</span></span>
- [<span data-ttu-id="2e4a0-129">Clicked</span><span class="sxs-lookup"><span data-stu-id="2e4a0-129">Clicked</span></span>](#clicked-state)
- [<span data-ttu-id="2e4a0-130">Activer et désactiver</span><span class="sxs-lookup"><span data-stu-id="2e4a0-130">Toggle On and Toggle Off</span></span>](#toggle-on-and-toggle-off-state)
- [<span data-ttu-id="2e4a0-131">Mot clé Speech</span><span class="sxs-lookup"><span data-stu-id="2e4a0-131">Speech Keyword</span></span>](#speech-keyword-state)

### <a name="how-to-add-a-core-state-via-inspector"></a><span data-ttu-id="2e4a0-132">Ajout d’un état de base via Inspector</span><span class="sxs-lookup"><span data-stu-id="2e4a0-132">How to Add a Core State via Inspector</span></span>

1. <span data-ttu-id="2e4a0-133">Accédez à **Ajouter l’état principal** dans l’inspecteur pour l’élément interactif.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-133">Navigate to **Add Core State** in the inspector for Interactive Element.</span></span>

    ![Ajouter un état principal via Inspector](../images/interactive-element/InEditor/InteractiveElementAddCoreState.png)


1. <span data-ttu-id="2e4a0-135">Sélectionnez le bouton **Sélectionner l’État** pour choisir l’état principal à ajouter.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-135">Select the **Select State** button to choose the core state to add.</span></span> <span data-ttu-id="2e4a0-136">Les États dans le menu sont triés par type d’interaction.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-136">The states in the menu are sorted by interaction type.</span></span>

    ![Ajouter un état principal via Inspector avec l’état sélectionné](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectState.png)

1. <span data-ttu-id="2e4a0-138">Ouvrez la foldout configuration des événements pour afficher les événements et les propriétés associés à l’État.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-138">Open the Event Configuration foldout to view the events and properties associated with the state.</span></span>

    ![Ajouter un état principal via Inspector avec configuration d’événement](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectStateEventConfig.png)


### <a name="how-to-add-a-core-state-via-script"></a><span data-ttu-id="2e4a0-140">Comment ajouter un état principal via un script</span><span class="sxs-lookup"><span data-stu-id="2e4a0-140">How to Add a Core State via Script</span></span>

<span data-ttu-id="2e4a0-141">Utilisez la `AddNewState(stateName)` méthode pour ajouter un état de base.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-141">Use the `AddNewState(stateName)` method to add a core state.</span></span> <span data-ttu-id="2e4a0-142">Pour obtenir la liste des noms d’État principaux disponibles, utilisez l' `CoreInteractionState` énumération.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-142">For a list of the available core state names, use the `CoreInteractionState` enum.</span></span>

```c#
// Add by name or add by CoreInteractionState enum to string

interactiveElement.AddNewState("SelectFar");

interactiveElement.AddNewState(CoreInteractionState.SelectFar.ToString());
```

### <a name="states-internal-structure"></a><span data-ttu-id="2e4a0-143">Structure interne des États</span><span class="sxs-lookup"><span data-stu-id="2e4a0-143">States Internal Structure</span></span> 

<span data-ttu-id="2e4a0-144">Les États dans l’élément interactif sont de type `InteractionState` .</span><span class="sxs-lookup"><span data-stu-id="2e4a0-144">The states in Interactive Element are of type `InteractionState`.</span></span>  <span data-ttu-id="2e4a0-145">Un `InteractionState` contient les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="2e4a0-145">An `InteractionState` contains the following properties:</span></span>

- <span data-ttu-id="2e4a0-146">**Nom**: nom de l’État.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-146">**Name**: The name of the state.</span></span>
- <span data-ttu-id="2e4a0-147">**Valeur**: valeur d’État.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-147">**Value**: The state value.</span></span>  <span data-ttu-id="2e4a0-148">Si l’État est activé, la valeur d’État est 1.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-148">If the state is on, the state value is 1.</span></span> <span data-ttu-id="2e4a0-149">Si l’État est OFF, la valeur d’État est 0.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-149">If the state is off, the state value is 0.</span></span>
- <span data-ttu-id="2e4a0-150">**Actif**: indique si l’État est actuellement actif.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-150">**Active**: Whether or not the state is currently active.</span></span> <span data-ttu-id="2e4a0-151">La valeur de la propriété active est true lorsque l’État est activé, false si l’État est désactivé.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-151">The value for the Active property is true when the state is on, false if the state is off.</span></span> 
- <span data-ttu-id="2e4a0-152">**Type** d’interaction : le type d’interaction d’un État est le type d’interaction auquel un État est destiné.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-152">**Interaction Type**: The Interaction Type of a state is the type of interaction a state is intended for.</span></span> 
  - <span data-ttu-id="2e4a0-153">`None`: Ne prend en charge aucune forme d’interaction d’entrée.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-153">`None`: Does not support any form of input interaction.</span></span>
  - <span data-ttu-id="2e4a0-154">`Near`: Prise en charge de l’interaction proche.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-154">`Near`: Near interaction support.</span></span> <span data-ttu-id="2e4a0-155">L’entrée est considérée comme proche de l’interaction quand une main articulée a un contact direct avec un autre objet de jeu, c’est-à-dire la position que la main articulée est proche de la position de l’objet de jeu dans l’espace universel.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-155">Input is considered near interaction when an articulated hand has direct contact with another game object, i.e. the position the articulated hand is close to the position of the game object in world space.</span></span>
  - <span data-ttu-id="2e4a0-156">`Far`: Prise en charge de l’interaction Far.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-156">`Far`: Far interaction support.</span></span> <span data-ttu-id="2e4a0-157">L’entrée est considérée comme une interaction éloignée lorsque le contact direct avec l’objet de jeu n’est pas requis.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-157">Input is considered far interaction when direct contact with the game object is not required.</span></span> <span data-ttu-id="2e4a0-158">Par exemple, l’entrée via le rayon du contrôleur ou le point de regard est considérée comme une entrée d’interaction Far.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-158">For example, input via controller ray or gaze is considered far interaction input.</span></span>
  - <span data-ttu-id="2e4a0-159">`NearAndFar`: Englobe la prise en charge de l’interaction near et Far.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-159">`NearAndFar`: Encompasses both near and far interaction support.</span></span> 
  - <span data-ttu-id="2e4a0-160">`Other`: Prise en charge de l’interaction indépendante du pointeur.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-160">`Other`: Pointer independent interaction support.</span></span>
- <span data-ttu-id="2e4a0-161">**Configuration** de l’événement : la configuration de l’événement pour un État est le point d’entrée du profil des événements sérialisés.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-161">**Event Configuration**: The event configuration for a state is the serialized events profile entry point.</span></span> 

<span data-ttu-id="2e4a0-162">Toutes ces propriétés sont définies en interne dans l' `State Manager` élément interactif contenu dans.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-162">All of these properties are set internally in the `State Manager` contained in Interactive Element.</span></span> <span data-ttu-id="2e4a0-163">Pour la modification des États, utilisez les méthodes d’assistance suivantes :</span><span class="sxs-lookup"><span data-stu-id="2e4a0-163">For modification of states use the following helper methods:</span></span>

<span data-ttu-id="2e4a0-164">**Méthodes d’assistance de paramétrage d’État**</span><span class="sxs-lookup"><span data-stu-id="2e4a0-164">**State Setting Helper Methods**</span></span>

```c# 
// Get the InteractionState
interactiveElement.GetState("StateName");

// Set a state value to 1/on
interactiveElement.SetStateOn("StateName");

// Set a state value to 0/off
interactiveElement.SetStateOff("StateName");

// Check if a state is present in the state list
interactiveElement.IsStatePresent("StateName");

// Check whether or not a state is active
interactiveElement.IsStateActive("StateName");

// Add a new state to the state list
interactiveElement.AddNewState("StateName");

// Remove a state from the state list
interactiveElement.RemoveState("StateName");
```

<span data-ttu-id="2e4a0-165">L’obtention de la configuration d’événement d’un État est spécifique à l’État lui-même.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-165">Getting the event configuration of a state is specific to the state itself.</span></span> <span data-ttu-id="2e4a0-166">Chaque État de base a un type de configuration d’événement spécifique qui est décrit ci-dessous sous les sections décrivant chaque État de base.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-166">Each core state has a specific event configuration type which is outlined below under the sections describing each core state.</span></span>

<span data-ttu-id="2e4a0-167">Voici un exemple généralisé de l’obtention de la configuration d’événement d’un État :</span><span class="sxs-lookup"><span data-stu-id="2e4a0-167">Here is a generalized example of getting a state's event configuration:</span></span>

```c#
// T varies depending on the core state - the specific T's are specified under each of the core state sections
T stateNameEvents = interactiveElement.GetStateEvents<T>("StateName");
```

### <a name="default-state"></a><span data-ttu-id="2e4a0-168">État par défaut</span><span class="sxs-lookup"><span data-stu-id="2e4a0-168">Default State</span></span>

<span data-ttu-id="2e4a0-169">L’État par défaut est toujours présent sur un élément interactif.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-169">The Default state is always present on an Interactive Element.</span></span>  <span data-ttu-id="2e4a0-170">Cet État est actif uniquement lorsque tous les autres États ne sont pas actifs.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-170">This state will be active only when all other states are not active.</span></span>  <span data-ttu-id="2e4a0-171">Si un autre État devient actif, l’État par défaut est défini sur désactivé en interne.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-171">If any other state becomes active, then the Default state will be set to off internally.</span></span> 

<span data-ttu-id="2e4a0-172">Un élément interactif est initialisé avec les États par défaut et de focus présents dans la liste d’États.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-172">An Interactive Element is initialized with the Default and Focus states present in the state list.</span></span> <span data-ttu-id="2e4a0-173">L’État par défaut doit toujours être présent dans la liste d’État.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-173">The Default state always needs to be present in the state list.</span></span> 

#### <a name="getting-default-state-events"></a><span data-ttu-id="2e4a0-174">Obtention des événements d’État par défaut</span><span class="sxs-lookup"><span data-stu-id="2e4a0-174">Getting Default State Events</span></span>

<span data-ttu-id="2e4a0-175">Type de configuration d’événement pour l’État par défaut : `StateEvents`</span><span class="sxs-lookup"><span data-stu-id="2e4a0-175">Event configuration type for the Default State: `StateEvents`</span></span>

```c#
StateEvents defaultEvents = interactiveElement.GetStateEvents<StateEvents>("Default");

defaultEvents.OnStateOn.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Default State On");
});

defaultEvents.OnStateOff.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Default State Off");
});
```

### <a name="focus-state"></a><span data-ttu-id="2e4a0-176">État du focus</span><span class="sxs-lookup"><span data-stu-id="2e4a0-176">Focus State</span></span>

<span data-ttu-id="2e4a0-177">L’état du focus est un état d’interaction proche et éloigné qui peut être considéré comme la réalité mixte équivalente au pointage.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-177">The Focus state is a near and far interaction state that can be thought of as the mixed reality equivalent to hover.</span></span> <span data-ttu-id="2e4a0-178">Le facteur distinctif entre une interaction proche et éloignée pour l’état du focus est le type de pointeur actif actuel.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-178">The distinguishing factor between near and far interaction for the Focus state is the current active pointer type.</span></span>  <span data-ttu-id="2e4a0-179">Si le type de pointeur de l’état de focus est le pointeur d’action en avant, l’interaction est considérée comme proche de l’interaction.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-179">If the pointer type for the Focus state is the Poke Pointer, then the interaction is considered near interaction.</span></span>  <span data-ttu-id="2e4a0-180">Si le pointeur principal n’est pas le pointeur avant, l’interaction est considérée comme une interaction lointaine.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-180">If the primary pointer is not the Poke Pointer, then the interaction is considered far interaction.</span></span> <span data-ttu-id="2e4a0-181">L’état du focus est présent dans l’élément interactif par défaut.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-181">The Focus state is present in Interactive Element by default.</span></span>

<span data-ttu-id="2e4a0-182">Comportement de l' **État du focus** 
 ![ État du focus avec interaction de la main virtuelle](../images/interactive-element/InEditor/Gifs/FocusStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="2e4a0-182">**Focus State Behavior**
![Focus state with virtual hand interaction](../images/interactive-element/InEditor/Gifs/FocusStateEditor.gif)</span></span> 

<span data-ttu-id="2e4a0-183">**Focus de l’inspecteur** 
 ![ d’État État du focus dans le Inpsector](../images/interactive-element/InEditor/FocusStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="2e4a0-183">**Focus State Inspector**
![Focus state in the Inpsector](../images/interactive-element/InEditor/FocusStateInspector.png)</span></span>

#### <a name="getting-focus-state-events&quot;></a><span data-ttu-id=&quot;2e4a0-184&quot;>Obtention des événements d’État du focus</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;2e4a0-184&quot;>Getting Focus State Events</span></span>

<span data-ttu-id=&quot;2e4a0-185&quot;>Type de configuration d’événement pour l’état de Focus : `FocusEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;2e4a0-185&quot;>Event configuration type for the Focus State: `FocusEvents`</span></span>

```c#
FocusEvents focusEvents = interactiveElement.GetStateEvents<FocusEvents>(&quot;Focus");

focusEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Focus On");
});

focusEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Focus Off");
});
```

#### <a name="focus-near-vs-focus-far-behavior"></a><span data-ttu-id="2e4a0-186">Concentrez-vous sur le comportement Far</span><span class="sxs-lookup"><span data-stu-id="2e4a0-186">Focus Near vs Focus Far Behavior</span></span> 

![Concentrez-vous presque et loin avec l’interaction avec la main virtuelle](../images/interactive-element/InEditor/Gifs/FocusNearFocusFar.gif)

### <a name="focus-near-state"></a><span data-ttu-id="2e4a0-188">Focus sur l’état proche</span><span class="sxs-lookup"><span data-stu-id="2e4a0-188">Focus Near State</span></span>

<span data-ttu-id="2e4a0-189">L’État Focus near est défini lorsqu’un événement focus est déclenché et que le pointeur principal est le pointeur de la fenêtre d’action, une indication de Near interaction.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-189">The Focus Near state is set when a focus event is raised and the primary pointer is the Poke pointer, an indication of near interaction.</span></span> 

<span data-ttu-id="2e4a0-190">**Focus sur le comportement** 
 ![ de l’état proche Focus sur l’état près de l’interaction avec la main virtuelle](../images/interactive-element/InEditor/Gifs/FocusNearStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="2e4a0-190">**Focus Near State Behavior**
![Focus near state with virtual hand interaction](../images/interactive-element/InEditor/Gifs/FocusNearStateEditor.gif)</span></span> 

<span data-ttu-id="2e4a0-191">**Focus près de l’inspecteur** 
 ![ d’État Focus sur le composant dans l’inspecteur](../images/interactive-element/InEditor/FocusNearStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="2e4a0-191">**Focus Near State Inspector**
![Focus near component in the Inspector](../images/interactive-element/InEditor/FocusNearStateInspector.png)</span></span>

#### <a name="getting-focusnear-state-events&quot;></a><span data-ttu-id=&quot;2e4a0-192&quot;>Obtention des événements d’État FocusNear</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;2e4a0-192&quot;>Getting FocusNear State Events</span></span>

<span data-ttu-id=&quot;2e4a0-193&quot;>Type de configuration d’événement pour l’État FocusNear : `FocusEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;2e4a0-193&quot;>Event configuration type for the FocusNear State: `FocusEvents`</span></span>

```c#
FocusEvents focusNearEvents = interactiveElement.GetStateEvents<FocusEvents>(&quot;FocusNear");

focusNearEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Near Interaction Focus On");
});

focusNearEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Near Interaction Focus Off");
});
```

### <a name="focus-far-state"></a><span data-ttu-id="2e4a0-194">Activer l’État Far</span><span class="sxs-lookup"><span data-stu-id="2e4a0-194">Focus Far State</span></span>

<span data-ttu-id="2e4a0-195">L’État Focus actif est défini lorsque le pointeur principal n’est pas le pointeur de l’e-out.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-195">The Focus Far state is set when the primary pointer is not the Poke pointer.</span></span>  <span data-ttu-id="2e4a0-196">Par exemple, le pointeur Ray du contrôleur par défaut et le pointeur GGV (point d’interligne, voix) sont considérés comme des pointeurs d’interaction Far.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-196">For example, the default controller ray pointer and the GGV (Gaze, Gesture, Voice) pointer are considered far interaction pointers.</span></span>

<span data-ttu-id="2e4a0-197">**Focus sur le comportement** 
 ![ d’État Far Focalisation de l’état avec l’interaction avec la main virtuelle](../images/interactive-element/InEditor/Gifs/FocusFarStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="2e4a0-197">**Focus Far State Behavior**
![Focus state far with virtual hand interaction](../images/interactive-element/InEditor/Gifs/FocusFarStateEditor.gif)</span></span>

<span data-ttu-id="2e4a0-198">**Activer l’inspecteur** 
 ![ d’État Far Focus sur le composant dans l’inspecteur](../images/interactive-element/InEditor/FocusFarStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="2e4a0-198">**Focus Far State Inspector**
![Focus far component in the Inspector](../images/interactive-element/InEditor/FocusFarStateInspector.png)</span></span>

#### <a name="getting-focus-far-state-events&quot;></a><span data-ttu-id=&quot;2e4a0-199&quot;>Obtention d’événements d’état de focus Far</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;2e4a0-199&quot;>Getting Focus Far State Events</span></span>

<span data-ttu-id=&quot;2e4a0-200&quot;>Type de configuration d’événement pour l’État FocusFar : `FocusEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;2e4a0-200&quot;>Event configuration type for the FocusFar State: `FocusEvents`</span></span>

```c#
FocusEvents focusFarEvents = interactiveElement.GetStateEvents<FocusEvents>(&quot;FocusFar");

focusFarEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Focus On");
});

focusFarEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Focus Off");
});
```

### <a name="touch-state"></a><span data-ttu-id="2e4a0-201">État tactile</span><span class="sxs-lookup"><span data-stu-id="2e4a0-201">Touch State</span></span>

<span data-ttu-id="2e4a0-202">L’État tactile est un état d’interaction proche qui est défini lorsqu’une main articulée touche l’objet directement.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-202">The Touch state is a near interaction state that is set when an articulated hand touches the object directly.</span></span>  <span data-ttu-id="2e4a0-203">Une pression tactile directe signifie que le doigt de l’index articulé est très proche de la position universelle de l’objet.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-203">A direct touch means that the articulated hand's index finger is very close to the world position of the object.</span></span> <span data-ttu-id="2e4a0-204">Par défaut, un `NearInteractionTouchableVolume` composant est attaché à l’objet si l’État tactile est ajouté à la liste d’États.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-204">By default, a `NearInteractionTouchableVolume` component is attached to the object if the Touch state is added to the the state list.</span></span>  <span data-ttu-id="2e4a0-205">La présence d’un  `NearInteractionTouchableVolume` `NearInteractionTouchable` composant ou est requise pour la détection des événements tactiles.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-205">The presence of a  `NearInteractionTouchableVolume` or `NearInteractionTouchable` component is required for detecting Touch events.</span></span>  <span data-ttu-id="2e4a0-206">La différence entre `NearInteractionTouchableVolume` et `NearInteractionTouchable` est que `NearInteractionTouchableVolume` détecte une pression tactile basée sur le conflit de l’objet et `NearInteractionTouchable` détecte une pression tactile dans une zone définie d’un plan.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-206">The difference between `NearInteractionTouchableVolume` and `NearInteractionTouchable` is that `NearInteractionTouchableVolume` detects a touch based on the collider of the object and `NearInteractionTouchable`detects touch within a defined area of a plane.</span></span>

<span data-ttu-id="2e4a0-207"> 
 Comportement ![ de Touch State État tactile avec interaction avec la main virtuelle](../images/interactive-element/InEditor/Gifs/TouchStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="2e4a0-207">**Touch State Behavior**
![Touch state with virtual hand interaction](../images/interactive-element/InEditor/Gifs/TouchStateEditor.gif)</span></span>

<span data-ttu-id="2e4a0-208"> 
 Inspecteur ![ d’État tactile Composant d’État tactile dans l’inspecteur](../images/interactive-element/InEditor/TouchStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="2e4a0-208">**Touch State Inspector**
![Touch state component in the Inspector](../images/interactive-element/InEditor/TouchStateInspector.png)</span></span>

#### <a name="getting-touch-state-events&quot;></a><span data-ttu-id=&quot;2e4a0-209&quot;>Obtention d’événements d’État tactile</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;2e4a0-209&quot;>Getting Touch State Events</span></span>

<span data-ttu-id=&quot;2e4a0-210&quot;>Type de configuration d’événement pour l’État tactile : `TouchEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;2e4a0-210&quot;>Event configuration type for the Touch State: `TouchEvents`</span></span>

```c#
TouchEvents touchEvents = interactiveElement.GetStateEvents<TouchEvents>(&quot;Touch");

touchEvents.OnTouchStarted.AddListener((touchData) =>
{
    Debug.Log($"{gameObject.name} Touch Started");
});

touchEvents.OnTouchCompleted.AddListener((touchData) =>
{
    Debug.Log($"{gameObject.name} Touch Completed");
});

touchEvents.OnTouchUpdated.AddListener((touchData) =>
{
    Debug.Log($"{gameObject.name} Touch Updated");
});
```

### <a name="select-far-state"></a><span data-ttu-id="2e4a0-211">Sélectionner l’État Far</span><span class="sxs-lookup"><span data-stu-id="2e4a0-211">Select Far State</span></span>

<span data-ttu-id="2e4a0-212">L’état de sélection FAR est `IMixedRealityPointerHandler` surfaced.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-212">The Select Far state is the `IMixedRealityPointerHandler` surfaced.</span></span>  <span data-ttu-id="2e4a0-213">Cet État est un état d’interaction beaucoup plus éloigné qui détecte l’interaction avec le clic (air-TAP) et maintient à travers l’utilisation de pointeurs d’interaction Far tels que le pointeur de rayon du contrôleur par défaut ou le pointeur GGV.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-213">This state is a far interaction state that detects far interaction click (air-tap) and holds through the use of far interaction pointers such as the default controller ray pointer or the GGV pointer.</span></span>  <span data-ttu-id="2e4a0-214">L’option de sélection de l’État Far a une option sous le foldout de configuration d’événement nommé `Global` .</span><span class="sxs-lookup"><span data-stu-id="2e4a0-214">The Select Far state has an option under the event configuration foldout named `Global`.</span></span> <span data-ttu-id="2e4a0-215">Si `Global` a la valeur true, le `IMixedRealityPointerHandler` est inscrit en tant que gestionnaire d’entrée global.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-215">If `Global` is true, then the `IMixedRealityPointerHandler` is registered as a global input handler.</span></span>  <span data-ttu-id="2e4a0-216">Il n’est pas nécessaire de se concentrer sur un objet pour déclencher des événements du système d’entrée si un gestionnaire est inscrit en tant que global.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-216">Focus on an object is not required to trigger input system events if a handler is registered as global.</span></span>  <span data-ttu-id="2e4a0-217">Par exemple, si un utilisateur souhaite savoir à quel moment le mouvement air-TAP/Select est effectué indépendamment de l’objet actif, définissez `Global` sur true.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-217">For example, if a user wants to know anytime the air-tap/select gesture is performed regardless of the object in focus, set `Global` to true.</span></span> 

<span data-ttu-id="2e4a0-218">**Sélectionner le comportement** 
 ![ de l’État Far Sélectionnez bien avec l’interaction avec la main virtuelle](../images/interactive-element/InEditor/Gifs/SelectFarStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="2e4a0-218">**Select Far State Behavior**
![Select far with virtual hand interaction](../images/interactive-element/InEditor/Gifs/SelectFarStateEditor.gif)</span></span>

<span data-ttu-id="2e4a0-219">**Sélectionner l’inspecteur** 
 ![ d’État Far Sélectionner le composant Far dans l’inspecteur](../images/interactive-element/InEditor/SelectFarStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="2e4a0-219">**Select Far State Inspector**
![Select far component in the Inspector](../images/interactive-element/InEditor/SelectFarStateInspector.png)</span></span>

#### <a name="getting-select-far-state-events&quot;></a><span data-ttu-id=&quot;2e4a0-220&quot;>Obtention d’événements d’état de sélection Far</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;2e4a0-220&quot;>Getting Select Far State Events</span></span>

<span data-ttu-id=&quot;2e4a0-221&quot;>Type de configuration d’événement pour l’État SelectFar : `SelectFarEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;2e4a0-221&quot;>Event configuration type for the SelectFar State: `SelectFarEvents`</span></span>

```c#
SelectFarEvents selectFarEvents = interactiveElement.GetStateEvents<SelectFarEvents>(&quot;SelectFar");

selectFarEvents.OnSelectUp.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Up");
});

selectFarEvents.OnSelectDown.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Down");
});

selectFarEvents.OnSelectHold.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Hold");
});

selectFarEvents.OnSelectClicked.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Clicked");
});
```

### <a name="clicked-state"></a><span data-ttu-id="2e4a0-222">État de clic</span><span class="sxs-lookup"><span data-stu-id="2e4a0-222">Clicked State</span></span>

<span data-ttu-id="2e4a0-223">L’état de clic est déclenché par un clic d’interaction Far (sélectionner l’État FAR) par défaut.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-223">The Clicked state is triggered by a far interaction click (Select Far state) by default.</span></span>  <span data-ttu-id="2e4a0-224">Cet État est activé en interne, appelle l’événement OnClicked, puis est immédiatement désactivé.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-224">This state is internally switched to on, invokes the OnClicked event and then is immediately switched to off.</span></span> 

> [!NOTE]
> <span data-ttu-id="2e4a0-225">Les commentaires visuels dans l’inspecteur en fonction de l’activité d’État ne sont pas présents pour l’état de clic, car ils sont activés et désactivés immédiatement.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-225">The visual feedback in the inspector based on state activity is not present for the Clicked state because it is switched on and then off immediately.</span></span> 

<span data-ttu-id="2e4a0-226">Comportement de l' **État de clic** 
 ![ État de clic avec interactions de la main virtuelle](../images/interactive-element/InEditor/Gifs/ClickedStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="2e4a0-226">**Clicked State Behavior**
![Clicked state with virtual hand interactions](../images/interactive-element/InEditor/Gifs/ClickedStateEditor.gif)</span></span>

<span data-ttu-id="2e4a0-227"> 
 Inspecteur ![ d’État cliqué Cliquer sur le composant État dans l’inspecteur](../images/interactive-element/InEditor/ClickedStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="2e4a0-227">**Clicked State Inspector**
![Click state component in the Inspector](../images/interactive-element/InEditor/ClickedStateInspector.png)</span></span>

<span data-ttu-id="2e4a0-228">**Exemple d’État near et Far cliqué**</span><span class="sxs-lookup"><span data-stu-id="2e4a0-228">**Near and Far Clicked State Example**</span></span>  
<span data-ttu-id="2e4a0-229">L’état de clic peut être déclenché via des points d’entrée supplémentaires à l’aide de la `interactiveElement.TriggerClickedState()` méthode.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-229">The clicked state can be triggered through additional entry points using the `interactiveElement.TriggerClickedState()` method.</span></span>  <span data-ttu-id="2e4a0-230">Par exemple, si un utilisateur souhaite une touche near interaction pour déclencher un clic sur un objet également, il ajoute la `TriggerClickedState()` méthode en tant qu’écouteur dans l’État tactile.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-230">For example, if a user wants a near interaction touch to trigger a click on an object as well, then they would add the `TriggerClickedState()` method as a listener in the touch state.</span></span>   

![État near et Far avec interactions avec la main virtuelle](../images/interactive-element/InEditor/Gifs/NearFarClickedState.gif)

#### <a name="getting-clicked-state-events&quot;></a><span data-ttu-id=&quot;2e4a0-232&quot;>Obtention des événements d’état de clic</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;2e4a0-232&quot;>Getting Clicked State Events</span></span>

<span data-ttu-id=&quot;2e4a0-233&quot;>Type de configuration d’événement pour l’état de clic : `ClickedEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;2e4a0-233&quot;>Event configuration type for the Clicked State: `ClickedEvents`</span></span>

```c#
ClickedEvents clickedEvent = interactiveElement.GetStateEvents<ClickedEvents>(&quot;Clicked");

clickedEvent.OnClicked.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Clicked");
});
```

### <a name="toggle-on-and-toggle-off-state"></a><span data-ttu-id="2e4a0-234">Activer et désactiver l’État</span><span class="sxs-lookup"><span data-stu-id="2e4a0-234">Toggle On and Toggle Off state</span></span>

<span data-ttu-id="2e4a0-235">Les États de basculement et de basculement sont une paire et doivent tous les deux être présents pour le comportement de basculement.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-235">The Toggle On and Toggle Off states are a pair and both need to be present for toggle behavior.</span></span>  <span data-ttu-id="2e4a0-236">Par défaut, les États activer/désactiver les basculements sont déclenchés à l’aide d’un clic d’interaction Far (sélectionnez l’État FAR).</span><span class="sxs-lookup"><span data-stu-id="2e4a0-236">By default, the Toggle On and Toggle Off states are triggered through a far interaction click (Select Far state).</span></span>  <span data-ttu-id="2e4a0-237">Par défaut, l’état de basculement est actif au démarrage, ce qui signifie que le basculement sera initialisé à OFF.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-237">By default, the Toggle Off state is active on start, meaning that the toggle will be initialized to off.</span></span>  <span data-ttu-id="2e4a0-238">Si un utilisateur souhaite activer l’État basculer sur actif au démarrage, dans l’État basculer sur défini sur `IsSelectedOnStart` true.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-238">If a user wants the Toggle On state to be active on start, then in the Toggle On state set `IsSelectedOnStart` to true.</span></span>

<span data-ttu-id="2e4a0-239">**ToggleOn et activer/désactiver le comportement** 
 ![ de l’État Activer et désactiver les interactions avec la main virtuelle](../images/interactive-element/InEditor/Gifs/ToggleOnToggleOffStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="2e4a0-239">**ToggleOn and Toggle Off State Behavior**
![Toggle on and off with virtual hand interactions](../images/interactive-element/InEditor/Gifs/ToggleOnToggleOffStateEditor.gif)</span></span>

<span data-ttu-id="2e4a0-240">**ToggleOn et activer/désactiver l’inspecteur** 
 ![ d’État Basculer le composant dans l’inspecteur](../images/interactive-element/InEditor/ToggleOnToggleOffStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="2e4a0-240">**ToggleOn and Toggle Off State Inspector**
![Toggle component in the Inspector](../images/interactive-element/InEditor/ToggleOnToggleOffStateInspector.png)</span></span>

<span data-ttu-id="2e4a0-241">**Exemple d’États de basculement near et Far**</span><span class="sxs-lookup"><span data-stu-id="2e4a0-241">**Near and Far Toggle States Example**</span></span>  
<span data-ttu-id="2e4a0-242">À l’instar de l’État cliqué, le paramètre basculer l’État peut avoir plusieurs points d’entrée à l’aide de la `interactiveElement.SetToggleStates()` méthode.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-242">Similar to the Clicked state, toggle state setting can have multiple entry points using the `interactiveElement.SetToggleStates()` method.</span></span> <span data-ttu-id="2e4a0-243">Par exemple, si un utilisateur souhaite toucher en tant que point d’entrée supplémentaire pour définir les États de basculement, il ajoute la `SetToggleStates()` méthode à l’un des événements à l’État tactile.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-243">For example, if a user wants touch as an additional entry point to set the toggle states, then they add the `SetToggleStates()` method to one of the events in the Touch state.</span></span> 

![Bascule presque et Far avec les interactions de la main virtuelle](../images/interactive-element/InEditor/Gifs/NearFarToggleStates.gif)

#### <a name="getting-toggle-on-and-toggle-off-state-events&quot;></a><span data-ttu-id=&quot;2e4a0-245&quot;>Activation et désactivation des événements d’État</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;2e4a0-245&quot;>Getting Toggle On and Toggle Off State Events</span></span>

<span data-ttu-id=&quot;2e4a0-246&quot;>Type de configuration d’événement pour l’État ToggleOn : `ToggleOnEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;2e4a0-246&quot;>Event configuration type for the ToggleOn State: `ToggleOnEvents`</span></span>  
<span data-ttu-id=&quot;2e4a0-247&quot;>Type de configuration d’événement pour l’État ToggleOff : `ToggleOffEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;2e4a0-247&quot;>Event configuration type for the ToggleOff State: `ToggleOffEvents`</span></span>

```c#
// Toggle On Events
ToggleOnEvents toggleOnEvent = interactiveElement.GetStateEvents<ToggleOnEvents>(&quot;ToggleOn");

toggleOnEvent.OnToggleOn.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Toggled On");
});

// Toggle Off Events
ToggleOffEvents toggleOffEvent = interactiveElement.GetStateEvents<ToggleOffEvents>("ToggleOff");

toggleOffEvent.OnToggleOff.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Toggled Off");
});
```

### <a name="speech-keyword-state"></a><span data-ttu-id="2e4a0-248">État du mot clé Speech</span><span class="sxs-lookup"><span data-stu-id="2e4a0-248">Speech Keyword State</span></span>

<span data-ttu-id="2e4a0-249">L’état du mot clé Speech écoute les mots clés définis dans le profil de voix de la réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-249">The Speech Keyword state listens for the keywords defined in the Mixed Reality Speech Profile.</span></span> <span data-ttu-id="2e4a0-250">Tout nouveau mot clé doit être enregistré dans le profil de commande vocale avant l’exécution (étapes ci-dessous).</span><span class="sxs-lookup"><span data-stu-id="2e4a0-250">Any new keyword MUST be registered in the speech command profile prior to runtime (steps below).</span></span> 

<span data-ttu-id="2e4a0-251">Comportement de l' **État des mots clés Speech** 
 ![ Mot clé Speech avec interaction virtuelle](../images/interactive-element/InEditor/Gifs/SpeechKeywordStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="2e4a0-251">**Speech Keyword State Behavior**
![Speech keyword with virtual interaction](../images/interactive-element/InEditor/Gifs/SpeechKeywordStateEditor.gif)</span></span>

<span data-ttu-id="2e4a0-252">Inspecteur d’état de **mot clé Speech** 
 ![ Composant de mot clé Speech dans l’inspecteur](../images/interactive-element/InEditor/SpeechKeywordStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="2e4a0-252">**Speech Keyword State Inspector**
![Speech keyword component in the Inspector](../images/interactive-element/InEditor/SpeechKeywordStateInspector.png)</span></span>

> [!NOTE]
> <span data-ttu-id="2e4a0-253">L’état du mot clé Speech a été déclenché dans l’éditeur en appuyant sur la touche F5 dans le GIF ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-253">The Speech Keyword state was triggered in editor by pressing the F5 key in the gif above.</span></span> <span data-ttu-id="2e4a0-254">La configuration dans l’éditeur de test pour la reconnaissance vocale est décrite dans les étapes ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-254">Setting up in editor testing for speech is outlined the steps below.</span></span> 

#### <a name="how-to-register-a-speech-commandkeyword"></a><span data-ttu-id="2e4a0-255">Comment inscrire une commande/un mot clé Speech</span><span class="sxs-lookup"><span data-stu-id="2e4a0-255">How to Register a Speech Command/Keyword</span></span>

1. <span data-ttu-id="2e4a0-256">Sélectionner l’objet de jeu **MixedRealityToolkit**</span><span class="sxs-lookup"><span data-stu-id="2e4a0-256">Select the **MixedRealityToolkit** game object</span></span>

1. <span data-ttu-id="2e4a0-257">Sélectionner **copier et personnaliser** le profil actuel</span><span class="sxs-lookup"><span data-stu-id="2e4a0-257">Select **Copy and Customize** the current profile</span></span>

1. <span data-ttu-id="2e4a0-258">Accédez à la section entrée et sélectionnez **clone** pour permettre la modification du profil d’entrée.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-258">Navigate to the Input section and select **Clone** to enable modification of the Input profile</span></span>

1. <span data-ttu-id="2e4a0-259">Faites défiler jusqu’à la section Speech du profil d’entrée et clonez le profil de reconnaissance vocale.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-259">Scroll down to the Speech section in the Input profile and clone the Speech Profile</span></span>

    ![Profil de mot clé Speech dans l’objet de jeu MRTK](../images/interactive-element/InEditor/SpeechKeywordProfileClone.png) 

1. <span data-ttu-id="2e4a0-261">Sélectionnez Ajouter une nouvelle commande vocale</span><span class="sxs-lookup"><span data-stu-id="2e4a0-261">Select Add a New Speech Command</span></span>

    ![Ajout d’un nouveau mot clé Speech dans le profil MRTK](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeyword.png) 

1. <span data-ttu-id="2e4a0-263">Entrez le mot clé New.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-263">Enter the new keyword.</span></span> <span data-ttu-id="2e4a0-264">Facultatif : remplacez keycode par F5 (ou un autre keycode) pour permettre le test dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-264">Optional: Change the KeyCode to F5 (or another KeyCode) to allow for testing in editor.</span></span> 

    ![Configuration du mot clé Speech dans le profil MRTK](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeywordName.png) 

1. <span data-ttu-id="2e4a0-266">Revenez à l’inspecteur d’état des mots clés Speech des éléments interactifs et sélectionnez **Ajouter un mot clé**</span><span class="sxs-lookup"><span data-stu-id="2e4a0-266">Go back to the Interactive Element Speech Keyword state inspector and select **Add Keyword**</span></span> 

    ![Ajout du mot clé au composant d’élément interactif](../images/interactive-element/InEditor/SpeechKeywordAddKeyword.png) 

    ![Validation et enregistrement des mots clés](../images/interactive-element/InEditor/SpeechKeywordAddKeywordBlank.png) 

1. <span data-ttu-id="2e4a0-269">Entrez le nouveau mot clé qui vient d’être enregistré dans le profil de voix</span><span class="sxs-lookup"><span data-stu-id="2e4a0-269">Enter the new keyword that was just registered in the Speech Profile</span></span>

    ![Saisie du nouveau mot clé Speech](../images/interactive-element/InEditor/SpeechKeywordEnterKeyword.png) 


<span data-ttu-id="2e4a0-271">Pour tester l’état du mot clé Speech dans l’éditeur, appuyez sur la touche de code définie à l’étape 6 (F5) pour simuler l’événement reconnu par mot clé Speech.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-271">To test the Speech Keyword state in editor, press the KeyCode that was defined in step 6 (F5) to simulate the speech keyword recognized event.</span></span>

#### <a name="getting-speech-keyword-state-events"></a><span data-ttu-id="2e4a0-272">Obtention d’événements d’état de mot clé Speech</span><span class="sxs-lookup"><span data-stu-id="2e4a0-272">Getting Speech Keyword State Events</span></span>

<span data-ttu-id="2e4a0-273">Type de configuration d’événement pour l’État SpeechKeyword : `SpeechKeywordEvents`</span><span class="sxs-lookup"><span data-stu-id="2e4a0-273">Event configuration type for the SpeechKeyword State: `SpeechKeywordEvents`</span></span>

```c#
SpeechKeywordEvents speechKeywordEvents = interactiveElement.GetStateEvents<SpeechKeywordEvents>("SpeechKeyword");

speechKeywordEvents.OnAnySpeechKeywordRecognized.AddListener((speechEventData) =>
{
    Debug.Log($"{speechEventData.Command.Keyword} recognized");
});

// Get the "Change" Keyword event specifically
KeywordEvent keywordEvent = speechKeywordEvents.Keywords.Find((keyword) => keyword.Keyword == "Change");

keywordEvent.OnKeywordRecognized.AddListener(() =>
{ 
    Debug.Log("Change Keyword Recognized"); 
});
```

## <a name="custom-states"></a><span data-ttu-id="2e4a0-274">États personnalisés</span><span class="sxs-lookup"><span data-stu-id="2e4a0-274">Custom States</span></span>

### <a name="how-to-create-a-custom-state-via-inspector"></a><span data-ttu-id="2e4a0-275">Comment créer un état personnalisé via Inspector</span><span class="sxs-lookup"><span data-stu-id="2e4a0-275">How to Create a Custom State via Inspector</span></span> 

<span data-ttu-id="2e4a0-276">L’état personnalisé créé via Inspector sera initialisé avec la configuration d’événement d’État par défaut.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-276">The custom state created via inspector will be initialized with the default state event configuration.</span></span> <span data-ttu-id="2e4a0-277">La configuration d’événement par défaut pour un état personnalisé est de type `StateEvents` et contient les événements OnStateOn et OnStateOff.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-277">The default event configuration for a custom state is of type `StateEvents` and contains the OnStateOn and OnStateOff events.</span></span>

1. <span data-ttu-id="2e4a0-278">Accédez à **créer un état personnalisé** dans l’inspecteur pour l’élément interactif.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-278">Navigate to **Create Custom State** in the inspector for Interactive Element.</span></span>
    
    ![Création d’un état personnalisé](../images/interactive-element/InEditor/InteractiveElementCreateCustomState.png)

1. <span data-ttu-id="2e4a0-280">Entrez le nom du nouvel État.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-280">Enter the name of the new state.</span></span> <span data-ttu-id="2e4a0-281">Ce nom doit être unique et ne peut pas être le même que les États de base existants.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-281">This name must be unique and cannot be the same as the existing core states.</span></span> 
    
    ![Saisie du nom d’un nouvel état personnalisé](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateName.png)

1. <span data-ttu-id="2e4a0-283">Sélectionnez **définir le nom** de l’État à ajouter à la liste d’États.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-283">Select **Set State Name** to add to the state list.</span></span>
    
    ![Ajouter un état personnalisé à la liste des États](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateNameSet.png)

   <span data-ttu-id="2e4a0-285">Cet état personnalisé est initialisé avec la configuration d' `StateEvents` événement par défaut qui contient `OnStateOn` les `OnStateOff` événements et.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-285">This custom state is initialized with the default `StateEvents` event configuration which contains the `OnStateOn` and `OnStateOff` events.</span></span> <span data-ttu-id="2e4a0-286">Pour créer une configuration d’événement personnalisée pour un nouvel État, consultez : [création d’un état personnalisé avec une configuration d’événement personnalisée](#creating-a-custom-state-with-a-custom-event-configuration).</span><span class="sxs-lookup"><span data-stu-id="2e4a0-286">To create a custom event configuration for a new state see: [Creating a Custom State with a Custom Event Configuration](#creating-a-custom-state-with-a-custom-event-configuration).</span></span>
    
    ![Nouvel état affiché dans le composant d’élément interactif](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateEventConfig.png)


### <a name="how-to-create-a-custom-state-via-script&quot;></a><span data-ttu-id=&quot;2e4a0-288&quot;>Comment créer un état personnalisé à l’aide d’un script</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;2e4a0-288&quot;>How to Create a Custom State via Script</span></span>

```c#
interactiveElement.AddNewState(&quot;MyNewState");

// A new state by default is initialized with a the default StateEvents configuration which contains the 
// OnStateOn and OnStateOff events

StateEvents myNewStateEvents = interactiveElement.GetStateEvents<StateEvents>("MyNewState");

myNewStateEvents.OnStateOn.AddListener(() =>
{
    Debug.Log($"MyNewState is On");
});

```

### <a name="creating-a-custom-state-with-a-custom-event-configuration"></a><span data-ttu-id="2e4a0-289">Création d’un état personnalisé avec une configuration d’événement personnalisée</span><span class="sxs-lookup"><span data-stu-id="2e4a0-289">Creating a Custom State with a Custom Event Configuration</span></span> 

<span data-ttu-id="2e4a0-290">Des exemples de fichiers pour un état personnalisé nommé **Keyboard** sont disponibles ici : MRTK\SDK\Experimental\InteractiveElement\Examples\Scripts\CustomStateExample</span><span class="sxs-lookup"><span data-stu-id="2e4a0-290">Example files for a custom state named **Keyboard** are located here: MRTK\SDK\Experimental\InteractiveElement\Examples\Scripts\CustomStateExample</span></span>

<span data-ttu-id="2e4a0-291">Les étapes suivantes décrivent un exemple de création de fichiers de configuration et de récepteur d’événement d’état personnalisé.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-291">The following steps walk through an existing example of creating a custom state event configuration and receiver files.</span></span>

1. <span data-ttu-id="2e4a0-292">Imaginez un nom d’État.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-292">Think of a state name.</span></span>  <span data-ttu-id="2e4a0-293">Ce nom doit être unique et ne peut pas être le même que les États de base existants.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-293">This name must be unique and cannot be the same as the existing core states.</span></span> <span data-ttu-id="2e4a0-294">Dans le cadre de cet exemple, le nom d’État est le **clavier**.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-294">For the purposes of this example, the state name is going to be **Keyboard**.</span></span>

1. <span data-ttu-id="2e4a0-295">Créez deux fichiers. cs nommés State Name + « Receiver » et State Name + « Events ».</span><span class="sxs-lookup"><span data-stu-id="2e4a0-295">Create two .cs files named state name + "Receiver" and state name + "Events".</span></span> <span data-ttu-id="2e4a0-296">L’attribution de noms à ces fichiers est prise en compte en interne et doit suivre le nom d’État + Convention Event/Receiver.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-296">The naming of these files are taken into consideration internally and must follow the state name + Event/Receiver convention.</span></span> 

    ![Scripts d’État du clavier](../images/interactive-element/InEditor/KeyboardStateFiles.png)

1. <span data-ttu-id="2e4a0-298">Pour plus d’informations sur le contenu des fichiers, consultez les fichiers KeyboardEvents. cs et KeyboardReceiver. cs.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-298">See the KeyboardEvents.cs and KeyboardReceiver.cs files for more details on file contents.</span></span> <span data-ttu-id="2e4a0-299">Les nouvelles classes de configuration d’événement doivent hériter de `BaseInteractionEventConfiguration` et de nouvelles classes de récepteur d’événements doivent hériter de `BaseEventReceiver` .</span><span class="sxs-lookup"><span data-stu-id="2e4a0-299">New event configuration classes must inherit from `BaseInteractionEventConfiguration` and new event receiver classes must inherit from `BaseEventReceiver`.</span></span>  <span data-ttu-id="2e4a0-300">Des exemples sur le paramètre d’état de l’état du clavier se trouvent dans le `CustomStateSettingExample.cs` fichier.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-300">Examples on state setting for the Keyboard state are located in the `CustomStateSettingExample.cs` file.</span></span> 

1. <span data-ttu-id="2e4a0-301">Ajoutez l’État à l’élément interactif en utilisant le nom d’État, le nom d’État sera reconnu si les fichiers de configuration d’événement et de récepteur d’événements existent.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-301">Add the state to Interactive Element using the state name, the state name will be recognized if event configuration and event receiver files exist.</span></span>  <span data-ttu-id="2e4a0-302">Les propriétés du fichier de configuration d’événement personnalisé doivent apparaître dans l’inspecteur.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-302">The properties in the custom event configuration file should appear in the inspector.</span></span>

    <span data-ttu-id="2e4a0-303">![Ajout d’un état personnalisé à un élément interactif ](../images/interactive-element/InEditor/AddKeyboardState.png) ![ état personnalisé reconnu dans l’élément interactif](../images/interactive-element/InEditor/SetKeyboardStateName.png)</span><span class="sxs-lookup"><span data-stu-id="2e4a0-303">![Adding custom state to interactive element](../images/interactive-element/InEditor/AddKeyboardState.png) ![Custom state recognized in the interactive element](../images/interactive-element/InEditor/SetKeyboardStateName.png)</span></span>


1. <span data-ttu-id="2e4a0-304">Pour obtenir plus d’exemples de configuration d’événements et de fichiers de récepteur d’événements, consultez les fichiers sur ces chemins d’accès :</span><span class="sxs-lookup"><span data-stu-id="2e4a0-304">For more examples of event configuration and event receiver files see the files at these paths:</span></span>    
- <span data-ttu-id="2e4a0-305">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventConfigurations</span><span class="sxs-lookup"><span data-stu-id="2e4a0-305">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventConfigurations</span></span>
- <span data-ttu-id="2e4a0-306">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventReceivers</span><span class="sxs-lookup"><span data-stu-id="2e4a0-306">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventReceivers</span></span>

## <a name="example-scene"></a><span data-ttu-id="2e4a0-307">Exemple de scène</span><span class="sxs-lookup"><span data-stu-id="2e4a0-307">Example Scene</span></span> 

<span data-ttu-id="2e4a0-308">L’exemple de scène pour l’élément interactif + visualiseur d’État se trouve ici : MRTK\SDK\Experimental\InteractiveElement\Examples\InteractiveElementExampleScene.unity</span><span class="sxs-lookup"><span data-stu-id="2e4a0-308">The example scene for Interactive Element + State Visualizer is located here: MRTK\SDK\Experimental\InteractiveElement\Examples\InteractiveElementExampleScene.unity</span></span>

![Exemple de scène avec élément interactif et visualiseur d’État](../images/interactive-element/InEditor/ExampleScene.png)

### <a name="compressable-button"></a><span data-ttu-id="2e4a0-310">Bouton compresseable</span><span class="sxs-lookup"><span data-stu-id="2e4a0-310">Compressable Button</span></span>

<span data-ttu-id="2e4a0-311">L’exemple de scène contient prefabs nommé `CompressableButton` et `CompressableButtonToggle` , ces prefabs reflètent le comportement des `PressableButtonHoloLens2` boutons, qui sont construits à l’aide de l’élément interactif et du visualiseur d’État.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-311">The example scene contains prefabs named `CompressableButton` and `CompressableButtonToggle`, these prefabs mirror the behavior of the `PressableButtonHoloLens2` buttons, that are constructed using Interactive Element and the State Visualizer.</span></span> <span data-ttu-id="2e4a0-312">Le `CompressableButton` composant est actuellement une combinaison de `PressableButton`  +  `PressableButtonHoloLens2` avec `BaseInteractiveElement` en tant que classe de base.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-312">The `CompressableButton` component is currently a combination of `PressableButton` + `PressableButtonHoloLens2` with `BaseInteractiveElement`as a base class.</span></span> 

## <a name="state-visualizer-experimental"></a><span data-ttu-id="2e4a0-313">Visualiseur d’État [expérimental]</span><span class="sxs-lookup"><span data-stu-id="2e4a0-313">State Visualizer [Experimental]</span></span>

<span data-ttu-id="2e4a0-314">Le composant visualiseur d’État ajoute des animations à un objet en fonction des États définis dans un composant d’élément interactif lié.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-314">The State Visualizer component adds animations to an object based on the states defined in a linked Interactive Element component.</span></span> <span data-ttu-id="2e4a0-315">Ce composant crée des ressources d’animation, les place dans le dossier MixedRealityToolkit. generated et active le paramètre d’image clé d’animation simplifiée via l’ajout de propriétés animables à un objet de jeu cible.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-315">This component creates animation assets, places them in the MixedRealityToolkit.Generated folder and enables simplified animation keyframe setting through adding Animatable properties to a target game object.</span></span> <span data-ttu-id="2e4a0-316">Pour permettre les transitions d’animation entre les États, un élément multimédia de contrôleur d’animation est créé et un ordinateur d’État par défaut est généré avec les paramètres associés et toutes les transitions d’État.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-316">To enable animation transitions between states, an Animator Controller asset is created and a default state machine is generated with associated parameters and any state transitions.</span></span>  <span data-ttu-id="2e4a0-317">La machine à États peut être affichée dans la fenêtre d’animation de Unity.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-317">The state machine can be viewed in Unity's Animator window.</span></span>

### <a name="state-visualizer-and-unity-animation-system"></a><span data-ttu-id="2e4a0-318">Visualiseur d’État et système d’animation Unity</span><span class="sxs-lookup"><span data-stu-id="2e4a0-318">State Visualizer and Unity Animation System</span></span>

<span data-ttu-id="2e4a0-319">Le visualiseur d’État tire actuellement parti du système d’animation Unity.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-319">The State Visualizer currently leverages the Unity Animation System.</span></span> 

<span data-ttu-id="2e4a0-320">Lorsque vous appuyez sur le bouton **générer de nouveaux clips d’animation** dans le visualiseur d’État, les nouvelles ressources de clip d’animation sont générées en fonction des noms d’État dans l’élément interactif et placées dans le dossier MixedRealityToolkit. generated.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-320">When the **Generate New Animation Clips** button in the State Visualizer is pressed, new animation clip assets are generated based on the state names in Interactive Element and are placed in the MixedRealityToolkit.Generated folder.</span></span> <span data-ttu-id="2e4a0-321">La propriété clip d’animation dans chaque conteneur d’État est définie sur le clip d’animation associé.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-321">The Animation Clip property in each state container is set to the associated animation clip.</span></span>

![Clips d’animation dans le composant de visualiseur d’État](../images/interactive-element/StateVisualizer/AnimationClips.png)

<span data-ttu-id="2e4a0-323">Une [machine d’état d’animation](https://docs.unity3d.com/Manual/AnimationOverview.html) est également générée pour gérer les transitions lisses entre les clips d’animation.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-323">An [Animator State Machine](https://docs.unity3d.com/Manual/AnimationOverview.html) is also generated to manage smooth transitions between animation clips.</span></span>  <span data-ttu-id="2e4a0-324">Par défaut, l’ordinateur d’État utilise l' [État any](https://docs.unity3d.com/Manual/class-State.html) pour autoriser les transitions entre n’importe quel état d’un élément interactif.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-324">By default, the state machine utilizes the [Any State](https://docs.unity3d.com/Manual/class-State.html) to allow transitions between any state in Interactive Element.</span></span> 

<span data-ttu-id="2e4a0-325">Les [visualiseurs d’État déclenchés dans l’animateur](https://docs.unity3d.com/Manual/AnimationParameters.html) sont également générés pour chaque État, les paramètres de déclencheur sont utilisés dans le visualiseur d’État pour déclencher une animation.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-325">[State visualizers triggered in the animator](https://docs.unity3d.com/Manual/AnimationParameters.html) are also generated for each state, the trigger parameters are used in the State Visualizer to trigger an animation.</span></span>

![Machine à États Unity](../images/interactive-element/StateVisualizer/UnityStateMachine.png)

### <a name="runtime-limitations"></a><span data-ttu-id="2e4a0-327">Limitations du runtime</span><span class="sxs-lookup"><span data-stu-id="2e4a0-327">Runtime Limitations</span></span> 

<span data-ttu-id="2e4a0-328">Le visualiseur d’État doit être ajouté à un objet via l’inspecteur et ne peut pas être ajouté par le biais d’un script.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-328">The State Visualizer must be added to an object via the Inspector and cannot be added via script.</span></span>  <span data-ttu-id="2e4a0-329">Les propriétés qui modifient le AnimatorStateMachine/AnimationController sont contenues dans un espace de noms d’éditeur ( `UnityEditor.Animations` ) qui est supprimé lors de la génération de l’application.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-329">The properties that modify the AnimatorStateMachine/AnimationController are contained in an editor namespace (`UnityEditor.Animations`) which get removed when the app is built.</span></span>

## <a name="how-to-use-the-state-visualizer"></a><span data-ttu-id="2e4a0-330">Comment utiliser le visualiseur d’État</span><span class="sxs-lookup"><span data-stu-id="2e4a0-330">How to use the State Visualizer</span></span>

1. <span data-ttu-id="2e4a0-331">Créer un cube</span><span class="sxs-lookup"><span data-stu-id="2e4a0-331">Create a Cube</span></span>
1. <span data-ttu-id="2e4a0-332">Attacher un élément interactif</span><span class="sxs-lookup"><span data-stu-id="2e4a0-332">Attach Interactive Element</span></span>
1. <span data-ttu-id="2e4a0-333">Visualiseur d’état d’attachement</span><span class="sxs-lookup"><span data-stu-id="2e4a0-333">Attach State Visualizer</span></span>
1. <span data-ttu-id="2e4a0-334">Sélectionner **générer de nouveaux clips d’animation**</span><span class="sxs-lookup"><span data-stu-id="2e4a0-334">Select **Generate New Animation Clips**</span></span>

    ![Génération de nouveaux clips d’animation](../images/interactive-element/StateVisualizer/GenerateAnimationClips.png)

    ![Présentation des clips d’animation générés dans les composants de visualiseur et d’élément interactif](../images/interactive-element/StateVisualizer/GenerateAnimationClips2.png)

1. <span data-ttu-id="2e4a0-337">Dans le conteneur d’état de focus, sélectionnez **Ajouter une cible** .</span><span class="sxs-lookup"><span data-stu-id="2e4a0-337">In the Focus state container, select **Add Target**</span></span>

    ![Ajout de la cible du visualiseur d’État](../images/interactive-element/StateVisualizer/AddTarget.png)

1. <span data-ttu-id="2e4a0-339">Faites glisser l’objet de jeu actuel vers le champ cible</span><span class="sxs-lookup"><span data-stu-id="2e4a0-339">Drag the current game object to the target field</span></span> 

    ![Définition de la cible du visualiseur d’État](../images/interactive-element/StateVisualizer/SetTarget.png)

1. <span data-ttu-id="2e4a0-341">Ouvrez le cube propriétés animables foldout</span><span class="sxs-lookup"><span data-stu-id="2e4a0-341">Open the Cube Animatable Properties foldout</span></span>
1. <span data-ttu-id="2e4a0-342">Sélectionnez le menu déroulant de la propriété animable et sélectionnez **couleur**</span><span class="sxs-lookup"><span data-stu-id="2e4a0-342">Select the Animatable property drop down menu and select **Color**</span></span>

    ![Définition de la couleur du visualiseur d’État](../images/interactive-element/StateVisualizer/SetColor.png)

1. <span data-ttu-id="2e4a0-344">Sélectionnez **Ajouter la couleur animable, propriété**</span><span class="sxs-lookup"><span data-stu-id="2e4a0-344">Select **Add the Color Animatable Property**</span></span>

    ![Sélection de la propriété d’animation couleur du visualiseur](../images/interactive-element/StateVisualizer/SetColorProperty.png)

1. <span data-ttu-id="2e4a0-346">Choisir une couleur</span><span class="sxs-lookup"><span data-stu-id="2e4a0-346">Choose a Color</span></span> 

    ![Choix d’une couleur de visualiseur à partir de la roue de couleur](../images/interactive-element/StateVisualizer/SetBlueColor.png)

1. <span data-ttu-id="2e4a0-348">Appuyez sur lire et observez la modification de la couleur de transition</span><span class="sxs-lookup"><span data-stu-id="2e4a0-348">Press play and observe the transitional color change</span></span>

    ![Exemple de changement de couleur transitoire avec interaction de la main virtuelle](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

## <a name="animatable-properties"></a><span data-ttu-id="2e4a0-350">Propriétés pouvant être animées</span><span class="sxs-lookup"><span data-stu-id="2e4a0-350">Animatable Properties</span></span>

<span data-ttu-id="2e4a0-351">L’objectif principal des propriétés pouvant être animées est de simplifier le paramètre d’image clé du clip d’animation.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-351">The primary purpose of the Animatable Properties is to simplify animation clip keyframe setting.</span></span>  <span data-ttu-id="2e4a0-352">Si un utilisateur est familiarisé avec le système d’animation Unity et préfère définir directement les images clés sur les clips d’animation générés, il peut simplement ne pas ajouter de propriétés animables à un objet cible et ouvrir le clip dans la fenêtre d’animation d’Unity (Windows > animation > Animation).</span><span class="sxs-lookup"><span data-stu-id="2e4a0-352">If a user is familiar with the Unity Animation System and would prefer to directly set keyframes on the generated animation clips, then they can simply not add Animatable properties to a target object and open the clip in Unity's Animation window (Windows > Animation > Animation).</span></span> 

<span data-ttu-id="2e4a0-353">Si vous utilisez les propriétés animables pour l’animation, le type de courbe est défini sur EaseInOut.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-353">If using the Animatable properties for animation, the curve type is set to EaseInOut.</span></span>

<span data-ttu-id="2e4a0-354">**Propriétés d’animation actuelles :**</span><span class="sxs-lookup"><span data-stu-id="2e4a0-354">**Current Animatable Properties:**</span></span>
- [<span data-ttu-id="2e4a0-355">Décalage de l’échelle</span><span class="sxs-lookup"><span data-stu-id="2e4a0-355">Scale Offset</span></span>](#scale-offset)
- [<span data-ttu-id="2e4a0-356">Décalage de position</span><span class="sxs-lookup"><span data-stu-id="2e4a0-356">Position Offset</span></span>](#position-offset)
- [<span data-ttu-id="2e4a0-357">Couleur</span><span class="sxs-lookup"><span data-stu-id="2e4a0-357">Color</span></span>](#color)
- [<span data-ttu-id="2e4a0-358">Couleur du nuanceur</span><span class="sxs-lookup"><span data-stu-id="2e4a0-358">Shader Color</span></span>](#shader-color)
- [<span data-ttu-id="2e4a0-359">Nuanceur float</span><span class="sxs-lookup"><span data-stu-id="2e4a0-359">Shader Float</span></span>](#shader-float)
- [<span data-ttu-id="2e4a0-360">Vecteur de nuanceur</span><span class="sxs-lookup"><span data-stu-id="2e4a0-360">Shader Vector</span></span>](#shader-vector)

### <a name="scale-offset"></a><span data-ttu-id="2e4a0-361">Décalage de l’échelle</span><span class="sxs-lookup"><span data-stu-id="2e4a0-361">Scale Offset</span></span>

<span data-ttu-id="2e4a0-362">La propriété animable de décalage de l’échelle prend l’échelle actuelle de l’objet et ajoute l’offset défini.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-362">The Scale Offset Animatable property takes the current scale of the object and adds the defined offset.</span></span>

![Décalage de l’échelle avec interaction de la main virtuelle](../images/interactive-element/InEditor/Gifs/ScaleOffset.gif)

### <a name="position-offset"></a><span data-ttu-id="2e4a0-364">Décalage de position</span><span class="sxs-lookup"><span data-stu-id="2e4a0-364">Position Offset</span></span>

<span data-ttu-id="2e4a0-365">La propriété animable de décalage de position prend la position actuelle de l’objet et ajoute l’offset défini.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-365">The Position Offset Animatable property takes the current position of the object and adds the defined offset.</span></span>

![Décalage de position avec interaction de la main virtuelle](../images/interactive-element/InEditor/Gifs/PositionOffset.gif)

### <a name="color"></a><span data-ttu-id="2e4a0-367">Couleur</span><span class="sxs-lookup"><span data-stu-id="2e4a0-367">Color</span></span>

<span data-ttu-id="2e4a0-368">La propriété d’animation de couleur représente la couleur principale d’un matériau si celui-ci a une propriété de couleur principale.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-368">The Color Animatable property represents the main color of a material if the material has a main color property.</span></span> <span data-ttu-id="2e4a0-369">Cette propriété anime la `material._Color` propriété.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-369">This property animates the `material._Color` property.</span></span>

![Modification de la couleur du focus avec interaction de la main virtuelle](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="shader-color"></a><span data-ttu-id="2e4a0-371">Couleur du nuanceur</span><span class="sxs-lookup"><span data-stu-id="2e4a0-371">Shader Color</span></span>

<span data-ttu-id="2e4a0-372">La propriété d’animation couleur du nuanceur fait référence à une propriété de nuanceur de type couleur.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-372">The Shader Color Animatable property refers to a shader property of type color.</span></span> <span data-ttu-id="2e4a0-373">Un nom de propriété est requis pour toutes les propriétés de nuanceur.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-373">A property name is required for all shader properties.</span></span> <span data-ttu-id="2e4a0-374">L’image gif ci-dessous montre comment animer une propriété de couleur de nuanceur nommée Fill_Color qui n’est pas la couleur de matériau principale.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-374">The gif below demonstrates animating a shader color property named Fill_Color that is not the main material color.</span></span>  <span data-ttu-id="2e4a0-375">Observez les valeurs variables dans l’inspecteur de matériau.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-375">Observe the changing values in the material inspector.</span></span>

![Ombrer la couleur avec interaction avec la main virtuelle](../images/interactive-element/InEditor/Gifs/ShaderColor.gif)

### <a name="shader-float"></a><span data-ttu-id="2e4a0-377">Nuanceur float</span><span class="sxs-lookup"><span data-stu-id="2e4a0-377">Shader Float</span></span>

<span data-ttu-id="2e4a0-378">La propriété d’animation float de nuanceur fait référence à une propriété de nuanceur de type float.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-378">The Shader Float Animatable property refers to a shader property of type float.</span></span> <span data-ttu-id="2e4a0-379">Un nom de propriété est requis pour toutes les propriétés de nuanceur.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-379">A property name is required for all shader properties.</span></span> <span data-ttu-id="2e4a0-380">Dans l’image gif ci-dessous, observez les valeurs variables de l’inspecteur de matériau pour la propriété métallique.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-380">In the gif below, observe the changing values in the material inspector for the Metallic property.</span></span> 

![Nuanceur flottant avec interaction de la main virtuelle](../images/interactive-element/InEditor/Gifs/ShaderFloat.gif)

### <a name="shader-vector"></a><span data-ttu-id="2e4a0-382">Vecteur de nuanceur</span><span class="sxs-lookup"><span data-stu-id="2e4a0-382">Shader Vector</span></span>

<span data-ttu-id="2e4a0-383">La propriété animable Vector Shader fait référence à une propriété de nuanceur de type Vector4.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-383">The Shader Vector Animatable property refers to a shader property of type Vector4.</span></span> <span data-ttu-id="2e4a0-384">Un nom de propriété est requis pour toutes les propriétés de nuanceur.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-384">A property name is required for all shader properties.</span></span> <span data-ttu-id="2e4a0-385">Dans l’image gif ci-dessous, observez les valeurs variables de l’inspecteur de matériau pour la propriété de mosaïque (main Tex_ST).</span><span class="sxs-lookup"><span data-stu-id="2e4a0-385">In the gif below, observe the changing values in the material inspector for the Tiling (Main Tex_ST) property.</span></span> 

![Vecteur de nuanceur avec interaction de la main virtuelle](../images/interactive-element/InEditor/Gifs/ShaderVector.gif)


### <a name="how-to-find-animatable-shader-property-names"></a><span data-ttu-id="2e4a0-387">Comment rechercher des noms de propriétés de nuanceur animables</span><span class="sxs-lookup"><span data-stu-id="2e4a0-387">How to Find Animatable Shader Property Names</span></span>

1. <span data-ttu-id="2e4a0-388">Naviguer vers la fenêtre > animation > animation</span><span class="sxs-lookup"><span data-stu-id="2e4a0-388">Navigate to Window > Animation > Animation</span></span>
1. <span data-ttu-id="2e4a0-389">S’assurer que l’objet avec le visualiseur d’État est sélectionné dans la hiérarchie</span><span class="sxs-lookup"><span data-stu-id="2e4a0-389">Ensure that the object with the State Visualizer is selected in the hierarchy</span></span>
1. <span data-ttu-id="2e4a0-390">Sélectionner un clip d’animation dans la fenêtre d’animation</span><span class="sxs-lookup"><span data-stu-id="2e4a0-390">Select any animation clip in the Animation window</span></span>
1. <span data-ttu-id="2e4a0-391">Sélectionnez **Ajouter une propriété**, ouvrez le convertisseur de maillage foldout</span><span class="sxs-lookup"><span data-stu-id="2e4a0-391">Select **Add Property**, open the Mesh Renderer foldout</span></span> 

    ![Ajout d’une propriété d’animation dans la fenêtre d’animation](../images/interactive-element/StateVisualizer/AnimationWindow.png)

1. <span data-ttu-id="2e4a0-393">Cette liste contient les noms de tous les noms de propriété pouvant être animés.</span><span class="sxs-lookup"><span data-stu-id="2e4a0-393">This list contains the names of all the Animatable property names</span></span> 

    ![Propriétés d’animation du convertisseur de maillage dans la fenêtre d’animation](../images/interactive-element/StateVisualizer/MeshRendererProperties.png)

## <a name="see-also"></a><span data-ttu-id="2e4a0-395">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e4a0-395">See also</span></span>

- [<span data-ttu-id="2e4a0-396">**Boutons**</span><span class="sxs-lookup"><span data-stu-id="2e4a0-396">**Buttons**</span></span>](../ux-building-blocks/button.md)
- [<span data-ttu-id="2e4a0-397">**Contrôle des limites**</span><span class="sxs-lookup"><span data-stu-id="2e4a0-397">**Bounds Control**</span></span>](../ux-building-blocks/bounds-control.md)
- [<span data-ttu-id="2e4a0-398">**Collection d’objets Grid**</span><span class="sxs-lookup"><span data-stu-id="2e4a0-398">**Grid Object Collection**</span></span>](../ux-building-blocks/object-collection.md)
- [<span data-ttu-id="2e4a0-399">**Solveur RadialView**</span><span class="sxs-lookup"><span data-stu-id="2e4a0-399">**RadialView Solver**</span></span>](../ux-building-blocks/solvers/solver.md)
