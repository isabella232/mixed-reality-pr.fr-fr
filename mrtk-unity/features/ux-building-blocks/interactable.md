---
title: Avec interaction
description: Vue d’ensemble du composant script d’interaction dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, interactive, événements,
ms.openlocfilehash: f141a394ec9395e0a27cc964caeb66654fb6fe08
ms.sourcegitcommit: 47c402dc8e588817ce60229bf019170fa36f3045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2021
ms.locfileid: "107581561"
---
# <a name="interactable"></a><span data-ttu-id="99377-104">Avec interaction</span><span class="sxs-lookup"><span data-stu-id="99377-104">Interactable</span></span>

![Avec interaction](../images/interactable/InteractableExamples.png)

<span data-ttu-id="99377-106">Le [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) composant est un conteneur tout-en-un pour rendre un objet facilement  accessible et réactif aux entrées.</span><span class="sxs-lookup"><span data-stu-id="99377-106">The [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) component is an all-in-one container to make any object easily *interactable* and responsive to input.</span></span> <span data-ttu-id="99377-107">Les actions interactifs agissent comme un tout pour tous les types d’entrée, y compris le toucher, les rayons de main, la parole, etc., et entonnoirnt ces interactions dans des [événements](#events) et des réponses de [thème visuel](visual-themes.md) .</span><span class="sxs-lookup"><span data-stu-id="99377-107">Interactable acts as a catch-all for all types of input including touch, hand rays, speech etc and funnel these interactions into [events](#events) and [visual theme](visual-themes.md) responses.</span></span> <span data-ttu-id="99377-108">Ce composant offre un moyen simple de créer des boutons, de modifier la couleur des objets avec le focus et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="99377-108">This component provides an easy way to make buttons, change color on objects with focus, and more.</span></span>

## <a name="how-to-configure-interactable"></a><span data-ttu-id="99377-109">Comment configurer l’interaction</span><span class="sxs-lookup"><span data-stu-id="99377-109">How to configure Interactable</span></span>

<span data-ttu-id="99377-110">Le composant permet trois principales sections de configuration :</span><span class="sxs-lookup"><span data-stu-id="99377-110">The component allows for three primary sections of configuration:</span></span>

1) [<span data-ttu-id="99377-111">Configuration d’entrée générale</span><span class="sxs-lookup"><span data-stu-id="99377-111">General input configuration</span></span>](#general-input-settings)
1) <span data-ttu-id="99377-112">[Thèmes visuels](visual-themes.md) ciblés sur plusieurs GameObjects</span><span class="sxs-lookup"><span data-stu-id="99377-112">[Visual Themes](visual-themes.md) targeted against multiple GameObjects</span></span>
1) [<span data-ttu-id="99377-113">Gestionnaires d’événements</span><span class="sxs-lookup"><span data-stu-id="99377-113">Event handlers</span></span>](#events)

### <a name="general-input-settings"></a><span data-ttu-id="99377-114">Paramètres d’entrée généraux</span><span class="sxs-lookup"><span data-stu-id="99377-114">General input settings</span></span>

![Paramètres généraux interactifs](../images/interactable/InputFeatures_short.png)

<span data-ttu-id="99377-116">**États**</span><span class="sxs-lookup"><span data-stu-id="99377-116">**States**</span></span>

<span data-ttu-id="99377-117">*States* est un paramètre [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) qui définit les phases d’interaction, comme l’appui ou l’observation, pour les profils et les [thèmes visuels](visual-themes.md)pouvant être [interagis](#interactable-profiles) .</span><span class="sxs-lookup"><span data-stu-id="99377-117">*States* is a [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) parameter that defines the interactions phases, like press or observed, for [Interactable Profiles](#interactable-profiles) and [Visual Themes](visual-themes.md).</span></span>

<span data-ttu-id="99377-118">**DefaultInteractableStates** (Assets/MRTK/SDK/features/UX/interactive/States/DefaultInteractableStates. Asset) est fourni avec MRTK out-of-Box et est le paramètre *par défaut pour les* composants interactifs.</span><span class="sxs-lookup"><span data-stu-id="99377-118">The **DefaultInteractableStates** (Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset) ships with MRTK out-of-box and is the default parameter for *Interactable* components.</span></span>

![Exemple ScriptableObject States dans Inspector](../images/interactable/DefaultInteractableStates.png)

<span data-ttu-id="99377-120">La ressource *DefaultInteractableStates* contient quatre États et utilise l' [`InteractableStates`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStates) implémentation du modèle d’État.</span><span class="sxs-lookup"><span data-stu-id="99377-120">The *DefaultInteractableStates* asset contains four states and utilizes the [`InteractableStates`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStates) state model implementation.</span></span>

* <span data-ttu-id="99377-121">**Valeur par défaut**: rien ne se passe, il s’agit de l’état de base le plus isolé.</span><span class="sxs-lookup"><span data-stu-id="99377-121">**Default**: Nothing is happening, this is the most isolated base state.</span></span>

* <span data-ttu-id="99377-122">**Focus**: l’objet est pointé.</span><span class="sxs-lookup"><span data-stu-id="99377-122">**Focus**: The object is being pointed at.</span></span> <span data-ttu-id="99377-123">Il s’agit d’un État unique, aucun autre État n’est actuellement défini, mais il n’a pas de classement par défaut.</span><span class="sxs-lookup"><span data-stu-id="99377-123">This is a single state, no other states are currently set, but it will out rank Default.</span></span>

* <span data-ttu-id="99377-124">**Appuyez sur**: l’objet est pointé et un bouton ou une main est enfoncé.</span><span class="sxs-lookup"><span data-stu-id="99377-124">**Press**: The object is being pointed at and a button or hand is pressing.</span></span> <span data-ttu-id="99377-125">La valeur par défaut et le focus de l’état de la presse.</span><span class="sxs-lookup"><span data-stu-id="99377-125">The Press state out ranks Default and Focus.</span></span> <span data-ttu-id="99377-126">Cet État est également défini en tant que secours pour une pression physique.</span><span class="sxs-lookup"><span data-stu-id="99377-126">This state will also get set as a fallback to Physical Press.</span></span>

* <span data-ttu-id="99377-127">**Désactivé**: le bouton ne doit pas être interactif et un retour visuel permettra à l’utilisateur de savoir si ce bouton n’est pas utilisable pour l’instant.</span><span class="sxs-lookup"><span data-stu-id="99377-127">**Disabled**: The button should not be interactive and visual feedback will let the user know if for some reason this button is not usable at this time.</span></span> <span data-ttu-id="99377-128">En théorie, l’état désactivé peut contenir tous les autres États, mais lorsque l’option est activée est désactivée, l’état désactivé prend tous les autres États.</span><span class="sxs-lookup"><span data-stu-id="99377-128">In theory, the disabled state could contain all other states, but when Enabled is turned off, the Disabled state trumps all other states.</span></span>

<span data-ttu-id="99377-129">Une valeur de bit (#) est assignée à l’État en fonction de l’ordre dans la liste.</span><span class="sxs-lookup"><span data-stu-id="99377-129">A bit value (#) is assigned to the state depending on the order in the list.</span></span>

> [!NOTE]
> <span data-ttu-id="99377-130">Il est généralement recommandé d’utiliser **DefaultInteractableStates** (Assets/MRTK/SDK/features/UX/interactive/States/DefaultInteractableStates. Asset) lors de *la création de* composants interactifs.</span><span class="sxs-lookup"><span data-stu-id="99377-130">It is generally recommended to utilize the **DefaultInteractableStates** (Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset) when creating *Interactable* components.</span></span>
>
> <span data-ttu-id="99377-131">Toutefois, il existe 17 États interactifs qui peuvent être utilisés pour piloter des thèmes, bien que certains soient destinés à être pilotés par d’autres composants.</span><span class="sxs-lookup"><span data-stu-id="99377-131">However, there are 17 Interactable states available that can be used to drive themes, though some are meant to be driven by other components.</span></span> <span data-ttu-id="99377-132">Voici une liste de ceux qui ont des fonctionnalités intégrées.</span><span class="sxs-lookup"><span data-stu-id="99377-132">Here is a list of those with built-in functionality.</span></span>
>
> * <span data-ttu-id="99377-133">Visité : l’utilisateur a cliqué sur l’interagissant.</span><span class="sxs-lookup"><span data-stu-id="99377-133">Visited: the Interactable has been clicked.</span></span>
> * <span data-ttu-id="99377-134">Activé/désactivé : le bouton est dans un État bascule ou l’index de dimension est un nombre impair.</span><span class="sxs-lookup"><span data-stu-id="99377-134">Toggled: The button is in a toggled state or Dimension index is an odd number.</span></span>
> * <span data-ttu-id="99377-135">Mouvement : la main ou le contrôleur a été enfoncé et a été déplacé de la position d’origine.</span><span class="sxs-lookup"><span data-stu-id="99377-135">Gesture: The hand or controller was pressed and has moved from the original position.</span></span>
> * <span data-ttu-id="99377-136">VoiceCommand : une commande vocale a été utilisée pour déclencher l’interaction.</span><span class="sxs-lookup"><span data-stu-id="99377-136">VoiceCommand: A speech command was used to trigger the Interactable.</span></span>
> * <span data-ttu-id="99377-137">PhysicalTouch : une entrée tactile est actuellement détectée [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) . Utilisez pour activer.</span><span class="sxs-lookup"><span data-stu-id="99377-137">PhysicalTouch: A touch input is currently detected, use [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) to enable.</span></span>
> * <span data-ttu-id="99377-138">Manipulation : une main est actuellement saisie dans les limites de l’objet, utilisez [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) pour activer</span><span class="sxs-lookup"><span data-stu-id="99377-138">Grab: A hand is currently grabbing in the bounds of the object, use [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) to enable</span></span>

<span data-ttu-id="99377-139">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="99377-139">**Enabled**</span></span>

<span data-ttu-id="99377-140">Active ou désactive l’activation d’une opération d’interaction.</span><span class="sxs-lookup"><span data-stu-id="99377-140">Toggles whether an Interactable will start enabled or not.</span></span> <span data-ttu-id="99377-141">Cela correspond au [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) dans le code.</span><span class="sxs-lookup"><span data-stu-id="99377-141">This corresponds to the [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) in code.</span></span>

<span data-ttu-id="99377-142">Une propriété activée pour une *interaction* est différente de la propriété activée configurée via gameobject/Component (c.-à-d.</span><span class="sxs-lookup"><span data-stu-id="99377-142">An *Interactable's* enabled property is different than the enabled property configured via GameObject/Component (i.e</span></span> <span data-ttu-id="99377-143">Setactal, etc.).</span><span class="sxs-lookup"><span data-stu-id="99377-143">SetActive etc).</span></span> <span data-ttu-id="99377-144">La désactivation du monocomportement GameObject ou *interactive* désactive l’exécution de tout élément de la classe, y compris l’entrée, les thèmes visuels, les événements, etc. La désactivation via [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) désactive la plupart des informations de gestion des entrées, en réinitialisant les États d’entrée associés.</span><span class="sxs-lookup"><span data-stu-id="99377-144">Disabling the GameObject or *Interactable* MonoBehaviour will disable everything in the class from running including input, visual themes, events, etc. Disabling via [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) will disable most input handling, resetting related input states.</span></span> <span data-ttu-id="99377-145">Toutefois, la classe exécute toujours chaque frame et reçoit les événements d’entrée qui seront ignorés.</span><span class="sxs-lookup"><span data-stu-id="99377-145">However, the class will still run every frame and receive input events which will be ignored.</span></span> <span data-ttu-id="99377-146">Cela est utile pour afficher l’état d’interaction dans un état désactivé qui peut être effectué par le biais de thèmes visuels.</span><span class="sxs-lookup"><span data-stu-id="99377-146">This is useful for displaying the Interactable in a disabled state which can be done via Visual Themes.</span></span> <span data-ttu-id="99377-147">Un bouton Envoyer est un exemple typique qui est l’attente de l’exécution de tous les champs d’entrée requis.</span><span class="sxs-lookup"><span data-stu-id="99377-147">A typical example of this would be a submit button waiting for all the required input fields to be completed.</span></span>

<span data-ttu-id="99377-148">**Actions d’entrée**</span><span class="sxs-lookup"><span data-stu-id="99377-148">**Input Actions**</span></span>

<span data-ttu-id="99377-149">Sélectionnez l' [action d’entrée](../input/input-actions.md) à partir de la configuration d’entrée ou du profil de mappage de contrôleur auquel *le composant pouvant* être utilisé doit réagir.</span><span class="sxs-lookup"><span data-stu-id="99377-149">Select the [input action](../input/input-actions.md) from the input configuration or controller mapping profile that the *Interactable* component should react to.</span></span>

<span data-ttu-id="99377-150">Cette propriété peut être configurée au moment de l’exécution dans le code via [`Interactable.InputAction`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.InputAction) .</span><span class="sxs-lookup"><span data-stu-id="99377-150">This property can be configured at runtime in code via [`Interactable.InputAction`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.InputAction).</span></span>

<span data-ttu-id="99377-151">**IsGlobal**</span><span class="sxs-lookup"><span data-stu-id="99377-151">**IsGlobal**</span></span>

<span data-ttu-id="99377-152">Si la valeur est true, le composant est marqué comme écouteur d’entrée global pour l' [action d’entrée](../input/input-actions.md)sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="99377-152">If true, this will mark the component as a global input listener for the selected [input action](../input/input-actions.md).</span></span> <span data-ttu-id="99377-153">Le comportement par défaut est false, ce qui limite l’entrée à ce conflit/GameObject pouvant être *interagi* .</span><span class="sxs-lookup"><span data-stu-id="99377-153">Default behavior is false which will restrict input to only this *Interactable* collider/GameObject.</span></span>

<span data-ttu-id="99377-154">Cette propriété peut être configurée au moment de l’exécution dans le code via [`Interactable.IsGlobal`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsGlobal) .</span><span class="sxs-lookup"><span data-stu-id="99377-154">This property can be configured at runtime in code via [`Interactable.IsGlobal`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsGlobal).</span></span>

<span data-ttu-id="99377-155">**Commande vocale**</span><span class="sxs-lookup"><span data-stu-id="99377-155">**Speech Command**</span></span>

<span data-ttu-id="99377-156">[Commande vocale](../input/speech.md), à partir du profil de commandes vocales MRTK, pour déclencher un événement OnClick pour une interaction vocale.</span><span class="sxs-lookup"><span data-stu-id="99377-156">[Speech command](../input/speech.md), from the MRTK Speech Commands Profile, to trigger an OnClick event for voice interaction.</span></span>

<span data-ttu-id="99377-157">Cette propriété peut être configurée au moment de l’exécution dans le code via [`Interactable.VoiceCommand`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceCommand) .</span><span class="sxs-lookup"><span data-stu-id="99377-157">This property can be configured at runtime in code via [`Interactable.VoiceCommand`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceCommand).</span></span>

<span data-ttu-id="99377-158">**Nécessite le focus**</span><span class="sxs-lookup"><span data-stu-id="99377-158">**Requires Focus**</span></span>

<span data-ttu-id="99377-159">Si la valeur est true, la commande vocale activera uniquement l’opération *interactive* si et uniquement si elle a déjà le focus à partir d’un pointeur.</span><span class="sxs-lookup"><span data-stu-id="99377-159">If true, the voice command will only activate the *Interactable* if and only if it already has focus from a pointer.</span></span> <span data-ttu-id="99377-160">Si la valeur est false, l’opération *interactive* agit comme un écouteur global pour la commande vocale sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="99377-160">If false, then the *Interactable* will act as a global listener for the selected voice command.</span></span> <span data-ttu-id="99377-161">Le comportement par défaut est true, car plusieurs écouteurs de reconnaissance vocale globaux peuvent être difficiles à organiser dans une scène.</span><span class="sxs-lookup"><span data-stu-id="99377-161">The default behavior is true, as multiple global speech listeners can be difficult to organize in a scene.</span></span>

<span data-ttu-id="99377-162">Cette propriété peut être configurée au moment de l’exécution dans le code via [`Interactable.VoiceRequiresFocus`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceRequiresFocus) .</span><span class="sxs-lookup"><span data-stu-id="99377-162">This property can be configured at runtime in code via [`Interactable.VoiceRequiresFocus`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceRequiresFocus).</span></span>

<span data-ttu-id="99377-163">**Mode de sélection**</span><span class="sxs-lookup"><span data-stu-id="99377-163">**Selection Mode**</span></span>

<span data-ttu-id="99377-164">Cette propriété définit la logique de sélection.</span><span class="sxs-lookup"><span data-stu-id="99377-164">This property defines the selection logic.</span></span> <span data-ttu-id="99377-165">Lorsqu’un utilisateur clique *sur un utilisateur* , il itère au niveau de la *dimension* suivante.</span><span class="sxs-lookup"><span data-stu-id="99377-165">When an *Interactable* is clicked, it iterates into a next *Dimension* level.</span></span> <span data-ttu-id="99377-166">Les *dimensions* sont similaires au rang et définissent un État en dehors des entrées (c.-à-d.</span><span class="sxs-lookup"><span data-stu-id="99377-166">*Dimensions* is similar to rank and defines a state outside of inputs (i.e</span></span> <span data-ttu-id="99377-167">le focus, appuyez sur etc.).</span><span class="sxs-lookup"><span data-stu-id="99377-167">focus, press etc).</span></span> <span data-ttu-id="99377-168">Ils sont utiles pour définir des États de basculement ou d’autres États à plusieurs rangs associés à un bouton.</span><span class="sxs-lookup"><span data-stu-id="99377-168">They are useful for defining Toggle states or other multi-rank states associated with a button.</span></span> <span data-ttu-id="99377-169">Le niveau de dimension actuel est suivi par `Interactable.DimensionIndex` .</span><span class="sxs-lookup"><span data-stu-id="99377-169">The current Dimension level is tracked by `Interactable.DimensionIndex`.</span></span>

<span data-ttu-id="99377-170">Les modes de sélection disponibles sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="99377-170">The selection modes available are:</span></span>

* <span data-ttu-id="99377-171">**Bouton**  -  *Dimensions* = 1, interactif simple  et interactifs</span><span class="sxs-lookup"><span data-stu-id="99377-171">**Button** - *Dimensions* = 1, simple clickable *Interactable*</span></span>
* <span data-ttu-id="99377-172">**Activer/désactiver**  -  *Dimensions* = *2,* alternatives  / *interactives* entre l’état inactif</span><span class="sxs-lookup"><span data-stu-id="99377-172">**Toggle** - *Dimensions* = 2, *Interactable* alternates between *on*/*off* state</span></span>
* <span data-ttu-id="99377-173">**Plusieurs dimensions**  -  *Dimensions* >= 3, chaque clic augmente le niveau de dimension actuel + 1.</span><span class="sxs-lookup"><span data-stu-id="99377-173">**Multi-dimension** - *Dimensions* >= 3, every click increases the current dimension level + 1.</span></span> <span data-ttu-id="99377-174">Utile pour définir un état de bouton sur une liste, etc.</span><span class="sxs-lookup"><span data-stu-id="99377-174">Useful for defining a button state to a list, etc.</span></span>

<span data-ttu-id="99377-175">L' *interaction* peut également permettre la définition de plusieurs thèmes par *dimension*.</span><span class="sxs-lookup"><span data-stu-id="99377-175">*Interactable* also allows for multiple Themes to be defined per *Dimension*.</span></span> <span data-ttu-id="99377-176">Par exemple, quand *SelectionMode = Toggle*, un thème peut être appliqué lorsque l’opération d' *interaction* est *désélectionnée* et qu’un autre thème est appliqué lorsque le composant est *sélectionné*.</span><span class="sxs-lookup"><span data-stu-id="99377-176">For example when *SelectionMode=Toggle*, one theme may be applied when the *Interactable* is *deselected* and another theme applied when the component is *selected*.</span></span>

<span data-ttu-id="99377-177">Le mode de sélection actuel peut être interrogé au moment de l’exécution via [`Interactable.ButtonMode`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.ButtonMode) .</span><span class="sxs-lookup"><span data-stu-id="99377-177">The current Selection Mode can be queried at runtime via [`Interactable.ButtonMode`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.ButtonMode).</span></span> <span data-ttu-id="99377-178">La mise à jour du mode au moment de l’exécution peut être obtenue en définissant la  [`Interactable.Dimensions`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.Dimensions) propriété pour qu’elle corresponde à la fonctionnalité souhaitée.</span><span class="sxs-lookup"><span data-stu-id="99377-178">Updating the mode at runtime can be achieved by setting the  [`Interactable.Dimensions`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.Dimensions) property to match the desired functionality.</span></span> <span data-ttu-id="99377-179">En outre, la dimension actuelle, utile pour les modes de *basculement* et de *plusieurs dimensions* , est accessible via [`Interactable.CurrentDimension`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.CurrentDimension) .</span><span class="sxs-lookup"><span data-stu-id="99377-179">Furthermore, the current dimension, useful for *Toggle* and *Multi-Dimension* modes, can be accessed via [`Interactable.CurrentDimension`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.CurrentDimension).</span></span>

### <a name="interactable-profiles"></a><span data-ttu-id="99377-180">Profils interactifs</span><span class="sxs-lookup"><span data-stu-id="99377-180">Interactable profiles</span></span>

<span data-ttu-id="99377-181">Les *profils* sont des éléments qui créent une relation entre un gameobject et un [thème visuel](visual-themes.md).</span><span class="sxs-lookup"><span data-stu-id="99377-181">*Profiles* are items that create a relationship between a GameObject and a [Visual Theme](visual-themes.md).</span></span> <span data-ttu-id="99377-182">Le profil définit le contenu qui sera manipulé par un thème lorsqu’un [changement d’État se produit](#general-input-settings).</span><span class="sxs-lookup"><span data-stu-id="99377-182">The profile defines what content will be manipulated by a theme when a [state change occurs](#general-input-settings).</span></span>

<span data-ttu-id="99377-183">Les thèmes fonctionnent beaucoup comme des documents.</span><span class="sxs-lookup"><span data-stu-id="99377-183">Themes work a lot like materials.</span></span> <span data-ttu-id="99377-184">Il s’agit d’objets scriptables qui contiennent une liste de propriétés qui seront affectées à un objet en fonction de l’état actuel.</span><span class="sxs-lookup"><span data-stu-id="99377-184">They are scriptable objects that contain a list of properties that will be assigned to an object based on the current state.</span></span> <span data-ttu-id="99377-185">Les thèmes sont également réutilisables et peuvent être attribués *sur plusieurs objets* UX interactifs.</span><span class="sxs-lookup"><span data-stu-id="99377-185">Themes are also re-usable and can be assigned across multiple *Interactable* UX objects.</span></span>

<span data-ttu-id="99377-186">**Réinitialisation lors de la destruction**</span><span class="sxs-lookup"><span data-stu-id="99377-186">**Reset On Destroy**</span></span>

<span data-ttu-id="99377-187">Les thèmes visuels modifient différentes propriétés sur un GameObject ciblé, selon la classe et le type de moteur de thème sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="99377-187">Visual themes modify various properties on a targeted GameObject, dependent on the class and type of theme engine selected.</span></span> <span data-ttu-id="99377-188">Si l’opération *de réinitialisation sur Destroy* a la valeur true lorsque le composant interactif est détruit, le composant rétablit les valeurs d’origine de toutes les propriétés modifiées des thèmes actifs.</span><span class="sxs-lookup"><span data-stu-id="99377-188">If *Reset On Destroy* is true when the Interactable component is destroyed, the component will reset all modified properties from active themes to their original values.</span></span> <span data-ttu-id="99377-189">Dans le cas contraire, lorsqu’il est détruit, le composant qui peut être interagi laisse toutes les propriétés modifiées en l’État.</span><span class="sxs-lookup"><span data-stu-id="99377-189">Otherwise, when destroyed, the Interactable component will leave any modified properties as-is.</span></span> <span data-ttu-id="99377-190">Dans ce dernier cas, le dernier état des valeurs est conservé, sauf s’il est modifié par un autre composant externe.</span><span class="sxs-lookup"><span data-stu-id="99377-190">In this latter case, the last state of values will persist unless altered by another external component.</span></span> <span data-ttu-id="99377-191">La valeur par défaut est false.</span><span class="sxs-lookup"><span data-stu-id="99377-191">The default is false.</span></span>

<img src="../images/interactable/Profiles_Themes.png" width="450" alt="Profile theams">

## <a name="events"></a><span data-ttu-id="99377-192">Événements</span><span class="sxs-lookup"><span data-stu-id="99377-192">Events</span></span>

<span data-ttu-id="99377-193">Chaque composant pouvant être utilisé est associé à un événement *OnClick* qui se déclenche lorsque *le composant est* simplement sélectionné.</span><span class="sxs-lookup"><span data-stu-id="99377-193">Every *Interactable* component has an *OnClick* event that fires when the component is simply selected.</span></span> <span data-ttu-id="99377-194">Toutefois, il peut être utilisé pour *détecter des événements* d’entrée autres que *OnClick*.</span><span class="sxs-lookup"><span data-stu-id="99377-194">However, *Interactable* can be used to detect input events other than just *OnClick*.</span></span>

<span data-ttu-id="99377-195">Cliquez sur le bouton *Ajouter un événement* pour ajouter un nouveau type de définition de récepteur d’événements.</span><span class="sxs-lookup"><span data-stu-id="99377-195">Click the *Add Event* button to add a new type of Event Receiver definition.</span></span> <span data-ttu-id="99377-196">Une fois ajouté, sélectionnez le type d’événement souhaité.</span><span class="sxs-lookup"><span data-stu-id="99377-196">Once added, select the type of Event desired.</span></span>

![Exemple d’événements](../images/interactable/Events.png)<span data-ttu-id="99377-198">)</span><span class="sxs-lookup"><span data-stu-id="99377-198">)</span></span>

<span data-ttu-id="99377-199">Il existe différents types de récepteurs d’événements pour répondre à différents types d’entrée.</span><span class="sxs-lookup"><span data-stu-id="99377-199">There are different types of event receivers to respond to different types of input.</span></span> <span data-ttu-id="99377-200">MRTK est fourni avec l’ensemble de récepteurs suivant, prêt à l’emploi.</span><span class="sxs-lookup"><span data-stu-id="99377-200">MRTK ships with the following set of receivers out-of-box.</span></span>

* [`InteractableAudioReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAudioReceiver)
* [`InteractableOnClickReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnClickReceiver)
* [`InteractableOnFocusReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)
* [`InteractableOnGrabReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnGrabReceiver)
* [`InteractableOnHoldReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnHoldReceiver)
* [`InteractableOnPressReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnPressReceiver)
* [`InteractableOnToggleReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnToggleReceiver)
* [`InteractableOnTouchReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnTouchReceiver)

<span data-ttu-id="99377-201">Un récepteur personnalisé peut être créé en créant une nouvelle classe qui étend [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) .</span><span class="sxs-lookup"><span data-stu-id="99377-201">A custom receiver can be created by making a new class that extends [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase).</span></span>

![Exemple de récepteur de basculement d’événement](../images/interactable/Event_toggle.png)

<span data-ttu-id="99377-203">*Exemple de récepteur d’événements Toggle*</span><span class="sxs-lookup"><span data-stu-id="99377-203">*Example of a Toggle Event Receiver*</span></span>

### <a name="interactable-receivers"></a><span data-ttu-id="99377-204">Récepteurs interactifs</span><span class="sxs-lookup"><span data-stu-id="99377-204">Interactable receivers</span></span>

 <span data-ttu-id="99377-205">Le [`InteractableReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiver) composant permet de définir des événements en dehors du composant d' *interaction* source.</span><span class="sxs-lookup"><span data-stu-id="99377-205">The [`InteractableReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiver) component allows for events to be defined outside of the source *Interactable* component.</span></span> <span data-ttu-id="99377-206">Le *InteractableReceiver* écoute un type d’événement filtré déclenché par un autre qui peut être *interagi*.</span><span class="sxs-lookup"><span data-stu-id="99377-206">The *InteractableReceiver* will listen for a filtered event type fired by another *Interactable*.</span></span> <span data-ttu-id="99377-207">Si la propriété *interactive* n’est pas affectée directement, la propriété de la *zone de recherche* définit la direction que le *InteractableReceiver* écoute pour les événements qui se trouvent sur lui-même, dans un parent ou dans un gameobject enfant.</span><span class="sxs-lookup"><span data-stu-id="99377-207">If the *Interactable* property is not directly assigned, then the *Search Scope* property defines the direction the *InteractableReceiver* listens for events which is either on itself, in a parent, or in a child GameObject.</span></span>

<span data-ttu-id="99377-208">[`InteractableReceiverList`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiverList) agit de manière similaire, mais pour une liste d’événements correspondants.</span><span class="sxs-lookup"><span data-stu-id="99377-208">[`InteractableReceiverList`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiverList) acts in a similar fashion but for a list of matching events.</span></span>

<img src="../images/interactable/InteractableReceiver.png" width="450" alt="Interactable reciver">

### <a name="create-custom-events"></a><span data-ttu-id="99377-209">Créer des événements personnalisés</span><span class="sxs-lookup"><span data-stu-id="99377-209">Create custom events</span></span>

<span data-ttu-id="99377-210">Comme les [thèmes visuels](visual-themes.md#custom-theme-engines), les événements peuvent être étendus pour détecter tout modèle d’État ou pour exposer des fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="99377-210">Like [Visual Themes](visual-themes.md#custom-theme-engines), events can be extended to detect any state pattern or to expose functionality.</span></span>

<span data-ttu-id="99377-211">Les événements personnalisés peuvent être créés de deux manières principales :</span><span class="sxs-lookup"><span data-stu-id="99377-211">Custom events can be created in two main ways:</span></span>

1) <span data-ttu-id="99377-212">Étendez la [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) classe pour créer un événement personnalisé qui s’affichera dans la liste déroulante des types d’événements.</span><span class="sxs-lookup"><span data-stu-id="99377-212">Extend the [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) class to create a custom event that will show up in the dropdown list of event types.</span></span> <span data-ttu-id="99377-213">Un événement Unity est fourni par défaut, mais des événements Unity supplémentaires peuvent être ajoutés ou l’événement peut être défini de façon à masquer les événements Unity.</span><span class="sxs-lookup"><span data-stu-id="99377-213">A Unity event is provided by default, but additional Unity events can be added or the event can be set to hide Unity events.</span></span> <span data-ttu-id="99377-214">Cette fonctionnalité permet à un concepteur de travailler avec un ingénieur sur un projet pour créer un événement personnalisé que le concepteur peut configurer dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="99377-214">This functionality allows a designer to work with an engineer on a project to create a custom event that the designer can setup in the editor.</span></span>

1) <span data-ttu-id="99377-215">Étendez la [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) classe pour créer un composant d’événement entièrement personnalisé qui peut résider  sur le ou un autre objet pouvant être utilisé.</span><span class="sxs-lookup"><span data-stu-id="99377-215">Extend the [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) class to create a completely custom event component that can reside on the *Interactable* or another object.</span></span> <span data-ttu-id="99377-216">Fait [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) référence à l’opération *interactive* pour détecter les modifications d’État.</span><span class="sxs-lookup"><span data-stu-id="99377-216">The [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) will reference the *Interactable* to detect state changes.</span></span>

#### <a name="example-of-extending-receiverbase"></a><span data-ttu-id="99377-217">Exemple d’extension `ReceiverBase`</span><span class="sxs-lookup"><span data-stu-id="99377-217">Example of extending `ReceiverBase`</span></span>

<span data-ttu-id="99377-218">La [`CustomInteractablesReceiver`](xref:Microsoft.MixedReality.Toolkit.UI) classe affiche des informations d’état  sur un intercepteur et est un exemple de création d’un récepteur d’événements personnalisé.</span><span class="sxs-lookup"><span data-stu-id="99377-218">The [`CustomInteractablesReceiver`](xref:Microsoft.MixedReality.Toolkit.UI) class displays status information about an *Interactable* and is an example of how to create a custom Event Receiver.</span></span>

```c#
public CustomInteractablesReceiver(UnityEvent ev) : base(ev, "CustomEvent")
{
    HideUnityEvents = true; // hides Unity events in the receiver - meant to be code only
}
```

<span data-ttu-id="99377-219">Les méthodes suivantes sont utiles pour remplacer/implémenter lors de la création d’un récepteur d’événements personnalisé.</span><span class="sxs-lookup"><span data-stu-id="99377-219">The following methods are useful to override/implement when creating a custom Event Receiver.</span></span> <span data-ttu-id="99377-220">[`ReceiverBase.OnUpdate()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) est une méthode abstraite qui peut être utilisée pour détecter des modèles d’état/des transitions.</span><span class="sxs-lookup"><span data-stu-id="99377-220">[`ReceiverBase.OnUpdate()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) is an abstract method that can be used to detect state patterns/transitions.</span></span> <span data-ttu-id="99377-221">En outre, [`ReceiverBase.OnVoiceCommand()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) les [`ReceiverBase.OnClick()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) méthodes et sont utiles pour la création d’une logique d’événement personnalisée lorsque l’option *interactive* est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="99377-221">Furthermore, the [`ReceiverBase.OnVoiceCommand()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) and [`ReceiverBase.OnClick()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) methods are useful for creating custom event logic when the *Interactable* is selected.</span></span>

```c#
public override void OnUpdate(InteractableStates state, Interactable source)
{
    if (state.CurrentState() != lastState)
    {
        // the state has changed, do something new
        lastState = state.CurrentState();
        ...
    }
}

public virtual void OnVoiceCommand(InteractableStates state, Interactable source,
                                    string command, int index = 0, int length = 1)
{
    base.OnVoiceCommand(state, source, command, index, length);
    // voice command called, perform some action
}  

public virtual void OnClick(InteractableStates state,
                            Interactable source,
                            IMixedRealityPointer pointer = null)
{
    base.OnClick(state, source);
    // click called, perform some action
}
```

##### <a name="displaying-custom-event-receiver-fields-in-the-inspector"></a><span data-ttu-id="99377-222">Affichage des champs de récepteur d’événements personnalisés dans l’inspecteur</span><span class="sxs-lookup"><span data-stu-id="99377-222">Displaying custom event receiver fields in the inspector</span></span>

<span data-ttu-id="99377-223">Les scripts *ReceiverBase* utilisent [`InspectorField`](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.InspectorField) des attributs pour exposer des propriétés personnalisées dans l’inspecteur.</span><span class="sxs-lookup"><span data-stu-id="99377-223">*ReceiverBase* scripts use [`InspectorField`](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.InspectorField) attributes to expose custom properties in the inspector.</span></span> <span data-ttu-id="99377-224">Voici un exemple de Vector3, une propriété personnalisée avec des informations d’info-bulle et d’étiquette.</span><span class="sxs-lookup"><span data-stu-id="99377-224">Here's an example of Vector3, a custom property with tooltip and label information.</span></span> <span data-ttu-id="99377-225">Cette propriété s’affiche comme configurable dans l’inspecteur lorsqu' *un GameObjectable* est sélectionné et que le type de récepteur d' *événements* associé est ajouté.</span><span class="sxs-lookup"><span data-stu-id="99377-225">This property will show up as configurable in the inspector when an *Interactable* GameObject is selected and has the associated *Event Receiver* type added.</span></span>

```c#
[InspectorField(Label = "<Property label>",Tooltip = "<Insert tooltip info>",Type = InspectorField.FieldTypes.Vector3)]
public Vector3 EffectOffset = Vector3.zero;
```

## <a name="how-to-use-interactable"></a><span data-ttu-id="99377-226">Comment utiliser les méthodes d’interaction</span><span class="sxs-lookup"><span data-stu-id="99377-226">How to use Interactable</span></span>

### <a name="building-a-simple-button"></a><span data-ttu-id="99377-227">Création d’un bouton simple</span><span class="sxs-lookup"><span data-stu-id="99377-227">Building a simple button</span></span>

<span data-ttu-id="99377-228">Vous pouvez créer un bouton simple en ajoutant le composant *interagissant* à un gameobject qui est configuré pour recevoir des événements d’entrée.</span><span class="sxs-lookup"><span data-stu-id="99377-228">One can create a simple button by adding the *Interactable* component to a GameObject that is configured to receive input events.</span></span> <span data-ttu-id="99377-229">Il peut y avoir un conflit ou un enfant pour recevoir l’entrée.</span><span class="sxs-lookup"><span data-stu-id="99377-229">It can have a collider on it or on a child to receive input.</span></span> <span data-ttu-id="99377-230">Si vous utilisez *interactive* avec un GameObjects basé sur une interface utilisateur Unity, il doit se trouver sous le canevas GameObject.</span><span class="sxs-lookup"><span data-stu-id="99377-230">If using *Interactable* with a Unity UI based GameObjects, it should be under the Canvas GameObject.</span></span>

<span data-ttu-id="99377-231">Suivez le bouton une étape plus loin, en créant un nouveau profil, en affectant le GameObject et en créant un nouveau thème.</span><span class="sxs-lookup"><span data-stu-id="99377-231">Take the button one step further, by creating a new profile, assigning the GameObject itself and creating a new theme.</span></span> <span data-ttu-id="99377-232">En outre, utilisez l’événement *OnClick* pour faire en sorte qu’un événement se produise.</span><span class="sxs-lookup"><span data-stu-id="99377-232">Furthermore, use the *OnClick* event to make something happen.</span></span>

> [!NOTE]
> <span data-ttu-id="99377-233">Le fait d' [appuyer sur un bouton](button.md) requiert le [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) composant.</span><span class="sxs-lookup"><span data-stu-id="99377-233">Making a [button pressable](button.md) requires the [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) component.</span></span> <span data-ttu-id="99377-234">En outre, le [`PhysicalPressEventRouter`](xref:Microsoft.MixedReality.Toolkit.PhysicalPressEventRouter) composant est nécessaire pour entonnoirr les événements d’appui sur le composant en *interaction* .</span><span class="sxs-lookup"><span data-stu-id="99377-234">Additionally, the [`PhysicalPressEventRouter`](xref:Microsoft.MixedReality.Toolkit.PhysicalPressEventRouter) component is needed to funnel press events to the *Interactable* component.</span></span>

### <a name="creating-toggle-and-multi-dimension-buttons"></a><span data-ttu-id="99377-235">Création de boutons bascule et à plusieurs dimensions</span><span class="sxs-lookup"><span data-stu-id="99377-235">Creating toggle and multi-dimension buttons</span></span>

#### <a name="toggle-button"></a><span data-ttu-id="99377-236">Bouton bascule</span><span class="sxs-lookup"><span data-stu-id="99377-236">Toggle button</span></span>

<span data-ttu-id="99377-237">Pour rendre un bouton activé, modifiez le [`Selection Mode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) champ en type `Toggle` .</span><span class="sxs-lookup"><span data-stu-id="99377-237">To make a button Toggle-able, change the [`Selection Mode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) field to type `Toggle`.</span></span> <span data-ttu-id="99377-238">Dans la section *profils* , un nouveau thème basculé est ajouté pour chaque profil utilisé lorsque l' *interaction* est activée.</span><span class="sxs-lookup"><span data-stu-id="99377-238">In the *Profiles* section, a new toggled theme is added for each profile that is used when the *Interactable* is toggled on.</span></span>

<span data-ttu-id="99377-239">Tandis que [`SelectionMode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) est défini pour basculer, la case à cocher *IsToggled* peut être utilisée pour définir la valeur par défaut du contrôle lors de l’initialisation du Runtime.</span><span class="sxs-lookup"><span data-stu-id="99377-239">While the [`SelectionMode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) is set to Toggle, the *IsToggled* check box can be used to set the default value of the control at runtime initialization.</span></span>

<span data-ttu-id="99377-240">*CanSelect* signifie que l' *interagissement* peut passer de *off* à *on* , tandis que le *CanDeselect* signifie l’inverse.</span><span class="sxs-lookup"><span data-stu-id="99377-240">*CanSelect* means the *Interactable* can go from *off* to *on* while the *CanDeselect* means the inverse.</span></span>

![Exemple de thème visuel basculement de profil](../images/interactable/Profile_toggle.png)

<span data-ttu-id="99377-242">Les développeurs peuvent utiliser [`SetToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) les [`IsToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) interfaces et pour accéder ou définir l’État bascule d’une interface *interactive* via du code.</span><span class="sxs-lookup"><span data-stu-id="99377-242">Developers can utilize the [`SetToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) and [`IsToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) interfaces to get/set the toggle state of an *Interactable* via code.</span></span>

```c#
// If using SelectionMode = Toggle (i.e Dimensions == 2)

// Make the Interactable selected and toggled on
myInteractable.IsToggled = true;

// Get whether the Interactable is selected or not
bool isSelected = myInteractable.IsToggled;
```

##### <a name="toggle-button-collection"></a><span data-ttu-id="99377-243">Basculer la collection de boutons</span><span class="sxs-lookup"><span data-stu-id="99377-243">Toggle button collection</span></span>

<span data-ttu-id="99377-244">Il est courant d’avoir une liste de boutons bascule où un seul peut être actif à un moment donné, également appelé un ensemble radial ou des cases d’option, etc.</span><span class="sxs-lookup"><span data-stu-id="99377-244">It is common to have a list of toggle buttons where only one can be active at any given time, also known as a radial set or radio buttons etc.</span></span>

<span data-ttu-id="99377-245">Utilisez le [`InteractableToggleCollection`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableToggleCollection) composant pour activer cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="99377-245">Use the [`InteractableToggleCollection`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableToggleCollection) component to enable this functionality.</span></span> <span data-ttu-id="99377-246">Ce contrôle garantit qu’un seul *interagissant* est activé à un moment donné.</span><span class="sxs-lookup"><span data-stu-id="99377-246">This control ensures only one *Interactable* is toggled on at any given time.</span></span> <span data-ttu-id="99377-247">*RadialSet* (Assets/MRTK/SDK/features/UX/interactive/Prefabs/RadialSet. Prefab) est également un excellent point de départ prêt à l’emploi.</span><span class="sxs-lookup"><span data-stu-id="99377-247">The *RadialSet* (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/RadialSet.prefab) is also a great starting point out-of-box.</span></span>

<span data-ttu-id="99377-248">Pour créer un groupe de boutons radial personnalisé :</span><span class="sxs-lookup"><span data-stu-id="99377-248">To create a custom radial button group:</span></span>

1) <span data-ttu-id="99377-249">Créer plusieurs *GameObjects* /boutons interactifs</span><span class="sxs-lookup"><span data-stu-id="99377-249">Create multiple *Interactable* GameObjects/buttons</span></span>
1) <span data-ttu-id="99377-250">Définir chaque *interagissant* avec *SelectionMode* = Toggle, *CanSelect* = true et *CanDeselect* = false</span><span class="sxs-lookup"><span data-stu-id="99377-250">Set each *Interactable* with *SelectionMode* = Toggle, *CanSelect* = true, and *CanDeselect* = false</span></span>
1) <span data-ttu-id="99377-251">Créer un GameObject parent vide sur tous les *Interactables* et ajouter le composant *InteractableToggleCollection*</span><span class="sxs-lookup"><span data-stu-id="99377-251">Create an empty parent GameObject over all the *Interactables* and add the *InteractableToggleCollection* component</span></span>
1) <span data-ttu-id="99377-252">Ajoutez tous les *Interactables* à *ToggleList* sur *InteractableToggleCollection*</span><span class="sxs-lookup"><span data-stu-id="99377-252">Add all *Interactables* to the *ToggleList* on the *InteractableToggleCollection*</span></span>
1) <span data-ttu-id="99377-253">Définissez la propriété *InteractableToggleCollection. CurrentIndex* pour déterminer le bouton sélectionné par défaut au démarrage</span><span class="sxs-lookup"><span data-stu-id="99377-253">Set the *InteractableToggleCollection.CurrentIndex* property to determine which button is selected by default at start</span></span>

<img src="../images/interactable/InteractableToggleCollection.png" width="450" alt="Toggle collection">

#### <a name="multi-dimensional-button"></a><span data-ttu-id="99377-254">Bouton multidimensionnel</span><span class="sxs-lookup"><span data-stu-id="99377-254">Multi-dimensional button</span></span>

<span data-ttu-id="99377-255">Le mode de sélection de plusieurs dimensions est utilisé pour créer des boutons séquentiels, ou un bouton qui compte plus de deux étapes, comme le contrôle de la vitesse avec trois valeurs, rapide (1x), plus rapide (2x) ou plus rapide (3x).</span><span class="sxs-lookup"><span data-stu-id="99377-255">Multi-Dimension selection mode is used to create sequential buttons, or a button that has more than two steps, like controlling speed with three values, Fast (1x), Faster (2x) or Fastest (3x).</span></span>

<span data-ttu-id="99377-256">Comme les dimensions sont une valeur numérique, vous pouvez ajouter jusqu’à 9 thèmes pour contrôler l’étiquette de texte ou la texture du bouton pour chaque paramètre de vitesse, à l’aide d’un thème différent pour chaque étape.</span><span class="sxs-lookup"><span data-stu-id="99377-256">With dimensions being a numeric value, up to 9 themes can be added to control the text label or texture of the button for each speed setting, using a different theme for each of step.</span></span>

<span data-ttu-id="99377-257">Chaque événement de clic avance de à `DimensionIndex` 1 au moment de l’exécution jusqu’à ce que la `Dimensions` valeur soit atteinte.</span><span class="sxs-lookup"><span data-stu-id="99377-257">Every click event will advance the `DimensionIndex` by 1 at runtime until the `Dimensions` value is reached.</span></span> <span data-ttu-id="99377-258">Le cycle est alors réinitialisé à 0.</span><span class="sxs-lookup"><span data-stu-id="99377-258">Then the cycle will reset to 0.</span></span>

![Exemple de profil multidimensionnel](../images/interactable/Profile_multiDimensions.png)

<span data-ttu-id="99377-260">Les développeurs peuvent évaluer le [`DimensionIndex`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) pour déterminer quelle dimension est actuellement active.</span><span class="sxs-lookup"><span data-stu-id="99377-260">Developers can assess the [`DimensionIndex`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) to determine which dimension is currently active.</span></span>

```c#
// If using SelectionMode = Multi-dimension (i.e Dimensions >= 3)

//Access the current DimensionIndex
int currentDimension = myInteractable.CurrentDimension;

//Set the current DimensionIndex to 2
myInteractable.CurrentDimension = 2;

// Promote Dimension to next level
myInteractable.IncreaseDimension();
```

### <a name="create-interactable-at-runtime"></a><span data-ttu-id="99377-261">Créer des dialogues interactifs au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="99377-261">Create Interactable at runtime</span></span>

<span data-ttu-id="99377-262">Vous *pouvez facilement* ajouter des GameObjectables à n’importe quel moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="99377-262">*Interactable* can be easily added to any GameObject at runtime.</span></span> <span data-ttu-id="99377-263">L’exemple suivant montre comment assigner un profil avec un [thème visuel](visual-themes.md).</span><span class="sxs-lookup"><span data-stu-id="99377-263">The following example demonstrates how to assign a profile with a [visual theme](visual-themes.md).</span></span>

```c#
var interactableObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
var interactable = interactableObject.AddComponent<Interactable>();

// Get the default configuration for the Theme engine InteractableColorTheme
var newThemeType = ThemeDefinition.GetDefaultThemeDefinition<InteractableColorTheme>().Value;

// Define a color for every state in our Default Interactable States
newThemeType.StateProperties[0].Values = new List<ThemePropertyValue>()
{
    new ThemePropertyValue() { Color = Color.black},  // Default
    new ThemePropertyValue() { Color = Color.black}, // Focus
    new ThemePropertyValue() { Color = Random.ColorHSV()},   // Pressed
    new ThemePropertyValue() { Color = Color.black},   // Disabled
};

interactable.Profiles = new List<InteractableProfileItem>()
{
    new InteractableProfileItem()
    {
        Themes = new List<Theme>()
        {
            Interactable.GetDefaultThemeAsset(new List<ThemeDefinition>() { newThemeType })
        },
        Target = interactableObject,
    },
};

// Force the Interactable to be clicked
interactable.TriggerOnClick()
```

### <a name="interactable-events-via-code"></a><span data-ttu-id="99377-264">Événements interactifs via du code</span><span class="sxs-lookup"><span data-stu-id="99377-264">Interactable events via code</span></span>

<span data-ttu-id="99377-265">Vous pouvez ajouter une action à l’événement de base [`Interactable.OnClick`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.OnClick) par le biais du code avec l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="99377-265">One can add an action to the base [`Interactable.OnClick`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.OnClick) event via code with the following example.</span></span>

```c#
public static void AddOnClick(Interactable interactable)
{
    interactable.OnClick.AddListener(() => Debug.Log("Interactable clicked"));
}
```

<span data-ttu-id="99377-266">Utilisez la [`Interactable.AddReceiver<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) fonction pour ajouter dynamiquement des récepteurs d’événements au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="99377-266">Use the [`Interactable.AddReceiver<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) function to add event receivers dynamically at runtime.</span></span>

<span data-ttu-id="99377-267">L’exemple de code ci-dessous montre comment ajouter un [InteractableOnFocusReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), qui écoute l’entrée/la sortie Focus, et définir le code d’action à exécuter lorsque les instances d’événements se déclenchent.</span><span class="sxs-lookup"><span data-stu-id="99377-267">The example code below demonstrates how to add an [InteractableOnFocusReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), which listens for focus enter/exit, and furthermore define action code to perform when the event instances fire.</span></span>

```c#
public static void AddFocusEvents(Interactable interactable)
{
    var onFocusReceiver = interactable.AddReceiver<InteractableOnFocusReceiver>();

    onFocusReceiver.OnFocusOn.AddListener(() => Debug.Log("Focus on"));
    onFocusReceiver.OnFocusOff.AddListener(() => Debug.Log("Focus off"));
}
```

<span data-ttu-id="99377-268">L’exemple de code ci-dessous montre comment ajouter un [InteractableOnToggleReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), qui écoute les transitions d’État sélectionnées/désélectionnées sur les *Interactables* pouvant être activés et qui définit le code d’action à exécuter lorsque les instances d’événements se déclenchent.</span><span class="sxs-lookup"><span data-stu-id="99377-268">The example code below demonstrates how to add an [InteractableOnToggleReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), which listens for selected/deselected state transitions on toggle-able *Interactables*, and furthermore defines action code to perform when the event instances fire.</span></span>

```c#
public static void AddToggleEvents(Interactable interactable)
{
    var toggleReceiver = interactable.AddReceiver<InteractableOnToggleReceiver>();

    // Make the interactable have toggle capability, from code.
    // In the gui editor it's much easier
    interactable.Dimensions = 2;
    interactable.CanSelect = true;
    interactable.CanDeselect  = true;

    toggleReceiver.OnSelect.AddListener(() => Debug.Log("Toggle selected"));
    toggleReceiver.OnDeselect.AddListener(() => Debug.Log("Toggle un-selected"));
}
```

## <a name="see-also"></a><span data-ttu-id="99377-269">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99377-269">See also</span></span>

* [<span data-ttu-id="99377-270">Thèmes visuels</span><span class="sxs-lookup"><span data-stu-id="99377-270">Visual Themes</span></span>](visual-themes.md)
* [<span data-ttu-id="99377-271">Actions d’entrée</span><span class="sxs-lookup"><span data-stu-id="99377-271">Input Actions</span></span>](../input/input-actions.md)
* [<span data-ttu-id="99377-272">Commandes vocales</span><span class="sxs-lookup"><span data-stu-id="99377-272">Speech Commands</span></span>](../input/speech.md)
* [<span data-ttu-id="99377-273">Boutons</span><span class="sxs-lookup"><span data-stu-id="99377-273">Buttons</span></span>](button.md)
* [<span data-ttu-id="99377-274">Nuanceur standard MRTK</span><span class="sxs-lookup"><span data-stu-id="99377-274">MRTK Standard Shader</span></span>](../rendering/MRTK-standard-shader.md)
