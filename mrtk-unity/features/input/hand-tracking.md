---
title: Suivi de la main
description: Documentation sur l’utilisation de HandTracking dans MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: unity, HoloLens, HoloLens 2, réalité mixte, développement, MRTK, suivi manuel,
ms.openlocfilehash: f9d3b6b0f83a513b849aa27d464595ec8543bc30b64314c9a6e341cd6cb3a519
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189491"
---
# <a name="hand-tracking"></a>Suivi de la main

## <a name="hand-tracking-profile"></a>Profil de suivi de la main

Le _profil de suivi_ de la main se trouve sous le _profil de système d’entrée_. Il contient les paramètres de personnalisation de la représentation manuelle.

<img src="../images/input/HandTrackingProfile.png" width="650px" alt="Hand Tracking Profile" style="display:block;">

## <a name="joint-prefabs"></a>Prefabs conjointe

Les prefabss conjointes sont visualisées à l’aide de prefabs simples. Les jointures de _palmier_ et d' _index_ ont une importance particulière et ont leur propre Prefab, tandis que tous les autres articulations partagent le même Prefab.

Par défaut, la prefabs jointe à la main sont des primitives géométriques simples. Vous pouvez les remplacer si vous le souhaitez. Si aucun Prefab n’est spécifié, les [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) vides sont créés à la place.

> [!WARNING]
> Évitez d’utiliser des scripts complexes ou un rendu coûteux dans des prefabss conjointes, car les objets conjoints sont transformés sur chaque image et peuvent avoir un coût de performances significatif.

Représentation conjointe de la main par défaut |  Étiquettes communes
:-------------------------:|:-------------------------:
<img src="../images/input-simulation/ArticulatedHandJoints.png" height="300px" alt="Articulated hand joints"  style="display:inline;">  |  <img src="../images/input-simulation/MRTK_Core_Input_Hands_JointNames.png" height="300px" alt="Input Hand joints"  style="display:inline;">

## <a name="hand-mesh-prefab"></a>Maille Prefab

Le maillage manuel est utilisé si les données de maillage entièrement définies sont fournies par l’appareil de suivi de la main. Le maillage qui peut être rendu dans le Prefab est remplacé par les données de l’appareil, de sorte qu’une maille factice comme un cube est suffisante. Le matériau de l’Prefab est utilisé pour le maillage à la main.

<img src="../images/input-simulation/MRTK_Core_Input_Hands_ArticulatedHandMesh.png" width="350px" alt="Input Hand Mesh"  style="display:block;">

L’affichage de maillage manuel peut avoir un impact notable sur les performances. pour cette raison, il peut être entièrement désactivé en désactivant l’option **activer la visualisation de maille manuelle** .

## <a name="hand-visualization-settings"></a>Paramètres de visualisation manuelle

Les visualisations conjointes à la main et à la main peuvent être désactivées ou activées par le biais du paramètre *modes de visualisation* de la main et des *modes de visualisation conjointe* . Ces paramètres sont spécifiques au mode application, ce qui signifie qu’il est possible d’activer certaines fonctionnalités dans l’éditeur (pour voir les jointures avec la simulation dans l’éditeur, par exemple) tout en désactivant les mêmes fonctionnalités lorsqu’elles sont déployées sur l’appareil (dans les versions Player).

Notez qu’il est généralement recommandé de faire en sorte que la visualisation conjointe manuelle soit activée dans l’éditeur (afin que la simulation dans l’éditeur indique où se trouvent les joints à la main) et que la visualisation conjointe et la visualisation de la maille manuelle soient désactivées dans le lecteur (car elles entraînent une baisse des performances).

## <a name="scripting"></a>Scripts

La position et la rotation peuvent être demandées à partir du système d’entrée pour chaque joint individuel sous la forme d’un [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) .

Le système permet également d’accéder aux [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) qui suivent les jointures. Cela peut être utile si un autre GameObject doit suivre une jointure en continu.

Les jointures disponibles sont répertoriées dans l' [`TrackedHandJoint`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedHandJoint) énumération.

