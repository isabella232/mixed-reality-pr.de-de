---
title: Handtracking
description: Dokumentation zur Verwendung von HandTracking in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Hand tracking,
ms.openlocfilehash: 6cd55bc76d9fba42640954bcbf50e62f66454a94
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143352"
---
# <a name="hand-tracking"></a><span data-ttu-id="8df25-104">Handtracking</span><span class="sxs-lookup"><span data-stu-id="8df25-104">Hand tracking</span></span>

## <a name="hand-tracking-profile"></a><span data-ttu-id="8df25-105">Handtrackingprofil</span><span class="sxs-lookup"><span data-stu-id="8df25-105">Hand tracking profile</span></span>

<span data-ttu-id="8df25-106">Das _Handtrackingprofil_ befindet sich unter dem _Profil Eingabesystem_.</span><span class="sxs-lookup"><span data-stu-id="8df25-106">The _Hand Tracking profile_ is found under the _Input System profile_.</span></span> <span data-ttu-id="8df25-107">Sie enthält Einstellungen zum Anpassen der Handdarstellung.</span><span class="sxs-lookup"><span data-stu-id="8df25-107">It contains settings for customizing hand representation.</span></span>

<img src="../images/input/HandTrackingProfile.png" width="650px" alt="Hand Tracking Profile" style="display:block;">

## <a name="joint-prefabs"></a><span data-ttu-id="8df25-108">Gemeinsame Prefabs</span><span class="sxs-lookup"><span data-stu-id="8df25-108">Joint prefabs</span></span>

<span data-ttu-id="8df25-109">Gemeinsame Prefabs werden mit einfachen Prefabs visualisiert.</span><span class="sxs-lookup"><span data-stu-id="8df25-109">Joint prefabs are visualized using simple prefabs.</span></span> <span data-ttu-id="8df25-110">Die _Handflächen-_ und _Zeigefingerverbindungen_ sind von besonderer Bedeutung und verfügen über ein eigenes Prefab, während alle anderen Fugen das gleiche Prefab verwenden.</span><span class="sxs-lookup"><span data-stu-id="8df25-110">The _Palm_ and _Index Finger_ joints are of special importance and have their own prefab, while all other joints share the same prefab.</span></span>

<span data-ttu-id="8df25-111">Standardmäßig sind die Handverbindungspräfabs einfache geometrische Grundtypen.</span><span class="sxs-lookup"><span data-stu-id="8df25-111">By default the hand joint prefabs are simple geometric primitives.</span></span> <span data-ttu-id="8df25-112">Diese können bei Bedarf ersetzt werden.</span><span class="sxs-lookup"><span data-stu-id="8df25-112">These can be replaced if desired.</span></span> <span data-ttu-id="8df25-113">Wenn überhaupt kein Prefab angegeben wird, werden stattdessen leere [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) erstellt.</span><span class="sxs-lookup"><span data-stu-id="8df25-113">If no prefab is specified at all, empty [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) are created instead.</span></span>

> [!WARNING]
> <span data-ttu-id="8df25-114">Vermeiden Sie komplexe Skripts oder teures Rendering in gemeinsamen Prefabs, da gemeinsame Objekte in jedem Frame transformiert werden und erhebliche Leistungskosten verursachen können!</span><span class="sxs-lookup"><span data-stu-id="8df25-114">Avoid using complex scripts or expensive rendering in joint prefabs, since joint objects are transformed on every frame and can have significant performance cost!</span></span>

<span data-ttu-id="8df25-115">Standarddarstellung von Handverbindungen</span><span class="sxs-lookup"><span data-stu-id="8df25-115">Default Hand Joint Representation</span></span> |  <span data-ttu-id="8df25-116">Gemeinsame Bezeichnungen</span><span class="sxs-lookup"><span data-stu-id="8df25-116">Joint Labels</span></span>
:-------------------------:|:-------------------------:
<img src="../images/input-simulation/ArticulatedHandJoints.png" height="300px" alt="Articulated hand joints"  style="display:inline;">  |  <img src="../images/input-simulation/MRTK_Core_Input_Hands_JointNames.png" height="300px" alt="Input Hand joints"  style="display:inline;">

