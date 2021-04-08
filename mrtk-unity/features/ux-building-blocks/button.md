---
title: Schaltflächen
description: Übersicht über Schaltflächen in mrtk
author: cre8ivepark
ms.author: dongpark
ms.date: 01/12/2021
keywords: Unity, hololens, hololens 2, Mixed Reality, Development, mrtk, mrtk-Schaltflächen
ms.openlocfilehash: 43570c225f25b9ea73c9d1fc4cc9b6c92b8c2dfc
ms.sourcegitcommit: 848b4b7bb8514c2e088a3a55512b1a8075d29093
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/07/2021
ms.locfileid: "107003109"
---
# <a name="button"></a><span data-ttu-id="57994-104">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="57994-104">Button</span></span>

![Schaltfläche Main](../images/button/MRTK_Button_Main.png)

<span data-ttu-id="57994-106">Eine Schaltfläche ermöglicht dem Benutzer das unmittelbare Auslösen einer Aktion.</span><span class="sxs-lookup"><span data-stu-id="57994-106">A button gives the user a way to trigger an immediate action.</span></span> <span data-ttu-id="57994-107">Es ist eine der grundlegenden Komponenten in gemischter Realität.</span><span class="sxs-lookup"><span data-stu-id="57994-107">It is one of the most foundational components in mixed reality.</span></span> <span data-ttu-id="57994-108">Mrtk bietet verschiedene Typen von Schaltflächen-Prefabs.</span><span class="sxs-lookup"><span data-stu-id="57994-108">MRTK provides various types of button prefabs.</span></span>

## <a name="button-prefabs-in-mrtk"></a><span data-ttu-id="57994-109">Schaltfläche "Prefabs" in mrtk</span><span class="sxs-lookup"><span data-stu-id="57994-109">Button prefabs in MRTK</span></span>

<span data-ttu-id="57994-110">Beispiele für die Schaltflächen "Prefabs" unter " ``MRTK/SDK/Features/UX/Interactable/Prefabs`` Folder"</span><span class="sxs-lookup"><span data-stu-id="57994-110">Examples of the button prefabs under ``MRTK/SDK/Features/UX/Interactable/Prefabs`` folder</span></span>

### <a name="unity-ui-imagegraphic-based-buttons"></a><span data-ttu-id="57994-111">Unity-Benutzeroberflächen Bild/Grafik basierte Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="57994-111">Unity UI Image/Graphic based buttons</span></span>

* `UnityUIInteractableButton.prefab`
* `PressableButtonUnityUI.prefab`
* `PressableButtonUnityUICircular.prefab`
* `PressableButtonHoloLens2UnityUI.prefab`

### <a name="collider-based-buttons"></a><span data-ttu-id="57994-112">Auf Collider basierende Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="57994-112">Collider based buttons</span></span>

:::row:::
    :::column:::
    ![PressableButtonHoloLens2](../images/button/MRTK_Button_Prefabs_HoloLens2.png) <span data-ttu-id="57994-114">PressableButtonHoloLens2</span><span class="sxs-lookup"><span data-stu-id="57994-114">PressableButtonHoloLens2</span></span> 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Unplated](../images/button/MRTK_Button_Prefabs_HoloLens2Unplated.png) <span data-ttu-id="57994-116">PressableButtonHoloLens2Unplated</span><span class="sxs-lookup"><span data-stu-id="57994-116">PressableButtonHoloLens2Unplated</span></span> 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Circular](../images/button/MRTK_Button_Prefabs_HoloLens2Circular.png) <span data-ttu-id="57994-118">PressableButtonHoloLens2Circular</span><span class="sxs-lookup"><span data-stu-id="57994-118">PressableButtonHoloLens2Circular</span></span> 
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    <span data-ttu-id="57994-119">Die shellstil-Schaltfläche von hololens 2 mit Backplate, die verschiedene visuelle Feedback wie Border Light, near Light und Compressed Front Plate unterstützt.</span><span class="sxs-lookup"><span data-stu-id="57994-119">HoloLens 2's shell-style button with backplate which supports various visual feedback such as border light, proximity light, and compressed front plate</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="57994-120">Schaltfläche im shellstil von hololens 2 ohne Backplate</span><span class="sxs-lookup"><span data-stu-id="57994-120">HoloLens 2's shell-style button without backplate</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="57994-121">Schaltfläche im shellstil von hololens 2 mit Zirkel Form</span><span class="sxs-lookup"><span data-stu-id="57994-121">HoloLens 2's shell-style button with circular shape</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    <span data-ttu-id="57994-122">![PressableButtonHoloLens2_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_32x96.png) **PressableButtonHoloLens2_32x96**</span><span class="sxs-lookup"><span data-stu-id="57994-122">![PressableButtonHoloLens2_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_32x96.png) **PressableButtonHoloLens2_32x96**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="57994-123">![PressableButtonHoloLens2Bar3H ](../images/button/MRTK_Button_Prefabs_HoloLens2BarH.png) **PressableButtonHoloLens2Bar3H**</span><span class="sxs-lookup"><span data-stu-id="57994-123">![PressableButtonHoloLens2Bar3H](../images/button/MRTK_Button_Prefabs_HoloLens2BarH.png) **PressableButtonHoloLens2Bar3H**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="57994-124">![PressableButtonHoloLens2Bar3V ](../images/button/MRTK_Button_Prefabs_HoloLens2BarV.png) **PressableButtonHoloLens2Bar3V**</span><span class="sxs-lookup"><span data-stu-id="57994-124">![PressableButtonHoloLens2Bar3V](../images/button/MRTK_Button_Prefabs_HoloLens2BarV.png) **PressableButtonHoloLens2Bar3V**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    <span data-ttu-id="57994-125">Shell-Stil-Schaltfläche "Wide hololens 2", 32 x 96mm</span><span class="sxs-lookup"><span data-stu-id="57994-125">Wide HoloLens 2's shell-style button 32x96mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="57994-126">Horizontale hololens 2-Schaltflächen Leiste mit frei gegebener Backplate</span><span class="sxs-lookup"><span data-stu-id="57994-126">Horizontal HoloLens 2 button bar with shared backplate</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="57994-127">Vertikale hololens 2-Schaltflächen Leiste mit frei gegebener Backplate</span><span class="sxs-lookup"><span data-stu-id="57994-127">Vertical HoloLens 2 button bar with shared backplate</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    <span data-ttu-id="57994-128">![PressableButtonHoloLens2ToggleCheckBox_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox.png) **PressableButtonHoloLens2ToggleCheckBox_32x32**</span><span class="sxs-lookup"><span data-stu-id="57994-128">![PressableButtonHoloLens2ToggleCheckBox_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox.png) **PressableButtonHoloLens2ToggleCheckBox_32x32**</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="57994-129">![PressableButtonHoloLens2ToggleSwitch_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch.png) **PressableButtonHoloLens2ToggleSwitch_32x32**</span><span class="sxs-lookup"><span data-stu-id="57994-129">![PressableButtonHoloLens2ToggleSwitch_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch.png) **PressableButtonHoloLens2ToggleSwitch_32x32**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="57994-130">![PressableButtonHoloLens2ToggleRadio_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio.png) **PressableButtonHoloLens2ToggleRadio_32x32**</span><span class="sxs-lookup"><span data-stu-id="57994-130">![PressableButtonHoloLens2ToggleRadio_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio.png) **PressableButtonHoloLens2ToggleRadio_32x32**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    <span data-ttu-id="57994-131">Kontrollkästchen für das shellformat von hololens 2 im shellstil 32x32mm</span><span class="sxs-lookup"><span data-stu-id="57994-131">HoloLens 2's shell-style checkbox 32x32mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="57994-132">Shellstil-Switch von hololens 2 32x32mm</span><span class="sxs-lookup"><span data-stu-id="57994-132">HoloLens 2's shell-style switch 32x32mm</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="57994-133">"Hololens 2" im shellstil "Radio 32x32mm"</span><span class="sxs-lookup"><span data-stu-id="57994-133">HoloLens 2's shell-style radio 32x32mm</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    <span data-ttu-id="57994-134">![PressableButtonHoloLens2ToggleCheckBox_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox_32x96.png) **PressableButtonHoloLens2ToggleCheckBox_32x96**</span><span class="sxs-lookup"><span data-stu-id="57994-134">![PressableButtonHoloLens2ToggleCheckBox_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox_32x96.png) **PressableButtonHoloLens2ToggleCheckBox_32x96**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="57994-135">![PressableButtonHoloLens2ToggleSwitch_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch_32x96.png) **PressableButtonHoloLens2ToggleSwitch_32x96**</span><span class="sxs-lookup"><span data-stu-id="57994-135">![PressableButtonHoloLens2ToggleSwitch_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch_32x96.png) **PressableButtonHoloLens2ToggleSwitch_32x96**</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="57994-136">![PressableButtonHoloLens2ToggleRadio_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio_32x96.png) **PressableButtonHoloLens2ToggleRadio_32x96**</span><span class="sxs-lookup"><span data-stu-id="57994-136">![PressableButtonHoloLens2ToggleRadio_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio_32x96.png) **PressableButtonHoloLens2ToggleRadio_32x96**</span></span> 
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="57994-137">Kontrollkästchen für das Shell-Format von hololens 2 im shellstil 32x96mm</span><span class="sxs-lookup"><span data-stu-id="57994-137">HoloLens 2's shell-style checkbox 32x96mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="57994-138">Shellstil-Switch von hololens 2 32x96mm</span><span class="sxs-lookup"><span data-stu-id="57994-138">HoloLens 2's shell-style switch 32x96mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="57994-139">Im shellstil von hololens 2 im Shell-Stil 32x96mm</span><span class="sxs-lookup"><span data-stu-id="57994-139">HoloLens 2's shell-style radio 32x96mm</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="57994-140">![Radialer ](../images/button/MRTK_Button_Radial.png) **radialer**</span><span class="sxs-lookup"><span data-stu-id="57994-140">![Radial](../images/button/MRTK_Button_Radial.png) **Radial**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="57994-141">![Kontrollkästchen](../images/button/MRTK_Button_Checkbox.png) **Kontrollkästchen**</span><span class="sxs-lookup"><span data-stu-id="57994-141">![Checkbox](../images/button/MRTK_Button_Checkbox.png) **Checkbox**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="57994-142">![Umggleswitch ](../images/button/MRTK_Button_ToggleSwitch.png)  -Schalter</span><span class="sxs-lookup"><span data-stu-id="57994-142">![ToggleSwitch](../images/button/MRTK_Button_ToggleSwitch.png) **ToggleSwitch**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="57994-143">Radiale Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="57994-143">Radial button</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="57994-144">Checkbox</span><span class="sxs-lookup"><span data-stu-id="57994-144">Checkbox</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="57994-145">Umschalter</span><span class="sxs-lookup"><span data-stu-id="57994-145">Toggle switch</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="57994-146">![ButtonHoloLens1 ](../images/button/MRTK_Button_HoloLens1.png) **ButtonHoloLens1**</span><span class="sxs-lookup"><span data-stu-id="57994-146">![ButtonHoloLens1](../images/button/MRTK_Button_HoloLens1.png) **ButtonHoloLens1**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="57994-147">![Pressableroundbutton ](../images/button/MRTK_Button_Round.png) **pressableroundbutton**</span><span class="sxs-lookup"><span data-stu-id="57994-147">![PressableRoundButton](../images/button/MRTK_Button_Round.png) **PressableRoundButton**</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="57994-148">![Schaltfläche ](../images/button/MRTK_Button_Base.png) **für** Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="57994-148">![Button Base](../images/button/MRTK_Button_Base.png) **Button**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="57994-149">Schraffurschaltfläche "hololens 1. gen"</span><span class="sxs-lookup"><span data-stu-id="57994-149">HoloLens 1st gen's shell style button</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="57994-150">Schaltfläche "Round Form"</span><span class="sxs-lookup"><span data-stu-id="57994-150">Round shape push button</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="57994-151">Basic-Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="57994-151">Basic button</span></span>
    :::column-end:::
