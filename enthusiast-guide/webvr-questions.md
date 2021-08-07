---
title: Häufig gestellte Fragen zu WebVR
description: Bleiben Sie mit Mixed Reality Problembehandlung für Webanwendungen auf dem laufenden, die über unsere Standarddokumentation für den Kundensupport hinausgehen.
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Problembehandlung, Fehler, Hilfe, Support, WebVR
ms.openlocfilehash: d0f91af9cf14d8019707e504a9f8bc076bbe39db566895f17e1e56d6b906336d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211092"
---
# <a name="webvr-faqs"></a>Häufig gestellte Fragen zu WebVR

## <a name="why-cant-i-see-my-controllers-when-viewing-vr-content-from-edge"></a>Warum kann ich meine Controller beim Anzeigen von VR-Inhalten von Edge nicht sehen?

Nicht alle WebVR-Inhalte werden zur Unterstützung von Motion-Controllern erstellt. WebVR ermöglicht Inhaltsentwicklern die Unterstützung verschiedener Eingabetypen, z. B. Gamecontroller oder Motion-Controller. Wenn Ihre Controller an einem Standort nicht angezeigt werden, verfügt sie wahrscheinlich nicht über Motion Controller-Unterstützung.

## <a name="why-cant-i-use-the-mouse-in-an-immersive-webvr-view"></a>Warum kann ich die Maus nicht in einer immersiven WebVR-Ansicht verwenden?

Die Verwendung einer Maus ist ein optionales Feature der WebVR-Spezifikation. Nicht alle Browser unterstützen diese Funktion, und nicht alle WebVR-Inhalte werden zur Unterstützung von Mauseingaben erstellt. WebVR ermöglicht Inhaltsentwicklern die Unterstützung verschiedener Eingabetypen, z. B. Maus, Tastatur, Gamecontroller oder Motion Controller. Das Verhalten der Mauseingabe variiert je nach Browser. Innerhalb Microsoft Edge müssen Websiteautoren sicherstellen, dass sie "Pointerlock" verwenden, wenn sie das Headset präsentieren, damit die Mauseingabe funktioniert.

## <a name="why-cant-i-view-360-degree-videos-from-youtubefacebookvimeothe-guardian-etc-from-edge-in-vr"></a>Warum kann ich keine 360-Grad-Videos von Youtube/Facebook/Vimeo/The Guardian usw. von Edge in VR anzeigen?

Es gibt eine WebVR-Spezifikation, mit der Websites VR-Umgebungen direkt über den Browser starten können. Die Autoren dieser Websites haben diese Spezifikation derzeit nicht implementiert. Es gibt möglicherweise herunterladbare Apps auf einigen Plattformen, die die Anzeige von VR-Inhalten von diesen Anbietern ermöglichen.

## <a name="why-cant-i-enter-vr-from-firefox-or-chrome"></a>Warum kann ich VR nicht über Firefox oder Chrome eingeben?

WebVR wird derzeit nur von Windows Mixed Reality Geräten in Edge unterstützt.

## <a name="when-i-enter-vr-from-a-website-why-do-i-see-a-blank-screen-in-my-headset"></a>Warum wird bei der Eingabe von VR von einer Website ein leerer Bildschirm in meinem Headset angezeigt?

Die Website hat möglicherweise keine Unterstützung für mehrere GPU-Computer (einschließlich Hybrid-GPU-Laptops) implementiert. Versuchen Sie,

* Laden Sie die Seite neu.
* Schließen Sie das Headset auf Desktopcomputern an denselben Grafikkartenadapter an wie der Monitor, der Microsoft Edge anzeigt. Schließen Sie beides an die höhere Grafikkarte an, nicht an den integrierten Grafikkartenadapter.

## <a name="when-i-exit-vr-when-watching-a-video-from-edge-the-sound-continues-playing-but-the-edge-window-is-grayed-out"></a>Beim Beenden von VR beim Ansehen eines Videos von Edge wird der Sound weiterhin wiedergegeben, aber das Edge-Fenster ist abgeblendet.

Dies ist ein bekanntes Problem bei der Ausführung von WebVR über Edge im Mixed Reality Haus an den Klippen. Drücken Sie zum Beheben dieses Problems escape auf der Tastatur anstelle der Fensterschaltfläche, um die WebVR-Benutzeroberfläche zu beenden, oder aktivieren Sie das abgeblendete Edgefenster, indem Sie es auswählen und dann das Video beenden.

## <a name="can-i-use-webvr-on-the-hololens"></a>Kann ich WebVR auf der HoloLens

Microsoft hat zu diesem Zeitpunkt keine Informationen zu WebVR im HoloLens angekündigt.

## <a name="why-is-my-view-at-floor-level-when-viewing-webvr-content-from-edge"></a>Warum befindet sich meine Ansicht beim Anzeigen von WebVR-Inhalten aus Edge auf Ebene des Stockwerks?

Die Website unterstützt Windows Mixed Reality Headsets nicht ordnungsgemäß. Dieses Problem können Sie folgendermaßen umgehen:

1. Platzieren Sie das Headset auf der Etage Ihres Raumes.
2. Navigieren Sie mit Microsoft Edge auf Ihrem Desktop (nicht innerhalb von Mixed Reality) zur WebVR-Seite.
3. Wählen Sie "ENTER VR" aus.
4. Warten Sie fünf bis zehn Sekunden, bis die Benutzeroberfläche vollständig in den immersiven Modus wechselt.
5. Setzen Sie das Headset an.

## <a name="the-display-is-low-resolution-in-some-webvr-experiences"></a>Die Anzeige ist in einigen WebVR-Funktionen mit geringer Auflösung dargestellt.

Diese Websites unterstützen keine headsets mit hoher Auflösung. Dieses Problem können Sie folgendermaßen umgehen:

* Wenn Sie WebVR über den Desktop starten (anstelle der Mixed Reality-Haus an den Klippen), stellen Sie sicher, dass das Fenster maximiert ist, bevor Sie "ENTER VR" auswählen.
* Vermeiden Sie es, die Größe des Microsoft Edge Fensters zu ändern, nachdem Sie VR eingegeben haben.

## <a name="why-does-the-webvr-immersive-view-exit-when-i-change-browser-tabs"></a>Warum wird die immersive WebVR-Ansicht beendet, wenn ich Browserregisterkarten ändere?

Dieses Verhalten ist normal. Aus Sicherheitsgründen kann nur die aktive Browserregisterkarte auf verbundene Headsets zugreifen.

## <a name="why-cant-i-hear-audio-on-a-particular-webvr-experience"></a>Warum kann ich keine Audiodaten in einer bestimmten WebVR-Benutzeroberfläche hören?

Die Website verwendet möglicherweise das OGG-Audiodateiformat, das Microsoft Edge derzeit nicht unterstützt.

Sie können fehlerhafte Websites direkt an das Microsoft Edge Browserteam in der [Problemverfolgung](https://developer.microsoft.com/microsoft-edge/platform/issues/)oder über Twitter melden, indem [Sie #EdgeBug Hashtag verwenden.](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/)

## <a name="why-does-haptic-feedback-not-work-in-webvr-with-motion-controllers"></a>Warum funktioniert haptisches Feedback in WebVR nicht mit Motion-Controllern?

Microsoft Edge unterstützt derzeit keine Haptik in den WebVR-Gamepad-API-Erweiterungen.