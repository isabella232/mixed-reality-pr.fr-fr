---
title: Objets natifs de réalité mixte dans Unity
description: Découvrez comment obtenir l’accès aux objets natifs holographiques sous-jacents dans Unity à l’aide de l’espace de noms XR.
author: vladkol
ms.author: vladkol
ms.date: 02/25/2021
ms.topic: article
keywords: Unity, la réalité mixte, native, xrdevice, spatialcoordinatesystem, holographicframe, holographiccamera, ispatialcoordinatesystem, iholographicframe, iholographiccamera, getnativeptr, casque de la réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle
ms.openlocfilehash: c202c698fe55bcd3215850579166ebcb8d4b8910
ms.sourcegitcommit: 441ef99e6090081c6cd3aa88ed21e13e941f0cc6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/09/2021
ms.locfileid: "102475071"
---
# <a name="mixed-reality-native-interop-in-unity"></a><span data-ttu-id="8340d-104">Interopérabilité native de la réalité mixte dans Unity</span><span class="sxs-lookup"><span data-stu-id="8340d-104">Mixed Reality native interop in Unity</span></span>

<span data-ttu-id="8340d-105">Chaque application de réalité mixte [obtient un HolographicSpace avant de](../native/getting-a-holographicspace.md) commencer à recevoir des données de caméra et des frames de rendu.</span><span class="sxs-lookup"><span data-stu-id="8340d-105">Every Mixed Reality app [gets a HolographicSpace](../native/getting-a-holographicspace.md) before it starts receiving camera data and rendering frames.</span></span> <span data-ttu-id="8340d-106">Dans Unity, le moteur prend en charge ces étapes pour vous, en gérant des objets holographiques et en effectuant une mise à jour en interne dans le cadre de sa boucle de rendu.</span><span class="sxs-lookup"><span data-stu-id="8340d-106">In Unity, the engine takes care of those steps for you, handling Holographic objects and internally updating as part of its render loop.</span></span>

<span data-ttu-id="8340d-107">Toutefois, dans les scénarios avancés, vous devrez peut-être accéder aux objets natifs sous-jacents, tels que <a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> et <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>actuel.</span><span class="sxs-lookup"><span data-stu-id="8340d-107">However, in advanced scenarios you may need to get access to the underlying native objects, such as the <a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> and current <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>.</span></span>

[!INCLUDE[](includes/unity-native-ptrs.md)]

### <a name="unmarshaling-native-pointers"></a><span data-ttu-id="8340d-108">Démarshaler des pointeurs natifs</span><span class="sxs-lookup"><span data-stu-id="8340d-108">Unmarshaling native pointers</span></span>

<span data-ttu-id="8340d-109">Après avoir obtenu le `IntPtr` à partir de l’une des méthodes ci-dessus (inutile pour MRTK), utilisez les extraits de code suivants pour les marshaler vers des objets managés.</span><span class="sxs-lookup"><span data-stu-id="8340d-109">After obtaining the `IntPtr` from one of the methods above (not needed for MRTK), use the following code snippets to marshal them to managed objects.</span></span>

<span data-ttu-id="8340d-110">Si vous utilisez [Microsoft. Windows. MixedReality. DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT), vous pouvez construire un objet managé à partir d’un pointeur natif à l’aide de la `FromNativePtr()` méthode :</span><span class="sxs-lookup"><span data-stu-id="8340d-110">If you are using [Microsoft.Windows.MixedReality.DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT), you can construct a managed object from a native pointer using the `FromNativePtr()` method:</span></span>

```cs
var worldOrigin = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(spatialCoordinateSystemPtr);
```

<span data-ttu-id="8340d-111">Sinon, utilisez `Marshal.GetObjectForIUnknown()` et effectuez un cast vers le type souhaité :</span><span class="sxs-lookup"><span data-stu-id="8340d-111">Otherwise, use `Marshal.GetObjectForIUnknown()` and cast to the type you want:</span></span>

```cs
#if ENABLE_WINMD_SUPPORT
var worldOrigin = Marshal.GetObjectForIUnknown(spatialCoordinateSystemPtr) as Windows.Perception.Spatial.SpatialCoordinateSystem;
#endif
```

### <a name="converting-between-coordinate-systems"></a><span data-ttu-id="8340d-112">Conversion entre des systèmes de coordonnées</span><span class="sxs-lookup"><span data-stu-id="8340d-112">Converting between coordinate systems</span></span>

<span data-ttu-id="8340d-113">Unity utilise un système de coordonnées gauche, tandis que les API de perception de Windows utilisent des systèmes de coordonnées droitiers.</span><span class="sxs-lookup"><span data-stu-id="8340d-113">Unity uses a left-handed coordinate system, while the Windows Perception APIs use right-handed coordinate systems.</span></span> <span data-ttu-id="8340d-114">Pour effectuer une conversion entre ces deux conventions, vous pouvez utiliser les applications d’assistance suivantes :</span><span class="sxs-lookup"><span data-stu-id="8340d-114">To convert between these two conventions, you can use the following helpers:</span></span>

