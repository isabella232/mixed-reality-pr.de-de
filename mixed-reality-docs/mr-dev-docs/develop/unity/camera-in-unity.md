---
title: Kamera Einrichtung in Unity
description: Erfahren Sie, wie Sie die Hauptkamera von Unity für die Windows Mixed Reality-Entwicklung einrichten und verwenden, um Holographic Rendering durchzuführen.
author: keveleigh
ms.author: kurtie
ms.date: 03/25/2021
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Holographic-Rendering, Holographic, immersive, Fokuspunkt, tiefen Puffer, nur Ausrichtung, Positional, nicht transparent, transparent, Clip, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: d3f69c6cf1889587b23b68259f22b34b89b925a4
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636298"
---
# <a name="camera-setup-in-unity"></a><span data-ttu-id="b0152-104">Kamera Einrichtung in Unity</span><span class="sxs-lookup"><span data-stu-id="b0152-104">Camera setup in Unity</span></span>

<span data-ttu-id="b0152-105">Wenn Sie ein Mixed Reality-Headset durch tragen, wird es zur Mitte ihrer Holographic World.</span><span class="sxs-lookup"><span data-stu-id="b0152-105">When you wear a mixed reality headset, it becomes the center of your holographic world.</span></span> <span data-ttu-id="b0152-106">Die Unity- [Kamera](https://docs.unity3d.com/Manual/class-Camera.html) Komponente verarbeitet das stereorenderingrendering automatisch und folgt der Bewegung und Drehung des Kopfes.</span><span class="sxs-lookup"><span data-stu-id="b0152-106">The Unity [Camera](https://docs.unity3d.com/Manual/class-Camera.html) component will automatically handle stereoscopic rendering and follow your head movement and rotation.</span></span> <span data-ttu-id="b0152-107">Sie sollten jedoch die unten beschriebenen Kameraeinstellungen festlegen, um die visuelle Qualität und die [Stabilität des Hologramms](../platform-capabilities-and-apis/hologram-stability.md)vollständig zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="b0152-107">However, to fully optimize visual quality and [hologram stability](../platform-capabilities-and-apis/hologram-stability.md), you should set the camera settings described below.</span></span>

## <a name="hololens-vs-vr-immersive-headsets"></a><span data-ttu-id="b0152-108">Hololens im Vergleich zu den von VR immersiven Headsets</span><span class="sxs-lookup"><span data-stu-id="b0152-108">HoloLens vs VR immersive headsets</span></span>

<span data-ttu-id="b0152-109">Die Standardeinstellungen für die Unity-Kamera-Komponente gelten für herkömmliche 3D-Anwendungen, die einen Skybox-ähnlichen Hintergrund benötigen, da Sie nicht über eine reale Welt verfügen.</span><span class="sxs-lookup"><span data-stu-id="b0152-109">The default settings on the Unity Camera component are for traditional 3D applications, which need a skybox-like background as they don't have a real world.</span></span>

* <span data-ttu-id="b0152-110">Bei der Ausführung auf einem **[immersiven Headset](../../discover/immersive-headset-hardware-details.md)** Rendern Sie alles, was dem Benutzer angezeigt wird, und Sie möchten die Skybox wahrscheinlich behalten.</span><span class="sxs-lookup"><span data-stu-id="b0152-110">When running on an **[immersive headset](../../discover/immersive-headset-hardware-details.md)**, you're rendering everything the user sees, and so you'll likely want to keep the skybox.</span></span>
* <span data-ttu-id="b0152-111">Wenn Sie jedoch auf einem **Holographic-Headset** wie [hololens](/hololens/hololens2-hardware)ausgeführt werden, sollte die reale Welt hinter der von der Kamera gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="b0152-111">However, when running on a **holographic headset** like [HoloLens](/hololens/hololens2-hardware), the real world should appear behind everything the camera renders.</span></span> <span data-ttu-id="b0152-112">Legen Sie den Kamera Hintergrund auf "transparent" (in hololens, schwarz rendert als transparent) anstelle einer Skybox-Textur fest:</span><span class="sxs-lookup"><span data-stu-id="b0152-112">Set the camera background to be transparent (in HoloLens, black renders as transparent) instead of a Skybox texture:</span></span>
    1. <span data-ttu-id="b0152-113">Wählen Sie die Hauptkamera im Hierarchie Panel aus.</span><span class="sxs-lookup"><span data-stu-id="b0152-113">Select the Main Camera in the Hierarchy panel</span></span>
    2. <span data-ttu-id="b0152-114">Suchen Sie im Inspektor-Panel die Kamera Komponente, und ändern Sie die Dropdown Liste Flag Löschen von Skybox in voll Tonfarbe.</span><span class="sxs-lookup"><span data-stu-id="b0152-114">In the Inspector panel, find the Camera component and change the Clear Flags dropdown from Skybox to Solid Color</span></span>
    3. <span data-ttu-id="b0152-115">Wählen Sie die Hintergrund Farbauswahl aus, und ändern Sie die RGBA-Werte in (0,0).</span><span class="sxs-lookup"><span data-stu-id="b0152-115">Select the Background color picker and change the RGBA values to (0, 0, 0, 0)</span></span>
        1. <span data-ttu-id="b0152-116">Wenn Sie diese Einstellung aus dem Code festlegen, können Sie Unity [`Color.clear`](https://docs.unity3d.com/ScriptReference/Color-clear.html)</span><span class="sxs-lookup"><span data-stu-id="b0152-116">If setting this from code, you can use Unity's [`Color.clear`](https://docs.unity3d.com/ScriptReference/Color-clear.html)</span></span>

[!INCLUDE[](includes/camera/opaque-camera-include.md)]

## <a name="camera-setup"></a><span data-ttu-id="b0152-117">Kamerasetup</span><span class="sxs-lookup"><span data-stu-id="b0152-117">Camera setup</span></span>

<span data-ttu-id="b0152-118">Je nachdem, welche Art von Benutzeroberflächen Sie entwickeln, ist die Hauptkamera immer die primäre Stereo-renderingkomponente, die an die von Ihrem Gerät angefügte Anzeige angeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="b0152-118">Whatever kind of experience you're developing, the Main Camera is always the primary stereo rendering component attached to your device's head-mounted display.</span></span> <span data-ttu-id="b0152-119">Es ist einfacher, Ihre APP zu entwerfen, wenn Sie sich die Anfangsposition des Benutzers als (X: 0, Y: 0, Z: 0) vorstellen.</span><span class="sxs-lookup"><span data-stu-id="b0152-119">It'll be easier to lay out your app if you imagine the starting position of the user as (X: 0, Y: 0, Z: 0).</span></span> <span data-ttu-id="b0152-120">Da die Hauptkamera die Bewegung des Benutzers nachverfolgt, kann die Startposition des Benutzers festgelegt werden, indem die Startposition der Hauptkamera festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="b0152-120">Since the Main Camera is tracking movement of the user's head, the starting position of the user can be set by setting the starting position of the Main Camera.</span></span>

<span data-ttu-id="b0152-121">Die zentrale Entscheidung, die Sie treffen müssen, ist, ob Sie für hololens oder für VR-immersive Headsets entwickeln.</span><span class="sxs-lookup"><span data-stu-id="b0152-121">The central choice you need to make is whether you're developing for HoloLens or VR immersive headsets.</span></span> <span data-ttu-id="b0152-122">Sobald dies der Fall ist, fahren Sie mit dem jeweiligen Einrichtungs Abschnitt fort.</span><span class="sxs-lookup"><span data-stu-id="b0152-122">Once you've got that, skip to whichever setup section applies.</span></span>

### <a name="hololens-camera-setup"></a><span data-ttu-id="b0152-123">Hololens-Kamera-Setup</span><span class="sxs-lookup"><span data-stu-id="b0152-123">HoloLens camera setup</span></span>

<span data-ttu-id="b0152-124">Bei hololens-apps müssen Sie Anker für alle Objekte verwenden, die Sie in der Szene Umgebung sperren möchten.</span><span class="sxs-lookup"><span data-stu-id="b0152-124">For HoloLens apps, you need to use anchors for any objects you want to lock to the scene environment.</span></span> <span data-ttu-id="b0152-125">Es wird empfohlen, unbegrenzten Speicherplatz zur Maximierung der Stabilität und zum Erstellen von Ankern in mehreren Räumen zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="b0152-125">We recommend using unbounded space to maximize stability and create anchors in multiple rooms.</span></span>

[!INCLUDE[](includes/camera/hololens-setup-include.md)]

### <a name="vr-camera-setup"></a><span data-ttu-id="b0152-126">Einrichtung der VR-Kamera</span><span class="sxs-lookup"><span data-stu-id="b0152-126">VR camera setup</span></span>

<span data-ttu-id="b0152-127">Windows Mixed Reality unterstützt Apps über eine Vielzahl von [Skalierungs](../../design/coordinate-systems.md#mixed-reality-experience-scales)Möglichkeiten hinweg, von ausgerichteten und skalierbaren apps bis hin zu hochskalierbaren apps.</span><span class="sxs-lookup"><span data-stu-id="b0152-127">Windows Mixed Reality supports apps across a wide range of [experience scales](../../design/coordinate-systems.md#mixed-reality-experience-scales), from orientation-only and seated-scale apps up through room-scale apps.</span></span> <span data-ttu-id="b0152-128">Auf hololens können Sie weitere apps erstellen und Apps erstellen, mit denen Benutzer mehr als 5 Meter durchlaufen können, indem Sie eine ganze Etage eines Builds und darüber hinaus untersuchen.</span><span class="sxs-lookup"><span data-stu-id="b0152-128">On HoloLens, you can go further and build world-scale apps that let users walk beyond 5 meters, exploring an entire floor of a building and beyond.</span></span>

<span data-ttu-id="b0152-129">Der erste Schritt beim Aufbau einer gemischten Realität in Unity besteht darin, zu bestimmen [, welche Benutzer](../../design/coordinate-systems.md) Oberfläche Ihre APP als Ziel hat:</span><span class="sxs-lookup"><span data-stu-id="b0152-129">Your first step in building a mixed reality experience in Unity is to determine which [experience scale](../../design/coordinate-systems.md) your app will target:</span></span>

* [<span data-ttu-id="b0152-130">Ausrichtung oder sitzender Maßstab</span><span class="sxs-lookup"><span data-stu-id="b0152-130">Orientation or seated-scale</span></span>](../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience)
* [<span data-ttu-id="b0152-131">Die Position oder die Raum Skala</span><span class="sxs-lookup"><span data-stu-id="b0152-131">Standing or room-scale</span></span>](../../design/coordinate-systems.md#building-a-standing-scale-or-room-scale-experience)
* [<span data-ttu-id="b0152-132">Weltweit skalieren</span><span class="sxs-lookup"><span data-stu-id="b0152-132">World-scale</span></span>](../../design/coordinate-systems.md#building-a-world-scale-experience)

#### <a name="room-scale-or-standing-experiences"></a><span data-ttu-id="b0152-133">Raum-oder Steh Erfahrung</span><span class="sxs-lookup"><span data-stu-id="b0152-133">Room-scale or standing experiences</span></span>

> [!NOTE]
> <span data-ttu-id="b0152-134">Wenn Sie für HL2 erstellen, empfiehlt es sich, eine benutzerfreundliche Oberfläche zu erstellen, oder Sie sollten die Verwendung von [Szenen](../platform-capabilities-and-apis/scene-understanding-sdk.md) Informationen in Erwägung gezogen haben.</span><span class="sxs-lookup"><span data-stu-id="b0152-134">If you're building for HL2, we recommend creating an eye-level experience, or consider using [Scene Understanding](../platform-capabilities-and-apis/scene-understanding-sdk.md) to reason about the floor of your scene.</span></span>

[!INCLUDE[](includes/camera/vr-setup-standing-include.md)]

#### <a name="seated-experiences"></a><span data-ttu-id="b0152-135">Sitzender Erfahrungs</span><span class="sxs-lookup"><span data-stu-id="b0152-135">Seated experiences</span></span>

[!INCLUDE[](includes/camera/vr-setup-seated-include.md)]

### <a name="setting-up-the-camera-background"></a><span data-ttu-id="b0152-136">Einrichten des Kamera Hintergrunds</span><span class="sxs-lookup"><span data-stu-id="b0152-136">Setting up the camera background</span></span>

<span data-ttu-id="b0152-137">Wenn Sie mrtk verwenden, wird der Hintergrund der Kamera automatisch konfiguriert und verwaltet.</span><span class="sxs-lookup"><span data-stu-id="b0152-137">If you're using MRTK, the camera's background is automatically configured and managed.</span></span> <span data-ttu-id="b0152-138">Für das XR SDK oder ältere WSA-Projekte empfiehlt es sich, den Hintergrund der Kamera auf hololens auf "Solid Black" festzulegen und die Skybox für VR beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="b0152-138">For XR SDK or Legacy WSA projects, we recommend setting the camera's background to solid black on HoloLens and keeping the skybox for VR.</span></span>

## <a name="using-multiple-cameras"></a><span data-ttu-id="b0152-139">Verwenden mehrerer Kameras</span><span class="sxs-lookup"><span data-stu-id="b0152-139">Using multiple cameras</span></span>

<span data-ttu-id="b0152-140">Wenn in der Szene mehrere Kamerakomponenten vorhanden sind, weiß Unity, welche Kamera für das stereorenrendering verwendet werden soll, je nachdem, welches gameobject über das maincamera-Tag verfügt.</span><span class="sxs-lookup"><span data-stu-id="b0152-140">When there are multiple Camera components in the scene, Unity knows which camera to use for stereoscopic rendering based on which GameObject has the MainCamera tag.</span></span> <span data-ttu-id="b0152-141">In Legacy XR wird dieses Tag auch verwendet, um die Head-Nachverfolgung zu synchronisieren.</span><span class="sxs-lookup"><span data-stu-id="b0152-141">In legacy XR, it also uses this tag to sync head tracking.</span></span> <span data-ttu-id="b0152-142">Im XR SDK wird die Head-Nachverfolgung durch ein an die Kamera angefügtes trackedtargedriver-Skript gesteuert.</span><span class="sxs-lookup"><span data-stu-id="b0152-142">In XR SDK, head tracking is driven by a TrackedPoseDriver script attached to the camera.</span></span>

## <a name="sharing-depth-buffers"></a><span data-ttu-id="b0152-143">Freigeben von tiefen Puffern</span><span class="sxs-lookup"><span data-stu-id="b0152-143">Sharing depth buffers</span></span>

<span data-ttu-id="b0152-144">Durch die Freigabe des tiefen Puffers Ihrer APP für die einzelnen Frames erhält Ihre APP einen von zwei Verb esse ungen in der – Hologramm-Stabilität, basierend auf der Art des von Ihnen Renderns:</span><span class="sxs-lookup"><span data-stu-id="b0152-144">Sharing your app's depth buffer to Windows each frame will give your app one of two boosts in hologram stability, based on the type of headset you're rendering for:</span></span>

* <span data-ttu-id="b0152-145">**VR-immersive Headsets** können bei der Bereitstellung eines tiefen Puffers die neuprojektion von Positionen durchführen, wobei die Hologramme sowohl an der Position als auch an der Ausrichtung für die mitediction angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="b0152-145">**VR immersive headsets** can take care of positional reprojection when a depth buffer is provided, adjusting your holograms for misprediction in both position and orientation.</span></span>
* <span data-ttu-id="b0152-146">**Hololens-Headsets** haben einige verschiedene Methoden.</span><span class="sxs-lookup"><span data-stu-id="b0152-146">**HoloLens headsets** have a few different methods.</span></span> <span data-ttu-id="b0152-147">Hololens 1 wählt automatisch einen [Fokuspunkt](focus-point-in-unity.md) aus, wenn ein tiefen Puffer bereitgestellt wird. Dadurch wird die – Hologramm-Stabilität entlang der Ebene optimiert, die den meisten Inhalt überschneidet.</span><span class="sxs-lookup"><span data-stu-id="b0152-147">HoloLens 1 will automatically select a [focus point](focus-point-in-unity.md) when a depth buffer is provided, optimizing hologram stability along the plane that intersects the most content.</span></span> <span data-ttu-id="b0152-148">Hololens 2 stabilisiert Inhalte mithilfe der [tiefen LSR (siehe Hinweise)](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint).</span><span class="sxs-lookup"><span data-stu-id="b0152-148">HoloLens 2 will stabilize content using [Depth LSR (see Remarks)](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint).</span></span>

[!INCLUDE[](includes/camera/depth-buffer-include.md)]

## <a name="using-clipping-planes"></a><span data-ttu-id="b0152-149">Verwenden von Clipping-Ebenen</span><span class="sxs-lookup"><span data-stu-id="b0152-149">Using clipping planes</span></span>

<span data-ttu-id="b0152-150">Das Rendern von Inhalten zu nahe am Benutzer kann in gemischter Realität unbequem sein.</span><span class="sxs-lookup"><span data-stu-id="b0152-150">Rendering content too close to the user can be uncomfortable in mixed reality.</span></span> <span data-ttu-id="b0152-151">Sie können die [Near-und Far-Clip-Plane](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) in der Kamera Komponente anpassen.</span><span class="sxs-lookup"><span data-stu-id="b0152-151">You can adjust the [near and far clip planes](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) on the Camera component.</span></span>

1. <span data-ttu-id="b0152-152">Wählen Sie die **Hauptkamera** im **Hierarchie** Panel aus.</span><span class="sxs-lookup"><span data-stu-id="b0152-152">Select the **Main Camera** in the **Hierarchy** panel</span></span>
2. <span data-ttu-id="b0152-153">Suchen Sie **im Inspektor** -Panel nach den **Ausschneide Flächen** der **Kamera** Komponente, und ändern Sie das Textfeld **in der Nähe** von **0,3** in **0,85**.</span><span class="sxs-lookup"><span data-stu-id="b0152-153">In the **Inspector** panel, find the **Camera** component **Clipping Planes** and change the **Near** textbox from **0.3** to **0.85**.</span></span> <span data-ttu-id="b0152-154">Inhalte, die noch enger gerendert werden, können zu Benutzer Unannehmlichkeiten führen und sollten gemäß den [Richtlinien für die renderentfernungs](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances)</span><span class="sxs-lookup"><span data-stu-id="b0152-154">Content rendered even closer can lead to user discomfort and should be avoided per the [render distance guidelines](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances).</span></span>

## <a name="recentering-the-camera"></a><span data-ttu-id="b0152-155">Wiedergeben der Kamera</span><span class="sxs-lookup"><span data-stu-id="b0152-155">Recentering the camera</span></span>

<span data-ttu-id="b0152-156">Wenn Sie eine Umgebung mit [sitzender Skalierung](../../design/coordinate-systems.md)entwickeln, können Sie den Welt Ursprung von Unity an der aktuellen Hauptposition des Benutzers wiederholen, indem Sie den **[XR aufrufen. Inputtracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** -Methode in der Legacy-Version XR oder der **[xrinputsubsystem. tryrecenter](https://docs.unity3d.com/ScriptReference/XR.XRInputSubsystem.TryRecenter.html)** -Methode im XR SDK.</span><span class="sxs-lookup"><span data-stu-id="b0152-156">If you're building a [seated-scale experience](../../design/coordinate-systems.md), you can recenter Unity's world origin at the user's current head position by calling the **[XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** method in legacy XR or the **[XRInputSubsystem.TryRecenter](https://docs.unity3d.com/ScriptReference/XR.XRInputSubsystem.TryRecenter.html)** method in XR SDK.</span></span>

## <a name="teleportation"></a><span data-ttu-id="b0152-157">Teleportation</span><span class="sxs-lookup"><span data-stu-id="b0152-157">Teleportation</span></span>

<span data-ttu-id="b0152-158">Diese Funktion ist in der Regel für die VR-Oberfläche reserviert:</span><span class="sxs-lookup"><span data-stu-id="b0152-158">This feature is typically reserved for VR experiences:</span></span>

[!INCLUDE[](includes/camera/teleport-include.md)]

## <a name="reprojection-modes"></a><span data-ttu-id="b0152-159">Neuprojektions Modi</span><span class="sxs-lookup"><span data-stu-id="b0152-159">Reprojection modes</span></span>

<span data-ttu-id="b0152-160">Sowohl hololens als auch immersive Headsets werden jeden Frame, der von der APP gerendert wird, neu projektet, um die tatsächliche Kopfzeile des Benutzers bei der Ausgabe von Phots anzupassen.</span><span class="sxs-lookup"><span data-stu-id="b0152-160">Both HoloLens and immersive headsets will reproject each frame your app renders to adjust for any misprediction of the user's actual head position when photons are emitted.</span></span>

<span data-ttu-id="b0152-161">Standardmäßig:</span><span class="sxs-lookup"><span data-stu-id="b0152-161">By default:</span></span>

* <span data-ttu-id="b0152-162">**VR-immersive Headsets** übernimmt die neuprojektion von positionellen, wenn die APP einen tiefen Puffer für einen bestimmten Frame bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="b0152-162">**VR immersive headsets** will take care of positional reprojection if the app provides a depth buffer for a given frame.</span></span> <span data-ttu-id="b0152-163">Mit immersiven Headsets werden Ihre Hologramme auch an der Position und Ausrichtung angepasst.</span><span class="sxs-lookup"><span data-stu-id="b0152-163">Immersive headsets will also adjust your holograms for misprediction in both position and orientation.</span></span> <span data-ttu-id="b0152-164">Wenn kein tiefen Puffer bereitgestellt wird, korrigiert das System nur die Fehleinstellungen in der Ausrichtung.</span><span class="sxs-lookup"><span data-stu-id="b0152-164">If a depth buffer isn't provided, the system will only correct mispredictions in orientation.</span></span>
* <span data-ttu-id="b0152-165">**Holographic-Headsets** wie hololens 2 kümmern sich um die neuprojektion von positionellen, unabhängig davon, ob die APP ihren tiefen Puffer bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="b0152-165">**Holographic headsets** like HoloLens 2 will take care of positional reprojection whether the app provides its depth buffer or not.</span></span> <span data-ttu-id="b0152-166">Eine positionelle neuprojektion ist ohne tiefen Puffer in hololens möglich, da das Rendering häufig geringer ist, wenn ein stabiler Hintergrund von der realen Welt bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="b0152-166">Positional reprojection is possible without depth buffers on HoloLens as rendering is often sparse with a stable background provided by the real world.</span></span>

[!INCLUDE[](includes/camera/reprojection-include.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="b0152-167">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="b0152-167">Next Development Checkpoint</span></span>

<span data-ttu-id="b0152-168">Wenn Sie der Unity-Entwicklungs Journey folgen, die wir angelegt haben, befinden Sie sich mitten in der Untersuchung der mrtk Core-Bausteine.</span><span class="sxs-lookup"><span data-stu-id="b0152-168">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="b0152-169">Von hier aus können Sie mit dem nächsten Baustein fortfahren:</span><span class="sxs-lookup"><span data-stu-id="b0152-169">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b0152-170">Anvisieren</span><span class="sxs-lookup"><span data-stu-id="b0152-170">Gaze</span></span>](gaze-in-unity.md)

<span data-ttu-id="b0152-171">Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:</span><span class="sxs-lookup"><span data-stu-id="b0152-171">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b0152-172">Gemeinsame Erfahrung</span><span class="sxs-lookup"><span data-stu-id="b0152-172">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="b0152-173">Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="b0152-173">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0152-174">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b0152-174">See also</span></span>

* [<span data-ttu-id="b0152-175">Hologrammstabilität</span><span class="sxs-lookup"><span data-stu-id="b0152-175">Hologram stability</span></span>](../platform-capabilities-and-apis/hologram-stability.md)
* [<span data-ttu-id="b0152-176">Skalierungsmöglichkeiten</span><span class="sxs-lookup"><span data-stu-id="b0152-176">Experience scales</span></span>](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="b0152-177">Räumliche Phase</span><span class="sxs-lookup"><span data-stu-id="b0152-177">Spatial stage</span></span>](../../design/coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="b0152-178">Verfolgbarkeitsverlust in Unity</span><span class="sxs-lookup"><span data-stu-id="b0152-178">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="b0152-179">Raumanker</span><span class="sxs-lookup"><span data-stu-id="b0152-179">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="b0152-180">Persistenz in Unity</span><span class="sxs-lookup"><span data-stu-id="b0152-180">Persistence in Unity</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="b0152-181">Gemeinsame Erlebnisse in Unity</span><span class="sxs-lookup"><span data-stu-id="b0152-181">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)
* [<span data-ttu-id="b0152-182">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="b0152-182">Azure Spatial Anchors</span></span>](/azure/spatial-anchors)
* [<span data-ttu-id="b0152-183">Azure Spatial Anchor SDK für Unity</span><span class="sxs-lookup"><span data-stu-id="b0152-183">Azure Spatial Anchors SDK for Unity</span></span>](/dotnet/api/Microsoft.Azure.SpatialAnchors)