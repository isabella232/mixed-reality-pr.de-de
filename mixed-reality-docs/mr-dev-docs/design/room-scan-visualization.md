---
title: Raumabtastvisualisierung
description: Anwendungen, die eine räumliche Zuordnung erfordern, verwenden das Gerät, um Daten im Zeitverlauf und Sitzungs übergreifend zu erfassen.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Gemischte Windows-Realität, App-Muster, Entwurf, hololens, Raum Überprüfung, räumliche Zuordnung, Mesh, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens
ms.openlocfilehash: f4ec072c8fde8d3e7e390bd837116a8262bac38b
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848250"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="3e1c9-104">Raumabtastvisualisierung</span><span class="sxs-lookup"><span data-stu-id="3e1c9-104">Room scan visualization</span></span>

<span data-ttu-id="3e1c9-105">Anwendungen, die eine räumliche Zuordnung erfordern, basieren auf dem Gerät, um Daten im Zeitverlauf und Sitzungs übergreifend zu erfassen.</span><span class="sxs-lookup"><span data-stu-id="3e1c9-105">Applications that require spatial mapping rely on the device to collect data over time and across sessions.</span></span> <span data-ttu-id="3e1c9-106">Die Vollständigkeit und Qualität der Zuordnungsdaten hängt von vielen Faktoren ab, z. b. vom Umfang der durchgeführten Untersuchung, von der seit der Durchsuchung übergebenen Zeit und davon, ob Objekte wie z. b. Möbel und Türen verschoben wurden, seit das Gerät den Bereich gescannt hat.</span><span class="sxs-lookup"><span data-stu-id="3e1c9-106">The completeness and quality of the mapping data depends on many factors, including the amount of exploration the user has done, how much time has passed since the exploration, and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="3e1c9-107">Anwendungsentwickler haben mehrere Möglichkeiten, um hilfreiche räumliche Daten zu gewährleisten:</span><span class="sxs-lookup"><span data-stu-id="3e1c9-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="3e1c9-108">Verlassen Sie sich darauf, was bereits gesammelt wurde.</span><span class="sxs-lookup"><span data-stu-id="3e1c9-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="3e1c9-109">Diese Daten sind anfänglich möglicherweise unvollständig.</span><span class="sxs-lookup"><span data-stu-id="3e1c9-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="3e1c9-110">Bitten Sie den Benutzer, mit der aufblühenden Bewegung den Windows Mixed Reality-Start zu verwenden und dann den Bereich zu erkunden, den Sie für die Benutzeroberfläche verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="3e1c9-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="3e1c9-111">Mithilfe von Air-Tap können Sie überprüfen, ob dem Gerät der gesamte erforderliche Bereich bekannt ist.</span><span class="sxs-lookup"><span data-stu-id="3e1c9-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="3e1c9-112">Erstellen Sie eine benutzerdefinierte Erkundung in ihrer eigenen Anwendung.</span><span class="sxs-lookup"><span data-stu-id="3e1c9-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="3e1c9-113">In all diesen Fällen werden die während der Durchsuchung gesammelten Daten vom System gespeichert, und die Anwendung muss dies nicht tun.</span><span class="sxs-lookup"><span data-stu-id="3e1c9-113">In all these cases, the actual data gathered during the exploration is stored by the system and the application doesn't need to do this.</span></span>

## <a name="device-support"></a><span data-ttu-id="3e1c9-114">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="3e1c9-114">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="3e1c9-115"><strong>Feature</strong></span><span class="sxs-lookup"><span data-stu-id="3e1c9-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="3e1c9-116"><a href="../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="3e1c9-116"><a href="../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="3e1c9-117"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="3e1c9-117"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="3e1c9-118">Raumabtastvisualisierung</span><span class="sxs-lookup"><span data-stu-id="3e1c9-118">Room scan visualization</span></span></td>
        <td><span data-ttu-id="3e1c9-119">✔️</span><span class="sxs-lookup"><span data-stu-id="3e1c9-119">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>



## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="3e1c9-120">Entwickeln eines benutzerdefinierten Scanvorgangs</span><span class="sxs-lookup"><span data-stu-id="3e1c9-120">Building a custom scanning experience</span></span>

