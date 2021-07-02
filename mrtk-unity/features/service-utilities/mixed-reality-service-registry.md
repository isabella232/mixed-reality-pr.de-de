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
# <a name="mixed-reality-service-registry"></a><span data-ttu-id="1d529-104">Mixed Reality-Dienstregistrierung</span><span class="sxs-lookup"><span data-stu-id="1d529-104">Mixed Reality service registry</span></span>

<span data-ttu-id="1d529-105">Das Mixed Reality Toolkit verfügt über zwei sehr ähnlich benannte Komponenten, die verwandte Aufgaben ausführen: MixedRealityServiceRegistry und IMixedRealityServiceRegistrar.</span><span class="sxs-lookup"><span data-stu-id="1d529-105">The Mixed Reality Toolkit has two very similarly named components that perform related tasks: MixedRealityServiceRegistry and IMixedRealityServiceRegistrar.</span></span>

## <a name="mixedrealityserviceregistry"></a><span data-ttu-id="1d529-106">MixedRealityServiceRegistry</span><span class="sxs-lookup"><span data-stu-id="1d529-106">MixedRealityServiceRegistry</span></span>

<span data-ttu-id="1d529-107">[MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) ist die Komponente, die Instanzen jedes registrierten Diensts (Kernsysteme und Erweiterungsdienste) enthält.</span><span class="sxs-lookup"><span data-stu-id="1d529-107">The [MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) is the component that contains instances of each registered service (core systems and extension services).</span></span>

> [!NOTE]
> <span data-ttu-id="1d529-108">MixedRealityServiceRegistry enthält Instanzen von -Objekten, die die [IMixedRealityService-Schnittstelle](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) implementieren, einschließlich [IMixedRealityExtensionService.](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)</span><span class="sxs-lookup"><span data-stu-id="1d529-108">The MixedRealityServiceRegistry contains instances of objects that implement [IMixedRealityService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) interface, including [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService).</span></span>
>
><span data-ttu-id="1d529-109">Objekte, die [IMixedRealityDataProvider](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) (eine Unterklasse von IMixedRealityService) implementieren, werden explizit nicht in MixedRealityServiceRegistry registriert.</span><span class="sxs-lookup"><span data-stu-id="1d529-109">Objects implementing the [IMixedRealityDataProvider](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) (a subclass of IMixedRealityService) are explicitly not registered in the MixedRealityServiceRegistry.</span></span> <span data-ttu-id="1d529-110">Diese Objekte werden von den einzelnen Diensten verwaltet (z. B. Räumliche Wahrnehmung).</span><span class="sxs-lookup"><span data-stu-id="1d529-110">These objects are managed by the individual services (ex: Spatial Awareness).</span></span>

<span data-ttu-id="1d529-111">MixedRealityServiceRegistry wird als statische C#-Klasse implementiert und ist das empfohlene Muster zum Abrufen von Dienstinstanzen im Anwendungscode.</span><span class="sxs-lookup"><span data-stu-id="1d529-111">The MixedRealityServiceRegistry is implemented as a static C# class and is the recommended pattern to use to acquire service instances in application code.</span></span>

<span data-ttu-id="1d529-112">Der folgende Codeausschnitt veranschaulicht das Abrufen einer IMixedRealityInputSystem-Instanz.</span><span class="sxs-lookup"><span data-stu-id="1d529-112">The following snippet demonstrates acquiring an IMixedRealityInputSystem instance.</span></span>

```c#
IMixedRealityInputSystem inputSystem = null;

if (!MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
{
    // Failed to acquire the input system. It may not have been registered
}
```

## <a name="imixedrealityserviceregistrar"></a><span data-ttu-id="1d529-113">IMixedRealityServiceRegistrar</span><span class="sxs-lookup"><span data-stu-id="1d529-113">IMixedRealityServiceRegistrar</span></span>

<span data-ttu-id="1d529-114">[IMixedRealityServiceRegistrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) ist die Schnittstelle, die die Funktionalität definiert, die von Komponenten implementiert wird, die die Registrierung eines oder mehrerer Dienste verwalten.</span><span class="sxs-lookup"><span data-stu-id="1d529-114">The [IMixedRealityServiceRegistrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) is the interface that defines the functionality implemented by components that manage the registration of one or more services.</span></span> <span data-ttu-id="1d529-115">Komponenten, die IMixedRealityServiceRegistrar implementieren, sind für das Hinzufügen und Entfernen der Daten in MixedRealityServiceRegistry verantwortlich.</span><span class="sxs-lookup"><span data-stu-id="1d529-115">Components that implement IMixedRealityServiceRegistrar are responsible for adding and removing the data within the MixedRealityServiceRegistry.</span></span> <span data-ttu-id="1d529-116">Das [MixedRealityToolkit-Objekt](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) ist eine solche Komponente.</span><span class="sxs-lookup"><span data-stu-id="1d529-116">The [MixedRealityToolkit](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) object is one such component.</span></span>

