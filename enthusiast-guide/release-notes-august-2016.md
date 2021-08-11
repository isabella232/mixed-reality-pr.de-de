---
title: Versionshinweise – August 2016
description: Bleiben Sie auf dem neuesten Stand HoloLens Versionshinweise für das Windows 10 Anniversary Release für Den Fall 2016.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, Versionshinweise, Betriebssystem, Plattform, Features, kommerzielle Suite
ms.openlocfilehash: 2cb6153877b27ce0e1260696447bd4c5c851c6f00a20a7889b855c5646e8871f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202460"
---
# <a name="release-notes---august-2016"></a>Versionshinweise – August 2016

Das HoloLens-Team lausiert auf Feedback von Entwicklern im Windows Insider Program, um unsere Arbeit zu priorisieren. Geben Sie [uns weiterhin Feedback](/windows/mixed-reality/give-us-feedback) über die Feedback-Hub, die [Entwicklerforen](https://forums.hololens.com) und [Twitter @HoloLens über ](https://twitter.com/hololens). Da Windows 10 Anniversary Update unterstützt, ist das HoloLens-Team gerne bereit, die holografische Erfahrung weiter zu verbessern. In diesem Update haben wir uns auf wichtige Fehlerbehebungen, Verbesserungen und einführungsfeatures konzentriert, die von Unternehmen angefordert und in der Microsoft HoloLens Commercial Suite.

**Neueste Version: Windows** Holographic August 2016 Update (**10.0.14393.0**, Windows 10 Anniversary Release)

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

Um auf das aktuelle Release  zu [aktualisieren,](/windows/mixed-reality/updating-hololens)öffnen Sie die Einstellungen-App, wechseln Sie zu *Update & Security*,und wählen Sie dann die Schaltfläche Nach *Updates suchen* aus.

## <a name="new-features"></a>Neue Funktionen

**An Prozessdebuggen** HoloLens unterstützt jetzt das Debuggen von Anfügen an Prozesse. Sie können Visual Studio 2015 Update 3 verwenden, um eine Verbindung mit einer ausgeführten App auf einem HoloLens und mit dem Debuggen [zu beginnen.](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-visual-studio#debugging-an-installed-or-running-app) Dies funktioniert, ohne dass eine Bereitstellung über ein Visual Studio muss.

**Aktualisierte HoloLens Emulator** Wir haben auch eine aktualisierte Version des HoloLens Emulator.

**Gamepad-Unterstützung** Sie können jetzt Gamepads mit Bluetooth kombinieren und HoloLens! Der neu veröffentlichte Xbox Wireless Controller S bietet Bluetooth Funktionen und kann verwendet werden, um Ihre bevorzugten Gamepad-fähigen Spiele und Apps zu spielen. Ein [Controllerupdate muss](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) angewendet werden, bevor Sie Xbox Wireless Controller S mit einem HoloLens. Xbox Wireless Controller S wird von [XInput und](/windows/win32/xinput/xinput-game-controller-apis-portal) [Windows. Gaming.Input-APIs.](/uwp/api/Windows.Gaming.Input) Sie können über die Bluetooth auf weitere [Controllermodelle Windows. Gaming.Input-API.](/uwp/api/Windows.Gaming.Input)

## <a name="improvements-and-fixes"></a>Verbesserungen und Fehlerbehebungen

Wir sind mit dem Rest des Windows 10 Anniversary-Updates synchron. Zusätzlich zu den HoloLens-spezifischen Fehlerbehebungen erhalten Sie also auch alle Verbesserungen des Windows-Updates, um die Zuverlässigkeit und Leistung der Plattform zu erhöhen. Ihr Feedback wird für Fehlerbehebungen in der Version sehr geschätzt und priorisiert.

Wir haben die folgenden Erfahrungen verbessert:
* Anmeldeerfahrungen.
* Arbeitsplatze werden beitreten.
* Energieeffizienz für Übergänge des Energiezustands von Geräten.
* Stabilität mit Mixed Reality Captures.
* Zuverlässigkeit für Bluetooth Konnektivität
* Hologrammpersistenz in Szenarios mit mehreren Apps.

Wir haben die folgenden Probleme behoben:
* Die Visual Studio Profiler und der Grafikdebugger können keine Verbindung herstellen.
* Fotos & werden nicht im Datei-Explorer im Geräteportal angezeigt.
* Die App-Leiste kann blinken, wenn der Cursor darüber im Anpassungsmodus platziert wird.
* Im Modus Anpassen ändert sich der Punktcursor für das Anvieren mit den Augen etwas langsamer in den Cursor mit vier Pfeilen.
* "Hey Cortana play music" startet nicht Groove.
* Nach dem vorherigen Update wird der Stecknadelbereich nicht ordnungsgemäß angezeigt, wenn "Gehe nach Hause" angezeigt wird.

## <a name="introducing-microsoft-hololens-commercial-suite"></a>Einführung Microsoft HoloLens Commercial Suite

Die Microsoft HoloLens Commercial Suite ist bereit für die Unternehmensbereitstellung. Wir haben von unseren [](/windows/mixed-reality/commercial-features) frühen Geschäftspartnern mehrere dringend angeforderte kommerzielle Features hinzugefügt.

Wenden Sie sich an ihren Microsoft-Konto Manager, um die Microsoft HoloLens Commercial Suite.

### <a name="key-commercial-features"></a>Wichtige kommerzielle Features 

* **Kioskmodus** Mit HoloLens Kioskmodus können Sie einschränken, welche Apps ausgeführt werden müssen, um Demo- oder Präsentationserfahrungen zu ermöglichen.<br>
  ![Im Kioskmodus wird HoloLens direkt in der App Ihrer Wahl gestartet.](images/201608-kioskmode-400px.png)
* **Verwaltung mobiler Geräte (MDM, Mobile Device Management) für HoloLens.** Ihre IT-Abteilung kann mehrere HoloLens geräte gleichzeitig mithilfe von Lösungen wie Microsoft Intune. Sie können Einstellungen verwalten, Apps auswählen, um Sicherheitskonfigurationen zu installieren und auf die Anforderungen Ihrer Organisation zugeschnitten festlegen.<br>
  ![Mobile Geräteverwaltung on HoloLens bietet geräteübergreifende Geräteverwaltung auf Unternehmensstufe auf mehreren Geräten.](images/201608-enterprisemanagement-400px.png)
* **Windows Update für Unternehmen.** Kontrollierte Betriebssystemupdates für Geräte und Unterstützung für Long-Term Servicing Branch.
* **Datensicherheit**. Die BitLocker-Datenverschlüsselung ist auf HoloLens aktiviert, um dasselbe Maß an Sicherheitsschutz wie jedes andere Windows-Gerät bereitzustellen.
* **Arbeitsplatzzugriff.** Jeder Benutzer in Ihrer Organisation kann eine Remoteverbindung mit dem Unternehmensnetzwerk über ein virtuelles privates Netzwerk in einem HoloLens. HoloLens kann auch auf WLAN-Netzwerke zugreifen, die Anmeldeinformationen erfordern.
* **Microsoft Store für Unternehmen.** Ihre IT-Abteilung kann auch einen privaten Store für Unternehmen einrichten, der nur die Apps Ihres Unternehmens für Ihre spezifische Nutzung HoloLens enthält. Verteilen Sie Ihre Unternehmenssoftware auf sichere Weise an ausgewählte Gruppen von Unternehmensbenutzern.

### <a name="development-edition-vs-commercial-suite"></a>Development Edition im Vergleich zu Commercial Suite

<table>
<tr>
<th>Funktionen</th><th>Development Edition</th><th>Commercial Suite</th>
</tr><tr>
<td>Geräteverschlüsselung (BitLocker)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Virtuelles privates Netzwerk (VPN):</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal#kiosk-mode">Kioskmodus</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Verwaltung und Bereitstellung</th>
</tr><tr>
<td>Mobile Geräteverwaltung (MDM)</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Möglichkeit zum Blockieren der Registrierungsaufhebung</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Zertifikatbasierter Zugriff auf Wi-Fi Unternehmensdaten</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft Store (Verbraucher)</td><td style="text-align: center;">Consumer</td><td style="text-align: center;">Filtern über MDM</td>
</tr><tr>
<td><a href="/microsoft-store/working-with-line-of-business-apps">Business Store-Portal</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Sicherheit und Identität</th>
</tr><tr>
<td>Anmelden mit Azure Active Directory (AAD)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Anmelden mit einem Microsoft-Konto (MSA)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Anmeldeinformationen der nächsten Generation mit PIN-Entsperrung</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="/windows-hardware/design/device-experiences/oem-secure-boot">Sicherer Start</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Wartung und Support</th>
</tr><tr>
<td>Automatische Systemaktualisierungen, sobald sie eintreffen</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="/windows/deployment/update/waas-manage-updates-wufb">Windows Update for Business</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Long Term Servicing Branch</td><td></td><td style="text-align: center;">✔️</td>
</tr>
</table>

## <a name="prior-release-notes"></a>Anmerkungen zu früheren Versionen
* [Versionshinweise – Mai 2016](release-notes-may-2016.md)
* [Versionshinweise – März 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Siehe auch
* [HoloLens – bekannte Probleme](/windows/mixed-reality/hololens-known-issues)
* [Kommerzielle Features](/windows/mixed-reality/commercial-features)
* [Installieren der Tools](/windows/mixed-reality/develop/install-the-tools)
* [Verwendung des HoloLens-Emulators](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)