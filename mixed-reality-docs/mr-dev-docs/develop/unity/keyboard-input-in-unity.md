---
title: Tastatureingabe in Unity
description: Unity stellt die touchscreenkeyboard-Klasse bereit, um Tastatureingaben zu akzeptieren, wenn keine physische Tastatur verfügbar ist.
author: MaxWang-MS
ms.author: wangmax
ms.date: 03/30/2021
ms.topic: article
keywords: Tastatur, Eingabe, Unity, touchscreenkeyboard, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, hololens 2
ms.openlocfilehash: 398a7c57dc701fc848fe9091949b45b2c1796987
ms.sourcegitcommit: e5bd72d8b92976a6590e0f59706a88e66374934c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/31/2021
ms.locfileid: "106098272"
---
# <a name="keyboard-input-in-unity"></a><span data-ttu-id="09623-104">Tastatureingabe in Unity</span><span class="sxs-lookup"><span data-stu-id="09623-104">Keyboard input in Unity</span></span>

<span data-ttu-id="09623-105">**Namespace:** *unityengine*</span><span class="sxs-lookup"><span data-stu-id="09623-105">**Namespace:** *UnityEngine*</span></span><br>
 <span data-ttu-id="09623-106">**Typ**: *[touchscreenkeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span><span class="sxs-lookup"><span data-stu-id="09623-106">**Type**: *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span></span>

<span data-ttu-id="09623-107">Obwohl hololens viele Formen von Eingaben einschließlich Bluetooth-Tastaturen unterstützt, können die meisten Anwendungen nicht davon ausgehen, dass für alle Benutzer eine physische Tastatur verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="09623-107">While HoloLens supports many forms of input including Bluetooth keyboards, most applications can't assume that all users will have a physical keyboard available.</span></span> <span data-ttu-id="09623-108">Wenn für Ihre Anwendung Texteingaben erforderlich sind, sollte eine Form der Bildschirmtastatur angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="09623-108">If your application requires text input, some form of on-screen keyboard should be provided.</span></span>

<span data-ttu-id="09623-109">Unity stellt die *[touchscreenkeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* -Klasse bereit, um Tastatureingaben zu akzeptieren, wenn keine physische Tastatur verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="09623-109">Unity provides the *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* class for accepting keyboard input when there's no physical keyboard available.</span></span>

## <a name="hololens-system-keyboard-behavior-in-unity"></a><span data-ttu-id="09623-110">Hololens System Tastatur Verhalten in Unity</span><span class="sxs-lookup"><span data-stu-id="09623-110">HoloLens system keyboard behavior in Unity</span></span>

<span data-ttu-id="09623-111">Auf hololens nutzt *touchscreenkeyboard* die Bildschirmtastatur des Systems und überlagert direkt über die volumetriansicht ihrer Mr-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="09623-111">On HoloLens, the *TouchScreenKeyboard* leverages the system's on-screen keyboard and directly overlays on top of the volumetric view of your MR application.</span></span> <span data-ttu-id="09623-112">Die Vorgehensweise ähnelt der Verwendung von Tastatur in den integrierten Apps von hololens.</span><span class="sxs-lookup"><span data-stu-id="09623-112">The experience is similar to using keyboard in the built-in apps of HoloLens.</span></span> <span data-ttu-id="09623-113">Beachten Sie, dass sich die System Tastatur gemäß den Funktionen der Zielplattform verhält, z. b. wenn die Tastatur auf hololens 2 direkte Interaktionen unterstützt, während die Tastatur auf hololens (1st Gen) GGV unterstützen würde (Blick, Bewegung und Stimme).</span><span class="sxs-lookup"><span data-stu-id="09623-113">Note that the system keyboard will behave according to the target platform's capabilities, for example the keyboard on HoloLens 2 would support direct hand interactions, while the keyboard on HoloLens (1st gen) would support GGV (Gaze, Gesture, and Voice).</span></span> <span data-ttu-id="09623-114">Außerdem wird die System Tastatur nicht angezeigt, wenn Unity-Remoting vom Editor zu einem hololens durchgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="09623-114">Additionally, the system keyboard will not show up when performing Unity Remoting from the editor to a HoloLens.</span></span>

## <a name="using-the-system-keyboard-in-your-unity-app"></a><span data-ttu-id="09623-115">Verwenden der System Tastatur in ihrer Unity-App</span><span class="sxs-lookup"><span data-stu-id="09623-115">Using the system keyboard in your Unity app</span></span>

### <a name="declare-the-keyboard"></a><span data-ttu-id="09623-116">Tastatur deklarieren</span><span class="sxs-lookup"><span data-stu-id="09623-116">Declare the keyboard</span></span>

<span data-ttu-id="09623-117">Deklarieren Sie in der-Klasse eine Variable zum Speichern der *touchscreenkeyboard* und eine Variable, um die von der Tastatur zurückgegebene Zeichenfolge zu speichern.</span><span class="sxs-lookup"><span data-stu-id="09623-117">In the class, declare a variable to store the *TouchScreenKeyboard* and a variable to hold the string the keyboard returns.</span></span>

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a><span data-ttu-id="09623-118">Tastatur aufrufen</span><span class="sxs-lookup"><span data-stu-id="09623-118">Invoke the keyboard</span></span>

<span data-ttu-id="09623-119">Wenn ein Ereignis beim Anfordern von Tastatureingaben auftritt, verwenden Sie Folgendes, um die Tastatur anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="09623-119">When an event occurs requesting keyboard input, use the following to show the keyboard.</span></span>

```cs
keyboard = TouchScreenKeyboard.Open("text to edit");
```

<span data-ttu-id="09623-120">Sie können zusätzliche Parameter verwenden, die an die Funktion weitergegeben werden `TouchScreenKeyboard.Open` , um das Verhalten der Tastatur zu steuern (z. b. das Festlegen von Platzhalter Text oder die Unterstützung der AutoKorrektur</span><span class="sxs-lookup"><span data-stu-id="09623-120">You can use additional parameters passed into the `TouchScreenKeyboard.Open` function to control the behavior of the keyboard (e.g. setting placeholder text or supporting autocorrection).</span></span> <span data-ttu-id="09623-121">Die vollständige Liste der Parameter finden Sie in der [Unity-Dokumentation](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.Open.html).</span><span class="sxs-lookup"><span data-stu-id="09623-121">For the full list of parameters please refer to [Unity's documentation](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.Open.html).</span></span>

### <a name="retrieve-typed-contents"></a><span data-ttu-id="09623-122">Abrufen von typisiertem Inhalt</span><span class="sxs-lookup"><span data-stu-id="09623-122">Retrieve typed contents</span></span>

<span data-ttu-id="09623-123">Der Inhalt kann einfach durch Aufrufen von abgerufen werden `keyboard.text` .</span><span class="sxs-lookup"><span data-stu-id="09623-123">The content can simply be retrieved by calling `keyboard.text`.</span></span> <span data-ttu-id="09623-124">Möglicherweise möchten Sie den Inhalt pro Frame oder nur dann abrufen, wenn die Tastatur geschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="09623-124">You may want to retrieve the content per frame or only when the keyboard is closed.</span></span>

```cs
keyboardText = keyboard.text;
```

## <a name="alternative-keyboard-options"></a><span data-ttu-id="09623-125">Alternative Tastatur Optionen</span><span class="sxs-lookup"><span data-stu-id="09623-125">Alternative keyboard options</span></span>

<span data-ttu-id="09623-126">Wenn Sie die *touchscreenkeyboard* -Klasse direkt verwenden, können Sie auch Benutzereingaben über das Benutzeroberflächen- *Eingabefeld* von Unity oder das *Eingabefeld "textmeschpro*" erhalten.</span><span class="sxs-lookup"><span data-stu-id="09623-126">Besides using the *TouchScreenKeyboard* class directly, you can also get user input by using Unity's *UI Input Field* or *TextMeshPro Input Field*.</span></span> <span data-ttu-id="09623-127">Außerdem gibt es eine auf *touchscreenkeyboard* basierende Implementierung in der [handinteraktionexamples-Szene](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples) von [mrtk](/windows/mixed-reality/mrtk-unity) (auf der linken Seite befindet sich ein Beispiel für eine Tastatur Interaktion).</span><span class="sxs-lookup"><span data-stu-id="09623-127">Additionally, there is an implementation based on *TouchScreenKeyboard* in the [HandInteractionExamples scene](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples) of [MRTK](/windows/mixed-reality/mrtk-unity) (there is a keyboard interaction sample on the left hand side).</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="09623-128">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="09623-128">Next Development Checkpoint</span></span>

<span data-ttu-id="09623-129">Wenn Sie der Unity-Entwicklungs Journey folgen, die wir gerade angelegt haben, sind Sie in der Mitte, die Funktionen und APIs der Mixed Reality-Plattform zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="09623-129">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="09623-130">Von hier aus können Sie mit jedem [Thema](unity-development-overview.md#3-advanced-features) fortfahren oder direkt zum Bereitstellen Ihrer APP auf einem Gerät oder Emulator wechseln.</span><span class="sxs-lookup"><span data-stu-id="09623-130">From here, you can continue to any [topic](unity-development-overview.md#3-advanced-features) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="09623-131">Bereitstellung in hololens oder Windows Mixed Reality-immersiven Headsets</span><span class="sxs-lookup"><span data-stu-id="09623-131">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)
