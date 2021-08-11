---
title: App-Ansichten
description: 'Erfahren Sie, wie Sie die beiden Arten von Ansichten in Windows Mixed Reality apps verwenden: immersive Ansichten und 2D-Ansichten.'
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Immersive Ansicht, 2D-Ansicht, Slate, App, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 1f779749938bfc8893f0e1f1f60c97549d30a24075b5b0926af61e2f88625b9c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115191510"
---
# <a name="app-views"></a>App-Ansichten

Windows Apps können zwei Arten von Ansichten enthalten: **immersive Ansichten** und **2D-Ansichten.** Apps können zwischen ihren verschiedenen immersiven und 2D-Ansichten wechseln und ihre 2D-Ansichten entweder auf einem Monitor als Fenster oder in einem Headset als Tafel anzeigen. Apps, die mindestens eine immersive Ansicht haben, werden als **Mixed Reality-Apps kategorisiert.** Bei Apps, die nicht über eine immersive Vollbildansicht verfügen, handelt es sich um **2D-Apps**.

## <a name="immersive-views"></a>Immersive Ansichten

Bei der Vollbildansicht erhält Ihre Anwendung die Möglichkeit, Hologramme in der Sie umgebenden Welt zu erstellen oder den Benutzer in eine virtuelle Umgebung eintauchen zu lassen. Wenn eine App in der immersiven Ansicht gezeichnen wird, wird keine andere App gleichzeitig Hologramme aus mehreren Apps zeichnen, die nicht &mdash; miteinander kombiniert werden. Indem Sie die Perspektive, aus [](../develop/platform-capabilities-and-apis/rendering.md) der Ihre App ihre Szene rendert, kontinuierlich an [](coordinate-systems.md) die Kopfbewegungen des Benutzers anpassen, kann Ihre App weltweit gesperrte Hologramme rendern. Weltweit gesperrte Hologramme bleiben an einem festen Punkt in der realen Welt oder können eine virtuelle Welt rendern, die ihre Position beim Bewegen eines Benutzers ein hält.

![In einer immersiven Ansicht können Hologramme in der Welt um Sie herum platziert werden.](images/designoverview-940px.jpg)<br>
*In einer immersiven Ansicht können Hologramme in der Welt um Sie herum platziert werden.*

Auf [HoloLens](/hololens/hololens1-hardware)rendert Ihre App ihre Hologramme über der realen Umgebung des Benutzers. Auf einem [Windows Mixed Reality immersives Headset](../discover/immersive-headset-hardware-details.md)kann der Benutzer die reale Welt nicht sehen, sodass Ihre App alles rendern muss, was dem Benutzer angezeigt wird.

Die [Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md) -Startseite (einschließlich der Startmenü und Hologramme, die Sie in der Umgebung platziert haben) wird auch in einer immersiven Ansicht nicht gerendert. Auf HoloLens leitet Cortana alle Systembenachrichtigungen weiter, die auftreten, während eine immersive Ansicht angezeigt wird, auf die der Benutzer mit Spracheingaben reagieren kann.

In einer immersiven Ansicht ist Ihre App auch für die Verarbeitung aller Eingaben verantwortlich. Die Eingabe in Windows Mixed Reality besteht [](gaze-and-commit.md)aus Anvieren, Gesten [(nur](gaze-and-commit.md#composite-gestures) HoloLens), [Voice- und Motion-Controllern [](motion-controllers.md) (nur immersive Headsets).

## <a name="2d-views"></a>2D-Ansichten

![Mehrere 2D-Ansichten, die auf der Startseite Windows Mixed Reality sind](images/teleportation-940px.png)<br>
*Mehrere Apps mit einer 2D-Ansicht, die sich um das Windows Mixed Reality befindet*

Eine App mit einer [2D-Ansicht](../discover/navigating-the-windows-mixed-reality-home.md) wird in der Windows Mixed Reality-Startseite (manchmal auch als "Shell" bezeichnet) als virtuelle Tafel angezeigt, die zusammen mit den App-Startprogramm und anderen Hologrammen gerendert wird, die der Benutzer in seiner Welt platziert hat. Der Benutzer kann diese Tafel anpassen, um sie zu verschieben und zu skalieren, obwohl sie unabhängig von ihrer Größe in einer festen Auflösung verbleibt. Wenn die erste Ansicht Ihrer App eine 2D-Ansicht ist, füllt Ihr 2D-Inhalt die gleiche Tafel aus, die zum Starten der App verwendet wurde.

In einem Desktop-Headset können Sie alle UWP-Apps (Universal Windows Platform) ausführen, die heute auf Ihrem Desktopmonitor ausgeführt werden. Diese Apps rendern bereits heute 2D-Ansichten, und ihre Inhalte werden beim Start automatisch in einer Tafel in der Welt des Benutzers angezeigt. 2D-UWP-Apps können auf die **Windows. Universelle** Gerätefamilie, die sowohl auf Desktop-Headsets als auch auf HoloLens als Slates ausgeführt werden kann.

Eine wichtige Verwendung von 2D-Ansichten ist das Anzeigen eines Texteingabeformulars, das die Systemtastatur verwendet. Da die Shell nicht über einer immersiven Ansicht gerendert werden kann, muss die App zu einer 2D-Ansicht wechseln, um die Systemtastatur zu zeigen. Apps, die Texteingaben akzeptieren möchten, müssen zu einer 2D-Ansicht mit einem Textfeld wechseln. Während dieses Textfeld den Fokus besitzt, zeigt das System die Systemtastatur an, sodass der Benutzer Text eingeben kann.

Eine App kann sowohl auf dem Desktopmonitor als auch in einem angeschlossenen Headset auf einem Desktop-PC über 2D-Ansichten verfügen. Beispielsweise können Sie Edge auf Ihrem Desktopmonitor mithilfe der 2D-Hauptansicht durchsuchen, um ein 360-Grad-Video zu finden. Wenn Sie dieses Video wieder geben, startet Edge eine sekundäre immersive Ansicht innerhalb des Headsets, um den immersiven Videoinhalt anzuzeigen.

## <a name="see-also"></a>Siehe auch

* [App-Modell](app-model.md)
* [Aktualisieren von 2D-UWP-Apps für Mixed Reality](../develop/porting-apps/building-2d-apps.md)
* [Abrufen eines HolographicSpace-Objekts](../develop/native/getting-a-holographicspace.md)
* [Navigieren auf der Startseite von Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md)
* [Typen von Mixed Reality-Apps](types-of-mixed-reality-apps.md)