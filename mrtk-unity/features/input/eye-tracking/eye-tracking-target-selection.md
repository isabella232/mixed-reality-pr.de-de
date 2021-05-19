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
# <a name="eye-supported-target-selection"></a><span data-ttu-id="45863-104">Durch die Augen unterstützte Zielauswahl</span><span class="sxs-lookup"><span data-stu-id="45863-104">Eye-supported target selection</span></span>

![MRTK](../../images/eye-tracking/mrtk_et_targetselect.png)

<span data-ttu-id="45863-106">Auf dieser Seite werden verschiedene Optionen für den Zugriff auf Daten zum Anvieren mit den Augen und bestimmte Ereignisse für das Anvieren mit den Augen erläutert, um Ziele im MRTK auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="45863-106">This page discusses different options for accessing eye gaze data and eye gaze specific events to select targets in MRTK.</span></span> <span data-ttu-id="45863-107">Eyetracking ermöglicht eine schnelle und mühelose Zielauswahl mithilfe einer Kombination von Informationen darüber, was ein Benutzer betrachtet, mit zusätzlichen Eingaben wie _Handtracking_ und _Sprachbefehlen:_</span><span class="sxs-lookup"><span data-stu-id="45863-107">Eye tracking allows for fast and effortless target selections using a combination of information about what a user is looking at with additional inputs such as _hand tracking_ and _voice commands_:</span></span>

- <span data-ttu-id="45863-108">Suchen & _Z.B. "Auswählen"_ (Standardstimmenbefehl)</span><span class="sxs-lookup"><span data-stu-id="45863-108">Look & Say _"Select"_ (default voice command)</span></span>
- <span data-ttu-id="45863-109">Suchen & _"Explode"_ oder _"Pop"_ (benutzerdefinierte Sprachbefehle)</span><span class="sxs-lookup"><span data-stu-id="45863-109">Look & Say _"Explode"_ or _"Pop"_ (custom voice commands)</span></span>
- <span data-ttu-id="45863-110">Suchen & Bluetooth-Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="45863-110">Look & Bluetooth button</span></span>
- <span data-ttu-id="45863-111">Suchen & Zusammendnüpfen (d. h. halten Sie die Hand vor Ihnen, und bringen Sie Ihren Daumen und Zeigefinger zusammen)</span><span class="sxs-lookup"><span data-stu-id="45863-111">Look & Pinch (i.e., hold up your hand in front of you and bring your thumb and index finger together)</span></span>
  - <span data-ttu-id="45863-112">Beachten Sie, dass die Handlichtlichter deaktiviert werden müssen, damit [dies funktioniert.](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray)</span><span class="sxs-lookup"><span data-stu-id="45863-112">Please note that for this to work, the [hand rays need to be disabled](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray)</span></span>

<span data-ttu-id="45863-113">Es gibt mehrere Optionen, um holografische Inhalte mit dem Anvitäts-Blick auf die Augen auszuwählen:</span><span class="sxs-lookup"><span data-stu-id="45863-113">To select holographic content using eye gaze, there are several options:</span></span>

