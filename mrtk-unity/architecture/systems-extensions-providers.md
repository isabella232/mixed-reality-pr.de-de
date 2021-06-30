---
title: Systemerweiterungsanbieter
description: MRTK-Erweiterungen und Datenanbieter
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Systemerweiterungen,
ms.openlocfilehash: 358294702971b7d9e8de1b842d3bc1844e5dc9bf
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121468"
---
# <a name="systems-extension-services-and-data-providers"></a><span data-ttu-id="f5b72-104">Systeme, Erweiterungsdienste und Datenanbieter</span><span class="sxs-lookup"><span data-stu-id="f5b72-104">Systems, extension services and data providers</span></span>

<span data-ttu-id="f5b72-105">Im Mixed Reality Toolkit werden viele der Features in Form von Diensten bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="f5b72-105">In the Mixed Reality Toolkit, many of the features are delivered in the form of services.</span></span> <span data-ttu-id="f5b72-106">Dienste sind in drei Hauptkategorien unterteilt: Systeme, Erweiterungsdienste und Datenanbieter.</span><span class="sxs-lookup"><span data-stu-id="f5b72-106">Services are grouped into three primary categories: systems, extension services and data providers.</span></span>

## <a name="systems"></a><span data-ttu-id="f5b72-107">Systeme</span><span class="sxs-lookup"><span data-stu-id="f5b72-107">Systems</span></span>

<span data-ttu-id="f5b72-108">Systeme sind Dienste, die die Kernfunktionen des Mixed Reality Toolkits bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="f5b72-108">Systems are services that provide the core functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="f5b72-109">Alle Systeme sind Implementierungen der [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) -Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="f5b72-109">All systems are implementations of the [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) interface.</span></span>

- [<span data-ttu-id="f5b72-110">BoundarySystem</span><span class="sxs-lookup"><span data-stu-id="f5b72-110">BoundarySystem</span></span>](../features/boundary/boundary-system-getting-started.md)
- [<span data-ttu-id="f5b72-111">CameraSystem</span><span class="sxs-lookup"><span data-stu-id="f5b72-111">CameraSystem</span></span>](../features/camera-system/camera-system-overview.md)
- [<span data-ttu-id="f5b72-112">DiagnosticsSystem</span><span class="sxs-lookup"><span data-stu-id="f5b72-112">DiagnosticsSystem</span></span>](../features/diagnostics/diagnostics-system-getting-started.md)
- [<span data-ttu-id="f5b72-113">InputSystem</span><span class="sxs-lookup"><span data-stu-id="f5b72-113">InputSystem</span></span>](../features/input/overview.md)
- [<span data-ttu-id="f5b72-114">SceneSystem</span><span class="sxs-lookup"><span data-stu-id="f5b72-114">SceneSystem</span></span>](../features/scene-system/scene-system-getting-started.md)
- [<span data-ttu-id="f5b72-115">SpatialAwarenessSystem</span><span class="sxs-lookup"><span data-stu-id="f5b72-115">SpatialAwarenessSystem</span></span>](../features/spatial-awareness/spatial-awareness-getting-started.md)
- [<span data-ttu-id="f5b72-116">TeleportSystem</span><span class="sxs-lookup"><span data-stu-id="f5b72-116">TeleportSystem</span></span>](../features/teleport-system/teleport-system.md)

<span data-ttu-id="f5b72-117">Jedes der aufgeführten Systeme wird im Konfigurationsprofil der MixedRealityToolkit-Komponente [angezeigt.](../features/profiles/profiles.md)</span><span class="sxs-lookup"><span data-stu-id="f5b72-117">Each of the listed systems are surfaced in the MixedRealityToolkit component's configuration [profile](../features/profiles/profiles.md).</span></span>

## <a name="extensions"></a><span data-ttu-id="f5b72-118">Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="f5b72-118">Extensions</span></span>

<span data-ttu-id="f5b72-119">Erweiterungsdienste sind Komponenten, die die Funktionalität des Mixed Reality-Toolkits erweitern.</span><span class="sxs-lookup"><span data-stu-id="f5b72-119">Extension services are components that extend the functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="f5b72-120">Alle Erweiterungsdienste müssen angeben, dass sie die -Schnittstelle [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) implementieren.</span><span class="sxs-lookup"><span data-stu-id="f5b72-120">All extension services must specify that they implement the [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) interface.</span></span>

<span data-ttu-id="f5b72-121">Informationen zum Erstellen von Erweiterungsdiensten finden Sie im Artikel [Erweiterungsdienste.](../features/extensions/extension-services.md)</span><span class="sxs-lookup"><span data-stu-id="f5b72-121">For information on creating extension services, please reference the [Extension services](../features/extensions/extension-services.md) article.</span></span>

