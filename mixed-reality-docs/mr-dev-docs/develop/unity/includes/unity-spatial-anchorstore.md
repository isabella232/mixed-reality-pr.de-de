---
ms.openlocfilehash: bb2df8c85dd05981c1438bdb076b0aad16c7efd7
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2021
ms.locfileid: "104719880"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="30966-101">Unity 2020 + openxr</span><span class="sxs-lookup"><span data-stu-id="30966-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="30966-102">Eine zusätzliche API mit dem Namen " **xranchorstore** " ermöglicht, dass Anker zwischen Sitzungen beibehalten werden.</span><span class="sxs-lookup"><span data-stu-id="30966-102">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="30966-103">Der xranchorstore ist eine Darstellung der gespeicherten Anker auf einem Gerät.</span><span class="sxs-lookup"><span data-stu-id="30966-103">The XRAnchorStore is a representation of the saved anchors on a device.</span></span> <span data-ttu-id="30966-104">Anker können von **aranchor** in der Unity-Szene persistent gespeichert, aus dem Speicher in neue **aranchor** geladen oder aus dem Speicher gelöscht werden.</span><span class="sxs-lookup"><span data-stu-id="30966-104">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="30966-105">Diese Anker müssen auf demselben Gerät gespeichert und geladen werden.</span><span class="sxs-lookup"><span data-stu-id="30966-105">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="30966-106">Der Geräte übergreifende Anker Speicher wird in einer zukünftigen Version durch Azure Spatial Anchor unterstützt.</span><span class="sxs-lookup"><span data-stu-id="30966-106">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

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

