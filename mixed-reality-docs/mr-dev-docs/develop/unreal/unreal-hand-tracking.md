---
title: Handtracking in Unreal
description: Erfahren Sie, wie Sie Hand nach Verfolgungs Eingaben, Pose, Hand-Meshes und Live Link Animationen in Unreal Mixed Reality-Apps verwenden.
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, Hand Verfolgung, Unreal, Unreal Engine 4, UE4, hololens, hololens 2, Mixed Reality, Entwicklung, Features, Dokumentation, Handbücher, holograms, Spieleentwicklung, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: e482c93233348325736d2c224788e9174c1f3b67
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010160"
---
# <a name="hand-tracking-in-unreal"></a><span data-ttu-id="9f0b1-104">Handtracking in Unreal</span><span class="sxs-lookup"><span data-stu-id="9f0b1-104">Hand tracking in Unreal</span></span>

<span data-ttu-id="9f0b1-105">Das Hand Verfolgungssystem verwendet die Palmen und Finger der Person als Eingabe.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-105">The hand tracking system uses a person’s palms and fingers as input.</span></span> <span data-ttu-id="9f0b1-106">Daten an Position und Drehung jedes Fingers, das gesamte Palmen und Handgesten sind verfügbar.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-106">Data on position and rotation of every finger, the entire palm, and hand gestures is available.</span></span> <span data-ttu-id="9f0b1-107">Ab Unreal 4,26 basiert die Hand Verfolgung auf dem Unreal headmounteddisplay-Plug-in und verwendet eine gemeinsame API für alle XR-Plattformen und-Geräte.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-107">Starting in Unreal 4.26, hand tracking is based on the Unreal HeadMountedDisplay plugin and uses a common API across all XR platforms and devices.</span></span> <span data-ttu-id="9f0b1-108">Die Funktionalität ist für Windows Mixed Reality und openxr Systems identisch.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-108">Functionality is the same for both Windows Mixed Reality and OpenXR systems.</span></span>

## <a name="hand-pose"></a><span data-ttu-id="9f0b1-109">Hand darstellen</span><span class="sxs-lookup"><span data-stu-id="9f0b1-109">Hand pose</span></span>

<span data-ttu-id="9f0b1-110">Hand darstellen ermöglicht Ihnen die Nachverfolgung und Verwendung der Hände und Finger der Benutzer als Eingabe, auf die in Blueprints und C++ zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-110">Hand pose lets you track and use the hands and fingers of your users as input, which can be accessed in both Blueprints and C++.</span></span> <span data-ttu-id="9f0b1-111">Die Unreal-API sendet die Daten als Koordinatensystem, wobei Ticks mit der Unreal-Engine synchronisiert werden.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-111">The Unreal API sends the data as a coordinate system, with ticks synchronized with the Unreal Engine.</span></span>

![Hand Gerüst](../native/images/hand-skeleton.png)

[!INCLUDE[](includes/tabs-tracking-hand-pose.md)]

## <a name="hand-live-link-animation"></a><span data-ttu-id="9f0b1-113">Live Link Animation Hand</span><span class="sxs-lookup"><span data-stu-id="9f0b1-113">Hand Live Link Animation</span></span>

<span data-ttu-id="9f0b1-114">Hand stellen werden der Animation mithilfe des [Live Link-Plug](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html)-ins ausgesetzt.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-114">Hand poses are exposed to Animation using the [Live Link plugin](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).</span></span>

<span data-ttu-id="9f0b1-115">Wenn die Windows Mixed Reality-und Live Link-Plug-ins aktiviert sind:</span><span class="sxs-lookup"><span data-stu-id="9f0b1-115">If the Windows Mixed Reality and Live Link plugins are enabled:</span></span>
1. <span data-ttu-id="9f0b1-116">Wählen Sie **Window > Live Link** aus, um das Fenster Live Link-Editor zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-116">Select **Window > Live Link** to open the Live Link editor window.</span></span>
2. <span data-ttu-id="9f0b1-117">**Quelle** auswählen und **Windows Mixed Reality-Hand Verfolgungs Quelle** aktivieren</span><span class="sxs-lookup"><span data-stu-id="9f0b1-117">Select **Source** and enable **Windows Mixed Reality Hand Tracking Source**</span></span>

