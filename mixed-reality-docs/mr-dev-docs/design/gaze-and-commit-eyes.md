---
title: Anvisieren mit den Augen und Ausführen
description: Erfahren Sie mehr über das Eingabemodell „Anvisieren mit den Augen und Ausführen“.
author: sostel
ms.author: sostel
ms.date: 05/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Eye Tracking, Mixed Reality, Eingabe, Anvisieren mit den Augen, Zielen mit den Augen, HoloLens 2, Blickgestützte Auswahl, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit, Anvisieren
ms.openlocfilehash: 12ffc24c39a9f8be329972516d42730dc98899d3ebba8359e9fea6ebbf6d02c2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197824"
---
# <a name="eye-gaze-and-commit"></a>Anvisieren mit den Augen und Ausführen

_Anvisieren mit den Augen und Ausführen_ ist ein Sonderfall des Eingabemodells [Anvisieren und Ausführen](gaze-and-commit.md), der das Anzielen eines Objekts mit Blicken beinhaltet. Sie können Handlungen für das Ziel mithilfe einer sekundären _Ausführen_-Eingabe einleiten, etwa einer Handgeste, einem Sprachbefehl oder einer Eingabe über ein Peripheriegerät wie einen Spielcontroller. 

Mit HoloLens 2 haben wir die großartige Möglichkeit, das Eingabemodell _Anvisieren und Ausführen_ durch das Anvisieren mit den Augen statt mit dem Kopf schneller und komfortabler zu gestalten. Auf diese Weise erweitern Sie das häufig verwendete Interaktionsmodell [Anvisieren mit dem Kopf und Ausführen](gaze-and-commit.md): 
1. Sehen Sie ein Ziel an 
2. Führen Sie zum Bestätigen Ihrer Zielauswahl eine der folgenden sekundären expliziten Eingaben aus:  
   - Handgeste (beispielsweise in die Luft tippen)
   - Drücken einer Taste (z. B. auf einer Bluetooth-Tastatur oder einem Klickgerät)
   - Sprachbefehl (z. B. „Auswählen“)
   - Verweilen (d. h. der Benutzer schaut zum Auswählen weiterhin auf das Ziel)

„Anvisieren mit den Augen“ verhält sich jedoch anders als das Anvisieren mit dem Kopf und bringt viele spezielle Herausforderungen mit sich. 

In den [Entwurfsrichtlinien für das Anvisieren mit den Augen](eye-tracking.md) sind die allgemeinen Vorteile und Herausforderungen zusammengefasst, die sich beim Verwenden der Blickverfolgung als Eingabemodell für die holografische App stellen. In diesem Abschnitt konzentrieren wir uns auf die speziellen Entwurfsüberlegungen für das Modell _Anvisieren mit den Augen und Ausführen_.
Zu Beginn sei vorausgeschickt, dass unsere Augen sich unglaublich schnell bewegen und hervorragend für die schnelle Zieladressierung im Sichtfeld geeignet sind. Das Anvisieren mit den Augen ist ideal für schnelle Aktionen des Typs „Anvisieren und Ausführen“ geeignet, besonders in Kombination mit schnellen Ausführaktionen wie Tippen in die Luft oder Drücken einer Schaltfläche.

## <a name="head-and-eye-tracking-design-concepts-demo"></a>Demo der Entwurfskonzepte für Kopf- und Eyetracking

Wenn Sie die Entwurfskonzepte für Kopf- und Eyetracking in Aktion sehen möchten, sehen Sie sich unten unsere Videodemo **Entwerfen von Hologrammen: Kopf- und Eyetracking** an. Wenn Sie fertig sind, fahren Sie mit einem ausführlicheren Einblick in bestimmte Themen fort.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

