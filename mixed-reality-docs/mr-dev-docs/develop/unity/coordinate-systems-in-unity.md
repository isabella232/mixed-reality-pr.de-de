---
title: Koordinatensysteme in Unity
description: Hier erfahren Sie, wie Sie in Unity Mixed Reality-Erfahrungen im Bereich "Platz", "Stehend", "Raum" und "Welt" erstellen.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Koordinatensystem, Raumkoordinatensystem, nur ausrichtungsbezogen, skaliert, stehend, Raumskalierung, Weltskala, 360 Grad, stehend, Stehend, Raum, Welt, Skalierung, Position, Ausrichtung, Unity, Anker, Raumanker, Weltanker, Weltsperren, Weltsperren, Körpersperren, Body-Locking, Nachverfolgungsverlust, Locatability, Begrenzungen, Aktueller, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 91b1adf6dcf1c54d0d29a02bfb97ac4674a87c88
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528750"
---
# <a name="coordinate-systems-in-unity"></a>Koordinatensysteme in Unity

Windows Mixed Reality unterstützt Apps für eine Vielzahl von Erfahrungsskalen– von apps mit ausrichtungsbasierter Und-Skalierung bis hin zu Apps im Raummaßstab. Auf HoloLens können Sie weitergehen und weltweit skalierende Apps erstellen, mit denen Benutzer mehr als 5 Meter gehen und eine gesamte Etage eines Gebäudes und darüber hinaus erkunden können.

Der erste Schritt beim Erstellen einer Mixed Reality-Erfahrung in Unity besteht darin, Koordinatensysteme zu verstehen [und die Benutzeroberfläche auszuwählen, die](../../design/coordinate-systems.md) Ihre App als Ziel verwenden soll.

## <a name="building-an-orientation-only-or-seated-scale-experience"></a>Erstellen einer reinen ausrichtungsbasierten oder skalierten Benutzeroberfläche

**Namespace:** *UnityEngine.XR*<br>
**Typ:** *XRDevice*