:::row-end:::

<span data-ttu-id="57994-152">Der `Button` (Assets/mrtk/SDK/Features/UX/interactable/Prefabs/Button. Prefab) basiert auf dem [interactable](interactable.md) -Konzept, um einfache UI-Steuerelemente für Schaltflächen oder andere Typen interaktiver Oberflächen bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="57994-152">The `Button` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/Button.prefab) is based on the [Interactable](interactable.md) concept to provide easy UI controls for buttons or other types of interactive surfaces.</span></span> <span data-ttu-id="57994-153">Die Schaltfläche Baseline unterstützt alle verfügbaren Eingabemethoden, einschließlich der Handgelenk Eingabe für die Near-Interaktionen sowie den Blick auf den Blick und den Mauszeiger für die weit entfernten Interaktionen.</span><span class="sxs-lookup"><span data-stu-id="57994-153">The baseline button supports all available input methods, including articulated hand input for the near interactions as well as gaze + air-tap for the far interactions.</span></span> <span data-ttu-id="57994-154">Sie können auch den Voice-Befehl verwenden, um die Schaltfläche zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="57994-154">You can also use voice command to trigger the button.</span></span>

<span data-ttu-id="57994-155">`PressableButtonHoloLens2` (Assets/mrtk/SDK/Features/UX/interactable/Prefabs/PressableButtonHoloLens2. Prefab) ist die shellstilschaltfläche "hololens 2", die die genaue Bewegung der Schaltfläche für die Eingabe der direkt Hand Nachverfolgung unterstützt.</span><span class="sxs-lookup"><span data-stu-id="57994-155">`PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) is HoloLens 2's shell style button that supports the precise movement of the button for the direct hand tracking input.</span></span> <span data-ttu-id="57994-156">Es kombiniert `Interactable` Skripts mit `PressableButton` Skripts.</span><span class="sxs-lookup"><span data-stu-id="57994-156">It combines `Interactable` script with `PressableButton` script.</span></span>

<span data-ttu-id="57994-157">Bei hololens 2 wird empfohlen, Schaltflächen mit einem nicht transparenten Backplate zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="57994-157">For HoloLens 2, it is recommended to use buttons with an opaque backplate.</span></span> <span data-ttu-id="57994-158">Transparente Schaltflächen werden aufgrund dieser Nutzbarkeits-und Stabilitätsprobleme nicht empfohlen:</span><span class="sxs-lookup"><span data-stu-id="57994-158">Transparent buttons are not recommended because of these usability and stability issues:</span></span>

* <span data-ttu-id="57994-159">Symbol und Text sind schwer zu lesen mit der physischen Umgebung.</span><span class="sxs-lookup"><span data-stu-id="57994-159">Icon and text are difficult to read with the physical environment</span></span>
* <span data-ttu-id="57994-160">Es ist schwer nachzuvollziehen, wenn das Ereignis ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="57994-160">It is hard to understand when the event triggers</span></span>
* <span data-ttu-id="57994-161">Holograms, die über eine transparente Ebene angezeigt werden, können mit der tiefen LSR-Stabilisierung von hololens 2 instabil werden.</span><span class="sxs-lookup"><span data-stu-id="57994-161">Holograms that are displayed through a transparent plane can be unstable with HoloLens 2's Depth LSR stabilization</span></span>

![Schaltfläche](../images/button/MRTK_Button_UsePlated.png)

## <a name="how-to-use-pressable-buttons"></a><span data-ttu-id="57994-163">Verwenden von druckbaren Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="57994-163">How to use pressable buttons</span></span>

### <a name="unity-ui-based-buttons"></a><span data-ttu-id="57994-164">Auf Unity-UI basierende Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="57994-164">Unity UI based buttons</span></span>

<span data-ttu-id="57994-165">Erstellen Sie einen Canvas in Ihrer Szene (gameobject-> UI-> Canvas).</span><span class="sxs-lookup"><span data-stu-id="57994-165">Create a Canvas in your scene (GameObject -> UI -> Canvas).</span></span> <span data-ttu-id="57994-166">Im Inspektor-Panel für Ihren Zeichenbereich:</span><span class="sxs-lookup"><span data-stu-id="57994-166">In the Inspector panel for your Canvas:</span></span>

* <span data-ttu-id="57994-167">Klicken Sie auf "in mrtk-Canvas konvertieren".</span><span class="sxs-lookup"><span data-stu-id="57994-167">Click "Convert to MRTK Canvas"</span></span>
* <span data-ttu-id="57994-168">Klicken Sie auf "nearinteraktiontouchableunityui hinzufügen".</span><span class="sxs-lookup"><span data-stu-id="57994-168">Click "Add NearInteractionTouchableUnityUI"</span></span>
* <span data-ttu-id="57994-169">Legen Sie die X-, Y-und Z-Skala der Rect-Transformations Komponente auf 0,001 fest.</span><span class="sxs-lookup"><span data-stu-id="57994-169">Set the Rect Transform component's X, Y, and Z scale to 0.001</span></span>

<span data-ttu-id="57994-170">Ziehen Sie dann `PressableButtonUnityUI` (Assets/mrtk/SDK/Features/UX/interactable/Prefabs/pressablebuttonunityui). Prefab), `PressableButtonUnityUICircular` (Assets/mrtk/SDK/Features/UX/interactable/Prefabs/pressablebuttonunityuizirkel. Prefab) oder `PressableButtonHoloLens2UnityUI` (Assets/mrtk/SDK/Features/UX/interactable/Prefabs/PressableButtonHoloLens2UnityUI. Prefab) auf der Canvas.</span><span class="sxs-lookup"><span data-stu-id="57994-170">Then, drag `PressableButtonUnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUI.prefab), `PressableButtonUnityUICircular` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUICircular.prefab), or `PressableButtonHoloLens2UnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2UnityUI.prefab) onto the Canvas.</span></span>

### <a name="collider-based-buttons"></a><span data-ttu-id="57994-171">Auf Collider basierende Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="57994-171">Collider based buttons</span></span>

<span data-ttu-id="57994-172">Ziehen Sie einfach `PressableButtonHoloLens2` (Assets/mrtk/SDK/Features/UX/interactable/Prefabs/PressableButtonHoloLens2. Prefab) oder `PressableButtonHoloLens2Unplated` (Assets/mrtk/SDK/Features/UX/interactable/Prefabs/PressableButtonHoloLens2Unplated. Prefab) in die Szene.</span><span class="sxs-lookup"><span data-stu-id="57994-172">Simply drag `PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) or `PressableButtonHoloLens2Unplated` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2Unplated.prefab) into the scene.</span></span> <span data-ttu-id="57994-173">Diese Schaltflächen-Prefabs sind bereits so konfiguriert, dass Sie audiovisuelles Feedback für die verschiedenen Typen von Eingaben haben, einschließlich Hand Eingaben und Blick auf die Hand.</span><span class="sxs-lookup"><span data-stu-id="57994-173">These button prefabs are already configured to have audio-visual feedback for the various types of inputs, including articulated hand input and gaze.</span></span>

