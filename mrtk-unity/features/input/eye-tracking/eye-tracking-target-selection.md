---
title: EyeTracking-Zielauswahl
description: Zugreifen auf Anvitätsdaten mit den Augen und bestimmte Ereignisse beim Anvingen mit den Augen zum Auswählen von Zielen im MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, EyeTracking,
ms.openlocfilehash: aab2f35259db183f4f3edb4fffc2b3e7a066bccf9c69e492c90ee193388b8b7a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189600"
---
# <a name="eye-supported-target-selection"></a>Durch die Augen unterstützte Zielauswahl

![MRTK](../../images/eye-tracking/mrtk_et_targetselect.png)

Auf dieser Seite werden verschiedene Optionen für den Zugriff auf Daten zum Anvieren mit den Augen und bestimmte Ereignisse für das Anvieren mit den Augen erläutert, um Ziele im MRTK auszuwählen. Eyetracking ermöglicht eine schnelle und mühelose Zielauswahl mithilfe einer Kombination von Informationen darüber, was ein Benutzer betrachtet, mit zusätzlichen Eingaben wie _Handtracking_ und _Sprachbefehlen:_

- Suchen & _Z.B. "Auswählen"_ (Standardstimmenbefehl)
- Suchen & _"Explode"_ oder _"Pop"_ (benutzerdefinierte Sprachbefehle)
- Schaltfläche "& Bluetooth suchen"
- Suchen & Zusammendnüpfen (d. h. halten Sie die Hand vor Ihnen, und bringen Sie Ihren Daumen und Zeigefinger zusammen)
  - Beachten Sie, dass die Handlichtlichter deaktiviert werden müssen, damit [dies funktioniert.](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray)

Es gibt mehrere Optionen, um holografische Inhalte mit dem Anvitäts-Blick auf die Augen auszuwählen:

