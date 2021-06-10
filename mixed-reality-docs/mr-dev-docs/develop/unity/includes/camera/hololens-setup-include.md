---
ms.openlocfilehash: 6e751f5376110ddc6ae92c75b4182fba8240a356
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748482"
---
# <a name="mrtk"></a>[<span data-ttu-id="465e8-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="465e8-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="465e8-102">Befolgen Sie dieses [Schritt-für-Schritt-Tutorial,](../../tutorials/mr-learning-base-01.md) um Mixed Reality Toolkit in Ihrem Unity-Projekt hinzuzufügen und automatisch zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="465e8-102">Follow this [step-by-step tutorial](../../tutorials/mr-learning-base-01.md) to add and automatically configure Mixed Reality Toolkit in your Unity project.</span></span> <span data-ttu-id="465e8-103">Es ist auch möglich, direkt mit der [MixedRealityPlayspace-Klasse](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) von MRTK für Unity zu arbeiten und die **Zielskala** auf **World** festzulegen:</span><span class="sxs-lookup"><span data-stu-id="465e8-103">It's also possible to work directly with the [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to **World**:</span></span>

![MRTK-Einstellungsfenster](../../images/mrtk-target-scale.png)

<span data-ttu-id="465e8-105">MRTK sollte die Position des Playspace und der Kamera automatisch behandeln, aber es ist gut, folgendes zu überprüfen:</span><span class="sxs-lookup"><span data-stu-id="465e8-105">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![MRTK-Playspace](../../images/mrtk-playspace.png)

1. <span data-ttu-id="465e8-107">Erweitern Sie im **Hierarchiebereich** das **GameObject MixedRealityPlayspace,** und suchen Sie nach dem untergeordneten **Hauptkameraobjekt.**</span><span class="sxs-lookup"><span data-stu-id="465e8-107">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="465e8-108">Suchen Sie im **Inspektorbereich** nach der **Komponente Transformieren,** und ändern Sie die **Position** in **(X: 0, Y: 0, Z: 0).**</span><span class="sxs-lookup"><span data-stu-id="465e8-108">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="465e8-109">XR SDK</span><span class="sxs-lookup"><span data-stu-id="465e8-109">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="465e8-110">Legen Sie den Nachverfolgungsursprungsmodus im [XRInputSubsystem fest.](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html)</span><span class="sxs-lookup"><span data-stu-id="465e8-110">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="465e8-111">Rufen Sie nach dem Abrufen des Subsystems [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html)auf:</span><span class="sxs-lookup"><span data-stu-id="465e8-111">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Unbounded); // Recommendation for OpenXR
```

<span data-ttu-id="465e8-112">Sie können [ARSession](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) für HoloLens-Anwendungen verwenden, was mit Ankern und ARKit/ARCore besser funktioniert.</span><span class="sxs-lookup"><span data-stu-id="465e8-112">You can use [ARSession](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) for HoloLens applications, which works better with anchors and ARKit/ARCore.</span></span>

![AR-Sitzung in der Hierarchie](../../images/xrsdk-arsession.png)

> [!IMPORTANT]
> <span data-ttu-id="465e8-114">AR-Sitzung und zugehörige Features müssen AR Foundation installiert sein.</span><span class="sxs-lookup"><span data-stu-id="465e8-114">AR Session and related features need AR Foundation installed.</span></span>

<span data-ttu-id="465e8-115">Es ist auch möglich, die Kameraänderungen manuell anzuwenden, ohne ARSession zu verwenden:</span><span class="sxs-lookup"><span data-stu-id="465e8-115">It's also possible to apply the camera changes manually without using ARSession:</span></span>

1. <span data-ttu-id="465e8-116">Auswählen der **Hauptkamera** im **Hierarchiebereich**</span><span class="sxs-lookup"><span data-stu-id="465e8-116">Select **Main Camera** in the **Hierarchy** panel</span></span>
1. <span data-ttu-id="465e8-117">Suchen Sie im **Inspektorbereich** nach der **Komponente Transformieren,** und ändern Sie die **Position** in **(X: 0, Y: 0, Z: 0).**</span><span class="sxs-lookup"><span data-stu-id="465e8-117">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

   <span data-ttu-id="465e8-118">![Kamera im Inspektorbereich in Unity](../../images/maincamera-350px.png)</span><span class="sxs-lookup"><span data-stu-id="465e8-118">![Camera in the Inspector pane in Unity](../../images/maincamera-350px.png)</span></span>  
   <span data-ttu-id="465e8-119">*Kamera im Inspektorbereich in Unity*</span><span class="sxs-lookup"><span data-stu-id="465e8-119">*Camera in the Inspector pane in Unity*</span></span>

1. <span data-ttu-id="465e8-120">Hinzufügen eines **TrackedPoseDriver** zur **Hauptkamera**</span><span class="sxs-lookup"><span data-stu-id="465e8-120">Add a **TrackedPoseDriver** to the **Main Camera**</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="465e8-121">Legacy-WSA</span><span class="sxs-lookup"><span data-stu-id="465e8-121">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="465e8-122">Auswählen der **Hauptkamera** im **Hierarchiebereich**</span><span class="sxs-lookup"><span data-stu-id="465e8-122">Select **Main Camera** in the **Hierarchy** panel</span></span>
1. <span data-ttu-id="465e8-123">Suchen Sie im **Inspektorbereich** nach der **Komponente Transformieren,** und ändern Sie die **Position** in **(X: 0, Y: 0, Z: 0).**</span><span class="sxs-lookup"><span data-stu-id="465e8-123">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

   <span data-ttu-id="465e8-124">![Kamera im Inspektorbereich in Unity](../../images/maincamera-350px.png)</span><span class="sxs-lookup"><span data-stu-id="465e8-124">![Camera in the Inspector pane in Unity](../../images/maincamera-350px.png)</span></span>  
   <span data-ttu-id="465e8-125">*Kamera im Inspektorbereich in Unity*</span><span class="sxs-lookup"><span data-stu-id="465e8-125">*Camera in the Inspector pane in Unity*</span></span>

1. <span data-ttu-id="465e8-126">Wechseln Sie zum Abschnitt **Andere Einstellungen** der Windows **Store Player-Einstellungen.**</span><span class="sxs-lookup"><span data-stu-id="465e8-126">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
1. <span data-ttu-id="465e8-127">Wählen Sie **Windows Mixed Reality** als Gerät aus, das in älteren Versionen von Unity als **Windows Holographic** aufgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="465e8-127">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
1. <span data-ttu-id="465e8-128">Wählen Sie **Virtual Reality Supported (Unterstützte Virtuelle Realität) aus.**</span><span class="sxs-lookup"><span data-stu-id="465e8-128">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="465e8-129">Da das Hauptkameraobjekt automatisch als Kamera gekennzeichnet wird, unterstützt Unity alle Bewegungen und Übersetzungen.</span><span class="sxs-lookup"><span data-stu-id="465e8-129">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="465e8-130">Diese Einstellungen müssen in jeder Szene Ihrer App auf die Kamera angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="465e8-130">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="465e8-131">Wenn Sie eine neue Szene in Unity erstellen, enthält sie standardmäßig ein Hauptkamera-GameObject in der Hierarchie, das die Kamerakomponente enthält, aber möglicherweise nicht ordnungsgemäß auf die Einstellungen angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="465e8-131">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but may not have the settings properly applied.</span></span>