---
title: App-Ansichten
description: 'Erfahren Sie, wie Sie die zwei Arten von Ansichten in Windows Mixed Reality-Apps verwenden: immersive Ansichten und 2D-Ansichten.'
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: immersive Ansicht, 2D-Ansicht, Slate, APP, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit
ms.openlocfilehash: b6a16fc3b1ac45d74874f37ce44a36d3e144fee8
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580104"
---
# <a name="app-views"></a>App-Ansichten

Windows-Apps können zwei Arten von Ansichten enthalten: **immersive Ansichten** und **2D-Ansichten**. Apps können zwischen den verschiedenen immersiven und 2D-Ansichten wechseln und ihre 2D-Ansichten entweder in einem Monitor als Fenster oder in einem Headset als Slate anzeigen. Apps, die mindestens eine immersive Ansicht aufweisen, werden als **Mixed Reality-apps** kategorisiert. Bei Apps, die nicht über eine immersive Vollbildansicht verfügen, handelt es sich um **2D-Apps**.

## <a name="immersive-views"></a>Immersive Ansichten

Bei der Vollbildansicht erhält Ihre Anwendung die Möglichkeit, Hologramme in der Sie umgebenden Welt zu erstellen oder den Benutzer in eine virtuelle Umgebung eintauchen zu lassen. Wenn eine app in der immersiven Ansicht gezeichnet wird, wird keine andere APP gleichzeitig gezeichnet, wenn &mdash; holograms aus mehreren apps nicht zusammengeführt werden. Durch die kontinuierliche Anpassung der Perspektive, von der Ihre APP die Szene [rendert](../develop/platform-capabilities-and-apis/rendering.md) , damit Sie den Head-Bewegungen des Benutzers entspricht, kann Ihre APP die [Welt gesperrten](coordinate-systems.md) holograms rendern. Weltweit gesperrte Hologramme bleiben an einem festgelegten Punkt in der realen Welt, oder Sie können eine virtuelle Welt, die ihre Position einnimmt, beim Verschieben eines Benutzers Rendering.

![Wenn Sie sich in einer immersiven Ansicht befinden, können Sie auf der ganzen Welt holograms platzieren.](images/designoverview-940px.jpg)<br>
*Wenn Sie sich in einer immersiven Ansicht befinden, können holograms auf der ganzen Welt platziert werden.*

Bei [hololens](/hololens/hololens1-hardware)rendert Ihre APP Ihre Hologramme auf der realen Umgebung des Benutzers. In einem [Windows Mixed Reality-immersiven Headset](../discover/immersive-headset-hardware-details.md)kann der Benutzer die reale Welt nicht sehen, sodass Ihre APP alles Rendering muss, was dem Benutzer angezeigt wird.

Die [Windows Mixed Reality-Startseite](../discover/navigating-the-windows-mixed-reality-home.md) (einschließlich Start Menü und holograms, die Sie in der Umgebung platziert haben) wird in einer immersiven Ansicht nicht angezeigt. Bei hololens leitet Cortana alle System Benachrichtigungen ein, die auftreten, während eine immersive Ansicht angezeigt wird, auf die der Benutzer mit der Spracheingabe Antworten kann.

In einer immersiven Ansicht ist Ihre APP auch für die Verarbeitung aller Eingaben verantwortlich. Die Eingabe in der gemischten Realität von Windows besteht aus [Blick](gaze-and-commit.md), Bewegung (nur hololens), [Voice-und [Motion-Controllern](motion-controllers.md) [(nur](gaze-and-commit.md#composite-gestures) immersive Headsets).

## <a name="2d-views"></a>2D-Ansichten

![Mehrere 2D-Ansichten in der Windows Mixed Reality-Startseite](images/teleportation-940px.png)<br>
*Mehrere apps mit einer 2D-Ansicht, die in der Windows Mixed Reality-Startseite platziert wird*

Eine APP mit einer 2D-Ansicht wird in der [Windows Mixed Reality-Start](../discover/navigating-the-windows-mixed-reality-home.md) Seite (manchmal als "Shell" bezeichnet) als virtuelles Slate angezeigt, das zusammen mit den App-launchern und anderen holograms gerendert wird, die der Benutzer in der Welt abgelegt hat. Der Benutzer kann dieses Slate anpassen, um es zu verschieben und zu skalieren, obwohl es bei einer Fixed-Auflösung auch immer seine Größe verbleibt. Wenn es sich bei der ersten Ansicht der App um eine 2D-Ansicht handelt, wird für den 2D-Inhalt das gleiche Slate-Element aufgefüllt, das zum Starten der APP

In einem Desktop-Headset können Sie alle universelle Windows-Plattform-Apps (UWP) ausführen, die noch heute auf dem Desktop Monitor ausgeführt werden. Diese apps Rendern bereits heute 2D-Ansichten, und ihre Inhalte werden automatisch auf einem Schiefer in der Benutzer Welt angezeigt, wenn Sie gestartet werden. 2D UWP-Apps können die **Windows. Universal** -Gerätefamilie für die Ausführung sowohl auf Desktop-Headsets als auch auf hololens als Slates ausrichten.

Eine zentrale Verwendung von 2D-Sichten zeigt ein Texteingabe Formular, das die System Tastatur verwendet. Da die Shell nicht über eine immersive Ansicht hinaus Rendering kann, muss die APP zu einer 2D-Ansicht wechseln, um die System Tastatur anzuzeigen. Apps, die Texteingaben akzeptieren möchten, müssen mit einem Textfeld zu einer 2D-Ansicht wechseln. Während dieses Textfeld den Fokus besitzt, zeigt das System die Tastatur des Systems an, sodass der Benutzer Text eingeben kann.

Eine APP kann über 2D-Ansichten sowohl auf dem Desktop Monitor als auch in einem angeschlossenen Headset auf einem Desktop-PC verfügen. Beispielsweise können Sie mit der zweiten 2D-Ansicht Edge auf dem Desktop Monitor durchsuchen, um ein Video mit dem 360-Grad zu finden. Wenn Sie das Video abspielen, startet Edge eine sekundäre immersive Ansicht im Headset, um die immersiven Videoinhalte anzuzeigen.

## <a name="see-also"></a>Weitere Informationen

* [App-Modell](app-model.md)
* [Aktualisieren von 2D-UWP-Apps für Mixed Reality](../develop/porting-apps/building-2d-apps.md)
* [Abrufen eines HolographicSpace-Objekts](../develop/native/getting-a-holographicspace.md)
* [Navigieren auf der Startseite von Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md)
* [Typen von Mixed Reality-Apps](types-of-mixed-reality-apps.md)