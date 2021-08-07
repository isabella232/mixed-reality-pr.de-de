---
title: HP Reverb G2-Controller in Unity
description: Erfahren Sie, wie Sie die neuen HP Reverb G2-Controller in SteamVR und Windows Mixed Reality Unity-Anwendungen einrichten und verwenden.
author: hferrone
ms.author: v-hferrone
ms.date: 10/14/2020
ms.topic: article
keywords: Unity, Reverb, Reverb G2, HP Reverb G2, Mixed Reality, Entwicklung, Motion Controller, Benutzereingabe, Features, neues Projekt, Emulator, Dokumentation, Leitfäden, Features, Hologramme, Spieleentwicklung
ms.openlocfilehash: 4e561cb1e46fe487f1b25ed526f0adeafc2de6c525835ffe3b1871d7516b233e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115215620"
---
# <a name="hp-reverb-g2-controllers-in-unity"></a>HP Reverb G2-Controller in Unity

HP Motion-Controller sind ein völlig neuer Typ von Windows Mixed Reality Controllern: die gleiche Nachverfolgungstechnologie mit einem etwas anderen Satz verfügbarer Eingaben: 

* Touchpad wurde durch zwei Schaltflächen ersetzt: A und B für den rechten Controller und X und Y für den linken Controller. 
* "Greifen" ist jetzt ein Trigger, der einen Datenstrom von Werten zwischen 0,0 und 1,0 anstatt einer Schaltfläche mit den Zuständen Gedrückt und Nicht gedrückt veröffentlicht. 

Da auf die neuen Eingaben nicht über vorhandene Windows und Unity-APIs zugegriffen werden kann, benötigen Sie das dedizierte UPM-Paket **Microsoft.MixedReality.Input.** 

> [!IMPORTANT]
> **Klassen in diesem Paket ersetzen vorhandene Windows und Unity-APIs nicht, sondern ergänzen sie.** Features, die häufig sowohl für klassische Windows Mixed Reality-Controller als auch für HP Motion Controllers verfügbar sind, sind über denselben Codepfad über vorhandene APIs zugänglich. Nur die neuen Eingaben erfordern die Verwendung des zusätzlichen Microsoft.MixedReality.Input-Pakets. 

## <a name="hp-motion-controller-overview"></a>Übersicht über HP Motion Controller

*Microsoft.MixedReality.Input.MotionController* stellt einen Motion Controller dar. Jede *MotionController-Instanz* verfügt über einen *XR. WSA. Input.InteractionSource-Peer,* der mithilfe von Handkraft, Anbieter-ID, Produkt-ID und Version korreliert werden kann. 

Sie können MotionController-Instanzen nutzen, indem Sie einen *MotionControllerWatcher* erstellen und dessen Ereignisse abonnieren, ähnlich wie bei der Verwendung von *InteractionManager-Ereignissen,* um neue *InteractionSource-Instanzen* zu ermitteln. Die Methoden und Eigenschaften des MotionController beschreiben die vom Controller unterstützten Eingaben, einschließlich der Schaltflächen, Trigger, der 2D-Achse und des Thumbsticks. Die MotionController-Klasse macht auch Methoden für den Zugriff auf Eingabezustände über die *MotionControllerReading-Klasse* verfügbar. Die MotionControllerReading-Klasse stellt eine Momentaufnahme des Zustands des Controllers zu einem bestimmten Zeitpunkt dar. 

## <a name="installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool"></a>Installieren von Microsoft.MixedReality.Input mit dem Mixed Reality Feature Tool

Installieren Sie das Microsoft.MixedReality.Input-Plug-In mit der neuen Anwendung Mixed Reality Feature Tool. Befolgen Sie die [Installations- und Nutzungsanweisungen,](welcome-to-mr-feature-tool.md) und wählen Sie das **Mixed Reality-Eingabepaket** in der Kategorie Mixed Reality Toolkit aus:

![Mixed Reality Fenster "Featuretoolpakete" mit hervorgehobener Mixed Reality-Eingabe](images/feature-tool-mrinput.png)

## <a name="using-microsoftmixedrealityinput"></a>Verwenden von Microsoft.MixedReality.Input 

### <a name="input-values"></a>Eingabewerte

