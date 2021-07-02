---
title: Handtracking
description: Dokumentation zur Verwendung von HandTracking in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Hand tracking,
ms.openlocfilehash: 68e936cb4121027008f37aae72496fe59445b636
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176891"
---
# <a name="hand-tracking"></a>Handtracking

## <a name="hand-tracking-profile"></a>Handtrackingprofil

Das _Handtrackingprofil_ befindet sich unter dem _Profil Eingabesystem_. Sie enthält Einstellungen zum Anpassen der Handdarstellung.

<img src="../images/input/HandTrackingProfile.png" width="650px" alt="Hand Tracking Profile" style="display:block;">

## <a name="joint-prefabs"></a>Gemeinsame Prefabs

Gemeinsame Prefabs werden mit einfachen Prefabs visualisiert. Die _Handflächen-_ und _Zeigefingerverbindungen_ sind von besonderer Bedeutung und verfügen über ein eigenes Prefab, während alle anderen Fugen das gleiche Prefab verwenden.

Standardmäßig sind die Handverbindungspräfabs einfache geometrische Grundtypen. Diese können bei Bedarf ersetzt werden. Wenn überhaupt kein Prefab angegeben wird, werden stattdessen leere [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) erstellt.

> [!WARNING]
> Vermeiden Sie komplexe Skripts oder teures Rendering in gemeinsamen Prefabs, da gemeinsame Objekte in jedem Frame transformiert werden und erhebliche Leistungskosten verursachen können!

Standarddarstellung von Handverbindungen |  Gemeinsame Bezeichnungen
:-------------------------:|:-------------------------:
<img src="../images/input-simulation/ArticulatedHandJoints.png" height="300px" alt="Articulated hand joints"  style="display:inline;">  |  <img src="../images/input-simulation/MRTK_Core_Input_Hands_JointNames.png" height="300px" alt="Input Hand joints"  style="display:inline;">

## <a name="hand-mesh-prefab"></a>Hand mesh prefab

Das Handgitternetz wird verwendet, wenn vom Handtrackinggerät vollständig definierte Gitternetzdaten bereitgestellt werden. Das Gitternetz, das im Prefab gerendert werden kann, wird durch Daten vom Gerät ersetzt, sodass ein Dummynetz wie ein Cube ausreichend ist. Das Material des Prefabs wird für das Handgitternetz verwendet.

<img src="../images/input-simulation/MRTK_Core_Input_Hands_ArticulatedHandMesh.png" width="350px" alt="Input Hand Mesh"  style="display:block;">

Die Anzeige des Handgitternetzes kann eine spürbare Auswirkung auf die Leistung haben. Aus diesem Grund kann es vollständig deaktiviert werden, indem die Option **Handnetzvisualisierung aktivieren** deaktiviert wird.

## <a name="hand-visualization-settings"></a>Einstellungen für die Handvisualisierung

Die Handgitternetz- und Handverbindungsvisualisierungen können über die Einstellung *Hand Mesh Visualization Modes* bzw. Hand Joint Visualization *Modes* aus- oder eingeschaltet werden. Diese Einstellungen sind anwendungsmodusspezifisch, d. h., es ist möglich, einige Features im Editor zu aktivieren (um z. B. Joints mit der Simulation im Editor anzuzeigen), während die gleichen Features deaktiviert sind, wenn sie auf dem Gerät bereitgestellt werden (in Playerbuilds).

Beachten Sie, dass es im Allgemeinen empfohlen wird, die Handverbindungsvisualisierung im Editor zu aktiviert zu lassen (damit die Simulation im Editor zeigt, wo sich die Handverbindungen befinden), und dass sowohl die Handverbindungsvisualisierung als auch die Handgittermodellvisualisierung im Spieler deaktiviert werden (da sie zu leistungsbezogenen Treffern führt).

## <a name="scripting"></a>Skripterstellung

Position und Drehung können vom Eingabesystem für jedes einzelne Handgesamt als angefordert [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) werden.

