---
title: Recommandations en matière de codage
description: Principes et conventions de codage à suivre lors de la contribution à MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, C#,
ms.openlocfilehash: c14f5f72d391c5474a01c798bfdaa5529700a509
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175334"
---
# <a name="coding-guidelines"></a>Recommandations en matière de codage

Ce document décrit les principes et conventions de codage à suivre pour contribuer à MRTK.

---

## <a name="philosophy"></a>Principe

### <a name="be-concise-and-strive-for-simplicity"></a>Soyez concis et efforcez-vous de simplifier

La solution la plus simple est souvent la meilleure. Il s’agit d’un objectif de remplacement de ces instructions et doit être l’objectif de toute activité de codage. Une partie du simple est très concise et cohérente avec le code existant. Essayez de simplifier votre code.

Les lecteurs doivent uniquement rencontrer des artefacts qui fournissent des informations utiles. Par exemple, les commentaires qui reexpliquent ce qui est évident ne fournissent pas d’informations supplémentaires et augmentent le bruit sur le rapport signal.

Simplifiez la logique du code. Notez qu’il ne s’agit pas d’une instruction sur l’utilisation d’un nombre de lignes moins élevé, ce qui réduit la taille des noms d’identificateurs ou des accolades, mais aussi la réduction du nombre de concepts et l’optimisation de la visibilité de ceux-ci par le biais de modèles familiers.

### <a name="produce-consistent-readable-code"></a>Produire du code cohérent et lisible

La lisibilité du code est corrélée avec un faible taux de défauts. Efforcez-vous de créer du code facile à lire. Efforcez-vous de créer du code avec une logique simple et de réutiliser les composants existants, car cela permet également de garantir l’exactitude.

Tous les détails du code que vous produisez, des détails les plus simples à l’exactitude du style et de la mise en forme cohérents. Assurez la cohérence de votre style de codage avec ce qui existe déjà, même s’il ne correspond pas à vos préférences. Cela augmente la lisibilité de l’ensemble du code base.

### <a name="support-configuring-components-both-in-editor-and-at-run-time"></a>Prendre en charge la configuration des composants à la fois dans l’éditeur et au moment de l’exécution

MRTK prend en charge un ensemble diversifié d’utilisateurs : les personnes qui préfèrent configurer des composants dans l’éditeur Unity et charger des prefabs, ainsi que les personnes qui doivent instancier et configurer des objets au moment de l’exécution.

Tout votre code doit fonctionner à la fois par l’ajout d’un composant à un GameObject dans une scène enregistrée et par l’instanciation de ce composant dans le code. Les tests doivent inclure un cas de test pour l’instanciation de prefabs et l’instanciation, la configuration du composant au moment de l’exécution.

### <a name="play-in-editor-is-your-first-and-primary-target-platform"></a>Play-in-Editor est votre première et plateforme cible principale

Play-in-Editor est le moyen le plus rapide d’effectuer une itération dans Unity. Fournir aux clients des moyens d’effectuer des itérations rapidement leur permet de développer des solutions plus rapidement et de tester plus d’idées. En d’autres termes, l’optimisation de la vitesse de l’itération permet à nos clients d’obtenir davantage d’informations.

Faites en sorte que tout fonctionne dans l’éditeur, puis faites-le fonctionner sur n’importe quelle autre plateforme. Conservez-le dans l’éditeur. Il est facile d’ajouter une nouvelle plateforme à la lecture dans l’éditeur. Il est très difficile d’utiliser l’éditeur de lecture dans le cas où votre application fonctionne uniquement sur un appareil.

### <a name="add-new-public-fields-properties-methods-and-serialized-private-fields-with-care"></a>Ajouter de nouveaux champs publics, propriétés, méthodes et champs privés sérialisés avec précaution

