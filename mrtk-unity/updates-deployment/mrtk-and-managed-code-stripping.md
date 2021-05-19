---
title: MRTK und Entfernen von verwaltetem Code
description: Code stripping in MRTK und Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 09e5140fd9585c19eacac5ba937eaf4ea8f2a8ea
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143737"
---
# <a name="mrtk-and-unity-managed-code-stripping"></a><span data-ttu-id="2ec68-104">MRTK- und Unity-Stripping für verwalteten Code</span><span class="sxs-lookup"><span data-stu-id="2ec68-104">MRTK and Unity managed code stripping</span></span>

<span data-ttu-id="2ec68-105">Bei Verwendung des IL2CPP-Skript-Back-Ends von Unity (optional in Unity 2018.4, erforderlich ab 2019) erfolgt das Stripping von [verwaltetem Code.](https://docs.unity3d.com/Manual/ManagedCodeStripping.html)</span><span class="sxs-lookup"><span data-stu-id="2ec68-105">When using Unity's IL2CPP scripting backend (optional in Unity 2018.4, required in 2019 and newer), [managed code stripping](https://docs.unity3d.com/Manual/ManagedCodeStripping.html) occurs.</span></span>
<span data-ttu-id="2ec68-106">Der Linker von Unity führt diesen Prozess aus, um die Binärgröße zu reduzieren und die Buildzeiten zu verkürzen.</span><span class="sxs-lookup"><span data-stu-id="2ec68-106">Unity's linker performs this process to reduce binary size as well as to decrease build times.</span></span>

<span data-ttu-id="2ec68-107">Das Mixed Reality Toolkit verwendet eine Datei, `link.xml` , um zu beeinflussen, wie der Linker von Unity MRTK-Assemblys verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="2ec68-107">The Mixed Reality Toolkit uses a file, `link.xml`, to influence how Unity's linker processes MRTK assemblies.</span></span> <span data-ttu-id="2ec68-108">Diese Datei, die vollständig in der [Unity-Dokumentation](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)beschrieben ist, stellt dem Linker Anweisungen zum Beibehalten von Code bereit, wenn seine Verwendung nicht abgeleitet werden kann (z. B. über Reflektion verwendet).</span><span class="sxs-lookup"><span data-stu-id="2ec68-108">This file, described in full in [Unity's documentation](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML), provides the linker with instructions on how to preserve code when its usage cannot be inferred (ex: used via reflection).</span></span>

<span data-ttu-id="2ec68-109">Als flexible und anpassbare Plattform erstellt MRTK die `link.xml` Datei beim Import in , wenn sie nicht vorhanden `Assets/MixedRealityToolkit.Generated` ist.</span><span class="sxs-lookup"><span data-stu-id="2ec68-109">As a flexible and customizable platform, MRTK creates the `link.xml` file in `Assets/MixedRealityToolkit.Generated` on import, if it is found to not exist.</span></span> <span data-ttu-id="2ec68-110">Bereits vorhandene link.xml Dateien werden nicht überschrieben.</span><span class="sxs-lookup"><span data-stu-id="2ec68-110">Pre-existing link.xml files are not overwritten.</span></span> <span data-ttu-id="2ec68-111">Es wird empfohlen, `link.xml` und `link.xml.meta` der Versionskontrolle hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="2ec68-111">It is recommended that `link.xml` and `link.xml.meta` be added to version control.</span></span> <span data-ttu-id="2ec68-112">Entwickler sollten sich gerne an die Anforderungen des Projekts anpassen `Assets/MixedRealityToolkit.Generated/link.xml` lassen.</span><span class="sxs-lookup"><span data-stu-id="2ec68-112">Developers should feel free to customize `Assets/MixedRealityToolkit.Generated/link.xml` to meet the needs of the project.</span></span>

<span data-ttu-id="2ec68-113">Standardmäßig behält die von MRTK erstellte link.xml-Datei die gesamten Assemblys bei, die in den folgenden Daten angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="2ec68-113">By default, the link.xml file created by MRTK preserves the entirety of the assemblies shown in the following data.</span></span>

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

<span data-ttu-id="2ec68-114">Weitere Informationen zum link.xml-Dateiformat finden Sie in der Unity-Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="2ec68-114">For more information on the link.xml file format, please refer to the Unity documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ec68-115">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="2ec68-115">See also</span></span>

- [<span data-ttu-id="2ec68-116">Unity: Stripping von verwaltetem Code</span><span class="sxs-lookup"><span data-stu-id="2ec68-116">Unity: Managed Code Stripping</span></span>](https://docs.unity3d.com/Manual/ManagedCodeStripping.html)
- [<span data-ttu-id="2ec68-117">Unity: LINK-XML-Datei</span><span class="sxs-lookup"><span data-stu-id="2ec68-117">Unity: Link XML file</span></span>](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML)
