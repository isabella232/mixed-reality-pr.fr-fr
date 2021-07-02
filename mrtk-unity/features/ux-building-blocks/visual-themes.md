---
title: Thèmes visuels
description: Vue d’ensemble thèmes visuels contrôle flexible des ressources UX dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, thèmes MRTK,
ms.openlocfilehash: d97c470bf1d77299c6848990cdc69d886d432ecb
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177171"
---
# <a name="visual-themes"></a><span data-ttu-id="2f2fe-104">Thèmes visuels</span><span class="sxs-lookup"><span data-stu-id="2f2fe-104">Visual themes</span></span>

<span data-ttu-id="2f2fe-105">Les thèmes permettent de contrôler de façon flexible les ressources de l’expérience utilisateur en réponse à différentes transitions d’États.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-105">Themes allow for flexible control of UX assets in response to various states transitions.</span></span> <span data-ttu-id="2f2fe-106">Cela peut impliquer la modification de la couleur d’un bouton, le redimensionnement d’un élément en réponse à un focus, etc. L’infrastructure de thèmes visuels est composée de deux éléments clés : 1) configuration et 2) moteurs d’exécution.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-106">This may involve changing a button's color, resizing an element in response to focus, etc. The Visual Themes framework is made up of two key pieces: 1) configuration and 2) runtime engines.</span></span>

<span data-ttu-id="2f2fe-107">Les [configurations de thème](#theme-configuration) sont des définitions de propriétés et de types, tandis que les moteurs de [thèmes](#theme-engines) sont des classes qui consomment les configurations et implémentent la logique pour mettre à jour les transformations, les matériaux et bien plus encore lors de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-107">[Theme configurations](#theme-configuration) are definitions of properties and types while [Theme Engines](#theme-engines) are classes that consume the configurations and implement the logic to update transforms, materials, and more at runtime.</span></span>

## <a name="theme-configuration"></a><span data-ttu-id="2f2fe-108">Configuration du thème</span><span class="sxs-lookup"><span data-stu-id="2f2fe-108">Theme configuration</span></span>

<span data-ttu-id="2f2fe-109">Les configurations de thème sont des [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) qui définissent la façon dont les moteurs de thème seront initialisés au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-109">Theme configurations are [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) that define how Theme Engines will be initialized at runtime.</span></span> <span data-ttu-id="2f2fe-110">Elles définissent les propriétés et les valeurs à utiliser en réponse à des modifications d’entrée ou d’état lors de l’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-110">They define what properties and values to utilize in response to input or other state changes when the app is running.</span></span> <span data-ttu-id="2f2fe-111">En tant que ressources [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) , les configurations de thème peuvent être définies une seule fois, puis réutilisées sur différents composants d’expérience utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-111">As [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) assets, theme configurations can be defined once and then re-used across different UX components.</span></span>

<span data-ttu-id="2f2fe-112">Pour créer un [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) élément multimédia :</span><span class="sxs-lookup"><span data-stu-id="2f2fe-112">To create a new [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset:</span></span>

1) <span data-ttu-id="2f2fe-113">cliquez avec le bouton droit dans la *fenêtre Project*</span><span class="sxs-lookup"><span data-stu-id="2f2fe-113">Right click in the *Project Window*</span></span>
1) <span data-ttu-id="2f2fe-114">sélectionner **créer** une  >  **réalité mixte Shared Computer Toolkit**  >  **thème**</span><span class="sxs-lookup"><span data-stu-id="2f2fe-114">Select **Create** > **Mixed Reality Toolkit** > **Theme**</span></span>

<span data-ttu-id="2f2fe-115">Vous trouverez des exemples de ressources de configuration de thème sous `MRTK/SDK/Features/UX/Interactable/Themes` .</span><span class="sxs-lookup"><span data-stu-id="2f2fe-115">Example Theme configuration assets can be found under `MRTK/SDK/Features/UX/Interactable/Themes`.</span></span>

![Exemple de ScriptableObject de thème dans Inspector](../images/visual-themes/ThemeInspectorExample.png)

