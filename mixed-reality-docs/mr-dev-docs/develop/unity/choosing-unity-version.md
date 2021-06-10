---
title: Auswählen einer Unity-Version und eines XR-Plug-Ins
description: Bleiben Sie über die neuesten Unity- und XR-Plug-In-Empfehlungen für die HoloLens-Anwendungsentwicklung auf dem Laufenden.
author: hferrone
ms.author: v-hferrone
ms.date: 03/26/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Unity
ms.openlocfilehash: da171db41e508fe556d8645b23f12f6f437446a1
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/10/2021
ms.locfileid: "111908234"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="b0852-104">Auswählen einer Unity-Version und eines XR-Plug-Ins</span><span class="sxs-lookup"><span data-stu-id="b0852-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="b0852-105">Wir empfehlen derzeit die **Installation von Unity 2019.4 LTS und die Verwendung von Legacy-integriertem XR** für die Mixed Reality Entwicklung. Sie können aber auch Apps mit anderen Unity-Konfigurationen erstellen.</span><span class="sxs-lookup"><span data-stu-id="b0852-105">While we currently **recommend installing Unity 2019.4 LTS and using Legacy Built-in XR** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20194-lts-recommended"></a><span data-ttu-id="b0852-106">Unity 2019.4 LTS (empfohlen)</span><span class="sxs-lookup"><span data-stu-id="b0852-106">Unity 2019.4 LTS (Recommended)</span></span>

<span data-ttu-id="b0852-107">Die aktuelle empfohlene Unity-Konfiguration von Microsoft für HoloLens 2 und Windows Mixed Reality Entwicklung ist **Unity 2019.4 LTS mit legacy-integrierter XR-Unterstützung.**</span><span class="sxs-lookup"><span data-stu-id="b0852-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2019.4 LTS using Legacy Built-in XR** support.</span></span>

<span data-ttu-id="b0852-108">Die beste Möglichkeit zum Installieren und Verwalten von Unity ist <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>.</span><span class="sxs-lookup"><span data-stu-id="b0852-108">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>.</span></span> <span data-ttu-id="b0852-109">Öffnen Sie nach der Installation Unity Hub:</span><span class="sxs-lookup"><span data-stu-id="b0852-109">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="b0852-110">Wählen Sie die Registerkarte **Installationen** und dann **HINZUFÜGEN** aus.</span><span class="sxs-lookup"><span data-stu-id="b0852-110">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="b0852-111">Wählen Sie Unity 2019.4 LTS aus, und klicken Sie auf **Weiter.**</span><span class="sxs-lookup"><span data-stu-id="b0852-111">Select Unity 2019.4 LTS and click **Next**</span></span>

![Unity Hub in der neuen Version](images/unity-hub-img-01.png)

3. <span data-ttu-id="b0852-113">Überprüfen Sie die folgenden Komponenten unter **"Plattformen".**</span><span class="sxs-lookup"><span data-stu-id="b0852-113">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="b0852-114">**Buildunterstützung für Universelle Windows-Plattform**</span><span class="sxs-lookup"><span data-stu-id="b0852-114">**Universal Windows Platform Build Support**</span></span> 
    * <span data-ttu-id="b0852-115">**Windows-Buildunterstützung (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="b0852-115">**Windows Build Support (IL2CPP)**</span></span>

![Unity: Option „Buildunterstützung für Universelle Windows-Plattform“](../images/Unity_Install_Option_UWP.png)

4. <span data-ttu-id="b0852-117">Wenn Sie Unity ohne diese Optionen installiert haben, können Sie sie über das Menü **"Module hinzufügen"** in Unity Hub hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="b0852-117">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Unity: Option „Windows-Buildunterstützung“](../images/Unity_Install_Option_UWP2.png)

<span data-ttu-id="b0852-119">Klicken Sie hier, um mit dem älteren integrierten XR in Unity 2019.4 LTS zu beginnen:</span><span class="sxs-lookup"><span data-stu-id="b0852-119">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b0852-120">Einrichten von Legacy-integriertem XR</span><span class="sxs-lookup"><span data-stu-id="b0852-120">Set up Legacy Built-in XR</span></span>](legacy-xr-support.md)

> [!NOTE]
> <span data-ttu-id="b0852-121">Unity hat die legacy-integrierte XR-Unterstützung ab Unity 2019 als veraltet erklärt.</span><span class="sxs-lookup"><span data-stu-id="b0852-121">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="b0852-122">Während Unity 2019 ein neues XR-Plug-In-Framework bietet, empfiehlt Microsoft diesen Pfad in Unity 2019 aufgrund von Inkompatibilitäten von Azure Spatial Anchors mit AR Foundation 2 derzeit nicht.</span><span class="sxs-lookup"><span data-stu-id="b0852-122">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="b0852-123">In Unity 2020 wird Azure Spatial Anchors im XR-Plug-In-Framework unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b0852-123">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="b0852-124">Wenn Sie Apps für HoloLens (1. Generation) entwickeln, werden diese Headsets in Unity 2019 LTS mit legacy-integriertem XR für den gesamten Lebenszyklus von Unity 2019 LTS bis Mitte 2022 weiterhin unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b0852-124">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20203-lts"></a><span data-ttu-id="b0852-125">Unity 2020.3 LTS</span><span class="sxs-lookup"><span data-stu-id="b0852-125">Unity 2020.3 LTS</span></span> 

