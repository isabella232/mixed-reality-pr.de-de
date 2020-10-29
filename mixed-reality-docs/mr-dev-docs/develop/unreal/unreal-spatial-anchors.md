---
title: Lokale Raumanker in Unreal
description: Leitfaden für die Verwendung von Raumankern in Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, Features, Dokumentation, Leitfäden, Hologramme, Raumanker
ms.openlocfilehash: d223c451cbbf0fb4e2cc1392394d2fe771ec8069
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2020
ms.locfileid: "91699085"
---
# <a name="local-spatial-anchors-in-unreal"></a><span data-ttu-id="dc2c5-104">Lokale Raumanker in Unreal</span><span class="sxs-lookup"><span data-stu-id="dc2c5-104">Local Spatial Anchors in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="dc2c5-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="dc2c5-105">Overview</span></span>

<span data-ttu-id="dc2c5-106">Raumanker werden verwendet, um Hologramme zwischen Anwendungssitzungen im realen Raum zu speichern.</span><span class="sxs-lookup"><span data-stu-id="dc2c5-106">Spatial anchors are used to save holograms in real-world space between application sessions.</span></span> <span data-ttu-id="dc2c5-107">Diese werden über Unreal mithilfe von **ARPin** s angezeigt und im Ankerspeicher von HoloLens gespeichert, der in zukünftigen Sitzungen geladen wird.</span><span class="sxs-lookup"><span data-stu-id="dc2c5-107">These get surfaced through Unreal as **ARPin** s and saved in the HoloLens’ anchor store, which is loaded in future sessions.</span></span> <span data-ttu-id="dc2c5-108">Lokale Anker eignen sich ideal als Fallback, wenn keine Internetverbindung vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="dc2c5-108">Local anchors are ideal as a fallback when there is no internet connectivity.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dc2c5-109">Lokale Anker werden auf dem Gerät gespeichert, während Azure-Raumanker in der Cloud gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="dc2c5-109">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="dc2c5-110">Wenn Sie Azure Cloud Services zum Speichern Ihrer Anker verwenden möchten, verfügen wir über ein Dokument, in dem Sie durch den Integrationsprozess für [Azure-Raumanker](unreal-azure-spatial-anchors.md) geführt werden.</span><span class="sxs-lookup"><span data-stu-id="dc2c5-110">If you're looking to use Azure cloud services to store your anchors, we have a document that can walk you through integrating [Azure Spatial Anchors](unreal-azure-spatial-anchors.md).</span></span> <span data-ttu-id="dc2c5-111">Beachten Sie, dass Sie sowohl lokale als auch Azure-Anker im selben Projekt haben können, ohne dass Konflikte auftreten.</span><span class="sxs-lookup"><span data-stu-id="dc2c5-111">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="checking-the-anchor-store"></a><span data-ttu-id="dc2c5-112">Überprüfen des Ankerspeichers</span><span class="sxs-lookup"><span data-stu-id="dc2c5-112">Checking the anchor store</span></span>

<span data-ttu-id="dc2c5-113">Vor dem Speichern oder Laden von Ankern müssen Sie sich zunächst vergewissern, dass der Ankerspeicher bereit ist.</span><span class="sxs-lookup"><span data-stu-id="dc2c5-113">Before saving or loading anchors, you need to check if the anchor store is ready.</span></span>  <span data-ttu-id="dc2c5-114">Versuche, eine der HoloLens-Ankerfunktionen aufzurufen, bevor der Ankerspeicher bereit ist, sind nicht erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="dc2c5-114">Calling any of the HoloLens anchor functions before the anchor store is ready will not succeed.</span></span>  

![Raumanker: Speicher bereit](images/unreal-spatialanchors-store-ready.PNG)

## <a name="saving-anchors"></a><span data-ttu-id="dc2c5-116">Speichern von Ankern</span><span class="sxs-lookup"><span data-stu-id="dc2c5-116">Saving anchors</span></span>

