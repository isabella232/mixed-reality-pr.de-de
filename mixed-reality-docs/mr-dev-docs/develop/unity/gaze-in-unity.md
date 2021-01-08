---
title: Anvisieren in Unity
description: Erfahren Sie, wie Sie die Blickwinkel Eingabe als primäre Methode für Benutzer verwenden können, um die Hologramme, die Ihre APP in gemischter Realität erstellt, als Ziel
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Eye-Blick, Head-Eye, Unity, Hologram, Mixed Reality, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, mrtk, Mixed Reality Toolkit
ms.openlocfilehash: 5dab8cb38aaa4b9a4547f4bf494afb093b6d8058
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009890"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="a5235-104">Kopf schauen in Unity</span><span class="sxs-lookup"><span data-stu-id="a5235-104">Head-gaze in Unity</span></span>

<span data-ttu-id="a5235-105">Der [Blick](../../design/gaze-and-commit.md) ist die primäre Methode für Benutzer, die auf die von ihrer app in [gemischter Realität](../../discover/mixed-reality.md)erstellten [Hologramme](../../discover/hologram.md) abzielen.</span><span class="sxs-lookup"><span data-stu-id="a5235-105">[Gaze](../../design/gaze-and-commit.md) is the primary way for users to target [holograms](../../discover/hologram.md) your app creates in [Mixed Reality](../../discover/mixed-reality.md).</span></span>

## <a name="implementing-head-gaze"></a><span data-ttu-id="a5235-106">Implementieren von Head-Gaze</span><span class="sxs-lookup"><span data-stu-id="a5235-106">Implementing head-gaze</span></span>

<span data-ttu-id="a5235-107">Konzeptionell bestimmen Sie den [Kopf Blick](../../design/gaze-and-commit.md) , indem Sie einen Strahl vorwärts aus dem Headset des Benutzers projizieren, um zu sehen, was er trifft.</span><span class="sxs-lookup"><span data-stu-id="a5235-107">Conceptually, you determine [head-gaze](../../design/gaze-and-commit.md) by projecting a ray forward from the user's headset to see what it hits.</span></span> <span data-ttu-id="a5235-108">In Unity werden die Head-Position und die Richtung des Benutzers über die [Kamera](camera-in-unity.md)verfügbar gemacht, insbesondere [unityengine. Camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) und [unityengine. Camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="a5235-108">In Unity, the user's head position and direction are exposed through the [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="a5235-109">Durch den Aufruf von " [Physik. raycast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) " erhalten Sie ein [raycasthit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) , das Informationen über die Kollision enthält, einschließlich des 3D-Kollisions Punkts und des anderen gameobject, das das Head-Gaze-Ray trifft.</span><span class="sxs-lookup"><span data-stu-id="a5235-109">Calling [Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) gives you a [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) containing information about the collision, including the 3D collision point and the other GameObject the head-gaze ray hit.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="a5235-110">Beispiel: Implementieren des Haupt Blicks</span><span class="sxs-lookup"><span data-stu-id="a5235-110">Example: Implement head-gaze</span></span>

```cs
void Update()
{
       RaycastHit hitInfo;
       if (Physics.Raycast(
               Camera.main.transform.position,
               Camera.main.transform.forward,
               out hitInfo,
               20.0f,
               Physics.DefaultRaycastLayers))
       {
           // If the Raycast has succeeded and hit a hologram
           // hitInfo's point represents the position being gazed at
           // hitInfo's collider GameObject represents the hologram being gazed at
       }
}
```

### <a name="best-practices"></a><span data-ttu-id="a5235-111">Empfohlene Methoden</span><span class="sxs-lookup"><span data-stu-id="a5235-111">Best practices</span></span>

<span data-ttu-id="a5235-112">Obwohl das obige Beispiel ein einzelnes raycast aus der Update-Schleife auslöst, um das Ziel zu finden, auf dem sich die Kopfzeile des Benutzers befindet, empfiehlt es sich, ein einzelnes-Objekt zum Verwalten aller Head-Blick-Prozesse zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="a5235-112">While the example above fires a single raycast from the update loop to find the target the user's head points at, we recommended using a single object to manage all head-gaze processes.</span></span> <span data-ttu-id="a5235-113">Durch die Kombination ihrer Head-Do-Logik wird Ihre APP als wertvolle Verarbeitungsleistung gespart, und Sie können die Raycasting-Einstellung auf eine pro Frame beschränken</span><span class="sxs-lookup"><span data-stu-id="a5235-113">Combining your head-gaze logic will save your app precious processing power and limit your raycasting to one per frame.</span></span>

## <a name="visualizing-head-gaze"></a><span data-ttu-id="a5235-114">Visualisieren des Haupt Blicks</span><span class="sxs-lookup"><span data-stu-id="a5235-114">Visualizing head-gaze</span></span>

<span data-ttu-id="a5235-115">Wie bei einem Mauszeiger auf einem Computer sollten Sie einen [Cursor](../../design/cursors.md) implementieren, der den Kopf des Benutzers darstellt.</span><span class="sxs-lookup"><span data-stu-id="a5235-115">Just like with a mouse pointer on a computer, you should implement a [cursor](../../design/cursors.md) that represents the user's head-gaze.</span></span> <span data-ttu-id="a5235-116">Wenn Sie wissen, mit welchem Inhalt ein Benutzer als Ziel dient, erhöhen Sie das Vertrauen in die Interaktion mit dem Benutzer.</span><span class="sxs-lookup"><span data-stu-id="a5235-116">Knowing what content a user is targeting increases confidence in what they're about to interact with.</span></span>

## <a name="head-gaze-in-the-mixed-reality-toolkit"></a><span data-ttu-id="a5235-117">Der Haupt Blick im Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="a5235-117">Head-gaze in the Mixed Reality Toolkit</span></span> 
<span data-ttu-id="a5235-118">Sie können über den [Eingabe-Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in mrtk auf den Haupt Blick zugreifen.</span><span class="sxs-lookup"><span data-stu-id="a5235-118">You can access head-gaze from the [Input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="a5235-119">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="a5235-119">Next Development Checkpoint</span></span>

<span data-ttu-id="a5235-120">Wenn Sie der Unity-Entwicklungs Journey folgen, die wir angelegt haben, befinden Sie sich mitten in der Untersuchung der mrtk Core-Bausteine.</span><span class="sxs-lookup"><span data-stu-id="a5235-120">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="a5235-121">Von hier aus können Sie mit dem nächsten Baustein fortfahren:</span><span class="sxs-lookup"><span data-stu-id="a5235-121">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a5235-122">Gesten und Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="a5235-122">Gestures and motion controllers</span></span>](gestures-and-motion-controllers-in-unity.md)

<span data-ttu-id="a5235-123">Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:</span><span class="sxs-lookup"><span data-stu-id="a5235-123">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a5235-124">Gemeinsame Erfahrung</span><span class="sxs-lookup"><span data-stu-id="a5235-124">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="a5235-125">Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="a5235-125">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="a5235-126">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="a5235-126">See also</span></span>
* [<span data-ttu-id="a5235-127">Kamera</span><span class="sxs-lookup"><span data-stu-id="a5235-127">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="a5235-128">Cursor</span><span class="sxs-lookup"><span data-stu-id="a5235-128">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="a5235-129">Anvisieren mit dem Kopf und Ausführen</span><span class="sxs-lookup"><span data-stu-id="a5235-129">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
