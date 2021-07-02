---
title: Ajout d’une interactivité proche
description: Documentation sur l’interaction proche dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, Near Interaction,
ms.openlocfilehash: 241425f0c158d684cad6dad8c88c8d692cbec42f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176874"
---
# <a name="how-to-add-near-interactivity"></a><span data-ttu-id="abf15-104">Ajout d’une interactivité proche</span><span class="sxs-lookup"><span data-stu-id="abf15-104">How to add near interactivity</span></span>

<span data-ttu-id="abf15-105">Les interactions proches se présentent sous la forme de fonctions de contact et de touches.</span><span class="sxs-lookup"><span data-stu-id="abf15-105">Near interactions come in the form of touches and grabs.</span></span> <span data-ttu-id="abf15-106">Les événements tactiles et de manipulation sont déclenchés en tant qu’événements de pointeur par [PokePointer](pointers.md#pokepointer) et [SpherePointer](pointers.md#spherepointer), respectivement.</span><span class="sxs-lookup"><span data-stu-id="abf15-106">Touch and grab events are raised as pointer events by the [PokePointer](pointers.md#pokepointer) and [SpherePointer](pointers.md#spherepointer), respectively.</span></span>

<span data-ttu-id="abf15-107">Trois étapes clés sont requises pour écouter les événements d’entrée tactile et/ou de manipulation sur un GameObject particulier.</span><span class="sxs-lookup"><span data-stu-id="abf15-107">Three key steps are required to listen for touch and/or grab input events on a particular GameObject.</span></span>

1. <span data-ttu-id="abf15-108">Vérifiez que le pointeur approprié est inscrit dans le [profil de configuration MRTK](../../configuration/mixed-reality-configuration-guide.md)principal.</span><span class="sxs-lookup"><span data-stu-id="abf15-108">Ensure the relevant pointer is registered in the main [MRTK Configuration Profile](../../configuration/mixed-reality-configuration-guide.md).</span></span>
1. <span data-ttu-id="abf15-109">Assurez-vous que le GameObject souhaité possède le composant de script de [manipulation](#add-grab-interactions) ou [tactile](#add-touch-interactions) approprié et [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html) .</span><span class="sxs-lookup"><span data-stu-id="abf15-109">Ensure the desired GameObject has the appropriate [grab](#add-grab-interactions) or [touch](#add-touch-interactions) script component and [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html).</span></span>
1. <span data-ttu-id="abf15-110">Implémentez une interface de gestionnaire d’entrée sur un script attaché au GameObject souhaité pour écouter les événements de [manipulation](#grab-code-example) ou [tactile](#touch-code-example) .</span><span class="sxs-lookup"><span data-stu-id="abf15-110">Implement an input handler interface on an attached script to the desired GameObject to listen for the [grab](#grab-code-example) or [touch](#touch-code-example) events.</span></span>

## <a name="add-grab-interactions"></a><span data-ttu-id="abf15-111">Ajouter des interactions de manipulation</span><span class="sxs-lookup"><span data-stu-id="abf15-111">Add grab interactions</span></span>

1. <span data-ttu-id="abf15-112">Assurez-vous qu’un [SpherePointer](pointers.md#spherepointer) est inscrit dans le *Profil du pointeur MRTK*.</span><span class="sxs-lookup"><span data-stu-id="abf15-112">Ensure a [SpherePointer](pointers.md#spherepointer) is registered in the *MRTK Pointer profile*.</span></span>

    <span data-ttu-id="abf15-113">le profil MRTK par défaut et le profil de HoloLens 2 par défaut contiennent déjà un *SpherePointer*.</span><span class="sxs-lookup"><span data-stu-id="abf15-113">The default MRTK profile and the default HoloLens 2 profile already contain a *SpherePointer*.</span></span> <span data-ttu-id="abf15-114">Vous pouvez confirmer qu’un SpherePointer sera créé en sélectionnant le profil de configuration MRTK et en accédant à pointeurs **d’entrée**  >    >  **Options du pointeur**.</span><span class="sxs-lookup"><span data-stu-id="abf15-114">One can confirm a SpherePointer will be created by selecting the MRTK Configuration Profile and navigating to **Input** > **Pointers** > **Pointer Options**.</span></span> <span data-ttu-id="abf15-115">La valeur par défaut `GrabPointer` de Prefab (Assets/MRTK/SDK/features/Prefabs/Pointers) doit être indiquée avec un *type de contrôleur* de la *main*.</span><span class="sxs-lookup"><span data-stu-id="abf15-115">The default `GrabPointer` prefab (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) should be listed with a *Controller Type* of *Articulated Hand*.</span></span> <span data-ttu-id="abf15-116">Un Prefab personnalisé peut être utilisé tant qu’il implémente la [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) classe.</span><span class="sxs-lookup"><span data-stu-id="abf15-116">A custom prefab can be utilized as long as it implements the [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) class.</span></span>

    ![Exemple de profil de pointeur de manipulation](../images/input/Pointers/GrabPointer_MRTKProfile.png)

    <span data-ttu-id="abf15-118">Le pointeur de manipulation par défaut recherche les objets avoisinants dans un cône autour du point de capture pour correspondre à l’interface Hololens 2 par défaut.</span><span class="sxs-lookup"><span data-stu-id="abf15-118">The default grab pointer queries for nearby objects in a cone around the grab point to match the default Hololens 2 interface.</span></span>

    ![Pointeur de manipulation conique](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

1. <span data-ttu-id="abf15-120">Sur le GameObject qui doit être extrait, ajoutez un [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) , ainsi qu’un conflit.</span><span class="sxs-lookup"><span data-stu-id="abf15-120">On the GameObject that should be grabbable, add a [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable), as well as a collider.</span></span>

    <span data-ttu-id="abf15-121">Assurez-vous que la couche du GameObject est sur une couche qui peut être saisie.</span><span class="sxs-lookup"><span data-stu-id="abf15-121">Make sure the layer of the GameObject is on a grabbable layer.</span></span> <span data-ttu-id="abf15-122">Par défaut, toutes les couches, à l’exception de la *détection spatiale* et *ignorent les Raycasts* , sont récupérables.</span><span class="sxs-lookup"><span data-stu-id="abf15-122">By default, all layers except *Spatial Awareness* and *Ignore Raycasts* are grabbable.</span></span> <span data-ttu-id="abf15-123">Consultez les couches qui peuvent être *récupérées* en inspectant les masques de couche de saisie dans votre Prefab *GrabPointer* .</span><span class="sxs-lookup"><span data-stu-id="abf15-123">See which layers are grabbable by inspecting the *Grab Layer Masks* in your *GrabPointer* prefab.</span></span>

1. <span data-ttu-id="abf15-124">Sur le GameObject ou l’un de ses ancêtres, ajoutez un composant script qui implémente l' [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interface.</span><span class="sxs-lookup"><span data-stu-id="abf15-124">On the GameObject or one of its ancestors, add a script component that implements the [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interface.</span></span> <span data-ttu-id="abf15-125">Tout ancêtre de l’objet avec le [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) sera en mesure de recevoir également des événements de pointeur.</span><span class="sxs-lookup"><span data-stu-id="abf15-125">Any ancestor of the object with the [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) will be able to receive pointer events, as well.</span></span>

### <a name="grab-code-example"></a><span data-ttu-id="abf15-126">Exemple de code de manipulation</span><span class="sxs-lookup"><span data-stu-id="abf15-126">Grab code example</span></span>

<span data-ttu-id="abf15-127">Vous trouverez ci-dessous un script qui s’imprimera si un événement est une pression tactile ou une capture.</span><span class="sxs-lookup"><span data-stu-id="abf15-127">Below is a script that will print if an event is a touch or grab.</span></span> <span data-ttu-id="abf15-128">Dans la fonction d’interface *IMixedRealityPointerHandler* appropriée, vous pouvez examiner le type de pointeur qui déclenche cet événement via le [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData) .</span><span class="sxs-lookup"><span data-stu-id="abf15-128">In the relevant *IMixedRealityPointerHandler* interface function, one can look at the type of pointer that triggers that event via the [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData).</span></span> <span data-ttu-id="abf15-129">Si le pointeur est un *SpherePointer*, l’interaction est une capture.</span><span class="sxs-lookup"><span data-stu-id="abf15-129">If the pointer is a *SpherePointer*, the interaction is a grab.</span></span>

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

## <a name="add-touch-interactions"></a><span data-ttu-id="abf15-130">Ajouter des interactions tactiles</span><span class="sxs-lookup"><span data-stu-id="abf15-130">Add touch interactions</span></span>

<span data-ttu-id="abf15-131">Le processus d’ajout d’interactions tactiles sur des éléments UnityUI est différent de celui des GameObjects 3D de vanille.</span><span class="sxs-lookup"><span data-stu-id="abf15-131">The process for adding touch interactions on UnityUI elements is different than for vanilla 3D GameObjects.</span></span> <span data-ttu-id="abf15-132">Vous pouvez passer à la section suivante, *interface utilisateur Unity*, pour l’activation des composants de l’interface utilisateur Unity.</span><span class="sxs-lookup"><span data-stu-id="abf15-132">You can skip to the following section, *Unity UI*, for enabling Unity UI components.</span></span>

<span data-ttu-id="abf15-133">Toutefois, pour **les deux** types d’éléments d’expérience utilisateur, assurez-vous qu’un [PokePointer](pointers.md#pokepointer) est inscrit dans le *profil de pointeur MRTK*.</span><span class="sxs-lookup"><span data-stu-id="abf15-133">For **both** types of UX elements though, ensure a [PokePointer](pointers.md#pokepointer) is registered in the *MRTK Pointer profile*.</span></span>

<span data-ttu-id="abf15-134">le profil MRTK par défaut et le profil de HoloLens 2 par défaut contiennent déjà un *PokePointer*.</span><span class="sxs-lookup"><span data-stu-id="abf15-134">The default MRTK profile and the default HoloLens 2 profile already contain a *PokePointer*.</span></span> <span data-ttu-id="abf15-135">Vous pouvez confirmer qu’un PokePointer sera créé en sélectionnant le profil de configuration MRTK et en accèdent aux  >  Options du pointeur **pointeurs** d’entrée  >  .</span><span class="sxs-lookup"><span data-stu-id="abf15-135">One can confirm a PokePointer will be created by selecting the MRTK Configuration Profile and navigate to **Input** > **Pointers** > **Pointer Options**.</span></span> <span data-ttu-id="abf15-136">La valeur par défaut `PokePointer` (ressources/MRTK/Kit de développement logiciel/SDK/features/Prefabs/pointeurs) Prefab doit être indiquée avec un *type de contrôleur* *articulé*.</span><span class="sxs-lookup"><span data-stu-id="abf15-136">The default `PokePointer` (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) prefab should be listed with a *Controller Type* of *Articulated Hand*.</span></span> <span data-ttu-id="abf15-137">Un Prefab personnalisé peut être utilisé tant qu’il implémente la [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) classe.</span><span class="sxs-lookup"><span data-stu-id="abf15-137">A custom prefab can be utilized as long as it implements the [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) class.</span></span>

![Exemple de profil de pointeur en avant](../images/input/Pointers/PokePointer_MRTKProfile.png)

### <a name="3d-gameobjects"></a><span data-ttu-id="abf15-139">GameObjects 3D</span><span class="sxs-lookup"><span data-stu-id="abf15-139">3D GameObjects</span></span>

<span data-ttu-id="abf15-140">Il existe deux façons d’ajouter des interactions tactiles à des GameObjects 3D, en fonction de si votre objet 3D ne doit avoir qu’un seul plan touchable, ou de s’il doit être touchable en fonction de l’ensemble de son conflit.</span><span class="sxs-lookup"><span data-stu-id="abf15-140">There are two different ways of adding touch interactions to 3D GameObjects, depending on if your 3d object should only have a single touchable plane, or of if it should be touchable based on its entire collider.</span></span>
<span data-ttu-id="abf15-141">La première consiste généralement à utiliser des objets avec BoxColliders, où il est souhaitable de n’avoir qu’une seule face de la réaction du conflit à des événements tactiles.</span><span class="sxs-lookup"><span data-stu-id="abf15-141">The first way is typically on objects with BoxColliders, where it is desired to only have a single face of the collider react to touch events.</span></span> <span data-ttu-id="abf15-142">L’autre est pour les objets qui doivent être touchable à partir de n’importe quelle direction en fonction de leur collision.</span><span class="sxs-lookup"><span data-stu-id="abf15-142">The other is for objects that need to be touchable from any direction based on their collider.</span></span>

### <a name="single-face-touch"></a><span data-ttu-id="abf15-143">Toucher simple</span><span class="sxs-lookup"><span data-stu-id="abf15-143">Single face touch</span></span>

<span data-ttu-id="abf15-144">Cela est utile pour activer les situations où une seule face doit être touchable.</span><span class="sxs-lookup"><span data-stu-id="abf15-144">This is useful to enable situations where only a single face needs to be touchable.</span></span> <span data-ttu-id="abf15-145">Cette option suppose que l’objet Game possède un BoxCollider.</span><span class="sxs-lookup"><span data-stu-id="abf15-145">This option assumes that the game object has a BoxCollider.</span></span> <span data-ttu-id="abf15-146">Il est possible de l’utiliser avec des objets non BoxColliders, auquel cas les propriétés « Bounds » et « local Center » doivent être définies manuellement pour configurer le plan touchable (par exemple, les limites doivent être définies sur une valeur différente de zéro).</span><span class="sxs-lookup"><span data-stu-id="abf15-146">it's possible to use this with non-BoxCollider objects, in which case the 'Bounds' and 'Local Center' properties much be manually set to configure the touchable plane (i.e. Bounds should be set to a non-zero-zero value).</span></span>

1. <span data-ttu-id="abf15-147">sur le GameObject qui doit être touchable, ajoutez un BoxCollider et un [ `NearInteractionTouchable` ] (xref : Microsoft. MixedReality. Shared Computer Toolkit. Input. NearInteractionTouchable).</span><span class="sxs-lookup"><span data-stu-id="abf15-147">On the GameObject that should be touchable, add a BoxCollider and a [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) component.</span></span>

    1. <span data-ttu-id="abf15-148">définissez les **événements à recevoir** pour *toucher* si vous utilisez [ `IMixedRealityTouchHandler` ] (xref : Microsoft. MixedReality. Shared Computer Toolkit. Input. IMixedRealityTouchHandler) dans votre script de composant ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="abf15-148">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`] (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

    1. <span data-ttu-id="abf15-149">Cliquez sur **corriger les limites** et **Fix Center**</span><span class="sxs-lookup"><span data-stu-id="abf15-149">Click **Fix bounds** and **Fix center**</span></span>

    ![Installation de NearInteractionTouchable](../images/input/Pointers/NearInteractionTouchableSetup.gif)

1. <span data-ttu-id="abf15-151">Sur cet objet ou sur l’un de ses ancêtres, ajoutez un composant script qui implémente le [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span><span class="sxs-lookup"><span data-stu-id="abf15-151">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span></span>
   <span data-ttu-id="abf15-152">interface.</span><span class="sxs-lookup"><span data-stu-id="abf15-152">interface.</span></span> <span data-ttu-id="abf15-153">tout ancêtre de l’objet avec [ `NearInteractionTouchable` ] (xref : Microsoft. MixedReality. Shared Computer Toolkit. Input. NearInteractionTouchable) sera également en mesure de recevoir des événements de pointeur.</span><span class="sxs-lookup"><span data-stu-id="abf15-153">Any ancestor of the object with the [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) will be able to receive pointer events, as well.</span></span>

> [!NOTE]
> <span data-ttu-id="abf15-154">Dans l’affichage scène de l’éditeur avec le gameobject *NearInteractionTouchable* sélectionné, notez le carré et la flèche du contour blanc.</span><span class="sxs-lookup"><span data-stu-id="abf15-154">In the editor scene view with the *NearInteractionTouchable* GameObject selected, notice a white outline square and arrow.</span></span> <span data-ttu-id="abf15-155">La flèche pointe vers l’avant de la touchable.</span><span class="sxs-lookup"><span data-stu-id="abf15-155">The arrow points to the "front" of the touchable.</span></span> <span data-ttu-id="abf15-156">Le conflit est touchable uniquement à partir de cette direction.</span><span class="sxs-lookup"><span data-stu-id="abf15-156">The collidable will only be touchable from that direction.</span></span> <span data-ttu-id="abf15-157">Pour rendre un touchable de collision dans toutes les directions, consultez la section relative à l' [interaction tactile](#arbitrary-collider-touch)de l’interrogation.</span><span class="sxs-lookup"><span data-stu-id="abf15-157">To make a collider touchable from all directions, see the section on [arbitrary collider touch](#arbitrary-collider-touch).</span></span>
> <span data-ttu-id="abf15-158">![NearInteractionTouchable gizmos ](../images/input/Pointers/NearInteractionTouchableGizmos.png)</span><span class="sxs-lookup"><span data-stu-id="abf15-158">![NearInteractionTouchable Gizmos ](../images/input/Pointers/NearInteractionTouchableGizmos.png)</span></span>

### <a name="arbitrary-collider-touch"></a><span data-ttu-id="abf15-159">Toucher arbitraire</span><span class="sxs-lookup"><span data-stu-id="abf15-159">Arbitrary collider touch</span></span>

<span data-ttu-id="abf15-160">Cela est utile pour activer les situations où l’objet de jeu doit être touchable le long de la face entière de son conflit.</span><span class="sxs-lookup"><span data-stu-id="abf15-160">This is useful to enable situations where the game object needs to be touchable along its entire collider face.</span></span> <span data-ttu-id="abf15-161">Par exemple, il peut être utilisé pour activer les interactions tactiles pour un objet avec un SphereCollider, où l’ensemble du conflit doit être touchable.</span><span class="sxs-lookup"><span data-stu-id="abf15-161">For example, this can be used to enable touch interactions for an object with a SphereCollider, where the entire collider needs to be touchable.</span></span>

1. <span data-ttu-id="abf15-162">sur le GameObject qui doit être touchable, ajoutez un conflit et un [ `NearInteractionTouchableVolume` ] (xref : Microsoft. MixedReality. Shared Computer Toolkit. Input. NearInteractionTouchableVolume).</span><span class="sxs-lookup"><span data-stu-id="abf15-162">On the GameObject that should be touchable, add a collider and a [`NearInteractionTouchableVolume`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume) component.</span></span>

    1. <span data-ttu-id="abf15-163">définissez les **événements à recevoir** pour *toucher* si vous utilisez [ `IMixedRealityTouchHandler` ] (xref : Microsoft. MixedReality. Shared Computer Toolkit. Input. IMixedRealityTouchHandler) dans votre script de composant ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="abf15-163">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`] (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

1. <span data-ttu-id="abf15-164">Sur cet objet ou sur l’un de ses ancêtres, ajoutez un composant script qui implémente le [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span><span class="sxs-lookup"><span data-stu-id="abf15-164">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span></span>
   <span data-ttu-id="abf15-165">interface.</span><span class="sxs-lookup"><span data-stu-id="abf15-165">interface.</span></span> <span data-ttu-id="abf15-166">tout ancêtre de l’objet avec [ `NearInteractionTouchable` ] (xref : Microsoft. MixedReality. Shared Computer Toolkit. Input. NearInteractionTouchable) sera également en mesure de recevoir des événements de pointeur.</span><span class="sxs-lookup"><span data-stu-id="abf15-166">Any ancestor of the object with the [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) will be able to receive pointer events, as well.</span></span>

### <a name="unity-ui"></a><span data-ttu-id="abf15-167">Interface utilisateur Unity</span><span class="sxs-lookup"><span data-stu-id="abf15-167">Unity UI</span></span>

1. <span data-ttu-id="abf15-168">Ajoutez/Vérifiez qu’il y a un [canevas UnityUI](https://docs.unity3d.com/Manual/UICanvas.html) dans la scène.</span><span class="sxs-lookup"><span data-stu-id="abf15-168">Add/ensure there is a [UnityUI canvas](https://docs.unity3d.com/Manual/UICanvas.html) in the scene.</span></span>

1. <span data-ttu-id="abf15-169">Sur le GameObject qui doit être touchable, ajoutez un [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) composant.</span><span class="sxs-lookup"><span data-stu-id="abf15-169">On the GameObject that should be touchable, add a [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) component.</span></span>  

    1. <span data-ttu-id="abf15-170">Définissez **événements sur recevoir** pour *toucher* si vous utilisez l' [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface dans votre script de composant ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="abf15-170">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

1. <span data-ttu-id="abf15-171">Sur cet objet ou sur l’un de ses ancêtres, ajoutez un composant script qui implémente l' [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface.</span><span class="sxs-lookup"><span data-stu-id="abf15-171">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface.</span></span> <span data-ttu-id="abf15-172">Tout ancêtre de l’objet avec le [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) sera en mesure de recevoir également des événements de pointeur.</span><span class="sxs-lookup"><span data-stu-id="abf15-172">Any ancestor of the object with the [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) will be able to receive pointer events as well.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="abf15-173">Les objets peuvent ne pas se comporter comme prévu s’ils se trouvent sur des objets de canevas qui se chevauchent.</span><span class="sxs-lookup"><span data-stu-id="abf15-173">Objects may not behave as expected if they are located on overlapping canvas objects.</span></span> <span data-ttu-id="abf15-174">Pour garantir un comportement cohérent, ne faites jamais chevaucher les objets Canvas dans votre scène.</span><span class="sxs-lookup"><span data-stu-id="abf15-174">To ensure consistent behavior, never overlap canvas objects in your scene.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="abf15-175">Sur le `NearInteractionTouchable` composant script, pour les *événements de propriété à recevoir* , il existe deux options : *pointeur* et *toucher*.</span><span class="sxs-lookup"><span data-stu-id="abf15-175">On the `NearInteractionTouchable` script component, for the property *Events to Receive* there are two options: *Pointer* and *Touch*.</span></span> <span data-ttu-id="abf15-176">Définissez les *événements à recevoir* à *pointeur* si vous utilisez l' [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interface et définissez sur *toucher* si vous utilisez l' [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface dans votre script de composant qui répond/gère les événements d’entrée.</span><span class="sxs-lookup"><span data-stu-id="abf15-176">Set *Events to Receive* to *Pointer* if using the [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interface and set to *Touch* if using the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script that responds/handles the input events.</span></span>

#### <a name="touch-code-example"></a><span data-ttu-id="abf15-177">Exemple de code tactile</span><span class="sxs-lookup"><span data-stu-id="abf15-177">Touch code example</span></span>

<span data-ttu-id="abf15-178">Le code ci-dessous illustre un monocomportement qui peut être attaché à un GameObject avec un [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) composant variant et répondre aux événements d’entrée tactile.</span><span class="sxs-lookup"><span data-stu-id="abf15-178">The code below demonstrates a MonoBehaviour that can be attached to a GameObject with a [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) variant component and respond to touch input events.</span></span>

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

## <a name="near-interaction-script-examples"></a><span data-ttu-id="abf15-179">Exemples de scripts near interaction</span><span class="sxs-lookup"><span data-stu-id="abf15-179">Near interaction script examples</span></span>

### <a name="touch-events"></a><span data-ttu-id="abf15-180">Événements tactiles</span><span class="sxs-lookup"><span data-stu-id="abf15-180">Touch events</span></span>

<span data-ttu-id="abf15-181">Cet exemple crée un cube, le rend touchable et modifie la couleur sur Touch.</span><span class="sxs-lookup"><span data-stu-id="abf15-181">This example creates a cube, makes it touchable, and changes color on touch.</span></span>

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

### <a name="grab-events"></a><span data-ttu-id="abf15-182">Événements de manipulation</span><span class="sxs-lookup"><span data-stu-id="abf15-182">Grab events</span></span>

<span data-ttu-id="abf15-183">L’exemple ci-dessous montre comment faire glisser un GameObject.</span><span class="sxs-lookup"><span data-stu-id="abf15-183">The below example shows how to make a GameObject draggable.</span></span> <span data-ttu-id="abf15-184">Suppose que l’objet de jeu comporte un conflit.</span><span class="sxs-lookup"><span data-stu-id="abf15-184">Assumes that the game object has a collider on it.</span></span>

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

## <a name="useful-apis"></a><span data-ttu-id="abf15-185">API utiles</span><span class="sxs-lookup"><span data-stu-id="abf15-185">Useful APIs</span></span>

* [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable)
* [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable)
* [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI)
* [`NearInteractionTouchableVolume`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume)
* [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
* [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)

## <a name="see-also"></a><span data-ttu-id="abf15-186">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="abf15-186">See also</span></span>

* [<span data-ttu-id="abf15-187">Vue d'ensemble des entrées</span><span class="sxs-lookup"><span data-stu-id="abf15-187">Input Overview</span></span>](overview.md)
* [<span data-ttu-id="abf15-188">Pointeurs</span><span class="sxs-lookup"><span data-stu-id="abf15-188">Pointers</span></span>](pointers.md)
* [<span data-ttu-id="abf15-189">Événements d’entrée</span><span class="sxs-lookup"><span data-stu-id="abf15-189">Input Events</span></span>](input-events.md)
