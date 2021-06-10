---
ms.openlocfilehash: 61fe8754192c1fbd0634fd9d1e1994327599321b
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748521"
---
# <a name="mrtk"></a>[<span data-ttu-id="1290f-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="1290f-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="1290f-102">Verwenden Sie [die MixedRealityPlayspace-Klasse](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) von MRTK für Unity, und legen Sie die **Zielskala** entweder **auf Room oder** Standing **fest:**</span><span class="sxs-lookup"><span data-stu-id="1290f-102">Use the [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to either **Room** or **Standing**:</span></span>

![MRTK-Einstellungsfenster](../../images/mrtk-target-scale.png)

<span data-ttu-id="1290f-104">MRTK sollte die Position des Playspace und der Kamera automatisch verarbeiten, aber es ist gut, dies zu überprüfen:</span><span class="sxs-lookup"><span data-stu-id="1290f-104">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![MRTK-Playspace](../../images/mrtk-playspace.png)

1. <span data-ttu-id="1290f-106">Erweitern Sie **im Bereich Hierarchie** das **GameObject MixedRealityPlayspace,** und suchen Sie nach dem **untergeordneten Hauptkameraobjekt.**</span><span class="sxs-lookup"><span data-stu-id="1290f-106">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="1290f-107">Suchen Sie **im Inspektorbereich** nach der **Komponente Transformieren,** und ändern Sie die **Position** in **(X: 0, Y: 0, Z: 0).**</span><span class="sxs-lookup"><span data-stu-id="1290f-107">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="1290f-108">XR SDK</span><span class="sxs-lookup"><span data-stu-id="1290f-108">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="1290f-109">Legen Sie den Ursprungsmodus für die Nachverfolgung auf [dem XRInputSubsystem fest.](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html)</span><span class="sxs-lookup"><span data-stu-id="1290f-109">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="1290f-110">Rufen Sie nach dem Abrufen des Subsystems [TrySetTrackingOriginMode auf:](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html)</span><span class="sxs-lookup"><span data-stu-id="1290f-110">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Floor);
```

<span data-ttu-id="1290f-111">Und arbeiten mit [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)von Unity.</span><span class="sxs-lookup"><span data-stu-id="1290f-111">And work with Unity's [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html).</span></span>

![XR-Warte in der Hierarchie](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="1290f-113">Legacy-WSA</span><span class="sxs-lookup"><span data-stu-id="1290f-113">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="1290f-114">Wechseln Sie **in den Einstellungen des** Windows **Store-Players** zum Abschnitt Andere Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="1290f-114">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
2. <span data-ttu-id="1290f-115">Wählen **Windows Mixed Reality** als Gerät aus, das in älteren Versionen von Unity möglicherweise als **Windows Holographic** aufgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="1290f-115">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
3. <span data-ttu-id="1290f-116">Wählen Sie **Virtual Reality Supported (Unterstützte virtuelle Realität) aus.**</span><span class="sxs-lookup"><span data-stu-id="1290f-116">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="1290f-117">Da das Hauptkameraobjekt automatisch als Kamera gekennzeichnet wird, wird unity für alle Bewegungen und Übersetzungen verwendet.</span><span class="sxs-lookup"><span data-stu-id="1290f-117">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="1290f-118">Diese Einstellungen müssen auf die Kamera in jeder Szene Ihrer App angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="1290f-118">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="1290f-119">Wenn Sie eine neue Szene in Unity erstellen, enthält sie standardmäßig ein Hauptkamera-GameObject in der Hierarchie, das die Kamerakomponente enthält, aber die unten aufgeführten Einstellungen nicht ordnungsgemäß angewendet haben.</span><span class="sxs-lookup"><span data-stu-id="1290f-119">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but does not have the settings below properly applied.</span></span>

<span data-ttu-id="1290f-120">**Namespace:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="1290f-120">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="1290f-121">**Typ:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="1290f-121">**Type:** *XRDevice*</span></span>

<span data-ttu-id="1290f-122">Für eine **Erfahrung im Stehend-** oder **Raummaßstab** müssen Sie Inhalte relativ zum Boden platzieren.</span><span class="sxs-lookup"><span data-stu-id="1290f-122">For a **standing-scale** or **room-scale experience**, you'll need to place content relative to the floor.</span></span> <span data-ttu-id="1290f-123">Sie können den Grund für **[](../../../../design/coordinate-systems.md#spatial-coordinate-systems)** den Boden des Benutzers mithilfe der räumlichen Stufe festlegen, die den vom Benutzer definierten Ursprung auf Bodenebene und die optionale Raumgrenze darstellt, die während der ersten Ausführung eingerichtet wurde.</span><span class="sxs-lookup"><span data-stu-id="1290f-123">You reason about the user's floor using the **[spatial stage](../../../../design/coordinate-systems.md#spatial-coordinate-systems)**, which represents the user's defined floor-level origin and optional room boundary, set up during first run.</span></span>

<span data-ttu-id="1290f-124">Um sicherzustellen, dass Unity mit seinem Weltkoordinatensystem auf Bodenebene ausgeführt wird, können Sie festlegen und testen, ob Unity den Raumtyp RoomScale-Nachverfolgung verwendet:</span><span class="sxs-lookup"><span data-stu-id="1290f-124">To ensure that Unity is operating with its world coordinate system at floor-level, you can set and test that Unity is using the RoomScale tracking space type:</span></span>

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

* <span data-ttu-id="1290f-125">Wenn SetTrackingSpaceType TRUE zurückgibt, hat Unity sein Weltkoordinatensystem erfolgreich umgeschaltet, um den Stageframe [des Verweises nachverfolgung zu können.](../../../../design/coordinate-systems.md#spatial-coordinate-systems)</span><span class="sxs-lookup"><span data-stu-id="1290f-125">If SetTrackingSpaceType returns true, Unity has successfully switched its world coordinate system to track the [stage frame of reference](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span></span>
* <span data-ttu-id="1290f-126">Wenn SetTrackingSpaceType false zurückgibt, konnte Unity nicht zum Stageframe des Verweises wechseln, wahrscheinlich weil der Benutzer in seiner Umgebung keinen Boden eingerichtet hat.</span><span class="sxs-lookup"><span data-stu-id="1290f-126">If SetTrackingSpaceType returns false, Unity was unable to switch to the stage frame of reference, likely because the user has not set up a floor in their environment.</span></span> <span data-ttu-id="1290f-127">Obwohl ein falscher Rückgabewert nicht üblich ist, kann dies passieren, wenn die Phase in einem anderen Raum eingerichtet wird und das Gerät in den aktuellen Raum verschoben wird, ohne dass der Benutzer eine neue Stufe eingerichtet hat.</span><span class="sxs-lookup"><span data-stu-id="1290f-127">While a false return value isn't common, it can happen if the stage is set up in a different room and the device is moved to the current room without the user setting up a new stage.</span></span>

<span data-ttu-id="1290f-128">Nachdem Ihre App den Raumtyp RoomScale-Nachverfolgung erfolgreich gesetzt hat, werden Inhalte auf der Ebene y=0 im Boden angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1290f-128">Once your app successfully sets the RoomScale tracking space type, content placed on the y=0 plane will appear on the floor.</span></span> <span data-ttu-id="1290f-129">Der Ursprung bei 0, 0, 0 ist der spezifische Ort im Boden, an dem der Benutzer während der Einrichtung des Raums mit -Z für die Vorwärtsrichtung steht, die er während des Setups hatte.</span><span class="sxs-lookup"><span data-stu-id="1290f-129">The origin at 0, 0, 0 will be the specific place on the floor where the user stood during room setup, with -Z representing the forward direction they were facing during setup.</span></span>