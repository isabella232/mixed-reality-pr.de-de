---
title: Anvisieren in Unity
description: Erfahren Sie, wie Sie die Eingabe zum Anvieren als primäre Möglichkeit für Benutzer verwenden, die Hologramme zu verwenden, die Ihre App in Mixed Reality erstellt.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Anvisiert mit den Augen, Anvieren mit dem Kopf, Unity, Hologramm, Mixed Reality, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: f10079d36f737e5d8a2ee74a88ca0f8b2b3d791c
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600149"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="715b3-104">Anvischen mit dem Kopf in Unity</span><span class="sxs-lookup"><span data-stu-id="715b3-104">Head-gaze in Unity</span></span>

<span data-ttu-id="715b3-105">[Das Anvieren](../../design/gaze-and-commit.md) ist die primäre Möglichkeit für Benutzer, [Hologramme](../../discover/hologram.md) als Ziel zu verwenden, die Ihre App in [Mixed Reality](../../discover/mixed-reality.md)erstellt.</span><span class="sxs-lookup"><span data-stu-id="715b3-105">[Gaze](../../design/gaze-and-commit.md) is the primary way for users to target [holograms](../../discover/hologram.md) your app creates in [Mixed Reality](../../discover/mixed-reality.md).</span></span>

## <a name="implementing-head-gaze"></a><span data-ttu-id="715b3-106">Implementieren des Anvingens mit dem Kopf</span><span class="sxs-lookup"><span data-stu-id="715b3-106">Implementing head-gaze</span></span>

<span data-ttu-id="715b3-107">Konzeptionell bestimmen Sie das [Anverfolgen](../../design/gaze-and-commit.md) mit dem Kopf, indem Sie einen Strahl nach vorn vom Headset des Benutzers pro projektieren, um zu sehen, was er trifft.</span><span class="sxs-lookup"><span data-stu-id="715b3-107">Conceptually, you determine [head-gaze](../../design/gaze-and-commit.md) by projecting a ray forward from the user's headset to see what it hits.</span></span> <span data-ttu-id="715b3-108">In Unity werden die Kopfposition und -richtung des Benutzers über die [Kamera](camera-in-unity.md)verfügbar gemacht, insbesondere [UnityEngine.Camera.main.](https://docs.unity3d.com/ScriptReference/Camera-main.html) [transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) und [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="715b3-108">In Unity, the user's head position and direction are exposed through the [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="715b3-109">Wenn Sie ["Physics.RayCast"](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) aufrufen, erhalten Sie ein [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) mit Informationen zum Konflikt, einschließlich des 3D-Kollisionspunkts und des anderen GameObject, auf das der Anverfolger mit dem Kopf strahlt.</span><span class="sxs-lookup"><span data-stu-id="715b3-109">Calling [Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) gives you a [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) containing information about the collision, including the 3D collision point and the other GameObject the head-gaze ray hit.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="715b3-110">Beispiel: Implementieren des Anvingens mit dem Kopf</span><span class="sxs-lookup"><span data-stu-id="715b3-110">Example: Implement head-gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="715b3-111">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="715b3-111">Best practices</span></span>

<span data-ttu-id="715b3-112">Während im obigen Beispiel ein einzelner Raycast aus der Updateschleife ausgelöst wird, um die Kopfpunkte des Benutzers zu finden, wird empfohlen, ein einzelnes Objekt zu verwenden, um alle Prozesse zum Anvieren mit dem Kopf zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="715b3-112">While the example above fires a single raycast from the update loop to find the target the user's head points at, we recommended using a single object to manage all head-gaze processes.</span></span> <span data-ttu-id="715b3-113">Wenn Sie Ihre Logik für das Anvieren mit dem Kopf kombinieren, sparen Sie Ihrer App wertvolle Verarbeitungsleistung und beschränken Ihr Raycasting auf einen pro Frame.</span><span class="sxs-lookup"><span data-stu-id="715b3-113">Combining your head-gaze logic will save your app precious processing power and limit your raycasting to one per frame.</span></span>

## <a name="visualizing-head-gaze"></a><span data-ttu-id="715b3-114">Visualisieren des Anvisierens mit dem Kopf</span><span class="sxs-lookup"><span data-stu-id="715b3-114">Visualizing head-gaze</span></span>

<span data-ttu-id="715b3-115">Genau wie bei einem Mauszeiger auf einem Computer sollten Sie einen [Cursor](../../design/cursors.md) implementieren, der den Anverweisen mit dem Kopf des Benutzers darstellt.</span><span class="sxs-lookup"><span data-stu-id="715b3-115">Just like with a mouse pointer on a computer, you should implement a [cursor](../../design/cursors.md) that represents the user's head-gaze.</span></span> <span data-ttu-id="715b3-116">Wenn Sie wissen, auf welche Inhalte ein Benutzer abzielt, wird das Vertrauen in die Interaktion mit erhöht.</span><span class="sxs-lookup"><span data-stu-id="715b3-116">Knowing what content a user is targeting increases confidence in what they're about to interact with.</span></span>

## <a name="head-gaze-in-the-mixed-reality-toolkit"></a><span data-ttu-id="715b3-117">Anvischen mit dem Kopf im Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="715b3-117">Head-gaze in the Mixed Reality Toolkit</span></span>

<span data-ttu-id="715b3-118">Sie können über den [Eingabe-Manager](/windows/mixed-reality/mrtk-unity/features/input/overview) im MRTK auf das Anvischen mit dem Kopf zugreifen.</span><span class="sxs-lookup"><span data-stu-id="715b3-118">You can access head-gaze from the [Input Manager](/windows/mixed-reality/mrtk-unity/features/input/overview) in MRTK.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="715b3-119">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="715b3-119">Next Development Checkpoint</span></span>

<span data-ttu-id="715b3-120">Wenn Sie die von uns festgelegte Unity-Entwicklungsreise verfolgen, befinden Sie sich in der Mitte der MRTK-Kernbausteine.</span><span class="sxs-lookup"><span data-stu-id="715b3-120">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="715b3-121">Von hier aus können Sie mit dem nächsten Baustein fortfahren:</span><span class="sxs-lookup"><span data-stu-id="715b3-121">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="715b3-122">Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="715b3-122">Motion controllers</span></span>](motion-controllers-in-unity.md)

<span data-ttu-id="715b3-123">Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:</span><span class="sxs-lookup"><span data-stu-id="715b3-123">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="715b3-124">Gemeinsame Erfahrung</span><span class="sxs-lookup"><span data-stu-id="715b3-124">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="715b3-125">Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="715b3-125">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="715b3-126">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="715b3-126">See also</span></span>
* [<span data-ttu-id="715b3-127">Kamera</span><span class="sxs-lookup"><span data-stu-id="715b3-127">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="715b3-128">Cursor</span><span class="sxs-lookup"><span data-stu-id="715b3-128">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="715b3-129">Anvisieren mit dem Kopf und Ausführen</span><span class="sxs-lookup"><span data-stu-id="715b3-129">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)