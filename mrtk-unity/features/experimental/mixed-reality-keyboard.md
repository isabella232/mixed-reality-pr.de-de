---
title: Mixed Reality-Tastatur
description: Beschreibung zur Verwendung der Mixed Reality-Tastatur
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 6a33ed5b021e90cba56344f32a9c9a33e8fcc476
ms.sourcegitcommit: c260aed8a37855faf9575d968e615959a56a13fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2021
ms.locfileid: "113466230"
---
# <a name="mixed-reality-and-hololens-keyboard-helper-classes"></a>Mixed Reality- und HoloLens-Tastaturhilfsklassen

MRTK bietet mehrere experimentelle Hilfskomponenten zum Starten und Lesen von Text über die [Systemtastatur.](../ux-building-blocks/system-keyboard.md)

Beachten Sie, dass sich die Systemtastatur gemäß den Funktionen der Zielplattform verhält, z. B. die Tastatur auf HoloLens 2 direkte Handinteraktionen unterstützen würde, während die Tastatur auf HoloLens (1. Generation) GGV<sup>[1](/windows/mixed-reality/gaze)</sup>unterstützt. Darüber hinaus wird die Systemtastatur nicht angezeigt, wenn [Unity-Remoting](../tools/holographic-remoting.md) vom Editor zu einem HoloLens ausgeführt wird.

## <a name="mixedrealitykeyboard"></a>MixedRealityKeyboard

[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) ist eine Komponente, die Methoden zum Starten und Schließen einer Systemtastatur sowie zum Interagieren mit Text bereitstellt, der von der Tastatur eingegeben wird.  

### <a name="how-to-use"></a>Verwendung

1. Fügen Sie die [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) Komponente an ein beliebiges Objekt an.
2. Rufen Sie auf, um die Tastatur ein- und auszublenden, und behandeln Sie die Ereignisse , und , die behandelt werden `ShowKeyboard(string text = "", bool multiLine = false)` `HideKeyboard()` `OnShowKeyboard` `OnHideKeyboard` `OnCommitText` sollen, wenn die Tastatur angezeigt, ausgeblendet und die EINGABETASTE gedrückt wird.

## <a name="input-fields-tmp_keyboardinputfield-and-ui_keyboardinputfield"></a>Eingabefelder TMP_KeyboardInputField und UI_KeyboardInputField

Die [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) Klassen und sind [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) Komponenten, die Texteingabefeldern hinzugefügt werden können, um automatisch die Systemtastatur aufzurufen, wenn darauf geklickt wird, und den Inhalt des Texteingabefelds zu aktualisieren, während der Benutzer Text eingibt.

### <a name="how-to-use"></a>Verwendung

1. Erstellen Sie ein Eingabefeld für UnityUI oder TextMeshPro.
2. Fügen Sie dem [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) Eingabefeldspielobjekt die entsprechende - oder [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) -Komponente hinzu.

Prefabs für UnityUI-Eingabefelder und TextMeshPro-Eingabefelder (TMPro) sind unter "Assets\MRTK\Experimental\MixedRealityKeyboard\Prefabs" verfügbar.

Ein Beispiel für die Verwendung von TMP_KeyboardInputField und UI_KeyboardInputField finden Sie unter "Assets\MRTK\Examples\Experimental\MixedRealityKeyboard\Scenes\MixedRealityKeyboardExample.unity".