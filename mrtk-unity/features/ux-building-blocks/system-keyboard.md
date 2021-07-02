---
title: Systemtastatur
description: Übersicht über system key board in MRTK
author: maxwang-ms
ms.author: wangmax
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Systemtastatur,
ms.openlocfilehash: 9b1db512a1a4e27a2c41e8e8b5752200c461ee6e
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176488"
---
# <a name="system-keyboard"></a><span data-ttu-id="b8cc6-104">Systemtastatur</span><span class="sxs-lookup"><span data-stu-id="b8cc6-104">System keyboard</span></span>

![Systemtastatur](../images/system-keyboard/MRTK_SystemKeyboard_Main.png)

<span data-ttu-id="b8cc6-106">Eine Unity-Anwendung kann die Systemtastatur jederzeit aufrufen.</span><span class="sxs-lookup"><span data-stu-id="b8cc6-106">A Unity application can invoke the system keyboard at any time.</span></span> <span data-ttu-id="b8cc6-107">Beachten Sie, dass sich die Systemtastatur gemäß den Funktionen der Zielplattform verhält, z. B. die Tastatur auf HoloLens 2 direkte Handinteraktionen unterstützen würde, während die Tastatur auf HoloLens (1. Generation) GGV (Anvieren, Geste und Stimme)<sup>[1](/windows/mixed-reality/gaze)</sup>unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b8cc6-107">Note that the system keyboard will behave according to the target platform's capabilities, for example the keyboard on HoloLens 2 would support direct hand interactions, while the keyboard on HoloLens (1st gen) would support GGV (Gaze, Gesture, and Voice)<sup>[1](/windows/mixed-reality/gaze)</sup>.</span></span> <span data-ttu-id="b8cc6-108">Darüber hinaus wird die Systemtastatur nicht angezeigt, wenn [Unity-Remoting](../tools/holographic-remoting.md) vom Editor zu einem HoloLens ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="b8cc6-108">Additionally, the system keyboard will not show up when performing [Unity Remoting](../tools/holographic-remoting.md) from the editor to a HoloLens.</span></span>

## <a name="how-to-invoke-the-system-keyboard"></a><span data-ttu-id="b8cc6-109">Aufrufen der Systemtastatur</span><span class="sxs-lookup"><span data-stu-id="b8cc6-109">How to invoke the system keyboard</span></span>

```c#
public TouchScreenKeyboard keyboard;

...

public void OpenSystemKeyboard()
{
    keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);
}
```

## <a name="how-to-read-the-input"></a><span data-ttu-id="b8cc6-110">Lesen der Eingabe</span><span class="sxs-lookup"><span data-stu-id="b8cc6-110">How to read the input</span></span>

```c#
public TouchScreenKeyboard keyboard;

...

private void Update()
{
    if (keyboard != null)
    {
        keyboardText = keyboard.text;
        // Do stuff with keyboardText
    }
}
```

## <a name="system-keyboard-example"></a><span data-ttu-id="b8cc6-111">Beispiel für Systemtastatur</span><span class="sxs-lookup"><span data-stu-id="b8cc6-111">System keyboard example</span></span>

<span data-ttu-id="b8cc6-112">Sie sehen ein einfaches Beispiel für das Einrichten der Systemtastatur in `MixedRealityKeyboard.cs` (Assets/MRTK/SDK/Experimental/Features/UX/MixedRealityKeyboard.cs).</span><span class="sxs-lookup"><span data-stu-id="b8cc6-112">You can see a simple example of how to bring up system keyboard in `MixedRealityKeyboard.cs` (Assets/MRTK/SDK/Experimental/Features/UX/MixedRealityKeyboard.cs)</span></span>

## <a name="see-also"></a><span data-ttu-id="b8cc6-113">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b8cc6-113">See Also</span></span>

- [<span data-ttu-id="b8cc6-114">Mixed Reality-Tastaturhilfsklassen</span><span class="sxs-lookup"><span data-stu-id="b8cc6-114">Mixed Reality Keyboard Helper Classes</span></span>](../experimental/mixed-reality-keyboard.md)
