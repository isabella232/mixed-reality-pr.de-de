---
title: Hologrammstabilität
description: Die HoloLens Hologramme automatisch stabil, aber es gibt Schritte, die Entwickler ergreifen können, um die Hologrammstabilität weiter zu verbessern.
author: thetuvix
ms.author: alexturn
ms.date: 07/08/2020
ms.topic: article
keywords: Hologramme, Stabilität, HoloLens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Bildfrequenz, Rendering, Neuprojektion, Farbtrennung
appliesto:
- HoloLens
ms.openlocfilehash: a9a260208764db86d3a2d945cb6a1a611e66848889dfc228d9341f10b8e054ef
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198818"
---
# <a name="hologram-stability"></a>Hologrammstabilität

Um stabile Hologramme zu erzielen, HoloLens über eine integrierte Bildstabilisierungspipeline. Die Stabilitätspipeline funktioniert automatisch im Hintergrund, sodass Sie keine zusätzlichen Schritte ausführen müssen, um sie zu aktivieren. Sie sollten jedoch Techniken anwenden, die die Hologrammstabilität verbessern und Szenarien vermeiden, die die Stabilität verringern.

## <a name="hologram-quality-terminology"></a>Terminologie zur Hologrammqualität

Die Qualität von Hologrammen ist das Ergebnis einer guten Umgebung und einer guten App-Entwicklung. Apps, die mit konstanten 60 Frames pro Sekunde in einer Umgebung ausgeführt werden, in der HoloLens die Umgebung nachverfolgen kann, stellen sicher, dass das Hologramm und das übereinstimmende Koordinatensystem synchron sind. Aus Sicht eines Benutzers werden Hologramme, die stationär sein sollen, nicht relativ zur Umgebung bewegt.

