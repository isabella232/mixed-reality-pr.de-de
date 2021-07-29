---
title: Ford GT40-Erlebnis
description: Sehen Sie sich die Entwicklung der Mixed Reality-Anwendung Ford GT40 mit MRTK für HoloLens 2 in Unreal an.
author: hferrone
ms.author: v-hferrone
ms.date: 3/23/2021
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Bereitstellen auf gerät, PC, Dokumentation, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
appliesto:
- HoloLens 2
ms.openlocfilehash: e634d75af92509372209d8e7c0cde2833127c128
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757196"
---
# <a name="the-making-of-the-ford-gt40-experience"></a>Die Herstellung der Ford GT40-Erfahrung
![Ford GT40-Herobild](images/ford-gt40-hero_1920.jpg)

*"Vor dem MRTK war die Entwicklung für HoloLens 2 mit Unreal etwas mühsam, da alle räumlichen Interaktionen in C++ von Hand codiert werden mussten. Das MRTK für Unreal hat viele dieser Aufgaben trivial gemacht. Ich würde schätzen, dass die Zeit, die für den anfänglichen Prototyp erforderlich ist, halb so lange geschneidert wurde."* – Jose Beim Softwareentwickler

*"Die Ford GT40-Erfahrung ist ein Beweis dafür, dass eine HoloLens 2-App mit hoher Genauigkeit in nur wenigen Monaten mit einem moderaten Budget abgeschlossen werden kann, aber dennoch sehr gute Ergebnisse liefert."*  – Daniel Tscheetham, Chief Innovation Officer, Happy Finish

Mithilfe des Mixed Reality Toolkits (MRTK) für Unreal lieferte das kreative Produktionsunternehmen Happy Finish eine HoloLens 2-Erfahrung, die eine neue Perspektive auf den Ford GT40 bietet, den 24 Stunden von Le Mans überrennten Rasenwagen.

Mithilfe einer Reihe von natürlichen und intuitiven räumlichen Interaktionen können Benutzer die Gt40-Klasse, die Leistung und die Technik erkunden– alles auf eine Weise, die von der hohen visuellen Genauigkeit der Unreal Engine profitieren kann. Die Softwareentwicklung für das gesamte Projekt wurde von einem einzelnen Entwickler in weniger als drei Monaten abgeschlossen, was durch MRTK für die visuelle Skripterstellung und Entwurfsumgebung von Unreal ermöglicht wurde.

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>Laden Sie die App Microsoft Store in HoloLens 2
Wenn Sie über HoloLens 2 verfügen, können Sie die App direkt herunterladen und auf Ihrem Gerät installieren.

<a href='//www.microsoft.com/store/apps/9p4vllktfvfp?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>


## <a name="the-ask"></a>Die Frage

Happy Finish ist eines der weltweit führenden Produktionsunternehmen für die Produktion mit einer Kundenbasis, die Ford, Microsoft,Client, Netflix, Netflix und andere Hausnamen umfasst. Das Unternehmen wurde als High-End-Foto-Retouch-Agentur gestartet und verzweigte sich in Film und CGI, bevor es seine Kompetenz in immersiven Immersive-Immersive-Designs mit 3D-Raumdesign und -interaktion erweitert hat.

Mitte 2020 näherte sich Microsoft Happy Finish an, um eine Demo-App zu erstellen, die dabei helfen könnte, die Möglichkeiten zu präsentieren, die das neue Mixed Reality Toolkit (MRTK) für Unreal bietet, das auf der Unterstützung für HoloLens 2 in der Unreal Engine aufbaut. An diesem Punkt hatte das Unternehmen bereits zwei erfolgreiche Unreal-on-HoloLens 2-Projekte im Blick. Beide waren für eine global erkannte Verbrauchermarke, die unreal on HoloLens 2 für ein internes R&D/B2B-Vertriebstool für seine hohe visuelle Genauigkeit ausgewählt hat, da dies erforderlich ist, um die eigenen High-End-Produkte des Kunden am besten zu präsentieren.

Obwohl die Lösung selbst dem Happy Finish über gelassen würde, musste sie einige wichtige Richtlinien erfüllen. Zunächst musste er sich auf ein Unternehmensszenario konzentrieren, um den Nutzen von Unreal auf HoloLens 2 außerhalb der Spielebranche zu veranschaulichen. Zweitens musste es nur gerätegeeigen sein, was bedeutet, dass es als eigenständige Demo dienen konnte– ohne dass eine Netzwerkverbindung und externe Verarbeitungsleistung erforderlich sind, um die Zielframeraten und die visuelle Qualität zu erhalten. Drittens sollte die Bandbreite intuitiver Interaktionen, die vom MRTK unterstützt werden, in ein nahtloses und natürliches Erlebnis kombiniert werden. Schließlich sollte die vorgeschlagene Lösung die inhärente visuelle Genauigkeit und andere Vorteile der Unreal Engine selbst, z. B. die Effizienz von Shadern, zeigen. 

