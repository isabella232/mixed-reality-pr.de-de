---
title: Versionshinweise – Oktober 2017
description: Bleiben Sie auf dem neuesten Stand zu den Windows Mixed Reality Versionshinweisen für die Windows 10 Fall Creators Update (Oktober 2017).
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Versionshinweise, Version, Windows 10, Build, rs3, os
ms.openlocfilehash: 09a33e1bc4a13c75e4c8a0ee250c7b67eb8e68e21220840037085e727acfb1f3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190594"
---
# <a name="release-notes---october-2017"></a>Versionshinweise – Oktober 2017

Willkommen bei Windows Mixed Reality! Das **[Windows 10 Fall Creators Update](https://blogs.windows.com/windowsexperience/2017/10/17/whats-new-windows-10-fall-creators-update/)** Release bietet Unterstützung für neue [Windows Mixed Reality immersive Headsets](/windows/mixed-reality/discover/immersive-headset-hardware-details) und [Motion-Controller.](/windows/mixed-reality/design/motion-controllers) Sie können jetzt neue Welten erkunden, VR-Spiele spielen und immersive Unterhaltung erleben, wenn Sie mit einem [Windows Mixed Reality fähigen PC](./windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)verbunden sind.

Die freigaben Windows Mixed Reality Headsets und Motion Controller sind das Ergebnis einer enormen Teamarbeit und ein wichtiger Schritt nach vorn für die [Windows Mixed Reality-Plattform,](/windows/mixed-reality/discover/mixed-reality)einschließlich [Microsoft HoloLens](/windows/mixed-reality/hololens-hardware-details). Obwohl HoloLens kein Update mit dem Windows 10 Fall Creators Update empfängt, wurde die Arbeit an HoloLens nicht beendet. Wir werden viele Erkenntnisse und Erkenntnisse aus unserer aktuellen Arbeit für Windows Mixed Reality als Ganzes anwenden können. Tatsächlich stellen Windows Mixed Reality immersive Headsets und Motion Controller auch für HoloLens einen hervorragenden Einstiegspunkt für die Entwicklung dar, da die gleichen APIs, Tools und Konzepte für beide gelten.

Öffnen Sie zum Aktualisieren auf die  neueste Version für jedes Gerät die Einstellungen-App, wechseln Sie zu **Update & Security (Sicherheit** aktualisieren), und wählen Sie dann die Schaltfläche **Nach Updates suchen** aus. Auf einem Windows 10 PC können Sie die Windows 10 Fall Creators Update auch manuell installieren, indem Sie das [Windows Medienerstellungstool verwenden.](https://www.microsoft.com/software-download/windows10)

 **Neuestes Release für Desktop:** Windows 10 Desktop Oktober 2017 (**10.0.16299.15**, Windows 10 Fall Creators Update)<br>
 **Neuestes Release für HoloLens:** [Windows 10 Holographic August 2016](release-notes-august-2016.md) (**10.0.14393.0**, Windows 10 Anniversary Update)

>[!VIDEO https://www.youtube.com/embed/YBcLy1lkegg]

## <a name="introducing-windows-mixed-reality"></a>Einführung in Windows Mixed Reality

Der Windows 10 Fall Creators Update bietet offiziell Unterstützung für Windows Mixed Reality Headsets und Motion Controller und macht Windows 10 zum ersten räumlichen Betriebssystem der Welt. Dies umfasst u.a. die folgenden Funktionen:
* **[Vielzahl von Headsets:](https://blogs.windows.com/windowsexperience/2017/10/03/how-to-pre-order-your-windows-mixed-reality-headset/)** Windows Mixed Reality ermöglicht Partnern das Anbieten verschiedener Headsettypen ab 399 USD, gebündelt mit Motion-Controllern.
* **[Motion-Controller:](/windows/mixed-reality/design/motion-controllers)** Windows Mixed Reality Motion-Controller über Bluetooth drahtlos mit Ihrem PC gekoppelt sind und sechs Grad an Nachverfolgung, eine Vielzahl von Eingabemethoden und IMUs bieten.
* **[Einfache Einrichtung und Portabilität:](./recommended-adapters-for-windows-mixed-reality-capable-pcs.md)** Richten Sie ein, und beginnen Sie in weniger als 10 Minuten. Immersive Headsets verwenden die Inside-Out-Nachverfolgung, um Ihre Bewegung und Ihre Motion-Controller mit sechs Grad Anlauf nachzuverfolgen. Keine externen Kameras oder Lighthousemarker erforderlich!
* **[Unterstützung für eine größere Bandbreite von PCs:](./windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)** Windows Mixed Reality ermöglichen es mehr Personen als je zuvor, Desktop-VR zu erleben, mit Unterstützung für ausgewählte integrierte Grafikkarten und PCs ab 499 USD.
* **[Windows Mixed Reality Startseite:](/windows/mixed-reality/discover/navigating-the-windows-mixed-reality-home)** Das erste räumliche Betriebssystem der Welt bietet eine vertraute Heimumgebung für Multitasking mit 2D-Apps, das Starten von VR-Spielen und -Apps und das Platzieren von zierliche Hologrammen.
* **[Beeindruckende VR-Spiele und -Apps in der Microsoft Store:](https://www.microsoft.com/store/collections/MR-All-ImmersiveContent/)** Von immersiver Unterhaltung wie Hulu VR und 360-Video bis hin zu epic-Spielen wie SUPERHOT VR und Arizona Headset bietet die Microsoft Store eine Reihe von Inhalten, die sie in Windows Mixed Reality erleben können.
* Early Access von **[SteamVR:](./using-steamvr-with-windows-mixed-reality.md)** Die Windows 10 Fall Creators Update ermöglicht die Wiedergabe von SteamVR-Titeln mit Windows Mixed Reality Headsets und Controllern, sodass Windows Mixed Reality Benutzern der größte Katalog mit VR-Titeln zur Verfügung steht.

## <a name="known-issues"></a>Bekannte Probleme

Wir haben hart daran gearbeitet, eine hervorragende Windows Mixed Reality zu bieten, aber wir verfolgen weiterhin einige bekannte Probleme. Wenn Sie andere finden, [senden Sie uns Feedback.](/windows/mixed-reality/give-us-feedback)

### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>Desktop-App im Windows Mixed Reality Startseite
* Snipping Tool funktioniert in der Desktop-App nicht.
* Die Desktop-App bleibt beim Neustart nicht erhalten.
* Wenn Sie Mixed Reality-Portal Vorschauversion auf Ihrem Desktop verwenden, werden Sie beim Öffnen der Desktop-App im Windows Mixed Reality Home möglicherweise den Unendlichkeitsspiegelungseffekt bemerken. 
* Das Ausführen der Desktop-App kann zu Leistungsproblemen auf PCs ohne Ultra-Windows Mixed Reality führen. es wird nicht empfohlen.  
* Die Desktop-App kann automatisch gestartet werden, da ein unsichtbares Fenster auf Desktop den Fokus besitzt. 
* Die Eingabeaufforderung für die Desktopbenutzerkontosteuerung macht das Headset schwarz, bis die Eingabeaufforderung abgeschlossen ist.

### <a name="windows-mixed-reality-setup"></a>Windows Mixed Reality-Setup
* Wenn Sie Windows mit einem verbundenen Headset einrichten, ist Ihr PC-Monitor möglicherweise leer. Trennen Sie Ihr Headset, um die Ausgabe an Ihren PC-Monitor zu aktivieren, um Windows Setup abzuschließen.
* Beim Erstellen einer Grenze kann die Ablaufverfolgung fehlschlagen. Wenn ja, versuchen Sie es erneut, da das System mehr über Ihren Speicherplatz im Laufe der Zeit erfahren wird.
* Wenn Sie Cortana während Windows Mixed Reality Setup aktivieren oder deaktivieren, wird diese Änderung auf Ihre Desktopeinstellungen Cortana angewendet.
* Wenn sie keine Verbundenen haben, fehlen Ihnen möglicherweise Tipps, wenn Sie das Windows Mixed Reality Startseite zum ersten Mal besuchen.
* Bluetooth Kann zu Störungen bei Motion-Controllern führen. Es wird empfohlen, Bluetooth Controller während Windows Mixed Reality Sitzungen nicht zu schließen oder ausgeschaltet zu lassen.

### <a name="games-and-apps-from-windows-store"></a>Spiele und Apps aus Windows Store
* Einige grafisch intensive Spiele, z. B. ForzaUngs 6, können leistungsprobleme auf weniger leistungsfähigen PCs verursachen, wenn sie innerhalb Windows Mixed Reality wiedergegeben werden.

### <a name="audio"></a>Audio
* Wie bereits erwähnt, funktionieren Bluetooth Audioperipheriegeräte nicht gut mit Windows Mixed Reality Sprach- und Raumklangerfahrungen. Sie können sich auch negativ auf die Motion Controller-Erfahrung auswirken. Es wird nicht empfohlen, Bluetooth Audio-Headsets mit Windows Mixed Reality zu verwenden.
* Sie können das Audiogerät, das mit dem Headset verbunden ist (oder ein Teil davon ist), nicht für die Audiowiedergabe verwenden, wenn das Gerät nicht ausgeschaltet wird. Wenn Sie nur über ein Audio-Headset verfügen, sollten Sie das Audio-Headset mit dem Host-PC anstelle des Headsets verbinden. Wenn ja, müssen Sie "Zu Headsetaudio wechseln" in **Einstellungen**  >  **Mixed Reality**  >  **Audio und Sprache** deaktivieren.
* Einige Anwendungen, z. B. viele anwendungen, die über SteamVR gestartet werden, können Audiodaten verlieren oder hängen bleiben, wenn sich das Audiogerät ändert, wenn Sie die Mixed Reality-Portal starten oder beenden. Starten Sie die App neu, nachdem Sie die Mixed Reality-Portal-App geöffnet haben, um dies zu korrigieren.
* Wenn Cortana auf Ihrem Host-PC aktiviert ist, bevor Sie Ihr Windows Mixed Reality Headset verwenden, verlieren Sie möglicherweise die Raumklangsimulation, die auf die Apps angewendet wird, die Sie im Windows Mixed Reality Haus platzieren. Die Umarbeitung besteht darin, "Windows Sonic für Kopfhörer" auf allen Audiogeräten zu aktivieren, die an Ihren PC angefügt sind, sogar auf Ihrem Audiogerät, das mit dem Headset verbunden ist:
   1. Klicken Sie mit der linken Maustaste auf das Lautsprechersymbol auf der Desktoptaskleiste, und wählen Sie aus der Liste der Audiogeräte aus.
   2. Klicken Sie mit der rechten Maustaste auf das Lautsprechersymbol auf der Desktoptaskleiste, und wählen Sie im Menü "Speaker setup" (Lautsprechereinrichtung) die Option "Windows Sonic für Kopfhörer" aus.
   3. Wiederholen Sie diese Schritte für alle Audiogeräte (Endpunkte).
>[!NOTE]
> - Da die mit Ihrem Headset verbundenen Lautsprecher nicht angezeigt werden, es sei denn, Sie tragen es aus, müssen Sie dies über das Fenster der Desktop-App im Windows Mixed Reality Home tun, um diese Einstellung auf das Audiogerät anzuwenden, das mit Ihrem Headset verbunden ist (oder in Ihr Headset integriert ist).
> - Eine weitere Möglichkeit besteht darin, "Let Cortana respond to Hey Cortana" in **Einstellungen**  >  **Cortana** auf Ihrem Desktop zu deaktivieren, bevor Windows Mixed Reality gestartet wird.

* Wenn sich ein anderes Multimedia-USB-Gerät (z. B. ein Webnadel) denselben USB-Hub (entweder extern oder innerhalb Ihres PCs) mit dem Windows Mixed Reality Headset teilt, kann es in seltenen Fällen vorkommen, dass die Audiobuchsen/-stecker des Headsets entweder einen Sound oder überhaupt keine Audiodaten aufweisen. Sie können dies über Ihr Headset an einem USB-Anschluss beheben, der nicht denselben Hub wie das andere Gerät verwendet, oder Ihr anderes USB-Multimediagerät trennen/deaktivieren.
* In seltenen Fällen kann der USB-Hub des Host-PCs nicht genügend Strom für das Windows Mixed Reality Headset bereitstellen, und Sie bemerken möglicherweise einen Burst von Rauschen von den mit dem Headset verbundenen Lautsprechern.

### <a name="speech"></a>Spracheingabe/-ausgabe
* Cortana können ihre Audiohinweise zum Lauschen/Denken und Audioantworten auf Befehle möglicherweise nicht wiedergeben.
* Cortana in china- und japanischen Märkten zeigt text während der Verwendung nicht ordnungsgemäß unter dem Cortana Kreis an.
* Cortana kann beim ersten Aufruf in einer Mixed Reality-Portal Sitzung langsam sein. Sie können dies umgehen, indem Sie sicherstellen, dass "Let Cortana respond to Hey Cortana" unter **Einstellungen**  >  **Cortana**  >  **Talk to Cortana** aktiviert ist.
* Cortana werden möglicherweise langsamer auf PCs ausgeführt, die nicht Windows Mixed Reality Ultra PCs sind.
* Wenn Die Systemtastatur auf eine andere Sprache als die Benutzeroberflächensprache in Windows Mixed Reality festgelegt ist, führt die Verwendung des Diktats von der Tastatur in Windows Mixed Reality zu einem Fehlerdialogfeld, in dem das Diktat nicht funktioniert, weil keine Wi-Fi Verbindung besteht. Um das Problem zu beheben, stellen Sie sicher, dass die Tastatursprache des Systems mit der Windows Mixed Reality Benutzeroberflächensprache übereinstimmt.
* Spanien wird nicht ordnungsgemäß als Markt erkannt, in dem Sprache für Windows Mixed Reality aktiviert ist.

### <a name="holograms"></a>Holograms
* Wenn Sie eine große Anzahl von Hologrammen in Ihrem Windows Mixed Reality Haus platziert haben, werden einige möglicherweise ausgeblendet und wieder angezeigt, wenn Sie sich umsehen. Um dies zu vermeiden, entfernen Sie einige der Hologramme in diesem Bereich der Windows Mixed Reality Startseite.

### <a name="motion-controllers"></a>Bewegungscontroller
* Wenn Sie eine Webseite in Edge auswählen, wird der Inhalt gelegentlich vergrößert, anstatt zu klicken.
* Wenn Sie in Edge einen Link auswählen, funktioniert die Auswahl manchmal nicht.

## <a name="prior-release-notes"></a>Anmerkungen zu früheren Versionen
* [Versionshinweise – August 2016](release-notes-august-2016.md)
* [Versionshinweise – Mai 2016](release-notes-may-2016.md)
* [Versionshinweise – März 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Siehe auch
* [Unterstützung für immersive Headsets (externer Link)](./troubleshooting-windows-mixed-reality.md)
* [HoloLens – bekannte Probleme](/windows/mixed-reality/hololens-known-issues)
* [Installieren der Tools](/windows/mixed-reality/develop/install-the-tools)
* [Geben Sie uns Feedback](/windows/mixed-reality/give-us-feedback)