---
title: Weitere Fragen
description: Weitere Tipps zur Problembehandlung in Windows Mixed Reality, die über die Standard-Support Dokumentation von Kunden hinausgehen.
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, Mr, Problembehandlung, Fehler, Hilfe, Support, Deinstallieren von Windows Mixed Reality, unterstützte Sprachen
appliesto:
- Windows 10
ms.openlocfilehash: aa61148a115ae295c1dc64b575a2fae7b0111470
ms.sourcegitcommit: feceb21018ce1d966188a34bd1faeddfdc1b9544
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2020
ms.locfileid: "93044459"
---
# <a name="other-questions"></a>Weitere Fragen

## <a name="my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors"></a>Mein Grafiktreiber wird nicht unterstützt (Fehler beim Grafiktreiber Fehler).

Suchen Sie nach "Dxdiag", und führen Sie es aus:

1.  Wenn das Ergebnis "grundlegender Renderer" ist, ist der Grafiktreiber nicht installiert. So beheben Sie dieses Problem:
    * Wechseln Sie zu **Geräte-Manager > Aktion > suchen Sie nach Hardware Änderungen** .
    * Verwenden Sie Windows Update, um den Treiber zu aktualisieren.
    * Wenn das Problem hierdurch nicht behoben wird, besuchen Sie die Website des Herstellers, und installieren Sie das aktuellste Treiberupdate. 
    * Wenn ein Update für Ihre GPU nicht verfügbar ist, wird WMR möglicherweise auf Ihrem Gerät nicht unterstützt. Wenn Sie der Ansicht sind, wenden Sie sich an den [Support](https://support.microsoft.com).
2.  Wenn Sie "WDDM 2,1" oder eine niedrigere Version erhalten, wird der Grafiktreiber installiert, aber möglicherweise nicht die neueste Version. So erhalten Sie die neueste Version:
    * Verwenden Sie Windows Update, um den Treiber zu aktualisieren.
    * Wenn das Problem durch dieses Update nicht behoben werden kann, besuchen Sie die Website des Herstellers, und installieren Sie das aktuellste Treiberupdate. 
    * Wenn ein Update für Ihre GPU nicht verfügbar ist, wird WMR möglicherweise auf Ihrem Gerät nicht unterstützt. Wenn Sie der Ansicht sind, wenden Sie sich an den [Support](https://support.microsoft.com).
    
Wenn das Setup von Windows Mixed Reality besagt, dass Ihre Grafikkarte die Anforderungen nicht erfüllt, und Sie meinen, dass das Headset an die richtige Karte angeschlossen ist.

## <a name="my-samsung-odyssey-or-odyssey-headset-firmware-update-is-stuck"></a>Mein Samsung Odyssee-oder Odyssee + Headset-Firmwareupdate bleibt hängen.

Samsung besitzt und veröffentlicht mit den Geräte begleitenden Apps "Samsung HMD Odyssee Setup" und "Samsung HMD Odyssee + Setup" die durch die Geräte bereitgestellten Headset-Firmware-Updates. Weitere Informationen und Hilfe bei Problemen mit der Aktualisierung von Samsung-Firmware finden Sie unter Samsung-Kundendienst.

Wenn der Firmwareupdate nicht mehr als fünf Minuten ausgeführt wird, wird der Vorgang nicht fortgesetzt:
* Entfernen Sie alle anderen USB-Geräte vorübergehend, und wiederholen Sie das Firmwareupdate.
* Verbinden Sie Ihr Samsung-Headset mit einem anderen USB 3,0-Port auf Ihrem PC.
* Deaktivieren und/oder deinstallieren installierter Software, die Firmwareupdates beeinträchtigen kann, wie z. b. die aorus-App Center von Gigabyte.
* Verwenden Sie einen anderen PC, um das Update für die Samsung-Headset-Firmware auszuführen.

## <a name="how-do-i-access-my-pc-desktop-in-mixed-reality"></a>Gewusst wie in gemischter Realität auf My PC Desktop zugreifen?
Starten Sie die Desktop-App im Headset von **Windows, > alle apps > Desktop** , um in gemischter Realität auf Ihren PC-Desktop zuzugreifen.

## <a name="how-can-i-see-multiple-monitors-in-mixed-reality"></a>Wie können mehrere Monitore in gemischter Realität angezeigt werden?
Standardmäßig schaltet die Desktop-App automatisch ein, um den Monitor mit dem Fokus anzuzeigen. Wenn Sie alle Monitore in gemischter Realität anzeigen möchten: 
* Klicken Sie in der oberen linken Ecke der APP auf das Symbol überwachen.
* Deaktivieren Sie "Monitor automatisch wechseln".
* Wählen Sie den Monitor aus, den Sie anzeigen möchten.
* Starten Sie eine andere Instanz der Desktop-App.
* Wählen Sie den Monitor aus, den Sie in dieser Instanz sehen möchten.
* Wiederholen Sie diesen Vorgang für alle physischen Monitore.
Beachten Sie, dass Sie den Monitor erneut auswählen müssen, um bei jedem Neustart von Mixed Reality auf jeder Desktop-App angezeigt zu werden. 

## <a name="my-desktop-app-only-shows-a-black-screen"></a>Meine Desktop-App zeigt nur einen schwarzen Bildschirm an.
Wenn Ihr PC über eine NVIDIA Hybrid GPU verfügt, kann das Problem dadurch verursacht werden, dass NVIDIA-Gerät die runtimebroker.exe auf der diskreten GPU anstelle der integrierten GPU ausführen kann. Um dieses Problem zu beheben, befolgen Sie die Anweisungen unter "[Gewusst wie Erstellen von Optimus-Einstellungen für ein neues Programm](http://nvidia.custhelp.com/app/answers/detail/a_id/2615/~/how-do-i-customize-optimus-profiles-and-settings%3F)". zum Hinzufügen von C:\windows\system32\runtimebroker.exe und erzwingen der Durchführung auf dem Prozessor "integrierte Grafiken". 

## <a name="my-wi-fi-slows-down-when-im-using-windows-mixed-reality"></a>Meine Wi-Fi verlangsamt sich, wenn ich Windows Mixed Reality verwende.

Wenn Sie eine Wi-Fi Verbindung mit 2,4 GHz verwenden, verlangsamen Ihre Bewegungs Controller möglicherweise das WLAN. Probieren Sie einen der folgenden Lösungsschritte aus:
* Wechseln Sie zu einer Wi-Fi Verbindung mit 5 GHz, sofern verfügbar. [Weitere Informationen](https://support.microsoft.com/en-us/help/4000461)
* Verwenden Sie einen separaten Bluetooth-Adapter, um Ihre Motion-Controller mit Ihrem PC zu verbinden. Siehe [Empfohlene Adapter](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines).

## <a name="i-got-a-message-that-said-to-plug-in-and-charge-my-pc-why"></a>Ich habe eine Meldung mit dem anbinden und Berechnen des PCs. Warum?

Wenn Sie einen Laptop verwenden, funktioniert Windows Mixed Reality am besten, wenn der PC vollständig abgerechnet und angeschlossen ist. 

## <a name="what-is-the-experience-options-setting"></a>Was ist die Einstellung der Erfahrungs Optionen?

Mit dieser Einstellung ( **Einstellungen > gemischte Realität > Headset-Anzeige > Optionen** ) können Sie die Windows Mixed Reality-Leistungseinstellungen ändern. Dies ermöglicht es Ihnen, für eine Reihe von Inhalten die beste Leistung für Ihre Hardwarekonfiguration auszuwählen. Dies sind die folgenden Optionen:
* Automatisch: in Windows Mixed Reality wird die beste Leistung für Ihre Hardwarekonfiguration festgestellt. Für die meisten Benutzer ist dies die beste Wahl, mit der Sie beginnen können.
* 60Hz: legt die Aktualisierungsrate auf 60Hz fest und deaktiviert bestimmte Features, wie z. b. Video Erfassung und Vorschau im Mixed Reality-Portal.
* 90Hz: legt die Aktualisierungsrate auf 90Hz fest.

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

Sie können Windows Mixed Reality verwenden, wenn Ihr PC auf eine andere Sprache festgelegt ist. die Schnittstelle wird jedoch in englischer Sprache (USA) angezeigt, und Sprachbefehle und Diktat sind nicht verfügbar. Die Windows Mixed Reality-Bildschirmtastatur ist nur in englischer Sprache (USA). Um Text in einer anderen Sprache einzugeben, verwenden Sie eine physische Tastatur, die mit Ihrem PC verbunden ist. Sie können auch in einer der oben aufgeführten unterstützten Windows Mixed Reality-Sprachen Diktat verwenden – Wählen Sie einfach Mikrofon auf der Bildschirmtastatur aus.

Windows Mixed Reality ist auch in den folgenden Sprachen ohne Sprachbefehle oder Diktat Features verfügbar:
* Chinesisch (traditionell) (Taiwan und Hongkong)
* Niederländisch (Niederlande)
* Koreanisch (Korea)
* Russisch (Russische Föderation)

## <a name="i-have-questions-about-my-headset-hardware"></a>Ich habe Fragen zu meiner Headset-Hardware.

Weitere Informationen zu Ihrem Headset finden Sie unter dem Hersteller. Möglicherweise gibt es ein Produkthandbuch, oder Sie können die Website des Herstellers ausprobieren.

## <a name="how-do-i-uninstall-windows-mixed-reality"></a>Gewusst wie deinstallieren Sie Windows Mixed Reality?

1. Trennen Sie das Headset von Ihrem PC.
2. Schließen Sie das Windows Mixed Reality-Portal.
2. Wechseln Sie zu  **Start > Einstellungen > gemischte Realität** , und wählen Sie "deinstallieren" aus.

Wenn Sie bereit sind, das Headset erneut zu verwenden, binden Sie es ein, und das Windows Mixed Reality-Portal führt Sie durch das Setup.

## <a name="i-got-a-we-couldnt-finish-uninstalling-windows-mixed-reality-message"></a>Ich erhalte die Meldung "Wir konnten die Windows Mixed Reality nicht deinstallieren".

Einige Dateien, einschließlich Informationen über Ihre Umgebung, befinden sich möglicherweise weiterhin auf dem Computer. Dies kann zu Problemen führen, wenn Sie Windows Mixed Reality später neu installieren. Sie können alle verbleibenden Windows Mixed Reality-Informationen manuell von Ihrem PC entfernen, indem Sie die Registrierung ändern und Windows PowerShell verwenden, um Befehle auszuführen. _Wenn Sie die Registrierung falsch ändern, können schwerwiegende Probleme auftreten. Stellen Sie sicher, dass Sie diese Schritte sorgfältig ausführen. Um zusätzlichen Schutz zu erhalten, sichern Sie Ihre Registrierung, bevor Sie Sie ändern, damit Sie Sie wiederherstellen können, wenn ein Problem vorliegt occurrs._ Weitere Informationen finden Sie unter [Sichern und Umordnen der Registrierung in Windows](https://support.microsoft.com/en-us/help/322756/how-to-back-up-and-restore-the-registry-in-windows). 

So deinstallieren Sie Windows Mixed Reality mithilfe der folgenden Befehle:
1. Starten Sie Ihren PC neu.
2. Geben Sie im **Suchfeld** "regedit" ein, und wählen Sie dann "yes" (ja) aus.
3. Entfernen Sie diese Registrierungs Werte:
   <ul>
    <li>Löschen Sie <b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>, und löschen Sie dann "firstranunwar".</li> 
    <li>Löschen Sie <b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic\SpeechAndAudio</b>, und löschen Sie dann "preferdesktopspeaker" und "preferdesktopmic".</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore&gt; Einstellunen\holographic</b>und dann "disablespeechinput" löschen. Hinweis: die Registrierungs Elemente in HHKEY_CURRENT_USER müssen für jedes Benutzerkonto auf dem PC gelöscht werden, auf dem Windows Mixed Reality verwendet wurde.</li> 
    <li>Löschen Sie <b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\PerceptionSimulationExtensions</b>, und löschen Sie dann "DeviceID" und "Mode".</li> 
    <li>Löschen Sie <b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>, und löschen Sie dann "onde vicelearningabgeschlossene".</li> 
   </ul>
4. Entfernen Sie die folgenden Registrierungsschlüssel: <ul>
   <li> <b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore\Settings\HolographicPreferences</b></li><br/></ul>
5. Schließen Sie den Registrierungs-Editor.
6. Wechseln Sie zu " **c:\users\benutzername\appdata\local\packages\ Microsoft.Windows.HolographicFirstRun_cw5n1h2txyewy \localstate** ", und löschen Sie "RoomBounds.json". Wiederholen Sie diesen Schritt für jeden Benutzer, der Windows Mixed Reality verwendet hat.
7. Öffnen Sie admin cmd prompt, und wechseln Sie zu **c:\programdata\windowsholographicdevices\spatialstore\hololenssensoren** . Löschen Sie den Inhalt des Ordners "headtracking-Daten" (aber nicht den Ordner selbst).
8. Geben Sie "PowerShell" in das Suchfeld ein, klicken Sie mit der rechten Maustaste auf "Windows PowerShell", und wählen Sie dann "als Administrator ausführen" aus.
9. In Windows PowerShell: <ul>
   <li>Kopieren Sie an der Eingabeaufforderung das <b>/Online/Get-Capabilities</b>, und fügen Sie es ein. Drücken Sie dann die EINGABETASTE.</b></li> 
   <li>Kopieren Sie die Funktions Identität, die mit "analog. Holographic. Desktop" beginnt (wenn Sie nicht vorhanden ist), bedeutet dies, dass dieses Element nicht installiert ist. Fahren Sie in diesem Fall mit Schritt 10 fort.)</li> 
   <li>Kopieren und fügen Sie die folgende Eingabeaufforderung ein, und drücken Sie dann die EINGABETASTE: <b>/Online/Remove-Capability/CapabilityName: die Funktions Identität, die Sie im letzten Schritt kopiert</b> haben.</li>
   </ul>
10. Starten Sie den PC neu.

