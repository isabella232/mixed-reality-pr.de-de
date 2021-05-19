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
# <a name="mixed-reality-and-hololens-keyboard-helper-classes"></a><span data-ttu-id="77bdd-104">Mixed Reality und HoloLens-Tastatur-Hilfsklassen</span><span class="sxs-lookup"><span data-stu-id="77bdd-104">Mixed Reality and HoloLens Keyboard Helper Classes</span></span>

<span data-ttu-id="77bdd-105">MRTK stellt mehrere experimentelle Hilfskomponenten zum Starten und Lesen von Text von der [Systemtastatur zur Verfügung.](../ux-building-blocks/system-keyboard.md)</span><span class="sxs-lookup"><span data-stu-id="77bdd-105">MRTK provides several experimental helper components to assist with launching and reading text from the [System Keyboard](../ux-building-blocks/system-keyboard.md).</span></span>

<span data-ttu-id="77bdd-106">Beachten Sie, dass sich die Systemtastatur entsprechend den Funktionen der Zielplattform verhält, z. B. würde die Tastatur auf HoloLens 2 direkte Handinteraktionen unterstützen, während die Tastatur auf HoloLens (1. Generation) GGV<sup>[1 unterstützen](/windows/mixed-reality/gaze)</sup>würde.</span><span class="sxs-lookup"><span data-stu-id="77bdd-106">Note that the system keyboard will behave according to the target platform's capabilities, for example the keyboard on HoloLens 2 would support direct hand interactions, while the keyboard on HoloLens (1st gen) would support GGV<sup>[1](/windows/mixed-reality/gaze)</sup>.</span></span> <span data-ttu-id="77bdd-107">Darüber hinaus wird die Systemtastatur nicht angezeigt, wenn [Unity-Remoting](../tools/holographic-remoting.md) vom Editor zu einer HoloLens-Anwendung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="77bdd-107">Additionally, the system keyboard will not show up when performing [Unity Remoting](../tools/holographic-remoting.md) from the editor to a HoloLens.</span></span>

## <a name="mixedrealitykeyboard"></a><span data-ttu-id="77bdd-108">MixedRealityKeyboard</span><span class="sxs-lookup"><span data-stu-id="77bdd-108">MixedRealityKeyboard</span></span>

<span data-ttu-id="77bdd-109">[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) ist eine Komponente, die Methoden zum Starten und Schließen einer Systemtastatur sowie zum Interagieren mit Text bietet, der von der Tastatur eingegeben wird.</span><span class="sxs-lookup"><span data-stu-id="77bdd-109">[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) is a component that provides methods for launching and closing a system keyboard, as well as interacting with text entered by the keyboard.</span></span>  

### <a name="how-to-use"></a><span data-ttu-id="77bdd-110">Verwendung</span><span class="sxs-lookup"><span data-stu-id="77bdd-110">How to Use</span></span>

1. <span data-ttu-id="77bdd-111">Fügen Sie die [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) Komponente an ein beliebiges Objekt an.</span><span class="sxs-lookup"><span data-stu-id="77bdd-111">Attach the [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) component to any object.</span></span>
2. <span data-ttu-id="77bdd-112">Rufen Sie auf, um die Tastatur ein- und auszublenden, und behandeln Sie die Ereignisse , und , die behandelt werden, wenn die Tastatur angezeigt, ausgeblendet und die EINGABETASTE `Show()` `Hide()` `OnShowKeyboard` `OnHideKeyboard` gedrückt `OnCommitText` wird.</span><span class="sxs-lookup"><span data-stu-id="77bdd-112">Call `Show()` `Hide()` to show and hide the keyboard, and handle the `OnShowKeyboard`, `OnHideKeyboard` and `OnCommitText` events to handle when the keyboard is shown, hidden, and when the enter key is pressed.</span></span>

## <a name="input-fields-tmp_keyboardinputfield-and-ui_keyboardinputfield"></a><span data-ttu-id="77bdd-113">Eingabefelder TMP_KeyboardInputField und UI_KeyboardInputField</span><span class="sxs-lookup"><span data-stu-id="77bdd-113">Input fields TMP_KeyboardInputField, and UI_KeyboardInputField</span></span>

<span data-ttu-id="77bdd-114">Die Klassen und sind Komponenten, die Texteingabefeldern hinzugefügt werden können, um beim Klicken automatisch die Systemtastatur auf zu rufen und den Texteingabefeldinhalt zu aktualisieren, während der Benutzer [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) Text ein gibt.</span><span class="sxs-lookup"><span data-stu-id="77bdd-114">The [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) and [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) classes are components that can be added to text input fields to automatically invoke the system keyboard when clicked and update the text input field contents as the user enters text.</span></span>

### <a name="how-to-use"></a><span data-ttu-id="77bdd-115">Verwendung</span><span class="sxs-lookup"><span data-stu-id="77bdd-115">How to use</span></span>

1. <span data-ttu-id="77bdd-116">Erstellen Sie ein Eingabefeld für UnityUI oder TextMeshPro.</span><span class="sxs-lookup"><span data-stu-id="77bdd-116">Create an input field for either UnityUI or TextMeshPro.</span></span>
2. <span data-ttu-id="77bdd-117">Fügen Sie dem [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) Eingabefeldspielobjekt die entsprechende - oder -Komponente hinzu.</span><span class="sxs-lookup"><span data-stu-id="77bdd-117">Add the corresponding [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) or [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) component to the input field game object.</span></span>

<span data-ttu-id="77bdd-118">Prefabs für UnityUI-Eingabefelder und TextMeshPro-Eingabefelder (TMPro) sind unter "Assets\MRTK\Experimental\MixedRealityKeyboard\Prefabs" verfügbar.</span><span class="sxs-lookup"><span data-stu-id="77bdd-118">Prefabs for both UnityUI input fields and TextMeshPro (TMPro) input fields are available at "Assets\MRTK\Experimental\MixedRealityKeyboard\Prefabs"</span></span>

<span data-ttu-id="77bdd-119">Ein Beispiel für die Verwendung von TMP_KeyboardInputField und UI_KeyboardInputField finden Sie unter "Assets\MRTK\Examples\Experimental\MixedRealityKeyboard\Scenes\MixedRealityKeyboardExample.unity".</span><span class="sxs-lookup"><span data-stu-id="77bdd-119">An example of how the to use TMP_KeyboardInputField and UI_KeyboardInputField is at "Assets\MRTK\Examples\Experimental\MixedRealityKeyboard\Scenes\MixedRealityKeyboardExample.unity"</span></span>