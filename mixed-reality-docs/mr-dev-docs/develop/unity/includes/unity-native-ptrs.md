---
ms.openlocfilehash: 78296dd4e6667c34926c954774547b21a223c5f4b6635476c51046c7ca22cdc3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208400"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)

## <a name="windowsmixedrealityutilities"></a>WindowsMixedRealityUtilities

**Namespace:** *Microsoft.MixedReality.Toolkit.WindowsMixedReality*<br>
**Typ:** *WindowsMixedRealityUtilities*

MRTK stellt über die **WindowsMixedRealityUtilities-Klasse** bereits marshalled-Typen für ältere WSA und das XR SDK bereit.

```cs
public static HolographicFrame CurrentHolographicFrame { get; }
public static SpatialCoordinateSystem SpatialCoordinateSystem { get; }
public static SpatialInteractionManager SpatialInteractionManager { get; }
```

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)

## <a name="windowsmrenvironment"></a>WindowsMREnvironment

**Namespace:** *UnityEngine.XR.WindowsMR*<br>
**Typ:** *WindowsMREnvironment*

Die statische **WindowsMREnvironment-Klasse** bietet Zugriff auf mehrere native Zeiger.

```cs
public static IntPtr CurrentHolographicRenderFrame { get; } // Windows::Graphics::Holographic::IHolographicFrame
public static IntPtr HolographicSpace { get; } // Windows::Graphics::Holographic::IHolographicSpace
public static IntPtr OriginSpatialCoordinateSystem { get; } // Windows::Perception::Spatial::ISpatialCoordinateSystem
```

# <a name="legacy-wsa"></a>[Legacy-WSA](#tab/wsa)

## <a name="xrdevice"></a>XRDevice

**Namespace:** *UnityEngine.XR*<br>
**Typ:** *XRDevice*

Mit dem <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**XRDevice-Typ**</a> können Sie mithilfe der <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr-Methode</a> Zugriff auf zugrunde liegende native Objekte erhalten. Die Rückgabe von GetNativePtr variiert je nach Plattform. Auf der universellen Windows Platform gibt XRDevice.GetNativePtr bei der Festlegung auf Windows Mixed Reality einen Zeiger (IntPtr) auf die folgende Struktur zurück:

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

Sie können es mithilfe der Marshal.PtrToStructure-Methode in HolographicFrameNativeData konvertieren:

```cs
IntPtr nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```

***IHolographicCameraPtr** ist ein Array von IntPtr, das als UnmanagedType.ByValArray gemarshallt wird und deren Länge maxNumberOfCameras entspricht.*
