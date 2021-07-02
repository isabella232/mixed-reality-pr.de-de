---
title: MRTK und verwaltetes Codestriping
description: Codestriping in MRTK und Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 8b8e0f4488a6e955e599084c0b59d8c80f553a78
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176295"
---
# <a name="mrtk-and-managed-code-stripping"></a><span data-ttu-id="de7f2-104">MRTK und verwaltetes Codestriping</span><span class="sxs-lookup"><span data-stu-id="de7f2-104">MRTK and managed code stripping</span></span>

<span data-ttu-id="de7f2-105">Wenn Sie das IL2CPP-Skript-Back-End von Unity verwenden (optional in Unity 2018.4, erforderlich in 2019 und [neuer),](https://docs.unity3d.com/Manual/ManagedCodeStripping.html) wird verwalteter Code entfernt.</span><span class="sxs-lookup"><span data-stu-id="de7f2-105">When using Unity's IL2CPP scripting backend (optional in Unity 2018.4, required in 2019 and newer), [managed code stripping](https://docs.unity3d.com/Manual/ManagedCodeStripping.html) occurs.</span></span>
<span data-ttu-id="de7f2-106">Der Unity-Linker führt diesen Prozess aus, um die Binärgröße zu reduzieren und die Buildzeiten zu verringern.</span><span class="sxs-lookup"><span data-stu-id="de7f2-106">Unity's linker performs this process to reduce binary size as well as to decrease build times.</span></span>

<span data-ttu-id="de7f2-107">Das Mixed Reality Toolkit verwendet die Datei , um zu beeinflussen, wie der `link.xml` Unity-Linker MRTK-Assemblys verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="de7f2-107">The Mixed Reality Toolkit uses a file, `link.xml`, to influence how Unity's linker processes MRTK assemblies.</span></span> <span data-ttu-id="de7f2-108">Diese Datei, die vollständig in der [Unity-Dokumentation](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)beschrieben wird, bietet dem Linker Anweisungen zum Beibehalten von Code, wenn seine Verwendung nicht abgeleitet werden kann (z. B. über Reflektion).</span><span class="sxs-lookup"><span data-stu-id="de7f2-108">This file, described in full in [Unity's documentation](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML), provides the linker with instructions on how to preserve code when its usage cannot be inferred (ex: used via reflection).</span></span>

<span data-ttu-id="de7f2-109">Als flexible und anpassbare Plattform erstellt MRTK die Datei beim Import in , wenn sie nicht `link.xml` `Assets/MixedRealityToolkit.Generated` vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="de7f2-109">As a flexible and customizable platform, MRTK creates the `link.xml` file in `Assets/MixedRealityToolkit.Generated` on import, if it is found to not exist.</span></span> <span data-ttu-id="de7f2-110">Bereits vorhandene link.xml werden nicht überschrieben.</span><span class="sxs-lookup"><span data-stu-id="de7f2-110">Pre-existing link.xml files are not overwritten.</span></span> <span data-ttu-id="de7f2-111">Es wird empfohlen, `link.xml` und `link.xml.meta` der Versionskontrolle hinzugefügt zu werden.</span><span class="sxs-lookup"><span data-stu-id="de7f2-111">It is recommended that `link.xml` and `link.xml.meta` be added to version control.</span></span> <span data-ttu-id="de7f2-112">Entwickler können die Anpassungen an `Assets/MixedRealityToolkit.Generated/link.xml` die Anforderungen des Projekts anpassen.</span><span class="sxs-lookup"><span data-stu-id="de7f2-112">Developers should feel free to customize `Assets/MixedRealityToolkit.Generated/link.xml` to meet the needs of the project.</span></span>

<span data-ttu-id="de7f2-113">Standardmäßig behält die link.xml MRTK erstellte Datei die gesamte Assembly bei, die in den folgenden Daten gezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="de7f2-113">By default, the link.xml file created by MRTK preserves the entirety of the assemblies shown in the following data.</span></span>

``` xml
<linker> 
  <!-- 
    This link.xml file is provided to prevent MRTK code from being optimized away 
    during IL2CPP builds.More details on when this is needed and why this is needed 
    can be found here: https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5273 
    If your application doesn't use some specific services (for example, if teleportation system is 
    disabled in the profile), it is possible to remove their corresponding lines down 
    below(in the previous example, we would remove the TeleportSystem below). 
    It's recommended to start with this list and narrow down if you want to ensure 
    specific bits of code get optimized away. 
  --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.SDK" preserve="all"/> 
  <!-- Core systems --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.BoundarySystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.CameraSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.DiagnosticsSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.InputSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.SceneSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.SpatialAwarenessSystem" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Services.TeleportSystem" preserve="all"/> 
  <!-- Data providers --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.LeapMotion" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenVR" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.UnityAR" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality.Shared" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.XRSDK.WindowsMixedReality" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.WindowsVoiceInput" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.XRSDK" preserve="all"/> 
  <!-- Extension services --> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Extensions.HandPhysics" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Extensions.Tracking" preserve="all"/> 
  <assembly fullname = "Microsoft.MixedReality.Toolkit.Extensions.SceneTransitionService" preserve="all"/> 
</linker>
```

<span data-ttu-id="de7f2-114">Weitere Informationen zum formatierten link.xml finden Sie in der Unity-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="de7f2-114">For more information on the link.xml file format, please refer to the Unity documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="de7f2-115">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="de7f2-115">See also</span></span>

- [<span data-ttu-id="de7f2-116">Unity: Beschriftung von verwaltetem Code</span><span class="sxs-lookup"><span data-stu-id="de7f2-116">Unity: Managed Code Stripping</span></span>](https://docs.unity3d.com/Manual/ManagedCodeStripping.html)
- [<span data-ttu-id="de7f2-117">Unity: Verknüpfen der XML-Datei</span><span class="sxs-lookup"><span data-stu-id="de7f2-117">Unity: Link XML file</span></span>](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)
