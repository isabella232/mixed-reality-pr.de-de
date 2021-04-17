---
title: Interaktionsfähig
description: Übersicht über die Interaktionsfähige Skriptkomponente in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Interactable, Events,
ms.openlocfilehash: f141a394ec9395e0a27cc964caeb66654fb6fe08
ms.sourcegitcommit: 47c402dc8e588817ce60229bf019170fa36f3045
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2021
ms.locfileid: "107581562"
---
# <a name="interactable"></a><span data-ttu-id="c4e43-104">Interaktionsfähig</span><span class="sxs-lookup"><span data-stu-id="c4e43-104">Interactable</span></span>

![Interaktionsfähig](../images/interactable/InteractableExamples.png)

<span data-ttu-id="c4e43-106">Die [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) Komponente ist ein All-in-One-Container, damit jedes Objekt problemlos *interagierbar* und reaktionsfähig für Eingaben ist.</span><span class="sxs-lookup"><span data-stu-id="c4e43-106">The [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) component is an all-in-one container to make any object easily *interactable* and responsive to input.</span></span> <span data-ttu-id="c4e43-107">Interaktiv fungiert als Catch-All für alle Arten von Eingaben, einschließlich Berührung, Handlicht, Sprache usw. und trichtert diese Interaktionen in [Ereignisse](#events) und [visuelle Designantworten.](visual-themes.md)</span><span class="sxs-lookup"><span data-stu-id="c4e43-107">Interactable acts as a catch-all for all types of input including touch, hand rays, speech etc and funnel these interactions into [events](#events) and [visual theme](visual-themes.md) responses.</span></span> <span data-ttu-id="c4e43-108">Diese Komponente bietet eine einfache Möglichkeit, Schaltflächen zu erstellen, die Farbe von Objekten mit Fokus zu ändern und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="c4e43-108">This component provides an easy way to make buttons, change color on objects with focus, and more.</span></span>

## <a name="how-to-configure-interactable"></a><span data-ttu-id="c4e43-109">Konfigurieren von Interactable</span><span class="sxs-lookup"><span data-stu-id="c4e43-109">How to configure Interactable</span></span>

<span data-ttu-id="c4e43-110">Die -Komponente ermöglicht drei hauptteilliche Konfigurationsabschnitte:</span><span class="sxs-lookup"><span data-stu-id="c4e43-110">The component allows for three primary sections of configuration:</span></span>

1) [<span data-ttu-id="c4e43-111">Allgemeine Eingabekonfiguration</span><span class="sxs-lookup"><span data-stu-id="c4e43-111">General input configuration</span></span>](#general-input-settings)
1) <span data-ttu-id="c4e43-112">[Visuelle Designs](visual-themes.md) für mehrere GameObjects</span><span class="sxs-lookup"><span data-stu-id="c4e43-112">[Visual Themes](visual-themes.md) targeted against multiple GameObjects</span></span>
1) [<span data-ttu-id="c4e43-113">Ereignishandler</span><span class="sxs-lookup"><span data-stu-id="c4e43-113">Event handlers</span></span>](#events)

### <a name="general-input-settings"></a><span data-ttu-id="c4e43-114">Allgemeine Eingabeeinstellungen</span><span class="sxs-lookup"><span data-stu-id="c4e43-114">General input settings</span></span>

![Allgemeine interaktivierbare Einstellungen](../images/interactable/InputFeatures_short.png)

<span data-ttu-id="c4e43-116">**Status**</span><span class="sxs-lookup"><span data-stu-id="c4e43-116">**States**</span></span>

<span data-ttu-id="c4e43-117">*States* ist ein [ScriptableObject-Parameter,](https://docs.unity3d.com/Manual/class-ScriptableObject.html) der die Interaktionsphasen definiert, z. B. drücken oder beobachtet, für [interaktivierbare Profile](#interactable-profiles) und [visuelle Designs](visual-themes.md).</span><span class="sxs-lookup"><span data-stu-id="c4e43-117">*States* is a [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) parameter that defines the interactions phases, like press or observed, for [Interactable Profiles](#interactable-profiles) and [Visual Themes](visual-themes.md).</span></span>

<span data-ttu-id="c4e43-118">**DefaultInteractableStates** (Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset) ist standardmäßig im MRTK enthalten und ist der Standardparameter für *interaktivierbare* Komponenten.</span><span class="sxs-lookup"><span data-stu-id="c4e43-118">The **DefaultInteractableStates** (Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset) ships with MRTK out-of-box and is the default parameter for *Interactable* components.</span></span>

![StatusskriptableObject-Beispiel im Inspektor](../images/interactable/DefaultInteractableStates.png)

<span data-ttu-id="c4e43-120">Das *DefaultInteractableStates-Medienobjekt* enthält vier Zustände und verwendet die [`InteractableStates`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStates) Zustandsmodellimplementierungen.</span><span class="sxs-lookup"><span data-stu-id="c4e43-120">The *DefaultInteractableStates* asset contains four states and utilizes the [`InteractableStates`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStates) state model implementation.</span></span>

* <span data-ttu-id="c4e43-121">**Standard:** Es geschieht nichts, dies ist der isolierteste Basiszustand.</span><span class="sxs-lookup"><span data-stu-id="c4e43-121">**Default**: Nothing is happening, this is the most isolated base state.</span></span>

* <span data-ttu-id="c4e43-122">**Focus:** Auf das Objekt wird gezeigt.</span><span class="sxs-lookup"><span data-stu-id="c4e43-122">**Focus**: The object is being pointed at.</span></span> <span data-ttu-id="c4e43-123">Dies ist ein einzelner Zustand, es sind derzeit keine anderen Zustände festgelegt, aber der Rang Standard wird nicht festgelegt.</span><span class="sxs-lookup"><span data-stu-id="c4e43-123">This is a single state, no other states are currently set, but it will out rank Default.</span></span>

* <span data-ttu-id="c4e43-124">**Drücken** Sie : Auf das Objekt wird gezeigt, und es wird eine Schaltfläche oder Hand gedrückt.</span><span class="sxs-lookup"><span data-stu-id="c4e43-124">**Press**: The object is being pointed at and a button or hand is pressing.</span></span> <span data-ttu-id="c4e43-125">Der Status "Press" (Drücken) rangiert auf den Plätzen Default (Standard) und Focus (Fokus).</span><span class="sxs-lookup"><span data-stu-id="c4e43-125">The Press state out ranks Default and Focus.</span></span> <span data-ttu-id="c4e43-126">Dieser Zustand wird auch als Fallback auf Physisches Drücken festgelegt.</span><span class="sxs-lookup"><span data-stu-id="c4e43-126">This state will also get set as a fallback to Physical Press.</span></span>

* <span data-ttu-id="c4e43-127">**Deaktiviert:** Die Schaltfläche sollte nicht interaktiv sein, und das visuelle Feedback gibt dem Benutzer auf, ob diese Schaltfläche aus irgendeinem Grund derzeit nicht verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="c4e43-127">**Disabled**: The button should not be interactive and visual feedback will let the user know if for some reason this button is not usable at this time.</span></span> <span data-ttu-id="c4e43-128">Theoretisch könnte der Deaktiviert-Zustand alle anderen Zustände enthalten, aber wenn Aktiviert deaktiviert ist, wird der Status Deaktiviert für alle anderen Zustände deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="c4e43-128">In theory, the disabled state could contain all other states, but when Enabled is turned off, the Disabled state trumps all other states.</span></span>

<span data-ttu-id="c4e43-129">Abhängig von der Reihenfolge in der Liste wird dem Zustand ein Bitwert (#) zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="c4e43-129">A bit value (#) is assigned to the state depending on the order in the list.</span></span>

> [!NOTE]
> <span data-ttu-id="c4e43-130">Im Allgemeinen wird empfohlen, **defaultInteractableStates** (Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset) beim Erstellen von *Interactable-Komponenten* zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="c4e43-130">It is generally recommended to utilize the **DefaultInteractableStates** (Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset) when creating *Interactable* components.</span></span>
>
> <span data-ttu-id="c4e43-131">Es sind jedoch 17 Interaktionsfähige Zustände verfügbar, die zum Erstellen von Designs verwendet werden können, obwohl einige von anderen Komponenten gesteuert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="c4e43-131">However, there are 17 Interactable states available that can be used to drive themes, though some are meant to be driven by other components.</span></span> <span data-ttu-id="c4e43-132">Im Folgenden finden Sie eine Liste mit integrierten Funktionen.</span><span class="sxs-lookup"><span data-stu-id="c4e43-132">Here is a list of those with built-in functionality.</span></span>
>
> * <span data-ttu-id="c4e43-133">Visited(Besucht): Es wurde auf "Interactable" geklickt.</span><span class="sxs-lookup"><span data-stu-id="c4e43-133">Visited: the Interactable has been clicked.</span></span>
> * <span data-ttu-id="c4e43-134">Umschalten: Die Schaltfläche befindet sich in einem umschalten Zustand, oder der Dimensionsindex ist eine ungerade Zahl.</span><span class="sxs-lookup"><span data-stu-id="c4e43-134">Toggled: The button is in a toggled state or Dimension index is an odd number.</span></span>
> * <span data-ttu-id="c4e43-135">Geste: Die Hand oder der Controller wurde gedrückt und von der ursprünglichen Position verschoben.</span><span class="sxs-lookup"><span data-stu-id="c4e43-135">Gesture: The hand or controller was pressed and has moved from the original position.</span></span>
> * <span data-ttu-id="c4e43-136">VoiceCommand: Ein Sprachbefehl wurde verwendet, um interactable auszulösen.</span><span class="sxs-lookup"><span data-stu-id="c4e43-136">VoiceCommand: A speech command was used to trigger the Interactable.</span></span>
> * <span data-ttu-id="c4e43-137">PhysicalTouch: Derzeit wird eine Toucheingabe erkannt, die zum Aktivieren [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="c4e43-137">PhysicalTouch: A touch input is currently detected, use [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) to enable.</span></span>
> * <span data-ttu-id="c4e43-138">Greifen: Eine Hand greift derzeit in die Begrenzungen des Objekts, verwenden Sie , [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) um zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="c4e43-138">Grab: A hand is currently grabbing in the bounds of the object, use [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) to enable</span></span>

<span data-ttu-id="c4e43-139">**Aktiviert**</span><span class="sxs-lookup"><span data-stu-id="c4e43-139">**Enabled**</span></span>

<span data-ttu-id="c4e43-140">Umschalten, ob ein Interactable-Gerät aktiviert wird oder nicht.</span><span class="sxs-lookup"><span data-stu-id="c4e43-140">Toggles whether an Interactable will start enabled or not.</span></span> <span data-ttu-id="c4e43-141">Dies entspricht dem [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) im Code.</span><span class="sxs-lookup"><span data-stu-id="c4e43-141">This corresponds to the [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) in code.</span></span>

<span data-ttu-id="c4e43-142">Die *aktivierte Eigenschaft eines Interactable-Objekts* ist anders als die aktivierte Eigenschaft, die über GameObject/Component konfiguriert wurde (d. h.</span><span class="sxs-lookup"><span data-stu-id="c4e43-142">An *Interactable's* enabled property is different than the enabled property configured via GameObject/Component (i.e</span></span> <span data-ttu-id="c4e43-143">SetActive usw.).</span><span class="sxs-lookup"><span data-stu-id="c4e43-143">SetActive etc).</span></span> <span data-ttu-id="c4e43-144">Wenn Sie GameObject oder *Interactable* MonoBehaviour deaktivieren, wird die Ausführung aller Elemente in der Klasse deaktiviert, einschließlich Eingaben, visuellen Designs, Ereignissen usw. Wenn Sie über [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) deaktivieren, wird die meisten Eingabebehandlungen deaktiviert, und die zugehörigen Eingabezustände werden zurücksetzungen.</span><span class="sxs-lookup"><span data-stu-id="c4e43-144">Disabling the GameObject or *Interactable* MonoBehaviour will disable everything in the class from running including input, visual themes, events, etc. Disabling via [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) will disable most input handling, resetting related input states.</span></span> <span data-ttu-id="c4e43-145">Die -Klasse wird jedoch weiterhin jeden Frame ausführen und Eingabeereignisse empfangen, die ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="c4e43-145">However, the class will still run every frame and receive input events which will be ignored.</span></span> <span data-ttu-id="c4e43-146">Dies ist nützlich, um interactable in einem deaktivierten Zustand anzuzeigen, der über visuelle Designs erfolgen kann.</span><span class="sxs-lookup"><span data-stu-id="c4e43-146">This is useful for displaying the Interactable in a disabled state which can be done via Visual Themes.</span></span> <span data-ttu-id="c4e43-147">Ein typisches Beispiel hierfür wäre eine Schaltfläche zum Übermitteln, die darauf wartet, dass alle erforderlichen Eingabefelder abgeschlossen sind.</span><span class="sxs-lookup"><span data-stu-id="c4e43-147">A typical example of this would be a submit button waiting for all the required input fields to be completed.</span></span>

<span data-ttu-id="c4e43-148">**Eingabeaktionen**</span><span class="sxs-lookup"><span data-stu-id="c4e43-148">**Input Actions**</span></span>

<span data-ttu-id="c4e43-149">Wählen Sie die [Eingabeaktion](../input/input-actions.md) aus der Eingabekonfiguration oder dem Controllerzuordnungsprofil aus, auf die die *interaktivierbare* Komponente reagieren soll.</span><span class="sxs-lookup"><span data-stu-id="c4e43-149">Select the [input action](../input/input-actions.md) from the input configuration or controller mapping profile that the *Interactable* component should react to.</span></span>

<span data-ttu-id="c4e43-150">Diese Eigenschaft kann zur Laufzeit im Code über konfiguriert [`Interactable.InputAction`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.InputAction) werden.</span><span class="sxs-lookup"><span data-stu-id="c4e43-150">This property can be configured at runtime in code via [`Interactable.InputAction`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.InputAction).</span></span>

<span data-ttu-id="c4e43-151">**IsGlobal**</span><span class="sxs-lookup"><span data-stu-id="c4e43-151">**IsGlobal**</span></span>

<span data-ttu-id="c4e43-152">True gibt an, dass die Komponente als globaler Eingabelistener für die ausgewählte [Eingabeaktion](../input/input-actions.md)markiert wird.</span><span class="sxs-lookup"><span data-stu-id="c4e43-152">If true, this will mark the component as a global input listener for the selected [input action](../input/input-actions.md).</span></span> <span data-ttu-id="c4e43-153">Das Standardverhalten ist false, wodurch die Eingabe auf diesen *interaktivierbaren* Collider/GameObject beschränkt wird.</span><span class="sxs-lookup"><span data-stu-id="c4e43-153">Default behavior is false which will restrict input to only this *Interactable* collider/GameObject.</span></span>

<span data-ttu-id="c4e43-154">Diese Eigenschaft kann zur Laufzeit im Code über konfiguriert [`Interactable.IsGlobal`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsGlobal) werden.</span><span class="sxs-lookup"><span data-stu-id="c4e43-154">This property can be configured at runtime in code via [`Interactable.IsGlobal`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsGlobal).</span></span>

<span data-ttu-id="c4e43-155">**Speech-Befehl**</span><span class="sxs-lookup"><span data-stu-id="c4e43-155">**Speech Command**</span></span>

<span data-ttu-id="c4e43-156">[Speech-Befehl](../input/speech.md)aus dem MRTK Speech Commands Profile, um ein OnClick-Ereignis für die Sprachinteraktion auszulösen.</span><span class="sxs-lookup"><span data-stu-id="c4e43-156">[Speech command](../input/speech.md), from the MRTK Speech Commands Profile, to trigger an OnClick event for voice interaction.</span></span>

<span data-ttu-id="c4e43-157">Diese Eigenschaft kann zur Laufzeit im Code über konfiguriert [`Interactable.VoiceCommand`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceCommand) werden.</span><span class="sxs-lookup"><span data-stu-id="c4e43-157">This property can be configured at runtime in code via [`Interactable.VoiceCommand`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceCommand).</span></span>

<span data-ttu-id="c4e43-158">**Erfordert Fokus**</span><span class="sxs-lookup"><span data-stu-id="c4e43-158">**Requires Focus**</span></span>

<span data-ttu-id="c4e43-159">True gibt an, dass der Sprachbefehl die *Interaktivierbare* nur aktiviert, wenn sie bereits den Fokus von einem Zeiger hat.</span><span class="sxs-lookup"><span data-stu-id="c4e43-159">If true, the voice command will only activate the *Interactable* if and only if it already has focus from a pointer.</span></span> <span data-ttu-id="c4e43-160">False gibt an, dass *interactable* als globaler Listener für den ausgewählten Sprachbefehl fungiert.</span><span class="sxs-lookup"><span data-stu-id="c4e43-160">If false, then the *Interactable* will act as a global listener for the selected voice command.</span></span> <span data-ttu-id="c4e43-161">Das Standardverhalten ist true, da es schwierig sein kann, mehrere globale Sprachlistener in einer Szene zu organisieren.</span><span class="sxs-lookup"><span data-stu-id="c4e43-161">The default behavior is true, as multiple global speech listeners can be difficult to organize in a scene.</span></span>

<span data-ttu-id="c4e43-162">Diese Eigenschaft kann zur Laufzeit im Code über konfiguriert [`Interactable.VoiceRequiresFocus`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceRequiresFocus) werden.</span><span class="sxs-lookup"><span data-stu-id="c4e43-162">This property can be configured at runtime in code via [`Interactable.VoiceRequiresFocus`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceRequiresFocus).</span></span>

<span data-ttu-id="c4e43-163">**Auswahlmodus**</span><span class="sxs-lookup"><span data-stu-id="c4e43-163">**Selection Mode**</span></span>

<span data-ttu-id="c4e43-164">Diese Eigenschaft definiert die Auswahllogik.</span><span class="sxs-lookup"><span data-stu-id="c4e43-164">This property defines the selection logic.</span></span> <span data-ttu-id="c4e43-165">Wenn auf *interaktivierbar* geklickt wird, wird es in eine nächste *Dimensionsebene* iteriert.</span><span class="sxs-lookup"><span data-stu-id="c4e43-165">When an *Interactable* is clicked, it iterates into a next *Dimension* level.</span></span> <span data-ttu-id="c4e43-166">*Dimensionen* ähneln dem Rang und definieren einen Zustand außerhalb von Eingaben (d. h.</span><span class="sxs-lookup"><span data-stu-id="c4e43-166">*Dimensions* is similar to rank and defines a state outside of inputs (i.e</span></span> <span data-ttu-id="c4e43-167">Fokus, Drücken usw.).</span><span class="sxs-lookup"><span data-stu-id="c4e43-167">focus, press etc).</span></span> <span data-ttu-id="c4e43-168">Sie sind nützlich zum Definieren von Umschaltzuständen oder anderen Zuständen mit mehreren Rang, die einer Schaltfläche zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="c4e43-168">They are useful for defining Toggle states or other multi-rank states associated with a button.</span></span> <span data-ttu-id="c4e43-169">Die aktuelle Dimensionsebene wird von `Interactable.DimensionIndex` nachverfolgt.</span><span class="sxs-lookup"><span data-stu-id="c4e43-169">The current Dimension level is tracked by `Interactable.DimensionIndex`.</span></span>

<span data-ttu-id="c4e43-170">Die verfügbaren Auswahlmodi sind:</span><span class="sxs-lookup"><span data-stu-id="c4e43-170">The selection modes available are:</span></span>

* <span data-ttu-id="c4e43-171">**Schaltfläche**  -  *Dimensionen* = 1, einfach klickbar *Interagierbar*</span><span class="sxs-lookup"><span data-stu-id="c4e43-171">**Button** - *Dimensions* = 1, simple clickable *Interactable*</span></span>
* <span data-ttu-id="c4e43-172">**Umschalten**  -  *Dimensionen* = 2, *Interagierbare Alternativen* zwischen on  / *off-Status*</span><span class="sxs-lookup"><span data-stu-id="c4e43-172">**Toggle** - *Dimensions* = 2, *Interactable* alternates between *on*/*off* state</span></span>
* <span data-ttu-id="c4e43-173">**Mehrere Dimensionen**  -  *Dimensionen* >= 3, jeder Klick erhöht die aktuelle Dimensionsebene + 1.</span><span class="sxs-lookup"><span data-stu-id="c4e43-173">**Multi-dimension** - *Dimensions* >= 3, every click increases the current dimension level + 1.</span></span> <span data-ttu-id="c4e43-174">Nützlich zum Definieren eines Schaltflächenzustands für eine Liste usw.</span><span class="sxs-lookup"><span data-stu-id="c4e43-174">Useful for defining a button state to a list, etc.</span></span>

<span data-ttu-id="c4e43-175">*Interagierbar* ermöglicht es auch, mehrere Designs pro Dimension *zu definieren.*</span><span class="sxs-lookup"><span data-stu-id="c4e43-175">*Interactable* also allows for multiple Themes to be defined per *Dimension*.</span></span> <span data-ttu-id="c4e43-176">Wenn z. B. *SelectionMode=Toggle* verwendet wird,  kann ein Design angewendet werden, wenn die Auswahl von *Interactable* aufgehoben wird, und ein anderes Design, wenn die Komponente *ausgewählt wird.*</span><span class="sxs-lookup"><span data-stu-id="c4e43-176">For example when *SelectionMode=Toggle*, one theme may be applied when the *Interactable* is *deselected* and another theme applied when the component is *selected*.</span></span>

<span data-ttu-id="c4e43-177">Der aktuelle Auswahlmodus kann zur Laufzeit über abgefragt [`Interactable.ButtonMode`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.ButtonMode) werden.</span><span class="sxs-lookup"><span data-stu-id="c4e43-177">The current Selection Mode can be queried at runtime via [`Interactable.ButtonMode`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.ButtonMode).</span></span> <span data-ttu-id="c4e43-178">Sie können den Modus zur Laufzeit aktualisieren, indem Sie die  [`Interactable.Dimensions`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.Dimensions) -Eigenschaft auf die gewünschte Funktionalität festlegen.</span><span class="sxs-lookup"><span data-stu-id="c4e43-178">Updating the mode at runtime can be achieved by setting the  [`Interactable.Dimensions`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.Dimensions) property to match the desired functionality.</span></span> <span data-ttu-id="c4e43-179">Darüber hinaus kann über auf die aktuelle Dimension zugegriffen werden, die für *den Umschaltmodus* und *den Mehrdimensionsmodus* nützlich [`Interactable.CurrentDimension`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.CurrentDimension) ist.</span><span class="sxs-lookup"><span data-stu-id="c4e43-179">Furthermore, the current dimension, useful for *Toggle* and *Multi-Dimension* modes, can be accessed via [`Interactable.CurrentDimension`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.CurrentDimension).</span></span>

### <a name="interactable-profiles"></a><span data-ttu-id="c4e43-180">Interagierbare Profile</span><span class="sxs-lookup"><span data-stu-id="c4e43-180">Interactable profiles</span></span>

<span data-ttu-id="c4e43-181">*Profile* sind Elemente, die eine Beziehung zwischen einem GameObject und einem [visuellen Design erstellen.](visual-themes.md)</span><span class="sxs-lookup"><span data-stu-id="c4e43-181">*Profiles* are items that create a relationship between a GameObject and a [Visual Theme](visual-themes.md).</span></span> <span data-ttu-id="c4e43-182">Das Profil definiert, welche Inhalte von einem Design bearbeitet werden, wenn eine [Zustandsänderung auftritt.](#general-input-settings)</span><span class="sxs-lookup"><span data-stu-id="c4e43-182">The profile defines what content will be manipulated by a theme when a [state change occurs](#general-input-settings).</span></span>

<span data-ttu-id="c4e43-183">Designs funktionieren ähnlich wie Materialien.</span><span class="sxs-lookup"><span data-stu-id="c4e43-183">Themes work a lot like materials.</span></span> <span data-ttu-id="c4e43-184">Sie sind skriptfähige Objekte, die eine Liste von Eigenschaften enthalten, die einem Objekt basierend auf dem aktuellen Zustand zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="c4e43-184">They are scriptable objects that contain a list of properties that will be assigned to an object based on the current state.</span></span> <span data-ttu-id="c4e43-185">Designs sind ebenfalls wiederverfetzbar und können mehreren *Interactable* UX-Objekten zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="c4e43-185">Themes are also re-usable and can be assigned across multiple *Interactable* UX objects.</span></span>

<span data-ttu-id="c4e43-186">**Reset On Destroy**</span><span class="sxs-lookup"><span data-stu-id="c4e43-186">**Reset On Destroy**</span></span>

<span data-ttu-id="c4e43-187">Visuelle Designs ändern verschiedene Eigenschaften für ein zielorientiertes GameObject, abhängig von der ausgewählten Klasse und dem Typ der Design-Engine.</span><span class="sxs-lookup"><span data-stu-id="c4e43-187">Visual themes modify various properties on a targeted GameObject, dependent on the class and type of theme engine selected.</span></span> <span data-ttu-id="c4e43-188">Wenn *Reset On Destroy true* ist, wenn die Interactable-Komponente zerstört wird, setzt die Komponente alle geänderten Eigenschaften von aktiven Designs auf ihre ursprünglichen Werte zurück.</span><span class="sxs-lookup"><span data-stu-id="c4e43-188">If *Reset On Destroy* is true when the Interactable component is destroyed, the component will reset all modified properties from active themes to their original values.</span></span> <span data-ttu-id="c4e43-189">Andernfalls belässt die interaktivierbare Komponente alle geänderten Eigenschaften bei ihrer Zerstörung.</span><span class="sxs-lookup"><span data-stu-id="c4e43-189">Otherwise, when destroyed, the Interactable component will leave any modified properties as-is.</span></span> <span data-ttu-id="c4e43-190">In diesem letzteren Fall bleibt der letzte Zustand von Werten erhalten, es sei denn, er wird von einer anderen externen Komponente geändert.</span><span class="sxs-lookup"><span data-stu-id="c4e43-190">In this latter case, the last state of values will persist unless altered by another external component.</span></span> <span data-ttu-id="c4e43-191">Die Standardeinstellung ist „false“.</span><span class="sxs-lookup"><span data-stu-id="c4e43-191">The default is false.</span></span>

<img src="../images/interactable/Profiles_Themes.png" width="450" alt="Profile theams">

## <a name="events"></a><span data-ttu-id="c4e43-192">Events</span><span class="sxs-lookup"><span data-stu-id="c4e43-192">Events</span></span>

<span data-ttu-id="c4e43-193">Jede *interaktivierbare* Komponente verfügt über ein *OnClick-Ereignis,* das ausgelöst wird, wenn die Komponente einfach ausgewählt wird.</span><span class="sxs-lookup"><span data-stu-id="c4e43-193">Every *Interactable* component has an *OnClick* event that fires when the component is simply selected.</span></span> <span data-ttu-id="c4e43-194">*Interactable* kann jedoch verwendet werden, um andere Eingabeereignisse als *nur OnClick* zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="c4e43-194">However, *Interactable* can be used to detect input events other than just *OnClick*.</span></span>

<span data-ttu-id="c4e43-195">Klicken Sie auf die Schaltfläche *Ereignis hinzufügen,* um einen neuen Typ der Ereignisempfängerdefinition hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="c4e43-195">Click the *Add Event* button to add a new type of Event Receiver definition.</span></span> <span data-ttu-id="c4e43-196">Wählen Sie nach dem Hinzufügen den gewünschten Ereignistyp aus.</span><span class="sxs-lookup"><span data-stu-id="c4e43-196">Once added, select the type of Event desired.</span></span>

![Beispiel für Ereignisse](../images/interactable/Events.png)<span data-ttu-id="c4e43-198">)</span><span class="sxs-lookup"><span data-stu-id="c4e43-198">)</span></span>

<span data-ttu-id="c4e43-199">Es gibt verschiedene Arten von Ereignisempfängern, um auf verschiedene Eingabetypen zu reagieren.</span><span class="sxs-lookup"><span data-stu-id="c4e43-199">There are different types of event receivers to respond to different types of input.</span></span> <span data-ttu-id="c4e43-200">MRTK wird mit den folgenden Empfängern ausgeliefert.</span><span class="sxs-lookup"><span data-stu-id="c4e43-200">MRTK ships with the following set of receivers out-of-box.</span></span>

* [`InteractableAudioReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAudioReceiver)
* [`InteractableOnClickReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnClickReceiver)
* [`InteractableOnFocusReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)
* [`InteractableOnGrabReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnGrabReceiver)
* [`InteractableOnHoldReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnHoldReceiver)
* [`InteractableOnPressReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnPressReceiver)
* [`InteractableOnToggleReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnToggleReceiver)
* [`InteractableOnTouchReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnTouchReceiver)

<span data-ttu-id="c4e43-201">Ein benutzerdefinierter Empfänger kann erstellt werden, indem eine neue Klasse erstellt wird, die [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) erweitert.</span><span class="sxs-lookup"><span data-stu-id="c4e43-201">A custom receiver can be created by making a new class that extends [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase).</span></span>

![Beispiel für ereignis umschaltende Empfänger](../images/interactable/Event_toggle.png)

<span data-ttu-id="c4e43-203">*Beispiel für einen Toggle-Ereignisempfänger*</span><span class="sxs-lookup"><span data-stu-id="c4e43-203">*Example of a Toggle Event Receiver*</span></span>

### <a name="interactable-receivers"></a><span data-ttu-id="c4e43-204">Interaktivierbare Empfänger</span><span class="sxs-lookup"><span data-stu-id="c4e43-204">Interactable receivers</span></span>

 <span data-ttu-id="c4e43-205">Mit der [`InteractableReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiver) -Komponente können Ereignisse außerhalb der *Interaktionsquelle* definiert werden.</span><span class="sxs-lookup"><span data-stu-id="c4e43-205">The [`InteractableReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiver) component allows for events to be defined outside of the source *Interactable* component.</span></span> <span data-ttu-id="c4e43-206">*InteractableReceiver* lauscht auf einen gefilterten Ereignistyp, der von einem anderen *interaktivierbaren* ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="c4e43-206">The *InteractableReceiver* will listen for a filtered event type fired by another *Interactable*.</span></span> <span data-ttu-id="c4e43-207">Wenn die *Interactable-Eigenschaft* nicht direkt zugewiesen ist, definiert die *Search Scope-Eigenschaft* die Richtung, in der *InteractableReceiver* auf Ereignisse lauscht, die sich entweder auf sich selbst, in einem übergeordneten Element oder in einem untergeordneten GameObject-Objekt befindet.</span><span class="sxs-lookup"><span data-stu-id="c4e43-207">If the *Interactable* property is not directly assigned, then the *Search Scope* property defines the direction the *InteractableReceiver* listens for events which is either on itself, in a parent, or in a child GameObject.</span></span>

<span data-ttu-id="c4e43-208">[`InteractableReceiverList`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiverList) verhält sich auf ähnliche Weise, aber für eine Liste übereinstimmender Ereignisse.</span><span class="sxs-lookup"><span data-stu-id="c4e43-208">[`InteractableReceiverList`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiverList) acts in a similar fashion but for a list of matching events.</span></span>

<img src="../images/interactable/InteractableReceiver.png" width="450" alt="Interactable reciver">

### <a name="create-custom-events"></a><span data-ttu-id="c4e43-209">Erstellen benutzerdefinierter Ereignisse</span><span class="sxs-lookup"><span data-stu-id="c4e43-209">Create custom events</span></span>

<span data-ttu-id="c4e43-210">Wie [visuelle Designs](visual-themes.md#custom-theme-engines)können Ereignisse erweitert werden, um beliebige Zustandsmuster zu erkennen oder Funktionen verfügbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="c4e43-210">Like [Visual Themes](visual-themes.md#custom-theme-engines), events can be extended to detect any state pattern or to expose functionality.</span></span>

<span data-ttu-id="c4e43-211">Benutzerdefinierte Ereignisse können auf zwei Arten erstellt werden:</span><span class="sxs-lookup"><span data-stu-id="c4e43-211">Custom events can be created in two main ways:</span></span>

1) <span data-ttu-id="c4e43-212">Erweitern Sie [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) die -Klasse, um ein benutzerdefiniertes Ereignis zu erstellen, das in der Dropdownliste der Ereignistypen angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="c4e43-212">Extend the [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) class to create a custom event that will show up in the dropdown list of event types.</span></span> <span data-ttu-id="c4e43-213">Standardmäßig wird ein Unity-Ereignis bereitgestellt, es können jedoch weitere Unity-Ereignisse hinzugefügt oder das Ereignis so festgelegt werden, dass Unity-Ereignisse ausblendet werden.</span><span class="sxs-lookup"><span data-stu-id="c4e43-213">A Unity event is provided by default, but additional Unity events can be added or the event can be set to hide Unity events.</span></span> <span data-ttu-id="c4e43-214">Diese Funktionalität ermöglicht es einem Designer, mit einem Techniker an einem Projekt zu arbeiten, um ein benutzerdefiniertes Ereignis zu erstellen, das der Designer im Editor einrichten kann.</span><span class="sxs-lookup"><span data-stu-id="c4e43-214">This functionality allows a designer to work with an engineer on a project to create a custom event that the designer can setup in the editor.</span></span>

1) <span data-ttu-id="c4e43-215">Erweitern Sie [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) die -Klasse, um eine vollständig benutzerdefinierte Ereigniskomponente zu erstellen, die sich im *Interactable-Objekt* oder einem anderen -Objekt befinden kann.</span><span class="sxs-lookup"><span data-stu-id="c4e43-215">Extend the [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) class to create a completely custom event component that can reside on the *Interactable* or another object.</span></span> <span data-ttu-id="c4e43-216">verweist [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) auf *interactable,* um Zustandsänderungen zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="c4e43-216">The [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) will reference the *Interactable* to detect state changes.</span></span>

#### <a name="example-of-extending-receiverbase"></a><span data-ttu-id="c4e43-217">Beispiel für die Erweiterung `ReceiverBase`</span><span class="sxs-lookup"><span data-stu-id="c4e43-217">Example of extending `ReceiverBase`</span></span>

<span data-ttu-id="c4e43-218">Die -Klasse zeigt Statusinformationen zu einem Interactable-Ereignis an und ist ein Beispiel für das Erstellen eines [`CustomInteractablesReceiver`](xref:Microsoft.MixedReality.Toolkit.UI) benutzerdefinierten Ereignisempfängers. </span><span class="sxs-lookup"><span data-stu-id="c4e43-218">The [`CustomInteractablesReceiver`](xref:Microsoft.MixedReality.Toolkit.UI) class displays status information about an *Interactable* and is an example of how to create a custom Event Receiver.</span></span>

```c#
public CustomInteractablesReceiver(UnityEvent ev) : base(ev, "CustomEvent")
{
    HideUnityEvents = true; // hides Unity events in the receiver - meant to be code only
}
```

<span data-ttu-id="c4e43-219">Die folgenden Methoden sind nützlich, um beim Erstellen eines benutzerdefinierten Ereignisempfängers zu überschreiben/zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="c4e43-219">The following methods are useful to override/implement when creating a custom Event Receiver.</span></span> <span data-ttu-id="c4e43-220">[`ReceiverBase.OnUpdate()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) ist eine abstrakte Methode, die verwendet werden kann, um Zustandsmuster/Übergänge zu erkennen.</span><span class="sxs-lookup"><span data-stu-id="c4e43-220">[`ReceiverBase.OnUpdate()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) is an abstract method that can be used to detect state patterns/transitions.</span></span> <span data-ttu-id="c4e43-221">Darüber hinaus sind die [`ReceiverBase.OnVoiceCommand()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) Methoden und [`ReceiverBase.OnClick()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) nützlich, um benutzerdefinierte Ereignislogik zu erstellen, wenn *Interactable* ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="c4e43-221">Furthermore, the [`ReceiverBase.OnVoiceCommand()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) and [`ReceiverBase.OnClick()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) methods are useful for creating custom event logic when the *Interactable* is selected.</span></span>

```c#
public override void OnUpdate(InteractableStates state, Interactable source)
{
    if (state.CurrentState() != lastState)
    {
        // the state has changed, do something new
        lastState = state.CurrentState();
        ...
    }
}

public virtual void OnVoiceCommand(InteractableStates state, Interactable source,
                                    string command, int index = 0, int length = 1)
{
    base.OnVoiceCommand(state, source, command, index, length);
    // voice command called, perform some action
}  

public virtual void OnClick(InteractableStates state,
                            Interactable source,
                            IMixedRealityPointer pointer = null)
{
    base.OnClick(state, source);
    // click called, perform some action
}
```

##### <a name="displaying-custom-event-receiver-fields-in-the-inspector"></a><span data-ttu-id="c4e43-222">Anzeigen benutzerdefinierter Ereignisempfängerfelder im Inspektor</span><span class="sxs-lookup"><span data-stu-id="c4e43-222">Displaying custom event receiver fields in the inspector</span></span>

<span data-ttu-id="c4e43-223">*ReceiverBase-Skripts* [`InspectorField`](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.InspectorField) verwenden Attribute, um benutzerdefinierte Eigenschaften im Inspektor verfügbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="c4e43-223">*ReceiverBase* scripts use [`InspectorField`](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.InspectorField) attributes to expose custom properties in the inspector.</span></span> <span data-ttu-id="c4e43-224">Hier sehen Sie ein Beispiel für Vector3, eine benutzerdefinierte Eigenschaft mit QuickInfo und Bezeichnungsinformationen.</span><span class="sxs-lookup"><span data-stu-id="c4e43-224">Here's an example of Vector3, a custom property with tooltip and label information.</span></span> <span data-ttu-id="c4e43-225">Diese Eigenschaft wird im Inspektor als konfigurierbar angezeigt, wenn ein *Interactable* GameObject ausgewählt ist und der zugeordnete *Ereignisempfängertyp* hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="c4e43-225">This property will show up as configurable in the inspector when an *Interactable* GameObject is selected and has the associated *Event Receiver* type added.</span></span>

```c#
[InspectorField(Label = "<Property label>",Tooltip = "<Insert tooltip info>",Type = InspectorField.FieldTypes.Vector3)]
public Vector3 EffectOffset = Vector3.zero;
```

## <a name="how-to-use-interactable"></a><span data-ttu-id="c4e43-226">Verwenden von Interactable</span><span class="sxs-lookup"><span data-stu-id="c4e43-226">How to use Interactable</span></span>

### <a name="building-a-simple-button"></a><span data-ttu-id="c4e43-227">Erstellen einer einfachen Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="c4e43-227">Building a simple button</span></span>

<span data-ttu-id="c4e43-228">Sie können eine einfache Schaltfläche erstellen, indem Sie die *Interactable-Komponente* einem GameObject hinzufügen, das für den Empfang von Eingabeereignissen konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="c4e43-228">One can create a simple button by adding the *Interactable* component to a GameObject that is configured to receive input events.</span></span> <span data-ttu-id="c4e43-229">Es kann ein Collider darauf oder auf einem untergeordneten -Paar zum Empfangen von Eingaben verfügen.</span><span class="sxs-lookup"><span data-stu-id="c4e43-229">It can have a collider on it or on a child to receive input.</span></span> <span data-ttu-id="c4e43-230">Wenn Sie *Interactable mit* einem auf der Unity-Benutzeroberfläche basierenden GameObjects verwenden, sollte es sich unter dem Canvas GameObject-Objekt befindet.</span><span class="sxs-lookup"><span data-stu-id="c4e43-230">If using *Interactable* with a Unity UI based GameObjects, it should be under the Canvas GameObject.</span></span>

<span data-ttu-id="c4e43-231">Gehen Sie mit der Schaltfläche noch einen Schritt weiter, indem Sie ein neues Profil erstellen, das GameObject selbst zuweisen und ein neues Design erstellen.</span><span class="sxs-lookup"><span data-stu-id="c4e43-231">Take the button one step further, by creating a new profile, assigning the GameObject itself and creating a new theme.</span></span> <span data-ttu-id="c4e43-232">Verwenden Sie darüber hinaus das *OnClick-Ereignis,* um etwas zu bewirken.</span><span class="sxs-lookup"><span data-stu-id="c4e43-232">Furthermore, use the *OnClick* event to make something happen.</span></span>

> [!NOTE]
> <span data-ttu-id="c4e43-233">Damit eine [Schaltfläche gedrückt werden kann,](button.md) ist die [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) Komponente erforderlich.</span><span class="sxs-lookup"><span data-stu-id="c4e43-233">Making a [button pressable](button.md) requires the [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) component.</span></span> <span data-ttu-id="c4e43-234">Darüber hinaus wird die [`PhysicalPressEventRouter`](xref:Microsoft.MixedReality.Toolkit.PhysicalPressEventRouter) -Komponente benötigt, um Ereignisse zur *Interaktivierbaren* Komponente zu trichtern.</span><span class="sxs-lookup"><span data-stu-id="c4e43-234">Additionally, the [`PhysicalPressEventRouter`](xref:Microsoft.MixedReality.Toolkit.PhysicalPressEventRouter) component is needed to funnel press events to the *Interactable* component.</span></span>

### <a name="creating-toggle-and-multi-dimension-buttons"></a><span data-ttu-id="c4e43-235">Erstellen von Umschaltflächen und Schaltflächen mit mehreren Dimensionen</span><span class="sxs-lookup"><span data-stu-id="c4e43-235">Creating toggle and multi-dimension buttons</span></span>

#### <a name="toggle-button"></a><span data-ttu-id="c4e43-236">Umschalter</span><span class="sxs-lookup"><span data-stu-id="c4e43-236">Toggle button</span></span>

<span data-ttu-id="c4e43-237">Um eine Schaltfläche umschaltfähig zu machen, ändern Sie das [`Selection Mode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) Feld in den Typ `Toggle` .</span><span class="sxs-lookup"><span data-stu-id="c4e43-237">To make a button Toggle-able, change the [`Selection Mode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) field to type `Toggle`.</span></span> <span data-ttu-id="c4e43-238">Im Abschnitt *Profile* wird ein neues umgeschaltetes Design für jedes Profil hinzugefügt, das verwendet wird, wenn *interaktivierbar* eingeschaltet wird.</span><span class="sxs-lookup"><span data-stu-id="c4e43-238">In the *Profiles* section, a new toggled theme is added for each profile that is used when the *Interactable* is toggled on.</span></span>

<span data-ttu-id="c4e43-239">Während auf [`SelectionMode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) Umschalten festgelegt ist, kann das *Kontrollkästchen IsToggled* verwendet werden, um den Standardwert des Steuerelements bei der Laufzeitinitialisierung festzulegen.</span><span class="sxs-lookup"><span data-stu-id="c4e43-239">While the [`SelectionMode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) is set to Toggle, the *IsToggled* check box can be used to set the default value of the control at runtime initialization.</span></span>

<span data-ttu-id="c4e43-240">*CanSelect* bedeutet, dass *interactable* von *aus* zu *eins* wechseln kann, während *CanDeselect* die Umkehrung bedeutet.</span><span class="sxs-lookup"><span data-stu-id="c4e43-240">*CanSelect* means the *Interactable* can go from *off* to *on* while the *CanDeselect* means the inverse.</span></span>

![Beispiel für visuelle Designs zum Umschalten von Profilen](../images/interactable/Profile_toggle.png)

<span data-ttu-id="c4e43-242">Entwickler können die [`SetToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) Schnittstellen und [`IsToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) verwenden, um den Umschaltzustand eines *Interaktivierbaren* über Code abzurufen bzw. festzulegen.</span><span class="sxs-lookup"><span data-stu-id="c4e43-242">Developers can utilize the [`SetToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) and [`IsToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) interfaces to get/set the toggle state of an *Interactable* via code.</span></span>

```c#
// If using SelectionMode = Toggle (i.e Dimensions == 2)

// Make the Interactable selected and toggled on
myInteractable.IsToggled = true;

// Get whether the Interactable is selected or not
bool isSelected = myInteractable.IsToggled;
```

##### <a name="toggle-button-collection"></a><span data-ttu-id="c4e43-243">Schaltflächensammlung umschalten</span><span class="sxs-lookup"><span data-stu-id="c4e43-243">Toggle button collection</span></span>

<span data-ttu-id="c4e43-244">Es ist üblich, eine Liste von Umschaltflächen zu verwenden, bei denen nur eine zu einem bestimmten Zeitpunkt aktiv sein kann. Dies wird auch als radiale Gruppe oder Optionsfelder usw. bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="c4e43-244">It is common to have a list of toggle buttons where only one can be active at any given time, also known as a radial set or radio buttons etc.</span></span>

<span data-ttu-id="c4e43-245">Verwenden Sie die [`InteractableToggleCollection`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableToggleCollection) -Komponente, um diese Funktionalität zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="c4e43-245">Use the [`InteractableToggleCollection`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableToggleCollection) component to enable this functionality.</span></span> <span data-ttu-id="c4e43-246">Dieses Steuerelement stellt sicher, dass immer nur ein *Interaktivierbarer* eingeschaltet wird.</span><span class="sxs-lookup"><span data-stu-id="c4e43-246">This control ensures only one *Interactable* is toggled on at any given time.</span></span> <span data-ttu-id="c4e43-247">*RadialSet* (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/RadialSet.prefab) ist ebenfalls ein idealer Ausgangspunkt.</span><span class="sxs-lookup"><span data-stu-id="c4e43-247">The *RadialSet* (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/RadialSet.prefab) is also a great starting point out-of-box.</span></span>

<span data-ttu-id="c4e43-248">So erstellen Sie eine benutzerdefinierte radiale Schaltflächengruppe:</span><span class="sxs-lookup"><span data-stu-id="c4e43-248">To create a custom radial button group:</span></span>

1) <span data-ttu-id="c4e43-249">Erstellen mehrerer *interaktivierbarer* GameObjects/Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="c4e43-249">Create multiple *Interactable* GameObjects/buttons</span></span>
1) <span data-ttu-id="c4e43-250">Legen Sie jedes *Interaktivierbare* mit *SelectionMode* = Umschalten, *CanSelect* = true und *CanDeselect* = false fest.</span><span class="sxs-lookup"><span data-stu-id="c4e43-250">Set each *Interactable* with *SelectionMode* = Toggle, *CanSelect* = true, and *CanDeselect* = false</span></span>
1) <span data-ttu-id="c4e43-251">Erstellen Sie ein leeres übergeordnetes GameObject für alle *Interactables,* und fügen Sie die *InteractableToggleCollection-Komponente* hinzu.</span><span class="sxs-lookup"><span data-stu-id="c4e43-251">Create an empty parent GameObject over all the *Interactables* and add the *InteractableToggleCollection* component</span></span>
1) <span data-ttu-id="c4e43-252">Hinzufügen aller *Interaktivierbaren* zu *ToggleList* in *interactableToggleCollection*</span><span class="sxs-lookup"><span data-stu-id="c4e43-252">Add all *Interactables* to the *ToggleList* on the *InteractableToggleCollection*</span></span>
1) <span data-ttu-id="c4e43-253">Legen Sie die *InteractableToggleCollection.CurrentIndex-Eigenschaft* fest, um zu bestimmen, welche Schaltfläche beim Start standardmäßig ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="c4e43-253">Set the *InteractableToggleCollection.CurrentIndex* property to determine which button is selected by default at start</span></span>

<img src="../images/interactable/InteractableToggleCollection.png" width="450" alt="Toggle collection">

#### <a name="multi-dimensional-button"></a><span data-ttu-id="c4e43-254">Mehrdimensionale Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="c4e43-254">Multi-dimensional button</span></span>

<span data-ttu-id="c4e43-255">Der Auswahlmodus für mehrere Dimensionen wird verwendet, um sequenzielle Schaltflächen oder eine Schaltfläche mit mehr als zwei Schritten zu erstellen, z. B. das Steuern der Geschwindigkeit mit drei Werten, Fast (1x), Faster (2x) oder Fastest (3x).</span><span class="sxs-lookup"><span data-stu-id="c4e43-255">Multi-Dimension selection mode is used to create sequential buttons, or a button that has more than two steps, like controlling speed with three values, Fast (1x), Faster (2x) or Fastest (3x).</span></span>

<span data-ttu-id="c4e43-256">Wenn Dimensionen ein numerischer Wert sind, können bis zu 9 Designs hinzugefügt werden, um die Textbezeichnung oder Textur der Schaltfläche für jede Geschwindigkeitseinstellung mit einem anderen Design für jeden Schritt zu steuern.</span><span class="sxs-lookup"><span data-stu-id="c4e43-256">With dimensions being a numeric value, up to 9 themes can be added to control the text label or texture of the button for each speed setting, using a different theme for each of step.</span></span>

<span data-ttu-id="c4e43-257">Jedes Klickereignis bewegt sich zur Laufzeit `DimensionIndex` um 1, bis `Dimensions` der Wert erreicht ist.</span><span class="sxs-lookup"><span data-stu-id="c4e43-257">Every click event will advance the `DimensionIndex` by 1 at runtime until the `Dimensions` value is reached.</span></span> <span data-ttu-id="c4e43-258">Anschließend wird der Zyklus auf 0 zurückgesetzt.</span><span class="sxs-lookup"><span data-stu-id="c4e43-258">Then the cycle will reset to 0.</span></span>

![Beispiel für ein mehrdimensionales Profil](../images/interactable/Profile_multiDimensions.png)

<span data-ttu-id="c4e43-260">Entwickler können bewerten, [`DimensionIndex`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) um zu bestimmen, welche Dimension derzeit aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="c4e43-260">Developers can assess the [`DimensionIndex`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) to determine which dimension is currently active.</span></span>

```c#
// If using SelectionMode = Multi-dimension (i.e Dimensions >= 3)

//Access the current DimensionIndex
int currentDimension = myInteractable.CurrentDimension;

//Set the current DimensionIndex to 2
myInteractable.CurrentDimension = 2;

// Promote Dimension to next level
myInteractable.IncreaseDimension();
```

### <a name="create-interactable-at-runtime"></a><span data-ttu-id="c4e43-261">Erstellen von Interactable zur Laufzeit</span><span class="sxs-lookup"><span data-stu-id="c4e43-261">Create Interactable at runtime</span></span>

<span data-ttu-id="c4e43-262">*Interactable* kann jedem GameObject zur Laufzeit problemlos hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="c4e43-262">*Interactable* can be easily added to any GameObject at runtime.</span></span> <span data-ttu-id="c4e43-263">Im folgenden Beispiel wird veranschaulicht, wie ein Profil mit einem visuellen [Design zugewiesen wird.](visual-themes.md)</span><span class="sxs-lookup"><span data-stu-id="c4e43-263">The following example demonstrates how to assign a profile with a [visual theme](visual-themes.md).</span></span>

```c#
var interactableObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
var interactable = interactableObject.AddComponent<Interactable>();

// Get the default configuration for the Theme engine InteractableColorTheme
var newThemeType = ThemeDefinition.GetDefaultThemeDefinition<InteractableColorTheme>().Value;

// Define a color for every state in our Default Interactable States
newThemeType.StateProperties[0].Values = new List<ThemePropertyValue>()
{
    new ThemePropertyValue() { Color = Color.black},  // Default
    new ThemePropertyValue() { Color = Color.black}, // Focus
    new ThemePropertyValue() { Color = Random.ColorHSV()},   // Pressed
    new ThemePropertyValue() { Color = Color.black},   // Disabled
};

interactable.Profiles = new List<InteractableProfileItem>()
{
    new InteractableProfileItem()
    {
        Themes = new List<Theme>()
        {
            Interactable.GetDefaultThemeAsset(new List<ThemeDefinition>() { newThemeType })
        },
        Target = interactableObject,
    },
};

// Force the Interactable to be clicked
interactable.TriggerOnClick()
```

### <a name="interactable-events-via-code"></a><span data-ttu-id="c4e43-264">Interagierbare Ereignisse über Code</span><span class="sxs-lookup"><span data-stu-id="c4e43-264">Interactable events via code</span></span>

<span data-ttu-id="c4e43-265">Mit dem folgenden Beispiel können Sie dem [`Interactable.OnClick`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.OnClick) Basisereignis über Code eine Aktion hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="c4e43-265">One can add an action to the base [`Interactable.OnClick`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.OnClick) event via code with the following example.</span></span>

```c#
public static void AddOnClick(Interactable interactable)
{
    interactable.OnClick.AddListener(() => Debug.Log("Interactable clicked"));
}
```

<span data-ttu-id="c4e43-266">Verwenden Sie [`Interactable.AddReceiver<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) die -Funktion, um Ereignisempfänger dynamisch zur Laufzeit hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="c4e43-266">Use the [`Interactable.AddReceiver<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) function to add event receivers dynamically at runtime.</span></span>

<span data-ttu-id="c4e43-267">Der folgende Beispielcode veranschaulicht, wie Ein [InteractableOnFocusReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)hinzugefügt wird, der auf fokusfähige Eingabe/Beendigung lausiert und darüber hinaus Aktionscode definiert, der beim Auftreten der Ereignisinstanzen verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="c4e43-267">The example code below demonstrates how to add an [InteractableOnFocusReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), which listens for focus enter/exit, and furthermore define action code to perform when the event instances fire.</span></span>

```c#
public static void AddFocusEvents(Interactable interactable)
{
    var onFocusReceiver = interactable.AddReceiver<InteractableOnFocusReceiver>();

    onFocusReceiver.OnFocusOn.AddListener(() => Debug.Log("Focus on"));
    onFocusReceiver.OnFocusOff.AddListener(() => Debug.Log("Focus off"));
}
```

<span data-ttu-id="c4e43-268">Der folgende Beispielcode veranschaulicht, wie ein [InteractableOnToggleReceiver-Element](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)hinzugefügt wird, das auf ausgewählte/deaktivierte Zustandsübergänge für umschaltbare *Interactables-Elemente* lauselt und darüber hinaus aktionscode definiert, der beim Auftreten der Ereignisinstanzen durchzuführen ist.</span><span class="sxs-lookup"><span data-stu-id="c4e43-268">The example code below demonstrates how to add an [InteractableOnToggleReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), which listens for selected/deselected state transitions on toggle-able *Interactables*, and furthermore defines action code to perform when the event instances fire.</span></span>

```c#
public static void AddToggleEvents(Interactable interactable)
{
    var toggleReceiver = interactable.AddReceiver<InteractableOnToggleReceiver>();

    // Make the interactable have toggle capability, from code.
    // In the gui editor it's much easier
    interactable.Dimensions = 2;
    interactable.CanSelect = true;
    interactable.CanDeselect  = true;

    toggleReceiver.OnSelect.AddListener(() => Debug.Log("Toggle selected"));
    toggleReceiver.OnDeselect.AddListener(() => Debug.Log("Toggle un-selected"));
}
```

## <a name="see-also"></a><span data-ttu-id="c4e43-269">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="c4e43-269">See also</span></span>

* [<span data-ttu-id="c4e43-270">Visuelle Designs</span><span class="sxs-lookup"><span data-stu-id="c4e43-270">Visual Themes</span></span>](visual-themes.md)
* [<span data-ttu-id="c4e43-271">Eingabeaktionen</span><span class="sxs-lookup"><span data-stu-id="c4e43-271">Input Actions</span></span>](../input/input-actions.md)
* [<span data-ttu-id="c4e43-272">Speech-Befehle</span><span class="sxs-lookup"><span data-stu-id="c4e43-272">Speech Commands</span></span>](../input/speech.md)
* [<span data-ttu-id="c4e43-273">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="c4e43-273">Buttons</span></span>](button.md)
* [<span data-ttu-id="c4e43-274">MRTK-Standard-Shader</span><span class="sxs-lookup"><span data-stu-id="c4e43-274">MRTK Standard Shader</span></span>](../rendering/MRTK-standard-shader.md)
