---
ms.openlocfilehash: 612168d7a1e56f74350ee8244e26e5ad886503c2
ms.sourcegitcommit: 441ef99e6090081c6cd3aa88ed21e13e941f0cc6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/09/2021
ms.locfileid: "102475074"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)

## <a name="windowsmixedrealityutilities"></a>Windowsmixedrealityutilities

**Namespace:** *Microsoft. mixedreality. Toolkit. windowsmixedreality*<br>
**Typ:** *windowsmixedrealityutilities*

Mrtk stellt über die **windowsmixedrealityutilities** -Klasse bereits gemarshallte Typen für die Legacy-WSA und das XR SDK bereit.

```cs
public static HolographicFrame CurrentHolographicFrame { get; }
public static SpatialCoordinateSystem SpatialCoordinateSystem { get; }
public static SpatialInteractionManager SpatialInteractionManager { get; }
```

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)

## <a name="windowsmrenvironment"></a>Windowsmrenvironment

**Namespace:** *unityengine. XR. windowsmr*<br>
**Typ:** *windowsmrenvironment*

Die statische **windowsmrenvironment** -Klasse ermöglicht den Zugriff auf mehrere Native Zeiger.

```cs
public static IntPtr CurrentHolographicRenderFrame { get; } // Windows::Graphics::Holographic::IHolographicFrame
public static IntPtr HolographicSpace { get; } // Windows::Graphics::Holographic::IHolographicSpace
public static IntPtr OriginSpatialCoordinateSystem { get; } // Windows::Perception::Spatial::ISpatialCoordinateSystem
```

# <a name="legacy-wsa"></a>[Legacy-WSA](#tab/wsa)

## <a name="xrdevice"></a>Xrdevice

**Namespace:** *unityengine. XR*<br>
**Typ:** *xrdevice*

Der <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**xrdevice**</a> -Typ ermöglicht es Ihnen, mithilfe der <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">getnativeptr</a> -Methode Zugriff auf zugrunde liegende Native Objekte zu erhalten. Was getnativeptr zurückgibt, variiert zwischen verschiedenen Plattformen. Bei der universelle Windows-Plattform für Windows Mixed Reality gibt xrdevice. getnativeptr einen Zeiger (IntPtr) an die folgende Struktur zurück:

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

Sie können es mithilfe der Marshal. ptrumstructure-Methode in holographicframenativedata konvertieren:

```cs
IntPtr nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```

***Iholographiccameraptr** ist ein Array von IntPtr, das als UnmanagedType. ByValArray gemarshallt wird, wobei eine Länge gleich maxnumofkameras ist.*
