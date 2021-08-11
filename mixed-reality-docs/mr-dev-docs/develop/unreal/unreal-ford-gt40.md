---
title: Ford GT40-Erlebnis
description: Gehen Sie wie folgt vor, wenn Sie die Erstellung der Mixed Reality-Anwendung Ford GT40 mit MRTK für HoloLens 2 in Unreal untersuchen.
author: hferrone
ms.author: v-hferrone
ms.date: 3/23/2021
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Bereitstellen auf dem Gerät, PC, Dokumentation, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
appliesto:
- HoloLens 2
ms.openlocfilehash: 17314cca69148e73ee11fcd4cdc5359a5dbae4cf84b609bafb6cc75d477ec26f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200616"
---
# <a name="the-making-of-the-ford-gt40-experience"></a>Die Erstellung der Ford GT40-Benutzeroberfläche
![Herobild für Ford GT40](images/ford-gt40-hero_1920.jpg)

*"Pre-MRTK, developing for HoloLens 2 using Unreal was a bit tedious because all the spatial interactions had be coded by hand, in C++. Das MRTK für Unreal hat viele dieser Aufgaben trivial gestaltet. Ich würde schätzen, dass die für den ersten Prototyp erforderliche Zeit halbiert wurde."* – Jos Sollz, Softwareentwickler

*"Die Ford GT40-Benutzeroberfläche ist ein Beweis dafür, dass eine high-fidelity HoloLens 2-App in nur wenigen Monaten mit einem niedrigen Budget abgeschlossen werden kann, aber dennoch äußerst leistungsfähige Ergebnisse liefert."*  – Daniel Cheetham, Chief Innovation Officer, Happy Finish

Mit dem Mixed Reality Toolkit (MRTK) für Unreal lieferte das kreativ produzierende Unternehmen Happy Finish eine HoloLens 2 Erfahrung, die eine neue Perspektive auf ford GT40 bietet, das 24-Stunden-Raceauto von Le Mans!

Mithilfe einer Reihe von natürlichen und intuitiven räumlichen Interaktionen können Benutzer die Persönlichkeit, Leistung und Technik des GT40 untersuchen– alles auf eine Weise, die von der hohen visuellen Genauigkeit der Unreal-Engine profitieren kann. Die Softwareentwicklung für das gesamte Projekt wurde von einem einzelnen Entwickler in weniger als drei Monaten abgeschlossen, was durch MRTK für die visuelle Skript- und Entwurfsumgebung von Unreal ermöglicht wurde.

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>Herunterladen der App aus Microsoft Store in HoloLens 2
Wenn Sie über HoloLens 2 Gerät verfügen, können Sie die App direkt herunterladen und auf Ihrem Gerät installieren.

<a href='//www.microsoft.com/store/apps/9p4vllktfvfp?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>


## <a name="the-ask"></a>Die Frage

Happy Finish ist eines der weltweit führenden Produktionsunternehmen mit einer Kundenbasis, zu der Ford, Microsoft, Gilt, Netflix, Dsl und andere Namen gehören. Das Unternehmen begann als High-End-Fotoretouch-Agentur, die sich in Film und CGI verzweigte, bevor es seine Leidenschaft auf erstklassiges immersives Storying mit räumlichem 3D-Design und Interaktion ausdehnte.

Mitte 2020 näherte sich Microsoft Happy Finish, um eine Demo-App zu erstellen, mit der die Möglichkeiten vorgestellt werden können, die das neue Mixed Reality Toolkit (MRTK) für Unreal bietet, das auf der Unterstützung für HoloLens 2 in der Unreal-Engine aufbaut. An diesem Punkt verfügte das Unternehmen bereits über zwei erfolgreiche Unreal-on-HoloLens 2-Projekte. Beides gilt für eine global bekannte Consumermarke, die unreal auf HoloLens 2 für ein internes R&D/B2B-Vertriebstool für seine hohe visuelle Genauigkeit ausgewählt hat, da dies erforderlich ist, um die eigenen High-End-Produkte dieses Kunden optimal zu präsentieren.

Obwohl die Lösung selbst dem Happy Finish überlassen würde, musste sie einige wichtige Richtlinien erfüllen. Zunächst musste sich das Unternehmen auf ein Unternehmensszenario konzentrieren, um den Nutzen von Unreal für HoloLens 2 außerhalb der Spielebranche zu veranschaulichen. Zweitens musste es gerätegeschützt sein, was bedeutet, dass es als eigenständige Demo dienen konnte– ohne eine Netzwerkverbindung und externe Verarbeitungsleistung, um die Zielframeraten und die visuelle Qualität zu erhalten. Drittens sollte die Bandbreite intuitiver Interaktionen, die vom MRTK unterstützt werden, zu einer nahtlosen und natürlichen Erfahrung kombiniert werden. Schließlich sollte die vorgeschlagene Lösung die inhärente visuelle Genauigkeit und andere Vorteile der Unreal Engine selbst zeigen, z. B. die Effizienz von Shadern. 

