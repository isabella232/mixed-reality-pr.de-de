---
title: Gesten in Unity
description: Erfahren Sie, wie Sie mithilfe von XR und allgemeinen Schaltflächen- und Achsen-APIs in Unity aktionen, indem Sie Handgesteneingaben verwenden.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: Gesten, Unity, Anvisiert, Eingabe, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 87666c120686547b1a07f6da41519219d4a47720
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600639"
---
# <a name="gestures-in-unity"></a>Gesten in Unity

Es gibt zwei wichtige Möglichkeiten, aktionen beim [Anvieren in Unity](gaze-in-unity.md)zu ergreifen: [Handgesten](../../design/gaze-and-commit.md#composite-gestures) und [Motion-Controller](../../design/motion-controllers.md) in HoloLens und Immersive HMD. Sie greifen über die gleichen APIs in Unity auf die Daten für beide Quellen räumlicher Eingaben zu.

Unity bietet zwei Hauptmethoden für den Zugriff auf räumliche Eingabedaten für Windows Mixed Reality. Die *gängigen Input.GetButton/Input.GetAxis-APIs* funktionieren über mehrere Unity XR SDKs hinweg, während die *InteractionManager/GestureRecognizer-API,* die für Windows Mixed Reality spezifisch ist, den vollständigen Satz räumlicher Eingabedaten verfügbar macht.

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a>Zusammengesetzte Gesten-APIs auf hoher Ebene (GestureRecognizer)

**Namespace:** *UnityEngine.XR.WSA.Input*<br>
**Typen:** *GestureRecognizer,* *GestureSettings,* *InteractionSourceKind*

Ihre App kann auch zusammengesetzte Gesten auf höherer Ebene für räumliche Eingabequellen, Tippen, Halten, Bearbeiten und Navigationsgesten erkennen. Sie können diese zusammengesetzten Gesten sowohl über [Hände](../../design/gaze-and-commit.md#composite-gestures) als auch [über Motion-Controller](../../design/motion-controllers.md) mithilfe von GestureRecognizer erkennen.

Jedes Gesture-Ereignis auf dem GestureRecognizer stellt sourceKind für die Eingabe sowie den Zielkopfstrahl zum Zeitpunkt des Ereignisses bereit. Einige Ereignisse stellen zusätzliche kontextspezifische Informationen bereit.

Es sind nur wenige Schritte erforderlich, um Gesten mithilfe einer Gestenerkennung zu erfassen:
1. Erstellen einer neuen Gestenerkennung
2. Geben Sie an, auf welche Gesten sie achten sollen.
3. Abonnieren von Ereignissen für diese Gesten
4. Starten der Erfassung von Gesten

### <a name="create-a-new-gesture-recognizer"></a>Erstellen einer neuen Gestenerkennung

Zum Verwenden von *GestureRecognizer* müssen Sie einen *GestureRecognizer* erstellt haben:

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a>Geben Sie an, auf welche Gesten sie achten sollen.

Geben Sie über *SetRecognizableGestures()* an, an welchen Gesten Sie interessiert sind:

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a>Abonnieren von Ereignissen für diese Gesten

Abonnieren Sie Ereignisse für die Gesten, die Sie interessieren.

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
>Navigations- und Bearbeitungsgesten schließen sich für eine Instanz eines *GestureRecognizer* gegenseitig aus.

### <a name="start-capturing-gestures"></a>Starten der Erfassung von Gesten

Standardmäßig überwacht ein *GestureRecognizer* die Eingabe erst, wenn *StartCapturingGestures()* aufgerufen wird. Es ist möglich, dass ein Gestenereignis generiert wird, nachdem *StopCapturingGestures()* aufgerufen wurde, wenn die Eingabe vor dem Frame durchgeführt wurde, in dem *StopCapturingGestures()* verarbeitet wurde. Der *GestureRecognizer* wird sich merken, ob er während des vorherigen Frames, in dem die Geste tatsächlich aufgetreten ist, ein- oder ausgeschaltet war. Daher ist es zuverlässig, die Gestenüberwachung basierend auf dem Anvisieren dieses Frames zu starten und zu beenden.

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a>Erfassungsgesten beenden

So beenden Sie die Gestenerkennung:

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a>Entfernen einer Gestenerkennung

Denken Sie daran, das Abonnement von abonnierten Ereignissen zu kündigen, bevor Sie ein *GestureRecognizer-Objekt* zerstören.

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a>Rendern des Motion Controller-Modells in Unity

![Motion Controller-Modell und Teleportierung](images/motioncontrollertest-teleport-1000px.png)<br>
*Motion Controller-Modell und Teleportation*

Sie können das **MotionController-Prefab** im [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/)verwenden, um Bewegungscontroller in Ihrer App zu rendern, die mit den physischen Controllern übereinstimmen, die Ihre Benutzer halten und formulieren, wenn verschiedene Schaltflächen gedrückt werden.  Dieses Prefab lädt dynamisch das richtige glTF-Modell zur Laufzeit vom installierten Motion Controller-Treiber des Systems.  Es ist wichtig, diese Modelle dynamisch zu laden, anstatt sie manuell im Editor zu importieren, damit Ihre App physisch genaue 3D-Modelle für alle aktuellen und zukünftigen Controller ihrer Benutzer anzeigen kann.

1. Befolgen Sie die [anweisungen Erste Schritte,](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) um das Mixed Reality Toolkit herunterzuladen und ihrem Unity-Projekt hinzuzufügen.
2. Wenn Sie Ihre Kamera im Rahmen der Erste Schritte Schritte durch das *MixedRealityCameraParent-Prefab* ersetzt haben, können Sie losgehen!  Dieses Prefab umfasst das Rendering des Bewegungscontrollers.  Fügen Sie andernfalls *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* aus dem Projektbereich zu Ihrer Szene hinzu.  Sie sollten dieses Prefab als untergeordnetes Element des übergeordneten Objekts hinzufügen, das Sie verwenden, um die Kamera zu bewegen, wenn der Benutzer in Ihrer Szene teleportiert, sodass die Controller mit dem Benutzer verbunden sind.  Wenn Ihre App keine Teleportierung umfasst, fügen Sie einfach das Prefab am Stamm ihrer Szene hinzu.

## <a name="throwing-objects"></a>Auslösen von Objekten

Das Auslösen von Objekten in der virtuellen Realität ist ein schwierigeres Problem, als es auf den ersten Blick erscheinen mag. Wie bei den meisten physisch basierten Interaktionen ist dies sofort offensichtlich und unterbricht die Immersion, wenn das Auslösen im Spiel auf unerwartete Weise erfolgt. Wir haben einige Zeit damit verbracht, tief darüber nachzudenken, wie ein physisch korrektes Auslösensverhalten dargestellt werden kann, und haben einige Richtlinien, die durch Updates unserer Plattform aktiviert wurden, für Sie freigegeben.

Ein Beispiel für die Empfohlene Implementierung von Throwing finden Sie [hier.](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage) Dieses Beispiel folgt diesen vier Richtlinien:
* **Verwenden Sie die *Geschwindigkeit* des Controllers anstelle der Position**. Im November-Update für Windows haben wir eine Änderung des Verhaltens eingeführt, wenn im [Positionsnachverfolgungsstatus "Approximate" (Ungefähr) angezeigt wird.](../../design/motion-controllers.md#controller-tracking-state) In diesem Zustand werden Geschwindigkeitsinformationen über den Controller weiterhin gemeldet, solange wir der Meinung sind, dass seine hohe Genauigkeit, die häufig länger als die Position ist, hoch ist.
* **Integrieren Sie die *Winkelgeschwindigkeit* des Controllers**. Diese Logik ist in der `throwing.cs` Datei in der `GetThrownObjectVelAngVel` statischen Methode innerhalb des oben verknüpften Pakets enthalten:
   1. Da die Winkelgeschwindigkeit erhalten bleibt, muss das ausgelöste Objekt die gleiche Winkelgeschwindigkeit beibehalten wie zum Zeitpunkt der Würfe: `objectAngularVelocity = throwingControllerAngularVelocity;`
   2. Da sich der Mittelpunkt der Massen des ausgelösten Objekts wahrscheinlich nicht am Ursprung der Klammerpose befindet, hat er wahrscheinlich eine andere Geschwindigkeit als die des Controllers im Bezugsrahmen des Benutzers. Der Teil der Geschwindigkeit des Objekts, der auf diese Weise beigetragen hat, ist die sofortige Tangentialgeschwindigkeit des Mittelpunkts der Massen des ausgelösten Objekts um den Controllerursprung. Diese Tangentialgeschwindigkeit ist das Kreuzprodukt der Winkelgeschwindigkeit des Controllers mit dem Vektor, der den Abstand zwischen dem Controllerursprung und dem Mittelpunkt des ausgelösten Objekts darstellt.

      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```

   3. Die Gesamtgeschwindigkeit des ausgelösten Objekts ist die Summe der Geschwindigkeit des Controllers und dieser Tangentialgeschwindigkeit: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`

* **Achten Sie genau auf den *Zeitpunkt,* zu dem wir die Geschwindigkeit anwenden.** Wenn eine Schaltfläche gedrückt wird, kann es bis zu 20 ms dauern, bis das Ereignis über Bluetooth zum Betriebssystem führt. Dies bedeutet: Wenn Sie eine Änderung des Controllerzustands von gedrückt in nicht gedrückt oder umgekehrt abfragen, ist der Controller, den Sie erhalten, informationen, die Sie erhalten, tatsächlich vor dieser Zustandsänderung. Darüber hinaus wird die von unserer Abruf-API dargestellte Controllerhaltung vorausgesagt, um eine wahrscheinliche Pose zum Zeitpunkt der Anzeige des Frames widerzuspiegeln, die in Zukunft mehr als 20 ms sein kann. Dies ist gut für das *Rendern* von gehaltenen Objekten geeignet, aber das Zeitproblem für das *Ziel* des Objekts wird verstärkt, da wir die Kurve für den Moment berechnen, in dem der Benutzer den Würfen losgelassen hat. Glücklicherweise enthält der Zustand mit dem November-Update, wenn ein Unity-Ereignis wie *InteractionSourcePressed* oder *InteractionSourceReleased* gesendet wird, die historischen Posendaten von zurück, als die Schaltfläche gedrückt oder losgelassen wurde.  Um das genaueste Controllerrendering und controllerzielende Ziel während Throws zu erhalten, müssen Sie das Abrufen und Ereignis ordnungsgemäß verwenden, je nach Bedarf:
   * Für **das Controllerrendering** jedes Frames sollte Ihre App das *GameObject* des Controllers an der vorwärts vorhergesagten Controllerhaltung für die Photonenzeit des aktuellen Frames positionieren.  Sie erhalten diese Daten von Unity-Abruf-APIs wie *[XR. InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* oder *[XR. WSA. Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.
   * Für **Controller,** die auf eine Veröffentlichung oder Veröffentlichung ausgerichtet sind, sollte Ihre App Raycasten und Berechnungen basierend auf der historischen Controllerpose für diese Veröffentlichungs- oder Veröffentlichungsereignisse anzeigen und berechnen.  Sie erhalten diese Daten von Unity-Ereignis-APIs wie *[InteractionManager.InteractionSourcePressed.](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*
* **Verwenden Sie die Klammerpose**. Die Winkelgeschwindigkeit und -geschwindigkeit werden relativ zur Klammerhaltung und nicht zur Zeigerhaltung gemeldet.

Das Auslösen von wird sich mit zukünftigen Windows-Updates weiter verbessern. Weitere Informationen dazu finden Sie hier.

## <a name="gesture-and-motion-controllers-in-mrtk"></a>Gesten- und Motion-Controller in MRTK

Sie können über den Eingabe-Manager auf Gesten- und Bewegungscontroller zugreifen.

* [Geste im MRTK](/windows/mixed-reality/mrtk-unity/features/input/gestures)
* [Motion Controller in MRTK](/windows/mixed-reality/mrtk-unity/features/input/controllers)

## <a name="follow-along-with-tutorials"></a>Immer am Ball mit Tutorials

Ausführliche Tutorials mit detaillierteren Anpassungsbeispielen finden Sie in der Mixed Reality Academy:

- [MR-Eingabe 211: Geste](tutorials/holograms-211.md)
- [MR-Eingabe 213: Motion-Controller](../../deprecated/mixed-reality-213.md)

[![MR-Eingabe 213 – Motion-Controller](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)<br>
*MR-Eingabe 213 – Motion-Controller*

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie die von uns festgelegte Unity-Entwicklungsreise verfolgen, befinden Sie sich in der Mitte der MRTK-Kernbausteine. Von hier aus können Sie mit dem nächsten Baustein fortfahren:

> [!div class="nextstepaction"]
> [Hand- und Eye-Tracking](./hand-eye-in-unity.md)

Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:

> [!div class="nextstepaction"]
> [Gemeinsame Erfahrung](shared-experiences-in-unity.md)

Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.

## <a name="see-also"></a>Siehe auch

* [Anvisieren mit dem Kopf und Ausführen](../../design/gaze-and-commit.md)
* [Motion-Controller](../../design/motion-controllers.md)