---
ms.openlocfilehash: 05e2b87383bbc91b7fd8785230152e3549f4b22d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2021
ms.locfileid: "104719980"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + openxr](#tab/openxr)

Das Mixed Reality openxr-Plug-in stellt grundlegende Anker Funktionen durch eine Implementierung von Unity **aranchormanager** bereit. Informationen zu den Grundlagen von aranchor in arfoundation finden Sie unter [arfoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html). 

# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Windows-XR-Plug-in](#tab/winxr)

Das Mixed Reality openxr-Plug-in stellt grundlegende Anker Funktionen durch eine Implementierung von Unity **aranchormanager** bereit. Informationen zu den Grundlagen von aranchor in arfoundation finden Sie unter [arfoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).

# <a name="legacy-wsa"></a>[Legacy-WSA](#tab/wsa)

## <a name="building-a-world-scale-experience"></a>Entwickeln eines weltweiten Erlebnisses

**Namespace:** *unityengine. XR. WSA*<br>
**Typ:** *worldanchor*

Für echte **Welt weite** Oberflächen in hololens, mit denen Benutzer mehr als 5 Meter bewegen können, benötigen Sie neue Techniken, die über diejenigen hinausgehen, die für Raum Skalierungen verwendet werden. Ein wichtiges Verfahren, das Sie verwenden, besteht darin, einen [räumlichen Anker](../../../design/coordinate-systems.md#spatial-anchors) zu erstellen, mit dem ein Cluster von holograms genau in der physischen Welt gesperrt wird, unabhängig davon, wie weit der Benutzer rostet hat, und [diese Hologramme in späteren Sitzungen erneut finden](../../../design/coordinate-systems.md#spatial-anchor-persistence).

In Unity erstellen Sie einen räumlichen Anker durch Hinzufügen der Unity-Komponente **worldanchor** zu einem gameobject-Objekt.

### <a name="adding-a-world-anchor"></a>Hinzufügen eines Welt Ankers

Um einen Welt Anker hinzuzufügen, müssen `AddComponent<WorldAnchor>()` Sie für das Spielobjekt mit der Transformation, die Sie in der realen Welt verankern möchten, anrufen.

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

Das ist alles! Dieses Spielobjekt wird nun an seinem aktuellen Speicherort in der physischen Welt verankert. möglicherweise werden die Unity-Weltkoordinaten im Laufe der Zeit leicht angepasst, um die physische Ausrichtung sicherzustellen. Weitere Informationen finden Sie in einer zukünftigen App-Sitzung unter [Laden eines Welt Ankers](#loading-a-worldanchor) .

### <a name="removing-a-world-anchor"></a>Entfernen eines Welt Ankers

Wenn Sie nicht mehr möchten, dass das gameobject-Objekt an eine physische Welt Stelle gesperrt ist, und Sie dieses Frame nicht verschieben möchten, können Sie einfach "zerstören" für die "World Anchor"-Komponente aufzurufen.

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

Wenn Sie das gameobject-Objekt in diesen Frame verschieben möchten, müssen Sie stattdessen destroyimmediate aufzurufen.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>Verschieben eines weltweit verankerten gameobject

Gameobject kann nicht verschoben werden, wenn ein Welt Anker darauf liegt. Wenn Sie das gameobject für diesen Frame verschieben müssen, müssen Sie Folgendes ausführen:

1. Destroyimmediate der Welt Anker Komponente
2. Verschieben des gameobject
3. Fügen Sie dem gameobject eine neue Welt Anker Komponente hinzu.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>Behandeln von Änderungen an der Anwendungs Freundlichkeit

Ein worldanchor kann nicht in der physischen Welt zu einem bestimmten Zeitpunkt einstellbar sein. Wenn dies der Fall ist, wird Unity die Transformation des verankerten Objekts nicht aktualisieren. Dies kann sich auch ändern, während eine app ausgeführt wird. Wenn Sie die Änderung der loerability nicht bewältigen, wird das Objekt nicht am richtigen physischen Speicherort der Welt angezeigt.

So erhalten Sie eine Benachrichtigung über die Änderungen der Änderungen:

1. Ontrackingchanged-Ereignis abonnieren
2. Behandeln des Ereignisses

Das **ontrackingchanged** -Ereignis wird immer dann aufgerufen, wenn sich der zugrunde liegende räumliche Anker zwischen dem Zustand "verwendbar" und "nicht zu verwendbar" ändert.

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

Behandeln Sie dann das-Ereignis:

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

Manchmal werden Anker sofort gefunden. In diesem Fall wird diese islocated-Eigenschaft des Ankers auf true festgelegt, wenn addComponent <WorldAnchor> () zurückgibt. Folglich wird das ontrackingchanged-Ereignis nicht ausgelöst. Ein sauberes Muster besteht darin, den ontrackingchanged-Handler mit dem ursprünglichen ISSE-Zustand nach dem Anfügen eines Ankers aufzurufen.

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```