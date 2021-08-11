---
title: Fallstudie – HoloTour
description: Erkunden Sie die HoloTour-Anwendungsfallstudie, und durchlaufen Sie den Prozess der Erfassung und Erstellung des Inhalts.
author: dannyaskew
ms.author: daaske
ms.date: 03/21/2018
ms.topic: article
keywords: HoloTour, HoloLens, Windows Mixed Reality
ms.openlocfilehash: 7e9bc2078e90b0f0cd98cf0612b583c06b2d51b400d682d3aff71e59eed620a4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202206"
---
# <a name="case-study---holotour"></a>Fallstudie – HoloTour

HoloTour für Microsoft HoloLens bietet immersive persönliche 3D-3D-Orte mit einzigartigen Orten auf der ganzen Welt. Wie die Designer, Interpreten, Producer, Audiodesigner und Entwickler, die an diesem Projekt arbeiten, erkannt haben, ist die Erstellung eines echten 3D-Renderings eines bekannten Orts eine einzigartige Mischung aus kreativer und technologischer Assistenten. In dieser Fallstudie wird der Prozess der Erfassung und Erstellung der für HoloTour verwendeten Inhalte durchlaufen.

## <a name="the-tech"></a>Die Technologie

Mit HoloTour wollten wir es Menschen ermöglichen, einige der weltweit besten Ziele – z. B. die [Sehenswürdigkeiten von "Hotels"](https://en.wikipedia.org/wiki/Machu_Picchu) in Mexiko oder "Modern Day [Navona](https://en.wikipedia.org/wiki/Piazza_Navona) in Rom" – direkt aus ihren eigenen Zimmern zu besuchen. Unser Team hat es zum Ziel von HoloTour gemacht, "ihnen das Gefühl zu geben, dass Sie wirklich da sind". Die Benutzeroberfläche musste mehr als nur Bilder oder Videos sein. Durch die Nutzung der einzigartigen Anzeige-, Nachverfolgungs- und Audiotechnologie von HoloLens konnten wir Sie virtuell an einen anderen Ort bringen. Wir müssten die Töne, Töne und dreidimensionale Geometrie jedes Standorts erfassen, den wir besucht haben, und diese dann innerhalb unserer App neu erstellen.

Dazu benötigen wir eine 360°-Kameraplattform mit direktionaler Audioaufnahme. Es musste mit extrem hoher Auflösung erfasst werden, damit das Material bei Wiedergabe auf einem HoloLens unaufgeregt aussieht und die Kameras nah beieinander positioniert werden müssten, um das Zusammenfügen von Artefakten zu minimieren. Wir wollten eine vollständige sphärische Abdeckung, nicht nur entlang des Horizonts, sondern auch über und unter Ihnen. Das Gerät musste auch portabel sein, damit es auf der ganzen Welt übertragen werden konnte. Wir haben die verfügbaren Standardoptionen ausgewertet und festgestellt, dass sie einfach nicht gut genug waren, um unsere Vision zu realisieren – entweder aufgrund von Auflösung, Kosten oder Größe. Wenn wir kein Kameragerät finden könnten, das unsere Anforderungen erfüllt, müssten wir selbst eins erstellen.

### <a name="building-the-rig"></a>Erstellen der Anlage

Die erste Version , die aus 14 GoPro-Kameras, Velcro, Band und 14 GoPro-Kameras erstellt wurde, war eine Version, auf die MacGyver gegrollt hätte. Nach der Überprüfung von Low-End-Lösungen bis hin zu benutzerdefinierten Fertigungsanlagen waren GoPro-Kameras letztendlich die beste Option für uns, da sie klein, kostengünstig und einfach zu verwendenden Speicher waren. Der kleine Formfaktor war besonders wichtig, da er es uns ermöglichte, Kameras relativ nah beieinander zu platzieren– je kleiner der Abstand zwischen den Kameras ist, desto kleiner sind die Zusammenfügen von Artefakten. Unsere einzigartige Kameraanordnung ermöglichte es uns, eine vollständige Kugelabdeckung *sowie* genügend Überschneidungen zu erhalten, um Kameras intelligent auszurichten und einige Artefakte während des Zusammenfügens zu glätten.

Die Nutzung der [räumlichen Soundfunktionen](../design/spatial-sound.md) auf HoloLens ist entscheidend, um eine echten immersiven Erfahrung zu schaffen. Wir haben ein Array mit vier Mikrofonen unter den Kameras auf dem Tripod verwendet, das Denkton von der Position der Kamera in vier Richtungen erfassen würde, sodass wir genügend Informationen erhalten, um räumliche Sounds in unseren Szenen zu erstellen.

![Unsere 360°-Kameraplattform, die für Drehungen außerhalb des Pantheon eingerichtet ist.](images/camera-pantheon-200px.png)

Unsere 360°-Kameraplattform, die für Drehungen außerhalb des Pantheon eingerichtet ist. 


Wir haben unsere heimelige Anlage getestet, indem wir sie auf RattlesnakeFirst in der Nähe von Seattle aufstellten und die Landschaften am Anfang der Kante erfassten. Das Ergebnis, obwohl es deutlich weniger ausgereift ist als die Standorte, die Sie heute in HoloTour sehen, hat uns das Vertrauen gegeben, dass unser Entwurf gut genug war, damit Sie das Gefühl haben, dass Sie wirklich dort sind.

Wir haben unsere Anlage von Velcro auf ein 3D-gedrucktes Kameragehäuse aktualisiert und externe Akkupakete für die GoPro-Kameras gekauft, um die Akkuverwaltung zu vereinfachen. Anschließend haben wir einen umfassenderen Test gemacht und sind nach San Francisco landet, um eine Tour durch die Stadt und die golden gate-Brücke zu erstellen. Dieses Kameragerät wurde für die meisten unserer Erfassungen der Orte verwendet, die Sie in HoloTour besuchen.

![Das 360°-Kameragerät, das in Der 360-Grad-Kamera gedreht wird.](images/camera-machu-pichu-500px.png)

Das 360°-Kameragerät, das in Der 360-Grad-Kamera gedreht wird. 

## <a name="behind-the-scenes"></a>Abläufe im Hintergrund

Vor den Drehungen mussten wir herausfinden, welche Orte wir in unsere virtuelle Tour aufnehmen wollten. Rom war der erste Standort, den wir liefern wollten, und wir wollten es richtig machen. Daher haben wir uns entschieden, im Voraus eine Scouting-Fahrt zu unternehmen. Wir haben ein Team von sechs Personen – darunter Architekten, Designer und Producer – zu einem persönlich besuchten Besuch der von uns in Betracht gezogenen Websites gesendet. Die Fahrt dauerte etwa 9 Tage – 2,5 für die Reise, der Rest für Drehungen. (Wir haben uns entschieden, keine Scout-Fahrt zu unternehmen, im Voraus zu recherchieren und ein paar Tage Puffer für Drehungen zu reservieren.)

In Rom hat das Team Fotos von den einzelnen Bereichen aufgenommen und interessante Fakten sowie praktische Überlegungen festgestellt, z. B. wie schwierig es ist, zu jedem Ort zu reisen, und wie schwierig es wäre, aufgrund von Menschenmengen oder Einschränkungen zu drehen. Dies mag wie ein Urlaub klingen, aber es ist viel Arbeit. Die Tage starteten früh am Morgen und waren bis zum Abend nicht mehr zu stoppen. Jede Nacht wurde Das Material für das Team zurück in Seattle hochgeladen, um es zu überprüfen. 

![Unsere Aufnahmebesatzung in Rom.](images/holotour-filming-crew-rome-500px.jpg) 

Unsere Aufnahmebesatzung in Rom. 


Nachdem die Scout-Fahrt abgeschlossen wurde, wurde ein endgültiger Plan für die tatsächlichen Drehungen erstellt. Dies erforderte eine detaillierte Liste, wo wir zu welchem Zeitpunkt zu welchem Zeitpunkt drehen wollten. Die tägliche Fahrt ist teuer, daher müssen diese Fahrten effizient sein. Wir haben Leitfäden und Handler in Rom reserviert, um uns zu helfen und jeden Tag von vor und nach dem Untergang vollständig verwendet zu werden. Wir müssen das bestmögliche Material erhalten, damit Sie das Gefühl haben, dass Sie wirklich dort sind.

### <a name="capturing-the-video"></a>Aufzeichnen des Videos

Das Durchführen einiger einfacher Dinge während der Erfassung kann die Nachverarbeitung erheblich vereinfachen. Wenn Sie beispielsweise Bilder von mehreren Kameras zusammenfügen, erhalten Sie visuelle Artefakte, da jede Kamera eine etwas andere Ansicht hat. Je näher die Objekte an der Kamera liegen, desto größer ist der Unterschied zwischen den Ansichten, und je größer die Zusammenfügen von Artefakten sind. Dies ist eine einfache Möglichkeit, das Problem zu visualisieren: Halten Sie den Daumen vor Ihrem Gesicht, und betrachten Sie es mit nur einem Auge. Wechseln Sie nun die Augen. Sie werden sehen, dass ihr Daumen relativ zum Hintergrund zu bewegen scheint. Wenn Sie den Daumen weiter weg vom Gesicht halten und das Experiment wiederholen, scheint sich ihr Daumen weniger zu bewegen. Diese offensichtliche Bewegung ähnelt dem zusammengefügten Problem: Ihre Augen sehen wie unsere Kameras nicht genau das gleiche Bild, da sie durch eine geringe Entfernung voneinander getrennt sind.

Da es viel einfacher ist, die schlechtesten Artefakte beim Filmen zu verhindern, als sie in der Nachbearbeitung zu korrigieren, haben wir versucht, Menschen und Dinge weit von der Kamera in der Freundlichkeit zu halten, die wir vermeiden könnten, Nahaufnahmeobjekte zusammenfügen zu müssen. Das Warten einer großen Bereinigung um unsere Kamera war wahrscheinlich eine der größten Herausforderungen, die wir beim Drehen hatten, und wir mussten uns kreativ machen, damit es funktionierte. Die Arbeit mit lokalen Leitfäden war eine große Hilfe bei der Verwaltung von Menschenmengen, aber wir haben auch festgestellt, dass die Verwendung von Schildern ( und manchmal kleinen Kegeln oder Bean-Behältern) zum Markieren unseres Drehbereichs relativ effektiv war, insbesondere da wir nur eine kurze Menge an Bildern an jedem Ort benötigen. Häufig war die beste Möglichkeit, eine gute Erfassung zu erhalten, einfach sehr früh am Morgen eintreffen, bevor die meisten Personen aufkamen.

Einige andere nützliche Erfassungstechniken stammen direkt aus herkömmlichen Filmpraktiken. Beispielsweise haben wir eine Farbkorrekturkarte für alle Unsere Kameras verwendet und Referenzfotos von Texturen und Objekten erfasst, die wir später möglicherweise benötigen. 

![Ein grober Schnitt von "Wiesn" mit der Karte für die Farbkorrektur.](images/rough-cut-machu-picchu-500px.png)

Ein grober Schnitt von Pantheon-Material vor dem Zusammenfügen.

### <a name="processing-the-video"></a>Verarbeiten des Videos

Das Erfassen von 360°-Inhalten ist nur der erste Schritt. Es ist eine menge Verarbeitung erforderlich, um die von uns erfassten rohen Kameraaufnahmen in die endgültigen Objekte zu konvertieren, die Sie in HoloTour sehen. Als wir wieder zu Hause waren, mussten wir das Video aus 14 verschiedenen Kamerafeeds aufnehmen und es in ein einzelnes kontinuierliches Video mit minimalen Artefakten umwandeln. Unser Grafikteam hat eine Reihe von Tools verwendet, um die erfassten Bilder zu kombinieren und zu optimieren, und wir haben eine Pipeline entwickelt, um die Verarbeitung so weit wie möglich zu optimieren. Das Material musste zusammengefügt, die Farbe korrigiert und dann zusammengesetzt werden, um ablenkende Elemente und Artefakte zu entfernen oder zusätzliche Taschen von Leben und Bewegung hinzuzufügen. All das zielte darauf ab, das Gefühl zu verbessern, tatsächlich dort zu sein.

![Ein grober Schnitt von Pantheon-Material vor dem Zusammenfügen.](images/rough-cut-pantheon-500px.png)

Ein grober Schnitt von Pantheon-Material vor dem Zusammenfügen. 


Zum Zusammenfügen der Videos haben wir ein Tool namens [PTGui](https://www.ptgui.com/) verwendet und in unsere Verarbeitungspipeline integriert. Im Rahmen der Nachbearbeitung haben wir Noch-Frames aus unseren Videos extrahiert und ein Zusammenfügensmuster gefunden, das für einen dieser Frames gut aussähe. Wir haben dieses Muster dann auf ein benutzerdefiniertes Plug-In angewendet, das unseren Videointeressierern ermöglicht hat, das Zusammenfügensmuster direkt beim Zusammenfügen in After Effects zu optimieren und zu optimieren. 

![Screenshot von PTGui mit dem zusammengefügten Pantheon-Material](images/stitching-tool-pantheon-500px.png)

Screenshot von PTGui mit dem zusammengefügten Pantheon-Material 


### <a name="video-playback"></a>Videowiedergabe

Nachdem die Verarbeitung des Bildmaterials abgeschlossen ist, haben wir ein nahtloses Video, aber es ist sehr groß – etwa 8K Auflösung. Das Decodieren von Videos ist teuer, und es gibt nur sehr wenige Computer, die ein 8K-Video verarbeiten können. Die nächste Herausforderung bestand also darin, eine Möglichkeit zu finden, dieses Video wieder auf HoloLens wiederzuspielen. Wir haben eine Reihe von Strategien entwickelt, um die Kosten für die Decodierung zu vermeiden, während der Benutzer das Gefühl hat, das gesamte Video anzuzeigen.

Die einfachste Optimierung besteht darin, das Decodieren von Teilen des Videos zu vermeiden, die sich nicht wesentlich ändern. Wir haben ein Tool geschrieben, um Bereiche in jeder Szene zu identifizieren, die wenig oder gar keine Bewegung aufweisen. Für diese Regionen zeigen wir ein statisches Bild an, anstatt für jeden Frame ein Video zu decodieren. Um dies zu ermöglichen, haben wir das riesige Video in viel kleinere Blöcke aufgeteilt.

Außerdem haben wir sichergestellt, dass jedes von uns decodierte Pixel am effektivsten verwendet wurde. Wir haben mit Komprimierungstechniken experimentiert, um die Größe des Videos zu verringern. wir teilen die Videobereiche entsprechend den Polygonen der Geometrie auf, auf die es projiziert wird. Wir haben UVs angepasst und die Videos basierend darauf, wie viele Details verschiedene Polygone enthalten sind, neu gepackt. Das Ergebnis dieser Arbeit ist, dass das, was als einzelnes 8k-Video gestartet wurde, in viele Blöcke umgewandelt wurde, die fast unverständlich aussehen, bis sie ordnungsgemäß in die Szene projiziert werden. Für einen Spieleentwickler, der die Texturzuordnung und UV-Komprimierung versteht, wird dies wahrscheinlich vertraut aussehen. 

![Eine vollständige Ansicht des Pantheon vor Optimierungen.](images/pantheon-before-optimization-500px.png) 

Eine vollständige Ansicht des Pantheon vor Optimierungen. 


![Die rechte Hälfte des Pantheon, verarbeitet für die Videowiedergabe.](images/pantheon-process-video-playback-500px.png) 

Die rechte Hälfte des Pantheon, verarbeitet für die Videowiedergabe. 


![Beispiel für einen einzelnen Videobereich nach Optimierung und Komprimierung.](images/single-video-region-after-optimization-500px.png) 

Beispiel für einen einzelnen Videobereich nach Optimierung und Komprimierung. 


Ein weiterer Trick, den wir verwendet haben, bestand darin, das Decodieren von Videos zu vermeiden, die Sie nicht aktiv anzeigen. In HoloTour können Sie nur einen Teil der vollständigen Szene zu einem bestimmten Zeitpunkt sehen. Wir decodieren nur Videos innerhalb oder kurz außerhalb Ihres Sichtfelds (Field of View, FOV). Wenn Sie den Kopf drehen, beginnen wir mit der Wiedergabe der Bereiche des Videos, die sich jetzt in Ihrem FOV befinden, und beenden die Wiedergabe von Bereichen, die sich nicht mehr darin befinden. Die meisten Werden nicht einmal bemerken, dass dies geschieht, aber wenn Sie sich schnell drehen, sehen Sie, dass das Video eine Sekunde dauert, um zu beginnen. In der Zwischenzeit sehen Sie ein statisches Bild, das dann wieder in das Video einblendet, sobald es bereit ist.

Damit diese Strategie funktioniert, haben wir ein umfassendes Videowiedergabesystem entwickelt. Wir haben den Wiedergabecode auf niedriger Ebene optimiert, um den Videowechsel äußerst effizient zu gestalten. Darüber hinaus mussten wir unsere Videos auf besondere Weise codieren, damit jederzeit schnell zu jedem Video gewechselt werden kann. Diese Wiedergabepipeline benötigte viel Entwicklungszeit, sodass wir sie in Phasen implementiert haben. Wir haben mit einem einfacheren System begonnen, das weniger effizient war, aber Designern und Architekten erlaubte, an der Erfahrung zu arbeiten, und es langsam zu einem stabileren Wiedergabesystem verbessert, das es uns ermöglichte, an der endgültigen Qualitätsleiste zu liefern. Dieses endgültige System hatte benutzerdefinierte Tools, die wir in Unity erstellt haben, um das Video innerhalb der Szene einzurichten und die Wiedergabe-Engine zu überwachen.

### <a name="recreating-near-space-objects-in-3d"></a>Recreating near-space objects in 3D

Videos machen den Großteil von dem aus, was Sie in HoloTour sehen, aber es gibt eine Reihe von 3D-Objekten, die in Ihrer Nähe angezeigt werden, z. B. das Zeichnen in Navona, das Licht außerhalb des Pantheon oder der Heißlichtsprechblasen, in dem Sie sich für Luftaufnahmen befinden. Diese 3D-Objekte sind wichtig, da die Menschliche Tiefenerkennung sehr gut aus nächster Nähe, aber nicht sehr weit entfernt ist. Wir können mit Videos in der Nähe fortkommen, aber um Benutzern zu ermöglichen, ihren Raum zu begehen und das Gefühl zu haben, dass sie wirklich dort sind, benötigen Objekte in der Nähe Tiefe. Diese Technik ähnelt der Art von Etwas, das Sie in einem Naturverlaufsgesicht sehen können: Stellen Sie sich eine Dioanlage vor, die physisches Kapseln, Pflanzen und Tierlichter im Vordergrund hat, sich aber in ein clever maskiertes mattes Bild im Hintergrund zurückverlegt.

Einige Objekte sind einfach 3D-Objekte, die wir erstellt und der Szene hinzugefügt haben, um die Erfahrung zu verbessern. Das Zeichnen und der Heißlichtsprechblasen fallen in diese Kategorie, da sie beim Dreh nicht vorhanden waren. Ähnlich wie Spielressourcen wurden sie von einem 3D-Interpreten in unserem Team erstellt und entsprechend strukturiert. Wir platzieren diese in unseren Szenen in der Nähe ihrer Position, und die Spiel-Engine kann sie für die beiden HoloLens Anzeigen rendern, sodass sie als 3D-Objekt angezeigt werden.

Andere Objekte, wie z.B. die Therde außerhalb des Pantheon, sind echte Objekte, die an den Orten vorhanden sind, an denen wir Videos drehen. Um diese Objekte jedoch aus dem Video und in 3D zu bringen, müssen wir eine Reihe von Aufgaben ausführen.

Zunächst benötigen wir zusätzliche Informationen zu jedem Objekt. Während des Drehs hat unser Team viele Referenzaufnahmen dieser Objekte erfasst, sodass wir über genügend detaillierte Bilder verfügen würden, um die Texturen genau neu zu erstellen. Das Team hat auch einen [Photogrammetry-Scan](https://en.wikipedia.org/wiki/Photogrammetry) durchgeführt, der ein 3D-Modell aus Dutzenden von 2D-Bildern erstellt, sodass wir ein grobes Modell des Objekts in perfekter Größe erhalten.

Während wir unser Material verarbeiten, werden Objekte, die später durch eine 3D-Darstellung ersetzt werden, aus dem Video entfernt. Das 3D-Medienobjekt basiert auf dem Photogrammetriemodell, wurde jedoch von unseren Interpreten bereinigt und vereinfacht. Für einige Objekte können wir Teile des Videos verwenden, z. B. die Wassertextur auf dem Gang, aber der größte Teil des Objekts ist jetzt ein 3D-Objekt, das es Benutzern ermöglicht, Tiefe zu erkennen und sie in einem begrenzten Raum in der Umgebung zu umgehen. Solche Objekte in der Nähe des Raumes tragen erheblich zum Realismus bei und tragen dazu bei, die Benutzer am virtuellen Standort zu ergrunden. 

![Pantheonmaterial mit entferntem Ausschnitt. Es wird durch ein 3D-Medienobjekt ersetzt.](images/object-removal-pantheon-500px.png)

Pantheonmaterial mit entferntem Ausschnitt. Es wird durch ein 3D-Medienobjekt ersetzt.


## <a name="final-thoughts"></a>Schlussbemerkungen

Natürlich gab es mehr zu erstellen, als wir hier erläutert haben. Es gibt einige Szenen , die wir gerne als "unmögliche Perspektiven" bezeichnen, einschließlich der Fahrt mit dem Heißlichtballon und der Sprechblasen im Colosseum, die einen kreativeren Ansatz verfolgten. Wir werden diese in einer zukünftigen Fallstudie untersuchen.

Wir hoffen, dass die Freigabe von Lösungen für einige der größeren Herausforderungen, die wir während der Produktion hatten, für andere Entwickler hilfreich ist und Sie dazu inspiriert sind, einige dieser Techniken zu verwenden, um Ihre eigenen immersiven Erfahrungen für HoloLens zu erstellen. (Wenn Sie dies tun, stellen Sie sicher, dass Sie es uns im [forum für die HoloLens App-Entwicklung](https://forums.hololens.com/)mitteilen!)

## <a name="about-the-authors"></a>Über die Autoren

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="David Haley" width="60" height="60" src="images/haley.png" /></td>
<td style="border:0" width="408"> <b>David Haley</b> ist ein leitender Entwickler, der mehr über Kameraplattformen und Videowiedergabe gelernt hat, als er bei der Arbeit an HoloTour für möglich gehalten hat.</td>
<td style="border:0" width="60px"> <img alt="Danny Askew" width="60" height="60" src="images/askew.png" /></td>
<td style="border:0" width="408"> <b>Danny Askew</b> ist ein Videoartist, der sicherstellte, dass Ihre Reise durch Rom so fehlerfrei wie möglich war.</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Jason Syltebo" width="60" height="60" src="images/syltebo.png" /></td>
<td style="border:0" width="408"> <b>Jason Syltebo</b> ist ein Audio-Designer, der sichergestellt hat, dass Sie die Soundscape jedes Ziels, das Sie besuchen, auch dann erleben können, wenn Sie in die Zeit zurückkehren.</td>
<td style="border:0" width="60px"> <img alt="Travis Steiner" width="60" height="60" src="images/steiner.png" /></td>
<td style="border:0" width="408"> <b>Travis Steiner</b> ist Design Director, der Orte recherchiert und durchsucht, Fahrtenpläne erstellt und Dreharbeiten vor Ort geleitet hat.</td>
</tr>
</table>



## <a name="see-also"></a>Siehe auch
* [Video: Microsoft HoloLens: HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)
