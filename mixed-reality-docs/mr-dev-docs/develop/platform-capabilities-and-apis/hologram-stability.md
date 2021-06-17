---
title: Hologrammstabilität
description: HoloLens stabiliert Hologramme automatisch, aber es gibt Schritte, die Entwickler ergreifen können, um die Hologrammstabilität weiter zu verbessern.
author: thetuvix
ms.author: alexturn
ms.date: 07/08/2020
ms.topic: article
keywords: Hologramme, Stabilität, Hololens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Bildfrequenz, Rendering, Neuprojektion, Farbtrennung
appliesto:
- HoloLens
ms.openlocfilehash: 560b1551b153f1735b0106869c6a82c977693968
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110109"
---
# <a name="hologram-stability"></a>Hologrammstabilität

HoloLens verfügt über eine integrierte Bildstabilitätspipeline, um stabile Hologramme zu erzielen. Die Stabilisierungspipeline funktioniert automatisch im Hintergrund, sodass Sie keine zusätzlichen Schritte ausführen müssen, um sie zu aktivieren. Sie sollten jedoch Techniken anwenden, die die Hologrammstabilität verbessern und Szenarien vermeiden, die die Stabilität verringern.

## <a name="hologram-quality-terminology"></a>Hologrammqualitätsterminologie

Die Qualität von Hologrammen ist ein Ergebnis einer guten Umgebung und einer guten App-Entwicklung. Apps, die mit konstanten 60 Frames pro Sekunde in einer Umgebung ausgeführt werden, in der HoloLens die Umgebung nachverfolgen kann, stellt sicher, dass das Hologramm und das übereinstimmende Koordinatensystem synchronisiert sind. Aus Sicht eines Benutzers werden Hologramme, die stationär sein sollen, nicht relativ zur Umgebung verschoben.