Ein MotionController kann zwei Arten von Eingaben verfügbar machen: 

* Schaltflächen und Triggerzustände werden durch einen eindeutigen float-Wert zwischen 0,0 und 1,0 ausgedrückt, der angibt, wie viel sie gedrückt werden.
    * Eine Schaltfläche kann nur 0,0 (wenn nicht gedrückt) oder 1,0 (wenn gedrückt) zurückgegeben werden, während ein Trigger kontinuierliche Werte zwischen 0,0 (vollständig freigegeben) und 1,0 (vollständig gedrückt) zurückgeben kann. 
* Der Thumbstickzustand wird durch einen Vector2 ausgedrückt, dessen X- und Y-Komponenten zwischen -1,0 und 1,0 liegen. 

Sie können *MotionController.GetPressableInputs()* verwenden, um eine Liste von Eingaben zurückzugeben, die einen gedrückten Wert zurückgeben (Schaltflächen und Trigger) oder die *MotionController.GetXYInputs()-Methode,* um eine Liste von Eingaben zurückzugeben, die einen 2-Achsen-Wert zurückgeben. 

Eine MotionControllerReading-Instanz stellt den Zustand des Controllers zu einem bestimmten Zeitpunkt dar: 

* *GetPressedValue()* ruft den Zustand einer Schaltfläche oder eines Triggers ab. 
* *GetXYValue()* ruft den Zustand eines Thumbsticks ab. 

### <a name="creating-a-cache-to-maintain-a-collection-of-motioncontroller-instances-and-their-states"></a>Erstellen eines Caches zum Verwalten einer Sammlung von MotionController-Instanzen und deren Zuständen 

Instanziieren Sie zunächst einen MotionControllerWatcher, und registrieren Sie Handler für die *MotionControllerAdded-* und *MotionControllerRemoved-Ereignisse,* um einen Cache verfügbarer MotionController-Instanzen beizubehalten. Dieser Cache sollte ein MonoBehavior sein, der wie im folgenden Code gezeigt an ein GameObject angefügt ist:

```csharp
public class MotionControllerStateCache : MonoBehaviour 
{ 
    /// <summary> 
    /// Internal helper class which associates a Motion Controller 
    /// and its known state 
    /// </summary> 
    private class MotionControllerState 
    { 
        /// <summary> 
        /// Construction 
        /// </summary> 
        /// <param name="mc">motion controller</param>` 
        public MotionControllerState(MotionController mc) 
        { 
            this.MotionController = mc; 
        } 

        /// <summary> 
        /// Motion Controller that the state represents 
        /// </summary> 
        public MotionController MotionController { get; private set; } 
        … 
    } 

    private MotionControllerWatcher _watcher; 
    private Dictionary<Handedness, MotionControllerState> 
        _controllers = new Dictionary<Handedness, MotionControllerState>(); 

    /// <summary> 
    /// Starts monitoring controller's connections and disconnections 
    /// </summary> 
    public void Start() 
    { 
        _watcher = new MotionControllerWatcher(); 
        _watcher.MotionControllerAdded += _watcher_MotionControllerAdded; 
        _watcher.MotionControllerRemoved += _watcher_MotionControllerRemoved; 
        var nowait = _watcher.StartAsync(); 
    } 

    /// <summary> 
    /// Stops monitoring controller's connections and disconnections 
    /// </summary> 
    public void Stop() 
    { 
        if (_watcher != null) 
        { 
            _watcher.MotionControllerAdded -= _watcher_MotionControllerAdded; 
            _watcher.MotionControllerRemoved -= _watcher_MotionControllerRemoved; 
            _watcher.Stop(); 
        } 
    }

    /// <summary> 
    /// called when a motion controller has been removed from the system: 
    /// Remove a motion controller from the cache 
    /// </summary> 
    /// <param name="sender">motion controller watcher</param> 
    /// <param name="e">motion controller </param> 
    private void _watcher_MotionControllerRemoved(object sender, MotionController e) 
    { 
        lock (_controllers) 
        { 
            _controllers.Remove(e.Handedness); 
        } 
    }

    /// <summary> 
    /// called when a motion controller has been added to the system: 
    /// Remove a motion controller from the cache 
    /// </summary> 
    /// <param name="sender">motion controller watcher</param> 
    /// <param name="e">motion controller </param> 
    private void _watcher_MotionControllerAdded(object sender, MotionController e) 
    { 
        lock (_controllers) 
        { 
            _controllers[e.Handedness] = new MotionControllerState(e); 
        } 
    } 
} 
```

### <a name="reading-new-inputs-by-polling"></a>Lesen neuer Eingaben durch Abfragen 

Sie können den aktuellen Zustand jedes bekannten Controllers über *MotionController.TryGetReadingAtTime* während der *Update-Methode* der MonoBehavior-Klasse lesen. Sie möchten *DateTime.Now* als timestamp-Parameter übergeben, um sicherzustellen, dass der neueste Zustand des Controllers gelesen wird. 

```csharp
public class MotionControllerStateCache : MonoBehaviour 
{ 
    … 

