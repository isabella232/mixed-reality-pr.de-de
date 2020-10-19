---
title: Funktionsweise von Inside-Out-Tracking
description: Informationen zum kamerabasierten, in Windows Mixed Reality verwendeten System zur Nachverfolgung.
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, Mr, Inside-Out, Inside Out, Tracking, Kamera
ms.openlocfilehash: a91b5fba399e9bb328fd579811a64aee03b49efd
ms.sourcegitcommit: 5eb27475f8616c9d4f95b4b386a5bd0d22f41125
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "92174334"
---
# <a name="inside-out-tracking"></a>Innere Nachverfolgung

## <a name="how-does-inside-out-tracking-work"></a>Funktionsweise der inneren Nachverfolgung

**Schnelle Antwort:** das nachverfolgungssystem verwendet zwei sichtbare Licht Kameras mit niedriger Auflösung, um Features in Ihrer Umgebung zu beobachten, und verbindet diese Informationen mit IMU-Daten, um eine genaue Position des Geräts in Ihrer Umgebung zu ermitteln.

**Weitere Details:** Das Überwachungssystem verwendet zwei Low-Resolution-schwarze und weiße Kameras, um Features in Ihrer Umgebung im sichtbaren Licht zu identifizieren. Das System untersucht seine Position basierend auf den beobachteten Features und ergänzt diese Informationen durch das Zusammenführen von IMU-Hochleistungs Daten, um eine kontinuierliche stellen Schätzung für den HMD in Ihrer Umgebung zu erhalten. Die Positionsinformationen werden von beiden Anwendungen zum Rendern einer Szene und durch das System verwendet, um dieses Rendering für jede fehl Vorhersage in Zeit und Position zu korrigieren. Informationen zu Ihrer Umgebung werden auf Ihrem PC gespeichert, damit das Überwachungssystem Umgebungs spezifische Daten, z. b. den physischen Speicherort der Grenze in Ihrem Raum, abrufen kann. Wenn Sie Ihr Gerät in mehreren Räumen verwenden, können Sie in jedem Raum unterschiedliche Grenzen einrichten, und das Überwachungssystem kann die jeweilige Grenze für den jeweiligen Raum abrufen.

