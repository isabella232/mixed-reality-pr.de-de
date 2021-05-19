---
title: Raumabtastvisualisierung
description: Anwendungen, die eine räumliche Zuordnung erfordern, verwenden das Gerät, um Daten im Zeitverlauf und sitzungsübergreifend zu sammeln.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, App-Muster, Design, HoloLens, Raumscan, räumliche Zuordnung, Mesh, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens
ms.openlocfilehash: 8c7f1ae95cfdb520e84835f7fd5d78522e62e341
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143609"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="f848e-104">Raumabtastvisualisierung</span><span class="sxs-lookup"><span data-stu-id="f848e-104">Room scan visualization</span></span>

<span data-ttu-id="f848e-105">Anwendungen, die eine räumliche Zuordnung erfordern, verlassen sich darauf, dass das Gerät Daten im Laufe der Zeit und sitzungsübergreifend sammelt.</span><span class="sxs-lookup"><span data-stu-id="f848e-105">Applications that require spatial mapping rely on the device to collect data over time and across sessions.</span></span> <span data-ttu-id="f848e-106">Die Vollständigkeit und Qualität der Zuordnungsdaten hängt von vielen Faktoren ab, einschließlich des Umfangs der Vom Benutzer durchgeführten Untersuchung, der Zeit, die seit der Untersuchung verstrichen ist, und davon, ob Objekte wie Türen und Türen seit dem Scannen des Bereichs durch das Gerät verschoben wurden.</span><span class="sxs-lookup"><span data-stu-id="f848e-106">The completeness and quality of the mapping data depends on many factors, including the amount of exploration the user has done, how much time has passed since the exploration, and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="f848e-107">Anwendungsentwickler haben mehrere Optionen, um nützliche räumliche Zuordnungsdaten sicherzustellen:</span><span class="sxs-lookup"><span data-stu-id="f848e-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="f848e-108">Verlassen Sie sich auf das, was möglicherweise bereits gesammelt wurde.</span><span class="sxs-lookup"><span data-stu-id="f848e-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="f848e-109">Diese Daten sind möglicherweise zunächst unvollständig.</span><span class="sxs-lookup"><span data-stu-id="f848e-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="f848e-110">Bitten Sie den Benutzer, die Geste "Bloom" zu verwenden, um zum Windows Mixed Reality Startseite zu gelangen und dann den Bereich zu erkunden, den er für die Umgebung verwenden möchte.</span><span class="sxs-lookup"><span data-stu-id="f848e-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="f848e-111">Sie können mithilfe von Tippen in die Luft bestätigen, dass dem Gerät der gesamte erforderliche Bereich bekannt ist.</span><span class="sxs-lookup"><span data-stu-id="f848e-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="f848e-112">Erstellen einer benutzerdefinierten Untersuchungserfahrung in ihrer eigenen Anwendung</span><span class="sxs-lookup"><span data-stu-id="f848e-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="f848e-113">In all diesen Fällen werden die während der Untersuchung gesammelten Daten vom System gespeichert, und die Anwendung muss dies nicht tun.</span><span class="sxs-lookup"><span data-stu-id="f848e-113">In all these cases, the actual data gathered during the exploration is stored by the system and the application doesn't need to do this.</span></span> <span data-ttu-id="f848e-114">Wenn Sie die Raumscanvisualisierung in Aktion sehen möchten, sehen Sie sich die folgende Videodemo [zum Entwerfen von Hologrammen – Räumliche Wahrnehmung]() an:</span><span class="sxs-lookup"><span data-stu-id="f848e-114">If you'd like to see room scan visualization in action, check out our [Designing Holograms - Spatial Awareness]() video demo below:</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

## <a name="device-support"></a><span data-ttu-id="f848e-115">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="f848e-115">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f848e-116"><strong>Feature</strong></span><span class="sxs-lookup"><span data-stu-id="f848e-116"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="f848e-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="f848e-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="f848e-118"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="f848e-118"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f848e-119">Raumabtastvisualisierung</span><span class="sxs-lookup"><span data-stu-id="f848e-119">Room scan visualization</span></span></td>
        <td><span data-ttu-id="f848e-120">✔️</span><span class="sxs-lookup"><span data-stu-id="f848e-120">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="f848e-121">Erstellen einer benutzerdefinierten Überprüfungserfahrung</span><span class="sxs-lookup"><span data-stu-id="f848e-121">Building a custom scanning experience</span></span>

