---
title: 'Fallstudie: Erstellen einer Galaxy in Mixed Reality'
description: Erfahren Sie mehr über die Anwendung "Galaxy Explorer" und wie sie für die Microsft-HoloLens und nach einer 24-stundenigen Twitter-Umfrage von Communityentwicklern erstellt wurde.
author: karimluccin
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Galaxy Explorer, HoloLens, Windows Mixed Reality, Teilen Ihrer Idee, Fallstudie
ms.openlocfilehash: 5891fbc052c52cd90176214d1eff8ef019a2bcfc80dbd5264489deced0fb1664
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208046"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a>Fallstudie: Erstellen einer Galaxy in Mixed Reality

Bevor Microsoft HoloLens ausgeliefert wurde, haben wir unsere Entwicklercommunity gefragt, welche Art von App sie wünschen, um einen erfahrenen internen Teambuild für das neue Gerät zu sehen. Mehr als 5.000 Ideen wurden geteilt, und nach einer 24-Stunden-Twitter-Umfrage war der Gewinner eine Idee namens [Galaxy Explorer.](../develop/unity/galaxy-explorer.md)

Andy Zibits, der Leiter des Projekts, und Karim Luczim, Grafiktechniker des Teams, sprechen über die zusammenarbeitsbereite Arbeit zwischen Technik und Technik, die zur Erstellung einer präzisen, interaktiven Darstellung der Milchweggalxie in Galaxy Explorer geführt hat.

## <a name="the-tech"></a>Die Technologie

