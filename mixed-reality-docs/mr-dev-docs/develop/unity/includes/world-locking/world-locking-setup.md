---
ms.openlocfilehash: 047a77259d78ba8ea68002a5142080971900e305
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2021
ms.locfileid: "123244295"
---
# <a name="world-locking-tools-recommended"></a>[World Locking Tools (Empfohlen)](#tab/wlt)

Es wird empfohlen, die World Locking Tools mit dem neuen Mixed Reality Feature Tool zu installieren. Nachdem Sie das Mixed Reality Feature-Tool über den folgenden Link heruntergeladen haben, wählen Sie im Abschnitt **World Locking Tools** die neueste Version von **WLT Core** aus:

![Mixed Reality Feature tool feature selection window with World Locking Tools selected (Featureauswahlfenster des Featuretools mit ausgewählter Option "World Locking Tools" (Weltsperrtools)](../../images/spatial-anchors-setup-img-01.png)

> [!div class="nextstepaction"]
> [Installieren von World Locking Tools mit dem MR Feature Tool](../../welcome-to-mr-feature-tool.md)

### <a name="automated-setup"></a>Automatisierte Einrichtung

Wenn Ihr Projekt einsatzbereit ist, führen Sie das Hilfsprogramm zum Konfigurieren der Szene aus **Mixed Reality > World Locking Tools** aus:

![Unity-Editor mit ausgewähltem Menü "Mixed Reality Toolkit"](../../images/world-locking-configuration-img-01.jpeg)

> [!IMPORTANT]
> Das Hilfsprogramm "Szene konfigurieren" kann jederzeit erneut ausführen. Sie sollte beispielsweise erneut gestartet werden, wenn das AR-Ziel von Legacy in XR SDK geändert wurde. Wenn die Szene bereits ordnungsgemäß konfiguriert ist, hat die Ausführung des Hilfsprogramms keine Auswirkungen.

### <a name="visualizers"></a>Schnellansichten

Während der frühen Entwicklung kann das Hinzufügen von Schnellansichten hilfreich sein, um sicherzustellen, dass WLT eingerichtet ist und ordnungsgemäß funktioniert. Sie können aus Gründen der Produktionsleistung entfernt werden, oder wenn sie aus irgendeinem Grund nicht mehr benötigt werden, indem Sie das Hilfsprogramm Schnellansichten entfernen verwenden. Weitere Informationen zu den Schnellansichten finden Sie in der [Tools-Dokumentation.](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/Tools.html#visualizers)

# <a name="aranchormanager"></a>[ARAnchorManager](#tab/anchorstore)

Das Mixed Reality OpenXR-Plug-In stellt grundlegende Ankerfunktionen über eine Implementierung von ARFoundation **ARAnchorManager** von Unity bereit. Informationen zu den Grundlagen zu ARAnchors in ARFoundation finden Sie im [ARFoundation-Handbuch für AR Anchor Manager.](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html) 

# <a name="worldanchor"></a>[WorldAnchor](#tab/worldanchor)

## <a name="building-a-world-scale-experience"></a>Erstellen einer weltweiten Erfahrung

**Namespace:** *UnityEngine.XR.WSA*<br>
**Typ:** *WorldAnchor*

Für echte **Welterfahrungen** auf HoloLens, die Es Benutzern ermöglichen, mehr als 5 Meter zu erkunden, benötigen Sie neue Techniken, die über diejenigen hinausgehen, die für Raumerfahrungen verwendet werden. Eine wichtige Technik, die Sie verwenden, besteht darin, einen [Raumanker](../../../../design/coordinate-systems.md#spatial-anchors) zu erstellen, um einen Cluster von Hologrammen genau in der physischen Welt zu sperren, unabhängig davon, wie weit der Benutzer sich entfernt hat, und diese [Hologramme dann in späteren Sitzungen wieder](../../../../design/coordinate-systems.md#spatial-anchor-persistence)zu finden.

In Unity erstellen Sie einen Raumanker, indem Sie die **Unity-Komponente WorldAnchor** einem GameObject hinzufügen.

### <a name="adding-a-world-anchor"></a>Hinzufügen eines Weltankers

Um einen Weltanker hinzuzufügen, rufen `AddComponent<WorldAnchor>()` Sie für das Spielobjekt mit der Transformation auf, die Sie in der realen Welt verankern möchten.

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

Das ist alles! Dieses Spielobjekt wird nun an seiner aktuellen Position in der physischen Welt verankert. Möglicherweise werden die Unity-Weltkoordinaten im Laufe der Zeit leicht angepasst, um die physische Ausrichtung sicherzustellen. Weitere Informationen finden Sie unter [Laden eines Weltankers,](#loading-a-worldanchor) um diesen verankerten Speicherort in einer zukünftigen App-Sitzung erneut zu finden.

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

GameObject-Objekte können nicht verschoben werden, während sich ein World Anchor darauf befindet. Wenn Sie das GameObject in diesen Frame verschieben müssen, müssen Sie folgendes unternehmen:

1. DestroyImmediate the World Anchor component
2. Verschieben des GameObject
3. Fügen Sie dem GameObject eine neue World Anchor-Komponente hinzu.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>Verarbeiten von Locatability-Änderungen

Ein WorldAnchor ist in der physischen Welt zu einem Zeitpunkt möglicherweise nicht verwendbar. In diesem Fall aktualisiert Unity die Transformation des verankerten Objekts nicht. Dies kann sich auch ändern, während eine App ausgeführt wird. Wenn die Änderung der Locatability nicht behandelt wird, wird das Objekt nicht an der richtigen physischen Position der Welt angezeigt.

So werden Sie über Änderungen an der Locatability benachrichtigt:

1. Abonnieren des OnTrackingChanged-Ereignisses
2. Behandeln des Ereignisses

Das **OnTrackingChanged-Ereignis** wird immer dann aufgerufen, wenn sich der zugrunde liegende Raumanker zwischen dem Zustand "Locatable" und "Not Locatable" ändert.

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

Behandeln Sie dann das Ereignis:

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

Manchmal werden Anker sofort gefunden. In diesem Fall wird diese isLocated-Eigenschaft des Ankers auf TRUE festgelegt, wenn AddComponent <WorldAnchor> () zurückgegeben wird. Daher wird das OnTrackingChanged-Ereignis nicht ausgelöst. Ein sauberes Muster wäre, ihren OnTrackingChanged-Handler mit dem anfänglichen IsLocated-Zustand nach dem Anfügen eines Ankers aufzurufen.

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```