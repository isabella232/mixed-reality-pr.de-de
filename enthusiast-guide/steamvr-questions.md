---
title: FAQs zu steamvr
description: Steamvr Windows Mixed Reality-Problembehandlung, die über die standardmäßige Kundensupport Dokumentation hinausgeht.
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, Mr, Problembehandlung, Fehler, Hilfe, Support, steamvr
ms.openlocfilehash: f1eafa303d0f2ee4c289f9acf337d8c512a7915c
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2020
ms.locfileid: "93132134"
---
# <a name="steamvr-faqs"></a>FAQs zu steamvr

## <a name="how-can-i-play-steamvr-games-in-my-windows-mixed-reality-headset"></a>Wie kann ich steamvr-Spiele in meinem Windows Mixed Reality-Headset abspielen?

1. [Herunterladen und Installieren von steamvr](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe). Das Tutorial "steamvr" sollte automatisch gestartet werden, wenn Sie "steamvr" starten.
2. Verbinden Sie Ihr Headset mit Ihrem PC, und schalten Sie die Motion-Controller ein.
3. Nachdem Sie Windows Mixed Reality Home geladen haben und ihre Controller sichtbar sind, öffnen Sie die app "Steam" auf Ihrem Desktop.
4. Verwenden Sie die app "Steam", um ein steamvr-Spiel aus ihrer Dampf Bibliothek zu starten. Zum Starten von steamvr-spielen, ohne Ihr Headset zu beenden, suchen und starten Sie Sie unter Windows Mixed Reality **Start > alle apps** .

## <a name="a-message-says-to-use-steamvr-with-windows-mixed-reality-you-need-to-install-the-latest-windows-update-or-windows-developer-mode-required"></a>Eine Meldung mit dem Hinweis "für die Verwendung von" steamvr "mit Windows Mixed Reality müssen Sie die neueste Windows Update" oder "Windows-Entwicklermodus erforderlich" installieren.

1. Stellen Sie sicher, dass auf Ihrem PC die neueste Version von Windows 10 ausgeführt wird. Wechseln Sie zu **Einstellungen > System >** Info, und stellen Sie unter "Windows-Spezifikationen" sicher, dass "OS Build" 16299,64 oder höher ist.
2. Stellen Sie sicher, dass keine Updates vorhanden sind, die auf den Download oder die Installation warten. Wechseln Sie zu **Einstellungen > aktualisieren Sie & Sicherheits > Windows Update** , und wählen Sie "nach Updates suchen". Sie müssen möglicherweise mehrmals prüfen, bis keine weiteren Updates verfügbar sind, und dann Ihren PC neu starten.

## <a name="steamvr-is-crashing-after-updating-windows"></a>Steamvr stürzt nach dem Aktualisieren von Windows ab

Einige ältere Versionen von Windows Mixed Reality für steamvr sind nicht mehr mit Windows kompatibel. Um sicherzustellen, dass Ihre Windows Mixed Reality-Version für steamvr aktuell ist:

1. Wechseln Sie in der Dampf Bibliothek zu **Software > Windows Mixed Reality for steamvr** .
2. Klicken Sie mit der rechten Maustaste darauf, und wechseln Sie zu "Eigenschaften".
3. Wählen Sie die Registerkarte "Aktualisieren" und "diese Anwendung immer auf dem neuesten standhalten" aus.
4. Erzwingen Sie die Aktualisierung, indem Sie auf die Registerkarte "lokale Dateien" klicken und "Integrität von Anwendungs Dateien überprüfen" auswählen.
5. Starten Sie Steam und steamvr neu.

Wenn steamvr nach dem Aktualisieren immer noch abgestürzt ist, haben Sie möglicherweise zwei Installationen von Windows Mixed Reality für steamvr auf Ihrem Computer. So überprüfen Sie, ob dies der Fall ist:

1. Suchen ```%localappdata%\openvr\openvrpaths.vrpath``` und öffnen Sie Sie im Editor.
2. Suchen Sie in den Abschnitten "externe Treiber" nach mehreren Einträgen für "mixedrealityvrdriver".
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver",
      "E:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
3. Wenn mehrere Einträge angezeigt werden, entfernen Sie den älteren der beiden Einträge. Wenn Sie nur einen Eintrag haben, sollte am Ende der Zeile kein Komma mehr vorhanden sein. Beispiel:
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
4. Speichern Sie die Datei, und schließen Sie sie.
5. Starten Sie Steam und steamvr neu.

## <a name="my-controllers-arent-working-as-expected-in-steamvr"></a>Meine Controller funktionieren in steamvr nicht erwartungsgemäß.

