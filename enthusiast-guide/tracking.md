---
title: FAQs zur Nachverfolgung
description: Nachverfolgung der Windows Mixed Reality-Problembehandlung, die über die standardmäßige Kundensupport Dokumentation hinausgeht
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, Mr, Problembehandlung, Fehler, Hilfe, Support, Nachverfolgung
ms.openlocfilehash: 7a7e6add79af5917749ba241347d6cf719f6ed90
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2020
ms.locfileid: "93132094"
---
# <a name="tracking-faqs"></a>FAQs zur Nachverfolgung

## <a name="my-headset-has-stopped-tracking"></a>Mein Headset hat die Überwachung beendet.

Stellen Sie sicher, dass die Lichter eingeschaltet sind und dass es keine Hindernisse für die in-out-nach Verfolgungs Kameras am Anfang Ihres Headsets gibt. Wenn die Nachverfolgung verloren geht, kann es einige Sekunden dauern, bis der Vorgang fortgesetzt wird. Wenn der Vorgang nicht fortgesetzt wird, starten Sie das Windows Mixed Reality-Portal neu.

## <a name="i-can-look-around-but-i-cant-translate-im-stuck-in-3dof"></a>Ich kann sehen, aber ich kann nicht übersetzt werden (ich bin in 3DOF stecken)

Dies bedeutet, dass das Überwachungssystem keine Pose generieren kann, oder die Anwendung die Verwendung neuer posiingdaten zum Rendering beendet hat. Überprüfen Sie Folgendes:

* Stellen Sie sicher, dass der Raum genug hell ist.
* Stellen Sie sicher, dass für den Raum genügend Details zur Verfolgung vorhanden sind.
* Entfernen Sie das Gerät, schließen Sie Windows Mixed Reality, und schließen Sie das Gerät erneut ein.
* Wenden Sie sich an den [Kundensupport](https://support.microsoft.com/) , wenn die Meldung weiterhin

## <a name="the-view-in-the-hmd-is-completely-frozen"></a>Die Ansicht im HMD ist vollständig fixiert.

Dies bedeutet in der Regel, dass die Anwendung oder eine Komponente auf Systemebene fehlgeschlagen ist. Versuchen Sie Folgendes:

1. Klicken Sie auf die Schaltfläche "Home", um die Anwendung zu verlassen.
2. Entfernen Sie das Gerät, schließen Sie die MRP, und schließen Sie das Gerät wieder ein.
3. Starten Sie den PC neu.

## <a name="the-world-briefly-froze-and-perhaps-tilted-or-flipped-upside-down-before-returning-to-normal"></a>Die Welt wurde kurz vor der Rückkehr zur normalen Umgebung kurz geblinkt und möglicherweise gekippt oder geflippt.

Dies kann darauf zurückzuführen sein, dass eine Anwendung oder eine Komponente auf Systemebene auf einen schwerwiegenden Fehler oder einen temporären Mangel an Arbeitsspeicher oder CPU-Ressourcen stößt. Überprüfen Sie Folgendes:

1. Öffnen Sie den Task-Manager, und stellen Sie sicher, dass mindestens 20% der CPU frei sind, 400 MB Arbeitsspeicher verfügbar sind und die Datenträger-e/a unter 80% liegen.
2. Wechseln Sie zu **Ereignisanzeige > Windows-Protokolle > Anwendung** , um nach Fehlern zu suchen, die in etwa zum Zeitpunkt der Sperrung aufgetreten sind. Suchen Sie nach allem, was auf hololens-Sensoren, gemischte Realität oder die Anwendung, die Sie um diese Zeit ausgeführt haben, verweist. Diese Protokolle können erläutern, was den Fehler verursacht hat.
3. Starten Sie den PC neu, wenn das Problem weiterhin besteht.

## <a name="the-world-flipped-upside-down-momentarily-and-returned-to-normal"></a>Die Welt wurde vorübergehend gekippt und wieder normal

Dies wird in der Regel durch Fehler beim Abrufen von Sensordaten aus dem Headset verursacht, um die Verfolgungs Algorithmen zu informieren. Wenn dies häufig auftritt:

1. Anschließen Sie das Headset an einen anderen USB 3,0-Port.
2. Anschließen Sie das Headset direkt in den PC und nicht in einen USB 3,0-Hub.
3. Wenn das Problem weiterhin besteht, wenden Sie sich an den [Kundensupport](https://support.microsoft.com/).

## <a name="the-world-is-tilted-but-i-can-navigate-and-walk-around-in-windows-mixed-reality"></a>Die Welt ist gekippt, aber ich kann in Windows Mixed Reality navigieren und Sie durchlaufen.

Wenn Sensordaten Fehler in den Umgebungs Daten auf Ihrem PC aufgezeichnet werden, kann dies dazu führen, dass Windows Mixed Reality manchmal auch dauerhaft angezeigt wird. So beheben Sie dieses Problem:

1. Entfernen Sie das Headset, schließen Sie Windows Mixed Reality, und schließen Sie das Headset wieder ein.
2. Starten Sie den PC neu.
3. Löschen Sie die Umgebungs Daten.