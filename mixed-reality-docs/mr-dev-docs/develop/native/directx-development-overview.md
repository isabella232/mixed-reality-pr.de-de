---
title: 'Native Entwicklung: Übersicht'
description: Erstellen Sie eine DirectX-basierte gemischte Reality-Engine, indem Sie die Windows Mixed Reality-APIs direkt verwenden.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: DirectX, Holographic Rendering, Native, Native APP, WinRT, WinRT-APP, Plattform-APIs, benutzerdefiniertes Modul, Middleware, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 0d5e364fdb4faac73f28649f5c009823a74ac595
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679649"
---
# <a name="native-development-overview"></a><span data-ttu-id="4bdfc-104">Native Entwicklung: Übersicht</span><span class="sxs-lookup"><span data-stu-id="4bdfc-104">Native development overview</span></span>

![Natives Banner Logo](../images/native_logo_banner.png)

<span data-ttu-id="4bdfc-106">3D-Engines wie [Unity](../unity/unity-development-overview.md) oder [Unreal](../unreal/unreal-development-overview.md) sind nicht die einzigen Entwicklungspfade mit gemischter Realität, die Ihnen offen sind.</span><span class="sxs-lookup"><span data-stu-id="4bdfc-106">3D engines like [Unity](../unity/unity-development-overview.md) or [Unreal](../unreal/unreal-development-overview.md) aren't the only Mixed Reality development paths open to you.</span></span> <span data-ttu-id="4bdfc-107">Sie können auch gemischte Reality-Apps erstellen, indem Sie direkt in die Windows Mixed Reality-APIs mit DirectX 11 oder DirectX 12 codieren.</span><span class="sxs-lookup"><span data-stu-id="4bdfc-107">You can also create Mixed Reality apps by directly coding to the Windows Mixed Reality APIs with DirectX 11 or DirectX 12.</span></span> <span data-ttu-id="4bdfc-108">Wenn Sie die Plattform direkt nutzen, werden Sie im Grunde Ihre eigene Middleware oder Ihr eigenes Framework entwickeln.</span><span class="sxs-lookup"><span data-stu-id="4bdfc-108">By leveraging the platform directly, you're essentially building your own middleware or framework.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="4bdfc-109">Wenn Sie über ein vorhandenes WinRT-Projekt verfügen, das Sie verwalten möchten, besuchen Sie die [WinRT](creating-a-holographic-directx-project.md)-Haupt Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="4bdfc-109">If you have an existing WinRT project that you'd like to maintain, head over to our main [WinRT documentation](creating-a-holographic-directx-project.md).</span></span> 

## <a name="development-checkpoints"></a><span data-ttu-id="4bdfc-110">Prüfpunkte für die Entwicklung</span><span class="sxs-lookup"><span data-stu-id="4bdfc-110">Development checkpoints</span></span>

<span data-ttu-id="4bdfc-111">Nutzen Sie die folgenden Prüfpunkte, um Ihre Unity-Spiele und Anwendungen in eine Mixed Reality-Welt einzubringen.</span><span class="sxs-lookup"><span data-stu-id="4bdfc-111">Use the following checkpoints to bring your Unity games and applications into the world of mixed reality.</span></span>

### <a name="1-getting-started"></a><span data-ttu-id="4bdfc-112">1. Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="4bdfc-112">1. Getting started</span></span>

