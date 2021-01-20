---
title: Contrôleurs de réverbération HP G2 dans Unity
description: Découvrez comment configurer et utiliser les nouveaux contrôleurs G2 de réverbération HP dans SteamVR et les applications Windows Mixed Reality Unity.
author: hferrone
ms.author: v-hferrone
ms.date: 10/14/2020
ms.topic: article
keywords: Unity, réverbération, réverbération G2, réverbération HP G2, réalité mixte, développement, contrôleurs de mouvement, entrée d’utilisateur, fonctionnalités, nouveau projet, émulateur, documentation, guides, fonctionnalités, hologrammes, développement de jeux
ms.openlocfilehash: fa9b80076d65978ae1602fc4f9519d7e11c651b5
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583574"
---
# <a name="hp-reverb-g2-controllers-in-unity"></a>Contrôleurs de réverbération HP G2 dans Unity

Les contrôleurs de mouvement HP sont un tout nouveau type de contrôleurs de réalité mixte Windows : la même technologie de suivi avec un ensemble légèrement différent d’entrées disponibles : 

* Le pavé tactile a été remplacé par deux boutons : A et B pour le contrôleur de droite, et X et Y pour le contrôleur de gauche. 
* Comprendre est maintenant un déclencheur qui publie un flux de valeurs entre 0,0 et 1,0 au lieu d’un bouton avec des États enfoncé et non enfoncé. 

Étant donné que les nouvelles entrées ne sont pas accessibles via les API Windows et Unity existantes, vous devez disposer du package UPM **Microsoft. MixedReality. Input** dédié. 

> [!IMPORTANT]
> **Les classes de ce package ne remplacent pas les API Windows et Unity existantes, mais les complètent.** Les fonctionnalités couramment disponibles pour les contrôleurs de réalité mixte Windows classiques et les contrôleurs de mouvement HP sont accessibles via le même chemin de code à l’aide des API existantes. Seules les nouvelles entrées nécessitent l’utilisation du package Microsoft. MixedReality. Input supplémentaire. 

## <a name="hp-motion-controller-overview"></a>Présentation du contrôleur HP motion

*Microsoft. MixedReality. Input. MotionController* représente un contrôleur de mouvement. Chaque instance *MotionController* a un *XR. WSA. Entrée. InteractionSource* , qui peut être corrélée à l’aide de la main, de l’ID de fournisseur, de l’ID de produit et de la version. 

Vous pouvez récupérer des instances MotionController en créant un *MotionControllerWatcher* et en vous abonnant à ses événements, de la même manière qu’en utilisant des événements *InteractionManager* pour découvrir de nouvelles instances *InteractionSource* . Les méthodes et propriétés de MotionController décrivent les entrées prises en charge par le contrôleur, y compris ses boutons, déclencheurs, axe 2D et stick analogique. La classe MotionController expose également des méthodes permettant d’accéder aux États d’entrée par le biais de la classe *MotionControllerReading* . La classe MotionControllerReading représente un instantané de l’état du contrôleur à un moment donné. 

## <a name="installing-microsoftmixedrealityinput-using-the-unity-package-manager"></a>Installation de Microsoft. MixedReality. Input à l’aide du gestionnaire de package Unity 

