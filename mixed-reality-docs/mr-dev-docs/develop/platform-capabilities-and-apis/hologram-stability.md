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
ms.openlocfilehash: a4a22221d3238bb7dfed711e6ee1f11edc70238e
ms.sourcegitcommit: 12ea3fb2df4664c5efd07dcbb9040c2ff173afb6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2021
ms.locfileid: "113042291"
---
# <a name="hologram-stability"></a>Hologrammstabilität

HoloLens verfügt über eine integrierte Bildstabilitätspipeline, um stabile Hologramme zu erzielen. Die Stabilisierungspipeline funktioniert automatisch im Hintergrund, sodass Sie keine zusätzlichen Schritte ausführen müssen, um sie zu aktivieren. Sie sollten jedoch Techniken anwenden, die die Hologrammstabilität verbessern und Szenarien vermeiden, die die Stabilität verringern.

## <a name="hologram-quality-terminology"></a>Hologrammqualitätsterminologie

Die Qualität von Hologrammen ist ein Ergebnis einer guten Umgebung und einer guten App-Entwicklung. Apps, die mit konstanten 60 Frames pro Sekunde in einer Umgebung ausgeführt werden, in der HoloLens die Umgebung nachverfolgen kann, stellt sicher, dass das Hologramm und das übereinstimmende Koordinatensystem synchronisiert sind. Aus Sicht eines Benutzers werden Hologramme, die stationär sein sollen, nicht relativ zur Umgebung verschoben.