<span data-ttu-id="dc2c5-117">Sobald die Anwendung über eine Komponente verfügt, die in der Umgebung fixiert werden muss, kann sie wie folgt im Ankerspeicher gespeichert werden:</span><span class="sxs-lookup"><span data-stu-id="dc2c5-117">Once the application has a component that needs to be pinned to the world, it can be saved to the anchor store with the following sequence:</span></span> 

![Raumanker: Speichern](images/unreal-spatialanchors-save.PNG)

<span data-ttu-id="dc2c5-119">Das heißt im Einzelnen:</span><span class="sxs-lookup"><span data-stu-id="dc2c5-119">Breaking this down:</span></span>
1. <span data-ttu-id="dc2c5-120">Erzeugen Sie einen Akteur an einer bekannten Position.</span><span class="sxs-lookup"><span data-stu-id="dc2c5-120">Spawn an actor at a known location.</span></span>
2. <span data-ttu-id="dc2c5-121">Erstellen Sie einen **ARPin** mit dieser Position und einem Namen, der auf der Klasse des Akteurs basiert.</span><span class="sxs-lookup"><span data-stu-id="dc2c5-121">Create an **ARPin** with that location and a name based on the actor’s class.</span></span> 
3. <span data-ttu-id="dc2c5-122">Fügen Sie dem **ARPin** den Akteur hinzu, und speichern Sie den Pin im HoloLens-Ankerspeicher.</span><span class="sxs-lookup"><span data-stu-id="dc2c5-122">Add the actor to the **ARPin** and save the pin to the HoloLens anchor store.</span></span>  
    * <span data-ttu-id="dc2c5-123">Der gewählte Ankername muss eindeutig sein, in diesem Fall verwenden wir dafür den aktuellen Zeitstempel.</span><span class="sxs-lookup"><span data-stu-id="dc2c5-123">The anchor name you choose must be unique, which in this example is the current timestamp.</span></span> 

4. <span data-ttu-id="dc2c5-124">Wenn der Anker erfolgreich im Ankerspeicher gespeichert wurde, kann er im HoloLens-Geräteportal unter **System > Map manager > Anchor Files Saved On Device** (System > Zuordnungs-Manager > Auf dem Gerät gespeicherte Ankerdateien) überprüft werden.</span><span class="sxs-lookup"><span data-stu-id="dc2c5-124">If the anchor is successfully saved to the anchor store, you can be inspect it in the HoloLens device portal under **System > Map manager > Anchor Files Saved On Device** .</span></span> 

## <a name="loading-anchors"></a><span data-ttu-id="dc2c5-125">Laden von Ankern</span><span class="sxs-lookup"><span data-stu-id="dc2c5-125">Loading anchors</span></span>

<span data-ttu-id="dc2c5-126">Beim Start einer Anwendung können Sie die folgende Blaupause verwenden, um Komponenten an ihren Ankerpositionen wiederherzustellen:</span><span class="sxs-lookup"><span data-stu-id="dc2c5-126">When an application starts, you can use the following blueprint to restore components to their anchor locations:</span></span>

![Raumanker: Laden](images/unreal-spatialanchors-load.PNG)

