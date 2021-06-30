---
title: Konfigurieren der Diagnose
description: Dokumentation zum Konfigurieren der Diagnose im MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 211ee2ed06ba9b13bd90169bcc7ee50da4594034
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121798"
---
# <a name="configuring-the-diagnostics-system"></a><span data-ttu-id="7141e-104">Konfigurieren des Diagnosesystems</span><span class="sxs-lookup"><span data-stu-id="7141e-104">Configuring the diagnostics system</span></span>

## <a name="general-settings"></a><span data-ttu-id="7141e-105">Allgemeine Einstellungen</span><span class="sxs-lookup"><span data-stu-id="7141e-105">General settings</span></span>

![Allgemeine Diagnoseeinstellungen](../images/diagnostics/DiagnosticsGeneralSettings.png)

### <a name="enable-verbose-logging"></a><span data-ttu-id="7141e-107">Ausführliche Protokollierung aktivieren</span><span class="sxs-lookup"><span data-stu-id="7141e-107">Enable verbose logging</span></span>

<span data-ttu-id="7141e-108">Gibt an, ob die ausführliche MRTK-Protokollierung aktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="7141e-108">Indicates whether or not verbose MRTK logging will be enabled.</span></span> <span data-ttu-id="7141e-109">Dieser Standardwert ist false, kann aber aktiviert werden, um detaillierte Ablaufverfolgungen zu verwenden, die es dem MRTK-Team ermöglichen, Probleme zu debuggen/zu beheben.</span><span class="sxs-lookup"><span data-stu-id="7141e-109">This defaults to false, but can be turned on to take detailed traces that allow the MRTK team to debug/dig into issues.</span></span> <span data-ttu-id="7141e-110">Wenn Sie beispielsweise ein Problem melden, kann das Anfügen der Unity-Playerprotokolle (entweder über den Editor oder über den Player) dazu beitragen, die Quelle von Fehlern und Problemen einzuengen.</span><span class="sxs-lookup"><span data-stu-id="7141e-110">For example, when filing an issue, attaching the Unity player logs (either from the editor or from the player) can help narrow down the source of bugs and issues.</span></span>

<span data-ttu-id="7141e-111">Beachten Sie, dass diese Option unabhängig davon ist, ob das Diagnosesystem aktiviert ist. Dies wird im Diagnosesystem angezeigt, da es sich um eine Protokollierungsoption handelt, aber letztendlich auf einer höheren Ebene arbeitet, da sie sich auf die Protokollierung in der gesamten MRTK-Codebasis auswirken.</span><span class="sxs-lookup"><span data-stu-id="7141e-111">Note that this option is independent of whether or not diagnostics system is enabled - this shows up under the diagnostics system because it's a logging option, but ultimately operates at a higher level because it affects logging across the entire MRTK codebase.</span></span>

### <a name="show-diagnostics"></a><span data-ttu-id="7141e-112">Diagnose anzeigen</span><span class="sxs-lookup"><span data-stu-id="7141e-112">Show diagnostics</span></span>

<span data-ttu-id="7141e-113">Gibt an, ob das Diagnosesystem die konfigurierten Diagnoseoptionen anzeigen soll.</span><span class="sxs-lookup"><span data-stu-id="7141e-113">Indicates whether or not the diagnostics system is to display the configured diagnostic options.</span></span>

<span data-ttu-id="7141e-114">Wenn diese Option deaktiviert ist, werden alle konfigurierten Diagnoseoptionen ausgeblendet.</span><span class="sxs-lookup"><span data-stu-id="7141e-114">When disabled, all configured diagnostic options will be hidden.</span></span>

## <a name="profiler-settings"></a><span data-ttu-id="7141e-115">Profilereinstellungen</span><span class="sxs-lookup"><span data-stu-id="7141e-115">Profiler settings</span></span>

![Einstellungen des Diagnoseprofilers](../images/diagnostics/DiagnosticsProfilerSettings.png)

### <a name="show-profiler"></a><span data-ttu-id="7141e-117">Profiler anzeigen</span><span class="sxs-lookup"><span data-stu-id="7141e-117">Show profiler</span></span>

<span data-ttu-id="7141e-118">Gibt an, ob der Visual Profiler angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="7141e-118">Indicates whether or not the Visual Profiler is to be displayed.</span></span>

### <a name="frame-sample-rate"></a><span data-ttu-id="7141e-119">Frame-Abtastrate</span><span class="sxs-lookup"><span data-stu-id="7141e-119">Frame sample rate</span></span>

