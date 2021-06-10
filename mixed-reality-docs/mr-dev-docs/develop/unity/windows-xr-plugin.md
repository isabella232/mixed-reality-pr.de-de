---
title: Verwenden des Windows XR-Plug-Ins
description: Erfahren Sie, wie Sie Ihre Unity-Projekte mit und ohne MRTK mithilfe der Windows XR-Unterstützung einrichten.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, Mixed Reality, Entwicklung, erste Schritte, neues Projekt, Windows Mixed Reality, UWP, XR, Leistung, Legacy, Mrtk, Fenster
ms.openlocfilehash: 44de6b418995b75d9e199f03922f89016b76c5cd
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743645"
---
# <a name="using-windows-xr-plugin"></a><span data-ttu-id="c1099-104">Verwenden des Windows XR-Plug-Ins</span><span class="sxs-lookup"><span data-stu-id="c1099-104">Using Windows XR plugin</span></span>

<span data-ttu-id="c1099-105">Für Entwickler, die Unity 2020 als Ziel verwenden, ermöglicht das Windows XR-Plug-In den Zugriff auf Mixed Reality-Features auf HoloLens 2 und Windows Mixed Reality Headsets.</span><span class="sxs-lookup"><span data-stu-id="c1099-105">For developers targeting Unity 2020, the Windows XR plugin enables access to mixed reality features on HoloLens 2 and Windows Mixed Reality headsets.</span></span>  <span data-ttu-id="c1099-106">Dieses Plug-In wird auch in Unity 2019 unterstützt, obwohl es einige bekannte Inkompatibilitäten mit Azure Spatial Anchors gibt, wenn dieses Plug-In für diese Version verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="c1099-106">This plugin is also supported on Unity 2019, although there are some known incompatibilities with Azure Spatial Anchors when using this plugin on that version.</span></span>

<span data-ttu-id="c1099-107">Microsoft und die Community haben OpenSource-Tools wie das [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) erstellt, mit denen die WMR-Umgebung automatisch eingerichtet wird, aber viele Entwickler möchten ihre Erfahrungen von Grund auf neu erstellen.</span><span class="sxs-lookup"><span data-stu-id="c1099-107">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>  <span data-ttu-id="c1099-108">In der folgenden Dokumentation wird veranschaulicht, wie Sie ein Projekt ordnungsgemäß für die entwicklung Mixed Reality, unabhängig davon, ob Sie MRTK verwenden oder nicht.</span><span class="sxs-lookup"><span data-stu-id="c1099-108">The following documentation will demonstrate how to properly set up a project for Mixed Reality development whether you are using MRTK or not.</span></span>  <span data-ttu-id="c1099-109">Die Einstellungen, die Sie ändern müssen, sind in zwei Kategorien unterteilt: Projektspezifische Einstellungen und Szenenspezifische Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="c1099-109">The settings you need to change are broken down into two categories: per-project settings and per-scene settings.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="c1099-110">Einrichten Ihres Projekts mit MRTK</span><span class="sxs-lookup"><span data-stu-id="c1099-110">Setting up your project with MRTK</span></span>

<span data-ttu-id="c1099-111">MRTK für Unity bietet ein plattformübergreifendes Eingabesystem, Grundlagenkomponenten und gemeinsame Bausteine für räumliche Interaktionen.</span><span class="sxs-lookup"><span data-stu-id="c1099-111">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="c1099-112">MRTK, Version 2, soll die Anwendungsentwicklung für Microsoft HoloLens, für immersive Windows Mixed Reality-Headsets (VR) und für die OpenVR-Plattform beschleunigen.</span><span class="sxs-lookup"><span data-stu-id="c1099-112">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="c1099-113">Das Projekt ist darauf ausgerichtet, die Einstiegshürden zum Erstellen von Mixed Reality-Anwendungen zu verringern, und einen Beitrag für die Community auf diesem stetig wachsenden Gebiet zu leisten.</span><span class="sxs-lookup"><span data-stu-id="c1099-113">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c1099-114">Probieren Sie unsere MRTK-Tutorials aus</span><span class="sxs-lookup"><span data-stu-id="c1099-114">Try out our MRTK tutorials</span></span>](./tutorials/mr-learning-base-02.md?tabs=winxr)

<span data-ttu-id="c1099-115">Weitere Details zu Features finden Sie in der [MRTK-Dokumentation](/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="c1099-115">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="c1099-116">Manuelle Einrichtung ohne MRTK</span><span class="sxs-lookup"><span data-stu-id="c1099-116">Manual setup without MRTK</span></span>

<span data-ttu-id="c1099-117">Wenn Sie Desktop VR als Ziel verwenden möchten, empfehlen wir die Verwendung der eigenständigen PC-Plattform, die standardmäßig für ein neues Unity-Projekt ausgewählt ist:</span><span class="sxs-lookup"><span data-stu-id="c1099-117">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit hervorgehobener eigenständiger &-Plattform](images/wmr-config-img-3.png)

