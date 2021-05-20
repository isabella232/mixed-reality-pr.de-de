---
title: Räumliche Abbildung
description: Die räumliche Zuordnung bietet eine detaillierte Darstellung von realen Oberflächen in der Umgebung um holoLens.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Räumliche Zuordnung, HoloLens, Mixed Reality, Oberflächenrekonstruktion, Mesh, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit, Szenenverständnis, Weltgitternetz, Verdeckung, Physik, Navigation, Oberflächenbeoker, Rendering, Meshverarbeitung
ms.openlocfilehash: 3268f25f86cdfea3aa1ae0b77c4fbeb9aa0ce1b9
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196425"
---
# <a name="spatial-mapping"></a>Räumliche Abbildung

Die räumliche Zuordnung bietet eine detaillierte Darstellung von realen Oberflächen in der Umgebung um holoLens, sodass Entwickler eine überzeugende Mixed Reality-Erfahrung erstellen können. Durch das Zusammenführen der realen Welt mit der virtuellen Welt kann eine Anwendung Hologramme real erscheinen lassen. Anwendungen können auch auf natürlichere Weise mit den Erwartungen der Benutzer übereinstimmen, indem sie vertrautes Verhalten und Interaktionen in der realen Welt bereitstellen.

<br>

>[!VIDEO https://www.youtube.com/embed/zff2aQ1RaVo]

## <a name="device-supports"></a>Geräteunterstützung

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Feature</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1. Generation)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Räumliche Abbildung</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>


## <a name="why-is-spatial-mapping-important"></a>Warum ist räumliche Zuordnung wichtig?

Räumliche Zuordnung macht es möglich, Objekte auf realen Oberflächen zu platzieren. Dies hilft, Objekte in der Welt des Benutzers zu verankern, und nutzt echte Tiefenhinweise. Das Verdecken Ihrer Hologramme basierend auf anderen Hologrammen und Objekten aus der realen Welt hilft dem Benutzer zu überzeugen, dass sich diese Hologramme tatsächlich in ihrem Raum befinden. Hologramme, die im Raum gleiten oder sich mit dem Benutzer bewegen, werden sich nicht so real anfühlen. Platzieren Sie nach Möglichkeit Elemente aus Komfortgründen.

Visualisieren von Oberflächen beim Platzieren oder Verschieben von Hologrammen (verwenden Sie ein projiziertes Raster). Dies hilft Benutzern zu wissen, wo sie ihre Hologramme am besten platzieren können, und zeigt, ob die Stelle, an der sie das Hologramm platzieren möchten, nicht zugeordnet ist. Sie können dem Benutzer "Elemente zuwenden", wenn sie zu weit in einem Winkel landen.

## <a name="conceptual-overview"></a>Konzeptionelle Übersicht

![Gitteroberflächen, die einen Raum abdecken](images/SurfaceReconstruction.jpg)<br>
*Ein Beispiel für ein Raumzuordnungsgitter, das einen Raum abdeckt*

Die beiden primären Objekttypen, die für die räumliche Zuordnung verwendet werden, sind "Spatial Surface Observer" und "Spatial Surface".

Die Anwendung stellt dem Spatial Surface Observer ein oder mehrere begrenzungsvolumes zur Verfügung, um die Bereiche des Raums zu definieren, in denen die Anwendung räumliche Zuordnungsdaten empfangen möchte. Für jedes dieser Volumes stellt die räumliche Zuordnung der Anwendung einen Satz räumlicher Oberflächen zur Verfügung.

Diese Volumes können fest (an einem festen Ort basierend auf der realen Welt) oder an die HoloLens angefügt sein (sie bewegen sich mit der HoloLens, während sie sich durch die Umgebung bewegen, aber nicht drehen). Jede räumliche Oberfläche beschreibt reale Oberflächen in einem kleinen Raumvolumen, dargestellt als Dreiecksgitternetz, das an ein weltgesperrte räumliches [Koordinatensystem angefügt ist.](coordinate-systems.md)

Wenn HoloLens neue Daten über die Umgebung sammelt und Änderungen an der Umgebung auftreten, werden räumliche Oberflächen angezeigt, verschwinden und ändern sich.

## <a name="spatial-awareness-design-concepts-demo"></a>Demo zu Entwurfskonzepten für räumliche Wahrnehmung

Wenn Sie räumliche Wahrnehmungsentwurfskonzepte in Aktion sehen möchten, sehen Sie sich unsere Videodemo **Designing Holograms - Spatial Awareness** (Entwerfen von Hologrammen – räumliche Wahrnehmung) weiter unten an. Wenn Sie fertig sind, fahren Sie fort, um ausführlichere Informationen zu bestimmten Themen zu erhalten.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

