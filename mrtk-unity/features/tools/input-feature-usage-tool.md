---
title: Inputfeatureusagetool
description: Dokumentation zum inputfeatureusage-Tool in mrtk
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 35b28557df37abee19a0c950b362117eb6a120b0
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300199"
---
# <a name="inputfeatureusage-tool"></a><span data-ttu-id="07a4f-104">Inputfeatureusage-Tool</span><span class="sxs-lookup"><span data-stu-id="07a4f-104">InputFeatureUsage tool</span></span>

<span data-ttu-id="07a4f-105">Das inputfeatureusage-Tool ist ein Lauf Zeit Tool (auf dem Gerät oder im Editor), mit dem Entwickler die verfügbaren Unity-inputfeatureverwendungen für eine erkannte Eingabe Quelle (z. h. Motion Controller oder Handgelenk) schnell ermitteln können.</span><span class="sxs-lookup"><span data-stu-id="07a4f-105">The InputFeatureUsage tool is a runtime (on device or in the editor) tool that enables developers to quickly determine the available Unity InputFeatureUsages for a detected input source (ex: motion controller or articulated hand).</span></span>

> [!NOTE]
> <span data-ttu-id="07a4f-106">Diese Szene funktioniert nur in Unity 2019,3 oder höher.</span><span class="sxs-lookup"><span data-stu-id="07a4f-106">This scene only works on Unity 2019.3 or later.</span></span>

<span data-ttu-id="07a4f-107">Dieses Tool ist sehr nützlich, wenn Sie die Unterstützung für einen neuen Hardware Controller entwickeln.</span><span class="sxs-lookup"><span data-stu-id="07a4f-107">This tool is very useful when developing support for a new hardware controller.</span></span> <span data-ttu-id="07a4f-108">Außerdem kann es hilfreich sein, ein verdächtiges steuerungsmappenproblem in der Unterstützungs Klasse für einen vorhandenen Controller zu bestätigen.</span><span class="sxs-lookup"><span data-stu-id="07a4f-108">It can also help to confirm a suspected control mapping issue in the support class for an existing controller.</span></span>

![Inputfeatureusage-Tool](../images/controller-mapping-tool/InputFeatureUsages.png)

## <a name="using-the-inputfeatureusage-tool"></a><span data-ttu-id="07a4f-110">Verwenden des inputfeatureusage-Tools</span><span class="sxs-lookup"><span data-stu-id="07a4f-110">Using the InputFeatureUsage tool</span></span>

<span data-ttu-id="07a4f-111">Um mit dem inputfeatureusage-Tool zu beginnen, navigieren Sie zu **mrtk/Tools/runtimetools/Tools/inputfeatureusagetool** , und öffnen Sie die **inputfeatureusagetool** -Szene.</span><span class="sxs-lookup"><span data-stu-id="07a4f-111">To get started with the InputFeatureUsage tool, navigate to **MRTK/Tools/RuntimeTools/Tools/InputFeatureUsageTool** and open the **InputFeatureUsageTool** scene.</span></span> <span data-ttu-id="07a4f-112">Nachdem die Szene geladen wurde, kann das Projekt entweder im Editor, über den Wiedergabemodus oder auf einem Gerät erstellt und ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="07a4f-112">Once the scene has been loaded, the project can either be run in the editor, using play mode, or built and run on a device.</span></span>

<span data-ttu-id="07a4f-113">So untersuchen Sie die Zuordnungen von Unity für einen Controller:</span><span class="sxs-lookup"><span data-stu-id="07a4f-113">To examine Unity's mappings for a controller:</span></span>

- <span data-ttu-id="07a4f-114">Verbinden des Controllers</span><span class="sxs-lookup"><span data-stu-id="07a4f-114">Connect the controller</span></span>
- <span data-ttu-id="07a4f-115">Drücken Sie jede Schaltfläche, und verschieben Sie jede Achse.</span><span class="sxs-lookup"><span data-stu-id="07a4f-115">Press each button and move each axis</span></span>
- <span data-ttu-id="07a4f-116">Beachten Sie die Funktions Verwendungen in der Anzeige.</span><span class="sxs-lookup"><span data-stu-id="07a4f-116">Note the feature usages in the display</span></span>
- <span data-ttu-id="07a4f-117">Aktualisieren der Steuerelement Zuordnungen im Eingabe Systemdaten Anbieter für den Controller</span><span class="sxs-lookup"><span data-stu-id="07a4f-117">Update the control mappings in the input system data provider for the controller</span></span>

> [!NOTE]
> <span data-ttu-id="07a4f-118">Das inputfeatureusage-Tool nutzt nicht die Microsoft Mixed Reality Toolkit-Komponenten.</span><span class="sxs-lookup"><span data-stu-id="07a4f-118">The InputFeatureUsage tool does not make use of Microsoft Mixed Reality Toolkit components.</span></span> <span data-ttu-id="07a4f-119">Er kommuniziert direkt mit Unity, um die Funktions Verwendungen zu bestimmen und anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="07a4f-119">It directly communicates with Unity to determine and display the feature usages.</span></span>

### <a name="panels"></a><span data-ttu-id="07a4f-120">Panels</span><span class="sxs-lookup"><span data-stu-id="07a4f-120">Panels</span></span>

<span data-ttu-id="07a4f-121">Die Bereiche zeigen den aktuellen Status aller gemeldeten inputfeatureusages für alle erkannten Unity-Eingabe Quellen an.</span><span class="sxs-lookup"><span data-stu-id="07a4f-121">The panels display the current state of all reported InputFeatureUsages on all detected Unity input sources.</span></span>

<span data-ttu-id="07a4f-122">Der kleinere Bereich am oberen Rand listet die Namen aller erkannten Quellen auf.</span><span class="sxs-lookup"><span data-stu-id="07a4f-122">The smaller panel along the top lists the names of all detected sources.</span></span>

## <a name="see-also"></a><span data-ttu-id="07a4f-123">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="07a4f-123">See also</span></span>

- [<span data-ttu-id="07a4f-124">Erstellen eines Eingabe System-Datenanbieters</span><span class="sxs-lookup"><span data-stu-id="07a4f-124">Creating an input system data provider</span></span>](../input/create-data-provider.md)
- [<span data-ttu-id="07a4f-125">Controller-Mapping-Tool</span><span class="sxs-lookup"><span data-stu-id="07a4f-125">Controller mapping tool</span></span>](controller-mapping-tool.md)