![Live Link Quelle](images/unreal/live-link-source.png)

<span data-ttu-id="9f0b1-119">Nachdem Sie die Quelle aktiviert und ein Animations Objekt geöffnet haben, erweitern Sie den Abschnitt **Animation** auf der Registerkarte **Vorschau Szene** , um zusätzliche Optionen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-119">After you enable the source and open an animation asset, expand the **Animation** section in the **Preview Scene** tab too see additional options.</span></span>

![Live Link Animation](images/unreal/live-link-animation.png)

<span data-ttu-id="9f0b1-121">Die Hand Animations Hierarchie ist identisch mit der in `EWMRHandKeypoint` .</span><span class="sxs-lookup"><span data-stu-id="9f0b1-121">The hand animation hierarchy is the same as in `EWMRHandKeypoint`.</span></span> <span data-ttu-id="9f0b1-122">Die Animation kann mithilfe von **windowsmixedrealityhandtrackinglebinkremapasset** neu zugewiesen werden:</span><span class="sxs-lookup"><span data-stu-id="9f0b1-122">Animation can be retargeted using **WindowsMixedRealityHandTrackingLiveLinkRemapAsset**:</span></span>

![Live Link Animation 2](images/unreal/live-link-animation2.png)

<span data-ttu-id="9f0b1-124">Sie kann auch im Editor untergeordnet werden:</span><span class="sxs-lookup"><span data-stu-id="9f0b1-124">It can also be subclassed in the editor:</span></span>

![Live Link Neuzuordnung](images/unreal/live-link-remap.png)

## <a name="hand-mesh"></a><span data-ttu-id="9f0b1-126">Hand Netz</span><span class="sxs-lookup"><span data-stu-id="9f0b1-126">Hand Mesh</span></span>

### <a name="hand-mesh-as-a-tracked-geometry"></a><span data-ttu-id="9f0b1-127">Hand Mesh als nach verfolgte Geometrie</span><span class="sxs-lookup"><span data-stu-id="9f0b1-127">Hand Mesh as a Tracked Geometry</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9f0b1-128">Zum Abrufen von Hand Netzen als nach verfolgte Geometrie in openxr müssen Sie **Set use Hand Mesh** with **aktivierte Tracking Geometry** aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-128">Getting hand meshes as a tracked geometry in OpenXR requires you to call **Set Use Hand Mesh** with **Enabled Tracking Geometry**.</span></span>

<span data-ttu-id="9f0b1-129">Um diesen Modus zu aktivieren, müssen Sie **Set use Hand Mesh** with **aktivierte nach Verfolgungs Geometrie** verwenden:</span><span class="sxs-lookup"><span data-stu-id="9f0b1-129">To enable that mode you should call **Set Use Hand Mesh** with **Enabled Tracking Geometry**:</span></span>

![Blaupause der Ereignis Start Wiedergabe, verbunden mit Set use Hand Mesh-Funktion mit aktiviertem nach Verfolgungs Geometrie Modus](images/unreal-hand-tracking-img-08.png)

> [!NOTE]
> <span data-ttu-id="9f0b1-131">Beide Modi können nicht gleichzeitig aktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-131">It’s not possible for both modes to be enabled at the same time.</span></span> <span data-ttu-id="9f0b1-132">Wenn Sie eins aktivieren, wird das andere automatisch deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-132">If you enable one, the other is automatically disabled.</span></span>

### <a name="accessing-hand-mesh-data"></a><span data-ttu-id="9f0b1-133">Zugreifen auf Hand Mesh-Daten</span><span class="sxs-lookup"><span data-stu-id="9f0b1-133">Accessing Hand Mesh Data</span></span>

![Hand Netz](images/unreal/hand-mesh.png)

<span data-ttu-id="9f0b1-135">Bevor Sie auf Hand Netz Daten zugreifen können, müssen Sie folgende Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="9f0b1-135">Before you can access hand mesh data, you'll need to:</span></span>
- <span data-ttu-id="9f0b1-136">Wählen Sie das Objekt " **arsessionconfig** " aus, erweitern Sie die Einstellungen für " **AR Settings-> World Mapping** ", und aktivieren Sie die Option **Mesh-Daten aus der**</span><span class="sxs-lookup"><span data-stu-id="9f0b1-136">Select your **ARSessionConfig** asset, expand the **AR Settings -> World Mapping** settings, and check **Generate Mesh Data from Tracked Geometry**.</span></span>

