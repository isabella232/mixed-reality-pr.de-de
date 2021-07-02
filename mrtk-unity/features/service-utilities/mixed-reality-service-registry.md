---
title: Mixed Reality-Dienstregistrierung
description: Dokumentation zu MixedRealityServiceRegistry und IMixedRealityServiceRegistrar
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 061e4233d61de817b1aaed7faaa6d461427d6f07
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176706"
---
# <a name="mixed-reality-service-registry"></a>Mixed Reality-Dienstregistrierung

Das Mixed Reality Toolkit verfügt über zwei sehr ähnlich benannte Komponenten, die verwandte Aufgaben ausführen: MixedRealityServiceRegistry und IMixedRealityServiceRegistrar.

## <a name="mixedrealityserviceregistry"></a>MixedRealityServiceRegistry

[MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) ist die Komponente, die Instanzen jedes registrierten Diensts (Kernsysteme und Erweiterungsdienste) enthält.

> [!NOTE]
> MixedRealityServiceRegistry enthält Instanzen von -Objekten, die die [IMixedRealityService-Schnittstelle](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) implementieren, einschließlich [IMixedRealityExtensionService.](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
>
>Objekte, die [IMixedRealityDataProvider](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) (eine Unterklasse von IMixedRealityService) implementieren, werden explizit nicht in MixedRealityServiceRegistry registriert. Diese Objekte werden von den einzelnen Diensten verwaltet (z. B. Räumliche Wahrnehmung).

MixedRealityServiceRegistry wird als statische C#-Klasse implementiert und ist das empfohlene Muster zum Abrufen von Dienstinstanzen im Anwendungscode.

Der folgende Codeausschnitt veranschaulicht das Abrufen einer IMixedRealityInputSystem-Instanz.

```c#
IMixedRealityInputSystem inputSystem = null;

if (!MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
{
    // Failed to acquire the input system. It may not have been registered
}
```

## <a name="imixedrealityserviceregistrar"></a>IMixedRealityServiceRegistrar

[IMixedRealityServiceRegistrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) ist die Schnittstelle, die die Funktionalität definiert, die von Komponenten implementiert wird, die die Registrierung eines oder mehrerer Dienste verwalten. Komponenten, die IMixedRealityServiceRegistrar implementieren, sind für das Hinzufügen und Entfernen der Daten in MixedRealityServiceRegistry verantwortlich. Das [MixedRealityToolkit-Objekt](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) ist eine solche Komponente.

Andere Registrierungsstellen finden Sie im Ordner MRTK/SDK/Experimental/Features. Diese Komponenten können verwendet werden, um einer Anwendung unterstützung für einen einzelnen Dienst (z. B. räumliche Wahrnehmung) hinzuzufügen. Diese einzelnen Dienst-Manager sind unten aufgeführt.

- [BoundarySystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Boundary.BoundarySystemManager)
- [CameraSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.CameraSystem.CameraSystemManager)
- [DiagnosticsSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Diagnostics.DiagnosticsSystemManager)
- [InputSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Input.InputSystemManager)
- [SpatialAwarenessSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSystemManager)
- [TeleportSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Teleport.TeleportSystemManager)

Jede der oben genannten Komponenten, mit Ausnahme von InputSystemManager, ist für die Verwaltung der Registrierung und des Status eines einzelnen Diensttyps verantwortlich. Das InputSystem erfordert einige zusätzliche Supportdienste (z. B. FocusProvider), die auch vom InputSystemManager verwaltet werden.

Im Allgemeinen werden die von IMixedRealityServiceRegistrar definierten Methoden intern von Dienstverwaltungskomponenten oder von Diensten aufgerufen, die zusätzliche Dienstkomponenten benötigen, um ordnungsgemäß zu funktionieren. Anwendungscode sollte diese Methoden im Allgemeinen nicht aufrufen, da dies dazu führen kann, dass sich die Anwendung unvorhersehbar verhält (z. B. kann eine zwischengespeicherte Dienstinstanz ungültig werden).

## <a name="see-also"></a>Siehe auch

- [IMixedRealityServiceRegistrar-API-Dokumentation](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar)
- [Dokumentation zur MixedRealityServiceRegistry-API](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
