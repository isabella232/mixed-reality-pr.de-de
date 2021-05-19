---
title: Systemerweiterungsanbieter
description: MRTK-Erweiterungen und -Datenanbieter
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Systemerweiterungen,
ms.openlocfilehash: add1f443edb687edfc387a316d83443779e079f9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143501"
---
# <a name="systems-extension-services-and-data-providers"></a>Systeme, Erweiterungsdienste und Datenanbieter

Im Mixed Reality Toolkit werden viele der Features in Form von Diensten bereitgestellt. Dienste sind in drei Hauptkategorien unterteilt: Systeme, Erweiterungsdienste und Datenanbieter.

## <a name="systems"></a>Systeme

Systeme sind Dienste, die die Kernfunktionen des Mixed Reality Toolkits bereitstellen. Alle Systeme sind Implementierungen der [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) -Schnittstelle.

- [BoundarySystem](../features/boundary/boundary-system-getting-started.md)
- [CameraSystem](../features/camera-system/camera-system-overview.md)
- [DiagnosticsSystem](../features/diagnostics/diagnostics-system-getting-started.md)
- [InputSystem](../features/input/overview.md)
- [SceneSystem](../features/scene-system/scene-system-getting-started.md)
- [SpatialAwarenessSystem](../features/spatial-awareness/spatial-awareness-getting-started.md)
- [TeleportSystem](../features/teleport-system/teleport-system.md)

Jedes der aufgeführten Systeme wird im Konfigurationsprofil der MixedRealityToolkit-Komponente [angezeigt.](../features/profiles/profiles.md)

## <a name="extensions"></a>-Erweiterungen

Erweiterungsdienste sind Komponenten, die die Funktionalität des Mixed Reality Toolkits erweitern. Alle Erweiterungsdienste müssen angeben, dass sie die [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) -Schnittstelle implementieren.

Informationen zum Erstellen von Erweiterungsdiensten finden Sie im Artikel [Erweiterungsdienste.](../features/extensions/extension-services.md)

Um für das MRTK zugänglich zu sein, werden Erweiterungsdienste im Abschnitt Erweiterungen des Konfigurationsprofils der MixedRealityToolkit-Komponente registriert und konfiguriert.

![Konfigurieren eines Erweiterungsdiensts](../features/images/profiles/ConfiguredExtensionService.png)

## <a name="data-providers"></a>Datenanbieter

Datenanbieter sind Komponenten, die nach ihrem Namen Daten für einen Mixed Reality Toolkit-Dienst bereitstellen. Alle Datenanbieter müssen angeben, dass sie die -Schnittstelle [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) implementieren.

> [!NOTE]
> Nicht alle Dienste erfordern Datenanbieter. Von den Mixed Reality Toolkits sind die Eingabe- und Räumliche Wahrnehmungssysteme die einzigen Dienste, die Datenanbieter nutzen.

Um für den spezifischen MRTK-Dienst zugänglich zu sein, werden Datenanbieter im Konfigurationsprofil des Diensts registriert.

Anwendungscode greifen über die -Schnittstelle auf Datenanbieter [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) zu. Um den Zugriff zu vereinfachen, können Datenanbieter auch über die `CoreServices` Hilfsklasse abgerufen werden.

```c#
var inputSimulationService = CoreServices.GetDataProvider<IInputSimulationService>(CoreServices.InputSystem);
```

> [!IMPORTANT]
> Obwohl `IMixedRealityDataProvider` von `IMixedRealityService` erbt, werden Datenanbieter nicht bei `MixedRealityServiceRegistry` registriert. Für den Zugriff auf Datenanbieter muss der Anwendungscode die Dienstinstanz abfragen, für die sie registriert wurden (z. B. Eingabesystem).

### <a name="input"></a>Eingabe

Das MRTK-Eingabesystem verwendet nur Datenanbieter, die [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) implementieren.

