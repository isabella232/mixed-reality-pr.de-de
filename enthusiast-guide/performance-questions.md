---
title: Häufig gestellte Fragen zur Leistung
description: Problembehandlung Windows Mixed Reality Leistung, die über unsere Standarddokumentation für den Kundensupport hinausgeht.
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Problembehandlung, Fehler, Hilfe, Support, Leistung
appliesto:
- Windows 10
ms.openlocfilehash: 6754923a07d4c75c6f0f44aad07c5d3c55c28ae4673900531d8a4af663d9e7c2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219416"
---
# <a name="performance-faqs"></a>Häufig gestellte Fragen zur Leistung

## <a name="is-my-windows-mixed-reality-headset-rendering-at-60-hz-or-90-hz-framerate"></a>Wird mein Windows Mixed Reality Headset mit 60 Hz oder 90 Hz Framerate gerendert?

Wenn Sie über eine diskrete GPU mit GPU 2.0-Ports und eine CPU mit vier oder mehr physischen Kernen verfügen, sollten Sie 90 Hz erhalten. Um dies zu bestätigen, überprüfen Sie **Geräteportal > Registerkarte Leistung.**

Hinweis: Wenn Ihre GPU nur über eine GPU 1.4-Ausgabe verfügt, können Sie als Problemumgehung einen DisplayPort-zu-NOTE [2.0-Adapter](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) verwenden.

Hinweis: Die Einstellungen für die visuelle Qualität in "Headsetanzeige" wirken sich nur auf das Rendern der Windows Mixed Reality-Benutzererfahrung aus.

## <a name="my-pc-is-running-slowly"></a>Mein PC wird langsam ausgeführt

Das System kann aus vielen Gründen langsam sein und in der Regel nur wenige Sekunden dauern. Wenn dieses Problem über einen längeren Zeitraum besteht:

1. Schließen Sie alle nicht verwendeten Anwendungen auf dem Desktop.
2. Stellen Sie sicher, dass Ihr Laptop an eine Stromquelle angeschlossen ist.
3. Stellen Sie sicher, dass der PC nicht aufwärmt.
4. Senken Sie die visuelle Qualität in Ihrer Windows Mixed Reality Zu Hause.
5. Stellen Sie sicher, dass Sie über die neuesten [Grafiktreiber](other-questions.md#my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors) für Ihren PC verfügen.

## <a name="my-pc-is-warming-up-as-i-run-the-mixed-reality-experiences-how-do-i-keep-it-cool"></a>Mein PC wird während der Ausführung der Mixed Reality aufwärmt. Gewusst wie sie kalt halten

1. Überprüfen Sie, ob der Akku geladen ist und die Stromquelle angeschlossen ist.
2. Stellen Sie sicher, dass die PC-Lüfter nicht blockiert werden.
3. Verwenden Sie den PC in einer relativ coolen Umgebung.
4. Stellen Sie sicher, dass keine Wärmequellen (z. B. die Sonnen- oder Wärmequellen) auf den PC zeigt.

## <a name="my-visuals-are-choppy-load-slowly-or-dont-look-good"></a>Meine Visuals sind abgesengt, werden langsam geladen oder sehen nicht gut aus.

* Stellen Sie sicher, dass Ihr Headset an die richtige Grafikkarte auf Ihrem PC angeschlossen ist. Einige PCs verfügen sowohl über integrierte als auch über diskrete Grafikkarten. Die diskrete Karte bietet im Allgemeinen die beste Leistung. [Erfahren Sie mehr über PC-Hardware.](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)
* Schließen Sie nicht verwendete Anwendungen auf Ihrem Desktop.
* Stellen Sie sicher, dass Ihr Headset gut passt (bewegen Sie es nach unten und höher oder nach links und rechts, um es anzupassen).
* Passen Sie die visuellen Einstellungen Ihres Headsets in Einstellungen > **Mixed Reality > Headset-Anzeige an.** Wenn "Visuelle Qualität" auf "Automatisch" festgelegt ist, wird die Mixed Reality-Erfahrung für Ihren PC automatisch ausgewählt. Um weitere visuelle Details zu erhalten, legen Sie "Visuelle Qualität" auf "Hoch" fest. Wenn Ihre Visuals gehackt sind, wählen Sie eine niedrigere Einstellung aus.
* Passen Sie den Headset-Kalibrierungsregler an, um sicherzustellen, dass die Brillen auf den richtigen Abstand zwischen Ihren Augen (ipd) festgelegt sind. Wenn Sie Ihre IPD nicht kennen, kann ein Optometrist sie für Sie messen oder eine Website verwenden, die für die Messung der IPD konzipiert ist. Wenn das Headset nicht über einen Kalibrierungsregler verfügen, wählen Sie Einstellungen > **Mixed Reality > Headset-Anzeige** aus, und passen Sie das "Kalibrierungssteuersystem" an.
* Wenn Sie einen USB-C- oder DisplayPort to ADAPTER-Adapter verwenden, versuchen Sie es mit einem anderen Adapter. Weitere Informationen [finden Sie unter Empfohlene Adapter.](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
* Trennen Sie alle zusätzlichen Monitore, die möglicherweise mit der Grafikkarte Ihres PCs verbunden sind.
* Probieren Sie verschiedene Mixed Reality-Apps aus dem Windows Store– einige funktionieren möglicherweise besser mit der Computereinrichtung.