## <a name="hand-mesh-prefab"></a><span data-ttu-id="8df25-117">Hand mesh prefab</span><span class="sxs-lookup"><span data-stu-id="8df25-117">Hand mesh prefab</span></span>

<span data-ttu-id="8df25-118">Das Handgitternetz wird verwendet, wenn vom Handtrackinggerät vollständig definierte Gitternetzdaten bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="8df25-118">The hand mesh is used if fully defined mesh data is provided by the hand tracking device.</span></span> <span data-ttu-id="8df25-119">Das Gitternetz, das im Prefab gerendert werden kann, wird durch Daten vom Gerät ersetzt, sodass ein Dummynetz wie ein Cube ausreichend ist.</span><span class="sxs-lookup"><span data-stu-id="8df25-119">The mesh renderable in the prefab is replaced by data from the device, so a dummy mesh such as a cube is sufficient.</span></span> <span data-ttu-id="8df25-120">Das Material des Prefabs wird für das Handgitternetz verwendet.</span><span class="sxs-lookup"><span data-stu-id="8df25-120">The material of the prefab is used for the hand mesh.</span></span>

<img src="../images/input-simulation/MRTK_Core_Input_Hands_ArticulatedHandMesh.png" width="350px" alt="Input Hand Mesh"  style="display:block;">

<span data-ttu-id="8df25-121">Die Anzeige des Handgitternetzes kann eine merkliche Auswirkung auf die Leistung haben. Aus diesem Grund kann sie vollständig deaktiviert werden, indem die Option **Handnetzvisualisierung aktivieren** deaktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="8df25-121">Hand mesh display can have a noticeable performance impact, for this reason it can be disabled entirely by unchecking **Enable Hand Mesh Visualization** option.</span></span>

## <a name="hand-visualization-settings"></a><span data-ttu-id="8df25-122">Einstellungen für die Handvisualisierung</span><span class="sxs-lookup"><span data-stu-id="8df25-122">Hand visualization settings</span></span>

<span data-ttu-id="8df25-123">Die Handgitter- und Hand-Hand-Fugenvisualisierungen können über die Einstellung Hand Mesh Visualization Modes (Handgittervisualisierungsmodi) bzw. Hand Joint Visualization Modes (Handgenetzvisualisierungsmodi) ein- bzw. *ausgeschaltet* werden. </span><span class="sxs-lookup"><span data-stu-id="8df25-123">The hand mesh and hand joint visualizations can be turned off or on via the *Hand Mesh Visualization Modes* setting and *Hand Joint Visualization Modes* respectively.</span></span> <span data-ttu-id="8df25-124">Diese Einstellungen sind anwendungsmodusspezifisch, d. h., es ist möglich, einige Features im Editor zu aktivieren (z. B. um Fugen mit In-Editor-Simulationen zu sehen), während dieselben Features bei der Bereitstellung auf dem Gerät (in Player-Builds) deaktiviert sind.</span><span class="sxs-lookup"><span data-stu-id="8df25-124">These settings are application-mode specific, meaning it is possible to turn on some features while in editor (to see joints with in-editor simulation, for example) while having the same features turned off when deployed to device (in player builds).</span></span>

<span data-ttu-id="8df25-125">Beachten Sie, dass es im Allgemeinen empfohlen wird, die Hand-Fugenvisualisierung im Editor eingeschaltet zu haben (damit die In-Editor-Simulation zeigt, wo sich die Handgelenke befinden), und sowohl die Hand-Fugevisualisierung als auch die Handgittervisualisierung im Player ausgeschaltet zu haben (da sie zu einem Leistungstreffer führen).</span><span class="sxs-lookup"><span data-stu-id="8df25-125">Note that it's generally recommended to have hand joint visualization turned on in editor (so that in-editor simulation will show where the hand joints are), and to have both hand joint visualization and hand mesh visualization turned off in player (because they incur a performance hit).</span></span>

