---
title: Anvisieren und Verweilen
description: Verschaffen Sie sich einen allgemeinen Überblick über das Eingabemodell zum Anvieren und Verweilen mit den Augen und mit dem Kopf für Mixed Reality-Anwendungen.
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Mixed Reality, Anvisierten, Verweilen, Interaktion, Design, Eyetracking, Kopfverfolgung, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: c65c13b06df70ed5471b283ad349dd72e1575018a98913177983d7a13571d666
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213674"
---
# <a name="gaze-and-dwell"></a>Anvisieren und Verweilen

Wenn die Hände mit Werkzeugen und Gegenständen beschäftigt sind, können Gesten mühsam oder unmöglich sein.
Sprachbefehle können auch in bestimmten Kontexten unzuverlässig sein, z. B. unter übermäßig lauten Bedingungen.
Anv und Verweilen bietet einen vertrauten und einfach zu bedienenden Mechanismus zum Arbeiten mit Kopf und Freihand auf HoloLens.
Darüber hinaus ist Anving und Verweilen ein hervorragendes Fallback, das unabhängig von Rauschunterdrückung oder Stilleeinschränkungen in der Betriebsumgebung ist.
Wir unterscheiden zwei Varianten des [](gaze-and-dwell-head.md) _Anvierens_ und Verweilens: Anvieren mit dem Kopf und Verweilen und [Anvieren mit den Augen und Verweilen.](gaze-and-dwell-eyes.md)

## <a name="scenarios"></a>Szenarien

Anvieren und Verweilen zeichnet sich in Szenarien aus, in denen die Hände einer Person mit anderen Aufgaben beschäftigt sind und die Stimme aufgrund von Umgebungs- oder sozialen Einschränkungen nicht zu 100 % zuverlässig oder verfügbar ist.
Ein gutes Beispiel ist eine Person, die eine HoloLens trägt, um Referenzinformationen bei der Reparatur eines Fahrzeugmotors zu überlagern.
Die Hände sind mit Werkzeugen beschäftigt oder stützen den eigenen Körper, während sich die Person in den Motorraum lehnt.
Der Garagenbereich ist laut, mit einem ständigen Klopfen und Knarren der Werkzeuge, wodurch sich die Verwendung von Sprachbefehlen schwierig gestaltet.
Anvieren und Verweilen ermöglicht es der Person, die HoloLens, sicher durch ihr Referenzmaterial zu navigieren, ohne ihren Workflow zu unterbrechen.

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

 ## <a name="see-also"></a>Siehe auch

* [Augenbasierte Interaktion](eye-gaze-interaction.md)
* [Blickverfolgung auf HoloLens 2](eye-tracking.md)
* [Anvisieren und Ausführen](gaze-and-commit.md)
* [Hände – Direkte Manipulation](direct-manipulation.md)
* [Hände – Gesten](gaze-and-commit.md#composite-gestures)
* [Hände – Zeigen und Ausführen](point-and-commit.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Spracheingabe](voice-input.md)