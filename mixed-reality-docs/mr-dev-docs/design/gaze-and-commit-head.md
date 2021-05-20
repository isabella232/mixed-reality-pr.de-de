---
title: Anvisieren mit dem Kopf und Ausführen
description: Beginnen Sie mit dem Eingabemodell mit dem Anvisieren mit dem Kopf und dem Commit, einschließlich Zielsizing, Platzierung und Stabilität.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Mixed Reality, Anvisierten, Anvisierten, Interaktion, Design, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit, Ziel, Fokus, Glättung
ms.openlocfilehash: 74f963a6b450d1fb7f1302886a01c12cf79ce28a
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196515"
---
# <a name="head-gaze-and-commit"></a>Anvisieren mit dem Kopf und Ausführen

_Anvität mit dem Kopf_ und [](gaze-and-commit.md) Commit ist ein Sonderfall des Eingabemodells zum Anvieren und Commiten, bei dem ein Objekt mit der Kopfrichtung des Benutzer als Ziel verwendet wird. Sie können auf das Ziel mit einer sekundären Eingabe wie dem Tippen auf die Handgestenbewegung oder dem Sprachbefehl "Select" (Auswählen) agieren. 

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
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1. Generation)</strong></a></td>
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

## <a name="head-and-eye-tracking-design-concepts-demo"></a>Demo zu Designkonzepten für Kopf- und Blickverfolgung

Wenn Sie die Designkonzepte für Kopf- und Blickverfolgung in Aktion sehen möchten, sehen Sie sich die Videodemo **Designing Holograms - Head Tracking and Eye Tracking** (Entwerfen von Hologrammen – Kopfverfolgung und Eyetracking) weiter unten an. Wenn Sie fertig sind, fahren Sie fort, um ausführlichere Informationen zu bestimmten Themen zu erhalten.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

