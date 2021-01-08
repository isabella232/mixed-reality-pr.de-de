---
title: Windows Mixed Reality und die neue Microsoft Edge
description: Erfahren Sie mehr über den neuen Microsoft Edge für die gemischte Realität, einschließlich der erwarteten Informationen, der Updates, die Sie kennen sollten, und bekannter Probleme.
author: mattzmsft
ms.author: mazeller
ms.date: 08/04/2020
ms.topic: article
keywords: Edge, New, immersives Web, Microsoft Edge, Browser, VR, 360, 360 Video, 360 Viewer, webxr, webvr
ms.openlocfilehash: ef55ee564e0a7ea11aaaad62ebf259459454ab72
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010030"
---
# <a name="the-new-microsoft-edge-for-windows-mixed-reality"></a>Die neue Microsoft Edge für Windows Mixed Reality

Der [neue Microsoft Edge ist jetzt zum Herunterladen verfügbar](https://blogs.windows.com/windowsexperience/?p=173496), Kunden können jedoch auch [auf ein zukünftiges Update warten, um es mit Windows 10 zu installieren](https://blogs.windows.com/msedgedev/2020/01/15/upgrading-new-microsoft-edge-79-chromium/), indem Sie in den nächsten Monaten einen gemessenen Rollout durchführen. 

Mit diesen Neuigkeiten **wollten wir die Kunden von Windows Mixed Reality VR Headset wissen, was vom neuen Microsoft Edge zu erwarten ist, und ausstehende Updates für eine verbesserte Browser Darstellung in Windows Mixed Reality anzeigen lassen**.

## <a name="introducing-the-new-microsoft-edge"></a>Einführung in den neuen Microsoft Edge

Das neue Microsoft Edge [übernimmt das Chromium-Open-Source-Projekt](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) auf dem Desktop, um eine bessere Kompatibilität für Kunden und weniger Fragmentierung des Internets für Webentwickler zu erzielen. Es unterstützt auch webxr beim Start, den neuen Standard zum Erstellen von immersiven Webumgebungen für VR-Headsets anstelle von webvr.

>[!IMPORTANT]
>Wenn Sie Microsoft Edge auf einem aktuellen Windows 10-Gerät installieren, ersetzt es die vorherige (Legacy-) Version auf Ihrem PC.

## <a name="getting-ready-for-the-new-microsoft-edge"></a>Vorbereitung auf den neuen Microsoft Edge

Windows Mixed Reality VR-Headset-Kunden, die den neuen Microsoft Edge in der Mixed Reality-Startseite verwenden möchten, sollten **auf Windows 10, Version 1903 oder höher, für die native Unterstützung von Win32-Anwendungen (wie dem neuen Microsoft Edge)** in der Mixed Reality-Startseite aktualisieren. Überprüfen Sie Windows Update oder [Installieren Sie die neueste Version von Windows 10 manuell](https://www.microsoft.com/en-us/software-download/windows10).

Um die bestmögliche Microsoft Edge-Benutzersprache in der Mixed Reality-Startseite zu nutzen, wird empfohlen, auf **einige wichtige Windows Mixed Reality-Optimierungen für den neuen Microsoft Edge zu warten, der mit dem kumulativen Update von 2020-01 für Windows 10, Version 1903 (oder höher)**, erreichbar ist, das in Windows Update bis Ende Januar verfügbar sein sollte.

>[!IMPORTANT]
>Wenn Sie den neuen Microsoft Edge herunterladen möchten, bevor Sie diese Updates ausführen, gibt es einige bekannte Probleme mit dem Verhalten in Windows Mixed Reality (Weitere Informationen finden Sie weiter unten).

## <a name="known-issues"></a>Bekannte Probleme

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>Bekannte Probleme, die durch das kumulative Update 2020-01 für Windows 10, Version 1903 (oder höher) behoben wurden

- Das Starten einer beliebigen Win32-APP, einschließlich des neuen Microsoft Edge, bewirkt, dass die Headset-Anzeige kurz fixiert wird.
- Die Microsoft Edge-Kachel verschwindet im Windows Mixed Reality-Startmenü (Sie finden es im Ordner "Classic Apps").
- Windows aus dem vorherigen Microsoft Edge wird immer noch um die gemischte Realität herum platziert, kann aber nicht verwendet werden. Es wird versucht, diese Windows Edge-Edge in der Desktop-App zu aktivieren.
- Wenn Sie einen Link in der Mixed Reality-Startseite auswählen, wird ein Webbrowser auf dem Desktop anstelle der Mixed Reality-Startseite gestartet.
- Die webvr-Showcase-APP ist in der Mixed Reality-Homepage enthalten, obwohl webvr nicht mehr unterstützt wird.
- Allgemeine Verbesserungen beim Starten von Tastatur und visuellen Elementen.

### <a name="monitor-and-input-handling-issues"></a>Probleme bei der Überwachung und Eingabe Behandlung

Nachdem Sie das kumulative Update 2020-01 für Windows 10, Version 1903 (oder höher) übernommen haben, werden virtuelle Monitore in den **Einstellungen > System >** in Windows Mixed Reality-Sitzungen angezeigt. Einige Kunden, insbesondere bei mehr als einem physischen Monitor, bemerken möglicherweise Probleme mit dem Desktop Layout und der Eingabe Behandlung.

**Warum dies geschieht**

Die Unterstützung für klassische Win32-Anwendungen in Windows Mixed Reality wurde mit dem [Windows 10-Update von Mai 2019](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-may-2019)eingeführt. Um diese Unterstützung zu aktivieren, muss ein virtueller Monitor erstellt werden, um die Win32-Anwendung zu hosten. Jedes Mal, wenn eine neue Win32-Anwendung gestartet wird, muss ein weiterer virtueller Monitor erstellt werden. Leider ist das Erstellen eines virtuellen Monitors eine intensive Aufgabe, die dazu führen kann, dass die Headset-Anzeige kurz fixiert wird. Kunden haben Feedback gegeben, dass dies ein unbequemer und störendes Verhalten war. Aufgrund von Feedback und erhöhter Verwendung von Win32-Anwendungen haben wir die Entscheidung getroffen, während des Starts von Windows Mixed Reality drei virtuelle Monitore vorab zuzuordnen. Dies verhindert Störungen und ermöglicht es den Kunden, bis zu drei gleichzeitige Win32-Anwendungen zu starten, ohne dass das Einfrieren der Headset angezeigt wird.

**Problemumgehung**

Wir haben seitdem Feedback erhalten, das einige Kunden, insbesondere solche mit mehreren physischen Monitoren, bevorzugen, diese virtuelle Monitor vorab Zuordnung zu deaktivieren. Um Kunden die Kontrolle zu verschaffen, haben wir eine Problem Umgehung aktiviert, die das Ändern eines Registrierungsschlüssel Werts erfordert, der mit den folgenden Windows-Updates verfügbar ist:

- 2020-07 kumulative Update Vorschau für Windows 10, Version 2004 (KB4568831)
- 2020-10 kumulative Update Vorschau für Windows 10, Version 1909 (KB4580386)
- 2020-10 kumulative Update Vorschau für Windows 10, Version 1903 (KB4580386)

>[!NOTE]
>Das Ändern von Registrierungsschlüssel Werten ist für fortgeschrittene Benutzer gedacht.

>[!WARNING]
>Das Deaktivieren der vorab Zuordnung des virtuellen Monitors kann dazu führen, dass Ihr Headset beim Starten einer Win32-Anwendung (z. b. "Steam", "New Microsoft Edge" oder Google Chrome) in Windows Mixed Reality kurz einfriert wird.

So deaktivieren Sie die vorab Zuordnung des virtuellen Monitors:
1. Aktivieren Sie **Windows Update** für eine der oben aufgeführten Versionen der kumulativen Windows 10-Update Vorschauversion, und installieren Sie das Update, wenn es verfügbar ist. Sie können das Update unter **optionale Updates** oder **Erweiterte Optionen** auf der Seite Windows Update Einstellungen finden.
2. **Registrierungs-Editor** starten
3. Navigieren Sie zu "HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Holographic\"
4. Wenn die REG_DWORD "prezuzuordnen catevirtualmonitors" nicht vorhanden ist, erstellen Sie Sie, indem Sie **> neuen > DWORD-Wert (32-Bit) bearbeiten** auswählen und als Name prezuzuordnen catevirtualmonitors eingeben.
5. Wenn die REG_DWORD "prezugecatevirtualmonitors" vorhanden ist (oder Sie soeben erstellt haben), doppelklicken Sie auf den Eintrag, und ändern Sie "Wertdaten" von 1 (Standardwert) in 0 (null).
    * TRUE-1
    * FALSE-0

Virtuelle Monitore werden nun zugeordnet, wenn Sie versuchen, eine Win32-Anwendung in Windows Mixed Reality zu starten, statt eine vorab Zuordnung durchführen zu müssen. Wenn Sie diese zurücksetzen und die vorab Zuordnung des virtuellen Monitors wieder aktivieren möchten, geben Sie das DWORD-"Wertdaten" in "1" zurück.

### <a name="other-known-issues"></a>Andere bekannte Probleme

-   Websites, die in Windows Mixed Reality geöffnet sind, gehen verloren, wenn das gemischte Reality-Portal geschlossen wird. Die Microsoft Edge-Fenster bleiben in der gemischten Realität Zuhause.
- Webxr-Funktionen, einschließlich der 360 Viewer-Erweiterung, werden möglicherweise auf PCs mit einem Hybrid-GPU-Setup nicht ordnungsgemäß gestartet. Sie können dieses Problem umgehen, indem Sie im neuen Microsoft Edge ein Vorschau Feature aktivieren. Navigieren Sie zu `edge://flags` , suchen Sie nach "Multi GPU", und aktivieren Sie das Flag **webxr-multigpu-Unterstützung**.
-   Das Audiomaterial von Microsoft Edge Windows ist nicht räumlich.
-   **Korrigiert in 360 Viewer Extension Version 2.3.8**: das Öffnen eines 360-Videos von YouTube in Windows Mixed Reality kann dazu führen, dass das Video im Headset verzerrt wird. Das Neustarten von Edge sollte die 360 Viewer-Erweiterung unsichtbar aktualisieren, um dieses Problem zu beheben. Sie können überprüfen, welche Version der Erweiterung Sie haben, indem Sie `edge://system/` in die Adressleiste eingeben und auf die Schaltfläche **erweitern** neben "Erweiterungen" klicken.
