---
title: Anvisieren in Unity
description: Der Blick ist eine primäre Möglichkeit für Benutzer, die Hologramme, die Ihre APP in gemischter Realität erstellt, als Ziel zu betrachten.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Eye-Blick, Head-Eye, Unity, Hologram, Mixed Reality, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, mrtk, Mixed Reality Toolkit
ms.openlocfilehash: 0c62de9cb1b7ea892831ea2cedbeb23be5ea7b37
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677509"
---
# <a name="head-gaze-in-unity"></a>Kopf schauen in Unity

Der Blick ist eine primäre Möglichkeit für Benutzer, die [Hologramme](../../discover/hologram.md) , die Ihre APP in [gemischter Realität](../../discover/mixed-reality.md)erstellt, als Ziel zu [betrachten](../../design/gaze-and-commit.md) .


## <a name="implementing-head-gaze"></a>Implementieren von Head-Gaze

Konzeptionell wird die [Kopfzeile](../../design/gaze-and-commit.md) implementiert, indem ein Strahl von der Kopfzeile des Benutzers projiziert wird, an der sich das Headset befindet, und in der Vorwärtsrichtung, mit der der Strahl in Konflikt steht.
In Unity werden die Head-Position und die Richtung des Benutzers über die Unity-Haupt [Kamera](camera-in-unity.md), insbesondere [unityengine. Camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html), verfügbar gemacht. [Transform. Forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) und [unityengine. Camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Position](https://docs.unity3d.com/ScriptReference/Transform-position.html).

Das Aufrufen von " [Physik. raycast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) " führt zu einer [raycasthit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) -Struktur, die Informationen über den Konflikt enthält, einschließlich des 3D-Punkts, bei dem der Konflikt aufgetreten ist, und des anderen gameobject, mit dem der Kopf-und

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

### <a name="best-practices"></a>Bewährte Methoden

Im obigen Beispiel wird veranschaulicht, wie ein einzelnes raycast in einer Update-Schleife ausgeführt wird, um das Ziel der Hauptpunkte des Benutzers zu finden. es wird empfohlen, dies in einem einzelnen Objekt zu tun, das die Kopfzeile verwaltet, anstatt dies in einem Objekt zu tun, das potenziell an dem Objekt interessiert ist, das in der Datei untersucht wird. Dadurch kann Ihre APP die Verarbeitung speichern, indem Sie für jeden Frame nur einen Head-Gaze-raycast durchgeführt wird.

## <a name="visualizing-head-gaze"></a>Visualisieren des Haupt Blicks

Ebenso wie auf dem Desktop, auf dem Sie mit einem Mauszeiger auf Inhalte abzielen und mit ihnen interagieren, sollten Sie einen [Cursor](../../design/cursors.md) implementieren, der die Kopfzeile des Benutzers darstellt. Dadurch erhält der Benutzer Vertrauen in das, was Sie im Begriff sind, mit zu interagieren.

## <a name="head-gaze-in-the-mixed-reality-toolkit-v2"></a>Der Haupt Blick im Mixed Reality Toolkit v2
Sie können über den [Eingabe-Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in mrtk v2 auf den Haupt Blick zugreifen.

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie dem Weg der Unity-Entwicklungsprüfpunkte folgen, den wir entworfen haben, befinden Sie sich mitten im Kennenlernen der MRTK-Grundbausteine. Von hier aus können Sie mit dem nächsten Baustein fortfahren:

> [!div class="nextstepaction"]
> [Gesten und Motion-Controller](gestures-and-motion-controllers-in-unity.md)

Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:

> [!div class="nextstepaction"]
> [Gemeinsame Erfahrung](shared-experiences-in-unity.md)

Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.

## <a name="see-also"></a>Siehe auch
* [Kamera](camera-in-unity.md)
* [Cursor](../../design/cursors.md)
* [Anvisieren mit dem Kopf und Ausführen](../../design/gaze-and-commit.md)
