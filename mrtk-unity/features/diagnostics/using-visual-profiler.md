---
title: Verwenden von Visual Profiler
description: Dokumentation zur Verwendung von Visual Profiler in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 4830615fd55a39614dd775dd7628938ee3af1c3b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143718"
---
# <a name="using-the-visual-profiler"></a>Verwenden des visuellen Profilers

VisualProfiler bietet eine einfach zu verwendende Anwendungsansicht der Leistung einer Mixed Reality-Anwendung. Der Profiler wird auf allen Plattformen des Mixed Reality Toolkits unterstützt, einschließlich:

- Microsoft HoloLens (1. Generation)
- Microsoft HoloLens 2
- Immersive Windows Mixed Reality-Headsets
- OpenVR

Konzentrieren Sie sich beim Entwickeln einer Anwendung auf mehrere Teile der Szene, da der Visual Profiler Daten relativ zur aktuellen Ansicht anzeigt.

> [!IMPORTANT]
> Konzentrieren Sie sich auf Teile der Szene mit komplexen Objekten, Partikeleffekten oder Aktivitäten. Diese und andere Faktoren tragen häufig zur Verringerung der Anwendungsleistung und zu einer weniger idealen Benutzererfahrung bei.

## <a name="visual-profiler-interface"></a>Grafische Profilerschnittstelle

![Visual Profiler-Schnittstelle](../images/diagnostics/VisualProfiler.png)

Die Visual Profiler-Schnittstelle umfasst die folgenden Komponenten:

- [Bildfrequenz](#frame-rate)
- [Framezeit](#frame-time)
- [Rahmendiagramm](#frame-graph)
- [Arbeitsspeicherauslastung](#memory-utilization)

### <a name="frame-rate"></a>Bildfrequenz

In der oberen linken Ecke der Schnittstelle befindet sich die Bildfrequenz, gemessen in Frames pro Sekunde. Für optimale Benutzerfreundlichkeit und Komfort sollte dieser Wert so hoch wie möglich sein.

Die spezifische Plattform- und Hardwarekonfiguration spielt eine wichtige Rolle bei der maximal erreichbaren Bildfrequenz. Einige allgemeine Zielwerte sind:

- Microsoft HoloLens: 60
- Windows Mixed Reality Ultra: 90

> [!NOTE]
> Aufgrund der [Drosselung der Bildfrequenz auf HoloLens, wenn der Standard-MRC aktiv ist,](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens)blendet sich der visuelle Profiler aus, während Videos und Fotos erfasst werden. Diese Einstellung kann im Diagnosesystemprofil überschrieben werden.

### <a name="frame-time"></a>Framedauer

Rechts neben der Bildfrequenz befindet sich die Für die CPU aufgewendete Framezeit in Millisekunden. Um die zuvor erwähnten Zielframeraten zu erreichen, kann eine Anwendung die folgende Zeit pro Frame aufwenden:

- 60 fps: 16,6 ms
- 90 fps: 11,1 ms

Die GPU-Zeit soll in einer zukünftigen Version hinzugefügt werden.

### <a name="frame-graph"></a>Framegraph

Das Framediagramm bietet eine grafische Darstellung des Verlaufs der Framerate der Anwendung.

![Visual Profiler– Diagramm für verpassten Frame](../images/diagnostics/VisualProfilerMissedFrames.png)

Wenn Sie die Anwendung verwenden, suchen Sie nach verpassten Frames, die darauf hinweisen, dass die Anwendung ihre Zielbildfrequenz nicht erreicht und möglicherweise Optimierungsaufgaben benötigt.

### <a name="memory-utilization"></a>Arbeitsspeichernutzung

Die Anzeige der Speicherauslastung ermöglicht ein einfaches Verständnis der Auswirkungen der aktuellen Ansicht auf den Arbeitsspeicherverbrauch einer Anwendung.

![Visual Profiler-Speicherdiagramm](../images/diagnostics/VisualProfilerMemory.png)

Wenn Sie die Anwendung verwenden, suchen Sie nach der Gesamtspeicherauslastung. Zu den Schlüsselindikatoren gehören das Fasten des Arbeitsspeicherlimits und schnelle Änderungen bei der Nutzung.

## <a name="customizing-the-visual-profiler"></a>Anpassen des visuellen Profiler

Die Darstellung und das Verhalten des Visual Profilers können über das Diagnosesystemprofil angepasst werden. Weitere Informationen finden Sie unter [Konfigurieren des Diagnosesystems.](configuring-diagnostics.md)

## <a name="see-also"></a>Weitere Informationen

- [Diagnosesystem](diagnostics-system-getting-started.md)
- [Konfigurieren des Diagnosesystems](configuring-diagnostics.md)