## <a name="scripting"></a><span data-ttu-id="8df25-126">Skripterstellung</span><span class="sxs-lookup"><span data-stu-id="8df25-126">Scripting</span></span>

<span data-ttu-id="8df25-127">Position und Drehung können vom Eingabesystem für jedes einzelne Handgelenk als angefordert [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) werden.</span><span class="sxs-lookup"><span data-stu-id="8df25-127">Position and rotation can be requested from the input system for each individual hand joint as a [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose).</span></span>

<span data-ttu-id="8df25-128">Alternativ ermöglicht das System den Zugriff auf [GameObjects,](https://docs.unity3d.com/ScriptReference/GameObject.html) die den Fugen folgen.</span><span class="sxs-lookup"><span data-stu-id="8df25-128">Alternatively the system allows access to [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) that follow the joints.</span></span> <span data-ttu-id="8df25-129">Dies kann nützlich sein, wenn ein anderes GameObject kontinuierlich ein Gemeinsames nachverfolgen soll.</span><span class="sxs-lookup"><span data-stu-id="8df25-129">This can be useful if another GameObject should track a joint continuously.</span></span>

<span data-ttu-id="8df25-130">Verfügbare Joints sind in der [`TrackedHandJoint`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedHandJoint) -Enum aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="8df25-130">Available joints are listed in the [`TrackedHandJoint`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedHandJoint) enum.</span></span>

> [!NOTE]
> <span data-ttu-id="8df25-131">Das gemeinsame Objekt wird zerstört, wenn die Handverfolgung verloren geht!</span><span class="sxs-lookup"><span data-stu-id="8df25-131">Joint object are destroyed when hand tracking is lost!</span></span> <span data-ttu-id="8df25-132">Stellen Sie sicher, dass alle Skripts, die das gemeinsame Objekt verwenden, den Fall ordnungsgemäß `null` behandeln, um Fehler zu vermeiden!</span><span class="sxs-lookup"><span data-stu-id="8df25-132">Make sure that any scripts using the joint object handle the `null` case gracefully to avoid errors!</span></span>

### <a name="accessing-a-given-hand-controller"></a><span data-ttu-id="8df25-133">Zugreifen auf einen bestimmten Handcontroller</span><span class="sxs-lookup"><span data-stu-id="8df25-133">Accessing a given hand controller</span></span>

<span data-ttu-id="8df25-134">Ein bestimmter Handcontroller ist häufig verfügbar, z. B. bei der Behandlung von Eingabeereignissen.</span><span class="sxs-lookup"><span data-stu-id="8df25-134">A specific hand controller is often available, e.g. when handling input events.</span></span> <span data-ttu-id="8df25-135">In diesem Fall können die gemeinsamen Daten über die Schnittstelle direkt vom Gerät angefordert [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) werden.</span><span class="sxs-lookup"><span data-stu-id="8df25-135">In this case the joint data can be requested directly from the device, using the [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) interface.</span></span>

#### <a name="polling-joint-pose-from-controller"></a><span data-ttu-id="8df25-136">Abruf der Gemeinsamen Pose vom Controller</span><span class="sxs-lookup"><span data-stu-id="8df25-136">Polling joint pose from controller</span></span>

<span data-ttu-id="8df25-137">Die [`TryGetJoint`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand.TryGetJoint*) Funktion gibt `false` zurück, wenn das angeforderte Joint aus irgendeinem Grund nicht verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="8df25-137">The [`TryGetJoint`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand.TryGetJoint*) function returns `false` if the requested joint is not available for some reason.</span></span> <span data-ttu-id="8df25-138">In diesem Fall ist die resultierende Pose [`MixedRealityPose.ZeroIdentity`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose.ZeroIdentity) .</span><span class="sxs-lookup"><span data-stu-id="8df25-138">In that case the resulting pose will be [`MixedRealityPose.ZeroIdentity`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose.ZeroIdentity).</span></span>

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

#### <a name="joint-transform-from-hand-visualizer"></a><span data-ttu-id="8df25-139">Gemeinsame Transformation aus der Handvis visualisieren</span><span class="sxs-lookup"><span data-stu-id="8df25-139">Joint transform from hand visualizer</span></span>

<span data-ttu-id="8df25-140">Gemeinsame Objekte können über die Controller-Schnellansicht [angefordert werden.](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController.Visualizer)</span><span class="sxs-lookup"><span data-stu-id="8df25-140">Joint objects can be requested from the [controller visualizer](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController.Visualizer).</span></span>

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

### <a name="simplified-joint-data-access"></a><span data-ttu-id="8df25-141">Vereinfachter gemeinsamer Datenzugriff</span><span class="sxs-lookup"><span data-stu-id="8df25-141">Simplified joint data access</span></span>

<span data-ttu-id="8df25-142">Wenn kein bestimmter Controller angegeben wird, werden Hilfsprogrammklassen für den komfortablen Zugriff auf Hand-Joint-Daten bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="8df25-142">If no specific controller is given then utility classes are provided for convenient access to hand joint data.</span></span> <span data-ttu-id="8df25-143">Diese Funktionen fordern gemeinsame Daten vom ersten verfügbaren Gerät an, das derzeit nachverfolgt wird.</span><span class="sxs-lookup"><span data-stu-id="8df25-143">These functions request joint data from the first available hand device currently tracked.</span></span>

#### <a name="polling-joint-pose-from-handjointutils"></a><span data-ttu-id="8df25-144">Polling joint pose from HandJointUtils</span><span class="sxs-lookup"><span data-stu-id="8df25-144">Polling joint pose from HandJointUtils</span></span>

<span data-ttu-id="8df25-145">[`HandJointUtils`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils) ist eine statische Klasse, die das erste aktive Gerät abfragt.</span><span class="sxs-lookup"><span data-stu-id="8df25-145">[`HandJointUtils`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils) is a static class that queries the first active hand device.</span></span>

```c#
if (HandJointUtils.TryGetJointPose(TrackedHandJoint.IndexTip, Handedness.Right, out MixedRealityPose pose))
{
    // ...
}
```

#### <a name="joint-transform-from-hand-joint-service"></a><span data-ttu-id="8df25-146">Gemeinsame Transformation aus handlichem gemeinsamen Dienst</span><span class="sxs-lookup"><span data-stu-id="8df25-146">Joint transform from hand joint service</span></span>

<span data-ttu-id="8df25-147">[`IMixedRealityHandJointService`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointService) behält einen permanenten Satz von [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) für die Nachverfolgung von Joints bei.</span><span class="sxs-lookup"><span data-stu-id="8df25-147">[`IMixedRealityHandJointService`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointService) keeps a persistent set of [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) for tracking joints.</span></span>

```c#
var handJointService = CoreServices.GetInputSystemDataProvider<IMixedRealityHandJointService>();
if (handJointService != null)
{
    Transform jointTransform = handJointService.RequestJointTransform(TrackedHandJoint.IndexTip, Handedness.Right);
    // ...
}
```

### <a name="hand-tracking-events"></a><span data-ttu-id="8df25-148">Handtrackingereignisse</span><span class="sxs-lookup"><span data-stu-id="8df25-148">Hand tracking events</span></span>

<span data-ttu-id="8df25-149">Das Eingabesystem stellt auch Ereignisse bereit, wenn das direkte Abfragen von Daten von Controllern nicht wünschenswert ist.</span><span class="sxs-lookup"><span data-stu-id="8df25-149">The input system provides events as well, if polling data from controllers directly is not desirable.</span></span>

#### <a name="joint-events"></a><span data-ttu-id="8df25-150">Gemeinsame Ereignisse</span><span class="sxs-lookup"><span data-stu-id="8df25-150">Joint events</span></span>

<span data-ttu-id="8df25-151">[`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) behandelt Updates von Gemeinsamen Positionen.</span><span class="sxs-lookup"><span data-stu-id="8df25-151">[`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) handles updates of joint positions.</span></span>

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

#### <a name="mesh-events"></a><span data-ttu-id="8df25-152">Mesh-Ereignisse</span><span class="sxs-lookup"><span data-stu-id="8df25-152">Mesh events</span></span>

<span data-ttu-id="8df25-153">[`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) behandelt Änderungen des artikulierten Handgitters.</span><span class="sxs-lookup"><span data-stu-id="8df25-153">[`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) handles changes of the articulated hand mesh.</span></span>

<span data-ttu-id="8df25-154">Beachten Sie, dass Handgitternetze standardmäßig nicht aktiviert sind.</span><span class="sxs-lookup"><span data-stu-id="8df25-154">Note that hand meshes are not enabled by default.</span></span>

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

## <a name="known-issues"></a><span data-ttu-id="8df25-155">Bekannte Probleme</span><span class="sxs-lookup"><span data-stu-id="8df25-155">Known issues</span></span>

### <a name="net-native"></a><span data-ttu-id="8df25-156">.NET systemeigen</span><span class="sxs-lookup"><span data-stu-id="8df25-156">.NET Native</span></span>

<span data-ttu-id="8df25-157">Derzeit gibt es ein bekanntes Problem mit Masterbuilds, die das .NET-Back-End verwenden.</span><span class="sxs-lookup"><span data-stu-id="8df25-157">There is currently a known issue with Master builds using the .NET backend.</span></span> <span data-ttu-id="8df25-158">In .NET Native können `IInspectable` Zeiger nicht mithilfe von von systemeigenem in verwalteten Code gemarshallt `Marshal.GetObjectForIUnknown` werden.</span><span class="sxs-lookup"><span data-stu-id="8df25-158">In .NET Native, `IInspectable` pointers cannot be marshaled from native to managed code using `Marshal.GetObjectForIUnknown`.</span></span> <span data-ttu-id="8df25-159">Das MRTK verwendet dies, um die `SpatialCoordinateSystem` abzurufen, um Hand- und Augendaten von der Plattform zu empfangen.</span><span class="sxs-lookup"><span data-stu-id="8df25-159">The MRTK uses this to obtain the `SpatialCoordinateSystem` in order to receive hand and eye data from the platform.</span></span>

<span data-ttu-id="8df25-160">Wir haben die DLL-Quelle als Problemumgehung für dieses Problem im [repository nativen Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit/tree/master/DotNetNativeWorkaround)bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="8df25-160">We've provided DLL source as a workaround for this issue, in [the native Mixed Reality Toolkit repo](https://github.com/microsoft/MixedRealityToolkit/tree/master/DotNetNativeWorkaround).</span></span> <span data-ttu-id="8df25-161">Befolgen Sie dort die Anweisungen in der README, und kopieren Sie die resultierenden Binärdateien in einen Plug-In-Ordner in Ihren Unity-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="8df25-161">Please follow the instructions in the README there and copy the resulting binaries into a Plugins folder in your Unity assets.</span></span> <span data-ttu-id="8df25-162">Danach löst das im MRTK bereitgestellte WindowsMixedRealityUtilities-Skript die Problemumgehung für Sie.</span><span class="sxs-lookup"><span data-stu-id="8df25-162">After that, the WindowsMixedRealityUtilities script provided in the MRTK will resolve the workaround for you.</span></span>

<span data-ttu-id="8df25-163">Wenn Sie eine eigene DLL erstellen oder diese Problemumgehung in eine vorhandene dll einschließen möchten, ist der Kern der Problemumgehung:</span><span class="sxs-lookup"><span data-stu-id="8df25-163">If you want to create your own DLL or include this workaround in an existing one, the core of the workaround is:</span></span>

```c++
extern "C" __declspec(dllexport) void __stdcall MarshalIInspectable(IUnknown* nativePtr, IUnknown** inspectable)
{
    *inspectable = nativePtr;
}
```

<span data-ttu-id="8df25-164">Und seine Verwendung in Ihrem C#-Unity-Code:</span><span class="sxs-lookup"><span data-stu-id="8df25-164">And its use in your C# Unity code:</span></span>

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
