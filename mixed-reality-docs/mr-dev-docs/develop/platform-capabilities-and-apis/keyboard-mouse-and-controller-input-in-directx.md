---
title: Tastatur-, Maus- und Controllereingaben in DirectX
description: Erläutert das Erstellen einer App für Windows Mixed Reality, die Tastatur-, Maus- und Gamecontroller verwendet.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, Tastatur, Maus, Gamecontroller, Xbox-Controller, HoloLens, Desktop, exemplarische Vorgehensweise, Beispielcode
ms.openlocfilehash: 2e83fa0a14a24eb98001c7dc88af062202a2ef9a5eee7cd53e9702dbe4eedc8e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192024"
---
# <a name="keyboard-mouse-and-controller-input-in-directx"></a>Tastatur-, Maus- und Controllereingaben in DirectX

> [!NOTE]
> Dieser Artikel bezieht sich auf die nativen WinRT-Legacy-APIs.  Für neue native App-Projekte wird die Verwendung der **[OpenXR-API](../native/openxr-getting-started.md)** empfohlen.

Tastaturen, Mausen und Gamecontroller können nützliche Eingabeformen für Windows Mixed Reality Geräte sein. Bluetooth Tastaturen und Mause werden auf HoloLens sowohl für das Debuggen Ihrer App als auch als alternative Eingabeform unterstützt. Windows Mixed Reality unterstützt auch immersive Headsets, die an PCs angefügt sind, wobei Maus, Tastatur und Gamecontroller in der Vergangenheit die Norm waren.

Um tastatureingaben auf HoloLens zu verwenden, koppeln Sie eine Bluetooth Tastatur mit Ihrem Gerät, oder verwenden Sie virtuelle Eingaben über die Windows Geräteportal. Wenn Sie eine Tastatureingabe verwenden möchten, während Sie ein Windows Mixed Reality immersive Headset verwenden, weisen Sie Mixed Reality den Eingabefokus zu, indem Sie das Gerät verwenden oder die Tastenkombination Windows Key + Y verwenden. Beachten Sie, dass Apps, die für HoloLens vorgesehen sind, Funktionen bereitstellen müssen, ohne dass diese Geräte angeschlossen sind.

>[!NOTE]
>Die Codeausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung von C++/CX anstelle von C++17-kompatiblem C++/WinRT, wie in der [holografischen C++-Projektvorlage](../native/creating-a-holographic-directx-project.md)verwendet.  Die Konzepte sind für ein C++/WinRT-Projekt gleichwertig, aber Sie müssen den Code übersetzen.

## <a name="subscribe-for-corewindow-input-events"></a>Abonnieren von CoreWindow-Eingabeereignissen

### <a name="keyboard-input"></a>Tastatureingabe

In der Windows Holographic-App-Vorlage fügen wir einen Ereignishandler für Tastatureingaben wie jede andere UWP-App hinzu. Ihre App verwendet Tastatureingabedaten auf die gleiche Weise in Windows Mixed Reality.

Über AppView.cpp:

```
// Register for keypress notifications.
   window->KeyDown +=
       ref new TypedEventHandler<CoreWindow^, KeyEventArgs^>(this, &AppView::OnKeyPressed);

    …

   // Input event handlers

   void AppView::OnKeyPressed(CoreWindow^ sender, KeyEventArgs^ args)
   {
       //
       // TODO: Respond to keyboard input here.
       //
   }
```

### <a name="virtual-keyboard-input"></a>Virtuelle Tastatureingabe
Für immersive Desktop-Headsets können Sie virtuelle Tastaturen unterstützen, die von Windows über Ihrer immersiven Ansicht gerendert werden, indem Sie **CoreTextEditContext** implementieren. Auf diese Weise können Windows den Zustand Ihrer eigenen in der App gerenderten Textfelder verstehen, sodass die virtuelle Tastatur ordnungsgemäß zum Text beitragen kann.

Weitere Informationen zum Implementieren der CoreTextEditContext-Unterstützung finden Sie im [CoreTextEditContext-Beispiel.](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl)

### <a name="mouse-input"></a>Mauseingabe

Sie können die Mauseingabe auch wieder über die UWP CoreWindow-Eingabeereignishandler verwenden. So ändern Sie die Windows Holographic-App-Vorlage, um Mausklicks auf die gleiche Weise wie gedrückte Gesten zu unterstützen. Nachdem Sie diese Änderung vorgenommen haben, positioniert ein Mausklick während des Tragens eines immersiven Headsetgeräts den Würfel neu.

