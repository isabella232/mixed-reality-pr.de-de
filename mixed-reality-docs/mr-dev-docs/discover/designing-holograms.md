---
title: Entwerfen von Hologrammen
description: Erfahren Sie mehr über Mixed Reality durch die neue Anwendung Designing Holograms (Entwerfen von Hologrammen) von Microsoft.
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: MRTK, Mixed Reality Toolkit, Hologramme, Entwerfen von Hologrammen, Lernen, Beispiel-App, Mixed Reality-Headset, Virtual Reality-Headset, Was ist Virtual Reality?
ms.openlocfilehash: 6e37c3f1ba98f202addb9c323632bca8bffae3b6
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143638"
---
# <a name="the-making-of-designing-holograms"></a>Erstellen von Hologrammen

> [!NOTE]
> Lassen Sie ein kleines Ladefenster zu, um alle coolen GIFs und eingebetteten Videos auf dieser Seite zu berücksichtigen.

Das Erlernen des Entwurfs für Mixed Reality kann schwierig sein, da das Medium nicht immer gut in 2D-Entwurfsprozesse übersetzt wird. Hier bei Microsoft haben wir eine kostenlose App für die HoloLens 2 erstellt, mit der Sie die Grundlagen von Mixed Reality UX Design aus erster Hand kennenlernen können. Der einzigartige Ansatz der App Designing Holograms (Entwerfen von Hologrammen) geht auf Mixed Reality-Verhalten, Tipps und Empfehlungen ein, um Ihnen zu helfen, ansprechende und beeindruckende HoloLens-Apps selbst zu erstellen. Laden Sie die App kostenlos von der Microsoft Store herunter, und lernen Sie vom Mixed Reality DesignTeam von Microsoft!

> [!div class="nextstepaction"]
> [Herunterladen der App "Entwerfen von Hologrammen"](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

<br>

![Animiertes GIF der Kopfverfolgungsszene im Demoraum des Entwerfens eines Hologramms](images/designing-holograms/demo-room.gif)

*Entwerfen des Demoraums des Hologramms (auch als "Haus der Brille" bezeichnet)*

## <a name="designing-for-mixed-reality"></a>Entwerfen für Mixed Reality

Wie viele von Ihnen habe ich mobile Apps entwickelt. Aus einer 2D-Entwurfsumgebung zu stammen, war der Einstieg in das räumliche Computing, in dem sich jetzt alles in der Welt befindet, eine bedeutende Verschiebung. In Mixed Reality sind Apps nicht mehr auf einen 2D-Bildschirm beschränkt. Tatsächlich sind sie fast frei, werden in der realen Welt platziert und interagieren mit echten Objekten.

Für mich ist das Verbinden von 3D-Erfahrungen mit herkömmlichen 2D-Entwurfsprozessen der schwierigste Aspekt der Mixed Reality-Entwicklung. In Gesprächen mit Kunden würde ich beispielsweise folgendes hören: "Ich weiß, welche Features einbezogen werden müssen und wie ich sie in Betrieb nehmen kann. Es ist Code, ich kann die Dokumentationen und Tutorials befolgen, aber die Benutzererfahrung? So viele Features, unterschiedliche Eingabeoptionen, verschiedene Szenarien und physische Umgebungen, das ist überwältigend."

![Bild vom HoloLens 2 Design Workshop in San Francisco ](images/designing-holograms/workshop.jpeg)
 *Bild vom HoloLens 2 Design Workshop in San Francisco*

## <a name="an-opportunity-to-teach"></a>Eine Möglichkeit zum Trainieren

Es war zunächst nicht offensichtlich, aber es wurde eine hervorragende Gelegenheit geboten, Mixed Reality als Medium zu verwenden, um es zu trainieren.

Das Entwerfen von Hologrammen ist ein visuelles Erlebnis, das Mixed Reality-Entwurfskonzepte und -empfehlungen erläutert. Es sind nur Sie und eine virtuelle Lehrkraft, die Mixed Reality-Entwurfskonzepte demonstrieren. Alles ist aus der Perspektive einer dritten Person mit der Erfahrung fest in Ihrem eigenen Bereich.

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Designing-Holograms-app-trailer/player]

*Video zum Entwerfen von Hologramm-Trailern*

## <a name="exploring-the-doll-house"></a>Erkunden des Hauses "House"

