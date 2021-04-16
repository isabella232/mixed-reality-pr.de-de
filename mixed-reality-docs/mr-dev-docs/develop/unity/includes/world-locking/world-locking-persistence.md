---
ms.openlocfilehash: 25e42ba872764a98d4cb966b5a4922cc1dea0dc9
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528792"
---
# <a name="world-locking-tools-recommended"></a>[<span data-ttu-id="59b72-101">World Locking Tools (empfohlen)</span><span class="sxs-lookup"><span data-stu-id="59b72-101">World Locking Tools (Recommended)</span></span>](#tab/wlt)

<span data-ttu-id="59b72-102">Standardmäßig stellen world locking Tools das Unity-Koordinatensystem in Bezug auf die physische Welt sitzungsübergreifend wieder auf.</span><span class="sxs-lookup"><span data-stu-id="59b72-102">By default, World Locking Tools will restore Unity's coordinate system relative to the physical world across sessions.</span></span> <span data-ttu-id="59b72-103">Dies bedeutet, dass das Hologramm nur wieder dieselbe Pose haben muss, damit ein Hologramm nach dem Beenden und erneuten Ausführen der Anwendung an der gleichen Stelle in der physischen Welt angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="59b72-103">This means that to have a hologram appear the same place in the physical world after quitting and re-running the application, the hologram only needs to have the same Pose again.</span></span>

![Kontextkomponente "Weltsperrung" im Unity-Inspektor](../../images/world-locking-tools-img-02.png)

<span data-ttu-id="59b72-105">Wenn die Anwendung eine feiner geschaltete Steuerung benötigt, werden **auto-save** und **auto-load** möglicherweise im Inspektor deaktiviert und Persistenz über ein Skript verwaltet, wie im Abschnitt persistenz der [Dokumentation beschrieben.](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/Concepts/Advanced/Persistence.html)</span><span class="sxs-lookup"><span data-stu-id="59b72-105">If the application needs finer control, **Auto-Save** and **Auto-Load** may be disabled in the inspector, and persistence managed from a script as described in the [persistence section of the documentation](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/Concepts/Advanced/Persistence.html).</span></span>

# <a name="aranchormanager"></a>[<span data-ttu-id="59b72-106">ARAnchorManager</span><span class="sxs-lookup"><span data-stu-id="59b72-106">ARAnchorManager</span></span>](#tab/anchorstore)

<span data-ttu-id="59b72-107">Mit einer zusätzlichen API namens **XRAnchorStore** können Anker zwischen Sitzungen beibehalten werden.</span><span class="sxs-lookup"><span data-stu-id="59b72-107">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="59b72-108">Der XRAnchorStore ist eine Darstellung der gespeicherten Anker auf einem Gerät.</span><span class="sxs-lookup"><span data-stu-id="59b72-108">The XRAnchorStore is a representation of the saved anchors on a device.</span></span> <span data-ttu-id="59b72-109">Anker können aus **ARAnchors** in der Unity-Szene beibehalten, aus dem Speicher in neue **ARAnchors** geladen oder aus dem Speicher gelöscht werden.</span><span class="sxs-lookup"><span data-stu-id="59b72-109">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="59b72-110">Diese Anker müssen auf demselben Gerät gespeichert und geladen werden.</span><span class="sxs-lookup"><span data-stu-id="59b72-110">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="59b72-111">Geräteübergreifender Ankerspeicher wird in einem Spatial Anchors Azure-Dienst unterstützt.</span><span class="sxs-lookup"><span data-stu-id="59b72-111">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

### <a name="namespaces"></a><span data-ttu-id="59b72-112">Namespaces</span><span class="sxs-lookup"><span data-stu-id="59b72-112">Namespaces</span></span>

<span data-ttu-id="59b72-113">Für **Unity 2020 und OpenXR:**</span><span class="sxs-lookup"><span data-stu-id="59b72-113">For **Unity 2020 and OpenXR**:</span></span> 

