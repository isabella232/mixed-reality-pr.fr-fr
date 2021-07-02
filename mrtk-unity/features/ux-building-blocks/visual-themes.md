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
# <a name="visual-themes"></a>Thèmes visuels

Les thèmes permettent de contrôler de façon flexible les ressources de l’expérience utilisateur en réponse à différentes transitions d’États. Cela peut impliquer la modification de la couleur d’un bouton, le redimensionnement d’un élément en réponse à un focus, etc. L’infrastructure de thèmes visuels est composée de deux éléments clés : 1) configuration et 2) moteurs d’exécution.

Les [configurations de thème](#theme-configuration) sont des définitions de propriétés et de types, tandis que les moteurs de [thèmes](#theme-engines) sont des classes qui consomment les configurations et implémentent la logique pour mettre à jour les transformations, les matériaux et bien plus encore lors de l’exécution.

## <a name="theme-configuration"></a>Configuration du thème

Les configurations de thème sont des [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) qui définissent la façon dont les moteurs de thème seront initialisés au moment de l’exécution. Elles définissent les propriétés et les valeurs à utiliser en réponse à des modifications d’entrée ou d’état lors de l’exécution de l’application. En tant que ressources [ScriptableObjects](https://docs.unity3d.com/Manual/class-ScriptableObject.html) , les configurations de thème peuvent être définies une seule fois, puis réutilisées sur différents composants d’expérience utilisateur.

Pour créer un [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) élément multimédia :

1) cliquez avec le bouton droit dans la *fenêtre Project*
1) sélectionner **créer** une  >  **réalité mixte Shared Computer Toolkit**  >  **thème**

Vous trouverez des exemples de ressources de configuration de thème sous `MRTK/SDK/Features/UX/Interactable/Themes` .

![Exemple de ScriptableObject de thème dans Inspector](../images/visual-themes/ThemeInspectorExample.png)

### <a name="states"></a>États

Lorsque vous créez un nouveau [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) , la première chose à définir est celle des États disponibles. La propriété *States* indique le nombre de valeurs qu’une configuration de thème doit définir, car il y aura une valeur par État. Dans l’exemple d’image ci-dessus, les [États par défaut définis pour le](interactable.md#general-input-settings) composant pouvant être interagi sont *default*, *focus*, *appuyé* et *Disabled*. Celles-ci sont définies dans le `DefaultInteractableStates` fichier d’élément multimédia (ressources/MRTK/Kit de développement logiciel/fonctionnalités/expérience utilisateur/États).

Pour créer un [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) élément multimédia :

1) cliquez avec le bouton droit dans la *fenêtre Project*
1) sélectionner **créer** une  >  **réalité mixte Shared Computer Toolkit** l'  >  **état**

![Exemple ScriptableObject States dans Inspector](../images/interactable/DefaultInteractableStates.png)

Un [`State`](xref:Microsoft.MixedReality.Toolkit.UI.States) ScriptableObject définit à la fois la liste des États et le type de *StateModel* à créer pour ces États. Un *StateModel* est une classe qui étend [`BaseStateModel`](xref:Microsoft.MixedReality.Toolkit.UI.BaseStateModel) et implémente la logique de l’ordinateur d’État pour générer l’état actuel au moment de l’exécution. L’état actuel de cette classe est généralement utilisé par les moteurs de thème au moment de l’exécution pour dicter les valeurs à définir par rapport aux propriétés de matériau, aux transformations GameObject, etc.

### <a name="theme-engine-properties"></a>Propriétés du moteur de thèmes

