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
# <a name="input-events"></a>Eingabeereignisse

In der folgenden Liste sind alle verfügbaren Eingabeereignisschnittstellen aufgeführt, die von einer benutzerdefinierten MonoBehaviour-Komponente implementiert werden sollen. Diese Schnittstellen werden vom MRTK-Eingabesystem aufgerufen, um benutzerdefinierte App-Logik basierend auf Benutzereingabeinteraktionen zu verarbeiten. [Zeigereingabeereignisse werden](pointers.md#pointer-event-interfaces) etwas anders behandelt als die unten angegebenen Standardeingabeereignistypen.

> [!IMPORTANT]
> Standardmäßig erhält ein Skript nur Dann Eingabeereignisse, wenn es sich um das GameObject im Fokus eines Zeigers oder übergeordneten Elements eines GameObject im Fokus handelt.

| Handler | Events | BESCHREIBUNG |
| --- | :---: | --- |
| [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | Quelle erkannt/verloren | Wird ausgelöst, wenn eine Eingabequelle erkannt wird oder verloren geht, z. B. wenn eine artikulierte Hand erkannt wird oder verloren geht. |
| [`IMixedRealitySourcePoseHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourcePoseHandler) | Quellpose geändert | Wird bei Änderungen der Quellpose ausgelöst. Die Quellpose stellt die allgemeine Pose der Eingabequelle dar. Bestimmte Posen wie Greif- oder Zeigerpose in einem sechs DOF-Controller können über ermittelt `IMixedRealityInputHandler<MixedRealityPose>` werden. |
| [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | Eingabe nach unten/nach oben | Wird bei Änderungen an binären Eingaben wie Schaltflächen ausgelöst. |
| [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Eingabe geändert | Wird bei Änderungen an Eingaben des angegebenen Typs ausgelöst. **T** kann die folgenden Werte verwenden: <br/> - *float* (z. B. gibt einen analogen Trigger zurück)<br/> - *Vector2* (gibt z.B. die Gamepad-Thumbstickrichtung zurück) <br/> - *Vector3* (z.B. Rückgabeposition des nachverfolgten Geräts) <br/> - *Quaternion* (gibt z. B. die Ausrichtung des nachverfolgten Geräts zurück)<br/> - [MixedRealityPose](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) (z. B. gibt das vollständig nachverfolgte Gerät zurück) |
| [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) | Speech-Schlüsselwort erkannt | Wird bei der Erkennung eines der Schlüsselwörter ausgelöst, die im *Speech-Befehlsprofil konfiguriert sind.* |
| [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) | Diktieren<br/> Hypothesis <br/> Ergebnis <br/> Abgeschlossen <br/> Fehler | Wird von Diktatsystemen ausgelöst, um die Ergebnisse einer Diktatsitzung zu melden. |
| [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) | Gestenereignisse für: <br/> Gestartet <br/> Aktualisiert <br/> Abgeschlossen <br/> Canceled | Wird bei der Gestenerkennung ausgelöst. |
| [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | Geste aktualisiert/abgeschlossen | Wird bei erkennung von Gesten ausgelöst, die zusätzliche Daten des angegebenen Typs enthalten. Weitere [**Informationen zu möglichen**](gestures.md#gesture-events) Werten für T finden Sie unter Gestenereignisse.  |
| [`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) | Handgelenke aktualisiert | Wird von artikulierten Handcontrollern ausgelöst, wenn Handgelenke aktualisiert werden. |
| [`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) | Hand Mesh aktualisiert | Wird von artikulierten Handcontrollern ausgelöst, wenn ein Handgitternetz aktualisiert wird. |
| [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) | Aktion gestartet/beendet | Wird zum Angeben des Aktionsstarts und -endes für Eingaben, die Aktionen zugeordnet sind, aus. |

## <a name="input-events-in-action"></a>Eingabeereignisse in Aktion

Auf Skriptebene können Eingabeereignisse verwendet werden, indem eine der in der obigen Tabelle gezeigten Ereignishandlerschnittstellen implementiert wird. Wenn ein Eingabeereignis über eine Benutzerinteraktion erfolgt, findet Folgendes statt:

1. Das MRTK-Eingabesystem erkennt, dass ein Eingabeereignis aufgetreten ist.
1. Das MRTK-Eingabesystem gibt die relevante Schnittstellenfunktion des Eingabeereigniss für alle registrierten [globalen Eingabehandler aus.](#register-for-global-input-events)
1. Für jeden aktiven Zeiger, der beim Eingabesystem registriert ist:
    1. Das Eingabesystem bestimmt, welches GameObject sich im Fokus für den aktuellen Zeiger befindet.
    1. Das Eingabesystem verwendet [das Unity-Ereignissystem,](https://docs.unity3d.com/Manual/EventSystem.html) um die relevante Schnittstellenfunktion für alle übereinstimmenden Komponenten auf dem fokussierten GameObject zu verwenden.
    1. Wenn zu einem beliebigen Zeitpunkt ein Eingabeereignis als verwendet markiert [wurde,](#how-to-stop-input-events)wird der Prozess beendet, und keine weiteren GameObjects erhalten Rückrufe.
        - Beispiel: Komponenten, die die Schnittstelle implementieren, werden [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) gesucht, wenn ein Sprachbefehl erkannt wird.
        - Hinweis: Das Unity-Ereignissystem blasen hoch, um das übergeordnete GameObject zu durchsuchen, wenn im aktuellen GameObject keine Komponenten gefunden werden, die mit der gewünschten Schnittstelle übereinstimmen.
1. Wenn keine globalen Eingabehandler registriert sind und kein GameObject mit einer übereinstimmenden Komponente/Schnittstelle gefunden wird, wird vom Eingabesystem jeder fallback registrierte Eingabehandler aufgerufen.

> [!NOTE]
> [Zeigereingabeereignisse werden](pointers.md#pointer-event-interfaces) auf eine etwas andere Weise als die oben aufgeführten Eingabeereignisschnittstellen behandelt. Insbesondere werden Zeigereingabeereignisse nur vom GameObject im Fokus durch den Zeiger, der das Eingabeereignis ausgelöst hat, sowie alle globalen Eingabehandler behandelt. Reguläre Eingabeereignisse werden von GameObjects im Fokus für alle aktiven Zeiger behandelt.

### <a name="input-event-interface-example"></a>Beispiel für eine Eingabeereignisschnittstelle

Der folgende Code veranschaulicht die Verwendung der [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) -Schnittstelle. Wenn der Benutzer die Wörter "kleiner" oder "größer" sagt, während er sich auf ein GameObject mit dieser Klasse konzentriert, skaliert sich das GameObject um die Hälfte oder `ShowHideSpeechHandler` das Doppelte.

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
> [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler)Eingabeereignisse erfordern, dass die gewünschten Schlüsselwörter vorab im [MRTK Speech Commands Profile registriert sind.](speech.md)

## <a name="register-for-global-input-events"></a>Registrieren für globale Eingabeereignisse

Eine Komponente muss sich beim Eingabesystem registrieren, um eine Komponente zu erstellen, die auf globale Eingabeereignisse lausiert, ohne zu ignorieren, welches GameObject sich möglicherweise im Fokus hat. Nach der Registrierung empfangen alle Instanzen dieses MonoBehaviour-Objekts Eingabeereignisse zusammen mit allen GameObjects, die sich derzeit im Fokus befindet, und anderen globalen registrierten Listenern.

Wenn ein Eingabeereignis als verwendet [markiert wurde,](#how-to-stop-input-events)empfangen globale registrierte Handler weiterhin Rückrufe. Das Ereignis wird jedoch nicht von GameObjects mit Fokus empfangen.

### <a name="global-input-registration-example"></a>Beispiel für eine globale Eingaberegistrierung

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

## <a name="register-for-fallback-input-events"></a>Registrieren für Fallbackeingabeereignisse

Fallbackeingabehandler ähneln registrierten globalen Eingabehandlern, werden aber als letztes Mittel für die Behandlung von Eingabeereignis behandelt. Nur wenn keine globalen Eingabehandler gefunden wurden und sich keine GameObjects im Fokus befinden, werden Fallbackeingabehandler genutzt.

### <a name="fallback-input-handler-example"></a>Beispiel für Fallbackeingabehandler

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

## <a name="how-to-stop-input-events"></a>Beenden von Eingabeereignissen

Jede Eingabeereignisschnittstelle stellt ein [`BaseInputEventData`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputEventData) Datenobjekt als Parameter für jede Funktion auf der Schnittstelle bereit. Dieses Ereignisdatenobjekt erweitert von Unitys [`AbstractEventData`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.html) eigenem .

Um zu verhindern, dass ein Eingabeereignis wie beschrieben durch seine Ausführung weiterverteilt [wird,](#input-events-in-action)kann eine Komponente aufrufen, um das Ereignis [`AbstractEventData.Use()`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.Use.html) als verwendet zu markieren. Dadurch wird der Empfang des aktuellen Eingabeereigniss durch andere GameObjects mit Ausnahme von globalen Eingabehandlern nicht mehr empfangen.

> [!NOTE]
> Eine Komponente, die die `Use()` -Methode aufruft, stoppt den Empfang anderer GameObjects. Andere Komponenten im aktuellen GameObject empfangen jedoch weiterhin das Eingabeereignis und geben alle zugehörigen Schnittstellenfunktionen aus.

## <a name="see-also"></a>Siehe auch

- [Zeiger](pointers.md)
- [Speech](speech.md)
- [Eingabezustand](input-state.md)
