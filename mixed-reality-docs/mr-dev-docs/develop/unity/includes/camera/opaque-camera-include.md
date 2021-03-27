---
ms.openlocfilehash: 0dfbe2cda2779c2eafe54b01d2d28e703444fd1a
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636294"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK gère automatiquement les paramètres spécifiques de l’appareil photo, en fonction de la [configuration du profil système de l’appareil photo](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings).

**Espace de noms :** *Microsoft. MixedReality. Toolkit. CameraSystem*<br>
**Type :** *MixedRealityCameraSystem*

Pour vérifier l’opacité de l’appareil photo, le système MixedRealityCamera a [une `IsOpaque` propriété](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).

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