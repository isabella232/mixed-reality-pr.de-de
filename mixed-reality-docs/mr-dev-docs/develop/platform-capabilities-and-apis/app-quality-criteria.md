---
title: Kriterien für die App-Qualität
description: In diesem Dokument werden die wichtigsten Faktoren beschrieben, die sich auf die Qualität von Mixed Reality-apps auswirken.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: App-Qualitätskriterien, gemischte Realität, Mixed Reality-APP, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: c18f4e8470f7f183fdf250472fd3a977f925dfbf
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677989"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="8165f-104">Kriterien für die App-Qualität</span><span class="sxs-lookup"><span data-stu-id="8165f-104">App quality criteria</span></span>

<span data-ttu-id="8165f-105">In diesem Dokument werden die wichtigsten Faktoren beschrieben, die sich auf die Qualität von Mixed Reality-apps auswirken.</span><span class="sxs-lookup"><span data-stu-id="8165f-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="8165f-106">Für jeden Faktor werden die folgenden Informationen bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="8165f-106">For each factor the following information is provided</span></span>
* <span data-ttu-id="8165f-107">Übersicht – eine kurze Beschreibung des Qualitäts Faktors und deren Wichtigkeit.</span><span class="sxs-lookup"><span data-stu-id="8165f-107">Overview – a brief description of the quality factor and why it is important.</span></span>
* <span data-ttu-id="8165f-108">Geräte Auswirkung: der Typ des Windows Mixed Reality-Geräts ist beeinträchtigt.</span><span class="sxs-lookup"><span data-stu-id="8165f-108">Device impact - which type of Window Mixed Reality device is impacted.</span></span>
* <span data-ttu-id="8165f-109">Qualitätskriterien – Auswerten des Qualitäts Faktors.</span><span class="sxs-lookup"><span data-stu-id="8165f-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="8165f-110">So messen Sie –-Methoden, um das Problem zu messen (oder zu erleben).</span><span class="sxs-lookup"><span data-stu-id="8165f-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="8165f-111">Empfehlungen – Zusammenfassung der Ansätze, um eine bessere Benutzer Leistung zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="8165f-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="8165f-112">Ressourcen – relevante Entwickler-und Entwurfs Ressourcen, die nützlich sind, um bessere App-Erfahrungen zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="8165f-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="8165f-113">Bildfrequenz</span><span class="sxs-lookup"><span data-stu-id="8165f-113">Frame rate</span></span>

<span data-ttu-id="8165f-114">Die Framerate ist die erste Säule der – Hologramm-Stabilität und des Benutzer Komforts.</span><span class="sxs-lookup"><span data-stu-id="8165f-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="8165f-115">Die Frame Rate unterhalb der empfohlenen Ziele kann dazu führen, dass holograms Jittery werden, was sich negativ auf die glaub Fähigkeit der Funktionalität auswirkt und möglicherweise Augen Müdigkeit auslöst.</span><span class="sxs-lookup"><span data-stu-id="8165f-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="8165f-116">Die zielframeworkrate für Ihre Benutzeroberflächen in Windows Mixed Reality-immersiven Headsets ist entweder 60Hz oder 90Hz, je nachdem, welche Windows Mixed Reality-kompatiblen PCs Sie unterstützen möchten.</span><span class="sxs-lookup"><span data-stu-id="8165f-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets will be either 60Hz or 90Hz depending on which Windows Mixed Reality Compatible PCs you wish to support.</span></span> <span data-ttu-id="8165f-117">Bei hololens beträgt die zielframeworkrate 60Hz.</span><span class="sxs-lookup"><span data-stu-id="8165f-117">For HoloLens the target frame rate is 60Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="8165f-118">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="8165f-118">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="8165f-119"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="8165f-119"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="8165f-120"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="8165f-120"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="8165f-121">✔️</span><span class="sxs-lookup"><span data-stu-id="8165f-121">✔️</span></span></td>
        <td><span data-ttu-id="8165f-122">✔️</span><span class="sxs-lookup"><span data-stu-id="8165f-122">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="8165f-123">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="8165f-123">Quality criteria</span></span>

|  <span data-ttu-id="8165f-124">Sehr hoch</span><span class="sxs-lookup"><span data-stu-id="8165f-124">Best</span></span>  |  <span data-ttu-id="8165f-125">Findet</span><span class="sxs-lookup"><span data-stu-id="8165f-125">Meets</span></span> |  <span data-ttu-id="8165f-126">Fehler</span><span class="sxs-lookup"><span data-stu-id="8165f-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="8165f-127">Die APP erfüllt konstant Frames pro Sekunde (fps) für Zielgerät: 60fps on hololens; 90fps auf ultrapcs; und 60fps auf gängigen PCs.</span><span class="sxs-lookup"><span data-stu-id="8165f-127">The app consistently meets frames per second (FPS) goal for target device: 60fps on HoloLens; 90fps on Ultra PCs; and 60fps on mainstream PCs.</span></span> | <span data-ttu-id="8165f-128">Die APP verfügt über zeitweilig auftretende Frame-Abstürze, die die Kernfunktionen nicht behindern. oder FPS ist konstant niedriger als das gewünschte Ziel, verhindert jedoch die APP-Darstellung.</span><span class="sxs-lookup"><span data-stu-id="8165f-128">The app has intermittent frame drops not impeding the core experience; or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="8165f-129">In der APP tritt im Durchschnitt alle zehn Sekunden eine Dropdown-Rate auf.</span><span class="sxs-lookup"><span data-stu-id="8165f-129">The app is experiencing a drop in frame rate on average every ten seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="8165f-130">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="8165f-130">How to measure</span></span>

