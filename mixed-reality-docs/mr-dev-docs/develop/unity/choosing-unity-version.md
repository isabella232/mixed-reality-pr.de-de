---
title: Auswählen einer Unity-Version und eines XR-Plug-ins
description: Bleiben Sie auf dem neuesten Stand mit den neuesten Empfehlungen für Unity und XR-Plug-Ins für die hololens-Anwendungsentwicklung.
author: hferrone
ms.author: v-hferrone
ms.date: 03/26/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-Unity, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Unity
ms.openlocfilehash: b8f5f0131da811393ee053541e0c2fa0c735472e
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938140"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="cfb32-104">Auswählen einer Unity-Version und eines XR-Plug-ins</span><span class="sxs-lookup"><span data-stu-id="cfb32-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="cfb32-105">Wir empfehlen zurzeit die **Installation von Unity 2019,4 LTS und die Verwendung von Legacy-integrierten XR** für die Entwicklung mit gemischter Realität. Außerdem können Sie Apps mit anderen Unity-Konfigurationen erstellen.</span><span class="sxs-lookup"><span data-stu-id="cfb32-105">While we currently **recommend installing Unity 2019.4 LTS and using Legacy Built-in XR** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20194-lts-recommended"></a><span data-ttu-id="cfb32-106">Unity 2019,4 LTS (empfohlen)</span><span class="sxs-lookup"><span data-stu-id="cfb32-106">Unity 2019.4 LTS (Recommended)</span></span>

<span data-ttu-id="cfb32-107">Die zurzeit Empfohlene Unity-Konfiguration von Microsoft für hololens 2 und die Windows Mixed Reality-Entwicklung ist **Unity 2019,4 LTS mit der integrierten** Unterstützung von XR.</span><span class="sxs-lookup"><span data-stu-id="cfb32-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2019.4 LTS using Legacy Built-in XR** support.</span></span>

<span data-ttu-id="cfb32-108">Die beste Möglichkeit zum Installieren und Verwalten von Unity besteht im <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity-Hub]</a>.</span><span class="sxs-lookup"><span data-stu-id="cfb32-108">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>.</span></span> <span data-ttu-id="cfb32-109">Öffnen Sie nach der Installation den Unity-Hub:</span><span class="sxs-lookup"><span data-stu-id="cfb32-109">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="cfb32-110">Wählen Sie die Registerkarte **Installationen** und dann **Hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="cfb32-110">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="cfb32-111">Wählen Sie Unity 2019,4 LTS aus, und klicken Sie auf **weiter**</span><span class="sxs-lookup"><span data-stu-id="cfb32-111">Select Unity 2019.4 LTS and click **Next**</span></span>

![Neue Version des Unity-Hubs 2010-32](images/unity-hub-img-01.png)

3. <span data-ttu-id="cfb32-113">Überprüfen Sie die folgenden Komponenten unter **"Plattformen"**</span><span class="sxs-lookup"><span data-stu-id="cfb32-113">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="cfb32-114">**Universelle Windows-Plattform Build-Unterstützung**</span><span class="sxs-lookup"><span data-stu-id="cfb32-114">**Universal Windows Platform Build Support**</span></span> 
    * <span data-ttu-id="cfb32-115">**Unterstützung für Windows-Builds (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="cfb32-115">**Windows Build Support (IL2CPP)**</span></span>

![Unity-universelle Windows-Plattform Build-Unterstützungs Option](../images/Unity_Install_Option_UWP.png)

4. <span data-ttu-id="cfb32-117">Wenn Sie Unity ohne diese Optionen installiert haben, können Sie Sie über das Menü **"Module hinzufügen"** im Unity-Hub hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="cfb32-117">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Unity-Windows-Buildunterstützung](../images/Unity_Install_Option_UWP2.png)

<span data-ttu-id="cfb32-119">Klicken Sie hier, um mit der integrierten Version XR in Unity 2019,4 LTS zu beginnen:</span><span class="sxs-lookup"><span data-stu-id="cfb32-119">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cfb32-120">Einrichten von Legacy-integrierter XR</span><span class="sxs-lookup"><span data-stu-id="cfb32-120">Set up Legacy Built-in XR</span></span>](legacy-xr-support.md)