Le gestionnaire de package Unity utilise un [fichier manifeste](https://docs.unity3d.com/Manual/upm-manifestPkg.html) (manifest.js) pour déterminer les packages à installer et les registres (serveurs) à partir desquels ils peuvent être installés. Avant de pouvoir utiliser le package Microsoft. MixedReality. Input, vous devez inscrire le serveur de composants de la réalité mixte.

### <a name="registering-the-mixed-reality-component-server"></a>Inscription du serveur de composants de la réalité mixte 

Pour chaque projet qui utilisera le package d’entrée de réalité mixte, le manifest.jssur le fichier (dans le dossier Packages) nécessite l’ajout du Registre avec étendue de la réalité mixte. Pour modifier correctement manifest.jsdans pour prendre en charge la réalité mixte : 
    1. Ouvrez <projectRoot> /Packages/manifest.jsdans un éditeur de texte, tel que Visual Studio code. 
    2. En haut du fichier manifeste, ajoutez le serveur de réalité mixte à la section du Registre étendu et enregistrez le fichier. 
    
<pre>
{ 
  "scopedRegistries": [ 
    { 
      "name": "Microsoft Mixed Reality", 
      "url": "https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/", 
      "scopes": [ 
        "com.microsoft.mixedreality" 
      ] 
    } 
  ], 
</pre>

### <a name="adding-the-microsoftmixedrealityinput-package"></a>Ajout du package Microsoft. MixedReality. Input 

Modifiez la section des dépendances de l' <projectRoot> manifest.js/packages/sur le fichier dans l’éditeur de texte pour ajouter le package com. Microsoft. mixedreality. Input et enregistrez le fichier. 

<pre>
  "dependencies": { 
    "com.microsoft.mixedreality.input": "0.9.2006", 
  }
</pre>

## <a name="using-microsoftmixedrealityinput"></a>Utilisation de Microsoft. MixedReality. Input 

### <a name="input-values"></a>Valeurs d’entrée

Un MotionController peut exposer deux types d’entrées : 

* Les boutons et les États de déclencheur sont exprimés par une valeur flottante unique comprise entre 0,0 et 1,0, qui indique combien ils sont appuyés.
    * Un bouton peut retourner uniquement 0,0 (lorsqu’il n’est pas enfoncé) ou 1,0 (lorsqu’il est enfoncé) alors qu’un déclencheur peut retourner des valeurs continues entre 0,0 (entièrement relâché) et 1,0 (entièrement enfoncé). 
* L’état du joystick est exprimé par un Vector2 dont les composants X et Y sont compris entre-1,0 et 1,0. 

Vous pouvez utiliser *MotionController. GetPressableInputs ()* pour retourner une liste d’entrées renvoyant une valeur appuyée (boutons et déclencheurs) ou la méthode *MotionController. GetXYInputs ()* pour retourner une liste d’entrées retournant une valeur à 2 axes. 

Une instance MotionControllerReading représente l’état du contrôleur à un moment donné : 

* *GetPressedValue ()* récupère l’état d’un bouton ou d’un déclencheur. 
* *GetXYValue ()* récupère l’état d’un stick analogique. 

### <a name="creating-a-cache-to-maintain-a-collection-of-motioncontroller-instances-and-their-states"></a>Création d’un cache pour tenir à jour une collection d’instances MotionController et leurs États 

Commencez par instancier un MotionControllerWatcher et inscrire des gestionnaires pour ses événements *MotionControllerAdded* et *MotionControllerRemoved* afin de conserver un cache des instances MotionController disponibles. Ce cache doit être un monocomportement attaché à un GameObject, comme illustré dans le code suivant :

```csharp
public class MotionControllerStateCache : MonoBehaviour 
{ 
    /// <summary> 
    /// Internal helper class which associates a Motion Controller 
    /// and its known state 
    /// </summary> 
    private class MotionControllerState 
    { 
        /// <summary> 
        /// Construction 
        /// </summary> 
        /// <param name="mc">motion controller</param>` 
        public MotionControllerState(MotionController mc) 
        { 
            this.MotionController = mc; 
        } 

        /// <summary> 
        /// Motion Controller that the state represents 
        /// </summary> 
        public MotionController MotionController { get; private set; } 
        … 
    } 

    private MotionControllerWatcher _watcher; 
    private Dictionary<Handedness, MotionControllerState> 
        _controllers = new Dictionary<Handedness, MotionControllerState>(); 

    /// <summary> 
    /// Starts monitoring controller's connections and disconnections 
    /// </summary> 
    public void Start() 
    { 
        _watcher = new MotionControllerWatcher(); 
        _watcher.MotionControllerAdded += _watcher_MotionControllerAdded; 
        _watcher.MotionControllerRemoved += _watcher_MotionControllerRemoved; 
        var nowait = _watcher.StartAsync(); 
    } 

    /// <summary> 
    /// Stops monitoring controller's connections and disconnections 
    /// </summary> 
    public void Stop() 
    { 
        if (_watcher != null) 
        { 
            _watcher.MotionControllerAdded -= _watcher_MotionControllerAdded; 
            _watcher.MotionControllerRemoved -= _watcher_MotionControllerRemoved; 
            _watcher.Stop(); 
        } 
    }

    /// <summary> 
    /// called when a motion controller has been removed from the system: 
    /// Remove a motion controller from the cache 
    /// </summary> 
    /// <param name="sender">motion controller watcher</param> 
    /// <param name="e">motion controller </param> 
    private void _watcher_MotionControllerRemoved(object sender, MotionController e) 
    { 
        lock (_controllers) 
        { 
            _controllers.Remove(e.Handedness); 
        } 
    }

    /// <summary> 
    /// called when a motion controller has been added to the system: 
    /// Remove a motion controller from the cache 
    /// </summary> 
    /// <param name="sender">motion controller watcher</param> 
    /// <param name="e">motion controller </param> 
    private void _watcher_MotionControllerAdded(object sender, MotionController e) 
    { 
        lock (_controllers) 
        { 
            _controllers[e.Handedness] = new MotionControllerState(e); 
        } 
    } 
} 
```

### <a name="reading-new-inputs-by-polling"></a>Lecture de nouvelles entrées par interrogation 

Vous pouvez lire l’état actuel de chaque contrôleur connu par le biais de *MotionController. TryGetReadingAtTime* pendant la méthode *Update* de la classe monobehavior. Vous souhaitez passer *DateTime. Now* en tant que paramètre timestamp pour vous assurer que l’état le plus récent du contrôleur est Read. 

```csharp
public class MotionControllerStateCache : MonoBehaviour 
{ 
    … 

