---
title: Verwenden von Microsoft Edge in Windows Mixed Reality
description: Machen Sie sich bereit für den neuen Microsoft Edge in Windows Mixed Reality. Enthält Änderungen, die erwartet werden sollen, sowie bekannte Probleme.
author: mattzmsft
ms.author: mazeller
ms.date: 11/11/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, Mr, Home, Navigate, get around, apps, Games, Microsoft Edge, Chrom, Edge, 360, 360 Video, 360 Viewer
ms.openlocfilehash: d3ed8f95285eefacf43177915d512bfb41730243
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725781"
---
# <a name="windows-mixed-reality-and-the-new-microsoft-edge"></a>Windows Mixed Reality und die neue Microsoft Edge

Der [neue Microsoft Edge](https://www.microsoft.com/edge) steht zum Herunterladen zur Verfügung und beginnt mit dem automatischen Rollout für Kunden über Windows Update. 

Das neue Microsoft Edge-Gerät [übernimmt das Projekt "Chromium Open Source](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) " auf dem Desktop. Dies sorgt für eine bessere Kompatibilität für Kunden und weniger Fragmentierung für Webentwickler. Außerdem wird webxr beim Start unterstützt. Dies ist der neue Standard zum Erstellen von immersiven Webumgebungen für VR-Headsets anstelle von webvr.

>[!IMPORTANT]
>Wenn Sie Microsoft Edge auf einem aktuellen Windows 10-Gerät installieren, ersetzt es die vorherige (Legacy-) Version auf Ihrem PC.

## <a name="installing-the-new-microsoft-edge"></a>Installieren des neuen Microsoft Edge 

Vor der Installation des neuen Microsoft Edge müssen Sie ein **Upgrade auf Windows 10, Version 1903 oder höher, für die native Unterstützung von Win32-Anwendungen wie die neue Microsoft Edge** in Windows Mixed Reality durchführen. Überprüfen Sie Windows Update oder [Installieren Sie die neueste Version von Windows 10 manuell](https://www.microsoft.com/software-download/windows10).

Wenn Sie Windows 10, Version 1903 oder höher, verwenden, sind Sie für die neue Microsoft Edge-Version bereit! Die neue Microsoft Edge-Anwendung wird über Windows Update Rollout, aber Sie können den neuen Microsoft Edge manuell von der [Microsoft Edge-Website](https://www.microsoft.com/edge) installieren, wenn Sie ihn früher benötigen.

>[!IMPORTANT]
>Die neue Microsoft Edge-Umgebung mit Unterstützung für webxr, der neue Standard zum Erstellen von immersiven Webumgebungen für VR-Headsets. Wenn Sie den neuen Microsoft Edge installieren, können Sie die webvr-Erfahrungen in Microsoft Edge nicht mehr wiedergeben. 

## <a name="known-issues"></a>Bekannte Probleme

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>Bekannte Probleme, die durch das kumulative Update 2020-01 für Windows 10, Version 1903 (oder höher) behoben wurden

- Das Starten einer beliebigen Win32-APP, einschließlich des neuen Microsoft Edge, bewirkt, dass die Headset-Anzeige kurz fixiert wird.
- Die Microsoft Edge-Kachel verschwindet im Windows Mixed Reality-Startmenü (Sie finden es im Ordner "Classic Apps").
- Windows aus dem vorherigen Microsoft Edge wird immer noch um die gemischte Realität herum platziert, kann aber nicht verwendet werden. Es wird versucht, diese Windows Edge-Edge in der Desktop-App zu aktivieren.
- Wenn Sie einen Link in der Mixed Reality-Startseite auswählen, wird ein Webbrowser auf dem Desktop anstelle der Mixed Reality-Startseite gestartet.
- Die webvr-Showcase-APP ist in der Mixed Reality-Homepage enthalten, obwohl webvr nicht mehr unterstützt wird.
- Allgemeine Verbesserungen beim Starten von Tastatur und visuellen Elementen.

### <a name="monitor-and-input-handling-issues"></a>Probleme bei der Überwachung und Eingabe Behandlung

Nachdem Sie das kumulative Update 2020-01 für Windows 10, Version 1903 oder höher, übernommen haben, werden virtuelle Monitore in den **Einstellungen > System >** in Windows Mixed Reality-Sitzungen angezeigt. Einige Kunden, insbesondere diejenigen mit mehr als einem physischen Monitor, bemerken möglicherweise Probleme mit dem Desktop Layout und der Eingabe Behandlung als Ergebnis.

**Warum dies geschieht**

Die Unterstützung für klassische Win32-Anwendungen in Windows Mixed Reality wurde mit dem [Windows 10-Update von Mai 2019](https://docs.microsoft.com/windows/mixed-reality/release-notes-may-2019)eingeführt. Um diese Unterstützung zu aktivieren, muss ein virtueller Monitor erstellt werden, um die Win32-Anwendung zu hosten. Jedes Mal, wenn eine neue Win32-Anwendung gestartet wird, muss ein weiterer virtueller Monitor erstellt werden. Leider ist das Erstellen eines virtuellen Monitors eine intensive Aufgabe, die dazu führen kann, dass die Headset-Anzeige kurz fixiert wird. Kunden haben Feedback gegeben, dass die benutzerfreundliche und unterbrechungsfreie benutzerfreundliche Aufgrund der zusätzlichen Verwendung von Win32-Anwendungen haben wir uns entschieden, drei virtuelle Monitore während des Starts von Windows Mixed Reality vorab zuzuweisen, um diese Unterbrechung zu verhindern und es den Kunden zu ermöglichen, bis zu drei gleichzeitige Win32-Anwendungen zu starten, ohne dass die Kopplung der Headset-Anzeige auftritt.

**Problemumgehung**

Wir haben seitdem Feedback erhalten, das einige Kunden, insbesondere solche mit mehreren physischen Monitoren, bevorzugen, diese virtuelle Monitor vorab Zuordnung zu deaktivieren. Um Kunden mehr Kontrolle zu verschaffen, haben wir eine Problem Umgehung aktiviert, die das Ändern eines Registrierungsschlüssel Werts erfordert, der mit den folgenden Windows-Updates verfügbar ist:

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

-   Websites, die in Windows Mixed Reality geöffnet werden, gehen verloren, wenn das gemischte Reality-Portal geschlossen wird. die Microsoft Edge-Fenster bleiben jedoch erhalten, wo Sie in der Mixed Reality-Startseite platziert werden.
- Webxr-Funktionen, einschließlich der 360 Viewer-Erweiterung, werden möglicherweise auf PCs mit einem Hybrid-GPU-Setup nicht ordnungsgemäß gestartet. Sie können dieses Problem umgehen, indem Sie im neuen Microsoft Edge ein Vorschau Feature aktivieren. Navigieren Sie zu `edge://flags` , suchen Sie nach "Multi GPU", und aktivieren Sie das Flag **webxr-multigpu-Unterstützung**.
-   Das Audiomaterial von Microsoft Edge Windows ist nicht räumlich.
-   **Korrigiert in 360 Viewer Extension Version 2.3.8**: das Öffnen eines 360-Videos von YouTube in Windows Mixed Reality kann dazu führen, dass das Video im Headset verzerrt wird. Das Neustarten von Edge sollte die 360 Viewer-Erweiterung unsichtbar aktualisieren, um dieses Problem zu beheben. Sie können überprüfen, welche Version der Erweiterung Sie haben, indem Sie `edge://system/` in die Adressleiste eingeben und auf die Schaltfläche **erweitern** neben "Erweiterungen" klicken.
