---
title: Auswählen einer Unity-Version und eines XR-Plug-Ins
description: Bleiben Sie über die neuesten Unity- und XR-Plug-In-Empfehlungen für die Entwicklung von HoloLens-Anwendungen auf dem laufenden.
author: hferrone
ms.author: v-hferrone
ms.date: 05/27/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Unity
ms.openlocfilehash: 1f658c0e69091ce0aaeb37b7f427e57f060c3fb2
ms.sourcegitcommit: 62e5909b837c9c7ecedd040164f2308868db4723
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2021
ms.locfileid: "111741922"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="5fbdc-104">Auswählen einer Unity-Version und eines XR-Plug-Ins</span><span class="sxs-lookup"><span data-stu-id="5fbdc-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="5fbdc-105">Es wird derzeit empfohlen, **Unity 2020.3 LTS** mit dem neuesten Mixed Reality OpenXR-Plug-In für die Mixed Reality-Entwicklung zu installieren. Sie können aber auch Apps mit anderen Unity-Konfigurationen erstellen.</span><span class="sxs-lookup"><span data-stu-id="5fbdc-105">While we currently **recommend installing Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20203-lts-recommended"></a><span data-ttu-id="5fbdc-106">Unity 2020.3 LTS (empfohlen)</span><span class="sxs-lookup"><span data-stu-id="5fbdc-106">Unity 2020.3 LTS (Recommended)</span></span>

