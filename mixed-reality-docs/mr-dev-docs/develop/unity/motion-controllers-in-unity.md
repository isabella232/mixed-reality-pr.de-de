---
title: Motion-Controller in Unity
description: Erfahren Sie, wie Sie mithilfe von XR und allgemeinen Schaltflächen- und Achsen-APIs Aktionen in Unity mit Motion Controller-Eingaben ergreifen.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: Motion-Controller, Unity, Eingabe, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: ccda5b11190e829ccc655989a6f679ef6ef647a920c01a3182548b23a3d85084
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115216240"
---
# <a name="motion-controllers-in-unity"></a>Motion-Controller in Unity

Es gibt zwei wichtige Möglichkeiten, aktionen beim [Anvieren in Unity](gaze-in-unity.md)zu ergreifen: [Handgesten](../../design/gaze-and-commit.md#composite-gestures) und [Motion-Controller](../../design/motion-controllers.md) in HoloLens und Immersive HMD. Sie greifen über die gleichen APIs in Unity auf die Daten für beide Quellen räumlicher Eingaben zu.

Unity bietet zwei Hauptmethoden für den Zugriff auf räumliche Eingabedaten für Windows Mixed Reality. Die *gängigen Input.GetButton/Input.GetAxis-APIs* funktionieren über mehrere Unity XR SDKs hinweg, während die *InteractionManager/GestureRecognizer-API,* die für Windows Mixed Reality spezifisch ist, den vollständigen Satz räumlicher Eingabedaten verfügbar macht.

## <a name="unity-xr-input-apis"></a>Unity XR-Eingabe-APIs

Für neue Projekte wird empfohlen, die neuen XR-Eingabe-APIs von Anfang an zu verwenden. 

Weitere Informationen zu den [XR-APIs](https://docs.unity3d.com/Manual/xr_input.html)finden Sie hier.

## <a name="unity-buttonaxis-mapping-table"></a>Unity-Schaltflächen-/Achsenzuordnungstabelle

Der Eingabe-Manager von Unity für Windows Mixed Reality Motion-Controller unterstützt die unten aufgeführten Schaltflächen- und Achsen-IDs über die *Input.GetButton/GetAxis-APIs.* Die Spalte "Windows MR-spezifisch" bezieht sich auf Eigenschaften, die vom *InteractionSourceState-Typ* verfügbar sind. Jede dieser APIs wird in den folgenden Abschnitten ausführlich beschrieben.

Die Zuordnungen der Schaltflächen-/Achsen-ID für Windows Mixed Reality im Allgemeinen mit den Oculus-Schaltflächen-/Achsen-IDs übereinstimmen.

Die Zuordnungen der Schaltflächen-/Achsen-ID für Windows Mixed Reality unterscheiden sich auf zwei Arten von den Zuordnungen von OpenVR:
1. Die Zuordnung verwendet Touchpad-IDs, die sich vom Fingerabdruck unterscheiden, um Controller mit Thumbsticks und Touchpads zu unterstützen.
2. Die Zuordnung vermeidet das Überladen der A- und X-Schaltflächen-IDs für die Menüschaltflächen, um sie für die physischen ABXY-Schaltflächen verfügbar zu lassen.

<table>
<tr>
<th rowspan="2">Eingabe </th><th colspan="2"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Allgemeine Unity-APIs</a><br />(Input.GetButton/GetAxis) </th><th rowspan="2"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">Windows MR-spezifische Eingabe-API</a><br />(XR. WSA. Eingabe)</th>
</tr><tr>
<th> Linken </th><th> Rechte Hand</th>
</tr><tr>
<td> Trigger gedrückt auswählen </td><td> Achse 9 = 1,0 </td><td> Achse 10 = 1,0 </td><td> selectPressed</td>
</tr><tr>
<td> Auswählen des analogen Triggerwerts </td><td> Achse 9 </td><td> Achse 10 </td><td> selectPressedAmount</td>
</tr><tr>
<td> Trigger teilweise gedrückt auswählen </td><td> Schaltfläche 14 <i>(Gamepad-Kompatibilität)</i> </td><td> Schaltfläche 15 <i>(Gamepad-Kompatibilität)</i> </td><td> selectPressedAmount &gt; 0.0</td>
</tr><tr>
<td> Menüschaltfläche gedrückt </td><td> Schaltfläche 6* </td><td> Schaltfläche 7* </td><td> menuPressed</td>
</tr><tr>
<td> Klammertaste gedrückt </td><td> Achse 11 = 1,0 (keine analogen Werte)<br />Schaltfläche 4 <i>(Gamepad-Kompatibilität)</i> </td><td> Achse 12 = 1,0 (keine analogen Werte)<br />Schaltfläche 5 <i>(Gamepad-Kompatibilität)</i> </td><td> Begriffen</td>
</tr><tr>
<td> Thumbstick X <i>(links: -1.0, rechts: 1.0)</i> </td><td> Achse 1 </td><td> Achse 4 </td><td> thumbstickPosition.x</td>
</tr><tr>
<td> Thumbstick Y <i>(oben: -1,0, unten: 1,0)</i> </td><td> Achse 2 </td><td> Achse 5 </td><td> thumbstickPosition.y</td>
</tr><tr>
<td> Thumbstick gedrückt </td><td> Schaltfläche 8 </td><td> Schaltfläche 9 </td><td> thumbstickPressed</td>
</tr><tr>
<td> Touchpad X <i>(links: -1.0, rechts: 1.0)</i> </td><td> Achse 17* </td><td> Achse 19* </td><td> touchpadPosition.x</td>
</tr><tr>
<td> Touchpad Y <i>(oben: -1,0, unten: 1,0)</i> </td><td> Achse 18* </td><td> Achse 20* </td><td> touchpadPosition.y</td>
</tr><tr>
<td> Touchpad touched </td><td> Schaltfläche 18* </td><td> Schaltfläche 19* </td><td> touchpadTouched</td>
</tr><tr>
<td> Touchpad gedrückt </td><td> Schaltfläche 16* </td><td> Schaltfläche 17* </td><td> touchpadPressed</td>
</tr><tr>
<td> 6DoF-Klammerpose oder Zeigerpose </td><td colspan="2"> <i>Nur Klammerpose:</i> <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. InputTracking.GetLocalPosition</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">Xr. InputTracking.GetLocalRotation</a></td><td> Übergeben Von <i>"Klammer"</i> oder <i>"Zeiger"</i> als Argument: sourceState.sourcePose.TryGetPosition<br />sourceState.sourcePose.TryGetRotation<br /></td>
</tr><tr>
<td> Nachverfolgungsstatus </td><td colspan="2"> <i>Positionsgenauigkeit und Quellverlustrisiko nur über MR-spezifische API verfügbar</i> </td><td> <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></td>
</tr>
</table>

>[!NOTE]
>Diese Schaltflächen-/Achsen-IDs unterscheiden sich von den IDs, die Unity für OpenVR aufgrund von Kollisionen in den Zuordnungen verwendet, die von Gamepads, Oculus Touch und OpenVR verwendet werden.

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

### <a name="openxr"></a>OpenXR

Informationen zu den Grundlagen zu Mixed Reality-Interaktionen in Unity finden Sie im [Unity-Handbuch für Unity XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html). In dieser Unity-Dokumentation werden die Zuordnungen von controllerspezifischen Eingaben zu **generalisierbareren InputFeatureUsage-Funktionen,** die Identifizierung und Kategorisierung verfügbarer XR-Eingaben, das Lesen von Daten aus diesen Eingaben und vieles mehr behandelt.

Das Mixed Reality OpenXR-Plug-In stellt zusätzliche Eingabeinteraktionsprofile bereit, die **standardmäßigen InputFeatureUsage-Funktionen** zugeordnet sind, wie unten beschrieben:

| InputFeatureUsage | HP Reverb G2 Controller (OpenXR) | HoloLens Hand (OpenXR) |
| ---- | ---- | ---- |
| primary2DAxis | Joystick | |
| primary2DAxisClick | Klicken Sie auf " " | |
| Trigger (trigger) | Trigger  | |
| Griff | Griff | Tippen in die Luft oder Anzippen |
| primaryButton | [X/A] – Drücken | In die Luft tippen |
| secondaryButton | [Y/B] – Drücken Sie | |
| gripButton | Greifer – Drücken | |
| triggerButton | Trigger – Drücken | |
| menuButton | Menü | |

## <a name="grip-pose-vs-pointing-pose"></a>Greifpose im Vergleich zu zeigenden Posen

Windows Mixed Reality unterstützt Bewegungscontroller in einer Vielzahl von Formfaktoren. Der Entwurf jedes Controllers unterscheidet sich in seiner Beziehung zwischen der Handposition des Benutzers und der natürlichen "Vorwärtsrichtung", die Apps verwenden sollten, um beim Rendern des Controllers zu zeigen.

Um diese Controller besser darstellen zu können, gibt es zwei  Arten von Posen, die Sie für jede Interaktionsquelle untersuchen können: die Greif- und die **Zeigerpose.** Die Greif- und Zeigerposenkoordinaten werden von allen Unity-APIs in globalen Unity-Weltkoordinaten ausgedrückt.

### <a name="grip-pose"></a>Greifpose

Die **Greifhaltung** stellt die Position der Benutzerfläche dar, die entweder von einem Benutzer erkannt HoloLens oder einen Bewegungscontroller hält.

Bei immersiven Headsets wird die Greifpose am besten verwendet, um die Hand des Benutzers oder ein Objekt in der Hand des **Benutzers zu rendern.**  Die Greifpose wird auch beim Visualisieren eines Bewegungscontrollers verwendet. Das **renderbare Modell,** das von Windows für einen Bewegungscontroller bereitgestellt wird, verwendet die Greifpose als Ursprung und Drehzentrum.

Die Greifpose ist wie folgt speziell definiert:
* Die **Greifposition:** Der Handflächenschwerpunkt, wenn der Controller natürlich hält, nach links oder rechts angepasst, um die Position innerhalb des Greifs zu zentriert. Auf dem Windows Mixed Reality Motion-Controller wird diese Position in der Regel an der Schaltfläche Greiftaste ausgerichtet.
* Die **rechte** Achse der Greifausrichtung: Wenn Sie Ihre Hand vollständig öffnen, um eine flache 5-Finger-Pose zu bilden, den Strahl, der normal zu Ihrer Handfläche ist (vorwärts von der linken Handfläche, rückwärts von der rechten Handfläche).
* Die **Vorwärtsachse** der Greifausrichtung: Wenn Sie die Hand teilweise schließen (als ob Sie den Controller halten), wird der Strahl, der "vorwärts" durch die Achse zeigt, die von Ihren Fingern ohne Daumen gebildet wird.
* Die **Nach-oben-Achse** der Greifausrichtung: Die up-Achse, die durch die Definitionen "Right" und "Forward" impliziert wird.

Sie können über die anbieterübergreifende Eingabe-API *(XR) von Unity auf die Greifpose [zugreifen. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation*) oder über die Windows MR-spezifische API (*sourceState.sourcePose.TryGetPosition/Rotation*, anfordernde Posendaten für den **Greifknoten).**

### <a name="pointer-pose"></a>Zeigerpose

Die **Zeigerpose stellt** die Spitze des Controllers dar, der nach vorne zeigt.

Die vom System bereitgestellte Zeigerdarstellung wird am besten zum Raycast verwendet, wenn Sie das **Controllermodell selbst rendern.** Wenn Sie ein anderes virtuelles Objekt statt des Controllers rendern, z. B. eine virtuelle Kanone, sollten Sie mit einem Strahl zeigen, der für dieses virtuelle Objekt am natürlichsten ist, z. B. einen Strahl, der durch die Maske des von der App definierten Kanonenmodells reist. Da Benutzer das virtuelle Objekt und nicht den physischen Controller sehen können, ist das Verweisen auf das virtuelle Objekt wahrscheinlich natürlicher für Diejenigen, die Ihre App verwenden.

Derzeit ist die Zeigerposition in Unity nur über die MR-spezifische Windows-API *sourceState.sourcePose.TryGetPosition/Rotation* verfügbar, die *InteractionSourceNode.Pointer* als Argument übergeben.

### <a name="openxr"></a>OpenXR 

Sie haben über OpenXR-Eingabeinteraktionen Zugriff auf zwei Sätze von Posen:

* Der Greif stellt zum Rendern von Objekten in der Hand dar.
* Das Ziel ist es, auf die Welt zu zeigen.

Weitere Informationen zu diesem Entwurf und den Unterschieden zwischen den beiden Posen finden Sie unter [OpenXR Specification - Input Subpaths ( OpenXR-Spezifikation : Eingabeunterpfade](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input)).

Von inputFeatureUsages **DevicePosition,** **DeviceRotation,** **DeviceVelocity** und **DeviceAngularVelocity** bereitgestellte Posen stellen alle die OpenXR-Greifposition dar.  InputFeatureUsages im Zusammenhang mit Greifposen sind in [CommonUsages von](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)Unity definiert.

Posen, die von inputFeatureUsages **PointerPosition,** **PointerRotation,** **PointerVelocity** und **PointerAngularVelocity** bereitgestellt werden, stellen alle die OpenXR-Zielpose dar.  Diese InputFeatureUsages sind in eingeschlossenen C#-Dateien nicht definiert, daher müssen Sie Ihre eigenen InputFeatureUsages wie folgt definieren:

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

## <a name="haptics"></a>Haptik

Weitere Informationen zur Verwendung von Obtik im XR-Eingabesystem von Unity finden Sie im [Unity-Handbuch für Unity XR Input –Tics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).

## <a name="controller-tracking-state"></a>Controllernachverfolgungsstatus

Wie die Headsets erfordert der Windows Mixed Reality Motion Controller keine Einrichtung externer Überwachungssensoren. Stattdessen werden die Controller von Sensoren im Headset selbst nachverfolgt.

Wenn der Benutzer die Controller aus dem Sichtfeld des Headsets verschiebt, Windows in den meisten Fällen weiterhin Controllerpositionen abgeleitet. Wenn der Controller die visuelle Nachverfolgung lange genug verloren hat, werden die Positionen des Controllers auf ungefähre Genauigkeitspositionen fallen.

An diesem Punkt sperrt das System den Controller per Body-Lock für den Benutzer und verfolgt dabei die Position des Benutzers, während er sich bewegt, während die echte Ausrichtung des Controllers mithilfe seiner internen Ausrichtungssensoren weiterhin verfügbar ist. Viele Apps, die Controller verwenden, um auf Benutzeroberflächenelemente zu zeigen und sie zu aktivieren, können normal und mit ungefährer Genauigkeit ausgeführt werden, ohne dass der Benutzer dies notiert.

<!-- The best way to get a feel for this is to try it yourself. Check out this video with examples of immersive content that works with motion controllers across various tracking states:

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g] -->

### <a name="reasoning-about-tracking-state-explicitly"></a>Explizite Nachverfolgung des Zustands

Apps, die Positionen basierend auf dem Nachverfolgungszustand unterschiedlich behandeln möchten, können weiter gehen und Eigenschaften im Zustand des Controllers überprüfen, z. B. *SourceLossRisk* und *PositionAccuracy:*

<table>
<tr>
<th> Nachverfolgungsstatus </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>Hohe Genauigkeit</b> </td><td style="background-color: green; color: white"> &lt; 1.0 </td><td style="background-color: green; color: white"> Hoch </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Hohe Genauigkeit (Risiko des Verlusts)</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: green; color: white"> Hoch </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Ungefähre Genauigkeit</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> Ungefähr </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Keine Position</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> Ungefähr </td><td style="background-color: orange"> false</td>
</tr>
</table>

Diese Bewegungscontroller-Nachverfolgungszustände sind wie folgt definiert:
* **Hohe Genauigkeit:** Während sich der Motion Controller innerhalb des Sichtfelds des Headsets befindet, stellt er in der Regel positionen mit hoher Genauigkeit basierend auf der visuellen Nachverfolgung zur Verfügung. Ein sich bewegender Controller, der das Sichtfeld kurzzeitig verlässt oder kurzzeitig von den Headsetsensoren verdeckt wird (z. B. durch die andere Hand des Benutzers), gibt weiterhin eine hohe Genauigkeit zurück, die auf der inertialen Nachverfolgung des Controllers selbst basiert.
* **Hohe Genauigkeit (Risiko des Verlusts):** Wenn der Benutzer den Motion Controller über den Rand des Sichtfelds des Headsets bewegt, kann das Headset die Position des Controllers bald nicht mehr visuell nachverfolgen. Die App weiß, wann der Controller diese FOV-Grenze erreicht hat, indem sie sieht, dass **SourceLossRisk** 1.0 erreicht. An diesem Punkt kann die App Controllergesten anhalten, die einen stabilen Stream von hochwertigen Posen erfordern.
* **Ungefähre Genauigkeit:** Wenn der Controller die visuelle Nachverfolgung lange genug verloren hat, werden die Positionen des Controllers auf ungefähre Genauigkeitspositionen fallen. An diesem Punkt sperrt das System den Controller per Body-Lock für den Benutzer und verfolgt dabei die Position des Benutzers, während er sich bewegt, während die echte Ausrichtung des Controllers mithilfe seiner internen Ausrichtungssensoren weiterhin verfügbar ist. Viele Apps, die Controller verwenden, um auf Benutzeroberflächenelemente zu zeigen und sie zu aktivieren, können normal und mit ungefährer Genauigkeit ausgeführt werden, ohne dass der Benutzer dies notiert. Apps mit höheren Eingabeanforderungen können diesen  Absturz von  Hoher Genauigkeit auf Ungefähre Genauigkeit durch Untersuchen der **Eigenschaft PositionAccuracy** einspüren, um dem Benutzer z. B. während dieser Zeit eine freundlichere Hitbox auf Off-Screen-Zielen zu geben.
* **Keine Position:** Während der Controller über einen längeren Zeitraum mit ungefährer Genauigkeit arbeiten kann, weiß das System manchmal, dass selbst eine körpergesperrte Position derzeit nicht sinnvoll ist. Beispielsweise wurde ein Controller, der eingeschaltet wurde, möglicherweise noch nie visuell beobachtet, oder ein Benutzer kann einen Controller herunter setzen, der dann von einer anderen Person verwendet wird. Zu diesem Zeitpunkt stellt das System der App keine Position zur Verfügung, und *TryGetPosition* gibt FALSE zurück.

## <a name="common-unity-apis-inputgetbuttongetaxis"></a>Allgemeine Unity-APIs (Input.GetButton/GetAxis)

**Namespace:** *UnityEngine*, *UnityEngine.XR*<br>
**Typen:** *Eingabe,* *XR. InputTracking*

Unity verwendet derzeit seine allgemeinen *Input.GetButton/Input.GetAxis-APIs,* um Eingaben für das [Oculus SDK,](https://docs.unity3d.com/Manual/OculusControllers.html)das [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) und Windows Mixed Reality verfügbar zu machen, einschließlich Händen und Motion-Controllern. Wenn Ihre App diese APIs für die Eingabe verwendet, kann sie problemlos Bewegungscontroller über mehrere XR SDKs hinweg unterstützen, einschließlich Windows Mixed Reality.

### <a name="getting-a-logical-buttons-pressed-state"></a>Abrufen des gedrückten Zustands einer logischen Schaltfläche

Um die allgemeinen Unity-Eingabe-APIs zu verwenden, beginnen Sie in der Regel damit, Schaltflächen und Achsen mit logischen Namen im [Unity-Eingabe-Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html)zu verkabeln und eine Schaltfläche oder Achsen-IDs an jeden Namen zu binden. Anschließend können Sie Code schreiben, der auf diesen logischen Schaltflächen-/Achsennamen verweist.

Wenn Sie z. B. die Triggerschaltfläche des linken Bewegungscontrollers der Aktion Senden zuordnen möchten, wechseln Sie zu Bearbeiten **> Project Einstellungen > Eingabe** in Unity, und erweitern Sie die Eigenschaften des Abschnitts Senden unter Achsen. Ändern Sie **die Eigenschaft Positive Schaltfläche** oder Alt Positive **Button** so, dass die **Schaltfläche 14** wie hier angezeigt wird:

![InputManager von Unity](images/unity-input-manager.png)<br>
*Unity InputManager*

Ihr Skript kann dann mit *input.GetButton* auf die Aktion Senden überprüfen:

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
Sie können weitere logische Schaltflächen hinzufügen, indem Sie die **Eigenschaft Größe** unter **Achsen ändern.**

### <a name="getting-a-physical-buttons-pressed-state-directly"></a>Direktes Abrufen des gedrückten Zustands einer physischen Schaltfläche

Sie können auch manuell über ihren vollqualifizierten Namen auf Schaltflächen zugreifen, indem *Sie Input.GetKey verwenden:*

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a>Abrufen der Posen eines Hand- oder Bewegungscontrollers

Sie können mit XR auf die Position und Drehung des Controllers *zugreifen. InputTracking*:

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

> [!NOTE] 
> Der obige Code stellt die Greifpose des Controllers dar (wobei der Benutzer den Controller hält), was zum Rendern einer Maske oder eines Greifs in der Hand des Benutzers oder eines Modells des Controllers selbst nützlich ist.
> 
> Die Beziehung zwischen dieser Greifpose und der Zeigerpose (wo die Spitze des Controllers aufzeigt) kann sich je nach Controller unterscheiden. Derzeit ist der Zugriff auf die Zeigerpose des Controllers nur über die MR-spezifische Eingabe-API möglich, die in den folgenden Abschnitten beschrieben wird.

## <a name="windows-specific-apis-xrwsainput"></a>Windows-spezifische APIs (XR. WSA. Eingabe)

> [!CAUTION]
> Wenn Ihr Projekt eine der XR-Daten verwendet. WSA-APIs werden in zukünftigen Unity-Releases zugunsten des XR SDK aus der Veröffentlichungsphase entfernt. Für neue Projekte wird empfohlen, das XR SDK von Anfang an zu verwenden. Weitere Informationen zum XR-Eingabesystem und zu den [APIs finden Sie hier.](https://docs.unity3d.com/Manual/xr_input.html)

**Namespace:** *UnityEngine.XR.WSA.Input*<br>
**Typen:** *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*

Um ausführlichere Informationen zu Windows Mixed Reality-Handeingaben (für HoloLens) und Motion-Controllern zu erhalten, können Sie die Windows-spezifischen APIs für räumliche Eingaben unter dem *UnityEngine.XR.WSA.Input-Namespace* verwenden. Dadurch können Sie auf zusätzliche Informationen zugreifen, z. B. die Position oder die Quellart, damit Sie Hände und Controller voneinander teilen können.

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a>Abruf des Zustands von Händen und Bewegungscontrollern

Sie können den Zustand dieses Frames für jede Interaktionsquelle (Hand- oder Bewegungscontroller) mithilfe der *GetCurrentReading-Methode* abrufen.

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

Jeder *InteractionSourceState,* den Sie erhalten, stellt eine Interaktionsquelle zum aktuellen Zeitpunkt dar. *InteractionSourceState macht* Informationen wie die folgenden verfügbar:
* Welche [Arten von Pressen](../../design/motion-controllers.md) auftreten (Select/Menu/Grasp/Touchpad/Thumbstick)

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* Andere datenspezifische Daten für Motion-Controller, z. B. die XY-Koordinaten und der berührte Zustand des Touchpads und/oder Fingerabdrucks

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```

* Die InteractionSourceKind, die weiß, ob die Quelle eine Hand oder ein Bewegungscontroller ist

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a>Abruf von vorwärts vorhergesagten Rendering-Posen

* Beim Abruf von Interaktionsquellendaten von Händen und Controllern werden die Posen, die Sie erhalten, für den Moment vorhergesagt, in dem die Photonen dieses Rahmens die Augen des Benutzers erreichen.  Vorausgesagte Posen werden am besten zum **Rendern des** Controllers oder eines gehaltenen Objekts in jedem Frame verwendet.  Wenn Sie eine bestimmte Veröffentlichung mit dem Controller als Ziel verwenden, ist dies am genauesten, wenn Sie die unten beschriebenen Verlaufsereignis-APIs verwenden.

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* Sie können auch die vorhergesagte Kopfpose für diesen aktuellen Frame erhalten.  Wie bei der Quellpose  ist dies nützlich für das Rendern eines Cursors, obwohl die Ausrichtung auf eine bestimmte Press- oder Release-Anweisung am genauesten ist, wenn Sie die unten beschriebenen Verlaufsereignis-APIs verwenden.

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a>Behandeln von Interaktionsquellenereignissen

Um Eingabeereignisse so zu behandeln, wie sie mit ihren genauen Verlaufsdaten der Posen vorkommen, können Sie Interaktionsquelle-Ereignisse verarbeiten, anstatt sie zu fragen.

So behandeln Sie Interaktionsquellenereignisse:
* Registrieren Sie sich für ein *InteractionManager-Eingabeereignis.* Für jeden Interaktionsereignistyp, an dem Sie interessiert sind, müssen Sie es abonnieren.

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* Behandeln Sie das -Ereignis. Nachdem Sie ein Interaktionsereignis abonniert haben, erhalten Sie gegebenenfalls den Rückruf. Im *SourcePressed-Beispiel* ist dies, nachdem die Quelle erkannt wurde und bevor sie freigegeben oder verloren geht.

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

Die verfügbaren Interaktionsquelle-Ereignisse sind:
* *InteractionSourceDetected* (Quelle wird aktiv)
* *InteractionSourceLost* (wird inaktiv)
* *InteractionSourcePressed* (Tippen, Drücken der Schaltfläche oder Äußerung "Auswählen")
* *InteractionSourceReleased* (Ende eines Tippens, Losgelassene Schaltfläche oder Ende der Äußerung "Auswählen")
* *InteractionSourceUpdated* (verschiebt oder ändert einen Zustand auf andere Weise)

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a>Ereignisse für die Historische Zielgruppenadressierung stellen eine genaue Übereinstimmung mit einer Veröffentlichung oder einem Pressen oder Release auf.

Die oben beschriebenen Abruf-APIs geben Ihrer App vorhergesagte Posen.  Die vorhergesagten Posen sind zwar am besten für das Rendern des Controllers oder eines virtuellen Objekts, aber zukünftige Posen sind für die Ausrichtung nicht optimal, aus zwei Wichtigen Gründen:
* Wenn der Benutzer eine Taste auf einem Controller drückt, kann es zu einer Drahtlosen Latenz von ca. 20 ms über Bluetooth, bevor das System die Pressung empfängt.
* Wenn Sie dann eine vorausgesagte Pose verwenden, werden weitere 10-20 ms Vorwärtsvorhersage angewendet, um die Zeit als Ziel zu verwenden, zu der die Photonen des aktuellen Frames die Augen des Benutzers erreichen.

Dies bedeutet, dass Sie beim Abruf eine Quell- oder Kopfpose erhalten, die 30 bis 40 ms vor dem Ort liegt, an dem der Kopf und die Hände des Benutzers tatsächlich zurück waren, als das Drücken oder Dies passiert ist.  Bei HoloLens Handeingaben gibt es zwar keine Drahtlose Übertragungsverzögerung, es gibt jedoch eine ähnliche Verarbeitungsverzögerung, um den Press zu erkennen.

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

## <a name="motion-controllers-in-mrtk"></a>Motion Controller in MRTK

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