Chaque fois que vous ajoutez une méthode publique, un champ, une propriété, elle devient partie intégrante de la surface de l’API publique de MRTK. Les champs privés marqués avec `[SerializeField]` exposent également des champs à l’éditeur et font partie de la surface de l’API publique. D’autres personnes peuvent utiliser cette méthode publique, configurer des prefabs personnalisés avec votre champ public et prendre une dépendance sur celle-ci.

Les nouveaux membres publics doivent être examinés avec soin. Tout champ public devra être conservé à l’avenir. N’oubliez pas que si le type d’un champ public (ou champ privé sérialisé) est modifié ou supprimé d’un monocomportement, cela risque de perturber d’autres personnes. Le champ doit d’abord être déconseillé pour une version, et le code pour migrer les modifications pour les personnes ayant pris des dépendances doit être fourni.

### <a name="prioritize-writing-tests"></a>Classer par ordre de priorité l’écriture des tests

MRTK est un projet communautaire, modifié par un large éventail de contributeurs. Ces contributeurs peuvent ne pas connaître les détails de votre correction de bogue/fonctionnalité et rompre accidentellement votre fonctionnalité. [MRTK exécute les tests d’intégration continue](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build?definitionId=16) avant de terminer chaque requête de tirage. Les modifications qui interrompent les tests ne peuvent pas être archivées. Par conséquent, les tests constituent la meilleure façon de s’assurer que les autres personnes ne perturbent pas votre fonctionnalité.

Quand vous résolvez un bogue, écrivez un test pour vous assurer qu’il n’est pas régressé à l’avenir. Si vous ajoutez une fonctionnalité, écrivez des tests qui vérifient que votre fonctionnalité fonctionne. Cela est requis pour toutes les fonctionnalités d’expérience utilisateur, à l’exception des fonctionnalités expérimentales.

## <a name="c-coding-conventions"></a>Conventions de codage C#

### <a name="script-license-information-headers"></a>En-têtes d’informations de licence de script

Tous les employés de Microsoft qui apportent de nouveaux fichiers doivent ajouter l’en-tête de licence standard suivant en haut de tous les nouveaux fichiers, exactement comme indiqué ci-dessous :

```c#
// Copyright (c) Microsoft Corporation.
// Licensed under the MIT License.
```

### <a name="function--method-summary-headers"></a>En-têtes de résumé de fonction/méthode

Toutes les classes publiques, les structs, les enums, les fonctions, les propriétés, les champs publiés dans MRTK doivent être décrits comme à son usage et à leur utilisation, exactement comme indiqué ci-dessous :

```c#
/// <summary>
/// The Controller definition defines the Controller as defined by the SDK / Unity.
/// </summary>
public struct Controller
{
    /// <summary>
    /// The ID assigned to the Controller
    /// </summary>
    public string ID;
}
```

Cela garantit que la documentation est correctement générée et diffusée pour toutes les classes, méthodes et propriétés.

Tous les fichiers de script soumis sans balises de résumé appropriées seront rejetés.

### <a name="mrtk-namespace-rules"></a>Règles d’espace de noms MRTK

la réalité mixte Shared Computer Toolkit utilise un modèle d’espace de noms basé sur des fonctionnalités, où tous les espaces de noms fondamentaux commencent par «Microsoft. MixedReality. Shared Computer Toolkit». En général, vous n’avez pas besoin de spécifier la couche du kit de tâches (par exemple, Core, Providers, services) dans vos espaces de noms.

Les espaces de noms actuellement définis sont :

- Microsoft. MixedReality. Shared Computer Toolkit
- Microsoft. MixedReality. Shared Computer Toolkit. Bordure
- Microsoft. MixedReality. Shared Computer Toolkit. Diagnostics
- Microsoft. MixedReality. Shared Computer Toolkit. Éditeurs
- Microsoft. MixedReality. Shared Computer Toolkit. Entrée
- Microsoft. MixedReality. Shared Computer Toolkit. SpatialAwareness
- Microsoft. MixedReality. Shared Computer Toolkit. Porte
- Microsoft. MixedReality. Shared Computer Toolkit. Utilitaires