<span data-ttu-id="9f0b1-137">Unten sind die standardmesh-Parameter aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="9f0b1-137">Below are the default mesh parameters:</span></span>

1.  <span data-ttu-id="9f0b1-138">Netzdaten für Okklusion verwenden</span><span class="sxs-lookup"><span data-stu-id="9f0b1-138">Use Mesh Data for Occlusion</span></span>
2.  <span data-ttu-id="9f0b1-139">Konflikt für Mesh-Daten generieren</span><span class="sxs-lookup"><span data-stu-id="9f0b1-139">Generate Collision for Mesh Data</span></span>
3.  <span data-ttu-id="9f0b1-140">Navigations Gitter für Mesh-Daten generieren</span><span class="sxs-lookup"><span data-stu-id="9f0b1-140">Generate Nav Mesh for Mesh Data</span></span>
4.  <span data-ttu-id="9f0b1-141">Gitternetz Daten in Wireframe Renderingparameter – Debug</span><span class="sxs-lookup"><span data-stu-id="9f0b1-141">Render Mesh Data in Wireframe – debug parameter that shows generated mesh</span></span>

<span data-ttu-id="9f0b1-142">Diese Parameterwerte werden als Gitter-und Hand Netz Standardwerte verwendet.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-142">These parameter values are used as the spatial mapping mesh and hand mesh defaults.</span></span> <span data-ttu-id="9f0b1-143">Sie können Sie jederzeit in Blaupausen oder Code für ein beliebiges Mesh ändern.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-143">You can change them at any time in Blueprints or code for any mesh.</span></span>

### <a name="c-api-reference"></a><span data-ttu-id="9f0b1-144">C++-API-Referenz</span><span class="sxs-lookup"><span data-stu-id="9f0b1-144">C++ API Reference</span></span>
<span data-ttu-id="9f0b1-145">Verwenden `EEARObjectClassification` Sie, um Hand gitterwerte in allen nachverfolgbare-Objekten zu suchen.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-145">Use `EEARObjectClassification` to find hand mesh values in all trackable objects.</span></span>
```cpp
enum class EARObjectClassification : uint8
{
    // Other types
    HandMesh,
};
```

<span data-ttu-id="9f0b1-146">Die folgenden Delegaten werden aufgerufen, wenn das System ein ausführbares Objekt erkennt, einschließlich eines Hand Netzes.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-146">The following delegates are called when the system detects any trackable object, including a hand mesh.</span></span>

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

<span data-ttu-id="9f0b1-147">Stellen Sie sicher, dass die Delegathandler der folgenden Funktions Signatur folgen:</span><span class="sxs-lookup"><span data-stu-id="9f0b1-147">Make sure your delegate handlers follow the function signature below:</span></span>

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

<span data-ttu-id="9f0b1-148">Sie können über die folgenden Schritte auf Mesh-Daten zugreifen  `UARTrackedGeometry::GetUnderlyingMesh` :</span><span class="sxs-lookup"><span data-stu-id="9f0b1-148">You can access mesh data through the  `UARTrackedGeometry::GetUnderlyingMesh`:</span></span>

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

### <a name="blueprint-api-reference"></a><span data-ttu-id="9f0b1-149">Referenz zur Blueprint-API</span><span class="sxs-lookup"><span data-stu-id="9f0b1-149">Blueprint API Reference</span></span>

<span data-ttu-id="9f0b1-150">So arbeiten Sie mit Hand-Meshes in Blaupausen:</span><span class="sxs-lookup"><span data-stu-id="9f0b1-150">To work with Hand Meshes in Blueprints:</span></span>
1. <span data-ttu-id="9f0b1-151">Hinzufügen einer **artrackablenotify** -Komponente zu einem Blueprint-Actor</span><span class="sxs-lookup"><span data-stu-id="9f0b1-151">Add an **ARTrackableNotify** Component to a Blueprint actor</span></span>

