---
title: Webvr-FAQs
description: Erweiterte Windows Mixed Reality-Problembehandlung, die über die standardmäßige Kundensupport Dokumentation hinausgeht.
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, Mr, Problembehandlung, Fehler, Hilfe, Support, webvr
ms.openlocfilehash: 8bc7ab010c1f6ebddf899262b09ba1d08f4ab3ae
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2020
ms.locfileid: "91685622"
---
# <a name="webvr-faqs"></a>Webvr-FAQs

## <a name="why-cant-i-see-my-controllers-when-viewing-vr-content-from-edge"></a>Warum werden meine Controller nicht angezeigt, wenn Sie den VR-Inhalt von Edge anzeigen?

Nicht alle webvr-Inhalte werden zur Unterstützung von Bewegungs Controllern erstellt. Webvr ermöglicht Inhalts Entwicklern die Unterstützung verschiedener Eingabetypen, z. b. Spiele Controller oder Bewegungs Controller. Wenn Ihre Controller an einem Standort nicht angezeigt werden, ist die Unterstützung von Motion Controller wahrscheinlich nicht vorhanden.

## <a name="why-cant-i-use-the-mouse-in-an-immersive-webvr-view"></a>Warum kann ich die Maus nicht in einer immersiven webvr-Ansicht verwenden?

Dies ist ein optionales Feature der webvr-Spezifikation. Diese Funktion wird nicht von allen Browsern unterstützt, und nicht alle webvr-Inhalte werden zur Unterstützung von Maus Eingaben erstellt. Webvr ermöglicht Inhalts Entwicklern die Unterstützung verschiedener Eingabetypen, z. b. Maus, Tastatur, Spiele Controller oder Bewegungs Controller. Das Verhalten der Maus Eingaben variiert je nach Browser. Innerhalb von Microsoft Edge müssen Website Autoren sicherstellen, dass Sie "pointerlock" verwenden, wenn Sie dem Headset präsentieren, damit die Maus Eingaben funktioniert.

## <a name="why-cant-i-view-360-degree-videos-from-youtubefacebookvimeothe-guardian-etc-from-edge-in-vr"></a>Warum kann ich keine Videos mit 360-Grad-Videos von YouTube/Facebook/Vimeo/dem Wächter usw. von Edge in VR anzeigen?

Es gibt eine webvr-Spezifikation, die es Websites ermöglicht, VR-Erlebnisse direkt aus dem Browser zu starten, und die Autoren dieser Websites haben diese Spezifikation zu diesem Zeitpunkt nicht implementiert. Möglicherweise können apps auf einigen Plattformen heruntergeladen werden, die die Anzeige von VR-Inhalten von diesen Anbietern ermöglichen.

## <a name="why-cant-i-enter-vr-from-firefox-or-chrome"></a>Warum kann ich VR aus Firefox oder Chrome nicht eingeben?

Webvr wird zurzeit nur von Windows Mixed Reality-Geräten in Edge unterstützt.

## <a name="when-i-enter-vr-from-a-website-why-do-i-see-a-blank-screen-in-my-headset"></a>Warum wird bei der Eingabe von VR von einer Website ein leerer Bildschirm in meinem Headset angezeigt?

Die-Website hat möglicherweise keine Unterstützung für multigpu-Computer (einschließlich hybridgpu-Laptops) implementiert. Versuchen Sie Folgendes:
* Laden Sie die Seite neu.
* Binden Sie das Headset auf Desktop Computern an denselben Grafikadapter wie den Monitor, der Microsoft Edge anzeigt. Verbinden Sie beide mit der höher gestützten Grafikkarte, nicht mit dem integrierten Grafikadapter.

## <a name="when-i-exit-vr-when-watching-a-video-from-edge-the-sound-continues-playing-but-the-edge-window-is-grayed-out"></a>Beim Beenden von VR beim Anschauen eines Videos von Edge wird der Sound weiterhin abgespielt, aber das Fenster Edge ist ausgegraut.

Dies ist ein bekanntes Problem beim Ausführen von webvr von Edge im Mixed Reality-Klippe-Haus. Um dieses Problem zu beheben, drücken Sie auf der Tastatur die Tastenkombination, anstatt die Windows-Taste zu drücken, um die webvr-Oberfläche zu beenden, oder aktivieren Sie das ausgelöerte Rand Fenster, indem Sie es auswählen und das Video beenden

## <a name="can-i-use-webvr-on-the-hololens"></a>Kann ich webvr auf den hololens verwenden?

Microsoft hat an dieser Stelle noch nichts über webvr in den hololens angekündigt.

## <a name="why-is-my-view-at-floor-level-when-viewing-webvr-content-from-edge"></a>Warum wird meine Ansicht beim Anzeigen von webvr-Inhalten von Edge auf der Floor-Ebene angezeigt?

Die Website unterstützt Windows Mixed Reality-Headsets nicht ordnungsgemäß. Dieses Problem können Sie folgendermaßen umgehen:
1. Platzieren Sie das Headset in der Etage Ihres Leerraums.
2. Navigieren Sie zur webvr-Seite mithilfe von Microsoft Edge auf Ihrem Desktop (nicht innerhalb gemischter Realität).
3. Wählen Sie "Enter VR" aus.
4. Warten Sie fünf bis 10 Sekunden, bis die Darstellung vollständig in den immersiven Modus wechselt.
5. Auf dem Headset ablegen.

## <a name="the-display-is-very-low-resolution-in-some-webvr-experiences"></a>Die Anzeige ist bei einigen webvr-Erfahrungen sehr gering.

Diese Websites unterstützen keine großen Lösungen mit hoher Auflösung. So umgehen Sie dieses Problem:
* Wenn Sie webvr über den Desktop starten (anstelle des "Mixed Reality"-Klippe), stellen Sie sicher, dass das Fenster maximiert ist, bevor Sie "Enter VR" auswählen.
* Vermeiden Sie das Ändern der Größe des Microsoft Edge-Fensters, nachdem Sie VR eingegeben haben.

## <a name="why-does-the-webvr-immersive-view-exit-when-i-change-browser-tabs"></a>Warum wird die webvr-immersive Ansicht beendet, wenn ich Browser Registerkarten ändere?

Dieses Verhalten wird erwartet. Aus Sicherheitsgründen kann nur die Registerkarte Active Browser auf verbundene Headsets zugreifen.

## <a name="why-cant-i-hear-audio-on-a-particular-webvr-experience"></a>Warum kann ich Audiodaten zu einem bestimmten webvr-Erlebnis nicht hören?

Die Website verwendet möglicherweise das Format der OGG-Audiodatei, das Microsoft Edge derzeit nicht unterstützt.

Sie können fehlerhafte Websites direkt an das Microsoft Edge-Browser Team in der [Problem](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)Verfolgung oder per Twitter über [#EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/)Berichten.

## <a name="why-does-haptic-feedback-not-work-in-webvr-with-motion-controllers"></a>Warum funktioniert das haptische Feedback nicht in webvr mit Motion-Controllern?

Microsoft Edge unterstützt zurzeit keine Haptik in den webvr-Gamepad-API-Erweiterungen.

