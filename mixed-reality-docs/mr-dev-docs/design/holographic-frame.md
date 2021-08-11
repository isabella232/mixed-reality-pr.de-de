---
title: Holografischer Rahmen
description: Erfahren Sie, wie Benutzer die Welt von Mixed Reality über den holografischen Rahmen sehen und wie Sie die Erfahrung am besten gestalten.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/25/2020
ms.topic: article
keywords: HoloLens, Windows Mixed Reality, holografischer Rahmen, Sichtfeld, FOV, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit, Interaktionen, Navigation, Menü
ms.openlocfilehash: be24f2b583541e6ed0adff25b3d8edd6c3fe5285aea93d0a4d6df8ee61e5c070
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226380"
---
# <a name="holographic-frame"></a>Holografischer Rahmen

Benutzer sehen die Welt der Mixed Reality durch ein rechteckiges Ansichtsfenster, das von ihren Headsets betrieben wird. Bei HoloLens wird dieser rechteckige Bereich als holografischer Rahmen bezeichnet und ermöglicht den Benutzern, die digitalen Inhalte zu sehen, die der realen Welt ihrer Umgebung überlagert sind. Das Entwerfen von Benutzeroberflächen, die für den holografischen Rahmen optimiert sind, schafft Möglichkeiten, entschärft Herausforderungen und verbessert die Benutzerfreundlichkeit von Mixed Reality-Anwendungen.

## <a name="designing-for-content"></a>Entwerfen für Inhalt

Designer haben häufig die Notwendigkeit, den Umfang ihrer Benutzererfahrung auf das zu beschränken, was dem Benutzer sofort angezeigt wird, und dabei die reale Skalierung zu versieren, um sicherzustellen, dass der Benutzer ein Objekt in seiner Gesamtheit sieht. Ebenso überladen Designer mit komplexen Anwendungen oft den holografischen Rahmen mit Inhalten, überladen Benutzer mit schwierige Interaktionen und unübersichtlichen Schnittstellen. Designer, die Mixed Reality-Inhalte erstellen, müssen die Benutzererfahrung nicht auf die direkte Vor- und Nachsicht des Benutzers beschränken. Wenn die physische Welt um den Benutzer herum zugeordnet ist, sollten alle diese Oberflächen als potenzieller Zeichenbereich für digitale Inhalte und Interaktionen betrachtet werden. Das richtige Design von Interaktionen und Inhalten innerhalb einer Umgebung sollte den Benutzer dazu bewegen, sich in seinen Raum zu bewegen, seine Aufmerksamkeit auf wichtige Inhalte zu richten und das volle Potenzial von Mixed Reality zu erkennen.

Das vielleicht wichtigste Verfahren zur Förderung von Bewegung und Untersuchung innerhalb einer App ist es, Benutzern die Anpassung **an die Benutzererfahrung zu ermöglichen.** Geben Sie Benutzern einen kurzen Zeitraum ohne Aufgaben mit dem Gerät. Dies kann so einfach sein, wie ein Objekt im Raum zu platzieren und Benutzern zu ermöglichen, es zu bewegen oder eine Einführung in die Umgebung zu geben. Diese Zeit sollte frei von kritischen Aufgaben oder bestimmten Gesten wie Tippen auf die Luft sein. Der Zweck besteht im Ermöglichen, dass Benutzer Inhalte über das Gerät anzeigen können, bevor Interaktivität erforderlich ist oder die App durchschreitet. Dies ist besonders wichtig für Erstbenutzer, da sie inhalte durch den holografischen Rahmen und die Natur von Hologrammen sehen können.

### <a name="large-objects"></a>Große Objekte

