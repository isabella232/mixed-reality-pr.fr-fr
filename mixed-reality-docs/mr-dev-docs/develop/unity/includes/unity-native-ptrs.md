---
ms.openlocfilehash: 612168d7a1e56f74350ee8244e26e5ad886503c2
ms.sourcegitcommit: 441ef99e6090081c6cd3aa88ed21e13e941f0cc6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/09/2021
ms.locfileid: "102475072"
---
# <a name="mrtk"></a>[<span data-ttu-id="cffc7-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="cffc7-101">MRTK</span></span>](#tab/mrtk)

## <a name="windowsmixedrealityutilities"></a><span data-ttu-id="cffc7-102">WindowsMixedRealityUtilities</span><span class="sxs-lookup"><span data-stu-id="cffc7-102">WindowsMixedRealityUtilities</span></span>

<span data-ttu-id="cffc7-103">**Espace de noms :** *Microsoft. MixedReality. Toolkit. WindowsMixedReality*</span><span class="sxs-lookup"><span data-stu-id="cffc7-103">**Namespace:** *Microsoft.MixedReality.Toolkit.WindowsMixedReality*</span></span><br>
<span data-ttu-id="cffc7-104">**Type :** *WindowsMixedRealityUtilities*</span><span class="sxs-lookup"><span data-stu-id="cffc7-104">**Type:** *WindowsMixedRealityUtilities*</span></span>

<span data-ttu-id="cffc7-105">MRTK fournit des types déjà marshalés dans le kit de développement logiciel (SDK) WSA et XR hérité par le biais de la classe **WindowsMixedRealityUtilities** .</span><span class="sxs-lookup"><span data-stu-id="cffc7-105">MRTK provides already-marshalled types across both legacy WSA and XR SDK through the **WindowsMixedRealityUtilities** class.</span></span>

```cs
public static HolographicFrame CurrentHolographicFrame { get; }
public static SpatialCoordinateSystem SpatialCoordinateSystem { get; }
public static SpatialInteractionManager SpatialInteractionManager { get; }
```

# <a name="xr-sdk"></a>[<span data-ttu-id="cffc7-106">SDK XR</span><span class="sxs-lookup"><span data-stu-id="cffc7-106">XR SDK</span></span>](#tab/xr)

## <a name="windowsmrenvironment"></a><span data-ttu-id="cffc7-107">WindowsMREnvironment</span><span class="sxs-lookup"><span data-stu-id="cffc7-107">WindowsMREnvironment</span></span>

<span data-ttu-id="cffc7-108">**Espace de noms :** *UnityEngine. XR. WindowsMR*</span><span class="sxs-lookup"><span data-stu-id="cffc7-108">**Namespace:** *UnityEngine.XR.WindowsMR*</span></span><br>
<span data-ttu-id="cffc7-109">**Type :** *WindowsMREnvironment*</span><span class="sxs-lookup"><span data-stu-id="cffc7-109">**Type:** *WindowsMREnvironment*</span></span>

<span data-ttu-id="cffc7-110">La classe statique **WindowsMREnvironment** fournit l’accès à plusieurs pointeurs natifs.</span><span class="sxs-lookup"><span data-stu-id="cffc7-110">The static **WindowsMREnvironment** class provides access to several native pointers.</span></span>

```cs
public static IntPtr CurrentHolographicRenderFrame { get; } // Windows::Graphics::Holographic::IHolographicFrame
public static IntPtr HolographicSpace { get; } // Windows::Graphics::Holographic::IHolographicSpace
public static IntPtr OriginSpatialCoordinateSystem { get; } // Windows::Perception::Spatial::ISpatialCoordinateSystem
```

# <a name="legacy-wsa"></a>[<span data-ttu-id="cffc7-111">WSA hérité</span><span class="sxs-lookup"><span data-stu-id="cffc7-111">Legacy WSA</span></span>](#tab/wsa)

## <a name="xrdevice"></a><span data-ttu-id="cffc7-112">XRDevice</span><span class="sxs-lookup"><span data-stu-id="cffc7-112">XRDevice</span></span>

<span data-ttu-id="cffc7-113">**Espace de noms :** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="cffc7-113">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="cffc7-114">**Type :** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="cffc7-114">**Type:** *XRDevice*</span></span>

<span data-ttu-id="cffc7-115">Le type <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**XRDevice**</a> vous permet d’accéder aux objets natifs sous-jacents à l’aide de la méthode <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> .</span><span class="sxs-lookup"><span data-stu-id="cffc7-115">The <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**XRDevice**</a> type allows you to get access to underlying native objects using the <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> method.</span></span> <span data-ttu-id="cffc7-116">Ce que GetNativePtr retourne varie entre différentes plateformes.</span><span class="sxs-lookup"><span data-stu-id="cffc7-116">What GetNativePtr returns varies between different platforms.</span></span> <span data-ttu-id="cffc7-117">Sur la plateforme Windows universelle lorsque vous ciblez Windows Mixed Reality, XRDevice. GetNativePtr retourne un pointeur (IntPtr) à la structure suivante :</span><span class="sxs-lookup"><span data-stu-id="cffc7-117">On the Universal Windows Platform when targeting Windows Mixed Reality, XRDevice.GetNativePtr returns a pointer (IntPtr) to the following structure:</span></span>

```cs
using System;
using System.Runtime.InteropServices;

[StructLayout(LayoutKind.Sequential)]
struct HolographicFrameNativeData
{
    public uint VersionNumber;
    public uint MaxNumberOfCameras;
    public IntPtr ISpatialCoordinateSystemPtr; // Windows::Perception::Spatial::ISpatialCoordinateSystem
    public IntPtr IHolographicFramePtr; // Windows::Graphics::Holographic::IHolographicFrame
    public IntPtr IHolographicCameraPtr; // Windows::Graphics::Holographic::IHolographicCamera
}
```

<span data-ttu-id="cffc7-118">Vous pouvez la convertir en HolographicFrameNativeData à l’aide de la méthode Marshal. PtrToStructure provoquent :</span><span class="sxs-lookup"><span data-stu-id="cffc7-118">You can convert it to HolographicFrameNativeData using Marshal.PtrToStructure method:</span></span>

```cs
IntPtr nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```

<span data-ttu-id="cffc7-119">***IHolographicCameraPtr** est un tableau de IntPtr marshalé en tant que UnmanagedType. ByValArray avec une longueur égale à MaxNumberOfCameras*</span><span class="sxs-lookup"><span data-stu-id="cffc7-119">***IHolographicCameraPtr** is an array of IntPtr marshaled as UnmanagedType.ByValArray with a length equal to MaxNumberOfCameras*</span></span>