Pour les espaces de noms avec une grande quantité de types, il est acceptable de créer un nombre limité de sous-espaces de noms pour faciliter l’utilisation de l’étendue.

L’omission de l’espace de noms pour une interface, une classe ou un type de données entraîne le blocage de votre modification.

### <a name="adding-new-monobehaviour-scripts"></a>Ajout de nouveaux scripts monocomportement

Lorsque vous ajoutez de nouveaux scripts monocomportement avec une requête de tirage, assurez-vous que l' [`AddComponentMenu`](https://docs.unity3d.com/ScriptReference/AddComponentMenu.html) attribut est appliqué à tous les fichiers applicables. Cela permet de s’assurer que le composant est facilement détectable dans l’éditeur, sous le bouton *Ajouter un composant* . L’indicateur d’attribut n’est pas nécessaire si le composant ne peut pas s’afficher dans un éditeur tel qu’une classe abstraite.

Dans l’exemple ci-dessous, le *package* doit être rempli avec l’emplacement du package du composant. Si vous placez un élément dans le dossier *MRTK/SDK* , le package sera le *Kit de développement logiciel (SDK)*.

```c#
[AddComponentMenu("Scripts/MRTK/{Package here}/MyNewComponent")]
public class MyNewComponent : MonoBehaviour
```

### <a name="adding-new-unity-inspector-scripts"></a>Ajout de nouveaux scripts d’inspecteur Unity

En général, essayez d’éviter de créer des scripts d’inspecteur personnalisés pour les composants MRTK. Il ajoute une surcharge et une gestion supplémentaires du code base qui peuvent être gérées par le moteur Unity.