<span data-ttu-id="f5b72-122">Um für das MRTK zugänglich zu sein, werden Erweiterungsdienste mithilfe des Abschnitts Erweiterungen des Konfigurationsprofils der MixedRealityToolkit-Komponente registriert und konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="f5b72-122">To be accessible to the MRTK, extension services are registered and configured using the Extensions section of the MixedRealityToolkit component's configuration profile.</span></span>

![Konfigurieren eines Erweiterungsdiensts](../features/images/profiles/ConfiguredExtensionService.png)

## <a name="data-providers"></a><span data-ttu-id="f5b72-124">Datenanbieter</span><span class="sxs-lookup"><span data-stu-id="f5b72-124">Data providers</span></span>

<span data-ttu-id="f5b72-125">Datenanbieter sind Komponenten, die nach ihrem Namen Daten für einen Mixed Reality Toolkit-Dienst bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="f5b72-125">Data providers are components that, per their name, provide data to a Mixed Reality Toolkit service.</span></span> <span data-ttu-id="f5b72-126">Alle Datenanbieter müssen angeben, dass sie die -Schnittstelle [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) implementieren.</span><span class="sxs-lookup"><span data-stu-id="f5b72-126">All data providers must specify that they implement the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!NOTE]
> <span data-ttu-id="f5b72-127">Nicht alle Dienste erfordern Datenanbieter.</span><span class="sxs-lookup"><span data-stu-id="f5b72-127">Not all services will require data providers.</span></span> <span data-ttu-id="f5b72-128">Von den Mixed Reality Toolkits sind die Eingabe- und Räumliche Wahrnehmungssysteme die einzigen Dienste, die Datenanbieter nutzen.</span><span class="sxs-lookup"><span data-stu-id="f5b72-128">Of the Mixed Reality Toolkit's systems, the Input and Spatial Awareness systems are the only services to utilize data providers.</span></span>

<span data-ttu-id="f5b72-129">Um für den spezifischen MRTK-Dienst zugänglich zu sein, werden Datenanbieter im Konfigurationsprofil des Diensts registriert.</span><span class="sxs-lookup"><span data-stu-id="f5b72-129">To be accessible to the specific MRTK service, data providers are registered in the service's configuration profile.</span></span>

<span data-ttu-id="f5b72-130">Anwendungscode greifen über die -Schnittstelle auf Datenanbieter [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) zu.</span><span class="sxs-lookup"><span data-stu-id="f5b72-130">Application code accesses data providers via the [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) interface.</span></span> <span data-ttu-id="f5b72-131">Um den Zugriff zu vereinfachen, können Datenanbieter auch über die `CoreServices` Hilfsklasse abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="f5b72-131">To simplify access, data providers can also be retrieved via the `CoreServices` helper class.</span></span>

```c#
var inputSimulationService = CoreServices.GetDataProvider<IInputSimulationService>(CoreServices.InputSystem);
```

> [!IMPORTANT]
> <span data-ttu-id="f5b72-132">Obwohl `IMixedRealityDataProvider` von `IMixedRealityService` erbt, werden Datenanbieter nicht bei `MixedRealityServiceRegistry` registriert.</span><span class="sxs-lookup"><span data-stu-id="f5b72-132">Although `IMixedRealityDataProvider` inherits from `IMixedRealityService`, data providers are not registered with the `MixedRealityServiceRegistry`.</span></span> <span data-ttu-id="f5b72-133">Für den Zugriff auf Datenanbieter muss der Anwendungscode die Dienstinstanz abfragen, für die sie registriert wurden (z. B. Eingabesystem).</span><span class="sxs-lookup"><span data-stu-id="f5b72-133">To access data providers, application code must query the service instance for which they were registered (ex: input system).</span></span>

### <a name="input"></a><span data-ttu-id="f5b72-134">Eingabe</span><span class="sxs-lookup"><span data-stu-id="f5b72-134">Input</span></span>

<span data-ttu-id="f5b72-135">Das MRTK-Eingabesystem verwendet nur Datenanbieter, die [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) implementieren.</span><span class="sxs-lookup"><span data-stu-id="f5b72-135">The MRTK input system utilizes only data providers that implement the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager).</span></span>

![Eingabesystemdatenanbieter](../features/images/input/RegisteredServiceProviders.PNG)

<span data-ttu-id="f5b72-137">Im folgenden Beispiel wird der Zugriff auf den Eingabesimulationsanbieter und das Umschalten der SmoothEyeTracking-Eigenschaft veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="f5b72-137">The following example demonstrates accessing the input simulation provider and toggle the SmoothEyeTracking property.</span></span>

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

