---
title: Schauen und wohnen
description: Allgemeine Übersicht über den (Augen-/Schreib-) Blick und das Eingangs Modell
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Gemischte Realität, Blick, wohnen, Interaktion, Entwurf, Eye Tracking, Head Tracking
ms.openlocfilehash: ee8b6487079a071fe84606949314f2dd315df45f
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2020
ms.locfileid: "91686979"
---
# <a name="gaze-and-dwell"></a>Schauen und wohnen

Wenn die Hände mit Werkzeugen und Gegenständen beschäftigt sind, können Gesten mühsam oder unmöglich sein.
Sprachbefehle können in bestimmten Kontexten auch unzuverlässig sein, z. b. unter übermäßig Laute Bedingungen.
"Blick" und "Wohnen" bietet einen vertrauten und leicht zu erarbeitenden Mechanismus für das Arbeiten mit den hololens und Freihand.
Außerdem ist "Blick" und "Wohnen" ein hervorragend Fall Back, das von Rausch Störungen oder Ruhe Einschränkungen in der Betriebsumgebung unabhängig ist.
Wir unterscheiden zwei Varianten von _Blick und wohnen_ : [Kopf-und](gaze-and-dwell-head.md) [Einblicken](gaze-and-dwell-eyes.md)und wohnen.

## <a name="scenarios"></a>Szenarien

Der Blick und das Leben sind hervorragend in Szenarios, in denen die Hände einer Person mit anderen Aufgaben beschäftigt sind, und die Stimme ist aufgrund von Umwelt-oder sozialen Einschränkungen nicht 100% zuverlässig oder verfügbar.
Ein gutes Beispiel ist eine Person, die eine HoloLens trägt, um Referenzinformationen bei der Reparatur eines Fahrzeugmotors zu überlagern.
Die Hände sind mit Werkzeugen beschäftigt oder stützen den eigenen Körper, während sich die Person in den Motorraum lehnt.
Der Garagenbereich ist laut, mit einem ständigen Klopfen und Knarren der Werkzeuge, wodurch sich die Verwendung von Sprachbefehlen schwierig gestaltet.
"Blick" und "Wohnen" ermöglicht es der Person, die die hololens verwendet, sicher zu navigieren, ohne den Workflow zu unterbrechen.

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
        <td>Anvisieren mit dem Kopf und Verweilen</td>
        <td>✔️ Empfohlen</td>
        <td>✔️ Empfohlen</td>
        <td>✔️ Empfohlen</td>
    </tr>
     <tr>
        <td>Anvisieren und Verweilen</td>
        <td>❌ Nicht verfügbar</td>
        <td>✔️ Empfohlen</td>
        <td>❌ Nicht verfügbar</td>
    </tr>
</table>


<br>

---

 ## <a name="see-also"></a>Weitere Informationen
* [Augenbasierte Interaktion](eye-gaze-interaction.md)
* [Blickverfolgung auf HoloLens 2](eye-tracking.md)
* [Anvisieren und Ausführen](gaze-and-commit.md)
* [Hände – Direkte Manipulation](direct-manipulation.md)
* [Hände – Gesten](gaze-and-commit.md#composite-gestures)
* [Hände – Zeigen und Ausführen](point-and-commit.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Spracheingabe](voice-input.md)
