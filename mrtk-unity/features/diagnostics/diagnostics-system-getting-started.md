---
title: Übersicht über das Diagnosesystem
description: Dokumentation zum Aktivieren und Deaktivieren der Diagnose in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 0de7b904a48453d6021cf7aed5835412c19b7884
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121778"
---
# <a name="diagnostic-system"></a><span data-ttu-id="f0591-104">Diagnosesystem</span><span class="sxs-lookup"><span data-stu-id="f0591-104">Diagnostic system</span></span>

<span data-ttu-id="f0591-105">Das Mixed Reality Toolkit-Diagnosesystem stellt Diagnosetools bereit, die in der Anwendung ausgeführt werden, um die Analyse von Anwendungsproblemen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="f0591-105">The Mixed Reality Toolkit Diagnostic System provides diagnostic tools that run within the application to enable analysis of application issues.</span></span>

<span data-ttu-id="f0591-106">Die erste Version des Diagnosesystems enthält [den Visual Profiler,](using-visual-profiler.md) der die Analyse von Leistungsproblemen während der Verwendung der Anwendung ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="f0591-106">The first release of the Diagnostic System contains the [Visual Profiler](using-visual-profiler.md) to allow for analyzing performance issues while using the application.</span></span>

## <a name="getting-started"></a><span data-ttu-id="f0591-107">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="f0591-107">Getting started</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f0591-108">Es wird **_dringend_** empfohlen, das Diagnosesystem während des gesamten Produktentwicklungszyklus zu aktivieren und als letzte Änderung vor dem Erstellen und Veröffentlichen der endgültigen Version zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="f0591-108">It is **_highly_** recommended that the Diagnostic System be enabled throughout the entire product development cycle and disabled as the last change prior to building and releasing the final version.</span></span>

<span data-ttu-id="f0591-109">Es gibt zwei wichtige Schritte, um mit der Verwendung des Diagnosesystems zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="f0591-109">There are two key steps to start using the Diagnostic System.</span></span>

