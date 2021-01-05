---
title: Anvisieren mit dem Kopf und Ausführen
description: Übersicht über das Head-und Commit-Eingabe Modell.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Gemischte Realität, Blick, Blick auf die Ausrichtung, Interaktion, Entwurf, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit, Ziel, Fokus, Glättung
ms.openlocfilehash: cc12c349704a63c5b95c9eede91d0486f56787a2
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847886"
---
# <a name="head-gaze-and-commit"></a>Anvisieren mit dem Kopf und Ausführen

Der _Kopf-und Commit-_ Vorgang ist ein Sonderfall des "Blick"- [und](gaze-and-commit.md) "Commit"-Eingabe Modells, bei dem ein Objekt mit der Benutzer Kopfzeile verwendet wird. Sie können das Ziel mit einer sekundären Eingabe, wie z. b. dem Befehl "Handbewegung Air Tap" oder "Select", für das Ziel handeln. 

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

Der Kopf Zeilenvektor wurde wiederholt angezeigt, um für die fein Ausrichtung geeignet zu sein. er eignet sich jedoch oft am besten für das anvisieren von größeren Zielen. Die minimalen Zielgrößen von 1 Grad bis 1,5 Grad ermöglichen in den meisten Szenarien erfolgreiche Benutzeraktionen, obwohl Ziele von 3 Grad häufig eine höhere Geschwindigkeit ermöglichen. Die Größe, auf die der Benutzer ausgerichtet ist, ist tatsächlich ein 2D-Bereich, auch bei 3D-Elementen, und die Projektion, mit der er konfrontiert ist, sollte der Zielbereich sein. Das Bereitstellen eines hervorragenden Anweisungs Elements, dass ein Element "aktiv" ist (das der Benutzer als Ziel verwendet), ist hilfreich. Dies kann z. b. z. b. sichtbare "Hover"-Effekte, audiohighlights oder Klicks oder eine klare Ausrichtung eines Cursors mit einem Element umfassen.

![Optimale Zielgröße im Abstand von 2 Metern](images/gazetargeting-size-1000px.jpg)<br>
*Optimale Zielgröße bei 2-Meter-Entfernung*

<br>

![Beispiel für die Hervorhebung eines anvisierten Objekts](images/gazetargeting-highlighting-940px.jpg)<br>
*Beispiel für die Hervorhebung eines anvisierten Objekts*

## <a name="target-placement"></a>Zielpositionierung

Benutzer können häufig keine Benutzeroberflächen Elemente finden, die sich entweder zu hoch oder zu niedrig im Sichtfeld befinden. Der größte Teil ihrer Aufmerksamkeit liegt am Ende der Bereiche, die sich in der Nähe des Hauptfokus befinden. Die Positionierung der meisten Ziele in einem vernünftigen Bereich auf Augenhöhe kann helfen. Angesichts der Tendenz, dass sich Benutzer jederzeit auf einen relativ kleinen visuellen Bereich konzentrieren können (der Teilnehmer ist ungefähr 10 Grad), kann das Gruppieren von Benutzeroberflächen Elementen zu dem Grad, den Sie konzeptionell verknüpft haben, das Verhalten der Aufmerksamkeit Verkettung von Item zu Item verwenden, wenn ein Benutzer den Blick durch einen Bereich verschiebt. Beachten Sie beim Entwerfen der Benutzeroberfläche die potenziellen großen Unterschiede beim Sichtfeld zwischen HoloLens und immersiven Headsets.

![Beispiel für gruppierte Benutzeroberflächenelemente zur einfacheren Zielbestimmung in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg).<br>
*Beispiel für gruppierte Benutzeroberflächenelemente zur einfacheren Zielbestimmung in Galaxy Explorer*.

## <a name="improving-targeting-behaviors"></a>Verbessern des Verhaltens bei der Zielbestimmung

Wenn der Benutzer beabsichtigt ist, etwas zu erreichen, kann es hilfreich sein, und es kann hilfreich sein, die Near-Fehler Interaktion zu akzeptieren, als ob Sie ordnungsgemäß als Ziel festgelegt wurden. Hier sind einige der erfolgreichen Methoden, die in gemischte Realität integriert werden können:

### <a name="head-gaze-stabilization-gravity-wells"></a>Stabilisierung beim Anvisieren mit dem Kopf („Gravitationsbrunnen“)

Dies sollte in den meisten Fällen oder in der Zeit aktiviert werden. Durch diese Vorgehensweise werden die natürlichen Kopf-und Hals jittoren entfernt, die Benutzer möglicherweise auch aufgrund der Betrachtung und des Sprech Verhaltens Verhalten haben.

### <a name="closest-link-algorithms"></a>Algorithmen für die engste Verbindung

Diese Algorithmen funktionieren am besten in Bereichen mit interaktiven Inhalten mit geringer Dichte. Wenn eine hohe Wahrscheinlichkeit besteht, dass Sie bestimmen können, mit welchem Benutzer Sie interagieren wollten, können Sie die Ziel Fähigkeiten ergänzen, indem Sie eine gewisse Absicht annehmen.

### <a name="backdating-and-postdating-actions"></a>Sicherungs-und postdating-Aktionen

Dieser Mechanismus ist hilfreich bei Aufgaben, die Geschwindigkeit erfordern. Wenn ein Benutzer mit der Geschwindigkeit eine Reihe von Ziel-und Aktivierungs Manövern durchläuft, ist es sinnvoll, eine beabsichtigte Absicht anzunehmen. Außerdem ist es hilfreich, die Ausführung von versäumten Schritten für Ziele zu ermöglichen, auf die sich der Benutzer vor oder nach dem tippen etwas ausgewirkt hat (50 ms vor/nach war in frühen Tests wirksam).

### <a name="smoothing"></a>Glättung

Dieser Mechanismus ist nützlich für die Bewegung von Bewegungen und reduziert die leichte Jitter und wackeln aufgrund natürlicher Kopf Verschiebungs Merkmale. Bei der Glättung von bewegungsbewegungen durch die Größe und die Entfernung von Bewegungen und nicht über die Zeit.

### <a name="magnetism"></a>Magnetismus

Dieser Mechanismus kann sich als allgemeinere Version der nächstgelegenen Verknüpfungs Algorithmen vorstellen: das Zeichnen eines Cursors in Richtung eines Ziels oder das einfache erhöhen der Treffer Felder, egal ob sichtbar oder nicht, wenn Benutzer wahrscheinliche Ziele erreichen, indem Sie einige Kenntnisse des interaktiven Layouts verwenden, um die Benutzer Absicht besser zu betrachten. Dies kann für kleine Ziele leistungsstark sein.

### <a name="focus-stickiness"></a>Fokusbindung

Wenn Sie bestimmen, welche interaktiven Elemente in der Nähe bereitgestellt werden sollen, wird der Fokus auf festgelegt, und der Fokus ist für das Element, das derzeit fokussiert ist. Dies trägt dazu bei, das Verhalten von erratischen Fokus Wechselverhalten zu verringern, wenn Sie in einem Mittelpunkt zwischen zwei Elementen mit natürlichem Rauschen schweben

## <a name="see-also"></a>Weitere Informationen

* [Augenbasierte Interaktion](eye-gaze-interaction.md)
* [Anvisieren und Verweilen](gaze-and-dwell.md)
* [Hände – Direkte Manipulation](direct-manipulation.md)
* [Hände – Gesten](gaze-and-commit.md#composite-gestures)
* [Hände – Zeigen und Ausführen](point-and-commit.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Spracheingabe](voice-input.md)



