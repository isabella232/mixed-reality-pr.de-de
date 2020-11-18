---
title: Anvisieren mit dem Kopf und Ausführen
description: Übersicht über das Eingabemodell „Anvisieren mit dem Kopf und Ausführen“
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Gemischte Realität, Blick, Blick auf die Ausrichtung, Interaktion, Entwurf, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit, Ziel, Fokus, Glättung
ms.openlocfilehash: d913ac81e20962d38178223a050fdccfb51d8632
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702386"
---
# <a name="head-gaze-and-commit"></a>Anvisieren mit dem Kopf und Ausführen
Der _Kopf-und Commit-_ Vorgang ist ein Sonderfall des "Blick"- [und](gaze-and-commit.md) "Commit"-Eingabe Modells, bei dem ein Objekt mit der Richtung ihrer Kopfzeile (Head-Direction) als Ziel verwendet wird, und dann mit einer sekundären Eingabe, wie z. b. dem Luftbild der Handbewegung oder dem Sprachbefehl "Select", behandelt wird. 

## <a name="device-support"></a>Geräteunterstützung

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Eingabemodell</strong></td>
        <td><a href="../hololens-hardware-details.md"><strong>HoloLens (1. Generation)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></td>
    </tr>
     <tr>
        <td>Anvisieren mit dem Kopf und Ausführen</td>
        <td>✔️ Empfohlen</td>
        <td>✔️ Empfohlen (dritte Auswahl – <a href="interaction-fundamentals.md">Siehe andere Optionen</a>)</td>
        <td>➕ Alternative Option</td>
    </tr>
</table>

---

## <a name="target-sizing-and-feedback"></a>Skalieren von Zielen und Feedback
Der Kopf Zeilenvektor wurde wiederholt angezeigt, um für die fein Ausrichtung geeignet zu sein. er eignet sich jedoch oft am besten für das erreichen von Brutto Zuweisungs zugriffung. Die minimalen Zielgrößen von 1 bis 1,5 Grad ermöglichen in den meisten Szenarien erfolgreiche Benutzeraktionen, obwohl Ziele von 3 Grad häufig eine höhere Geschwindigkeit ermöglichen. Beachten Sie, dass die Größe, auf die der Benutzer ausgerichtet ist, auch für 3D-Elemente effektiv ein 2D-Bereich ist. Die ihm jeweils zugewandte Projektion sollte der Zielbereich sein. Ein Hinweis darauf, dass ein Element "aktiv" ist (der der Benutzer als Ziel verwendet), ist äußerst hilfreich. Dies kann z. b. z. b. sichtbare "Hover"-Effekte, audiohighlights oder Klicks oder eine klare Ausrichtung eines Cursors mit einem Element umfassen.

![Optimale Zielgröße im Abstand von 2 Metern](images/gazetargeting-size-1000px.jpg)<br>
*Optimale Zielgröße im Abstand von 2 Metern*

<br>

![Beispiel für die Hervorhebung eines anvisierten Objekts](images/gazetargeting-highlighting-940px.jpg)<br>
*Beispiel für die Hervorhebung eines anvisierten Objekts*

## <a name="target-placement"></a>Zielpositionierung
Benutzer können häufig keine UI-Elemente finden, die in ihrer Ansicht sehr hoch oder sehr niedrig angeordnet sind. Sie konzentrieren sich auf Bereiche, die sich in der Nähe des Hauptfokus befinden, also ungefähr in der Perspektive. Die Positionierung der meisten Ziele in einem vernünftigen Bereich auf Augenhöhe kann helfen. Angesichts der Tendenz, dass sich der Benutzer jeweils auf einen relativ kleinen visuellen Bereich konzentrieren kann (der Blickwinkel beträgt etwa 10 Grad), kann die Gruppierung von Benutzeroberflächenelementen in dem Maße, in dem sie konzeptionell verwandt sind, das Verhalten zum Kombinieren der Aufmerksamkeit von Element zu Element nutzen, wenn der Blick eines Benutzers durch einen Bereich schweift. Beachten Sie beim Entwerfen der Benutzeroberfläche die potenziellen großen Unterschiede beim Sichtfeld zwischen HoloLens und immersiven Headsets.

