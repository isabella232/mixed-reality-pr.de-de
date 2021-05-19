---
title: EyeTracking-Zielauswahl
description: Zugreifen auf Anvitätsdaten mit den Augen und bestimmte Ereignisse beim Anvingen mit den Augen zum Auswählen von Zielen im MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, EyeTracking,
ms.openlocfilehash: 229903e01c597aefbb3fc29de8a49d79cbbd42d0
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144195"
---
# <a name="eye-supported-target-selection"></a>Durch die Augen unterstützte Zielauswahl

![MRTK](../../images/eye-tracking/mrtk_et_targetselect.png)

Auf dieser Seite werden verschiedene Optionen für den Zugriff auf Daten zum Anvieren mit den Augen und bestimmte Ereignisse für das Anvieren mit den Augen erläutert, um Ziele im MRTK auszuwählen. Eyetracking ermöglicht eine schnelle und mühelose Zielauswahl mithilfe einer Kombination von Informationen darüber, was ein Benutzer betrachtet, mit zusätzlichen Eingaben wie _Handtracking_ und _Sprachbefehlen:_

- Suchen & _Z.B. "Auswählen"_ (Standardstimmenbefehl)
- Suchen & _"Explode"_ oder _"Pop"_ (benutzerdefinierte Sprachbefehle)
- Suchen & Bluetooth-Schaltfläche
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

- Gehen Sie zur Schaltfläche, und drücken Sie sie.
- Sehen Sie sich ihn aus der Entfernung an, und sagen Sie "Auswählen".
- Ziel der Schaltfläche mithilfe eines Handstrahls und Ausführen einer Zusammendrückung. In diesem Fall besteht die flexibelste Lösung darin, den primären Fokushandler zu verwenden, da er Sie benachrichtigt, wenn der aktuell priorisierte primäre Fokuszeiger ein Ereignis auslöst. Beachten Sie, dass bei aktivierter Handlichtstrahl der Fokuszeiger für den Kopf oder das Anvisierten der Augen deaktiviert ist, sobald die Hände angezeigt werden.

> [!IMPORTANT]
> Beachten Sie, dass bei aktivierter Handlichtstrahl der Fokuszeiger für den Kopf oder das Anvisierten der Augen deaktiviert ist, sobald die Hände angezeigt werden. Wenn Sie eine [ _"Look and Pinch"-Interaktion_ unterstützen möchten, müssen Sie den Handstrahl deaktivieren.](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray) In unseren Eyetracking-Beispielszenen haben wir den Handstrahl deaktiviert, um umfangreichere Interaktionen mitHilfe von Augen und Handbewegungen zu zeigen . Weitere Informationen finden Sie unter z.B. [Eye-Supported Positioning](eye-tracking-eyes-and-hands.md).