[**1. Verwenden Sie den primären Fokuszeiger:**](#1-use-generic-focus-and-pointer-handlers)

Dies kann als priorisierter Cursor verstanden werden.
Wenn die Hände angezeigt werden, wäre dies standardmäßig Handlichtlichter.
Wenn keine Hände angezeigt werden, ist der priorisierte Zeiger das Anvisieren mit dem Kopf oder den Augen.
Beachten Sie daher, dass basierend auf dem aktuellen Design das Anvieren mit dem Kopf oder mit den Augen als Cursoreingabe unterdrückt wird, wenn Handlichtlichter verwendet werden.

Beispiel:

Ein Benutzer möchte eine entfernte holografische Schaltfläche auswählen.
Als Entwickler möchten Sie eine flexible Lösung bereitstellen, die es dem Benutzer ermöglicht, diese Aufgaben unter verschiedenen Bedingungen auszuführen:

- Gehen Sie zur Schaltfläche, und klicken Sie darauf.
- Betrachten Sie es aus der Entfernung, und sagen Sie "auswählen".
- Anheften der Schaltfläche mithilfe eines Handstrahls und Durchführen einer Taste In diesem Fall ist die flexibelste Lösung die Verwendung des primären Fokushandlers, da er Sie benachrichtigt, wenn der aktuell priorisierte primäre Fokuszeiger ein Ereignis auslöst. Beachten Sie, dass der Fokuszeiger für das Anvieren mit dem Kopf oder den Augen deaktiviert ist, sobald die Hände sichtbar sind, wenn die Handlichtlichter aktiviert sind.

> [!IMPORTANT]
> Beachten Sie, dass der Fokuszeiger für das Anvieren mit dem Kopf oder den Augen deaktiviert ist, sobald die Hände sichtbar sind, wenn die Handlichtlichter aktiviert sind. Wenn Sie eine "Look and Pinch"-Interaktion unterstützen möchten, müssen Sie [  den Handstrahl deaktivieren.](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray) In unseren Eyetracking-Beispielszenen haben wir den Handstrahl deaktiviert, um mithilfe von Augen und Handbewegungen vielfältigere Interaktionen zu ermöglichen . Weitere Informationen finden Sie beispielsweise unter [Eye-Supported Positioning](eye-tracking-eyes-and-hands.md)(Augengestützte Positionierung).

[**2. Verwenden Sie sowohl den Augenfokus als auch den Handlichtstrahl gleichzeitig:**](#2-independent-eye-gaze-specific-eyetrackingtarget)

Es kann Fälle geben, in denen Sie spezifischer sein möchten, welche Art von Fokuszeigatoren bestimmte Ereignisse auslösen und gleichzeitig die Verwendung mehrerer Verfahren für die Ferninteraktion zulassen kann.

Beispiel: In Ihrer App kann ein Benutzer fernen Handlichtstrahl verwenden, um holografisches technisches Setup zu bearbeiten, z. B. einige entfernte holografische Engine-Teile zu greifen und zu halten und an Ort und Stelle zu halten. Dabei muss der Benutzer eine Reihe von Anweisungen durchgehen und seinen Fortschritt aufzeichnen, indem er einige Kontrollkästchen deaktiviert. Wenn der Benutzer nicht ausgelastet _ist,_ wäre es instinktiv, einfach das Kontrollkästchen zu berühren oder es mithilfe eines Handstrahls auszuwählen. Wenn der Benutzer jedoch seine Hände ausgelastet hat, wie in unserem Fall bei einigen holografischen Engine-Teilen, möchten Sie es dem Benutzer ermöglichen, die Anweisungen mit dem Anvogramm mit den Augen nahtlos zu scrollen und einfach ein Kontrollkästchen zu betrachten und zu sagen: "Check it!".

Um dies zu ermöglichen, müssen Sie ein eyespezifisches EyeTrackingTarget-Skript verwenden, das unabhängig von den KERN-MRTK FocusHandlers ist und weiter unten erläutert wird.

## <a name="1-use-generic-focus-and-pointer-handlers"></a>1. Verwenden von generischen Fokus- und Zeigerhandlern

Wenn die Eyetracking ordnungsgemäß eingerichtet ist (siehe Grundlegende [MRTK-Einrichtung](eye-tracking-basic-setup.md)zur Verwendung der Blickverfolgung), ist die Auswahl von Hologrammen mit ihren Augen für Benutzer identisch mit jeder anderen Fokuseingabe (z. B. Anvieren mit dem Kopf oder Handstrahl). Dies bietet den großen Vorteil einer flexiblen Möglichkeit, mit Ihren Hologrammen zu interagieren, indem der Hauptfokustyp in Ihrem MRTK-Eingabezeigerprofil abhängig von den Anforderungen Ihres Benutzers definiert wird, während der Code unverändert bleibt. Dies ermöglicht das Wechseln zwischen dem Anvieren mit dem Kopf oder den Augen, ohne eine Codezeile zu ändern oder Handlichtlichter durch Das Ziel der Augen für ferne Interaktionen zu ersetzen.

### <a name="focusing-on-a-hologram"></a>Konzentrieren auf ein Hologramm

Verwenden Sie die _Schnittstelle "IMixedRealityFocusHandler",_ die Ihnen zwei Schnittstellenmitglieder zur Verfügung stellt, um zu erkennen, wann ein Hologramm den Fokus hat: _OnFocusEnter_ und _OnFocusExit_.

Hier sehen Sie ein einfaches Beispiel aus [ColorTap.cs,](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ColorTap) um die Farbe eines Hologramms zu ändern, wenn sie sich anschaut.

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler
{
    void IMixedRealityFocusHandler.OnFocusEnter(FocusEventData eventData)
    {
        material.color = color_OnHover;
    }

    void IMixedRealityFocusHandler.OnFocusExit(FocusEventData eventData)
    {
        material.color = color_IdleState;
    }
    ...
}
```

### <a name="selecting-a-focused-hologram"></a>Auswählen eines fokussierten Hologramms

Um ein fokussiertes Hologramm auszuwählen, verwenden Sie _PointerHandler,_ um auf Eingabeereignisse zu lauschen, um eine Auswahl zu bestätigen.
Wenn Sie beispielsweise den _IMixedRealityPointerHandler_ hinzufügen, reagieren sie auf einfache Zeigereingaben.
Die _IMixedRealityPointerHandler-Schnittstelle_ erfordert die Implementierung der folgenden drei Schnittstellenmitglieder: _OnPointerUp,_ _OnPointerDown_ und _OnPointerClicked_.

Im folgenden Beispiel ändern wir die Farbe eines Hologramms, indem wir es ansehen und "Auswählen" anheften oder sagen.
Die erforderliche Aktion zum Auslösen des Ereignisses wird definiert, indem wir den Typ von im Unity-Editor festlegen können. Standardmäßig handelt es sich um die `eventData.MixedRealityInputAction == selectAction` `selectAction` Aktion "Auswählen". Die Typen der verfügbaren [MixedRealityInputActions können](../input-actions.md) im MRTK-Profil über Eingabeaktionen des _MRTK-Konfigurationsprofils_  ->    ->  _konfiguriert werden._

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler, IMixedRealityPointerHandler
{
    // Allow for editing the type of select action in the Unity Editor.
    [SerializeField]
    private MixedRealityInputAction selectAction = MixedRealityInputAction.None;
    ...

    void IMixedRealityPointerHandler.OnPointerUp(MixedRealityPointerEventData eventData)
    {
        if (eventData.MixedRealityInputAction == selectAction)
        {
            material.color = color_OnHover;
        }
    }

    void IMixedRealityPointerHandler.OnPointerDown(MixedRealityPointerEventData eventData)
    {
        if (eventData.MixedRealityInputAction == selectAction)
        {
            material.color = color_OnSelect;
        }
    }

    void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData) { }
}
```

### <a name="eye-gaze-specific-baseeyefocushandler"></a>BaseEyeFocusHandler-Spezifisches Anvieren mit den Augen

Da sich das Anvingen mit den Augen stark von anderen Zeigereingaben unterscheiden kann, sollten Sie sicherstellen, dass Sie nur auf die Fokuseingabe reagieren, wenn es sich um ein Anving mit den Augen handelt und es sich derzeit um den primären Eingabezeiger handelt. 
Zu diesem Zweck verwenden Sie die , die für eye tracking spezifisch ist und von [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) der ableitung. [`BaseFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseFocusHandler)
Wie bereits erwähnt, wird sie nur ausgelöst, wenn das Anvanving mit den Augen derzeit die primäre Zeigereingabe ist (d. h., es ist kein Handstrahl aktiv). Weitere Informationen finden Sie unter [How to support eye gaze + hand gestures](eye-tracking-eyes-and-hands.md).

Hier ist ein Beispiel aus `EyeTrackingDemo-03-Navigation` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes).
In dieser Demo gibt es zwei 3D-Hologramme, die sich abhängig davon drehen, welcher Teil des Objekts betrachtet wird: Wenn der Benutzer auf die linke Seite des Hologramms blickt, wird dieser Teil langsam an die Vorderseite des Benutzers gerichtet.
Wenn die rechte Seite angezeigt wird, wird dieser Teil langsam an den Anfang bewegt.
Dies ist ein Verhalten, das Sie möglicherweise nicht immer aktiv haben möchten, und auch etwas, das Sie möglicherweise nicht versehentlich durch einen Handstrahl oder einen Blick auf den Kopf auslösen möchten.
Wenn das [`OnLookAtRotateByEyeGaze`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) angefügt ist, rotiert ein GameObject, während es sich anschaut.

```c#
public class OnLookAtRotateByEyeGaze : BaseEyeFocusHandler
{
    ...

    protected override void OnEyeFocusStay()
    {
        // Update target rotation
        RotateHitTarget();
    }

    ...

    ///
    /// This function computes the rotation of the target to move the currently
    /// looked at aspect slowly to the front.
    ///
    private void RotateHitTarget()
    {
        // Example for querying the hit position of the eye gaze ray using EyeGazeProvider
        Vector3 TargetToHit = (this.gameObject.transform.position - InputSystem.EyeGazeProvider.HitPosition).normalized;

        ...
    }
}
```

Eine vollständige Liste der verfügbaren Ereignisse von finden Sie in der [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) API-Dokumentation:

- **OnEyeFocusStart:** Wird ausgelöst, sobald der Blickstrahl *beginnt,* sich mit dem Collider dieses Ziels zu überschneiden.
- **OnEyeFocusStay:** Wird *ausgelöst,* während sich der Blickstrahl mit dem Collider dieses Ziels überschneidet.
- **OnEyeFocusStop:** Wird ausgelöst, sobald sich der Blickstrahl *nicht* mehr mit dem Collider dieses Ziels überschneidet.
- **OnEyeFocusDwell:** Wird ausgelöst, nachdem sich der Blickstrahl für einen bestimmten Zeitraum mit dem Collider dieses Ziels überschneidet hat.

## <a name="2-independent-eye-gaze-specific-eyetrackingtarget"></a>2. Unabhängige eye-gaze-spezifische EyeTrackingTarget-Methode

Schließlich stellen wir Ihnen eine Lösung zur Verfügung, mit der Sie die augenbasierte Eingabe über das Skript vollständig unabhängig von anderen Fokuszeige behandeln [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) können.

Dies hat drei _Vorteile:_

- Sie können sicherstellen, dass das Hologramm nur auf das Anvieren mit den Augen des Benutzers reagiert.
- Dies ist unabhängig von der derzeit aktiven primären Eingabe. Daher können Sie mehrere Eingaben gleichzeitig verarbeiten, z. B. indem Sie schnelles Eye-Targeting mit Handgesten kombinieren.
- Es wurden bereits mehrere Unity-Ereignisse eingerichtet, um das Behandeln und Wiederverwenden vorhandener Verhaltensweisen innerhalb des Unity-Editors oder über Code zu ermöglichen.

Es gibt auch _einige Nachteile:_

- Mehr Aufwand für die individuelle Handhabung separater Eingaben.
- Keine eleganten Beeinträchtigungen: Sie unterstützt nur das Ziel der Augen. Wenn eye tracking nicht funktioniert, ist ein zusätzlicher Fallback erforderlich.

Ähnlich wie _baseFocusHandler_ ist _das EyeTrackingTarget-Objekt_ mit mehreren Unity-Ereignissen bereit, die anvisiert werden und auf die Sie bequem entweder über den Unity-Editor (siehe Beispiel unten) oder mit _AddListener()_ im Code lauschen können:

- OnLookAtStart()
- WhileLookingAtTarget()
- OnLookAway()
- OnDwell()
- OnSelected()

Im Folgenden werden einige Beispiele für die Verwendung von _EyeTrackingTarget erläutert._

### <a name="example-1-eye-supported-smart-notifications"></a>Beispiel #1: Von den Augen unterstützte intelligente Benachrichtigungen

In `EyeTrackingDemo-02-TargetSelection` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes) finden Sie ein Beispiel für _"intelligente_ Benachrichtigungen", die auf das Anvieren mit den Augen reagieren.
Hierbei handelt es sich um 3D-Textfelder, die in der Szene platziert werden können und sich reibungslos vergrößern und sich dem Benutzer wenden, wenn er sich anschaut, um die Lesbarkeit zu erleichtern. Während der Benutzer die Benachrichtigung liest, werden die Informationen immer wieder klar und klar angezeigt. Nachdem sie gelesen und die Benachrichtigung entfernt wurde, wird die Benachrichtigung automatisch verworfen und ausgeblendet. Um all dies zu erreichen, gibt es einige generische Verhaltensskripts, die überhaupt nicht spezifisch für eye tracking sind, z. B.:

- [`FaceUser`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FaceUser)
- [`ChangeSize`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ChangeSize)
- [`BlendOut`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.BlendOut)

Der Vorteil dieses Ansatzes ist, dass dieselben Skripts von verschiedenen Ereignissen wiederverwendet werden können. Beispielsweise kann ein Hologramm dem Benutzer auf der Grundlage von Sprachbefehlen oder nach dem Drücken einer virtuellen Schaltfläche zur Seite stehen. Um diese Ereignisse auszulösen, können Sie einfach auf die Methoden verweisen, die in dem Skript ausgeführt werden sollen, [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) das an Ihr GameObject angefügt ist.

Im Beispiel für "Intelligente _Benachrichtigungen zu Benachrichtigungen für_ Benachrichtigungen" geschieht Folgendes:

- **OnLookAtStart():** Die Benachrichtigung beginnt mit...
  - *FaceUser.Engage:* ... auf den Benutzer zu.
  - *ChangeSize.Engage:* ... vergrößeren _(bis zu einer angegebenen maximalen Skalierung)_.
  - *BlendOut.Engage:* ... beginnt, mehr zu mischen (nachdem er sich in einem _feineren Leerlaufzustand befindet)._  

- **OnDwell():** Informiert das _BlendOut-Skript_ darüber, dass die Benachrichtigung ausreichend untersucht wurde.

- **OnLookAway():** Die Benachrichtigung beginnt mit...
  - *FaceUser.Disengage:* ... zur ursprünglichen Ausrichtung zurückwechseln.
  - *ChangeSize.Disengage:* ... auf die ursprüngliche Größe zurück verringern.
  - *BlendOut.Disengage:* ... beginnt zu mischen: Wenn _OnDwell()_ ausgelöst wurde, blenden Sie vollständig aus und zerstören sie, andernfalls wieder in den Leerlaufzustand.

**Entwurfserwägung:** Der Schlüssel zu einer freundlicheren Erfahrung besteht hier in der sorgfältigen Feinabstimmung der Geschwindigkeit eines dieser Verhaltensweisen, um zu vermeiden, dass es zu Unannehmlichkeiten kommt, indem sie immer zu schnell auf das Anvieren des Benutzers reagieren.
Andernfalls kann dies schnell sehr überfordernd sein.

<img src="../../images/eye-tracking/mrtk_et_EyeTrackingTarget_Notification.jpg" width="750" alt="Target Notification">

### <a name="example-2-holographic-gem-rotates-slowly-when-looking-at-it"></a>Beispiel #2: Holographic gem rotates slowly when looking it

Ähnlich wie bei Beispiel #1 können wir problemlos ein Hoverfeedback für unsere holografischen Gems in der Szene (Assets/MRTK/Examples/Demos/EyeTracking/Scenes) erstellen, die sich langsam in konstanter Richtung und mit konstanter Geschwindigkeit (im Gegensatz zum oben gezeigten Drehungsbeispiel) drehen wird, wenn wir uns `EyeTrackingDemo-02-TargetSelection` betrachten. Sie müssen nur die Drehung des holografischen Gems aus dem _WhileLookingAtTarget()-Ereignis_ von _EyeTrackingTarget_ auslösen. Im Anschluss finden Sie einige weitere Details:

1. Erstellen Sie ein generisches Skript, das eine öffentliche Funktion enthält, um das GameObject zu drehen, an das es angefügt ist. Im Folgenden finden Sie ein Beispiel aus _RotateWithConstSpeedDir.cs,_ in dem wir die Drehrichtung und Geschwindigkeit aus dem Unity-Editor optimieren können.

    ```c#
    using UnityEngine;

    namespace Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking
    {
        /// <summary>
        /// The associated GameObject will rotate when RotateTarget() is called based on a given direction and speed.
        /// </summary>
        public class RotateWithConstSpeedDir : MonoBehaviour
        {
            [Tooltip("Euler angles by which the object should be rotated by.")]
            [SerializeField]
            private Vector3 RotateByEulerAngles = Vector3.zero;

            [Tooltip("Rotation speed factor.")]
            [SerializeField]
            private float speed = 1f;

            /// <summary>
            /// Rotate game object based on specified rotation speed and Euler angles.
            /// </summary>
            public void RotateTarget()
            {
                transform.eulerAngles = transform.eulerAngles + RotateByEulerAngles * speed;
            }
        }
    }
    ```

1. Fügen Sie das Skript ihrem Ziel-GameObject hinzu, und verweisen Sie im UnityEvent-Trigger auf die [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) _RotateTarget()-Funktion,_ wie im folgenden Screenshot gezeigt:

    ![EyeTrackingTarget-Beispiel](../../images/eye-tracking/mrtk_et_EyeTrackingTargetSample.jpg)

### <a name="example-3-pop-those-gems-aka-_multi-modal-eye-gaze-supported-target-selection_"></a>Beispiel #3: Diese Gems werden per Pop aus der Zielauswahl bzw. durch das _multi-modale_ Anvingen mit den Augen unterstützt.

Im vorherigen Beispiel haben wir gezeigt, wie einfach es ist, zu erkennen, ob ein Ziel angezeigt wird und wie eine Reaktion darauf ausgelöst werden kann. Als Nächstes lassen Sie die Gems mithilfe des _OnSelected()-Ereignisses_ aus explodieren. [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) Der interessante Teil *ist, wie* die Auswahl ausgelöst wird. Ermöglicht [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) das schnelle Zuweisen verschiedener Methoden zum Aufrufen einer Auswahl:

- _Geste zum Anheften:_ Wenn Sie "Aktion auswählen" auf "Auswählen" festlegen, wird die Auswahl mit der Standardhandgeste ausgelöst.
Dies bedeutet, dass der Benutzer einfach seine Hand erhöhen und den Daumen und den Zeigefinger zusammendrippen kann, um die Auswahl zu bestätigen.

- Sagen _Sie "Auswählen":_ Verwenden Sie den Standardstimmenbefehl _"Auswählen",_ um ein Hologramm auszuwählen.

- Sagen _Sie "Explode"_ oder _"Pop":_ Um benutzerdefinierte Sprachbefehle zu verwenden, müssen Sie zwei Schritte ausführen:
    1. Einrichten einer benutzerdefinierten Aktion wie _"DestroyTarget"_
        - Navigieren Sie zu _MRTK -> Input -> Input Actions_
        - Klicken Sie auf "Neue Aktion hinzufügen".

    2. Richten Sie die Sprachbefehle ein, die diese Aktion auslösen, z. _B. "Explode"_ oder _"Pop"._
        - Navigieren Sie _zu MRTK -> Input -> Speech._
        - Klicken Sie auf "Neuen Sprachbefehl hinzufügen".
            - Zuordnen der aktion, die Sie gerade erstellt haben
            - Weisen Sie einen _KeyCode zu,_ um das Auslösen der Aktion über einen Schaltflächendruck zu ermöglichen.

![Beispiel für Sprachbefehle eyeTrackingTarget](../../images/eye-tracking/mrtk_et_voicecmdsample.jpg)

Wenn ein Gem ausgewählt wird, wird es explodiert, wodurch ein Sound angezeigt wird und nicht mehr angezeigt wird. Dies wird vom Skript [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) behandelt. Sie haben zwei Möglichkeiten:

- **Im Unity-Editor:** Sie können einfach das Skript, das an jede unserer Gem-Vorlagen angefügt ist, mit dem Unity-Ereignis OnSelected() im Unity-Editor verknüpfen.
- **In code:** If you don't want to drag and drop GameObjects around, you can also simply add a event listener directly to your script.  
Hier sehen Sie ein Beispiel aus der Ausführung im [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) Skript:

```c#
/// <summary>
/// Destroys the game object when selected and optionally plays a sound or animation when destroyed.
/// </summary>
[RequireComponent(typeof(EyeTrackingTarget))] // This helps to ensure that the EyeTrackingTarget is attached
public class HitBehaviorDestroyOnSelect : MonoBehaviour
{
    ...
    private EyeTrackingTarget myEyeTrackingTarget = null;

    private void Start()
    {
        myEyeTrackingTarget = this.GetComponent<EyeTrackingTarget>();

        if (myEyeTrackingTarget != null)
        {
            myEyeTrackingTarget.OnSelected.AddListener(TargetSelected);
        }
    }

    ...

    ///
    /// This is called once the EyeTrackingTarget detected a selection.
    ///
    public void TargetSelected()
    {
        // Play some animation
        // Play some audio effect
        // Handle destroying the target appropriately
    }
}
```

### <a name="example-4-use-hand-rays-and-eye-gaze-input-together"></a>Beispiel #4: Gemeinsames Verwenden von Handlichtlichtern und Blickeingaben

Handlichtlichter haben Vorrang vor dem Ziel des Anvisiertns mit dem Kopf und den Augen. Dies bedeutet, dass der Handstrahl als primärer Zeiger verwendet wird, wenn Handlichtlichter aktiviert sind, sobald die Hände angezeigt werden.
Es kann jedoch Situationen geben, in denen Sie Handlichtlichter verwenden möchten, während Sie dennoch erkennen, ob ein Benutzer ein bestimmtes Hologramm betrachtet. Kein Problem! Im Wesentlichen sind zwei Schritte erforderlich:

**1. Aktivieren des Handstrahls:** Um den Handstrahl zu aktivieren, wechseln Sie zu _Mixed Reality Toolkit -> Input -> Pointers_.
In _der EyeTrackingDemo-00-RootScene,_ in der das Mixed Reality Toolkit einmal für alle Eyetracking-Demoszenen konfiguriert ist, sollte _eyeTrackingDemoPointerProfile_ zu sehen sein.
Sie können entweder ein neues _Eingabeprofil_ von Grund auf neu erstellen oder das aktuelle Eyetracking-Profil anpassen:

- **Von Grund auf neu:** Wählen Sie _auf der Registerkarte_ Zeiger im Kontextmenü _defaultMixedRealityInputPointerProfile_ aus.
Dies ist das Standardzeigerprofil, für das der Handstrahl bereits aktiviert ist.
Um den Standardcursor (einen nicht transparenten weißen Punkt) zu ändern, klonen Sie einfach das Profil, und erstellen Sie Ein eigenes benutzerdefiniertes Zeigerprofil.
Ersetzen Sie _dann DefaultCursor durch_ _EyeCursor unter_ Gaze Cursor _Prefab_.  
- **Basierend auf dem vorhandenen _EyeTrackingDemoPointerProfile:_ Doppelklicken** Sie auf _das EyeTrackingDemoPointerProfile,_ und fügen Sie unter Zeigeroptionen den folgenden _Eintrag hinzu:_
  - **Controllertyp:** "Artikulierte Hand", "Windows Mixed Reality"
  - **Übergabe:** jegliche
  - **Zeiger-Prefab:** DefaultControllerPointer

**2. Erkennen, dass** ein Hologramm angezeigt wird: Verwenden Sie das Skript, um die Erkennung zu ermöglichen, dass ein Hologramm wie oben [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) beschrieben angezeigt wird. Sie können sich auch das Beispielskript zur Inspiration anschauen, da dies ein Hologramm zeigt, das auf das Anvieren mit den Augen folgt (z. B. ein Cursor), unabhängig davon, ob Handlichtlichter `FollowEyeGaze` aktiviert sind oder nicht.

Wenn Sie nun mit den Szenen der Eyetrackingdemo beginnen, sollten Sie einen Strahl sehen, der von Ihren Händen kommt.
In der Demo zur Auswahl des Eyetrackingziels folgt der halbtransparente Kreis noch immer Ihren Blicken, und die Gems reagieren darauf, ob sie anviert werden oder nicht, während die Menüschaltflächen der oberen Szene stattdessen den primären Eingabezeiger (Ihre Hände) verwenden.

---
[Zurück zu "Eye tracking in the MixedRealityToolkit"](eye-tracking-main.md)
