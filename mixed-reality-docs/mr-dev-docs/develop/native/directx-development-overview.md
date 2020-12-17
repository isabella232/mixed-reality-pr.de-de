---
title: 'Native Entwicklung: Übersicht'
description: Erstellen Sie eine DirectX-basierte gemischte Reality-Engine, indem Sie die Windows Mixed Reality-APIs direkt verwenden.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: DirectX, Holographic Rendering, Native, Native APP, WinRT, WinRT-APP, Plattform-APIs, benutzerdefiniertes Modul, Middleware, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 493715660ff8df79df25e09c82fe48b863053ed3
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613074"
---
# <a name="native-development-overview"></a><span data-ttu-id="2391a-104">Native Entwicklung: Übersicht</span><span class="sxs-lookup"><span data-stu-id="2391a-104">Native development overview</span></span>

![Natives Banner Logo](../images/native_logo_banner.png)

<span data-ttu-id="2391a-106">3D-Engines wie [Unity](../unity/unity-development-overview.md) oder [Unreal](../unreal/unreal-development-overview.md) sind nicht die einzigen Entwicklungspfade mit gemischter Realität, die Ihnen offen sind.</span><span class="sxs-lookup"><span data-stu-id="2391a-106">3D engines like [Unity](../unity/unity-development-overview.md) or [Unreal](../unreal/unreal-development-overview.md) aren't the only Mixed Reality development paths open to you.</span></span> <span data-ttu-id="2391a-107">Sie können auch gemischte Reality-apps mit den Windows Mixed Reality-APIs mit DirectX 11 oder DirectX 12 erstellen.</span><span class="sxs-lookup"><span data-stu-id="2391a-107">You can also create Mixed Reality apps using the Windows Mixed Reality APIs with DirectX 11 or DirectX 12.</span></span> <span data-ttu-id="2391a-108">Wenn Sie zur Platt Form Quelle navigieren, werden Sie im Grunde Ihre eigene Middleware oder Ihr eigenes Framework entwickeln.</span><span class="sxs-lookup"><span data-stu-id="2391a-108">By going to the platform source, you're essentially building your own middleware or framework.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="2391a-109">Wenn Sie über ein vorhandenes WinRT-Projekt verfügen, das Sie verwalten möchten, besuchen Sie die [WinRT](creating-a-holographic-directx-project.md)-Haupt Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="2391a-109">If you have an existing WinRT project that you'd like to maintain, head over to our main [WinRT documentation](creating-a-holographic-directx-project.md).</span></span> 

## <a name="development-checkpoints"></a><span data-ttu-id="2391a-110">Prüfpunkte für die Entwicklung</span><span class="sxs-lookup"><span data-stu-id="2391a-110">Development checkpoints</span></span>

<span data-ttu-id="2391a-111">Nutzen Sie die folgenden Prüfpunkte, um Ihre Unity-Spiele und Anwendungen in eine Mixed Reality-Welt einzubringen.</span><span class="sxs-lookup"><span data-stu-id="2391a-111">Use the following checkpoints to bring your Unity games and applications into the world of mixed reality.</span></span>

### <a name="1-getting-started"></a><span data-ttu-id="2391a-112">1. Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="2391a-112">1. Getting started</span></span>

