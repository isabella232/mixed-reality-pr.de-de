---
ms.openlocfilehash: 6229b258233f7a80ef6530edd6eb94774a0e54cf
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528775"
---
# <a name="world-locking-tools-recommended"></a>[<span data-ttu-id="47665-101">World Locking Tools (empfohlen)</span><span class="sxs-lookup"><span data-stu-id="47665-101">World Locking Tools (Recommended)</span></span>](#tab/wlt)

<span data-ttu-id="47665-102">Es wird empfohlen, World Locking Tools mithilfe des neuen Mixed Reality Featuretools zu installieren.</span><span class="sxs-lookup"><span data-stu-id="47665-102">We recommend installing World Locking Tools using the new Mixed Reality Feature Tool.</span></span> <span data-ttu-id="47665-103">Nachdem Sie das Mixed Reality Feature Tool über den folgenden Link heruntergeladen haben, wählen Sie die neueste Version von **WLT Core** aus dem Abschnitt **"World Locking Tools"** aus:</span><span class="sxs-lookup"><span data-stu-id="47665-103">Once you've downloaded the Mixed Reality Feature Tool from the link below, select the latest version of **WLT Core** from the **World Locking Tools** section:</span></span>

![Mixed Reality Featureauswahlfenster des Featuretools mit ausgewählter Option "World Locking Tools"](../../images/spatial-anchors-setup-img-01.png)

> [!div class="nextstepaction"]
> [<span data-ttu-id="47665-105">Installieren von World Locking Tools mit dem MR-Featuretool</span><span class="sxs-lookup"><span data-stu-id="47665-105">Install World Locking Tools with the MR Feature Tool</span></span>](../../welcome-to-mr-feature-tool.md)

### <a name="automated-setup"></a><span data-ttu-id="47665-106">Automatisierte Einrichtung</span><span class="sxs-lookup"><span data-stu-id="47665-106">Automated setup</span></span>

<span data-ttu-id="47665-107">Wenn Ihr Projekt einsatzbereit ist, führen Sie das Hilfsprogramm zum Konfigurieren der Szene aus Mixed Reality **Toolkit > Utilities > World Locking Tools aus:**</span><span class="sxs-lookup"><span data-stu-id="47665-107">When your project is ready to go, run the configure scene utility from **Mixed Reality Toolkit > Utilities > World Locking Tools**:</span></span>

![Unity-Editor mit Mixed Reality Toolkit ausgewählt](../../images/world-locking-configuration-img-01.jpeg)

> [!IMPORTANT]
> <span data-ttu-id="47665-109">Das Hilfsprogramm Szene konfigurieren kann jederzeit erneut ausführen werden.</span><span class="sxs-lookup"><span data-stu-id="47665-109">The Configure scene utility can be rerun at any time.</span></span> <span data-ttu-id="47665-110">Beispielsweise sollte sie erneut ausführen werden, wenn das AR-Ziel von Legacy in XR SDK geändert wurde.</span><span class="sxs-lookup"><span data-stu-id="47665-110">For example, it should be rerun if the AR target has been changed from Legacy to XR SDK.</span></span> <span data-ttu-id="47665-111">Wenn die Szene bereits ordnungsgemäß konfiguriert ist, hat die Ausführung des Hilfsprogramms keine Auswirkungen.</span><span class="sxs-lookup"><span data-stu-id="47665-111">If the scene is already properly configured, running the utility has no effect.</span></span>

### <a name="visualizers"></a><span data-ttu-id="47665-112">Schnellansichten</span><span class="sxs-lookup"><span data-stu-id="47665-112">Visualizers</span></span>