Si une classe Inspector est nécessaire, essayez d’utiliser Unity [`DrawDefaultInspector()`](https://docs.unity3d.com/ScriptReference/Editor.DrawDefaultInspector.html) . Cela simplifie la classe Inspector et laisse une grande partie du travail à Unity.

```c#
public override void OnInspectorGUI()
{
    // Do some custom calculations or checks
    // ....
    DrawDefaultInspector();
}
```

Si le rendu personnalisé est requis dans la classe Inspector, essayez d’utiliser [`SerializedProperty`](https://docs.unity3d.com/ScriptReference/SerializedProperty.html) et [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) . Ainsi, Unity gère correctement le rendu des prefabs imbriqués et des valeurs modifiées.

Si [`EditorGUILayout.PropertyField`](https://docs.unity3d.com/ScriptReference/EditorGUILayout.PropertyField.html) ne peut pas être utilisé en raison d’une spécification dans une logique personnalisée, assurez-vous que toute utilisation est encapsulée autour d’un [`EditorGUI.PropertyScope`](https://docs.unity3d.com/ScriptReference/EditorGUI.PropertyScope.html) . Cela permet de garantir que Unity rend correctement l’inspecteur pour les prefabs imbriquées et les valeurs modifiées avec la propriété donnée.

En outre, essayez de décorer la classe Inspector personnalisée avec un [`CanEditMultipleObjects`](https://docs.unity3d.com/ScriptReference/CanEditMultipleObjects.html) . Cette balise permet de s’assurer que plusieurs objets avec ce composant dans la scène peuvent être sélectionnés et modifiés ensemble. Toutes les nouvelles classes Inspector doivent vérifier que leur code fonctionne dans cette situation dans la scène.

```c#
    // Example inspector class demonstrating usage of SerializedProperty & EditorGUILayout.PropertyField
    // as well as use of EditorGUI.PropertyScope for custom property logic
    [CustomEditor(typeof(MyComponent))]
    public class MyComponentInspector : UnityEditor.Editor
    {
        private SerializedProperty myProperty;
        private SerializedProperty handedness;

        protected virtual void OnEnable()
        {
            myProperty = serializedObject.FindProperty("myProperty");
            handedness = serializedObject.FindProperty("handedness");
        }

        public override void OnInspectorGUI()
        {
            EditorGUILayout.PropertyField(destroyOnSourceLost);

            Rect position = EditorGUILayout.GetControlRect();
            var label = new GUIContent(handedness.displayName);
            using (new EditorGUI.PropertyScope(position, label, handedness))
            {
                var currentHandedness = (Handedness)handedness.enumValueIndex;

                handedness.enumValueIndex = (int)(Handedness)EditorGUI.EnumPopup(
                    position,
                    label,
                    currentHandedness,
                    (value) => {
                        // This function is executed by Unity to determine if a possible enum value
                        // is valid for selection in the editor view
                        // In this case, only Handedness.Left and Handedness.Right can be selected
                        return (Handedness)value == Handedness.Left
                        || (Handedness)value == Handedness.Right;
                    });
            }
        }
    }
```

### <a name="adding-new-scriptableobjects"></a>Ajout de New ScriptableObjects

Lorsque vous ajoutez de nouveaux scripts ScriptableObject, vérifiez que l' [`CreateAssetMenu`](https://docs.unity3d.com/ScriptReference/CreateAssetMenu.html) attribut est appliqué à tous les fichiers applicables. Cela permet de s’assurer que le composant est facilement détectable dans l’éditeur par le biais des menus de création de composants. L’indicateur d’attribut n’est pas nécessaire si le composant ne peut pas s’afficher dans un éditeur tel qu’une classe abstraite.

Dans l’exemple ci-dessous, le *sous-dossier* doit être rempli avec le sous-dossier MRTK, le cas échéant. Si vous placez un élément dans le dossier *MRTK/Providers* , le package sera *fournisseurs*. Si vous placez un élément dans le dossier *MRTK/Core* , affectez-lui la valeur « profiles ».

Dans l’exemple ci-dessous, *MyNewService | MyNewProvider* doit être rempli avec le nom de votre nouvelle classe, le cas échéant. Si vous placez un élément dans le dossier *MixedRealityToolkit* , laissez cette chaîne vide.

```c#
[CreateAssetMenu(fileName = "MyNewProfile", menuName = "Mixed Reality Toolkit/{Subfolder}/{MyNewService | MyNewProvider}/MyNewProfile")]
public class MyNewProfile : ScriptableObject
```

### <a name="logging"></a>Journalisation

Lorsque vous ajoutez de nouvelles fonctionnalités ou mettez à jour des fonctionnalités existantes, envisagez d’ajouter des journaux DebugUtilities. LogVerbose à du code intéressant qui peut s’avérer utile pour un débogage ultérieur. Il y a un compromis entre l’ajout de la journalisation et le bruit ajouté et la journalisation insuffisante (ce qui rend le diagnostic difficile).

Un exemple intéressant où la journalisation est utile (avec une charge utile intéressante) :

```c#
DebugUtilities.LogVerboseFormat("RaiseSourceDetected: Source ID: {0}, Source Type: {1}", source.SourceId, source.SourceType);
```

Ce type de journalisation peut vous aider à détecter des problèmes tels que des erreurs [https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8016) de source incompatible détectées et des événements de perte de source.

Évitez d’ajouter des journaux pour les données et les événements qui se produisent dans tous les cas où la journalisation idéale devrait couvrir des événements « intéressants » pilotés par des entrées d’utilisateur distinctes (c’est-à-dire un « clic » par un utilisateur et l’ensemble de modifications et d’événements provenant de qui sont intéressants pour le journal). L’État en cours « l’utilisateur maintient toujours un geste » enregistré dans chaque cadre n’est pas intéressant et surcharge les journaux.

Notez que cette journalisation documentée n’est pas activée par défaut (elle doit être activée dans les [paramètres du système de diagnostic](../features/diagnostics/configuring-diagnostics.md#enable-verbose-logging)).

### <a name="spaces-vs-tabs"></a>Espaces et tabulations

Veillez à utiliser 4 espaces à la place des onglets lors de la contribution à ce projet.

### <a name="spacing"></a>Espacement

N’ajoutez pas d’espaces supplémentaires entre les crochets et les parenthèses :

#### <a name="dont"></a>À ne pas faire

```c#
private Foo()
{
    int[ ] var = new int [ 9 ];
    Vector2 vector = new Vector2 ( 0f, 10f );
}

```

#### <a name="do"></a>À faire

```c#
private Foo()
{
    int[] var = new int[9];
    Vector2 vector = new Vector2(0f, 10f);
}
```

### <a name="naming-conventions"></a>Conventions d’affectation de noms

Utilisez toujours `PascalCase` pour les propriétés. Utilisez `camelCase` pour la plupart des champs, à l’exception `PascalCase` des `static readonly` `const` champs et. La seule exception concerne les structures de données qui requièrent que les champs soient sérialisés par le `JsonUtility` .

#### <a name="dont"></a>À ne pas faire

```c#
public string myProperty; // <- Starts with a lowercase letter
private string MyField; // <- Starts with an uppercase letter
```

#### <a name="do"></a>À faire

```c#
public string MyProperty;
protected string MyProperty;
private static readonly string MyField;
private string myField;
```

### <a name="access-modifiers"></a>Modificateurs d’accès

Déclarez toujours un modificateur d’accès pour tous les champs, propriétés et méthodes.

- Toutes les méthodes de l’API Unity doivent être `private` par défaut, sauf si vous devez les substituer dans une classe dérivée. Dans ce cas, `protected` doit être utilisé.

- Les champs doivent toujours être `private` , avec des `public` `protected` accesseurs de propriété ou.

- Utiliser des [membres expression-astiers](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#expression-bodied-function-members) et des [propriétés auto](https://github.com/dotnet/roslyn/wiki/New-Language-Features-in-C%23-6#auto-property-enhancements) lorsque cela est possible

#### <a name="dont"></a>À ne pas faire

```c#
// protected field should be private
protected int myVariable = 0;

// property should have protected setter
public int MyVariable => myVariable;

// No public / private access modifiers
void Foo() { }
void Bar() { }
```

#### <a name="do"></a>À faire

```c#
public int MyVariable { get; protected set; } = 0;

private void Foo() { }
public void Bar() { }
protected virtual void FooBar() { }
```

### <a name="use-braces"></a>Utiliser des accolades

Utilisez toujours les accolades après chaque bloc d’instructions et placez-les sur la ligne suivante.

#### <a name="dont"></a>Pratiques déconseillées

```c#
private Foo()
{
    if (Bar==null) // <- missing braces surrounding if action
        DoThing();
    else
        DoTheOtherThing();
}
```

#### <a name="dont"></a>À ne pas faire

```c#
private Foo() { // <- Open bracket on same line
    if (Bar==null) DoThing(); <- if action on same line with no surrounding brackets
    else DoTheOtherThing();
}
```

#### <a name="do"></a>À faire

```c#
private Foo()
{
    if (Bar==true)
    {
        DoThing();
    }
    else
    {
        DoTheOtherThing();
    }
}
```

### <a name="public-classes-structs-and-enums-should-all-go-in-their-own-files"></a>Les classes, structs et enums publics doivent tous se trouver dans leurs propres fichiers

Si la classe, le struct ou l’enum peut être rendu privé, il est possible de l’inclure dans le même fichier.  Cela évite les problèmes de compilation avec Unity et s’assure que l’abstraction du code appropriée se produit, elle réduit également les conflits et les modifications avec rupture lorsque le code doit changer.

#### <a name="dont"></a>À ne pas faire

```c#
public class MyClass
{
    public struct MyStruct() { }
    public enum MyEnumType() { }
    public class MyNestedClass() { }
}
```

#### <a name="do"></a>À faire

```c#
 // Private references for use inside the class only
public class MyClass
{
    private struct MyStruct() { }
    private enum MyEnumType() { }
    private class MyNestedClass() { }
}
```

#### <a name="do"></a>Pratiques conseillées

MyStruct. cs

```c#
// Public Struct / Enum definitions for use in your class.  Try to make them generic for reuse.
public struct MyStruct
{
    public string Var1;
    public string Var2;
}
```

MyEnumType. cs

```c#
public enum MuEnumType
{
    Value1,
    Value2 // <- note, no "," on last value to denote end of list.
}
```

MyClass. cs

```c#
public class MyClass
{
    private MyStruct myStructReference;
    private MyEnumType myEnumReference;
}
```

### <a name="initialize-enums"></a>Initialiser les énumérations

Pour vous assurer que tous les enums sont correctement initialisés à partir de 0, .NET vous donne un raccourci tidy pour initialiser automatiquement l’énumération en ajoutant simplement la première valeur (Starter). (par exemple, valeur 1 = 0 les valeurs restantes ne sont pas requises)

#### <a name="dont"></a>À ne pas faire

```c#
public enum Value
{
    Value1, <- no initializer
    Value2,
    Value3
}
```

#### <a name="do"></a>À faire

```c#
public enum ValueType
{
    Value1 = 0,
    Value2,
    Value3
}
```

### <a name="order-enums-for-appropriate-extension"></a>Commandes enums pour l’extension appropriée

Si une énumération est susceptible d’être étendue à l’avenir, il est essentiel de classer les valeurs par défaut en haut de l’énumération, ce qui garantit que les index enum ne sont pas affectés par de nouveaux ajouts.

#### <a name="dont"></a>À ne pas faire

```c#
public enum SDKType
{
    WindowsMR,
    OpenVR,
    OpenXR,
    None, <- default value not at start
    Other <- anonymous value left to end of enum
}
```

#### <a name="do"></a>À faire

```c#
/// <summary>
/// The SDKType lists the VR SDKs that are supported by the MRTK
/// Initially, this lists proposed SDKs, not all may be implemented at this time (please see ReleaseNotes for more details)
/// </summary>
public enum SDKType
{
    /// <summary>
    /// No specified type or Standalone / non-VR type
    /// </summary>
    None = 0,
    /// <summary>
    /// Undefined SDK.
    /// </summary>
    Other,
    /// <summary>
    /// The Windows 10 Mixed reality SDK provided by the Universal Windows Platform (UWP), for Immersive MR headsets and HoloLens.
    /// </summary>
    WindowsMR,
    /// <summary>
    /// The OpenVR platform provided by Unity (does not support the downloadable SteamVR SDK).
    /// </summary>
    OpenVR,
    /// <summary>
    /// The OpenXR platform. SDK to be determined once released.
    /// </summary>
    OpenXR
}
```

### <a name="review-enum-use-for-bitfields"></a>Examiner l’utilisation des énumérations pour les champs binaires

S’il existe une possibilité pour une énumération d’exiger plusieurs États comme valeur, par exemple, droitier = gauche & droite. Ensuite, l’énumération doit être décorée correctement avec indicateurs pour permettre son utilisation correcte

Le fichier droitier. cs a une implémentation concrète pour cela

### <a name="dont"></a>À ne pas faire

```c#
public enum Handedness
{
    None,
    Left,
    Right
}
```

### <a name="do"></a>À faire

```c#
[Flags]
public enum Handedness
{
    None = 0 << 0,
    Left = 1 << 0,
    Right = 1 << 1,
    Both = Left | Right
}
```

### <a name="hard-coded-file-paths"></a>Chemins d’accès aux fichiers codés en dur

Lors de la génération de chemins d’accès de fichier de chaîne, et en particulier l’écriture de chemins d’accès de chaîne codés en dur, procédez comme suit :

1. Utilisez des [ `Path` API](/dotnet/api/system.io.path?preserve-view=true&view=netframework-4.8) C# dans la mesure du possible, telles que `Path.Combine` ou `Path.GetFullPath` .
1. Utilisez/ou à la [`Path.DirectorySeparatorChar`](/dotnet/api/system.io.path.directoryseparatorchar?preserve-view=true&view=netframework-4.8) place de \ ou \\ \\ .

ces étapes permettent de s’assurer que MRTK fonctionne sur les systèmes Windows et Unix.

### <a name="dont"></a>À ne pas faire

```c#
private const string FilePath = "MyPath\\to\\a\\file.txt";
private const string OtherFilePath = "MyPath\to\a\file.txt";

string filePath = myVarRootPath + myRelativePath;
```

### <a name="do"></a>À faire

```c#
private const string FilePath = "MyPath/to/a/file.txt";
private const string OtherFilePath = "folder{Path.DirectorySeparatorChar}file.txt";

string filePath = Path.Combine(myVarRootPath,myRelativePath);

// Path.GetFullPath() will return the full length path of provided with correct system directory separators
string cleanedFilePath = Path.GetFullPath(unknownSourceFilePath);
```

## <a name="best-practices-including-unity-recommendations"></a>Meilleures pratiques, y compris les recommandations Unity

Certaines des plates-formes cibles de ce projet nécessitent de prendre en compte les performances. En tenant compte de cela, soyez toujours prudent quand vous allouez de la mémoire dans du code fréquemment appelé dans des boucles ou des algorithmes de mise à jour serrés.

### <a name="encapsulation"></a>Encapsulation

Utilisez toujours les champs privés et les propriétés publiques si l’accès au champ est nécessaire à partir de l’extérieur de la classe ou du struct.  Veillez à colocaliser le champ privé et la propriété publique. Cela permet de mieux voir, d’un seul coup d’œil, ce qui stocke la propriété et que le champ est modifiable par le script.

> [!NOTE]
> La seule exception concerne les structures de données qui requièrent que les champs soient sérialisés par le `JsonUtility` , où une classe de données doit avoir tous les champs publics pour que la sérialisation fonctionne.

#### <a name="dont"></a>À ne pas faire

```c#
private float myValue1;
private float myValue2;

public float MyValue1
{
    get{ return myValue1; }
    set{ myValue1 = value }
}

public float MyValue2
{
    get{ return myValue2; }
    set{ myValue2 = value }
}
```

#### <a name="do"></a>À faire

```c#
// Enable field to be configurable in the editor and available externally to other scripts (field is correctly serialized in Unity)
[SerializeField]
[ToolTip("If using a tooltip, the text should match the public property's summary documentation, if appropriate.")]
private float myValue; // <- Notice we co-located the backing field above our corresponding property.

/// <summary>
/// If using a tooltip, the text should match the public property's summary documentation, if appropriate.
/// </summary>
public float MyValue
{
    get => myValue;
    set => myValue = value;
}

/// <summary>
/// Getter/Setters not wrapping a value directly should contain documentation comments just as public functions would
/// </summary>
public float AbsMyValue
{
    get
    {
        if (MyValue < 0)
        {
            return -MyValue;
        }

        return MyValue
    }
}
```

### <a name="cache-values-and-serialize-them-in-the-sceneprefab-whenever-possible"></a>Mettre en cache les valeurs et les sérialiser dans Scene/Prefab chaque fois que cela est possible

avec la HoloLens à l’esprit, il est préférable d’optimiser les performances et les références de cache dans la scène ou prefab pour limiter les allocations de mémoire du runtime.

#### <a name="dont"></a>À ne pas faire

```c#
void Update()
{
    gameObject.GetComponent<Renderer>().Foo(Bar);
}
```

#### <a name="do"></a>À faire

```c#
[SerializeField] // To enable setting the reference in the inspector.
private Renderer myRenderer;

private void Awake()
{
    // If you didn't set it in the inspector, then we cache it on awake.
    if (myRenderer == null)
    {
        myRenderer = gameObject.GetComponent<Renderer>();
    }
}

private void Update()
{
    myRenderer.Foo(Bar);
}
```

### <a name="cache-references-to-materials-do-not-call-the-material-each-time"></a>Mettre en cache des références à des matériaux, n’appelez pas « . Material » à chaque fois

Unity crée un nouveau matériau chaque fois que vous utilisez « . Material », ce qui entraîne une fuite de mémoire si elle n’est pas nettoyée correctement.

#### <a name="dont"></a>À ne pas faire

```c#
public class MyClass
{
    void Update()
    {
        Material myMaterial = GetComponent<Renderer>().material;
        myMaterial.SetColor("_Color", Color.White);
    }
}
```

#### <a name="do"></a>À faire

```c#
// Private references for use inside the class only
public class MyClass
{
    private Material cachedMaterial;

    private void Awake()
    {
        cachedMaterial = GetComponent<Renderer>().material;
    }

    void Update()
    {
        cachedMaterial.SetColor("_Color", Color.White);
    }

    private void OnDestroy()
    {
        Destroy(cachedMaterial);
    }
}
```

> [!NOTE]
> Vous pouvez également utiliser la propriété « SharedMaterial » d’Unity qui ne crée pas de nouveau matériau chaque fois qu’elle est référencée.

### <a name="use-platform-dependent-compilation-to-ensure-the-toolkit-wont-break-the-build-on-another-platform"></a>utilisez la [compilation dépendante](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) de la plateforme pour vous assurer que la Shared Computer Toolkit n’interrompt pas la génération sur une autre plateforme

- Utilisez afin `WINDOWS_UWP` d’utiliser des API non Unity spécifiques à UWP. Cela les empêchera d’essayer de s’exécuter dans l’éditeur ou sur des plateformes non prises en charge. Cela équivaut à `UNITY_WSA && !UNITY_EDITOR` et doit être utilisé en faveur de.
- Utilisez `UNITY_WSA` pour utiliser des API Unity spécifiques à UWP, telles que l' `UnityEngine.XR.WSA` espace de noms. Cette opération s’exécute dans l’éditeur lorsque la plateforme est définie sur UWP, ainsi que dans les applications UWP générées.

Ce graphique peut vous aider à décider de ce qui `#if` doit être utilisé, en fonction de vos cas d’usage et des paramètres de génération attendus.

|Plateforme | IL2CPP UWP | .NET UWP | Éditeur |
| --- | --- | --- | --- |
| `UNITY_EDITOR` | Faux | False | True |
| `UNITY_WSA` | True | True | True |
| `WINDOWS_UWP` | True | True | False |
| `UNITY_WSA && !UNITY_EDITOR` | True | True | False |
| `ENABLE_WINMD_SUPPORT` | True | True | Faux |
| `NETFX_CORE` | False | True | Faux |

### <a name="prefer-datetimeutcnow-over-datetimenow"></a>Préférez DateTime. UtcNow à DateTime. Now

DateTime. UtcNow est plus rapide que DateTime. Now. Dans les enquêtes de performances précédentes, nous avons découvert que l’utilisation de DateTime. ajoute désormais une surcharge significative en particulier lorsqu’elle est utilisée dans la boucle Update (). [D’autres ont rencontré le même problème](https://stackoverflow.com/questions/1561791/optimizing-alternatives-to-datetime-now).

Préférez l’utilisation de DateTime. UtcNow, sauf si vous avez réellement besoin des heures localisées (il est possible que vous souhaitiez afficher l’heure actuelle dans le fuseau horaire de l’utilisateur). Si vous traitez des temps relatifs (par exemple, le delta entre une dernière mise à jour et maintenant), il est préférable d’utiliser DateTime. UtcNow pour éviter la surcharge liée à la réalisation de conversions de fuseau horaire.

## <a name="powershell-coding-conventions"></a>Conventions de codage PowerShell

Un sous-ensemble du code base MRTK utilise PowerShell pour l’infrastructure de pipeline et divers scripts et utilitaires. Le nouveau code PowerShell doit suivre le [style PoshCode](https://poshcode.gitbooks.io/powershell-practice-and-style/).

## <a name="see-also"></a>Voir aussi

 [Conventions de codage C# de MSDN](/dotnet/csharp/programming-guide/inside-a-program/coding-conventions)