    private class MotionControllerState 
    {
        … 

        /// <summary> 
        /// Update the current state of the motion controller 
        /// </summary> 
        /// <param name="when">time of the reading</param> 
        public void Update(DateTime when) 
        { 
            this.CurrentReading = this.MotionController.TryGetReadingAtTime(when); 
        } 

        /// <summary> 
        /// Last reading from the controller 
        /// </summary> 
        public MotionControllerReading CurrentReading { get; private set; } 
    } 

    /// <summary> 
    /// Updates the input states of the known motion controllers 
    /// </summary> 
    public void Update() 
    { 
        var now = DateTime.Now; 

        lock (_controllers) 
        { 
            foreach (var controller in _controllers) 
            { 
                controller.Value.Update(now); 
            } 
        } 
    } 
} 
```

Vous pouvez récupérer la valeur d’entrée actuelle des contrôleurs à l’aide de la droitier du contrôleur : 

```csharp
public class MotionControllerStateCache : MonoBehaviour 
{ 
    … 
    /// <summary> 
    /// Returns the current value of a controller input such as button or trigger 
    /// </summary> 
    /// <param name="handedness">Handedness of the controller</param> 
    /// <param name="input">Button or Trigger to query</param> 
    /// <returns>float value between 0.0 (not pressed) and 1.0 
    /// (fully pressed)</returns> 
    public float GetValue(Handedness handedness, ControllerInput input) 
    { 
        MotionControllerReading currentReading = null; 

        lock (_controllers) 
        { 
            if (_controllers.TryGetValue(handedness, out MotionControllerState mc)) 
            { 
                currentReading = mc.CurrentReading; 
            } 
        } 

        return (currentReading == null) ? 0.0f : currentReading.GetPressedValue(input); 
    } 

    /// <summary> 
    /// Returns the current value of a controller input such as button or trigger 
    /// </summary> 
    /// <param name="handedness">Handedness of the controller</param> 
    /// <param name="input">Button or Trigger to query</param> 
    /// <returns>float value between 0.0 (not pressed) and 1.0 
    /// (fully pressed)</returns> 
    public float GetValue(UnityEngine.XR.WSA.Input.InteractionSourceHandedness handedness, ControllerInput input) 
    { 
        return GetValue(Convert(handedness), input); 
    } 

