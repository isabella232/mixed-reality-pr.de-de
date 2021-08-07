---
title: Räumliche Abbildung
description: Die räumliche Zuordnung bietet eine detaillierte Darstellung von realen Oberflächen in der Umgebung um die HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Räumliche Zuordnung, HoloLens, Mixed Reality, Oberflächenrekonstruktion, Gitternetz, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit, Szenenverständnis, Weltgitternetz, Verdeckung, Physik, Navigation, Surface Observer, Rendering, Meshverarbeitung
ms.openlocfilehash: 342ba116a5e33073acf2d4dbe563e74bccbf7053ec96d9b3f2f7ba88bd13da90
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212420"
---
# <a name="spatial-mapping"></a>Räumliche Abbildung

Die räumliche Zuordnung bietet eine detaillierte Darstellung von realen Oberflächen in der Umgebung um die HoloLens, sodass Entwickler eine überzeugende Mixed Reality-Erfahrung erstellen können. Durch das Zusammenführen der realen Welt mit der virtuellen Welt kann eine Anwendung Hologramme real erscheinen lassen. Anwendungen können auch auf natürlichere Weise mit den Erwartungen der Benutzer übereinstimmen, indem sie vertraute Verhaltensweisen und Interaktionen in der realen Welt bereitstellen.

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


## <a name="why-is-spatial-mapping-important"></a>Warum ist die räumliche Zuordnung wichtig?

Räumliche Zuordnung macht es möglich, Objekte auf realen Oberflächen zu platzieren. Dies hilft, Objekte in der Welt des Benutzers zu verankern, und nutzt echte Tiefenhinweise. Das Verdecken Ihrer Hologramme basierend auf anderen Hologrammen und Objekten aus der realen Welt hilft dem Benutzer zu überzeugen, dass sich diese Hologramme tatsächlich in ihrem Raum befinden. Hologramme im Raum zu gleiten oder sich mit dem Benutzer zu bewegen, wird sich nicht so real anfühlen. Platzieren Sie nach Möglichkeit Elemente aus Komfortgründen.

Visualisieren von Oberflächen beim Platzieren oder Verschieben von Hologrammen (verwenden Sie ein projiziertes Raster). Dies hilft Benutzern zu wissen, wo sie ihre Hologramme am besten platzieren können, und zeigt, ob die Stelle, an der sie das Hologramm platzieren möchten, nicht zugeordnet ist. Sie können dem Benutzer "Elemente zuwenden", wenn sie zu weit in einem Winkel landen.

## <a name="conceptual-overview"></a>Konzeptionelle Übersicht

![Gitteroberflächen, die einen Raum abdecken](images/SurfaceReconstruction.jpg)<br>
*Ein Beispiel für ein Raumzuordnungsgitter, das einen Raum abdeckt*

Die beiden primären Objekttypen, die für die räumliche Zuordnung verwendet werden, sind "Spatial Surface Observer" und "Spatial Surface".

Die Anwendung stellt dem Spatial Surface Observer ein oder mehrere begrenzungsvolumes zur Verfügung, um die Bereiche des Raums zu definieren, in denen die Anwendung räumliche Zuordnungsdaten empfangen möchte. Für jedes dieser Volumes stellt die räumliche Zuordnung der Anwendung einen Satz räumlicher Oberflächen bereit.

Diese Volumes können stationär sein (an einem festen Ort, der auf der realen Welt basiert), oder sie können an die HoloLens angefügt werden (sie bewegen sich, drehen sich jedoch nicht, mit dem HoloLens, während er sich durch die Umgebung bewegt). Jede räumliche Oberfläche beschreibt reale Oberflächen in einem kleinen Raumvolumen, dargestellt als Dreiecksgitter, das an ein weltumschließendes [räumliches Koordinatensystem](coordinate-systems.md)angefügt ist.

Wenn der HoloLens neue Daten über die Umgebung sammelt und Änderungen an der Umgebung auftreten, werden räumliche Oberflächen angezeigt, verschwinden und ändern sich.

## <a name="spatial-awareness-design-concepts-demo"></a>Demo zu Entwurfskonzepten für räumliche Wahrnehmung

Wenn Sie die Entwurfskonzepte für räumliche Wahrnehmung in Aktion sehen möchten, sehen Sie sich unsere Videodemo **designing Hologramme – Spatial Awareness** weiter unten an. Wenn Sie fertig sind, fahren Sie mit einem ausführlicheren Einblick in bestimmte Themen fort.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