<span data-ttu-id="57994-174">Die Ereignisse, die in der vorfab selbst und der [interactable](interactable.md) -Komponente verfügbar gemacht werden, können verwendet werden, um zusätzliche Aktionen zu initiieren.</span><span class="sxs-lookup"><span data-stu-id="57994-174">The events exposed in the prefab itself as well as the [Interactable](interactable.md) component can be used to trigger additional actions.</span></span> <span data-ttu-id="57994-175">Die druckbaren Schaltflächen in der [handinteraktionexample-Szene](../example-scenes/hand-interaction-examples.md) verwenden das *OnClick* -Ereignis von interactable, um eine Änderung in der Farbe eines Cubes auslöst.</span><span class="sxs-lookup"><span data-stu-id="57994-175">The pressable buttons in the [HandInteractionExample scene](../example-scenes/hand-interaction-examples.md) use Interactable's *OnClick* event to trigger a change in the color of a cube.</span></span> <span data-ttu-id="57994-176">Dieses Ereignis wird für verschiedene Typen von Eingabemethoden ausgelöst, z. b. "Blick", "Air-Tap", "Hand Strahl" und "physische Schaltflächen" über das Schaltflächen Skript.</span><span class="sxs-lookup"><span data-stu-id="57994-176">This event gets triggered for different types of input methods such as gaze, air-tap, hand-ray, as well as physical button presses through the pressable button script.</span></span>

<img src="../images/button/MRTK_Button_HowToUse_Interactable.png" width="450" alt="How to Use Interactable">

<span data-ttu-id="57994-177">Sie können konfigurieren, wann das *OnClick* -Ereignis über die Schaltfläche `PhysicalPressEventRouter` auf der Schaltfläche ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="57994-177">You can configure when the pressable button fires the *OnClick* event via the `PhysicalPressEventRouter` on the button.</span></span> <span data-ttu-id="57994-178">Beispielsweise können Sie festlegen, dass " *OnClick* " ausgelöst wird, wenn die Schaltfläche zum ersten Mal gedrückt wird, anstatt gedrückt und freigegeben zu werden, indem Sie *interactable beim Klicken* auf das *Ereignis beim Drücken* festlegen.</span><span class="sxs-lookup"><span data-stu-id="57994-178">For example, you can set *OnClick* to fire when the button is first pressed, as opposed to being pressed and released, by setting *Interactable On Click* to *Event On Press*.</span></span>

<img src="../images/button/MRTK_Button_HowTo_Events.png" width="450" alt="How to use events">

<span data-ttu-id="57994-179">Um bestimmte Informationen zum Hand Eingabe Zustand zu nutzen, können Sie Druck Bare Schaltflächen Ereignisse verwenden: *Berührungs Anfang*, *Berührungs Ende*, Schaltfläche, *gedrückt*, *Schaltfläche losgelassen*.</span><span class="sxs-lookup"><span data-stu-id="57994-179">To leverage specific articulated hand input state information, you can use pressable buttons events - *Touch Begin*, *Touch End*, *Button Pressed*, *Button Released*.</span></span> <span data-ttu-id="57994-180">Diese Ereignisse werden jedoch nicht als Reaktion auf Luft tippen-, Hand Strahl-oder Augen Eingaben ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="57994-180">These events will not fire in response to air-tap, hand-ray, or eye inputs, however.</span></span> <span data-ttu-id="57994-181">**Zur Unterstützung von Near-und Far-Interaktionen wird empfohlen, das *OnClick* -Ereignis der interactable zu verwenden.**</span><span class="sxs-lookup"><span data-stu-id="57994-181">**To support both near and far interactions, it is recommended to use Interactable's *OnClick* event.**</span></span>

<img src="../images/button/MRTK_Button_HowTo_PressableButton.png" width="450"  alt="How to use Pressable Buttons">

## <a name="interaction-states"></a><span data-ttu-id="57994-182">Interaktions Zustände</span><span class="sxs-lookup"><span data-stu-id="57994-182">Interaction states</span></span>

<span data-ttu-id="57994-183">Im Leerlaufzustand ist die Vorderseite der Schaltfläche nicht sichtbar.</span><span class="sxs-lookup"><span data-stu-id="57994-183">In the idle state, the button's front plate is not visible.</span></span> <span data-ttu-id="57994-184">Wenn eine Fingereingabe oder ein Cursor von der Blick Eingabe auf die Oberfläche abzielt, wird der leuchtende Rahmen der Vorderseite sichtbar.</span><span class="sxs-lookup"><span data-stu-id="57994-184">As a finger approaches or a cursor from gaze input targets the surface, the front plate's glowing border becomes visible.</span></span> <span data-ttu-id="57994-185">Es gibt zusätzliche Hervorhebung der Fingertip-Position auf der Vorderseite der Oberplatte.</span><span class="sxs-lookup"><span data-stu-id="57994-185">There is additional highlighting of the fingertip position on the front plate surface.</span></span> <span data-ttu-id="57994-186">Bei einem Fingerabdruck wird die Vorderseite mit dem Fingertipp bewegt.</span><span class="sxs-lookup"><span data-stu-id="57994-186">When pushed with a finger, the front plate moves with the fingertip.</span></span> <span data-ttu-id="57994-187">Wenn sich der Fingertipp auf die Oberfläche der Vorderseite auswirkt, wird ein feiner Impuls Effekt angezeigt, um dem TouchPoint ein visuelles Feedback zu geben.</span><span class="sxs-lookup"><span data-stu-id="57994-187">When the fingertip touches the surface of the front plate, it shows a subtle pulse effect to give visual feedback of the touch point.</span></span>

