---
ms.openlocfilehash: c3775dc73f41b822c233d8fc4ec62459e789b89f
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122265019"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)

## <a name="windowsmixedrealityutilities"></a>WindowsMixedRealityUtilities

**espace de noms :** *Microsoft. MixedReality. Shared Computer Toolkit. WindowsMixedReality*<br>
**Type :** *WindowsMixedRealityUtilities*

MRTK fournit des types déjà marshalés dans le kit de développement logiciel (SDK) WSA et XR hérité par le biais de la classe **WindowsMixedRealityUtilities** .

```cs
public static HolographicFrame CurrentHolographicFrame { get; }
public static SpatialCoordinateSystem SpatialCoordinateSystem { get; }
public static SpatialInteractionManager SpatialInteractionManager { get; }
```

# <a name="windows-xr-plugin"></a>[Windows Plug-in XR](#tab/xr)

## <a name="windowsmrenvironment"></a>WindowsMREnvironment

**Espace de noms :** *UnityEngine. XR. WindowsMR*<br>
**Type :** *WindowsMREnvironment*

La classe statique **WindowsMREnvironment** fournit l’accès à plusieurs pointeurs natifs.

```cs
public static IntPtr CurrentHolographicRenderFrame { get; } // Windows::Graphics::Holographic::IHolographicFrame
public static IntPtr HolographicSpace { get; } // Windows::Graphics::Holographic::IHolographicSpace
public static IntPtr OriginSpatialCoordinateSystem { get; } // Windows::Perception::Spatial::ISpatialCoordinateSystem
```

# <a name="legacy-wsa"></a>[WSA hérité](#tab/wsa)

## <a name="xrdevice"></a>XRDevice

**Espace de noms :** *UnityEngine. XR*<br>
**Type :** *XRDevice*

Le type <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**XRDevice**</a> vous permet d’accéder aux objets natifs sous-jacents à l’aide de la méthode <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> . Ce que GetNativePtr retourne varie entre différentes plateformes. sur la plateforme Windows universelle lorsque vous ciblez Windows Mixed Reality, XRDevice. GetNativePtr retourne un pointeur (IntPtr) à la structure suivante :

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

Vous pouvez la convertir en HolographicFrameNativeData à l’aide de la méthode Marshal. PtrToStructure provoquent :

```cs
IntPtr nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```

***IHolographicCameraPtr** est un tableau de IntPtr marshalé en tant que UnmanagedType. ByValArray avec une longueur égale à MaxNumberOfCameras*
