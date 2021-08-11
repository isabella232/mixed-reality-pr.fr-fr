---
title: Avec interaction
description: Vue d’ensemble du composant script d’interaction dans MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, événements interactifs, événements,
ms.openlocfilehash: a0aee99d01ae59a8ebedc4d62a4b0aaf844a7afaa6961bbfd05238dd9d5b673d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115206773"
---
# <a name="interactable"></a>Avec interaction

![Avec interaction](../images/interactable/InteractableExamples.png)

Le [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) composant est un conteneur tout-en-un pour rendre un objet facilement  accessible et réactif aux entrées. Les actions interactifs agissent comme un tout pour tous les types d’entrée, y compris le toucher, les rayons de main, la parole, etc., et entonnoirnt ces interactions dans des [événements](#events) et des réponses de [thème visuel](visual-themes.md) . Ce composant offre un moyen simple de créer des boutons, de modifier la couleur des objets avec le focus et bien plus encore.

## <a name="how-to-configure-interactable"></a>Comment configurer l’interaction

Le composant permet trois principales sections de configuration :

1) [Configuration d’entrée générale](#general-input-settings)
1) [Thèmes visuels](visual-themes.md) ciblés sur plusieurs GameObjects
1) [Gestionnaires d’événements](#events)

### <a name="general-input-settings"></a>Paramètres d’entrée généraux

![Paramètres interactifs générales](../images/interactable/InputFeatures_short.png)

**États**

*States* est un paramètre [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) qui définit les phases d’interaction, comme l’appui ou l’observation, pour les profils et les [thèmes visuels](visual-themes.md)pouvant être [interagis](#interactable-profiles) .

**DefaultInteractableStates** (Assets/MRTK/SDK/features/UX/interactive/States/DefaultInteractableStates. Asset) est fourni avec MRTK out-of-Box et est le paramètre *par défaut pour les* composants interactifs.

![Exemple ScriptableObject States dans Inspector](../images/interactable/DefaultInteractableStates.png)

La ressource *DefaultInteractableStates* contient quatre États et utilise l' [`InteractableStates`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStates) implémentation du modèle d’État.

* **Valeur par défaut**: rien ne se passe, il s’agit de l’état de base le plus isolé.

* **Focus**: l’objet est pointé. Il s’agit d’un État unique, aucun autre État n’est actuellement défini, mais il n’a pas de classement par défaut.

* **Appuyez sur**: l’objet est pointé et un bouton ou une main est enfoncé. La valeur par défaut et le focus de l’état de la presse. Cet État est également défini en tant que secours pour une pression physique.

* **Désactivé**: le bouton ne doit pas être interactif et un retour visuel permettra à l’utilisateur de savoir si ce bouton n’est pas utilisable pour l’instant. En théorie, l’état désactivé peut contenir tous les autres États, mais lorsque l’option est activée est désactivée, l’état désactivé prend tous les autres États.

Une valeur de bit (#) est assignée à l’État en fonction de l’ordre dans la liste.

> [!NOTE]
> Il est généralement recommandé d’utiliser **DefaultInteractableStates** (Assets/MRTK/SDK/features/UX/interactive/States/DefaultInteractableStates. Asset) lors de *la création de* composants interactifs.
>
> Toutefois, il existe 17 États interactifs qui peuvent être utilisés pour piloter des thèmes, bien que certains soient destinés à être pilotés par d’autres composants. Voici une liste de ceux qui ont des fonctionnalités intégrées.
>
> * Visité : l’utilisateur a cliqué sur l’interagissant.
> * Activé/désactivé : le bouton est dans un État bascule ou l’index de dimension est un nombre impair.
> * Mouvement : la main ou le contrôleur a été enfoncé et a été déplacé de la position d’origine.
> * VoiceCommand : une commande vocale a été utilisée pour déclencher l’interaction.
> * PhysicalTouch : une entrée tactile est actuellement détectée [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) . Utilisez pour activer.
> * Manipulation : une main est actuellement saisie dans les limites de l’objet, utilisez [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) pour activer

**Activé**

Active ou désactive l’activation d’une opération d’interaction. Cela correspond au [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) dans le code.

Une propriété activée pour une *interaction* est différente de la propriété activée configurée via gameobject/Component (c.-à-d. Setactal, etc.). La désactivation du monocomportement GameObject ou *interactive* désactive l’exécution de tout élément de la classe, y compris l’entrée, les thèmes visuels, les événements, etc. La désactivation via [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) désactive la plupart des informations de gestion des entrées, en réinitialisant les États d’entrée associés. Toutefois, la classe exécute toujours chaque frame et reçoit les événements d’entrée qui seront ignorés. Cela est utile pour afficher l’état d’interaction dans un état désactivé qui peut être effectué par le biais de thèmes visuels. Un bouton Envoyer est un exemple typique qui est l’attente de l’exécution de tous les champs d’entrée requis.

**Actions d’entrée**

Sélectionnez l' [action d’entrée](../input/input-actions.md) à partir de la configuration d’entrée ou du profil de mappage de contrôleur auquel *le composant pouvant* être utilisé doit réagir.

Cette propriété peut être configurée au moment de l’exécution dans le code via [`Interactable.InputAction`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.InputAction) .

**IsGlobal**

Si la valeur est true, le composant est marqué comme écouteur d’entrée global pour l' [action d’entrée](../input/input-actions.md)sélectionnée. Le comportement par défaut est false, ce qui limite l’entrée à ce conflit/GameObject pouvant être *interagi* .

Cette propriété peut être configurée au moment de l’exécution dans le code via [`Interactable.IsGlobal`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsGlobal) .

**Commande vocale**

[Commande vocale](../input/speech.md), à partir du profil de commandes vocales MRTK, pour déclencher un événement OnClick pour une interaction vocale.

Cette propriété peut être configurée au moment de l’exécution dans le code via [`Interactable.VoiceCommand`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceCommand) .

**Nécessite le focus**

Si la valeur est true, la commande vocale activera uniquement l’opération *interactive* si et uniquement si elle a déjà le focus à partir d’un pointeur. Si la valeur est false, l’opération *interactive* agit comme un écouteur global pour la commande vocale sélectionnée. Le comportement par défaut est true, car plusieurs écouteurs de reconnaissance vocale globaux peuvent être difficiles à organiser dans une scène.

Cette propriété peut être configurée au moment de l’exécution dans le code via [`Interactable.VoiceRequiresFocus`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceRequiresFocus) .

**Mode de sélection**

Cette propriété définit la logique de sélection. Lorsqu’un utilisateur clique *sur un utilisateur* , il itère au niveau de la *dimension* suivante. Les *dimensions* sont similaires au rang et définissent un État en dehors des entrées (c.-à-d. le focus, appuyez sur etc.). Ils sont utiles pour définir des États de basculement ou d’autres États à plusieurs rangs associés à un bouton. Le niveau de dimension actuel est suivi par `Interactable.DimensionIndex` .

Les modes de sélection disponibles sont les suivants :

* **Bouton**  -  *Dimensions* = 1, interactif simple  et interactifs
* **Activer/désactiver**  -  *Dimensions* = *2,* alternatives  / *interactives* entre l’état inactif
* **Plusieurs dimensions**  -  *Dimensions* >= 3, chaque clic augmente le niveau de dimension actuel + 1. Utile pour définir un état de bouton sur une liste, etc.

L' *interaction* peut également permettre la définition de plusieurs thèmes par *dimension*. Par exemple, quand *SelectionMode = Toggle*, un thème peut être appliqué lorsque l’opération d' *interaction* est *désélectionnée* et qu’un autre thème est appliqué lorsque le composant est *sélectionné*.

Le mode de sélection actuel peut être interrogé au moment de l’exécution via [`Interactable.ButtonMode`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.ButtonMode) . La mise à jour du mode au moment de l’exécution peut être obtenue en définissant la  [`Interactable.Dimensions`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.Dimensions) propriété pour qu’elle corresponde à la fonctionnalité souhaitée. En outre, la dimension actuelle, utile pour les modes de *basculement* et de *plusieurs dimensions* , est accessible via [`Interactable.CurrentDimension`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.CurrentDimension) .

### <a name="interactable-profiles"></a>Profils interactifs

Les *profils* sont des éléments qui créent une relation entre un gameobject et un [thème visuel](visual-themes.md). Le profil définit le contenu qui sera manipulé par un thème lorsqu’un [changement d’État se produit](#general-input-settings).

Les thèmes fonctionnent beaucoup comme des documents. Il s’agit d’objets scriptables qui contiennent une liste de propriétés qui seront affectées à un objet en fonction de l’état actuel. Les thèmes sont également réutilisables et peuvent être attribués *sur plusieurs objets* UX interactifs.

**Réinitialisation lors de la destruction**

Les thèmes visuels modifient différentes propriétés sur un GameObject ciblé, selon la classe et le type de moteur de thème sélectionnés. Si l’opération *de réinitialisation sur Destroy* a la valeur true lorsque le composant interactif est détruit, le composant rétablit les valeurs d’origine de toutes les propriétés modifiées des thèmes actifs. Dans le cas contraire, lorsqu’il est détruit, le composant qui peut être interagi laisse toutes les propriétés modifiées en l’État. Dans ce dernier cas, le dernier état des valeurs est conservé, sauf s’il est modifié par un autre composant externe. La valeur par défaut est false.

<img src="../images/interactable/Profiles_Themes.png" width="450" alt="Profile theams">

## <a name="events"></a>Événements

Chaque composant pouvant être utilisé est associé à un événement *OnClick* qui se déclenche lorsque *le composant est* simplement sélectionné. Toutefois, il peut être utilisé pour *détecter des événements* d’entrée autres que *OnClick*.

Cliquez sur le bouton *Ajouter un événement* pour ajouter un nouveau type de définition de récepteur d’événements. Une fois ajouté, sélectionnez le type d’événement souhaité.

![Exemple d’événements](../images/interactable/Events.png))

Il existe différents types de récepteurs d’événements pour répondre à différents types d’entrée. MRTK est fourni avec l’ensemble de récepteurs suivant, prêt à l’emploi.

* [`InteractableAudioReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAudioReceiver)
* [`InteractableOnClickReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnClickReceiver)
* [`InteractableOnFocusReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)
* [`InteractableOnGrabReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnGrabReceiver)
* [`InteractableOnHoldReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnHoldReceiver)
* [`InteractableOnPressReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnPressReceiver)
* [`InteractableOnToggleReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnToggleReceiver)
* [`InteractableOnTouchReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnTouchReceiver)

Un récepteur personnalisé peut être créé en créant une nouvelle classe qui étend [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) .

![Exemple de récepteur de basculement d’événement](../images/interactable/Event_toggle.png)

*Exemple de récepteur d’événements Toggle*

### <a name="interactable-receivers"></a>Récepteurs interactifs

 Le [`InteractableReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiver) composant permet de définir des événements en dehors du composant d' *interaction* source. Le *InteractableReceiver* écoute un type d’événement filtré déclenché par un autre qui peut être *interagi*. Si la propriété *interactive* n’est pas affectée directement, la propriété de la *zone de recherche* définit la direction que le *InteractableReceiver* écoute pour les événements qui se trouvent sur lui-même, dans un parent ou dans un gameobject enfant.

[`InteractableReceiverList`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiverList) agit de manière similaire, mais pour une liste d’événements correspondants.

<img src="../images/interactable/InteractableReceiver.png" width="450" alt="Interactable reciver">

### <a name="create-custom-events"></a>Créer des événements personnalisés

Comme les [thèmes visuels](visual-themes.md#custom-theme-engines), les événements peuvent être étendus pour détecter tout modèle d’État ou pour exposer des fonctionnalités.

Les événements personnalisés peuvent être créés de deux manières principales :

1) Étendez la [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) classe pour créer un événement personnalisé qui s’affichera dans la liste déroulante des types d’événements. Un événement Unity est fourni par défaut, mais des événements Unity supplémentaires peuvent être ajoutés ou l’événement peut être défini de façon à masquer les événements Unity. Cette fonctionnalité permet à un concepteur de travailler avec un ingénieur sur un projet pour créer un événement personnalisé que le concepteur peut configurer dans l’éditeur.

1) Étendez la [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) classe pour créer un composant d’événement entièrement personnalisé qui peut résider  sur le ou un autre objet pouvant être utilisé. Fait [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) référence à l’opération *interactive* pour détecter les modifications d’État.

#### <a name="example-of-extending-receiverbase"></a>Exemple d’extension `ReceiverBase`

La [`CustomInteractablesReceiver`](xref:Microsoft.MixedReality.Toolkit.UI) classe affiche des informations d’état  sur un intercepteur et est un exemple de création d’un récepteur d’événements personnalisé.

```c#
public CustomInteractablesReceiver(UnityEvent ev) : base(ev, "CustomEvent")
{
    HideUnityEvents = true; // hides Unity events in the receiver - meant to be code only
}
```

Les méthodes suivantes sont utiles pour remplacer/implémenter lors de la création d’un récepteur d’événements personnalisé. [`ReceiverBase.OnUpdate()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) est une méthode abstraite qui peut être utilisée pour détecter des modèles d’état/des transitions. En outre, [`ReceiverBase.OnVoiceCommand()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) les [`ReceiverBase.OnClick()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) méthodes et sont utiles pour la création d’une logique d’événement personnalisée lorsque l’option *interactive* est sélectionnée.

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

##### <a name="displaying-custom-event-receiver-fields-in-the-inspector"></a>Affichage des champs de récepteur d’événements personnalisés dans l’inspecteur

Les scripts *ReceiverBase* utilisent [`InspectorField`](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.InspectorField) des attributs pour exposer des propriétés personnalisées dans l’inspecteur. Voici un exemple de Vector3, une propriété personnalisée avec des informations d’info-bulle et d’étiquette. Cette propriété s’affiche comme configurable dans l’inspecteur lorsqu' *un GameObjectable* est sélectionné et que le type de récepteur d' *événements* associé est ajouté.

```c#
[InspectorField(Label = "<Property label>",Tooltip = "<Insert tooltip info>",Type = InspectorField.FieldTypes.Vector3)]
public Vector3 EffectOffset = Vector3.zero;
```

## <a name="how-to-use-interactable"></a>Comment utiliser les méthodes d’interaction

### <a name="building-a-simple-button"></a>Création d’un bouton simple

Vous pouvez créer un bouton simple en ajoutant le composant *interagissant* à un gameobject qui est configuré pour recevoir des événements d’entrée. Il peut y avoir un conflit ou un enfant pour recevoir l’entrée. Si vous utilisez *interactive* avec un GameObjects basé sur une interface utilisateur Unity, il doit se trouver sous le canevas GameObject.

Suivez le bouton une étape plus loin, en créant un nouveau profil, en affectant le GameObject et en créant un nouveau thème. En outre, utilisez l’événement *OnClick* pour faire en sorte qu’un événement se produise.

> [!NOTE]
> Le fait d' [appuyer sur un bouton](button.md) requiert le [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) composant. En outre, le [`PhysicalPressEventRouter`](xref:Microsoft.MixedReality.Toolkit.PhysicalPressEventRouter) composant est nécessaire pour entonnoirr les événements d’appui sur le composant en *interaction* .

### <a name="creating-toggle-and-multi-dimension-buttons"></a>Création de boutons bascule et à plusieurs dimensions

#### <a name="toggle-button"></a>Bouton bascule

Pour rendre un bouton activé, modifiez le [`Selection Mode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) champ en type `Toggle` . Dans la section *profils* , un nouveau thème basculé est ajouté pour chaque profil utilisé lorsque l' *interaction* est activée.

Tandis que [`SelectionMode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) est défini pour basculer, la case à cocher *IsToggled* peut être utilisée pour définir la valeur par défaut du contrôle lors de l’initialisation du Runtime.

*CanSelect* signifie que l' *interagissement* peut passer de *off* à *on* , tandis que le *CanDeselect* signifie l’inverse.

![Exemple de thème visuel basculement de profil](../images/interactable/Profile_toggle.png)

Les développeurs peuvent utiliser [`SetToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) les [`IsToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) interfaces et pour accéder ou définir l’État bascule d’une interface *interactive* via du code.

```c#
// If using SelectionMode = Toggle (i.e Dimensions == 2)

// Make the Interactable selected and toggled on
myInteractable.IsToggled = true;

// Get whether the Interactable is selected or not
bool isSelected = myInteractable.IsToggled;
```

##### <a name="toggle-button-collection"></a>Basculer la collection de boutons

Il est courant d’avoir une liste de boutons bascule où un seul peut être actif à un moment donné, également appelé un ensemble radial ou des cases d’option, etc.

Utilisez le [`InteractableToggleCollection`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableToggleCollection) composant pour activer cette fonctionnalité. Ce contrôle garantit qu’un seul *interagissant* est activé à un moment donné. *RadialSet* (Assets/MRTK/SDK/features/UX/interactive/Prefabs/RadialSet. Prefab) est également un excellent point de départ prêt à l’emploi.

Pour créer un groupe de boutons radial personnalisé :

1) Créer plusieurs *GameObjects* /boutons interactifs
1) Définir chaque *interagissant* avec *SelectionMode* = Toggle, *CanSelect* = true et *CanDeselect* = false
1) Créer un GameObject parent vide sur tous les *Interactables* et ajouter le composant *InteractableToggleCollection*
1) Ajoutez tous les *Interactables* à *ToggleList* sur *InteractableToggleCollection*
1) Définissez la propriété *InteractableToggleCollection. CurrentIndex* pour déterminer le bouton sélectionné par défaut au démarrage