<span data-ttu-id="5fbdc-107">Die derzeit empfohlene Unity-Konfiguration von Microsoft für HoloLens 2- und Windows Mixed Reality-Entwicklung ist **Unity 2020.3 LTS** mit dem neuesten Mixed Reality OpenXR-Plug-In.</span><span class="sxs-lookup"><span data-stu-id="5fbdc-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5fbdc-108">Unity 2020 unterstützt holoLens (1. Generation) nicht.</span><span class="sxs-lookup"><span data-stu-id="5fbdc-108">Unity 2020 does not support targeting HoloLens (1st gen).</span></span> <span data-ttu-id="5fbdc-109">Diese Headsets werden in **[Unity 2019 LTS](#unity-20194-lts)** mit integriertem Legacy-XR für den gesamten Lebenszyklus von Unity 2019 LTS bis Mitte 2022 weiterhin unterstützt.</span><span class="sxs-lookup"><span data-stu-id="5fbdc-109">These headsets remain supported in **[Unity 2019 LTS](#unity-20194-lts)** with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

<span data-ttu-id="5fbdc-110">Das Mixed Reality OpenXR-Plug-In unterstützt AR Foundation 4.0 vollständig und stellt ARPlaneManager- und ARRaycastManager-Implementierungen zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="5fbdc-110">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="5fbdc-111">Auf diese Weise können Sie Treffertestcode schreiben, der sich dann über HoloLens 2 und ARCore/ARKit-Smartphones und -Tablets erstreckt.</span><span class="sxs-lookup"><span data-stu-id="5fbdc-111">This enables you to write hit-testing code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

<span data-ttu-id="5fbdc-112">Der beste Weg, um Unity zu installieren und zu verwalten, ist über <a href="https://unity3d.com/get-unity/download" target="_blank">Unity Hub</a>.</span><span class="sxs-lookup"><span data-stu-id="5fbdc-112">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">Unity Hub</a>.</span></span> <span data-ttu-id="5fbdc-113">Wenn sie installiert ist, öffnen Sie Unity Hub:</span><span class="sxs-lookup"><span data-stu-id="5fbdc-113">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="5fbdc-114">Wählen Sie die **Registerkarte Installs (Installationen)** und dann **ADD (HINZUFÜGEN) aus.**</span><span class="sxs-lookup"><span data-stu-id="5fbdc-114">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="5fbdc-115">Wählen Sie Unity 2020.3 LTS aus, und klicken Sie auf **Weiter.**</span><span class="sxs-lookup"><span data-stu-id="5fbdc-115">Select Unity 2020.3 LTS and click **Next**</span></span>

![Neue Version des Unity-Hubs](images/unity-hub-img-01.png)

3. <span data-ttu-id="5fbdc-117">Überprüfen Sie die folgenden Komponenten unter **"Plattformen".**</span><span class="sxs-lookup"><span data-stu-id="5fbdc-117">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="5fbdc-118">**Buildunterstützung für Universelle Windows-Plattform**</span><span class="sxs-lookup"><span data-stu-id="5fbdc-118">**Universal Windows Platform Build Support**</span></span>
    * <span data-ttu-id="5fbdc-119">**Windows-Buildunterstützung (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="5fbdc-119">**Windows Build Support (IL2CPP)**</span></span>

![Unity: Option „Buildunterstützung für Universelle Windows-Plattform“](../images/Unity_Install_Option_UWP.png)

4. <span data-ttu-id="5fbdc-121">Wenn Sie Unity ohne diese Optionen installiert haben, können Sie diese über das Menü **"Module hinzufügen"** im Unity-Hub hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="5fbdc-121">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Unity: Option „Windows-Buildunterstützung“](../images/Unity_Install_Option_UWP2.png)

> [!div class="nextstepaction"]
> [<span data-ttu-id="5fbdc-123">Verwenden des OpenXR-Plug-Ins</span><span class="sxs-lookup"><span data-stu-id="5fbdc-123">Using the OpenXR plugin</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=openxr)

> [!NOTE]
> <span data-ttu-id="5fbdc-124">Es wird zwar empfohlen, OpenXR für alle neuen Projekte zu verwenden, Unity 2020.3 LTS unterstützt jedoch auch das **[Windows XR-Plug-In](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr)**.</span><span class="sxs-lookup"><span data-stu-id="5fbdc-124">While we recommend using OpenXR for all new projects, Unity 2020.3 LTS also supports the **[Windows XR plugin](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr)**.</span></span> <span data-ttu-id="5fbdc-125">Bekannte Probleme, die sich auf die Hologrammstabilität und andere Features auf HoloLens 2 auswirken:</span><span class="sxs-lookup"><span data-stu-id="5fbdc-125">Known issues that affect hologram stability and other features on HoloLens 2 include:</span></span>
>
> * <span data-ttu-id="5fbdc-126">Holographic App-Remotinganwendungen, die Universelle Windows-Plattform Buildziel verwenden, funktionieren nicht.</span><span class="sxs-lookup"><span data-stu-id="5fbdc-126">Holographic app remoting applications using the Universal Windows Platform build target are not working.</span></span>
> * <span data-ttu-id="5fbdc-127">Das Unity-Grafikaufträgesystem ist standardmäßig aktiviert, obwohl es nicht mit HoloLens-Projekten kompatibel ist.</span><span class="sxs-lookup"><span data-stu-id="5fbdc-127">The Unity graphics jobs system is defaulted on, even though it is not compatible with HoloLens projects.</span></span>

## <a name="unity-20194-lts"></a><span data-ttu-id="5fbdc-128">Unity 2019.4 LTS</span><span class="sxs-lookup"><span data-stu-id="5fbdc-128">Unity 2019.4 LTS</span></span>

<span data-ttu-id="5fbdc-129">Wenn Sie Unity 2019 verwenden müssen, können Sie **Unity 2019 LTS mit integriertem Legacy-XR verwenden.**</span><span class="sxs-lookup"><span data-stu-id="5fbdc-129">If you need to use Unity 2019, you can use **Unity 2019 LTS with Legacy Built-in XR**.</span></span> <span data-ttu-id="5fbdc-130">Klicken Sie hier, um mit der älteren integrierten XR in Unity 2019.4 LTS zu beginnen:</span><span class="sxs-lookup"><span data-stu-id="5fbdc-130">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5fbdc-131">Einrichten von legacy-integriertem XR</span><span class="sxs-lookup"><span data-stu-id="5fbdc-131">Set up Legacy Built-in XR</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=legacy)

> [!NOTE]
> <span data-ttu-id="5fbdc-132">Unity hat die integrierte Legacy-XR-Unterstützung seit Unity 2019 als veraltet bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="5fbdc-132">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="5fbdc-133">Unity 2019 bietet zwar ein neues XR-Plug-In-Framework, Microsoft empfiehlt diesen Pfad in Unity 2019 jedoch aufgrund von Azure Spatial Anchors-Inkompatibilitäten mit AR Foundation 2 nicht.</span><span class="sxs-lookup"><span data-stu-id="5fbdc-133">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="5fbdc-134">In Unity 2020 wird Azure Spatial Anchors im XR-Plug-In-Framework unterstützt.</span><span class="sxs-lookup"><span data-stu-id="5fbdc-134">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="5fbdc-135">Wenn Sie Apps für HoloLens (1. Generation) entwickeln, werden diese Headsets in Unity 2019 LTS mit integriertem Legacy-XR für den gesamten Lebenszyklus von Unity 2019 LTS bis Mitte 2022 weiterhin unterstützt.</span><span class="sxs-lookup"><span data-stu-id="5fbdc-135">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20211"></a><span data-ttu-id="5fbdc-136">Unity 2021.1</span><span class="sxs-lookup"><span data-stu-id="5fbdc-136">Unity 2021.1</span></span>

<span data-ttu-id="5fbdc-137">Wenn Sie frühe **Unity 2021.1-Builds** ausprobieren, sollten Sie mit dem **OpenXR-Plug-In** vorankommen, da das Windows XR-Plug-In dort veraltet ist.</span><span class="sxs-lookup"><span data-stu-id="5fbdc-137">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="5fbdc-138">Ab Unity 2021.2 ist das OpenXR-Plug-In der einzige Pfad für die Mixed Reality-Entwicklung, da das Windows XR-Plug-In nicht mehr unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="5fbdc-138">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="5fbdc-139">Unity 2018.4 LTS</span><span class="sxs-lookup"><span data-stu-id="5fbdc-139">Unity 2018.4 LTS</span></span>

<span data-ttu-id="5fbdc-140">Wenn Sie bereits über ein Projekt mit Unity 2018.4 LTS verfügen, wird Ihre Unity-Engine nach der Veröffentlichung zwei Jahre lang weiterhin unterstützt.</span><span class="sxs-lookup"><span data-stu-id="5fbdc-140">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="5fbdc-141">Unity 2018 LTS erreicht das Dienstende im Januar 2021.</span><span class="sxs-lookup"><span data-stu-id="5fbdc-141">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>
