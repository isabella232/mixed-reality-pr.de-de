---
title: Anvisieren mit dem Kopf und Ausführen
description: Beginnen Sie mit dem Eingabemodell mit dem Anvisieren mit dem Kopf und dem Commit, einschließlich Zielsizing, Platzierung und Stabilität.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Mixed Reality, Anvisierten, Anvisierten, Interaktion, Design, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit, Ziel, Fokus, Glättung
ms.openlocfilehash: 641e403df23b2559429ca80aa06f384c4845ee347518adca2cfde1b3dbe874dd
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223658"
---
# <a name="head-gaze-and-commit"></a>Anvisieren mit dem Kopf und Ausführen

_Anvität mit dem Kopf_ und [](gaze-and-commit.md) Commit ist ein Sonderfall des Eingabemodells zum Anvieren und Commiten, bei dem ein Objekt mit der Kopfrichtung des Benutzer als Ziel verwendet wird. Sie können auf dem Ziel mit einer sekundären Eingabe agieren, z. B. dem Handgesten-Tippen in die Luft oder dem Sprachbefehl "Select". 

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

## <a name="head-and-eye-tracking-design-concepts-demo"></a>Demo der Entwurfskonzepte für Kopf- und Eyetracking

Wenn Sie die Entwurfskonzepte für Kopf- und Eyetracking in Aktion sehen möchten, sehen Sie sich unten unsere Videodemo **Entwerfen von Hologrammen: Kopf- und Eyetracking** an. Wenn Sie fertig sind, fahren Sie mit einem ausführlicheren Einblick in bestimmte Themen fort.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

