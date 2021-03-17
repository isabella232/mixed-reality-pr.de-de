---
ms.openlocfilehash: df8dbe19b0a93e2452a8e0b677145bed42b05010
ms.sourcegitcommit: e51e18e443d73a74a9c0b86b3ca5748652cd1b24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2021
ms.locfileid: "103603384"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="ac841-101">Unity 2020 + openxr</span><span class="sxs-lookup"><span data-stu-id="ac841-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

> [!NOTE]
> <span data-ttu-id="ac841-102">Diese Anker müssen auf demselben Gerät gespeichert und geladen werden.</span><span class="sxs-lookup"><span data-stu-id="ac841-102">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="ac841-103">Der Geräte übergreifende Anker Speicher wird in einer zukünftigen Version durch Azure Spatial Anchor unterstützt.</span><span class="sxs-lookup"><span data-stu-id="ac841-103">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

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

<span data-ttu-id="ac841-104">Zum Laden von xranchorstore stellt das Plug-in eine Erweiterungsmethode für das xranchorsubsystem bereit, das Subsystem von aranchormanager:</span><span class="sxs-lookup"><span data-stu-id="ac841-104">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="ac841-105">Um diese Erweiterungsmethode zu verwenden, greifen Sie über das Subsystem von aranchormanager wie folgt auf Sie zu:</span><span class="sxs-lookup"><span data-stu-id="ac841-105">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="ac841-106">Ein vollständiges Beispiel für das beibehalten/beibehalten von Ankern finden Sie unter Anker-> Anker Sample gameobject und AnchorsSample.cs Script in the [Mixed Reality openxr Plugin Sample Scene](../openxr-getting-started.md#hololens-2-samples):</span><span class="sxs-lookup"><span data-stu-id="ac841-106">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](../openxr-getting-started.md#hololens-2-samples):</span></span>

![Screenshot des Bereichs "Hierarchie" im Unity-Editor mit hervorgehobenem Anker Beispiel](../images/openxr-features-img-04.png)

![Screenshot des Bereichs "Inspector" im Unity-Editor mit hervorgehobenem Anker Beispielskript](../images/openxr-features-img-05.png)

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="ac841-109">Unity 2019/2020 + Windows-XR-Plug-in</span><span class="sxs-lookup"><span data-stu-id="ac841-109">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

> [!NOTE]
> <span data-ttu-id="ac841-110">Diese Anker müssen auf demselben Gerät gespeichert und geladen werden.</span><span class="sxs-lookup"><span data-stu-id="ac841-110">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="ac841-111">Der Geräte übergreifende Anker Speicher wird in einer zukünftigen Version durch Azure Spatial Anchor unterstützt.</span><span class="sxs-lookup"><span data-stu-id="ac841-111">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

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

<span data-ttu-id="ac841-112">Zum Laden von xranchorstore stellt das Plug-in eine Erweiterungsmethode für xrreferencepointsubsystem (Unity 2019) oder xranchorsubsystem (Unity 2020) dar, das Subsystem von arreferencepointmanager/aranchormanager:</span><span class="sxs-lookup"><span data-stu-id="ac841-112">To load the XRAnchorStore, the plugin provides an extension method on the XRReferencePointSubsystem (Unity 2019) or XRAnchorSubsystem (Unity 2020), the subsystem of an ARReferencePointManager/ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem); // Unity 2019
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem); // Unity 2020
```

<span data-ttu-id="ac841-113">Um diese Erweiterungsmethode zu verwenden, greifen Sie über das Subsystem von aranchormanager wie folgt für Unity 2019 auf Sie zu:</span><span class="sxs-lookup"><span data-stu-id="ac841-113">To use this extension method, access it from an ARAnchorManager's subsystem as follows for Unity 2019:</span></span>

``` cs
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();
```

<span data-ttu-id="ac841-114">oder für Unity 2020:</span><span class="sxs-lookup"><span data-stu-id="ac841-114">or for Unity 2020:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

# <a name="legacy-wsa"></a>[<span data-ttu-id="ac841-115">Legacy-WSA</span><span class="sxs-lookup"><span data-stu-id="ac841-115">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="ac841-116">**Namespace:** *unityengine. XR. WSA. Persistenz*</span><span class="sxs-lookup"><span data-stu-id="ac841-116">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="ac841-117">**Klasse:** *worldanchorstore*</span><span class="sxs-lookup"><span data-stu-id="ac841-117">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="ac841-118">Mit worldanchorstore können Sie den Speicherort von worldanchor Sitzungs übergreifend beibehalten.</span><span class="sxs-lookup"><span data-stu-id="ac841-118">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="ac841-119">Sie müssen ihre gameobjects-Objekte, die einen bestimmten Welt Anker verwenden, separat nachverfolgen, um Hologramme in mehreren Sitzungen dauerhaft beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="ac841-119">To actually persist holograms across sessions, you'll need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="ac841-120">Häufig ist es sinnvoll, einen gameobject-Stamm mit einem Welt Anker zu erstellen und untergeordnete Hologramme mit einem lokalen Positions Offset zu verankern.</span><span class="sxs-lookup"><span data-stu-id="ac841-120">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="ac841-121">So laden Sie holograms aus vorherigen Sitzungen:</span><span class="sxs-lookup"><span data-stu-id="ac841-121">To load holograms from previous sessions:</span></span>

1. <span data-ttu-id="ac841-122">Verschaffen Sie sich den worldanchorstore</span><span class="sxs-lookup"><span data-stu-id="ac841-122">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="ac841-123">Laden von App-Daten in Bezug auf den World-Anker, der Ihnen die ID des Welt Ankers liefert</span><span class="sxs-lookup"><span data-stu-id="ac841-123">Load app data relating to the world anchor, which gives you the ID of the world anchor</span></span>
3. <span data-ttu-id="ac841-124">Einen Welt Anker aus seiner ID laden</span><span class="sxs-lookup"><span data-stu-id="ac841-124">Load a world anchor from its ID</span></span>

<span data-ttu-id="ac841-125">So speichern Sie Hologramme für zukünftige Sitzungen:</span><span class="sxs-lookup"><span data-stu-id="ac841-125">To save holograms for future sessions:</span></span>

1. <span data-ttu-id="ac841-126">Verschaffen Sie sich den worldanchorstore</span><span class="sxs-lookup"><span data-stu-id="ac841-126">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="ac841-127">Speichern eines Welt Ankers, der eine ID angibt</span><span class="sxs-lookup"><span data-stu-id="ac841-127">Save a world anchor specifying an ID</span></span>
3. <span data-ttu-id="ac841-128">Speichern von App-Daten, die sich auf den Welt Anker beziehen, sowie eine ID</span><span class="sxs-lookup"><span data-stu-id="ac841-128">Save app data relating to the world anchor along with an ID</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="ac841-129">Der worldanchorstore wird erhalten.</span><span class="sxs-lookup"><span data-stu-id="ac841-129">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="ac841-130">Sie sollten einen Verweis auf den worldanchorstore behalten, damit Sie wissen, wann er bereit ist, einen Vorgang auszuführen.</span><span class="sxs-lookup"><span data-stu-id="ac841-130">You'll want to keep a reference to the WorldAnchorStore so you know when it's ready to perform an operation.</span></span> <span data-ttu-id="ac841-131">Da es sich hierbei um einen asynchronen-Befehl handelt, der möglicherweise unmittelbar nach dem Start aufgerufen wird, sollten Sie Folgendes aufrufen:</span><span class="sxs-lookup"><span data-stu-id="ac841-131">Since this is an async call, potentially as soon as start up, you want to call:</span></span>

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="ac841-132">Storeloaded ist in diesem Fall der Handler für den Fall, dass der worldanchorstore das Laden abgeschlossen hat:</span><span class="sxs-lookup"><span data-stu-id="ac841-132">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

<span data-ttu-id="ac841-133">Wir haben nun einen Verweis auf den worldanchorstore, den wir verwenden werden, um bestimmte weltanker zu speichern und zu laden.</span><span class="sxs-lookup"><span data-stu-id="ac841-133">We now have a reference to the WorldAnchorStore, which we'll use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="ac841-134">Speichern von worldanchor</span><span class="sxs-lookup"><span data-stu-id="ac841-134">Saving a WorldAnchor</span></span>

<span data-ttu-id="ac841-135">Zum Speichern müssen wir einfach den Namen der Speicherung benennen und Sie an den worldanchor übergeben, den wir vor dem Speichern erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="ac841-135">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="ac841-136">Hinweis: Wenn Sie versuchen, zwei Anker in derselben Zeichenfolge zu speichern, tritt ein Fehler auf (speichern. Save gibt false zurück).</span><span class="sxs-lookup"><span data-stu-id="ac841-136">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="ac841-137">Löschen Sie die vorherige Speicherung, bevor Sie die neue speichern:</span><span class="sxs-lookup"><span data-stu-id="ac841-137">Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="ac841-138">Laden von worldanchor</span><span class="sxs-lookup"><span data-stu-id="ac841-138">Loading a WorldAnchor</span></span>

<span data-ttu-id="ac841-139">Und zum Laden:</span><span class="sxs-lookup"><span data-stu-id="ac841-139">And to load:</span></span>

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

<span data-ttu-id="ac841-140">Wir können außerdem "Store" verwenden. Delete () um einen Anker zu entfernen, den wir zuvor gespeichert und gespeichert haben. Löschen Sie (), um alle zuvor gespeicherten Daten zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="ac841-140">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="ac841-141">Auflisten vorhandener Anker</span><span class="sxs-lookup"><span data-stu-id="ac841-141">Enumerating Existing Anchors</span></span>

<span data-ttu-id="ac841-142">Um zuvor gespeicherte Anker zu ermitteln, müssen Sie getallids aufrufen.</span><span class="sxs-lookup"><span data-stu-id="ac841-142">To discover previously stored anchors, call GetAllIds.</span></span>

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="ac841-143">Entwickeln eines weltweiten Erlebnisses</span><span class="sxs-lookup"><span data-stu-id="ac841-143">Building a world-scale experience</span></span>

<span data-ttu-id="ac841-144">**Namespace:** *unityengine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="ac841-144">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="ac841-145">**Typ:** *worldanchor*</span><span class="sxs-lookup"><span data-stu-id="ac841-145">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="ac841-146">Für echte **Welt weite** Oberflächen in hololens, mit denen Benutzer mehr als 5 Meter bewegen können, benötigen Sie neue Techniken, die über diejenigen hinausgehen, die für Raum Skalierungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ac841-146">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="ac841-147">Ein wichtiges Verfahren, das Sie verwenden, besteht darin, einen [räumlichen Anker](../../../design/coordinate-systems.md#spatial-anchors) zu erstellen, mit dem ein Cluster von holograms genau in der physischen Welt gesperrt wird, unabhängig davon, wie weit der Benutzer rostet hat, und [diese Hologramme in späteren Sitzungen erneut finden](../../../design/coordinate-systems.md#spatial-anchor-persistence).</span><span class="sxs-lookup"><span data-stu-id="ac841-147">One key technique you'll use is to create a [spatial anchor](../../../design/coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, no matter how far the user has roamed, and then [find those holograms again in later sessions](../../../design/coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="ac841-148">In Unity erstellen Sie einen räumlichen Anker durch Hinzufügen der Unity-Komponente **worldanchor** zu einem gameobject-Objekt.</span><span class="sxs-lookup"><span data-stu-id="ac841-148">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="ac841-149">Hinzufügen eines Welt Ankers</span><span class="sxs-lookup"><span data-stu-id="ac841-149">Adding a World Anchor</span></span>

<span data-ttu-id="ac841-150">Um einen Welt Anker hinzuzufügen, müssen `AddComponent<WorldAnchor>()` Sie für das Spielobjekt mit der Transformation, die Sie in der realen Welt verankern möchten, anrufen.</span><span class="sxs-lookup"><span data-stu-id="ac841-150">To add a world anchor, call `AddComponent<WorldAnchor>()` on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="ac841-151">Das ist alles!</span><span class="sxs-lookup"><span data-stu-id="ac841-151">That's it!</span></span> <span data-ttu-id="ac841-152">Dieses Spielobjekt wird nun an seinem aktuellen Speicherort in der physischen Welt verankert. möglicherweise werden die Unity-Weltkoordinaten im Laufe der Zeit leicht angepasst, um die physische Ausrichtung sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="ac841-152">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="ac841-153">Weitere Informationen finden Sie in einer zukünftigen App-Sitzung unter [Laden eines Welt Ankers](#loading-a-worldanchor) .</span><span class="sxs-lookup"><span data-stu-id="ac841-153">Refer to [loading a world anchor](#loading-a-worldanchor) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="ac841-154">Entfernen eines Welt Ankers</span><span class="sxs-lookup"><span data-stu-id="ac841-154">Removing a World Anchor</span></span>

<span data-ttu-id="ac841-155">Wenn Sie nicht mehr möchten, dass das gameobject-Objekt an eine physische Welt Stelle gesperrt ist, und Sie dieses Frame nicht verschieben möchten, können Sie einfach "zerstören" für die "World Anchor"-Komponente aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="ac841-155">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="ac841-156">Wenn Sie das gameobject-Objekt in diesen Frame verschieben möchten, müssen Sie stattdessen destroyimmediate aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="ac841-156">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="ac841-157">Verschieben eines weltweit verankerten gameobject</span><span class="sxs-lookup"><span data-stu-id="ac841-157">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="ac841-158">Gameobject kann nicht verschoben werden, wenn ein Welt Anker darauf liegt.</span><span class="sxs-lookup"><span data-stu-id="ac841-158">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="ac841-159">Wenn Sie das gameobject für diesen Frame verschieben müssen, müssen Sie Folgendes ausführen:</span><span class="sxs-lookup"><span data-stu-id="ac841-159">If you need to move the GameObject this frame, you need to:</span></span>

1. <span data-ttu-id="ac841-160">Destroyimmediate der Welt Anker Komponente</span><span class="sxs-lookup"><span data-stu-id="ac841-160">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="ac841-161">Verschieben des gameobject</span><span class="sxs-lookup"><span data-stu-id="ac841-161">Move the GameObject</span></span>
3. <span data-ttu-id="ac841-162">Fügen Sie dem gameobject eine neue Welt Anker Komponente hinzu.</span><span class="sxs-lookup"><span data-stu-id="ac841-162">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="ac841-163">Behandeln von Änderungen an der Anwendungs Freundlichkeit</span><span class="sxs-lookup"><span data-stu-id="ac841-163">Handling Locatability Changes</span></span>

<span data-ttu-id="ac841-164">Ein worldanchor kann nicht in der physischen Welt zu einem bestimmten Zeitpunkt einstellbar sein.</span><span class="sxs-lookup"><span data-stu-id="ac841-164">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="ac841-165">Wenn dies der Fall ist, wird Unity die Transformation des verankerten Objekts nicht aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="ac841-165">If that occurs, Unity won't be updating the transform of the anchored object.</span></span> <span data-ttu-id="ac841-166">Dies kann sich auch ändern, während eine app ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="ac841-166">This also can change while an app is running.</span></span> <span data-ttu-id="ac841-167">Wenn Sie die Änderung der loerability nicht bewältigen, wird das Objekt nicht am richtigen physischen Speicherort der Welt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ac841-167">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="ac841-168">So erhalten Sie eine Benachrichtigung über die Änderungen der Änderungen:</span><span class="sxs-lookup"><span data-stu-id="ac841-168">To be notified about locatability changes:</span></span>

1. <span data-ttu-id="ac841-169">Ontrackingchanged-Ereignis abonnieren</span><span class="sxs-lookup"><span data-stu-id="ac841-169">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="ac841-170">Behandeln des Ereignisses</span><span class="sxs-lookup"><span data-stu-id="ac841-170">Handle the event</span></span>

<span data-ttu-id="ac841-171">Das **ontrackingchanged** -Ereignis wird immer dann aufgerufen, wenn sich der zugrunde liegende räumliche Anker zwischen dem Zustand "verwendbar" und "nicht zu verwendbar" ändert.</span><span class="sxs-lookup"><span data-stu-id="ac841-171">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="ac841-172">Behandeln Sie dann das-Ereignis:</span><span class="sxs-lookup"><span data-stu-id="ac841-172">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="ac841-173">Manchmal werden Anker sofort gefunden.</span><span class="sxs-lookup"><span data-stu-id="ac841-173">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="ac841-174">In diesem Fall wird diese islocated-Eigenschaft des Ankers auf true festgelegt, wenn addComponent <WorldAnchor> () zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="ac841-174">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="ac841-175">Folglich wird das ontrackingchanged-Ereignis nicht ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="ac841-175">As a result, the OnTrackingChanged event won't be triggered.</span></span> <span data-ttu-id="ac841-176">Ein sauberes Muster besteht darin, den ontrackingchanged-Handler mit dem ursprünglichen ISSE-Zustand nach dem Anfügen eines Ankers aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="ac841-176">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="ac841-177">Beibehalten von holograms für mehrere Geräte</span><span class="sxs-lookup"><span data-stu-id="ac841-177">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="ac841-178">Sie können <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial</a> Anchor verwenden, um einen permanenten cloudanker von einem lokalen worldanchor zu erstellen, den Ihre APP dann über mehrere hololens-, IOS-und Android-Geräte hinweg finden kann, auch wenn diese Geräte nicht gleichzeitig vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="ac841-178">You can use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices aren't present together at the same time.</span></span>  <span data-ttu-id="ac841-179">Da cloudananker permanent sind, können mehrere Geräte im Lauf der Zeit jeweils Inhalte sehen, die relativ zu diesem Anker am gleichen physischen Standort gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="ac841-179">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="ac841-180">Um mit der Einführung von freigegebenen Erfahrungen in Unity zu beginnen, testen Sie die fünfminütigen <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchor Unity-Schnellstarts</a>.</span><span class="sxs-lookup"><span data-stu-id="ac841-180">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="ac841-181">Sobald Sie mit räumlichen Azure-Ankern arbeiten, können Sie <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Anker in Unity erstellen und lokalisieren</a>.</span><span class="sxs-lookup"><span data-stu-id="ac841-181">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>