Angesichts dieser Richtlinien begann Happy Finish mit dem Brainstorming der Möglichkeiten und kam auf die Idee einer Mixed Reality-Erfahrung, bei der die räumliche Interaktion genutzt wurde, um den Wert eines hochwertigen Markenprodukts zu kommunizieren. Nach der Berücksichtigung einer Reihe von Objekten, die Uhren, Kameras, Autos und private Jets umfassten, entscheidet sich Happy Finish letztendlich für den Ford GT40, eine Automobillegende, die 1966, als Ford während der 24 Stunden von Le Mans geplaudert hat, eine Automobillegende erlangte, die im Blockbuster-Film Ford vs. Sender 2019 zu sehen war. 

Nach dem Erwerb des Buy-Ins von Ford, einem vorhandenen Happy Finish-Client, hat das Unternehmen eine neue Perspektive auf das klassische Automobilsymbol geliefert.

## <a name="the-solution"></a>Die Lösung

Die Arbeit begann am 7. Mai 2020. Nach dem Abrufen der GT40-Modelldateien hat ein 3D-Interpret drei Wochen damit verbracht, Polygonmodelle zu optimieren, UV-Zuordnungen zu erstellen, Texturkarten neu zu gezeichnet und diese Karten in so wenige Texturen wie möglich zu verdichten. Ein technischer Techniker hat parallel daran gearbeitet, die Ausgabe des 3D-Interpreten zu vergleichen, optimale Texturgrößen anhand der Zielframeraten zu bestimmen und die beste Methode zum Anwenden von benutzerdefinierten Shadern in Unreal zu ermitteln. All diese Vorproduktionsvorgänge wurden durchgeführt, um die Benutzerfreundlichkeit auf dem Gerät zu optimieren.

Creative Director Alex Lambert hat das Bild eingegeben, nachdem die Vorproduktion abgeschlossen wurde. Er begann damit, Ford und Einem zu beobachten und darüber nachzudenken, wie eine Geschichte um die Szenarien und Interaktionen verwebt werden kann. Er sammelte auch visuelle Verweise für den Ui-Interpreten, z. B. Bilder des GT40-Dashboards und Visuals der Le Mans-Racespur, und sammelte Audioaufzeichnungen des GT40 in Aktion für den Sound-Designer.

Mit den definierten und optimierten Präproduktionsressourcen in der Geschichte wurde der Entwickler der Software, Jos Msiz, eingetragen, um alles zusammenzuführen. Er war der Entwickler der beiden vorherigen Unreal-on-HoloLens 2-Projekte, die Happy Finish ausgeführt hatte, bevor das MRTK für Unreal veröffentlicht wurde.

Der wert, der vom MRTK für Unreal bereitgestellt wurde, wurde früh offensichtlich und half Dannz, einen ersten Prototyp in einer Woche bereitzustellen. Er implementierte drei einzigartige Szenarien, eines für jeden der wichtigsten Aspekte des GT40, die Lambert identifiziert hatte: seine Leistung, seine Leistung und seine Entwicklung. Für jedes Szenario hat Sichz das MRTK verwendet, um die optimierten 3D-Ressourcen aus der Präproduktionsphase in eine Reihe räumlicher Interaktionen zu integrieren. 

