---
title: Kriterien für die App-Qualität
description: In diesem Dokument werden die wichtigsten Faktoren beschrieben, die sich auf die Qualität von Mixed Reality-Apps auswirken.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: App-Qualitätskriterien, Mixed Reality, Mixed Reality-App, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 858b0782c4e6754ee6753d463d5fe498e3a893f6c21b3f1c86ac14f8c0e6c8cf
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189380"
---
# <a name="app-quality-criteria"></a>Kriterien für die App-Qualität

In diesem Dokument werden die wichtigsten Faktoren beschrieben, die sich auf die Qualität von Mixed Reality-Apps auswirken. Für jeden Faktor werden die folgenden Informationen bereitgestellt:
* Übersicht: Eine kurze Beschreibung des Qualitätsfaktors und dessen Bedeutung.
* Auswirkungen auf das Gerät: Welche Art von Fenster Mixed Reality Gerät ist betroffen?
* Qualitätskriterien: Auswerten des Qualitätsfaktors.
* Messen: Methoden zum Messen (oder Erleben) des Problems.
* Empfehlungen: Zusammenfassung der Ansätze zur Verbesserung der Benutzerfreundlichkeit.
* Ressourcen: relevante Entwickler- und Entwurfsressourcen, die nützlich sind, um bessere App-Erfahrungen zu erstellen.

## <a name="frame-rate"></a>Bildfrequenz

Die Bildfrequenz ist die erste Säule der Hologrammstabilität und des Benutzerfreundlichkeits. Die Bildfrequenz unterhalb der empfohlenen Ziele kann dazu führen, dass Hologramme jitterisch erscheinen, was sich negativ auf die Zuverlässigkeit der Erfahrung auswirkt und potenziell zu Augenmüdigkeit führt. Die Zielbildfrequenz für Ihre Erfahrung mit Windows Mixed Reality immersiven Headsets beträgt je nach unterstützten Windows Mixed Reality kompatiblen PCs 60 Hz oder 90 Hz. Für HoloLens beträgt die Zielbildfrequenz 60 Hz.

### <a name="device-impact"></a>Auswirkungen auf das Gerät

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

|  Sehr hoch  |  Erfüllt |  Fehler |
--- | --- | ---
| Die App erfüllt konsistent das Zielframes pro Sekunde (FPS) für das Zielgerät: 60 FPS auf HoloLens; 90 fps auf Ultra-PCs; und 60 FPS auf gängigen PCs. | Die App verfügt über zeitweilige Frameverluste, die die Kernerfahrung nicht beeinträchtigen, oder FPS ist konsistent niedriger als das gewünschte Ziel, beeinträchtigt jedoch nicht die App-Erfahrung. | Die Bildfrequenz der App sinkt im Durchschnitt alle 10 Sekunden oder weniger. |

### <a name="how-to-measure"></a>Messen

