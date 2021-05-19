---
title: Suivi de la main
description: Documentation sur l’utilisation de HandTracking dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, suivi de la main,
ms.openlocfilehash: 6cd55bc76d9fba42640954bcbf50e62f66454a94
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143354"
---
# <a name="hand-tracking"></a><span data-ttu-id="4ede1-104">Suivi de la main</span><span class="sxs-lookup"><span data-stu-id="4ede1-104">Hand tracking</span></span>

## <a name="hand-tracking-profile"></a><span data-ttu-id="4ede1-105">Profil de suivi de la main</span><span class="sxs-lookup"><span data-stu-id="4ede1-105">Hand tracking profile</span></span>

<span data-ttu-id="4ede1-106">Le _profil de suivi_ de la main se trouve sous le _profil de système d’entrée_.</span><span class="sxs-lookup"><span data-stu-id="4ede1-106">The _Hand Tracking profile_ is found under the _Input System profile_.</span></span> <span data-ttu-id="4ede1-107">Il contient les paramètres de personnalisation de la représentation manuelle.</span><span class="sxs-lookup"><span data-stu-id="4ede1-107">It contains settings for customizing hand representation.</span></span>

<img src="../images/input/HandTrackingProfile.png" width="650px" alt="Hand Tracking Profile" style="display:block;">

## <a name="joint-prefabs"></a><span data-ttu-id="4ede1-108">Prefabs conjointe</span><span class="sxs-lookup"><span data-stu-id="4ede1-108">Joint prefabs</span></span>

<span data-ttu-id="4ede1-109">Les prefabss conjointes sont visualisées à l’aide de prefabs simples.</span><span class="sxs-lookup"><span data-stu-id="4ede1-109">Joint prefabs are visualized using simple prefabs.</span></span> <span data-ttu-id="4ede1-110">Les jointures de _palmier_ et d' _index_ ont une importance particulière et ont leur propre Prefab, tandis que tous les autres articulations partagent le même Prefab.</span><span class="sxs-lookup"><span data-stu-id="4ede1-110">The _Palm_ and _Index Finger_ joints are of special importance and have their own prefab, while all other joints share the same prefab.</span></span>

<span data-ttu-id="4ede1-111">Par défaut, la prefabs jointe à la main sont des primitives géométriques simples.</span><span class="sxs-lookup"><span data-stu-id="4ede1-111">By default the hand joint prefabs are simple geometric primitives.</span></span> <span data-ttu-id="4ede1-112">Vous pouvez les remplacer si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="4ede1-112">These can be replaced if desired.</span></span> <span data-ttu-id="4ede1-113">Si aucun Prefab n’est spécifié, les [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) vides sont créés à la place.</span><span class="sxs-lookup"><span data-stu-id="4ede1-113">If no prefab is specified at all, empty [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) are created instead.</span></span>

> [!WARNING]
> <span data-ttu-id="4ede1-114">Évitez d’utiliser des scripts complexes ou un rendu coûteux dans des prefabss conjointes, car les objets conjoints sont transformés sur chaque image et peuvent avoir un coût de performances significatif.</span><span class="sxs-lookup"><span data-stu-id="4ede1-114">Avoid using complex scripts or expensive rendering in joint prefabs, since joint objects are transformed on every frame and can have significant performance cost!</span></span>

<span data-ttu-id="4ede1-115">Représentation conjointe de la main par défaut</span><span class="sxs-lookup"><span data-stu-id="4ede1-115">Default Hand Joint Representation</span></span> |  <span data-ttu-id="4ede1-116">Étiquettes communes</span><span class="sxs-lookup"><span data-stu-id="4ede1-116">Joint Labels</span></span>
:-------------------------:|:-------------------------:
<img src="../images/input-simulation/ArticulatedHandJoints.png" height="300px" alt="Articulated hand joints"  style="display:inline;">  |  <img src="../images/input-simulation/MRTK_Core_Input_Hands_JointNames.png" height="300px" alt="Input Hand joints"  style="display:inline;">

## <a name="hand-mesh-prefab"></a><span data-ttu-id="4ede1-117">Maille Prefab</span><span class="sxs-lookup"><span data-stu-id="4ede1-117">Hand mesh prefab</span></span>