<span data-ttu-id="b0852-126">Wenn Sie **Unity 2020.3 LTS** verwenden, können Sie das **Windows XR-Plug-In** verwenden, um HoloLens 2 und Windows Mixed Reality Anwendungen zu entwickeln.</span><span class="sxs-lookup"><span data-stu-id="b0852-126">If you’re using **Unity 2020.3 LTS**, you can use the **Windows XR plugin** to develop HoloLens 2 and Windows Mixed Reality applications.</span></span>

<span data-ttu-id="b0852-127">Es gibt jedoch bekannte Probleme, die sich auf die Hologrammstabilität und andere Features auf HoloLens 2 auswirken:</span><span class="sxs-lookup"><span data-stu-id="b0852-127">However, there are known issues that affect hologram stability and other features on HoloLens 2:</span></span> 

* <span data-ttu-id="b0852-128">Holografische App-Remotinganwendungen, die das Universelle Windows-Plattform Buildziel verwenden, funktionieren nicht.</span><span class="sxs-lookup"><span data-stu-id="b0852-128">Holographic app remoting applications using the Universal Windows Platform build target are not working.</span></span>
* <span data-ttu-id="b0852-129">Das Unity-Grafikaufträgesystem ist standardmäßig aktiviert, obwohl es nicht mit HoloLens-Projekten kompatibel ist.</span><span class="sxs-lookup"><span data-stu-id="b0852-129">The Unity graphics jobs system is defaulted on, even though it is not compatible with HoloLens projects.</span></span>

<span data-ttu-id="b0852-130">Wenn Sie noch heute ein neues Projekt in Unity 2020 starten möchten, sollten Sie in den kommenden Monaten nach aktualisierten Unity-Builds und Windows XR-Plug-In-Builds suchen, bevor Sie Ihre App versenden.</span><span class="sxs-lookup"><span data-stu-id="b0852-130">If you choose to start a new project in Unity 2020 today, be sure to follow up over the coming months for updated Unity builds and Windows XR plugin builds before shipping your app.</span></span>  <span data-ttu-id="b0852-131">Dadurch wird sichergestellt, dass Ihre Benutzer die richtige Hologrammstabilität erhalten.</span><span class="sxs-lookup"><span data-stu-id="b0852-131">This will ensure that your users experience proper hologram stability.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b0852-132">Verwenden des Windows XR-Plug-Ins</span><span class="sxs-lookup"><span data-stu-id="b0852-132">Using the Windows XR plugin</span></span>](windows-xr-plugin.md)

### <a name="using-openxr"></a><span data-ttu-id="b0852-133">Verwenden von OpenXR</span><span class="sxs-lookup"><span data-stu-id="b0852-133">Using OpenXR</span></span>

<span data-ttu-id="b0852-134">Unity 2020.3 LTS unterstützt auch eine öffentliche Vorschauversion des Mixed Reality OpenXR-Plug-Ins. </span><span class="sxs-lookup"><span data-stu-id="b0852-134">Unity 2020.3 LTS also supports a public preview of the **Mixed Reality OpenXR** plugin.</span></span>

<span data-ttu-id="b0852-135">Das Mixed Reality OpenXR-Plug-In unterstützt AR Foundation 4.0 vollständig und stellt ARPlaneManager- und ARRaycastManager-Implementierungen bereit.</span><span class="sxs-lookup"><span data-stu-id="b0852-135">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="b0852-136">Dadurch können Sie einmal Treffertestcode schreiben, der sich dann über HoloLens 2 und ARCore/ARKit-Smartphones und -Tablets erstreckt.</span><span class="sxs-lookup"><span data-stu-id="b0852-136">This enables you to write hit-testing code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span> 

<span data-ttu-id="b0852-137">Später in diesem Jahr wird **Unity 2020.3 LTS mit dem OpenXR-Plug-In** zur empfohlenen Unity-Konfiguration, und zukünftige HoloLens 2 Features in Unity werden nur über dieses Plug-In verfügbar gemacht.</span><span class="sxs-lookup"><span data-stu-id="b0852-137">Later this year, **Unity 2020.3 LTS with the OpenXR plugin** will become the recommended Unity configuration, and future HoloLens 2 features in Unity will be exposed only through this plugin.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b0852-138">Verwenden des OpenXR-Plug-Ins</span><span class="sxs-lookup"><span data-stu-id="b0852-138">Using the OpenXR plugin</span></span>](openxr-getting-started.md)

## <a name="unity-20211"></a><span data-ttu-id="b0852-139">Unity 2021.1</span><span class="sxs-lookup"><span data-stu-id="b0852-139">Unity 2021.1</span></span>

<span data-ttu-id="b0852-140">Wenn Sie frühe **Unity 2021.1-Builds** ausprobieren, sollten Sie mit dem **OpenXR-Plug-In** fortschreiten, da das Windows XR-Plug-In dort veraltet ist.</span><span class="sxs-lookup"><span data-stu-id="b0852-140">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="b0852-141">Ab Unity 2021.2 ist das OpenXR-Plug-In der einzige Pfad für Mixed Reality Entwicklung, da das Windows XR-Plug-In nicht mehr unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="b0852-141">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="b0852-142">Unity 2018.4 LTS</span><span class="sxs-lookup"><span data-stu-id="b0852-142">Unity 2018.4 LTS</span></span>

<span data-ttu-id="b0852-143">Wenn Sie bereits über ein Projekt mit Unity 2018.4 LTS verfügen, wird Ihre Unity-Engine nach der Veröffentlichung 2 Jahre lang weiterhin unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b0852-143">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="b0852-144">Unity 2018 LTS wird im Spring 2021 das Ende des Diensts erreichen.</span><span class="sxs-lookup"><span data-stu-id="b0852-144">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>