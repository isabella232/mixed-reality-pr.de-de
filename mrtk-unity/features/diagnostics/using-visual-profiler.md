---
title: Verwenden des visuellen Profiler
description: Dokumentation zur Verwendung von Visual Profiler in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 018d6bf2087b73697a1e1f43e206c96ae25e1f21
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177219"
---
# <a name="using-the-visual-profiler"></a>Verwenden des visuellen Profiler

VisualProfiler bietet eine benutzerfreundliche Anwendungsansicht der Leistung einer Mixed Reality-Anwendung. Der Profiler wird auf allen Mixed Reality Toolkit-Plattformen unterstützt, einschließlich:

- Microsoft HoloLens (1. Generation)
- Microsoft HoloLens 2
- Immersive Windows Mixed Reality-Headsets
- OpenVR

Konzentrieren Sie sich beim Entwickeln einer Anwendung auf mehrere Teile der Szene, da der Visual Profiler Daten relativ zur aktuellen Ansicht anzeigt.

> [!IMPORTANT]
> Konzentrieren Sie sich auf Teile der Szene mit komplexen Objekten, Partikeleffekten oder Aktivitäten. Diese und andere Faktoren tragen häufig zur Verringerung der Anwendungsleistung und einer weniger idealen Benutzererfahrung bei.

## <a name="visual-profiler-interface"></a>Grafische Profiler-Schnittstelle

![Grafische Profiler-Schnittstelle](../images/diagnostics/VisualProfiler.png)

Die Visual Profiler-Schnittstelle umfasst die folgenden Komponenten:

- [Bildfrequenz](#frame-rate)
- [Framezeit](#frame-time)
- [Frame-Graph](#frame-graph)
- [Arbeitsspeicherauslastung](#memory-utilization)

### <a name="frame-rate"></a>Bildfrequenz

In der oberen linken Ecke der Schnittstelle befindet sich die Bildfrequenz, gemessen in Frames pro Sekunde. Für optimale Benutzerfreundlichkeit und Komfort sollte dieser Wert so hoch wie möglich sein.

Die spezifische Plattform- und Hardwarekonfiguration spielt eine wichtige Rolle bei der maximal erreichbaren Bildfrequenz. Einige allgemeine Zielwerte sind:

- Microsoft HoloLens: 60
- Windows Mixed Reality Ultra: 90

> [!NOTE]
> Aufgrund einer [Drosselung der Bildfrequenz bei HoloLens wenn der Standard-MRC aktiv ist,](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens)blendet sich der visuelle Profiler aus, während Videos und Fotos erfasst werden. Diese Einstellung kann im Diagnosesystemprofil überschrieben werden.

### <a name="frame-time"></a>Framedauer

Rechts neben der Bildfrequenz befindet sich die Für die CPU aufgewendete Framezeit in Millisekunden. Um die zuvor erwähnten Zielframeraten zu erreichen, kann eine Anwendung die folgende Zeit pro Frame aufwenden:

- 60 fps: 16,6 ms
- 90 fps: 11,1 ms

Die GPU-Zeit soll in einer zukünftigen Version hinzugefügt werden.

### <a name="frame-graph"></a>Framegraph

Das Framediagramm bietet eine grafische Darstellung des Verlaufs der Framerate der Anwendung.

![Visual Profiler– Graph "Frame verpasst"](../images/diagnostics/VisualProfilerMissedFrames.png)

Wenn Sie die Anwendung verwenden, suchen Sie nach verpassten Frames, die darauf hinweisen, dass die Anwendung ihre Zielbildfrequenz nicht erreicht und möglicherweise Optimierungsaufgaben benötigt.

### <a name="memory-utilization"></a>Arbeitsspeichernutzung

Die Anzeige der Speicherauslastung ermöglicht ein einfaches Verständnis der Auswirkungen der aktuellen Ansicht auf den Arbeitsspeicherverbrauch einer Anwendung.

![Speicher Graph für Visual Profiler](../images/diagnostics/VisualProfilerMemory.png)

Wenn Sie die Anwendung verwenden, suchen Sie nach der Gesamtspeicherauslastung. Zu den Schlüsselindikatoren gehören das Fasten des Arbeitsspeicherlimits und schnelle Änderungen bei der Nutzung.

## <a name="customizing-the-visual-profiler"></a>Anpassen des visuellen Profiler

Die Darstellung und das Verhalten des Visual Profilers können über das Diagnosesystemprofil angepasst werden. Weitere Informationen finden Sie unter [Konfigurieren des Diagnosesystems.](configuring-diagnostics.md)

## <a name="see-also"></a>Siehe auch

- [Diagnosesystem](diagnostics-system-getting-started.md)
- [Konfigurieren des Diagnosesystems](configuring-diagnostics.md)
