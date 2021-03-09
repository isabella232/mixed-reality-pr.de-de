---
title: Native Mixed Reality-Objekte in Unity
description: Erfahren Sie, wie Sie mit dem XR-Namespace Zugriff auf zugrunde liegende Holographic Native-Objekte in Unity erhalten.
author: vladkol
ms.author: vladkol
ms.date: 02/25/2021
ms.topic: article
keywords: Unity, Mixed Reality, Native, xrdevice, spatialcoordinatesystem, holographicframe, holographiccamera, ispatialcoordinatesystem, iholographicframe, iholographiccamera, getnativeptr, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: c202c698fe55bcd3215850579166ebcb8d4b8910
ms.sourcegitcommit: 441ef99e6090081c6cd3aa88ed21e13e941f0cc6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/09/2021
ms.locfileid: "102475073"
---
# <a name="mixed-reality-native-interop-in-unity"></a><span data-ttu-id="654bf-104">Gemischte Realität Native Interop in Unity</span><span class="sxs-lookup"><span data-stu-id="654bf-104">Mixed Reality native interop in Unity</span></span>

<span data-ttu-id="654bf-105">Jede Mixed Reality-APP [erhält einen holographicspace](../native/getting-a-holographicspace.md) , bevor Sie mit dem Empfang von Kameradaten und renderingframes beginnt.</span><span class="sxs-lookup"><span data-stu-id="654bf-105">Every Mixed Reality app [gets a HolographicSpace](../native/getting-a-holographicspace.md) before it starts receiving camera data and rendering frames.</span></span> <span data-ttu-id="654bf-106">In Unity übernimmt die Engine die Schritte für Sie, die Verarbeitung von Holographic-Objekten und die interne Aktualisierung im Rahmen der Renderingschleife.</span><span class="sxs-lookup"><span data-stu-id="654bf-106">In Unity, the engine takes care of those steps for you, handling Holographic objects and internally updating as part of its render loop.</span></span>

<span data-ttu-id="654bf-107">In erweiterten Szenarien müssen Sie jedoch möglicherweise Zugriff auf die zugrunde liegenden systemeigenen Objekte erhalten, wie z. b. <a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">holographiccamera</a> und Current <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">holographicframe</a>.</span><span class="sxs-lookup"><span data-stu-id="654bf-107">However, in advanced scenarios you may need to get access to the underlying native objects, such as the <a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> and current <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>.</span></span>

[!INCLUDE[](includes/unity-native-ptrs.md)]

### <a name="unmarshaling-native-pointers"></a><span data-ttu-id="654bf-108">Nicht Marshalling nativer Zeiger</span><span class="sxs-lookup"><span data-stu-id="654bf-108">Unmarshaling native pointers</span></span>

<span data-ttu-id="654bf-109">Nachdem Sie den `IntPtr` von einer der oben genannten Methoden (nicht benötigt für mrtk) erhalten haben, verwenden Sie die folgenden Code Ausschnitte, um Sie in verwaltete Objekte zu Mars Hallen.</span><span class="sxs-lookup"><span data-stu-id="654bf-109">After obtaining the `IntPtr` from one of the methods above (not needed for MRTK), use the following code snippets to marshal them to managed objects.</span></span>

<span data-ttu-id="654bf-110">Wenn Sie [Microsoft. Windows. mixedreality. dotnetwinrt](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT)verwenden, können Sie mithilfe der-Methode ein verwaltetes Objekt aus einem nativen Zeiger erstellen `FromNativePtr()` :</span><span class="sxs-lookup"><span data-stu-id="654bf-110">If you are using [Microsoft.Windows.MixedReality.DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT), you can construct a managed object from a native pointer using the `FromNativePtr()` method:</span></span>

```cs
var worldOrigin = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(spatialCoordinateSystemPtr);
```

<span data-ttu-id="654bf-111">Verwenden Sie andernfalls `Marshal.GetObjectForIUnknown()` und in den gewünschten Typ:</span><span class="sxs-lookup"><span data-stu-id="654bf-111">Otherwise, use `Marshal.GetObjectForIUnknown()` and cast to the type you want:</span></span>

```cs
#if ENABLE_WINMD_SUPPORT
var worldOrigin = Marshal.GetObjectForIUnknown(spatialCoordinateSystemPtr) as Windows.Perception.Spatial.SpatialCoordinateSystem;
#endif
```

