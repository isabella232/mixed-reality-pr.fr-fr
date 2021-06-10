---
ms.openlocfilehash: 76f72ac81b677acabf98444f626b7a6b908c29fb
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748454"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK gère automatiquement les paramètres spécifiques de l’appareil photo, en fonction de la [configuration du profil système de l’appareil photo](/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings).

**Espace de noms :** *Microsoft. MixedReality. Toolkit. CameraSystem*<br>
**Type :** *MixedRealityCameraSystem*

Pour vérifier l’opacité de l’appareil photo, le système MixedRealityCamera a [une `IsOpaque` propriété](/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).

```cs
CoreServices.CameraSystem.IsOpaque;
```

# <a name="xr-sdk"></a>[Kit de développement logiciel (SDK) XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

**Espace de noms :** *UnityEngine. XR*<br>
**Type :** *XRDisplaySubsystem*

Vous pouvez utiliser le code de script pour déterminer au moment de l’exécution si le casque est immersif ou holographique en vérifiant [displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) sur le [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html)activement en cours d’exécution.

# <a name="legacy-wsa"></a>[WSA hérité](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

**Espace de noms :** *UnityEngine. XR. WSA*<br>
**Type :** *HolographicSettings*

Vous pouvez utiliser le code de script pour déterminer au moment de l’exécution si le casque est immersif ou holographique en vérifiant [HolographicSettings. IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).