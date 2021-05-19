---
title: MRTK-Modularisierung
description: Beschreibt die Komponentenisierung in MRTK.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 04b2e6155e591a918b95aed20961a0450afe5f43
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144419"
---
# <a name="mixed-reality-toolkit-componentization"></a><span data-ttu-id="3f5fa-104">Mixed Reality Toolkit-Komponenten</span><span class="sxs-lookup"><span data-stu-id="3f5fa-104">Mixed Reality Toolkit componentization</span></span>

<span data-ttu-id="3f5fa-105">Eines der hervorragenden neuen Features von Mixed Reality Toolkit v2 ist die verbesserte Komponentenisierung.</span><span class="sxs-lookup"><span data-stu-id="3f5fa-105">One of the great new features of Mixed Reality Toolkit v2 is improved componentization.</span></span> <span data-ttu-id="3f5fa-106">Nach Möglichkeit sind einzelne Komponenten von allen Komponenten bis auf die Kernebene der Grundlage isoliert.</span><span class="sxs-lookup"><span data-stu-id="3f5fa-106">Wherever possible, individual components are isolated from all but the core layer of the foundation.</span></span>

## <a name="minimized-dependencies"></a><span data-ttu-id="3f5fa-107">Minimierte Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="3f5fa-107">Minimized dependencies</span></span>

<span data-ttu-id="3f5fa-108">MRTK v2 wurde absichtlich entwickelt, um modular zu sein und Abhängigkeiten zwischen Systemdiensten zu minimieren (z. B. räumliche Wahrnehmung).</span><span class="sxs-lookup"><span data-stu-id="3f5fa-108">MRTK v2 was intentionally developed to be modular and to minimize dependencies between system services (ex: spatial awareness).</span></span>

<span data-ttu-id="3f5fa-109">Aufgrund der Art einiger Systemdienste (z. B. Eingabe und Teleportierung) gibt es eine kleine Anzahl von Abhängigkeiten.</span><span class="sxs-lookup"><span data-stu-id="3f5fa-109">Due to the nature of some system services (ex: input and teleportation), a small number of dependencies exist.</span></span>

<span data-ttu-id="3f5fa-110">Es ist zwar zu erwarten, dass Dienste eine oder mehrere Datenanbieterkomponenten benötigen, es gibt jedoch keine direkten Verknüpfungen zwischen ihnen.</span><span class="sxs-lookup"><span data-stu-id="3f5fa-110">While it is expected that services will need one or more data provider components, there are no direct links between them.</span></span> <span data-ttu-id="3f5fa-111">Dasselbe gilt für SDK-Features (z. B. Benutzeroberfläche Komponenten).</span><span class="sxs-lookup"><span data-stu-id="3f5fa-111">The same is true for SDK features (ex: User Interface components).</span></span>

## <a name="component-communication"></a><span data-ttu-id="3f5fa-112">Komponentenkommunikation</span><span class="sxs-lookup"><span data-stu-id="3f5fa-112">Component communication</span></span>

<span data-ttu-id="3f5fa-113">Um sicherzustellen, dass es keine direkten Verknüpfungen zwischen Komponenten gibt, verwendet MRTK v2 Schnittstellen für die Kommunikation zwischen Diensten, Datenanbietern und Anwendungscode.</span><span class="sxs-lookup"><span data-stu-id="3f5fa-113">To ensure that there are no direct links between components, MRTK v2 utilizes interfaces to communicate between services, data providers and application code.</span></span> <span data-ttu-id="3f5fa-114">Diese Schnittstellen werden in definiert, und die gesamte Kommunikation wird über die Mixed Reality Toolkit-Kernkomponente geleitet.</span><span class="sxs-lookup"><span data-stu-id="3f5fa-114">These interfaces are defined in and all communication is routed through the Mixed Reality Toolkit core component.</span></span>

![Verwenden des Räumlichen Wahrnehmungssystems über Schnittstellen](../features/images/packaging/AccessingViaInterfaces.png)

## <a name="minimizing-mrtk-import-footprint"></a><span data-ttu-id="3f5fa-116">Minimieren des MRTK-Importbedarfs</span><span class="sxs-lookup"><span data-stu-id="3f5fa-116">Minimizing MRTK import footprint</span></span>

<span data-ttu-id="3f5fa-117">Derzeit wird das MRTK als einzelnes Basispaket importiert (wobei das Vorhandensein des Beispielpakets, das ein vollständig optionales Paket ist, für einen Moment ignoriert wird).</span><span class="sxs-lookup"><span data-stu-id="3f5fa-117">At this moment, the MRTK is imported as a single foundation package (ignoring for a moment the existence of the examples package, which is a completely optional package).</span></span> <span data-ttu-id="3f5fa-118">Es ist möglich, diesen Speicherbedarf zu verringern, indem Sie die importierten Dateien manuell reduzieren. Dies ist jedoch ein sehr manueller Prozess, der keine genau definierte Anleitung enthält.</span><span class="sxs-lookup"><span data-stu-id="3f5fa-118">It is possible to make this footprint smaller by manually cutting down on the files imported, though this is a highly manual process which doesn't have a well-defined guide.</span></span>

