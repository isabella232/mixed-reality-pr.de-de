---
title: Anvisieren in Unity
description: Der Blick ist eine primäre Möglichkeit für Benutzer, die Hologramme, die Ihre APP in gemischter Realität erstellt, als Ziel zu betrachten.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Eye-Do, Head-Blick, Unity, Hologram, gemischte Realität
ms.openlocfilehash: 8c1a6cb0847cd0e6e776c6d4e1f7c1efdc126279
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684707"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="f09bb-104">Kopf schauen in Unity</span><span class="sxs-lookup"><span data-stu-id="f09bb-104">Head-gaze in Unity</span></span>

<span data-ttu-id="f09bb-105">Der Blick ist eine primäre Möglichkeit für Benutzer, die [Hologramme](../../discover/hologram.md) , die Ihre APP in [gemischter Realität](../../discover/mixed-reality.md)erstellt, als Ziel zu [betrachten](../../design/gaze-and-commit.md) .</span><span class="sxs-lookup"><span data-stu-id="f09bb-105">[Gaze](../../design/gaze-and-commit.md) is a primary way for users to target the [holograms](../../discover/hologram.md) your app creates in [Mixed Reality](../../discover/mixed-reality.md).</span></span>


## <a name="implementing-head-gaze"></a><span data-ttu-id="f09bb-106">Implementieren von Head-Gaze</span><span class="sxs-lookup"><span data-stu-id="f09bb-106">Implementing head-gaze</span></span>

<span data-ttu-id="f09bb-107">Konzeptionell wird die [Kopfzeile](../../design/gaze-and-commit.md) implementiert, indem ein Strahl von der Kopfzeile des Benutzers projiziert wird, an der sich das Headset befindet, und in der Vorwärtsrichtung, mit der der Strahl in Konflikt steht.</span><span class="sxs-lookup"><span data-stu-id="f09bb-107">Conceptually, [head-gaze](../../design/gaze-and-commit.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span>
<span data-ttu-id="f09bb-108">In Unity werden die Head-Position und die Richtung des Benutzers über die Unity-Haupt [Kamera](camera-in-unity.md), insbesondere [unityengine. Camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html), verfügbar gemacht. [Transform. Forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) und [unityengine. Camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="f09bb-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="f09bb-109">Das Aufrufen von " [Physik. raycast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) " führt zu einer [raycasthit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) -Struktur, die Informationen über den Konflikt enthält, einschließlich des 3D-Punkts, bei dem der Konflikt aufgetreten ist, und des anderen gameobject, mit dem der Kopf-und</span><span class="sxs-lookup"><span data-stu-id="f09bb-109">Calling [Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the head-gaze ray collided with.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="f09bb-110">Beispiel: Implementieren des Haupt Blicks</span><span class="sxs-lookup"><span data-stu-id="f09bb-110">Example: Implement head-gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="f09bb-111">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="f09bb-111">Best practices</span></span>

<span data-ttu-id="f09bb-112">Im obigen Beispiel wird veranschaulicht, wie ein einzelnes raycast in einer Update-Schleife ausgeführt wird, um das Ziel der Hauptpunkte des Benutzers zu finden. es wird empfohlen, dies in einem einzelnen Objekt zu tun, das die Kopfzeile verwaltet, anstatt dies in einem Objekt zu tun, das potenziell an dem Objekt interessiert ist, das in der Datei untersucht wird.</span><span class="sxs-lookup"><span data-stu-id="f09bb-112">While the example above demonstrates how to do a single raycast in an update loop to find the target the user's head points at, it is recommended to do this in a single object managing head-gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="f09bb-113">Dadurch kann Ihre APP die Verarbeitung speichern, indem Sie für jeden Frame nur einen Head-Gaze-raycast durchgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="f09bb-113">This lets your app save processing by doing just one head-gaze raycast each frame.</span></span>

## <a name="visualizing-head-gaze"></a><span data-ttu-id="f09bb-114">Visualisieren des Haupt Blicks</span><span class="sxs-lookup"><span data-stu-id="f09bb-114">Visualizing head-gaze</span></span>

<span data-ttu-id="f09bb-115">Ebenso wie auf dem Desktop, auf dem Sie mit einem Mauszeiger auf Inhalte abzielen und mit ihnen interagieren, sollten Sie einen [Cursor](../../design/cursors.md) implementieren, der die Kopfzeile des Benutzers darstellt.</span><span class="sxs-lookup"><span data-stu-id="f09bb-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](../../design/cursors.md) that represents the user's head-gaze.</span></span> <span data-ttu-id="f09bb-116">Dadurch erhält der Benutzer Vertrauen in das, was Sie im Begriff sind, mit zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="f09bb-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="head-gaze-in-the-mixed-reality-toolkit-v2"></a><span data-ttu-id="f09bb-117">Der Haupt Blick im Mixed Reality Toolkit v2</span><span class="sxs-lookup"><span data-stu-id="f09bb-117">Head-gaze in the Mixed Reality Toolkit v2</span></span>
<span data-ttu-id="f09bb-118">Sie können über den [Eingabe-Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in mrtk v2 auf den Haupt Blick zugreifen.</span><span class="sxs-lookup"><span data-stu-id="f09bb-118">You can access head-gaze from the [Input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK v2.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="f09bb-119">Nächster Entwicklungs Prüfpunkt</span><span class="sxs-lookup"><span data-stu-id="f09bb-119">Next Development Checkpoint</span></span>

<span data-ttu-id="f09bb-120">Wenn Sie der Unity-Entwicklungs Prüf Punkt Journey folgen, die wir gerade angelegt haben, sind Sie in der Mitte, dass Sie die Hauptbausteine von mrtk untersuchen.</span><span class="sxs-lookup"><span data-stu-id="f09bb-120">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="f09bb-121">Von hier aus können Sie mit dem nächsten Baustein fortfahren:</span><span class="sxs-lookup"><span data-stu-id="f09bb-121">From here, you can proceed to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f09bb-122">Gesten und Motion-Controller</span><span class="sxs-lookup"><span data-stu-id="f09bb-122">Gestures and motion controllers</span></span>](gestures-and-motion-controllers-in-unity.md)

<span data-ttu-id="f09bb-123">Oder springen Sie zu den Funktionen und APIs der Mixed Reality-Plattform:</span><span class="sxs-lookup"><span data-stu-id="f09bb-123">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f09bb-124">Gemeinsame Erfahrung</span><span class="sxs-lookup"><span data-stu-id="f09bb-124">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="f09bb-125">Sie können jederzeit jederzeit zu den [Unity-Entwicklungs Prüfpunkten](unity-development-overview.md#2-core-building-blocks) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="f09bb-125">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="f09bb-126">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f09bb-126">See also</span></span>
* [<span data-ttu-id="f09bb-127">Kamera</span><span class="sxs-lookup"><span data-stu-id="f09bb-127">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="f09bb-128">Cursor</span><span class="sxs-lookup"><span data-stu-id="f09bb-128">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="f09bb-129">Anvisieren mit dem Kopf und Ausführen</span><span class="sxs-lookup"><span data-stu-id="f09bb-129">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
