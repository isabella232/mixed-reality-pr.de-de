---
title: Spectator View
description: Visualisieren Sie Hologramme von einem externen Gerät, um ein Mixed-Reality-Erlebnis auf einem externen Display zu darzustellen oder aufzunehmen.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Spectator View, iPhone, iOS, iPad, OpenCV, Kamera, ARKit, HoloLens, Mixed Reality, MixedRealityToolkit, Demo, aufzeichnen
ms.openlocfilehash: c344edea9b499bdff15d1d93e400b8be626a63b6
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530111"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a><span data-ttu-id="3c3d4-104">Spectator View für HoloLens und HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="3c3d4-104">Spectator View for HoloLens and HoloLens 2</span></span>

![Marker](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a><span data-ttu-id="3c3d4-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="3c3d4-106">Overview</span></span>

<span data-ttu-id="3c3d4-107">Wenn Sie eine HoloLens tragen, vergessen Sie leicht, dass eine Person ohne HoloLens nicht dieselben Wunder erleben kann, die Sie sehen.</span><span class="sxs-lookup"><span data-stu-id="3c3d4-107">When you're wearing a HoloLens, it's easy to forget a person without one can't experience the same wonders you're seeing.</span></span> <span data-ttu-id="3c3d4-108">Mit Spectator View können andere sehen, was ein HoloLens-Benutzer auf einem 2D-Bildschirm sieht.</span><span class="sxs-lookup"><span data-stu-id="3c3d4-108">Spectator View lets others see what a HoloLens user sees on a 2D screen.</span></span> <span data-ttu-id="3c3d4-109">Es ist außerdem ein schneller und kostengünstiger Ansatz, um Hologramme in HD mit mobilen Geräten aufzunehmen und mit Videokameras Aufnahmen von Hologrammen in hoher Qualität zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="3c3d4-109">It's also a fast and affordable approach to recording holograms in HD with mobile devices and getting great quality recordings of holograms with video cameras.</span></span>

## <a name="key-resources"></a><span data-ttu-id="3c3d4-110">Wichtige Ressourcen</span><span class="sxs-lookup"><span data-stu-id="3c3d4-110">Key Resources</span></span>

* [<span data-ttu-id="3c3d4-111">**Spectator View auf GitHub**</span><span class="sxs-lookup"><span data-stu-id="3c3d4-111">**Spectator View on GitHub**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView)
* [<span data-ttu-id="3c3d4-112">**Spectator View-Dokumentation**</span><span class="sxs-lookup"><span data-stu-id="3c3d4-112">**Spectator View Documentation**</span></span>](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [<span data-ttu-id="3c3d4-113">**Spectator View-Beispiele**</span><span class="sxs-lookup"><span data-stu-id="3c3d4-113">**Spectator View Samples**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a><span data-ttu-id="3c3d4-114">Anwendungsfälle</span><span class="sxs-lookup"><span data-stu-id="3c3d4-114">Use Cases</span></span>

* <span data-ttu-id="3c3d4-115">Sie können ein Mixed Reality-Erlebnis mithilfe eines iPhone- oder Android-Geräts aufzeichnen.</span><span class="sxs-lookup"><span data-stu-id="3c3d4-115">You can record a mixed reality experience using an iPhone or Android device.</span></span> <span data-ttu-id="3c3d4-116">Zeichnen Sie in Full-HD auf, und wenden Sie Anti-Aliasing auf Hologramme und Schatten an – eine kostengünstige und schnelle Möglichkeit, Videos von Hologrammen aufzunehmen.</span><span class="sxs-lookup"><span data-stu-id="3c3d4-116">Record in full HD and apply anti-aliasing to holograms and shadow for a cost-effective and quick way to capture video of holograms.</span></span>
* <span data-ttu-id="3c3d4-117">Streamen Sie von Ihrem iPhone oder iPad verzögerungsfrei Mixed Reality-Erlebnisse live auf ein Apple TV!</span><span class="sxs-lookup"><span data-stu-id="3c3d4-117">Stream live mixed reality experiences to an Apple TV directly from your iPhone or iPad, lag-free!</span></span>
* <span data-ttu-id="3c3d4-118">Teilen Sie das Erlebnis mit Gästen: Lassen Sie Benutzer ohne HoloLens Hologramme direkt auf Ihren Smartphones oder Tablets erleben.</span><span class="sxs-lookup"><span data-stu-id="3c3d4-118">Share the experience with guests: Let non-HoloLens users experience holograms directly from their phones or tablets.</span></span>

## <a name="current-features"></a><span data-ttu-id="3c3d4-119">Aktuelle Features</span><span class="sxs-lookup"><span data-stu-id="3c3d4-119">Current Features</span></span>

* <span data-ttu-id="3c3d4-120">Synchronisierung von Hologrammen im Raum, sodass alle die Hologramme an genau der gleichen Stelle sehen.</span><span class="sxs-lookup"><span data-stu-id="3c3d4-120">Spatial synchronization of Holograms, so everyone sees holograms in the exact same place.</span></span>
* <span data-ttu-id="3c3d4-121">Unterstützung für iOS- (ARKit-fähige Geräte) und Android-Geräte (ARCore-fähige Geräte).</span><span class="sxs-lookup"><span data-stu-id="3c3d4-121">iOS (ARKit-enabled devices) and Android (ARCore-enabled devices) support.</span></span>
<span data-ttu-id="3c3d4-122">Mehrere iOS-Gäste.</span><span class="sxs-lookup"><span data-stu-id="3c3d4-122">Multiple iOS guests.</span></span>
<span data-ttu-id="3c3d4-123">Aufzeichnung von Video + Hologrammen + Raumklang + Hologrammklang.</span><span class="sxs-lookup"><span data-stu-id="3c3d4-123">Recording of video + holograms + ambient sound + hologram sound.</span></span>
<span data-ttu-id="3c3d4-124">Freigabeblatt, auf dem Sie Videos speichern, sie per E-Mail senden oder sie mit anderen unterstützten Apps teilen können.</span><span class="sxs-lookup"><span data-stu-id="3c3d4-124">Share sheet so you can save video, email it, or share with other supporting apps.</span></span>

<span data-ttu-id="3c3d4-125">![Marker](images/SpecViewPhoneDemo.jpg)
![Marker](images/hololensspectatorview-500px.jpg) ![Marker](images/spectatorview-300px.png)</span><span class="sxs-lookup"><span data-stu-id="3c3d4-125">![Marker](images/SpecViewPhoneDemo.jpg)
![Marker](images/hololensspectatorview-500px.jpg) ![Marker](images/spectatorview-300px.png)</span></span>

<span data-ttu-id="3c3d4-126">In der folgenden Tabelle sind verschiedene Funktionen von Spectator View aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="3c3d4-126">The following table shows different Spectator View functionality and their capabilities.</span></span> <span data-ttu-id="3c3d4-127">Wählen Sie die Option aus, die Ihren Anforderungen an Videoaufzeichnung am besten entspricht:</span><span class="sxs-lookup"><span data-stu-id="3c3d4-127">Choose the option that best fits your video recording needs:</span></span>

|      <span data-ttu-id="3c3d4-128">Funktionalität</span><span class="sxs-lookup"><span data-stu-id="3c3d4-128">Functionality</span></span>                                | <span data-ttu-id="3c3d4-129">Mobile</span><span class="sxs-lookup"><span data-stu-id="3c3d4-129">Mobile</span></span>                  |                    <span data-ttu-id="3c3d4-130">Videokamera</span><span class="sxs-lookup"><span data-stu-id="3c3d4-130">Video Camera</span></span>              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| <span data-ttu-id="3c3d4-131">HD-Qualität</span><span class="sxs-lookup"><span data-stu-id="3c3d4-131">HD quality</span></span>                           |         <span data-ttu-id="3c3d4-132">Full HD</span><span class="sxs-lookup"><span data-stu-id="3c3d4-132">Full HD</span></span>         |        <span data-ttu-id="3c3d4-133">Filmen in professioneller Qualität (durch die Videokamera bestimmt)</span><span class="sxs-lookup"><span data-stu-id="3c3d4-133">Professional quality filming (as determined by video camera)</span></span>      |
| <span data-ttu-id="3c3d4-134">Einfache Kamerabewegung</span><span class="sxs-lookup"><span data-stu-id="3c3d4-134">Easy camera movement</span></span>                 |            <span data-ttu-id="3c3d4-135">✔</span><span class="sxs-lookup"><span data-stu-id="3c3d4-135">✔</span></span>            |                      <span data-ttu-id="3c3d4-136">✔</span><span class="sxs-lookup"><span data-stu-id="3c3d4-136">✔</span></span>                      |
| <span data-ttu-id="3c3d4-137">Third-Person-Ansicht</span><span class="sxs-lookup"><span data-stu-id="3c3d4-137">Third-person view</span></span>                    |            <span data-ttu-id="3c3d4-138">✔</span><span class="sxs-lookup"><span data-stu-id="3c3d4-138">✔</span></span>            |                      <span data-ttu-id="3c3d4-139">✔</span><span class="sxs-lookup"><span data-stu-id="3c3d4-139">✔</span></span>                      |
| <span data-ttu-id="3c3d4-140">Kann auf Bildschirme gestreamt werden</span><span class="sxs-lookup"><span data-stu-id="3c3d4-140">Can be streamed to screens</span></span>           |            <span data-ttu-id="3c3d4-141">✔</span><span class="sxs-lookup"><span data-stu-id="3c3d4-141">✔</span></span>            |                      <span data-ttu-id="3c3d4-142">✔</span><span class="sxs-lookup"><span data-stu-id="3c3d4-142">✔</span></span>                      |
| <span data-ttu-id="3c3d4-143">Portabel</span><span class="sxs-lookup"><span data-stu-id="3c3d4-143">Portable</span></span>                             |            <span data-ttu-id="3c3d4-144">✔</span><span class="sxs-lookup"><span data-stu-id="3c3d4-144">✔</span></span>            |                                             |
| <span data-ttu-id="3c3d4-145">Drahtlos</span><span class="sxs-lookup"><span data-stu-id="3c3d4-145">Wireless</span></span>                             |            <span data-ttu-id="3c3d4-146">✔</span><span class="sxs-lookup"><span data-stu-id="3c3d4-146">✔</span></span>            |                                             |
| <span data-ttu-id="3c3d4-147">Zusätzlich erforderliche Hardware</span><span class="sxs-lookup"><span data-stu-id="3c3d4-147">Additional required hardware</span></span>         |     <span data-ttu-id="3c3d4-148">Android-Smartphone, iPhone</span><span class="sxs-lookup"><span data-stu-id="3c3d4-148">Android phone, iPhone</span></span>    | <span data-ttu-id="3c3d4-149">HoloLens + Rig + Stativ + Videokamera + PC + Unity</span><span class="sxs-lookup"><span data-stu-id="3c3d4-149">HoloLens + Rig + Tripod + Video Camera + PC + Unity</span></span> |
| <span data-ttu-id="3c3d4-150">Hardwareinvestition</span><span class="sxs-lookup"><span data-stu-id="3c3d4-150">Hardware investment</span></span>                  |           <span data-ttu-id="3c3d4-151">Niedrig</span><span class="sxs-lookup"><span data-stu-id="3c3d4-151">Low</span></span>            |                     <span data-ttu-id="3c3d4-152">Hoch</span><span class="sxs-lookup"><span data-stu-id="3c3d4-152">High</span></span>                    |
| <span data-ttu-id="3c3d4-153">Plattformübergreifend</span><span class="sxs-lookup"><span data-stu-id="3c3d4-153">Cross-platform</span></span>                       |           <span data-ttu-id="3c3d4-154">Android, iOS</span><span class="sxs-lookup"><span data-stu-id="3c3d4-154">Android, iOS</span></span>   |                                             |
| <span data-ttu-id="3c3d4-155">Synchronisierte Inhalte</span><span class="sxs-lookup"><span data-stu-id="3c3d4-155">Synchronized content</span></span>                 |            <span data-ttu-id="3c3d4-156">✔</span><span class="sxs-lookup"><span data-stu-id="3c3d4-156">✔</span></span>            |                      <span data-ttu-id="3c3d4-157">✔</span><span class="sxs-lookup"><span data-stu-id="3c3d4-157">✔</span></span>                      |
| <span data-ttu-id="3c3d4-158">Dauer des Runtime-Setups</span><span class="sxs-lookup"><span data-stu-id="3c3d4-158">Runtime setup duration</span></span>               |         <span data-ttu-id="3c3d4-159">Sofort</span><span class="sxs-lookup"><span data-stu-id="3c3d4-159">Instant</span></span>          |                     <span data-ttu-id="3c3d4-160">Langsam</span><span class="sxs-lookup"><span data-stu-id="3c3d4-160">Slow</span></span>                    |
## <a name="see-also"></a><span data-ttu-id="3c3d4-161">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="3c3d4-161">See also</span></span>

* [<span data-ttu-id="3c3d4-162">Mixed-Reality-Aufnahme</span><span class="sxs-lookup"><span data-stu-id="3c3d4-162">Mixed reality capture</span></span>](../../mixed-reality-capture.md) 
* [<span data-ttu-id="3c3d4-163">Mixed Reality-Aufnahme für Entwickler</span><span class="sxs-lookup"><span data-stu-id="3c3d4-163">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="3c3d4-164">Gemeinsame Erlebnisse in Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="3c3d4-164">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
