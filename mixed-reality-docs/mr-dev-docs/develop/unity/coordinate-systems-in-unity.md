---
title: Koordinatensysteme in Unity
description: Hier erfahren Sie, wie Sie in Unity Mixed Reality-Erfahrungen im Bereich "Platz", "Stehend", "Raum" und "Welt" erstellen.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Koordinatensystem, Raumkoordinatensystem, nur ausrichtungsbezogen, skaliert, stehend, Raumskalierung, Weltskala, 360 Grad, stehend, Stehend, Raum, Welt, Skalierung, Position, Ausrichtung, Unity, Anker, Raumanker, Weltanker, Weltsperren, Weltsperren, Körpersperren, Body-Locking, Nachverfolgungsverlust, Locatability, Begrenzungen, Aktueller, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 91b1adf6dcf1c54d0d29a02bfb97ac4674a87c88
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528750"
---
# <a name="coordinate-systems-in-unity"></a><span data-ttu-id="9d6ec-104">Koordinatensysteme in Unity</span><span class="sxs-lookup"><span data-stu-id="9d6ec-104">Coordinate systems in Unity</span></span>

<span data-ttu-id="9d6ec-105">Windows Mixed Reality unterstützt Apps für eine Vielzahl von Erfahrungsskalen– von apps mit ausrichtungsbasierter Und-Skalierung bis hin zu Apps im Raummaßstab.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-105">Windows Mixed Reality supports apps across a wide range of experience scales, from orientation-only and seated-scale apps up through room-scale apps.</span></span> <span data-ttu-id="9d6ec-106">Auf HoloLens können Sie weitergehen und weltweit skalierende Apps erstellen, mit denen Benutzer mehr als 5 Meter gehen und eine gesamte Etage eines Gebäudes und darüber hinaus erkunden können.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-106">On HoloLens, you can go further and build world-scale apps that let users walk beyond 5 meters, exploring an entire floor of a building and beyond.</span></span>

<span data-ttu-id="9d6ec-107">Der erste Schritt beim Erstellen einer Mixed Reality-Erfahrung in Unity besteht darin, Koordinatensysteme zu verstehen [und die Benutzeroberfläche auszuwählen, die](../../design/coordinate-systems.md) Ihre App als Ziel verwenden soll.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-107">Your first step in building a mixed reality experience in Unity is to understand [coordinate systems and choose the experience scale](../../design/coordinate-systems.md) your app will target.</span></span>

## <a name="building-an-orientation-only-or-seated-scale-experience"></a><span data-ttu-id="9d6ec-108">Erstellen einer reinen ausrichtungsbasierten oder skalierten Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="9d6ec-108">Building an orientation-only or seated-scale experience</span></span>

<span data-ttu-id="9d6ec-109">**Namespace:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="9d6ec-109">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="9d6ec-110">**Typ:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="9d6ec-110">**Type:** *XRDevice*</span></span>

<span data-ttu-id="9d6ec-111">Zum Erstellen einer **reinen ausrichtungsbasierten** oder **besetzen Benutzeroberfläche** müssen Sie Unity auf den Typ Stationärer Nachverfolgungsbereich festlegen.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-111">To build an **orientation-only** or **seated-scale experience**, you need to set Unity to the Stationary tracking space type.</span></span> <span data-ttu-id="9d6ec-112">Der ortsaufstärkungsraum legt das Weltkoordinatensystem von Unity fest, um den [stationären Bezugsrahmen](../../design/coordinate-systems.md#spatial-coordinate-systems)nachzuverfolgen.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-112">Stationary tracking space sets Unity's world coordinate system to track the [stationary frame of reference](../../design/coordinate-systems.md#spatial-coordinate-systems).</span></span> <span data-ttu-id="9d6ec-113">Im Nachverfolgungsmodus "Stationär" werden Inhalte, die im Editor direkt vor der Standardposition der Kamera platziert werden (forward ist -Z), vor dem Benutzer angezeigt, wenn die App gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-113">In the Stationary tracking mode, content placed in the editor just in front of the camera's default location (forward is -Z) will appear in front of the user when the app launches.</span></span>

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

<span data-ttu-id="9d6ec-114">**Namespace:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="9d6ec-114">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="9d6ec-115">**Typ:** *InputTracking*</span><span class="sxs-lookup"><span data-stu-id="9d6ec-115">**Type:** *InputTracking*</span></span>

