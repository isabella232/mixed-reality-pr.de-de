---
title: Motion-Controller in Unity
description: Erfahren Sie, wie Sie mit der Motion Controller-Eingabe mithilfe von XR und allgemeinen Schaltflächen-und Achsen-APIs Maßnahmen für Ihren Blick in Unity durchführen.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: Motion Controllers, Unity, Input, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, mrtk, Mixed Reality Toolkit
ms.openlocfilehash: db103e674a369f13e62aac5e8c0513b2c2c17f9e
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583508"
---
# <a name="motion-controllers-in-unity"></a>Motion-Controller in Unity

Es gibt zwei wichtige Möglichkeiten, um Ihre [Blicke in Unity](gaze-in-unity.md), [Handgesten](../../design/gaze-and-commit.md#composite-gestures) und [Bewegungs Controllern](../../design/motion-controllers.md) in hololens und immersiven HMD zu ergreifen. Sie greifen über dieselben APIs in Unity auf die Daten für beide Quellen räumlicher Eingaben zu.

Unity bietet zwei Hauptmethoden für den Zugriff auf räumliche Eingabedaten für Windows Mixed Reality. Die gängigen *Input. getbutton/Input. getaxis-* APIs funktionieren über mehrere Unity-XR-SDK hinweg, während die *interaktionmanager/GestureRecognizer* -API speziell für Windows Mixed Reality den vollständigen Satz räumlicher Eingabedaten verfügbar macht.

## <a name="unity-xr-input-apis"></a>Eingabe-APIs für Unity XR

Bei neuen Projekten wird die Verwendung der neuen XR-Eingabe-APIs von Anfang an empfohlen. 

Weitere Informationen zu den [XR-APIs](https://docs.unity3d.com/Manual/xr_input.html)finden Sie hier.

## <a name="unity-buttonaxis-mapping-table"></a>Unity-Schaltfläche/Achsen Zuordnung (Tabelle)

Der Eingabe-Manager von Unity für Windows Mixed Reality Motion Controllers unterstützt die unten aufgeführten Schaltflächen-und Achsen-IDs über die *Eingabe. getbutton/getaxis-* APIs. Die Spalte "Windows Mr-spezifisch" bezieht sich auf Eigenschaften, die vom *interaktionsourcestate* -Typ verfügbar sind. Jede dieser APIs wird in den folgenden Abschnitten ausführlich beschrieben.

Die Zuordnungen von Schaltflächen/Achsen-IDs für Windows Mixed Reality entsprechen im Allgemeinen den Oculus-Schaltflächen-/Achsen-IDs

Die Zuordnungen von Schaltflächen/Achsen-IDs für Windows Mixed Reality unterscheiden sich auf zwei Arten von den Zuordnungen von openvr:
1. Die Zuordnung verwendet Touchpad-IDs, die sich vom Finger Stick unterscheiden, um Controller mit beiden Fingerabdrücken und Touchpads zu unterstützen.
2. Durch die Zuordnung wird vermieden, dass die Schaltflächen-IDs A und X für die Menü Schaltflächen überladen werden, damit Sie für die physischen abxy-Schaltflächen

<table>
<tr>
<th rowspan="2">Eingabe </th><th colspan="2"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Allgemeine Unity-APIs</a><br />(Input. getbutton/getaxis) </th><th rowspan="2"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">Windows-spezifische Eingabe-API</a><br />XR. WSA. Der</th>
</tr><tr>
<th> Links </th><th> Rechte Seite</th>
</tr><tr>
<td> Select-Taste gedrückt </td><td> Achse 9 = 1,0 </td><td> Achse 10 = 1,0 </td><td> selectpressed</td>
</tr><tr>
<td> Auswählen des analogen Auslöse Werts </td><td> Achse 9 </td><td> Achse 10 </td><td> selectpressedamount</td>
</tr><tr>
<td> Select-Taste teilweise gedrückt </td><td> Schaltfläche 14 <i>(Gamepad-Kompatibilität)</i> </td><td> Schaltfläche 15 <i>(Gamepad-Kompatibilität)</i> </td><td> selectpressedamount &gt; 0,0</td>
</tr><tr>
<td> Menü Schaltfläche gedrückt </td><td> Schaltfläche 6 * </td><td> Schaltfläche 7 * </td><td> menupressed</td>
</tr><tr>
<td> Zieh Schaltfläche gedrückt </td><td> Achse 11 = 1,0 (keine analogen Werte)<br />Schaltfläche 4 <i>(Gamepad-Kompatibilität)</i> </td><td> Achse 12 = 1,0 (keine analogen Werte)<br />Schaltfläche 5 <i>(Gamepad-Kompatibilität)</i> </td><td> Schna</td>
</tr><tr>
<td> Thumbstick X <i>(Links:-1,0, right: 1,0)</i> </td><td> Achse 1 </td><td> Achse 4 </td><td> thumbstickposition. x</td>
</tr><tr>
<td> Thumbstick Y <i>(oben:-1,0, unten: 1,0)</i> </td><td> Achse 2 </td><td> Achse 5 </td><td> thumbstickposition. y</td>
</tr><tr>
<td> Thumbstick gedrückt </td><td> Schaltfläche 8 </td><td> Schaltfläche 9 </td><td> thumbstickpressed</td>
</tr><tr>
<td> Touchpad X <i>(Links:-1,0, right: 1,0)</i> </td><td> Achse 17 * </td><td> Achse 19 * </td><td> touchpadposition. x</td>
</tr><tr>
<td> Touchpad Y <i>(oben:-1,0, unten: 1,0)</i> </td><td> Achse 18 * </td><td> Achse 20 * </td><td> touchpadposition. y</td>
</tr><tr>
<td> Touchpad berührt </td><td> Schaltfläche 18 * </td><td> Schaltfläche 19 * </td><td> touchpadtouched</td>
</tr><tr>
<td> Touchpad gedrückt </td><td> Schaltfläche 16 * </td><td> Schaltfläche 17 * </td><td> touchpadpressed</td>
</tr><tr>
<td> 6DOF-Zieh Punkt Pose oder Zeiger Pose </td><td colspan="2"> <i></i> Nur Ziehpunkt: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. Inputtracking. getlocalposition</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR. Input Tracking. getlocalrotation</a></td><td> Pass <i>-</i> oder <i>Zeiger</i> als Argument: SourceState. sourcepose. trygetposition<br />SourceState. sourcepose. trygetrotation<br /></td>
</tr><tr>
<td> Nach verfolgungsstatus </td><td colspan="2"> <i>Die Positionsgenauigkeit und das Risiko von Quell Verlusten sind nur über die Mr-spezifische API verfügbar.</i> </td><td> <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">SourceState. sourcepose. positionaccuracy</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">SourceState. Properties. sourcelossrisk</a></td>
</tr>
</table>

>[!NOTE]
>Diese Schaltflächen-/Achsen-IDs unterscheiden sich von den IDs, die Unity für openvr verwendet, aufgrund von Konflikten in den von Gamepads, oculus Touchscreen und openvr verwendeten Zuordnungen.

<!-- ### Using HP Reverb G2 controllers

If you're using the HP Reverb G2 controllers, refer to the table below for button and axis IDs.

<table>
<tr>
<th rowspan="2"><a href="https://docs.unity3d.com/ScriptReference/XR.CommonUsages.html">Input </th><th colspan="2">Common Unity APIs</a><br />(Input.GetButton/GetAxis) </th><th rowspan="2">HP Reverb G2 Input API</a></th>
</tr><tr>
<th> Left hand </th><th> Right hand</th>
</tr><tr>
<td> Primary2DAxis </td><td> Axis 1 (X) / Axis 2 (Y) </td><td> Axis 4 (X) / Axis 5(Y) </td><td> Thumbstick</td>
</tr><tr>
<td> Trigger pressed </td><td> Axis 9 </td><td> Axis 10 </td><td> Index trigger</td>
</tr><tr>
<td> Grip </td><td> Axis 11d </td><td> Axis 12 </td><td> Grip trigger</td>
</tr><tr>
<td> PrimaryButton pressed </td><td> Button 2 </td><td> Button 0 </td><td> Menu button pressed</td>
</tr><tr>
<td> SecondaryButton pressed </td><td> Button 3 </td><td> Button 1 </td><td> A/X button</td>
</tr><tr>
<td> GripButton </td><td> Button 4 </td><td> Button 5 </td><td> Grip trigger</td>
</tr><tr>
<td> TriggerButton </td><td> Button 14 </td><td> Button 15 </td><td> Index trigger</td>
</tr><tr>
</tr>
</table> -->


## <a name="grip-pose-vs-pointing-pose"></a>Ziehpunkt im Vergleich zu Zeige darstellen

Windows Mixed Reality unterstützt Bewegungs Controller in einer Vielzahl von Formfaktoren. Der Entwurf eines Controllers unterscheidet sich in seiner Beziehung zwischen der Handposition des Benutzers und der natürlichen Vorwärtsrichtung, die apps zum zeigen beim Rendern des Controllers verwenden sollten.

Um diese Controller besser darzustellen, gibt es zwei Arten von Posen, die Sie für jede Interaktions Quelle untersuchen können, die Ziehpunkt- **und die** **Zeiger** Darstellung. Sowohl die Ziehpunkt-als auch die zeigerpose-Koordinaten werden von allen Unity-APIs in globalen Unity-Weltkoordinaten ausgedrückt.

### <a name="grip-pose"></a>Ziehpunkt darstellen

Der Ziehpunkt stellt den Speicherort der Benutzer- **Palm dar,** der entweder von einem hololens oder einem Bewegungs Controller erkannt wird.

Bei immersiven Headsets wird die Zieh Punkt Darstellung am besten zum Rendering **der Benutzer Hand** oder eines Objekts verwendet, das **in der Hand des Benutzers gespeichert** ist. Die Zieh Punkt Darstellung wird auch bei der Visualisierung eines Bewegungs Controllers verwendet. Das **zum Rendern-Modell** , das von Windows für einen Motion-Controller bereitgestellt wird, verwendet die Zieh Punkt Pose als Ursprung und Mittelpunkt der Drehung.

Die Ziehpunkt-Pose wird wie folgt definiert:
* Die Zieh **Punktposition**: der Palmen Schwerpunkt bei der natürlichen Aufbewahrung des Controllers, nach links oder rechts, um die Position im Ziehpunkt zu zentrieren. Auf dem Windows Mixed Reality Motion Controller richtet sich diese Position im Allgemeinen nach der Schaltfläche "verstehen".
* Die **Rechte Achse** der Ziehpunkt Ausrichtung: Wenn Sie Ihre Hand vollständig geöffnet haben, um eine flache 5-Finger-Darstellung zu bilden, ist das Strahl-Ray, das normal ist (vorwärts von links nach links, rückwärts von rechter Palme).
* Die **Forward-Achse** der Ziehpunkt Ausrichtung: Wenn Sie die Hand teilweise schließen (wie beim Halten des Controllers), wird der Strahl, der durch das durch ihre nicht-Thumb-Finger formatierte Rohr auf "Vorwärts" zeigt.
* Die **aufwärts Achse** der Ziehpunkt Ausrichtung: die aufwärts Achse, die durch die Rechte-und vorwärts Definitionen impliziert wird.

Sie können auf die Ziehpunkt-Pose über die Anbieter übergreifende Eingabe-API von Unity (XR) zugreifen *[. Inputtracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). Getlocalposition/Rotation*) oder über die Windows-spezifische API (*SourceState. sourcepose. trygetposition/Rotation*), die die Daten für den **Zieh Knoten** anfordert.

### <a name="pointer-pose"></a>Zeiger Pose

Die **Zeiger** Darstellung stellt die Spitze des Controllers dar, der vorwärts zeigt.

Die vom System bereitgestellte Zeiger Darstellung eignet sich am besten für raycast, wenn Sie **das Controller Modell selbst Rendern**. Wenn Sie ein anderes virtuelles Objekt anstelle des Controllers (z. b. eine virtuelle Pistole) rendern, sollten Sie auf einen Strahl zeigen, der für das virtuelle Objekt am natürlichsten ist, z. b. ein Strahl, der auf dem Barrel des App-defined Gun-Modells verläuft. Da Benutzer das virtuelle Objekt und nicht den physischen Controller sehen können, ist das verweisen mit dem virtuellen Objekt für diejenigen, die Ihre APP verwenden, wahrscheinlich natürlicher.

Derzeit ist die Zeiger Pose in Unity nur über die Windows Mr-spezifische API, *SourceState. sourcepose. trygetposition/Rotation* verfügbar, wobei *interaktionsourcenode. Pointer* als Argument übergeben wird.

## <a name="controller-tracking-state"></a>Controller nach verfolgungsstatus

Wie bei den Headsets ist für Windows Mixed Reality Motion Controller das Einrichten externer nach Verfolgungs Sensoren nicht erforderlich. Stattdessen werden die Controller von Sensoren im Headset selbst nachverfolgt.

Wenn der Benutzer die Controller aus der Ansicht des Dashboards verschiebt, werden die Controller Positionen in den meisten Fällen von Windows weiter abgeleitet. Wenn die visuelle Überwachung für den Controller lange genug verloren gegangen ist, werden die Positionen des Controllers auf Positionen mit ungefähren Genauigkeit abgelegt.

An diesem Punkt sperrt das System den Controller für den Benutzer, wobei die Position des Benutzers nachverfolgt wird, während er sich bewegt, während er weiterhin die echte Ausrichtung des Controllers mithilfe der internen Ausrichtungs Sensoren verfügbar macht. Viele apps, die Controller verwenden, um auf Benutzeroberflächen Elemente zu verweisen und diese zu aktivieren, können normal funktionieren, ohne dass der Benutzer das merkt.

Die beste Möglichkeit, dies zu erreichen, besteht darin, es selbst auszuprobieren. Sehen Sie sich dieses Video mit Beispielen für den immersiven Inhalt an, der mit Motion-Controllern über verschiedene Überwachungs Zustände hinweg funktioniert:

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a>Grund für die explizite Nachverfolgung des Zustands

Apps, die Positionen basierend auf dem nach verfolgungsstatus unterschiedlich behandeln möchten, können weiter gehen und die Eigenschaften des Controller Zustands überprüfen, z. b. *sourcelossrisk* und *positionaccuracy*:

<table>
<tr>
<th> Nach verfolgungsstatus </th><th> Sourcelossrisk </th><th> Positionsgenauigkeit </th><th> Trygetposition</th>
</tr><tr>
<td> <b>Hohe Genauigkeit</b> </td><td style="background-color: green; color: white"> &lt; 1,0 </td><td style="background-color: green; color: white"> High </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Hohe Genauigkeit (Risiko eines Verlusts)</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: green; color: white"> High </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Ungefähre Genauigkeit</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: orange"> Ungefähr </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Keine Position</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: orange"> Ungefähr </td><td style="background-color: orange"> false</td>
</tr>
</table>

Diese Motion Controller-Überwachungs Zustände werden wie folgt definiert:
* **Hohe Genauigkeit:** Während sich der Motion-Controller in der Ansicht des Dashboards befindet, stellt er im Allgemeinen hohe Genauigkeits Positionen auf der Grundlage der visuellen Nachverfolgung bereit. Ein beweglicher Controller, der das Sichtfeld vorübergehend verlässt oder vorübergehend von den Headset-Sensoren (z. b. durch die andere Seite des Benutzers) verdeckt wird, gibt weiterhin hohe Genauigkeit für kurze Zeit zurück, basierend auf der Trägheits Verfolgung des Controllers.
* **Hohe Genauigkeit (Risiko des Verlusts):** Wenn der Benutzer den Bewegungs Controller über den Rand des Felds der Ansicht bewegt, kann das Headset die Position des Controllers in Kürze nicht visuell nachverfolgen. Die APP weiß, wann der Controller diese FOV-Grenze erreicht hat, indem er den **sourcelossrisk** -REACH-1,0 sieht. An diesem Punkt kann die APP die Controller Gesten anhalten, die einen stabilen Stream von qualitativ hochwertigen Posen erfordern.
* **Ungefähre Genauigkeit:** Wenn die visuelle Überwachung für den Controller lange genug verloren gegangen ist, werden die Positionen des Controllers auf Positionen mit ungefähren Genauigkeit abgelegt. An diesem Punkt sperrt das System den Controller für den Benutzer, wobei die Position des Benutzers nachverfolgt wird, während er sich bewegt, während er weiterhin die echte Ausrichtung des Controllers mithilfe der internen Ausrichtungs Sensoren verfügbar macht. Viele apps, die Controller verwenden, um auf Benutzeroberflächen Elemente zu verweisen und diese zu aktivieren, können so normal agieren, dass Sie in der ungefähren Genauigkeit nicht bemerkt werden Bei apps mit schwereren Eingabe Anforderungen ist es möglicherweise sinnvoll, diesen Löschvorgang von **hoher** Genauigkeit zur **ungefähren** Genauigkeit zu verstehen, indem die **positionaccuracy** -Eigenschaft überprüft wird, z. b. um dem Benutzer während dieses Zeitraums eine eher großzügigere Position in den offscreenzielen zu geben.
* **Keine Position:** Wenngleich der Controller für einen längeren Zeitraum mit der ungefähren Genauigkeit arbeiten kann, weiß das System manchmal, dass auch eine durch den Text gesperrten Position nicht sinnvoll ist. Beispielsweise kann ein Controller, der eingeschaltet wurde, nie visuell beobachtet werden, oder ein Benutzer kann einen Controller ablegen, der dann von einer anderen Person abgerufen wird. Zu diesen Zeitpunkten stellt das System keine Position für die APP bereit, und *trygetposition* gibt false zurück.

## <a name="common-unity-apis-inputgetbuttongetaxis"></a>Allgemeine Unity-APIs (Input. getbutton/getaxis)

**Namespace:** *unityengine*, *unityengine. XR*<br>
**Typen**: *Input*, *XR. Inputtracking*

Unity verwendet derzeit die allgemeinen *Input. getbutton/Input. getaxis-* APIs, um Eingaben für [das Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [das openvr SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) und Windows Mixed Reality, einschließlich der Hands-und Motion-Controller, verfügbar zu machen. Wenn Ihre APP diese APIs für die Eingabe verwendet, kann Sie Bewegungs Controller über mehrere XR-sdche hinweg unterstützen, einschließlich Windows Mixed Reality.

### <a name="getting-a-logical-buttons-pressed-state"></a>Der gedrückte Zustand einer logischen Schaltfläche wird erhalten.

Wenn Sie die allgemeinen Unity-Eingabe-APIs verwenden möchten, beginnen Sie in der Regel mit dem Verknüpfen von Schaltflächen und Achsen mit logischen Namen im [Unity-Eingabe-Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), und binden Sie eine Schaltfläche oder eine Achsen-ID an jeden Namen Anschließend können Sie Code schreiben, der auf den Namen der logischen Schaltfläche/Achse verweist.

Um z. b. die triggerschaltfläche des linken Bewegungs Controllers der Aktion senden zuzuordnen, wechseln Sie zu **Edit > Project Settings > Input** in Unity, und erweitern Sie die Eigenschaften des Abschnitts übermitteln unter Achsen. Ändern Sie die Schaltfläche **positiv** oder **alt positive Schaltfläche** , um die Schaltfläche "Taste **14**" wie folgt zu lesen:

![InputManager von Unity](images/unity-input-manager.png)<br>
*Unity-InputManager*

Das Skript kann dann mithilfe von " *Input. getbutton*" die Aktion "Senden" überprüfen:

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
Sie können weitere logische Schaltflächen hinzufügen, indem Sie die **size** -Eigenschaft unter **Achsen** ändern.

### <a name="getting-a-physical-buttons-pressed-state-directly"></a>Direktes drücken des gedrückten Zustands einer physischen Schaltfläche

Sie können mithilfe von *Input. GetKey* auch manuell mit dem voll qualifizierten Namen auf Schaltflächen zugreifen:

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a>Die Pose eines Hand-oder Bewegungs Controllers

Sie können auf die Position und Drehung des Controllers mithilfe von *XR zugreifen. Inputtracking*:

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

> [!NOTE] 
> Der obige Code stellt die Zieh Punktposition des Controllers dar (in der der Benutzer den Controller hält). Dies ist nützlich, um ein Schwert oder eine Waffe in der Hand des Benutzers oder ein Modell des Controllers selbst zu rendern.
> 
> Die Beziehung zwischen diesem Ziehpunkt und der Zeiger Pose (bei der die Spitze des Controllers zeigt) kann sich zwischen Controllern unterscheiden. Zurzeit ist der Zugriff auf die Zeiger-Pose des Controllers nur über die in den folgenden Abschnitten beschriebene Mr-spezifische Eingabe-API möglich.

## <a name="windows-specific-apis-xrwsainput"></a>Windows-spezifische APIs (XR. WSA. Der

> [!CAUTION]
> , Wenn Ihr Projekt einen der XR-verwendet. WSA-APIs werden nach dem XR SDK in zukünftigen Unity-Releases eingestellt. Für neue Projekte wird empfohlen, das XR SDK von Anfang an zu verwenden. Weitere Informationen zum [XR-Eingabe System und](https://docs.unity3d.com/Manual/xr_input.html)zu den APIs finden Sie hier.

**Namespace:** *unityengine. XR. WSA. Input*<br>
**Typen**: *interaktionsmanager*, *interaktionsourcestate*, *interaktionsource*, *interaktionsourceproperties*, *interaktionsourcekind*, *interaktionsourcelokation*

Um ausführlichere Informationen zu Windows Mixed Reality-Hand Eingaben (für hololens) und Bewegungs Controller zu erhalten, können Sie die Windows-spezifischen räumlichen Eingabe-APIs im Namespace *unityengine. XR. WSA. Input* verwenden. Auf diese Weise können Sie auf zusätzliche Informationen zugreifen, wie z. b. Die Positionsgenauigkeit oder die quellart, sodass Sie die Hände und Controller voneinander trennen können.

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a>Abrufen des Zustands von Händen und Bewegungs Controllern

Sie können den Status dieses Frames für jede Interaktions Quelle (Hand-oder Bewegungs Controller) mithilfe der *getcurrentreading* -Methode abrufen.

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

Jedes *interaktionsourcestate* , das Sie zurückerhalten, stellt eine Interaktions Quelle zum aktuellen Zeitpunkt dar. Das *interaktionsourcestate* macht Informationen wie z. b.:
* Welche [Arten von Druck](../../design/motion-controllers.md) vorgehungen werden auftreten (Select/Menu/grasp/Touchpad/Thumbstick)

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* Andere Daten, die für Bewegungs Controller spezifisch sind, z. b. die XY-Koordinaten des Touchpads und/oder Finger Ansichts Status

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```

* Interaktionsourcekind, um zu wissen, ob es sich bei der Quelle um einen Hand-oder Bewegungs Controller handelt

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a>Abrufen von vorwärts vorhergesagten Renderingvorgängen

* Beim Abrufen von Interaktions Quelldaten von Hand und Controllern sind die von Ihnen abzurufenden Datenquellen für den Zeitpunkt, zu dem die Daten des Bilds den Augen des Benutzers erreichen, von vorne vorhergesagte Posen.  Vorwärts vorhersagende Posen werden am besten zum **Rendern** des Controllers oder eines gehaltenen Objekts in jedem Frame verwendet.  Wenn Sie ein bestimmtes Press-oder-Release mit dem Controller als Ziel verwenden, wird dies am genauesten sein, wenn Sie die unten beschriebenen Vergangenheits Ereignis-APIs verwenden.

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* Sie können auch die vorwärts Gesagte Kopfzeile für diesen aktuellen Frame erhalten.  Wie bei der Quell Darstellung ist dies für das **Rendern** eines Cursors nützlich, obwohl das Ziel einer bestimmten Presse oder Freigabe am genauesten ist, wenn Sie die unten beschriebenen Vergangenheits Ereignis-APIs verwenden.

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a>Behandeln von Interaktions Quell Ereignissen

Um Eingabeereignisse zu behandeln, wie Sie mit Ihren exakten Vergangenheits Daten auftreten, können Sie Interaktions Quell Ereignisse behandeln, anstatt Sie abzufragen.

So behandeln Sie Interaktions Quell Ereignisse:
* Registrieren Sie sich für ein *interaktionmanager* -Eingabe Ereignis. Für jede Art von Interaktions Ereignis, für das Sie sich interessieren, müssen Sie es abonnieren.

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* Behandeln Sie das-Ereignis. Wenn Sie ein Interaktions Ereignis abonniert haben, erhalten Sie gegebenenfalls den Rückruf. Im Beispiel " *sourcepressed* " ist dies der Fall, nachdem die Quelle erkannt wurde und bevor Sie freigegeben oder verloren geht.

   ```cs
   void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
       var interactionSourceState = args.state;

       // args.state has information about:
          // targeting head ray at the time when the event was triggered
          // whether the source is pressed or not
          // properties like position, velocity, source loss risk
          // source id (which hand id for example) and source kind like hand, voice, controller or other
   }
   ```

### <a name="how-to-stop-handling-an-event"></a>Beenden der Behandlung eines Ereignisses

Sie müssen die Behandlung eines Ereignisses beenden, wenn Sie nicht mehr an dem Ereignis interessiert sind oder das Objekt zerstören, das das Ereignis abonniert hat. Wenn Sie die Verarbeitung des Ereignisses beenden möchten, kündigen Sie das Ereignis an.

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a>Liste der Interaktions Quell Ereignisse

Die folgenden Interaktions Quell Ereignisse sind verfügbar:
* *Interaktionsourceerkannt* (Quelle wird aktiv)
* *Interaktionsourcelost* (wird inaktiv)
* *Interaktionsourcepressed* (tippen, drücken der Schaltfläche oder "auswählen")
* *Interaktionsourcereleasing* (Ende einer Tap-Schaltfläche, oder Ende der "Select"-Taste)
* *Interaktionsourceupveraltet* (verschieben oder anderweitig ändern eines Zustands)

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a>Ereignisse für Vergangenheits Ziele, die mit einem Press oder Release am genauesten zu vergleichen sind

Die zuvor beschriebenen Abruf-APIs machen Ihre APP-vorhergesagte Posen aus.  Obwohl die vorhergesagten Posen am besten zum Rendern des Controllers oder eines virtuellen Hand Held Objekts geeignet sind, sind zukünftige Formen für das Ziel nicht optimal, aus zwei wichtigen Gründen:
* Wenn der Benutzer eine Schaltfläche auf einem Controller drückt, kann es ungefähr 20 ms drahtlose Latenz über Bluetooth geben, bevor das System den Druck erhält.
* Wenn Sie dann eine vorwärts Gesagte Pose verwenden, gibt es eine weitere 10-20 MS der Forward-Vorhersage, auf die die Uhrzeit angewendet wird, zu der die Daten des aktuellen Frames die Augen des Benutzers erreichen.

Dies bedeutet, dass bei der Abfrage eine Quell Pose oder eine Kopfzeile angezeigt wird, die 30-40 ms vorwärts ist, von wo aus die Kopfzeile des Benutzers und die Hände wieder zurück waren, als die Taste oder das Release aufgetreten ist  Bei der Eingabe von hololens-Hand Eingaben gibt es eine ähnliche Verarbeitungs Verzögerung, um den Druck zu erkennen.

Um basierend auf der ursprünglichen Absicht des Benutzers für eine Hand oder einen Controller eine genaue Zielsetzung zu erreichen, sollten Sie die historische Quell Pose oder die Kopfzeile aus dem *interaktionsourcepressed* -oder *interaktionsourcereleasing* -Eingabe Ereignis verwenden.

Sie können eine Presse oder eine Freigabe mit Verlaufs Daten des Benutzers oder des Controllers als Ziel haben:
* Die Kopfzeile zu dem Zeitpunkt, an dem eine Geste oder eine Controller Bewegung aufgetreten ist, die für die **Ziel** Bestimmung verwendet werden kann, um zu bestimmen, was der [Benutzer untersucht hat:](../../design/gaze-and-commit.md)

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args) {
       var interactionSourceState = args.state;
       var headPose = interactionSourceState.headPose;
       RaycastHit raycastHit;
       if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
           var targetObject = raycastHit.collider.gameObject;
           // ...
       }
   }
   ```

* Die Quell Pose zu dem Zeitpunkt, zu dem eine Bewegung des Bewegungs Controllers stattgefunden hat. diese kann verwendet werden, **um zu bestimmen** , auf welche Weise der Benutzer den Controller verwiesen hat.  Dabei handelt es sich um den Zustand des Controllers, der den Druck erhalten hat.  Wenn Sie den Controller selbst rendern, können Sie die Zeiger Darstellung anstelle der Ziehpunkt-Pose anfordern, um das Ziel-Ray von dem zu überprüfen, was der Benutzer für den natürlichen Tipp des gerenderten Controllers in Erwägung zieht:

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args)
   {
       var interactionSourceState = args.state;
       var sourcePose = interactionSourceState.sourcePose;
       Vector3 sourceGripPosition;
       Quaternion sourceGripRotation;
       if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Pointer)) &&
           (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Pointer))) {
           RaycastHit raycastHit;
           if (Physics.Raycast(sourceGripPosition, sourceGripRotation * Vector3.forward, out raycastHit, 10)) {
               var targetObject = raycastHit.collider.gameObject;
               // ...
           }
       }
   }
   ```

### <a name="event-handlers-example"></a>Beispiel für Ereignishandler

```cs
using UnityEngine.XR.WSA.Input;

