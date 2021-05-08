---
title: HowToAddNearInteractivity
description: Documentation sur l’interaction proche dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, Near interaction,
ms.openlocfilehash: fc6fbb33e5a8e9aa6930f56f292f8ded51c53ff0
ms.sourcegitcommit: 0c717ed0043c7a65e2caf1452eb0f49059cdf154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108644845"
---
# <a name="how-to-add-near-interaction-in-mrtk"></a>Ajout d’une interaction near dans MRTK

Les interactions proches se présentent sous la forme de fonctions de contact et de touches. Les événements tactiles et de manipulation sont déclenchés en tant qu’événements de pointeur par [PokePointer](pointers.md#pokepointer) et [SpherePointer](pointers.md#spherepointer), respectivement.

Trois étapes clés sont requises pour écouter les événements d’entrée tactile et/ou de manipulation sur un GameObject particulier.

1. Vérifiez que le pointeur approprié est inscrit dans le [profil de configuration MRTK](../../configuration/mixed-reality-configuration-guide.md)principal.
1. Assurez-vous que le GameObject souhaité possède le composant de script de [manipulation](#add-grab-interactions) ou [tactile](#add-touch-interactions) approprié et [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html) .
1. Implémentez une interface de gestionnaire d’entrée sur un script attaché au GameObject souhaité pour écouter les événements de [manipulation](#grab-code-example) ou [tactile](#touch-code-example) .

## <a name="add-grab-interactions"></a>Ajouter des interactions de manipulation

1. Assurez-vous qu’un [SpherePointer](pointers.md#spherepointer) est inscrit dans le *Profil du pointeur MRTK*.

    Le profil MRTK par défaut et le profil HoloLens 2 par défaut contiennent déjà un *SpherePointer*. Vous pouvez confirmer qu’un SpherePointer sera créé en sélectionnant le profil de configuration MRTK et en accédant à pointeurs **d’entrée**  >    >  **Options du pointeur**. La valeur par défaut `GrabPointer` de Prefab (Assets/MRTK/SDK/features/Prefabs/Pointers) doit être indiquée avec un *type de contrôleur* de la *main*. Un Prefab personnalisé peut être utilisé tant qu’il implémente la [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) classe.

    ![Exemple de profil de pointeur de manipulation](../images/input/Pointers/GrabPointer_MRTKProfile.png)

    Le pointeur de manipulation par défaut recherche les objets avoisinants dans un cône autour du point de capture pour correspondre à l’interface Hololens 2 par défaut.

    ![Pointeur de manipulation conique](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

1. Sur le GameObject qui doit être extrait, ajoutez un [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) , ainsi qu’un conflit.

    Assurez-vous que la couche du GameObject est sur une couche qui peut être saisie. Par défaut, toutes les couches, à l’exception de la *détection spatiale* et *ignorent les Raycasts* , sont récupérables. Consultez les couches qui peuvent être *récupérées* en inspectant les masques de couche de saisie dans votre Prefab *GrabPointer* .

1. Sur le GameObject ou l’un de ses ancêtres, ajoutez un composant script qui implémente l' [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interface. Tout ancêtre de l’objet avec le [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) sera en mesure de recevoir également des événements de pointeur.

### <a name="grab-code-example"></a>Exemple de code de manipulation

Vous trouverez ci-dessous un script qui s’imprimera si un événement est une pression tactile ou une capture. Dans la fonction d’interface *IMixedRealityPointerHandler* appropriée, vous pouvez examiner le type de pointeur qui déclenche cet événement via le [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData) . Si le pointeur est un *SpherePointer*, l’interaction est une capture.

```c#
public class PrintPointerEvents : MonoBehaviour, IMixedRealityPointerHandler
{
    public void OnPointerDown(MixedRealityPointerEventData eventData)
    {
        if (eventData.Pointer is SpherePointer)
        {
            Debug.Log($"Grab start from {eventData.Pointer.PointerName}");
        }
        if (eventData.Pointer is PokePointer)
        {
            Debug.Log($"Touch start from {eventData.Pointer.PointerName}");
        }
    }

    public void OnPointerClicked(MixedRealityPointerEventData eventData) {}
    public void OnPointerDragged(MixedRealityPointerEventData eventData) {}
    public void OnPointerUp(MixedRealityPointerEventData eventData) {}
}
```

## <a name="add-touch-interactions"></a>Ajouter des interactions tactiles

Le processus d’ajout d’interactions tactiles sur des éléments UnityUI est différent de celui des GameObjects 3D de vanille. Vous pouvez passer à la section suivante, *interface utilisateur Unity*, pour l’activation des composants de l’interface utilisateur Unity.

Toutefois, pour **les deux** types d’éléments d’expérience utilisateur, assurez-vous qu’un [PokePointer](pointers.md#pokepointer) est inscrit dans le *profil de pointeur MRTK*.

Le profil MRTK par défaut et le profil HoloLens 2 par défaut contiennent déjà un *PokePointer*. Vous pouvez confirmer qu’un PokePointer sera créé en sélectionnant le profil de configuration MRTK et en accèdent aux  >  Options du pointeur **pointeurs** d’entrée  >  . La valeur par défaut `PokePointer` (ressources/MRTK/Kit de développement logiciel/SDK/features/Prefabs/pointeurs) Prefab doit être indiquée avec un *type de contrôleur* *articulé*. Un Prefab personnalisé peut être utilisé tant qu’il implémente la [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) classe.

![Exemple de profil de pointeur en avant](../images/input/Pointers/PokePointer_MRTKProfile.png)

### <a name="3d-gameobjects"></a>GameObjects 3D

Il existe deux façons d’ajouter des interactions tactiles à des GameObjects 3D, en fonction de si votre objet 3D ne doit avoir qu’un seul plan touchable, ou de s’il doit être touchable en fonction de l’ensemble de son conflit.
La première consiste généralement à utiliser des objets avec BoxColliders, où il est souhaitable de n’avoir qu’une seule face de la réaction du conflit à des événements tactiles. L’autre est pour les objets qui doivent être touchable à partir de n’importe quelle direction en fonction de leur collision.

### <a name="single-face-touch"></a>Toucher simple

Cela est utile pour activer les situations où une seule face doit être touchable. Cette option suppose que l’objet Game possède un BoxCollider. Il est possible de l’utiliser avec des objets non BoxColliders, auquel cas les propriétés « Bounds » et « local Center » doivent être définies manuellement pour configurer le plan touchable (par exemple, les limites doivent être définies sur une valeur différente de zéro).

1. Sur le GameObject qui doit être touchable, ajoutez un BoxCollider et un `NearInteractionTouchable` composant [] (XREF : Microsoft. MixedReality. Toolkit. Input. NearInteractionTouchable).

    1. Définissez **événements sur recevoir** pour *toucher* si vous utilisez l' `IMixedRealityTouchHandler` interface [] (XREF : Microsoft. MixedReality. Toolkit. Input. IMixedRealityTouchHandler) dans votre script de composant ci-dessous.

    1. Cliquez sur **corriger les limites** et **Fix Center**

    ![Installation de NearInteractionTouchable](../images/input/Pointers/NearInteractionTouchableSetup.gif)

1. Sur cet objet ou sur l’un de ses ancêtres, ajoutez un composant script qui implémente le [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
   interface. Tout ancêtre de l’objet avec [ `NearInteractionTouchable` ] (XREF : Microsoft. MixedReality. Toolkit. Input. NearInteractionTouchable) pourra également recevoir des événements de pointeur.

> [!NOTE]
> Dans l’affichage scène de l’éditeur avec le gameobject *NearInteractionTouchable* sélectionné, notez le carré et la flèche du contour blanc. La flèche pointe vers l’avant de la touchable. Le conflit est touchable uniquement à partir de cette direction. Pour rendre un touchable de collision dans toutes les directions, consultez la section relative à l' [interaction tactile](#arbitrary-collider-touch)de l’interrogation.
> ![NearInteractionTouchable gizmos ](../images/input/Pointers/NearInteractionTouchableGizmos.png)

### <a name="arbitrary-collider-touch"></a>Toucher arbitraire

Cela est utile pour activer les situations où l’objet de jeu doit être touchable le long de la face entière de son conflit. Par exemple, il peut être utilisé pour activer les interactions tactiles pour un objet avec un SphereCollider, où l’ensemble du conflit doit être touchable.

1. Sur le GameObject qui doit être touchable, ajoutez un conflit et un composant [ `NearInteractionTouchableVolume` ] (XREF : Microsoft. MixedReality. Toolkit. Input. NearInteractionTouchableVolume).

    1. Définissez **événements sur recevoir** pour *toucher* si vous utilisez l' `IMixedRealityTouchHandler` interface [] (XREF : Microsoft. MixedReality. Toolkit. Input. IMixedRealityTouchHandler) dans votre script de composant ci-dessous.

1. Sur cet objet ou sur l’un de ses ancêtres, ajoutez un composant script qui implémente le [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
   interface. Tout ancêtre de l’objet avec [ `NearInteractionTouchable` ] (XREF : Microsoft. MixedReality. Toolkit. Input. NearInteractionTouchable) pourra également recevoir des événements de pointeur.

### <a name="unity-ui"></a>Interface utilisateur Unity

1. Ajoutez/Vérifiez qu’il y a un [canevas UnityUI](https://docs.unity3d.com/Manual/UICanvas.html) dans la scène.

1. Sur le GameObject qui doit être touchable, ajoutez un [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) composant.  

    1. Définissez **événements sur recevoir** pour *toucher* si vous utilisez l' [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface dans votre script de composant ci-dessous.

1. Sur cet objet ou sur l’un de ses ancêtres, ajoutez un composant script qui implémente l' [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface. Tout ancêtre de l’objet avec le [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) sera en mesure de recevoir également des événements de pointeur.

> [!IMPORTANT]
> Les objets peuvent ne pas se comporter comme prévu s’ils se trouvent sur des objets de canevas qui se chevauchent. Pour garantir un comportement cohérent, ne faites jamais chevaucher les objets Canvas dans votre scène.

> [!IMPORTANT]
> Sur le `NearInteractionTouchable` composant script, pour les *événements de propriété à recevoir* , il existe deux options : *pointeur* et *toucher*. Définissez les *événements à recevoir* à *pointeur* si vous utilisez l' [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interface et définissez sur *toucher* si vous utilisez l' [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface dans votre script de composant qui répond/gère les événements d’entrée.

#### <a name="touch-code-example"></a>Exemple de code tactile

Le code ci-dessous illustre un monocomportement qui peut être attaché à un GameObject avec un [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) composant variant et répondre aux événements d’entrée tactile.

```c#
public class TouchEventsExample : MonoBehaviour, IMixedRealityTouchHandler
{
    public void OnTouchStarted(HandTrackingInputEventData eventData)
    {
        string ptrName = eventData.Pointer.PointerName;
        Debug.Log($"Touch started from {ptrName}");
    }
    public void OnTouchCompleted(HandTrackingInputEventData eventData) {}
    public void OnTouchUpdated(HandTrackingInputEventData eventData) { }
}
```

## <a name="near-interaction-script-examples"></a>Exemples de scripts near interaction

### <a name="touch-events"></a>Événements tactiles

Cet exemple crée un cube, le rend touchable et modifie la couleur sur Touch.

```c#
public static void MakeChangeColorOnTouch(GameObject target)
{
    // Add and configure the touchable
    var touchable = target.AddComponent<NearInteractionTouchableVolume>();
    touchable.EventsToReceive = TouchableEventType.Pointer;

    var material = target.GetComponent<Renderer>().material;
    // Change color on pointer down and up
    var pointerHandler = target.AddComponent<PointerHandler>();
    pointerHandler.OnPointerDown.AddListener((e) => material.color = Color.green);
    pointerHandler.OnPointerUp.AddListener((e) => material.color = Color.magenta);
}
```

### <a name="grab-events"></a>Événements de manipulation

L’exemple ci-dessous montre comment faire glisser un GameObject. Suppose que l’objet de jeu comporte un conflit.

```c#
public static void MakeNearDraggable(GameObject target)
{
    // Instantiate and add grabbable
    target.AddComponent<NearInteractionGrabbable>();

    // Add ability to drag by re-parenting to pointer object on pointer down
    var pointerHandler = target.AddComponent<PointerHandler>();
    pointerHandler.OnPointerDown.AddListener((e) =>
    {
        if (e.Pointer is SpherePointer)
        {
            target.transform.parent = ((SpherePointer)(e.Pointer)).transform;
        }
    });
    pointerHandler.OnPointerUp.AddListener((e) =>
    {
        if (e.Pointer is SpherePointer)
        {
            target.transform.parent = null;
        }
    });
}
```

## <a name="useful-apis"></a>API utiles

* [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable)
* [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable)
* [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI)
* [`NearInteractionTouchableVolume`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume)
* [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
* [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)

## <a name="see-also"></a>Voir aussi

* [Vue d'ensemble des entrées](overview.md)
* [Pointeurs](pointers.md)
* [Événements d’entrée](input-events.md)
