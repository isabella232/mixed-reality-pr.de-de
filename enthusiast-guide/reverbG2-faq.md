---
title: FAQ zu HP Reverb G2
description: Bleiben Sie auf dem neuesten Stand mit häufig gestellten Fragen zur Verwendung von HP-Reverb G2-Headset mit Windows Mixed Reality-immersiven Headsets.
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, Mr, Problembehandlung, Fehler, Hilfe, Support, Leistung
appliesto:
- Windows 10
ms.openlocfilehash: 9b477042ebed33600a007778cd534d3074e34770
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759285"
---
# <a name="hp-reverb-g2-frequently-asked-questions"></a>Häufig gestellte Fragen zu HP Reverb G2

## <a name="is-there-a-specific-order-i-should-follow-to-connect-my-headset-cables-to-a-pc"></a>Gibt es eine bestimmte Reihenfolge, die ich befolgen sollte, um meine Headset-Kabel mit einem PC zu verbinden.

HP empfiehlt Folgendes:

- Verbinden Sie das 6-Meter-Kabel zuerst mit dem Headset, bevor Sie eine Verbindung mit dem PC oder der Netzteil herstellen.
- Lassen Sie das 6-Meter-Kabel nach der Erstinstallation mit dem Headset verbunden.
- Wenn das Headset nicht verwendet wird, trennen Sie die Verbindung zwischen dem Strom Adapter und dem 6-Meter-Kabel.

## <a name="what-should-i-do-to-get-a-crisper-image"></a>Was soll ich tun, um ein Crisper-Bild zu erhalten?

Es gibt einige Dinge, die Sie ausprobieren können, wenn Sie der Ansicht sind, dass die Anzeige etwas unscharf aussieht:

- Stellen Sie sicher, dass sich Ihr Headset ordnungsgemäß auf dem Kopf befindet, wenn die Augen auf die-Objektive zentriert sind.
- Versuchen Sie, die IPD (interpupillary Distance) anzupassen. "Reverb G2" verwendet eine Hardware-IPD. Um dies zu ändern, suchen Sie auf Ihrem Headset nach IPD-Anpassung.
- Wenn Sie eine Brille oder Kontakte benötigen, müssen Sie diese bei Verwendung des Geräts verwenden.
- Überprüfen Sie, ob Ihre Linsen bereinigt sind (nur Mikro Fiber – keine Flüssigkeiten).
- Aufgrund des erweiterten Headset-Entwurfs ist es möglich, dass in den ersten Minuten ein geringfügig Abbild-Ghosting vorhanden ist, wenn das Gerät kalt ist, bis die LCDs die Möglichkeit zum Aufwärmen haben.

## <a name="i-am-getting-a-7-14-something-went-wrong-error-when-i-plug-in-my-headset"></a>Ich erhalte die Fehlermeldung "7-14 ein Fehler ist aufgetreten", wenn ich mein Headset hinzufüge.

7-14 etwas, was schief gelaufen ist, bedeutet, dass einige der erforderlichen USB2-Komponenten nicht gefunden wurden.  Aufgrund des extra langen Kabels des HP-Reverb-G2 sind einige der Toleranzen für die USB-Signale enger.  Dies bedeutet, dass ein Port auf dem Computer möglicherweise zuverlässiger funktioniert als ein anderer.

Wenn die Fehlermeldung "7-14 ein Fehler ist aufgetreten" angezeigt wird, führen Sie die folgenden Schritte aus:

- Stellen Sie sicher, dass Sie die neuesten Treiber für Ihr Headset und den USB-Controller installiert haben.
- Stellen Sie sicher, dass Sie einen Microsoft-USB-Treiber verwenden. Der Name des "Extensible Host Controller"-Geräts sollte "Microsoft" lauten.
- Versuchen Sie, das Kabel an einen anderen USB-3,0-Port auf dem Computer zu binden. (USB-Typ-C-und Typ-A-Ports testen)
- Verwenden Sie das enthaltene USB-C für einen Adapter, um andere Ports auszuprobieren.
- Versuchen Sie, das Headset mit einem USB-Hub an Ihren Computer zu übernehmen.