<span data-ttu-id="c1099-119">Wenn Sie auf HoloLens 2 möchten, müssen Sie zum folgenden Universelle Windows-Plattform:</span><span class="sxs-lookup"><span data-stu-id="c1099-119">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="c1099-120">Wählen **Sie Datei > Buildeinstellungen... aus.**</span><span class="sxs-lookup"><span data-stu-id="c1099-120">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="c1099-121">Wählen **Universelle Windows-Plattform** in der Liste Plattform aus, und wählen Sie **Plattform wechseln aus.**</span><span class="sxs-lookup"><span data-stu-id="c1099-121">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="c1099-122">Legen Sie **Architektur** auf **ARM 64** fest</span><span class="sxs-lookup"><span data-stu-id="c1099-122">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="c1099-123">Legen Sie **Zielgerät** auf **HoloLens** fest</span><span class="sxs-lookup"><span data-stu-id="c1099-123">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="c1099-124">Legen Sie **Buildtyp** auf **D3D** fest</span><span class="sxs-lookup"><span data-stu-id="c1099-124">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="c1099-125">Legen Sie **UWP SDK** auf **Zuletzt installiert** fest</span><span class="sxs-lookup"><span data-stu-id="c1099-125">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="c1099-126">Legen Sie **Buildkonfiguration** auf **Release** fest, da beim Debuggen bekannte Leistungsprobleme auftreten.</span><span class="sxs-lookup"><span data-stu-id="c1099-126">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Screenshot des Fensters "Buildeinstellungen" im Unity-Editor mit hervorgehobener Universelle Windows-Plattform](images/wmr-config-img-4.png)

<span data-ttu-id="c1099-128">Nachdem Sie Ihre Plattform festlegen, müssen Sie [](../../design/app-views.md) Unity darüber informieren, dass beim Exportieren eine immersive Ansicht anstelle einer 2D-Ansicht erstellt werden soll:</span><span class="sxs-lookup"><span data-stu-id="c1099-128">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported:</span></span>

1. <span data-ttu-id="c1099-129">Navigieren Sie im Unity-Editor zu Bearbeiten **> Projekteinstellungen,** und wählen Sie **XR-Plug-In-Verwaltung aus.**</span><span class="sxs-lookup"><span data-stu-id="c1099-129">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="c1099-130">Wählen Sie **XR-Plug-In-Verwaltung installieren aus.**</span><span class="sxs-lookup"><span data-stu-id="c1099-130">Select **Install XR Plugin Management**</span></span>

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor mit hervorgehobener XR-Plug-In-Verwaltung](images/wmr-config-img-5.png)

3. <span data-ttu-id="c1099-132">Wählen **Sie XR beim Start initialisieren und Windows Mixed Reality** </span><span class="sxs-lookup"><span data-stu-id="c1099-132">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor mit hervorgehobener XR-Plug-In-Verwaltung](images/wmr-config-img-7.png)

4. <span data-ttu-id="c1099-134">Erweitern Sie den **Abschnitt XR-Plug-In-Verwaltung,** und wählen Sie die Registerkarte **"Einstellungen für die Windows-Plattform"** aus.</span><span class="sxs-lookup"><span data-stu-id="c1099-134">Expand the **XR Plug-in Management** section and select **Univeral Windows Platform Settings** tab</span></span>
5. <span data-ttu-id="c1099-135">Wenn Sie Unity 2020 oder höher verwenden, sehen Sie die Optionen zum Überprüfen von **OpenXR** **oder Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="c1099-135">If you're using Unity 2020 or later, you'll see the options to check **OpenXR** or **Windows Mixed Reality**.</span></span> 
    * <span data-ttu-id="c1099-136">Sie können eine der beiden Laufzeiten auswählen.</span><span class="sxs-lookup"><span data-stu-id="c1099-136">You can choose either runtime.</span></span>  <span data-ttu-id="c1099-137">Wenn Sie speziell für die HoloLens 2 oder HP Reverb G2 entwickeln und sich entschließen, **OpenXR** auszuprobieren, wählen Sie das Feld OpenXR aus, und sehen Sie sich unseren Leitfaden unter Verwenden des Mixed Reality OpenXR-Plug-Ins für [Unity](openxr-getting-started.md) an, um sich für diese Geräte richtig einrichten zu lassen, bevor Sie zu diesem Tutorial zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="c1099-137">If you're specifically developing for the HoloLens 2 or the HP Reverb G2 and decide to try the **OpenXR**, select the OpenXR box and review our guide to [Using the Mixed Reality OpenXR Plugin for Unity](openxr-getting-started.md) to get yourself set up correctly for these devices before returning to this tutorial</span></span>

> [!NOTE]
> <span data-ttu-id="c1099-138">Ab Unity 2020 LTS geht Microsoft von der Entwicklung mit OpenXR aus.</span><span class="sxs-lookup"><span data-stu-id="c1099-138">Starting in Unity 2020 LTS, Microsoft is embracing development with OpenXR.</span></span>  <span data-ttu-id="c1099-139">Bei der Migration zu diesem Pfad wird in Unity 2021.1 das Windows XR-Plug-In veraltet sein und in 2021.2 entfernt, wodurch OpenXR der einzige unterstützte Pfad ist.</span><span class="sxs-lookup"><span data-stu-id="c1099-139">As we migrate to this path, in Unity 2021.1 the Windows XR plugin will be deprecated and removed in 2021.2 making OpenXR the only supported path.</span></span> <span data-ttu-id="c1099-140">Weitere Informationen finden Sie unter [Verwenden des Mixed Reality OpenXR-Plug-Ins.](openxr-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="c1099-140">You can find more information in [Using the Mixed Reality OpenXR plugin](openxr-getting-started.md).</span></span>

6. <span data-ttu-id="c1099-141">Wenn Sie sich für das **Windows Mixed Reality-Plug-In** entscheiden, aktivieren Sie alle Kontrollkästchen, und legen Sie **tiefenübermittlungsmodus** auf Tiefe **16 Bit fest.**</span><span class="sxs-lookup"><span data-stu-id="c1099-141">If you decide to choose the **Windows Mixed Reality** plugin, check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![Screenshot des Fensters "Projekteinstellungen" im Unity-Editor mit hervorgehobener Windows Mixed Reality Abschnitt](images/wmr-config-img-8.png)