---
title: HP-Reverb-G2-Controller in Unity
description: Anweisungen zur Verwendung der HP-Reverb-G2-Controller in steamvr und Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 10/14/2020
ms.topic: article
keywords: Unity, Reverb, Reverb G2, HP-Simulator G2, gemischte Realität, Entwicklung, Motion Controller, Benutzereingaben, Features, neues Projekt, Emulator, Dokumentation, Anleitungen, Features, Hologramme, Spieleentwicklung
ms.openlocfilehash: 17f373a3d94740bf103821b85ee5d6fe4dbaa11f
ms.sourcegitcommit: 8b16945d6a551f174a65fa3980ba392682ca45d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2020
ms.locfileid: "92886253"
---
# <a name="hp-reverb-g2-controllers-in-unity"></a>HP-Reverb-G2-Controller in Unity

HP Motion Controller sind eine völlig neue Art von Windows Mixed Reality-Controllern: die gleiche nach Verfolgungs Technologie mit einem etwas anderen Satz verfügbarer Eingaben: 

* Touchpad wurde durch zwei Schaltflächen ersetzt: A und B für den rechten Controller und X und Y für den linken Controller. 
* "Grasp" ist jetzt ein-auslöst, der einen Datenstrom von Werten zwischen 0,0 und 1,0 anstelle einer Schaltfläche mit gedrückten und nicht gedrückten Zuständen veröffentlicht. 

Da die neuen Eingaben nicht über vorhandene Windows-und Unity-APIs zugänglich sind, benötigen Sie das dedizierte **Microsoft. mixedreality. Input** UPM-Paket. 

> [!IMPORTANT]
> **Die Klassen in diesem Paket werden nicht durch vorhandene Windows-und Unity-APIs ersetzt, sondern ergänzt.** Features, die allgemein für klassische Windows Mixed Reality-Controller und HP Motion Controller verfügbar sind, können über denselben Codepfad mithilfe vorhandener APIs aufgerufen werden. Nur für die neuen Eingaben ist die Verwendung des zusätzlichen Pakets "Microsoft. mixedreality. Input" erforderlich. 

## <a name="hp-motion-controller-overview"></a>Übersicht über den HP Motion Controller

*Microsoft. mixedreality. Input. mutioncontroller* stellt einen Bewegungs Controller dar. Jede Instanz von " *mutioncontroller* " weist einen *XR auf. WSA. Input. interaktionsource* -Peer, der mithilfe von häntigkeit, Hersteller-ID, Produkt-ID und Version korreliert werden kann. 

Sie können die "mutioncontroller"-Instanzen durch Erstellen eines " *mutioncontrollerwatcher* "-Instanzen erfassen und deren Ereignisse abonnieren, ähnlich wie bei der Verwendung von *Interaction Manager* -Ereignissen zum Ermitteln neuer *Interaction Source* -Instanzen. Die Methoden und Eigenschaften von "mutioncontroller" beschreiben die Eingaben, die vom Controller unterstützt werden, einschließlich der Schaltflächen, Trigger, 2D-Achse und des Finger Anglers. Die Klasse "mutioncontroller" macht auch Methoden für den Zugriff auf Eingabe Zustände über die Klasse *"Klasse"* verfügbar. Die Klasse "mutioncontrollerreading" stellt eine Momentaufnahme des Controller Zustands zu einem bestimmten Zeitpunkt dar. 

## <a name="installing-microsoftmixedrealityinput-using-the-unity-package-manager"></a>Installieren von Microsoft. mixedreality. Input mithilfe des Unity-Paket-Managers 

