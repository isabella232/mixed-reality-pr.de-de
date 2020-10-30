---
title: FAQ zu HP Reverb G2
description: Häufig gestellte Fragen zur Verwendung von HP-Reverb G2-Headset
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, Mr, Problembehandlung, Fehler, Hilfe, Support, Leistung
appliesto:
- Windows 10
ms.openlocfilehash: 82f9accc8e24574faf7c826aff1908bea7350b08
ms.sourcegitcommit: feceb21018ce1d966188a34bd1faeddfdc1b9544
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049472"
---
# <a name="hp-reverb-g2-frequently-asked-questions"></a>Häufig gestellte Fragen zu HP Reverb G2

## <a name="is-there-a-specific-order-i-should-follow-to-connect-my-headset-cables-to-a-pc"></a>Gibt es eine bestimmte Reihenfolge, die ich befolgen sollte, um meine Headset-Kabel mit einem PC zu verbinden.

HP empfiehlt Folgendes:

- Verbinden Sie das 6-Meter-Kabel zuerst mit dem Headset, bevor Sie eine Verbindung mit dem PC oder der Netzteil herstellen.
- Lassen Sie das 6-Meter-Kabel nach der Erstinstallation mit dem Headset verbunden.
- Wenn das Headset nicht verwendet wird, trennen Sie die Verbindung zwischen dem Netzadapter und dem 6-Meter-Kabel.

## <a name="what-should-i-do-to-get-a-crisper-image"></a>Was soll ich tun, um ein Crisper-Bild zu erhalten?

Es gibt einige Dinge, die Sie ausprobieren können, wenn Sie der Ansicht sind, dass die Anzeige etwas unscharf aussieht:

- Stellen Sie sicher, dass sich Ihr Headset ordnungsgemäß auf dem Kopf befindet, sodass die Augen auf die-Objektive zentriert sind.
- Versuchen Sie, die IPD (interpupillary Distance) anzupassen. Beachten Sie, dass "Reverb G2" eine Hardware-IPD verwendet. Um dies zu ändern, suchen Sie auf Ihrem Headset nach IPD-Anpassung.
- Wenn Sie eine Brille oder Kontakte benötigen, sind Sie weiterhin erforderlich.
- Überprüfen Sie Ihre Linsen, wenn Sie bereinigt werden müssen (nur Mikro Fiber – keine Flüssigkeiten).
- Aufgrund des erweiterten Entwurfs des Headsets kann es in den ersten Minuten einige kleinere Abbild-Ghosting geben, während das Gerät kalt ist, bis die LCDs eine Aufwärm Chance haben.

## <a name="i-am-getting-a-7-14-something-went-wrong-error-when-i-plug-in-my-headset"></a>Ich erhalte die Fehlermeldung "7-14 ein Fehler ist aufgetreten", wenn ich mein Headset hinzufüge.

Wenn die Fehlermeldung "7-14 ein Fehler ist aufgetreten" angezeigt wird, führen Sie die folgenden Schritte aus:

- Stellen Sie sicher, dass Sie die neuesten Treiber installiert haben.
- Versuchen Sie, das Kabel an einen anderen USB-3,0-Port zu binden.
- Verwenden Sie den USB-C-Adapter für einen Adapter, der zum Ausprobieren anderer Ports verwendet wird.

Versuchen Sie, das Kabel an einen anderen USB-Hub zu binden.  

> [!NOTE]
> HP empfiehlt, nur USB-Controller zu verwenden, die in die Hauptplatine mit den Geräten der Hall-G2
> Wenn Sie Ihr Gerät nicht verbinden können, wenden Sie sich an den [HP Support](https://support.hp.com/us-en) .

## <a name="i-am-getting-a-13-14-something-went-wrong-error-when-my-pc-resumes-from-hibernate-s4"></a>Ich erhalte die Fehlermeldung "Es ist 13-14 ein Fehler aufgetreten", wenn mein PC aus dem Ruhezustand (S4) fortgesetzt wird.

Manchmal kann die Grafikkarte während des fort Setzens keine Verbindung herstellen. Wenn Sie also den USB-Typ C vom PC deinstallieren und wiederherstellen, können Sie eine Verbindung herstellen.

## <a name="the-mixed-reality-portal-says-cant-run-mixed-reality-on-this-headset-but-this-worked-fine-with-my-previous-wmr-headset"></a>Das Mixed Reality-Portal besagt, dass die gemischte Realität auf diesem Headset nicht ausgeführt werden kann. Dies funktionierte aber problemlos mit meinem vorherigen WMR-Headset.

Dies kann der Fall sein, wenn Ihr HP-Reverb-G2 einen leistungsfähigeren PC erfordert, um die optimale Leistung zu gewährleisten. Weitere Informationen finden Sie unter den Mindestanforderungen für [PCs](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) .

## <a name="it-looks-like-my-left-display-is-stretched-and-the-right-display-is-off-centered-and-half-black"></a>Es sieht so aus, als würde meine linke Anzeige gestreckt, und die Rechte Anzeige ist nicht zentriert und halb schwarz.

Dies kann vorkommen, wenn Ihr Headset nicht bei der nativen Auflösung ausgeführt wird. Aufgrund der Art der hochauflösenden Anzeige im HP-Hash-G2-HMD können nicht alle Systeme die native Auflösung renderrengen. In einem zukünftigen Windows Update wird ein Fix behoben, der das Renderingproblem behandelt, wenn sich das Headset nicht in der nativen Auflösung befindet.

Es gibt einige Gründe, warum Ihr System nicht in der Lage ist, bei der systemeigenen Auflösung zu Rendering:

- Der DisplayPort auf dem System ist möglicherweise nicht 1,3-kompatibel, oder es werden nicht alle vier Bereiche unterstützt.
- Wenn Sie einen Adapter verwenden, wird er möglicherweise nicht mit HBR3 kompatibel unterstützt, oder es werden nicht alle vier Bereiche unterstützt.
- Wenn Ihr System über eine hybride GPU verfügt, kann dies die für den DisplayPort verfügbare Bandbreite einschränken.

## <a name="why-are-my-hp-motion-controller-models-not-showing-up-correctly-in-a-game"></a>Warum werden meine HP Motion Controller-Modelle in einem Spiel nicht richtig angezeigt?

Obwohl viele Spiele sofort mit HP Motion Controller funktionieren, haben einige Spiele Abhängigkeiten von vorhandenen Controller Features und können daher einige Probleme haben:

- Falsches Modell angezeigt: die Korrektur erfordert ein Spiel Update. In der Regel werden dadurch keine Features des Spiels blockiert. Dies kann jedoch zu Verwirrung oder sogar visuellen Artefakten führen.
- Abhängigkeit von dem Touchpad oder eher im Allgemeinen für das Eingabe Layout des Controllers. Mit steamvr können benutzerdefinierte Bindungen erstellt werden, um diese Art von Problem zu umgehen:
    - Windows Mixed Reality für steamvr umfasst benutzerdefinierte Bindungen für einige Spiele. Diese Bindungen werden automatisch verwendet, wenn das Spiel gestartet wird, und es ist keine Benutzeraktion erforderlich.