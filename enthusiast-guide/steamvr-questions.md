---
title: Häufig gestellte Fragen zu SteamVR
description: Die Problembehandlung von SteamVR Windows Mixed Reality, die über unsere Standarddokumentation zur Kundenunterstützung hinausgeht.
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Problembehandlung, Fehler, Hilfe, Support, SteamVR
ms.openlocfilehash: 0fb9c07dda8fe354966403bc9c6a21acb600e61cb943c270eb9c87f5ec2fb89a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115199496"
---
# <a name="steamvr-faqs"></a>Häufig gestellte Fragen zu SteamVR

## <a name="how-can-i-play-steamvr-games-in-my-windows-mixed-reality-headset"></a>Wie kann ich SteamVR-Spiele in meinem Windows Mixed Reality Headset spielen?

1. [Laden Sie SteamVR herunter, und installieren Sie](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe)es. Das Tutorial zu SteamVR sollte automatisch gestartet werden, wenn Sie SteamVR starten.
2. Verbinden Ihr Headset an Ihren PC, und schalten Sie Ihre Motion-Controller ein.
3. Nachdem Windows Mixed Reality Home geladen wurde und Ihre Controller sichtbar sind, öffnen Sie die Steam-App auf Ihrem Desktop.
4. Verwenden Sie die Steam-App, um ein SteamVR-Spiel aus Ihrer Steam-Bibliothek zu starten. Um Die Spiele von SteamVR zu starten, ohne ihr Headset zu starten, suchen und starten Sie sie unter start Windows Mixed Reality es **Start > All Apps (Starten > Alle Apps).**

## <a name="a-message-says-to-use-steamvr-with-windows-mixed-reality-you-need-to-install-the-latest-windows-update-or-windows-developer-mode-required"></a>In einer Meldung wird folgende Meldung angezeigt: "Um SteamVR mit Windows Mixed Reality verwenden zu können, müssen Sie das neueste Windows Update installieren" oder "Windows Developer Mode Required" (Windows Developer Mode Required)

1. Stellen Sie sicher, dass auf Ihrem PC die neueste Version von Windows 10 ausgeführt wird. Wechseln Sie zu **Einstellungen > System > About**,, und stellen Sie unter "Windows Specifications" sicher, dass "Betriebssystembuild" 16299.64 oder höher ist.
2. Stellen Sie sicher, dass sie keine Updates haben, die auf den Download oder die Installation warten. Wechseln Sie zu **Einstellungen > Update & Security > Windows Update,** und wählen Sie "Nach Updates suchen" aus. Möglicherweise müssen Sie mehrmals überprüfen, bis keine weiteren Updates verfügbar sind, und dann Ihren PC neu starten.

## <a name="steamvr-is-crashing-after-updating-windows"></a>Nach dem Aktualisieren von Windows stürzt Dies ist ein Absturz von SteamVR.

Einige ältere Versionen von Windows Mixed Reality für SteamVR sind nicht mehr mit Windows kompatibel. So stellen Sie sicher, dass Ihre Version von Windows Mixed Reality für SteamVR aktuell ist:

1. Wechseln Sie in Ihrer Steam-Bibliothek zu **Software > Windows Mixed Reality for SteamVR**.
2. Klicken Sie mit der rechten Maustaste darauf, und wechseln Sie zu "Eigenschaften".
3. Wählen Sie die Registerkarte "Aktualisieren" und "Diese Anwendung immer auf dem neuesten Stand halten".
4. Erzwingen Sie das Update, indem Sie auf die Registerkarte "Lokale Dateien" klicken und "Integrität der Anwendungsdateien überprüfen" auswählen.
5. Starten Sie "Steam" und "SteamVR" neu.

Wenn Das SteamVR nach dem Update weiterhin abstürzt, verfügen Sie möglicherweise über zwei Installationen von Windows Mixed Reality für SteamVR auf Ihrem Computer. So bestätigen Sie den Vorgang

1. Suchen ```%localappdata%\openvr\openvrpaths.vrpath``` sie in Editor, und öffnen Sie sie.
2. Suchen Sie in den Abschnitten "Externe Treiber" nach mehreren Einträgen für "MixedRealityVRDriver".
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver",
      "E:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
3. Wenn mehrere Einträge angezeigt werden, entfernen Sie den älteren der beiden Einträge. Sobald Sie nur über einen Eintrag verfügen, sollte am Ende der Zeile kein Komma mehr vorhanden sein. Beispiel:
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
4. Speichern Sie die Datei, und schließen Sie sie.
5. Starten Sie "Steam" und "SteamVR" neu.

## <a name="my-controllers-arent-working-as-expected-in-steamvr"></a>Meine Controller funktionieren in SteamVR nicht wie erwartet.

