---
title: Auswählen einer Unity-Version und eines XR-Plug-Ins
description: Bleiben Sie über die neuesten Unity- und XR-Plug-In-Empfehlungen für die HoloLens-Anwendungsentwicklung auf dem Laufenden.
author: hferrone
ms.author: v-hferrone
ms.date: 06/24/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Unity
ms.openlocfilehash: 646a0ec3b3b332b038509cba39caa085c1590c1a
ms.sourcegitcommit: 593e8f80297ac0b5eccb2488d3f333885eab9adf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2021
ms.locfileid: "112921424"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="c43aa-104">Auswählen einer Unity-Version und eines XR-Plug-Ins</span><span class="sxs-lookup"><span data-stu-id="c43aa-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="c43aa-105">Wir empfehlen zwar derzeit die **Installation von Unity 2020.3 LTS mit dem neuesten Mixed Reality OpenXR-Plug-In** für Mixed Reality Entwicklung, Sie können aber auch Apps mit anderen Unity-Konfigurationen erstellen.</span><span class="sxs-lookup"><span data-stu-id="c43aa-105">While we currently **recommend installing Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20203-lts-recommended"></a><span data-ttu-id="c43aa-106">Unity 2020.3 LTS (empfohlen)</span><span class="sxs-lookup"><span data-stu-id="c43aa-106">Unity 2020.3 LTS (Recommended)</span></span>