Zum Erstellen einer **reinen ausrichtungsbasierten** oder **besetzen Benutzeroberfläche** müssen Sie Unity auf den Typ Stationärer Nachverfolgungsbereich festlegen. Der ortsaufstärkungsraum legt das Weltkoordinatensystem von Unity fest, um den [stationären Bezugsrahmen](../../design/coordinate-systems.md#spatial-coordinate-systems)nachzuverfolgen. Im Nachverfolgungsmodus "Stationär" werden Inhalte, die im Editor direkt vor der Standardposition der Kamera platziert werden (forward ist -Z), vor dem Benutzer angezeigt, wenn die App gestartet wird.

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

**Namespace:** *UnityEngine.XR*<br>
**Typ:** *InputTracking*

Für eine reine **Ausrichtungserfahrung,** z. B. einen 360-Grad-Video-Viewer (bei dem Positionskopfupdates die Tante verfälschen würden), können Sie dann [XR festlegen. InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) auf TRUE:

```cs
InputTracking.disablePositionalTracking = true;
```

Für eine **benutzerdefinierte Benutzeroberfläche** können Sie XR aufrufen, damit der Benutzer später den stammseitigen Ursprung erhalten [kann. InputTracking.Recenter-Methode:](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a>Erstellen einer Erfahrung im Stehend- oder Raummaßstab

**Namespace:** *UnityEngine.XR*<br>
**Typ:** *XRDevice*

Für eine **Erfahrung im Stehend-** oder **Raummaßstab** müssen Sie Inhalte relativ zum Boden platzieren. Sie können die Grundfläche des **[](../../design/coordinate-systems.md#spatial-coordinate-systems)** Benutzers mithilfe der räumlichen Stufe festlegen, die den vom Benutzer definierten Ursprung auf Bodenebene und die optionale Raumgrenze darstellt, die während der ersten Ausführung eingerichtet wurde.

Um sicherzustellen, dass Unity mit seinem Weltkoordinatensystem auf Bodenebene ausgeführt wird, können Sie festlegen und testen, ob Unity den Raumtyp RoomScale-Nachverfolgung verwendet:

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```
* Wenn SetTrackingSpaceType "true" zurückgibt, hat Unity sein Weltkoordinatensystem erfolgreich umgeschaltet, um den Stageframe [des Verweises zu verfolgen.](../../design/coordinate-systems.md#spatial-coordinate-systems)
* Wenn SetTrackingSpaceType false zurückgibt, konnte Unity nicht zum Stageframe des Verweises wechseln, wahrscheinlich weil der Benutzer in seiner Umgebung keinen Boden eingerichtet hat. Ein falscher Rückgabewert ist zwar nicht üblich, aber dies kann passieren, wenn die Phase in einem anderen Raum eingerichtet ist und das Gerät in den aktuellen Raum verschoben wird, ohne dass der Benutzer eine neue Stufe eingerichtet hat.

Nachdem Ihre App den Raumtyp RoomScale-Nachverfolgung erfolgreich gesetzt hat, werden Inhalte auf der Ebene y=0 auf dem Boden angezeigt. Der Ursprung bei 0, 0, 0 ist der spezifische Ort im Boden, an dem der Benutzer während der Einrichtung des Raums mit -Z für die Vorwärtsrichtung steht, die er während des Setups hatte.

**Namespace:** *UnityEngine.Experimental.XR*<br>
**Typ:** *Grenze*

Im Skriptcode können Sie dann die TryGetGeometry-Methode für den UnityEngine.Experimental.XR.Boundary-Typ aufrufen, um ein Begrenzungspolygon zu erhalten, und dabei den Begrenzungstyp TrackedArea angeben. Wenn der Benutzer eine Grenze definiert hat (Sie erhalten eine Liste von  Scheitellinien), ist es sicher, dem Benutzer eine Raumerfahrung zu bieten, in der er die von Ihnen erstellten Szenen durchläuft.

> [!NOTE]
> Das System rendert die Grenze automatisch, wenn sich der Benutzer ihr nähert. Ihre App muss dieses Polygon nicht verwenden, um die Grenze selbst zu rendern. Sie können ihre Szenenobjekte jedoch mithilfe dieses Begrenzungpolygons gestalten, um sicherzustellen, dass der Benutzer diese Objekte physisch erreichen kann, ohne teleportieren zu müssen:

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a>Erstellen einer weltweiten Erfahrung

**Namespace:** *UnityEngine.XR.WSA*<br>
**Typ:** *WorldAnchor*

Für echte **Welterfahrungen** auf HoloLens, die Es Benutzern ermöglichen, mehr als 5 Meter zu erkunden, benötigen Sie neue Techniken, die über diejenigen hinausgehen, die für Raumerfahrungen verwendet werden. Eine wichtige Technik, die Sie verwenden, besteht darin, einen [Raumanker](../../design/coordinate-systems.md#spatial-anchors) zu erstellen, um einen Cluster von Hologrammen genau in der physischen Welt zu sperren, unabhängig davon, wie weit der Benutzer sich entfernt hat, und [diese Hologramme dann in späteren Sitzungen wieder](../../design/coordinate-systems.md#spatial-anchor-persistence)zu finden.

In Unity erstellen Sie einen Raumanker, indem Sie die **Unity-Komponente WorldAnchor** einem GameObject hinzufügen.

### <a name="adding-a-world-anchor"></a>Hinzufügen eines Weltankers

Um einen Weltanker hinzuzufügen, rufen Sie AddComponent <WorldAnchor> () für das Spielobjekt mit der Transformation auf, die Sie in der realen Welt verankern möchten.

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

Das ist alles! Dieses Spielobjekt wird nun an seiner aktuellen Position in der physischen Welt verankert. Möglicherweise werden die Unity-Weltkoordinaten im Laufe der Zeit leicht angepasst, um die physische Ausrichtung sicherzustellen. Verwenden Sie [Persistenz,](persistence-in-unity.md) um diesen verankerten Speicherort in einer zukünftigen App-Sitzung erneut zu finden.

### <a name="removing-a-world-anchor"></a>Entfernen eines Weltankers

Wenn Sie nicht mehr möchten, dass das GameObject an einem physischen Ort der Welt gesperrt ist und nicht beabsichtigen, es in diesem Frame zu verschieben, können Sie einfach Destroy für die World Anchor-Komponente aufrufen.

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

Wenn Sie das GameObject in diesen Frame verschieben möchten, müssen Sie stattdessen DestroyImmediate aufrufen.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>Verschieben eines world Anchored GameObject

GameObject-Objekte können nicht verschoben werden, während sich ein World Anchor darauf befindet. Wenn Sie das GameObject in diesen Frame verschieben müssen, müssen Sie Folgendes:
1. DestroyImmediate the World Anchor component
2. Verschieben des GameObject
3. Fügen Sie dem GameObject eine neue World Anchor-Komponente hinzu.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>Behandeln von Änderungen an der Verkettbarkeit

Ein WorldAnchor ist in der physischen Welt zu einem bestimmten Zeitpunkt möglicherweise nicht zu finden. In diesem Fall aktualisiert Unity die Transformation des verankerten Objekts nicht. Dies kann sich auch ändern, während eine App ausgeführt wird. Wenn die Änderung der Verkettbarkeit nicht behandelt wird, wird das Objekt nicht an der richtigen physischen Position auf der Welt angezeigt.

So werden Sie über Änderungen bei der Verkettung benachrichtigt:
1. Abonnieren des OnTrackingChanged-Ereignisses
2. Behandeln des Ereignisses

Das **OnTrackingChanged-Ereignis** wird immer dann aufgerufen, wenn sich der zugrunde liegende Raumanker zwischen einem Zustand ändert, in dem er nicht verkettet ist oder nicht.

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

Behandeln Sie dann das -Ereignis:

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

Manchmal werden Anker sofort gefunden. In diesem Fall wird diese isLocated-Eigenschaft des Ankers auf TRUE festgelegt, wenn AddComponent <WorldAnchor> () zurückgegeben wird. Daher wird das OnTrackingChanged-Ereignis nicht ausgelöst. Ein sauberes Muster wäre das Aufrufen des OnTrackingChanged-Handlers mit dem anfänglichen IsLocated-Zustand nach dem Anfügen eines Ankers.

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a>Geräteübergreifendes Freigeben von Ankern

Verwenden <a href="/azure/spatial-anchors/overview" target="_blank">Sie Azure Spatial Anchors,</a> um einen permanenten Cloudanker aus einem lokalen WorldAnchor zu erstellen, den Ihre App dann auf mehreren HoloLens-, iOS- und Android-Geräten finden kann.  Indem ein gemeinsamer Raumanker auf mehreren Geräten gemeinsam verwendet wird, kann jeder Benutzer Inhalte sehen, die relativ zu diesem Anker an derselben physischen Position gerendert werden.  Dies ermöglicht gemeinsame Erfahrungen in Echtzeit.

Probieren Sie die fünfminütigen Schnellstartanleitungen zu Azure Spatial Anchors Unity aus, um mit dem Erstellen gemeinsamer Erfahrungen in <a href="/azure/spatial-anchors/unity-overview" target="_blank">Unity zu beginnen.</a>

Sobald Sie azure Spatial Anchors haben, können Sie Anker in Unity erstellen <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">und suchen.</a>

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie die Von uns an den Prüfpunkt für die Unity-Entwicklung 2017 2017 2016 2016 durchgeführte Entwicklung mithilfe von Prüfpunkten fortsetzen, sind Sie gerade dabei, die wichtigsten Mixed Reality zu erkunden. Von hier aus können Sie mit dem nächsten Baustein fortfahren:

> [!div class="nextstepaction"]
> [Anvisieren](gaze-in-unity.md)

Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:

> [!div class="nextstepaction"]
> [Gemeinsame Erfahrung](shared-experiences-in-unity.md)

Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.

## <a name="see-also"></a>Weitere Informationen
* [Erfahrungsskala](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [Räumliche Phase](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Verfolgbarkeitsverlust in Unity](tracking-loss-in-unity.md)
* [Raumanker](../../design/spatial-anchors.md)
* [Persistenz in Unity](persistence-in-unity.md)
* [Gemeinsame Erlebnisse in Unity](shared-experiences-in-unity.md)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK für Unity</a>