Häufig ist der Inhalt, den eine Erfahrung erfordert, insbesondere der reale Inhalt, größer als der holografische Rahmen. Objekte, die normalerweise nicht in den holografischen Rahmen passen, sollten verkleinert werden, damit sie bei der ersten Einführung (in kleinerem Umfang oder in der Entfernung) eingeführt werden. Der Schlüssel besteht im **Erkennen der vollständigen** Größe des Objekts, bevor der Frame durch die Skalierung überlastet wird. Beispielsweise sollte ein holografisches Gerüst angezeigt werden, damit es vollständig in den Rahmen passt. Dies ermöglicht es Benutzern, ein räumliches Verständnis der Gesamtform des Tiers zu erhalten, bevor es in der Nähe des Benutzers auf die reale [Skalierung](scale.md) skaliert wird.

Bei der vollständigen Größe des Objekts haben Benutzer die Erwartung, wo sie sich bewegen und nach bestimmten Teilen dieses Objekts suchen müssen. In einer Erfahrung mit immersivem Inhalt ist es hilfreich, auf die gesamte Größe dieses Inhalts zurück verweisen zu können. Wenn die Erfahrung z. B. das Durchgehen eines Modells eines virtuellen Hauses umfasst, ist es hilfreich, eine kleinere Version der Umgebung in der Größe des Hauses zu verwenden, um den Ort zu finden, an dem sie sich im Haus befinden.

