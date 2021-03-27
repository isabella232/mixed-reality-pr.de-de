---
ms.openlocfilehash: 0dfbe2cda2779c2eafe54b01d2d28e703444fd1a
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636368"
---
# <a name="mrtk"></a>[<span data-ttu-id="7885c-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="7885c-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="7885c-102">Mrtk verarbeitet bestimmte Kameraeinstellungen automatisch basierend auf der [Konfiguration im Kamerasystem Profil](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings).</span><span class="sxs-lookup"><span data-stu-id="7885c-102">MRTK will handle specific camera settings automatically, based on the [configuration in the camera system profile](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings).</span></span>

<span data-ttu-id="7885c-103">**Namespace:** *Microsoft. mixedreality. Toolkit. camerasystem*</span><span class="sxs-lookup"><span data-stu-id="7885c-103">**Namespace:** *Microsoft.MixedReality.Toolkit.CameraSystem*</span></span><br>
<span data-ttu-id="7885c-104">**Typ:** *mixedrealitycamerasystem*</span><span class="sxs-lookup"><span data-stu-id="7885c-104">**Type:** *MixedRealityCameraSystem*</span></span>

<span data-ttu-id="7885c-105">Zum Überprüfen der Verfügbarkeit der Kamera hat das mixedrealitycamera-System [eine- `IsOpaque` Eigenschaft](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).</span><span class="sxs-lookup"><span data-stu-id="7885c-105">To check the camera's opaqueness, the MixedRealityCamera system has [an `IsOpaque` property](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).</span></span>

```cs
CoreServices.CameraSystem.IsOpaque;
```

# <a name="xr-sdk"></a>[<span data-ttu-id="7885c-106">XR SDK</span><span class="sxs-lookup"><span data-stu-id="7885c-106">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="7885c-107">**Namespace:** *unityengine. XR*</span><span class="sxs-lookup"><span data-stu-id="7885c-107">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="7885c-108">**Typ:** *xrdisplaysubsystem*</span><span class="sxs-lookup"><span data-stu-id="7885c-108">**Type:** *XRDisplaySubsystem*</span></span>

<span data-ttu-id="7885c-109">Sie können Skriptcode verwenden, um zur Laufzeit zu bestimmen, ob das Headset immersiv oder holografisch ist, indem Sie [displayopaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) auf dem aktiv ausgelaufenden [xrdisplaysubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html)überprüfen.</span><span class="sxs-lookup"><span data-stu-id="7885c-109">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) on the actively running [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html).</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="7885c-110">Legacy-WSA</span><span class="sxs-lookup"><span data-stu-id="7885c-110">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="7885c-111">**Namespace:** *unityengine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="7885c-111">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="7885c-112">**Typ:** *holographicsettings*</span><span class="sxs-lookup"><span data-stu-id="7885c-112">**Type:** *HolographicSettings*</span></span>

<span data-ttu-id="7885c-113">Sie können Skriptcode verwenden, um zur Laufzeit zu bestimmen, ob das Headset durch das Überprüfen von [holographicsettings. isdisplayopisch](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)durch ein immersives oder Holographic ist.</span><span class="sxs-lookup"><span data-stu-id="7885c-113">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).</span></span>