<span data-ttu-id="47665-113">Während der frühen Entwicklung kann das Hinzufügen von Schnellansichten hilfreich sein, um sicherzustellen, dass WLT eingerichtet ist und ordnungsgemäß funktioniert.</span><span class="sxs-lookup"><span data-stu-id="47665-113">During early development, adding visualizers can be helpful to ensure WLT is setup and working properly.</span></span> <span data-ttu-id="47665-114">Sie können zur Produktionsleistung entfernt werden, oder wenn sie aus irgendeinem Grund nicht mehr benötigt werden, indem Sie das Hilfsprogramm Schnellansichten entfernen verwenden.</span><span class="sxs-lookup"><span data-stu-id="47665-114">They can be removed for production performance, or if for any reason are no longer needed, using the Remove visualizers utility.</span></span> <span data-ttu-id="47665-115">Weitere Informationen zu den Schnellansichten finden Sie in der [Tools-Dokumentation.](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/Tools.html#visualizers)</span><span class="sxs-lookup"><span data-stu-id="47665-115">More details on the visualizers can be found in the [Tools documentation](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/Tools.html#visualizers).</span></span>

# <a name="aranchormanager"></a>[<span data-ttu-id="47665-116">ARAnchorManager</span><span class="sxs-lookup"><span data-stu-id="47665-116">ARAnchorManager</span></span>](#tab/anchorstore)

<span data-ttu-id="47665-117">Das Mixed Reality OpenXR-Plug-In stellt grundlegende Ankerfunktionen über eine Implementierung von **ARFoundation ARAnchorManager** von Unity zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="47665-117">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="47665-118">Informationen zu den Grundlagen zu ARAnchors in ARFoundation finden Sie im [ARFoundation-Handbuch für AR Anchor Manager.](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html)</span><span class="sxs-lookup"><span data-stu-id="47665-118">To learn the basics on ARAnchors in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> 

# <a name="worldanchor"></a>[<span data-ttu-id="47665-119">WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="47665-119">WorldAnchor</span></span>](#tab/worldanchor)

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="47665-120">Erstellen einer weltweiten Erfahrung</span><span class="sxs-lookup"><span data-stu-id="47665-120">Building a world-scale experience</span></span>

<span data-ttu-id="47665-121">**Namespace:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="47665-121">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="47665-122">**Typ:** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="47665-122">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="47665-123">Für echte **Welterfahrungen** auf HoloLens, die Es Benutzern ermöglichen, mehr als 5 Meter zu erkunden, benötigen Sie neue Techniken, die über diejenigen hinausgehen, die für Raumerfahrungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="47665-123">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="47665-124">Eine wichtige Technik, die Sie verwenden, besteht darin, einen [Raumanker](../../../../design/coordinate-systems.md#spatial-anchors) zu erstellen, um einen Cluster von Hologrammen genau in der physischen Welt zu sperren, unabhängig davon, wie weit der Benutzer sich entfernt hat, und [diese Hologramme dann in späteren Sitzungen wieder](../../../../design/coordinate-systems.md#spatial-anchor-persistence)zu finden.</span><span class="sxs-lookup"><span data-stu-id="47665-124">One key technique you'll use is to create a [spatial anchor](../../../../design/coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, no matter how far the user has roamed, and then [find those holograms again in later sessions](../../../../design/coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="47665-125">In Unity erstellen Sie einen Raumanker, indem Sie die **Unity-Komponente WorldAnchor** einem GameObject hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="47665-125">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="47665-126">Hinzufügen eines Weltankers</span><span class="sxs-lookup"><span data-stu-id="47665-126">Adding a World Anchor</span></span>

<span data-ttu-id="47665-127">Um einen Weltanker hinzuzufügen, rufen `AddComponent<WorldAnchor>()` Sie für das Spielobjekt mit der Transformation auf, die Sie in der realen Welt verankern möchten.</span><span class="sxs-lookup"><span data-stu-id="47665-127">To add a world anchor, call `AddComponent<WorldAnchor>()` on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="47665-128">Das ist alles!</span><span class="sxs-lookup"><span data-stu-id="47665-128">That's it!</span></span> <span data-ttu-id="47665-129">Dieses Spielobjekt wird nun an seiner aktuellen Position in der physischen Welt verankert. Möglicherweise werden die Unity-Weltkoordinaten im Laufe der Zeit leicht angepasst, um die physische Ausrichtung sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="47665-129">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="47665-130">Weitere Informationen finden Sie unter [Laden eines Weltankers,](#loading-a-worldanchor) um diesen verankerten Speicherort in einer zukünftigen App-Sitzung erneut zu finden.</span><span class="sxs-lookup"><span data-stu-id="47665-130">Refer to [loading a world anchor](#loading-a-worldanchor) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="47665-131">Entfernen eines Weltankers</span><span class="sxs-lookup"><span data-stu-id="47665-131">Removing a World Anchor</span></span>

<span data-ttu-id="47665-132">Wenn Sie nicht mehr möchten, dass das GameObject an einem physischen Ort der Welt gesperrt ist und nicht beabsichtigen, es in diesem Frame zu verschieben, können Sie einfach Destroy für die World Anchor-Komponente aufrufen.</span><span class="sxs-lookup"><span data-stu-id="47665-132">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="47665-133">Wenn Sie das GameObject in diesen Frame verschieben möchten, müssen Sie stattdessen DestroyImmediate aufrufen.</span><span class="sxs-lookup"><span data-stu-id="47665-133">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="47665-134">Verschieben eines world Anchored GameObject</span><span class="sxs-lookup"><span data-stu-id="47665-134">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="47665-135">GameObject-Objekte können nicht verschoben werden, während sich ein World Anchor darauf befindet.</span><span class="sxs-lookup"><span data-stu-id="47665-135">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="47665-136">Wenn Sie das GameObject in diesen Frame verschieben müssen, müssen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="47665-136">If you need to move the GameObject this frame, you need to:</span></span>

1. <span data-ttu-id="47665-137">DestroyImmediate the World Anchor component</span><span class="sxs-lookup"><span data-stu-id="47665-137">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="47665-138">Verschieben des GameObject</span><span class="sxs-lookup"><span data-stu-id="47665-138">Move the GameObject</span></span>
3. <span data-ttu-id="47665-139">Fügen Sie dem GameObject eine neue World Anchor-Komponente hinzu.</span><span class="sxs-lookup"><span data-stu-id="47665-139">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="47665-140">Verarbeiten von Locatability-Änderungen</span><span class="sxs-lookup"><span data-stu-id="47665-140">Handling Locatability Changes</span></span>

<span data-ttu-id="47665-141">Ein WorldAnchor ist in der physischen Welt zu einem Zeitpunkt möglicherweise nicht verwendbar.</span><span class="sxs-lookup"><span data-stu-id="47665-141">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="47665-142">In diesem Fall aktualisiert Unity die Transformation des verankerten Objekts nicht.</span><span class="sxs-lookup"><span data-stu-id="47665-142">If that occurs, Unity won't be updating the transform of the anchored object.</span></span> <span data-ttu-id="47665-143">Dies kann sich auch ändern, während eine App ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="47665-143">This also can change while an app is running.</span></span> <span data-ttu-id="47665-144">Wenn die Änderung der Locatability nicht behandelt wird, wird das Objekt nicht an der richtigen physischen Position der Welt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="47665-144">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="47665-145">So werden Sie über Änderungen der Locatability benachrichtigt:</span><span class="sxs-lookup"><span data-stu-id="47665-145">To be notified about locatability changes:</span></span>

1. <span data-ttu-id="47665-146">Abonnieren des OnTrackingChanged-Ereignisses</span><span class="sxs-lookup"><span data-stu-id="47665-146">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="47665-147">Behandeln des Ereignisses</span><span class="sxs-lookup"><span data-stu-id="47665-147">Handle the event</span></span>

<span data-ttu-id="47665-148">Das **OnTrackingChanged-Ereignis** wird immer dann aufgerufen, wenn sich der zugrunde liegende Raumanker zwischen dem Zustand "Locatable" und "Not Locatable" ändert.</span><span class="sxs-lookup"><span data-stu-id="47665-148">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="47665-149">Behandeln Sie dann das Ereignis:</span><span class="sxs-lookup"><span data-stu-id="47665-149">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="47665-150">Manchmal werden Anker sofort gefunden.</span><span class="sxs-lookup"><span data-stu-id="47665-150">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="47665-151">In diesem Fall wird diese isLocated-Eigenschaft des Ankers auf TRUE festgelegt, wenn AddComponent <WorldAnchor> () zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="47665-151">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="47665-152">Daher wird das OnTrackingChanged-Ereignis nicht ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="47665-152">As a result, the OnTrackingChanged event won't be triggered.</span></span> <span data-ttu-id="47665-153">Ein sauberes Muster wäre, ihren OnTrackingChanged-Handler mit dem anfänglichen IsLocated-Zustand nach dem Anfügen eines Ankers aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="47665-153">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```