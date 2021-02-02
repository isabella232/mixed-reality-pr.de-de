---
title: HP-Reverb-G2-Controller in Unity
description: Erfahren Sie, wie Sie die neuen HP-Hall-G2-Controller in den Unity-Anwendungen steamvr und Windows Mixed Reality einrichten und verwenden.
author: hferrone
ms.author: v-hferrone
ms.date: 10/14/2020
ms.topic: article
keywords: Unity, Reverb, Reverb G2, HP-Simulator G2, gemischte Realität, Entwicklung, Motion Controller, Benutzereingaben, Features, neues Projekt, Emulator, Dokumentation, Anleitungen, Features, Hologramme, Spieleentwicklung
ms.openlocfilehash: 26435ef57c9baf59b1008fb4750aedd913a19814
ms.sourcegitcommit: 1304f8f0a838290c1ae3db34670b67c75ea9bdaa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2021
ms.locfileid: "99421393"
---
# <a name="hp-reverb-g2-controllers-in-unity"></a><span data-ttu-id="23da2-104">HP-Reverb-G2-Controller in Unity</span><span class="sxs-lookup"><span data-stu-id="23da2-104">HP Reverb G2 Controllers in Unity</span></span>

<span data-ttu-id="23da2-105">HP Motion Controller sind eine völlig neue Art von Windows Mixed Reality-Controllern: die gleiche nach Verfolgungs Technologie mit einem etwas anderen Satz verfügbarer Eingaben:</span><span class="sxs-lookup"><span data-stu-id="23da2-105">HP Motion controllers are a brand new type of Windows Mixed Reality controllers: all the same tracking technology with a slightly different set of available inputs:</span></span> 

* <span data-ttu-id="23da2-106">Touchpad wurde durch zwei Schaltflächen ersetzt: A und B für den rechten Controller und X und Y für den linken Controller.</span><span class="sxs-lookup"><span data-stu-id="23da2-106">Touchpad has been replaced by two buttons: A and B for the right controller, and X and Y for the left controller.</span></span> 
* <span data-ttu-id="23da2-107">"Grasp" ist jetzt ein-auslöst, der einen Datenstrom von Werten zwischen 0,0 und 1,0 anstelle einer Schaltfläche mit gedrückten und nicht gedrückten Zuständen veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="23da2-107">Grasp is now a trigger that publishes a stream of values between 0.0 and 1.0 instead of a button with Pressed and Not Pressed states.</span></span> 

<span data-ttu-id="23da2-108">Da die neuen Eingaben nicht über vorhandene Windows-und Unity-APIs zugänglich sind, benötigen Sie das dedizierte **Microsoft. mixedreality. Input** UPM-Paket.</span><span class="sxs-lookup"><span data-stu-id="23da2-108">Since the new inputs aren't accessible through existing Windows and Unity APIs, you need the dedicated **Microsoft.MixedReality.Input** UPM Package.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="23da2-109">**Die Klassen in diesem Paket werden nicht durch vorhandene Windows-und Unity-APIs ersetzt, sondern ergänzt.**</span><span class="sxs-lookup"><span data-stu-id="23da2-109">**Classes in this package do not replace existing Windows and Unity APIs but complement them.**</span></span> <span data-ttu-id="23da2-110">Features, die allgemein für klassische Windows Mixed Reality-Controller und HP Motion Controller verfügbar sind, können über denselben Codepfad mithilfe vorhandener APIs aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="23da2-110">Features commonly available to both classic Windows Mixed Reality controllers and HP Motion Controllers are accessible through the same code path using existing APIs.</span></span> <span data-ttu-id="23da2-111">Nur für die neuen Eingaben ist die Verwendung des zusätzlichen Pakets "Microsoft. mixedreality. Input" erforderlich.</span><span class="sxs-lookup"><span data-stu-id="23da2-111">Only the new inputs require the use of the additional Microsoft.MixedReality.Input package.</span></span> 

## <a name="hp-motion-controller-overview"></a><span data-ttu-id="23da2-112">Übersicht über den HP Motion Controller</span><span class="sxs-lookup"><span data-stu-id="23da2-112">HP Motion Controller overview</span></span>

