---
title: Systemtastatur
description: Übersicht über das Systemschlüsselboard in MRTK
author: maxwang-ms
ms.author: wangmax
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Systemtastatur,
ms.openlocfilehash: 4fc7023f6f39d9794011a09810e078f2ebbfc1c01c22e7003d5a3742e4c85921
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224736"
---
# <a name="system-keyboard"></a>Systemtastatur

![Systemtastatur](../images/system-keyboard/MRTK_SystemKeyboard_Main.png)

Eine Unity-Anwendung kann die Systemtastatur jederzeit aufrufen. Beachten Sie, dass sich die Systemtastatur entsprechend den Funktionen der Zielplattform verhält, z. B. würde die Tastatur auf HoloLens 2 direkte Handinteraktionen unterstützen, während die Tastatur auf HoloLens (1. Generation) GGV (Anvieren, Gesten und Stimme)<sup>[1 unterstützen würde.](/windows/mixed-reality/gaze)</sup> Darüber hinaus wird die Systemtastatur nicht angezeigt, wenn [Unity-Remoting](../tools/holographic-remoting.md) vom Editor zu einem HoloLens.

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

- [Mixed Reality Tastatur-Hilfsklassen](../experimental/mixed-reality-keyboard.md)