<span data-ttu-id="f848e-122">Anwendungen können die räumlichen Zuordnungsdaten zu Beginn der Benutzeroberfläche analysieren, um zu beurteilen, ob der Benutzer zusätzliche Schritte ausführen soll, um seine Vollständigkeit und Qualität zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="f848e-122">Applications may analyze the spatial mapping data at the start of the experience to judge whether they want the user to do extra steps to improve its completeness and quality.</span></span> <span data-ttu-id="f848e-123">Wenn die Analyse angibt, dass die Qualität verbessert werden sollte, sollten Entwickler eine Visualisierung zur Überlagerung auf der Welt bereitstellen, um Folgendes anzugeben:</span><span class="sxs-lookup"><span data-stu-id="f848e-123">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="f848e-124">Wie viel des Gesamtvolumens in der Benutzerumgebung muss Teil der Benutzeroberfläche sein?</span><span class="sxs-lookup"><span data-stu-id="f848e-124">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="f848e-125">Ort, an dem der Benutzer Daten verbessern soll</span><span class="sxs-lookup"><span data-stu-id="f848e-125">Where the user should go to improve data</span></span>

<span data-ttu-id="f848e-126">Benutzer wissen nicht, was einen "guten" Scan ausmacht.</span><span class="sxs-lookup"><span data-stu-id="f848e-126">Users don't know what makes a "good" scan.</span></span> <span data-ttu-id="f848e-127">Sie müssen angezeigt oder gefragt werden, was sie suchen sollten, wenn sie aufgefordert werden, einen Scan zu bewerten – Flachheit, Abstand von den tatsächlichen Wänden und so weiter.</span><span class="sxs-lookup"><span data-stu-id="f848e-127">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, and so on.</span></span> <span data-ttu-id="f848e-128">Der Entwickler sollte eine Feedbackschleife implementieren, die das Aktualisieren der Räumlichen Zuordnungsdaten während der Überprüfungs- oder Untersuchungsphase umfasst.</span><span class="sxs-lookup"><span data-stu-id="f848e-128">The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="f848e-129">In vielen Fällen ist es am besten, den Benutzer darüber zu informieren, was er tun muss, um die erforderliche Scanqualität zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="f848e-129">In many cases, it's best to tell the user what they need to do to get the necessary scan quality.</span></span> <span data-ttu-id="f848e-130">Sehen Sie sich z. B. die Obergrenze an, sehen Sie sich hinter Gittern an, und so weiter.</span><span class="sxs-lookup"><span data-stu-id="f848e-130">For example, look at the ceiling, look behind furniture, and so on.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="f848e-131">Zwischengespeicherte und kontinuierliche räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="f848e-131">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="f848e-132">Die räumlichen Zuordnungsdaten sind die am stärksten gewichteten Datenquellenanwendungen, die verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="f848e-132">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="f848e-133">Um Leistungsprobleme wie z. B. gelöschte Frames oder Dasttern zu vermeiden, sollte der Verbrauch dieser Daten sorgfältig erfolgen.</span><span class="sxs-lookup"><span data-stu-id="f848e-133">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="f848e-134">Das aktive Scannen während einer Erfahrung kann sowohl vorteilhaft als auch negativ sein, sodass Sie basierend auf der Erfahrung entscheiden müssen, welche Methode verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="f848e-134">Active scanning during an experience can be both beneficial and detrimental, so you'll need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="f848e-135">Zwischengespeicherte räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="f848e-135">Cached spatial mapping</span></span>

<span data-ttu-id="f848e-136">Wenn zwischengespeicherte räumliche Zuordnungsdaten vorhanden sind, erstellt die Anwendung in der Regel eine Momentaufnahme der Räumlichen Zuordnungsdaten und verwendet diese Momentaufnahme während der Erfahrung.</span><span class="sxs-lookup"><span data-stu-id="f848e-136">If there's cached spatial mapping data, the application typically takes a snapshot of the spatial mapping data and uses this snapshot during the experience.</span></span>