Der Unity-Paket-Manager verwendet eine [Manifest-Datei](https://docs.unity3d.com/Manual/upm-manifestPkg.html) (manifest.json), um zu bestimmen, welche Pakete installiert werden müssen, und die Registrierungen (Server), aus denen Sie installiert werden können. Bevor Sie das Microsoft. mixedreality. Input-Paket verwenden können, müssen Sie den gemischten Reality-Komponenten Server registrieren.

### <a name="registering-the-mixed-reality-component-server"></a>Registrieren des gemischten Reality-Komponenten Servers 

Für jedes Projekt, das das gemischte Reality-Eingabe Paket verwendet, muss für die manifest.jsfür die Datei (im Ordner "Pakete") die gemischte Registrierungs Bereichs bezogene Registrierung hinzugefügt werden. So ändern Sie manifest.jsauf, um gemischte Realität zu unterstützen: 
    1. Öffnen Sie <projectRoot> /Packages/manifest.jsin einem Text-Editor, z. b. Visual Studio Code. 
    2. Fügen Sie am Anfang der Manifestressource dem Bereich für die Bereichs bezogene Registrierung den Mixed Reality-Server hinzu, und speichern Sie die Datei. 
    
<pre>
{ 
  "scopedRegistries": [ 
    { 
      "name": "Microsoft Mixed Reality", 
      "url": "https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/", 
      "scopes": [ 
        "com.microsoft.mixedreality" 
      ] 
    } 
  ], 
</pre>

### <a name="adding-the-microsoftmixedrealityinput-package"></a>Hinzufügen des Pakets "Microsoft. mixedreality. Input" 

Ändern Sie den Abschnitt Abhängigkeiten der <projectRoot> Datei/Packages/manifest.jsin der Datei im Text-Editor, um das Paket com. Microsoft. mixedreality. Input hinzuzufügen und die Datei zu speichern. 

<pre>
  "dependencies": { 
    "com.microsoft.mixedreality.input": "0.9.2006", 
  }
</pre>

## <a name="using-microsoftmixedrealityinput"></a>Verwenden von "Microsoft. mixedreality. Input" 

### <a name="input-values"></a>Eingabewerte

Ein "mutioncontroller" kann zwei Arten von Eingaben verfügbar machen: 

* Schaltflächen und Auslöse Zustände werden durch einen eindeutigen float-Wert zwischen 0,0 und 1,0 ausgedrückt, der angibt, wie stark Sie gedrückt werden.
    * Eine Schaltfläche kann nur 0,0 (wenn nicht gedrückt) oder 1,0 (beim Drücken) zurückgeben, während ein-ausgelöst fortlaufende Werte zwischen 0,0 (vollständig freigegeben) und 1,0 (vollständig gedrückt) zurückgeben kann. 
* Der Fingerabdruck Zustand wird durch ein Vector2 ausgedrückt, dessen X-und Y-Komponenten zwischen-1,0 und 1,0 liegen. 

Mithilfe von " *wtioncontroller. getpressableinputs ()* " können Sie eine Liste von Eingaben zurückgeben, die einen gedrückten Wert (Schaltflächen und Trigger) zurückgeben, oder die Methode " *wtioncontroller. getxyinputs ()* ", um eine Liste von Eingaben zurückzugeben, die einen Wert von 2 Achsen zurückgeben 

Eine "mutioncontrollerreading"-Instanz stellt den Zustand des Controllers zu einem bestimmten Zeitpunkt dar: 

* *Getpressedvalue ()* Ruft den Zustand einer Schaltfläche oder eines Auslösers ab. 
* *Getxyvalue ()* Ruft den Status eines thumbsticks ab. 

### <a name="creating-a-cache-to-maintain-a-collection-of-motioncontroller-instances-and-their-states"></a>Erstellen eines Caches zum Verwalten einer Sammlung von "mtioncontroller"-Instanzen und deren Zuständen 

Beginnen Sie mit dem Instanziieren eines "wtioncontrollerwatcher" und dem Registrieren von Handlern für die Ereignisse " *mutioncontrolleradded* " und " *wtioncontrollerremoved* ", um einen Cache verfügbarer "mutioncontroller"-Instanzen beizubehalten Dieser Cache sollte ein monobehavior-Objekt sein, das an ein gameobject-Objekt angefügt ist, wie im folgenden Code gezeigt:

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

### <a name="reading-new-inputs-by-polling"></a>Lesen von neuen Eingaben durch Abrufen 

Sie können den aktuellen Status jedes bekannten Controllers über " *mutioncontroller. trygetreadingattime* " während der *Update* -Methode der monobehavior-Klasse lesen. Sie möchten *DateTime. Now* als Zeitstempel-Parameter übergeben, um sicherzustellen, dass der aktuelle Zustand des Controllers gelesen wird. 

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

Sie können den aktuellen Eingabe Wert des Controllers mithilfe der häntigkeit des Controllers erfassen: 

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

Um z. b. den analogen Wert von "interaktionsource" zu lesen: 

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

### <a name="generating-events-from-the-new-inputs"></a>Erstellen von Ereignissen aus den neuen Eingaben 

Anstatt den Zustand eines Controllers einmal pro Frame abzufragen, haben Sie die Möglichkeit, alle Zustandsänderungen als Ereignisse zu behandeln, sodass Sie auch die schnellsten Aktionen verarbeiten können, die kleiner als ein Frame sind. Damit dieser Ansatz funktioniert, muss der Cache der Motion-Controller alle Zustände verarbeiten, die seit dem letzten Frame von einem Controller veröffentlicht wurden. Sie können dies tun, indem Sie den Zeitstempel des letzten von einem "mutioncontroller" abgerufenen "comtioncontrollerreading" Speichern und " *mutioncontroller. trygetreadingaftertime ()* " aufrufen: 

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

Nachdem Sie nun die internen Cache Klassen aktualisiert haben, kann die monobehavior-Klasse zwei Ereignisse – gedrückt und freigegeben – verfügbar machen und Sie über die Update ()-Methode aufrufen: 

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

## <a name="see-also"></a>Weitere Informationen

<!-- ## Getting started

There's no additional setup required to use the HP Reverb G2 controller if you're developing for SteamVR or using the Windows Mixed Reality Input API (XR.WSA.Input). However, the A, B, X, Y buttons and the squeeze trigger are not currently accessible through the Input Manager unless you're using SteamVR. Support for the extra Reverb G2 inputs will be available in the near future, so be sure to check back!

## Porting existing applications

If you already have an existing app that you're developing for Windows Mixed Reality immersive headsets, check out our [porting guide](../porting-apps/porting-guides.md) and [project settings](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) sections for general suggestions.

## Mapping input

When you're ready to get your input mapping up and running for your new controllers, start at the [input mapping](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) section of the immersive porting guide. Instructions on how to configure inputs in Unity is detailed in [Gestures and motion controllers](gestures-and-motion-controllers-in-unity.md), along with a full [button and axis mapping table](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) for reference.

## See also
* [Updating for SteamVR](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md) -->