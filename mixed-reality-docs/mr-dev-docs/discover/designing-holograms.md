---
title: Entwerfen von holograms
description: Erfahren Sie mehr über die gemischte Realität durch die neue Anwendung zum Entwickeln von holograms von Microsoft.
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: Mrtk, Mixed Reality Toolkit, holograms, Entwerfen von holograms, erlernen, Beispiel-APP, Mixed Reality-Headset, Virtual Reality-Headset, was ist Virtual Reality?
ms.openlocfilehash: 243b6f28da7b074b3ff6d48794d525ac08281fa7
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96355337"
---
# <a name="the-making-of-designing-holograms"></a>Das Entwerfen von holograms

> [!NOTE]
> Gestatten Sie einem kleinen lade Fenster, alle coolen GIFs und eingebetteten Videos auf dieser Seite zu berücksichtigen.

Das Erlernen des Entwurfs für gemischte Realität kann schwierig sein, insbesondere in Bezug darauf, wie visuell das Mittel ist, was sich nicht immer gut in 2D-Entwurfs Prozesse übersetzt. Wir haben hier bei Microsoft eine kostenlose App erstellt, die Sie für die hololens 2 herunterladen können. Sie hilft Ihnen, die Grundlagen von Mixed Reality UX zu erlernen, indem wir Sie in erster Hand sehen. Der einzigartige Ansatz der APP zum Entwerfen von holograms ist in gemischtes Realitäts Verhalten, Tipps und Empfehlungen integriert, um Ihnen die Erstellung ansprechender und verblüffender hololens-apps zu erleichtern. Laden Sie die App kostenlos von der Microsoft Store herunter, und lernen Sie von dem Mixed Reality-Design Team von Microsoft.

> [!div class="nextstepaction"]
> [Herunterladen der APP zum Entwerfen von holograms](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

<br>

![Animiertes GIF der Head Tracking-Szene im Demoraum des Entwurfs holograms](images/designing-holograms/demo-room.gif)

*Entwerfen von Hologram als Demoraum (auch als "Puppenhaus" bezeichnet)*

## <a name="designing-for-mixed-reality"></a>Entwerfen für gemischte Realität

Wie viele von Ihnen habe ich zum Entwerfen mobiler Apps verwendet. Aus einer 2D-Entwurfs Welt, die sich vollständig bei räumlichen Computing, wo alles heute auf der Welt ist, befindet, war es eine bedeutende Umstellung. In gemischter Realität sind apps nicht mehr auf einen 2D-Bildschirm beschränkt. Tatsächlich sind Sie fast kostenlos, werden in der realen Welt platziert und interagieren mit echten Objekten.

Für mich ist das Verbinden von 3D-Erfahrungen mit konventionellen 2D-Entwurfs Prozessen der anspruchsvollste Aspekt der Mixed Reality-Entwicklung. In Konversationen mit Kunden würde ich Folgendes hören: "Ich weiß, welche Features eingeschlossen werden müssen und wie Sie Sie einrichten und ausführen. Es handelt sich um Code, ich kann die Dokumentation und Lernprogramme, aber die Benutzer Darstellung befolgen? Viele Features, verschiedene Eingabeoptionen, verschiedene Szenarien und physische Umgebungen sind überwältigend.

![Bild aus dem Design Workshop hololens 2 im San Francisco- ](images/designing-holograms/workshop.jpeg)
 *Image aus dem hololens 2-Entwurfs Workshop in San Francisco*

## <a name="an-opportunity-to-teach"></a>Eine Gelegenheit zum vermitteln

Zuerst war es nicht offensichtlich, aber es wurde eine hervorragende Gelegenheit geboten, gemischte Realität als Mittel zu verwenden, um es zu vermitteln.

Das Entwerfen von holograms ist eine visuelle Darstellung, in der gemischte Entwurfskonzepte und-Empfehlungen erläutert werden. Es handelt sich lediglich um einen virtuellen Lehrer, der gemischte Realitäts Entwurfskonzepte demonstriert. Alles ist von einer dritten Person, die die benutzerfreundliche Darstellung in Ihrem eigenen Bereich hat.

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Designing-Holograms-app-trailer/player]