<span data-ttu-id="2391a-113">Windows Mixed Reality unterstützt [zwei Arten von apps](../../design/app-views.md):</span><span class="sxs-lookup"><span data-stu-id="2391a-113">Windows Mixed Reality supports [two kinds of apps](../../design/app-views.md):</span></span>
* <span data-ttu-id="2391a-114">UWP-oder Win32- **Anwendungen mit gemischter Realität** , die die [holographicspace-API](getting-a-holographicspace.md) oder [openxr-API](openxr.md) verwenden, um eine [immersive Ansicht](../../design/app-views.md) zu erzeugen, die die Headset-Anzeige</span><span class="sxs-lookup"><span data-stu-id="2391a-114">UWP or Win32 **Mixed Reality applications** that use the [HolographicSpace API](getting-a-holographicspace.md) or [OpenXR API](openxr.md) to render an [immersive view](../../design/app-views.md) that fills the headset display</span></span>
* <span data-ttu-id="2391a-115">**2D-apps** (UWP), die DirectX, XAML oder ein anderes Framework zum Rendering von [2D-Ansichten](../../design/app-views.md#2d-views) auf Slate in der Windows Mixed Reality-Startseite verwenden</span><span class="sxs-lookup"><span data-stu-id="2391a-115">**2D apps** (UWP) that use DirectX, XAML, or another framework to render [2D views](../../design/app-views.md#2d-views) on slates in the Windows Mixed Reality home</span></span>

<span data-ttu-id="2391a-116">Die Unterschiede zwischen der DirectX [-Entwicklung für 2D-Ansichten und immersive Ansichten](../../design/app-views.md) betreffen in erster Linie das holografische Rendering und räumliche Eingaben.</span><span class="sxs-lookup"><span data-stu-id="2391a-116">The differences between DirectX development for [2D views and immersive views](../../design/app-views.md) primarily concern holographic rendering and spatial input.</span></span> <span data-ttu-id="2391a-117">Die [iframeworkview](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) ihrer UWP-Anwendung oder das HWND ihrer Win32-Anwendung ist erforderlich und bleibt größtenteils unverändert.</span><span class="sxs-lookup"><span data-stu-id="2391a-117">Your UWP application's [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) or your Win32 application's HWND are required and remain largely the same.</span></span> <span data-ttu-id="2391a-118">Das gleiche gilt für die WinRT-APIs, die für Ihre app verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="2391a-118">The same is true for the WinRT APIs that are available to your app.</span></span> <span data-ttu-id="2391a-119">Sie müssen jedoch eine andere Teilmenge dieser APIs verwenden, um die Vorteile der Holographic-Features zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="2391a-119">But you must use a different subset of these APIs to take advantage of holographic features.</span></span> <span data-ttu-id="2391a-120">Das System für Holographic-Anwendungen verwaltet z. b. die vorhandenes SwapChain und den Frame, die eine Pose-vorhergesagte Frame Schleife ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="2391a-120">For example, the system for holographic applications manages the swapchain and frame present to enable a pose-predicted frame loop.</span></span>

[!INCLUDE[](../includes/native-getting-started.md)]

### <a name="2-core-building-blocks"></a><span data-ttu-id="2391a-121">2. Grundbausteine</span><span class="sxs-lookup"><span data-stu-id="2391a-121">2. Core building blocks</span></span>

<span data-ttu-id="2391a-122">Windows Mixed Reality-Anwendungen verwenden die folgenden APIs, um Umgebungen mit [gemischter Realität](../../discover/mixed-reality.md) für hololens und andere immersive Headsets zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="2391a-122">Windows Mixed Reality applications use the following APIs to build [mixed-reality](../../discover/mixed-reality.md) experiences for HoloLens and other immersive headsets:</span></span>

|  <span data-ttu-id="2391a-123">Feature</span><span class="sxs-lookup"><span data-stu-id="2391a-123">Feature</span></span>  |  <span data-ttu-id="2391a-124">Funktion</span><span class="sxs-lookup"><span data-stu-id="2391a-124">Capability</span></span>  |
| --- | --- |
| [<span data-ttu-id="2391a-125">Anvisieren</span><span class="sxs-lookup"><span data-stu-id="2391a-125">Gaze</span></span>](../../design/gaze-and-commit.md) | <span data-ttu-id="2391a-126">Ermöglichen Sie Benutzern das Anzielen von Hologrammen durch Anblicken</span><span class="sxs-lookup"><span data-stu-id="2391a-126">Let users target holograms with by looking at them</span></span> |
| [<span data-ttu-id="2391a-127">Geste</span><span class="sxs-lookup"><span data-stu-id="2391a-127">Gesture</span></span>](../../design/gaze-and-commit.md#composite-gestures) | <span data-ttu-id="2391a-128">Hinzufügen von räumlichen Aktionen zu ihren apps</span><span class="sxs-lookup"><span data-stu-id="2391a-128">Add spatial actions to your apps</span></span> |
| [<span data-ttu-id="2391a-129">Holographisches Rendern</span><span class="sxs-lookup"><span data-stu-id="2391a-129">Holographic rendering</span></span>](../platform-capabilities-and-apis/rendering.md) | <span data-ttu-id="2391a-130">Zeichnen Sie ein – Hologramm an einer exakten Stelle weltweit um Ihre Benutzer</span><span class="sxs-lookup"><span data-stu-id="2391a-130">Draw a hologram at a precise location in the world around your users</span></span> |
| [<span data-ttu-id="2391a-131">Bewegungs Controller</span><span class="sxs-lookup"><span data-stu-id="2391a-131">Motion controller</span></span>](../../design/motion-controllers.md) | <span data-ttu-id="2391a-132">Ermöglichen Sie Ihren Benutzern, Aktionen in ihren Umgebungen mit gemischter Realität auszuführen.</span><span class="sxs-lookup"><span data-stu-id="2391a-132">Let your users take action in your Mixed Reality environments</span></span> |
| [<span data-ttu-id="2391a-133">Räumliche Abbildung</span><span class="sxs-lookup"><span data-stu-id="2391a-133">Spatial mapping</span></span>](../../design/spatial-mapping.md) | <span data-ttu-id="2391a-134">Bilden Sie Ihren physischen Raum mit einem überlagerten virtuellen Gittermodell ab, um die Begrenzungen Ihrer Umgebung zu kennzeichnen</span><span class="sxs-lookup"><span data-stu-id="2391a-134">Map your physical space with a virtual mesh overlay to mark the boundaries of your environment</span></span> |
| [<span data-ttu-id="2391a-135">Voice</span><span class="sxs-lookup"><span data-stu-id="2391a-135">Voice</span></span>](../../design/voice-input.md) | <span data-ttu-id="2391a-136">Erfassen Sie gesprochene Schlüsselwörter, Ausdrücke und Diktate von Benutzern</span><span class="sxs-lookup"><span data-stu-id="2391a-136">Capture spoken keywords, phrases, and dictation from your users</span></span> |
 
> [!NOTE]
> <span data-ttu-id="2391a-137">In der openxr [Roadmap](openxr.md#roadmap) -Dokumentation finden Sie anstehende und in der Entwicklung stehende wichtige Features.</span><span class="sxs-lookup"><span data-stu-id="2391a-137">You can find upcoming and in-development core features in the OpenXR [roadmap](openxr.md#roadmap) documentation.</span></span>

### <a name="3-deploying-and-testing"></a><span data-ttu-id="2391a-138">3. bereitstellen und testen</span><span class="sxs-lookup"><span data-stu-id="2391a-138">3. Deploying and testing</span></span>

<span data-ttu-id="2391a-139">Sie können auf einem Desktop mit openxr auf einem hololens 2-oder Windows Mixed Reality-immersiven Headset entwickeln.</span><span class="sxs-lookup"><span data-stu-id="2391a-139">You can develop on a desktop using OpenXR on a HoloLens 2 or Windows Mixed Reality immersive headset.</span></span>  <span data-ttu-id="2391a-140">Wenn Sie keinen Zugriff auf ein Headset haben, können Sie stattdessen den [hololens 2-Emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md) oder den [Windows Mixed Reality-Simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) verwenden.</span><span class="sxs-lookup"><span data-stu-id="2391a-140">If you don't have access to a headset, you can use the [HoloLens 2 Emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md) or the [Windows Mixed Reality Simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) instead.</span></span>

## <a name="whats-next"></a><span data-ttu-id="2391a-141">Wie geht es weiter?</span><span class="sxs-lookup"><span data-stu-id="2391a-141">What's next?</span></span>

<span data-ttu-id="2391a-142">Die Arbeit eines Entwicklers ist nie getan, insbesondere nicht beim Lernen eines neuen Tools oder SDKs.</span><span class="sxs-lookup"><span data-stu-id="2391a-142">A developer's job is never done, especially when learning a new tool or SDK.</span></span> <span data-ttu-id="2391a-143">In den folgenden Abschnitten gelangen Sie zu Bereichen, die über das von Ihnen bereits abgeschlossene Material für Einsteiger hinausgehen.</span><span class="sxs-lookup"><span data-stu-id="2391a-143">The following sections can take you into areas beyond the beginner level material you've already completed.</span></span> <span data-ttu-id="2391a-144">Diese Themen und Ressourcen befinden sich nicht in sequenzieller Reihenfolge</span><span class="sxs-lookup"><span data-stu-id="2391a-144">These topics and resources aren't in any sequential order, so feel free to jump around and explore!</span></span>

### <a name="additional-resources"></a><span data-ttu-id="2391a-145">Zusätzliche Ressourcen</span><span class="sxs-lookup"><span data-stu-id="2391a-145">Additional resources</span></span>

<span data-ttu-id="2391a-146">Wenn Sie Ihr openxr-Spiel skalieren möchten, sehen Sie sich die folgenden Links an:</span><span class="sxs-lookup"><span data-stu-id="2391a-146">If you're looking to level up your OpenXR game, check out the links below:</span></span>

* [<span data-ttu-id="2391a-147">OpenXR – Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="2391a-147">OpenXR best practices</span></span>](openxr-best-practices.md)
* [<span data-ttu-id="2391a-148">OpenXR – Leistung</span><span class="sxs-lookup"><span data-stu-id="2391a-148">OpenXR performance</span></span>](openxr-performance.md)
* [<span data-ttu-id="2391a-149">OpenXR – Problembehandlung</span><span class="sxs-lookup"><span data-stu-id="2391a-149">OpenXR troubleshooting</span></span>](openxr-troubleshooting.md)

## <a name="see-also"></a><span data-ttu-id="2391a-150">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="2391a-150">See also</span></span>
* [<span data-ttu-id="2391a-151">App-Modell</span><span class="sxs-lookup"><span data-stu-id="2391a-151">App model</span></span>](../../design/app-model.md)
* [<span data-ttu-id="2391a-152">App-Ansichten</span><span class="sxs-lookup"><span data-stu-id="2391a-152">App views</span></span>](../../design/app-views.md)
