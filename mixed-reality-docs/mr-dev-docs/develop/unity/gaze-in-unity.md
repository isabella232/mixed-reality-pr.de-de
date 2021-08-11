---
title: Anvisieren in Unity
description: Erfahren Sie, wie Sie die Eingabe des Anvierens als primäre Möglichkeit für Benutzer verwenden, die hologramme, die Ihre App in Mixed Reality erstellt, als Ziel zu verwenden.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Anvisiert mit den Augen, Anvisiert mit dem Kopf, Unity, Hologramm, Mixed Reality, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: c6a435e958a92adeed6cd965bebd0b8829e00da735bd193ca72a68acb9e0d6aa
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200112"
---
# <a name="head-gaze-in-unity"></a>Anvischen mit dem Kopf in Unity

[Das Anvieren](../../design/gaze-and-commit.md) ist die primäre Möglichkeit für Benutzer, [Hologramme](../../discover/hologram.md) als Ziel zu verwenden, die Ihre App in [Mixed Reality](../../discover/mixed-reality.md)erstellt.

## <a name="implementing-head-gaze"></a>Implementieren des Anvingens mit dem Kopf

Konzeptionell bestimmen Sie das [Anverfolgen](../../design/gaze-and-commit.md) mit dem Kopf, indem Sie einen Strahl nach vorn vom Headset des Benutzers pro projektieren, um zu sehen, was er trifft. In Unity werden die Kopfposition und -richtung des Benutzers über die [Kamera](camera-in-unity.md)verfügbar gemacht, insbesondere [UnityEngine.Camera.main.](https://docs.unity3d.com/ScriptReference/Camera-main.html) [transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) und [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).

Wenn Sie ["Physics.RayCast"](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) aufrufen, erhalten Sie ein [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) mit Informationen zum Konflikt, einschließlich des 3D-Kollisionspunkts und des anderen GameObject, auf das der Anverfolger mit dem Kopf strahlt.

### <a name="example-implement-head-gaze"></a>Beispiel: Implementieren des Anvingens mit dem Kopf

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

### <a name="best-practices"></a>Bewährte Methoden

Während im obigen Beispiel ein einzelner Raycast aus der Updateschleife ausgelöst wird, um die Kopfpunkte des Benutzers zu finden, wird empfohlen, ein einzelnes Objekt zu verwenden, um alle Prozesse zum Anvieren mit dem Kopf zu verwalten. Wenn Sie Ihre Logik für das Anvieren mit dem Kopf kombinieren, sparen Sie Ihrer App wertvolle Verarbeitungsleistung und beschränken Ihr Raycasting auf einen pro Frame.

## <a name="visualizing-head-gaze"></a>Visualisieren des Anvisierens mit dem Kopf

Genau wie bei einem Mauszeiger auf einem Computer sollten Sie einen [Cursor](../../design/cursors.md) implementieren, der den Anverweisen mit dem Kopf des Benutzers darstellt. Wenn Sie wissen, auf welche Inhalte ein Benutzer abzielt, wird das Vertrauen in die Interaktion mit erhöht.

## <a name="head-gaze-in-the-mixed-reality-toolkit"></a>Anvischen mit dem Kopf im Mixed Reality Toolkit

Sie können über den [Eingabe-Manager](/windows/mixed-reality/mrtk-unity/features/input/overview) im MRTK auf das Anvischen mit dem Kopf zugreifen.

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie die von uns festgelegte Unity-Entwicklungsreise verfolgen, befinden Sie sich in der Mitte der MRTK-Kernbausteine. Von hier aus können Sie mit dem nächsten Baustein fortfahren:

> [!div class="nextstepaction"]
> [Motion-Controller](motion-controllers-in-unity.md)

Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:

> [!div class="nextstepaction"]
> [Gemeinsame Erfahrung](shared-experiences-in-unity.md)

Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.

## <a name="see-also"></a>Siehe auch
* [Kamera](camera-in-unity.md)
* [Cursor](../../design/cursors.md)
* [Anvisieren mit dem Kopf und Ausführen](../../design/gaze-and-commit.md)