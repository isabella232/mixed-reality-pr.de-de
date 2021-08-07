---
title: Testen Ihrer App auf HoloLens
description: Erfahren Sie mehr über allgemeine Anleitungen und Vorschläge zum Testen und Optimieren der Leistung Ihrer HoloLens Mixed Reality-Anwendungen.
author: jonmlyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, Testen
ms.openlocfilehash: 2f423560191fea8b516db80d533898b5a1f15973442e7bb6cd8878d486e0ffba
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212096"
---
# <a name="testing-your-app-on-hololens"></a>Testen Ihrer App auf HoloLens

Das Testen HoloLens Anwendungen ähnelt dem Testen Windows Anwendungen. Sie müssen weiterhin Funktionalität, Interoperabilität, Leistung, Sicherheit, Zuverlässigkeit usw. berücksichtigen. Einige Bereiche, die nicht in PC- oder Smartphone-Apps angezeigt werden, erfordern jedoch eine besondere Behandlung. Holographic-Apps müssen in einer Vielzahl von Umgebungen reibungslos ausgeführt werden. Außerdem müssen sie jederzeit Leistung und Benutzerfreundlichkeit aufrechterhalten. Dieser Leitfaden hilft Ihnen beim Testen dieser Bereiche.

## <a name="performance"></a>Leistung

Holographic-Apps müssen in einer Vielzahl von Umgebungen reibungslos ausgeführt werden. Außerdem müssen sie jederzeit Leistung und Benutzerfreundlichkeit aufrechterhalten. Die Leistung ist für die Benutzererfahrung mit einer Holographic-App so wichtig, dass wir ein ganzes Thema haben. Stellen Sie sicher, dass Sie die Informationen zur Leistung für Mixed Reality lesen und [befolgen.](understanding-performance-for-mixed-reality.md)

## <a name="testing-3d-in-3d"></a>Testen von 3D in 3D

