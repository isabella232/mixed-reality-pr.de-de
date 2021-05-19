---
title: Mixed Reality-Tastatur
description: Beschreibung unter Verwenden der Mixed Reality-Tastatur
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 9fa81db9a71f1d0ce32bdd80a123eb072fc26fc5
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143390"
---
# <a name="mixed-reality-and-hololens-keyboard-helper-classes"></a>Mixed Reality und HoloLens-Tastatur-Hilfsklassen

MRTK stellt mehrere experimentelle Hilfskomponenten zum Starten und Lesen von Text von der [Systemtastatur zur Verfügung.](../ux-building-blocks/system-keyboard.md)

Beachten Sie, dass sich die Systemtastatur entsprechend den Funktionen der Zielplattform verhält, z. B. würde die Tastatur auf HoloLens 2 direkte Handinteraktionen unterstützen, während die Tastatur auf HoloLens (1. Generation) GGV<sup>[1 unterstützen](/windows/mixed-reality/gaze)</sup>würde. Darüber hinaus wird die Systemtastatur nicht angezeigt, wenn [Unity-Remoting](../tools/holographic-remoting.md) vom Editor zu einer HoloLens-Anwendung verwendet wird.

## <a name="mixedrealitykeyboard"></a>MixedRealityKeyboard

[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) ist eine Komponente, die Methoden zum Starten und Schließen einer Systemtastatur sowie zum Interagieren mit Text bietet, der von der Tastatur eingegeben wird.  

### <a name="how-to-use"></a>Verwendung

1. Fügen Sie die [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) Komponente an ein beliebiges Objekt an.
2. Rufen Sie auf, um die Tastatur ein- und auszublenden, und behandeln Sie die Ereignisse , und , die behandelt werden, wenn die Tastatur angezeigt, ausgeblendet und die EINGABETASTE `Show()` `Hide()` `OnShowKeyboard` `OnHideKeyboard` gedrückt `OnCommitText` wird.

## <a name="input-fields-tmp_keyboardinputfield-and-ui_keyboardinputfield"></a>Eingabefelder TMP_KeyboardInputField und UI_KeyboardInputField

Die Klassen und sind Komponenten, die Texteingabefeldern hinzugefügt werden können, um beim Klicken automatisch die Systemtastatur auf zu rufen und den Texteingabefeldinhalt zu aktualisieren, während der Benutzer [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) Text ein gibt.

### <a name="how-to-use"></a>Verwendung

1. Erstellen Sie ein Eingabefeld für UnityUI oder TextMeshPro.
2. Fügen Sie dem [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) Eingabefeldspielobjekt die entsprechende - oder -Komponente hinzu.

Prefabs für UnityUI-Eingabefelder und TextMeshPro-Eingabefelder (TMPro) sind unter "Assets\MRTK\Experimental\MixedRealityKeyboard\Prefabs" verfügbar.

Ein Beispiel für die Verwendung von TMP_KeyboardInputField und UI_KeyboardInputField finden Sie unter "Assets\MRTK\Examples\Experimental\MixedRealityKeyboard\Scenes\MixedRealityKeyboardExample.unity".