---
title: Événements d’entrée
description: Documentation de InputEvents dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, événements,
ms.openlocfilehash: 450c6dbbed8fc9bbb1a648b7a22f0de66747cbaf
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145227"
---
# <a name="input-events"></a><span data-ttu-id="40ca4-104">Événements d’entrée</span><span class="sxs-lookup"><span data-stu-id="40ca4-104">Input events</span></span>

<span data-ttu-id="40ca4-105">La liste ci-dessous présente toutes les interfaces d’événement d’entrée disponibles à implémenter par un composant monocomportement personnalisé.</span><span class="sxs-lookup"><span data-stu-id="40ca4-105">The list below outlines all available input event interfaces to be implemented by a custom MonoBehaviour component.</span></span> <span data-ttu-id="40ca4-106">Ces interfaces sont appelées par le système d’entrée MRTK pour gérer la logique d’application personnalisée en fonction des interactions entre les utilisateurs et les entrées.</span><span class="sxs-lookup"><span data-stu-id="40ca4-106">These interfaces will be called by the MRTK input system to handle custom app logic based on user input interactions.</span></span> <span data-ttu-id="40ca4-107">Les [événements d’entrée de pointeur](pointers.md#pointer-event-interfaces) sont traités légèrement différemment des types d’événements d’entrée standard ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="40ca4-107">[Pointer input events](pointers.md#pointer-event-interfaces) are handled slightly differently than the standard input event types below.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="40ca4-108">Par défaut, un script reçoit des événements d’entrée uniquement s’il s’agit du GameObject en focus par un pointeur ou un parent d’un GameObject dans le focus.</span><span class="sxs-lookup"><span data-stu-id="40ca4-108">By default, a script will receive input events only if it is the GameObject in focus by a pointer or parent of a GameObject in focus.</span></span>

| <span data-ttu-id="40ca4-109">Handler</span><span class="sxs-lookup"><span data-stu-id="40ca4-109">Handler</span></span> | <span data-ttu-id="40ca4-110">Événements</span><span class="sxs-lookup"><span data-stu-id="40ca4-110">Events</span></span> | <span data-ttu-id="40ca4-111">Description</span><span class="sxs-lookup"><span data-stu-id="40ca4-111">Description</span></span> |
| --- | :---: | --- |
| [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | <span data-ttu-id="40ca4-112">Source détectée/perdue</span><span class="sxs-lookup"><span data-stu-id="40ca4-112">Source Detected / Lost</span></span> | <span data-ttu-id="40ca4-113">Déclenché lorsqu’une source d’entrée est détectée/perdue, par exemple lorsqu’une main articulée est détectée ou perdue.</span><span class="sxs-lookup"><span data-stu-id="40ca4-113">Raised when an input source is detected/lost, like when an articulated hand is detected or lost track of.</span></span> |
| [`IMixedRealitySourcePoseHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourcePoseHandler) | <span data-ttu-id="40ca4-114">Modification de la source</span><span class="sxs-lookup"><span data-stu-id="40ca4-114">Source Pose Changed</span></span> | <span data-ttu-id="40ca4-115">Levée sur les modifications de la source.</span><span class="sxs-lookup"><span data-stu-id="40ca4-115">Raised on source pose changes.</span></span> <span data-ttu-id="40ca4-116">La source pose représente la pose générale de la source d’entrée.</span><span class="sxs-lookup"><span data-stu-id="40ca4-116">The source pose represents the general pose of the input source.</span></span> <span data-ttu-id="40ca4-117">Vous pouvez obtenir des poses spécifiques, comme la poignée ou le pointeur dans un contrôleur de six DDL, à l’aide de `IMixedRealityInputHandler<MixedRealityPose>` .</span><span class="sxs-lookup"><span data-stu-id="40ca4-117">Specific poses, like the grip or pointer pose in a six DOF controller, can be obtained via `IMixedRealityInputHandler<MixedRealityPose>`.</span></span> |
| [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | <span data-ttu-id="40ca4-118">Entrée vers le haut/haut</span><span class="sxs-lookup"><span data-stu-id="40ca4-118">Input Down / Up</span></span> | <span data-ttu-id="40ca4-119">Déclenché sur les modifications apportées aux entrées binaires telles que les boutons.</span><span class="sxs-lookup"><span data-stu-id="40ca4-119">Raised on changes to binary inputs like buttons.</span></span> |
| [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | <span data-ttu-id="40ca4-120">Entrée modifiée</span><span class="sxs-lookup"><span data-stu-id="40ca4-120">Input Changed</span></span> | <span data-ttu-id="40ca4-121">Déclenché lors des modifications apportées aux entrées du type donné.</span><span class="sxs-lookup"><span data-stu-id="40ca4-121">Raised on changes to inputs of the given type.</span></span> <span data-ttu-id="40ca4-122">**T** peut prendre les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="40ca4-122">**T** can take the following values:</span></span> <br/> <span data-ttu-id="40ca4-123">- *float* (retourne le déclencheur analogique)</span><span class="sxs-lookup"><span data-stu-id="40ca4-123">- *float* (e.g returns analog trigger)</span></span><br/> <span data-ttu-id="40ca4-124">- *Vector2* (par exemple, retourne la direction du joystick)</span><span class="sxs-lookup"><span data-stu-id="40ca4-124">- *Vector2* (e.g returns gamepad thumbstick direction)</span></span> <br/> <span data-ttu-id="40ca4-125">- *Vector3* (par exemple, retour de la position de l’appareil suivi)</span><span class="sxs-lookup"><span data-stu-id="40ca4-125">- *Vector3* (e.g return position of tracked device)</span></span> <br/> <span data-ttu-id="40ca4-126">- *Quaternion* (par exemple, retourne l’orientation de l’appareil suivi)</span><span class="sxs-lookup"><span data-stu-id="40ca4-126">- *Quaternion* (e.g returns orientation of tracked device)</span></span><br/> <span data-ttu-id="40ca4-127">- [MixedRealityPose](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) (par exemple, retourne un appareil entièrement suivi)</span><span class="sxs-lookup"><span data-stu-id="40ca4-127">- [MixedRealityPose](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) (e.g. returns fully tracked device)</span></span> |
| [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) | <span data-ttu-id="40ca4-128">Mot clé Speech reconnu</span><span class="sxs-lookup"><span data-stu-id="40ca4-128">Speech Keyword Recognized</span></span> | <span data-ttu-id="40ca4-129">Déclenché lors de la reconnaissance de l’un des mots clés configurés dans le *profil de commandes vocales*.</span><span class="sxs-lookup"><span data-stu-id="40ca4-129">Raised on recognition of one of the keywords configured in the *Speech Commands Profile*.</span></span> |
| [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) | <span data-ttu-id="40ca4-130">Dictation</span><span class="sxs-lookup"><span data-stu-id="40ca4-130">Dictation</span></span><br/> <span data-ttu-id="40ca4-131">Hypothèse</span><span class="sxs-lookup"><span data-stu-id="40ca4-131">Hypothesis</span></span> <br/> <span data-ttu-id="40ca4-132">Résultat</span><span class="sxs-lookup"><span data-stu-id="40ca4-132">Result</span></span> <br/> <span data-ttu-id="40ca4-133">Terminé</span><span class="sxs-lookup"><span data-stu-id="40ca4-133">Complete</span></span> <br/> <span data-ttu-id="40ca4-134">Erreur</span><span class="sxs-lookup"><span data-stu-id="40ca4-134">Error</span></span> | <span data-ttu-id="40ca4-135">Déclenché par les systèmes de dictée pour signaler les résultats d’une session de dictée.</span><span class="sxs-lookup"><span data-stu-id="40ca4-135">Raised by dictation systems to report the results of a dictation session.</span></span> |
| [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) | <span data-ttu-id="40ca4-136">Événements de mouvement sur :</span><span class="sxs-lookup"><span data-stu-id="40ca4-136">Gesture events on:</span></span> <br/> <span data-ttu-id="40ca4-137">Démarré</span><span class="sxs-lookup"><span data-stu-id="40ca4-137">Started</span></span> <br/> <span data-ttu-id="40ca4-138">Mis à jour</span><span class="sxs-lookup"><span data-stu-id="40ca4-138">Updated</span></span> <br/> <span data-ttu-id="40ca4-139">Effectué</span><span class="sxs-lookup"><span data-stu-id="40ca4-139">Completed</span></span> <br/> <span data-ttu-id="40ca4-140">Opération annulée</span><span class="sxs-lookup"><span data-stu-id="40ca4-140">Canceled</span></span> | <span data-ttu-id="40ca4-141">Déclenché lors de la détection de mouvement.</span><span class="sxs-lookup"><span data-stu-id="40ca4-141">Raised on gesture detection.</span></span> |
| [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | <span data-ttu-id="40ca4-142">Mouvement mis à jour/terminé</span><span class="sxs-lookup"><span data-stu-id="40ca4-142">Gesture Updated / Completed</span></span> | <span data-ttu-id="40ca4-143">Déclenché sur la détection des mouvements contenant des données supplémentaires du type donné.</span><span class="sxs-lookup"><span data-stu-id="40ca4-143">Raised on detection of gestures containing additional data of the given type.</span></span> <span data-ttu-id="40ca4-144">Pour plus d’informations sur les valeurs possibles pour **T**, consultez [**événements de mouvement**](gestures.md#gesture-events) .</span><span class="sxs-lookup"><span data-stu-id="40ca4-144">See [**gesture events**](gestures.md#gesture-events) for details on possible values for **T**.</span></span> |
| [`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) | <span data-ttu-id="40ca4-145">Jointures manuelles mises à jour</span><span class="sxs-lookup"><span data-stu-id="40ca4-145">Hand Joints Updated</span></span> | <span data-ttu-id="40ca4-146">Levées par les contrôleurs de main articulés lorsque les joints à la main sont mis à jour.</span><span class="sxs-lookup"><span data-stu-id="40ca4-146">Raised by articulated hand controllers when hand joints are updated.</span></span> |
| [`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) | <span data-ttu-id="40ca4-147">Maille manuelle mise à jour</span><span class="sxs-lookup"><span data-stu-id="40ca4-147">Hand Mesh Updated</span></span> | <span data-ttu-id="40ca4-148">Déclenché par les contrôleurs de main articulés lorsqu’un maillage à la main est mis à jour.</span><span class="sxs-lookup"><span data-stu-id="40ca4-148">Raised by articulated hand controllers when a hand mesh is updated.</span></span> |
| [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) | <span data-ttu-id="40ca4-149">Action démarrée/terminée</span><span class="sxs-lookup"><span data-stu-id="40ca4-149">Action Started / Ended</span></span> | <span data-ttu-id="40ca4-150">Raise pour indiquer le début et la fin de l’action pour les entrées mappées à des actions.</span><span class="sxs-lookup"><span data-stu-id="40ca4-150">Raise to indicate action start and end for inputs mapped to actions.</span></span> |

## <a name="input-events-in-action"></a><span data-ttu-id="40ca4-151">Événements d’entrée en action</span><span class="sxs-lookup"><span data-stu-id="40ca4-151">Input events in action</span></span>

<span data-ttu-id="40ca4-152">Au niveau du script, les événements d’entrée peuvent être consommés en implémentant l’une des interfaces de gestionnaire d’événements indiquées dans le tableau ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="40ca4-152">At the script level, input events can be consumed by implementing one of the event handler interfaces shown in the table above.</span></span> <span data-ttu-id="40ca4-153">Lorsqu’un événement d’entrée se déclenche via une intervention de l’utilisateur, les éléments suivants ont lieu :</span><span class="sxs-lookup"><span data-stu-id="40ca4-153">When an input event fires via a user interaction, the following takes place:</span></span>

1. <span data-ttu-id="40ca4-154">Le système d’entrée MRTK reconnaît qu’un événement d’entrée s’est produit.</span><span class="sxs-lookup"><span data-stu-id="40ca4-154">The MRTK input system recognizes that an input event has occurred.</span></span>
1. <span data-ttu-id="40ca4-155">Le système d’entrée MRTK déclenche la fonction d’interface appropriée de l’événement d’entrée à tous les [gestionnaires d’entrée globaux inscrits](#register-for-global-input-events) .</span><span class="sxs-lookup"><span data-stu-id="40ca4-155">The MRTK input system fires the relevant interface function of the input event to all [registered global input handlers](#register-for-global-input-events)</span></span>
1. <span data-ttu-id="40ca4-156">Pour chaque pointeur actif inscrit avec le système d’entrée :</span><span class="sxs-lookup"><span data-stu-id="40ca4-156">For every active pointer registered with the input system:</span></span>
    1. <span data-ttu-id="40ca4-157">Le système d’entrée détermine quel GameObject est en focus pour le pointeur actuel.</span><span class="sxs-lookup"><span data-stu-id="40ca4-157">The input system determines which GameObject is in focus for the current pointer.</span></span>
    1. <span data-ttu-id="40ca4-158">Le système d’entrée utilise le [système d’événements Unity](https://docs.unity3d.com/Manual/EventSystem.html) pour déclencher la fonction d’interface appropriée pour tous les composants correspondants sur le gameobject ciblé.</span><span class="sxs-lookup"><span data-stu-id="40ca4-158">The input system utilizes [Unity's event system](https://docs.unity3d.com/Manual/EventSystem.html) to fire the relevant interface function for all matching components on the focused GameObject.</span></span>
    1. <span data-ttu-id="40ca4-159">Si, à un moment donné, un événement d’entrée a été [marqué comme étant utilisé](#how-to-stop-input-events), le processus se termine et aucun autre GameObjects ne reçoit les rappels.</span><span class="sxs-lookup"><span data-stu-id="40ca4-159">If at any point an input event has been [marked as used](#how-to-stop-input-events), the process will end and no further GameObjects will receive callbacks.</span></span>
        - <span data-ttu-id="40ca4-160">Exemple : les composants qui implémentent l’interface sont [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) recherchés lorsqu’une commande vocale est reconnue.</span><span class="sxs-lookup"><span data-stu-id="40ca4-160">Example: Components implementing the interface [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) will be searched for when a speech command is recognized.</span></span>
        - <span data-ttu-id="40ca4-161">Remarque : le système d’événements Unity se propage pour rechercher le GameObject parent si aucun composant correspondant à l’interface souhaitée n’est trouvé sur le GameObject actuel.</span><span class="sxs-lookup"><span data-stu-id="40ca4-161">Note: The Unity event system will bubble up to search the parent GameObject if no components matching the desired interface are found on the current GameObject.</span></span>
1. <span data-ttu-id="40ca4-162">Si aucun gestionnaire d’entrée global n’est inscrit et qu’aucun GameObject n’est trouvé avec un composant/une interface correspondant, le système d’entrée appellera chaque gestionnaire d’entrée de secours inscrit</span><span class="sxs-lookup"><span data-stu-id="40ca4-162">If no global input handlers are registered and no GameObject is found with a matching component/interface, then the input system will call each fallback registered input handler</span></span>

> [!NOTE]
> <span data-ttu-id="40ca4-163">Les [événements d’entrée de pointeur](pointers.md#pointer-event-interfaces) sont gérés de manière légèrement différente des interfaces d’événements d’entrée répertoriées ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="40ca4-163">[Pointer input events](pointers.md#pointer-event-interfaces) are handled in a slightly different manner than the input event interfaces listed above.</span></span> <span data-ttu-id="40ca4-164">En particulier, les événements d’entrée de pointeur sont gérés uniquement par le GameObject en focus par le pointeur qui a déclenché l’événement d’entrée, ainsi que tous les gestionnaires d’entrée globaux.</span><span class="sxs-lookup"><span data-stu-id="40ca4-164">In particular, pointer input events are handled only by the GameObject in focus by the pointer that fired the input event - as well as any global input handlers.</span></span> <span data-ttu-id="40ca4-165">Les événements d’entrée standard sont gérés par GameObjects dans le focus pour tous les pointeurs actifs.</span><span class="sxs-lookup"><span data-stu-id="40ca4-165">Regular input events are handled by GameObjects in focus for all active pointers.</span></span>

### <a name="input-event-interface-example"></a><span data-ttu-id="40ca4-166">Exemple d’interface d’événement d’entrée</span><span class="sxs-lookup"><span data-stu-id="40ca4-166">Input event interface example</span></span>

<span data-ttu-id="40ca4-167">Le code ci-dessous illustre l’utilisation de l' [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) interface.</span><span class="sxs-lookup"><span data-stu-id="40ca4-167">The code below demonstrates use of the [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) interface.</span></span> <span data-ttu-id="40ca4-168">Lorsque l’utilisateur dit les mots « plus petit » ou « plus grand » tout en se concentrant sur un GameObject avec cette `ShowHideSpeechHandler` classe, le gameobject se met à l’échelle d’une demi-ou deux fois.</span><span class="sxs-lookup"><span data-stu-id="40ca4-168">When the user says the words "smaller" or "bigger" while focusing on a GameObject with this `ShowHideSpeechHandler` class, the GameObject will scale itself by half or twice as much.</span></span>

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
> <span data-ttu-id="40ca4-169">[`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) les événements d’entrée requièrent que les mots clés souhaités soient préinscrits dans le [profil de commandes vocales MRTK](speech.md).</span><span class="sxs-lookup"><span data-stu-id="40ca4-169">[`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) input events require that the desired keywords are pre-registered in the [MRTK Speech Commands Profile](speech.md).</span></span>

## <a name="register-for-global-input-events"></a><span data-ttu-id="40ca4-170">S’inscrire pour les événements d’entrée globaux</span><span class="sxs-lookup"><span data-stu-id="40ca4-170">Register for global input events</span></span>

<span data-ttu-id="40ca4-171">Pour créer un composant qui écoute les événements d’entrée globaux, en ignorant les GameObject qui peuvent être activés, un composant doit s’inscrire auprès du système d’entrée.</span><span class="sxs-lookup"><span data-stu-id="40ca4-171">To create a component that listens for global input events, disregarding what GameObject may be in focus, a component must register itself with the Input System.</span></span> <span data-ttu-id="40ca4-172">Une fois inscrite, toutes les instances de ce monocomportement recevront des événements d’entrée ainsi que des GameObject (s) de focus et d’autres écouteurs inscrits globaux.</span><span class="sxs-lookup"><span data-stu-id="40ca4-172">Once registered, any instances of this MonoBehaviour will receive input events along with any GameObject(s) currently in focus and other global registered listeners.</span></span>

<span data-ttu-id="40ca4-173">Si un événement d’entrée a été [marqué comme étant utilisé](#how-to-stop-input-events), les gestionnaires enregistrés globaux continuent de recevoir tous les rappels.</span><span class="sxs-lookup"><span data-stu-id="40ca4-173">If an input event has been [marked as used](#how-to-stop-input-events), global registered handlers will still all receive callbacks.</span></span> <span data-ttu-id="40ca4-174">Toutefois, aucun GameObjects ayant le focus ne recevra l’événement.</span><span class="sxs-lookup"><span data-stu-id="40ca4-174">However, no focused GameObjects will receive the event.</span></span>

### <a name="global-input-registration-example"></a><span data-ttu-id="40ca4-175">Exemple d’inscription d’entrée globale</span><span class="sxs-lookup"><span data-stu-id="40ca4-175">Global input registration example</span></span>

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

## <a name="register-for-fallback-input-events"></a><span data-ttu-id="40ca4-176">S’inscrire pour les événements d’entrée de secours</span><span class="sxs-lookup"><span data-stu-id="40ca4-176">Register for fallback input events</span></span>

<span data-ttu-id="40ca4-177">Les gestionnaires d’entrée de secours sont similaires aux gestionnaires d’entrée globaux inscrits, mais ils sont traités en dernier recours pour la gestion des événements d’entrée.</span><span class="sxs-lookup"><span data-stu-id="40ca4-177">Fallback input handlers are similar to registered global input handlers but are treated as a last resort for input event handling.</span></span> <span data-ttu-id="40ca4-178">Si aucun gestionnaire d’entrée global n’a été trouvé et qu’aucun GameObjects n’est activé, les gestionnaires d’entrée de secours seront exploités.</span><span class="sxs-lookup"><span data-stu-id="40ca4-178">Only if no global input handlers were found and no GameObjects are in focus will fallback input handlers be leveraged.</span></span>

### <a name="fallback-input-handler-example"></a><span data-ttu-id="40ca4-179">Exemple de gestionnaire d’entrée de secours</span><span class="sxs-lookup"><span data-stu-id="40ca4-179">Fallback input handler example</span></span>

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

## <a name="how-to-stop-input-events"></a><span data-ttu-id="40ca4-180">Comment arrêter des événements d’entrée</span><span class="sxs-lookup"><span data-stu-id="40ca4-180">How to stop input events</span></span>

<span data-ttu-id="40ca4-181">Chaque interface d’événement d’entrée fournit un [`BaseInputEventData`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputEventData) objet de données en tant que paramètre à chaque fonction de l’interface.</span><span class="sxs-lookup"><span data-stu-id="40ca4-181">Every input event interface provides a [`BaseInputEventData`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputEventData) data object as a parameter to each function on the interface.</span></span> <span data-ttu-id="40ca4-182">Cet objet de données d’événement s’étend du sien de Unity [`AbstractEventData`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.html) .</span><span class="sxs-lookup"><span data-stu-id="40ca4-182">This event data object extends from Unity's own [`AbstractEventData`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.html).</span></span>

<span data-ttu-id="40ca4-183">Afin d’empêcher un événement d’entrée de se propager dans son exécution [comme indiqué](#input-events-in-action), un composant peut appeler [`AbstractEventData.Use()`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.Use.html) pour marquer l’événement comme étant utilisé.</span><span class="sxs-lookup"><span data-stu-id="40ca4-183">In order to stop an input event from propagating through its execution [as outlined](#input-events-in-action), a component can call [`AbstractEventData.Use()`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.Use.html) to mark the event as used.</span></span> <span data-ttu-id="40ca4-184">Cela empêchera tout autre GameObjects de recevoir l’événement d’entrée actuel, à l’exception des gestionnaires d’entrée globaux.</span><span class="sxs-lookup"><span data-stu-id="40ca4-184">This will stop any other GameObjects from receiving the current input event, with the exception of global input handlers.</span></span>

> [!NOTE]
> <span data-ttu-id="40ca4-185">Un composant qui appelle la `Use()` méthode empêche d’autres GameObjects de le recevoir.</span><span class="sxs-lookup"><span data-stu-id="40ca4-185">A component that calls the `Use()` method will stop other GameObjects from receiving it.</span></span> <span data-ttu-id="40ca4-186">Toutefois, d’autres composants sur le GameObject actuel recevront toujours l’événement d’entrée et déclencheront toutes les fonctions d’interface associées.</span><span class="sxs-lookup"><span data-stu-id="40ca4-186">However, other components on the current GameObject will still receive the input event and fire any related interface functions.</span></span>

## <a name="see-also"></a><span data-ttu-id="40ca4-187">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40ca4-187">See also</span></span>

- [<span data-ttu-id="40ca4-188">Pointeurs</span><span class="sxs-lookup"><span data-stu-id="40ca4-188">Pointers</span></span>](pointers.md)
- [<span data-ttu-id="40ca4-189">Speech</span><span class="sxs-lookup"><span data-stu-id="40ca4-189">Speech</span></span>](speech.md)
- [<span data-ttu-id="40ca4-190">État d’entrée</span><span class="sxs-lookup"><span data-stu-id="40ca4-190">Input State</span></span>](input-state.md)
