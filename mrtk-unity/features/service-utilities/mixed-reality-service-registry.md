---
title: Mixed Reality Service Registry und IMixedRealityServiceRegistrar
description: Dokumentation zu MixedRealityServiceRegistry und IMixedRealityServiceRegistrar
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 09b20537824af42d241b6c33496cedcb4f530bc7
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145232"
---
# <a name="what-are-the-mixedrealityserviceregistry-and-imixedrealityserviceregistrar"></a>Was sind MixedRealityServiceRegistry und IMixedRealityServiceRegistrar?

Das Mixed Reality Toolkit verfügt über zwei ähnlich benannte Komponenten, die verwandte Aufgaben ausführen: MixedRealityServiceRegistry und IMixedRealityServiceRegistrar.

## <a name="mixedrealityserviceregistry"></a>MixedRealityServiceRegistry

[MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) ist die Komponente, die Instanzen der einzelnen registrierten Dienste (Kernsysteme und Erweiterungsdienste) enthält.

> [!NOTE]
> MixedRealityServiceRegistry enthält Instanzen von -Objekten, die [die IMixedRealityService-Schnittstelle](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) implementieren, einschließlich [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService).
>
>Objekte, die [den IMixedRealityDataProvider](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) (eine Unterklasse von IMixedRealityService) implementieren, werden explizit nicht in MixedRealityServiceRegistry registriert. Diese Objekte werden von den einzelnen Diensten verwaltet (z.B. Räumliche Wahrnehmung).

MixedRealityServiceRegistry wird als statische C#-Klasse implementiert und ist das empfohlene Muster zum Erwerben von Dienstinstanzen im Anwendungscode.

Der folgende Codeausschnitt veranschaulicht das Abrufen einer IMixedRealityInputSystem-Instanz.

```c#
IMixedRealityInputSystem inputSystem = null;

if (!MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
{
    // Failed to acquire the input system. It may not have been registered
}
```

## <a name="imixedrealityserviceregistrar"></a>IMixedRealityServiceRegistrar

[IMixedRealityServiceRegistrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) ist die Schnittstelle, die die Funktionalität definiert, die von Komponenten implementiert wird, die die Registrierung eines oder mehrere Dienste verwalten. Komponenten, die IMixedRealityServiceRegistrar implementieren, sind für das Hinzufügen und Entfernen der Daten in MixedRealityServiceRegistry verantwortlich. Das [MixedRealityToolkit-Objekt](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) ist eine solche Komponente.

Andere Registrierungsstellen finden Sie im Ordner MRTK/SDK/Experimental/Features. Diese Komponenten können verwendet werden, um einer Anwendung Unterstützung für einen einzelnen Dienst (z. B. Räumliche Wahrnehmung) hinzuzufügen. Diese einzelnen Dienst-Manager sind unten aufgeführt.

- [BoundarySystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Boundary.BoundarySystemManager)
- [CameraSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.CameraSystem.CameraSystemManager)
- [DiagnosticsSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Diagnostics.DiagnosticsSystemManager)
- [InputSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Input.InputSystemManager)
- [SpatialAwarenessSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSystemManager)
- [TeleportSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Teleport.TeleportSystemManager)

Jede der oben genannten Komponenten, mit Ausnahme von InputSystemManager, ist für die Verwaltung der Registrierung und des Status eines einzelnen Diensttyps verantwortlich. Das InputSystem erfordert einige zusätzliche Supportdienste (z. B. FocusProvider), die auch vom InputSystemManager verwaltet werden.

Im Allgemeinen werden die von IMixedRealityServiceRegistrar definierten Methoden intern von Dienstverwaltungskomponenten oder von Diensten aufgerufen, die zusätzliche Dienstkomponenten benötigen, um ordnungsgemäß zu funktionieren. Anwendungscode sollte diese Methoden im Allgemeinen nicht aufrufen, da dies dazu führen kann, dass sich die Anwendung unvorhersehbar verhält (z. B. kann eine zwischengespeicherte Dienstinstanz ungültig werden).

## <a name="see-also"></a>Weitere Informationen

- [IMixedRealityServiceRegistrar-API-Dokumentation](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar)
- [Dokumentation zur MixedRealityServiceRegistry-API](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