<span data-ttu-id="3e1c9-121">Anwendungen können die räumlichen Zuordnungsdaten zu Beginn der Umgebung analysieren, um zu beurteilen, ob der Benutzer zusätzliche Schritte ausführen soll, um seine Vollständigkeit und Qualität zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="3e1c9-121">Applications may analyze the spatial mapping data at the start of the experience to judge whether they want the user to do extra steps to improve its completeness and quality.</span></span> <span data-ttu-id="3e1c9-122">Wenn die Analyse anzeigt, dass die Qualität verbessert werden sollte, sollten Entwickler eine Visualisierung bereitstellen, um auf der ganzen Welt zu überlagern:</span><span class="sxs-lookup"><span data-stu-id="3e1c9-122">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="3e1c9-123">Der Anteil des Gesamtvolumens in der Benutzer Nähe muss Teil der Benutzerumgebung sein.</span><span class="sxs-lookup"><span data-stu-id="3e1c9-123">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="3e1c9-124">An welcher Stelle der Benutzerdaten verbessern sollte</span><span class="sxs-lookup"><span data-stu-id="3e1c9-124">Where the user should go to improve data</span></span>

<span data-ttu-id="3e1c9-125">Benutzer wissen nicht, was einen "guten" Scan vornimmt.</span><span class="sxs-lookup"><span data-stu-id="3e1c9-125">Users don't know what makes a "good" scan.</span></span> <span data-ttu-id="3e1c9-126">Sie müssen angezeigt werden, oder Sie müssen wissen, was Sie suchen müssen, wenn Sie aufgefordert werden, eine Überprüfung zu evaluieren – die Flatness, die Entfernung von tatsächlichen Wänden usw.</span><span class="sxs-lookup"><span data-stu-id="3e1c9-126">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, and so on.</span></span> <span data-ttu-id="3e1c9-127">Der Entwickler sollte eine Feedback Schleife implementieren, die das Aktualisieren der räumlichen Daten während der Scan-oder Auswertungs Phase umfasst.</span><span class="sxs-lookup"><span data-stu-id="3e1c9-127">The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="3e1c9-128">In vielen Fällen ist es am besten, den Benutzern mitzuteilen, was Sie tun müssen, um die erforderliche Scanqualität zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="3e1c9-128">In many cases, it's best to tell the user what they need to do to get the necessary scan quality.</span></span> <span data-ttu-id="3e1c9-129">Sehen Sie sich beispielsweise die Obergrenze an, sehen Sie sich die Möbel an, usw.</span><span class="sxs-lookup"><span data-stu-id="3e1c9-129">For example, look at the ceiling, look behind furniture, and so on.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="3e1c9-130">Zwischengespeicherte und fortlaufende räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="3e1c9-130">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="3e1c9-131">Die räumlichen Daten sind die Daten, die von den Datenquellen Anwendungen mit hohem Gewicht beansprucht werden können.</span><span class="sxs-lookup"><span data-stu-id="3e1c9-131">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="3e1c9-132">Um Leistungsprobleme zu vermeiden, wie z. b. gelöschte Frames oder stutor-Daten, sollte die Nutzung dieser Daten sorgfältig erfolgen.</span><span class="sxs-lookup"><span data-stu-id="3e1c9-132">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="3e1c9-133">Die aktive Überprüfung während einer-Darstellung kann sowohl vorteilhaft als auch schädlich sein, daher müssen Sie entscheiden, welche Methode basierend auf der-Methode verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="3e1c9-133">Active scanning during an experience can be both beneficial and detrimental, so you'll need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="3e1c9-134">Zwischengespeicherte räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="3e1c9-134">Cached spatial mapping</span></span>

<span data-ttu-id="3e1c9-135">Wenn zwischengespeicherte räumliche Zuordnungsdaten vorliegen, erstellt die Anwendung in der Regel eine Momentaufnahme der räumlichen Zuordnungsdaten und verwendet diese Momentaufnahme während des Vorgangs.</span><span class="sxs-lookup"><span data-stu-id="3e1c9-135">If there's cached spatial mapping data, the application typically takes a snapshot of the spatial mapping data and uses this snapshot during the experience.</span></span>

<span data-ttu-id="3e1c9-136">**Vorteile**</span><span class="sxs-lookup"><span data-stu-id="3e1c9-136">**Benefits**</span></span>
* <span data-ttu-id="3e1c9-137">Reduzierter mehr Aufwand für das System während der Ausführung der Leistung, was zu Leistungssteigerungen bei der Leistung, der Wärmeversorgung und der CPU führt.</span><span class="sxs-lookup"><span data-stu-id="3e1c9-137">Reduced overhead on the system while the experience is running leading to dramatic power, thermal, and cpu performance gains.</span></span>
* <span data-ttu-id="3e1c9-138">Eine einfachere Implementierung des Haupt Erlebnisses, da diese nicht durch Änderungen in den räumlichen Daten unterbrochen wird.</span><span class="sxs-lookup"><span data-stu-id="3e1c9-138">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="3e1c9-139">Ein einzelner Zeitaufwand für die nach Verarbeitung der räumlichen Daten für die Physik, Grafiken und andere Zwecke.</span><span class="sxs-lookup"><span data-stu-id="3e1c9-139">A single one time cost on any post processing of the spatial data for physics, graphics, and other purposes.</span></span>