<span data-ttu-id="9d6ec-116">Für eine reine **Ausrichtungserfahrung,** z. B. einen 360-Grad-Video-Viewer (bei dem Positionskopfupdates die Tante verfälschen würden), können Sie dann [XR festlegen. InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) auf TRUE:</span><span class="sxs-lookup"><span data-stu-id="9d6ec-116">For a pure **orientation-only experience** such as a 360-degree video viewer (where positional head updates would ruin the illusion), you can then set [XR.InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) to true:</span></span>

```cs
InputTracking.disablePositionalTracking = true;
```

<span data-ttu-id="9d6ec-117">Für eine **benutzerdefinierte Benutzeroberfläche** können Sie XR aufrufen, damit der Benutzer später den stammseitigen Ursprung erhalten [kann. InputTracking.Recenter-Methode:](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)</span><span class="sxs-lookup"><span data-stu-id="9d6ec-117">For a **seated-scale experience**, to let the user later recenter the seated origin, you can call the [XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) method:</span></span>

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a><span data-ttu-id="9d6ec-118">Erstellen einer Erfahrung im Stehend- oder Raummaßstab</span><span class="sxs-lookup"><span data-stu-id="9d6ec-118">Building a standing-scale or room-scale experience</span></span>

<span data-ttu-id="9d6ec-119">**Namespace:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="9d6ec-119">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="9d6ec-120">**Typ:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="9d6ec-120">**Type:** *XRDevice*</span></span>

<span data-ttu-id="9d6ec-121">Für eine **Erfahrung im Stehend-** oder **Raummaßstab** müssen Sie Inhalte relativ zum Boden platzieren.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-121">For a **standing-scale** or **room-scale experience**, you'll need to place content relative to the floor.</span></span> <span data-ttu-id="9d6ec-122">Sie können die Grundfläche des **[](../../design/coordinate-systems.md#spatial-coordinate-systems)** Benutzers mithilfe der räumlichen Stufe festlegen, die den vom Benutzer definierten Ursprung auf Bodenebene und die optionale Raumgrenze darstellt, die während der ersten Ausführung eingerichtet wurde.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-122">You reason about the user's floor using the **[spatial stage](../../design/coordinate-systems.md#spatial-coordinate-systems)**, which represents the user's defined floor-level origin and optional room boundary, set up during first run.</span></span>

