---
title: Verwenden des visuellen Profilers
description: Dokumentation zur Verwendung von Visual Profiler in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: c3238aed60f6bbf824c74c034ddf506f49f436c7
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121648"
---
# <a name="using-the-visual-profiler"></a><span data-ttu-id="c9aae-104">Verwenden des visuellen Profilers</span><span class="sxs-lookup"><span data-stu-id="c9aae-104">Using the visual profiler</span></span>

<span data-ttu-id="c9aae-105">VisualProfiler bietet eine einfach zu verwendende Anwendungsansicht der Leistung einer Mixed Reality-Anwendung.</span><span class="sxs-lookup"><span data-stu-id="c9aae-105">The VisualProfiler provides an easy to use, in-application view of a mixed reality application's performance.</span></span> <span data-ttu-id="c9aae-106">Der Profiler wird auf allen Plattformen des Mixed Reality Toolkits unterstützt, einschließlich:</span><span class="sxs-lookup"><span data-stu-id="c9aae-106">The profiler is supported on all Mixed Reality Toolkit platforms, including:</span></span>

- <span data-ttu-id="c9aae-107">Microsoft HoloLens (1. Generation)</span><span class="sxs-lookup"><span data-stu-id="c9aae-107">Microsoft HoloLens (1st gen)</span></span>
- <span data-ttu-id="c9aae-108">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="c9aae-108">Microsoft HoloLens 2</span></span>
- <span data-ttu-id="c9aae-109">Immersive Windows Mixed Reality-Headsets</span><span class="sxs-lookup"><span data-stu-id="c9aae-109">Windows Mixed Reality immersive headsets</span></span>
- <span data-ttu-id="c9aae-110">OpenVR</span><span class="sxs-lookup"><span data-stu-id="c9aae-110">OpenVR</span></span>

<span data-ttu-id="c9aae-111">Konzentrieren Sie sich beim Entwickeln einer Anwendung auf mehrere Teile der Szene, da der Visual Profiler Daten relativ zur aktuellen Ansicht anzeigt.</span><span class="sxs-lookup"><span data-stu-id="c9aae-111">While developing an application, focus on multiple parts of the scene as the Visual Profiler displays data relative to the current view.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c9aae-112">Konzentrieren Sie sich auf Teile der Szene mit komplexen Objekten, Partikeleffekten oder Aktivitäten.</span><span class="sxs-lookup"><span data-stu-id="c9aae-112">Focus attention on portions of the scene with complex objects, particle effects or activity.</span></span> <span data-ttu-id="c9aae-113">Diese und andere Faktoren tragen häufig zur Verringerung der Anwendungsleistung und zu einer weniger idealen Benutzererfahrung bei.</span><span class="sxs-lookup"><span data-stu-id="c9aae-113">These and other factors often contribute to reduction in application performance and a less than ideal user experience.</span></span>

## <a name="visual-profiler-interface"></a><span data-ttu-id="c9aae-114">Grafische Profilerschnittstelle</span><span class="sxs-lookup"><span data-stu-id="c9aae-114">Visual profiler interface</span></span>

![Visual Profiler-Schnittstelle](../images/diagnostics/VisualProfiler.png)

<span data-ttu-id="c9aae-116">Die Visual Profiler-Schnittstelle umfasst die folgenden Komponenten:</span><span class="sxs-lookup"><span data-stu-id="c9aae-116">The Visual Profiler interface includes the following components:</span></span>

