---
ms.openlocfilehash: 2ab12da2da926d906a5ae57868f152ecc2b13d90
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2021
ms.locfileid: "123244301"
---
# <a name="world-locking-tools-recommended"></a>[World Locking Tools (Empfohlen)](#tab/wlt)

Standardmäßig stellt World Locking Tools das Unity-Koordinatensystem relativ zur physischen Welt sitzungsübergreifend auf Geräten wieder her, die persistierende lokale Raumanker unterstützen. Damit ein Hologramm nach dem Beenden und erneuten Ausführen der Anwendung an der gleichen Stelle in der physischen Welt angezeigt wird, muss das Hologramm nur noch einmal dieselbe Pose aufweisen.

![Kontextkomponente "World Locking" im Unity-Inspektor](../../images/world-locking-tools-img-02.png)

Wenn die Anwendung eine feiner kontrollierte Steuerung benötigt, können **automatisches Speichern** und **automatisches Laden** im Inspektor deaktiviert und persistenz über ein Skript verwaltet werden, wie im [Abschnitt "Persistenz" der Dokumentation](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/Concepts/Advanced/Persistence.html)beschrieben.

Lokale Ankerpersistenz wird derzeit nur für die HoloLens Gerätefamilie unterstützt. Unter Android und iOS sowie HoloLens wird die Sitzungsübergreifende Persistenz von Koordinatenbereichen sowie die geräteübergreifende Freigabe von Koordinatenbereichen über eine Integration in Azure Spatial Anchors unterstützt. Es gibt eine Vielzahl [weiterer Informationen und Beispiele](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/WLT_ASA.html) zur Verwendung von World Locking Tools zusammen mit Azure Spatial Anchors.

# <a name="aranchormanager"></a>[ARAnchorManager](#tab/anchorstore)

Mit einer zusätzlichen API namens **XRAnchorStore** können Anker zwischen Sitzungen beibehalten werden. XRAnchorStore ist eine Darstellung der gespeicherten Anker auf einem Gerät. Anker können aus **ARAnchors** in der Unity-Szene beibehalten, aus dem Speicher in neue **ARAnchors** geladen oder aus dem Speicher gelöscht werden.

> [!NOTE]
> Diese Anker müssen auf demselben Gerät gespeichert und geladen werden. Geräteübergreifender Ankerspeicher wird in einer zukünftigen Version über Azure Spatial Anchors unterstützt.

### <a name="namespaces"></a>Namespaces

Für **Unity 2020 und OpenXR:** 

``` cs
using Microsoft.MixedReality.ARSubsystems.XRAnchorStore
```

oder **Unity 2019/2020 + Windows XR-Plug-In:** 

```cs 
using UnityEngine.XR.WindowsMR.XRAnchorStore
```

### <a name="public-methods"></a>Öffentliche Methoden

```cs 
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

### <a name="getting-an-anchor-store-reference"></a>Abrufen eines Ankerspeicherverweis 

Verwenden Sie zum Laden von XRAnchorStore mit **Unity 2020 und OpenXR** die Erweiterungsmethode für das XRAnchorSubsystem, das Subsystem eines ARAnchorManager:

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

Um XRAnchorStore mit **Unity 2019/2020 und dem Windows XR-Plug-In** zu laden, verwenden Sie die Erweiterungsmethode für das XRReferencePointSubsystem (Unity 2019) oder XRAnchorSubsystem (Unity 2020), das Subsystem eines ARReferencePointManager/ARAnchorManager:

```cs
// Unity 2019 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem);

// Unity 2020 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem);
```

### <a name="loading-an-anchor-store"></a>Laden eines Ankerspeichers

Um einen Ankerspeicher in **Unity 2020 und OpenXR** zu laden, greifen Sie wie folgt über das Subsystem eines ARAnchorManager darauf zu:

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

oder mit **Unity 2019/2020 und dem Windows XR-Plug-In:**

``` cs
// Unity 2019
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();

// Unity 2020
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