<span data-ttu-id="f848e-137">**Vorteile**</span><span class="sxs-lookup"><span data-stu-id="f848e-137">**Benefits**</span></span>
* <span data-ttu-id="f848e-138">Reduzierter Mehraufwand für das System, während die Erfahrung ausgeführt wird, was zu erheblichen Leistungssteigerungen, Wärme- und CPU-Leistungssteigerungen führt.</span><span class="sxs-lookup"><span data-stu-id="f848e-138">Reduced overhead on the system while the experience is running leading to dramatic power, thermal, and cpu performance gains.</span></span>
* <span data-ttu-id="f848e-139">Eine einfachere Implementierung der Haupterfahrung, da sie nicht durch Änderungen der räumlichen Daten unterbrochen wird.</span><span class="sxs-lookup"><span data-stu-id="f848e-139">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="f848e-140">Ein einzelner einmaliger Kosten für jede Nachverarbeitung der räumlichen Daten für Physikalische, Grafiken und andere Zwecke.</span><span class="sxs-lookup"><span data-stu-id="f848e-140">A single one time cost on any post processing of the spatial data for physics, graphics, and other purposes.</span></span>

<span data-ttu-id="f848e-141">**Nachteile**</span><span class="sxs-lookup"><span data-stu-id="f848e-141">**Drawbacks**</span></span>
* <span data-ttu-id="f848e-142">Die Bewegung realer Objekte oder Personen spiegelt sich nicht in den zwischengespeicherten Daten wider.</span><span class="sxs-lookup"><span data-stu-id="f848e-142">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="f848e-143">Beispielsweise könnte die Anwendung eine türöffnend betrachten, wenn sie jetzt geschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="f848e-143">for example, the application might consider a door open when it's closed now.</span></span>
* <span data-ttu-id="f848e-144">Möglicherweise mehr Anwendungsspeicher, um die zwischengespeicherte Version der Daten zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="f848e-144">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="f848e-145">Ein guter Fall für diese Methode ist eine kontrollierte Umgebung oder ein Tabellenspiel.</span><span class="sxs-lookup"><span data-stu-id="f848e-145">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="f848e-146">Kontinuierliche räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="f848e-146">Continuous spatial mapping</span></span>

<span data-ttu-id="f848e-147">Bei bestimmten Anwendungen wird die Überprüfung möglicherweise fortgesetzt, um räumliche Zuordnungsdaten zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="f848e-147">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="f848e-148">**Vorteile**</span><span class="sxs-lookup"><span data-stu-id="f848e-148">**Benefits**</span></span>
* <span data-ttu-id="f848e-149">Sie müssen keine separate Überprüfungs- oder Untersuchungserfahrung im Voraus in Ihrer Anwendung erstellen.</span><span class="sxs-lookup"><span data-stu-id="f848e-149">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="f848e-150">Die Bewegung realer Objekte kann durch das Spiel widergespiegelt werden, allerdings mit einiger Verzögerung.</span><span class="sxs-lookup"><span data-stu-id="f848e-150">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="f848e-151">**Nachteile**</span><span class="sxs-lookup"><span data-stu-id="f848e-151">**Drawbacks**</span></span>
* <span data-ttu-id="f848e-152">Höhere Komplexität bei der Implementierung der Haupterfahrung.</span><span class="sxs-lookup"><span data-stu-id="f848e-152">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="f848e-153">Potenzieller Mehraufwand durch die zusätzliche grafik- und physikalische Verarbeitung, da Änderungen inkrementell von diesen Systemen aufgenommen werden müssen.</span><span class="sxs-lookup"><span data-stu-id="f848e-153">Potential overhead from the extra graphic and physics processing, as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="f848e-154">Höhere Leistung, wärmer und CPU-Auswirkungen.</span><span class="sxs-lookup"><span data-stu-id="f848e-154">Higher power, thermal, and CPU impact.</span></span>

<span data-ttu-id="f848e-155">Ein guter Fall für diese Methode ist, dass Hologramme mit bewegten Objekten interagieren sollen, z. B. ein holografisches Auto, das auf dem Boden fährt, je nachdem, ob es offen oder geschlossen ist, auf eine Tür stoßen möchte.</span><span class="sxs-lookup"><span data-stu-id="f848e-155">A good case for this method is one where holograms are expected to interact with moving objects, for example, a holographic car that drives on the floor may want to bump into a door depending on whether it's open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="f848e-156">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f848e-156">See also</span></span>

* [<span data-ttu-id="f848e-157">Räumliche Abbildung</span><span class="sxs-lookup"><span data-stu-id="f848e-157">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="f848e-158">Koordinatensysteme</span><span class="sxs-lookup"><span data-stu-id="f848e-158">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="f848e-159">Raumklangentwurf</span><span class="sxs-lookup"><span data-stu-id="f848e-159">Spatial sound design</span></span>](spatial-sound-design.md)