*Entwerfen von holograms-Nachspann Videos*

## <a name="exploring-the-doll-house"></a>Erkunden des Puppenhauses

Das Puppenhaus ist die virtuelle Umgebung, die wir in der App verwenden, einem 80 x 60 x 40-cm-Miniatur Raum, der die grundlegenden Elemente enthält, die die meisten Räume gemeinsam haben, wie z. b. Wände, Lampen, Möbel, eine Tabelle und ein TV. Das Puppenhaus ist der Hauptprotagonist der APP-Umgebung, daher mussten wir sicherstellen, dass es in jeder Umgebung gut funktioniert. Sehen Sie sich dies als kleinen Demo Raum an, in dem Sie alle Arten gemischter Realitäts Konzepte visualisieren.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Dollhouse-adjustment-behavior-in-the-Designing-Holograms-app/player]
*Video zum Anpassungs Verhalten von Dollhouse*

### <a name="11-vs-110-prototypes"></a>1:1 vs 1:10-Prototypen

Unsere anfängliche Annahme war, dass 1:1 Demonstrationen erstaunlich waren, fast wie man sich einen echten Lehrer ansieht. Dem Benutzer werden alle Elemente angezeigt, die der Lehrer in einer realen lebensskala sieht. Wir haben jedoch sofort erkannt, dass es einige Probleme gibt:

- Die meisten Entwickler führen Ihre apps in Büros oder Räumen aus, die kleiner sind als der Demoraum, sodass es nicht passt.
- Anzeigen sind additiv, was bedeutet, dass die gesamte virtuelle Umgebung über dem Raum eines Benutzers überlagert wird. Dies kann mit zwei Tabellen verwirrend werden, möglicherweise mit doppelten Couches und Wänden, die nicht ausgerichtet sind.
- Und das schlechteste aus einer virtuellen Umgebung, die stark durch ein Sichtfeld eingeschränkt ist.

Als wir eine Mini-1:10-Skalierung ausprobiert haben, war das Ergebnis eine fantastische Vogelperspektive in einem realistischen Raum, in dem Sie alle Elemente sehen konnten, die von einem beliebigen Winkel und alle gleichzeitig durchgeführt wurden. Was am offensichtlichsten war, ist, dass die meisten Tester es so viel mehr einsehen, dass Sie eine kleine Version sehen konnten, und dann nie wieder zur 1:1-Skala gewechselt. Wir haben uns entschieden, die Version 1:1 zu bereinigen und die zusätzliche Arbeit zu vermeiden, die zum Anpassen der Benutzeroberfläche und anderer Aspekte der APP erforderlich ist.

![Sichtfeld mit 1:1-Skalierungs ](images/designing-holograms/1-1-scale.png)
 *Feld Ansicht mit 1:1-Skala*

![Sichtfeld mit 1:10-Skalierungs ](images/designing-holograms/1-10-scale.png)
 *Feld Ansicht mit 1:10-Skala*

## <a name="using-mixed-reality-capture"></a>Verwenden der Mixed Reality-Erfassung

Eines der charakterischsten Features dieser APP ist die Verwendung der gemischten Reality-Erfassung, um gemischte Entwurfskonzepte für die Realität zu vermitteln und zu veranschaulichen.

Microsoft verfügt über eine Mixed Reality Capture Studio in San Francisco. Microsoft lizenziert diese Technologie auch an andere Studio, die eine Avatar-Dimension in Washington D.C., metastage in Los Angeles, Dimensions-Studios in London, SK Telecom in Seoul und volucap in Berlin enthalten. Weitere Informationen zu unseren [Mixed Reality Capture-Studios](https://www.microsoft.com/mixed-reality/capture-studios)finden Sie hier.

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Raw-capture-footage-for-the-Designing-Holograms-app/player]
*Unformatierte Text Aufnahmen von Daniel Escudero von einer der 106-Kameras im Mixed Reality Capture Studio in San Francisco.*

