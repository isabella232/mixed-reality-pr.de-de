---
title: Auswählen einer Unity-Version und eines XR-Plug-Ins
description: Bleiben Sie über die neuesten Unity- und XR-Plug-In-Empfehlungen für die Entwicklung von HoloLens-Anwendungen auf dem laufenden.
author: hferrone
ms.author: v-hferrone
ms.date: 06/18/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Unity
ms.openlocfilehash: 452692b1be98459cc242833149b1cfd91f0f4d4a
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394416"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="3dc69-104">Auswählen einer Unity-Version und eines XR-Plug-Ins</span><span class="sxs-lookup"><span data-stu-id="3dc69-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="3dc69-105">Es wird derzeit empfohlen, **Unity 2019.4 LTS** zu installieren und ältere integrierte XR-Daten für die Mixed Reality-Entwicklung zu verwenden. Sie können aber auch Apps mit anderen Unity-Konfigurationen erstellen.</span><span class="sxs-lookup"><span data-stu-id="3dc69-105">While we currently **recommend installing Unity 2019.4 LTS and using Legacy Built-in XR** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20194-lts-recommended"></a><span data-ttu-id="3dc69-106">Unity 2019.4 LTS (empfohlen)</span><span class="sxs-lookup"><span data-stu-id="3dc69-106">Unity 2019.4 LTS (Recommended)</span></span>

<span data-ttu-id="3dc69-107">Die derzeit empfohlene Unity-Konfiguration von Microsoft für die HoloLens 2- und Windows Mixed Reality-Entwicklung ist **Unity 2019.4 LTS mit integrierter Legacy-XR-Unterstützung.**</span><span class="sxs-lookup"><span data-stu-id="3dc69-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2019.4 LTS using Legacy Built-in XR** support.</span></span>

<span data-ttu-id="3dc69-108">Die beste Möglichkeit zum Installieren und Verwalten von Unity ist der <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>.</span><span class="sxs-lookup"><span data-stu-id="3dc69-108">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>.</span></span> <span data-ttu-id="3dc69-109">Wenn sie installiert ist, öffnen Sie Unity Hub:</span><span class="sxs-lookup"><span data-stu-id="3dc69-109">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="3dc69-110">Wählen Sie die **Registerkarte Installs (Installationen)** und dann **ADD (HINZUFÜGEN) aus.**</span><span class="sxs-lookup"><span data-stu-id="3dc69-110">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="3dc69-111">Wählen Sie Unity 2019.4 LTS aus, und klicken Sie auf **Weiter.**</span><span class="sxs-lookup"><span data-stu-id="3dc69-111">Select Unity 2019.4 LTS and click **Next**</span></span>

![Neue Version des Unity-Hubs](images/unity-hub-img-2019.png)

3. <span data-ttu-id="3dc69-113">Überprüfen Sie die folgenden Komponenten unter **"Plattformen".**</span><span class="sxs-lookup"><span data-stu-id="3dc69-113">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="3dc69-114">**Buildunterstützung für Universelle Windows-Plattform**</span><span class="sxs-lookup"><span data-stu-id="3dc69-114">**Universal Windows Platform Build Support**</span></span> 
    * <span data-ttu-id="3dc69-115">**Windows-Buildunterstützung (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="3dc69-115">**Windows Build Support (IL2CPP)**</span></span>

![Unity: Option „Buildunterstützung für Universelle Windows-Plattform“](images/Unity_Install_Option_UWP_2019.png)

4. <span data-ttu-id="3dc69-117">Wenn Sie Unity ohne diese Optionen installiert haben, können Sie diese über das Menü **"Module hinzufügen"** in Unity Hub hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="3dc69-117">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Unity: Option „Windows-Buildunterstützung“](images/Unity_Install_Option_UWP2_2019.png)

<span data-ttu-id="3dc69-119">Klicken Sie hier, um mit der älteren integrierten XR in Unity 2019.4 LTS zu beginnen:</span><span class="sxs-lookup"><span data-stu-id="3dc69-119">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3dc69-120">Einrichten von legacy-integriertem XR</span><span class="sxs-lookup"><span data-stu-id="3dc69-120">Set up Legacy Built-in XR</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=legacy)

> [!NOTE]
> <span data-ttu-id="3dc69-121">Unity hat die integrierte Legacy-XR-Unterstützung ab Unity 2019 als veraltet bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="3dc69-121">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="3dc69-122">Unity 2019 bietet zwar ein neues XR-Plug-In-Framework, Microsoft empfiehlt diesen Pfad in Unity 2019 jedoch aufgrund von Azure Spatial Anchors-Inkompatibilitäten mit AR Foundation 2 nicht.</span><span class="sxs-lookup"><span data-stu-id="3dc69-122">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="3dc69-123">In Unity 2020 wird Azure Spatial Anchors im XR-Plug-In-Framework unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3dc69-123">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="3dc69-124">Wenn Sie Apps für HoloLens (1. Generation) entwickeln, werden diese Headsets in Unity 2019 LTS mit integriertem Legacy-XR für den gesamten Lebenszyklus von Unity 2019 LTS bis Mitte 2022 weiterhin unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3dc69-124">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20203-lts"></a><span data-ttu-id="3dc69-125">Unity 2020.3 LTS</span><span class="sxs-lookup"><span data-stu-id="3dc69-125">Unity 2020.3 LTS</span></span> 

