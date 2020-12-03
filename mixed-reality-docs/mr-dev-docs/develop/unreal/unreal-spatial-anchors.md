---
title: Lokale Raumanker in Unreal
description: Leitfaden für die Verwendung von Raumankern in Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, Features, Dokumentation, Leitfäden, Hologramme, Raumanker, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 8be1521d44a9dda521c1570d3ac55955e475bc30
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354493"
---
# <a name="local-spatial-anchors-in-unreal"></a><span data-ttu-id="6cbb4-104">Lokale Raumanker in Unreal</span><span class="sxs-lookup"><span data-stu-id="6cbb4-104">Local Spatial Anchors in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="6cbb4-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="6cbb4-105">Overview</span></span>

<span data-ttu-id="6cbb4-106">Raumanker werden verwendet, um Hologramme zwischen Anwendungssitzungen im realen Raum zu speichern.</span><span class="sxs-lookup"><span data-stu-id="6cbb4-106">Spatial anchors are used to save holograms in real-world space between application sessions.</span></span> <span data-ttu-id="6cbb4-107">Diese werden über Unreal mithilfe von **ARPin** s angezeigt und im Ankerspeicher von HoloLens gespeichert, der in zukünftigen Sitzungen geladen wird.</span><span class="sxs-lookup"><span data-stu-id="6cbb4-107">These get surfaced through Unreal as **ARPin** s and saved in the HoloLens’ anchor store, which is loaded in future sessions.</span></span> <span data-ttu-id="6cbb4-108">Lokale Anker eignen sich ideal als Fallback, wenn keine Internetverbindung vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="6cbb4-108">Local anchors are ideal as a fallback when there is no internet connectivity.</span></span>

> [!NOTE]
> <span data-ttu-id="6cbb4-109">Ankerfunktionen aus UE 4.25 sind in 4.26 veraltet und sollten durch neuere ersetzt werden.</span><span class="sxs-lookup"><span data-stu-id="6cbb4-109">Anchor functions from UE 4.25 are obsolete in 4.26 and should be replaced with newer ones.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="6cbb4-110">Lokale Anker werden auf dem Gerät gespeichert, während Azure-Raumanker in der Cloud gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="6cbb4-110">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="6cbb4-111">Wenn Sie Azure Cloud Services zum Speichern Ihrer Anker verwenden möchten, verfügen wir über ein Dokument, in dem Sie durch den Integrationsprozess für [Azure-Raumanker](unreal-azure-spatial-anchors.md) geführt werden.</span><span class="sxs-lookup"><span data-stu-id="6cbb4-111">If you're looking to use Azure cloud services to store your anchors, we have a document that can walk you through integrating [Azure Spatial Anchors](unreal-azure-spatial-anchors.md).</span></span> <span data-ttu-id="6cbb4-112">Beachten Sie, dass Sie sowohl lokale als auch Azure-Anker im selben Projekt haben können, ohne dass Konflikte auftreten.</span><span class="sxs-lookup"><span data-stu-id="6cbb4-112">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="checking-the-anchor-store"></a><span data-ttu-id="6cbb4-113">Überprüfen des Ankerspeichers</span><span class="sxs-lookup"><span data-stu-id="6cbb4-113">Checking the anchor store</span></span>

<span data-ttu-id="6cbb4-114">Vor dem Speichern oder Laden von Ankern müssen Sie sich zunächst vergewissern, dass der Ankerspeicher bereit ist.</span><span class="sxs-lookup"><span data-stu-id="6cbb4-114">Before saving or loading anchors, you need to check if the anchor store is ready.</span></span>  <span data-ttu-id="6cbb4-115">Versuche, eine der HoloLens-Ankerfunktionen aufzurufen, bevor der Ankerspeicher bereit ist, sind nicht erfolgreich.</span><span class="sxs-lookup"><span data-stu-id="6cbb4-115">Calling any of the HoloLens anchor functions before the anchor store is ready will not succeed.</span></span>  

[!INCLUDE[](includes/tabs-sa-1.md)]