    /// <summary> 
    /// Returns a boolean indicating whether a controller input such as button or trigger is pressed 
    /// </summary> 
    /// <param name="handedness">Handedness of the controller</param> 
    /// <param name="input">Button or Trigger to query</param> 
    /// <returns>true if pressed, false if not pressed</returns> 
    public bool IsPressed(Handedness handedness, ControllerInput input) 
    { 
        return GetValue(handedness, input) >= PressedThreshold; 
    } 
} 
```

Par exemple, pour lire la valeur de préhension analogique d’un InteractionSource : 

```csharp
/// Read the analog grasp value of all connected interaction sources 
void Update() 
{ 
    … 
    var stateCache = gameObject.GetComponent<MotionControllerStateCache>(); 
    foreach (var sourceState in InteractionManager.GetCurrentReading()) 
    { 
        float graspValue = stateCache.GetValue(sourceState.source.handedness, 
            Microsoft.MixedReality.Input.ControllerInput.Grasp);
        … 
    }
} 
```

### <a name="generating-events-from-the-new-inputs"></a>Génération d’événements à partir des nouvelles entrées 

Au lieu d’interroger l’état d’un contrôleur une fois par Frame, vous avez la possibilité de gérer toutes les modifications d’État en tant qu’événements, ce qui vous permet de gérer même les actions les plus rapides qui sont moins qu’un cadre. Pour que cette approche fonctionne, le cache des contrôleurs motion doit traiter tous les États publiés par un contrôleur depuis la dernière trame, ce que vous pouvez faire en stockant l’horodateur du dernier MotionControllerReading récupéré à partir d’un MotionController et en appelant *MotionController. TryGetReadingAfterTime ()*: 

```csharp
private class MotionControllerState 
{ 
    … 
    /// <summary> 
    /// Returns an array representng buttons which are pressed 
    /// </summary> 
    /// <param name="reading">motion controller reading</param> 
    /// <returns>array of booleans</returns> 
    private bool[] GetPressed(MotionControllerReading reading) 
    { 
        if (reading == null) 
        { 
            return null; 
        } 
        else 
        { 
            bool[] ret = new bool[this.pressableInputs.Length]; 
            for (int i = 0; i < pressableInputs.Length; ++i) 
            { 
                ret[i] = reading.GetPressedValue(pressableInputs[i]) >= PressedThreshold; 
            } 

            return ret; 
        } 
    } 

    /// <summary> 
    /// Get the next available state of the motion controller 
    /// </summary> 
    /// <param name="lastReading">previous reading</param> 
    /// <param name="newReading">new reading</param> 
    /// <returns>true is a new reading was available</returns> 
    private bool GetNextReading(MotionControllerReading lastReading, out MotionControllerReading newReading) 
    { 
        if (lastReading == null) 
        { 
            // Get the first state published by the controller 
            newReading = this.MotionController.TryGetReadingAfterSystemRelativeTime(TimeSpan.FromSeconds(0.0)); 
        } 
        else 
        { 
            // Get the next state published by the controller 
            newReading = this.MotionController.TryGetReadingAfterTime(lastReading.InputTime); 
        } 

        return newReading != null; 
    } 

    /// <summary> 
    /// Processes all the new states published by the controller since the last call 
    /// </summary> 
    public IEnumerable<MotionControllerEventArgs> GetNextEvents() 
    {
        MotionControllerReading lastReading = this.CurrentReading; 
        bool[] lastPressed = GetPressed(lastReading); 
        MotionControllerReading newReading; 
        bool[] newPressed; 

        while (GetNextReading(lastReading, out newReading)) 
        { 
            newPressed = GetPressed(newReading); 

            // If we have two readings, compare and generate events 
            if (lastPressed != null) 
            { 
                for (int i = 0; i < pressableInputs.Length; ++i) 
                { 
                    if (newPressed[i] != lastPressed[i]) 
                    { 
                        yield return new MotionControllerEventArgs(this.MotionController.Handedness, newPressed[i], this.pressableInputs[i], newReading.InputTime); 
                    } 
                } 
            } 

            lastPressed = newPressed; 
            lastReading = newReading; 
        } 

        // No more reading 
        this.CurrentReading = lastReading; 
    } 
} 
```

Maintenant que vous avez mis à jour les classes internes du cache, la classe monobehavior peut exposer deux événements, appuyés et libérés, et les déclencher à partir de sa méthode Update () : 

```csharp
/// <summary> 
/// Event argument class for InputPressed and InputReleased events 
/// </summary> 
public class MotionControllerEventArgs : EventArgs 
{ 
    public MotionControllerEventArgs(Handedness handedness, bool isPressed, rollerInput input, DateTime inputTime) 
    { 
        this.Handedness = handedness; 
        this.Input = input; 
        this.InputTime = inputTime; 
        this.IsPressed = isPressed; 
    } 

    /// <summary> 
    /// Handedness of the controller raising the event 
    /// </summary> 
    public Handedness Handedness { get; private set; } 

