---
title: Handtracking in Unreal
description: Erläutert die Verwendung der Hand Verfolgung in Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, Hand Verfolgung, Unreal, Unreal Engine 4, UE4, hololens, hololens 2, Mixed Reality, Entwicklung, Features, Dokumentation, Handbücher, holograms, Spieleentwicklung, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 4c66e2353c1e881c05541fd0fe9eafa553ea5c23
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609711"
---
# <a name="hand-tracking-in-unreal"></a><span data-ttu-id="d51a9-104">Handtracking in Unreal</span><span class="sxs-lookup"><span data-stu-id="d51a9-104">Hand tracking in Unreal</span></span>

<span data-ttu-id="d51a9-105">Das Hand Verfolgungssystem verwendet die Palmen und Finger der Person als Eingabe.</span><span class="sxs-lookup"><span data-stu-id="d51a9-105">The hand tracking system uses a person’s palms and fingers as input.</span></span> <span data-ttu-id="d51a9-106">Daten an Position und Drehung jedes Fingers, das gesamte Palmen und Handgesten sind verfügbar.</span><span class="sxs-lookup"><span data-stu-id="d51a9-106">Data on position and rotation of every finger, the entire palm, and hand gestures is available.</span></span> 

## <a name="hand-pose"></a><span data-ttu-id="d51a9-107">Hand darstellen</span><span class="sxs-lookup"><span data-stu-id="d51a9-107">Hand Pose</span></span>

<span data-ttu-id="d51a9-108">Hand darstellen ermöglicht Ihnen die Nachverfolgung und Verwendung der Hände und Finger der Benutzer als Eingabe.</span><span class="sxs-lookup"><span data-stu-id="d51a9-108">Hand pose lets you track and use the hands and fingers of your users as input.</span></span> <span data-ttu-id="d51a9-109">Sie können sowohl in Blueprints als auch C++ auf Überwachungsdaten zugreifen.</span><span class="sxs-lookup"><span data-stu-id="d51a9-109">You can access tracking data both in Blueprints and C++.</span></span> <span data-ttu-id="d51a9-110">Weitere technische Details finden Sie in der [Windows. perception. People. handpose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) -API von Unreal.</span><span class="sxs-lookup"><span data-stu-id="d51a9-110">You can find more technical details in Unreal's [Windows.Perception.People.HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) API.</span></span> <span data-ttu-id="d51a9-111">Die Unreal-API sendet die Daten als Koordinatensystem, wobei Ticks mit der Unreal-Engine synchronisiert werden.</span><span class="sxs-lookup"><span data-stu-id="d51a9-111">The Unreal API sends the data as a coordinate system, with ticks synchronized with the Unreal Engine.</span></span>

### <a name="understanding-the-bone-hierarchy"></a><span data-ttu-id="d51a9-112">Grundlegendes zur Knochen Hierarchie</span><span class="sxs-lookup"><span data-stu-id="d51a9-112">Understanding the bone hierarchy</span></span>

<span data-ttu-id="d51a9-113">Die `EWMRHandKeypoint` -Enumeration beschreibt die Knochen Hierarchie der Hand.</span><span class="sxs-lookup"><span data-stu-id="d51a9-113">The `EWMRHandKeypoint` enum describes the Hand’s bone hierarchy.</span></span> <span data-ttu-id="d51a9-114">Sie finden jeden Hand-keypoint, der in ihren Blaupausen aufgeführt ist:</span><span class="sxs-lookup"><span data-stu-id="d51a9-114">You can find each hand keypoint listed in your Blueprints:</span></span>

![Hand-keypoint-BP](images/hand-keypoint-bp.png)

<span data-ttu-id="d51a9-116">Die vollständige C++-Aufzählung ist im folgenden aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="d51a9-116">The full C++ enum is listed below:</span></span>
```cpp
enum class EWMRHandKeypoint : uint8
{
    Palm,
    Wrist,
    ThumbMetacarpal,
    ThumbProximal,
    ThumbDistal,
    ThumbTip,
    IndexMetacarpal,
    IndexProximal,
    IndexIntermediate,
    IndexDistal,
    IndexTip,
    MiddleMetacarpal,
    MiddleProximal,
    MiddleIntermediate,
    MiddleDistal,
    MiddleTip,
    RingMetacarpal,
    RingProximal,
    RingIntermediate,
    RingDistal,
    RingTip,
    LittleMetacarpal,
    LittleProximal,
    LittleIntermediate,
    LittleDistal,
    LittleTip
};
```

<span data-ttu-id="d51a9-117">Sie können die numerischen Werte für jeden enumerationsfall in der Tabelle " [Windows. perception. People. handjointkind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) " finden.</span><span class="sxs-lookup"><span data-stu-id="d51a9-117">You can find the numerical values for each enum case in the [Windows.Perception.People.HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) table.</span></span> <span data-ttu-id="d51a9-118">In der folgenden Abbildung ist das gesamte Hand Layout mit passenden Enumeration-Fällen dargestellt:</span><span class="sxs-lookup"><span data-stu-id="d51a9-118">The entire hand pose layout with matching enum cases is shown in the image below:</span></span>