Angesichts dieser Richtlinien begann Happy Finish mit dem Brainstorming der Möglichkeiten und kam auf die Idee für eine Mixed Reality-Erfahrung, die räumliche Interaktion verwendet hat, um den Wert eines hochwertigen Markenprodukts zu kommunizieren. Nach Berücksichtigung einer Reihe von Objekten, die Uhren, Kameras, Autos und private Jets umfassten, hat sich Happy Finish schließlich für den Ford GT40 entschieden, eine Automobillegende, die 1966 Bekanntheit erreicht hat, als Ford bei den 24 Stunden von Le Mans die Welt erklang– wie im Blockbuster-Film Ford im Vergleich zu Denen von 2019 gezeigt. 

Nach dem Erwerb des Kaufs von Ford, einem vorhandenen Happy Finish-Client, hat das Unternehmen eine neue Perspektive auf das klassische Automobilsymbol entwickelt.

## <a name="the-solution"></a>Die Lösung

Die Arbeit begann am 7. Mai 2020. Nach dem Abrufen der GT40-Modelldateien hat ein 3D-Interpret drei Wochen damit verbracht, Polygonmodelle, DIE UV-Zuordnung, das Neupaintieren von Texturzuordnungen und das Verdichten dieser Karten in möglichst wenigen Texturen zu optimieren. Ein technischer Interpret hat parallel daran gearbeitet, einen Vergleich der Ausgabe des 3D-Interpreten zu erstellen, optimale Texturgrößen für die Zielframeraten zu bestimmen und die beste Methode zum Anwenden benutzerdefinierter Shader in Unreal zu ermitteln. All diese Präproduktionsarbeit wurde durchgeführt, um die Benutzererfahrung auf dem Gerät zu optimieren.

Creative Director Alex Lambert hat das Bild nach Abschluss der Präproduktionsarbeit eingegeben. Er begann mit dem Ansehen von Ford im Vergleich zu Einer und überlegte, wie eine Geschichte um die Szenarien und Interaktionen miteinander verwebt werden kann. Außerdem sammelte er visuelle Verweise für den Ui-Interpreten, z. B. Bilder des GT40-Dashboards und Visuals der Le Mans-Racetrack, und sammelte Audioaufzeichnungen des GT40 in Aktion für den Sound-Designer.

Da die geschichtet definierten und optimierten Präproduktionsressourcen zur Hand waren, wurde der Softwareentwickler Der Softwareentwickler Solle wurde eingetragen, um alles zusammenzubringen. Er war der Entwickler der beiden vorherigen Unreal-on-HoloLens 2-Projekte, die Happy Finish durchgeführt hatte, bevor das MRTK für Unreal veröffentlicht wurde.

Der vom MRTK für Unreal bereitgestellte Wert wurde früh deutlich und hilft Dabei, einen ersten Prototyp in einer Woche zu erstellen. Er implementierte drei einzigartige Szenarios: eines für jeden der wichtigsten Aspekte des GT40, den Lambert identifiziert hat: seine Leistung, seine Leistung und sein Engineering. Für jedes Szenario verwendete Erding das MRTK, um die optimierten 3D-Objekte aus der Präproduktionsphase in eine Reihe von räumlichen Interaktionen zu integrieren. 

