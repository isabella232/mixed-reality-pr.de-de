---
ms.openlocfilehash: 96da41f28533c227fb106d8842907747f34098ec
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "110349986"
---
# <a name="world-locking-tools-recommended"></a>[World Locking Tools (empfohlen)](#tab/wlt)

Standardmäßig stellen world locking Tools das Unity-Koordinatensystem in Bezug auf die physische Welt sitzungsübergreifend wieder auf. Dies bedeutet, dass das Hologramm nur wieder dieselbe Pose haben muss, damit ein Hologramm nach dem Beenden und erneuten Ausführen der Anwendung an der gleichen Stelle in der physischen Welt angezeigt wird.

![Kontextkomponente "Weltsperrung" im Unity-Inspektor](../../images/world-locking-tools-img-02.png)

Wenn die Anwendung eine feiner geschaltete Steuerung benötigt, werden **auto-save** und **auto-load** möglicherweise im Inspektor deaktiviert, und persistenz wird über ein Skript verwaltet, wie im Abschnitt persistenz der Dokumentation [beschrieben.](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/Concepts/Advanced/Persistence.html)

# <a name="aranchormanager"></a>[ARAnchorManager](#tab/anchorstore)

Mit einer zusätzlichen API namens **XRAnchorStore** können Anker zwischen Sitzungen beibehalten werden. Der XRAnchorStore ist eine Darstellung der gespeicherten Anker auf einem Gerät. Anker können aus **ARAnchors** in der Unity-Szene beibehalten, aus dem Speicher in neue **ARAnchors** geladen oder aus dem Speicher gelöscht werden.

> [!NOTE]
> Diese Anker müssen auf demselben Gerät gespeichert und geladen werden. Geräteübergreifender Ankerspeicher wird in einem Spatial Anchors Azure-Portal unterstützt.

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

### <a name="getting-an-anchor-store-reference"></a>Abrufen eines Ankerspeicherverweises 

Um XRAnchorStore mit **Unity 2020 und OpenXR** zu laden, verwenden Sie die Erweiterungsmethode für das XRAnchorSubsystem, das Subsystem eines ARAnchorManager:

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

Um einen Ankerspeicher in **Unity 2020 und OpenXR** zu laden, greifen Sie wie folgt über das Subsystem von ARAnchorManager darauf zu:

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

Ein vollständiges Beispiel für das Beibehalten/Nicht beibehalten von Ankern finden Sie im Skript Anchors -> Anchors Sample GameObject und AnchorsSample.cs in der [Mixed Reality OpenXR-Plug-In-Beispielszene:](../../openxr-getting-started.md#unity-sample-projects-for-openxr-and-hololens-2)

![Screenshot des im Unity-Editor geöffneten Hierarchiebereichs mit hervorgehobener Ankerbeispiel](../../images/openxr-features-img-04.png)

![Screenshot des im Unity-Editor geöffneten Inspektorbereichs mit hervorgehobener Anchors-Beispielskript](../../images/openxr-features-img-05.png)

# <a name="worldanchor"></a>[WorldAnchor](#tab/worldanchor)

**WorldAnchorStore** ist der Schlüssel zum Erstellen holografischer Erfahrungen, bei denen Hologramme in bestimmten realen Positionen über Instanzen der Anwendung hinweg bleiben. Benutzer können dann einzelne Hologramme anheften, wo sie möchten, und sie später an derselben Stelle bei vielen Verwendungen Ihrer App finden.

**Namespace:** *UnityEngine.XR.WSA.Persistence*<br>
**Klasse:** *WorldAnchorStore*

Mit worldAnchorStore können Sie den Speicherort von WorldAnchor sitzungsübergreifend beibehalten. Um Hologramme tatsächlich sitzungsübergreifend zu erhalten, müssen Sie Ihre GameObjects, die einen bestimmten Weltanker verwenden, separat nachverfolgen. Es ist oft sinnvoll, einen GameObject-Stamm mit einem Weltanker zu erstellen und von ihm verankerte hologramme mit einem lokalen Positionsoffset zu verankern.

So laden Sie Hologramme aus vorherigen Sitzungen:

1. WorldAnchorStore herunterladen
2. Laden von App-Daten im Zusammenhang mit dem Weltanker, der Ihnen die ID des Weltankers gibt
3. Laden eines Weltankers aus seiner ID

So speichern Sie Hologramme für zukünftige Sitzungen:

1. WorldAnchorStore herunterladen
2. Speichern eines Weltankers unter Angabe einer ID
3. Speichern von App-Daten im Zusammenhang mit dem Weltanker zusammen mit einer ID

### <a name="getting-the-worldanchorstore"></a>Abrufen des WorldAnchorStore

Sie sollten einen Verweis auf den WorldAnchorStore behalten, damit Sie wissen, wann er bereit ist, einen Vorgang durchzuführen. Da es sich um einen asynchronen Aufruf handelt, möchten Sie möglicherweise kurz nach dem Start Aufrufen von:

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

StoreLoaded ist in diesem Fall unser Handler für den Fall, dass der WorldAnchorStore das Laden abgeschlossen hat:

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

Wir verfügen nun über einen Verweis auf den WorldAnchorStore, den wir zum Speichern und Laden bestimmter World Anchors verwenden.

### <a name="saving-a-worldanchor"></a>Speichern eines WorldAnchor

Um zu speichern, müssen wir einfach benennen, was wir speichern, und es an den WorldAnchor übergeben, den wir zuvor beim Speichern haben. Hinweis: Beim Versuch, zwei Anker in derselben Zeichenfolge zu speichern, ist ein Fehler (Speicher. "Speichern" gibt "false" zurück. Löschen Sie den vorherigen Speicher, bevor Sie den neuen speichern:

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

Und laden Sie:

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

Darüber hinaus können wir store verwenden. Delete(), um einen Zuvor gespeicherten und gespeicherten Anker zu entfernen. Clear(), um alle zuvor gespeicherten Daten zu entfernen.

### <a name="enumerating-existing-anchors"></a>Aufzählen vorhandener Anker

Rufen Sie GetAllIds auf, um zuvor gespeicherte Anker zu finden.

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>Beibehalten von Hologrammen für mehrere Geräte

Sie können <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> verwenden, um einen permanenten Cloudanker aus einem lokalen WorldAnchor zu erstellen, den Ihre App dann auf mehreren HoloLens-, iOS- und Android-Geräten finden kann, auch wenn diese Geräte nicht gleichzeitig vorhanden sind.  Da Cloudanker persistent sind, können mehrere Geräte im Laufe der Zeit Inhalte sehen, die relativ zu diesem Anker am gleichen physischen Ort gerendert werden.

Probieren Sie die fünfminütigen Schnellstartanleitungen zu Azure Spatial Anchors Unity aus, um mit dem Erstellen gemeinsamer Erfahrungen in <a href="/azure/spatial-anchors/unity-overview" target="_blank">Unity zu beginnen.</a>

Sobald Sie azure Spatial Anchors haben, können Sie Anker in Unity erstellen <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">und suchen.</a>
