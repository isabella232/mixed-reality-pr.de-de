---
title: Persistenz in Unity
description: Mit der Persistenz können Sie die einzelnen Hologramme an den gewünschten Ort anheften und später über viele Verwendungszwecke Ihrer APP suchen.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Hololens, Persistenz, Unity, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 7d12764dac2259388fe57d3924165783eab3dac5
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583496"
---
# <a name="persistence-in-unity"></a><span data-ttu-id="07fa7-104">Persistenz in Unity</span><span class="sxs-lookup"><span data-stu-id="07fa7-104">Persistence in Unity</span></span>

<span data-ttu-id="07fa7-105">**Namespace:** *unityengine. XR. WSA. Persistenz*</span><span class="sxs-lookup"><span data-stu-id="07fa7-105">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="07fa7-106">**Klasse:** *worldanchorstore*</span><span class="sxs-lookup"><span data-stu-id="07fa7-106">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="07fa7-107">Worldanchorstore ist der Schlüssel für die Erstellung von Holographic-Erfahrungen, bei denen Hologramme in den einzelnen Anwendungs Instanzen in bestimmten realen Positionen bleiben.</span><span class="sxs-lookup"><span data-stu-id="07fa7-107">The WorldAnchorStore is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="07fa7-108">Benutzer können dann jedes beliebige Hologramm an die gewünschte Stelle anheften und später auf der gleichen Stelle über viele Verwendungszwecke Ihrer APP suchen.</span><span class="sxs-lookup"><span data-stu-id="07fa7-108">Users can then pin individual holograms wherever they want, and find them later in the same spot over many uses of your app.</span></span>

## <a name="how-to-persist-holograms-across-sessions"></a><span data-ttu-id="07fa7-109">Beibehalten von holograms über Sitzungen hinweg</span><span class="sxs-lookup"><span data-stu-id="07fa7-109">How to persist holograms across sessions</span></span>

<span data-ttu-id="07fa7-110">Mit worldanchorstore können Sie den Speicherort von worldanchor Sitzungs übergreifend beibehalten.</span><span class="sxs-lookup"><span data-stu-id="07fa7-110">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="07fa7-111">Sie müssen ihre gameobjects-Objekte, die einen bestimmten Welt Anker verwenden, separat nachverfolgen, um Hologramme in mehreren Sitzungen dauerhaft beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="07fa7-111">To actually persist holograms across sessions, you'll need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="07fa7-112">Häufig ist es sinnvoll, einen gameobject-Stamm mit einem Welt Anker zu erstellen und untergeordnete Hologramme mit einem lokalen Positions Offset zu verankern.</span><span class="sxs-lookup"><span data-stu-id="07fa7-112">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="07fa7-113">So laden Sie holograms aus vorherigen Sitzungen:</span><span class="sxs-lookup"><span data-stu-id="07fa7-113">To load holograms from previous sessions:</span></span>
1. <span data-ttu-id="07fa7-114">Verschaffen Sie sich den worldanchorstore</span><span class="sxs-lookup"><span data-stu-id="07fa7-114">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="07fa7-115">Laden von App-Daten in Bezug auf den World-Anker, der Ihnen die ID des Welt Ankers liefert</span><span class="sxs-lookup"><span data-stu-id="07fa7-115">Load app data relating to the world anchor, which gives you the ID of the world anchor</span></span>
3. <span data-ttu-id="07fa7-116">Einen Welt Anker aus seiner ID laden</span><span class="sxs-lookup"><span data-stu-id="07fa7-116">Load a world anchor from its ID</span></span>

<span data-ttu-id="07fa7-117">So speichern Sie Hologramme für zukünftige Sitzungen:</span><span class="sxs-lookup"><span data-stu-id="07fa7-117">To save holograms for future sessions:</span></span>
1. <span data-ttu-id="07fa7-118">Verschaffen Sie sich den worldanchorstore</span><span class="sxs-lookup"><span data-stu-id="07fa7-118">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="07fa7-119">Speichern eines Welt Ankers, der eine ID angibt</span><span class="sxs-lookup"><span data-stu-id="07fa7-119">Save a world anchor specifying an ID</span></span>
3. <span data-ttu-id="07fa7-120">Speichern von App-Daten, die sich auf den Welt Anker beziehen, sowie eine ID</span><span class="sxs-lookup"><span data-stu-id="07fa7-120">Save app data relating to the world anchor along with an ID</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="07fa7-121">Der worldanchorstore wird erhalten.</span><span class="sxs-lookup"><span data-stu-id="07fa7-121">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="07fa7-122">Sie sollten einen Verweis auf den worldanchorstore behalten, damit Sie wissen, wann er bereit ist, einen Vorgang auszuführen.</span><span class="sxs-lookup"><span data-stu-id="07fa7-122">You'll want to keep a reference to the WorldAnchorStore so you know when it's ready to perform an operation.</span></span> <span data-ttu-id="07fa7-123">Da es sich hierbei um einen asynchronen-Befehl handelt, der möglicherweise unmittelbar nach dem Start aufgerufen wird, sollten Sie Folgendes aufrufen:</span><span class="sxs-lookup"><span data-stu-id="07fa7-123">Since this is an async call, potentially as soon as start up, you want to call:</span></span>

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="07fa7-124">Storeloaded ist in diesem Fall der Handler für den Fall, dass der worldanchorstore das Laden abgeschlossen hat:</span><span class="sxs-lookup"><span data-stu-id="07fa7-124">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

