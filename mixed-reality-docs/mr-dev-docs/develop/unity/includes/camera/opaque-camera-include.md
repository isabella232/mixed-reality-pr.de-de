---
ms.openlocfilehash: 0dfbe2cda2779c2eafe54b01d2d28e703444fd1a
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636368"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Mrtk verarbeitet bestimmte Kameraeinstellungen automatisch basierend auf der [Konfiguration im Kamerasystem Profil](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings).

**Namespace:** *Microsoft. mixedreality. Toolkit. camerasystem*<br>
**Typ:** *mixedrealitycamerasystem*

Zum Überprüfen der Verfügbarkeit der Kamera hat das mixedrealitycamera-System [eine- `IsOpaque` Eigenschaft](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).

```cs
CoreServices.CameraSystem.IsOpaque;
```

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

**Namespace:** *unityengine. XR*<br>
**Typ:** *xrdisplaysubsystem*

Sie können Skriptcode verwenden, um zur Laufzeit zu bestimmen, ob das Headset immersiv oder holografisch ist, indem Sie [displayopaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) auf dem aktiv ausgelaufenden [xrdisplaysubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html)überprüfen.

# <a name="legacy-wsa"></a>[Legacy-WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

**Namespace:** *unityengine. XR. WSA*<br>
**Typ:** *holographicsettings*

Sie können Skriptcode verwenden, um zur Laufzeit zu bestimmen, ob das Headset durch das Überprüfen von [holographicsettings. isdisplayopisch](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)durch ein immersives oder Holographic ist.