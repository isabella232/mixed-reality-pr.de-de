---
title: Anvisieren und Verweilen
description: Verschaffen Sie sich einen allgemeinen Überblick über das Eingabe Modell für den Augenblick und das Leben für gemischte Reality-Anwendungen.
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Gemischte Realität, Blick, wohnen, Interaktion, Entwurf, Augen Verfolgung, Head-Tracking, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit
ms.openlocfilehash: aa4fceeb8875da89fd7f84c3709ff6db07fd96f4
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582136"
---
# <a name="gaze-and-dwell"></a>Anvisieren und Verweilen

Wenn die Hände mit Werkzeugen und Gegenständen beschäftigt sind, können Gesten mühsam oder unmöglich sein.
Sprachbefehle können in bestimmten Kontexten auch unzuverlässig sein, z. b. unter übermäßig Laute Bedingungen.
"Blick" und "Wohnen" bietet einen vertrauten und leicht zu erarbeitenden Mechanismus für das Arbeiten mit den hololens und Freihand.
Außerdem ist "Blick" und "Wohnen" ein hervorragend Fallback, das von Rausch Störungen oder Ruhe Einschränkungen in der Betriebsumgebung unabhängig ist.
Wir unterscheiden zwei Varianten von _Blick und wohnen_: [Kopf-und](gaze-and-dwell-head.md) [Einblicken](gaze-and-dwell-eyes.md)und wohnen.

## <a name="scenarios"></a>Szenarien

Der Blick und das Leben sind hervorragend in Szenarios, in denen die Hände einer Person mit anderen Aufgaben beschäftigt sind, und die Stimme ist aufgrund von Umwelt-oder sozialen Einschränkungen nicht 100% zuverlässig oder nicht verfügbar.
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
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1. Generation)</strong></a></td>
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