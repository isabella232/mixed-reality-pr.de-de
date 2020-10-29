---
title: Häufig gestellte Fragen zur Leistung
description: Erweiterte Windows Mixed Reality-Problembehandlung, die über die standardmäßige Kundensupport Dokumentation hinausgeht.
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, Mr, Problembehandlung, Fehler, Hilfe, Support, Leistung
appliesto:
- Windows 10
ms.openlocfilehash: 2150d605ecf29bb0bcf88f0f76a0193046f74ed5
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2020
ms.locfileid: "91685814"
---
# <a name="performance-faqs"></a>Häufig gestellte Fragen zur Leistung

## <a name="is-my-windows-mixed-reality-headset-rendering-at-60hz-or-90hz-framerate"></a>Ist mein Windows Mixed Reality-Headset bei 60Hz oder 90Hz Framerate?

Wenn Sie über ein diskretes GPU mit 2,0-Ports und eine CPU mit vier oder mehr physischen Kernen verfügen, sollten Sie 90 Hz erhalten. Um dies zu bestätigen, aktivieren Sie die Registerkarte **Leistung des Geräte Portals >** . 

Hinweis: Wenn Ihre GPU nur über die Ausgabe "HDMI 1,4" verfügt, können Sie als Problem Umgehung einen DisplayPort für den [2,0 HDMI-Adapter](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) verwenden. 

Hinweis: die Einstellungen für die visuelle Qualität in "Headset Display" wirken sich nur auf das Rendering des Windows Mixed Reality-Start Erlebnisses aus.

## <a name="my-pc-is-running-slowly"></a>Der PC wird langsam ausgeführt.

Das System kann aus vielen Gründen langsam und in den meisten Fällen nur wenige Sekunden dauern. Wenn dieses Problem über einen längeren Zeitraum auftritt:
1. Schließen Sie die gesamte nicht verwendete Anwendung auf dem Desktop.
2. Stellen Sie sicher, dass Ihr Laptop an eine Stromquelle angeschlossen ist.
3. Stellen Sie sicher, dass der PC nicht aufwärmt.
4. Verringern Sie die visuelle Qualität in Ihrer Windows Mixed Reality-Startseite.
5. Stellen Sie sicher, dass Sie über die neuesten [Grafiktreiber](other-questions.md#my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors) für Ihren PC verfügen.

## <a name="my-pc-is-warming-up-as-i-run-the-mixed-reality-experiences-how-do-i-keep-it-cool"></a>Der PC wird beim Ausführen der gemischten Realität erwärmt. Gewusst wie bleiben Sie dabei cool?

1. Überprüfen Sie, ob der Akku in Rechnung gestellt wird und die Stromquelle angeschlossen ist.
2. Stellen Sie sicher, dass die PC-Fans nicht blockiert sind.
3. Verwenden Sie den PC in einer relativ kalten Umgebung.
4. Stellen Sie sicher, dass keine Wärmequellen (z. b. Sun oder Heat Vents) auf dem PC angezeigt werden.

## <a name="my-visuals-are-choppy-load-slowly-or-dont-look-good"></a>Meine visuellen Elemente sind choppy, werden langsam geladen oder sind nicht gut geeignet.
* Stellen Sie sicher, dass Ihr Headset an der richtigen Grafikkarte auf Ihrem PC angeschlossen ist. Einige PCs verfügen sowohl über integrierte als auch diskrete Grafikkarten. Die diskrete Karte bietet im Allgemeinen die beste Leistung. [Erfahren Sie mehr über PC-Hardware](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines).
* Schließen Sie nicht verwendete Anwendungen auf Ihrem Desktop.
* Stellen Sie sicher, dass Ihr Headset passend ist (verschieben Sie es nach unten und nach oben oder nach links und rechts, um es anzupassen).
* Passen Sie die visuellen Einstellungen Ihres Headsets in den **Einstellungen > gemischte Realität > die Headset-Anzeige** an. Wenn "visuelle Qualität" auf "automatisch" festgelegt ist, wird die gemischte Realität für Ihren PC automatisch ausgewählt. Wenn Sie weitere visuelle Details möchten, legen Sie "visuelle Qualität" auf "hoch" fest. Wählen Sie eine niedrigere Einstellung aus, wenn Ihre visuellen Elemente nicht angezeigt werden.
* Passen Sie den Knopf für die Headset-Kalibrierung an, um sicherzustellen, dass die Linsen auf den korrekten Abstand zwischen ihren Schülern (IPD) festgelegt sind. Wenn Sie Ihre IPD nicht kennen, sollte optomezst in der Lage sein, Sie für Sie zu messen, oder eine Website verwenden, die für die Messung von IPD konzipiert ist. Wenn das Headset keinen Kalibrierungs Knopf hat, wählen Sie **Einstellungen > gemischte Realität > Headset-Anzeige** aus, und passen Sie das "kalibrierungssteuerelement" an.
* Wenn Sie einen USB-C-oder DisplayPort für den HDMI-Adapter verwenden, versuchen Sie es mit einem anderen. Siehe [Empfohlene Adapter.](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
* Trennen Sie alle zusätzlichen Monitore, die möglicherweise mit der Grafikkarte Ihres PCs verbunden sind.
* Probieren Sie verschiedene gemischte Reality-Apps aus dem Windows Store aus – einige Arbeiten mit dem Einrichten des Computers möglicherweise besser.
