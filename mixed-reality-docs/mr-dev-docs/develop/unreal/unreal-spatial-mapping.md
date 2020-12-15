---
title: Räumliche Abbildung in Unreal
description: Leitfaden für die Verwendung der räumlichen Abbildung in Unreal
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, Features, Dokumentation, Leitfäden, Hologramme, räumliche Abbildung, Mixed Reality-Headset Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 6d70e7f2d32fbf39bc51534661b8224547c36acc
ms.sourcegitcommit: f2782d0925b2075fdaa0a4ecdef3dd4f0b4e1e99
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96926049"
---
# <a name="spatial-mapping-in-unreal"></a>Räumliche Abbildung in Unreal

Mit der räumlichen Abbildung können Sie Objekte auf physischen Oberflächen in der realen Welt platzieren. Wenn die Welt, die die HoloLens umgibt, abgebildet ist, erscheinen Hologramme für Benutzer lebensechter. Die räumliche Abbildung verankert darüber hinaus Objekte in der Welt des Benutzers, indem sie Tiefeninformationen nutzt, was dabei hilft, den Benutzer davon zu überzeugen, dass sich diese Hologramme tatsächlich in seinem Bereich befinden. Hologramme, die im Raum schweben oder sich zusammen mit dem Benutzer bewegen, fühlen sich nicht so real an, weshalb Sie nach Möglichkeit Elemente immer unter dem Aspekt des Komforts platzieren sollten.

Weitere Informationen zur Qualität der räumlichen Abbildung, Platzierung, Verdeckung, Rendering und mehr finden Sie im Dokument [Räumliche Abbildung](../../design/spatial-mapping.md).

## <a name="enabling-spatial-mapping"></a>Aktivieren der räumlichen Abbildung

So aktivieren Sie die räumliche Abbildung in HoloLens:
- Öffnen Sie **Edit > Project Settings** (Bearbeiten > Projekteinstellungen), und scrollen Sie zum Abschnitt **Platforms** (Plattformen) herunter.    
    + Wählen Sie **HoloLens** aus, und aktivieren Sie **Spatial Perception** (Räumliche Wahrnehmung).

![Screenshot der HoloLens-Funktionalität für Projekteinstellungen mit hervorgehobener Option zur räumlichen Abbildung](images/unreal-spatial-mapping-img-01.png)

So abonnieren Sie räumliche Abbildung und debuggen das **MRMesh** in einem HoloLens-Spiel:
1. Öffnen Sie die **ARSessionConfig**, und klappen Sie den Abschnitt **ARSettings > World Mapping** (Weltdarstellung) auf. 

2. Aktivieren Sie **Generate Mesh Data from Tracked Geometry** (Daten des Gittermodells auf der Grundlage der nachverfolgten Geometrie generieren), wodurch das HoloLens-Plug-In angewiesen wird, mit dem asynchronen Abrufen von räumlichen Abbildungsdaten und ihrer Oberflächenzuordnung in Unreal mithilfe von **MRMesh** zu beginnen. 
3. Aktivieren Sie **Render Mesh Data in Wireframe** (Gittermodelldaten im Drahtmodell rendern), um einen weißen Drahtmodellumriss jedes Dreiecks im **MRMesh** darzustellen. 

![Raumanker: Speicher bereit](images/unreal-spatialmapping-arsettings.PNG)


## <a name="spatial-mapping-at-runtime"></a>Räumliche Abbildung zur Laufzeit
Sie können die folgenden Parameter ändern, um das Laufzeitverhalten der räumlichen Abbildung zu ändern:

- Öffnen Sie **Edit > Project Settings** (Bearbeiten > Projekteinstellungen), scrollen Sie nach unten zum Abschnitt **Platforms** (Plattformen), und wählen Sie **HoloLens > Spatial Mapping** (HoloLens > Räumliche Abbildung) aus: 

![Raumanker: Projekteinstellungen](images/unreal-spatialmapping-projectsettings.PNG)

- **Max Triangles Per Cubic Meter** (Maximale Anzahl von Dreiecken pro Kubikmeter) dient zum Aktualisieren der Dichte der Dreiecke im Gitter der räumlichen Abbildung.  
- **Spatial Meshing Volume Size** (Volumengröße des räumlichen Gitters) dient zum Angeben der Größe des Würfels, der den Spieler umgibt, um Daten der räumlichen Abbildung zu rendern und zu aktualisieren.  
    + Im Falle einer großen Anwendungslaufzeitumgebung muss dieser Wert ggf. hoch sein, um dem realen Raum gerecht zu werden. Der Wert kann kleiner sein, wenn die Anwendung lediglich Hologramme auf Oberflächen in der unmittelbareren Umgebung des Benutzers platzieren muss. Wenn sich der Benutzer in der Umgebung bewegt, bewegt sich das Volumen der räumlichen Abbildung mit ihm mit. 

## <a name="working-with-mrmesh"></a>Arbeiten mit MRMesh

Zunächst müssen Sie die räumliche Abbildung starten:

![Blaupause der Funktion „ToggleARCapture“ mit hervorgehobenem Erfassungstyp für räumliche Abbildung](images/unreal-spatial-mapping-img-02.png)

Nachdem die räumliche Abbildung für den Raum erfasst wurde, empfehlen wir, die räumliche Abbildung zu deaktivieren.  Die räumliche Abbildung kann entweder nach einer bestimmten Zeitspanne abgeschlossen sein, oder wenn Raycasts in jede Richtung Kollisionen mit dem MRMesh zurückgeben.

So erhalten Sie zur Laufzeit Zugriff auf das **MRMesh**:
1. Fügen Sie einem Blaupausenakteur eine **ARTrackableNotify**-Komponente hinzu. 

![Raumanker: In AR nachverfolgbare Benachrichtigung](images/unreal-spatialmapping-artrackablenotify.PNG)

2. Wählen Sie die **ARTrackableNotify**-Komponente aus, und klappen Sie im Bereich **Details** den Abschnitt **Events** (Ereignisse) auf. 
    - Wählen Sie die Schaltfläche **+** für die Ereignisse aus, die Sie überwachen möchten. 

![Raumanker: Ereignisse](images/unreal-spatialmapping-events.PNG)

In diesem Fall wird das Ereignis **On Add Tracked Geometry** überwacht, das nach gültigen Gittermodellen der Realumgebung sucht, die mit Daten der räumlichen Abbildung übereinstimmen. Die vollständige Liste der Ereignisse finden Sie in der Komponenten-API [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html). 

Sie können das Material des Gittermodells im Ereignisdiagramm der Blaupause oder in C++ ändern. Auf dem Screenshot unten ist die Route der Blaupause dargestellt: 

![Raumanker: Beispiel](images/unreal-spatialmapping-example.PNG)

## <a name="spatial-mapping-in-c"></a>Räumliche Abbildung in C++

Fügen Sie in der build.cs-Datei Ihres Spiels **AugmentedReality** und **MRMesh** zur Liste „PublicDependencyModuleNames“ hinzu:

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

Abonnieren Sie zum Zugriff auf das MRMesh die **OnTrackableAdded**-Delegaten:

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
> Es gibt ähnliche Delegaten für aktualisierte und entfernte Ereignisse, **AddOnTrackableUpdatedDelegate_Handle** bzw. **AddOnTrackableRemovedDelegate_Handle**.
>
> Die vollständige Liste der Ereignisse finden Sie in der Komponenten-API [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html).

## <a name="see-also"></a>Siehe auch
* [Räumliche Abbildung](../../design/spatial-mapping.md)
