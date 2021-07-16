---
title: Création d’un fournisseur de données de système d’entrée
description: documentation pour créer un système d’entrée et un fournisseur de données dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: 0b6012871a4d4988fdb70336a3c33455f479bcac
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281926"
---
# <a name="creating-an-input-system-data-provider"></a><span data-ttu-id="47afb-104">Création d’un fournisseur de données de système d’entrée</span><span class="sxs-lookup"><span data-stu-id="47afb-104">Creating an input system data provider</span></span>

<span data-ttu-id="47afb-105">la réalité mixte Shared Computer Toolkit système d’entrée est un système extensible permettant d’activer la prise en charge des périphériques d’entrée.</span><span class="sxs-lookup"><span data-stu-id="47afb-105">The Mixed Reality Toolkit input system is an extensible system for enabling input device support.</span></span> <span data-ttu-id="47afb-106">Pour ajouter la prise en charge d’une nouvelle plateforme matérielle, un fournisseur de données d’entrée personnalisé peut être nécessaire.</span><span class="sxs-lookup"><span data-stu-id="47afb-106">To add support for a new hardware platform, a custom input data provider may be required.</span></span>

<span data-ttu-id="47afb-107">Cet article explique comment créer des fournisseurs de données personnalisés, également appelés gestionnaires d’appareils, pour le système d’entrée.</span><span class="sxs-lookup"><span data-stu-id="47afb-107">This article describes how to create custom data providers, also called device managers, for the input system.</span></span> <span data-ttu-id="47afb-108">L’exemple de code présenté ici provient de [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) .</span><span class="sxs-lookup"><span data-stu-id="47afb-108">The example code shown here is from the [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager).</span></span>

> <span data-ttu-id="47afb-109">Le code complet utilisé dans cet exemple se trouve dans le dossier MRTK/Providers/WindowsMixedReality.</span><span class="sxs-lookup"><span data-stu-id="47afb-109">The complete code used in this example can be found in the MRTK/Providers/WindowsMixedReality folder.</span></span>

## <a name="namespace-and-folder-structure"></a><span data-ttu-id="47afb-110">Structure de l’espace de noms et du dossier</span><span class="sxs-lookup"><span data-stu-id="47afb-110">Namespace and folder structure</span></span>

<span data-ttu-id="47afb-111">les fournisseurs de données peuvent être distribués en tant que complément tiers ou dans le cadre de la Shared Computer Toolkit de la réalité mixte Microsoft.</span><span class="sxs-lookup"><span data-stu-id="47afb-111">Data providers can be distributed as a third party add-on or as a part of the Microsoft Mixed Reality Toolkit.</span></span> <span data-ttu-id="47afb-112">Le processus d’approbation pour les envois de nouveaux fournisseurs de données à l’MRTK varie au cas par cas et est communiqué au moment de la proposition initiale.</span><span class="sxs-lookup"><span data-stu-id="47afb-112">The approval process for submissions of new data providers to the MRTK will vary on a case-by-case basis and will be communicated at the time of the initial proposal.</span></span>