<span data-ttu-id="57994-188">In der Schaltfläche "hololens 2 Shell-Style" gibt es viele visuelle Hinweise und Kosten, um das Vertrauen des Benutzers auf die Interaktion zu erhöhen.</span><span class="sxs-lookup"><span data-stu-id="57994-188">In HoloLens 2 shell-style button, there are many visual cues and affordances to increase the user's confidence on interaction.</span></span>

|  ![Near Light](../images/button/ux_button_affordance_proximitylight.jpg) | ![Fokus Hervorhebung](../images/button/ux_button_affordance_focushighlight.jpg)  | ![Komprimieren von Cage](../images/button/ux_button_affordance_compression.jpg) | ![Pulse on-Triggern](../images/button/ux_button_affordance_pulse.jpg) |
|:--- | :--- | :--- | :--- |
| <span data-ttu-id="57994-193">Near Light</span><span class="sxs-lookup"><span data-stu-id="57994-193">Proximity light</span></span> | <span data-ttu-id="57994-194">Fokus Hervorhebung</span><span class="sxs-lookup"><span data-stu-id="57994-194">Focus highlight</span></span> | <span data-ttu-id="57994-195">Komprimieren von Cage</span><span class="sxs-lookup"><span data-stu-id="57994-195">Compressing cage</span></span> | <span data-ttu-id="57994-196">Pulse on-Triggern</span><span class="sxs-lookup"><span data-stu-id="57994-196">Pulse on trigger</span></span> |

<span data-ttu-id="57994-197">Der feine Pulse-Effekt wird durch die Schaltfläche zum Drücken der Schaltfläche ausgelöst, die nach dem aktuell interagierenden Zeiger, der nach dem aktuell interagierenden Zeiger ist *, nach "* ".</span><span class="sxs-lookup"><span data-stu-id="57994-197">The subtle pulse effect is triggered by the pressable button, which looks for *ProximityLight(s)* that live on the currently interacting pointer.</span></span> <span data-ttu-id="57994-198">Wenn Näherungs Lichter gefunden werden, wird die- `ProximityLight.Pulse` Methode aufgerufen, die Shader-Parameter automatisch animiert, um einen Impuls anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="57994-198">If any proximity lights are found, the `ProximityLight.Pulse` method is called, which automatically animates shader parameters to display a pulse.</span></span>

## <a name="inspector-properties"></a><span data-ttu-id="57994-199">Inspektor-Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="57994-199">Inspector properties</span></span>

![Schaltflächen Struktur](../images/button/MRTK_Button_Structure.png)

<span data-ttu-id="57994-201">**Box-Collider** 
 `Box Collider` für die Vorderseite der Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="57994-201">**Box Collider**
`Box Collider` for the button's front plate.</span></span>

<span data-ttu-id="57994-202">**Schaltfläche zum Komprimieren** Die Logik für die Schaltflächen Bewegung mit der Hand Press Interaktion.</span><span class="sxs-lookup"><span data-stu-id="57994-202">**Pressable Button** The logic for the button movement with hand press interaction.</span></span>

<span data-ttu-id="57994-203">**Physischer Press-Ereignis Router** Dieses Skript sendet Ereignisse von der Hand Press Interaktion an [interactable](interactable.md).</span><span class="sxs-lookup"><span data-stu-id="57994-203">**Physical Press Event Router** This script sends events from hand press interaction to [Interactable](interactable.md).</span></span>

<span data-ttu-id="57994-204">**Interactable** 
 [Interactable](interactable.md) behandelt verschiedene Typen von Interaktions Zuständen und-Ereignissen.</span><span class="sxs-lookup"><span data-stu-id="57994-204">**Interactable**
[Interactable](interactable.md) handles various types of interaction states and events.</span></span> <span data-ttu-id="57994-205">Hololens, Eingaben, Gesten und Spracheingabe und immersive Headset-Bewegung Controller Eingaben werden direkt von diesem Skript behandelt.</span><span class="sxs-lookup"><span data-stu-id="57994-205">HoloLens gaze, gesture, and voice input and immersive headset motion controller input are directly handled by this script.</span></span>

<span data-ttu-id="57994-206">**Audioquelle** Unity-Audioquelle für die Audiofeedback-Clips.</span><span class="sxs-lookup"><span data-stu-id="57994-206">**Audio Source** Unity audio source for the audio feedback clips.</span></span>

<span data-ttu-id="57994-207">" *Nearinteraktiontouchable. cs* " ist erforderlich, damit ein beliebiges Objekt mit einer Handgelenk Eingabe touchfähig ist.</span><span class="sxs-lookup"><span data-stu-id="57994-207">*NearInteractionTouchable.cs* Required to make any object touchable with articulated hand input.</span></span>

## <a name="prefab-layout"></a><span data-ttu-id="57994-208">Vorfab-Layout</span><span class="sxs-lookup"><span data-stu-id="57994-208">Prefab layout</span></span>

<span data-ttu-id="57994-209">Das *buttoncontent* -Objekt enthält Front Plate, Text Bezeichnung und Symbol.</span><span class="sxs-lookup"><span data-stu-id="57994-209">The *ButtonContent* object contains front plate, text label and icon.</span></span> <span data-ttu-id="57994-210">Die *frontplate* antwortet mit dem *Button_Box* -Shader auf die Nähe des Index fingerabbilds.</span><span class="sxs-lookup"><span data-stu-id="57994-210">The *FrontPlate* responds to the proximity of the index fingertip using the *Button_Box* shader.</span></span> <span data-ttu-id="57994-211">Es zeigt leuchtende Rahmen, Näherungs Licht und einen Impuls Effekt bei der Berührung.</span><span class="sxs-lookup"><span data-stu-id="57994-211">It shows glowing borders, proximity light, and a pulse effect on touch.</span></span> <span data-ttu-id="57994-212">Die Bezeichnung Text wird mit textmesh pro erstellt.</span><span class="sxs-lookup"><span data-stu-id="57994-212">The text label is made with TextMesh Pro.</span></span> <span data-ttu-id="57994-213">Die Sichtbarkeit von " *mineitsayitlabel*" wird durch das Design der [interactable](interactable.md)gesteuert.</span><span class="sxs-lookup"><span data-stu-id="57994-213">*SeeItSayItLabel*'s visibility is controlled by [Interactable](interactable.md)'s theme.</span></span>

![Schaltflächen Layout](../images/button/MRTK_Button_Layout.png)

## <a name="how-to-change-the-icon-and-text"></a><span data-ttu-id="57994-215">Ändern von Symbol und Text</span><span class="sxs-lookup"><span data-stu-id="57994-215">How to change the icon and text</span></span>

<span data-ttu-id="57994-216">Mrtk-Schaltflächen verwenden eine `ButtonConfigHelper` Komponente, um das Symbol, den Text und die Bezeichnung der Schaltfläche zu ändern.</span><span class="sxs-lookup"><span data-stu-id="57994-216">MRTK buttons use a `ButtonConfigHelper` component to assist you in changing the button's icon, text and label.</span></span> <span data-ttu-id="57994-217">(Beachten Sie, dass einige Felder möglicherweise fehlen, wenn Elemente nicht auf der ausgewählten Schaltfläche vorhanden sind.)</span><span class="sxs-lookup"><span data-stu-id="57994-217">(Note that some fields may be absent if elements are not present on the selected button.)</span></span>

![Schaltflächen Konfigurations Hilfsprogramm](../images/button/MRTK_Button_Config_Helper.png)

### <a name="creating-and-modifying-icon-sets"></a><span data-ttu-id="57994-219">Erstellen und Ändern von Symbol Sätzen</span><span class="sxs-lookup"><span data-stu-id="57994-219">Creating and Modifying Icon Sets</span></span>

<span data-ttu-id="57994-220">Ein **Symbolsatz** ist ein frei gegebener Satz von Symbol Ressourcen, die von der Komponente verwendet werden `ButtonConfigHelper` .</span><span class="sxs-lookup"><span data-stu-id="57994-220">An **Icon Set** is a shared set of icon assets used by the `ButtonConfigHelper` component.</span></span> <span data-ttu-id="57994-221">Drei Symbol *Stile* werden unterstützt.</span><span class="sxs-lookup"><span data-stu-id="57994-221">Three icon *styles* are supported.</span></span>