> [!NOTE]
> HP empfiehlt, nur USB-Controller zu verwenden, die in die Hauptplatine mit den Geräten der Hall-G2
> Wenn Sie Ihr Gerät nicht verbinden können, wenden Sie sich an den [HP Support](https://support.hp.com/us-en) .

## <a name="i-am-getting-a-13-14-something-went-wrong-error-when-my-pc-resumes-from-hibernate-s4"></a>Ich erhalte die Fehlermeldung "Es ist 13-14 ein Fehler aufgetreten", wenn mein PC aus dem Ruhezustand (S4) fortgesetzt wird.

Manchmal kann die Grafikkarte während des fort Setzens keine Verbindung herstellen. Wenn Sie also den USB-Typ C vom PC trennen und wiederherstellen, können Sie eine Verbindung herstellen.

## <a name="my-hp-motion-controller-joystick-will-sometimes-stick-to-one-side"></a>Mein HP Motion Controller-Joystick kommt manchmal an eine Seite.

Dieses Problem wird behoben, indem der Joystick vollständig drückt wird, bis es klickt, und der Wechsel erfolgt frei.

## <a name="others-state-i-am-loud-or-that-my-audio-is-clipping-while-i-am-using-the-microphone-with-some-applications"></a>Andere Bundesland ich bin laut oder mein Audioausschnitt, während ich das Mikrofon mit einigen Anwendungen verwende

Die Eingabe volumeebenen werden automatisch auf 100% festgelegt, wenn das HP-Reverb-Mikrofon zuerst von einem Windows-PC erkannt wird. Aufgrund des Reverb-G2's hochwertigen Mikrofonen ist die Eingabe Sensitivität weitaus höher als die standardmäßigen Windows 10-Einstellungen erwartet. Es wird empfohlen, die eingabebene "Reverb G2-Mikrofon" beginnend bei 50% zu setzen und von dort zentral hoch Eine optimale Einstellung ist für den Benutzer spezifisch, insbesondere dann, wenn Anwendungen verwendet werden, die nicht über die Mikrofon Einstellung "automatisch gewinnen" verfügen. Beispiele für Anwendungen mit "automatischer Gewinn" sind Skype, Zoom, Teams und Cisco WebEx, aber nicht alle VR Social-oder Broadcasting-Anwendungen haben dieses Feature.

## <a name="the-mixed-reality-portal-says-cant-run-mixed-reality-on-this-headset-but-this-worked-fine-with-my-previous-wmr-headset"></a>Das Mixed Reality-Portal besagt, dass die gemischte Realität auf diesem Headset nicht ausgeführt werden kann. Dies funktionierte aber problemlos mit meinem vorherigen WMR-Headset.

Dies kann der Fall sein, wenn Ihr HP-Reverb-G2 einen leistungsfähigeren PC erfordert, um die optimale Leistung zu gewährleisten. Weitere Informationen finden Sie unter den Mindestanforderungen für [PCs](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) .

## <a name="it-looks-like-my-left-display-is-stretched-and-the-right-display-is-off-centered-and-half-black"></a>Es sieht so aus, als würde meine linke Anzeige gestreckt, und die Rechte Anzeige ist nicht zentriert und halb schwarz.

Dies kann vorkommen, wenn Ihr Headset nicht bei der nativen Auflösung ausgeführt wird. Aufgrund der Art der hochauflösenden Anzeige im HP-Hash-G2-HMD können nicht alle Systeme die native Auflösung renderden. In einem zukünftigen Windows Update gibt es eine Lösung, die das Renderingproblem behandelt, wenn das Headset nicht in der nativen Auflösung vorliegt.

Es gibt einige Gründe, warum das System nicht in der Lage ist, bei der nativen Auflösung zu Rendering:

- Der DisplayPort auf dem System ist möglicherweise nicht 1,3-kompatibel, oder es werden nicht alle vier Bereiche unterstützt.
- Wenn Sie einen Adapter verwenden, wird möglicherweise HBR3 nicht unterstützt, oder es werden nicht alle vier Bereiche unterstützt.
- Wenn Ihr System über eine hybride GPU verfügt, kann dies die für den DisplayPort verfügbare Bandbreite einschränken.

## <a name="why-are-my-hp-motion-controller-models-not-showing-up-correctly-in-a-game"></a>Warum werden meine HP Motion Controller-Modelle in einem Spiel nicht richtig angezeigt?

Während bei den meisten spielen die Controller nicht angezeigt werden oder die vom Treiber installierten Modelle verwendet werden, verwenden einige Spiele ihre eigenen Versionen der Controller Modelle, um Sie anzupassen oder um die kontextbezogene Hilfe für die verfügbaren Eingaben anzuzeigen. In der Regel werden dadurch keine Features der Spiele blockiert. Dies kann jedoch zu Verwirrung oder sogar visuellen Artefakten führen. Dies kann nur mit einem Update des Spiels selbst korrigiert werden.

## <a name="my-steamvr-games-dont-appear-to-work-correctly-with-my-hp-motion-controllers"></a>Meine steamvr-Spiele scheinen nicht ordnungsgemäß für meine HP Motion-Controller zu funktionieren.

Während Entwickler daran arbeiten, ihre Spiele für die Kompatibilität mit HP Motion Controller zu aktualisieren, haben wir benutzerdefinierte Controller Bindungen für viele der beliebtesten Spiele im Stream bereitgestellt. Wenn "Windows Mixed Reality for steamvr" vollständig auf Version 1.2.444 aktualisiert wurde, sollten diese Bindungen automatisch abgerufen werden, wenn das Spiel ausgeführt wird. Wenn Ihr Spiel ihre Aktionen zu diesem Zeitpunkt jedoch nicht registrieren sollte, können Sie mithilfe des Menüs "steamvr-Einstellungen" manuell nach benutzerdefinierten Bindungs Profilen suchen.
Aufgabe

- Öffnen Sie das Menü "steamvr" durch Drücken der Menü Schaltfläche des rechten Bewegungs Controllers.
- Wählen Sie das Symbol "Einstellungen" in der unteren rechten Ecke des Menü "steamvr" aus.
- Wählen Sie die Registerkarte "controller" aus.
- Wählen Sie die Option "Controller Bindungen verwalten" aus.

Von hier aus können Sie die aktive Controller Bindung in "Custom" (Benutzer definiert) ändern. Dadurch wird die Option zum Ausprobieren der von der Community gemeinsam genutzten Spiel Bindungen geöffnet.
Wenn noch keine benutzerdefinierten Spiel Bindungen für dieses Spiel freigegeben wurden (oder wenn Sie mit den versuchen nicht vollständig zufrieden sind), können Sie auch eigene benutzerdefinierte Spiel Bindungen erstellen und sogar den Rest der Community unterstützen, indem Sie Sie nach einigen Spielsitzungen freigeben.

## <a name="i-have-all-cables-connected-to-the-headset-and-pc-but-it-wont-turn-on"></a>Ich verfüge über alle Kabel, die mit dem Headset und dem PC verbunden sind, aber nicht einschalten.

Vergewissern Sie sich, dass das mit dem Headset verbundene Kabel vollständig sitzt. Am oberen Rand des Kabels wird ein kleiner Punkt angezeigt, der sich neben dem oberen Rand des Headsets befindet, wenn er vollständig eingefügt wurde:

![Kleiner Punkt am oberen Rand des Kabels](images/small-dot.jpg)

## <a name="how-can-i-power-down-the-headset-while-still-using-my-pc"></a>Wie kann ich das Headset ausschalten, während mein PC weiterhin verwendet wird

Deinstallieren Sie den AC-Verbindungs Adapter aus dem Linkfeld des Headset-Kabels, um die Stromversorgung für das Headset zu entfernen.

## <a name="the-image-of-the-displays-of-the-reverb-g2-is-smaller-and-only-in-the-upper-left"></a>Das Bild der Anzeige des Reverb-G2 ist kleiner und nur in der linken oberen Ecke.

Wenn Sie über eine AMD-Power GPU verfügen, müssen Sie die automatische upskalierung deaktivieren. Wenn Ihr Headset verbunden ist, navigieren Sie zu Einstellungen-> gemischte Reality->->-Auflösung.
Wählen Sie im Dropdown Menü die Option "4320 x 2160 (beste Qualität)" aus. Wenn "Automatische uploadskalierung (beste Leistung)" ausgewählt ist, kann das Problem mit der Anzeige angezeigt werden.
