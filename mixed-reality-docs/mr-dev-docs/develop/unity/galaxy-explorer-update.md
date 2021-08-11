---
title: Making of Galaxy Explorer for HoloLens 2
description: Erfahren Sie, wie unser Team das Open-Source-Projekt von Galaxy Explorer für HoloLens 2 auf GitHub.
author: l-garrett
ms.author: grbury
ms.date: 06/30/2019
ms.topic: article
keywords: Galaxy Explorer, Fallstudie, Projekt, Beispiel, MRTK, Mixed Reality Toolkit, Unity, Beispiel-Apps, Beispiel-Apps, Open Source, Microsoft Store, HoloLens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: c3d9c6da13446816f3fd75f83e5a9088661c9604ef4d86ea805202f538d395b5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200504"
---
# <a name="the-making-of-galaxy-explorer-for-hololens-2"></a>Das Erstellen von Galaxy Explorer für HoloLens 2

![Neues Galaxy Explorer-Logo](../images/GalaxyExplorer2.jpg)


Willkommen beim aktualisierten Galaxy Explorer für HoloLens 2 Anwendung! [Galaxy Explorer](/windows/mixed-reality/galaxy-explorer "Galaxy Explorer") wurde ursprünglich als Open-Source-Anwendung für HoloLens (erste Generation) über das Share Your Idea-Programm entwickelt und ist eine der ersten Mixed Reality-Erfahrungen, die viele Menschen hatten. Jetzt aktualisieren wir es für die neuen und interessanten [Funktionen von HoloLens 2.](https://www.microsoft.com/hololens/hardware)

Als eines der [Microsoft Mixed Reality Studio-Unternehmen](galaxy-explorer-update.md#mixed-reality-studios)entwickeln wir in der Regel lösungen für den kommerziellen Bereich und entwickeln & Tests auf Zielplattformen während des gesamten Schaffens- und Entwicklungsprozesses. Wir arbeiten an diesem Projekt mithilfe der Frameworks und Tools (z.B. [MRTK),](mrtk-getting-started.md)sobald sie für uns und die Community verfügbar werden, und wir möchten Sie für die Fahrt mitbringen.

Genau wie der ursprüngliche [](galaxy-explorer-update.md#meet-the-team) Galaxy Explorer [](https://github.com/Microsoft/GalaxyExplorer) wird unser Team das Projekt auf der GitHub öffnen, um sicherzustellen, dass die Community Vollzugriff hat. Wir dokumentieren auch unsere Reise hier in vollständiger Transparenz darüber, wie wir von MRTK v1 zu MRTK v2 portiert haben, die Erfahrung mit neuen Features verbessert haben, die in HoloLens 2 verfügbar sind, und stellen sicher, dass Galaxy Explorer eine plattformübergreifende Erfahrung bleibt. Unabhängig davon, ob Sie Galaxy Explorer auf HoloLens (erste Generation), HoloLens 2, einem Windows Mixed Reality-Headset oder auf Ihrem Windows 10-Desktop anzeigen, möchten wir sicherstellen, dass Sie die Reise so gut wie möglich begleiten!

Diese Seite wird während der Bearbeitung des Projekts mit Links zu ausführlicheren Artikeln, Code, Entwurfsartefakten und zusätzlicher MRTK-Dokumentation erweitert, um Ihnen einen Einblick in das Projekt zu geben.

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>Laden Sie die App Microsoft Store in HoloLens 2
Wenn Sie über HoloLens 2 verfügen, können Sie die App direkt herunterladen und auf Ihrem Gerät installieren.

<a href='//www.microsoft.com/store/apps/9nblggh4q4jg?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>

## <a name="thinking-about-interactions"></a>Überlegungen zu Interaktionen

Als Creative Studio haben wir uns über die Berechtigung zum Portieren von Galaxy Explorer in HoloLens 2. Wir wussten von Anfang an, dass die Erfahrung ein Teil des neuen Geräts sein soll, und um zu zeigen, dass Mixed Reality nur durch die Vorstellungsreichtum eingeschränkt ist.

HoloLens 2 können Benutzer Hologramme auf natürliche Weise berühren, erfassen und verschieben– sie reagieren ähnlich wie echte Objekte. Vollständig artikulierte Handmodelle sind verblüffend, da sie es Benutzern ermöglichen, das zu tun, was sich natürlich anfühlt. Beispielsweise nimmt jeder einen Becher etwas anders an – und anstatt eine bestimmte Möglichkeit zu erzwingen, HoloLens 2 Sie es auf Ihre Weise tun.

>[!VIDEO https://www.youtube.com/embed/wogJv5v9x-s]

Dies ist eine erhebliche Änderung der auf Air Tap basierenden Schnittstellen auf Geräten der HoloLens Generation. Anstatt aus der Entfernung mit Hologrammen zu interagieren, können Benutzer jetzt "nah und privat" sein. Beim Portieren vorhandener Erfahrungen auf HoloLens 2 oder beim Planen neuer Erfahrungen ist es wichtig, sich mit der direkten Manipulation von Hologrammen vertraut zu machen.

### <a name="direct-manipulation-vs-the-vast-distances-in-space"></a>Direkte Manipulation im Vergleich zu den großen Entfernungen im Raum

Es ist ein magisches Erlebnis, sich zu erreichen, einen Planeten zu greifen und ihn in der Hand zu halten. Die Herausforderung bei diesem Ansatz ist die Größe des Sonnensystems – es ist sehr groß! Der Benutzer müsste seinen Raum umher gehen, um jedem Planeten nahe zu kommen, um mit ihm zu interagieren.

Damit Benutzer mit weiter entfernten Objekten interagieren können, bietet MRTK Handlichtlichter, die aus der Mitte der Handfläche des Benutzers herauslaufen und als Erweiterung der Hand agieren. Ein donutförmiger Cursor wird am Ende des Strahls angefügt, um anzugeben, wo sich der Strahl mit einem Zielobjekt überschneidet. Das Objekt, auf dem der Cursor landet, kann dann gestische Befehle von der Hand empfangen. 

>[!VIDEO https://www.youtube.com/embed/Qol5OFNfN14]

In der ursprünglichen Version von Galaxy Explorer würde der Benutzer einen Planeten mit dem Anvitätscursor als Ziel verwenden und dann in die Luft tippen, um ihn näher zu nennen. Die einfachste Möglichkeit, die Erfahrung zu portieren, HoloLens 2, besteht in der Verwendung dieses Verhaltens und der Verwendung von Handlichtstrahl zur Auswahl von Planeten. Obwohl dies funktionierte, wollten wir mehr.

### <a name="back-to-the-drawing-board"></a>Sich etwas Neues einfallen lassen müssen

Wir sind zusammen gekommen, um zu verstehen, was auf den vorhandenen Interaktionen aufgebaut werden könnte. Das Denken war: Obwohl HoloLens 2 Benutzer auf natürliche, realistische Weise mit Hologrammen interagieren können, sind Hologramme definitionsgemäß nicht real. Solange eine Interaktion für den Benutzer wichtig ist, spielt es keine Rolle, ob diese Interaktion mit einem echten Objekt möglich wäre oder nicht– wir können dies ermöglichen.

Ein Konzept, das wir untersucht haben, war die Telekinesis– die Leistung, Objekte mit dem Kopf zu bearbeiten. Häufig in Super-Hero-Filmen gesehen, würde eine Person sich mit ihrem Kopf erreichen und ein Objekt in die offene Hand rufen. Wir haben mit der Idee noch mehr herumgespielt und haben einen kurzen Überblick darüber entwickelt, wie das Konzept funktionieren könnte.

![Konzept für die Force Grab-Interaktion](images/ge-update-interactions-concept-force-grab.png)

Der Benutzer würde den Handstrahl auf einen Planeten zeigen, der Zielfeedback geben würde. Wenn der Benutzer dann seine offene Hand ausdehnt, wird der Planet durch eine ungnische Kraft auf den Benutzer gezogen, bis er nahe genug ist, ihn zu greifen. Daher unser Name für die Interaktion: Force Grab. Da der Benutzer den Planeten mit der offenen Hand wegdrängen würde, würde er wieder in seine Umkreisung zurückkehren.

### <a name="force-grab-prototyping"></a>Erzwingen der Prototyperstellung für Greifer

Anschließend haben wir mehrere Prototypen erstellt, um das Konzept zu testen: Wie wirkt sich die Interaktion insgesamt aus? Sollte das aufgerufene Objekt vor dem Benutzer stehen bleiben oder an den Händen bleiben, bis es platziert wird? Sollte das aufgerufene Objekt die Größe oder Skalierung ändern, während es aufgerufen wird?

<!--
Here is Amit Rojtblat (Technical Artist) presenting one of the prototypes to Yasushi Zonno (Creative Lead).

------------------------------------------------------------------

__*--- VIDEO OF AMIT PLAYING AND EXPLAINING THE PROTOTYPE ---*__

__*--- NEEDS TO BE UPLOADED (TO YOUTUBE?) AND LINKED ---*__

------------------------------------------------------------------
-->

### <a name="implementing-force-grab-into-the-application"></a>Implementieren von Force Grab in der Anwendung

Als wir den Force Grab auf Planeten versuchten, erkannten wir, dass wir die Skalierung des Sonnensystems ändern mussten. Es stellte sich heraus, dass eine genaue, mittelgroße Darstellung des Sonnensystems für Benutzer schwierig zu verstehen und zu navigieren ist– sie wussten nicht, wo sie suchen sollten. Durch eine kleine Darstellung wurden einige Planeten jedoch zu klein, um leicht ausgewählt werden zu können. Daher wurden die Größe der Planeten und der Abstand zwischen Solarobjekten so entworfen, dass sie sich in einem mittelgroßen Raum wohl fühlen und gleichzeitig die relative Genauigkeit beibehalten.

In den späteren Phasen unseres Entwicklungssprints waren wir so glücklich, msft Mixed Reality-Experten vor Ort zu haben, sodass wir als erfahrene Tester ihre Eingaben erhalten und schnelle Iterationen bei der Force Grab-Interaktion durchgeführt haben.

![Jenny Kam testet einen Preview-Build von Galaxy Explorer](images/ge-update-user-testing.png)

Bild: Jenny Kam, Senior Design Lead, testing a work-in-progress of Galaxy Explorer.

### <a name="adding-affordances-for-targeting"></a>Hinzufügen von Bezahlbarkeiten für die Zielgruppenadressierung

Als wir mit HoloLens 2 experimentiert haben, haben wir festgestellt, dass Hologramme, obwohl die neuen Interaktionen natürlich und intuitiv sind, unverändert bleiben: ohne Gewichtung oder taktile Brillen. Da Hologramme kein natürliches Feedback liefern, das Menschen bei der Interaktion mit Objekten gewohnt sind, mussten wir sie erstellen.

Wir haben über das visuelle und Audiofeedback nachdenklich gemacht, dass Benutzer für die verschiedenen Phasen ihrer Interaktionen bereitgestellt werden, und da der Mechanismus zum Erzwingen des Greifens für die Interaktion mit Galaxy Explorer von zentraler Bedeutung ist, haben wir viele Iterationen durchgeführt. Das Ziel war es, das richtige Gleichgewicht zwischen Audio- und visuellem Feedback für jede Phase der Interaktion zu finden: sich auf das beabsichtigte Objekt zu konzentrieren, es dem Benutzer zu rufen und es dann frei zu geben. Wir haben gelernt, dass mehr Audio- und visuelles Feedback erforderlich war, um die Interaktion zu verstärken, als wir es für HoloLens (erste Generation) gewohnt waren.

![Visuelle Bezahlbarkeiten auf Planeten](images/ge-update-planet-affordances.png)

### <a name="adding-affordances-for-force-grab"></a>Hinzufügen von Bezahlbarkeiten für force grab
 
Sobald wir den grundlegenden Force Grab-Mechanismus mit Audio- und visuellen Veranschaulichungen hatten, haben wir uns damit um die Benutzerfreundlichkeit der Auswahl von Planeten geerbt. Es gab zwei Hauptansprache: Da es sich bei dem Solarsystem um eine 3D-Schnittstelle handelt, ist es für Benutzer komplexer, zu lernen, wie Objekte konsistent als Ziel verwendet werden können. Dies wurde durch die Tatsache, dass der Handstrahl beim Auswählen eines Objekts schnell ist, die Planeten auf den Benutzer zu bewegen, sehr schnell.

Wir haben dies mit einer dreigeschützten Lösung an die Reihe kommen. Die erste war ziemlich intuitiv: Verlangsamt den Auswahlprozess, sodass Planets den Benutzer mit einem natürlicheren Tempo anspricht. Nachdem die Geschwindigkeit angepasst wurde, mussten wir die Audio- und visuellen Bezahlbarkeiten erneut besuchen und Audiofeedback hinzufügen, während der Planet dem Benutzer nachsingt.

Der zweite Teil der Lösung war es, die Visualisierung der gesamten Force Grab-Interaktion erlebbar zu machen. Wir haben eine dichte Linie visualisiert, die sich auf das Zielobjekt zubewegt, sobald der Handstrahl eine Verbindung mit ihm herstellt, und das Objekt dann wieder an den Benutzer zurücksingt – wie ein Lasso. 

![Visuelle "lasso"-Bezahlbarkeiten für den Force Grab](images/ge-update-lasso-affordances.png)

Schließlich haben wir die Skalierung des Sonnensystems so optimiert, dass die Planeten groß genug waren, damit das Anvieren und der Handstrahl des Benutzers sie als Ziel haben. 

Diese drei Verbesserungen ermöglichten es Benutzern, eine genaue Auswahl zu treffen, indem sie planets auf intuitive Weise aufrufen. Insgesamt ist der Effekt des letzten Force Grabs eine immersivere und interaktivere Erfahrung im Sonnensystem.

## <a name="spotlight-on-jupiter"></a>Spotlight auf Einem

Das Erstellen der Sonnenkörper der Milchwegs war ein beredendes Erlebnis. Insbesondere die einzigartigen Merkmale von Sollen machen es zu einem Anblick. Es ist das größte und farbigste der Gasriesen und enthält mehr Massen als alle anderen Planeten zusammen. Seine schieren Größe und die mesmerisierenden Bänder von Wirtschaftlichen und Cloud dynamics sind prädektor für besondere Aufmerksamkeit.

### <a name="geometry-and-meshes"></a>Geometrie und Gitternetze

Als Gasriese bestehen die äußeren Shells von Gegensässigen aus gasförmigen Schichten. Die Kombination der schnellen Drehgeschwindigkeit, des inneren Wärmeaustauschs und der Coriolis-Erzwingung erzeugt farbige Schichten und Streams, die sich in sich drehende Cloudbänder und Vortices bilden. Die Erfassung dieses komplexen Systems war entscheidend für die Erstellung unseres Sonnensystems.

Es war sofort klar, dass die Verwendung von Visualisierungstechniken wie Strömungssimulationen und animierten Texturen mit vorausbesetzten Streams nicht in Frage kam. Die Rechenleistung, die erforderlich ist, um dies in Kombination mit allen anderen Gleichzeitigen zu simulieren, hätte erhebliche negative Auswirkungen auf die Leistung. 

![Übersicht über das Objekt "Soll"](images/ge-update-jupiter-shells-complete.jpg)

Der nächste Ansatz war eine "Smoke-and-Mirror"-Lösung, die aus überlagernden transparenten Texturebenen besteht, von denen jede einen bestimmten Aspekt der Bewegungsbewegung behandelt hat, die auf einer Zusammensetzung rotierender Gitternetze kompiliert wurde.

In der folgenden Abbildung sehen Sie die innere Shell auf der linken Seite. Diese Matebene lieferte einen Hintergrund für die Komposition, um sich vor kleinen Lücken zwischen den verschiedenen Schichten zu schützen, aus denen die Clouds bestehen. Aufgrund der langsamen Drehung der Ebene fungierte sie auch als visueller Puffer zwischen den schneller bewegenden Bändern, um visuelle Unity in allen Ebenen zu erstellen.

Nach dem Festlegen dieses Ankers auf das Modell wurden die sich bewegenden Cloudebenen dann auf die mittleren und rechten Gittermodelle projiziert, die unten zu sehen sind.

![Übersicht über das Objekt "Soll" mit getrennten Shells](images/ge-update-jupiter-shells-separated.jpg)

### <a name="texturing"></a>Texturierung

Die vorhandene Textur wurde in einen dreiteiligen Texturatlas getrennt: Das obere Dritte hostet eine bewegungslose Schicht von Clouds mit Lücken, um einen paraarmierten Effekt zu erzielen, der mittlere Abschnitt enthält die schnell bewegenden äußeren Datenströme, und das untere Dritte enthält eine langsam rotierende innere Basisschicht.

Das Merkmal Great Red Spot wurde auch in seine verschiedenen beweglichen Teile unterteilt und dann in einen ansonsten unsichtbaren Bereich der Textur eingefügt. Diese Komponenten können als rot-tonierte Speckles im mittleren Abschnitt der folgenden Abbildung angezeigt werden.

Da jedes Band eine bestimmte Richtung und Geschwindigkeit hat, wurde die Textur einzeln auf jedes Gitternetz angewendet. Die Gitternetze hatten dann einen gemeinsamen Mittelpunkt und Pivotpunkt, wodurch es möglich war, die gesamte Oberfläche konzentrisch zu animieren.

![Übersicht über Die Texturen vonIgen](images/ge-update-jupiter-planet-cloud-texture.png)

### <a name="rotation-and-texture-behavior"></a>Rotations- und Texturverhalten

Nachdem die visuelle Komposition von Soll festgelegt wurde, mussten wir sicherstellen, dass dreh- und umkreisgeschwindigkeiten ordnungsgemäß berechnet und entsprechend angewendet wurden. Es dauert ungefähr 9 Stunden, bis Eine vollständige Drehung abgeschlossen ist. Dies ist aufgrund der differenziellen Drehung eine Definitionssache. Daher wurde der Äquatorialstream als "Masterstream" festgelegt, der 3.600 Frames für eine vollständige Drehung verwendet. Jede andere Schicht musste eine Drehgeschwindigkeit als Faktor 3600 haben, um ihre Ausgangsposition zu finden, sodass z.B. 600, 900, 1200, 1800 usw. möglich sind.

![Shelltexturen von Shell](images/ge-update-shell-texture.jpg)


### <a name="the-great-red-spot"></a>The Great Red Spot

Die einzeln rotierenden Datenströme boten einen guten visuellen Eindruck, fehlten jedoch im Detail, wenn sie im Nahbereich beobachtet wurden.

Der auffallendste Teil war Der große rote Kasten von Great Red Spot, daher haben wir speziell eine Reihe von Gittern und Texturen erstellt, um sie zu präsentieren.
 
Wir haben einen ähnlichen Mechanismus wie bei Den bändern verwendet: Eine Reihe rotierender Teile wurde übereinander zusammengesetzt, während sie auch unter ihrer "Masterebene" gruppiert wurden, um sicherzustellen, dass sie unabhängig davon, wie schnell sich der Rest bewegt, an Position bleiben.

Als die Gitternetze eingerichtet und eingerichtet wurden, wurden verschiedene Schichten des stormy-Vortex angewendet, und jede Folie wurde dann einzeln animiert, die Mittelpunkte bewegen sich am schnellsten, und der Rest verlangsamt sich progressiv, während er sich nach außen bewegt.

![Great Red Spot Mesh](images/ge-update-great-red-spot-mesh.jpg)

Die Komposition hatte auch den gleichen Pivot wie jedes andere Gitter, während sie gleichzeitig ihre Neigung von der ursprünglichen Y-Achse (!) hält, um die Flexibilität bei der Animation der Drehung zu ermöglichen. 3.600 Frames ist die Basisrate, bei der jede Ebene einen Faktor dafür als Rotationszeitraum hat.

![Great Red Spot-Textur von Great Red Spot](images/ge-update-red-spot-mesh-texture.jpg)

### <a name="getting-it-right-in-unity"></a>Erste Schritte in Unity

Bei der Implementierung in Unity sind einige wichtige Dinge zu beachten.

Unity ist leicht verwirrend, wenn es um große Mengen von transparenten Ebenen geht. Die Lösung besteht darin, das Texturmaterial für jedes Gitter zu duplizieren und aufsteigende Renderwarteschlangenwerte progressiv von innen nach außen um 5 auf jedes Material anzuwenden.

Das Ergebnis war, dass die innere Shell einen Renderwarteschlangenwert von 3000 (Standard) auf hatte, das statische rot-toned outer später einen Wert von 3005 hatte, die schnellen weißen äußeren Clouds 3010. Der Great Red Spot (von der inneren zur äußeren Ebene) wurde in diesem Modell mit dem Wert 3025 abgeschlossen.

![Endgültiges Objekt](images/ge-update-jupiter-final.jpg)

### <a name="final-touches"></a>Letzte Schritte

Die texturierten -Ebenen wurden zuerst eingerichtet, was sich als unzureichend für die Implementierung erwiesen hat.

Der ursprüngliche Planet Standard-Shader und alle seine Variationen empfangen ihre Beleuchtungsinformationen über das Skript SunLightReceiver, das vom MRTK Standard-Shader nicht unterstützt wird.

Das einfache Austauschen der Shader war keine Lösung, da der Planet Standard-Shader keine Texturzuordnungen mit Transparenz unterstützt. Wir haben diesen Shader bearbeitet, damit der Build von Bein wie vorgesehen funktioniert.

Schließlich mussten die Alphablends eingerichtet werden, indem die Quellblendung auf 10 und die Zielblendung auf 5 festgelegt werden.

![Eigenschaften von Unity](images/ge-update-jupiter-unity-render-queue.jpg)

Sie können das endgültige Rendering von Stern im Galaxy Explorer sehen!

## <a name="meet-the-team"></a>Lernen Sie das Team kennen 

Unser Mixed Reality Studio-Team besteht aus Designern, 3D-Architekten, UX-Spezialisten, Entwicklern, einem Programmmanager und einem Studioleiter. Wir freuen uns aus der ganzen Welt: Großbritannien, Kanada, Deutschland, Indien, Japan, Vereinigtes Königreich und USA. Wir sind ein multidisziplinäres Team, das aus einem vielfältigen Hintergrund stammt: Spiele – sowohl traditionelle als auch Indie-Spiele, digitales Marketing, Gesundheitswesen und Wissenschaft.

Wir freuen uns, Galaxy Explorer für HoloLens 2 zu erstellen und die Versionen HoloLens (erste Generation), VR und Desktop zu aktualisieren. 

![Das Galaxy Explorer-Team](images/ge-update-team-image.png)

Oben von links nach rechts:Anz Tsouflidou (Entwickler), Angie Teickner (Visual Designer), David Janer (UX Designer), Sr. Ben Turner (Delivery & Production Lead), Yasushi Zonno (Creative Lead), Eline Ledent (Developer) und Ben Turner (Sr. Developer).
Unten von links nach rechts: Amit Rojtblat (Technischer Interpret), MartinGsig (3D-Interpret) und Dann Sonilla (Studio Head).
Nicht ausgewählte: Tim Gerken (Tech Lead) und Paus Salandin (Visual Designer).

## <a name="additional-information"></a>Weitere Informationen

### <a name="mixed-reality-studios"></a>Mixed Reality Studio

Microsoft Mixed Reality Studio-Teams, die sich in Nordamerika, Europa und Asia-Pacific befinden, sind Experten in den Folgenden: Entwurf der Benutzeroberfläche, holografisches Computing, AR/VR-Technologien und 3D-Entwicklung. einschließlich 3D-Ressourcenerstellung, DirectX, Unity und Unreal. Wir helfen Ihnen dabei, die gewünschten Zukünftigen zu entwerfen, Lösungen zu entwerfen, zu erstellen und zu liefern, und ermöglichen kunden gleichzeitig, messbare Auswirkungen in ihrer gesamten Organisation zu erzielen. Die Studio-Unternehmen arbeiten eng mit über 22.000 Microsoft Services-Experten zusammen, um die Integration von Unternehmensanwendungen, die Einführung, den Betrieb und den Support zu unterstützen.