Das Haus ist die virtuelle Umgebung, die wir in der gesamten App verwenden. Die Umgebung ist ein 80 x 60 x 40 cm großer Raum, der die grundlegenden Elemente enthält, die die meisten Räume gemeinsam haben, wie z. B. Wände, Licht, Gäste, einen Tisch und einen Fernseher. Das Haus ist der Hauptbereich der App-Erfahrung, daher mussten wir sicherstellen, dass es in jeder Umgebung hervorragend funktioniert. Stellen Sie sich dies als kleinen Demoraum für die Visualisierung aller arten von Mixed Reality-Konzepten vor.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Dollhouse-adjustment-behavior-in-the-Designing-Holograms-app/player]
*Video zum Anpassungsverhalten vonHouse*

### <a name="11-vs-110-prototypes"></a>1:1 vs 1:10 Prototypen

Unsere anfängliche Annahme war, dass 1:1-Demonstrationen unglaublich sein würden, fast wie ein Blick auf einen echten Lehrer. Der Benutzer sieht alles, was die Lehrkraft in der Praxis sieht. Wir haben jedoch sofort festgestellt, dass es einige Probleme geben würde:

- Die meisten Entwickler führen ihre Apps in Büros oder in Räumen aus, die kleiner als der Demoraum sind, sodass sie nicht passen.
- Anzeigen sind additiv, d. h., die gesamte virtuelle Umgebung wird über dem Raum eines Benutzers überlagert. Dies kann mit zwei Tabellen verwirrend werden, z. B. doppelten Couchs und Wänden, die nicht ausgerichtet sind.
- Und im schlimmsten Fall ist eine virtuelle Umgebung stark durch ein Sichtfeld eingeschränkt.

Als wir eine Miniskala von 1:10 ausprobiert haben, war das Ergebnis ein ansprechender Blick auf einen realistischen Raum. Sie konnten alles, was gerade passierte, aus einem beliebigen Winkel gleichzeitig sehen. Am überraschendsten war, dass die meisten Tester es so viel immersiver gefunden haben, eine kleine Version zu sehen, als dass sie nie wieder auf die 1:1-Skalierung umgeschaltet wurden. Daher haben wir uns entschieden, die Version 1:1 tatsächlich zu nutzen und die zusätzliche Arbeit zu vermeiden, die erforderlich ist, um die Benutzeroberfläche und andere Aspekte der App anzupassen.

![Ansichtsfeld mit 1:1-Skalierungsfeld ](images/designing-holograms/1-1-scale.png)
 *mit 1:1-Skalierung*

![View Field of View with 1:10 scale ](images/designing-holograms/1-10-scale.png)
 *Field of View with 1:10 scale (Sichtfeld mit 1:10* Skalierung)

## <a name="using-mixed-reality-capture"></a>Verwenden von Mixed Reality-Aufnahme

Eines der typischen Merkmale dieser App ist die Verwendung von Mixed Reality-Aufnahme zum Trainieren und Demonstrieren von Mixed Reality-Entwurfskonzepten.

Microsoft verfügt über ein Mixed Reality-Aufnahme Studio in San Francisco. Microsoft lizenziert diese Technologie auch an andere Studios, z.B. Avatar Dimension in Washington D.C., Metastage in Los Angeles, Dimension Studio in London, SK Telecom in Seattle und Volucap in London. Weitere Informationen zu unseren Mixed Reality-Aufnahme Studio finden Sie [hier.](https://www.microsoft.com/mixed-reality/capture-studios)

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Raw-capture-footage-for-the-Designing-Holograms-app/player]
*Rohmaterial von Daniel Ualdero von einer der 106 Kameras im Mixed Reality-Aufnahme Studio in San Francisco.*

Der Erfassungsprozess generiert ein keyframed-Gittermodell, Normalität und Textur, das als OBJ-/PNG-Dateien für die weitere Postproduktion oder als komprimierte H.264-MP4-Datei zur Wiedergabe bereit sein kann. Diese Dateien können in Unity-, Unreal-, Native- und WebXR-Projekte importiert werden. Dateien können unter Windows, iOS, Mac, Android, Magic Leap und Playstation VR ausgeführt werden.

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Mixed-Reality-Capture-footage-for-the-Designing-Holograms-app/player]
*Der Capture Player zum Analysieren von MP4-Dateien, die Video mit Audio und eingebetteten Gitternetzen enthalten.*

## <a name="manipulating-captures-and-virtual-objects"></a>Bearbeiten von Erfassungen und virtuellen Objekten