[Unser Team,](../develop/unity/galaxy-explorer.md#meet-the-team) das aus zwei Designern, drei Entwicklern, vier Architekten, einem Producer und einem Tester besteht, hatte sechs Wochen Zeit, um eine voll funktionsfähige App zu erstellen, mit der Sichten über die Unendlichkeit und Denkfähigkeit unserer Milchwegxie informieren und diese erkunden können.

Wir wollten die Möglichkeit der HoloLens nutzen, um 3D-Objekte direkt in Ihrem Leben zu rendern. Daher haben wir uns entschieden, eine realistisch aussehende Galaxy zu erstellen, in der Menschen in der Lage sind, einzelne Sterne zu vergrößern und jeweils auf ihren eigenen Sehenswürdigkeiten zu sehen.

In der ersten Woche der Entwicklung haben wir uns einige Ziele für unsere Darstellung der Milchweg-Galaxy ein wenig vorgestellt: Sie musste über Tiefe, Bewegung und Lautstärke verfügen – voll von Sternen, die zur Erstellung der Form der Galaxy beitragen würden.

Das Problem beim Erstellen einer animierten Galaxy mit Milliarden von Sternen bestand darin, dass die schieren Anzahl von einzelnen Elementen, die aktualisiert werden müssen, zu groß pro Frame wäre, damit HoloLens die CPU animieren kann. Unsere Lösung umfasste eine komplexe Mischung aus Technik und Wissenschaft.

## <a name="behind-the-scenes"></a>Abläufe im Hintergrund

Damit Menschen einzelne Sterne untersuchen können, bestand der erste Schritt darin, herauszufinden, wie viele Partikel gleichzeitig gerendert werden konnten.

### <a name="rendering-particles"></a>Rendern von Partikeln

Aktuelle CPUs eignen sich hervorragend für die gleichzeitige Verarbeitung von seriellen Aufgaben und bis zu einigen parallelen Aufgaben (je nachdem, wie viele Kerne sie haben), aber GPUs sind viel effektiver bei der parallelen Verarbeitung von Tausenden von Vorgängen. Da sie jedoch in der Regel nicht denselben Arbeitsspeicher wie die CPU nutzen, kann der Austausch von Daten zwischen CPU-<>GPU schnell zu einem Engpass werden. Unsere Lösung bestand darin, eine Galaxy auf der GPU zu erstellen, die vollständig auf der GPU geschaltet werden musste.

Wir haben Belastungstests mit Tausenden von Punktteilchen in verschiedenen Mustern gestartet. Dadurch konnten wir die Galaxy auf HoloLens abrufen, um zu sehen, was funktioniert hat und was nicht.

### <a name="creating-the-position-of-the-stars"></a>Erstellen der Position der Sterne

Eines unserer Teammitglieder hatte bereits den C#-Code geschrieben, der Sterne an ihrer ursprünglichen Position generieren würde. Die Sterne befinden sich auf einer Ellipse, und ihre Position kann durch (**curveOffset**, **ellipseSize**, **elevation**) beschrieben werden, wobei **curveOffset** der Winkel des Sterns entlang der Ellipse ist, **ellipseSize** die Dimension der Ellipse entlang X und Z und die rechte Höhe des Sterns innerhalb der Galaxy. Daher können wir einen Puffer ([ComputeBuffer](https://docs.unity3d.com/ScriptReference/ComputeBuffer.html)von Unity ) erstellen, der mit jedem Sternattribut initialisiert wird, und ihn an die GPU senden, in der er für den Rest der Umgebung zu finden ist. Um diesen Puffer zu zeichnen, verwenden wir [DrawProcedural](https://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) von Unity, das das Ausführen eines Shaders (Code auf einer GPU) auf einem beliebigen Satz von Punkten ohne ein tatsächliches Gitter ermöglicht, das die Galaxy darstellt:

**Cpu:**




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

**Gpu:**




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

Wir haben mit rohen Kreismustern mit Tausenden von Partikeln begonnen. Dies hat uns den Beweis gegeben, dass wir viele Partikel verwalten und mit hoher Geschwindigkeit ausführen konnten, aber wir waren mit der Gesamtform der Galaxy nicht zufrieden. Um die Form zu verbessern, haben wir verschiedene Muster und Partikelsysteme mit Drehung versucht. Diese waren anfänglich unwahrscheinlich, da die Anzahl der Partikel und die Leistung konsistent bleiben, aber die Form in der Nähe des Mittelpunkts abbricht und die Sterne nach außen ausgegeben wurden, was nicht realistisch war. Wir benötigten eine Ausgabe, die es uns ermöglichte, die Zeit zu bearbeiten und die Partikel realistisch zu bewegen und sich immer näher an der Mitte der Galaxy zu bewegen.

![Wir haben verschiedene Muster und Partikelsysteme wie diese gedreht.](images/galaxy-patterns-500px.png)

Wir haben verschiedene Muster und Partikelsysteme wie diese gedreht.

Unser Team hat einige Untersuchungen zur Funktionsweise von Ellipsen durchgeführt und ein benutzerdefiniertes Partikelsystem speziell für die Galaxy erstellt, sodass wir die Partikel auf Ellipsen basierend auf der["Dichtewellentheorie"](https://en.wikipedia.org/wiki/Density_wave_theory)verschieben konnten, die besagt, dass die Arme einer Galaxy Bereiche mit höherer Dichte, aber in konstantem Fluss sind, z. B. eine Verkehrsstaus. Es erscheint stabil und fest, aber die Sterne bewegen sich tatsächlich in die und aus den Armen, während sie sich entlang ihrer jeweiligen Ellipsen bewegen. In unserem System sind die Partikel nie auf der CPU vorhanden. Wir generieren die Karten und richten sie alle auf der GPU aus, sodass das gesamte System einfach den Anfangszustand und die Zeit aufnimmt. Der Fortschritt sieht wie folgt aus:

![Fortschritt des Partikelsystems mit GPU-Rendering](images/spiral-galaxy-arms-500px.jpg)

Fortschritt des Partikelsystems mit GPU-Rendering


Sobald genügend Ellipsen hinzugefügt wurden und für die Drehung festgelegt wurden, haben die Ellipsen begonnen, "Arme" zu bilden, in denen die Bewegung der Sterne konvergiert. Der Abstand der Sterne entlang jedes elliptischen Pfads wurde mit einer gewissen Zufälligkeit versehen, und jedem Stern wurde ein wenig Zufälligkeit der Position hinzugefügt. Dadurch wurde eine wesentlich natürlicher aussehende Verteilung von Sternbewegungen und Armform erstellt. Schließlich haben wir die Möglichkeit hinzugefügt, die Farbe basierend auf der Entfernung vom Mittelpunkt zu steuern.

### <a name="creating-the-motion-of-the-stars"></a>Erstellen der Bewegung der Sterne

Um die allgemeine Sternbewegung zu animieren, mussten wir einen konstanten Winkel für jeden Frame hinzufügen und Sterne mit konstanter radialer Geschwindigkeit entlang ihrer Ellipsen bewegen. Dies ist der Hauptgrund für die Verwendung von **curveOffset.** Dies ist technisch nicht richtig, da sterne sich schneller entlang der langen Seiten der Ellipsen bewegen, aber die allgemeine Bewegung gut verläuft.

![Sterne bewegen sich schneller auf dem langen Bogen, langsamer an den Rändern.](images/ellipse-movement.jpg)

Sterne bewegen sich schneller auf dem langen Bogen, langsamer an den Rändern.


Damit wird jeder Stern vollständig von (**curveOffset**, **ellipseSize**, **elevation**, **Age**) beschrieben, wobei **Age** eine Akkumulation der Gesamtzeit ist, die seit dem Laden der Szene verstrichen ist.




```
float3 ComputeStarPosition(StarDescriptor star)
{

  float curveOffset = star.curveOffset + Age;
  
  // this will be coded as a “sincos” on the hardware which will compute both sides
  float x = cos(curveOffset) * star.xRadii;
  float z = sin(curveOffset) * star.zRadii;
   
  return float3(x, star.elevation, z);
  
}
```

Dies ermöglichte es uns, zu Beginn der Anwendung Zehntausende von Sternen zu generieren, und dann haben wir eine einzelne Gruppe von Sternen entlang der festgelegten Kurven animiert. Da sich alles auf der GPU befindet, kann das System alle Sterne ohne Kosten für die CPU parallel animieren.

![So sieht es beim Zeichnen weißer Quader aus.](images/drawing-white-quads-300px.jpg)

So sieht es beim Zeichnen weißer Quader aus.



Um jedes Quad-Gesicht zur Kamera zu machen, haben wir einen Geometrie-Shader verwendet, um jede Sternposition in ein 2D-Rechteck auf dem Bildschirm zu transformieren, das unsere Sterntextur enthält.

![Rauten anstelle von Quadern.](images/drawing-white-quads-300px.jpg)

Rauten anstelle von Quadern.


Da wir die Überzeichnung (Anzahl der Verarbeitungen eines Pixels) so weit wie möglich einschränken wollten, haben wir unsere Quader gedreht, sodass sie sich weniger überlappen.

### <a name="adding-clouds"></a>Hinzufügen von Clouds

Es gibt viele Möglichkeiten, ein volumetrisches Gefühl mit Partikeln zu erhalten – vom Strahllauf innerhalb eines Volumes bis hin zum Zeichnen so vieler Partikel wie möglich, um eine Cloud zu simulieren. Da das Strahlmärschen in Echtzeit zu teuer und schwer zu erstellen war, haben wir zunächst versucht, ein Impostersystem zu erstellen, indem wir eine Methode zum Rendern von Gesamtstrukturen in Spielen verwendet haben – mit vielen 2D-Bildern von Strukturen, die der Kamera gegenüberstehen. Wenn wir dies in einem Spiel tun, können Texturen von Strukturen von einer Kamera gerendert werden, die sich umdreht, alle diese Bilder speichern und zur Laufzeit für jede Kartenkarte das Bild auswählen, das der Ansichtsrichtung entspricht. Dies funktioniert nicht so gut, wenn es sich bei den Bildern um Hologramme handelt. Der Unterschied zwischen dem linken und dem rechten Auge macht es so, dass wir eine viel höhere Auflösung benötigen. Andernfalls sieht es einfach flach, aliasiert oder sich wiederholend aus.

Im zweiten Versuch haben wir versucht, so viele Partikel wie möglich zu haben. Die besten visuellen Elemente wurden erzielt, wenn wir die Partikel additiv gezeichnet und unscharf gemacht haben, bevor wir sie der Szene hinzufügen. Die typischen Probleme bei diesem Ansatz bezogen sich darauf, wie viele Partikel wir zu einem einzigen Zeitpunkt zeichnen konnten, und wie viel Bildschirmbereich sie abdeckten, während sie immer noch 60 Fps beibehälten. Das Weichzeichnen des resultierenden Bilds, um dieses Cloudstimmungsbild zu erhalten, war in der Regel ein sehr kostspieliger Vorgang.

![Ohne Textur würden die Clouds mit einer Deckkraft von 2 % so aussehen.](images/clouds-without-texture-300px.jpg)

Ohne Textur würden die Clouds mit einer Deckkraft von 2 % so aussehen.



Additiv zu sein und viele davon zu haben, bedeutet, dass mehrere Quader übereinander stehen und das gleiche Pixel wiederholt schattiert wird. In der Mitte der Galaxy hat das gleiche Pixel Hunderte von Quadern übereinander, und dies hatte große Kosten, wenn der Vollbildmodus durchgeführt wurde.

Das Durchführen von Vollbildclouds und der Versuch, sie zu verwischen, wäre eine schlechte Idee gewesen. Stattdessen haben wir uns entschieden, die Hardware die Arbeit für uns erledigen zu lassen.

### <a name="a-bit-of-context-first"></a>Zunächst ein wenig Kontext

Bei der Verwendung von Texturen in einem Spiel entspricht die Texturgröße selten dem Bereich, in dem sie verwendet werden soll. Wir können jedoch eine andere Art von Texturfilterung verwenden, um die Grafikkarte zu erhalten, um die gewünschte Farbe aus den Pixeln der Textur zu interpolieren ([Texturfilterung](/previous-versions/visualstudio/visual-studio-2015/debugger/point-bilinear-trilinear-and-anisotropic-texture-filtering-variants)). Die Filterung, die für uns von Interesse ist, ist [die bilineare Filterung,](/windows/win32/direct3d9/bilinear-texture-filtering) die den Wert eines beliebigen Pixels mit den vier nächsten Nachbarn berechnet.

![Original vor dem Filtern](images/texture-1.png)

![Ergebnis nach dem Filtern](images/texture-2.png)

Mit dieser Eigenschaft sehen wir, dass jedes Mal, wenn wir versuchen, eine Textur in einen doppelt so großen Bereich zu zeichnen, das Ergebnis unscharf wird.

Anstatt auf einen Vollbildbildschirm zu rendern und diese wertvollen Millisekunden zu verlieren, die wir für etwas anderes ausgeben könnten, rendern wir zu einer kleinen Version des Bildschirms. Wenn sie diese Textur dann kopiert und mehrmals um den Faktor 2 gestreckt wird, gelangen wir zurück zum Vollbildmodus, während der Inhalt im Prozess unscharf wird.

![x3-Hochskalierung bis zur vollständigen Auflösung.](images/galaxy-resolutions-300px.png)

x3-Hochskalierung bis zur vollständigen Auflösung.



Dadurch konnten wir den Cloudteil nur mit einem Bruchteil der ursprünglichen Kosten abrufen. Anstatt Clouds in der vollständigen Auflösung hinzuzufügen, zeichnen wir nur 1/64 Pixel und strecken die Textur einfach auf die vollständige Auflösung zurück.

![Links, mit einer Hochskalierung von 1/8 bis zur vollständigen Auflösung; und rechts, mit 3 Hochskalierung mit einer Leistung von 2.](images/stars-upscaled-300px.jpg)

Links, mit einer Hochskalierung von 1/8 bis zur vollständigen Auflösung; und rechts, mit 3 Hochskalierung mit einer Leistung von 2.


Beachten Sie, dass der Versuch, von 1/64 zur vollständigen Größe auf einmal zu wechseln, völlig anders aussieht, da die Grafikkarte in unserem Setup immer noch 4 Pixel zum Schattieren eines größeren Bereichs verwendet und Artefakte angezeigt werden.

Wenn wir dann Sterne mit vollständiger Auflösung mit kleineren Karten hinzufügen, erhalten wir die vollständige Galaxy:

![Nahezu das Endergebnis des Galaxy Renderings mit Sternen mit voller Auflösung](images/full-galaxy-500px.png)

Sobald wir uns mit der Form auf dem richtigen Weg befanden, haben wir eine Ebene von Clouds hinzugefügt, die temporären Punkte mit denen ausgetauscht, die wir in Bildern gezeichnet haben, und zusätzliche Farbe hinzugefügt. Das Ergebnis war ein "Milky Way Galaxy", über das sich unsere Technik- und Entwicklungsteams sowohl gut als auch unsere Ziele von Tiefe, Volumen und Bewegung informiert haben – alles ohne cpu-Auslastung.

![Unsere letzte Milky Way Galaxy in 3D.](images/final-galaxy-500px.jpg)

Unsere letzte Milky Way Galaxy in 3D.


### <a name="more-to-explore"></a>Weitere Informationen

Wir haben den Code für die Galaxy Explorer-App als Open Source veröffentlicht und auf [GitHub](https://github.com/Microsoft/GalaxyExplorer) für Entwickler zur Verfügung gestellt, auf der sie aufbauen können.

Möchten Sie mehr über den Entwicklungsprozess für Galaxy Explorer erfahren? Sehen Sie sich alle unsere früheren Projektupdates auf dem [Microsoft HoloLens YouTube-Kanal](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)an.

## <a name="about-the-authors"></a>Über die Autoren

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><b>Karim Lucimp</b> ist Softwareentwickler und ein Fan von ausgefallenen Visuals. Er war Grafiktechniker für Galaxy Explorer.</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><b>Andy Zibits</b> ist ein Grafikleiter und Space-Fan, der das 3D-Modellierungsteam für Galaxy Explorer verwaltet und sich um noch mehr Partikel eingesetzt hat.</td>
</tr>
</table>


## <a name="see-also"></a>Siehe auch
* [Galaxy Explorer auf GitHub](https://github.com/Microsoft/GalaxyExplorer)
* [Galaxy Explorer-Projektupdates auf YouTube](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)