    private class MotionControllerState 
    {
        … 

        /// <summary> 
        /// Update the current state of the motion controller 
        /// </summary> 
        /// <param name="when">time of the reading</param> 
        public void Update(DateTime when) 
        { 
            this.CurrentReading = this.MotionController.TryGetReadingAtTime(when); 
        } 

        /// <summary> 
        /// Last reading from the controller 
        /// </summary> 
        public MotionControllerReading CurrentReading { get; private set; } 
    } 

    /// <summary> 
    /// Updates the input states of the known motion controllers 
    /// </summary> 
    public void Update() 
    { 
        var now = DateTime.Now; 

        lock (_controllers) 
        { 
            foreach (var controller in _controllers) 
            { 
                controller.Value.Update(now); 
            } 
        } 
    } 
} 
```

Sie können den aktuellen Eingabewert der Controller mithilfe der Handkraft des Controllers abrufen: 

```csharp
public class MotionControllerStateCache : MonoBehaviour 
{ 
    … 
    /// <summary> 
    /// Returns the current value of a controller input such as button or trigger 
    /// </summary> 
    /// <param name="handedness">Handedness of the controller</param> 
    /// <param name="input">Button or Trigger to query</param> 
    /// <returns>float value between 0.0 (not pressed) and 1.0 
    /// (fully pressed)</returns> 
    public float GetValue(Handedness handedness, ControllerInput input) 
    { 
        MotionControllerReading currentReading = null; 

        lock (_controllers) 
        { 
            if (_controllers.TryGetValue(handedness, out MotionControllerState mc)) 
            { 
                currentReading = mc.CurrentReading; 
            } 
        } 

        return (currentReading == null) ? 0.0f : currentReading.GetPressedValue(input); 
    } 

    /// <summary> 
    /// Returns the current value of a controller input such as button or trigger 
    /// </summary> 
    /// <param name="handedness">Handedness of the controller</param> 
    /// <param name="input">Button or Trigger to query</param> 
    /// <returns>float value between 0.0 (not pressed) and 1.0 
    /// (fully pressed)</returns> 
    public float GetValue(UnityEngine.XR.WSA.Input.InteractionSourceHandedness handedness, ControllerInput input) 
    { 
        return GetValue(Convert(handedness), input); 
    } 

