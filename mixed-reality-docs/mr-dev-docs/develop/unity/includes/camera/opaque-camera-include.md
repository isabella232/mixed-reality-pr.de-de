---
ms.openlocfilehash: 73aba70497323d406b5138eca9c7d2054b8d8b3cea6e82ef67e962a21876c280
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212303"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MrTK verarbeitet bestimmte Kameraeinstellungen automatisch, basierend auf der Konfiguration [im Kamerasystemprofil](/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings).

**Namespace:** *Microsoft.MixedReality.Toolkit.CameraSystem*<br>
**Typ:** *MixedRealityCameraSystem*

Um die Deckkraft der Kamera zu überprüfen, verfügt das MixedRealityCamera-System [über die `IsOpaque` -Eigenschaft](/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).

```cs
CoreServices.CameraSystem.IsOpaque;
```

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

**Namespace:** *UnityEngine.XR*<br>
**Typ:** *XRDisplaySubsystem*

Sie können Skriptcode verwenden, um zur Laufzeit zu bestimmen, ob das Headset immersives oder holografisches Headset ist, indem Sie [displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) auf dem aktiv ausgeführten [XRDisplaySubsystem überprüfen.](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html)

# <a name="legacy-wsa"></a>[Legacy-WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

**Namespace:** *UnityEngine.XR.WSA*<br>
**Typ:** *HolographicSettings*

Sie können Skriptcode verwenden, um zur Laufzeit zu bestimmen, ob das Headset immersiver oder holografischer Art ist, indem Sie [HolographicSettings.IsDisplayOpaque überprüfen.](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)