<span data-ttu-id="30966-107">Zum Laden von xranchorstore stellt das Plug-in eine Erweiterungsmethode für das xranchorsubsystem bereit, das Subsystem von aranchormanager:</span><span class="sxs-lookup"><span data-stu-id="30966-107">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="30966-108">Um diese Erweiterungsmethode zu verwenden, greifen Sie über das Subsystem von aranchormanager wie folgt auf Sie zu:</span><span class="sxs-lookup"><span data-stu-id="30966-108">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="30966-109">Ein vollständiges Beispiel für persistente/nicht persistente Anker finden Sie im Beispiel für die Anker-> Anker Sample gameobject und das anchorssample. cs-Skript in der [Beispiel Szene für das Mixed Reality openxr-Plug](../openxr-getting-started.md#hololens-2-samples)-in:</span><span class="sxs-lookup"><span data-stu-id="30966-109">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](../openxr-getting-started.md#hololens-2-samples):</span></span>

![Screenshot des Bereichs "Hierarchie" im Unity-Editor mit hervorgehobenem Anker Beispiel](../images/openxr-features-img-04.png)

![Screenshot des Bereichs "Inspector" im Unity-Editor mit hervorgehobenem Anker Beispielskript](../images/openxr-features-img-05.png)

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="30966-112">Unity 2019/2020 + Windows-XR-Plug-in</span><span class="sxs-lookup"><span data-stu-id="30966-112">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="30966-113">Eine API mit dem Namen " **xranchorstore** " ermöglicht es, dass Anker zwischen Sitzungen beibehalten werden.</span><span class="sxs-lookup"><span data-stu-id="30966-113">An API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="30966-114">Der xranchorstore ist eine Darstellung der gespeicherten Anker auf einem Gerät.</span><span class="sxs-lookup"><span data-stu-id="30966-114">The XRAnchorStore is a representation of the saved anchors on a device.</span></span> <span data-ttu-id="30966-115">Anker können von **aranchor** in der Unity-Szene persistent gespeichert, aus dem Speicher in neue **aranchor** geladen oder aus dem Speicher gelöscht werden.</span><span class="sxs-lookup"><span data-stu-id="30966-115">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="30966-116">Diese Anker müssen auf demselben Gerät gespeichert und geladen werden.</span><span class="sxs-lookup"><span data-stu-id="30966-116">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="30966-117">Der Geräte übergreifende Anker Speicher wird in einer zukünftigen Version durch Azure Spatial Anchor unterstützt.</span><span class="sxs-lookup"><span data-stu-id="30966-117">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

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

<span data-ttu-id="30966-118">Zum Laden von xranchorstore stellt das Plug-in eine Erweiterungsmethode für xrreferencepointsubsystem (Unity 2019) oder xranchorsubsystem (Unity 2020) dar, das Subsystem von arreferencepointmanager/aranchormanager:</span><span class="sxs-lookup"><span data-stu-id="30966-118">To load the XRAnchorStore, the plugin provides an extension method on the XRReferencePointSubsystem (Unity 2019) or XRAnchorSubsystem (Unity 2020), the subsystem of an ARReferencePointManager/ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem); // Unity 2019
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem); // Unity 2020
```

<span data-ttu-id="30966-119">Um diese Erweiterungsmethode zu verwenden, greifen Sie über das Subsystem von aranchormanager wie folgt für Unity 2019 auf Sie zu:</span><span class="sxs-lookup"><span data-stu-id="30966-119">To use this extension method, access it from an ARAnchorManager's subsystem as follows for Unity 2019:</span></span>

``` cs
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();
```

<span data-ttu-id="30966-120">oder für Unity 2020:</span><span class="sxs-lookup"><span data-stu-id="30966-120">or for Unity 2020:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

# <a name="legacy-wsa"></a>[<span data-ttu-id="30966-121">Legacy-WSA</span><span class="sxs-lookup"><span data-stu-id="30966-121">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="30966-122">**Worldanchorstore** ist der Schlüssel für die Erstellung von Holographic-Erfahrungen, bei denen Hologramme in den einzelnen Anwendungs Instanzen in bestimmten realen Positionen bleiben.</span><span class="sxs-lookup"><span data-stu-id="30966-122">The **WorldAnchorStore** is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="30966-123">Benutzer können dann jedes beliebige Hologramm an die gewünschte Stelle anheften und später auf der gleichen Stelle über viele Verwendungszwecke Ihrer APP suchen.</span><span class="sxs-lookup"><span data-stu-id="30966-123">Users can then pin individual holograms wherever they want, and find them later in the same spot over many uses of your app.</span></span>

<span data-ttu-id="30966-124">**Namespace:** *unityengine. XR. WSA. Persistenz*</span><span class="sxs-lookup"><span data-stu-id="30966-124">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="30966-125">**Klasse:** *worldanchorstore*</span><span class="sxs-lookup"><span data-stu-id="30966-125">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="30966-126">Mit worldanchorstore können Sie den Speicherort von worldanchor Sitzungs übergreifend beibehalten.</span><span class="sxs-lookup"><span data-stu-id="30966-126">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="30966-127">Sie müssen ihre gameobjects-Objekte, die einen bestimmten Welt Anker verwenden, separat nachverfolgen, um Hologramme in mehreren Sitzungen dauerhaft beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="30966-127">To actually persist holograms across sessions, you'll need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="30966-128">Häufig ist es sinnvoll, einen gameobject-Stamm mit einem Welt Anker zu erstellen und untergeordnete Hologramme mit einem lokalen Positions Offset zu verankern.</span><span class="sxs-lookup"><span data-stu-id="30966-128">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="30966-129">So laden Sie holograms aus vorherigen Sitzungen:</span><span class="sxs-lookup"><span data-stu-id="30966-129">To load holograms from previous sessions:</span></span>

1. <span data-ttu-id="30966-130">Verschaffen Sie sich den worldanchorstore</span><span class="sxs-lookup"><span data-stu-id="30966-130">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="30966-131">Laden von App-Daten in Bezug auf den World-Anker, der Ihnen die ID des Welt Ankers liefert</span><span class="sxs-lookup"><span data-stu-id="30966-131">Load app data relating to the world anchor, which gives you the ID of the world anchor</span></span>
3. <span data-ttu-id="30966-132">Einen Welt Anker aus seiner ID laden</span><span class="sxs-lookup"><span data-stu-id="30966-132">Load a world anchor from its ID</span></span>

<span data-ttu-id="30966-133">So speichern Sie Hologramme für zukünftige Sitzungen:</span><span class="sxs-lookup"><span data-stu-id="30966-133">To save holograms for future sessions:</span></span>

1. <span data-ttu-id="30966-134">Verschaffen Sie sich den worldanchorstore</span><span class="sxs-lookup"><span data-stu-id="30966-134">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="30966-135">Speichern eines Welt Ankers, der eine ID angibt</span><span class="sxs-lookup"><span data-stu-id="30966-135">Save a world anchor specifying an ID</span></span>
3. <span data-ttu-id="30966-136">Speichern von App-Daten, die sich auf den Welt Anker beziehen, sowie eine ID</span><span class="sxs-lookup"><span data-stu-id="30966-136">Save app data relating to the world anchor along with an ID</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="30966-137">Der worldanchorstore wird erhalten.</span><span class="sxs-lookup"><span data-stu-id="30966-137">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="30966-138">Sie sollten einen Verweis auf den worldanchorstore behalten, damit Sie wissen, wann er bereit ist, einen Vorgang auszuführen.</span><span class="sxs-lookup"><span data-stu-id="30966-138">You'll want to keep a reference to the WorldAnchorStore so you know when it's ready to perform an operation.</span></span> <span data-ttu-id="30966-139">Da es sich hierbei um einen asynchronen-Befehl handelt, der möglicherweise unmittelbar nach dem Start aufgerufen wird, sollten Sie Folgendes aufrufen:</span><span class="sxs-lookup"><span data-stu-id="30966-139">Since this is an async call, potentially as soon as start up, you want to call:</span></span>

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="30966-140">Storeloaded ist in diesem Fall der Handler für den Fall, dass der worldanchorstore das Laden abgeschlossen hat:</span><span class="sxs-lookup"><span data-stu-id="30966-140">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

<span data-ttu-id="30966-141">Wir haben nun einen Verweis auf den worldanchorstore, den wir verwenden werden, um bestimmte weltanker zu speichern und zu laden.</span><span class="sxs-lookup"><span data-stu-id="30966-141">We now have a reference to the WorldAnchorStore, which we'll use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="30966-142">Speichern von worldanchor</span><span class="sxs-lookup"><span data-stu-id="30966-142">Saving a WorldAnchor</span></span>

<span data-ttu-id="30966-143">Zum Speichern müssen wir einfach den Namen der Speicherung benennen und Sie an den worldanchor übergeben, den wir vor dem Speichern erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="30966-143">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="30966-144">Hinweis: Wenn Sie versuchen, zwei Anker in derselben Zeichenfolge zu speichern, tritt ein Fehler auf (speichern. Save gibt false zurück).</span><span class="sxs-lookup"><span data-stu-id="30966-144">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="30966-145">Löschen Sie die vorherige Speicherung, bevor Sie die neue speichern:</span><span class="sxs-lookup"><span data-stu-id="30966-145">Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="30966-146">Laden von worldanchor</span><span class="sxs-lookup"><span data-stu-id="30966-146">Loading a WorldAnchor</span></span>

<span data-ttu-id="30966-147">Und zum Laden:</span><span class="sxs-lookup"><span data-stu-id="30966-147">And to load:</span></span>

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

<span data-ttu-id="30966-148">Wir können außerdem "Store" verwenden. Delete () um einen Anker zu entfernen, den wir zuvor gespeichert und gespeichert haben. Löschen Sie (), um alle zuvor gespeicherten Daten zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="30966-148">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="30966-149">Auflisten vorhandener Anker</span><span class="sxs-lookup"><span data-stu-id="30966-149">Enumerating Existing Anchors</span></span>

<span data-ttu-id="30966-150">Um zuvor gespeicherte Anker zu ermitteln, müssen Sie getallids aufrufen.</span><span class="sxs-lookup"><span data-stu-id="30966-150">To discover previously stored anchors, call GetAllIds.</span></span>

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="30966-151">Beibehalten von holograms für mehrere Geräte</span><span class="sxs-lookup"><span data-stu-id="30966-151">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="30966-152">Sie können <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial</a> Anchor verwenden, um einen permanenten cloudanker von einem lokalen worldanchor zu erstellen, den Ihre APP dann über mehrere hololens-, IOS-und Android-Geräte hinweg finden kann, auch wenn diese Geräte nicht gleichzeitig vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="30966-152">You can use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices aren't present together at the same time.</span></span>  <span data-ttu-id="30966-153">Da cloudananker permanent sind, können mehrere Geräte im Lauf der Zeit jeweils Inhalte sehen, die relativ zu diesem Anker am gleichen physischen Standort gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="30966-153">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="30966-154">Um mit der Einführung von freigegebenen Erfahrungen in Unity zu beginnen, testen Sie die fünfminütigen <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchor Unity-Schnellstarts</a>.</span><span class="sxs-lookup"><span data-stu-id="30966-154">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="30966-155">Sobald Sie mit räumlichen Azure-Ankern arbeiten, können Sie <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Anker in Unity erstellen und lokalisieren</a>.</span><span class="sxs-lookup"><span data-stu-id="30966-155">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>
