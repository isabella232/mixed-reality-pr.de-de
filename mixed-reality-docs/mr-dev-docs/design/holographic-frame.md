---
title: Holografischer Rahmen
description: Erfahren Sie, wie Benutzer die Welt der Mixed Reality über den holografischen Rahmen sehen und wie Sie die Erfahrung am besten gestalten.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/25/2020
ms.topic: article
keywords: HoloLens, Windows Mixed Reality, holografischer Rahmen, Sichtfeld, FOV, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit, Interaktionen, Navigation, Menü
ms.openlocfilehash: fee6af6370f9f3d166768144e689e09fd3fda2db
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143255"
---
# <a name="holographic-frame"></a>Holografischer Rahmen

Benutzer sehen die Welt der Mixed Reality durch ein rechteckiges Ansichtsfenster, das von ihren Headsets betrieben wird. Bei HoloLens wird dieser rechteckige Bereich als holografischer Rahmen bezeichnet und ermöglicht den Benutzern, die digitalen Inhalte zu sehen, die der realen Welt ihrer Umgebung überlagert sind. Das Entwerfen von Benutzeroberflächen, die für den holografischen Rahmen optimiert sind, schafft Möglichkeiten, entschärft Herausforderungen und verbessert die Benutzerfreundlichkeit von Mixed Reality-Anwendungen.

## <a name="designing-for-content"></a>Entwerfen für Inhalt

Designer haben häufig die Notwendigkeit, den Umfang ihrer Benutzererfahrung auf das zu beschränken, was dem Benutzer sofort angezeigt wird, und dabei die reale Skalierung zu versieren, um sicherzustellen, dass der Benutzer ein Objekt in seiner Gesamtheit sieht. Auf ähnliche Weise überladen Designer mit komplexen Anwendungen oft den holografischen Rahmen mit Inhalten, überladen Benutzer mit komplizierten Interaktionen und unübersichtlichen Schnittstellen. Designer, die Mixed Reality-Inhalte erstellen, müssen die Benutzererfahrung nicht auf die direkte Vor- und Nachsicht des Benutzers beschränken. Wenn die physische Welt um den Benutzer herum zugeordnet ist, sollten alle diese Oberflächen als potenzieller Zeichenbereich für digitale Inhalte und Interaktionen betrachtet werden. Das richtige Design von Interaktionen und Inhalten innerhalb einer Umgebung sollte den Benutzer dazu bewegen, sich in seinen Raum zu bewegen, seine Aufmerksamkeit auf wichtige Inhalte zu richten und das volle Potenzial von Mixed Reality zu erkennen.

Das vielleicht wichtigste Verfahren zur Förderung von Bewegung und Untersuchung innerhalb einer App ist es, Benutzern die Anpassung **an die Benutzererfahrung zu ermöglichen.** Geben Sie Benutzern einen kurzen Zeitraum ohne Aufgaben mit dem Gerät. Dies kann so einfach sein, wie ein Objekt im Raum zu platzieren und Benutzern zu ermöglichen, es zu bewegen oder eine Einführung in die Umgebung zu geben. Diese Zeit sollte frei von kritischen Aufgaben oder bestimmten Gesten wie Tippen in die Luft sein. Der Zweck besteht im Ermöglichen, dass Benutzer Inhalte über das Gerät anzeigen können, bevor Interaktivität erforderlich ist oder die App durchschreitet. Dies ist besonders wichtig für Erstmalige Benutzer, da sie sich mit dem Sehen von Inhalten über den holografischen Rahmen und die Art der Hologramme vertraut machen.

### <a name="large-objects"></a>Große Objekte