<span data-ttu-id="4ede1-118">Le maillage manuel est utilisé si les données de maillage entièrement définies sont fournies par l’appareil de suivi de la main.</span><span class="sxs-lookup"><span data-stu-id="4ede1-118">The hand mesh is used if fully defined mesh data is provided by the hand tracking device.</span></span> <span data-ttu-id="4ede1-119">Le maillage qui peut être rendu dans le Prefab est remplacé par les données de l’appareil, de sorte qu’une maille factice comme un cube est suffisante.</span><span class="sxs-lookup"><span data-stu-id="4ede1-119">The mesh renderable in the prefab is replaced by data from the device, so a dummy mesh such as a cube is sufficient.</span></span> <span data-ttu-id="4ede1-120">Le matériau de l’Prefab est utilisé pour le maillage à la main.</span><span class="sxs-lookup"><span data-stu-id="4ede1-120">The material of the prefab is used for the hand mesh.</span></span>

<img src="../images/input-simulation/MRTK_Core_Input_Hands_ArticulatedHandMesh.png" width="350px" alt="Input Hand Mesh"  style="display:block;">

<span data-ttu-id="4ede1-121">L’affichage de maillage manuel peut avoir un impact notable sur les performances. pour cette raison, il peut être entièrement désactivé en désactivant l’option **activer la visualisation de maille manuelle** .</span><span class="sxs-lookup"><span data-stu-id="4ede1-121">Hand mesh display can have a noticeable performance impact, for this reason it can be disabled entirely by unchecking **Enable Hand Mesh Visualization** option.</span></span>

## <a name="hand-visualization-settings"></a><span data-ttu-id="4ede1-122">Paramètres de visualisation manuelle</span><span class="sxs-lookup"><span data-stu-id="4ede1-122">Hand visualization settings</span></span>

<span data-ttu-id="4ede1-123">Les visualisations conjointes à la main et à la main peuvent être désactivées ou activées par le biais du paramètre *modes de visualisation* de la main et des *modes de visualisation conjointe* .</span><span class="sxs-lookup"><span data-stu-id="4ede1-123">The hand mesh and hand joint visualizations can be turned off or on via the *Hand Mesh Visualization Modes* setting and *Hand Joint Visualization Modes* respectively.</span></span> <span data-ttu-id="4ede1-124">Ces paramètres sont spécifiques au mode application, ce qui signifie qu’il est possible d’activer certaines fonctionnalités dans l’éditeur (pour voir les jointures avec la simulation dans l’éditeur, par exemple) tout en désactivant les mêmes fonctionnalités lorsqu’elles sont déployées sur l’appareil (dans les versions Player).</span><span class="sxs-lookup"><span data-stu-id="4ede1-124">These settings are application-mode specific, meaning it is possible to turn on some features while in editor (to see joints with in-editor simulation, for example) while having the same features turned off when deployed to device (in player builds).</span></span>

<span data-ttu-id="4ede1-125">Notez qu’il est généralement recommandé de faire en sorte que la visualisation conjointe manuelle soit activée dans l’éditeur (afin que la simulation dans l’éditeur indique où se trouvent les joints à la main) et que la visualisation conjointe et la visualisation de la maille manuelle soient désactivées dans le lecteur (car elles entraînent une baisse des performances).</span><span class="sxs-lookup"><span data-stu-id="4ede1-125">Note that it's generally recommended to have hand joint visualization turned on in editor (so that in-editor simulation will show where the hand joints are), and to have both hand joint visualization and hand mesh visualization turned off in player (because they incur a performance hit).</span></span>

## <a name="scripting"></a><span data-ttu-id="4ede1-126">Scripts</span><span class="sxs-lookup"><span data-stu-id="4ede1-126">Scripting</span></span>

<span data-ttu-id="4ede1-127">La position et la rotation peuvent être demandées à partir du système d’entrée pour chaque joint individuel sous la forme d’un [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) .</span><span class="sxs-lookup"><span data-stu-id="4ede1-127">Position and rotation can be requested from the input system for each individual hand joint as a [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose).</span></span>

<span data-ttu-id="4ede1-128">Le système permet également d’accéder aux [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) qui suivent les jointures.</span><span class="sxs-lookup"><span data-stu-id="4ede1-128">Alternatively the system allows access to [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) that follow the joints.</span></span> <span data-ttu-id="4ede1-129">Cela peut être utile si un autre GameObject doit suivre une jointure en continu.</span><span class="sxs-lookup"><span data-stu-id="4ede1-129">This can be useful if another GameObject should track a joint continuously.</span></span>

<span data-ttu-id="4ede1-130">Les jointures disponibles sont répertoriées dans l' [`TrackedHandJoint`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedHandJoint) énumération.</span><span class="sxs-lookup"><span data-stu-id="4ede1-130">Available joints are listed in the [`TrackedHandJoint`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedHandJoint) enum.</span></span>