<span data-ttu-id="4bdfc-113">Windows Mixed Reality unterstützt [zwei Arten von apps](../../design/app-views.md):</span><span class="sxs-lookup"><span data-stu-id="4bdfc-113">Windows Mixed Reality supports [two kinds of apps](../../design/app-views.md):</span></span>
* <span data-ttu-id="4bdfc-114">**Anwendungen mit gemischter Realität** (UWP oder Win32), die die [holographicspace-API](getting-a-holographicspace.md) oder die [openxr-API](openxr.md) verwenden, um eine [immersive Ansicht](../../design/app-views.md) für den Benutzer zu erzeugen, der die Headset-Anzeige füllt</span><span class="sxs-lookup"><span data-stu-id="4bdfc-114">**Mixed-reality applications** (UWP or Win32) that use the [HolographicSpace API](getting-a-holographicspace.md) or [OpenXR API](openxr.md) to render an [immersive view](../../design/app-views.md) to the user that fills the headset display</span></span>
* <span data-ttu-id="4bdfc-115">**2D-apps** (UWP), die DirectX, XAML oder ein anderes Framework zum Rendering von [2D-Ansichten](../../design/app-views.md#2d-views) auf Slate in der Windows Mixed Reality-Startseite verwenden</span><span class="sxs-lookup"><span data-stu-id="4bdfc-115">**2D apps** (UWP) that use DirectX, XAML, or another framework to render [2D views](../../design/app-views.md#2d-views) on slates in the Windows Mixed Reality home</span></span>

<span data-ttu-id="4bdfc-116">Die Unterschiede zwischen der DirectX [-Entwicklung für 2D-Ansichten und immersive Ansichten](../../design/app-views.md) betreffen in erster Linie das holografische Rendering und räumliche Eingaben.</span><span class="sxs-lookup"><span data-stu-id="4bdfc-116">The differences between DirectX development for [2D views and immersive views](../../design/app-views.md) primarily concern holographic rendering and spatial input.</span></span> <span data-ttu-id="4bdfc-117">Die [iframeworkview](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) ihrer UWP-Anwendung oder das HWND ihrer Win32-Anwendung ist erforderlich und bleibt größtenteils unverändert.</span><span class="sxs-lookup"><span data-stu-id="4bdfc-117">Your UWP application's [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) or your Win32 application's HWND are required and remain largely the same.</span></span> <span data-ttu-id="4bdfc-118">Das gleiche gilt für die WinRT-APIs, die für Ihre app verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="4bdfc-118">The same is true for the WinRT APIs that are available to your app.</span></span> <span data-ttu-id="4bdfc-119">Sie müssen jedoch eine andere Teilmenge dieser APIs verwenden, um die Vorteile der Holographic-Features zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="4bdfc-119">But you must use a different subset of these APIs to take advantage of holographic features.</span></span> <span data-ttu-id="4bdfc-120">Beispielsweise werden die "vorhandenes SwapChain" und "Frame" vom System für holografische Anwendungen verwaltet, um eine von Pose vorhergesagte Frame Schleife zu aktivieren.</span><span class="sxs-lookup"><span data-stu-id="4bdfc-120">For example, the swapchain and frame present is managed by the system for holographic applications in order to enable a pose-predicted frame loop.</span></span>

[!INCLUDE[](../includes/native-getting-started.md)]

### <a name="2-core-building-blocks"></a><span data-ttu-id="4bdfc-121">2. Grundbausteine</span><span class="sxs-lookup"><span data-stu-id="4bdfc-121">2. Core building blocks</span></span>

<span data-ttu-id="4bdfc-122">Windows Mixed Reality-Anwendungen verwenden die folgenden APIs, um Umgebungen mit [gemischter Realität](../../discover/mixed-reality.md) für hololens und andere immersive Headsets zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="4bdfc-122">Windows Mixed Reality applications use the following APIs to build [mixed-reality](../../discover/mixed-reality.md) experiences for HoloLens and other immersive headsets:</span></span>

|  <span data-ttu-id="4bdfc-123">Feature</span><span class="sxs-lookup"><span data-stu-id="4bdfc-123">Feature</span></span>  |  <span data-ttu-id="4bdfc-124">Funktion</span><span class="sxs-lookup"><span data-stu-id="4bdfc-124">Capability</span></span>  |
| --- | --- |
| [<span data-ttu-id="4bdfc-125">Anvisieren</span><span class="sxs-lookup"><span data-stu-id="4bdfc-125">Gaze</span></span>](../../design/gaze-and-commit.md) | <span data-ttu-id="4bdfc-126">Ermöglichen Sie Benutzern das Anzielen von Hologrammen durch Anblicken</span><span class="sxs-lookup"><span data-stu-id="4bdfc-126">Let users target holograms with by looking at them</span></span> |
| [<span data-ttu-id="4bdfc-127">Geste</span><span class="sxs-lookup"><span data-stu-id="4bdfc-127">Gesture</span></span>](../../design/gaze-and-commit.md#composite-gestures) | <span data-ttu-id="4bdfc-128">Hinzufügen von räumlichen Aktionen zu ihren apps</span><span class="sxs-lookup"><span data-stu-id="4bdfc-128">Add spatial actions to your apps</span></span> |
| [<span data-ttu-id="4bdfc-129">Holographisches Rendern</span><span class="sxs-lookup"><span data-stu-id="4bdfc-129">Holographic rendering</span></span>](../platform-capabilities-and-apis/rendering.md) | <span data-ttu-id="4bdfc-130">Zeichnen Sie ein – Hologramm an einer exakten Stelle weltweit um Ihre Benutzer</span><span class="sxs-lookup"><span data-stu-id="4bdfc-130">Draw a hologram at a precise location in the world around your users</span></span> |
| [<span data-ttu-id="4bdfc-131">Bewegungs Controller</span><span class="sxs-lookup"><span data-stu-id="4bdfc-131">Motion controller</span></span>](../../design/motion-controllers.md) | <span data-ttu-id="4bdfc-132">Ermöglichen Sie Ihren Benutzern, Aktionen in ihren Umgebungen mit gemischter Realität auszuführen.</span><span class="sxs-lookup"><span data-stu-id="4bdfc-132">Let your users take action in your Mixed Reality environments</span></span> |
| [<span data-ttu-id="4bdfc-133">Räumliche Abbildung</span><span class="sxs-lookup"><span data-stu-id="4bdfc-133">Spatial mapping</span></span>](../../design/spatial-mapping.md) | <span data-ttu-id="4bdfc-134">Bilden Sie Ihren physischen Raum mit einem überlagerten virtuellen Gittermodell ab, um die Begrenzungen Ihrer Umgebung zu kennzeichnen</span><span class="sxs-lookup"><span data-stu-id="4bdfc-134">Map your physical space with a virtual mesh overlay to mark the boundaries of your environment</span></span> |
| [<span data-ttu-id="4bdfc-135">Voice</span><span class="sxs-lookup"><span data-stu-id="4bdfc-135">Voice</span></span>](../../design/voice-input.md) | <span data-ttu-id="4bdfc-136">Erfassen Sie gesprochene Schlüsselwörter, Ausdrücke und Diktate von Benutzern</span><span class="sxs-lookup"><span data-stu-id="4bdfc-136">Capture spoken keywords, phrases, and dictation from your users</span></span> |
 
> [!NOTE]
> <span data-ttu-id="4bdfc-137">In der openxr [Roadmap](openxr.md#roadmap) -Dokumentation finden Sie anstehende und in der Entwicklung stehende wichtige Features.</span><span class="sxs-lookup"><span data-stu-id="4bdfc-137">You can find upcoming and in-development core features in the OpenXR [roadmap](openxr.md#roadmap) documentation.</span></span>

### <a name="3-deploying-and-testing"></a><span data-ttu-id="4bdfc-138">3. bereitstellen und testen</span><span class="sxs-lookup"><span data-stu-id="4bdfc-138">3. Deploying and testing</span></span>

<span data-ttu-id="4bdfc-139">Sie können mit OpenXR auf einem immersiven HoloLens 2- oder Windows Mixed Reality-Headset auf dem Desktop entwickeln.</span><span class="sxs-lookup"><span data-stu-id="4bdfc-139">You can develop using OpenXR on a HoloLens 2 or Windows Mixed Reality immersive headset on the desktop.</span></span>  <span data-ttu-id="4bdfc-140">Wenn Sie keinen Zugriff auf ein Headset haben, können Sie stattdessen den [hololens 2-Emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md) oder den [Windows Mixed Reality-Simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) verwenden.</span><span class="sxs-lookup"><span data-stu-id="4bdfc-140">If you don't have access to a headset, you can use the [HoloLens 2 Emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md) or the [Windows Mixed Reality Simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) instead.</span></span>

## <a name="whats-next"></a><span data-ttu-id="4bdfc-141">Wie geht es weiter?</span><span class="sxs-lookup"><span data-stu-id="4bdfc-141">What's next?</span></span>

<span data-ttu-id="4bdfc-142">Die Arbeit eines Entwicklers ist nie getan, insbesondere beim Lernen eines neuen Tools oder SDKs.</span><span class="sxs-lookup"><span data-stu-id="4bdfc-142">A developers job is never done, especially when learning a new tool or SDK.</span></span> <span data-ttu-id="4bdfc-143">Die folgenden Abschnitte führen Sie in Gebiete, die jenseits des Materials auf Einstiegsniveau liegen, das Sie bereits durchgearbeitet haben, ergänzt um nützliche Ressourcen, wenn es einmal hakt.</span><span class="sxs-lookup"><span data-stu-id="4bdfc-143">The following sections can take you into areas beyond the beginner level material you've already completed, along with helpful resources if you get stuck.</span></span> <span data-ttu-id="4bdfc-144">Beachten Sie, dass diese Themen und Ressourcen keine bestimmte Reihenfolge aufweisen, tauchen Sie also ruhig ein!</span><span class="sxs-lookup"><span data-stu-id="4bdfc-144">Note that these topics and resources are not in any sequential order, so feel free to jump around and explore!</span></span>

### <a name="additional-resources"></a><span data-ttu-id="4bdfc-145">Zusätzliche Ressourcen</span><span class="sxs-lookup"><span data-stu-id="4bdfc-145">Additional resources</span></span>

<span data-ttu-id="4bdfc-146">Wenn Sie Ihr openxr-Spiel skalieren möchten, sehen Sie sich die folgenden Links an:</span><span class="sxs-lookup"><span data-stu-id="4bdfc-146">If you're looking to level up your OpenXR game, check out the links below:</span></span>

* [<span data-ttu-id="4bdfc-147">OpenXR – Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="4bdfc-147">OpenXR best practices</span></span>](openxr-best-practices.md)
* [<span data-ttu-id="4bdfc-148">OpenXR – Leistung</span><span class="sxs-lookup"><span data-stu-id="4bdfc-148">OpenXR performance</span></span>](openxr-performance.md)
* [<span data-ttu-id="4bdfc-149">OpenXR – Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="4bdfc-149">OpenXR troubleshooting</span></span>](openxr-troubleshooting.md)

## <a name="see-also"></a><span data-ttu-id="4bdfc-150">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="4bdfc-150">See also</span></span>
* [<span data-ttu-id="4bdfc-151">App-Modell</span><span class="sxs-lookup"><span data-stu-id="4bdfc-151">App model</span></span>](../../design/app-model.md)
* [<span data-ttu-id="4bdfc-152">App-Ansichten</span><span class="sxs-lookup"><span data-stu-id="4bdfc-152">App views</span></span>](../../design/app-views.md)
