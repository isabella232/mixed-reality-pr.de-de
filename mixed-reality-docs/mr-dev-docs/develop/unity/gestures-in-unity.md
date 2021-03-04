---
title: Gesten in Unity
description: Erfahren Sie, wie Sie mithilfe von XR und allgemeinen Schaltflächen-und Achsen-APIs Aktionen in Unity mit Hand Stift Eingaben durchführen können.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: Gesten, Unity, Blick, Input, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, mrtk, Mixed Reality Toolkit
ms.openlocfilehash: 4c3db98e3047cdc74663c5cbee1c4607b77008e0
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759081"
---
# <a name="gestures-in-unity"></a>Gesten in Unity

Es gibt zwei wichtige Möglichkeiten, um Ihre [Blicke in Unity](gaze-in-unity.md), [Handgesten](../../design/gaze-and-commit.md#composite-gestures) und [Bewegungs Controllern](../../design/motion-controllers.md) in hololens und immersiven HMD zu ergreifen. Sie greifen über dieselben APIs in Unity auf die Daten für beide Quellen räumlicher Eingaben zu.

Unity bietet zwei Hauptmethoden für den Zugriff auf räumliche Eingabedaten für Windows Mixed Reality. Die gängigen *Input. getbutton/Input. getaxis-* APIs funktionieren über mehrere Unity-XR-SDK hinweg, während die *interaktionmanager/GestureRecognizer* -API speziell für Windows Mixed Reality den vollständigen Satz räumlicher Eingabedaten verfügbar macht.

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a>APIs für zusammengesetzte Gesten auf hoher Ebene (GestureRecognizer)

**Namespace:** *unityengine. XR. WSA. Input*<br>
**Typen**: *GestureRecognizer*, *gesturesettings*, *interaktionsourcekind*

Ihre APP kann auch zusammengesetzte Gesten auf höherer Ebene für räumliche Eingabe Quellen, Tap-, Halt-, Bearbeitungs-und Navigations Gesten erkennen. Mit dem GestureRecognizer können Sie diese zusammengesetzten Gesten sowohl in [Hand](../../design/gaze-and-commit.md#composite-gestures) -als auch in [Bewegungs Controllern](../../design/motion-controllers.md) erkennen.

Jedes Gesten Ereignis für den GestureRecognizer stellt sowohl sourcekind für die Eingabe als auch den Ziel-Head-Strahl zum Zeitpunkt des Ereignisses bereit. Einige Ereignisse bieten zusätzliche kontextspezifische Informationen.

Es sind nur wenige Schritte erforderlich, um Gesten mithilfe einer Gestenerkennung zu erfassen:
1. Erstellen einer neuen Gestenerkennung
2. Legen Sie fest, welche Gesten überwacht werden sollen.
3. Ereignisse für diese Gesten abonnieren
4. Erfassungs Gesten starten

### <a name="create-a-new-gesture-recognizer"></a>Erstellen einer neuen Gestenerkennung

Wenn Sie den *GestureRecognizer* verwenden möchten, müssen Sie einen *GestureRecognizer* erstellt haben:

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a>Legen Sie fest, welche Gesten überwacht werden sollen.

Geben Sie an, für welche Gesten Sie *sich über "*" in "" von "" "

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a>Ereignisse für diese Gesten abonnieren

Abonnieren Sie Ereignisse für die Gesten, an denen Sie interessiert sind.

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
>Navigations-und Manipulations Gesten schließen sich gegenseitig für eine Instanz eines *GestureRecognizer* aus.

### <a name="start-capturing-gestures"></a>Erfassungs Gesten starten

Standardmäßig überwacht ein *GestureRecognizer* die Eingabe erst, wenn *startcapturinggesten ()* aufgerufen wird. Möglicherweise wird ein Gesten Ereignis generiert, nachdem *stopcapturinggesten ()* aufgerufen wurde, wenn Eingaben vor dem Frame durchgeführt wurden, in dem *stopcapturinggesten ()* verarbeitet wurde. Der *GestureRecognizer* weiß, ob er während des vorherigen Frames, in dem die Geste tatsächlich aufgetreten ist, ein-oder ausgeschaltet war, und daher ist es zuverlässig, die Gesten Überwachung auf der Grundlage der Anzeige Ziele dieses Frames zu starten und zu beenden.

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a>Erfassungs Gesten nicht mehr

So verhindern Sie die Gestenerkennung:

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a>Entfernen einer Gestenerkennung

Denken Sie daran, abonnierte Ereignisse abzubestellen, bevor Sie ein *GestureRecognizer* -Objekt zerstören.

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

![Motion Controller-Modell und-teleportierung](images/motioncontrollertest-teleport-1000px.png)<br>
*Motion Controller-Modell und-teleportierung*

Zum Rendering von Bewegungs Controllern in Ihrer APP, die den physischen Controllern entsprechen, die die Benutzer als verschiedene Schaltflächen verwenden, die Sie verwenden, können Sie die **vorfab von "mutioncontroller** " im [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/)verwenden.  Dieser Prefab lädt das korrekte gltf-Modell zur Laufzeit dynamisch aus dem installierten Motion Controller-Treiber des Systems.  Es ist wichtig, dass diese Modelle dynamisch geladen werden, anstatt Sie manuell in den Editor zu importieren, damit Ihre APP physisch genaue 3D-Modelle für alle aktuellen und zukünftigen Controller anzeigt, die Ihre Benutzer möglicherweise haben.

1. Befolgen Sie [die Anweisungen für die ersten](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) Schritte, um das Mixed Reality Toolkit herunterzuladen und es Ihrem Unity-Projekt hinzuzufügen.
2. Wenn Sie Ihre Kamera durch das *mixedrealitycameraparent* -präfab im Rahmen der Schritte für die ersten Schritte ersetzt haben, können Sie es tun!  Dieses präfab umfasst das Rendern von Bewegungs Controllern.  Andernfalls fügen Sie *Assets/holotoolkit/Input/Prefabs/mutioncontrollers. Prefab* aus dem Projektbereich in die Szene ein.  Sie sollten diese Prefab als untergeordnetes Element eines beliebigen übergeordneten Objekts hinzufügen, das Sie verwenden, um die Kamera zu bewegen, wenn der Benutzer in der Szene Teleports verwendet, sodass die Controller mit dem Benutzer zusammenkommen.  Wenn Ihre APP keine teleportierung umfasst, fügen Sie einfach die vorfab im Stammverzeichnis Ihrer Szene hinzu.

## <a name="throwing-objects"></a>Auslösen von Objekten

Das Auslösen von Objekten in Virtual Reality ist ein schwierigeres Problem, als es möglicherweise zum ersten Mal erscheint. Wie bei den meisten physisch basierenden Interaktionen verhält es sich, wenn das Auslösen im Spiel unerwartet funktioniert, sofort offensichtlich und unterbricht das eintauchen. Wir haben einige Zeit damit verbracht, ein physisch korrektes auslösverhalten darzustellen, und haben einige Richtlinien, die über Updates auf unserer Plattform aktiviert wurden, für Sie freigeben möchten.

Ein Beispiel für die Implementierung von "throw" finden Sie [hier](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage). Dieses Beispiel befolgt diese vier Richtlinien:
* **Verwenden Sie die *Geschwindigkeit* des Controllers anstelle der Position**. Im November-Update für Windows haben wir eine Änderung des Verhaltens eingeführt, wenn der [ungefähre Status der Positionsüberwachung ("ungefähre"](../../design/motion-controllers.md#controller-tracking-state)) ist. In diesem Zustand werden Velocity-Informationen über den Controller weiterhin gemeldet, solange wir der hohen Genauigkeit glauben, was häufig länger ist als die Position mit hoher Genauigkeit.
* **Integrieren Sie die *Winkelgeschwindigkeit* des Controllers**. Diese Logik ist in der- `throwing.cs` Datei in der `GetThrownObjectVelAngVel` statischen-Methode innerhalb des oben verknüpften Pakets enthalten:
   1. Wenn die Angular-Geschwindigkeit beibehalten wird, muss das ausgelöste Objekt dieselbe Angular-Geschwindigkeit wie in der Zeit der throw-Ausnahme beibehalten: `objectAngularVelocity = throwingControllerAngularVelocity;`
   2. Da sich der Mittelpunkt der Masse des ausgelösten Objekts wahrscheinlich nicht am Ursprung der Ziehpunkt-Pose befindet, weist es wahrscheinlich eine andere Geschwindigkeit auf als die des Controllers im Frame des Verweises des Benutzers. Der Teil der auf diese Weise beigetragenen Geschwindigkeit des Objekts ist die sofortige tangential Geschwindigkeit des Mittelpunkts der Masse des ausgelösten Objekts um den Controller Ursprung. Diese tangential-Geschwindigkeit ist das Kreuz Produkt der Angular-Geschwindigkeit des Controllers mit dem Vektor, der den Abstand zwischen dem Controller Ursprung und dem Mittelpunkt der Masse des ausgelösten Objekts darstellt.

      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```

   3. Die Gesamtgeschwindigkeit des ausgelösten Objekts ist die Summe der Geschwindigkeit des Controllers und der tangential Geschwindigkeit: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`

* Achten **Sie genau auf die *Zeit* , zu der wir die Geschwindigkeit anwenden**. Wenn eine Schaltfläche gedrückt wird, kann es bis zu 20 ms dauern, bis das Ereignis durch Bluetooth bis zum Betriebssystem hochskalieren kann. Dies bedeutet Folgendes: Wenn Sie eine Änderung des Controller Zustands von gedrückte in nicht gedrückt oder umgekehrt durchführt, werden die Informationen, die Sie mit dem Controller erhalten, tatsächlich vor dieser Zustandsänderung angezeigt. Darüber hinaus wird die von unserer Abruf-API dargestellte Controller Darstellung vorhergesagt, um zu dem Zeitpunkt, zu dem der Rahmen angezeigt wird, eine wahrscheinliche Darstellung darzustellen, die in der Zukunft mehr als 20 ms betragen kann. Dies eignet sich gut für das *Rendern* von gehaltenen Objekten, aber ist unser Zeitproblem für das *Ziel des Objekts* , da wir den Weg für den Zeitpunkt berechnen, zu dem der Benutzer den Throw losgelassen hat. Wenn Sie mit dem November-Update ein Unity-Ereignis wie *interaktionsourcepressed* oder *interaktionsourcereleasing* gesendet haben, enthält der Zustand glücklicherweise die Vergangenheits Daten von hinten, wenn die Schaltfläche gedrückt oder freigegeben wurde.  Um das präzisere Controller Rendering und die Zielplattform für das Ausführen von Triggeroptionen zu erhalten, müssen Sie nach Bedarf Abruf-und Ereignis Ereignisse ordnungsgemäß verwenden:
   * Für den Controller, der die einzelnen Frames **rendert** , sollte Ihre APP das *gameobject* des Controllers an der vorwärts Gesagten Controller Darstellung für die Photon-Zeit des aktuellen Frames positionieren.  Sie erhalten diese Daten von Unity-Abruf-APIs wie *[XR. Inputtracking. getlocalposition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* oder *[XR. WSA. Input. interaktionmanager. getcurrentreading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.
   * Für den Controller, der auf eine Presse oder ein Release **abzielt** , sollte Ihre APP auf der Grundlage der Verlaufs Controller-Pose für das Press-oder releaseereignis auf der Grundlage der Verlaufs Controller-  Sie erhalten diese Daten aus den Unity-Ereignis-APIs, wie z. b. *[interaktionmanager. interaktionsourcepressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.
* **Verwenden Sie die** Ziehpunkt-Pose. Winkelgeschwindigkeit und-Geschwindigkeit werden relativ zur Zieh Punkt Pose, nicht zum Darstellen von Zeigern, angezeigt.

Das auslösen wird mit zukünftigen Windows-Updates weiter verbessern, und Sie können davon ausgehen, dass Sie hier weitere Informationen finden.

## <a name="gesture-and-motion-controllers-in-mrtk"></a>Gesten-und Bewegungs Controller in mrtk

Sie können über den Eingabe-Manager auf Gesten-und Bewegungs Controller zugreifen.
* [Gesten in mrtk](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/gestures.md)
* [Motion Controller in mrtk](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/controllers.md)


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