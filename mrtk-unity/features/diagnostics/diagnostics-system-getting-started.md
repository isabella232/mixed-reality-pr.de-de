---
title: 'Diagnosesystem: Erste Schritte'
description: Dokumentation zum Aktivieren und Deaktivieren der Diagnose in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 66d68902dd9ffa36a5b30c1130a8640d154ac5e1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144724"
---
# <a name="diagnostic-system"></a>Diagnosesystem

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
> Während es möglich ist, den Unity-Wiedergabemodus bei der Entwicklung von Anwendungen zu verwenden, ohne dass die Schritte zum Erstellen und Bereitstellen erforderlich sind, ist es wichtig, die Diagnosesystemergebnisse mithilfe einer kompilierten Anwendung zu bewerten, die auf der Zielhardware und -plattform ausgeführt wird.
>
> Die Leistungsdiagnose, z. B. [Visual Profiler,](using-visual-profiler.md)spiegelt die tatsächliche Anwendungsleistung möglicherweise nicht genau wider, wenn sie im Editor ausgeführt wird.

## <a name="see-also"></a>Weitere Informationen

- [Diagnose-API-Dokumentation](xref:Microsoft.MixedReality.Toolkit.Diagnostics)
- [Konfigurieren des Diagnosesystems](configuring-diagnostics.md)
- [Verwenden des Visual Profilers](using-visual-profiler.md)
