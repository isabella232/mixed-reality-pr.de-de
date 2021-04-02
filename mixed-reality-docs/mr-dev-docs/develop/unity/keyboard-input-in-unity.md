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
# <a name="keyboard-input-in-unity"></a>Tastatureingabe in Unity

**Namespace:** *unityengine*<br>
 **Typ**: *[touchscreenkeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*

Obwohl hololens viele Formen von Eingaben einschließlich Bluetooth-Tastaturen unterstützt, können die meisten Anwendungen nicht davon ausgehen, dass für alle Benutzer eine physische Tastatur verfügbar ist. Wenn für Ihre Anwendung Texteingaben erforderlich sind, sollte eine Form der Bildschirmtastatur angegeben werden.

Unity stellt die *[touchscreenkeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* -Klasse bereit, um Tastatureingaben zu akzeptieren, wenn keine physische Tastatur verfügbar ist.

## <a name="hololens-system-keyboard-behavior-in-unity"></a>Hololens System Tastatur Verhalten in Unity

Auf hololens nutzt *touchscreenkeyboard* die Bildschirmtastatur des Systems und überlagert direkt über die volumetriansicht ihrer Mr-Anwendung. Die Vorgehensweise ähnelt der Verwendung von Tastatur in den integrierten Apps von hololens. Beachten Sie, dass sich die System Tastatur gemäß den Funktionen der Zielplattform verhält, z. b. wenn die Tastatur auf hololens 2 direkte Interaktionen unterstützt, während die Tastatur auf hololens (1st Gen) GGV unterstützen würde (Blick, Bewegung und Stimme). Außerdem wird die System Tastatur nicht angezeigt, wenn Unity-Remoting vom Editor zu einem hololens durchgeführt wird.

## <a name="using-the-system-keyboard-in-your-unity-app"></a>Verwenden der System Tastatur in ihrer Unity-App

### <a name="declare-the-keyboard"></a>Tastatur deklarieren

Deklarieren Sie in der-Klasse eine Variable zum Speichern der *touchscreenkeyboard* und eine Variable, um die von der Tastatur zurückgegebene Zeichenfolge zu speichern.

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a>Tastatur aufrufen

Wenn ein Ereignis beim Anfordern von Tastatureingaben auftritt, verwenden Sie Folgendes, um die Tastatur anzuzeigen.

```cs
keyboard = TouchScreenKeyboard.Open("text to edit");
```

Sie können zusätzliche Parameter verwenden, die an die Funktion weitergegeben werden `TouchScreenKeyboard.Open` , um das Verhalten der Tastatur zu steuern (z. b. das Festlegen von Platzhalter Text oder die Unterstützung der AutoKorrektur Die vollständige Liste der Parameter finden Sie in der [Unity-Dokumentation](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.Open.html).

### <a name="retrieve-typed-contents"></a>Abrufen von typisiertem Inhalt

Der Inhalt kann einfach durch Aufrufen von abgerufen werden `keyboard.text` . Möglicherweise möchten Sie den Inhalt pro Frame oder nur dann abrufen, wenn die Tastatur geschlossen wird.

```cs
keyboardText = keyboard.text;
```

## <a name="alternative-keyboard-options"></a>Alternative Tastatur Optionen

Wenn Sie die *touchscreenkeyboard* -Klasse direkt verwenden, können Sie auch Benutzereingaben über das Benutzeroberflächen- *Eingabefeld* von Unity oder das *Eingabefeld "textmeschpro*" erhalten. Außerdem gibt es eine auf *touchscreenkeyboard* basierende Implementierung in der [handinteraktionexamples-Szene](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples) von [mrtk](/windows/mixed-reality/mrtk-unity) (auf der linken Seite befindet sich ein Beispiel für eine Tastatur Interaktion).

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie der Unity-Entwicklungs Journey folgen, die wir gerade angelegt haben, sind Sie in der Mitte, die Funktionen und APIs der Mixed Reality-Plattform zu untersuchen. Von hier aus können Sie mit jedem [Thema](unity-development-overview.md#3-advanced-features) fortfahren oder direkt zum Bereitstellen Ihrer APP auf einem Gerät oder Emulator wechseln.

> [!div class="nextstepaction"]
> [Bereitstellung in hololens oder Windows Mixed Reality-immersiven Headsets](../platform-capabilities-and-apis/using-visual-studio.md)
