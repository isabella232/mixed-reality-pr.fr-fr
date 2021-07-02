---
title: Événements d’entrée
description: Documentation de InputEvents dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, événements,
ms.openlocfilehash: c8871aa575e2aa4507e9dbbdcc8bdf0fc0604633
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176784"
---
# <a name="input-events"></a>Événements d’entrée

La liste ci-dessous présente toutes les interfaces d’événement d’entrée disponibles à implémenter par un composant monocomportement personnalisé. Ces interfaces sont appelées par le système d’entrée MRTK pour gérer la logique d’application personnalisée en fonction des interactions entre les utilisateurs et les entrées. Les [événements d’entrée de pointeur](pointers.md#pointer-event-interfaces) sont traités légèrement différemment des types d’événements d’entrée standard ci-dessous.

> [!IMPORTANT]
> Par défaut, un script reçoit des événements d’entrée uniquement s’il s’agit du GameObject en focus par un pointeur ou un parent d’un GameObject dans le focus.

| Handler | Événements | Description |
| --- | :---: | --- |
| [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | Source détectée/perdue | Déclenché lorsqu’une source d’entrée est détectée/perdue, par exemple lorsqu’une main articulée est détectée ou perdue. |
| [`IMixedRealitySourcePoseHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourcePoseHandler) | Modification de la source | Levée sur les modifications de la source. La source pose représente la pose générale de la source d’entrée. Vous pouvez obtenir des poses spécifiques, comme la poignée ou le pointeur dans un contrôleur de six DDL, à l’aide de `IMixedRealityInputHandler<MixedRealityPose>` . |
| [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | Entrée vers le haut/haut | Déclenché sur les modifications apportées aux entrées binaires telles que les boutons. |
| [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Entrée modifiée | Déclenché lors des modifications apportées aux entrées du type donné. **T** peut prendre les valeurs suivantes : <br/> - *float* (retourne le déclencheur analogique)<br/> - *Vector2* (par exemple, retourne la direction du joystick) <br/> - *Vector3* (par exemple, retour de la position de l’appareil suivi) <br/> - *Quaternion* (par exemple, retourne l’orientation de l’appareil suivi)<br/> - [MixedRealityPose](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) (par exemple, retourne un appareil entièrement suivi) |
| [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) | Mot clé Speech reconnu | Déclenché lors de la reconnaissance de l’un des mots clés configurés dans le *profil de commandes vocales*. |
| [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) | Dictation<br/> Hypothèse <br/> Result <br/> Terminé <br/> Erreur | Déclenché par les systèmes de dictée pour signaler les résultats d’une session de dictée. |
| [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) | Événements de mouvement sur : <br/> Démarré <br/> Mis à jour <br/> Effectué <br/> Opération annulée | Déclenché lors de la détection de mouvement. |
| [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | Mouvement mis à jour/terminé | Déclenché sur la détection des mouvements contenant des données supplémentaires du type donné. Pour plus d’informations sur les valeurs possibles pour **T**, consultez [**événements de mouvement**](gestures.md#gesture-events) . |
| [`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) | Jointures manuelles mises à jour | Levées par les contrôleurs de main articulés lorsque les joints à la main sont mis à jour. |
| [`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) | Maille manuelle mise à jour | Déclenché par les contrôleurs de main articulés lorsqu’un maillage à la main est mis à jour. |
| [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) | Action démarrée/terminée | Raise pour indiquer le début et la fin de l’action pour les entrées mappées à des actions. |

## <a name="input-events-in-action"></a>Événements d’entrée en action

Au niveau du script, les événements d’entrée peuvent être consommés en implémentant l’une des interfaces de gestionnaire d’événements indiquées dans le tableau ci-dessus. Lorsqu’un événement d’entrée se déclenche via une intervention de l’utilisateur, les éléments suivants ont lieu :

1. Le système d’entrée MRTK reconnaît qu’un événement d’entrée s’est produit.
1. Le système d’entrée MRTK déclenche la fonction d’interface appropriée de l’événement d’entrée à tous les [gestionnaires d’entrée globaux inscrits](#register-for-global-input-events) .
1. Pour chaque pointeur actif inscrit avec le système d’entrée :
    1. Le système d’entrée détermine quel GameObject est en focus pour le pointeur actuel.
    1. Le système d’entrée utilise le [système d’événements Unity](https://docs.unity3d.com/Manual/EventSystem.html) pour déclencher la fonction d’interface appropriée pour tous les composants correspondants sur le gameobject ciblé.
    1. Si, à un moment donné, un événement d’entrée a été [marqué comme étant utilisé](#how-to-stop-input-events), le processus se termine et aucun autre GameObjects ne reçoit les rappels.
        - Exemple : les composants qui implémentent l’interface sont [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) recherchés lorsqu’une commande vocale est reconnue.
        - Remarque : le système d’événements Unity se propage pour rechercher le GameObject parent si aucun composant correspondant à l’interface souhaitée n’est trouvé sur le GameObject actuel.
1. Si aucun gestionnaire d’entrée global n’est inscrit et qu’aucun GameObject n’est trouvé avec un composant/une interface correspondant, le système d’entrée appellera chaque gestionnaire d’entrée de secours inscrit

> [!NOTE]
> Les [événements d’entrée de pointeur](pointers.md#pointer-event-interfaces) sont gérés de manière légèrement différente des interfaces d’événements d’entrée répertoriées ci-dessus. En particulier, les événements d’entrée de pointeur sont gérés uniquement par le GameObject en focus par le pointeur qui a déclenché l’événement d’entrée, ainsi que tous les gestionnaires d’entrée globaux. Les événements d’entrée standard sont gérés par GameObjects dans le focus pour tous les pointeurs actifs.

### <a name="input-event-interface-example"></a>Exemple d’interface d’événement d’entrée

Le code ci-dessous illustre l’utilisation de l' [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) interface. Lorsque l’utilisateur dit les mots « plus petit » ou « plus grand » tout en se concentrant sur un GameObject avec cette `ShowHideSpeechHandler` classe, le gameobject se met à l’échelle d’une demi-ou deux fois.

```c#
public class ShowHideSpeechHandler : MonoBehaviour, IMixedRealitySpeechHandler
{
    ...

    void IMixedRealitySpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.Command.Keyword == "smaller")
        {
            transform.localScale *= 0.5f;
        }
        else if (eventData.Command.Keyword == "bigger")
        {
            transform.localScale *= 2.0f;
        }
    }
}
```

> [!NOTE]
> [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) les événements d’entrée requièrent que les mots clés souhaités soient préinscrits dans le [profil de commandes vocales MRTK](speech.md).

## <a name="register-for-global-input-events"></a>S’inscrire pour les événements d’entrée globaux

Pour créer un composant qui écoute les événements d’entrée globaux, en ignorant les GameObject qui peuvent être activés, un composant doit s’inscrire auprès du système d’entrée. Une fois inscrite, toutes les instances de ce monocomportement recevront des événements d’entrée ainsi que des GameObject (s) de focus et d’autres écouteurs inscrits globaux.

Si un événement d’entrée a été [marqué comme étant utilisé](#how-to-stop-input-events), les gestionnaires enregistrés globaux continuent de recevoir tous les rappels. Toutefois, aucun GameObjects ayant le focus ne recevra l’événement.

### <a name="global-input-registration-example"></a>Exemple d’inscription d’entrée globale

```c#
public class GlobalHandListenerExample : MonoBehaviour,
    IMixedRealitySourceStateHandler, // Handle source detected and lost
    IMixedRealityHandJointHandler // handle joint position updates for hands
{
    private void OnEnable()
    {
        // Instruct Input System that we would like to receive all input events of type
        // IMixedRealitySourceStateHandler and IMixedRealityHandJointHandler
        CoreServices.InputSystem?.RegisterHandler<IMixedRealitySourceStateHandler>(this);
        CoreServices.InputSystem?.RegisterHandler<IMixedRealityHandJointHandler>(this);
    }

    private void OnDisable()
    {
        // This component is being destroyed
        // Instruct the Input System to disregard us for input event handling
        CoreServices.InputSystem?.UnregisterHandler<IMixedRealitySourceStateHandler>(this);
        CoreServices.InputSystem?.UnregisterHandler<IMixedRealityHandJointHandler>(this);
    }

    // IMixedRealitySourceStateHandler interface
    public void OnSourceDetected(SourceStateEventData eventData)
    {
        var hand = eventData.Controller as IMixedRealityHand;

        // Only react to articulated hand input sources
        if (hand != null)
        {
            Debug.Log("Source detected: " + hand.ControllerHandedness);
        }
    }

    public void OnSourceLost(SourceStateEventData eventData)
    {
        var hand = eventData.Controller as IMixedRealityHand;

        // Only react to articulated hand input sources
        if (hand != null)
        {
            Debug.Log("Source lost: " + hand.ControllerHandedness);
        }
    }

    public void OnHandJointsUpdated(
                InputEventData<IDictionary<TrackedHandJoint, MixedRealityPose>> eventData)
    {
        MixedRealityPose palmPose;
        if (eventData.InputData.TryGetValue(TrackedHandJoint.Palm, out palmPose))
        {
            Debug.Log("Hand Joint Palm Updated: " + palmPose.Position);
        }
    }
}
```

## <a name="register-for-fallback-input-events"></a>S’inscrire pour les événements d’entrée de secours

Les gestionnaires d’entrée de secours sont similaires aux gestionnaires d’entrée globaux inscrits, mais ils sont traités en dernier recours pour la gestion des événements d’entrée. Si aucun gestionnaire d’entrée global n’a été trouvé et qu’aucun GameObjects n’est activé, les gestionnaires d’entrée de secours seront exploités.

### <a name="fallback-input-handler-example"></a>Exemple de gestionnaire d’entrée de secours

```c#
public class GlobalHandListenerExample : MonoBehaviour,
    IMixedRealitySourceStateHandler // Handle source detected and lost
{
    private void OnEnable()
    {
        CoreServices.InputSystem?.PushFallbackInputHandler(this);
    }

    private void OnDisable()
    {
        CoreServices.InputSystem?.PopFallbackInputHandler();
    }

    // IMixedRealitySourceStateHandler interface
    public void OnSourceDetected(SourceStateEventData eventData)
    {
        ...
    }

    public void OnSourceLost(SourceStateEventData eventData)
    {
        ...
    }
}
```

## <a name="how-to-stop-input-events"></a>Comment arrêter des événements d’entrée

Chaque interface d’événement d’entrée fournit un [`BaseInputEventData`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputEventData) objet de données en tant que paramètre à chaque fonction de l’interface. Cet objet de données d’événement s’étend du sien de Unity [`AbstractEventData`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.html) .

Afin d’empêcher un événement d’entrée de se propager dans son exécution [comme indiqué](#input-events-in-action), un composant peut appeler [`AbstractEventData.Use()`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.Use.html) pour marquer l’événement comme étant utilisé. Cela empêchera tout autre GameObjects de recevoir l’événement d’entrée actuel, à l’exception des gestionnaires d’entrée globaux.

> [!NOTE]
> Un composant qui appelle la `Use()` méthode empêche d’autres GameObjects de le recevoir. Toutefois, d’autres composants sur le GameObject actuel recevront toujours l’événement d’entrée et déclencheront toutes les fonctions d’interface associées.

## <a name="see-also"></a>Voir aussi

- [Pointeurs](pointers.md)
- [Speech](speech.md)
- [État d’entrée](input-state.md)