![Eingabesystemdatenanbieter](../features/images/input/RegisteredServiceProviders.PNG)

Im folgenden Beispiel wird der Zugriff auf den Eingabesimulationsanbieter und das Umschalten der SmoothEyeTracking-Eigenschaft veranschaulicht.

```c#
IMixedRealityDataProviderAccess dataProviderAccess = CoreServices.InputSystem as IMixedRealityDataProviderAccess;

if (dataProviderAccess != null)
{
    IInputSimulationService inputSimulation =
        dataProviderAccess.GetDataProvider<IInputSimulationService>();

    if (inputSimulation != null)
    {
        inputSimulation.SmoothEyeTracking = !inputSimulation.SmoothEyeTracking;
    }
}
```

Der Zugriff auf einen Datenanbieter für das Kerneingabesystem kann auch mithilfe der `CoreServices` Hilfsklasse vereinfacht werden.

```c#
var inputSimulationService = CoreServices.GetInputSystemDataProvider<IInputSimulationService>();
if (inputSimulationService != null)
{
    // do something here
}
```

> [!NOTE]
> Das Eingabesystem gibt nur Datenanbieter zurück, die für die Plattform unterstützt werden, auf der die Anwendung ausgeführt wird.

Informationen zum Schreiben eines Datenanbieters für das MRTK-Eingabesystem finden Sie unter [Erstellen eines Eingabesystem-Datenanbieters.](../features/input/create-data-provider.md)

### <a name="spatial-awareness"></a>Räumliche Wahrnehmung

Das MRTK-Raumerkennsystem nutzt nur Datenanbieter, die die -Schnittstelle [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) implementieren.

![Anbieter von Räumlichen Wahrnehmungssystemdaten](../features/images/spatial-awareness/SpatialAwarenessProfile.png)

Im folgenden Beispiel wird der Zugriff auf die registrierten Räumlichen Gitternetz-Datenanbieter und das Ändern der Sichtbarkeit der Gitternetze veranschaulicht.

```c#
IMixedRealityDataProviderAccess dataProviderAccess =
    CoreServices.SpatialAwarenessSystem as IMixedRealityDataProviderAccess;

if (dataProviderAccess != null)
{
    IReadOnlyList<IMixedRealitySpatialAwarenessMeshObserver> observers =
        dataProviderAccess.GetDataProviders<IMixedRealitySpatialAwarenessMeshObserver>();

    foreach (IMixedRealitySpatialAwarenessMeshObserver observer in observers)
    {
        // Set the mesh to use the occlusion material
        observer.DisplayOption = SpatialMeshDisplayOptions.Occlusion;
    }
}
```

Der Zugriff auf einen Datenanbieter für das Kernsystem für räumliche Wahrnehmung kann auch mithilfe der Hilfsklasse vereinfacht `CoreServices` werden.

```c#
var dataProvider = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();
if (dataProvider != null)
{
    // do something here
}
```

> [!NOTE]
> Das System für räumliche Wahrnehmung gibt nur Datenanbieter zurück, die für die Plattform unterstützt werden, auf der die Anwendung ausgeführt wird.

Informationen zum Schreiben eines Datenanbieters für das MRTK-System zur räumlichen Wahrnehmung finden Sie unter [Erstellen eines Datenanbieters für räumliche Wahrnehmungssysteme.](../features/spatial-awareness/create-data-provider.md)

## <a name="see-also"></a>Weitere Informationen

- [Erweiterungsdienste](../features/extensions/extension-services.md)
- [Erstellen eines Eingabesystemdatenanbieters](../features/input/create-data-provider.md)
- [Erstellen eines Systemdatenanbieters für räumliche Wahrnehmung](../features/spatial-awareness/create-data-provider.md)
- [IMixedRealityService-Schnittstelle](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService)
- [IMixedRealityDataProvider-Schnittstelle](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [IMixedRealityExtensionService-Schnittstelle](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
