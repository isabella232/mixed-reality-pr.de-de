---
title: Konfigurieren des Diagnosesystems
description: Dokumentation zum Konfigurieren der Diagnose in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: d81b441cd9bcd40846eb94320f6f7de1bbd2f0a8
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177255"
---
# <a name="configuring-the-diagnostics-system"></a>Konfigurieren des Diagnosesystems

## <a name="general-settings"></a>Allgemeine Einstellungen

![Diagnose allgemein Einstellungen](../images/diagnostics/DiagnosticsGeneralSettings.png)

### <a name="enable-verbose-logging"></a>Ausführliche Protokollierung aktivieren

Gibt an, ob die ausführliche MRTK-Protokollierung aktiviert wird. Dies ist standardmäßig auf FALSE festgelegt, kann aber aktiviert werden, um detaillierte Ablaufverfolgungen zu verwenden, die es dem MRTK-Team ermöglichen, Probleme zu debuggen/zu untersuchen. Wenn Sie z. B. ein Problem melden, kann das Anfügen der Unity-Playerprotokolle (entweder über den Editor oder den Player) dazu beitragen, die Quelle von Fehlern und Problemen einzugrenzen.

Beachten Sie, dass diese Option unabhängig davon ist, ob das Diagnosesystem aktiviert ist. Dies wird im Diagnosesystem angezeigt, da es sich um eine Protokollierungsoption handelt, aber letztendlich auf einer höheren Ebene ausgeführt wird, da sie sich auf die Protokollierung über die gesamte MRTK-Codebasis auswirkt.

### <a name="show-diagnostics"></a>Diagnose anzeigen

Gibt an, ob das Diagnosesystem die konfigurierten Diagnoseoptionen anzeigen soll.

Wenn diese Option deaktiviert ist, werden alle konfigurierten Diagnoseoptionen ausgeblendet.

## <a name="profiler-settings"></a>Profilereinstellungen

![Einstellungen für Diagnoseprofiler](../images/diagnostics/DiagnosticsProfilerSettings.png)

### <a name="show-profiler"></a>Profiler anzeigen

Gibt an, ob der Visual Profiler angezeigt werden soll.

### <a name="frame-sample-rate"></a>Bildabtastrate

Die Zeitspanne in Sekunden zum Erfassen von Frames für die Berechnung der Bildfrequenz. Der Bereich beträgt 0 bis 5 Sekunden.

### <a name="window-anchor"></a>Fensteranker

An welchem Teil des Ansichtsports das Profilerfenster verankert werden soll. Der Standardwert ist Lower Center.

### <a name="window-offset"></a>Fensteroffset

Der Offset von der Mitte des Ansichtsports, um den Visual Profiler zu platzieren. Der Offset befindet sich in Richtung der *Window Anchor-Eigenschaft.*

### <a name="window-scale"></a>Fensterskala

Auf das Profilerfenster angewendeter Größenmultiplikator. Wenn Sie beispielsweise den Wert auf 2 festlegen, wird die Fenstergröße verdoppelt.

### <a name="window-follow-speed"></a>Fensterfolgegeschwindigkeit

Die Geschwindigkeit, mit der das Profilerfenster verschoben werden soll, um die Sichtbarkeit innerhalb des Ansichtsports beizubehalten.

## <a name="programmatically-controlling-the-diagnostics-system"></a>Programmgesteuerte Steuerung des Diagnosesystems

Es ist auch möglich, die Sichtbarkeit des Diagnosesystems und des Profilers zur Laufzeit umzuschalten. Der folgende Code blendet beispielsweise das Diagnosesystem und den Profiler aus.

```c#
CoreServices.DiagnosticsSystem.ShowDiagnostics = false;

CoreServices.DiagnosticsSystem.ShowProfiler = false;
```

## <a name="see-also"></a>Siehe auch

- [Diagnosesystem](diagnostics-system-getting-started.md)
- [Verwenden von Visual Profiler](using-visual-profiler.md)
