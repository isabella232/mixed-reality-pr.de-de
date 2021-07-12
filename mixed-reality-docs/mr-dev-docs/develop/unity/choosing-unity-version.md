---
title: Auswählen einer Unity-Version und eines XR-Plug-Ins
description: Bleiben Sie über die neuesten Unity- und XR-Plug-In-Empfehlungen für HoloLens Anwendungsentwicklung auf dem Laufenden.
author: hferrone
ms.author: v-hferrone
ms.date: 06/24/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Unity
ms.openlocfilehash: c69576e991f3fe32ae69fce10069ecdae65b3f9a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603681"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="6fd4f-104">Auswählen einer Unity-Version und eines XR-Plug-Ins</span><span class="sxs-lookup"><span data-stu-id="6fd4f-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="6fd4f-105">Es wird derzeit empfohlen, **Unity 2020.3 LTS** mit dem neuesten Mixed Reality OpenXR-Plug-In für die Mixed Reality-Entwicklung zu installieren. Sie können aber auch Apps mit anderen Unity-Konfigurationen erstellen.</span><span class="sxs-lookup"><span data-stu-id="6fd4f-105">While we currently **recommend installing Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20203-lts-recommended"></a><span data-ttu-id="6fd4f-106">Unity 2020.3 LTS (empfohlen)</span><span class="sxs-lookup"><span data-stu-id="6fd4f-106">Unity 2020.3 LTS (Recommended)</span></span>