[<span data-ttu-id="45863-114">**1. Verwenden Sie den primären Fokuszeiger:**</span><span class="sxs-lookup"><span data-stu-id="45863-114">**1. Use the primary focus pointer:**</span></span>](#1-use-generic-focus-and-pointer-handlers)

<span data-ttu-id="45863-115">Dies kann als priorisierter Cursor verstanden werden.</span><span class="sxs-lookup"><span data-stu-id="45863-115">This can be understood as your prioritized cursor.</span></span>
<span data-ttu-id="45863-116">Wenn die Hände angezeigt werden, wäre dies standardmäßig Handlichtlichter.</span><span class="sxs-lookup"><span data-stu-id="45863-116">By default, if the hands are in view, then this would be hand rays.</span></span>
<span data-ttu-id="45863-117">Wenn keine Hände angezeigt werden, ist der priorisierte Zeiger das Anvisieren mit dem Kopf oder den Augen.</span><span class="sxs-lookup"><span data-stu-id="45863-117">If no hands are in view, then the prioritized pointer would be head or eye gaze.</span></span>
<span data-ttu-id="45863-118">Beachten Sie daher, dass basierend auf dem aktuellen Design das Anvieren mit dem Kopf oder mit den Augen als Cursoreingabe unterdrückt wird, wenn Handlichtlichter verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="45863-118">Thus, please note that based on the current design head or eye gaze is suppressed as a cursor input if hand rays are used.</span></span>

<span data-ttu-id="45863-119">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="45863-119">For example:</span></span>

<span data-ttu-id="45863-120">Ein Benutzer möchte eine entfernte holografische Schaltfläche auswählen.</span><span class="sxs-lookup"><span data-stu-id="45863-120">A user wants to select a distant holographic button.</span></span>
<span data-ttu-id="45863-121">Als Entwickler möchten Sie eine flexible Lösung bereitstellen, die es dem Benutzer ermöglicht, diese Aufgaben unter verschiedenen Bedingungen auszuführen:</span><span class="sxs-lookup"><span data-stu-id="45863-121">As a developer, you want to provide a flexible solution that allows the user to achieve this tasks in various conditions:</span></span>

- <span data-ttu-id="45863-122">Gehen Sie zur Schaltfläche, und drücken Sie sie.</span><span class="sxs-lookup"><span data-stu-id="45863-122">Walk up to the button and poke it</span></span>
- <span data-ttu-id="45863-123">Sehen Sie sich ihn aus der Entfernung an, und sagen Sie "Auswählen".</span><span class="sxs-lookup"><span data-stu-id="45863-123">Look at it from a distance and say "select"</span></span>
- <span data-ttu-id="45863-124">Ziel der Schaltfläche mithilfe eines Handstrahls und Ausführen einer Zusammendrückung. In diesem Fall besteht die flexibelste Lösung darin, den primären Fokushandler zu verwenden, da er Sie benachrichtigt, wenn der aktuell priorisierte primäre Fokuszeiger ein Ereignis auslöst.</span><span class="sxs-lookup"><span data-stu-id="45863-124">Target the button using a hand ray and performing a pinch In this case, the most flexible solution is to use the primary focus handler as it will notify you whenever the currently prioritized primary focus pointer triggers an event.</span></span> <span data-ttu-id="45863-125">Beachten Sie, dass bei aktivierter Handlichtstrahl der Fokuszeiger für den Kopf oder das Anvisierten der Augen deaktiviert ist, sobald die Hände angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="45863-125">Please note that if hand rays are enabled, the head or eye gaze focus pointer are disabled as soon as the hands come into view.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="45863-126">Beachten Sie, dass bei aktivierter Handlichtstrahl der Fokuszeiger für den Kopf oder das Anvisierten der Augen deaktiviert ist, sobald die Hände angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="45863-126">Please note that if hand rays are enabled, the head or eye gaze focus pointer are disabled as soon as the hands come into view.</span></span> <span data-ttu-id="45863-127">Wenn Sie eine [ _"Look and Pinch"-Interaktion_ unterstützen möchten, müssen Sie den Handstrahl deaktivieren.](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray)</span><span class="sxs-lookup"><span data-stu-id="45863-127">If you want to support a [_'look and pinch'_ interaction, you need to disable the hand ray](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray).</span></span> <span data-ttu-id="45863-128">In unseren Eyetracking-Beispielszenen haben wir den Handstrahl deaktiviert, um umfangreichere Interaktionen mitHilfe von Augen und Handbewegungen zu zeigen . Weitere Informationen finden Sie unter z.B. [Eye-Supported Positioning](eye-tracking-eyes-and-hands.md).</span><span class="sxs-lookup"><span data-stu-id="45863-128">In our eye tracking sample scenes, we have disabled the hand ray to allow for showcasing richer interactions using eyes + hand motions - see for example [Eye-Supported Positioning](eye-tracking-eyes-and-hands.md).</span></span>

[<span data-ttu-id="45863-129">**2. Verwenden Sie den Augenfokus und den Handlichtstrahl gleichzeitig:**</span><span class="sxs-lookup"><span data-stu-id="45863-129">**2. Use both eye focus and hand rays at the same time:**</span></span>](#2-independent-eye-gaze-specific-eyetrackingtarget)

<span data-ttu-id="45863-130">Es kann Fälle geben, in denen Sie spezifischer sein möchten, welche Art von Fokuszeigern bestimmte Ereignisse auslösen und gleichzeitig die Verwendung mehrerer Methoden für die Ferninteraktion ermöglichen kann.</span><span class="sxs-lookup"><span data-stu-id="45863-130">There might be instances where you want to be more specific which type of focus pointers can trigger certain events and allow for simultaneously using multiple far interaction techniques.</span></span>

<span data-ttu-id="45863-131">Beispiel: In Ihrer App kann ein Benutzer fernen Handstrahl verwenden, um ein holografisches, maschinelles Setup zu bearbeiten, z. B. einige entfernte holografische Engine-Teile zu greifen und zu halten und sie an Ort und Stelle zu halten.</span><span class="sxs-lookup"><span data-stu-id="45863-131">For example: In your app, a user can use far hand rays to manipulate some holographic mechanical setup - e.g., grab and hold some distant holographic engine parts and hold them in place.</span></span> <span data-ttu-id="45863-132">Dabei muss der Benutzer eine Reihe von Anweisungen durchlaufen und seinen Fortschritt aufzeichnen, indem er einige Kontrollkästchen deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="45863-132">While doing so, the user has to go through a number of instructions and record her/his progress by marking off some check boxes.</span></span> <span data-ttu-id="45863-133">Wenn der Benutzer seine Hände _nicht ausgelastet_ hat, wäre es instinktiv, einfach das Kontrollkästchen zu berühren oder es mit einem Handstrahl auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="45863-133">If the user has her/his hands _not busy_, it would be instinctual to simply touch the check box or select it using a hand ray.</span></span> <span data-ttu-id="45863-134">Wenn der Benutzer jedoch seine Hände ausgelastet hat, wie in unserem Fall einige holografische Engine-Teile, möchten Sie es dem Benutzer ermöglichen, nahtlos durch die Anweisungen mit dem Blick zu scrollen und einfach ein Kontrollkästchen zu betrachten und "Check it!" zu sagen.</span><span class="sxs-lookup"><span data-stu-id="45863-134">However, if the user has her/his hands busy, as in our case holding some holographic engine parts in place, you want to enable the user to seamlessly scroll through the instructions using their eye gaze and to simply look at a check box and say "check it!".</span></span>

<span data-ttu-id="45863-135">Um dies zu ermöglichen, müssen Sie ein eye-spezifisches EyeTrackingTarget-Skript verwenden, das von den KERN-MRTK FocusHandlers unabhängig ist und weiter unten erläutert wird.</span><span class="sxs-lookup"><span data-stu-id="45863-135">To enable this, you need to use eye-specific EyeTrackingTarget script that is independent from the core MRTK FocusHandlers and will be discussed further below.</span></span>

## <a name="1-use-generic-focus-and-pointer-handlers"></a><span data-ttu-id="45863-136">1. Verwenden von generischen Fokus- und Zeigerhandlern</span><span class="sxs-lookup"><span data-stu-id="45863-136">1. Use generic focus and pointer handlers</span></span>

<span data-ttu-id="45863-137">Wenn eye tracking ordnungsgemäß eingerichtet ist (siehe Grundlegende [MRTK-Einrichtung](eye-tracking-basic-setup.md)zur Verwendung von Eyetracking), ist die Auswahl von Hologrammen mit ihren Augen für Benutzer identisch mit jeder anderen Fokuseingabe (z. B. Anvieren mit dem Kopf oder Handstrahl). Dies bietet den großen Vorteil einer flexiblen Möglichkeit, mit Ihren Hologrammen zu interagieren, indem der Hauptfokustyp in Ihrem MRTK-Eingabezeigerprofil abhängig von den Anforderungen Ihres Benutzers definiert wird, während der Code unverändert bleibt.</span><span class="sxs-lookup"><span data-stu-id="45863-137">If eye tracking is set up correctly (see [Basic MRTK setup to use eye tracking](eye-tracking-basic-setup.md)), enabling users to select holograms using their eyes is the same as for any other focus input (e.g., head gaze or hand ray).This provides the great advantage of a flexible way to interact with your holograms by defining the main focus type in your MRTK Input Pointer Profile depending on your user's needs, while leaving your code untouched.</span></span> <span data-ttu-id="45863-138">Dies ermöglicht das Wechseln zwischen dem Anvieren mit dem Kopf oder den Augen, ohne eine Codezeile zu ändern oder Handlichtlichter durch Das Ziel der Augen für ferne Interaktionen zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="45863-138">This allows for switching between head or eye gaze without changing a line of code or replace hand rays with eye targeting for far interactions.</span></span>

### <a name="focusing-on-a-hologram"></a><span data-ttu-id="45863-139">Konzentrieren auf ein Hologramm</span><span class="sxs-lookup"><span data-stu-id="45863-139">Focusing on a hologram</span></span>

<span data-ttu-id="45863-140">Um zu erkennen, wann ein Hologramm den Fokus hat, verwenden Sie die _Schnittstelle "IMixedRealityFocusHandler",_ die Zwei-Schnittstellen-Member zur Verfügung stellt: _OnFocusEnter_ und _OnFocusExit._</span><span class="sxs-lookup"><span data-stu-id="45863-140">To detect when a hologram is focused, use the _'IMixedRealityFocusHandler'_ interface that provides you with two interface members: _OnFocusEnter_ and _OnFocusExit_.</span></span>

<span data-ttu-id="45863-141">Hier sehen Sie ein einfaches Beispiel aus [ColorTap.cs,](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ColorTap) um die Farbe eines Hologramms zu ändern, wenn sie sich anschaut.</span><span class="sxs-lookup"><span data-stu-id="45863-141">Here is a simple example from [ColorTap.cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ColorTap) to change a hologram's color when being looked at.</span></span>

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

### <a name="selecting-a-focused-hologram"></a><span data-ttu-id="45863-142">Auswählen eines fokussierten Hologramms</span><span class="sxs-lookup"><span data-stu-id="45863-142">Selecting a focused hologram</span></span>

<span data-ttu-id="45863-143">Um ein fokussiertes Hologramm auszuwählen, verwenden Sie _PointerHandler,_ um auf Eingabeereignisse zu lauschen, um eine Auswahl zu bestätigen.</span><span class="sxs-lookup"><span data-stu-id="45863-143">To select a focused hologram, use _PointerHandler_ to listen for input events to confirm a selection.</span></span>
<span data-ttu-id="45863-144">Wenn Sie beispielsweise den _IMixedRealityPointerHandler_ hinzufügen, reagieren sie auf einfache Zeigereingaben.</span><span class="sxs-lookup"><span data-stu-id="45863-144">For example, adding the _IMixedRealityPointerHandler_ will make them react to simple pointer input.</span></span>
<span data-ttu-id="45863-145">Die _IMixedRealityPointerHandler-Schnittstelle_ erfordert die Implementierung der folgenden drei Schnittstellenmitglieder: _OnPointerUp,_ _OnPointerDown_ und _OnPointerClicked_.</span><span class="sxs-lookup"><span data-stu-id="45863-145">The _IMixedRealityPointerHandler_ interface requires implementing the following three interface members: _OnPointerUp_, _OnPointerDown_, and _OnPointerClicked_.</span></span>

<span data-ttu-id="45863-146">Im folgenden Beispiel ändern wir die Farbe eines Hologramms, indem wir es sehen und "auswählen" anheften oder sagen.</span><span class="sxs-lookup"><span data-stu-id="45863-146">In the example below, we change the color of a hologram by looking at it and pinching or saying "select".</span></span>
<span data-ttu-id="45863-147">Die erforderliche Aktion zum Auslösen des Ereignisses wird definiert, indem wir den Typ von im Unity-Editor festlegen können. Standardmäßig handelt es sich um die `eventData.MixedRealityInputAction == selectAction` `selectAction` Aktion "Auswählen".</span><span class="sxs-lookup"><span data-stu-id="45863-147">The required action to trigger the event is defined by `eventData.MixedRealityInputAction == selectAction` whereby we can set the type of `selectAction` in the Unity Editor - by default it's the "Select" action.</span></span> <span data-ttu-id="45863-148">Die Typen der verfügbaren [MixedRealityInputActions können](../input-actions.md) im MRTK-Profil über Eingabeaktionen des _MRTK-Konfigurationsprofils_  ->    ->  _konfiguriert werden._</span><span class="sxs-lookup"><span data-stu-id="45863-148">The types of available [MixedRealityInputActions](../input-actions.md) can be configured in the MRTK Profile via _MRTK Configuration Profile_ -> _Input_ -> _Input Actions_.</span></span>

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

### <a name="eye-gaze-specific-baseeyefocushandler"></a><span data-ttu-id="45863-149">BaseEyeFocusHandler-Spezifisches Anvieren mit den Augen</span><span class="sxs-lookup"><span data-stu-id="45863-149">Eye-gaze-specific BaseEyeFocusHandler</span></span>

<span data-ttu-id="45863-150">Da sich das Anvingen mit den Augen stark von anderen Zeigereingaben unterscheiden kann, sollten Sie sicherstellen, dass Sie nur auf die Fokuseingabe reagieren, wenn es sich um das Anvingen mit den Augen handelt und es sich derzeit um den primären Eingabezeiger handelt. </span><span class="sxs-lookup"><span data-stu-id="45863-150">Given that eye gaze can be very different to other pointer inputs, you may want to make sure to only react to the focus input if it is _eye gaze_ and it is currently the primary input pointer.</span></span>
<span data-ttu-id="45863-151">Zu diesem Zweck verwenden Sie die , die für eye tracking spezifisch ist und von [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) der ableitung. [`BaseFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseFocusHandler)</span><span class="sxs-lookup"><span data-stu-id="45863-151">For this purpose, you would use the [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) which is specific to eye tracking and which derives from the [`BaseFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseFocusHandler).</span></span>
<span data-ttu-id="45863-152">Wie bereits erwähnt, wird sie nur ausgelöst, wenn das Anvanving mit den Augen derzeit die primäre Zeigereingabe ist (d. h., es ist kein Handstrahl aktiv).</span><span class="sxs-lookup"><span data-stu-id="45863-152">As mentioned before, it will only trigger if eye gaze targeting is currently the primary pointer input (i.e., no hand ray is active).</span></span> <span data-ttu-id="45863-153">Weitere Informationen finden Sie unter [Unterstützen von Anving und Handgesten mit den Augen.](eye-tracking-eyes-and-hands.md)</span><span class="sxs-lookup"><span data-stu-id="45863-153">For more information, see [How to support eye gaze + hand gestures](eye-tracking-eyes-and-hands.md).</span></span>

<span data-ttu-id="45863-154">Hier ist ein Beispiel aus `EyeTrackingDemo-03-Navigation` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes).</span><span class="sxs-lookup"><span data-stu-id="45863-154">Here is an example from `EyeTrackingDemo-03-Navigation` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes).</span></span>
<span data-ttu-id="45863-155">In dieser Demo gibt es zwei 3D-Hologramme, die sich abhängig davon drehen, welcher Teil des Objekts betrachtet wird: Wenn der Benutzer auf die linke Seite des Hologramms blickt, wird dieser Teil langsam an die Vorderseite des Benutzers gerichtet.</span><span class="sxs-lookup"><span data-stu-id="45863-155">In this demo, there are two 3D holograms that will turn depending on which part of the object is looked at: If the user looks at the left side of the hologram, then that part will slowly move towards the front facing the user.</span></span>
<span data-ttu-id="45863-156">Wenn die rechte Seite angezeigt wird, wird dieser Teil langsam an den Anfang bewegt.</span><span class="sxs-lookup"><span data-stu-id="45863-156">If the right side is looked at, then that part will slowly move to the front.</span></span>
<span data-ttu-id="45863-157">Dies ist ein Verhalten, das Sie möglicherweise nicht immer aktiv haben möchten, und auch etwas, das Sie möglicherweise nicht versehentlich durch einen Handstrahl oder anvieren mit dem Kopf auslösen möchten.</span><span class="sxs-lookup"><span data-stu-id="45863-157">This is a behavior that you may not want to have active at all times and also something that you may not want to accidentally trigger by a hand ray or head gaze.</span></span>
<span data-ttu-id="45863-158">Wenn das [`OnLookAtRotateByEyeGaze`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) angefügt ist, wird ein GameObject rotiert, während es sich anschaut.</span><span class="sxs-lookup"><span data-stu-id="45863-158">Having the [`OnLookAtRotateByEyeGaze`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) attached, a GameObject will rotate while being looked at.</span></span>

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

