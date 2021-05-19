---
title: Interaktives Element
description: Dokumentation zu InteractiveElement MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 02/22/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Interactive Element, Interactable
ms.openlocfilehash: 65f518c53414d68d3a9d2093cb427140cc65560b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144766"
---
# <a name="interactive-element-experimental"></a><span data-ttu-id="356ab-104">Interactive-Element [Experimentell]</span><span class="sxs-lookup"><span data-stu-id="356ab-104">Interactive Element [Experimental]</span></span>

<span data-ttu-id="356ab-105">Ein vereinfachter zentralisierter Einstiegspunkt zum MRTK-Eingabesystem.</span><span class="sxs-lookup"><span data-stu-id="356ab-105">A simplified centralized entry point to the MRTK input system.</span></span> <span data-ttu-id="356ab-106">Enthält Zustandsverwaltungsmethoden, Ereignisverwaltung und die Zustandseinstellungslogik für Kerninteraktionszustände.</span><span class="sxs-lookup"><span data-stu-id="356ab-106">Contains state management methods, event management and the state setting logic for Core Interaction States.</span></span>

<span data-ttu-id="356ab-107">Interactive Element ist ein experimentelles Feature, das in Unity 2019.3 und bis unterstützt wird, da es eine neue Funktion für Unity 2019.3 nutzt: [Serialize Reference](https://docs.unity3d.com/ScriptReference/SerializeReference.html).</span><span class="sxs-lookup"><span data-stu-id="356ab-107">Interactive Element is an experimental feature supported in Unity 2019.3 and up as it utilizes a capability new to Unity 2019.3: [Serialize Reference](https://docs.unity3d.com/ScriptReference/SerializeReference.html).</span></span>

### <a name="interactive-element-inspector"></a><span data-ttu-id="356ab-108">Interactive Element Inspector</span><span class="sxs-lookup"><span data-stu-id="356ab-108">Interactive Element Inspector</span></span>

<span data-ttu-id="356ab-109">Während des Wiedergabemodus stellt der Interactive Element Inspector visuelles Feedback bereit, das angibt, ob der aktuelle Zustand aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="356ab-109">During play mode, the Interactive Element inspector provides visual feedback that indicates whether or not the current state is active.</span></span> <span data-ttu-id="356ab-110">Wenn ein Zustand aktiv ist, wird er mit einer Cyanfarbe hervorgehoben.</span><span class="sxs-lookup"><span data-stu-id="356ab-110">If a state is active, it will be highlighted with a cyan color.</span></span>  <span data-ttu-id="356ab-111">Wenn der Zustand nicht aktiv ist, wird die Farbe nicht geändert.</span><span class="sxs-lookup"><span data-stu-id="356ab-111">If the state is not active, the color is not changed.</span></span> <span data-ttu-id="356ab-112">Die Zahlen neben den Zuständen im Inspektor sind die Zustandswerte. Wenn der Zustand aktiv ist, ist der Wert 1, wenn der Zustand nicht aktiv ist, ist der Wert 0.</span><span class="sxs-lookup"><span data-stu-id="356ab-112">The numbers next to the states in the inspector are the state values, if the state is active then the value is 1, if the state is not active the value is 0.</span></span>

![Interaktives Element mit virtueller Handinteraktion](../images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

## <a name="core-states"></a><span data-ttu-id="356ab-114">Kernzustände</span><span class="sxs-lookup"><span data-stu-id="356ab-114">Core States</span></span>

<span data-ttu-id="356ab-115">Interactive-Element enthält Kernzustände und unterstützt das Hinzufügen von [benutzerdefinierten Zuständen.](#custom-states)</span><span class="sxs-lookup"><span data-stu-id="356ab-115">Interactive Element contains core states and supports the addition of [custom states](#custom-states).</span></span>  <span data-ttu-id="356ab-116">Ein Kernzustand ist ein Zustand, für den bereits die Zustandseinstellungslogik in definiert `BaseInteractiveElement` ist.</span><span class="sxs-lookup"><span data-stu-id="356ab-116">A core state is one that already has the state setting logic defined in `BaseInteractiveElement`.</span></span> <span data-ttu-id="356ab-117">Im Folgenden sind die aktuellen eingabegesteuerten Kernzustände aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="356ab-117">The following is a list of the current input-driven core states:</span></span> 

### <a name="current-core-states"></a><span data-ttu-id="356ab-118">Aktuelle Kernzustände</span><span class="sxs-lookup"><span data-stu-id="356ab-118">Current Core States</span></span>

- [<span data-ttu-id="356ab-119">Standard</span><span class="sxs-lookup"><span data-stu-id="356ab-119">Default</span></span>](#default-state) 

<span data-ttu-id="356ab-120">Near and Far Interaction Core States (Kernzustände für nah und fernen Interaktion):</span><span class="sxs-lookup"><span data-stu-id="356ab-120">Near and Far Interaction Core States:</span></span>
- [<span data-ttu-id="356ab-121">Fokus</span><span class="sxs-lookup"><span data-stu-id="356ab-121">Focus</span></span>](#focus-state) 

<span data-ttu-id="356ab-122">Near Interaction Core States (Kernzustände der nahezuen Interaktion):</span><span class="sxs-lookup"><span data-stu-id="356ab-122">Near Interaction Core States:</span></span>

- [<span data-ttu-id="356ab-123">Fokus in der Nähe</span><span class="sxs-lookup"><span data-stu-id="356ab-123">Focus Near</span></span>](#focus-near-state)
- [<span data-ttu-id="356ab-124">Toucheingabe</span><span class="sxs-lookup"><span data-stu-id="356ab-124">Touch</span></span>](#touch-state)

<span data-ttu-id="356ab-125">Kernzustände der Ferninteraktion:</span><span class="sxs-lookup"><span data-stu-id="356ab-125">Far Interaction Core States:</span></span>
- [<span data-ttu-id="356ab-126">Focus Far</span><span class="sxs-lookup"><span data-stu-id="356ab-126">Focus Far</span></span>](#focus-far-state)
- [<span data-ttu-id="356ab-127">Wählen Sie Far (Weit) aus.</span><span class="sxs-lookup"><span data-stu-id="356ab-127">Select Far</span></span>](#select-far-state)

<span data-ttu-id="356ab-128">Andere Kernzustände:</span><span class="sxs-lookup"><span data-stu-id="356ab-128">Other Core States:</span></span>
- [<span data-ttu-id="356ab-129">Clicked</span><span class="sxs-lookup"><span data-stu-id="356ab-129">Clicked</span></span>](#clicked-state)
- [<span data-ttu-id="356ab-130">Ein- und Ausschalten</span><span class="sxs-lookup"><span data-stu-id="356ab-130">Toggle On and Toggle Off</span></span>](#toggle-on-and-toggle-off-state)
- [<span data-ttu-id="356ab-131">Speech-Schlüsselwort</span><span class="sxs-lookup"><span data-stu-id="356ab-131">Speech Keyword</span></span>](#speech-keyword-state)

### <a name="how-to-add-a-core-state-via-inspector"></a><span data-ttu-id="356ab-132">Hinzufügen eines Kernzustands über den Inspektor</span><span class="sxs-lookup"><span data-stu-id="356ab-132">How to Add a Core State via Inspector</span></span>

1. <span data-ttu-id="356ab-133">Navigieren Sie **im Inspektor für Interactive-Element** zu Kernzustand hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="356ab-133">Navigate to **Add Core State** in the inspector for Interactive Element.</span></span>

    ![Hinzufügen eines Kernzustands über inspector](../images/interactive-element/InEditor/InteractiveElementAddCoreState.png)


1. <span data-ttu-id="356ab-135">Wählen Sie die **Schaltfläche Status auswählen** aus, um den hinzuzufügenden Kernzustand auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="356ab-135">Select the **Select State** button to choose the core state to add.</span></span> <span data-ttu-id="356ab-136">Die Zustände im Menü werden nach Interaktionstyp sortiert.</span><span class="sxs-lookup"><span data-stu-id="356ab-136">The states in the menu are sorted by interaction type.</span></span>

    ![Hinzufügen eines Kernzustands über den Inspektor mit ausgewähltem Zustand](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectState.png)

1. <span data-ttu-id="356ab-138">Öffnen Sie das Foldout Ereigniskonfiguration, um die Ereignisse und Eigenschaften des Zustands anzeigen zu können.</span><span class="sxs-lookup"><span data-stu-id="356ab-138">Open the Event Configuration foldout to view the events and properties associated with the state.</span></span>

    ![Hinzufügen eines Kernzustands über inspector mit Ereigniskonfiguration](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectStateEventConfig.png)


### <a name="how-to-add-a-core-state-via-script"></a><span data-ttu-id="356ab-140">Hinzufügen eines Kernzustands per Skript</span><span class="sxs-lookup"><span data-stu-id="356ab-140">How to Add a Core State via Script</span></span>

<span data-ttu-id="356ab-141">Verwenden Sie die `AddNewState(stateName)` -Methode, um einen Kernzustand hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="356ab-141">Use the `AddNewState(stateName)` method to add a core state.</span></span> <span data-ttu-id="356ab-142">Verwenden Sie die -Enum, um eine Liste der verfügbaren `CoreInteractionState` Kernzustandsnamen zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="356ab-142">For a list of the available core state names, use the `CoreInteractionState` enum.</span></span>

```c#
// Add by name or add by CoreInteractionState enum to string

interactiveElement.AddNewState("SelectFar");

interactiveElement.AddNewState(CoreInteractionState.SelectFar.ToString());
```

### <a name="states-internal-structure"></a><span data-ttu-id="356ab-143">Interne Zuständestruktur</span><span class="sxs-lookup"><span data-stu-id="356ab-143">States Internal Structure</span></span> 

<span data-ttu-id="356ab-144">Die Zustände in Interactive Element sind vom Typ `InteractionState` .</span><span class="sxs-lookup"><span data-stu-id="356ab-144">The states in Interactive Element are of type `InteractionState`.</span></span>  <span data-ttu-id="356ab-145">Enthält `InteractionState` die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="356ab-145">An `InteractionState` contains the following properties:</span></span>

- <span data-ttu-id="356ab-146">**Name:** Der Name des Zustands.</span><span class="sxs-lookup"><span data-stu-id="356ab-146">**Name**: The name of the state.</span></span>
- <span data-ttu-id="356ab-147">**Wert:** Der Zustandswert.</span><span class="sxs-lookup"><span data-stu-id="356ab-147">**Value**: The state value.</span></span>  <span data-ttu-id="356ab-148">Wenn der Status "On" (Ein) ist, ist der Zustandswert 1.</span><span class="sxs-lookup"><span data-stu-id="356ab-148">If the state is on, the state value is 1.</span></span> <span data-ttu-id="356ab-149">Wenn der Status deaktiviert ist, ist der Zustandswert 0.</span><span class="sxs-lookup"><span data-stu-id="356ab-149">If the state is off, the state value is 0.</span></span>
- <span data-ttu-id="356ab-150">**Aktiv:** Gibt an, ob der Zustand derzeit aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="356ab-150">**Active**: Whether or not the state is currently active.</span></span> <span data-ttu-id="356ab-151">Der Wert für die Active-Eigenschaft ist true, wenn der Zustand eingeschaltet ist, false, wenn der Status deaktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="356ab-151">The value for the Active property is true when the state is on, false if the state is off.</span></span> 
- <span data-ttu-id="356ab-152">**Interaktionstyp:** Der Interaktionstyp eines Zustands ist der Typ der Interaktion, für die ein Zustand vorgesehen ist.</span><span class="sxs-lookup"><span data-stu-id="356ab-152">**Interaction Type**: The Interaction Type of a state is the type of interaction a state is intended for.</span></span> 
  - <span data-ttu-id="356ab-153">`None`: Unterstützt keine Form der Eingabeinteraktion.</span><span class="sxs-lookup"><span data-stu-id="356ab-153">`None`: Does not support any form of input interaction.</span></span>
  - <span data-ttu-id="356ab-154">`Near`: Unterstützung der Interaktion in der Nähe.</span><span class="sxs-lookup"><span data-stu-id="356ab-154">`Near`: Near interaction support.</span></span> <span data-ttu-id="356ab-155">Eingaben werden als nahezu interaktionsnah betrachtet, wenn eine artikulierte Hand direkten Kontakt mit einem anderen Spielobjekt hat, d. h. die Position, in der sich die artikulierte Hand in der Nähe der Position des Spielobjekts im Weltraum befindet.</span><span class="sxs-lookup"><span data-stu-id="356ab-155">Input is considered near interaction when an articulated hand has direct contact with another game object, i.e. the position the articulated hand is close to the position of the game object in world space.</span></span>
  - <span data-ttu-id="356ab-156">`Far`: Unterstützung der Ferninteraktion.</span><span class="sxs-lookup"><span data-stu-id="356ab-156">`Far`: Far interaction support.</span></span> <span data-ttu-id="356ab-157">Die Eingabe wird als Ferninteraktion betrachtet, wenn kein direkter Kontakt mit dem Spielobjekt erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="356ab-157">Input is considered far interaction when direct contact with the game object is not required.</span></span> <span data-ttu-id="356ab-158">Beispielsweise wird die Eingabe über controller ray oder gaze als Ferninteraktionseingabe betrachtet.</span><span class="sxs-lookup"><span data-stu-id="356ab-158">For example, input via controller ray or gaze is considered far interaction input.</span></span>
  - <span data-ttu-id="356ab-159">`NearAndFar`: Umfasst die Unterstützung von Nah- und Ferninteraktion.</span><span class="sxs-lookup"><span data-stu-id="356ab-159">`NearAndFar`: Encompasses both near and far interaction support.</span></span> 
  - <span data-ttu-id="356ab-160">`Other`: Zeigerunabhängige Interaktionsunterstützung.</span><span class="sxs-lookup"><span data-stu-id="356ab-160">`Other`: Pointer independent interaction support.</span></span>
- <span data-ttu-id="356ab-161">**Ereigniskonfiguration:** Die Ereigniskonfiguration für einen Zustand ist der Einstiegspunkt für das Serialisierungsereignisprofil.</span><span class="sxs-lookup"><span data-stu-id="356ab-161">**Event Configuration**: The event configuration for a state is the serialized events profile entry point.</span></span> 

<span data-ttu-id="356ab-162">Alle diese Eigenschaften werden intern in der festgelegt, die `State Manager` im Interactive-Element enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="356ab-162">All of these properties are set internally in the `State Manager` contained in Interactive Element.</span></span> <span data-ttu-id="356ab-163">Verwenden Sie zum Ändern von Zuzuständen die folgenden Hilfsmethoden:</span><span class="sxs-lookup"><span data-stu-id="356ab-163">For modification of states use the following helper methods:</span></span>

<span data-ttu-id="356ab-164">**Hilfsmethoden für Zustandseinstellungen**</span><span class="sxs-lookup"><span data-stu-id="356ab-164">**State Setting Helper Methods**</span></span>

```c# 
// Get the InteractionState
interactiveElement.GetState("StateName");

// Set a state value to 1/on
interactiveElement.SetStateOn("StateName");

// Set a state value to 0/off
interactiveElement.SetStateOff("StateName");

// Check if a state is present in the state list
interactiveElement.IsStatePresent("StateName");

// Check whether or not a state is active
interactiveElement.IsStateActive("StateName");

// Add a new state to the state list
interactiveElement.AddNewState("StateName");

// Remove a state from the state list
interactiveElement.RemoveState("StateName");
```

<span data-ttu-id="356ab-165">Das Abrufen der Ereigniskonfiguration eines Zustands ist spezifisch für den Zustand selbst.</span><span class="sxs-lookup"><span data-stu-id="356ab-165">Getting the event configuration of a state is specific to the state itself.</span></span> <span data-ttu-id="356ab-166">Jeder Kernzustand verfügt über einen bestimmten Ereigniskonfigurationstyp, der unten in den Abschnitten beschrieben wird, in denen die einzelnen Kernstatus beschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="356ab-166">Each core state has a specific event configuration type which is outlined below under the sections describing each core state.</span></span>

<span data-ttu-id="356ab-167">Hier ist ein generalisiertes Beispiel für das Abrufen der Ereigniskonfiguration eines Zustands:</span><span class="sxs-lookup"><span data-stu-id="356ab-167">Here is a generalized example of getting a state's event configuration:</span></span>

```c#
// T varies depending on the core state - the specific T's are specified under each of the core state sections
T stateNameEvents = interactiveElement.GetStateEvents<T>("StateName");
```

### <a name="default-state"></a><span data-ttu-id="356ab-168">Standardzustand</span><span class="sxs-lookup"><span data-stu-id="356ab-168">Default State</span></span>

<span data-ttu-id="356ab-169">Der Standardzustand ist für ein interaktives Element immer vorhanden.</span><span class="sxs-lookup"><span data-stu-id="356ab-169">The Default state is always present on an Interactive Element.</span></span>  <span data-ttu-id="356ab-170">Dieser Zustand ist nur aktiv, wenn alle anderen Status nicht aktiv sind.</span><span class="sxs-lookup"><span data-stu-id="356ab-170">This state will be active only when all other states are not active.</span></span>  <span data-ttu-id="356ab-171">Wenn ein anderer Zustand aktiv wird, wird der Standardzustand intern auf off festgelegt.</span><span class="sxs-lookup"><span data-stu-id="356ab-171">If any other state becomes active, then the Default state will be set to off internally.</span></span> 

<span data-ttu-id="356ab-172">Ein interaktives Element wird mit dem Standard- und Fokusstatus initialisiert, der in der Statusliste vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="356ab-172">An Interactive Element is initialized with the Default and Focus states present in the state list.</span></span> <span data-ttu-id="356ab-173">Der Standardzustand muss immer in der Statusliste vorhanden sein.</span><span class="sxs-lookup"><span data-stu-id="356ab-173">The Default state always needs to be present in the state list.</span></span> 

#### <a name="getting-default-state-events"></a><span data-ttu-id="356ab-174">Abrufen von Standardzustandsereignissen</span><span class="sxs-lookup"><span data-stu-id="356ab-174">Getting Default State Events</span></span>

<span data-ttu-id="356ab-175">Ereigniskonfigurationstyp für den Standardzustand: `StateEvents`</span><span class="sxs-lookup"><span data-stu-id="356ab-175">Event configuration type for the Default State: `StateEvents`</span></span>

```c#
StateEvents defaultEvents = interactiveElement.GetStateEvents<StateEvents>("Default");

defaultEvents.OnStateOn.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Default State On");
});

defaultEvents.OnStateOff.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Default State Off");
});
```

### <a name="focus-state"></a><span data-ttu-id="356ab-176">Fokuszustand</span><span class="sxs-lookup"><span data-stu-id="356ab-176">Focus State</span></span>

<span data-ttu-id="356ab-177">Der Fokuszustand ist ein nah- und ferner Interaktionszustand, der als Mixed Reality-Äquivalent zum Hovern bezeichnet werden kann.</span><span class="sxs-lookup"><span data-stu-id="356ab-177">The Focus state is a near and far interaction state that can be thought of as the mixed reality equivalent to hover.</span></span> <span data-ttu-id="356ab-178">Der Unterscheidungsfaktor zwischen nah und ferner Interaktion für den Fokuszustand ist der aktuelle aktive Zeigertyp.</span><span class="sxs-lookup"><span data-stu-id="356ab-178">The distinguishing factor between near and far interaction for the Focus state is the current active pointer type.</span></span>  <span data-ttu-id="356ab-179">Wenn der Zeigertyp für den Fokuszustand der Poke-Zeiger ist, wird die Interaktion als interaktionsnahe Interaktion betrachtet.</span><span class="sxs-lookup"><span data-stu-id="356ab-179">If the pointer type for the Focus state is the Poke Pointer, then the interaction is considered near interaction.</span></span>  <span data-ttu-id="356ab-180">Wenn der primäre Zeiger nicht der Poke-Zeiger ist, wird die Interaktion als ferne Interaktion betrachtet.</span><span class="sxs-lookup"><span data-stu-id="356ab-180">If the primary pointer is not the Poke Pointer, then the interaction is considered far interaction.</span></span> <span data-ttu-id="356ab-181">Der Fokuszustand ist standardmäßig im Interactive-Element vorhanden.</span><span class="sxs-lookup"><span data-stu-id="356ab-181">The Focus state is present in Interactive Element by default.</span></span>

<span data-ttu-id="356ab-182">**Fokuszustandsverhalten** 
 ![ Fokuszustand mit virtueller Handinteraktion](../images/interactive-element/InEditor/Gifs/FocusStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="356ab-182">**Focus State Behavior**
![Focus state with virtual hand interaction](../images/interactive-element/InEditor/Gifs/FocusStateEditor.gif)</span></span> 

<span data-ttu-id="356ab-183">**Fokuszustandsinspektor** 
 ![ Fokuszustand im Inpsector](../images/interactive-element/InEditor/FocusStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="356ab-183">**Focus State Inspector**
![Focus state in the Inpsector](../images/interactive-element/InEditor/FocusStateInspector.png)</span></span>

#### <a name="getting-focus-state-events&quot;></a><span data-ttu-id=&quot;356ab-184&quot;>Abrufen von Fokuszustandsereignissen</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;356ab-184&quot;>Getting Focus State Events</span></span>

<span data-ttu-id=&quot;356ab-185&quot;>Ereigniskonfigurationstyp für den Fokuszustand: `FocusEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;356ab-185&quot;>Event configuration type for the Focus State: `FocusEvents`</span></span>

```c#
FocusEvents focusEvents = interactiveElement.GetStateEvents<FocusEvents>(&quot;Focus");

focusEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Focus On");
});

focusEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Focus Off");
});
```

#### <a name="focus-near-vs-focus-far-behavior"></a><span data-ttu-id="356ab-186">Focus Near vs Focus Far Behavior</span><span class="sxs-lookup"><span data-stu-id="356ab-186">Focus Near vs Focus Far Behavior</span></span> 

![Fokus nah und fern mit virtueller Handinteraktion](../images/interactive-element/InEditor/Gifs/FocusNearFocusFar.gif)

### <a name="focus-near-state"></a><span data-ttu-id="356ab-188">Fokus nah am Zustand</span><span class="sxs-lookup"><span data-stu-id="356ab-188">Focus Near State</span></span>

<span data-ttu-id="356ab-189">Der Focus Near-Zustand wird festgelegt, wenn ein Fokusereignis ausgelöst wird, und der primäre Zeiger ist der Zeiger Der Zeiger ist ein Hinweis auf eine interaktionsnahe Interaktion.</span><span class="sxs-lookup"><span data-stu-id="356ab-189">The Focus Near state is set when a focus event is raised and the primary pointer is the Poke pointer, an indication of near interaction.</span></span> 

<span data-ttu-id="356ab-190">**Verhalten des fokussensischen Zustands** 
 ![ Fokus bei zustandsnäher Interaktion mit virtueller Hand](../images/interactive-element/InEditor/Gifs/FocusNearStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="356ab-190">**Focus Near State Behavior**
![Focus near state with virtual hand interaction](../images/interactive-element/InEditor/Gifs/FocusNearStateEditor.gif)</span></span> 

<span data-ttu-id="356ab-191">**Fokus Near State Inspector** 
 ![ Fokus in der Nähe der Komponente im Inspektor](../images/interactive-element/InEditor/FocusNearStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="356ab-191">**Focus Near State Inspector**
![Focus near component in the Inspector](../images/interactive-element/InEditor/FocusNearStateInspector.png)</span></span>

#### <a name="getting-focusnear-state-events&quot;></a><span data-ttu-id=&quot;356ab-192&quot;>Abrufen von FocusNear-Zustandsereignissen</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;356ab-192&quot;>Getting FocusNear State Events</span></span>

<span data-ttu-id=&quot;356ab-193&quot;>Ereigniskonfigurationstyp für den FocusNear-Zustand: `FocusEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;356ab-193&quot;>Event configuration type for the FocusNear State: `FocusEvents`</span></span>

```c#
FocusEvents focusNearEvents = interactiveElement.GetStateEvents<FocusEvents>(&quot;FocusNear");

focusNearEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Near Interaction Focus On");
});

focusNearEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Near Interaction Focus Off");
});
```

### <a name="focus-far-state"></a><span data-ttu-id="356ab-194">Focus Far State</span><span class="sxs-lookup"><span data-stu-id="356ab-194">Focus Far State</span></span>

<span data-ttu-id="356ab-195">Der Focus Far-Zustand wird festgelegt, wenn der primäre Zeiger nicht der Zeiger "Zeiger" ist.</span><span class="sxs-lookup"><span data-stu-id="356ab-195">The Focus Far state is set when the primary pointer is not the Poke pointer.</span></span>  <span data-ttu-id="356ab-196">Beispielsweise werden der Standardstrahlzeiger des Controllers und der GGV-Zeiger (Anvieren, Geste, Stimme) als Zeiger für fernen Interaktionszeiger betrachtet.</span><span class="sxs-lookup"><span data-stu-id="356ab-196">For example, the default controller ray pointer and the GGV (Gaze, Gesture, Voice) pointer are considered far interaction pointers.</span></span>

<span data-ttu-id="356ab-197">**Fokuszustandsverhalten** 
 ![ Fokuszustand weit entfernt mit virtueller Handinteraktion](../images/interactive-element/InEditor/Gifs/FocusFarStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="356ab-197">**Focus Far State Behavior**
![Focus state far with virtual hand interaction](../images/interactive-element/InEditor/Gifs/FocusFarStateEditor.gif)</span></span>

<span data-ttu-id="356ab-198">**Focus Far State Inspector** 
 ![ Focus far-Komponente im Inspektor](../images/interactive-element/InEditor/FocusFarStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="356ab-198">**Focus Far State Inspector**
![Focus far component in the Inspector](../images/interactive-element/InEditor/FocusFarStateInspector.png)</span></span>

#### <a name="getting-focus-far-state-events&quot;></a><span data-ttu-id=&quot;356ab-199&quot;>Abrufen von &quot;Focus Far State&quot;-Ereignissen</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;356ab-199&quot;>Getting Focus Far State Events</span></span>

<span data-ttu-id=&quot;356ab-200&quot;>Ereigniskonfigurationstyp für den FocusFar-Zustand: `FocusEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;356ab-200&quot;>Event configuration type for the FocusFar State: `FocusEvents`</span></span>

```c#
FocusEvents focusFarEvents = interactiveElement.GetStateEvents<FocusEvents>(&quot;FocusFar");

focusFarEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Focus On");
});

focusFarEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Focus Off");
});
```

### <a name="touch-state"></a><span data-ttu-id="356ab-201">Touchzustand</span><span class="sxs-lookup"><span data-stu-id="356ab-201">Touch State</span></span>

<span data-ttu-id="356ab-202">Der Touchzustand ist ein Nahezu-Interaktionszustand, der festgelegt wird, wenn eine artikulierte Hand das Objekt direkt berührt.</span><span class="sxs-lookup"><span data-stu-id="356ab-202">The Touch state is a near interaction state that is set when an articulated hand touches the object directly.</span></span>  <span data-ttu-id="356ab-203">Eine direkte Berührung bedeutet, dass der Zeigefinger der artikulierten Hand sehr nah an der Weltposition des Objekts liegt.</span><span class="sxs-lookup"><span data-stu-id="356ab-203">A direct touch means that the articulated hand's index finger is very close to the world position of the object.</span></span> <span data-ttu-id="356ab-204">Standardmäßig wird eine `NearInteractionTouchableVolume` Komponente an das -Objekt angefügt, wenn der Touch-Zustand der Statusliste hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="356ab-204">By default, a `NearInteractionTouchableVolume` component is attached to the object if the Touch state is added to the the state list.</span></span>  <span data-ttu-id="356ab-205">Zum Erkennen von Touchereignissen ist das Vorhandensein einer  `NearInteractionTouchableVolume` - oder `NearInteractionTouchable` -Komponente erforderlich.</span><span class="sxs-lookup"><span data-stu-id="356ab-205">The presence of a  `NearInteractionTouchableVolume` or `NearInteractionTouchable` component is required for detecting Touch events.</span></span>  <span data-ttu-id="356ab-206">Der Unterschied zwischen `NearInteractionTouchableVolume` und `NearInteractionTouchable` besteht darin, dass eine Berührung basierend `NearInteractionTouchableVolume` auf dem Collider des Objekts und innerhalb `NearInteractionTouchable` eines definierten Bereichs einer Ebene erkennt.</span><span class="sxs-lookup"><span data-stu-id="356ab-206">The difference between `NearInteractionTouchableVolume` and `NearInteractionTouchable` is that `NearInteractionTouchableVolume` detects a touch based on the collider of the object and `NearInteractionTouchable`detects touch within a defined area of a plane.</span></span>

<span data-ttu-id="356ab-207">**Touchzustandsverhalten** 
 ![ Touchzustand mit Interaktion mit virtueller Hand](../images/interactive-element/InEditor/Gifs/TouchStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="356ab-207">**Touch State Behavior**
![Touch state with virtual hand interaction](../images/interactive-element/InEditor/Gifs/TouchStateEditor.gif)</span></span>

<span data-ttu-id="356ab-208">**Touch State Inspector** 
 ![ Touchzustandskomponente im Inspektor](../images/interactive-element/InEditor/TouchStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="356ab-208">**Touch State Inspector**
![Touch state component in the Inspector](../images/interactive-element/InEditor/TouchStateInspector.png)</span></span>

#### <a name="getting-touch-state-events&quot;></a><span data-ttu-id=&quot;356ab-209&quot;>Abrufen von Touchzustandsereignissen</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;356ab-209&quot;>Getting Touch State Events</span></span>

<span data-ttu-id=&quot;356ab-210&quot;>Ereigniskonfigurationstyp für den Touchzustand: `TouchEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;356ab-210&quot;>Event configuration type for the Touch State: `TouchEvents`</span></span>

```c#
TouchEvents touchEvents = interactiveElement.GetStateEvents<TouchEvents>(&quot;Touch");

touchEvents.OnTouchStarted.AddListener((touchData) =>
{
    Debug.Log($"{gameObject.name} Touch Started");
});

touchEvents.OnTouchCompleted.AddListener((touchData) =>
{
    Debug.Log($"{gameObject.name} Touch Completed");
});

touchEvents.OnTouchUpdated.AddListener((touchData) =>
{
    Debug.Log($"{gameObject.name} Touch Updated");
});
```

### <a name="select-far-state"></a><span data-ttu-id="356ab-211">Wählen Sie Far State (Fernzustand) aus.</span><span class="sxs-lookup"><span data-stu-id="356ab-211">Select Far State</span></span>

<span data-ttu-id="356ab-212">Der Select Far-Status ist die `IMixedRealityPointerHandler` Oberfläche.</span><span class="sxs-lookup"><span data-stu-id="356ab-212">The Select Far state is the `IMixedRealityPointerHandler` surfaced.</span></span>  <span data-ttu-id="356ab-213">Bei diesem Zustand handelt es sich um einen zustandsweiten Interaktionszustand, der einen Weitklick (Tippen in die Luft) erkennt und die Verwendung von Ferninteraktionszeigern wie dem Standardmäßigen Controllerstrahlzeiger oder dem GGV-Zeiger durchfing.</span><span class="sxs-lookup"><span data-stu-id="356ab-213">This state is a far interaction state that detects far interaction click (air-tap) and holds through the use of far interaction pointers such as the default controller ray pointer or the GGV pointer.</span></span>  <span data-ttu-id="356ab-214">Der Status Far auswählen verfügt über eine Option unter dem Foldout für die Ereigniskonfiguration mit dem Namen `Global` .</span><span class="sxs-lookup"><span data-stu-id="356ab-214">The Select Far state has an option under the event configuration foldout named `Global`.</span></span> <span data-ttu-id="356ab-215">Wenn `Global` true ist, wird `IMixedRealityPointerHandler` als globaler Eingabehandler registriert.</span><span class="sxs-lookup"><span data-stu-id="356ab-215">If `Global` is true, then the `IMixedRealityPointerHandler` is registered as a global input handler.</span></span>  <span data-ttu-id="356ab-216">Der Fokus auf ein Objekt ist nicht erforderlich, um Eingabesystemereignisse auszulösen, wenn ein Handler als global registriert ist.</span><span class="sxs-lookup"><span data-stu-id="356ab-216">Focus on an object is not required to trigger input system events if a handler is registered as global.</span></span>  <span data-ttu-id="356ab-217">Wenn ein Benutzer z. B. wissen möchte, wann immer die Geste zum Tippen/Auswählen in die Luft ausgeführt wird, unabhängig vom Objekt im Fokus, legen Sie `Global` auf TRUE fest.</span><span class="sxs-lookup"><span data-stu-id="356ab-217">For example, if a user wants to know anytime the air-tap/select gesture is performed regardless of the object in focus, set `Global` to true.</span></span> 

<span data-ttu-id="356ab-218">**Wählen Sie Far State Behavior (Fernzustandsverhalten) aus.** 
 ![ Auswählen von "fern" mit virtueller Handinteraktion](../images/interactive-element/InEditor/Gifs/SelectFarStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="356ab-218">**Select Far State Behavior**
![Select far with virtual hand interaction](../images/interactive-element/InEditor/Gifs/SelectFarStateEditor.gif)</span></span>

<span data-ttu-id="356ab-219">**Wählen Sie Far State Inspector (Inspektor für fernen Zustand) aus** 
 ![ Auswählen der Far-Komponente im Inspektor](../images/interactive-element/InEditor/SelectFarStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="356ab-219">**Select Far State Inspector**
![Select far component in the Inspector](../images/interactive-element/InEditor/SelectFarStateInspector.png)</span></span>

#### <a name="getting-select-far-state-events&quot;></a><span data-ttu-id=&quot;356ab-220&quot;>Abrufen von Ereignissen der Option &quot;Far State&quot;</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;356ab-220&quot;>Getting Select Far State Events</span></span>

<span data-ttu-id=&quot;356ab-221&quot;>Ereigniskonfigurationstyp für selectFar State: `SelectFarEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;356ab-221&quot;>Event configuration type for the SelectFar State: `SelectFarEvents`</span></span>

```c#
SelectFarEvents selectFarEvents = interactiveElement.GetStateEvents<SelectFarEvents>(&quot;SelectFar");

selectFarEvents.OnSelectUp.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Up");
});

selectFarEvents.OnSelectDown.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Down");
});

selectFarEvents.OnSelectHold.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Hold");
});

selectFarEvents.OnSelectClicked.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Clicked");
});
```

### <a name="clicked-state"></a><span data-ttu-id="356ab-222">Clicked State</span><span class="sxs-lookup"><span data-stu-id="356ab-222">Clicked State</span></span>

<span data-ttu-id="356ab-223">Der Clicked-Status wird standardmäßig durch einen Fern-Interaktionsklick (Far-Status auswählen) ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="356ab-223">The Clicked state is triggered by a far interaction click (Select Far state) by default.</span></span>  <span data-ttu-id="356ab-224">Dieser Zustand wird intern auf "Ein" umgeschaltet, ruft das OnClicked-Ereignis auf und wird dann sofort in "Aus" umgeschaltet.</span><span class="sxs-lookup"><span data-stu-id="356ab-224">This state is internally switched to on, invokes the OnClicked event and then is immediately switched to off.</span></span> 

> [!NOTE]
> <span data-ttu-id="356ab-225">Das visuelle Feedback im Inspektor basierend auf der Zustandsaktivität ist für den Zustand "Geklickt" nicht vorhanden, da es sofort ein- und ausgeschaltet wird.</span><span class="sxs-lookup"><span data-stu-id="356ab-225">The visual feedback in the inspector based on state activity is not present for the Clicked state because it is switched on and then off immediately.</span></span> 

<span data-ttu-id="356ab-226">**Zustandsverhalten durch Klicken** 
 ![ Klicken auf den Zustand mit Interaktionen virtueller Hand](../images/interactive-element/InEditor/Gifs/ClickedStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="356ab-226">**Clicked State Behavior**
![Clicked state with virtual hand interactions](../images/interactive-element/InEditor/Gifs/ClickedStateEditor.gif)</span></span>

<span data-ttu-id="356ab-227">**Klicken Sie auf Zustandsinspektor.** 
 ![ Klicken Sie im Inspektor auf die Zustandskomponente.](../images/interactive-element/InEditor/ClickedStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="356ab-227">**Clicked State Inspector**
![Click state component in the Inspector](../images/interactive-element/InEditor/ClickedStateInspector.png)</span></span>

<span data-ttu-id="356ab-228">**Near and Far Clicked State Example**</span><span class="sxs-lookup"><span data-stu-id="356ab-228">**Near and Far Clicked State Example**</span></span>  
<span data-ttu-id="356ab-229">Der zustandsweise Klicken kann über zusätzliche Einstiegspunkte mithilfe der -Methode ausgelöst `interactiveElement.TriggerClickedState()` werden.</span><span class="sxs-lookup"><span data-stu-id="356ab-229">The clicked state can be triggered through additional entry points using the `interactiveElement.TriggerClickedState()` method.</span></span>  <span data-ttu-id="356ab-230">Wenn ein Benutzer beispielsweise möchte, dass auch ein Klick auf ein Objekt durch eine Touchinteraktion ausgelöst wird, fügt er die Methode als Listener im `TriggerClickedState()` Touchzustand hinzu.</span><span class="sxs-lookup"><span data-stu-id="356ab-230">For example, if a user wants a near interaction touch to trigger a click on an object as well, then they would add the `TriggerClickedState()` method as a listener in the touch state.</span></span>   

![Near and far state with virtual hand interactions (Nah- und Fernzustand mit Interaktionen virtueller Hand)](../images/interactive-element/InEditor/Gifs/NearFarClickedState.gif)

#### <a name="getting-clicked-state-events&quot;></a><span data-ttu-id=&quot;356ab-232&quot;>Abrufen von Statusereignissen, auf die geklickt wird</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;356ab-232&quot;>Getting Clicked State Events</span></span>

<span data-ttu-id=&quot;356ab-233&quot;>Ereigniskonfigurationstyp für den Zustand &quot;Geklickt&quot;: `ClickedEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;356ab-233&quot;>Event configuration type for the Clicked State: `ClickedEvents`</span></span>

```c#
ClickedEvents clickedEvent = interactiveElement.GetStateEvents<ClickedEvents>(&quot;Clicked");

clickedEvent.OnClicked.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Clicked");
});
```

### <a name="toggle-on-and-toggle-off-state"></a><span data-ttu-id="356ab-234">Ein- und Ausschalten des Zustands</span><span class="sxs-lookup"><span data-stu-id="356ab-234">Toggle On and Toggle Off state</span></span>

<span data-ttu-id="356ab-235">Die Zustände Ein und Aus umschalten sind ein Paar und müssen beide vorhanden sein, um das Umschaltverhalten zu steuern.</span><span class="sxs-lookup"><span data-stu-id="356ab-235">The Toggle On and Toggle Off states are a pair and both need to be present for toggle behavior.</span></span>  <span data-ttu-id="356ab-236">Standardmäßig werden die Zustände Ein ein- und Ausschalten durch einen Fernklick (Far-Status auswählen) ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="356ab-236">By default, the Toggle On and Toggle Off states are triggered through a far interaction click (Select Far state).</span></span>  <span data-ttu-id="356ab-237">Standardmäßig ist der Status Aus umschalten beim Start aktiv, was bedeutet, dass der Umschalter auf off initialisiert wird.</span><span class="sxs-lookup"><span data-stu-id="356ab-237">By default, the Toggle Off state is active on start, meaning that the toggle will be initialized to off.</span></span>  <span data-ttu-id="356ab-238">Wenn ein Benutzer möchte, dass der Status Ein beim Start aktiv ist, legen Sie im Status Ein ein auf `IsSelectedOnStart` TRUE fest.</span><span class="sxs-lookup"><span data-stu-id="356ab-238">If a user wants the Toggle On state to be active on start, then in the Toggle On state set `IsSelectedOnStart` to true.</span></span>

<span data-ttu-id="356ab-239">**ToggleOn und Toggle Off State Behavior** 
 ![ Ein- und Ausschalten mit Interaktionen virtueller Hand](../images/interactive-element/InEditor/Gifs/ToggleOnToggleOffStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="356ab-239">**ToggleOn and Toggle Off State Behavior**
![Toggle on and off with virtual hand interactions](../images/interactive-element/InEditor/Gifs/ToggleOnToggleOffStateEditor.gif)</span></span>

<span data-ttu-id="356ab-240">**ToggleOn und Toggle Off State Inspector** 
 ![ Umschalten der Komponente im Inspektor](../images/interactive-element/InEditor/ToggleOnToggleOffStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="356ab-240">**ToggleOn and Toggle Off State Inspector**
![Toggle component in the Inspector](../images/interactive-element/InEditor/ToggleOnToggleOffStateInspector.png)</span></span>

<span data-ttu-id="356ab-241">**Near and Far Toggle States Example**</span><span class="sxs-lookup"><span data-stu-id="356ab-241">**Near and Far Toggle States Example**</span></span>  
<span data-ttu-id="356ab-242">Ähnlich wie beim Zustand "Geklickt" kann die Einstellung für den Umschaltzustand mehrere Einstiegspunkte mithilfe der -Methode `interactiveElement.SetToggleStates()` haben.</span><span class="sxs-lookup"><span data-stu-id="356ab-242">Similar to the Clicked state, toggle state setting can have multiple entry points using the `interactiveElement.SetToggleStates()` method.</span></span> <span data-ttu-id="356ab-243">Wenn ein Benutzer beispielsweise touch als zusätzlichen Einstiegspunkt zum Festlegen der Umschaltzustände verwenden möchte, fügt er die -Methode einem der Ereignisse im `SetToggleStates()` Touchzustand hinzu.</span><span class="sxs-lookup"><span data-stu-id="356ab-243">For example, if a user wants touch as an additional entry point to set the toggle states, then they add the `SetToggleStates()` method to one of the events in the Touch state.</span></span> 

![Nah- und Fern-Umschalten mit Interaktionen virtueller Hand](../images/interactive-element/InEditor/Gifs/NearFarToggleStates.gif)

#### <a name="getting-toggle-on-and-toggle-off-state-events&quot;></a><span data-ttu-id=&quot;356ab-245&quot;>Ein- und Ausschalten von Zustandsereignissen</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;356ab-245&quot;>Getting Toggle On and Toggle Off State Events</span></span>

<span data-ttu-id=&quot;356ab-246&quot;>Ereigniskonfigurationstyp für den ToggleOn-Zustand: `ToggleOnEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;356ab-246&quot;>Event configuration type for the ToggleOn State: `ToggleOnEvents`</span></span>  
<span data-ttu-id=&quot;356ab-247&quot;>Ereigniskonfigurationstyp für toggleOff State: `ToggleOffEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;356ab-247&quot;>Event configuration type for the ToggleOff State: `ToggleOffEvents`</span></span>

```c#
// Toggle On Events
ToggleOnEvents toggleOnEvent = interactiveElement.GetStateEvents<ToggleOnEvents>(&quot;ToggleOn");

toggleOnEvent.OnToggleOn.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Toggled On");
});

// Toggle Off Events
ToggleOffEvents toggleOffEvent = interactiveElement.GetStateEvents<ToggleOffEvents>("ToggleOff");

toggleOffEvent.OnToggleOff.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Toggled Off");
});
```

### <a name="speech-keyword-state"></a><span data-ttu-id="356ab-248">Speech-Schlüsselwortzustand</span><span class="sxs-lookup"><span data-stu-id="356ab-248">Speech Keyword State</span></span>

<span data-ttu-id="356ab-249">Der Zustand des Speech-Schlüsselworts lauscht auf die Schlüsselwörter, die im Mixed Reality Speech-Profil definiert sind.</span><span class="sxs-lookup"><span data-stu-id="356ab-249">The Speech Keyword state listens for the keywords defined in the Mixed Reality Speech Profile.</span></span> <span data-ttu-id="356ab-250">Jedes neue Schlüsselwort MUSS vor der Laufzeit im Sprachbefehlsprofil registriert werden (schritte unten).</span><span class="sxs-lookup"><span data-stu-id="356ab-250">Any new keyword MUST be registered in the speech command profile prior to runtime (steps below).</span></span> 

<span data-ttu-id="356ab-251">**Verhalten des Speech-Schlüsselwortzustands** 
 ![ Speech-Schlüsselwort mit virtueller Interaktion](../images/interactive-element/InEditor/Gifs/SpeechKeywordStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="356ab-251">**Speech Keyword State Behavior**
![Speech keyword with virtual interaction](../images/interactive-element/InEditor/Gifs/SpeechKeywordStateEditor.gif)</span></span>

<span data-ttu-id="356ab-252">**Sprachschlüsselwort-Zustandsinspektor** 
 ![ Speech-Schlüsselwortkomponente im Inspektor](../images/interactive-element/InEditor/SpeechKeywordStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="356ab-252">**Speech Keyword State Inspector**
![Speech keyword component in the Inspector](../images/interactive-element/InEditor/SpeechKeywordStateInspector.png)</span></span>

> [!NOTE]
> <span data-ttu-id="356ab-253">Der Speech-Schlüsselwortzustand wurde im Editor ausgelöst, indem die F5-Taste im gif oben gedrückt wurde.</span><span class="sxs-lookup"><span data-stu-id="356ab-253">The Speech Keyword state was triggered in editor by pressing the F5 key in the gif above.</span></span> <span data-ttu-id="356ab-254">Die Einrichtung in Editor-Tests für Sprache wird in den folgenden Schritten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="356ab-254">Setting up in editor testing for speech is outlined the steps below.</span></span> 

#### <a name="how-to-register-a-speech-commandkeyword"></a><span data-ttu-id="356ab-255">Registrieren eines Speech-Befehls/-Schlüsselworts</span><span class="sxs-lookup"><span data-stu-id="356ab-255">How to Register a Speech Command/Keyword</span></span>

1. <span data-ttu-id="356ab-256">Auswählen des **MixedRealityToolkit-Spielobjekts**</span><span class="sxs-lookup"><span data-stu-id="356ab-256">Select the **MixedRealityToolkit** game object</span></span>

1. <span data-ttu-id="356ab-257">Wählen Sie **Kopieren und Anpassen** des aktuellen Profils aus.</span><span class="sxs-lookup"><span data-stu-id="356ab-257">Select **Copy and Customize** the current profile</span></span>

1. <span data-ttu-id="356ab-258">Navigieren Sie zum Abschnitt Eingabe, und wählen **Sie Klonen** aus, um die Änderung des Eingabeprofils zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="356ab-258">Navigate to the Input section and select **Clone** to enable modification of the Input profile</span></span>

1. <span data-ttu-id="356ab-259">Scrollen Sie nach unten zum Abschnitt Speech im Eingabeprofil, und klonen Sie das Sprachprofil.</span><span class="sxs-lookup"><span data-stu-id="356ab-259">Scroll down to the Speech section in the Input profile and clone the Speech Profile</span></span>

    ![Speech-Schlüsselwortprofil im MRTK-Spielobjekt](../images/interactive-element/InEditor/SpeechKeywordProfileClone.png) 

1. <span data-ttu-id="356ab-261">Wählen Sie Neuen Sprachbefehl hinzufügen aus.</span><span class="sxs-lookup"><span data-stu-id="356ab-261">Select Add a New Speech Command</span></span>

    ![Hinzufügen eines neuen Speech-Schlüsselworts im MRTK-Profil](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeyword.png) 

1. <span data-ttu-id="356ab-263">Geben Sie das schlüsselwort new ein.</span><span class="sxs-lookup"><span data-stu-id="356ab-263">Enter the new keyword.</span></span> <span data-ttu-id="356ab-264">Optional: Ändern Sie KeyCode in F5 (oder einen anderen KeyCode), um Tests im Editor zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="356ab-264">Optional: Change the KeyCode to F5 (or another KeyCode) to allow for testing in editor.</span></span> 

    ![Konfigurieren des Speech-Schlüsselworts im MRTK-Profil](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeywordName.png) 

1. <span data-ttu-id="356ab-266">Wechseln Sie zurück zum Zustandsinspektor Interactive Element Speech-Schlüsselwort, und wählen **Sie Schlüsselwort hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="356ab-266">Go back to the Interactive Element Speech Keyword state inspector and select **Add Keyword**</span></span> 

    ![Hinzufügen eines Schlüsselworts zur interaktiven Elementkomponente](../images/interactive-element/InEditor/SpeechKeywordAddKeyword.png) 

    ![Schlüsselwortvalidierung und -registrierung](../images/interactive-element/InEditor/SpeechKeywordAddKeywordBlank.png) 

1. <span data-ttu-id="356ab-269">Geben Sie das neue Schlüsselwort ein, das gerade im Speech-Profil registriert wurde.</span><span class="sxs-lookup"><span data-stu-id="356ab-269">Enter the new keyword that was just registered in the Speech Profile</span></span>

    ![Eingeben eines neuen Sprachschlüsselworts](../images/interactive-element/InEditor/SpeechKeywordEnterKeyword.png) 


<span data-ttu-id="356ab-271">Um den Zustand des Speech-Schlüsselworts im Editor zu testen, drücken Sie den KeyCode, der in Schritt 6 (F5) definiert wurde, um das erkannte Speech-Schlüsselwortereignis zu simulieren.</span><span class="sxs-lookup"><span data-stu-id="356ab-271">To test the Speech Keyword state in editor, press the KeyCode that was defined in step 6 (F5) to simulate the speech keyword recognized event.</span></span>

#### <a name="getting-speech-keyword-state-events"></a><span data-ttu-id="356ab-272">Abrufen von Speech-Schlüsselwortzustandsereignissen</span><span class="sxs-lookup"><span data-stu-id="356ab-272">Getting Speech Keyword State Events</span></span>

<span data-ttu-id="356ab-273">Ereigniskonfigurationstyp für den SpeechKeyword-Zustand: `SpeechKeywordEvents`</span><span class="sxs-lookup"><span data-stu-id="356ab-273">Event configuration type for the SpeechKeyword State: `SpeechKeywordEvents`</span></span>

```c#
SpeechKeywordEvents speechKeywordEvents = interactiveElement.GetStateEvents<SpeechKeywordEvents>("SpeechKeyword");

speechKeywordEvents.OnAnySpeechKeywordRecognized.AddListener((speechEventData) =>
{
    Debug.Log($"{speechEventData.Command.Keyword} recognized");
});

// Get the "Change" Keyword event specifically
KeywordEvent keywordEvent = speechKeywordEvents.Keywords.Find((keyword) => keyword.Keyword == "Change");

keywordEvent.OnKeywordRecognized.AddListener(() =>
{ 
    Debug.Log("Change Keyword Recognized"); 
});
```

## <a name="custom-states"></a><span data-ttu-id="356ab-274">Benutzerdefinierte Zustände</span><span class="sxs-lookup"><span data-stu-id="356ab-274">Custom States</span></span>

### <a name="how-to-create-a-custom-state-via-inspector"></a><span data-ttu-id="356ab-275">Erstellen eines benutzerdefinierten Zustands über den Inspektor</span><span class="sxs-lookup"><span data-stu-id="356ab-275">How to Create a Custom State via Inspector</span></span> 

<span data-ttu-id="356ab-276">Der über inspector erstellte benutzerdefinierte Zustand wird mit der Standardzustandsereigniskonfiguration initialisiert.</span><span class="sxs-lookup"><span data-stu-id="356ab-276">The custom state created via inspector will be initialized with the default state event configuration.</span></span> <span data-ttu-id="356ab-277">Die Standardereigniskonfiguration für einen benutzerdefinierten Zustand ist vom Typ `StateEvents` und enthält die Ereignisse OnStateOn und OnStateOff.</span><span class="sxs-lookup"><span data-stu-id="356ab-277">The default event configuration for a custom state is of type `StateEvents` and contains the OnStateOn and OnStateOff events.</span></span>

1. <span data-ttu-id="356ab-278">Navigieren Sie **im Inspektor für interactive-Element** zu Benutzerdefinierten Zustand erstellen.</span><span class="sxs-lookup"><span data-stu-id="356ab-278">Navigate to **Create Custom State** in the inspector for Interactive Element.</span></span>
    
    ![Erstellen eines benutzerdefinierten Zustands](../images/interactive-element/InEditor/InteractiveElementCreateCustomState.png)

1. <span data-ttu-id="356ab-280">Geben Sie den Namen des neuen Zustands ein.</span><span class="sxs-lookup"><span data-stu-id="356ab-280">Enter the name of the new state.</span></span> <span data-ttu-id="356ab-281">Dieser Name muss eindeutig sein und darf nicht mit den vorhandenen Kernzuständen identisch sein.</span><span class="sxs-lookup"><span data-stu-id="356ab-281">This name must be unique and cannot be the same as the existing core states.</span></span> 
    
    ![Eingeben des Namens eines neuen benutzerdefinierten Zustands](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateName.png)

1. <span data-ttu-id="356ab-283">Wählen **Sie Statusname festlegen aus,** um der Statusliste hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="356ab-283">Select **Set State Name** to add to the state list.</span></span>
    
    ![Hinzufügen eines benutzerdefinierten Zustands zur Statusliste](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateNameSet.png)

   <span data-ttu-id="356ab-285">Dieser benutzerdefinierte Zustand wird mit der Standardereigniskonfiguration `StateEvents` initialisiert, die die Ereignisse und `OnStateOn` `OnStateOff` enthält.</span><span class="sxs-lookup"><span data-stu-id="356ab-285">This custom state is initialized with the default `StateEvents` event configuration which contains the `OnStateOn` and `OnStateOff` events.</span></span> <span data-ttu-id="356ab-286">Informationen zum Erstellen einer benutzerdefinierten Ereigniskonfiguration für einen neuen Zustand finden Sie unter Erstellen eines [benutzerdefinierten Zustands mit einer benutzerdefinierten Ereigniskonfiguration.](#creating-a-custom-state-with-a-custom-event-configuration)</span><span class="sxs-lookup"><span data-stu-id="356ab-286">To create a custom event configuration for a new state see: [Creating a Custom State with a Custom Event Configuration](#creating-a-custom-state-with-a-custom-event-configuration).</span></span>
    
    ![Neuer Status in der interaktiven Elementkomponente](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateEventConfig.png)


### <a name="how-to-create-a-custom-state-via-script&quot;></a><span data-ttu-id=&quot;356ab-288&quot;>Erstellen eines benutzerdefinierten Zustands per Skript</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;356ab-288&quot;>How to Create a Custom State via Script</span></span>

```c#
interactiveElement.AddNewState(&quot;MyNewState");

// A new state by default is initialized with a the default StateEvents configuration which contains the 
// OnStateOn and OnStateOff events

StateEvents myNewStateEvents = interactiveElement.GetStateEvents<StateEvents>("MyNewState");

myNewStateEvents.OnStateOn.AddListener(() =>
{
    Debug.Log($"MyNewState is On");
});

```

### <a name="creating-a-custom-state-with-a-custom-event-configuration"></a><span data-ttu-id="356ab-289">Erstellen eines benutzerdefinierten Zustands mit einer benutzerdefinierten Ereigniskonfiguration</span><span class="sxs-lookup"><span data-stu-id="356ab-289">Creating a Custom State with a Custom Event Configuration</span></span> 

<span data-ttu-id="356ab-290">Beispieldateien für einen benutzerdefinierten Zustand namens **Tastatur** befinden sich hier: MRTK\SDK\Experimental\InteractiveElement\Examples\Scripts\CustomStateExample</span><span class="sxs-lookup"><span data-stu-id="356ab-290">Example files for a custom state named **Keyboard** are located here: MRTK\SDK\Experimental\InteractiveElement\Examples\Scripts\CustomStateExample</span></span>

<span data-ttu-id="356ab-291">In den folgenden Schritten wird ein vorhandenes Beispiel für das Erstellen einer benutzerdefinierten Zustandsereigniskonfiguration und von Empfängerdateien beschrieben.</span><span class="sxs-lookup"><span data-stu-id="356ab-291">The following steps walk through an existing example of creating a custom state event configuration and receiver files.</span></span>

1. <span data-ttu-id="356ab-292">Stellen Sie sich einen Zustandsnamen vor.</span><span class="sxs-lookup"><span data-stu-id="356ab-292">Think of a state name.</span></span>  <span data-ttu-id="356ab-293">Dieser Name muss eindeutig sein und darf nicht mit den vorhandenen Kernzuständen identisch sein.</span><span class="sxs-lookup"><span data-stu-id="356ab-293">This name must be unique and cannot be the same as the existing core states.</span></span> <span data-ttu-id="356ab-294">Im Rahmen dieses Beispiels lautet der Statusname **Tastatur.**</span><span class="sxs-lookup"><span data-stu-id="356ab-294">For the purposes of this example, the state name is going to be **Keyboard**.</span></span>

1. <span data-ttu-id="356ab-295">Erstellen Sie zwei CS-Dateien mit dem Namen state name + "Receiver" und state name + "Events".</span><span class="sxs-lookup"><span data-stu-id="356ab-295">Create two .cs files named state name + "Receiver" and state name + "Events".</span></span> <span data-ttu-id="356ab-296">Die Benennung dieser Dateien wird intern berücksichtigt und muss der Konvention für Statusname und Ereignis/Empfänger entsprechen.</span><span class="sxs-lookup"><span data-stu-id="356ab-296">The naming of these files are taken into consideration internally and must follow the state name + Event/Receiver convention.</span></span> 

    ![Tastaturzustandsskripts](../images/interactive-element/InEditor/KeyboardStateFiles.png)

1. <span data-ttu-id="356ab-298">Weitere Informationen zum Dateiinhalt finden Sie in den Dateien KeyboardEvents.cs und KeyboardReceiver.cs.</span><span class="sxs-lookup"><span data-stu-id="356ab-298">See the KeyboardEvents.cs and KeyboardReceiver.cs files for more details on file contents.</span></span> <span data-ttu-id="356ab-299">Neue Ereigniskonfigurationsklassen müssen von `BaseInteractionEventConfiguration` erben, und neue Ereignisempfängerklassen müssen von `BaseEventReceiver` erben.</span><span class="sxs-lookup"><span data-stu-id="356ab-299">New event configuration classes must inherit from `BaseInteractionEventConfiguration` and new event receiver classes must inherit from `BaseEventReceiver`.</span></span>  <span data-ttu-id="356ab-300">Beispiele für die Statuseinstellung für den Tastaturzustand befinden sich in der `CustomStateSettingExample.cs` Datei.</span><span class="sxs-lookup"><span data-stu-id="356ab-300">Examples on state setting for the Keyboard state are located in the `CustomStateSettingExample.cs` file.</span></span> 

1. <span data-ttu-id="356ab-301">Fügen Sie den Zustand dem Interactive-Element mithilfe des Zustandsnamens hinzu. Der Zustandsname wird erkannt, wenn Ereigniskonfigurations- und Ereignisempfängerdateien vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="356ab-301">Add the state to Interactive Element using the state name, the state name will be recognized if event configuration and event receiver files exist.</span></span>  <span data-ttu-id="356ab-302">Die Eigenschaften in der benutzerdefinierten Ereigniskonfigurationsdatei sollten im Inspektor angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="356ab-302">The properties in the custom event configuration file should appear in the inspector.</span></span>

    <span data-ttu-id="356ab-303">![Hinzufügen eines benutzerdefinierten Zustands zum interaktiven Element ](../images/interactive-element/InEditor/AddKeyboardState.png) ![ Benutzerdefinierter Zustand, der im interaktiven Element erkannt wird](../images/interactive-element/InEditor/SetKeyboardStateName.png)</span><span class="sxs-lookup"><span data-stu-id="356ab-303">![Adding custom state to interactive element](../images/interactive-element/InEditor/AddKeyboardState.png) ![Custom state recognized in the interactive element](../images/interactive-element/InEditor/SetKeyboardStateName.png)</span></span>


1. <span data-ttu-id="356ab-304">Weitere Beispiele für Ereigniskonfigurations- und Ereignisempfängerdateien finden Sie in den Dateien unter diesen Pfaden:</span><span class="sxs-lookup"><span data-stu-id="356ab-304">For more examples of event configuration and event receiver files see the files at these paths:</span></span>    
- <span data-ttu-id="356ab-305">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventConfigurations</span><span class="sxs-lookup"><span data-stu-id="356ab-305">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventConfigurations</span></span>
- <span data-ttu-id="356ab-306">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventReceivers</span><span class="sxs-lookup"><span data-stu-id="356ab-306">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventReceivers</span></span>

## <a name="example-scene"></a><span data-ttu-id="356ab-307">Beispielszene</span><span class="sxs-lookup"><span data-stu-id="356ab-307">Example Scene</span></span> 

<span data-ttu-id="356ab-308">Die Beispielszene für Interactive Element + State Visualizer befindet sich hier: MRTK\SDK\Experimental\InteractiveElement\Examples\InteractiveElementExampleScene.unity</span><span class="sxs-lookup"><span data-stu-id="356ab-308">The example scene for Interactive Element + State Visualizer is located here: MRTK\SDK\Experimental\InteractiveElement\Examples\InteractiveElementExampleScene.unity</span></span>

![Beispielszene mit interaktivem Element und Zustands-Schnellansicht](../images/interactive-element/InEditor/ExampleScene.png)

### <a name="compressable-button"></a><span data-ttu-id="356ab-310">Schaltfläche "Komprimierbar"</span><span class="sxs-lookup"><span data-stu-id="356ab-310">Compressable Button</span></span>

<span data-ttu-id="356ab-311">Die Beispielszene enthält Prefabs mit den Namen und . Diese Prefabs spiegeln das Verhalten der Schaltflächen, die mit dem Interactive-Element und der `CompressableButton` `CompressableButtonToggle` Zustandsvis `PressableButtonHoloLens2` visualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="356ab-311">The example scene contains prefabs named `CompressableButton` and `CompressableButtonToggle`, these prefabs mirror the behavior of the `PressableButtonHoloLens2` buttons, that are constructed using Interactive Element and the State Visualizer.</span></span> <span data-ttu-id="356ab-312">Die `CompressableButton` Komponente ist derzeit eine Kombination von mit als `PressableButton`  +  `PressableButtonHoloLens2` `BaseInteractiveElement` Basisklasse.</span><span class="sxs-lookup"><span data-stu-id="356ab-312">The `CompressableButton` component is currently a combination of `PressableButton` + `PressableButtonHoloLens2` with `BaseInteractiveElement`as a base class.</span></span> 

## <a name="state-visualizer-experimental"></a><span data-ttu-id="356ab-313">Zustands-Schnellansicht [Experimentell]</span><span class="sxs-lookup"><span data-stu-id="356ab-313">State Visualizer [Experimental]</span></span>

<span data-ttu-id="356ab-314">Die Komponente State Visualizer fügt einem Objekt Animationen hinzu, die auf den in einer verknüpften Komponente des interaktiven Elements definierten Zuzuständen basieren.</span><span class="sxs-lookup"><span data-stu-id="356ab-314">The State Visualizer component adds animations to an object based on the states defined in a linked Interactive Element component.</span></span> <span data-ttu-id="356ab-315">Diese Komponente erstellt Animationsobjekte, platziert sie im Ordner MixedRealityToolkit.Generated und ermöglicht eine vereinfachte Keyframeeinstellung für Animationen, indem einem Zielspielobjekt Animatable-Eigenschaften hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="356ab-315">This component creates animation assets, places them in the MixedRealityToolkit.Generated folder and enables simplified animation keyframe setting through adding Animatable properties to a target game object.</span></span> <span data-ttu-id="356ab-316">Um Animationsübergänge zwischen Zuzuständen zu ermöglichen, wird ein AnimatorController-Objekt erstellt, und ein Standardzustandscomputer wird mit zugeordneten Parametern und allen Zustandsübergängen generiert.</span><span class="sxs-lookup"><span data-stu-id="356ab-316">To enable animation transitions between states, an Animator Controller asset is created and a default state machine is generated with associated parameters and any state transitions.</span></span>  <span data-ttu-id="356ab-317">Der Zustandsautomat kann im Unity-Fenster Animator angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="356ab-317">The state machine can be viewed in Unity's Animator window.</span></span>

### <a name="state-visualizer-and-unity-animation-system"></a><span data-ttu-id="356ab-318">Zustands-Schnellansicht und Unity-Animationssystem</span><span class="sxs-lookup"><span data-stu-id="356ab-318">State Visualizer and Unity Animation System</span></span>

<span data-ttu-id="356ab-319">Die Zustands-Schnellansicht nutzt derzeit das Unity-Animationssystem.</span><span class="sxs-lookup"><span data-stu-id="356ab-319">The State Visualizer currently leverages the Unity Animation System.</span></span> 

<span data-ttu-id="356ab-320">Wenn die **Schaltfläche Generate New Animation Clips** (Neue Animationsclips generieren) in der Zustandsansicht gedrückt wird, werden neue Animationsclipressourcen basierend auf den Zustandsnamen im Interactive-Element generiert und im Ordner MixedRealityToolkit.Generated platziert.</span><span class="sxs-lookup"><span data-stu-id="356ab-320">When the **Generate New Animation Clips** button in the State Visualizer is pressed, new animation clip assets are generated based on the state names in Interactive Element and are placed in the MixedRealityToolkit.Generated folder.</span></span> <span data-ttu-id="356ab-321">Die Animation Clip-Eigenschaft in jedem Zustandscontainer wird auf den zugeordneten Animationsclip festgelegt.</span><span class="sxs-lookup"><span data-stu-id="356ab-321">The Animation Clip property in each state container is set to the associated animation clip.</span></span>

![Animationsclips in der Zustands-Schnellansichtskomponente](../images/interactive-element/StateVisualizer/AnimationClips.png)

<span data-ttu-id="356ab-323">Außerdem [wird ein Animatorzustandscomputer](https://docs.unity3d.com/Manual/AnimationOverview.html) generiert, um reibungslose Übergänge zwischen Animationsclips zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="356ab-323">An [Animator State Machine](https://docs.unity3d.com/Manual/AnimationOverview.html) is also generated to manage smooth transitions between animation clips.</span></span>  <span data-ttu-id="356ab-324">Standardmäßig verwendet der Zustandscomputer den Zustand ["Any State",](https://docs.unity3d.com/Manual/class-State.html) um Übergänge zwischen einem beliebigen Zustand im interactive-Element zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="356ab-324">By default, the state machine utilizes the [Any State](https://docs.unity3d.com/Manual/class-State.html) to allow transitions between any state in Interactive Element.</span></span> 

<span data-ttu-id="356ab-325">[Zustandsansichten, die im Animator ausgelöst](https://docs.unity3d.com/Manual/AnimationParameters.html) werden, werden auch für jeden Zustand generiert. Die Triggerparameter werden in der Zustandsansicht verwendet, um eine Animation auszulösen.</span><span class="sxs-lookup"><span data-stu-id="356ab-325">[State visualizers triggered in the animator](https://docs.unity3d.com/Manual/AnimationParameters.html) are also generated for each state, the trigger parameters are used in the State Visualizer to trigger an animation.</span></span>

![Unity-Zustandsautomat](../images/interactive-element/StateVisualizer/UnityStateMachine.png)

### <a name="runtime-limitations"></a><span data-ttu-id="356ab-327">Runtime-Einschränkungen</span><span class="sxs-lookup"><span data-stu-id="356ab-327">Runtime Limitations</span></span> 

<span data-ttu-id="356ab-328">Die Zustandsansicht muss einem Objekt über den Inspektor hinzugefügt werden und kann nicht per Skript hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="356ab-328">The State Visualizer must be added to an object via the Inspector and cannot be added via script.</span></span>  <span data-ttu-id="356ab-329">Die Eigenschaften, die den AnimatorStateMachine/AnimationController ändern, sind in einem Editor-Namespace ( `UnityEditor.Animations` ) enthalten, der beim Erstellen der App entfernt wird.</span><span class="sxs-lookup"><span data-stu-id="356ab-329">The properties that modify the AnimatorStateMachine/AnimationController are contained in an editor namespace (`UnityEditor.Animations`) which get removed when the app is built.</span></span>

## <a name="how-to-use-the-state-visualizer"></a><span data-ttu-id="356ab-330">Verwenden der Zustandsansicht</span><span class="sxs-lookup"><span data-stu-id="356ab-330">How to use the State Visualizer</span></span>

1. <span data-ttu-id="356ab-331">Erstellen eines Cubes</span><span class="sxs-lookup"><span data-stu-id="356ab-331">Create a Cube</span></span>
1. <span data-ttu-id="356ab-332">Attach Interactive-Element</span><span class="sxs-lookup"><span data-stu-id="356ab-332">Attach Interactive Element</span></span>
1. <span data-ttu-id="356ab-333">Zustandsansicht anfügen</span><span class="sxs-lookup"><span data-stu-id="356ab-333">Attach State Visualizer</span></span>
1. <span data-ttu-id="356ab-334">Wählen Sie **Generate New Animation Clips (Neue Animationsclips generieren) aus.**</span><span class="sxs-lookup"><span data-stu-id="356ab-334">Select **Generate New Animation Clips**</span></span>

    ![Generieren neuer Animationsclips](../images/interactive-element/StateVisualizer/GenerateAnimationClips.png)

    ![Anzeigen generierter Animationsclips in schnellansichts- und interaktiven Elementkomponenten](../images/interactive-element/StateVisualizer/GenerateAnimationClips2.png)

1. <span data-ttu-id="356ab-337">Wählen Sie im Container Fokuszustand die Option **Ziel hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="356ab-337">In the Focus state container, select **Add Target**</span></span>

    ![Hinzufügen eines Zustandsansichtsziels](../images/interactive-element/StateVisualizer/AddTarget.png)

1. <span data-ttu-id="356ab-339">Ziehen Sie das aktuelle Spielobjekt in das Zielfeld.</span><span class="sxs-lookup"><span data-stu-id="356ab-339">Drag the current game object to the target field</span></span> 

    ![Festlegen des Statusvisuierungsziels](../images/interactive-element/StateVisualizer/SetTarget.png)

1. <span data-ttu-id="356ab-341">Öffnen des Foldouts cube Animatable Properties (Animatable-Eigenschaften)</span><span class="sxs-lookup"><span data-stu-id="356ab-341">Open the Cube Animatable Properties foldout</span></span>
1. <span data-ttu-id="356ab-342">Wählen Sie das Dropdownmenü Animatable property (Animatable-Eigenschaft) und **dann Color (Farbe) aus.**</span><span class="sxs-lookup"><span data-stu-id="356ab-342">Select the Animatable property drop down menu and select **Color**</span></span>

    ![Festlegen der Farbe der Zustandsansicht](../images/interactive-element/StateVisualizer/SetColor.png)

1. <span data-ttu-id="356ab-344">Wählen **Sie Add the Color Animatable Property (Animatable-Eigenschaft für Farbe hinzufügen)** aus.</span><span class="sxs-lookup"><span data-stu-id="356ab-344">Select **Add the Color Animatable Property**</span></span>

    ![Auswählen der animierbaren Eigenschaft für die Schnellansichtsfarbe](../images/interactive-element/StateVisualizer/SetColorProperty.png)

1. <span data-ttu-id="356ab-346">Auswählen einer Farbe</span><span class="sxs-lookup"><span data-stu-id="356ab-346">Choose a Color</span></span> 

    ![Auswählen einer Schnellansichtsfarbe aus dem Farbrad](../images/interactive-element/StateVisualizer/SetBlueColor.png)

1. <span data-ttu-id="356ab-348">Drücken Sie die Wiedergabe, und beobachten Sie die Farbänderung der Übergangsfarbe.</span><span class="sxs-lookup"><span data-stu-id="356ab-348">Press play and observe the transitional color change</span></span>

    ![Beispiel für farblich geänderte Übergangsfarbe mit Interaktion mit virtueller Hand](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

## <a name="animatable-properties"></a><span data-ttu-id="356ab-350">Eigenschaften, die animiert werden können</span><span class="sxs-lookup"><span data-stu-id="356ab-350">Animatable Properties</span></span>

<span data-ttu-id="356ab-351">Der Hauptzweck der animierbaren Eigenschaften besteht in der Vereinfachung der Keyframeeinstellung für Animationsclips.</span><span class="sxs-lookup"><span data-stu-id="356ab-351">The primary purpose of the Animatable Properties is to simplify animation clip keyframe setting.</span></span>  <span data-ttu-id="356ab-352">Wenn ein Benutzer mit dem Unity Animation System vertraut ist und lieber Keyframes direkt für die generierten Animationsclips festlegen möchte, kann er einem Zielobjekt einfach keine animierbaren Eigenschaften hinzufügen und den Clip im Unity-Fenster Animation (Windows > Animation > Animation) öffnen.</span><span class="sxs-lookup"><span data-stu-id="356ab-352">If a user is familiar with the Unity Animation System and would prefer to directly set keyframes on the generated animation clips, then they can simply not add Animatable properties to a target object and open the clip in Unity's Animation window (Windows > Animation > Animation).</span></span> 

<span data-ttu-id="356ab-353">Wenn Sie die animierbaren Eigenschaften für die Animation verwenden, wird der Kurventyp auf EaseInOut festgelegt.</span><span class="sxs-lookup"><span data-stu-id="356ab-353">If using the Animatable properties for animation, the curve type is set to EaseInOut.</span></span>

<span data-ttu-id="356ab-354">**Aktuelle animierbare Eigenschaften:**</span><span class="sxs-lookup"><span data-stu-id="356ab-354">**Current Animatable Properties:**</span></span>
- [<span data-ttu-id="356ab-355">Skalierungsoffset</span><span class="sxs-lookup"><span data-stu-id="356ab-355">Scale Offset</span></span>](#scale-offset)
- [<span data-ttu-id="356ab-356">Positionsoffset</span><span class="sxs-lookup"><span data-stu-id="356ab-356">Position Offset</span></span>](#position-offset)
- [<span data-ttu-id="356ab-357">Farbe</span><span class="sxs-lookup"><span data-stu-id="356ab-357">Color</span></span>](#color)
- [<span data-ttu-id="356ab-358">Shaderfarbe</span><span class="sxs-lookup"><span data-stu-id="356ab-358">Shader Color</span></span>](#shader-color)
- [<span data-ttu-id="356ab-359">Shader Float</span><span class="sxs-lookup"><span data-stu-id="356ab-359">Shader Float</span></span>](#shader-float)
- [<span data-ttu-id="356ab-360">Shadervektor</span><span class="sxs-lookup"><span data-stu-id="356ab-360">Shader Vector</span></span>](#shader-vector)

### <a name="scale-offset"></a><span data-ttu-id="356ab-361">Skalierungsoffset</span><span class="sxs-lookup"><span data-stu-id="356ab-361">Scale Offset</span></span>

<span data-ttu-id="356ab-362">Die Eigenschaft Scale Offset Animatable übernimmt die aktuelle Skala des Objekts und fügt den definierten Offset hinzu.</span><span class="sxs-lookup"><span data-stu-id="356ab-362">The Scale Offset Animatable property takes the current scale of the object and adds the defined offset.</span></span>

![Skalierungsoffset mit virtueller Handinteraktion](../images/interactive-element/InEditor/Gifs/ScaleOffset.gif)

### <a name="position-offset"></a><span data-ttu-id="356ab-364">Positionsoffset</span><span class="sxs-lookup"><span data-stu-id="356ab-364">Position Offset</span></span>

<span data-ttu-id="356ab-365">Die Eigenschaft Position Offset Animatable nimmt die aktuelle Position des Objekts an und fügt den definierten Offset hinzu.</span><span class="sxs-lookup"><span data-stu-id="356ab-365">The Position Offset Animatable property takes the current position of the object and adds the defined offset.</span></span>

![Positionsoffset mit virtueller Handinteraktion](../images/interactive-element/InEditor/Gifs/PositionOffset.gif)

### <a name="color"></a><span data-ttu-id="356ab-367">Color</span><span class="sxs-lookup"><span data-stu-id="356ab-367">Color</span></span>

<span data-ttu-id="356ab-368">Die Color Animatable-Eigenschaft stellt die Hauptfarbe eines Materials dar, wenn das Material über eine Hauptfarbeigenschaft verfügt.</span><span class="sxs-lookup"><span data-stu-id="356ab-368">The Color Animatable property represents the main color of a material if the material has a main color property.</span></span> <span data-ttu-id="356ab-369">Diese Eigenschaft animiert die `material._Color` -Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="356ab-369">This property animates the `material._Color` property.</span></span>

![Farbänderung des Fokus mit virtueller Handinteraktion](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="shader-color"></a><span data-ttu-id="356ab-371">Shaderfarbe</span><span class="sxs-lookup"><span data-stu-id="356ab-371">Shader Color</span></span>

<span data-ttu-id="356ab-372">Die shader color Animatable-Eigenschaft verweist auf eine Shadereigenschaft vom Typ Color.</span><span class="sxs-lookup"><span data-stu-id="356ab-372">The Shader Color Animatable property refers to a shader property of type color.</span></span> <span data-ttu-id="356ab-373">Für alle Shadereigenschaften ist ein Eigenschaftenname erforderlich.</span><span class="sxs-lookup"><span data-stu-id="356ab-373">A property name is required for all shader properties.</span></span> <span data-ttu-id="356ab-374">Das folgende GIF veranschaulicht das Animieren einer Shaderfarbeigenschaft namens Fill_Color, die nicht die Hauptmaterialfarbe ist.</span><span class="sxs-lookup"><span data-stu-id="356ab-374">The gif below demonstrates animating a shader color property named Fill_Color that is not the main material color.</span></span>  <span data-ttu-id="356ab-375">Beobachten Sie die sich ändernden Werte im Materialinspektor.</span><span class="sxs-lookup"><span data-stu-id="356ab-375">Observe the changing values in the material inspector.</span></span>

![Schattierungsfarbe mit virtueller Handinteraktion](../images/interactive-element/InEditor/Gifs/ShaderColor.gif)

### <a name="shader-float"></a><span data-ttu-id="356ab-377">Shader Float</span><span class="sxs-lookup"><span data-stu-id="356ab-377">Shader Float</span></span>

<span data-ttu-id="356ab-378">Die Float Animatable-Eigenschaft des Shaders verweist auf eine Shadereigenschaft vom Typ float.</span><span class="sxs-lookup"><span data-stu-id="356ab-378">The Shader Float Animatable property refers to a shader property of type float.</span></span> <span data-ttu-id="356ab-379">Für alle Shadereigenschaften ist ein Eigenschaftenname erforderlich.</span><span class="sxs-lookup"><span data-stu-id="356ab-379">A property name is required for all shader properties.</span></span> <span data-ttu-id="356ab-380">Beobachten Sie in der folgenden GIF-Datei die sich ändernden Werte im Materialinspektor für die Eigenschaft "Eigenschaft".</span><span class="sxs-lookup"><span data-stu-id="356ab-380">In the gif below, observe the changing values in the material inspector for the Metallic property.</span></span> 

![Shader float mit virtueller Handinteraktion](../images/interactive-element/InEditor/Gifs/ShaderFloat.gif)

### <a name="shader-vector"></a><span data-ttu-id="356ab-382">Shadervektor</span><span class="sxs-lookup"><span data-stu-id="356ab-382">Shader Vector</span></span>

<span data-ttu-id="356ab-383">Die animierbare Shader Vector-Eigenschaft verweist auf eine Shadereigenschaft vom Typ Vector4.</span><span class="sxs-lookup"><span data-stu-id="356ab-383">The Shader Vector Animatable property refers to a shader property of type Vector4.</span></span> <span data-ttu-id="356ab-384">Für alle Shadereigenschaften ist ein Eigenschaftenname erforderlich.</span><span class="sxs-lookup"><span data-stu-id="356ab-384">A property name is required for all shader properties.</span></span> <span data-ttu-id="356ab-385">Beobachten Sie im gif unten die sich ändernden Werte im Materialinspektor für die Eigenschaft Tiling (Main Tex_ST).</span><span class="sxs-lookup"><span data-stu-id="356ab-385">In the gif below, observe the changing values in the material inspector for the Tiling (Main Tex_ST) property.</span></span> 

![Shadervektor mit virtueller Handinteraktion](../images/interactive-element/InEditor/Gifs/ShaderVector.gif)


### <a name="how-to-find-animatable-shader-property-names"></a><span data-ttu-id="356ab-387">Suchen nach animierbaren Shader-Eigenschaftennamen</span><span class="sxs-lookup"><span data-stu-id="356ab-387">How to Find Animatable Shader Property Names</span></span>

1. <span data-ttu-id="356ab-388">Navigieren Sie zu Window > Animation > Animation</span><span class="sxs-lookup"><span data-stu-id="356ab-388">Navigate to Window > Animation > Animation</span></span>
1. <span data-ttu-id="356ab-389">Stellen Sie sicher, dass das Objekt mit der Zustandsansicht in der Hierarchie ausgewählt ist.</span><span class="sxs-lookup"><span data-stu-id="356ab-389">Ensure that the object with the State Visualizer is selected in the hierarchy</span></span>
1. <span data-ttu-id="356ab-390">Auswählen eines beliebigen Animationsclips im Fenster "Animation"</span><span class="sxs-lookup"><span data-stu-id="356ab-390">Select any animation clip in the Animation window</span></span>
1. <span data-ttu-id="356ab-391">Wählen Sie **Eigenschaft hinzufügen** aus, und öffnen Sie das Foldout des Mesh-Renderers.</span><span class="sxs-lookup"><span data-stu-id="356ab-391">Select **Add Property**, open the Mesh Renderer foldout</span></span> 

    ![Hinzufügen der Animationseigenschaft im Animatorfenster](../images/interactive-element/StateVisualizer/AnimationWindow.png)

1. <span data-ttu-id="356ab-393">Diese Liste enthält die Namen aller Animatable-Eigenschaftennamen.</span><span class="sxs-lookup"><span data-stu-id="356ab-393">This list contains the names of all the Animatable property names</span></span> 

    ![Animationseigenschaften des Mesh-Renderers im Animatorfenster](../images/interactive-element/StateVisualizer/MeshRendererProperties.png)

## <a name="see-also"></a><span data-ttu-id="356ab-395">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="356ab-395">See also</span></span>

- [<span data-ttu-id="356ab-396">**Schaltflächen**</span><span class="sxs-lookup"><span data-stu-id="356ab-396">**Buttons**</span></span>](../ux-building-blocks/button.md)
- [<span data-ttu-id="356ab-397">**Begrenzungssteuerelement**</span><span class="sxs-lookup"><span data-stu-id="356ab-397">**Bounds Control**</span></span>](../ux-building-blocks/bounds-control.md)
- [<span data-ttu-id="356ab-398">**Grid-Objektaufsammlung**</span><span class="sxs-lookup"><span data-stu-id="356ab-398">**Grid Object Collection**</span></span>](../ux-building-blocks/object-collection.md)
- [<span data-ttu-id="356ab-399">**RadialView-Solver**</span><span class="sxs-lookup"><span data-stu-id="356ab-399">**RadialView Solver**</span></span>](../ux-building-blocks/solvers/solver.md)
