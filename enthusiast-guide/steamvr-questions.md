---
title: Häufig gestellte Fragen zu SteamVR
description: Die Problembehandlung Windows Mixed Reality Dies geht über unsere Standarddokumentation für den Kundensupport hinaus.
author: qianwen
ms.author: v-qianwen
ms.date: 09/24/2021
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Problembehandlung, Fehler, Hilfe, Support,Vr
ms.openlocfilehash: 17ab1709e8a2fc7e3eee70082aef64f0dc23d318
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436799"
---
# <a name="steamvr-faqs"></a>Häufig gestellte Fragen zu SteamVR

## <a name="how-can-i-play-steamvr-games-in-my-windows-mixed-reality-headset"></a>Wie kann ich Games von "SteamVR" in meinem headset Windows Mixed Reality spielen?

1. [Laden Sie Den Download und die Installation von SteamVR herunter, und installieren](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe)Sie . Das Tutorial zu "SteamVR" sollte automatisch gestartet werden, wenn Sie "VrVR" starten.
2. Verbinden Ihr Headset an Ihren PC an, und schalten Sie die Motion-Controller ein.
3. Sobald Windows Mixed Reality home geladen wurde und Ihre Controller sichtbar sind, öffnen Sie die App "Steam" auf Ihrem Desktop.
4. Verwenden Sie die "Steam"-App, um ein Game "SteamVR" aus Ihrer Bibliothek "Steam" zu starten. Zum Starten von Games im Rahmen von "Alle Apps Windows Mixed Reality > starten Sie alle Apps, ohne ihr Headset zu **starten.**

## <a name="a-message-says-to-use-steamvr-with-windows-mixed-reality-you-need-to-install-the-latest-windows-update-or-windows-developer-mode-required"></a>Eine Meldung mit dem Text "Zur Verwendung von SteamVR mit Windows Mixed Reality müssen Sie das neueste Windows Update installieren" oder "Windows Developer Mode Required" (Entwicklermodus erforderlich)

1. Stellen Sie sicher, dass auf Ihrem PC die neueste Version von Windows 10 oder Windows 11 ausgeführt wird. Wechseln Sie zu Einstellungen > System > About ( System > **About),** und vergewissern Sie sich unter "Windows specifications", dass "OS Build" 16299.64 oder höher ist.
2. Stellen Sie sicher, dass keine Updates auf den Download oder die Installation warten. Wechseln Sie **zu Einstellungen > Update & Security > Windows Update,** und wählen Sie "Nach Updates suchen" aus. Möglicherweise müssen Sie mehrmals überprüfen, bis keine weiteren Updates verfügbar sind, und dann Ihren PC neu starten.

## <a name="steamvr-is-crashing-after-updating-windows"></a>Nach dem Aktualisieren des Windows

Einige ältere Versionen von Windows Mixed Reality für SteamVR sind nicht mehr mit Windows. So stellen Sie sicher, dass Ihre Version Windows Mixed Reality für SteamVR aktuell ist:

1. Wechseln Sie in Ihrer Bibliothek zu **Software > Windows Mixed Reality für SteamVR**.
2. Klicken Sie mit der rechten Maustaste darauf, und wechseln Sie zu "Eigenschaften".
3. Wählen Sie die Registerkarte "Aktualisieren" und "Diese Anwendung immer auf dem neuesten Stand halten" aus.
4. Erzwingen Sie das Update, indem Sie zur Registerkarte "Lokale Dateien" gehen und "Integrität von Anwendungsdateien überprüfen" auswählen.
5. Starten Sie "Steam" und "SteamVR" neu.

Wenn Es nach dem Update immer noch zu einem Absturz von SteamVR kommt, verfügen Sie möglicherweise über zwei Installationen von Windows Mixed Reality für SteamVR auf Ihrem Computer. So bestätigen Sie den Vorgang

1. Suchen ```%localappdata%\openvr\openvrpaths.vrpath``` und öffnen Sie es in Editor.
2. Suchen Sie in den Abschnitten "Externe Treiber" nach mehreren Einträgen für "MixedRealityVRDriver".
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver",
      "E:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
3. Wenn mehrere Einträge angezeigt werden, entfernen Sie den älteren der beiden Einträge. Wenn Sie nur einen Eintrag haben, sollte am Ende der Zeile kein Komma mehr stehen. Beispiel:
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
4. Speichern Sie die Datei, und schließen Sie sie.
5. Starten Sie "Steam" und "SteamVR" neu.

## <a name="my-controllers-arent-working-as-expected-in-steamvr"></a>Meine Controller funktionieren in "ControllersVR" nicht wie erwartet.

