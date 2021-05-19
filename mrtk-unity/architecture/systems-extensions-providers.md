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
# <a name="systems-extension-services-and-data-providers"></a><span data-ttu-id="1d6f6-104">Systeme, Erweiterungsdienste und Datenanbieter</span><span class="sxs-lookup"><span data-stu-id="1d6f6-104">Systems, extension services and data providers</span></span>

<span data-ttu-id="1d6f6-105">Im Mixed Reality Toolkit werden viele der Features in Form von Diensten bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="1d6f6-105">In the Mixed Reality Toolkit, many of the features are delivered in the form of services.</span></span> <span data-ttu-id="1d6f6-106">Dienste sind in drei Hauptkategorien unterteilt: Systeme, Erweiterungsdienste und Datenanbieter.</span><span class="sxs-lookup"><span data-stu-id="1d6f6-106">Services are grouped into three primary categories: systems, extension services and data providers.</span></span>

## <a name="systems"></a><span data-ttu-id="1d6f6-107">Systeme</span><span class="sxs-lookup"><span data-stu-id="1d6f6-107">Systems</span></span>

<span data-ttu-id="1d6f6-108">Systeme sind Dienste, die die Kernfunktionen des Mixed Reality Toolkits bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="1d6f6-108">Systems are services that provide the core functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="1d6f6-109">Alle Systeme sind Implementierungen der [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) -Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="1d6f6-109">All systems are implementations of the [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) interface.</span></span>

- [<span data-ttu-id="1d6f6-110">BoundarySystem</span><span class="sxs-lookup"><span data-stu-id="1d6f6-110">BoundarySystem</span></span>](../features/boundary/boundary-system-getting-started.md)
- [<span data-ttu-id="1d6f6-111">CameraSystem</span><span class="sxs-lookup"><span data-stu-id="1d6f6-111">CameraSystem</span></span>](../features/camera-system/camera-system-overview.md)
- [<span data-ttu-id="1d6f6-112">DiagnosticsSystem</span><span class="sxs-lookup"><span data-stu-id="1d6f6-112">DiagnosticsSystem</span></span>](../features/diagnostics/diagnostics-system-getting-started.md)
- [<span data-ttu-id="1d6f6-113">InputSystem</span><span class="sxs-lookup"><span data-stu-id="1d6f6-113">InputSystem</span></span>](../features/input/overview.md)
- [<span data-ttu-id="1d6f6-114">SceneSystem</span><span class="sxs-lookup"><span data-stu-id="1d6f6-114">SceneSystem</span></span>](../features/scene-system/scene-system-getting-started.md)
- [<span data-ttu-id="1d6f6-115">SpatialAwarenessSystem</span><span class="sxs-lookup"><span data-stu-id="1d6f6-115">SpatialAwarenessSystem</span></span>](../features/spatial-awareness/spatial-awareness-getting-started.md)
- [<span data-ttu-id="1d6f6-116">TeleportSystem</span><span class="sxs-lookup"><span data-stu-id="1d6f6-116">TeleportSystem</span></span>](../features/teleport-system/teleport-system.md)

<span data-ttu-id="1d6f6-117">Jedes der aufgeführten Systeme wird im Konfigurationsprofil der MixedRealityToolkit-Komponente [angezeigt.](../features/profiles/profiles.md)</span><span class="sxs-lookup"><span data-stu-id="1d6f6-117">Each of the listed systems are surfaced in the MixedRealityToolkit component's configuration [profile](../features/profiles/profiles.md).</span></span>

## <a name="extensions"></a><span data-ttu-id="1d6f6-118">-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="1d6f6-118">Extensions</span></span>

<span data-ttu-id="1d6f6-119">Erweiterungsdienste sind Komponenten, die die Funktionalität des Mixed Reality Toolkits erweitern.</span><span class="sxs-lookup"><span data-stu-id="1d6f6-119">Extension services are components that extend the functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="1d6f6-120">Alle Erweiterungsdienste müssen angeben, dass sie die [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) -Schnittstelle implementieren.</span><span class="sxs-lookup"><span data-stu-id="1d6f6-120">All extension services must specify that they implement the [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) interface.</span></span>

<span data-ttu-id="1d6f6-121">Informationen zum Erstellen von Erweiterungsdiensten finden Sie im Artikel [Erweiterungsdienste.](../features/extensions/extension-services.md)</span><span class="sxs-lookup"><span data-stu-id="1d6f6-121">For information on creating extension services, please reference the [Extension services](../features/extensions/extension-services.md) article.</span></span>