Der Erfassungsprozess generiert ein keyframed Mesh, Normals und eine Textur, die als obj/PNG-Dateien zur weiteren Nachbereitung bereitgestellt werden können, oder zur Wiedergabe als H. 264-komprimierte MP4-Datei. Diese Dateien können in Unity, Unreal, Native und webxr importiert und unter Windows, Ios, Mac, Android, Magic Leap und Play Play (VR) ausgeführt werden.

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Mixed-Reality-Capture-footage-for-the-Designing-Holograms-app/player]
*Der Erfassungs Player, der zum Analysieren von MP4 Bitrate bereitgestellt wird, die Videos mit Audiodaten und eingebetteten Meshes enthalten*

## <a name="manipulating-captures-and-virtual-objects"></a>Bearbeiten von Erfassungen und virtuellen Objekten

Gemischte Reality-Erfassungen führen zu virtuellen Darstellungen von Personen oder Tieren. Manchmal benötigen Sie diese Zeichen jedoch möglicherweise, um mit anderen virtuellen Objekten zu interagieren. In den folgenden beiden Beispielen werden verschiedene Möglichkeiten veranschaulicht, wie die Kulissen bearbeitet wurden, um diesen Effekt zu erzielen.

### <a name="head-gaze-adjustment"></a>Anpassung des Head-Blicks

Mit der Überschrift Anpassung können Sie den Kopf einer erfassten Person zur Laufzeit verschieben, was bedeutet, dass Sie ein Erfassungs Gesicht für einen Benutzer haben könnten. In unserem Fall haben wir Sie verwendet, um das Feld für die Ansicht und das gewünschte Feld anzuzeigen. Im folgenden sehen Sie ein bewegliches gameobject, das als Ziel für den Haupt Blick fungiert. Wenn das Ziel von Seite zu Seite verschoben wird, wird der Anfang der Erfassung befolgt.

Wir haben diesen Trick verwendet, um sicherzustellen, dass die im Leerlauf befindliche Erfassung stets mit holograms in unterschiedlichen Teilen des Puppenhauses konfrontiert wird. 

![Der Kopf der Erfassung, der zur Laufzeit nach einem Ziel-gameobject in Unity verschoben wird](images/designing-holograms/head-adjustment.gif)

*Der Kopf der Erfassung, der zur Laufzeit nach einem Ziel-gameobject in Unity verschoben wird.*

### <a name="syncing-animated-objects"></a>Synchronisieren von animierten Objekten

Die zweite war das Animieren von Objekten, die mit einer Erfassungs Bewegung synchronisiert werden sollen. In unterschiedlichen Teilen der APP haben wir alle fünf Frames das sequenzielle OBJS einer bestimmten Erfassung importiert. Die OBJS wurde dann in der Szene animiert, um sicherzustellen, dass Sie mit dem entsprechenden Frame der Erfassung übereinstimmen. Es ist ein mühsamer Prozess der Animation und der Keyframes, aber das Ergebnis ist hervorragend, Sie können nun eine gemischte Reality-Erfassung sehen, die mit nicht erfassten Objekten interagiert.

![Synchronisierungs Animation zwischen einem gemischten Reality-Erfassungs-und UI-Panel](images/designing-holograms/synced-objects.gif)

*Synchronisierungs Animation zwischen einem gemischten Reality-Erfassungs-und UI-Panel*

### <a name="ui-creative-process"></a>Kreativer UI-Prozess

Als wir mit der ideierung des UI-Entwurfs begonnen haben, wollten wir neben dem Transport von Informationen auch einige der magischen und Möglichkeiten zeigen, die holograms anbieten müssen. Die einfache Anzeige statischer 2D-Fenster und Textfelder ist in der 3D-Welt nicht gleich, und es werden nicht viele der Möglichkeiten angezeigt. Wir haben uns also von Anfang an entschieden, von diesem Weg zu kommen und den Holographic 3D-Raum vollständig zu nutzen.

