---
ms.openlocfilehash: e4ada87db2d9e483758030bf1bbe56dbacd7664ae7e1921540c0c7abfe14a7c7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208855"
---
# <a name="world-locking-tools-recommended"></a>[World Locking Tools (empfohlen)](#tab/wlt)

Es wird empfohlen, World Locking Tools mit dem neuen Mixed Reality FeatureTool zu installieren. Nachdem Sie das Mixed Reality-Featuretool über den folgenden Link heruntergeladen haben, wählen Sie die neueste Version von **WLT Core** aus dem Abschnitt **World Locking Tools (World Locking Tools)** aus:

![Mixed Reality Featureauswahlfenster des Featuretools mit ausgewählter Option "World Locking Tools"](../../images/spatial-anchors-setup-img-01.png)

> [!div class="nextstepaction"]
> [Installieren von World Locking Tools mit dem MR Feature Tool](../../welcome-to-mr-feature-tool.md)

### <a name="automated-setup"></a>Automatisierte Einrichtung

Wenn Ihr Projekt einsatzbereit ist, führen Sie das Hilfsprogramm zum Konfigurieren der Szene aus Mixed Reality **Toolkit > Utilities > World Locking Tools aus:**

![Unity-Editor mit ausgewähltem Mixed Reality Toolkit](../../images/world-locking-configuration-img-01.jpeg)

> [!IMPORTANT]
> Das Hilfsprogramm Szene konfigurieren kann jederzeit erneut ausführen werden. Beispielsweise sollte sie erneut ausführen werden, wenn das AR-Ziel von Legacy in XR SDK geändert wurde. Wenn die Szene bereits ordnungsgemäß konfiguriert ist, hat die Ausführung des Hilfsprogramms keine Auswirkungen.

### <a name="visualizers"></a>Schnellansichten

Während der frühen Entwicklung kann das Hinzufügen von Schnellansichten hilfreich sein, um sicherzustellen, dass WLT eingerichtet ist und ordnungsgemäß funktioniert. Sie können zur Produktionsleistung entfernt werden, oder wenn sie aus irgendeinem Grund nicht mehr benötigt werden, indem Sie das Hilfsprogramm Schnellansichten entfernen verwenden. Weitere Informationen zu den Schnellansichten finden Sie in der [Tools-Dokumentation.](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/Tools.html#visualizers)

# <a name="aranchormanager"></a>[ARAnchorManager](#tab/anchorstore)

Das Mixed Reality OpenXR-Plug-In stellt grundlegende Ankerfunktionen über eine Implementierung von **ARFoundation ARAnchorManager** von Unity zur Verfügung. Informationen zu den Grundlagen zu ARAnchors in ARFoundation finden Sie im [ARFoundation-Handbuch für AR Anchor Manager.](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html) 

# <a name="worldanchor"></a>[WorldAnchor](#tab/worldanchor)

## <a name="building-a-world-scale-experience"></a>Erstellen einer weltweiten Erfahrung

**Namespace:** *UnityEngine.XR.WSA*<br>
**Typ:** *WorldAnchor*

Für echte **Welterfahrungen** auf HoloLens, die es Benutzern ermöglichen, mehr als 5 Meter zu erkunden, benötigen Sie neue Techniken, die über diejenigen hinausgehen, die für Raumerfahrungen verwendet werden. Eine wichtige Methode, die Sie [](../../../../design/coordinate-systems.md#spatial-anchors) verwenden, ist das Erstellen eines Raumanker, um einen Cluster von Hologrammen genau in der physischen Welt zu sperren, unabhängig davon, wie weit der Benutzer roamingt, und diese Hologramme dann in späteren Sitzungen wieder zu [finden.](../../../../design/coordinate-systems.md#spatial-anchor-persistence)

In Unity erstellen Sie einen Raumanker, indem Sie einem GameObject die **Unity-Komponente WorldAnchor** hinzufügen.

### <a name="adding-a-world-anchor"></a>Hinzufügen eines Weltankers

Um einen Weltanker hinzuzufügen, rufen Sie für das Spielobjekt mit der Transformation auf, `AddComponent<WorldAnchor>()` die Sie in der realen Welt verankern möchten.

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

Das ist alles! Dieses Spielobjekt wird nun an seiner aktuellen Position in der physischen Welt verankert. Möglicherweise sehen Sie, dass sich die Unity-Weltkoordinaten im Laufe der Zeit leicht anpassen, um die physische Ausrichtung sicherzustellen. Informationen zum [Erneuten Finden dieses verankerten Speicherorts](#loading-a-worldanchor) in einer zukünftigen App-Sitzung finden Sie unter Laden eines Weltankers.

### <a name="removing-a-world-anchor"></a>Entfernen eines Weltankers

Wenn Sie das GameObject nicht mehr an einen physischen Ort in der Welt versperren möchten und nicht beabsichtigen, es in diesen Rahmen zu verschieben, können Sie für die Komponente "World Anchor" einfach Destroy aufrufen.

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

Wenn Sie das GameObject in diesem Frame verschieben möchten, müssen Sie stattdessen DestroyImmediate aufrufen.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>Verschieben eines in der Welt verankerten GameObject

GameObject-Objekte können nicht verschoben werden, während ein World Anchor darauf ist. Wenn Sie das GameObject in diesem Frame verschieben müssen, müssen Sie:

1. DestroyImmediate the World Anchor component
2. Verschieben des GameObject
3. Fügen Sie dem GameObject eine neue World Anchor-Komponente hinzu.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>Behandeln von Änderungen an der Verkettbarkeit

Ein WorldAnchor kann in der physischen Welt zu einem bestimmten Zeitpunkt möglicherweise nicht verkettet werden. In diesem Fall aktualisiert Unity die Transformation des verankerten Objekts nicht. Dies kann sich auch ändern, während eine App ausgeführt wird. Wenn die Änderung der Verkettbarkeit nicht behandelt wird, wird das Objekt nicht an der richtigen physischen Position auf der Welt angezeigt.

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