<span data-ttu-id="45863-159">Eine vollständige Liste der verfügbaren Ereignisse von finden Sie in der [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) API-Dokumentation:</span><span class="sxs-lookup"><span data-stu-id="45863-159">Check the API documentation for a complete list of available events of the [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler):</span></span>

- <span data-ttu-id="45863-160">**OnEyeFocusStart:** Wird ausgelöst, sobald der Blickstrahl *beginnt,* sich mit dem Collider dieses Ziels zu überschneiden.</span><span class="sxs-lookup"><span data-stu-id="45863-160">**OnEyeFocusStart:** Triggered once the eye gaze ray *starts* intersecting with this target's collider.</span></span>
- <span data-ttu-id="45863-161">**OnEyeFocusStay:** Wird *ausgelöst, während* sich der Blickstrahl mit dem Collider dieses Ziels überschneidet.</span><span class="sxs-lookup"><span data-stu-id="45863-161">**OnEyeFocusStay:** Triggered *while* the eye gaze ray is intersecting with this target's collider.</span></span>
- <span data-ttu-id="45863-162">**OnEyeFocusStop:** Wird ausgelöst, sobald  der Blickstrahl die Schnittpunkte mit dem Collider dieses Ziels beendet.</span><span class="sxs-lookup"><span data-stu-id="45863-162">**OnEyeFocusStop:** Triggered once the eye gaze ray *stops* intersecting with this target's collider.</span></span>
- <span data-ttu-id="45863-163">**OnEyeFocusDwell:** Wird ausgelöst, sobald sich der Blickstrahl für einen bestimmten Zeitraum mit dem Collider dieses Ziels überschneidet hat.</span><span class="sxs-lookup"><span data-stu-id="45863-163">**OnEyeFocusDwell:** Triggered once the eye gaze ray has intersected with this target's collider for a specified amount of time.</span></span>