### <a name="converting-between-coordinate-systems"></a><span data-ttu-id="654bf-112">Zwischen Koordinatensystemen</span><span class="sxs-lookup"><span data-stu-id="654bf-112">Converting between coordinate systems</span></span>

<span data-ttu-id="654bf-113">Unity verwendet ein Links händiges Koordinatensystem, während die Windows-perception-APIs rechts gerichtete Koordinatensysteme verwenden.</span><span class="sxs-lookup"><span data-stu-id="654bf-113">Unity uses a left-handed coordinate system, while the Windows Perception APIs use right-handed coordinate systems.</span></span> <span data-ttu-id="654bf-114">Zum Konvertieren zwischen diesen beiden Konventionen können Sie die folgenden Hilfsprogramme verwenden:</span><span class="sxs-lookup"><span data-stu-id="654bf-114">To convert between these two conventions, you can use the following helpers:</span></span>

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

### <a name="using-holographicframe-native-data"></a><span data-ttu-id="654bf-115">Verwenden von systemeigenen holographicframe-Daten</span><span class="sxs-lookup"><span data-stu-id="654bf-115">Using HolographicFrame native data</span></span>

> [!NOTE]
> <span data-ttu-id="654bf-116">Das Ändern des Zustands der systemeigenen Objekte, die über holographicframenativedata empfangen werden, kann zu unvorhersehbarem Verhalten und Rendern von Artefakten führen, insbesondere dann, wenn Unity auch für denselben Zustand verantwortlich ist.</span><span class="sxs-lookup"><span data-stu-id="654bf-116">Changing the state of the native objects received via HolographicFrameNativeData may cause unpredictable behavior and rendering artifacts, especially if Unity also reasons about that same state.</span></span>  <span data-ttu-id="654bf-117">Sie sollten z. b. holographicframe. updatecurrentvorhersage nicht aufrufen, oder andernfalls ist die Pose-Vorhersage, die Unity mit diesem Frame rendert, nicht mit der von Windows erwarteten Pose synchron. Dadurch wird die [– Hologramm-Stabilität](../platform-capabilities-and-apis/hologram-stability.md)reduziert.</span><span class="sxs-lookup"><span data-stu-id="654bf-117">For example, you should not call HolographicFrame.UpdateCurrentPrediction, or else the pose prediction that Unity renders with that frame will be out of sync with the pose that Windows is expecting, which will reduce [hologram stability](../platform-capabilities-and-apis/hologram-stability.md).</span></span>

<span data-ttu-id="654bf-118">Wenn Sie Zugriff auf systemeigene Schnittstellen für Rendering-oder Debuggingzwecke benötigen, verwenden Sie Daten von holographicframenativedata in ihren systemeigenen Plug-ins oder c#-Code.</span><span class="sxs-lookup"><span data-stu-id="654bf-118">If you need access to native interfaces for rendering or debugging purposes, use data from HolographicFrameNativeData in your native plugins or C# code.</span></span>

<span data-ttu-id="654bf-119">Im folgenden finden Sie ein Beispiel dafür, wie Sie holographicframenativedata verwenden können, um die Vorhersage des aktuellen Frames für die Photonen Zeit mithilfe der XR SDK-Erweiterungen zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="654bf-119">Here's an example of how you can use HolographicFrameNativeData to get the current frame's prediction for photon time using the XR SDK extensions.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="654bf-120">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="654bf-120">See Also</span></span>

* [<span data-ttu-id="654bf-121">Verwenden des Windows-Namespace mit Unity-Apps für HoloLens</span><span class="sxs-lookup"><span data-stu-id="654bf-121">Using the Windows namespace with Unity apps for HoloLens</span></span>](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* <span data-ttu-id="654bf-122"><a href="/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">Spatialcoordinatesystem</a></span><span class="sxs-lookup"><span data-stu-id="654bf-122"><a href="/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span></span>
* <span data-ttu-id="654bf-123"><a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span><span class="sxs-lookup"><span data-stu-id="654bf-123"><a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span></span>
* <span data-ttu-id="654bf-124"><a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span><span class="sxs-lookup"><span data-stu-id="654bf-124"><a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span></span>
* [<span data-ttu-id="654bf-125">Rendern in DirectX</span><span class="sxs-lookup"><span data-stu-id="654bf-125">Rendering in DirectX</span></span>](../native/rendering-in-directx.md)
