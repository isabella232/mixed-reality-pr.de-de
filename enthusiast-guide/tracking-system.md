---
title: Funktionsweise von Inside-Out-Tracking
description: Informationen zum kamerabasierten Inside-Out-Nachverfolgungssystem, das in Windows Mixed Reality verwendet wird.
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, inside-out, inside out, tracking, camera
ms.openlocfilehash: 579ef23c1eca2c184d07878c4e71ce298c5ad9922255b5e43643458a256b61bf
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197864"
---
# <a name="inside-out-tracking"></a>Inside-Out-Tracking

## <a name="how-does-inside-out-tracking-work"></a>Wie funktioniert die Inside-Out-Nachverfolgung?

**Schnelle Antwort: Das** Nachverfolgungssystem verwendet zwei kameras mit sichtbarem Licht und niedriger Auflösung, um Merkmale in Ihrer Umgebung zu beobachten. Die Kameras verbinden die Informationen dann mit IMU-Daten, um eine genaue Position des Geräts in Ihrer Umgebung zu bestimmen.

**Weitere Informationen:** Das Nachverfolgungssystem verwendet zwei schwarz-weiße Kameras mit niedriger Auflösung, um Merkmale in Ihrer Umgebung in sichtbarem Licht zu identifizieren. Das System trianguliert seine Position basierend auf den beobachteten Merkmalen, die dann die Informationen ergänzen, indem imU-Daten mit hoher Rate verfingt werden, um eine kontinuierliche Posenschätzung für das HMD in Ihrer Umgebung zu erstellen. Die Positionsinformationen werden von beiden Anwendungen verwendet, um eine Szene zu rendern, und vom System, um dieses Rendering zu korrigieren, um fehlgeleitete Vorhersagen in Zeit und Position zu treffen. Ihr PC speichert Umgebungsinformationen, damit das Nachverfolgungssystem umgebungsspezifische Daten wie die Raumgrenzen des physischen Standorts zurückrufen kann. Wenn Sie Ihr Gerät in mehreren Räumen verwenden, können Sie in jedem Raum unterschiedliche Grenzen einrichten, und das Nachverfolgungssystem kann die spezifische Grenze für den jeweiligen Raum zurückrufen.

