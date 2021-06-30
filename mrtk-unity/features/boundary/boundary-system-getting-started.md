---
title: Übersicht über das Begrenzungssystem
description: Landing page for boundary system in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Begrenzungssystem,
ms.openlocfilehash: 405a2d06be5d929d5c276fc8cd7ab36b6b3cf68c
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121358"
---
# <a name="boundary-system"></a>Begrenzungssystem

Das Begrenzungssystem bietet Unterstützung für die Visualisierung von Virtual Reality-Begrenzungskomponenten in Mixed Reality-Anwendungen. Grenzen definieren den Bereich, in dem sich Benutzer sicher bewegen können, während sie ein VR-Headset tragen. Grenzen sind eine wichtige Komponente einer Mixed Reality-Erfahrung, mit der Benutzer ungesehene Hindernisse beim Tragen eines VR-Headsets vermeiden können.

Viele Virtual Reality-Plattformen bieten eine automatische Anzeige, z. B. einen weißen Umriss, der auf der virtuellen Welt überlagert wird, wenn sich der Benutzer oder sein Controller der Grenze nähert. Das Begrenzungssystem des Mixed Reality Toolkits erweitert dieses Feature, um die Anzeige einer Gliederung des nachverfolgten Bereichs, einer Bodenebene und anderer Features zu ermöglichen, die verwendet werden können, um Benutzern zusätzliche Informationen bereitzustellen.

## <a name="getting-started"></a>Erste Schritte

Das Hinzufügen von Unterstützung für Grenzen erfordert zwei Hauptkomponenten des Mixed Reality Toolkits: das Begrenzungssystem und eine Virtual Reality-Plattform, die mit einer Grenze konfiguriert ist.

1. [Aktivieren](#enable-boundary-system) des Begrenzungssystems
2. [Konfigurieren](#configure-boundary-visualization) der Begrenzungsvisualisierung
3. [Erstellen und Bereitstellen](#build-and-deploy) auf einer VR-Plattform mit einer konfigurierten Grenze

## <a name="enable-boundary-system"></a>Aktivieren des Begrenzungssystems

Das Begrenzungssystem wird vom MixedRealityToolkit-Objekt (oder einer anderen [Dienstregistrierungsstellenkomponente)](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) verwaltet.

In den folgenden Schritten wird davon ausgegangen, dass das MixedRealityToolkit-Objekt verwendet wird. Die für andere Dienstregistrierungsstellen erforderlichen Schritte können unterschiedlich sein.

1. Wählen Sie das MixedRealityToolkit-Objekt in der Szenenhierarchie aus.

    ![KONFIGURIERTE MRTK-Szenenhierarchie](../images/MRTK_ConfiguredHierarchy.png)

1. Navigieren Sie im Bereich Inspector (Inspektor) zum Abschnitt Boundary System (Begrenzungssystem), und aktivieren Sie Enable (Aktivieren).

    ![Aktivieren des Begrenzungssystems](../images/boundary/MRTKConfig_Boundary.png)

1. Wählen Sie die Implementierung des Begrenzungssystems aus. Die vom MRTK bereitgestellte Standardklassenimplementierungen sind : [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)

    ![Auswählen der Implementierung des Begrenzungssystems](../images/boundary/BoundarySelectSystemType.png)

> [!NOTE]
> Alle Implementierungen des Begrenzungssystems müssen die [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)

## <a name="configure-boundary-visualization"></a>Konfigurieren der Begrenzungsvisualisierung

Das [Begrenzungssystem verwendet ein Konfigurationsprofil,](configuring-boundary-visualization.md) um anzugeben, welche Begrenzungskomponenten angezeigt werden sollen, und um deren Darstellung zu konfigurieren.

![Optionen für die Begrenzungsvisualisierung](../images/boundary/BoundaryVisualizationProfile.png)

> [!NOTE]
> Benutzer des `DefaultMixedRealityBoundaryVisualizationProfile` Standardprofils (Assets/MRTK/SDK/Profile) haben das Begrenzungssystem vorkonfiguriert, um eine Bodenebene, den Spielbereich und den nachverfolgten Bereich anzuzeigen.

## <a name="build-and-deploy"></a>Erstellen und Bereitstellen

Nachdem das Begrenzungssystem mit den gewünschten Visualisierungsoptionen konfiguriert wurde, kann das Projekt auf der Zielplattform bereitgestellt werden.

> [!NOTE]
> Der Unity-Wiedergabemodus ermöglicht die Visualisierung der konfigurierten Grenze im Editor. Dieses Feature ermöglicht schnelle Entwicklung und Tests, ohne dass der Build- und Bereitstellungsschritt erforderlich ist. Stellen Sie sicher, dass Sie abschließende Akzeptanztests mit einer erstellten und bereitgestellten Version der Anwendung durchführen, die auf der Zielhardware und -plattform ausgeführt wird.

## <a name="accessing-boundary-system-via-code"></a>Zugreifen auf das Begrenzungssystem über Code

Wenn diese Option aktiviert und konfiguriert ist, kann über die statische Hilfsklasse CoreServices auf das Begrenzungssystem zugegriffen werden. Der Verweis kann dann verwendet werden, um die Boundary-Parameter dynamisch zu ändern und auf verwandte GameObjects zuzugreifen, die vom System verwaltet werden.

```c#
// Hide Boundary Walls at runtime
CoreServices.BoundarySystem.ShowBoundaryWalls = false;

// Get Unity GameObject for the floor visualization in scene
GameObject floorVisual = CoreServices.BoundarySystem.GetFloorVisualization();
```

## <a name="see-also"></a>Siehe auch

- [Dokumentation zur Begrenzungs-API](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [Konfigurieren der Begrenzungsvisualisierung](configuring-boundary-visualization.md)