> [!NOTE]
> UWP-Apps können auch unformatierte XY-Daten für die Maus mithilfe der [MouseDevice-API](/uwp/api/Windows.Devices.Input.MouseDevice) abrufen.

Deklarieren Sie zunächst einen neuen OnPointerPressed-Handler in AppView.h:

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

Fügen Sie in AppView.cpp den code zu SetWindow hinzu:

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

Legen Sie dann diese Definition für OnPointerPressed am Ende der Datei ab:

```
void AppView::OnPointerPressed(CoreWindow^ sender, PointerEventArgs^ args)
   {
       // Allow the user to interact with the holographic world using the mouse.
       if (m_main != nullptr)
       {
           m_main->OnPointerPressed();
       }
   }
```

Der soeben hinzugefügte Ereignishandler ist ein Pass-Through zur Hauptklasse der Vorlage. Wir ändern die Hauptklasse, um diese Pass-Through-Klasse zu unterstützen. Fügen Sie der Headerdatei die folgende öffentliche Methodendeklaration hinzu:

```
// Handle mouse input.
       void OnPointerPressed();
```

Sie benötigen auch diese private Membervariable:

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

Schließlich aktualisieren wir die Hauptklasse mit neuer Logik, um Mausklicks zu unterstützen. Fügen Sie zunächst diesen Ereignishandler hinzu. Stellen Sie sicher, dass Sie den Klassennamen aktualisieren:

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

Ersetzen Sie nun in der Update-Methode die vorhandene Logik zum Abrufen einer Zeigerpose durch Folgendes:

```
SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

Erneutes Kompilieren und erneutes Bereitstellen. Beachten Sie, dass der Würfel nun mit dem Mausklick in Ihrem immersiven Headset neu positioniert wird – oder HoloLens mit angefügter Bluetooth-Maus.

### <a name="game-controller-support"></a>Unterstützung von Spielcontrollern

Gamecontroller können eine interessante und praktische Möglichkeit sein, dem Benutzer die Steuerung einer immersiven Windows Mixed Reality zu ermöglichen.

 Fügen Sie der Headerklasse für Ihre Hauptdatei die folgenden privaten Memberdeklarationen hinzu:

```
// Recognize gamepads that are plugged in after the app starts.
       void OnGamepadAdded(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
// Stop looking for gamepads that are unplugged.
       void OnGamepadRemoved(Platform::Object^, Windows::Gaming::Input::Gamepad^ args);
```

```
Windows::Foundation::EventRegistrationToken                     m_gamepadAddedEventToken;
       Windows::Foundation::EventRegistrationToken                     m_gamepadRemovedEventToken;
```

```
// Keeps track of a gamepad and the state of its A button.
       struct GamepadWithButtonState
       {
           Windows::Gaming::Input::Gamepad^ gamepad;
           bool buttonAWasPressedLastFrame = false;
       };
       std::vector<GamepadWithButtonState>                             m_gamepads;
```

Initialisieren Sie Gamepadereignisse und alle gamepads, die derzeit angefügt sind, im Konstruktor für Ihre Hauptklasse:

```
// If connected, a game controller can also be used for input.
   m_gamepadAddedEventToken = Gamepad::GamepadAdded +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadAdded, this, _1, _2)
           );
```

```
m_gamepadRemovedEventToken = Gamepad::GamepadRemoved +=
       ref new EventHandler<Gamepad^>(
           bind(&$safeprojectname$Main::OnGamepadRemoved, this, _1, _2)
           );
```

```
for (auto const& gamepad : Gamepad::Gamepads)
   {
       OnGamepadAdded(nullptr, gamepad);
   }
```

Fügen Sie diese Ereignishandler ihrer Hauptklasse hinzu. Stellen Sie sicher, dass Sie den Klassennamen aktualisieren:

```
void MyHolographicAppMain::OnGamepadAdded(Object^, Gamepad^ args)
   {
       for (auto const& gamepadWithButtonState : m_gamepads)
       {
           if (args == gamepadWithButtonState.gamepad)
           {
               // This gamepad is already in the list.
               return;
           }
       }
       m_gamepads.push_back({ args, false });
   }