<span data-ttu-id="f5b72-138">Der Zugriff auf einen Datenanbieter für das Kerneingabesystem kann auch mithilfe der `CoreServices` Hilfsklasse vereinfacht werden.</span><span class="sxs-lookup"><span data-stu-id="f5b72-138">Accessing a data provider for the core input system can also be simplified via use of the `CoreServices` helper class.</span></span>

```c#
var inputSimulationService = CoreServices.GetInputSystemDataProvider<IInputSimulationService>();
if (inputSimulationService != null)
{
    // do something here
}
```

> [!NOTE]
> <span data-ttu-id="f5b72-139">Das Eingabesystem gibt nur Datenanbieter zurück, die für die Plattform unterstützt werden, auf der die Anwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="f5b72-139">The input system returns only data providers that are supported for the platform on which the application is running.</span></span>

<span data-ttu-id="f5b72-140">Informationen zum Schreiben eines Datenanbieters für das MRTK-Eingabesystem finden Sie unter [Erstellen eines Eingabesystemdatenanbieters.](../features/input/create-data-provider.md)</span><span class="sxs-lookup"><span data-stu-id="f5b72-140">For information on writing a data provider for the MRTK input system, please see [creating an input system data provider](../features/input/create-data-provider.md).</span></span>

### <a name="spatial-awareness"></a><span data-ttu-id="f5b72-141">Räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="f5b72-141">Spatial awareness</span></span>

<span data-ttu-id="f5b72-142">Das MRTK-Raumbewusstseinssystem nutzt nur Datenanbieter, die die -Schnittstelle [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) implementieren.</span><span class="sxs-lookup"><span data-stu-id="f5b72-142">The MRTK spatial awareness system utilizes only data providers that implement the [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface.</span></span>

![Anbieter von Räumlichen Wahrnehmungssystemdaten](../features/images/spatial-awareness/SpatialAwarenessProfile.png)

<span data-ttu-id="f5b72-144">Im folgenden Beispiel wird der Zugriff auf die registrierten Räumlichen Gitternetz-Datenanbieter und das Ändern der Sichtbarkeit der Gitternetze veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="f5b72-144">The following example demonstrates accessing the registered spatial mesh data providers and changing the visibility of the meshes.</span></span>

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

<span data-ttu-id="f5b72-145">Der Zugriff auf einen Datenanbieter für das zentrale räumliche Bewusstseinssystem kann auch mithilfe der `CoreServices` Hilfsklasse vereinfacht werden.</span><span class="sxs-lookup"><span data-stu-id="f5b72-145">Accessing a data provider for the core spatial awareness system can also be simplified via use of the `CoreServices` helper class.</span></span>

```c#
var dataProvider = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();
if (dataProvider != null)
{
    // do something here
}
```

> [!NOTE]
> <span data-ttu-id="f5b72-146">Das Räumliche Bewusstseinssystem gibt nur Datenanbieter zurück, die für die Plattform unterstützt werden, auf der die Anwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="f5b72-146">The spatial awareness system returns only data providers that are supported for the platform on which the application is running.</span></span>

<span data-ttu-id="f5b72-147">Informationen zum Schreiben eines Datenanbieters für das MRTK-System für räumliche Wahrnehmung finden Sie unter Erstellen eines Systemdatenanbieters für [räumliche Wahrnehmung.](../features/spatial-awareness/create-data-provider.md)</span><span class="sxs-lookup"><span data-stu-id="f5b72-147">For information on writing a data provider for the MRTK spatial awareness system, please see [creating a spatial awareness system data provider](../features/spatial-awareness/create-data-provider.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f5b72-148">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f5b72-148">See also</span></span>

- [<span data-ttu-id="f5b72-149">Erweiterungsdienste</span><span class="sxs-lookup"><span data-stu-id="f5b72-149">Extension services</span></span>](../features/extensions/extension-services.md)
- [<span data-ttu-id="f5b72-150">Erstellen eines Eingabesystemdatenanbieters</span><span class="sxs-lookup"><span data-stu-id="f5b72-150">Creating an input system data provider</span></span>](../features/input/create-data-provider.md)
- [<span data-ttu-id="f5b72-151">Erstellen eines Systemdatenanbieters für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="f5b72-151">Creating a spatial awareness system system data provider</span></span>](../features/spatial-awareness/create-data-provider.md)
- [<span data-ttu-id="f5b72-152">IMixedRealityService-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="f5b72-152">IMixedRealityService interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService)
- [<span data-ttu-id="f5b72-153">IMixedRealityDataProvider-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="f5b72-153">IMixedRealityDataProvider interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [<span data-ttu-id="f5b72-154">IMixedRealityExtensionService-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="f5b72-154">IMixedRealityExtensionService interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