*Dieses Video wurde aus der HoloLens 2-App „Entwerfen von Hologrammen“ aufgenommen. Laden Sie die vollständige Erfahrung [hier](https://aka.ms/dhapp) herunter, und genießen Sie sie.*

## <a name="spatial-mapping-vs-scene-understanding-worldmesh"></a>Spatial Mapping vs. Scene Understanding WorldMesh

Für HoloLens 2 ist es möglich, eine statische Version der räumlichen Zuordnungsdaten mithilfe des [Scene Understanding SDK](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md) (EnableWorldMesh-Einstellung) abzufragen. Hier sind die Unterschiede zwischen zwei Möglichkeiten für den Zugriff auf die räumlichen Zuordnungsdaten:
* Raumzuordnungs-API:
   * Begrenzter Bereich: Die räumlichen Zuordnungsdaten, die Anwendungen in einer begrenzten Größe zur Verfügung stehen, die in einer "Blase" um den Benutzer zwischengespeichert sind.
   * Stellt Updates für geänderte Gitternetzbereiche mit geringer Latenz über SurfacesChanged-Ereignisse bereit.
   * Variable Detailebene, gesteuert durch den Parameter "Triangles Per Kubikmeter".
* Scene understanding SDK:
   * Unbegrenzter Bereich: Stellt alle gescannten räumlichen Zuordnungsdaten innerhalb des Abfrageradius bereit.
   * Stellt eine statische Momentaufnahme der räumlichen Zuordnungsdaten bereit. Zum Abrufen der aktualisierten räumlichen Zuordnungsdaten muss eine neue Abfrage für das gesamte Gitternetz ausgeführt werden.
   * Konsistente Detailebene, die durch die Einstellung RequestedMeshLevelOfDetail gesteuert wird.

## <a name="what-influences-spatial-mapping-quality"></a>Was wirkt sich auf die Qualität der räumlichen Zuordnung aus?

Die Häufigkeit und der Schweregrad dieser Fehler können sich auf mehrere Faktoren auswirken, die [hier](/hololens/hololens-environment-considerations)ausführlich beschrieben werden.  Sie sollten Ihre Anwendung jedoch so entwerfen, dass der Benutzer seine Ziele auch bei Fehlern in den Räumlichen Zuordnungsdaten erreichen kann.

## <a name="common-usage-scenarios"></a>Allgemeine Verwendungsszenarios

![Abbildungen allgemeiner Verwendungsszenarien für räumliche Zuordnungen: Platzierung, Verdeckung, Physik und Navigation](images/sm-concepts-1000px.png)

### <a name="placement"></a>Platzierung

Die räumliche Zuordnung bietet Anwendungen die Möglichkeit, dem Benutzer natürliche und vertraute Interaktionsformen zu präsentieren. was könnte natürlicher sein, als ihr Telefon auf dem Tisch zu platzieren?

Das Einschränken der Platzierung von Hologrammen (oder allgemeiner gesagt jede Auswahl räumlicher Positionen), die auf Oberflächen liegt, ermöglicht eine natürliche Zuordnung von 3D (Punkt im Raum) zu 2D (Punkt auf der Oberfläche). Dies reduziert die Menge der Informationen, die der Benutzer für die Anwendung bereitstellen muss, und macht die Interaktionen des Benutzers schneller, einfacher und präziser. Dies ist richtig, da "Distance Away" nicht für die physische Kommunikation mit anderen Personen oder Computern verwendet wird. Wenn wir mit dem Finger zeigen, geben wir eine Richtung, aber keinen Abstand an.

Ein wichtiger Nachteil hierbei ist, dass, wenn eine Anwendung Abstand von der Richtung hergeleitet (z. B. durch einen Raycast entlang der Anviertrichtung des Benutzers, um die nächstgelegene räumliche Oberfläche zu finden), ergebnisse liefern muss, die der Benutzer zuverlässig vorhersagen kann. Andernfalls verliert der Benutzer sein Gefühl der Kontrolle, und dies kann schnell frustrierend werden. Eine Methode, die dabei hilft, besteht darin, mehrere Raycasts statt nur eines zu verwenden. Die Aggregatergebnisse sollten reibungsloser und besser vorhersagbar sein und weniger anfällig für die Einflussnahme durch vorübergehende "Ausreißerergebnisse" sein (dies kann durch Lichtstrahl verursacht werden, der kleine Löcher durchläuft oder kleine Teile der Geometrie erreicht, die dem Benutzer nicht bekannt sind). Aggregation oder Glättung können auch im Laufe der Zeit ausgeführt werden. Beispielsweise können Sie die maximale Geschwindigkeit begrenzen, mit der ein Hologramm in der Entfernung zum Benutzer variieren kann. Das einfache Einschränken des Mindest- und Höchstwerts für die Entfernung kann ebenfalls hilfreich sein, sodass das verschobene Hologramm nicht plötzlich in die Entfernung fliegt oder wieder in das Gesicht des Benutzers abstürzt.

Anwendungen können auch die Form und Richtung von Oberflächen verwenden, um die Hologrammplatzierung zu steuern. Ein holografischer Hoss sollte nicht durch Dielen blättern und mit dem Boden leer sein, auch wenn er etwas ungleichmäßig ist. Diese Art von Funktionalität beruht wahrscheinlich auf der Verwendung von physikalischen Kollisionen und nicht von Raycasts, aber es gelten ähnliche Bedenken. Wenn das platzierte Hologramm viele kleine Polygone aufhält, wie z. B. die Ecken auf einem Tisch, kann es sinnvoll sein, die physikalische Darstellung dieser Polygone auf etwas breiter und reibungsloser zu erweitern, sodass sie besser über räumliche Oberflächen gleiten können, ohne sich zu verkleinern.

Im Extremfall kann die Benutzereingabe vollständig vereinfacht werden, und räumliche Oberflächen können für eine vollständig automatische Hologrammplatzierung verwendet werden. Beispielsweise könnte die Anwendung einen holografischen Lichtschalter an einer Stelle an der Wand platzieren, auf die der Benutzer drücken kann. Die gleiche Einschränkung bezüglich der Vorhersagbarkeit gilt hier doppelt. Wenn der Benutzer die Kontrolle über die Hologrammplatzierung erwartet, die Anwendung hologramme jedoch nicht immer an der erwarteten Stelle platziert (wenn der Lichtschalter an einer Stelle angezeigt wird, die der Benutzer nicht erreichen kann), ist dies eine frustrierende Erfahrung. Es kann sogar schlechter sein, eine automatische Platzierung vorzunehmen, die eine Benutzerkorrektur erfordert, als nur zu verlangen, dass der Benutzer die Platzierung immer selbst vornimmt. da eine erfolgreiche automatische Platzierung *erwartet* wird, wirkt die manuelle Korrektur wie eine Belastung!

Beachten Sie auch, dass die Fähigkeit einer Anwendung, räumliche Oberflächen für die Platzierung zu verwenden, stark von der [Scanerfahrung](spatial-mapping.md#the-environment-scanning-experience)der Anwendung abhängt. Wenn eine Oberfläche nicht überprüft wurde, kann sie nicht für die Platzierung verwendet werden. Es liegt an der Anwendung, dies für den Benutzer klar zu machen, damit er entweder beim Scannen neuer Oberflächen oder beim Auswählen eines neuen Standorts helfen kann.

Visuelles Feedback an den Benutzer ist während der Platzierung von größter Bedeutung. Der Benutzer muss wissen, wo das Hologramm auf der nächsten Oberfläche mit [Erdungseffekten](spatial-mapping.md#visualization)basiert. Sie sollten verstehen, warum die Bewegung ihres Hologramms eingeschränkt wird (z. B. aufgrund von Kollisionen mit einer anderen Oberfläche in der Nähe). Wenn sie kein Hologramm an der aktuellen Position platzieren können, sollte visuelles Feedback deutlich machen, warum nicht. Wenn der Benutzer z. B. versucht, eine holografische Couch zu platzieren, die halb an der Wand hängen bleibt, sollten die Teile der Couch, die sich hinter der Wand befinden, in einer farbigen Farbe pulsieren. Oder umgekehrt: Wenn die Anwendung keine räumliche Oberfläche an einem Ort finden kann, an dem der Benutzer eine reale Oberfläche sehen kann, sollte die Anwendung dies deutlich machen. Das offensichtliche Fehlen eines grounding-Effekts in diesem Bereich kann diesen Zweck erreichen.

### <a name="occlusion"></a>Okklusion

Eine der Hauptverwendungen räumlicher Zuordnungsoberflächen ist einfach das Verdecken von Hologrammen. Dieses einfache Verhalten hat einen großen Einfluss auf die wahrgenommene Realität von Hologrammen und trägt dazu bei, ein sichtbares Gefühl zu schaffen, das tatsächlich den gleichen physischen Raum wie der Benutzer beeinträchtigt.

Occlusion stellt dem Benutzer auch Informationen bereit. Wenn ein Hologramm von einer realen Oberfläche verdeckt zu sein scheint, bietet dies zusätzliches visuelles Feedback zur räumlichen Position dieses Hologramms in der Welt. Umgekehrt kann die Verdeckung auch hilfreiche Informationen für den Benutzer *ausblenden.* Das Verdecken von Hologrammen hinter Wänden kann die visuelle Übersicht auf intuitive Weise reduzieren. Um ein Hologramm auszublenden oder anzuzeigen, muss der Benutzer lediglich den Kopf bewegen.

Occlusion kann auch verwendet werden, um die Erwartungen an eine natürliche Benutzeroberfläche basierend auf vertrauten physischen Interaktionen zu erfüllen. Wenn ein Hologramm von einer Oberfläche verdeckt wird, liegt dies daran, dass diese Oberfläche voll ist. Daher sollte der Benutzer erwarten, dass das Hologramm mit dieser Oberfläche *kollidiert* und nicht durch sie geleitet wird.

Manchmal ist die Verdeckung von Hologrammen unerwünscht. Wenn ein Benutzer mit einem Hologramm interagieren muss, muss er es sehen – auch wenn es sich hinter einer realen Oberfläche befindet. In solchen Fällen ist es in der Regel sinnvoll, ein solches Hologramm anders zu rendern, wenn es verdeckt ist (z. B. durch Verringern seiner Helligkeit). Auf diese Weise kann der Benutzer das Hologramm visuell finden, aber er weiß immer noch, dass es sich hinter etwas befindet.

### <a name="physics"></a>Physische Effekte

Die Verwendung der Physikalischen Simulation ist eine weitere Möglichkeit, mit der die räumliche Zuordnung verwendet werden kann, um das *Vorhandensein* von Hologrammen im physischen Raum des Benutzers zu verstärken. Wenn meine holografische Kugel realistisch von meinem Tisch rollt, über den Boden springt und unter der Couch verschwindet, ist es für mich möglicherweise schwierig zu glauben, dass sie nicht vorhanden ist.

Die Physikalische Simulation bietet einer Anwendung auch die Möglichkeit, natürliche und vertraute physikalische Interaktionen zu verwenden. Das Bewegen eines Holografiestücks auf dem Boden ist für den Benutzer wahrscheinlich einfacher, wenn die Oberfläche reagiert, als würde sie mit der entsprechenden Trägheit und Reibung über den Boden gleiten.

Um realistisches physisches Verhalten zu generieren, müssen Sie wahrscheinlich eine [Gitternetzverarbeitung](spatial-mapping.md#mesh-processing) durchführen, z. B. Löcher füllen, unverankerte Hallucinationen entfernen und raue Oberflächen glätten.

Sie müssen auch berücksichtigen, wie sich die [Scanerfahrung](spatial-mapping.md#the-environment-scanning-experience) Ihrer Anwendung auf die physikalische Simulation auswirkt. Erstens werden fehlende Oberflächen nicht mit etwas kollidiert. Was geschieht, wenn die Kugel die Würfe herunterrollt und am Ende der bekannten Welt endet? Zweitens müssen Sie entscheiden, ob Sie im Laufe der Zeit weiterhin auf Änderungen in der Umgebung reagieren. In einigen Fällen möchten Sie so schnell wie möglich reagieren. Angenommen, der Benutzer verwendet Türen und Türen als verschiebbare Balkensymbole zum Schutz vor einem Tempest eingehender lateinischer Pfeile. In anderen Fällen möchten Sie jedoch möglicherweise neue Updates ignorieren. Das Fahren ihres holografischen Sportwagens um die Racespur auf Ihrem Boden kann plötzlich nicht so viel Spaß machen, wenn Sich Ihr Hund entscheidet, sich in der Mitte der Spur zu befinden.

### <a name="navigation"></a>Navigation

Anwendungen können räumliche Zuordnungsdaten verwenden, um holografischen Zeichen (oder Agents) die Möglichkeit zu geben, in der realen Welt auf die gleiche Weise wie eine echte Person zu navigieren. Dies kann dazu beitragen, das Vorhandensein holografischer Zeichen zu verstärken, indem sie auf die gleichen natürlichen, vertrauten Verhaltensweisen wie die des Benutzers und seiner Freunde beschränkt werden.

Navigationsfunktionen können auch für Benutzer nützlich sein. Sobald eine Navigationskarte in einem bestimmten Bereich erstellt wurde, kann sie freigegeben werden, um holografische Anweisungen für neue Benutzer bereitzustellen, die mit diesem Standort nicht vertraut sind. Diese Karte könnte so entworfen werden, dass der "Verkehrsfluss" reibungslos verläuft oder Dass es an gefährlichen Orten wie Baustellen zu Einem Verkehrstoten kommt.

Die wichtigsten technischen Herausforderungen bei der Implementierung von Navigationsfunktionen sind die zuverlässige Erkennung von begehbaren Oberflächen (Menschen gehen nicht auf Tabellen!) und eine gute Anpassung an Änderungen in der Umgebung (Menschen durchlaufen keine geschlossenen Türen!). Das Gitternetz erfordert möglicherweise eine [Verarbeitung,](spatial-mapping.md#mesh-processing) bevor es für die Pfadplanung und Navigation durch ein virtuelles Zeichen verwendet werden kann. Das Glätten des Gitternetzes und das Entfernen von Halluzinationen können dazu beitragen, zu vermeiden, dass Zeichen hängen bleiben. Möglicherweise möchten Sie auch das Gitternetz drastisch vereinfachen, um die Pfadplanungs- und Navigationsberechnungen Ihres Zeichens zu beschleunigen. Diese Herausforderungen haben bei der Entwicklung der Spieletechnologie große Aufmerksamkeit erhalten, und es gibt eine Vielzahl von verfügbaren Forschungsinhalten zu diesen Themen.

Die integrierte NavMesh-Funktionalität in Unity kann nicht mit räumlichen Zuordnungsoberflächen verwendet werden. Dies liegt daran, dass räumliche Zuordnungsoberflächen erst bekannt sind, wenn die Anwendung gestartet wird. NavMesh-Datendateien müssen jedoch im Voraus aus Quellressourcen generiert werden. Beachten Sie außerdem, dass das Räumliche Zuordnungssystem keine [Informationen zu Oberflächen](spatial-mapping.md#the-environment-scanning-experience) bereitstellt, die weit vom aktuellen Standort des Benutzers entfernt sind. Daher muss sich die Anwendung oberflächen selbst "merken", wenn sie eine Karte eines großen Bereichs erstellen soll.

### <a name="visualization"></a>Visualisierung

In den meisten Jahren ist es für räumliche Oberflächen geeignet, unsichtbar zu sein. , um visuelle Überladen zu minimieren und die reale Welt für sich selbst sprechen zu lassen. Manchmal ist es jedoch hilfreich, räumliche Kartenoberflächen direkt zu visualisieren, obwohl ihre realen Entsprechungen sichtbar sind.

Wenn der Benutzer z. B. versucht, ein Hologramm auf einer Oberfläche zu platzieren (z. B. ein holografisches Gehäuse an der Wand), kann es nützlich sein, das Hologramm zu "bodenn", indem er einen Schatten auf die Oberfläche wirft. Dies gibt dem Benutzer ein viel klareres Gefühl der genauen physischen Nähe zwischen dem Hologramm und der Oberfläche. Dies ist auch ein Beispiel für die allgemeinere Praxis der visuellen "Vorschau" einer Änderung, bevor der Benutzer sich dafür committet.

Durch die Visualisierung von Oberflächen kann die Anwendung das Verständnis der Umgebung für den Benutzer freigeben. Beispielsweise könnte ein holografisches Brettspiel die horizontalen Oberflächen visualisieren, die es als "Tabellen" identifiziert hat, damit der Benutzer weiß, wo er interagieren soll.

Das Visualisieren von Oberflächen kann eine nützliche Möglichkeit sein, dem Benutzer In der Nähe befindliche Bereiche anzuzeigen, die in der Ansicht ausgeblendet sind. Dies könnte eine Möglichkeit bieten, dem Benutzer den Zugriff auf seine Kita (und alle darin enthaltenen Hologramme) aus seinem Haus zu gewähren.

Die von der räumlichen Zuordnung bereitgestellten Oberflächengitternetze sind möglicherweise nicht besonders "sauber". Es ist wichtig, sie entsprechend zu visualisieren. Herkömmliche Beleuchtungsberechnungen können Fehler in Oberflächennormalisierungen visuell ablenkend hervorheben, während "bereinigte" Texturen, die auf die Oberfläche projiziert werden, dabei helfen können, ihr eine übersichtlichere Darstellung zu verleihen. Es ist auch möglich, [die Gitternetzverarbeitung](spatial-mapping.md#mesh-processing) vor dem Rendern der Oberflächen zur Verbesserung der Gitternetzeigenschaften zu durchführen.

> [!NOTE]
> HoloLens 2 implementiert eine neue [Scene Understanding-Runtime,](scene-understanding.md)die Mixed Reality Entwicklern eine strukturierte, übergeordnete Umgebungsdarstellung bereitstellt, die die Implementierung von Platzierung, Verdeckung, Physik und Navigation vereinfacht.

## <a name="using-the-surface-observer"></a>Verwenden des Surface Observer

Der Ausgangspunkt für die räumliche Zuordnung ist der Oberflächenbeoter. Der Programmablauf sieht wie folgt aus:
* Erstellen eines Surface Observer-Objekts
   * Geben Sie ein oder mehrere räumliche Volumes an, um die bereiche zu definieren, in denen die Anwendung räumliche Zuordnungsdaten empfangen möchte. Ein räumliches Volume ist einfach eine Form, die einen Raumbereich definiert, z. B. eine Kugel oder ein Feld.
   * Verwenden Sie ein räumliches Volume mit einem weltweit gesperrten räumlichen Koordinatensystem, um einen festen Bereich der physischen Welt zu identifizieren.
   * Verwenden Sie ein räumliches Volume, das jeden Frame mit einem körpergesperrten räumlichen Koordinatensystem aktualisiert, um einen Raumbereich zu identifizieren, der sich mit dem Benutzer verschiebt (aber nicht rotiert).
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

Räumliche Oberflächen werden durch dichte Dreiecksgitternetze dargestellt. Das Speichern, Rendern und Verarbeiten dieser Gitternetze kann erhebliche Rechen- und Speicherressourcen beanspruchen. Daher sollte jede Anwendung ein Gittermodell-Cacheschema anwenden, das ihren Anforderungen entspricht, um die für die Meshverarbeitung und -speicherung verwendeten Ressourcen zu minimieren. Dieses Schema sollte bestimmen, welche Gitternetze beibehalten und welche verworfen werden sollen und wann das Gittermodell für jede räumliche Oberfläche aktualisiert werden soll.

Viele der hier erläuterten Überlegungen informieren direkt darüber, wie Ihre Anwendung die Meshzwischenspeicherung verwenden sollte. Sie sollten berücksichtigen, wie sich der Benutzer durch die Umgebung bewegt, welche Oberflächen benötigt werden, wann verschiedene Oberflächen beobachtet werden und wann Änderungen in der Umgebung erfasst werden sollen.

Beim Interpretieren des vom Surface Observer bereitgestellten Ereignisses "oberflächenverändert" lautet die grundlegende Zwischenspeicherungslogik für das Gitternetz wie folgt:
* Wenn die Anwendung eine räumliche Oberflächen-ID sieht, die sie zuvor noch nicht gesehen hat, sollte sie diese als neue räumliche Oberfläche behandeln.
* Wenn die Anwendung eine räumliche Oberfläche mit einer bekannten ID, aber mit einer neuen Aktualisierungszeit sieht, sollte sie diese als aktualisierte räumliche Oberfläche behandeln.
* Wenn die Anwendung keine räumliche Oberfläche mit einer bekannten ID mehr sieht, sollte sie diese als entfernte räumliche Oberfläche behandeln.

Es liegt an jeder Anwendung, dann die folgenden Optionen zu treffen:
* Sollte für neue räumliche Oberflächen ein Gitter angefordert werden?
   * Im Allgemeinen sollte das Gitternetz für neue räumliche Oberflächen sofort angefordert werden, was dem Benutzer nützliche neue Informationen liefern kann.
   * Neue räumliche Oberflächen in der Nähe und vor dem Benutzer sollten jedoch Priorität erhalten, und das Gitternetz sollte zuerst angefordert werden.
   * Wenn das neue Gittermodell nicht benötigt wird, z. B. wenn die Anwendung ihr Modell der Umgebung dauerhaft oder vorübergehend "fixiert" hat, sollte es nicht angefordert werden.
* Sollte für aktualisierte räumliche Oberflächen das Gitternetz angefordert werden?
   * Aktualisierte räumliche Oberflächen in der Nähe und vor dem Benutzer sollten Priorität erhalten, und das Gitternetz sollte zuerst angefordert werden.
   * Es kann auch sinnvoll sein, neuen Oberflächen eine höhere Priorität zuzuweisen als aktualisierten Oberflächen, insbesondere während der Überprüfung.
   * Um die Verarbeitungskosten zu begrenzen, möchten Anwendungen möglicherweise die Rate drosseln, mit der sie Aktualisierungen von räumlichen Oberflächen verarbeiten.
   * Möglicherweise kann abgeleitet werden, dass Änderungen an einer räumlichen Oberfläche geringfügig sind, z. B. wenn die Begrenzungen der Oberfläche klein sind. In diesem Fall ist die Aktualisierung möglicherweise nicht wichtig genug, um sie zu verarbeiten.
   * Aktualisierungen räumlicher Oberflächen außerhalb des aktuellen Bereichs, der für den Benutzer von Interesse ist, können vollständig ignoriert werden. In diesem Fall kann es jedoch effizienter sein, die räumlichen Begrenzungsvolumen zu ändern, die vom Oberflächenbeoachter verwendet werden.
* Sollte das Gitternetz für entfernte räumliche Oberflächen verworfen werden?
   * Im Allgemeinen sollte das Gitternetz für entfernte räumliche Oberflächen sofort verworfen werden, damit die Hologrammverdeckung korrekt bleibt.
   * Wenn die Anwendung jedoch Grund zu der Annahme hat, dass eine räumliche Oberfläche in Kürze wieder angezeigt wird (basierend auf dem Entwurf der Benutzeroberfläche), ist es möglicherweise effizienter, sie beizubehalten, als das Gitternetz zu verwerfen und später erneut zu erstellen.
   * Wenn die Anwendung ein umfangreiches Modell der Umgebung des Benutzers aufbaut, möchte sie möglicherweise überhaupt keine Gittermodelle verwerfen. Die Ressourcennutzung muss jedoch weiterhin eingeschränkt werden, möglicherweise durch Daspoolen von Gitternetzen auf den Datenträger, wenn räumliche Oberflächen verschwinden.
   * Einige relativ seltene Ereignisse während der Generierung räumlicher Oberflächen können dazu führen, dass räumliche Oberflächen durch neue räumliche Oberflächen an einem ähnlichen Ort, aber mit unterschiedlichen IDs ersetzt werden. Daher sollten Anwendungen, die sich gegen das Verwerfen einer entfernten Oberfläche entscheiden, darauf achten, nicht mit mehreren stark überlappenden Gitternetzen für räumliche Oberflächen zu enden, die denselben Ort abdecken.
* Sollte das Gitternetz für alle anderen räumlichen Oberflächen verworfen werden?
   * Auch wenn eine räumliche Oberfläche vorhanden ist, sollte sie verworfen werden, wenn sie für die Benutzerfreundlichkeit nicht mehr nützlich ist. Wenn die Anwendung beispielsweise den Raum auf der anderen Seite eines Türbereichs durch einen alternativen virtuellen Raum "ersetzt", spielen die räumlichen Oberflächen in diesem Raum keine Rolle mehr.

Hier ist ein Beispiel für eine Strategie für die Meshzwischenspeicherung mit räumlicher und temporaler Hysterese:
* Stellen Sie sich eine Anwendung vor, die ein frustumförmiges räumliches Volume von Interesse verwenden möchte, das dem Anvieren des Benutzers folgt, während er sich umsehen und herumgehen möchte.
* Eine räumliche Oberfläche verschwindet möglicherweise vorübergehend von diesem Volume, einfach weil der Benutzer von der Oberfläche wegsieht oder schritte weiter entfernt... nur, um einen Moment später zurückzublicken oder sich näher zu bewegen. In diesem Fall stellt das Verwerfen und erneute Erstellen des Gitternetzes für diese Oberfläche viele redundante Verarbeitungen dar.
* Um die Anzahl der verarbeiteten Änderungen zu reduzieren, verwendet die Anwendung zwei Beobachter der räumlichen Oberfläche, einen innerhalb des anderen. Das größere Volume ist sphärisch und folgt dem Benutzer "verzögert". sie wird nur verschoben, wenn dies erforderlich ist, um sicherzustellen, dass ihr Mittelpunkt innerhalb von 2,0 Metern des Benutzers liegt.
* Neue und aktualisierte Gittergitternetze für räumliche Oberflächen werden immer vom kleineren Beobachter der inneren Oberfläche verarbeitet, aber Gittergitter werden zwischengespeichert, bis sie vom größeren Beobachter der äußeren Oberfläche entfernt werden. Dadurch kann die Anwendung viele redundante Änderungen aufgrund der lokalen Benutzerbewegung vermeiden.
* Da eine räumliche Oberfläche aufgrund von Nachverfolgungsverlusten auch vorübergehend ausgeblendet werden kann, verwirft die Anwendung auch entfernte räumliche Oberflächen während des Nachverfolgungsverlusts.
* Im Allgemeinen sollte eine Anwendung den Kompromiss zwischen einer reduzierten Updateverarbeitung und einer erhöhten Arbeitsspeicherauslastung auswerten, um die ideale Cachestrategie zu bestimmen.

## <a name="rendering"></a>Darstellung

Es gibt drei Hauptmethoden, mit denen Gitternetze für räumliche Zuordnungen tendenziell für das Rendering verwendet werden:
* Für die Oberflächenvisualisierung
   * Häufig ist es hilfreich, räumliche Oberflächen direkt zu visualisieren. Beispielsweise kann das Werfen von Schatten von Objekten auf räumliche Oberflächen hilfreiches visuelles Feedback für den Benutzer bereitstellen, während er Hologramme auf Oberflächen platziert.
   * Beachten Sie, dass räumliche Gitternetze sich von der Art der Gitternetze unterscheiden, die ein 3D-Interpret erstellen könnte. Die Dreieckstopologie ist nicht so "sauber" wie die von Menschen erstellte Topologie, und das Gitternetz hat verschiedene [Fehler.](spatial-mapping.md#what-influences-spatial-mapping-quality)
   * Um ein ansprechendes visuelles Erscheinungsbild zu erstellen, sollten Sie eine Gitternetzverarbeitung [verwenden,](spatial-mapping.md#mesh-processing)z. B. zum Füllen von Lücken oder normalen Oberflächenglättungen. Sie können auch einen Shader verwenden, um vom Interpreten entworfene Texturen in Ihr Gitternetz zu projektieren, anstatt die Gitternetztopologie und die Normalen direkt zu visualisieren.
* Für das Umschließen von Hologrammen hinter realen Oberflächen
   * Räumliche Oberflächen können in einem tiefenbasierten Durchlauf gerendert werden, der sich nur auf den Tiefenpuffer und nicht auf Farbrenderingziele auswirken kann. [](/windows/win32/direct3d9/depth-buffers)
   * Dies primiert den Tiefenpuffer, um anschließend gerenderte Hologramme hinter räumlichen Oberflächen zu verdecken. Die genaue Okklusion von Hologrammen verbessert das Gefühl, dass Hologramme tatsächlich im physischen Raum des Benutzers vorhanden sind.
   * Aktualisieren Sie zum Aktivieren des Tiefenrenderings den Blendzustand, um [renderTargetWriteMask](/windows/win32/api/d3d11_1/ns-d3d11_1-d3d11_render_target_blend_desc1) für alle Farbrenderingziele auf 0 (null) festzulegen.
* Zum Ändern der Darstellung von Hologrammen, die von realen Oberflächen umschließen
   * Normalerweise wird gerenderte Geometrie ausgeblendet, wenn sie verdeckt wird. Dies wird erreicht, indem [](/windows/win32/api/d3d11/ns-d3d11-d3d11_depth_stencil_desc) sie die Tiefenfunktion im Tiefen-Schablonenzustand auf "kleiner als oder  gleich" setzt. Dies bewirkt, dass die Geometrie nur dort sichtbar ist, wo sie sich näher an der Kamera befindet als alle zuvor gerenderten Geometrien.
   * Es kann jedoch hilfreich sein, bestimmte Geometrien auch dann sichtbar zu halten, wenn sie verblendet ist, und ihre Darstellung zu ändern, wenn sie als Möglichkeit zur Visuellen Feedbacks für den Benutzer verblendet wird. So kann die Anwendung dem Benutzer beispielsweise die Position eines Objekts anzeigen und gleichzeitig deutlich machen, dass sich hinter einer realen Oberfläche befindet.
   * Um dies zu erreichen, rendern Sie die Geometrie ein zweites Mal mit einem anderen Shader, der die gewünschte "okkluded"-Darstellung erstellt. Bevor Sie die Geometrie zum zweiten Mal rendern, nehmen Sie zwei Änderungen am [Tiefen-Schablonenzustand vor.](/windows/win32/api/d3d11/ns-d3d11-d3d11_depth_stencil_desc) Legen Sie zunächst die Tiefenfunktion auf "größer als oder gleich" fest,  damit die Geometrie nur dort sichtbar ist, wo sie weiter von der Kamera entfernt ist als alle zuvor gerenderten Geometrien. Legen Sie zweitens die DepthWriteMask auf 0 (null) fest, damit der Tiefenpuffer nicht geändert  wird (der Tiefenpuffer sollte weiterhin die Tiefe der Geometrie darstellen, die der Kamera am nächsten liegt).

[Die Leistung](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) ist ein wichtiges Problem beim Rendern von Gittern für räumliche Zuordnungen. Hier sind einige Renderingleistungstechniken für das Rendern von Gittern für räumliche Zuordnungen:
* Anpassen der Dreiecksdichte
   * Fordern Sie beim Anfordern von Gittern der räumlichen Oberfläche von Ihrem Oberflächenbeobachter die niedrigste Dichte von Dreiecksgittern an, die für Ihre Anforderungen ausreicht.
   * Es kann sinnvoll sein, die Dreiecksdichte auf Oberflächenbasis zu variieren, abhängig vom Abstand der Oberfläche zum Benutzer und ihrer Relevanz für die Benutzererfahrung.
   * Die Reduzierung der Dreiecksanzahl reduziert die Speicherauslastung und die Vertexverarbeitungskosten auf der GPU, wirkt sich jedoch nicht auf die Pixelverarbeitungskosten aus.
* Verwenden von Frustum-Culling
   * Frustum-Culling überspringt Zeichnungsobjekte, die nicht angezeigt werden können, da sie sich außerhalb des aktuellen Frustums der Anzeige befinden. Dadurch werden sowohl die CPU- als auch die GPU-Verarbeitungskosten reduziert.
   * Da das Culling auf Gitternetzbasis durchgeführt wird und räumliche Oberflächen groß sein können, kann das Aufbrechen jedes Gitters der räumlichen Oberfläche in kleinere Gitternetze zu einem effizienteren Culling führen (da weniger Offscreen-Dreiecke gerendert werden). Es gibt jedoch einen Kompromiss. Desto mehr Gitternetze sie haben, desto mehr Zeichnen-Aufrufe müssen Sie tätigen, was die CPU-Kosten erhöhen kann. Im Extremfall können die Frustum-Cullingberechnungen selbst sogar messbare CPU-Kosten haben.
* Anpassen der Rendering reihenfolge
   * Räumliche Oberflächen sind in der Regel groß, da sie die gesamte Umgebung des Benutzers darstellen. Die Pixelverarbeitungskosten auf der GPU können hoch sein, insbesondere in Fällen, in denen mehr als eine Ebene der sichtbaren Geometrie (einschließlich räumlicher Oberflächen und anderer Hologramme) besteht. In diesem Fall wird die ebene, die dem Benutzer am nächsten liegt, alle Schichten weiter entfernt verschließen, sodass jede GPU-Zeit, die für das Rendern dieser entfernteren Ebenen aufwendet wird, verschwendet wird.
   * Um diese redundante Arbeit auf der GPU zu reduzieren, ist es hilfreich, undurchsichtige Oberflächen in der Reihenfolge von vorn zu zurück zu rendern (nähere zuerst, entfernte Oberflächen zuletzt). Mit "opaque" werden Oberflächen bezeichnet, für die DepthWriteMask in Ihrem [Tiefen-Schablonenzustand auf eins festgelegt ist.](/windows/win32/api/d3d11/ns-d3d11-d3d11_depth_stencil_desc) Wenn die nächstgelegenen Oberflächen gerendert werden, wird der Tiefenpuffer so geprimt, dass entferntere Oberflächen effizient vom Pixelprozessor auf der GPU übersprungen werden.

## <a name="mesh-processing"></a>Mesh-Verarbeitung

Eine Anwendung möchte möglicherweise verschiedene [Vorgänge an Gittern](spatial-mapping.md#mesh-processing) der räumlichen Oberfläche entsprechend ihren Anforderungen machen. Die index- und vertex-Daten, die mit jedem raumoberflächen Gitternetz bereitgestellt werden, verwenden das gleiche vertraute Layout wie die Scheitelpunkt- und Indexpuffer, die zum Rendern von [Dreiecksgittern](/windows/win32/direct3d9/rendering-from-vertex-and-index-buffers) in allen modernen Rendering-APIs verwendet werden. Eine wichtige Zu beachtende Tatsache ist jedoch, dass Dreiecke der räumlichen Zuordnung eine im Uhrzeigersinn **vorn wendende Reihenfolge haben.** Jedes Dreieck wird durch drei Scheitelpunktindizes im Indexpuffer des Gitters dargestellt, und  diese Indizes identifizieren die Scheitelpunkte des Dreiecks im Uhrzeigersinn, wenn das Dreieck von der vorderen Seite aus angezeigt wird.  Die Vorderseite (oder außen) von Gittern der räumlichen Oberfläche entspricht der vorderen (sichtbaren) Seite der realen Oberflächen.

Anwendungen sollten die Gittermodellverschnunfachung nur dann tun, wenn die vom Oberflächenbeobachter bereitgestellte grobe Dreiecksdichte immer noch zu gering ist. Diese Arbeit ist rechenintensiv und wird bereits von der Laufzeit ausgeführt, um die verschiedenen bereitgestellten Detailebenen zu generieren.

Da jeder Oberflächenbeobachter mehrere nicht miteinander verbundenen räumlichen Oberflächen bereitstellen kann, möchten einige Anwendungen diese räumlichen Oberflächengitter möglicherweise miteinander abschneiden und dann zusammenschneiden. Im Allgemeinen ist der Clippingschritt erforderlich, da sich naheliegende Gitternetze für räumliche Oberflächen häufig geringfügig überlappen.

## <a name="raycasting-and-collision"></a>Raycasting und Kollision

Damit eine physikalische API (z. B. [Havok)](https://www.havok.com/)eine Anwendung mit Raycasting- und Kollisionsfunktionen für räumliche Oberflächen bereitstellen kann, muss die Anwendung raumbezogene Oberflächengitternetze für die physikalische API bereitstellen. Gitternetze, die für die Physik verwendet werden, haben häufig die folgenden Eigenschaften:
* Sie enthalten nur eine kleine Anzahl von Dreiecken. Physikalische Operationen sind rechenintensiver als Renderingvorgänge.
* Sie sind "water-tight". Oberflächen, die als fest gedacht sind, sollten keine kleinen Lücken in ihnen haben. sogar Lücken, die zu klein sind, um sichtbar zu sein, können Probleme verursachen.
* Sie werden in konvexe Hüllen konvertiert. Konvexe Hüllen verfügen über wenige Polygone und sind frei von Lücken, und sie sind wesentlich recheneffizienter zu verarbeiten als rohe Dreiecksgittermodelle.

Beachten Sie beim Verwenden von Raycasts für räumliche Oberflächen, dass diese Oberflächen oft komplexe, unübersichtliche Formen mit unübersichtlichen kleinen Details sind – genau wie Ihr Arbeitsplatz! Dies bedeutet, dass ein einzelner Raycast häufig nicht ausreicht, um genügend Informationen über die Form der Oberfläche und die Form des leeren Raums in ihrer Nähe zu erhalten. Es ist in der Regel eine gute Idee, viele Raycasts in einem kleinen Bereich zu verwenden und die Aggregatergebnisse zu verwenden, um ein zuverlässigeres Verständnis der Oberfläche zu erzielen. Wenn Sie z. B. den Durchschnitt von 10 Raycasts verwenden, um die Hologrammplatzierung auf einer Oberfläche zu leiten, führt dies zu einem deutlich reibungsloseren und weniger "jittery"-Ergebnis, da nur ein einzelner Raycast verwendet wird.

Beachten Sie jedoch, dass jeder Raycast hohe Berechnungskosten haben kann. Abhängig von Ihrem Nutzungsszenario sollten Sie die Berechnungskosten für zusätzliche Raycasts (für [](spatial-mapping.md#mesh-processing) jeden Frame) gegen die Berechnungskosten der Gittermodellverarbeitung abhandeln, um Lücken in räumlichen Oberflächen zu glätten und zu entfernen (dies erfolgt, wenn räumliche Gittermodelle aktualisiert werden).

## <a name="the-environment-scanning-experience"></a>Umgebungsscans

Jede Anwendung, die räumliche Zuordnung verwendet, sollte eine "Scanerfahrung" bereitstellen. der Prozess, durch den die Anwendung den Benutzer durchsucht, um Oberflächen zu überprüfen, die für die korrekte Funktionsweise der Anwendung erforderlich sind.

![Beispiel für die Überprüfung](images/sr-mixedworld-140429-8pm-00068-1000px.png)<br>
*Beispiel für die Überprüfung*

Die Art dieser Überprüfungserfahrung kann je nach den Anforderungen der einzelnen Anwendungen stark variieren, aber es sollten zwei Hauptprinzipien für den Entwurf gelten.

Erstens ist **eine klare Kommunikation mit dem Benutzer das Hauptanliegen** von . Der Benutzer sollte immer wissen, ob die Anforderungen der Anwendung erfüllt werden. Wenn sie nicht erfüllt werden, sollte dem Benutzer sofort klar sein, warum dies der Fall ist, und er sollte schnell dazu veranlasst werden, die entsprechenden Maßnahmen zu ergreifen.

Zweitens sollten **Anwendungen versuchen, ein Gleichgewicht zwischen** Effizienz und Zuverlässigkeit zu finden. Wenn dies zuverlässig möglich **ist,** sollten Anwendungen automatisch räumliche Zuordnungsdaten analysieren, um dem Benutzer Zeit zu sparen. Wenn dies nicht zuverlässig möglich ist, sollten Anwendungen es dem Benutzer stattdessen ermöglichen, der Anwendung schnell die benötigten zusätzlichen Informationen zur Verfügung zu stellen.

Um die richtige Überprüfungserfahrung zu entwerfen, überlegen Sie, welche der folgenden Möglichkeiten auf Ihre Anwendung anwendbar sind:

* **Keine Überprüfungserfahrung**
   * Eine Anwendung kann ohne geführte Scanfunktionen einwandfrei funktionieren. Es wird über Oberflächen erfahren, die im Verlauf der natürlichen Benutzerbewegung beobachtet werden.
   * Beispielsweise erfordert eine Anwendung, die dem Benutzer das Zeichnen auf Oberflächen mit holografischem Spray paint ermöglicht, nur Kenntnisse über die Oberflächen, die für den Benutzer derzeit sichtbar sind.
   * Die Umgebung wird möglicherweise bereits überprüft, wenn der Benutzer bereits viel Zeit mit der Verwendung des HoloLens.
   * Beachten Sie jedoch, dass die kamera, die von der räumlichen Zuordnung verwendet wird, nur 3,1 m vor dem Benutzer sehen kann, sodass die räumliche Zuordnung keine entfernteren Oberflächen kennt, es sei denn, der Benutzer hat sie in der Vergangenheit aus näherer Entfernung beobachtet.
   * Damit der Benutzer versteht, welche Oberflächen gescannt wurden, sollte die Anwendung visuelles Feedback zu diesem Effekt bereitstellen. Beispielsweise kann das Werfen von virtuellen Schatten auf gescannte Oberflächen dem Benutzer helfen, Hologramme auf diesen Oberflächen zu platzieren.
   * In diesem Fall sollten die Begrenzungsvolumes des Raumoberflächenbeobachter jeden Frame in ein textgesperrte raumkoordinatensystem [aktualisieren,](coordinate-systems.md)damit sie dem Benutzer folgen.

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
   * Eine Anwendung erfordert möglicherweise eine Überprüfung aller Oberflächen im aktuellen Raum, einschließlich der Oberflächen hinter dem Benutzer.
   * Beispielsweise kann ein Spiel den Benutzer in die Rolle von Gulliver bringen, der von Hunderten von kleinen Lilliputians belagert wird, die sich aus allen Richtungen nähern.
   * In solchen Fällen muss die Anwendung bestimmen, wie viele Oberflächen im aktuellen Raum bereits gescannt wurden, und den Blick des Benutzers an sie richten, um erhebliche Lücken zu schließen.
   * Der Schlüssel zu diesem Prozess ist die Bereitstellung von visuellem Feedback, das dem Benutzer klar macht, welche Oberflächen noch nicht gescannt wurden. Die Anwendung könnte beispielsweise [](/windows/win32/direct3d9/fog-formulas) entfernungsbasierte Abstände verwenden, um Bereiche visuell hervorzuheben, die nicht von räumlichen Kartenoberflächen abgedeckt sind.

* **Erstellen einer Anfangsmomentaufnahme der Umgebung**
   * Eine Anwendung möchte möglicherweise alle Änderungen in der Umgebung ignorieren, nachdem eine erste Momentaufnahme erstellt wurde.
   * Dies kann geeignet sein, um eine Unterbrechung der vom Benutzer erstellten Daten zu vermeiden, die eng mit dem ursprünglichen Zustand der Umgebung gekoppelt sind.
   * In diesem Fall sollte die Anwendung nach Abschluss des Scans eine Kopie der Räumlichen Zuordnungsdaten im ursprünglichen Zustand erstellen.
   * Anwendungen sollten weiterhin Updates für räumliche Zuordnungsdaten erhalten, wenn Hologramme von der Umgebung immer noch ordnungsgemäß verblendet werden sollen.
   * Kontinuierliche Aktualisierungen der räumlichen Zuordnungsdaten ermöglichen auch die Visualisierung aller vorgenommenen Änderungen, um dem Benutzer die Unterschiede zwischen dem vorherigen und dem aktuellen Umgebungszuständen zu verdeutlichen.

* **Erstellen von vom Benutzer initiierten Momentaufnahmen der Umgebung**
   * Eine Anwendung möchte möglicherweise nur auf Umgebungsänderungen reagieren, wenn sie vom Benutzer angewiesen wird.
   * Beispielsweise könnte der Benutzer mehrere 3D-"3D-"3D-"3D-"3D-Bilder" eines Freundes erstellen, indem er seine Posen zu unterschiedlichen Zeitpunkten erfasst.

* **Zulassen, dass der Benutzer die Umgebung ändert**
   * Eine Anwendung kann so entworfen werden, dass sie in Echtzeit auf Änderungen reagiert, die in der Umgebung des Benutzers vorgenommen wurden.
   * Beispielsweise könnte der Benutzer, der einen Zeichner zieht, eine "Szenenänderung" für ein holografisches Spiel auslösen, das auf der anderen Seite stattfindet.

* **Anleitung für den Benutzer, um Fehler in den räumlichen Zuordnungsdaten zu vermeiden**
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
   * Lücken wirken sich auf Raycasts aus: Wenn Sie Raycasts verwenden, um Benutzern die Interaktion mit Oberflächen zu ermöglichen, ist es möglicherweise unerwünscht, dass diese Strahle Lücken passieren. Eine Lösung besteht in der Verwendung eines Bündels von mehreren Raycasts, die eine region mit entsprechender Größe abdecken. Auf diese Weise können Sie Die Ergebnisse von Ausreißern filtern, sodass das Aggregatergebnis auch dann gültig ist, wenn ein Raycast eine kleine Lücke durchläuft. Dieser Ansatz geht jedoch mit Rechenkosten eins ein.
   * Lücken wirken sich auf physikalische Kollisionen aus: Ein objekt, das von der Physikalischen Simulation gesteuert wird, kann durch eine Lücke im Boden fallen und verloren gehen.
   * Es ist möglich, solche Lücken im Oberflächengitter algorithmusisch zu füllen. Sie müssen ihren Algorithmus jedoch so optimieren, dass "echte Lücken" wie Fenster und Türtüren nicht ausgefüllt werden. Es kann schwierig sein, "echte Lücken" zuverlässig von "imaginären Lücken" zu unterscheiden, sodass Sie mit verschiedenen Heuristiken wie "Größe" und "Begrenzungsform" experimentieren müssen.

* **Halluzinationsentfernung**
   * Reflektionen, helles Licht und bewegende Objekte können kleine, nach wie vor "Halluzinationen" in der Luft gleiten lassen.
   * Halluzinationen wirken sich auf die Okklusion aus: Halluzinationen werden möglicherweise sichtbar, wenn sich dunkle Formen vor anderen Hologrammen bewegen und umschließen.
   * Halluzinationen wirken sich auf Raycasts aus: Wenn Sie Raycasts verwenden, um Benutzern die Interaktion mit Oberflächen zu ermöglichen, können diese Lichtstrahl eine Halluzination anstelle der Oberfläche darunter treffen. Wie bei Lücken besteht eine Entschärfung in der Verwendung vieler Raycasts anstelle eines einzelnen Raycasts. Dies wird jedoch auch hier zu Rechenkosten kommen.
   * Halluzinationen wirken sich auf physikalische Kollisionen aus: Ein objekt, das von der physikalischen Simulation gesteuert wird, kann an einer Halluzination hängen bleiben und kann sich nicht durch einen scheinbar klaren Raumbereich bewegen.
   * Es ist möglich, solche Halluzinationen aus dem Oberflächengitter zu filtern. Wie bei Lücken müssen Sie ihren Algorithmus jedoch so optimieren, dass echte kleine Objekte wie Lampe-Hänger und Türziehpunkte nicht entfernt werden.

* **Glättung**
   * Die räumliche Zuordnung kann Oberflächen zurückgeben, die im Vergleich zu ihren realen Entsprechungen grob oder "laut" zu sein scheinen.
   * Glättung wirkt sich auf physische Kollisionen aus: Wenn der Boden rau ist, rollt eine physisch simulierte Ballkugel möglicherweise nicht reibungslos auf einer geraden Linie darüber.
   * Glätte wirkt sich auf das Rendering aus: Wenn eine Oberfläche direkt visualisiert wird, können sich grobe Oberflächennorm normale Darstellungen auf die Darstellung auswirken und ein "sauberes" Aussehen beeinträchtigen. Es ist möglich, dies mithilfe der entsprechenden Beleuchtung und Texturen im Shader zu verringern, der zum Rendern der Oberfläche verwendet wird.
   * Es ist möglich, die Rauheit in einem Oberflächengitter zu glätten. Dadurch wird die Oberfläche jedoch möglicherweise weiter von der entsprechenden realen Oberfläche entfernt. Eine enge Entsprechung ist wichtig, um eine genaue Hologrammverschluss zu erzeugen und Benutzern zu ermöglichen, präzise und vorhersagbare Interaktionen mit holografischen Oberflächen zu erzielen.
   * Wenn nur eine gängige Änderung erforderlich ist, kann es ausreichen, die Scheitelpunktnorm normal zu glätten, ohne die Scheitelpunktpositionen zu ändern.

* **Ebenensuche**
   * Es gibt viele Formen der Analyse, die eine Anwendung möglicherweise auf den von der räumlichen Zuordnung bereitgestellten Oberflächen ausführen möchte.
   * Ein einfaches Beispiel ist "Plane Finding". Identifizieren von begrenzungsgebundenen, größtenteils planaren Oberflächen.
   * Planare Regionen können als holografische Arbeitsoberflächen verwendet werden, wobei holografische Inhalte von der Anwendung automatisch platziert werden können.
   * Planare Regionen können die Benutzeroberfläche einschränken, um Benutzer bei der Interaktion mit den Oberflächen zu unterstützen, die ihren Anforderungen am besten entsprechen.
   * Planare Regionen können wie in der realen Welt für holografische Entsprechungen zu funktionalen Objekten wie DISPLAY-Bildschirmen, Tabellen oder Whiteboards verwendet werden.
   * Planare Regionen können Spielbereiche definieren, die die Grundlage von Videospielebenen bilden.
   * Planare Regionen können virtuellen Agents helfen, durch die reale Welt zu navigieren, indem sie die Bereiche des Bodens identifizieren, auf denen echte Menschen wahrscheinlich weiter gehen werden.

## <a name="prototyping-and-debugging"></a>Prototyperstellung und Debuggen

### <a name="useful-tools"></a>Nützliche Tools

* Der [HoloLens-Emulator](../develop/platform-capabilities-and-apis/using-the-hololens-emulator.md) kann verwendet werden, um Anwendungen mit räumlicher Zuordnung ohne Zugriff auf eine physische HoloLens. Damit können Sie eine Livesitzung auf einer HoloLens in einer realistischen Umgebung mit allen Daten simulieren, die Ihre Anwendung normalerweise nutzen würde, einschließlich HoloLens-Bewegung, Raumkoordinatensystemen und Gitternetzen für räumliche Karten. Dies kann verwendet werden, um zuverlässige, wiederholbare Eingaben zu bieten, die für das Debuggen von Problemen und das Auswerten von Änderungen am Code nützlich sein können.
* Um ein Szenario zu reproduzieren, erfassen Sie daten der räumlichen Zuordnung über das Netzwerk von einem Live-HoloLens, speichern sie dann auf dem Datenträger und verwenden sie in späteren Debugsitzungen wieder.
* Die [Windows-Geräteportal-3D-Ansicht](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#3d-view) bietet eine Möglichkeit, alle räumlichen Oberflächen zu sehen, die derzeit über das Raumzuordnungssystem verfügbar sind. Dies ist eine Grundlage für den Vergleich der räumlichen Oberflächen in Ihrer Anwendung. Beispielsweise können Sie leicht erkennen, ob räumliche Oberflächen fehlen oder an der falschen Stelle angezeigt werden.

### <a name="general-prototyping-guidance"></a>Allgemeiner Leitfaden zur Prototyperstellung

* Da [Fehler](spatial-mapping.md#what-influences-spatial-mapping-quality) in den räumlichen Zuordnungsdaten die Benutzerfreundlichkeit stark beeinträchtigen können, wird empfohlen, ihre Anwendung in einer Vielzahl von Umgebungen zu testen.
* Lassen Sie sich nicht in der Angewohnheit verfangen, immer am gleichen Standort zu testen, z. B. an Ihrem Arbeitsplatz. Testen Sie unbedingt auf verschiedenen Oberflächen mit unterschiedlichen Positionen, Formen, Größen und Materialien.
* Auch wenn synthetische oder aufgezeichnete Daten für das Debuggen nützlich sein können, sind Sie nicht zu stark von denselben Testfällen abhängig. Dies kann die Suche nach wichtigen Problemen verzögern, die bei unterschiedlicheren Tests zuvor auft gewesen wären.
* Es ist eine gute Idee, Tests mit echten (und idealerweise nichtcoachierten) Benutzern durchzuführen, da sie die HoloLens oder Ihre Anwendung möglicherweise nicht auf die gleiche Weise wie Sie verwenden. Tatsächlich ist es vielleicht überraschend, wie unterschiedliche Verhaltensweisen, Kenntnisse und Annahmen von Menschen sein können!

## <a name="troubleshooting"></a>Problembehandlung

* Damit die Oberflächengitternetze ordnungsgemäß geerbt werden, muss jedes GameObject aktiv sein, bevor es an den SurfaceObserver gesendet wird, damit das Gitternetz erstellt wird. Andernfalls werden die Gitternetze in Ihrem Raum angezeigt, aber in schrägen Winkeln gedreht.
* Das GameObject, mit dem das Skript ausgeführt wird, das mit dem SurfaceObserver kommuniziert, muss auf den Ursprung festgelegt werden. Andernfalls haben alle GameObjects, die Sie erstellen und an den SurfaceObserver senden, um ihre Gitternetze zu erstellen, einen Offset, der dem Offset des übergeordneten Spielobjekts entspricht. Dies kann dazu sorgen, dass Ihre Gitternetze mehrere Meter entfernt werden, was das Debuggen der Daten erschwert.

## <a name="see-also"></a>Weitere Informationen

* [Koordinatensysteme](coordinate-systems.md)
* [Räumliche Abbildung in DirectX](../develop/native/spatial-mapping-in-directx.md)
* [Räumliche Abbildung in Unity](../develop/unity/spatial-mapping-in-unity.md)
* [Szenenverständnis](scene-understanding.md)
* [Raumabtastvisualisierung](room-scan-visualization.md)
* [Raumklangentwurf](spatial-sound-design.md)
* [Fallstudie – Schauen durch Löcher in Ihrer Realität](../out-of-scope/case-study-looking-through-holes-in-your-reality.md)