---
title: Verwenden des Windows XR-Plug-ins
description: Erfahren Sie, wie Sie Ihre Unity-Projekte mit und ohne mrtk mithilfe von Windows-XR-Unterstützung einrichten.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, gemischte Realität, Entwicklung, Einstieg, neues Projekt, Windows Mixed Reality, UWP, XR, Leistung, Legacy, mrtk, Windows
ms.openlocfilehash: 24da4b5116b926cfd5eda12db6eedee2f9e85621
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938107"
---
# <a name="using-windows-xr-plugin"></a><span data-ttu-id="8f9de-104">Verwenden des Windows-</span><span class="sxs-lookup"><span data-stu-id="8f9de-104">Using Windows XR plugin</span></span>

<span data-ttu-id="8f9de-105">Für Entwickler, die auf Unity 2020 abzielen, ermöglicht das Windows-XR-Plug-in den Zugriff auf gemischte Reality-Features auf hololens 2-und Windows Mixed Reality-</span><span class="sxs-lookup"><span data-stu-id="8f9de-105">For developers targeting Unity 2020, the Windows XR plugin enables access to mixed reality features on HoloLens 2 and Windows Mixed Reality headsets.</span></span>  <span data-ttu-id="8f9de-106">Dieses Plug-in wird auch in Unity 2019 unterstützt, obwohl bei Verwendung dieses Plug-Ins für diese Version einige bekannte Inkompatibilitäten mit räumlichen Azure-Anker vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="8f9de-106">This plugin is also supported on Unity 2019, although there are some known incompatibilities with Azure Spatial Anchors when using this plugin on that version.</span></span>

<span data-ttu-id="8f9de-107">Obwohl Microsoft und die Community Open Source-Tools wie das [Mixed Reality Toolkit (mrtk)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) erstellt haben, das die WMR-Umgebung automatisch einrichten wird, möchten viele Entwickler ihre Erfahrungen von Grund auf neu erstellen.</span><span class="sxs-lookup"><span data-stu-id="8f9de-107">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>  <span data-ttu-id="8f9de-108">In der folgenden Dokumentation wird veranschaulicht, wie Sie ein Projekt für die Entwicklung mit gemischter Realität ordnungsgemäß einrichten, unabhängig davon, ob Sie mrtk verwenden oder nicht.</span><span class="sxs-lookup"><span data-stu-id="8f9de-108">The following documentation will demonstrate how to properly set up a project for Mixed Reality development whether you are using MRTK or not.</span></span>  <span data-ttu-id="8f9de-109">Die Einstellungen, die Sie ändern müssen, werden in zwei Kategorien unterteilt: Einstellungen pro Projekt und Einstellungen pro Szene.</span><span class="sxs-lookup"><span data-stu-id="8f9de-109">The settings you need to change are broken down into two categories: per-project settings and per-scene settings.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="8f9de-110">Einrichten Ihres Projekts mit mrtk</span><span class="sxs-lookup"><span data-stu-id="8f9de-110">Setting up your project with MRTK</span></span>

<span data-ttu-id="8f9de-111">MRTK für Unity bietet ein plattformübergreifendes Eingabesystem, Grundlagenkomponenten und gemeinsame Bausteine für räumliche Interaktionen.</span><span class="sxs-lookup"><span data-stu-id="8f9de-111">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="8f9de-112">MRTK, Version 2, soll die Anwendungsentwicklung für Microsoft HoloLens, für immersive Windows Mixed Reality-Headsets (VR) und für die OpenVR-Plattform beschleunigen.</span><span class="sxs-lookup"><span data-stu-id="8f9de-112">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="8f9de-113">Das Projekt ist darauf ausgerichtet, die Einstiegshürden zum Erstellen von Mixed Reality-Anwendungen zu verringern, und einen Beitrag für die Community auf diesem stetig wachsenden Gebiet zu leisten.</span><span class="sxs-lookup"><span data-stu-id="8f9de-113">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8f9de-114">Testen Sie unsere mrtk-Tutorials</span><span class="sxs-lookup"><span data-stu-id="8f9de-114">Try out our MRTK tutorials</span></span>](tutorials/mr-learning-base-01.md)

<span data-ttu-id="8f9de-115">Weitere Featuredetails finden Sie in [der Dokumentation zu mrtk](/windows/mixed-reality/mrtk-unity) .</span><span class="sxs-lookup"><span data-stu-id="8f9de-115">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="8f9de-116">Manuelles Setup ohne mrtk</span><span class="sxs-lookup"><span data-stu-id="8f9de-116">Manual setup without MRTK</span></span>

<span data-ttu-id="8f9de-117">Wenn Sie auf Desktop VR abzielen, empfiehlt es sich, die eigenständige PC-Plattform zu verwenden, die für ein neues Unity-Projekt standardmäßig ausgewählt ist:</span><span class="sxs-lookup"><span data-stu-id="8f9de-117">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit PC, Mac & eigenständige Plattform hervorgehoben](images/wmr-config-img-3.png)