* Ein Diagramm der Echtzeitbildfrequenz wird von der [Windows Geräteportal](using-the-windows-device-portal.md#system-performance) unter "Systemleistung" bereitgestellt.
* Fügen Sie zum Debuggen der Entwicklung der App einen Diagnoseleistungsindikator für die Bildfrequenz hinzu. Einen Beispielzähler finden Sie unter Ressourcen.
* Bildfrequenzverluste können auf dem Gerät während der Ausführung der App erfolgen, indem Sie den Kopf von einer Seite zur anderen bewegen. Wenn das Hologramm eine unerwartete Jitterybewegung anzeigt, ist wahrscheinlich eine niedrige Bildfrequenz oder die Stabilitätsebene die Ursache.

### <a name="recommendations"></a>Empfehlungen

* Fügen Sie am Anfang der Entwicklungsarbeit einen Bildfrequenzzähler hinzu.
* Änderungen, die zu einem Abfall der Bildfrequenz kommen, sollten ausgewertet und entsprechend als Leistungsfehler behoben werden.

### <a name="resources"></a>Ressourcen

#### <a name="documentation"></a>Dokumentation

* [Grundlegendes zur Leistung für Mixed Reality](understanding-performance-for-mixed-reality.md)
* [Hologrammstabilität und Framerate](hologram-stability.md#frame-rate)
* [Ressourcenleistungsbudget](../../design/asset-creation-process.md)
* [Leistungsempfehlungen für Unity](../unity/performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a>Tools und Tutorials

* [Mixed Reality Toolkit, FPS-Indikatoranzeige](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [Mixed Reality Toolkit, Shader](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a>Externe Verweise

* [Unity, Optimieren mobiler Anwendungen](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a>Hologrammstabilität

Stabile Hologramme erhöhen die Benutzerfreundlichkeit und Zuverlässigkeit Ihrer App und sorgen für ein komfortableres Anzeigeerlebnis für den Benutzer. Die Qualität der Hologrammstabilität ist das Ergebnis einer guten App-Entwicklung und der Fähigkeit des Geräts, seine Umgebung zu verstehen (nachzuverfolgen). Die Framerate ist zwar die erste Säule der Stabilität, aber andere Faktoren können sich auf die Stabilität auswirken, z. B.:

* Verwendung der Stabilisierungsebene
* Abstand zu Raumankern
* Nachverfolgung

### <a name="device-impact"></a>Auswirkungen auf das Gerät

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

|  Sehr hoch  |  Erfüllt |  Fehler |
--- | --- | ---
|  Hologramme werden konsistent stabil angezeigt. | Sekundärer Inhalt zeigt unerwartete Verschiebungen an. oder unerwartete Bewegung beeinträchtigt nicht die allgemeine App-Erfahrung. | Primärer Inhalt im Frame zeigt unerwartete Verschiebungen an. |

### <a name="how-to-measure"></a>Messen

Während sie das Gerät verwenden und die Benutzeroberfläche anzeigen:

* Bewegen Sie den Kopf von einer Seite zur anderen. Wenn die Hologramme unerwartete Bewegungen zeigen, ist eine niedrige Bildfrequenz oder eine falsche Ausrichtung der Stabilitätsebene an der Fokuspunktebene die wahrscheinliche Ursache.
* Bewegen Sie sich um die Hologramme und die Umgebung, und suchen Sie nach Verhaltensweisen wie Badieren und Springen. Diese Art von Bewegung wird wahrscheinlich dadurch verursacht, dass das Gerät die Umgebung nicht verfolgt oder die Entfernung zum Raumanker.
* Wenn sich große oder mehrere Hologramme im Rahmen befinden, beobachten Sie das Hologrammverhalten in verschiedenen Tiefen, während Sie die Kopfposition von einer Seite zur anderen bewegen. Wenn Störungen auftreten, wird dies wahrscheinlich durch die Stabilisierungsebene verursacht.

### <a name="recommendations"></a>Empfehlungen

* Fügen Sie am Anfang der Entwicklungsarbeit einen Bildfrequenzzähler hinzu.
* Verwenden Sie die Stabilisierungsebene.
* Rendern Sie verankerte Hologramme immer innerhalb von 3 Metern ihres Ankers.
* Stellen Sie sicher, dass Ihre Umgebung für die ordnungsgemäße Nachverfolgung eingerichtet ist.
* Entwerfen Sie Ihre Erfahrung so, dass Hologramme auf verschiedenen Fokustiefeebenen innerhalb des Frames vermieden werden.

### <a name="resources"></a>Ressourcen

#### <a name="documentation"></a>Dokumentation

* [Hologrammstabilität und Framerate](hologram-stability.md#frame-rate)
* [Fallstudie: Verwenden der Stabilisierungsebene](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [Grundlegendes zur Leistung für Mixed Reality](understanding-performance-for-mixed-reality.md)
* [Leistungsempfehlungen für Unity](../unity/performance-recommendations-for-unity.md)
* [Raumanker](../../design/spatial-anchors.md)
* [Behandeln von Nachverfolgungsfehlern](../../design/coordinate-systems.md#handling-tracking-errors)
* [Stationärer Bezugsrahmen](../../design/coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a>Tools und Tutorials

* [MR Companion Kit, Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a>Hologramme Position auf realen Oberflächen

Fehlausrichtungen von Hologrammen mit physischen Objekten (wenn sie in Beziehung zueinander platziert werden sollen) sind ein eindeutiger Hinweis auf die Nicht-Vereinigung von Hologrammen und der realen Welt. Die Genauigkeit der Platzierung sollte relativ zu den Anforderungen des Szenarios sein. Beispielsweise kann die allgemeine Oberflächenplatzierung die räumliche Karte verwenden, aber eine genauere Platzierung erfordert eine gewisse Verwendung von Markern und Kalibrierung.

### <a name="device-impact"></a>Auswirkungen auf das Gerät

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

|  Sehr hoch  |  Erfüllt |  Fehler |
--- | --- | ---
| Hologramme an der Oberfläche ausgerichtet werden, in der Regel im Bereich von Cm cm bis Zoll. Wenn Sie mehr Genauigkeit benötigen, sollte die App ein effizientes Mittel für die Zusammenarbeit innerhalb der App-Spezifikation bereitstellen. | Nicht verfügbar | Die Hologramme erscheinen nicht ausgerichtet mit dem physischen Zielobjekt, indem sie entweder die Oberflächenebene unterbricht oder scheinbar von der Oberfläche weg gleitet. Wenn Genauigkeit erforderlich ist, sollten Hologramme die Näherungsspezifikation des Szenarios erfüllen. | 

### <a name="how-to-measure"></a>Messen

* Hologramme, die auf räumlicher Karte platziert werden, sollten nicht so aussehen, als ob sie über oder unter der Oberfläche erheblich gleiten.
* Hologramme, die eine genaue Platzierung erfordern, sollten über eine Form von Marker- und Kalibrierungssystem verfügen, die den Anforderungen des Szenarios entspricht.

### <a name="recommendations"></a>Empfehlungen

* Räumliche Karte ist nützlich, um Objekte auf Oberflächen zu platzieren, wenn keine Genauigkeit erforderlich ist.
* Um die beste Genauigkeit zu erhalten, verwenden Sie Marker oder Poster, um die Hologramme und einen Xbox-Controller (oder einen manuellen Ausrichtungsmechanismus) für die endgültige Kalibrierung festzulegen.
* Erwägen Sie, besonders große Hologramme in logische Teile aufzuteilen und die einzelnen Teile an der Oberfläche auszurichten.
* Falsch festgelegte Interpupillary Distance (IPD) kann sich auch auf die Hologrammausrichtung auswirken. Konfigurieren Sie immer HoloLens für die IPD des Benutzers.

### <a name="resources"></a>Ressourcen

#### <a name="documentation"></a>Dokumentation

* [Platzierung der räumlichen Zuordnung](../../design/spatial-mapping.md#placement)
* [Prozess der Raumüberprüfung](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [Bewährte Methoden für Raumanker](../../design/spatial-anchors.md#best-practices)
* [Behandeln von Nachverfolgungsfehlern](../../design/coordinate-systems.md#handling-tracking-errors)
* [Räumliche Abbildung in Unity](../unity/spatial-mapping-in-unity.md)
* [Übersicht über die Vuforia-Entwicklung](../unity/vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a>Tools und Tutorials

* [MR-Toolkit, Bibliotheken für räumliche Zuordnung](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [MR Companion Kit, Poster Kalibrierungsbeispiel](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [MR Companion Kit, Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a>Externe Verweise

* [Lowes-Fallstudie, Genauigkeitsausrichtung](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a>Anzeigen der Komfortzone

App-Entwickler steuern, wo die Augen der Benutzer konvergieren, indem sie Inhalte und Hologramme in verschiedenen Tiefen platzieren. Benutzer, die HoloLens werden immer bis zu 2,0 m aufnehmen, um ein klares Bild zu erhalten, da HoloLens Anzeigen in einer optischen Entfernung von ca. 2,0 m vom Benutzer entfernt sind. Eine unsachgemäße Inhaltstiefe kann zu visueller Störungen oder Ermüdung führen.

### <a name="device-impact"></a>Auswirkungen auf das Gerät

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

<table>
<tr>
<td> Sehr hoch </td><td><ul>
<li>Platzieren Sie den Inhalt um 2 m.</li><li>Wenn Hologramme nicht bei 2 m platziert werden können und Konflikte zwischen Konvergenz und Bewegung nicht vermieden werden können, liegt die optimale Zone für die Hologrammplatzierung zwischen 1,25 m und 5 m.</li><li>In jedem Fall sollten Designer Inhalte strukturieren, um Benutzer zur Interaktion mehr als 1 m zu ermutigen (z. B. Anpassen der Inhaltsgröße und der Standardplatzierungsparameter).</li><li>Sofern dies nicht für das Szenario erforderlich ist, sollte eine Clippingebene implementiert werden, deren Ausblendung bei 1 m beginnt.</li><li>In Fällen, in denen eine genauere Beobachtung eines bewegungslosen Hologramms erforderlich ist, sollte der Inhalt nicht näher als 50 cm sein.</li>
</ul></td>
</tr><tr>
<td> Erfüllt</td><td> Der Inhalt befindet sich innerhalb der Anzeige- und Bewegungsleitfäden, jedoch nicht ordnungsgemäß oder ohne Verwendung der Clippingebene.</td>
</tr><tr>
<td> Fehler </td><td> Der Inhalt wird zu nahe angezeigt (in der Regel &lt; 1,25 m oder &lt; 50 cm für stationäre Hologramme, die eine genauere Beobachtung erfordern).)</td>
</tr>
</table>

### <a name="how-to-measure"></a>Messen

* Der Inhalt sollte in der Regel 2 m entfernt, aber nicht näher als 1,25 oder weiter als 5 m sein.
* Mit wenigen Ausnahmen sollte der HoloLens Clipping-Renderabstand auf 85CM festgelegt werden, wobei der Inhalt ab 1 m ausgeblendet wird. Nähern Sie sich dem Inhalt, und notieren Sie sich den Effekt der Clippingebene.
* Stationärer Inhalt darf nicht näher als 50 cm entfernt sein.

### <a name="recommendations"></a>Empfehlungen

* Entwurfsinhalt für den optimalen Anzeigeabstand von 2 m.
* Legen Sie den Clippingrenderabstand auf 85 cm fest, wobei der Inhalt ab 1 m ausgeblendet wird.
* Bei feststehenden Hologrammen, die näher angezeigt werden müssen, sollte die Clippingebene nicht näher als 30 cm sein, und die Ausblendung sollte mindestens 10 cm von der Clippingebene entfernt beginnen.

### <a name="resources"></a>Ressourcen

* [Renderentfernung](hologram-stability.md#hologram-render-distances)
* [Fokuspunkt in Unity](../unity/focus-point-in-unity.md)
* [Experimentieren mit Skalierung](../../design/scale.md#experimenting-with-scale)
* [Text, Empfohlener Schriftgrad](../../design/typography.md#recommended-font-size)

## <a name="depth-switching"></a>Tiefenwechsel

Unabhängig von der Anzeige von Komfortproblemen kann die Anforderung, dass der Benutzer häufig oder schnell zwischen nah- und fernen Fokusobjekten (einschließlich Hologrammen und realen Inhalten) wechseln muss, zu okzitaler Ermüdung und allgemeiner Störungen führen.

### <a name="device-impact"></a>Auswirkungen auf das Gerät

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

|  Sehr hoch  |  Erfüllt |  Fehler |
--- | --- | ---
|  Eingeschränkter oder natürlicher Tiefenwechsel, der nicht dazu führt, dass der Benutzer sich unnatürlich neu konzentriert. | Ein plötzlicher Tiefenwechsel ist dies der Kern, der in die App-Erfahrung integriert ist, oder ein plötzlicher Tiefenschalter, der durch unerwartete Inhalte in der realen Welt verursacht wird. | Konsistenter Tiefenschalter oder plötzlicher Tiefenwechsel, der für die App-Erfahrung nicht erforderlich oder kernig ist. | 

### <a name="how-to-measure"></a>Messen

* Wenn die App erfordert, dass der Benutzer den Tiefenfokus konsistent und/oder plötzlich ändert, liegt ein Tiefenwechselproblem vor.

### <a name="recommendations"></a>Empfehlungen

* Behalten Sie den primären Inhalt auf einer konsistenten Fokusebene bei, und stellen Sie sicher, dass die Stabilisierungsebene der Fokuspunktebene entspricht. Dadurch werden okzibulische Ermüdung und unerwartete Hologrammbewegungen entschärft.

### <a name="resources"></a>Ressourcen

* [Renderentfernung](hologram-stability.md#hologram-render-distances)
* [Fokuspunkt in Unity](../unity/focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a>Verwendung von raumbezogenem Sound

In Windows Mixed Reality stellt die Audio-Engine die aurale Komponente der Mixed Reality-Umgebung bereit, indem 3D-Sound mithilfe von Richtungs-, Entfernungs- und Umgebungssimulationen simuliert wird. Die Verwendung von räumlichem Sound in einer Anwendung ermöglicht Entwicklern, Sounds in einem dreidimensionalen Raum (Kugel) rund um den Benutzer zu platzieren. Diese Sounds werden dann so aussehen, als würden sie von realen physischen Objekten oder den Mixed Reality-Hologrammen in der Umgebung des Benutzers stammen. Räumlicher Sound ist ein leistungsstarkes Tool für Immersion, Barrierefreiheit und UX-Design in Mixed Reality-Anwendungen.

### <a name="device-impact"></a>Auswirkungen auf das Gerät

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

|  Sehr hoch  |  Erfüllt |  Fehler |
--- | --- | ---
|  Der Sound wird logisch räumlich verräumlicht, und die Benutzeroberfläche verwendet sound entsprechend, um die Objektermittlung und das Benutzerfeedback zu unterstützen. Sound ist natürlich und für Objekte relevant und im gesamten Szenario normalisiert. | Räumliche Audiodaten werden aus Gründen der Zuverlässigkeit angemessen verwendet, fehlen jedoch als Mittel, um benutzerbezogenes Feedback und Erkennbarkeit zu unterstützen. | Der Sound wird nicht wie erwartet räumlich verräumlicht, und/oder es fehlt an Sound, um den Benutzer innerhalb der Benutzeroberfläche zu unterstützen. Oder räumliche Audiodaten wurden beim Entwurf des Szenarios nicht berücksichtigt oder verwendet. | 

### <a name="how-to-measure"></a>Messen

* Im Allgemeinen sollten relevante Töne von Ziel holografischen Hologrammen (z. B. Holografischer Hund) ausgeben.
* Soundhinweise sollten auf der gesamten Benutzeroberfläche verwendet werden, um den Benutzer bei Feedback oder dem Bewusstsein von Aktionen außerhalb des holografischen Frames zu unterstützen.

### <a name="recommendations"></a>Empfehlungen

* Verwenden Sie räumliche Audiodaten, um die Objektermittlung und Benutzeroberflächen zu unterstützen.
* Echte Sounds funktionieren besser als synthetisierter oder unnatürlicher Sound.
* Die meisten Sounds sollten räumlich verräumlicht werden.
* Vermeiden Sie unsichtbare Emitter.
* Vermeiden Sie räumliche Maskierung.
* Normalisieren Sie alle Sounds.

### <a name="resources"></a>Ressourcen

#### <a name="documentation"></a>Dokumentation

* [Raumklang](../../design/spatial-sound.md)
* [Raumklangentwurf](../../design/spatial-sound-design.md)
* [Raumklang in Unity](../unity/spatial-sound-in-unity.md)
* [Fallstudie, Räumlicher Sound für HoloTour](../../design/case-study-spatial-sound-design-for-holotour.md)
* [Fallstudie: Verwenden von räumlichem Sound in RoboRaid](../../design/case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a>Tools und Tutorials

* [Mixed Reality Toolkit – Räumliche Audiodaten](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a>Fokus auf Holographic Frame-Grenzen (FOV)

Gut entworfene Benutzeroberflächen können einen nützlichen Kontext der virtuellen Umgebung erstellen und verwalten, die sich um die Benutzer erstreckt. Die Verringerung der Auswirkungen der FOV-Grenzen umfasst ein durchdachtes Design der Inhaltsskala und des Kontexts, die Verwendung räumlicher Audiodaten, Leitsysteme und die Position des Benutzers. Wenn dies richtig erfolgt ist, wird der Benutzer durch die FOV-Grenzen weniger beeinträchtigt, während er eine komfortable App-Erfahrung hat.

### <a name="device-impact"></a>Auswirkungen auf das Gerät

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

|  Sehr hoch  |  Erfüllt |  Fehler |
--- | --- | ---
|  Der Benutzer verliert nie den Kontext, und die Anzeige ist komfortabel. Kontextunterstützung wird für große Objekte bereitgestellt. Informationen zur Auffindbarkeit und Anzeige von Objekten außerhalb des Frames finden Sie hier. Im Allgemeinen sind das Bewegungsdesign und die Skalierung der Hologramme für eine komfortable Anzeige geeignet. | Der Benutzer verliert nie den Kontext, aber in eingeschränkten Situationen kann zusätzliche Bewegung erforderlich sein. In eingeschränkten Situationen führt die Skalierung dazu, dass Hologramme entweder den vertikalen oder horizontalen Frame unterbrechen, was dazu führt, dass einige Bewegungsbewegungen Hologramme anzeigen. | Der Benutzer, der wahrscheinlich den Kontext und/oder die konsistente Bewegung verliert, ist erforderlich, um Hologramme anzuzeigen. Keine Kontextleitfäden für große holografische Objekte, das Verschieben von Objekten, die leicht außerhalb des Rahmens ohne Erkennbarkeitsleitfaden verloren gehen, oder hohe Hologramme erfordern eine reguläre Bewegungsbewegung. | 

### <a name="how-to-measure"></a>Messen

* Der Kontext für ein (großes) Hologramm geht verloren oder wird nicht verstanden, weil er an den Grenzen abgeschnitten wird.
* Positionen von Hologrammen sind aufgrund der fehlenden Aufmerksamkeit oder des Inhalts, die sich schnell in den holografischen Rahmen bewegen, schwer zu finden.
* Das Szenario erfordert eine regelmäßige und sich wiederholende Kopfbewegung nach oben und unten, um ein Hologramm vollständig zu sehen, das zu Sehmüdigkeit führt.

### <a name="recommendations"></a>Empfehlungen

* Starten Sie die Benutzeroberfläche mit kleinen Objekten, die zum FOV passen, und gehen Sie dann mit visuellen Hinweisen zu größeren Versionen über.
* Verwenden Sie räumliche Audio- und Aufmerksamkeitswiedergabe, um den Benutzer bei der Suche nach Inhalten zu unterstützen, die sich außerhalb des FOV befinden.
* Vermeiden Sie so weit wie möglich Hologramme, die den FOV vertikal abschneiden.
* Stellen Sie dem Benutzer In-App-Anleitungen bereit, um einen optimalen Anzeigeort zu erhalten.

### <a name="resources"></a>Ressourcen

#### <a name="documentation"></a>Dokumentation

* [Holografischer Rahmen](../../design/holographic-frame.md)
* [Fallstudie, HoloStudio Benutzeroberflächen- und Interaktionsentwurfslernen](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [Skalierung von Objekten und Umgebungen](../../design/scale.md)
* [Cursor, visuelle Hinweise](../../design/cursors.md#visual-cues)

#### <a name="external-references"></a>Externe Verweise

* [Viel Ado über die FOV](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a>Inhalt reagiert auf Benutzerposition

Hologramme sollten auf die Benutzerposition ungefähr auf die gleiche Weise reagieren wie "echte" Objekte. Ein wesentlicher Entwurfsüberlegung sind Benutzeroberflächenelemente, die nicht unbedingt davon ausgehen können, dass die Position eines Benutzers stationär ist und sich an die Bewegung des Benutzers anpasst. Das Entwerfen einer App, die sich ordnungsgemäß an die Benutzerposition anpasst, führt zu einer besseren Benutzerfreundlichkeit und vereinfacht die Verwendung.

### <a name="device-impact"></a>Auswirkungen auf das Gerät

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

<table>
<tr>
<td> Sehr hoch </td><td> Inhalt und Benutzeroberfläche passen sich an Benutzerpositionen an, sodass Benutzer im Rahmen der erwarteten Benutzerbewegung auf natürliche Weise mit Inhalten interagieren können.</td>
</tr><tr>
<td> Erfüllt </td><td> Die Benutzeroberfläche passt sich an die Benutzerposition an, kann jedoch die Ansicht wichtiger Inhalte beeinträchtigen, sodass der Benutzer seine Position anpassen muss.</td>
</tr><tr>
<td> Fehler </td><td><ol>
<li>Benutzeroberflächenelemente gehen während der Verschiebung verloren oder werden gesperrt, was dazu führt, dass Benutzer unnatürlich zu Steuerelementen zurückkehren (oder diese suchen).</li><li>Benutzeroberflächenelemente beschränken die Ansicht des primären Inhalts.</li><li>Die Benutzeroberflächenbewegung ist nicht für die Anzeige von Entfernung und Geschwindigkeit optimiert, insbesondere bei <a href="../../design/billboarding-and-tag-along.md">Tag-Along-UI-Elementen.</a></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a>Messen

* Alle Messungen sollten innerhalb eines angemessenen Bereichs des Szenarios durchgeführt werden. Während die Benutzerbewegung variieren wird, versuchen Sie nicht, die App mit extremer Benutzerbewegung auszutricksen.
* Für Benutzeroberflächenelemente sollten relevante Steuerelemente unabhängig von der Benutzerbewegung verfügbar sein. Wenn der Benutzer beispielsweise eine 3D-Karte mit Zoom anzeigt und durchläuft, sollte das Zoomsteuerelement für den Benutzer unabhängig vom Standort verfügbar sein.

### <a name="recommendations"></a>Empfehlungen

* Der Benutzer ist die Kamera und steuert die Bewegung. Lassen Sie sie laufwerken.
* Erwägen Sie die Suche nach Text- und Menüsystemen, die andernfalls weltversperrt oder verdeckt wären, wenn sich ein Benutzer bewegen würde.
* Verwenden Sie tag-along für Inhalte, die dem Benutzer folgen müssen, während dem Benutzer weiterhin angezeigt wird, was sich vor dem Benutzer befindet.

### <a name="resources"></a>Ressourcen

#### <a name="documentation"></a>Dokumentation

* [Interaktionsgestaltung](../../discover/hologram.md)
* [Farbe, Licht und Material](../../design/color-light-and-materials.md)
* [Billboarding und Tag-along](../../design/billboarding-and-tag-along.md)
* [Instinktive Interaktionen](../../design/interaction-fundamentals.md)
* [Eigenbewegung und Ortsveränderung des Benutzers](../../design/comfort.md#self-motion-and-user-locomotion)

## <a name="input-interaction-clarity"></a>Übersichtlichkeit der Eingabeinteraktion

Die Übersichtlichkeit der Eingabeinteraktion ist entscheidend für die Benutzerfreundlichkeit einer App und umfasst Eingabekonsistenz, Annäherbarkeit und Auffindbarkeit von Interaktionsmethoden. Benutzer können plattformweite allgemeine Interaktionen ohne Relearning verwenden. Wenn die App über benutzerdefinierte Eingaben verfügt, sollte sie eindeutig kommuniziert und veranschaulicht werden.

### <a name="device-impact"></a>Auswirkungen auf das Gerät

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

|  Sehr hoch  |  Erfüllt |  Fehler |
--- | --- | ---
|  Eingabeinteraktionsmethoden stimmen mit Windows Mixed Reality bereitgestellten [Anleitung](../../design/interaction-fundamentals.md)überein. Benutzerdefinierte Eingaben sollten nicht mit Standardeingaben redundant sein (sondern eine Standardinteraktion verwenden) und müssen dem Benutzer klar kommuniziert und veranschaulicht werden. | Ähnlich wie am besten, aber benutzerdefinierte Eingaben sind mit Standardeingabemethoden redundant. Benutzer können das Ziel und den Fortschritt der App-Benutzeroberfläche dennoch erreichen. | Schwer zu verstehende Eingabemethode oder Schaltflächenzuordnung. Die Eingabe ist stark angepasst, unterstützt keine Standardeingabe, keine Anweisungen oder verursacht wahrscheinlich Probleme mit Dermüdung und Komfort. | 

### <a name="how-to-measure"></a>Messen

* Die App verwendet konsistente [Standardeingabemethoden.](../../design/interaction-fundamentals.md)
* Wenn die App über benutzerdefinierte Eingaben verfügt, wird sie über Folgendes klar kommuniziert:
* Erfahrung bei der ersten Ausführung
* Einführungsbildschirme
* QuickInfos
* Hand Coach
* Hilfeabschnitt
* Voice-over

### <a name="recommendations"></a>Empfehlungen

* Verwenden Sie nach Möglichkeit Standardeingabemethoden.
* Stellen Sie Demos, Tutorials und QuickInfos für nicht standardmäßige Eingabemethoden bereit.
* Verwenden Sie ein konsistentes Interaktionsmodell in der gesamten App.

### <a name="resources"></a>Ressourcen

#### <a name="documentation"></a>Dokumentation

* [Instinktive Interaktionen](../../design/interaction-fundamentals.md)
* [Interaktivierbare Objekte](../../design/interactable-object.md)
* [Anvisieren mit dem Kopf und Verweilen](../../design/gaze-and-dwell.md)
* [Cursor](../../design/cursors.md)
* [Komfort und Anv](../../design/comfort.md#gaze-direction)
* [Spracheingabe](../../design/voice-input.md)
* [Motion-Controller](../../design/motion-controllers.md)
* [Leitfaden für Eingabeportierung für Unity](../porting-apps/input-porting-guide-for-unity.md)
* [Tastatureingabe in Unity](../unity/keyboard-input-in-unity.md)
* [Anvisieren in Unity](../unity/gaze-in-unity.md)
* [Motion-Controller in Unity](../unity/motion-controllers-in-unity.md)
* [Gesten in Unity](../unity/gestures-in-unity.md)
* [Spracheingabe in Unity](../unity/voice-input-in-unity.md)
* [Tastatur-, Maus- und Controllereingaben in DirectX](./keyboard-mouse-and-controller-input-in-directx.md)
* [Anvisieren mit dem Kopf und mit den Augen in DirectX](../native/gaze-in-directx.md)
* [Hände und Motion-Controller in DirectX](../native/hands-and-motion-controllers-in-directx.md)
* [Spracheingabe in DirectX](../native/voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a>Tools und Tutorials

* [Fallstudie: Die Verfolgung von personaleren Computing-Kapazitäten](../../out-of-scope/case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [Umwandlungsstudie: HoloStudio Lernfunktionen für Benutzeroberflächen- und Interaktionsdesign](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [Beispiel-App: Periodische Tabelle der Elemente](../unity/periodic-table-of-the-elements.md)
* [Beispiel-App: Lunar-Modul](../unity/lunar-module.md)

## <a name="interactable-objects"></a>Interaktivierbare Objekte

Eine Schaltfläche ist seit langem eine Metapher zum Auslösen eines Ereignisses in der abstrakten 2D-Welt. In der dreidimensionalen Mixed Reality-Welt müssen wir uns nicht mehr auf diese Abstraktionswelt beschränken. Alles kann ein interaktivierbares Objekt sein, das ein Ereignis auslöst. Ein interaktives Objekt kann als alles dargestellt werden, von einer Kaffeetasse auf dem Tisch bis hin zu einem in der Luft gleitenden Sprechblasen. Unabhängig vom Formular sollten interaktive Objekte vom Benutzer durch visuelle und Audiohinweise eindeutig erkennbar sein.

### <a name="device-impact"></a>Auswirkungen auf das Gerät

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

|  Sehr hoch  |  Erfüllt |  Fehler |
--- | --- | ---
|  Unabhängig von der Form sind interaktivierbare Objekte durch visuelle und Audiohinweise über drei Zustände hinweg erkennbar: im Leerlauf, zielorientiert und ausgewählt. "Sehen Sie es, sagen Sie es" ist klar und wird während der gesamten Benutzeroberfläche konsistent verwendet. Objekte werden skaliert und verteilt, um eine fehlerfreie Zielgruppenadressierung zu ermöglichen. | Der Benutzer kann das Objekt durch Audio- oder visuelles Feedback als interaktiv erkennen und das Objekt als Ziel und aktivieren. | Wenn keine visuellen oder Audiohinweise vorhanden sind, kann der Benutzer ein interaktives Objekt nicht erkennen. Interaktionen sind aufgrund der Objektskala oder des Abstands zwischen Objekten fehleranfällig. | 

### <a name="how-to-measure"></a>Messen

* Interaktive Objekte sind als "interaktiv" erkennbar. einschließlich Schaltflächen, Menüs und app-spezifischer Inhalte. Als Faustregel sollte es einen visuellen und audio-Hinweis geben, wenn interaktive Objekte als Ziel verwendet werden.

### <a name="recommendations"></a>Empfehlungen

* Verwenden Sie visuelles und Audiofeedback für Interaktionen.
* Visuelles Feedback sollte für jeden Eingabezustand (leer, zielgerichtet, ausgewählt) unterschieden werden.
* Interaktive Objekte sollten skaliert und für fehlerfreie Zielgruppenadressierung platziert werden.
* Gruppierte interaktivierbare Objekte (z. B. eine Menüleiste oder Liste) sollten über einen geeigneten Abstand für die Zielgruppenadressierung verfügen.
* Schaltflächen und Menüs, die Sprachbefehle unterstützen, sollten Textbezeichnungen für das Befehlsschlüsselwort ("Sehen, sagen Sie es") bereitstellen.

### <a name="resources"></a>Ressourcen

#### <a name="documentation"></a>Dokumentation

* [Interaktionsfähiges Objekt](../../design/interactable-object.md)
* [Text in Unity](../unity/text-in-unity.md)
* [Begrenzungsrahmen und App-Leiste](../../design/app-bar-and-bounding-box.md)
* [Spracheingabe](../../design/voice-input.md)

#### <a name="tools-and-tutorials"></a>Tools und Tutorials

* [Mixed Reality Toolkit – Benutzererfahrung](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a>Raumüberprüfung

Apps, die räumliche Zuordnungsdaten erfordern, benötigen das Gerät, um diese Daten im Laufe der Zeit und sitzungsübergreifend automatisch zu sammeln, während der Benutzer seine Umgebung mit dem aktiven Gerät untersucht. Die Vollständigkeit und Qualität dieser Daten hängt von einer Reihe von Faktoren ab, z. B. vom Umfang der Vom Benutzer durchgeführten Erkundungen, davon, wie viel Zeit seit der Untersuchung verstrichen ist und ob Objekte wie Türen und Türen seit dem Scannen des Bereichs durch das Gerät verschoben wurden. Viele Apps analysieren die räumlichen Zuordnungsdaten zu Beginn der Benutzeroberfläche, um zu beurteilen, ob der Benutzer zusätzliche Schritte ausführen sollte, um die Vollständigkeit und Qualität der räumlichen Karte zu verbessern. Wenn der Benutzer die Umgebung überprüfen muss, sollte während der Überprüfung eine klare Anleitung bereitgestellt werden.

### <a name="device-impact"></a>Auswirkungen auf das Gerät

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

|  Sehr hoch  |  Erfüllt |  Fehler |
--- | --- | ---
|  Die Visualisierung des räumlichen Gitters teilt Benutzern mit, dass die Überprüfung ausgeführt wird. Der Benutzer weiß eindeutig, was zu tun ist und wann der Scan gestartet und beendet wird. | Die Visualisierung des räumlichen Gitternetzes wird bereitgestellt, aber der Benutzer weiß möglicherweise nicht genau, was zu tun ist, und es werden keine Statusinformationen bereitgestellt. | Keine Visualisierung des Gitternetzes. Für den Benutzer werden keine Anleitungen dazu bereitgestellt, wo er suchen soll oder wann der Scan gestartet/beendet wird. |

### <a name="how-to-measure"></a>Messen

* Während einer erforderlichen Raumüberprüfung werden visuelle und audio-Anleitungen bereitgestellt, die angeben, wo gesucht werden soll und wann die Überprüfung gestartet und beendet werden soll.

### <a name="recommendations"></a>Empfehlungen

* Geben Sie an, wie viel des Gesamtvolumens in der Benutzerumgebung Teil der Benutzeroberfläche sein muss.
* Kommunizieren Sie, wenn der Scan gestartet und beendet wird, z. B. eine Statusanzeige.
* Verwenden Sie während der Überprüfung eine Visualisierung des Gitternetzes.
* Stellen Sie visuelle und Audiohinweise bereit, um den Benutzer zu ermutigen, den Raum zu suchen und zu bewegen.
* Informieren Sie den Benutzer darüber, wo er die Daten verbessern soll. In vielen Fällen kann es am besten sein, dem Benutzer mitzuteilen, was er tun muss (z. B. an der Obergrenze oder hinter der Hülle), um die erforderliche Scanqualität zu erhalten.

### <a name="resources"></a>Ressourcen

#### <a name="documentation"></a>Dokumentation

* [Raumabtastvisualisierung](../../design/room-scan-visualization.md)
* [Fallstudie: Erweitern der Räumlichen Zuordnungsfunktionen von HoloLens](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [Fallstudie: Räumlicher Soundentwurf für HoloTour](../../design/case-study-spatial-sound-design-for-holotour.md)
* [Fallstudie: Erstellen einer immersiven Benutzeroberfläche in Fragmenten](../../out-of-scope/case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a>Tools und Tutorials

* [Mixed Reality Toolkit – Benutzererfahrung](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a>Richtungsindikatoren

In einer Mixed Reality-App können Sich Inhalte außerhalb des Sichtfelds befinden oder von realen Objekten verdeckt werden. Eine gut entworfene App erleichtert dem Benutzer die Suche nach nicht sichtbaren Inhalten. Richtungsindikatoren warnen einen Benutzer vor wichtigen Inhalten und stellen Eine Anleitung für den Inhalt relativ zur Position des Benutzers bereit. Anleitungen für nicht sichtbare Inhalte können in Form von Soundemittern, Richtungspfeilen oder direkten visuellen Hinweisen erfolgen.

### <a name="device-impact"></a>Auswirkungen auf das Gerät

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

|  Sehr hoch  |  Erfüllt |  Fehler |
--- | --- | ---
|  Visuelle und Audiohinweise leiten den Benutzer direkt zu relevanten Inhalten außerhalb des Sichtfelds. | Ein Pfeil oder ein Indikator, der den Benutzer in die allgemeine Richtung des Inhalts zeigt. | Relevante Inhalte befinden sich außerhalb des Sichtfelds, und dem Benutzer wird ein schlechter oder kein Standortleitfaden bereitgestellt. | 

### <a name="how-to-measure"></a>Messen

* Relevante Inhalte außerhalb des Benutzerbereichs können über visuelle und/oder Audiohinweise ermittelt werden.

### <a name="recommendations"></a>Empfehlungen

* Wenn sich relevante Inhalte außerhalb des Sichtfelds des Benutzers befindet, verwenden Sie Richtungsindikatoren und Audiohinweise, um den Benutzer zum Inhalt zu leiten. In vielen Fällen wird eine direkte visuelle Anleitung gegenüber richtungsweisenden Pfeilen bevorzugt.
* Richtungsindikatoren sollten nicht in den Cursor integriert werden.

### <a name="resources"></a>Ressourcen

* [Holografischer Rahmen](../../design/holographic-frame.md)

## <a name="data-loading"></a>Laden von Daten

Ein Statussteuerelement gibt dem Benutzer eine Rückmeldung, dass ein Vorgang mit langer Laufzeit ausgeführt wird. Dies kann bedeuten, dass der Benutzer nicht mit der App interagieren kann, wenn die Statusanzeige sichtbar ist, und auch angeben kann, wie lange die Wartezeit sein kann.

### <a name="device-impact"></a>Auswirkungen auf das Gerät

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Qualitätskriterien

|  Sehr hoch  |  Erfüllt |  Fehler |
--- | --- | ---
|  Animierter visueller Indikator in Form einer Statusanzeige oder eines Rings, der den Fortschritt während des Ladens oder Verarbeitens von Daten anzeigt. Der visuelle Indikator enthält Anleitungen dazu, wie lange die Wartezeit dauern könnte. | Der Benutzer wird darüber informiert, dass das Laden von Daten ausgeführt wird, aber es gibt keinen Hinweis darauf, wie lange der Wartevorgang dauern könnte. | Keine Datenlade- oder Verarbeitungsindikatoren für Aufgaben, die länger als 5 Sekunden dauern. |

### <a name="how-to-measure"></a>Messen

* Überprüfen Sie während des Ladens der Daten, ob mehr als 5 Sekunden lang kein leerer Zustand vorhanden ist.

### <a name="recommendations"></a>Empfehlungen

* Geben Sie einen Datenlade-Animator an, der den Fortschritt in jeder Situation anzeigt, in der der Benutzer feststellen kann, dass diese App angehalten oder abgestürzt ist. Eine sinnvolle Faustregel ist jede Ladeaktivität, die mehr als 5 Sekunden dauern kann.

### <a name="resources"></a>Ressourcen

* [Anzeigen des Fortschritts](../../design/progress.md)