1. Schließen Sie "SteamVR".
2. Kehren Sie Windows Mixed Reality zurück, und vergewissern Sie sich, dass Ihre Controller funktionieren.
3. Starten Sie die Funktion "SteamVR" erneut, und Ihre Controller sollten wieder normal sein.
4. Wenn probleme weiterhin bestehen, senden Sie Feedback mithilfe Windows-Feedback-Hub [unter](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app) der kategorie Mixed Reality und schließen Sie "SteamVR" in die Zusammenfassung ein.

Sie verwenden Ihre Motion-Controller unterschiedlich in verschiedenen Spielen. Hier sind einige Grundlagen für den Einstieg:
* Drücken Sie zum Öffnen des Dashboards "Dashboard" den linken Fingerabdruck nach unten.
* Klicken Sie auf die Schaltfläche "Windows" , um ein Game vom Windows Mixed Reality zu beenden und zum Windows Mixed Reality zurückzukehren. Wählen Sie dann die Mixed Reality Startschaltfläche aus, die auf dem Bildschirm angezeigt wird.

## <a name="my-left-and-right-controllers-are-reversed-in-steamvr"></a>Mein linker und rechter Controller werden in "ControllersVR" umgekehrt.

Starten Sie das Spiel mit ausgeschalteten Controllern, und aktivieren Sie dann den linken Controller, gefolgt vom rechten Controller.

## <a name="my-games-are-running-slowly"></a>Meine Spiele werden langsam ausgeführt

1. Stellen Sie sicher, dass Ihr PC die Spezifikationen für Dies ist Windows Mixed Reality und das Spiel, das Sie spielen, erfüllt.
2. Wählen Mixed Reality-Portal Desktop auf "Anhalten" aus, um die Desktopvorschau zu beenden.
3. Wechseln Sie Einstellungen > System > About ( System > **About),** und vergewissern Sie sich unter "Windows Specifications", dass "OS Build" 16299.64 oder höher ist.
4. Stellen Sie sicher, dass Ihr PC über die neuesten Grafiktreiber verfügt ("Nach Updates suchen" in Windows Update).
5. Überprüfen Sie "Task-Manager", um zu sehen, welche anderen Prozesse Möglicherweise Ressourcen auf Ihrem PC verbrauchen.
6. Überprüfen Sie, ob Steam ein Spiel im Hintergrund herunterladt, wodurch Ressourcen verbraucht werden und Spiele schlecht ausgeführt werden.
7. Eine kleine Klasse von Apps, die über kein sichtbares Fenster verfügen (z. B. "SteamVR Home"), haben ein bekanntes Leistungsproblem. Die meisten Apps fallen nicht in diese Kategorie, und eine Lösung wird in einem zukünftigen Update verfügbar sein.

Wenn weiterhin unerwartete Leistungsprobleme auft sind, senden Sie uns feedback mithilfe der [Windows-Feedback-Hub.](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app) Stellen Sie sicher, dass Sie die Anweisungen befolgen, [um eine "Trace" für die Leistung von "Trace" (Ablaufverfolgung für die Leistung) einzulassen.](using-steamvr-with-windows-mixed-reality.md#sharing-feedback-on-steamvr)

## <a name="steamvr-is-showing-a-compositor-error-for-example-shared-ipc-compositor-connect-failed-400"></a>Bei "SteamVR" wird ein Compositorfehler angezeigt (z. B. "Shared IPC Compositor Verbinden Failed (400)").

Dies kann passieren, wenn sich Ihr Headset und der primäre Monitor auf zwei verschiedenen Grafikkarten befinden. Fügen Sie Ihren Monitor an denselben Adapter wie Ihr Headset an, und konfigurieren Sie ihn als primären Monitor in Einstellungen-App > **System > Display.**

## <a name="steamvr-content-appears-in-the-wrong-place-like-beneath-the-floor-or-above-my-head"></a>Der Inhalt von "SteamVR" wird an der falschen Stelle angezeigt, beispielsweise unter dem Boden oder über meinem Kopf.

Setzen Sie Ihre Position zurück:

1. Wählen Sie den Thumbstick des linken Controllers aus, um das Dashboard "ControllersVR" anzuzeigen.
2. Wählen Sie die Schaltfläche "Einstellungen" aus.
3. Wählen Sie "Position zurücksetzen" aus.

## <a name="my-steam-app-closed-unexpectedly"></a>My Steam app closed unexpectedly (Meine "Wasser"-App wurde unerwartet geschlossen)

Die "Steam"-App wird geschlossen, wenn:

* Sie sperren ihren PC-Bildschirm
* Entfernen Ihres Headsets
* Wechseln von Benutzern
* Ihr PC geht in den Ruhezustand