## <a name="2-independent-eye-gaze-specific-eyetrackingtarget"></a><span data-ttu-id="45863-164">2. Unabhängige eye-gaze-spezifische EyeTrackingTarget-Methode</span><span class="sxs-lookup"><span data-stu-id="45863-164">2. Independent eye-gaze-specific EyeTrackingTarget</span></span>

<span data-ttu-id="45863-165">Schließlich stellen wir Ihnen eine Lösung zur Verfügung, mit der Sie die augenbasierte Eingabe über das Skript vollständig unabhängig von anderen Fokuszeige behandeln [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) können.</span><span class="sxs-lookup"><span data-stu-id="45863-165">Finally, we provide you with a solution that let's you treat eye-based input completely independent from other focus pointers via the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script.</span></span>

<span data-ttu-id="45863-166">Dies hat drei _Vorteile:_</span><span class="sxs-lookup"><span data-stu-id="45863-166">This has three _advantages_:</span></span>

- <span data-ttu-id="45863-167">Sie können sicherstellen, dass das Hologramm nur auf das Anvieren mit den Augen des Benutzers reagiert.</span><span class="sxs-lookup"><span data-stu-id="45863-167">You can make sure that the hologram is only reacting to the user's eye gaze.</span></span>
- <span data-ttu-id="45863-168">Dies ist unabhängig von der derzeit aktiven primären Eingabe.</span><span class="sxs-lookup"><span data-stu-id="45863-168">This is independent from the currently active primary input.</span></span> <span data-ttu-id="45863-169">Daher können Sie mehrere Eingaben gleichzeitig verarbeiten, z. B. das Kombinieren der Schnellen Blickrichtung mit Handgesten.</span><span class="sxs-lookup"><span data-stu-id="45863-169">Hence, you can process multiple inputs at once - for example, combining fast eye targeting with hand gestures.</span></span>
- <span data-ttu-id="45863-170">Mehrere Unity-Ereignisse wurden bereits eingerichtet, um es schnell und bequem zu machen, vorhandene Verhaltensweisen innerhalb des Unity-Editors oder über Code zu verarbeiten und wiederzuverwenden.</span><span class="sxs-lookup"><span data-stu-id="45863-170">Several Unity events have already been set up to make it fast and convenient to handle and reuse existing behaviors from within the Unity Editor or via code.</span></span>

<span data-ttu-id="45863-171">Es gibt auch einige _Nachteile:_</span><span class="sxs-lookup"><span data-stu-id="45863-171">There are also some _disadvantages:_</span></span>

- <span data-ttu-id="45863-172">Mehr Aufwand, separate Eingaben einzeln zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="45863-172">More effort to handle separate inputs individually.</span></span>
- <span data-ttu-id="45863-173">Keine eleganten Beeinträchtigungen: Sie unterstützt nur eye targeting.</span><span class="sxs-lookup"><span data-stu-id="45863-173">No elegant degradation: It only supports eye targeting.</span></span> <span data-ttu-id="45863-174">Wenn die Blickverfolgung nicht funktioniert, benötigen Sie ein zusätzliches Fallback.</span><span class="sxs-lookup"><span data-stu-id="45863-174">If eye tracking is not working, you require some additional fallback.</span></span>

<span data-ttu-id="45863-175">Ähnlich wie beim _BaseFocusHandler_ ist _EyeTrackingTarget_ mit mehreren unity-spezifischen Unity-Ereignissen bereit, die Sie bequem über den Unity-Editor (siehe Beispiel unten) oder mit _AddListener()_ im Code lauschen können:</span><span class="sxs-lookup"><span data-stu-id="45863-175">Similar to the _BaseFocusHandler_, the _EyeTrackingTarget_ comes ready with several eye-gaze-specific Unity events that you can conveniently listen to either via the Unity Editor (see example below) or by using _AddListener()_ in code:</span></span>

