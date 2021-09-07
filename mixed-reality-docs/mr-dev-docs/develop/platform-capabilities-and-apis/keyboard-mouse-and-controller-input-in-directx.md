---
title: Tastatur-, Maus- und Controllereingaben in DirectX
description: Erläutert das Erstellen einer App für Windows Mixed Reality, die Tastatur-, Maus- und Spielcontroller verwendet.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, Tastatur, Maus, Gamecontroller, Xbox Controller, HoloLens, Desktop, exemplarische Vorgehensweise, Beispielcode
ms.openlocfilehash: e7ae65e660fe0348205fabc1c292328912fb1cdc
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2021
ms.locfileid: "123244177"
---
# <a name="keyboard-mouse-and-controller-input-in-directx"></a>Tastatur-, Maus- und Controllereingaben in DirectX

> [!NOTE]
> Dieser Artikel bezieht sich auf die älteren nativen WinRT-APIs.  Für neue native App-Projekte wird die Verwendung der **[OpenXR-API empfohlen.](../native/openxr-getting-started.md)**

Tastaturen, Maus und Gamecontroller können alle nützliche Eingabeformen für Windows Mixed Reality sein. Bluetooth Tastaturen und Mausen werden beide auf HoloLens unterstützt, um sie zum Debuggen Ihrer App oder als alternative Eingabeform zu verwenden. Windows Mixed Reality unterstützt auch immersive Headsets, die an PCs angefügt sind, bei denen es sich in der Vergangenheit um Maus, Tastaturen und Gamecontroller gab.

Um Tastatureingaben auf HoloLens zu verwenden, koppeln Sie eine Bluetooth-Tastatur mit Ihrem Gerät, oder verwenden Sie virtuelle Eingaben über Windows Geräteportal. Um die Tastatureingabe zu verwenden, während Sie ein Windows Mixed Reality immersives Headset verwenden, weisen Sie Mixed Reality den Eingabefokus zu, indem Sie das Gerät anschalten oder die Tastenkombination Windows+ Y verwenden. Denken Sie daran, dass Apps, die für HoloLens vorgesehen sind, Funktionen bereitstellen müssen, ohne dass diese Geräte angefügt sind.
<!--Unity Note: the paragraph below explains that the article provides C++ code snippets. -->
>[!NOTE]
>Die Codeausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung von C++/CX anstelle von C++17-kompatiblem C++/WinRT, wie in der holografischen C++-Projektvorlage [verwendet.](../native/creating-a-holographic-directx-project.md)  Die Konzepte sind für ein C++/WinRT-Projekt gleichwertig, obwohl Sie den Code übersetzen müssen.

## <a name="subscribe-for-corewindow-input-events"></a>Abonnieren von CoreWindow-Eingabeereignissen

### <a name="keyboard-input"></a>Tastatureingabe

In der Windows Holographic-App-Vorlage fügen wir wie jede andere UWP-App einen Ereignishandler für tastatureingaben ein. Ihre App verwendet Tastatureingabedaten auf die gleiche Weise wie Windows Mixed Reality.

Aus AppView.cpp:

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
Für immersive Desktop-Headsets können Sie virtuelle Tastaturen unterstützen, die von Windows immersive Ansicht gerendert werden, indem **Sie CoreTextEditContext implementieren.** Dadurch können Windows den Zustand ihrer eigenen durch die App gerenderten Textfelder verstehen, damit die virtuelle Tastatur ordnungsgemäß zum Text beitragen kann.

Weitere Informationen zum Implementieren der CoreTextEditContext-Unterstützung finden Sie im [CoreTextEditContext-Beispiel.](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl)

### <a name="mouse-input"></a>Mauseingabe

Sie können auch die Mauseingabe verwenden, wiederum über die UWP CoreWindow-Eingabeereignishandler. Hier erfahren Sie, wie Sie die Windows Holographic-App-Vorlage so ändern, dass Mausklicks auf die gleiche Weise wie gedrückte Gesten unterstützt werden. Nachdem Sie diese Änderung vorgenommen haben, wird der Würfel durch einen Mausklick neu positioniert, während ein immersives Headsetgerät verwendet wird.

> [!NOTE]
> UWP-Apps können mithilfe der [MouseDevice-API](/uwp/api/Windows.Devices.Input.MouseDevice) auch unformatiert XY-Daten für die Maus abrufen.

