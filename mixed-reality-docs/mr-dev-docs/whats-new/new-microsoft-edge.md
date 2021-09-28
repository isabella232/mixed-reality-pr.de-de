---
title: Windows Mixed Reality und die neue Microsoft Edge
description: Erfahren Sie mehr über die neuen Microsoft Edge für Mixed Reality, einschließlich der zu erwartenden Informationen, der zu überprüfenden Updates und bekannter Probleme.
author: mattzmsft
ms.author: v-vtieto
ms.date: 09/24/2021
ms.topic: article
keywords: edge, new, immersive web, microsoft edge, browser, vr, 360, 360 video, 360 viewer, webxr, webvr
ms.openlocfilehash: ca849f63d2a755639bedba68c47e419528006a6d
ms.sourcegitcommit: 3176df29fb0c9508751bd370f1211031d50d2c14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2021
ms.locfileid: "129148649"
---
# <a name="the-new-microsoft-edge-for-windows-mixed-reality"></a>Die neue Microsoft Edge für Windows Mixed Reality

Die [neue Microsoft Edge steht jetzt zum Herunterladen zur Verfügung.](https://blogs.windows.com/windowsexperience/?p=173496)Kunden können jedoch auch auf ein [zukünftiges Update warten, um es mit Windows 10 zu installieren.](https://blogs.windows.com/msedgedev/2020/01/15/upgrading-new-microsoft-edge-79-chromium/)Dies erfolgt nach einem gemessenen Rolloutansatz in den nächsten Monaten. 

Mit diesen Neuigkeiten **wollten wir Windows Mixed Reality VR-Headset-Kunden mitteilen, was von der neuen Microsoft Edge erwartet wird, und ausstehende Updates für eine verbesserte Browsererfahrung in Windows Mixed Reality anzeigen.**

## <a name="introducing-the-new-microsoft-edge"></a>Vorstellung des neuen Microsoft Edge

Die neue Microsoft Edge [übernimmt das Chromium Open Source-Projekt](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) auf dem Desktop, um eine bessere Kompatibilität für Kunden und eine geringere Fragmentierung des Webs für Webentwickler zu schaffen. Außerdem wird WebXR beim Start unterstützt, der neue Standard zum Erstellen immersiver Weberfahrungen für VR-Headsets anstelle von WebVR.

>[!IMPORTANT]
>Wenn Sie Microsoft Edge auf einem aktuellen Windows 10 Gerät installieren, wird die vorherige Version (Legacyversion) auf Ihrem PC ersetzt.

## <a name="getting-ready-for-the-new-microsoft-edge"></a>Vorbereiten der neuen Microsoft Edge

Windows Mixed Reality VR-Headset-Kunden, die die neue Microsoft Edge im Mixed Reality Startumgebung verwenden möchten, sollten **ein Upgrade auf Windows 10 Version 1903 oder höher durchführen, um die native Unterstützung von Win32-Anwendungen (z. B. der neuen Microsoft Edge)** im Mixed Reality Startumgebung zu erhalten. Überprüfen Sie Windows Update, oder [installieren Sie manuell die neueste Version von Windows 10](https://www.microsoft.com/en-us/software-download/windows10).

Für die bestmögliche Microsoft Edge in der Mixed Reality Startumgebung empfehlen wir auch, auf einige wichtige Windows Mixed Reality Optimierungen für die neue Microsoft Edge zu warten, **die mit dem kumulativen Update 2020-01 für Windows 10 Version 1903 (oder höher) eintreffen,** das ende Januar in Windows Update verfügbar sein sollte.

>[!IMPORTANT]
>Wenn Sie die neue Microsoft Edge herunterladen möchten, bevor Sie diese Updates ausführen, treten einige bekannte Probleme mit dem Verhalten in Windows Mixed Reality auf (die Sie weiter unten lesen können).

## <a name="known-issues"></a>Bekannte Probleme

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>Bekannte Probleme, die durch das kumulative Update 2020-01 für Windows 10 Version 1903 (oder höher) behoben wurden

- Das Starten einer beliebigen Win32-App, einschließlich der neuen Microsoft Edge, bewirkt, dass die Headsetanzeige kurz einfriert.
- Die Microsoft Edge Kachel wird nicht mehr im Windows Mixed Reality Startmenü angezeigt (Sie finden sie im Ordner "Klassische Apps").
- Windows aus dem vorherigen Microsoft Edge werden immer noch um die Mixed Reality Startumgebung platziert, können aber nicht verwendet werden. Wenn Sie versuchen, diese Fenster zu aktivieren, wird Edge in der Desktop-App gestartet.
- Wenn Sie einen Link in der Mixed Reality Startumgebung auswählen, wird anstelle der Mixed Reality Startumgebung ein Webbrowser auf dem Desktop gestartet.
- Die WebVR Showcase-App ist im Mixed Reality Startumgebung vorhanden, obwohl WebVR nicht mehr unterstützt wird.
- Allgemeine Verbesserungen am Tastaturstart und an Visuals.

### <a name="monitor-and-input-handling-issues"></a>Probleme bei der Überwachung und Eingabebehandlung

Nach dem kumulativen Update 2020-01 für Windows 10 Version 1903 (oder höher) werden virtuelle Monitore während Windows Mixed Reality Sitzungen als generische physische Monitore in **Einstellungen > System > Display** angezeigt. Einige Kunden, insbesondere bei mehr als einem physischen Monitor, bemerken möglicherweise Probleme mit dem Desktoplayout und der Eingabebehandlung.

**Warum dies geschieht**

Die Unterstützung für klassische Win32-Anwendungen in Windows Mixed Reality wurde mit dem [Windows 10 May 2019 Update](/windows/mixed-reality/enthusiast-guide/release-notes-may-2019)eingeführt. Um diese Unterstützung zu aktivieren, muss ein virtueller Monitor zum Hosten der Win32-Anwendung erstellt werden. Jedes Mal, wenn eine neue Win32-Anwendung gestartet wird, muss ein anderer virtueller Monitor erstellt werden. Leider ist das Erstellen eines virtuellen Monitors eine intensive Aufgabe, die dazu führen kann, dass die Headsetanzeige kurz einfriert. Kunden haben uns Feedback dazu geboten, dass es sich dabei um ein hervorragendes und unterbrechungsfreies Erlebnis handelt. Aufgrund des Feedbacks und der erhöhten Win32-Anwendungsnutzung haben wir die Entscheidung getroffen, drei virtuelle Monitore während des Starts von Windows Mixed Reality vorab zuzuordnen. Dadurch werden Unterbrechungen verhindert, und Kunden können bis zu drei gleichzeitige Win32-Anwendungen starten, ohne dass die Headsetanzeige einfriert.

**Problemumgehung**

Wir haben seitdem Feedback erhalten, dass einige Kunden, insbesondere kunden mit mehreren physischen Monitoren, diese vorab zugeordnete virtuelle Überwachung deaktivieren möchten. Um Kunden die Kontrolle zu geben, haben wir eine Problemumgehung aktiviert, die das Ändern eines Registrierungsschlüsselwerts umfasst, der mit den folgenden Windows Updates verfügbar ist:

- 2020-07 Cumulative Update Preview for Windows 10 Version 2004 (KB4568831)
- 2020-10 Cumulative Update Preview for Windows 10 Version 1909 (KB4580386)
- 2020-10 Cumulative Update Preview for Windows 10 Version 1903 (KB4580386)

>[!NOTE]
>Das Ändern von Registrierungsschlüsselwerten ist für fortgeschrittene Benutzer vorgesehen.

>[!WARNING]
>Das Deaktivieren der vorab zugewiesenen virtuellen Monitore kann dazu führen, dass die Headsetanzeige beim Starten einer Win32-Anwendung (z. B. Stream, der neuen Microsoft Edge oder Google Chrome) in Windows Mixed Reality kurz fixiert wird.

So deaktivieren Sie die Vorabzuordnung des virtuellen Monitors:
1. Überprüfen Sie **Windows Update** auf eine der oben aufgeführten Versionen Windows 10 kumulativen Updates, und installieren Sie das Update, sofern verfügbar. Sie finden das Update unter **Optionale Updates** oder **Erweiterte Optionen** auf der Seite Windows Updateeinstellungen.
2. Starten **des Registrierungs-Editors**
3. Navigieren Sie zu "HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Holographic\"
4. Wenn die REG_DWORD "PreallocateVirtualMonitors" nicht vorhanden ist, erstellen Sie sie, indem **Sie edit > New > DWORD(32-bit) Value (Neuen > DWORD-Wert bearbeiten)** auswählen und PreallocateVirtualMonitors als Namen eingeben.
5. Wenn die REG_DWORD "PreallocateVirtualMonitors" vorhanden ist (oder Sie sie gerade erstellt haben), doppelklicken Sie auf den Eintrag, und ändern Sie "Wertdaten" von 1 (standardwert) in 0 (null).
    * TRUE – 1
    * FALSE : 0

Virtuelle Monitore werden jetzt zugeordnet, wenn Sie versuchen, eine Win32-Anwendung in Windows Mixed Reality zu starten, anstatt sie vorab zuzuordnen. Um dies zurückzusetzen und die Vorabzuordnung des virtuellen Monitors erneut zu aktivieren, geben Sie die DWORD-Wertdaten auf 1 zurück.

### <a name="other-known-issues"></a>Andere bekannte Probleme

-   Audiodaten aus Microsoft Edge Fenstern werden nicht räumlich verräumlicht.

## <a name="see-also"></a>Weitere Informationen

* [Übersicht über WebXR](../develop/javascript/webxr-overview.md)