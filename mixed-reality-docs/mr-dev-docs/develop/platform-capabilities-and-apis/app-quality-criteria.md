---
title: Kriterien für die App-Qualität
description: In diesem Dokument werden die wichtigsten Faktoren beschrieben, die sich auf die Qualität von Mixed Reality-apps auswirken.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: App-Qualitätskriterien, gemischte Realität, Mixed Reality-APP, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 8037b573f50ef1f1137a6c50913990fadf40e92e
ms.sourcegitcommit: a1bb77f729ee2e0b3dbd1c2c837bb7614ba7b9bd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98192678"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="05c7b-104">Kriterien für die App-Qualität</span><span class="sxs-lookup"><span data-stu-id="05c7b-104">App quality criteria</span></span>

<span data-ttu-id="05c7b-105">In diesem Dokument werden die wichtigsten Faktoren beschrieben, die sich auf die Qualität von Mixed Reality-apps auswirken.</span><span class="sxs-lookup"><span data-stu-id="05c7b-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="05c7b-106">Für jeden Faktor werden die folgenden Informationen bereitgestellt:</span><span class="sxs-lookup"><span data-stu-id="05c7b-106">For each factor, the following information is provided</span></span>
* <span data-ttu-id="05c7b-107">Übersicht – eine kurze Beschreibung des Qualitäts Faktors und die Wichtigkeit.</span><span class="sxs-lookup"><span data-stu-id="05c7b-107">Overview – a brief description of the quality factor and why it's important.</span></span>
* <span data-ttu-id="05c7b-108">Geräte Auswirkung: der Typ des Windows Mixed Reality-Geräts ist betroffen.</span><span class="sxs-lookup"><span data-stu-id="05c7b-108">Device impact - which type of Window Mixed Reality device is affected.</span></span>
* <span data-ttu-id="05c7b-109">Qualitätskriterien – Auswerten des Qualitäts Faktors.</span><span class="sxs-lookup"><span data-stu-id="05c7b-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="05c7b-110">So messen Sie –-Methoden, um das Problem zu messen (oder zu erleben).</span><span class="sxs-lookup"><span data-stu-id="05c7b-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="05c7b-111">Empfehlungen – Zusammenfassung der Ansätze, um eine bessere Benutzer Leistung zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="05c7b-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="05c7b-112">Ressourcen – relevante Entwickler-und Entwurfs Ressourcen, die nützlich sind, um bessere App-Erfahrungen zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="05c7b-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="05c7b-113">Bildfrequenz</span><span class="sxs-lookup"><span data-stu-id="05c7b-113">Frame rate</span></span>

<span data-ttu-id="05c7b-114">Die Framerate ist die erste Säule der – Hologramm-Stabilität und des Benutzer Komforts.</span><span class="sxs-lookup"><span data-stu-id="05c7b-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="05c7b-115">Die Frame Rate unterhalb der empfohlenen Ziele kann dazu führen, dass holograms Jittery werden, was sich negativ auf die glaub Fähigkeit der Funktionalität auswirkt und möglicherweise Augen Müdigkeit auslöst.</span><span class="sxs-lookup"><span data-stu-id="05c7b-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="05c7b-116">Die zielframeworkrate für Ihre Benutzeroberflächen in Windows Mixed Reality-immersiven Headsets ist entweder 60 Hz oder 90 Hz, je nachdem, welche Windows Mixed Reality-kompatiblen PCs Sie unterstützen.</span><span class="sxs-lookup"><span data-stu-id="05c7b-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets is either 60 Hz or 90 Hz depending on which Windows Mixed Reality Compatible PCs you're supporting.</span></span> <span data-ttu-id="05c7b-117">Bei hololens beträgt die zielframeworkrate 60 Hz.</span><span class="sxs-lookup"><span data-stu-id="05c7b-117">For HoloLens, the target frame rate is 60 Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="05c7b-118">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="05c7b-118">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="05c7b-119"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="05c7b-119"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="05c7b-120"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="05c7b-120"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="05c7b-121">✔️</span><span class="sxs-lookup"><span data-stu-id="05c7b-121">✔️</span></span></td>
        <td><span data-ttu-id="05c7b-122">✔️</span><span class="sxs-lookup"><span data-stu-id="05c7b-122">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="05c7b-123">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="05c7b-123">Quality criteria</span></span>

|  <span data-ttu-id="05c7b-124">Sehr hoch</span><span class="sxs-lookup"><span data-stu-id="05c7b-124">Best</span></span>  |  <span data-ttu-id="05c7b-125">Findet</span><span class="sxs-lookup"><span data-stu-id="05c7b-125">Meets</span></span> |  <span data-ttu-id="05c7b-126">Fehler</span><span class="sxs-lookup"><span data-stu-id="05c7b-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="05c7b-127">Die APP erfüllt konsistent Frames pro Sekunde (fps) für Zielgerät: 60 fps bei hololens; 90 fps bei ultrapcs; und 60 fps auf gängigen PCs.</span><span class="sxs-lookup"><span data-stu-id="05c7b-127">The app consistently meets frames per second (FPS) goal for target device: 60 fps on HoloLens; 90 fps on Ultra PCs; and 60 fps on mainstream PCs.</span></span> | <span data-ttu-id="05c7b-128">Die APP verfügt über zeitweilig auftretende Frame-Löschvorgänge, die die Kernfunktionen nicht behindern, oder FPS ist einheitlich niedriger als das gewünschte Ziel, verhindert jedoch die APP-Darstellung.</span><span class="sxs-lookup"><span data-stu-id="05c7b-128">The app has intermittent frame drops not impeding the core experience, or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="05c7b-129">In der APP tritt im Durchschnitt alle 10 Sekunden eine Dropdown-Rate auf.</span><span class="sxs-lookup"><span data-stu-id="05c7b-129">The app is experiencing a drop in frame rate on average every 10 seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="05c7b-130">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="05c7b-130">How to measure</span></span>