Ein vollständiges Beispiel für das Beibehalten/Aufheben von Ankern finden Sie im Skript Anchors -> Anchors Sample GameObject und AnchorsSample.cs in der [Mixed Reality OpenXR-Plug-In-Beispielszene:](../../xr-project-setup.md#unity-sample-projects-for-openxr-and-hololens-2)

![Screenshot des im Unity-Editor geöffneten Hierarchiebereichs mit hervorgehobenen Ankerbeispielen](../../images/openxr-features-img-04.png)

![Screenshot des im Unity-Editor geöffneten Inspektorbereichs mit hervorgehobener Anchors-Beispielskript](../../images/openxr-features-img-05.png)

# <a name="worldanchor"></a>[WorldAnchor](#tab/worldanchor)

**WorldAnchorStore** ist der Schlüssel zum Erstellen holografischer Erfahrungen, bei denen Hologramme in bestimmten realen Positionen über Instanzen der Anwendung hinweg verbleiben. Benutzer können dann einzelne Hologramme an jeder gewünschten Stelle anheften und sie später bei vielen Verwendungsmöglichkeiten Ihrer App an der gleichen Stelle finden.

**Namespace:** *UnityEngine.XR.WSA.Persistence*<br>
**Klasse:** *WorldAnchorStore*

Mit WorldAnchorStore können Sie den Speicherort von WorldAnchor sitzungsübergreifend beibehalten. Um Hologramme tatsächlich sitzungsübergreifend beizubehalten, müssen Sie Ihre GameObjects, die einen bestimmten Weltanker verwenden, separat nachverfolgen. Es ist oft sinnvoll, einen GameObject-Stamm mit einem Weltanker zu erstellen und untergeordnete Hologramme mit einem lokalen Positionsoffset zu verankern.

So laden Sie Hologramme aus vorherigen Sitzungen:

1. Abrufen von WorldAnchorStore
2. Laden von App-Daten im Zusammenhang mit dem Weltanker, der Ihnen die ID des Weltankers liefert
3. Laden eines Weltankers aus seiner ID

So speichern Sie Hologramme für zukünftige Sitzungen:

1. Abrufen von WorldAnchorStore
2. Speichern eines Weltankers, der eine ID angibt
3. Speichern von App-Daten im Zusammenhang mit dem Weltanker zusammen mit einer ID

### <a name="getting-the-worldanchorstore"></a>Abrufen des WorldAnchorStore

Sie sollten einen Verweis auf WorldAnchorStore beibehalten, damit Sie wissen, wann er bereit ist, einen Vorgang auszuführen. Da dies ein asynchroner Aufruf ist, möchten Sie möglicherweise nach dem Start Aufrufen von:

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

StoreLoaded ist in diesem Fall unser Handler für den Fall, dass das Laden von WorldAnchorStore abgeschlossen wurde:

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

Wir haben nun einen Verweis auf den WorldAnchorStore, den wir zum Speichern und Laden bestimmter World Anchors verwenden.

### <a name="saving-a-worldanchor"></a>Speichern eines WorldAnchor

Um zu speichern, müssen wir einfach benennen, was wir speichern, und es im WorldAnchor übergeben, den wir zuvor erhalten haben, als wir speichern möchten. Hinweis: Beim Versuch, zwei Anker in derselben Zeichenfolge zu speichern, tritt ein Fehler auf (speichern. Speichern gibt FALSE zurück. Löschen Sie den vorherigen Speicher, bevor Sie den neuen speichern:

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

### <a name="loading-a-worldanchor"></a>Laden eines WorldAnchor

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

Darüber hinaus können wir store verwenden. Delete() zum Entfernen eines Zuvor gespeicherten und gespeicherten Ankers. Clear(), um alle zuvor gespeicherten Daten zu entfernen.

### <a name="enumerating-existing-anchors"></a>Aufzählen vorhandener Anker

Rufen Sie GetAllIds auf, um zuvor gespeicherte Anker zu ermitteln.

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>Beibehalten von Hologrammen für mehrere Geräte

Sie können <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> verwenden, um einen permanenten Cloudanker aus einem lokalen WorldAnchor zu erstellen, den Ihre App dann auf mehreren HoloLens-, iOS- und Android-Geräten finden kann, auch wenn diese Geräte nicht gleichzeitig vorhanden sind.  Da Cloudanker persistent sind, können mehrere Geräte im Laufe der Zeit jeweils Inhalte sehen, die relativ zu diesem Anker an demselben physischen Ort gerendert werden.

Probieren Sie die fünfminütigen <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity-Schnellstarts</a>aus, um mit dem Erstellen freigegebener Erfahrungen in Unity zu beginnen.

Sobald Sie mit Azure Spatial Anchors ausgeführt werden, können Sie <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Anker in Unity erstellen und suchen.</a>