> [!Important]
> <span data-ttu-id="47afb-113">si un fournisseur de données de système d’entrée est envoyé à la [réalité mixte Shared Computer Toolkit référentiel](https://github.com/Microsoft/MixedRealityToolkit-Unity), l’espace de noms **doit** commencer par Microsoft. MixedReality. Shared Computer Toolkit (par exemple : Microsoft. MixedReality. Shared Computer Toolkit. WindowsMixedReality) et le code doivent se trouver dans un dossier sous MRTK/Providers (ex : MRTK/Providers/WindowsMixedReality).</span><span class="sxs-lookup"><span data-stu-id="47afb-113">If an input system data provider is being submitted to the [Mixed Reality Toolkit repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), the namespace **must** begin with Microsoft.MixedReality.Toolkit (ex: Microsoft.MixedReality.Toolkit.WindowsMixedReality) and the code should be located in a folder beneath MRTK/Providers (ex: MRTK/Providers/WindowsMixedReality).</span></span>

### <a name="namespace"></a><span data-ttu-id="47afb-114">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="47afb-114">Namespace</span></span>

<span data-ttu-id="47afb-115">Les fournisseurs de données doivent disposer d’un espace de noms pour atténuer les conflits de noms potentiels.</span><span class="sxs-lookup"><span data-stu-id="47afb-115">Data providers are required to have a namespace to mitigate potential name collisions.</span></span> <span data-ttu-id="47afb-116">Il est recommandé que l’espace de noms inclue les composants suivants.</span><span class="sxs-lookup"><span data-stu-id="47afb-116">It is recommended that the namespace includes the following components.</span></span>

- <span data-ttu-id="47afb-117">Nom de la société</span><span class="sxs-lookup"><span data-stu-id="47afb-117">Company name</span></span>
- <span data-ttu-id="47afb-118">Domaine de fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="47afb-118">Feature area</span></span>

<span data-ttu-id="47afb-119">Par exemple, un fournisseur de données d’entrée créé par la société contoso peut être «contoso. MixedReality. Shared Computer Toolkit. Entrée».</span><span class="sxs-lookup"><span data-stu-id="47afb-119">For example, an input data provider created by the Contoso company may be "Contoso.MixedReality.Toolkit.Input".</span></span>

### <a name="recommended-folder-structure"></a><span data-ttu-id="47afb-120">Structure de dossiers recommandée</span><span class="sxs-lookup"><span data-stu-id="47afb-120">Recommended folder structure</span></span>

<span data-ttu-id="47afb-121">Il est recommandé que le code source des fournisseurs de données soit disposé dans une hiérarchie de dossiers, comme indiqué dans l’image suivante.</span><span class="sxs-lookup"><span data-stu-id="47afb-121">It is recommended that the source code for data providers be layed out in a folder hierarchy as shown in the following image.</span></span>

![Exemple de structure de dossiers](../images/input/ExampleProviderFolderStructure.png)

<span data-ttu-id="47afb-123">Où ContosoInput contient l’implémentation du fournisseur de données, le dossier de l’éditeur contient l’inspecteur (et tout autre code spécifique à l’éditeur Unity), le dossier textures contient des images des contrôleurs pris en charge, et les profils contiennent un ou plusieurs profils prédéfinis.</span><span class="sxs-lookup"><span data-stu-id="47afb-123">Where ContosoInput contains the implementation of the data provider, the Editor folder contains the inspector (and any other Unity editor specific code), the Textures folder contains images of the supported controllers, and Profiles contains one or more pre-made profiles.</span></span>

> [!Note]
> <span data-ttu-id="47afb-124">Certaines images de contrôleur courantes se trouvent dans le dossier MixedRealityToolkit\StandardAssets\Textures.</span><span class="sxs-lookup"><span data-stu-id="47afb-124">Some common controller images can be found in the MixedRealityToolkit\StandardAssets\Textures folder.</span></span>

## <a name="implement-the-data-provider"></a><span data-ttu-id="47afb-125">Implémenter le fournisseur de données</span><span class="sxs-lookup"><span data-stu-id="47afb-125">Implement the data provider</span></span>

### <a name="specify-interface-andor-base-class-inheritance"></a><span data-ttu-id="47afb-126">Spécifier l’héritage de l’interface et/ou de la classe de base</span><span class="sxs-lookup"><span data-stu-id="47afb-126">Specify interface and/or base class inheritance</span></span>

<span data-ttu-id="47afb-127">Tous les fournisseurs de données de système d’entrée doivent implémenter l' [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interface, qui spécifie les fonctionnalités minimales requises par le système d’entrée.</span><span class="sxs-lookup"><span data-stu-id="47afb-127">All input system data providers must implement the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interface, which specifies the minimum functionality required by the input system.</span></span> <span data-ttu-id="47afb-128">MRTK Foundation inclut la [`BaseInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) classe qui fournit une implémentation par défaut de cette fonctionnalité requise.</span><span class="sxs-lookup"><span data-stu-id="47afb-128">The MRTK foundation includes the [`BaseInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) class which provides a default implementation of this required functionality.</span></span> <span data-ttu-id="47afb-129">Pour les appareils qui s’appuient sur la classe UInput de Unity, la [`UnityJoystickManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) classe peut être utilisée comme classe de base.</span><span class="sxs-lookup"><span data-stu-id="47afb-129">For devices that build upon Unity's UInput class, the [`UnityJoystickManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) class can be used as a base class.</span></span>

> [!Note]
> <span data-ttu-id="47afb-130">Les `BaseInputDeviceManager` `UnityJoystickManager` classes et fournissent l' `IMixedRealityInputDeviceManager` implémentation requise.</span><span class="sxs-lookup"><span data-stu-id="47afb-130">The `BaseInputDeviceManager` and `UnityJoystickManager` classes provide the required `IMixedRealityInputDeviceManager` implementation.</span></span>

```c#
public class WindowsMixedRealityDeviceManager :
    BaseInputDeviceManager,
    IMixedRealityCapabilityCheck
{ }
```

> <span data-ttu-id="47afb-131">`IMixedRealityCapabilityCheck` est utilisé par le `WindowsMixedRealityDeviceManager` pour indiquer qu’il fournit la prise en charge d’un ensemble de fonctionnalités d’entrée, en particulier des mains articulées, des mains et des contrôleurs de mouvement de mouvement de regard.</span><span class="sxs-lookup"><span data-stu-id="47afb-131">`IMixedRealityCapabilityCheck` is used by the `WindowsMixedRealityDeviceManager` to indicate that it provides support for a set of input capabilities, specifically; articulated hands, gaze-gesture-voice hands and motion controllers.</span></span>

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a><span data-ttu-id="47afb-132">Appliquer l’attribut MixedRealityDataProvider</span><span class="sxs-lookup"><span data-stu-id="47afb-132">Apply the MixedRealityDataProvider attribute</span></span>

<span data-ttu-id="47afb-133">Une étape clé de la création d’un fournisseur de données de système d’entrée consiste à appliquer l' [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attribut à la classe.</span><span class="sxs-lookup"><span data-stu-id="47afb-133">A key step of creating an input system data provider is to apply the [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attribute to the class.</span></span> <span data-ttu-id="47afb-134">Cette étape permet de définir le profil et la ou les plateformes par défaut pour le fournisseur, lorsqu’ils sont sélectionnés dans le profil de système d’entrée.</span><span class="sxs-lookup"><span data-stu-id="47afb-134">This step enables setting the default profile and platform(s) for the provider, when selected in the input system profile.</span></span>

```c#
[MixedRealityDataProvider(
    typeof(IMixedRealityInputSystem),
    SupportedPlatforms.WindowsUniversal,
    "Windows Mixed Reality Device Manager")]
public class WindowsMixedRealityDeviceManager :
    BaseInputDeviceManager,
    IMixedRealityCapabilityCheck
{ }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a><span data-ttu-id="47afb-135">Implémenter les méthodes IMixedRealityDataProvider</span><span class="sxs-lookup"><span data-stu-id="47afb-135">Implement the IMixedRealityDataProvider methods</span></span>

<span data-ttu-id="47afb-136">Une fois que la classe a été définie, l’étape suivante consiste à fournir l’implémentation de l' [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span><span class="sxs-lookup"><span data-stu-id="47afb-136">Once the class has been defined, the next step is to provide the implementation of the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!Note]
> <span data-ttu-id="47afb-137">La `BaseInputDeviceManager` classe, via la `BaseService` classe, fournit uniquement des implémentations vides pour les `IMixedRealityDataProvider` méthodes.</span><span class="sxs-lookup"><span data-stu-id="47afb-137">The `BaseInputDeviceManager` class, via the `BaseService` class, provides only empty implementations for `IMixedRealityDataProvider` methods.</span></span> <span data-ttu-id="47afb-138">Les détails de ces méthodes sont généralement spécifiques au fournisseur de données.</span><span class="sxs-lookup"><span data-stu-id="47afb-138">The details of these methods are generally data provider specific.</span></span>

<span data-ttu-id="47afb-139">Les méthodes qui doivent être implémentées par le fournisseur de données sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="47afb-139">The methods that should be implemented by the data provider are:</span></span>

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a><span data-ttu-id="47afb-140">Implémenter la logique du fournisseur de données</span><span class="sxs-lookup"><span data-stu-id="47afb-140">Implement the data provider logic</span></span>

<span data-ttu-id="47afb-141">L’étape suivante consiste à ajouter la logique de gestion des périphériques d’entrée, y compris les contrôleurs à prendre en charge.</span><span class="sxs-lookup"><span data-stu-id="47afb-141">The next step is to add the logic for managing the input devices, including any controllers to be supported.</span></span>

### <a name="implement-the-controller-classes"></a><span data-ttu-id="47afb-142">Implémenter les classes de contrôleur</span><span class="sxs-lookup"><span data-stu-id="47afb-142">Implement the controller classes</span></span>

 <span data-ttu-id="47afb-143">L’exemple de `WindowsMixedRealityDeviceManager` définit et implémente les classes de contrôleur suivantes.</span><span class="sxs-lookup"><span data-stu-id="47afb-143">The example of the `WindowsMixedRealityDeviceManager` defines and implements the following controller classes.</span></span>

> <span data-ttu-id="47afb-144">Le code source de chacune de ces classes se trouve dans le dossier MRTK/Providers/WindowsMixedReality.</span><span class="sxs-lookup"><span data-stu-id="47afb-144">The source code for each of these classes can be found in the MRTK/Providers/WindowsMixedReality folder.</span></span>

- <span data-ttu-id="47afb-145">WindowsMixedRealityArticulatedHand. cs</span><span class="sxs-lookup"><span data-stu-id="47afb-145">WindowsMixedRealityArticulatedHand.cs</span></span>
- <span data-ttu-id="47afb-146">WindowsMixedRealityController. cs</span><span class="sxs-lookup"><span data-stu-id="47afb-146">WindowsMixedRealityController.cs</span></span>
- <span data-ttu-id="47afb-147">WindowsMixedRealityGGVHand. cs</span><span class="sxs-lookup"><span data-stu-id="47afb-147">WindowsMixedRealityGGVHand.cs</span></span>

> [!Note]
> <span data-ttu-id="47afb-148">Tous les gestionnaires d’appareils ne prennent pas en charge plusieurs types de contrôleurs.</span><span class="sxs-lookup"><span data-stu-id="47afb-148">Not all device managers will support multiple controller types.</span></span>

#### <a name="apply-the-mixedrealitycontroller-attribute"></a><span data-ttu-id="47afb-149">Appliquer l’attribut MixedRealityController</span><span class="sxs-lookup"><span data-stu-id="47afb-149">Apply the MixedRealityController attribute</span></span>

<span data-ttu-id="47afb-150">Ensuite, appliquez l' [`MixedRealityController`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityControllerAttribute) attribut à la classe.</span><span class="sxs-lookup"><span data-stu-id="47afb-150">Next, apply the [`MixedRealityController`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityControllerAttribute) attribute to the class.</span></span> <span data-ttu-id="47afb-151">Cet attribut spécifie le type de contrôleur (par ex., la main), la main (par exemple : gauche ou droite) et une image de contrôleur facultative.</span><span class="sxs-lookup"><span data-stu-id="47afb-151">This attribute specifies the type of controller (ex: articulated hand), the handedness (ex: left or right) and an optional controller image.</span></span>

```c#
[MixedRealityController(
    SupportedControllerType.WindowsMixedReality,
    new[] { Handedness.Left, Handedness.Right },
    "StandardAssets/Textures/MotionController")]
{ }
```

#### <a name="configure-the-interaction-mappings"></a><span data-ttu-id="47afb-152">Configurer les mappages d’interaction</span><span class="sxs-lookup"><span data-stu-id="47afb-152">Configure the interaction mappings</span></span>

<span data-ttu-id="47afb-153">L’étape suivante consiste à définir l’ensemble de mappages d’interaction pris en charge par le contrôleur.</span><span class="sxs-lookup"><span data-stu-id="47afb-153">The next step is to define the set of interaction mappings supported by the controller.</span></span> <span data-ttu-id="47afb-154">Pour les appareils qui reçoivent leurs données via la classe d’entrée Unity, l' [outil de mappage de contrôleur](../tools/controller-mapping-tool.md) est une ressource utile pour confirmer les mappages d’axe et de bouton appropriés à attribuer aux interactions.</span><span class="sxs-lookup"><span data-stu-id="47afb-154">For devices that receive their data via Unity's Input class, the [controller mapping tool](../tools/controller-mapping-tool.md) is a helpful resource to confirm the correct axis and button mappings to assign to interactions.</span></span>

<span data-ttu-id="47afb-155">L’exemple suivant est abrégé de la `GenericOpenVRController` classe, qui se trouve dans le dossier MRTK/Providers/OpenVR.</span><span class="sxs-lookup"><span data-stu-id="47afb-155">The following example is abbreviated from the `GenericOpenVRController` class, located in the MRTK/Providers/OpenVR folder.</span></span>

```c#
public override MixedRealityInteractionMapping[] DefaultLeftHandedInteractions => new[]
{
    // Controller Pose
    new MixedRealityInteractionMapping(0, "Spatial Pointer", AxisType.SixDof, DeviceInputType.SpatialPointer, MixedRealityInputAction.None),
    // Left Trigger Squeeze
    new MixedRealityInteractionMapping(1, "Trigger Position", AxisType.SingleAxis, DeviceInputType.Trigger, ControllerMappingLibrary.AXIS_9),
    // Left Trigger Press (Select)
    new MixedRealityInteractionMapping(2, "Trigger Press (Select)", AxisType.Digital, DeviceInputType.TriggerPress, KeyCode.JoystickButton14),
};
```

>[!Note]
><span data-ttu-id="47afb-156">La [`ControllerMappingLibrary`](xref:Microsoft.MixedReality.Toolkit.Input.ControllerMappingLibrary) classe fournit des constantes symboliques pour l’axe d’entrée Unity et les définitions de bouton.</span><span class="sxs-lookup"><span data-stu-id="47afb-156">The [`ControllerMappingLibrary`](xref:Microsoft.MixedReality.Toolkit.Input.ControllerMappingLibrary) class provides symbolic constants for the Unity input axis and button definitions.</span></span>

### <a name="raise-notification-events"></a><span data-ttu-id="47afb-157">Déclencher des événements de notification</span><span class="sxs-lookup"><span data-stu-id="47afb-157">Raise notification events</span></span>

<span data-ttu-id="47afb-158">Pour permettre aux applications de répondre aux entrées de l’utilisateur, le fournisseur de données déclenche des événements de notification correspondant aux modifications de l’état du contrôleur, comme défini dans les [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) interfaces et.</span><span class="sxs-lookup"><span data-stu-id="47afb-158">To enable applications to respond to input from the user, the data provider raises notification events corresponding to controller state changes as defined in the [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) and [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) interfaces.</span></span>

<span data-ttu-id="47afb-159">Pour les contrôles de type numérique (bouton), déclenchez les événements OnInputDown et OnInputUp.</span><span class="sxs-lookup"><span data-stu-id="47afb-159">For digital (button) type controls, raise the OnInputDown and OnInputUp events.</span></span>

```c#
// inputAction is the input event that is to be raised.
if (interactionSourceState.touchpadPressed)
{
    InputSystem?.RaiseOnInputDown(InputSource, ControllerHandedness, inputAction);
}
else
{
    InputSystem?.RaiseOnInputUp(InputSource, ControllerHandedness, inputAction);
}
```

<span data-ttu-id="47afb-160">Pour les contrôles analogiques (par ex., position du pavé tactile), l’événement InputChanged doit être déclenché.</span><span class="sxs-lookup"><span data-stu-id="47afb-160">For analog controls (ex: touchpad position) the InputChanged event should be raised.</span></span>

```c#
InputSystem?.RaisePositionInputChanged(InputSource, ControllerHandedness, interactionMapping.MixedRealityInputAction, interactionSourceState.touchpadPosition);
```

### <a name="add-unity-profiler-instrumentation"></a><span data-ttu-id="47afb-161">Ajouter l’instrumentation du profileur Unity</span><span class="sxs-lookup"><span data-stu-id="47afb-161">Add Unity Profiler instrumentation</span></span>

<span data-ttu-id="47afb-162">Les performances sont essentielles dans les applications de réalité mixte.</span><span class="sxs-lookup"><span data-stu-id="47afb-162">Performance is critical in mixed reality applications.</span></span> <span data-ttu-id="47afb-163">Chaque composant ajoute une quantité de surcharge pour laquelle les applications doivent tenir compte.</span><span class="sxs-lookup"><span data-stu-id="47afb-163">Every component adds some amount of overhead for which applications must account.</span></span> <span data-ttu-id="47afb-164">À cette fin, il est important que tous les fournisseurs de données d’entrée contiennent l’instrumentation du profileur Unity dans la boucle interne et les chemins de code fréquemment utilisés.</span><span class="sxs-lookup"><span data-stu-id="47afb-164">To this end, it is important that all input data providers contain Unity Profiler instrumentation in inner loop and frequently utilized code paths.</span></span>

<span data-ttu-id="47afb-165">Il est recommandé d’implémenter le modèle utilisé par MRTK lors de l’instrumentation de fournisseurs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="47afb-165">It is recommended to implement the pattern utilized by the MRTK when instrumenting custom providers.</span></span>

```c#
        private static readonly ProfilerMarker GetOrAddControllerPerfMarker = new ProfilerMarker("[MRTK] WindowsMixedRealityDeviceManager.GetOrAddController");

        private async void GetOrAddController(InteractionSourceState interactionSourceState)
        {
            using (GetOrAddControllerPerfMarker.Auto())
            {
                // Code to be measured.
            }
        }
```

> [!Note]
> <span data-ttu-id="47afb-166">Le nom utilisé pour identifier le marqueur du profileur est arbitraire.</span><span class="sxs-lookup"><span data-stu-id="47afb-166">The name used to identify the profiler marker is arbitrary.</span></span> <span data-ttu-id="47afb-167">MRTK utilise le modèle suivant.</span><span class="sxs-lookup"><span data-stu-id="47afb-167">The MRTK uses the following pattern.</span></span>
>
> <span data-ttu-id="47afb-168">"[Product] className. methodName-Optional note"</span><span class="sxs-lookup"><span data-stu-id="47afb-168">"[product] className.methodName - optional note"</span></span>
>
> <span data-ttu-id="47afb-169">Il est recommandé que les fournisseurs de données personnalisés suivent un modèle similaire pour simplifier l’identification des composants et des méthodes spécifiques lors de l’analyse des traces.</span><span class="sxs-lookup"><span data-stu-id="47afb-169">It is recommended that custom data providers follow a similar pattern to help simplify identification of specific components and methods when analyzing traces.</span></span>

## <a name="create-the-profile-and-inspector"></a><span data-ttu-id="47afb-170">Créer le profil et l’inspecteur</span><span class="sxs-lookup"><span data-stu-id="47afb-170">Create the profile and inspector</span></span>

<span data-ttu-id="47afb-171">dans la Shared Computer Toolkit de la réalité mixte, les fournisseurs de données sont configurés à l’aide de [profils](../profiles/profiles.md).</span><span class="sxs-lookup"><span data-stu-id="47afb-171">In the Mixed Reality Toolkit, data providers are configured using [profiles](../profiles/profiles.md).</span></span>

<span data-ttu-id="47afb-172">Les fournisseurs de données avec des options de configuration supplémentaires (ex : [InputSimulationService](../input-simulation/input-simulation-service.md)) doivent créer un profil et un inspecteur pour permettre aux clients de modifier le comportement en fonction des besoins de l’application.</span><span class="sxs-lookup"><span data-stu-id="47afb-172">Data providers with additional configuration options (ex: [InputSimulationService](../input-simulation/input-simulation-service.md)) should create a profile and inspector to allow customers to modify the behavior to best suit the needs of the application.</span></span>

> <span data-ttu-id="47afb-173">Le code complet de l’exemple de cette section se trouve dans le MRTK. Dossier services/InputSimulation.</span><span class="sxs-lookup"><span data-stu-id="47afb-173">The complete code for the example in this section can be found in the MRTK.Services/InputSimulation folder.</span></span>

### <a name="define-the-profile"></a><span data-ttu-id="47afb-174">Définir le profil</span><span class="sxs-lookup"><span data-stu-id="47afb-174">Define the profile</span></span>

<span data-ttu-id="47afb-175">Le contenu du profil doit refléter les propriétés accessibles de l’observateur (par ex., intervalle de mise à jour).</span><span class="sxs-lookup"><span data-stu-id="47afb-175">Profile contents should mirror the accessible properties of the observer (ex: update interval).</span></span> <span data-ttu-id="47afb-176">Toutes les propriétés configurables par l’utilisateur définies dans chaque interface doivent être contenues dans le profil.</span><span class="sxs-lookup"><span data-stu-id="47afb-176">All of the user configurable properties defined in each interface should be contained with the profile.</span></span>

```c#
[CreateAssetMenu(
    menuName = "Mixed Reality Toolkit/Profiles/Mixed Reality Simulated Input Profile",
    fileName = "MixedRealityInputSimulationProfile",
    order = (int)CreateProfileMenuItemIndices.InputSimulation)]
public class MixedRealityInputSimulationProfile : BaseMixedRealityProfile
{ }
```

<span data-ttu-id="47afb-177">l' `CreateAssetMenu` attribut peut être appliqué à la classe de profil pour permettre aux clients de créer une instance de profil à l’aide du menu **créer des ressources > > Shared Computer Toolkit de la réalité mixte > des profils** .</span><span class="sxs-lookup"><span data-stu-id="47afb-177">The `CreateAssetMenu` attribute can be applied to the profile class to enable customers to create a profile instance using the **Create > Assets > Mixed Reality Toolkit > Profiles** menu.</span></span>

### <a name="implement-the-inspector"></a><span data-ttu-id="47afb-178">Implémenter l’inspecteur</span><span class="sxs-lookup"><span data-stu-id="47afb-178">Implement the inspector</span></span>

<span data-ttu-id="47afb-179">Les inspecteurs de profil sont l’interface utilisateur permettant de configurer et d’afficher le contenu des profils.</span><span class="sxs-lookup"><span data-stu-id="47afb-179">Profile inspectors are the user interface for configuring and viewing profile contents.</span></span> <span data-ttu-id="47afb-180">Chaque inspecteur de profil doit étendre la classe [« BaseMixedRealityToolkitConfigurationProfileInspector »](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) .</span><span class="sxs-lookup"><span data-stu-id="47afb-180">Each profile inspector should extend the [\`BaseMixedRealityToolkitConfigurationProfileInspector](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) class.</span></span>

```c#
[CustomEditor(typeof(MixedRealityInputSimulationProfile))]
public class MixedRealityInputSimulationProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

<span data-ttu-id="47afb-181">L' `CustomEditor` attribut indique à Unity le type de ressource auquel s’applique l’inspecteur.</span><span class="sxs-lookup"><span data-stu-id="47afb-181">The `CustomEditor` attribute informs Unity the type of asset to which the inspector applies.</span></span>

## <a name="create-assembly-definitions"></a><span data-ttu-id="47afb-182">Créer une ou plusieurs définitions d’assembly</span><span class="sxs-lookup"><span data-stu-id="47afb-182">Create assembly definition(s)</span></span>

<span data-ttu-id="47afb-183">la réalité mixte Shared Computer Toolkit utilise des fichiers de définition d’assembly ([. asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) pour spécifier les dépendances entre les composants, ainsi que pour aider unity à réduire le temps de compilation.</span><span class="sxs-lookup"><span data-stu-id="47afb-183">The Mixed Reality Toolkit uses assembly definition ([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) files to specify dependencies between components as well as to assist Unity in reducing compilation time.</span></span>

<span data-ttu-id="47afb-184">Il est recommandé de créer des fichiers de définition d’assembly pour tous les fournisseurs de données et leurs composants d’éditeur.</span><span class="sxs-lookup"><span data-stu-id="47afb-184">It is recommended that assembly definition files are created for all data providers and their editor components.</span></span>

<span data-ttu-id="47afb-185">À l’aide de la [structure de dossiers](#recommended-folder-structure) dans l’exemple précédent, il existe deux fichiers. asmdef pour le fournisseur de données ContosoInput.</span><span class="sxs-lookup"><span data-stu-id="47afb-185">Using the [folder structure](#recommended-folder-structure) in the earlier example, there would be two .asmdef files for the ContosoInput data provider.</span></span>

<span data-ttu-id="47afb-186">La première définition d’assembly est pour le fournisseur de données.</span><span class="sxs-lookup"><span data-stu-id="47afb-186">The first assembly definition is for the data provider.</span></span> <span data-ttu-id="47afb-187">Pour cet exemple, il est appelé ContosoInput et se trouve dans le dossier ContosoInput de l’exemple.</span><span class="sxs-lookup"><span data-stu-id="47afb-187">For this example, it will be called ContosoInput and will be located in the example's ContosoInput folder.</span></span>
<span data-ttu-id="47afb-188">Cette définition d’assembly doit spécifier une dépendance sur Microsoft. MixedReality. Shared Computer Toolkit et tout autre assembly dont il dépend.</span><span class="sxs-lookup"><span data-stu-id="47afb-188">This assembly definition must specify a dependency on Microsoft.MixedReality.Toolkit and any other assemblies upon which it depends.</span></span>

<span data-ttu-id="47afb-189">La définition de l’assembly ContosoInputEditor spécifie l’inspecteur de profil et tout code spécifique à l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="47afb-189">The ContosoInputEditor assembly definition will specify the profile inspector and any editor specific code.</span></span> <span data-ttu-id="47afb-190">Ce fichier doit se trouver dans le dossier racine du code de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="47afb-190">This file must be located in the root folder of the editor code.</span></span> <span data-ttu-id="47afb-191">Dans cet exemple, le fichier se trouve dans le dossier ContosoInput\Editor</span><span class="sxs-lookup"><span data-stu-id="47afb-191">In this example, the file will be located in the ContosoInput\Editor folder.</span></span> <span data-ttu-id="47afb-192">Cette définition d’assembly contient une référence à l’assembly ContosoInput, ainsi que les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="47afb-192">This assembly definition will contain a reference to the ContosoInput assembly as well as:</span></span>

- <span data-ttu-id="47afb-193">Microsoft. MixedReality. Shared Computer Toolkit</span><span class="sxs-lookup"><span data-stu-id="47afb-193">Microsoft.MixedReality.Toolkit</span></span>
- <span data-ttu-id="47afb-194">Microsoft. MixedReality. Shared Computer Toolkit. Editor. Inspectors</span><span class="sxs-lookup"><span data-stu-id="47afb-194">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span></span>
- <span data-ttu-id="47afb-195">Microsoft. MixedReality. Shared Computer Toolkit. Éditeur. Utilities</span><span class="sxs-lookup"><span data-stu-id="47afb-195">Microsoft.MixedReality.Toolkit.Editor.Utilities</span></span>

## <a name="register-the-data-provider"></a><span data-ttu-id="47afb-196">Inscrire le fournisseur de données</span><span class="sxs-lookup"><span data-stu-id="47afb-196">Register the data provider</span></span>

<span data-ttu-id="47afb-197">Une fois créé, le fournisseur de données peut être inscrit avec le système d’entrée et être utilisé dans l’application.</span><span class="sxs-lookup"><span data-stu-id="47afb-197">Once created, the data provider can be registered with the input system and be used in the application.</span></span>

![Fournisseurs de données de système d’entrée inscrits](../images/input/RegisteredServiceProviders.PNG)

## <a name="packaging-and-distribution"></a><span data-ttu-id="47afb-199">Packaging et distribution</span><span class="sxs-lookup"><span data-stu-id="47afb-199">Packaging and distribution</span></span>

<span data-ttu-id="47afb-200">Les fournisseurs de données qui sont distribués en tant que composants tiers ont les détails spécifiques de l’empaquetage et de la distribution laissés à la préférence du développeur.</span><span class="sxs-lookup"><span data-stu-id="47afb-200">Data providers that are distributed as third party components have the specific details of packaging and distribution left to the preference of the developer.</span></span> <span data-ttu-id="47afb-201">Il est probable que la solution la plus courante consiste à générer un. pour Unity et à le distribuer via le magasin d’actifs Unity.</span><span class="sxs-lookup"><span data-stu-id="47afb-201">Likely, the most common solution will be to generate a .unitypackage and distribute via the Unity Asset Store.</span></span>

<span data-ttu-id="47afb-202">si un fournisseur de données est soumis et accepté dans le cadre du package Shared Computer Toolkit de la réalité mixte microsoft, l’équipe microsoft MRTK l’empaqueter et la distribuer dans le cadre des offres MRTK.</span><span class="sxs-lookup"><span data-stu-id="47afb-202">If a data provider is submitted and accepted as a part of the Microsoft Mixed Reality Toolkit package, the Microsoft MRTK team will package and distribute it as part of the MRTK offerings.</span></span>

## <a name="see-also"></a><span data-ttu-id="47afb-203">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47afb-203">See also</span></span>

- [<span data-ttu-id="47afb-204">Système d’entrée</span><span class="sxs-lookup"><span data-stu-id="47afb-204">Input system</span></span>](overview.md)
- [<span data-ttu-id="47afb-205">Classe `BaseInputDeviceManager`</span><span class="sxs-lookup"><span data-stu-id="47afb-205">`BaseInputDeviceManager` class</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager)
- [<span data-ttu-id="47afb-206">`IMixedRealityInputDeviceManager` interface</span><span class="sxs-lookup"><span data-stu-id="47afb-206">`IMixedRealityInputDeviceManager` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager)
- [<span data-ttu-id="47afb-207">`IMixedRealityInputHandler` interface</span><span class="sxs-lookup"><span data-stu-id="47afb-207">`IMixedRealityInputHandler` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler)
- [<span data-ttu-id="47afb-208">`IMixedRealityInputHandler<T>` interface</span><span class="sxs-lookup"><span data-stu-id="47afb-208">`IMixedRealityInputHandler<T>` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1)
- [<span data-ttu-id="47afb-209">`IMixedRealityDataProvider` interface</span><span class="sxs-lookup"><span data-stu-id="47afb-209">`IMixedRealityDataProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [<span data-ttu-id="47afb-210">`IMixedRealityCapabilityCheck` interface</span><span class="sxs-lookup"><span data-stu-id="47afb-210">`IMixedRealityCapabilityCheck` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [<span data-ttu-id="47afb-211">Outil de mappage de contrôleur</span><span class="sxs-lookup"><span data-stu-id="47afb-211">Controller Mapping Tool</span></span>](../tools/controller-mapping-tool.md)