![Hand Gerüst](../native/images/hand-skeleton.png)
 
### <a name="supporting-hand-tracking"></a><span data-ttu-id="d51a9-120">Unterstützende Hand Verfolgung</span><span class="sxs-lookup"><span data-stu-id="d51a9-120">Supporting Hand Tracking</span></span>

<span data-ttu-id="d51a9-121">Sie können die Hand Verfolgung in Blaupausen verwenden, indem Sie die Hand Verfolgung von Hand Nachverfolgung **> Windows Mixed Reality** **Hinzufügen** :</span><span class="sxs-lookup"><span data-stu-id="d51a9-121">You can use hand tracking in Blueprints by adding **Supports Hand Tracking** from **Hand Tracking > Windows Mixed Reality**:</span></span>

![Hand Tracking-BP](images/unreal/hand-tracking-bp.png)

<span data-ttu-id="d51a9-123">Diese Funktion gibt zurück, `true` Wenn die Hand Verfolgung auf dem Gerät unterstützt wird und die `false` Hand Nachverfolgung nicht verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="d51a9-123">This function returns `true` if hand tracking is supported on the device and `false` if hand tracking isn't available.</span></span>

![Unterstützt die Hand Überwachung von BP](images/unreal/supports-hand-tracking-bp.png)

<span data-ttu-id="d51a9-125">C++:</span><span class="sxs-lookup"><span data-stu-id="d51a9-125">C++:</span></span> 

<span data-ttu-id="d51a9-126">Schließen Sie `WindowsMixedRealityHandTrackingFunctionLibrary.h` ein.</span><span class="sxs-lookup"><span data-stu-id="d51a9-126">Include `WindowsMixedRealityHandTrackingFunctionLibrary.h`.</span></span>

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a><span data-ttu-id="d51a9-127">Erhalten von Hand Nachverfolgung</span><span class="sxs-lookup"><span data-stu-id="d51a9-127">Getting Hand Tracking</span></span>

<span data-ttu-id="d51a9-128">Mit **gethandjointtransform** können Sie räumliche Daten von Hand zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="d51a9-128">You can use **GetHandJointTransform** to return spatial data from the hand.</span></span> <span data-ttu-id="d51a9-129">Die Daten aktualisieren jeden Frame, aber wenn Sie sich innerhalb eines Frames befinden, werden die zurückgegebenen Werte zwischengespeichert.</span><span class="sxs-lookup"><span data-stu-id="d51a9-129">The data updates every frame, but if you're inside a frame the returned values are cached.</span></span> <span data-ttu-id="d51a9-130">Es wird aus Leistungsgründen nicht empfohlen, in dieser Funktion eine hohe Logik zu haben.</span><span class="sxs-lookup"><span data-stu-id="d51a9-130">It's not recommended to have heavy logic in this function for performance reasons.</span></span> 

![Hand Gelenk Transformation](images/unreal/get-hand-joint-transform.png)
 
<span data-ttu-id="d51a9-132">C++:</span><span class="sxs-lookup"><span data-stu-id="d51a9-132">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

<span data-ttu-id="d51a9-133">Im folgenden finden Sie eine Aufschlüsselung der Funktionsparameter von gethandjointtransform:</span><span class="sxs-lookup"><span data-stu-id="d51a9-133">Here's a breakdown of GetHandJointTransform's function parameters:</span></span>

* <span data-ttu-id="d51a9-134">**Hand** – kann die Benutzer Links oder rechts sein.</span><span class="sxs-lookup"><span data-stu-id="d51a9-134">**Hand** – can be the users left or right hand.</span></span>
* <span data-ttu-id="d51a9-135">**Keypoint** – der Knochen der Hand.</span><span class="sxs-lookup"><span data-stu-id="d51a9-135">**Keypoint** – the bone of the hand.</span></span> 
* <span data-ttu-id="d51a9-136">**Transformation** – Koordinaten und Ausrichtung der Basis von Bone.</span><span class="sxs-lookup"><span data-stu-id="d51a9-136">**Transform** – coordinates and orientation of bone’s base.</span></span> <span data-ttu-id="d51a9-137">Sie können die Basis des nächsten Knochens anfordern, um die Transformations Daten für das Ende eines Knochens zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="d51a9-137">You can request the base of the next bone to get the transform data for the end of a bone.</span></span> <span data-ttu-id="d51a9-138">Ein spezieller Tip-Bone gibt das Ende der distal-Tabelle an.</span><span class="sxs-lookup"><span data-stu-id="d51a9-138">A special Tip bone gives end of distal.</span></span> 
* <span data-ttu-id="d51a9-139">**RADIUS** – Radius der Basis des Knochens.</span><span class="sxs-lookup"><span data-stu-id="d51a9-139">**Radius** — radius of the base of the bone.</span></span>
* <span data-ttu-id="d51a9-140">**Rückgabewert** – true, wenn der Bereich in diesem Frame nachverfolgt wird, false, wenn der Knochen nicht nachverfolgt wird.</span><span class="sxs-lookup"><span data-stu-id="d51a9-140">**Return Value** — true if the bone is tracked this frame, false if the bone isn't tracked.</span></span>