Deklarieren Sie zunächst einen neuen OnPointerPressed-Handler in AppView.h:

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

Fügen Sie in AppView.cpp setWindow diesen Code hinzu:

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

Der soeben hinzugefügte Ereignishandler ist ein Pass-Through zur Hauptklasse der Vorlage. Ändern Wir nun die Hauptklasse, um diese Pass-Through-Klasse zu unterstützen. Fügen Sie der Headerdatei diese öffentliche Methodendeklaration hinzu:

```
// Handle mouse input.
       void OnPointerPressed();
```

Sie benötigen auch diese private Membervariable:

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

Abschließend aktualisieren wir die Hauptklasse mit neuer Logik, um Mausklicks zu unterstützen. Fügen Sie zunächst diesen Ereignishandler hinzu. Aktualisieren Sie unbedingt den Klassennamen:

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

Ersetzen Sie nun in der Update-Methode die vorhandene Logik zum Abrufen einer Zeigerpose durch Diese:

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

Erneutes Kompilieren und erneutes Bereitstellen. Beachten Sie, dass der Mausklick den Würfel nun in Ihrem immersiven Headset neu positioniert – oder HoloLens bluetooth-Maus angeschlossen ist.

### <a name="game-controller-support"></a>Gamecontrollerunterstützung

Spielcontroller können eine praktische und praktische Möglichkeit sein, dem Benutzer die Steuerung einer immersiven Windows Mixed Reality zu ermöglichen.

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

Initialisieren Sie Gamepadereignisse und alle Gamepads, die derzeit angefügt sind, im Konstruktor für Ihre Hauptklasse:

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

Fügen Sie diese Ereignishandler ihrer Hauptklasse hinzu. Aktualisieren Sie unbedingt den Klassennamen:

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

Aktualisieren Sie abschließend die Eingabelogik, um Änderungen im Controllerzustand zu erkennen. Hier verwenden wir die gleiche m_pointerPressed, die im obigen Abschnitt zum Hinzufügen von Mausereignissen erläutert wurde. Fügen Sie dies der Update-Methode hinzu, kurz bevor sie nach SpatialPointerPose sucht:

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

Kompilieren Sie erneut, und stellen Sie sie erneut zur Bereitstellung. Sie können nun einen Spielcontroller anfügen oder koppeln und damit den sich drehenden Würfel neu positionieren.

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a>Wichtige Richtlinien für Tastatur- und Mauseingaben

Es gibt einige wichtige Unterschiede in der Verwendung dieses Codes auf Microsoft HoloLens – einem Gerät, das hauptsächlich auf natürlichen Benutzereingaben basiert – im Vergleich zu dem, was auf einem Windows Mixed Reality-fähigen PC verfügbar ist.
* Sie können sich nicht darauf verlassen, dass Tastatur- oder Mauseingaben vorhanden sind. Alle Funktionen Ihrer App müssen mit Anvitäts-, Gesten- und Spracheingaben funktionieren.
* Wenn eine Bluetooth tastatur angefügt ist, kann es hilfreich sein, tastatureingaben für jeden Text zu aktivieren, den Ihre App möglicherweise anfragt. Dies kann z. B. eine hervorragende Ergänzung für das Diktat sein.
* Verlassen Sie sich beim Entwerfen Ihrer App nicht (z. B.) auf WASD- und Maus-Look-Steuerelemente für Ihr Spiel. HoloLens ist so konzipiert, dass der Benutzer durch den Raum geht. In diesem Fall steuert der Benutzer die Kamera direkt. Eine Schnittstelle zum Bewegen der Kamera im Raum mit Move/Look-Steuerelementen bietet nicht die gleiche Erfahrung.
* Tastatureingaben sind eine hervorragende Möglichkeit, das Debuggen Ihrer App oder Spiele-Engine zu steuern, insbesondere, da der Benutzer die Tastatur nicht verwenden muss. Die Verkabelung ist mit CoreWindow-Ereignis-APIs identisch wie gewohnt. In diesem Szenario können Sie eine Methode implementieren, um Ihre App so zu konfigurieren, dass Tastaturereignisse während Ihrer Debugsitzungen an den Modus "Nur Debugeingabe" geroutet werden.
* Bluetooth-Controller funktionieren auch.

## <a name="see-also"></a>Siehe auch
* [Hardware-Zubehör](../../discover/hardware-accessories.md)