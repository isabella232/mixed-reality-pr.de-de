---
ms.openlocfilehash: 05e2b87383bbc91b7fd8785230152e3549f4b22d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2021
ms.locfileid: "104719980"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="9ecc9-101">Unity 2020 + openxr</span><span class="sxs-lookup"><span data-stu-id="9ecc9-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="9ecc9-102">Das Mixed Reality openxr-Plug-in stellt grundlegende Anker Funktionen durch eine Implementierung von Unity **aranchormanager** bereit.</span><span class="sxs-lookup"><span data-stu-id="9ecc9-102">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="9ecc9-103">Informationen zu den Grundlagen von aranchor in arfoundation finden Sie unter [arfoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span><span class="sxs-lookup"><span data-stu-id="9ecc9-103">To learn the basics on ARAnchors in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> 

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="9ecc9-104">Unity 2019/2020 + Windows-XR-Plug-in</span><span class="sxs-lookup"><span data-stu-id="9ecc9-104">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="9ecc9-105">Das Mixed Reality openxr-Plug-in stellt grundlegende Anker Funktionen durch eine Implementierung von Unity **aranchormanager** bereit.</span><span class="sxs-lookup"><span data-stu-id="9ecc9-105">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="9ecc9-106">Informationen zu den Grundlagen von aranchor in arfoundation finden Sie unter [arfoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span><span class="sxs-lookup"><span data-stu-id="9ecc9-106">To learn the basics on ARAnchors in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="9ecc9-107">Legacy-WSA</span><span class="sxs-lookup"><span data-stu-id="9ecc9-107">Legacy WSA</span></span>](#tab/wsa)

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="9ecc9-108">Entwickeln eines weltweiten Erlebnisses</span><span class="sxs-lookup"><span data-stu-id="9ecc9-108">Building a world-scale experience</span></span>

<span data-ttu-id="9ecc9-109">**Namespace:** *unityengine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="9ecc9-109">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="9ecc9-110">**Typ:** *worldanchor*</span><span class="sxs-lookup"><span data-stu-id="9ecc9-110">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="9ecc9-111">Für echte **Welt weite** Oberflächen in hololens, mit denen Benutzer mehr als 5 Meter bewegen können, benötigen Sie neue Techniken, die über diejenigen hinausgehen, die für Raum Skalierungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="9ecc9-111">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="9ecc9-112">Ein wichtiges Verfahren, das Sie verwenden, besteht darin, einen [räumlichen Anker](../../../design/coordinate-systems.md#spatial-anchors) zu erstellen, mit dem ein Cluster von holograms genau in der physischen Welt gesperrt wird, unabhängig davon, wie weit der Benutzer rostet hat, und [diese Hologramme in späteren Sitzungen erneut finden](../../../design/coordinate-systems.md#spatial-anchor-persistence).</span><span class="sxs-lookup"><span data-stu-id="9ecc9-112">One key technique you'll use is to create a [spatial anchor](../../../design/coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, no matter how far the user has roamed, and then [find those holograms again in later sessions](../../../design/coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="9ecc9-113">In Unity erstellen Sie einen räumlichen Anker durch Hinzufügen der Unity-Komponente **worldanchor** zu einem gameobject-Objekt.</span><span class="sxs-lookup"><span data-stu-id="9ecc9-113">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="9ecc9-114">Hinzufügen eines Welt Ankers</span><span class="sxs-lookup"><span data-stu-id="9ecc9-114">Adding a World Anchor</span></span>

<span data-ttu-id="9ecc9-115">Um einen Welt Anker hinzuzufügen, müssen `AddComponent<WorldAnchor>()` Sie für das Spielobjekt mit der Transformation, die Sie in der realen Welt verankern möchten, anrufen.</span><span class="sxs-lookup"><span data-stu-id="9ecc9-115">To add a world anchor, call `AddComponent<WorldAnchor>()` on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="9ecc9-116">Das ist alles!</span><span class="sxs-lookup"><span data-stu-id="9ecc9-116">That's it!</span></span> <span data-ttu-id="9ecc9-117">Dieses Spielobjekt wird nun an seinem aktuellen Speicherort in der physischen Welt verankert. möglicherweise werden die Unity-Weltkoordinaten im Laufe der Zeit leicht angepasst, um die physische Ausrichtung sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="9ecc9-117">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="9ecc9-118">Weitere Informationen finden Sie in einer zukünftigen App-Sitzung unter [Laden eines Welt Ankers](#loading-a-worldanchor) .</span><span class="sxs-lookup"><span data-stu-id="9ecc9-118">Refer to [loading a world anchor](#loading-a-worldanchor) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="9ecc9-119">Entfernen eines Welt Ankers</span><span class="sxs-lookup"><span data-stu-id="9ecc9-119">Removing a World Anchor</span></span>

<span data-ttu-id="9ecc9-120">Wenn Sie nicht mehr möchten, dass das gameobject-Objekt an eine physische Welt Stelle gesperrt ist, und Sie dieses Frame nicht verschieben möchten, können Sie einfach "zerstören" für die "World Anchor"-Komponente aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="9ecc9-120">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="9ecc9-121">Wenn Sie das gameobject-Objekt in diesen Frame verschieben möchten, müssen Sie stattdessen destroyimmediate aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="9ecc9-121">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="9ecc9-122">Verschieben eines weltweit verankerten gameobject</span><span class="sxs-lookup"><span data-stu-id="9ecc9-122">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="9ecc9-123">Gameobject kann nicht verschoben werden, wenn ein Welt Anker darauf liegt.</span><span class="sxs-lookup"><span data-stu-id="9ecc9-123">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="9ecc9-124">Wenn Sie das gameobject für diesen Frame verschieben müssen, müssen Sie Folgendes ausführen:</span><span class="sxs-lookup"><span data-stu-id="9ecc9-124">If you need to move the GameObject this frame, you need to:</span></span>

1. <span data-ttu-id="9ecc9-125">Destroyimmediate der Welt Anker Komponente</span><span class="sxs-lookup"><span data-stu-id="9ecc9-125">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="9ecc9-126">Verschieben des gameobject</span><span class="sxs-lookup"><span data-stu-id="9ecc9-126">Move the GameObject</span></span>
3. <span data-ttu-id="9ecc9-127">Fügen Sie dem gameobject eine neue Welt Anker Komponente hinzu.</span><span class="sxs-lookup"><span data-stu-id="9ecc9-127">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="9ecc9-128">Behandeln von Änderungen an der Anwendungs Freundlichkeit</span><span class="sxs-lookup"><span data-stu-id="9ecc9-128">Handling Locatability Changes</span></span>

<span data-ttu-id="9ecc9-129">Ein worldanchor kann nicht in der physischen Welt zu einem bestimmten Zeitpunkt einstellbar sein.</span><span class="sxs-lookup"><span data-stu-id="9ecc9-129">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="9ecc9-130">Wenn dies der Fall ist, wird Unity die Transformation des verankerten Objekts nicht aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="9ecc9-130">If that occurs, Unity won't be updating the transform of the anchored object.</span></span> <span data-ttu-id="9ecc9-131">Dies kann sich auch ändern, während eine app ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="9ecc9-131">This also can change while an app is running.</span></span> <span data-ttu-id="9ecc9-132">Wenn Sie die Änderung der loerability nicht bewältigen, wird das Objekt nicht am richtigen physischen Speicherort der Welt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="9ecc9-132">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="9ecc9-133">So erhalten Sie eine Benachrichtigung über die Änderungen der Änderungen:</span><span class="sxs-lookup"><span data-stu-id="9ecc9-133">To be notified about locatability changes:</span></span>

1. <span data-ttu-id="9ecc9-134">Ontrackingchanged-Ereignis abonnieren</span><span class="sxs-lookup"><span data-stu-id="9ecc9-134">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="9ecc9-135">Behandeln des Ereignisses</span><span class="sxs-lookup"><span data-stu-id="9ecc9-135">Handle the event</span></span>

<span data-ttu-id="9ecc9-136">Das **ontrackingchanged** -Ereignis wird immer dann aufgerufen, wenn sich der zugrunde liegende räumliche Anker zwischen dem Zustand "verwendbar" und "nicht zu verwendbar" ändert.</span><span class="sxs-lookup"><span data-stu-id="9ecc9-136">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="9ecc9-137">Behandeln Sie dann das-Ereignis:</span><span class="sxs-lookup"><span data-stu-id="9ecc9-137">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="9ecc9-138">Manchmal werden Anker sofort gefunden.</span><span class="sxs-lookup"><span data-stu-id="9ecc9-138">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="9ecc9-139">In diesem Fall wird diese islocated-Eigenschaft des Ankers auf true festgelegt, wenn addComponent <WorldAnchor> () zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="9ecc9-139">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="9ecc9-140">Folglich wird das ontrackingchanged-Ereignis nicht ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="9ecc9-140">As a result, the OnTrackingChanged event won't be triggered.</span></span> <span data-ttu-id="9ecc9-141">Ein sauberes Muster besteht darin, den ontrackingchanged-Handler mit dem ursprünglichen ISSE-Zustand nach dem Anfügen eines Ankers aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="9ecc9-141">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```