> [!NOTE]
> <span data-ttu-id="4ede1-131">L’objet joint est détruit lorsque le suivi de la main est perdu !</span><span class="sxs-lookup"><span data-stu-id="4ede1-131">Joint object are destroyed when hand tracking is lost!</span></span> <span data-ttu-id="4ede1-132">Assurez-vous que les scripts qui utilisent l’objet joint gèrent le `null` cas correctement pour éviter les erreurs.</span><span class="sxs-lookup"><span data-stu-id="4ede1-132">Make sure that any scripts using the joint object handle the `null` case gracefully to avoid errors!</span></span>

### <a name="accessing-a-given-hand-controller"></a><span data-ttu-id="4ede1-133">Accès à un contrôleur de main donné</span><span class="sxs-lookup"><span data-stu-id="4ede1-133">Accessing a given hand controller</span></span>

<span data-ttu-id="4ede1-134">Un contrôleur de main spécifique est souvent disponible, par exemple lors du traitement des événements d’entrée.</span><span class="sxs-lookup"><span data-stu-id="4ede1-134">A specific hand controller is often available, e.g. when handling input events.</span></span> <span data-ttu-id="4ede1-135">Dans ce cas, les données conjointes peuvent être demandées directement à partir de l’appareil, à l’aide de l' [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) interface.</span><span class="sxs-lookup"><span data-stu-id="4ede1-135">In this case the joint data can be requested directly from the device, using the [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) interface.</span></span>

#### <a name="polling-joint-pose-from-controller"></a><span data-ttu-id="4ede1-136">Attaque d’interrogation du contrôleur</span><span class="sxs-lookup"><span data-stu-id="4ede1-136">Polling joint pose from controller</span></span>

<span data-ttu-id="4ede1-137">La [`TryGetJoint`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand.TryGetJoint*) fonction retourne `false` si l’articulation demandé n’est pas disponible pour une raison quelconque.</span><span class="sxs-lookup"><span data-stu-id="4ede1-137">The [`TryGetJoint`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand.TryGetJoint*) function returns `false` if the requested joint is not available for some reason.</span></span> <span data-ttu-id="4ede1-138">Dans ce cas, le pose obtenu sera [`MixedRealityPose.ZeroIdentity`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose.ZeroIdentity) .</span><span class="sxs-lookup"><span data-stu-id="4ede1-138">In that case the resulting pose will be [`MixedRealityPose.ZeroIdentity`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose.ZeroIdentity).</span></span>

```c#
public void OnSourceDetected(SourceStateEventData eventData)
{
  var hand = eventData.Controller as IMixedRealityHand;
  if (hand != null)
  {
    if (hand.TryGetJoint(TrackedHandJoint.IndexTip, out MixedRealityPose jointPose)
    {
      // ...
    }
  }
}
```

#### <a name="joint-transform-from-hand-visualizer"></a><span data-ttu-id="4ede1-139">Transformation conjointe à partir du visualiseur main</span><span class="sxs-lookup"><span data-stu-id="4ede1-139">Joint transform from hand visualizer</span></span>

<span data-ttu-id="4ede1-140">Les objets conjoints peuvent être demandés à partir du [visualiseur du contrôleur](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController.Visualizer).</span><span class="sxs-lookup"><span data-stu-id="4ede1-140">Joint objects can be requested from the [controller visualizer](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController.Visualizer).</span></span>

```c#
public void OnSourceDetected(SourceStateEventData eventData)
{
  var handVisualizer = eventData.Controller.Visualizer as IMixedRealityHandVisualizer;
  if (handVisualizer != null)
  {
    if (handVisualizer.TryGetJointTransform(TrackedHandJoint.IndexTip, out Transform jointTransform)
    {
      // ...
    }
  }
}
```

### <a name="simplified-joint-data-access"></a><span data-ttu-id="4ede1-141">Accès simplifié aux données jointes</span><span class="sxs-lookup"><span data-stu-id="4ede1-141">Simplified joint data access</span></span>

<span data-ttu-id="4ede1-142">Si aucun contrôleur spécifique n’est donné, les classes utilitaires sont fournies pour faciliter l’accès aux données jointes à la main.</span><span class="sxs-lookup"><span data-stu-id="4ede1-142">If no specific controller is given then utility classes are provided for convenient access to hand joint data.</span></span> <span data-ttu-id="4ede1-143">Ces fonctions demandent des données communes à partir du premier appareil disponible actuellement suivi.</span><span class="sxs-lookup"><span data-stu-id="4ede1-143">These functions request joint data from the first available hand device currently tracked.</span></span>