void Start()
{
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased += InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
}

void OnDestroy()
{
    InteractionManager.InteractionSourceDetected -= InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost -= InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased -= InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;
}

void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
{
    // Source was detected
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceLost(InteractionSourceLostEventArgs state)
{
    // Source was lost. This will be after a SourceDetected event and no other events for this
    // source id will occur until it is Detected again
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs state)
{
    // Source was pressed. This will be after the source was detected and before it is
    // released or lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceReleased(InteractionSourceReleasedEventArgs state)
{
    // Source was released. The source would have been detected and pressed before this point.
    // This event will not fire if the source is lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs state)
{
    // Source was updated. The source would have been detected before this point
    // args.state has the current state of the source including id, position, kind, etc.
}
```

## <a name="motion-controllers-in-mrtk-v2"></a>Motion-Controller in mrtk v2

Sie können über den Eingabe-Manager auf [Gesten-und Bewegungs Controller](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html) zugreifen.

## <a name="follow-along-with-tutorials"></a>Immer am Ball mit Tutorials

Schritt-für-Schritt-Tutorials mit ausführlicheren Anpassungs Beispielen sind in der Mixed Reality Academy verfügbar:

- [MR-Eingabe 211: Geste](tutorials/holograms-211.md)
- [MR-Eingabe 213: Motion-Controller](../../deprecated/mixed-reality-213.md)

[![Mr-Eingabe 213-Motion Controller](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)<br>
*Mr-Eingabe 213-Motion Controller*

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie der Unity-Entwicklungs Journey folgen, die wir angelegt haben, befinden Sie sich mitten in der Untersuchung der mrtk Core-Bausteine. Von hier aus können Sie mit dem nächsten Baustein fortfahren:

> [!div class="nextstepaction"]
> [Hand- und Eye-Tracking](./hand-eye-in-unity.md)

Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:

> [!div class="nextstepaction"]
> [Gemeinsame Erfahrung](shared-experiences-in-unity.md)

Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.

## <a name="see-also"></a>Siehe auch

* [Anvisieren mit dem Kopf und Ausführen](../../design/gaze-and-commit.md)
* [Motion-Controller](../../design/motion-controllers.md)