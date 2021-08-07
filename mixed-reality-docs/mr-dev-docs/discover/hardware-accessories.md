---
title: Hardware-Zubehör
description: Beschreibt die Arten von Zubehör, die mit Windows Mixed Reality verwendet werden können, und wie sie eingerichtet werden.
author: mattzmsft
ms.author: mazeller
ms.date: 05/20/2020
ms.topic: article
keywords: Vorgehensweise, Zubehör, Bluetooth, Bt, Controller, Gamepad, Clicker, Xbox, Hardware, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Motion Controller
ms.openlocfilehash: a6776df9374fce3f1399de944be06c93ff6fdcb3e6f4a38dcc92453556857376
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188454"
---
# <a name="hardware-accessories"></a>Hardware-Zubehör

Windows Mixed Reality Geräte unterstützen Zubehör. Sie können Bluetooth oder USB-Anschlüsse verwenden, um unterstütztes Zubehör von Ihrem PC mit einem immersiven Headset zu koppeln.

Informationen zur Verwendung von Bluetooth Zubehör mit HoloLens finden Sie unter [Verbinden für Bluetooth und USB-C-Geräte.](/hololens/hololens-connect-devices)

Windows Mixed Reality immersive Headsets benötigen Zubehör für Eingaben, die über [Anvieren](../design/gaze-and-commit.md) und [Spracheingabe](../design/voice-input.md)hinausgehen. Zu den unterstützten Zubehör gehören **Tastatur und Maus,** **Gamepad** und **[Motion-Controller.](../design/motion-controllers.md)**

## <a name="pairing-bluetooth-accessories"></a>Koppeln von Bluetooth Zubehör

Das Koppeln eines Bluetooth Peripheriegeräts mit einem immersiven Headset ähnelt dem Koppeln eines Bluetooth Peripheriegeräts mit einem Windows 10 Desktopgerät oder mobilen Gerät:

1. Öffnen Sie im Startmenü die **Einstellungen-App.**
2. Wechseln Sie zu **Geräte.**
3. Aktivieren Sie das Bluetooth, wenn es mit dem Schiebereglerschalter ausgeschaltet ist.
4. Platzieren Sie Ihr Bluetooth Gerät im Kopplungsmodus. Dieser Prozess variiert von Gerät zu Gerät, aber auf den meisten Bluetooth Geräte drücken und halten mindestens eine Taste gedrückt.
5. Warten Sie, bis der Name des Geräts in der Liste der Bluetooth Geräte angezeigt wird. Wählen Sie anschließend das Gerät und dann die Schaltfläche **Koppeln** aus. Wenn Sie viele Bluetooth Geräte in der Nähe haben, müssen Sie möglicherweise nach unten in der Geräteliste Bluetooth scrollen, um das Gerät anzuzeigen, das Sie koppeln möchten.
6. Beim Koppeln Bluetooth Peripheriegeräten mit Eingabefunktion (z. B. Bluetooth Tastaturen) wird möglicherweise ein sechsstelliger oder ein achtstelliger Pin angezeigt. Geben Sie diesen Stecknadel an das Peripheriegerät ein, und drücken Sie dann die EINGABETASTE, um die Kopplung mit dem Headset abzuschließen.

## <a name="motion-controllers"></a>Bewegungscontroller

Windows Mixed Reality [Motion-Controller](../design/motion-controllers.md) werden von immersiven Headsets unterstützt, jedoch nicht HoloLens. Diese Controller bieten eine präzise und reaktionsfähige Bewegungsnachverfolgung in Ihrem Sichtfeld. Sensoren im immersiven Headset erledigen die Nachverfolgung, d.h., es ist nicht erforderlich, Hardware auf den Wänden in Ihrem Raum zu installieren. Jeder Controller verfügt über mehrere Eingabemethoden.

![Windows Mixed Reality Motion-Controller](../design/images/winmr-ck-1080x1080-350px.jpg)

## <a name="bluetooth-keyboards"></a>Bluetooth Tastaturen

Qwerty in englischer Sprache Bluetooth Tastaturen können gekoppelt und überall dort verwendet werden, wo Sie die holografische Tastatur verwenden können. Das Abrufen einer hochwertigen Tastatur macht einen Unterschied, daher empfehlen wir die [Microsoft Universal Foldable Keyboard](https://www.microsoft.com/accessories/products/keyboards/universal-foldable-keyboard/gu5-00001) oder microsoft Designer Bluetooth [Desktop](https://www.microsoft.com/accessories/products/keyboards/designer-bluetooth-desktop/7n9-00001).

## <a name="bluetooth-gamepads"></a>Bluetooth Gamepads

Sie können einen Controller mit Apps und Spielen verwenden, die speziell gamepad-Unterstützung ermöglichen. Gamepads können nicht zum Steuern der HoloLens Benutzeroberfläche verwendet werden.

Xbox-Funkcontroller, die mit dem Xbox One S geliefert oder als Zubehör für das Xbox One S-Feature Bluetooth Konnektivität verkauft werden, sodass Sie sie mit HoloLens und immersiven Headsets verwenden können. Der Xbox Wireless Controller [muss aktualisiert werden,](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) bevor er mit HoloLens verwendet werden kann.

Andere Marken von Bluetooth Gamepads funktionieren möglicherweise mit Windows Mixed Reality Geräten, aber die Unterstützung variiert je nach Anwendung.

## <a name="other-bluetooth-accessories"></a>Anderes Bluetooth Zubehör

Solange das Peripheriegerät die Bluetooth HID- oder GATT-Profile unterstützt, kann es mit HoloLens gekoppelt werden. Andere Bluetooth HID- und GATT-Geräte neben Tastatur, Maus und HoloLens Clicker erfordern möglicherweise eine Begleitanwendung auf Microsoft HoloLens, um voll funktionsfähig zu sein.

Zu den nicht unterstützten Peripheriegeräten gehören:

* Peripheriegeräte in den Bluetooth Audioprofilen werden nicht unterstützt.
* Bluetooth Audiogeräte wie Lautsprecher und Headsets sind möglicherweise in der Einstellungen-App verfügbar, werden jedoch nicht mit Microsoft HoloLens als Audioendpunkt unterstützt.
* Bluetooth-fähige Telefone und PCs werden für Kopplung und Dateiübertragungen nicht unterstützt.

## <a name="unpairing-a-bluetooth-peripheral"></a>Entkohen eines Bluetooth Peripheriegeräts

1. Öffnen Sie im Startmenü die **Einstellungen-App.**
2. Wechseln Sie zu **Geräte.**
3. Aktivieren Sie das Bluetooth, wenn es deaktiviert ist.
4. Suchen Sie Ihr Gerät in der Liste der verfügbaren Bluetooth Geräte.
5. Wählen Sie Ihr Gerät aus der Liste und dann die Schaltfläche **Entfernen** aus.