<span data-ttu-id="3e1c9-140">**Nachteil**</span><span class="sxs-lookup"><span data-stu-id="3e1c9-140">**Drawbacks**</span></span>
* <span data-ttu-id="3e1c9-141">Die Verschiebung von realen Objekten oder Personen wird von den zwischengespeicherten Daten nicht widergespiegelt.</span><span class="sxs-lookup"><span data-stu-id="3e1c9-141">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="3e1c9-142">die Anwendung kann z. b. eine Tür als geöffnet sehen, wenn Sie jetzt geschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="3e1c9-142">for example, the application might consider a door open when it's closed now.</span></span>
* <span data-ttu-id="3e1c9-143">Potenziell mehr Anwendungs Speicher, um die zwischengespeicherte Version der Daten beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="3e1c9-143">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="3e1c9-144">Ein guter Fall für diese Methode ist eine kontrollierte Umgebung oder ein Top-Spiel der Tabelle.</span><span class="sxs-lookup"><span data-stu-id="3e1c9-144">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="3e1c9-145">Fortlaufende räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="3e1c9-145">Continuous spatial mapping</span></span>

<span data-ttu-id="3e1c9-146">Bestimmte Anwendungen verlassen sich möglicherweise auf das Fortsetzen des Scans, um räumliche Daten zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="3e1c9-146">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="3e1c9-147">**Vorteile**</span><span class="sxs-lookup"><span data-stu-id="3e1c9-147">**Benefits**</span></span>
* <span data-ttu-id="3e1c9-148">Sie müssen in Ihrer Anwendung nicht in einer separaten Überprüfung oder Durchsuchung arbeiten.</span><span class="sxs-lookup"><span data-stu-id="3e1c9-148">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="3e1c9-149">Die Bewegung von realen Objekten kann durch das Spiel reflektiert werden, obwohl es sich um eine Verzögerung handelt.</span><span class="sxs-lookup"><span data-stu-id="3e1c9-149">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="3e1c9-150">**Nachteil**</span><span class="sxs-lookup"><span data-stu-id="3e1c9-150">**Drawbacks**</span></span>
* <span data-ttu-id="3e1c9-151">Höhere Komplexität bei der Implementierung des Haupt Erlebnisses.</span><span class="sxs-lookup"><span data-stu-id="3e1c9-151">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="3e1c9-152">Potenzieller mehr Aufwand bei der zusätzlichen Grafik-und Physik Verarbeitung, da Änderungen inkrementell von diesen Systemen erfasst werden müssen.</span><span class="sxs-lookup"><span data-stu-id="3e1c9-152">Potential overhead from the extra graphic and physics processing, as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="3e1c9-153">Höhere Stromversorgung, thermische und CPU-Auswirkung.</span><span class="sxs-lookup"><span data-stu-id="3e1c9-153">Higher power, thermal, and CPU impact.</span></span>

<span data-ttu-id="3e1c9-154">Ein guter Fall für diese Methode ist eine Methode, bei der holograms mit verschiebenden Objekten interagieren soll, z. b. Wenn ein Holographic Car, das auf dem Boden ist, möglicherweise an eine Tür stößt, je nachdem, ob es geöffnet oder geschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="3e1c9-154">A good case for this method is one where holograms are expected to interact with moving objects, for example, a holographic car that drives on the floor may want to bump into a door depending on whether it's open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="3e1c9-155">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="3e1c9-155">See also</span></span>

* [<span data-ttu-id="3e1c9-156">Räumliche Abbildung</span><span class="sxs-lookup"><span data-stu-id="3e1c9-156">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="3e1c9-157">Koordinatensysteme</span><span class="sxs-lookup"><span data-stu-id="3e1c9-157">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="3e1c9-158">Raumklangentwurf</span><span class="sxs-lookup"><span data-stu-id="3e1c9-158">Spatial sound design</span></span>](spatial-sound-design.md)
