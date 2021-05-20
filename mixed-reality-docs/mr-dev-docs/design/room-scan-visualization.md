---
title: Raumabtastvisualisierung
description: Anwendungen, die eine räumliche Zuordnung erfordern, verwenden das Gerät, um Daten im Laufe der Zeit und sitzungsübergreifend zu sammeln.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, App-Muster, Design, HoloLens, Raumscan, räumliche Abbildung, Gitter, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, HoloLens
ms.openlocfilehash: 87312a5d5361ac0e8c24a622cf69fe3e9b147ff5
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196405"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="84cd4-104">Raumabtastvisualisierung</span><span class="sxs-lookup"><span data-stu-id="84cd4-104">Room scan visualization</span></span>

<span data-ttu-id="84cd4-105">Anwendungen, die räumliche Zuordnung erfordern, verlassen sich darauf, dass das Gerät Daten im Zeit- und sitzungsübergreifenden Zeitraum sammelt.</span><span class="sxs-lookup"><span data-stu-id="84cd4-105">Applications that require spatial mapping rely on the device to collect data over time and across sessions.</span></span> <span data-ttu-id="84cd4-106">Die Vollständigkeit und Qualität der Zuordnungsdaten hängt von vielen Faktoren ab, z. B. dem Umfang der Untersuchung durch den Benutzer, der Verstrichenheit seit der Untersuchung und davon, ob Objekte wie Hänge und Türen seit dem Scannen des Bereichs durch das Gerät verschoben wurden.</span><span class="sxs-lookup"><span data-stu-id="84cd4-106">The completeness and quality of the mapping data depends on many factors, including the amount of exploration the user has done, how much time has passed since the exploration, and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="84cd4-107">Um nützliche räumliche Zuordnungsdaten sicherzustellen, haben Anwendungsentwickler mehrere Optionen:</span><span class="sxs-lookup"><span data-stu-id="84cd4-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="84cd4-108">Verlassen Sie sich darauf, was möglicherweise bereits erfasst wurde.</span><span class="sxs-lookup"><span data-stu-id="84cd4-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="84cd4-109">Diese Daten sind möglicherweise anfänglich unvollständig.</span><span class="sxs-lookup"><span data-stu-id="84cd4-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="84cd4-110">Bitten Sie den Benutzer, die Blumengeste zu verwenden, um zum Haus Windows Mixed Reality zu kommen und dann den Bereich zu erkunden, den er für die Benutzeroberfläche verwenden möchte.</span><span class="sxs-lookup"><span data-stu-id="84cd4-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="84cd4-111">Sie können mithilfe von Tippen in die Luft bestätigen, dass dem Gerät alle erforderlichen Flächen bekannt sind.</span><span class="sxs-lookup"><span data-stu-id="84cd4-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="84cd4-112">Erstellen Sie eine benutzerdefinierte Erkundungserfahrung in ihrer eigenen Anwendung.</span><span class="sxs-lookup"><span data-stu-id="84cd4-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="84cd4-113">In all diesen Fällen werden die tatsächlichen Daten, die während der Untersuchung gesammelt werden, vom System gespeichert, und die Anwendung muss dies nicht tun.</span><span class="sxs-lookup"><span data-stu-id="84cd4-113">In all these cases, the actual data gathered during the exploration is stored by the system and the application doesn't need to do this.</span></span> <span data-ttu-id="84cd4-114">Wenn Sie die Raumscanvisualisierung in Aktion sehen möchten, sehen Sie sich unsere Videodemo **Designing Holograms - Spatial Awareness** (Entwerfen von Hologrammen – räumliche Wahrnehmung) weiter unten an:</span><span class="sxs-lookup"><span data-stu-id="84cd4-114">If you'd like to see room scan visualization in action, check out our **Designing Holograms - Spatial Awareness** video demo below:</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