1. <span data-ttu-id="f0591-110">[Aktivieren](#enable-diagnostics) des Diagnosesystems</span><span class="sxs-lookup"><span data-stu-id="f0591-110">[Enable](#enable-diagnostics) the Diagnostic System</span></span>
2. <span data-ttu-id="f0591-111">[Konfigurieren von](#configure-diagnostic-options) Diagnoseoptionen</span><span class="sxs-lookup"><span data-stu-id="f0591-111">[Configure](#configure-diagnostic-options) diagnostic options</span></span>

### <a name="enable-diagnostics"></a><span data-ttu-id="f0591-112">Aktivieren der Diagnosefunktion</span><span class="sxs-lookup"><span data-stu-id="f0591-112">Enable diagnostics</span></span>

<span data-ttu-id="f0591-113">Das Diagnosesystem wird vom MixedRealityToolkit-Objekt (oder einer anderen [Dienstregistrierungskomponente)](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) verwaltet.</span><span class="sxs-lookup"><span data-stu-id="f0591-113">The diagnostics system is managed by the MixedRealityToolkit object (or another [service registrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) component).</span></span>

<span data-ttu-id="f0591-114">Die folgenden Schritte setzen die Verwendung des MixedRealityToolkit-Objekts voraus.</span><span class="sxs-lookup"><span data-stu-id="f0591-114">The following steps presume use of the MixedRealityToolkit object.</span></span> <span data-ttu-id="f0591-115">Die für andere Dienstregistrierungen erforderlichen Schritte können unterschiedlich sein.</span><span class="sxs-lookup"><span data-stu-id="f0591-115">Steps required for other service registrars may be different.</span></span>

1. <span data-ttu-id="f0591-116">Wählen Sie das MixedRealityToolkit-Objekt in der Szenenhierarchie aus.</span><span class="sxs-lookup"><span data-stu-id="f0591-116">Select the MixedRealityToolkit object in the scene hierarchy.</span></span>

    ![MRTK– Konfigurierte Szenenhierarchie](../images/MRTK_ConfiguredHierarchy.png)

1. <span data-ttu-id="f0591-118">Navigieren Sie im Inspektorbereich zum Abschnitt Diagnosesystem, und aktivieren Sie Aktivieren.</span><span class="sxs-lookup"><span data-stu-id="f0591-118">Navigate the Inspector panel to the Diagnostics System section and check Enable</span></span>
1. <span data-ttu-id="f0591-119">Auswählen der Diagnosesystemimplementierung</span><span class="sxs-lookup"><span data-stu-id="f0591-119">Select the Diagnostics System implementation</span></span>

    ![Auswählen der Diagnosesystemimplementierung](../images/diagnostics/DiagnosticsSelectSystemType.png)

> [!NOTE]
> <span data-ttu-id="f0591-121">Für Benutzer des Standardprofils (Assets/MRTK/SDK/Profiles) ist das Diagnosesystem für die Verwendung des Objekts `DefaultMixedRealityToolkitConfigurationProfile` [`MixedRealityDiagnosticsSystem`](xref:Microsoft.MixedReality.Toolkit.Diagnostics.MixedRealityDiagnosticsSystem) vorkonfiguriert.</span><span class="sxs-lookup"><span data-stu-id="f0591-121">Users of the default profile, `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles), will have the diagnostics system pre-configured to use the [`MixedRealityDiagnosticsSystem`](xref:Microsoft.MixedReality.Toolkit.Diagnostics.MixedRealityDiagnosticsSystem) object.</span></span>

### <a name="configure-diagnostic-options"></a><span data-ttu-id="f0591-122">Konfigurieren von Diagnoseoptionen</span><span class="sxs-lookup"><span data-stu-id="f0591-122">Configure diagnostic options</span></span>

<span data-ttu-id="f0591-123">Das Diagnosesystem verwendet ein Konfigurationsprofil, um anzugeben, welche Komponenten angezeigt werden sollen, und um deren Einstellungen zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="f0591-123">The diagnostics system uses a configuration profile to specify which components are to be displayed and to configure their settings.</span></span> <span data-ttu-id="f0591-124">Weitere Informationen [zu den verfügbaren Komponenteneinstellungen](configuring-diagnostics.md) finden Sie unter Konfigurieren des Diagnosesystems.</span><span class="sxs-lookup"><span data-stu-id="f0591-124">Please see [Configuring the Diagnostics System](configuring-diagnostics.md) for more information pertaining to the available component settings.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f0591-125">Während es möglich ist, den Unity-Wiedergabemodus bei der Entwicklung von Anwendungen zu verwenden, ohne dass die Schritte zum Erstellen und Bereitstellen erforderlich sind, ist es wichtig, die Diagnosesystemergebnisse mithilfe einer kompilierten Anwendung zu bewerten, die auf der Zielhardware und -plattform ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="f0591-125">While it is possible to use Unity's Play Mode while developing applications without requiring the build and deploy steps, it is important to evaluate the diagnostics system results using a compiled application running on the target hardware and platform.</span></span>
>
> <span data-ttu-id="f0591-126">Die Leistungsdiagnose, z. B. [Visual Profiler,](using-visual-profiler.md)spiegelt die tatsächliche Anwendungsleistung möglicherweise nicht genau wider, wenn sie im Editor ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="f0591-126">Performance diagnostics, such as the [Visual Profiler](using-visual-profiler.md), may not accurately reflect actual application performance when run from within the editor.</span></span>

## <a name="see-also"></a><span data-ttu-id="f0591-127">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f0591-127">See also</span></span>

- [<span data-ttu-id="f0591-128">Diagnose-API-Dokumentation</span><span class="sxs-lookup"><span data-stu-id="f0591-128">Diagnostics API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Diagnostics)
- [<span data-ttu-id="f0591-129">Konfigurieren des Diagnosesystems</span><span class="sxs-lookup"><span data-stu-id="f0591-129">Configuring the Diagnostics System</span></span>](configuring-diagnostics.md)
- [<span data-ttu-id="f0591-130">Verwenden von Visual Profiler</span><span class="sxs-lookup"><span data-stu-id="f0591-130">Using the Visual Profiler</span></span>](using-visual-profiler.md)
