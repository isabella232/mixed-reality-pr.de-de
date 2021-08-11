---
title: Versionshinweise – April 2018
description: Bleiben Sie über HoloLens und Windows Mixed Reality Versionshinweise für das Update vom april 2018/RS4 Windows 10 auf dem laufenden.
author: mattzmsft
ms.author: mazeller
ms.date: 05/21/2018
ms.topic: article
keywords: Versionshinweise, Version, Windows 10, Build, rs4, os
ms.openlocfilehash: 27f80d659c63362191a80eeae973111ca342090901c243772868d1a7c11e24d3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202432"
---
# <a name="release-notes---april-2018"></a>Versionshinweise – April 2018

Das **[update Windows 10 April 2018](https://blogs.windows.com/windowsexperience/2018/04/30/whats-new-in-the-windows-10-april-2018-update)** (auch als RS4 bezeichnet) enthält neue Features für HoloLens und Windows Mixed Reality immersive Headsets, die mit PCs verbunden sind. 

Öffnen Sie die Einstellungen-App, wechseln  Sie zu Update & **Security (& Sicherheit** aktualisieren), und wählen Sie dann die Schaltfläche Nach **Updates suchen** aus, um ein Update auf das neueste Release für beide Gerätetypen zu starten. Auf einem Windows 10 PC können Sie das Windows 10 April 2018-Update auch manuell installieren, indem Sie das [Windows Medienerstellungstool verwenden.](https://www.microsoft.com/software-download/windows10)

**Neuestes Release für Desktop:** update Windows 10 April 2018 (**10.0.17134.1**)<br>
**Neuestes Release für HoloLens:** Windows 10 Update vom April 2018 (**10.0.17134.80**)<br>
<br>

>[!VIDEO https://www.youtube.com/embed/O-84oWjSbr0]

*Eine Nachricht von Alex Kipman und eine Übersicht über neue Mixed Reality-Features im update Windows 10 April 2018*

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>Neue Features für Windows Mixed Reality immersive Headsets

Das update Windows 10 April 2018 enthält viele Verbesserungen für die Verwendung von Windows Mixed Reality immersiven Headsets (VR) mit Ihrem Desktop-PC, z. B.: 

* **Neue Umgebungen für die Mixed Reality Startumgebung:** Wählen Sie zwischen der Haus an den Klippen und der neuen Sky dll-Umgebung aus, indem Sie im Startmenü Die Option **Orte** auswählen. Wir haben auch [ein experimentelles Feature](/windows/mixed-reality/design/add-custom-home-environments) hinzugefügt, mit dem Sie benutzerdefinierte Umgebungen verwenden können, die Sie erstellt haben.
* **Schnellzugriff zur Mixed Reality-Erfassung:** Nehmen Sie Mixed Reality-Fotos mithilfe eines Bewegungscontrollers für Umgebungen und Apps auf, erfassen Sie jedoch keine inhalte, die mit DRM geschützt sind. Halten Sie die schaltfläche Windows gedrückt, und tippen Sie dann auf den Trigger. .
* Neue Optionen zum Starten und Ändern der Größe von **Inhalten:** Apps werden jetzt automatisch vor Ihnen platziert, wenn Sie sie über die Startmenü starten. Sie können jetzt auch die Größe von 2D-Apps ändern, indem Sie die Ränder und Ecken des Fensters ziehen.
* **Einfaches Springen zu Inhalten mit dem Sprachbefehl "Teleport"** – Schnelles Teleportieren vor Inhalten im Windows Mixed Reality Home, indem sie inhalten und "teleport" sagen.
* **[Animierte 3D-App-Startelemente](/windows/mixed-reality/distribute/creating-3d-models-for-use-in-the-windows-mixed-reality-home#animation-guidelines) und [3D-Objekte](/windows/mixed-reality/distribute/enable-placement-of-3d-models-in-the-home) für die Mixed Reality Startumgebung**. Sie können jetzt Animationen zu 3D-App-Startmodellen hinzufügen und Benutzern ermöglichen, 3D-Modelle von einer Webseite oder 2D-App in der Windows Mixed Reality Zu hause zu platzieren.
* **[Verbesserungen an Windows Mixed Reality für SteamVR:](/windows/mixed-reality/develop/porting-apps/updating-your-steamvr-application-for-windows-mixed-reality)** Windows Mixed Reality für SteamVR ist aufgrund neuer Upgrades nicht "frühzeitig verfügbar", einschließlich: haptisches Feedback bei der Verwendung von Motion-Controllern, verbesserte Leistung und Zuverlässigkeit sowie Verbesserungen der Darstellung von Motion-Controllern in SteamVR.
* **Weitere Verbesserungen:** Aktualisierte einstellungen für die automatische Leistung bieten eine optimierte Umgebung (Sie können diese Einstellung [manuell außer Kraft setzen).](#visual-quality) Setup bietet nun ausführlichere Informationen zu allgemeinen Kompatibilitätsproblemen mit USB 3.0-Controllern und -Grafikkarten.

## <a name="new-features-for-hololens"></a>Neue Features für HoloLens

Das Windows 10 April 2018-Update ist für alle HoloLens Kunden eingetroffen! Dieses Update ist mit Verbesserungen gepackt, die seit der letzten Hauptversion von HoloLens Software im [August 2016](release-notes-august-2016.md)eingeführt wurden.

### <a name="for-everyone"></a>Für alle Benutzer

<table>
  <tr>
    <th>Funktion</th><th>Details</th><th>Anweisungen</th>
  </tr>
  <tr>
    <td>Automatische Platzierung von 2D- und 3D-Inhalten beim Start</td><td>Ein 2D-App-Start- oder 2D-UWP-App wird automatisch in der Welt in einer optimalen Größe und Entfernung platziert, wenn es gestartet wird, anstatt dass der Benutzer sie platzieren muss. Wenn eine <a href="/windows/mixed-reality/design/app-views">immersive App</a> einen 2D-App-Starter anstelle eines <a href="/windows/mixed-reality/distribute/3d-app-launcher-design-guidance">3D-App-Starters</a>verwendet, startet die immersive App automatisch vom 2D-App-Starter aus wie in RS1.<br><br>Ein 3D-App-Starter aus dem Startmenü auch automatische Orte auf der Ganzen Welt. Anstatt die App automatisch zu starten, können Benutzer dann auf den Start auf klicken, um die immersive App zu starten. 3D-Inhalt, der über die Hologramme-App und über Edge geöffnet wird, wird auch an automatischen Orten auf der Ganzen Welt geöffnet.</td><td>Wenn Sie eine App über die Startmenü öffnen, werden Sie nicht aufgefordert, sie auf der ganzen Welt zu platzieren.<br><br>Wenn die Platzierung des<a href="/windows/mixed-reality/distribute/3d-app-launcher-design-guidance">2D-App-/3D-App-Starters</a> nicht optimal ist, können Sie sie mithilfe der unten beschriebenen neuen, fließenden App-Manipulationen einfach verschieben. Sie können den 2D-App-Start-/3D-Inhalt auch neu positionieren, indem Sie "Verschieben" sagen und dann anvieren, um den Inhalt neu zu positionieren.</td>
  </tr>
  <tr>
    <td>Fluide App-Manipulation</td><td>Verschieben, Ändern der Größe und Drehen von 2D- und 3D-Inhalten, ohne in den Modus "Anpassen" wechseln zu müssen.</td><td>Um eine 2D-UWP-App oder ein 2D-App-Starter zu verschieben, betrachten Sie einfach die App-Leiste, und verwenden Sie dann die Geste tippen + halten + ziehen. Sie können 3D-Inhalt verschieben, indem Sie an einer beliebigen Stelle im Objekt und dann mithilfe von Tippen + Halten + Ziehen.<br><br>Um die Größe des 2D-Inhalts zu ändern, können Sie an seine Ecke anvisieren. Der Anvisieren-Cursor wird in einen Cursor zur Größenänderung umgewandelt. Anschließend können Sie auf + halten und ziehen, um die Größe zu ändern. Sie können 2D-Inhalte auch größer oder breiter gestalten, indem Sie ihre Ränder betrachten und ziehen.<br><br>Um die Größe des 3D-Inhalts zu ändern, heben Sie beide Hände in den Gestenrahmen hoch und zeigen an der bereiten Position nach oben. Sie sehen, wie sich der Cursor in einen Zustand mit zwei kleinen Händen wandelt. Tippen Und halten Sie die Geste mit beiden Händen. Wenn Sie ihre Hände näher oder weiter voneinander trennen, ändern Sie die Größe des Objekts. Wenn Sie ihre Hände in Beziehung zueinander vorwärts und rückwärts bewegen, wird das Objekt gedreht. Auf diese Weise können Sie auch die Größe von 2D-Inhalten ändern/drehen.</td>
  </tr>
  <tr>
    <td>Horizontale Größenänderung der 2D-App mit Reflow</td><td>Machen Sie eine 2D-UWP-App im Seitenverhältnis breiter, um mehr App-Inhalte anzuzeigen. So können Sie z. B. die E-Mail-App breit genug machen, um den Vorschaubereich anzuzeigen.</td><td>Anvisieren Sie einfach den linken oder rechten Rand der 2D-UWP-App, um die Größe des Cursors zu ändern, und verwenden Sie dann die Geste tippen + halten + ziehen, um die Größe zu ändern.</td>
  </tr>
  <tr>
    <td>Erweiterte Sprachbefehlsunterstützung</td><td>Sie können mehr einfach mit Ihrer Stimme tun.</td><td>Probieren Sie die folgenden Sprachbefehle aus:<ul><li>"Gehe zu Start": Ruft die Startmenü auf oder beendet eine <a href="/windows/mixed-reality/design/app-views">immersive App.</a></li><li>"Verschieben": Ermöglicht das Verschieben eines Objekts.</li></ul></td>
  </tr>
  <tr>
    <td>Aktualisierte Hologramme- und Fotos-Apps</td><td>Hologramme App wurde mit neuen Hologrammen aktualisiert. Fotos App aktualisiert.</td><td>Sie werden einen aktualisierten Blick auf die Hologramme- und Fotos-Apps feststellen. Die Hologramme-App enthält mehrere neue Hologramme und einen Beschriftungsersteller für eine einfachere Texterstellung.</td>
  </tr>
  <tr>
    <td>Verbesserte Mixed Reality-Erfassung</td><td>MrC-Video zum Starten und Beenden von Hardwareverknüpfungen.</td><td>Halten Sie volume up + down für 3 Sekunden gedrückt, um mit der Aufzeichnung des MRC-Videos zu beginnen. Tippen Sie erneut auf beide, oder verwenden Sie die Geste "Bloom", um zu enden.</td>
  </tr>
  <tr>
    <td>Konsolidierte Leerzeichen</td><td>Vereinfachen Sie die Raumverwaltung für Hologramme in einem einzelnen Raum.</td><td>HoloLens findet Ihren Speicherplatz automatisch und erfordert nicht mehr, dass Sie Leerzeichen verwalten oder auswählen müssen. Wenn Sie Probleme mit Hologrammen in Ihrer Umgebung haben, können Sie zu <b>Einstellungen > System > Hologramme > Entfernen von Hologrammen in der Nähe</b>wechseln. Bei Bedarf können Sie auch <b>Alle Hologramme entfernen</b>auswählen.</td>
  </tr>
  <tr>
    <td>Verbesserte Audiointesion</td><td>Sie können jetzt in lauten Umgebungen HoloLens besser hören und mehr lebensähnlichen Sound von Anwendungen erhalten, da der Sound durch echte Wände verdeckt wird, die vom Gerät erkannt werden.</td><td>Sie müssen nichts unternehmen, um den verbesserten räumlichen Sound zu nutzen.</td>
  </tr>
  <tr>
    <td>Datei-Explorer</td><td>Verschieben und Löschen von Dateien aus HoloLens.</td><td>Sie können die <b>Datei-Explorer-App</b> verwenden, um Dateien innerhalb HoloLens zu verschieben und zu löschen.<br><br><b>Tipp:</b> Wenn keine Dateien angezeigt werden, ist der Filter "Zuletzt verwendet" möglicherweise aktiv (das Uhrsymbol ist im linken Bereich hervorgehoben). Wählen Sie zum Beheben dieses Problems </b> im linken Bereich dieses Gerätedokumentsymbol (unterhalb des Uhrsymbols) aus, oder öffnen Sie das Menü, und wählen Sie Dieses <b>Gerät</b>aus.
</td>
  </tr>
  <tr>
    <td>MTP-Unterstützung (Media Transfer Protocol)</td><td>Ermöglicht Ihrem Desktop-PC den Zugriff auf Ihre Bibliotheken (Fotos, Videos, Dokumente) auf HoloLens zur einfachen Übertragung.</td><td>Wie bei anderen mobilen Geräten verbinden Sie Ihre HoloLens mit Ihrem PC, um den <b>Datei-Explorer</b> für den Zugriff auf Ihre HoloLens Bibliotheken (Fotos, Videos, Dokumente) für die einfache Übertragung zu öffnen.<br><br><b>Tipps:</b><ul><li>Wenn keine Dateien angezeigt werden, stellen Sie sicher, dass Sie sich bei Ihrem HoloLens anmelden, um den Zugriff auf Ihre Daten zu ermöglichen.</li><li>Im <b>Datei-Explorer</b> auf Ihrem PC können Sie <b>Geräteeigenschaften</b> auswählen, um Windows Versionsnummer des Holographic-Betriebssystems (Firmwareversion) und Seriennummer des Geräts anzuzeigen.</li></ul><b>Bekanntes Problem:</b> Das Umbenennen HoloLens über <b>den Datei-Explorer</b> auf Ihrem PC ist nicht aktiviert.</td>
  </tr>
  <tr>
    <td>Netzwerkunterstützung des Captive-Portals während des Setups</td><td>Sie können Ihre HoloLens jetzt in einem Gastnetzwerk in Hotels, Konferenzcentern, Einzelhandelsladen oder Unternehmen einrichten, die das Captive Portal verwenden.</td><td>Wählen Sie während des Setups das Netzwerk aus, aktivieren Sie automatisch die Verbindung, und geben Sie die Netzwerkinformationen ein, wenn Sie dazu aufgefordert werden.</td>
  </tr>
  <tr>
    <td>Foto- und Videosynchronisierung über OneDrive-App</td><td>Ihre Fotos und Videos aus HoloLens werden jetzt über die OneDrive-App über die Microsoft Store anstatt über die Fotos-App synchronisiert.</td><td>Um dies einzurichten, laden Sie die OneDrive-App aus der Store herunter, und starten Sie sie. Bei der ersten Ausführung werden Sie aufgefordert, Ihre Fotos automatisch in OneDrive hochzuladen. Wenn diese Eingabeaufforderung nicht angezeigt wird, finden Sie die Option in den App-Einstellungen.</td>
  </tr>
</table>

### <a name="for-developers"></a>Für Entwickler

<table>
  <tr>
    <th>Funktion</th><th>Details</th><th>Anweisungen</th>
  </tr>
  <tr>
    <td>Verbesserungen bei der räumlichen Zuordnung</td><td>Qualitäts-, Vereinfachungs- und Leistungsverbesserungen.</td><td>Das Gitternetz für räumliche Zuordnungen wird übersichtlicher angezeigt– es sind weniger Dreiecke erforderlich, um die gleiche Detailebene darzustellen. Möglicherweise bemerken Sie Änderungen an der Dreiecksdichte in der Szene.</td>
  </tr>
  <tr>
    <td>Automatische Auswahl des Fokuspunkts basierend auf dem Tiefenpuffer</td><td>Durch das Übermitteln eines Tiefenpuffers an Windows können HoloLens automatisch einen Fokuspunkt auswählen, um die Hologrammstabilität zu optimieren.</td><td>Wechseln Sie in Unity zur <b>Registerkarte Edit > Project Einstellungen > Player > Universal Windows Platform > XR Einstellungen</b>, erweitern Sie das Element Windows Mixed Reality <b>SDK,</b> und aktivieren <b>Sie Die Tiefenpufferfreigabe aktivieren.</b> Dies wird automatisch auf neue Projekte überprüft.<br><br>Stellen Sie bei DirectX-Apps sicher, dass Sie die <a href="/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer">CommitDirect3D11DepthBuffer-Methode</a> für <b>holographicRenderingParameters</b> jeden Frame aufrufen, um den Tiefenpuffer für Windows.
</td>
  </tr>
  <tr>
    <td>Holographic reprojection modes (Holographic Reprojection-Modi)</td><td>Sie können jetzt die Positionsreprojektion auf HoloLens deaktivieren, um die Hologrammstabilität von festkörpergesperrten Inhalten wie 360-Grad-Video zu verbessern.</td><td>Legen Sie in Unity <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html">HolographicSettings.ReprojectionMode</a> auf <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html">HolographicReprojectionMode.OrientationOnly</a> fest, wenn der gesamte inhalt in der Ansicht fest durch den Text gesperrt ist.<br><br>Legen Sie für DirectX-Apps <a href="/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.reprojectionmode"> HolographicCameraRenderingParameters.ReprojectionMode</a> auf <a href="/uwp/api/windows.graphics.holographic.holographicreprojectionmode">HolographicReprojectionMode.OrientationOnly</a> fest, wenn der gesamte inhalt in der Ansicht fest durch den Text gesperrt ist.</td>
  </tr>
  <tr>
    <td>App-Anpassungs-APIs</td><td>Windows APIs wissen mehr darüber, wo Ihre App ausgeführt wird, z. B. ob die Anzeige des Geräts transparent (HoloLens) oder nicht transparent (immersives Headset) ist und ob die 2D-Ansicht einer UWP-App in der holografischen Shell angezeigt wird.</td><td>Unity hatte <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html">HolographicSettings.IsDisplayOpaque</a> zuvor manuell auf eine Weise verfügbar gemacht, die bereits vor diesem Build funktioniert hat.<br><br>Für DirectX-Apps können Sie jetzt auf vorhandene APIs wie <a href="/uwp/api/windows.graphics.holographic.holographicdisplay.isopaque">HolographicDisplay.GetDefault() zugreifen. IsOpaque</a> und <a href="/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview.iscurrentviewpresentedonholographicdisplay">HolographicApplicationPreview.IsCurrentViewPresentedOnHolographicDisplay</a> auch auf HoloLens.
</td>
  </tr>
  <tr>
      <td>Forschungsmodus</td><td>Ermöglicht Entwicklern den Zugriff auf wichtige HoloLens Sensoren beim Erstellen von akademischen und industriell entwickelten Anwendungen, um neue Ideen in den Bereichen Computer Vision und Roboter zu testen, einschließlich:<ul><li>Die vier Umgebungsverfolgungskameras</li><li>Zwei Versionen der Tiefenzuordnungskameradaten</li><li>Zwei Versionen eines IR-Reflektionsstreams</li></ul></td><td><a href="/windows/mixed-reality/develop/platform-capabilities-and-apis/research-mode">Dokumentation zum Forschungsmodus</a><br><a href="https://github.com/Microsoft/HoloLensForCV">Beispiel-Apps im Forschungsmodus</a></td>
  </tr>
</table>

### <a name="for-commercial-customers"></a>Für kommerzielle Kunden

<table>
  <tr>
    <th>Funktion</th><th>Details</th><th>Anweisungen</th>
  </tr>
  <tr>
    <td>Verwenden mehrerer Azure Active Directory Benutzerkonten auf einem einzelnen Gerät</td><td>Geben Sie eine HoloLens für mehrere Azure AD Benutzer frei, die jeweils über ihre eigenen Benutzereinstellungen und Benutzerdaten auf dem Gerät verfügen.</td><td><a href="/hololens/hololens-multiple-users">IT Pro Center: Freigeben von HoloLens für mehrere Personen</a></td>
  </tr>
  <tr>
    <td>Ändern Wi-Fi Netzwerk bei der Anmeldung</td><td>Ändern Sie Wi-Fi Netzwerk, bevor Sie sich anmelden, damit sich ein anderer Benutzer zum ersten Mal mit seinem Azure AD Benutzerkonto anmelden kann, sodass Benutzer Geräte an verschiedenen Standorten und Auftragswebsites freigeben können.</td><td>Auf dem Anmeldebildschirm können Sie das Netzwerksymbol unterhalb des Kennwortfelds verwenden, um eine Verbindung mit einem Netzwerk herzustellen. Dies ist hilfreich, wenn Sie sich zum ersten Mal bei einem Gerät anmelden.</td>
  </tr>
  <tr>
    <td>Einheitliche Registrierung</td><td>Es ist jetzt für einen HoloLens Benutzer, der das Gerät mit einem persönlichen Microsoft-Konto eingerichtet hat, einfach, ein Arbeitskonto (Azure AD) hinzuzufügen und das Gerät dem MDM-Server hinzuzufügen.</td><td>Melden Sie sich mit einem Azure AD-Konto an, und die Registrierung erfolgt automatisch.</td>
  </tr>
  <tr>
    <td>E-Mail-Synchronisierung ohne MDM-Registrierung</td><td>Unterstützung für die E-Mail-Synchronisierung Exchange Active Sync (EAS), ohne dass eine MDM-Registrierung erforderlich ist.</td><td>Sie können E-Mails jetzt synchronisieren, ohne sich bei MDM zu registrieren. Sie können das Gerät mit einem Microsoft-Konto einrichten, die E-Mail-App herunterladen und installieren und direkt ein E-Mail-Konto hinzufügen.</td>
  </tr>
</table>

### <a name="for-it-pros"></a>Für IT-Spezialisten

<table>
  <tr>
    <th>Funktion</th><th>Details</th><th>Anweisungen</th>
  </tr>
  <tr>
    <td>Neuer Betriebssystemname "Windows Holographic for Business"</td><td>Eindeutige Editionsbenennung, um Verwirrung bei der Lizenzanwendung für Editionsupgrades zu vermeiden, wenn Commercial Suite-Features auf HoloLens aktiviert sind.</td><td>In Einstellungen > <b>System > About</b>können Sie sehen, welche Edition von Windows Holographic auf Ihrem Gerät enthalten ist. "Windows Holographic for Business" wird angezeigt, wenn ein Editionsupdate angewendet wurde, um Commercial Suite-Features zu aktivieren. Erfahren Sie, wie Sie <a href="/hololens/hololens-upgrade-enterprise">Windows Holographic for Business Features entsperren.</a></td>
  </tr>
  <tr>
  <td>Windows Konfigurations-Designer (WCD)</td><td>Erstellen und bearbeiten Sie Bereitstellungspakete, um HoloLens über eine aktualisierte WCD-App zu konfigurieren. Einfacher HoloLens-Assistent für Editionsupdates, konfigurierbare OOBE, Region/Zeitzone, Massen-Azure AD Token, Netzwerk und Entwickler-CSP. Erweiterter Editor, gefiltert nach HoloLens unterstützten Optionen, einschließlich zugewiesener Zugriffs- und Kontoverwaltungs-CSPs.</td><td><a href="/hololens/hololens-provisioning">IT Pro Center: Konfigurieren HoloLens mithilfe eines Bereitstellungspakets</a></td>
  </tr>
  <tr>
    <td>Konfigurierbares Setup (OOBE)</td><td>Blenden Sie kalibrierte, gesten-/anvtraining und Wi-Fi Konfigurationsbildschirme während des Setups aus.</td><td><a href="/hololens/hololens-provisioning#create-a-provisioning-package-for-hololens-using-the-hololens-wizard">IT Pro Center: Konfigurieren HoloLens mithilfe eines Bereitstellungspakets</a></td>
  </tr>
  <tr>
    <td>Unterstützung von Massen-Azure AD-Token</td><td>Registrieren Sie das Gerät vorab bei Azure AD Verzeichnismandanten, um den Benutzersetupflow zu beschleunigten.</td><td><a href="/hololens/hololens-provisioning">IT Pro Center: Konfigurieren HoloLens mithilfe eines Bereitstellungspakets</a></td>
  </tr>
  <tr>
  <td>DeveloperSetup-CSP</td><td>Stellen Sie das Profil bereit, um HoloLens im Entwicklermodus einzurichten. Nützlich für Entwicklungs- und Demogeräte.</td><td><a href="/hololens/hololens-provisioning">IT Pro Center: Konfigurieren HoloLens mithilfe eines Bereitstellungspakets</a></td>
  </tr>
  <tr>
  <td>AccountManagement-CSP</td><td>Geben Sie ein HoloLens Gerät frei, und entfernen Sie Benutzerdaten nach dem Abmelden oder Inaktivitäts-/Speicherschwellenwerten für die temporäre Nutzung. Unterstützt Azure AD Konten.</td><td><a href="/hololens/hololens-provisioning">IT Pro Center: Konfigurieren HoloLens mithilfe eines Bereitstellungspakets</a></td>
  </tr>
  <tr>
  <td>Zugewiesener Zugriff</td><td>Windows zugewiesenen Zugriff für Erstzeilenmitarbeiter oder Demos. Einzel- oder Multi-App-Sperrung. Entwickler müssen nicht entsperren.</td><td><a href="/hololens/hololens-kiosk">IT Pro Center: Einrichten HoloLens im Kioskmodus</a></td>
  </tr>
  <tr>
  <td>Gastzugriff für Kioskgeräte</td><td>Windows zugewiesenen Zugriff mit kennwortfreiem Gastkonto für Demos. Einzel- oder Multi-App-Sperrung. Entwickler müssen nicht entsperren.</td><td><a href="/hololens/hololens-kiosk#guest">IT Pro Center: Einrichten HoloLens im Kioskmodus</a></td>
  </tr>
  <tr>
    <td>Einrichten der Diagnose (OOBE)</td><td>Abrufen von Diagnoseprotokollen aus HoloLens, damit Sie Azure AD Anmeldefehler beheben können (bevor Feedback-Hub für den Benutzer verfügbar ist, dessen Anmeldung fehlgeschlagen ist).</td><td>Wenn das Setup oder die Anmeldung fehlschlägt, wählen Sie die neue Option <b>Informationen sammeln</b> aus, um Diagnoseprotokolle für die Problembehandlung abzurufen.</td>
  </tr>
  <tr>
    <td>Ablauf des lokalen Kontos mit unbestimmtem Kennwort</td><td>Entfernen Sie die Unterbrechung der Geräterücksetzung, wenn das Kennwort des lokalen Kontos abläuft.</td><td>Bei der Bereitstellung eines lokalen Kontos müssen Sie das Kennwort nicht mehr alle 42 Tage in <b>Einstellungen</b>ändern, da das Kontokennwort nicht mehr abläuft.</td>
  </tr>
  <tr>
    <td>MDM-Synchronisierungsstatus und Details</td><td>Standard-Windows-Funktionalität, um den MDM-Synchronisierungsstatus und Details aus HoloLens zu verstehen.</td><td>Sie können den MDM-Synchronisierungsstatus für ein Gerät in <b>Einstellungen > Accounts > Access Work or School > Info</b>überprüfen. Im <b> Abschnitt Gerätesynchronisierungsstatus <b> können Sie eine Synchronisierung starten, von MDM verwaltete Bereiche anzeigen und einen erweiterten Diagnosebericht erstellen und exportieren.</td>
  </tr>
</table>

## <a name="known-issues"></a>Bekannte Probleme

Wir haben hart daran gearbeitet, eine hervorragende Windows Mixed Reality zu bieten, aber wir verfolgen weiterhin einige bekannte Probleme. Wenn Sie andere finden, senden Sie [uns Feedback.](/windows/mixed-reality/give-us-feedback)

### <a name="hololens"></a>HoloLens

#### <a name="after-update"></a>Nach dem Update

Nach dem Aktualisieren von RS1 auf RS4 auf Ihrem HoloLens können folgende Probleme auftreten:
* Zurücksetzen von **Pins:** Die an Ihre Startmenü angehefteten 3x3-Apps werden nach dem Update auf die Standardwerte zurückgesetzt. 
* **Zurücksetzung von Apps und platzierten Hologrammen:** Apps, die in Ihrer Welt platziert werden, werden nach dem Update entfernt und müssen im gesamten Bereich neu platziert werden. 
* **Feedback-Hub werden möglicherweise nicht sofort gestartet:** Unmittelbar nach dem Update dauert es einige Minuten, bis Sie einige Posteingangs-Apps wie Feedback-Hub starten können, während sie sich selbst aktualisieren. 
* **Unternehmenszertifikate Wi-Fi müssen erneut synchronisiert werden.** Wir untersuchen ein Problem, das erfordert, dass die HoloLens mit einem anderen Netzwerk verbunden ist, damit Unternehmenszertifikate erneut mit dem Gerät synchronisiert werden können, bevor die Verbindung mit Unternehmensnetzwerken mithilfe von Zertifikaten wiederhergestellt werden kann. 
* **H.265 HEVC Video Playback doesn't work ( H.265 HEVC Video Playback doesn't work** – Anwendungen, die versuchen, H.265-Videos wiederzugeben, erhalten eine Fehlermeldung. Die Problemumgehung besteht darin, [auf die Windows Geräteportal zuzugreifen,](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal) **auf** der linken Navigationsleiste Apps auszuwählen und die HEVC-Anwendung **zu entfernen.** Installieren Sie dann die neuesten [HEVC-Videoerweiterung](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) aus dem Microsoft Store. Wir untersuchen das Problem. 

#### <a name="for-developers-updating-hololens-apps-for-devices-running-windows-10-april-2018-update"></a>Für Entwickler: Aktualisieren HoloLens Apps für Geräte, auf denen Windows 10 Update vom April 2018 ausgeführt wird

Zusammen mit einer hervorragenden Liste [der neuen Features](#new-features-for-hololens)erzwingt das Windows 10 April 2018 Update (RS4) für HoloLens einige Codeverhalten, die frühere Versionen nicht ausgeführt haben:
* **Berechtigungsanforderungen für die Verwendung sensibler Ressourcen (Kamera, Mikrofon usw.):** RS4 auf HoloLens erzwingt Berechtigungsanforderungen für Apps, die auf sensible Ressourcen wie Kamera oder Mikrofon zugreifen möchten. RS1 auf HoloLens diese Eingabeaufforderungen nicht erzwingen. Wenn Ihre App also von sofortigem Zugriff auf diese Ressourcen ausgeht, kann sie in RS4 abstürzt (auch wenn der Benutzer die Berechtigung für die angeforderte Ressource erteilt). Weitere Informationen finden Sie im Entsprechenden Artikel zu [UWP-App-Funktionsdeklarationen.](/windows/uwp/packaging/app-capability-declarations)
* **Aufrufe von Apps außerhalb Ihrer eigenen** - RS4 auf HoloLens erzwingt die ordnungsgemäße Verwendung derWindows.Sys [ *tem.Startprogramm-Klasse,*](/uwp/api/Windows.System.Launcher) um eine andere App von Ihrer eigenen App aus zu starten. Beispielsweise haben wir Probleme mit Apps festgestellt, die *Windows.System.Startprogramm aufrufen. LaunchUriForResultsAsync* aus einem Nicht-ASTA-Thread (UI). Dies wäre in RS1 auf HoloLens erfolgreich, aber RS4 erfordert, dass der Aufruf im UI-Thread ausgeführt wird.

### <a name="windows-mixed-reality-on-desktop"></a>Windows Mixed Reality auf dem Desktop

#### <a name="visual-quality"></a>Visuelle Qualität

* Wenn Sie nach dem Update vom april 2018 Windows 10 feststellen, dass Grafiken unscharfer als zuvor sind oder dass das Sichtfeld auf Ihrem Headset kleiner aussieht, wurde die automatische Leistungseinstellung möglicherweise geändert, um eine ausreichende Framerate auf einer weniger leistungsstarken Grafikkarte (z. B. Nvidia 1050) beizubehalten. Sie können dies manuell außer Kraft setzen (wenn Sie dies auswählen), indem Sie zu **Einstellungen > Mixed Reality > Headset-Anzeige > Experience-Optionen navigieren > Ändern** und "Automatisch" in "90 Hz" ändern. Sie können auch versuchen, **die visuelle Qualität** (auf der gleichen seite Einstellungen) in "Hoch" zu ändern.

#### <a name="windows-mixed-reality-setup"></a>Windows Mixed Reality-Setup

* Wenn Sie Windows mit einem verbundenen Headset einrichten, ist Ihr PC-Monitor möglicherweise leer. Trennen Sie Ihr Headset, um die Ausgabe an Ihren PC-Monitor zu aktivieren, um Windows Setup abzuschließen.
* Wenn sie keine Verbundenen haben, fehlen Ihnen möglicherweise Tipps, wenn Sie das Windows Mixed Reality Startseite zum ersten Mal besuchen.
* Andere Bluetooth Geräte können zu Störungen bei Motion-Controllern führen. Wenn bei den Motion-Controllern Verbindungs-/Kopplungs-/Nachverfolgungsprobleme auftreten, stellen Sie sicher, dass das Bluetooth Radio (wenn ein externer Dongle) an eine nicht erreichbare Position und nicht direkt neben einem anderen Bluetooth Dongle angeschlossen ist. Versuchen Sie auch, andere Bluetooth Peripheriegeräte während Windows Mixed Reality Sitzungen herunterzuschalten, um festzustellen, ob dies hilfreich ist.

#### <a name="games-and-apps-from-the-microsoft-store"></a>Spiele und Apps aus dem Microsoft Store

* Einige grafisch intensive Spiele, z. B. ForzaUngs 7, können leistungsprobleme auf weniger leistungsfähigen PCs verursachen, wenn sie innerhalb Windows Mixed Reality wiedergegeben werden.

#### <a name="audio"></a>Audio

* Wenn Cortana auf Ihrem Host-PC aktiviert ist, bevor Sie Ihr Windows Mixed Reality Headset verwenden, verlieren Sie möglicherweise die Raumklangsimulation, die auf die Apps angewendet wird, die Sie im Windows Mixed Reality Haus platzieren. 
   * Die Umarbeitung besteht darin, "Windows Sonic für Kopfhörer" auf allen Audiogeräten zu aktivieren, die an Ihren PC angefügt sind, sogar auf Ihrem Mit Headset verbundenen Audiogerät:
      1. Klicken Sie mit der linken Maustaste auf das Lautsprechersymbol auf der Desktoptaskleiste, und wählen Sie aus der Liste der Audiogeräte aus.
      2. Klicken Sie auf der Desktoptaskleiste mit der rechten Maustaste auf das Lautsprechersymbol, und wählen Sie im Menü "Speaker setup" (Lautsprechereinrichtung) die Option "Windows Sonic für Kopfhörer" aus.
      3. Wiederholen Sie diese Schritte für alle Audiogeräte (Endpunkte).
   * Eine weitere Option ist das Deaktivieren von "Let Cortana respond to Hey Cortana" in **Einstellungen**  >  **Cortana** on your desktop before launch Windows Mixed Reality.
* Wenn ein anderes Multimedia-USB-Gerät (z. B. ein Webnadel) denselben USB-Hub (entweder extern oder innerhalb Ihres PCs) mit dem Windows Mixed Reality Headset teilt, können in seltenen Fällen die Audiobuchsen/-stecknadeln des Headsets entweder einen soundenden Sound oder gar keine Audiodaten aufweisen. Sie können dies über Ihr Headset an einem USB-Anschluss beheben, der nicht denselben Hub wie das andere Gerät verwendet, oder Ihr anderes USB-Multimediagerät trennen/deaktivieren.
* In seltenen Fällen kann der USB-Hub des Host-PCs nicht genügend Strom für das Windows Mixed Reality Headset bereitstellen, und Sie bemerken möglicherweise einen Rauschen von den mit dem Headset verbundenen Lautsprechern.

#### <a name="holograms"></a>Holograms

* Wenn Sie eine große Anzahl von Hologrammen in Ihrem Windows Mixed Reality Haus platziert haben, werden einige möglicherweise ausgeblendet und wieder angezeigt, wenn Sie sich umsehen. Um dies zu vermeiden, entfernen Sie einige der Hologramme in diesem Bereich der Windows Mixed Reality Startseite.

#### <a name="motion-controllers"></a>Bewegungscontroller

* Wenn die Eingabe nicht an das Headset weitergeleitet wird, verschwindet der Motion Controller kurz, wenn er neben der Raumgrenze gehalten wird. Wenn Sie Win+Y drücken, um sicherzustellen, dass auf dem Desktopmonitor ein blaues Banner angezeigt wird, wird dies behoben. 
* Wenn Sie in Microsoft Edge auf eine Webseite klicken, wird der Inhalt gelegentlich vergrößert, anstatt zu klicken.

#### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>Desktop-App im Windows Mixed Reality Startseite

* Snipping Tool funktioniert in der Desktop-App nicht.
* Die Desktop-App bleibt beim Neustart nicht erhalten.
* Wenn Sie Mixed Reality-Portal Vorschauversion auf Ihrem Desktop verwenden, werden Sie beim Öffnen der Desktop-App im Windows Mixed Reality Home möglicherweise den Unendlichkeitsspiegelungseffekt bemerken. 
* Das Ausführen der Desktop-App kann zu Leistungsproblemen auf PCs ohne Ultra-Windows Mixed Reality führen. es wird nicht empfohlen.  
* Die Desktop-App kann automatisch gestartet werden, da ein unsichtbares Fenster auf Desktop den Fokus besitzt. 
* Die Eingabeaufforderung für die Desktopbenutzerkontosteuerung macht das Headset schwarz, bis die Eingabeaufforderung abgeschlossen ist.

#### <a name="windows-mixed-reality-for-steamvr"></a>Windows Mixed Reality für SteamVR

* Möglicherweise müssen Sie Mixed Reality-Portal nach dem Update starten, um sicherzustellen, dass die erforderlichen Softwareupdates für das Windows 10 April 2018-Update abgeschlossen wurden, bevor Sie Dies ist ein Start von SteamVR. 
* Sie müssen eine aktuelle Version von Windows Mixed Reality verwenden, damit SteamVR mit dem Windows 10 April 2018-Update kompatibel bleibt. Stellen Sie sicher, dass automatische Updates für Windows Mixed Reality für SteamVR aktiviert sind, das sich im Abschnitt "Software" Ihrer Bibliothek in Steam befindet.  

#### <a name="other-issues"></a>Andere Probleme

>[!IMPORTANT]
>In einer frühen Version des updates vom april 2018 Windows 10, das per Push an Insider (Version 17134.5) übertragen wurde, fehlte ein Softwareteil, der zum Ausführen von Windows Mixed Reality erforderlich war. Es wird empfohlen, diese Version zu vermeiden, wenn Sie Windows Mixed Reality verwenden. 

Wir haben eine Leistungsregression ermittelt, wenn wir Surface Book 2 in der ersten Version dieses Updates (10.0.17134.1) verwenden, an deren Behebung wir in einem zukünftigen Updatepatch arbeiten. Es wird empfohlen, zu warten, bis dies behoben wurde, bevor Sie das Update manuell aktualisieren oder warten, bis das Update normal ausgeführt wird.

## <a name="provide-feedback-and-report-issues"></a>Bereitstellen von Feedback und Melden von Problemen

Verwenden Sie die [Feedback-Hub-App auf Ihrem HoloLens- oder Windows 10-PC,](/windows/mixed-reality/give-us-feedback) um Feedback zu geben und Probleme zu melden. Die Verwendung von Feedback-Hub stellt sicher, dass alle erforderlichen Diagnoseinformationen enthalten sind, damit unsere Techniker das Problem schnell debuggen und beheben können.

>[!NOTE]
>Achten Sie darauf, dass Sie die Eingabeaufforderung akzeptieren, in der Sie gefragt werden, ob sie Feedback-Hub möchten, auf Ihren Ordner Dokumente zuzugreifen (wählen Sie **Ja** aus, wenn Sie dazu aufgefordert werden).

## <a name="prior-release-notes"></a>Anmerkungen zu früheren Versionen

* [Versionshinweise – Oktober 2017](release-notes-october-2017.md)
* [Versionshinweise – August 2016](release-notes-august-2016.md)
* [Versionshinweise – Mai 2016](release-notes-may-2016.md)
* [Versionshinweise – März 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Siehe auch
* [Unterstützung für immersive Headsets (externer Link)](./troubleshooting-windows-mixed-reality.md)
* [HoloLens-Unterstützung (externer Link)](https://support.microsoft.com/products/hololens)
* [Installieren der Tools](/windows/mixed-reality/develop/install-the-tools)
* [Geben Sie uns Feedback](/windows/mixed-reality/give-us-feedback)