- <span data-ttu-id="45863-176">OnLookAtStart()</span><span class="sxs-lookup"><span data-stu-id="45863-176">OnLookAtStart()</span></span>
- <span data-ttu-id="45863-177">WhileLookingAtTarget()</span><span class="sxs-lookup"><span data-stu-id="45863-177">WhileLookingAtTarget()</span></span>
- <span data-ttu-id="45863-178">OnLookAway()</span><span class="sxs-lookup"><span data-stu-id="45863-178">OnLookAway()</span></span>
- <span data-ttu-id="45863-179">OnDwell()</span><span class="sxs-lookup"><span data-stu-id="45863-179">OnDwell()</span></span>
- <span data-ttu-id="45863-180">OnSelected()</span><span class="sxs-lookup"><span data-stu-id="45863-180">OnSelected()</span></span>

<span data-ttu-id="45863-181">Im Folgenden werden einige Beispiele für die Verwendung von _EyeTrackingTarget erläutert._</span><span class="sxs-lookup"><span data-stu-id="45863-181">In the following, we walk you through a few examples for how to use _EyeTrackingTarget_.</span></span>

### <a name="example-1-eye-supported-smart-notifications"></a><span data-ttu-id="45863-182">Beispiel #1: Intelligente Benachrichtigungen mit Eye-Unterstützung</span><span class="sxs-lookup"><span data-stu-id="45863-182">Example #1: Eye-supported smart notifications</span></span>

<span data-ttu-id="45863-183">In `EyeTrackingDemo-02-TargetSelection` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes) finden Sie ein Beispiel für _"intelligente Benachrichtigungen",_ die auf das Anverfolgen der Augen reagieren.</span><span class="sxs-lookup"><span data-stu-id="45863-183">In `EyeTrackingDemo-02-TargetSelection` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes), you can find an example for _'smart attentive notifications'_ that react to your eye gaze.</span></span>
<span data-ttu-id="45863-184">Hierbei handelt es sich um 3D-Textfelder, die in der Szene platziert werden können und die sich nahtlos vergrößern und dem Benutzer zuwenden, wenn sie betrachtet werden, um die Lesbarkeit zu erleichtern.</span><span class="sxs-lookup"><span data-stu-id="45863-184">These are 3D text boxes that can be placed in the scene and that will smoothly enlarge and turn toward the user when being looked at to ease legibility.</span></span> <span data-ttu-id="45863-185">Während der Benutzer die Benachrichtigung liest, werden die Informationen immer übersichtlicher und übersichtlicher angezeigt.</span><span class="sxs-lookup"><span data-stu-id="45863-185">While the user is reading the notification, the information keeps getting displayed crisp and clear.</span></span> <span data-ttu-id="45863-186">Nach dem Lesen und Wegsehen von der Benachrichtigung wird die Benachrichtigung automatisch verworfen und ausgeblendet. Um all dies zu erreichen, gibt es einige generische Verhaltensskripts, die überhaupt nicht spezifisch für eye tracking sind, z. B.:</span><span class="sxs-lookup"><span data-stu-id="45863-186">After reading it and looking away from the notification, the notification will automatically be dismissed and fades out. To achieve all this, there are a few generic behavior scripts that are not specific to eye tracking at all, such as:</span></span>

- [`FaceUser`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FaceUser)
- [`ChangeSize`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ChangeSize)
- [`BlendOut`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.BlendOut)

<span data-ttu-id="45863-187">Der Vorteil dieses Ansatzes besteht darin, dass dieselben Skripts von verschiedenen Ereignissen wiederverwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="45863-187">The advantage of this approach is that the same scripts can be reused by various events.</span></span> <span data-ttu-id="45863-188">Ein Hologramm kann z. B. auf der Grundlage von Sprachbefehlen oder nach dem Drücken einer virtuellen Schaltfläche mit dem Benutzer beginnen.</span><span class="sxs-lookup"><span data-stu-id="45863-188">For example, a hologram may start facing the user based on a voice commands or after pressing a virtual button.</span></span> <span data-ttu-id="45863-189">Um diese Ereignisse auszulösen, können Sie einfach auf die Methoden verweisen, die in dem Skript ausgeführt werden [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) sollen, das an Ihr GameObject angefügt ist.</span><span class="sxs-lookup"><span data-stu-id="45863-189">To trigger these events, you can simply reference the methods that should be executed in the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script that is attached to your GameObject.</span></span>

<span data-ttu-id="45863-190">Für das Beispiel der _"intelligenten Benachrichtigungen"_ geschieht Folgendes:</span><span class="sxs-lookup"><span data-stu-id="45863-190">For the example of the _'smart attentive notifications'_, the following happens:</span></span>

- <span data-ttu-id="45863-191">**OnLookAtStart()**: Die Benachrichtigung beginnt mit...</span><span class="sxs-lookup"><span data-stu-id="45863-191">**OnLookAtStart()**: The notification starts to...</span></span>
  - <span data-ttu-id="45863-192">*FaceUser.Engage:* ... wenden Sie sich an den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="45863-192">*FaceUser.Engage:* ... turn toward the user.</span></span>
  - <span data-ttu-id="45863-193">*ChangeSize.Engage:* ... Vergrößern _(bis zu einer angegebenen maximalen Skala)_.</span><span class="sxs-lookup"><span data-stu-id="45863-193">*ChangeSize.Engage:* ... increase in size _(up to a specified maximum scale)_.</span></span>
  - <span data-ttu-id="45863-194">*BlendOut.Engage:* ... beginnt, mehr zu mischen _(nachdem sie sich in einem dezenteren Leerlaufzustand befinden)_.</span><span class="sxs-lookup"><span data-stu-id="45863-194">*BlendOut.Engage:* ... starts to blend in more _(after being at a more subtle idle state)_.</span></span>  

- <span data-ttu-id="45863-195">**OnDwell():** Informiert das _BlendOut-Skript_ darüber, dass die Benachrichtigung ausreichend untersucht wurde.</span><span class="sxs-lookup"><span data-stu-id="45863-195">**OnDwell()**: Informs the _BlendOut_ script that the notification has been looked at sufficiently.</span></span>

