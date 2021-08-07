---
title: Native Mixed Reality-Objekte in Unity
description: Erfahren Sie, wie Sie mithilfe des XR-Namespace Zugriff auf zugrunde liegende native Holographic-Objekte in Unity erhalten.
author: vladkol
ms.author: vladkol
ms.date: 02/25/2021
ms.topic: article
keywords: Unity, Mixed Reality, nativ, xrdevice, spatialcoordinatesystem, holographicframe, holographiccamera, islipalcoordinatesystem, iholographicframe, iholographiccamera, getnativeptr, mixed reality headset, windows mixed reality headset, virtual reality headset
ms.openlocfilehash: 63ee9c33a972cb918f141df3b4c1608a561b96dc5c37910deb77b089f7be69b8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208401"
---
# <a name="mixed-reality-native-interop-in-unity"></a>Native Mixed Reality-Interop in Unity

Jede Mixed Reality-App [erhält einen HolographicSpace,](../native/getting-a-holographicspace.md) bevor sie mit dem Empfang von Kameradaten und Renderingframes beginnt. In Unity übernimmt die Engine diese Schritte für Sie, um Holographic-Objekte zu behandeln und intern als Teil der Renderschleife zu aktualisieren.

In erweiterten Szenarien müssen Sie jedoch möglicherweise Zugriff auf die zugrunde liegenden nativen Objekte wie <a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> und den aktuellen <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame erhalten.</a>

[!INCLUDE[](includes/unity-native-ptrs.md)]

### <a name="unmarshaling-native-pointers"></a>Unmarshaling nativer Zeiger

Verwenden Sie nach dem Abrufen von aus einer der oben genannten Methoden (für MRTK nicht erforderlich) die folgenden Codeausschnitte, um sie in verwaltete `IntPtr` Objekte zu marshallen.

Wenn Sie [Microsoft.Windows. MixedReality.DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT): Sie können ein verwaltetes Objekt mithilfe der -Methode aus einem nativen Zeiger `FromNativePtr()` erstellen:

```cs
var worldOrigin = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(spatialCoordinateSystemPtr);
```

Verwenden Sie `Marshal.GetObjectForIUnknown()` andernfalls , und geben Sie sie in den von Ihnen angegebenen Typ um:

```cs
#if ENABLE_WINMD_SUPPORT
var worldOrigin = Marshal.GetObjectForIUnknown(spatialCoordinateSystemPtr) as Windows.Perception.Spatial.SpatialCoordinateSystem;
#endif
```

### <a name="converting-between-coordinate-systems"></a>Konvertieren zwischen Koordinatensystemen

Unity verwendet ein linkshändiges Koordinatensystem, während die Windows Perception-APIs rechtshändige Koordinatensysteme verwenden. Um zwischen diesen beiden Konventionen zu konvertieren, können Sie die folgenden Hilfsatoren verwenden:

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

### <a name="using-holographicframe-native-data"></a>Verwenden nativer HolographicFrame-Daten

> [!NOTE]
> Das Ändern des Zustands der nativen Objekte, die über HolographicFrameNativeData empfangen werden, kann zu unvorhersehbarem Verhalten und Renderingartefakten führen, insbesondere dann, wenn Unity denselben Zustand ebenfalls verursacht.  Sie sollten z. B. HolographicFrame.UpdateCurrentPrediction nicht aufrufen, da die Vorhersage der Posen, die Unity mit diesem Frame rendert, nicht mit der von Windows zu erwartenden Pose synchron ist, wodurch die [Hologrammstabilität](../platform-capabilities-and-apis/hologram-stability.md)reduziert wird.

Wenn Sie zu Rendering- oder Debugzwecken Zugriff auf native Schnittstellen benötigen, verwenden Sie Daten aus HolographicFrameNativeData in Ihren nativen Plug-Ins oder C#-Code.

Hier ist ein Beispiel dafür, wie Sie HolographicFrameNativeData verwenden können, um die Vorhersage des aktuellen Frames für die Photonenzeit mithilfe der XR SDK-Erweiterungen zu erhalten.

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

## <a name="see-also"></a>Weitere Informationen

* [Verwenden des Windows-Namespace mit Unity-Apps für HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* <a href="/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>
* <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>
* <a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>
* [Rendern in DirectX](../native/rendering-in-directx.md)