    /// <summary> 
    /// Returns a boolean indicating whether a controller input such as button or trigger is pressed 
    /// </summary> 
    /// <param name="handedness">Handedness of the controller</param> 
    /// <param name="input">Button or Trigger to query</param> 
    /// <returns>true if pressed, false if not pressed</returns> 
    public bool IsPressed(Handedness handedness, ControllerInput input) 
    { 
        return GetValue(handedness, input) >= PressedThreshold; 
    } 
} 
```

Um z. B. den analogen Greifwert einer InteractionSource zu lesen: 

```csharp
/// Read the analog grasp value of all connected interaction sources 
void Update() 
{ 
    … 
    var stateCache = gameObject.GetComponent<MotionControllerStateCache>(); 
    foreach (var sourceState in InteractionManager.GetCurrentReading()) 
    { 
        float graspValue = stateCache.GetValue(sourceState.source.handedness, 
            Microsoft.MixedReality.Input.ControllerInput.Grasp);
        … 
    }
} 
```

### <a name="generating-events-from-the-new-inputs"></a>Generieren von Ereignissen aus den neuen Eingaben 

Anstatt den Zustand eines Controllers einmal pro Frame abzufragen, haben Sie die Möglichkeit, alle Zustandsänderungen als Ereignisse zu verarbeiten, wodurch Sie selbst die schnellsten Aktionen verarbeiten können, die weniger als einen Frame dauern. Damit dieser Ansatz funktioniert, muss der Cache von MotionControllern alle Zustände verarbeiten, die seit dem letzten Frame von einem Controller veröffentlicht wurden. Dies können Sie tun, indem Sie den Zeitstempel des letzten MotionControllerReading speichern, das von einem MotionController abgerufen wurde, und *MotionController.TryGetReadingAfterTime()* aufrufen: 

```csharp
private class MotionControllerState 
{ 
    … 
    /// <summary> 
    /// Returns an array representng buttons which are pressed 
    /// </summary> 
    /// <param name="reading">motion controller reading</param> 
    /// <returns>array of booleans</returns> 
    private bool[] GetPressed(MotionControllerReading reading) 
    { 
        if (reading == null) 
        { 
            return null; 
        } 
        else 
        { 
            bool[] ret = new bool[this.pressableInputs.Length]; 
            for (int i = 0; i < pressableInputs.Length; ++i) 
            { 
                ret[i] = reading.GetPressedValue(pressableInputs[i]) >= PressedThreshold; 
            } 

            return ret; 
        } 
    } 

    /// <summary> 
    /// Get the next available state of the motion controller 
    /// </summary> 
    /// <param name="lastReading">previous reading</param> 
    /// <param name="newReading">new reading</param> 
    /// <returns>true is a new reading was available</returns> 
    private bool GetNextReading(MotionControllerReading lastReading, out MotionControllerReading newReading) 
    { 
        if (lastReading == null) 
        { 
            // Get the first state published by the controller 
            newReading = this.MotionController.TryGetReadingAfterSystemRelativeTime(TimeSpan.FromSeconds(0.0)); 
        } 
        else 
        { 
            // Get the next state published by the controller 
            newReading = this.MotionController.TryGetReadingAfterTime(lastReading.InputTime); 
        } 

        return newReading != null; 
    } 

    /// <summary> 
    /// Processes all the new states published by the controller since the last call 
    /// </summary> 
    public IEnumerable<MotionControllerEventArgs> GetNextEvents() 
    {
        MotionControllerReading lastReading = this.CurrentReading; 
        bool[] lastPressed = GetPressed(lastReading); 
        MotionControllerReading newReading; 
        bool[] newPressed; 

        while (GetNextReading(lastReading, out newReading)) 
        { 
            newPressed = GetPressed(newReading); 

            // If we have two readings, compare and generate events 
            if (lastPressed != null) 
            { 
                for (int i = 0; i < pressableInputs.Length; ++i) 
                { 
                    if (newPressed[i] != lastPressed[i]) 
                    { 
                        yield return new MotionControllerEventArgs(this.MotionController.Handedness, newPressed[i], this.pressableInputs[i], newReading.InputTime); 
                    } 
                } 
            } 

            lastPressed = newPressed; 
            lastReading = newReading; 
        } 

        // No more reading 
        this.CurrentReading = lastReading; 
    } 
} 
```

Nachdem Sie die internen Cacheklassen aktualisiert haben, kann die MonoBehavior-Klasse zwei Ereignisse verfügbar machen – Pressed und Released – und sie über ihre Update()-Methode auslösen: 

```csharp
/// <summary> 
/// Event argument class for InputPressed and InputReleased events 
/// </summary> 
public class MotionControllerEventArgs : EventArgs 
{ 
    public MotionControllerEventArgs(Handedness handedness, bool isPressed, rollerInput input, DateTime inputTime) 
    { 
        this.Handedness = handedness; 
        this.Input = input; 
        this.InputTime = inputTime; 
        this.IsPressed = isPressed; 
    } 

    /// <summary> 
    /// Handedness of the controller raising the event 
    /// </summary> 
    public Handedness Handedness { get; private set; } 

    /// <summary> 
    /// Button pressed or released 
    /// </summary> 
    public ControllerInput Input { get; private set; } 