<span data-ttu-id="3f5fa-119">Es ist möglich, beliebige Elemente während des Imports des Foundation-Pakets zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="3f5fa-119">It is possible to uncheck arbitrary items during the import of the Foundation package.</span></span> <span data-ttu-id="3f5fa-120">Es wird jedoch nicht empfohlen, dies zu einem frühen Zeitpunkt in der Entwicklung zu tun, da dies die Funktionalität beeinträchtigen kann.</span><span class="sxs-lookup"><span data-stu-id="3f5fa-120">However, it's not recommended to do this at an early stage in development as it might break functionality.</span></span> <span data-ttu-id="3f5fa-121">Nachdem Sie den endgültigen Featuresatz einer App herausgefunden haben, können Sie nicht benötigte Anbieter und Dienste in den folgenden Ordnern löschen:</span><span class="sxs-lookup"><span data-stu-id="3f5fa-121">After having figured out the final feature set of an app, pruning unneeded providers and services can be done on the following folders:</span></span>

- <span data-ttu-id="3f5fa-122">MRTK/Services</span><span class="sxs-lookup"><span data-stu-id="3f5fa-122">MRTK/Services</span></span>
- <span data-ttu-id="3f5fa-123">MRTK/Providers</span><span class="sxs-lookup"><span data-stu-id="3f5fa-123">MRTK/Providers</span></span>
- <span data-ttu-id="3f5fa-124">MRTK/SDK/Features</span><span class="sxs-lookup"><span data-stu-id="3f5fa-124">MRTK/SDK/Features</span></span>

> [!NOTE]
> <span data-ttu-id="3f5fa-125">MRTK v2.x **_erfordert_** den Inhalt des Ordners Assets/MRTK/Core.</span><span class="sxs-lookup"><span data-stu-id="3f5fa-125">MRTK v2.x **_requires_** the contents of the Assets/MRTK/Core folder.</span></span>

## <a name="upcoming-features"></a><span data-ttu-id="3f5fa-126">Nächste Features</span><span class="sxs-lookup"><span data-stu-id="3f5fa-126">Upcoming features</span></span>

### <a name="application-architecture"></a><span data-ttu-id="3f5fa-127">Anwendungsarchitektur</span><span class="sxs-lookup"><span data-stu-id="3f5fa-127">Application architecture</span></span>

<span data-ttu-id="3f5fa-128">Das MRTK bietet Unterstützung für die Entwicklung von Anwendungen mit einer Vielzahl von Architekturen, einschließlich:</span><span class="sxs-lookup"><span data-stu-id="3f5fa-128">The MRTK will have support to enable applications to be built with a variety of architectures, including:</span></span>

