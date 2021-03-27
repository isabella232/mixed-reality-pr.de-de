---
ms.openlocfilehash: c5775d29fb3934d324cceb6dc451e6588d15fe6d
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636359"
---
# <a name="mrtk"></a>[<span data-ttu-id="352c8-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="352c8-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="352c8-102">Mrtk verfügt zurzeit nicht über Hilfsprogramme für den Modus für die neuprojektion.</span><span class="sxs-lookup"><span data-stu-id="352c8-102">MRTK doesn't currently have helpers for the reprojection mode.</span></span> <span data-ttu-id="352c8-103">Weitere Informationen finden Sie auf einer der anderen Registerkarten.</span><span class="sxs-lookup"><span data-stu-id="352c8-103">Please see one of the other tabs for more information.</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="352c8-104">XR SDK</span><span class="sxs-lookup"><span data-stu-id="352c8-104">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="352c8-105">Der Modus für die neuprojektion kann durch Festlegen von [xrdisplaysubsystem. reprojectionmode](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-reprojectionMode.html) auf den entsprechenden Wert konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="352c8-105">The reprojection mode is configurable by setting [XRDisplaySubsystem.reprojectionMode](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-reprojectionMode.html) to the appropriate value.</span></span>

<span data-ttu-id="352c8-106">Wenn Sie z. b. eine [Ausrichtungs bezogene](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) Umgebung mit ordnungsgemäß gesperrtem Inhalt (z. b. 360-Grad-Videoinhalt) entwickeln, können Sie den neuprojektions Modus explizit auf "Orientation" festlegen, indem Sie ihn auf " [reprojectionmode. orientationonly](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.ReprojectionMode.html)" festlegen.</span><span class="sxs-lookup"><span data-stu-id="352c8-106">For example, if you're building an [orientation-only experience](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) with rigidly body-locked content (for example, 360-degree video content), you can explicitly set the reprojection mode to orientation only by setting it to [ReprojectionMode.OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.ReprojectionMode.html).</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="352c8-107">Legacy-WSA</span><span class="sxs-lookup"><span data-stu-id="352c8-107">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="352c8-108">Der Modus für die neuprojektion kann durch Festlegen von [holographicsettings. reprojectionmode](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) auf den entsprechenden Wert konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="352c8-108">The reprojection mode is configurable by setting [HolographicSettings.ReprojectionMode](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) to the appropriate value.</span></span>

<span data-ttu-id="352c8-109">Wenn Sie z. b. eine [Ausrichtungs bezogene](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) Umgebung mit ordnungsgemäß gesperrtem Inhalt (z. b. 360-Grad-Videoinhalt) entwickeln, können Sie den neuprojektions Modus explizit auf die Ausrichtung festlegen, indem Sie ihn auf [holographikreprojectionmode. orientationonly](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html)festlegen.</span><span class="sxs-lookup"><span data-stu-id="352c8-109">For example, if you're building an [orientation-only experience](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) with rigidly body-locked content (for example, 360-degree video content), you can explicitly set the reprojection mode to orientation only by setting it to [HolographicReprojectionMode.OrientationOnly](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).</span></span>