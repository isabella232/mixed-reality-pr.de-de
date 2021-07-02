---
title: Tool zur Verwendung von Eingabefeatures
description: InputFeatureUsage-Dokumentationstool im MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 413d2a3105294411f9c08f4a2add9365389ea783
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176123"
---
# <a name="input-feature-usage-tool"></a><span data-ttu-id="3be7f-104">Tool zur Verwendung von Eingabefeatures</span><span class="sxs-lookup"><span data-stu-id="3be7f-104">Input feature usage tool</span></span>

<span data-ttu-id="3be7f-105">Das InputFeatureUsage-Tool ist ein Runtimetool (auf dem Gerät oder im Editor), mit dem Entwickler schnell die verfügbaren Unity InputFeatureUsages für eine erkannte Eingabequelle (z. B. Motion Controller oder Artikulierte Hand) bestimmen können.</span><span class="sxs-lookup"><span data-stu-id="3be7f-105">The InputFeatureUsage tool is a runtime (on device or in the editor) tool that enables developers to quickly determine the available Unity InputFeatureUsages for a detected input source (ex: motion controller or articulated hand).</span></span>

> [!NOTE]
> <span data-ttu-id="3be7f-106">Diese Szene funktioniert nur mit Unity 2019.3 oder höher.</span><span class="sxs-lookup"><span data-stu-id="3be7f-106">This scene only works on Unity 2019.3 or later.</span></span>

<span data-ttu-id="3be7f-107">Dieses Tool ist sehr nützlich, wenn Unterstützung für einen neuen Hardwarecontroller entwickelt wird.</span><span class="sxs-lookup"><span data-stu-id="3be7f-107">This tool is very useful when developing support for a new hardware controller.</span></span> <span data-ttu-id="3be7f-108">Es kann auch helfen, ein vermutetes Problem mit der Steuerelementzuordnung in der Supportklasse für einen vorhandenen Controller zu bestätigen.</span><span class="sxs-lookup"><span data-stu-id="3be7f-108">It can also help to confirm a suspected control mapping issue in the support class for an existing controller.</span></span>

![InputFeatureUsage-Tool](../images/controller-mapping-tool/InputFeatureUsages.png)

## <a name="using-the-inputfeatureusage-tool"></a><span data-ttu-id="3be7f-110">Verwenden des InputFeatureUsage-Tools</span><span class="sxs-lookup"><span data-stu-id="3be7f-110">Using the InputFeatureUsage tool</span></span>

<span data-ttu-id="3be7f-111">Navigieren Sie zum Einstieg mit dem InputFeatureUsage-Tool zu **MRTK/Tools/RuntimeTools/Tools/InputFeatureUsageTool,** und öffnen Sie die **InputFeatureUsageTool-Szene.**</span><span class="sxs-lookup"><span data-stu-id="3be7f-111">To get started with the InputFeatureUsage tool, navigate to **MRTK/Tools/RuntimeTools/Tools/InputFeatureUsageTool** and open the **InputFeatureUsageTool** scene.</span></span> <span data-ttu-id="3be7f-112">Nachdem die Szene geladen wurde, kann das Projekt entweder im Editor, im Wiedergabemodus oder auf einem Gerät erstellt und ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="3be7f-112">Once the scene has been loaded, the project can either be run in the editor, using play mode, or built and run on a device.</span></span>

<span data-ttu-id="3be7f-113">So untersuchen Sie die Zuordnungen von Unity für einen Controller:</span><span class="sxs-lookup"><span data-stu-id="3be7f-113">To examine Unity's mappings for a controller:</span></span>

- <span data-ttu-id="3be7f-114">Verbinden des Controllers</span><span class="sxs-lookup"><span data-stu-id="3be7f-114">Connect the controller</span></span>
- <span data-ttu-id="3be7f-115">Drücken Sie jede Schaltfläche, und verschieben Sie jede Achse.</span><span class="sxs-lookup"><span data-stu-id="3be7f-115">Press each button and move each axis</span></span>
- <span data-ttu-id="3be7f-116">Beachten Sie die Featureverwendungen in der Anzeige.</span><span class="sxs-lookup"><span data-stu-id="3be7f-116">Note the feature usages in the display</span></span>
- <span data-ttu-id="3be7f-117">Aktualisieren der Steuerelementzuordnungen im Eingabesystemdatenanbieter für den Controller</span><span class="sxs-lookup"><span data-stu-id="3be7f-117">Update the control mappings in the input system data provider for the controller</span></span>

> [!NOTE]
> <span data-ttu-id="3be7f-118">Das InputFeatureUsage-Tool verwendet keine Microsoft Mixed Reality Toolkit-Komponenten.</span><span class="sxs-lookup"><span data-stu-id="3be7f-118">The InputFeatureUsage tool does not make use of Microsoft Mixed Reality Toolkit components.</span></span> <span data-ttu-id="3be7f-119">Es kommuniziert direkt mit Unity, um die Funktionsverwendungen zu bestimmen und anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="3be7f-119">It directly communicates with Unity to determine and display the feature usages.</span></span>

### <a name="panels"></a><span data-ttu-id="3be7f-120">Panels</span><span class="sxs-lookup"><span data-stu-id="3be7f-120">Panels</span></span>

<span data-ttu-id="3be7f-121">In den Panels wird der aktuelle Status aller gemeldeten InputFeatureUsages für alle erkannten Unity-Eingabequellen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="3be7f-121">The panels display the current state of all reported InputFeatureUsages on all detected Unity input sources.</span></span>

<span data-ttu-id="3be7f-122">Im kleineren Bereich oben werden die Namen aller erkannten Quellen aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="3be7f-122">The smaller panel along the top lists the names of all detected sources.</span></span>

## <a name="see-also"></a><span data-ttu-id="3be7f-123">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="3be7f-123">See also</span></span>

- [<span data-ttu-id="3be7f-124">Erstellen eines Eingabesystemdatenanbieters</span><span class="sxs-lookup"><span data-stu-id="3be7f-124">Creating an input system data provider</span></span>](../input/create-data-provider.md)
- [<span data-ttu-id="3be7f-125">Controllerzuordnungstool</span><span class="sxs-lookup"><span data-stu-id="3be7f-125">Controller mapping tool</span></span>](controller-mapping-tool.md)