<span data-ttu-id="23da2-113">*Microsoft. mixedreality. Input. mutioncontroller* stellt einen Bewegungs Controller dar.</span><span class="sxs-lookup"><span data-stu-id="23da2-113">*Microsoft.MixedReality.Input.MotionController* represents a motion controller.</span></span> <span data-ttu-id="23da2-114">Jede Instanz von " *mutioncontroller* " weist einen *XR auf. WSA. Input. interaktionsource* -Peer, der mithilfe von häntigkeit, Hersteller-ID, Produkt-ID und Version korreliert werden kann.</span><span class="sxs-lookup"><span data-stu-id="23da2-114">Each *MotionController* instance has an *XR.WSA.Input.InteractionSource* peer, which can be correlated using handedness, vendor ID, product ID, and version.</span></span> 

<span data-ttu-id="23da2-115">Sie können die "mutioncontroller"-Instanzen durch Erstellen eines " *mutioncontrollerwatcher* "-Instanzen erfassen und deren Ereignisse abonnieren, ähnlich wie bei der Verwendung von *Interaction Manager* -Ereignissen zum Ermitteln neuer *Interaction Source* -Instanzen.</span><span class="sxs-lookup"><span data-stu-id="23da2-115">You can grab MotionController instances by creating a *MotionControllerWatcher* and subscribing to its events, similar to using *InteractionManager* events to discover new *InteractionSource* instances.</span></span> <span data-ttu-id="23da2-116">Die Methoden und Eigenschaften von "mutioncontroller" beschreiben die Eingaben, die vom Controller unterstützt werden, einschließlich der Schaltflächen, Trigger, 2D-Achse und des Finger Anglers.</span><span class="sxs-lookup"><span data-stu-id="23da2-116">The MotionController’s methods and properties describe the inputs supported by the controller, including its buttons, triggers, 2D axis, and thumbstick.</span></span> <span data-ttu-id="23da2-117">Die Klasse "mutioncontroller" macht auch Methoden für den Zugriff auf Eingabe Zustände über die Klasse *"Klasse"* verfügbar.</span><span class="sxs-lookup"><span data-stu-id="23da2-117">The MotionController class also exposes methods for accessing input states through the *MotionControllerReading* class.</span></span> <span data-ttu-id="23da2-118">Die Klasse "mutioncontrollerreading" stellt eine Momentaufnahme des Controller Zustands zu einem bestimmten Zeitpunkt dar.</span><span class="sxs-lookup"><span data-stu-id="23da2-118">The MotionControllerReading class represents a snapshot of the controller’s state at a given time.</span></span> 

## <a name="installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool"></a><span data-ttu-id="23da2-119">Installieren von Microsoft. mixedreality. Input mit dem Feature-Tool Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="23da2-119">Installing Microsoft.MixedReality.Input with the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="23da2-120">Installieren Sie das Plug-in "Microsoft. mixedreality. Input" mit der neuen Anwendung Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="23da2-120">Install the Microsoft.MixedReality.Input plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="23da2-121">Befolgen Sie die [Installations-und Verwendungs Anweisungen](welcome-to-mr-feature-tool.md) , und wählen Sie in der Kategorie Mixed Reality Toolkit das **gemischte Eingabe** Paket aus:</span><span class="sxs-lookup"><span data-stu-id="23da2-121">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality Input** package in the Mixed Reality Toolkit category:</span></span>

![Gemischtes Fenster mit gemischter Reality-Eingabe hervorgehoben](images/feature-tool-mrinput.png)

## <a name="using-microsoftmixedrealityinput"></a><span data-ttu-id="23da2-123">Verwenden von "Microsoft. mixedreality. Input"</span><span class="sxs-lookup"><span data-stu-id="23da2-123">Using Microsoft.MixedReality.Input</span></span> 

### <a name="input-values"></a><span data-ttu-id="23da2-124">Eingabewerte</span><span class="sxs-lookup"><span data-stu-id="23da2-124">Input values</span></span>

<span data-ttu-id="23da2-125">Ein "mutioncontroller" kann zwei Arten von Eingaben verfügbar machen:</span><span class="sxs-lookup"><span data-stu-id="23da2-125">A MotionController can expose two kinds of inputs:</span></span> 

* <span data-ttu-id="23da2-126">Schaltflächen und Auslöse Zustände werden durch einen eindeutigen float-Wert zwischen 0,0 und 1,0 ausgedrückt, der angibt, wie stark Sie gedrückt werden.</span><span class="sxs-lookup"><span data-stu-id="23da2-126">Buttons and trigger states are expressed by a unique float value between 0.0 and 1.0 that indicates how much they're pressed.</span></span>
    * <span data-ttu-id="23da2-127">Eine Schaltfläche kann nur 0,0 (wenn nicht gedrückt) oder 1,0 (beim Drücken) zurückgeben, während ein-ausgelöst fortlaufende Werte zwischen 0,0 (vollständig freigegeben) und 1,0 (vollständig gedrückt) zurückgeben kann.</span><span class="sxs-lookup"><span data-stu-id="23da2-127">A button can only return 0.0 (when not pressed) or 1.0 (when pressed) while a trigger can return continuous values between 0.0 (fully released) to 1.0 (fully pressed).</span></span> 