### <a name="states"></a><span data-ttu-id="2f2fe-117">États</span><span class="sxs-lookup"><span data-stu-id="2f2fe-117">States</span></span>

<span data-ttu-id="2f2fe-118">Lorsque vous créez un nouveau [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) , la première chose à définir est celle des États disponibles.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-118">When creating a new [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme), the first thing to set is what states are available.</span></span> <span data-ttu-id="2f2fe-119">La propriété *States* indique le nombre de valeurs qu’une configuration de thème doit définir, car il y aura une valeur par État.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-119">The *States* property indicates how many values a Theme configuration needs to define as there will be one value per state.</span></span> <span data-ttu-id="2f2fe-120">Dans l’exemple d’image ci-dessus, les [États par défaut définis pour le](interactable.md#general-input-settings) composant pouvant être interagi sont *default*, *focus*, *appuyé* et *Disabled*.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-120">In the example image above, the [default states defined for the Interactable](interactable.md#general-input-settings) component are *Default*, *Focus*, *Pressed*, and *Disabled*.</span></span> <span data-ttu-id="2f2fe-121">Celles-ci sont définies dans le `DefaultInteractableStates` fichier d’élément multimédia (ressources/MRTK/Kit de développement logiciel/fonctionnalités/expérience utilisateur/États).</span><span class="sxs-lookup"><span data-stu-id="2f2fe-121">These are defined in the `DefaultInteractableStates` (Assets/MRTK/SDK/Features/UX/Interactable/States) asset file.</span></span>

<span data-ttu-id="2f2fe-122">Pour créer un [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) élément multimédia :</span><span class="sxs-lookup"><span data-stu-id="2f2fe-122">To create a new [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) asset:</span></span>

1) <span data-ttu-id="2f2fe-123">cliquez avec le bouton droit dans la *fenêtre Project*</span><span class="sxs-lookup"><span data-stu-id="2f2fe-123">Right click in the *Project Window*</span></span>
1) <span data-ttu-id="2f2fe-124">sélectionner **créer** une  >  **réalité mixte Shared Computer Toolkit** l'  >  **état**</span><span class="sxs-lookup"><span data-stu-id="2f2fe-124">Select **Create** > **Mixed Reality Toolkit** > **State**</span></span>

![Exemple ScriptableObject States dans Inspector](../images/interactable/DefaultInteractableStates.png)

<span data-ttu-id="2f2fe-126">Un [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) ScriptableObject définit à la fois la liste des États et le type de *StateModel* à créer pour ces États.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-126">A [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) ScriptableObject defines both the list of states as well as the type of *StateModel* to create for these states.</span></span> <span data-ttu-id="2f2fe-127">Un *StateModel* est une classe qui étend [`BaseStateModel`](xref:Microsoft.MixedReality.Toolkit.UI.BaseStateModel) et implémente la logique de l’ordinateur d’État pour générer l’état actuel au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-127">A *StateModel* is a class that extends [`BaseStateModel`](xref:Microsoft.MixedReality.Toolkit.UI.BaseStateModel) and implements the state machine logic to generate the current state at runtime.</span></span> <span data-ttu-id="2f2fe-128">L’état actuel de cette classe est généralement utilisé par les moteurs de thème au moment de l’exécution pour dicter les valeurs à définir par rapport aux propriétés de matériau, aux transformations GameObject, etc.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-128">The current state from this class is generally used by Theme Engines at runtime to dictate what values to set against material properties, GameObject transforms, and more.</span></span>

### <a name="theme-engine-properties"></a><span data-ttu-id="2f2fe-129">Propriétés du moteur de thèmes</span><span class="sxs-lookup"><span data-stu-id="2f2fe-129">Theme engine properties</span></span>

