---
title: Entwerfen von Hologrammen
description: Erfahren Sie Mixed Reality der neuen Designing Hologramme-Anwendung von Microsoft.
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: MRTK, Mixed Reality Toolkit, Hologramme, Entwerfen Hologramme, Lernen, Beispiel-App, Mixed Reality-Headset, Virtual Reality-Headset, Was ist virtual reality?
ms.openlocfilehash: fb60dabcd03d276a7d901ee5b2f061460fbfa05acfbdf226a8aee9325f160cff
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192410"
---
# <a name="the-making-of-designing-holograms"></a>Die Erstellung von Entwerfen Hologramme

> [!NOTE]
> Lassen Sie ein kleines Ladefenster zu, um alle coolen GIFs und eingebetteten Videos auf dieser Seite zu berücksichtigen.

Learning der Entwurf für Mixed Reality kann schwierig sein, da das Medium nicht immer gut in 2D-Entwurfsprozesse übersetzt wird. Hier bei Microsoft haben wir eine kostenlose App für die HoloLens 2 erstellt, mit der Sie die Grundlagen von Mixed Reality UX Design aus erster Hand erlernen können. Der einzigartige Ansatz der Designing Hologramme-App geht auf Mixed Reality-Verhalten, Tipps und Empfehlungen ein, um Sie dabei zu unterstützen, ansprechende und beeindruckende HoloLens eigenen Apps zu erstellen. Laden Sie die App kostenlos von der Microsoft Store herunter, und lernen Sie vom Mixed Reality Design-Team von Microsoft!

> [!div class="nextstepaction"]
> [Herunterladen der Designing Hologramme-App](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

<br>

![Animiertes GIF der Kopfverfolgungsszene im Demoraum des Designing Hologram](images/designing-holograms/demo-room.gif)

*Entwerfen des Demoraums des Hologramms (auch bekannt als "House"))*

## <a name="designing-for-mixed-reality"></a>Entwerfen für Mixed Reality

Wie viele von Ihnen habe ich mobile Apps bereits entwerfen können. Aus einer 2D-Designwelt zu kommen, war der Sprung ins Ganze auf dem Räumlichen Computing, wo sich alles jetzt auf der Welt befindet, eine erhebliche Verschiebung. In Mixed Reality sind Apps nicht mehr auf einen 2D-Bildschirm beschränkt. tatsächlich sind sie fast kostenlos, werden in der realen Welt platziert und interagieren mit echten Objekten.

Für mich ist das Verbinden von 3D-Erfahrungen mit herkömmlichen 2D-Entwurfsprozessen der anspruchsvollste Aspekt der Mixed Reality-Entwicklung. In Unterhaltungen mit Kunden würde ich z. B. folgendes hören: "Ich weiß, welche Features enthalten sein müssen und wie ich sie in Betrieb nehmen kann. Es ist Code, ich kann die Dokumente und Tutorials befolgen, aber die Benutzererfahrung? So viele Features, unterschiedliche Eingabeoptionen, verschiedene Szenarien und physische Umgebungen, es ist überfordernd."

![Bild aus dem HoloLens 2 Design Workshop in San Francisco ](images/designing-holograms/workshop.jpeg)
 *Image aus dem HoloLens 2 Design Workshop in San Francisco*

## <a name="an-opportunity-to-teach"></a>Eine Gelegenheit zum Vermitteln

Es war zunächst nicht offensichtlich, aber es wurde eine hervorragende Gelegenheit gegeben, Mixed Reality als Medium zu verwenden, um es zu vermitteln.

Entwerfen Hologramme ist eine visuelle Erfahrung, die Mixed Reality-Entwurfskonzepte und -empfehlungen erläutert. Es sind nur Sie und eine virtuelle Lehrkraft, die Mixed Reality-Entwurfskonzepte demonstriert. Alles ist aus Sicht einer dritten Person mit der Erfahrung in Ihrem eigenen Bereich.

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Designing-Holograms-app-trailer/player]

*Entwerfen Hologramme Trailervideos*

## <a name="exploring-the-doll-house"></a>Erkunden des Hauses