```

```
void MyHolographicAppMain::OnGamepadRemoved(Object^, Gamepad^ args)
   {
       m_gamepads.erase(
           std::remove_if(m_gamepads.begin(), m_gamepads.end(), [&](GamepadWithButtonState& gamepadWithState)
               {
                   return gamepadWithState.gamepad == args;
               }),
           m_gamepads.end());
   }
```

Aktualisieren Sie abschließend die Eingabelogik, um Änderungen im Controllerzustand zu erkennen. Hier verwenden wir die gleiche m_pointerPressed Variable, die im obigen Abschnitt zum Hinzufügen von Mausereignissen erläutert wird. Fügen Sie dies der Update-Methode direkt vor dem Ort hinzu, an dem sie nach SpatialPointerPose sucht:

```
// Check for new input state since the last frame.
   for (auto& gamepadWithButtonState : m_gamepads)
   {
       bool buttonDownThisUpdate = ((gamepadWithButtonState.gamepad->GetCurrentReading().Buttons & GamepadButtons::A) == GamepadButtons::A);
       if (buttonDownThisUpdate && !gamepadWithButtonState.buttonAWasPressedLastFrame)
       {
           m_pointerPressed = true;
       }
       gamepadWithButtonState.buttonAWasPressedLastFrame = buttonDownThisUpdate;
   }
```

```
// For context.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   SpatialPointerPose^ pose = nullptr;
   if (pointerState != nullptr)
   {
       pose = pointerState->TryGetPointerPose(currentCoordinateSystem);
   }
   else if (m_pointerPressed)
   {
       pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
   }
   m_pointerPressed = false;
```

Vergessen Sie nicht, die Registrierung der Ereignisse beim Bereinigen der Hauptklasse zu aufheben:

```
if (m_gamepadAddedEventToken.Value != 0)
   {
       Gamepad::GamepadAdded -= m_gamepadAddedEventToken;
   }
   if (m_gamepadRemovedEventToken.Value != 0)
   {
       Gamepad::GamepadRemoved -= m_gamepadRemovedEventToken;
   }
```

Kompilieren Sie neu, und stellen Sie es erneut her. Sie können jetzt einen Spielcontroller anfügen oder koppeln und ihn verwenden, um den drehenden Würfel neu zu positionieren.

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a>Wichtige Richtlinien für Tastatur- und Mauseingaben

Es gibt einige wichtige Unterschiede in bezug darauf, wie dieser Code auf Microsoft HoloLens verwendet werden kann – bei dem es sich um ein Gerät handelt, das hauptsächlich auf natürlichen Benutzereingaben basiert – und was auf einem Windows Mixed Reality-fähigen PC verfügbar ist.
* Sie können sich nicht darauf verlassen, dass Tastatur- oder Mauseingaben vorhanden sind. Die gesamte Funktionalität Ihrer App muss mit Anvieren, Gesten und Spracheingaben funktionieren.
* Wenn eine Bluetooth Tastatur angefügt ist, kann es hilfreich sein, Tastatureingaben für beliebigen Text zu aktivieren, den Ihre App möglicherweise anfragt. Dies kann z. B. eine hervorragende Ergänzung für das Diktieren sein.
* Verlassen Sie sich beim Entwerfen Ihrer App nicht auf WASD- und Maus-Look-Steuerelemente für Ihr Spiel(z. B. ). HoloLens ist für den Benutzer konzipiert, um durch den Raum zu gehen. In diesem Fall steuert der Benutzer die Kamera direkt. Eine Schnittstelle zum Steuern der Kamera im Raum mit Bewegungs-/Aussehen-Steuerelementen bietet nicht die gleiche Benutzeroberfläche.
* Tastatureingaben sind eine hervorragende Möglichkeit, das Debuggen Ihrer App oder Spiel-Engine zu steuern, insbesondere, da der Benutzer die Tastatur nicht verwenden muss. Die Verkabelung ist mit den CoreWindow-Ereignis-APIs identisch mit Ihren gewohnten. In diesem Szenario können Sie eine Möglichkeit implementieren, Ihre App so zu konfigurieren, dass Tastaturereignisse während der Debugsitzungen in den Modus "Nur Debugeingabe" weitergeleitet werden.
* Bluetooth Controller funktionieren auch.

## <a name="see-also"></a>Siehe auch
* [Hardware-Zubehör](../../discover/hardware-accessories.md)