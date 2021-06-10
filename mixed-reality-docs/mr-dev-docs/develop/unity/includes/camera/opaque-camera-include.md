---
ms.openlocfilehash: 76f72ac81b677acabf98444f626b7a6b908c29fb
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748529"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK verarbeitet bestimmte Kameraeinstellungen automatisch, basierend auf der [Konfiguration im Kamerasystemprofil.](/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings)

**Namespace:** *Microsoft.MixedReality.Toolkit.CameraSystem*<br>
**Typ:** *MixedRealityCameraSystem*

Um die Nichtdurchsichtigkeit der Kamera zu überprüfen, verfügt das MixedRealityCamera-System über [die `IsOpaque` Eigenschaft](/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).

```cs
CoreServices.CameraSystem.IsOpaque;
```

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

**Namespace:** *UnityEngine.XR*<br>
**Typ:** *XRDisplaySubsystem*

Sie können Skriptcode verwenden, um zur Laufzeit zu bestimmen, ob das Headset immersiver oder holografischer Ist, indem Sie [displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) auf dem aktiv ausgeführten [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html)überprüfen.

# <a name="legacy-wsa"></a>[Legacy-WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

**Namespace:** *UnityEngine.XR.WSA*<br>
**Typ:** *HolographicSettings*

Sie können Skriptcode verwenden, um zur Laufzeit zu bestimmen, ob das Headset immersive oder holographic ist, indem Sie [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)überprüfen.