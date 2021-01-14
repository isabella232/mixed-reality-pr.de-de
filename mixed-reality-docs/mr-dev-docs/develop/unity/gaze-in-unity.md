---
title: Anvisieren in Unity
description: Erfahren Sie, wie Sie die Blickwinkel Eingabe als primäre Methode für Benutzer verwenden können, um die Hologramme, die Ihre APP in gemischter Realität erstellt, als Ziel
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Eye-Blick, Head-Eye, Unity, Hologram, Mixed Reality, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, mrtk, Mixed Reality Toolkit
ms.openlocfilehash: 7efc77eff90a164fdc0476a90912a0f52c9bb33d
ms.sourcegitcommit: a1bb77f729ee2e0b3dbd1c2c837bb7614ba7b9bd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98192638"
---
# <a name="head-gaze-in-unity"></a>Kopf schauen in Unity

Der [Blick](../../design/gaze-and-commit.md) ist die primäre Methode für Benutzer, die auf die von ihrer app in [gemischter Realität](../../discover/mixed-reality.md)erstellten [Hologramme](../../discover/hologram.md) abzielen.

## <a name="implementing-head-gaze"></a>Implementieren von Head-Gaze

Konzeptionell bestimmen Sie den [Kopf Blick](../../design/gaze-and-commit.md) , indem Sie einen Strahl vorwärts aus dem Headset des Benutzers projizieren, um zu sehen, was er trifft. In Unity werden die Head-Position und die Richtung des Benutzers über die [Kamera](camera-in-unity.md)verfügbar gemacht, insbesondere [unityengine. Camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) und [unityengine. Camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Position](https://docs.unity3d.com/ScriptReference/Transform-position.html).

Durch den Aufruf von " [Physik. raycast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) " erhalten Sie ein [raycasthit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) , das Informationen über die Kollision enthält, einschließlich des 3D-Kollisions Punkts und des anderen gameobject, das das Head-Gaze-Ray trifft.

### <a name="example-implement-head-gaze"></a>Beispiel: Implementieren des Haupt Blicks

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

### <a name="best-practices"></a>Empfohlene Methoden

Obwohl das obige Beispiel ein einzelnes raycast aus der Update-Schleife auslöst, um das Ziel zu finden, auf dem sich die Kopfzeile des Benutzers befindet, empfiehlt es sich, ein einzelnes-Objekt zum Verwalten aller Head-Blick-Prozesse zu verwenden. Durch die Kombination ihrer Head-Do-Logik wird Ihre APP als wertvolle Verarbeitungsleistung gespart, und Sie können die Raycasting-Einstellung auf eine pro Frame beschränken

## <a name="visualizing-head-gaze"></a>Visualisieren des Haupt Blicks

Wie bei einem Mauszeiger auf einem Computer sollten Sie einen [Cursor](../../design/cursors.md) implementieren, der den Kopf des Benutzers darstellt. Wenn Sie wissen, mit welchem Inhalt ein Benutzer als Ziel dient, erhöhen Sie das Vertrauen in die Interaktion mit dem Benutzer.

## <a name="head-gaze-in-the-mixed-reality-toolkit"></a>Der Haupt Blick im Mixed Reality Toolkit 
Sie können über den [Eingabe-Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in mrtk auf den Haupt Blick zugreifen.

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie der Unity-Entwicklungs Journey folgen, die wir angelegt haben, befinden Sie sich mitten in der Untersuchung der mrtk Core-Bausteine. Von hier aus können Sie mit dem nächsten Baustein fortfahren:

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