1. Schließen Sie "SteamVR".
2. Kehren Sie zu Windows Mixed Reality Startseite zurück, und vergewissern Sie sich, dass Ihre Controller funktionieren.
3. Starten Sie die SteamVR-Benutzeroberfläche erneut, und Ihre Controller sollten wieder normal sein.
4. Wenn Probleme weiterhin auftreten, senden Sie Feedback mithilfe des [Windows-Feedback-Hub](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app) unter der Kategorie Mixed Reality, und schließen Sie SteamVR in die Zusammenfassung ein.

Sie verwenden Ihre Motion-Controller in verschiedenen Spielen unterschiedlich. Im Folgenden finden Sie einige Grundlegendes zu den ersten Schritte:
* Um das Dashboard "Steam" zu öffnen, drücken Sie direkt nach unten auf den linken Stick.
* Klicken Sie auf die Schaltfläche Windows, um ein Game vom Windows Mixed Reality zu beenden. Wählen Sie dann die Mixed Reality Schaltfläche Start aus, die auf dem Bildschirm angezeigt wird.

## <a name="my-left-and-right-controllers-are-reversed-in-steamvr"></a>Meine linken und rechten Controller werden in SteamVR umgekehrt.

Starten Sie das Spiel mit den Controllern aus, und aktivieren Sie dann den linken Controller, gefolgt vom rechten Controller.

## <a name="my-games-are-running-slowly"></a>Meine Spiele werden langsam ausgeführt.

1. Stellen Sie sicher, dass Ihr PC die Spezifikationen für SteamVR in Windows Mixed Reality und dem Spiel, das Sie spielen, erfüllt.
2. Wählen Sie in Mixed Reality-Portal auf Ihrem Desktop "Anhalten" aus, um die Desktopvorschau zu beenden.
3. Wechseln Sie zu **Einstellungen > System > About** ,, und stellen Sie unter "Windows Specifications" sicher, dass "Betriebssystembuild" 16299.64 oder höher ist.
4. Stellen Sie sicher, dass Ihr PC über die neuesten Grafiktreiber verfügt ("Nach Updates suchen" in Windows Update).
5. Überprüfen Sie "Task-Manager", um zu sehen, welche anderen Prozesse Ressourcen auf Ihrem PC verbrauchen.
6. Überprüfen Sie, ob Steam ein Spiel im Hintergrund herunterlädt, wodurch Ressourcen verbraucht und Spiele schlecht ausgeführt werden.
7. Eine kleine Klasse von Apps ohne sichtbares Fenster (z. B. "SteamVR Home") hat ein bekanntes Leistungsproblem. Die meisten Apps fallen nicht in diese Kategorie, und eine Korrektur wird in einem zukünftigen Update verfügbar sein.

Wenn weiterhin unerwartete Leistungsprobleme auftreten, senden Sie uns feedback über die [Windows-Feedback-Hub](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app). Befolgen Sie die Anweisungen, um eine Ablaufverfolgung für die Leistung von [SteamVR einzufügen.](using-steamvr-with-windows-mixed-reality.md#sharing-feedback-on-steamvr)

## <a name="steamvr-is-showing-a-compositor-error-for-example-shared-ipc-compositor-connect-failed-400"></a>"SteamVR" zeigt einen Compositorfehler an (z.B. "Shared IPC Compositor Verbinden Failed (400)").

Dies kann passieren, wenn sich Ihr Headset und ihr primärer Monitor auf zwei verschiedenen Grafikkarten befinden. Fügen Sie ihren Monitor an den gleichen Adapter wie Ihr Headset an, und konfigurieren Sie ihn als primären Monitor in **Einstellungen App > System > Display**.

## <a name="steamvr-content-appears-in-the-wrong-place-like-beneath-the-floor-or-above-my-head"></a>Der Inhalt von "SteamVR" wird an der falschen Stelle angezeigt, z. B. unter dem Boden oder über meinem Kopf.

Setzen Sie Ihre Position zurück:

1. Wählen Sie den Fingerabdruck des linken Controllers aus, um das "SteamVR-Dashboard" aufzuführen.
2. Wählen Sie die Schaltfläche "Einstellungen" aus.
3. Wählen Sie "Reset Seated Position" (Gesetzte Position zurücksetzen) aus.

## <a name="my-steam-app-closed-unexpectedly"></a>Meine Steam-App wurde unerwartet geschlossen.

Die Steam-App wird geschlossen, wenn:

* Sie sperren ihren PC-Bildschirm
* Entfernen Des Headsets
* Wechseln von Benutzern
* Ihr PC wechselt in den Standbymodus.