<span data-ttu-id="6fd4f-107">Die derzeit von Microsoft empfohlene Unity-Konfiguration für HoloLens 2- und Windows Mixed Reality-Entwicklung ist **Unity 2020.3 LTS** mit dem neuesten Mixed Reality OpenXR-Plug-In.</span><span class="sxs-lookup"><span data-stu-id="6fd4f-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin**.</span></span> <span data-ttu-id="6fd4f-108">Sie **müssen** Unity Patch Release 2020.3.8f1 oder höher verwenden, um bekannte Leistungsprobleme mit früheren 2020.3-Builds zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="6fd4f-108">You **must** use Unity patch release 2020.3.8f1 or later to avoid known performance issues with earlier 2020.3 builds.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6fd4f-109">Unity 2020 unterstützt keine Zielgruppenadressierung HoloLens (1. Generation).</span><span class="sxs-lookup"><span data-stu-id="6fd4f-109">Unity 2020 does not support targeting HoloLens (1st gen).</span></span> <span data-ttu-id="6fd4f-110">Diese Headsets werden in **[Unity 2019 LTS](#unity-20194-lts)** mit integriertem Legacy-XR für den gesamten Lebenszyklus von Unity 2019 LTS bis Mitte 2022 weiterhin unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6fd4f-110">These headsets remain supported in **[Unity 2019 LTS](#unity-20194-lts)** with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

<span data-ttu-id="6fd4f-111">Die beste Möglichkeit zum Installieren und Verwalten von Unity ist der **Unity Hub:**</span><span class="sxs-lookup"><span data-stu-id="6fd4f-111">The best way to install and manage Unity is through the **Unity Hub**:</span></span>

1. <span data-ttu-id="6fd4f-112">Installieren <a href="https://unity3d.com/get-unity/download" target="_blank">**Sie Unity Hub**</a>.</span><span class="sxs-lookup"><span data-stu-id="6fd4f-112">Install <a href="https://unity3d.com/get-unity/download" target="_blank">**Unity Hub**</a>.</span></span>
2. <span data-ttu-id="6fd4f-113">Wählen Sie die **Registerkarte Installs** (Installationen) und dann **Add (Hinzufügen) aus.**</span><span class="sxs-lookup"><span data-stu-id="6fd4f-113">Select the **Installs** tab and choose **Add**.</span></span>
3. <span data-ttu-id="6fd4f-114">Wählen **Sie Unity 2020.3 LTS aus,** und klicken Sie auf **Weiter.**</span><span class="sxs-lookup"><span data-stu-id="6fd4f-114">Select **Unity 2020.3 LTS** and click **Next**.</span></span>

![Unity Hub: Installieren einer neuen Version](images/unity-hub-img-01.png)

4. <span data-ttu-id="6fd4f-116">Überprüfen Sie die folgenden Komponenten unter **"Plattformen":**</span><span class="sxs-lookup"><span data-stu-id="6fd4f-116">Check the following components under **'Platforms'**:</span></span>
    * <span data-ttu-id="6fd4f-117">**Buildunterstützung für Universelle Windows-Plattform**</span><span class="sxs-lookup"><span data-stu-id="6fd4f-117">**Universal Windows Platform Build Support**</span></span>
    * <span data-ttu-id="6fd4f-118">**Windows-Buildunterstützung (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="6fd4f-118">**Windows Build Support (IL2CPP)**</span></span>

![Unity: Option „Buildunterstützung für Universelle Windows-Plattform“](../images/Unity_Install_Option_UWP.png)

5. <span data-ttu-id="6fd4f-120">Wenn Sie Unity zuvor ohne diese Optionen installiert haben, können Sie diese über das Menü **"Module hinzufügen"** im Unity-Hub hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="6fd4f-120">If you previously installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Unity: Option „Windows-Buildunterstützung“](../images/Unity_Install_Option_UWP2.png)

<span data-ttu-id="6fd4f-122">Sobald Sie Unity 2020.3 installiert haben, beginnen Sie mit dem Erstellen eines Projekts oder Aktualisieren eines vorhandenen Projekts mithilfe des openXR Mixed Reality-Plug-Ins:</span><span class="sxs-lookup"><span data-stu-id="6fd4f-122">Once you have Unity 2020.3 installed, get started creating a project or upgrading an existing project using the Mixed Reality OpenXR plugin:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6fd4f-123">Einrichten Ihres Projekts mit dem OpenXR-Plug-In</span><span class="sxs-lookup"><span data-stu-id="6fd4f-123">Set up your project with the OpenXR plugin</span></span>](xr-project-setup.md?tabs=openxr)

> [!NOTE]
> <span data-ttu-id="6fd4f-124">Es wird zwar empfohlen, OpenXR für alle neuen Projekte zu verwenden, Unity 2020.3 LTS unterstützt jedoch auch das [Windows XR-Plug-In](xr-project-setup.md?tabs=windowsxr).</span><span class="sxs-lookup"><span data-stu-id="6fd4f-124">While we recommend using OpenXR for all new projects, Unity 2020.3 LTS also supports the [Windows XR plugin](xr-project-setup.md?tabs=windowsxr).</span></span> <span data-ttu-id="6fd4f-125">Dieses Plug-In wird vollständig unterstützt, obwohl es keine neuen Features wie AR Foundation 4.0-Unterstützung erhält.</span><span class="sxs-lookup"><span data-stu-id="6fd4f-125">This plugin is fully supported, although it won't receive new features such as AR Foundation 4.0 support.</span></span>

## <a name="unity-20194-lts"></a><span data-ttu-id="6fd4f-126">Unity 2019.4 LTS</span><span class="sxs-lookup"><span data-stu-id="6fd4f-126">Unity 2019.4 LTS</span></span>

<span data-ttu-id="6fd4f-127">Wenn Sie Unity 2019 verwenden müssen, können Sie **Unity 2019 LTS mit integriertem Legacy-XR verwenden.**</span><span class="sxs-lookup"><span data-stu-id="6fd4f-127">If you need to use Unity 2019, you can use **Unity 2019 LTS with Legacy Built-in XR**.</span></span> <span data-ttu-id="6fd4f-128">Klicken Sie hier, um mit der älteren integrierten XR in Unity 2019.4 LTS zu beginnen:</span><span class="sxs-lookup"><span data-stu-id="6fd4f-128">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6fd4f-129">Einrichten Ihres Projekts mit legacy-integriertem XR</span><span class="sxs-lookup"><span data-stu-id="6fd4f-129">Set up your project with Legacy Built-in XR</span></span>](xr-project-setup.md?tabs=legacy)

> [!NOTE]
> <span data-ttu-id="6fd4f-130">Unity hat die integrierte Legacy-XR-Unterstützung ab Unity 2019 als veraltet bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="6fd4f-130">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="6fd4f-131">Unity 2019 bietet zwar ein neues XR-Plug-In-Framework, Microsoft empfiehlt diesen Pfad in Unity 2019 jedoch aufgrund von Azure Spatial Anchors-Inkompatibilitäten mit AR Foundation 2 nicht.</span><span class="sxs-lookup"><span data-stu-id="6fd4f-131">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="6fd4f-132">In Unity 2020 wird Azure Spatial Anchors im XR-Plug-In-Framework unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6fd4f-132">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="6fd4f-133">Wenn Sie Apps für HoloLens (1. Generation) entwickeln, bleiben diese Headsets in Unity 2019 LTS mit integriertem Legacy-XR für den gesamten Lebenszyklus von Unity 2019 LTS bis Mitte 2022 unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6fd4f-133">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20212"></a><span data-ttu-id="6fd4f-134">Unity 2021.2</span><span class="sxs-lookup"><span data-stu-id="6fd4f-134">Unity 2021.2</span></span>

<span data-ttu-id="6fd4f-135">Wenn Sie frühe **Unity 2021.2-Builds** ausprobieren, beginnen Sie mit dem Mixed Reality [**OpenXR-Plug-In.**](xr-project-setup.md?tabs=openxr)</span><span class="sxs-lookup"><span data-stu-id="6fd4f-135">If you are trying out early **Unity 2021.2** builds, get started with the [**Mixed Reality OpenXR plugin**](xr-project-setup.md?tabs=openxr).</span></span> <span data-ttu-id="6fd4f-136">Das OpenXR-Plug-In ist der einzige Pfad für die Mixed Reality-Entwicklung in Unity 2021.2 und höher, da unity 2021.1 die endgültige Unity-Version zur Unterstützung des Windows XR-Plug-Ins war.</span><span class="sxs-lookup"><span data-stu-id="6fd4f-136">The OpenXR plugin is the only path for mixed reality development in Unity 2021.2 and later, as the final Unity version to support the Windows XR plugin was Unity 2021.1.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="6fd4f-137">Unity 2018.4 LTS</span><span class="sxs-lookup"><span data-stu-id="6fd4f-137">Unity 2018.4 LTS</span></span>

<span data-ttu-id="6fd4f-138">Unity 2018.4 LTS hat das Ende des zwei jahre dauernden Long-Term-Supportfensters von Unity erreicht und empfängt keine Updates mehr von Unity, obwohl Ihre Projekte weiterhin ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="6fd4f-138">Unity 2018.4 LTS has reached the end of Unity's two-year Long-Term Support window and is no longer receiving updates from Unity, although your projects will continue to run.</span></span>

<span data-ttu-id="6fd4f-139">Wenn Sie über ein Unity 2018-Projekt verfügen, sollten Sie eine Migration zu Unity 2020.3 LTS und dem Mixed Reality OpenXR-Plug-In planen.</span><span class="sxs-lookup"><span data-stu-id="6fd4f-139">If you have a Unity 2018 project, you should consider planning for a migration forward to Unity 2020.3 LTS and the Mixed Reality OpenXR plugin.</span></span>