Da die Nachverfolgung auf Windows Mixed Reality-immersiven Headsets wie das Nachverfolgen von [Microsoft hololens](https://www.microsoft.com/en-us/hololens)funktioniert, ist dieses Video möglicherweise hilfreich:

>[!VIDEO https://www.youtube.com/embed/TneGSeqVAXQ]

## <a name="what-do-i-need-to-make-tracking-work-well"></a>Was muss ich tun, damit die Nachverfolgung funktioniert?

Um sicherzustellen, dass die Überwachung für Sie gut funktioniert, sind zwei Aspekte zu berücksichtigen:
1. Stellen Sie sicher, dass Ihr PC die Anforderungen zum Ausführen von Windows Mixed Reality erfüllt. Wenn Ihr PC die Mindestanforderungen für Windows Mixed Reality erfüllt, verfügt die Überwachung über genügend Ressourcen, um auf Ihrem PC gut auszuführen.
2. Stellen Sie sicher, dass Ihre Umgebung für den Typ der visuellen Nachverfolgung geeignet ist, die das Gerät verwendet. Sie sollten das Gerät in einer Umgebung mit ausreichendem Licht verwenden. Da das Gerät funktioniert, indem Sie Ihre Umgebung im sichtbaren Licht beobachten, muss ausreichend Licht vorhanden sein, damit die Umgebung beobachtet werden kann. Es müssen auch ausreichend unter Scheid Ende visuelle Features vorhanden sein (mit anderen Worten: Dekorationen, Kontrastpunkte usw.), damit das Überwachungssystem funktioniert.

## <a name="how-much-light-is-enough-light"></a>Wie viel Licht ist ausreichend hell?

Eine gute Faustregel ist, wenn Sie in der Umgebung bequem herum navigieren können, ohne dass diese zu dunkel ist, und wenn Sie die Funktionen von anderen Personen über den Raum hinweg beobachten können, ist das Überwachungssystem wahrscheinlich genug Licht.

## <a name="what-is-the-recommended-amount-of-environmental-features"></a>Was ist die empfohlene Menge an Umgebungs Features?

Das Produkt ist so konzipiert, dass es in normalen Umgebungen funktioniert. Sehen Sie sich das folgende Denk Experiment an: Wenn Sie sich in einem vollständig leeren Raum (weiße Wände, weiße Obergrenze, weiße Fläche) befinden, würde das nachverfolgungssystem keine Features finden, die nachverfolgt werden können und fehlschlagen. Wenn Sie sich in einem Raum befanden, der in der Kunst Arbeit und-Dekoration abgedeckt war, würde das Überwachungssystem viele Features finden, die Sie nachverfolgen und gut funktionieren würden. In den meisten Fällen wurden in der Regel die in der Regel ergänzten Häuser und Büros mit ausreichenden Featuredetails veranschaulicht.

## <a name="how-fast-can-i-move-with-the-device"></a>Wie schnell kann ich mit dem Gerät wechseln?

Das Gerät ist für die Unterstützung von Bewegung konzipiert, die über das, was normalerweise von der menschlichen Kopfbewegung verfügt, hinausgeht Sie können sich jederzeit bewegen. Denken Sie daran, dass Sie das Bewusstsein ihrer physischen Umgebung in einem immersiven Headset reduziert haben. Stellen Sie also sicher, dass Sie in Ihrer Umgebung sicher sind.

## <a name="where-will-tracking-not-work"></a>Wo funktioniert die Überwachung nicht?

Die Nachverfolgung funktioniert nicht in einem dunklen Raum, in dem die Kameras aufgrund von geringem Licht nicht genügend Features sehen können. Die Nachverfolgung ist in der Regel nicht gut geeignet (bzw. manchmal überhaupt), wenn Fahrzeuge wie Flugzeuge, Busse, trainiert, Fahrzeuge oder Aufzüge eingesetzt werden.

## <a name="what-is-the-difference-between-3dof-and-6dof"></a>Worin besteht der Unterschied zwischen 3DOF und 6DOF?

Zuerst ist DOF für "Freiheitsgrade" eine kurze Hand. Bei der Erörterung von Überwachungssystemen ist dies der Grad oder die Art der Bewegung, die erkannt werden können. Diese Bewegungen sind in zwei Hauptkategorien unterteilt: "Rotation" und "Rotation mit Übersetzung". 3DOF bezieht sich auf drei Freiheitsgrade und stellt Drehungen zu jeder Achse dar. Einfach ausgedrückt: 3DOF Tracking ermöglicht Ihnen, nach links/rechts, nach oben oder unten zu suchen und die Kopfzeile (Roll) nebeneinander zu kippen. Sie können in 3DOF nicht übersetzen oder vorwärts/rückwärts gehen. 6DOF ist für 6 Grad an Freiheit kurz. Es baut auf der Drehung von 3DOF auf und fügt diese Übersetzungen hinzu. Dies bedeutet, dass Sie vorwärts/rückwärts, die nach links/rechts und die Bereinigung und den standbyvorgang durchlaufen können. 3 DOF-Nachverfolgung ist die Art der Nachverfolgung, die Sie in der Regel auf einem Telefon oder einem mobilen VR-Produkt finden, während 6DOF auf leistungsfähigeren VR-Plattformen zu finden ist. Einige Erfahrungen sind auf 3DOF zugeschnitten und lassen nur 3DOF Motion (Drehungen) zu, auch wenn das Gerät die Nachverfolgung von 6DOF unterstützt. Ein Beispiel hierfür wäre das sehen eines 360-Videos in Windows Mixed Reality. Das Video ermöglicht Ihnen, sich anzusehen, aber Sie können die Umgebung nicht durchlaufen.

## <a name="things-are-jittering-or-stuttering-in-my-headset-is-my-tracking-not-working"></a>Die Dinge sind JITing oder Stottern erfüllt in meinem Headset. Funktioniert meine Nachverfolgung nicht?

Es gibt eine Reihe von Quellen für diese Art von Fehler. Es ist wichtig, dass Sie in der Lage sein können, das zu überwachen, was Sie beobachten, damit es behoben werden kann. Informationen dazu, warum dies möglich ist, finden Sie im Abschnitt zur [Problem](tracking.md) Behandlung.

## <a name="can-i-bring-my-own-tracking-technology-to-windows-mixed-reality"></a>Kann ich meine eigene Überwachungstechnologie in Windows Mixed Reality bringen?

Dies wird derzeit nicht unterstützt.

## <a name="why-do-i-see-ui-that-says-cant-find-your-boundary"></a>Warum wird die Benutzeroberfläche angezeigt, die besagt, dass ihre Grenze nicht gefunden werden kann.

Da die Sicherheitsgrenze für einen physischen Standort spezifisch ist, kann das System die Begrenzungen nicht finden, wenn Sie das Gerät an einem anderen Speicherort verwenden. Außerdem wird das System nach dem Einrichten der Grenze immer darauf achten, auch wenn Sie das Gerät an einem anderen physischen Speicherort verwenden. Diese Benutzeroberfläche wird immer dann angezeigt, wenn Sie das Gerät an einem anderen Speicherort verwenden und noch keine Grenze an diesem Standort eingerichtet haben. Sie können an jedem Speicherort, an dem Sie das Gerät verwenden, Grenzen einrichten, und das Gerät erinnert sich an Ihre ortsspezifischen Grenzen.

Wenn Sie das Gerät an einem Speicherort verwenden, an dem Sie zuvor eine Grenze eingerichtet haben, und das Gerät es noch immer nicht finden kann, können Sie neue Grenzen einrichten oder alle Umgebungs Daten löschen, um alle Begrenzungen vom Gerät zu entfernen. Informationen dazu, warum das System ihre Grenzen nicht finden kann, finden Sie im Abschnitt [Problem](tracking.md) Behandlung.

## <a name="how-do-i-set-up-tracking"></a>Gewusst wie die Nachverfolgung einrichten?

Die Nachverfolgung in Windows Mixed Reality ist einfach zu verwenden. Es ist keine Infrastruktur oder kein Setup erforderlich, und das Gerät wird standardmäßig verwendet. Wenn Sie sich für entschieden haben, können Sie eine virtuelle Grenze für die Verwendung einrichten. Weitere Informationen finden Sie im Abschnitt zum [Einrichten der Grenze](set-up-windows-mixed-reality.md#set-up-your-room-boundary) .

## <a name="how-do-i-clear-tracking-and-environment-data"></a>Gewusst wie Sie die nach Verfolgungs-und Umgebungs Daten löschen?

Das Überwachungssystem speichert einige Umgebungs Daten so, dass Sie den tatsächlichen physischen Speicherort der Dinge wie Ihre Sicherheitsgrenzen abrufen können. Diese Informationen, einschließlich ihrer Sicherheitsgrenzen, können jederzeit entfernt werden. Wenn diese Informationen entfernt werden, erkennt das System Ihren Speicherplatz nicht mehr und kann Ihre Sicherheitsgrenzen nicht mehr abrufen. Wenn Sie nach dem Löschen der Umgebungs Daten Sicherheitsgrenzen verwenden möchten, müssen Sie Sie erneut einrichten. Weitere Informationen finden Sie im Abschnitt [Einrichten der Grenze](set-up-windows-mixed-reality.md#set-up-your-room-boundary) für das Einrichten einer neuen Grenze. Um alle diese Daten zu entfernen, öffnen Sie Einstellungen, navigieren Sie zu "Gemischte Realität", und wählen Sie den Abschnitt Umgebung im Menü auf der linken Seite aus. Klicken Sie auf die Schaltfläche "Umgebungs Daten löschen", um alle Umgebungs-und Überwachungsdaten zu entfernen.

## <a name="see-also"></a>Weitere Informationen
* [Problembehandlung für das Überwachungssystem](tracking.md)
* [Funktionsweise von Motion-Controllern](controller-in-wmr.md)
* [Ihre Windows Mixed Reality-Startumgebung](your-mixed-reality-home.md)
* [Verwenden von spielen und apps in Windows Mixed Reality](using-games-and-apps-in-windows-mixed-reality.md)
