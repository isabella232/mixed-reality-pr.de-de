---
title: Motion-Controller in Unity
description: Erfahren Sie, wie Sie mithilfe von XR und allgemeinen Schaltflächen- und Achsen-APIs Aktionen für Ihre Anvis in Unity mit Motion Controller-Eingaben ergreifen.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: Motion-Controller, Unity, Eingabe, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: ff1eedcc337edd2d7edfe8d961bb88bcb859cd23
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743486"
---
# <a name="motion-controllers-in-unity"></a>Motion-Controller in Unity

Es gibt zwei wichtige Möglichkeiten, um beim Anvieren [in Unity](gaze-in-unity.md)Aktionen zu [ergreifen:](../../design/gaze-and-commit.md#composite-gestures) Handgesten und [Motion-Controller](../../design/motion-controllers.md) in HoloLens und Immersive HMD. Sie greifen auf die Daten für beide Quellen räumlicher Eingaben über die gleichen APIs in Unity zu.

Unity bietet zwei primäre Möglichkeiten für den Zugriff auf räumliche Eingabedaten für Windows Mixed Reality. Die allgemeinen *Input.GetButton/Input.GetAxis-APIs* funktionieren über mehrere Unity XR SDKs hinweg, während die für Windows Mixed Reality spezifische *InteractionManager/GestureRecognizer-API* den vollständigen Satz räumlicher Eingabedaten verfügbar macht.

## <a name="unity-xr-input-apis"></a>Unity XR-Eingabe-APIs

Für neue Projekte wird empfohlen, die neuen XR-Eingabe-APIs von Anfang an zu verwenden. 

Weitere Informationen zu den [XR-APIs finden Sie hier.](https://docs.unity3d.com/Manual/xr_input.html)

## <a name="unity-buttonaxis-mapping-table"></a>Unity-Schaltflächen-/Achsenzuordnungstabelle

Der Eingabe-Manager für Windows Mixed Reality Motion-Controller von Unity unterstützt die unten aufgeführten Schaltflächen- und Achsen-IDs über die *Input.GetButton/GetAxis-APIs.* Die Spalte "Windows MR-spezifisch" bezieht sich auf Eigenschaften, die vom *Typ InteractionSourceState verfügbar* sind. Jede dieser APIs wird in den folgenden Abschnitten ausführlich beschrieben.

Die Schaltflächen-/Achsen-ID-Zuordnungen für Windows Mixed Reality im Allgemeinen mit den Oculus-Schaltflächen-/Achsen-IDs übereinstimmen.

Die Schaltflächen-/Achsen-ID-Zuordnungen für Windows Mixed Reality unterscheiden sich von den OpenVR-Zuordnungen auf zwei Arten:
1. Die Zuordnung verwendet Touchpad-IDs, die sich von thumbstick unterscheiden, um Controller mit Thumbsticks und Touchpads zu unterstützen.
2. Die Zuordnung vermeidet das Überladen der A- und X-Schaltflächen-IDs für die Menüschaltflächen, damit sie für die physischen ABXY-Schaltflächen verfügbar sind.

<table>
<tr>
<th rowspan="2">Eingabe </th><th colspan="2"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Allgemeine Unity-APIs</a><br />(Input.GetButton/GetAxis) </th><th rowspan="2"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">Windows MR-spezifische Eingabe-API</a><br />(XR. WSA. Eingabe)</th>
</tr><tr>
<th> Linken </th><th> Rechte Hand</th>
</tr><tr>
<td> Auswählen des gedrückten Triggers </td><td> Achse 9 = 1,0 </td><td> Achse 10 = 1,0 </td><td> selectPressed</td>
</tr><tr>
<td> Auswählen des analogen Triggerwerts </td><td> Achse 9 </td><td> Achse 10 </td><td> selectPressedAmount</td>
</tr><tr>
<td> Select trigger partially pressed (Trigger teilweise gedrückt auswählen) </td><td> Schaltfläche 14 <i>(Gamepad-Kompatibilität)</i> </td><td> Schaltfläche 15 <i>(Gamepad-Kompatibilität)</i> </td><td> selectPressedAmount &gt; 0.0</td>
</tr><tr>
<td> Menüschaltfläche gedrückt </td><td> Schaltfläche 6* </td><td> Schaltfläche 7* </td><td> menuPressed</td>
</tr><tr>
<td> Greiftaste gedrückt </td><td> Achse 11 = 1,0 (keine analogen Werte)<br />Schaltfläche 4 <i>(Gamepad-Kompatibilität)</i> </td><td> Achse 12 = 1,0 (keine analogen Werte)<br />Schaltfläche 5 <i>(Gamepad-Kompatibilität)</i> </td><td> Begriffen</td>
</tr><tr>
<td> Thumbstick X <i>(left: -1.0, right: 1.0)</i> </td><td> Achse 1 </td><td> Achse 4 </td><td> thumbstickPosition.x</td>
</tr><tr>
<td> Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </td><td> Achse 2 </td><td> Achse 5 </td><td> thumbstickPosition.y</td>
</tr><tr>
<td> Thumbstick pressed (Gedrückter Fingerabdruck) </td><td> Schaltfläche 8 </td><td> Schaltfläche 9 </td><td> thumbstickPressed</td>
</tr><tr>
<td> Touchpad X <i>(links: -1.0, rechts: 1.0)</i> </td><td> Achse 17* </td><td> Achse 19* </td><td> touchpadPosition.x</td>
</tr><tr>
<td> Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </td><td> Achse 18* </td><td> Achse 20* </td><td> touchpadPosition.y</td>
</tr><tr>
<td> Touchpad berührt </td><td> Schaltfläche 18* </td><td> Schaltfläche 19* </td><td> touchpadTouched</td>
</tr><tr>
<td> Touchpad gedrückt </td><td> Schaltfläche 16* </td><td> Schaltfläche 17* </td><td> touchpadPressed</td>
</tr><tr>
<td> 6DoF-Greif- oder Zeigerpose </td><td colspan="2"> <i>Nur</i> Greifpose: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. InputTracking.GetLocalPosition</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">Xr. InputTracking.GetLocalRotation</a></td><td> Übergeben <i>Sie "Pointer"</i> oder <i>"Pointer"</i> als Argument: sourceState.sourcePose.TryGetPosition<br />sourceState.sourcePose.TryGetRotation<br /></td>
</tr><tr>
<td> Nachverfolgungsstatus </td><td colspan="2"> <i>Position accuracy and source loss risk only available through MR-specific API</i> </td><td> <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></td>
</tr>
</table>

>[!NOTE]
>Diese Schaltflächen-/Achsen-IDs unterscheiden sich von den IDs, die Unity für OpenVR verwendet, aufgrund von Kollisionen in den Zuordnungen, die von Gamepads, Oculus Touch und OpenVR verwendet werden.

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


## <a name="grip-pose-vs-pointing-pose"></a>Greifpose im Vergleich zu zeigenden Posen

Windows Mixed Reality unterstützt Bewegungscontroller in einer Vielzahl von Formfaktoren. Der Entwurf jedes Controllers unterscheidet sich in seiner Beziehung zwischen der Handposition des Benutzers und der natürlichen "Vorwärtsrichtung", die Apps verwenden sollten, um beim Rendern des Controllers zu zeigen.

Um diese Controller besser darstellen zu können, gibt es zwei  Arten von Posen, die Sie für jede Interaktionsquelle untersuchen können: die Greifpose und die **Zeigerpose.** Die Greif- und Zeiger-Posenkoordinaten werden von allen Unity-APIs in globalen Unity-Weltkoordinaten ausgedrückt.

### <a name="grip-pose"></a>Greifpose

Die **Greifhaltung** stellt die Position der Benutzerfläche dar, die entweder von einer HoloLens erkannt wird oder einen Bewegungscontroller hält.

Bei immersiven Headsets wird die Greifpose am besten verwendet, um die Hand des Benutzers oder ein Objekt in der Hand des **Benutzers zu rendern.**  Die Greifpose wird auch beim Visualisieren eines Bewegungscontrollers verwendet. Das **renderbare Modell, das** von Windows für einen Bewegungscontroller bereitgestellt wird, verwendet die Greifpose als Ursprung und Drehzentrum.

Die Greifpose ist wie folgt speziell definiert:
* Die **Greifposition:** Der Handflächenschwerpunkt, wenn der Controller natürlich hält, nach links oder rechts angepasst, um die Position innerhalb des Greifs zu zentriert. Auf dem Windows Mixed Reality Motion-Controller wird diese Position in der Regel an der Schaltfläche Greiftaste ausgerichtet.
* Die **rechte** Achse der Greifausrichtung: Wenn Sie Ihre Hand vollständig öffnen, um eine flache 5-Finger-Pose zu bilden, den Strahl, der normal zu Ihrer Handfläche ist (vorwärts von der linken Handfläche, rückwärts von der rechten Handfläche).
* **Die Vorwärtsachse der Klammerausrichtung:** Wenn Sie Ihre Hand teilweise schließen (so als ob sie den Controller hält), zeigt der Strahl, der "vorwärts" durch die Von den Nichtfingerfingern gebildeten Strahl zeigt.
* Die **Nach-oben-Achse der Klammerausrichtung:** Die nach oben-Achse, die durch die Definitionen Rechts und Vorwärts impliziert wird.

Sie können über die anbieterübergreifende Eingabe-API von Unity ( XR) auf die Klammerhaltung *[zugreifen. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation*) oder über die MR-spezifische Windows-API (*sourceState.sourcePose.TryGetPosition/Rotation*, anfordern von Pose-Daten für den **Klammerknoten).**

### <a name="pointer-pose"></a>Zeigerpose

Die **Zeigerpose** stellt die Spitze des Controllers dar, der nach vorn zeigt.

Die vom System bereitgestellte Zeigerpose wird am besten zum Raycasten verwendet, wenn Sie **das Controllermodell selbst rendern.** Wenn Sie ein anderes virtuelles Objekt anstelle des Controllers rendern, z. B. ein virtuelles Geschütz, sollten Sie mit einem Strahl zeigen, der für dieses virtuelle Objekt am natürlichsten ist, z. B. ein Strahl, der entlang des Durchlaufs des von der App definierten Strahlmodells verläuft. Da Benutzer das virtuelle Objekt und nicht den physischen Controller sehen können, ist das Verweisen auf das virtuelle Objekt wahrscheinlich natürlicher für Benutzer, die Ihre App verwenden.

Derzeit ist die Zeigerhaltung in Unity nur über die Windows MR-spezifische API *sourceState.sourcePose.TryGetPosition/Rotation* verfügbar, wobei *InteractionSourceNode.Pointer* als Argument übergeben wird.

## <a name="controller-tracking-state"></a>Controller-Nachverfolgungsstatus

Wie die Headsets erfordert auch der Windows Mixed Reality Motion Controller keine Einrichtung externer Überwachungssensoren. Stattdessen werden die Controller von Sensoren im Headset selbst nachverfolgt.

Wenn der Benutzer die Controller aus dem Ansichtsfeld des Headsets verschiebt, leitet Windows in den meisten Fällen weiterhin Controllerpositionen ab. Wenn der Controller die visuelle Nachverfolgung lange genug verloren hat, werden die Positionen des Controllers auf Positionen mit ungefährer Genauigkeit abgesenkt.

An diesem Punkt sperrt das System den Controller für den Benutzer, verfolgt die Position des Benutzers, während er sich bewegt, während die tatsächliche Ausrichtung des Controllers weiterhin mit seinen internen Ausrichtungssensoren verfügbar ist. Viele Apps, die Controller verwenden, um auf Benutzeroberflächenelemente zu zeigen und diese zu aktivieren, können normal und mit ungefährer Genauigkeit ausgeführt werden, ohne dass der Benutzer dies feststellen muss.

<!-- The best way to get a feel for this is to try it yourself. Check out this video with examples of immersive content that works with motion controllers across various tracking states:

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g] -->

### <a name="reasoning-about-tracking-state-explicitly"></a>Explizite Überlegungen zum Nachverfolgungsstatus

Apps, die Positionen basierend auf dem Nachverfolgungsstatus unterschiedlich behandeln möchten, können weiter gehen und Eigenschaften für den Zustand des Controllers überprüfen, z. B. *SourceLossRisk* und *PositionAccuracy:*

<table>
<tr>
<th> Nachverfolgungsstatus </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>Hohe Genauigkeit</b> </td><td style="background-color: green; color: white"> &lt; 1.0 </td><td style="background-color: green; color: white"> Hoch </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Hohe Genauigkeit (verlustgefahrt)</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: green; color: white"> Hoch </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Ungefähre Genauigkeit</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> Ungefähr </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Keine Position</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> Ungefähr </td><td style="background-color: orange"> false</td>
</tr>
</table>

Diese Nachverfolgungszustände des Motion-Controllers sind wie folgt definiert:
* **Hohe Genauigkeit:** Während sich der Bewegungscontroller im Ansichtsfeld des Headsets befindet, bietet er in der Regel basierend auf der visuellen Nachverfolgung positionen mit hoher Genauigkeit. Ein sich bewegender Controller, der vorübergehend das Sichtfeld verlässt oder kurzzeitig von den Headsetsensoren verdeckt wird (z. B. durch die andere Seite des Benutzers), gibt weiterhin eine kurze Zeit lang hochgenaue Posen zurück, basierend auf der trägen Nachverfolgung des Controllers selbst.
* **Hohe Genauigkeit (verlustgefährdete):** Wenn der Benutzer den Motion-Controller hinter den Rand des Ansichtsfelds des Headsets bewegt, kann das Headset die Position des Controllers bald nicht mehr visuell nachverfolgen. Die App weiß, wann der Controller diese FOV-Grenze erreicht hat, indem sie den **SourceLossRisk-Wert** 1.0 erreicht. An diesem Punkt kann die App Controllergesten anhalten, die einen stabilen Stream von hochwertigen Posen erfordern.
* **Ungefähre Genauigkeit:** Wenn der Controller die visuelle Nachverfolgung lange genug verloren hat, werden die Positionen des Controllers auf Positionen mit ungefährer Genauigkeit abgesenkt. An diesem Punkt sperrt das System den Controller für den Benutzer, verfolgt die Position des Benutzers, während er sich bewegt, während die tatsächliche Ausrichtung des Controllers weiterhin mit seinen internen Ausrichtungssensoren verfügbar ist. Viele Apps, die Controller verwenden, um auf Benutzeroberflächenelemente zu zeigen und diese zu aktivieren, können normal und mit ungefährer Genauigkeit ausgeführt werden, ohne dass der Benutzer darauf hinweist. Apps mit größeren Eingabeanforderungen können diesen Abfall von **Hoher** Genauigkeit zu **Ungefähre** Genauigkeit durch Untersuchen der **PositionAccuracy-Eigenschaft** einsehen, um dem Benutzer z. B. während dieser Zeit einen freundlicheren Hitbox-Wert für Ziele außerhalb des Bildschirms zu geben.
* **Keine Position:** Der Controller kann zwar über einen längeren Zeitraum mit ungefährer Genauigkeit arbeiten, manchmal weiß das System jedoch, dass selbst eine durch Körper gesperrte Position im Moment nicht sinnvoll ist. Beispielsweise wurde ein controller, der aktiviert wurde, möglicherweise nie visuell beobachtet, oder ein Benutzer kann einen Controller abstellen, der dann von einer anderen Person übernommen wird. Zu diesen Zeiten stellt das System keine Position für die App bereit, und *TryGetPosition* gibt FALSE zurück.

## <a name="common-unity-apis-inputgetbuttongetaxis"></a>Allgemeine Unity-APIs (Input.GetButton/GetAxis)

**Namespace:** *UnityEngine*, *UnityEngine.XR*<br>
**Typen:** *Eingabe,* *XR. InputTracking*

Unity verwendet derzeit die allgemeinen *Input.GetButton/Input.GetAxis-APIs,* um Eingaben für [das Oculus SDK,](https://docs.unity3d.com/Manual/OculusControllers.html) [das OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) und Windows Mixed Reality verfügbar zu machen, einschließlich Hände und Motion Controller. Wenn Ihre App diese APIs für die Eingabe verwendet, kann sie Motion-Controller problemlos über mehrere XR SDKs hinweg unterstützen, einschließlich Windows Mixed Reality.

### <a name="getting-a-logical-buttons-pressed-state"></a>Abrufen des gedrückten Zustands einer logischen Schaltfläche

Um die allgemeinen Unity-Eingabe-APIs zu verwenden, beginnen Sie in der Regel damit, Schaltflächen und Achsen mit logischen Namen im [Unity-Eingabe-Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html)zu verkabeln und eine Schaltfläche oder Achsen-IDs an jeden Namen zu binden. Anschließend können Sie Code schreiben, der auf diesen logischen Schaltflächen-/Achsennamen verweist.

Um z. B. die Triggerschaltfläche des linken Bewegungscontrollers der Aktion Senden zuzuordnen, wechseln Sie zu **Bearbeiten > Projekteinstellungen > Eingabe** in Unity, und erweitern Sie die Eigenschaften des Abschnitts Senden unter Achsen. Ändern Sie die Eigenschaft **Positive Schaltfläche** oder Alt **Positive Button** wie folgt, um **schaltfläche 14** zu lesen:

![InputManager von Unity](images/unity-input-manager.png)<br>
*Unity InputManager*

Ihr Skript kann dann mit *Input.GetButton* nach der Aktion Senden suchen:

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
Sie können weitere logische Schaltflächen hinzufügen, indem Sie die **Eigenschaft Größe** unter **Achsen** ändern.

### <a name="getting-a-physical-buttons-pressed-state-directly"></a>Direktes Abrufen des gedrückten Zustands einer physischen Schaltfläche

Sie können auch manuell über ihren vollqualifizierten Namen auf Schaltflächen zugreifen, indem *Sie Input.GetKey* verwenden:

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a>Abrufen der Posen eines Hand- oder Bewegungscontrollers

Sie können mit XR auf die Position und Drehung des Controllers *zugreifen. InputTracking:*

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

> [!NOTE] 
> Der obige Code stellt die Klammerpose des Controllers dar (in der der Benutzer den Controller hält), die nützlich ist, um eine Schütze in der Hand des Benutzers oder ein Modell des Controllers selbst zu rendern.
> 
> Die Beziehung zwischen dieser Klammerpose und der Zeigerpose (wobei die Spitze des Controllers zeigt) kann sich über controllerübergreifend unterscheiden. Derzeit ist der Zugriff auf die Zeigerhaltung des Controllers nur über die MR-spezifische Eingabe-API möglich, die in den folgenden Abschnitten beschrieben wird.

## <a name="windows-specific-apis-xrwsainput"></a>Windows-spezifische APIs (XR. WSA. Eingabe)

> [!CAUTION]
> Wenn Ihr Projekt eine der XR-Dateien verwendet. WSA-APIs, die in zukünftigen Unity-Releases zugunsten des XR SDK eingestellt werden. Für neue Projekte wird empfohlen, das XR SDK von Anfang an zu verwenden. Weitere Informationen zum [XR-Eingabesystem und](https://docs.unity3d.com/Manual/xr_input.html)zu den APIs finden Sie hier.

**Namespace:** *UnityEngine.XR.WSA.Input*<br>
**Typen:** *InteractionManager,* *InteractionSourceState,* *InteractionSource,* *InteractionSourceProperties,* *InteractionSourceKind,* *InteractionSourceLocation*

Um ausführlichere Informationen zu Windows Mixed Reality Handeingabe (für HoloLens) und Motion-Controllern zu erhalten, können Sie die Windows-spezifischen APIs für räumliche Eingaben unter dem *UnityEngine.XR.WSA.Input-Namespace* verwenden. Dadurch können Sie auf zusätzliche Informationen wie Positionsgenauigkeit oder Quellart zugreifen, sodass Sie Hände und Controller voneinander unterscheiden können.

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a>Abfragen des Zustands von Händen und Motion-Controllern

Sie können den Zustand dieses Frames für jede Interaktionsquelle (Hand oder Motion Controller) mithilfe der *GetCurrentReading-Methode* abfragen.

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

Jeder *InteractionSourceState,* den Sie zurückerhalten, stellt eine Interaktionsquelle zum aktuellen Zeitpunkt dar. *InteractionSourceState* macht Informationen verfügbar, z. B.:
* Welche [Arten von Pressen](../../design/motion-controllers.md) auftreten (Auswählen/Menü/Greifen/Touchpad/Fingerabdruck)

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* Andere spezifische Daten für Motion-Controller, z. B. das Touchpad und/oder die XY-Koordinaten und den touchierten Zustand des Sticks

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```

* InteractionSourceKind, um zu wissen, ob es sich bei der Quelle um eine Hand oder einen Motion Controller handelt

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a>Abfragen von vorwärts vorhergesagten Renderingdarstellungen

* Beim Abfragen von Interaktionsquelldaten von Händen und Controllern sind die Posen, die Sie erhalten, vorwärts vorhergesagte Posen für den Moment, in dem die Photonen dieses Frames die Augen des Benutzers erreichen.  Vorwärtsvorhersagen werden am besten zum **Rendern** des Controllers oder eines gehaltenen Objekts für jeden Frame verwendet.  Wenn Sie eine bestimmte Veröffentlichung mit dem Controller als Ziel verwenden, ist dies am genauesten, wenn Sie die unten beschriebenen APIs für historische Ereignisse verwenden.

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* Sie können auch die vorwärts vorhergesagte Kopfpose für diesen aktuellen Frame abrufen.  Wie bei der Quellpose ist dies nützlich für das **Rendern** eines Cursors, obwohl das Ziel einer bestimmten Veröffentlichung am genauesten ist, wenn Sie die unten beschriebenen APIs für historische Ereignisse verwenden.

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a>Behandeln von Interaktionsquellereignissen

Um Eingabeereignisse so zu behandeln, wie sie mit ihren genauen Historischen Posendaten auftreten, können Sie Interaktionsquellereignisse behandeln, anstatt abzufragen.

So behandeln Sie Interaktionsquellereignisse:
* Registrieren Sie sich für ein *InteractionManager-Eingabeereignis.* Für jede Art von Interaktionsereignis, an dem Sie interessiert sind, müssen Sie es abonnieren.

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* Behandeln sie das -Ereignis. Nachdem Sie ein Interaktionsereignis abonniert haben, erhalten Sie ggf. den Rückruf. Im *SourcePressed-Beispiel* ist dies, nachdem die Quelle erkannt wurde und bevor sie freigegeben oder verloren geht.

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

Sie müssen die Behandlung eines Ereignisses beenden, wenn Sie nicht mehr am Ereignis interessiert sind oder das Objekt zerstören, das das Ereignis abonniert hat. Um die Behandlung des Ereignisses zu beenden, kündigen Sie das Ereignis.

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a>Liste der Interaktionsquelle-Ereignisse

Die verfügbaren Interaktionsquellenereignisse sind:
* *InteractionSourceDetected* (Quelle wird aktiv)
* *InteractionSourceLost* (wird inaktiv)
* *InteractionSourcePressed* (Tippen, Drücken der Schaltfläche oder Äußerung "Auswählen")
* *InteractionSourceReleased* (Ende eines Tippens, losgelassene Schaltfläche oder Ende der Äußerung "Auswählen")
* *InteractionSourceUpdated* (verschiebt oder ändert einen Zustand auf andere Weise)

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a>Ereignisse für historische Zielgruppenadressierung stellen eine genaue Übereinstimmung mit einer Veröffentlichung oder einer Veröffentlichung

Die oben beschriebenen Abruf-APIs geben Ihrer App vorhergesagte Posen.  Die vorhergesagten Posen sind zwar am besten für das Rendern des Controllers oder eines virtuellen Objekts, aber zukünftige Posen sind für die Ausrichtung nicht optimal, aus zwei Wichtigen Gründen:
* Wenn der Benutzer eine Taste auf einem Controller drückt, kann es über Bluetooth zu einer Funklatenz von etwa 20 ms geben, bevor das System die Taste empfängt.
* Wenn Sie dann eine vorausgesagte Pose verwenden, werden weitere 10-20 ms Vorwärtsvorhersage angewendet, um die Zeit als Ziel zu verwenden, zu der die Photonen des aktuellen Frames die Augen des Benutzers erreichen.

Dies bedeutet, dass Sie beim Abruf eine Quell- oder Kopfpose erhalten, die 30 bis 40 ms vor dem Ort liegt, an dem der Kopf und die Hände des Benutzers tatsächlich zurück waren, als das Drücken oder Dies passiert ist.  Bei HoloLens-Handeingaben gibt es zwar keine Drahtlose Übertragungsverzögerung, es gibt jedoch eine ähnliche Verarbeitungsverzögerung, um den Press zu erkennen.

Um auf der Grundlage der ursprünglichen Absicht des Benutzers für eine Hand- oder Controllereingabe genau als Ziel zu verwenden, sollten Sie die historische Quellpose oder Kopfpose aus diesem *InteractionSourcePressed-* oder *InteractionSourceReleased-Eingabeereignis* verwenden.

Sie können eine Press- oder Release-Version mit Verlaufsdaten aus dem Kopf des Benutzers oder seinem Controller als Ziel verwenden:
* Die Kopfpose zu dem Zeitpunkt, zu dem eine Geste  oder ein Controller-Press aufgetreten [ist,](../../design/gaze-and-commit.md) die zum Festlegen des Ziels verwendet werden kann, um zu bestimmen, worum es sich beim Benutzer gezaust hat:

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

* Die Quellpose zu dem Zeitpunkt, zu dem ein Bewegungscontroller gedrückt wurde, der zum Festlegen des Ziels verwendet werden kann, um zu bestimmen, auf was der Benutzer auf den Controller zeigen soll.   Dies ist der Zustand des Controllers, bei dem das Drücken auft ist.  Wenn Sie den Controller selbst rendern, können Sie die Zeigerpose anstelle der Greifpose anfordern, um den Zielstrahl von dem zu kippen, was der Benutzer als natürliche Spitze dieses gerenderten Controllers betrachten wird:

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

## <a name="motion-controllers-in-mrtk"></a>Motion Controllers in MRTK

Sie können über den [Eingabe-Manager auf gesten-](/windows/mixed-reality/mrtk-unity/features/input/controllers) und bewegungscontroller zugreifen.

## <a name="follow-along-with-tutorials"></a>Immer am Ball mit Tutorials

Ausführliche Tutorials mit ausführlicheren Anpassungsbeispielen finden Sie in der Mixed Reality Academy:

- [MR-Eingabe 211: Geste](tutorials/holograms-211.md)
- [MR-Eingabe 213: Motion-Controller](../../deprecated/mixed-reality-213.md)

[![MR-Eingabe 213 – Motion-Controller](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)<br>
*MR-Eingabe 213 – Motion-Controller*

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie den Weg zur Unity-Entwicklung, den wir ihnen auf den Weg geben, folgen, sind Sie gerade dabei, die MRTK-Kernbausteine zu erkunden. Von hier aus können Sie mit dem nächsten Baustein fortfahren:

> [!div class="nextstepaction"]
> [Hand- und Eye-Tracking](./hand-eye-in-unity.md)

Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:

> [!div class="nextstepaction"]
> [Gemeinsame Erfahrung](shared-experiences-in-unity.md)

Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.

## <a name="see-also"></a>Siehe auch

* [Anvisieren mit dem Kopf und Ausführen](../../design/gaze-and-commit.md)
* [Motion-Controller](../../design/motion-controllers.md)