## <a name="hand-live-link-animation"></a><span data-ttu-id="d51a9-141">Live Link Animation Hand</span><span class="sxs-lookup"><span data-stu-id="d51a9-141">Hand Live Link Animation</span></span>

<span data-ttu-id="d51a9-142">Hand stellen werden der Animation mithilfe des [Live Link-Plug](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html)-ins ausgesetzt.</span><span class="sxs-lookup"><span data-stu-id="d51a9-142">Hand poses are exposed to Animation using the [Live Link plugin](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).</span></span>

<span data-ttu-id="d51a9-143">Wenn die Windows Mixed Reality-und Live Link-Plug-ins aktiviert sind:</span><span class="sxs-lookup"><span data-stu-id="d51a9-143">If the Windows Mixed Reality and Live Link plugins are enabled:</span></span> 
1. <span data-ttu-id="d51a9-144">Wählen Sie **Window > Live Link** aus, um das Fenster Live Link-Editor zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="d51a9-144">Select **Window > Live Link** to open the Live Link editor window.</span></span> 
2. <span data-ttu-id="d51a9-145">**Quelle** auswählen und **Windows Mixed Reality-Hand Verfolgungs Quelle** aktivieren</span><span class="sxs-lookup"><span data-stu-id="d51a9-145">Select **Source** and enable **Windows Mixed Reality Hand Tracking Source**</span></span>

![Live Link Quelle](images/unreal/live-link-source.png)
 
<span data-ttu-id="d51a9-147">Nachdem Sie die Quelle aktiviert und ein Animations Objekt geöffnet haben, erweitern Sie den Abschnitt **Animation** auf der Registerkarte **Vorschau Szene** , um zusätzliche Optionen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="d51a9-147">After you enable the source and open an animation asset, expand the **Animation** section in the **Preview Scene** tab too see additional options.</span></span>

![Live Link Animation](images/unreal/live-link-animation.png)
 
<span data-ttu-id="d51a9-149">Die Hand Animations Hierarchie ist identisch mit der in `EWMRHandKeypoint` .</span><span class="sxs-lookup"><span data-stu-id="d51a9-149">The hand animation hierarchy is the same as in `EWMRHandKeypoint`.</span></span> <span data-ttu-id="d51a9-150">Die Animation kann mithilfe von **windowsmixedrealityhandtrackinglebinkremapasset** neu zugewiesen werden:</span><span class="sxs-lookup"><span data-stu-id="d51a9-150">Animation can be retargeted using **WindowsMixedRealityHandTrackingLiveLinkRemapAsset**:</span></span>

![Live Link Animation 2](images/unreal/live-link-animation2.png)
 
<span data-ttu-id="d51a9-152">Sie kann auch im Editor untergeordnet werden:</span><span class="sxs-lookup"><span data-stu-id="d51a9-152">It can also be subclassed in the editor:</span></span>

![Live Link Neuzuordnung](images/unreal/live-link-remap.png)
 
## <a name="accessing-hand-mesh-data"></a><span data-ttu-id="d51a9-154">Zugreifen auf Hand Mesh-Daten</span><span class="sxs-lookup"><span data-stu-id="d51a9-154">Accessing Hand Mesh Data</span></span>

![Hand Netz](images/unreal/hand-mesh.png)

<span data-ttu-id="d51a9-156">Bevor Sie auf Hand Netz Daten zugreifen können, müssen Sie folgende Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="d51a9-156">Before you can access hand mesh data, you'll need to:</span></span>
- <span data-ttu-id="d51a9-157">Wählen Sie das Objekt " **arsessionconfig** " aus, erweitern Sie die Einstellungen für " **AR Settings-> World Mapping** ", und aktivieren Sie die Option **Mesh-Daten aus der**</span><span class="sxs-lookup"><span data-stu-id="d51a9-157">Select your **ARSessionConfig** asset, expand the **AR Settings -> World Mapping** settings, and check **Generate Mesh Data from Tracked Geometry**.</span></span> 

<span data-ttu-id="d51a9-158">Unten sind die standardmesh-Parameter aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="d51a9-158">Below are the default mesh parameters:</span></span>

