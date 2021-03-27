---
ms.openlocfilehash: c7e5be36420ef14fe5aaeaafb49c0a990942339f
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636380"
---
# <a name="mrtk"></a>[<span data-ttu-id="3bcef-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="3bcef-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="3bcef-102">Verwenden Sie die [mixedrealityplayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) -Klasse von mrtk für Unity, und legen Sie die **zielskala** auf " **sitzend**" fest:</span><span class="sxs-lookup"><span data-stu-id="3bcef-102">Use the [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to **Seated**:</span></span>

![Fenster "mrtk-Einstellungen"](../../images/mrtk-target-scale.png)

<span data-ttu-id="3bcef-104">Mrtk sollte die Position von Playspace und Kamera automatisch verarbeiten, aber es ist gut, eine Überprüfung durchzuführen:</span><span class="sxs-lookup"><span data-stu-id="3bcef-104">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![Mrtk-Playspace](../../images/mrtk-playspace.png)

1. <span data-ttu-id="3bcef-106">Erweitern Sie im Bereich **Hierarchie** das " **mixedrealityplayspace** "-gameobject, und suchen Sie nach dem untergeordneten Objekt der **Hauptkamera** .</span><span class="sxs-lookup"><span data-stu-id="3bcef-106">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="3bcef-107">Suchen Sie im **Inspektor** -Panel die **Transformations** Komponente, und ändern Sie die **Position** in **(X: 0, Y: 0, Z: 0)** .</span><span class="sxs-lookup"><span data-stu-id="3bcef-107">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="3bcef-108">XR SDK</span><span class="sxs-lookup"><span data-stu-id="3bcef-108">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="3bcef-109">Legen Sie den nach Verfolgungs Ursprungs Modus für das [xrinputsubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html)fest.</span><span class="sxs-lookup"><span data-stu-id="3bcef-109">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="3bcef-110">Nachdem Sie das Subsystem erhalten haben, wenden Sie sich an [trysettrackingoriginmode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span><span class="sxs-lookup"><span data-stu-id="3bcef-110">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
```

<span data-ttu-id="3bcef-111">Und arbeiten mit dem [xrrig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)von Unity.</span><span class="sxs-lookup"><span data-stu-id="3bcef-111">And work with Unity's [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html).</span></span>

![XR-rig in der Hierarchie](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="3bcef-113">Legacy-WSA</span><span class="sxs-lookup"><span data-stu-id="3bcef-113">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="3bcef-114">Wechseln Sie zum Abschnitt **andere Einstellungen** der **Windows Store-Player-Einstellungen** .</span><span class="sxs-lookup"><span data-stu-id="3bcef-114">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
2. <span data-ttu-id="3bcef-115">Wählen Sie **Windows Mixed Reality** als Gerät aus, das in älteren Versionen von Unity als **Windows Holographic** aufgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="3bcef-115">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
3. <span data-ttu-id="3bcef-116">**Unterstützte virtuelle Realität** auswählen</span><span class="sxs-lookup"><span data-stu-id="3bcef-116">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="3bcef-117">Da das Hauptkamera Objekt automatisch als Kamera gekennzeichnet wird, ermöglicht Unity die gesamte Bewegung und Übersetzung.</span><span class="sxs-lookup"><span data-stu-id="3bcef-117">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="3bcef-118">Diese Einstellungen müssen in jeder Szene der APP auf die Kamera angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="3bcef-118">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="3bcef-119">Wenn Sie in Unity eine neue Szene erstellen, enthält diese standardmäßig ein Hauptkamera-gameobject in der Hierarchie, die die Kamera Komponente enthält, aber die unten aufgeführten Einstellungen sind nicht ordnungsgemäß angewendet.</span><span class="sxs-lookup"><span data-stu-id="3bcef-119">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but does not have the settings below properly applied.</span></span>

<span data-ttu-id="3bcef-120">**Namespace:** *unityengine. XR*</span><span class="sxs-lookup"><span data-stu-id="3bcef-120">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="3bcef-121">**Typ:** *xrdevice*</span><span class="sxs-lookup"><span data-stu-id="3bcef-121">**Type:** *XRDevice*</span></span>

<span data-ttu-id="3bcef-122">Zum Erstellen einer reinen **Orientierung** oder einer **Skalierungs** Funktion müssen Sie Unity auf den Typ des stationären nach Verfolgungs Raums festlegen.</span><span class="sxs-lookup"><span data-stu-id="3bcef-122">To build an **orientation-only** or **seated-scale experience**, you need to set Unity to the Stationary tracking space type.</span></span> <span data-ttu-id="3bcef-123">Stationärer nach Verfolgungs Raum legt das World-Koordinatensystem von Unity fest, um den [stationären Verweis Rahmen](../../../../design/coordinate-systems.md#spatial-coordinate-systems)zu verfolgen.</span><span class="sxs-lookup"><span data-stu-id="3bcef-123">Stationary tracking space sets Unity's world coordinate system to track the [stationary frame of reference](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span></span> <span data-ttu-id="3bcef-124">Im Modus der stationären Nachverfolgung wird der Inhalt, der direkt vor dem Standard Speicherort der Kamera (vorwärts ist-Z) im Editor eingefügt wird, vor dem Benutzer angezeigt, wenn die APP gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="3bcef-124">In the Stationary tracking mode, content placed in the editor just in front of the camera's default location (forward is -Z) will appear in front of the user when the app launches.</span></span>

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

<span data-ttu-id="3bcef-125">**Namespace:** *unityengine. XR*</span><span class="sxs-lookup"><span data-stu-id="3bcef-125">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="3bcef-126">**Typ:** *inputtracking*</span><span class="sxs-lookup"><span data-stu-id="3bcef-126">**Type:** *InputTracking*</span></span>

<span data-ttu-id="3bcef-127">Bei einer reinen **Orientierung** , z. b. bei einem Video Viewer mit einem 360-Grad (bei dem Positions Aktualisierungen die Illusion zerstören würden), können Sie "XR" festlegen [. Inputtracking. disablepositionaltracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) auf true:</span><span class="sxs-lookup"><span data-stu-id="3bcef-127">For a pure **orientation-only experience** such as a 360-degree video viewer (where positional head updates would ruin the illusion), you can then set [XR.InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) to true:</span></span>

```cs
InputTracking.disablePositionalTracking = true;
```

<span data-ttu-id="3bcef-128">Um dem Benutzer die Möglichkeit zu geben, den sitzenden Ursprung zu einem späteren Zeitpunkt wieder einzugeben, können Sie den XR-Vorgang für eine Benutzer **freundliche Skalierung** durchführen [. Inputtracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) -Methode:</span><span class="sxs-lookup"><span data-stu-id="3bcef-128">For a **seated-scale experience**, to let the user later recenter the seated origin, you can call the [XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) method:</span></span>

```cs
InputTracking.Recenter();
```

<span data-ttu-id="3bcef-129">Wenn Sie eine Umgebung mit [sitzender Skalierung](../../../../design/coordinate-systems.md)entwickeln, können Sie den Welt Ursprung von Unity an der aktuellen Hauptposition des Benutzers wiederholen, indem Sie den **[XR aufrufen. Inputtracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** -Methode.</span><span class="sxs-lookup"><span data-stu-id="3bcef-129">If you're building a [seated-scale experience](../../../../design/coordinate-systems.md), you can recenter Unity's world origin at the user's current head position by calling the **[XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** method.</span></span>