<span data-ttu-id="07fa7-125">Wir haben nun einen Verweis auf den worldanchorstore, den wir verwenden werden, um bestimmte weltanker zu speichern und zu laden.</span><span class="sxs-lookup"><span data-stu-id="07fa7-125">We now have a reference to the WorldAnchorStore, which we'll use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="07fa7-126">Speichern von worldanchor</span><span class="sxs-lookup"><span data-stu-id="07fa7-126">Saving a WorldAnchor</span></span>

<span data-ttu-id="07fa7-127">Zum Speichern müssen wir einfach den Namen der Speicherung benennen und Sie an den worldanchor übergeben, den wir vor dem Speichern erhalten haben.</span><span class="sxs-lookup"><span data-stu-id="07fa7-127">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="07fa7-128">Hinweis: Wenn Sie versuchen, zwei Anker in derselben Zeichenfolge zu speichern, tritt ein Fehler auf (speichern. Save gibt false zurück).</span><span class="sxs-lookup"><span data-stu-id="07fa7-128">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="07fa7-129">Löschen Sie die vorherige Speicherung, bevor Sie die neue speichern:</span><span class="sxs-lookup"><span data-stu-id="07fa7-129">Delete the previous save before saving the new one:</span></span>

```
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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="07fa7-130">Laden von worldanchor</span><span class="sxs-lookup"><span data-stu-id="07fa7-130">Loading a WorldAnchor</span></span>

<span data-ttu-id="07fa7-131">Und zum Laden:</span><span class="sxs-lookup"><span data-stu-id="07fa7-131">And to load:</span></span>

```
private void LoadGame()
{
       // Save data about holograms positioned by this world anchor
       this.savedRoot = this.store.Load("rootGameObject", rootGameObject);
       if (!this.savedRoot)
       {
              // We didn't actually have the game root saved! We have to re-place our objects or start over
       }
}
```

<span data-ttu-id="07fa7-132">Wir können außerdem "Store" verwenden. Delete () um einen Anker zu entfernen, den wir zuvor gespeichert und gespeichert haben. Löschen Sie (), um alle zuvor gespeicherten Daten zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="07fa7-132">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="07fa7-133">Auflisten vorhandener Anker</span><span class="sxs-lookup"><span data-stu-id="07fa7-133">Enumerating Existing Anchors</span></span>

<span data-ttu-id="07fa7-134">Um zuvor gespeicherte Anker zu ermitteln, müssen Sie getallids aufrufen.</span><span class="sxs-lookup"><span data-stu-id="07fa7-134">To discover previously stored anchors, call GetAllIds.</span></span>

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="07fa7-135">Beibehalten von holograms für mehrere Geräte</span><span class="sxs-lookup"><span data-stu-id="07fa7-135">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="07fa7-136">Sie können <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial</a> Anchor verwenden, um einen permanenten cloudanker von einem lokalen worldanchor zu erstellen, den Ihre APP dann über mehrere hololens-, IOS-und Android-Geräte hinweg finden kann, auch wenn diese Geräte nicht gleichzeitig vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="07fa7-136">You can use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices aren't present together at the same time.</span></span>  <span data-ttu-id="07fa7-137">Da cloudananker permanent sind, können mehrere Geräte im Lauf der Zeit jeweils Inhalte sehen, die relativ zu diesem Anker am gleichen physischen Standort gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="07fa7-137">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="07fa7-138">Um mit der Einführung von freigegebenen Erfahrungen in Unity zu beginnen, testen Sie die fünfminütigen <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchor Unity-Schnellstarts</a>.</span><span class="sxs-lookup"><span data-stu-id="07fa7-138">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="07fa7-139">Sobald Sie mit räumlichen Azure-Ankern arbeiten, können Sie <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Anker in Unity erstellen und lokalisieren</a>.</span><span class="sxs-lookup"><span data-stu-id="07fa7-139">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="07fa7-140">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="07fa7-140">Next Development Checkpoint</span></span>

<span data-ttu-id="07fa7-141">Wenn Sie der Unity-Entwicklungs Prüf Punkt Journey folgen, die wir gerade angelegt haben, sind Sie in der Mitte, dass Sie die Grundbausteine der gemischten Realität erkunden.</span><span class="sxs-lookup"><span data-stu-id="07fa7-141">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="07fa7-142">Von hier aus können Sie mit dem nächsten Baustein fortfahren:</span><span class="sxs-lookup"><span data-stu-id="07fa7-142">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="07fa7-143">Räumliche Abbildung</span><span class="sxs-lookup"><span data-stu-id="07fa7-143">Spatial mapping</span></span>](spatial-mapping-in-unity.md)

<span data-ttu-id="07fa7-144">Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:</span><span class="sxs-lookup"><span data-stu-id="07fa7-144">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="07fa7-145">Gemeinsame Erfahrung</span><span class="sxs-lookup"><span data-stu-id="07fa7-145">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="07fa7-146">Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="07fa7-146">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="07fa7-147">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="07fa7-147">See Also</span></span>
* [<span data-ttu-id="07fa7-148">Dauerhaftigkeit räumlicher Anker</span><span class="sxs-lookup"><span data-stu-id="07fa7-148">Spatial anchor persistence</span></span>](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <span data-ttu-id="07fa7-149"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="07fa7-149"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="07fa7-150"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchor SDK für Unity</a></span><span class="sxs-lookup"><span data-stu-id="07fa7-150"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>