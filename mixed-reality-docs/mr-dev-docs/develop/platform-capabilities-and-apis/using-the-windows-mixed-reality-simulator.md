---
title: Verwenden des Windows Mixed Reality-Simulators
description: Mit dem Windows Mixed Reality Simulator können Sie Mixed Reality-Apps auf Ihrem PC ohne Windows Mixed Reality immersive Headset testen.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
keywords: Windows Mixed Reality, Simulator, Testen
ms.openlocfilehash: 0a6ff0cb0cd893c40e354c0590437201fb97e75c67421a638e47897b19a8f688
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220933"
---
# <a name="using-the-windows-mixed-reality-simulator"></a>Verwenden des Windows Mixed Reality-Simulators

Mit dem Windows Mixed Reality Simulator können Sie Mixed Reality-Apps auf Ihrem PC ohne Windows Mixed Reality immersive Headset testen. Der Simulator ist mit dem Windows 10 Creators Update verfügbar. Der Simulator ähnelt dem [HoloLens Emulator](using-the-hololens-emulator.md), obwohl der Simulator keinen virtuellen Computer verwendet. Simulierte Apps werden in Ihrer Windows 10 Desktopbenutzersitzung ausgeführt, genau wie bei Verwendung eines immersiven Headsets. Die Eingaben von Menschen und Umgebungen, die von den Sensoren auf einem immersiven Headset gelesen werden, werden stattdessen mithilfe Ihrer Tastatur, Maus oder Ihres Xbox-Controllers simuliert. Apps müssen nicht geändert werden, um im Simulator ausgeführt zu werden, und wissen nicht, dass sie nicht auf einem immersiven Headset ausgeführt werden.

## <a name="enabling-the-windows-mixed-reality-simulator"></a>Aktivieren des Windows Mixed Reality Simulators

1. **Aktivieren des Entwicklermodus** über Einstellungen -> Update and Security -> For developers
2. Starten der **Mixed Reality-Portal** über den Desktop
3. Wenn Sie das Portal zum ersten Mal starten, müssen Sie die Einrichtung durchlaufen.
   1. Wählen Sie **Erste Schritte aus.**
   2. Wählen Sie **Ich stimme** zu aus, um die Vereinbarung zu akzeptieren.
   3. Wählen Sie **Für Simulation einrichten (für Entwickler)** aus, um das Setup ohne physisches Gerät fortzusetzen.
   4. Wählen Sie **Einrichten** aus, um Ihre Auswahl zu bestätigen.
4. Wählen Sie links im Mixed Reality-Portal die Schaltfläche **For developers (Entwickler)** aus.
5. Umschalten der Umschaltfläche "Simulation" auf **"Ein"**
   * Durch aktivieren der Simulation wird standardmäßig der nach links simulierte 6-DOF-Controller installiert und aktiviert.  Vor dem update Windows 10 Mai 2019 sind für die Installation eines simulierten 6-DOF-Controllers Administratorberechtigungen erforderlich.  Akzeptieren Sie das Dialogfeld Benutzerkontensteuerung, wenn eines angezeigt wird.

Sie sollten jetzt mit simulation ausgeführt werden!

Wenn Sie den Entwicklermodus in Einstellungen deaktivieren möchten, sollten Sie zuerst im Abschnitt **Für Entwickler** des Mixed Reality-Portal die Umschaltfläche Simulation auf **Aus** umschalten.

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a>Bereitstellen von Apps im Mixed Reality Simulator

Da der Simulator auf Ihrem lokalen PC ohne virtuellen Computer ausgeführt wird, können Sie Ihre Universellen Windows-Apps beim Debuggen auf dem **lokalen Computer** bereitstellen.

## <a name="basic-simulator-input"></a>Grundlegende Simulatoreingabe

Die Steuerung des Simulators ähnelt vielen gängigen 3D-Spielen und dem [HoloLens Emulator.](using-the-hololens-emulator.md) Es stehen Eingabeoptionen über die Tastatur, Maus oder den Xbox-Controller zur Verfügung.

Sie steuern den Simulator, indem Sie die Aktionen eines simulierten Benutzers mit einem immersiven Headset steuern. Ihre Aktionen verschieben den simulierten Benutzer und verursachen Interaktionen mit Apps, die wie auf einem immersiven Headset reagieren.
* **Nach vorne, hinten, links und rechts gehen**: Verwenden Sie die Tasten W, A, S und D auf Ihrer Tastatur oder den linken Stick eines Xbox-Controllers.
* **Nach oben, unten, links und rechts:** Wählen Sie die Maus aus, ziehen Sie sie, verwenden Sie die Pfeiltasten auf der Tastatur oder den rechten Stick auf einem Xbox-Controller.
* **Aktionstaste auf Controller drücken:** Klicken Sie mit der rechten Maustaste auf die Maus, drücken Sie die EINGABETASTE auf der Tastatur, oder verwenden Sie die Taste A auf einem Xbox-Controller.
* **Starttaste drücken auf Controller:** Drücken Sie die Windows Taste oder F2-Taste auf der Tastatur, oder drücken Sie die B-Taste auf einem Xbox-Controller.
* **Controllerbewegung zum Scrollen:** Halten Sie die ALT-TASTE und die rechte Maustaste gedrückt, und ziehen Sie dann die Maus nach oben/unten. Halten Sie auf einem Xbox-Controller den rechten Auslöser und die A-Taste gedrückt, und bewegen Sie den rechten Stift nach oben und unten.

## <a name="tracked-controllers"></a>Nachverfolgte Controller

Der Mixed Reality Simulator kann bis zu zwei handgehaltene nachverfolgte Motion-Controller simulieren. Aktivieren Sie sie mithilfe der Umschaltschalter im Mixed Reality-Portal. Jeder simulierte Controller verfügt über:
* Position und Ausrichtung im Raum
* Schaltfläche „Start“
* Menü-Taste
* Taste "Klammer"
* Touchpad
* Thumbstick
* Akkustand

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie dem Weg der Unity-Entwicklungsprüfpunkte folgen, den wir entworfen haben, befinden Sie sich in der Mitte der Bereitstellungsphase. Hier können Sie mit dem nächsten [Thema](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) fortfahren oder direkt mit dem Hinzufügen erweiterter Dienste fortfahren.

> [!div class="nextstepaction"]
> [Erweiterte Dienste](../../develop/unity/unity-development-overview.md#5-adding-services)


## <a name="see-also"></a>Siehe auch
* [Verwendung des HoloLens-Emulators](using-the-hololens-emulator.md)
* [Erweiterte Mixed Reality Simulatoreingabe](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Räumliche Abbildung in Unity](../../develop/unity/spatial-mapping-in-unity.md)
* [Räumliche Abbildung in DirectX](../../develop/native/spatial-mapping-in-directx.md)