<span data-ttu-id="2f2fe-130">En dehors des *États*, un [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) élément multimédia définit également une liste de moteurs de thèmes et les propriétés associées pour ces moteurs.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-130">Outside of *States*, a [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset also defines a list of Theme Engines and the associated properties for these engines.</span></span> <span data-ttu-id="2f2fe-131">Un [moteur de thème](#theme-engines) définit à nouveau la logique pour définir les valeurs correctes par rapport à un gameobject au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-131">A [Theme engine](#theme-engines) again defines the logic to set the correct values against a GameObject at runtime.</span></span>

<span data-ttu-id="2f2fe-132">Un [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) élément multimédia peut définir plusieurs moteurs de thèmes pour obtenir des transitions d’États visuels sophistiquées ciblant plusieurs propriétés GameObject.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-132">A [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) asset can define multiple Theme Engines to achieve sophisticated visual states transitions targeting multiple GameObject properties.</span></span>

<span data-ttu-id="2f2fe-133">**Runtime du thème**</span><span class="sxs-lookup"><span data-stu-id="2f2fe-133">**Theme Runtime**</span></span>

<span data-ttu-id="2f2fe-134">Définit le type de classe du moteur de thème qui sera créé</span><span class="sxs-lookup"><span data-stu-id="2f2fe-134">Defines the class type of the Theme engine that will be created</span></span>

<span data-ttu-id="2f2fe-135">**Simplifier**</span><span class="sxs-lookup"><span data-stu-id="2f2fe-135">**Easing**</span></span>

<span data-ttu-id="2f2fe-136">Certains *moteurs de thèmes*, s’ils définissent leur propriété [IsEasingSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported) comme true, prennent en charge l’accélération entre les États.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-136">Some *Theme Engines*, if they define their property [IsEasingSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported) as true, support easing between states.</span></span> <span data-ttu-id="2f2fe-137">Par exemple, lerping entre deux couleurs quand un changement d’État se produit.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-137">For example, lerping between two colors when a state change occurs.</span></span> <span data-ttu-id="2f2fe-138">La *durée* définit, en secondes, le délai d’exécution de la valeur de début à la valeur de fin et la *courbe d’animation* définit le taux de modification au cours de cette période.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-138">The *Duration* defines in seconds how long to ease from start value to end value and the *Animation Curve* defines the rate of change during that time period.</span></span>

<span data-ttu-id="2f2fe-139">**Propriétés du nuanceur**</span><span class="sxs-lookup"><span data-stu-id="2f2fe-139">**Shader properties**</span></span>

<span data-ttu-id="2f2fe-140">Certains *moteurs de thèmes*, s’ils définissent leur propriété [AreShadersSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported) sur true, modifient les propriétés de nuanceur spécifiques au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-140">Some *Theme Engines*, if they define their property [AreShadersSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported) as true, will modify particular shader properties at runtime.</span></span> <span data-ttu-id="2f2fe-141">Les champs de *nuanceur* et de *propriété* définissent la propriété de nuanceur à cibler.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-141">The *Shader* and *Property* fields define the shader property to target.</span></span>

### <a name="create-a-theme-configuration-via-code"></a><span data-ttu-id="2f2fe-142">Créer une configuration de thème par le biais du code</span><span class="sxs-lookup"><span data-stu-id="2f2fe-142">Create a theme configuration via code</span></span>

<span data-ttu-id="2f2fe-143">En général, il est plus facile de concevoir des configurations de thème via l’inspecteur Unity, mais il existe des cas où les thèmes doivent être générés dynamiquement au moment de l’exécution via du code.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-143">In general, it is easier to design Theme configurations via the Unity inspector but there are cases where Themes must be dynamically generated at runtime via code.</span></span> <span data-ttu-id="2f2fe-144">L’extrait de code ci-dessous fournit un exemple de la façon d’accomplir cette tâche.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-144">The code snippet below gives an example of how to accomplish this task.</span></span>

<span data-ttu-id="2f2fe-145">Pour accélérer le développement, les méthodes d’assistance suivantes sont utiles pour simplifier l’installation.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-145">To help expedite development, the following helper methods are useful for simplifying setup.</span></span>

<span data-ttu-id="2f2fe-146">[`Interactable.GetDefaultInteractableStates()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) -crée un ScriptableObject d’États avec les quatre valeurs d’État par défaut utilisées dans le composant [interagissant](interactable.md) .</span><span class="sxs-lookup"><span data-stu-id="2f2fe-146">[`Interactable.GetDefaultInteractableStates()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) - creates a new States ScriptableObject with the four default state values used in the [Interactable](interactable.md) component.</span></span>

<span data-ttu-id="2f2fe-147">[`ThemeDefinition.GetDefaultThemeDefinition<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) -Chaque moteur de thèmes définit une configuration par défaut avec les propriétés appropriées nécessaires pour ce type de Runtime de thème.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-147">[`ThemeDefinition.GetDefaultThemeDefinition<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) - Every Theme Engine defines a default configuration with the correct properties needed for that Theme runtime type.</span></span> <span data-ttu-id="2f2fe-148">Cette application d’assistance crée une définition pour le type de moteur de thème donné.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-148">This helper creates a definition for the given Theme Engine type.</span></span>

```c#
// This code example builds a Theme ScriptableObject that can be used with an Interactable component.
// A random color is selected for the on pressed state every time this code is executed.

// Use the default states utilized in the Interactable component
var defaultStates = Interactable.GetDefaultInteractableStates();

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

// Create the Theme configuration asset
Theme testTheme = ScriptableObject.CreateInstance<Theme>();
testTheme.States = defaultStates;
testTheme.Definitions = new List<ThemeDefinition>() { newThemeType };
```

## <a name="theme-engines"></a><span data-ttu-id="2f2fe-149">Moteurs de thèmes</span><span class="sxs-lookup"><span data-stu-id="2f2fe-149">Theme engines</span></span>

<span data-ttu-id="2f2fe-150">Un [moteur de thèmes](#theme-engines) est une classe qui s’étend de la [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) classe.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-150">A [Theme Engine](#theme-engines) is a class that extends from the [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) class.</span></span> <span data-ttu-id="2f2fe-151">Ces classes sont instanciées au moment de l’exécution et configurées avec un [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) objet comme décrit précédemment.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-151">These classes are instantiated at runtime and configured with a [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) object as outlined earlier.</span></span>

### <a name="default-theme-engines"></a><span data-ttu-id="2f2fe-152">Moteurs de thèmes par défaut</span><span class="sxs-lookup"><span data-stu-id="2f2fe-152">Default theme engines</span></span>

<span data-ttu-id="2f2fe-153">MRTK est fourni avec un ensemble par défaut de moteurs de thèmes listés ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="2f2fe-153">MRTK ships with a default set of Theme Engines listed below:</span></span>

- [`InteractableActivateTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableActivateTheme)
- [`InteractableAnimatorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAnimatorTheme)
- [`InteractableAudioTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAudioTheme)
- [`InteractableColorChildrenTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorChildrenTheme)
- [`InteractableColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorTheme)
- [`InteractableGrabScaleTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableGrabScaleTheme)
- [`InteractableMaterialTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableMaterialTheme)
- [`InteractableOffsetTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOffsetTheme)
- [`InteractableRotationTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableRotationTheme)
- [`InteractableScaleTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableScaleTheme)
- [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme)
- [`InteractableStringTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStringTheme)
- [`InteractableTextureTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableTextureTheme)
- [`ScaleOffsetColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.ScaleOffsetColorTheme)

<span data-ttu-id="2f2fe-154">Les moteurs de thèmes par défaut se trouvent sous `MRTK/SDK/Features/UX/Scripts/VisualThemes/ThemeEngines` .</span><span class="sxs-lookup"><span data-stu-id="2f2fe-154">The default Theme Engines can be found under `MRTK/SDK/Features/UX/Scripts/VisualThemes/ThemeEngines`.</span></span>

### <a name="custom-theme-engines"></a><span data-ttu-id="2f2fe-155">Moteurs de thèmes personnalisés</span><span class="sxs-lookup"><span data-stu-id="2f2fe-155">Custom theme engines</span></span>

<span data-ttu-id="2f2fe-156">Comme indiqué, un moteur de thèmes est défini en tant que classe qui s’étend de la [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) classe.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-156">As stated, a Theme Engine is defined as a class that extends from the [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) class.</span></span> <span data-ttu-id="2f2fe-157">Ainsi, le nouveau moteur de thème n’a besoin que d’étendre cette classe et d’implémenter les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="2f2fe-157">Thus, new Theme Engine need only extend this class and implement the following:</span></span>

#### <a name="mandatory-implementations"></a><span data-ttu-id="2f2fe-158">Implémentations obligatoires</span><span class="sxs-lookup"><span data-stu-id="2f2fe-158">Mandatory implementations</span></span>

<span data-ttu-id="2f2fe-159">`public abstract void SetValue(ThemeStateProperty property, int index, float percentage)`(XREF : Microsoft. MixedReality. Shared Computer Toolkit. L'. InteractableThemeBase. SetValue)</span><span class="sxs-lookup"><span data-stu-id="2f2fe-159">`public abstract void SetValue(ThemeStateProperty property, int index, float percentage)` (xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.SetValue)</span></span>

<span data-ttu-id="2f2fe-160">Pour la propriété donnée, qui peut être identifiée par `ThemeStateProperty.Name` , définissez sa valeur d’État actuelle sur l’hôte gameobject ciblé (c.-à-d.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-160">For the given property, which can be identified by `ThemeStateProperty.Name`, set its current state value on the targeted GameObject host (i.e</span></span> <span data-ttu-id="2f2fe-161">Définissez la couleur de la matière, etc.).</span><span class="sxs-lookup"><span data-stu-id="2f2fe-161">set the material color, etc).</span></span> <span data-ttu-id="2f2fe-162">L' *index* indique la valeur d’État actuelle à laquelle accéder et le *pourcentage*, une valeur float comprise entre 0 et 1, est utilisé pour l’accélération/la lerping entre les valeurs.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-162">The *index* indicates the current state value to access and the *percentage*, a float between 0 and 1, is used for easing/lerping between values.</span></span>

<span data-ttu-id="2f2fe-163">`public abstract ThemePropertyValue GetProperty(ThemeStateProperty property)`(XREF : Microsoft. MixedReality. Shared Computer Toolkit. L'. InteractableThemeBase. GetProperty)</span><span class="sxs-lookup"><span data-stu-id="2f2fe-163">`public abstract ThemePropertyValue GetProperty(ThemeStateProperty property)`(xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.GetProperty)</span></span>

<span data-ttu-id="2f2fe-164">Pour la propriété donnée, qui peut être identifiée par `ThemeStateProperty.Name` , retournez la valeur actuelle définie sur le gameobject hôte ciblé (c.-à-d.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-164">For the given property, which can be identified by `ThemeStateProperty.Name`, return the current value set on the targeted Host  GameObject (i.e</span></span> <span data-ttu-id="2f2fe-165">la couleur matérielle actuelle, l’offset de position local actuel, etc.).</span><span class="sxs-lookup"><span data-stu-id="2f2fe-165">the current material color, the current local position offset, etc).</span></span> <span data-ttu-id="2f2fe-166">Cela est principalement utilisé pour la mise en cache de la valeur de début lors de l’accélération entre les États.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-166">This is primarily used for caching the start value when easing between states.</span></span>

<span data-ttu-id="2f2fe-167">`public abstract ThemeDefinition GetDefaultThemeDefinition()`(XREF : Microsoft. MixedReality. Shared Computer Toolkit. L'. InteractableThemeBase.GetDefaultThemeDefinition)</span><span class="sxs-lookup"><span data-stu-id="2f2fe-167">`public abstract ThemeDefinition GetDefaultThemeDefinition()`(xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.GetDefaultThemeDefinition)</span></span>

<span data-ttu-id="2f2fe-168">Retourne un [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) objet qui définit les propriétés et la configuration par défaut nécessaires pour le thème personnalisé</span><span class="sxs-lookup"><span data-stu-id="2f2fe-168">Returns a [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) object that defines the default properties and configuration needed for the custom theme</span></span>

`protected abstract void SetValue(ThemeStateProperty property, ThemePropertyValue value)`

<span data-ttu-id="2f2fe-169">Variante protégée de la `SetValue()` définition publique, à l’exception de ThemePropertyValue fournies, à définir au lieu de rediriger l’utilisation de la configuration de l’index et/ou du pourcentage.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-169">Protected variant of the public `SetValue()` definition, except provided ThemePropertyValue to set instead of directing to use index and/or percentage configuration.</span></span>

#### <a name="recommended-overrides"></a><span data-ttu-id="2f2fe-170">Remplacements recommandés</span><span class="sxs-lookup"><span data-stu-id="2f2fe-170">Recommended overrides</span></span>

[`InteractableThemeBase.Init(GameObject host, ThemeDefinition settings)`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase)

<span data-ttu-id="2f2fe-171">Effectuez toutes les étapes d’initialisation en ciblant le paramètre *gameobject* fourni et en utilisant les propriétés et les configurations définies dans le paramètre *ThemeDefinition* .</span><span class="sxs-lookup"><span data-stu-id="2f2fe-171">Perform any initialization steps here targeting the provided *GameObject* parameter and using the properties and configurations defined in the *ThemeDefinition* parameter.</span></span> <span data-ttu-id="2f2fe-172">Il est recommandé d’appeler `base.Init(host, settings)` au début d’une substitution.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-172">It is recommended to call `base.Init(host, settings)` at the beginning of an override.</span></span>

[`InteractableThemeBase.IsEasingSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported)

<span data-ttu-id="2f2fe-173">Si le moteur de thèmes personnalisé peut prendre en charge l’accélération entre les valeurs configurées via la [`ThemeDefinition.Easing`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition.Easing) propriété.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-173">If the custom Theme Engine can support easing between values which is configured via the [`ThemeDefinition.Easing`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition.Easing) property.</span></span>

[`InteractableThemeBase.AreShadersSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported)

<span data-ttu-id="2f2fe-174">Si le moteur de thèmes personnalisé peut prendre en charge le ciblage des propriétés du nuanceur.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-174">If the custom Theme Engine can support targeting shader properties.</span></span> <span data-ttu-id="2f2fe-175">Il est recommandé d’étendre à [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) pour tirer parti de l’infrastructure existante pour définir/récupérer efficacement des propriétés de nuanceur via [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html).</span><span class="sxs-lookup"><span data-stu-id="2f2fe-175">It is recommended to extend from [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) to benefit from the existing infrastructure to efficiently set/get shader properties via [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html).</span></span> <span data-ttu-id="2f2fe-176">Les informations de propriété du nuanceur sont stockées dans chaque [`ThemeStateProperty`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty) via [`ThemeStateProperty.TargetShader`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.TargetShader) et [`ThemeStateProperty.ShaderPropertyName`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.ShaderPropertyName) .</span><span class="sxs-lookup"><span data-stu-id="2f2fe-176">The shader property information is stored in each [`ThemeStateProperty`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty) via [`ThemeStateProperty.TargetShader`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.TargetShader) and [`ThemeStateProperty.ShaderPropertyName`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.ShaderPropertyName).</span></span>

> [!NOTE]
> <span data-ttu-id="2f2fe-177">En cas [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) d’extension, il peut également être utile de remplacer [InteractableShaderTheme. DefaultShaderProperty](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme.DefaultShaderProperty) par *New*.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-177">If extending [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme), it can also be useful to override the [InteractableShaderTheme.DefaultShaderProperty](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme.DefaultShaderProperty) via *new*.</span></span>
>
> <span data-ttu-id="2f2fe-178">Exemple de code : `protected new const string DefaultShaderProperty = "_Color";`</span><span class="sxs-lookup"><span data-stu-id="2f2fe-178">Example code: `protected new const string DefaultShaderProperty = "_Color";`</span></span>
>
> <span data-ttu-id="2f2fe-179">En outre, les classes suivantes étendent la [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) classe qui utilise de nouveau [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) pour modifier les valeurs de propriété du nuanceur.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-179">Furthermore, the following classes below extend the [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) class which again uses [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) to modify shader property values.</span></span> <span data-ttu-id="2f2fe-180">Cette approche [améliore les performances](https://docs.unity3d.com/Manual/DrawCallBatching.html) , car les *MaterialPropertyBlocks* ne créent pas de nouveaux matériaux instanciés lorsque les valeurs changent.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-180">This approach [helps performance](https://docs.unity3d.com/Manual/DrawCallBatching.html) because *MaterialPropertyBlocks* do not create new instanced materials when values change.</span></span> <span data-ttu-id="2f2fe-181">Toutefois, l’accès aux propriétés de classe [Material](https://docs.unity3d.com/ScriptReference/Material.html) standard ne retourne pas les valeurs attendues.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-181">However, accessing the typical [Material](https://docs.unity3d.com/ScriptReference/Material.html) class properties will not return expected values.</span></span> <span data-ttu-id="2f2fe-182">Utilisez *MaterialPropertyBlocks* pour récupérer et valider les valeurs de propriété de matériau actuelles (par exemple,</span><span class="sxs-lookup"><span data-stu-id="2f2fe-182">Use *MaterialPropertyBlocks* to get and validate current material property values (i.e</span></span> <span data-ttu-id="2f2fe-183">*_Color* ou *_MainTex*).</span><span class="sxs-lookup"><span data-stu-id="2f2fe-183">*_Color* or *_MainTex*).</span></span>
>
> - [`InteractableColorChildrenTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorChildrenTheme)
> - [`InteractableColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorTheme)
> - [`InteractableTextureTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableTextureTheme)
> - [`ScaleOffsetColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.ScaleOffsetColorTheme)

[`InteractableThemeBase.Reset`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.Reset)

<span data-ttu-id="2f2fe-184">Indique au thème de rétablir les valeurs d’origine des propriétés modifiées qui ont été définies sur l’hôte GameObject lorsque ce moteur de thème a été initialisé.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-184">Directs the theme to reset any modified properties back to their original values that were set on the host GameObject when this theme engine was initialized.</span></span>  

### <a name="custom-theme-engine-example"></a><span data-ttu-id="2f2fe-185">Exemple de moteur de thème personnalisé</span><span class="sxs-lookup"><span data-stu-id="2f2fe-185">Custom theme engine example</span></span>

<span data-ttu-id="2f2fe-186">La classe ci-dessous est un exemple de nouveau moteur de thème personnalisé.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-186">The class below is an example of a custom new Theme Engine.</span></span> <span data-ttu-id="2f2fe-187">Cette implémentation trouvera un composant [MeshRenderer](https://docs.unity3d.com/ScriptReference/MeshRenderer.html) sur l’objet hôte initialisé et contrôle sa visibilité en fonction de l’état actuel.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-187">This implementation will find a [MeshRenderer](https://docs.unity3d.com/ScriptReference/MeshRenderer.html) component on the initialized host object and control its visibility based on the current state.</span></span>

```c#
using Microsoft.MixedReality.Toolkit.UI;
using System;
using System.Collections.Generic;
using UnityEngine;

// This class demonstrates a custom theme to control a Host's MeshRenderer visibility
public class MeshVisibilityTheme : InteractableThemeBase
{
    // Bool visibility does not make sense for lerping
    public override bool IsEasingSupported => false;

    // No material or shaders are being modified
    public override bool AreShadersSupported => false;

    // Cache reference to the MeshRenderer component on our Host
    private MeshRenderer meshRenderer;

    public MeshVisibilityTheme()
    {
        Types = new Type[] { typeof(MeshRenderer) };
        Name = "Mesh Visibility Theme";
    }

    // Define a default configuration to simplify initialization of this theme engine
    // There is only one state property with a value per available state
    // This state property is a boolean that defines whether the renderer is enabled
    public override ThemeDefinition GetDefaultThemeDefinition()
    {
        return new ThemeDefinition()
        {
            ThemeType = GetType(),
            StateProperties = new List<ThemeStateProperty>()
            {
                new ThemeStateProperty()
                {
                    Name = "Mesh Visible",
                    Type = ThemePropertyTypes.Bool,
                    Values = new List<ThemePropertyValue>(),
                    Default = new ThemePropertyValue() { Bool = true }
                },
            },
            CustomProperties = new List<ThemeProperty>()
        };
    }

    // When initializing, cache a reference to the MeshRenderer component
    public override void Init(GameObject host, ThemeDefinition definition)
    {
        base.Init(host, definition);

        meshRenderer = host.GetComponent<MeshRenderer>();
    }

    // Get the current state of the MeshRenderer visibility
    public override ThemePropertyValue GetProperty(ThemeStateProperty property)
    {
        return new ThemePropertyValue()
        {
            Bool = meshRenderer.enabled
        };
    }

    // Update the MeshRenderer visibility based on the property state value data
    public override void SetValue(ThemeStateProperty property, int index, float percentage)
    {
        meshRenderer.enabled = property.Values[index].Bool;
    }
}
```

## <a name="end-to-end-example"></a><span data-ttu-id="2f2fe-188">Exemple de bout en bout</span><span class="sxs-lookup"><span data-stu-id="2f2fe-188">End-to-end example</span></span>

<span data-ttu-id="2f2fe-189">En étendant le moteur de thème personnalisé défini dans la section précédente, l’exemple de code ci-dessous montre comment contrôler ce thème au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-189">Extending off of the custom Theme Engine defined in the earlier section, the code example below demonstrates how to control this theme at runtime.</span></span> <span data-ttu-id="2f2fe-190">En particulier, comment définir l’état actuel sur le thème pour que la visibilité MeshRenderer soit mise à jour de manière appropriée.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-190">In particular, how to set the current state on the theme so the MeshRenderer visibility is updated appropriately.</span></span>

> [!NOTE]
> <span data-ttu-id="2f2fe-191">`theme.OnUpdate(state,force)` doit généralement être appelé dans la méthode Update () pour prendre en charge les moteurs de thèmes qui utilisent l’accélération/lerping entre les valeurs.</span><span class="sxs-lookup"><span data-stu-id="2f2fe-191">`theme.OnUpdate(state,force)` should generally be called in the Update() method to support Theme Engines that utilize easing/lerping between values.</span></span>

```c#
using Microsoft.MixedReality.Toolkit.UI;
using System;
using System.Collections.Generic;
using UnityEngine;

public class MeshVisibilityController : MonoBehaviour
{
    private MeshVisibilityTheme themeEngine;
    private bool hideMesh = false;

    private void Start()
    {
        // Define the default configuration. State 0 will be on while State 1 will be off
        var themeDefinition = ThemeDefinition.GetDefaultThemeDefinition<MeshVisibilityTheme>().Value;
        themeDefinition.StateProperties[0].Values = new List<ThemePropertyValue>()
        {
            new ThemePropertyValue() { Bool = true }, // show state
            new ThemePropertyValue() { Bool = false }, // hide state
        };

        // Create the actual Theme engine and initialize it with the GameObject we are attached to
        themeEngine = (MeshVisibilityTheme)InteractableThemeBase.CreateAndInitTheme(themeDefinition, this.gameObject);
    }

    private void Update()
    {
        // Update the theme engine to set our MeshRenderer visibility
        // based on our current state (i.e the hideMesh variable)
        themeEngine.OnUpdate(Convert.ToInt32(hideMesh));
    }

    public void ToggleVisibility()
    {
        // Alternate state of visibility
        hideMesh = !hideMesh;
    }
}
```

## <a name="see-also"></a><span data-ttu-id="2f2fe-192">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f2fe-192">See also</span></span>

- [<span data-ttu-id="2f2fe-193">Avec interaction</span><span class="sxs-lookup"><span data-stu-id="2f2fe-193">Interactable</span></span>](interactable.md)
