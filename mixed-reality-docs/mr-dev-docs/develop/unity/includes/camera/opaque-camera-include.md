---
ms.openlocfilehash: 76f72ac81b677acabf98444f626b7a6b908c29fb
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748529"
---
# <a name="mrtk"></a>[<span data-ttu-id="b12d6-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="b12d6-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="b12d6-102">MRTK verarbeitet bestimmte Kameraeinstellungen automatisch, basierend auf der [Konfiguration im Kamerasystemprofil.](/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings)</span><span class="sxs-lookup"><span data-stu-id="b12d6-102">MRTK will handle specific camera settings automatically, based on the [configuration in the camera system profile](/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings).</span></span>

<span data-ttu-id="b12d6-103">**Namespace:** *Microsoft.MixedReality.Toolkit.CameraSystem*</span><span class="sxs-lookup"><span data-stu-id="b12d6-103">**Namespace:** *Microsoft.MixedReality.Toolkit.CameraSystem*</span></span><br>
<span data-ttu-id="b12d6-104">**Typ:** *MixedRealityCameraSystem*</span><span class="sxs-lookup"><span data-stu-id="b12d6-104">**Type:** *MixedRealityCameraSystem*</span></span>

<span data-ttu-id="b12d6-105">Um die Nichtdurchsichtigkeit der Kamera zu überprüfen, verfügt das MixedRealityCamera-System über [die `IsOpaque` Eigenschaft](/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).</span><span class="sxs-lookup"><span data-stu-id="b12d6-105">To check the camera's opaqueness, the MixedRealityCamera system has [an `IsOpaque` property](/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).</span></span>

```cs
CoreServices.CameraSystem.IsOpaque;
```

# <a name="xr-sdk"></a>[<span data-ttu-id="b12d6-106">XR SDK</span><span class="sxs-lookup"><span data-stu-id="b12d6-106">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="b12d6-107">**Namespace:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="b12d6-107">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="b12d6-108">**Typ:** *XRDisplaySubsystem*</span><span class="sxs-lookup"><span data-stu-id="b12d6-108">**Type:** *XRDisplaySubsystem*</span></span>

<span data-ttu-id="b12d6-109">Sie können Skriptcode verwenden, um zur Laufzeit zu bestimmen, ob das Headset immersiver oder holografischer Ist, indem Sie [displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) auf dem aktiv ausgeführten [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html)überprüfen.</span><span class="sxs-lookup"><span data-stu-id="b12d6-109">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) on the actively running [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html).</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="b12d6-110">Legacy-WSA</span><span class="sxs-lookup"><span data-stu-id="b12d6-110">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="b12d6-111">**Namespace:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="b12d6-111">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="b12d6-112">**Typ:** *HolographicSettings*</span><span class="sxs-lookup"><span data-stu-id="b12d6-112">**Type:** *HolographicSettings*</span></span>

<span data-ttu-id="b12d6-113">Sie können Skriptcode verwenden, um zur Laufzeit zu bestimmen, ob das Headset immersive oder holographic ist, indem Sie [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)überprüfen.</span><span class="sxs-lookup"><span data-stu-id="b12d6-113">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).</span></span>