*Dieses Video wurde aus der App "Entwerfen von Hologrammen" HoloLens 2 aufgenommen. Laden Sie hier herunter, und profitieren Sie [von der vollständigen Erfahrung.](https://aka.ms/dhapp)*

## <a name="target-sizing-and-feedback"></a>Skalieren von Zielen und Feedback

Der Anvisierungsvektor mit dem Kopf wurde wiederholt als für die Zieladressierung verwendet werden können, funktioniert aber häufig am besten für die Bruttozieladressierung – das Abrufen größerer Ziele. Minimale Zielgrößen von 1 bis 1,5 Grad ermöglichen in den meisten Szenarien erfolgreiche Benutzeraktionen, obwohl Ziele von 3 Grad häufig eine höhere Geschwindigkeit ermöglichen. Die Größe, auf die der Benutzer ausgerichtet ist, ist im Wesentlichen ein 2D-Bereich, auch für 3D-Elemente – die Projektion, auf die sie ausgerichtet sind, sollte der zielfähige Bereich sein. Es ist hilfreich, einen wichtigen Hinweis darauf zu geben, dass ein Element "aktiv" ist (dass der Benutzer es als Ziel hat). Dies kann z. B. sichtbare "Hover"-Effekte, Audiohighlights oder Klicks oder eine klare Ausrichtung eines Cursors mit einem Element umfassen.

![Optimale Zielgröße im Abstand von 2 Metern](images/gazetargeting-size-1000px.jpg)<br>
*Optimale Zielgröße bei 2-Meter-Entfernung*

<br>

![Beispiel für die Hervorhebung eines anvisierten Objekts](images/gazetargeting-highlighting-940px.jpg)<br>
*Beispiel für die Hervorhebung eines anvisierten Objekts*

## <a name="target-placement"></a>Zielpositionierung

Benutzer finden benutzeroberflächenelemente häufig nicht, die sich in ihrem Sichtfeld entweder zu hoch oder niedrig befinden. Die meiste Aufmerksamkeit liegt auf Bereichen um ihren Hauptfokus, die ungefähr auf Augenebene liegt. Die Positionierung der meisten Ziele in einem vernünftigen Bereich auf Augenhöhe kann helfen. Angesichts der Tatsache, dass Benutzer sich jederzeit auf einen relativ kleinen visuellen Bereich konzentrieren (der Aufmerksamkeitskegel des Sehens beträgt ungefähr 10 Grad), kann das Gruppieren von Ui-Elementen in dem Maße, in dem sie konzeptionell miteinander verknüpft sind, Aufmerksamkeitsverkettungsverhalten von Element zu Element verwenden, während ein Benutzer den Blick durch einen Bereich bewegt. Beachten Sie beim Entwerfen der Benutzeroberfläche die potenziellen großen Unterschiede beim Sichtfeld zwischen HoloLens und immersiven Headsets.

![Beispiel für gruppierte Benutzeroberflächenelemente zur einfacheren Zielbestimmung in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg).<br>
*Beispiel für gruppierte Benutzeroberflächenelemente zur einfacheren Zielbestimmung in Galaxy Explorer*.

## <a name="improving-targeting-behaviors"></a>Verbessern des Verhaltens bei der Zielbestimmung

Wenn die Absicht des Benutzers, auf etwas abzuzielen, bestimmt oder eng angenähert werden kann, kann es hilfreich sein, Interaktionsversuche nahezu ausgelassen zu akzeptieren, als wären sie korrekt ausgerichtet. Hier sind einige erfolgreiche Methoden, die in Mixed Reality-Erfahrungen integriert werden können:

### <a name="head-gaze-stabilization-gravity-wells"></a>Stabilisierung beim Anvisieren mit dem Kopf („Gravitationsbrunnen“)

Dies sollte die meiste Zeit oder die ganze Zeit aktiviert sein. Mit dieser Technik werden die natürlichen Kopf- und Sprechbewegungen entfernt, die Benutzer aufgrund des Aussehens und Sprechverhaltens möglicherweise haben.

### <a name="closest-link-algorithms"></a>Algorithmen für die engste Verbindung

Diese Algorithmen funktionieren am besten in Bereichen mit wenig interaktivem Inhalt. Wenn es eine hohe Wahrscheinlichkeit gibt, dass Sie bestimmen können, mit welchem Benutzer versucht wurde, zu interagieren, können Sie seine Zielfähigkeiten ergänzen, indem Sie ein gewisses Maß an Absicht annehmen.

### <a name="backdating-and-postdating-actions"></a>Backdating- und Postdating-Aktionen

Dieser Mechanismus ist hilfreich bei Aufgaben, die Geschwindigkeit erfordern. Wenn ein Benutzer eine Reihe von Ziel- und Aktivierungsreaktivierungen schnell durchgeht, ist es hilfreich, eine Absicht anzunehmen. Es ist auch hilfreich, verpasste Schritte zuzulassen, um auf Ziele zu reagieren, die der Benutzer vor oder nach dem Tippen leicht im Fokus hatte (50 ms vorher/nach waren in frühen Tests wirksam).

### <a name="smoothing"></a>Glättung

Dieser Mechanismus ist nützlich für das Verschieben von Bewegungen, wodurch das leichte Jittern und Wackeln aufgrund natürlicher Kopfbewegungsmerkmale reduziert wird. Beim Glätten über Pfadbewegungen, glätten Sie nach Größe und Entfernung von Bewegungen und nicht im Laufe der Zeit.

### <a name="magnetism"></a>Magnetismus

Dieser Mechanismus kann als allgemeinere Version von Algorithmen für nahe bezogene Verknüpfungen bezeichnet werden– das Zeichnen eines Cursors in Richtung eines Ziels oder das einfache Erhöhen von Trefferboxen, ob sichtbar oder nicht, da Benutzer wahrscheinliche Ziele nähern, indem sie ein gewisses Wissen über das interaktive Layout verwenden, um die Benutzerabsicht besser zu erreichen. Dies kann für kleine Ziele leistungsfähig sein.

### <a name="focus-stickiness"></a>Fokusbindung

Bei der Bestimmung, welchen interaktiven Elementen in der Nähe der Fokus zu geben ist, sorgt die Fokushaftigkeit für eine Verzerrung des Elements, das gerade fokussiert ist. Dies trägt dazu bei, das Verhalten bei einem erratischen Fokuswechsel zu reduzieren, wenn das Gleiten an einem Mittelpunkt zwischen zwei Elementen mit natürlichem Rauschen vor sich geht.

## <a name="see-also"></a>Weitere Informationen

* [Augenbasierte Interaktion](eye-gaze-interaction.md)
* [Anvisieren und Verweilen](gaze-and-dwell.md)
* [Hände – Direkte Manipulation](direct-manipulation.md)
* [Hände – Gesten](gaze-and-commit.md#composite-gestures)
* [Hände – Zeigen und Ausführen](point-and-commit.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Spracheingabe](voice-input.md)