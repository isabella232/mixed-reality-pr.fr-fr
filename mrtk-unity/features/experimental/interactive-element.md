---
title: Élément interactif
description: Documentation de InteractiveElement MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 02/22/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, élément interactif, interactif
ms.openlocfilehash: 6d8f36c4780844e991eb32943645402503fab8340c6843dbb607f1c11033d912
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220442"
---
# <a name="interactive-element-experimental"></a>Élément interactif [expérimental]

Point d’entrée centralisé simplifié dans le système d’entrée MRTK. Contient les méthodes de gestion d’État, la gestion des événements et la logique de paramétrage d’État pour les États d’interaction de base.

L’élément interactif est une fonctionnalité expérimentale prise en charge dans Unity 2019,3 et up, car elle utilise une fonctionnalité nouvelle dans Unity 2019,3 : [Serialize Reference](https://docs.unity3d.com/ScriptReference/SerializeReference.html).

### <a name="interactive-element-inspector"></a>Inspecteur d’élément interactif

En mode lecture, l’inspecteur d’élément interactif fournit un retour visuel qui indique si l’état actuel est actif ou non. Si un État est actif, il est mis en surbrillance avec une couleur cyan.  Si l’État n’est pas actif, la couleur n’est pas modifiée. Les nombres situés à côté des États dans l’inspecteur sont les valeurs d’État, si l’État est actif, alors la valeur est 1, si l’État n’est pas actif, la valeur est 0.

![Élément interactif avec interaction de la main virtuelle](../images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

## <a name="core-states"></a>États de base

L’élément interactif contient les États principaux et prend en charge l’ajout d' [États personnalisés](#custom-states).  Un état de base est un État qui possède déjà la logique du paramètre d’état définie dans `BaseInteractiveElement` . La liste suivante répertorie les États de base d’entrée actuels : 

### <a name="current-core-states"></a>États de base actuels

- [Par défaut](#default-state) 

États de base de l’interaction near et Far :
- [Spécialisés](#focus-state) 

États de base near interaction :

- [Focus près](#focus-near-state)
- [Interface tactile](#touch-state)

États des cœurs d’interaction Far :
- [Focus à l’extrême](#focus-far-state)
- [Sélectionnez Far](#select-far-state)

Autres États de base :
- [Clicked](#clicked-state)
- [Activer et désactiver](#toggle-on-and-toggle-off-state)
- [Mot clé Speech](#speech-keyword-state)

### <a name="how-to-add-a-core-state-via-inspector"></a>Ajout d’un état de base via Inspector

1. Accédez à **Ajouter l’état principal** dans l’inspecteur pour l’élément interactif.

    ![Ajouter un état principal via Inspector](../images/interactive-element/InEditor/InteractiveElementAddCoreState.png)


1. Sélectionnez le bouton **Sélectionner l’État** pour choisir l’état principal à ajouter. Les États dans le menu sont triés par type d’interaction.

    ![Ajouter un état principal via Inspector avec l’état sélectionné](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectState.png)

1. Ouvrez la foldout configuration des événements pour afficher les événements et les propriétés associés à l’État.

    ![Ajouter un état principal via Inspector avec configuration d’événement](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectStateEventConfig.png)


### <a name="how-to-add-a-core-state-via-script"></a>Comment ajouter un état principal via un script

Utilisez la `AddNewState(stateName)` méthode pour ajouter un état de base. Pour obtenir la liste des noms d’État principaux disponibles, utilisez l' `CoreInteractionState` énumération.

```c#
// Add by name or add by CoreInteractionState enum to string

interactiveElement.AddNewState("SelectFar");

interactiveElement.AddNewState(CoreInteractionState.SelectFar.ToString());
```

### <a name="states-internal-structure"></a>Structure interne des États 

Les États dans l’élément interactif sont de type `InteractionState` .  Un `InteractionState` contient les propriétés suivantes :

- **Nom**: nom de l’État.
- **Valeur**: valeur d’État.  Si l’État est activé, la valeur d’État est 1. Si l’État est OFF, la valeur d’État est 0.
- **Actif**: indique si l’État est actuellement actif. La valeur de la propriété active est true lorsque l’État est activé, false si l’État est désactivé. 
- **Type** d’interaction : le type d’interaction d’un État est le type d’interaction auquel un État est destiné. 
  - `None`: Ne prend en charge aucune forme d’interaction d’entrée.
  - `Near`: Prise en charge de l’interaction proche. L’entrée est considérée comme proche de l’interaction quand une main articulée a un contact direct avec un autre objet de jeu, c’est-à-dire la position que la main articulée est proche de la position de l’objet de jeu dans l’espace universel.
  - `Far`: Prise en charge de l’interaction Far. L’entrée est considérée comme une interaction éloignée lorsque le contact direct avec l’objet de jeu n’est pas requis. Par exemple, l’entrée via le rayon du contrôleur ou le point de regard est considérée comme une entrée d’interaction Far.
  - `NearAndFar`: Englobe la prise en charge de l’interaction near et Far. 
  - `Other`: Prise en charge de l’interaction indépendante du pointeur.
- **Configuration** de l’événement : la configuration de l’événement pour un État est le point d’entrée du profil des événements sérialisés. 

Toutes ces propriétés sont définies en interne dans l' `State Manager` élément interactif contenu dans. Pour la modification des États, utilisez les méthodes d’assistance suivantes :

**Méthodes d’assistance de paramétrage d’État**

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

L’obtention de la configuration d’événement d’un État est spécifique à l’État lui-même. Chaque État de base a un type de configuration d’événement spécifique qui est décrit ci-dessous sous les sections décrivant chaque État de base.

Voici un exemple généralisé de l’obtention de la configuration d’événement d’un État :

```c#
// T varies depending on the core state - the specific T's are specified under each of the core state sections
T stateNameEvents = interactiveElement.GetStateEvents<T>("StateName");
```

### <a name="default-state"></a>État par défaut

L’État par défaut est toujours présent sur un élément interactif.  Cet État est actif uniquement lorsque tous les autres États ne sont pas actifs.  Si un autre État devient actif, l’État par défaut est défini sur désactivé en interne. 

Un élément interactif est initialisé avec les États par défaut et de focus présents dans la liste d’États. L’État par défaut doit toujours être présent dans la liste d’État. 

#### <a name="getting-default-state-events"></a>Obtention des événements d’État par défaut

Type de configuration d’événement pour l’État par défaut : `StateEvents`

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

### <a name="focus-state"></a>État du focus

L’état du focus est un état d’interaction proche et éloigné qui peut être considéré comme la réalité mixte équivalente au pointage. Le facteur distinctif entre une interaction proche et éloignée pour l’état du focus est le type de pointeur actif actuel.  Si le type de pointeur de l’état de focus est le pointeur d’action en avant, l’interaction est considérée comme proche de l’interaction.  Si le pointeur principal n’est pas le pointeur avant, l’interaction est considérée comme une interaction lointaine. L’état du focus est présent dans l’élément interactif par défaut.

Comportement de l' **État du focus** 
 ![ État du focus avec interaction de la main virtuelle](../images/interactive-element/InEditor/Gifs/FocusStateEditor.gif) 

**Focus de l’inspecteur** 
 ![ d’État État du focus dans le Inpsector](../images/interactive-element/InEditor/FocusStateInspector.png)

#### <a name="getting-focus-state-events&quot;></a>Obtention des événements d’État du focus

Type de configuration d’événement pour l’état de Focus : `FocusEvents`

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

#### <a name="focus-near-vs-focus-far-behavior"></a>Concentrez-vous sur le comportement Far 

![Concentrez-vous presque et loin avec l’interaction avec la main virtuelle](../images/interactive-element/InEditor/Gifs/FocusNearFocusFar.gif)

### <a name="focus-near-state"></a>Focus sur l’état proche

L’État Focus near est défini lorsqu’un événement focus est déclenché et que le pointeur principal est le pointeur de la fenêtre d’action, une indication de Near interaction. 

**Focus sur le comportement** 
 ![ de l’état proche Focus sur l’état près de l’interaction avec la main virtuelle](../images/interactive-element/InEditor/Gifs/FocusNearStateEditor.gif) 

**Focus près de l’inspecteur** 
 ![ d’État Focus sur le composant dans l’inspecteur](../images/interactive-element/InEditor/FocusNearStateInspector.png)

#### <a name="getting-focusnear-state-events&quot;></a>Obtention des événements d’État FocusNear

Type de configuration d’événement pour l’État FocusNear : `FocusEvents`

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

### <a name="focus-far-state"></a>Activer l’État Far

L’État Focus actif est défini lorsque le pointeur principal n’est pas le pointeur de l’e-out.  Par exemple, le pointeur Ray du contrôleur par défaut et le pointeur GGV (point d’interligne, voix) sont considérés comme des pointeurs d’interaction Far.

**Focus sur le comportement** 
 ![ d’État Far Focalisation de l’état avec l’interaction avec la main virtuelle](../images/interactive-element/InEditor/Gifs/FocusFarStateEditor.gif)

**Activer l’inspecteur** 
 ![ d’État Far Focus sur le composant dans l’inspecteur](../images/interactive-element/InEditor/FocusFarStateInspector.png)

#### <a name="getting-focus-far-state-events&quot;></a>Obtention d’événements d’état de focus Far

Type de configuration d’événement pour l’État FocusFar : `FocusEvents`

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

### <a name="touch-state"></a>État tactile

L’État tactile est un état d’interaction proche qui est défini lorsqu’une main articulée touche l’objet directement.  Une pression tactile directe signifie que le doigt de l’index articulé est très proche de la position universelle de l’objet. Par défaut, un `NearInteractionTouchableVolume` composant est attaché à l’objet si l’État tactile est ajouté à la liste d’États.  La présence d’un  `NearInteractionTouchableVolume` `NearInteractionTouchable` composant ou est requise pour la détection des événements tactiles.  La différence entre `NearInteractionTouchableVolume` et `NearInteractionTouchable` est que `NearInteractionTouchableVolume` détecte une pression tactile basée sur le conflit de l’objet et `NearInteractionTouchable` détecte une pression tactile dans une zone définie d’un plan.

 
 Comportement ![ de Touch State État tactile avec interaction avec la main virtuelle](../images/interactive-element/InEditor/Gifs/TouchStateEditor.gif)

 
 Inspecteur ![ d’État tactile Composant d’État tactile dans l’inspecteur](../images/interactive-element/InEditor/TouchStateInspector.png)

#### <a name="getting-touch-state-events&quot;></a>Obtention d’événements d’État tactile

Type de configuration d’événement pour l’État tactile : `TouchEvents`

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

### <a name="select-far-state"></a>Sélectionner l’État Far

L’état de sélection FAR est `IMixedRealityPointerHandler` surfaced.  Cet État est un état d’interaction beaucoup plus éloigné qui détecte l’interaction avec le clic (air-TAP) et maintient à travers l’utilisation de pointeurs d’interaction Far tels que le pointeur de rayon du contrôleur par défaut ou le pointeur GGV.  L’option de sélection de l’État Far a une option sous le foldout de configuration d’événement nommé `Global` . Si `Global` a la valeur true, le `IMixedRealityPointerHandler` est inscrit en tant que gestionnaire d’entrée global.  Il n’est pas nécessaire de se concentrer sur un objet pour déclencher des événements du système d’entrée si un gestionnaire est inscrit en tant que global.  Par exemple, si un utilisateur souhaite savoir à quel moment le mouvement air-TAP/Select est effectué indépendamment de l’objet actif, définissez `Global` sur true. 

**Sélectionner le comportement** 
 ![ de l’État Far Sélectionnez bien avec l’interaction avec la main virtuelle](../images/interactive-element/InEditor/Gifs/SelectFarStateEditor.gif)

**Sélectionner l’inspecteur** 
 ![ d’État Far Sélectionner le composant Far dans l’inspecteur](../images/interactive-element/InEditor/SelectFarStateInspector.png)

#### <a name="getting-select-far-state-events&quot;></a>Obtention d’événements d’état de sélection Far

Type de configuration d’événement pour l’État SelectFar : `SelectFarEvents`

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

### <a name="clicked-state"></a>État de clic

L’état de clic est déclenché par un clic d’interaction Far (sélectionner l’État FAR) par défaut.  Cet État est activé en interne, appelle l’événement OnClicked, puis est immédiatement désactivé. 

> [!NOTE]
> Les commentaires visuels dans l’inspecteur en fonction de l’activité d’État ne sont pas présents pour l’état de clic, car ils sont activés et désactivés immédiatement. 

Comportement de l' **État de clic** 
 ![ État de clic avec interactions de la main virtuelle](../images/interactive-element/InEditor/Gifs/ClickedStateEditor.gif)

 
 Inspecteur ![ d’État cliqué Cliquer sur le composant État dans l’inspecteur](../images/interactive-element/InEditor/ClickedStateInspector.png)

**Exemple d’État near et Far cliqué**  
L’état de clic peut être déclenché via des points d’entrée supplémentaires à l’aide de la `interactiveElement.TriggerClickedState()` méthode.  Par exemple, si un utilisateur souhaite une touche near interaction pour déclencher un clic sur un objet également, il ajoute la `TriggerClickedState()` méthode en tant qu’écouteur dans l’État tactile.   

![État near et Far avec interactions avec la main virtuelle](../images/interactive-element/InEditor/Gifs/NearFarClickedState.gif)

#### <a name="getting-clicked-state-events&quot;></a>Obtention des événements d’état de clic

Type de configuration d’événement pour l’état de clic : `ClickedEvents`

```c#
ClickedEvents clickedEvent = interactiveElement.GetStateEvents<ClickedEvents>(&quot;Clicked");

clickedEvent.OnClicked.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Clicked");
});
```

### <a name="toggle-on-and-toggle-off-state"></a>Activer et désactiver l’État

Les États de basculement et de basculement sont une paire et doivent tous les deux être présents pour le comportement de basculement.  Par défaut, les États activer/désactiver les basculements sont déclenchés à l’aide d’un clic d’interaction Far (sélectionnez l’État FAR).  Par défaut, l’état de basculement est actif au démarrage, ce qui signifie que le basculement sera initialisé à OFF.  Si un utilisateur souhaite activer l’État basculer sur actif au démarrage, dans l’État basculer sur défini sur `IsSelectedOnStart` true.

**ToggleOn et activer/désactiver le comportement** 
 ![ de l’État Activer et désactiver les interactions avec la main virtuelle](../images/interactive-element/InEditor/Gifs/ToggleOnToggleOffStateEditor.gif)

**ToggleOn et activer/désactiver l’inspecteur** 
 ![ d’État Basculer le composant dans l’inspecteur](../images/interactive-element/InEditor/ToggleOnToggleOffStateInspector.png)

**Exemple d’États de basculement near et Far**  
À l’instar de l’État cliqué, le paramètre basculer l’État peut avoir plusieurs points d’entrée à l’aide de la `interactiveElement.SetToggleStates()` méthode. Par exemple, si un utilisateur souhaite toucher en tant que point d’entrée supplémentaire pour définir les États de basculement, il ajoute la `SetToggleStates()` méthode à l’un des événements à l’État tactile. 

![Bascule presque et Far avec les interactions de la main virtuelle](../images/interactive-element/InEditor/Gifs/NearFarToggleStates.gif)

#### <a name="getting-toggle-on-and-toggle-off-state-events&quot;></a>Activation et désactivation des événements d’État

Type de configuration d’événement pour l’État ToggleOn : `ToggleOnEvents`  
Type de configuration d’événement pour l’État ToggleOff : `ToggleOffEvents`

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

### <a name="speech-keyword-state"></a>État du mot clé Speech

L’état du mot clé Speech écoute les mots clés définis dans le profil de voix de la réalité mixte. Tout nouveau mot clé doit être enregistré dans le profil de commande vocale avant l’exécution (étapes ci-dessous). 

Comportement de l' **État des mots clés Speech** 
 ![ Mot clé Speech avec interaction virtuelle](../images/interactive-element/InEditor/Gifs/SpeechKeywordStateEditor.gif)

Inspecteur d’état de **mot clé Speech** 
 ![ Composant de mot clé Speech dans l’inspecteur](../images/interactive-element/InEditor/SpeechKeywordStateInspector.png)

> [!NOTE]
> L’état du mot clé Speech a été déclenché dans l’éditeur en appuyant sur la touche F5 dans le GIF ci-dessus. La configuration dans l’éditeur de test pour la reconnaissance vocale est décrite dans les étapes ci-dessous. 

#### <a name="how-to-register-a-speech-commandkeyword"></a>Comment inscrire une commande/un mot clé Speech

1. Sélectionner l’objet de jeu **MixedRealityToolkit**

1. Sélectionner **copier et personnaliser** le profil actuel

1. Accédez à la section entrée et sélectionnez **clone** pour permettre la modification du profil d’entrée.

1. Faites défiler jusqu’à la section Speech du profil d’entrée et clonez le profil de reconnaissance vocale.

    ![Profil de mot clé Speech dans l’objet de jeu MRTK](../images/interactive-element/InEditor/SpeechKeywordProfileClone.png) 

1. Sélectionnez Ajouter une nouvelle commande vocale

    ![Ajout d’un nouveau mot clé Speech dans le profil MRTK](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeyword.png) 

1. Entrez le mot clé New. Facultatif : remplacez keycode par F5 (ou un autre keycode) pour permettre le test dans l’éditeur. 

    ![Configuration du mot clé Speech dans le profil MRTK](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeywordName.png) 

1. Revenez à l’inspecteur d’état des mots clés Speech des éléments interactifs et sélectionnez **Ajouter un mot clé** 

    ![Ajout du mot clé au composant d’élément interactif](../images/interactive-element/InEditor/SpeechKeywordAddKeyword.png) 

    ![Validation et enregistrement des mots clés](../images/interactive-element/InEditor/SpeechKeywordAddKeywordBlank.png) 

1. Entrez le nouveau mot clé qui vient d’être enregistré dans le profil de voix

    ![Saisie du nouveau mot clé Speech](../images/interactive-element/InEditor/SpeechKeywordEnterKeyword.png) 


Pour tester l’état du mot clé Speech dans l’éditeur, appuyez sur la touche de code définie à l’étape 6 (F5) pour simuler l’événement reconnu par mot clé Speech.

#### <a name="getting-speech-keyword-state-events&quot;></a>Obtention d’événements d’état de mot clé Speech

Type de configuration d’événement pour l’État SpeechKeyword : `SpeechKeywordEvents`

```c#
SpeechKeywordEvents speechKeywordEvents = interactiveElement.GetStateEvents<SpeechKeywordEvents>(&quot;SpeechKeyword");

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

## <a name="custom-states"></a>États personnalisés

### <a name="how-to-create-a-custom-state-via-inspector"></a>Comment créer un état personnalisé via Inspector 

L’état personnalisé créé via Inspector sera initialisé avec la configuration d’événement d’État par défaut. La configuration d’événement par défaut pour un état personnalisé est de type `StateEvents` et contient les événements OnStateOn et OnStateOff.

1. Accédez à **créer un état personnalisé** dans l’inspecteur pour l’élément interactif.
    
    ![Création d’un état personnalisé](../images/interactive-element/InEditor/InteractiveElementCreateCustomState.png)

1. Entrez le nom du nouvel État. Ce nom doit être unique et ne peut pas être le même que les États de base existants. 
    
    ![Saisie du nom d’un nouvel état personnalisé](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateName.png)

1. Sélectionnez **définir le nom** de l’État à ajouter à la liste d’États.
    
    ![Ajouter un état personnalisé à la liste des États](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateNameSet.png)

   Cet état personnalisé est initialisé avec la configuration d' `StateEvents` événement par défaut qui contient `OnStateOn` les `OnStateOff` événements et. Pour créer une configuration d’événement personnalisée pour un nouvel État, consultez : [création d’un état personnalisé avec une configuration d’événement personnalisée](#creating-a-custom-state-with-a-custom-event-configuration).
    
    ![Nouvel état affiché dans le composant d’élément interactif](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateEventConfig.png)


### <a name="how-to-create-a-custom-state-via-script&quot;></a>Comment créer un état personnalisé à l’aide d’un script

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

### <a name="creating-a-custom-state-with-a-custom-event-configuration"></a>Création d’un état personnalisé avec une configuration d’événement personnalisée 

Des exemples de fichiers pour un état personnalisé nommé **Keyboard** sont disponibles ici : MRTK\SDK\Experimental\InteractiveElement\Examples\Scripts\CustomStateExample

Les étapes suivantes décrivent un exemple de création de fichiers de configuration et de récepteur d’événement d’état personnalisé.

1. Imaginez un nom d’État.  Ce nom doit être unique et ne peut pas être le même que les États de base existants. Dans le cadre de cet exemple, le nom d’État est le **clavier**.

1. Créez deux fichiers. cs nommés State Name + « Receiver » et State Name + « Events ». L’attribution de noms à ces fichiers est prise en compte en interne et doit suivre le nom d’État + Convention Event/Receiver. 

    ![Scripts d’État du clavier](../images/interactive-element/InEditor/KeyboardStateFiles.png)

1. Pour plus d’informations sur le contenu des fichiers, consultez les fichiers KeyboardEvents. cs et KeyboardReceiver. cs. Les nouvelles classes de configuration d’événement doivent hériter de `BaseInteractionEventConfiguration` et de nouvelles classes de récepteur d’événements doivent hériter de `BaseEventReceiver` .  Des exemples sur le paramètre d’état de l’état du clavier se trouvent dans le `CustomStateSettingExample.cs` fichier. 

1. Ajoutez l’État à l’élément interactif en utilisant le nom d’État, le nom d’État sera reconnu si les fichiers de configuration d’événement et de récepteur d’événements existent.  Les propriétés du fichier de configuration d’événement personnalisé doivent apparaître dans l’inspecteur.

    ![Ajout d’un état personnalisé à un élément interactif ](../images/interactive-element/InEditor/AddKeyboardState.png) ![ état personnalisé reconnu dans l’élément interactif](../images/interactive-element/InEditor/SetKeyboardStateName.png)


1. Pour obtenir plus d’exemples de configuration d’événements et de fichiers de récepteur d’événements, consultez les fichiers sur ces chemins d’accès :    
- MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventConfigurations
- MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventReceivers

## <a name="example-scene"></a>Exemple de scène 

L’exemple de scène pour l’élément interactif + visualiseur d’État se trouve ici : MRTK\SDK\Experimental\InteractiveElement\Examples\InteractiveElementExampleScene.unity

![Exemple de scène avec élément interactif et visualiseur d’État](../images/interactive-element/InEditor/ExampleScene.png)

### <a name="compressable-button"></a>Bouton compresseable

L’exemple de scène contient prefabs nommé `CompressableButton` et `CompressableButtonToggle` , ces prefabs reflètent le comportement des `PressableButtonHoloLens2` boutons, qui sont construits à l’aide de l’élément interactif et du visualiseur d’État. Le `CompressableButton` composant est actuellement une combinaison de `PressableButton`  +  `PressableButtonHoloLens2` avec `BaseInteractiveElement` en tant que classe de base. 

## <a name="state-visualizer-experimental"></a>Visualiseur d’État [expérimental]

Le composant visualiseur d’État ajoute des animations à un objet en fonction des États définis dans un composant d’élément interactif lié. Ce composant crée des ressources d’animation, les place dans le dossier MixedRealityToolkit. generated et active le paramètre d’image clé d’animation simplifiée via l’ajout de propriétés animables à un objet de jeu cible. Pour permettre les transitions d’animation entre les États, un élément multimédia de contrôleur d’animation est créé et un ordinateur d’État par défaut est généré avec les paramètres associés et toutes les transitions d’État.  La machine à États peut être affichée dans la fenêtre d’animation de Unity.

### <a name="state-visualizer-and-unity-animation-system"></a>Visualiseur d’État et système d’animation Unity

Le visualiseur d’État tire actuellement parti du système d’animation Unity. 

Lorsque vous appuyez sur le bouton **générer de nouveaux clips d’animation** dans le visualiseur d’État, les nouvelles ressources de clip d’animation sont générées en fonction des noms d’État dans l’élément interactif et placées dans le dossier MixedRealityToolkit. generated. La propriété clip d’animation dans chaque conteneur d’État est définie sur le clip d’animation associé.

![Clips d’animation dans le composant de visualiseur d’État](../images/interactive-element/StateVisualizer/AnimationClips.png)

Une [machine d’état d’animation](https://docs.unity3d.com/Manual/AnimationOverview.html) est également générée pour gérer les transitions lisses entre les clips d’animation.  Par défaut, l’ordinateur d’État utilise l' [État any](https://docs.unity3d.com/Manual/class-State.html) pour autoriser les transitions entre n’importe quel état d’un élément interactif. 

Les [visualiseurs d’État déclenchés dans l’animateur](https://docs.unity3d.com/Manual/AnimationParameters.html) sont également générés pour chaque État, les paramètres de déclencheur sont utilisés dans le visualiseur d’État pour déclencher une animation.

![Machine à États Unity](../images/interactive-element/StateVisualizer/UnityStateMachine.png)

### <a name="runtime-limitations"></a>Limitations du runtime 

Le visualiseur d’État doit être ajouté à un objet via l’inspecteur et ne peut pas être ajouté par le biais d’un script.  Les propriétés qui modifient le AnimatorStateMachine/AnimationController sont contenues dans un espace de noms d’éditeur ( `UnityEditor.Animations` ) qui est supprimé lors de la génération de l’application.

## <a name="how-to-use-the-state-visualizer"></a>Comment utiliser le visualiseur d’État

1. Créer un cube
1. Attacher un élément interactif
1. Visualiseur d’état d’attachement
1. Sélectionner **générer de nouveaux clips d’animation**

    ![Génération de nouveaux clips d’animation](../images/interactive-element/StateVisualizer/GenerateAnimationClips.png)

    ![Présentation des clips d’animation générés dans les composants de visualiseur et d’élément interactif](../images/interactive-element/StateVisualizer/GenerateAnimationClips2.png)

1. Dans le conteneur d’état de focus, sélectionnez **Ajouter une cible** .

    ![Ajout de la cible du visualiseur d’État](../images/interactive-element/StateVisualizer/AddTarget.png)

1. Faites glisser l’objet de jeu actuel vers le champ cible 

    ![Définition de la cible du visualiseur d’État](../images/interactive-element/StateVisualizer/SetTarget.png)

1. Ouvrez le cube propriétés animables foldout
1. Sélectionnez le menu déroulant de la propriété animable et sélectionnez **couleur**

    ![Définition de la couleur du visualiseur d’État](../images/interactive-element/StateVisualizer/SetColor.png)

1. Sélectionnez **Ajouter la couleur animable, propriété**

    ![Sélection de la propriété d’animation couleur du visualiseur](../images/interactive-element/StateVisualizer/SetColorProperty.png)

1. Choisir une couleur 

    ![Choix d’une couleur de visualiseur à partir de la roue de couleur](../images/interactive-element/StateVisualizer/SetBlueColor.png)

1. Appuyez sur lire et observez la modification de la couleur de transition

    ![Exemple de changement de couleur transitoire avec interaction de la main virtuelle](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

## <a name="animatable-properties"></a>Propriétés pouvant être animées

L’objectif principal des propriétés pouvant être animées est de simplifier le paramètre d’image clé du clip d’animation.  si un utilisateur est familiarisé avec le système d’animation unity et préfère définir directement les images clés sur les clips d’animation générés, il peut simplement ne pas ajouter de propriétés animables à un objet cible et ouvrir le clip dans la fenêtre d’animation d’unity (Windows > animation > animation). 

Si vous utilisez les propriétés animables pour l’animation, le type de courbe est défini sur EaseInOut.

**Propriétés d’animation actuelles :**
- [Décalage de l’échelle](#scale-offset)
- [Décalage de position](#position-offset)
- [Couleur](#color)
- [Couleur du nuanceur](#shader-color)
- [Nuanceur float](#shader-float)
- [Vecteur de nuanceur](#shader-vector)

### <a name="scale-offset"></a>Décalage de l’échelle

La propriété animable de décalage de l’échelle prend l’échelle actuelle de l’objet et ajoute l’offset défini.

![Décalage de l’échelle avec interaction de la main virtuelle](../images/interactive-element/InEditor/Gifs/ScaleOffset.gif)

### <a name="position-offset"></a>Décalage de position

La propriété animable de décalage de position prend la position actuelle de l’objet et ajoute l’offset défini.

![Décalage de position avec interaction de la main virtuelle](../images/interactive-element/InEditor/Gifs/PositionOffset.gif)

### <a name="color"></a>Couleur

La propriété d’animation de couleur représente la couleur principale d’un matériau si celui-ci a une propriété de couleur principale. Cette propriété anime la `material._Color` propriété.

![Modification de la couleur du focus avec interaction de la main virtuelle](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="shader-color"></a>Couleur du nuanceur

La propriété d’animation couleur du nuanceur fait référence à une propriété de nuanceur de type couleur. Un nom de propriété est requis pour toutes les propriétés de nuanceur. L’image gif ci-dessous montre comment animer une propriété de couleur de nuanceur nommée Fill_Color qui n’est pas la couleur de matériau principale.  Observez les valeurs variables dans l’inspecteur de matériau.

![Ombrer la couleur avec interaction avec la main virtuelle](../images/interactive-element/InEditor/Gifs/ShaderColor.gif)

### <a name="shader-float"></a>Nuanceur float

La propriété d’animation float de nuanceur fait référence à une propriété de nuanceur de type float. Un nom de propriété est requis pour toutes les propriétés de nuanceur. Dans l’image gif ci-dessous, observez les valeurs variables de l’inspecteur de matériau pour la propriété métallique. 

![Nuanceur flottant avec interaction de la main virtuelle](../images/interactive-element/InEditor/Gifs/ShaderFloat.gif)

### <a name="shader-vector"></a>Vecteur de nuanceur

La propriété animable Vector Shader fait référence à une propriété de nuanceur de type Vector4. Un nom de propriété est requis pour toutes les propriétés de nuanceur. Dans l’image gif ci-dessous, observez les valeurs variables de l’inspecteur de matériau pour la propriété de mosaïque (main Tex_ST). 

![Vecteur de nuanceur avec interaction de la main virtuelle](../images/interactive-element/InEditor/Gifs/ShaderVector.gif)


### <a name="how-to-find-animatable-shader-property-names"></a>Comment rechercher des noms de propriétés de nuanceur animables

1. Naviguer vers la fenêtre > animation > animation
1. S’assurer que l’objet avec le visualiseur d’État est sélectionné dans la hiérarchie
1. Sélectionner un clip d’animation dans la fenêtre d’animation
1. Sélectionnez **Ajouter une propriété**, ouvrez le convertisseur de maillage foldout 

    ![Ajout d’une propriété d’animation dans la fenêtre d’animation](../images/interactive-element/StateVisualizer/AnimationWindow.png)

1. Cette liste contient les noms de tous les noms de propriété pouvant être animés. 

    ![Propriétés d’animation du convertisseur de maillage dans la fenêtre d’animation](../images/interactive-element/StateVisualizer/MeshRendererProperties.png)

## <a name="see-also"></a>Voir aussi

- [**Boutons**](../ux-building-blocks/button.md)
- [**Contrôle de limites**](../ux-building-blocks/bounds-control.md)
- [**Collection d’objets Grid**](../ux-building-blocks/object-collection.md)
- [**Solveur RadialView**](../ux-building-blocks/solvers/solver.md)