1. **Testen Sie Ihre App in so vielen verschiedenen Bereichen wie möglich.** Probieren Sie es in großen Räumen, kleinen Räumen, Filialen, Filialen, Filialen usw. aus. Berücksichtigen Sie auch Räume mit nicht standardmäßigen Merkmalen, z. B. nicht vertikale Wände, gekrümmte Wände, nicht horizontale Decken. Funktioniert es gut beim Übergang zwischen Räumen, Etagen, durch Hallen oder Durchgang?
2. **Testen Sie Ihre App unter unterschiedlichen Beleuchtungsbedingungen.** Reagiert er ordnungsgemäß auf unterschiedliche Umgebungsbedingungen wie Beleuchtung, schwarze Oberflächen und transparente oder reflektierende Oberflächen wie Spiegel und Brillen.
3. **Testen Sie Ihre App unter unterschiedlichen Bewegungsbedingungen.** Setzen Sie auf das Gerät, und probieren Sie Ihre Szenarien in verschiedenen Bewegungszuständen aus. Reagiert sie ordnungsgemäß auf unterschiedliche Bewegungen oder einen stabilen Zustand?
4. **Testen Sie, wie Ihre App aus verschiedenen Winkeln funktioniert.** Wenn Sie über ein weltweit gesperrtes Hologramm verfügen, was geschieht, wenn Ihr Benutzer hinter ihm läuft? Was geschieht, wenn zwischen dem Benutzer und dem Hologramm etwas passiert? Was geschieht, wenn der Benutzer das Hologramm von oben oder unten betrachtet?
5. **Verwenden Sie räumliche und Audiohinweise.** Stellen Sie sicher, dass Ihre App räumliche und Audiohinweise verwendet, um zu verhindern, dass der Benutzer verloren geht.
6. **Testen Sie Ihre App auf unterschiedlichen Umgebungsrauschen.** Wenn Sie Sprachbefehle implementiert haben, versuchen Sie, sie mit unterschiedlichen Umgebungsrauschen aufzubringen.
7. **Testen Sie Ihre App mit und im Stehen.** Stellen Sie sicher, dass Sie sowohl an der Position als auch an der Position im Stehen testen.
8. **Testen Sie Ihre App aus unterschiedlichen Entfernungen.** Können Benutzeroberflächenelemente von weit entfernt gelesen und mit ihnen interagiert werden? Reagiert Ihre App darauf, dass Benutzer ihren Hologrammen zu nahe kommen?
9. **Testen Sie Ihre App mit allgemeinen Interaktionen auf der App-Leiste.** Alle App-Kacheln und universellen 2D-Apps verfügen über eine [App-Leiste,](../../discover/navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps) mit der Sie die Position der Apps in der Mixed World steuern können. Stellen Sie sicher, dass durch Klicken auf Entfernen Der App-Prozess ordnungsgemäß beendet wird und dass die Schaltfläche "Zurück" im Kontext Ihrer universellen 2D-App unterstützt wird. Versuchen Sie, Ihre App sowohl während ihrer Aktiven als auch während einer angehaltenen App-Kachel im [Modus Anpassen](../../discover/navigating-the-windows-mixed-reality-home.md#moving-and-adjusting-apps) zu skalieren und zu verschieben.

### <a name="environmental-test-matrix"></a>Umgebungstestmatrix

![Umgebungstestmatrix für HoloLens App-Entwicklung](images/environment-matrix-600px.png)

## <a name="comfort"></a>Komfort

1. **Clipebenen.** Achten Sie darauf, wo [Hologramme gerendert werden.](hologram-stability.md#hologram-render-distances)
2. **Vermeiden Sie virtuelle Verschiebungen, die mit der tatsächlichen Kopfbewegung inkonsistent sind.** Vermeiden Sie es, die Kamera auf eine Weise zu bewegen, die nicht repräsentativ für die tatsächliche Bewegung des Benutzers ist. Wenn Ihre App das Verschieben des Benutzers durch eine Szene erfordert, machen Sie die Bewegung vorhersagbar, minimieren Sie die Beschleunigung, und lassen Sie den Benutzer die Bewegung steuern.
3. **Befolgen Sie die Hologrammqualitätsrichtlinien.** Performante Apps, die den Leitfaden zur [Hologrammqualität](hologram-stability.md) implementieren, führen mit geringerer Wahrscheinlichkeit zu Benutzerfreundlichkeit.
4. **Verteilen Sie Hologramme horizontal und nicht vertikal.** Wenn der Benutzer gezwungen wird, längere Zeit nach oben oder unten zu suchen, kann dies zu Ermüdung in der Ähre führen.

## <a name="input"></a>Eingabe

### <a name="interaction-models"></a>Interaktionsmodelle

Stellen Sie sicher, dass die Hologramminteraktionen mit dem ausgewählten [Interaktionsmodell](../../design/interaction-fundamentals.md)funktionieren.
Es ist auch eine gute Idee, mit unterschiedlichen Zubehör wie Maus und Tastatur zu überprüfen, ob sie zur Unterstützung der Barrierefreiheit benötigt werden.

**Überprüfen Sie mit Maus und Fingereingabe, ob Ihre App ein anderes Verhalten auf hat.** Identifiziert Inkonsistenzen und Hilfe bei Entwurfsentscheidungen, um die Benutzerfreundlichkeit zu verbessern. Beispielsweise das Auslösen einer Aktion basierend auf dem Mauszeiger.


### <a name="custom-voice-commands"></a>Benutzerdefinierte Sprachbefehle

[Die Spracheingabe](../../design/voice-input.md) ist eine natürliche Form der Interaktion. Je nachdem, wie Sie Befehle auswählen und wie Sie sie verfügbar machen, kann die Benutzeroberfläche verwirrend oder verwirrend sein. In der Regel sollten Sie keine Sprachbefehle des Systems wie "Select" oder "Hey Cortana" als benutzerdefinierte Befehle verwenden. Hier sind einige Punkte zu beachten:
1. **Vermeiden Sie die Verwendung von Befehlen, die ähnlich klingen.** Kann möglicherweise den falschen Befehl auslösen.
2. **Wählen Sie nach Möglichkeit phonetisch umfangreiche Wörter aus.** Minimiert und/oder vermeidet falsche Aktivierungen.

### <a name="peripherals"></a>Peripheriegeräte

Benutzer können über [Peripheriegeräte](../../discover/hardware-accessories.md)mit Ihrer App interagieren. Apps müssen nichts Besonderes tun, um diese Funktion nutzen zu können. Es gibt jedoch einige Dinge, die überprüft werden sollten.
1. **Überprüfen sie benutzerdefinierte Interaktionen.** Beispielsweise benutzerdefinierte Tastenkombinationen für Ihre App.
2. **Überprüfen des Wechsels von Eingabetypen.** Es wurde versucht, mehrere Eingabemethoden zum Ausführen einer Aufgabe zu verwenden, z. B. Stimme, Geste, Maus und Tastatur im selben Szenario.

## <a name="system-integration"></a>Systemintegration

### <a name="battery"></a>Akku

Testen Sie Ihre Anwendung ohne angeschlossene Stromquelle, um zu verstehen, wie schnell der Akku entladen wird. Sie können den Akkuzustand leicht nachvollziehen, indem Sie sich die Power LED-Messwerte ansehen. 

![LED-Zustände, die die Akkuleistung angeben](images/batterypowerledindication-500px.png)<br>

*LED-Zustände, die die Akkuleistung angeben*

### <a name="power-state-transitions"></a>Energiezustandsübergänge

Überprüfen Sie, ob wichtige Szenarien beim Übergang zwischen Energiezuständen erwartungsgemäß funktionieren. Bleibt die Anwendung beispielsweise an ihrer ursprünglichen Position? Wird der Zustand ordnungsgemäß beibehalten? Funktioniert es weiterhin wie erwartet?
1. **Stand-by/Resume.** Um in den Standbymodus zu gelangen, können Sie den Netzschalter sofort drücken und loslassen. Das Gerät wechselt auch nach 3 Minuten Inaktivität automatisch in den Standbymodus. Um den Betrieb aus dem Standbymodus fortzusetzen, können Sie den Netzschalter sofort drücken und loslassen. Das Gerät wird auch fortgesetzt, wenn Sie es mit einer Stromquelle verbinden oder trennen.
2. **Herunterfahren/Neustart.** Drücken sie zum Herunterfahren, und halten Sie den Netzschalter 6 Sekunden lang kontinuierlich gedrückt. Drücken Sie zum Neustarten den Netzschalter.

### <a name="multi-app-scenarios"></a>Szenarien mit mehreren Apps

Überprüfen Sie die Kernfunktionen von Apps beim Wechseln zwischen Apps, insbesondere wenn Sie eine Hintergrundaufgabe implementiert haben. Kopieren/Einfügen und Cortana Integration sind ggf. ebenfalls zu überprüfen.

## <a name="telemetry"></a>Telemetrie

Verwenden Sie Telemetrie und Analysen, um Sie zu leiten. Die Integration von Analysen in Ihre App hilft Ihnen, Einblicke in Ihre App von Ihren Betatestern und Endbenutzern zu erhalten. Diese Daten können verwendet werden, um Ihre App zu optimieren, bevor sie an die Store und für zukünftige Updates eingereicht werden. Es gibt viele Analyseoptionen. Wenn Sie nicht sicher sind, wo Sie beginnen sollten, lesen Sie [App Insights](https://www.visualstudio.com/products/application-insights-vs.aspx).

Zu berücksichtigende Fragen:
1. Wie verwenden Benutzer den Bereich?
2. Wie platziert die App Objekte auf der Welt– können Sie Probleme erkennen?
3. Wie viel Zeit verbringen sie in verschiedenen Phasen der Anwendung?
4. Wie viel Zeit verbringen sie in der App?
5. Welche Nutzungspfade werden von Benutzern am häufigsten verwendet?
6. Treten bei Benutzern unerwartete Zustände oder Fehler auf?

## <a name="emulator-and-simulated-input"></a>Emulator und simulierte Eingabe

Der [HoloLens-Emulator](using-the-hololens-emulator.md) ist eine hervorragende Möglichkeit, Ihre Holographic-App effizient mit verschiedenen Arten simulierter Benutzermerkmale und -leerzeichen zu testen. Im Folgenden finden Sie einige Vorschläge für die effektive Verwendung des Emulators zum Testen Ihrer App:
1. **Verwenden Sie die virtuellen Räume des Emulators, um Ihre Tests zu erweitern.** Der Emulator enthält eine Reihe von virtuellen Räumen, mit denen Sie Ihre App in noch mehr Umgebungen testen können.
2. **Verwenden Sie den Emulator, um Ihre App aus allen Winkeln zu betrachten.** Die PageUp-/PageDn-Schlüssel sorgen dafür, dass Der simulierte Benutzer größer oder kürzer wird.
3. **Testen Sie Ihre App mit einem echten HoloLens.** Das HoloLens Emulator ist ein hervorragendes Tool, mit dem Sie eine App schnell iterieren und neue Fehler abfangen können. Stellen Sie jedoch sicher, dass Sie auch auf einem physischen HoloLens testen, bevor Sie es an die Windows Store. Dies ist wichtig, um sicherzustellen, dass die Leistung und Erfahrung auf echter Hardware gut ist.

## <a name="automated-testing-with-perception-simulation"></a>Automatisierte Tests mit Perception Simulation

Einige App-Entwickler möchten das Testen ihrer Apps möglicherweise automatisieren. Neben einfachen Komponententests können [](perception-simulation.md) Sie den Wahrnehmungssimulationsstapel in HoloLens, um menschliche und weltliche Eingaben für Ihre App zu automatisieren. Die Wahrnehmungssimulations-API kann simulierte Eingaben entweder an den HoloLens Emulator oder an einen physischen HoloLens.

## <a name="windows-app-certification-kit"></a>Zertifizierungskit für Windows-Apps

Um Ihrer App die beste Chance zu geben, auf dem Windows Store veröffentlicht zu [werden,](../../distribute/submitting-an-app-to-the-microsoft-store.md)überprüfen und testen Sie sie lokal, bevor Sie sie zur Zertifizierung einreichen. Wenn Ihre App auf die Windows. Die Holographic-Gerätefamilie, Windows [App Certification Kit](/windows/uwp/debug-test-perf/windows-app-certification-kit) nur lokale statische Analysetests auf Ihrem PC ausführen. Auf Ihrem Computer werden keine Tests HoloLens.

## <a name="see-also"></a>Siehe auch

* [Übermitteln einer App an die Windows Store](../../distribute/submitting-an-app-to-the-microsoft-store.md)