---
title: Raumabtastvisualisierung
description: Anwendungen, die eine räumliche Zuordnung erfordern, verwenden das Gerät, um Daten im Laufe der Zeit und sitzungsübergreifend zu sammeln.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, App-Muster, Design, HoloLens, Raumscan, räumliche Abbildung, Gitter, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens
ms.openlocfilehash: 87312a5d5361ac0e8c24a622cf69fe3e9b147ff5
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196405"
---
# <a name="room-scan-visualization"></a>Raumabtastvisualisierung

Anwendungen, die räumliche Zuordnung erfordern, verlassen sich darauf, dass das Gerät Daten im Zeit- und sitzungsübergreifenden Zeitraum sammelt. Die Vollständigkeit und Qualität der Zuordnungsdaten hängt von vielen Faktoren ab, z. B. dem Umfang der Untersuchung durch den Benutzer, der Verstrichenheit seit der Untersuchung und davon, ob Objekte wie Hänge und Türen seit dem Scannen des Bereichs durch das Gerät verschoben wurden.

Um nützliche räumliche Zuordnungsdaten sicherzustellen, haben Anwendungsentwickler mehrere Optionen:
* Verlassen Sie sich darauf, was möglicherweise bereits erfasst wurde. Diese Daten sind möglicherweise anfänglich unvollständig.
* Bitten Sie den Benutzer, die Blumengeste zu verwenden, um zum Haus Windows Mixed Reality zu kommen und dann den Bereich zu erkunden, den er für die Benutzeroberfläche verwenden möchte. Sie können mithilfe von Tippen in die Luft bestätigen, dass dem Gerät alle erforderlichen Flächen bekannt sind.
* Erstellen Sie eine benutzerdefinierte Erkundungserfahrung in ihrer eigenen Anwendung.

In all diesen Fällen werden die tatsächlichen Daten, die während der Untersuchung gesammelt werden, vom System gespeichert, und die Anwendung muss dies nicht tun. Wenn Sie die Raumscanvisualisierung in Aktion sehen möchten, sehen Sie sich unsere Videodemo **Designing Holograms - Spatial Awareness** (Entwerfen von Hologrammen – räumliche Wahrnehmung) weiter unten an:

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

*Dieses Video wurde aus der App "Entwerfen von Hologrammen" HoloLens 2 aufgenommen. Laden Sie hier herunter, und profitieren Sie [von der vollständigen Erfahrung.](https://aka.ms/dhapp)*

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

Anwendungen können die räumlichen Zuordnungsdaten zu Beginn der Benutzeroberfläche analysieren, um zu beurteilen, ob der Benutzer zusätzliche Schritte ausführen soll, um seine Vollständigkeit und Qualität zu verbessern. Wenn die Analyse darauf hindeutet, dass die Qualität verbessert werden sollte, sollten Entwickler eine Visualisierung bereitstellen, die der Welt überlagert werden soll, um Anzugeben:
* Wie viel des Gesamtvolumens in der Umgebung der Benutzer muss teil der Erfahrung sein?
* Wo sollte der Benutzer die Daten verbessern?

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
* Die Bewegung von realen Objekten oder Personen wird nicht durch die zwischengespeicherten Daten widergespiegelt. Beispielsweise könnte die Anwendung eine Tür öffnen, wenn sie jetzt geschlossen wird.
* Potenziell mehr Anwendungsspeicher, um die zwischengespeicherte Version der Daten zu verwalten.

Ein guter Fall für diese Methode ist eine kontrollierte Umgebung oder ein Tabellen-Top-Spiel.

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