<span data-ttu-id="3dc69-126">Wenn Sie **Unity 2020.3 LTS** verwenden, ist die aktuelle Empfehlung von Microsoft die neueste Version Mixed Reality **OpenXR-Plug-Ins.**</span><span class="sxs-lookup"><span data-stu-id="3dc69-126">If you’re using **Unity 2020.3 LTS**, Microsoft’s current recommendation is the latest **Mixed Reality OpenXR plugin**.</span></span> <span data-ttu-id="3dc69-127">Sie MÜSSEN Unity Patch Release 2020.3.8f1 oder höher verwenden, um bekannte Leistungsprobleme mit früheren 2020.3-Builds zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="3dc69-127">You MUST use Unity patch release 2020.3.8f1 or later to avoid known performance issues with earlier 2020.3 builds.</span></span>

<span data-ttu-id="3dc69-128">Das Mixed Reality OpenXR-Plug-In unterstützt AR Foundation 4.0 vollständig und stellt ARPlaneManager- und ARRaycastManager-Implementierungen zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="3dc69-128">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="3dc69-129">Auf diese Weise können Sie Treffertestcode schreiben, der sich dann über HoloLens 2 und ARCore/ARKit-Smartphones und -Tablets erstreckt.</span><span class="sxs-lookup"><span data-stu-id="3dc69-129">This enables you to write hit-testing code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

<span data-ttu-id="3dc69-130">Es gibt jedoch bekannte Probleme, die Unity 2020 LTS-Projekte betreffen:</span><span class="sxs-lookup"><span data-stu-id="3dc69-130">However, there are known issues that affect Unity 2020 LTS projects:</span></span>

* <span data-ttu-id="3dc69-131">Die Universal Rendering Pipeline (URP) 10.5.0 oder älter hat Leistungsbeend auf HoloLens 2 Geräten.</span><span class="sxs-lookup"><span data-stu-id="3dc69-131">The Universal Rendering Pipeline (URP) 10.5.0 or older has performance penalties on HoloLens 2 devices.</span></span>

<span data-ttu-id="3dc69-132">Wenn Sie sich entscheiden, noch heute ein neues Projekt in Unity 2020 zu starten, sollten Sie in den kommenden Wochen unbedingt nach den aktualisierten Unity-Builds und URP-Paketen suchen, bevor Sie Ihre App versenden.</span><span class="sxs-lookup"><span data-stu-id="3dc69-132">If you choose to start a new project in Unity 2020 today, be sure to follow up over the coming weeks for updated Unity builds and URP packages before shipping your app.</span></span>  <span data-ttu-id="3dc69-133">Dadurch wird sichergestellt, dass Ihre Benutzer die richtige Hologrammstabilität haben.</span><span class="sxs-lookup"><span data-stu-id="3dc69-133">This will ensure that your users experience proper hologram stability.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3dc69-134">Verwenden des OpenXR-Plug-Ins</span><span class="sxs-lookup"><span data-stu-id="3dc69-134">Using the OpenXR plugin</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=openxr)

## <a name="unity-20211"></a><span data-ttu-id="3dc69-135">Unity 2021.1</span><span class="sxs-lookup"><span data-stu-id="3dc69-135">Unity 2021.1</span></span>

<span data-ttu-id="3dc69-136">Wenn Sie frühe **Unity 2021.1-Builds** ausprobieren, sollten Sie mit dem **OpenXR-Plug-In** weiterkommen, da das Windows XR-Plug-In dort veraltet ist.</span><span class="sxs-lookup"><span data-stu-id="3dc69-136">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="3dc69-137">Ab Unity 2021.2 ist das OpenXR-Plug-In der einzige Pfad für die Mixed Reality-Entwicklung, da das Windows XR-Plug-In nicht mehr unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="3dc69-137">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="3dc69-138">Unity 2018.4 LTS</span><span class="sxs-lookup"><span data-stu-id="3dc69-138">Unity 2018.4 LTS</span></span>

<span data-ttu-id="3dc69-139">Wenn Sie bereits über ein Projekt mit Unity 2018.4 LTS verfügen, wird Ihre Unity-Engine nach der Veröffentlichung zwei Jahre lang weiterhin unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3dc69-139">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="3dc69-140">Unity 2018 LTS erreicht das Ende des Diensts im Januar 2021.</span><span class="sxs-lookup"><span data-stu-id="3dc69-140">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>