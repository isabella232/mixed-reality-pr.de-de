---
title: Verwenden des Windows Mixed Reality-Simulators
description: Der Windows Mixed Reality-Simulator ermöglicht Ihnen das Testen von Mixed Reality-apps auf Ihrem PC ohne ein Windows Mixed Reality-immersives-Headset.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
keywords: Gemischte Windows-Realität, Simulator, Tests
ms.openlocfilehash: 4ed3355df242f1df35c009e53149d834ea113e1f
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530297"
---
# <a name="using-the-windows-mixed-reality-simulator"></a>Verwenden des Windows Mixed Reality-Simulators

Der Windows Mixed Reality-Simulator ermöglicht Ihnen das Testen von Mixed Reality-apps auf Ihrem PC ohne ein Windows Mixed Reality-immersives-Headset. Der Simulator ist mit dem Windows 10 Creators Update verfügbar. Der Simulator ähnelt dem [hololens-Emulator](using-the-hololens-emulator.md), obwohl der Simulator keinen virtuellen Computer verwendet. Simulierte apps werden in Ihrer Windows 10-Desktop Benutzersitzung genauso wie bei Verwendung eines immersiven Headsets ausgeführt. Die von den Sensoren auf einem immersiven Headset gelesenen Personen-und Umgebungs Eingaben werden stattdessen mit dem Tastatur-, Maus-oder Xbox-Controller simuliert. Apps müssen keine Änderungen für die Ausführung im Simulator ausführen, und Sie wissen nicht, dass Sie nicht auf einem immersiven Headset ausgeführt werden.

## <a name="enabling-the-windows-mixed-reality-simulator"></a>Aktivieren des Windows Mixed Reality-Simulators

1. **Aktivieren des Entwicklermodus** über Einstellungen-> Update-und Sicherheits > für Entwickler
2. Starten des **Mixed Reality-Portals** über den Desktop
3. Wenn Sie das Portal zum ersten Mal starten, müssen Sie die Einrichtung durchlaufen.
   1. " **Get Started** " auswählen
   2. Wählen Sie **Ich stimme** zu, um die Vereinbarung zu akzeptieren.
   3. Wählen Sie **für Simulation einrichten (für Entwickler)** , um das Setup ohne physisches Gerät fortzusetzen
   4. Wählen Sie " **Einrichten** ", um Ihre Auswahl zu bestätigen.
4. Wählen Sie auf der linken Seite des Mixed Reality-Portals die Schaltfläche **für Entwickler aus** .
5. Aktivieren **Sie die UMSCHALT Fläche für Simulation** aktivieren auf ein.
   * Durch das Aktivieren der Simulation wird der linke simulierte 6-DOF-Controller standardmäßig installiert und aktiviert.  Vor dem Windows 10-Update von Mai 2019 ist für die Installation eines simulierten 6-DOF-Controllers Administrator Berechtigungen erforderlich.  Akzeptieren Sie das Dialogfeld Benutzerkontensteuerung, wenn eine solche angezeigt wird.

Sie sollten jetzt mit Simulation ausführen!

Wenn Sie den Entwicklermodus in den Einstellungen deaktivieren möchten, müssen Sie zunächst im Mixed Reality-Portal im Abschnitt **for Developers (für Entwickler** ) die Option Simulation Umschalten auf **aus** deaktivieren.

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a>Bereitstellen von apps im Mixed Reality-Simulator

Da der Simulator auf dem lokalen PC ohne einen virtuellen Computer ausgeführt wird, können Sie beim Debuggen ihre universellen Windows-apps auf dem **lokalen Computer** bereitstellen.

## <a name="basic-simulator-input"></a>Grundlegende simulatoreingabe

Das Steuern des Simulators ähnelt vielen gängigen 3D-Videospielen und dem [hololens-Emulator](using-the-hololens-emulator.md). Es stehen Eingabeoptionen über die Tastatur, Maus oder den Xbox-Controller zur Verfügung.

Sie steuern den Simulator, indem Sie die Aktionen eines simulierten Benutzers mit einem immersiven Headset umleiten. Ihre Aktionen verschieben den simulierten Benutzer und bewirken Interaktionen mit apps, die so reagieren, wie Sie auf einem immersiven Headset auftreten würden.
* **Nach vorne, hinten, links und rechts gehen**: Verwenden Sie die Tasten W, A, S und D auf Ihrer Tastatur oder den linken Stick eines Xbox-Controllers.
* **Suchen Sie nach oben, nach unten, nach links und** mit der rechten Maustaste, und ziehen Sie die Maus, verwenden Sie die Pfeiltasten auf der Tastatur oder den rechten Strich auf einem Xbox-Controller.
* **Aktions Schaltfläche auf Controller drücken** : Klicken Sie mit der rechten Maustaste auf die Maus, drücken Sie die Eingabetaste auf der Tastatur, oder verwenden Sie die Schaltfläche A auf einem Xbox-Controller.
* **Start Taste auf dem Controller** drücken Sie die Windows-Taste oder F2-Taste auf der Tastatur, oder drücken Sie auf einem Xbox-Controller die Taste B.
* **Controller Bewegung für Scrollen** : halten Sie die Alt-Taste und die Rechte Maustaste gedrückt, und ziehen Sie die Maus nach oben/unten. Halten Sie in einem Xbox-Controller den rechten und eine Schaltfläche gedrückt, und verschieben Sie den rechten Stift nach oben und unten.

## <a name="tracked-controllers"></a>Nach verfolgte Controller

Der Simulator für gemischte Realität kann bis zu zwei handgehaltene Bewegungs Controller simulieren. Aktivieren Sie diese mithilfe der umschaltschalter im Mixed Reality-Portal. Jeder simulierte Controller hat Folgendes:
* Position und Ausrichtung im Raum
* Schaltfläche „Start“
* Menü-Taste
* Zieh Schaltfläche
* Touchpad
* Ministick
* Akku Pegel

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie dem Weg der Unity-Entwicklungsprüfpunkte folgen, den wir entworfen haben, befinden Sie sich in der Mitte der Bereitstellungsphase. Von hier aus können Sie mit dem nächsten [Thema](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) fortfahren oder direkt zum Hinzufügen von Advanced Services springen.

> [!div class="nextstepaction"]
> [Erweiterte Dienste](../../develop/unity/unity-development-overview.md#5-adding-services)


## <a name="see-also"></a>Weitere Informationen
* [Verwendung des HoloLens-Emulators](using-the-hololens-emulator.md)
* [Erweiterte Eingabe des gemischten Reality-Simulators](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Räumliche Abbildung in Unity](../../develop/unity/spatial-mapping-in-unity.md)
* [Räumliche Abbildung in DirectX](../../develop/native/spatial-mapping-in-directx.md)