*Dieses Video wurde aus der HoloLens 2-App „Entwerfen von Hologrammen“ aufgenommen. Laden Sie die vollständige Erfahrung [hier](https://aka.ms/dhapp) herunter, und genießen Sie sie.*

## <a name="target-sizing-and-feedback"></a>Skalieren von Zielen und Feedback

Der Anvisierungsvektor mit dem Kopf wurde wiederholt als für die Zieladressierung mit dem Kopf verwendet werden können, funktioniert aber häufig am besten für die Bruttozieladressierung – das Abrufen größerer Ziele. Minimale Zielgrößen von 1 grad bis 1,5 Grad ermöglichen erfolgreiche Benutzeraktionen in den meisten Szenarien, obwohl Ziele von 3 Grad häufig eine höhere Geschwindigkeit ermöglichen. Die Größe, auf die der Benutzer ausgerichtet ist, ist im Wesentlichen ein 2D-Bereich, auch für 3D-Elemente – die Projektion sollte der zielfähige Bereich sein. Es ist hilfreich, einen wichtigen Hinweis darauf zu geben, dass ein Element "aktiv" ist (dass der Benutzer es als Ziel hat). Dies kann z. B. sichtbare "Hover"-Effekte, Audiohighlights oder Klicks oder eine klare Ausrichtung eines Cursors mit einem Element umfassen.

![Optimale Zielgröße im Abstand von 2 Metern](images/gazetargeting-size-1000px.jpg)<br>
*Optimale Zielgröße bei 2-Meter-Entfernung*

<br>

![Beispiel für die Hervorhebung eines anvisierten Objekts](images/gazetargeting-highlighting-940px.jpg)<br>
*Beispiel für die Hervorhebung eines anvisierten Objekts*

## <a name="target-placement"></a>Zielpositionierung

Benutzer finden benutzeroberflächenelemente häufig nicht, die sich in ihrem Sichtfeld entweder zu hoch oder niedrig befinden. Die meiste Aufmerksamkeit liegt auf Bereichen um ihren Hauptfokus, die ungefähr auf Augenebene liegt. Die Positionierung der meisten Ziele in einem vernünftigen Bereich auf Augenhöhe kann helfen. Angesichts der Neigung der Benutzer, sich jederzeit auf einen relativ kleinen visuellen Bereich zu konzentrieren (der Visuelle Blickpunkt beträgt ungefähr 10 Grad), kann das Gruppieren von Benutzeroberflächenelementen in dem Maße, in dem sie konzeptionell verknüpft sind, Aufmerksamkeitsverkettungsverhalten von Element zu Element verwenden, wenn ein Benutzer seinen Anvisieren durch einen Bereich bewegt. Beachten Sie beim Entwerfen der Benutzeroberfläche die potenziellen großen Unterschiede beim Sichtfeld zwischen HoloLens und immersiven Headsets.

![Beispiel für gruppierte Benutzeroberflächenelemente zur einfacheren Zielbestimmung in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg).<br>
*Beispiel für gruppierte Benutzeroberflächenelemente zur einfacheren Zielbestimmung in Galaxy Explorer*.

## <a name="improving-targeting-behaviors"></a>Verbessern des Verhaltens bei der Zielbestimmung

Wenn die Absicht des Benutzers, etwas als Ziel zu verwenden, bestimmt oder näher bestimmt werden kann, kann es hilfreich sein, Interaktionsversuche mit nahezu einem Fehlschlag so zu akzeptieren, als ob sie ordnungsgemäß als Ziel verwendet würden. Hier sind einige erfolgreiche Methoden, die in Mixed Reality-Erfahrungen integriert werden können:

### <a name="head-gaze-stabilization-gravity-wells"></a>Stabilisierung beim Anvisieren mit dem Kopf („Gravitationsbrunnen“)

Dies sollte die meiste oder die ganze Zeit aktiviert sein. Durch diese Technik werden die natürlichen Kopf- und Jitter entfernt, die benutzer möglicherweise auch aufgrund des Aussehens und des Sprechverhaltens bewegen.

### <a name="closest-link-algorithms"></a>Algorithmen für die engste Verbindung

Diese Algorithmen funktionieren am besten in Bereichen mit wenig interaktiven Inhalten. Wenn die Wahrscheinlichkeit hoch ist, dass Sie bestimmen können, mit welchem Ziel ein Benutzer interagieren wollte, können Sie seine Zielfähigkeiten ergänzen, indem Sie eine bestimmte Absichtsstufe annehmen.

### <a name="backdating-and-postdating-actions"></a>Sichern und Postdieren von Aktionen

Dieser Mechanismus ist hilfreich bei Aufgaben, die Geschwindigkeit erfordern. Wenn sich ein Benutzer schnell durch eine Reihe von Ziel- und Aktivierungsaktivierungsaktivierungs-Aktivierungen bewegt, ist es hilfreich, eine Absicht anzunehmen. Es ist auch hilfreich, zu ermöglichen, dass verpasste Schritte auf Ziele wirken, die der Benutzer etwas vor oder etwas nach dem Tippen im Fokus hatte (50 ms vorher/nach war in frühen Tests wirksam).

### <a name="smoothing"></a>Glättung

Dieser Mechanismus ist nützlich für Pfadbewegungen, die das leichte Jittern und Wabbeln aufgrund natürlicher Kopfbewegungsmerkmale reduzieren. Glätten Sie beim Glätten über pfadende Bewegungen nicht im Laufe der Zeit, sondern durch die Größe und den Abstand der Bewegungen.

### <a name="magnetism"></a>Magnetismus

Dieser Mechanismus kann als eine allgemeinere Version der nächstgelegenen Verknüpfungsalgorithmen bezeichnet werden– das Zeichnen eines Cursors auf ein Ziel oder einfach das Erhöhen von Hitboxes, ob sichtbar oder nicht, da Benutzer wahrscheinliche Ziele erreichen, indem sie ein gewisses Wissen über das interaktive Layout verwenden, um die Benutzerabsicht besser zu erreichen. Dies kann für kleine Ziele leistungsfähiger sein.

### <a name="focus-stickiness"></a>Fokusbindung

Bei der Bestimmung, welchen interaktiven Elementen in der Nähe der Fokus zu geben ist, sorgt die Fokushaftigkeit für eine Verzerrung des Elements, das gerade fokussiert ist. Dies trägt dazu bei, das Verhalten bei einem erratischen Fokuswechsel zu reduzieren, wenn an einem Mittelpunkt zwischen zwei Elementen mit natürlichem Rauschen geschwebt wird.

## <a name="see-also"></a>Siehe auch

* [Augenbasierte Interaktion](eye-gaze-interaction.md)
* [Anvisieren und Verweilen](gaze-and-dwell.md)
* [Hände – Direkte Manipulation](direct-manipulation.md)
* [Hände – Gesten](gaze-and-commit.md#composite-gestures)
* [Hände – Zeigen und Ausführen](point-and-commit.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Spracheingabe](voice-input.md)