---
title: Windows Mixed Reality und die neue Microsoft Edge
description: Erfahren Sie mehr über die Microsoft Edge für Mixed Reality, einschließlich der zu erwartenden Informationen, der zu achtenden Updates und bekannter Probleme.
author: mattzmsft
ms.author: mazeller
ms.date: 08/04/2020
ms.topic: article
keywords: edge, new, immersive web, microsoft edge, browser, vr, 360, 360 video, 360 viewer, webxr, webvr
ms.openlocfilehash: 51efc5c4d3afb4d46ba7722867514f740a9f60a4280652fdbd665134f83af23d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115218822"
---
# <a name="the-new-microsoft-edge-for-windows-mixed-reality"></a>Die neue Microsoft Edge für Windows Mixed Reality

Die [neue Microsoft Edge](https://blogs.windows.com/windowsexperience/?p=173496)steht jetzt zum Download zur Verfügung. Kunden können jedoch auch auf ein zukünftiges Update warten, um es mit [Windows 10](https://blogs.windows.com/msedgedev/2020/01/15/upgrading-new-microsoft-edge-79-chromium/)zu installieren. Dies erfolgt nach einem gemessenen Rolloutansatz in den nächsten Monaten. 

Mit dieser Nachricht wollten wir Windows Mixed Reality VR-Headset-Kunden wissen lassen, was sie von der neuen Microsoft Edge erwarten können, und ausstehende Updates für eine verbesserte Browsererfahrung **in Windows Mixed Reality.**

## <a name="introducing-the-new-microsoft-edge"></a>Vorstellung des neuen Microsoft Edge

Die neue Microsoft Edge übernimmt das open [source Chromium projekt](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) auf dem Desktop, um eine bessere Kompatibilität für Kunden und eine geringere Fragmentierung des Webs für Webentwickler zu schaffen. Außerdem wird WebXR beim Start unterstützt, der neue Standard zum Erstellen immersiver Weberfahrungen für VR-Headsets, statt WebVR.

>[!IMPORTANT]
>Wenn Sie Microsoft Edge auf einem aktuellen Gerät Windows 10 installieren, wird die vorherige (Legacy-) Version auf Ihrem PC ersetzt.

## <a name="getting-ready-for-the-new-microsoft-edge"></a>Erste Schritte für die neue Microsoft Edge

Windows Mixed Reality VR-Headset-Kunden, die die neue Microsoft Edge im Mixed Reality Startumgebung verwenden möchten, sollten ein Upgrade auf Windows 10 Version **1903** oder höher durchführen, um win32-Anwendungen (z. B. die neue Microsoft Edge) im Mixed Reality Startumgebung. Überprüfen Windows Update, oder installieren Sie manuell [die neueste Version von Windows 10](https://www.microsoft.com/en-us/software-download/windows10).

Für die bestmögliche Microsoft Edge-Erfahrung im Mixed Reality Startumgebung empfehlen wir auch, auf einige wichtige Windows Mixed Reality-Optimierungen für die neue Microsoft Edge zu warten, die mit dem kumulativen Update **2020-01 für Windows 10 Version 1903 (oder höher)** eintreffen, die in Windows Update bis Ende Januar verfügbar sein sollten.

>[!IMPORTANT]
>Wenn Sie die neue Microsoft Edge herunterladen, bevor Sie diese Updates verwenden, gibt es einige bekannte Probleme mit dem Verhalten in Windows Mixed Reality (die Sie weiter unten lesen können).

## <a name="known-issues"></a>Bekannte Probleme

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>Bekannte Probleme, die durch das kumulative Update 2020-01 für Windows 10 Version 1903 (oder höher) behoben wurden

- Das Starten einer win32-App, einschließlich der neuen Microsoft Edge, bewirkt, dass die Headsetanzeige kurz einfriert.
- Die Microsoft Edge kachel verschwindet im Windows Mixed Reality Startmenü (Sie finden sie im Ordner "Klassische Apps").
- Windows aus dem vorherigen Microsoft Edge werden weiterhin um den Mixed Reality Startumgebung platziert, können jedoch nicht verwendet werden. Beim Versuch, diese Fenster zu aktivieren, wird Edge in der Desktop-App gestartet.
- Wenn Sie einen Link in der Mixed Reality Startumgebung, wird ein Webbrowser auf dem Desktop anstatt auf dem Mixed Reality Startumgebung.
- Die WebVR Showcase-App ist in der Mixed Reality Startumgebung vorhanden, obwohl WebVR nicht mehr unterstützt wird.
- Allgemeine Verbesserungen an Tastaturstarts und Visuals.

### <a name="monitor-and-input-handling-issues"></a>Probleme bei der Überwachung und Eingabebehandlung

Nach der Übernahme des kumulativen Updates 2020-01 für Windows 10 Version 1903 (oder höher) werden virtuelle Monitore während Windows Mixed Reality-Sitzungen als generische physische Monitore in **Einstellungen > System > Display** angezeigt. Einige Kunden, insbesondere mit mehr als einem physischen Monitor, bemerken möglicherweise Probleme mit dem Desktoplayout und der Eingabebehandlung.

**Warum dies geschieht**

Die Unterstützung für klassische Win32-Anwendungen in Windows Mixed Reality wurde mit [dem](/windows/mixed-reality/enthusiast-guide/release-notes-may-2019)Windows 10 May 2019 Update. Um diese Unterstützung zu aktivieren, muss ein virtueller Monitor erstellt werden, um die Win32-Anwendung zu hosten. Jedes Mal, wenn eine neue Win32-Anwendung gestartet wird, muss ein weiterer virtueller Monitor erstellt werden. Leider ist das Erstellen eines virtuellen Monitors eine intensive Aufgabe, die dazu führen kann, dass die Headsetanzeige kurz einfriert. Kunden haben uns feedback gegeben, dass es sich um eine umstliche und störende Erfahrung geerbte. Aufgrund von Feedback und einer erhöhten Nutzung von Win32-Anwendungen haben wir uns entschieden, drei virtuelle Monitore beim Start der Anwendung vorab Windows Mixed Reality. Dadurch wird eine Unterbrechung verhindert, und Kunden können bis zu drei gleichzeitige Win32-Anwendungen starten, ohne dass die Headsetanzeige einfrieren muss.

**Problemumgehung**

Wir haben seitdem Feedback erhalten, dass einige Kunden, insbesondere kunden mit mehreren physischen Monitoren, diese Vorabzuordnung für virtuelle Monitore deaktivieren möchten. Um Kunden die Kontrolle zu geben, haben wir eine Problemumgehung aktiviert, die das Ändern eines Registrierungsschlüsselwerts umfasst, der mit den folgenden Updates Windows ist:

- 2020-07 Cumulative Update Preview for Windows 10 Version 2004 (KB4568831)
- 2020-10 Cumulative Update Preview for Windows 10 Version 1909 (KB4580386)
- 2020-10 Cumulative Update Preview for Windows 10 Version 1903 (KB4580386)

>[!NOTE]
>Das Ändern von Registrierungsschlüsselwerten ist für fortgeschrittene Benutzer vorgesehen.

>[!WARNING]
>Wenn Sie die Vorabzuordnung virtueller Monitore deaktivieren, kann dies dazu führen, dass die Headsetanzeige kurzzeitig einfriert, wenn Sie eine Win32-Anwendung (wie z. B. Steam, das neue Microsoft Edge oder Google Chrome) in Windows Mixed Reality.

So deaktivieren Sie die Vorabzuordnung virtueller Monitore:
1. Überprüfen **Windows Update** auf eine der oben Windows 10 kumulativen Updatevorschauversionen, und installieren Sie das Update, falls verfügbar. Sie finden das Update unter **Optionale Updates** oder **Erweiterte Optionen auf** der Seite Windows Updateeinstellungen.
2. Starten des **Registrierungs-Editors**
3. Navigieren Sie zu "HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Holographic\"
4. Wenn die REG_DWORD "PreallocateVirtualMonitors" nicht vorhanden ist, erstellen Sie sie, indem Sie bearbeiten **> Neuer >-DWORD-Wert (32-Bit)** auswählen und PreallocateVirtualMonitors als Namen eingeben.
5. Wenn die REG_DWORD "PreallocateVirtualMonitors" vorhanden ist (oder Sie sie gerade erstellt haben), doppelklicken Sie auf den Eintrag, und ändern Sie "Wertdaten" von 1 (Standardwert) in 0 (null).
    * TRUE – 1
    * FALSE – 0

Virtuelle Monitore werden jetzt reserviert, wenn Sie versuchen, eine Win32-Anwendung in Windows Mixed Reality Vorabzuweisung zu starten. Um dies zurückzusetzen und die Vorabzuordnung des virtuellen Monitors erneut zu aktivieren, geben Sie das DWORD "Wertdaten" auf 1 zurück.

### <a name="other-known-issues"></a>Andere bekannte Probleme

-   Websites, die in Windows Mixed Reality geöffnet werden, gehen verloren, wenn Mixed Reality-Portal werden. Die Microsoft Edge Fenster bleiben an ihren platzierten Positionen in der Mixed Reality Startumgebung.
- WebXR-Funktionen, einschließlich der 360 Viewer-Erweiterung, werden möglicherweise nicht ordnungsgemäß auf PCs mit einer Hybrid-GPU-Einrichtung gestartet. Sie können dieses Problem beheben, indem Sie eine Vorschaufunktion im neuen Microsoft Edge. Navigieren Sie zu `edge://flags` , suchen Sie nach "Multi-GPU", und aktivieren Sie das Flag **WebXR Multi-GPU-Unterstützung.**
-   Audiodaten Microsoft Edge Fenstern werden nicht räumlichisiert.
-   **Behoben in Version 2.3.8 der 360** Viewer-Erweiterung: Das Öffnen eines 360-Videos von YouTube in Windows Mixed Reality kann dazu führen, dass das Video im Headset verzerrt wird. Beim Neustarten von Edge sollte die 360 Viewer-Erweiterung unsichtbar aktualisiert werden, um dieses Problem zu beheben. Sie können überprüfen, über welche Version der Erweiterung Sie verfügen, indem Sie in der Adressleiste eingeben und neben `edge://system/` "Erweiterungen" auf die Schaltfläche Erweitern klicken. 