* <span data-ttu-id="23da2-128">Der Fingerabdruck Zustand wird durch ein Vector2 ausgedrückt, dessen X-und Y-Komponenten zwischen-1,0 und 1,0 liegen.</span><span class="sxs-lookup"><span data-stu-id="23da2-128">Thumbstick state is expressed by a Vector2 whose X and Y components are between -1.0 and 1.0.</span></span> 

<span data-ttu-id="23da2-129">Mithilfe von " *wtioncontroller. getpressableinputs ()* " können Sie eine Liste von Eingaben zurückgeben, die einen gedrückten Wert (Schaltflächen und Trigger) zurückgeben, oder die Methode " *wtioncontroller. getxyinputs ()* ", um eine Liste von Eingaben zurückzugeben, die einen Wert von 2 Achsen zurückgeben</span><span class="sxs-lookup"><span data-stu-id="23da2-129">You can use *MotionController.GetPressableInputs()* to return a list of inputs returning a pressed value (buttons and triggers) or the *MotionController.GetXYInputs()* method to return a list of inputs returning a 2-axis value.</span></span> 

<span data-ttu-id="23da2-130">Eine "mutioncontrollerreading"-Instanz stellt den Zustand des Controllers zu einem bestimmten Zeitpunkt dar:</span><span class="sxs-lookup"><span data-stu-id="23da2-130">A MotionControllerReading instance represents the state of the controller at a given time:</span></span> 

* <span data-ttu-id="23da2-131">*Getpressedvalue ()* Ruft den Zustand einer Schaltfläche oder eines Auslösers ab.</span><span class="sxs-lookup"><span data-stu-id="23da2-131">*GetPressedValue()* retrieves the state of a button or a trigger.</span></span> 
* <span data-ttu-id="23da2-132">*Getxyvalue ()* Ruft den Status eines thumbsticks ab.</span><span class="sxs-lookup"><span data-stu-id="23da2-132">*GetXYValue()* retrieves the state of a thumbstick.</span></span> 

### <a name="creating-a-cache-to-maintain-a-collection-of-motioncontroller-instances-and-their-states"></a><span data-ttu-id="23da2-133">Erstellen eines Caches zum Verwalten einer Sammlung von "mtioncontroller"-Instanzen und deren Zuständen</span><span class="sxs-lookup"><span data-stu-id="23da2-133">Creating a cache to maintain a collection of MotionController instances and their states</span></span> 

<span data-ttu-id="23da2-134">Beginnen Sie mit dem Instanziieren eines "wtioncontrollerwatcher" und dem Registrieren von Handlern für die Ereignisse " *mutioncontrolleradded* " und " *wtioncontrollerremoved* ", um einen Cache verfügbarer "mutioncontroller"-Instanzen beizubehalten</span><span class="sxs-lookup"><span data-stu-id="23da2-134">Start by instantiating a MotionControllerWatcher and registering handlers for its *MotionControllerAdded* and *MotionControllerRemoved* events to keep a cache of available MotionController instances.</span></span> <span data-ttu-id="23da2-135">Dieser Cache sollte ein monobehavior-Objekt sein, das an ein gameobject-Objekt angefügt ist, wie im folgenden Code gezeigt:</span><span class="sxs-lookup"><span data-stu-id="23da2-135">This cache should be a MonoBehavior attached to a GameObject as demonstrated in the following code:</span></span>

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

### <a name="reading-new-inputs-by-polling"></a><span data-ttu-id="23da2-136">Lesen von neuen Eingaben durch Abrufen</span><span class="sxs-lookup"><span data-stu-id="23da2-136">Reading new inputs by polling</span></span> 

<span data-ttu-id="23da2-137">Sie können den aktuellen Status jedes bekannten Controllers über " *mutioncontroller. trygetreadingattime* " während der *Update* -Methode der monobehavior-Klasse lesen.</span><span class="sxs-lookup"><span data-stu-id="23da2-137">You can read the current state of each known controller through *MotionController.TryGetReadingAtTime* during the *Update* method of the MonoBehavior class.</span></span> <span data-ttu-id="23da2-138">Sie möchten *DateTime. Now* als Zeitstempel-Parameter übergeben, um sicherzustellen, dass der aktuelle Zustand des Controllers gelesen wird.</span><span class="sxs-lookup"><span data-stu-id="23da2-138">You want to pass *DateTime.Now* as the timestamp parameter to ensure that the latest state of the controller is read.</span></span> 

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

