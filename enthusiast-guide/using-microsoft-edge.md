---
title: Verwenden von Microsoft Edge in Windows Mixed Reality
description: Bereiten Sie sich auf die neue Microsoft Edge in Windows Mixed Reality vor. Enthält zu erwartende Änderungen, updates, nach denen gesucht werden muss, und bekannte Probleme.
author: qianw211
ms.author: v-qianwen
ms.date: 9/24/2021
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Home, Navigate, Get around, apps, games, Microsoft Edge, chromium, Edge, 360, 360 video, 360 viewer
ms.openlocfilehash: 2834adc7325f6b600a5cf5f65c74948e0feb2c57
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436697"
---
# <a name="windows-mixed-reality-and-the-new-microsoft-edge"></a>Windows Mixed Reality und die neue Microsoft Edge

Die [neue Microsoft Edge](https://www.microsoft.com/edge) steht zum Download zur Verfügung und wurde über Windows Update automatisch für Kunden bereitgestellt. 

Die neue Microsoft Edge [übernimmt das Chromium Open Source-Projekt](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) auf dem Desktop. Dies führt zu einer besseren Kompatibilität für Kunden und einer geringeren Fragmentierung für Webentwickler. Außerdem wird WebXR beim Start unterstützt. Dies ist der neue Standard zum Erstellen immersiver Weberfahrungen für VR-Headsets anstelle von WebVR.

>[!IMPORTANT]
>Wenn Sie Microsoft Edge auf einem aktuellen Windows 10- oder Windows 11-Gerät installieren, wird die vorherige (Legacy-) Version auf Ihrem PC ersetzt.

## <a name="installing-the-new-microsoft-edge"></a>Installieren des neuen Microsoft Edge 

Bevor Sie die neue Microsoft Edge installieren, führen Sie **ein Upgrade auf Windows 10 Version 1903 oder höher oder Windows 11 für native Win32-Anwendungsunterstützung durch, z.** B. die neue Microsoft Edge in Windows Mixed Reality. Überprüfen Sie Windows Update, oder installieren Sie die neueste Version von Windows 10 oder Windows 11 [manuell.](https://www.microsoft.com/software-download/windows10)

Sobald Sie Windows 10 Version 1903 oder höher oder Windows 11 haben, sind Sie bereit für die neue Microsoft Edge! Die neue Microsoft Edge wird über Windows Update veröffentlicht. Sie können die neue Microsoft Edge jedoch manuell von der [Microsoft Edge Website](https://www.microsoft.com/edge) installieren, wenn Sie dies früher wünschen.

>[!IMPORTANT]
>Die neue Microsoft Edge wird mit Unterstützung für WebXR gestartet, dem neuen Standard zum Erstellen immersiver Weberfahrungen für VR-Headsets. Wenn Sie die neue Microsoft Edge installieren, können Sie WebVR-Funktionen nicht mehr in Microsoft Edge wiedergeben. 

## <a name="known-issues"></a>Bekannte Probleme

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>Bekannte Probleme, die durch das kumulative Update 2020-01 für Windows 10 Version 1903 (oder höher) behoben wurden

- Das Starten einer beliebigen Win32-App, einschließlich der neuen Microsoft Edge, bewirkt, dass die Headsetanzeige kurz einfriert.
- Die kachel Microsoft Edge wird im Windows Mixed Reality Startmenü nicht mehr angezeigt (Sie finden sie im Ordner "Klassische Apps").
- Windows aus dem vorherigen Microsoft Edge werden immer noch um die Mixed Reality Startumgebung platziert, können aber nicht verwendet werden. Wenn Sie versuchen, diese Fenster zu aktivieren, wird Edge in der Desktop-App gestartet.
- Wenn Sie einen Link in der Mixed Reality Startumgebung auswählen, wird anstelle des Mixed Reality Startumgebung ein Webbrowser auf dem Desktop gestartet.
- Die WebVR Showcase-App ist im Mixed Reality Startumgebung vorhanden, obwohl WebVR nicht mehr unterstützt wird.
- Allgemeine Verbesserungen am Tastaturstart und an Visuals.

### <a name="monitor-and-input-handling-issues"></a>Probleme bei der Überwachung und Eingabebehandlung

Nach dem kumulativen Update 2020-01 für Windows 10 Version 1903 oder höher werden virtuelle Monitore während Windows Mixed Reality Sitzungen als generische physische Monitore in **Einstellungen > System > Display** angezeigt. Einige Kunden, insbesondere kunden mit mehr als einem physischen Monitor, bemerken möglicherweise Probleme mit dem Desktoplayout und der Eingabeverarbeitung.

**Warum dies geschieht**

Die Unterstützung für klassische Win32-Anwendungen in Windows Mixed Reality wurde mit dem [Windows 10 May 2019 Update](/windows/mixed-reality/release-notes-may-2019)eingeführt. Um diese Unterstützung zu aktivieren, muss ein virtueller Monitor zum Hosten der Win32-Anwendung erstellt werden. Jedes Mal, wenn eine neue Win32-Anwendung gestartet wird, muss ein anderer virtueller Monitor erstellt werden. Leider ist das Erstellen eines virtuellen Monitors eine intensive Aufgabe, die dazu führen kann, dass die Headsetanzeige kurz einfriert. Kunden haben Feedback zu einer freundlichkeit und unterbrechungsfreien Erfahrung geboten. Aufgrund dieses Feedbacks haben wir uns zusammen mit der zunehmenden Nutzung von Win32-Anwendungen entschieden, während des Starts von Windows Mixed Reality drei virtuelle Monitore vorab zuzuordnen, um diese Unterbrechung zu verhindern und Kunden zu ermöglichen, bis zu drei gleichzeitige Win32-Anwendungen zu starten, ohne dass die Headsetanzeige fixiert wird.

**Problemumgehung**

Wir haben seitdem Feedback erhalten, dass einige Kunden, insbesondere kunden mit mehreren physischen Monitoren, diese vorab zugeordnete virtuelle Überwachung deaktivieren möchten. Um Kunden mehr Kontrolle zu geben, haben wir eine Problemumgehung aktiviert, die das Ändern eines Registrierungsschlüsselwerts umfasst, der mit den folgenden Windows Updates verfügbar ist:

- 2020-07 Cumulative Update Preview for Windows 10 Version 2004 (KB4568831)
- 2020-10 Cumulative Update Preview for Windows 10 Version 1909 (KB4580386)
- 2020-10 Cumulative Update Preview for Windows 10 Version 1903 (KB4580386)

>[!NOTE]
>Das Ändern von Registrierungsschlüsselwerten ist für fortgeschrittene Benutzer vorgesehen.

>[!WARNING]
>Das Deaktivieren der Vorabzuordnung des virtuellen Monitors kann dazu führen, dass die Headsetanzeige kurz eingefroren wird, wenn Sie eine Win32-Anwendung (z. B. Stream, die neue Microsoft Edge oder Google Chrome) in Windows Mixed Reality starten.

So deaktivieren Sie die Vorabzuordnung des virtuellen Monitors:
1. Überprüfen Sie **Windows Update** für eine der oben aufgeführten versionen des Windows 10 kumulativen Updates, und installieren Sie das Update, sofern verfügbar. Sie finden das Update unter **Optionale Updates** oder **Erweiterte Optionen** auf der Seite Windows Updateeinstellungen.
2. Starten des **Registrierungs-Editors**
3. Navigieren Sie zu "HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Holographic\"
4. Wenn die REG_DWORD "PreallocateVirtualMonitors" nicht vorhanden ist, erstellen Sie sie, indem **Sie > neuen > DWORD-Wert (32 Bit) bearbeiten** auswählen und PreallocateVirtualMonitors als Namen eingeben.
5. Wenn die REG_DWORD "PreallocateVirtualMonitors" vorhanden ist (oder Sie sie gerade erstellt haben), doppelklicken Sie auf den Eintrag, und ändern Sie "Wertdaten" von 1 (Standardwert) in 0 (null).
    * TRUE – 1
    * FALSE : 0

Virtuelle Monitore ordnen jetzt zu, wenn Sie versuchen, eine Win32-Anwendung in Windows Mixed Reality zu starten, anstatt sie vorab zuzuordnen. Um dies zurückzusetzen und die Vorabzuordnung des virtuellen Monitors erneut zu aktivieren, geben Sie die DWORD-Wertdaten auf 1 zurück.

### <a name="other-known-issues"></a>Andere bekannte Probleme

-   Websites, die in Windows Mixed Reality geöffnet werden, verloren, wenn Mixed Reality-Portal geschlossen wird, obwohl die Microsoft Edge Fenster dort bleiben, wo sie im Mixed Reality Startumgebung platziert wurden.
- WebXR-Funktionen, einschließlich der 360 Viewer-Erweiterung, werden auf PCs mit hybrider GPU-Einrichtung möglicherweise nicht ordnungsgemäß gestartet. Sie können dieses Problem umgehen, indem Sie eine Vorschaufunktion im neuen Microsoft Edge aktivieren. Navigieren Sie zu `edge://flags` , suchen Sie nach "Multi-GPU", und aktivieren Sie das Flag **WebXR Multi GPU Support**.
-   Audiodaten aus Microsoft Edge Fenstern werden nicht räumlich verräumlicht.
-   **Behoben in Version 2.3.8 der 360 Viewer-Erweiterung:** Das Öffnen eines 360-Videos von YouTube in Windows Mixed Reality kann dazu führen, dass das Video im Headset verzerrt wird. Wenn Sie Edge neu starten, sollte die Erweiterung 360 Viewer unsichtbar aktualisiert werden, um dieses Problem zu beheben. Sie können bestätigen, welche Version der Erweiterung Sie haben, indem Sie in der Adressleiste eingeben `edge://system/` und die Schaltfläche **Erweitern** neben "Erweiterungen" auswählen.