Ein Beispiel für das Entwerfen für große Objekte finden Sie unter [Cars .](holographic-frame.md#volvo-cars)

### <a name="many-objects"></a>Viele Objekte

Erfahrungen mit vielen Objekten oder Komponenten sollten die Verwendung des gesamten Platzes um den Benutzer in Betracht ziehen, um zu vermeiden, dass der holografische Rahmen direkt vor dem Benutzer überladen wird. Es wird empfohlen, die Einführung von Inhalten in eine Benutzeroberfläche zu verlangsamen, insbesondere bei Benutzeroberflächen, die viele Objekte für den Benutzer bedienen möchten. Der Schlüssel besteht **im** Verstehen des Inhaltslayouts in der Umgebung, wodurch sie ein räumliches Verständnis dessen erhalten, was sich um sie herum als Inhaltsaktualisierungen befindet.

Ein Verfahren, um dies zu erreichen, besteht in der Bereitstellung dauerhafter Punkte (auch als Sehenswürdigkeiten bezeichnet) in der Erfahrung, die Inhalte in der realen Welt verankert. Ein Orientierungspunkt kann beispielsweise ein physisches Objekt in der realen Welt sein, z. B. eine Tabelle, in der digitale Inhalte angezeigt werden, oder ein digitales Objekt, z. B. eine Gruppe von digitalen Bildschirmen, auf denen Inhalte häufig angezeigt werden. Objekte können auch in der Freundlichkeit des holografischen Rahmens platziert werden, um den Benutzer zu ermutigen, auf wichtige Inhalte zu achten. Die Ermittlung von Inhalten über die Grenzen hinaus kann von [Aufmerksamkeitsleitern als Hilfe verwendet werden.](holographic-frame.md#attention-directors)

Das Platzieren von Objekten in der Nisse kann benutzer dazu ermutigen, auf die Seite zu schauen, und dies kann von Aufmerksamkeitsleitern unterstützt werden, wie unten beschrieben. Weitere Informationen zu Überlegungen zu holografischen Rahmen finden Sie in der [Komfortdokumentation.](comfort.md#holographic-frame-considerations)

<br>

---

## <a name="interaction-considerations"></a>Überlegungen zur Interaktion

Wie bei Inhalten müssen Interaktionen in einer Mixed Reality-Erfahrung nicht auf das beschränkt werden, was der Benutzer sofort sehen kann. Interaktionen können überall im realen Raum um den Benutzer stattfinden. Diese Interaktionen können Benutzer dazu ermutigen, sich zu bewegen und Erfahrungen zu erkunden.

### <a name="attention-directors"></a>Attention-Geschäftsleitung

Das Angeben von Points of Interest oder Schlüsselinteraktionen kann entscheidend sein, um Benutzer durch eine Erfahrung zu führen. Die Benutzerfreundlichkeit und -bewegung des holografischen Rahmens kann auf subtile oder schwerhändige Weise erfolgen. Denken Sie daran, die Aufmerksamkeitsleitung mit Zeiträumen der kostenlosen Erkundung in Mixed Reality (insbesondere am Anfang einer Erfahrung) in Balance zu bringen, um zu vermeiden, dass der Benutzer überfordert wird. Im Allgemeinen gibt es zwei Arten von Aufmerksamkeitsleitung:
* **Visueller Leiter:** Die einfachste Möglichkeit, den Benutzer darüber zu informieren, dass er sich in eine bestimmte Richtung bewegen sollte, besteht in der Bereitstellung einer visuellen Anzeige. Dies kann durch einen visuellen Effekt (z. B. einen Pfad, dem der Benutzer visuell zum nächsten Teil der Benutzeroberfläche folgen kann) oder sogar als einfache Richtungspfeile erfolgen. Jeder visuelle Indikator sollte innerhalb der Umgebung des Benutzers geerbt sein, nicht an den holografischen Rahmen oder den Cursor "angefügt".
* **Audioaufnahmen: Räumlicher** [Sound](spatial-sound-design.md) kann eine leistungsstarke Möglichkeit bieten, Objekte in einer Szene zu erstellen. Sie können Benutzer darauf aufmerksam machen, dass Objekte in eine Benutzeroberfläche eintreten, oder sie können die Aufmerksamkeit auf einen bestimmten Punkt im Raum richten, indem Sie die Ansicht des Benutzers in Richtung wichtiger Objekte verschieben. Die Verwendung von Audioaufnahmen, um die Aufmerksamkeit des Benutzers zu leiten, kann feiner und weniger aufdringlich sein als visueller Leiter. In einigen Fällen kann es am besten sein, mit einem Audio director zu beginnen und dann zu einem visuellen Director zu wechseln, wenn der Benutzer den Hinweis nicht erkennt. Audioleiter können auch mit visuellen Leitern gekoppelt werden, um zusätzlichen Schwerpunkt zu bieten.

### <a name="commanding-navigation-and-menus"></a>Befehle, Navigation und Menüs

Schnittstellen in Mixed Reality-Oberflächen werden idealerweise eng mit den digitalen Inhalten gekoppelt, die sie steuern. Daher sind frei schwebende 2D-Menüs oft nicht ideal für die Interaktion und können für Benutzer innerhalb des holografischen Rahmens zu kompliziert sein. Für Benutzeroberflächen, die Schnittstellenelemente wie Menüs oder Textfelder erfordern, sollten Sie die Verwendung einer [Tag-Along-Methode](billboarding-and-tag-along.md) in Betracht ziehen, um dem holografischen Rahmen nach einer kurzen Verzögerung zu folgen. Vermeiden Sie das Sperren von Inhalten für den Frame wie eine Kopf-auf-Anzeige, da dies für den Benutzer desordnend sein und das Gefühl der Immersion für andere digitale Objekte in der Szene unterbricht.

Sie können Schnittstellenelemente auch direkt auf den spezifischen Inhalt platzieren, den sie steuern, sodass Interaktionen auf natürliche Weise um den physischen Raum des Benutzers stattfinden können. Teilen Sie beispielsweise ein komplexes Menü in separate Teile auf, bei dem jede Schaltfläche oder Gruppe von Steuerelementen an das bestimmte Objekt angefügt ist, auf das die Interaktion wirkt. Um dieses Konzept weiter zu verstehen, sollten Sie die Verwendung von [interagierbaren Objekten in Betracht ziehen.](interactable-object.md)

### <a name="gaze-and-gaze-targeting"></a>Anving und Anving als Ziel

Der holografische Rahmen stellt ein Tool für den Entwickler dar, um Interaktionen auszulösen und zu bewerten, wo die Aufmerksamkeit eines Benutzers verweilt. [Anving](gaze-and-commit.md) ist eine der wichtigsten Interaktionen auf [HoloLens,](interaction-fundamentals.md)bei denen das Anving mit Gesten [(z.](gaze-and-commit.md#composite-gestures) B. mit Tippen in die Luft) oder einer Stimme [(die](voice-input.md) kürzere, natürlichere sprachbasierte Interaktionen ermöglicht) gekoppelt werden kann. Dies macht den holografischen Rahmen zu einem Raum für die Beobachtung digitaler Inhalte und die Interaktion damit. Wenn die Benutzeroberfläche die Interaktion mit mehreren Objekten um den Raum des Benutzers erfordert (z. B. Objekte mit mehrfacher Auswahl um den Raum des Benutzers mit Anvität und Geste), ziehen Sie in Betracht, diese Objekte in die Ansicht des Benutzers zu bringen oder die Menge der erforderlichen Kopfbewegungen zu beschränken, um den Benutzerfreundlichkeit zu [erhöhen.](comfort.md)

Anvis können auch verwendet werden, um die Aufmerksamkeit der Benutzer über eine Benutzeroberfläche zu verfolgen und zu sehen, auf welche Objekte oder Teile der Szene der Benutzer am meisten achten sollte. Dies kann insbesondere zum Debuggen einer Beerfahrung verwendet werden, sodass Analysetools wie Heatmaps erkennen können, wo Benutzer die meiste Zeit verbringen oder bestimmte Objekte oder Interaktionen fehlen. Die Nachverfolgung von Anvitatoren kann auch ein leistungsstarkes Tool für Vermittler in Beerlebnissen sein (siehe [Lowes Beispiel für Die 2016-30-Uhr).](holographic-frame.md#lowes-kitchen)

Wenn Sie design concepts in action (Designkonzepte für Kopf- und Eyetracking) in Aktion sehen möchten, sehen Sie sich die Videodemo **Designing Hologramme – Head Tracking and Eye Tracking** weiter unten an:

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

*Dieses Video wurde aus der HoloLens 2-App „Entwerfen von Hologrammen“ aufgenommen. Laden Sie die vollständige Erfahrung [hier](https://aka.ms/dhapp) herunter, und genießen Sie sie.*

<br>

---

## <a name="performance"></a>Leistung

Die richtige Verwendung des holografischen Rahmens ist für die [Leistungsqualität von grundlegender](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) Bedeutung. Eine häufige technische (und nutzbare) Herausforderung besteht darin, den Rahmen des Benutzers mit digitalen Inhalten zu überladen, wodurch die Renderingleistung beeinträchtigt wird. Verwenden Sie stattdessen den gesamten Platz um den Benutzer, um digitale Inhalte mithilfe der oben beschriebenen Verfahren zu anordnen, um den Aufwand für das Rendering zu verringern und eine optimale Anzeigequalität sicherzustellen.

Digitaler Inhalt innerhalb des holografischen Rahmens des HoloLens kann [](../develop/platform-capabilities-and-apis/case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md) auch mit der Stabilitätsebene gekoppelt werden, um eine optimale Leistung und [Hologrammstabilität zu erzielen.](../develop/platform-capabilities-and-apis/hologram-stability.md)

<br>

---

## <a name="examples"></a>Beispiele

### <a name="volvo-cars"></a>Cars (Autos)

<iframe width="940" height="530" src="https://www.youtube.com/embed/DilzwF90vec" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

In der Befahrenserfahrung von Durchkn. Autos sind Kunden eingeladen, sich mit den Funktionen eines neuen Autos vertraut zu machen, HoloLens einer Mitarbeiterin geführt wird. Beim holografischen Rahmen stand Ein Fahrzeug in voller Größe zu groß, um es direkt neben einem Benutzer zu setzen. Die Lösung war, die Erfahrung mit einem physischen Wahrzeichen zu beginnen, einer zentralen Tabelle in der Tafel, mit einem kleineren digitalen Modell des Autos, das über der Tabelle platziert wurde. Dadurch wird sichergestellt, dass der Benutzer das vollständige Auto sieht, wenn es eingeführt wird. Dadurch wird ein Gefühl des räumlichen Verständnisses ermöglicht, sobald das Auto später in der Praxis auf seine tatsächliche Größe anwächst.

Die Erfahrung von Intendanten nutzt auch visuelle Leiter und sorgt so für einen langen visuellen Effekt vom Kleinwagenmodell auf dem Tisch bis zu einer Wand im Showraum. Dies führt zu einem "magischen Fenster"-Effekt, der die vollständige Ansicht des Autos aus der Entfernung zeigt und weitere Merkmale des Autos in der realen Welt veranschaulicht. Die Kopfbewegung ist horizontal, ohne direkte Interaktion des Benutzers (stattdessen visuelles Erfassen von Cues und der Darstellung der Erfahrung durch die Mitarbeiterin der -Mitarbeiterin).

<br>

---

### <a name="lowes-kitchen"></a>Lowe esUnge

Eine Store-Erfahrung von Lowe lädt Kunden zu einem vollständigen Modell einer Este aus, um verschiedene Umgestaltungsmöglichkeiten zu präsentieren, die durch die HoloLens. Die Schränke im Laden bieten eine physische Kulisse für digitale Objekte, eine leere Canvas mit Geräten, Arbeitsgeräten und Schränken für die Mixed Reality-Erfahrung.

Physische Oberflächen fungieren als statische Orientierungszeichen für den Benutzer, um sich in der Benutzeroberfläche zu bodenten, da der Mitarbeiter von Lowe den Benutzer durch verschiedene Produktoptionen führt und abschließt. Auf diese Weise kann der Mitarbeiter die Aufmerksamkeit des Benutzers auf den "Kühlraum" oder "Mittelpunkt der Kaffeemaschine" richten, um digitale Inhalte zu präsentieren.

![Ein Mitarbeiter von Lowe verwendet ein Tablet, um Kunden durch die HoloLens zu führen.](images/loweskitchen-750px.jpg)<br>
*Eine Mitarbeiterin von Lowe verwendet ein Tablet, um Kunden durch die HoloLens führen.*

Die Benutzererfahrung wird teilweise von einer Tablet-Benutzeroberfläche verwaltet, die vom Mitarbeiter von Lowe gesteuert wird. Ein Teil der Rolle des Mitarbeiters wäre in diesem Fall auch die Beschränkung übermäßiger Kopfbewegungen, die ihre Aufmerksamkeit reibungslos über die Points of Interest in der 2010-2016-2016-2016-2016 richten. Die Tablet-Benutzeroberfläche bietet lowe auch Anvitätsdaten in Form einer Wärmebildansicht der Wanne, um zu verstehen, wo sich der Benutzer befindet (z. B. in einem bestimmten Bereich der Schränkung), um ihnen genauere Anleitungen für die Umgestaltung zu geben.

Einen tieferen Blick auf die Experience von Lowe esUnge finden Sie in der Microsoft-Rede zur [Ignite 2016](https://www.youtube.com/watch?v=gC_4JxF0e_k).

<br>

---

### <a name="fragments"></a>Fragments

Im HoloLens Spiel Fragmente wird Ihr Leben in eine virtuelle Szene mit Tatverbrechen umgewandelt, die Hinweise und Beweise zeigt, und in einen virtuellen Besprechungsraum, in dem Sie mit Zeichen sprechen, die sich auf Ihrem Äte befinden und sich an Ihren Wänden befinden.

![Fragmente wurden so entworfen, dass sie in der Startseite eines Benutzers stattfinden, mit Zeichen, die mit realen Objekten und Oberflächen interagieren.](images/fragments-750px.jpg)<br>
*Fragmente wurden so entworfen, dass sie in der Startseite eines Benutzers stattfinden, mit Zeichen, die mit realen Objekten und Oberflächen interagieren.*

Wenn Benutzer die Benutzeroberfläche anfänglich starten, erhalten sie einen kurzen Anpassungszeitraum mit wenig bis gar keiner Interaktion. Stattdessen wird empfohlen, sich umzusehen und sich zu orientieren und sicherzustellen, dass der Raum ordnungsgemäß für die interaktiven Inhalte des Spiels zugeordnet ist.

Während der gesamten Benutzeroberfläche werden Zeichen zu Mittelpunkten und fungieren als visuelles Erscheinungsbild (Kopfbewegungen zwischen Zeichen, Drehen zum Aussehen oder Gesten zu interessanten Bereichen). Das Spiel basiert auch auf hervorgehobeneren visuellen Hinweisen, wenn ein Benutzer zu lange nach einem Objekt oder Ereignis sucht und räumliche Audioinhalte stark nutzt (insbesondere bei Zeichenstimmen beim Eintreten in eine Szene).

<br>

---

### <a name="destination-mars"></a>Ziel: Mars

Unter Destination: Mars experience featured at [NASA es Centre (Destination:](https://blogs.windows.com/devices/2016/09/19/hololens-experience-destination-mars-now-open-at-kennedy-space-center-visitor-complex/)Mars) (Ziel: Mars-Erfahrung, die im Space Center der NASA vorgestellt wird) wurden Besucher zu einer immersiven Reise auf die Marsoberfläche eingeladen, die von einer virtuellen Darstellung des Astronauten Msi Aldrin geleitet wurde.

![Ein virtueller Switch-Aldrin wird zum Mittelpunkt für Benutzer in Destination: Mars.](images/destinationmars-750px.png)<br>
*Ein virtueller Switch-Aldrin wird zum Mittelpunkt für Benutzer in Destination: Mars.*

Als immersive Benutzeroberfläche wurden diese Benutzer aufgefordert, sich umzusehen und ihren Kopf in alle Richtungen zu bewegen, um die Virtuelle Martian-Landschaft zu sehen. Um den Komfort der Benutzer zu gewährleisten, bildeten die Sprachausgabe und die virtuelle Präsenz von Fly Aldrin während der gesamten Umgebung einen zentralen Punkt. Diese virtuelle Aufzeichnung von Mouse (erstellt von [den Mixed Reality-Aufnahme Studio von Microsoft)](https://www.microsoft.com/mixed-reality/capture-studios)befindet sich in realer, menschlicher Größe in der Ecke des Raumes, sodass Benutzer ihn nahezu vollständig sehen können. Die Sprachausgabe von Summer hat Benutzer angewiesen, sich auf verschiedene Punkte in der Umgebung zu konzentrieren (z. B. eine Gruppe von Martergestein auf dem Boden oder einen Höhenbereich in der Entfernung) mit bestimmten Szenenänderungen oder Objekten, die von ihm eingeführt wurden.

![Die virtuellen Sprachausgabe verfolgt die Bewegung eines Benutzers und erstellt einen leistungsfähigen Fokuspunkt in der gesamten Umgebung.](images/gazereset-750px.png)<br>
*Die virtuellen Sprachausgabe verfolgt die Bewegung eines Benutzers und erstellt einen leistungsfähigen Fokuspunkt in der gesamten Umgebung.*

Die realistische Darstellung von "Username" bot einen leistungsfähigen Fokuspunkt, der mit feinen Techniken ausgestattet war, um dem Benutzer das Gefühl zu geben, als wäre er da und sprach mit Ihnen. Während sich der Benutzer um die Benutzeroberfläche bewegt, wechselt Der Trend zu Einem Schwellenwert, bevor er zu einem neutralen Zustand zurückkehrt, wenn der Benutzer zu weit über seine Peripherie hinaus bewegt wird. Wenn der Benutzer vollständig von "Trend" aussieht (z. B. um etwas an anderer Stelle in der Szene zu betrachten), dann wieder zurück zu "Summer", konzentriert sich die direktionale Position der Sprachausgabe wieder auf den Benutzer. Techniken wie diese bieten ein leistungsfähiges Gefühl für Immersion und schaffen einen Fokuspunkt innerhalb des holografischen Rahmens, wodurch übermäßige Kopfbewegungen reduziert und [benutzerfreundlichkeit](comfort.md)fördert werden.

## <a name="see-also"></a>Siehe auch
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Komfort](comfort.md)
* [Skalieren](scale.md)
* [Anvisieren mit dem Kopf und Verweilen](gaze-and-dwell.md)
* [Hologrammstabilität](../develop/platform-capabilities-and-apis/hologram-stability.md)
