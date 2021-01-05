---
title: Funktionsweise von Inside-Out-Tracking
description: Informationen zum kamerabasierten, in Windows Mixed Reality verwendeten System zur Nachverfolgung.
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, Mr, Inside-Out, Inside Out, Tracking, Kamera
ms.openlocfilehash: af7553b27bec63c2ae83bed390c17e1fcf006954
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725871"
---
# <a name="inside-out-tracking"></a>Inside-Out-Tracking

## <a name="how-does-inside-out-tracking-work"></a>Funktionsweise der inneren Nachverfolgung

**Schnelle Antwort:** das nachverfolgungssystem verwendet zwei sichtbare Licht Kameras mit niedriger Auflösung, um Features in Ihrer Umgebung zu beobachten. Die Kameras verbinden die Informationen dann mit IMU-Daten, um eine genaue Position des Geräts in Ihrer Umgebung zu ermitteln.

**Weitere Details:** Das Überwachungssystem verwendet zwei Low-Auflösungen-schwarze und weiße Kameras, um Features in Ihrer Umgebung im sichtbaren Licht zu identifizieren. Das System stellt seine Position basierend auf den beobachteten Features fest, die dann die Informationen ergänzen, indem Sie hochgradig hohe IMU-Daten zusammenfassen, um eine kontinuierliche nach Schätzung für das HMD in Ihrer Umgebung zu erhalten. Die Positionsinformationen werden von beiden Anwendungen zum Rendern einer Szene und durch das System verwendet, um dieses Rendering für jede fehl Vorhersage in Zeit und Position zu korrigieren. Ihr PC speichert Umgebungs Informationen, damit das Überwachungssystem Umgebungs spezifische Daten wie den physischen Speicherort der Raum Grenzen abrufen kann. Wenn Sie Ihr Gerät in mehreren Räumen verwenden, können Sie in jedem Raum unterschiedliche Grenzen einrichten, und das Überwachungssystem kann sich die jeweilige Grenze für den jeweiligen Raum merken.