En dehors des *États*, un [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) élément multimédia définit également une liste de moteurs de thèmes et les propriétés associées pour ces moteurs. Un [moteur de thème](#theme-engines) définit à nouveau la logique pour définir les valeurs correctes par rapport à un gameobject au moment de l’exécution.

Un [`Theme`](xref:Microsoft.MixedReality.Toolkit.UI.Theme) élément multimédia peut définir plusieurs moteurs de thèmes pour obtenir des transitions d’États visuels sophistiquées ciblant plusieurs propriétés GameObject.

**Runtime du thème**

Définit le type de classe du moteur de thème qui sera créé

**Simplifier**

Certains *moteurs de thèmes*, s’ils définissent leur propriété [IsEasingSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported) comme true, prennent en charge l’accélération entre les États. Par exemple, lerping entre deux couleurs quand un changement d’État se produit. La *durée* définit, en secondes, le délai d’exécution de la valeur de début à la valeur de fin et la *courbe d’animation* définit le taux de modification au cours de cette période.

**Propriétés du nuanceur**

Certains *moteurs de thèmes*, s’ils définissent leur propriété [AreShadersSupported](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported) sur true, modifient les propriétés de nuanceur spécifiques au moment de l’exécution. Les champs de *nuanceur* et de *propriété* définissent la propriété de nuanceur à cibler.

### <a name="create-a-theme-configuration-via-code"></a>Créer une configuration de thème par le biais du code

En général, il est plus facile de concevoir des configurations de thème via l’inspecteur Unity, mais il existe des cas où les thèmes doivent être générés dynamiquement au moment de l’exécution via du code. L’extrait de code ci-dessous fournit un exemple de la façon d’accomplir cette tâche.

Pour accélérer le développement, les méthodes d’assistance suivantes sont utiles pour simplifier l’installation.

[`Interactable.GetDefaultInteractableStates()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) -crée un ScriptableObject d’États avec les quatre valeurs d’État par défaut utilisées dans le composant [interagissant](interactable.md) .

[`ThemeDefinition.GetDefaultThemeDefinition<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) -Chaque moteur de thèmes définit une configuration par défaut avec les propriétés appropriées nécessaires pour ce type de Runtime de thème. Cette application d’assistance crée une définition pour le type de moteur de thème donné.

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

## <a name="theme-engines"></a>Moteurs de thèmes

Un [moteur de thèmes](#theme-engines) est une classe qui s’étend de la [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) classe. Ces classes sont instanciées au moment de l’exécution et configurées avec un [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) objet comme décrit précédemment.

### <a name="default-theme-engines"></a>Moteurs de thèmes par défaut

MRTK est fourni avec un ensemble par défaut de moteurs de thèmes listés ci-dessous :

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

Les moteurs de thèmes par défaut se trouvent sous `MRTK/SDK/Features/UX/Scripts/VisualThemes/ThemeEngines` .

### <a name="custom-theme-engines"></a>Moteurs de thèmes personnalisés

Comme indiqué, un moteur de thèmes est défini en tant que classe qui s’étend de la [`InteractableThemeBase`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase) classe. Ainsi, le nouveau moteur de thème n’a besoin que d’étendre cette classe et d’implémenter les éléments suivants :

#### <a name="mandatory-implementations"></a>Implémentations obligatoires

`public abstract void SetValue(ThemeStateProperty property, int index, float percentage)`(XREF : Microsoft. MixedReality. Shared Computer Toolkit. L'. InteractableThemeBase. SetValue)

Pour la propriété donnée, qui peut être identifiée par `ThemeStateProperty.Name` , définissez sa valeur d’État actuelle sur l’hôte gameobject ciblé (c.-à-d. Définissez la couleur de la matière, etc.). L' *index* indique la valeur d’État actuelle à laquelle accéder et le *pourcentage*, une valeur float comprise entre 0 et 1, est utilisé pour l’accélération/la lerping entre les valeurs.

`public abstract ThemePropertyValue GetProperty(ThemeStateProperty property)`(XREF : Microsoft. MixedReality. Shared Computer Toolkit. L'. InteractableThemeBase. GetProperty)

Pour la propriété donnée, qui peut être identifiée par `ThemeStateProperty.Name` , retournez la valeur actuelle définie sur le gameobject hôte ciblé (c.-à-d. la couleur matérielle actuelle, l’offset de position local actuel, etc.). Cela est principalement utilisé pour la mise en cache de la valeur de début lors de l’accélération entre les États.

`public abstract ThemeDefinition GetDefaultThemeDefinition()`(XREF : Microsoft. MixedReality. Shared Computer Toolkit. L'. InteractableThemeBase.GetDefaultThemeDefinition)

Retourne un [`ThemeDefinition`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition) objet qui définit les propriétés et la configuration par défaut nécessaires pour le thème personnalisé

`protected abstract void SetValue(ThemeStateProperty property, ThemePropertyValue value)`

Variante protégée de la `SetValue()` définition publique, à l’exception de ThemePropertyValue fournies, à définir au lieu de rediriger l’utilisation de la configuration de l’index et/ou du pourcentage.

#### <a name="recommended-overrides"></a>Remplacements recommandés

[`InteractableThemeBase.Init(GameObject host, ThemeDefinition settings)`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase)

Effectuez toutes les étapes d’initialisation en ciblant le paramètre *gameobject* fourni et en utilisant les propriétés et les configurations définies dans le paramètre *ThemeDefinition* . Il est recommandé d’appeler `base.Init(host, settings)` au début d’une substitution.

[`InteractableThemeBase.IsEasingSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.IsEasingSupported)

Si le moteur de thèmes personnalisé peut prendre en charge l’accélération entre les valeurs configurées via la [`ThemeDefinition.Easing`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeDefinition.Easing) propriété.

[`InteractableThemeBase.AreShadersSupported`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.AreShadersSupported)

Si le moteur de thèmes personnalisé peut prendre en charge le ciblage des propriétés du nuanceur. Il est recommandé d’étendre à [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) pour tirer parti de l’infrastructure existante pour définir/récupérer efficacement des propriétés de nuanceur via [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html). Les informations de propriété du nuanceur sont stockées dans chaque [`ThemeStateProperty`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty) via [`ThemeStateProperty.TargetShader`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.TargetShader) et [`ThemeStateProperty.ShaderPropertyName`](xref:Microsoft.MixedReality.Toolkit.UI.ThemeStateProperty.ShaderPropertyName) .

> [!NOTE]
> En cas [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) d’extension, il peut également être utile de remplacer [InteractableShaderTheme. DefaultShaderProperty](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme.DefaultShaderProperty) par *New*.
>
> Exemple de code : `protected new const string DefaultShaderProperty = "_Color";`
>
> En outre, les classes suivantes étendent la [`InteractableShaderTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableShaderTheme) classe qui utilise de nouveau [MaterialPropertyBlocks](https://docs.unity3d.com/ScriptReference/MaterialPropertyBlock.html) pour modifier les valeurs de propriété du nuanceur. Cette approche [améliore les performances](https://docs.unity3d.com/Manual/DrawCallBatching.html) , car les *MaterialPropertyBlocks* ne créent pas de nouveaux matériaux instanciés lorsque les valeurs changent. Toutefois, l’accès aux propriétés de classe [Material](https://docs.unity3d.com/ScriptReference/Material.html) standard ne retourne pas les valeurs attendues. Utilisez *MaterialPropertyBlocks* pour récupérer et valider les valeurs de propriété de matériau actuelles (par exemple, *_Color* ou *_MainTex*).
>
> - [`InteractableColorChildrenTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorChildrenTheme)
> - [`InteractableColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableColorTheme)
> - [`InteractableTextureTheme`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableTextureTheme)
> - [`ScaleOffsetColorTheme`](xref:Microsoft.MixedReality.Toolkit.UI.ScaleOffsetColorTheme)

[`InteractableThemeBase.Reset`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableThemeBase.Reset)

Indique au thème de rétablir les valeurs d’origine des propriétés modifiées qui ont été définies sur l’hôte GameObject lorsque ce moteur de thème a été initialisé.  

### <a name="custom-theme-engine-example"></a>Exemple de moteur de thème personnalisé

La classe ci-dessous est un exemple de nouveau moteur de thème personnalisé. Cette implémentation trouvera un composant [MeshRenderer](https://docs.unity3d.com/ScriptReference/MeshRenderer.html) sur l’objet hôte initialisé et contrôle sa visibilité en fonction de l’état actuel.

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

## <a name="end-to-end-example"></a>Exemple de bout en bout

En étendant le moteur de thème personnalisé défini dans la section précédente, l’exemple de code ci-dessous montre comment contrôler ce thème au moment de l’exécution. En particulier, comment définir l’état actuel sur le thème pour que la visibilité MeshRenderer soit mise à jour de manière appropriée.

> [!NOTE]
> `theme.OnUpdate(state,force)` doit généralement être appelé dans la méthode Update () pour prendre en charge les moteurs de thèmes qui utilisent l’accélération/lerping entre les valeurs.

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

## <a name="see-also"></a>Voir aussi

- [Avec interaction](interactable.md)