> [!NOTE]
> <span data-ttu-id="cfb32-121">Unity hat seine ältere integrierte XR-Unterstützung seit Unity 2019 als veraltet markiert.</span><span class="sxs-lookup"><span data-stu-id="cfb32-121">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="cfb32-122">Während Unity 2019 ein neues XR-Plug-in-Framework bietet, wird dieser Pfad von Microsoft aufgrund von Inkompatibilitäten in Azure Spatial-verankert mit AR Foundation 2 derzeit nicht in Unity 2019 empfohlen.</span><span class="sxs-lookup"><span data-stu-id="cfb32-122">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="cfb32-123">In Unity 2020 wird Azure Spatial Anchor im XR-Plug-in-Framework unterstützt.</span><span class="sxs-lookup"><span data-stu-id="cfb32-123">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="cfb32-124">Wenn Sie Apps für hololens (1. Generation) entwickeln, werden diese Headsets in Unity 2019 LTS mit Legacy-integrierter XR für den vollständigen Lebenszyklus von Unity 2019 LTS bis Mitte 2022 unterstützt.</span><span class="sxs-lookup"><span data-stu-id="cfb32-124">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20203-lts"></a><span data-ttu-id="cfb32-125">Unity 2020,3 LTS</span><span class="sxs-lookup"><span data-stu-id="cfb32-125">Unity 2020.3 LTS</span></span> 

<span data-ttu-id="cfb32-126">Wenn Sie **Unity 2020,3 LTS** verwenden, können Sie das Windows- **XR-Plug** -in verwenden, um hololens 2-und Windows Mixed Reality-Anwendungen zu entwickeln.</span><span class="sxs-lookup"><span data-stu-id="cfb32-126">If you’re using **Unity 2020.3 LTS**, you can use the **Windows XR plugin** to develop HoloLens 2 and Windows Mixed Reality applications.</span></span>

<span data-ttu-id="cfb32-127">Es gibt jedoch bekannte Probleme, die die – Hologramm-Stabilität und andere Features auf hololens 2 beeinflussen:</span><span class="sxs-lookup"><span data-stu-id="cfb32-127">However, there are known issues that affect hologram stability and other features on HoloLens 2:</span></span> 

* <span data-ttu-id="cfb32-128">Die Tiefe Puffer Übermittlung wurde in aktuellen Unity 2020-Builds zurückgekehrt, was zu einer schwerwiegenden – Hologramm-Instabilität führt.</span><span class="sxs-lookup"><span data-stu-id="cfb32-128">Depth buffer submission has regressed in recent Unity 2020 builds, which results in severe hologram instability.</span></span>
* <span data-ttu-id="cfb32-129">Holographic App-Remoting-Anwendungen, die das universelle Windows-Plattform Build-Ziel verwenden, funktionieren nicht.</span><span class="sxs-lookup"><span data-stu-id="cfb32-129">Holographic app remoting applications using the Universal Windows Platform build target are not working.</span></span>
* <span data-ttu-id="cfb32-130">Das Unity-Grafik Auftrags System ist standardmäßig eingeschaltet, obwohl es nicht mit hololens-Projekten kompatibel ist.</span><span class="sxs-lookup"><span data-stu-id="cfb32-130">The Unity graphics jobs system is defaulted on, even though it is not compatible with HoloLens projects.</span></span>

<span data-ttu-id="cfb32-131">Wenn Sie noch heute ein neues Projekt in Unity 2020 starten möchten, sollten Sie sich in den kommenden Monaten für aktualisierte Unity-Builds und Windows-XR-Plug-in-Builds vor dem Versenden Ihrer APP informieren.</span><span class="sxs-lookup"><span data-stu-id="cfb32-131">If you choose to start a new project in Unity 2020 today, be sure to follow up over the coming months for updated Unity builds and Windows XR plugin builds before shipping your app.</span></span>  <span data-ttu-id="cfb32-132">Dadurch wird sichergestellt, dass Ihre Benutzer über die richtige – Hologramm-Stabilität verfügen.</span><span class="sxs-lookup"><span data-stu-id="cfb32-132">This will ensure that your users experience proper hologram stability.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cfb32-133">Verwenden des Windows XR-Plug-ins</span><span class="sxs-lookup"><span data-stu-id="cfb32-133">Using the Windows XR plugin</span></span>](windows-xr-plugin.md)

### <a name="using-openxr"></a><span data-ttu-id="cfb32-134">Verwenden von openxr</span><span class="sxs-lookup"><span data-stu-id="cfb32-134">Using OpenXR</span></span>

