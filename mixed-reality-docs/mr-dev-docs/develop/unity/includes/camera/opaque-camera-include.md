---
ms.openlocfilehash: 0dfbe2cda2779c2eafe54b01d2d28e703444fd1a
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636294"
---
# <a name="mrtk"></a>[<span data-ttu-id="94ad4-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="94ad4-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="94ad4-102">MRTK gère automatiquement les paramètres spécifiques de l’appareil photo, en fonction de la [configuration du profil système de l’appareil photo](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings).</span><span class="sxs-lookup"><span data-stu-id="94ad4-102">MRTK will handle specific camera settings automatically, based on the [configuration in the camera system profile](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings).</span></span>

<span data-ttu-id="94ad4-103">**Espace de noms :** *Microsoft. MixedReality. Toolkit. CameraSystem*</span><span class="sxs-lookup"><span data-stu-id="94ad4-103">**Namespace:** *Microsoft.MixedReality.Toolkit.CameraSystem*</span></span><br>
<span data-ttu-id="94ad4-104">**Type :** *MixedRealityCameraSystem*</span><span class="sxs-lookup"><span data-stu-id="94ad4-104">**Type:** *MixedRealityCameraSystem*</span></span>

<span data-ttu-id="94ad4-105">Pour vérifier l’opacité de l’appareil photo, le système MixedRealityCamera a [une `IsOpaque` propriété](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).</span><span class="sxs-lookup"><span data-stu-id="94ad4-105">To check the camera's opaqueness, the MixedRealityCamera system has [an `IsOpaque` property](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).</span></span>

```cs
CoreServices.CameraSystem.IsOpaque;
```

# <a name="xr-sdk"></a>[<span data-ttu-id="94ad4-106">Kit de développement logiciel (SDK) XR</span><span class="sxs-lookup"><span data-stu-id="94ad4-106">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="94ad4-107">**Espace de noms :** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="94ad4-107">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="94ad4-108">**Type :** *XRDisplaySubsystem*</span><span class="sxs-lookup"><span data-stu-id="94ad4-108">**Type:** *XRDisplaySubsystem*</span></span>

<span data-ttu-id="94ad4-109">Vous pouvez utiliser le code de script pour déterminer au moment de l’exécution si le casque est immersif ou holographique en vérifiant [displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) sur le [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html)activement en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="94ad4-109">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) on the actively running [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html).</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="94ad4-110">WSA hérité</span><span class="sxs-lookup"><span data-stu-id="94ad4-110">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="94ad4-111">**Espace de noms :** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="94ad4-111">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="94ad4-112">**Type :** *HolographicSettings*</span><span class="sxs-lookup"><span data-stu-id="94ad4-112">**Type:** *HolographicSettings*</span></span>

<span data-ttu-id="94ad4-113">Vous pouvez utiliser le code de script pour déterminer au moment de l’exécution si le casque est immersif ou holographique en vérifiant [HolographicSettings. IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).</span><span class="sxs-lookup"><span data-stu-id="94ad4-113">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).</span></span>