``` cs
using Microsoft.MixedReality.ARSubsystems.XRAnchorStore
```

<span data-ttu-id="59b72-114">oder **Unity 2019/2020 + Windows XR-Plug-In:**</span><span class="sxs-lookup"><span data-stu-id="59b72-114">or **Unity 2019/2020 + Windows XR Plugin**:</span></span> 

```cs 
using UnityEngine.XR.WindowsMR.XRAnchorStore
```

### <a name="public-methods"></a><span data-ttu-id="59b72-115">Öffentliche Methoden</span><span class="sxs-lookup"><span data-stu-id="59b72-115">Public methods</span></span>

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

### <a name="getting-an-anchor-store-reference"></a><span data-ttu-id="59b72-116">Abrufen eines Ankerspeicherverweises</span><span class="sxs-lookup"><span data-stu-id="59b72-116">Getting an anchor store reference</span></span> 

<span data-ttu-id="59b72-117">Um XRAnchorStore mit **Unity 2020 und OpenXR** zu laden, verwenden Sie die Erweiterungsmethode für das XRAnchorSubsystem, das Subsystem eines ARAnchorManager:</span><span class="sxs-lookup"><span data-stu-id="59b72-117">To load the XRAnchorStore with **Unity 2020 and OpenXR**, use extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="59b72-118">Um XRAnchorStore mit **Unity 2019/2020 und dem Windows XR-Plug-In** zu laden, verwenden Sie die Erweiterungsmethode für das XRReferencePointSubsystem (Unity 2019) oder XRAnchorSubsystem (Unity 2020), das Subsystem eines ARReferencePointManager/ARAnchorManager:</span><span class="sxs-lookup"><span data-stu-id="59b72-118">To load the XRAnchorStore with **Unity 2019/2020 and the Windows XR Plugin**, use the extension method on the XRReferencePointSubsystem (Unity 2019) or XRAnchorSubsystem (Unity 2020), the subsystem of an ARReferencePointManager/ARAnchorManager:</span></span>

```cs
// Unity 2019 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem);

// Unity 2020 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem);
```

### <a name="loading-an-anchor-store"></a><span data-ttu-id="59b72-119">Laden eines Ankerspeichers</span><span class="sxs-lookup"><span data-stu-id="59b72-119">Loading an anchor store</span></span>

<span data-ttu-id="59b72-120">Um einen Ankerspeicher in **Unity 2020 und OpenXR** zu laden, greifen Sie wie folgt über das Subsystem von ARAnchorManager darauf zu:</span><span class="sxs-lookup"><span data-stu-id="59b72-120">To load an anchor store in **Unity 2020 and OpenXR**, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="59b72-121">oder mit **Unity 2019/2020 und dem Windows XR-Plug-In:**</span><span class="sxs-lookup"><span data-stu-id="59b72-121">or with **Unity 2019/2020 and the Windows XR Plugin**:</span></span>