<img src="../images/interactable/InteractableToggleCollection.png" width="450" alt="Toggle collection">

#### <a name="multi-dimensional-button"></a>Bouton multidimensionnel

Le mode de sélection de plusieurs dimensions est utilisé pour créer des boutons séquentiels, ou un bouton qui compte plus de deux étapes, comme le contrôle de la vitesse avec trois valeurs, rapide (1x), plus rapide (2x) ou plus rapide (3x).

Comme les dimensions sont une valeur numérique, vous pouvez ajouter jusqu’à 9 thèmes pour contrôler l’étiquette de texte ou la texture du bouton pour chaque paramètre de vitesse, à l’aide d’un thème différent pour chaque étape.

Chaque événement de clic avance de à `DimensionIndex` 1 au moment de l’exécution jusqu’à ce que la `Dimensions` valeur soit atteinte. Le cycle est alors réinitialisé à 0.

![Exemple de profil multidimensionnel](../images/interactable/Profile_multiDimensions.png)

Les développeurs peuvent évaluer le [`DimensionIndex`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) pour déterminer quelle dimension est actuellement active.

```c#
// If using SelectionMode = Multi-dimension (i.e Dimensions >= 3)

//Access the current DimensionIndex
int currentDimension = myInteractable.CurrentDimension;

//Set the current DimensionIndex to 2
myInteractable.CurrentDimension = 2;

// Promote Dimension to next level
myInteractable.IncreaseDimension();
```

