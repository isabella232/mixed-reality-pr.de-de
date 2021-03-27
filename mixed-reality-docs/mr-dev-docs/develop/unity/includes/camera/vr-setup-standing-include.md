---
ms.openlocfilehash: 5f990569ae4052377cba717b5526bb8ba51b8016
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636383"
---
# <a name="mrtk"></a>[<span data-ttu-id="cf515-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="cf515-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="cf515-102">Verwenden Sie die [mixedrealityplayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) -Klasse von mrtk für Unity, und legen Sie die **zielskala** entweder auf **Raum** oder auf **Stand** fest:</span><span class="sxs-lookup"><span data-stu-id="cf515-102">Use the [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to either **Room** or **Standing**:</span></span>

![Fenster "mrtk-Einstellungen"](../../images/mrtk-target-scale.png)

<span data-ttu-id="cf515-104">Mrtk sollte die Position von Playspace und Kamera automatisch verarbeiten, aber es ist gut, eine Überprüfung durchzuführen:</span><span class="sxs-lookup"><span data-stu-id="cf515-104">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![Mrtk-Playspace](../../images/mrtk-playspace.png)

1. <span data-ttu-id="cf515-106">Erweitern Sie im Bereich **Hierarchie** das " **mixedrealityplayspace** "-gameobject, und suchen Sie nach dem untergeordneten Objekt der **Hauptkamera** .</span><span class="sxs-lookup"><span data-stu-id="cf515-106">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="cf515-107">Suchen Sie im **Inspektor** -Panel die **Transformations** Komponente, und ändern Sie die **Position** in **(X: 0, Y: 0, Z: 0)** .</span><span class="sxs-lookup"><span data-stu-id="cf515-107">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="cf515-108">XR SDK</span><span class="sxs-lookup"><span data-stu-id="cf515-108">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="cf515-109">Legen Sie den nach Verfolgungs Ursprungs Modus für das [xrinputsubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html)fest.</span><span class="sxs-lookup"><span data-stu-id="cf515-109">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="cf515-110">Nachdem Sie das Subsystem erhalten haben, wenden Sie sich an [trysettrackingoriginmode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span><span class="sxs-lookup"><span data-stu-id="cf515-110">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Floor);
```

<span data-ttu-id="cf515-111">Und arbeiten mit dem [xrrig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)von Unity.</span><span class="sxs-lookup"><span data-stu-id="cf515-111">And work with Unity's [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html).</span></span>

![XR-rig in der Hierarchie](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="cf515-113">Legacy-WSA</span><span class="sxs-lookup"><span data-stu-id="cf515-113">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="cf515-114">Wechseln Sie zum Abschnitt **andere Einstellungen** der **Windows Store-Player-Einstellungen** .</span><span class="sxs-lookup"><span data-stu-id="cf515-114">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
2. <span data-ttu-id="cf515-115">Wählen Sie **Windows Mixed Reality** als Gerät aus, das in älteren Versionen von Unity als **Windows Holographic** aufgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="cf515-115">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
3. <span data-ttu-id="cf515-116">**Unterstützte virtuelle Realität** auswählen</span><span class="sxs-lookup"><span data-stu-id="cf515-116">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="cf515-117">Da das Hauptkamera Objekt automatisch als Kamera gekennzeichnet wird, ermöglicht Unity die gesamte Bewegung und Übersetzung.</span><span class="sxs-lookup"><span data-stu-id="cf515-117">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="cf515-118">Diese Einstellungen müssen in jeder Szene der APP auf die Kamera angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="cf515-118">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="cf515-119">Wenn Sie in Unity eine neue Szene erstellen, enthält diese standardmäßig ein Hauptkamera-gameobject in der Hierarchie, die die Kamera Komponente enthält, aber die unten aufgeführten Einstellungen sind nicht ordnungsgemäß angewendet.</span><span class="sxs-lookup"><span data-stu-id="cf515-119">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but does not have the settings below properly applied.</span></span>

<span data-ttu-id="cf515-120">**Namespace:** *unityengine. XR*</span><span class="sxs-lookup"><span data-stu-id="cf515-120">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="cf515-121">**Typ:** *xrdevice*</span><span class="sxs-lookup"><span data-stu-id="cf515-121">**Type:** *XRDevice*</span></span>

<span data-ttu-id="cf515-122">Für eine **Dauer-** oder **Raum Skalierung** müssen Sie Inhalte in Relation zum Boden platzieren.</span><span class="sxs-lookup"><span data-stu-id="cf515-122">For a **standing-scale** or **room-scale experience**, you'll need to place content relative to the floor.</span></span> <span data-ttu-id="cf515-123">Sie haben eine Begründung für den Benutzer, der die **[räumliche Phase](../../../../design/coordinate-systems.md#spatial-coordinate-systems)** verwendet, die den definierten Ursprung und die optionale Raumgrenze des Benutzers darstellt, die während der ersten Durchführung eingerichtet wird.</span><span class="sxs-lookup"><span data-stu-id="cf515-123">You reason about the user's floor using the **[spatial stage](../../../../design/coordinate-systems.md#spatial-coordinate-systems)**, which represents the user's defined floor-level origin and optional room boundary, set up during first run.</span></span>

<span data-ttu-id="cf515-124">Um sicherzustellen, dass Unity mit dem globalen Koordinatensystem auf Grundebene betrieben wird, können Sie festlegen und testen, ob Unity den Bereich für die nach Verfolgungs Fläche von roomscale verwendet:</span><span class="sxs-lookup"><span data-stu-id="cf515-124">To ensure that Unity is operating with its world coordinate system at floor-level, you can set and test that Unity is using the RoomScale tracking space type:</span></span>

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

* <span data-ttu-id="cf515-125">Wenn settrackingspacetype true zurückgibt, hat Unity das World-Koordinatensystem erfolgreich umgestellt, um den [stagingframe des Verweises](../../../../design/coordinate-systems.md#spatial-coordinate-systems)nachzuverfolgen.</span><span class="sxs-lookup"><span data-stu-id="cf515-125">If SetTrackingSpaceType returns true, Unity has successfully switched its world coordinate system to track the [stage frame of reference](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span></span>
* <span data-ttu-id="cf515-126">Wenn settrackingspacetype false zurückgibt, konnte Unity nicht in den stagingframe des Verweises wechseln. Dies liegt wahrscheinlich daran, dass der Benutzer keine Etage in der Umgebung eingerichtet hat.</span><span class="sxs-lookup"><span data-stu-id="cf515-126">If SetTrackingSpaceType returns false, Unity was unable to switch to the stage frame of reference, likely because the user has not set up a floor in their environment.</span></span> <span data-ttu-id="cf515-127">Obwohl ein falscher Rückgabewert nicht häufig vorkommt, kann dies vorkommen, wenn die Stufe in einem anderen Raum eingerichtet ist und das Gerät in den aktuellen Raum verschoben wird, ohne dass der Benutzer eine neue Stufe einrichten muss.</span><span class="sxs-lookup"><span data-stu-id="cf515-127">While a false return value isn't common, it can happen if the stage is set up in a different room and the device is moved to the current room without the user setting up a new stage.</span></span>

<span data-ttu-id="cf515-128">Nachdem Ihre APP den Typ für die Nachverfolgung von roomscale festgelegt hat, wird der Inhalt auf der Ebene "y = 0" auf der Etage angezeigt.</span><span class="sxs-lookup"><span data-stu-id="cf515-128">Once your app successfully sets the RoomScale tracking space type, content placed on the y=0 plane will appear on the floor.</span></span> <span data-ttu-id="cf515-129">Der Ursprung bei 0, 0, 0 ist die spezifische Stelle auf dem Boden, an der der Benutzer während der Raumeinrichtung Stand, wobei-Z die Vorwärtsrichtung darstellt, die während des Setups aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="cf515-129">The origin at 0, 0, 0 will be the specific place on the floor where the user stood during room setup, with -Z representing the forward direction they were facing during setup.</span></span>