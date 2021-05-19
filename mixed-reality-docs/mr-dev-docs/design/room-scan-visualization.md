---
title: Raumabtastvisualisierung
description: Anwendungen, die eine räumliche Zuordnung erfordern, verwenden das Gerät, um Daten im Zeitverlauf und sitzungsübergreifend zu sammeln.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, App-Muster, Design, HoloLens, Raumscan, räumliche Zuordnung, Mesh, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens
ms.openlocfilehash: 8c7f1ae95cfdb520e84835f7fd5d78522e62e341
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143609"
---
# <a name="room-scan-visualization"></a>Raumabtastvisualisierung

Anwendungen, die eine räumliche Zuordnung erfordern, verlassen sich darauf, dass das Gerät Daten im Laufe der Zeit und sitzungsübergreifend sammelt. Die Vollständigkeit und Qualität der Zuordnungsdaten hängt von vielen Faktoren ab, einschließlich des Umfangs der Vom Benutzer durchgeführten Untersuchung, der Zeit, die seit der Untersuchung verstrichen ist, und davon, ob Objekte wie Türen und Türen seit dem Scannen des Bereichs durch das Gerät verschoben wurden.

Anwendungsentwickler haben mehrere Optionen, um nützliche räumliche Zuordnungsdaten sicherzustellen:
* Verlassen Sie sich auf das, was möglicherweise bereits gesammelt wurde. Diese Daten sind möglicherweise zunächst unvollständig.
* Bitten Sie den Benutzer, die Geste "Bloom" zu verwenden, um zum Windows Mixed Reality Startseite zu gelangen und dann den Bereich zu erkunden, den er für die Umgebung verwenden möchte. Sie können mithilfe von Tippen in die Luft bestätigen, dass dem Gerät der gesamte erforderliche Bereich bekannt ist.
* Erstellen einer benutzerdefinierten Untersuchungserfahrung in ihrer eigenen Anwendung

In all diesen Fällen werden die während der Untersuchung gesammelten Daten vom System gespeichert, und die Anwendung muss dies nicht tun. Wenn Sie die Raumscanvisualisierung in Aktion sehen möchten, sehen Sie sich die folgende Videodemo [zum Entwerfen von Hologrammen – Räumliche Wahrnehmung]() an:

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

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

Benutzer wissen nicht, was einen "guten" Scan ausmacht. Sie müssen angezeigt oder gefragt werden, was sie suchen sollten, wenn sie aufgefordert werden, einen Scan zu bewerten – Flachheit, Abstand von den tatsächlichen Wänden und so weiter. Der Entwickler sollte eine Feedbackschleife implementieren, die das Aktualisieren der Räumlichen Zuordnungsdaten während der Überprüfungs- oder Untersuchungsphase umfasst.

In vielen Fällen ist es am besten, den Benutzer darüber zu informieren, was er tun muss, um die erforderliche Scanqualität zu erhalten. Sehen Sie sich z. B. die Obergrenze an, sehen Sie sich hinter Gittern an, und so weiter.

## <a name="cached-versus-continuous-spatial-mapping"></a>Zwischengespeicherte und kontinuierliche räumliche Zuordnung

Die räumlichen Zuordnungsdaten sind die am stärksten gewichteten Datenquellenanwendungen, die verwendet werden können. Um Leistungsprobleme wie z. B. gelöschte Frames oder Dasttern zu vermeiden, sollte der Verbrauch dieser Daten sorgfältig erfolgen.

Das aktive Scannen während einer Erfahrung kann sowohl vorteilhaft als auch negativ sein, sodass Sie basierend auf der Erfahrung entscheiden müssen, welche Methode verwendet werden soll.

### <a name="cached-spatial-mapping"></a>Zwischengespeicherte räumliche Zuordnung

Wenn zwischengespeicherte räumliche Zuordnungsdaten vorhanden sind, erstellt die Anwendung in der Regel eine Momentaufnahme der Räumlichen Zuordnungsdaten und verwendet diese Momentaufnahme während der Erfahrung.

**Vorteile**
* Reduzierter Mehraufwand für das System, während die Erfahrung ausgeführt wird, was zu erheblichen Leistungssteigerungen, Wärme- und CPU-Leistungssteigerungen führt.
* Eine einfachere Implementierung der Haupterfahrung, da sie nicht durch Änderungen der räumlichen Daten unterbrochen wird.
* Ein einzelner einmaliger Kosten für jede Nachverarbeitung der räumlichen Daten für Physikalische, Grafiken und andere Zwecke.

**Nachteile**
* Die Bewegung realer Objekte oder Personen spiegelt sich nicht in den zwischengespeicherten Daten wider. Beispielsweise könnte die Anwendung eine türöffnend betrachten, wenn sie jetzt geschlossen ist.
* Möglicherweise mehr Anwendungsspeicher, um die zwischengespeicherte Version der Daten zu verwalten.

Ein guter Fall für diese Methode ist eine kontrollierte Umgebung oder ein Tabellenspiel.

### <a name="continuous-spatial-mapping"></a>Kontinuierliche räumliche Zuordnung

Bei bestimmten Anwendungen wird die Überprüfung möglicherweise fortgesetzt, um räumliche Zuordnungsdaten zu aktualisieren.

**Vorteile**
* Sie müssen keine separate Überprüfungs- oder Untersuchungserfahrung im Voraus in Ihrer Anwendung erstellen.
* Die Bewegung realer Objekte kann durch das Spiel widergespiegelt werden, allerdings mit einiger Verzögerung.

**Nachteile**
* Höhere Komplexität bei der Implementierung der Haupterfahrung.
* Potenzieller Mehraufwand durch die zusätzliche grafik- und physikalische Verarbeitung, da Änderungen inkrementell von diesen Systemen aufgenommen werden müssen.
* Höhere Leistung, wärmer und CPU-Auswirkungen.

Ein guter Fall für diese Methode ist, dass Hologramme mit bewegten Objekten interagieren sollen, z. B. ein holografisches Auto, das auf dem Boden fährt, je nachdem, ob es offen oder geschlossen ist, auf eine Tür stoßen möchte.

## <a name="see-also"></a>Siehe auch

* [Räumliche Abbildung](spatial-mapping.md)
* [Koordinatensysteme](coordinate-systems.md)
* [Raumklangentwurf](spatial-sound-design.md)