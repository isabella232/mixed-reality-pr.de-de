---
title: Raumabtastvisualisierung
description: Anwendungen, die eine räumliche Zuordnung erfordern, verwenden das Gerät, um Daten im Zeitverlauf und sitzungsübergreifend zu sammeln.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, App-Muster, Entwurf, HoloLens, Raumscan, räumliche Zuordnung, Gitternetz, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens
ms.openlocfilehash: 0ebfbd9a1f07ffd0671d36dcc63dbd5303a2cdbceb906839be9736f43de76937
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207828"
---
# <a name="room-scan-visualization"></a>Raumabtastvisualisierung

Anwendungen, die eine räumliche Zuordnung erfordern, verlassen sich darauf, dass das Gerät Daten im Laufe der Zeit und sitzungsübergreifend sammelt. Die Vollständigkeit und Qualität der Zuordnungsdaten hängt von vielen Faktoren ab, einschließlich des Umfangs der Vom Benutzer durchgeführten Untersuchung, der Zeit, die seit der Untersuchung verstrichen ist, und davon, ob Objekte wie Türen und Türen seit dem Scannen des Bereichs durch das Gerät verschoben wurden.

Anwendungsentwickler haben mehrere Optionen, um nützliche räumliche Zuordnungsdaten sicherzustellen:
* Verlassen Sie sich auf das, was möglicherweise bereits gesammelt wurde. Diese Daten sind möglicherweise zunächst unvollständig.
* Bitten Sie den Benutzer, die Geste "Bloom" zu verwenden, um zum Windows Mixed Reality Startseite zu gelangen und dann den Bereich zu erkunden, den er für die Umgebung verwenden möchte. Sie können mithilfe von Tippen in die Luft bestätigen, dass dem Gerät der gesamte erforderliche Bereich bekannt ist.
* Erstellen Sie eine benutzerdefinierte Erkundungserfahrung in ihrer eigenen Anwendung.

In all diesen Fällen werden die während der Untersuchung gesammelten Daten vom System gespeichert, und die Anwendung muss dies nicht tun. Wenn Sie die Raumscanvisualisierung in Aktion sehen möchten, sehen Sie sich die folgende Videodemo **zum Entwerfen Hologramme – Räumliche Wahrnehmung** an:

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

*Dieses Video wurde aus der HoloLens 2-App „Entwerfen von Hologrammen“ aufgenommen. Laden Sie die vollständige Erfahrung [hier](https://aka.ms/dhapp) herunter, und genießen Sie sie.*

## <a name="device-support"></a>Geräteunterstützung

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Feature</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Raumabtastvisualisierung</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="building-a-custom-scanning-experience"></a>Erstellen einer benutzerdefinierten Überprüfungserfahrung

Anwendungen können die räumlichen Zuordnungsdaten zu Beginn der Benutzeroberfläche analysieren, um zu beurteilen, ob der Benutzer zusätzliche Schritte ausführen soll, um seine Vollständigkeit und Qualität zu verbessern. Wenn die Analyse angibt, dass die Qualität verbessert werden sollte, sollten Entwickler eine Visualisierung zur Überlagerung auf der Welt bereitstellen, um Folgendes anzugeben:
* Wie viel des Gesamtvolumens in der Benutzerumgebung muss Teil der Benutzeroberfläche sein?
* Ort, an dem der Benutzer Daten verbessern soll

Benutzer wissen nicht, was einen "guten" Scan ausmacht. Sie müssen angezeigt oder informiert werden, wonach sie suchen müssen, wenn sie aufgefordert werden, einen Scan auszuwerten – Flachkeit, Abstand von tatsächlichen Wänden usw. Der Entwickler sollte eine Feedbackschleife implementieren, die das Aktualisieren der räumlichen Zuordnungsdaten während der Überprüfungs- oder Untersuchungsphase einschließt.

In vielen Fällen ist es am besten, dem Benutzer mitzuteilen, was er tun muss, um die erforderliche Scanqualität zu erhalten. Sehen Sie sich z. B. die Obergrenze an, sehen Sie sich die Hintergründe an, und so weiter.

## <a name="cached-versus-continuous-spatial-mapping"></a>Zwischengespeicherte und kontinuierliche räumliche Zuordnung

Die räumlichen Zuordnungsdaten sind die datenquellenanwendungen mit der höchsten Gewichtung, die sie nutzen können. Um Leistungsprobleme wie gelöschte Frames oder Stuttern zu vermeiden, sollte die Nutzung dieser Daten sorgfältig durchgeführt werden.

Aktive Überprüfungen während einer Benutzeroberfläche können sowohl vorteilhaft als auch schädlich sein, sodass Sie basierend auf der Benutzeroberfläche entscheiden müssen, welche Methode verwendet werden soll.

### <a name="cached-spatial-mapping"></a>Zwischengespeicherte räumliche Zuordnung

Wenn zwischengespeicherte räumliche Zuordnungsdaten vorhanden sind, erstellt die Anwendung in der Regel eine Momentaufnahme der räumlichen Zuordnungsdaten und verwendet diese Momentaufnahme während der Benutzeroberfläche.

**Vorteile**
* Reduzierter Mehraufwand für das System, während die Benutzeroberfläche ausgeführt wird, was zu erheblichen Leistungssteigerungen bei Leistung, Wärme und CPU führt.
* Eine einfachere Implementierung der Haupterfahrung, da sie nicht durch Änderungen in den räumlichen Daten unterbrochen wird.
* Einmalige Kosten für jede Nachverarbeitung der räumlichen Daten zu Physikalischen, Grafik- und anderen Zwecken.

**Nachteile**
* Die Bewegung von realen Objekten oder Personen wird nicht durch die zwischengespeicherten Daten widergespiegelt. Beispielsweise kann die Anwendung eine türöffnend betrachten, wenn sie jetzt geschlossen wird.
* Potenziell mehr Anwendungsspeicher, um die zwischengespeicherte Version der Daten beizubehalten.

Ein guter Fall für diese Methode ist eine kontrollierte Umgebung oder ein Tabellen-Top-Spiel.

### <a name="continuous-spatial-mapping"></a>Kontinuierliche räumliche Zuordnung

Bestimmte Anwendungen können sich auf die fortgesetzte Überprüfung verlassen, um räumliche Zuordnungsdaten zu aktualisieren.

**Vorteile**
* Sie müssen keine separate Überprüfungs- oder Untersuchungserfahrung im Voraus in Ihrer Anwendung erstellen.
* Die Bewegung realer Objekte kann vom Spiel reflektiert werden, allerdings mit etwas Verzögerung.

**Nachteile**
* Höhere Komplexität bei der Implementierung der Haupterfahrung.
* Potenzieller Mehraufwand durch die zusätzliche grafik- und physikalische Verarbeitung, da Änderungen inkrementell von diesen Systemen erfasst werden müssen.
* Höhere Auswirkungen auf Leistung, Wärme und CPU.

Ein guter Fall für diese Methode ist ein Fall, bei dem Hologramme mit bewegten Objekten interagieren sollen, z. B. ein holografisches Auto, das im Boden fährt, möglicherweise in eine Tür stoßen soll, je nachdem, ob es offen oder geschlossen ist.

## <a name="see-also"></a>Siehe auch

* [Räumliche Abbildung](spatial-mapping.md)
* [Koordinatensysteme](coordinate-systems.md)
* [Raumklangentwurf](spatial-sound-design.md)