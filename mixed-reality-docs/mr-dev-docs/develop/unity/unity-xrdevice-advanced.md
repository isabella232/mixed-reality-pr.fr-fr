---
title: Objets natifs de réalité mixte dans Unity
description: Découvrez comment obtenir l’accès aux objets natifs holographiques sous-jacents dans Unity à l’aide de l’espace de noms XR.
author: vladkol
ms.author: vladkol
ms.date: 05/20/2018
ms.topic: article
keywords: Unity, la réalité mixte, native, xrdevice, spatialcoordinatesystem, holographicframe, holographiccamera, ispatialcoordinatesystem, iholographicframe, iholographiccamera, getnativeptr, casque de la réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle
ms.openlocfilehash: 7aa69286942ce98909e23508d92fb88c59ce9175
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009809"
---
# <a name="mixed-reality-native-objects-in-unity"></a>Objets natifs de réalité mixte dans Unity

Chaque application de réalité mixte [obtient un HolographicSpace avant de](../native/getting-a-holographicspace.md) commencer à recevoir des données de caméra et des frames de rendu. Dans Unity, le moteur prend en charge ces étapes pour vous, en gérant des objets holographiques et en effectuant une mise à jour en interne dans le cadre de sa boucle de rendu.

Toutefois, dans les scénarios avancés, vous devrez peut-être accéder aux objets natifs sous-jacents, tels que <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> et <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>actuel. <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine. XR. XRDevice</a> est ce qui permet d’accéder à ces objets natifs.

## <a name="xrdevice"></a>XRDevice 

**Espace de noms :** *UnityEngine. XR*<br>
**Type :** *XRDevice*

Le type *XRDevice* vous permet d’accéder aux objets natifs sous-jacents à l’aide de la méthode <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> . Ce que GetNativePtr retourne varie entre différentes plateformes. Sur la plateforme Windows universelle, quand vous ciblez le kit de développement logiciel (SDK) XR Windows Mixed Reality, XRDevice. GetNativePtr retourne un pointeur (IntPtr) à la structure suivante : 

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
    public IntPtr IHolographicCameraPtr; // // Windows::Graphics::Holographic::IHolographicCamera
}
```
Vous pouvez la convertir en HolographicFrameNativeData à l’aide de la méthode Marshal. PtrToStructure provoquent :
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
***IHolographicCameraPtr** est un tableau de IntPtr marshalé en tant que UnmanagedType. ByValArray avec une longueur égale à MaxNumberOfCameras* 

### <a name="unmarshaling-native-pointers"></a>Démarshaler des pointeurs natifs

Si vous utilisez [Microsoft. Windows. MixedReality. DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT), vous pouvez construire un objet managé à partir d’un pointeur natif à l’aide de la `FromNativePtr()` méthode :

```cs
var worldOrigin = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(hfd.ISpatialCoordinateSystemPtr);
```

Sinon, utilisez `Marshal.GetObjectForIUnknown()` et effectuez un cast vers le type souhaité :

```cs
#if ENABLE_WINMD_SUPPORT
var worldOrigin = (Windows.Perception.Spatial.SpatialCoordinateSystem)Marshal.GetObjectForIUnknown(hfd.ISpatialCoordinateSystemPtr);
#endif
```

### <a name="converting-between-coordinate-systems"></a>Conversion entre des systèmes de coordonnées

Unity utilise un système de coordonnées gauche, tandis que les API de perception de Windows utilisent des systèmes de coordonnées droitiers. Pour effectuer une conversion entre ces deux conventions, vous pouvez utiliser les applications d’assistance suivantes :

```cs
namespace NumericsConversion
{
    public static class NumericsConversionExtensions
    {
        public static UnityEngine.Vector3 ToUnity(this System.Numerics.Vector3 v) => new UnityEngine.Vector3(v.X, v.Y, -v.Z);
        public static UnityEngine.Quaternion ToUnity(this System.Numerics.Quaternion q) => new UnityEngine.Quaternion(-q.X, -q.Y, q.Z, q.W);
        public static UnityEngine.Matrix4x4 ToUnity(this System.Numerics.Matrix4x4 m) => new UnityEngine.Matrix4x4(
            new Vector4( m.M11,  m.M12, -m.M13,  m.M14),
            new Vector4( m.M21,  m.M22, -m.M23,  m.M24),
            new Vector4(-m.M31, -m.M32,  m.M33, -m.M34),
            new Vector4( m.M41,  m.M42, -m.M43,  m.M44));

        public static System.Numerics.Vector3 ToSystem(this UnityEngine.Vector3 v) => new System.Numerics.Vector3(v.x, v.y, -v.z);
        public static System.Numerics.Quaternion ToSystem(this UnityEngine.Quaternion q) => new System.Numerics.Quaternion(-q.x, -q.y, q.z, q.w);
        public static System.Numerics.Matrix4x4 ToSystem(this UnityEngine.Matrix4x4 m) => new System.Numerics.Matrix4x4(
            m.m00,  m.m10, -m.m20,  m.m30,
            m.m01,  m.m11, -m.m21,  m.m31,
           -m.m02, -m.m12,  m.m22, -m.m32,
            m.m03,  m.m13, -m.m23,  m.m33);
    }
}
```

### <a name="using-holographicframe-native-data"></a>Utilisation de données natives HolographicFrame

> [!NOTE]
> La modification de l’état des objets natifs reçus via HolographicFrameNativeData peut entraîner un comportement imprévisible et des artefacts de rendu, en particulier si Unity a également des raisons de ce même État.  Par exemple, vous ne devez pas appeler HolographicFrame. UpdateCurrentPrediction, ou la prédiction de pose que les rendus Unity avec cette image ne seront pas synchronisées avec la pose attendue par Windows, ce qui réduira la stabilité de l' [hologramme](../platform-capabilities-and-apis/hologram-stability.md).

Si vous avez besoin d’accéder à des interfaces natives à des fins de rendu ou de débogage, utilisez les données de HolographicFrameNativeData dans vos plug-ins natifs ou votre code C#. 

Voici un exemple de la façon dont vous pouvez utiliser HolographicFrameNativeData pour obtenir la prédiction de l’image actuelle pour l’heure de la photonique. 

```cs
using System;
using System.Runtime.InteropServices;

public static bool GetCurrentFrameDateTime(out DateTime frameDateTime)
{
#if (!UNITY_EDITOR && UNITY_WSA) || ENABLE_WINMD_SUPPORT
    IntPtr nativeStruct = UnityEngine.XR.XRDevice.GetNativePtr();

    if (nativeStruct != IntPtr.Zero)
    {
        HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativeStruct);

        if (hfd.IHolographicFramePtr != IntPtr.Zero)
        {
            var holographicFrame = (Windows.Graphics.Holographic.HolographicFrame)Marshal.GetObjectForIUnknown(hfd.IHolographicFramePtr);
            frameDateTime = holographicFrame.CurrentPrediction.Timestamp.TargetTime.DateTime;
            return true;
        }
    }

#endif

    frameDateTime = DateTime.MinValue;
    return false;
}

```

## <a name="see-also"></a>Voir aussi

* [Utilisation de l’espace de noms Windows avec les applications Unity pour HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>
* [Rendu dans DirectX](../native/rendering-in-directx.md)
