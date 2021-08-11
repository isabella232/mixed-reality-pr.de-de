---
title: Advanced HoloLens Emulator and Mixed Reality Simulator
description: Ausführliche Anweisungen für die Verwendung von Tastatur, Maus und Xbox-Controller zum Simulieren von Eingaben für den HoloLens Emulator und Windows Mixed Reality Simulator.
author: pbarnettms
ms.author: pbarnett
ms.date: 06/8/2020
ms.topic: article
keywords: HoloLens, Emulator, Simulation, Windows Mixed Reality, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: a4e66b2738d5f89949b14fd6f901e2b30dc38cd9e02072f640345d374b9eb9fe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217126"
---
# <a name="advanced-hololens-emulator-and-mixed-reality-simulator-input"></a>Erweiterte Eingabe für HoloLens-Emulator und Mixed Reality-Simulator

Die meisten Emulatorbenutzer müssen nur die grundlegenden Eingabesteuerelemente für die [HoloLens Emulator](using-the-hololens-emulator.md#basic-emulator-input) oder den [Windows Mixed Reality-Simulator](using-the-windows-mixed-reality-simulator.md#basic-simulator-input)verwenden. Die folgenden Details gelten für fortgeschrittene Benutzer, die komplexere Eingabetypen simulieren müssen.

## <a name="concepts"></a>Konzepte

Um mit dem Steuern der virtuellen Eingabe für den HoloLens Emulator und Windows Mixed Reality Simulator zu beginnen, sollten Sie zunächst einige Konzepte verstehen.

Bewegung bezieht sich auf das Steuern und Ändern der Position und Ausrichtung von etwas in der Szene. Für ein zielorientiertes steuerbares Objekt wird die Bewegung sowohl mit Drehung als auch mit Übersetzung (Bewegung) auf drei Achsen gesteuert.
* **Yaw:** Nach links oder rechts drehen.
* **Tonhöhe:** Nach oben oder unten.
* **Roll:** Roll-to-Side.
* **X:** Nach links oder rechts verschieben.
* **Y:** Nach oben oder unten verschieben.
* **Z:** Vorwärts- oder Rückwärtsbewegung.

Gesten- und Bewegungscontrollereingaben werden physischen Geräten eng zugeordnet:
* **Aktion:** Simuliert die Aktion durch Drücken des Zeigefingers auf den Ziehfinger oder Ziehen der Aktionsschaltfläche auf einem Controller. Beispielsweise kann die Aktionseingabe verwendet werden, um die Tippbewegung in die Luft zu simulieren, um durch den Inhalt zu scrollen und zu halten.
* **[](../../design/system-gesture.md#bloom)Bloom/Systemgeste oder Home:** Die HoloLens Geste "bloom/system" oder die Home-Schaltfläche eines Controllers wird verwendet, um zur Shell zurückzukehren und Systemaktionen auszulöschen.

Hände verfügen über eine umfangreiche Darstellung in HoloLens 2.  Zusätzlich zur Nachverfolgung bzw. nicht nachverfolgt und für Fahrgesten verwendbar, verfügen Die Hände jetzt über ein artikuliertes Gerüstmodell, das an sie angepasst und für den Entwickler verfügbar gemacht wird.  Das Gerüstmodell verfügt über 26 nachverfolgte Punkte auf jeder Hand.  
* **Joint**: Eine von 20 nachverfolgten Positionen für eine bestimmte nachverfolgte Hand mit einem zugeordneten Punkt im 3D-Raum.
* **Pose:** Eine vollständige Sammlung aller Joints in einer nachverfolgten Hand, 26 Joints in all. 

Wir machen derzeit keine direkte Kontrolle über einzelne gemeinsame Positionen über den Emulator verfügbar, aber Sie können sie über die Simulations-API festlegen. Wir verfügen über eine Reihe nützlicher repräsentativer Positionen, mit denen Sie mit dem Emulator zwischen diesen wechseln können.

Sie können auch den Zustand der simulierten Sensoreingabe steuern:
* **Zurücksetzen:** Gibt alle simulierten Sensoren auf ihre Standardwerte zurück.  Ab dem HoloLens 2 Emulator kann eine Zurücksetzung auf eine oder beide Hände erweitert werden. Binden Sie die gewünschten Hand(en) mithilfe der Modifizierertaste(n) oder Schaltfläche(n) (Links und/oder Rechts alt oder mit dem linken und/oder rechten Bumper auf dem Gamepad) ein.
* **Nachverfolgung:** Durchläufe durch die Positionsnachverfolgungsmodi, einschließlich:
  * **Standard:** Das Betriebssystem wählt den besten Nachverfolgungsmodus basierend auf den Anforderungen des Systems aus.
   * **Orientation**: Erzwingt die ausschließliche Ausrichtungsnachverfolgung, unabhängig von den Systemanforderungen.
   * **Positional:** Erzwingt die Positionsnachverfolgung, unabhängig von den Systemanforderungen.

## <a name="types-of-input"></a>Eingabetypen

In der folgenden Tabelle wird gezeigt, wie jeder Eingabetyp der Tastatur, der Maus und dem Xbox-Controller zugeordnet wird. Jeder Typ weist je nach Eingabesteuerungsmodus eine andere Zuordnung auf. Weitere Informationen zu Eingabesteuerungsmodi finden Sie weiter unten in diesem Dokument.

| Eingabe |  Tastatur |  Maus |  Xbox-Controller | 
|----------|----------|----------|----------|
|  Gier |  Nach-links-/nach-rechts-Pfeile |  Ziehen Sie nach links/rechts. |  Rechter Fingerabdruck nach links/rechts | 
|  Neigung |  NACH-OBEN-/NACH-UNTEN-TASTE |  Nach oben/unten ziehen |  Rechter Fingerabdruck nach oben/unten | 
|  rollen |  Q/E |  |  DPad links/rechts | 
|  X |  A/D |  |  Linker Fingerabdruck nach links/rechts | 
|  J |  Vorherige Seite/Seite nach unten |  |  DPad nach oben/unten | 
|  Z |  W/S |  |  Linker Fingerabdruck nach oben/unten | 
|  Action |  Eingabe oder Leerzeichen |  Schaltfläche "Rechts" |  Eine Schaltfläche oder ein Trigger | 
|  Bloom/System |  F2- oder Windows-Taste |  |  B-Taste | 
|  Controller-Klammertaste/Handumfassen |  G  |  |  | 
|  Menüschaltfläche "Controller" |  M  |  |  | 
|  Touchpad-Toucheingabe für Controller |  U  |  |  | 
|  Controllertouchpad drücken |  P  |  |  | 
|  Controllerfingerabdruck drücken |  K  |  |  | 
|  Nachverfolgungsstatus des linken Controllers |  F9 |  |  | 
|  Nachverfolgungsstatus des rechten Controllers |  F10 |  |  | 
|  Hand "Close" Pose | 7 |  |  |
|  Hand "Open" Pose (Standard) | 8 |  |  |
|  Hand "Point" Pose | 9 |  |  |
|  Hand "Pinch" Pose | 0 |  |  |
|  Reset |  Escapetaste |  |  Starttaste | 
|  Nachverfolgung |  T oder F3 |  |  X-Taste | 


Hinweis: Die Controllerschaltflächen können mithilfe der Hand-Targeting-Modifizierer auf eine Hand/einen Controller oder auf die andere ausgerichtet werden.

## <a name="targeting"></a>Zielgruppenadressierung 

Einige der oben genannten Eingabekonzepte stehen für sich allein.  Action, Bloom/System, Reset und Tracking sind vollständige Konzepte, die keine zusätzlichen Modifizierer für die Zielgruppenadressierung benötigen und von diesen nicht betroffen sind.  Die übrigen Konzepte können auf eines von mehreren Zielen angewendet werden. Wir haben Möglichkeiten eingeführt, wie Sie angeben können, auf welches Ziel Ihr Befehl angewendet werden soll.  In allen Fällen ist es möglich, über die Benutzeroberfläche oder über Tastatureingaben anzugeben, welches Objekt als Ziel verwendet werden soll.  In einigen Fällen ist es auch möglich, direkt mit dem Xbox-Controller anzugeben. 

In der folgenden Tabelle werden die Optionen für die Zielgruppenadressierung und die Art der Aktivierung beschrieben.

| Object | Tastaturmodifizierer | Controllermodifizierer | Emulator Benutzeroberflächenmodifizierer |
|----------|----------|----------|----------|
| Text | (Standard) | (Standard) | (Standard) |
| Head | H halten | (Nicht verfügbar) | (Nicht verfügbar) |
| Linke Hand/Controller | Linke ALT-Taste gedrückt halten | Halten Sie die linke Maustaste gedrückt. | Left-Hand-Pin | 
| Rechte Hand/Controller | Halten Sie die rechte ALT-Taste gedrückt. | Halten Sie die rechte Maustaste gedrückt. | Right-Hand-Pin |
| Augen | Halten Sie Y | (Nicht verfügbar) | Augen-Pin |
  
In der folgenden Tabelle wird gezeigt, wie jeder Zielmodifizierer die einzelnen Grundlegenden Eingabekonzepte der Bewegung zueinander zueinander zu ordnet.

| Eingabe | Standard (Text) |  Hand/Controller (Alt halten, Gamepad-Umschaltfläche halten oder UI-Pin umschalten) |  Kopf (H halten)  |  Augen (Y halten oder UI-Pin umschalten) |
|----------|----------|----------|----------|----------|
|  Gier |  Text nach links/rechts drehen |  Hand nach links/rechts verschieben |  Kopf nach links/rechts drehen | Anving mit den Augen sieht links/rechts aus |
|  Neigung |  Kopf nach oben/unten schalten |  Hand nach oben/unten verschieben |  Kopf nach oben/unten schalten | Anvschauung mit den Augen nach oben/unten | 
|  rollen |  Kopf nach links/rechts rollen |  |  Kopf nach links/rechts rollen | (Keine Aktion) |
|  X |  Schiebekörper links/rechts |  Hand/Controller nach links/rechts verschieben |  Kopf nach links/rechts drehen | (Keine Aktion) |
|  J |  Text nach oben/unten verschieben |  Hand/Controller nach oben/unten verschieben |  Kopf nach oben/unten schalten | (Keine Aktion) |
|  Z |  Text nach vorne/rückwärts verschieben |  Hand/Controller vorwärts/rückwärts verschieben |  Kopf nach oben/unten schalten | (Keine Aktion) |
 
 
## <a name="controlling-an-app"></a>Steuern einer App

Die folgenden Steuerelemente werden für die täglichen Verwendung empfohlen:

|  Vorgang |  Tastatur und Maus |  Controller | 
|----------|----------|----------|
|  Text X |  A/D |  Linker Thumbstick links/rechts | 
|  Text Y |  Vorherige Seite/Nach unten |  DPad nach oben/unten | 
|  Text Z |  W/S |  Linker Thumbstick nach oben/unten | 
|  Body Yaw |  Ziehen der Maus nach links/rechts |  Rechter Fingerabdruck links/rechts | 
|  Kopf yaw |  H + Ziehen der Maus nach links/rechts |  H (auf der Tastatur) + rechter Fingerabdruck links/rechts | 
|  Kopfhöhe |  Ziehen der Maus nach oben/unten |  Rechter Fingerabdruck nach oben/unten | 
|  Head Roll |  Q/E |  DPad links/rechts | 
|  Hand/Controller X |  ALT + A /D |  Shoulder + left thumbstick left/right | 
|  Hand/Controller Y |  ALT +Vorherige Seite/Nach unten |  Shoulder + DPad up/down | 
|  Hand/Controller Z |  ALT +W/S |  Shoulder + Left thumbstick up/down | 
|  Hand-/Controller-Yaw |  ALT +Maus nach links/rechts ziehen |  Shoulder + right thumbstick left/right | 
|  Hand/Controller-Tonhöhe |  ALT + Maus nach oben/unten ziehen |  Shoulder + right thumbstick up/down | 
|  Hand/Controllerroll |  ALT +Q/E |  Shoulder + DPad left/right | 
|  Action |  Rechte Maustaste |  Trigger | 
|  Bloom/System/Home |  F2- oder Windows-Taste |  B-Taste | 
|  Reset |  Escape |  Starttaste | 
|  Nachverfolgung |  T |  X-Taste | 
|  Bildlauf |  ALT+ RECHTE MAUSTASTE + Maus nach oben/unten ziehen |  Shoulder + trigger + right thumbstick up/down | 
|  Schnelleres Verschieben/Drehen | UMSCHALTTASTE nach links oder rechts | Drücken Sie den rechten Fingerabdruck, und halten Sie den Stick gedrückt. |
|  Langsames Verschieben/Drehen | LINKE oder RECHTE STRG-TASTE | Halten Sie den linken Daumenstick gedrückt. |

## <a name="using-a-windows-mixed-reality-immersive-headset-and-motion-controllers-with-the-hololens-2-emulator"></a>Verwenden eines immersiven Headsets für Windows Mixed Reality und des Motion-Controllers mit dem Hololens 2-Emulator

Bei Verwendung eines Windows Mixed Reality immersiven Headsets mit dem HoloLens 2 Emulator werden Bewegung und Drehung automatisch Headsetbewegungen und Drehungen zugeordnet.  Position und Ausrichtung des Bewegungscontrollers werden automatisch der Handposition und -ausrichtung im Emulator zugeordnet.  In der folgenden Tabelle sind zusätzliche Aktionen aufgeführt, die bei Verwendung eines Motion-Controllers verfügbar sind.

> [!NOTE]
> Bei Verwendung eines Headsets werden Standardsteuerelemente für Tastatur, Maus und Gamepad automatisch ignoriert.

|  Vorgang |  Aktion |  Hinweise | 
|----------|----------|----------|
|  Text X |  Thumbstick Left/Right |   | 
|  Text Z |  Thumbstick Forward/Back |   | 
|  Text Y |  Tastaturseite nach oben /Nach unten | Stellen Sie sicher, dass Windows Mixed Reality den Fokus besitzt.  Drücken Sie Win+Y, wenn der Fokus auf dem Windows Desktop liegt, um den Fokus auf Windows Mixed Reality zurückzugeben. |
|  Augen sehen nach links/rechts aus |  DPad links/rechts | |
|  Augen nach oben/unten | DPad nach oben/unten | |
|  Tippen | Trigger | |
|  Kneifen/Greifen | Klammertaste | |
|  Systemgeste | Menü-Taste | |
|  Position zurücksetzen | Fingerabdruckklick | |

## <a name="perception-simulation-control-panel-keyboard-shortcuts"></a>Perception Simulation Systemsteuerung Tastenkombinationen

Sie können auf die Perception Simulation-Systemsteuerung zugreifen und PC-Eingabegeräte mit den folgenden Tastenkombinationen aktivieren oder deaktivieren.

| Vorgang | Verknüpfung | Beschreibung/Hinweise |
|-----------|----------|-------------|
| Umschalten von "Verwenden der Tastatur für die Simulation" | F4 | Wenn sie deaktiviert ist, wird die Tastatureingabe an die anwendung HoloLens oder Windows Mixed Reality. |
| Umschalten von "Maus für Simulation verwenden" | F5 | Wenn die Mauseingabe deaktiviert ist, wird die Mixed Reality Umgebung (nur Windows Mixed Reality) |
| Umschalten von "Gamepad für Simulation verwenden" | F6 | Wenn die Gamepadeingabe deaktiviert ist, wird sie von der Simulation ignoriert. |
| Ein- oder Ausblenden der Systemsteuerung | F7 | |
| Festlegen des Tastaturfokus auf die Systemsteuerung | F8 | Wenn der Bereich derzeit nicht angezeigt wird, wird er zuerst angezeigt. |
| Andocken oder Abdocken des Bereichs an den Emulator oder Mixed Reality-Portal Fenster | F9 | Wenn das Fenster beim Abdocken geschlossen wird, wird es angedockt und ausgeblendet. |

## <a name="see-also"></a>Siehe auch
* [Installieren der Tools](../install-the-tools.md)
* [Verwendung des HoloLens-Emulators](using-the-hololens-emulator.md)
* [Verwenden des Windows Mixed Reality-Simulators](using-the-windows-mixed-reality-simulator.md)
