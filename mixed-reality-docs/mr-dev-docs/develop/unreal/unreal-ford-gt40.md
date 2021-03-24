---
title: Ford GT40-Darstellung
description: Sehen Sie sich an, wie Sie die Anwendung "Ford GT40 Mixed Reality" mit mrtk für hololens 2 in Unreal kennenlernen.
author: hferrone
ms.author: v-hferrone
ms.date: 3/23/2021
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, hololens, hololens 2, Mixed Reality, bereitstellen auf Geräten, PCs, Dokumentationen, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
appliesto:
- HoloLens 2
ms.openlocfilehash: ca577bdc5bc30aebf80c9888345eb0e2d5c3ce6d
ms.sourcegitcommit: cc9d90b046a9fce792058fea25ae13a9186e43e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2021
ms.locfileid: "105008925"
---
# <a name="the-making-of-the-ford-gt40-experience"></a>Die Darstellung der "Ford GT40"-Funktion

*"Pre-mrtk, Entwicklung für hololens 2 mithilfe von Unreal war etwas mühsam, da alle räumlichen Interaktionen in C++ per handcodiert werden mussten. Der mrtk für Unreal machte viele dieser Aufgaben trivial. Ich würde schätzen, dass die benötigte Zeit für den anfänglichen Prototyp in der Hälfte verkürzt wird. "* -Jose Rodriguez, Software Entwickler

*"Der Ford GT40-Vorgang ist ein Beleg dafür, dass eine hochwertige hololens 2-app in nur wenigen Monaten mit einem gering fügenden Budget abgeschlossen werden kann, aber trotzdem äußerst wirkungsvolle Ergebnisse liefert."*  -Daniel Cheetham, Chief Innovation Officer, glückliche Fertigstellung

Mit dem Mixed Reality Toolkit (mrtk) für Unreal war die glückliche Fertigstellung des Creative Production-Unternehmens eine "hololens 2"-Umgebung, die eine neue Perspektive für den Ford GT40 bietet, das legendäre Rennfahrzeug, das Ferrari zu den 24 Stunden von Le Mans schlug

Durch die Verwendung einer Reihe natürlicher und intuitiver räumlicher Interaktionen können Benutzer die GT40's Beauty, Performance und Engineering – auf eine Weise durchsuchen, die die von der Unreal Engine bereitgestellte hohe visuelle Genauigkeit nutzt. Die Software Entwicklung für das gesamte Projekt wurde in weniger als drei Monaten von einem einzelnen Entwickler abgeschlossen, der von mrtk für die visuelle Skript-und Entwurfs Umgebung von Unreal ermöglicht wurde.

