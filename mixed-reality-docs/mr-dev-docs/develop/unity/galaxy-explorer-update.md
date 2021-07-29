---
title: Making of Galaxy Explorer for HoloLens 2
description: Erfahren Sie, wie unser Team das Galaxy Explorer-Open-Source-Projekt für HoloLens 2 auf GitHub aktualisiert.
author: l-garrett
ms.author: grbury
ms.date: 06/30/2019
ms.topic: article
keywords: Galaxy Explorer, Fallstudie, Projekt, Beispiel, MRTK, Mixed Reality Toolkit, Unity, Beispiel-Apps, Beispiel-Apps, Open Source, Microsoft Store, HoloLens, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 1e19f63f493eba2559cf60ef7c1224b7323ec825
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757072"
---
# <a name="the-making-of-galaxy-explorer-for-hololens-2"></a>Die Erstellung von Galaxy Explorer für HoloLens 2

![Neues Galaxy Explorer-Logo](../images/GalaxyExplorer2.jpg)


Willkommen bei der aktualisierten Galaxy Explorer-Anwendung für HoloLens 2! [Galaxy Explorer](/windows/mixed-reality/galaxy-explorer "Galaxy Explorer") wurde ursprünglich als Open-Source-Anwendung für HoloLens (erste Generation) über das Share Your Idea-Programm entwickelt und ist eine der ersten Mixed Reality-Erfahrungen, die viele Menschen hatten. Jetzt aktualisieren wir es für die [neuen und interessanten Funktionen von HoloLens 2](https://www.microsoft.com/hololens/hardware).

Als eines der [Microsoft Mixed Reality Studios](galaxy-explorer-update.md#mixed-reality-studios)entwickeln wir in der Regel kommerzielle Lösungen und entwickeln & Tests auf Zielplattformen während des gesamten Schaffens- und Entwicklungsprozesses. Wir beginnen mit diesem Projekt, indem wir die Frameworks und Tools (wie [MRTK)](mrtk-getting-started.md)verwenden, sobald sie für uns und die Community verfügbar sind. Wir möchten Sie für die Fahrt mitführen.

Genau wie der ursprüngliche Galaxy Explorer wird [unser Team](galaxy-explorer-update.md#meet-the-team) das Projekt auf [GitHub öffnen,](https://github.com/Microsoft/GalaxyExplorer) um sicherzustellen, dass die Community Vollzugriff hat. Wir dokumentieren unsere Reise hier auch in vollständiger Transparenz darüber, wie wir von MRTK v1 zu MRTK v2 portiert haben, die Benutzeroberfläche durch neue Features verbessert haben, die in HoloLens 2 verfügbar sind, und stellen sicher, dass Galaxy Explorer eine plattformübergreifende Erfahrung bleibt. Unabhängig davon, ob Sie Galaxy Explorer auf HoloLens (erste Generation), HoloLens 2, einem Windows Mixed Reality Headset oder auf Ihrem Windows 10 Desktop anzeigen, möchten wir sicherstellen, dass Sie die Reise so gut wie möglich gestalten!

Diese Seite wird erweitert, während wir das Projekt durchlaufen, mit Links zu ausführlicheren Artikeln, Code, Entwurfsartefakten und zusätzlicher MRTK-Dokumentation, um Ihnen einen Einblick in das Projekt zu geben.

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>Herunterladen der App aus Microsoft Store in HoloLens 2
Wenn Sie über HoloLens 2 Gerät verfügen, können Sie die App direkt herunterladen und auf Ihrem Gerät installieren.

<a href='//www.microsoft.com/store/apps/9nblggh4q4jg?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>

## <a name="thinking-about-interactions"></a>Überlegungen zu Interaktionen

Als Creative Studio waren wir über die Berechtigung, Galaxy Explorer zu HoloLens 2 zu porten, sehr verzeilt. Wir wussten von Anfang an, dass wir möchten, dass die Benutzeroberfläche eine Vorstellung von dem neuen Gerät ist, und um zu zeigen, dass Mixed Reality Riegel nur durch die Vorstellungsfähigkeit eingeschränkt ist.

HoloLens 2 ermöglicht es Benutzern, Hologramme so zu berühren, zu verstehen und zu verschieben, dass sie sich natürlich anfühlen – sie reagieren sehr ähnlich wie echte Objekte. Vollständig formulierte Handmodelle sind verblüffend, da sie es Benutzern ermöglichen, das zu tun, was sich natürlich anfühlt. Beispielsweise nimmt jeder einen Becher etwas anders ab – und anstatt eine bestimmte Möglichkeit zu erzwingen, können Sie HoloLens 2 dies auf Ihre Weise tun.

>[!VIDEO https://www.youtube.com/embed/wogJv5v9x-s]

Dies ist eine erhebliche Änderung gegenüber den air tap-basierten Schnittstellen auf geräten der ersten Generation HoloLens. Anstatt aus der Entfernung mit Hologrammen zu interagieren, können Benutzer jetzt "ganz nah und persönlich" kommen. Beim Portieren vorhandener Erfahrungen auf HoloLens 2 oder beim Planen neuer Erfahrungen ist es wichtig, sich mit der direkten Bearbeitung von Hologrammen vertraut zu machen.

### <a name="direct-manipulation-vs-the-vast-distances-in-space"></a>Direkte Bearbeitung im Vergleich zu den großen Entfernungen im Raum

Es ist eine magische Erfahrung, einen Planeten zu erreichen, ihn in der Hand zu halten. Die Herausforderung bei diesem Ansatz ist die Größe des Sonnensystems – es ist sehr groß! Der Benutzer muss sein Zimmer umhergehen, um sich jedem Planeten nähern zu können, um damit zu interagieren.

Damit Benutzer mit Objekten interagieren können, die weiter entfernt sind, bietet MRTK Handlichtlicht, das aus der Mitte der Handfläche des Benutzers herausgepusht wird und als Erweiterung der Hand fungiert. Ein donutförmiger Cursor wird am Ende des Strahls angefügt, um anzugeben, wo sich der Strahl mit einem Zielobjekt überschneidet. Das Objekt, auf dem der Cursor landet, kann dann gestische Befehle von der Hand empfangen. 

>[!VIDEO https://www.youtube.com/embed/Qol5OFNfN14]

In der ursprünglichen Version von Galaxy Explorer zielte der Benutzer mit dem Anvischer auf einen Planeten und tippte dann in die Luft, um ihn näher zu nennen. Die einfachste Möglichkeit, die Benutzeroberfläche auf HoloLens 2 zu portieren, besteht darin, dieses Verhalten zu nutzen und Handlichtstrahl zu verwenden, um Planeten auszuwählen. Dies war zwar funktionsfähig, aber wir wollten mehr.

### <a name="back-to-the-drawing-board"></a>Sich etwas Neues einfallen lassen müssen

Wir haben zusammen erfahren, was auf den vorhandenen Interaktionen aufbauen könnte. Das Denken lautete: Obwohl HoloLens 2 benutzern die Interaktion mit Hologrammen auf natürliche, realistische Weise ermöglicht, sind Hologramme definitionsgemäß nicht real. Solange eine Interaktion für den Benutzer einfach ist, spielt es keine Rolle, ob diese Interaktion mit einem echten Objekt möglich wäre oder nicht – wir können dies ermöglichen.

Ein Konzept, das wir untersucht haben, basierte auf Telekinesis– der Potenz, Objekte mit dem Kopf zu bearbeiten. Häufig in Super hero-Filmen zu sehen, würde eine Person mit ihrem Kopf anrücken und ein Objekt in die offene Hand rufen. Wir haben etwas mehr mit der Idee herumgespielt und eine kurze Kurzübersicht darüber entwickelt, wie das Konzept funktionieren könnte.

![Konzept für die Force Grab-Interaktion](images/ge-update-interactions-concept-force-grab.png)

Der Benutzer würde den Handstrahl auf einen Planeten zeigen, der Zielfeedback bereitstellen würde. Wenn der Benutzer dann seine offene Hand erweitert, wird der Planeten mit einer magischen Kraft auf den Benutzer gezogen, bis er nah genug ist, um ihn zu greifen. Daher unser Name für die Interaktion: Force Grab. Da der Benutzer den Planeten mit seiner offenen Hand wegschieben würde, kehrt er wieder zu seiner Umkreisung zurück.

### <a name="force-grab-prototyping"></a>Erzwingen der Grab-Prototyperstellung

Anschließend haben wir mehrere Prototypen erstellt, um das Konzept zu testen: Wie sieht die Interaktion insgesamt aus? Sollte das aufgerufene Objekt vor dem Benutzer stehen bleiben oder an den Händen bleiben, bis es platziert wurde? Sollte das aufgerufene Objekt die Größe oder Skalierung ändern, während es aufgerufen wird?

<!--
Here is Amit Rojtblat (Technical Artist) presenting one of the prototypes to Yasushi Zonno (Creative Lead).

------------------------------------------------------------------

__*--- VIDEO OF AMIT PLAYING AND EXPLAINING THE PROTOTYPE ---*__

__*--- NEEDS TO BE UPLOADED (TO YOUTUBE?) AND LINKED ---*__

------------------------------------------------------------------
-->

### <a name="implementing-force-grab-into-the-application"></a>Implementieren von Force Grab in der Anwendung

Als wir den Force Grab auf Planeten versucht haben, haben wir festgestellt, dass wir die Skalierung des Sonnensystems ändern mussten. Es hat sich herausstellt, dass eine genaue, mittelgroße Darstellung des Sonnensystems für Benutzer schwierig zu verstehen und zu navigieren ist– sie wussten nicht, wo sie suchen sollten. Durch eine kleine Darstellung wurden einige Planeten jedoch zu klein, um einfach ausgewählt zu werden. Daher wurden die Größe der Planeten und der Abstand zwischen Solarobjekten so entworfen, dass sie sich in einem mittelgroßen Raum wohl fühlen und gleichzeitig die relative Genauigkeit aufrechterhalten.

In den späteren Phasen unseres Entwicklungssprints waren wir sehr glücklich genug, msft Mixed Reality Experten im Haus zu haben, sodass wir uns als Experten-Tester an die Arbeit gemacht und schnelle Iterationen für die Force Grab-Interaktion durchgeführt haben.

![Jenny Kam testet einen Vorschaubuild von Galaxy Explorer](images/ge-update-user-testing.png)

Bild: Jenny Kam, Senior Design Lead, testing a work-in-progress of Galaxy Explorer.

### <a name="adding-affordances-for-targeting"></a>Hinzufügen von Möglichkeiten für die Zielgruppenadressierung

Als wir mit HoloLens 2 experimentiert haben, haben wir festgestellt, dass hologramme unverändert bleiben, obwohl die neuen Interaktionen natürlich und intuitiv sind: ohne Gewicht oder taktilen Schläger. Da Hologramme kein natürliches Feedback liefern, das Menschen bei der Interaktion mit Objekten erhalten, mussten wir sie erstellen.

Wir haben uns gedanken über das Visuelle und Audiofeedback, das Benutzern für die verschiedenen Phasen ihrer Interaktionen zur Verfügung gestellt wird, und da der Force Grab-Mechanismus für die Interaktion mit Galaxy Explorer von zentraler Bedeutung ist, haben wir viele Iterationen durchgeführt. Das Ziel bestand darin, die richtige Balance von Audio- und visuellem Feedback für jede Phase der Interaktion zu finden: konzentrieren Sie sich auf das beabsichtigte Objekt, rufen Sie es dem Benutzer auf, und geben Sie es dann frei. Wir haben gelernt, dass mehr Audio- und visuelles Feedback erforderlich war, um die Interaktion zu verstärken, als wir für HoloLens (erste Generation) gewohnt waren.

![Visuelle Erschwinglichkeit auf Planeten](images/ge-update-planet-affordances.png)

### <a name="adding-affordances-for-force-grab"></a>Hinzufügen von Möglichkeiten zum Erzwingen des Greifens
 
Nachdem wir den grundlegenden Force Grab-Mechanismus mit Audio- und visuellen Möglichkeiten hatten, haben wir uns angesehen, wie wir die Auswahl von Planeten benutzerfreundlicher gestalten können. Es gab zwei wichtige Punkte zu beheben: Da es sich bei dem Solarsystem um eine 3D-bewegliche Schnittstelle handelt, erhöht sich die Komplexität für Benutzer, um zu lernen, wie Objekte konsistent ausgerichtet werden. Dies wurde durch die Tatsache verstärkt, dass der Handstrahl schnell ein Objekt auswählt, sodass Planeten sich unglaublich schnell in Richtung des Benutzers bewegen.

Wir haben dies mit einer dreistufigen Lösung erreicht. Die erste war ziemlich intuitiv: Verlangsamen Sie den Auswahlprozess, sodass Planets den Benutzer in einem natürlicheren Tempo annähern. Nachdem die Geschwindigkeit angepasst wurde, mussten wir die Audio- und visuellen Möglichkeiten erneut besuchen und Audiofeedback hinzufügen, während der Planet dem Benutzer gegenüber nachverfolgt wurde.

Der zweite Teil der Lösung bestand darin, die Visualisierung der gesamten Force Grab-Interaktion greifbar zu machen. Wir haben eine dichte Linie visualisiert, die sich in Richtung des Zielobjekts bewegt, sobald der Handstrahl eine Verbindung mit ihm herstellt, und das Objekt dann wieder an den Benutzer zurückgibt , z. B. ein Lasso. 

![Visuelle "Lasso"-Elemente für die Force Grab-Aktion](images/ge-update-lasso-affordances.png)

Schließlich haben wir die Skala des Sonnensystems so optimiert, dass die Planeten groß genug waren, damit der Benutzer anvisieren und den Handstrahl auf sie ausrichten kann. 

Diese drei Verbesserungen ermöglichten es Benutzern, eine genaue Auswahl zu treffen und ihnen auf intuitive Weise Planeten zu nennen. Insgesamt ist der Effekt des endgültigen Force Grabens ein immersiveres und interaktiveres Erlebnis im Sonnensystem.

## <a name="spotlight-on-jupiter"></a>Spotlight auf Einem

Das Erstellen der Solarkörper des Milchwegs war eine verwaschene Erfahrung. Insbesondere die einzigartigen Merkmale von Dass machen ihn zu einem sichtigen Blick. Es ist der größte und farbigeste der Gasriesen und enthält mehr Massen als alle anderen Planeten kombiniert. Die schiere Größe und die mesmerisierenden Bänder von Schwankungen und Cloud dynamics sind präfect für besondere Aufmerksamkeit.

### <a name="geometry-and-meshes"></a>Geometrie und Gitternetze

Als Gasriese bestehen Die äußeren Shells von Dasss aus gasförmigen Schichten. Die Kombination aus schneller Drehgeschwindigkeit, innerem Wärmeaustausch und Coriolis-Zwingen erstellt farbige Schichten und Ströme, die sich zu verkabelten Cloudbändern und Vortices bilden. Die Erfassung dieser komplexen Landschaft war der Schlüssel zum Erstellen unseres Sonnensystems.

Es war sofort klar, dass die Verwendung von Visualisierungstechniken wie Fluidsimulationen und animierten Texturen mit vorausberechnen Streams nicht inFrage kam. Die Rechenleistung, die erforderlich ist, um dies in Kombination mit allen anderen Ereignissen gleichzeitig zu simulieren, hätte erhebliche negative Auswirkungen auf die Leistung haben können. 

![Übersicht über das Objekt "Wiesn"](images/ge-update-jupiter-shells-complete.jpg)

Der nächste Ansatz war eine "Feuer-und-Spiegel"-Lösung, die aus überlagernden transparenten Texturebenen besteht, von denen jede einen bestimmten Aspekt der Luftbewegung behandelt hat, die auf einer Zusammensetzung rotierender Gitternetze kompiliert wurde.

In der folgenden Abbildung sehen Sie die innere Shell auf der linken Seite. Diese Mat-Schicht bot einen Hintergrund für die Komposition, um sich vor kleinen Lücken zwischen den mehreren Ebenen zu schützen, aus denen sich die Clouds zusammensetzten. Aufgrund der langsamen Drehung der Ebene fungierte sie auch als visueller Puffer zwischen den schneller verschiebenden Bändern, um visuelle Unity in den Ebenen zu erstellen.

Nach dem Festlegen dieses Ankers auf das Modell wurden die sich bewegenden Cloudebenen dann auf die mittleren und rechten Gittermodelle projiziert, die unten dargestellt sind.

![Übersicht über das Objekt "Wiege" mit getrennten Shells](images/ge-update-jupiter-shells-separated.jpg)

### <a name="texturing"></a>Texturierung

Die vorhandene Textur wurde in einen dreiteiligen Texturatmus unterteilt: Das obere Dritte hostet eine bewegungslose Schicht von Clouds mit Lücken, um einen Paraplanxeffekt bereitzustellen, der mittlere Abschnitt enthält die sich schnell bewegenden äußeren Datenströme, und das untere dritte enthält eine langsam rotierende innere Basisebene.

Das Merkmal Great Red Spot wurde auch in seine verschiedenen beweglichen Teile aufgeteilt und dann in einen ansonsten unsichtbaren Bereich der Textur eingefügt. Diese Komponenten können als rot gezeichnete Speckles im mittleren Abschnitt der folgenden Abbildung angezeigt werden.

Da jedes Band eine bestimmte Richtung und Geschwindigkeit hat, wurde die Textur einzeln auf jedes Netz angewendet. Die Gitternetze hatten dann einen gemeinsamen Mittelpunkt und Pivotpunkt, der es ermöglichte, die gesamte Oberfläche verkettet zu animieren.

![Übersicht über Texturen](images/ge-update-jupiter-planet-cloud-texture.png)

### <a name="rotation-and-texture-behavior"></a>Drehungs- und Texturverhalten

Sobald die visuelle Komposition von Dividiert festgelegt wurde, mussten wir sicherstellen, dass die Drehungs- und Umkreisgeschwindigkeiten ordnungsgemäß berechnet und entsprechend angewendet wurden. Es dauert ungefähr 9 Stunden, bis Eine vollständige Drehung abgeschlossen ist. Dies ist aufgrund der differenziellen Drehung definitionsbedingt. Daher wurde der äquatoriale Stream als "Masterstream" festgelegt, wobei 3.600 Frames für eine vollständige Drehung aufgenommen wurden. Jede andere Ebene benötigt eine Drehungsgeschwindigkeit als Faktor von 3600, um ihre Anfangsposition zu entsprechen, z.B. 600, 900, 1200, 1800 usw.

![Shelltexturen in Der Shell](images/ge-update-shell-texture.jpg)


### <a name="the-great-red-spot"></a>The Great Red Spot

Die einzeln rotierenden Streams boten einen guten visuellen Eindruck, fehlten jedoch im Detail, wenn sie im nahstehenden Bereich beobachtet wurden.

Der auffallendste Teil war "Great Red Spot", also haben wir eine Reihe von Gittern und Texturen speziell erstellt, um sie zu präsentieren.
 
Wir haben einen ähnlichen Mechanismus wie bei den Bands vonEinander verwendet: Eine Reihe rotierender Teile wurde übereinander zusammengestellt und gleichzeitig unter ihrer "Masterebene" gruppiert, um sicherzustellen, dass sie unabhängig davon, wie schnell sich der Rest bewegt, an Position bleiben.

Wenn die Gitternetze eingerichtet und eingerichtet wurden, wurden verschiedene Schichten des Stormy-Vortex angewendet, und jede Folie wurde dann einzeln animiert, wobei sich die Mittelpunkte am schnellsten bewegten, wobei sich der Rest progressiv verlangsamte, während er sich nach außen bewegte.

![Großartiges Rotes Spot-Netz](images/ge-update-great-red-spot-mesh.jpg)

Die Komposition hatte auch den gleichen Pivot wie jedes andere Gitternetz, während gleichzeitig die Neigung von der ursprünglichen Y-Achse (!) gehalten wurde, um die Drehung frei zu halten. 3.600 Frames ist die Basisrate, wobei jede Ebene einen Faktor davon als Drehungszeitraum aufweist.

![Great Red Spot Texture](images/ge-update-red-spot-mesh-texture.jpg)

### <a name="getting-it-right-in-unity"></a>Richtiges Lernen in Unity

Bei der Implementierung in Unity sind einige wichtige Punkte zu beachten.

Unity ist leicht zu verwechseln, wenn es um große Mengen von transparenten Ebenen geht. Die Lösung bestand darin, das Texturmaterial für jedes Gitternetz zu duplizieren und aufsteigende Renderwarteschlangenwerte progressiv vom inneren zum äußeren um 5 auf jedes Material anzuwenden.

Das Ergebnis war, dass die innere Shell den Renderwarteschlangenwert 3000 (Standard) aufwies, die statische rot geträumte äußere Schleife später den Wert 3005 und die schnellen weißen äußeren Clouds 3010. Great Red Spot (von innerer zur äußeren Ebene) wurde in diesem Modell mit dem Wert 3025 abgeschlossen.

![Final object (Final-Objekt)](images/ge-update-jupiter-final.jpg)

### <a name="final-touches"></a>Letzte Schritte

Die texturierten Wiegeebenen wurden zunächst eingerichtet, was sich als unzureichend für die Implementierung erwiesen hat.

Der ursprüngliche Planet Standard-Shader und alle seine Variationen erhalten ihre Beleuchtungsinformationen über ein Skript, das SunLightReceiver, das vom MRTK Standard-Shader nicht unterstützt wird.

Das einfache Austauschen der Shader war keine Lösung, da der Planet Standard-Shader keine Texturzuordnungen mit Transparenzen unterstützt. Wir haben diesen Shader bearbeitet, damit derBuild vonBuild wie vorgesehen funktioniert.

Schließlich mussten die Alphablends eingerichtet werden, indem der Quellblend auf 10 und der Zielblend auf 5 festgelegt wurden.

![Unity-Eigenschaften von Unity](images/ge-update-jupiter-unity-render-queue.jpg)

Sie können das endgültige Rendern von Galaxy Explorer sehen.

## <a name="meet-the-team"></a>Lernen Sie das Team kennen 

Unser Mixed Reality Studio-Team besteht aus Designern, 3D-Architekten, UX-Spezialisten, Entwicklern, einem Programmleiter und einem Studioleiter. Wir stammen aus der ganzen Welt: Kanada, Kanada, Deutschland, Tokio, Japan, Vereinigtes Königreich und die USA. Wir sind ein übergreifendes Team, das aus einem vielfältigen Hintergrund stammt: Spiele – sowohl traditionelle als auch Indie, digitales Marketing, Gesundheitswesen und Wissenschaft.

Wir freuen uns, Galaxy Explorer für HoloLens 2 zu erstellen und die HoloLens (erste Generation), VR und Desktopversionen zu aktualisieren. 

![Das Galaxy Explorer-Team](images/ge-update-team-image.png)

Oben von links nach rechts: Trap Tsouflidou (Entwickler), Angie Teickner (Visual Designer), David Janer (UX Designer), Garrett (Delivery & Production Lead), Yasushi Zonno (Creative Lead), Eline Ledent (Developer) und Ben Turner (Sr. Developer).
Unten von links nach rechts: Amit Rojtblat (Technischer Interpret), Martin Linkenig (3D-Interpret) und Deinstalliert Sonteroperabilität (Studio Head).
Nicht vorgestellt: Tim Gerken (Tech Lead) und Sas salandin (Visual Designer).

## <a name="additional-information"></a>Zusätzliche Informationen

### <a name="mixed-reality-studios"></a>Mixed Reality Studio

Microsoft Mixed Reality Studio-Teams, die sich in Nordamerika, Europa und Asia-Pacific befinden, sind Experten für Benutzererlebnisdesign, holografisches Computing, AR/VR-Technologien und 3D-Entwicklung. einschließlich Erstellung von 3D-Medienobjekten, DirectX, Unity und Unreal. Wir unterstützen Sie dabei, die gewünschten Futures zu entwerfen, zu erstellen und Lösungen bereitzustellen, und ermöglichen es Kunden gleichzeitig, messbare Auswirkungen auf ihre gesamte Organisation zu erzielen. Die Studios arbeiten eng mit über 22.000 Microsoft Services-Experten zusammen, um Anwendungsintegration, Einführung, Betrieb und Support für Unternehmen zu unterstützen.