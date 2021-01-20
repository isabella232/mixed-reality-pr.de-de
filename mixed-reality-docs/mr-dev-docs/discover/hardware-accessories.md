---
title: Hardware-Zubehör
description: Beschreibt die Arten von Zubehör, die für die Verwendung mit Windows Mixed Reality verfügbar sind, und wie diese eingerichtet werden.
author: mattzmsft
ms.author: mazeller
ms.date: 05/20/2020
ms.topic: article
keywords: Anleitungen, Zubehör, Bluetooth, BT, Controller, Gamepad, Clicker, Xbox, Hardware, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Motion Controller
ms.openlocfilehash: b9a58a34a88de01d1d2351ff0a5efbe4f99298db
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583323"
---
# <a name="hardware-accessories"></a>Hardware-Zubehör

Windows Mixed Reality-Geräte unterstützen Zubehör. Sie können Bluetooth-oder USB-Ports verwenden, um unterstützte Zubehör mit einem immersiven Headset von Ihrem PC zu koppeln.

Informationen zur Verwendung von Bluetooth-Zubehör mit hololens finden Sie unter [Herstellen einer Verbindung mit Bluetooth und USB-C-Geräten](/hololens/hololens-connect-devices).

Immersive Headsets in Windows Mixed Reality erfordern Zubehör für Eingaben, die über den [Blick](../design/gaze-and-commit.md) und die [Stimme](../design/voice-input.md)hinausgehen. Unterstützte Zubehör sind **Tastatur-und Maus-**, **Gamepad**-und **[Bewegungs Controller](../design/motion-controllers.md)**.

## <a name="pairing-bluetooth-accessories"></a>Kopplung von Bluetooth-Zubehör

Die Kopplung einer Bluetooth-Peripherie mit einem immersiven Headset ähnelt dem Koppeln einer Bluetooth-Peripherie mit einem Windows 10-Desktop oder einem mobilen Gerät:

1. Öffnen Sie im Startmenü die app " **Einstellungen** ".
2. Zu **Geräten** wechseln
3. Aktivieren Sie das Bluetooth-Radio, wenn es mithilfe des Schieberegler-Schalters ausgeschaltet ist.
4. Platzieren Sie Ihr Bluetooth-Gerät im Paarmodus. Dieser Prozess unterscheidet sich von Gerät zu Gerät, aber auf den meisten Bluetooth-Geräten halten Sie eine oder mehrere Schaltflächen gedrückt.
5. Warten Sie, bis der Name des Geräts in der Liste der Bluetooth-Geräte angezeigt wird. Wählen Sie dann das Gerät aus, und wählen Sie dann die Schaltfläche **paar** aus. Wenn Sie über viele Bluetooth-Geräte in der Nähe verfügen, müssen Sie möglicherweise einen Bildlauf zum Ende der Bluetooth-Geräteliste durchführen, um das Gerät anzuzeigen, das Sie koppeln möchten.
6. Beim Koppeln von Bluetooth-Peripheriegeräten mit Eingabefunktionen (z. b. Bluetooth-Tastaturen) kann eine 6-stellige oder eine 8-stellige PIN angezeigt werden. Achten Sie darauf, dass Sie diese Pin am Peripheriegerät eingeben und dann die EINGABETASTE drücken, um die Kopplung mit dem Headset abzuschließen.

## <a name="motion-controllers"></a>Bewegungscontroller

Windows Mixed Reality [Motion Controller](../design/motion-controllers.md) werden von immersiven Headsets, aber nicht von hololens unterstützt. Diese Controller bieten eine präzise und reaktionsfähige Bewegungs Nachverfolgung in ihrer Sicht. Sensoren im immersiven Headset führen die Nachverfolgung aus, d. h., es ist nicht erforderlich, Hardware an den Wänden in Ihrem Bereich zu installieren. Jeder Controller verfügt über mehrere Methoden der Eingabe.

![Windows Mixed Reality-Bewegungs Controller](../design/images/winmr-ck-1080x1080-350px.jpg)

## <a name="bluetooth-keyboards"></a>Bluetooth-Tastaturen

In englischer Sprache Verfügbarkeit Bluetooth-Tastaturen können paarweise gekoppelt und überall dort verwendet werden, wo Sie die holografische Tastatur verwenden können. Wenn Sie eine Qualitäts Tastatur erhalten, empfiehlt es sich, die [universelle Microsoft-Tastatur](https://www.microsoft.com/accessories/products/keyboards/universal-foldable-keyboard/gu5-00001) oder den [Microsoft Designer Bluetooth Desktop](https://www.microsoft.com/accessories/products/keyboards/designer-bluetooth-desktop/7n9-00001)zu erhalten.

## <a name="bluetooth-gamepads"></a>Bluetooth-Gamepads

Sie können einen Controller mit apps und spielen verwenden, die die Gamepad-Unterstützung speziell aktivieren. Gamepads können nicht zum Steuern der hololens-Benutzeroberfläche verwendet werden.

Xbox Wireless-Controller, die mit der Xbox One s oder als Zubehör für die Xbox One s-Funktion für Bluetooth-Konnektivität verkauft werden, damit Sie Sie mit hololens und immersiven Headsets verwenden können. Der Xbox Wireless Controller [muss aktualisiert werden](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) , bevor er mit hololens verwendet werden kann.

Andere Marken von Bluetooth-Gamepads können mit Windows Mixed Reality-Geräten verwendet werden, die Unterstützung variiert jedoch je nach Anwendung.

## <a name="other-bluetooth-accessories"></a>Andere Bluetooth-Zubehör

Solange das Peripheriegerät entweder die Bluetooth HID-oder GATT-Profile unterstützt, kann es mit hololens gekoppelt werden. Andere Bluetooth HID-und GATT-Geräte außer Tastatur, MICE und hololens Clicker erfordern möglicherweise, dass eine Begleit Anwendung auf Microsoft hololens voll funktionsfähig ist.

Zu den nicht unterstützten Peripheriegeräten gehören:

* Peripheriegeräte in den Bluetooth-audioprofilen werden nicht unterstützt.
* Bluetooth-Audiogeräte, wie z. b. Sprecher und Headsets, sind möglicherweise in der App "Einstellungen" verfügbar, werden aber nicht mit Microsoft hololens als audioendpunkt unterstützt.
* Bluetooth-aktivierte Telefone und PCs werden für Kopplung und Dateiübertragungen nicht unterstützt.

## <a name="unpairing-a-bluetooth-peripheral"></a>Entkopplung einer Bluetooth-Peripherie

1. Öffnen Sie im Startmenü die app " **Einstellungen** ".
2. Zu **Geräten** wechseln
3. Aktivieren Sie das Bluetooth-Radio, wenn es deaktiviert ist.
4. Suchen Ihres Geräts in der Liste der verfügbaren Bluetooth-Geräte
5. Wählen Sie Ihr Gerät aus der Liste aus, und klicken Sie dann auf die Schaltfläche **Entfernen**