Die folgende Terminologie kann Ihnen helfen, Probleme mit der Umgebung, inkonsistente oder niedrige Renderingraten oder andere Probleme zu identifizieren.
* **Genauigkeit.** Sobald das Hologramm in der Welt gesperrt und in der realen Welt platziert ist, sollte es dort bleiben, wo es relativ zur umgebungsumgeflichen Umgebung platziert wird und unabhängig von Benutzerbewegungen oder kleinen und geringer Umgebungsänderungen ist. Wenn ein Hologramm später an einem unerwarteten Ort angezeigt wird, ist dies ein *Genauigkeitsproblem.* Solche Szenarien können vorkommen, wenn zwei unterschiedliche Räume identisch aussehen.
* **Jitter.** Benutzer beobachten Jitter als hochfrequenzes Shaking eines Hologramms, das auftreten kann, wenn die Nachverfolgung der Umgebung beeinträchtigt wird. Für Benutzer wird in der Lösung die [Sensoroptimierung ausgeführt.](/hololens/hololens-updates)
* **Judder.** Niedrige Renderinghäufigkeiten führen zu ungleichmäßiger Bewegung und doppelten Bildern von Hologrammen. Judder ist besonders bei Hologrammen mit Bewegung zu sehen. Entwickler müssen eine Konstante von [60 FPS verwalten.](hologram-stability.md#frame-rate)
* **Drift.** Benutzer sehen Abweichungen, wenn ein Hologramm sich scheinbar von seiner ursprünglichen Stelle entfernt. Drift tritt auf, wenn Hologramme weit von Raumankern entfernt [sind,](../../design/spatial-anchors.md)insbesondere in nicht zugeordneten Teilen der Umgebung. Das Erstellen von Hologrammen in der Nähe von Raumankern senkt die Wahrscheinlichkeit von Abweichungen.
* **Sprunghaftigkeit.** Wenn ein Hologramm gelegentlich von seiner Position "springt". Sprunghaftigkeit kann auftreten, wenn die Nachverfolgung Hologramme an das aktualisierte Verständnis Ihrer Umgebung an passt.
* **Schwimmen.** Wenn ein Hologramm der Bewegung des Kopfes des Benutzers entspricht, scheint es zu nieren. Das Problem tritt auf, wenn die [](hologram-stability.md#reprojection)Anwendung die Neuprojektion nicht vollständig implementiert [](/hololens/hololens-calibration) hat und die HoloLens für den aktuellen Benutzer nicht kalibriert ist. Der Benutzer kann die Kalibrierungsanwendung [erneut ausführen,](/hololens/hololens-calibration) um das Problem zu beheben. Entwickler können die Stabilitätsebene aktualisieren, um die Stabilität weiter zu verbessern.
* **Farbtrennung.** Die Displays in HoloLens sind sequenzielle Farbanzeigen, die flashfarbene Kanäle von Rot-Grün-Blau-Grün mit 60 Hz (einzelne Farbfelder werden mit 240 Hz angezeigt). Jedes Mal, wenn ein Benutzer ein bewegtes Hologramm mit seinen Augen verfolgt, trennen sich die führenden und nachdenkenden Kanten dieses Hologramms in ihren konstituierenden Farben, was einen Effekt erzeugt. Der Grad der Trennung hängt von der Geschwindigkeit des Hologramms ab. In einigen seltenen Fällen kann das schnelle Bewegen eines Kopfs beim Blick auf ein stilles Hologramm auch zu einem Effekt führen, der als *[Farbtrennung bezeichnet wird.](hologram-stability.md#color-separation)*

## <a name="frame-rate"></a>Bildfrequenz

Die Bildfrequenz ist die erste Säule der Hologrammstabilität. Damit Hologramme in der Welt stabil erscheinen, muss jedes dem Benutzer angezeigte Bild die Hologramme an der richtigen Stelle gezeichnet haben. Der wird HoloLens 240 Mal pro Sekunde aktualisiert und zeigt vier separate Farbfelder für jedes neu gerenderte Bild an, was zu einer Benutzererfahrung von 60 FPS (Frames pro Sekunde) führt. Um die bestmögliche Benutzererfahrung zu bieten, müssen Anwendungsentwickler 60 FPS verwalten. Dies bedeutet, dass alle 16 Millisekunden durchgängig ein neues Image für das Betriebssystem zur Verfügung stellt.

**60 FPS** Um Hologramme so zu zeichnen, als ob sie sich in der realen Welt HoloLens, müssen Bilder aus der Position des Benutzers gerendert werden. Da das Rendern von Bildern einige Zeit HoloLens vorhersagt, wo sich der Kopf eines Benutzers befinden wird, wenn die Bilder in den Anzeigen angezeigt werden. Dieser Vorhersagealgorithmus ist jedoch eine Näherung. HoloLens verfügt über Hardware, mit der das gerenderte Bild angepasst wird, um die Abweichung zwischen der vorhergesagten Kopfposition und der tatsächlichen Kopfposition zu berücksichtigen. Durch die Anpassung wird das Bild, das dem Benutzer angezeigt wird, so angezeigt, als würde es von der richtigen Position gerendert, und Hologramme verhalten sich stabil. Die Bildaktualisierungen funktionieren am besten mit kleinen Änderungen und können bestimmte Dinge im gerenderten Bild nicht vollständig beheben, z. B. Motion-Paramelx.

Durch das Rendern mit 60 FPS führen Sie drei Dinge aus, um stabile Hologramme zu erstellen:
1. Minimieren der Gesamtlatenz zwischen dem Rendern eines Bilds und dem Vom Benutzer angezeigten Bild. In einer Engine mit einem Spiel und einem Renderthread, der in lockstep ausgeführt wird, kann die Ausführung mit 30FPS eine zusätzliche Latenz von 33,3 ms hinzufügen. Die Verringerung der Latenz verringert den Vorhersagefehler und erhöht die Hologrammstabilität.
2. Damit jedes Bild, das die Augen des Benutzers erreicht, eine konsistente Latenz hat. Wenn Sie bei 30 FPS rendern, zeigt die Anzeige weiterhin Bilder bei 60 FPS an, was bedeutet, dass das gleiche Bild zweimal in einer Zeile angezeigt wird. Der zweite Frame hat 16,6 ms mehr Latenz als der erste Frame und muss eine deutlichere Fehlermenge korrigieren. Diese Inkonsistenz in der Fehlergröße kann unerwünschte 60-Hz-Zieher verursachen.
3. Verringern des Auftretens von Vibration (Judder), die sich durch ungleichmäßige Bewegung und Doppelbilder bemerkbar macht. Eine schnellere Bewegung von Hologrammen und niedrigere Renderingraten gehen mit verstärkter Vibration einher. Die Möglichkeit, jederzeit 60 FPS zu verwalten, hilft dabei, Zieher für ein bestimmtes bewegendes Hologramm zu vermeiden.

**Konsistenz der Framerate** Die Konsistenz der Bildfrequenz ist genauso wichtig wie eine hohe Frames pro Sekunde. Gelegentlich gelöschte Frames sind für jede inhaltsreiche Anwendung unvermeidbar, und die HoloLens implementiert einige komplexe Algorithmen zur Wiederherstellung nach gelegentlichen Störungen. Eine ständig schwankende Framerate ist für einen Benutzer jedoch deutlich spürbarer als eine konstante Ausführung mit niedrigeren Frameraten. Beispielsweise erscheint eine Anwendung, die für fünf Frames (60 FPS für die Dauer dieser fünf Frames) reibungslos rendert und dann jeden anderen Frame für die nächsten 10 Frames (30 FPS für die Dauer dieser 10 Frames) löscht, instabiler als eine Anwendung, die konsistent mit 30 FPS rendert.

In einem verwandten Hinweis drosselt das Betriebssystem Anwendungen auf 30 FPS, wenn [die Mixed Reality-Erfassung](/hololens/holographic-photos-and-videos) ausgeführt wird.

**Leistungsanalyse** Es gibt verschiedene Arten von Tools, die verwendet werden können, um die Framerate Ihrer Anwendung zu messen, z. B.:
* GPUView
* Visual Studio-Grafikdebugger
* In 3D-Engines wie Unity integrierte Profiler

## <a name="hologram-render-distances"></a>Hologramm-Renderentfernungen

>[!VIDEO https://www.youtube.com/embed/-606oZKLa_s]

Das visuelle System des Menschen integriert mehrere entfernungsabhängige Signale, wenn es ein Objekt fixiert und konzentriert.
* [Besendung:](https://en.wikipedia.org/wiki/Accommodation_%28eye%29) Der Fokus eines einzelnen Auges.
* [Konvergenz:](https://en.wikipedia.org/wiki/Convergence_(eye)) Zwei Augen bewegen sich nach innen oder nach außen, um ein Objekt zu zentriert.
* [Binokenbild:](https://en.wikipedia.org/wiki/Stereopsis) Unterschiede zwischen den Bildern mit dem linken und rechten Auge, die von der Entfernung eines Objekts von Ihrem Fixierungspunkt abhängig sind.
* Schattierung, relative Winkelgröße und andere Monoken -Hinweise (einzelnes Auge).

Konvergenz und Konvergenz sind einzigartig, da sich ihre zusätzlichen Hinweise darauf bezieht, wie sich die Augen ändern, um Objekte in unterschiedlichen Entfernungen zu erkennen. Beim natürlichen Betrachten sind Konvergenz und Beherbung miteinander verknüpft. Wenn die Augen etwas in der Nähe sehen (z. B. Ihre Nasen), kreuzen sich die Augen und sind bis zu einem nahem Punkt zu sehen. Wenn die Augen unendlich sehen, werden die Augen parallel, und das Auge ist unendlich. 

Benutzer, die HoloLens, werden immer bis zu 2,0 m aufnehmen, um ein klares Bild zu erhalten, da die HoloLens-Displays in einem optischen Abstand von etwa 2,0 m vom Benutzer festgelegt sind. App-Entwickler steuern, wo die Augen der Benutzer konvergieren, indem sie Inhalte und Hologramme in verschiedenen Tiefen platzieren. Wenn Benutzer unterschiedliche Abstände aufnehmen und konvergieren, ist die natürliche Verknüpfung zwischen den beiden Hinweise unterbrochen, was zu visuellen Zuständen oder Sehbehinderungen führen kann, insbesondere wenn die Größe des Konflikts groß ist. 

Die Vermeidung von Konflikten mit DerEnthaltung kann vermieden oder minimiert werden, indem konvergierte Inhalte so nah wie möglich an 2,0 m gehalten werden (d. h. in einer Szene mit viel Tiefe platzieren Sie die für Sie interessanten Bereiche möglichst nahe 2,0 m). Wenn Inhalte nicht in der Nähe von 2,0 m platziert werden können, ist das Auftreten des Konflikts zwischen Denk- und Nachbehaltungen am größten, wenn der Benutzer zwischen verschiedenen Entfernungen hin- und herviert. Anders ausgedrückt, es ist viel angenehmer, ein stehendes Hologramm zu betrachten, das in 50 cm Entfernung bleibt, als ein Hologramm in 50 cm Entfernung zu betrachten, das sich im Lauf der Zeit auf Sie zu und von Ihnen weg bewegt.

Das Platzieren von Inhalten bei 2,0 m ist ebenfalls von Vorteil, da die beiden Anzeigen so konzipiert sind, dass sie sich in dieser Entfernung vollständig überschneiden. Bei Bildern, die von dieser Ebene aus platziert werden, werden sie während der Bewegung von der Seite des holografischen Rahmens von einer Anzeige aus angezeigt, während sie weiterhin auf der anderen sichtbar sind. Diese Binokentogramme können die Tiefenempfinden des Hologramms stören.

**Optimale Entfernung vom Benutzer für die Positionierung von Hologrammen**

![Optimale Entfernung vom Benutzer für die Positionierung von Hologrammen](images/distanceguiderendering-750px.png)

**ClipEbenen** Für maximalen Komfort empfiehlt es sich, den Renderabstand bei 85 cm zu beschneiden, während der Inhalt ab 1 m ausgeblendet wird. In Anwendungen, in denen Hologramme und Benutzer beide stationär sind, können Hologramme nahezu 50 cm lang angezeigt werden. In diesen Fällen sollten Anwendungen eine Clipebene nicht näher als 30 cm platzieren, und das Ausblenden sollte mindestens 10 cm von der Clipebene entfernt beginnen. Wenn Inhalt näher als 85 cm liegt, ist es wichtig sicherzustellen, dass Benutzer sich nicht häufig näher oder weiter von Hologrammen bewegen oder dass Hologramme sich nicht häufig näher an oder weiter vom Benutzer bewegen, da diese Situationen höchstwahrscheinlich zu Einermut aufgrund des Konflikts bei der Beständigkeit führen. Inhalte sollten so entworfen werden, dass die Notwendigkeit von Interaktionen, die näher als 85 cm vom Benutzer liegen, minimiert werden muss. Wenn Inhalte jedoch näher als 85 cm gerendert werden müssen, ist es eine gute Faustregel für Entwickler, Szenarien zu entwerfen, in denen Benutzer und/oder Hologramme nicht mehr als 25 % der Zeit in die Tiefe gehen.

**Bewährte Methoden** Wenn Hologramme nicht bei 2 m platziert werden können und Konflikte zwischen Konvergenz und Besenkung nicht vermieden werden können, liegt die optimale Zone für die Hologrammplatzierung zwischen 1,25 m und 5 m. In jedem Fall sollten Designer Inhalte strukturieren, um Benutzer zu ermutigen, mehr als 1 m entfernt zu interagieren (z. B. Inhaltsgröße und Standardplatzierungsparameter anpassen).

## <a name="reprojection"></a>Neuprojektion
HoloLens verfügt über ein ausgereiftes hardwaregestütztes holografisches Stabilisierungsverfahren, das als Neuprojektion bezeichnet wird. Bei der Neuprojektion werden Bewegungen und Änderungen des Standpunkts (CameraPose) berücksichtigt, wenn die Szene animiert wird und der Benutzer den Kopf bewegt.  Anwendungen müssen bestimmte Aktionen ausführen, um die Neuprojektion am besten zu verwenden.


Es gibt vier Haupttypen der Neuprojektion.
* **Tiefenreprojektion:**  Erzeugt die besten Ergebnisse mit dem geringsten Aufwand aus der Anwendung.  Alle Teile der gerenderten Szene werden unabhängig von ihrer Entfernung zum Benutzer stabilisiert.  Einige Renderingartefakte sind möglicherweise sichtbar, wenn sich die Tiefe stark ändert.  Diese Option ist nur für HoloLens 2 und immersive Headsets verfügbar.
* **Planare Neuprojektion:**  Ermöglicht der Anwendung eine präzise Steuerung der Stabilisierung.  Eine Ebene wird von der Anwendung festgelegt, und alles auf dieser Ebene ist der stabilste Teil der Szene.  Je weiter ein Hologramm von der Ebene entfernt ist, desto weniger stabil ist es.  Diese Option ist auf allen Windows MR-Plattformen verfügbar.
* **Automatische planare Neuprojektion:**  Das System legt eine Stabilisierungsebene mithilfe von Informationen im Tiefenpuffer fest.  Diese Option ist auf HoloLens Generation 1 und HoloLens 2 verfügbar.
* **Keine:** Wenn die Anwendung nichts tut, wird Planar Reprojection mit der Stabilisierungsebene verwendet, die auf 2 Meter in Richtung des Anvisiertes an den Kopf des Benutzers festgelegt ist, was in der Regel zu unterstandardmäßigen Ergebnissen führt.

Anwendungen müssen bestimmte Aktionen ausführen, um die verschiedenen Arten der Neuprojektion zu ermöglichen.
* **Tiefenreprojektion:** Die Anwendung sendet ihren Tiefenpuffer für jeden gerenderten Frame an das System.  In Unity erfolgt die Tiefenreprojektion mit der Option **Freigegebener Tiefenpuffer** im **bereich Windows Mixed Reality Einstellungen** unter **XR-Plug-In-Verwaltung.**  DirectX-Apps rufen CommitDirect3D11DepthBuffer auf.  Die Anwendung sollte SetFocusPoint nicht aufrufen.
* **Planare Neuprojektion:** Auf jedem Frame teilen Anwendungen dem System die Position einer Ebene mit, die sich stabil machen soll.  Unity-Anwendungen rufen SetFocusPointForFrame auf und sollten **freigegebenen Tiefenpuffer** deaktiviert haben.  DirectX-Apps rufen SetFocusPoint auf und sollten CommitDirect3D11DepthBuffer nicht aufrufen.
* **Automatische planare Neuprojektion:** Um dies zu aktivieren, muss die Anwendung ihren Tiefenpuffer wie bei der Tiefenreprojektion an das System übermitteln. Apps, die das Mixed Reality Toolkit (MRTK) verwenden, können den [Kameraeinstellungsanbieter](/windows/mixed-reality/mrtk-unity/features/camera-system/windows-mixed-reality-camera-settings#hololens-2-reprojection-method) für die Verwendung von AutoPlanar Reprojection konfigurieren. Native Apps sollten `DepthReprojectionMode` in [den HolographicCameraRenderingParameters](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters) auf `AutoPlanar` jeden Frame festlegen. Für HoloLens Generation 1 sollte die Anwendung SetFocusPoint nicht aufrufen.

### <a name="choosing-reprojection-technique"></a>Auswählen der Methode "Reprojection"

Stabilisierungstyp |    Immersive Headsets |    HoloLens Generation 1 | HoloLens 2
--- | --- | --- | ---
Tiefenreprojektion |    Empfohlen |   – |   Empfohlen<br/><br/>Unity-Anwendungen müssen Unity 2018.4.12 und mehr, Unity 2019.3+ oder Unity 2020.3+ verwenden. Verwenden Sie andernfalls Automatische planare Neuprojektion.
Automatische planare Neuprojektion | – |   Empfohlene Standardeinstellung |   Empfohlen, wenn die Tiefenreprojektion nicht die besten Ergebnisse liefert<br/><br/>Unity-Anwendungen werden empfohlen, Unity 2018.4.12 und mehr, Unity 2019.3 oder unity 2020.3 oder mehr zu verwenden.  Frühere Unity-Versionen funktionieren mit leicht beeinträchtigten Ergebnissen der Neuprojektion.
Planare Neuprojektion |   Nicht empfohlen |   Empfohlen, wenn die automatische Planar-Lösung nicht die besten Ergebnisse liefert | Verwenden Sie , wenn keine der Tiefenoptionen gewünschte Ergebnisse liefert.    

### <a name="verifying-depth-is-set-correctly"></a>Überprüfen, ob die Tiefe richtig festgelegt ist
            
Wenn eine Methode zur Neuprojektion den Tiefenpuffer verwendet, ist es wichtig zu überprüfen, ob der Inhalt des Tiefenpuffers die gerenderte Szene der Anwendung darstellt.  Eine Reihe von Faktoren kann Probleme verursachen. Wenn beispielsweise eine zweite Kamera zum Rendern von Überlagerungen der Benutzeroberfläche verwendet wird, überschreibt sie wahrscheinlich alle Tiefeninformationen aus der tatsächlichen Ansicht.  Transparente Objekte legen häufig keine Tiefe fest.  Bei einigen Textrenderings wird die Tiefe standardmäßig nicht festgelegt.  Es gibt sichtbare Störungen beim Rendering, wenn die Tiefe nicht mit den gerenderten Hologrammen übereinstimmt.
            
HoloLens 2 verfügt über eine Schnellansicht, um anzuzeigen, wo die Tiefe festgelegt ist und nicht festgelegt wird, die über Geräteportal aktiviert werden kann.  Aktivieren Sie auf der Registerkarte **Ansichten**  >  **Hologrammstabilität** das Kontrollkästchen **Tiefenvisualisierung im Headset anzeigen.**  Bereiche, für die die Tiefe ordnungsgemäß festgelegt ist, sind blau.  Gerenderte Elemente ohne Tiefensatz werden rot markiert und müssen korrigiert werden.  

> [!NOTE]
> Die Visualisierung der Tiefe wird nicht in Mixed Reality-Aufnahme angezeigt.  Sie ist nur über das Gerät sichtbar.
            
Einige GPU-Anzeigetools ermöglichen die Visualisierung des Tiefenpuffers.  Anwendungsentwickler können diese Tools verwenden, um sicherzustellen, dass die Tiefe ordnungsgemäß festgelegt wird.  Lesen Sie die Dokumentation für die Tools der Anwendung.

### <a name="using-planar-reprojection"></a>Verwenden von Planar Reprojection
> [!NOTE]
> Bei immersiven Desktop-Headsets ist das Festlegen einer Stabilisierungsebene in der Regel kontraproduktiv, da sie weniger visuelle Qualität bietet als die Bereitstellung des Tiefenpuffers Ihrer App für das System, um eine pixelbasierte tiefenbasierte Neuprojektion zu ermöglichen. Sofern sie nicht auf einem HoloLens ausgeführt wird, sollten Sie im Allgemeinen vermeiden, die Stabilisierungsebene festzulegen.

![Stabilisierungsebene für 3D-Objekte](images/stab-plane-500px.jpg)

Das Gerät versucht automatisch, diese Ebene auszuwählen, aber die Anwendung sollte dabei helfen, den Fokuspunkt in der Szene auszuwählen. Unity-Apps, die auf einem HoloLens ausgeführt werden, sollten den besten Fokuspunkt basierend auf Ihrer Szene auswählen und an [SetFocusPoint()](../unity/focus-point-in-unity.md)übergeben. Ein Beispiel für das Festlegen des Fokuspunkts in DirectX ist in der standardmäßigen rotierenden Cubevorlage enthalten.

Unity sendet Ihren Tiefenpuffer an Windows, um eine Pixel-reprojection zu ermöglichen, wenn Sie Ihre App auf einem immersiven Headset ausführen, das mit einem Desktop-PC verbunden ist. Dies bietet eine noch bessere Imagequalität ohne explizite Arbeit durch die App. Sie sollten einen Fokuspunkt nur bereitstellen, wenn Ihre App auf einem HoloLens ausgeführt wird oder die Pro-Pixel-Neuprojektion überschrieben wird.


```cs
// SetFocusPoint informs the system about a specific point in your scene to
// prioritize for image stabilization. The focus point is set independently
// for each holographic camera.
// You should set the focus point near the content that the user is looking at.
// In this example, we put the focus point at the center of the sample hologram,
// since that is the only hologram available for the user to focus on.
// You can also set the relative velocity and facing of that content; the sample
// hologram is at a fixed point so we only need to indicate its position.
renderingParameters.SetFocusPoint(
    currentCoordinateSystem,
    spinningCubeRenderer.Position
    );
```

Die Platzierung des Fokuspunkts hängt größtenteils davon ab, was das Hologramm ansieht. Die App verfügt über den Anvektor zum Anvieren, und der App-Designer weiß, welche Inhalte der Benutzer beobachten soll.

Das Wichtigste, was ein Entwickler tun kann, um Hologramme zu stabiler machen, ist das Rendern bei 60 FPS. Wenn Sie unter 60 FPS fallen, wird die Hologrammstabilität unabhängig von der Optimierung der Stabilisierungsebene erheblich reduziert.

**Bewährte Methoden** Es gibt keine universelle Möglichkeit, die Stabilisierungsebene einzurichten, und sie ist app-spezifisch. Unsere Hauptempfehlung besteht darin, zu experimentieren und zu sehen, was für Ihr Szenario am besten funktioniert. Versuchen Sie jedoch, die Stabilisierungsebene so weit wie möglich an Inhalten auszurichten, da der gesamte Inhalt auf dieser Ebene perfekt stabil ist.

Beispiel:
* Wenn Sie nur planaren Inhalt haben (Lese-App, Videowiedergabe-App), richten Sie die Stabilisierungsebene an der Ebene aus, die Ihren Inhalt enthält.
* Wenn es drei kleine Kugeln gibt, die weltweit gesperrt sind, sollten Sie die Stabilisierungsebene durch die Mittelpunkte aller Kugeln "schneiden", die sich derzeit in der Ansicht des Benutzers befinden.
* Wenn Ihre Szene Inhalte in wesentlich unterschiedlichen Tiefen auf enthält, bevorzugen Sie weitere Objekte.
* Stellen Sie sicher, dass Sie den Stabilisierungspunkt jedes Frames so anpassen, dass er mit dem Hologramm übereinstimmt, das der Benutzer ansieht.

**Zu vermeidende Dinge** Die Stabilisierungsebene ist ein hervorragendes Tool, um stabile Hologramme zu erzielen, aber wenn sie missbraucht wird, kann dies zu schwerwiegender Bildinstabilität führen.
* Nicht "Fire and Forget" (Wird ausgelöst und vergessen) Sie können die Stabilisierungsebene hinter dem Benutzer oder an ein Objekt anfügen, das sich nicht mehr in der Ansicht des Benutzers befindet. Stellen Sie sicher, dass die Normalität der Stabilisierungsebene gegenüber der Kamera nach vorn festgelegt ist (z. B. -camera.forward).
* Ändern Sie die Stabilisierungsebene nicht schnell zwischen Extreme
* Lassen Sie die Stabilisierungsebene nicht auf einen festen Abstand bzw. eine feste Ausrichtung festgelegt.
* Lassen Sie nicht zu, dass die Stabilisierungsebene den Benutzer durchschneidet.
* Legen Sie den Fokuspunkt nicht fest, wenn Sie auf einem Desktop-PC anstatt auf einem HoloLens ausgeführt werden, und verlassen Sie sich stattdessen auf eine auf Pixeltiefe basierende Neuprojektion.

## <a name="color-separation"></a>Farbtrennung 

Aufgrund der Art HoloLens Anzeigen kann manchmal ein Artefakt namens "Farbtrennung" wahrgenommen werden. Es wird als Bild angezeigt, das in einzelne Basisfarben unterteilt wird : Rot, Grün und Blau. Das Artefakt kann besonders beim Anzeigen weißer Objekte sichtbar sein, da es große Mengen an Rot, Grün und Blau enthält. Dies ist besonders deutlich, wenn ein Benutzer ein Hologramm visuell verfolgt, das sich mit hoher Geschwindigkeit über den holografischen Frame bewegt. Eine andere Möglichkeit, wie sich das Artefakt manifestieren kann, ist das Verzerren/Vertauschen von Objekten. Wenn ein Objekt einen hohen Kontrast und/oder reine Farben wie Rot, Grün, Blau hat, wird die Farbtrennung als Verzerren verschiedener Teile des Objekts wahrgenommen.

**Beispiel dafür, wie die Farbtrennung eines mit dem Kopf gesperrten weißen runden Cursors aussehen könnte, wenn ein Benutzer den Kopf zur Seite dreht:**

![Beispiel dafür, wie die Farbtrennung eines mit dem Kopf gesperrten weißen runden Cursors aussehen könnte, wenn ein Benutzer den Kopf zur Seite drehen würde.](images/colorseparationofroundwhitecursor-300px.png)

Obwohl es schwierig ist, die Farbtrennung vollständig zu vermeiden, stehen mehrere Techniken zur Verfügung, um sie zu verringern.

**Die Farbtrennung ist auf:**
* Objekte, die sich schnell bewegen, einschließlich mit dem Kopf gesperrter Objekte wie der [Cursor](../../design/cursors.md).
* Objekte, die wesentlich weit von der [Stabilitätsebene entfernt sind.](hologram-stability.md#reprojection)

**So dämpfen Sie die Auswirkungen der Farbtrennung:**
* Sorgen Sie dafür, dass das Objekt beim Anvitätsverhalten des Benutzers verzögert wird. Es sollte so angezeigt werden, als ob es eine gewisse Trägheit auft und an das Anving "auf Trägheit" angefügt ist. Dieser Ansatz verlangsamt den Cursor (reduziert den Trennungsabstand) und setzt ihn hinter den wahrscheinlichen Anvspunkt des Benutzers. Solange es schnell aufholt, wenn der Benutzer das Anvieren nicht mehr verschiebt, sieht es natürlich aus.
* Wenn Sie ein Hologramm verschieben möchten, versuchen Sie, seine Bewegungsgeschwindigkeit unter 5 Grad/Sekunde zu halten, wenn Sie erwarten, dass der Benutzer ihm mit den Augen folgt.
* Verwenden *Sie light* anstelle von *geometry* für den Cursor. Eine Quelle virtueller Anvisierte, die an den Anvisierten angefügt ist, wird als interaktiver Zeiger wahrgenommen, verursacht jedoch keine Farbtrennung.
* Passen Sie die Stabilitätsebene an die Hologramme an, an die sich der Benutzer befindet.
* Machen Sie das Objekt rot, grün oder blau.
* Wechseln Sie zu einer unscharfen Version des Inhalts. Beispielsweise könnte ein runder weißer Cursor in eine leicht unscharfe Linie geändert werden, die in richtung der Bewegung ausgerichtet ist.

Wie zuvor sind das Rendern bei 60 FPS und das Festlegen der Stabilitätsebene die wichtigsten Techniken für die Hologrammstabilität. Wenn eine spürbare Farbtrennung zu erwarten ist, stellen Sie zunächst sicher, dass die Framerate die Erwartungen erfüllt.

## <a name="see-also"></a>Siehe auch
* [Grundlegendes zur Leistung Mixed Reality](understanding-performance-for-mixed-reality.md)
* [Farbe, Licht und Materialien](../../design/color-light-and-materials.md)
* [Instinktive Interaktionen](../../design/interaction-fundamentals.md)
* [MRTK Hologram Stabilization](/windows/mixed-reality/mrtk-unity/performance/hologram-stabilization)