Mit dem MRTK für Unreal wurde jedes Szenario mithilfe des visuellen UMG-UI-Designers (Unreal Motion Graphics) erstellt, anstatt alles in C++ implementieren zu müssen. [UX Tools for Unreal](https://www.unrealengine.com/marketplace/product/mixed-reality-ux-tools), the plug-in containing UX building blocks and components within the MRTK, gave him [Unreal Blueprints](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/index.html) for input simulation, visually scripting hand interactions, pressable buttons, 3D image manipulation, surface magnetism, and more—all within a no-code, drag-and-drop design environment.

"Pre-MRTK, developing for HoloLens 2 using Unreal was a bit tedious because all the spatial interactions to be coded by hand, in C++" (Vor-MRTK, entwickeln für HoloLens 2 mit Unreal war etwas mühsam, da alle räumlichen Interaktionen in C++ von Hand codiert werden mussten.) "Das MRTK für Unreal hat viele dieser Aufgaben trivial gemacht. Ich würde schätzen, dass die Zeit, die für den anfänglichen Prototyp erforderlich ist, halb so lange geschneidert wurde."

Mit einem Prototyp begann das Team wöchentliche Iterationen, um die Benutzererfahrung zu verfeinern. "Dies ist der Fall, Mixed Reality-Aufnahme Feature und die Windows Geräteportal sehr hilfreich wurden", erinnert sich Lambert. "Ich habe sie verwendet, um meine Entwurfsüberprüfungen zu erfassen, mein Feedback an andere zu senden und an Änderungen zusammenzuarbeiten. Eine solche Isolation wäre ohne solche Tools nicht möglich gewesen."

![Unreal-Editor: Ford GT40-App, die mit nacheinander ausgelegten Radkomponenten ausgeführt wird](images/ford-gt40-img-04.JPG)

Als Lambert Änderungen anfragte, z. B. das Neupositionieren von Benutzeroberflächenelementen oder das Ändern des Verhaltens einer Schaltfläche, wurden sie von Lambert implementiert. Während einige der Änderungen kleine Codeänderungen erforderten, wurden die meisten davon im visuellen Unreal-Designer verarbeitet. "Ich war überraschend, wie schnell ich iterieren konnte", sagt Denn. "Es wurde keine Zeit verschwendet. Ich würde den Designer ändern und dann die Wiedergabe drücken, um ihn sofort auf dem Gerät zu sehen. Das MRTK hat meine Arbeit optimiert."

Außerdem erinnern wir uns daran, wie produktionsbereit alle Entwicklungstools waren. "Wir haben uns vom ersten Prototyp bis zur endgültigen Produktion reibungslos entwickelt, ohne dass wir die Dinge im Code erneut ausführen oder optimieren müssen", sagt er.  

## <a name="the-final-build"></a>Der endgültige Build

Happy Finish hat die Produktion von Ford GT40 Experience for HoloLens 2 am 28. Juli 2020 abgeschlossen und eine neue Perspektive auf das 28. Juli 2020 gegeben. Die Benutzeroberfläche beginnt mit einem Begrüßungsbildschirm und führt den Benutzer dann an, einen Anker zu erstellen, indem er das Ford-Logo greift und es auf einer flachen Oberfläche wie einer Tabelle oder einem Desktop platziert. 

### <a name="beauty"></a>Schönheit

Das **Segment "2"** bringt den Benutzer zu einem GT40-Konfigurator, der den GT40 auf einem rotierenden Profil anzeigt, ähnlich wie ein physisches Auto auf einer Automobilschau angezeigt werden könnte. Der Benutzer kann verschiedene Radoptionen anwenden, aus verschiedenen Farbschemas auswählen und die Türen und den Kofferraum öffnen und schließen (oder den Kofferraum, wie er es im Vereinigten Königreich nennen). Während der gesamten Benutzeroberfläche kann der Benutzer das Auto auswählen und frei bearbeiten, um es genauer zu betrachten.

![Animiertes GIF des GT40-Konfigurators, das auf einem Gerät ausgeführt wird](images/ford-gt40-img-05.gif)

### <a name="performance"></a>Leistung

Das **Leistungssegment** zeigt die Geschwindigkeit und Dauerhaftigkeit des GT40. Der Voiceover beginnt damit, zu beschreiben, wie das Auto entwickelt wurde und sein Tempo bei Ford es Kingman, Arizona- erweist sich als Zeichner, mit 3D-Visuals, die den GT40 in Bewegung auf der Testspur zeigen. Wenn die Einführung in das Leistungssegment endet, fordert der Voiceover den Benutzer auf, "Die Le Mans-Schaltfläche zu drücken, um die Racetrack zu treffen."

![Animiertes GIF der auf einem Gerät ausgeführten Gt40-App für Geschwindigkeit und Dauerhaftigkeit](images/ford-gt40-img-06.gif)

Der zweite Teil des Leistungssegments zeigt den GT40 unter den verschiedenen Bedingungen, die Treiber bei den 24 Stunden von Le Mans erleben können, die jährlich auf der Circuit de la Sarthe in der Nähe von Le Mans, Frankreich, stattfinden. In einer 3D-Ansicht wird das Auto auf der Le Mans-Spur in Bewegung angezeigt, und es werden Schaltflächen bereitgestellt, um das Auto schneller oder langsamer zu machen. Bilder des analogen Geschwindigkeitsmessers und Tachometers des GT40 gleiten über der Racetrackansicht, und im Hintergrund werden mehr Racetelemetriedaten angezeigt. Der Benutzer kann zwischen Tages- und Nachtansichten und zwischen den Bedingungen für die Fahrt mit dem Wasser und dem Versendungsverhalten umschalten und so eine realistische und lebensähnliche Perspektive auf das bieten, was Ken Miles und die anderen GT40-Fahrer im eigentlichen Race gesehen haben.

### <a name="engineering"></a>Entwicklung

Das **Engineering-Segment** der Ford GT40 Experience zeigt eine der technischen Innovationen, die Ford dabei halfen, das Race zu gewinnen: die Fähigkeit, Beläge und Pads in weniger als einer Minute zu ändern, im Vergleich zu den 20 bis 30 Minuten, die von allen anderen Teams benötigt werden. Mithilfe intuitiver Gesten kann der Benutzer ein detailliertes 3D-Modell der GT40-Rad- und Derbebauung bearbeiten. Um die Assembly zu erweitern, wählt der Benutzer einen Lugschlüssel aus, richtet ihn an der Zentrierung des Rads aus, schaltet ihn gegen den Uhrzeigersinn und zieht ihn dann vom Rad weg. Andere Gesten werden verwendet, um die Stürzte und Pads zu entfernen, durch neue zu ersetzen, die Assembly zu reduzieren und die Zentrierungssperre zu sichern. Im Hintergrund zeigt ein Timer die verstrichene Zeit an, damit der Benutzer erkennen kann, ob er den Prozess so schnell abschließen kann wie das Pit-Team in Le Mans.

![Animiertes GIF der GT40-Entwicklungserfahrung, die auf einem Gerät ausgeführt wird](images/ford-gt40-img-07.gif)

Die Ford GT40 Experience kann aus dem [Microsoft Store](https://www.microsoft.com/p/ford-gt40/9p4vllktfvfp?activetab=pivot:overviewtab)heruntergeladen werden, sodass jeder mit einem HoloLens 2 untersuchen kann, wie Happy Finish eine neue Perspektive in das Raceauto gebracht hat.

### <a name="getting-impressive-visual-fidelity"></a>Erhalten von beeindruckender visueller Genauigkeit

Die Bandbreite der räumlichen Interaktionen, die von ford GT40 Experience unterstützt werden, ist zwar von selbst beeindruckender Art, aber die Kreativität und visuelle Genauigkeit, die die Erfahrung bietet, ist das, was sie wirklich zum Glänzen macht. Durch die Optimierung von 3D-Modellen und die Verwendung von benutzerdefinierten Unreal-Shadern hat Happy Finish sein Ziel von 60 Frames pro Sekunde erreicht, auch wenn das Leistungssegment der App 315.000 Polygone nähert. 

"Ich bin sehr zufrieden, wie wir eine Reihe von fließenden, intuitiven Interaktionen zu einer stimmigen und ansprechenden Geschichte zusammenbringen konnten", sagt Lambert. "Die Leistung der Unreal Engine auf HoloLens 2 eröffnet eine neue Welt der Möglichkeiten für überraschende und spannende Mixed Reality-Erfahrungen. Unkompromromisierte visuelle Genauigkeit ist nicht immer das Endziel für Unternehmensanwendungen auf HoloLens 2, aber wenn dies der Wert ist, wird die Unterstützung für Unreal auf HoloLens 2 sehr wertvoll."

### <a name="rapid-solution-delivery"></a>Schnelle Lösungsbereitstellung

So überzeugend wie der Endbenutzer Ford GT40 Experience ist, wie schnell Happy Finish es mit dem gesamten Projekt – von der Präproduktion bis zur endgültigen Bereitstellung – innerhalb von knapp 12 Wochen geliefert hat. Zusammenfassend hat das Projekt 1.088 Stunden Arbeit verbraucht und ist wie folgt aufgeschlüsselt: Creative Director (80 Stunden), UX-Designer (56 Stunden), UI-Designer (40 Stunden), Sounddesigner (40 Stunden), 3D/Technical Art (328 Stunden), Softwareentwickler (408 Stunden), technischer Leiter (40 Stunden), Producer (56 Stunden) und Qualitätssicherung (40 Stunden).

"Insgesamt sind wir unseren ursprünglichen Projektschätzungen sehr nahe gekommen", sagt Daniel Tscheetham, Chief Innovation Officer bei Happy Finish, der die interaktive Abteilung des Unternehmens leitet. "Die Ford GT40-Erfahrung ist ein Beweis dafür, dass eine HoloLens 2-App mit hoher Genauigkeit in nur wenigen Monaten mit einem moderaten Budget abgeschlossen werden kann, aber dennoch sehr gute Ergebnisse liefert." 

Aus Entwicklungssicht schätzt Der MRTK für Unreal basierend auf seinen vorherigen Erfahrungen mit Unreal auf HoloLens 2, dass der MRTK für Unreal die erforderliche Gesamtzeit und den Gesamtaufwand für seine Seite halbiert hat. Er stellt außerdem fest, wie das MRTK Entwicklern helfen kann, die noch nie mit HoloLens 2 gearbeitet haben. "Wenn andere Entwickler sagen, dass sie an Mixed Reality interessiert sind, ermutige ich sie, einfach zu springen, den HoloLens 2-Entwicklungsstapel und das MRTK zu installieren und dafür zu wechseln. Das MRTK erleichtert das schnelle und einfache Erstellen einer App, und der visuelle Unreal-Editor funktioniert so gut, dass Sie nicht einmal ein HoloLens 2 benötigen, um zu beginnen. Es ist überhaupt nicht kompliziert– alles funktioniert einfach."

### <a name="potential-azure-service-enhancements"></a>Potenzielle Erweiterungen des Azure-Diensts

Lambert sieht mehrere Möglichkeiten, wie Azure Mixed Reality-Dienste verwendet werden können, um die Ford GT40-Erfahrung zu verbessern, z. B. die Verwendung von Azure Spatial Anchors, um eine in der realen Welt verankerte Mehrbenutzererfahrung zu bieten. "Aus kreativer Sicht eröffnen Azure Spatial Anchors eine völlig neue Palette von Möglichkeiten, indem sie 3D-Inhalte oder Points of Interest innerhalb unserer physischen Welt zuordnen, beibehalten und wiederherstellen können", sagt er.

Lambert geht auch davon aus, wie die App entweder mit Azure Remote Rendering oder mithilfe des Streamings aus Azure verwendet werden kann, um bei der Arbeit mit detaillierteren und komplexeren 3D-Modellen die gewünschten Frameraten zu erzielen. "Wir mussten einige hochgradig optimierte benutzerdefinierte Shader in Unreal implementieren, um unser Geräteziel von 60 Frames pro Sekunde zu erreichen", erklärt er. "Mit Azure Remote Rendering könnten wir viel mehr tun – und dies viel einfacher, ohne dass so viel Arbeit erforderlich ist, um Polygonmodelle zu optimieren, Texturzuordnungen neu zu gezeichnet usw."

### <a name="endless-new-possibilities"></a>Endlose neue Möglichkeiten

Wie geht es mit Happy Finish weiter? Das Feedback von Ford zur Ford GT40-Erfahrung war überwältigend positiv, was zu weiteren Diskussionen zwischen Happy Finish und Ford zu zukünftigen HoloLens 2-Projekten führte. Außerhalb der Beziehung zu Ford startet Happy Finish bereits ein neues Projekt auf HoloLens 2, bei dem das MRTK für Unreal ein grundlegender Baustein für die meisten Benutzeroberflächen sein wird. 

"Wir haben für jedes neue Projekt immer einen technologieunabhängigen Ansatz verfolgt, der angibt, welches Toolset am besten geeignet ist, um dem Kunden zu helfen, die gewünschten Ergebnisse zu erzielen", sagt Cheetham. "Allerdings hat sich HoloLens 2 als De-facto-Goldstandard für Mixed Reality entwickelt, insbesondere im Unternehmen, da sie vor allen anderen Optionen stehen, was die Gerätefunktionen und die Überdringlichkeit des unterstützenden Ökosystems betrifft."

Laut Cheetham hat die globale Pandemie bei potenziellen Kunden ein enormes neues Interesse an immersiver Mixed Reality ausgelöst. "Wir sind viel beschäftigter als je zuvor, und ungefähr 50 Prozent der potenziellen Kunden sind offen für die Diskussion über eine Mixed Reality-Option", sagt er. "Der Schlüssel besteht darin, die Benutzer dazu zu bringen, es auszuprobieren. Sie können sie den ganzen Tag über Mixed Reality informieren, aber wenn Sie ihnen eine HoloLens 2 übergeben, die sie für sich selbst erleben können, erhalten sie sofort, wie es ein Game Changer sein kann. Die Unterstützung der Unreal-Engine in HoloLens 2 erhöht nur den Nutzen, den wir bieten können, sodass wir visuell beeindruckende Erfahrungen bereitstellen können, die auch die anspruchsvollsten Clients erfüllen."

## <a name="try-it-out"></a>Probieren Sie es aus!

> [!div class="nextstepaction"]
> [Herunterladen der Ford GT40-App](https://www.microsoft.com/p/ford-gt40/9p4vllktfvfp)

Sehen Sie sich unsere [Einführung in Mixed Reality Entwicklung auf HoloLens 2](../development.md) oder [MRTK für Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal) auf GitHub an.

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