Alternativ ermöglicht das System den Zugriff auf [GameObjects,](https://docs.unity3d.com/ScriptReference/GameObject.html) die den Fugen folgen. Dies kann nützlich sein, wenn ein anderes GameObject ein Gemeinsames kontinuierlich nachverfolgen soll.

Verfügbare Fugen sind in der [`TrackedHandJoint`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedHandJoint) Enumeration aufgeführt.

> [!NOTE]
> Gemeinsame Objekte werden zerstört, wenn die Handverfolgung verloren geht! Stellen Sie sicher, dass alle Skripts, die das gemeinsame -Objekt verwenden, den `null` Fall ordnungsgemäß behandeln, um Fehler zu vermeiden!

### <a name="accessing-a-given-hand-controller"></a>Zugreifen auf einen bestimmten Handcontroller

Ein bestimmter Handcontroller ist häufig verfügbar, z. B. bei der Behandlung von Eingabeereignissen. In diesem Fall können die gemeinsamen Daten über die -Schnittstelle direkt vom Gerät angefordert [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) werden.

#### <a name="polling-joint-pose-from-controller"></a>Abfragen der gemeinsamen Posen vom Controller

Die [`TryGetJoint`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand.TryGetJoint*) Funktion gibt `false` zurück, wenn das angeforderte Gemeinsame aus irgendeinem Grund nicht verfügbar ist. In diesem Fall ist die resultierende Pose [`MixedRealityPose.ZeroIdentity`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose.ZeroIdentity) .

```c#
public void OnSourceDetected(SourceStateEventData eventData)
{
  var hand = eventData.Controller as IMixedRealityHand;
  if (hand != null)
  {
    if (hand.TryGetJoint(TrackedHandJoint.IndexTip, out MixedRealityPose jointPose)
    {
      // ...
    }
  }
}
```

#### <a name="joint-transform-from-hand-visualizer"></a>Gemeinsame Transformation aus Hand-Schnellansicht

Gemeinsame Objekte können über die [Controller-Schnellansicht](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController.Visualizer)angefordert werden.

```c#
public void OnSourceDetected(SourceStateEventData eventData)
{
  var handVisualizer = eventData.Controller.Visualizer as IMixedRealityHandVisualizer;
  if (handVisualizer != null)
  {
    if (handVisualizer.TryGetJointTransform(TrackedHandJoint.IndexTip, out Transform jointTransform)
    {
      // ...
    }
  }
}
```

### <a name="simplified-joint-data-access"></a>Vereinfachter gemeinsamer Datenzugriff

Wenn kein bestimmter Controller angegeben wird, werden Hilfsprogrammklassen für den bequemen Zugriff auf gemeinsame Handdaten bereitgestellt. Diese Funktionen fordern gemeinsame Daten vom ersten verfügbaren Handgerät an, das derzeit nachverfolgt wird.

#### <a name="polling-joint-pose-from-handjointutils"></a>Polling joint pose from HandJointUtils

[`HandJointUtils`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils) ist eine statische Klasse, die das erste aktive Gerät abfragt.

```c#
if (HandJointUtils.TryGetJointPose(TrackedHandJoint.IndexTip, Handedness.Right, out MixedRealityPose pose))
{
    // ...
}
```

#### <a name="joint-transform-from-hand-joint-service"></a>Gemeinsame Transformation aus handlichem gemeinsamen Dienst

[`IMixedRealityHandJointService`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointService) behält einen permanenten Satz von [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) für die Nachverfolgung von Joints bei.

```c#
var handJointService = CoreServices.GetInputSystemDataProvider<IMixedRealityHandJointService>();
if (handJointService != null)
{
    Transform jointTransform = handJointService.RequestJointTransform(TrackedHandJoint.IndexTip, Handedness.Right);
    // ...
}
```

### <a name="hand-tracking-events"></a>Handtrackingereignisse

Das Eingabesystem stellt auch Ereignisse bereit, wenn das direkte Abfragen von Daten von Controllern nicht wünschenswert ist.

#### <a name="joint-events"></a>Gemeinsame Ereignisse

[`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) behandelt Updates von Gemeinsamen Positionen.

```c#
public class MyHandJointEventHandler : IMixedRealityHandJointHandler
{
    public Handedness myHandedness;

    void IMixedRealityHandJointHandler.OnHandJointsUpdated(InputEventData<IDictionary<TrackedHandJoint, MixedRealityPose>> eventData)
    {
        if (eventData.Handedness == myHandedness)
        {
            if (eventData.InputData.TryGetValue(TrackedHandJoint.IndexTip, out MixedRealityPose pose))
            {
                // ...
            }
        }
    }
}
```

#### <a name="mesh-events"></a>Mesh-Ereignisse

[`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) behandelt Änderungen des artikulierten Handgitters.

Beachten Sie, dass Handgitternetze standardmäßig nicht aktiviert sind.

```c#
public class MyHandMeshEventHandler : IMixedRealityHandMeshHandler
{
    public Handedness myHandedness;
    public Mesh myMesh;

    public void OnHandMeshUpdated(InputEventData<HandMeshInfo> eventData)
    {
        if (eventData.Handedness == myHandedness)
        {
            myMesh.vertices = eventData.InputData.vertices;
            myMesh.normals = eventData.InputData.normals;
            myMesh.triangles = eventData.InputData.triangles;

            if (eventData.InputData.uvs != null && eventData.InputData.uvs.Length > 0)
            {
                myMesh.uv = eventData.InputData.uvs;
            }

            // ...
        }
    }
}
```

## <a name="known-issues"></a>Bekannte Probleme

### <a name="net-native"></a>.NET systemeigen

Derzeit gibt es ein bekanntes Problem mit Masterbuilds, die das .NET-Back-End verwenden. In .NET Native können `IInspectable` Zeiger nicht mithilfe von von systemeigenem in verwalteten Code gemarshallt `Marshal.GetObjectForIUnknown` werden. Das MRTK verwendet dies, um die `SpatialCoordinateSystem` abzurufen, um Hand- und Augendaten von der Plattform zu empfangen.

Wir haben die DLL-Quelle als Problemumgehung für dieses Problem im [repository nativen Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit/tree/master/DotNetNativeWorkaround)bereitgestellt. Befolgen Sie dort die Anweisungen in der README, und kopieren Sie die resultierenden Binärdateien in einen Plug-In-Ordner in Ihren Unity-Ressourcen. Danach löst das im MRTK bereitgestellte WindowsMixedRealityUtilities-Skript die Problemumgehung für Sie.

Wenn Sie eine eigene DLL erstellen oder diese Problemumgehung in eine vorhandene dll einschließen möchten, ist der Kern der Problemumgehung:

```c++
extern "C" __declspec(dllexport) void __stdcall MarshalIInspectable(IUnknown* nativePtr, IUnknown** inspectable)
{
    *inspectable = nativePtr;
}
```

Und seine Verwendung in Ihrem C#-Unity-Code:

```c#
[DllImport("DotNetNativeWorkaround.dll", EntryPoint = "MarshalIInspectable")]
private static extern void GetSpatialCoordinateSystem(IntPtr nativePtr, out SpatialCoordinateSystem coordinateSystem);

private static SpatialCoordinateSystem GetSpatialCoordinateSystem(IntPtr nativePtr)
{
    try
    {
        GetSpatialCoordinateSystem(nativePtr, out SpatialCoordinateSystem coordinateSystem);
        return coordinateSystem;
    }
    catch
    {
        UnityEngine.Debug.LogError("Call to the DotNetNativeWorkaround plug-in failed. The plug-in is required for correct behavior when using .NET Native compilation");
        return Marshal.GetObjectForIUnknown(nativePtr) as SpatialCoordinateSystem;
    }
}
```