Mixed Reality Captures erzeugt virtuelle Darstellungen von Menschen oder Haustieren, aber manchmal benötigen Sie diese Zeichen möglicherweise, um mit anderen virtuellen Objekten zu interagieren. Die folgenden beiden Beispiele zeigen verschiedene Möglichkeiten, wie wir die Szenen bearbeitet haben, um diesen Effekt zu erzielen.

### <a name="head-gaze-adjustment"></a>Anpassung des Anvings mit dem Kopf

Mit der Kopfkopfanpassung können Sie den Kopf einer erfassten Person zur Laufzeit verschieben, was bedeutet, dass Sie ein Erfassungsgesicht für einen Benutzer haben könnten. In unserem Fall haben wir es verwendet, um das Sichtfeld und das feld of interest zu zeigen. Unten sehen Sie ein sich bewegendes Spielobjekt, das als Ziel für den Anvschauungs-Blick mit dem Kopf verwendet wird. Wenn wir das Ziel von Seite zu Seite verschieben, folgt der Kopf der Erfassung.

Wir haben diesen Trick verwendet, um sicherzustellen, dass die Aufnahme im Leerlauf immer hologrammen gegenüberstehen würde, die in verschiedenen Teilen des Haus platziert wurden. 

![Der Kopf des Capture-Objekts wird zur Laufzeit nach einem Zielspielobjekt in Unity verschoben.](images/designing-holograms/head-adjustment.gif)

*Der Kopf des Capture-Objekts wird zur Laufzeit nach einem Zielspielobjekt in Unity verschoben.*

### <a name="syncing-animated-objects"></a>Synchronisieren von animierten Objekten

Das zweite war das Animieren von Objekten zur Synchronisierung mit der Bewegung einer Erfassung. In verschiedenen Teilen der App haben wir sequenzielle OBJs einer bestimmten Erfassung alle fünf Frames importiert. Die OBJs wurden dann in der Szene animiert, um sicherzustellen, dass sie mit dem entsprechenden Frame der Aufnahme übereinstimmen. Es ist ein mühsamer Prozess der Animation und Schlüsselinfrastruktur, aber das Ergebnis ist sehr gut. Sie können nun sehen, Mixed Reality-Aufnahme mit nicht erfassten Objekten interagiert.

![Synchronisierte Animation zwischen einem Mixed Reality-Aufnahme und einem Benutzeroberflächenbereich](images/designing-holograms/synced-objects.gif)

*Synchronisierte Animation zwischen einem Mixed Reality-Aufnahme und einem Benutzeroberflächenbereich*

### <a name="ui-creative-process"></a>Kreativer Prozess der Benutzeroberfläche

Als wir mit dem Entwurf der Benutzeroberfläche begonnen haben, wollten wir einige der Magischen und Möglichkeiten zeigen, die Hologramme zu bieten haben. Das einfache Anzeigen statischer 2D-Fenster und Textfelder ist in der 3D-Welt nicht das richtige. Viele der möglichkeiten zur Hand werden einfach nicht angezeigt. Daher haben wir uns von Anfang an entschieden, davon abzugehen und den holografischen 3D-Raum voll zu nutzen.

Zunächst haben wir mit dem Hinzufügen einiger Stärke zu den Panels, Symbolen und Textinformationen begonnen. Als Benutzer wird jedoch ein Textfeld angezeigt. Textfelder mit Bildern, aber nicht vorhanden. Wir haben die Mixed Reality Toolkit-Shader (MRTK) verwendet. Die MRTK-Shader wurden zu einem leistungsstarken Tool, und wir haben die Schablonenfeatures genutzt, um den Panels negative Tiefe hinzuzufügen. Das bedeutet, dass die Symbole jetzt hinter einem transparenten Bereich angezeigt werden, anstatt Elemente vor einem Textfeld hinzuzufügen. Was ich jetzt als Benutzer sehe, ist etwas, das ich in der realen Welt einfach nicht mehr replizieren kann, und an dieser Stelle hat holografische Magic begonnen. Auch als Benutzer, den ich nicht wirklich lesen möchte, tue ich bereits viel in der physischen Welt.

Symbole funktionieren natürlich viel besser als einfacher Text. Um eine noch leistungsfähigere Anleitung bereitzustellen, habe ich dann damit begonnen, eine Reihe von animierten Objekten und Avataren zu erstellen, von denen jeder eine kleine Geschichte darüber erzählen, was im jeweiligen Szenario geschieht und wie es verwendet wird.