Da die Nachverfolgung auf Windows Mixed Reality-immersiven Headsets wie das Nachverfolgen von [Microsoft hololens](https://www.microsoft.com/en-us/hololens)funktioniert, ist dieses Video möglicherweise hilfreich:

>[!VIDEO https://www.youtube.com/embed/TneGSeqVAXQ]

## <a name="what-do-i-need-to-make-tracking-work-well"></a>Was muss ich tun, damit die Nachverfolgung funktioniert?

Um sicherzustellen, dass die Überwachung für Sie gut funktioniert, sind zwei Aspekte zu berücksichtigen:
1. Stellen Sie sicher, dass Ihr PC die Anforderungen zum Ausführen von Windows Mixed Reality erfüllt. Wenn Ihr PC die Mindestanforderungen für Windows Mixed Reality erfüllt, verfügt die Überwachung über genügend Ressourcen, um auf Ihrem PC gut auszuführen.
2. Stellen Sie sicher, dass Ihre Umgebung für den Typ der visuellen Nachverfolgung geeignet ist, die das Gerät verwendet. Sie sollten das Gerät in einer Umgebung mit ausreichendem Licht verwenden. Da das Gerät funktioniert, indem Sie Ihre Umgebung im sichtbaren Licht beobachten, muss ausreichend Licht vorhanden sein, damit die Umgebung beobachtet werden kann. Es müssen auch ausreichend unter Scheid Ende visuelle Features vorhanden sein (mit anderen Worten: Dekorationen, Kontrastpunkte usw.), damit das Überwachungssystem funktioniert.

## <a name="how-much-light-is-enough-light"></a>Wie viel Licht ist ausreichend hell?

Wenn Sie in der Umgebung bequem herum navigieren können, ohne dass es zu dunkel ist, und wenn Sie die Funktionen auf anderen Personen im Raum sehen können, verfügt das Überwachungssystem wahrscheinlich über ausreichend Licht. Denken Sie daran, dass es zu viel Licht gibt. Wenn Sie die Sonne direkt betrachten, können die Kameras satt werden und werden nicht zuverlässig nachverfolgt. 

## <a name="what-is-the-recommended-number-of-environmental-features"></a>Was ist die empfohlene Anzahl von Umgebungs Features?

Das Produkt ist so konzipiert, dass es in normalen Umgebungen funktioniert. Sehen Sie sich das folgende Denk Experiment an: Wenn Sie sich in einem leeren Raum mit weißen Wänden, einer weißen Oberfläche und einem weißen Boden befanden, würde das Überwachungssystem keine Features finden, die nachverfolgt werden können und fehlschlagen. Wenn Sie sich in einem Raum befanden, der in der Kunst Arbeit und-Dekoration abgedeckt war, würde das Überwachungssystem viele Features finden, die Sie nachverfolgen und gut funktionieren würden. In der Regel wurden in der Regel die in der Regel ergänzten Häuser und Niederlassungen mit ausreichenden Featuredetails veranschaulicht,

## <a name="how-fast-can-i-move-with-the-device"></a>Wie schnell kann ich mit dem Gerät wechseln?

Das Gerät ist für die Unterstützung von Bewegung konzipiert, die über das, was normalerweise von der menschlichen Kopfbewegung verfügt, hinausgeht Sie können sich jederzeit bewegen. Denken Sie daran, dass Sie das Bewusstsein ihrer physischen Umgebung in einem immersiven Headset reduziert haben. Stellen Sie also sicher, dass Sie sicher in Ihrer Umgebung arbeiten.

## <a name="where-will-tracking-not-work"></a>Wo funktioniert die Überwachung nicht?

Die Nachverfolgung funktioniert nicht in einem dunklen Raum, in dem die Kameras aufgrund von geringem Licht nicht genügend Features sehen können. Die Nachverfolgung funktioniert nicht (oder manchmal überhaupt), wenn Fahrzeuge wie Flugzeuge, Busse, Wagen, Fahrzeuge oder Aufzüge verschoben werden. Die Nachverfolgung kann auch fehlschlagen, wenn es zu viel Licht oder einen starken leichten Unterschied gibt. Wenn z. b. ein direkter Strom von Sonnen Sonnen in einem Raum vorhanden ist, können die Kameras den Bedarf verringern, um die Sättigung zu verringern, und es werden keine regulären Natur Features angezeigt. Es wird empfohlen, dass Sie sich auf eine relativ gleichmäßige Beleuchtung beschränken, und wenn Sie Dinge ungemütlich hervorheben müssen, ist das Überwachungssystem möglicherweise nicht gut geeignet. 

## <a name="what-is-the-difference-between-3dof-and-6dof"></a>Worin besteht der Unterschied zwischen 3DOF und 6DOF?

Zuerst ist DOF für "Freiheitsgrade" eine kurze Hand. Bei der Erörterung von Überwachungssystemen ist dies der Grad oder die Art der Bewegung, die erkannt werden können. Diese Bewegungen sind in zwei Hauptkategorien unterteilt: "Rotation" und "Rotation mit Übersetzung". 3DOF bezieht sich auf drei Freiheitsgrade und stellt Drehungen zu jeder Achse dar. Einfach ausgedrückt: die 3DOF-Nachverfolgung ermöglicht Ihnen die Suche nach links/rechts, nach oben/unten und das Kippen ihrer Kopfzeile (Roll) nebeneinander. Sie können in 3DOF nicht übersetzen oder vorwärts/rückwärts gehen. 6DOF ist für 6 Grad an Freiheit kurz. Es baut auf der Drehung von 3DOF auf und fügt diese Übersetzungen hinzu. Dies bedeutet, dass Sie vorwärts/rückwärts gehen, die nach links/rechts einspielen und sich sichern und einspielen können. Der Typ der Nachverfolgung, die Sie in der Regel auf einem Telefon oder einem mobilen mobilen VR-Produkt finden würden, ist drei. Einige Erfahrungen sind auf 3DOF zugeschnitten und lassen nur 3DOF Motion (Drehungen) zu, auch wenn das Gerät die Nachverfolgung von 6DOF unterstützt. Ein Beispiel hierfür wäre das sehen eines 360-Videos in Windows Mixed Reality. Das Video ermöglicht Ihnen, sich anzusehen, aber Sie können nicht in Ihrer Umgebung arbeiten.

## <a name="things-are-jittering-or-stuttering-in-my-headset-is-my-tracking-not-working"></a>Die Dinge sind JITing oder Stottern erfüllt in meinem Headset. Funktioniert meine Nachverfolgung nicht?

Es gibt eine Reihe von Quellen für diese Art von Fehler. Es ist wichtig, zu berücksichtigen, was Sie in der richtigen Ursache beobachten, damit Sie möglicherweise behoben wird. Informationen dazu, warum dies möglich ist, finden Sie im Abschnitt zur [Problem](tracking.md) Behandlung.

## <a name="can-i-bring-my-own-tracking-technology-to-windows-mixed-reality"></a>Kann ich meine eigene Überwachungstechnologie in Windows Mixed Reality bringen?

Diese Funktion wird zurzeit nicht unterstützt.

## <a name="why-do-i-see-ui-that-says-cant-find-your-boundary"></a>Warum wird die Benutzeroberfläche angezeigt, die besagt, dass ihre Grenze nicht gefunden werden kann.

Da die Sicherheitsgrenze für einen physischen Standort spezifisch ist, kann das System die Begrenzungen nicht finden, wenn Sie das Gerät an einem anderen Speicherort verwenden. Außerdem wird das System nach dem Einrichten der Grenze immer darauf achten, auch wenn Sie das Gerät an einem anderen physischen Speicherort verwenden. Diese Benutzeroberfläche wird immer dann angezeigt, wenn Sie das Gerät an einem anderen Speicherort verwenden und noch keine Grenze an diesem Standort eingerichtet haben. Sie können an jedem Speicherort, an dem Sie das Gerät verwenden, Grenzen einrichten, und das Gerät erinnert sich an Ihre ortsspezifischen Begrenzungen.

Wenn Sie das Gerät an einem Speicherort verwenden, an dem Sie zuvor eine Grenze eingerichtet haben, und das Gerät das Gerät trotzdem nicht finden kann, können Sie neue Grenzen einrichten oder alle Umgebungs Daten löschen, um alle Begrenzungen vom Gerät zu entfernen. Informationen dazu, warum das System ihre Grenzen nicht finden kann, finden Sie im Abschnitt [Problem](tracking.md) Behandlung.

## <a name="how-do-i-set-up-tracking"></a>Gewusst wie die Nachverfolgung einrichten?

Die Nachverfolgung in Windows Mixed Reality ist einfach zu verwenden, es ist keine Infrastruktur oder kein Setup erforderlich. Wenn Sie sich für entschieden haben, können Sie eine virtuelle Grenze für die Verwendung einrichten. Weitere Informationen finden Sie im Abschnitt zum [Einrichten der Grenze](set-up-windows-mixed-reality.md#set-up-your-room-boundary) .

## <a name="how-do-i-clear-tracking-and-environment-data"></a>Gewusst wie Sie die nach Verfolgungs-und Umgebungs Daten löschen?

Das Überwachungssystem speichert einige Umgebungs Daten so, dass Sie den tatsächlichen physischen Speicherort der Dinge wie Ihre Sicherheitsgrenzen abrufen können. Diese Informationen, einschließlich ihrer Sicherheitsgrenzen, können jederzeit entfernt werden. Wenn diese Informationen entfernt werden, erkennt das System Ihren Speicherplatz nicht mehr, oder Sie erinnern sich an Ihre Sicherheitsgrenzen. Wenn Sie nach dem Löschen der Umgebungs Daten Sicherheitsgrenzen verwenden möchten, müssen Sie Sie erneut einrichten. Weitere Informationen finden Sie im Abschnitt [Einrichten der Grenze](set-up-windows-mixed-reality.md#set-up-your-room-boundary) für das Einrichten einer neuen Grenze. Um alle diese Daten zu entfernen, öffnen Sie Einstellungen, navigieren Sie zu "Gemischte Realität", und wählen Sie den Abschnitt Umgebung im Menü auf der linken Seite aus. Wählen Sie die Schaltfläche "Umgebungs Daten löschen" aus, um alle Umgebungs-und Überwachungsdaten zu entfernen.

## <a name="see-also"></a>Weitere Informationen
* [Problembehandlung für das Überwachungssystem](tracking.md)
* [Motion-Controller](controllers-in-wmr.md)
* [Ihre Windows Mixed Reality-Startumgebung](your-mixed-reality-home.md)
* [Verwenden von spielen und apps in Windows Mixed Reality](using-games-and-apps-in-windows-mixed-reality.md)