- <span data-ttu-id="45863-196">**OnLookAway():** Die Benachrichtigung beginnt mit...</span><span class="sxs-lookup"><span data-stu-id="45863-196">**OnLookAway()**: The notification starts to...</span></span>
  - <span data-ttu-id="45863-197">*FaceUser.Disengage:* ... Kehren Sie zur ursprünglichen Ausrichtung zurück.</span><span class="sxs-lookup"><span data-stu-id="45863-197">*FaceUser.Disengage:* ... turn back to its original orientation.</span></span>
  - <span data-ttu-id="45863-198">*ChangeSize.Disengage:* ... Verringern Sie wieder auf die ursprüngliche Größe.</span><span class="sxs-lookup"><span data-stu-id="45863-198">*ChangeSize.Disengage:* ... decrease back to its original size.</span></span>
  - <span data-ttu-id="45863-199">*BlendOut.Disengage:* ... beginnt mit dem Ausblenden: Wenn _OnDwell()_ ausgelöst wurde, blenden Sie vollständig aus, und zerstören Sie es, andernfalls wieder in den Leerlaufzustand zurück.</span><span class="sxs-lookup"><span data-stu-id="45863-199">*BlendOut.Disengage:* ... starts to blend out - If _OnDwell()_ was triggered, blend out completely and destroy, otherwise back to its idle state.</span></span>

<span data-ttu-id="45863-200">**Entwurfsüberlegung:** Der Schlüssel zu einer ansprechenden Erfahrung besteht darin, die Geschwindigkeit jedes dieser Verhaltensweisen sorgfältig zu optimieren, um zu vermeiden, dass es zu Störungen führt, indem sie ständig zu schnell auf die Blicke des Benutzers reagieren.</span><span class="sxs-lookup"><span data-stu-id="45863-200">**Design consideration:** The key to an enjoyable experience here is to carefully tune the speed of any of these behaviors to avoid causing discomfort by reacting to the user’s eye gaze too quickly all the time.</span></span>
<span data-ttu-id="45863-201">Andernfalls kann dies schnell extrem überwältigend wirken.</span><span class="sxs-lookup"><span data-stu-id="45863-201">Otherwise this can quickly feel extremely overwhelming.</span></span>

<img src="../../images/eye-tracking/mrtk_et_EyeTrackingTarget_Notification.jpg" width="750" alt="Target Notification">

### <a name="example-2-holographic-gem-rotates-slowly-when-looking-at-it"></a><span data-ttu-id="45863-202">Beispiel #2: Holografisches Gem wird beim Betrachten langsam gedreht</span><span class="sxs-lookup"><span data-stu-id="45863-202">Example #2: Holographic gem rotates slowly when looking at it</span></span>

<span data-ttu-id="45863-203">Ähnlich wie bei beispiel #1 können wir einfach ein Hoverfeedback für unsere holografischen Gems in `EyeTrackingDemo-02-TargetSelection` der Szene (Assets/MRTK/Examples/Demos/EyeTracking/Scenes) erstellen, die sich langsam in konstanter Richtung und mit konstanter Geschwindigkeit (im Gegensatz zum Obigen Drehungsbeispiel) drehen, wenn wir uns ansehen.</span><span class="sxs-lookup"><span data-stu-id="45863-203">Similar to Example #1, we can easily create a hover feedback for our holographic gems in `EyeTrackingDemo-02-TargetSelection` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes) scene that will slowly rotate in a constant direction and at a constant speed (in contrast to the rotation example from above) when being looked at.</span></span> <span data-ttu-id="45863-204">Sie müssen lediglich die Drehung des holografischen Gem aus dem _WhileLookingAtTarget()-Ereignis_ von _EyeTrackingTarget_ auslösen.</span><span class="sxs-lookup"><span data-stu-id="45863-204">All you need is to trigger the rotation of the holographic gem from the _EyeTrackingTarget_'s _WhileLookingAtTarget()_ event.</span></span> <span data-ttu-id="45863-205">Im Anschluss finden Sie einige weitere Details:</span><span class="sxs-lookup"><span data-stu-id="45863-205">Here are a few more details:</span></span>

1. <span data-ttu-id="45863-206">Erstellen Sie ein generisches Skript, das eine öffentliche Funktion zum Drehen des GameObject enthält, an das es angefügt ist.</span><span class="sxs-lookup"><span data-stu-id="45863-206">Create a generic script that includes a public function to rotate the GameObject it is attached to.</span></span> <span data-ttu-id="45863-207">Im Folgenden finden Sie ein Beispiel aus _RotateWithConstSpeedDir.cs,_ in dem wir die Drehrichtung und Geschwindigkeit im Unity-Editor optimieren können.</span><span class="sxs-lookup"><span data-stu-id="45863-207">Below is an example from _RotateWithConstSpeedDir.cs_ where we can tweak the rotation direction and speed from the Unity Editor.</span></span>

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

1. <span data-ttu-id="45863-208">Fügen Sie das Skript ihrem Ziel-GameObject hinzu, und verweisen Sie im UnityEvent-Trigger wie im folgenden Screenshot gezeigt [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) auf die _RotateTarget()-Funktion:_</span><span class="sxs-lookup"><span data-stu-id="45863-208">Add the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script to your target GameObject and reference the _RotateTarget()_ function in the UnityEvent trigger as shown the screenshot below:</span></span>

    ![EyeTrackingTarget-Beispiel](../../images/eye-tracking/mrtk_et_EyeTrackingTargetSample.jpg)

### <a name="example-3-pop-those-gems-aka-_multi-modal-eye-gaze-supported-target-selection_"></a><span data-ttu-id="45863-210">Beispiel #3: Pop those gems aka _multi-modal eye-gaze-supported target selection_</span><span class="sxs-lookup"><span data-stu-id="45863-210">Example #3: Pop those gems aka _multi-modal eye-gaze-supported target selection_</span></span>

<span data-ttu-id="45863-211">Im vorherigen Beispiel haben wir gezeigt, wie einfach es ist, zu erkennen, ob ein Ziel angezeigt wird und wie eine Reaktion darauf ausgelöst werden kann.</span><span class="sxs-lookup"><span data-stu-id="45863-211">In the previous example, we have shown how easy it is to detect whether a target is looked at and how to trigger a reaction to that.</span></span> <span data-ttu-id="45863-212">Als Nächstes lassen Sie die Gems mithilfe des _OnSelected()-Ereignisses_ aus explodieren. [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget)</span><span class="sxs-lookup"><span data-stu-id="45863-212">Next, let's make the gems explode using the _OnSelected()_ event from the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget).</span></span> <span data-ttu-id="45863-213">Der interessante Teil *ist, wie* die Auswahl ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="45863-213">The interesting part is *how* the selection is triggered.</span></span> <span data-ttu-id="45863-214">Ermöglicht [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) das schnelle Zuweisen verschiedener Methoden zum Aufrufen einer Auswahl:</span><span class="sxs-lookup"><span data-stu-id="45863-214">The [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) allows for quickly assigning different ways to invoke a selection:</span></span>

