---
ms.openlocfilehash: 7470690a96380184ead7319d4461005042c6db82
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636301"
---
# <a name="mrtk"></a>[<span data-ttu-id="d35a2-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="d35a2-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="d35a2-102">Führen Sie dieses [Schritt-für-Schritt-Tutorial](../../tutorials/mr-learning-base-01.md) aus, um das Mixed Reality Toolkit in Ihrem Unity-Projekt hinzuzufügen und automatisch zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="d35a2-102">Follow this [step-by-step tutorial](../../tutorials/mr-learning-base-01.md) to add and automatically configure Mixed Reality Toolkit in your Unity project.</span></span> <span data-ttu-id="d35a2-103">Es ist auch möglich, direkt mit der [mixedrealityplayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) -Klasse von mrtk für Unity zu arbeiten und die **zielskala** auf **World** festzulegen:</span><span class="sxs-lookup"><span data-stu-id="d35a2-103">It's also possible to work directly with the [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to **World**:</span></span>

![Fenster "mrtk-Einstellungen"](../../images/mrtk-target-scale.png)

<span data-ttu-id="d35a2-105">Mrtk sollte die Position von Playspace und Kamera automatisch verarbeiten, aber es ist gut, eine Überprüfung durchzuführen:</span><span class="sxs-lookup"><span data-stu-id="d35a2-105">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![Mrtk-Playspace](../../images/mrtk-playspace.png)

1. <span data-ttu-id="d35a2-107">Erweitern Sie im Bereich **Hierarchie** das " **mixedrealityplayspace** "-gameobject, und suchen Sie nach dem untergeordneten Objekt der **Hauptkamera** .</span><span class="sxs-lookup"><span data-stu-id="d35a2-107">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="d35a2-108">Suchen Sie im **Inspektor** -Panel die **Transformations** Komponente, und ändern Sie die **Position** in **(X: 0, Y: 0, Z: 0)** .</span><span class="sxs-lookup"><span data-stu-id="d35a2-108">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="d35a2-109">XR SDK</span><span class="sxs-lookup"><span data-stu-id="d35a2-109">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="d35a2-110">Legen Sie den nach Verfolgungs Ursprungs Modus für das [xrinputsubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html)fest.</span><span class="sxs-lookup"><span data-stu-id="d35a2-110">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="d35a2-111">Nachdem Sie das Subsystem erhalten haben, wenden Sie sich an [trysettrackingoriginmode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span><span class="sxs-lookup"><span data-stu-id="d35a2-111">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Unbounded); // Recommendation for OpenXR
```

<span data-ttu-id="d35a2-112">Sie können [arsession](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) für hololens-Anwendungen verwenden, die mit Anker und Arkit/Arcore besser funktionieren.</span><span class="sxs-lookup"><span data-stu-id="d35a2-112">You can use [ARSession](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) for HoloLens applications, which works better with anchors and ARKit/ARCore.</span></span>

![AR-Sitzung in der Hierarchie](../../images/xrsdk-arsession.png)

> [!IMPORTANT]
> <span data-ttu-id="d35a2-114">Für AR-Sitzung und verwandte Funktionen muss AR Foundation installiert sein.</span><span class="sxs-lookup"><span data-stu-id="d35a2-114">AR Session and related features need AR Foundation installed.</span></span>

<span data-ttu-id="d35a2-115">Es ist auch möglich, die Kamera Änderungen manuell ohne die Verwendung von "arsession" anzuwenden:</span><span class="sxs-lookup"><span data-stu-id="d35a2-115">It's also possible to apply the camera changes manually without using ARSession:</span></span>

1. <span data-ttu-id="d35a2-116">Auswählen der **Hauptkamera** im **Hierarchie** Panel</span><span class="sxs-lookup"><span data-stu-id="d35a2-116">Select **Main Camera** in the **Hierarchy** panel</span></span>
1. <span data-ttu-id="d35a2-117">Suchen Sie im **Inspektor** -Panel die **Transformations** Komponente, und ändern Sie die **Position** in **(X: 0, Y: 0, Z: 0)** .</span><span class="sxs-lookup"><span data-stu-id="d35a2-117">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

   <span data-ttu-id="d35a2-118">![Kamera im Inspektor-Bereich in Unity](../../images/maincamera-350px.png)</span><span class="sxs-lookup"><span data-stu-id="d35a2-118">![Camera in the Inspector pane in Unity](../../images/maincamera-350px.png)</span></span>  
   <span data-ttu-id="d35a2-119">*Kamera im Inspektor-Bereich in Unity*</span><span class="sxs-lookup"><span data-stu-id="d35a2-119">*Camera in the Inspector pane in Unity*</span></span>

1. <span data-ttu-id="d35a2-120">Hinzufügen eines **trackedtargedriver** zur **Hauptkamera**</span><span class="sxs-lookup"><span data-stu-id="d35a2-120">Add a **TrackedPoseDriver** to the **Main Camera**</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="d35a2-121">Legacy-WSA</span><span class="sxs-lookup"><span data-stu-id="d35a2-121">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="d35a2-122">Auswählen der **Hauptkamera** im **Hierarchie** Panel</span><span class="sxs-lookup"><span data-stu-id="d35a2-122">Select **Main Camera** in the **Hierarchy** panel</span></span>
1. <span data-ttu-id="d35a2-123">Suchen Sie im **Inspektor** -Panel die **Transformations** Komponente, und ändern Sie die **Position** in **(X: 0, Y: 0, Z: 0)** .</span><span class="sxs-lookup"><span data-stu-id="d35a2-123">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

   <span data-ttu-id="d35a2-124">![Kamera im Inspektor-Bereich in Unity](../../images/maincamera-350px.png)</span><span class="sxs-lookup"><span data-stu-id="d35a2-124">![Camera in the Inspector pane in Unity](../../images/maincamera-350px.png)</span></span>  
   <span data-ttu-id="d35a2-125">*Kamera im Inspektor-Bereich in Unity*</span><span class="sxs-lookup"><span data-stu-id="d35a2-125">*Camera in the Inspector pane in Unity*</span></span>

1. <span data-ttu-id="d35a2-126">Wechseln Sie zum Abschnitt **andere Einstellungen** der **Windows Store-Player-Einstellungen** .</span><span class="sxs-lookup"><span data-stu-id="d35a2-126">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
1. <span data-ttu-id="d35a2-127">Wählen Sie **Windows Mixed Reality** als Gerät aus, das in älteren Versionen von Unity als **Windows Holographic** aufgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="d35a2-127">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
1. <span data-ttu-id="d35a2-128">**Unterstützte virtuelle Realität** auswählen</span><span class="sxs-lookup"><span data-stu-id="d35a2-128">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="d35a2-129">Da das Hauptkamera Objekt automatisch als Kamera gekennzeichnet wird, ermöglicht Unity die gesamte Bewegung und Übersetzung.</span><span class="sxs-lookup"><span data-stu-id="d35a2-129">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="d35a2-130">Diese Einstellungen müssen in jeder Szene der APP auf die Kamera angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="d35a2-130">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="d35a2-131">Wenn Sie in Unity eine neue Szene erstellen, enthält diese standardmäßig ein Hauptkamera-gameobject in der Hierarchie, die die Kamera Komponente enthält, die Einstellungen aber möglicherweise nicht ordnungsgemäß angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="d35a2-131">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but may not have the settings properly applied.</span></span>