![Beispiel für gruppierte Benutzeroberflächenelemente zur einfacheren Zielbestimmung in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg).<br>
*Beispiel für gruppierte Benutzeroberflächenelemente zur einfacheren Zielbestimmung in Galaxy Explorer*.

## <a name="improving-targeting-behaviors"></a>Verbessern des Verhaltens bei der Zielbestimmung
Wenn der Benutzer beabsichtigt ist, etwas als Ziel festzustellen, kann es sehr hilfreich sein, fast Fehlversuche bei der Interaktion zu akzeptieren, als wären Sie ordnungsgemäß als Ziel festgelegt. Im folgenden finden Sie eine Reihe von erfolgreichen Methoden, die in gemischte Realität integriert werden können:

### <a name="head-gaze-stabilization-gravity-wells"></a>Stabilisierung beim Anvisieren mit dem Kopf („Gravitationsbrunnen“)
Dies sollte in den meisten Fällen oder in der Zeit aktiviert werden. Diese Methode entfernt die natürlichen Kopf-und Hals Jitter, die Benutzer möglicherweise durch das Aussehen und Sprech Verhalten durchsuchen.

### <a name="closest-link-algorithms"></a>Algorithmen für die engste Verbindung
Diese funktionieren am besten in Bereichen mit wenig interaktiven Inhalten. Wenn eine hohe Wahrscheinlichkeit besteht, dass Sie bestimmen können, mit welchem Benutzer versucht wurde, zu interagieren, können Sie die Zielfunktionen ergänzen, indem Sie eine gewisse Absicht annehmen.

### <a name="backdating-and-postdating-actions"></a>Sicherungs-und postdating-Aktionen
Dieser Mechanismus ist hilfreich bei Aufgaben, die Geschwindigkeit erfordern. Wenn ein Benutzer mit der Geschwindigkeit eine Reihe von Ziel-und Aktivierungs Manövern durchläuft, ist es sinnvoll, eine Absicht anzunehmen und versäumte Schritte zuzulassen, um auf Ziele zu reagieren, auf die sich der Benutzer vor oder nach dem tippen etwas bewegt hat (50 ms vor/nach war in frühen Tests wirksam).

### <a name="smoothing"></a>Glättung
Dieser Mechanismus eignet sich für die Bewegung von bewegungsbewegungen, wodurch das leichte Jitter und das Wackeln aufgrund natürlicher Kopf Verschiebungs Merkmale reduziert werden. Bei der Glättung von bewegungsbewegungen durch die Größe und die Entfernung von Bewegungen und nicht über die Zeit.

### <a name="magnetism"></a>Magnetismus
Dieser Mechanismus kann sich als allgemeinere Version der nächstgelegenen Verknüpfungs Algorithmen vorstellen: das Zeichnen eines Cursors in Richtung eines Ziels oder das einfache erhöhen der Treffer Felder, egal ob sichtbar oder nicht, wenn Benutzer wahrscheinliche Ziele erreichen, indem Sie einige Kenntnisse des interaktiven Layouts verwenden, um die Benutzer Absicht besser zu betrachten. Dies kann insbesondere bei kleinen Zielen sehr wirkungsvoll sein.

### <a name="focus-stickiness"></a>Fokusbindung
Wenn Sie bestimmen, auf welche nahe gelegenen interaktiven Elemente der Fokus gelegt werden soll, stellt die Fokus Bindung eine Abweichung für das Element bereit, das momentan fokussiert ist. Dies trägt dazu bei, das Verhalten von erratischen Fokus Wechselverhalten zu verringern, wenn Sie in einem Mittelpunkt zwischen zwei Elementen mit natürlichem Rauschen schweben


## <a name="see-also"></a>Siehe auch
* [Augenbasierte Interaktion](eye-gaze-interaction.md)
* [Anvisieren und Verweilen](gaze-and-dwell.md)
* [Hände – Direkte Manipulation](direct-manipulation.md)
* [Hände – Gesten](gaze-and-commit.md#composite-gestures)
* [Hände – Zeigen und Ausführen](point-and-commit.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Spracheingabe](voice-input.md)



