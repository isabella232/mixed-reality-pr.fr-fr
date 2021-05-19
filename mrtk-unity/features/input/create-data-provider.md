---
title: Création de fournisseurs de données d’entrée
description: documentation pour créer un système d’entrée et un fournisseur de données dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, développement, MRTK
ms.openlocfilehash: c164fa406ae6822f4d889aff3bf615cf7fa76337
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144074"
---
# <a name="creating-an-input-system-data-provider"></a>Création d’un fournisseur de données de système d’entrée

Le système d’entrée de la réalité mixte Toolkit est un système extensible permettant d’activer la prise en charge des périphériques d’entrée. Pour ajouter la prise en charge d’une nouvelle plateforme matérielle, un fournisseur de données d’entrée personnalisé peut être nécessaire.

Cet article explique comment créer des fournisseurs de données personnalisés, également appelés gestionnaires d’appareils, pour le système d’entrée. L’exemple de code présenté ici provient de [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) .

> Le code complet utilisé dans cet exemple se trouve dans le dossier MRTK/Providers/WindowsMixedReality.

## <a name="namespace-and-folder-structure"></a>Structure de l’espace de noms et du dossier

Les fournisseurs de données peuvent être distribués en tant que complément tiers ou dans le cadre de la boîte à outils Microsoft Mixed Reality Toolkit. Le processus d’approbation pour les envois de nouveaux fournisseurs de données à l’MRTK varie au cas par cas et est communiqué au moment de la proposition initiale.