* <span data-ttu-id="05c7b-131">Ein Echtzeit-Frameraten Diagramm wird durch das [Windows-Geräte Portal](using-the-windows-device-portal.md#system-performance) unter "System Leistung" bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="05c7b-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="05c7b-132">Fügen Sie für das Entwicklungs Debuggen der APP einen framerraten-diagnosecounter hinzu.</span><span class="sxs-lookup"><span data-stu-id="05c7b-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="05c7b-133">Einen Beispiel Zählers finden Sie unter Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="05c7b-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="05c7b-134">Die abfrageate können auf dem Gerät auftreten, während die app ausgeführt wird, indem Sie Ihren Kopf von der Seite zu Seite wechseln.</span><span class="sxs-lookup"><span data-stu-id="05c7b-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="05c7b-135">Wenn das – Hologramm unerwartete gezittert-Bewegung anzeigt, ist die niedrige Framerate oder die Stabilitäts Ebene wahrscheinlich die Ursache.</span><span class="sxs-lookup"><span data-stu-id="05c7b-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="05c7b-136">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="05c7b-136">Recommendations</span></span>

* <span data-ttu-id="05c7b-137">Fügen Sie am Anfang der Entwicklungsarbeit einen Frameraten-Counter hinzu.</span><span class="sxs-lookup"><span data-stu-id="05c7b-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="05c7b-138">Änderungen, die eine Ablage in der Framerate verursachen, sollten ausgewertet und als Leistungsfehler entsprechend aufgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="05c7b-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="05c7b-139">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="05c7b-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="05c7b-140">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="05c7b-140">Documentation</span></span>

* [<span data-ttu-id="05c7b-141">Grundlegendes zur Leistung für gemischte Realität</span><span class="sxs-lookup"><span data-stu-id="05c7b-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="05c7b-142">Hologram Stabilität und Framerate</span><span class="sxs-lookup"><span data-stu-id="05c7b-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="05c7b-143">Asset Performance Budget</span><span class="sxs-lookup"><span data-stu-id="05c7b-143">Asset performance budget</span></span>](../../design/asset-creation-process.md)
* [<span data-ttu-id="05c7b-144">Leistungsempfehlungen für Unity</span><span class="sxs-lookup"><span data-stu-id="05c7b-144">Performance recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="05c7b-145">Tools und Tutorials</span><span class="sxs-lookup"><span data-stu-id="05c7b-145">Tools and tutorials</span></span>

* [<span data-ttu-id="05c7b-146">Mixed Reality Toolkit, FPS counter Display</span><span class="sxs-lookup"><span data-stu-id="05c7b-146">Mixed Reality Toolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="05c7b-147">Mixed Reality Toolkit, Shaders</span><span class="sxs-lookup"><span data-stu-id="05c7b-147">Mixed Reality Toolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="05c7b-148">Externe Verweise</span><span class="sxs-lookup"><span data-stu-id="05c7b-148">External references</span></span>

* [<span data-ttu-id="05c7b-149">Unity, optimieren mobiler Anwendungen</span><span class="sxs-lookup"><span data-stu-id="05c7b-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="05c7b-150">Hologrammstabilität</span><span class="sxs-lookup"><span data-stu-id="05c7b-150">Hologram stability</span></span>

<span data-ttu-id="05c7b-151">Stabile Hologramme verbessern die Benutzerfreundlichkeit und Glaubwürdigkeit Ihrer APP und sorgen für einen komfortableren Anzeige Vorgang für den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="05c7b-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="05c7b-152">Die Qualität der – Hologramm-Stabilität ist das Ergebnis einer guten App-Entwicklung und der Fähigkeit des Geräts, die Umgebung zu verstehen (nachverfolgen).</span><span class="sxs-lookup"><span data-stu-id="05c7b-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="05c7b-153">Obwohl die Framerate die erste Säule der Stabilität ist, können sich andere Faktoren auf die Stabilität auswirken, einschließlich:</span><span class="sxs-lookup"><span data-stu-id="05c7b-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="05c7b-154">Verwendung der Stabilisierungs Ebene</span><span class="sxs-lookup"><span data-stu-id="05c7b-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="05c7b-155">Entfernung zu räumlichen Ankern</span><span class="sxs-lookup"><span data-stu-id="05c7b-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="05c7b-156">Nachverfolgung</span><span class="sxs-lookup"><span data-stu-id="05c7b-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="05c7b-157">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="05c7b-157">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="05c7b-158"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="05c7b-158"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="05c7b-159"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="05c7b-159"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="05c7b-160">✔️</span><span class="sxs-lookup"><span data-stu-id="05c7b-160">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="05c7b-161">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="05c7b-161">Quality criteria</span></span>

|  <span data-ttu-id="05c7b-162">Sehr hoch</span><span class="sxs-lookup"><span data-stu-id="05c7b-162">Best</span></span>  |  <span data-ttu-id="05c7b-163">Findet</span><span class="sxs-lookup"><span data-stu-id="05c7b-163">Meets</span></span> |  <span data-ttu-id="05c7b-164">Fehler</span><span class="sxs-lookup"><span data-stu-id="05c7b-164">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="05c7b-165">Holograms werden konsistent angezeigt.</span><span class="sxs-lookup"><span data-stu-id="05c7b-165">Holograms consistently appear stable.</span></span> | <span data-ttu-id="05c7b-166">Sekundärer Inhalt zeigt unerwartete Bewegung an. oder eine unerwartete Bewegung beeinträchtigt nicht die gesamte App-Leistung.</span><span class="sxs-lookup"><span data-stu-id="05c7b-166">Secondary content shows unexpected movement; or unexpected movement doesn't impede overall app experience.</span></span> | <span data-ttu-id="05c7b-167">Primärer Inhalt in Frame zeigt unerwartete Bewegung an.</span><span class="sxs-lookup"><span data-stu-id="05c7b-167">Primary content in frame shows unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="05c7b-168">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="05c7b-168">How to measure</span></span>

<span data-ttu-id="05c7b-169">Beim Ausführen des Geräts und Anzeigen der Anzeige:</span><span class="sxs-lookup"><span data-stu-id="05c7b-169">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="05c7b-170">Bewegen Sie den Kopf von der Seite zur Seite.</span><span class="sxs-lookup"><span data-stu-id="05c7b-170">Move your head from side to side.</span></span> <span data-ttu-id="05c7b-171">Wenn die holograms unerwartete Verschiebungen anzeigen, ist die wahrscheinliche Ursache eine niedrige Framerate oder eine falsche Ausrichtung der Stabilitäts Ebene auf die Fokusebene.</span><span class="sxs-lookup"><span data-stu-id="05c7b-171">If the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="05c7b-172">Navigieren Sie in den holograms und in der Umgebung, und suchen Sie nach Verhaltensweisen wie z. b. Schwimmen und Sprung</span><span class="sxs-lookup"><span data-stu-id="05c7b-172">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="05c7b-173">Diese Art von Bewegung wird wahrscheinlich dadurch verursacht, dass das Gerät die Umgebung nicht nachverfolgt, oder die Entfernung zum räumlichen Anker.</span><span class="sxs-lookup"><span data-stu-id="05c7b-173">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="05c7b-174">Wenn sich große oder mehrere holograms im Frame befinden, beobachten Sie das – Hologramm-Verhalten in unterschiedlichen Tiefen, während Sie die Kopfzeile von der Seite zu Seite bewegen, wenn die Schattierung auftritt, wird dies wahrscheinlich durch die Stabilisierungs Ebene verursacht.</span><span class="sxs-lookup"><span data-stu-id="05c7b-174">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recommendations"></a><span data-ttu-id="05c7b-175">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="05c7b-175">Recommendations</span></span>

* <span data-ttu-id="05c7b-176">Fügen Sie am Anfang der Entwicklungsarbeit einen Frameraten-Counter hinzu.</span><span class="sxs-lookup"><span data-stu-id="05c7b-176">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="05c7b-177">Verwenden Sie die Stabilisierungs Ebene.</span><span class="sxs-lookup"><span data-stu-id="05c7b-177">Use the stabilization plane.</span></span>
* <span data-ttu-id="05c7b-178">Sie sollten immer verankert Hologramme innerhalb von drei Metern Ihres Ankers darstellen.</span><span class="sxs-lookup"><span data-stu-id="05c7b-178">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="05c7b-179">Stellen Sie sicher, dass Ihre Umgebung für die ordnungsgemäße Überwachung eingerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="05c7b-179">Make sure your environment is set up for proper tracking.</span></span>
* <span data-ttu-id="05c7b-180">Entwerfen Sie Ihre Benutzeroberflächen, um Hologramme auf verschiedenen Schwerpunkt Ebenen innerhalb des Rahmens zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="05c7b-180">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="05c7b-181">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="05c7b-181">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="05c7b-182">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="05c7b-182">Documentation</span></span>

* [<span data-ttu-id="05c7b-183">Hologram Stabilität und Framerate</span><span class="sxs-lookup"><span data-stu-id="05c7b-183">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="05c7b-184">Fallstudie mithilfe der Stabilisierungs Ebene</span><span class="sxs-lookup"><span data-stu-id="05c7b-184">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="05c7b-185">Grundlegendes zur Leistung für gemischte Realität</span><span class="sxs-lookup"><span data-stu-id="05c7b-185">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="05c7b-186">Leistungsempfehlungen für Unity</span><span class="sxs-lookup"><span data-stu-id="05c7b-186">Performance recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)
* [<span data-ttu-id="05c7b-187">Raumanker</span><span class="sxs-lookup"><span data-stu-id="05c7b-187">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="05c7b-188">Behandeln von nach Verfolgungs Fehlern</span><span class="sxs-lookup"><span data-stu-id="05c7b-188">Handling tracking errors</span></span>](../../design/coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="05c7b-189">Stationärer Frame des Verweises</span><span class="sxs-lookup"><span data-stu-id="05c7b-189">Stationary frame of reference</span></span>](../../design/coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="05c7b-190">Tools und Tutorials</span><span class="sxs-lookup"><span data-stu-id="05c7b-190">Tools and tutorials</span></span>

* [<span data-ttu-id="05c7b-191">Mr Companion Kit, kinect IPD</span><span class="sxs-lookup"><span data-stu-id="05c7b-191">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="05c7b-192">Holograms-Position auf realen Oberflächen</span><span class="sxs-lookup"><span data-stu-id="05c7b-192">Holograms position on real surfaces</span></span>

<span data-ttu-id="05c7b-193">Falsche Abweichungen von holograms mit physischen Objekten (wenn Sie in Beziehung zueinander gesetzt werden sollen) sind ein eindeutiger Hinweis auf die nicht-Union von holograms und der realen Welt.</span><span class="sxs-lookup"><span data-stu-id="05c7b-193">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) are a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="05c7b-194">Die Genauigkeit der Platzierung sollte in Relation zu den Anforderungen des Szenarios liegen. Beispielsweise kann bei der allgemeinen Oberflächen Platzierung die räumliche Karte verwendet werden, aber eine genauere Platzierung erfordert die Verwendung von Markern und die Kalibrierung.</span><span class="sxs-lookup"><span data-stu-id="05c7b-194">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="05c7b-195">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="05c7b-195">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="05c7b-196"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="05c7b-196"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="05c7b-197"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="05c7b-197"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="05c7b-198">✔️</span><span class="sxs-lookup"><span data-stu-id="05c7b-198">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="05c7b-199">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="05c7b-199">Quality criteria</span></span>

|  <span data-ttu-id="05c7b-200">Sehr hoch</span><span class="sxs-lookup"><span data-stu-id="05c7b-200">Best</span></span>  |  <span data-ttu-id="05c7b-201">Findet</span><span class="sxs-lookup"><span data-stu-id="05c7b-201">Meets</span></span> |  <span data-ttu-id="05c7b-202">Fehler</span><span class="sxs-lookup"><span data-stu-id="05c7b-202">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="05c7b-203">Holograms werden an der Oberfläche ausgerichtet, die sich in der Regel im Bereich von Zentimetern bis Zoll</span><span class="sxs-lookup"><span data-stu-id="05c7b-203">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="05c7b-204">Wenn Sie mehr Genauigkeit benötigen, sollte die APP eine effiziente Möglichkeit zur Zusammenarbeit innerhalb der APP-Spezifikation bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="05c7b-204">If you need more accuracy, the app should provide an efficient means for collaboration within the app spec.</span></span> | <span data-ttu-id="05c7b-205">Nicht verfügbar</span><span class="sxs-lookup"><span data-stu-id="05c7b-205">NA</span></span> | <span data-ttu-id="05c7b-206">Die Hologramme werden mit dem physischen Zielobjekt nicht ausgerichtet angezeigt, indem die Oberfläche unterbrochen wird oder die Fläche von der Oberfläche entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="05c7b-206">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="05c7b-207">Wenn die Genauigkeit erforderlich ist, sollten holograms die Näherungs Spezifikation des Szenarios erfüllen.</span><span class="sxs-lookup"><span data-stu-id="05c7b-207">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="05c7b-208">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="05c7b-208">How to measure</span></span>

* <span data-ttu-id="05c7b-209">Holograms, die auf räumlicher Zuordnung platziert werden, sollten sich nicht in der Oberfläche oberhalb oder unterhalb der Oberfläche befinden.</span><span class="sxs-lookup"><span data-stu-id="05c7b-209">Holograms that are placed on spatial map shouldn't appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="05c7b-210">Holograms, die eine exakte Platzierung erfordern, sollten eine Form von Marker-und Kalibrierungs Systemen aufweisen, die auf die Anforderungen des Szenarios zutreffen.</span><span class="sxs-lookup"><span data-stu-id="05c7b-210">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="05c7b-211">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="05c7b-211">Recommendations</span></span>

* <span data-ttu-id="05c7b-212">Die räumliche Zuordnung eignet sich zum Platzieren von Objekten auf Oberflächen, wenn die Genauigkeit nicht erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="05c7b-212">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="05c7b-213">Verwenden Sie zum Festlegen der optimalen Genauigkeit Marker oder Poster, um die holograms und einen Xbox-Controller (oder einen manuellen Ausrichtungs Mechanismus) für die endgültige Kalibrierung festzulegen.</span><span class="sxs-lookup"><span data-stu-id="05c7b-213">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="05c7b-214">Es empfiehlt sich, zusätzliche große Hologramme in logische Teile zu zerlegen und die einzelnen Teile an der Oberfläche auszurichten.</span><span class="sxs-lookup"><span data-stu-id="05c7b-214">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="05c7b-215">Nicht ordnungsgemäß festgelegten interpupillary Distance (IPD) können auch die Ausrichtung von holograms beeinflussen.</span><span class="sxs-lookup"><span data-stu-id="05c7b-215">Improperly set interpupillary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="05c7b-216">Konfigurieren Sie hololens immer für die IPD des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="05c7b-216">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="05c7b-217">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="05c7b-217">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="05c7b-218">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="05c7b-218">Documentation</span></span>

* [<span data-ttu-id="05c7b-219">Platzierung räumlicher Zuordnung</span><span class="sxs-lookup"><span data-stu-id="05c7b-219">Spatial mapping placement</span></span>](../../design/spatial-mapping.md#placement)
* [<span data-ttu-id="05c7b-220">Raum Scanprozess</span><span class="sxs-lookup"><span data-stu-id="05c7b-220">Room scanning process</span></span>](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="05c7b-221">Bewährte Methoden für räumliche Anker</span><span class="sxs-lookup"><span data-stu-id="05c7b-221">Spatial anchors best practices</span></span>](../../design/spatial-anchors.md#best-practices)
* [<span data-ttu-id="05c7b-222">Behandeln von nach Verfolgungs Fehlern</span><span class="sxs-lookup"><span data-stu-id="05c7b-222">Handling tracking errors</span></span>](../../design/coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="05c7b-223">Räumliche Abbildung in Unity</span><span class="sxs-lookup"><span data-stu-id="05c7b-223">Spatial mapping in Unity</span></span>](../unity/spatial-mapping-in-unity.md)
* [<span data-ttu-id="05c7b-224">Übersicht über die vuforia-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="05c7b-224">Vuforia development overview</span></span>](../unity/vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="05c7b-225">Tools und Tutorials</span><span class="sxs-lookup"><span data-stu-id="05c7b-225">Tools and tutorials</span></span>

* [<span data-ttu-id="05c7b-226">Mr Toolkit, Bibliotheken für räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="05c7b-226">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="05c7b-227">Mr Companion Kit, Poster-Kalibrierungs Beispiel</span><span class="sxs-lookup"><span data-stu-id="05c7b-227">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="05c7b-228">Mr Companion Kit, kinect IPD</span><span class="sxs-lookup"><span data-stu-id="05c7b-228">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="05c7b-229">Externe Verweise</span><span class="sxs-lookup"><span data-stu-id="05c7b-229">External references</span></span>

* [<span data-ttu-id="05c7b-230">Lowes-Fallstudie, Genauigkeits Ausrichtung</span><span class="sxs-lookup"><span data-stu-id="05c7b-230">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="05c7b-231">Anzeigen der Komfortzone</span><span class="sxs-lookup"><span data-stu-id="05c7b-231">Viewing zone of comfort</span></span>

<span data-ttu-id="05c7b-232">App-Entwickler steuern, wohin die Augen der Benutzer konvergiert werden, indem Sie Inhalte und Hologramme in verschiedenen Tiefen platzieren.</span><span class="sxs-lookup"><span data-stu-id="05c7b-232">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="05c7b-233">Benutzer, die hololens durchführen, unterstützen immer 2,0 m, um ein klares Bild zu erhalten, da hololens in einer optischen Entfernung von ungefähr 2,0 m vom Benutzer korrigiert werden.</span><span class="sxs-lookup"><span data-stu-id="05c7b-233">Users wearing HoloLens will always accommodate to 2.0 m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0 m away from the user.</span></span> <span data-ttu-id="05c7b-234">Eine nicht ordnungsgemäße Inhalts Tiefe kann zu einem visuellen Unbehagen oder Müdigkeit führen.</span><span class="sxs-lookup"><span data-stu-id="05c7b-234">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="05c7b-235">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="05c7b-235">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="05c7b-236"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="05c7b-236"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="05c7b-237"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="05c7b-237"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="05c7b-238">✔️</span><span class="sxs-lookup"><span data-stu-id="05c7b-238">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="05c7b-239">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="05c7b-239">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="05c7b-240">Sehr hoch</span><span class="sxs-lookup"><span data-stu-id="05c7b-240">Best</span></span> </td><td><ul>
<li><span data-ttu-id="05c7b-241">Platzieren Sie den Inhalt bei 2 m.</span><span class="sxs-lookup"><span data-stu-id="05c7b-241">Place content at 2 m.</span></span></li><li><span data-ttu-id="05c7b-242">Wenn holograms bei 2 m nicht platziert werden können und Konflikte zwischen Konvergenz und Unterbringung nicht vermieden werden können, liegt die optimale Zone für die – Hologramm-Platzierung zwischen 1,25 m und 5 m.</span><span class="sxs-lookup"><span data-stu-id="05c7b-242">When holograms cannot be placed at 2 m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25 m and 5 m.</span></span></li><li><span data-ttu-id="05c7b-243">In jedem Fall sollten Designer Inhalte strukturieren, um Benutzern die Interaktion von 1 + m zu empfehlen (z. b. Anpassen von Inhalts Größe und Standard Platzierungs Parametern).</span><span class="sxs-lookup"><span data-stu-id="05c7b-243">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="05c7b-244">Sofern dies nicht für das Szenario erforderlich ist, sollte eine Clippingebene mit "Fade out" implementiert werden, beginnend bei 1 Mio.</span><span class="sxs-lookup"><span data-stu-id="05c7b-244">Unless not required by the scenario, a clipping plane should be implement with fade out starting at 1 m.</span></span></li><li><span data-ttu-id="05c7b-245">In Fällen, in denen eine genauere Betrachtung eines sehr großen holograms erforderlich ist, sollte der Inhalt nicht näher als 50 cm sein.</span><span class="sxs-lookup"><span data-stu-id="05c7b-245">In cases where closer observation of a motionless hologram is required, the content shouldn't be closer than 50 cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="05c7b-246">Findet</span><span class="sxs-lookup"><span data-stu-id="05c7b-246">Meets</span></span></td><td> <span data-ttu-id="05c7b-247">Der Inhalt befindet sich in der Anzeige-und Bewegungs Anleitung, aber nicht ordnungsgemäß oder ohne Verwendung der Clippingebene.</span><span class="sxs-lookup"><span data-stu-id="05c7b-247">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="05c7b-248">Fehler</span><span class="sxs-lookup"><span data-stu-id="05c7b-248">Fail</span></span> </td><td> <span data-ttu-id="05c7b-249">Der Inhalt wird zu nah dargestellt (in der Regel &lt; 1,25 m oder &lt; 50 cm für stationäre Hologramme, die eine genauere Beobachtung erfordern).</span><span class="sxs-lookup"><span data-stu-id="05c7b-249">Content is presented too close (typically &lt;1.25 m, or &lt;50 cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="05c7b-250">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="05c7b-250">How to measure</span></span>

* <span data-ttu-id="05c7b-251">Der Inhalt sollte in der Regel 2 Mio., aber nicht größer als 1,25 oder größer als 5 Mio. sein.</span><span class="sxs-lookup"><span data-stu-id="05c7b-251">Content should typically be 2 m away, but no closer than 1.25 or further than 5 m.</span></span>
* <span data-ttu-id="05c7b-252">Mit wenigen Ausnahmen sollte die Länge des Clipping-renderingrenderwerts auf 85 cm festgelegt werden, wobei der Inhalt ab 1 Mio. nicht mehr angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="05c7b-252">With few exceptions, the HoloLens clipping render distance should be set to 85CM with fade out of content starting at 1 m.</span></span> <span data-ttu-id="05c7b-253">Wenden Sie sich an den Inhalt, und notieren Sie sich die Ausschneide Ebene.</span><span class="sxs-lookup"><span data-stu-id="05c7b-253">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="05c7b-254">Stationärer Inhalt sollte nicht näher als 50 cm entfernt sein.</span><span class="sxs-lookup"><span data-stu-id="05c7b-254">Stationary content should not be closer than 50 cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="05c7b-255">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="05c7b-255">Recommendations</span></span>

* <span data-ttu-id="05c7b-256">Entwerfen Sie den Inhalt für die optimale Anzeige Distanz von 2 m.</span><span class="sxs-lookup"><span data-stu-id="05c7b-256">Design content for the optimal viewing distance of 2 m.</span></span>
* <span data-ttu-id="05c7b-257">Legen Sie die Entfernungs-renderentfernungs Entfernung auf 85 cm mit dem Ausblenden von Inhalt ab 1 m fest.</span><span class="sxs-lookup"><span data-stu-id="05c7b-257">Set the clipping render distance to 85 cm with fade out of content starting at 1 m.</span></span>
* <span data-ttu-id="05c7b-258">Bei stationären Hologrammen, die näher betrachtet werden müssen, sollte die Clippingebene nicht kleiner als 30 cm sein, und das ausblenden sollte mindestens 10 cm von der Clippingebene aus beginnen.</span><span class="sxs-lookup"><span data-stu-id="05c7b-258">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30 cm and fade out should start at least 10 cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="05c7b-259">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="05c7b-259">Resources</span></span>

* [<span data-ttu-id="05c7b-260">Rendering-Entfernung</span><span class="sxs-lookup"><span data-stu-id="05c7b-260">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="05c7b-261">Fokuspunkt in Unity</span><span class="sxs-lookup"><span data-stu-id="05c7b-261">Focus point in Unity</span></span>](../unity/focus-point-in-unity.md)
* [<span data-ttu-id="05c7b-262">Experimentieren mit der Skala</span><span class="sxs-lookup"><span data-stu-id="05c7b-262">Experimenting with scale</span></span>](../../design/scale.md#experimenting-with-scale)
* [<span data-ttu-id="05c7b-263">Text, Empfohlene Schriftgröße</span><span class="sxs-lookup"><span data-stu-id="05c7b-263">Text, Recommended font size</span></span>](../../design/typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="05c7b-264">Tiefen Wechsel</span><span class="sxs-lookup"><span data-stu-id="05c7b-264">Depth switching</span></span>

<span data-ttu-id="05c7b-265">Unabhängig von der Anzeige Zone von Komfort Problemen kann es sein, dass der Benutzer häufig oder schnell zwischen Near-und Far-Fokus Objekten (einschließlich holograms und realen Inhalten) wechselt.</span><span class="sxs-lookup"><span data-stu-id="05c7b-265">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="05c7b-266">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="05c7b-266">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="05c7b-267"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="05c7b-267"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="05c7b-268"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="05c7b-268"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="05c7b-269">✔️</span><span class="sxs-lookup"><span data-stu-id="05c7b-269">✔️</span></span></td>
        <td><span data-ttu-id="05c7b-270">✔️</span><span class="sxs-lookup"><span data-stu-id="05c7b-270">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="05c7b-271">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="05c7b-271">Quality criteria</span></span>

|  <span data-ttu-id="05c7b-272">Sehr hoch</span><span class="sxs-lookup"><span data-stu-id="05c7b-272">Best</span></span>  |  <span data-ttu-id="05c7b-273">Findet</span><span class="sxs-lookup"><span data-stu-id="05c7b-273">Meets</span></span> |  <span data-ttu-id="05c7b-274">Fehler</span><span class="sxs-lookup"><span data-stu-id="05c7b-274">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="05c7b-275">Eingeschränkter oder natürlicher tiefen Wechsel, der nicht bewirkt, dass sich der Benutzer nicht ganz natürlich neu konzentriert.</span><span class="sxs-lookup"><span data-stu-id="05c7b-275">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="05c7b-276">Abrupter tiefen Wechsel hierbei handelt es sich um einen Kern, der in die APP-Umgebung integriert wird, oder um einen abrupten Wechsel, der durch unerwartete reale Inhalte verursacht wurde.</span><span class="sxs-lookup"><span data-stu-id="05c7b-276">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="05c7b-277">Der konsistente tiefen Wechsel oder der abrupte, nicht erforderliche Wechsel oder Kern der APP-Leistung.</span><span class="sxs-lookup"><span data-stu-id="05c7b-277">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="05c7b-278">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="05c7b-278">How to measure</span></span>

* <span data-ttu-id="05c7b-279">Wenn die APP erfordert, dass der Benutzer den tiefen Fokus konsistent und/oder abrupt ändert, liegt ein Problem mit dem tiefen Wechsel vor.</span><span class="sxs-lookup"><span data-stu-id="05c7b-279">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="05c7b-280">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="05c7b-280">Recommendations</span></span>

* <span data-ttu-id="05c7b-281">Behalten Sie primären Inhalt in einer konsistenten Fokusebene, und stellen Sie sicher, dass die Stabilisierungs Ebene mit der Fokusebene übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="05c7b-281">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="05c7b-282">Dadurch wird die oomotor-Müdigkeit und unerwartete – Hologramm-Bewegung verringert.</span><span class="sxs-lookup"><span data-stu-id="05c7b-282">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="05c7b-283">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="05c7b-283">Resources</span></span>

* [<span data-ttu-id="05c7b-284">Rendering-Entfernung</span><span class="sxs-lookup"><span data-stu-id="05c7b-284">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="05c7b-285">Fokuspunkt in Unity</span><span class="sxs-lookup"><span data-stu-id="05c7b-285">Focus point in Unity</span></span>](../unity/focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="05c7b-286">Verwendung von räumlichem Sound</span><span class="sxs-lookup"><span data-stu-id="05c7b-286">Use of spatial sound</span></span>

<span data-ttu-id="05c7b-287">In Windows Mixed Reality bietet die Audioengine die Audiowiedergabe-Komponente der gemischten Realität, indem 3D-Sounds mithilfe von Richtungs-, Entfernungs-und Umgebungs Simulationen simuliert werden.</span><span class="sxs-lookup"><span data-stu-id="05c7b-287">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="05c7b-288">Die Verwendung von räumlichem Sound in einer Anwendung ermöglicht Entwicklern das überzeugend Platzieren von Sounds in einem dreidimensionalen Raum (Kugel), der sich alle um den Benutzer dreht.</span><span class="sxs-lookup"><span data-stu-id="05c7b-288">Using spatial sound in an application allows developers to convincingly place sounds in a 3-dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="05c7b-289">Diese Sounds erscheinen dann so, als wären Sie von echten physischen Objekten oder den Mixed Reality holograms in der Benutzerumgebung.</span><span class="sxs-lookup"><span data-stu-id="05c7b-289">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="05c7b-290">Räumlicher Sound ist ein leistungsfähiges Tool für das Eintauchen, die Barrierefreiheit und den UX-Entwurf in gemischten Reality-Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="05c7b-290">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="05c7b-291">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="05c7b-291">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="05c7b-292"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="05c7b-292"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="05c7b-293"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="05c7b-293"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="05c7b-294">✔️</span><span class="sxs-lookup"><span data-stu-id="05c7b-294">✔️</span></span></td>
        <td><span data-ttu-id="05c7b-295">✔️</span><span class="sxs-lookup"><span data-stu-id="05c7b-295">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="05c7b-296">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="05c7b-296">Quality criteria</span></span>

|  <span data-ttu-id="05c7b-297">Sehr hoch</span><span class="sxs-lookup"><span data-stu-id="05c7b-297">Best</span></span>  |  <span data-ttu-id="05c7b-298">Findet</span><span class="sxs-lookup"><span data-stu-id="05c7b-298">Meets</span></span> |  <span data-ttu-id="05c7b-299">Fehler</span><span class="sxs-lookup"><span data-stu-id="05c7b-299">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="05c7b-300">Sound ist logisch räumlich, und die UX verwendet den Sound entsprechend, um die Objekt Ermittlung und das Benutzer Feedback zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="05c7b-300">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="05c7b-301">Sound ist naturgemäß und relevant für Objekte und wird im gesamten Szenario normalisiert.</span><span class="sxs-lookup"><span data-stu-id="05c7b-301">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="05c7b-302">Räumliche Audiodaten werden in angemessener Weise verwendet, um Benutzer Feedback und Auffindbarkeit zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="05c7b-302">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="05c7b-303">Sound ist nicht erwartungsgemäß räumlich und/oder ungenügender Ton, um Benutzer innerhalb der UX zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="05c7b-303">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="05c7b-304">Das räumliche audiobild wurde im Entwurf des Szenarios nicht berücksichtigt oder verwendet.</span><span class="sxs-lookup"><span data-stu-id="05c7b-304">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="05c7b-305">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="05c7b-305">How to measure</span></span>

* <span data-ttu-id="05c7b-306">Im Allgemeinen sollten relevante Sounds aus Ziel-holograms (z. b. "Bark Sound" von Holographic Dog) ausgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="05c7b-306">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="05c7b-307">Sound Hinweise sollten in der gesamten Benutzeroberfläche verwendet werden, um dem Benutzer Feedback oder das Bewusstsein von Aktionen außerhalb des Holographic Frame zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="05c7b-307">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="05c7b-308">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="05c7b-308">Recommendations</span></span>

* <span data-ttu-id="05c7b-309">Verwenden Sie räumliche Audiodaten, um die Objekt Ermittlung und Benutzeroberflächen zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="05c7b-309">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="05c7b-310">Echte Sounds funktionieren besser als synthetisieren oder unnatürlicher Sound.</span><span class="sxs-lookup"><span data-stu-id="05c7b-310">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="05c7b-311">Die meisten Sounds sollten räumlich behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="05c7b-311">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="05c7b-312">Vermeiden Sie unsichtbare Emitter.</span><span class="sxs-lookup"><span data-stu-id="05c7b-312">Avoid invisible emitters.</span></span>
* <span data-ttu-id="05c7b-313">Vermeiden Sie die räumliche Maskierung.</span><span class="sxs-lookup"><span data-stu-id="05c7b-313">Avoid spatial masking.</span></span>
* <span data-ttu-id="05c7b-314">Normalisieren Sie alle Sounds.</span><span class="sxs-lookup"><span data-stu-id="05c7b-314">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="05c7b-315">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="05c7b-315">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="05c7b-316">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="05c7b-316">Documentation</span></span>

* [<span data-ttu-id="05c7b-317">Raumklang</span><span class="sxs-lookup"><span data-stu-id="05c7b-317">Spatial sound</span></span>](../../design/spatial-sound.md)
* [<span data-ttu-id="05c7b-318">Raumklangentwurf</span><span class="sxs-lookup"><span data-stu-id="05c7b-318">Spatial sound design</span></span>](../../design/spatial-sound-design.md)
* [<span data-ttu-id="05c7b-319">Raumklang in Unity</span><span class="sxs-lookup"><span data-stu-id="05c7b-319">Spatial sound in Unity</span></span>](../unity/spatial-sound-in-unity.md)
* [<span data-ttu-id="05c7b-320">Fallstudie, räumlicher Sound für holotour</span><span class="sxs-lookup"><span data-stu-id="05c7b-320">Case study, Spatial sound for HoloTour</span></span>](../../design/case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="05c7b-321">Fallstudie mit räumlichem Sound in roboraid</span><span class="sxs-lookup"><span data-stu-id="05c7b-321">Case study, Using spatial sound in RoboRaid</span></span>](../../design/case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="05c7b-322">Tools und Tutorials</span><span class="sxs-lookup"><span data-stu-id="05c7b-322">Tools and tutorials</span></span>

* [<span data-ttu-id="05c7b-323">Mixed Reality Toolkit: räumliche Audiodaten</span><span class="sxs-lookup"><span data-stu-id="05c7b-323">Mixed Reality Toolkit - Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="05c7b-324">Fokus auf Holographic Frame-Grenzen (FOV)</span><span class="sxs-lookup"><span data-stu-id="05c7b-324">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="05c7b-325">Gut gestaltete Benutzeroberflächen können den nützlichen Kontext der virtuellen Umgebung erstellen und verwalten, die sich um die Benutzer erstreckt.</span><span class="sxs-lookup"><span data-stu-id="05c7b-325">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="05c7b-326">Das Verringern der Auswirkungen der FOV-Grenzen umfasst einen durchdachten Entwurf der Inhalts Skala und des Kontexts, die Verwendung räumlicher Audiodaten, Leitfäden und die Position des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="05c7b-326">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="05c7b-327">Wenn dies der Fall ist, wird der Benutzer durch die FOV-Grenzen weniger beeinträchtigt, während er eine bequeme App-Erfahrung bietet.</span><span class="sxs-lookup"><span data-stu-id="05c7b-327">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="05c7b-328">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="05c7b-328">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="05c7b-329"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="05c7b-329"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="05c7b-330"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="05c7b-330"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="05c7b-331">✔️</span><span class="sxs-lookup"><span data-stu-id="05c7b-331">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="05c7b-332">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="05c7b-332">Quality criteria</span></span>

|  <span data-ttu-id="05c7b-333">Sehr hoch</span><span class="sxs-lookup"><span data-stu-id="05c7b-333">Best</span></span>  |  <span data-ttu-id="05c7b-334">Findet</span><span class="sxs-lookup"><span data-stu-id="05c7b-334">Meets</span></span> |  <span data-ttu-id="05c7b-335">Fehler</span><span class="sxs-lookup"><span data-stu-id="05c7b-335">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="05c7b-336">Der Benutzer verliert nie den Kontext, und die Anzeige ist bequem.</span><span class="sxs-lookup"><span data-stu-id="05c7b-336">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="05c7b-337">Für große Objekte wird Kontextunterstützung bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="05c7b-337">Context assistance is provided for large objects.</span></span> <span data-ttu-id="05c7b-338">Ermittelbarkeits-und Anzeige Anleitungen werden für Objekte außerhalb des Frames bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="05c7b-338">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="05c7b-339">Im Allgemeinen sind Bewegungs Entwurf und Skalierung der holograms für eine bequeme Anzeige geeignet.</span><span class="sxs-lookup"><span data-stu-id="05c7b-339">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="05c7b-340">Der Benutzer verliert den Kontext nie, aber in bestimmten Situationen ist möglicherweise eine zusätzliche Nacken Bewegung erforderlich.</span><span class="sxs-lookup"><span data-stu-id="05c7b-340">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="05c7b-341">In einer begrenzten Situation bewirkt die Skalierung, dass holograms entweder den vertikalen oder horizontalen Rahmen unterbrechen, was dazu führt, dass die Bewegung holograms durch einen Hals</span><span class="sxs-lookup"><span data-stu-id="05c7b-341">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="05c7b-342">Der Benutzer verliert wahrscheinlich den Kontext und/oder eine konsistente Hals Bewegung zum Anzeigen von holograms.</span><span class="sxs-lookup"><span data-stu-id="05c7b-342">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="05c7b-343">Keine Kontext Leit Fäden für große Holographic-Objekte, die das Verschieben von Objekten außerhalb des Frames ohne auffindbarkeits Leit Fäden vereinfachen, oder die Verwendung von hohen holograms erfordert eine reguläre Hals Bewegung zum anzeigen.</span><span class="sxs-lookup"><span data-stu-id="05c7b-343">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="05c7b-344">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="05c7b-344">How to measure</span></span>

* <span data-ttu-id="05c7b-345">Der Kontext für ein (großes) – Hologramm geht verloren oder wird nicht verstanden, weil er an den Begrenzungen abgeschnitten wurde.</span><span class="sxs-lookup"><span data-stu-id="05c7b-345">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="05c7b-346">Die Speicherorte von holograms sind schwer zu finden, da Sie nicht über die Aufmerksamkeit von Regisseuren oder Inhalten verfügen, die sich schnell in den Holographic-Frame bewegen.</span><span class="sxs-lookup"><span data-stu-id="05c7b-346">Locations of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="05c7b-347">Das Szenario erfordert reguläre und wiederkehrende aufruhenden aufruhenden Bewegung, um ein – Hologramm vollständig zu sehen</span><span class="sxs-lookup"><span data-stu-id="05c7b-347">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="05c7b-348">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="05c7b-348">Recommendations</span></span>

* <span data-ttu-id="05c7b-349">Starten Sie die Arbeit mit kleinen Objekten, die für den FOV geeignet sind, und wechseln Sie dann mit visuellen Cues in größere Versionen.</span><span class="sxs-lookup"><span data-stu-id="05c7b-349">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="05c7b-350">Verwenden Sie die Directors für räumliche Audiodaten und Aufmerksamkeit, um dem Benutzer zu helfen, Inhalte außerhalb des FOV zu finden.</span><span class="sxs-lookup"><span data-stu-id="05c7b-350">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="05c7b-351">Vermeiden Sie so weit wie möglich Hologramme, die den FOV vertikal abschneiden.</span><span class="sxs-lookup"><span data-stu-id="05c7b-351">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="05c7b-352">Stellen Sie dem Benutzer einen in-App-Leitfaden für den optimalen Anzeige Speicherort zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="05c7b-352">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="05c7b-353">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="05c7b-353">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="05c7b-354">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="05c7b-354">Documentation</span></span>

* [<span data-ttu-id="05c7b-355">Holografischer Rahmen</span><span class="sxs-lookup"><span data-stu-id="05c7b-355">Holographic frame</span></span>](../../design/holographic-frame.md)
* [<span data-ttu-id="05c7b-356">Fallstudie, Entwicklung von holostudio-UI und Interaktions Entwurf</span><span class="sxs-lookup"><span data-stu-id="05c7b-356">Case Study, HoloStudio UI and interaction design learnings</span></span>](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="05c7b-357">Skalieren von Objekten und Umgebungen</span><span class="sxs-lookup"><span data-stu-id="05c7b-357">Scale of objects and environments</span></span>](../../design/scale.md)
* [<span data-ttu-id="05c7b-358">Cursor, visuelle Hinweise</span><span class="sxs-lookup"><span data-stu-id="05c7b-358">Cursors, Visual cues</span></span>](../../design/cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="05c7b-359">Externe Verweise</span><span class="sxs-lookup"><span data-stu-id="05c7b-359">External references</span></span>

* [<span data-ttu-id="05c7b-360">Viel ADO zum FOV</span><span class="sxs-lookup"><span data-stu-id="05c7b-360">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="05c7b-361">Inhalt reagiert auf Benutzer Position</span><span class="sxs-lookup"><span data-stu-id="05c7b-361">Content reacts to user position</span></span>

<span data-ttu-id="05c7b-362">Holograms sollten auf ungefähr die gleiche Weise wie "echte" Objekte auf die Benutzer Position reagieren.</span><span class="sxs-lookup"><span data-stu-id="05c7b-362">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="05c7b-363">Ein wichtiger Entwurfs Aspekt sind Benutzeroberflächen Elemente, die nicht unbedingt annehmen können, dass die Position eines Benutzers stationär ist und sich an die Bewegung des Benutzers anpasst.</span><span class="sxs-lookup"><span data-stu-id="05c7b-363">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="05c7b-364">Das Entwerfen einer APP, die sich ordnungsgemäß an die Benutzer Position anpasst, führt zu einer besseren Benutzerfreundlichkeit und erleichtert die Verwendung.</span><span class="sxs-lookup"><span data-stu-id="05c7b-364">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="05c7b-365">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="05c7b-365">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="05c7b-366"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="05c7b-366"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="05c7b-367"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="05c7b-367"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="05c7b-368">✔️</span><span class="sxs-lookup"><span data-stu-id="05c7b-368">✔️</span></span></td>
        <td><span data-ttu-id="05c7b-369">✔️</span><span class="sxs-lookup"><span data-stu-id="05c7b-369">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="05c7b-370">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="05c7b-370">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="05c7b-371">Sehr hoch</span><span class="sxs-lookup"><span data-stu-id="05c7b-371">Best</span></span> </td><td> <span data-ttu-id="05c7b-372">Der Inhalt und die Benutzeroberfläche werden an Benutzer Positionen angepasst, damit Benutzer im Bereich der erwarteten Benutzer Bewegung natürlich mit Inhalten interagieren können.</span><span class="sxs-lookup"><span data-stu-id="05c7b-372">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="05c7b-373">Findet</span><span class="sxs-lookup"><span data-stu-id="05c7b-373">Meets</span></span> </td><td> <span data-ttu-id="05c7b-374">Die Benutzeroberfläche passt sich an die Benutzer Position an, kann jedoch die Ansicht von Schlüssel Inhalten behindern, die den Benutzer zum Anpassen Ihrer Position benötigen.</span><span class="sxs-lookup"><span data-stu-id="05c7b-374">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="05c7b-375">Fehler</span><span class="sxs-lookup"><span data-stu-id="05c7b-375">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="05c7b-376">Benutzeroberflächen Elemente gehen verloren oder sind während der Bewegung gesperrt, sodass der Benutzer nicht auf natürliche Weise zu den Steuerelementen zurückkehrt.</span><span class="sxs-lookup"><span data-stu-id="05c7b-376">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="05c7b-377">Elemente der Benutzeroberfläche beschränken die Ansicht von primärem Inhalt.</span><span class="sxs-lookup"><span data-stu-id="05c7b-377">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="05c7b-378">Die UI-Bewegung ist nicht für die Anzeige von Distanz und Schwung optimiert, insbesondere bei Benutzeroberflächen Elementen mit <a href="../../design/billboarding-and-tag-along.md">tagentlang</a> .</span><span class="sxs-lookup"><span data-stu-id="05c7b-378">UI movement isn't optimized for viewing distance and momentum particularly with <a href="../../design/billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="05c7b-379">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="05c7b-379">How to measure</span></span>

* <span data-ttu-id="05c7b-380">Alle Messungen sollten innerhalb eines angemessenen Umfangs des Szenarios durchgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="05c7b-380">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="05c7b-381">Während die Benutzer Bewegung variieren kann, versuchen Sie nicht, die APP mit extremer Benutzer Bewegung zu täuschen.</span><span class="sxs-lookup"><span data-stu-id="05c7b-381">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="05c7b-382">Für Elemente der Benutzeroberfläche sollten relevante Steuerelemente unabhängig von der Benutzer Bewegung verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="05c7b-382">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="05c7b-383">Wenn der Benutzer z. b. eine 3D-Karte mit Zoom anzeigen und durchläuft, sollte das Zoom Steuerelement dem Benutzer unabhängig von der Position sofort verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="05c7b-383">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="05c7b-384">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="05c7b-384">Recommendations</span></span>

* <span data-ttu-id="05c7b-385">Der Benutzer ist die Kamera und steuert die Bewegung.</span><span class="sxs-lookup"><span data-stu-id="05c7b-385">The user is the camera and they control the movement.</span></span> <span data-ttu-id="05c7b-386">Das können Sie steuern.</span><span class="sxs-lookup"><span data-stu-id="05c7b-386">Let them drive.</span></span>
* <span data-ttu-id="05c7b-387">Ziehen Sie die Abrechnung für Text-und menuingsysteme in Erwägung, die andernfalls in der Welt gesperrt oder verdeckt werden, wenn sich ein Benutzer bewegen würde.</span><span class="sxs-lookup"><span data-stu-id="05c7b-387">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="05c7b-388">Verwenden Sie tagzusammen für Inhalte, die dem Benutzer folgen müssen, während der Benutzer weiterhin sehen kann, was vor ihm steht.</span><span class="sxs-lookup"><span data-stu-id="05c7b-388">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="05c7b-389">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="05c7b-389">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="05c7b-390">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="05c7b-390">Documentation</span></span>

* [<span data-ttu-id="05c7b-391">Interaktionsgestaltung</span><span class="sxs-lookup"><span data-stu-id="05c7b-391">Interaction design</span></span>](../../discover/hologram.md)
* [<span data-ttu-id="05c7b-392">Farbe, Licht und Material</span><span class="sxs-lookup"><span data-stu-id="05c7b-392">Color, light, and material</span></span>](../../color,-light-and-materials.md)
* [<span data-ttu-id="05c7b-393">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="05c7b-393">Billboarding and tag-along</span></span>](../../design/billboarding-and-tag-along.md)
* [<span data-ttu-id="05c7b-394">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="05c7b-394">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)
* [<span data-ttu-id="05c7b-395">Eigenbewegung und Ortsveränderung des Benutzers</span><span class="sxs-lookup"><span data-stu-id="05c7b-395">Self-motion and user locomotion</span></span>](../../design/comfort.md#self-motion-and-user-locomotion)

## <a name="input-interaction-clarity"></a><span data-ttu-id="05c7b-396">Klarheit der Eingabe Interaktion</span><span class="sxs-lookup"><span data-stu-id="05c7b-396">Input interaction clarity</span></span>

<span data-ttu-id="05c7b-397">Die Übersichtlichkeit der Eingabe Interaktion ist wichtig für die Benutzerfreundlichkeit einer APP und umfasst Eingabe Konsistenz, genehmigende Zulässigkeit, Auffindbarkeit von Interaktions Methoden.</span><span class="sxs-lookup"><span data-stu-id="05c7b-397">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="05c7b-398">Der Benutzer kann plattformweite allgemeine Interaktionen ohne Relearning verwenden.</span><span class="sxs-lookup"><span data-stu-id="05c7b-398">User can use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="05c7b-399">Wenn die APP benutzerdefinierte Eingaben hat, sollte Sie eindeutig kommuniziert und demonstriert werden.</span><span class="sxs-lookup"><span data-stu-id="05c7b-399">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="05c7b-400">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="05c7b-400">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="05c7b-401"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="05c7b-401"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="05c7b-402"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="05c7b-402"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="05c7b-403">✔️</span><span class="sxs-lookup"><span data-stu-id="05c7b-403">✔️</span></span></td>
        <td><span data-ttu-id="05c7b-404">✔️</span><span class="sxs-lookup"><span data-stu-id="05c7b-404">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="05c7b-405">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="05c7b-405">Quality criteria</span></span>

|  <span data-ttu-id="05c7b-406">Sehr hoch</span><span class="sxs-lookup"><span data-stu-id="05c7b-406">Best</span></span>  |  <span data-ttu-id="05c7b-407">Findet</span><span class="sxs-lookup"><span data-stu-id="05c7b-407">Meets</span></span> |  <span data-ttu-id="05c7b-408">Fehler</span><span class="sxs-lookup"><span data-stu-id="05c7b-408">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="05c7b-409">Eingabe Interaktions Methoden sind mit der von Windows Mixed Reality bereitgestellten [Anleitung](../../design/interaction-fundamentals.md)konsistent.</span><span class="sxs-lookup"><span data-stu-id="05c7b-409">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](../../design/interaction-fundamentals.md).</span></span> <span data-ttu-id="05c7b-410">Alle benutzerdefinierten Eingaben sollten nicht mit der Standardeingabe redundant sein (sondern standardmäßig verwendet werden), und Sie müssen für den Benutzer eindeutig kommuniziert und demonstriert werden.</span><span class="sxs-lookup"><span data-stu-id="05c7b-410">Any custom input shouldn't be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="05c7b-411">Ähnlich wie die beste, aber benutzerdefinierte Eingaben sind bei Standardeingabe Methoden redundant.</span><span class="sxs-lookup"><span data-stu-id="05c7b-411">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="05c7b-412">Der Benutzer kann das Ziel und den Fortschritt auch über die App-Benutzer Leistung erreichen.</span><span class="sxs-lookup"><span data-stu-id="05c7b-412">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="05c7b-413">Das Verständnis der Eingabemethode oder der Schaltflächen Zuordnung ist schwierig.</span><span class="sxs-lookup"><span data-stu-id="05c7b-413">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="05c7b-414">Die Eingabe ist stark angepasst, unterstützt keine Standard Eingaben, keine Anweisungen, oder es werden wahrscheinlich Ermüdungs-und komfortprobleme verursacht.</span><span class="sxs-lookup"><span data-stu-id="05c7b-414">Input is heavily customized, doesn't support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="05c7b-415">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="05c7b-415">How to measure</span></span>

* <span data-ttu-id="05c7b-416">Die APP verwendet konsistente [Standardeingabe Methoden.](../../design/interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="05c7b-416">The app uses consistent [standard input methods.](../../design/interaction-fundamentals.md)</span></span>
* <span data-ttu-id="05c7b-417">Wenn die APP über benutzerdefinierte Eingaben verfügt, wird Sie eindeutig übermittelt:</span><span class="sxs-lookup"><span data-stu-id="05c7b-417">If the app has custom input, it's clearly communicated through:</span></span>
* <span data-ttu-id="05c7b-418">Erstmaligen Testlauf</span><span class="sxs-lookup"><span data-stu-id="05c7b-418">First-run experience</span></span>
* <span data-ttu-id="05c7b-419">Einführungs Bildschirme</span><span class="sxs-lookup"><span data-stu-id="05c7b-419">Introductory screens</span></span>
* <span data-ttu-id="05c7b-420">QuickInfos</span><span class="sxs-lookup"><span data-stu-id="05c7b-420">Tooltips</span></span>
* <span data-ttu-id="05c7b-421">Hand Coach</span><span class="sxs-lookup"><span data-stu-id="05c7b-421">Hand coach</span></span>
* <span data-ttu-id="05c7b-422">Hilfe Abschnitt</span><span class="sxs-lookup"><span data-stu-id="05c7b-422">Help section</span></span>
* <span data-ttu-id="05c7b-423">Voice-over</span><span class="sxs-lookup"><span data-stu-id="05c7b-423">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="05c7b-424">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="05c7b-424">Recommendations</span></span>

* <span data-ttu-id="05c7b-425">Verwenden Sie nach Möglichkeit immer Standardeingabe Methoden.</span><span class="sxs-lookup"><span data-stu-id="05c7b-425">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="05c7b-426">Stellen Sie Demonstrationen, Tutorials und Quick Infos für nicht standardmäßige Eingabemethoden bereit.</span><span class="sxs-lookup"><span data-stu-id="05c7b-426">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="05c7b-427">Verwenden Sie in der gesamten App ein konsistentes Interaktionsmodell.</span><span class="sxs-lookup"><span data-stu-id="05c7b-427">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="05c7b-428">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="05c7b-428">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="05c7b-429">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="05c7b-429">Documentation</span></span>

* [<span data-ttu-id="05c7b-430">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="05c7b-430">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)
* [<span data-ttu-id="05c7b-431">Interactable-Objekte</span><span class="sxs-lookup"><span data-stu-id="05c7b-431">Interactable objects</span></span>](../../design/interactable-object.md)
* [<span data-ttu-id="05c7b-432">Anvisieren mit dem Kopf und Verweilen</span><span class="sxs-lookup"><span data-stu-id="05c7b-432">Head-gaze and dwell</span></span>](../../design/gaze-and-dwell.md)
* [<span data-ttu-id="05c7b-433">Cursor</span><span class="sxs-lookup"><span data-stu-id="05c7b-433">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="05c7b-434">Komfort und Blick</span><span class="sxs-lookup"><span data-stu-id="05c7b-434">Comfort and gaze</span></span>](../../design/comfort.md#gaze-direction)
* [<span data-ttu-id="05c7b-435">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="05c7b-435">Voice input</span></span>](../../design/voice-input.md)
* [<span data-ttu-id="05c7b-436">Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="05c7b-436">Motion controllers</span></span>](../../design/motion-controllers.md)
* [<span data-ttu-id="05c7b-437">Leitfaden für Eingabeportierung für Unity</span><span class="sxs-lookup"><span data-stu-id="05c7b-437">Input porting guide for Unity</span></span>](../porting-apps/input-porting-guide-for-unity.md)
* [<span data-ttu-id="05c7b-438">Tastatureingabe in Unity</span><span class="sxs-lookup"><span data-stu-id="05c7b-438">Keyboard input in Unity</span></span>](../unity/keyboard-input-in-unity.md)
* [<span data-ttu-id="05c7b-439">Anvisieren in Unity</span><span class="sxs-lookup"><span data-stu-id="05c7b-439">Gaze in Unity</span></span>](../unity/gaze-in-unity.md)
* [<span data-ttu-id="05c7b-440">Motion-Controller in Unity</span><span class="sxs-lookup"><span data-stu-id="05c7b-440">Motion controllers in Unity</span></span>](../unity/motion-controllers-in-unity.md)
* [<span data-ttu-id="05c7b-441">Gesten in Unity</span><span class="sxs-lookup"><span data-stu-id="05c7b-441">Gestures in Unity</span></span>](../unity/gestures-in-unity.md)
* [<span data-ttu-id="05c7b-442">Spracheingabe in Unity</span><span class="sxs-lookup"><span data-stu-id="05c7b-442">Voice input in Unity</span></span>](../unity/voice-input-in-unity.md)
* [<span data-ttu-id="05c7b-443">Tastatur-, Maus- und Controllereingaben in DirectX</span><span class="sxs-lookup"><span data-stu-id="05c7b-443">Keyboard, mouse, and controller input in DirectX</span></span>](../../keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="05c7b-444">Anvisieren mit dem Kopf und mit den Augen in DirectX</span><span class="sxs-lookup"><span data-stu-id="05c7b-444">Head and eye gaze in DirectX</span></span>](../native/gaze-in-directx.md)
* [<span data-ttu-id="05c7b-445">Hände und Motion-Controller in DirectX</span><span class="sxs-lookup"><span data-stu-id="05c7b-445">Hands and motion controllers in DirectX</span></span>](../native/hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="05c7b-446">Spracheingabe in DirectX</span><span class="sxs-lookup"><span data-stu-id="05c7b-446">Voice input in DirectX</span></span>](../native/voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="05c7b-447">Tools und Tutorials</span><span class="sxs-lookup"><span data-stu-id="05c7b-447">Tools and tutorials</span></span>

* [<span data-ttu-id="05c7b-448">Fallstudie: die Verfolgung von mehr persönlichen Computing</span><span class="sxs-lookup"><span data-stu-id="05c7b-448">Case study: The pursuit of more personal computing</span></span>](../../out-of-scope/case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="05c7b-449">Umwandlungs Studie: Entwicklung von holostudio-UI-und Interaktions Entwürfen</span><span class="sxs-lookup"><span data-stu-id="05c7b-449">Cast study: HoloStudio UI and interaction design learnings</span></span>](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="05c7b-450">Beispiel-App: periodische Tabelle der Elemente</span><span class="sxs-lookup"><span data-stu-id="05c7b-450">Sample app: Periodic table of the elements</span></span>](../unity/periodic-table-of-the-elements.md)
* [<span data-ttu-id="05c7b-451">Beispiel-App: Mond Modul</span><span class="sxs-lookup"><span data-stu-id="05c7b-451">Sample app: Lunar module</span></span>](../unity/lunar-module.md)

## <a name="interactable-objects"></a><span data-ttu-id="05c7b-452">Interactable-Objekte</span><span class="sxs-lookup"><span data-stu-id="05c7b-452">Interactable objects</span></span>

<span data-ttu-id="05c7b-453">Eine Schaltfläche ist lange eine Metapher, die zum Auslösen eines Ereignisses in der 2D-abstrakten Welt verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="05c7b-453">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="05c7b-454">In der dreidimensionalen Mixed Reality-Welt müssen wir nicht mehr auf diese Abstraktions Welt beschränkt werden.</span><span class="sxs-lookup"><span data-stu-id="05c7b-454">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="05c7b-455">Dabei kann es sich um ein Objekt handeln, das ein Objekt ist, das ein Ereignis auslöst.</span><span class="sxs-lookup"><span data-stu-id="05c7b-455">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="05c7b-456">Ein Objekt, das sich in der Tabelle befindet, kann als beliebiger von einem Kaffeebecher in der Tabelle dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="05c7b-456">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="05c7b-457">Unabhängig vom Formular sollte der Benutzer durch visuelle und Audiohinweise eindeutig erkennbar sein.</span><span class="sxs-lookup"><span data-stu-id="05c7b-457">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="05c7b-458">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="05c7b-458">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="05c7b-459"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="05c7b-459"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="05c7b-460"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="05c7b-460"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="05c7b-461">✔️</span><span class="sxs-lookup"><span data-stu-id="05c7b-461">✔️</span></span></td>
        <td><span data-ttu-id="05c7b-462">✔️</span><span class="sxs-lookup"><span data-stu-id="05c7b-462">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="05c7b-463">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="05c7b-463">Quality criteria</span></span>

|  <span data-ttu-id="05c7b-464">Sehr hoch</span><span class="sxs-lookup"><span data-stu-id="05c7b-464">Best</span></span>  |  <span data-ttu-id="05c7b-465">Findet</span><span class="sxs-lookup"><span data-stu-id="05c7b-465">Meets</span></span> |  <span data-ttu-id="05c7b-466">Fehler</span><span class="sxs-lookup"><span data-stu-id="05c7b-466">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="05c7b-467">Unabhängig von der Form sind Interaktionen-Objekte durch visuelle und Audiohinweise in drei Zuständen erkennbar: im Leerlauf, gezielt und ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="05c7b-467">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="05c7b-468">"Wie Sie sehen, ist es klar und in der gesamten gesamten Darstellung verwendet.</span><span class="sxs-lookup"><span data-stu-id="05c7b-468">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="05c7b-469">Objekte werden skaliert und verteilt, um eine fehlerfreie Zielversion zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="05c7b-469">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="05c7b-470">Der Benutzer kann das Objekt als Interaktionen durch Audiomaterial oder visuelles Feedback erkennen und das Objekt auf das Objekt ausrichten und aktivieren.</span><span class="sxs-lookup"><span data-stu-id="05c7b-470">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="05c7b-471">Wenn keine visuellen oder Audiohinweise angezeigt werden, kann der Benutzer kein Objekt mit Interaktionen erkennen.</span><span class="sxs-lookup"><span data-stu-id="05c7b-471">Given no visual or audio cues, user can't recognize an interactable object.</span></span> <span data-ttu-id="05c7b-472">Interaktionen sind aufgrund der Objekt Skala oder der Entfernung zwischen Objekten fehleranfällig.</span><span class="sxs-lookup"><span data-stu-id="05c7b-472">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="05c7b-473">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="05c7b-473">How to measure</span></span>

* <span data-ttu-id="05c7b-474">Interactable-Objekte sind als "interactable" erkennbar. einschließen von Schaltflächen, Menüs und App-spezifischem Inhalt.</span><span class="sxs-lookup"><span data-stu-id="05c7b-474">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app-specific content.</span></span> <span data-ttu-id="05c7b-475">Als Faustregel gilt, dass ein visueller und audiohinweis vorhanden sein sollte, wenn Sie auf Objekte mit Interaktionen abzielen.</span><span class="sxs-lookup"><span data-stu-id="05c7b-475">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="05c7b-476">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="05c7b-476">Recommendations</span></span>

* <span data-ttu-id="05c7b-477">Verwenden Sie visuelles und Audiofeedback für Interaktionen.</span><span class="sxs-lookup"><span data-stu-id="05c7b-477">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="05c7b-478">Visuelles Feedback sollte für jeden Eingabe Status unterschieden werden (im Leerlauf, gezielt, ausgewählt).</span><span class="sxs-lookup"><span data-stu-id="05c7b-478">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="05c7b-479">Interactable-Objekte sollten skaliert und für fehlerfreie Zielgruppen vorgesehen werden.</span><span class="sxs-lookup"><span data-stu-id="05c7b-479">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="05c7b-480">Gruppierte Interaktionen-Objekte (z. b. eine Menüleiste oder Liste) sollten über den richtigen Abstand zum Ziel verfügen.</span><span class="sxs-lookup"><span data-stu-id="05c7b-480">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="05c7b-481">Schaltflächen und Menüs, die den Voice-Befehl unterstützen, sollten Text Bezeichnungen für das Befehls Schlüsselwort bereitstellen ("siehe IT, sagen Sie")</span><span class="sxs-lookup"><span data-stu-id="05c7b-481">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="05c7b-482">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="05c7b-482">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="05c7b-483">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="05c7b-483">Documentation</span></span>

* [<span data-ttu-id="05c7b-484">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="05c7b-484">Interactable object</span></span>](../../design/interactable-object.md)
* [<span data-ttu-id="05c7b-485">Text in Unity</span><span class="sxs-lookup"><span data-stu-id="05c7b-485">Text in Unity</span></span>](../unity/text-in-unity.md)
* [<span data-ttu-id="05c7b-486">Begrenzungsrahmen und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="05c7b-486">Bounding box and App bar</span></span>](../../design/app-bar-and-bounding-box.md)
* [<span data-ttu-id="05c7b-487">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="05c7b-487">Voice input</span></span>](../../design/voice-input.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="05c7b-488">Tools und Tutorials</span><span class="sxs-lookup"><span data-stu-id="05c7b-488">Tools and tutorials</span></span>

* [<span data-ttu-id="05c7b-489">Mixed Reality Toolkit-UX</span><span class="sxs-lookup"><span data-stu-id="05c7b-489">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="05c7b-490">Raum Überprüfung</span><span class="sxs-lookup"><span data-stu-id="05c7b-490">Room scanning</span></span>

<span data-ttu-id="05c7b-491">Apps, die räumliche Daten für die Zuordnung benötigen, benötigen das Gerät, um diese Daten automatisch über einen Zeitraum und Sitzungs übergreifend zu erfassen, da der Benutzer seine Umgebung mit dem aktiven Gerät untersucht.</span><span class="sxs-lookup"><span data-stu-id="05c7b-491">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="05c7b-492">Die Vollständigkeit und Qualität dieser Daten hängt von einer Reihe von Faktoren ab, z. b. vom Umfang der durchgeführten Untersuchung, von der seit der Durchsuchung übergebenen Zeit und davon, ob Objekte wie z. b. Möbel und Türen verschoben wurden, seit das Gerät den Bereich überprüft hat.</span><span class="sxs-lookup"><span data-stu-id="05c7b-492">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="05c7b-493">Viele apps analysieren die räumlichen Zuordnungs Daten zu Beginn der Benutzer Darstellung, um zu beurteilen, ob der Benutzer zusätzliche Schritte ausführen muss, um die Vollständigkeit und Qualität der räumlichen Karte zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="05c7b-493">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="05c7b-494">Wenn der Benutzer die Umgebung scannen muss, sollten Sie während der Überprüfung eine klare Anleitung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="05c7b-494">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="05c7b-495">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="05c7b-495">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="05c7b-496"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="05c7b-496"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="05c7b-497"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="05c7b-497"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="05c7b-498">✔️</span><span class="sxs-lookup"><span data-stu-id="05c7b-498">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="05c7b-499">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="05c7b-499">Quality criteria</span></span>

|  <span data-ttu-id="05c7b-500">Sehr hoch</span><span class="sxs-lookup"><span data-stu-id="05c7b-500">Best</span></span>  |  <span data-ttu-id="05c7b-501">Findet</span><span class="sxs-lookup"><span data-stu-id="05c7b-501">Meets</span></span> |  <span data-ttu-id="05c7b-502">Fehler</span><span class="sxs-lookup"><span data-stu-id="05c7b-502">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="05c7b-503">Die Visualisierung des räumlichen Netzes weist auf die Überprüfung von Benutzern hin.</span><span class="sxs-lookup"><span data-stu-id="05c7b-503">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="05c7b-504">Der Benutzer weiß eindeutig, was zu tun ist und wann die Überprüfung gestartet und beendet wird.</span><span class="sxs-lookup"><span data-stu-id="05c7b-504">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="05c7b-505">Die Visualisierung des räumlichen Netzes wird bereitgestellt, aber der Benutzer weiß möglicherweise nicht, was zu tun ist, und es werden keine Fortschrittsinformationen bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="05c7b-505">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="05c7b-506">Keine Visualisierung von Mesh.</span><span class="sxs-lookup"><span data-stu-id="05c7b-506">No visualization of mesh.</span></span> <span data-ttu-id="05c7b-507">Für den Benutzer werden keine Leitfäden bezüglich des abzurufenden oder zum Starten/Beenden der Überprüfung bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="05c7b-507">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="05c7b-508">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="05c7b-508">How to measure</span></span>

* <span data-ttu-id="05c7b-509">Während eines erforderlichen Raum Scans werden visuelle und audioanleitungen bereitgestellt, die angeben, wo gesucht werden soll und wann das Scannen gestartet und beendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="05c7b-509">During a required room scan, visual and audio guidance are provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="05c7b-510">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="05c7b-510">Recommendations</span></span>

* <span data-ttu-id="05c7b-511">Geben Sie an, wie viel des gesamten Volumes in der Benutzerumgebung in der Umgebung enthalten sein muss.</span><span class="sxs-lookup"><span data-stu-id="05c7b-511">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="05c7b-512">Kommunizieren, wenn die Überprüfung gestartet und beendet wird, z. b. eine Statusanzeige.</span><span class="sxs-lookup"><span data-stu-id="05c7b-512">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="05c7b-513">Verwenden Sie während des Scanvorgangs eine Visualisierung des Netzes.</span><span class="sxs-lookup"><span data-stu-id="05c7b-513">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="05c7b-514">Stellen Sie visuelle und Audiohinweise bereit, um den Benutzer zu unterstützen, um den Raum zu sehen und zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="05c7b-514">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="05c7b-515">Informieren Sie den Benutzer, wohin Sie die Daten verbessern möchten.</span><span class="sxs-lookup"><span data-stu-id="05c7b-515">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="05c7b-516">In vielen Fällen kann es am besten sein, den Benutzern mitzuteilen, was Sie tun müssen (z. b. die Obergrenze, das Aussehen hinter den Möbeln), um die erforderliche Scanqualität zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="05c7b-516">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="05c7b-517">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="05c7b-517">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="05c7b-518">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="05c7b-518">Documentation</span></span>

* [<span data-ttu-id="05c7b-519">Raumabtastvisualisierung</span><span class="sxs-lookup"><span data-stu-id="05c7b-519">Room scan visualization</span></span>](../../design/room-scan-visualization.md)
* [<span data-ttu-id="05c7b-520">Fallstudie: Erweitern der Funktionen für räumliche Zuordnung von hololens</span><span class="sxs-lookup"><span data-stu-id="05c7b-520">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="05c7b-521">Fallstudie: räumliches Sound Design für holotour</span><span class="sxs-lookup"><span data-stu-id="05c7b-521">Case study: Spatial sound design for HoloTour</span></span>](../../design/case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="05c7b-522">Fallstudie: Erstellen eines immersiven Erlebnisses in Fragmenten</span><span class="sxs-lookup"><span data-stu-id="05c7b-522">Case study: Creating an immersive experience in Fragments</span></span>](../../out-of-scope/case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="05c7b-523">Tools und Tutorials</span><span class="sxs-lookup"><span data-stu-id="05c7b-523">Tools and tutorials</span></span>

* [<span data-ttu-id="05c7b-524">Mixed Reality Toolkit-UX</span><span class="sxs-lookup"><span data-stu-id="05c7b-524">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="05c7b-525">Direktionale Indikatoren</span><span class="sxs-lookup"><span data-stu-id="05c7b-525">Directional indicators</span></span>

<span data-ttu-id="05c7b-526">In einer Mixed Reality-App kann es sein, dass sich Inhalte außerhalb des Felds befinden oder durch reale Objekte verdeckt werden.</span><span class="sxs-lookup"><span data-stu-id="05c7b-526">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="05c7b-527">Eine gut entworfene App erleichtert dem Benutzer das Auffinden nicht sichtbarer Inhalte.</span><span class="sxs-lookup"><span data-stu-id="05c7b-527">A well-designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="05c7b-528">Direktionale Indikatoren warnen einen Benutzer für wichtige Inhalte und bieten Anleitungen für den Inhalt in Bezug auf die Position des Benutzers an.</span><span class="sxs-lookup"><span data-stu-id="05c7b-528">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="05c7b-529">Anleitungen für nicht sichtbare Inhalte können als audioemitter, direktionale Pfeile oder direkte visuelle Hinweise genutzt werden.</span><span class="sxs-lookup"><span data-stu-id="05c7b-529">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="05c7b-530">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="05c7b-530">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="05c7b-531"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="05c7b-531"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="05c7b-532"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="05c7b-532"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="05c7b-533">✔️</span><span class="sxs-lookup"><span data-stu-id="05c7b-533">✔️</span></span></td>
        <td><span data-ttu-id="05c7b-534">✔️</span><span class="sxs-lookup"><span data-stu-id="05c7b-534">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="05c7b-535">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="05c7b-535">Quality criteria</span></span>

|  <span data-ttu-id="05c7b-536">Sehr hoch</span><span class="sxs-lookup"><span data-stu-id="05c7b-536">Best</span></span>  |  <span data-ttu-id="05c7b-537">Findet</span><span class="sxs-lookup"><span data-stu-id="05c7b-537">Meets</span></span> |  <span data-ttu-id="05c7b-538">Fehler</span><span class="sxs-lookup"><span data-stu-id="05c7b-538">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="05c7b-539">Visuelle und Audiohinweise leiten den Benutzer direkt an relevante Inhalte außerhalb des Felds der Ansicht.</span><span class="sxs-lookup"><span data-stu-id="05c7b-539">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="05c7b-540">Ein Pfeil oder ein Indikator, der den Benutzer in der allgemeinen Richtung des Inhalts zeigt.</span><span class="sxs-lookup"><span data-stu-id="05c7b-540">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="05c7b-541">Relevante Inhalte sind nicht in der Ansicht enthalten, und dem Benutzer wird ein schlechter oder kein Orts Leit Faden bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="05c7b-541">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="05c7b-542">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="05c7b-542">How to measure</span></span>

* <span data-ttu-id="05c7b-543">Relevante Inhalte außerhalb des Benutzer Felds können durch visuelle und/oder Audiohinweise erkannt werden.</span><span class="sxs-lookup"><span data-stu-id="05c7b-543">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="05c7b-544">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="05c7b-544">Recommendations</span></span>

* <span data-ttu-id="05c7b-545">Wenn relevante Inhalte außerhalb des Benutzer Felds liegen, verwenden Sie richtungsindikatoren und Audiohinweise, um den Benutzer zum Inhalt zu leiten.</span><span class="sxs-lookup"><span data-stu-id="05c7b-545">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="05c7b-546">In vielen Fällen wird ein direkter visueller Leitfaden als direktionale Pfeile bevorzugt.</span><span class="sxs-lookup"><span data-stu-id="05c7b-546">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="05c7b-547">Direktionale Indikatoren sollten nicht in den Cursor integriert werden.</span><span class="sxs-lookup"><span data-stu-id="05c7b-547">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="05c7b-548">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="05c7b-548">Resources</span></span>

* [<span data-ttu-id="05c7b-549">Holografischer Rahmen</span><span class="sxs-lookup"><span data-stu-id="05c7b-549">Holographic frame</span></span>](../../design/holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="05c7b-550">Laden von Daten</span><span class="sxs-lookup"><span data-stu-id="05c7b-550">Data loading</span></span>

<span data-ttu-id="05c7b-551">Ein Statussteuerelement gibt dem Benutzer eine Rückmeldung, dass ein Vorgang mit langer Laufzeit ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="05c7b-551">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="05c7b-552">Dies kann bedeuten, dass der Benutzer nicht mit der APP interagieren kann, wenn die Statusanzeige sichtbar ist, und auch angeben kann, wie lange die Wartezeit dauern kann.</span><span class="sxs-lookup"><span data-stu-id="05c7b-552">It can mean that the user can't interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="05c7b-553">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="05c7b-553">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="05c7b-554"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="05c7b-554"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="05c7b-555"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="05c7b-555"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="05c7b-556">✔️</span><span class="sxs-lookup"><span data-stu-id="05c7b-556">✔️</span></span></td>
        <td><span data-ttu-id="05c7b-557">✔️</span><span class="sxs-lookup"><span data-stu-id="05c7b-557">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="05c7b-558">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="05c7b-558">Quality criteria</span></span>

|  <span data-ttu-id="05c7b-559">Sehr hoch</span><span class="sxs-lookup"><span data-stu-id="05c7b-559">Best</span></span>  |  <span data-ttu-id="05c7b-560">Findet</span><span class="sxs-lookup"><span data-stu-id="05c7b-560">Meets</span></span> |  <span data-ttu-id="05c7b-561">Fehler</span><span class="sxs-lookup"><span data-stu-id="05c7b-561">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="05c7b-562">Animierter visueller Indikator in Form einer Statusanzeige oder eines Rings, der den Fortschritt beim Laden oder Verarbeiten von Daten anzeigt.</span><span class="sxs-lookup"><span data-stu-id="05c7b-562">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="05c7b-563">Der visuelle Indikator gibt eine Anleitung dazu, wie lange der Warte Vorgang sein könnte.</span><span class="sxs-lookup"><span data-stu-id="05c7b-563">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="05c7b-564">Der Benutzer wird darüber informiert, dass das Laden von Daten ausgeführt wird. es gibt jedoch keinen Hinweis darauf, wie lange der Warte Vorgang sein könnte.</span><span class="sxs-lookup"><span data-stu-id="05c7b-564">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="05c7b-565">Das Laden von Daten oder das Verarbeiten von Indikatoren für den Task dauert länger als 5 Sekunden.</span><span class="sxs-lookup"><span data-stu-id="05c7b-565">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="05c7b-566">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="05c7b-566">How to measure</span></span>

* <span data-ttu-id="05c7b-567">Vergewissern Sie sich beim Laden von Daten, dass es für mehr als 5 Sekunden keinen leeren Zustand gibt.</span><span class="sxs-lookup"><span data-stu-id="05c7b-567">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="05c7b-568">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="05c7b-568">Recommendations</span></span>

* <span data-ttu-id="05c7b-569">Stellen Sie eine Animation zum Laden von Daten bereit, die den Fortschritt in jeder Situation anzeigt, in der der Benutzer diese APP möglicherweise als angehalten oder abstürzt</span><span class="sxs-lookup"><span data-stu-id="05c7b-569">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="05c7b-570">Eine vernünftige Faustregel ist jede "Lade Aktivität", die mehr als 5 Sekunden in Anspruch nehmen kann.</span><span class="sxs-lookup"><span data-stu-id="05c7b-570">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="05c7b-571">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="05c7b-571">Resources</span></span>

* [<span data-ttu-id="05c7b-572">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="05c7b-572">Displaying progress</span></span>](../../design/progress.md)
