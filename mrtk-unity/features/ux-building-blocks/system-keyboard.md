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
# <a name="system-keyboard"></a>Systemtastatur

![Systemtastatur](../images/system-keyboard/MRTK_SystemKeyboard_Main.png)

Eine Unity-Anwendung kann die Systemtastatur jederzeit aufrufen. Beachten Sie, dass sich die Systemtastatur gemäß den Funktionen der Zielplattform verhält, z. B. die Tastatur auf HoloLens 2 direkte Handinteraktionen unterstützen würde, während die Tastatur auf HoloLens (1. Generation) GGV (Anvieren, Geste und Stimme)<sup>[1](/windows/mixed-reality/gaze)</sup>unterstützt. Darüber hinaus wird die Systemtastatur nicht angezeigt, wenn [Unity-Remoting](../tools/holographic-remoting.md) vom Editor zu einem HoloLens ausgeführt wird.

## <a name="how-to-invoke-the-system-keyboard"></a>Aufrufen der Systemtastatur

```c#
public TouchScreenKeyboard keyboard;

...

public void OpenSystemKeyboard()
{
    keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);
}
```

## <a name="how-to-read-the-input"></a>Lesen der Eingabe

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

## <a name="system-keyboard-example"></a>Beispiel für Systemtastatur

Sie sehen ein einfaches Beispiel für das Einrichten der Systemtastatur in `MixedRealityKeyboard.cs` (Assets/MRTK/SDK/Experimental/Features/UX/MixedRealityKeyboard.cs).

## <a name="see-also"></a>Weitere Informationen

- [Mixed Reality-Tastaturhilfsklassen](../experimental/mixed-reality-keyboard.md)
