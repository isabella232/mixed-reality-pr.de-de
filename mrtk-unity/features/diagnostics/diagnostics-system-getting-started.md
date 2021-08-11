---
title: Übersicht des Diagnosesystems
description: Dokumentation zum Aktivieren und Deaktivieren der Diagnose im MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 536a35a0af0c0d0190f2f423f4a39e0d89e92c1acaa105ab37e8cf7fdc37cbf5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221812"
---
# <a name="diagnostics-system-overview"></a>Übersicht des Diagnosesystems

Das Mixed Reality Toolkit Diagnostic System stellt Diagnosetools bereit, die in der Anwendung ausgeführt werden, um die Analyse von Anwendungsprobleme zu ermöglichen.

Das erste Release des Diagnosesystems enthält den [Visual Profiler,](using-visual-profiler.md) der die Analyse von Leistungsproblemen während der Verwendung der Anwendung ermöglicht.

## <a name="getting-started"></a>Erste Schritte

> [!IMPORTANT]
> Es wird **_dringend_** empfohlen, das Diagnosesystem während des gesamten Produktentwicklungszyklus zu aktivieren und als letzte Änderung vor dem Erstellen und Veröffentlichen der endgültigen Version zu deaktivieren.

Es gibt zwei wichtige Schritte, um mit der Verwendung des Diagnosesystems zu beginnen.

1. [Aktivieren](#enable-diagnostics) des Diagnosesystems
2. [Konfigurieren von](#configure-diagnostic-options) Diagnoseoptionen

### <a name="enable-diagnostics"></a>Aktivieren der Diagnosefunktion

Das Diagnosesystem wird vom MixedRealityToolkit-Objekt (oder einer anderen [Dienstregistrierungsstellenkomponente)](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) verwaltet.

In den folgenden Schritten wird davon ausgegangen, dass das MixedRealityToolkit-Objekt verwendet wird. Die für andere Dienstregistrierungsstellen erforderlichen Schritte können unterschiedlich sein.

1. Wählen Sie das MixedRealityToolkit-Objekt in der Szenenhierarchie aus.

    ![KONFIGURIERTE MRTK-Szenenhierarchie](../images/MRTK_ConfiguredHierarchy.png)

1. Navigieren Sie im Bereich Inspector zum Abschnitt Diagnosesystem, und aktivieren Sie Aktivieren.
1. Auswählen der Diagnosesystemimplementierung

    ![Auswählen der Diagnosesystemimplementierung](../images/diagnostics/DiagnosticsSelectSystemType.png)

> [!NOTE]
> Benutzer des Standardprofils `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profile) haben das Diagnosesystem für die Verwendung des Objekts vorkonfiguriert. [`MixedRealityDiagnosticsSystem`](xref:Microsoft.MixedReality.Toolkit.Diagnostics.MixedRealityDiagnosticsSystem)

### <a name="configure-diagnostic-options"></a>Konfigurieren von Diagnoseoptionen

Das Diagnosesystem verwendet ein Konfigurationsprofil, um anzugeben, welche Komponenten angezeigt werden sollen, und um ihre Einstellungen zu konfigurieren. Weitere Informationen zu den verfügbaren Komponenteneinstellungen finden Sie unter Konfigurieren des [Diagnosesystems.](configuring-diagnostics.md)

> [!IMPORTANT]
> Es ist zwar möglich, den Unity-Wiedergabemodus bei der Entwicklung von Anwendungen zu verwenden, ohne dass die Build- und Bereitstellungsschritte erforderlich sind, aber es ist wichtig, die Ergebnisse des Diagnosesystems mithilfe einer kompilierten Anwendung auszuwerten, die auf der Zielhardware und -plattform ausgeführt wird.
>
> Die Leistungsdiagnose, z. B. [der Visual Profiler,](using-visual-profiler.md)spiegelt möglicherweise die tatsächliche Anwendungsleistung nicht genau wider, wenn sie im Editor ausgeführt wird.

## <a name="see-also"></a>Siehe auch

- [Dokumentation zur Diagnose-API](xref:Microsoft.MixedReality.Toolkit.Diagnostics)
- [Konfigurieren des Diagnosesystems](configuring-diagnostics.md)
- [Verwenden von Visual Profiler](using-visual-profiler.md)