> [!div class="nextstepaction"]
> [Herunterladen der Ford GT40-App](https://www.microsoft.com/p/ford-gt40/9p4vllktfvfp)

![Ford GT40 Hero-Image](images/ford-gt40-hero.jpg)

## <a name="the-ask"></a>Die Frage

Die glückliche Fertigstellung ist eine der weltweit führenden kreativen Produktionsunternehmen mit einer Client Basis, die, Ford, Microsoft, Nike, Netflix, Vodafone und andere Haus Namen umfasst. Das Unternehmen ist als High-End-Photo-reberührungs-Agentur gestartet worden, die in Film und CGI Verzweigungen, bevor es seine Hingabe auf die Exzellenz im immersiven Storytelling mit 3D-Design und-Interaktion erweitert.

In Mitte-2020 hat Microsoft die glückliche Fertigstellung zum Erstellen einer Demo-App herangezogen, die Ihnen dabei helfen könnte, die Möglichkeiten aufzuzeigen, die das neue Mixed Reality Toolkit (mrtk) für Unreal ermöglicht, das auf der Unterstützung von hololens 2 in der Unreal-Engine aufbaut. An diesem Punkt hat das Unternehmen bereits zwei erfolgreiche Unreal-on-hololens 2-Projekte unter dem Band. Beide waren für eine Global erkannte Consumermarke, die für ein internes R&D/B2B-Verkaufstool für die hohe visuelle Genauigkeit Unreal auf hololens 2 gewählt hat. Dies war erforderlich, um die eigenen High-End-Produkte des Clients zu veranschaulichen.

Obwohl die Lösung selbst für eine glückliche Fertigstellung verbleiben würde, musste Sie einige wichtige Richtlinien erfüllen. Zuerst musste Sie sich auf ein Unternehmens Szenario konzentrieren, um das Hilfsprogramm von Unreal auf hololens 2 außerhalb der Spielebranche zu veranschaulichen. Zweitens musste Sie nur Gerät sein, was bedeutet, dass Sie als eigenständiges Demo fungieren konnte – ohne dass eine Netzwerkverbindung und eine externe Verarbeitungsleistung erforderlich sind, um die Ziel Frameraten und die visuelle Qualität zu erzielen. Drittens sollte es den Bereich intuitiver Interaktionen, die von mrtk unterstützt werden, in eine nahtlose und natürliche Darstellung einblenden. Schließlich sollte die vorgeschlagene Lösung die inhärente visuelle Genauigkeit und andere Vorteile der Unreal Engine selbst veranschaulichen, wie z. b. shadereffizienz. 

Angesichts dieser Richtlinien begann die glückliche Fertigstellung mit der Zusammenarbeit mit der Idee für eine gemischte Realität, bei der die räumliche Interaktion verwendet wurde, um den Wert eines hochwertigen Produkts zu kommunizieren. Nach der Betrachtung einer Reihe von Objekten, die Uhren, Kameras, Autos und private Jets enthalten, entschied sich die glückliche Fertigstellung letztendlich für den Ford GT40, eine Auto Mobil Legende, die die notoriiety in 1966 erreicht hat, als er den 24 Stunden der Le Mans – hat, wie im 2019-Blockbuster-Film "Ford vs. Ferrari" gezeigt. 

Bei der Beschaffung von einem bereits vorhandenen, glücklichen Fertigstellen-Client hat das Unternehmen eine neue Perspektive auf dem klassischen automobilsymbol bereitzustellen.

## <a name="the-solution"></a>Die Lösung

Die Arbeit begann am 7. Mai 2020. Nach dem Abrufen der GT40-Modelldateien hat ein 3D-Künstler drei Wochen Zeit für das Optimieren von Polygon Modellen, die UV-Zuordnung, das Neuzeichnen von Textur Karten und das Auffüllen der Karten in so wenig Texturen wie möglich aufgewendet. Ein technischer Künstler hat parallel gearbeitet, um die Ausgabe des 3D-Künstlers zu messen, optimale Textur Größen für die Ziel Frameraten festzulegen und die beste Methode zum Anwenden von benutzerdefinierten Shadern in Unreal herauszufinden. Alle diese vorab Produktionsarbeit wurde durchgeführt, um die Umgebung auf dem Gerät zu optimieren.

Creative Director Alex Lambert hat das Bild eingegeben, nachdem die Präproduktionsumgebung abgeschlossen wurde. Er begann mit der Betrachtung von Ford gegen Ferrari und dachte, wie eine Geschichte mit den Szenarien und Interaktionen zusammengefasst werden muss. Er hat auch visuelle Referenzen für den UI-Entwickler gesammelt, z. b. Bilder des "GT40"-Dashboards und Visualisierungen der Le Mans-Rennbahn und erfassten Audioaufzeichnungen der "GT40 in"-Aktion für den Sound-Designer.

Wenn die von Ihnen festgelegte und optimierte Präproduktionsumgebung in der Hand ist, wurde der Softwareentwickler Jose Rodriguez eingetragen, um alles zusammenzubringen. Rodriguez war Entwickler der vorherigen beiden Projekte von Unreal-on-hololens 2, die für die glückliche Fertigstellung durchgeführt wurden, bevor das mrtk für Unreal veröffentlicht wurde.

Der von mrtk für Unreal bereitgestellte Wert wurde frühzeitig ersichtlich und unterstützt Rodriguez in einer Woche dabei, einen anfänglichen Prototyp zu liefern. Er hat drei einmalige Szenarien implementiert, eine für jeden der wichtigsten Aspekte der von Lambert identifizierten, von Lambert identifizierten Aspekte: seine Schönheit, seine Leistung und seine Engineering. Für jedes Szenario hat Rodriguez den mrtk verwendet, um die optimierten 3D-Assets aus der Präproduktionsphase in verschiedene räumliche Interaktionen zu integrieren. 

Mit dem mrtk für Unreal hat Rodriguez jedes Szenario mit dem Benutzeroberflächen-Designer von Visual Unreal Motion Graphics (UMG) erstellt, anstatt alles in C++ implementieren zu müssen. Die [UX-Tools für Unreal](https://www.unrealengine.com/marketplace/product/mixed-reality-ux-tools), das Plug-in mit UX-Bausteinen und-Komponenten innerhalb von mrtk, haben ihm [Unreal Blueprints](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/index.html) für die Eingabe Simulation, visuelle Skripterstellung für Hand Interaktionen, Druck Bare Schaltflächen, 3D-Bildbearbeitung, Oberflächen Magnetismus und mehr – alles in einer nicht-Code-, Drag & Drop-Entwurfs Umgebung.

"Pre-mrtk, die Entwicklung für hololens 2 mithilfe von Unreal war etwas mühsam, da alle räumlichen Interaktionen von Hand in C++ codiert werden mussten", sagt Rodriguez. "Das mrtk für Unreal machte viele dieser Aufgaben trivial. Ich würde schätzen, dass die benötigte Zeit für den anfänglichen Prototyp in der Hälfte verkürzt wird. "

Mit einem Prototyp begann das Team wöchentliche Iterationen, um die Leistung zu verfeinern. "Dies ist der Fall, wenn das Feature für die gemischte Reality-Erfassung und das Windows-Geräte Portal wirklich hilfreich waren". "Ich habe Sie verwendet, um meine Entwurfs Überprüfungen aufzuzeichnen, mein Feedback an andere zu senden und an Änderungen zusammenzuarbeiten. Eine Isolation wie diese wäre ohne solche Tools nicht möglich. "

![Unreal Editor "Ford GT40"-App mit ausgelegter radkomponenten in der Reihenfolge](images/ford-gt40-img-04.JPG)

Da Lambert Änderungen angefordert hat, wie z. b. das Neupositionieren von Benutzeroberflächen Elementen oder das Ändern des Verhaltens einer Schaltfläche, hat Rodriguez diese Einige Änderungen erforderten kleinere Code Optimierungen, die meisten wurden im Unreal Visual Designer behandelt. "Ich war überrascht, wie schnell ich iterieren konnte", sagt Rodriguez. "Es wurde keine Zeit verschwendet. Ich würde eine Änderung im Designer vornehmen und dann auf "Play" (Wiedergabe) klicken, um die Datei sofort auf dem Gerät anzuzeigen. Die mrtk optimiert meine Arbeit wirklich. "

Rodriguez wird auch daran erinnert, dass die Produktion für alle Entwicklungs Tools durch die Produktion vorbereitet wurde. "Wir haben den ursprünglichen Prototyp durch die endgültige Produktion reibungslos fortgeführt, ohne dass wir die Dinge im Code neu implementieren oder optimieren müssen", sagt er.  

## <a name="the-final-build"></a>Der endgültige Build

"Happy Finish" hat die Produktion der Ford-Umgebung "GT40" für hololens 2 am 28. Juli 2020 abgeschlossen und bietet eine neue Perspektive auf dem legendären boocar. Die Oberfläche beginnt mit einem Willkommensbildschirm und leitet den Benutzer dann zur Einrichtung eines Ankers durch ein, indem er das Ford-Logo einrichtet und auf einer flachen Oberfläche wie einer Tabelle oder einem Desktop platziert. 

### <a name="beauty"></a>Schönes

Das **Beauty** -Segment bringt den Benutzer zu einem "GT40 Configurator", der die "GT40" auf einer drehenden sockal anzeigt, ähnlich wie ein physisches Auto in einer Auto Mobil Show angezeigt werden könnte. Der Benutzer kann verschiedene Rad Optionen anwenden, aus unterschiedlichen Farbschemas auswählen und die Türen und den trunk öffnen und schließen (oder starten, wenn er im Vereinigten Königreich aufgerufen wird). Während des gesamten Schönheits Erlebnisses kann der Benutzer das Auto übernehmen und es für eine genauere Betrachtung kostenlos bearbeiten.

![Animiertes GIF des "GT40 Configurator", der auf einem Gerät ausgeführt wird](images/ford-gt40-img-05.gif)

### <a name="performance"></a>Leistung

Das **Leistungs** Segment zeigt die Geschwindigkeit und Dauerhaftigkeit des GT40's an. Der VoiceOver erläutert zunächst, wie das Fahrzeug entwickelt wurde, und hat seine eigenen paces in der Kingman-, Arizona-Prüfseite von Ford erläutert, wobei 3D-Visualisierungen die GT40 in Bewegung im Testlauf anzeigt. Wenn die Einführung in das Leistungssegment endet, wird der Benutzer von VoiceOver aufgefordert, "auf die Schaltfläche" Le Mans "zu klicken, um die Rennstrecke zu treffen.

![Animiertes GIF der App "GT40 Speed and Dauerhaftigkeit", die auf einem Gerät ausgeführt wird](images/ford-gt40-img-06.gif)

Der zweite Teil des Leistungs Segments zeigt die GT40 unter den verschiedenen Bedingungen an, die Treiber in den 24 Stunden von Le Mans haben können. Diese werden jährlich an der Leitung de la Sari in der Nähe von Le Mans (Frankreich) aufbewahrt. Eine 3D-Ansicht zeigt das Fahrzeug in Bewegung auf der Le Mans-Spur, mit Schaltflächen, die dafür sorgen, dass das Auto schneller oder langsamer wird. Bilder des GT40's-analogen speedmessers und des tachmessers schweben oberhalb der raceansicht, wobei im Hintergrund weitere racetelemetriedaten angezeigt werden. Der Benutzer kann zwischen den Ansichten "Tag" und "Nacht" wechseln und zwischen den trocken-und nass Fahrbedingungen wechseln, um eine realistische und sehr echte Perspektive zu sehen, was Ken Meilen und die anderen, nicht im eigentlichen Wettlauf verwendeten GT40-Treiber hatten.

### <a name="engineering"></a>Entwicklung

Das **Engineering** -Segment der Ford GT40-Darstellung zeigt eine der technischen Neuerungen, mit denen sich der Wett Kampf von Ford gewinnen konnte: die Möglichkeit, Brems-und Pads in weniger als einer Minute zu ändern, im Vergleich zu den von allen anderen Teams benötigten 20-30 Minuten. Mithilfe intuitiver Gesten kann der Benutzer ein detailliertes 3D-Modell des GT40-Rades und der Brems-Assembly bearbeiten. Zum Erweitern der Assembly wählt der Benutzer einen Ziehpunkt aus, richtet ihn an der Mittelpunkt Sperre auf dem Rad aus, schaltet ihn gegen den Uhrzeigersinn um und zieht ihn dann aus dem Rad Weg. Andere Gesten werden verwendet, um die abgenutzten Brems-Rotoren und Pads zu entfernen, Sie durch neue zu ersetzen, die Assembly zu reduzieren und die mitten Sperre erneut zu sichern. Im Hintergrund zeigt ein Timer die verstrichene Zeit an, sodass der Benutzer feststellen kann, ob er den Prozess so schnell wie die boxinggruppe in Le Mans ausführen kann.

![Animiertes GIF der auf einem Gerät laufenden "GT40 Engineering"-Funktion](images/ford-gt40-img-07.gif)

Die "Ford GT40"-Oberfläche kann [aus dem Microsoft Store heruntergeladen](https://www.microsoft.com/p/ford-gt40/9p4vllktfvfp?activetab=pivot:overviewtab)werden, sodass jeder Benutzer mit hololens 2 untersuchen kann, wie die glückliche Fertigstellung eine neue Perspektive auf den legendären Rennwagen gebracht hat.

### <a name="getting-impressive-visual-fidelity"></a>Beeindruckende visuelle Treue

Obwohl der Bereich der räumlichen Interaktionen, der von der Ford-Funktion "GT40" unterstützt wird, selbst beeindruckend ist, ist die Kreativität und visuelle Darstellung, die die Benutzeroberflächen bereitstellt, das, was wirklich glänzt. Durch die Optimierung von 3D-Modellen und die Verwendung von Unreal Custom-Shadern erreicht die glückliche Fertigstellung das Ziel von 60 Frames pro Sekunde, auch wenn sich das Leistungssegment der APP mit einer Größe von 315.000 Polygonen nähert. 

"Ich bin mir sehr zufrieden, wie wir einen Satz von fließenden, intuitiven Interaktionen in eine kohärente und ansprechende Darstellung einbinden konnten," sagt Lambert. "Die Leistungsfähigkeit von Unreal Engine auf hololens 2 eröffnet eine neue Welt der Chancen für eine über rasch wirkende und faszinierende gemischte Umgebung. Nicht kompromittierte visuelle Treue ist nicht immer das Endziel für Unternehmensanwendungen auf hololens 2, aber wenn dies der Fall ist, ist die Unterstützung von Unreal auf hololens 2 äußerst wertvoll. "

### <a name="rapid-solution-delivery"></a>Schnelle Lösungs Bereitstellung

So beeindruckend die Endbenutzer-Ford-Umgebung ist, wie schnell die Übertragung abgeschlossen wurde, mit dem gesamten Projekt – von der Präproduktionsumgebung bis zur endgültigen Bereitstellung – wurde in nur 12 Wochen abgeschlossen. Zusammengefasst: das Projekt hat 1088 Stunden Arbeitsaufwand verbraucht, wie folgt aufgeschlüsselt: Creative Director (80 Stunden), UX-Designer (56 Stunden), UI-Designer (40 Stunden), Sound-Designer (40 Stunden), 3D/technische Künstlerin (328 Stunden), Softwareentwickler (408 Stunden), Technical Director (40 Stunden), Producer (56 Stunden) und Qualitätssicherung (40 Stunden).

"Insgesamt haben wir unsere ursprünglichen Projekt Schätzwerte in ziemlich naher Nähe", sagt Daniel Cheetham, Chief Innovation Officer bei Happy Finish, der die interaktive Abteilung des Unternehmens leitet. "Der Ford GT40-Vorgang ist ein Beleg dafür, dass eine hochwertige hololens 2-app in nur wenigen Monaten mit einem gering fügenden Budget abgeschlossen werden kann, aber trotzdem äußerst wirkungsvolle Ergebnisse liefert." 

Aus Sicht der Entwicklung, basierend auf der bisherigen Arbeit mit Unreal auf hololens 2, schätzt Rodriguez, dass der mrtk für Unreal die Gesamtzeit und den erforderlichen Aufwand für sein Teil der Hälfte ausschneidet. Außerdem erläutert er, wie der mrtk Entwicklern helfen kann, die noch nie mit hololens 2 mit den ersten Schritten gearbeitet haben. "Wenn andere Entwickler sagen, dass Sie an gemischter Realität interessiert sind, empfehle ich Ihnen, den hololens 2-Entwicklungs Stapel und den mrtk zu installieren. Der mrtk ermöglicht das schnelle und einfache entwickeln einer APP, und der unechte visuelle Editor funktioniert so gut, dass Sie nicht einmal ein hololens 2-Gerät benötigen, um loszulegen. Es ist überhaupt nicht kompliziert – alles funktioniert einfach. "

### <a name="potential-azure-service-enhancements"></a>Mögliche Azure-Dienst Verbesserungen

Lambert sieht auf verschiedene Weise, dass Azure Mixed Reality-Dienste verwendet werden können, um die Verwendung von Ford GT40 zu verbessern, wie z. b. die Verwendung von Azure Spatial Anchor, um eine mehr Benutzerumgebung bereitzustellen, die in der realen "Aus kreativer Sicht eröffnen räumliche Azure-Anker eine völlig neue Palette von Möglichkeiten, die Ihnen die Möglichkeit bietet, 3D-Inhalte zu ordnen, beizubehalten und wiederherzustellen.

Lambert gibt auch an, wie das Azure-Remote Rendering oder das Streaming der APP aus Azure verwendet werden kann, um die gewünschten Frameraten bei der Arbeit mit detaillierteren und komplexeren 3D-Modellen zu erzielen. "Wir mussten einige hochgradig optimierte benutzerdefinierte Shader in Unreal implementieren, um das Ziel von 60 Frames pro Sekunde zu erreichen. "Mit dem Azure-Remote Rendering könnten wir viel mehr erreichen – und es ist viel einfacher, ohne so viel Arbeit zum Optimieren von Polygon Modellen, Neuzeichnen von Textur Karten usw.

### <a name="endless-new-possibilities"></a>Unendliche neue Möglichkeiten

Was ist das nächste Mal, wenn Sie fertig sind? Das Feedback von Ford in Bezug auf die Verwendung von Ford GT40 war überaus positiv und führte zu weiteren Diskussionen zwischen der glücklichen Fertigstellung und dem Ford in zukünftigen hololens 2-Projekten. Außerhalb der Beziehung mit Ford startet die glückliche Fertigstellung bereits ein neues Projekt auf hololens 2, wobei der mrtk für Unreal ein grundlegender Baustein für die meisten Benutzeroberflächen ist. 

"Wir haben immer einen technologieunabhängigen Ansatz für jedes neue Projekt erhalten, das vorschlägt, welcher Toolsatz am besten geeignet ist, um dem Client zu helfen, die gewünschten Ergebnisse zu erzielen", sagt Cheetham. "Das heißt, hololens 2 wurde als de-facto-Gold-Standard für gemischte Realität, vor allem im Unternehmen, zu einer Spitze und Schulter über allen anderen Optionen in Bezug auf die Gerätefunktionen und die Möglichkeiten des unterstützenden Ökosystems."

Laut Cheetham hat die globale Pandemie ein riesiges neues Interesse an der immersiven gemischten Realität zwischen potenziellen Kunden geschürt. "Wir sind Beschäftigter als je zuvor, mit ungefähr 50 Prozent der potenziellen Clients, die für die Erörterung einer gemischten Reality-Option offen sind", sagt er. "Der Schlüssel besteht darin, die Benutzer zu testen. Sie können Sie über die gemischte Realität jeden Tag informieren, aber wenn Sie Sie an die Hand halten, werden Sie sofort an die Hand, wie Sie ein Spielwechsler sein können. Die Unterstützung für das Unreal Engine in hololens 2 erhöht nur den Wert, den wir anbieten können, sodass wir visuell beeindruckende Erlebnisse bereitstellen können, die auch die anspruchsvollsten Clients erfüllen. "

## <a name="try-it-out"></a>Probieren Sie es aus!

> [!div class="nextstepaction"]
> [Herunterladen der Ford GT40-App](https://www.microsoft.com/p/ford-gt40/9p4vllktfvfp)

Weitere Informationen finden Sie in der [Einführung in die Entwicklung mit gemischter Realität auf hololens 2](../development.md) oder [mrtk für Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal) auf GitHub.

<!-- ## About the team

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Jack Caron" width="60" height="60" src="images/kippys-escape/jack-caron.jpg"></td>
<td style="border-style: none"><b>Jack Caron</b><br><i>Lead Game Designer</i><br>Jack currently works on Mixed Reality experiences for Microsoft, including HoloLens 2 projects and AltspaceVR, and was previously a designer on the HoloLens platform team.</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Summer Wu" width="60" height="60" src="images/kippys-escape/summer-wu.jpg"></td>
<td style="border-style: none"><b>Summer Wu</b><br><i>Producer</i><br>Summer works on the mixed reality developer platform and heads the team’s Unreal Engine related efforts.</td>
</tr>
</table> -->