- [<span data-ttu-id="c9aae-117">Bildfrequenz</span><span class="sxs-lookup"><span data-stu-id="c9aae-117">Frame Rate</span></span>](#frame-rate)
- [<span data-ttu-id="c9aae-118">Framezeit</span><span class="sxs-lookup"><span data-stu-id="c9aae-118">Frame Time</span></span>](#frame-time)
- [<span data-ttu-id="c9aae-119">Rahmendiagramm</span><span class="sxs-lookup"><span data-stu-id="c9aae-119">Frame Graph</span></span>](#frame-graph)
- [<span data-ttu-id="c9aae-120">Arbeitsspeicherauslastung</span><span class="sxs-lookup"><span data-stu-id="c9aae-120">Memory Utilization</span></span>](#memory-utilization)

### <a name="frame-rate"></a><span data-ttu-id="c9aae-121">Bildfrequenz</span><span class="sxs-lookup"><span data-stu-id="c9aae-121">Frame rate</span></span>

<span data-ttu-id="c9aae-122">In der oberen linken Ecke der Schnittstelle befindet sich die Bildfrequenz, gemessen in Frames pro Sekunde.</span><span class="sxs-lookup"><span data-stu-id="c9aae-122">In the upper-left corner of the interface is the frame rate, measured in frames per second.</span></span> <span data-ttu-id="c9aae-123">Für optimale Benutzerfreundlichkeit und Komfort sollte dieser Wert so hoch wie möglich sein.</span><span class="sxs-lookup"><span data-stu-id="c9aae-123">For the best user experience and comfort, this value should be as high as possible.</span></span>

<span data-ttu-id="c9aae-124">Die spezifische Plattform- und Hardwarekonfiguration spielt eine wichtige Rolle bei der maximal erreichbaren Bildfrequenz.</span><span class="sxs-lookup"><span data-stu-id="c9aae-124">The specific platform and hardware configuration will play a significant role in the maximum achievable frame rate.</span></span> <span data-ttu-id="c9aae-125">Einige allgemeine Zielwerte sind:</span><span class="sxs-lookup"><span data-stu-id="c9aae-125">Some common target values include:</span></span>

- <span data-ttu-id="c9aae-126">Microsoft HoloLens: 60</span><span class="sxs-lookup"><span data-stu-id="c9aae-126">Microsoft HoloLens: 60</span></span>
- <span data-ttu-id="c9aae-127">Windows Mixed Reality Ultra: 90</span><span class="sxs-lookup"><span data-stu-id="c9aae-127">Windows Mixed Reality Ultra: 90</span></span>

> [!NOTE]
> <span data-ttu-id="c9aae-128">Aufgrund der [Frameratendrosselung auf HoloLens,](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens)wenn mrC standardmäßig aktiv ist, blendet sich der visuelle Profiler selbst aus, während Videos und Fotos erfasst werden.</span><span class="sxs-lookup"><span data-stu-id="c9aae-128">Due to [frame rate throttling on HoloLens when default MRC is active](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens), the visual profiler hides itself while videos and photos are captured.</span></span> <span data-ttu-id="c9aae-129">Diese Einstellung kann im Diagnosesystemprofil überschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="c9aae-129">This setting can be overridden in the diagnostics system profile.</span></span>

### <a name="frame-time"></a><span data-ttu-id="c9aae-130">Framedauer</span><span class="sxs-lookup"><span data-stu-id="c9aae-130">Frame time</span></span>

<span data-ttu-id="c9aae-131">Rechts neben der Bildfrequenz befindet sich die Für die CPU ausgegebene Framezeit in Millisekunden.</span><span class="sxs-lookup"><span data-stu-id="c9aae-131">To the right of the frame rate is the frame time, in milliseconds, spent on the CPU.</span></span> <span data-ttu-id="c9aae-132">Um die zuvor erwähnten Zielframeraten zu erreichen, kann eine Anwendung die folgende Zeit pro Frame verbringen:</span><span class="sxs-lookup"><span data-stu-id="c9aae-132">To achieve the target frame rates mentioned previously, an application can spend the following amount of time per frame:</span></span>

- <span data-ttu-id="c9aae-133">60 Fps: 16,6 ms</span><span class="sxs-lookup"><span data-stu-id="c9aae-133">60 fps: 16.6 ms</span></span>
- <span data-ttu-id="c9aae-134">90 Fps: 11,1 ms</span><span class="sxs-lookup"><span data-stu-id="c9aae-134">90 fps: 11.1 ms</span></span>

<span data-ttu-id="c9aae-135">Die GPU-Zeit soll in einem zukünftigen Release hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="c9aae-135">GPU time is planned to be added in a future release.</span></span>

### <a name="frame-graph"></a><span data-ttu-id="c9aae-136">Framediagramm</span><span class="sxs-lookup"><span data-stu-id="c9aae-136">Frame graph</span></span>

<span data-ttu-id="c9aae-137">Das Framediagramm stellt eine grafische Darstellung des Verlaufs der Anwendungsrahmenrate dar.</span><span class="sxs-lookup"><span data-stu-id="c9aae-137">The frame graph provides a graphical display of the application frame rate history.</span></span>

![Visual Profiler – Diagramm für verpasste Frames](../images/diagnostics/VisualProfilerMissedFrames.png)

<span data-ttu-id="c9aae-139">Wenn Sie die Anwendung verwenden, suchen Sie nach verpassten Frames, die darauf hinweisen, dass die Anwendung die Zielbildrate nicht erreicht und möglicherweise Optimierungsarbeit benötigt.</span><span class="sxs-lookup"><span data-stu-id="c9aae-139">When using the application, look for missed frames which indicate that the application is not hitting its target frame rate and may need optimization work.</span></span>

### <a name="memory-utilization"></a><span data-ttu-id="c9aae-140">Arbeitsspeichernutzung</span><span class="sxs-lookup"><span data-stu-id="c9aae-140">Memory utilization</span></span>

<span data-ttu-id="c9aae-141">Die Anzeige der Speicherauslastung ermöglicht ein einfaches Verständnis der Auswirkungen der aktuellen Ansicht auf die Arbeitsspeichernutzung einer Anwendung.</span><span class="sxs-lookup"><span data-stu-id="c9aae-141">The memory utilization display allows for easy understanding of how the current view is impacting an application's memory consumption.</span></span>

![Visual Profiler-Speicherdiagramm](../images/diagnostics/VisualProfilerMemory.png)

<span data-ttu-id="c9aae-143">Wenn Sie die Anwendung verwenden, suchen Sie nach der Gesamtspeicherauslastung.</span><span class="sxs-lookup"><span data-stu-id="c9aae-143">When using the application, look for total memory usage.</span></span> <span data-ttu-id="c9aae-144">Zu den Schlüsselindikatoren zählen das Nähern des Arbeitsspeicherlimits und schnelle Änderungen bei der Nutzung.</span><span class="sxs-lookup"><span data-stu-id="c9aae-144">Key indicators include nearing the memory limit and rapid changes in usage.</span></span>

## <a name="customizing-the-visual-profiler"></a><span data-ttu-id="c9aae-145">Anpassen des visuellen Profilers</span><span class="sxs-lookup"><span data-stu-id="c9aae-145">Customizing the visual profiler</span></span>

<span data-ttu-id="c9aae-146">Die Darstellung und das Verhalten des Visual Profilers können über das Diagnosesystemprofil angepasst werden.</span><span class="sxs-lookup"><span data-stu-id="c9aae-146">The Visual Profiler's appearance and behavior are customizable via the diagnostics system profile.</span></span> <span data-ttu-id="c9aae-147">Weitere Informationen [finden Sie unter Konfigurieren](configuring-diagnostics.md) des Diagnosesystems.</span><span class="sxs-lookup"><span data-stu-id="c9aae-147">Please see [Configuring the Diagnostics System](configuring-diagnostics.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="c9aae-148">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="c9aae-148">See also</span></span>

- [<span data-ttu-id="c9aae-149">Diagnosesystem</span><span class="sxs-lookup"><span data-stu-id="c9aae-149">Diagnostics System</span></span>](diagnostics-system-getting-started.md)
- [<span data-ttu-id="c9aae-150">Konfigurieren des Diagnosesystems</span><span class="sxs-lookup"><span data-stu-id="c9aae-150">Configuring the Diagnostics System</span></span>](configuring-diagnostics.md)