* <span data-ttu-id="57994-222">**Quad** -Symbole werden mithilfe eines auf einem Quad gerendert `MeshRenderer` .</span><span class="sxs-lookup"><span data-stu-id="57994-222">**Quad** icons are rendered on a quad using a `MeshRenderer`.</span></span> <span data-ttu-id="57994-223">Dies ist der standardmäßige Symbol Stil.</span><span class="sxs-lookup"><span data-stu-id="57994-223">This is the default icon style.</span></span>
* <span data-ttu-id="57994-224">**Sprite** -Symbole werden mithilfe von gerendert `SpriteRenderer` .</span><span class="sxs-lookup"><span data-stu-id="57994-224">**Sprite** icons are rendered using a `SpriteRenderer`.</span></span> <span data-ttu-id="57994-225">Dies ist hilfreich, wenn Sie Ihre Symbole lieber als Sprite-Tabelle importieren möchten, oder wenn Sie möchten, dass Ihre Symbol Objekte mit Unity-UI-Komponenten gemeinsam genutzt werden.</span><span class="sxs-lookup"><span data-stu-id="57994-225">This is useful if you prefer to import your icons as a sprite sheet, or if you want your icon assets to be shared with Unity UI components.</span></span> <span data-ttu-id="57994-226">Um dieses Format zu verwenden, müssen Sie das Sprite-Editor **-Paket (Windows-> Package Manager-> 2D Sprite) installieren.**</span><span class="sxs-lookup"><span data-stu-id="57994-226">To use this style you will need to install the Sprite Editor package **(Windows -> Package Manager -> 2D Sprite)**</span></span>
* <span data-ttu-id="57994-227">**Char** -Symbole werden mithilfe einer-Komponente gerendert `TextMeshPro` .</span><span class="sxs-lookup"><span data-stu-id="57994-227">**Char** icons are rendered using a `TextMeshPro` component.</span></span> <span data-ttu-id="57994-228">Dies ist nützlich, wenn Sie lieber eine Symbol Schriftart verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="57994-228">This is useful if you prefer to use an icon font.</span></span> <span data-ttu-id="57994-229">Wenn Sie die hololens-Symbol Schriftart verwenden möchten, müssen Sie ein `TextMeshPro` Schriftart Objekt erstellen.</span><span class="sxs-lookup"><span data-stu-id="57994-229">To use the HoloLens icon font you will need to create a `TextMeshPro` font asset.</span></span>

<span data-ttu-id="57994-230">Um den Stil der Schaltfläche zu ändern, erweitern Sie die Dropdown Liste *Symbole* in der Schaltfläche buttonconfighelper, und wählen Sie aus der Dropdown Liste *Icon Style* aus.</span><span class="sxs-lookup"><span data-stu-id="57994-230">To change which style your button uses, expand the *Icons* dropdown in the ButtonConfigHelper and select from the *Icon Style* dropdown.</span></span>

<span data-ttu-id="57994-231">Sie können mit dem Asset-Menü ein neues Schaltflächen Symbol erstellen: **Erstellen Sie > Mixed Reality Toolkit > Symbolsatz.**</span><span class="sxs-lookup"><span data-stu-id="57994-231">You can create a new button icon set with the asset menu: **Create > Mixed Reality Toolkit > Icon Set.**</span></span> <span data-ttu-id="57994-232">Um Quad-und Sprite-Symbole hinzuzufügen, ziehen Sie Sie einfach in ihre jeweiligen Arrays.</span><span class="sxs-lookup"><span data-stu-id="57994-232">To add quad and sprite icons, simply drag them into their respective arrays.</span></span> <span data-ttu-id="57994-233">Um char-Symbole hinzuzufügen, müssen Sie zuerst ein Schriftart Objekt erstellen und zuweisen.</span><span class="sxs-lookup"><span data-stu-id="57994-233">To add Char icons, you must first create and assign a font asset.</span></span>

<span data-ttu-id="57994-234">In mrtk 2,4 und höher wird empfohlen, benutzerdefinierte Symbol Texturen in ein Iconset zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="57994-234">In MRTK 2.4 and beyond, we recommend custom icon textures be moved into an IconSet.</span></span>
<span data-ttu-id="57994-235">Um die Assets auf allen Schaltflächen in einem Projekt auf das neue empfohlene Format zu aktualisieren, verwenden Sie den buttonconfighelpermigrationhandler.</span><span class="sxs-lookup"><span data-stu-id="57994-235">To upgrade the assets on all buttons in a project to the new recommended format, use the ButtonConfigHelperMigrationHandler.</span></span>
<span data-ttu-id="57994-236">(Mixed Reality Toolkit-> Utilities-> Migrations Fenster-> Migrations handlerauswahl-> Microsoft. mixedreality. Toolkit. Utilities. buttonconfighelpermigrationhandler)</span><span class="sxs-lookup"><span data-stu-id="57994-236">(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality.Toolkit.Utilities.ButtonConfigHelperMigrationHandler)</span></span>

<span data-ttu-id="57994-237">Importieren des Microsoft. mixedrealitytoolkit. Unity. Tools-Pakets, das zum Aktualisieren der Schaltflächen erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="57994-237">Importing the Microsoft.MixedRealityToolkit.Unity.Tools package required to upgrade the buttons.</span></span>

