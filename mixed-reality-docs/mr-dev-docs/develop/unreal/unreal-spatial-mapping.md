---
title: Räumliche Abbildung in Unreal
description: Leitfaden für die Verwendung der räumlichen Abbildung in Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, Features, Dokumentation, Leitfäden, Hologramme, räumliche Abbildung, Mixed Reality-Headset Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 878eae5f5fd0b7a1630511faa23c1477455ed988
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354376"
---
# <a name="spatial-mapping-in-unreal"></a><span data-ttu-id="4a291-104">Räumliche Abbildung in Unreal</span><span class="sxs-lookup"><span data-stu-id="4a291-104">Spatial Mapping in Unreal</span></span>

<span data-ttu-id="4a291-105">Die räumliche Abbildung ermöglicht es, durch Anzeigen der die HoloLens umgebenden Welt Objekte auf Oberflächen in der physischen Welt zu platzieren. Dadurch erscheinen Hologramme für den Benutzer realer.</span><span class="sxs-lookup"><span data-stu-id="4a291-105">Spatial mapping makes it possible to place objects on surfaces in the physical world by showing the world around the HoloLens, which makes holograms seem more real to the user.</span></span> <span data-ttu-id="4a291-106">Die räumliche Abbildung verankert darüber hinaus Objekte in der Welt des Benutzers und nutzt dazu Tiefeninformationen der realen Welt. Dies hilft dabei, den Benutzer zu überzeugen, dass sich die betreffenden Hologramme tatsächlich in seinem Bereich befinden; frei im Raum schwebende oder sich mit dem Benutzer bewegende Hologramme fühlen sich weniger real an.</span><span class="sxs-lookup"><span data-stu-id="4a291-106">Spatial mapping also anchors objects in the user's world by taking advantage of real world depth cues. This helps convince the user that these holograms are actually in their space; holograms floating in space or moving with the user will not feel as real.</span></span> <span data-ttu-id="4a291-107">Wann immer es möglich ist, sollten Sie Elemente platzieren, um das Wohlbefinden des Benutzers zu steigern.</span><span class="sxs-lookup"><span data-stu-id="4a291-107">You want to place items for comfort whenever possible.</span></span>

