---
title: Konfigurieren des Diagnosesystems
description: Dokumentation zum Konfigurieren der Diagnose im MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 521ef71abd1ddf920863530a2a423c1080a135e5a404a26f1611fc14f92c2796
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198240"
---
# <a name="configuring-the-diagnostics-system"></a>Konfigurieren des Diagnosesystems

## <a name="general-settings"></a>Allgemeine Einstellungen

![Diagnose allgemein Einstellungen](../images/diagnostics/DiagnosticsGeneralSettings.png)

### <a name="enable-verbose-logging"></a>Ausführliche Protokollierung aktivieren

Gibt an, ob die ausführliche MRTK-Protokollierung aktiviert wird. Dieser Standardwert ist false, kann aber aktiviert werden, um detaillierte Ablaufverfolgungen zu verwenden, die es dem MRTK-Team ermöglichen, Probleme zu debuggen/zu beheben. Wenn Sie beispielsweise ein Problem melden, kann das Anfügen der Unity-Playerprotokolle (entweder über den Editor oder über den Player) dazu beitragen, die Quelle von Fehlern und Problemen einzuengen.

Beachten Sie, dass diese Option unabhängig davon ist, ob das Diagnosesystem aktiviert ist. Dies wird im Diagnosesystem angezeigt, da es sich um eine Protokollierungsoption handelt, aber letztendlich auf einer höheren Ebene arbeitet, da sie sich auf die Protokollierung in der gesamten MRTK-Codebasis auswirken.

### <a name="show-diagnostics"></a>Diagnose anzeigen

Gibt an, ob das Diagnosesystem die konfigurierten Diagnoseoptionen anzeigen soll.

Wenn diese Option deaktiviert ist, werden alle konfigurierten Diagnoseoptionen ausgeblendet.

## <a name="profiler-settings"></a>Profilereinstellungen

![Diagnoseprofiler-Einstellungen](../images/diagnostics/DiagnosticsProfilerSettings.png)

### <a name="show-profiler"></a>Profiler anzeigen

Gibt an, ob der Visual Profiler angezeigt werden soll.

### <a name="frame-sample-rate"></a>Frame-Abtastrate

Die Zeit in Sekunden zum Erfassen von Frames für die Berechnung der Bildfrequenz. Der Bereich beträgt 0 bis 5 Sekunden.

### <a name="window-anchor"></a>Fensteranker

An welchem Teil des Ansichtsport sollte das Profilerfenster verankert werden. Der Standardwert ist Lower Center.

### <a name="window-offset"></a>Fensteroffset

Der Offset von der Mitte des Ansichtsportes zum Platzieren des Visual Profilers. Der Offset wird in Richtung der Eigenschaft *Fensteranker* angezeigt.

### <a name="window-scale"></a>Fensterskala

Auf das Profilerfenster angewendeter Größenmultiplikator. Wenn Sie beispielsweise den Wert auf 2 festlegen, wird die Fenstergröße verdoppelt.

### <a name="window-follow-speed"></a>Fenster folgt Geschwindigkeit

Die Geschwindigkeit, mit der das Profilerfenster bewegt werden soll, um die Sichtbarkeit innerhalb des Ansichtsport zu erhalten.

## <a name="programmatically-controlling-the-diagnostics-system"></a>Programmgesteuertes Steuern des Diagnosesystems

Es ist auch möglich, die Sichtbarkeit des Diagnosesystems und des Profilers zur Laufzeit umschalten. Der folgende Code blendet z. B. das Diagnosesystem und den Profiler aus.

```c#
CoreServices.DiagnosticsSystem.ShowDiagnostics = false;

CoreServices.DiagnosticsSystem.ShowProfiler = false;
```

## <a name="see-also"></a>Siehe auch

- [Diagnosesystem](diagnostics-system-getting-started.md)
- [Verwenden von Visual Profiler](using-visual-profiler.md)
