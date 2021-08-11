---
title: Interaktives Element
description: Dokumentation zu InteractiveElement MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 02/22/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Interactive-Element, Interactable
ms.openlocfilehash: 6d8f36c4780844e991eb32943645402503fab8340c6843dbb607f1c11033d912
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220443"
---
# <a name="interactive-element-experimental"></a>Interactive-Element [Experimentell]

Ein vereinfachter zentralisierter Einstiegspunkt für das MRTK-Eingabesystem. Enthält Zustandsverwaltungsmethoden, Ereignisverwaltung und die Zustandseinstellungslogik für Kerninteraktionszustände.

Interactive Element ist ein experimentelles Feature, das ab Unity 2019.3 unterstützt wird, da es eine funktion nutzt, die neu in Unity 2019.3: [Serialize Reference](https://docs.unity3d.com/ScriptReference/SerializeReference.html)ist.

### <a name="interactive-element-inspector"></a>Interaktiver Elementinspektor

Während des Wiedergabemodus gibt der Interaktive Elementinspektor visuelles Feedback, das angibt, ob der aktuelle Zustand aktiv ist oder nicht. Wenn ein Zustand aktiv ist, wird er mit einer Zyanfarbe hervorgehoben.  Wenn der Status nicht aktiv ist, wird die Farbe nicht geändert. Die Zahlen neben den Statuswerten im Inspektor sind die Zustandswerte. Wenn der Zustand aktiv ist, ist der Wert 1, und wenn der Status nicht aktiv ist, ist der Wert 0.

![Interaktives Element mit Interaktion mit virtueller Hand](../images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

## <a name="core-states"></a>Kernzustände

Interactive-Element enthält Kernzustände und unterstützt das Addition [benutzerdefinierter Zustände.](#custom-states)  Ein Kernzustand ist einer, in dem bereits die Zustandseinstellungslogik definiert `BaseInteractiveElement` ist. Im Folgenden finden Sie eine Liste der aktuellen eingabegesteuerten Kernzustände: 

### <a name="current-core-states"></a>Aktuelle Kernzustände

- [Standard](#default-state) 

Near and Far Interaction Core States (Nah- und Ferninteraktionskernzustände):
- [Fokus](#focus-state) 

Kernzustände in der Nähe der Interaktion:

- [Fokus nah](#focus-near-state)
- [Toucheingabe](#touch-state)

Kernzustände der Ferninteraktion:
- [Focus Far](#focus-far-state)
- [Wählen Sie Far (Weit) aus.](#select-far-state)

Andere Kernzustände:
- [Clicked](#clicked-state)
- [Ein- und Ausschalten](#toggle-on-and-toggle-off-state)
- [Speech-Schlüsselwort](#speech-keyword-state)

### <a name="how-to-add-a-core-state-via-inspector"></a>Hinzufügen eines Kernzustands über den Inspektor

1. Navigieren Sie **im Inspektor für Interactive-Element** zu Kernzustand hinzufügen.

    ![Hinzufügen eines Kernzustands über den Inspektor](../images/interactive-element/InEditor/InteractiveElementAddCoreState.png)


1. Wählen Sie die **Schaltfläche Status auswählen** aus, um den hinzuzufügenden Kernzustand auszuwählen. Die Zustände im Menü werden nach Interaktionstyp sortiert.

    ![Hinzufügen eines Kernzustands über inspector mit ausgewähltem Zustand](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectState.png)

1. Öffnen Sie das Foldout Ereigniskonfiguration, um die Ereignisse und Eigenschaften des Zustands anzeigen zu können.

    ![Hinzufügen eines Kernzustands über inspector mit Ereigniskonfiguration](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectStateEventConfig.png)


### <a name="how-to-add-a-core-state-via-script"></a>Hinzufügen eines Kernzustands per Skript

Verwenden Sie die `AddNewState(stateName)` -Methode, um einen Kernzustand hinzuzufügen. Verwenden Sie die -Enum, um eine Liste der verfügbaren `CoreInteractionState` Kernzustandsnamen zu erhalten.

```c#
// Add by name or add by CoreInteractionState enum to string

interactiveElement.AddNewState("SelectFar");

interactiveElement.AddNewState(CoreInteractionState.SelectFar.ToString());
```

### <a name="states-internal-structure"></a>Interne Zuständestruktur 

Die Zustände in Interactive Element sind vom Typ `InteractionState` .  Enthält `InteractionState` die folgenden Eigenschaften:

- **Name:** Der Name des Zustands.
- **Wert:** Der Zustandswert.  Wenn der Status "On" (Ein) ist, ist der Zustandswert 1. Wenn der Status deaktiviert ist, ist der Zustandswert 0.
- **Aktiv:** Gibt an, ob der Zustand derzeit aktiv ist. Der Wert für die Active-Eigenschaft ist true, wenn der Status eingeschaltet ist, false, wenn der Zustand deaktiviert ist. 
- **Interaktionstyp:** Der Interaktionstyp eines Zustands ist der Typ der Interaktion, für die ein Zustand vorgesehen ist. 
  - `None`: Unterstützt keine Form der Eingabeinteraktion.
  - `Near`: Unterstützung der Interaktion in der Nähe. Eingaben werden als nahezu interaktionsnah betrachtet, wenn eine artikulierte Hand direkten Kontakt mit einem anderen Spielobjekt hat, d. h. die Position, an der sich die artikulierte Hand in der Nähe der Position des Spielobjekts im Weltraum befindet.
  - `Far`: Unterstützung der Ferninteraktion. Die Eingabe wird als Ferninteraktion betrachtet, wenn kein direkter Kontakt mit dem Spielobjekt erforderlich ist. Beispielsweise wird die Eingabe über controller ray oder gaze als Ferninteraktionseingabe betrachtet.
  - `NearAndFar`: Umfasst die Unterstützung von Nah- und Ferninteraktion. 
  - `Other`: Zeigerunabhängige Interaktionsunterstützung.
- **Ereigniskonfiguration:** Die Ereigniskonfiguration für einen Zustand ist der Einstiegspunkt für das Serialisierungsereignisprofil. 

Alle diese Eigenschaften werden intern in der festgelegt, die `State Manager` im Interactive-Element enthalten ist. Verwenden Sie zum Ändern von Zuzuständen die folgenden Hilfsmethoden:

**Hilfsmethoden für Zustandseinstellungen**

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

Das Abrufen der Ereigniskonfiguration eines Zustands ist spezifisch für den Zustand selbst. Jeder Kernzustand verfügt über einen bestimmten Ereigniskonfigurationstyp, der unten in den Abschnitten beschrieben wird, in denen die einzelnen Kernstatus beschrieben werden.

Hier ist ein generalisiertes Beispiel für das Abrufen der Ereigniskonfiguration eines Zustands:

```c#
// T varies depending on the core state - the specific T's are specified under each of the core state sections
T stateNameEvents = interactiveElement.GetStateEvents<T>("StateName");
```

### <a name="default-state"></a>Standardzustand

Der Standardzustand ist für ein interaktives Element immer vorhanden.  Dieser Zustand ist nur aktiv, wenn alle anderen Status nicht aktiv sind.  Wenn ein anderer Zustand aktiv wird, wird der Standardzustand intern auf off festgelegt. 

Ein interaktives Element wird mit den Standard- und Fokuszuständen initialisiert, die in der Statusliste vorhanden sind. Der Standardzustand muss immer in der Statusliste vorhanden sein. 

#### <a name="getting-default-state-events"></a>Abrufen von Standardzustandsereignissen

Ereigniskonfigurationstyp für den Standardzustand: `StateEvents`

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

### <a name="focus-state"></a>Fokuszustand

Der Fokuszustand ist ein nah- und ferner Interaktionszustand, der als Mixed Reality-Äquivalent zum Hovern bezeichnet werden kann. Der Unterscheidungsfaktor zwischen nah und ferner Interaktion für den Fokuszustand ist der aktuelle aktive Zeigertyp.  Wenn der Zeigertyp für den Fokuszustand der Poke-Zeiger ist, wird die Interaktion als interaktionsnahe Interaktion betrachtet.  Wenn der primäre Zeiger nicht der Poke-Zeiger ist, wird die Interaktion als ferne Interaktion betrachtet. Der Fokuszustand ist standardmäßig im Interactive-Element vorhanden.

**Fokuszustandsverhalten** 
 ![ Fokuszustand mit virtueller Handinteraktion](../images/interactive-element/InEditor/Gifs/FocusStateEditor.gif) 

**Fokuszustandsinspektor** 
 ![ Fokuszustand im Inpsector](../images/interactive-element/InEditor/FocusStateInspector.png)

#### <a name="getting-focus-state-events&quot;></a>Abrufen von Fokuszustandsereignissen

Ereigniskonfigurationstyp für den Fokuszustand: `FocusEvents`

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

#### <a name="focus-near-vs-focus-far-behavior"></a>Focus Near vs Focus Far Behavior 

![Nah- und Fernfokus mit virtueller Handinteraktion](../images/interactive-element/InEditor/Gifs/FocusNearFocusFar.gif)

### <a name="focus-near-state"></a>Fokus near state

Der Fokus nah-Zustand wird festgelegt, wenn ein Fokusereignis ausgelöst wird und der primäre Zeiger der Poke-Zeiger ist, ein Hinweis auf eine nahezue Interaktion. 

**Fokus des Verhaltens des zustandsnahen Zustands** 
 ![ Fokus near state with virtual hand interaction (Nahzustandsfokus mit Virtueller Handinteraktion)](../images/interactive-element/InEditor/Gifs/FocusNearStateEditor.gif) 

**Focus Near State Inspector** 
 ![ Fokus in der Nähe der Komponente im Inspektor](../images/interactive-element/InEditor/FocusNearStateInspector.png)

#### <a name="getting-focusnear-state-events&quot;></a>Abrufen von FocusNear State Events

Ereigniskonfigurationstyp für den FocusNear-Zustand: `FocusEvents`

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

### <a name="focus-far-state"></a>Fokus ferner Zustand

Der Fokusweit-Zustand wird festgelegt, wenn der primäre Zeiger nicht der Poke-Zeiger ist.  Beispielsweise werden der Standardmäßige Controllerstrahlzeiger und der GGV-Zeiger (Gaze, Gesture, Voice) als Ferninteraktionszeiger betrachtet.

**Fokus fernen Zustandsverhaltens** 
 ![ Fokuszustand weit mit virtueller Handinteraktion](../images/interactive-element/InEditor/Gifs/FocusFarStateEditor.gif)

**Focus Far State Inspector** 
 ![ Komponente "Fokus fern" im Inspektor](../images/interactive-element/InEditor/FocusFarStateInspector.png)

#### <a name="getting-focus-far-state-events&quot;></a>Abrufen von Fokus-Far State-Ereignissen

Ereigniskonfigurationstyp für den FocusFar-Zustand: `FocusEvents`

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

### <a name="touch-state"></a>Touchzustand

Der Touchzustand ist ein zustandsnaher Interaktionszustand, der festgelegt wird, wenn eine artikulierte Hand das Objekt direkt berührt.  Eine direkte Berührung bedeutet, dass sich der Zeigefinger der artikulierten Hand sehr nah an der Weltposition des Objekts befindet. Standardmäßig wird eine Komponente an das -Objekt angefügt, `NearInteractionTouchableVolume` wenn der Touchzustand der Statusliste hinzugefügt wird.  Zum Erkennen von Touchereignissen ist das Vorhandensein einer -  `NearInteractionTouchableVolume` `NearInteractionTouchable` oder -Komponente erforderlich.  Der Unterschied zwischen und besteht in der Erkennung einer Berührung basierend auf dem Collider des Objekts und der Berührung innerhalb eines definierten Bereichs `NearInteractionTouchableVolume` `NearInteractionTouchable` einer `NearInteractionTouchableVolume` `NearInteractionTouchable` Ebene.

**Verhalten des Touchzustands** 
 ![ Touchzustand mit Interaktion mit virtueller Hand](../images/interactive-element/InEditor/Gifs/TouchStateEditor.gif)

**Touch State Inspector** 
 ![ Touchzustandskomponente im Inspektor](../images/interactive-element/InEditor/TouchStateInspector.png)

#### <a name="getting-touch-state-events&quot;></a>Abrufen von Touchzustandsereignissen

Ereigniskonfigurationstyp für den Touchzustand: `TouchEvents`

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

### <a name="select-far-state"></a>Wählen Sie Far State (Fernzustand) aus.

Der Select Far-Status ist die `IMixedRealityPointerHandler` Oberfläche.  Bei diesem Zustand handelt es sich um einen fernen Interaktionszustand, der einen Weitklick (Tippen in die Luft) erkennt und die Verwendung von Ferninteraktionszeigern wie dem Standardmäßigen Controllerstrahlzeiger oder dem GGV-Zeiger durchfing.  Der Status Far auswählen verfügt über eine Option unter dem Foldout für die Ereigniskonfiguration mit dem Namen `Global` . Wenn `Global` true ist, wird `IMixedRealityPointerHandler` als globaler Eingabehandler registriert.  Der Fokus auf ein Objekt ist nicht erforderlich, um Eingabesystemereignisse auszulösen, wenn ein Handler als global registriert ist.  Wenn ein Benutzer z. B. wissen möchte, wann immer die Geste zum Tippen in die Luft/Auswahl ausgeführt wird, unabhängig vom Objekt im Fokus, legen Sie `Global` auf TRUE fest. 

**Wählen Sie Far State Behavior (Fernzustandsverhalten) aus.** 
 ![ Auswählen von "fern" mit virtueller Handinteraktion](../images/interactive-element/InEditor/Gifs/SelectFarStateEditor.gif)

**Wählen Sie Far State Inspector (Inspektor für fernen Zustand) aus** 
 ![ Auswählen der Far-Komponente im Inspektor](../images/interactive-element/InEditor/SelectFarStateInspector.png)

#### <a name="getting-select-far-state-events&quot;></a>Abrufen von Ereignissen der Option &quot;Far State&quot;

Ereigniskonfigurationstyp für selectFar State: `SelectFarEvents`

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

### <a name="clicked-state"></a>Clicked State

Der Zustand Clicked (Geklickt) wird standardmäßig durch einen Fern-Interaktionsklick (Far-Status auswählen) ausgelöst.  Dieser Zustand wird intern auf "Ein" umgeschaltet, ruft das OnClicked-Ereignis auf und wird dann sofort in "Aus" umgeschaltet. 

> [!NOTE]
> Das visuelle Feedback im Inspektor basierend auf der Zustandsaktivität ist für den Zustand "Geklickt" nicht vorhanden, da es sofort ein- und ausgeschaltet wird. 

**Zustandsverhalten durch Klicken** 
 ![ Klicken auf den Zustand mit Interaktionen virtueller Hand](../images/interactive-element/InEditor/Gifs/ClickedStateEditor.gif)

**Klicken Sie auf Zustandsinspektor.** 
 ![ Klicken Sie im Inspektor auf die Zustandskomponente.](../images/interactive-element/InEditor/ClickedStateInspector.png)

**Near and Far Clicked State Example**  
Der zustandsweise Klicken kann über zusätzliche Einstiegspunkte mithilfe der -Methode ausgelöst `interactiveElement.TriggerClickedState()` werden.  Wenn ein Benutzer beispielsweise möchte, dass auch ein Klick auf ein Objekt durch eine Touchinteraktion ausgelöst wird, fügt er die Methode als Listener im `TriggerClickedState()` Touchzustand hinzu.   

![Near and far state with virtual hand interactions (Nah- und Fernzustand mit Interaktionen virtueller Hand)](../images/interactive-element/InEditor/Gifs/NearFarClickedState.gif)

#### <a name="getting-clicked-state-events&quot;></a>Abrufen von Statusereignissen, auf die geklickt wird

Ereigniskonfigurationstyp für den zustands geklickten Status: `ClickedEvents`

```c#
ClickedEvents clickedEvent = interactiveElement.GetStateEvents<ClickedEvents>(&quot;Clicked");

clickedEvent.OnClicked.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Clicked");
});
```

### <a name="toggle-on-and-toggle-off-state"></a>Ein- und Ausschalten des Zustands

Die Zustände Ein und Aus umschalten sind ein Paar und müssen beide vorhanden sein, um das Umschaltverhalten zu steuern.  Standardmäßig werden die Zustände Ein ein- und Ausschalten durch einen Fernklick (Far-Status auswählen) ausgelöst.  Standardmäßig ist der Status Aus umschalten beim Start aktiv, was bedeutet, dass der Umschalter auf off initialisiert wird.  Wenn ein Benutzer möchte, dass der Status Ein beim Start aktiv ist, legen Sie im Status Ein ein auf `IsSelectedOnStart` TRUE fest.

**ToggleOn und Toggle Off State Behavior** 
 ![ Ein- und Ausschalten mit Interaktionen virtueller Hand](../images/interactive-element/InEditor/Gifs/ToggleOnToggleOffStateEditor.gif)

**Ein- und Ausschalten des Zustandsinspektors** 
 ![ Umschalten der Komponente im Inspektor](../images/interactive-element/InEditor/ToggleOnToggleOffStateInspector.png)

**Near and Far Toggle States Example**  
Ähnlich wie beim Zustand "Geklickt" kann die Einstellung für den Umschaltzustand mehrere Einstiegspunkte mithilfe der -Methode `interactiveElement.SetToggleStates()` haben. Wenn ein Benutzer beispielsweise touch als zusätzlichen Einstiegspunkt zum Festlegen der Umschaltzustände verwenden möchte, fügt er die -Methode einem der Ereignisse im `SetToggleStates()` Touchzustand hinzu. 

![Nah- und Fern-Umschalten mit Interaktionen virtueller Hand](../images/interactive-element/InEditor/Gifs/NearFarToggleStates.gif)

#### <a name="getting-toggle-on-and-toggle-off-state-events&quot;></a>Ein- und Ausschalten von Zustandsereignissen

Ereigniskonfigurationstyp für den ToggleOn-Zustand: `ToggleOnEvents`  
Ereigniskonfigurationstyp für den ToggleOff-Zustand: `ToggleOffEvents`

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

### <a name="speech-keyword-state"></a>Speech-Schlüsselwortzustand

Der Status des Speech-Schlüsselworts lausiert auf die Schlüsselwörter, die im Mixed Reality Speech-Profil definiert sind. Jedes neue Schlüsselwort MUSS vor der Laufzeit im Sprachbefehlsprofil registriert werden (schritte unten). 

**Zustandsverhalten des Speech-Schlüsselworts** 
 ![ Speech-Schlüsselwort mit virtueller Interaktion](../images/interactive-element/InEditor/Gifs/SpeechKeywordStateEditor.gif)

**Zustandsinspektor des Speech-Schlüsselworts** 
 ![ Speech-Schlüsselwortkomponente im Inspektor](../images/interactive-element/InEditor/SpeechKeywordStateInspector.png)

> [!NOTE]
> Der Zustand des Speech-Schlüsselworts wurde im Editor durch Drücken der F5-Taste in der GIF-Datei oben ausgelöst. Die einrichtung im Editor für Sprachtests wird in den folgenden Schritten beschrieben. 

#### <a name="how-to-register-a-speech-commandkeyword"></a>Registrieren eines Speech-Befehls/-Schlüsselworts

1. Auswählen des **MixedRealityToolkit-Spielobjekts**

1. Wählen Sie **Kopieren und Aktuelles** Profil anpassen aus.

1. Navigieren Sie zum Abschnitt Eingabe, und wählen Sie **Klonen aus,** um die Änderung des Eingabeprofils zu aktivieren.

1. Scrollen Sie im Eingabeprofil nach unten zum Abschnitt Speech, und klonen Sie das Sprachprofil.

    ![Speech-Schlüsselwortprofil im MRTK-Spielobjekt](../images/interactive-element/InEditor/SpeechKeywordProfileClone.png) 

1. Wählen Sie Neuen Sprachbefehl hinzufügen aus.

    ![Hinzufügen eines neuen Speech-Schlüsselworts im MRTK-Profil](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeyword.png) 

1. Geben Sie das schlüsselwort new ein. Optional: Ändern Sie den KeyCode in F5 (oder einen anderen KeyCode), um Tests im Editor zu ermöglichen. 

    ![Konfigurieren des Sprachschlüsselworts im MRTK-Profil](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeywordName.png) 

1. Wechseln Sie zurück zum Zustandsinspektor des Speech-Schlüsselworts für interaktive Elemente, und wählen Sie **Schlüsselwort hinzufügen aus.** 

    ![Hinzufügen eines Schlüsselworts zur interaktiven Elementkomponente](../images/interactive-element/InEditor/SpeechKeywordAddKeyword.png) 

    ![Schlüsselwortvalidierung und -registrierung](../images/interactive-element/InEditor/SpeechKeywordAddKeywordBlank.png) 

1. Geben Sie das neue Schlüsselwort ein, das gerade im Speech-Profil registriert wurde.

    ![Eingeben eines neuen Sprachschlüsselworts](../images/interactive-element/InEditor/SpeechKeywordEnterKeyword.png) 


Um den Zustand des Speech-Schlüsselworts im Editor zu testen, drücken Sie den KeyCode, der in Schritt 6 (F5) definiert wurde, um das erkannte Speech-Schlüsselwortereignis zu simulieren.

#### <a name="getting-speech-keyword-state-events&quot;></a>Abrufen von Speech-Schlüsselwortzustandsereignissen

Ereigniskonfigurationstyp für den SpeechKeyword-Zustand: `SpeechKeywordEvents`

```c#
SpeechKeywordEvents speechKeywordEvents = interactiveElement.GetStateEvents<SpeechKeywordEvents>(&quot;SpeechKeyword");

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

## <a name="custom-states"></a>Benutzerdefinierte Zustände

### <a name="how-to-create-a-custom-state-via-inspector"></a>Erstellen eines benutzerdefinierten Zustands über den Inspektor 

Der über inspector erstellte benutzerdefinierte Zustand wird mit der Standardzustandsereigniskonfiguration initialisiert. Die Standardereigniskonfiguration für einen benutzerdefinierten Zustand ist vom Typ `StateEvents` und enthält die Ereignisse OnStateOn und OnStateOff.

1. Navigieren Sie **im Inspektor für interactive-Element** zu Benutzerdefinierten Zustand erstellen.
    
    ![Erstellen eines benutzerdefinierten Zustands](../images/interactive-element/InEditor/InteractiveElementCreateCustomState.png)

1. Geben Sie den Namen des neuen Zustands ein. Dieser Name muss eindeutig sein und darf nicht mit den vorhandenen Kernzuständen identisch sein. 
    
    ![Eingeben des Namens eines neuen benutzerdefinierten Zustands](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateName.png)

1. Wählen **Sie Statusname festlegen aus,** um der Statusliste hinzuzufügen.
    
    ![Hinzufügen eines benutzerdefinierten Zustands zur Statusliste](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateNameSet.png)

   Dieser benutzerdefinierte Zustand wird mit der Standardereigniskonfiguration `StateEvents` initialisiert, die die Ereignisse und `OnStateOn` `OnStateOff` enthält. Informationen zum Erstellen einer benutzerdefinierten Ereigniskonfiguration für einen neuen Zustand finden Sie unter Erstellen eines [benutzerdefinierten Zustands mit einer benutzerdefinierten Ereigniskonfiguration.](#creating-a-custom-state-with-a-custom-event-configuration)
    
    ![Neuer Zustand, der in der interaktiven Elementkomponente angezeigt wird](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateEventConfig.png)


### <a name="how-to-create-a-custom-state-via-script&quot;></a>Erstellen eines benutzerdefinierten Zustands per Skript

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

### <a name="creating-a-custom-state-with-a-custom-event-configuration"></a>Erstellen eines benutzerdefinierten Zustands mit einer benutzerdefinierten Ereigniskonfiguration 

Beispieldateien für einen benutzerdefinierten Zustand mit dem Namen **Tastatur** befinden sich hier: MRTK\SDK\Experimental\InteractiveElement\Examples\Scripts\CustomStateExample

In den folgenden Schritten wird ein vorhandenes Beispiel zum Erstellen einer benutzerdefinierten Zustandsereigniskonfiguration und von Empfängerdateien beschrieben.

1. Stellen Sie sich einen Zustandsnamen vor.  Dieser Name muss eindeutig sein und darf nicht mit den vorhandenen Kernzuständen identisch sein. Im Rahmen dieses Beispiels wird der Statusname Tastatur **sein.**

1. Erstellen Sie zwei CS-Dateien mit dem Namen state name + "Receiver" und state name + "Events". Die Benennung dieser Dateien wird intern berücksichtigt und muss der Konvention für Zustandsname + Ereignis/Empfänger folgen. 

    ![Tastaturzustandsskripts](../images/interactive-element/InEditor/KeyboardStateFiles.png)

1. Weitere Informationen zu Dateiinhalten finden Sie in den Dateien KeyboardEvents.cs und KeyboardReceiver.cs. Neue Ereigniskonfigurationsklassen müssen von `BaseInteractionEventConfiguration` erben, und neue Ereignisempfängerklassen müssen von `BaseEventReceiver` erben.  Beispiele für die Zustandseinstellung für den Tastaturzustand befinden sich in der `CustomStateSettingExample.cs` Datei. 

1. Fügen Sie den Zustand dem Interactive-Element mithilfe des Zustandsnamens hinzu. Der Zustandsname wird erkannt, wenn Ereigniskonfigurations- und Ereignisempfängerdateien vorhanden sind.  Die Eigenschaften in der benutzerdefinierten Ereigniskonfigurationsdatei sollten im Inspektor angezeigt werden.

    ![Hinzufügen eines benutzerdefinierten Zustands zum interaktiven Element ](../images/interactive-element/InEditor/AddKeyboardState.png) ![ Benutzerdefinierter Zustand, der im interaktiven Element erkannt wird](../images/interactive-element/InEditor/SetKeyboardStateName.png)


1. Weitere Beispiele für Ereigniskonfigurations- und Ereignisempfängerdateien finden Sie in den Dateien unter diesen Pfaden:    
- MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventConfigurations
- MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventReceivers

## <a name="example-scene"></a>Beispielszene 

Die Beispielszene für Interactive Element + State Visualizer befindet sich hier: MRTK\SDK\Experimental\InteractiveElement\Examples\InteractiveElementExampleScene.unity

![Beispielszene mit interaktiver Element- und Zustandsansicht](../images/interactive-element/InEditor/ExampleScene.png)

### <a name="compressable-button"></a>Komprimierbare Schaltfläche

Die Beispielszene enthält Prefabs mit den Namen `CompressableButton` und `CompressableButtonToggle` . Diese Prefabs spiegeln das Verhalten der `PressableButtonHoloLens2` Schaltflächen wider, die mithilfe des interaktiven Elements und der Zustandsansicht erstellt werden. Die `CompressableButton` -Komponente ist derzeit eine Kombination von `PressableButton`  +  `PressableButtonHoloLens2` mit als `BaseInteractiveElement` Basisklasse. 

## <a name="state-visualizer-experimental"></a>Zustandsansicht [Experimentell]

Die State Visualizer-Komponente fügt einem Objekt Animationen hinzu, die auf den Zuständen basieren, die in einer verknüpften interaktiven Elementkomponente definiert sind. Diese Komponente erstellt Animationsobjekte, platziert sie im Ordner MixedRealityToolkit.Generated und ermöglicht eine vereinfachte Einstellung des Animationsschlüsselrahmens durch Hinzufügen von animierbaren Eigenschaften zu einem Zielspielobjekt. Um Animationsübergänge zwischen Zuständen zu aktivieren, wird ein Animator Controller-Medienobjekt erstellt, und ein Standardzustandscomputer wird mit zugeordneten Parametern und allen Zustandsübergängen generiert.  Der Zustandsautomat kann im Animatorfenster von Unity angezeigt werden.

### <a name="state-visualizer-and-unity-animation-system"></a>Zustandsansicht und Unity-Animationssystem

Die Zustandsansicht nutzt derzeit das Unity-Animationssystem. 

Wenn die Schaltfläche **Neue Animationsclips generieren** in der Zustandsansicht gedrückt wird, werden neue Animationsclipressourcen basierend auf den Statusnamen im Interactive-Element generiert und im Ordner MixedRealityToolkit.Generated platziert. Die Animation Clip-Eigenschaft in jedem Zustandscontainer wird auf den zugeordneten Animationsclip festgelegt.

![Animationsclips in der Zustandsansichtskomponente](../images/interactive-element/StateVisualizer/AnimationClips.png)

Außerdem wird [ein Animatorstatuscomputer](https://docs.unity3d.com/Manual/AnimationOverview.html) generiert, um reibungslose Übergänge zwischen Animationsclips zu verwalten.  Standardmäßig verwendet der Zustandscomputer [beliebige](https://docs.unity3d.com/Manual/class-State.html) Zustände, um Übergänge zwischen beliebigen Zuständen in Interactive Element zuzulassen. 

[Zustandsansichten, die im Animator ausgelöst](https://docs.unity3d.com/Manual/AnimationParameters.html) werden, werden auch für jeden Zustand generiert. Die Triggerparameter werden in der Zustandsansicht verwendet, um eine Animation auszulösen.

![Unity-Zustandsautomat](../images/interactive-element/StateVisualizer/UnityStateMachine.png)

### <a name="runtime-limitations"></a>Runtime-Einschränkungen 

Die Zustandsansicht muss einem Objekt über den Inspektor hinzugefügt werden und kann nicht per Skript hinzugefügt werden.  Die Eigenschaften, die den AnimatorStateMachine/AnimationController ändern, sind in einem Editor-Namespace ( `UnityEditor.Animations` ) enthalten, der beim Erstellen der App entfernt wird.

## <a name="how-to-use-the-state-visualizer"></a>Verwenden der Zustandsansicht

1. Erstellen eines Cubes
1. Attach Interactive-Element
1. Zustandsansicht anfügen
1. Wählen Sie **Generate New Animation Clips (Neue Animationsclips generieren) aus.**

    ![Generieren neuer Animationsclips](../images/interactive-element/StateVisualizer/GenerateAnimationClips.png)

    ![Anzeigen generierter Animationsclips in schnellansichts- und interaktiven Elementkomponenten](../images/interactive-element/StateVisualizer/GenerateAnimationClips2.png)

1. Wählen Sie im Container Fokuszustand die Option **Ziel hinzufügen** aus.

    ![Hinzufügen eines Zustandsansichtsziels](../images/interactive-element/StateVisualizer/AddTarget.png)

1. Ziehen Sie das aktuelle Spielobjekt in das Zielfeld. 

    ![Festlegen des Statusvisuierungsziels](../images/interactive-element/StateVisualizer/SetTarget.png)

1. Öffnen des Foldouts Cube Animatable Properties (Animatable-Eigenschaften)
1. Wählen Sie das Dropdownmenü Animatable property (Animatable-Eigenschaft) und **dann Color (Farbe) aus.**

    ![Festlegen der Farbe der Zustandsansicht](../images/interactive-element/StateVisualizer/SetColor.png)

1. Wählen **Sie Add the Color Animatable Property (Animatable-Eigenschaft für Farbe hinzufügen)** aus.

    ![Auswählen der animierbaren Eigenschaft für die Schnellansichtsfarbe](../images/interactive-element/StateVisualizer/SetColorProperty.png)

1. Auswählen einer Farbe 

    ![Auswählen einer Schnellansichtsfarbe aus dem Farbrad](../images/interactive-element/StateVisualizer/SetBlueColor.png)

1. Drücken Sie die Wiedergabe, und beobachten Sie die Farbänderung der Übergangsfarbe.

    ![Beispiel für farbliche Übergangsänderung mit Interaktion virtueller Hand](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

## <a name="animatable-properties"></a>Eigenschaften, die animiert werden können

Der Hauptzweck der animierbaren Eigenschaften besteht darin, die Keyframeeinstellung für Animationsclips zu vereinfachen.  Wenn ein Benutzer mit dem Unity Animation System vertraut ist und es vorziehen würde, Keyframes direkt für die generierten Animationsclips festzulegen, kann er einfach keine animierbaren Eigenschaften zu einem Zielobjekt hinzufügen und den Clip im Animationsfenster von Unity öffnen (Windows > Animation > Animation). 

Wenn Sie die animierbaren Eigenschaften für Animationen verwenden, wird der Kurventyp auf EaseInOut festgelegt.

**Aktuelle animierbare Eigenschaften:**
- [Skalierungsoffset](#scale-offset)
- [Positionsoffset](#position-offset)
- [Farbe](#color)
- [Shaderfarbe](#shader-color)
- [Shader Float](#shader-float)
- [Shadervektor](#shader-vector)

### <a name="scale-offset"></a>Skalierungsoffset

Die animierbare Eigenschaft Skalierungsoffset übernimmt die aktuelle Skalierung des Objekts und fügt den definierten Offset hinzu.

![Skalierungsoffset mit virtueller Handinteraktion](../images/interactive-element/InEditor/Gifs/ScaleOffset.gif)

### <a name="position-offset"></a>Positionsoffset

Die Position Offset Animatable -Eigenschaft nimmt die aktuelle Position des -Objekts an und fügt den definierten Offset hinzu.

![Positionsoffset mit virtueller Handinteraktion](../images/interactive-element/InEditor/Gifs/PositionOffset.gif)

### <a name="color"></a>Color

Die Color Animatable-Eigenschaft stellt die Hauptfarbe eines Materials dar, wenn das Material über eine Hauptfarbeigenschaft verfügt. Diese Eigenschaft animiert die `material._Color` -Eigenschaft.

![Fokusfarbänderung durch Interaktion mit virtuellen Hand](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="shader-color"></a>Shaderfarbe

Die Animatable-Eigenschaft Shaderfarbe bezieht sich auf eine Shadereigenschaft vom Typ Color. Für alle Shadereigenschaften ist ein Eigenschaftenname erforderlich. Das folgende GIF zeigt das Animieren einer Shaderfarbeigenschaft namens Fill_Color, die nicht die Hauptmaterialfarbe ist.  Beobachten Sie die sich ändernden Werte im Materialinspektor.

![Farbton mit Interaktion mit virtueller Hand](../images/interactive-element/InEditor/Gifs/ShaderColor.gif)

### <a name="shader-float"></a>Shader Float

Die Float Animatable-Eigenschaft des Shaders verweist auf eine Shadereigenschaft vom Typ float. Für alle Shadereigenschaften ist ein Eigenschaftenname erforderlich. Beobachten Sie im gif unten die sich ändernden Werte im Materialinspektor für die Eigenschaft "Materials". 

![Shader float with virtual hand interaction](../images/interactive-element/InEditor/Gifs/ShaderFloat.gif)

### <a name="shader-vector"></a>Shadervektor

Die Shader Vector Animatable-Eigenschaft verweist auf eine Shadereigenschaft vom Typ Vector4. Für alle Shadereigenschaften ist ein Eigenschaftenname erforderlich. Beobachten Sie im gif unten die sich ändernden Werte im Materialinspektor für die Tiling (Main Tex_ST)-Eigenschaft. 

![Shadervektor mit virtueller Handinteraktion](../images/interactive-element/InEditor/Gifs/ShaderVector.gif)


### <a name="how-to-find-animatable-shader-property-names"></a>Suchen nach animierbaren Shadereigenschaftennamen

1. Navigieren Sie zu Window > Animation > Animation.
1. Stellen Sie sicher, dass das Objekt mit der Zustandsansicht in der Hierarchie ausgewählt ist.
1. Auswählen eines beliebigen Animationsclips im Animationsfenster
1. Wählen Sie **Add Property (Eigenschaft hinzufügen)** aus, und öffnen Sie das Foldout des Mesh-Renderers. 

    ![Hinzufügen einer Animationseigenschaft im Animatorfenster](../images/interactive-element/StateVisualizer/AnimationWindow.png)

1. Diese Liste enthält die Namen aller Animatable-Eigenschaftsnamen. 

    ![Animationseigenschaften des Mesh-Renderers im Animatorfenster](../images/interactive-element/StateVisualizer/MeshRendererProperties.png)

## <a name="see-also"></a>Siehe auch

- [**Schaltflächen**](../ux-building-blocks/button.md)
- [**Begrenzungssteuerelement**](../ux-building-blocks/bounds-control.md)
- [**Grid-Objektauflistung**](../ux-building-blocks/object-collection.md)
- [**RadialView-Solver**](../ux-building-blocks/solvers/solver.md)
