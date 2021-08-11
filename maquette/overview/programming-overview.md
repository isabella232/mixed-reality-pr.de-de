---
title: Programmierung, Übersicht
description: Erfahren Sie, wie Sie mit Skripts auf Maquette-Objekte und -Schnittstellen zugreifen.
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, Maquette, Prototyperstellung, Mixed Reality, Virtual Reality, VR, MR, Feedback, Feedback-Hub, Fehler
ms.openlocfilehash: 969a4aedb60d947782acb41742b33f275e7c841c1989144b586b0329db3c3b57
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197874"
---
# <a name="programming-overview"></a>Programmierung, Übersicht

<!-- TODO(Harrison): Need consolidated logo with text -->

![Logo](../images/MaquetteIcon.png) Übersicht über die Programmierung

Microsoft Maquette verwendet JavaScript (ECMAScript 5.1 mit Erweiterungen) basierend auf dem [Jint-Interpreter.](https://github.com/sebastienros/jint) Die Erweiterung `.mqjs` wird verwendet, um Maquette-JavaScript-Dateien von normalen JavaScript-Dateien zu unterscheiden.

<!-- TODO(Stefan): Need more context and high-level explanation of Maquette objects, their accessible interfaces, and functionality. 
                   - What can they do and what problems can they solve?
                   - Is there a specific link to the Maquette object API that can be included here?  
-->
Auf Maquette-Objekte und -Schnittstellen kann über das -Objekt zugegriffen `Maquette` werden. Die Dokumentation zu Maquette-Objekten und -Schnittstellen finden Sie in der API-Referenz von Maquette.

<!-- TODO(Stefan): Link to roadmap information, which hasn't been documented yet. -->
MaquetteScript ist eine neue Ergänzung und im Fluss, daher sollten Änderungen erwartet werden. Ausführlichere Dokumentation und Updates sind in Kürze verfügbar.

<!-- TODO(Stefan): Is Spotlights a component or added functionality of Maquette? -->
## <a name="spotlights-on-scripting"></a>Spotlights on Scripting

* TBD: Skripts mit Fokus als Beispiele/Tutorials
  * 2x Images/Caption – Link zur Spotlight-Seite

<!-- TODO(Stefan): Each of these bullets need to be fleshed out. -->
## <a name="getting-started-with-maquettescript"></a>Erste Schritte mit MaquetteScript

* Mqjs im Vergleich zu JS
* Programmiermodell
  * Bearbeitung im Vergleich zu "Wird ausgeführt"
* Link zum Programmierworkflow
* Link zu Freigabeergebnissen

## <a name="programming-workflow"></a>Programmierworkflow

<!-- TODO(Stefan): Which of these bullets are no longer TBD? We only want to include documentation on existing content. -->
TBD
* REPL
* Skripterstellungsvorgang
* Debuggervorgang
* Debugschleife
* Kopieren/Einfügen von Code?

## <a name="running-mqjs-scripts"></a>Ausführen von MQJS-Skripts

<!-- TODO(Stefan): Need screenshot -->
Um eine MaquetteScript-MQJS-Datei auszuführen, wechseln Sie zu den Begleitfenstern von Maquette, und öffnen Sie die Skriptregisterkarte, um Skripts zu suchen.

> [!NOTE] 
> Einige Optionen funktionieren noch nicht, da die Skripts noch nicht im Versand sind.

## <a name="vscode-editor-workflow"></a>Workflow des VSCode-Editors

Um das Skript in Maquette aus VSCode auswerten zu können, muss der Benutzer zwei Befehle kennen:

   `CTRL-5` wertet den ausgewählten Text oder die gesamte Zeile aus, in der sich der Cursor befindet. 

   `CTRL-SHIFT-5` wertet die gesamte Datei aus.

<!-- TODO(Stefan): This could use a nice simple infographic of the REPL loop. -->
Text wird an Maquette gesendet, in der JavaScript-Umgebung ausgewertet, und das Ergebnis wird zurück an die Ausgabekonsole von VSCode gesendet. Dies kann als REPL (read-eval-print-loop) verwendet werden.

## <a name="example-first-step"></a>Beispiel für den ersten Schritt

<!-- TODO(Stefan): What kind of file, a C# or .mqjs file? -->
Kopieren Sie den folgenden Code in eine Datei in VSCode:

```csharp
var myCube = Maquette.CreateCube();
myCube.position = Maquette.User.GetPositionInFront(0.6);
myCube.color = Color(1.0, 0.5, 0.0);
```

<!-- TODO(Stefan): Need screenshot. -->
Wählen Sie den Code oder nur Abschnitte aus, und klicken Sie auf `CTRL-5` , um die Ausführung auszuführen. Dadurch sollte ein Cube erstellt, vor Ihnen platzieren und seine Farbe ändern.

Es gibt weitere Beispiele, die Über die Erweiterung zu finden sind.

## <a name="sharing-results"></a>Freigeben von Ergebnissen

<!-- TODO(Stefan): Need to fill in content/context for these bullets. If there's a lot of content, we might consider breaking this out into it's own doc. -->
Freigeben zwischen Benutzern/Teams
* Zip-Projekt im Dokumentverzeichnis
* Kopieren eines Projekts in eine Dateifreigabe
* Hinzufügen des Dateispeicherorts von Teamfreigabeübermittlungen an das Maquette-Team

<!-- TODO(Stefan): Need to break these out into their own sections and fill in the missing content/context. 
                   - Which of these is accessible now and not TBD?
-->
TBD
* Includes, Verweis auf Code an anderer Stelle mit relativen/absoluten Pfaden, Module
* Bibliotheken?
* Laufzeitunterstützung
* Nicht aufgelöste externe Einträge: Verhalten bei fehlenden/abstürzenden Einträgen
* Können Skripts, die bestimmten Objekten zugeordnet sind, hinzugefügt/bearbeitet/beobachtet werden?
  * Können wir dieses Skript an eine andere Stelle kopieren bzw. einfügen?
  * Was ist mit Objekteigenschaften?
  * Benennen von Objekten in meiner Szene? (Umbenennen des Skripts damit)
  * THIS- oder SELF-Schlüsselwort für Skripts, die einem Objekt zugeordnet sind
  * Wenn ich mit der rechten Maustaste auf ein Objekt klicke, kann ich code associated with it (and all it es hierarchy)
  * Kann ich in der Benutzeroberfläche auswählen und im Code in VSCode angezeigt werden?
  * Code, der einem Objekt zugeordnet ist, "zusammen" in der Skriptquellendatei?
  * Fenster "Eigenschaften anzeigen" eines Objekts, wenn ich darauf klicke? In VR und auf der Hauptregisterkarte?
* Sicherheitsprobleme
* Testen– kann TBD sein, aber wir könnten video- oder frame grab by script vorschlagen.
* Wenn wir über einen Mechanismus zur Fehlerberichterstattung verfügen, können wir diesen über ein Skript für andere (?) zugänglich machen... Später
* Bereitstellung: "Freigeben" des Ergebnisses als EXE-Paket
* Ausführen/Steuern einer Demo oder Überprüfung/Überwachung
* Playermodus
* Möglicherweise gibt es ein Segment, in dem erläutert wird, wie "Komponenten" für die Freigabe gemacht werden? (möglicherweise tbd)
  * Gibt es #include? Dies behandelt reine JS- Ich vermute, aber es kann Namespacekonflikte geben.
  * Gibt es etwas, was wir für ein Maquette tun können, um einige andere Maquette mit benannten Objekten zu integrieren, um JS-Code zu finden?
