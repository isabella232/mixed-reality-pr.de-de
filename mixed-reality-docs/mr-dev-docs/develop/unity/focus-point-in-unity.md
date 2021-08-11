---
title: Fokuspunkt in Unity
description: Erfahren Sie, wie Sie die Hologrammstabilität in Unity manuell optimieren, indem Sie den Fokuspunkt für HoloLens festlegen und immersive Headsets Windows Mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, Fokuspunkt, Fokusebene, Stabilisierungsebene, Stabilisierungspunkt, Neuprojektion, LSR, Tiefenpuffer, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 91fba310cf86f145174512c4c1e23d69907d2f57f48f3fe1992b417eb283235f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203592"
---
# <a name="focus-point-in-unity"></a>Fokuspunkt in Unity

**Namespace:** *UnityEngine.XR.WSA*<br>
**Typ:** *HolographicSettings*

Verwenden Sie den [Fokuspunkt,](../platform-capabilities-and-apis/hologram-stability.md#reprojection) um HoloLens einen Hinweis zur optimalen Stabilisierung der aktuell angezeigten Hologramme bereitzustellen.

Wenn Sie den Fokuspunkt in Unity festlegen möchten, muss er mit *HolographicSettings.SetFocusPointForFrame()* für jeden Frame festgelegt werden. Wenn der Fokuspunkt nicht für einen Frame festgelegt ist, wird die Standard-Stabilisierungsebene verwendet.

> [!NOTE]
> Standardmäßig ist für neue Unity-Projekte die Option "Tiefenpufferfreigabe aktivieren" festgelegt.  Mit dieser Option sendet eine Unity-App, die entweder auf einem immersiven Desktop-Headset oder einem HoloLens ausgeführt wird, auf dem das Update vom Windows 10 April 2018 (RS4) oder höher ausgeführt wird, Ihren Tiefenpuffer an Windows, um die Hologrammstabilität automatisch zu optimieren, ohne dass Ihre App einen Fokuspunkt angibt:
> * Auf einem immersiven Desktop-Headset ermöglicht dies eine pixelbasierte tiefenbasierte Neuprojektion.
> * Auf einer HoloLens, die das Update vom April 2018 oder höher Windows 10 ausführt, wird der Tiefenpuffer analysiert, um automatisch eine optimale Stabilisierungsebene zu wählen.
>
> Beide Ansätze sollten eine noch bessere Imagequalität bieten, ohne dass Ihre App explizit einen Fokuspunkt für jeden Frame auswählen muss.  Beachten Sie Folgendes: Wenn Sie manuell einen Fokuspunkt angeben, überschreibt dies das oben beschriebene automatische Verhalten und reduziert in der Regel die Hologrammstabilität.  Im Allgemeinen sollten Sie nur dann einen manuellen Fokuspunkt angeben, wenn Ihre App auf einem HoloLens ausgeführt wird, der noch nicht auf das Update vom Windows 10 April 2018 aktualisiert wurde.

### <a name="example"></a>Beispiel

Es gibt viele Möglichkeiten, den Fokuspunkt festzulegen, wie von den Überladungen vorgeschlagen, die in der statischen *SetFocusPointForFrame-Funktion* verfügbar sind. Im Folgenden finden Sie ein einfaches Beispiel zum Festlegen der Fokusebene auf das angegebene Objekt für jeden Frame:

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
> Der obige einfache Code kann die Hologrammstabilität verringern, wenn das fokussierte Objekt hinter dem Benutzer endet. Im Allgemeinen wird empfohlen, **[die Option Tiefenpufferfreigabe aktivieren](camera-in-unity.md#sharing-depth-buffers)** festzulegen, anstatt manuell einen Fokuspunkt anzugeben.

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie die von uns festgelegte Unity-Entwicklungsreise verfolgen, erkunden Sie die Mixed Reality Plattformfunktionen und APIs. Von hier aus können Sie mit dem nächsten Thema fortfahren:

> [!div class="nextstepaction"]
> [Verlust der Nachverfolgung](tracking-loss-in-unity.md)

Oder wechseln Sie direkt zur Bereitstellung Ihrer App auf einem Gerät oder Emulator:

> [!div class="nextstepaction"]
> [Bereitstellen in HoloLens oder Windows Mixed Reality immersiven Headsets](../platform-capabilities-and-apis/using-visual-studio.md)

Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#3-advanced-features) zurückkehren.

### <a name="see-also"></a>Siehe auch

* [Stabilisierungsebene](../platform-capabilities-and-apis/hologram-stability.md#reprojection)