> [!NOTE]
> L’objet joint est détruit lorsque le suivi de la main est perdu ! Assurez-vous que les scripts qui utilisent l’objet joint gèrent le `null` cas correctement pour éviter les erreurs.

### <a name="accessing-a-given-hand-controller"></a>Accès à un contrôleur de main donné

Un contrôleur de main spécifique est souvent disponible, par exemple lors du traitement des événements d’entrée. Dans ce cas, les données conjointes peuvent être demandées directement à partir de l’appareil, à l’aide de l' [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) interface.

#### <a name="polling-joint-pose-from-controller"></a>Attaque d’interrogation du contrôleur

La [`TryGetJoint`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand.TryGetJoint*) fonction retourne `false` si l’articulation demandé n’est pas disponible pour une raison quelconque. Dans ce cas, le pose obtenu sera [`MixedRealityPose.ZeroIdentity`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose.ZeroIdentity) .

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

#### <a name="joint-transform-from-hand-visualizer"></a>Transformation conjointe à partir du visualiseur main

Les objets conjoints peuvent être demandés à partir du [visualiseur du contrôleur](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController.Visualizer).

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

### <a name="simplified-joint-data-access"></a>Accès simplifié aux données jointes

Si aucun contrôleur spécifique n’est donné, les classes utilitaires sont fournies pour faciliter l’accès aux données jointes à la main. Ces fonctions demandent des données communes à partir du premier appareil disponible actuellement suivi.

#### <a name="polling-joint-pose-from-handjointutils"></a>Interrogation conjointe de HandJointUtils

[`HandJointUtils`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils) est une classe statique qui interroge le premier appareil main actif.

```c#
if (HandJointUtils.TryGetJointPose(TrackedHandJoint.IndexTip, Handedness.Right, out MixedRealityPose pose))
{
    // ...
}
```

#### <a name="joint-transform-from-hand-joint-service"></a>Transformation conjointe à partir du service joint à la main

[`IMixedRealityHandJointService`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointService) conserve un ensemble persistant de [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) pour le suivi des jointures.

```c#
var handJointService = CoreServices.GetInputSystemDataProvider<IMixedRealityHandJointService>();
if (handJointService != null)
{
    Transform jointTransform = handJointService.RequestJointTransform(TrackedHandJoint.IndexTip, Handedness.Right);
    // ...
}
```

### <a name="hand-tracking-events"></a>Événements de suivi de la main

Le système d’entrée fournit également des événements, si l’interrogation directe de données à partir de contrôleurs n’est pas souhaitable.

#### <a name="joint-events"></a>Événements communs

[`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) gère les mises à jour des positions de jointure.

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

#### <a name="mesh-events"></a>Événements de maillage

[`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) gère les modifications du maillage articulé.

Notez que les maillages de main ne sont pas activés par défaut.

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

## <a name="known-issues"></a>Problèmes connus

### <a name="net-native"></a>.NET Native

Il existe actuellement un problème connu avec les builds principales à l’aide du backend .NET. dans .NET Native, les `IInspectable` pointeurs ne peuvent pas être marshalés du code natif au code managé à l’aide de `Marshal.GetObjectForIUnknown` . Le MRTK utilise cette valeur pour obtenir le afin de `SpatialCoordinateSystem` recevoir les données de la plateforme et de la main.

nous avons fourni une source DLL comme solution de contournement pour ce problème, dans [la réalité mixte native Shared Computer Toolkit référentiel](https://github.com/microsoft/MixedRealityToolkit/tree/master/DotNetNativeWorkaround). Veuillez suivre les instructions du fichier Lisez-moi et copier les fichiers binaires résultants dans un dossier plugins de vos ressources Unity. Après cela, le script WindowsMixedRealityUtilities fourni dans le MRTK permet de résoudre la solution de contournement.

Si vous souhaitez créer votre propre DLL ou inclure cette solution de contournement dans une solution existante, le cœur de la solution de contournement est le suivant :

```c++
extern "C" __declspec(dllexport) void __stdcall MarshalIInspectable(IUnknown* nativePtr, IUnknown** inspectable)
{
    *inspectable = nativePtr;
}
```

Et son utilisation dans votre code C# Unity :

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
