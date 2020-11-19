---
title: Übersicht über die Programmierung
description: Erfahren Sie, wie Sie mit Skripts auf Makett-Objekte und-Schnittstellen zugreifen
author: hferrone
ms.author: v-hferrone
ms.date: 10/26/2020
ms.topic: article
keywords: Windows Mixed Reality, Maquette, Prototyperstellung, gemischte Realität, Virtual Reality, VR, Mr, Feedback, Feedback-Hub, Fehler
ms.openlocfilehash: 6761ed0fab70b0d497ad1e1398cbd6c1af6ab38b
ms.sourcegitcommit: fae413a2b0420e787671af90f14ee39cde51640f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94935507"
---
# <a name="programming-overview"></a>Übersicht über die Programmierung

<!-- TODO(Harrison): Need consolidated logo with text -->

![Logo](../images/MaquetteIcon.png) Übersicht über die Programmierung

Microsoft Maquette verwendet JavaScript (ECMAScript 5,1 mit Erweiterungen), das auf dem [Jint](https://github.com/sebastienros/jint) -Interpreter basiert. Die Erweiterung `.mqjs` wird verwendet, um Makett-JavaScript-Dateien von normalem JavaScript zu unterscheiden.

<!-- TODO(Stefan): Need more context and high-level explanation of Maquette objects, their accessible interfaces, and functionality. 
                   - What can they do and what problems can they solve?
                   - Is there a specific link to the Maquette object API that can be included here?  
-->
Auf Maquette-Objekte und-Schnittstellen kann über das-Objekt zugegriffen werden `Maquette` . Dokumentation zu Maquette-Objekten und-Schnittstellen finden Sie in der Referenz zur API-Referenz von Maquette.

<!-- TODO(Stefan): Link to roadmap information, which hasn't been documented yet. -->
Maquettescript ist eine neue Addition und in Flux, damit Änderungen erwartet werden. Ausführlichere Dokumentation und Updates sind in Kürze verfügbar.

<!-- TODO(Stefan): Is Spotlights a component or added functionality of Maquette? -->
## <a name="spotlights-on-scripting"></a>Spotlights bei der Skripterstellung

* TBD-Skripts für die Skripterstellung als Beispiele/Tutorials
  * 2X-Bilder/Beschriftung – Link zur Spotlight-Seite

<!-- TODO(Stefan): Each of these bullets need to be fleshed out. -->
## <a name="getting-started-with-maquettescript"></a>Einstieg in maquettescript

* Mqjs im Vergleich zu JS
* Programmiermodell
  * Bearbeiten und ausführen
* Link zum Programmier Workflow
* Link zu Freigabe Ergebnissen

## <a name="programming-workflow"></a>Programmier Workflow

<!-- TODO(Stefan): Which of these bullets are no longer TBD? We only want to include documentation on existing content. -->
TBD
* REPL
* Skript Vorgang
* Debugger-Vorgang
* Debugschleife
* Code kopieren/einfügen?

## <a name="running-mqjs-scripts"></a>Ausführen von mqjs-Skripts

<!-- TODO(Stefan): Need screenshot -->
Wechseln Sie zum Ausführen einer Datei maquettescript. mqjs zum Begleit Fenster von Maquette, und öffnen Sie die Registerkarte Skripterstellung, um nach Skripts zu suchen.

> [!NOTE] 
> Einige Optionen sind noch nicht funktionsfähig, da die Skripts nicht ausgeliefert wurden.

## <a name="vscode-editor-workflow"></a>Vscode-Editor-Workflow

Um Skripts in Maquette aus vscode heraus auszuwerten, muss der Benutzer zwei Befehle kennen:

   `CTRL-5` wertet den markierten Text oder die gesamte Zeile aus, in der sich der Cursor befindet. 

   `CTRL-SHIFT-5` wertet die gesamte Datei aus.

<!-- TODO(Stefan): This could use a nice simple infographic of the REPL loop. -->
Der Text wird an die Makette gesendet, in der JavaScript-Umgebung ausgewertet, und das Ergebnis wird zurück an die Ausgabe Konsole von vscode gesendet. Diese kann als REPL (Read-eval-Print-Loop) verwendet werden.

## <a name="example-first-step"></a>Beispiel für den ersten Schritt

<!-- TODO(Stefan): What kind of file, a C# or .mqjs file? -->
Kopieren Sie den folgenden Code in eine Datei in vscode:

```csharp
var myCube = Maquette.CreateCube();
myCube.position = Maquette.User.GetPositionInFront(0.6);
myCube.color = Color(1.0, 0.5, 0.0);
```

<!-- TODO(Stefan): Need screenshot. -->
Wählen Sie den Code oder nur die Abschnitte aus, und klicken Sie `CTRL-5` auf ausführen. Dies sollte einen Cube erstellen, ihn vor Ihnen platzieren und seine Farbe ändern.

Weitere Beispiele finden Sie in der Erweiterung.

## <a name="sharing-results"></a>Freigabe Ergebnisse

<!-- TODO(Stefan): Need to fill in content/context for these bullets. If there's a lot of content, we might consider breaking this out into it's own doc. -->
Freigeben zwischen Benutzern und Teams
* ZIP-Projekt im Verzeichnis "Dokumente"
* Projekt in Dateifreigabe kopieren
* Hinzufügen des Dateispeicher Orts von Team Freigabe Einreichungen zum Maquette-Team

<!-- TODO(Stefan): Need to break these out into their own sections and fill in the missing content/context. 
                   - Which of these is accessible now and not TBD?
-->
TBD
* Enthält einen Verweis auf Code an anderer Stelle mit relativen/absoluten Pfaden, Modulen
* Bibliotheken?
* Laufzeitunterstützung
* Nicht aufgelöste externale: Verhalten bei fehlenden/abstürzenden Einträgen
* Können wir Skripts hinzufügen/bearbeiten/beobachten, die bestimmten Objekten zugeordnet sind?
  * Können wir dieses Skript kopieren und an anderer Stelle einfügen?
  * Was ist mit Objekteigenschaften?
  * Benennen von Objekten in meiner Szene? (Skript mit dem Skript umbenennen)
  * Dieses oder selbst Schlüsselwort für ein einem Objekt zugeordnetes Skript
  * Wenn ich mit der rechten Maustaste auf ein Objekt klicke, kann ich Code sehen, der ihm zugeordnet ist (und hier Hierarchie).
  * Kann ich in der Benutzeroberfläche auswählen und im Code in vscode angezeigt werden?
  * Zusammenhalten von Code, der einem Objekt zugeordnet ist, in der Skript Quelldatei
  * Wenn ich auf das Eigenschaften Fenster eines Objekts klicke? In VR und in der Haupt Registerkarte?
* Sicherheitsprobleme
* Test – kann "TBD" lauten, aber wir könnten Video-oder Frame-Einfügeverfahren mit Skript
* Wenn ein Fehlerbericht Erstellungs Mechanismus vorhanden ist, kann dies über das Skript für andere Benutzer (?) verfügbar gemacht werden... höher
* Bereitstellung – Gewusst wie: "freigeben" des Ergebnisses, Verpacken als exe
* Ausführen/Steuern einer Demo oder spectierung/Überwachung
* Player Modus
* Wir verfügen möglicherweise über ein Segment zum Erstellen von "Komponenten" für die Freigabe? (kann "TBD" lauten)
  * Gibt es #include? Dies kümmert sich um das reine js, es kann jedoch zu Namespace Konflikten kommen.
  * Gibt es etwas, was wir für eine Maquette tun könnten, um eine andere Makett mit benannten Objekten zu integrieren, um den JS-Code abzugleichen?