1. Schließen Sie steamvr.
2. Kehren Sie zu Windows Mixed Reality Home zurück, und vergewissern Sie sich, dass Ihre Controller funktionieren.
3. Starten Sie die Verwendung von "steamvr" erneut, und ihre Controller sollten wieder normal sein.
4. Wenn weiterhin Probleme auftreten, verwenden Sie das Feedback für den [Windows-Feedback-Hub](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app) unter der Kategorie Gemischte Realität, und fügen Sie in der Zusammenfassung steamvr ein.

Beachten Sie, dass Sie Ihre Bewegungs Controller in verschiedenen Spielen unterschiedlich verwenden. Hier sind einige Grundlagen für den Einstieg:
* Um das Steam-Dashboard zu öffnen, klicken Sie auf den linken Finger Stick.
* Um ein steamvr-Spiel zu beenden und zum Windows Mixed Reality-Start zurückzukehren, drücken Sie die Windows-Taste. Wählen Sie dann die Schaltfläche Mixed Reality, die auf dem Bildschirm angezeigt wird.

## <a name="my-left-and-right-controllers-are-reversed-in-steamvr"></a>Meine linken und rechten Controller werden in "steamvr" umgekehrt

Starten Sie das Spiel mit ihren Controllern, und schalten Sie dann den linken Controller ein, gefolgt von der rechten Seite.

## <a name="my-games-are-running-slowly"></a>Meine Spiele laufen langsam

1. Stellen Sie sicher, dass Ihr PC die Spezifikationen für steamvr in Windows Mixed Reality und für das von Ihnen wiedergegebene steamvr-Spiel erfüllt.
2. Wählen Sie im Mixed Reality-Portal auf Ihrem Desktop "anhalten", um die Desktop Vorschau zu stoppen.
3. Wechseln Sie zu **Einstellungen > System > über** und unter "Windows-Spezifikationen", und stellen Sie sicher, dass "OS Build" 16299,64 oder höher ist.
4. Stellen Sie sicher, dass Ihr PC über die neuesten Grafiktreiber verfügt ("nach Updates suchen" in Windows Update).
5. Überprüfen Sie den Task-Manager, um festzustellen, welche anderen Prozesse möglicherweise Ressourcen auf Ihrem PC verbrauchen.
6. Überprüfen Sie, ob der Stream ein Spiel im Hintergrund herunterlädt. Dies kann Ressourcen verbrauchen und das Ausführen von spielen erleichtern.
7. Eine kleine Klasse von apps, die nicht über ein sichtbares Fenster verfügen (z. b. "steamvr Home"), hat ein bekanntes Leistungsproblem. Die meisten apps fallen nicht in diese Kategorie, und eine Korrektur wird in einem zukünftigen Update verfügbar sein.

Wenn noch unerwartete Leistungsprobleme auftreten, senden Sie uns Feedback über den Windows- [Feedback-Hub](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app). Befolgen Sie die Anweisungen, um eine Ablauf Verfolgung für die [steamvr-Leistung einzuschließen](using-steamvr-with-windows-mixed-reality.md#sharing-feedback-on-steamvr).

## <a name="steamvr-is-showing-a-compositor-error-for-example-shared-ipc-compositor-connect-failed-400"></a>"Steamvr" zeigt einen compositorfehler an (z. b. "Fehler beim freigegebenen IPC Compositor Connect-Fehler (400)").

Dies kann vorkommen, wenn sich Ihr Headset und der primäre Monitor auf zwei verschiedenen Video Adaptern befinden. Fügen Sie den Monitor an denselben Adapter wie Ihr Headset an, und konfigurieren Sie diesen Monitor so, dass er der primäre Monitor in den **Einstellungen app > System > angezeigt** wird.

## <a name="steamvr-content-appears-in-the-wrong-place-like-beneath-the-floor-or-above-my-head"></a>Der Inhalt von "steamvr" wird an der falschen Stelle angezeigt, z. b. unterhalb oder oberhalb des Kopfes.

Position zurücksetzen:

1. Klicken Sie auf den Finger Stick des linken Controllers, um das "steamvr-Dashboard" zu aktivieren.
2. Wählen Sie die Schaltfläche "Einstellungen" aus.
3. Wählen Sie "Position an Position zurücksetzen".

## <a name="my-steam-app-closed-unexpectedly"></a>Meine Steam-App wurde unerwartet geschlossen.

Die Steam-APP wird geschlossen, wenn Sie den PC-Bildschirm sperren, das Headset entfernen, Benutzer wechseln oder wenn Ihr PC in den Standbymodus wechselt.