    /// <summary> 
    /// Time of the event 
    /// </summary> 
    public DateTime InputTime { get; private set; } 

    /// <summary> 
    /// true if button is pressed, false otherwise 
    /// </summary> 
    public bool IsPressed { get; private set; } 
} 

/// <summary> 
/// Event raised when a button is pressed 
/// </summary> 
public event EventHandler<MotionControllerEventArgs> InputPressed; 

/// <summary> 
/// Event raised when a button is released 
/// </summary> 
public event EventHandler<MotionControllerEventArgs> InputReleased; 

/// <summary> 
/// Updates the input states of the known motion controllers 
/// </summary> 
public void Update() 
{ 
    // If some event handler has been registered, we need to process all states  
    // since the last update, to avoid missing a quick press / release 
    if ((InputPressed != null) || (InputReleased != null)) 
    { 
        List<MotionControllerEventArgs> events = new <MotionControllerEventArgs>(); 

        lock (_controllers) 
        { 
            foreach (var controller in _controllers) 
            { 
                events.AddRange(controller.Value.GetNextEvents()); 
            } 
        } 
 
        // Sort the events by time 
        events.Sort((e1, e2) => DateTime.Compare(e1.InputTime, e2.InputTime)); 

        foreach (MotionControllerEventArgs evt in events) 
        { 
            if (evt.IsPressed && (InputPressed != null)) 
            { 
                InputPressed(this, evt); 
            } 
            else if (!evt.IsPressed && (InputReleased != null)) 
            { 
                InputReleased(this, evt); 
            } 
        } 
    } 
    else 
    { 
        // As we do not predict button presses and the timestamp of the next e is in the future 
        // DateTime.Now is correct in this context as it will return the latest e of controllers 
        // which is the best we have at the moment for the frame. 
        var now = DateTime.Now; 
        lock (_controllers) 
        { 
            foreach (var controller in _controllers) 
            { 
                controller.Value.Update(now); 
            } 
        } 
    } 
} 
```

Die Struktur in den obigen Codebeispielen macht das Registrieren von Ereignissen viel besser lesbar: 

```csharp
public InteractionSourceHandedness handedness; 
public Microsoft.MixedReality.Input.ControllerInput redButton;

// Start of the Mono Behavior: register handlers for events from cache 
void Start() 
{ 
    var stateCache = gameObject.GetComponent<MotionControllerStateCache>(); 
    stateCache.InputPressed += stateCache_InputPressed; 
    stateCache.InputReleased += stateCache_InputReleased; 
    … 
} 

// Called when a button is released 
private void stateCache_InputReleased(object sender, MotionControllerStateCache.MotionControllerEventArgs e) 
{ 
    if ((e.SourceHandedness == handedness) && (e.Input == redButton)) 
    { 
        … 
    } 
} 

// Called when a button is pressed 
private void stateCache_InputPressed(object sender, MotionControllerStateCache.MotionControllerEventArgs e) 
{ 
    if ((e.SourceHandedness == handedness) && (e.Input == redButton)) 
    { 
        … 
    } 
} 
```

## <a name="see-also"></a>Siehe auch

<!-- ## Getting started

There's no additional setup required to use the HP Reverb G2 controller if you're developing for SteamVR or using the Windows Mixed Reality Input API (XR.WSA.Input). However, the A, B, X, Y buttons and the squeeze trigger are not currently accessible through the Input Manager unless you're using SteamVR. Support for the extra Reverb G2 inputs will be available in the near future, so be sure to check back!

## Porting existing applications

If you already have an existing app that you're developing for Windows Mixed Reality immersive headsets, check out our [porting guide](../porting-apps/porting-guides.md) and [project settings](../porting-apps/porting-guides.md?tabs=project#unity-porting-guidance) sections for general suggestions.

## Mapping input

When you're ready to get your input mapping up and running for your new controllers, start at the [input mapping](../porting-apps/porting-guides.md?tabs=input#unity-porting-guidance) section of the immersive porting guide. Instructions on how to configure inputs in Unity is detailed in [Gestures and motion controllers](gestures-and-motion-controllers-in-unity.md), along with a full [button and axis mapping table](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) for reference.

## See also
* [Updating for SteamVR](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md) -->