* <span data-ttu-id="8165f-131">Ein Echtzeit-Frameraten Diagramm wird durch das [Windows-Geräte Portal](using-the-windows-device-portal.md#system-performance) unter "System Leistung" bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="8165f-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="8165f-132">Fügen Sie für das Entwicklungs Debuggen der APP einen framerraten-diagnosecounter hinzu.</span><span class="sxs-lookup"><span data-stu-id="8165f-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="8165f-133">Einen Beispiel Zählers finden Sie unter Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="8165f-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="8165f-134">Die abfrageate können auf dem Gerät auftreten, während die app ausgeführt wird, indem Sie Ihren Kopf von der Seite zu Seite wechseln.</span><span class="sxs-lookup"><span data-stu-id="8165f-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="8165f-135">Wenn das – Hologramm unerwartete gezittert-Bewegung anzeigt, ist die niedrige Framerate oder die Stabilitäts Ebene wahrscheinlich die Ursache.</span><span class="sxs-lookup"><span data-stu-id="8165f-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="8165f-136">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="8165f-136">Recommendations</span></span>

* <span data-ttu-id="8165f-137">Fügen Sie am Anfang der Entwicklungsarbeit einen Frameraten-Counter hinzu.</span><span class="sxs-lookup"><span data-stu-id="8165f-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="8165f-138">Änderungen, die eine Ablage in der Framerate verursachen, sollten ausgewertet und als Leistungsfehler entsprechend aufgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="8165f-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="8165f-139">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="8165f-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="8165f-140">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="8165f-140">Documentation</span></span>

* [<span data-ttu-id="8165f-141">Grundlegendes zur Leistung für gemischte Realität</span><span class="sxs-lookup"><span data-stu-id="8165f-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="8165f-142">Hologram Stabilität und Framerate</span><span class="sxs-lookup"><span data-stu-id="8165f-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="8165f-143">Asset Performance Budget</span><span class="sxs-lookup"><span data-stu-id="8165f-143">Asset performance budget</span></span>](../../design/asset-creation-process.md)
* [<span data-ttu-id="8165f-144">Leistungsempfehlungen für Unity</span><span class="sxs-lookup"><span data-stu-id="8165f-144">Performance recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="8165f-145">Tools und Tutorials</span><span class="sxs-lookup"><span data-stu-id="8165f-145">Tools and tutorials</span></span>

* [<span data-ttu-id="8165f-146">Mrtoolkit, FPS-Counter-Anzeige</span><span class="sxs-lookup"><span data-stu-id="8165f-146">MRToolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="8165f-147">Mrtoolkit, Shaders</span><span class="sxs-lookup"><span data-stu-id="8165f-147">MRToolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="8165f-148">Externe Verweise</span><span class="sxs-lookup"><span data-stu-id="8165f-148">External references</span></span>

* [<span data-ttu-id="8165f-149">Unity, optimieren mobiler Anwendungen</span><span class="sxs-lookup"><span data-stu-id="8165f-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="8165f-150">Hologrammstabilität</span><span class="sxs-lookup"><span data-stu-id="8165f-150">Hologram stability</span></span>

<span data-ttu-id="8165f-151">Stabile Hologramme verbessern die Benutzerfreundlichkeit und Glaubwürdigkeit Ihrer APP und sorgen für einen komfortableren Anzeige Vorgang für den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="8165f-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="8165f-152">Die Qualität der – Hologramm-Stabilität ist das Ergebnis einer guten App-Entwicklung und der Fähigkeit des Geräts, die Umgebung zu verstehen (nachverfolgen).</span><span class="sxs-lookup"><span data-stu-id="8165f-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="8165f-153">Obwohl die Framerate die erste Säule der Stabilität ist, können sich andere Faktoren auf die Stabilität auswirken, einschließlich:</span><span class="sxs-lookup"><span data-stu-id="8165f-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="8165f-154">Verwendung der Stabilisierungs Ebene</span><span class="sxs-lookup"><span data-stu-id="8165f-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="8165f-155">Entfernung zu räumlichen Ankern</span><span class="sxs-lookup"><span data-stu-id="8165f-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="8165f-156">Nachverfolgung</span><span class="sxs-lookup"><span data-stu-id="8165f-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="8165f-157">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="8165f-157">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="8165f-158"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="8165f-158"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="8165f-159"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="8165f-159"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="8165f-160">✔️</span><span class="sxs-lookup"><span data-stu-id="8165f-160">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="8165f-161">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="8165f-161">Quality criteria</span></span>

|  <span data-ttu-id="8165f-162">Sehr hoch</span><span class="sxs-lookup"><span data-stu-id="8165f-162">Best</span></span>  |  <span data-ttu-id="8165f-163">Findet</span><span class="sxs-lookup"><span data-stu-id="8165f-163">Meets</span></span> |  <span data-ttu-id="8165f-164">Fehler</span><span class="sxs-lookup"><span data-stu-id="8165f-164">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="8165f-165">Holograms werden konsistent angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8165f-165">Holograms consistently appear stable.</span></span> | <span data-ttu-id="8165f-166">Der sekundäre Inhalt zeigt unerwartete Verschiebungen an; oder unerwartete Verschiebungen beeinträchtigen nicht die gesamte App-Leistung.</span><span class="sxs-lookup"><span data-stu-id="8165f-166">Secondary content exhibits unexpected movement; or unexpected movement does not impede overall app experience.</span></span> | <span data-ttu-id="8165f-167">Primärer Inhalt in Frame zeigt unerwartete Bewegung an.</span><span class="sxs-lookup"><span data-stu-id="8165f-167">Primary content in frame exhibits unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="8165f-168">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="8165f-168">How to measure</span></span>

<span data-ttu-id="8165f-169">Beim Ausführen des Geräts und Anzeigen der Anzeige:</span><span class="sxs-lookup"><span data-stu-id="8165f-169">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="8165f-170">Bewegen Sie den Kopf von der Seite zur Seite, wenn die holograms unerwartete Verschiebungen anzeigen, dann ist die niedrige Framerate oder die falsche Ausrichtung der Stabilitäts Ebene auf die Fokusebene die wahrscheinliche Ursache.</span><span class="sxs-lookup"><span data-stu-id="8165f-170">Move your head from side to side, if the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="8165f-171">Navigieren Sie in den holograms und in der Umgebung, und suchen Sie nach Verhaltensweisen wie z. b. Schwimmen und Sprung</span><span class="sxs-lookup"><span data-stu-id="8165f-171">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="8165f-172">Diese Art von Bewegung wird wahrscheinlich dadurch verursacht, dass das Gerät die Umgebung nicht nachverfolgt, oder die Entfernung zum räumlichen Anker.</span><span class="sxs-lookup"><span data-stu-id="8165f-172">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="8165f-173">Wenn sich große oder mehrere holograms im Frame befinden, beobachten Sie das – Hologramm-Verhalten in unterschiedlichen Tiefen, während Sie die Kopfzeile von der Seite zu Seite bewegen, wenn die Schattierung auftritt, wird dies wahrscheinlich durch die Stabilisierungs Ebene verursacht.</span><span class="sxs-lookup"><span data-stu-id="8165f-173">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recommendations"></a><span data-ttu-id="8165f-174">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="8165f-174">Recommendations</span></span>

* <span data-ttu-id="8165f-175">Fügen Sie am Anfang der Entwicklungsarbeit einen Frameraten-Counter hinzu.</span><span class="sxs-lookup"><span data-stu-id="8165f-175">Add an frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="8165f-176">Verwenden Sie die Stabilisierungs Ebene.</span><span class="sxs-lookup"><span data-stu-id="8165f-176">Use the stabilization plane.</span></span>
* <span data-ttu-id="8165f-177">Sie sollten immer verankert Hologramme innerhalb von drei Metern Ihres Ankers darstellen.</span><span class="sxs-lookup"><span data-stu-id="8165f-177">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="8165f-178">Stellen Sie sicher, dass Ihre Umgebung für die ordnungsgemäße Überwachung eingerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="8165f-178">Make sure your environment is setup for proper tracking.</span></span>
* <span data-ttu-id="8165f-179">Entwerfen Sie Ihre Benutzeroberflächen, um Hologramme auf verschiedenen Schwerpunkt Ebenen innerhalb des Rahmens zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="8165f-179">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="8165f-180">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="8165f-180">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="8165f-181">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="8165f-181">Documentation</span></span>

* [<span data-ttu-id="8165f-182">Hologram Stabilität und Framerate</span><span class="sxs-lookup"><span data-stu-id="8165f-182">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="8165f-183">Fallstudie mithilfe der Stabilisierungs Ebene</span><span class="sxs-lookup"><span data-stu-id="8165f-183">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="8165f-184">Grundlegendes zur Leistung für gemischte Realität</span><span class="sxs-lookup"><span data-stu-id="8165f-184">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="8165f-185">Leistungsempfehlungen für Unity</span><span class="sxs-lookup"><span data-stu-id="8165f-185">Performance recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)
* [<span data-ttu-id="8165f-186">Raumanker</span><span class="sxs-lookup"><span data-stu-id="8165f-186">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="8165f-187">Behandeln von nach Verfolgungs Fehlern</span><span class="sxs-lookup"><span data-stu-id="8165f-187">Handling tracking errors</span></span>](../../design/coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="8165f-188">Stationärer Frame des Verweises</span><span class="sxs-lookup"><span data-stu-id="8165f-188">Stationary frame of reference</span></span>](../../design/coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="8165f-189">Tools und Tutorials</span><span class="sxs-lookup"><span data-stu-id="8165f-189">Tools and tutorials</span></span>

* [<span data-ttu-id="8165f-190">Mr Companion Kit, kinect IPD</span><span class="sxs-lookup"><span data-stu-id="8165f-190">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="8165f-191">Holograms-Position auf realen Oberflächen</span><span class="sxs-lookup"><span data-stu-id="8165f-191">Holograms position on real surfaces</span></span>

<span data-ttu-id="8165f-192">Falsche Abweichungen von holograms mit physischen Objekten (wenn Sie in Beziehung zueinander gesetzt werden sollen) sind ein eindeutiger Hinweis auf die nicht-Union von holograms und der realen Welt.</span><span class="sxs-lookup"><span data-stu-id="8165f-192">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) is a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="8165f-193">Die Genauigkeit der Platzierung sollte in Relation zu den Anforderungen des Szenarios liegen. Beispielsweise kann bei der allgemeinen Oberflächen Platzierung die räumliche Karte verwendet werden, aber eine genauere Platzierung erfordert die Verwendung von Markern und die Kalibrierung.</span><span class="sxs-lookup"><span data-stu-id="8165f-193">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="8165f-194">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="8165f-194">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="8165f-195"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="8165f-195"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="8165f-196"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="8165f-196"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="8165f-197">✔️</span><span class="sxs-lookup"><span data-stu-id="8165f-197">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="8165f-198">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="8165f-198">Quality criteria</span></span>

|  <span data-ttu-id="8165f-199">Sehr hoch</span><span class="sxs-lookup"><span data-stu-id="8165f-199">Best</span></span>  |  <span data-ttu-id="8165f-200">Findet</span><span class="sxs-lookup"><span data-stu-id="8165f-200">Meets</span></span> |  <span data-ttu-id="8165f-201">Fehler</span><span class="sxs-lookup"><span data-stu-id="8165f-201">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="8165f-202">Holograms werden an der Oberfläche ausgerichtet, die sich in der Regel im Bereich von Zentimetern bis Zoll</span><span class="sxs-lookup"><span data-stu-id="8165f-202">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="8165f-203">Wenn mehr Genauigkeit erforderlich ist, sollte die APP eine effiziente Möglichkeit zur Zusammenarbeit innerhalb der gewünschten App-Spezifikation bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="8165f-203">If more accuracy is required, the app should provide an efficient means for collaboration within the desired app spec.</span></span> | <span data-ttu-id="8165f-204">–</span><span class="sxs-lookup"><span data-stu-id="8165f-204">NA</span></span> | <span data-ttu-id="8165f-205">Die Hologramme werden mit dem physischen Zielobjekt nicht ausgerichtet angezeigt, indem die Oberfläche unterbrochen wird oder die Fläche von der Oberfläche entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="8165f-205">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="8165f-206">Wenn die Genauigkeit erforderlich ist, sollten holograms die Näherungs Spezifikation des Szenarios erfüllen.</span><span class="sxs-lookup"><span data-stu-id="8165f-206">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="8165f-207">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="8165f-207">How to measure</span></span>

* <span data-ttu-id="8165f-208">Holograms, die auf räumlicher Zuordnung platziert werden, sollten nicht zu einem dramatischen Gleit Komma Wert oberhalb oder unterhalb der Oberfläche erscheinen.</span><span class="sxs-lookup"><span data-stu-id="8165f-208">Holograms that are placed on spatial map should not appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="8165f-209">Holograms, die eine exakte Platzierung erfordern, sollten eine Form von Marker-und Kalibrierungs Systemen aufweisen, die auf die Anforderungen des Szenarios zutreffen.</span><span class="sxs-lookup"><span data-stu-id="8165f-209">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="8165f-210">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="8165f-210">Recommendations</span></span>

* <span data-ttu-id="8165f-211">Die räumliche Zuordnung eignet sich zum Platzieren von Objekten auf Oberflächen, wenn die Genauigkeit nicht erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="8165f-211">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="8165f-212">Verwenden Sie zum Festlegen der optimalen Genauigkeit Marker oder Poster, um die holograms und einen Xbox-Controller (oder einen manuellen Ausrichtungs Mechanismus) für die endgültige Kalibrierung festzulegen.</span><span class="sxs-lookup"><span data-stu-id="8165f-212">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="8165f-213">Es empfiehlt sich, zusätzliche große Hologramme in logische Teile zu zerlegen und die einzelnen Teile an der Oberfläche auszurichten.</span><span class="sxs-lookup"><span data-stu-id="8165f-213">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="8165f-214">Nicht ordnungsgemäß festgelegten interpupillary Distance (IPD) können auch die Ausrichtung von holograms beeinflussen.</span><span class="sxs-lookup"><span data-stu-id="8165f-214">Improperly set interpupillary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="8165f-215">Konfigurieren Sie hololens immer für die IPD des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="8165f-215">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="8165f-216">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="8165f-216">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="8165f-217">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="8165f-217">Documentation</span></span>

* [<span data-ttu-id="8165f-218">Platzierung räumlicher Zuordnung</span><span class="sxs-lookup"><span data-stu-id="8165f-218">Spatial mapping placement</span></span>](../../design/spatial-mapping.md#placement)
* [<span data-ttu-id="8165f-219">Raum Scanprozess</span><span class="sxs-lookup"><span data-stu-id="8165f-219">Room scanning process</span></span>](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="8165f-220">Bewährte Methoden für räumliche Anker</span><span class="sxs-lookup"><span data-stu-id="8165f-220">Spatial anchors best practices</span></span>](../../design/spatial-anchors.md#best-practices)
* [<span data-ttu-id="8165f-221">Behandeln von nach Verfolgungs Fehlern</span><span class="sxs-lookup"><span data-stu-id="8165f-221">Handling tracking errors</span></span>](../../design/coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="8165f-222">Räumliche Abbildung in Unity</span><span class="sxs-lookup"><span data-stu-id="8165f-222">Spatial mapping in Unity</span></span>](../unity/spatial-mapping-in-unity.md)
* [<span data-ttu-id="8165f-223">Übersicht über die vuforia-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="8165f-223">Vuforia development overview</span></span>](../unity/vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="8165f-224">Tools und Tutorials</span><span class="sxs-lookup"><span data-stu-id="8165f-224">Tools and tutorials</span></span>

* [<span data-ttu-id="8165f-225">Mr Toolkit, Bibliotheken für räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="8165f-225">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="8165f-226">Mr Companion Kit, Poster-Kalibrierungs Beispiel</span><span class="sxs-lookup"><span data-stu-id="8165f-226">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="8165f-227">Mr Companion Kit, kinect IPD</span><span class="sxs-lookup"><span data-stu-id="8165f-227">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="8165f-228">Externe Verweise</span><span class="sxs-lookup"><span data-stu-id="8165f-228">External references</span></span>

* [<span data-ttu-id="8165f-229">Lowes-Fallstudie, Genauigkeits Ausrichtung</span><span class="sxs-lookup"><span data-stu-id="8165f-229">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="8165f-230">Anzeigen der Komfortzone</span><span class="sxs-lookup"><span data-stu-id="8165f-230">Viewing zone of comfort</span></span>

<span data-ttu-id="8165f-231">App-Entwickler steuern, wohin die Augen der Benutzer konvergiert werden, indem Sie Inhalte und Hologramme in verschiedenen Tiefen platzieren.</span><span class="sxs-lookup"><span data-stu-id="8165f-231">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="8165f-232">Benutzer, die hololens durchführen, unterstützen immer 2.0 m, um ein klares Bild zu erhalten, da hololens in einer optischen Entfernung von ungefähr 2,0 m vom Benutzer korrigiert werden.</span><span class="sxs-lookup"><span data-stu-id="8165f-232">Users wearing HoloLens will always accommodate to 2.0m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0m away from the user.</span></span> <span data-ttu-id="8165f-233">Eine nicht ordnungsgemäße Inhalts Tiefe kann zu einem visuellen Unbehagen oder Müdigkeit führen.</span><span class="sxs-lookup"><span data-stu-id="8165f-233">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="8165f-234">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="8165f-234">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="8165f-235"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="8165f-235"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="8165f-236"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="8165f-236"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="8165f-237">✔️</span><span class="sxs-lookup"><span data-stu-id="8165f-237">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="8165f-238">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="8165f-238">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="8165f-239">Sehr hoch</span><span class="sxs-lookup"><span data-stu-id="8165f-239">Best</span></span> </td><td><ul>
<li><span data-ttu-id="8165f-240">Platzieren Sie den Inhalt bei 2 m.</span><span class="sxs-lookup"><span data-stu-id="8165f-240">Place content at 2m.</span></span></li><li><span data-ttu-id="8165f-241">Wenn holograms bei 2 m nicht platziert werden können und Konflikte zwischen Konvergenz und Unterbringung nicht vermieden werden können, liegt die optimale Zone für die – Hologramm-Platzierung zwischen 1,25 m und 5 m.</span><span class="sxs-lookup"><span data-stu-id="8165f-241">When holograms cannot be placed at 2m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25m and 5m.</span></span></li><li><span data-ttu-id="8165f-242">In jedem Fall sollten Designer Inhalte strukturieren, um Benutzern die Interaktion von 1 + m zu empfehlen (z. b. Anpassen von Inhalts Größe und Standard Platzierungs Parametern).</span><span class="sxs-lookup"><span data-stu-id="8165f-242">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="8165f-243">Sofern dies nicht speziell für das Szenario erforderlich ist, sollte eine Clippingebene mit "FadeOut" implementiert werden, beginnend bei 1 Mio.</span><span class="sxs-lookup"><span data-stu-id="8165f-243">Unless specifically not required by the scenario, a clipping plane should be implement with fadeout starting at 1m.</span></span></li><li><span data-ttu-id="8165f-244">In Fällen, in denen eine genauere Betrachtung eines sehr großen holograms erforderlich ist, sollte der Inhalt nicht kleiner als 50 cm sein.</span><span class="sxs-lookup"><span data-stu-id="8165f-244">In cases where closer observation of a motionless hologram is required, the content should not be closer than 50cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="8165f-245">Findet</span><span class="sxs-lookup"><span data-stu-id="8165f-245">Meets</span></span></td><td> <span data-ttu-id="8165f-246">Der Inhalt befindet sich in der Anzeige-und Bewegungs Anleitung, aber nicht ordnungsgemäß oder ohne Verwendung der Clippingebene.</span><span class="sxs-lookup"><span data-stu-id="8165f-246">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8165f-247">Fehler</span><span class="sxs-lookup"><span data-stu-id="8165f-247">Fail</span></span> </td><td> <span data-ttu-id="8165f-248">Der Inhalt wird zu nah dargestellt (in der Regel &lt; 1,25 m oder &lt; 50 cm für stationäre Hologramme, die eine genauere Beobachtung erfordern).</span><span class="sxs-lookup"><span data-stu-id="8165f-248">Content is presented too close (typically &lt;1.25m, or &lt;50cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="8165f-249">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="8165f-249">How to measure</span></span>

* <span data-ttu-id="8165f-250">Der Inhalt sollte in der Regel 2 Mio., aber nicht größer als 1,25 oder größer als 5 Mio. sein.</span><span class="sxs-lookup"><span data-stu-id="8165f-250">Content should typically be 2m away, but no closer than 1.25 or further than 5m.</span></span>
* <span data-ttu-id="8165f-251">Mit wenigen Ausnahmen sollte die Länge des Clipping-renderingrenderwerts auf. 85 cm festgelegt werden, wobei die faout-Inhalte beginnend bei 1 Mio. liegen.</span><span class="sxs-lookup"><span data-stu-id="8165f-251">With few exceptions, the HoloLens clipping render distance should be set to .85CM with fadeout of content starting at 1m.</span></span> <span data-ttu-id="8165f-252">Wenden Sie sich an den Inhalt, und notieren Sie sich die Ausschneide Ebene.</span><span class="sxs-lookup"><span data-stu-id="8165f-252">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="8165f-253">Stationärer Inhalt sollte nicht kleiner als 50 cm sein.</span><span class="sxs-lookup"><span data-stu-id="8165f-253">Stationary content should not be closer than 50cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="8165f-254">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="8165f-254">Recommendations</span></span>

* <span data-ttu-id="8165f-255">Entwerfen Sie den Inhalt für die optimale Anzeige Distanz von 2 m.</span><span class="sxs-lookup"><span data-stu-id="8165f-255">Design content for the optimal viewing distance of 2m.</span></span>
* <span data-ttu-id="8165f-256">Legen Sie die Entfernungs-renderingdistanz auf 85 cm mit dem faout-Inhalt ab 1 Mio. fest.</span><span class="sxs-lookup"><span data-stu-id="8165f-256">Set the clipping render distance to 85cm with fadeout of content starting at 1m.</span></span>
* <span data-ttu-id="8165f-257">Bei stationären Hologrammen, die näher betrachtet werden müssen, sollte die Clippingebene nicht größer als 30 cm sein, und Fadeout sollte mindestens 10 cm von der Clippingebene ausgehen.</span><span class="sxs-lookup"><span data-stu-id="8165f-257">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30cm and fadeout should start at least 10cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="8165f-258">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="8165f-258">Resources</span></span>

* [<span data-ttu-id="8165f-259">Rendering-Entfernung</span><span class="sxs-lookup"><span data-stu-id="8165f-259">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="8165f-260">Fokuspunkt in Unity</span><span class="sxs-lookup"><span data-stu-id="8165f-260">Focus point in Unity</span></span>](../unity/focus-point-in-unity.md)
* [<span data-ttu-id="8165f-261">Experimentieren mit der Skala</span><span class="sxs-lookup"><span data-stu-id="8165f-261">Experimenting with scale</span></span>](../../design/scale.md#experimenting-with-scale)
* [<span data-ttu-id="8165f-262">Text, Empfohlene Schriftgröße</span><span class="sxs-lookup"><span data-stu-id="8165f-262">Text, Recommended font size</span></span>](../../design/typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="8165f-263">Tiefen Wechsel</span><span class="sxs-lookup"><span data-stu-id="8165f-263">Depth switching</span></span>

<span data-ttu-id="8165f-264">Unabhängig von der Anzeige Zone von Komfort Problemen kann es sein, dass der Benutzer häufig oder schnell zwischen Near-und Far-Fokus Objekten (einschließlich holograms und realen Inhalten) wechselt.</span><span class="sxs-lookup"><span data-stu-id="8165f-264">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="8165f-265">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="8165f-265">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="8165f-266"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="8165f-266"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="8165f-267"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="8165f-267"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="8165f-268">✔️</span><span class="sxs-lookup"><span data-stu-id="8165f-268">✔️</span></span></td>
        <td><span data-ttu-id="8165f-269">✔️</span><span class="sxs-lookup"><span data-stu-id="8165f-269">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="8165f-270">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="8165f-270">Quality criteria</span></span>

|  <span data-ttu-id="8165f-271">Sehr hoch</span><span class="sxs-lookup"><span data-stu-id="8165f-271">Best</span></span>  |  <span data-ttu-id="8165f-272">Findet</span><span class="sxs-lookup"><span data-stu-id="8165f-272">Meets</span></span> |  <span data-ttu-id="8165f-273">Fehler</span><span class="sxs-lookup"><span data-stu-id="8165f-273">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="8165f-274">Eingeschränkter oder natürlicher tiefen Wechsel, der nicht bewirkt, dass sich der Benutzer nicht ganz natürlich neu konzentriert.</span><span class="sxs-lookup"><span data-stu-id="8165f-274">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="8165f-275">Abrupter tiefen Wechsel hierbei handelt es sich um einen Kern, der in die APP-Umgebung integriert wird, oder um einen abrupten Wechsel, der durch unerwartete reale Inhalte verursacht wurde.</span><span class="sxs-lookup"><span data-stu-id="8165f-275">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="8165f-276">Der konsistente tiefen Wechsel oder der abrupte, nicht erforderliche Wechsel oder Kern der APP-Leistung.</span><span class="sxs-lookup"><span data-stu-id="8165f-276">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="8165f-277">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="8165f-277">How to measure</span></span>

* <span data-ttu-id="8165f-278">Wenn die APP erfordert, dass der Benutzer den tiefen Fokus konsistent und/oder abrupt ändert, liegt ein Problem mit dem tiefen Wechsel vor.</span><span class="sxs-lookup"><span data-stu-id="8165f-278">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="8165f-279">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="8165f-279">Recommendations</span></span>

* <span data-ttu-id="8165f-280">Behalten Sie primären Inhalt in einer konsistenten Fokusebene, und stellen Sie sicher, dass die Stabilisierungs Ebene mit der Fokusebene übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="8165f-280">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="8165f-281">Dadurch wird die oomotor-Müdigkeit und unerwartete – Hologramm-Bewegung verringert.</span><span class="sxs-lookup"><span data-stu-id="8165f-281">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="8165f-282">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="8165f-282">Resources</span></span>

* [<span data-ttu-id="8165f-283">Rendering-Entfernung</span><span class="sxs-lookup"><span data-stu-id="8165f-283">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="8165f-284">Fokuspunkt in Unity</span><span class="sxs-lookup"><span data-stu-id="8165f-284">Focus point in Unity</span></span>](../unity/focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="8165f-285">Verwendung von räumlichem Sound</span><span class="sxs-lookup"><span data-stu-id="8165f-285">Use of spatial sound</span></span>

<span data-ttu-id="8165f-286">In Windows Mixed Reality bietet die Audioengine die Audiowiedergabe-Komponente der gemischten Realität, indem 3D-Sounds mithilfe von Richtungs-, Entfernungs-und Umgebungs Simulationen simuliert werden.</span><span class="sxs-lookup"><span data-stu-id="8165f-286">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="8165f-287">Die Verwendung von räumlichem Sound in einer Anwendung ermöglicht Entwicklern das überzeugend Platzieren von Sounds in einem dreidimensionalen Raum (Kugel), der sich alle um den Benutzer dreht.</span><span class="sxs-lookup"><span data-stu-id="8165f-287">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="8165f-288">Diese Sounds erscheinen dann so, als wären Sie von echten physischen Objekten oder den Mixed Reality holograms in der Benutzerumgebung.</span><span class="sxs-lookup"><span data-stu-id="8165f-288">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="8165f-289">Räumlicher Sound ist ein leistungsfähiges Tool für das Eintauchen, die Barrierefreiheit und den UX-Entwurf in gemischten Reality-Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="8165f-289">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="8165f-290">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="8165f-290">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="8165f-291"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="8165f-291"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="8165f-292"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="8165f-292"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="8165f-293">✔️</span><span class="sxs-lookup"><span data-stu-id="8165f-293">✔️</span></span></td>
        <td><span data-ttu-id="8165f-294">✔️</span><span class="sxs-lookup"><span data-stu-id="8165f-294">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="8165f-295">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="8165f-295">Quality criteria</span></span>

|  <span data-ttu-id="8165f-296">Sehr hoch</span><span class="sxs-lookup"><span data-stu-id="8165f-296">Best</span></span>  |  <span data-ttu-id="8165f-297">Findet</span><span class="sxs-lookup"><span data-stu-id="8165f-297">Meets</span></span> |  <span data-ttu-id="8165f-298">Fehler</span><span class="sxs-lookup"><span data-stu-id="8165f-298">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="8165f-299">Sound ist logisch räumlich, und die UX verwendet den Sound entsprechend, um die Objekt Ermittlung und das Benutzer Feedback zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="8165f-299">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="8165f-300">Sound ist naturgemäß und relevant für Objekte und wird im gesamten Szenario normalisiert.</span><span class="sxs-lookup"><span data-stu-id="8165f-300">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="8165f-301">Räumliche Audiodaten werden in angemessener Weise verwendet, um Benutzer Feedback und Auffindbarkeit zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="8165f-301">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="8165f-302">Sound ist nicht erwartungsgemäß räumlich und/oder ungenügender Ton, um Benutzer innerhalb der UX zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="8165f-302">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="8165f-303">Das räumliche audiobild wurde im Entwurf des Szenarios nicht berücksichtigt oder verwendet.</span><span class="sxs-lookup"><span data-stu-id="8165f-303">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="8165f-304">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="8165f-304">How to measure</span></span>

* <span data-ttu-id="8165f-305">Im Allgemeinen sollten relevante Sounds aus Ziel-holograms (z. b. "Bark Sound" von Holographic Dog) ausgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="8165f-305">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="8165f-306">Sound Hinweise sollten in der gesamten Benutzeroberfläche verwendet werden, um dem Benutzer Feedback oder das Bewusstsein von Aktionen außerhalb des Holographic Frame zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="8165f-306">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="8165f-307">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="8165f-307">Recommendations</span></span>

* <span data-ttu-id="8165f-308">Verwenden Sie räumliche Audiodaten, um die Objekt Ermittlung und Benutzeroberflächen zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="8165f-308">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="8165f-309">Echte Sounds funktionieren besser als synthetisieren oder unnatürlicher Sound.</span><span class="sxs-lookup"><span data-stu-id="8165f-309">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="8165f-310">Die meisten Sounds sollten räumlich behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="8165f-310">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="8165f-311">Vermeiden Sie unsichtbare Emitter.</span><span class="sxs-lookup"><span data-stu-id="8165f-311">Avoid invisible emitters.</span></span>
* <span data-ttu-id="8165f-312">Vermeiden Sie die räumliche Maskierung.</span><span class="sxs-lookup"><span data-stu-id="8165f-312">Avoid spatial masking.</span></span>
* <span data-ttu-id="8165f-313">Normalisieren Sie alle Sounds.</span><span class="sxs-lookup"><span data-stu-id="8165f-313">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="8165f-314">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="8165f-314">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="8165f-315">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="8165f-315">Documentation</span></span>

* [<span data-ttu-id="8165f-316">Raumklang</span><span class="sxs-lookup"><span data-stu-id="8165f-316">Spatial sound</span></span>](../../design/spatial-sound.md)
* [<span data-ttu-id="8165f-317">Raumklangentwurf</span><span class="sxs-lookup"><span data-stu-id="8165f-317">Spatial sound design</span></span>](../../design/spatial-sound-design.md)
* [<span data-ttu-id="8165f-318">Raumklang in Unity</span><span class="sxs-lookup"><span data-stu-id="8165f-318">Spatial sound in Unity</span></span>](../unity/spatial-sound-in-unity.md)
* [<span data-ttu-id="8165f-319">Fallstudie, räumlicher Sound für holotour</span><span class="sxs-lookup"><span data-stu-id="8165f-319">Case study, Spatial sound for HoloTour</span></span>](../../design/case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="8165f-320">Fallstudie mit räumlichem Sound in roboraid</span><span class="sxs-lookup"><span data-stu-id="8165f-320">Case study, Using spatial sound in RoboRaid</span></span>](../../design/case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="8165f-321">Tools und Tutorials</span><span class="sxs-lookup"><span data-stu-id="8165f-321">Tools and tutorials</span></span>

* [<span data-ttu-id="8165f-322">Mrtoolkit, räumliche Audiodaten</span><span class="sxs-lookup"><span data-stu-id="8165f-322">MRToolkit, Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="8165f-323">Fokus auf Holographic Frame-Grenzen (FOV)</span><span class="sxs-lookup"><span data-stu-id="8165f-323">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="8165f-324">Gut gestaltete Benutzeroberflächen können den nützlichen Kontext der virtuellen Umgebung erstellen und verwalten, die sich um die Benutzer erstreckt.</span><span class="sxs-lookup"><span data-stu-id="8165f-324">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="8165f-325">Das Verringern der Auswirkungen der FOV-Grenzen umfasst einen durchdachten Entwurf der Inhalts Skala und des Kontexts, die Verwendung räumlicher Audiodaten, Leitfäden und die Position des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="8165f-325">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="8165f-326">Wenn dies der Fall ist, wird der Benutzer durch die FOV-Grenzen weniger beeinträchtigt, während er eine bequeme App-Erfahrung bietet.</span><span class="sxs-lookup"><span data-stu-id="8165f-326">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="8165f-327">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="8165f-327">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="8165f-328"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="8165f-328"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="8165f-329"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="8165f-329"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="8165f-330">✔️</span><span class="sxs-lookup"><span data-stu-id="8165f-330">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="8165f-331">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="8165f-331">Quality criteria</span></span>

|  <span data-ttu-id="8165f-332">Sehr hoch</span><span class="sxs-lookup"><span data-stu-id="8165f-332">Best</span></span>  |  <span data-ttu-id="8165f-333">Findet</span><span class="sxs-lookup"><span data-stu-id="8165f-333">Meets</span></span> |  <span data-ttu-id="8165f-334">Fehler</span><span class="sxs-lookup"><span data-stu-id="8165f-334">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="8165f-335">Der Benutzer verliert nie den Kontext, und die Anzeige ist bequem.</span><span class="sxs-lookup"><span data-stu-id="8165f-335">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="8165f-336">Für große Objekte wird Kontextunterstützung bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="8165f-336">Context assistance is provided for large objects.</span></span> <span data-ttu-id="8165f-337">Ermittelbarkeits-und Anzeige Anleitungen werden für Objekte außerhalb des Frames bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="8165f-337">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="8165f-338">Im Allgemeinen sind Bewegungs Entwurf und Skalierung der holograms für eine bequeme Anzeige geeignet.</span><span class="sxs-lookup"><span data-stu-id="8165f-338">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="8165f-339">Der Benutzer verliert den Kontext nie, aber in bestimmten Situationen ist möglicherweise eine zusätzliche Nacken Bewegung erforderlich.</span><span class="sxs-lookup"><span data-stu-id="8165f-339">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="8165f-340">In einer begrenzten Situation bewirkt die Skalierung, dass holograms entweder den vertikalen oder horizontalen Rahmen unterbrechen, was dazu führt, dass die Bewegung holograms durch einen Hals</span><span class="sxs-lookup"><span data-stu-id="8165f-340">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="8165f-341">Der Benutzer verliert wahrscheinlich den Kontext und/oder eine konsistente Hals Bewegung zum Anzeigen von holograms.</span><span class="sxs-lookup"><span data-stu-id="8165f-341">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="8165f-342">Keine Kontext Leit Fäden für große Holographic-Objekte, die das Verschieben von Objekten außerhalb des Frames ohne auffindbarkeits Leit Fäden vereinfachen, oder die Verwendung von hohen holograms erfordert eine reguläre Hals Bewegung zum anzeigen.</span><span class="sxs-lookup"><span data-stu-id="8165f-342">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="8165f-343">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="8165f-343">How to measure</span></span>

* <span data-ttu-id="8165f-344">Der Kontext für ein (großes) – Hologramm geht verloren oder wird nicht verstanden, weil er an den Begrenzungen abgeschnitten wurde.</span><span class="sxs-lookup"><span data-stu-id="8165f-344">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="8165f-345">Der Speicherort von holograms ist schwierig zu finden, da es sich nicht um die Aufmerksamkeit von Regisseuren oder Inhalten handelt, die sich schnell in den Holographic-Frame bewegen.</span><span class="sxs-lookup"><span data-stu-id="8165f-345">Location of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="8165f-346">Das Szenario erfordert reguläre und wiederkehrende aufruhenden aufruhenden Bewegung, um ein – Hologramm vollständig zu sehen</span><span class="sxs-lookup"><span data-stu-id="8165f-346">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="8165f-347">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="8165f-347">Recommendations</span></span>

* <span data-ttu-id="8165f-348">Starten Sie die Arbeit mit kleinen Objekten, die für den FOV geeignet sind, und wechseln Sie dann mit visuellen Cues in größere Versionen.</span><span class="sxs-lookup"><span data-stu-id="8165f-348">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="8165f-349">Verwenden Sie die Directors für räumliche Audiodaten und Aufmerksamkeit, um dem Benutzer zu helfen, Inhalte außerhalb des FOV zu finden.</span><span class="sxs-lookup"><span data-stu-id="8165f-349">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="8165f-350">Vermeiden Sie so weit wie möglich Hologramme, die den FOV vertikal abschneiden.</span><span class="sxs-lookup"><span data-stu-id="8165f-350">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="8165f-351">Stellen Sie dem Benutzer einen in-App-Leitfaden für den optimalen Anzeige Speicherort zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="8165f-351">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="8165f-352">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="8165f-352">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="8165f-353">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="8165f-353">Documentation</span></span>

* [<span data-ttu-id="8165f-354">Holografischer Rahmen</span><span class="sxs-lookup"><span data-stu-id="8165f-354">Holographic frame</span></span>](../../design/holographic-frame.md)
* [<span data-ttu-id="8165f-355">Fallstudie, Entwicklung von holostudio-UI und Interaktions Entwurf</span><span class="sxs-lookup"><span data-stu-id="8165f-355">Case Study, HoloStudio UI and interaction design learnings</span></span>](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="8165f-356">Skalieren von Objekten und Umgebungen</span><span class="sxs-lookup"><span data-stu-id="8165f-356">Scale of objects and environments</span></span>](../../design/scale.md)
* [<span data-ttu-id="8165f-357">Cursor, visuelle Hinweise</span><span class="sxs-lookup"><span data-stu-id="8165f-357">Cursors, Visual cues</span></span>](../../design/cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="8165f-358">Externe Verweise</span><span class="sxs-lookup"><span data-stu-id="8165f-358">External references</span></span>

* [<span data-ttu-id="8165f-359">Viel ADO zum FOV</span><span class="sxs-lookup"><span data-stu-id="8165f-359">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="8165f-360">Inhalt reagiert auf Benutzer Position</span><span class="sxs-lookup"><span data-stu-id="8165f-360">Content reacts to user position</span></span>

<span data-ttu-id="8165f-361">Holograms sollten auf ungefähr die gleiche Weise wie "echte" Objekte auf die Benutzer Position reagieren.</span><span class="sxs-lookup"><span data-stu-id="8165f-361">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="8165f-362">Ein wichtiger Entwurfs Aspekt sind Benutzeroberflächen Elemente, die nicht unbedingt annehmen können, dass die Position eines Benutzers stationär ist und sich an die Bewegung des Benutzers anpasst.</span><span class="sxs-lookup"><span data-stu-id="8165f-362">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="8165f-363">Das Entwerfen einer APP, die sich ordnungsgemäß an die Benutzer Position anpasst, führt zu einer besseren Benutzerfreundlichkeit und erleichtert die Verwendung.</span><span class="sxs-lookup"><span data-stu-id="8165f-363">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="8165f-364">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="8165f-364">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="8165f-365"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="8165f-365"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="8165f-366"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="8165f-366"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="8165f-367">✔️</span><span class="sxs-lookup"><span data-stu-id="8165f-367">✔️</span></span></td>
        <td><span data-ttu-id="8165f-368">✔️</span><span class="sxs-lookup"><span data-stu-id="8165f-368">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="8165f-369">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="8165f-369">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="8165f-370">Sehr hoch</span><span class="sxs-lookup"><span data-stu-id="8165f-370">Best</span></span> </td><td> <span data-ttu-id="8165f-371">Der Inhalt und die Benutzeroberfläche werden an Benutzer Positionen angepasst, damit Benutzer im Bereich der erwarteten Benutzer Bewegung natürlich mit Inhalten interagieren können.</span><span class="sxs-lookup"><span data-stu-id="8165f-371">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8165f-372">Findet</span><span class="sxs-lookup"><span data-stu-id="8165f-372">Meets</span></span> </td><td> <span data-ttu-id="8165f-373">Die Benutzeroberfläche passt sich an die Benutzer Position an, kann jedoch die Ansicht von Schlüssel Inhalten behindern, die den Benutzer zum Anpassen Ihrer Position benötigen.</span><span class="sxs-lookup"><span data-stu-id="8165f-373">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="8165f-374">Fehler</span><span class="sxs-lookup"><span data-stu-id="8165f-374">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="8165f-375">Benutzeroberflächen Elemente gehen verloren oder sind während der Bewegung gesperrt, sodass der Benutzer nicht auf natürliche Weise zu den Steuerelementen zurückkehrt.</span><span class="sxs-lookup"><span data-stu-id="8165f-375">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="8165f-376">Elemente der Benutzeroberfläche beschränken die Ansicht von primärem Inhalt.</span><span class="sxs-lookup"><span data-stu-id="8165f-376">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="8165f-377">Die UI-Verschiebung ist nicht für die Anzeige von Distance und Impulsen vor allem mit <a href="../../design/billboarding-and-tag-along.md">tagbasierten</a> Benutzeroberflächen Elementen optimiert.</span><span class="sxs-lookup"><span data-stu-id="8165f-377">UI movement is not optimized for viewing distance and momentum particularly with <a href="../../design/billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="8165f-378">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="8165f-378">How to measure</span></span>

* <span data-ttu-id="8165f-379">Alle Messungen sollten innerhalb eines angemessenen Umfangs des Szenarios durchgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="8165f-379">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="8165f-380">Während die Benutzer Bewegung variieren kann, versuchen Sie nicht, die APP mit extremer Benutzer Bewegung zu täuschen.</span><span class="sxs-lookup"><span data-stu-id="8165f-380">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="8165f-381">Für Elemente der Benutzeroberfläche sollten relevante Steuerelemente unabhängig von der Benutzer Bewegung verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="8165f-381">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="8165f-382">Wenn der Benutzer z. b. eine 3D-Karte mit Zoom anzeigen und durchläuft, sollte das Zoom Steuerelement dem Benutzer unabhängig von der Position sofort verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="8165f-382">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="8165f-383">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="8165f-383">Recommendations</span></span>

* <span data-ttu-id="8165f-384">Der Benutzer ist die Kamera und steuert die Bewegung.</span><span class="sxs-lookup"><span data-stu-id="8165f-384">The user is the camera and they control the movement.</span></span> <span data-ttu-id="8165f-385">Das können Sie steuern.</span><span class="sxs-lookup"><span data-stu-id="8165f-385">Let them drive.</span></span>
* <span data-ttu-id="8165f-386">Ziehen Sie die Abrechnung für Text-und menuingsysteme in Erwägung, die andernfalls in der Welt gesperrt oder verdeckt werden, wenn sich ein Benutzer bewegen würde.</span><span class="sxs-lookup"><span data-stu-id="8165f-386">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="8165f-387">Verwenden Sie tagzusammen für Inhalte, die dem Benutzer folgen müssen, während der Benutzer weiterhin sehen kann, was vor ihm steht.</span><span class="sxs-lookup"><span data-stu-id="8165f-387">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="8165f-388">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="8165f-388">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="8165f-389">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="8165f-389">Documentation</span></span>

* [<span data-ttu-id="8165f-390">Interaktionsgestaltung</span><span class="sxs-lookup"><span data-stu-id="8165f-390">Interaction design</span></span>](../../discover/hologram.md)
* [<span data-ttu-id="8165f-391">Farbe, Licht und Material</span><span class="sxs-lookup"><span data-stu-id="8165f-391">Color, light, and material</span></span>](../../color,-light-and-materials.md)
* [<span data-ttu-id="8165f-392">Billboarding und Tag-along</span><span class="sxs-lookup"><span data-stu-id="8165f-392">Billboarding and tag-along</span></span>](../../design/billboarding-and-tag-along.md)
* [<span data-ttu-id="8165f-393">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="8165f-393">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)
* [<span data-ttu-id="8165f-394">Eigenbewegung und Ortsveränderung des Benutzers</span><span class="sxs-lookup"><span data-stu-id="8165f-394">Self-motion and user locomotion</span></span>](../../design/comfort.md#self-motion-and-user-locomotion)

## <a name="input-interaction-clarity"></a><span data-ttu-id="8165f-395">Klarheit der Eingabe Interaktion</span><span class="sxs-lookup"><span data-stu-id="8165f-395">Input interaction clarity</span></span>

<span data-ttu-id="8165f-396">Die Übersichtlichkeit der Eingabe Interaktion ist wichtig für die Benutzerfreundlichkeit einer APP und umfasst Eingabe Konsistenz, genehmigende Zulässigkeit, Auffindbarkeit von Interaktions Methoden.</span><span class="sxs-lookup"><span data-stu-id="8165f-396">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="8165f-397">Der Benutzer sollte in der Lage sein, plattformweite allgemeine Interaktionen ohne Relearning zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="8165f-397">User should be able to use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="8165f-398">Wenn die APP benutzerdefinierte Eingaben hat, sollte Sie eindeutig kommuniziert und demonstriert werden.</span><span class="sxs-lookup"><span data-stu-id="8165f-398">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="8165f-399">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="8165f-399">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="8165f-400"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="8165f-400"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="8165f-401"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="8165f-401"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="8165f-402">✔️</span><span class="sxs-lookup"><span data-stu-id="8165f-402">✔️</span></span></td>
        <td><span data-ttu-id="8165f-403">✔️</span><span class="sxs-lookup"><span data-stu-id="8165f-403">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="8165f-404">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="8165f-404">Quality criteria</span></span>

|  <span data-ttu-id="8165f-405">Sehr hoch</span><span class="sxs-lookup"><span data-stu-id="8165f-405">Best</span></span>  |  <span data-ttu-id="8165f-406">Findet</span><span class="sxs-lookup"><span data-stu-id="8165f-406">Meets</span></span> |  <span data-ttu-id="8165f-407">Fehler</span><span class="sxs-lookup"><span data-stu-id="8165f-407">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="8165f-408">Eingabe Interaktions Methoden sind mit der von Windows Mixed Reality bereitgestellten [Anleitung](../../design/interaction-fundamentals.md)konsistent.</span><span class="sxs-lookup"><span data-stu-id="8165f-408">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](../../design/interaction-fundamentals.md).</span></span> <span data-ttu-id="8165f-409">Jede benutzerdefinierte Eingabe sollte nicht mit Standard Eingaben redundant sein (sondern eher die Standard Interaktion verwenden), und Sie muss für den Benutzer eindeutig kommuniziert und demonstriert werden.</span><span class="sxs-lookup"><span data-stu-id="8165f-409">Any custom input should not be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="8165f-410">Ähnlich wie die beste, aber benutzerdefinierte Eingaben sind bei Standardeingabe Methoden redundant.</span><span class="sxs-lookup"><span data-stu-id="8165f-410">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="8165f-411">Der Benutzer kann das Ziel und den Fortschritt auch über die App-Benutzer Leistung erreichen.</span><span class="sxs-lookup"><span data-stu-id="8165f-411">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="8165f-412">Das Verständnis der Eingabemethode oder der Schaltflächen Zuordnung ist schwierig.</span><span class="sxs-lookup"><span data-stu-id="8165f-412">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="8165f-413">Die Eingabe ist stark angepasst, bietet keine Unterstützung für Standard Eingaben, keine Anweisungen, oder es werden wahrscheinlich Ermüdungs-und komfortprobleme verursacht.</span><span class="sxs-lookup"><span data-stu-id="8165f-413">Input is heavily customized, does not support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="8165f-414">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="8165f-414">How to measure</span></span>

* <span data-ttu-id="8165f-415">Die APP verwendet konsistente [Standardeingabe Methoden.](../../design/interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="8165f-415">The app uses consistent [standard input methods.](../../design/interaction-fundamentals.md)</span></span>
* <span data-ttu-id="8165f-416">Wenn die APP über benutzerdefinierte Eingaben verfügt, wird Sie eindeutig übermittelt:</span><span class="sxs-lookup"><span data-stu-id="8165f-416">If the app has custom input, it is clearly communicated through:</span></span>
* <span data-ttu-id="8165f-417">Erstmaligen Testlauf</span><span class="sxs-lookup"><span data-stu-id="8165f-417">First-run experience</span></span>
* <span data-ttu-id="8165f-418">Einführungs Bildschirme</span><span class="sxs-lookup"><span data-stu-id="8165f-418">Introductory screens</span></span>
* <span data-ttu-id="8165f-419">QuickInfos</span><span class="sxs-lookup"><span data-stu-id="8165f-419">Tooltips</span></span>
* <span data-ttu-id="8165f-420">Hand Coach</span><span class="sxs-lookup"><span data-stu-id="8165f-420">Hand coach</span></span>
* <span data-ttu-id="8165f-421">Hilfe Abschnitt</span><span class="sxs-lookup"><span data-stu-id="8165f-421">Help section</span></span>
* <span data-ttu-id="8165f-422">Voice-over</span><span class="sxs-lookup"><span data-stu-id="8165f-422">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="8165f-423">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="8165f-423">Recommendations</span></span>

* <span data-ttu-id="8165f-424">Verwenden Sie nach Möglichkeit immer Standardeingabe Methoden.</span><span class="sxs-lookup"><span data-stu-id="8165f-424">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="8165f-425">Stellen Sie Demonstrationen, Tutorials und Quick Infos für nicht standardmäßige Eingabemethoden bereit.</span><span class="sxs-lookup"><span data-stu-id="8165f-425">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="8165f-426">Verwenden Sie in der gesamten App ein konsistentes Interaktionsmodell.</span><span class="sxs-lookup"><span data-stu-id="8165f-426">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="8165f-427">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="8165f-427">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="8165f-428">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="8165f-428">Documentation</span></span>

* [<span data-ttu-id="8165f-429">Instinktive Interaktionen</span><span class="sxs-lookup"><span data-stu-id="8165f-429">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)
* [<span data-ttu-id="8165f-430">Interactable-Objekte</span><span class="sxs-lookup"><span data-stu-id="8165f-430">Interactable objects</span></span>](../../design/interactable-object.md)
* [<span data-ttu-id="8165f-431">Anvisieren mit dem Kopf und Verweilen</span><span class="sxs-lookup"><span data-stu-id="8165f-431">Head-gaze and dwell</span></span>](../../design/gaze-and-dwell.md)
* [<span data-ttu-id="8165f-432">Cursor</span><span class="sxs-lookup"><span data-stu-id="8165f-432">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="8165f-433">Komfort und Blick</span><span class="sxs-lookup"><span data-stu-id="8165f-433">Comfort and gaze</span></span>](../../design/comfort.md#gaze-direction)
* [<span data-ttu-id="8165f-434">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="8165f-434">Voice input</span></span>](../../design/voice-input.md)
* [<span data-ttu-id="8165f-435">Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="8165f-435">Motion controllers</span></span>](../../design/motion-controllers.md)
* [<span data-ttu-id="8165f-436">Leitfaden für Eingabeportierung für Unity</span><span class="sxs-lookup"><span data-stu-id="8165f-436">Input porting guide for Unity</span></span>](../porting-apps/input-porting-guide-for-unity.md)
* [<span data-ttu-id="8165f-437">Tastatureingabe in Unity</span><span class="sxs-lookup"><span data-stu-id="8165f-437">Keyboard input in Unity</span></span>](../unity/keyboard-input-in-unity.md)
* [<span data-ttu-id="8165f-438">Anvisieren in Unity</span><span class="sxs-lookup"><span data-stu-id="8165f-438">Gaze in Unity</span></span>](../unity/gaze-in-unity.md)
* [<span data-ttu-id="8165f-439">Gesten und Motion-Controller in Unity</span><span class="sxs-lookup"><span data-stu-id="8165f-439">Gestures and motion controllers in Unity</span></span>](../unity/gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="8165f-440">Spracheingabe in Unity</span><span class="sxs-lookup"><span data-stu-id="8165f-440">Voice input in Unity</span></span>](../unity/voice-input-in-unity.md)
* [<span data-ttu-id="8165f-441">Tastatur-, Maus- und Controllereingaben in DirectX</span><span class="sxs-lookup"><span data-stu-id="8165f-441">Keyboard, mouse, and controller input in DirectX</span></span>](../../keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="8165f-442">Anvisieren mit dem Kopf und mit den Augen in DirectX</span><span class="sxs-lookup"><span data-stu-id="8165f-442">Head and eye gaze in DirectX</span></span>](../native/gaze-in-directx.md)
* [<span data-ttu-id="8165f-443">Hände und Motion-Controller in DirectX</span><span class="sxs-lookup"><span data-stu-id="8165f-443">Hands and motion controllers in DirectX</span></span>](../native/hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="8165f-444">Spracheingabe in DirectX</span><span class="sxs-lookup"><span data-stu-id="8165f-444">Voice input in DirectX</span></span>](../native/voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="8165f-445">Tools und Tutorials</span><span class="sxs-lookup"><span data-stu-id="8165f-445">Tools and tutorials</span></span>

* [<span data-ttu-id="8165f-446">Fallstudie: die Verfolgung von mehr persönlichen Computing</span><span class="sxs-lookup"><span data-stu-id="8165f-446">Case study: The pursuit of more personal computing</span></span>](../../out-of-scope/case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="8165f-447">Umwandlungs Studie: Entwicklung von holostudio-UI-und Interaktions Entwürfen</span><span class="sxs-lookup"><span data-stu-id="8165f-447">Cast study: HoloStudio UI and interaction design learnings</span></span>](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="8165f-448">Beispiel-App: periodische Tabelle der Elemente</span><span class="sxs-lookup"><span data-stu-id="8165f-448">Sample app: Periodic table of the elements</span></span>](../unity/periodic-table-of-the-elements.md)
* [<span data-ttu-id="8165f-449">Beispiel-App: Mond Modul</span><span class="sxs-lookup"><span data-stu-id="8165f-449">Sample app: Lunar module</span></span>](../unity/lunar-module.md)

## <a name="interactable-objects"></a><span data-ttu-id="8165f-450">Interactable-Objekte</span><span class="sxs-lookup"><span data-stu-id="8165f-450">Interactable objects</span></span>

<span data-ttu-id="8165f-451">Eine Schaltfläche ist lange eine Metapher, die zum Auslösen eines Ereignisses in der 2D-abstrakten Welt verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="8165f-451">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="8165f-452">In der dreidimensionalen Mixed Reality-Welt müssen wir nicht mehr auf diese Abstraktions Welt beschränkt werden.</span><span class="sxs-lookup"><span data-stu-id="8165f-452">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="8165f-453">Dabei kann es sich um ein Objekt handeln, das ein Objekt ist, das ein Ereignis auslöst.</span><span class="sxs-lookup"><span data-stu-id="8165f-453">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="8165f-454">Ein Objekt, das sich in der Tabelle befindet, kann als beliebiger von einem Kaffeebecher in der Tabelle dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="8165f-454">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="8165f-455">Unabhängig vom Formular sollte der Benutzer durch visuelle und Audiohinweise eindeutig erkennbar sein.</span><span class="sxs-lookup"><span data-stu-id="8165f-455">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="8165f-456">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="8165f-456">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="8165f-457"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="8165f-457"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="8165f-458"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="8165f-458"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="8165f-459">✔️</span><span class="sxs-lookup"><span data-stu-id="8165f-459">✔️</span></span></td>
        <td><span data-ttu-id="8165f-460">✔️</span><span class="sxs-lookup"><span data-stu-id="8165f-460">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="8165f-461">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="8165f-461">Quality criteria</span></span>

|  <span data-ttu-id="8165f-462">Sehr hoch</span><span class="sxs-lookup"><span data-stu-id="8165f-462">Best</span></span>  |  <span data-ttu-id="8165f-463">Findet</span><span class="sxs-lookup"><span data-stu-id="8165f-463">Meets</span></span> |  <span data-ttu-id="8165f-464">Fehler</span><span class="sxs-lookup"><span data-stu-id="8165f-464">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="8165f-465">Unabhängig von der Form sind Interaktionen-Objekte durch visuelle und Audiohinweise in drei Zuständen erkennbar: im Leerlauf, gezielt und ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="8165f-465">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="8165f-466">"Wie Sie sehen, ist es klar und in der gesamten gesamten Darstellung verwendet.</span><span class="sxs-lookup"><span data-stu-id="8165f-466">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="8165f-467">Objekte werden skaliert und verteilt, um eine fehlerfreie Zielversion zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="8165f-467">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="8165f-468">Der Benutzer kann das Objekt als Interaktionen durch Audiomaterial oder visuelles Feedback erkennen und das Objekt auf das Objekt ausrichten und aktivieren.</span><span class="sxs-lookup"><span data-stu-id="8165f-468">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="8165f-469">Wenn keine visuellen oder Audiohinweise angezeigt werden, kann der Benutzer ein Objekt mit Interaktionen nicht erkennen.</span><span class="sxs-lookup"><span data-stu-id="8165f-469">Given no visual or audio cues, user cannot recognize an interactable object.</span></span> <span data-ttu-id="8165f-470">Interaktionen sind aufgrund der Objekt Skala oder der Entfernung zwischen Objekten fehleranfällig.</span><span class="sxs-lookup"><span data-stu-id="8165f-470">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="8165f-471">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="8165f-471">How to measure</span></span>

* <span data-ttu-id="8165f-472">Interactable-Objekte sind als "interactable" erkennbar. einschließen von Schaltflächen, Menüs und App-spezifischem Inhalt.</span><span class="sxs-lookup"><span data-stu-id="8165f-472">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app specific content.</span></span> <span data-ttu-id="8165f-473">Als Faustregel gilt, dass ein visueller und audiohinweis vorhanden sein sollte, wenn Sie auf Objekte mit Interaktionen abzielen.</span><span class="sxs-lookup"><span data-stu-id="8165f-473">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="8165f-474">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="8165f-474">Recommendations</span></span>

* <span data-ttu-id="8165f-475">Verwenden Sie visuelles und Audiofeedback für Interaktionen.</span><span class="sxs-lookup"><span data-stu-id="8165f-475">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="8165f-476">Visuelles Feedback sollte für jeden Eingabe Status unterschieden werden (im Leerlauf, gezielt, ausgewählt).</span><span class="sxs-lookup"><span data-stu-id="8165f-476">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="8165f-477">Interactable-Objekte sollten skaliert und für fehlerfreie Zielgruppen vorgesehen werden.</span><span class="sxs-lookup"><span data-stu-id="8165f-477">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="8165f-478">Gruppierte Interaktionen-Objekte (z. b. eine Menüleiste oder Liste) sollten über den richtigen Abstand zum Ziel verfügen.</span><span class="sxs-lookup"><span data-stu-id="8165f-478">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="8165f-479">Schaltflächen und Menüs, die den Voice-Befehl unterstützen, sollten Text Bezeichnungen für das Befehls Schlüsselwort bereitstellen ("siehe IT, sagen Sie")</span><span class="sxs-lookup"><span data-stu-id="8165f-479">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="8165f-480">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="8165f-480">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="8165f-481">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="8165f-481">Documentation</span></span>

* [<span data-ttu-id="8165f-482">Interaktionsfähiges Objekt</span><span class="sxs-lookup"><span data-stu-id="8165f-482">Interactable object</span></span>](../../design/interactable-object.md)
* [<span data-ttu-id="8165f-483">Text in Unity</span><span class="sxs-lookup"><span data-stu-id="8165f-483">Text in Unity</span></span>](../unity/text-in-unity.md)
* [<span data-ttu-id="8165f-484">Begrenzungsrahmen und App-Leiste</span><span class="sxs-lookup"><span data-stu-id="8165f-484">Bounding box and App bar</span></span>](../../design/app-bar-and-bounding-box.md)
* [<span data-ttu-id="8165f-485">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="8165f-485">Voice input</span></span>](../../design/voice-input.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="8165f-486">Tools und Tutorials</span><span class="sxs-lookup"><span data-stu-id="8165f-486">Tools and tutorials</span></span>

* [<span data-ttu-id="8165f-487">Mixed Reality Toolkit-UX</span><span class="sxs-lookup"><span data-stu-id="8165f-487">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="8165f-488">Raum Überprüfung</span><span class="sxs-lookup"><span data-stu-id="8165f-488">Room scanning</span></span>

<span data-ttu-id="8165f-489">Apps, die räumliche Daten für die Zuordnung benötigen, benötigen das Gerät, um diese Daten automatisch über einen Zeitraum und Sitzungs übergreifend zu erfassen, da der Benutzer seine Umgebung mit dem aktiven Gerät untersucht.</span><span class="sxs-lookup"><span data-stu-id="8165f-489">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="8165f-490">Die Vollständigkeit und Qualität dieser Daten hängt von einer Reihe von Faktoren ab, z. b. vom Umfang der durchgeführten Untersuchung, von der seit der Durchsuchung übergebenen Zeit und davon, ob Objekte wie z. b. Möbel und Türen verschoben wurden, seit das Gerät den Bereich überprüft hat.</span><span class="sxs-lookup"><span data-stu-id="8165f-490">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="8165f-491">Viele apps analysieren die räumlichen Zuordnungs Daten zu Beginn der Benutzer Darstellung, um zu beurteilen, ob der Benutzer zusätzliche Schritte ausführen muss, um die Vollständigkeit und Qualität der räumlichen Karte zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="8165f-491">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="8165f-492">Wenn der Benutzer die Umgebung scannen muss, sollten Sie während der Überprüfung eine klare Anleitung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="8165f-492">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="8165f-493">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="8165f-493">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="8165f-494"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="8165f-494"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="8165f-495"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="8165f-495"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="8165f-496">✔️</span><span class="sxs-lookup"><span data-stu-id="8165f-496">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="8165f-497">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="8165f-497">Quality criteria</span></span>

|  <span data-ttu-id="8165f-498">Sehr hoch</span><span class="sxs-lookup"><span data-stu-id="8165f-498">Best</span></span>  |  <span data-ttu-id="8165f-499">Findet</span><span class="sxs-lookup"><span data-stu-id="8165f-499">Meets</span></span> |  <span data-ttu-id="8165f-500">Fehler</span><span class="sxs-lookup"><span data-stu-id="8165f-500">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="8165f-501">Die Visualisierung des räumlichen Netzes weist auf die Überprüfung von Benutzern hin.</span><span class="sxs-lookup"><span data-stu-id="8165f-501">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="8165f-502">Der Benutzer weiß eindeutig, was zu tun ist und wann die Überprüfung gestartet und beendet wird.</span><span class="sxs-lookup"><span data-stu-id="8165f-502">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="8165f-503">Die Visualisierung des räumlichen Netzes wird bereitgestellt, aber der Benutzer weiß möglicherweise nicht, was zu tun ist, und es werden keine Fortschrittsinformationen bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="8165f-503">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="8165f-504">Keine Visualisierung von Mesh.</span><span class="sxs-lookup"><span data-stu-id="8165f-504">No visualization of mesh.</span></span> <span data-ttu-id="8165f-505">Für den Benutzer werden keine Leitfäden bezüglich des abzurufenden oder zum Starten/Beenden der Überprüfung bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="8165f-505">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="8165f-506">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="8165f-506">How to measure</span></span>

* <span data-ttu-id="8165f-507">Während eines erforderlichen Raum Scans werden visuelle und audioanleitungen bereitgestellt, die angeben, wo gesucht werden soll und wann das Scannen gestartet und beendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="8165f-507">During a required room scan, visual and audio guidance is provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="8165f-508">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="8165f-508">Recommendations</span></span>

* <span data-ttu-id="8165f-509">Geben Sie an, wie viel des gesamten Volumes in der Benutzerumgebung in der Umgebung enthalten sein muss.</span><span class="sxs-lookup"><span data-stu-id="8165f-509">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="8165f-510">Kommunizieren, wenn die Überprüfung gestartet und beendet wird, z. b. eine Statusanzeige.</span><span class="sxs-lookup"><span data-stu-id="8165f-510">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="8165f-511">Verwenden Sie während des Scanvorgangs eine Visualisierung des Netzes.</span><span class="sxs-lookup"><span data-stu-id="8165f-511">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="8165f-512">Stellen Sie visuelle und Audiohinweise bereit, um den Benutzer zu unterstützen, um den Raum zu sehen und zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="8165f-512">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="8165f-513">Informieren Sie den Benutzer, wohin Sie die Daten verbessern möchten.</span><span class="sxs-lookup"><span data-stu-id="8165f-513">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="8165f-514">In vielen Fällen kann es am besten sein, den Benutzern mitzuteilen, was Sie tun müssen (z. b. die Obergrenze, das Aussehen hinter den Möbeln), um die erforderliche Scanqualität zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="8165f-514">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="8165f-515">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="8165f-515">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="8165f-516">Dokumentation</span><span class="sxs-lookup"><span data-stu-id="8165f-516">Documentation</span></span>

* [<span data-ttu-id="8165f-517">Raumabtastvisualisierung</span><span class="sxs-lookup"><span data-stu-id="8165f-517">Room scan visualization</span></span>](../../design/room-scan-visualization.md)
* [<span data-ttu-id="8165f-518">Fallstudie: Erweitern der Funktionen für räumliche Zuordnung von hololens</span><span class="sxs-lookup"><span data-stu-id="8165f-518">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="8165f-519">Fallstudie: räumliches Sound Design für holotour</span><span class="sxs-lookup"><span data-stu-id="8165f-519">Case study: Spatial sound design for HoloTour</span></span>](../../design/case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="8165f-520">Fallstudie: Erstellen eines immersiven Erlebnisses in Fragmenten</span><span class="sxs-lookup"><span data-stu-id="8165f-520">Case study: Creating an immersive experience in Fragments</span></span>](../../out-of-scope/case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="8165f-521">Tools und Tutorials</span><span class="sxs-lookup"><span data-stu-id="8165f-521">Tools and tutorials</span></span>

* [<span data-ttu-id="8165f-522">Mixed Reality Toolkit-UX</span><span class="sxs-lookup"><span data-stu-id="8165f-522">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="8165f-523">Direktionale Indikatoren</span><span class="sxs-lookup"><span data-stu-id="8165f-523">Directional indicators</span></span>

<span data-ttu-id="8165f-524">In einer Mixed Reality-App kann es sein, dass sich Inhalte außerhalb des Felds befinden oder durch reale Objekte verdeckt werden.</span><span class="sxs-lookup"><span data-stu-id="8165f-524">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="8165f-525">Eine gut entworfene App vereinfacht das Auffinden nicht sichtbarer Inhalte durch den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="8165f-525">A well designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="8165f-526">Direktionale Indikatoren warnen einen Benutzer für wichtige Inhalte und bieten Anleitungen für den Inhalt in Bezug auf die Position des Benutzers an.</span><span class="sxs-lookup"><span data-stu-id="8165f-526">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="8165f-527">Anleitungen für nicht sichtbare Inhalte können als audioemitter, direktionale Pfeile oder direkte visuelle Hinweise genutzt werden.</span><span class="sxs-lookup"><span data-stu-id="8165f-527">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="8165f-528">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="8165f-528">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="8165f-529"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="8165f-529"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="8165f-530"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="8165f-530"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="8165f-531">✔️</span><span class="sxs-lookup"><span data-stu-id="8165f-531">✔️</span></span></td>
        <td><span data-ttu-id="8165f-532">✔️</span><span class="sxs-lookup"><span data-stu-id="8165f-532">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="8165f-533">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="8165f-533">Quality criteria</span></span>

|  <span data-ttu-id="8165f-534">Sehr hoch</span><span class="sxs-lookup"><span data-stu-id="8165f-534">Best</span></span>  |  <span data-ttu-id="8165f-535">Findet</span><span class="sxs-lookup"><span data-stu-id="8165f-535">Meets</span></span> |  <span data-ttu-id="8165f-536">Fehler</span><span class="sxs-lookup"><span data-stu-id="8165f-536">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="8165f-537">Visuelle und Audiohinweise leiten den Benutzer direkt an relevante Inhalte außerhalb des Felds der Ansicht.</span><span class="sxs-lookup"><span data-stu-id="8165f-537">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="8165f-538">Ein Pfeil oder ein Indikator, der den Benutzer in der allgemeinen Richtung des Inhalts zeigt.</span><span class="sxs-lookup"><span data-stu-id="8165f-538">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="8165f-539">Relevante Inhalte sind nicht in der Ansicht enthalten, und dem Benutzer wird ein schlechter oder kein Orts Leit Faden bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="8165f-539">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="8165f-540">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="8165f-540">How to measure</span></span>

* <span data-ttu-id="8165f-541">Relevante Inhalte außerhalb des Benutzer Felds können durch visuelle und/oder Audiohinweise erkannt werden.</span><span class="sxs-lookup"><span data-stu-id="8165f-541">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="8165f-542">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="8165f-542">Recommendations</span></span>

* <span data-ttu-id="8165f-543">Wenn relevante Inhalte außerhalb des Benutzer Felds liegen, verwenden Sie richtungsindikatoren und Audiohinweise, um den Benutzer zum Inhalt zu leiten.</span><span class="sxs-lookup"><span data-stu-id="8165f-543">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="8165f-544">In vielen Fällen wird ein direkter visueller Leitfaden als direktionale Pfeile bevorzugt.</span><span class="sxs-lookup"><span data-stu-id="8165f-544">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="8165f-545">Direktionale Indikatoren sollten nicht in den Cursor integriert werden.</span><span class="sxs-lookup"><span data-stu-id="8165f-545">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="8165f-546">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="8165f-546">Resources</span></span>

* [<span data-ttu-id="8165f-547">Holografischer Rahmen</span><span class="sxs-lookup"><span data-stu-id="8165f-547">Holographic frame</span></span>](../../design/holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="8165f-548">Laden von Daten</span><span class="sxs-lookup"><span data-stu-id="8165f-548">Data loading</span></span>

<span data-ttu-id="8165f-549">Ein Statussteuerelement gibt dem Benutzer eine Rückmeldung, dass ein Vorgang mit langer Laufzeit ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="8165f-549">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="8165f-550">Dies kann bedeuten, dass der Benutzer nicht mit der APP interagieren kann, wenn die Statusanzeige sichtbar ist, und auch angeben kann, wie lange die Wartezeit dauern kann.</span><span class="sxs-lookup"><span data-stu-id="8165f-550">It can mean that the user cannot interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="8165f-551">Geräte Auswirkung</span><span class="sxs-lookup"><span data-stu-id="8165f-551">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="8165f-552"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="8165f-552"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="8165f-553"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="8165f-553"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="8165f-554">✔️</span><span class="sxs-lookup"><span data-stu-id="8165f-554">✔️</span></span></td>
        <td><span data-ttu-id="8165f-555">✔️</span><span class="sxs-lookup"><span data-stu-id="8165f-555">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="8165f-556">Qualitätskriterien</span><span class="sxs-lookup"><span data-stu-id="8165f-556">Quality criteria</span></span>

|  <span data-ttu-id="8165f-557">Sehr hoch</span><span class="sxs-lookup"><span data-stu-id="8165f-557">Best</span></span>  |  <span data-ttu-id="8165f-558">Findet</span><span class="sxs-lookup"><span data-stu-id="8165f-558">Meets</span></span> |  <span data-ttu-id="8165f-559">Fehler</span><span class="sxs-lookup"><span data-stu-id="8165f-559">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="8165f-560">Animierter visueller Indikator in Form einer Statusanzeige oder eines Rings, der den Fortschritt beim Laden oder Verarbeiten von Daten anzeigt.</span><span class="sxs-lookup"><span data-stu-id="8165f-560">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="8165f-561">Der visuelle Indikator gibt eine Anleitung dazu, wie lange der Warte Vorgang sein könnte.</span><span class="sxs-lookup"><span data-stu-id="8165f-561">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="8165f-562">Der Benutzer wird darüber informiert, dass das Laden von Daten ausgeführt wird. es gibt jedoch keinen Hinweis darauf, wie lange der Warte Vorgang sein könnte.</span><span class="sxs-lookup"><span data-stu-id="8165f-562">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="8165f-563">Das Laden von Daten oder das Verarbeiten von Indikatoren für den Task dauert länger als 5 Sekunden.</span><span class="sxs-lookup"><span data-stu-id="8165f-563">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="8165f-564">So messen Sie</span><span class="sxs-lookup"><span data-stu-id="8165f-564">How to measure</span></span>

* <span data-ttu-id="8165f-565">Vergewissern Sie sich beim Laden von Daten, dass es für mehr als 5 Sekunden keinen leeren Zustand gibt.</span><span class="sxs-lookup"><span data-stu-id="8165f-565">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="8165f-566">Empfehlungen</span><span class="sxs-lookup"><span data-stu-id="8165f-566">Recommendations</span></span>

* <span data-ttu-id="8165f-567">Stellen Sie eine Animation zum Laden von Daten bereit, die den Fortschritt in jeder Situation anzeigt, in der der Benutzer diese APP möglicherweise als angehalten oder abstürzt</span><span class="sxs-lookup"><span data-stu-id="8165f-567">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="8165f-568">Eine vernünftige Faustregel ist jede "Lade Aktivität", die mehr als 5 Sekunden in Anspruch nehmen kann.</span><span class="sxs-lookup"><span data-stu-id="8165f-568">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="8165f-569">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="8165f-569">Resources</span></span>

* [<span data-ttu-id="8165f-570">Anzeigen des Fortschritts</span><span class="sxs-lookup"><span data-stu-id="8165f-570">Displaying progress</span></span>](../../design/progress.md)