> [!Important]
> Si un fournisseur de données de système d’entrée est soumis au référentiel du kit d’outils de la [réalité mixte](https://github.com/Microsoft/MixedRealityToolkit-Unity), l’espace de noms **doit** commencer par Microsoft. MixedReality. Toolkit (par exemple, Microsoft. MixedReality. Toolkit. WindowsMixedReality) et le code doit se trouver dans un dossier sous MRTK/Providers (ex : MRTK/Providers/WindowsMixedReality).

### <a name="namespace"></a>Espace de noms

Les fournisseurs de données doivent disposer d’un espace de noms pour atténuer les conflits de noms potentiels. Il est recommandé que l’espace de noms inclue les composants suivants.

- Nom de la société
- Domaine de fonctionnalité

Par exemple, un fournisseur de données d’entrée créé par la société contoso peut être « contoso. MixedReality. Toolkit. Input ».

### <a name="recommended-folder-structure"></a>Structure de dossiers recommandée

Il est recommandé que le code source des fournisseurs de données soit disposé dans une hiérarchie de dossiers, comme indiqué dans l’image suivante.

![Exemple de structure de dossiers](../images/input/ExampleProviderFolderStructure.png)

Où ContosoInput contient l’implémentation du fournisseur de données, le dossier de l’éditeur contient l’inspecteur (et tout autre code spécifique à l’éditeur Unity), le dossier textures contient des images des contrôleurs pris en charge, et les profils contiennent un ou plusieurs profils prédéfinis.

> [!Note]
> Certaines images de contrôleur courantes se trouvent dans le dossier MixedRealityToolkit\StandardAssets\Textures.

## <a name="implement-the-data-provider"></a>Implémenter le fournisseur de données

### <a name="specify-interface-andor-base-class-inheritance"></a>Spécifier l’héritage de l’interface et/ou de la classe de base

Tous les fournisseurs de données de système d’entrée doivent implémenter l' [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interface, qui spécifie les fonctionnalités minimales requises par le système d’entrée. MRTK Foundation inclut la [`BaseInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) classe qui fournit une implémentation par défaut de cette fonctionnalité requise. Pour les appareils qui s’appuient sur la classe UInput de Unity, la [`UnityJoystickManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) classe peut être utilisée comme classe de base.

> [!Note]
> Les `BaseInputDeviceManager` `UnityJoystickManager` classes et fournissent l' `IMixedRealityInputDeviceManager` implémentation requise.

```c#
public class WindowsMixedRealityDeviceManager :
    BaseInputDeviceManager,
    IMixedRealityCapabilityCheck
{ }
```

> `IMixedRealityCapabilityCheck` est utilisé par le `WindowsMixedRealityDeviceManager` pour indiquer qu’il fournit la prise en charge d’un ensemble de fonctionnalités d’entrée, en particulier des mains articulées, des mains et des contrôleurs de mouvement de mouvement de regard.

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a>Appliquer l’attribut MixedRealityDataProvider

Une étape clé de la création d’un fournisseur de données de système d’entrée consiste à appliquer l' [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attribut à la classe. Cette étape permet de définir le profil et la ou les plateformes par défaut pour le fournisseur, lorsqu’ils sont sélectionnés dans le profil de système d’entrée.

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

### <a name="implement-the-imixedrealitydataprovider-methods"></a>Implémenter les méthodes IMixedRealityDataProvider

Une fois que la classe a été définie, l’étape suivante consiste à fournir l’implémentation de l' [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.

> [!Note]
> La `BaseInputDeviceManager` classe, via la `BaseService` classe, fournit uniquement des implémentations vides pour les `IMixedRealityDataProvider` méthodes. Les détails de ces méthodes sont généralement spécifiques au fournisseur de données.

Les méthodes qui doivent être implémentées par le fournisseur de données sont les suivantes :

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a>Implémenter la logique du fournisseur de données

L’étape suivante consiste à ajouter la logique de gestion des périphériques d’entrée, y compris les contrôleurs à prendre en charge.

### <a name="implement-the-controller-classes"></a>Implémenter les classes de contrôleur

 L’exemple de `WindowsMixedRealityDeviceManager` définit et implémente les classes de contrôleur suivantes.

> Le code source de chacune de ces classes se trouve dans le dossier MRTK/Providers/WindowsMixedReality.

- WindowsMixedRealityArticulatedHand. cs
- WindowsMixedRealityController. cs
- WindowsMixedRealityGGVHand. cs

> [!Note]
> Tous les gestionnaires d’appareils ne prennent pas en charge plusieurs types de contrôleurs.

#### <a name="apply-the-mixedrealitycontroller-attribute"></a>Appliquer l’attribut MixedRealityController

Ensuite, appliquez l' [`MixedRealityController`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityControllerAttribute) attribut à la classe. Cet attribut spécifie le type de contrôleur (par ex., la main), la main (par exemple : gauche ou droite) et une image de contrôleur facultative.

```c#
[MixedRealityController(
    SupportedControllerType.WindowsMixedReality,
    new[] { Handedness.Left, Handedness.Right },
    "StandardAssets/Textures/MotionController")]
{ }
```

#### <a name="configure-the-interaction-mappings"></a>Configurer les mappages d’interaction

L’étape suivante consiste à définir l’ensemble de mappages d’interaction pris en charge par le contrôleur. Pour les appareils qui reçoivent leurs données via la classe d’entrée Unity, l' [outil de mappage de contrôleur](../tools/controller-mapping-tool.md) est une ressource utile pour confirmer les mappages d’axe et de bouton appropriés à attribuer aux interactions.

L’exemple suivant est abrégé de la `GenericOpenVRController` classe, qui se trouve dans le dossier MRTK/Providers/OpenVR.

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
>La [`ControllerMappingLibrary`](xref:Microsoft.MixedReality.Toolkit.Input.ControllerMappingLibrary) classe fournit des constantes symboliques pour l’axe d’entrée Unity et les définitions de bouton.

### <a name="raise-notification-events"></a>Déclencher des événements de notification

Pour permettre aux applications de répondre aux entrées de l’utilisateur, le fournisseur de données déclenche des événements de notification correspondant aux modifications de l’état du contrôleur, comme défini dans les [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) interfaces et.

Pour les contrôles de type numérique (bouton), déclenchez les événements OnInputDown et OnInputUp.

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

Pour les contrôles analogiques (par ex., position du pavé tactile), l’événement InputChanged doit être déclenché.

```c#
InputSystem?.RaisePositionInputChanged(InputSource, ControllerHandedness, interactionMapping.MixedRealityInputAction, interactionSourceState.touchpadPosition);
```

### <a name="add-unity-profiler-instrumentation"></a>Ajouter l’instrumentation du profileur Unity

Les performances sont essentielles dans les applications de réalité mixte. Chaque composant ajoute une quantité de surcharge pour laquelle les applications doivent tenir compte. À cette fin, il est important que tous les fournisseurs de données d’entrée contiennent l’instrumentation du profileur Unity dans la boucle interne et les chemins de code fréquemment utilisés.

Il est recommandé d’implémenter le modèle utilisé par MRTK lors de l’instrumentation de fournisseurs personnalisés.

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
> Le nom utilisé pour identifier le marqueur du profileur est arbitraire. MRTK utilise le modèle suivant.
>
> "[Product] className. methodName-Optional note"
>
> Il est recommandé que les fournisseurs de données personnalisés suivent un modèle similaire pour simplifier l’identification des composants et des méthodes spécifiques lors de l’analyse des traces.

## <a name="create-the-profile-and-inspector"></a>Créer le profil et l’inspecteur

Dans la boîte à outils de la réalité mixte, les fournisseurs de données sont configurés à l’aide de [profils](../profiles/profiles.md).

Les fournisseurs de données avec des options de configuration supplémentaires (ex : [InputSimulationService](../input-simulation/input-simulation-service.md)) doivent créer un profil et un inspecteur pour permettre aux clients de modifier le comportement en fonction des besoins de l’application.

> Le code complet de l’exemple de cette section se trouve dans le MRTK. Dossier services/InputSimulation.

### <a name="define-the-profile"></a>Définir le profil

Le contenu du profil doit refléter les propriétés accessibles de l’observateur (par ex., intervalle de mise à jour). Toutes les propriétés configurables par l’utilisateur définies dans chaque interface doivent être contenues dans le profil.

```c#
[CreateAssetMenu(
    menuName = "Mixed Reality Toolkit/Profiles/Mixed Reality Simulated Input Profile",
    fileName = "MixedRealityInputSimulationProfile",
    order = (int)CreateProfileMenuItemIndices.InputSimulation)]
public class MixedRealityInputSimulationProfile : BaseMixedRealityProfile
{ }
```

L' `CreateAssetMenu` attribut peut être appliqué à la classe de profil pour permettre aux clients de créer une instance de profil à l’aide du menu **créer des ressources > > > profils du kit de ressources de réalité mixte** .

### <a name="implement-the-inspector"></a>Implémenter l’inspecteur

Les inspecteurs de profil sont l’interface utilisateur permettant de configurer et d’afficher le contenu des profils. Chaque inspecteur de profil doit étendre la classe [« BaseMixedRealityToolkitConfigurationProfileInspector »](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) .

```c#
[CustomEditor(typeof(MixedRealityInputSimulationProfile))]
public class MixedRealityInputSimulationProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

L' `CustomEditor` attribut indique à Unity le type de ressource auquel s’applique l’inspecteur.

## <a name="create-assembly-definitions"></a>Créer une ou plusieurs définitions d’assembly

La boîte à outils de réalité mixte utilise des fichiers de définition d’assembly ([. asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) pour spécifier les dépendances entre les composants, ainsi que pour aider Unity à réduire le temps de compilation.

Il est recommandé de créer des fichiers de définition d’assembly pour tous les fournisseurs de données et leurs composants d’éditeur.

À l’aide de la [structure de dossiers](#recommended-folder-structure) dans l’exemple précédent, il existe deux fichiers. asmdef pour le fournisseur de données ContosoInput.

La première définition d’assembly est pour le fournisseur de données. Pour cet exemple, il est appelé ContosoInput et se trouve dans le dossier ContosoInput de l’exemple.
Cette définition d’assembly doit spécifier une dépendance sur Microsoft. MixedReality. Toolkit et tout autre assembly dont elle dépend.

La définition de l’assembly ContosoInputEditor spécifie l’inspecteur de profil et tout code spécifique à l’éditeur. Ce fichier doit se trouver dans le dossier racine du code de l’éditeur. Dans cet exemple, le fichier se trouve dans le dossier ContosoInput\Editor Cette définition d’assembly contient une référence à l’assembly ContosoInput, ainsi que les éléments suivants :

- Microsoft. MixedReality. Toolkit
- Microsoft. MixedReality. Toolkit. Editor. Inspectors
- Microsoft. MixedReality. Toolkit. Editor. Utilities

## <a name="register-the-data-provider"></a>Inscrire le fournisseur de données

Une fois créé, le fournisseur de données peut être inscrit avec le système d’entrée et être utilisé dans l’application.

![Fournisseurs de données de système d’entrée inscrits](../images/input/RegisteredServiceProviders.PNG)

## <a name="packaging-and-distribution"></a>Packaging et distribution

Les fournisseurs de données qui sont distribués en tant que composants tiers ont les détails spécifiques de l’empaquetage et de la distribution laissés à la préférence du développeur. Il est probable que la solution la plus courante consiste à générer un. pour Unity et à le distribuer via le magasin d’actifs Unity.

Si un fournisseur de données est soumis et accepté dans le cadre du package Microsoft Mixed Reality Toolkit, l’équipe Microsoft MRTK l’empaqueter et la distribuer dans le cadre des offres MRTK.

## <a name="see-also"></a>Voir aussi

- [Système d’entrée](overview.md)
- [Classe `BaseInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager)
- [`IMixedRealityInputDeviceManager` interface](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager)
- [`IMixedRealityInputHandler` interface](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler)
- [`IMixedRealityInputHandler<T>` interface](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1)
- [`IMixedRealityDataProvider` interface](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [`IMixedRealityCapabilityCheck` interface](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [Outil de mappage de contrôleur](../tools/controller-mapping-tool.md)