Die folgende Terminologie kann Ihnen helfen, wenn Sie Probleme mit der Umgebung, inkonsistente oder niedrige Renderingraten oder andere Probleme identifizieren.
* **Genauigkeit.** Sobald das Hologramm weltweit gesperrt und in der realen Welt platziert ist, sollte es in Bezug auf die umgebungsbezogene Umgebung und unabhängig von Benutzerbewegungen oder kleinen und platzsparenden Umgebungsänderungen dort bleiben, wo es platziert wird. Wenn ein Hologramm später an einem unerwarteten  Ort angezeigt wird, ist dies ein Genauigkeitsproblem. Solche Szenarien können auftreten, wenn zwei unterschiedliche Räume identisch aussehen.
* **Jitter.** Benutzer beobachten Jitter als hochfrequentes Vidern eines Hologramms, das auftreten kann, wenn die Nachverfolgung der Umgebung abnimmt. Für Benutzer führt die Lösung die [Sensoroptimierung](/hololens/hololens-updates)aus.
* **Judder.** Niedrige Renderinghäufigkeiten führen zu ungleichmäßiger Bewegung und doppelten Bildern von Hologrammen. Judder ist besonders in Hologrammen mit Bewegung zu erkennen. Entwickler müssen eine Konstante von [60 FPS](hologram-stability.md#frame-rate)beibehalten.
* **Drift.** Benutzer sehen Abweichungen, da sich ein Hologramm scheinbar von dem Ort entfernt, an dem es ursprünglich platziert wurde. Drift tritt auf, wenn Sie Hologramme weit weg von [Raumankern](../../design/spatial-anchors.md)platzieren, insbesondere in nicht zugeordneten Teilen der Umgebung. Das Erstellen von Hologrammen in der Nähe von Raumankern verringert die Wahrscheinlichkeit von Abweichungen.
* **Jumpiness.** Wenn ein Hologramm gelegentlich von seiner Position "popt" oder "springt". Jumpiness kann auftreten, wenn die Nachverfolgung Hologramme an das aktualisierte Verständnis Ihrer Umgebung anpasst.
* **Schwimmen.** Wenn ein Hologramm entsprechend der Bewegung des Kopfes des Benutzers zu wankt. Das Bad tritt auf, wenn die Anwendung die [Neuprojektion](hologram-stability.md#reprojection)nicht vollständig implementiert hat und die HoloLens nicht für den aktuellen Benutzer [kalibriert](/hololens/hololens-calibration) ist. Der Benutzer kann die [Kalibrierungsanwendung](/hololens/hololens-calibration) erneut ausführen, um das Problem zu beheben. Entwickler können die Stabilisierungsebene aktualisieren, um die Stabilität weiter zu verbessern.
* **Farbtrennung.** Die Displays in HoloLens sind farblich sequenzielle Displays, die Farbkanäle von Rot-Grün-Blau-Grün bei 60 Hz blinken (einzelne Farbfelder werden bei 240 Hz angezeigt). Wenn ein Benutzer ein bewegtes Hologramm mit seinen Augen verfolgt, trennen sich die führenden und nachgestellten Ränder des Hologramms in ihren konstituierenden Farben, wodurch ein Farbeffekt erzeugt wird. Der Grad der Trennung hängt von der Geschwindigkeit des Hologramms ab. In einigen seltenen Fällen kann das schnelle Bewegen eines Kopfes beim Betrachten eines stationären Hologramms auch zu einem Gleiteffekt führen, der als *[Farbtrennung](hologram-stability.md#color-separation)* bezeichnet wird.

## <a name="frame-rate"></a>Bildfrequenz

Die Bildfrequenz ist die erste Säule der Hologrammstabilität. Damit Hologramme in der Welt stabil angezeigt werden, muss jedes Bild, das dem Benutzer präsentiert wird, die Hologramme an der richtigen Stelle zeichnen. Die Displays auf HoloLens werden 240 Mal pro Sekunde aktualisiert, wobei vier separate Farbfelder für jedes neu gerenderte Bild angezeigt werden, was zu einer Benutzerfreundlichkeit von 60 FPS (Frames pro Sekunde) führt. Um die bestmögliche Erfahrung zu bieten, müssen Anwendungsentwickler 60 FPS verwalten. Dies bedeutet, dass dem Betriebssystem alle 16 Millisekunden konsistent ein neues Image zur Verfügung stellt.

**60 FPS** Um Hologramme so zu zeichnen, dass sie in der realen Welt liegen, muss HoloLens Bilder von der Position des Benutzers rendern. Da das Rendern von Bildern eine Weile dauert, sagt HoloLens vorher, wo sich der Kopf eines Benutzers befinden wird, wenn die Bilder in den Bildschirmen angezeigt werden. Dieser Vorhersagealgorithmus ist jedoch eine Näherung. HoloLens verfügt über Hardware, die das gerenderte Bild anpasst, um die Abweichung zwischen der vorhergesagten Kopfposition und der tatsächlichen Kopfposition zu berücksichtigen. Durch die Anpassung wird das Bild, das dem Benutzer angezeigt wird, so angezeigt, als würde es von der richtigen Position gerendert, und Hologramme sind stabil. Die Bildaktualisierungen funktionieren am besten mit kleinen Änderungen, und sie können bestimmte Dinge im gerenderten Bild nicht vollständig korrigieren, z. B. motion-parallax.

Indem Sie bei 60 FPS rendern, tun Sie drei Dinge, um stabile Hologramme zu erstellen:
1. Minimieren der Gesamtlatenz zwischen dem Rendern eines Bilds und dem Bild, das vom Benutzer angezeigt wird. In einer Engine mit einem Spiel und einem Renderthread, der in lockstep ausgeführt wird, kann die Ausführung bei 30FPS eine zusätzliche Latenz von 33,3 ms hinzufügen. Die Reduzierung der Latenz verringert Vorhersagefehler und erhöht die Hologrammstabilität.
2. Damit jedes Bild, das die Augen des Benutzers erreicht, eine konsistente Latenz hat. Wenn Sie mit 30 fps rendern, werden auf der Anzeige weiterhin Bilder mit 60 FPS angezeigt. Das bedeutet, dass das gleiche Bild zweimal in einer Zeile angezeigt wird. Der zweite Frame hat 16,6 ms mehr Latenz als der erste Frame und muss eine deutlichere Fehlermenge korrigieren. Diese Inkonsistenz in der Fehlergröße kann zu unerwünschtem 60-Hz-Judder führen.
3. Verringern des Auftretens von Vibration (Judder), die sich durch ungleichmäßige Bewegung und Doppelbilder bemerkbar macht. Eine schnellere Bewegung von Hologrammen und niedrigere Renderingraten gehen mit verstärkter Vibration einher. Die Beibehaltung von 60 FPS zu jedem Zeitpunkt hilft dabei, Judder für ein bestimmtes bewegendes Hologramm zu vermeiden.

**Frameratenkonsistenz** Die Konsistenz der Bildfrequenz ist genauso wichtig wie eine hohe Bildfrequenz pro Sekunde. Gelegentlich gelöschte Frames sind für jede inhaltsreiche Anwendung unvermeidlich, und die HoloLens implementiert einige komplexe Algorithmen, um nach gelegentlichen Störungen wiederherzustellen. Eine ständig schwankende Framerate ist für einen Benutzer jedoch deutlich erkennbarer als eine konsistente Ausführung mit niedrigeren Bildfrequenzen. Eine Anwendung, die z. B. für fünf Frames reibungslos gerendert wird (60 FPS für die Dauer dieser fünf Frames) und dann jeden anderen Frame für die nächsten 10 Frames (30 FPS für die Dauer dieser 10 Frames) löscht, erscheint instabiler als eine Anwendung, die konsistent bei 30 FPS gerendert wird.

In diesem Zusammenhang drosselt das Betriebssystem Anwendungen auf 30 FPS, wenn [die Mixed Reality-Erfassung](/hololens/holographic-photos-and-videos) ausgeführt wird.

**Leistungsanalyse** Es gibt verschiedene Arten von Tools, die zum Vergleichen ihrer Anwendungsrahmenrate verwendet werden können, z. B.:
* GPUView
* Visual Studio-Grafikdebugger
* Profiler, die in 3D-Engines wie Unity integriert sind

## <a name="hologram-render-distances"></a>Hologrammrender entfernungen

>[!VIDEO https://www.youtube.com/embed/-606oZKLa_s]

Das visuelle System des Menschen integriert mehrere abstandsabhängige Signale, wenn es ein Objekt fixiert und sich auf dieses konzentriert.
* [Aufnahme:](https://en.wikipedia.org/wiki/Accommodation_%28eye%29) Der Fokus eines einzelnen Auges.
* [Konvergenz:](https://en.wikipedia.org/wiki/Convergence_(eye)) Zwei Augen bewegen sich nach innen oder nach außen, um ein Objekt in den Mittelpunkt zu bringen.
* [Binokulares Sehen:](https://en.wikipedia.org/wiki/Stereopsis) Dies ist ein Zusammenhang zwischen den Bildern mit den linken und rechten Augen, die von der Entfernung eines Objekts von Ihrem Fixierungspunkt abhängen.
* Schattierung, relative Winkelgröße und andere monoulare Hinweise (einzelnes Auge).

Konvergenz und Konvergenz sind einzigartig, da ihre extra-netzigen Hinweise darauf zusammenhängen, wie sich die Augen ändern, um Objekte in unterschiedlichen Abständen zu erkennen. Beim natürlichen Sehen sind Konvergenz und Konvergenz miteinander verknüpft. Wenn die Augen etwas in der Nähe sehen (z. B. Ihre Nasen), kreuzen sich die Augen und sind an einem punktnahen Punkt unterzubringen. Wenn die Augen etwas unendlich sehen, werden die Augen parallel, und das Auge ist unendlich. 

Benutzer, die HoloLens verwenden, können immer bis zu 2,0 m aufnehmen, um ein klares Bild zu erhalten, da die HoloLens-Displays in einer optischen Entfernung von ungefähr 2,0 m vom Benutzer entfernt sind. App-Entwickler steuern, wo die Augen der Benutzer konvergieren, indem sie Inhalte und Hologramme in verschiedenen Tiefen platzieren. Wenn Benutzer unterschiedliche Abstände aufnehmen und konvergieren, wird die natürliche Verbindung zwischen den beiden Hinweisen unterbrochen, was zu visueller Störungen oder Ermüdung führen kann, insbesondere wenn die Größe des Konflikts groß ist. 

Die Minderung des Konflikts mit der Konfliktlösung kann vermieden oder minimiert werden, indem konvergierte Inhalte möglichst nahe bei 2,0 m gehalten werden (d. h., in einer Szene mit vielen Tiefenbereichen befinden sich die interessanten Bereiche nach Möglichkeit in der Nähe von 2,0 m). Wenn Inhalte nicht in der Nähe von 2,0 m platziert werden können, ist die Freundlichkeit des Konflikts zwischen Denk- und Störungen am größten, wenn der Blick des Benutzers zwischen verschiedenen Entfernungen hin und her geht. Anders ausgedrückt, es ist viel angenehmer, ein stehendes Hologramm zu betrachten, das in 50 cm Entfernung bleibt, als ein Hologramm in 50 cm Entfernung zu betrachten, das sich im Lauf der Zeit auf Sie zu und von Ihnen weg bewegt.

Das Platzieren von Inhalten bei 2,0 m ist ebenfalls vorteilhaft, da die beiden Anzeigen so konzipiert sind, dass sie sich in dieser Entfernung vollständig überlappen. Bei Bildern, die von dieser Ebene aus platziert werden, werden sie während des Wechsels von der Seite des holografischen Rahmens von einer Anzeige angezeigt, während sie weiterhin auf der anderen sichtbar sind. Diese binokulare Störungen können die Tiefeneigenz des Hologramms stören.

**Optimale Entfernung vom Benutzer für die Positionierung von Hologrammen**

![Optimale Entfernung vom Benutzer für die Positionierung von Hologrammen](images/distanceguiderendering-750px.png)

**ClipEbenen** Für maximalen Komfort empfehlen wir das Beschneiden der Renderentfernung bei 85 cm, wobei der Inhalt ab 1 m ausgeblendet wird. In Anwendungen, in denen Hologramme und Benutzer stationär sind, können Hologramme nahezu 50 cm lang angezeigt werden. In diesen Fällen sollten Anwendungen eine Clipebene nicht näher als 30 cm platzieren, und das Ausblenden sollte mindestens 10 cm von der Clipebene entfernt beginnen. Immer wenn der Inhalt näher als 85 cm liegt, ist es wichtig sicherzustellen, dass benutzer sich nicht häufig näher oder weiter von Hologrammen bewegen oder dass Hologramme nicht häufig näher oder weiter vom Benutzer entfernt werden, da diese Situationen höchstwahrscheinlich eine Störungen aufgrund des Konflikts zwischen Denk- und Störungen verursachen. Inhalt sollte so entworfen werden, dass die Notwendigkeit einer Interaktion zwischen 85 cm und dem Benutzer minimiert wird. Wenn Der Inhalt jedoch näher als 85 cm gerendert werden muss, ist eine gute Faustregel für Entwickler das Entwerfen von Szenarien, in denen Benutzer und/oder Hologramme nicht mehr als 25 % der Zeit in die Tiefe verschoben werden.

**Bewährte Methoden** Wenn Hologramme nicht bei 2 m platziert werden können und Konflikte zwischen Konvergenz und Bewegung nicht vermieden werden können, liegt die optimale Zone für die Hologrammplatzierung zwischen 1,25 m und 5 m. In jedem Fall sollten Designer Inhalte strukturieren, um Benutzer zur Interaktion mehr als 1 m zu ermutigen (z. B. Anpassen der Inhaltsgröße und der Standardplatzierungsparameter).

## <a name="reprojection"></a>Neuprojektion
HoloLens verfügt über eine anspruchsvolle hardwareunterstützte holografische Stabilisierungstechnik, die als Reprojektion bezeichnet wird. Bei der Neuprojektion werden Bewegung und Änderung des Standpunkts (CameraPose) berücksichtigt, während die Szene animiert und der Benutzer den Kopf bewegt.  Anwendungen müssen bestimmte Aktionen ausführen, um die Neuprojektion am besten zu verwenden.


Es gibt vier Haupttypen der Neuprojektion.
* **Tiefenreprojektion:**  Erzeugt die besten Ergebnisse mit dem geringsten Aufwand aus der Anwendung.  Alle Teile der gerenderten Szene werden unabhängig von ihrer Entfernung zum Benutzer stabilisiert.  Einige Renderingartefakte sind möglicherweise sichtbar, wenn sich die Tiefe stark ändert.  Diese Option ist nur für HoloLens 2 und immersive Headsets verfügbar.
* **Planare Neuprojektion:**  Ermöglicht der Anwendung eine präzise Steuerung der Stabilisierung.  Eine Ebene wird von der Anwendung festgelegt, und alles auf dieser Ebene ist der stabilste Teil der Szene.  Je weiter ein Hologramm von der Ebene entfernt ist, desto weniger stabil ist es.  Diese Option ist auf allen Windows MR-Plattformen verfügbar.
* **Automatische planare Neuprojektion:**  Das System legt eine Stabilisierungsebene mithilfe von Informationen im Tiefenpuffer fest.  Diese Option ist auf HoloLens Generation 1 und HoloLens 2 verfügbar.
* **Keine:** Wenn die Anwendung nichts tut, wird Planar Reprojection mit der Stabilisierungsebene verwendet, die auf 2 Meter in Richtung des Anvisiertes an den Kopf des Benutzers festgelegt ist, was in der Regel zu unterstandardmäßigen Ergebnissen führt.

Anwendungen müssen bestimmte Aktionen ausführen, um die verschiedenen Arten der Neuprojektion zu ermöglichen.
* **Tiefenreprojektion:** Die Anwendung sendet ihren Tiefenpuffer für jeden gerenderten Frame an das System.  In Unity erfolgt die Tiefenreprojektion mit der Option **Freigegebener Tiefenpuffer** im **Bereich Windows Mixed Reality-Einstellungen** unter **XR-Plug-In-Verwaltung.**  DirectX-Apps rufen CommitDirect3D11DepthBuffer auf.  Die Anwendung sollte SetFocusPoint nicht aufrufen.
* **Planare Neuprojektion:** In jedem Frame weisen Anwendungen dem System die Position einer Ebene an, die sich stabil machen soll.  Unity-Anwendungen rufen SetFocusPointForFrame auf und sollten **freigegebenen Tiefenpuffer** deaktiviert haben.  DirectX-Apps rufen SetFocusPoint auf und sollten CommitDirect3D11DepthBuffer nicht aufrufen.
* **Automatische planare Neuprojektion:** Um dies zu aktivieren, muss die Anwendung ihren Tiefenpuffer wie bei der Tiefenreprojektion an das System übermitteln. Apps, die das Mixed Reality Toolkit (MRTK) verwenden, können den [Kameraeinstellungsanbieter](/windows/mixed-reality/mrtk-unity/features/camera-system/windows-mixed-reality-camera-settings#hololens-2-reprojection-method) für die Verwendung von AutoPlanar Reprojection konfigurieren. Native Apps sollten `DepthReprojectionMode` in [den HolographicCameraRenderingParameters](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters) auf `AutoPlanar` jeden Frame festlegen. Für HoloLens Generation 1 sollte die Anwendung SetFocusPoint nicht aufrufen.

### <a name="choosing-reprojection-technique"></a>Auswählen der Methode "Reprojection"

Stabilisierungstyp |    Immersive Headsets |    HoloLens Generation 1 | HoloLens 2
--- | --- | --- | ---
Tiefenreprojektion |    Empfohlen |   – |   Empfohlen<br/><br/>Unity-Anwendungen müssen Unity 2018.4.12 und mehr, Unity 2019.3+ oder Unity 2020.3+ verwenden. Verwenden Sie andernfalls Automatische planare Neuprojektion.
Automatische planare Neuprojektion | – |   Empfohlene Standardeinstellung |   Empfohlen, wenn die Tiefenreprojektion nicht die besten Ergebnisse liefert<br/><br/>Unity-Anwendungen werden empfohlen, Unity 2018.4.12 und mehr, Unity 2019.3 oder unity 2020.3+ zu verwenden.  Frühere Unity-Versionen funktionieren mit leicht beeinträchtigten Ergebnissen der Neuprojektion.
Planare Neuprojektion |   Nicht empfohlen |   Empfohlen, wenn die automatische Planar-Lösung nicht die besten Ergebnisse liefert | Verwenden Sie , wenn keine der Tiefenoptionen gewünschte Ergebnisse liefert.    

### <a name="verifying-depth-is-set-correctly"></a>Überprüfen, ob die Tiefe richtig festgelegt ist
            
Wenn eine Methode zur Neuprojektion den Tiefenpuffer verwendet, ist es wichtig zu überprüfen, ob der Inhalt des Tiefenpuffers die gerenderte Szene der Anwendung darstellt.  Eine Reihe von Faktoren kann Probleme verursachen. Wenn beispielsweise eine zweite Kamera zum Rendern von Benutzeroberflächenüberlagerungen verwendet wird, überschreibt sie wahrscheinlich alle Tiefeninformationen aus der tatsächlichen Ansicht.  Transparente Objekte legen häufig keine Tiefe fest.  Bei einigen Textrenderings wird die Tiefe standardmäßig nicht festgelegt.  Es gibt sichtbare Störungen beim Rendering, wenn die Tiefe nicht mit den gerenderten Hologrammen übereinstimmt.
            
HoloLens 2 verfügt über eine Schnellansicht, um anzuzeigen, wo tiefe ist und nicht festgelegt wird, die über Geräteportal aktiviert werden kann.  Aktivieren Sie auf der Registerkarte **Ansichten**  >  **Hologrammstabilität** das Kontrollkästchen **Tiefenvisualisierung im Headset anzeigen.**  Bereiche, für die die Tiefe ordnungsgemäß festgelegt ist, sind blau.  Gerenderte Elemente ohne Tiefensatz werden rot markiert und müssen korrigiert werden.  

> [!NOTE]
> Die Visualisierung der Tiefe wird nicht in Mixed Reality-Aufnahme angezeigt.  Sie ist nur über das Gerät sichtbar.
            
Einige GPU-Anzeigetools ermöglichen die Visualisierung des Tiefenpuffers.  Anwendungsentwickler können diese Tools verwenden, um sicherzustellen, dass die Tiefe ordnungsgemäß festgelegt wird.  Informationen zu den Tools der Anwendung finden Sie in der Dokumentation.

### <a name="using-planar-reprojection"></a>Verwenden von Planar Reprojection
> [!NOTE]
> Bei immersiven Desktop-Headsets ist das Festlegen einer Stabilisierungsebene in der Regel kontraproduktiv, da sie weniger visuelle Qualität bietet als die Bereitstellung des Tiefenpuffers Ihrer App für das System, um eine pixelbasierte tiefenbasierte Neuprojektion zu ermöglichen. Wenn Sie nicht auf einer HoloLens ausgeführt werden, sollten Sie im Allgemeinen vermeiden, die Stabilisierungsebene festzulegen.

![Stabilisierungsebene für 3D-Objekte](images/stab-plane-500px.jpg)

Das Gerät versucht automatisch, diese Ebene auszuwählen, aber die Anwendung sollte sie unterstützen, indem sie den Fokuspunkt in der Szene auswählt. Unity-Apps, die auf einer HoloLens ausgeführt werden, sollten basierend auf Ihrer Szene den besten Fokuspunkt auswählen und an [SetFocusPoint()](../unity/focus-point-in-unity.md)übergeben. Ein Beispiel für das Festlegen des Fokuspunkts in DirectX ist in der standardmäßigen rotierenden Cubevorlage enthalten.

Unity sendet Ihren Tiefenpuffer an Windows, um eine Pixel-reprojection zu ermöglichen, wenn Sie Ihre App auf einem immersiven Headset ausführen, das mit einem Desktop-PC verbunden ist, was eine noch bessere Imagequalität ohne explizite Arbeit durch die App bietet. Sie sollten einen Fokuspunkt nur bereitstellen, wenn Ihre App auf einer HoloLens ausgeführt wird oder die Pro-Pixel-Neuprojektion überschrieben wird.


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
* "Fire and Forget" (Löschen und Vergessen) nicht. Sie können die Stabilisierungsebene hinter dem Benutzer oder an ein Objekt anfügen, das sich nicht mehr in der Ansicht des Benutzers befindet. Stellen Sie sicher, dass die Normalität der Stabilisierungsebene gegenüber der Kamera nach vorn festgelegt ist (z. B. -camera.forward).
* Ändern Sie die Stabilisierungsebene nicht schnell zwischen Extreme
* Lassen Sie die Stabilisierungsebene nicht auf einen festen Abstand bzw. eine feste Ausrichtung festgelegt.
* Lassen Sie nicht zu, dass die Stabilisierungsebene den Benutzer durchschneidet.
* Legen Sie den Fokuspunkt nicht fest, wenn Sie auf einem Desktop-PC statt auf einer HoloLens ausgeführt werden, und verwenden Sie stattdessen eine pixelbasierte tiefenbasierte Neuprojektion.

## <a name="color-separation"></a>Farbtrennung 

Aufgrund der Art von HoloLens-Displays kann manchmal ein Artefakt namens "Farbtrennung" erkannt werden. Es wird als Bild angezeigt, das in einzelne Basisfarben unterteilt wird : Rot, Grün und Blau. Das Artefakt kann besonders beim Anzeigen weißer Objekte sichtbar sein, da es große Mengen an Rot, Grün und Blau enthält. Dies ist besonders deutlich, wenn ein Benutzer ein Hologramm visuell verfolgt, das sich mit hoher Geschwindigkeit über den holografischen Rahmen bewegt. Eine andere Möglichkeit, wie sich das Artefakt manifestieren kann, ist das Verzerren/Vertauschen von Objekten. Wenn ein Objekt einen hohen Kontrast und/oder reine Farben wie Rot, Grün, Blau hat, wird die Farbtrennung als Verzerren verschiedener Teile des Objekts wahrgenommen.

**Beispiel dafür, wie die Farbtrennung eines mit dem Kopf gesperrten weißen runden Cursors aussehen könnte, wenn ein Benutzer den Kopf zur Seite dreht:**

![Beispiel dafür, wie die Farbtrennung eines mit dem Kopf gesperrten weißen runden Cursors aussehen könnte, wenn ein Benutzer den Kopf zur Seite drehen würde.](images/colorseparationofroundwhitecursor-300px.png)

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