1.  <span data-ttu-id="d51a9-159">Netzdaten für Okklusion verwenden</span><span class="sxs-lookup"><span data-stu-id="d51a9-159">Use Mesh Data for Occlusion</span></span>
2.  <span data-ttu-id="d51a9-160">Konflikt für Mesh-Daten generieren</span><span class="sxs-lookup"><span data-stu-id="d51a9-160">Generate Collision for Mesh Data</span></span>
3.  <span data-ttu-id="d51a9-161">Navigations Gitter für Mesh-Daten generieren</span><span class="sxs-lookup"><span data-stu-id="d51a9-161">Generate Nav Mesh for Mesh Data</span></span>
4.  <span data-ttu-id="d51a9-162">Gitternetz Daten in Wireframe Renderingparameter – Debug</span><span class="sxs-lookup"><span data-stu-id="d51a9-162">Render Mesh Data in Wireframe – debug parameter that shows generated mesh</span></span>

<span data-ttu-id="d51a9-163">Diese Parameterwerte werden als Gitter-und Hand Netz Standardwerte verwendet.</span><span class="sxs-lookup"><span data-stu-id="d51a9-163">These parameter values are used as the spatial mapping mesh and hand mesh defaults.</span></span> <span data-ttu-id="d51a9-164">Sie können Sie jederzeit in Blaupausen oder Code für ein beliebiges Mesh ändern.</span><span class="sxs-lookup"><span data-stu-id="d51a9-164">You can change them at any time in Blueprints or code for any mesh.</span></span>

### <a name="c-api-reference"></a><span data-ttu-id="d51a9-165">C++-API-Referenz</span><span class="sxs-lookup"><span data-stu-id="d51a9-165">C++ API Reference</span></span> 
<span data-ttu-id="d51a9-166">Verwenden `EEARObjectClassification` Sie, um Hand gitterwerte in allen nachverfolgbare-Objekten zu suchen.</span><span class="sxs-lookup"><span data-stu-id="d51a9-166">Use `EEARObjectClassification` to find hand mesh values in all trackable objects.</span></span>
```cpp
enum class EARObjectClassification : uint8
{
    // Other types 
    HandMesh,
};
```

<span data-ttu-id="d51a9-167">Die folgenden Delegaten werden aufgerufen, wenn das System ein ausführbares Objekt erkennt, einschließlich eines Hand Netzes.</span><span class="sxs-lookup"><span data-stu-id="d51a9-167">The following delegates are called when the system detects any trackable object, including a hand mesh.</span></span> 

```cpp
class FARSupportInterface 
{
    public:
    // Other params 
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

<span data-ttu-id="d51a9-168">Stellen Sie sicher, dass die Delegathandler der folgenden Funktions Signatur folgen:</span><span class="sxs-lookup"><span data-stu-id="d51a9-168">Make sure your delegate handlers follow the function signature below:</span></span>

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

<span data-ttu-id="d51a9-169">Sie können über die folgenden Schritte auf Mesh-Daten zugreifen  `UARTrackedGeometry::GetUnderlyingMesh` :</span><span class="sxs-lookup"><span data-stu-id="d51a9-169">You can access mesh data through the  `UARTrackedGeometry::GetUnderlyingMesh`:</span></span>

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```


### <a name="blueprint-api-reference"></a><span data-ttu-id="d51a9-170">Referenz zur Blueprint-API</span><span class="sxs-lookup"><span data-stu-id="d51a9-170">Blueprint API Reference</span></span>

<span data-ttu-id="d51a9-171">So arbeiten Sie mit Hand-Meshes in Blaupausen:</span><span class="sxs-lookup"><span data-stu-id="d51a9-171">To work with Hand Meshes in Blueprints:</span></span>
1. <span data-ttu-id="d51a9-172">Hinzufügen einer **artrackablenotify** -Komponente zu einem Blueprint-Actor</span><span class="sxs-lookup"><span data-stu-id="d51a9-172">Add an **ARTrackableNotify** Component to a Blueprint actor</span></span>

![Meldung zu einem darstellbaren Element](images/unreal/ar-trackable-notify.png)
 
2. <span data-ttu-id="d51a9-174">Wechseln Sie zum **Detail** Panel, und erweitern Sie den Abschnitt **Ereignisse** .</span><span class="sxs-lookup"><span data-stu-id="d51a9-174">Go to the **Details** panel and expand the **Events** section.</span></span> 

![Artrackable Benachrichtigen 2](images/unreal/ar-trackable-notify2.png)
 
3. <span data-ttu-id="d51a9-176">Überschreiben Sie beim Hinzufügen/Aktualisieren/Entfernen der überwachten Geometrie mit den folgenden Knoten im Ereignis Diagramm:</span><span class="sxs-lookup"><span data-stu-id="d51a9-176">Overwrite On Add/Update/Remove Tracked Geometry with the following nodes in your Event Graph:</span></span>