## <a name="saving-anchors"></a><span data-ttu-id="6cbb4-116">Speichern von Ankern</span><span class="sxs-lookup"><span data-stu-id="6cbb4-116">Saving anchors</span></span>

<span data-ttu-id="6cbb4-117">Sobald die Anwendung über eine Komponente verfügt, die in der Umgebung fixiert werden muss, kann sie wie folgt im Ankerspeicher gespeichert werden:</span><span class="sxs-lookup"><span data-stu-id="6cbb4-117">Once the application has a component that needs to be pinned to the world, it can be saved to the anchor store with the following sequence:</span></span> 

[!INCLUDE[](includes/tabs-sa-2.md)]

<span data-ttu-id="6cbb4-118">Das heißt im Einzelnen:</span><span class="sxs-lookup"><span data-stu-id="6cbb4-118">Breaking this down:</span></span>
1. <span data-ttu-id="6cbb4-119">Erzeugen Sie einen Akteur an einer bekannten Position.</span><span class="sxs-lookup"><span data-stu-id="6cbb4-119">Spawn an actor at a known location.</span></span>
2. <span data-ttu-id="6cbb4-120">Erstellen Sie einen **ARPin** mit dieser Position und einem Namen, der auf der Klasse des Akteurs basiert.</span><span class="sxs-lookup"><span data-stu-id="6cbb4-120">Create an **ARPin** with that location and a name based on the actor’s class.</span></span> 
3. <span data-ttu-id="6cbb4-121">Fügen Sie dem **ARPin** den Akteur hinzu, und speichern Sie den Pin im HoloLens-Ankerspeicher.</span><span class="sxs-lookup"><span data-stu-id="6cbb4-121">Add the actor to the **ARPin** and save the pin to the HoloLens anchor store.</span></span>  
    * <span data-ttu-id="6cbb4-122">Der gewählte Ankername muss eindeutig sein, in diesem Fall verwenden wir dafür den aktuellen Zeitstempel.</span><span class="sxs-lookup"><span data-stu-id="6cbb4-122">The anchor name you choose must be unique, which in this example is the current timestamp.</span></span> 

4. <span data-ttu-id="6cbb4-123">Wenn der Anker erfolgreich im Ankerspeicher gespeichert wurde, kann er im HoloLens-Geräteportal unter **System > Map manager > Anchor Files Saved On Device** (System > Zuordnungs-Manager > Auf dem Gerät gespeicherte Ankerdateien) überprüft werden.</span><span class="sxs-lookup"><span data-stu-id="6cbb4-123">If the anchor is successfully saved to the anchor store, you can be inspect it in the HoloLens device portal under **System > Map manager > Anchor Files Saved On Device**.</span></span> 

## <a name="loading-anchors"></a><span data-ttu-id="6cbb4-124">Laden von Ankern</span><span class="sxs-lookup"><span data-stu-id="6cbb4-124">Loading anchors</span></span>

<span data-ttu-id="6cbb4-125">Beim Start einer Anwendung können Sie die folgende Blaupause verwenden, um Komponenten an ihren Ankerpositionen wiederherzustellen:</span><span class="sxs-lookup"><span data-stu-id="6cbb4-125">When an application starts, you can use the following blueprint to restore components to their anchor locations:</span></span>

[!INCLUDE[](includes/tabs-sa-3.md)]