Mit dem MRTK für Unreal hat Sichz jedes Szenario mit dem visuellen UMG-UI-Designer (Unreal Motion Graphics) erstellt, anstatt alles in C++ implementieren zu müssen. [UX Tools for Unreal](https://www.unrealengine.com/marketplace/product/mixed-reality-ux-tools), the plug-in containing UX building blocks and components within the MRTK, gave him [Unreal Blueprints](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/index.html) for input simulation, visually scripting hand interactions, pressable buttons, 3D image manipulation, surface magnetism, and more—all within a no-code, drag-and-drop design environment.

"Pre-MRTK, developing for HoloLens 2 using Unreal was a bit tedious because all of the spatial interactions had to be coded by hand, in C++", saysZähler. "Das MRTK für Unreal hat viele dieser Aufgaben trivial gestaltet. Ich würde schätzen, dass sich die für den ersten Prototyp erforderliche Zeit halbiert hat."

Mit einem Prototyp in der Hand begann das Team wöchentliche Iterationen, um die Erfahrung zu verfeinern. "Dies ist der Zeitpunkt, an dem das feature Mixed Reality-Aufnahme und die Windows Geräteportal sehr hilfreich wurden", erinnert sich Lambert. "Ich habe sie verwendet, um meine Entwurfsüberprüfungen zu erfassen, mein Feedback an andere zu senden und an Änderungen zusammenzuarbeiten. So isoliert zu arbeiten, wäre ohne solche Tools nicht möglich gewesen."

![Unreal-Editor: Ford GT40-App, die mit nacheinander angeordneten Radkomponenten ausgeführt wird](images/ford-gt40-img-04.JPG)

Als Lambert Änderungen anforderte, z. B. das Neupositionieren von Benutzeroberflächenelementen oder das Ändern des Verhaltens einer Schaltfläche, implementierte Sie diese. Während einige der Änderungen kleine Codeanpassungen erforderten, wurden die meisten im visuellen Unreal-Designer verarbeitet. "Ich war überraschend, wie schnell ich iterieren konnte", sagt Derz. "Es wurde keine Zeit verschwendet. Ich würde eine Änderung im Designer vornehmen und dann die Wiedergabe drücken, um sie sofort auf dem Gerät anzuzeigen. Das MRTK hat meine Arbeit optimiert."

Außerdem ist Ermeinung darüber, wie produktionsbereit alle Entwicklungstools waren. "Wir haben einen reibungslosen Verlauf vom ersten Prototyp bis zur endgültigen Produktion erzielt, ohne dass wir zurückkommen und die Dinge im Code neuimplementieren oder optimieren mussten", sagt er.  

## <a name="the-final-build"></a>Der endgültige Build

Happy Finish hat die Produktion der Ford GT40 Experience für HoloLens 2 am 28. Juli 2020 abgeschlossen und bietet eine neue Perspektive auf das 2010-Raceauto. Die Benutzeroberfläche beginnt mit einem Begrüßungsbildschirm und führt den Benutzer dann zum Einrichten eines Ankers, indem er das Ford-Logo greift und es auf einer flachen Oberfläche wie einer Tabelle oder einem Desktop platziert. 

### <a name="beauty"></a>Schönheit

Mit dem **Segment "Fahrt"** gelangen Benutzer zu einem GT40-Konfigurator, der den GT40 auf einem rotierenden Gitter anzeigt, ähnlich wie ein physisches Auto auf einer Automobilschau angezeigt werden kann. Der Benutzer kann verschiedene Radoptionen anwenden, aus verschiedenen Farbschemas auswählen und die Türen und den Trunk öffnen und schließen (oder boot, wie er es im Vereinigten Königreich genannt wird). Während der gesamten Erfahrung kann der Benutzer das Auto abholen und frei bearbeiten, um es genauer zu betrachten.

![Animierte GIF-Datei des GT40-Konfigurators, der auf einem Gerät ausgeführt wird](images/ford-gt40-img-05.gif)

### <a name="performance"></a>Leistung

Das **Leistungssegment** zeigt die Geschwindigkeit und Dauerhaftigkeit des GT40. Der Voiceover beginnt damit, zu beschreiben, wie das Auto entwickelt wurde und wie es bei Ford es Kingman, Arizona, 2016 aufspürt, mit 3D-Visuals, die den GT40 in Bewegung auf der Testspur zeigen. Wenn die Einführung in das Leistungssegment abgeschlossen ist, fordert der Voiceover den Benutzer auf, "Die Le Mans-Schaltfläche zu drücken, um die Racetrack zu drücken".

![Animierte GIF-Datei der Auf einem Gerät ausgeführten App für Geschwindigkeit und Dauerhaftigkeit GT40](images/ford-gt40-img-06.gif)

Im zweiten Teil des Leistungssegments wird der GT40 unter den Verschiedenen Bedingungen vorgestellt, die Treiber bei den 24 Stunden von Le Mans erleben können, die jährlich auf der Circuit de la Sarthe in der Nähe von Le Mans, Frankreich, stattfinden. Eine 3D-Ansicht zeigt das Auto in Bewegung auf der Le Mans-Spur mit Schaltflächen, mit deren Hilfe das Auto schneller oder langsamer fahren kann. Bilder des analogen Speedometers und Tachometers des GT40 über der Racetrackansicht, wobei im Hintergrund mehr Racetelemetrie angezeigt wird. Der Benutzer kann zwischen Tages- und Nachtansichten sowie zwischen den Bedingungen für das verregnete und verregnete Fahren wechseln und so eine realistische und realistische Perspektive dafür bieten, was Ken Miles und die anderen GT40-Fahrer im eigentlichen Race erleben.

### <a name="engineering"></a>Entwicklung

Das **Engineering-Segment** der Ford GT40-Benutzeroberfläche zeigt eine der Technischen Innovationen, die Ford dabei halfen, das Race zu gewinnen: die Möglichkeit, die Beläge und Pads in weniger als einer Minute zu ändern, im Vergleich zu den 20 bis 30 Minuten, die von allen anderen Teams benötigt werden. Mithilfe intuitiver Gesten kann der Benutzer ein detailliertes 3D-Modell der GT40-Rad- und -Unterbauassembly bearbeiten. Um die Assembly zu erweitern, nimmt der Benutzer einen Lugschlüssel entgegen, richtet ihn an der Mittleren Sperre des Rads aus, schaltet ihn gegen den Uhrzeigersinn um und entfernt ihn dann vom Rad. Andere Gesten werden verwendet, um die Ähren und Pads zu entfernen, sie durch neue zu ersetzen, die Assembly zu reduzieren und die Mittlere Sperre zu sichern. Im Hintergrund zeigt ein Timer die verstrichene Zeit an, sodass der Benutzer sehen kann, ob er den Prozess so schnell abschließen kann wie die Grubenbesatzung in Le Mans.

![Animierte GIF-Datei der GT40-Entwicklungserfahrung, die auf einem Gerät ausgeführt wird](images/ford-gt40-img-07.gif)

Die Ford GT40 Experience kann [aus dem Microsoft Store heruntergeladen](https://www.microsoft.com/p/ford-gt40/9p4vllktfvfp?activetab=pivot:overviewtab)werden, sodass jeder mit einem HoloLens 2 untersuchen kann, wie Happy Finish eine neue Perspektive für das Raceauto geschaffen hat.

### <a name="getting-impressive-visual-fidelity"></a>Erhalten von beeindruckender visueller Genauigkeit

Während die von der Ford GT40-Erfahrung unterstützten räumlichen Interaktionen eigenständig überzeugend sind, ist die Schaffens- und visuelle Genauigkeit, die die Erfahrung bietet, das, was sie wirklich ausmacht. Durch die Optimierung von 3D-Modellen und die Verwendung von benutzerdefinierten Unreal-Shadern erreicht Happy Finish das Ziel von 60 Frames pro Sekunde, selbst wenn das Leistungssegment der App 315.000 Polygone erreicht. 

"Ich bin sehr zufrieden damit, wie wir eine Reihe von fließenden, intuitiven Interaktionen zu einer zusammenhängenden und ansprechenden Geschichte zusammenbringen konnten", sagt Lambert. "Die Leistungsfähigkeit der Unreal-Engine auf HoloLens 2 öffnet eine neue Welt von Möglichkeiten für überraschendere und interessantere Mixed Reality-Erfahrungen. Nicht vertrauenswürdige visuelle Genauigkeit ist nicht immer das Endziel für Unternehmensanwendungen auf HoloLens 2, aber wenn dies der Anfang ist, ist die Unterstützung für Unreal auf HoloLens 2 nicht mehr wichtig."

### <a name="rapid-solution-delivery"></a>Schnelle Lösungsbereitstellung

So überzeugend wie die Ford GT40 Experience des Endbenutzers ist, wie schnell Happy Finish das Projekt mit dem gesamten Projekt – von der Präproduktion bis zur endgültigen Übermittlung – in knapp 12 Wochen abgeschlossen hat. Zusammenfassend hat das Projekt 1.088 Stunden Aufwand verbraucht, unterteilt wie folgt: Creative Director (80 Stunden), UX-Designer (56 Stunden), UI-Designer (40 Stunden), Sounddesigner (40 Stunden), 3D/Technischer Interpret (328 Stunden), Softwareentwickler (408 Stunden), technischer Leiter (40 Stunden), Producer (56 Stunden) und Qualitätssicherung (40 Stunden).

"Insgesamt sind wir unseren ursprünglichen Projektschätzungen sehr nahe gekommen", sagt Daniel Cheetham, Chief Innovation Officer bei Happy Finish, der die interaktive Abteilung des Unternehmens leitet. "Die Ford GT40-Erfahrung ist ein Beweis dafür, dass eine high-fidelity HoloLens 2 App in nur wenigen Monaten mit einem geringen Budget abgeschlossen werden kann, aber dennoch äußerst leistungsfähige Ergebnisse liefert." 

Aus Entwicklungssicht schätzt Erz basierend auf seiner bisherigen Erfahrung mit Unreal auf HoloLens 2, dass das MRTK für Unreal die gesamt erforderliche Zeit und den Aufwand seiner Hälfte reduziert hat. Außerdem stellt er fest, wie das MRTK Entwicklern helfen kann, die noch nie mit HoloLens 2 gearbeitet haben. "Wenn andere Entwickler sagen, dass sie an Mixed Reality interessiert sind, ermutige ich ihnen, einfach zu springen, den HoloLens 2 Entwicklungsstapel und MRTK zu installieren und zu verwenden. Das MRTK macht das Erstellen einer App schnell und einfach, und der visuelle Unreal-Editor funktioniert so gut, dass Sie nicht einmal ein HoloLens 2 Gerät benötigen, um zu beginnen. Es ist überhaupt nicht kompliziert– alles funktioniert einfach."

### <a name="potential-azure-service-enhancements"></a>Potenzielle Verbesserungen des Azure-Diensts

Lambert sieht mehrere Möglichkeiten, wie Azure Mixed Reality-Dienste verwendet werden können, um die Ford GT40-Erfahrung zu verbessern, z. B. die Verwendung von Azure Spatial Anchors, um eine in der realen Welt verankerte Benutzeroberfläche mit mehreren Benutzern bereitzustellen. "Aus kreativer Perspektive eröffnet Azure Spatial Anchors eine völlig neue Palette von Möglichkeiten durch die Möglichkeit, 3D-Inhalte oder Points of Interest innerhalb unserer physischen Welt zu zuordnen, dauerhaft zu erhalten und wiederherzustellen", sagt er.

Lambert erfände sich auch, Azure Remote Rendering oder das Streamen der App aus Azure verwendet werden könnte, um gewünschte Frameraten zu erzielen und gleichzeitig mit detaillierteren und komplexeren 3D-Modellen zu arbeiten. "Wir mussten einige hochgradig optimierte benutzerdefinierte Shader in Unreal implementieren, um unser Geräteziel von 60 Frames pro Sekunde zu erreichen", erklärt er. "Mit Azure Remote Rendering könnten wir viel mehr tun – und das viel einfacher, ohne dass so viel Arbeit erforderlich ist, um Polygonmodelle zu optimieren, Texturzuordnungen neu zu anpainten und so weiter."

### <a name="endless-new-possibilities"></a>Endlose neue Möglichkeiten

Wie geht es nun mit Happy Finish weiter? Das Ford-Feedback zur Ford GT40-Erfahrung war überaus positiv, was zu weiteren Diskussionen zwischen Happy Finish und Ford zu zukünftigen HoloLens 2 geführt hat. Außerhalb seiner Beziehung zu Ford startet Happy Finish bereits ein neues Projekt auf HoloLens 2, wobei das MRTK für Unreal ein grundlegendes Baustein für die meisten Benutzererfahrungen sein wird. 

"Wir haben immer einen technologieunabhängigen Ansatz für jedes neue Projekt verfolgt, indem wir uns vorgebe, welcher Toolsatz am besten geeignet ist, um dem Client zu helfen, die gewünschten Ergebnisse zu erzielen", sagt Tscheetham. "Das heißt, HoloLens 2 hat sich als de-facto-Goldstandard für Mixed Reality entwickelt, insbesondere im Unternehmen, das kopf-und-bei-kopf über allen anderen Optionen in Bezug auf die Gerätefunktionen und die Durchdringlichkeit des unterstützenden Ökosystems steht."

Laut Tscheetham hat die globale Pandemie ein enormes neues Interesse an immersiver Mixed Reality unter potenziellen Kunden angeseutet. "Wir sind so viel wie noch nie, da etwa 50 Prozent der potenziellen Clients offen sind, über eine Mixed Reality-Option zu sprechen", sagt er. "Der Schlüssel besteht im Versuch, dies auszuprobieren. Sie können ihnen den ganzen Tag etwas über Mixed Reality mitteilen, aber wenn Sie ihnen ein HoloLens 2 zur Selbsterfahrung geben, erhalten sie sofort, wie es ein Spielveränderungs-Können sein kann. Die Unterstützung für unreal engine in HoloLens 2 erhöht nur den Wert, den wir anbieten können, sodass wir visuell beeindruckende Umgebungen bieten können, die auch die anspruchsvollsten Clients erfüllen."

## <a name="try-it-out"></a>Probieren Sie es aus!

> [!div class="nextstepaction"]
> [Herunterladen der Ford GT40-App](https://www.microsoft.com/p/ford-gt40/9p4vllktfvfp)

Sehen Sie sich [unsere Einführung in Mixed Reality Entwicklung auf HoloLens 2](../development.md) oder [MRTK für Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal) auf GitHub.

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