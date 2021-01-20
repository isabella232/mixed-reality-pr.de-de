---
title: Tastatur-, Maus- und Controllereingaben in DirectX
description: Erläutert das Erstellen einer APP für Windows Mixed Reality, in der Tastatur-, Maus-und Spielcontroller verwendet werden.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, Tastatur, Maus, Game Controller, Xbox Controller, hololens, Desktop, Exemplarische Vorgehensweise, Beispielcode
ms.openlocfilehash: 3cf35ba195e839332cbedb8b2c3945334a158cbc
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583638"
---
# <a name="keyboard-mouse-and-controller-input-in-directx"></a><span data-ttu-id="8270c-104">Tastatur-, Maus- und Controllereingaben in DirectX</span><span class="sxs-lookup"><span data-stu-id="8270c-104">Keyboard, mouse, and controller input in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="8270c-105">Dieser Artikel bezieht sich auf die älteren WinRT-APIs.</span><span class="sxs-lookup"><span data-stu-id="8270c-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="8270c-106">Bei neuen nativen App-Projekten wird die Verwendung der **[openxr-API](../native/openxr-getting-started.md)** empfohlen.</span><span class="sxs-lookup"><span data-stu-id="8270c-106">For new native app projects, we recommend using the **[OpenXR API](../native/openxr-getting-started.md)**.</span></span>

<span data-ttu-id="8270c-107">Tastaturen, Mäuse und Spielcontroller können als nützliche Formen der Eingabe für Windows Mixed Reality-Geräte dienen.</span><span class="sxs-lookup"><span data-stu-id="8270c-107">Keyboards, mice, and game controllers can all be useful forms of input for Windows Mixed Reality devices.</span></span> <span data-ttu-id="8270c-108">Bluetooth-Tastaturen und-Mäuse werden sowohl in hololens unterstützt als auch beim Debuggen Ihrer APP oder als Alternative Form der Eingabe.</span><span class="sxs-lookup"><span data-stu-id="8270c-108">Bluetooth keyboards and mice are both supported on HoloLens, for use with debugging your app or as an alternate form of input.</span></span> <span data-ttu-id="8270c-109">Windows Mixed Reality unterstützt auch immersive Headsets, die an PCs angeschlossen sind, bei denen Mäuse, Tastaturen und Spielcontroller in der Vergangenheit die Norm waren.</span><span class="sxs-lookup"><span data-stu-id="8270c-109">Windows Mixed Reality also supports immersive headsets attached to PCs - where mice, keyboards, and game controllers have historically been the norm.</span></span>

<span data-ttu-id="8270c-110">Um Tastatureingaben in hololens zu verwenden, koppeln Sie eine Bluetooth-Tastatur mit Ihrem Gerät, oder verwenden Sie die virtuelle Eingabe über das Windows-Geräte Portal.</span><span class="sxs-lookup"><span data-stu-id="8270c-110">To use keyboard input on HoloLens, pair a Bluetooth keyboard to your device or use virtual input via the Windows Device Portal.</span></span> <span data-ttu-id="8270c-111">Wenn Sie Tastatureingaben beim Durchführen eines Windows Mixed Reality-immersiven Headsets verwenden möchten, weisen Sie der gemischten Realität den Eingabefokus zu, indem Sie das Gerät platzieren oder die Tastenkombination Windows-Taste + Y verwenden.</span><span class="sxs-lookup"><span data-stu-id="8270c-111">To use keyboard input while wearing a Windows Mixed Reality immersive headset, assign input focus to mixed reality by putting on the device or using the Windows Key + Y keyboard combination.</span></span> <span data-ttu-id="8270c-112">Beachten Sie, dass apps, die für hololens vorgesehen sind, Funktionen ohne angehängte Geräte bereitstellen müssen.</span><span class="sxs-lookup"><span data-stu-id="8270c-112">Keep in mind that apps intended for HoloLens must provide functionality without these devices attached.</span></span>

