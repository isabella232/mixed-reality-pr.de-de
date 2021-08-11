---
title: Häufig gestellte Fragen zur Nachverfolgung
description: Nachverfolgen Windows Mixed Reality Problembehandlung, die über unsere Standarddokumentation für den Kundensupport hinausgeht.
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Problembehandlung, Fehler, Hilfe, Support, Nachverfolgung
ms.openlocfilehash: fe5462a53de7b196db37edbbf0e56199a17c4c99b54ea1e7d9edf72e0845c9e5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115199476"
---
# <a name="tracking-faqs"></a>Häufig gestellte Fragen zur Nachverfolgung

## <a name="my-headset-has-stopped-tracking"></a>Mein Headset hat die Nachverfolgung beendet.

Stellen Sie sicher, dass die Beleuchtung eingeschaltet ist und dass die Außenkameras am Front ihres Headsets nicht blockiert werden. Wenn die Nachverfolgung verloren geht, kann es einige Sekunden dauern, bis die Nachverfolgung fortgesetzt wird. Starten Sie den Windows Mixed Reality, der vom Portal nachverfolgt wird, nicht neu gestartet wird.

## <a name="i-can-look-around-but-i-cant-translate-im-stuck-in-3dof"></a>Ich kann mich umschauen, aber nicht übersetzen (ich bin in 3DOF hängen geblieben)

Dies bedeutet, dass das Nachverfolgungssystem keine Pose generieren kann, oder die Anwendung hat die Verwendung neuer Posendaten zum Rendern beendet. So beheben Sie das Problem:

* Stellen Sie sicher, dass der Raum genügend Licht hat.
* Stellen Sie sicher, dass der Raum über genügend Details zum Nachverfolgen verfügt.
* Trennen Sie das Gerät, schließen Sie Windows Mixed Reality, und schließen Sie das Gerät erneut an.
* Wenn die Nachricht weiterhin besteht, wenden Sie sich an [den Kundensupport.](https://support.microsoft.com/)

## <a name="the-view-in-the-hmd-is-frozen"></a>Die Ansicht im HMD ist fixiert.

Dies bedeutet in der Regel, dass die Anwendung oder eine Komponente auf Systemebene fehlgeschlagen ist. Versuchen Sie, dies zu versuchen:

1. Klicken Sie auf die Schaltfläche "Home", um die Anwendung zu verlassen.
2. Trennen Sie das Gerät, schließen Sie MRP, und schließen Sie das Gerät wieder ein.
3. Starten Sie den PC neu.

## <a name="the-world-briefly-froze-and-tilted-or-flipped-upside-down-before-returning-to-normal"></a>Die Welt hat kurz eingefroren und gekippt oder auf den Kopf gekippt, bevor sie wieder normal wird.

Dies kann durch einen schwerwiegenden Fehler oder einen vorübergehenden Mangel an Arbeitsspeicher oder CPU-Ressourcen durch eine Anwendung oder Komponente auf Systemebene verursacht werden. So überprüfen Sie:

1. Öffnen Task-Manager, und stellen Sie sicher, dass mindestens 20 % der CPU frei sind, 400 MB Arbeitsspeicher verfügbar sind und die Datenträger-E/A unter 80 % liegt.
2. Wechseln Sie **Ereignisanzeige > Windows Protokolle > Anwendung,** um nach Fehlern zu suchen, die ungefähr zum Zeitpunkt des Einfrierens aufgetreten sind. Suchen Sie nach allem, was sich auf HoloLens Sensoren, Mixed Reality oder die Anwendung bezieht, die Sie zu diesem Zeitpunkt ausgeführt haben. In diesen Protokollen wird möglicherweise erläutert, was den Fehler verursacht hat.
3. Starten Sie den PC neu, wenn das Problem weiterhin besteht.

## <a name="the-world-flipped-upside-down-momentarily-and-returned-to-normal"></a>Die Welt ist kurz wieder auf den Kopf gekippt und normal.

Dies wird in der Regel durch Fehler beim Abrufen von Sensordaten aus dem Headset verursacht, um die Nachverfolgungsalgorithmen zu informieren. Wenn dies häufig geschieht:

1. Schließen Sie das Headset an einen anderen USB 3.0-Anschluss an.
2. Schließen Sie das Headset direkt an den PC und nicht an einen USB 3.0-Hub an.
3. Wenn das Problem weiterhin besteht, wenden Sie sich an [den Kundensupport.](https://support.microsoft.com/)

## <a name="the-world-is-tilted-but-i-can-navigate-and-walk-around-in-windows-mixed-reality"></a>Die Welt ist gekippt, aber ich kann in der Umgebung navigieren und Windows Mixed Reality

Wenn Sensordatenfehler in den Umgebungsdaten auf Ihrem PC aufgezeichnet werden, kann dies dazu führen, dass Windows Mixed Reality, manchmal dauerhaft, geneigt erscheinen. So beheben Sie dieses Problem:

1. Trennen Sie das Headset, schließen Sie Windows Mixed Reality, und schließen Sie das Headset wieder ein.
2. Starten Sie den PC neu.
3. Löschen Sie Ihre Umgebungsdaten.