<span data-ttu-id="1d6f6-122">Um für das MRTK zugänglich zu sein, werden Erweiterungsdienste im Abschnitt Erweiterungen des Konfigurationsprofils der MixedRealityToolkit-Komponente registriert und konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="1d6f6-122">To be accessible to the MRTK, extension services are registered and configured using the Extensions section of the MixedRealityToolkit component's configuration profile.</span></span>

![Konfigurieren eines Erweiterungsdiensts](../features/images/profiles/ConfiguredExtensionService.png)

## <a name="data-providers"></a><span data-ttu-id="1d6f6-124">Datenanbieter</span><span class="sxs-lookup"><span data-stu-id="1d6f6-124">Data providers</span></span>

<span data-ttu-id="1d6f6-125">Datenanbieter sind Komponenten, die nach ihrem Namen Daten für einen Mixed Reality Toolkit-Dienst bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="1d6f6-125">Data providers are components that, per their name, provide data to a Mixed Reality Toolkit service.</span></span> <span data-ttu-id="1d6f6-126">Alle Datenanbieter müssen angeben, dass sie die -Schnittstelle [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) implementieren.</span><span class="sxs-lookup"><span data-stu-id="1d6f6-126">All data providers must specify that they implement the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!NOTE]
> <span data-ttu-id="1d6f6-127">Nicht alle Dienste erfordern Datenanbieter.</span><span class="sxs-lookup"><span data-stu-id="1d6f6-127">Not all services will require data providers.</span></span> <span data-ttu-id="1d6f6-128">Von den Mixed Reality Toolkits sind die Eingabe- und Räumliche Wahrnehmungssysteme die einzigen Dienste, die Datenanbieter nutzen.</span><span class="sxs-lookup"><span data-stu-id="1d6f6-128">Of the Mixed Reality Toolkit's systems, the Input and Spatial Awareness systems are the only services to utilize data providers.</span></span>

<span data-ttu-id="1d6f6-129">Um für den spezifischen MRTK-Dienst zugänglich zu sein, werden Datenanbieter im Konfigurationsprofil des Diensts registriert.</span><span class="sxs-lookup"><span data-stu-id="1d6f6-129">To be accessible to the specific MRTK service, data providers are registered in the service's configuration profile.</span></span>

<span data-ttu-id="1d6f6-130">Anwendungscode greifen über die -Schnittstelle auf Datenanbieter [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) zu.</span><span class="sxs-lookup"><span data-stu-id="1d6f6-130">Application code accesses data providers via the [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) interface.</span></span> <span data-ttu-id="1d6f6-131">Um den Zugriff zu vereinfachen, können Datenanbieter auch über die `CoreServices` Hilfsklasse abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="1d6f6-131">To simplify access, data providers can also be retrieved via the `CoreServices` helper class.</span></span>

```c#
var inputSimulationService = CoreServices.GetDataProvider<IInputSimulationService>(CoreServices.InputSystem);
```

> [!IMPORTANT]
> <span data-ttu-id="1d6f6-132">Obwohl `IMixedRealityDataProvider` von `IMixedRealityService` erbt, werden Datenanbieter nicht bei `MixedRealityServiceRegistry` registriert.</span><span class="sxs-lookup"><span data-stu-id="1d6f6-132">Although `IMixedRealityDataProvider` inherits from `IMixedRealityService`, data providers are not registered with the `MixedRealityServiceRegistry`.</span></span> <span data-ttu-id="1d6f6-133">Für den Zugriff auf Datenanbieter muss der Anwendungscode die Dienstinstanz abfragen, für die sie registriert wurden (z. B. Eingabesystem).</span><span class="sxs-lookup"><span data-stu-id="1d6f6-133">To access data providers, application code must query the service instance for which they were registered (ex: input system).</span></span>

### <a name="input"></a><span data-ttu-id="1d6f6-134">Eingabe</span><span class="sxs-lookup"><span data-stu-id="1d6f6-134">Input</span></span>

<span data-ttu-id="1d6f6-135">Das MRTK-Eingabesystem verwendet nur Datenanbieter, die [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) implementieren.</span><span class="sxs-lookup"><span data-stu-id="1d6f6-135">The MRTK input system utilizes only data providers that implement the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager).</span></span>

![Eingabesystemdatenanbieter](../features/images/input/RegisteredServiceProviders.PNG)

<span data-ttu-id="1d6f6-137">Im folgenden Beispiel wird der Zugriff auf den Eingabesimulationsanbieter und das Umschalten der SmoothEyeTracking-Eigenschaft veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="1d6f6-137">The following example demonstrates accessing the input simulation provider and toggle the SmoothEyeTracking property.</span></span>

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

<span data-ttu-id="1d6f6-138">Der Zugriff auf einen Datenanbieter für das Kerneingabesystem kann auch mithilfe der `CoreServices` Hilfsklasse vereinfacht werden.</span><span class="sxs-lookup"><span data-stu-id="1d6f6-138">Accessing a data provider for the core input system can also be simplified via use of the `CoreServices` helper class.</span></span>