![Bei der über sichtbaren Benachrichtigung](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a><span data-ttu-id="d51a9-178">Hand Strahlen</span><span class="sxs-lookup"><span data-stu-id="d51a9-178">Hand Rays</span></span>

<span data-ttu-id="d51a9-179">Sie können einen Hand Strahl als Zeigegerät sowohl in C++ als auch in Blueprints verwenden, das die [Windows. UI. Input. Spatial. spatialpointerinteraktionsourcepose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) -API verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="d51a9-179">You can use a hand ray as a pointing device in both C++ and Blueprints, which exposes the [Windows.UI.Input.Spatial.SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) API.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d51a9-180">Da alle Funktions Ergebnisse jeden Frame ändern, werden Sie alle aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="d51a9-180">Since all function results change every frame, they're all made callable.</span></span> <span data-ttu-id="d51a9-181">Weitere Informationen zu reinen und impformen oder Aufruf baren Funktionen finden Sie in der Blueprint-Benutzer-GUID für [Funktionen](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure).</span><span class="sxs-lookup"><span data-stu-id="d51a9-181">For more information about pure and impure or callable functions, see the Blueprint user guid on [functions](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure).</span></span>

<span data-ttu-id="d51a9-182">Um Hand Abdrücke in Blaupausen zu verwenden, suchen Sie nach den Aktionen unter **Windows Mixed Reality HMD**:</span><span class="sxs-lookup"><span data-stu-id="d51a9-182">To use Hand Rays in Blueprints, search for any of the actions under **Windows Mixed Reality HMD**:</span></span>

![Hand Strahlen-BP](images/unreal/hand-rays-bp.png)
 
<span data-ttu-id="d51a9-184">Wenn Sie in C++ auf Sie zugreifen möchten, schließen Sie am `WindowsMixedRealityFunctionLibrary.h` Anfang der aufrufenden Codedatei ein.</span><span class="sxs-lookup"><span data-stu-id="d51a9-184">To access them in C++, include `WindowsMixedRealityFunctionLibrary.h` to the top of your calling code file.</span></span>

### <a name="enum"></a><span data-ttu-id="d51a9-185">Enumeration</span><span class="sxs-lookup"><span data-stu-id="d51a9-185">Enum</span></span>

<span data-ttu-id="d51a9-186">Sie haben auch Zugriff auf die Eingabe Fälle unter **ehmdinputcontrollerbuttons**, die in Blaupausen verwendet werden können:</span><span class="sxs-lookup"><span data-stu-id="d51a9-186">You also have access to input cases under **EHMDInputControllerButtons**, which can be used in Blueprints:</span></span>

![Eingabe Controller-Schaltflächen](images/unreal/input-controller-buttons.png)

<span data-ttu-id="d51a9-188">Verwenden Sie für den Zugriff in C++ die `EHMDInputControllerButtons` Enumerationsklasse:</span><span class="sxs-lookup"><span data-stu-id="d51a9-188">For access in C++, use the `EHMDInputControllerButtons` enum class:</span></span>
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

<span data-ttu-id="d51a9-189">Im folgenden finden Sie eine Aufschlüsselung der beiden anwendbaren Aufzählungs Fälle:</span><span class="sxs-lookup"><span data-stu-id="d51a9-189">Below is a breakdown of the two applicable enum cases:</span></span>

* <span data-ttu-id="d51a9-190">**Select** -User hat Select-Ereignis ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="d51a9-190">**Select** - User triggered Select event.</span></span> 
    * <span data-ttu-id="d51a9-191">Ausgelöst in hololens 2 durch Luft tippen, Überblicks und Commit oder durch "Select" mit aktivierter [Spracheingabe](unreal-voice-input.md) .</span><span class="sxs-lookup"><span data-stu-id="d51a9-191">Triggered in HoloLens 2 by air-tap, gaze, and commit, or by saying “Select” with [voice input](unreal-voice-input.md) enabled.</span></span> 
* <span data-ttu-id="d51a9-192">Das von Benutzern ausgelöste Ereignis **zum Erfassen von** Ereignissen.</span><span class="sxs-lookup"><span data-stu-id="d51a9-192">**Grasp** - User triggered Grasp event.</span></span> 
    * <span data-ttu-id="d51a9-193">Wird in hololens 2 ausgelöst, indem die Finger des Benutzers in einem Hologram geschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="d51a9-193">Triggered in HoloLens 2 by closing the user’s fingers on a hologram.</span></span> 

<span data-ttu-id="d51a9-194">Sie können auf den Überwachungs Status Ihres Hand Netzes in C++ über die unten gezeigte Aufzählung zugreifen `EHMDTrackingStatus` :</span><span class="sxs-lookup"><span data-stu-id="d51a9-194">You can access the tracking status of your hand mesh in C++ through the `EHMDTrackingStatus` enum shown below:</span></span>

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

<span data-ttu-id="d51a9-195">Im folgenden finden Sie eine Aufschlüsselung der beiden anwendbaren Aufzählungs Fälle:</span><span class="sxs-lookup"><span data-stu-id="d51a9-195">Below is a breakdown of the two applicable enum cases:</span></span>

* <span data-ttu-id="d51a9-196">**Notverfolgt** – die Hand ist nicht sichtbar.</span><span class="sxs-lookup"><span data-stu-id="d51a9-196">**NotTracked** –- the hand isn’t visible</span></span>
* <span data-ttu-id="d51a9-197">Nach **verfolgte** –: die Hand ist vollständig nachverfolgt.</span><span class="sxs-lookup"><span data-stu-id="d51a9-197">**Tracked** –- the hand is fully tracked</span></span>

### <a name="struct"></a><span data-ttu-id="d51a9-198">Struktur</span><span class="sxs-lookup"><span data-stu-id="d51a9-198">Struct</span></span>

<span data-ttu-id="d51a9-199">Die pointerposeinfo-Struktur kann Ihnen Informationen zu den folgenden Daten liefern:</span><span class="sxs-lookup"><span data-stu-id="d51a9-199">The PointerPoseInfo struct can give you information on the following hand data:</span></span>

* <span data-ttu-id="d51a9-200">**Ursprung** – Ursprung der Hand</span><span class="sxs-lookup"><span data-stu-id="d51a9-200">**Origin** – origin of the hand</span></span>
* <span data-ttu-id="d51a9-201">**Richtung** – Richtung der Hand</span><span class="sxs-lookup"><span data-stu-id="d51a9-201">**Direction** – direction of the hand</span></span>
* <span data-ttu-id="d51a9-202">**Up** – Up Vector of the Hand</span><span class="sxs-lookup"><span data-stu-id="d51a9-202">**Up** – up vector of the hand</span></span>
* <span data-ttu-id="d51a9-203">**Ausrichtung** – Ausrichtung Quaternion</span><span class="sxs-lookup"><span data-stu-id="d51a9-203">**Orientation** – orientation quaternion</span></span> 
* <span data-ttu-id="d51a9-204">**Überwachungs Status** – aktueller Überwachungs Status</span><span class="sxs-lookup"><span data-stu-id="d51a9-204">**Tracking Status** – current tracking status</span></span>

<span data-ttu-id="d51a9-205">Sie können auf die pointerposeinfo-Struktur über Blaupausen zugreifen, wie unten dargestellt:</span><span class="sxs-lookup"><span data-stu-id="d51a9-205">You can access the PointerPoseInfo struct through Blueprints, as shown below:</span></span>

![Zeiger stellen Informationen BP dar](images/unreal/pointer-pose-info-bp.png)

<span data-ttu-id="d51a9-207">Oder mit C++:</span><span class="sxs-lookup"><span data-stu-id="d51a9-207">Or with C++:</span></span>

```cpp
struct FPointerPoseInfo
{
    FVector Origin;
    FVector Direction;
    FVector Up;
    FQuat Orientation;
    EHMDTrackingStatus TrackingStatus;
};
```

### <a name="functions"></a><span data-ttu-id="d51a9-208">Functions</span><span class="sxs-lookup"><span data-stu-id="d51a9-208">Functions</span></span>

<span data-ttu-id="d51a9-209">Alle unten aufgeführten Funktionen können für jeden Frame aufgerufen werden, der eine kontinuierliche Überwachung ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="d51a9-209">All of the functions listed below can be called on every frame, which allows continuous monitoring.</span></span> 

1. <span data-ttu-id="d51a9-210">**Get Pointer Pose Info** gibt alle Informationen über die Richtung des Hand Gers im aktuellen Frame zurück.</span><span class="sxs-lookup"><span data-stu-id="d51a9-210">**Get Pointer Pose Info** returns complete information about the hand ray direction in the current frame.</span></span> 

<span data-ttu-id="d51a9-211">Karte</span><span class="sxs-lookup"><span data-stu-id="d51a9-211">Blueprint:</span></span>

![Informationen zum Darstellen von Zeigern](images/unreal/get-pointer-pose-info.png)

<span data-ttu-id="d51a9-213">C++:</span><span class="sxs-lookup"><span data-stu-id="d51a9-213">C++:</span></span> 
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. <span data-ttu-id="d51a9-214">**Ist** "-Wert" gibt "true" zurück, wenn die Hand im aktuellen Frame erfasst wird.</span><span class="sxs-lookup"><span data-stu-id="d51a9-214">**Is Grasped** returns true if the hand is grasped in the current frame.</span></span>

<span data-ttu-id="d51a9-215">Karte</span><span class="sxs-lookup"><span data-stu-id="d51a9-215">Blueprint:</span></span>

![Erfasste BP](images/unreal/is-grasped-bp.png)

<span data-ttu-id="d51a9-217">C++:</span><span class="sxs-lookup"><span data-stu-id="d51a9-217">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
 
3. <span data-ttu-id="d51a9-218">**Ist SELECT gedrückt** gibt true zurück, wenn der Benutzer SELECT im aktuellen Frame ausgelöst hat.</span><span class="sxs-lookup"><span data-stu-id="d51a9-218">**Is Select Pressed** returns true if the user triggered Select in the current frame.</span></span>

<span data-ttu-id="d51a9-219">Karte</span><span class="sxs-lookup"><span data-stu-id="d51a9-219">Blueprint:</span></span>

![Ist SELECT-Taste für BP](images/unreal/is-select-pressed-bp.png)

<span data-ttu-id="d51a9-221">C++:</span><span class="sxs-lookup"><span data-stu-id="d51a9-221">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. <span data-ttu-id="d51a9-222">**Wird auf die Schaltfläche "wird geklickt** " zurückgegeben, wenn das Ereignis oder die Schaltfläche im aktuellen Frame ausgelöst wird</span><span class="sxs-lookup"><span data-stu-id="d51a9-222">**Is Button Clicked** returns true if the event or button is triggered in the current frame.</span></span>

<span data-ttu-id="d51a9-223">Karte</span><span class="sxs-lookup"><span data-stu-id="d51a9-223">Blueprint:</span></span>

![Ist Schaltfläche, auf die ein](images/unreal/is-button-clicked-bp.png)

<span data-ttu-id="d51a9-225">C++:</span><span class="sxs-lookup"><span data-stu-id="d51a9-225">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. <span data-ttu-id="d51a9-226">**Get Controller Tracking Status** gibt den verfolgungsstatus im aktuellen Frame zurück.</span><span class="sxs-lookup"><span data-stu-id="d51a9-226">**Get Controller Tracking Status** returns the tracking status in the current frame.</span></span>

<span data-ttu-id="d51a9-227">Karte</span><span class="sxs-lookup"><span data-stu-id="d51a9-227">Blueprint:</span></span>

![Controller-Überwachungs Status-BP erhalten](images/unreal/get-controller-tracking-status-bp.png)

<span data-ttu-id="d51a9-229">C++:</span><span class="sxs-lookup"><span data-stu-id="d51a9-229">C++:</span></span>
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```

## <a name="gestures"></a><span data-ttu-id="d51a9-230">Gesten</span><span class="sxs-lookup"><span data-stu-id="d51a9-230">Gestures</span></span>

<span data-ttu-id="d51a9-231">Hololens 2 verfolgt räumliche Gesten, was bedeutet, dass Sie diese Gesten als Eingabe erfassen können.</span><span class="sxs-lookup"><span data-stu-id="d51a9-231">The HoloLens 2 tracks spatial gestures, which means you can capture those gestures as input.</span></span> <span data-ttu-id="d51a9-232">Weitere Informationen zu Gesten finden Sie im Artikel zur [grundlegenden Verwendung von hololens 2](https://docs.microsoft.com/hololens/hololens2-basic-usage) .</span><span class="sxs-lookup"><span data-stu-id="d51a9-232">You can find more details about gestures are the [HoloLens 2 Basic Usage](https://docs.microsoft.com/hololens/hololens2-basic-usage) document.</span></span>

<span data-ttu-id="d51a9-233">Sie finden die Blueprint-Funktion in unter **Windows Mixed Reality Spatial Input** und die C++-Funktion, indem Sie `WindowsMixedRealitySpatialInputFunctionLibrary.h` Ihre aufrufende Codedatei hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="d51a9-233">You can find the Blueprint function in under **Windows Mixed Reality Spatial Input**, and the C++ function by adding `WindowsMixedRealitySpatialInputFunctionLibrary.h` in your calling code file.</span></span>

![Erfassungs Gesten](images/unreal/capture-gestures.png)

### <a name="enum"></a><span data-ttu-id="d51a9-235">Enumeration</span><span class="sxs-lookup"><span data-stu-id="d51a9-235">Enum</span></span>
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
<span data-ttu-id="d51a9-236">Karte</span><span class="sxs-lookup"><span data-stu-id="d51a9-236">Blueprint:</span></span> 

![Gesten-Typ](images/unreal/gesture-type.png)

<span data-ttu-id="d51a9-238">C++:</span><span class="sxs-lookup"><span data-stu-id="d51a9-238">C++:</span></span>
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a><span data-ttu-id="d51a9-239">Funktion</span><span class="sxs-lookup"><span data-stu-id="d51a9-239">Function</span></span>
<span data-ttu-id="d51a9-240">Sie können die Gesten Erfassung mit der-Funktion aktivieren und deaktivieren `CaptureGestures` .</span><span class="sxs-lookup"><span data-stu-id="d51a9-240">You can enable and disable gesture capture with the `CaptureGestures` function.</span></span> <span data-ttu-id="d51a9-241">Wenn eine aktivierte Geste Eingabeereignisse auslöst, gibt die Funktion zurück, `true` Wenn die Gesten Erfassung erfolgreich war, und, `false` Wenn ein Fehler vorliegt.</span><span class="sxs-lookup"><span data-stu-id="d51a9-241">When an enabled gesture fires input events, the function returns `true` if gesture capture succeeded, and `false` if there's an error.</span></span>

<span data-ttu-id="d51a9-242">Karte</span><span class="sxs-lookup"><span data-stu-id="d51a9-242">Blueprint:</span></span>

![Erfassungs Gesten BP](images/unreal/capture-gestures-bp.png)

<span data-ttu-id="d51a9-244">C++:</span><span class="sxs-lookup"><span data-stu-id="d51a9-244">C++:</span></span>
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false, 
    bool Hold = false, 
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None, 
    bool NavigationAxisX = true, 
    bool NavigationAxisY = true, 
    bool NavigationAxisZ = true);
```

<span data-ttu-id="d51a9-245">Im folgenden finden Sie wichtige Ereignisse, die in Blueprints und C++: Key-Ereignisse zu finden sind. ![](images/unreal/key-events.png)</span><span class="sxs-lookup"><span data-stu-id="d51a9-245">The following are key events, which you can find in Blueprints and C++: ![Key Events](images/unreal/key-events.png)</span></span>

![Schlüsselereignisse 2](images/unreal/key-events2.png)
```cpp
const FKey FSpatialInputKeys::TapGesture(TapGestureName);
const FKey FSpatialInputKeys::DoubleTapGesture(DoubleTapGestureName);
const FKey FSpatialInputKeys::HoldGesture(HoldGestureName);

const FKey FSpatialInputKeys::LeftTapGesture(LeftTapGestureName);
const FKey FSpatialInputKeys::LeftDoubleTapGesture(LeftDoubleTapGestureName);
const FKey FSpatialInputKeys::LeftHoldGesture(LeftHoldGestureName);

const FKey FSpatialInputKeys::RightTapGesture(RightTapGestureName);
const FKey FSpatialInputKeys::RightDoubleTapGesture(RightDoubleTapGestureName);
const FKey FSpatialInputKeys::RightHoldGesture(RightHoldGestureName);

const FKey FSpatialInputKeys::LeftManipulationGesture(LeftManipulationGestureName);
const FKey FSpatialInputKeys::LeftManipulationXGesture(LeftManipulationXGestureName);
const FKey FSpatialInputKeys::LeftManipulationYGesture(LeftManipulationYGestureName);
const FKey FSpatialInputKeys::LeftManipulationZGesture(LeftManipulationZGestureName);

const FKey FSpatialInputKeys::LeftNavigationGesture(LeftNavigationGestureName);
const FKey FSpatialInputKeys::LeftNavigationXGesture(LeftNavigationXGestureName);
const FKey FSpatialInputKeys::LeftNavigationYGesture(LeftNavigationYGestureName);
const FKey FSpatialInputKeys::LeftNavigationZGesture(LeftNavigationZGestureName);


const FKey FSpatialInputKeys::RightManipulationGesture(RightManipulationGestureName);
const FKey FSpatialInputKeys::RightManipulationXGesture(RightManipulationXGestureName);
const FKey FSpatialInputKeys::RightManipulationYGesture(RightManipulationYGestureName);
const FKey FSpatialInputKeys::RightManipulationZGesture(RightManipulationZGestureName);

const FKey FSpatialInputKeys::RightNavigationGesture(RightNavigationGestureName);
const FKey FSpatialInputKeys::RightNavigationXGesture(RightNavigationXGestureName);
const FKey FSpatialInputKeys::RightNavigationYGesture(RightNavigationYGestureName);
const FKey FSpatialInputKeys::RightNavigationZGesture(RightNavigationZGestureName);
```

## <a name="next-development-checkpoint"></a><span data-ttu-id="d51a9-247">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="d51a9-247">Next Development Checkpoint</span></span>

<span data-ttu-id="d51a9-248">Wenn Sie die unwirkliche Entwicklungs Journey befolgen, die wir festgelegt haben, befinden Sie sich mitten in der Untersuchung der mrtk Core-Bausteine.</span><span class="sxs-lookup"><span data-stu-id="d51a9-248">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="d51a9-249">Von hier aus können Sie mit dem nächsten Baustein fortfahren:</span><span class="sxs-lookup"><span data-stu-id="d51a9-249">From here, you can continue to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="d51a9-250">Lokale Raumanker</span><span class="sxs-lookup"><span data-stu-id="d51a9-250">Local Spatial Anchors</span></span>](unreal-spatial-anchors.md)

<span data-ttu-id="d51a9-251">Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:</span><span class="sxs-lookup"><span data-stu-id="d51a9-251">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d51a9-252">HoloLens-Kamera</span><span class="sxs-lookup"><span data-stu-id="d51a9-252">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="d51a9-253">Sie können jederzeit zu den [Prüfpunkten für die Unreal-Entwicklung](unreal-development-overview.md#2-core-building-blocks) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="d51a9-253">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>