<span data-ttu-id="8f9de-119">Wenn Sie hololens 2 als Ziel verwenden, müssen Sie zum universelle Windows-Plattform wechseln:</span><span class="sxs-lookup"><span data-stu-id="8f9de-119">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="8f9de-120">**Datei > Buildeinstellungen auswählen...**</span><span class="sxs-lookup"><span data-stu-id="8f9de-120">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="8f9de-121">Wählen Sie in der Platt Form Liste **universelle Windows-Plattform** aus, und wählen Sie **Plattform wechseln**</span><span class="sxs-lookup"><span data-stu-id="8f9de-121">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="8f9de-122">**Architektur** auf **Arm 64** festlegen</span><span class="sxs-lookup"><span data-stu-id="8f9de-122">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="8f9de-123">**Zielgerät** auf **hololens** festlegen</span><span class="sxs-lookup"><span data-stu-id="8f9de-123">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="8f9de-124">**Buildtyp** auf **D3D** festlegen</span><span class="sxs-lookup"><span data-stu-id="8f9de-124">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="8f9de-125">**UWP SDK** auf **Letztes installiert** festlegen</span><span class="sxs-lookup"><span data-stu-id="8f9de-125">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="8f9de-126">**Buildkonfiguration** auf **Release** festlegen, da beim Debuggen bekannte Leistungsprobleme auftreten</span><span class="sxs-lookup"><span data-stu-id="8f9de-126">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor öffnen mit hervorgehobener universelle Windows-Plattform](images/wmr-config-img-4.png)

<span data-ttu-id="8f9de-128">Nachdem Sie Ihre Plattform festgelegt haben, müssen Sie Unity mitteilen, dass Sie beim Exportieren eine [immersive Ansicht](../../design/app-views.md) anstelle einer 2D-Ansicht erstellen können:</span><span class="sxs-lookup"><span data-stu-id="8f9de-128">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="8f9de-129">Navigieren Sie im Unity-Editor zu **Edit > Project Settings** , und wählen Sie die **Verwaltung von XR Plugin** aus.</span><span class="sxs-lookup"><span data-stu-id="8f9de-129">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="8f9de-130">Select </span><span class="sxs-lookup"><span data-stu-id="8f9de-130">Select **Install XR Plugin Management**</span></span>

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor geöffnet, mit hervorgehobener Verwaltung von XR](images/wmr-config-img-5.png)

3. <span data-ttu-id="8f9de-132">Wählen Sie " **XR beim Start** und **Windows Mixed Reality** initialisieren" aus.</span><span class="sxs-lookup"><span data-stu-id="8f9de-132">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor geöffnet, mit hervorgehobener Verwaltung von XR](images/wmr-config-img-7.png)

4. <span data-ttu-id="8f9de-134">Erweitern Sie den Abschnitt **XR-Plug-in-Verwaltung** , und wählen Sie die Registerkarte **universelle Windows-Plattform**</span><span class="sxs-lookup"><span data-stu-id="8f9de-134">Expand the **XR Plug-in Management** section and select **Univeral Windows Platform Settings** tab</span></span>
5. <span data-ttu-id="8f9de-135">Wenn Sie Unity 2020 oder höher verwenden, sehen Sie die Optionen zum Überprüfen von **openxr** oder **Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="8f9de-135">If you're using Unity 2020 or later, you'll see the options to check **OpenXR** or **Windows Mixed Reality**.</span></span> 
    * <span data-ttu-id="8f9de-136">Sie können beide Laufzeitoptionen auswählen.</span><span class="sxs-lookup"><span data-stu-id="8f9de-136">You can choose either runtime.</span></span>  <span data-ttu-id="8f9de-137">Wenn Sie speziell für die hololens 2 oder den HP-Reverb-G2 entwickeln und das **openxr** testen möchten, wählen Sie das Feld openxr aus, und lesen Sie unser Handbuch zum [Verwenden des gemischten Reality openxr-Plug-Ins für Unity](openxr-getting-started.md) , um sich vor der Rückkehr zu diesem Tutorial ordnungsgemäß für diese Geräte einzurichten.</span><span class="sxs-lookup"><span data-stu-id="8f9de-137">If you're specifically developing for the HoloLens 2 or the HP Reverb G2 and decide to try the **OpenXR**, select the OpenXR box and review our guide to [Using the Mixed Reality OpenXR Plugin for Unity](openxr-getting-started.md) to get yourself set up correctly for these devices before returning to this tutorial</span></span>

> [!NOTE]
> <span data-ttu-id="8f9de-138">Ab Unity 2020 LTS geht Microsoft mit der Entwicklung mit openxr um.</span><span class="sxs-lookup"><span data-stu-id="8f9de-138">Starting in Unity 2020 LTS, Microsoft is embracing development with OpenXR.</span></span>  <span data-ttu-id="8f9de-139">Wenn wir zu diesem Pfad migrieren, wird das Windows-XR-Plug-in in Unity 2021,1 als veraltet markiert und 2021,2 entfernt, sodass openxr der einzige unterstützte Pfad ist.</span><span class="sxs-lookup"><span data-stu-id="8f9de-139">As we migrate to this path, in Unity 2021.1 the Windows XR plugin will be deprecated and removed in 2021.2 making OpenXR the only supported path.</span></span> <span data-ttu-id="8f9de-140">Weitere Informationen finden Sie unter [Verwenden des gemischten Reality openxr-Plug](openxr-getting-started.md)-ins.</span><span class="sxs-lookup"><span data-stu-id="8f9de-140">You can find more information in [Using the Mixed Reality OpenXR plugin](openxr-getting-started.md).</span></span>

6. <span data-ttu-id="8f9de-141">Wenn Sie das **Windows Mixed Reality** -Plug-in auswählen, aktivieren Sie alle Kontrollkästchen, und legen Sie den tiefen Übermittlungs **Modus** auf **Tiefe 16 Bit** fest.</span><span class="sxs-lookup"><span data-stu-id="8f9de-141">If you decide to choose the **Windows Mixed Reality** plugin, check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor geöffnet mit hervorgehobenem Windows Mixed Reality-Abschnitt](images/wmr-config-img-8.png)