<span data-ttu-id="4a291-108">Weitere Informationen zur Qualität der räumlichen Abbildung, Platzierung, Verdeckung, Rendering und mehr finden Sie im Dokument [Räumliche Abbildung](../../design/spatial-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="4a291-108">You can find more information on spatial mapping quality, placement, occlusion, rendering, and more, in the [Spatial mapping](../../design/spatial-mapping.md) document.</span></span>

## <a name="enabling-spatial-mapping"></a><span data-ttu-id="4a291-109">Aktivieren der räumlichen Abbildung</span><span class="sxs-lookup"><span data-stu-id="4a291-109">Enabling Spatial Mapping</span></span>

<span data-ttu-id="4a291-110">So aktivieren Sie die räumliche Abbildung in HoloLens:</span><span class="sxs-lookup"><span data-stu-id="4a291-110">To enable spatial mapping on HoloLens:</span></span>
- <span data-ttu-id="4a291-111">Öffnen Sie **Edit > Project Settings** (Bearbeiten > Projekteinstellungen), und scrollen Sie zum Abschnitt **Platforms** (Plattformen) herunter.</span><span class="sxs-lookup"><span data-stu-id="4a291-111">Open **Edit > Project Settings** and scroll down to the **Platforms** section.</span></span>    
    + <span data-ttu-id="4a291-112">Wählen Sie **HoloLens** aus, und aktivieren Sie **Spatial Perception** (Räumliche Wahrnehmung).</span><span class="sxs-lookup"><span data-stu-id="4a291-112">Select **HoloLens** and check **Spatial Perception**.</span></span>

![Screenshot der HoloLens-Funktionalität für Projekteinstellungen mit hervorgehobener Option zur räumlichen Abbildung](images/unreal-spatial-mapping-img-01.png)

<span data-ttu-id="4a291-114">So abonnieren Sie räumliche Abbildung und debuggen das **MRMesh** in einem HoloLens-Spiel:</span><span class="sxs-lookup"><span data-stu-id="4a291-114">To opt into spatial mapping and debug the **MRMesh** in a HoloLens game:</span></span>
1. <span data-ttu-id="4a291-115">Öffnen Sie die **ARSessionConfig**, und klappen Sie den Abschnitt **ARSettings > World Mapping** (Weltdarstellung) auf.</span><span class="sxs-lookup"><span data-stu-id="4a291-115">Open the **ARSessionConfig** and expand the **ARSettings > World Mapping** section.</span></span> 

2. <span data-ttu-id="4a291-116">Aktivieren Sie **Generate Mesh Data from Tracked Geometry** (Daten des Gittermodells auf der Grundlage der nachverfolgten Geometrie generieren), wodurch das HoloLens-Plug-In angewiesen wird, mit dem asynchronen Abrufen von räumlichen Abbildungsdaten und ihrer Oberflächenzuordnung in Unreal mithilfe von **MRMesh** zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="4a291-116">Check **Generate Mesh Data from Tracked Geometry**, which tells the HoloLens plugin to start asynchronously getting spatial mapping data and surface it to Unreal through the **MRMesh**.</span></span> 
3. <span data-ttu-id="4a291-117">Aktivieren Sie **Render Mesh Data in Wireframe** (Gittermodelldaten im Drahtmodell rendern), um einen weißen Drahtmodellumriss jedes Dreiecks im **MRMesh** darzustellen.</span><span class="sxs-lookup"><span data-stu-id="4a291-117">Check **Render Mesh Data in Wireframe** to show a white wireframe outline of every triangle in the **MRMesh**.</span></span> 

![Raumanker: Speicher bereit](images/unreal-spatialmapping-arsettings.PNG)


## <a name="spatial-mapping-at-runtime"></a><span data-ttu-id="4a291-119">Räumliche Abbildung zur Laufzeit</span><span class="sxs-lookup"><span data-stu-id="4a291-119">Spatial Mapping at runtime</span></span>
<span data-ttu-id="4a291-120">Sie können die folgenden Parameter ändern, um das Laufzeitverhalten der räumlichen Abbildung zu ändern:</span><span class="sxs-lookup"><span data-stu-id="4a291-120">You can modify the following parameters to update the spatial mapping runtime behavior:</span></span>

- <span data-ttu-id="4a291-121">Öffnen Sie **Edit > Project Settings** (Bearbeiten > Projekteinstellungen), scrollen Sie nach unten zum Abschnitt **Platforms** (Plattformen), und wählen Sie **HoloLens > Spatial Mapping** (HoloLens > Räumliche Abbildung) aus:</span><span class="sxs-lookup"><span data-stu-id="4a291-121">Open **Edit > Project Settings**, scroll down to the **Platforms** section and select **HoloLens > Spatial Mapping**:</span></span> 

![Raumanker: Projekteinstellungen](images/unreal-spatialmapping-projectsettings.PNG)

- <span data-ttu-id="4a291-123">**Max Triangles Per Cubic Meter** (Maximale Anzahl von Dreiecken pro Kubikmeter) dient zum Aktualisieren der Dichte der Dreiecke im Gitter der räumlichen Abbildung.</span><span class="sxs-lookup"><span data-stu-id="4a291-123">**Max Triangles Per Cubic Meter** updates the density of the triangles in the spatial mapping mesh.</span></span>  
- <span data-ttu-id="4a291-124">**Spatial Meshing Volume Size** (Volumengröße des räumlichen Gitters) dient zum Angeben der Größe des Würfels, der den Spieler umgibt, um Daten der räumlichen Abbildung zu rendern und zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="4a291-124">**Spatial Meshing Volume Size** is the size of the cube around the player to render and update spatial mapping data.</span></span>  
    + <span data-ttu-id="4a291-125">Im Falle einer großen Anwendungslaufzeitumgebung muss dieser Wert ggf. hoch sein, um dem realen Raum gerecht zu werden.</span><span class="sxs-lookup"><span data-stu-id="4a291-125">If the expected application runtime environment is expected to be large, this value may need to be large to match the real-world space.</span></span>  <span data-ttu-id="4a291-126">Dagegen kann dieser Wert kleiner sein, wenn die Anwendung lediglich Hologramme auf Oberflächen in der unmittelbareren Umgebung des Benutzers platzieren muss.</span><span class="sxs-lookup"><span data-stu-id="4a291-126">On the other hand, this value can be smaller if the application only needs to place holograms on surfaces immediately around the user.</span></span> <span data-ttu-id="4a291-127">Wenn sich der Benutzer in der Umgebung bewegt, bewegt sich das Volumen der räumlichen Abbildung mit ihm mit.</span><span class="sxs-lookup"><span data-stu-id="4a291-127">As the user walks around the world, the spatial mapping volume will move with them.</span></span> 

## <a name="working-with-mrmesh"></a><span data-ttu-id="4a291-128">Arbeiten mit MRMesh</span><span class="sxs-lookup"><span data-stu-id="4a291-128">Working with MRMesh</span></span>

<span data-ttu-id="4a291-129">Zunächst müssen Sie die räumliche Abbildung starten:</span><span class="sxs-lookup"><span data-stu-id="4a291-129">First, you need to start Spatial Mapping:</span></span>

![Blaupause der Funktion „ToggleARCapture“ mit hervorgehobenem Erfassungstyp für räumliche Abbildung](images/unreal-spatial-mapping-img-02.png)

<span data-ttu-id="4a291-131">Nachdem die räumliche Abbildung für den Raum erfasst wurde, empfehlen wir, die räumliche Abbildung zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="4a291-131">Once spatial mapping has been captured for the space, we recommend toggling spatial mapping off.</span></span>  <span data-ttu-id="4a291-132">Die räumliche Abbildung kann entweder nach einer bestimmten Zeitspanne abgeschlossen sein, oder wenn Raycasts in jede Richtung Kollisionen mit dem MRMesh zurückgeben.</span><span class="sxs-lookup"><span data-stu-id="4a291-132">The spatial mapping may be completed either after a certain amount of time, or when raycasts in each direction return collisions against the MRMesh.</span></span>

<span data-ttu-id="4a291-133">So erhalten Sie zur Laufzeit Zugriff auf das **MRMesh**:</span><span class="sxs-lookup"><span data-stu-id="4a291-133">To get access to the **MRMesh** at runtime:</span></span>
1. <span data-ttu-id="4a291-134">Fügen Sie einem Blaupausenakteur eine **ARTrackableNotify**-Komponente hinzu.</span><span class="sxs-lookup"><span data-stu-id="4a291-134">Add an **ARTrackableNotify** Component to a Blueprint actor.</span></span> 

![Raumanker: In AR nachverfolgbare Benachrichtigung](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="4a291-136">Wählen Sie die **ARTrackableNotify**-Komponente aus, und klappen Sie im Bereich **Details** den Abschnitt **Events** (Ereignisse) auf.</span><span class="sxs-lookup"><span data-stu-id="4a291-136">Select the **ARTrackableNotify** component and expand the **Events** section in the **Details** panel.</span></span> 
    - <span data-ttu-id="4a291-137">Klicken Sie auf die Schaltfläche **+** für die Ereignisse, die Sie überwachen möchten.</span><span class="sxs-lookup"><span data-stu-id="4a291-137">Click the **+** button on the events you want to monitor.</span></span> 

![Raumanker: Ereignisse](images/unreal-spatialmapping-events.PNG)

<span data-ttu-id="4a291-139">In diesem Fall wird das Ereignis **On Add Tracked Geometry** überwacht, das nach gültigen Gittermodellen der Realumgebung sucht, die mit Daten der räumlichen Abbildung übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="4a291-139">In this case, the **On Add Tracked Geometry** event is being monitored, which looks for valid world meshes matching to spatial mapping data.</span></span> <span data-ttu-id="4a291-140">Die vollständige Liste der Ereignisse finden Sie in der Komponenten-API [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html).</span><span class="sxs-lookup"><span data-stu-id="4a291-140">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span> 

<span data-ttu-id="4a291-141">Sie können das Material des Gittermodells im Ereignisdiagramm der Blaupause oder in C++ ändern.</span><span class="sxs-lookup"><span data-stu-id="4a291-141">You can change the mesh’s material in the Blueprint Event Graph or in C++.</span></span> <span data-ttu-id="4a291-142">Auf dem Screenshot unten ist die Route der Blaupause dargestellt:</span><span class="sxs-lookup"><span data-stu-id="4a291-142">The screenshot below shows the Blueprint route:</span></span> 

![Raumanker: Beispiel](images/unreal-spatialmapping-example.PNG)

## <a name="spatial-mapping-in-c"></a><span data-ttu-id="4a291-144">Räumliche Abbildung in C++</span><span class="sxs-lookup"><span data-stu-id="4a291-144">Spatial Mapping in C++</span></span>

<span data-ttu-id="4a291-145">Fügen Sie in der build.cs-Datei Ihres Spiels **AugmentedReality** und **MRMesh** zur Liste „PublicDependencyModuleNames“ hinzu:</span><span class="sxs-lookup"><span data-stu-id="4a291-145">In your game's build.cs file, add **AugmentedReality** and **MRMesh** to the PublicDependencyModuleNames list:</span></span>

```cpp
PublicDependencyModuleNames.AddRange(
    new string[] {
        "Core",
        "CoreUObject",
        "Engine",
        "InputCore",    
        "EyeTracker",
        "AugmentedReality",
        "MRMesh"
});
```

<span data-ttu-id="4a291-146">Abonnieren Sie zum Zugriff auf das MRMesh die **OnTrackableAdded**-Delegaten:</span><span class="sxs-lookup"><span data-stu-id="4a291-146">To access the MRMesh, subscribe to the **OnTrackableAdded** delegates:</span></span>

```cpp
#include "ARBlueprintLibrary.h"
#include "MRMeshComponent.h"

void AARTrackableMonitor::BeginPlay()
{
    Super::BeginPlay();

    // Subscribe to Tracked Geometry delegates
    UARBlueprintLibrary::AddOnTrackableAddedDelegate_Handle(
        FOnTrackableAddedDelegate::CreateUObject(this, &AARTrackableMonitor::OnTrackableAdded)
    );
}

void AARTrackableMonitor::OnTrackableAdded(UARTrackedGeometry* Added)
{
    // When tracked geometry is received, check that it's from spatial mapping
    if(Added->GetObjectClassification() == EARObjectClassification::World)
    {
        UMRMeshComponent* MRMesh = Added->GetUnderlyingMesh();
    }
}
```

> [!NOTE]
> <span data-ttu-id="4a291-147">Es gibt ähnliche Delegaten für aktualisierte und entfernte Ereignisse, **AddOnTrackableUpdatedDelegate_Handle** bzw. **AddOnTrackableRemovedDelegate_Handle**.</span><span class="sxs-lookup"><span data-stu-id="4a291-147">There are similar delegates for updated and removed events, **AddOnTrackableUpdatedDelegate_Handle** and **AddOnTrackableRemovedDelegate_Handle** respectively.</span></span>
>
> <span data-ttu-id="4a291-148">Die vollständige Liste der Ereignisse finden Sie in der Komponenten-API [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html).</span><span class="sxs-lookup"><span data-stu-id="4a291-148">You can find the full list of events in the [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html) API.</span></span>

## <a name="see-also"></a><span data-ttu-id="4a291-149">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="4a291-149">See also</span></span>
* [<span data-ttu-id="4a291-150">Räumliche Abbildung</span><span class="sxs-lookup"><span data-stu-id="4a291-150">Spatial mapping</span></span>](../../design/spatial-mapping.md)