``` cs
// Unity 2019
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();

// Unity 2020
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

<span data-ttu-id="59b72-122">Ein vollständiges Beispiel für das Beibehalten/Aufheben von Ankern finden Sie im Skript Anchors -> Anchors Sample GameObject und AnchorsSample.cs in der [Mixed Reality OpenXR-Plug-In-Beispielszene:](../../openxr-getting-started.md#hololens-2-samples)</span><span class="sxs-lookup"><span data-stu-id="59b72-122">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](../../openxr-getting-started.md#hololens-2-samples):</span></span>

![Screenshot des im Unity-Editor geöffneten Hierarchiebereichs mit hervorgehobenen Ankerbeispielen](../../images/openxr-features-img-04.png)

![Screenshot des im Unity-Editor geöffneten Inspektorbereichs mit hervorgehobenen Beispielskripts für Anker](../../images/openxr-features-img-05.png)

# <a name="worldanchor"></a>[<span data-ttu-id="59b72-125">WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="59b72-125">WorldAnchor</span></span>](#tab/worldanchor)

<span data-ttu-id="59b72-126">**WorldAnchorStore** ist der Schlüssel zum Erstellen holografischer Erfahrungen, bei denen Hologramme in bestimmten realen Positionen über Instanzen der Anwendung hinweg verbleiben.</span><span class="sxs-lookup"><span data-stu-id="59b72-126">The **WorldAnchorStore** is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="59b72-127">Benutzer können dann einzelne Hologramme an jeder gewünschten Stelle anheften und sie später bei vielen Verwendungsmöglichkeiten Ihrer App an der gleichen Stelle finden.</span><span class="sxs-lookup"><span data-stu-id="59b72-127">Users can then pin individual holograms wherever they want, and find them later in the same spot over many uses of your app.</span></span>

<span data-ttu-id="59b72-128">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span><span class="sxs-lookup"><span data-stu-id="59b72-128">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="59b72-129">**Klasse:** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="59b72-129">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="59b72-130">Mit WorldAnchorStore können Sie den Speicherort von WorldAnchor sitzungsübergreifend beibehalten.</span><span class="sxs-lookup"><span data-stu-id="59b72-130">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="59b72-131">Um Hologramme tatsächlich sitzungsübergreifend beizubehalten, müssen Sie Ihre GameObjects, die einen bestimmten Weltanker verwenden, separat nachverfolgen.</span><span class="sxs-lookup"><span data-stu-id="59b72-131">To actually persist holograms across sessions, you'll need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="59b72-132">Es ist oft sinnvoll, einen GameObject-Stamm mit einem Weltanker zu erstellen und untergeordnete Hologramme mit einem lokalen Positionsoffset zu verankern.</span><span class="sxs-lookup"><span data-stu-id="59b72-132">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="59b72-133">So laden Sie Hologramme aus vorherigen Sitzungen:</span><span class="sxs-lookup"><span data-stu-id="59b72-133">To load holograms from previous sessions:</span></span>

1. <span data-ttu-id="59b72-134">Abrufen des WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="59b72-134">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="59b72-135">Laden von App-Daten im Zusammenhang mit dem Weltanker, der Ihnen die ID des Weltankers liefert</span><span class="sxs-lookup"><span data-stu-id="59b72-135">Load app data relating to the world anchor, which gives you the ID of the world anchor</span></span>
3. <span data-ttu-id="59b72-136">Laden eines Weltankers aus seiner ID</span><span class="sxs-lookup"><span data-stu-id="59b72-136">Load a world anchor from its ID</span></span>

<span data-ttu-id="59b72-137">So speichern Sie Hologramme für zukünftige Sitzungen:</span><span class="sxs-lookup"><span data-stu-id="59b72-137">To save holograms for future sessions:</span></span>

1. <span data-ttu-id="59b72-138">Abrufen des WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="59b72-138">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="59b72-139">Speichern eines Weltankers, der eine ID angibt</span><span class="sxs-lookup"><span data-stu-id="59b72-139">Save a world anchor specifying an ID</span></span>
3. <span data-ttu-id="59b72-140">Speichern von App-Daten im Zusammenhang mit dem Weltanker zusammen mit einer ID</span><span class="sxs-lookup"><span data-stu-id="59b72-140">Save app data relating to the world anchor along with an ID</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="59b72-141">Abrufen des WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="59b72-141">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="59b72-142">Sie sollten einen Verweis auf den WorldAnchorStore behalten, damit Sie wissen, wann er zum Ausführen eines Vorgangs bereit ist.</span><span class="sxs-lookup"><span data-stu-id="59b72-142">You'll want to keep a reference to the WorldAnchorStore so you know when it's ready to perform an operation.</span></span> <span data-ttu-id="59b72-143">Da es sich um einen asynchronen Aufruf handelt, möchten Sie möglicherweise kurz nach dem Start Aufrufen von:</span><span class="sxs-lookup"><span data-stu-id="59b72-143">Since this is an async call, potentially as soon as start up, you want to call:</span></span>

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="59b72-144">StoreLoaded ist in diesem Fall unser Handler für den Fall, dass der WorldAnchorStore das Laden abgeschlossen hat:</span><span class="sxs-lookup"><span data-stu-id="59b72-144">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

<span data-ttu-id="59b72-145">Wir verfügen nun über einen Verweis auf den WorldAnchorStore, den wir zum Speichern und Laden bestimmter World Anchors verwenden.</span><span class="sxs-lookup"><span data-stu-id="59b72-145">We now have a reference to the WorldAnchorStore, which we'll use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="59b72-146">Speichern eines WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="59b72-146">Saving a WorldAnchor</span></span>

<span data-ttu-id="59b72-147">Um zu speichern, müssen wir einfach benennen, was wir speichern, und es an den WorldAnchor übergeben, den wir zuvor beim Speichern hatten.</span><span class="sxs-lookup"><span data-stu-id="59b72-147">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="59b72-148">Hinweis: Beim Versuch, zwei Anker in derselben Zeichenfolge zu speichern, ist ein Fehler (Speicher. "Speichern" gibt "false" zurück.</span><span class="sxs-lookup"><span data-stu-id="59b72-148">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="59b72-149">Löschen Sie den vorherigen Speicher, bevor Sie den neuen speichern:</span><span class="sxs-lookup"><span data-stu-id="59b72-149">Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="59b72-150">Laden eines WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="59b72-150">Loading a WorldAnchor</span></span>

<span data-ttu-id="59b72-151">Und laden Sie:</span><span class="sxs-lookup"><span data-stu-id="59b72-151">And to load:</span></span>

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

<span data-ttu-id="59b72-152">Darüber hinaus können wir store verwenden. Delete(), um einen Zuvor gespeicherten und gespeicherten Anker zu entfernen. Clear(), um alle zuvor gespeicherten Daten zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="59b72-152">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="59b72-153">Aufzählen vorhandener Anker</span><span class="sxs-lookup"><span data-stu-id="59b72-153">Enumerating Existing Anchors</span></span>

<span data-ttu-id="59b72-154">Rufen Sie GetAllIds auf, um zuvor gespeicherte Anker zu finden.</span><span class="sxs-lookup"><span data-stu-id="59b72-154">To discover previously stored anchors, call GetAllIds.</span></span>

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="59b72-155">Beibehalten von Hologrammen für mehrere Geräte</span><span class="sxs-lookup"><span data-stu-id="59b72-155">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="59b72-156">Sie können <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> verwenden, um einen permanenten Cloudanker aus einem lokalen WorldAnchor zu erstellen, den Ihre App dann auf mehreren HoloLens-, iOS- und Android-Geräten finden kann, auch wenn diese Geräte nicht gleichzeitig zusammen vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="59b72-156">You can use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices aren't present together at the same time.</span></span>  <span data-ttu-id="59b72-157">Da Cloudanker persistent sind, können mehrere Geräte im Laufe der Zeit Inhalte sehen, die relativ zu diesem Anker am gleichen physischen Ort gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="59b72-157">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="59b72-158">Probieren Sie die fünfminütigen Schnellstartanleitungen zu Azure Spatial Anchors Unity aus, um mit dem Erstellen gemeinsamer Erfahrungen in <a href="/azure/spatial-anchors/unity-overview" target="_blank">Unity zu beginnen.</a></span><span class="sxs-lookup"><span data-stu-id="59b72-158">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="59b72-159">Sobald Sie azure Spatial Anchors haben, können Sie Anker in Unity erstellen <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">und suchen.</a></span><span class="sxs-lookup"><span data-stu-id="59b72-159">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>