![Dialog](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

<span data-ttu-id="57994-239">Wenn ein Symbol bei der Migration nicht im Standard Symbol festgelegt wurde, wird ein benutzerdefiniertes Symbol in mixedrealitytoolkit. generated/customiensets erstellt.</span><span class="sxs-lookup"><span data-stu-id="57994-239">If an icon is not found in the default icon set during migration, a custom icon set will be created in MixedRealityToolkit.Generated/CustomIconSets.</span></span> <span data-ttu-id="57994-240">In einem Dialogfeld wird angezeigt, dass dies stattfindet.</span><span class="sxs-lookup"><span data-stu-id="57994-240">A dialog will indicate that this has taken place.</span></span>

![Benachrichtigung über benutzerdefinierte Symbole](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

### <a name="creating-a-hololens-icon-font-asset"></a><span data-ttu-id="57994-242">Erstellen eines hololens-Symbol Schriftart-Assets</span><span class="sxs-lookup"><span data-stu-id="57994-242">Creating a HoloLens Icon Font Asset</span></span>

<span data-ttu-id="57994-243">Importieren Sie zunächst die Symbol Schriftart in Unity.</span><span class="sxs-lookup"><span data-stu-id="57994-243">First, import the icon font into Unity.</span></span> <span data-ttu-id="57994-244">Auf Windows-Computern finden Sie die Standard Schriftart hololens in *Windows/Fonts/holomdl2. ttf.*</span><span class="sxs-lookup"><span data-stu-id="57994-244">On Windows machines you can find the default HoloLens font in *Windows/Fonts/holomdl2.ttf.*</span></span> <span data-ttu-id="57994-245">Kopieren Sie diese Datei, und fügen Sie Sie in den Ordner Assets ein.</span><span class="sxs-lookup"><span data-stu-id="57994-245">Copy and paste this file into your Assets folder.</span></span>

<span data-ttu-id="57994-246">Öffnen Sie als nächstes den textmeschpro-schriftstellerersteller über **Fenster > textmeshpro > Schriftart Asset Creator.**</span><span class="sxs-lookup"><span data-stu-id="57994-246">Next, open the TextMeshPro Font Asset Creator via **Window > TextMeshPro > Font Asset Creator.**</span></span> <span data-ttu-id="57994-247">Hier finden Sie die empfohlenen Einstellungen für die Erstellung eines hololens-Schriftart Atlas.</span><span class="sxs-lookup"><span data-stu-id="57994-247">Here are the recommended settings for generating a HoloLens font atlas.</span></span> <span data-ttu-id="57994-248">Fügen Sie den folgenden Unicode-Bereich in das Feld *Zeichenfolge* ein, um alle Symbole einzuschließen:</span><span class="sxs-lookup"><span data-stu-id="57994-248">To include all icons, paste the following Unicode range into the *Character Sequence* field:</span></span>

```c#
E700-E702,E706,E70D-E70E,E710-E714,E718,E71A,E71D-E71E,E720,E722,E728,E72A-E72E,E736,E738,E73F,E74A-E74B,E74D,E74F-E752,E760-E761,E765,E767-E769,E76B-E76C,E770,E772,E774,E777,E779-E77B,E782-E783,E785-E786,E799,E7A9-E7AB,E7AF-E7B1,E7B4,E7C8,E7E8-E7E9,E7FC,E80F,E821,E83F,E850-E859,E872-E874,E894-E895,E8A7,E8B2,E8B7,E8B9,E8D5,E8EC,E8FB,E909,E91B,E92C,E942,E95B,E992-E995,E9E9-E9EA,EA37,EA40,EA4A,EA55,EA96,EB51-EB52,EB65,EB9D-EBB5,EBCB-EBCC,EBCF-EBD3,EC03,EC19,EC3F,EC7A,EC8E-EC98,ECA2,ECD8-ECDA,ECE0,ECE7-ECEB,ED17,EE93,EFA9,F114-F120,F132,F181,F183-F186
```

![Schaltflächen Erstellung 1](../images/button/MRTK_Font_Asset_Creation_1.png)

<span data-ttu-id="57994-250">Nachdem das Schriftart Objekt generiert wurde, speichern Sie es in Ihrem Projekt, und weisen Sie es dem Symbol *Schriftart* Feldzeichen für Symbolsatz zu.</span><span class="sxs-lookup"><span data-stu-id="57994-250">Once the font asset is generated, save it to your project and assign it to your Icon Set's *Char Icon Font* field.</span></span> <span data-ttu-id="57994-251">Die Dropdown Liste *verfügbare Symbole* wird nun aufgefüllt.</span><span class="sxs-lookup"><span data-stu-id="57994-251">The *Available Icons* dropdown will now be populated.</span></span> <span data-ttu-id="57994-252">Um ein Symbol für die Verwendung durch eine Schaltfläche verfügbar zu machen, klicken Sie darauf.</span><span class="sxs-lookup"><span data-stu-id="57994-252">To make an icon available for use by a button, click it.</span></span> <span data-ttu-id="57994-253">Sie wird der Dropdown Liste *ausgewählte Symbole* hinzugefügt und wird jetzt im angezeigt `ButtonConfigHelper.` . Optional können Sie dem Symbol ein Tag geben.</span><span class="sxs-lookup"><span data-stu-id="57994-253">It will be added to the *Selected Icons* dropdown and will now show up in the `ButtonConfigHelper.` You can optionally give the icon a tag.</span></span> <span data-ttu-id="57994-254">Dadurch kann das Symbol zur Laufzeit festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="57994-254">This enables setting the icon at runtime.</span></span>

![Schaltflächen Erstellung 3](../images/button/MRTK_Font_Asset_Creation_3.png)

![Schaltflächen Erstellung 2](../images/button/MRTK_Font_Asset_Creation_2.png)

```c#
public void SetButtonToAdjust()
{
    ButtonConfigHelper buttonConfigHelper = gameObject.GetComponent<ButtonConfigHelper>();
    buttonConfigHelper.SetCharIconByName("AppBarAdjust");
}
```

<span data-ttu-id="57994-257">Um das Symbol festzulegen, wählen Sie eine Schaltfläche aus, erweitern Sie das Dropdown Feldsymbole in der, `ButtonConfigHelper` und weisen Sie es dem Feld *Symbolsatz* zu.</span><span class="sxs-lookup"><span data-stu-id="57994-257">To use your Icon Set select a button, expand the Icons dropdown in the `ButtonConfigHelper` and assign it to the *Icon Set* field.</span></span>

![Schaltflächen Symbolsatz](../images/button/MRTK_Button_Icon_Set_Assign.png)

## <a name="how-to-change-the-size-of-a-button"></a><span data-ttu-id="57994-259">Ändern der Größe einer Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="57994-259">How to change the size of a button</span></span>

<span data-ttu-id="57994-260">Die Größe der Schaltfläche im shellstil von hololens 2 beträgt 32 x 32mm.</span><span class="sxs-lookup"><span data-stu-id="57994-260">HoloLens 2's shell-style button's size is 32x32mm.</span></span> <span data-ttu-id="57994-261">Um die Dimension anzupassen, ändern Sie die Größe dieser Objekte in der Schaltfläche Prefab:</span><span class="sxs-lookup"><span data-stu-id="57994-261">To customize the dimension, change the size of these objects in the button prefab:</span></span>

1. <span data-ttu-id="57994-262">**Frontplate**</span><span class="sxs-lookup"><span data-stu-id="57994-262">**FrontPlate**</span></span>
2. <span data-ttu-id="57994-263">**Quad** unter "Backplate"</span><span class="sxs-lookup"><span data-stu-id="57994-263">**Quad** under BackPlate</span></span>
3. <span data-ttu-id="57994-264">**Box-Collider** im Stamm</span><span class="sxs-lookup"><span data-stu-id="57994-264">**Box Collider** on the root</span></span>

<span data-ttu-id="57994-265">Klicken Sie dann im "nearinteraktiontouchable"-Skript, das sich im Stammverzeichnis der Schaltfläche befindet, auf die Schaltfläche " **Begrenzungen reparieren** "</span><span class="sxs-lookup"><span data-stu-id="57994-265">Then, click **Fix Bounds** button in the NearInteractionTouchable script which is in the root of the button.</span></span>

<span data-ttu-id="57994-266">Aktualisieren Sie die Größe der frontplate- ![ Schaltflächen Größenanpassung 1.](../images/button/MRTK_Button_SizeCustomization1.png)</span><span class="sxs-lookup"><span data-stu-id="57994-266">Update the size of the FrontPlate ![Button Size customization 1](../images/button/MRTK_Button_SizeCustomization1.png)</span></span>

<span data-ttu-id="57994-267">Aktualisieren der Größe der Größenanpassung von Quad- ![ Schaltflächen 2](../images/button/MRTK_Button_SizeCustomization2.png)</span><span class="sxs-lookup"><span data-stu-id="57994-267">Update the size of the Quad ![Button Size customization 2](../images/button/MRTK_Button_SizeCustomization2.png)</span></span>

<span data-ttu-id="57994-268">Aktualisieren der Größe der Schaltfläche für die ![ Größe der Schaltfläche der Schaltfläche für das Feld](../images/button/MRTK_Button_SizeCustomization3.png)</span><span class="sxs-lookup"><span data-stu-id="57994-268">Update the size of the Box Collider ![Button Size customization 3](../images/button/MRTK_Button_SizeCustomization3.png)</span></span>

<span data-ttu-id="57994-269">Klicken Sie auf die Schaltfläche "Korrektur Begrenzungen" ![ Schaltflächen Größe 4](../images/button/MRTK_Button_SizeCustomization4.png)</span><span class="sxs-lookup"><span data-stu-id="57994-269">Click 'Fix Bounds' ![Button Size customization 4](../images/button/MRTK_Button_SizeCustomization4.png)</span></span>

## <a name="voice-command-see-it-say-it&quot;></a><span data-ttu-id=&quot;57994-270&quot;>Sprachbefehl (&quot;See-it, Say-it")</span><span class="sxs-lookup"><span data-stu-id="57994-270">Voice command ('see-it, say-it')</span></span>

<span data-ttu-id="57994-271">**Spracheingabe Handler** Das [interactable](interactable.md) -Skript in der druckbaren Schaltfläche implementiert bereits `IMixedRealitySpeechHandler` .</span><span class="sxs-lookup"><span data-stu-id="57994-271">**Speech Input Handler** The [Interactable](interactable.md) script in Pressable Button already implements `IMixedRealitySpeechHandler`.</span></span> <span data-ttu-id="57994-272">Ein sprach Befehls Schlüsselwort kann hier festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="57994-272">A voice command keyword can be set here.</span></span>

<img src="../images/button/MRTK_Button_Speech1.png" width="450" alt="Buttons Speech">

<span data-ttu-id="57994-273">**Spracheingabe Profil** Außerdem müssen Sie das sprach Befehls Schlüsselwort im Profil für globale *Sprachbefehle* registrieren.</span><span class="sxs-lookup"><span data-stu-id="57994-273">**Speech Input Profile** Additionally, you need to register the voice command keyword in the global *Speech Commands Profile*.</span></span>

<img src="../images/button/MRTK_Button_Speech2.png" width="450" alt="Button speech 2">

<span data-ttu-id="57994-274">**Siehe die Bezeichnung** . Die Prefab-Schaltflächen-Prefab hat eine Platzhalter textmesh pro-Bezeichnung unter dem *seeitsayitlabel* -Objekt.</span><span class="sxs-lookup"><span data-stu-id="57994-274">**See-it, Say-it label** The pressable button prefab has a placeholder TextMesh Pro label under the *SeeItSayItLabel* object.</span></span> <span data-ttu-id="57994-275">Mit dieser Bezeichnung können Sie dem Benutzer das Voice-Befehls Schlüsselwort für die Schaltfläche mitteilen.</span><span class="sxs-lookup"><span data-stu-id="57994-275">You can use this label to communicate the voice command keyword for the button to the user.</span></span>

<img src="../images/button/MRTK_Button_Speech3.png" width="450" alt="Button Speech 3">

## <a name="how-to-make-a-button-from-scratch"></a><span data-ttu-id="57994-276">So erstellen Sie eine Schaltfläche von Grund auf</span><span class="sxs-lookup"><span data-stu-id="57994-276">How to make a button from scratch</span></span>

<span data-ttu-id="57994-277">Die Beispiele für diese Schaltflächen können Sie in der **pressablebuttonexample** -Szene finden.</span><span class="sxs-lookup"><span data-stu-id="57994-277">You can find the examples of these buttons in the **PressableButtonExample** scene.</span></span>

<img src="../images/button/MRTK_PressableButtonCube0.png" alt="Pressable button cube 0">

### <a name="1-creating-a-pressable-button-with-cube-near-interaction-only"></a><span data-ttu-id="57994-278">1. Erstellen einer druckbaren Schaltfläche mit Cube (nur in naher Interaktion)</span><span class="sxs-lookup"><span data-stu-id="57994-278">1. Creating a pressable button with cube (near interaction only)</span></span>

1. <span data-ttu-id="57994-279">Erstellen eines Unity-Cubes (gameobject > 3D-Objekt > Cube)</span><span class="sxs-lookup"><span data-stu-id="57994-279">Create a Unity Cube (GameObject > 3D Object > Cube)</span></span>
2. <span data-ttu-id="57994-280">Skript hinzufügen `PressableButton.cs`</span><span class="sxs-lookup"><span data-stu-id="57994-280">Add `PressableButton.cs` script</span></span>
3. <span data-ttu-id="57994-281">Skript hinzufügen `NearInteractionTouchable.cs`</span><span class="sxs-lookup"><span data-stu-id="57994-281">Add `NearInteractionTouchable.cs` script</span></span>

<span data-ttu-id="57994-282">`PressableButton`Weisen Sie im Bereich Inspektor das Cube-Objekt den visuellen Elementen der Verschieb **enden Schaltfläche** zu.</span><span class="sxs-lookup"><span data-stu-id="57994-282">In the `PressableButton`'s Inspector panel, assign the cube object to the **Moving Button Visuals**.</span></span>

<img src="../images/button/MRTK_PressableButtonCube3.png" width="450" alt="pressable button cube 3">

<span data-ttu-id="57994-283">Wenn Sie den Cube auswählen, werden mehrere farbige Ebenen für das Objekt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="57994-283">When you select the cube, you will see multiple colored layers on the object.</span></span> <span data-ttu-id="57994-284">Dadurch werden die Entfernungs Werte unter " **Einstellungen**" angezeigt.</span><span class="sxs-lookup"><span data-stu-id="57994-284">This visualizes the distance values under **Press Settings**.</span></span> <span data-ttu-id="57994-285">Mithilfe der Handles können Sie konfigurieren, wann Sie mit dem Drücken der Taste (Verschieben des Objekts) und dem Zeitpunkt des Auslösers eines Ereignisses beginnen.</span><span class="sxs-lookup"><span data-stu-id="57994-285">Using the handles, you can configure when to start press (move the object) and when to trigger event.</span></span>

<img src="../images/button/MRTK_PressableButtonCube1.jpg" width="450" alt="Pressable Buton cube 1">

<img src="../images/button/MRTK_PressableButtonCube2.png" width="450" alt="Pressable button cube 2">

<span data-ttu-id="57994-286">Wenn Sie auf die Schaltfläche klicken, werden die richtigen Ereignisse, die im Skript verfügbar gemacht werden, wie z. b. `PressableButton.cs` touchbegin (), touchend (), ButtonPressed (), buttonreleased (), verschoben und generiert.</span><span class="sxs-lookup"><span data-stu-id="57994-286">When you press the button, it will move and generate proper events exposed in the `PressableButton.cs` script such as TouchBegin(), TouchEnd(), ButtonPressed(), ButtonReleased().</span></span>

<img src="../images/button/MRTK_PressableButtonCubeRun1.jpg" alt="Pressable button cube run 1">

#### <a name="troubleshooting"></a><span data-ttu-id="57994-287">Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="57994-287">Troubleshooting</span></span>

<span data-ttu-id="57994-288">Wenn die Schaltfläche eine Doppel Taste ausführt, stellen Sie sicher, dass die Eigenschaft " **Front Push erzwingen** " aktiv ist und die **Start-pushentfernungsebene** vor der **touchfähigen** Ebene der Near-Interaktion platziert wird.</span><span class="sxs-lookup"><span data-stu-id="57994-288">If your button is executing a double press, make sure the **Enforce Front Push** property is active and the **Start Push Distance** plane is placed in front of the **Near Interaction Touchable** plane.</span></span> <span data-ttu-id="57994-289">Die **touchable** -Ebene der Near-Interaktion wird durch die blaue Ebene angezeigt, die vor dem Ursprung des weißen Pfeils in der GIF unten platziert wird:</span><span class="sxs-lookup"><span data-stu-id="57994-289">The **Near Interaction Touchable** plane is indicated by the blue plane placed in front of the origin of the white arrow in the gif below:</span></span>

![Druck Bare Schaltflächen Skript Komponente mit hervorgehobener Front-Push-Eigenschaft](../images/button/MRTK_Button_Enforce_Push.png)

![Animiertes Beispiel für das Verschieben der Start-Push-Distanz vor der touchfähigen Ebene der Near-Interaktion](../images/button/MRTK_Button_Front_Touch.gif)

### <a name="2-adding-visual-feedback-to-the-basic-cube-button"></a><span data-ttu-id="57994-292">2. Hinzufügen von visuellem Feedback zur grundlegenden Cube-Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="57994-292">2. Adding visual feedback to the basic cube button</span></span>

<span data-ttu-id="57994-293">Der mrtk-Standard-Shader bietet verschiedene Funktionen, die das Hinzufügen von visuellem Feedback erleichtern.</span><span class="sxs-lookup"><span data-stu-id="57994-293">MRTK Standard Shader provides various features that makes it easy to add visual feedback.</span></span> <span data-ttu-id="57994-294">Erstellen Sie ein Material, und wählen Sie Shader aus `Mixed Reality Toolkit/Standard` .</span><span class="sxs-lookup"><span data-stu-id="57994-294">Create a material and select shader `Mixed Reality Toolkit/Standard`.</span></span> <span data-ttu-id="57994-295">Oder Sie können eines der vorhandenen Materialien unter verwenden oder duplizieren `/SDK/StandardAssets/Materials/` , das den mrtk-Standard-Shader verwendet.</span><span class="sxs-lookup"><span data-stu-id="57994-295">Or you can use or duplicate one of the existing materials under `/SDK/StandardAssets/Materials/` that uses MRTK Standard Shader.</span></span>

<img src="../images/button/MRTK_PressableButtonCube4.png" width="450" alt="Pressable button cube 4">

<span data-ttu-id="57994-296">Überprüfen Sie `Hover Light` und `Proximity Light` unter den Optionen für **fließend**.</span><span class="sxs-lookup"><span data-stu-id="57994-296">Check `Hover Light` and `Proximity Light` under **Fluent Options**.</span></span> <span data-ttu-id="57994-297">Dies ermöglicht visuelles Feedback sowohl für Near-Light-Interaktionen (Näherungs Licht) als auch für Fern Zeiger (Hover Light).</span><span class="sxs-lookup"><span data-stu-id="57994-297">This enables visual feedback for both near hand(Proximity Light) and far pointer(Hover Light) interactions.</span></span>

<img src="../images/button/MRTK_PressableButtonCube5.png" width="450" alt="pressable button cube 5">

<img src="../images/button/MRTK_PressableButtonCubeRun2.jpg" alt="pressable button cube run 2">

### <a name="3-adding-audio-feedback-to-the-basic-cube-button"></a><span data-ttu-id="57994-298">3. Hinzufügen von Audiofeedback zur grundlegenden Cube-Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="57994-298">3. Adding audio feedback to the basic cube button</span></span>

<span data-ttu-id="57994-299">Da `PressableButton.cs` Skripts Ereignisse wie touchbegin (), touchend (), ButtonPressed (), buttonreleased () verfügbar machen, können wir einfach Audiofeedback zuweisen.</span><span class="sxs-lookup"><span data-stu-id="57994-299">Since `PressableButton.cs` script exposes events such as TouchBegin(), TouchEnd(), ButtonPressed(), ButtonReleased(), we can easily assign audio feedback.</span></span> <span data-ttu-id="57994-300">Fügen Sie einfach Unity `Audio Source` zum Cube-Objekt hinzu, und weisen Sie dann Audioclips zu, indem Sie audiosource. playoneshot () auswählen.</span><span class="sxs-lookup"><span data-stu-id="57994-300">Simply add Unity's `Audio Source` to the cube object then assign audio clips by selecting AudioSource.PlayOneShot().</span></span> <span data-ttu-id="57994-301">Sie können MRTK_Select_Main und MRTK_Select_Secondary Audioclips unter `/SDK/StandardAssets/Audio/` Ordner verwenden.</span><span class="sxs-lookup"><span data-stu-id="57994-301">You can use MRTK_Select_Main and MRTK_Select_Secondary audio clips under `/SDK/StandardAssets/Audio/` folder.</span></span>

<img src="../images/button/MRTK_PressableButtonCube7.png" width="450" alt="pressable button cube 7">

<img src="../images/button/MRTK_PressableButtonCube6.png" width="450" alt="Pressable Button Cube 6">

### <a name="4-adding-visual-states-and-handle-far-interaction-events"></a><span data-ttu-id="57994-302">4. Hinzufügen von visuellen Zuständen und behandeln von weitem Interaktions Ereignissen</span><span class="sxs-lookup"><span data-stu-id="57994-302">4. Adding visual states and handle far interaction events</span></span>

<span data-ttu-id="57994-303">[Interactable](interactable.md) ist ein Skript, mit dem Sie einen visuellen Zustand für die verschiedenen Typen von Eingabe Interaktionen leicht erstellen können.</span><span class="sxs-lookup"><span data-stu-id="57994-303">[Interactable](interactable.md) is a script that makes it easy to create a visual state for the various types of input interactions.</span></span> <span data-ttu-id="57994-304">Es verarbeitet außerdem weit entfernte Interaktions Ereignisse.</span><span class="sxs-lookup"><span data-stu-id="57994-304">It also handles far interaction events.</span></span> <span data-ttu-id="57994-305">Fügen Sie `Interactable.cs` das Cube-Objekt hinzu, und ziehen Sie es in das Feld **Ziel** unter **profile**.</span><span class="sxs-lookup"><span data-stu-id="57994-305">Add `Interactable.cs` and drag and drop the cube object onto the **Target** field under **Profiles**.</span></span> <span data-ttu-id="57994-306">Erstellen Sie dann ein neues Design mit dem Typ **scaleoffsetcolortheme**.</span><span class="sxs-lookup"><span data-stu-id="57994-306">Then, create a new Theme with a type **ScaleOffsetColorTheme**.</span></span> <span data-ttu-id="57994-307">Unter diesem Thema können Sie die Farbe des-Objekts für die spezifischen Interaktions Zustände angeben, z. b. **Fokus** und **gedrückt**.</span><span class="sxs-lookup"><span data-stu-id="57994-307">Under this theme, you can specify the color of the object for the specific interaction states, such as **Focus** and **Pressed**.</span></span> <span data-ttu-id="57994-308">Sie können auch die Skalierung und den Offset steuern.</span><span class="sxs-lookup"><span data-stu-id="57994-308">You can also control Scale and Offset, as well.</span></span> <span data-ttu-id="57994-309">Aktivieren **Sie** die Beschleunigungs-und festgelegte Dauer, um den visuellen Übergang reibungslos zu gestalten.</span><span class="sxs-lookup"><span data-stu-id="57994-309">Check **Easing** and set duration to make the visual transition smooth.</span></span>

![Profildesign auswählen](../images/button/mrtk_button_profiles.gif)

<span data-ttu-id="57994-311">Sie sehen, dass das-Objekt auf den weit entfernten (Hand Strahl-oder Cursor Cursor) und Near-Interaktionen (Hand) antwortet.</span><span class="sxs-lookup"><span data-stu-id="57994-311">You will see the object respond to both far (hand ray or gaze cursor) and near(hand) interactions.</span></span>

<img src="../images/button/MRTK_PressableButtonCubeRun3.jpg" alt="Pressable Button Cube Run 3">
<img src="../images/button/MRTK_PressableButtonCubeRun4.jpg" alt="Pressable Button Cube Run 4">

## <a name="custom-button-examples"></a><span data-ttu-id="57994-312">Benutzerdefinierte Schaltflächen Beispiele</span><span class="sxs-lookup"><span data-stu-id="57994-312">Custom button examples</span></span>

<span data-ttu-id="57994-313">In der [handinteraktionexample-Szene](../example-scenes/hand-interaction-examples.md)finden Sie die Beispiele für das Klavier und die roundschaltfläche, die beide verwenden `PressableButton` .</span><span class="sxs-lookup"><span data-stu-id="57994-313">In the [HandInteractionExample scene](../example-scenes/hand-interaction-examples.md), see the piano and round button examples which are both using `PressableButton`.</span></span>

<img src="../images/button/MRTK_Button_Custom1.png" width="450" alt="Pressable Custom1">

<img src="../images/button/MRTK_Button_Custom2.png" width="450" alt="Pressable Custom2">

<span data-ttu-id="57994-314">Jedem Klavierschlüssel ist ein `PressableButton` -und ein- `NearInteractionTouchable` Skript zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="57994-314">Each piano key has a `PressableButton` and a `NearInteractionTouchable` script assigned.</span></span> <span data-ttu-id="57994-315">Es ist wichtig, zu überprüfen, ob die *lokale vorwärts* Richtung `NearInteractionTouchable` korrekt ist.</span><span class="sxs-lookup"><span data-stu-id="57994-315">It is important to verify that the *Local Forward* direction of `NearInteractionTouchable` is correct.</span></span> <span data-ttu-id="57994-316">Sie wird durch einen weißen Pfeil im Editor dargestellt.</span><span class="sxs-lookup"><span data-stu-id="57994-316">It is represented by a white arrow in the editor.</span></span> <span data-ttu-id="57994-317">Stellen Sie sicher, dass der Pfeil von der Vorderseite der Schaltfläche entfernt wird:</span><span class="sxs-lookup"><span data-stu-id="57994-317">Make sure the arrow points away from the button's front face:</span></span>

<img src="../images/button/MRTK_Button_Custom3.png" width="450" alt="Pressable Custom3">

## <a name="see-also"></a><span data-ttu-id="57994-318">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="57994-318">See also</span></span>

* [<span data-ttu-id="57994-319">Interaktionsfähig</span><span class="sxs-lookup"><span data-stu-id="57994-319">Interactable</span></span>](interactable.md)
* [<span data-ttu-id="57994-320">Visuelle Designs</span><span class="sxs-lookup"><span data-stu-id="57994-320">Visual Themes</span></span>](visual-themes.md)