<span data-ttu-id="84cd4-115">*Dieses Video wurde aus der App "Entwerfen von Hologrammen" HoloLens 2 aufgenommen. Laden Sie hier herunter, und profitieren Sie [von der vollständigen Erfahrung.](https://aka.ms/dhapp)*</span><span class="sxs-lookup"><span data-stu-id="84cd4-115">*This video was taken from the "Designing Holograms" HoloLens 2 app. Download and enjoy the full experience [here](https://aka.ms/dhapp).*</span></span>

## <a name="device-support"></a><span data-ttu-id="84cd4-116">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="84cd4-116">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="84cd4-117"><strong>Feature</strong></span><span class="sxs-lookup"><span data-stu-id="84cd4-117"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="84cd4-118"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="84cd4-118"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="84cd4-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="84cd4-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="84cd4-120">Raumabtastvisualisierung</span><span class="sxs-lookup"><span data-stu-id="84cd4-120">Room scan visualization</span></span></td>
        <td><span data-ttu-id="84cd4-121">✔️</span><span class="sxs-lookup"><span data-stu-id="84cd4-121">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="84cd4-122">Erstellen einer benutzerdefinierten Überprüfungserfahrung</span><span class="sxs-lookup"><span data-stu-id="84cd4-122">Building a custom scanning experience</span></span>

<span data-ttu-id="84cd4-123">Anwendungen können die räumlichen Zuordnungsdaten zu Beginn der Benutzeroberfläche analysieren, um zu beurteilen, ob der Benutzer zusätzliche Schritte ausführen soll, um seine Vollständigkeit und Qualität zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="84cd4-123">Applications may analyze the spatial mapping data at the start of the experience to judge whether they want the user to do extra steps to improve its completeness and quality.</span></span> <span data-ttu-id="84cd4-124">Wenn die Analyse darauf hindeutet, dass die Qualität verbessert werden sollte, sollten Entwickler eine Visualisierung bereitstellen, die der Welt überlagert werden soll, um Anzugeben:</span><span class="sxs-lookup"><span data-stu-id="84cd4-124">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="84cd4-125">Wie viel des Gesamtvolumens in der Umgebung der Benutzer muss teil der Erfahrung sein?</span><span class="sxs-lookup"><span data-stu-id="84cd4-125">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="84cd4-126">Wo sollte der Benutzer die Daten verbessern?</span><span class="sxs-lookup"><span data-stu-id="84cd4-126">Where the user should go to improve data</span></span>

<span data-ttu-id="84cd4-127">Benutzer wissen nicht, was einen "guten" Scan ausmacht.</span><span class="sxs-lookup"><span data-stu-id="84cd4-127">Users don't know what makes a "good" scan.</span></span> <span data-ttu-id="84cd4-128">Sie müssen angezeigt oder informiert werden, wonach sie suchen müssen, wenn sie aufgefordert werden, einen Scan auszuwerten – Flachkeit, Abstand von tatsächlichen Wänden usw.</span><span class="sxs-lookup"><span data-stu-id="84cd4-128">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, and so on.</span></span> <span data-ttu-id="84cd4-129">Der Entwickler sollte eine Feedbackschleife implementieren, die das Aktualisieren der räumlichen Zuordnungsdaten während der Überprüfungs- oder Untersuchungsphase einschließt.</span><span class="sxs-lookup"><span data-stu-id="84cd4-129">The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="84cd4-130">In vielen Fällen ist es am besten, dem Benutzer mitzuteilen, was er tun muss, um die erforderliche Scanqualität zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="84cd4-130">In many cases, it's best to tell the user what they need to do to get the necessary scan quality.</span></span> <span data-ttu-id="84cd4-131">Sehen Sie sich z. B. die Obergrenze an, sehen Sie sich die Hintergründe an, und so weiter.</span><span class="sxs-lookup"><span data-stu-id="84cd4-131">For example, look at the ceiling, look behind furniture, and so on.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="84cd4-132">Zwischengespeicherte und kontinuierliche räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="84cd4-132">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="84cd4-133">Die räumlichen Zuordnungsdaten sind die datenquellenanwendungen mit der höchsten Gewichtung, die sie nutzen können.</span><span class="sxs-lookup"><span data-stu-id="84cd4-133">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="84cd4-134">Um Leistungsprobleme wie gelöschte Frames oder Stuttern zu vermeiden, sollte die Nutzung dieser Daten sorgfältig durchgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="84cd4-134">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="84cd4-135">Aktive Überprüfungen während einer Benutzeroberfläche können sowohl vorteilhaft als auch schädlich sein, sodass Sie basierend auf der Benutzeroberfläche entscheiden müssen, welche Methode verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="84cd4-135">Active scanning during an experience can be both beneficial and detrimental, so you'll need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="84cd4-136">Zwischengespeicherte räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="84cd4-136">Cached spatial mapping</span></span>

<span data-ttu-id="84cd4-137">Wenn zwischengespeicherte räumliche Zuordnungsdaten vorhanden sind, erstellt die Anwendung in der Regel eine Momentaufnahme der räumlichen Zuordnungsdaten und verwendet diese Momentaufnahme während der Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="84cd4-137">If there's cached spatial mapping data, the application typically takes a snapshot of the spatial mapping data and uses this snapshot during the experience.</span></span>

<span data-ttu-id="84cd4-138">**Vorteile**</span><span class="sxs-lookup"><span data-stu-id="84cd4-138">**Benefits**</span></span>
* <span data-ttu-id="84cd4-139">Reduzierter Mehraufwand für das System, während die Benutzeroberfläche ausgeführt wird, was zu erheblichen Leistungssteigerungen bei Leistung, Wärme und CPU führt.</span><span class="sxs-lookup"><span data-stu-id="84cd4-139">Reduced overhead on the system while the experience is running leading to dramatic power, thermal, and cpu performance gains.</span></span>
* <span data-ttu-id="84cd4-140">Eine einfachere Implementierung der Haupterfahrung, da sie nicht durch Änderungen in den räumlichen Daten unterbrochen wird.</span><span class="sxs-lookup"><span data-stu-id="84cd4-140">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="84cd4-141">Einmalige Kosten für jede Nachverarbeitung der räumlichen Daten zu Physikalischen, Grafik- und anderen Zwecken.</span><span class="sxs-lookup"><span data-stu-id="84cd4-141">A single one time cost on any post processing of the spatial data for physics, graphics, and other purposes.</span></span>

<span data-ttu-id="84cd4-142">**Nachteile**</span><span class="sxs-lookup"><span data-stu-id="84cd4-142">**Drawbacks**</span></span>
* <span data-ttu-id="84cd4-143">Die Bewegung von realen Objekten oder Personen wird nicht durch die zwischengespeicherten Daten widergespiegelt.</span><span class="sxs-lookup"><span data-stu-id="84cd4-143">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="84cd4-144">Beispielsweise könnte die Anwendung eine Tür öffnen, wenn sie jetzt geschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="84cd4-144">for example, the application might consider a door open when it's closed now.</span></span>
* <span data-ttu-id="84cd4-145">Potenziell mehr Anwendungsspeicher, um die zwischengespeicherte Version der Daten zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="84cd4-145">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="84cd4-146">Ein guter Fall für diese Methode ist eine kontrollierte Umgebung oder ein Tabellen-Top-Spiel.</span><span class="sxs-lookup"><span data-stu-id="84cd4-146">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="84cd4-147">Kontinuierliche räumliche Zuordnung</span><span class="sxs-lookup"><span data-stu-id="84cd4-147">Continuous spatial mapping</span></span>

<span data-ttu-id="84cd4-148">Bei bestimmten Anwendungen wird die Überprüfung möglicherweise fortgesetzt, um räumliche Zuordnungsdaten zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="84cd4-148">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="84cd4-149">**Vorteile**</span><span class="sxs-lookup"><span data-stu-id="84cd4-149">**Benefits**</span></span>
* <span data-ttu-id="84cd4-150">Sie müssen keine separate Überprüfungs- oder Untersuchungserfahrung im Voraus in Ihrer Anwendung erstellen.</span><span class="sxs-lookup"><span data-stu-id="84cd4-150">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="84cd4-151">Die Bewegung realer Objekte kann durch das Spiel widergespiegelt werden, allerdings mit einiger Verzögerung.</span><span class="sxs-lookup"><span data-stu-id="84cd4-151">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="84cd4-152">**Nachteile**</span><span class="sxs-lookup"><span data-stu-id="84cd4-152">**Drawbacks**</span></span>
* <span data-ttu-id="84cd4-153">Höhere Komplexität bei der Implementierung der Haupterfahrung.</span><span class="sxs-lookup"><span data-stu-id="84cd4-153">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="84cd4-154">Potenzieller Mehraufwand durch die zusätzliche grafik- und physikalische Verarbeitung, da Änderungen inkrementell von diesen Systemen aufgenommen werden müssen.</span><span class="sxs-lookup"><span data-stu-id="84cd4-154">Potential overhead from the extra graphic and physics processing, as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="84cd4-155">Höhere Leistung, wärmer und CPU-Auswirkungen.</span><span class="sxs-lookup"><span data-stu-id="84cd4-155">Higher power, thermal, and CPU impact.</span></span>

<span data-ttu-id="84cd4-156">Ein guter Fall für diese Methode ist, dass Hologramme mit bewegten Objekten interagieren sollen, z. B. ein holografisches Auto, das auf dem Boden fährt, je nachdem, ob es offen oder geschlossen ist, auf eine Tür stoßen möchte.</span><span class="sxs-lookup"><span data-stu-id="84cd4-156">A good case for this method is one where holograms are expected to interact with moving objects, for example, a holographic car that drives on the floor may want to bump into a door depending on whether it's open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="84cd4-157">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="84cd4-157">See also</span></span>

* [<span data-ttu-id="84cd4-158">Räumliche Abbildung</span><span class="sxs-lookup"><span data-stu-id="84cd4-158">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="84cd4-159">Koordinatensysteme</span><span class="sxs-lookup"><span data-stu-id="84cd4-159">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="84cd4-160">Raumklangentwurf</span><span class="sxs-lookup"><span data-stu-id="84cd4-160">Spatial sound design</span></span>](spatial-sound-design.md)