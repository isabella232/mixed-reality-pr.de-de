---
title: Fokuspunkt in Unity
description: Erfahren Sie, wie Sie die – Hologramm-Stabilität in Unity manuell optimieren, indem Sie den Fokuspunkt für hololens und Windows Mixed Reality-immersive Headsets festlegen.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, Fokuspunkt, Fokusebene, Stabilisierungs Ebene, Stabilisierungs Punkt, neuprojektion, LSR, tiefen Puffer, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: bd662a079f23ed590708d961e924859675a44917
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009340"
---
# <a name="focus-point-in-unity"></a>Fokuspunkt in Unity

**Namespace:** *unityengine. XR. WSA*<br>
**Typ**: *holographicsettings*

Verwenden Sie den [Schwerpunkt Punkt](../platform-capabilities-and-apis/hologram-stability.md#reprojection) , um hololens einen Hinweis dazu zu geben, wie die derzeit angezeigten holograms am besten stabilisiert werden.

Wenn Sie den Fokuspunkt in Unity festlegen möchten, muss er jedes Frame mithilfe von *holographicsettings. setfocuspointforframe ()* festgelegt werden. Wenn der Fokuspunkt nicht für einen Frame festgelegt ist, wird die Standard Stabilisierungs Ebene verwendet.

> [!NOTE]
> In neuen Unity-Projekten ist die Option "Tiefe Puffer Freigabe aktivieren" standardmäßig festgelegt.  Mit dieser Option sendet eine Unity-APP, die auf einem immersiven Desktop-Headset oder einem hololens ausgeführt wird, auf dem das Windows 10 April 2018 Update (RS4) oder höher ausgeführt wird, ihren tiefen Puffer an Windows, um die hologrammstabilität automatisch zu optimieren, ohne dass Ihre APP einen Schwerpunkt Punkt angibt:
> * Auf einem immersiven Desktop-Headset wird dadurch eine auf pro Pixel basierende Reprojektion ermöglicht.
> * Auf einem hololens, auf dem das Windows 10-Update vom April 2018 oder höher ausgeführt wird, wird der tiefen Puffer analysiert, um automatisch eine optimale Stabilisierungs Ebene auszuwählen.
>
> Beide Ansätze sollten eine noch bessere Bildqualität bieten, ohne dass Ihre APP explizit arbeiten muss, um für jeden Frame einen Schwerpunkt Punkt auszuwählen.  Beachten Sie Folgendes: Wenn Sie einen Schwerpunkt Punkt manuell angeben, wird das oben beschriebene automatische Verhalten überschrieben, und die Stabilität des Hologramms wird normalerweise verringert.  Im Allgemeinen sollten Sie nur dann einen manuellen Fokuspunkt angeben, wenn die APP auf einem hololens ausgeführt wird, der noch nicht auf das Windows 10-Update vom April 2018 aktualisiert wurde.

### <a name="example"></a>Beispiel

Es gibt viele Möglichkeiten, den Schwerpunkt Punkt festzulegen, wie von den über Ladungen für die statische Funktion *setfocuspointforframe* vorgeschlagen. Im folgenden finden Sie ein einfaches Beispiel für die Festlegung der Fokusebene auf das bereitgestellte-Objekt für jeden Frame:

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
> Der einfache Code oben kann die Stabilität des Hologramms verringern, wenn das fokussierte Objekt hinter dem Benutzer endet. Im Allgemeinen wird empfohlen, die **[tiefen Puffer Freigabe zu aktivieren](camera-in-unity.md#sharing-your-depth-buffers-with-windows)** , anstatt manuell einen Fokuspunkt anzugeben.

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie der Unity-Entwicklungs Journey folgen, die wir gerade angelegt haben, sind Sie in der Mitte, die Funktionen und APIs der Mixed Reality-Plattform zu untersuchen. Von hier aus können Sie mit dem nächsten Thema fortfahren:

> [!div class="nextstepaction"]
> [Verlust der Nachverfolgung](tracking-loss-in-unity.md)

Oder wechseln Sie direkt zur Bereitstellung Ihrer App auf einem Gerät oder Emulator:

> [!div class="nextstepaction"]
> [Bereitstellung in hololens oder Windows Mixed Reality-immersiven Headsets](../platform-capabilities-and-apis/using-visual-studio.md)

Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#3-platform-capabilities-and-apis) zurückkehren.

### <a name="see-also"></a>Siehe auch

* [Stabilisierungs Ebene](../platform-capabilities-and-apis/hologram-stability.md#reprojection)