Da die Nachverfolgung Windows Mixed Reality immersiven Headsets wie die Nachverfolgung auf Microsoft HoloLens [funktioniert,](https://www.microsoft.com/en-us/hololens)finden Sie dieses Video möglicherweise nützlich:

>[!VIDEO https://www.youtube.com/embed/TneGSeqVAXQ]

## <a name="what-do-i-need-to-make-tracking-work-well"></a>Was muss ich tun, damit die Nachverfolgung gut funktioniert?

Es gibt zwei Bedenken, um sicherzustellen, dass die Nachverfolgung für Sie gut funktioniert:
1. Stellen Sie sicher, dass Ihr PC die Anforderungen für die Ausführung Windows Mixed Reality. Wenn Ihr PC die Mindestanforderungen für die Windows Mixed Reality erfüllt, hat die Nachverfolgung genügend Ressourcen, um gut auf Ihrem PC ausgeführt zu werden.
2. Stellen Sie sicher, dass Ihre Umgebung für die Art der visuellen Nachverfolgung geeignet ist, die das Gerät verwendet. Sie sollten das Gerät in einer Umgebung mit ausreichend Licht verwenden. Da das Gerät ihre Umgebung in sichtbarem Licht beobachtet, muss ausreichend Licht vorhanden sein, damit die Umgebung beobachtet werden kann. Es muss auch genügend unterscheidungsreiche visuelle Merkmale (d. h.Dekorationen, Kontrastpunkte und so weiter) geben, damit das Nachverfolgungssystem funktioniert.

## <a name="how-much-light-is-enough-light"></a>Wie viel Licht ist ausreichend Licht?

Wenn Sie sich problemlos in der Umgebung bewegen können, ohne das Gefühl zu haben, dass es zu dunkel ist, und wenn Sie die Merkmale eines anderen Personengesichts von überall im Raum beobachten können, hat das Nachverfolgungssystem wahrscheinlich genügend Licht. Denken Sie daran, dass es zu viel Licht gibt. Wenn Sie direkt auf die Sun blicken, können die Kameras übersättigt werden und nicht zuverlässig nachverfolgen. 

## <a name="what-is-the-recommended-number-of-environmental-features"></a>Wie viele Umgebungsfeatures werden empfohlen?

Das Produkt wurde für normale Umgebungen entwickelt. Betrachten Sie das folgende Denkexperiment: Wenn Sie sich in einem leeren Raum mit weißen Wänden, einer weißen Decke und einem weißen Boden befinden, würde das Nachverfolgungssystem keine Nachverfolgungsfeatures finden und würde fehlschlagen. Wenn Sie sich in einem Raum befingen, der mit Arbeiten und Dekorationen abgedeckt war, würde das Nachverfolgungssystem viele Features finden, die nachverfolgt werden können und gut funktionieren würden. In der Regel wurde gezeigt, dass in der Regel eingerichtete Heime und Büros über ausreichende Featuredetails verfügen, um eine gute Nachverfolgung zu bieten.

## <a name="how-fast-can-i-move-with-the-device"></a>Wie schnell kann ich mich mit dem Gerät bewegen?

Das Gerät ist so konzipiert, dass es bewegungen unterstützt, die über das liegt, was normalerweise durch menschliche Kopfbewegungen passiert. Sie können nach Be willen wechseln. Denken Sie daran, dass Sie in einem immersiven Headset ein geringeres Bewusstsein für Ihre physische Umgebung haben. Stellen Sie daher sicher, dass Sie sich in Ihrer Umgebung sicher bewegen.

## <a name="where-will-tracking-not-work"></a>Wo funktioniert die Nachverfolgung nicht?

Die Nachverfolgung funktioniert nicht in einem dunklen Raum, in dem die Kameras aufgrund von geringem Licht nicht genügend Merkmale sehen können. Die Nachverfolgung funktioniert nicht gut (oder funktioniert manchmal überhaupt nicht) in bewegten Fahrzeugen wie Flugzeugen, Bus, Zügen, Autos oder Aufzügen. Die Nachverfolgung kann auch in Situationen fehlschlagen, in denen zu viel Licht oder ein starker Lichtunterschied vorfällt. Wenn beispielsweise ein direkter Strom von Strömen in einen Raum vor sich geht, können die Kameras die Belichtung verringern, um die Sättigung zu verringern, und es werden keine regulären natürlichen Merkmale mehr zu sehen sein. Es wird empfohlen, sich an relativ gleichmäßige Beleuchtung zu halten, und wenn Sie etwas unkomprimiert oder unüblich hell finden müssen, funktioniert das Nachverfolgungssystem möglicherweise nicht gut. 

## <a name="what-is-the-difference-between-3dof-and-6dof"></a>Was ist der Unterschied zwischen 3DOF und 6DOF?

Erstens ist DOF kurz für "Grad der Freiheit". Bei der Diskussion über Nachverfolgungssysteme bedeutet dies die Grade oder Arten von Bewegungen, die erkannt werden können. Diese Bewegungen sind in zwei Hauptkategorien unterteilt: "Drehung" und "Drehung mit Übersetzung". 3DOF bezieht sich auf 3 Grad an Freiheit und stellt Drehungen um jede Achse dar. Einfach ausgedrückt: Mit der 3DOF-Nachverfolgung können Sie nach links/rechts, nach oben/unten suchen und den Kopf (Roll) an die Seite neigen. Sie können 3DOF nicht übersetzen oder vorwärts/rückwärts gehen. 6DOF ist kurz für 6 Grad an Freiheit. Er baut auf den Drehungen von 3DOF auf und fügt übersetzungen hinzu. Dies bedeutet, dass Sie vorwärts/rückwärts, nach links/rechts und nach unten und nach unten gehen und aufstehen können. Drei DOF-Trackings sind die Art der Nachverfolgung, die Sie in der Regel auf einem Smartphone oder einem mobilen VR-Produkt finden würden, während 6DOF auf leistungsfähigeren VR-Plattformen zu finden ist. Einige Erfahrungen sind auf 3DOF zugeschnitten und lassen nur 3DOF-Bewegung (Drehungen) zu, auch wenn das Gerät die 6DOF-Nachverfolgung unterstützt. Ein Beispiel hierfür wäre das Ansehen eines 360-Videos in Windows Mixed Reality. Im Video können Sie sich umschauen, aber sie können nicht in Ihrer Umgebung arbeiten.

## <a name="things-are-jittering-or-stuttering-in-my-headset-is-my-tracking-not-working"></a>Die Dinge sind jitternd oder versäumend in meinem Headset. Funktioniert meine Nachverfolgung nicht?

Es gibt einige Fehlerquellen dieser Art. Es ist wichtig, das, was Sie beobachten, der richtigen Ursache zu attributen, damit es behoben werden kann. Informationen [dazu, warum](tracking.md) dies passieren kann, finden Sie im Abschnitt zur Problembehandlung.

## <a name="can-i-bring-my-own-tracking-technology-to-windows-mixed-reality"></a>Kann ich meine eigene Nachverfolgungstechnologie für Windows Mixed Reality?

Diese Funktionalität wird derzeit nicht unterstützt.

## <a name="why-do-i-see-ui-that-says-cant-find-your-boundary"></a>Warum wird die Benutzeroberfläche angezeigt, die besagt, dass Sie Ihre Grenze nicht finden können?

Da die Sicherheitsgrenze für einen physischen Standort spezifisch ist, kann das System die Begrenzungen nicht finden, wenn Sie das Gerät an einem anderen Ort verwenden. Nachdem Sie Ihre Grenze eingerichtet haben, sucht das System auch dann immer nach dieser Grenze, wenn Sie das Gerät an einem anderen physischen Standort verwenden. Diese Benutzeroberfläche wird immer dann angezeigt, wenn Sie das Gerät an einem anderen Ort verwenden und noch keine Grenze an diesem Standort eingerichtet haben. Sie können Grenzen an jedem Standort einrichten, an dem Sie das Gerät verwenden, und das Gerät ruft Ihre standortspezifischen Grenzen ab.

Wenn Sie das Gerät an einem Standort verwenden, an dem Sie zuvor eine Grenze eingerichtet haben, und das Gerät es immer noch nicht finden kann, können Sie neue Begrenzungen einrichten oder alle Umgebungsdaten löschen, um alle Begrenzungen vom Gerät zu entfernen. Lesen Sie den [Abschnitt zur](tracking.md) Problembehandlung, um zu verstehen, warum das System Ihre Grenzen und Schritte zur Korrektur nicht finden kann.

## <a name="how-do-i-set-up-tracking"></a>Gewusst wie Einrichten der Nachverfolgung?

Die Nachverfolgung in Windows Mixed Reality ist einfach zu verwenden, es ist keine Infrastruktur oder Einrichtung erforderlich. Wenn Sie dies ausgewählt haben, können Sie eine virtuelle Grenze für die Verwendung einrichten. Weitere Informationen finden Sie [im Abschnitt zum Einrichten](set-up-windows-mixed-reality.md#set-up-your-room-boundary) Ihrer Grenze.

## <a name="how-do-i-clear-tracking-and-environment-data"></a>Gewusst wie klare Nachverfolgung und Umgebungsdaten?

Das Nachverfolgungssystem speichert einige Umgebungsdaten, damit es den realen physischen Standort von Dingen wie Ihren Sicherheitsgrenzes zurückrufen kann. Diese Informationen, einschließlich Ihrer Sicherheitsgrenze, können jederzeit entfernt werden. Wenn diese Informationen entfernt werden, erkennt das System Ihren Speicherplatz nicht mehr und ruft ihre Sicherheitsgrenze nicht mehr ab. Wenn Sie sicherheitsgebundene Daten nach dem Löschen der Umgebungsdaten verwenden möchten, müssen Sie sie erneut einrichten. Weitere Informationen zum Einrichten [einer neuen Grenze finden](set-up-windows-mixed-reality.md#set-up-your-room-boundary) Sie im Abschnitt einrichten Ihrer Grenze. Um alle diese Daten zu entfernen, öffnen Sie Einstellungen, navigieren Sie zu "Mixed Reality", und wählen Sie im Menü auf der linken Seite den Abschnitt Umgebung aus. Wählen Sie die Schaltfläche "Umgebungsdaten löschen" aus, um alle Umgebungs- und Nachverfolgungsdaten zu entfernen.

## <a name="see-also"></a>Siehe auch
* [Problembehandlung für das Nachverfolgungssystem](tracking.md)
* [Motion-Controller](controllers-in-wmr.md)
* [Ihre Windows Mixed Reality-Startumgebung](your-mixed-reality-home.md)
* [Verwenden von Spielen und Apps in Windows Mixed Reality](using-games-and-apps-in-windows-mixed-reality.md)