- [<span data-ttu-id="3f5fa-129">MixedRealityToolkit-Dienstlocator</span><span class="sxs-lookup"><span data-stu-id="3f5fa-129">MixedRealityToolkit service locator</span></span>](#mixedrealitytoolkit-service-locator)
- [<span data-ttu-id="3f5fa-130">Einzelne Dienste</span><span class="sxs-lookup"><span data-stu-id="3f5fa-130">Individual services</span></span>](#individual-service-components)
- [<span data-ttu-id="3f5fa-131">Benutzerdefinierter Dienstlocator</span><span class="sxs-lookup"><span data-stu-id="3f5fa-131">Custom service locator</span></span>](#custom-service-locator)
- [<span data-ttu-id="3f5fa-132">Hybridarchitektur</span><span class="sxs-lookup"><span data-stu-id="3f5fa-132">Hybrid architecture</span></span>](#hybrid-architecture)

<span data-ttu-id="3f5fa-133">Bei der Auswahl einer Anwendungsarchitektur ist es wichtig, Entwurfsflexibilität und Anwendungsleistung zu berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="3f5fa-133">When selecting an application architecture, it is important to consider design flexibility and application performance.</span></span> <span data-ttu-id="3f5fa-134">Es wird nicht erwartet, dass die hier beschriebenen Architekturen für jede Anwendung geeignet sind.</span><span class="sxs-lookup"><span data-stu-id="3f5fa-134">The architectures described here are not expected to be suitable for every application.</span></span>

#### <a name="mixedrealitytoolkit-service-locator"></a><span data-ttu-id="3f5fa-135">MixedRealityToolkit-Dienstlocator</span><span class="sxs-lookup"><span data-stu-id="3f5fa-135">MixedRealityToolkit service locator</span></span>

<span data-ttu-id="3f5fa-136">Das MRTK ermöglicht (und konfiguriert) Anwendungsszenen automatisch, um die Standardmäßige [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) Dienstlocatorkomponente zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="3f5fa-136">The MRTK enables (and automatically configures) application scenes to use the default [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) service locator component.</span></span> <span data-ttu-id="3f5fa-137">Diese Komponente bietet Unterstützung für die Konfiguration von MRTK-Systemen und -Datenanbietern über Konfigurationsinspektoren und verwaltet die Lebensdauer und das Kernverhalten von Komponenten (z. B. wann aktualisiert werden soll).</span><span class="sxs-lookup"><span data-stu-id="3f5fa-137">This component includes support for configuring MRTK systems and data providers via configuration inspectors and manages component lifespans and core behaviors (ex: when to update).</span></span>

<span data-ttu-id="3f5fa-138">Alle Systeme werden im Hauptkonfigurationsinspektor dargestellt, unabhängig davon, ob sie im Projekt vorhanden oder aktiviert sind.</span><span class="sxs-lookup"><span data-stu-id="3f5fa-138">All systems are represented in the core configuration inspector, regardless of whether or not they are present or enabled in the project.</span></span> <span data-ttu-id="3f5fa-139">Weitere Informationen finden [Sie Mixed Reality-Konfigurationshandbuch.](../configuration/mixed-reality-configuration-guide.md)</span><span class="sxs-lookup"><span data-stu-id="3f5fa-139">Please see the [Mixed Reality Configuration Guide](../configuration/mixed-reality-configuration-guide.md) for more information.</span></span>

#### <a name="individual-service-components"></a><span data-ttu-id="3f5fa-140">Einzelne Dienstkomponenten</span><span class="sxs-lookup"><span data-stu-id="3f5fa-140">Individual service components</span></span>

<span data-ttu-id="3f5fa-141">Einige Entwickler haben den Wunsch ausgedrückt, einzelne Dienstkomponenten in die Anwendungsszenenhierarchie ein-/ausdingen zu können.</span><span class="sxs-lookup"><span data-stu-id="3f5fa-141">Some developers have expressed a desire to include individual service components into the application scene hierarchy.</span></span> <span data-ttu-id="3f5fa-142">Um diese Nutzung zu ermöglichen, müssen Dienste entweder in einer benutzerdefinierten Registrierungsstelle gekapselt werden oder sich selbst registrieren/selbst verwalten.</span><span class="sxs-lookup"><span data-stu-id="3f5fa-142">To enable this usage, services will either need to be encapsulated in a custom registrar or be self-registering / self-managing.</span></span>

<span data-ttu-id="3f5fa-143">Ein selbstregistrierungsdienst würde implementieren und sich selbst registrieren, damit der Anwendungscode die Dienstinstanz über [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) eine Registrierung entdecken kann.</span><span class="sxs-lookup"><span data-stu-id="3f5fa-143">A self-registering service would implement the [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) and register itself so that application code could discover the service instance via a registry.</span></span>

<span data-ttu-id="3f5fa-144">Ein Selbstverwaltungsdienst kann als Singletonobjekt in der Szenenhierarchie implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="3f5fa-144">A self-managing service could be implemented as a singleton object in the scene hierarchy.</span></span> <span data-ttu-id="3f5fa-145">Dieses Objekt stellt die Instanzeigenschaft und zur Verfügung, mit der Anwendungscode direkt auf die Dienstfunktionalität zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="3f5fa-145">This object would provide and instance property which application code could use to directly access service functionality.</span></span>

#### <a name="custom-service-locator"></a><span data-ttu-id="3f5fa-146">Benutzerdefinierter Dienstlocator</span><span class="sxs-lookup"><span data-stu-id="3f5fa-146">Custom service locator</span></span>

<span data-ttu-id="3f5fa-147">Einige Entwickler haben die Möglichkeit angefordert, eine benutzerdefinierte Dienstlocatorkomponente zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="3f5fa-147">Some developers have requested the ability to create a custom service locator component.</span></span> <span data-ttu-id="3f5fa-148">Benutzerdefinierte Dienstlocator implementieren die -Schnittstelle und verwalten den Lebenszyklus und das [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) Kernverhalten aktiver Dienste.</span><span class="sxs-lookup"><span data-stu-id="3f5fa-148">Custom service locators would implement the [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) interface and manage the life cycle and core behaviors of active services.</span></span>

#### <a name="hybrid-architecture"></a><span data-ttu-id="3f5fa-149">Hybridarchitektur</span><span class="sxs-lookup"><span data-stu-id="3f5fa-149">Hybrid architecture</span></span>

<span data-ttu-id="3f5fa-150">Das MRTK unterstützt eine Hybridarchitektur, in der Entwickler die vorherigen Ansätze nach Bedarf oder wunsch kombinieren können.</span><span class="sxs-lookup"><span data-stu-id="3f5fa-150">The MRTK will support a hybrid architecture in which developers can combine the previous approaches as needed or desired.</span></span> <span data-ttu-id="3f5fa-151">Beispielsweise könnte ein Entwickler mit dem [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) Dienstlocator beginnen und einen selbstregistrierungsbasierten Dienst hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="3f5fa-151">For example, a developer could start with the [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) service locator and add a self-registering service.</span></span>

> [!NOTE]
> <span data-ttu-id="3f5fa-152">Wenn Sie sich für eine Hybridarchitektur entscheiden, ist es wichtig, jede Duplizierung der Arbeit zu berücksichtigen (z. B. das Abrufen von Controllerdaten von mehreren Komponenten).</span><span class="sxs-lookup"><span data-stu-id="3f5fa-152">When opting for a hybrid architecture, it is important to be mindful of any duplication of work (ex: acquiring controller data from multiple components).</span></span>