<span data-ttu-id="6cbb4-126">Das heißt im Einzelnen:</span><span class="sxs-lookup"><span data-stu-id="6cbb4-126">Breaking this down:</span></span>
1. <span data-ttu-id="6cbb4-127">Iterieren Sie über alle Anker im Ankerspeicher.</span><span class="sxs-lookup"><span data-stu-id="6cbb4-127">Iterate over all of the anchors in the anchor store.</span></span> 
2. <span data-ttu-id="6cbb4-128">Erzeugen Sie einen Akteur an einem neutralen Element.</span><span class="sxs-lookup"><span data-stu-id="6cbb4-128">Spawn an actor at identity.</span></span>
3. <span data-ttu-id="6cbb4-129">Heften Sie diesen Akteur an den **ARPin** aus dem Ankerspeicher an.</span><span class="sxs-lookup"><span data-stu-id="6cbb4-129">Pin that actor to the **ARPin** from the anchor store.</span></span>  

    * <span data-ttu-id="6cbb4-130">Es ist wichtig, den Akteur am neutralen Element zu erzeugen, da der Anker dazu dient, das Hologramm in der Umgebung auf der Grundlage des gespeicherten Orts zu positionieren.</span><span class="sxs-lookup"><span data-stu-id="6cbb4-130">It's important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved.</span></span> <span data-ttu-id="6cbb4-131">Jede hier hinzugefügte Transformation fügt dem Anker einen Offset hinzu.</span><span class="sxs-lookup"><span data-stu-id="6cbb4-131">Any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="6cbb4-132">Die Anker-ID wird ebenfalls abgefragt, um abhängig vom gespeicherten Namen des Ankers unterschiedliche Akteure erzeugen zu können.</span><span class="sxs-lookup"><span data-stu-id="6cbb4-132">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="removing-anchors"></a><span data-ttu-id="6cbb4-133">Entfernen von Ankern</span><span class="sxs-lookup"><span data-stu-id="6cbb4-133">Removing anchors</span></span> 

<span data-ttu-id="6cbb4-134">Wenn Sie die Arbeit mit einem Anker beendet haben, können Sie einzelne Anker oder den gesamten Ankerspeicher mit den Komponenten **Remove ARPin from WMRAnchor Store** (ARPin aus WMRAnkerspeicher entfernen) und **Remove All ARPins from WMRAnchor Store** (Alle ARPins aus WMRAnkerspeicher entfernen) löschen.</span><span class="sxs-lookup"><span data-stu-id="6cbb4-134">When you're done with an anchor you can clear individual anchors or the entire anchor store with the **Remove ARPin from WMRAnchor Store** and **Remove All ARPins from WMRAnchor Store** components.</span></span>

[!INCLUDE[](includes/tabs-sa-4.md)]

> [!NOTE]
> <span data-ttu-id="6cbb4-135">Beachten Sie, dass Raumanker sich noch in der Betaphase befinden, prüfen Sie also unbedingt auf aktualisierte Informationen und Features.</span><span class="sxs-lookup"><span data-stu-id="6cbb4-135">Bear in mind that Spatial Anchors are still in Beta, so be sure to check back for updated information and features.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="6cbb4-136">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="6cbb4-136">Next Development Checkpoint</span></span>

<span data-ttu-id="6cbb4-137">Wenn Sie dem Weg der Unreal-Entwicklungsprüfpunkte folgen, den wir entworfen haben, befinden Sie sich mitten im Kennenlernen der MRTK-Grundbausteine.</span><span class="sxs-lookup"><span data-stu-id="6cbb4-137">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="6cbb4-138">Von hier aus können Sie mit dem nächsten Baustein fortfahren:</span><span class="sxs-lookup"><span data-stu-id="6cbb4-138">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="6cbb4-139">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="6cbb4-139">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)

<span data-ttu-id="6cbb4-140">Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:</span><span class="sxs-lookup"><span data-stu-id="6cbb4-140">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6cbb4-141">HoloLens-Kamera</span><span class="sxs-lookup"><span data-stu-id="6cbb4-141">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="6cbb4-142">Sie können jederzeit zu den [Prüfpunkten für die Unreal-Entwicklung](unreal-development-overview.md#2-core-building-blocks) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="6cbb4-142">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="6cbb4-143">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="6cbb4-143">See also</span></span>
* [<span data-ttu-id="6cbb4-144">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="6cbb4-144">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)
* [<span data-ttu-id="6cbb4-145">Raumanker</span><span class="sxs-lookup"><span data-stu-id="6cbb4-145">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="6cbb4-146">Koordinatensysteme</span><span class="sxs-lookup"><span data-stu-id="6cbb4-146">Coordinate systems</span></span>](../../design/coordinate-systems.md)