<span data-ttu-id="dc2c5-128">Das heißt im Einzelnen:</span><span class="sxs-lookup"><span data-stu-id="dc2c5-128">Breaking this down:</span></span>
1. <span data-ttu-id="dc2c5-129">Iterieren Sie über alle Anker im Ankerspeicher.</span><span class="sxs-lookup"><span data-stu-id="dc2c5-129">Iterate over all of the anchors in the anchor store.</span></span> 
2. <span data-ttu-id="dc2c5-130">Erzeugen Sie einen Akteur an einem neutralen Element.</span><span class="sxs-lookup"><span data-stu-id="dc2c5-130">Spawn an actor at identity.</span></span>
3. <span data-ttu-id="dc2c5-131">Heften Sie diesen Akteur an den **ARPin** aus dem Ankerspeicher an.</span><span class="sxs-lookup"><span data-stu-id="dc2c5-131">Pin that actor to the **ARPin** from the anchor store.</span></span>  

    * <span data-ttu-id="dc2c5-132">Es ist wichtig, den Akteur am neutralen Element zu erzeugen, da der Anker dazu dient, das Hologramm in der Umgebung auf der Grundlage des gespeicherten Orts zu positionieren.</span><span class="sxs-lookup"><span data-stu-id="dc2c5-132">It's important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved.</span></span> <span data-ttu-id="dc2c5-133">Jede hier hinzugefügte Transformation fügt dem Anker einen Offset hinzu.</span><span class="sxs-lookup"><span data-stu-id="dc2c5-133">Any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="dc2c5-134">Die Anker-ID wird ebenfalls abgefragt, um abhängig vom gespeicherten Namen des Ankers unterschiedliche Akteure erzeugen zu können.</span><span class="sxs-lookup"><span data-stu-id="dc2c5-134">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="removing-anchors"></a><span data-ttu-id="dc2c5-135">Entfernen von Ankern</span><span class="sxs-lookup"><span data-stu-id="dc2c5-135">Removing anchors</span></span> 

<span data-ttu-id="dc2c5-136">Wenn Sie die Arbeit mit einem Anker beendet haben, können Sie einzelne Anker oder den gesamten Ankerspeicher mit den Komponenten **Remove ARPin from WMRAnchor Store** (ARPin aus WMRAnkerspeicher entfernen) und **Remove All ARPins from WMRAnchor Store** (Alle ARPins aus WMRAnkerspeicher entfernen) löschen.</span><span class="sxs-lookup"><span data-stu-id="dc2c5-136">When you're done with an anchor you can clear individual anchors or the entire anchor store with the **Remove ARPin from WMRAnchor Store** and **Remove All ARPins from WMRAnchor Store** components.</span></span>

![Raumanker: Entfernen](images/unreal-spatialanchors-remove.PNG)

> [!NOTE]
> <span data-ttu-id="dc2c5-138">Beachten Sie, dass Raumanker sich noch in der Betaphase befinden, prüfen Sie also unbedingt auf aktualisierte Informationen und Features.</span><span class="sxs-lookup"><span data-stu-id="dc2c5-138">Bear in mind that Spatial Anchors are still in Beta, so be sure to check back for updated information and features.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="dc2c5-139">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="dc2c5-139">Next Development Checkpoint</span></span>

<span data-ttu-id="dc2c5-140">Wenn Sie dem Weg der Unreal-Entwicklungsprüfpunkte folgen, den wir entworfen haben, befinden Sie sich mitten im Kennenlernen der MRTK-Grundbausteine.</span><span class="sxs-lookup"><span data-stu-id="dc2c5-140">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="dc2c5-141">Von hier aus können Sie mit dem nächsten Baustein fortfahren:</span><span class="sxs-lookup"><span data-stu-id="dc2c5-141">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="dc2c5-142">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="dc2c5-142">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)

<span data-ttu-id="dc2c5-143">Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:</span><span class="sxs-lookup"><span data-stu-id="dc2c5-143">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dc2c5-144">HoloLens-Kamera</span><span class="sxs-lookup"><span data-stu-id="dc2c5-144">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="dc2c5-145">Sie können jederzeit zu den [Prüfpunkten für die Unreal-Entwicklung](unreal-development-overview.md#2-core-building-blocks) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="dc2c5-145">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="dc2c5-146">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="dc2c5-146">See also</span></span>
* [<span data-ttu-id="dc2c5-147">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="dc2c5-147">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)
* [<span data-ttu-id="dc2c5-148">Raumanker</span><span class="sxs-lookup"><span data-stu-id="dc2c5-148">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="dc2c5-149">Koordinatensysteme</span><span class="sxs-lookup"><span data-stu-id="dc2c5-149">Coordinate systems</span></span>](../../design/coordinate-systems.md)