*Dieses Video wurde aus der HoloLens 2-App „Entwerfen von Hologrammen“ aufgenommen. Laden Sie die vollständige Erfahrung [hier](https://aka.ms/dhapp) herunter, und genießen Sie sie.*
   
## <a name="design-guidelines-for-eye-gaze-and-commit"></a>Entwurfsrichtlinien für „Anvisieren mit den Augen und Ausführen“

**Zeigen Sie keinen Cursor an**: Eine Interaktion ohne Cursor ist beim Anvisieren mit dem Kopf nahezu unmöglich. Beim Anvisieren mit den Augen lenkt der Cursor jedoch schnell ab und wirkt störend. Verwenden Sie zur Information des Benutzers, ob das Anvisieren mit den Augen funktioniert und das aktuell anvisierte Ziel korrekt erkannt wurde, dezente optische Markierungen.

**Bemühen Sie sich um ein dezent ein- und ausgeblendetes Zeigefeedback**: Was beim Anvisieren mit dem Kopf als hervorragendes visuelles Feedback erscheint, kann beim Anvisieren mit den Augen eine ziemliche Überforderung sein. Denken Sie daran, dass Augen überaus schnell sind und schnell über Punkte im Sichtfeld fliegen. Schnelle plötzliche Markierungsänderungen (Ein/Aus) können beim Umherschauen zu einem flackernden Feedback führen. Wir empfehlen daher, beim Zeigefeedback eine sanft eingeblendete (und beim Wegschauen sanft ausgeblendete) Markierung zu verwenden. Dies bedeutet, dass Sie beim Anvisieren eines Ziels das Feedback zuerst kaum wahrnehmen. Im Verlauf von 500-1000 ms würde die Markierung an Intensität zunehmen. Während unerfahrene Benutzer weiterhin das Ziel anvisieren könnten, um sicherzustellen, dass das System das anvisierte Ziel korrekt bestimmt hat, könnten erfahrene Benutzer schnell die Aktion „Anvisieren und Ausführen“ abschließen, ohne darauf zu warten, bis das Feedback die volle Intensität erreicht. Wir empfehlen außerdem, ein Ausblenden des Zeigefeedbacks zu verwenden. Untersuchungen haben gezeigt, dass schnelle Bewegungen und Kontraständerungen im peripheren Sichtbereich (dem Bereich des Sichtfelds, den Sie nicht direkt anschauen) gut wahrnehmbar sind.
Das Ausblenden muss nicht so langsam erfolgen wie das Einblenden. Dies ist nur wichtig, wenn Sie für die Markierung starke Kontrast- oder Farbänderungen verwenden. Wenn das Zeigefeedback zu Beginn dezent war, werden Sie wahrscheinlich keinen Unterschied feststellen.

**Achten Sie auf die Synchronisierung der Anvisier- und Ausführungssignale**: Die Synchronisierung der Eingabesignale ist wahrscheinlich keine große Herausforderung für das einfache in die Luft tippen und Drücken von Schaltflächen. Wenn Sie etwas kompliziertere Ausführungsaktionen verwenden möchten, sollten Sie allerdings darauf achten, auch wenn das lange Sprachbefehle oder komplizierte Handgesten beinhalten kann. Stellen Sie sich vor, dass Sie ein Ziel anvisieren und einen langen Sprachbefehl äußern. Bedenken Sie, dass sich In der Zeit, die Sie zum Sprechen benötigen, und der Zeit, die das System für die Spracherkennung benötigt, Ihr Auge in der Regel schon längst einem neuen Ziel in der Szene zugewandt hat. Weisen Sie entweder Ihre Benutzer darauf hin, dass sie das Ziel so lange anvisieren müssen, bis der Befehl erkannt wurde, oder Sie müssen bei der Verarbeitung der Eingabe den Beginn des Befehls und den zu diesem Zeitpunkt anvisierten Punkt bestimmen.

## <a name="see-also"></a>Siehe auch

* [Augenbasierte Interaktion] (eye-gaze-interaction.md)
* [Blickverfolgung auf HoloLens 2] (eye-tracking.md)
* [Anvisieren und Ausführen](gaze-and-commit.md)
* [Anvisieren und Verweilen](gaze-and-dwell.md)
* [Hände – Direkte Manipulation](direct-manipulation.md)
* [Hände – Gesten](gaze-and-commit.md#composite-gestures)
* [Hände – Zeigen und Ausführen](point-and-commit.md)
* [Instinktive Interaktionen](interaction-fundamentals.md)
* [Spracheingabe](voice-input.md)