[**2. Verwenden Sie den Augenfokus und den Handlichtstrahl gleichzeitig:**](#2-independent-eye-gaze-specific-eyetrackingtarget)

Es kann Fälle geben, in denen Sie spezifischer sein möchten, welche Art von Fokuszeigern bestimmte Ereignisse auslösen und gleichzeitig die Verwendung mehrerer Methoden für die Ferninteraktion ermöglichen kann.

Beispiel: In Ihrer App kann ein Benutzer fernen Handstrahl verwenden, um ein holografisches, maschinelles Setup zu bearbeiten, z. B. einige entfernte holografische Engine-Teile zu greifen und zu halten und sie an Ort und Stelle zu halten. Dabei muss der Benutzer eine Reihe von Anweisungen durchlaufen und seinen Fortschritt aufzeichnen, indem er einige Kontrollkästchen deaktiviert. Wenn der Benutzer seine Hände _nicht ausgelastet_ hat, wäre es instinktiv, einfach das Kontrollkästchen zu berühren oder es mit einem Handstrahl auszuwählen. Wenn der Benutzer jedoch seine Hände ausgelastet hat, wie in unserem Fall einige holografische Engine-Teile, möchten Sie es dem Benutzer ermöglichen, nahtlos durch die Anweisungen mit dem Blick zu scrollen und einfach ein Kontrollkästchen zu betrachten und "Check it!" zu sagen.

Um dies zu ermöglichen, müssen Sie ein eye-spezifisches EyeTrackingTarget-Skript verwenden, das von den KERN-MRTK FocusHandlers unabhängig ist und weiter unten erläutert wird.

## <a name="1-use-generic-focus-and-pointer-handlers"></a>1. Verwenden von generischen Fokus- und Zeigerhandlern

Wenn eye tracking ordnungsgemäß eingerichtet ist (siehe Grundlegende [MRTK-Einrichtung](eye-tracking-basic-setup.md)zur Verwendung von Eyetracking), ist die Auswahl von Hologrammen mit ihren Augen für Benutzer identisch mit jeder anderen Fokuseingabe (z. B. Anvieren mit dem Kopf oder Handstrahl). Dies bietet den großen Vorteil einer flexiblen Möglichkeit, mit Ihren Hologrammen zu interagieren, indem der Hauptfokustyp in Ihrem MRTK-Eingabezeigerprofil abhängig von den Anforderungen Ihres Benutzers definiert wird, während der Code unverändert bleibt. Dies ermöglicht das Wechseln zwischen dem Anvieren mit dem Kopf oder den Augen, ohne eine Codezeile zu ändern oder Handlichtlichter durch Das Ziel der Augen für ferne Interaktionen zu ersetzen.

### <a name="focusing-on-a-hologram"></a>Konzentrieren auf ein Hologramm

Um zu erkennen, wann ein Hologramm den Fokus hat, verwenden Sie die _Schnittstelle "IMixedRealityFocusHandler",_ die Zwei-Schnittstellen-Member zur Verfügung stellt: _OnFocusEnter_ und _OnFocusExit._

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

Im folgenden Beispiel ändern wir die Farbe eines Hologramms, indem wir es sehen und "auswählen" anheften oder sagen.
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

Da sich das Anvingen mit den Augen stark von anderen Zeigereingaben unterscheiden kann, sollten Sie sicherstellen, dass Sie nur auf die Fokuseingabe reagieren, wenn es sich um das Anvingen mit den Augen handelt und es sich derzeit um den primären Eingabezeiger handelt. 
Zu diesem Zweck verwenden Sie die , die für eye tracking spezifisch ist und von [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) der ableitung. [`BaseFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseFocusHandler)
Wie bereits erwähnt, wird sie nur ausgelöst, wenn das Anvanving mit den Augen derzeit die primäre Zeigereingabe ist (d. h., es ist kein Handstrahl aktiv). Weitere Informationen finden Sie unter [Unterstützen von Anving und Handgesten mit den Augen.](eye-tracking-eyes-and-hands.md)

Hier ist ein Beispiel aus `EyeTrackingDemo-03-Navigation` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes).
In dieser Demo gibt es zwei 3D-Hologramme, die sich abhängig davon drehen, welcher Teil des Objekts betrachtet wird: Wenn der Benutzer auf die linke Seite des Hologramms blickt, wird dieser Teil langsam an die Vorderseite des Benutzers gerichtet.
Wenn die rechte Seite angezeigt wird, wird dieser Teil langsam an den Anfang bewegt.
Dies ist ein Verhalten, das Sie möglicherweise nicht immer aktiv haben möchten, und auch etwas, das Sie möglicherweise nicht versehentlich durch einen Handstrahl oder anvieren mit dem Kopf auslösen möchten.
Wenn das [`OnLookAtRotateByEyeGaze`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) angefügt ist, wird ein GameObject rotiert, während es sich anschaut.

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
- **OnEyeFocusStay:** Wird *ausgelöst, während* sich der Blickstrahl mit dem Collider dieses Ziels überschneidet.
- **OnEyeFocusStop:** Wird ausgelöst, sobald  der Blickstrahl die Schnittpunkte mit dem Collider dieses Ziels beendet.
- **OnEyeFocusDwell:** Wird ausgelöst, sobald sich der Blickstrahl für einen bestimmten Zeitraum mit dem Collider dieses Ziels überschneidet hat.

## <a name="2-independent-eye-gaze-specific-eyetrackingtarget"></a>2. Unabhängige eye-gaze-spezifische EyeTrackingTarget-Methode

Schließlich stellen wir Ihnen eine Lösung zur Verfügung, mit der Sie die augenbasierte Eingabe über das Skript vollständig unabhängig von anderen Fokuszeige behandeln [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) können.

Dies hat drei _Vorteile:_

- Sie können sicherstellen, dass das Hologramm nur auf das Anvieren mit den Augen des Benutzers reagiert.
- Dies ist unabhängig von der derzeit aktiven primären Eingabe. Daher können Sie mehrere Eingaben gleichzeitig verarbeiten, z. B. das Kombinieren der Schnellen Blickrichtung mit Handgesten.
- Mehrere Unity-Ereignisse wurden bereits eingerichtet, um es schnell und bequem zu machen, vorhandene Verhaltensweisen innerhalb des Unity-Editors oder über Code zu verarbeiten und wiederzuverwenden.

Es gibt auch einige _Nachteile:_

- Mehr Aufwand, separate Eingaben einzeln zu verarbeiten.
- Keine eleganten Beeinträchtigungen: Sie unterstützt nur eye targeting. Wenn die Blickverfolgung nicht funktioniert, benötigen Sie ein zusätzliches Fallback.

Ähnlich wie beim _BaseFocusHandler_ ist _EyeTrackingTarget_ mit mehreren unity-spezifischen Unity-Ereignissen bereit, die Sie bequem über den Unity-Editor (siehe Beispiel unten) oder mit _AddListener()_ im Code lauschen können:

- OnLookAtStart()
- WhileLookingAtTarget()
- OnLookAway()
- OnDwell()
- OnSelected()

Im Folgenden werden einige Beispiele für die Verwendung von _EyeTrackingTarget erläutert._

### <a name="example-1-eye-supported-smart-notifications"></a>Beispiel #1: Intelligente Benachrichtigungen mit Eye-Unterstützung

In `EyeTrackingDemo-02-TargetSelection` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes) finden Sie ein Beispiel für _"intelligente Benachrichtigungen",_ die auf das Anverfolgen der Augen reagieren.
Hierbei handelt es sich um 3D-Textfelder, die in der Szene platziert werden können und die sich nahtlos vergrößern und dem Benutzer zuwenden, wenn sie betrachtet werden, um die Lesbarkeit zu erleichtern. Während der Benutzer die Benachrichtigung liest, werden die Informationen immer übersichtlicher und übersichtlicher angezeigt. Nach dem Lesen und Wegsehen von der Benachrichtigung wird die Benachrichtigung automatisch verworfen und ausgeblendet. Um all dies zu erreichen, gibt es einige generische Verhaltensskripts, die überhaupt nicht spezifisch für eye tracking sind, z. B.:

- [`FaceUser`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FaceUser)
- [`ChangeSize`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ChangeSize)
- [`BlendOut`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.BlendOut)

Der Vorteil dieses Ansatzes besteht darin, dass dieselben Skripts von verschiedenen Ereignissen wiederverwendet werden können. Ein Hologramm kann z. B. auf der Grundlage von Sprachbefehlen oder nach dem Drücken einer virtuellen Schaltfläche mit dem Benutzer beginnen. Um diese Ereignisse auszulösen, können Sie einfach auf die Methoden verweisen, die in dem Skript ausgeführt werden [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) sollen, das an Ihr GameObject angefügt ist.

Für das Beispiel der _"intelligenten Benachrichtigungen"_ geschieht Folgendes:

- **OnLookAtStart()**: Die Benachrichtigung beginnt mit...
  - *FaceUser.Engage:* ... wenden Sie sich an den Benutzer.
  - *ChangeSize.Engage:* ... Vergrößern _(bis zu einer angegebenen maximalen Skala)_.
  - *BlendOut.Engage:* ... beginnt, mehr zu mischen _(nachdem sie sich in einem dezenteren Leerlaufzustand befinden)_.  

- **OnDwell():** Informiert das _BlendOut-Skript_ darüber, dass die Benachrichtigung ausreichend untersucht wurde.

- **OnLookAway():** Die Benachrichtigung beginnt mit...
  - *FaceUser.Disengage:* ... Kehren Sie zur ursprünglichen Ausrichtung zurück.
  - *ChangeSize.Disengage:* ... Verringern Sie wieder auf die ursprüngliche Größe.
  - *BlendOut.Disengage:* ... beginnt mit dem Ausblenden: Wenn _OnDwell()_ ausgelöst wurde, blenden Sie vollständig aus, und zerstören Sie es, andernfalls wieder in den Leerlaufzustand zurück.

**Entwurfsüberlegung:** Der Schlüssel zu einer ansprechenden Erfahrung besteht darin, die Geschwindigkeit jedes dieser Verhaltensweisen sorgfältig zu optimieren, um zu vermeiden, dass es zu Störungen führt, indem sie ständig zu schnell auf die Blicke des Benutzers reagieren.
Andernfalls kann dies schnell extrem überwältigend wirken.

<img src="../../images/eye-tracking/mrtk_et_EyeTrackingTarget_Notification.jpg" width="750" alt="Target Notification">

### <a name="example-2-holographic-gem-rotates-slowly-when-looking-at-it"></a>Beispiel #2: Holografisches Gem wird beim Betrachten langsam gedreht

Ähnlich wie bei beispiel #1 können wir einfach ein Hoverfeedback für unsere holografischen Gems in `EyeTrackingDemo-02-TargetSelection` der Szene (Assets/MRTK/Examples/Demos/EyeTracking/Scenes) erstellen, die sich langsam in konstanter Richtung und mit konstanter Geschwindigkeit (im Gegensatz zum Obigen Drehungsbeispiel) drehen, wenn wir uns ansehen. Sie müssen lediglich die Drehung des holografischen Gem aus dem _WhileLookingAtTarget()-Ereignis_ von _EyeTrackingTarget_ auslösen. Im Anschluss finden Sie einige weitere Details:

1. Erstellen Sie ein generisches Skript, das eine öffentliche Funktion zum Drehen des GameObject enthält, an das es angefügt ist. Im Folgenden finden Sie ein Beispiel aus _RotateWithConstSpeedDir.cs,_ in dem wir die Drehrichtung und Geschwindigkeit im Unity-Editor optimieren können.

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

1. Fügen Sie das Skript ihrem Ziel-GameObject hinzu, und verweisen Sie im UnityEvent-Trigger wie im folgenden Screenshot gezeigt [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) auf die _RotateTarget()-Funktion:_

    ![EyeTrackingTarget-Beispiel](../../images/eye-tracking/mrtk_et_EyeTrackingTargetSample.jpg)

### <a name="example-3-pop-those-gems-aka-_multi-modal-eye-gaze-supported-target-selection_"></a>Beispiel #3: Pop those gems aka _multi-modal eye-gaze-supported target selection_

Im vorherigen Beispiel haben wir gezeigt, wie einfach es ist, zu erkennen, ob ein Ziel angezeigt wird und wie eine Reaktion darauf ausgelöst werden kann. Als Nächstes lassen Sie die Gems mithilfe des _OnSelected()-Ereignisses_ aus explodieren. [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) Der interessante Teil *ist, wie* die Auswahl ausgelöst wird. Ermöglicht [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) das schnelle Zuweisen verschiedener Methoden zum Aufrufen einer Auswahl:

- _Geste zum Anheften:_ Wenn Sie "Aktion auswählen" auf "Auswählen" festlegen, wird die Standardhandgeste verwendet, um die Auswahl auszulösen.
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

![EyeTrackingTarget-Beispiel für Sprachbefehle](../../images/eye-tracking/mrtk_et_voicecmdsample.jpg)

Wenn ein Gem ausgewählt wird, explodiert es, sodass ein Sound entsteht und verschwindet. Dies wird vom [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) Skript behandelt. Sie haben zwei Möglichkeiten:

- **Im Unity-Editor:** Sie können das Skript, das an jede unserer Gem-Vorlagen angefügt ist, einfach mit dem Unity-Ereignis OnSelected() im Unity-Editor verknüpfen.
- **In code:** If you don't want to drag and drop GameObjects around, you can also simply add a event listener directly to your script.  
Hier sehen Sie ein Beispiel dafür, wie wir dies im Skript gemacht [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) haben:

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

### <a name="example-4-use-hand-rays-and-eye-gaze-input-together"></a>Beispiel #4: Gemeinsames Verwenden von Handlicht- und Anvisierteneingaben mit den Augen

Handlichter haben Vorrang vor dem Anvisieren mit dem Kopf und den Augen. Dies bedeutet, dass der Handstrahl als primärer Zeiger fungiert, wenn Handlichtlicht aktiviert ist, sobald die Hände angezeigt werden.
Es kann jedoch Situationen geben, in denen Sie Handstrahl verwenden möchten, während Sie dennoch erkennen, ob ein Benutzer ein bestimmtes Hologramm ansieht. Kein Problem! Im Wesentlichen sind zwei Schritte erforderlich:

**1. Aktivieren des Handstrahls:** Um den Handstrahl zu aktivieren, wechseln Sie zu _Mixed Reality Toolkit -> Input -> Pointers_.
Im _EyeTrackingDemo-00-RootScene,_ in dem das Mixed Reality Toolkit einmal für alle Eyetracking-Demoszenen konfiguriert ist, sollte _eyeTrackingDemoPointerProfile_ angezeigt werden.
Sie können entweder ein neues _Eingabeprofil_ von Grund auf neu erstellen oder das aktuelle Eyetracking anpassen:

- **Von Grund auf neu:** Wählen Sie auf der Registerkarte _Zeiger_ im Kontextmenü _defaultMixedRealityInputPointerProfile_ aus.
Dies ist das Standardzeigerprofil, für das der Handstrahl bereits aktiviert ist.
Um den Standardcursor (einen nicht transparenten weißen Punkt) zu ändern, klonen Sie einfach das Profil, und erstellen Sie Ein eigenes benutzerdefiniertes Zeigerprofil.
Ersetzen Sie dann _DefaultCursor_ durch _EyeGazeCursor_ unter _Gaze Cursor Prefab_.  
- **Basierend auf dem vorhandenen _EyeTrackingDemoPointerProfile:_** Doppelklicken Sie auf _eyeTrackingDemoPointerProfile,_ und fügen Sie unter _Zeigeroptionen_ den folgenden Eintrag hinzu:
  - **Controllertyp:** "Artikulierte Hand", "Windows Mixed Reality"
  - **Übergabe:** jegliche
  - **Zeiger-Prefab:** DefaultControllerPointer

**2. Erkennen, dass** ein Hologramm angezeigt wird: Verwenden Sie das Skript, um die Erkennung zu ermöglichen, dass ein Hologramm wie oben [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) beschrieben angezeigt wird. Sie können sich auch das Beispielskript zur Inspiration anschauen, da dies ein Hologramm zeigt, das auf das Anvieren mit den Augen folgt (z. B. ein Cursor), unabhängig davon, ob Handlichtlichter `FollowEyeGaze` aktiviert sind oder nicht.

Wenn Sie nun mit den Szenen der Eyetrackingdemo beginnen, sollten Sie einen Strahl sehen, der von Ihren Händen kommt.
In der Demo zur Auswahl des Eyetrackingziels folgt der halbtransparente Kreis noch immer ihren Blickanviert, und die Gems reagieren darauf, ob sie anviert werden oder nicht, während die Menüschaltflächen der oberen Szene stattdessen den primären Eingabezeiger (Ihre Hände) verwenden.

---
[Zurück zu "Eye tracking in the MixedRealityToolkit"](eye-tracking-main.md)