- <span data-ttu-id="45863-215">_Geste zum Anheften:_ Wenn Sie "Aktion auswählen" auf "Auswählen" festlegen, wird die Standardhandgeste verwendet, um die Auswahl auszulösen.</span><span class="sxs-lookup"><span data-stu-id="45863-215">_Pinch gesture_: Setting the 'Select Action' to 'Select' uses the default hand gesture to trigger the selection.</span></span>
<span data-ttu-id="45863-216">Dies bedeutet, dass der Benutzer einfach seine Hand erhöhen und den Daumen und den Zeigefinger zusammendrippen kann, um die Auswahl zu bestätigen.</span><span class="sxs-lookup"><span data-stu-id="45863-216">This means that the user can simply raise their hand and pinch their thumb and index finger together to confirm the selection.</span></span>

- <span data-ttu-id="45863-217">Sagen _Sie "Auswählen":_ Verwenden Sie den Standardstimmenbefehl _"Auswählen",_ um ein Hologramm auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="45863-217">Say _"Select"_: Use the default voice command _"Select"_ for selecting a hologram.</span></span>

- <span data-ttu-id="45863-218">Sagen _Sie "Explode"_ oder _"Pop":_ Um benutzerdefinierte Sprachbefehle zu verwenden, müssen Sie zwei Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="45863-218">Say _"Explode"_ or _"Pop"_: To use custom voice commands, you need to follow two steps:</span></span>
    1. <span data-ttu-id="45863-219">Einrichten einer benutzerdefinierten Aktion wie _"DestroyTarget"_</span><span class="sxs-lookup"><span data-stu-id="45863-219">Set up a custom action such as _"DestroyTarget"_</span></span>
        - <span data-ttu-id="45863-220">Navigieren Sie zu _MRTK -> Input -> Input Actions_</span><span class="sxs-lookup"><span data-stu-id="45863-220">Navigate to _MRTK -> Input -> Input Actions_</span></span>
        - <span data-ttu-id="45863-221">Klicken Sie auf "Neue Aktion hinzufügen".</span><span class="sxs-lookup"><span data-stu-id="45863-221">Click "Add a new action"</span></span>

    2. <span data-ttu-id="45863-222">Richten Sie die Sprachbefehle ein, die diese Aktion auslösen, z. _B. "Explode"_ oder _"Pop"._</span><span class="sxs-lookup"><span data-stu-id="45863-222">Set up the voice commands that trigger this action such as _"Explode"_ or _"Pop"_</span></span>
        - <span data-ttu-id="45863-223">Navigieren Sie _zu MRTK -> Input -> Speech._</span><span class="sxs-lookup"><span data-stu-id="45863-223">Navigate to _MRTK -> Input -> Speech_</span></span>
        - <span data-ttu-id="45863-224">Klicken Sie auf "Neuen Sprachbefehl hinzufügen".</span><span class="sxs-lookup"><span data-stu-id="45863-224">Click "Add a new speech command"</span></span>
            - <span data-ttu-id="45863-225">Zuordnen der aktion, die Sie gerade erstellt haben</span><span class="sxs-lookup"><span data-stu-id="45863-225">Associate the action you just created</span></span>
            - <span data-ttu-id="45863-226">Weisen Sie einen _KeyCode zu,_ um das Auslösen der Aktion über einen Schaltflächendruck zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="45863-226">Assign a _KeyCode_ to allow for triggering the action via a button press</span></span>

![EyeTrackingTarget-Beispiel für Sprachbefehle](../../images/eye-tracking/mrtk_et_voicecmdsample.jpg)