Zunächst haben wir begonnen, den Bereichen und Symbolen zusätzlich zu den Textinformationen eine gewisse Stärke hinzuzufügen. Als Benutzer sehen Sie das Textfeld. Text Felder mit Bildern, aber wir sind nicht vorhanden. Wir haben mit den Shader von Mixed Reality Toolkit (mrtk) fortgefahren. Die mrtk-Shader wurden zu einem leistungsfähigen Tool, und wir haben die Schablonen Features genutzt, von denen einige möglicherweise als Portal Effekt bekannt sind, um den Bereichen negative Tiefe hinzuzufügen. Das heißt, anstatt Elemente vor einem Textfeld hinzuzufügen, werden die Symbole jetzt hinter einem transparenten Panel angezeigt. Ich sehe jetzt als Benutzer etwas, das ich einfach nicht mehr in der realen Welt replizieren kann. an dieser Stelle begann Holographic Magic. Auch als Benutzer, den ich nicht möchte, mache ich das noch viel in der physischen Welt.

Natürlich funktionieren Symbole viel besser als der einfache Text. um eine noch leistungsfähigere Anleitung bereitzustellen, habe ich dann mit dem Erstellen eines Satzes von animierten Objekten und Avatars begonnen, von denen jeder eine kleine Story darüber erzählt, was im jeweiligen Szenario passiert und wie es verwendet wird.

![Animiertes GIF eines interaktiven Holographic-Menüsystems](images/designing-holograms/creative-process.gif)

## <a name="try-it-out-moments"></a>Augenblicke ausprobieren

Der Entwurf von holograms vermittelt gemischte Reality-Konzepte, aber Sie können Sie auch in Ihrem Raum ausprobieren. Nach einigen dieser Erläuterungen halten wir Sie an der Puppenstube und werden in einen interaktiven Moment einsteigen. Im folgenden sind einige Beispiele für diese interaktiven Momente aufgeführt:

![Animiertes GIF des Hand Verfolgungs Rahmens, der angezeigt wird, wenn die Hände erkannt werden, und wenn Sie das Sichtfeld eingeben.](images/designing-holograms/try-out-1.gif)

*Der handverfolgungsframe, der angezeigt wird, wenn die Hände erkannt werden, und wenn Sie das Feld der Ansicht eingeben.*

![Animiertes GIF der Interaktion mit kollidierenden Kristallen durch die weite Interaktion](images/designing-holograms/try-out-2.gif)

*Interagieren mit kollidierenden Kristallen durch die weite Interaktion*

![Animiertes GIF zum Durchsuchen von Near Interaktionen](images/designing-holograms/try-out-3.gif)

*Erkunden von Near Interaktion-auffortungen*

## <a name="about-the-team"></a>Informationen zum Team

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Daniel Escudero" width="60" height="60" src="images/designing-holograms/daniel-escudero.jpeg"></td>
<td style="border-style: none"><b>Daniel Escudero</b><br><i>Leitender technischer Designer</i><br>Dan ist der Creative Director zum Entwerfen von holograms und funktioniert zurzeit als Entwurfs Leiter für die gemischte Reality Academy von Microsoft in San Francisco und war zuvor ein Designer in einem der Mixed Reality-Studio von Microsoft in London.</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Martin Wettig" width="60" height="60" src="images/designing-holograms/martin-wettig.jpeg"></td>
<td style="border-style: none"><b>Martin-Wettig</b><br><i>Senior 3D-Künstler</i><br>Martin leitet 3D-Grafiken und UI-Design für das Entwerfen von holograms ein und war zuvor Senior 3D-Artist in einem der Mixed Reality-Studio von Microsoft in Berlin.</td>
</tr>
</table>

Ein sehr vielen Dank für das Mixed Reality-Entwurfs Team, das so viel Wissen und natürlich an die erstaunlichen Leute der [Objekt Theorie](https://objecttheory.com/) weitergegeben hat, die in jedem einzelnen Schritt dieses Projekts wesentliche Teammitglieder wurden. Vielen Dank für ihre faszinierenden Talente, für Ihre Leidenschaft und das besondere Design.

> [!div class="nextstepaction"]
> [Herunterladen der APP zum Entwerfen von holograms](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)