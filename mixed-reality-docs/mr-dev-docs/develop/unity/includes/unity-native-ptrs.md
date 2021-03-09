---
ms.openlocfilehash: 612168d7a1e56f74350ee8244e26e5ad886503c2
ms.sourcegitcommit: 441ef99e6090081c6cd3aa88ed21e13e941f0cc6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/09/2021
ms.locfileid: "102475074"
---
# <a name="mrtk"></a>[<span data-ttu-id="8f75f-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="8f75f-101">MRTK</span></span>](#tab/mrtk)

## <a name="windowsmixedrealityutilities"></a><span data-ttu-id="8f75f-102">Windowsmixedrealityutilities</span><span class="sxs-lookup"><span data-stu-id="8f75f-102">WindowsMixedRealityUtilities</span></span>

<span data-ttu-id="8f75f-103">**Namespace:** *Microsoft. mixedreality. Toolkit. windowsmixedreality*</span><span class="sxs-lookup"><span data-stu-id="8f75f-103">**Namespace:** *Microsoft.MixedReality.Toolkit.WindowsMixedReality*</span></span><br>
<span data-ttu-id="8f75f-104">**Typ:** *windowsmixedrealityutilities*</span><span class="sxs-lookup"><span data-stu-id="8f75f-104">**Type:** *WindowsMixedRealityUtilities*</span></span>

<span data-ttu-id="8f75f-105">Mrtk stellt über die **windowsmixedrealityutilities** -Klasse bereits gemarshallte Typen für die Legacy-WSA und das XR SDK bereit.</span><span class="sxs-lookup"><span data-stu-id="8f75f-105">MRTK provides already-marshalled types across both legacy WSA and XR SDK through the **WindowsMixedRealityUtilities** class.</span></span>

```cs
public static HolographicFrame CurrentHolographicFrame { get; }
public static SpatialCoordinateSystem SpatialCoordinateSystem { get; }
public static SpatialInteractionManager SpatialInteractionManager { get; }
```

# <a name="xr-sdk"></a>[<span data-ttu-id="8f75f-106">XR SDK</span><span class="sxs-lookup"><span data-stu-id="8f75f-106">XR SDK</span></span>](#tab/xr)

## <a name="windowsmrenvironment"></a><span data-ttu-id="8f75f-107">Windowsmrenvironment</span><span class="sxs-lookup"><span data-stu-id="8f75f-107">WindowsMREnvironment</span></span>

<span data-ttu-id="8f75f-108">**Namespace:** *unityengine. XR. windowsmr*</span><span class="sxs-lookup"><span data-stu-id="8f75f-108">**Namespace:** *UnityEngine.XR.WindowsMR*</span></span><br>
<span data-ttu-id="8f75f-109">**Typ:** *windowsmrenvironment*</span><span class="sxs-lookup"><span data-stu-id="8f75f-109">**Type:** *WindowsMREnvironment*</span></span>

<span data-ttu-id="8f75f-110">Die statische **windowsmrenvironment** -Klasse ermöglicht den Zugriff auf mehrere Native Zeiger.</span><span class="sxs-lookup"><span data-stu-id="8f75f-110">The static **WindowsMREnvironment** class provides access to several native pointers.</span></span>

```cs
public static IntPtr CurrentHolographicRenderFrame { get; } // Windows::Graphics::Holographic::IHolographicFrame
public static IntPtr HolographicSpace { get; } // Windows::Graphics::Holographic::IHolographicSpace
public static IntPtr OriginSpatialCoordinateSystem { get; } // Windows::Perception::Spatial::ISpatialCoordinateSystem
```

# <a name="legacy-wsa"></a>[<span data-ttu-id="8f75f-111">Legacy-WSA</span><span class="sxs-lookup"><span data-stu-id="8f75f-111">Legacy WSA</span></span>](#tab/wsa)

## <a name="xrdevice"></a><span data-ttu-id="8f75f-112">Xrdevice</span><span class="sxs-lookup"><span data-stu-id="8f75f-112">XRDevice</span></span>

<span data-ttu-id="8f75f-113">**Namespace:** *unityengine. XR*</span><span class="sxs-lookup"><span data-stu-id="8f75f-113">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="8f75f-114">**Typ:** *xrdevice*</span><span class="sxs-lookup"><span data-stu-id="8f75f-114">**Type:** *XRDevice*</span></span>

<span data-ttu-id="8f75f-115">Der <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**xrdevice**</a> -Typ ermöglicht es Ihnen, mithilfe der <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">getnativeptr</a> -Methode Zugriff auf zugrunde liegende Native Objekte zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="8f75f-115">The <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**XRDevice**</a> type allows you to get access to underlying native objects using the <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> method.</span></span> <span data-ttu-id="8f75f-116">Was getnativeptr zurückgibt, variiert zwischen verschiedenen Plattformen.</span><span class="sxs-lookup"><span data-stu-id="8f75f-116">What GetNativePtr returns varies between different platforms.</span></span> <span data-ttu-id="8f75f-117">Bei der universelle Windows-Plattform für Windows Mixed Reality gibt xrdevice. getnativeptr einen Zeiger (IntPtr) an die folgende Struktur zurück:</span><span class="sxs-lookup"><span data-stu-id="8f75f-117">On the Universal Windows Platform when targeting Windows Mixed Reality, XRDevice.GetNativePtr returns a pointer (IntPtr) to the following structure:</span></span>

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

<span data-ttu-id="8f75f-118">Sie können es mithilfe der Marshal. ptrumstructure-Methode in holographicframenativedata konvertieren:</span><span class="sxs-lookup"><span data-stu-id="8f75f-118">You can convert it to HolographicFrameNativeData using Marshal.PtrToStructure method:</span></span>

```cs
IntPtr nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```

<span data-ttu-id="8f75f-119">***Iholographiccameraptr** ist ein Array von IntPtr, das als UnmanagedType. ByValArray gemarshallt wird, wobei eine Länge gleich maxnumofkameras ist.*</span><span class="sxs-lookup"><span data-stu-id="8f75f-119">***IHolographicCameraPtr** is an array of IntPtr marshaled as UnmanagedType.ByValArray with a length equal to MaxNumberOfCameras*</span></span>