![Meldung zu einem darstellbaren Element](images/unreal/ar-trackable-notify.png)

2. <span data-ttu-id="9f0b1-153">Wechseln Sie zum **Detail** Panel, und erweitern Sie den Abschnitt **Ereignisse** .</span><span class="sxs-lookup"><span data-stu-id="9f0b1-153">Go to the **Details** panel and expand the **Events** section.</span></span>

![Artrackable Benachrichtigen 2](images/unreal/ar-trackable-notify2.png)

3. <span data-ttu-id="9f0b1-155">Überschreiben Sie beim Hinzufügen/Aktualisieren/Entfernen der überwachten Geometrie mit den folgenden Knoten im Ereignis Diagramm:</span><span class="sxs-lookup"><span data-stu-id="9f0b1-155">Overwrite On Add/Update/Remove Tracked Geometry with the following nodes in your Event Graph:</span></span>

![Bei der über sichtbaren Benachrichtigung](images/unreal/on-artrackable-notify.png)

### <a name="hand-mesh-visualization-in-openxr"></a><span data-ttu-id="9f0b1-157">Hand Mesh-Visualisierung in openxr</span><span class="sxs-lookup"><span data-stu-id="9f0b1-157">Hand Mesh visualization in OpenXR</span></span>

<span data-ttu-id="9f0b1-158">Die empfohlene Vorgehensweise zum Visualisieren des Hand Netzes ist, das xrvisualisierung-Plug-in von epic gemeinsam mit dem [Microsoft openxr-Plug](https://github.com/microsoft/Microsoft-OpenXR-Unreal)-in zu verwenden</span><span class="sxs-lookup"><span data-stu-id="9f0b1-158">The recommended way to visualize hand mesh is to use Epic’s XRVisualization plugin together with the [Microsoft OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span></span> 

<span data-ttu-id="9f0b1-159">Verwenden Sie dann im Blueprint-Editor die Option **use Hand Mesh** Function aus dem [Microsoft openxr-Plug](https://github.com/microsoft/Microsoft-OpenXR-Unreal) -in mit **aktiviertem xrvisualisierung** als Parameter.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-159">Then in the blueprint editor, you should use **Set Use Hand Mesh** function from the [Microsoft OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal) with **Enabled XRVisualization** as a parameter:</span></span>

![Blaupause für Ereignis BEGIN Play ist verbunden mit Set use Hand Mesh-Funktion mit aktiviertem xrvisualisierungs Modus](images/unreal-hand-tracking-img-05.png)

<span data-ttu-id="9f0b1-161">Um den Renderingprozess zu verwalten, sollten Sie **renderbewegungs-Controller** aus xrvisualisierung verwenden:</span><span class="sxs-lookup"><span data-stu-id="9f0b1-161">To manage the rendering process, you should use **Render Motion Controller** from XRVisualization:</span></span>

![Blaupause der Get Motion Controller-Daten Funktion, die mit der Funktion "Rendering Motion Controller" verbunden](images/unreal-hand-tracking-img-06.png)

<span data-ttu-id="9f0b1-163">Das Ergebnis:</span><span class="sxs-lookup"><span data-stu-id="9f0b1-163">The result:</span></span>

![Bild der digitalen Hand, die auf einer echten Menschen überladenen Hand ist](images/unreal-hand-tracking-img-07.png) 

<span data-ttu-id="9f0b1-165">Wenn Sie etwas komplizierteres benötigen (z. b. das Zeichnen eines Hand Diagramms mit einem benutzerdefinierten Shader), müssen Sie die Netzen als nach verfolgte Geometrie erhalten.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-165">If you need anything more complicated, such as drawing a hand mesh with a custom shader, you need to get the meshes as a tracked geometry.</span></span> 

## <a name="hand-rays"></a><span data-ttu-id="9f0b1-166">Handlichtstrahl</span><span class="sxs-lookup"><span data-stu-id="9f0b1-166">Hand rays</span></span>

<span data-ttu-id="9f0b1-167">Das Abrufen von Hand stellen funktioniert für schließen-Interaktionen wie das Durchsuchen von Objekten oder das Drücken von</span><span class="sxs-lookup"><span data-stu-id="9f0b1-167">Getting hand pose works for close interactions like grabbing objects or pressing buttons.</span></span> <span data-ttu-id="9f0b1-168">Manchmal müssen Sie jedoch mit holograms arbeiten, die von den Benutzern weit entfernt sind.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-168">However, sometimes you need to work with holograms that are far away from your users.</span></span> <span data-ttu-id="9f0b1-169">Dies kann mit Hand Strahlen erreicht werden, die als Zeigegeräte sowohl in C++ als auch in Blaupausen verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-169">This can be accomplished with hand rays, which can be used as pointing devices in both C++ and Blueprints.</span></span> <span data-ttu-id="9f0b1-170">Sie können einen Strahl von Hand zu einem Punkt zeichnen und, mit Hilfe von Unreal Ray Tracing, ein – Hologramm auswählen, das andernfalls nicht erreichbar wäre.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-170">You can draw a ray from your hand to a far point and, with some help from Unreal ray tracing, select a hologram that would otherwise be out of reach.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="9f0b1-171">Da alle Funktions Ergebnisse jeden Frame ändern, werden Sie alle aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-171">Since all function results change every frame, they're all made callable.</span></span> <span data-ttu-id="9f0b1-172">Weitere Informationen zu reinen und impformen oder Aufruf baren Funktionen finden Sie in der Blueprint-Benutzer-GUID für [Funktionen](https://docs.unrealengine.com/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure).</span><span class="sxs-lookup"><span data-stu-id="9f0b1-172">For more information about pure and impure or callable functions, see the Blueprint user guid on [functions](https://docs.unrealengine.com/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure).</span></span>

[!INCLUDE[](includes/tabs-tracking-hand-ray.md)]

## <a name="gestures"></a><span data-ttu-id="9f0b1-173">Gesten</span><span class="sxs-lookup"><span data-stu-id="9f0b1-173">Gestures</span></span>

<span data-ttu-id="9f0b1-174">Hololens 2 verfolgt räumliche Gesten, was bedeutet, dass Sie diese Gesten als Eingabe erfassen können.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-174">The HoloLens 2 tracks spatial gestures, which means you can capture those gestures as input.</span></span> <span data-ttu-id="9f0b1-175">Die Gesten Verfolgung basiert auf einem Abonnement Modell.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-175">Gesture tracking is based on a subscription model.</span></span> <span data-ttu-id="9f0b1-176">Verwenden Sie die Funktion "Gesten konfigurieren", um dem Gerät mitzuteilen, welche Gesten Sie nachverfolgen möchten.  Weitere Informationen zu Gesten finden Sie im Artikel zur [grundlegenden Verwendung von hololens 2](https://docs.microsoft.com/hololens/hololens2-basic-usage) .</span><span class="sxs-lookup"><span data-stu-id="9f0b1-176">You should use the “Configure Gestures” function to tell the device which gestures you want to track.  You can find more details about gestures are the [HoloLens 2 Basic Usage](https://docs.microsoft.com/hololens/hololens2-basic-usage) document.</span></span>

[!INCLUDE[](includes/tabs-tracking-gestures.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="9f0b1-177">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="9f0b1-177">Next Development Checkpoint</span></span>

<span data-ttu-id="9f0b1-178">Wenn Sie der Unreal-Entwicklungs-Journey folgen, die wir entworfen haben, befinden Sie sich mitten im Kennenlernen der MRTK-Grundbausteine.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-178">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="9f0b1-179">Von hier aus können Sie mit dem nächsten Baustein fortfahren:</span><span class="sxs-lookup"><span data-stu-id="9f0b1-179">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9f0b1-180">Lokale Raumanker</span><span class="sxs-lookup"><span data-stu-id="9f0b1-180">Local Spatial Anchors</span></span>](unreal-spatial-anchors.md)

<span data-ttu-id="9f0b1-181">Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:</span><span class="sxs-lookup"><span data-stu-id="9f0b1-181">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9f0b1-182">HoloLens-Kamera</span><span class="sxs-lookup"><span data-stu-id="9f0b1-182">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="9f0b1-183">Sie können jederzeit zu den [Prüfpunkten für die Unreal-Entwicklung](unreal-development-overview.md#2-core-building-blocks) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="9f0b1-183">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>
