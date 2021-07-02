---
title: Übersicht über das Diagnosesystem
description: Dokumentation zum Aktivieren und Deaktivieren der Diagnose in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: a31b88f661c141941cae2d0b01668b26c0bed7d7
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177246"
---
# <a name="diagnostics-system-overview"></a>Übersicht über das Diagnosesystem

Das Mixed Reality Toolkit-Diagnosesystem stellt Diagnosetools bereit, die in der Anwendung ausgeführt werden, um die Analyse von Anwendungsproblemen zu ermöglichen.

Die erste Version des Diagnosesystems enthält [den Visual Profiler,](using-visual-profiler.md) der die Analyse von Leistungsproblemen während der Verwendung der Anwendung ermöglicht.

## <a name="getting-started"></a>Erste Schritte

> [!IMPORTANT]
> Es wird **_dringend_** empfohlen, das Diagnosesystem während des gesamten Produktentwicklungszyklus zu aktivieren und als letzte Änderung vor dem Erstellen und Veröffentlichen der endgültigen Version zu deaktivieren.

Es gibt zwei wichtige Schritte, um mit der Verwendung des Diagnosesystems zu beginnen.

1. [Aktivieren](#enable-diagnostics) des Diagnosesystems
2. [Konfigurieren von](#configure-diagnostic-options) Diagnoseoptionen

### <a name="enable-diagnostics"></a>Aktivieren der Diagnosefunktion

Das Diagnosesystem wird vom MixedRealityToolkit-Objekt (oder einer anderen [Dienstregistrierungskomponente)](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) verwaltet.

Die folgenden Schritte setzen die Verwendung des MixedRealityToolkit-Objekts voraus. Die für andere Dienstregistrierungen erforderlichen Schritte können unterschiedlich sein.

1. Wählen Sie das MixedRealityToolkit-Objekt in der Szenenhierarchie aus.

    ![MRTK– Konfigurierte Szenenhierarchie](../images/MRTK_ConfiguredHierarchy.png)

1. Navigieren Sie im Inspektorbereich zum Abschnitt Diagnosesystem, und aktivieren Sie Aktivieren.
1. Auswählen der Diagnosesystemimplementierung

    ![Auswählen der Diagnosesystemimplementierung](../images/diagnostics/DiagnosticsSelectSystemType.png)

> [!NOTE]
> Für Benutzer des Standardprofils (Assets/MRTK/SDK/Profiles) ist das Diagnosesystem für die Verwendung des Objekts `DefaultMixedRealityToolkitConfigurationProfile` [`MixedRealityDiagnosticsSystem`](xref:Microsoft.MixedReality.Toolkit.Diagnostics.MixedRealityDiagnosticsSystem) vorkonfiguriert.

### <a name="configure-diagnostic-options"></a>Konfigurieren von Diagnoseoptionen

Das Diagnosesystem verwendet ein Konfigurationsprofil, um anzugeben, welche Komponenten angezeigt werden sollen, und um deren Einstellungen zu konfigurieren. Weitere Informationen [zu den verfügbaren Komponenteneinstellungen](configuring-diagnostics.md) finden Sie unter Konfigurieren des Diagnosesystems.

> [!IMPORTANT]
> Während es möglich ist, den Unity-Wiedergabemodus bei der Entwicklung von Anwendungen zu verwenden, ohne dass die Schritte zum Erstellen und Bereitstellen erforderlich sind, ist es wichtig, die Diagnosesystemergebnisse mithilfe einer kompilierten Anwendung zu bewerten, die auf der Zielhardware und -plattform ausgeführt wird.
>
> Die Leistungsdiagnose, z. B. [Visual Profiler,](using-visual-profiler.md)spiegelt die tatsächliche Anwendungsleistung möglicherweise nicht genau wider, wenn sie im Editor ausgeführt wird.

## <a name="see-also"></a>Siehe auch

- [Diagnose-API-Dokumentation](xref:Microsoft.MixedReality.Toolkit.Diagnostics)
- [Konfigurieren des Diagnosesystems](configuring-diagnostics.md)
- [Verwenden des Visual Profilers](using-visual-profiler.md)