<span data-ttu-id="7141e-120">Die Zeit in Sekunden zum Erfassen von Frames für die Berechnung der Bildfrequenz.</span><span class="sxs-lookup"><span data-stu-id="7141e-120">The amount of time, in seconds to collect frames for frame rate calculation.</span></span> <span data-ttu-id="7141e-121">Der Bereich beträgt 0 bis 5 Sekunden.</span><span class="sxs-lookup"><span data-stu-id="7141e-121">The range is 0 to 5 seconds.</span></span>

### <a name="window-anchor"></a><span data-ttu-id="7141e-122">Fensteranker</span><span class="sxs-lookup"><span data-stu-id="7141e-122">Window anchor</span></span>

<span data-ttu-id="7141e-123">An welchem Teil des Ansichtsport sollte das Profilerfenster verankert werden.</span><span class="sxs-lookup"><span data-stu-id="7141e-123">To what portion of the view port should the profiler window be anchored.</span></span> <span data-ttu-id="7141e-124">Der Standardwert ist Lower Center.</span><span class="sxs-lookup"><span data-stu-id="7141e-124">The default value is Lower Center.</span></span>

### <a name="window-offset"></a><span data-ttu-id="7141e-125">Fensteroffset</span><span class="sxs-lookup"><span data-stu-id="7141e-125">Window offset</span></span>

<span data-ttu-id="7141e-126">Der Offset von der Mitte des Ansichtsport, um den Visual Profiler zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="7141e-126">The offset, from the center of the view port, to place the Visual Profiler.</span></span> <span data-ttu-id="7141e-127">Der Offset wird in Richtung der Eigenschaft *Fensteranker* angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7141e-127">The offset will be in the direction of the *Window Anchor* property.</span></span>

### <a name="window-scale"></a><span data-ttu-id="7141e-128">Fensterskala</span><span class="sxs-lookup"><span data-stu-id="7141e-128">Window scale</span></span>

<span data-ttu-id="7141e-129">Auf das Profilerfenster angewendeter Größenmultiplikator.</span><span class="sxs-lookup"><span data-stu-id="7141e-129">Size multiplier applied to the profiler window.</span></span> <span data-ttu-id="7141e-130">Wenn Sie beispielsweise den Wert auf 2 festlegen, wird die Fenstergröße verdoppelt.</span><span class="sxs-lookup"><span data-stu-id="7141e-130">For example, setting the value to 2 will double the window size.</span></span>

### <a name="window-follow-speed"></a><span data-ttu-id="7141e-131">Fenster folgt Geschwindigkeit</span><span class="sxs-lookup"><span data-stu-id="7141e-131">Window follow speed</span></span>

<span data-ttu-id="7141e-132">Die Geschwindigkeit, mit der das Profilerfenster bewegt werden soll, um die Sichtbarkeit innerhalb des Ansichtsport zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="7141e-132">The speed at which to move the profiler window to maintain visibility within the view port.</span></span>

## <a name="programmatically-controlling-the-diagnostics-system"></a><span data-ttu-id="7141e-133">Programmgesteuertes Steuern des Diagnosesystems</span><span class="sxs-lookup"><span data-stu-id="7141e-133">Programmatically controlling the diagnostics system</span></span>

<span data-ttu-id="7141e-134">Es ist auch möglich, die Sichtbarkeit des Diagnosesystems und des Profilers zur Laufzeit umschalten.</span><span class="sxs-lookup"><span data-stu-id="7141e-134">It's also possible to toggle the visibility of the diagnostics system and the profiler at runtime.</span></span> <span data-ttu-id="7141e-135">Der folgende Code blendet z. B. das Diagnosesystem und den Profiler aus.</span><span class="sxs-lookup"><span data-stu-id="7141e-135">For example, the code below will hide the diagnostics system and profiler.</span></span>

```c#
CoreServices.DiagnosticsSystem.ShowDiagnostics = false;

CoreServices.DiagnosticsSystem.ShowProfiler = false;
```

## <a name="see-also"></a><span data-ttu-id="7141e-136">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="7141e-136">See also</span></span>

- [<span data-ttu-id="7141e-137">Diagnosesystem</span><span class="sxs-lookup"><span data-stu-id="7141e-137">Diagnostics System</span></span>](diagnostics-system-getting-started.md)
- [<span data-ttu-id="7141e-138">Verwenden von Visual Profiler</span><span class="sxs-lookup"><span data-stu-id="7141e-138">Using the Visual Profiler</span></span>](using-visual-profiler.md)
