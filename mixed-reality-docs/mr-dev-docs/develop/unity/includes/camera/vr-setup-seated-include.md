---
ms.openlocfilehash: 3bffb5db8f4a36d04c2b408c939cbd2010a7def7
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748528"
---
# <a name="mrtk"></a>[<span data-ttu-id="1f8d9-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="1f8d9-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="1f8d9-102">Verwenden Sie die [MixedRealityPlayspace-Klasse](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) von MRTK für Unity, und legen Sie die **Zielskala** auf **Seated fest:**</span><span class="sxs-lookup"><span data-stu-id="1f8d9-102">Use the [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to **Seated**:</span></span>

![MRTK-Einstellungsfenster](../../images/mrtk-target-scale.png)

<span data-ttu-id="1f8d9-104">MRTK sollte die Position des Playspace und der Kamera automatisch behandeln, aber es ist gut, folgendes zu überprüfen:</span><span class="sxs-lookup"><span data-stu-id="1f8d9-104">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![MRTK-Playspace](../../images/mrtk-playspace.png)

1. <span data-ttu-id="1f8d9-106">Erweitern Sie im **Hierarchiebereich** das **GameObject MixedRealityPlayspace,** und suchen Sie nach dem untergeordneten **Hauptkameraobjekt.**</span><span class="sxs-lookup"><span data-stu-id="1f8d9-106">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="1f8d9-107">Suchen Sie im **Inspektorbereich** nach der **Komponente Transformieren,** und ändern Sie die **Position** in **(X: 0, Y: 0, Z: 0).**</span><span class="sxs-lookup"><span data-stu-id="1f8d9-107">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="1f8d9-108">XR SDK</span><span class="sxs-lookup"><span data-stu-id="1f8d9-108">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="1f8d9-109">Legen Sie den Nachverfolgungsursprungsmodus im [XRInputSubsystem fest.](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html)</span><span class="sxs-lookup"><span data-stu-id="1f8d9-109">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="1f8d9-110">Rufen Sie nach dem Abrufen des Subsystems [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html)auf:</span><span class="sxs-lookup"><span data-stu-id="1f8d9-110">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
```

<span data-ttu-id="1f8d9-111">Und arbeiten Sie mit [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)von Unity.</span><span class="sxs-lookup"><span data-stu-id="1f8d9-111">And work with Unity's [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html).</span></span>

![XR-Struktur in der Hierarchie](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="1f8d9-113">Legacy-WSA</span><span class="sxs-lookup"><span data-stu-id="1f8d9-113">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="1f8d9-114">Wechseln Sie zum Abschnitt **Andere Einstellungen** der Windows **Store Player-Einstellungen.**</span><span class="sxs-lookup"><span data-stu-id="1f8d9-114">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
2. <span data-ttu-id="1f8d9-115">Wählen Sie **Windows Mixed Reality** als Gerät aus, das in älteren Versionen von Unity als **Windows Holographic** aufgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="1f8d9-115">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
3. <span data-ttu-id="1f8d9-116">Wählen Sie **Virtual Reality Supported (Unterstützte Virtuelle Realität) aus.**</span><span class="sxs-lookup"><span data-stu-id="1f8d9-116">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="1f8d9-117">Da das Hauptkameraobjekt automatisch als Kamera gekennzeichnet wird, unterstützt Unity alle Bewegungen und Übersetzungen.</span><span class="sxs-lookup"><span data-stu-id="1f8d9-117">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="1f8d9-118">Diese Einstellungen müssen in jeder Szene Ihrer App auf die Kamera angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="1f8d9-118">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="1f8d9-119">Wenn Sie eine neue Szene in Unity erstellen, enthält sie standardmäßig ein Hauptkamera-GameObject in der Hierarchie, das die Kamerakomponente enthält, aber die unten angegebenen Einstellungen nicht ordnungsgemäß angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="1f8d9-119">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but does not have the settings below properly applied.</span></span>

<span data-ttu-id="1f8d9-120">**Namespace:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="1f8d9-120">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="1f8d9-121">**Typ:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="1f8d9-121">**Type:** *XRDevice*</span></span>

<span data-ttu-id="1f8d9-122">Zum Erstellen einer **reinen ausrichtungsbasierten** oder **besetzen Benutzeroberfläche** müssen Sie Unity auf den Typ Stationärer Nachverfolgungsbereich festlegen.</span><span class="sxs-lookup"><span data-stu-id="1f8d9-122">To build an **orientation-only** or **seated-scale experience**, you need to set Unity to the Stationary tracking space type.</span></span> <span data-ttu-id="1f8d9-123">Der ortsaufstärkungsraum legt das Weltkoordinatensystem von Unity fest, um den [stationären Bezugsrahmen](../../../../design/coordinate-systems.md#spatial-coordinate-systems)nachzuverfolgen.</span><span class="sxs-lookup"><span data-stu-id="1f8d9-123">Stationary tracking space sets Unity's world coordinate system to track the [stationary frame of reference](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span></span> <span data-ttu-id="1f8d9-124">Im Nachverfolgungsmodus "Stationär" werden Inhalte, die im Editor direkt vor der Standardposition der Kamera platziert werden (forward ist -Z), vor dem Benutzer angezeigt, wenn die App gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="1f8d9-124">In the Stationary tracking mode, content placed in the editor just in front of the camera's default location (forward is -Z) will appear in front of the user when the app launches.</span></span>

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

<span data-ttu-id="1f8d9-125">**Namespace:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="1f8d9-125">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="1f8d9-126">**Typ:** *InputTracking*</span><span class="sxs-lookup"><span data-stu-id="1f8d9-126">**Type:** *InputTracking*</span></span>

<span data-ttu-id="1f8d9-127">Für eine reine **Ausrichtungserfahrung** wie einen 360-Grad-Videoviewer (bei dem Positionskopfupdates die Vorstellungen verfälschen würden), können Sie dann [XR festlegen. InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) auf TRUE:</span><span class="sxs-lookup"><span data-stu-id="1f8d9-127">For a pure **orientation-only experience** such as a 360-degree video viewer (where positional head updates would ruin the illusion), you can then set [XR.InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) to true:</span></span>

```cs
InputTracking.disablePositionalTracking = true;
```

<span data-ttu-id="1f8d9-128">Für eine **benutzerdefinierte Benutzeroberfläche** können Sie XR aufrufen, damit der Benutzer später den stammseitigen Ursprung erhalten [kann. InputTracking.Recenter-Methode:](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)</span><span class="sxs-lookup"><span data-stu-id="1f8d9-128">For a **seated-scale experience**, to let the user later recenter the seated origin, you can call the [XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) method:</span></span>

```cs
InputTracking.Recenter();
```

<span data-ttu-id="1f8d9-129">Wenn Sie eine [benutzerdefinierte Benutzeroberfläche](../../../../design/coordinate-systems.md)erstellen, können Sie den weltweiten Ursprung von Unity an der aktuellen Kopfposition des Benutzers durch Aufrufen von **[XR aufrufen. InputTracking.Recenter-Methode.](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)**</span><span class="sxs-lookup"><span data-stu-id="1f8d9-129">If you're building a [seated-scale experience](../../../../design/coordinate-systems.md), you can recenter Unity's world origin at the user's current head position by calling the **[XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** method.</span></span>