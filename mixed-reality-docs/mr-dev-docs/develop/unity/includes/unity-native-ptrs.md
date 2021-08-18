---
ms.openlocfilehash: c3775dc73f41b822c233d8fc4ec62459e789b89f
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2021
ms.locfileid: "122264976"
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

# <a name="windows-xr-plugin"></a>[Windows XR-Plug-In](#tab/xr)

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

Der <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**XRDevice-Typ**</a> ermöglicht ihnen den Zugriff auf zugrunde liegende native Objekte mithilfe der <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr-Methode.</a> Die Rückgabe von GetNativePtr variiert auf verschiedenen Plattformen. Auf der universellen Windows Platform gibt XRDevice.GetNativePtr beim Ziel Windows Mixed Reality einen Zeiger (IntPtr) auf die folgende Struktur zurück:

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

***IHolographicCameraPtr** ist ein Array von IntPtr, das als UnmanagedType.ByValArray gemarshallt wird und eine Länge hat, die maxNumberOfCameras entspricht.*
