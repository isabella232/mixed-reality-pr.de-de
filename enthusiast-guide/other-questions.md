---
title: Häufig gestellte Fragen zu immersiver Hardware
description: Zusätzliche Windows Mixed Reality Tipps zur Problembehandlung, die über unsere Standarddokumentation zur Kundenunterstützung hinausgehen.
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Troubleshoot, Errors, Help, Support, Uninstalling Windows Mixed Reality, Supported Languages
appliesto:
- Windows 10
ms.openlocfilehash: 9de3ecfe2f2fc58a0afee0d7702b15131b15b12086d9f4f9851b3a9d4920afe3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219716"
---
# <a name="other-questions"></a>Andere Fragen

## <a name="my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors"></a>Mein Grafiktreiber wird nicht unterstützt (ich erhalte Fehler beim Grafiktreiber).

Suchen Sie nach "dxdiag", und führen Sie sie aus:

1.  Wenn das Ergebnis "Basic Renderer" ist, wird der Grafiktreiber nicht installiert. So beheben Sie dieses Problem:
    * Wechseln Sie zu **Geräte-Manager > Aktion > Überprüfung auf Hardwareänderungen.**
    * Verwenden Sie Windows Update, um den Treiber zu aktualisieren.
    * Wenn das Problem dadurch nicht behoben wird, wechseln Sie zur Website des Herstellers, und installieren Sie das neueste Treiberupdate. 
    * Wenn für Ihre GPU kein Update verfügbar ist, wird WMR auf Ihrem Gerät möglicherweise nicht unterstützt. Wenn Sie der Meinung sind, dass dies der Sollte sein sollte, wenden Sie sich an den [Support.](https://support.microsoft.com)
2.  Wenn Sie eine "WDDM 2.1" oder eine niedrigere Version erhalten, ist der Grafiktreiber installiert, aber möglicherweise nicht die neueste Version. So erhalten Sie die neueste Version:
    * Verwenden Sie Windows Update, um den Treiber zu aktualisieren.
    * Wenn das Problem mit diesem Update nicht behoben wird, wechseln Sie zur Website des Herstellers, und installieren Sie das neueste Treiberupdate. 
    * Wenn für Ihre GPU kein Update verfügbar ist, wird WMR auf Ihrem Gerät möglicherweise nicht unterstützt. Wenn Sie der Meinung sind, dass dies der Sollte sein sollte, wenden Sie sich an den [Support.](https://support.microsoft.com)

Wenn Windows Mixed Reality Setup besagt, dass Ihre Grafikkarte die Anforderungen nicht erfüllt und Sie denken, dass dies der Fall ist, stellen Sie sicher, dass Ihr Headset an die richtige Karte angeschlossen ist.

## <a name="my-samsung-odyssey-or-odyssey-headset-firmware-update-is-stuck"></a>Mein Samsung Odyssey- oder Odyssey+-Headset-Firmwareupdate bleibt hängen.

Samsung besitzt und veröffentlicht Firmwareupdates für Headsets, die über die Begleit-Apps "Samsung HMD Odyssey Setup" und "Samsung HMD Odyssey+ Setup" bereitgestellt werden. Weitere Informationen und Hilfe zu Problemen mit Samsung-Firmwareupdates erhalten Sie vom Samsung-Kundendienst.

Wenn der Firmwareupdateprozess hängen bleibt und seit mehr als fünf Minuten kein Fortschritt mehr besteht:

* Trennen Sie alle anderen USB-Geräte vorübergehend, und wiederholen Sie das Firmwareupdate.
* Verbinden Ihr Samsung-Headset an einen anderen USB 3.0-Anschluss auf Ihrem PC an.
* Deaktivieren oder deinstallieren Sie installierte Software, die Firmwareupdates beeinträchtigen kann, z. B. die AORUS-App Center von Gigabyte.
* Verwenden Sie einen anderen PC, um die Firmware des Samsung-Headsets zu aktualisieren.

## <a name="how-do-i-access-my-pc-desktop-in-mixed-reality"></a>Gewusst wie auf meinen PC-Desktop in Mixed Reality zugreifen?
Starten Sie die Desktop-App im Headset über **Windows Button > Alle Apps > Desktop,** um auf Ihren PC-Desktop in Mixed Reality zuzugreifen.

## <a name="how-can-i-see-multiple-monitors-in-mixed-reality"></a>Wie kann ich mehrere Monitore in Mixed Reality

Standardmäßig wechselt die Desktop-App automatisch, um den Monitor mit Fokus anzuzeigen. Wenn Sie alle Monitore in Mixed Reality anzeigen möchten:

* Wählen Sie das Monitorsymbol in der oberen linken Ecke der App aus.
* Deaktivieren Sie "Monitor automatisch wechseln".
* Wählen Sie den Monitor aus, den Sie anzeigen möchten.
* Starten Sie eine andere Instanz der Desktop-App.
* Wählen Sie den Monitor aus, den Sie für diese Instanz anzeigen möchten.
* Wiederholen Sie dies für alle physischen Monitore.
Sie müssen den Monitor neu auswählen, damit er bei jedem Neustart von Mixed Reality in jeder Desktop-App angezeigt wird.

## <a name="my-desktop-app-only-shows-a-black-screen"></a>Meine Desktop-App zeigt nur einen schwarzen Bildschirm an

Wenn Ihr PC über eine Nvidia-Hybrid-GPU verfügt, kann das Nvidia-Gerät, auf dem die runtimebroker.exe ausgeführt wird, auf der diskreten GPU anstelle der integrierten GPU der Grund dafür sein. Um dieses Problem zu beheben, befolgen Sie diese Anweisungen unter["Gewusst wie Erstellen von Wiesnmus-Einstellungen für ein neues Programm?".](http://nvidia.custhelp.com/app/answers/detail/a_id/2615/~/how-do-i-customize-optimus-profiles-and-settings%3F) , um C:\windows\system32\runtimebroker.exe hinzuzufügen und die Ausführung auf dem Prozessor "Integrierte Grafiken" zu erzwingen. 

## <a name="my-wi-fi-slows-down-when-im-using-windows-mixed-reality"></a>Meine Wi-Fi verlangsamt sich, wenn ich Windows Mixed Reality verwende.

Wenn Sie eine Wi-Fi-Verbindung mit 2,4 GHz verwenden, verlangsamen Ihre Motion-Controller möglicherweise das WLAN:

* Wechseln Sie zu einer 5-GHz-Wi-Fi-Verbindung, sofern verfügbar. [Weitere Informationen](https://support.microsoft.com/help/4000461)
* Verwenden Sie einen separaten Bluetooth Adapter, um Ihre Motion-Controller mit Ihrem PC zu verbinden. Weitere Informationen finden Sie [unter Empfohlene Adapter.](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)

## <a name="i-got-a-message-that-said-to-plug-in-and-charge-my-pc-why"></a>Ich habe eine Nachricht mit dem Hinweis erhalten, dass mein PC angeschlossen und in Rechnung gestellt werden soll. Warum?

Wenn Sie einen Laptop verwenden, funktioniert Windows Mixed Reality am besten, wenn der PC vollständig in Rechnung gestellt und angeschlossen ist.

## <a name="what-is-the-experience-options-setting"></a>Was ist die Einstellung "Benutzeroberflächesoptionen"?

**Einstellungen > Mixed Reality > Headset-Anzeigeoptionen > Experience** können Sie die Windows Mixed Reality Leistungseinstellungen ändern. Auf diese Weise können Sie die beste Benutzeroberfläche für Ihre Hardwarekonfiguration für eine Vielzahl von Inhalten auswählen. Sie haben drei Möglichkeiten zur Auswahl:
* Automatisch: Windows Mixed Reality bestimmen die beste Benutzeroberfläche für Ihre Hardwarekonfiguration. Für die meisten Benutzer ist dies die beste Wahl, um damit zu beginnen.
* 60 Hz: Legt die Aktualisierungsrate auf 60 Hz fest und deaktiviert bestimmte Features, z. B. Videoaufnahme und Vorschau in Mixed Reality-Portal.
* 90 Hz: Legt die Aktualisierungsrate auf 90 Hz fest.

## <a name="what-languages-are-supported-in-windows-mixed-reality"></a>Welche Sprachen werden in Windows Mixed Reality unterstützt?

Windows Mixed Reality ist in den folgenden Sprachen verfügbar:

* Chinesisch (Vereinfacht, China)
* Englisch (Australien)
* Englisch (Kanada)
* Englisch (Großbritannien)
* Englisch (USA)
* Französisch (Kanada)
* Französisch (Frankreich)
* Deutsch (Deutschland)
* Italienisch (Italien)
* Japanisch (Japan)
* Spanisch (Mexiko)
* Spanisch (Spanien)

Sie können Windows Mixed Reality verwenden, wenn Ihr PC auf eine andere Sprache festgelegt ist. Die Schnittstelle wird jedoch auf Englisch (USA) angezeigt, und Sprachbefehle und Diktat sind nicht verfügbar. Die Windows Mixed Reality Bildschirmtastatur ist nur englisch (USA). Um Text in einer anderen Sprache einzugeben, verwenden Sie eine physische Tastatur, die mit Ihrem PC verbunden ist. Sie können das Diktieren auch in einer der oben aufgeführten unterstützten Windows Mixed Reality Sprachen verwenden. Wählen Sie einfach mikrofon auf der Bildschirmtastatur aus.

Windows Mixed Reality ist auch in den folgenden Sprachen ohne Sprachbefehle oder Diktatfeatures verfügbar:
* Chinesisch (traditionell) (Taiwan und Hongkong)
* Niederländisch (Niederlande)
* Koreanisch (Korea)
* Russisch (Russische Föderation)

## <a name="i-have-questions-about-my-headset-hardware"></a>Ich habe Fragen zu meiner Headsethardware.

Ausführliche Informationen zu Ihrem Headset finden Sie beim Hersteller. Möglicherweise ist ein Produktleitfaden im Feld enthalten, oder Sie können die Website des Herstellers ausprobieren.

## <a name="how-do-i-uninstall-windows-mixed-reality"></a>Gewusst wie Windows Mixed Reality deinstallieren?

1. Trennen Sie Ihr Headset von Ihrem PC.
2. Schließen Sie Windows Mixed Reality Portal.
2. Wechseln Sie zu **Start > Einstellungen > Mixed Reality,** und wählen Sie "Deinstallieren" aus.

Wenn Sie bereit sind, Ihr Headset erneut zu verwenden, schließen Sie es an, und Windows Mixed Reality Portal führt Sie durch das Setup.

## <a name="i-got-a-we-couldnt-finish-uninstalling-windows-mixed-reality-message"></a>Ich habe die Meldung "We couldn't finish uninstalling Windows Mixed Reality" (Wir konnten die Deinstallation Windows Mixed Reality nicht abschließen) erhalten.

Einige Dateien, einschließlich Informationen zu Ihrer Umgebung, befinden sich möglicherweise noch auf Ihrem Computer. Dies kann zu Problemen führen, wenn Sie Windows Mixed Reality später neu installieren möchten. Sie können alle verbleibenden Windows Mixed Reality Informationen manuell von Ihrem PC entfernen, indem Sie die Registrierung ändern und Windows PowerShell verwenden, um Befehle auszuführen. _Wenn Sie die Registrierung falsch ändern, können schwerwiegende Probleme auftreten. Führen Sie diese Schritte sorgfältig aus. Um zusätzlichen Schutz zu erhalten, sichern Sie Ihre Registrierung, bevor Sie sie ändern, damit Sie sie wiederherstellen können, wenn ein Problem auftritt._ Weitere Informationen finden Sie unter [Sichern und Wiederherstellen der Registrierung in Windows](https://support.microsoft.com/en-us/help/322756/how-to-back-up-and-restore-the-registry-in-windows). 

So deinstallieren Sie Windows Mixed Reality mithilfe der folgenden Befehle:
1. Starten Sie Ihren PC neu.
2. Geben Sie **im Suchfeld** "regedit" ein, und wählen Sie dann "Ja" aus.
3. Entfernen Sie diese Registrierungswerte:
   <ul>
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>, und löschen Sie dann "FirstRunSucceeded".</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic\SpeechAndAudio</b>, und löschen Sie dann "PreferDesktopSpeaker" und "PreferDesktopMic".</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore&gt; Einstellungen\Holographic,</b>und löschen Sie dann "DisableSpeechInput". Hinweis: Die Registrierungselemente in HHKEY_CURRENT_USER müssen für jedes Benutzerkonto auf dem PC gelöscht werden, das Windows Mixed Reality.</li> 
    <li><b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\PerceptionSimulationExtensions</b>, und löschen Sie dann "DeviceID" und "Mode".</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>, und löschen Sie dann "OnDeviceLearningCompleted".</li> 
   </ul>
4. Entfernen Sie die folgenden Registrierungsschlüssel: <ul>
   <li> <b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore\Settings\HolographicPreferences</b></li><br/></ul>
5. Schließen Sie den Registrierungs-Editor.
6.Wechseln Sie **zu C:\Benutzer\Benutzername\AppData\Local\Packages\Microsoft.Windows. HolographicFirstRun_cw5n1h2txyewy\LocalState, und** löschen Sie "RoomBounds.json". Wiederholen Sie dies für jeden Benutzer, der die Windows Mixed Reality.
7. Öffnen Sie die Administrator-Eingabeaufforderung, und wechseln Sie zu **C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors**. Löschen Sie den Inhalt des Ordners "HeadTracking data" (aber nicht des Ordners selbst).
8.Geben Sie "powershell" in das Suchfeld ein, klicken Sie mit der rechten Maustaste auf "Windows PowerShell", und wählen Sie dann "Als Administrator ausführen" aus.
9.In Windows PowerShell: <ul>
   <li>Kopieren Sie an der Eingabeaufforderung <b>Dism /online /Get-Capabilities,</b>und fügen Sie ihn ein, und drücken Sie dann die EINGABETASTE.</b></li> 
   <li>Kopieren Sie die Funktionsidentität, die mit Analog.Holographic.Desktop beginnt. Wenn es nicht dort ist, ist das Element nicht installiert, und Sie können mit Schritt 10 springen.</li> 
   <li>Kopieren Sie die folgende Eingabeaufforderung, fügen Sie sie ein, und drücken Sie dann die EINGABETASTE: <b>Dism /online /Remove-Capability /CapabilityName: die</b> im letzten Schritt kopierte Funktionsidentität.</li>
   </ul>
10. Starten Sie Ihren PC neu.