<span data-ttu-id="9d6ec-123">Um sicherzustellen, dass Unity mit seinem Weltkoordinatensystem auf Bodenebene ausgeführt wird, können Sie festlegen und testen, ob Unity den Raumtyp RoomScale-Nachverfolgung verwendet:</span><span class="sxs-lookup"><span data-stu-id="9d6ec-123">To ensure that Unity is operating with its world coordinate system at floor-level, you can set and test that Unity is using the RoomScale tracking space type:</span></span>

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```
* <span data-ttu-id="9d6ec-124">Wenn SetTrackingSpaceType "true" zurückgibt, hat Unity sein Weltkoordinatensystem erfolgreich umgeschaltet, um den Stageframe [des Verweises zu verfolgen.](../../design/coordinate-systems.md#spatial-coordinate-systems)</span><span class="sxs-lookup"><span data-stu-id="9d6ec-124">If SetTrackingSpaceType returns true, Unity has successfully switched its world coordinate system to track the [stage frame of reference](../../design/coordinate-systems.md#spatial-coordinate-systems).</span></span>
* <span data-ttu-id="9d6ec-125">Wenn SetTrackingSpaceType false zurückgibt, konnte Unity nicht zum Stageframe des Verweises wechseln, wahrscheinlich weil der Benutzer in seiner Umgebung keinen Boden eingerichtet hat.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-125">If SetTrackingSpaceType returns false, Unity was unable to switch to the stage frame of reference, likely because the user has not set up a floor in their environment.</span></span> <span data-ttu-id="9d6ec-126">Ein falscher Rückgabewert ist zwar nicht üblich, aber dies kann passieren, wenn die Phase in einem anderen Raum eingerichtet ist und das Gerät in den aktuellen Raum verschoben wird, ohne dass der Benutzer eine neue Stufe eingerichtet hat.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-126">While a false return value isn't common, it can happen if the stage is set up in a different room and the device is moved to the current room without the user setting up a new stage.</span></span>

<span data-ttu-id="9d6ec-127">Nachdem Ihre App den Raumtyp RoomScale-Nachverfolgung erfolgreich gesetzt hat, werden Inhalte auf der Ebene y=0 auf dem Boden angezeigt.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-127">Once your app successfully sets the RoomScale tracking space type, content placed on the y=0 plane will appear on the floor.</span></span> <span data-ttu-id="9d6ec-128">Der Ursprung bei 0, 0, 0 ist der spezifische Ort im Boden, an dem der Benutzer während der Einrichtung des Raums mit -Z für die Vorwärtsrichtung steht, die er während des Setups hatte.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-128">The origin at 0, 0, 0 will be the specific place on the floor where the user stood during room setup, with -Z representing the forward direction they were facing during setup.</span></span>

<span data-ttu-id="9d6ec-129">**Namespace:** *UnityEngine.Experimental.XR*</span><span class="sxs-lookup"><span data-stu-id="9d6ec-129">**Namespace:** *UnityEngine.Experimental.XR*</span></span><br>
<span data-ttu-id="9d6ec-130">**Typ:** *Grenze*</span><span class="sxs-lookup"><span data-stu-id="9d6ec-130">**Type:** *Boundary*</span></span>

<span data-ttu-id="9d6ec-131">Im Skriptcode können Sie dann die TryGetGeometry-Methode für den UnityEngine.Experimental.XR.Boundary-Typ aufrufen, um ein Begrenzungspolygon zu erhalten, und dabei den Begrenzungstyp TrackedArea angeben.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-131">In script code, you can then call the TryGetGeometry method on the UnityEngine.Experimental.XR.Boundary type to get a boundary polygon, specifying a boundary type of TrackedArea.</span></span> <span data-ttu-id="9d6ec-132">Wenn der Benutzer eine Grenze definiert hat (Sie erhalten eine Liste von  Scheitellinien), ist es sicher, dem Benutzer eine Raumerfahrung zu bieten, in der er die von Ihnen erstellten Szenen durchläuft.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-132">If the user defined a boundary (you get back a list of vertices), it's safe to deliver a **room-scale experience** to the user, where they can walk around the scene you create.</span></span>

> [!NOTE]
> <span data-ttu-id="9d6ec-133">Das System rendert die Grenze automatisch, wenn sich der Benutzer ihr nähert.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-133">The system will automatically render the boundary when the user approaches it.</span></span> <span data-ttu-id="9d6ec-134">Ihre App muss dieses Polygon nicht verwenden, um die Grenze selbst zu rendern.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-134">Your app doesn't need to use this polygon to render the boundary itself.</span></span> <span data-ttu-id="9d6ec-135">Sie können ihre Szenenobjekte jedoch mithilfe dieses Begrenzungpolygons gestalten, um sicherzustellen, dass der Benutzer diese Objekte physisch erreichen kann, ohne teleportieren zu müssen:</span><span class="sxs-lookup"><span data-stu-id="9d6ec-135">However, you may choose to lay out your scene objects using this boundary polygon, to ensure the user can physically reach those objects without teleporting:</span></span>

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="9d6ec-136">Erstellen einer weltweiten Erfahrung</span><span class="sxs-lookup"><span data-stu-id="9d6ec-136">Building a world-scale experience</span></span>

<span data-ttu-id="9d6ec-137">**Namespace:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="9d6ec-137">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="9d6ec-138">**Typ:** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="9d6ec-138">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="9d6ec-139">Für echte **Welterfahrungen** auf HoloLens, die Es Benutzern ermöglichen, mehr als 5 Meter zu erkunden, benötigen Sie neue Techniken, die über diejenigen hinausgehen, die für Raumerfahrungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-139">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="9d6ec-140">Eine wichtige Technik, die Sie verwenden, besteht darin, einen [Raumanker](../../design/coordinate-systems.md#spatial-anchors) zu erstellen, um einen Cluster von Hologrammen genau in der physischen Welt zu sperren, unabhängig davon, wie weit der Benutzer sich entfernt hat, und [diese Hologramme dann in späteren Sitzungen wieder](../../design/coordinate-systems.md#spatial-anchor-persistence)zu finden.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-140">One key technique you'll use is to create a [spatial anchor](../../design/coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, no matter how far the user has roamed, and then [find those holograms again in later sessions](../../design/coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="9d6ec-141">In Unity erstellen Sie einen Raumanker, indem Sie die **Unity-Komponente WorldAnchor** einem GameObject hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-141">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="9d6ec-142">Hinzufügen eines Weltankers</span><span class="sxs-lookup"><span data-stu-id="9d6ec-142">Adding a World Anchor</span></span>

<span data-ttu-id="9d6ec-143">Um einen Weltanker hinzuzufügen, rufen Sie AddComponent <WorldAnchor> () für das Spielobjekt mit der Transformation auf, die Sie in der realen Welt verankern möchten.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-143">To add a world anchor, call AddComponent<WorldAnchor>() on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="9d6ec-144">Das ist alles!</span><span class="sxs-lookup"><span data-stu-id="9d6ec-144">That's it!</span></span> <span data-ttu-id="9d6ec-145">Dieses Spielobjekt wird nun an seiner aktuellen Position in der physischen Welt verankert. Möglicherweise werden die Unity-Weltkoordinaten im Laufe der Zeit leicht angepasst, um die physische Ausrichtung sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-145">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="9d6ec-146">Verwenden Sie [Persistenz,](persistence-in-unity.md) um diesen verankerten Speicherort in einer zukünftigen App-Sitzung erneut zu finden.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-146">Use [persistence](persistence-in-unity.md) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="9d6ec-147">Entfernen eines Weltankers</span><span class="sxs-lookup"><span data-stu-id="9d6ec-147">Removing a World Anchor</span></span>

<span data-ttu-id="9d6ec-148">Wenn Sie nicht mehr möchten, dass das GameObject an einem physischen Ort der Welt gesperrt ist und nicht beabsichtigen, es in diesem Frame zu verschieben, können Sie einfach Destroy für die World Anchor-Komponente aufrufen.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-148">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="9d6ec-149">Wenn Sie das GameObject in diesen Frame verschieben möchten, müssen Sie stattdessen DestroyImmediate aufrufen.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-149">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="9d6ec-150">Verschieben eines world Anchored GameObject</span><span class="sxs-lookup"><span data-stu-id="9d6ec-150">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="9d6ec-151">GameObject-Objekte können nicht verschoben werden, während sich ein World Anchor darauf befindet.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-151">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="9d6ec-152">Wenn Sie das GameObject in diesen Frame verschieben müssen, müssen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="9d6ec-152">If you need to move the GameObject this frame, you need to:</span></span>
1. <span data-ttu-id="9d6ec-153">DestroyImmediate the World Anchor component</span><span class="sxs-lookup"><span data-stu-id="9d6ec-153">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="9d6ec-154">Verschieben des GameObject</span><span class="sxs-lookup"><span data-stu-id="9d6ec-154">Move the GameObject</span></span>
3. <span data-ttu-id="9d6ec-155">Fügen Sie dem GameObject eine neue World Anchor-Komponente hinzu.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-155">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="9d6ec-156">Behandeln von Änderungen an der Verkettbarkeit</span><span class="sxs-lookup"><span data-stu-id="9d6ec-156">Handling Locatability Changes</span></span>

<span data-ttu-id="9d6ec-157">Ein WorldAnchor ist in der physischen Welt zu einem bestimmten Zeitpunkt möglicherweise nicht zu finden.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-157">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="9d6ec-158">In diesem Fall aktualisiert Unity die Transformation des verankerten Objekts nicht.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-158">If that occurs, Unity won't be updating the transform of the anchored object.</span></span> <span data-ttu-id="9d6ec-159">Dies kann sich auch ändern, während eine App ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-159">This also can change while an app is running.</span></span> <span data-ttu-id="9d6ec-160">Wenn die Änderung der Verkettbarkeit nicht behandelt wird, wird das Objekt nicht an der richtigen physischen Position auf der Welt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-160">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="9d6ec-161">So werden Sie über Änderungen bei der Verkettung benachrichtigt:</span><span class="sxs-lookup"><span data-stu-id="9d6ec-161">To be notified about locatability changes:</span></span>
1. <span data-ttu-id="9d6ec-162">Abonnieren des OnTrackingChanged-Ereignisses</span><span class="sxs-lookup"><span data-stu-id="9d6ec-162">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="9d6ec-163">Behandeln des Ereignisses</span><span class="sxs-lookup"><span data-stu-id="9d6ec-163">Handle the event</span></span>

<span data-ttu-id="9d6ec-164">Das **OnTrackingChanged-Ereignis** wird immer dann aufgerufen, wenn sich der zugrunde liegende Raumanker zwischen einem Zustand ändert, in dem er nicht verkettet ist oder nicht.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-164">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="9d6ec-165">Behandeln Sie dann das -Ereignis:</span><span class="sxs-lookup"><span data-stu-id="9d6ec-165">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="9d6ec-166">Manchmal werden Anker sofort gefunden.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-166">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="9d6ec-167">In diesem Fall wird diese isLocated-Eigenschaft des Ankers auf TRUE festgelegt, wenn AddComponent <WorldAnchor> () zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-167">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="9d6ec-168">Daher wird das OnTrackingChanged-Ereignis nicht ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-168">As a result, the OnTrackingChanged event won't be triggered.</span></span> <span data-ttu-id="9d6ec-169">Ein sauberes Muster wäre das Aufrufen des OnTrackingChanged-Handlers mit dem anfänglichen IsLocated-Zustand nach dem Anfügen eines Ankers.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-169">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a><span data-ttu-id="9d6ec-170">Geräteübergreifendes Freigeben von Ankern</span><span class="sxs-lookup"><span data-stu-id="9d6ec-170">Sharing anchors across devices</span></span>

<span data-ttu-id="9d6ec-171">Verwenden <a href="/azure/spatial-anchors/overview" target="_blank">Sie Azure Spatial Anchors,</a> um einen permanenten Cloudanker aus einem lokalen WorldAnchor zu erstellen, den Ihre App dann auf mehreren HoloLens-, iOS- und Android-Geräten finden kann.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-171">Use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="9d6ec-172">Indem ein gemeinsamer Raumanker auf mehreren Geräten gemeinsam verwendet wird, kann jeder Benutzer Inhalte sehen, die relativ zu diesem Anker an derselben physischen Position gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-172">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="9d6ec-173">Dies ermöglicht gemeinsame Erfahrungen in Echtzeit.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-173">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="9d6ec-174">Probieren Sie die fünfminütigen Schnellstartanleitungen zu Azure Spatial Anchors Unity aus, um mit dem Erstellen gemeinsamer Erfahrungen in <a href="/azure/spatial-anchors/unity-overview" target="_blank">Unity zu beginnen.</a></span><span class="sxs-lookup"><span data-stu-id="9d6ec-174">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="9d6ec-175">Sobald Sie azure Spatial Anchors haben, können Sie Anker in Unity erstellen <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">und suchen.</a></span><span class="sxs-lookup"><span data-stu-id="9d6ec-175">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="9d6ec-176">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="9d6ec-176">Next Development Checkpoint</span></span>

<span data-ttu-id="9d6ec-177">Wenn Sie die Von uns an den Prüfpunkt für die Unity-Entwicklung 2017 2017 2016 2016 durchgeführte Entwicklung mithilfe von Prüfpunkten fortsetzen, sind Sie gerade dabei, die wichtigsten Mixed Reality zu erkunden.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-177">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="9d6ec-178">Von hier aus können Sie mit dem nächsten Baustein fortfahren:</span><span class="sxs-lookup"><span data-stu-id="9d6ec-178">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9d6ec-179">Anvisieren</span><span class="sxs-lookup"><span data-stu-id="9d6ec-179">Gaze</span></span>](gaze-in-unity.md)

<span data-ttu-id="9d6ec-180">Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:</span><span class="sxs-lookup"><span data-stu-id="9d6ec-180">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9d6ec-181">Gemeinsame Erfahrung</span><span class="sxs-lookup"><span data-stu-id="9d6ec-181">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="9d6ec-182">Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="9d6ec-182">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="9d6ec-183">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="9d6ec-183">See Also</span></span>
* [<span data-ttu-id="9d6ec-184">Erfahrungsskala</span><span class="sxs-lookup"><span data-stu-id="9d6ec-184">Experience scales</span></span>](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="9d6ec-185">Räumliche Phase</span><span class="sxs-lookup"><span data-stu-id="9d6ec-185">Spatial stage</span></span>](../../design/coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="9d6ec-186">Verfolgbarkeitsverlust in Unity</span><span class="sxs-lookup"><span data-stu-id="9d6ec-186">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="9d6ec-187">Raumanker</span><span class="sxs-lookup"><span data-stu-id="9d6ec-187">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="9d6ec-188">Persistenz in Unity</span><span class="sxs-lookup"><span data-stu-id="9d6ec-188">Persistence in Unity</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="9d6ec-189">Gemeinsame Erlebnisse in Unity</span><span class="sxs-lookup"><span data-stu-id="9d6ec-189">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)
* <span data-ttu-id="9d6ec-190"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="9d6ec-190"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="9d6ec-191"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK für Unity</a></span><span class="sxs-lookup"><span data-stu-id="9d6ec-191"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>