Das Haus ist die virtuelle Umgebung, die wir in der gesamten App verwenden. Die Umgebung ist ein 80 x 60 x 40 cm großes Zimmer, das die grundlegenden Elemente enthält, die die meisten Räume gemeinsam haben, z. B. Wände, Tafeln, Tisch und TV. Das Haus ist das Wichtigste der App-Erfahrung, daher mussten wir sicherstellen, dass es in jeder Umgebung gut funktioniert. Stellen Sie sich dies als kleinen Demoraum zum Visualisieren aller Arten von Mixed Reality-Konzepten vor.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Dollhouse-adjustment-behavior-in-the-Designing-Holograms-app/player]
*Video des Anpassungsverhaltens von "House"*

### <a name="11-vs-110-prototypes"></a>1:1 im Vergleich zu 1:10 Prototypen

Unsere anfängliche Annahme war, dass 1:1-Demonstrationen überraschend wären, fast wie ein realer Lehrer. Der Benutzer sieht alles, was die Lehrkraft im realen Leben sieht. Wir haben jedoch sofort festgestellt, dass es einige Probleme geben würde:

- Die meisten Entwickler führen ihre Apps in Büros oder Räumen aus, die kleiner als der Demoraum sind, sodass sie nicht passen würden.
- Anzeigen sind additiv, was bedeutet, dass die gesamte virtuelle Umgebung über dem Raum eines Benutzers überlagert wird. Dies kann bei zwei Tabellen verwirrend sein, z. B. doppelten Couchs und nicht ausgerichteten Wänden.
- Und am schlechtesten ist eine virtuelle Umgebung, die stark durch ein Sichtfeld eingeschränkt ist.

Als wir eine mini 1:10-Skala ausprobiert haben, war das Ergebnis eine hervorragende Sicht auf einen realistischen Raum. Sie können alles sehen, was aus jedem Winkel zur gleichen Zeit vor sich geht. Was am überraschendsten war, ist, dass die meisten Tester es so viel immersiver finden, um eine kleine Version zu sehen, dann haben sie nie zur 1:1-Skala zurückschaltet. Daher haben wir uns entschieden, die 1:1-Version tatsächlich zu nutzen und den zusätzlichen Arbeitsaufwand zu vermeiden, der erforderlich ist, um die Benutzeroberfläche und andere Aspekte der App anzupassen.

![Sichtfeld mit 1:1-SkalaAnsichtsfeld ](images/designing-holograms/1-1-scale.png)
 *mit 1:1-Skala*

![Sichtfeld mit einer Skala von 1:10, ](images/designing-holograms/1-10-scale.png)
 *Sichtfeld mit einer Skala von 1:10*

## <a name="using-mixed-reality-capture"></a>Verwenden Mixed Reality-Aufnahme

Eines der wichtigsten Features dieser App ist die Verwendung von Mixed Reality-Aufnahme, um Mixed Reality-Entwurfskonzepte zu vermitteln und zu demonstrieren.

Microsoft verfügt über Mixed Reality-Aufnahme Studio in San Francisco. Microsoft lizenziert diese Technologie auch an andere Studiostudios, darunter Avatar Dimension in Washington D.C., Metastage in Los Angeles, Dimension Studio in London, SK Telecom in Tokio und Volucap in Tokio. Weitere Informationen zu unseren Mixed Reality-Aufnahme [Studio finden Sie hier.](https://www.microsoft.com/mixed-reality/capture-studios)

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Raw-capture-footage-for-the-Designing-Holograms-app/player]
*Rohmaterial von Daniel Pherdero von einer der 106 Kameras im Mixed Reality-Aufnahme Studio in San Francisco.*

Der Erfassungsprozess generiert ein keyframed mesh, normals und texture, das als OBJ/PNG-Dateien für die weitere Postproduktion oder für die Wiedergabe als komprimierte H.264-MP4-Datei bereitgestellt werden kann. Diese Dateien können in Unity-, Unreal-, Native- und WebXR-Projekte importiert werden. Dateien können auf Windows, iOS, Mac, Android, Magic Leap und Playstation VR ausgeführt werden.

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Mixed-Reality-Capture-footage-for-the-Designing-Holograms-app/player]
*Der capture-Player, der zum Analysieren von MP4-Dateien bereitgestellt wird, die Videos mit Audiodaten und eingebetteten Gittern enthalten.*

## <a name="manipulating-captures-and-virtual-objects"></a>Bearbeiten von Erfassungen und virtuellen Objekten

