---
ms.openlocfilehash: d30bf4b5c382ca953314996dd51087427224e872158b607fd1c5f4c85c62a124
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212304"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK verfügt derzeit nicht über Hilfsprojekte für den Neuprojektionsmodus. Weitere Informationen finden Sie auf einer der anderen Registerkarten.

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Der Neuprojektionsmodus kann konfiguriert werden, indem [XRDisplaySubsystem.reprojectionMode](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-reprojectionMode.html) auf den entsprechenden Wert festgelegt wird.

Wenn Sie z. B. eine rein auf Ausrichtung ausgerichtete [Benutzeroberfläche](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) mit festem Text gesperrtem Inhalt erstellen (z. B. 360-Grad-Videoinhalte), können Sie den Reprojection-Modus explizit nur auf Ausrichtung festlegen, indem Sie ihn auf [ReprojectionMode.OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.ReprojectionMode.html)festlegen.

# <a name="legacy-wsa"></a>[Legacy-WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Der Neuprojektionsmodus kann konfiguriert werden, indem [HolographicSettings.ReprojectionMode](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) auf den entsprechenden Wert festgelegt wird.

Wenn Sie z. B. eine [rein auf Ausrichtung ausgerichtete Benutzeroberfläche](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) mit festem Text gesperrtem Inhalt erstellen (z. B. 360-Grad-Videoinhalte), können Sie den Reprojection-Modus explizit nur auf Ausrichtung festlegen, indem Sie ihn auf [HolographicReprojectionMode.OrientationOnly](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html)festlegen.