<span data-ttu-id="c43aa-107">Die aktuelle empfohlene Unity-Konfiguration von Microsoft für HoloLens 2 und Windows Mixed Reality Entwicklung ist **Unity 2020.3 LTS mit dem neuesten Mixed Reality OpenXR-Plug-In.**</span><span class="sxs-lookup"><span data-stu-id="c43aa-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin**.</span></span> <span data-ttu-id="c43aa-108">Sie MÜSSEN Unity Patch Release 2020.3.8f1 oder höher verwenden, um bekannte Leistungsprobleme mit früheren Builds von 2020.3 zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="c43aa-108">You MUST use Unity patch release 2020.3.8f1 or later to avoid known performance issues with earlier 2020.3 builds.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c43aa-109">Unity 2020 unterstützt keine Zielgruppenadressierung für HoloLens (1. Generation).</span><span class="sxs-lookup"><span data-stu-id="c43aa-109">Unity 2020 does not support targeting HoloLens (1st gen).</span></span> <span data-ttu-id="c43aa-110">Diese Headsets werden in **[Unity 2019 LTS](#unity-20194-lts)** mit legacy-integriertem XR für den gesamten Lebenszyklus von Unity 2019 LTS bis Mitte 2022 weiterhin unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c43aa-110">These headsets remain supported in **[Unity 2019 LTS](#unity-20194-lts)** with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>
>
> [!NOTE]
> <span data-ttu-id="c43aa-111">Einige Pakete sind noch nicht mit Mixed Reality-Projekten in Unity 2020 LTS kompatibel:</span><span class="sxs-lookup"><span data-stu-id="c43aa-111">Some packages are not yet compatible with mixed reality projects in Unity 2020 LTS:</span></span>
> 
> * <span data-ttu-id="c43aa-112">Die Universal Rendering Pipeline (URP) 10.5.0 oder älter weist auf HoloLens 2 Geräten ein bekanntes Leistungsproblem auf.</span><span class="sxs-lookup"><span data-stu-id="c43aa-112">The Universal Rendering Pipeline (URP) 10.5.0 or older has a known performance issue on HoloLens 2 devices.</span></span> <span data-ttu-id="c43aa-113">_(behoben in der nächsten URP-Version)_</span><span class="sxs-lookup"><span data-stu-id="c43aa-113">_(fixed in the next URP release)_</span></span>
> * <span data-ttu-id="c43aa-114">Azure Remote Rendering wurde noch kein aktualisiertes Release veröffentlicht, das Unity 2020 unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c43aa-114">Azure Remote Rendering has not yet shipped an updated release supporting Unity 2020.</span></span>
>
> <span data-ttu-id="c43aa-115">Wenn Ihr Unity-Projekt die Universelle Renderingpipeline oder Azure Remote Rendering verwendet, wird empfohlen, das Upgrade Ihres Projekts auf Unity 2020 abzuwarten, bis aktualisierte Pakete verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="c43aa-115">If your Unity project uses the Universal Rendering Pipeline or Azure Remote Rendering, we recommend holding off on upgrading your project to Unity 2020 until updated packages are available.</span></span>

<span data-ttu-id="c43aa-116">Der beste Weg, um Unity zu installieren und zu verwalten, ist über <a href="https://unity3d.com/get-unity/download" target="_blank">Unity Hub</a>.</span><span class="sxs-lookup"><span data-stu-id="c43aa-116">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">Unity Hub</a>.</span></span> <span data-ttu-id="c43aa-117">Öffnen Sie nach der Installation Unity Hub:</span><span class="sxs-lookup"><span data-stu-id="c43aa-117">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="c43aa-118">Wählen Sie die Registerkarte **Installationen** und dann **HINZUFÜGEN** aus.</span><span class="sxs-lookup"><span data-stu-id="c43aa-118">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="c43aa-119">Wählen Sie Unity 2020.3 LTS aus, und klicken Sie auf **Weiter.**</span><span class="sxs-lookup"><span data-stu-id="c43aa-119">Select Unity 2020.3 LTS and click **Next**</span></span>

![Unity Hub in der neuen Version](images/unity-hub-img-01.png)

3. <span data-ttu-id="c43aa-121">Überprüfen Sie die folgenden Komponenten unter **"Plattformen".**</span><span class="sxs-lookup"><span data-stu-id="c43aa-121">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="c43aa-122">**Buildunterstützung für Universelle Windows-Plattform**</span><span class="sxs-lookup"><span data-stu-id="c43aa-122">**Universal Windows Platform Build Support**</span></span>
    * <span data-ttu-id="c43aa-123">**Windows-Buildunterstützung (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="c43aa-123">**Windows Build Support (IL2CPP)**</span></span>

![Unity: Option „Buildunterstützung für Universelle Windows-Plattform“](../images/Unity_Install_Option_UWP.png)

4. <span data-ttu-id="c43aa-125">Wenn Sie Unity ohne diese Optionen installiert haben, können Sie sie über das Menü **"Module hinzufügen"** in Unity Hub hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="c43aa-125">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Unity: Option „Windows-Buildunterstützung“](../images/Unity_Install_Option_UWP2.png)

> [!div class="nextstepaction"]
> [<span data-ttu-id="c43aa-127">Verwenden des OpenXR-Plug-Ins</span><span class="sxs-lookup"><span data-stu-id="c43aa-127">Using the OpenXR plugin</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=openxr)

> [!NOTE]
> <span data-ttu-id="c43aa-128">Es wird zwar empfohlen, OpenXR für alle neuen Projekte zu verwenden, Unity 2020.3 LTS unterstützt jedoch auch das [Windows XR-Plug-In](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr).</span><span class="sxs-lookup"><span data-stu-id="c43aa-128">While we recommend using OpenXR for all new projects, Unity 2020.3 LTS also supports the [Windows XR plugin](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr).</span></span> <span data-ttu-id="c43aa-129">Dieses Plug-In wird vollständig unterstützt, obwohl es keine neuen Features wie AR Foundation 4.0-Unterstützung erhält.</span><span class="sxs-lookup"><span data-stu-id="c43aa-129">This plugin is fully supported, although it won't receive new features such as AR Foundation 4.0 support.</span></span>

## <a name="unity-20194-lts"></a><span data-ttu-id="c43aa-130">Unity 2019.4 LTS</span><span class="sxs-lookup"><span data-stu-id="c43aa-130">Unity 2019.4 LTS</span></span>

<span data-ttu-id="c43aa-131">Wenn Sie Unity 2019 verwenden müssen, können Sie **Unity 2019 LTS mit legacy-integriertem XR** verwenden.</span><span class="sxs-lookup"><span data-stu-id="c43aa-131">If you need to use Unity 2019, you can use **Unity 2019 LTS with Legacy Built-in XR**.</span></span> <span data-ttu-id="c43aa-132">Klicken Sie hier, um mit dem älteren integrierten XR in Unity 2019.4 LTS zu beginnen:</span><span class="sxs-lookup"><span data-stu-id="c43aa-132">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c43aa-133">Einrichten von Legacy-integriertem XR</span><span class="sxs-lookup"><span data-stu-id="c43aa-133">Set up Legacy Built-in XR</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=legacy)

> [!NOTE]
> <span data-ttu-id="c43aa-134">Unity hat die legacy-integrierte XR-Unterstützung ab Unity 2019 als veraltet erklärt.</span><span class="sxs-lookup"><span data-stu-id="c43aa-134">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="c43aa-135">Während Unity 2019 ein neues XR-Plug-In-Framework bietet, empfiehlt Microsoft diesen Pfad in Unity 2019 aufgrund von Inkompatibilitäten von Azure Spatial Anchors mit AR Foundation 2 derzeit nicht.</span><span class="sxs-lookup"><span data-stu-id="c43aa-135">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="c43aa-136">In Unity 2020 wird Azure Spatial Anchors im XR-Plug-In-Framework unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c43aa-136">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="c43aa-137">Wenn Sie Apps für HoloLens (1. Generation) entwickeln, werden diese Headsets in Unity 2019 LTS mit legacy-integriertem XR für den gesamten Lebenszyklus von Unity 2019 LTS bis Mitte 2022 weiterhin unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c43aa-137">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20211"></a><span data-ttu-id="c43aa-138">Unity 2021.1</span><span class="sxs-lookup"><span data-stu-id="c43aa-138">Unity 2021.1</span></span>

<span data-ttu-id="c43aa-139">Wenn Sie frühe **Unity 2021.1-Builds** ausprobieren, sollten Sie mit dem **OpenXR-Plug-In** fortschreiten, da das Windows XR-Plug-In dort veraltet ist.</span><span class="sxs-lookup"><span data-stu-id="c43aa-139">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="c43aa-140">Ab Unity 2021.2 ist das OpenXR-Plug-In der einzige Pfad für Mixed Reality Entwicklung, da das Windows XR-Plug-In nicht mehr unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="c43aa-140">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="c43aa-141">Unity 2018.4 LTS</span><span class="sxs-lookup"><span data-stu-id="c43aa-141">Unity 2018.4 LTS</span></span>

<span data-ttu-id="c43aa-142">Wenn Sie bereits über ein Projekt mit Unity 2018.4 LTS verfügen, wird Ihre Unity-Engine nach der Veröffentlichung 2 Jahre lang weiterhin unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c43aa-142">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="c43aa-143">Unity 2018 LTS wird im Spring 2021 das Ende des Diensts erreichen.</span><span class="sxs-lookup"><span data-stu-id="c43aa-143">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>
