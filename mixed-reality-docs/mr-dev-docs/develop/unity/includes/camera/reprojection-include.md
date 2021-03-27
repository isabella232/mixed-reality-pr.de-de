---
ms.openlocfilehash: c5775d29fb3934d324cceb6dc451e6588d15fe6d
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636359"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Mrtk verfügt zurzeit nicht über Hilfsprogramme für den Modus für die neuprojektion. Weitere Informationen finden Sie auf einer der anderen Registerkarten.

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Der Modus für die neuprojektion kann durch Festlegen von [xrdisplaysubsystem. reprojectionmode](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-reprojectionMode.html) auf den entsprechenden Wert konfiguriert werden.

Wenn Sie z. b. eine [Ausrichtungs bezogene](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) Umgebung mit ordnungsgemäß gesperrtem Inhalt (z. b. 360-Grad-Videoinhalt) entwickeln, können Sie den neuprojektions Modus explizit auf "Orientation" festlegen, indem Sie ihn auf " [reprojectionmode. orientationonly](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.ReprojectionMode.html)" festlegen.

# <a name="legacy-wsa"></a>[Legacy-WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Der Modus für die neuprojektion kann durch Festlegen von [holographicsettings. reprojectionmode](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) auf den entsprechenden Wert konfiguriert werden.

Wenn Sie z. b. eine [Ausrichtungs bezogene](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) Umgebung mit ordnungsgemäß gesperrtem Inhalt (z. b. 360-Grad-Videoinhalt) entwickeln, können Sie den neuprojektions Modus explizit auf die Ausrichtung festlegen, indem Sie ihn auf [holographikreprojectionmode. orientationonly](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html)festlegen.