Häufig ist der Inhalt, den eine Benutzeroberfläche erfordert, insbesondere realer Inhalt, größer als der holografische Frame. Objekte, die normalerweise nicht in den holografischen Rahmen passen, sollten verkleinert werden, damit sie zum ersten Mal eingeführt werden (entweder in kleinerem Maßstab oder in einer Entfernung). Der Schlüssel besteht darin, **Benutzern zu ermöglichen, die vollständige Größe des Objekts anzuzeigen,** bevor die Skala den Frame überlastet. Beispielsweise sollte ein holografisches Gerüst angezeigt werden, damit es vollständig in den Rahmen passt. Auf diese Weise können Benutzer ein räumliches Verständnis der Gesamtform des Tiers bilden, bevor sie es in der Nähe des Benutzers in [die reale Dimensionierung](scale.md) bringen.

Unter Berücksichtigung der vollständigen Größe des Objekts haben Benutzer die Erwartung, wo sie sich bewegen und nach bestimmten Teilen dieses Objekts suchen sollten. In einer Erfahrung mit immersivem Inhalt ist es hilfreich, eine Möglichkeit zu haben, auf die vollständige Größe dieses Inhalts zu verweisen. Wenn die Erfahrung z. B. ein Modell eines virtuellen Hauses umfasst, hilft es, eine kleinere Version der Benutzeroberfläche zu erhalten, um zu ermitteln, wo sie sich im Haus befinden.