*Dieses Video wurde aus der App "Entwerfen von Hologrammen" HoloLens 2 aufgenommen. Laden Sie hier herunter, und profitieren Sie [von der vollständigen Erfahrung.](https://aka.ms/dhapp)*

## <a name="spatial-mapping-vs-scene-understanding-worldmesh"></a>Räumliche Zuordnung im Vergleich zu Scene Understanding WorldMesh

Für HoloLens 2 ist es möglich, eine statische Version der räumlichen Zuordnungsdaten mithilfe des [Scene Understanding SDK](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md) (EnableWorldMesh-Einstellung) abfragt. Hier sind die Unterschiede zwischen zwei Möglichkeiten für den Zugriff auf die räumlichen Zuordnungsdaten:
* SPATIAL MAPPING-API:
   * Begrenzter Bereich: Die räumlichen Zuordnungsdaten, die Anwendungen in einer begrenzten Größe zur Verfügung stehen, die "Blase" um den Benutzer herum zwischengespeichert wird.
   * Bietet Updates für geänderte Gitternetzregionen mit geringer Latenz über SurfacesChanged-Ereignisse.
   * Variable Detailebene, die durch den Parameter Dreiecke pro kubischer Verbrauchsmessung gesteuert wird.
* Scene understanding SDK:
   * Unbegrenzter Bereich: Stellt alle gescannten räumlichen Zuordnungsdaten innerhalb des Abfrageradius zur Verfügung.
   * Stellt eine statische Momentaufnahme der räumlichen Zuordnungsdaten zur Zum Abrufen der aktualisierten Räumlichen Zuordnungsdaten muss eine neue Abfrage für das gesamte Gitternetz ausgeführt werden.
   * Konsistente Detailebene, die von der RequestedMeshLevelOfDetail-Einstellung gesteuert wird.

## <a name="what-influences-spatial-mapping-quality"></a>Was wirkt sich auf die Qualität der räumlichen Zuordnung aus?

Die Häufigkeit und der Schweregrad dieser Fehler können sich auf mehrere Faktoren auswirken, die [hier](/hololens/hololens-environment-considerations)ausführlich beschrieben werden.  Sie sollten Ihre Anwendung jedoch so entwerfen, dass der Benutzer seine Ziele auch bei Fehlern in den Räumlichen Zuordnungsdaten erreichen kann.

## <a name="common-usage-scenarios"></a>Allgemeine Verwendungsszenarios

![Abbildungen allgemeiner Verwendungsszenarien für räumliche Zuordnungen: Platzierung, Verdeckung, Physik und Navigation](images/sm-concepts-1000px.png)

### <a name="placement"></a>Platzierung

Die räumliche Zuordnung bietet Anwendungen die Möglichkeit, dem Benutzer natürliche und vertraute Interaktionsformen zu präsentieren. was kann natürlicher sein, als ihr Telefon auf dem Tisch abzulegen?

Das Einschränken der Platzierung von Hologrammen (oder allgemeiner gesagt jede Auswahl räumlicher Positionen), die auf Oberflächen liegt, ermöglicht eine natürliche Zuordnung von 3D (Punkt im Raum) zu 2D (Punkt auf der Oberfläche). Dadurch wird die Menge der Informationen reduziert, die der Benutzer für die Anwendung bereitstellen muss, und die Interaktionen des Benutzers werden schneller, einfacher und präziser. Dies ist richtig, da "Distance Away" nicht für die physische Kommunikation mit anderen Personen oder Computern verwendet wird. Wenn wir mit dem Finger zeigen, geben wir eine Richtung, aber keinen Abstand an.

Ein wichtiger Nachteil hierbei ist, dass, wenn eine Anwendung Abstand von der Richtung hergeleitet (z. B. durch einen Raycast entlang der Anviertrichtung des Benutzers, um die nächstgelegene räumliche Oberfläche zu finden), ergebnisse liefern muss, die der Benutzer zuverlässig vorhersagen kann. Andernfalls verliert der Benutzer sein Gefühl der Kontrolle, und dies kann schnell frustrierend werden. Eine Methode, die dabei hilft, besteht darin, mehrere Raycasts statt nur eines zu verwenden. Die Aggregatergebnisse sollten reibungsloser und besser vorhersagbar sein und weniger anfällig für die Einflussnahme durch vorübergehende "Ausreißerergebnisse" sein (dies kann durch Lichtstrahl verursacht werden, der kleine Löcher durchläuft oder kleine Teile der Geometrie erreicht, die dem Benutzer nicht bekannt sind). Aggregation oder Glättung kann auch im Laufe der Zeit ausgeführt werden. Beispielsweise können Sie die maximale Geschwindigkeit begrenzen, mit der ein Hologramm in der Entfernung zum Benutzer variieren kann. Es kann auch helfen, einfach den minimalen und maximalen Abstandswert zu beschränken, damit das hologramm, das bewegt wird, nicht plötzlich in die Entfernung stürzt oder wieder in das Gesicht des Benutzers stürzt.

Anwendungen können auch die Form und Richtung von Oberflächen verwenden, um die Hologrammplatzierung zu leiten. Ein holografischer Sessel sollte nicht durch Dieben schweben und mit dem Boden leeren, auch wenn er etwas ungleichmäßig ist. Diese Art von Funktionalität würde wahrscheinlich von der Verwendung von physikalischen Kollisionen anstelle von Raycasts abhängig sein, es gelten jedoch ähnliche Bedenken. Wenn das platzierte Hologramm über viele kleine Polygone verfügt, die sich wie die Brille auf einem Sessel herausdrücken, kann es sinnvoll sein, die physikalische Darstellung dieser Polygone auf einen breiteren und reibungsloseren Bereich zu erweitern, damit sie besser über räumliche Oberflächen gleiten können, ohne zu versnieren.

Im Extremfall können Benutzereingaben vollständig vereinfacht werden, und räumliche Oberflächen können für eine vollständig automatische Hologrammplatzierung verwendet werden. Beispielsweise könnte die Anwendung einen holografischen Lichtschalter an einer anderen Stelle an der Wand platzieren, damit der Benutzer drücken kann. Der gleiche Nachteil bei der Vorhersagbarkeit gilt hier doppelt. Wenn der Benutzer die Kontrolle über die Hologrammplatzierung erwartet, die Anwendung hologramme jedoch nicht immer dort abstelle, wo sie es erwarten (wenn der Lichtschalter an einer Stelle angezeigt wird, die der Benutzer nicht erreichen kann), ist dies eine frustrierende Erfahrung. Es kann eigentlich schlechter sein, eine automatische Platzierung vorzunehmen, die die Benutzerkorrektur einen Teil der Zeit erfordert, als nur zu erfordern, dass der Benutzer die Platzierung immer selbst vornehmen muss. da eine erfolgreiche automatische Platzierung *erwartet wird,* wirkt die manuelle Korrektur wie eine Belastung!

Beachten Sie auch, dass die Fähigkeit einer Anwendung, räumliche Oberflächen für die Platzierung zu verwenden, stark von der Scanoberfläche der [Anwendung abhängt.](spatial-mapping.md#the-environment-scanning-experience) Wenn eine Oberfläche nicht gescannt wurde, kann sie nicht für die Platzierung verwendet werden. Die Anwendung muss dies dem Benutzer klar machen, damit er entweder neue Oberflächen scannen oder einen neuen Speicherort auswählen kann.

Visuelles Feedback an den Benutzer ist während der Platzierung von größter Bedeutung. Der Benutzer muss wissen, wo das Hologramm auf der nächsten Oberfläche mit [Erdungseffekten](spatial-mapping.md#visualization)basiert. Sie sollten verstehen, warum die Bewegung ihres Hologramms eingeschränkt wird (z. B. aufgrund von Kollisionen mit einer anderen Oberfläche in der Nähe). Wenn sie kein Hologramm an der aktuellen Position platzieren können, sollte visuelles Feedback deutlich machen, warum nicht. Wenn der Benutzer z. B. versucht, eine holografische Couch in der Mitte an der Wand zu platzieren, sollten die Teile der Couch, die sich hinter der Wand befinden, in einer farbigen Farbe pulsieren. Oder umgekehrt: Wenn die Anwendung keine räumliche Oberfläche an einem Ort finden kann, an dem der Benutzer eine reale Oberfläche sehen kann, sollte die Anwendung dies deutlich machen. Das offensichtliche Fehlen eines grounding-Effekts in diesem Bereich kann diesen Zweck erreichen.

### <a name="occlusion"></a>Okklusion

Eine der Hauptverwendungen räumlicher Zuordnungsoberflächen ist einfach das Verdecken von Hologrammen. Dieses einfache Verhalten hat einen großen Einfluss auf die wahrgenommene Realität von Hologrammen und trägt dazu bei, ein viszerales Gefühl zu schaffen, das tatsächlich den gleichen physischen Raum wie der Benutzer verliert.

Occlusion stellt dem Benutzer auch Informationen bereit. Wenn ein Hologramm von einer realen Oberfläche verdeckt zu sein scheint, bietet dies zusätzliches visuelles Feedback zur räumlichen Position dieses Hologramms in der Welt. Umgekehrt kann die Verdeckung auch hilfreiche Informationen für den Benutzer *ausblenden.* Das Verdecken von Hologrammen hinter Wänden kann die visuelle Übersicht auf intuitive Weise reduzieren. Um ein Hologramm auszublenden oder anzuzeigen, muss der Benutzer lediglich den Kopf bewegen.

Occlusion kann auch verwendet werden, um die Erwartungen an eine natürliche Benutzeroberfläche basierend auf vertrauten physischen Interaktionen zu erfüllen. Wenn ein Hologramm von einer Oberfläche verdeckt wird, liegt dies daran, dass diese Oberfläche voll ist. Daher sollte der Benutzer erwarten, dass das Hologramm mit dieser Oberfläche *kollidiert* und nicht durch sie geleitet wird.

Manchmal ist die Verdeckung von Hologrammen unerwünscht. Wenn ein Benutzer mit einem Hologramm interagieren muss, muss er es sehen , auch wenn es sich hinter einer realen Oberfläche befindet. In solchen Fällen ist es in der Regel sinnvoll, ein solches Hologramm anders zu rendern, wenn es verblendet ist (z. B. durch Verringern der Helligkeit). Auf diese Weise kann der Benutzer das Hologramm visuell finden, aber er weiß immer noch, dass es sich hinter etwas befindet.

### <a name="physics"></a>Physische Effekte

Die Verwendung der physikalischen Simulation ist eine weitere Möglichkeit, mit der die räumliche Zuordnung verwendet werden kann, um das Vorhandensein von Hologrammen im physischen Raum des Benutzers zu verstärken.  Wenn meine Hologrammkugel realistisch vom Tisch rollt, über den Boden springt und unter der Couch verschwindet, kann es für mich schwierig sein zu glauben, dass sie nicht dort ist.

Die Physikalische Simulation bietet einer Anwendung auch die Möglichkeit, natürliche und vertraute physikalische Interaktionen zu verwenden. Das Verschieben eines Hologramms auf dem Boden ist für den Benutzer wahrscheinlich einfacher, wenn die Trägheit und Diebe so reagieren, als würde sie mit der entsprechenden Trägheit und Spannung über den Boden gleiten.

Um realistisches physisches Verhalten zu generieren, [](spatial-mapping.md#mesh-processing) müssen Sie wahrscheinlich einige Gitternetzverarbeitungen wie das Auffüllen von Lücken, das Entfernen von unverankerten Halluzinationen und das Glätten von rauen Oberflächen unternehmen.

Sie müssen auch berücksichtigen, wie sich die Scanerfahrung Ihrer Anwendung [auf](spatial-mapping.md#the-environment-scanning-experience) die physikalische Simulation ausdringt. Erstens: Fehlende Oberflächen können nicht mit anderen Oberflächen kollidieren. was geschieht, wenn die Würfel vom Würfel abrollt und am Ende der bekannten Welt abrollt? Zweitens müssen Sie entscheiden, ob Sie im Laufe der Zeit weiterhin auf Änderungen in der Umgebung reagieren. In einigen Fällen sollten Sie so schnell wie möglich reagieren. z. B. wenn der Benutzer Türen und Türen als verschiebbare Schieberkaden verwendet, um sich vor einer Verlockung eingehender pfeilförmiger Pfeile zu härten. In anderen Fällen sollten Sie jedoch neue Updates ignorieren. Wenn Ihr Hund sich in der Mitte der Spur befindet, kann es plötzlich nicht so viel Spaß machen, wenn Sie Ihren holografischen Sportwagen auf der Laufstrecke umfahren.

### <a name="navigation"></a>Navigation

Anwendungen können räumliche Zuordnungsdaten verwenden, um holografischen Zeichen (oder Agents) die Möglichkeit zu geben, in der realen Welt auf die gleiche Weise wie eine echte Person zu navigieren. Dies kann dazu beitragen, das Vorhandensein holografischer Zeichen zu verstärken, indem sie auf die gleichen natürlichen, vertrauten Verhaltensweisen wie die des Benutzers und seiner Freunde beschränkt werden.

Navigationsfunktionen können auch für Benutzer nützlich sein. Sobald eine Navigationskarte in einem bestimmten Bereich erstellt wurde, kann sie freigegeben werden, um holografische Anweisungen für neue Benutzer bereitzustellen, die mit diesem Standort nicht vertraut sind. Diese Karte könnte so entworfen werden, dass der "Verkehrsfluss" in der Stadt reibungslos bleibt oder dass es an gefährlichen Orten wie Baustellen zu Einem Unfahren kommt.

Die wichtigsten technischen Herausforderungen bei der Implementierung von Navigationsfunktionen sind die zuverlässige Erkennung von begehbaren Oberflächen (Menschen gehen nicht auf Tabellen!) und eine gute Anpassung an Änderungen in der Umgebung (Menschen durchlaufen keine geschlossenen Türen!). Das Gitternetz erfordert möglicherweise eine [Verarbeitung,](spatial-mapping.md#mesh-processing) bevor es für die Pfadplanung und Navigation durch ein virtuelles Zeichen verwendet werden kann. Das Glätten des Gitternetzes und das Entfernen von Halluzinationen können dazu beitragen, zu vermeiden, dass Zeichen hängen bleiben. Möglicherweise möchten Sie auch das Gitternetz drastisch vereinfachen, um die Pfadplanungs- und Navigationsberechnungen Ihres Zeichens zu beschleunigen. Diese Herausforderungen haben bei der Entwicklung der Spieletechnologie große Aufmerksamkeit erhalten, und es gibt eine Vielzahl von verfügbaren Forschungsinhalten zu diesen Themen.

Die integrierte NavMesh-Funktionalität in Unity kann nicht mit räumlichen Zuordnungsoberflächen verwendet werden. Dies liegt daran, dass räumliche Zuordnungsoberflächen erst bekannt sind, wenn die Anwendung gestartet wird, navmesh-Datendateien jedoch im Voraus aus Quellressourcen generiert werden müssen. Beachten Sie außerdem, dass das Räumliche Zuordnungssystem keine [Informationen zu Oberflächen](spatial-mapping.md#the-environment-scanning-experience) bereitstellt, die weit vom aktuellen Standort des Benutzers entfernt sind. Daher muss sich die Anwendung oberflächen selbst "merken", wenn sie eine Karte eines großen Bereichs erstellen soll.

### <a name="visualization"></a>Visualisierung

In den meisten Jahren ist es für räumliche Oberflächen geeignet, unsichtbar zu sein. , um die visuelle Übersichtlichkeit zu minimieren und die reale Welt für sich selbst sprechen zu lassen. Manchmal ist es jedoch hilfreich, Oberflächen der räumlichen Abbildung direkt zu visualisieren, obwohl ihre realen Entsprechungen sichtbar sind.

Wenn der Benutzer beispielsweise versucht, ein Hologramm auf einer Oberfläche zu platzieren (z. B. ein holografisches Schränk an der Wand zu platzieren), kann es hilfreich sein, das Hologramm zu "erdigen", indem er einen Schatten auf die Oberfläche wirft. Dies gibt dem Benutzer ein viel deutlicheres Gefühl für die genaue physische Nähe zwischen hologramm und Oberfläche. Dies ist auch ein Beispiel für die allgemeinere Vorgehensweise, eine Änderung visuell zu "in der Vorschau anzuzeigen", bevor der Benutzer ein Commit für diese änderungsbegeht.

Durch visualisieren von Oberflächen kann die Anwendung dem Benutzer sein Verständnis der Umgebung teilen. Beispielsweise könnte ein holografisches Boardspiel die horizontalen Oberflächen visualisieren, die es als "Tabellen" identifiziert hat, damit der Benutzer weiß, wo er interagieren soll.

Das Visualisieren von Oberflächen kann eine nützliche Möglichkeit sein, um den Benutzer in der Nähe von Räumen zu zeigen, die nicht angezeigt werden. Dies könnte eine Möglichkeit bieten, dem Benutzer Zugriff auf seine Zimmer (und alle darin enthaltenen Hologramme) aus seinem Zimmer zu geben.

Die von der räumlichen Zuordnung bereitgestellten Oberflächengitternetze sind möglicherweise nicht besonders "sauber". Es ist wichtig, sie entsprechend zu visualisieren. Herkömmliche Beleuchtungsberechnungen können Fehler in oberflächennormlen Oberflächen auf visuell ablenkende Weise hervorheben, während "saubere" Texturen, die auf die Oberfläche projiziert werden, dazu beitragen können, ihr ein saubereres Aussehen zu verleihen. Es ist auch möglich, die [Gitternetzverarbeitung zur](spatial-mapping.md#mesh-processing) Verbesserung der Gitternetzeigenschaften vor dem Rendern der Oberflächen zu verwenden.

> [!NOTE]
> HoloLens 2 implementiert eine neue [Scene Understanding Runtime,](scene-understanding.md)die Mixed Reality-Entwicklern eine strukturierte, grundlegende Umgebungsdarstellung bietet, die die Implementierung von Platzierung, Okklusion, Physik und Navigation vereinfacht.

## <a name="using-the-surface-observer"></a>Verwenden des Surface Observer

Der Ausgangspunkt für die räumliche Zuordnung ist der Oberflächenbeobachter. Der Programmablauf lautet wie folgt:
* Erstellen eines Surface Observer-Objekts
   * Geben Sie ein oder mehrere räumliche Volumes an, um die bereiche zu definieren, in denen die Anwendung räumliche Zuordnungsdaten empfangen möchte. Ein räumliches Volume ist einfach eine Form, die einen Raumbereich definiert, z. B. eine Kugel oder ein Feld.
   * Verwenden Sie ein räumliches Volume mit einem weltweit gesperrten räumlichen Koordinatensystem, um einen festen Bereich der physischen Welt zu identifizieren.
   * Verwenden Sie ein räumliches Volume, das jeden Frame mit einem körpergesperrten räumlichen Koordinatensystem aktualisiert, um einen Raumbereich zu identifizieren, der sich mit dem Benutzer bewegt (aber nicht rotiert).
   * Diese räumlichen Volumes können zu einem späteren Zeitpunkt geändert werden, wenn sich der Status der Anwendung oder des Benutzers ändert.
* Abrufen von Informationen zu räumlichen Oberflächen mithilfe von Abrufen oder Benachrichtigungen
   * Sie können den Oberflächenbeodrucker jederzeit auf den Status der räumlichen Oberfläche "abfragen". Stattdessen können Sie sich für das Surface Observer-Ereignis "surfaces changed" registrieren, das die Anwendung benachrichtigt, wenn sich räumliche Oberflächen geändert haben.
   * Für ein dynamisches räumliches Volume, z. B. das Sicht-Frustum oder ein durch Text gesperrtes Volume, müssen Anwendungen Änderungen für jeden Frame abfragen, indem sie den bereich von Interesse festlegen und dann den aktuellen Satz räumlicher Oberflächen abrufen.
   * Bei einem statischen Volume, z. B. einem weltweit gesperrten Würfel, der einen einzelnen Raum abdeckt, können Sich Anwendungen für das Ereignis "Oberflächen geändert" registrieren, um benachrichtigt zu werden, wenn sich räumliche Oberflächen innerhalb dieses Volumes geändert haben können.
* Änderungen an Prozessoberflächen
   * Iterieren Sie den bereitgestellten Satz räumlicher Oberflächen.
   * Klassifizieren Sie räumliche Oberflächen als hinzugefügt, geändert oder entfernt.
   * Übermitteln Sie für jede hinzugefügte oder geänderte räumliche Oberfläche ggf. eine asynchrone Anforderung, um ein aktualisiertes Gitternetz zu empfangen, das den aktuellen Zustand der Oberfläche auf der gewünschten Detailebene darstellt.
* Verarbeiten Sie die asynchrone Meshanforderung (weitere Details in den folgenden Abschnitten).

## <a name="mesh-caching"></a>Meshzwischenspeicherung

Räumliche Oberflächen werden durch dichte Dreiecksgitternetze dargestellt. Das Speichern, Rendern und Verarbeiten dieser Gitternetze kann erhebliche Rechen- und Speicherressourcen beanspruchen. Daher sollte jede Anwendung ein Gitternetz-Cachingschema übernehmen, das ihren Anforderungen entspricht, um die Ressourcen zu minimieren, die für die Meshverarbeitung und -speicherung verwendet werden. Dieses Schema sollte bestimmen, welche Gitternetze behalten und welche verworfen werden sollen und wann das Gitternetz für jede räumliche Oberfläche aktualisiert werden soll.

Viele der hier erläuterten Überlegungen informieren direkt darüber, wie Ihre Anwendung sich dem Zwischenspeichern von Netzen nähern sollte. Sie sollten berücksichtigen, wie sich der Benutzer durch die Umgebung bewegt, welche Oberflächen benötigt werden, wann verschiedene Oberflächen beobachtet werden und wann Änderungen in der Umgebung erfasst werden sollen.

Beim Interpretieren des vom Oberflächenbeobachter bereitgestellten Ereignisses "Oberflächen geändert" lautet die grundlegende Logik für das Zwischenspeichern von Gittern wie folgt:
* Wenn die Anwendung eine räumliche Oberflächen-ID sieht, die sie noch nicht gesehen hat, sollte sie diese als neue räumliche Oberfläche behandeln.
* Wenn die Anwendung eine räumliche Oberfläche mit einer bekannten ID, aber mit einer neuen Aktualisierungszeit sieht, sollte sie diese als aktualisierte räumliche Oberfläche behandeln.
* Wenn die Anwendung keine räumliche Oberfläche mit einer bekannten ID mehr erkennt, sollte sie diese als entfernte räumliche Oberfläche behandeln.

Jede Anwendung muss dann die folgenden Optionen treffen:
* Sollte für neue räumliche Oberflächen ein Gitternetz angefordert werden?
   * Im Allgemeinen sollte mesh sofort für neue räumliche Oberflächen angefordert werden, die dem Benutzer nützliche neue Informationen liefern können.
   * Neue räumliche Oberflächen in der Nähe und vor dem Benutzer sollten jedoch Priorität erhalten, und ihr Gitternetz sollte zuerst angefordert werden.
   * Wenn das neue Gittermodell nicht benötigt wird, z. B. wenn die Anwendung ihr Umgebungsmodell dauerhaft oder vorübergehend "eingefroren" hat, sollte es nicht angefordert werden.
* Sollte für aktualisierte räumliche Oberflächen ein Gitternetz angefordert werden?
   * Aktualisierte räumliche Oberflächen in der Nähe und vor dem Benutzer sollten Priorität erhalten, und ihr Gitternetz sollte zuerst angefordert werden.
   * Es kann auch sinnvoll sein, neuen Oberflächen eine höhere Priorität zu geben als aktualisierten Oberflächen, insbesondere während der Überprüfung.
   * Um die Verarbeitungskosten zu begrenzen, möchten Anwendungen möglicherweise die Rate drosseln, mit der sie Aktualisierungen an räumlichen Oberflächen verarbeiten.
   * Möglicherweise kann abgeleitet werden, dass Änderungen an einer räumlichen Oberfläche geringfügig sind, z. B. wenn die Begrenzungen der Oberfläche klein sind. In diesem Fall ist die Aktualisierung möglicherweise nicht wichtig genug, um sie zu verarbeiten.
   * Aktualisierungen räumlicher Oberflächen außerhalb des aktuellen Bereichs, der für den Benutzer von Interesse ist, können vollständig ignoriert werden. In diesem Fall kann es jedoch effizienter sein, die räumlichen Begrenzungsvolumen zu ändern, die vom Oberflächenbeoachter verwendet werden.
* Sollte das Gitternetz für entfernte räumliche Oberflächen verworfen werden?
   * Im Allgemeinen sollte das Gitternetz für entfernte räumliche Oberflächen sofort verworfen werden, damit die Hologrammverdeckung korrekt bleibt.
   * Wenn die Anwendung jedoch Grund zu der Annahme hat, dass eine räumliche Oberfläche in Kürze wieder angezeigt wird (basierend auf dem Entwurf der Benutzeroberfläche), ist es möglicherweise effizienter, sie beizubehalten, als das Gitternetz zu verwerfen und später erneut zu erstellen.
   * Wenn die Anwendung ein umfangreiches Modell der Umgebung des Benutzers aufbaut, möchte sie möglicherweise überhaupt keine Gittermodelle verwerfen. Die Ressourcennutzung muss jedoch weiterhin eingeschränkt werden, möglicherweise durch Daspoolen von Gitternetzen auf den Datenträger, wenn räumliche Oberflächen verschwinden.
   * Einige relativ seltene Ereignisse während der Generierung räumlicher Oberflächen können dazu führen, dass räumliche Oberflächen durch neue räumliche Oberflächen an einem ähnlichen Ort, aber mit unterschiedlichen IDs ersetzt werden. Daher sollten Anwendungen, die sich gegen das Verwerfen einer entfernten Oberfläche entscheiden, darauf achten, nicht mit mehreren stark überlappenden Gitternetzen für räumliche Oberflächen zu enden, die denselben Ort abdecken.
* Sollte das Gitternetz für andere räumliche Oberflächen verworfen werden?
   * Auch wenn eine räumliche Oberfläche vorhanden ist, sollte sie verworfen werden, wenn sie für die Benutzerfreundlichkeit nicht mehr nützlich ist. Wenn die Anwendung beispielsweise den Raum auf der anderen Seite eines Türbereichs durch einen alternativen virtuellen Raum "ersetzt", spielen die räumlichen Oberflächen in diesem Raum keine Rolle mehr.

Hier ist ein Beispiel für eine Strategie für die Meshzwischenspeicherung mit räumlicher und temporaler Hysterese:
* Stellen Sie sich eine Anwendung vor, die ein frustumförmiges räumliches Volumen verwenden möchte, das dem Anvitieren des Benutzers folgt, während er sich umschaut und durch die Umgebung geht.
* Eine räumliche Oberfläche verschwindet möglicherweise vorübergehend von diesem Volume, einfach weil der Benutzer von der Oberfläche wegsieht oder weiter davon entfernt ist... nur, um einen Moment später zurück- oder näher zu kommen. In diesem Fall stellt das Verwerfen und erneute Erstellen des Gitters für diese Oberfläche viele redundante Verarbeitungen dar.
* Um die Anzahl der verarbeiteten Änderungen zu reduzieren, verwendet die Anwendung zwei Raumoberflächenbeobachter, die in der anderen enthalten sind. Das größere Volume ist pherisch und folgt dem Benutzer "lazily". Er wird nur bei Bedarf bewegt, um sicherzustellen, dass sich sein Mittelpunkt innerhalb von 2,0 Metern vom Benutzer entfernt befindet.
* Neue und aktualisierte Gitternetze für räumliche Oberflächen werden immer vom kleineren Inneren Oberflächenbeobachter verarbeitet, aber Gitternetze werden zwischengespeichert, bis sie vom größeren Äußeren Oberflächenbeobachter verschwinden. Dadurch kann die Anwendung viele redundante Änderungen aufgrund von lokalen Benutzerbewegungen vermeiden.
* Da eine räumliche Oberfläche auch vorübergehend aufgrund von Nachverfolgungsverlusten verschwindet, wird das Verwerfen entfernter räumlicher Oberflächen während des Nachverfolgungsverlusts ebenfalls zurückgenommen.
* Im Allgemeinen sollte eine Anwendung den Kompromiss zwischen reduzierter Updateverarbeitung und erhöhter Speicherauslastung auswerten, um die ideale Strategie für die Zwischenspeicherung zu ermitteln.

## <a name="rendering"></a>Darstellung

Es gibt drei Primäre Möglichkeiten, wie Gitternetze für räumliche Zuordnungen tendenziell zum Rendern verwendet werden:
* Für die Oberflächenvisualisierung
   * Häufig ist es hilfreich, räumliche Oberflächen direkt zu visualisieren. Beispielsweise kann das Werfen von Schatten von Objekten auf räumliche Oberflächen hilfreiches visuelles Feedback für den Benutzer bereitstellen, während hologramme auf Oberflächen platziert werden.
   * Beachten Sie, dass räumliche Gitternetze sich von der Art der Gitternetze unterscheiden, die ein 3D-Interpret erstellen könnte. Die Dreieckstopologie ist nicht so "sauber" wie die von Menschen erstellte Topologie, und das Gitternetz hat verschiedene [Fehler.](spatial-mapping.md#what-influences-spatial-mapping-quality)
   * Um ein ansprechendes visuelles Aussehen zu schaffen, können Sie eine [Gitternetzverarbeitung](spatial-mapping.md#mesh-processing)durchführen, z. B. um Löcher oder reibungslose Oberflächennormalisierungen zu füllen. Sie können auch einen Shader verwenden, um von Einem Interpret entworfene Texturen in Ihr Gitternetz zu pro projektieren, anstatt die Meshtopologie und -normalitäten direkt zu visualisieren.
* Zum Verdecken von Hologrammen hinter realen Oberflächen
   * Räumliche Oberflächen können in einem reinen Tiefendurchlauf gerendert werden. Dies wirkt sich nur auf den [Tiefenpuffer](/windows/win32/direct3d9/depth-buffers) und nicht auf Farbrenderziele aus.
   * Dadurch wird der Tiefenpuffer so grundiert, dass nachfolgend gerenderte Hologramme hinter räumlichen Oberflächen verdeckt werden. Eine genaue Verdeckung von Hologrammen verbessert das Gefühl, dass Hologramme tatsächlich im physischen Raum des Benutzers vorhanden sind.
   * Aktualisieren Sie den Blendzustand, um [renderTargetWriteMask](/windows/win32/api/d3d11_1/ns-d3d11_1-d3d11_render_target_blend_desc1) für alle Farbrenderziele auf null festzulegen, um das rein tiefenbezogene Rendering zu aktivieren.
* Zum Ändern der Darstellung von Hologrammen, die von realen Oberflächen verdeckt werden
   * Normalerweise gerenderte Geometrie wird ausgeblendet, wenn sie verdeckt wird. Dies wird erreicht, indem die Tiefenfunktion in Ihrem [Tiefenschablonenzustand](/windows/win32/api/d3d11/ns-d3d11-d3d11_depth_stencil_desc) auf "kleiner als oder gleich" festgelegt wird, wodurch die Geometrie nur dort sichtbar wird, wo sie **sich näher** an der Kamera befindet als alle zuvor gerenderten Geometrien.
   * Es kann jedoch hilfreich sein, eine bestimmte Geometrie sichtbar zu halten, auch wenn sie verdeckunglich ist, und die Darstellung zu ändern, wenn sie als Möglichkeit zum Bereitstellen visuellen Feedbacks für den Benutzer verwendet wird. Dies ermöglicht der Anwendung beispielsweise, dem Benutzer den Speicherort eines Objekts anzuzeigen und gleichzeitig deutlich zu machen, dass sich hinter einer realen Oberfläche befindet.
   * Um dies zu erreichen, rendern Sie die Geometrie ein zweites Mal mit einem anderen Shader, der die gewünschte Verdeckungsdarstellung erstellt. Nehmen Sie vor dem zweiten Rendern der Geometrie zwei Änderungen am [Tiefenschablonenzustand](/windows/win32/api/d3d11/ns-d3d11-d3d11_depth_stencil_desc)vor. Legen Sie zunächst die Tiefenfunktion auf "größer als oder gleich" fest, sodass die Geometrie nur sichtbar ist, wenn sie **sich weiter** von der Kamera entfernt als alle zuvor gerenderten Geometrien befindet. Legen Sie zweitens die DepthWriteMask auf 0 (null) fest, damit der Tiefenpuffer nicht geändert  wird (der Tiefenpuffer sollte weiterhin die Tiefe der Geometrie darstellen, die der Kamera am nächsten liegt).

[Die Leistung](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) ist ein wichtiges Problem beim Rendern von Gittern für räumliche Zuordnungen. Hier sind einige Renderingleistungstechniken für das Rendern von Gittern für räumliche Zuordnungen:
* Anpassen der Dreiecksdichte
   * Fordern Sie beim Anfordern von Gittern der räumlichen Oberfläche von Ihrem Oberflächenbeobachter die niedrigste Dichte von Dreiecksgittern an, die für Ihre Anforderungen ausreicht.
   * Es kann sinnvoll sein, die Dreiecksdichte auf Oberflächenbasis zu variieren, abhängig vom Abstand der Oberfläche zum Benutzer und ihrer Relevanz für die Benutzererfahrung.
   * Die Reduzierung der Dreiecksanzahl reduziert die Speicherauslastung und die Vertexverarbeitungskosten auf der GPU, wirkt sich jedoch nicht auf die Pixelverarbeitungskosten aus.
* Verwenden von Frustum-Culling
   * Frustum-Culling überspringt Zeichnungsobjekte, die nicht angezeigt werden können, da sie sich außerhalb des aktuellen Frustums der Anzeige befinden. Dadurch werden sowohl die CPU- als auch die GPU-Verarbeitungskosten reduziert.
   * Da das Culling auf Gitternetzbasis durchgeführt wird und räumliche Oberflächen groß sein können, kann das Aufbrechen jedes Gitters der räumlichen Oberfläche in kleinere Gitternetze zu einem effizienteren Culling führen (da weniger Offscreen-Dreiecke gerendert werden). Es gibt jedoch einen Kompromiss. Desto mehr Gitternetze sie haben, desto mehr Zeichnen-Aufrufe müssen Sie tätigen, was die CPU-Kosten erhöhen kann. Im Extremfall können die Frustum-Cullingberechnungen selbst sogar messbare CPU-Kosten haben.
* Anpassen der Rendering reihenfolge
   * Räumliche Oberflächen sind in der Regel groß, da sie die gesamte Umgebung des Benutzers darstellen, die sie umhing. Die Pixelverarbeitungskosten auf der GPU können hoch sein, insbesondere in Fällen, in denen mehr als eine Ebene der sichtbaren Geometrie (einschließlich räumlicher Oberflächen und anderer Hologramme) vorlag. In diesem Fall wird die ebene, die dem Benutzer am nächsten liegt, alle Schichten weiter entfernt verschließen, sodass jede GPU-Zeit, die für das Rendern dieser entfernteren Ebenen aufwendet wird, verschwendet wird.
   * Um diese redundante Arbeit auf der GPU zu reduzieren, hilft es, nicht transparente Oberflächen in front-to-back-Reihenfolge zu rendern (zuerst näher, entferntere zuletzt). Mit "opak" meinen wir Oberflächen, für die die DepthWriteMask im [Tiefenschablonenzustand](/windows/win32/api/d3d11/ns-d3d11-d3d11_depth_stencil_desc)auf eins festgelegt ist. Wenn die nächstgelegenen Oberflächen gerendert werden, wird der Tiefenpuffer so grundiert, dass entferntere Oberflächen effizient vom Pixelprozessor auf der GPU übersprungen werden.

## <a name="mesh-processing"></a>Mesh-Verarbeitung

Eine Anwendung möchte möglicherweise [verschiedene Vorgänge](spatial-mapping.md#mesh-processing) für Gitternetze auf räumlicher Oberfläche durchführen, um ihre Anforderungen zu erfüllen. Die Index- und Scheitelpunktdaten, die mit jedem Raumoberflächengitternetz bereitgestellt werden, verwenden das gleiche vertraute Layout wie die [Scheitelpunkt- und Indexpuffer,](/windows/win32/direct3d9/rendering-from-vertex-and-index-buffers) die zum Rendern von Dreiecksgittern in allen modernen Rendering-APIs verwendet werden. Eine wichtige Tatsache, die Sie beachten sollten, ist jedoch, dass räumliche Zuordnungsdreiecke eine **Umdrehungsreihenfolge von vorn im Uhrzeigersinn aufweisen.** Jedes Dreieck wird durch drei Scheitelpunktindizes im Indexpuffer des Gitters dargestellt, und diese Indizes identifizieren die Scheitelpunkte des Dreiecks im **Uhrzeigersinn,** wenn das Dreieck von der **Vorderseite** aus angezeigt wird. Die Frontseite (oder außen) von Gitternetzen für räumliche Oberflächen entspricht dem, was Sie von der (sichtbaren) Frontseite der realen Oberflächen erwarten würden.

Anwendungen sollten eine Mesh-Vereinfachung nur durchführen, wenn die vom Oberflächenbeohrer bereitgestellte dichte des kleinsten Dreiecks immer noch unzureichend ist. Diese Arbeit ist rechenintensiv und wird bereits von der Laufzeit ausgeführt, um die verschiedenen bereitgestellten Detailebenen zu generieren.

Da jeder Oberflächenbeozeuger mehrere nicht verbundene räumliche Oberflächen bereitstellen kann, möchten einige Anwendungen diese Gitternetze der räumlichen Oberfläche möglicherweise aufeinander abschneiden und dann zusammen zippen. Im Allgemeinen ist der Clippingschritt erforderlich, da sich Gitternetze in der Nähe häufig geringfügig überschneiden.

## <a name="raycasting-and-collision"></a>Raycasting und Kollision

Damit eine physikalische API (z. B. [Havok](https://www.havok.com/)) eine Anwendung mit Raycasting- und Kollisionsfunktionen für räumliche Oberflächen bereitstellen kann, muss die Anwendung raumbezogene Oberflächengitter für die Physikalische API bereitstellen. Gitternetze, die für die Physik verwendet werden, haben häufig die folgenden Eigenschaften:
* Sie enthalten nur eine kleine Anzahl von Dreiecken. Physikalische Operationen sind rechenintensiver als Renderingvorgänge.
* Sie sind "water-tight". Oberflächen, die als fest gedacht sind, sollten keine kleinen Lücken in ihnen haben. sogar Lücken, die zu klein sind, um sichtbar zu sein, können Probleme verursachen.
* Sie werden in konvexe Hüllen konvertiert. Konvexe Hüllen verfügen über wenige Polygone und sind frei von Lücken, und sie sind wesentlich recheneffizienter zu verarbeiten als unformatiert dreieckige Gittermodelle.

Beachten Sie beim Verwenden von Raycasts für räumliche Oberflächen, dass diese Oberflächen oft komplexe, unübersichtliche Formen mit unübersichtlichen kleinen Details sind – genau wie Ihr Arbeitsplatz! Dies bedeutet, dass ein einzelner Raycast häufig nicht ausreicht, um genügend Informationen über die Form der Oberfläche und die Form des leeren Raums in ihrer Nähe zu erhalten. Es ist in der Regel eine gute Idee, viele Raycasts in einem kleinen Bereich zu verwenden und die Aggregatergebnisse zu verwenden, um ein zuverlässigeres Verständnis der Oberfläche zu erzielen. Wenn Sie z. B. den Durchschnitt von 10 Raycasts verwenden, um die Hologrammplatzierung auf einer Oberfläche zu leiten, führt dies zu einem deutlich reibungsloseren und weniger "jittery"-Ergebnis, da nur ein einzelner Raycast verwendet wird.

Beachten Sie jedoch, dass jeder Raycast hohe Berechnungskosten haben kann. Abhängig von Ihrem Nutzungsszenario sollten Sie die Berechnungskosten für zusätzliche Raycasts (für [](spatial-mapping.md#mesh-processing) jeden Frame) gegen die Berechnungskosten der Gittermodellverarbeitung abhandeln, um Lücken in räumlichen Oberflächen zu glätten und zu entfernen (dies erfolgt, wenn räumliche Gittermodelle aktualisiert werden).

## <a name="the-environment-scanning-experience"></a>Umgebungsscans

Jede Anwendung, die räumliche Zuordnung verwendet, sollte eine "Scanerfahrung" bereitstellen. der Prozess, durch den die Anwendung den Benutzer durchsucht, um Oberflächen zu überprüfen, die für die korrekte Funktionsweise der Anwendung erforderlich sind.

![Beispiel für die Überprüfung](images/sr-mixedworld-140429-8pm-00068-1000px.png)<br>
*Beispiel für die Überprüfung*

Die Art dieser Überprüfungserfahrung kann je nach Den Anforderungen der einzelnen Anwendungen stark variieren, aber zwei Hauptprinzipien sollten den Entwurf leiten.

Erstens **ist die klare Kommunikation mit dem Benutzer das Hauptanliegen.** Der Benutzer sollte immer wissen, ob die Anforderungen der Anwendung erfüllt werden. Wenn sie nicht erfüllt werden, sollte dem Benutzer sofort klar sein, warum dies der Grund ist, und er sollte schnell dazu veranlasst werden, die entsprechenden Maßnahmen zu ergreifen.

Zweitens **sollten Anwendungen versuchen, ein Gleichgewicht zwischen Effizienz und Zuverlässigkeit zu finden.** Wenn dies **zuverlässig** möglich ist, sollten Anwendungen räumliche Zuordnungsdaten automatisch analysieren, um dem Benutzer Zeit zu sparen. Wenn dies nicht zuverlässig möglich ist, sollten Anwendungen es dem Benutzer stattdessen ermöglichen, der Anwendung schnell die zusätzlichen Informationen bereitzustellen, die sie benötigt.

Um die richtige Überprüfungserfahrung zu entwerfen, sollten Sie berücksichtigen, welche der folgenden Möglichkeiten für Ihre Anwendung zutreffen:

* **Keine Überprüfungserfahrung**
   * Eine Anwendung kann ohne geführte Überprüfung perfekt funktionieren. es wird über Oberflächen informiert, die im Verlauf der natürlichen Benutzerbewegung beobachtet werden.
   * Beispielsweise erfordert eine Anwendung, die es dem Benutzer ermöglicht, mit holografischer Sprayfarbe auf Oberflächen zu zeichnen, nur die Oberflächen zu wissen, die derzeit für den Benutzer sichtbar sind.
   * Die Umgebung kann bereits überprüft werden, wenn der Benutzer bereits viel Zeit mit der Verwendung der HoloLens verbracht hat.
   * Beachten Sie jedoch, dass die von der räumlichen Zuordnung verwendete Kamera nur 3,1 m vor dem Benutzer sehen kann, sodass die räumliche Zuordnung keine weiteren entfernten Oberflächen kennt, es sei denn, der Benutzer hat sie in der Vergangenheit aus größerer Entfernung beobachtet.
   * Damit der Benutzer versteht, welche Oberflächen gescannt wurden, sollte die Anwendung visuelles Feedback zu diesem Effekt bereitstellen. Beispielsweise kann das Umwandeln virtueller Schatten auf gescannte Oberflächen dem Benutzer helfen, Hologramme auf diesen Oberflächen zu platzieren.
   * In diesem Fall sollten die Begrenzungsvolumes des Raumoberflächenbeobachter für jeden Frame in ein textgesperrte räumliches Koordinatensystem aktualisiert [werden,](coordinate-systems.md)damit sie dem Benutzer folgen.

* **Suchen eines geeigneten Standorts**
   * Eine Anwendung kann für die Verwendung an einem Standort mit bestimmten Anforderungen entworfen werden.
   * Beispielsweise kann die Anwendung einen leeren Bereich um den Benutzer erfordern, damit er holografisches kung-fu sicher üben kann.
   * Anwendungen sollten dem Benutzer im Vorhinhin alle spezifischen Anforderungen übermitteln und mit klarem visuellem Feedback verstärken.
   * In diesem Beispiel sollte die Anwendung den Umfang des erforderlichen leeren Bereichs visualisieren und das Vorhandensein unerwünschter Objekte innerhalb dieser Zone visuell hervorheben.
   * In diesem Fall sollten die Begrenzungsvolumes des Raumoberflächenbeobachter ein weltgesperrte Raumkoordinatensystem [an](coordinate-systems.md) der ausgewählten Position verwenden.

* **Suchen einer geeigneten Konfiguration von Oberflächen**
   * Eine Anwendung erfordert möglicherweise eine bestimmte Konfiguration von Oberflächen, z. B. zwei große, flache, gegensätzliche Wände, um eine holografische Spiegelfläche zu erstellen.
   * In solchen Fällen muss die Anwendung die von der räumlichen Zuordnung bereitgestellten Oberflächen analysieren, um geeignete Oberflächen zu erkennen, und den Benutzer an diese weiter richten.
   * Der Benutzer sollte über eine Fallbackoption verfügen, wenn die Oberflächenanalyse der Anwendung nicht zuverlässig ist. Wenn die Anwendung beispielsweise fälschlicherweise eine Tür als flache Wand identifiziert, benötigt der Benutzer eine einfache Möglichkeit, diesen Fehler zu beheben.

* **Überprüfen eines Teils der Umgebung**
   * Eine Anwendung möchte möglicherweise nur einen Teil der Umgebung erfassen, wie vom Benutzer gewünscht.
   * Die Anwendung scannt z. B. einen Teil eines Raums, damit der Benutzer eine holografische klassifizierte Werbeanzeige für die Produkte posten kann, die er verkaufen möchte.
   * In diesem Fall sollte die Anwendung räumliche Kartendaten in den Regionen erfassen, die der Benutzer während seiner Überprüfung beobachtet hat.

* **Scannen des gesamten Raums**
   * Eine Anwendung erfordert möglicherweise eine Überprüfung aller Oberflächen im aktuellen Raum, einschließlich der oberflächen hinter dem Benutzer.
   * Ein Spiel kann z. B. den Benutzer in die Rolle von Gulliver versetzen, der von Hunderten von kleinen Lierungputern belagert wird, die sich aus allen Richtungen nähern.
   * In solchen Fällen muss die Anwendung bestimmen, wie viele der Oberflächen im aktuellen Raum bereits gescannt wurden, und den Blick des Benutzers anweisen, erhebliche Lücken zu füllen.
   * Der Schlüssel zu diesem Prozess ist das bereitstellen von visuellem Feedback, das dem Benutzer deutlich macht, welche Oberflächen noch nicht überprüft wurden. Die Anwendung könnte z. B. [entfernungsbasierte Bilder](/windows/win32/direct3d9/fog-formulas) verwenden, um Bereiche visuell hervorzuheben, die nicht von räumlichen Zuordnungsoberflächen abgedeckt werden.

* **Erstellen einer Anfangsmomentaufnahme der Umgebung**
   * Eine Anwendung möchte möglicherweise alle Änderungen in der Umgebung ignorieren, nachdem eine anfängliche Momentaufnahme erstellt wurde.
   * Dies kann geeignet sein, um eine Unterbrechung von vom Benutzer erstellten Daten zu vermeiden, die eng mit dem ursprünglichen Zustand der Umgebung verknüpft sind.
   * In diesem Fall sollte die Anwendung eine Kopie der räumlichen Zuordnungsdaten im ursprünglichen Zustand erstellen, sobald die Überprüfung abgeschlossen ist.
   * Anwendungen sollten weiterhin Aktualisierungen an räumlichen Zuordnungsdaten erhalten, wenn Hologramme weiterhin ordnungsgemäß von der Umgebung verdeckt werden sollen.
   * Fortlaufende Aktualisierungen von Räumlichen Zuordnungsdaten ermöglichen auch das Visualisieren aufgetretener Änderungen, wodurch dem Benutzer die Unterschiede zwischen früheren und aktuellen Zuständen der Umgebung verdeutlicht werden.

* **Erstellen von vom Benutzer initiierten Momentaufnahmen der Umgebung**
   * Eine Anwendung möchte möglicherweise nur auf Umgebungsänderungen reagieren, wenn sie vom Benutzer angewiesen wird.
   * Beispielsweise könnte der Benutzer mehrere 3D-"Gänge" eines Freundes erstellen, indem er seine Posen zu unterschiedlichen Zeitpunkten erfasst.

* **Benutzern das Ändern der Umgebung erlauben**
   * Eine Anwendung kann so entworfen werden, dass sie in Echtzeit auf Änderungen reagiert, die in der Umgebung des Benutzers vorgenommen wurden.
   * Beispielsweise könnte der Benutzer, der einen Graphen zeichnet, eine "Szenenänderung" für ein holografisches Spiel auslösen, das auf der anderen Seite stattfindet.

* **Anleitung des Benutzers zur Vermeidung von Fehlern in den Räumlichen Zuordnungsdaten**
   * Eine Anwendung möchte dem Benutzer beim Scannen seiner Umgebung möglicherweise Anleitungen geben.
   * Dies kann dem Benutzer helfen, bestimmte Arten von Fehlern [in](spatial-mapping.md#what-influences-spatial-mapping-quality)den räumlichen Zuordnungsdaten zu vermeiden, z. B. indem er sich von den fenstern oder spiegelnden Fenstern entfernt.

Ein zusätzliches Detail, das Sie beachten sollten, ist, dass der "Bereich" der räumlichen Zuordnungsdaten nicht unbegrenzt ist. Die räumliche Zuordnung erstellt zwar eine permanente Datenbank mit großen Räumen, stellt diese Daten jedoch nur Anwendungen in einer "Blase" mit begrenzter Größe um den Benutzer zur Verfügung. Wenn Sie am Anfang einer langen Ungnung beginnen und weit genug vom Anfang entfernt gehen, werden die räumlichen Oberflächen am Anfang schließlich wieder verschwinden. Sie können dies minimieren, indem Sie diese Oberflächen in Ihrer Anwendung zwischenspeichern, nachdem sie aus den verfügbaren räumlichen Zuordnungsdaten entfernt wurden.

## <a name="mesh-processing"></a>Mesh-Verarbeitung

Es kann helfen, häufige Arten von Fehlern in Oberflächen zu erkennen und die räumlichen Zuordnungsdaten nach Geeigneten zu filtern, zu entfernen oder zu ändern.

Beachten Sie, dass räumliche Kartendaten so gut wie möglich für reale Oberflächen bestimmt sind, sodass jede Verarbeitung, die Sie anwenden, risiken, ihre Oberflächen weiter von der "Wahrheit" zu verschieben.

Im Folgenden finden Sie einige Beispiele für verschiedene Arten von Gitternetzverarbeitung, die sie möglicherweise nützlich finden:

* **Füllung von Füllstellen**
   * Wenn ein kleines Objekt, das aus einem dunklen Material besteht, nicht gescannt werden kann, wird eine Lücke in der umgebenden Oberfläche hinterlassen.
   * Lücken wirken sich auf die Okklusion aus: Hologramme können "durch" eine Lücke in einer vermutlich undurchsichtigen realen Oberfläche gesehen werden.
   * Lücken wirken sich auf Raycasts aus: Wenn Sie Raycasts verwenden, um Benutzern die Interaktion mit Oberflächen zu ermöglichen, ist es möglicherweise unerwünscht, dass diese Lichtstrahl lückenübergehen. Eine Lösung besteht in der Verwendung eines Bündels von mehreren Raycasts, die einen entsprechend großen Bereich abdecken. Auf diese Weise können Sie Ausreißerergebnisse filtern, sodass das Aggregatergebnis auch dann gültig ist, wenn ein Raycast eine kleine Lücke durchläuft. Dieser Ansatz geht jedoch mit Rechenkosten ein.
   * Löcher wirken sich auf physikalische Kollisionen aus: Ein objekt, das von der Physikalischen Simulation gesteuert wird, kann durch ein Löcher im Boden fallen und verlorengehen.
   * Es ist möglich, solche Löcher im Oberflächengitternetz algorithmusgesteuert zu füllen. Sie müssen ihren Algorithmus jedoch so optimieren, dass "echte Löcher" wie Fenster und Türtüren nicht ausgefüllt werden. Es kann schwierig sein, "echte Löcher" zuverlässig von "imaginären Löchern" zu unterscheiden, sodass Sie mit verschiedenen Heuristiken wie "Größe" und "Begrenzungsform" experimentieren müssen.

* **Hallucinationsentfernung**
   * Reflexionen, helle Lichtlichter und bewegte Objekte können kleine verweilende Hallucinationen in der Luft gleiten lassen.
   * Hallucinationen wirken sich auf die Verdeckung aus: Halluzinationen werden möglicherweise sichtbar, wenn sich dunkle Formen vor anderen Hologrammen bewegen und diese verdecken.
   * Hallucinationen wirken sich auf Raycasts aus: Wenn Sie Raycasts verwenden, um Benutzer bei der Interaktion mit Oberflächen zu unterstützen, können diese Lichtstrahle auf eine Hallucination anstatt auf die oberfläche darunter treffen. Wie bei Löchern besteht eine Entschärfung darin, viele Raycasts anstelle eines einzelnen Raycasts zu verwenden, aber dies führt wiederum zu Rechenkosten.
   * Hallucinationen wirken sich auf physikalische Konflikte aus: Ein objekt, das von der physikalischen Simulation gesteuert wird, kann an einer Halluzination hängen bleiben und sich nicht durch einen scheinbar klaren Raumbereich bewegen können.
   * Es ist möglich, solche Halluzinationen aus dem Oberflächengitternetz zu filtern. Wie bei Löchern müssen Sie ihren Algorithmus jedoch so optimieren, dass echte kleine Objekte wie Laternenständer und Türhandles nicht entfernt werden.

* **Glättung**
   * Räumliche Zuordnungen können Oberflächen zurückgeben, die im Vergleich zu ihren realen Entsprechungen grob oder "laut" erscheinen.
   * Glättung wirkt sich auf physikalische Kollisionen aus: Wenn der Boden grob ist, rollt eine physisch simulierte Kugel möglicherweise nicht gleichmäßig in einer geraden Linie darüber.
   * Glättung wirkt sich auf das Rendering aus: Wenn eine Oberfläche direkt visualisiert wird, können sich grobe Oberflächennorm normal auf ihre Darstellung auswirken und ein "sauberes" Aussehen unterbrechen. Es ist möglich, dies zu verringern, indem Sie die entsprechende Beleuchtung und Texturen im Shader verwenden, der zum Rendern der Oberfläche verwendet wird.
   * Es ist möglich, die Rauheit in einem Oberflächengitter zu glätten. Dadurch wird die Oberfläche jedoch möglicherweise weiter von der entsprechenden realen Oberfläche entfernt. Eine enge Entsprechung ist wichtig, um eine genaue Hologrammverschluss zu erzeugen und Benutzern zu ermöglichen, präzise und vorhersagbare Interaktionen mit holografischen Oberflächen zu erzielen.
   * Wenn nur eine gängige Änderung erforderlich ist, kann es ausreichen, die Scheitelpunktnorm normal zu glätten, ohne die Scheitelpunktpositionen zu ändern.

* **Ebenensuche**
   * Es gibt viele Formen der Analyse, die eine Anwendung möglicherweise auf den Oberflächen durchführen möchte, die von der räumlichen Zuordnung bereitgestellt werden.
   * Ein einfaches Beispiel ist "Plane Finding". Identifizieren von begrenzungsgebundenen, größtenteils planaren Oberflächen.
   * Planare Regionen können als holografische Arbeitsoberflächen verwendet werden, wobei holografische Inhalte von der Anwendung automatisch platziert werden können.
   * Planare Regionen können die Benutzeroberfläche einschränken, um Benutzer bei der Interaktion mit den Oberflächen zu unterstützen, die ihren Anforderungen am besten entsprechen.
   * Planare Regionen können wie in der realen Welt für holografische Entsprechungen zu funktionalen Objekten wie DISPLAYS-Bildschirmen, Tabellen oder Whiteboards verwendet werden.
   * Planare Regionen können Spielbereiche definieren, die die Grundlage von Videospielebenen bilden.
   * Planare Regionen können virtuellen Agents helfen, durch die reale Welt zu navigieren, indem sie die Bereiche des Bodens identifizieren, auf denen echte Menschen wahrscheinlich weiter gehen werden.

## <a name="prototyping-and-debugging"></a>Prototyperstellung und Debuggen

### <a name="useful-tools"></a>Nützliche Tools

* Der [HoloLens-Emulator kann](../develop/platform-capabilities-and-apis/using-the-hololens-emulator.md) verwendet werden, um Anwendungen mit räumlicher Zuordnung ohne Zugriff auf eine physische HoloLens zu entwickeln. Sie können eine Livesitzung auf einer HoloLens in einer realistischen Umgebung mit allen Daten simulieren, die Ihre Anwendung normalerweise nutzen würde, einschließlich HoloLens-Bewegung, raumbezogene Koordinatensysteme und Gitternetze für räumliche Karten. Dies kann verwendet werden, um zuverlässige, wiederholbare Eingaben zu bieten, die für das Debuggen von Problemen und das Auswerten von Änderungen am Code nützlich sein können.
* Um ein Szenario zu reproduzieren, erfassen Sie räumliche Zuordnungsdaten über das Netzwerk von einer Live-HoloLens, speichern sie dann auf dem Datenträger und verwenden sie in späteren Debugsitzungen wieder.
* Die [3D-Ansicht des Windows-Geräteportals](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#3d-view) bietet eine Möglichkeit, alle räumlichen Oberflächen anzuzeigen, die derzeit über das Räumliche Zuordnungssystem verfügbar sind. Dies stellt eine Vergleichsbasis für die räumlichen Oberflächen in Ihrer Anwendung bereit. Beispielsweise können Sie leicht erkennen, ob räumliche Oberflächen fehlen oder an der falschen Stelle angezeigt werden.

### <a name="general-prototyping-guidance"></a>Allgemeine Anleitungen zur Prototyperstellung

* Da [Sich Fehler](spatial-mapping.md#what-influences-spatial-mapping-quality) in den Räumlichen Zuordnungsdaten stark auf die Benutzerfreundlichkeit auswirken können, empfehlen wir Ihnen, Ihre Anwendung in einer Vielzahl von Umgebungen zu testen.
* Lassen Sie sich nicht davon abfangen, immer an demselben Ort zu testen, z. B. an Ihrem Arbeitsplatz. Stellen Sie sicher, dass Sie verschiedene Oberflächen unterschiedlicher Positionen, Formen, Größen und Materialien testen.
* Auch wenn synthetische oder aufgezeichnete Daten für das Debuggen nützlich sein können, werden Sie nicht zu stark von den gleichen Testfällen abhängig. Dies kann die Ermittlung wichtiger Probleme verzögern, die zuvor durch unterschiedliche Tests abgefangen worden wären.
* Es ist eine gute Idee, Tests mit echten (und idealerweise nicht coachierten) Benutzern durchzuführen, da sie die HoloLens oder Ihre Anwendung möglicherweise nicht auf die gleiche Weise wie Sie verwenden. Tatsächlich ist es möglicherweise überraschend, wie ungenannt das Verhalten, das Wissen und die Annahmen von Menschen sein können!

## <a name="troubleshooting"></a>Problembehandlung

* Damit die Oberflächengitternetze ordnungsgemäß geordnet sind, muss jedes GameObject aktiv sein, bevor es an den SurfaceObserver gesendet wird, damit sein Gitternetz erstellt wird. Andernfalls werden die Gitternetze in Ihrem Raum angezeigt, aber in schrägen Winkeln gedreht.
* Das GameObject, das das Skript ausführt, das mit dem SurfaceObserver kommuniziert, muss auf den Ursprung festgelegt werden. Andernfalls haben alle GameObjects, die Sie erstellen und an den SurfaceObserver senden, damit ihre Gitternetze erstellt werden, einen Offset, der dem Offset des übergeordneten Spielobjekts entspricht. Dadurch können Ihre Gitternetze mehrere Meter entfernt angezeigt werden, was das Debuggen der Daten erschwert.

## <a name="see-also"></a>Weitere Informationen

* [Koordinatensysteme](coordinate-systems.md)
* [Räumliche Abbildung in DirectX](../develop/native/spatial-mapping-in-directx.md)
* [Räumliche Abbildung in Unity](../develop/unity/spatial-mapping-in-unity.md)
* [Szenenverständnis](scene-understanding.md)
* [Raumabtastvisualisierung](room-scan-visualization.md)
* [Raumklangentwurf](spatial-sound-design.md)
* [Fallstudie – Schauen durch Löcher in Ihrer Realität](../out-of-scope/case-study-looking-through-holes-in-your-reality.md)