Mixed Reality Captures erzeugen virtuelle Darstellungen von Personen oder Haustieren, aber manchmal benötigen Sie diese Zeichen möglicherweise, um mit anderen virtuellen Objekten zu interagieren. Die folgenden beiden Beispiele zeigen verschiedene Möglichkeiten, wie wir die Szenen bearbeitet haben, um diesen Effekt zu erzielen.

### <a name="head-gaze-adjustment"></a>Anpassung des Anvings mit dem Kopf

Mit der Kopfkopfanpassung können Sie den Kopf einer erfassten Person zur Laufzeit verschieben, was bedeutet, dass Sie ein Erfassungsgesicht für einen Benutzer haben könnten. In unserem Fall haben wir es verwendet, um das Sichtfeld und das feld of interest zu zeigen. Unten sehen Sie ein bewegendes Spielobjekt, das als Ziel für den Anvschauungs-Blick mit dem Kopf verwendet wird. Wenn wir das Ziel von Seite zu Seite verschieben, folgt der Kopf der Erfassung.

Wir haben diesen Trick verwendet, um sicherzustellen, dass die Aufnahme im Leerlauf immer hologrammen gegenüberstehen würde, die in verschiedenen Teilen des Haus platziert wurden. 

![Der Kopf des Capture-Objekts wird zur Laufzeit nach einem Zielspielobjekt in Unity verschoben.](images/designing-holograms/head-adjustment.gif)

*Der Kopf des Capture-Objekts wird zur Laufzeit nach einem Zielspielobjekt in Unity verschoben.*

### <a name="syncing-animated-objects"></a>Synchronisieren von animierten Objekten

Das zweite war das Animieren von Objekten zur Synchronisierung mit der Bewegung einer Erfassung. In verschiedenen Teilen der App haben wir sequenzielle OBJs einer bestimmten Erfassung alle fünf Frames importiert. Die OBJs wurden dann in der Szene animiert, um sicherzustellen, dass sie mit dem entsprechenden Frame der Aufnahme übereinstimmen. Es ist ein mühsamer Prozess der Animation und Schlüsselinfrastruktur, aber das Ergebnis ist sehr gut. Sie können nun sehen, Mixed Reality-Aufnahme mit nicht erfassten Objekten interagiert.

![Synchronisierte Animation zwischen einem Mixed Reality-Aufnahme und dem Benutzeroberflächenbereich](images/designing-holograms/synced-objects.gif)

*Synchronisierte Animation zwischen einem Mixed Reality-Aufnahme und dem Benutzeroberflächenbereich*

### <a name="ui-creative-process"></a>Kreativer Prozess der Benutzeroberfläche

Als wir mit dem Entwurf der Benutzeroberfläche begonnen haben, wollten wir einige der Magischen und Möglichkeiten zeigen, die Hologramme zu bieten haben. Das einfache Anzeigen statischer 2D-Fenster und Textfelder ist in der 3D-Welt nicht das richtige. Viele der möglichkeiten, die zur Hand sind, werden einfach nicht gezeigt. Daher haben wir uns von Anfang an entschieden, davon weg zu wechseln und den holografischen 3D-Raum vollständig zu nutzen.

Zunächst haben wir damit begonnen, den Panels, Symbolen und Textinformationen eine gewisse Stärke zu geben. Als Benutzer wird jedoch ein Textfeld angezeigt. Textfelder mit Bildern, aber wir sind nicht dort. Wir haben die Shader des Mixed Reality Toolkits (MRTK) weiter verwendet. Die MRTK-Shader wurden zu einem leistungsstarken Tool, und wir haben seine Schablonenfeatures verwendet, um den Panels negative Tiefe hinzuzufügen. Das bedeutet, dass die Symbole jetzt hinter einem transparenten Bereich angezeigt werden, anstatt Elemente vor einem Textfeld hinzufügen zu müssen. Was ich jetzt als Benutzer sehe, ist etwas, das ich in der realen Welt einfach nicht mehr replizieren kann, und an diesem Ort begann holografische Magic. Auch als Benutzer, den ich nicht wirklich lese, kann ich bereits viel in der physischen Welt tun.

Natürlich funktionieren Symbole viel besser als einfacher Text. Um eine noch leistungsfähigere Anleitung zu bieten, habe ich dann damit begonnen, eine Reihe von animierten Objekten und Avataren zu erstellen, die jeweils eine kleine Geschichte darüber erzählen, was im jeweiligen Szenario geschieht und wie sie verwendet werden.

