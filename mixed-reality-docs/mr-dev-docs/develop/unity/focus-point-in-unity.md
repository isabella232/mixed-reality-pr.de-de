---
title: Fokuspunkt in Unity
description: Erfahren Sie, wie Sie die – Hologramm-Stabilität in Unity manuell optimieren, indem Sie den Fokuspunkt für hololens und Windows Mixed Reality-immersive Headsets festlegen.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, Fokuspunkt, Fokusebene, Stabilisierungs Ebene, Stabilisierungs Punkt, neuprojektion, LSR, tiefen Puffer, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 16f359e1742b86c5f12c0c5965ac9e818ea76aee
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636222"
---
# <a name="focus-point-in-unity"></a><span data-ttu-id="27b83-104">Fokuspunkt in Unity</span><span class="sxs-lookup"><span data-stu-id="27b83-104">Focus point in Unity</span></span>

<span data-ttu-id="27b83-105">**Namespace:** *unityengine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="27b83-105">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="27b83-106">**Typ**: *holographicsettings*</span><span class="sxs-lookup"><span data-stu-id="27b83-106">**Type**: *HolographicSettings*</span></span>

<span data-ttu-id="27b83-107">Verwenden Sie den [Schwerpunkt Punkt](../platform-capabilities-and-apis/hologram-stability.md#reprojection) , um hololens einen Hinweis dazu zu geben, wie die derzeit angezeigten holograms am besten stabilisiert werden.</span><span class="sxs-lookup"><span data-stu-id="27b83-107">Use the [focus point](../platform-capabilities-and-apis/hologram-stability.md#reprojection) to provide HoloLens with a hint about how to best stabilize the holograms currently being displayed.</span></span>

<span data-ttu-id="27b83-108">Wenn Sie den Fokuspunkt in Unity festlegen möchten, muss er jedes Frame mithilfe von *holographicsettings. setfocuspointforframe ()* festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="27b83-108">If you want to set the Focus Point in Unity, it needs to be set every frame using *HolographicSettings.SetFocusPointForFrame()*.</span></span> <span data-ttu-id="27b83-109">Wenn der Fokuspunkt nicht für einen Frame festgelegt ist, wird die Standard Stabilisierungs Ebene verwendet.</span><span class="sxs-lookup"><span data-stu-id="27b83-109">When the Focus Point isn't set for a frame, the default stabilization plane is used.</span></span>

> [!NOTE]
> <span data-ttu-id="27b83-110">In neuen Unity-Projekten ist die Option "Tiefe Puffer Freigabe aktivieren" standardmäßig festgelegt.</span><span class="sxs-lookup"><span data-stu-id="27b83-110">By default, new Unity projects have the "Enable Depth Buffer Sharing" option set.</span></span>  <span data-ttu-id="27b83-111">Mit dieser Option sendet eine Unity-APP, die auf einem immersiven Desktop-Headset oder einem hololens ausgeführt wird, auf dem das Windows 10 April 2018 Update (RS4) oder höher ausgeführt wird, ihren tiefen Puffer an Windows, um die hologrammstabilität automatisch zu optimieren, ohne dass Ihre APP einen Schwerpunkt Punkt angibt:</span><span class="sxs-lookup"><span data-stu-id="27b83-111">With this option, a Unity app running on either an immersive desktop headset or a HoloLens running the Windows 10 April 2018 Update (RS4) or later will submit your depth buffer to Windows to optimize hologram stability automatically, without your app specifying a focus point:</span></span>
> * <span data-ttu-id="27b83-112">Auf einem immersiven Desktop-Headset wird dadurch eine auf pro Pixel basierende Reprojektion ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="27b83-112">On an immersive desktop headset, this will enable per-pixel depth-based reprojection.</span></span>
> * <span data-ttu-id="27b83-113">Auf einem hololens, auf dem das Windows 10-Update vom April 2018 oder höher ausgeführt wird, wird der tiefen Puffer analysiert, um automatisch eine optimale Stabilisierungs Ebene auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="27b83-113">On a HoloLens running the Windows 10 April 2018 Update or later, this will analyze the depth buffer to pick an optimal stabilization plane automatically.</span></span>
>
> <span data-ttu-id="27b83-114">Beide Ansätze sollten eine noch bessere Bildqualität bieten, ohne dass Ihre APP explizit arbeiten muss, um für jeden Frame einen Schwerpunkt Punkt auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="27b83-114">Either approach should provide even better image quality without explicit work by your app to select a focus point for each frame.</span></span>  <span data-ttu-id="27b83-115">Beachten Sie Folgendes: Wenn Sie einen Schwerpunkt Punkt manuell angeben, wird das oben beschriebene automatische Verhalten überschrieben, und die Stabilität des Hologramms wird normalerweise verringert.</span><span class="sxs-lookup"><span data-stu-id="27b83-115">Note that if you do provide a focus point manually, that will override the automatic behavior described above, and will usually reduce hologram stability.</span></span>  <span data-ttu-id="27b83-116">Im Allgemeinen sollten Sie nur dann einen manuellen Fokuspunkt angeben, wenn die APP auf einem hololens ausgeführt wird, der noch nicht auf das Windows 10-Update vom April 2018 aktualisiert wurde.</span><span class="sxs-lookup"><span data-stu-id="27b83-116">Generally, you should only specify a manual focus point when your app is running on a HoloLens that has not yet been updated to the Windows 10 April 2018 Update.</span></span>

### <a name="example"></a><span data-ttu-id="27b83-117">Beispiel</span><span class="sxs-lookup"><span data-stu-id="27b83-117">Example</span></span>

<span data-ttu-id="27b83-118">Es gibt viele Möglichkeiten, den Schwerpunkt Punkt festzulegen, wie von den über Ladungen für die statische Funktion *setfocuspointforframe* vorgeschlagen.</span><span class="sxs-lookup"><span data-stu-id="27b83-118">There are many ways to set the Focus Point, as suggested by the overloads available on the *SetFocusPointForFrame* static function.</span></span> <span data-ttu-id="27b83-119">Im folgenden finden Sie ein einfaches Beispiel für die Festlegung der Fokusebene auf das bereitgestellte-Objekt für jeden Frame:</span><span class="sxs-lookup"><span data-stu-id="27b83-119">Presented below is a simple example to set the focus plane to the provided object for each frame:</span></span>

```cs
public GameObject focusedObject;
void Update()
{
    // Normally the normal is best set to be the opposite of the main camera's
    // forward vector.
    // If the content is actually all on a plane (like text), set the normal to
    // the normal of the plane and ensure the user does not pass through the
    // plane.
    var normal = -Camera.main.transform.forward;     
    var position = focusedObject.transform.position;
    UnityEngine.XR.WSA.HolographicSettings.SetFocusPointForFrame(position, normal);
}
```

> [!NOTE]
> <span data-ttu-id="27b83-120">Der einfache Code oben kann die Stabilität des Hologramms verringern, wenn das fokussierte Objekt hinter dem Benutzer endet.</span><span class="sxs-lookup"><span data-stu-id="27b83-120">The simple code above may reduce hologram stability if the focused object ends up behind the user.</span></span> <span data-ttu-id="27b83-121">Im Allgemeinen wird empfohlen, die **[tiefen Puffer Freigabe zu aktivieren](camera-in-unity.md#sharing-depth-buffers)** , anstatt manuell einen Fokuspunkt anzugeben.</span><span class="sxs-lookup"><span data-stu-id="27b83-121">We generally recommend setting **[Enable Depth Buffer Sharing](camera-in-unity.md#sharing-depth-buffers)** instead of manually specifying a focus point.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="27b83-122">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="27b83-122">Next Development Checkpoint</span></span>

<span data-ttu-id="27b83-123">Wenn Sie der Unity-Entwicklungs Journey folgen, die wir gerade angelegt haben, sind Sie in der Mitte, die Funktionen und APIs der Mixed Reality-Plattform zu untersuchen.</span><span class="sxs-lookup"><span data-stu-id="27b83-123">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="27b83-124">Von hier aus können Sie mit dem nächsten Thema fortfahren:</span><span class="sxs-lookup"><span data-stu-id="27b83-124">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="27b83-125">Verlust der Nachverfolgung</span><span class="sxs-lookup"><span data-stu-id="27b83-125">Tracking loss</span></span>](tracking-loss-in-unity.md)

<span data-ttu-id="27b83-126">Oder wechseln Sie direkt zur Bereitstellung Ihrer App auf einem Gerät oder Emulator:</span><span class="sxs-lookup"><span data-stu-id="27b83-126">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="27b83-127">Bereitstellung in hololens oder Windows Mixed Reality-immersiven Headsets</span><span class="sxs-lookup"><span data-stu-id="27b83-127">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="27b83-128">Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#3-advanced-features) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="27b83-128">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-advanced-features) at any time.</span></span>

### <a name="see-also"></a><span data-ttu-id="27b83-129">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="27b83-129">See also</span></span>

* [<span data-ttu-id="27b83-130">Stabilisierungs Ebene</span><span class="sxs-lookup"><span data-stu-id="27b83-130">Stabilization plane</span></span>](../platform-capabilities-and-apis/hologram-stability.md#reprojection)
