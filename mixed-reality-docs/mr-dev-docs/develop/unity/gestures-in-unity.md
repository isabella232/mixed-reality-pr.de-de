---
title: Gesten in Unity
description: Erfahren Sie, wie Sie mithilfe von XR und gängigen Schaltflächen- und Achsen-APIs Aktionen beim Anvisieren in Unity mithilfe von Handgesteneingaben ergreifen.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: Gesten, Unity, Anvisierten, Eingabe, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 8dd6b64dd0bb52e64515a43d69713ecc5dc6bcec203a987568f7c25ac492a864
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214759"
---
# <a name="gestures-in-unity"></a>Gesten in Unity

Es gibt zwei wichtige Möglichkeiten, aktionen für Ihre Blicke [in Unity](gaze-in-unity.md)zu [ergreifen:](../../design/gaze-and-commit.md#composite-gestures) Handgesten und Motion-Controller [in](../../design/motion-controllers.md) HoloLens immersivem HMD. Sie greifen auf die Daten für beide Quellen räumlicher Eingaben über die gleichen APIs in Unity zu.

Unity bietet zwei primäre Möglichkeiten für den Zugriff auf räumliche Eingabedaten für Windows Mixed Reality. Die allgemeinen *Input.GetButton/Input.GetAxis-APIs* funktionieren über mehrere Unity XR SDKs hinweg, während die für Windows Mixed Reality spezifische *InteractionManager/GestureRecognizer-API* den vollständigen Satz räumlicher Eingabedaten verfügbar macht.

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a>Zusammengesetzte Gesten-APIs auf hoher Ebene (GestureRecognizer)

**Namespace:** *UnityEngine.XR.WSA.Input*<br>
**Typen:** *GestureRecognizer,* *GestureSettings,* *InteractionSourceKind*

Ihre App kann auch zusammengesetzte Gesten höherer Ebene für räumliche Eingabequellen, Tippen, Halten, Manipulation und Navigationsgesten erkennen. Sie können diese zusammengesetzten [](../../design/gaze-and-commit.md#composite-gestures) Gesten sowohl über Hände als auch über [Bewegungscontroller](../../design/motion-controllers.md) erkennen, indem Sie den GestureRecognizer verwenden.

Jedes Gestenereignis auf dem GestureRecognizer stellt das SourceKind für die Eingabe sowie den Zielkopfstrahl zum Zeitpunkt des Ereignisses zur Seite. Einige Ereignisse stellen zusätzliche kontextspezifische Informationen zur Verfügung.

Es sind nur einige Schritte erforderlich, um Gesten mithilfe einer Gestenerkennung zu erfassen:
1. Erstellen einer neuen Gestenerkennung
2. Angeben der zu achtenden Gesten
3. Abonnieren von Ereignissen für diese Gesten
4. Starten der Erfassung von Gesten

### <a name="create-a-new-gesture-recognizer"></a>Erstellen einer neuen Gestenerkennung

Um den *GestureRecognizer verwenden zu* können, müssen Sie einen *GestureRecognizer erstellt haben:*

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a>Angeben der zu achtenden Gesten

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
>Navigations- und Manipulationsgesten schließen sich bei einer Instanz eines *GestureRecognizer* gegenseitig aus.

### <a name="start-capturing-gestures"></a>Starten der Erfassung von Gesten

Standardmäßig überwacht ein *GestureRecognizer die* Eingabe erst, wenn *StartCapturingGestures()* aufgerufen wird. Es ist möglich, dass ein Gestenereignis generiert wird, nachdem *StopCapturingGestures()* aufgerufen wurde, wenn die Eingabe vor dem Frame durchgeführt wurde, in dem *StopCapturingGestures()* verarbeitet wurde. Der *GestureRecognizer* kann sich merken, ob er während des vorherigen Frames ein- oder ausgeschaltet war, in dem die Geste tatsächlich aufgetreten ist. Daher ist es zuverlässig, die Gestenüberwachung basierend auf dem Ziel dieses Rahmens zu starten und zu beenden.

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a>Beenden der Erfassung von Gesten

So beenden Sie die Gestenerkennung:

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a>Entfernen einer Gestenerkennung

Denken Sie daran, abonnierte Ereignisse zu kündigen, bevor Sie ein *GestureRecognizer-Objekt* zerstören.

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

![Motion Controller-Modell und Teleportation](images/motioncontrollertest-teleport-1000px.png)<br>
*Motion Controller-Modell und Teleportation*

Zum Rendern von Motion-Controllern in Ihrer App, die mit den physischen Controllern übereinstimmen, die Ihre Benutzer halten und artikulieren, wenn verschiedene Schaltflächen gedrückt werden, können Sie das **MotionController-Prefab** im Mixed Reality [Toolkit verwenden.](https://github.com/Microsoft/MixedRealityToolkit-Unity/)  Dieses Prefab lädt dynamisch das richtige glTF-Modell zur Laufzeit aus dem installierten Motion Controller-Treiber des Systems.  Es ist wichtig, diese Modelle dynamisch zu laden, anstatt sie manuell in den Editor zu importieren, damit Ihre App physisch genaue 3D-Modelle für alle aktuellen und zukünftigen Controller ihrer Benutzer anzeigen kann.

1. Befolgen Sie [Erste Schritte](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) Anweisungen, um das Mixed Reality Toolkit herunterzuladen und ihrem Unity-Projekt hinzuzufügen.
2. Wenn Sie Ihre Kamera im Rahmen der schritte der Erste Schritte durch das *MixedRealityCameraParent-Prefab* ersetzt haben, können Sie losgehen!  Dieses Prefab umfasst das Rendern des Bewegungscontrollers.  Fügen Sie *andernfalls Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* aus dem Project ihrer Szene hinzu.  Sie sollten dieses Prefab als untergeordnetes Element eines übergeordneten Objekts hinzufügen, das Sie zum Bewegen der Kamera verwenden, wenn der Benutzer in Ihrer Szene teleportiert, sodass die Controller mit dem Benutzer zusammenkommen.  Wenn Ihre App keine Teleportierung umfasst, fügen Sie einfach das Prefab im Stammverzeichnis Ihrer Szene hinzu.

## <a name="throwing-objects"></a>Auslösen von Objekten

Das Auslösen von Objekten in der virtuellen Realität ist ein schwierigeres Problem, als es auf den ersten Blick erscheinen mag. Wie bei den meisten physisch basierten Interaktionen ist es sofort offensichtlich und unterbricht das Immersion, wenn das Auslösen im Spiel auf unerwartete Weise vor sich geht. Wir haben einige Zeit lang tief darüber nachzudenken, wie ein physisch korrektes Throwingverhalten repräsentiert werden kann, und wir haben einige Richtlinien entwickelt, die durch Aktualisierungen unserer Plattform aktiviert wurden und die wir für Sie freigeben möchten.

Ein Beispiel dafür, wie wir die Implementierung von throwing empfehlen, finden Sie [hier.](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage) Dieses Beispiel folgt diesen vier Richtlinien:
* **Verwenden Sie die Geschwindigkeit des *Controllers anstelle* der Position**. Im November-Update für Windows haben wir eine Änderung des Verhaltens eingeführt, wenn sich der Positionsnachverfolgungsstatus ["Approximate" (Ungefähr) beträgt.](../../design/motion-controllers.md#controller-tracking-state) In diesem Zustand werden Geschwindigkeitsinformationen über den Controller weiterhin gemeldet, solange wir der Meinung sind, dass seine hohe Genauigkeit, die häufig länger als die Position ist, eine hohe Genauigkeit bleibt.
* **Integrieren Sie *die Winkelgeschwindigkeit des* Controllers**. Diese Logik ist alle in der Datei `throwing.cs` in der `GetThrownObjectVelAngVel` statischen Methode innerhalb des oben verknüpften Pakets enthalten:
   1. Wenn die Winkelgeschwindigkeit erhalten bleibt, muss das ausgelöste Objekt die gleiche Winkelgeschwindigkeit wie zum Zeitpunkt der Auslöse behalten: `objectAngularVelocity = throwingControllerAngularVelocity;`
   2. Da sich der Mittelpunkt der Massen des ausgelösten Objekts wahrscheinlich nicht am Ursprung der Greifpose befindet, hat es wahrscheinlich eine andere Geschwindigkeit als der Controller im Referenzrahmen des Benutzers. Der Auf diese Weise beigetragene Teil der Geschwindigkeit des Objekts ist die sofortige Tangentialgeschwindigkeit des Massenkerns des ausgelösten Objekts um den Controllerursprung. Diese Tangentialgeschwindigkeit ist das Kreuzprodukt der Winkelgeschwindigkeit des Controllers mit dem Vektor, der den Abstand zwischen dem Controllerursprung und dem Mittelpunkt der Massen des ausgelösten Objekts darstellt.

      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```

   3. Die Gesamtgeschwindigkeit des ausgelösten Objekts ist die Summe der Geschwindigkeit des Controllers und dieser Tangentialgeschwindigkeit: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`

* **Achten Sie besonders auf den *Zeitpunkt,* zu dem wir die Geschwindigkeit anwenden.** Wenn eine Schaltfläche gedrückt wird, kann es bis zu 20 ms dauern, bis dieses Ereignis über Bluetooth Betriebssystem hochlädt. Dies bedeutet, dass die Controller-Poseinformationen, die Sie damit erhalten, vor dieser Zustandsänderung tatsächlich vor dieser Zustandsänderung liegen, wenn Sie eine Controllerzustandsänderung von gedrückt in nicht gedrückt oder umgekehrt abstimmen. Darüber hinaus wird die controller-Pose, die von unserer Abruf-API dargestellt wird, vorwärts vorhergesagt, um eine wahrscheinliche Pose zum Zeitpunkt der Anzeige des Frames widerzubekommen, der in der Zukunft mehr als 20 ms sein kann. Dies ist  gut für das Rendern  von gehaltenen Objekten, aber wir lösen unser Zeitproblem für das Ziel des Objekts, da wir die Kurve für den Moment berechnen, in dem der Benutzer die Würfe freigegeben hat. Glücklicherweise enthält der Zustand mit dem November-Update, wenn ein Unity-Ereignis wie *InteractionSourcePressed* oder *InteractionSourceReleased* gesendet wird, die Verlaufsdaten von zurück, als die Schaltfläche gedrückt oder freigegeben wurde.  Um das genaueste Controllerrendering und Controlleradressierung während Der Throws zu erhalten, müssen Sie abruf- und ereignisgenau verwenden:
   * Für **das Controllerrendering** der einzelnen Frames sollte Ihre App das *GameObject* des Controllers an der vorhergesagten Controllerposition für die Photonenzeit des aktuellen Frames positionieren.  Sie erhalten diese Daten von Unity-Abruf-APIs wie *[XR. InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* oder *[XR. WSA. Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.
   * Für **Controller, die** auf eine Veröffentlichung oder eine Veröffentlichung abzielen, sollte Ihre App raycasten und Vorhersage anhand der historischen Controllerpose für dieses Press- oder Releaseereignis berechnen.  Sie erhalten diese Daten von Unity-Ereignis-APIs wie *[InteractionManager.InteractionSourcePressed.](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*
* **Verwenden Sie die Greifpose**. Angular Geschwindigkeit und Geschwindigkeit werden relativ zur Greifpose und nicht zur Zeigerpose gemeldet.

Das Auslösen von wird sich mit zukünftigen updates Windows verbessern, und Sie können hier weitere Informationen dazu erwarten.

## <a name="gesture-and-motion-controllers-in-mrtk"></a>Gesten- und Bewegungscontroller im MRTK

Sie können über den Eingabe-Manager auf gesten- und bewegungscontroller zugreifen.

* [Geste im MRTK](/windows/mixed-reality/mrtk-unity/features/input/gestures)
* [Motion Controller in MRTK](/windows/mixed-reality/mrtk-unity/features/input/controllers)

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