![Animiertes GIF eines interaktiven holografischen Menüsystems](images/designing-holograms/creative-process.gif)

## <a name="core-concepts"></a>Kernkonzepte

**Head Tracking und Eye Tracking**

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

**Handtracking**

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Hand-Tracking-Chapter/player]

**Räumliche Wahrnehmung**

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

**Holografischer Rahmen**

![Animierte GIF-Datei eines Benutzers, der sich mit hervorgehobener holografischem Rahmen um das Reihenhäuschen kümmert](images/designing-holograms/FOVandFOI.gif)

**Koordinatensysteme**

![Animierte GIF-Datei eines Benutzers, der sich mit den hervorgehobenen Koordinatensystemen um das Haus herumschaut](images/designing-holograms/CoordinateSystems.gif)

**Eyetracking – Blickverfolgung**

![Animierte GIF-Datei eines Benutzers, der mit hervorgehobener Strahlaufnahme des Anvierens mit den Augen stationäre Hologramme ansieht](images/designing-holograms/EyeTracking.gif)

**Raumscanvisualisierung und räumliche Zuordnung**

![Animiertes GIF aller Oberflächen innerhalb des zuzuordnenden Doppelhäuschens](images/designing-holograms/SpatialMapping.gif)

**Grundlegendes zu Szenen**

![Animiertes GIF von Objekten im Doppelhaus, das erkannt wird](images/designing-holograms/SceneUnderstanding.gif)

**Zeigen und Committen mit Handstrahl**

![Animiertes GIF eines Benutzers, der seine Hand mit einem hervorgehobenen Handstrahl hebt](images/designing-holograms/HandRays.gif)

## <a name="try-it-out-moments"></a>"Try it out" (Ausprobieren)

Das Entwerfen von Hologrammen vermittelt Mixed Reality-Konzepte, ermöglicht ihnen aber auch, sie in Ihrem Raum auszuprobieren. Nach einigen dieser Erklärungen halten wir an, und nehmen Sie aus dem Haus des Schlosses in einen interaktiven Moment. Im Folgenden finden Sie einige Beispiele für diese interaktiven Augenblicke:

![Animiertes GIF des Handtrackingframes, das anzeigt, wann Hände erkannt werden und wann sie in das Sichtfeld gelangen](images/designing-holograms/try-out-1.gif)

*Der Handtrackingrahmen, der anzeigt, wann Hände erkannt werden und wann sie in das Sichtfeld gelangen.*

![Animiertes GIF der Interaktion mit kollidierenden Steine durch fernen Interaktion](images/designing-holograms/try-out-2.gif)

*Interaktion mit kollidierenden Steine durch weit entfernte Interaktion*

![Animierte GIF-Datei zum Untersuchen von Umgebungsinteraktions-Affordances](images/designing-holograms/try-out-3.gif)

*Untersuchen von Nahezu-Interaktionsentitäten*

## <a name="about-the-team"></a>Informationen zum Team

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Daniel Escudero" width="60" height="60" src="images/designing-holograms/daniel-escudero.jpeg"></td>
<td style="border-style: none"><b>Daniel Osodero</b><br><i>Leitender technischer Designer</i><br>Dan ist Creative Director für das Entwerfen von Hologrammen und arbeitet derzeit als Designleiter für die Mixed Reality Academy von Microsoft in San Francisco und war zuvor Designer in einer der Mixed Reality Studios von Microsoft in London.</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Martin Wettig" width="60" height="60" src="images/designing-holograms/martin-wettig.jpeg"></td>
<td style="border-style: none"><b>MartinUngig</b><br><i>Senior 3D-Interpret</i><br>Martin leitet 3D-Grafik und UI-Design beim Entwerfen von Hologrammen und war zuvor Senior 3D-Interpret in einer der Mixed Reality Studio von Microsoft in Konzeption.</td>
</tr>
</table>

Ein großer Dank gilt dem Mixed Reality-Entwurfsteam, dass es so viel Wissen geteilt hat, und den beeindruckenden Mitarbeitern der [Objekttheorie,](https://objecttheory.com/) die in jedem Schritt des Projekts wichtige Teampartner sind. Vielen Dank für Ihren großartigen Talent, für Ihre Leidenschaft und ihren besonderen Blick für das Design.

> [!div class="nextstepaction"]
> [Herunterladen der App "Entwerfen von Hologrammen"](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)