<span data-ttu-id="1d529-117">Andere Registrierungsstellen finden Sie im Ordner MRTK/SDK/Experimental/Features.</span><span class="sxs-lookup"><span data-stu-id="1d529-117">Other registrars can be found in the MRTK/SDK/Experimental/Features folder.</span></span> <span data-ttu-id="1d529-118">Diese Komponenten können verwendet werden, um einer Anwendung unterstützung für einen einzelnen Dienst (z. B. räumliche Wahrnehmung) hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="1d529-118">These components can be used to add single service (ex: Spatial Awareness) support to an application.</span></span> <span data-ttu-id="1d529-119">Diese einzelnen Dienst-Manager sind unten aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="1d529-119">These single service managers are listed below.</span></span>

- [<span data-ttu-id="1d529-120">BoundarySystemManager</span><span class="sxs-lookup"><span data-stu-id="1d529-120">BoundarySystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Boundary.BoundarySystemManager)
- [<span data-ttu-id="1d529-121">CameraSystemManager</span><span class="sxs-lookup"><span data-stu-id="1d529-121">CameraSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.CameraSystem.CameraSystemManager)
- [<span data-ttu-id="1d529-122">DiagnosticsSystemManager</span><span class="sxs-lookup"><span data-stu-id="1d529-122">DiagnosticsSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Diagnostics.DiagnosticsSystemManager)
- [<span data-ttu-id="1d529-123">InputSystemManager</span><span class="sxs-lookup"><span data-stu-id="1d529-123">InputSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Input.InputSystemManager)
- [<span data-ttu-id="1d529-124">SpatialAwarenessSystemManager</span><span class="sxs-lookup"><span data-stu-id="1d529-124">SpatialAwarenessSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSystemManager)
- [<span data-ttu-id="1d529-125">TeleportSystemManager</span><span class="sxs-lookup"><span data-stu-id="1d529-125">TeleportSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Teleport.TeleportSystemManager)

<span data-ttu-id="1d529-126">Jede der oben genannten Komponenten, mit Ausnahme von InputSystemManager, ist für die Verwaltung der Registrierung und des Status eines einzelnen Diensttyps verantwortlich.</span><span class="sxs-lookup"><span data-stu-id="1d529-126">Each of the above components, with the exception of the InputSystemManager, are responsible for managing the registration and status of a single service type.</span></span> <span data-ttu-id="1d529-127">Das InputSystem erfordert einige zusätzliche Supportdienste (z. B. FocusProvider), die auch vom InputSystemManager verwaltet werden.</span><span class="sxs-lookup"><span data-stu-id="1d529-127">The InputSystem requires some additional support services (ex: FocusProvider) that are also managed by the InputSystemManager.</span></span>

<span data-ttu-id="1d529-128">Im Allgemeinen werden die von IMixedRealityServiceRegistrar definierten Methoden intern von Dienstverwaltungskomponenten oder von Diensten aufgerufen, die zusätzliche Dienstkomponenten benötigen, um ordnungsgemäß zu funktionieren.</span><span class="sxs-lookup"><span data-stu-id="1d529-128">In general, the methods defined by IMixedRealityServiceRegistrar are called internally by service management components or called by services that require additional service components to function correctly.</span></span> <span data-ttu-id="1d529-129">Anwendungscode sollte diese Methoden im Allgemeinen nicht aufrufen, da dies dazu führen kann, dass sich die Anwendung unvorhersehbar verhält (z. B. kann eine zwischengespeicherte Dienstinstanz ungültig werden).</span><span class="sxs-lookup"><span data-stu-id="1d529-129">Application code should, generally, not call these methods as doing so may cause the application to behave unpredictably (ex: a cached service instance may become invalid).</span></span>

## <a name="see-also"></a><span data-ttu-id="1d529-130">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="1d529-130">See also</span></span>

- [<span data-ttu-id="1d529-131">IMixedRealityServiceRegistrar-API-Dokumentation</span><span class="sxs-lookup"><span data-stu-id="1d529-131">IMixedRealityServiceRegistrar API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar)
- [<span data-ttu-id="1d529-132">Dokumentation zur MixedRealityServiceRegistry-API</span><span class="sxs-lookup"><span data-stu-id="1d529-132">MixedRealityServiceRegistry API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)