    /// <summary> 
    /// Button pressed or released 
    /// </summary> 
    public ControllerInput Input { get; private set; } 

    /// <summary> 
    /// Time of the event 
    /// </summary> 
    public DateTime InputTime { get; private set; } 

    /// <summary> 
    /// true if button is pressed, false otherwise 
    /// </summary> 
    public bool IsPressed { get; private set; } 
} 

/// <summary> 
/// Event raised when a button is pressed 
/// </summary> 
public event EventHandler<MotionControllerEventArgs> InputPressed; 

/// <summary> 
/// Event raised when a button is released 
/// </summary> 
public event EventHandler<MotionControllerEventArgs> InputReleased; 

/// <summary> 
/// Updates the input states of the known motion controllers 
/// </summary> 
public void Update() 
{ 
    // If some event handler has been registered, we need to process all states  
    // since the last update, to avoid missing a quick press / release 
    if ((InputPressed != null) || (InputReleased != null)) 
    { 
        List<MotionControllerEventArgs> events = new <MotionControllerEventArgs>(); 

        lock (_controllers) 
        { 
            foreach (var controller in _controllers) 
            { 
                events.AddRange(controller.Value.GetNextEvents()); 
            } 
        } 
 
        // Sort the events by time 
        events.Sort((e1, e2) => DateTime.Compare(e1.InputTime, e2.InputTime)); 

        foreach (MotionControllerEventArgs evt in events) 
        { 
            if (evt.IsPressed && (InputPressed != null)) 
            { 
                InputPressed(this, evt); 
            } 
            else if (!evt.IsPressed && (InputReleased != null)) 
            { 
                InputReleased(this, evt); 
            } 
        } 
    } 
    else 
    { 
        // As we do not predict button presses and the timestamp of the next e is in the future 
        // DateTime.Now is correct in this context as it will return the latest e of controllers 
        // which is the best we have at the moment for the frame. 
        var now = DateTime.Now; 
        lock (_controllers) 
        { 
            foreach (var controller in _controllers) 
            { 
                controller.Value.Update(now); 
            } 
        } 
    } 
} 
```

La structure dans les exemples de code ci-dessus rend les événements d’inscription plus lisibles : 

```csharp
public InteractionSourceHandedness handedness; 
public Microsoft.MixedReality.Input.ControllerInput redButton;

// Start of the Mono Behavior: register handlers for events from cache 
void Start() 
{ 
    var stateCache = gameObject.GetComponent<MotionControllerStateCache>(); 
    stateCache.InputPressed += stateCache_InputPressed; 
    stateCache.InputReleased += stateCache_InputReleased; 
    … 
} 

// Called when a button is released 
private void stateCache_InputReleased(object sender, MotionControllerStateCache.MotionControllerEventArgs e) 
{ 
    if ((e.SourceHandedness == handedness) && (e.Input == redButton)) 
    { 
        … 
    } 
} 

// Called when a button is pressed 
private void stateCache_InputPressed(object sender, MotionControllerStateCache.MotionControllerEventArgs e) 
{ 
    if ((e.SourceHandedness == handedness) && (e.Input == redButton)) 
    { 
        … 
    } 
} 
```

## <a name="see-also"></a>Voir aussi

<!-- ## Getting started

There's no additional setup required to use the HP Reverb G2 controller if you're developing for SteamVR or using the Windows Mixed Reality Input API (XR.WSA.Input). However, the A, B, X, Y buttons and the squeeze trigger are not currently accessible through the Input Manager unless you're using SteamVR. Support for the extra Reverb G2 inputs will be available in the near future, so be sure to check back!

## Porting existing applications

If you already have an existing app that you're developing for Windows Mixed Reality immersive headsets, check out our [porting guide](../porting-apps/porting-guides.md) and [project settings](../porting-apps/porting-guides.md?tabs=project#unity-porting-guidance) sections for general suggestions.

## Mapping input

When you're ready to get your input mapping up and running for your new controllers, start at the [input mapping](../porting-apps/porting-guides.md?tabs=input#unity-porting-guidance) section of the immersive porting guide. Instructions on how to configure inputs in Unity is detailed in [Gestures and motion controllers](gestures-and-motion-controllers-in-unity.md), along with a full [button and axis mapping table](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) for reference.

## See also
* [Updating for SteamVR](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md) -->