<span data-ttu-id="45863-228">Wenn ein Gem ausgewählt wird, explodiert es, sodass ein Sound entsteht und verschwindet.</span><span class="sxs-lookup"><span data-stu-id="45863-228">When a gem is selected it will explode, making a sound and disappear.</span></span> <span data-ttu-id="45863-229">Dies wird vom [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) Skript behandelt.</span><span class="sxs-lookup"><span data-stu-id="45863-229">This is handled by the [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script.</span></span> <span data-ttu-id="45863-230">Sie haben zwei Möglichkeiten:</span><span class="sxs-lookup"><span data-stu-id="45863-230">You have two options:</span></span>

- <span data-ttu-id="45863-231">**Im Unity-Editor:** Sie können das Skript, das an jede unserer Gem-Vorlagen angefügt ist, einfach mit dem Unity-Ereignis OnSelected() im Unity-Editor verknüpfen.</span><span class="sxs-lookup"><span data-stu-id="45863-231">**In the Unity Editor:** You could simply link the script that is attached to each of our gem templates to the OnSelected() Unity event in the Unity Editor.</span></span>
- <span data-ttu-id="45863-232">**In code:** If you don't want to drag and drop GameObjects around, you can also simply add a event listener directly to your script.</span><span class="sxs-lookup"><span data-stu-id="45863-232">**In code:** If you don't want to drag and drop GameObjects around, you can also simply add a event listener directly to your script.</span></span>  
<span data-ttu-id="45863-233">Hier sehen Sie ein Beispiel dafür, wie wir dies im Skript gemacht [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) haben:</span><span class="sxs-lookup"><span data-stu-id="45863-233">Here's an example from how we did it in the [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script:</span></span>

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

### <a name="example-4-use-hand-rays-and-eye-gaze-input-together"></a><span data-ttu-id="45863-234">Beispiel #4: Gemeinsames Verwenden von Handlicht- und Anvisierteneingaben mit den Augen</span><span class="sxs-lookup"><span data-stu-id="45863-234">Example #4: Use hand rays and eye gaze input together</span></span>

<span data-ttu-id="45863-235">Handlichter haben Vorrang vor dem Anvisieren mit dem Kopf und den Augen.</span><span class="sxs-lookup"><span data-stu-id="45863-235">Hand rays take priority over head and eye gaze targeting.</span></span> <span data-ttu-id="45863-236">Dies bedeutet, dass der Handstrahl als primärer Zeiger fungiert, wenn Handlichtlicht aktiviert ist, sobald die Hände angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="45863-236">This means, if hand rays are enabled, the moment the hands come into view, the hand ray will act as the primary pointer.</span></span>
<span data-ttu-id="45863-237">Es kann jedoch Situationen geben, in denen Sie Handstrahl verwenden möchten, während Sie dennoch erkennen, ob ein Benutzer ein bestimmtes Hologramm ansieht.</span><span class="sxs-lookup"><span data-stu-id="45863-237">However, there might be situations in which you want to use hand rays while still detecting whether a user is looking at a certain hologram.</span></span> <span data-ttu-id="45863-238">Kein Problem!</span><span class="sxs-lookup"><span data-stu-id="45863-238">Easy!</span></span> <span data-ttu-id="45863-239">Im Wesentlichen sind zwei Schritte erforderlich:</span><span class="sxs-lookup"><span data-stu-id="45863-239">Essentially you require two steps:</span></span>

<span data-ttu-id="45863-240">**1. Aktivieren des Handstrahls:** Um den Handstrahl zu aktivieren, wechseln Sie zu _Mixed Reality Toolkit -> Input -> Pointers_.</span><span class="sxs-lookup"><span data-stu-id="45863-240">**1. Enable the hand ray:** To enable the hand ray, go to _Mixed Reality Toolkit -> Input -> Pointers_.</span></span>
<span data-ttu-id="45863-241">Im _EyeTrackingDemo-00-RootScene,_ in dem das Mixed Reality Toolkit einmal für alle Eyetracking-Demoszenen konfiguriert ist, sollte _eyeTrackingDemoPointerProfile_ angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="45863-241">In the _EyeTrackingDemo-00-RootScene_ where the Mixed Reality Toolkit is configured once for all of the eye tracking demo scenes, you should see the _EyeTrackingDemoPointerProfile_.</span></span>
<span data-ttu-id="45863-242">Sie können entweder ein neues _Eingabeprofil_ von Grund auf neu erstellen oder das aktuelle Eyetracking anpassen:</span><span class="sxs-lookup"><span data-stu-id="45863-242">You can either create a new _Input Profile_ from scratch or adapt the current eye tracking one:</span></span>

- <span data-ttu-id="45863-243">**Von Grund auf neu:** Wählen Sie auf der Registerkarte _Zeiger_ im Kontextmenü _defaultMixedRealityInputPointerProfile_ aus.</span><span class="sxs-lookup"><span data-stu-id="45863-243">**From scratch:** In the _Pointers_ tab, select the _DefaultMixedRealityInputPointerProfile_ from the context menu.</span></span>
<span data-ttu-id="45863-244">Dies ist das Standardzeigerprofil, für das der Handstrahl bereits aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="45863-244">This is the default pointer profile that already has the hand ray enabled!</span></span>
<span data-ttu-id="45863-245">Um den Standardcursor (einen nicht transparenten weißen Punkt) zu ändern, klonen Sie einfach das Profil, und erstellen Sie Ein eigenes benutzerdefiniertes Zeigerprofil.</span><span class="sxs-lookup"><span data-stu-id="45863-245">To change the default cursor (an opaque white dot), simply clone the profile and create your own custom pointer profile.</span></span>
<span data-ttu-id="45863-246">Ersetzen Sie dann _DefaultCursor_ durch _EyeGazeCursor_ unter _Gaze Cursor Prefab_.</span><span class="sxs-lookup"><span data-stu-id="45863-246">Then replace _DefaultCursor_ with _EyeGazeCursor_ under _Gaze Cursor Prefab_.</span></span>  
- <span data-ttu-id="45863-247">**Basierend auf dem vorhandenen _EyeTrackingDemoPointerProfile:_** Doppelklicken Sie auf _eyeTrackingDemoPointerProfile,_ und fügen Sie unter _Zeigeroptionen_ den folgenden Eintrag hinzu:</span><span class="sxs-lookup"><span data-stu-id="45863-247">**Based on the existing _EyeTrackingDemoPointerProfile_:** Double-click the _EyeTrackingDemoPointerProfile_ and add the following entry under _Pointer Options_:</span></span>
  - <span data-ttu-id="45863-248">**Controllertyp:** "Artikulierte Hand", "Windows Mixed Reality"</span><span class="sxs-lookup"><span data-stu-id="45863-248">**Controller Type:** 'Articulated Hand', 'Windows Mixed Reality'</span></span>
  - <span data-ttu-id="45863-249">**Übergabe:** jegliche</span><span class="sxs-lookup"><span data-stu-id="45863-249">**Handedness:** Any</span></span>
  - <span data-ttu-id="45863-250">**Zeiger-Prefab:** DefaultControllerPointer</span><span class="sxs-lookup"><span data-stu-id="45863-250">**Pointer Prefab:** DefaultControllerPointer</span></span>

<span data-ttu-id="45863-251">**2. Erkennen, dass** ein Hologramm angezeigt wird: Verwenden Sie das Skript, um die Erkennung zu ermöglichen, dass ein Hologramm wie oben [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) beschrieben angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="45863-251">**2. Detect that a hologram is looked at:** Use the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script to enable detecting that a hologram is looked at as described above.</span></span> <span data-ttu-id="45863-252">Sie können sich auch das Beispielskript zur Inspiration anschauen, da dies ein Hologramm zeigt, das auf das Anvieren mit den Augen folgt (z. B. ein Cursor), unabhängig davon, ob Handlichtlichter `FollowEyeGaze` aktiviert sind oder nicht.</span><span class="sxs-lookup"><span data-stu-id="45863-252">You can also take a look at the `FollowEyeGaze` sample script for inspiration as this is showing a hologram following your eye gaze (e.g., a cursor) whether hand rays are enabled or not.</span></span>

<span data-ttu-id="45863-253">Wenn Sie nun mit den Szenen der Eyetrackingdemo beginnen, sollten Sie einen Strahl sehen, der von Ihren Händen kommt.</span><span class="sxs-lookup"><span data-stu-id="45863-253">Now, when you start the eye tracking demo scenes, you should see a ray coming from your hands.</span></span>
<span data-ttu-id="45863-254">In der Demo zur Auswahl des Eyetrackingziels folgt der halbtransparente Kreis noch immer ihren Blickanviert, und die Gems reagieren darauf, ob sie anviert werden oder nicht, während die Menüschaltflächen der oberen Szene stattdessen den primären Eingabezeiger (Ihre Hände) verwenden.</span><span class="sxs-lookup"><span data-stu-id="45863-254">For example, in the eye tracking target selection demo, the semi-transparent circle is still following your eye gaze and the gems respond to whether they are looked at or not, while the top scene menu buttons use the primary input pointer (your hands) instead.</span></span>

---
[<span data-ttu-id="45863-255">Zurück zu "Eye tracking in the MixedRealityToolkit"</span><span class="sxs-lookup"><span data-stu-id="45863-255">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](eye-tracking-main.md)