#### <a name="polling-joint-pose-from-handjointutils"></a><span data-ttu-id="4ede1-144">Interrogation conjointe de HandJointUtils</span><span class="sxs-lookup"><span data-stu-id="4ede1-144">Polling joint pose from HandJointUtils</span></span>

<span data-ttu-id="4ede1-145">[`HandJointUtils`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils) est une classe statique qui interroge le premier appareil main actif.</span><span class="sxs-lookup"><span data-stu-id="4ede1-145">[`HandJointUtils`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils) is a static class that queries the first active hand device.</span></span>

```c#
if (HandJointUtils.TryGetJointPose(TrackedHandJoint.IndexTip, Handedness.Right, out MixedRealityPose pose))
{
    // ...
}
```

#### <a name="joint-transform-from-hand-joint-service"></a><span data-ttu-id="4ede1-146">Transformation conjointe à partir du service joint à la main</span><span class="sxs-lookup"><span data-stu-id="4ede1-146">Joint transform from hand joint service</span></span>

<span data-ttu-id="4ede1-147">[`IMixedRealityHandJointService`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointService) conserve un ensemble persistant de [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) pour le suivi des jointures.</span><span class="sxs-lookup"><span data-stu-id="4ede1-147">[`IMixedRealityHandJointService`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointService) keeps a persistent set of [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) for tracking joints.</span></span>

```c#
var handJointService = CoreServices.GetInputSystemDataProvider<IMixedRealityHandJointService>();
if (handJointService != null)
{
    Transform jointTransform = handJointService.RequestJointTransform(TrackedHandJoint.IndexTip, Handedness.Right);
    // ...
}
```

### <a name="hand-tracking-events"></a><span data-ttu-id="4ede1-148">Événements de suivi de la main</span><span class="sxs-lookup"><span data-stu-id="4ede1-148">Hand tracking events</span></span>

<span data-ttu-id="4ede1-149">Le système d’entrée fournit également des événements, si l’interrogation directe de données à partir de contrôleurs n’est pas souhaitable.</span><span class="sxs-lookup"><span data-stu-id="4ede1-149">The input system provides events as well, if polling data from controllers directly is not desirable.</span></span>

#### <a name="joint-events"></a><span data-ttu-id="4ede1-150">Événements communs</span><span class="sxs-lookup"><span data-stu-id="4ede1-150">Joint events</span></span>

<span data-ttu-id="4ede1-151">[`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) gère les mises à jour des positions de jointure.</span><span class="sxs-lookup"><span data-stu-id="4ede1-151">[`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) handles updates of joint positions.</span></span>

```c#
public class MyHandJointEventHandler : IMixedRealityHandJointHandler
{
    public Handedness myHandedness;

    void IMixedRealityHandJointHandler.OnHandJointsUpdated(InputEventData<IDictionary<TrackedHandJoint, MixedRealityPose>> eventData)
    {
        if (eventData.Handedness == myHandedness)
        {
            if (eventData.InputData.TryGetValue(TrackedHandJoint.IndexTip, out MixedRealityPose pose))
            {
                // ...
            }
        }
    }
}
```

#### <a name="mesh-events"></a><span data-ttu-id="4ede1-152">Événements de maillage</span><span class="sxs-lookup"><span data-stu-id="4ede1-152">Mesh events</span></span>

<span data-ttu-id="4ede1-153">[`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) gère les modifications du maillage articulé.</span><span class="sxs-lookup"><span data-stu-id="4ede1-153">[`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) handles changes of the articulated hand mesh.</span></span>

<span data-ttu-id="4ede1-154">Notez que les maillages de main ne sont pas activés par défaut.</span><span class="sxs-lookup"><span data-stu-id="4ede1-154">Note that hand meshes are not enabled by default.</span></span>

```c#
public class MyHandMeshEventHandler : IMixedRealityHandMeshHandler
{
    public Handedness myHandedness;
    public Mesh myMesh;

    public void OnHandMeshUpdated(InputEventData<HandMeshInfo> eventData)
    {
        if (eventData.Handedness == myHandedness)
        {
            myMesh.vertices = eventData.InputData.vertices;
            myMesh.normals = eventData.InputData.normals;
            myMesh.triangles = eventData.InputData.triangles;

            if (eventData.InputData.uvs != null && eventData.InputData.uvs.Length > 0)
            {
                myMesh.uv = eventData.InputData.uvs;
            }

            // ...
        }
    }
}
```

