---
title: 'Begrenzungssystem: Erste Schritte'
description: Landing page for Boundary system in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Boundary System,
ms.openlocfilehash: 2858b770fb49a44d1e2d704e8d3a81affe74d272
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144729"
---
# <a name="boundary-system"></a>Begrenzungssystem

Das Begrenzungssystem bietet Unterstützung für die Visualisierung von Virtual Reality-Begrenzungskomponenten in Mixed Reality-Anwendungen. Grenzen definieren den Bereich, in dem Benutzer sich sicher bewegen können, während sie ein VR-Headset verwenden. Grenzen sind eine wichtige Komponente einer Mixed Reality-Umgebung, um Benutzern zu helfen, unsichtbare Hindernisse zu vermeiden, während sie ein VR-Headset tragen.

Viele Virtual Reality-Plattformen bieten eine automatische Anzeige, z. B. eine weiße Kontur, die der virtuellen Welt überlagert wird, wenn sich der Benutzer oder sein Controller der Grenze nähert. Das Boundary System des Mixed Reality Toolkits erweitert dieses Feature, um die Anzeige eines Umrisses des nachverfolgten Bereichs, einer Bodenebene und anderer Features zu ermöglichen, die verwendet werden können, um benutzern zusätzliche Informationen zur Verfügung zu stellen.

## <a name="getting-started"></a>Erste Schritte

Zum Hinzufügen von Unterstützung für Grenzen sind zwei Hauptkomponenten des Mixed Reality Toolkits erforderlich: das Boundary System und eine Virtual Reality-Plattform, die mit einer Grenze konfiguriert ist.

1. [Aktivieren](#enable-boundary-system) des Begrenzungssystems
2. [Konfigurieren der](#configure-boundary-visualization) Begrenzungsvisualisierung
3. [Erstellen und Bereitstellen](#build-and-deploy) auf einer VR-Plattform mit einer konfigurierten Grenze

## <a name="enable-boundary-system"></a>Aktivieren des Begrenzungssystems

Das Boundary System wird vom MixedRealityToolkit-Objekt (oder einer anderen [Dienstregistrierungskomponente)](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) verwaltet.

Die folgenden Schritte setzen die Verwendung des MixedRealityToolkit-Objekts voraus. Die schritte, die für andere Dienstregistrierungsstelle erforderlich sind, können sich unterscheiden.

1. Wählen Sie das MixedRealityToolkit-Objekt in der Szenenhierarchie aus.

    ![MRTK- konfigurierte Szenenhierarchie](../images/MRTK_ConfiguredHierarchy.png)

1. Navigieren Sie im Inspektorbereich zum Abschnitt Begrenzungssystem, und aktivieren Sie Aktivieren.

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

## <a name="see-also"></a>Weitere Informationen

- [Dokumentation zur Begrenzungs-API](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [Konfigurieren der Begrenzungsvisualisierung](configuring-boundary-visualization.md)