![Animiertes GIF eines interaktiven holografischen Menüsystems](images/designing-holograms/creative-process.gif)

## <a name="core-concepts"></a>Kernkonzepte

**Kopf- und Blickverfolgung**

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

**Hand-Tracking**

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Hand-Tracking-Chapter/player]

**Räumliche Wahrnehmung**

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

**Holografischer Rahmen**

![Animiertes GIF eines Benutzers, der sich im Lagerhäuschen mit hervorgehobener Holografie](images/designing-holograms/FOVandFOI.gif)

**Koordinatensysteme**

![Animiertes GIF eines Benutzers, der das Lager mit hervorgehobenen Koordinatensystemen durch das Lager sucht](images/designing-holograms/CoordinateSystems.gif)

**Eyetracking – Blickverfolgung**

![Animiertes GIF eines Benutzers, der sich stationäre Hologramme anschaut, bei der der Blickstrahl mit den Augen hervorgehoben ist](images/designing-holograms/EyeTracking.gif)

**Raumscanvisualisierung und räumliche Zuordnung**

![Animiertes GIF aller Oberflächen innerhalb des Lagers, das zugeordnet wird](images/designing-holograms/SpatialMapping.gif)

**Grundlegendes zu Szenen**

![Animiertes GIF von Objekten im Lagerhaus, die erkannt werden](images/designing-holograms/SceneUnderstanding.gif)

**Zeigen und Commit mit Handlichtstrahl**

![Animiertes GIF eines Benutzers mit hervorgehobener Handstrahl](images/designing-holograms/HandRays.gif)

## <a name="try-it-out-moments"></a>Moment "Ausprobieren"

Das entwerfen Hologramme vermittelt Mixed Reality-Konzepte, ermöglicht ihnen aber auch, sie in Ihrem Raum auszuprobieren. Nach einigen dieser Erklärungen halten wir an und nehmen Sie aus dem Haus und in einen interaktiven Moment. Im Folgenden finden Sie einige Beispiele für diese interaktiven Augenblicke:

![Animiertes GIF des Handtrackingrahmens, der zeigt, wann Hände erkannt werden und wann sie in das Sichtfeld gelangen](images/designing-holograms/try-out-1.gif)

*Der Handverfolgungsrahmen, der angibt, wann Hände erkannt werden und wann sie in das Sichtfeld gelangen.*

![Animiertes GIF der Interaktion mit kollidiertenDekollangen durch Ferninteraktion](images/designing-holograms/try-out-2.gif)

*Interagieren mit kollidiertenDekollangen durch fernen Interaktion*

![Animierte GIF-Datei zur Untersuchung von Nahezu-Interaktions-Bezahlbarkeiten](images/designing-holograms/try-out-3.gif)

*Untersuchen von Nahezu-Interaktions-Affordances*

## <a name="about-the-team"></a>Informationen zum Team

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Daniel Escudero" width="60" height="60" src="images/designing-holograms/daniel-escudero.jpeg"></td>
<td style="border-style: none"><b>Daniel Pherdero</b><br><i>Lead Technical Designer</i><br>Dan ist creative Director für Designing Hologramme und arbeitet derzeit als Designleiter für die Mixed Reality Academy von Microsoft in San Francisco und war zuvor Designer in einem der Mixed Reality Studio von Microsoft in London.</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Martin Wettig" width="60" height="60" src="images/designing-holograms/martin-wettig.jpeg"></td>
<td style="border-style: none"><b>MartinGsig</b><br><i>Senior 3D Interpret</i><br>Martin leitet 3D Art and UI Design bei Designing Hologramme und war zuvor Senior 3D Interpret in einem der Mixed Reality Studio von Microsoft in Deutschland.</td>
</tr>
</table>

Ein großer Dank an das Mixed Reality Design Team, dass es so viel Wissen geteilt hat, und an die beeindruckenden Mitarbeiter bei [Object Theory,](https://objecttheory.com/) die in jedem Schritt des Projekts wichtige Teamkollegen sind. Vielen Dank für Ihren großartigen Talent, für Ihre Leidenschaft und ihren besonderen Blick für das Design.

> [!div class="nextstepaction"]
> [Herunterladen der Designing Hologramme-App](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)