## <a name="known-issues"></a><span data-ttu-id="4ede1-155">Problèmes connus</span><span class="sxs-lookup"><span data-stu-id="4ede1-155">Known issues</span></span>

### <a name="net-native"></a><span data-ttu-id="4ede1-156">.NET Native</span><span class="sxs-lookup"><span data-stu-id="4ede1-156">.NET Native</span></span>

<span data-ttu-id="4ede1-157">Il existe actuellement un problème connu avec les builds principales à l’aide du backend .NET.</span><span class="sxs-lookup"><span data-stu-id="4ede1-157">There is currently a known issue with Master builds using the .NET backend.</span></span> <span data-ttu-id="4ede1-158">Dans .NET Native, les `IInspectable` pointeurs ne peuvent pas être marshalés du code natif au code managé à l’aide de `Marshal.GetObjectForIUnknown` .</span><span class="sxs-lookup"><span data-stu-id="4ede1-158">In .NET Native, `IInspectable` pointers cannot be marshaled from native to managed code using `Marshal.GetObjectForIUnknown`.</span></span> <span data-ttu-id="4ede1-159">Le MRTK utilise cette valeur pour obtenir le afin de `SpatialCoordinateSystem` recevoir les données de la plateforme et de la main.</span><span class="sxs-lookup"><span data-stu-id="4ede1-159">The MRTK uses this to obtain the `SpatialCoordinateSystem` in order to receive hand and eye data from the platform.</span></span>

<span data-ttu-id="4ede1-160">Nous avons fourni une source de solution de contournement pour résoudre ce problème, dans [le Toolkit de réalité mixte Native référentiel](https://github.com/microsoft/MixedRealityToolkit/tree/master/DotNetNativeWorkaround).</span><span class="sxs-lookup"><span data-stu-id="4ede1-160">We've provided DLL source as a workaround for this issue, in [the native Mixed Reality Toolkit repo](https://github.com/microsoft/MixedRealityToolkit/tree/master/DotNetNativeWorkaround).</span></span> <span data-ttu-id="4ede1-161">Veuillez suivre les instructions du fichier Lisez-moi et copier les fichiers binaires résultants dans un dossier plugins de vos ressources Unity.</span><span class="sxs-lookup"><span data-stu-id="4ede1-161">Please follow the instructions in the README there and copy the resulting binaries into a Plugins folder in your Unity assets.</span></span> <span data-ttu-id="4ede1-162">Après cela, le script WindowsMixedRealityUtilities fourni dans le MRTK permet de résoudre la solution de contournement.</span><span class="sxs-lookup"><span data-stu-id="4ede1-162">After that, the WindowsMixedRealityUtilities script provided in the MRTK will resolve the workaround for you.</span></span>

<span data-ttu-id="4ede1-163">Si vous souhaitez créer votre propre DLL ou inclure cette solution de contournement dans une solution existante, le cœur de la solution de contournement est le suivant :</span><span class="sxs-lookup"><span data-stu-id="4ede1-163">If you want to create your own DLL or include this workaround in an existing one, the core of the workaround is:</span></span>

```c++
extern "C" __declspec(dllexport) void __stdcall MarshalIInspectable(IUnknown* nativePtr, IUnknown** inspectable)
{
    *inspectable = nativePtr;
}
```

<span data-ttu-id="4ede1-164">Et son utilisation dans votre code C# Unity :</span><span class="sxs-lookup"><span data-stu-id="4ede1-164">And its use in your C# Unity code:</span></span>

```c#
[DllImport("DotNetNativeWorkaround.dll", EntryPoint = "MarshalIInspectable")]
private static extern void GetSpatialCoordinateSystem(IntPtr nativePtr, out SpatialCoordinateSystem coordinateSystem);

private static SpatialCoordinateSystem GetSpatialCoordinateSystem(IntPtr nativePtr)
{
    try
    {
        GetSpatialCoordinateSystem(nativePtr, out SpatialCoordinateSystem coordinateSystem);
        return coordinateSystem;
    }
    catch
    {
        UnityEngine.Debug.LogError("Call to the DotNetNativeWorkaround plug-in failed. The plug-in is required for correct behavior when using .NET Native compilation");
        return Marshal.GetObjectForIUnknown(nativePtr) as SpatialCoordinateSystem;
    }
}
```