<span data-ttu-id="cfb32-135">Unity 2020,3 LTS unterstützt auch eine öffentliche Vorschau des **Mixed Reality openxr** -Plug-ins.</span><span class="sxs-lookup"><span data-stu-id="cfb32-135">Unity 2020.3 LTS also supports a public preview of the **Mixed Reality OpenXR** plugin.</span></span>

<span data-ttu-id="cfb32-136">Das Mixed Reality openxr-Plug-in unterstützt AR Foundation 4,0 vollständig und stellt die Implementierungen arplanemanager und arraycastmanager bereit.</span><span class="sxs-lookup"><span data-stu-id="cfb32-136">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="cfb32-137">Auf diese Weise können Sie Code für die Treffer Überprüfung schreiben, der dann die hololens 2-und Arcore-/Arkit-Telefone und-Tablets umfasst.</span><span class="sxs-lookup"><span data-stu-id="cfb32-137">This enables you to write hit-testing code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span> 

<span data-ttu-id="cfb32-138">Im weiteren Verlauf dieses Jahres wird **Unity 2020,3 LTS mit dem openxr-Plug-in** die empfohlene Unity-Konfiguration, und zukünftige hololens 2-Funktionen in Unity werden nur über dieses Plug-in verfügbar gemacht.</span><span class="sxs-lookup"><span data-stu-id="cfb32-138">Later this year, **Unity 2020.3 LTS with the OpenXR plugin** will become the recommended Unity configuration, and future HoloLens 2 features in Unity will be exposed only through this plugin.</span></span>  <span data-ttu-id="cfb32-139">Sie können das Projekt jetzt hier starten. Wenn Ihr Projekt jedoch auf hololens 2 ausgerichtet ist, stoßen Sie derzeit auf die Stabilität von Unity 2020 – Hologramm und andere Probleme, die oben aufgeführt sind.</span><span class="sxs-lookup"><span data-stu-id="cfb32-139">You can start your project here for now - however, if your project targets HoloLens 2, you will currently encounter the Unity 2020 hologram stability and other issues listed above.</span></span>  <span data-ttu-id="cfb32-140">Stellen Sie sicher, dass Sie sich in den kommenden Monaten für aktualisierte Unity-Builds und openxr-Plug-in-Builds ansehen, bevor Sie Ihre APP versenden</span><span class="sxs-lookup"><span data-stu-id="cfb32-140">Be sure to check back in the coming months for updated Unity builds and OpenXR plugin builds before shipping your app.</span></span>  <span data-ttu-id="cfb32-141">Dadurch wird sichergestellt, dass Ihre Benutzer über die richtige – Hologramm-Stabilität verfügen.</span><span class="sxs-lookup"><span data-stu-id="cfb32-141">This will ensure that your users experience proper hologram stability.</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="cfb32-142">Verwenden des openxr-Plug-ins</span><span class="sxs-lookup"><span data-stu-id="cfb32-142">Using the OpenXR plugin</span></span>](openxr-getting-started.md)

## <a name="unity-20211"></a><span data-ttu-id="cfb32-143">Unity 2021,1</span><span class="sxs-lookup"><span data-stu-id="cfb32-143">Unity 2021.1</span></span>

<span data-ttu-id="cfb32-144">Wenn Sie frühe **Unity 2021,1** -Builds ausprobieren, sollten Sie zum **openxr-Plug**-in wechseln, da das Windows-XR-Plug-in dort veraltet ist.</span><span class="sxs-lookup"><span data-stu-id="cfb32-144">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="cfb32-145">Ab Unity 2021,2 ist das openxr-Plug-in der einzige Pfad für die Entwicklung mit gemischter Realität, da das Windows-XR-Plug-in nicht mehr unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="cfb32-145">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="cfb32-146">Unity 2018,4 LTS</span><span class="sxs-lookup"><span data-stu-id="cfb32-146">Unity 2018.4 LTS</span></span>

<span data-ttu-id="cfb32-147">Wenn Sie bereits über ein Projekt verfügen, das Unity 2018,4 LTS verwendet, wird Ihre Unity-Engine nach der Veröffentlichung weiterhin 2 Jahre lang unterstützt.</span><span class="sxs-lookup"><span data-stu-id="cfb32-147">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="cfb32-148">Unity 2018 LTS erreicht das Dienst Ende im Frühjahr 2021.</span><span class="sxs-lookup"><span data-stu-id="cfb32-148">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>
