---
title: Tastatureingabe in Unity
description: Unity stellt die TouchScreenKeyboard-Klasse zum Akzeptieren von Tastatureingaben bereit, wenn keine physische Tastatur verfügbar ist.
author: MaxWang-MS
ms.author: wangmax
ms.date: 03/30/2021
ms.topic: article
keywords: Tastatur, Eingabe, Unity, Touchscreenkeyboard, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens, HoloLens 2
ms.openlocfilehash: a7bd392036ca548fdd1f25581c8fc1910308909253f9c8df763e2039a32d3e9a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203852"
---
# <a name="keyboard-input-in-unity"></a>Tastatureingabe in Unity

**Namespace:** *UnityEngine*<br>
 **Typ:** *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*

Während HoloLens viele Eingabearten unterstützt, einschließlich Bluetooth Tastaturen, können die meisten Anwendungen nicht davon ausgehen, dass für alle Benutzer eine physische Tastatur verfügbar ist. Wenn Ihre Anwendung Texteingaben erfordert, sollte eine Form der Bildschirmtastatur bereitgestellt werden.

Unity stellt die *[TouchScreenKeyboard-Klasse](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* zum Akzeptieren von Tastatureingaben bereit, wenn keine physische Tastatur verfügbar ist.

## <a name="hololens-system-keyboard-behavior-in-unity"></a>HoloLens Systemtastaturverhalten in Unity

Auf HoloLens nutzt das *TouchScreenKeyboard* die Bildschirmtastatur des Systems und überlagert direkt die volumetrische Ansicht Ihrer MR-Anwendung. Die Benutzeroberfläche ähnelt der Verwendung der Tastatur in den integrierten Apps von HoloLens. Beachten Sie, dass sich die Systemtastatur gemäß den Funktionen der Zielplattform verhält, z. B. die Tastatur auf HoloLens 2 direkte Handinteraktionen unterstützen würde, während die Tastatur auf HoloLens (1. Generation) GGV (Anvieren, Gesten und Stimme) unterstützt. Darüber hinaus wird die Systemtastatur nicht angezeigt, wenn Unity-Remoting vom Editor zu einem HoloLens ausgeführt wird.

## <a name="using-the-system-keyboard-in-your-unity-app"></a>Verwenden der Systemtastatur in Ihrer Unity-App

### <a name="declare-the-keyboard"></a>Deklarieren der Tastatur

Deklarieren Sie in der -Klasse eine Variable zum Speichern des *TouchScreenKeyboard* und eine Variable zum Speichern der Zeichenfolge, die die Tastatur zurückgibt.

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a>Aufrufen der Tastatur

Wenn ein Ereignis auftritt, das eine Tastatureingabe anfordert, verwenden Sie Folgendes, um die Tastatur anzuzeigen.

```cs
keyboard = TouchScreenKeyboard.Open("text to edit");
```

Sie können zusätzliche Parameter verwenden, die an die Funktion übergeben `TouchScreenKeyboard.Open` werden, um das Verhalten der Tastatur zu steuern (z. B. Festlegen von Platzhaltertext oder Unterstützen der automatischen Korrektur). Die vollständige Liste der Parameter finden Sie in der [Unity-Dokumentation.](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.Open.html)

### <a name="retrieve-typed-contents"></a>Abrufen typisierter Inhalte

Der Inhalt kann einfach durch Aufrufen von abgerufen `keyboard.text` werden. Möglicherweise möchten Sie den Inhalt pro Frame oder nur abrufen, wenn die Tastatur geschlossen ist.

```cs
keyboardText = keyboard.text;
```

## <a name="alternative-keyboard-options"></a>Alternative Tastaturoptionen

Neben der direkten Verwendung der *TouchScreenKeyboard-Klasse* können Sie auch Benutzereingaben mithilfe des *Eingabefelds* der Benutzeroberfläche von Unity oder des *TextMeshPro-Eingabefelds* abrufen. Darüber hinaus gibt es eine Implementierung, die auf *TouchScreenKeyboard* in der [HandInteractionExamples-Szene](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples) von [MRTK](/windows/mixed-reality/mrtk-unity) basiert (auf der linken Seite befindet sich ein Beispiel für eine Tastaturinteraktion).

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie die von uns festgelegte Unity-Entwicklungsreise verfolgen, erkunden Sie die Funktionen und APIs der Mixed Reality Plattform. Von hier aus können Sie mit jedem [Thema](unity-development-overview.md#3-advanced-features) fortfahren oder direkt mit der Bereitstellung Ihrer App auf einem Gerät oder Emulator fortfahren.

> [!div class="nextstepaction"]
> [Bereitstellen auf HoloLens oder Windows Mixed Reality immersiven Headsets](../platform-capabilities-and-apis/using-visual-studio.md)