```c#
var inputSimulationService = CoreServices.GetInputSystemDataProvider<IInputSimulationService>();
if (inputSimulationService != null)
{
    // do something here
}
```

> [!NOTE]
> <span data-ttu-id="1d6f6-139">Das Eingabesystem gibt nur Datenanbieter zurück, die für die Plattform unterstützt werden, auf der die Anwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="1d6f6-139">The input system returns only data providers that are supported for the platform on which the application is running.</span></span>

<span data-ttu-id="1d6f6-140">Informationen zum Schreiben eines Datenanbieters für das MRTK-Eingabesystem finden Sie unter [Erstellen eines Eingabesystem-Datenanbieters.](../features/input/create-data-provider.md)</span><span class="sxs-lookup"><span data-stu-id="1d6f6-140">For information on writing a data provider for the MRTK input system, please see [creating an input system data provider](../features/input/create-data-provider.md).</span></span>

### <a name="spatial-awareness"></a><span data-ttu-id="1d6f6-141">Räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="1d6f6-141">Spatial awareness</span></span>

<span data-ttu-id="1d6f6-142">Das MRTK-Raumerkennsystem nutzt nur Datenanbieter, die die -Schnittstelle [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) implementieren.</span><span class="sxs-lookup"><span data-stu-id="1d6f6-142">The MRTK spatial awareness system utilizes only data providers that implement the [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface.</span></span>

![Anbieter von Räumlichen Wahrnehmungssystemdaten](../features/images/spatial-awareness/SpatialAwarenessProfile.png)

<span data-ttu-id="1d6f6-144">Im folgenden Beispiel wird der Zugriff auf die registrierten Räumlichen Gitternetz-Datenanbieter und das Ändern der Sichtbarkeit der Gitternetze veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="1d6f6-144">The following example demonstrates accessing the registered spatial mesh data providers and changing the visibility of the meshes.</span></span>

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

<span data-ttu-id="1d6f6-145">Der Zugriff auf einen Datenanbieter für das Kernsystem für räumliche Wahrnehmung kann auch mithilfe der Hilfsklasse vereinfacht `CoreServices` werden.</span><span class="sxs-lookup"><span data-stu-id="1d6f6-145">Accessing a data provider for the core spatial awareness system can also be simplified via use of the `CoreServices` helper class.</span></span>

```c#
var dataProvider = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();
if (dataProvider != null)
{
    // do something here
}
```

> [!NOTE]
> <span data-ttu-id="1d6f6-146">Das System für räumliche Wahrnehmung gibt nur Datenanbieter zurück, die für die Plattform unterstützt werden, auf der die Anwendung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="1d6f6-146">The spatial awareness system returns only data providers that are supported for the platform on which the application is running.</span></span>

<span data-ttu-id="1d6f6-147">Informationen zum Schreiben eines Datenanbieters für das MRTK-System zur räumlichen Wahrnehmung finden Sie unter [Erstellen eines Datenanbieters für räumliche Wahrnehmungssysteme.](../features/spatial-awareness/create-data-provider.md)</span><span class="sxs-lookup"><span data-stu-id="1d6f6-147">For information on writing a data provider for the MRTK spatial awareness system, please see [creating a spatial awareness system data provider](../features/spatial-awareness/create-data-provider.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1d6f6-148">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="1d6f6-148">See also</span></span>

- [<span data-ttu-id="1d6f6-149">Erweiterungsdienste</span><span class="sxs-lookup"><span data-stu-id="1d6f6-149">Extension services</span></span>](../features/extensions/extension-services.md)
- [<span data-ttu-id="1d6f6-150">Erstellen eines Eingabesystemdatenanbieters</span><span class="sxs-lookup"><span data-stu-id="1d6f6-150">Creating an input system data provider</span></span>](../features/input/create-data-provider.md)
- [<span data-ttu-id="1d6f6-151">Erstellen eines Systemdatenanbieters für räumliche Wahrnehmung</span><span class="sxs-lookup"><span data-stu-id="1d6f6-151">Creating a spatial awareness system system data provider</span></span>](../features/spatial-awareness/create-data-provider.md)
- [<span data-ttu-id="1d6f6-152">IMixedRealityService-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="1d6f6-152">IMixedRealityService interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService)
- [<span data-ttu-id="1d6f6-153">IMixedRealityDataProvider-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="1d6f6-153">IMixedRealityDataProvider interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [<span data-ttu-id="1d6f6-154">IMixedRealityExtensionService-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="1d6f6-154">IMixedRealityExtensionService interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