<span data-ttu-id="23da2-139">Sie können den aktuellen Eingabe Wert des Controllers mithilfe der häntigkeit des Controllers erfassen:</span><span class="sxs-lookup"><span data-stu-id="23da2-139">You can grab the controllers current input value using the Handedness of the controller:</span></span> 

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

<span data-ttu-id="23da2-140">Um z. b. den analogen Wert von "interaktionsource" zu lesen:</span><span class="sxs-lookup"><span data-stu-id="23da2-140">For example, to read the analog grasp value of an InteractionSource:</span></span> 

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

### <a name="generating-events-from-the-new-inputs"></a><span data-ttu-id="23da2-141">Erstellen von Ereignissen aus den neuen Eingaben</span><span class="sxs-lookup"><span data-stu-id="23da2-141">Generating events from the new inputs</span></span> 

<span data-ttu-id="23da2-142">Anstatt den Zustand eines Controllers einmal pro Frame abzufragen, haben Sie die Möglichkeit, alle Zustandsänderungen als Ereignisse zu behandeln, sodass Sie auch die schnellsten Aktionen verarbeiten können, die kleiner als ein Frame sind.</span><span class="sxs-lookup"><span data-stu-id="23da2-142">Instead of polling for a controller's state once per frame, you have the option of handling all state changes as events, which lets you handle even the quickest actions lasting less than a frame.</span></span> <span data-ttu-id="23da2-143">Damit dieser Ansatz funktioniert, muss der Cache der Motion-Controller alle Zustände verarbeiten, die seit dem letzten Frame von einem Controller veröffentlicht wurden. Sie können dies tun, indem Sie den Zeitstempel des letzten von einem "mutioncontroller" abgerufenen "comtioncontrollerreading" Speichern und " *mutioncontroller. trygetreadingaftertime ()*" aufrufen:</span><span class="sxs-lookup"><span data-stu-id="23da2-143">In order for this approach to work, the cache of motion controllers needs to process all states published by a controller since the last frame, which you can do by storing the timestamp of the last MotionControllerReading retrieved from a MotionController and calling *MotionController.TryGetReadingAfterTime()*:</span></span> 

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

<span data-ttu-id="23da2-144">Nachdem Sie nun die internen Cache Klassen aktualisiert haben, kann die monobehavior-Klasse zwei Ereignisse – gedrückt und freigegeben – verfügbar machen und Sie über die Update ()-Methode aufrufen:</span><span class="sxs-lookup"><span data-stu-id="23da2-144">Now that you've updated the cache internal classes, the MonoBehavior class can expose two events – Pressed and Released – and raise them from its Update() method:</span></span> 

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

<span data-ttu-id="23da2-145">Die Struktur in den obigen Codebeispielen macht das Registrieren von Ereignissen viel besser lesbar:</span><span class="sxs-lookup"><span data-stu-id="23da2-145">The structure in the above code examples makes registering events much more readable:</span></span> 

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

## <a name="see-also"></a><span data-ttu-id="23da2-146">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="23da2-146">See also</span></span>

<!-- ## Getting started

There's no additional setup required to use the HP Reverb G2 controller if you're developing for SteamVR or using the Windows Mixed Reality Input API (XR.WSA.Input). However, the A, B, X, Y buttons and the squeeze trigger are not currently accessible through the Input Manager unless you're using SteamVR. Support for the extra Reverb G2 inputs will be available in the near future, so be sure to check back!

## Porting existing applications

If you already have an existing app that you're developing for Windows Mixed Reality immersive headsets, check out our [porting guide](../porting-apps/porting-guides.md) and [project settings](../porting-apps/porting-guides.md?tabs=project#unity-porting-guidance) sections for general suggestions.

## Mapping input

When you're ready to get your input mapping up and running for your new controllers, start at the [input mapping](../porting-apps/porting-guides.md?tabs=input#unity-porting-guidance) section of the immersive porting guide. Instructions on how to configure inputs in Unity is detailed in [Gestures and motion controllers](gestures-and-motion-controllers-in-unity.md), along with a full [button and axis mapping table](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) for reference.

## See also
* [Updating for SteamVR](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md) -->