Ein Beispiel für das Entwerfen für große Objekte finden Sie unter [Automobile Cars](holographic-frame.md#volvo-cars).

### <a name="many-objects"></a>Viele Objekte

Erfahrungen mit vielen Objekten oder Komponenten sollten die Verwendung des vollständigen Platzes um den Benutzer in Betracht ziehen, um zu vermeiden, dass der holografische Frame direkt vor dem Benutzer überladen wird. Es wird empfohlen, die Einführung von Inhalten in eine Benutzeroberfläche zu verlangsamen, insbesondere bei Benutzeroberflächen, die viele Objekte für den Benutzer verarbeiten möchten. Der Schlüssel besteht darin, **Benutzern das Inhaltslayout** in der Umgebung zu vermitteln, was ihnen hilft, ein räumliches Verständnis dessen zu erhalten, was sie bei Inhaltsaktualisierungen umgibt.

Eine Technik, um dies zu erreichen, besteht darin, persistente Punkte (auch als Sehenswürdigkeiten bezeichnet) in der Erfahrung bereitzustellen, die Inhalte in der realen Welt verankert. Ein Orientierungspunkt könnte beispielsweise ein physisches Objekt in der realen Welt sein, z. B. eine Tabelle, in der digitale Inhalte angezeigt werden, oder ein digitales Objekt, z. B. eine Gruppe von digitalen Bildschirmen, auf denen Inhalte häufig angezeigt werden. Objekte können auch in der Ungnung des holografischen Rahmens platziert werden, um den Benutzer zu ermutigen, auf wichtige Inhalte zu achten. Die Ermittlung von Inhalten über die Grenzen hinaus kann von [Aufmerksamkeitsleitern als Hilfe verwendet werden.](holographic-frame.md#attention-directors)

Das Platzieren von Objekten in der Nisse kann benutzer dazu ermutigen, auf die Seite zu schauen, und dies kann von Aufmerksamkeitsleitern unterstützt werden, wie unten beschrieben. Weitere Informationen zu holografischen Rahmenüberlegungen finden Sie in der [Komfortdokumentation.](comfort.md#holographic-frame-considerations)

<br>

---

## <a name="interaction-considerations"></a>Überlegungen zur Interaktion

Wie bei Inhalten müssen Interaktionen in einer Mixed Reality-Erfahrung nicht auf das beschränkt sein, was der Benutzer sofort sehen kann. Interaktionen können überall im realen Raum um den Benutzer stattfinden. Diese Interaktionen können Benutzer dazu ermutigen, sich zu bewegen und Erfahrungen zu erkunden.

### <a name="attention-directors"></a>Attention-Geschäftsleitung

Das Angeben von Points of Interest oder Schlüsselinteraktionen kann entscheidend sein, um Benutzer durch eine Erfahrung zu führen. Die Benutzerfreundlichkeit und -bewegung des holografischen Rahmens kann auf subtile oder schwerhändige Weise erfolgen. Denken Sie daran, die Aufmerksamkeitsleitung mit Zeiträumen der kostenlosen Erkundung in Mixed Reality (insbesondere am Anfang einer Erfahrung) in Balance zu bringen, um zu vermeiden, dass der Benutzer überfordert wird. Im Allgemeinen gibt es zwei Arten von Aufmerksamkeitsleitung:
* **Visueller Leiter:** Die einfachste Möglichkeit, den Benutzer darüber zu informieren, dass er sich in eine bestimmte Richtung bewegen sollte, besteht in der Bereitstellung einer visuellen Anzeige. Dies kann durch einen visuellen Effekt (z. B. einen Pfad, dem der Benutzer visuell zum nächsten Teil der Benutzeroberfläche folgen kann) oder sogar als einfache Richtungspfeile erfolgen. Jeder visuelle Indikator sollte innerhalb der Umgebung des Benutzers geerbt sein, nicht an den holografischen Rahmen oder den Cursor "angefügt".
* **Audioaufnahmen: Räumlicher** [Sound](spatial-sound-design.md) kann eine leistungsstarke Möglichkeit bieten, Objekte in einer Szene zu erstellen. Sie können Benutzer über Objekte benachrichtigen, die eine Benutzeroberfläche eingeben, oder die Aufmerksamkeit auf einen bestimmten Punkt im Raum lenken, indem Sie die Ansicht des Benutzers in Richtung wichtiger Objekte verschieben. Die Verwendung von Audioaufnahmen zur Orientierung der Aufmerksamkeit des Benutzers kann feiner und weniger aufdringlich sein als visuelle Leitungen. In einigen Fällen kann es am besten sein, mit einem Audio director zu beginnen und dann zu einem visuellen Leiter zu wechseln, wenn der Benutzer den Hinweis nicht erkennt. Audioleiter können auch mit visuellen Leitungen gekoppelt werden, um einen zusätzlichen Schwerpunkt zu erhalten.

### <a name="commanding-navigation-and-menus"></a>Befehle, Navigation und Menüs

Schnittstellen in Mixed Reality-Erfahrungen sind idealerweise eng mit den digitalen Inhalten gekoppelt, die sie steuern. Daher sind Freikomma-2D-Menüs häufig nicht ideal für die Interaktion und können für Benutzer schwierig sein, die innerhalb des holografischen Rahmens zu artig sind. Für Benutzeroberflächen, die Schnittstellenelemente wie Menüs oder Textfelder erfordern, sollten Sie eine [Tag-Along-Methode](billboarding-and-tag-along.md) verwenden, um dem holografischen Frame nach einer kurzen Verzögerung zu folgen. Vermeiden Sie das Sperren von Inhalten für den Frame wie eine Kopf-auf-Kopf-Anzeige, da dies für den Benutzer destruktierend sein kann, und unterbrechen Sie das Gefühl der Immersion für andere digitale Objekte in der Szene.

Sie können Schnittstellenelemente auch direkt auf den spezifischen Inhalt platzieren, den sie steuern, sodass Interaktionen auf natürliche Weise um den physischen Raum des Benutzers erfolgen können. Teilen Sie beispielsweise ein komplexes Menü in separate Teile auf, wobei jede Schaltfläche oder Gruppe von Steuerelementen an das jeweilige Objekt angefügt ist, auf das sich die Interaktion auswirkt. Um dieses Konzept weiter zu nutzen, sollten Sie die Verwendung von [interaktiven Objekten](interactable-object.md)in Betracht ziehen.

### <a name="gaze-and-gaze-targeting"></a>Anvisieren und Anvisieren als Ziel

Der holografische Rahmen stellt ein Tool dar, mit dem Entwickler Interaktionen auslösen und auswerten können, wo die Aufmerksamkeit eines Benutzers verweilt. [Das Anvieren](gaze-and-commit.md) ist eine der [wichtigsten Interaktionen auf HoloLens,](interaction-fundamentals.md)bei der das Anvieren mit [Gesten](gaze-and-commit.md#composite-gestures) (z. B. mit Tippen in die Luft) oder [mit Der Stimme](voice-input.md) gekoppelt werden kann (wodurch kürzere, natürlichere sprachbasierte Interaktionen möglich sind). Daher ist der holografische Rahmen sowohl ein Raum für die Beobachtung digitaler Inhalte als auch für die Interaktion damit. Wenn die Benutzeroberfläche die Interaktion mit mehreren Objekten im Bereich des Benutzers erfordert (z. B. Objekte mit mehrfacher Auswahl um den Raum des Benutzers mit Anvität und Geste), ziehen Sie in Betracht, diese Objekte in die Ansicht des Benutzers zu bringen oder die Menge der erforderlichen Kopfbewegungen zu beschränken, um den Komfort des Benutzers zu [erhöhen.](comfort.md)

Anvis können auch verwendet werden, um die Aufmerksamkeit der Benutzer über eine Benutzeroberfläche zu verfolgen und zu sehen, auf welche Objekte oder Teile der Szene der Benutzer am meisten achten sollte. Dies kann insbesondere zum Debuggen einer Beerfahrung verwendet werden, sodass Analysetools wie Heatmaps erkennen können, wo Benutzer die meiste Zeit verbringen oder bestimmte Objekte oder Interaktionen fehlen. Die Nachverfolgung von Anvitatoren kann auch ein leistungsstarkes Tool für Vermittler in Erfahrungen sein (siehe [Lowe es Eye-Beispiel).](holographic-frame.md#lowes-kitchen)

Wenn Sie design concepts in action (Designkonzepte für Kopf- und Eyetracking) in Aktion sehen möchten, sehen Sie sich die Videodemo [Designing Holograms - Head Tracking and Eye Tracking]() (Entwerfen von Hologrammen – Kopfverfolgung und Eyetracking) weiter unten an:

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

<br>

---

## <a name="performance"></a>Leistung

Die richtige Verwendung des holografischen Rahmens ist für die [Leistungsqualität von grundlegender](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) Bedeutung. Eine häufige technische (und nutzbare) Herausforderung besteht darin, den Rahmen des Benutzers mit digitalen Inhalten zu überladen, wodurch die Renderingleistung beeinträchtigt wird. Verwenden Sie stattdessen den gesamten Platz um den Benutzer, um digitale Inhalte mithilfe der oben beschriebenen Verfahren zu anordnen, um den Aufwand für das Rendering zu verringern und eine optimale Anzeigequalität sicherzustellen.

Digitaler Inhalt innerhalb des holografischen Rahmens der HoloLens kann auch mit der Stabilitätsebene gekoppelt werden, um eine optimale Leistung und [](../develop/platform-capabilities-and-apis/case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md) [Hologrammstabilität zu erzielen.](../develop/platform-capabilities-and-apis/hologram-stability.md)

<br>

---

## <a name="examples"></a>Beispiele

### <a name="volvo-cars"></a>Cars (Autos)

<iframe width="940" height="530" src="https://www.youtube.com/embed/DilzwF90vec" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

In der Befahrenserfahrung von Überl. Cars sind Kunden eingeladen, sich über die Funktionen eines neuen Autos in einer HoloLens-Erfahrung zu informieren, die von einem Mitarbeiter von Einer-Mitarbeiter geleitet wird. Beim holografischen Rahmen stand Einer der Herausforderungen gegenüber: Ein Fahrzeug in voller Größe ist zu groß, um es direkt neben einem Benutzer zu setzen. Die Lösung war, die Erfahrung mit einem physischen Wahrzeichen zu beginnen, einer zentralen Tabelle in der Tafel, mit einem kleineren digitalen Modell des Autos, das über der Tabelle platziert wurde. Dadurch wird sichergestellt, dass der Benutzer das vollständige Auto sieht, wenn es eingeführt wird, was ein Gefühl des räumlichen Verständnisses ermöglicht, sobald das Auto später auf seine reale Größe anwällt.

Die Erfahrung macht sich auch mit visuellen Leitungen aus und erzeugt einen langen visuellen Effekt vom Kleinwagenmodell auf dem Tisch bis zu einer Wand im Showraum. Dies führt zu einem "magischen Fenster"-Effekt, der die vollständige Ansicht des Autos in einer Entfernung anzeigt und weitere Merkmale des Autos im realen Maßstab veranschaulicht. Die Kopfbewegung ist horizontal, ohne direkte Interaktion durch den Benutzer (stattdessen das visuelle Erfassen von Hinweisen und die Sprachausgabe der Benutzeroberfläche des Zuordnungsbenutzers).

<br>

---

### <a name="lowes-kitchen"></a>Lowe es Ausstatter

Eine Store-Erfahrung aus Lowe lädt Kunden in eine umfassende Modellierung einer Filiale ein, um verschiedene Möglichkeiten zum Umgestalten zu präsentieren, die über die HoloLens zu sehen sind. Die Filiale im Geschäft bietet einen physischen Hintergrund für digitale Objekte, eine leere Canvas von Geräten, Arbeitsflächen und Schränken, um die Mixed Reality-Erfahrung zu verbessern.

Physische Oberflächen fungieren als statische Orientierungspunkte, damit sich der Benutzer in der Benutzeroberfläche befinden kann, da ein Lowe-Mitarbeiter den Benutzer durch verschiedene Produktoptionen führt und beendet. Auf diese Weise kann der Geschäftspartner die Aufmerksamkeit des Benutzers auf den "Kühlraum" oder "Mittelpunkt der Kaffeemaschine" lenken, um digitale Inhalte zu präsentieren.

![Ein Lowe-Mitarbeiter verwendet ein Tablet, um Kunden durch die HoloLens-Benutzeroberfläche zu führen.](images/loweskitchen-750px.jpg)<br>
*Ein Lowe-Mitarbeiter verwendet ein Tablet, um Kunden durch die HoloLens-Benutzeroberfläche zu führen.*

Die Benutzerfreundlichkeit wird teilweise von einem Tablet verwaltet, das vom Lowe-Mitarbeiter gesteuert wird. Teil der Rolle des Mitarbeiters in diesem Fall wäre auch die Begrenzung übermäßiger Kopfbewegungen, die ihre Aufmerksamkeit reibungslos über die Points of Interest in der Tee leiten. Die Tablet-Benutzeroberfläche bietet auch dem Lowe-Objekt Anvitätsdaten in Form einer Wärmebildansicht der Wanne, um zu verstehen, wo sich der Benutzer befindet (z. B. in einem bestimmten Bereich der Schränkung), um ihm genauere Anleitungen zum Umgestalten zu geben.

Einen tieferen Blick auf die Experience von Lowe esUnge finden Sie in der Microsoft-Rede zur [Ignite 2016](https://www.youtube.com/watch?v=gC_4JxF0e_k).

<br>

---

### <a name="fragments"></a>Fragments

In den HoloLens-Spielfragmenten wird Ihr Lebensraum in eine virtuelle Szene mit Hinweisen und Beweisen sowie in einen virtuellen Besprechungsraum transformiert, in dem Sie mit Figuren sprechen, die sich auf Ihren Brillen und an Ihren Wänden lehnen.

![Fragmente wurden so entworfen, dass sie in der Startseite eines Benutzers stattfinden, bei der Zeichen mit realen Objekten und Oberflächen interagieren.](images/fragments-750px.jpg)<br>
*Fragmente wurden so entworfen, dass sie in der Startseite eines Benutzers stattfinden, bei der Zeichen mit realen Objekten und Oberflächen interagieren.*

Wenn Benutzer die Benutzererfahrung anfänglich beginnen, erhalten sie eine kurze Anpassungsphase mit wenig bis gar keiner Interaktion. Stattdessen wird empfohlen, sich selbst zu umschauen und sich zu orientieren und dafür zu sorgen, dass der Raum dem interaktiven Inhalt des Spiels ordnungsgemäß zugeordnet ist.

Während der gesamten Benutzererfahrung werden Zeichen zu Schwerpunkten und fungieren als visuelle Steller (Kopfbewegungen zwischen Zeichen, Hin- oder Gesten in Richtung von Interessenbereichen). Das Spiel basiert auch auf prominenteren visuellen Hinweise, wenn ein Benutzer zu lange benötigt, um ein Objekt oder Ereignis zu finden, und stark räumliche Audiodaten nutzt (insbesondere bei Zeichenstimmen beim Eintritt in eine Szene).

<br>

---

### <a name="destination-mars"></a>Ziel: Mars

In der Destination: Mars-Umgebung, die im [Space Center der NASA](https://blogs.windows.com/devices/2016/09/19/hololens-experience-destination-mars-now-open-at-kennedy-space-center-visitor-complex/)vorgestellt wurde, wurden Besucher zu einem immersiven Trip zur Oberfläche des Mars eingeladen, der von einer virtuellen Darstellung des Astronauten Aldrin des Astronauten Geleitet wird.

![Ein virtueller Aldrin-Aldrin wird zum Schwerpunkt für Benutzer in Destination: Mars.](images/destinationmars-750px.png)<br>
*Ein virtueller Aldrin-Aldrin wird zum Schwerpunkt für Benutzer in Destination: Mars.*

Als immersive Benutzeroberfläche wurden diese Benutzer aufgefordert, sich umzusehen und ihren Kopf in alle Richtungen zu bewegen, um die Virtuelle Martian-Landschaft zu sehen. Um den Komfort der Benutzer zu gewährleisten, bildeten die Sprachausgabe und die virtuelle Präsenz von Fly Aldrin während der gesamten Umgebung einen zentralen Punkt. Diese virtuelle Aufzeichnung von Mouse (erstellt von [microsofts Mixed Reality-Aufnahme Studios)](https://www.microsoft.com/mixed-reality/capture-studios)wird in echter, menschlicher Größe in der Ecke des Raumes angezeigt, sodass Benutzer ihn nahezu vollständig sehen können. Die Sprachausgabe von Summer hat die Benutzer angewiesen, sich auf verschiedene Punkte in der Umgebung zu konzentrieren (z. B. eine Gruppe von Marsgestein auf dem Boden oder einen Höhenbereich in der Entfernung) mit bestimmten Szenenänderungen oder Objekten, die von ihm eingeführt wurden.

![Die virtuellen Sprachausgabe verfolgt die Bewegung eines Benutzers und erstellt einen leistungsfähigen Fokuspunkt in der gesamten Umgebung.](images/gazereset-750px.png)<br>
*Die virtuellen Sprachausgabe verfolgt die Bewegung eines Benutzers und erstellt einen leistungsfähigen Fokuspunkt in der gesamten Umgebung.*

Die realistische Darstellung von "Username" bot einen leistungsfähigen Fokuspunkt, der mit feinen Techniken ausgestattet war, um dem Benutzer das Gefühl zu geben, als wäre er da und sprach mit Ihnen. Während sich der Benutzer um die Benutzeroberfläche bewegt, wechselt Der Benutzer zu einem Schwellenwert, bevor er zu einem neutralen Zustand zurückkehrt, wenn der Benutzer zu weit über seine Peripherie hinaus bewegt wird. Wenn der Benutzer vollständig von "Trend" aussieht (z. B. um etwas an anderer Stelle in der Szene zu betrachten), dann wieder zu "Überschnall", konzentriert sich die direktionale Position der Sprachausgabe wieder auf den Benutzer. Techniken wie diese bieten ein leistungsfähiges Gefühl für Immersion und schaffen einen Fokuspunkt innerhalb des holografischen Rahmens, wodurch übermäßige Kopfbewegungen reduziert und [benutzerfreundlichkeit](comfort.md)fördert werden.

## <a name="see-also"></a>Weitere Informationen
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Komfort](comfort.md)
* [Skalieren](scale.md)
* [Anvisieren mit dem Kopf und Verweilen](gaze-and-dwell.md)
* [Hologrammstabilität](../develop/platform-capabilities-and-apis/hologram-stability.md)
