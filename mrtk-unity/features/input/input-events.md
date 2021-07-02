---
title: Eingabeereignisse
description: Dokumentation für InputEvents im MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Ereignisse,
ms.openlocfilehash: c8871aa575e2aa4507e9dbbdcc8bdf0fc0604633
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176781"
---
# <a name="input-events"></a><span data-ttu-id="dcd04-104">Eingabeereignisse</span><span class="sxs-lookup"><span data-stu-id="dcd04-104">Input events</span></span>

<span data-ttu-id="dcd04-105">In der folgenden Liste sind alle verfügbaren Eingabeereignisschnittstellen aufgeführt, die von einer benutzerdefinierten MonoBehaviour-Komponente implementiert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="dcd04-105">The list below outlines all available input event interfaces to be implemented by a custom MonoBehaviour component.</span></span> <span data-ttu-id="dcd04-106">Diese Schnittstellen werden vom MRTK-Eingabesystem aufgerufen, um benutzerdefinierte App-Logik basierend auf Benutzereingabeinteraktionen zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="dcd04-106">These interfaces will be called by the MRTK input system to handle custom app logic based on user input interactions.</span></span> <span data-ttu-id="dcd04-107">[Zeigereingabeereignisse werden](pointers.md#pointer-event-interfaces) etwas anders behandelt als die unten angegebenen Standardeingabeereignistypen.</span><span class="sxs-lookup"><span data-stu-id="dcd04-107">[Pointer input events](pointers.md#pointer-event-interfaces) are handled slightly differently than the standard input event types below.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dcd04-108">Standardmäßig erhält ein Skript nur Dann Eingabeereignisse, wenn es sich um das GameObject im Fokus eines Zeigers oder übergeordneten Elements eines GameObject im Fokus handelt.</span><span class="sxs-lookup"><span data-stu-id="dcd04-108">By default, a script will receive input events only if it is the GameObject in focus by a pointer or parent of a GameObject in focus.</span></span>

| <span data-ttu-id="dcd04-109">Handler</span><span class="sxs-lookup"><span data-stu-id="dcd04-109">Handler</span></span> | <span data-ttu-id="dcd04-110">Events</span><span class="sxs-lookup"><span data-stu-id="dcd04-110">Events</span></span> | <span data-ttu-id="dcd04-111">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="dcd04-111">Description</span></span> |
| --- | :---: | --- |
| [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | <span data-ttu-id="dcd04-112">Quelle erkannt/verloren</span><span class="sxs-lookup"><span data-stu-id="dcd04-112">Source Detected / Lost</span></span> | <span data-ttu-id="dcd04-113">Wird ausgelöst, wenn eine Eingabequelle erkannt wird oder verloren geht, z. B. wenn eine artikulierte Hand erkannt wird oder verloren geht.</span><span class="sxs-lookup"><span data-stu-id="dcd04-113">Raised when an input source is detected/lost, like when an articulated hand is detected or lost track of.</span></span> |
| [`IMixedRealitySourcePoseHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourcePoseHandler) | <span data-ttu-id="dcd04-114">Quellpose geändert</span><span class="sxs-lookup"><span data-stu-id="dcd04-114">Source Pose Changed</span></span> | <span data-ttu-id="dcd04-115">Wird bei Änderungen der Quellpose ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="dcd04-115">Raised on source pose changes.</span></span> <span data-ttu-id="dcd04-116">Die Quellpose stellt die allgemeine Pose der Eingabequelle dar.</span><span class="sxs-lookup"><span data-stu-id="dcd04-116">The source pose represents the general pose of the input source.</span></span> <span data-ttu-id="dcd04-117">Bestimmte Posen wie Greif- oder Zeigerpose in einem sechs DOF-Controller können über ermittelt `IMixedRealityInputHandler<MixedRealityPose>` werden.</span><span class="sxs-lookup"><span data-stu-id="dcd04-117">Specific poses, like the grip or pointer pose in a six DOF controller, can be obtained via `IMixedRealityInputHandler<MixedRealityPose>`.</span></span> |
| [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | <span data-ttu-id="dcd04-118">Eingabe nach unten/nach oben</span><span class="sxs-lookup"><span data-stu-id="dcd04-118">Input Down / Up</span></span> | <span data-ttu-id="dcd04-119">Wird bei Änderungen an binären Eingaben wie Schaltflächen ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="dcd04-119">Raised on changes to binary inputs like buttons.</span></span> |
| [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | <span data-ttu-id="dcd04-120">Eingabe geändert</span><span class="sxs-lookup"><span data-stu-id="dcd04-120">Input Changed</span></span> | <span data-ttu-id="dcd04-121">Wird bei Änderungen an Eingaben des angegebenen Typs ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="dcd04-121">Raised on changes to inputs of the given type.</span></span> <span data-ttu-id="dcd04-122">**T** kann die folgenden Werte verwenden:</span><span class="sxs-lookup"><span data-stu-id="dcd04-122">**T** can take the following values:</span></span> <br/> <span data-ttu-id="dcd04-123">- *float* (z. B. gibt einen analogen Trigger zurück)</span><span class="sxs-lookup"><span data-stu-id="dcd04-123">- *float* (e.g returns analog trigger)</span></span><br/> <span data-ttu-id="dcd04-124">- *Vector2* (gibt z.B. die Gamepad-Thumbstickrichtung zurück)</span><span class="sxs-lookup"><span data-stu-id="dcd04-124">- *Vector2* (e.g returns gamepad thumbstick direction)</span></span> <br/> <span data-ttu-id="dcd04-125">- *Vector3* (z.B. Rückgabeposition des nachverfolgten Geräts)</span><span class="sxs-lookup"><span data-stu-id="dcd04-125">- *Vector3* (e.g return position of tracked device)</span></span> <br/> <span data-ttu-id="dcd04-126">- *Quaternion* (gibt z. B. die Ausrichtung des nachverfolgten Geräts zurück)</span><span class="sxs-lookup"><span data-stu-id="dcd04-126">- *Quaternion* (e.g returns orientation of tracked device)</span></span><br/> <span data-ttu-id="dcd04-127">- [MixedRealityPose](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) (z. B. gibt das vollständig nachverfolgte Gerät zurück)</span><span class="sxs-lookup"><span data-stu-id="dcd04-127">- [MixedRealityPose](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) (e.g. returns fully tracked device)</span></span> |
| [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) | <span data-ttu-id="dcd04-128">Speech-Schlüsselwort erkannt</span><span class="sxs-lookup"><span data-stu-id="dcd04-128">Speech Keyword Recognized</span></span> | <span data-ttu-id="dcd04-129">Wird bei der Erkennung eines der Schlüsselwörter ausgelöst, die im *Speech-Befehlsprofil konfiguriert sind.*</span><span class="sxs-lookup"><span data-stu-id="dcd04-129">Raised on recognition of one of the keywords configured in the *Speech Commands Profile*.</span></span> |
| [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) | <span data-ttu-id="dcd04-130">Diktieren</span><span class="sxs-lookup"><span data-stu-id="dcd04-130">Dictation</span></span><br/> <span data-ttu-id="dcd04-131">Hypothesis</span><span class="sxs-lookup"><span data-stu-id="dcd04-131">Hypothesis</span></span> <br/> <span data-ttu-id="dcd04-132">Ergebnis</span><span class="sxs-lookup"><span data-stu-id="dcd04-132">Result</span></span> <br/> <span data-ttu-id="dcd04-133">Abgeschlossen</span><span class="sxs-lookup"><span data-stu-id="dcd04-133">Complete</span></span> <br/> <span data-ttu-id="dcd04-134">Fehler</span><span class="sxs-lookup"><span data-stu-id="dcd04-134">Error</span></span> | <span data-ttu-id="dcd04-135">Wird von Diktatsystemen ausgelöst, um die Ergebnisse einer Diktatsitzung zu melden.</span><span class="sxs-lookup"><span data-stu-id="dcd04-135">Raised by dictation systems to report the results of a dictation session.</span></span> |
| [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) | <span data-ttu-id="dcd04-136">Gestenereignisse für:</span><span class="sxs-lookup"><span data-stu-id="dcd04-136">Gesture events on:</span></span> <br/> <span data-ttu-id="dcd04-137">Gestartet</span><span class="sxs-lookup"><span data-stu-id="dcd04-137">Started</span></span> <br/> <span data-ttu-id="dcd04-138">Aktualisiert</span><span class="sxs-lookup"><span data-stu-id="dcd04-138">Updated</span></span> <br/> <span data-ttu-id="dcd04-139">Abgeschlossen</span><span class="sxs-lookup"><span data-stu-id="dcd04-139">Completed</span></span> <br/> <span data-ttu-id="dcd04-140">Canceled</span><span class="sxs-lookup"><span data-stu-id="dcd04-140">Canceled</span></span> | <span data-ttu-id="dcd04-141">Wird bei der Gestenerkennung ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="dcd04-141">Raised on gesture detection.</span></span> |
| [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | <span data-ttu-id="dcd04-142">Geste aktualisiert/abgeschlossen</span><span class="sxs-lookup"><span data-stu-id="dcd04-142">Gesture Updated / Completed</span></span> | <span data-ttu-id="dcd04-143">Wird bei erkennung von Gesten ausgelöst, die zusätzliche Daten des angegebenen Typs enthalten.</span><span class="sxs-lookup"><span data-stu-id="dcd04-143">Raised on detection of gestures containing additional data of the given type.</span></span> <span data-ttu-id="dcd04-144">Weitere [**Informationen zu möglichen**](gestures.md#gesture-events) Werten für T finden Sie unter Gestenereignisse. </span><span class="sxs-lookup"><span data-stu-id="dcd04-144">See [**gesture events**](gestures.md#gesture-events) for details on possible values for **T**.</span></span> |
| [`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) | <span data-ttu-id="dcd04-145">Handgelenke aktualisiert</span><span class="sxs-lookup"><span data-stu-id="dcd04-145">Hand Joints Updated</span></span> | <span data-ttu-id="dcd04-146">Wird von artikulierten Handcontrollern ausgelöst, wenn Handgelenke aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="dcd04-146">Raised by articulated hand controllers when hand joints are updated.</span></span> |
| [`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) | <span data-ttu-id="dcd04-147">Hand Mesh aktualisiert</span><span class="sxs-lookup"><span data-stu-id="dcd04-147">Hand Mesh Updated</span></span> | <span data-ttu-id="dcd04-148">Wird von artikulierten Handcontrollern ausgelöst, wenn ein Handgitternetz aktualisiert wird.</span><span class="sxs-lookup"><span data-stu-id="dcd04-148">Raised by articulated hand controllers when a hand mesh is updated.</span></span> |
| [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) | <span data-ttu-id="dcd04-149">Aktion gestartet/beendet</span><span class="sxs-lookup"><span data-stu-id="dcd04-149">Action Started / Ended</span></span> | <span data-ttu-id="dcd04-150">Wird zum Angeben des Aktionsstarts und -endes für Eingaben, die Aktionen zugeordnet sind, aus.</span><span class="sxs-lookup"><span data-stu-id="dcd04-150">Raise to indicate action start and end for inputs mapped to actions.</span></span> |

## <a name="input-events-in-action"></a><span data-ttu-id="dcd04-151">Eingabeereignisse in Aktion</span><span class="sxs-lookup"><span data-stu-id="dcd04-151">Input events in action</span></span>

<span data-ttu-id="dcd04-152">Auf Skriptebene können Eingabeereignisse verwendet werden, indem eine der in der obigen Tabelle gezeigten Ereignishandlerschnittstellen implementiert wird.</span><span class="sxs-lookup"><span data-stu-id="dcd04-152">At the script level, input events can be consumed by implementing one of the event handler interfaces shown in the table above.</span></span> <span data-ttu-id="dcd04-153">Wenn ein Eingabeereignis über eine Benutzerinteraktion erfolgt, findet Folgendes statt:</span><span class="sxs-lookup"><span data-stu-id="dcd04-153">When an input event fires via a user interaction, the following takes place:</span></span>

1. <span data-ttu-id="dcd04-154">Das MRTK-Eingabesystem erkennt, dass ein Eingabeereignis aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="dcd04-154">The MRTK input system recognizes that an input event has occurred.</span></span>
1. <span data-ttu-id="dcd04-155">Das MRTK-Eingabesystem gibt die relevante Schnittstellenfunktion des Eingabeereigniss für alle registrierten [globalen Eingabehandler aus.](#register-for-global-input-events)</span><span class="sxs-lookup"><span data-stu-id="dcd04-155">The MRTK input system fires the relevant interface function of the input event to all [registered global input handlers](#register-for-global-input-events)</span></span>
1. <span data-ttu-id="dcd04-156">Für jeden aktiven Zeiger, der beim Eingabesystem registriert ist:</span><span class="sxs-lookup"><span data-stu-id="dcd04-156">For every active pointer registered with the input system:</span></span>
    1. <span data-ttu-id="dcd04-157">Das Eingabesystem bestimmt, welches GameObject sich im Fokus für den aktuellen Zeiger befindet.</span><span class="sxs-lookup"><span data-stu-id="dcd04-157">The input system determines which GameObject is in focus for the current pointer.</span></span>
    1. <span data-ttu-id="dcd04-158">Das Eingabesystem verwendet [das Unity-Ereignissystem,](https://docs.unity3d.com/Manual/EventSystem.html) um die relevante Schnittstellenfunktion für alle übereinstimmenden Komponenten auf dem fokussierten GameObject zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="dcd04-158">The input system utilizes [Unity's event system](https://docs.unity3d.com/Manual/EventSystem.html) to fire the relevant interface function for all matching components on the focused GameObject.</span></span>
    1. <span data-ttu-id="dcd04-159">Wenn zu einem beliebigen Zeitpunkt ein Eingabeereignis als verwendet markiert [wurde,](#how-to-stop-input-events)wird der Prozess beendet, und keine weiteren GameObjects erhalten Rückrufe.</span><span class="sxs-lookup"><span data-stu-id="dcd04-159">If at any point an input event has been [marked as used](#how-to-stop-input-events), the process will end and no further GameObjects will receive callbacks.</span></span>
        - <span data-ttu-id="dcd04-160">Beispiel: Komponenten, die die Schnittstelle implementieren, werden [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) gesucht, wenn ein Sprachbefehl erkannt wird.</span><span class="sxs-lookup"><span data-stu-id="dcd04-160">Example: Components implementing the interface [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) will be searched for when a speech command is recognized.</span></span>
        - <span data-ttu-id="dcd04-161">Hinweis: Das Unity-Ereignissystem blasen hoch, um das übergeordnete GameObject zu durchsuchen, wenn im aktuellen GameObject keine Komponenten gefunden werden, die mit der gewünschten Schnittstelle übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="dcd04-161">Note: The Unity event system will bubble up to search the parent GameObject if no components matching the desired interface are found on the current GameObject.</span></span>
1. <span data-ttu-id="dcd04-162">Wenn keine globalen Eingabehandler registriert sind und kein GameObject mit einer übereinstimmenden Komponente/Schnittstelle gefunden wird, wird vom Eingabesystem jeder fallback registrierte Eingabehandler aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="dcd04-162">If no global input handlers are registered and no GameObject is found with a matching component/interface, then the input system will call each fallback registered input handler</span></span>

> [!NOTE]
> <span data-ttu-id="dcd04-163">[Zeigereingabeereignisse werden](pointers.md#pointer-event-interfaces) auf eine etwas andere Weise als die oben aufgeführten Eingabeereignisschnittstellen behandelt.</span><span class="sxs-lookup"><span data-stu-id="dcd04-163">[Pointer input events](pointers.md#pointer-event-interfaces) are handled in a slightly different manner than the input event interfaces listed above.</span></span> <span data-ttu-id="dcd04-164">Insbesondere werden Zeigereingabeereignisse nur vom GameObject im Fokus durch den Zeiger, der das Eingabeereignis ausgelöst hat, sowie alle globalen Eingabehandler behandelt.</span><span class="sxs-lookup"><span data-stu-id="dcd04-164">In particular, pointer input events are handled only by the GameObject in focus by the pointer that fired the input event - as well as any global input handlers.</span></span> <span data-ttu-id="dcd04-165">Reguläre Eingabeereignisse werden von GameObjects im Fokus für alle aktiven Zeiger behandelt.</span><span class="sxs-lookup"><span data-stu-id="dcd04-165">Regular input events are handled by GameObjects in focus for all active pointers.</span></span>

### <a name="input-event-interface-example"></a><span data-ttu-id="dcd04-166">Beispiel für eine Eingabeereignisschnittstelle</span><span class="sxs-lookup"><span data-stu-id="dcd04-166">Input event interface example</span></span>

<span data-ttu-id="dcd04-167">Der folgende Code veranschaulicht die Verwendung der [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) -Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="dcd04-167">The code below demonstrates use of the [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) interface.</span></span> <span data-ttu-id="dcd04-168">Wenn der Benutzer die Wörter "kleiner" oder "größer" sagt, während er sich auf ein GameObject mit dieser Klasse konzentriert, skaliert sich das GameObject um die Hälfte oder `ShowHideSpeechHandler` das Doppelte.</span><span class="sxs-lookup"><span data-stu-id="dcd04-168">When the user says the words "smaller" or "bigger" while focusing on a GameObject with this `ShowHideSpeechHandler` class, the GameObject will scale itself by half or twice as much.</span></span>

```c#
public class ShowHideSpeechHandler : MonoBehaviour, IMixedRealitySpeechHandler
{
    ...

    void IMixedRealitySpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.Command.Keyword == "smaller")
        {
            transform.localScale *= 0.5f;
        }
        else if (eventData.Command.Keyword == "bigger")
        {
            transform.localScale *= 2.0f;
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="dcd04-169">[`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler)Eingabeereignisse erfordern, dass die gewünschten Schlüsselwörter vorab im [MRTK Speech Commands Profile registriert sind.](speech.md)</span><span class="sxs-lookup"><span data-stu-id="dcd04-169">[`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) input events require that the desired keywords are pre-registered in the [MRTK Speech Commands Profile](speech.md).</span></span>

## <a name="register-for-global-input-events"></a><span data-ttu-id="dcd04-170">Registrieren für globale Eingabeereignisse</span><span class="sxs-lookup"><span data-stu-id="dcd04-170">Register for global input events</span></span>

<span data-ttu-id="dcd04-171">Eine Komponente muss sich beim Eingabesystem registrieren, um eine Komponente zu erstellen, die auf globale Eingabeereignisse lausiert, ohne zu ignorieren, welches GameObject sich möglicherweise im Fokus hat.</span><span class="sxs-lookup"><span data-stu-id="dcd04-171">To create a component that listens for global input events, disregarding what GameObject may be in focus, a component must register itself with the Input System.</span></span> <span data-ttu-id="dcd04-172">Nach der Registrierung empfangen alle Instanzen dieses MonoBehaviour-Objekts Eingabeereignisse zusammen mit allen GameObjects, die sich derzeit im Fokus befindet, und anderen globalen registrierten Listenern.</span><span class="sxs-lookup"><span data-stu-id="dcd04-172">Once registered, any instances of this MonoBehaviour will receive input events along with any GameObject(s) currently in focus and other global registered listeners.</span></span>

<span data-ttu-id="dcd04-173">Wenn ein Eingabeereignis als verwendet [markiert wurde,](#how-to-stop-input-events)empfangen globale registrierte Handler weiterhin Rückrufe.</span><span class="sxs-lookup"><span data-stu-id="dcd04-173">If an input event has been [marked as used](#how-to-stop-input-events), global registered handlers will still all receive callbacks.</span></span> <span data-ttu-id="dcd04-174">Das Ereignis wird jedoch nicht von GameObjects mit Fokus empfangen.</span><span class="sxs-lookup"><span data-stu-id="dcd04-174">However, no focused GameObjects will receive the event.</span></span>

### <a name="global-input-registration-example"></a><span data-ttu-id="dcd04-175">Beispiel für eine globale Eingaberegistrierung</span><span class="sxs-lookup"><span data-stu-id="dcd04-175">Global input registration example</span></span>

```c#
public class GlobalHandListenerExample : MonoBehaviour,
    IMixedRealitySourceStateHandler, // Handle source detected and lost
    IMixedRealityHandJointHandler // handle joint position updates for hands
{
    private void OnEnable()
    {
        // Instruct Input System that we would like to receive all input events of type
        // IMixedRealitySourceStateHandler and IMixedRealityHandJointHandler
        CoreServices.InputSystem?.RegisterHandler<IMixedRealitySourceStateHandler>(this);
        CoreServices.InputSystem?.RegisterHandler<IMixedRealityHandJointHandler>(this);
    }

    private void OnDisable()
    {
        // This component is being destroyed
        // Instruct the Input System to disregard us for input event handling
        CoreServices.InputSystem?.UnregisterHandler<IMixedRealitySourceStateHandler>(this);
        CoreServices.InputSystem?.UnregisterHandler<IMixedRealityHandJointHandler>(this);
    }

    // IMixedRealitySourceStateHandler interface
    public void OnSourceDetected(SourceStateEventData eventData)
    {
        var hand = eventData.Controller as IMixedRealityHand;

        // Only react to articulated hand input sources
        if (hand != null)
        {
            Debug.Log("Source detected: " + hand.ControllerHandedness);
        }
    }

    public void OnSourceLost(SourceStateEventData eventData)
    {
        var hand = eventData.Controller as IMixedRealityHand;

        // Only react to articulated hand input sources
        if (hand != null)
        {
            Debug.Log("Source lost: " + hand.ControllerHandedness);
        }
    }

    public void OnHandJointsUpdated(
                InputEventData<IDictionary<TrackedHandJoint, MixedRealityPose>> eventData)
    {
        MixedRealityPose palmPose;
        if (eventData.InputData.TryGetValue(TrackedHandJoint.Palm, out palmPose))
        {
            Debug.Log("Hand Joint Palm Updated: " + palmPose.Position);
        }
    }
}
```

## <a name="register-for-fallback-input-events"></a><span data-ttu-id="dcd04-176">Registrieren für Fallbackeingabeereignisse</span><span class="sxs-lookup"><span data-stu-id="dcd04-176">Register for fallback input events</span></span>

<span data-ttu-id="dcd04-177">Fallbackeingabehandler ähneln registrierten globalen Eingabehandlern, werden aber als letztes Mittel für die Behandlung von Eingabeereignis behandelt.</span><span class="sxs-lookup"><span data-stu-id="dcd04-177">Fallback input handlers are similar to registered global input handlers but are treated as a last resort for input event handling.</span></span> <span data-ttu-id="dcd04-178">Nur wenn keine globalen Eingabehandler gefunden wurden und sich keine GameObjects im Fokus befinden, werden Fallbackeingabehandler genutzt.</span><span class="sxs-lookup"><span data-stu-id="dcd04-178">Only if no global input handlers were found and no GameObjects are in focus will fallback input handlers be leveraged.</span></span>

### <a name="fallback-input-handler-example"></a><span data-ttu-id="dcd04-179">Beispiel für Fallbackeingabehandler</span><span class="sxs-lookup"><span data-stu-id="dcd04-179">Fallback input handler example</span></span>

```c#
public class GlobalHandListenerExample : MonoBehaviour,
    IMixedRealitySourceStateHandler // Handle source detected and lost
{
    private void OnEnable()
    {
        CoreServices.InputSystem?.PushFallbackInputHandler(this);
    }

    private void OnDisable()
    {
        CoreServices.InputSystem?.PopFallbackInputHandler();
    }

    // IMixedRealitySourceStateHandler interface
    public void OnSourceDetected(SourceStateEventData eventData)
    {
        ...
    }

    public void OnSourceLost(SourceStateEventData eventData)
    {
        ...
    }
}
```

## <a name="how-to-stop-input-events"></a><span data-ttu-id="dcd04-180">Beenden von Eingabeereignissen</span><span class="sxs-lookup"><span data-stu-id="dcd04-180">How to stop input events</span></span>

<span data-ttu-id="dcd04-181">Jede Eingabeereignisschnittstelle stellt ein [`BaseInputEventData`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputEventData) Datenobjekt als Parameter für jede Funktion auf der Schnittstelle bereit.</span><span class="sxs-lookup"><span data-stu-id="dcd04-181">Every input event interface provides a [`BaseInputEventData`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputEventData) data object as a parameter to each function on the interface.</span></span> <span data-ttu-id="dcd04-182">Dieses Ereignisdatenobjekt erweitert von Unitys [`AbstractEventData`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.html) eigenem .</span><span class="sxs-lookup"><span data-stu-id="dcd04-182">This event data object extends from Unity's own [`AbstractEventData`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.html).</span></span>

<span data-ttu-id="dcd04-183">Um zu verhindern, dass ein Eingabeereignis wie beschrieben durch seine Ausführung weiterverteilt [wird,](#input-events-in-action)kann eine Komponente aufrufen, um das Ereignis [`AbstractEventData.Use()`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.Use.html) als verwendet zu markieren.</span><span class="sxs-lookup"><span data-stu-id="dcd04-183">In order to stop an input event from propagating through its execution [as outlined](#input-events-in-action), a component can call [`AbstractEventData.Use()`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.Use.html) to mark the event as used.</span></span> <span data-ttu-id="dcd04-184">Dadurch wird der Empfang des aktuellen Eingabeereigniss durch andere GameObjects mit Ausnahme von globalen Eingabehandlern nicht mehr empfangen.</span><span class="sxs-lookup"><span data-stu-id="dcd04-184">This will stop any other GameObjects from receiving the current input event, with the exception of global input handlers.</span></span>

> [!NOTE]
> <span data-ttu-id="dcd04-185">Eine Komponente, die die `Use()` -Methode aufruft, stoppt den Empfang anderer GameObjects.</span><span class="sxs-lookup"><span data-stu-id="dcd04-185">A component that calls the `Use()` method will stop other GameObjects from receiving it.</span></span> <span data-ttu-id="dcd04-186">Andere Komponenten im aktuellen GameObject empfangen jedoch weiterhin das Eingabeereignis und geben alle zugehörigen Schnittstellenfunktionen aus.</span><span class="sxs-lookup"><span data-stu-id="dcd04-186">However, other components on the current GameObject will still receive the input event and fire any related interface functions.</span></span>

## <a name="see-also"></a><span data-ttu-id="dcd04-187">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="dcd04-187">See also</span></span>

- [<span data-ttu-id="dcd04-188">Zeiger</span><span class="sxs-lookup"><span data-stu-id="dcd04-188">Pointers</span></span>](pointers.md)
- [<span data-ttu-id="dcd04-189">Speech</span><span class="sxs-lookup"><span data-stu-id="dcd04-189">Speech</span></span>](speech.md)
- [<span data-ttu-id="dcd04-190">Eingabezustand</span><span class="sxs-lookup"><span data-stu-id="dcd04-190">Input State</span></span>](input-state.md)