>[!NOTE]
><span data-ttu-id="8270c-113">Die Code Ausschnitte in diesem Artikel veranschaulichen derzeit die Verwendung von C++/CX anstelle von C + +17-kompatiblen C++/WinRT, wie Sie in der [C++ Holographic-Projektvorlage](../native/creating-a-holographic-directx-project.md)verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="8270c-113">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](../native/creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="8270c-114">Die Konzepte sind äquivalent zu einem C++/WinRT-Projekt. Sie müssen jedoch den Code übersetzen.</span><span class="sxs-lookup"><span data-stu-id="8270c-114">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="subscribe-for-corewindow-input-events"></a><span data-ttu-id="8270c-115">Abonnieren von corewindow-Eingabe Ereignissen</span><span class="sxs-lookup"><span data-stu-id="8270c-115">Subscribe for CoreWindow input events</span></span>

### <a name="keyboard-input"></a><span data-ttu-id="8270c-116">Tastatureingabe</span><span class="sxs-lookup"><span data-stu-id="8270c-116">Keyboard input</span></span>

<span data-ttu-id="8270c-117">In der Windows Holographic-App-Vorlage fügen wir einen Ereignishandler für Tastatureingaben wie jede andere UWP-App ein.</span><span class="sxs-lookup"><span data-stu-id="8270c-117">In the Windows Holographic app template, we include an event handler for keyboard input just like any other UWP app.</span></span> <span data-ttu-id="8270c-118">Ihre APP beansprucht Tastatureingabe Daten in Windows Mixed Reality auf dieselbe Weise.</span><span class="sxs-lookup"><span data-stu-id="8270c-118">Your app consumes keyboard input data the same way in Windows Mixed Reality.</span></span>

<span data-ttu-id="8270c-119">Aus appview. cpp:</span><span class="sxs-lookup"><span data-stu-id="8270c-119">From AppView.cpp:</span></span>

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

### <a name="virtual-keyboard-input"></a><span data-ttu-id="8270c-120">Virtuelle Tastatureingabe</span><span class="sxs-lookup"><span data-stu-id="8270c-120">Virtual keyboard input</span></span>
<span data-ttu-id="8270c-121">Bei immersiven Desktop-Headsets können Sie durch die Implementierung von **coretexteditcontext** virtuelle Tastaturen, die von Windows gerendert werden, in ihrer immersiven Ansicht unterstützen.</span><span class="sxs-lookup"><span data-stu-id="8270c-121">For immersive desktop headsets, you can support virtual keyboards rendered by Windows over your immersive view by implementing **CoreTextEditContext**.</span></span> <span data-ttu-id="8270c-122">Dadurch kann Windows den Zustand ihrer eigenen, von der APP gerenderten Textfelder verstehen, sodass die virtuelle Tastatur ordnungsgemäß zum Text beitragen kann.</span><span class="sxs-lookup"><span data-stu-id="8270c-122">This lets Windows understand the state of your own app-rendered text boxes, so the virtual keyboard can correctly contribute to the text there.</span></span>

<span data-ttu-id="8270c-123">Weitere Informationen zum Implementieren der coretexteditcontext-Unterstützung finden Sie im [coretexteditcontext-Beispiel](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span><span class="sxs-lookup"><span data-stu-id="8270c-123">For more information on implementing CoreTextEditContext support, see the [CoreTextEditContext sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/CustomEditControl).</span></span>

### <a name="mouse-input"></a><span data-ttu-id="8270c-124">Mauseingabe</span><span class="sxs-lookup"><span data-stu-id="8270c-124">Mouse Input</span></span>

<span data-ttu-id="8270c-125">Sie können auch über die Eingabe Ereignishandler von UWP corewindow auch Maus Eingaben verwenden.</span><span class="sxs-lookup"><span data-stu-id="8270c-125">You can also use mouse input, again via the UWP CoreWindow input event handlers.</span></span> <span data-ttu-id="8270c-126">Im folgenden wird erläutert, wie Sie die Windows Holographic-App-Vorlage ändern, um Mausklicks auf die gleiche Weise wie gedrückte Gesten zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="8270c-126">Here's how to modify the Windows Holographic app template to support mouse clicks in the same way as pressed gestures.</span></span> <span data-ttu-id="8270c-127">Nachdem Sie diese Änderung vorgenommen haben, wird der Cube durch einen Mausklick beim Ausführen eines immersiven Headset-Geräts neu positioniert.</span><span class="sxs-lookup"><span data-stu-id="8270c-127">After making this modification, a mouse click while wearing an immersive headset device will reposition the cube.</span></span>

> [!NOTE]
> <span data-ttu-id="8270c-128">UWP-Apps können auch unformatierte XY-Daten für die Maus mit der [MouseDevice](/uwp/api/Windows.Devices.Input.MouseDevice) -API erhalten.</span><span class="sxs-lookup"><span data-stu-id="8270c-128">UWP apps can also get raw XY data for the mouse by using the [MouseDevice](/uwp/api/Windows.Devices.Input.MouseDevice) API.</span></span>

<span data-ttu-id="8270c-129">Beginnen Sie mit dem Deklarieren eines neuen onpointerpressed-Handlers in appview. h:</span><span class="sxs-lookup"><span data-stu-id="8270c-129">Start by declaring a new OnPointerPressed handler in AppView.h:</span></span>

```
protected:
       void OnPointerPressed(Windows::UI::Core::CoreWindow^ sender, Windows::UI::Core::PointerEventArgs^ args);
```

<span data-ttu-id="8270c-130">Fügen Sie in appview. cpp den folgenden Code zu SetWindow hinzu:</span><span class="sxs-lookup"><span data-stu-id="8270c-130">In AppView.cpp, add this code to SetWindow:</span></span>

```
// Register for pointer pressed notifications.
   window->PointerPressed +=
       ref new TypedEventHandler<CoreWindow^, PointerEventArgs^>(this, &AppView::OnPointerPressed);
```

<span data-ttu-id="8270c-131">Fügen Sie dann diese Definition für "onpointerpressed" am Ende der Datei ein:</span><span class="sxs-lookup"><span data-stu-id="8270c-131">Then put this definition for OnPointerPressed at the bottom of the file:</span></span>

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

<span data-ttu-id="8270c-132">Der soeben hinzugefügte Ereignishandler ist eine Pass-Through-Funktion für die Hauptklasse der Vorlage.</span><span class="sxs-lookup"><span data-stu-id="8270c-132">The event handler we just added is a pass-through to the template main class.</span></span> <span data-ttu-id="8270c-133">Ändern wir nun die Hauptklasse, um diese Pass-Through-Unterstützung zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="8270c-133">Let's modify the main class to support this pass-through.</span></span> <span data-ttu-id="8270c-134">Fügen Sie diese Deklaration der öffentlichen Methode der Header Datei hinzu:</span><span class="sxs-lookup"><span data-stu-id="8270c-134">Add this public method declaration to the header file:</span></span>

```
// Handle mouse input.
       void OnPointerPressed();
```

<span data-ttu-id="8270c-135">Sie benötigen auch diese private Member-Variable:</span><span class="sxs-lookup"><span data-stu-id="8270c-135">You'll need this private member variable, as well:</span></span>

```
// Keep track of mouse input.
       bool m_pointerPressed = false;
```

<span data-ttu-id="8270c-136">Zum Schluss aktualisieren wir die Hauptklasse mit neuer Logik zur Unterstützung von Mausklicks.</span><span class="sxs-lookup"><span data-stu-id="8270c-136">Finally, we'll update the main class with new logic to support mouse clicks.</span></span> <span data-ttu-id="8270c-137">Beginnen Sie mit dem Hinzufügen dieses Ereignis Handlers.</span><span class="sxs-lookup"><span data-stu-id="8270c-137">Start by adding this event handler.</span></span> <span data-ttu-id="8270c-138">Stellen Sie sicher, dass Sie den Klassennamen aktualisieren:</span><span class="sxs-lookup"><span data-stu-id="8270c-138">Make sure to update the class name:</span></span>

```
void MyHolographicAppMain::OnPointerPressed()
   {
       m_pointerPressed = true;
   }
```

<span data-ttu-id="8270c-139">Ersetzen Sie nun in der Update-Methode die vorhandene Logik, um eine Zeiger Pose mit folgenden Informationen zu erhalten:</span><span class="sxs-lookup"><span data-stu-id="8270c-139">Now, in the Update method, replace the existing logic for getting a pointer pose with this:</span></span>

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

<span data-ttu-id="8270c-140">Neukompilieren und erneut bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="8270c-140">Recompile and redeploy.</span></span> <span data-ttu-id="8270c-141">Beachten Sie, dass mit dem Maus Klick nun der Cube in Ihrem immersiven Headset oder hololens mit der Bluetooth-Maus angefügt wird.</span><span class="sxs-lookup"><span data-stu-id="8270c-141">Notice that the mouse click will now reposition the cube in your immersive headset - or HoloLens with bluetooth mouse attached.</span></span>

### <a name="game-controller-support"></a><span data-ttu-id="8270c-142">Spiele Controller Unterstützung</span><span class="sxs-lookup"><span data-stu-id="8270c-142">Game controller support</span></span>

<span data-ttu-id="8270c-143">Spiele Controller können eine angenehme und bequeme Möglichkeit bieten, dem Benutzer zu ermöglichen, eine immersive Windows Mixed Reality-Darstellung zu steuern.</span><span class="sxs-lookup"><span data-stu-id="8270c-143">Game controllers can be a fun and convenient way of allowing the user to control an immersive Windows Mixed Reality experience.</span></span>

 <span data-ttu-id="8270c-144">Fügen Sie der Header Klasse für Ihre Hauptdatei die folgenden privaten Member-Deklarationen hinzu:</span><span class="sxs-lookup"><span data-stu-id="8270c-144">add the following private member declarations to the header class for your main file:</span></span>

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

<span data-ttu-id="8270c-145">Initialisieren Sie Gamepad-Ereignisse und alle derzeit angefügten Gamepads im Konstruktor für Ihre Hauptklasse:</span><span class="sxs-lookup"><span data-stu-id="8270c-145">Initialize gamepad events, and any gamepads that are currently attached, in the constructor for your main class:</span></span>

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

<span data-ttu-id="8270c-146">Fügen Sie diese Ereignishandler ihrer Hauptklasse hinzu.</span><span class="sxs-lookup"><span data-stu-id="8270c-146">Add these event handlers to your main class.</span></span> <span data-ttu-id="8270c-147">Stellen Sie sicher, dass Sie den Klassennamen aktualisieren:</span><span class="sxs-lookup"><span data-stu-id="8270c-147">Make sure to update the class name:</span></span>

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

<span data-ttu-id="8270c-148">Aktualisieren Sie schließlich die Eingabe Logik, um Änderungen im Controller Zustand zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="8270c-148">Finally, update the input logic to recognize changes in controller state.</span></span> <span data-ttu-id="8270c-149">Hier verwenden wir die gleiche m_pointerPressed Variable, die im obigen Abschnitt zum Hinzufügen von Mausereignissen erläutert wurde.</span><span class="sxs-lookup"><span data-stu-id="8270c-149">Here, we use the same m_pointerPressed variable discussed in the section above for adding mouse events.</span></span> <span data-ttu-id="8270c-150">Fügen Sie diese der Update-Methode hinzu, kurz bevor Sie die Anwendung auf spatialpointerpose überprüft:</span><span class="sxs-lookup"><span data-stu-id="8270c-150">Add this to the Update method, just before where it checks for the SpatialPointerPose:</span></span>

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

<span data-ttu-id="8270c-151">Vergessen Sie nicht, die Registrierung der Ereignisse beim Bereinigen der Hauptklasse aufzuheben:</span><span class="sxs-lookup"><span data-stu-id="8270c-151">Don't forget to unregister the events when cleaning up the main class:</span></span>

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

<span data-ttu-id="8270c-152">Neukompilieren und erneut bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="8270c-152">Recompile, and redeploy.</span></span> <span data-ttu-id="8270c-153">Sie können jetzt einen Spielcontroller anfügen oder koppeln und ihn verwenden, um den drehenden Cube neu zu positionieren.</span><span class="sxs-lookup"><span data-stu-id="8270c-153">You can now attach, or pair, a game controller and use it to reposition the spinning cube.</span></span>

## <a name="important-guidelines-for-keyboard-and-mouse-input"></a><span data-ttu-id="8270c-154">Wichtige Richtlinien für Tastatur-und Maus Eingaben</span><span class="sxs-lookup"><span data-stu-id="8270c-154">Important guidelines for keyboard and mouse input</span></span>

<span data-ttu-id="8270c-155">Es gibt einige wichtige Unterschiede bei der Verwendung dieses Codes für Microsoft hololens – bei dem es sich um ein Gerät handelt, das hauptsächlich auf natürlichen Benutzereingaben basiert – im Vergleich zu den Funktionen, die auf einem Windows Mixed Reality-fähigen PC verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="8270c-155">There are some key differences in how this code can be used on Microsoft HoloLens – which is a device that relies primarily on natural user input – versus what is available on a Windows Mixed Reality-enabled PC.</span></span>
* <span data-ttu-id="8270c-156">Sie können sich nicht darauf verlassen, dass Tastatur-oder Maus Eingaben vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="8270c-156">You can’t rely on keyboard or mouse input to be present.</span></span> <span data-ttu-id="8270c-157">Alle Funktionen Ihrer APP müssen mit Blick, Gesten und Spracheingaben funktionieren.</span><span class="sxs-lookup"><span data-stu-id="8270c-157">All of your app's functionality must work with gaze, gesture, and speech input.</span></span>
* <span data-ttu-id="8270c-158">Wenn eine Bluetooth-Tastatur angefügt wird, kann es hilfreich sein, Tastatureingaben für jeden Text zu aktivieren, der von Ihrer APP angefordert werden kann.</span><span class="sxs-lookup"><span data-stu-id="8270c-158">When a Bluetooth keyboard is attached, it can be helpful to enable keyboard input for any text that your app might ask for.</span></span> <span data-ttu-id="8270c-159">Dies kann z. b. eine hervor artige Ergänzung zum Diktat darstellen.</span><span class="sxs-lookup"><span data-stu-id="8270c-159">This can be a great supplement for dictation, for example.</span></span>
* <span data-ttu-id="8270c-160">Wenn Sie Ihre APP entwerfen möchten, verlassen Sie sich nicht auf (z. b.) WASD-und Mauszeiger-Steuerelemente für Ihr Spiel.</span><span class="sxs-lookup"><span data-stu-id="8270c-160">When it comes to designing your app, don’t rely on (for example) WASD and mouse look controls for your game.</span></span> <span data-ttu-id="8270c-161">Hololens ist dafür konzipiert, dass der Benutzer den Raum durchläuft.</span><span class="sxs-lookup"><span data-stu-id="8270c-161">HoloLens is designed for the user to walk around the room.</span></span> <span data-ttu-id="8270c-162">In diesem Fall steuert der Benutzer die Kamera direkt.</span><span class="sxs-lookup"><span data-stu-id="8270c-162">In this case, the user controls the camera directly.</span></span> <span data-ttu-id="8270c-163">Eine Schnittstelle zum Steuern der Kamera um den Raum mit Verschiebe-und Bild-Steuerelementen bietet nicht die gleiche Umgebung.</span><span class="sxs-lookup"><span data-stu-id="8270c-163">An interface for driving the camera around the room with move/look controls won't provide the same experience.</span></span>
* <span data-ttu-id="8270c-164">Tastatureingaben sind eine hervorragende Möglichkeit, um das Debuggen Ihrer APP-oder Spiel-Engine zu steuern, insbesondere, da der Benutzer die Tastatur nicht verwenden muss.</span><span class="sxs-lookup"><span data-stu-id="8270c-164">Keyboard input is an excellent way to control your app or game engine debugging, especially since the user won't be required to use the keyboard.</span></span> <span data-ttu-id="8270c-165">Die Verknüpfung ist identisch mit der Verwendung von corewindow-Ereignis-APIs.</span><span class="sxs-lookup"><span data-stu-id="8270c-165">Wiring it up is the same as you're used to, with CoreWindow event APIs.</span></span> <span data-ttu-id="8270c-166">In diesem Szenario können Sie eine Möglichkeit implementieren, um Ihre APP so zu konfigurieren, dass Tastatur Ereignisse während der Debugsitzungen an den Modus "nur debugeingabe" weitergeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="8270c-166">In this scenario, you might choose to implement a way to configure your app to route keyboard events to a "debug input only" mode during your debug sessions.</span></span>
* <span data-ttu-id="8270c-167">Bluetooth-Controller sind ebenfalls funktionsfähig.</span><span class="sxs-lookup"><span data-stu-id="8270c-167">Bluetooth controllers work as well.</span></span>

## <a name="see-also"></a><span data-ttu-id="8270c-168">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="8270c-168">See also</span></span>
* [<span data-ttu-id="8270c-169">Hardware-Zubehör</span><span class="sxs-lookup"><span data-stu-id="8270c-169">Hardware accessories</span></span>](../../discover/hardware-accessories.md)