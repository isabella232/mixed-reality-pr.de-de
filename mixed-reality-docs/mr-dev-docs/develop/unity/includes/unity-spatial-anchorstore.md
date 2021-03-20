---
ms.openlocfilehash: bb2df8c85dd05981c1438bdb076b0aad16c7efd7
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2021
ms.locfileid: "104719880"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + openxr](#tab/openxr)

Eine zusätzliche API mit dem Namen " **xranchorstore** " ermöglicht, dass Anker zwischen Sitzungen beibehalten werden. Der xranchorstore ist eine Darstellung der gespeicherten Anker auf einem Gerät. Anker können von **aranchor** in der Unity-Szene persistent gespeichert, aus dem Speicher in neue **aranchor** geladen oder aus dem Speicher gelöscht werden.

> [!NOTE]
> Diese Anker müssen auf demselben Gerät gespeichert und geladen werden. Der Geräte übergreifende Anker Speicher wird in einer zukünftigen Version durch Azure Spatial Anchor unterstützt.

``` cs
public class Microsoft.MixedReality.ARSubsystems.XRAnchorStore
{
    // A list of all persisted anchors, which can be loaded.
    public IReadOnlyList<string> PersistedAnchorNames { get; }

    // Clear all persisted anchors
    public void Clear();

    // Load a single persisted anchor by name. The ARAnchorManager will create this new anchor and report it in
    // the ARAnchorManager.anchorsChanged event. The TrackableId returned here is the same TrackableId the
    // ARAnchor will have when it is instantiated.
    public TrackableId LoadAnchor(string name);

    // Attempts to persist an existing ARAnchor with the given TrackableId to the local store. Returns true if
    // the storage is successful, false otherwise.
    public bool TryPersistAnchor(string name, TrackableId trackableId);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

Zum Laden von xranchorstore stellt das Plug-in eine Erweiterungsmethode für das xranchorsubsystem bereit, das Subsystem von aranchormanager:

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

Um diese Erweiterungsmethode zu verwenden, greifen Sie über das Subsystem von aranchormanager wie folgt auf Sie zu:

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

Ein vollständiges Beispiel für persistente/nicht persistente Anker finden Sie im Beispiel für die Anker-> Anker Sample gameobject und das anchorssample. cs-Skript in der [Beispiel Szene für das Mixed Reality openxr-Plug](../openxr-getting-started.md#hololens-2-samples)-in:

![Screenshot des Bereichs "Hierarchie" im Unity-Editor mit hervorgehobenem Anker Beispiel](../images/openxr-features-img-04.png)

![Screenshot des Bereichs "Inspector" im Unity-Editor mit hervorgehobenem Anker Beispielskript](../images/openxr-features-img-05.png)

# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Windows-XR-Plug-in](#tab/winxr)

Eine API mit dem Namen " **xranchorstore** " ermöglicht es, dass Anker zwischen Sitzungen beibehalten werden. Der xranchorstore ist eine Darstellung der gespeicherten Anker auf einem Gerät. Anker können von **aranchor** in der Unity-Szene persistent gespeichert, aus dem Speicher in neue **aranchor** geladen oder aus dem Speicher gelöscht werden.

> [!NOTE]
> Diese Anker müssen auf demselben Gerät gespeichert und geladen werden. Der Geräte übergreifende Anker Speicher wird in einer zukünftigen Version durch Azure Spatial Anchor unterstützt.

``` cs
public class UnityEngine.XR.WindowsMR.XRAnchorStore
{
    // A list of all persisted anchors, which can be loaded.
    public IReadOnlyList<string> PersistedAnchorNames { get; }

    // Clear all persisted anchors
    public void Clear();

    // Load a single persisted anchor by name. The ARAnchorManager will create this new anchor and report it in
    // the ARAnchorManager.anchorsChanged event. The TrackableId returned here is the same TrackableId the
    // ARAnchor will have when it is instantiated.
    public TrackableId LoadAnchor(string name);

    // Attempts to persist an existing ARAnchor with the given TrackableId to the local store. Returns true if
    // the storage is successful, false otherwise.
    public bool TryPersistAnchor(TrackableId id, string name);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

Zum Laden von xranchorstore stellt das Plug-in eine Erweiterungsmethode für xrreferencepointsubsystem (Unity 2019) oder xranchorsubsystem (Unity 2020) dar, das Subsystem von arreferencepointmanager/aranchormanager:

``` cs
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem); // Unity 2019
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem); // Unity 2020
```

Um diese Erweiterungsmethode zu verwenden, greifen Sie über das Subsystem von aranchormanager wie folgt für Unity 2019 auf Sie zu:

``` cs
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();
```

oder für Unity 2020:

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

# <a name="legacy-wsa"></a>[Legacy-WSA](#tab/wsa)

**Worldanchorstore** ist der Schlüssel für die Erstellung von Holographic-Erfahrungen, bei denen Hologramme in den einzelnen Anwendungs Instanzen in bestimmten realen Positionen bleiben. Benutzer können dann jedes beliebige Hologramm an die gewünschte Stelle anheften und später auf der gleichen Stelle über viele Verwendungszwecke Ihrer APP suchen.

**Namespace:** *unityengine. XR. WSA. Persistenz*<br>
**Klasse:** *worldanchorstore*

Mit worldanchorstore können Sie den Speicherort von worldanchor Sitzungs übergreifend beibehalten. Sie müssen ihre gameobjects-Objekte, die einen bestimmten Welt Anker verwenden, separat nachverfolgen, um Hologramme in mehreren Sitzungen dauerhaft beizubehalten. Häufig ist es sinnvoll, einen gameobject-Stamm mit einem Welt Anker zu erstellen und untergeordnete Hologramme mit einem lokalen Positions Offset zu verankern.

So laden Sie holograms aus vorherigen Sitzungen:

1. Verschaffen Sie sich den worldanchorstore
2. Laden von App-Daten in Bezug auf den World-Anker, der Ihnen die ID des Welt Ankers liefert
3. Einen Welt Anker aus seiner ID laden

So speichern Sie Hologramme für zukünftige Sitzungen:

1. Verschaffen Sie sich den worldanchorstore
2. Speichern eines Welt Ankers, der eine ID angibt
3. Speichern von App-Daten, die sich auf den Welt Anker beziehen, sowie eine ID

### <a name="getting-the-worldanchorstore"></a>Der worldanchorstore wird erhalten.

Sie sollten einen Verweis auf den worldanchorstore behalten, damit Sie wissen, wann er bereit ist, einen Vorgang auszuführen. Da es sich hierbei um einen asynchronen-Befehl handelt, der möglicherweise unmittelbar nach dem Start aufgerufen wird, sollten Sie Folgendes aufrufen:

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

Storeloaded ist in diesem Fall der Handler für den Fall, dass der worldanchorstore das Laden abgeschlossen hat:

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

Wir haben nun einen Verweis auf den worldanchorstore, den wir verwenden werden, um bestimmte weltanker zu speichern und zu laden.

### <a name="saving-a-worldanchor"></a>Speichern von worldanchor

Zum Speichern müssen wir einfach den Namen der Speicherung benennen und Sie an den worldanchor übergeben, den wir vor dem Speichern erhalten haben. Hinweis: Wenn Sie versuchen, zwei Anker in derselben Zeichenfolge zu speichern, tritt ein Fehler auf (speichern. Save gibt false zurück). Löschen Sie die vorherige Speicherung, bevor Sie die neue speichern:

```cs
private void SaveGame()
{
    // Save data about holograms positioned by this world anchor
    if (!this.savedRoot) // Only Save the root once
    {
           this.savedRoot = this.store.Save("rootGameObject", anchor);
           Assert(this.savedRoot);
    }
}
```

### <a name="loading-a-worldanchor"></a>Laden von worldanchor

Und zum Laden:

```cs
private void LoadGame()
{
    // Save data about holograms positioned by this world anchor
    this.savedRoot = this.store.Load("rootGameObject", rootGameObject);
    if (!this.savedRoot)
    {
        s// We didn't actually have the game root saved! We have to re-place our objects or start over
    }
}
```

Wir können außerdem "Store" verwenden. Delete () um einen Anker zu entfernen, den wir zuvor gespeichert und gespeichert haben. Löschen Sie (), um alle zuvor gespeicherten Daten zu entfernen.

### <a name="enumerating-existing-anchors"></a>Auflisten vorhandener Anker

Um zuvor gespeicherte Anker zu ermitteln, müssen Sie getallids aufrufen.

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>Beibehalten von holograms für mehrere Geräte

Sie können <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial</a> Anchor verwenden, um einen permanenten cloudanker von einem lokalen worldanchor zu erstellen, den Ihre APP dann über mehrere hololens-, IOS-und Android-Geräte hinweg finden kann, auch wenn diese Geräte nicht gleichzeitig vorhanden sind.  Da cloudananker permanent sind, können mehrere Geräte im Lauf der Zeit jeweils Inhalte sehen, die relativ zu diesem Anker am gleichen physischen Standort gerendert werden.

Um mit der Einführung von freigegebenen Erfahrungen in Unity zu beginnen, testen Sie die fünfminütigen <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchor Unity-Schnellstarts</a>.

Sobald Sie mit räumlichen Azure-Ankern arbeiten, können Sie <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Anker in Unity erstellen und lokalisieren</a>.