Die folgende Terminologie kann Ihnen bei der Identifizierung von Problemen mit der Umgebung, inkonsistenten oder niedrigen Renderingraten oder anderen Problemen helfen.
* **Genauigkeit.** Sobald das Hologramm in der Welt gesperrt und in der realen Welt platziert ist, sollte es in Bezug auf die umgebungsbezogene Umgebung und unabhängig von Benutzerbewegungen oder kleinen und geringen Umgebungsänderungen an der Stelle bleiben, an der es platziert wird. Wenn ein Hologramm später an einem unerwarteten  Ort angezeigt wird, ist dies ein Genauigkeitsproblem. Solche Szenarien können auftreten, wenn zwei unterschiedliche Räume identisch aussehen.
* **Jitter.** Benutzer beobachten Jitter als hochfrequentes Vidern eines Hologramms, was passieren kann, wenn die Nachverfolgung der Umgebung abnimmt. Für Benutzer führt die Lösung die [Sensoroptimierung](/hololens/hololens-updates)aus.
* **Judder.** Niedrige Renderinghäufigkeiten führen zu ungleichmäßiger Bewegung und doppelten Bildern von Hologrammen. Judder ist besonders in Hologrammen mit Bewegung zu erkennen. Entwickler müssen eine Konstante von [60 FPS](hologram-stability.md#frame-rate)beibehalten.
* **Drift.** Benutzer sehen Eine Abweichung, da sich ein Hologramm scheinbar von dem Ort entfernt, an dem es ursprünglich platziert wurde. Drift tritt auf, wenn Sie Hologramme weit weg von [Raumankern](../../design/spatial-anchors.md)platzieren, insbesondere in nicht zugeordneten Teilen der Umgebung. Das Erstellen von Hologrammen in der Nähe von Raumankern verringert die Wahrscheinlichkeit von Abweichungen.
* **Jumpiness.** Wenn ein Hologramm gelegentlich von seiner Position "popt" oder "springt". Jumpiness kann auftreten, wenn die Nachverfolgung Hologramme an das aktualisierte Verständnis Ihrer Umgebung anpasst.
* **Schwimmen.** Wenn ein Hologramm entsprechend der Bewegung des Kopfes des Benutzers zu wankt. Das Bad tritt auf, wenn die Anwendung die [Neuprojektion](hologram-stability.md#reprojection)nicht vollständig implementiert hat und die HoloLens nicht für den aktuellen Benutzer [kalibriert](/hololens/hololens-calibration) ist. Der Benutzer kann die [Kalibrierungsanwendung](/hololens/hololens-calibration) erneut ausführen, um das Problem zu beheben. Entwickler können die Stabilisierungsebene aktualisieren, um die Stabilität weiter zu verbessern.
* **Farbtrennung.** Die Displays in HoloLens sind farblich sequenzielle Displays, die Farbkanäle von Rot-Grün-Blau-Grün bei 60 Hz blinken (einzelne Farbfelder werden bei 240 Hz angezeigt). Wenn ein Benutzer ein bewegtes Hologramm mit seinen Augen verfolgt, trennen sich die führenden und nachgestellten Ränder des Hologramms in ihren konstituierenden Farben und erzeugen einen Farbeffekt. Der Grad der Trennung hängt von der Geschwindigkeit des Hologramms ab. In einigen seltenen Fällen kann das schnelle Bewegen eines Kopfes beim Betrachten eines stationären Hologramms auch zu einem Gleiteffekt führen, der als *[Farbtrennung](hologram-stability.md#color-separation)* bezeichnet wird.

## <a name="frame-rate"></a>Bildfrequenz

Die Bildfrequenz ist die erste Säule der Hologrammstabilität. Damit Hologramme in der Welt stabil angezeigt werden, muss jedes Bild, das dem Benutzer präsentiert wird, über die Hologramme verfügen, die an der richtigen Stelle gezeichnet werden. Die Bildschirme auf HoloLens werden 240 Mal pro Sekunde aktualisiert, wobei vier separate Farbfelder für jedes neu gerenderte Bild angezeigt werden, was zu einer Benutzerfreundlichkeit von 60 FPS (Frames pro Sekunde) führt. Um die bestmögliche Erfahrung zu bieten, müssen Anwendungsentwickler 60 FPS verwalten, was bedeutet, dass dem Betriebssystem alle 16 Millisekunden konsistent ein neues Image zur Verfügung stellt.

**60 FPS** Um Hologramme so zu zeichnen, dass sie in der realen Welt liegen, muss HoloLens Bilder von der Position des Benutzers rendern. Da das Rendern von Bildern eine Weile dauert, sagt HoloLens vorher, wo sich der Kopf eines Benutzers befinden wird, wenn die Bilder in den Bildschirmen angezeigt werden. Dieser Vorhersagealgorithmus ist jedoch eine Näherung. HoloLens verfügt über Hardware, die das gerenderte Bild anpasst, um die Abweichung zwischen der vorhergesagten Kopfposition und der tatsächlichen Kopfposition zu berücksichtigen. Durch die Anpassung wird das Bild, das dem Benutzer angezeigt wird, so angezeigt, als würde es von der richtigen Position gerendert, und Hologramme sind stabil. Die Bildaktualisierungen funktionieren am besten mit kleinen Änderungen, und sie können bestimmte Dinge im gerenderten Bild nicht vollständig korrigieren, z. B. motion-parallax.

Indem Sie bei 60 FPS rendern, tun Sie drei Dinge, um stabile Hologramme zu erstellen:
1. Minimieren der Gesamtlatenz zwischen dem Rendern eines Bilds und dem Bild, das vom Benutzer angezeigt wird. In einer Engine mit einem Spiel und einem Renderthread, der in lockstep ausgeführt wird, kann die Ausführung bei 30FPS eine zusätzliche Latenz von 33,3 ms hinzufügen. Die Verringerung der Latenz verringert Vorhersagefehler und erhöht die Hologrammstabilität.
2. Damit jedes Bild, das die Augen des Benutzers erreicht, eine konsistente Latenz hat. Wenn Sie mit 30 FPS rendern, werden auf der Anzeige weiterhin Bilder mit 60 FPS angezeigt. Das bedeutet, dass das gleiche Bild zweimal in einer Zeile angezeigt wird. Der zweite Frame hat 16,6 ms mehr Latenz als der erste Frame und muss eine deutlichere Fehlermenge korrigieren. Diese Inkonsistenz in der Fehlergröße kann zu unerwünschtem 60-Hz-Judder führen.
3. Verringern des Auftretens von Vibration (Judder), die sich durch ungleichmäßige Bewegung und Doppelbilder bemerkbar macht. Eine schnellere Bewegung von Hologrammen und niedrigere Renderingraten gehen mit verstärkter Vibration einher. Wenn Sie 60 FPS jederzeit beibehalten möchten, können Sie Judder für ein bestimmtes bewegtes Hologramm vermeiden.

**Frameratenkonsistenz** Die Konsistenz der Bildfrequenz ist genauso wichtig wie eine hohe Bildfrequenz pro Sekunde. Gelegentlich gelöschte Frames sind für jede inhaltsreiche Anwendung unvermeidlich, und die HoloLens implementiert einige komplexe Algorithmen, um nach gelegentlichen Störungen wiederherzustellen. Eine ständig schwankende Framerate ist für einen Benutzer jedoch deutlich erkennbarer als eine konsistente Ausführung mit niedrigeren Bildfrequenzen. Eine Anwendung, die z. B. für fünf Frames reibungslos gerendert wird (60 FPS für die Dauer dieser fünf Frames) und dann jeden anderen Frame für die nächsten 10 Frames (30 FPS für die Dauer dieser 10 Frames) löscht, erscheint instabiler als eine Anwendung, die konsistent mit 30 FPS gerendert wird.

In diesem Zusammenhang drosselt das Betriebssystem Anwendungen auf 30 FPS, wenn [die Mixed Reality-Erfassung](/hololens/holographic-photos-and-videos) ausgeführt wird.

**Leistungsanalyse** Es gibt verschiedene Arten von Tools, die zum Vergleichen ihrer Anwendungsrahmenrate verwendet werden können, z. B.:
* GPUView
* Visual Studio-Grafikdebugger
* Profiler, die in 3D-Engines wie Unity integriert sind

## <a name="hologram-render-distances"></a>Hologrammrender entfernungen

>[!VIDEO https://www.youtube.com/embed/-606oZKLa_s]

Das visuelle System des Menschen integriert mehrere abstandsabhängige Signale, wenn es ein Objekt korrigiert und sich auf dieses konzentriert.
* [Aufnahme:](https://en.wikipedia.org/wiki/Accommodation_%28eye%29) Der Fokus eines einzelnen Auges.
* [Konvergenz:](https://en.wikipedia.org/wiki/Convergence_(eye)) Zwei Augen, die sich nach innen oder nach außen bewegen, um sich auf ein Objekt zu konzentrieren.
* [Binokulares Sehen:](https://en.wikipedia.org/wiki/Stereopsis) Dies ist ein Zusammenhang zwischen den Bildern mit den linken und rechten Augen, die von der Entfernung eines Objekts von Ihrem Fixierungspunkt abhängen.
* Schattierung, relative Winkelgröße und andere monoulare Hinweise (einzelnes Auge).

Konvergenz und Konvergenz sind einzigartig, da ihre extra-netzigen Hinweise darauf zusammenhängen, wie sich die Augen ändern, um Objekte in unterschiedlichen Abständen zu erkennen. Beim natürlichen Sehen sind Konvergenz und Konvergenz miteinander verknüpft. Wenn die Augen etwas in der Nähe sehen (z. B. Ihre Nasen), kreuzen sich die Augen und werden bis zu einem näheren Punkt aufgenommen. Wenn die Augen etwas unendlich sehen, werden die Augen parallel, und das Auge ist unendlich. 

Benutzer, die HoloLens verwenden, können immer bis zu 2,0 m aufnehmen, um ein klares Bild zu erhalten, da die HoloLens-Displays in einer optischen Entfernung von ungefähr 2,0 m vom Benutzer entfernt sind. App-Entwickler steuern, wo die Augen der Benutzer konvergieren, indem sie Inhalte und Hologramme in verschiedenen Tiefen platzieren. Wenn Benutzer unterschiedliche Abstände aufnehmen und konvergieren, wird die natürliche Verbindung zwischen den beiden Hinweisen unterbrochen, was zu visueller Störungen oder Ermüdung führen kann, insbesondere wenn die Größe des Konflikts groß ist. 

Die Minderung des Konflikts mit der Konfliktlösung kann vermieden oder minimiert werden, indem konvergierte Inhalte möglichst nahe bei 2,0 m gehalten werden (d. h., in einer Szene mit vielen Tiefenbereichen befinden sich die interessanten Bereiche nach Möglichkeit in der Nähe von 2,0 m). Wenn Inhalte nicht in der Nähe von 2,0 m platziert werden können, ist die Freundlichkeit des Konflikts zwischen Denk- und Störungen am größten, wenn der Blick des Benutzers zwischen verschiedenen Entfernungen hin und her geht. Anders ausgedrückt, es ist viel angenehmer, ein stehendes Hologramm zu betrachten, das in 50 cm Entfernung bleibt, als ein Hologramm in 50 cm Entfernung zu betrachten, das sich im Lauf der Zeit auf Sie zu und von Ihnen weg bewegt.

Das Platzieren von Inhalten auf 2,0 m ist ebenfalls von Vorteil, da die beiden Anzeigen so konzipiert sind, dass sie sich in dieser Entfernung vollständig überlappen. Bei Bildern, die von dieser Ebene aus platziert werden, werden sie bei der Verschiebung von der Seite des holografischen Rahmens von einer Anzeige angezeigt, während sie weiterhin auf der anderen sichtbar sind. Diese binokulare Störungen können die tiefen Wahrnehmung des Hologramms stören.

**Optimale Entfernung vom Benutzer für die Positionierung von Hologrammen**

![Optimale Entfernung vom Benutzer für die Positionierung von Hologrammen](images/distanceguiderendering-750px.png)

**Clipebenen** Für maximalen Komfort empfehlen wir das Beschneiden der Renderentfernung bei 85 cm, wobei der Inhalt ab 1 m ausgeblendet wird. In Anwendungen, in denen Hologramme und Benutzer beide stationär sind, können Hologramme in der Nähe von 50 cm beobachtet werden. In diesen Fällen sollten Anwendungen eine Clipebene nicht näher als 30 cm platzieren, und das Ausblenden sollte mindestens 10 cm von der Clipebene entfernt beginnen. Immer wenn der Inhalt näher als 85 cm liegt, ist es wichtig sicherzustellen, dass benutzer sich nicht häufig näher oder weiter von Hologrammen bewegen oder dass Hologramme nicht häufig näher oder weiter vom Benutzer entfernt werden, da diese Situationen höchstwahrscheinlich eine Störungen aufgrund des Konflikts zwischen Denk- und Störungen verursachen. Inhalt sollte so entworfen werden, dass die Notwendigkeit einer Interaktion zwischen 85 cm und dem Benutzer minimiert wird. Wenn Der Inhalt jedoch näher als 85 cm gerendert werden muss, ist eine gute Faustregel für Entwickler das Entwerfen von Szenarien, in denen Benutzer und/oder Hologramme nicht mehr als 25 % der Zeit in die Tiefe verschoben werden.

**Bewährte Methoden** Wenn Hologramme nicht bei 2 m platziert werden können und Konflikte zwischen Konvergenz und Bewegung nicht vermieden werden können, liegt die optimale Zone für die Hologrammplatzierung zwischen 1,25 m und 5 m. In jedem Fall sollten Designer Inhalte strukturieren, um Benutzer zur Interaktion mehr als 1 m zu ermutigen (z. B. Anpassen der Inhaltsgröße und der Standardplatzierungsparameter).

## <a name="reprojection"></a>Neuprojektion
HoloLens verfügt über eine anspruchsvolle hardwareunterstützte holografische Stabilisierungstechnik, die als Reprojektion bezeichnet wird. Bei der Neuprojektion werden Bewegung und Änderung des Standpunkts (CameraPose) berücksichtigt, während die Szene animiert und der Benutzer den Kopf bewegt.  Anwendungen müssen bestimmte Maßnahmen ergreifen, um die Neuprojektion optimal zu nutzen.


Es gibt vier Haupttypen der Neuprojektion.
* **Tiefenreprojektion:**  Erzeugt die besten Ergebnisse mit dem geringsten Aufwand aus der Anwendung.  Alle Teile der gerenderten Szene werden unabhängig voneinander basierend auf ihrem Abstand zum Benutzer stabilisiert.  Einige Renderingartefakte sind möglicherweise sichtbar, wenn es starke Änderungen in der Tiefe gibt.  Diese Option ist nur für HoloLens 2 immersive Headsets verfügbar.
* **Planare Neuprojektion:**  Ermöglicht der Anwendung eine präzise Steuerung der Stabilität.  Eine Ebene wird von der Anwendung festgelegt, und alles auf dieser Ebene ist der stabilste Teil der Szene.  Wenn sich ein Hologramm weiter von der Ebene entfernt, desto weniger stabil ist es.  Diese Option ist auf allen Windows MR-Plattformen verfügbar.
* **Automatische planare Neuprojektion:**  Das System legt mithilfe von Informationen im Tiefenpuffer eine Stabilitätsebene fest.  Diese Option ist für HoloLens Generation 1 und HoloLens 2.
* **Keine:** Wenn die Anwendung nichts tut, wird die planare Neuprojektion mit der Stabilierungsebene verwendet, die auf 2 Meter in Richtung des Anvisierens mit dem Kopf des Benutzers festgelegt ist, was in der Regel zu unterstandardigen Ergebnissen führt.

Anwendungen müssen bestimmte Aktionen ausführen, um die verschiedenen Arten der Neuprojektion zu ermöglichen.
* **Tiefenreprojektion:** Die Anwendung übermittelt ihren Tiefenpuffer für jeden gerenderten Frame an das System.  In Unity erfolgt die Tiefenreprojektion mit der  Option Shared **Depth Buffer** (Freigegebener Tiefenpuffer) im Windows Mixed Reality-Einstellungen unter **XR-Plug-In-Verwaltung.**  DirectX-Apps rufen CommitDirect3D11DepthBuffer auf.  Die Anwendung sollte SetFocusPoint nicht aufrufen.
* **Planare Neuprojektion:** In jedem Frame teilen Anwendungen dem System die Position einer Ebene mit, die sich stabilisiert.  Unity-Anwendungen rufen SetFocusPointForFrame auf und sollten **den freigegebenen Tiefenpuffer** deaktiviert haben.  DirectX-Apps rufen SetFocusPoint auf und sollten CommitDirect3D11DepthBuffer nicht aufrufen.
* **Automatische planare Neuprojektion:** Um dies zu ermöglichen, muss die Anwendung ihren Tiefenpuffer wie bei der Tiefenprojektion an das System übermitteln. Apps, die das Mixed Reality Toolkit (MRTK) [](/windows/mixed-reality/mrtk-unity/features/camera-system/windows-mixed-reality-camera-settings#hololens-2-reprojection-method) verwenden, können den Kameraeinstellungsanbieter für die Verwendung von AutoPlanar Reprojection konfigurieren. Native Apps sollten in `DepthReprojectionMode` den [HolographicCameraRenderingParameters](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters) auf jeden `AutoPlanar` Frame festlegen. Für HoloLens Generation 1 sollte die Anwendung SetFocusPoint nicht aufrufen.

### <a name="choosing-reprojection-technique"></a>Auswählen der Neuprojektionstechnik

Stabilisierungstyp |    Immersive Headsets |    HoloLens Generation 1 | HoloLens 2
--- | --- | --- | ---
Tiefenprojektion |    Empfohlen |   – |   Empfohlen<br/><br/>Unity-Anwendungen müssen Unity 2018.4.12 oder höher oder Unity 2019.3 oder höher verwenden. Verwenden Sie andernfalls automatische planare Neuprojektion.
Automatische planare Neuprojektion | – |   Empfohlener Standardwert |   Empfohlen, wenn die Tiefenprojektion nicht die besten Ergebnisse liefert<br/><br/>Unity-Anwendungen sollten Unity 2018.4.12 oder höher oder Unity 2019.3 oder höher verwenden.  Frühere Unity-Versionen funktionieren mit leicht beeinträchtigten Ergebnissen der Neuprojektion.
Planare Neuprojektion |   Nicht empfohlen |   Empfohlen, wenn die automatische Planarisierung nicht die besten Ergebnisse liefert | Verwenden Sie , wenn keine der Tiefenoptionen gewünschte Ergebnisse liefert.    

### <a name="verifying-depth-is-set-correctly"></a>Überprüfen, ob die Tiefe richtig festgelegt ist
            
Wenn eine Neuprojektionsmethode den Tiefenpuffer verwendet, ist es wichtig zu überprüfen, ob der Inhalt des Tiefenpuffers die gerenderte Szene der Anwendung repräsentiert.  Eine Reihe von Faktoren kann Probleme verursachen. Wenn beispielsweise eine zweite Kamera zum Rendern von Benutzeroberflächenüberlagerungen verwendet wird, überschreibt sie wahrscheinlich alle Tiefeninformationen aus der tatsächlichen Ansicht.  Transparente Objekte legen häufig keine Tiefe fest.  Bei einigen Textrenderings wird die Tiefe standardmäßig nicht festgelegt.  Es gibt sichtbare Störungen im Rendering, wenn die Tiefe nicht mit den gerenderten Hologrammen übereinstimmen.
            
HoloLens 2 verfügt über eine Schnellansicht, die zeigt, wo die Tiefe ist und nicht festgelegt wird. Diese kann über die Geräteportal.  Aktivieren Sie **auf der Registerkarte Ansichten**  >  **Hologrammstabilität** das Kontrollkästchen **Tiefenvisualisierung im Headset** anzeigen.  Bereiche, für die die Tiefe ordnungsgemäß festgelegt ist, sind blau.  Gerenderte Elemente, für die keine Tiefe festgelegt ist, sind rot markiert und müssen korrigiert werden.  

> [!NOTE]
> Die Visualisierung der Tiefe wird nicht in der Mixed Reality-Aufnahme.  Sie ist nur über das Gerät sichtbar.
            
Einige GPU-Anzeigetools ermöglichen die Visualisierung des Tiefenpuffers.  Anwendungsentwickler können diese Tools verwenden, um sicherzustellen, dass die Tiefe ordnungsgemäß festgelegt wird.  Die Tools der Anwendung finden Sie in der Dokumentation.

### <a name="using-planar-reprojection"></a>Verwenden der planaren Neuprojektion
> [!NOTE]
> Bei immersiven Desktop-Headsets ist das Festlegen einer Stabilitätsebene in der Regel kontraproduktiv, da sie weniger visuelle Qualität bietet als die Bereitstellung des Tiefenpuffers Ihrer App für das System, um eine tiefenbasierte Pro-Pixel-Neuprojektion zu ermöglichen. Wenn sie nicht auf einer HoloLens ausgeführt wird, sollten Sie in der Regel vermeiden, die Stabilitätsebene zu setzen.

![Stabilitätsebene für 3D-Objekte](images/stab-plane-500px.jpg)

Das Gerät versucht automatisch, diese Ebene auszuwählen, aber die Anwendung sollte ihnen helfen, indem sie den Fokuspunkt in der Szene auswählt. Unity-Apps, die auf einer HoloLens ausgeführt werden, sollten den besten Fokuspunkt basierend auf Ihrer Szene auswählen und an [SetFocusPoint() übergeben.](../unity/focus-point-in-unity.md) Ein Beispiel für das Festlegen des Fokuspunkts in DirectX ist in der standardmäßigen Vorlage für rotierende Würfel enthalten.

Unity übermittelt Ihren Tiefenpuffer an Windows, um eine Neuprojektion pro Pixel zu ermöglichen, wenn Sie Ihre App auf einem immersiven Headset ausführen, das mit einem Desktop-PC verbunden ist. Dies bietet eine noch bessere Bildqualität ohne explizite Arbeit durch die App. Sie sollten nur dann einen Fokuspunkt bereitstellen, wenn Ihre App auf einer HoloLens ausgeführt wird, oder die Pro-Pixel-Neuprojektion wird überschrieben.


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

Die Platzierung des Fokuspunkts hängt größtenteils davon ab, was das Hologramm betrachtet. Die App verfügt über den Anvisierungsvektor als Referenz, und der App-Designer weiß, welche Inhalte der Benutzer beobachten soll.

Das wichtigste, was ein Entwickler tun kann, um Hologramme zu stabilisiert, ist das Rendern mit 60 FPS. Wenn sie unter 60 FPS fällt, wird die Hologrammstabilität erheblich reduziert, unabhängig von der Optimierung der Stabilitätsebene.

**Bewährte Methoden** Es gibt keine universelle Möglichkeit zum Einrichten der Stabilitätsebene und ist app-spezifisch. Es wird empfohlen, zu experimentieren und zu sehen, was für Ihr Szenario am besten funktioniert. Versuchen Sie jedoch, die Stabilitätsebene mit so viel Inhalt wie möglich auszurichten, da der inhalt auf dieser Ebene perfekt stabil ist.

Beispiel:
* Wenn Sie nur über planaren Inhalt (Lese-App, Videowiedergabe-App) verfügen, richten Sie die Stabilitätsebene an der Ebene aus, auf der Sich ihr Inhalt befingt.
* Wenn es drei kleine Kugeln gibt, die auf der Welt gesperrt sind, lassen Sie die Stabilitätsebene durch die Zentren aller Kugeln", die sich derzeit in der Ansicht des Benutzers befinden, "ausschneiden".
* Wenn Ihre Szene Inhalte in erheblich unterschiedlichen Tiefen enthält, bevorzugen Sie weitere Objekte.
* Stellen Sie sicher, dass sie den Stabilitätspunkt jedes Frames so anpassen, dass er mit dem Hologramm, das der Benutzer betrachtet, zusammenfallen kann.

**Zu vermeidende Dinge** Die Stabilitätsebene ist ein hervorragendes Tool, um stabile Hologramme zu erreichen, aber wenn sie missbraucht wird, kann dies zu schwerwiegender Bildinstabilität führen.
* "Fire and Forget" darf nicht "fire and forget" (Aus- und Vergessen) sein. Sie können die Stabilitätsebene hinter dem Benutzer oder an ein Objekt anfügen, das sich nicht mehr in der Ansicht des Benutzers befindet. Stellen Sie sicher, dass die Normalität der Stabilisierungsebene gegenüber der Kamera nach vorn festgelegt ist (z. B. -camera.forward).
* Ändern Sie die Stabilitätsebene nicht schnell zwischen Extrems hin und her.
* Lassen Sie die Stabilitätsebene nicht auf einen festen Abstand/eine feste Ausrichtung festgelegt.
* Lassen Sie die Stabilitätsebene den Benutzer nicht durchschneiden.
* Legen Sie nicht den Fokuspunkt fest, wenn Sie auf einem Desktop-PC und nicht auf einer HoloLens ausgeführt werden, und verlassen Sie sich stattdessen auf eine tiefenbasierte Neuprojektion pro Pixel.

## <a name="color-separation"></a>Farbtrennung 

Aufgrund der Art von HoloLens-Displays kann manchmal ein Artefakt namens "Farbtrennung" wahrgenommen werden. Es wird als bildtrennendes Bild in einzelne Basisfarben dargestellt : Rot, Grün und Blau. Das Artefakt kann besonders sichtbar sein, wenn weiße Objekte angezeigt werden, da sie große Mengen an Rot, Grün und Blau haben. Dies wird besonders deutlich, wenn ein Benutzer ein Hologramm, das sich mit hoher Geschwindigkeit über den holografischen Rahmen bewegt, visuell verfolgt. Eine andere Möglichkeit, wie sich das Artefakt manifestieren kann, ist das Verzerren/Verzerren von Objekten. Wenn ein Objekt über hohen Kontrast und/oder reine Farben wie Rot, Grün, Blau verfügt, wird die Farbtrennung als Verzerren verschiedener Teile des Objekts wahrgenommen.

**Beispiel dafür, wie die Farbtrennung eines mit dem Kopf gesperrten weißen runden Cursors aussehen könnte, wenn ein Benutzer seinen Kopf auf die Seite dreht:**

![Beispiel dafür, wie die Farbtrennung eines mit dem Kopf gesperrten weißen runden Cursors aussehen könnte, wenn ein Benutzer den Kopf zur Seite dreht.](images/colorseparationofroundwhitecursor-300px.png)

Obwohl es schwierig ist, die Farbtrennung vollständig zu vermeiden, stehen mehrere Techniken zur Verfügung, um sie zu verringern.

**Die Farbtrennung ist auf:**
* Objekte, die sich schnell bewegen, einschließlich mit dem Kopf gesperrter Objekte wie der [Cursor](../../design/cursors.md).
* Objekte, die wesentlich weit von der [Stabilitätsebene entfernt sind.](hologram-stability.md#reprojection)

**So dämpfen Sie die Auswirkungen der Farbtrennung:**
* Sorgen Sie dafür, dass das Objekt beim Anvitätsverhalten des Benutzers verzögert wird. Es sollte so angezeigt werden, als ob es eine gewisse Trägheit auft, und es wird an das Anving "on 10" angefügt. Dieser Ansatz verlangsamt den Cursor (reduziert den Trennungsabstand) und setzt ihn hinter den wahrscheinlichen Anvierungspunkt des Benutzers. Solange es schnell aufholt, wenn der Benutzer das Anvieren nicht mehr verschiebt, sieht es natürlich aus.
* Wenn Sie ein Hologramm verschieben möchten, versuchen Sie, seine Bewegungsgeschwindigkeit unter 5 Grad/Sekunde zu halten, wenn Sie erwarten, dass der Benutzer ihm mit den Augen folgt.
* Verwenden *Sie light* anstelle von *geometry* für den Cursor. Eine Quelle des virtuellen Anvisiertes, die an den Anvisierten angefügt ist, wird als interaktiver Zeiger wahrgenommen, verursacht jedoch keine Farbtrennung.
* Passen Sie die Stabilitätsebene an die Hologramme an, an die sich der Benutzer befindet.
* Machen Sie das Objekt rot, grün oder blau.
* Wechseln Sie zu einer unscharfen Version des Inhalts. Beispielsweise könnte ein runder weißer Cursor in eine leicht unscharfe Linie geändert werden, die in richtung der Bewegung ausgerichtet ist.

Wie zuvor sind das Rendern bei 60 FPS und das Festlegen der Stabilitätsebene die wichtigsten Techniken für hologrammstabilität. Wenn eine spürbare Farbtrennung zu erwarten ist, stellen Sie zunächst sicher, dass die Framerate die Erwartungen erfüllt.

## <a name="see-also"></a>Siehe auch
* [Grundlegendes zur Leistung Mixed Reality](understanding-performance-for-mixed-reality.md)
* [Farbe, Licht und Materialien](../../design/color-light-and-materials.md)
* [Instinktive Interaktionen](../../design/interaction-fundamentals.md)
* [MRTK Hologram Stabilization](/windows/mixed-reality/mrtk-unity/performance/hologram-stabilization)