### <a name="create-interactable-at-runtime"></a>Créer des dialogues interactifs au moment de l’exécution

Vous *pouvez facilement* ajouter des GameObjectables à n’importe quel moment de l’exécution. L’exemple suivant montre comment assigner un profil avec un [thème visuel](visual-themes.md).

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

### <a name="interactable-events-via-code"></a>Événements interactifs via du code

Vous pouvez ajouter une action à l’événement de base [`Interactable.OnClick`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.OnClick) par le biais du code avec l’exemple suivant.

```c#
public static void AddOnClick(Interactable interactable)
{
    interactable.OnClick.AddListener(() => Debug.Log("Interactable clicked"));
}
```

Utilisez la [`Interactable.AddReceiver<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) fonction pour ajouter dynamiquement des récepteurs d’événements au moment de l’exécution.

L’exemple de code ci-dessous montre comment ajouter un [InteractableOnFocusReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), qui écoute l’entrée/la sortie Focus, et définir le code d’action à exécuter lorsque les instances d’événements se déclenchent.

```c#
public static void AddFocusEvents(Interactable interactable)
{
    var onFocusReceiver = interactable.AddReceiver<InteractableOnFocusReceiver>();

    onFocusReceiver.OnFocusOn.AddListener(() => Debug.Log("Focus on"));
    onFocusReceiver.OnFocusOff.AddListener(() => Debug.Log("Focus off"));
}
```

L’exemple de code ci-dessous montre comment ajouter un [InteractableOnToggleReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), qui écoute les transitions d’État sélectionnées/désélectionnées sur les *Interactables* pouvant être activés et qui définit le code d’action à exécuter lorsque les instances d’événements se déclenchent.

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

## <a name="see-also"></a>Voir aussi

* [Thèmes visuels](visual-themes.md)
* [Actions d’entrée](../input/input-actions.md)
* [Commandes vocales](../input/speech.md)
* [Boutons](button.md)
* [Nuanceur standard MRTK](../rendering/MRTK-standard-shader.md)