```cs
namespace NumericsConversion
{
    public static class NumericsConversionExtensions
    {
        public static UnityEngine.Vector3 ToUnity(this System.Numerics.Vector3 v) => new UnityEngine.Vector3(v.X, v.Y, -v.Z);
        public static UnityEngine.Quaternion ToUnity(this System.Numerics.Quaternion q) => new UnityEngine.Quaternion(q.X, q.Y, -q.Z, -q.W);
        public static UnityEngine.Matrix4x4 ToUnity(this System.Numerics.Matrix4x4 m) => new UnityEngine.Matrix4x4(
            new Vector4( m.M11,  m.M12, -m.M13,  m.M14),
            new Vector4( m.M21,  m.M22, -m.M23,  m.M24),
            new Vector4(-m.M31, -m.M32,  m.M33, -m.M34),
            new Vector4( m.M41,  m.M42, -m.M43,  m.M44));

        public static System.Numerics.Vector3 ToSystem(this UnityEngine.Vector3 v) => new System.Numerics.Vector3(v.x, v.y, -v.z);
        public static System.Numerics.Quaternion ToSystem(this UnityEngine.Quaternion q) => new System.Numerics.Quaternion(q.x, q.y, -q.z, -q.w);
        public static System.Numerics.Matrix4x4 ToSystem(this UnityEngine.Matrix4x4 m) => new System.Numerics.Matrix4x4(
            m.m00,  m.m10, -m.m20,  m.m30,
            m.m01,  m.m11, -m.m21,  m.m31,
           -m.m02, -m.m12,  m.m22, -m.m32,
            m.m03,  m.m13, -m.m23,  m.m33);
    }
}
```

### <a name="using-holographicframe-native-data"></a><span data-ttu-id="8340d-115">Utilisation de données natives HolographicFrame</span><span class="sxs-lookup"><span data-stu-id="8340d-115">Using HolographicFrame native data</span></span>

> [!NOTE]
> <span data-ttu-id="8340d-116">La modification de l’état des objets natifs reçus via HolographicFrameNativeData peut entraîner un comportement imprévisible et des artefacts de rendu, en particulier si Unity a également des raisons à ce même État.</span><span class="sxs-lookup"><span data-stu-id="8340d-116">Changing the state of the native objects received via HolographicFrameNativeData may cause unpredictable behavior and rendering artifacts, especially if Unity also reasons about that same state.</span></span>  <span data-ttu-id="8340d-117">Par exemple, vous ne devez pas appeler HolographicFrame. UpdateCurrentPrediction, ou la prédiction de pose que les rendus Unity avec cette image ne seront pas synchronisées avec la pose attendue par Windows, ce qui réduira la stabilité de l' [hologramme](../platform-capabilities-and-apis/hologram-stability.md).</span><span class="sxs-lookup"><span data-stu-id="8340d-117">For example, you should not call HolographicFrame.UpdateCurrentPrediction, or else the pose prediction that Unity renders with that frame will be out of sync with the pose that Windows is expecting, which will reduce [hologram stability](../platform-capabilities-and-apis/hologram-stability.md).</span></span>

<span data-ttu-id="8340d-118">Si vous avez besoin d’accéder à des interfaces natives à des fins de rendu ou de débogage, utilisez les données de HolographicFrameNativeData dans vos plug-ins natifs ou votre code C#.</span><span class="sxs-lookup"><span data-stu-id="8340d-118">If you need access to native interfaces for rendering or debugging purposes, use data from HolographicFrameNativeData in your native plugins or C# code.</span></span>

<span data-ttu-id="8340d-119">Voici un exemple de la façon dont vous pouvez utiliser HolographicFrameNativeData pour obtenir la prédiction de l’image actuelle pour le temps de la photonique à l’aide des extensions du kit de développement logiciel (SDK) XR.</span><span class="sxs-lookup"><span data-stu-id="8340d-119">Here's an example of how you can use HolographicFrameNativeData to get the current frame's prediction for photon time using the XR SDK extensions.</span></span>

```cs
using System;
using System.Runtime.InteropServices;

public static bool GetCurrentFrameDateTime(out DateTime frameDateTime)
{
#if ENABLE_WINMD_SUPPORT
    IntPtr holographicFramePtr = UnityEngine.XR.WindowsMR.WindowsMREnvironment.CurrentHolographicRenderFrame;

    if (holographicFramePtr != IntPtr.Zero)
    {
        var holographicFrame = Marshal.GetObjectForIUnknown(holographicFramePtr) as Windows.Graphics.Holographic.HolographicFrame;
        frameDateTime = holographicFrame.CurrentPrediction.Timestamp.TargetTime.DateTime;
        return true;
    }
#endif

    frameDateTime = DateTime.MinValue;
    return false;
}
```

## <a name="see-also"></a><span data-ttu-id="8340d-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8340d-120">See Also</span></span>

* [<span data-ttu-id="8340d-121">Utilisation de l’espace de noms Windows avec les applications Unity pour HoloLens</span><span class="sxs-lookup"><span data-stu-id="8340d-121">Using the Windows namespace with Unity apps for HoloLens</span></span>](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* <span data-ttu-id="8340d-122"><a href="/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span><span class="sxs-lookup"><span data-stu-id="8340d-122"><a href="/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span></span>
* <span data-ttu-id="8340d-123"><a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span><span class="sxs-lookup"><span data-stu-id="8340d-123"><a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span></span>
* <span data-ttu-id="8340d-124"><a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span><span class="sxs-lookup"><span data-stu-id="8340d-124"><a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span></span>
* [<span data-ttu-id="8340d-125">Rendu dans DirectX</span><span class="sxs-lookup"><span data-stu-id="8340d-125">Rendering in DirectX</span></span>](../native/rendering-in-directx.md)
