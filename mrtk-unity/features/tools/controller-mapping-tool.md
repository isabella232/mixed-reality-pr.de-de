---
title: Controllerzuordnungstool
description: Dokumentation zum Controllerzuordnungstool in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 8c1da7ae6a46bd00599a77b1c4cbb0b2f7baa632
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176170"
---
# <a name="controller-mapping-tool"></a><span data-ttu-id="a91dc-104">Controllerzuordnungstool</span><span class="sxs-lookup"><span data-stu-id="a91dc-104">Controller mapping tool</span></span>

<span data-ttu-id="a91dc-105">Das Controllerzuordnungstool ist ein Laufzeittool (auf dem Gerät oder im Editor), mit dem Entwickler schnell die Unity-Eingabeachse und Schaltflächenzuordnungen für einen Hardwarecontroller (z. B. Motion Controller) bestimmen können.</span><span class="sxs-lookup"><span data-stu-id="a91dc-105">The controller mapping tool is a runtime (on device or in the editor) tool that enables developers to quickly determine the Unity input axis and button mappings for a hardware controller (ex: motion controller).</span></span>

<span data-ttu-id="a91dc-106">Dieses Tool ist sehr nützlich, wenn Sie Unterstützung für einen neuen Hardwarecontroller entwickeln.</span><span class="sxs-lookup"><span data-stu-id="a91dc-106">This tool is very useful when developing support for a new hardware controller.</span></span> <span data-ttu-id="a91dc-107">Es kann auch helfen, ein vermutetes Problem bei der Zuordnung von Steuerelementen in der Supportklasse für einen vorhandenen Controller zu bestätigen.</span><span class="sxs-lookup"><span data-stu-id="a91dc-107">It can also help to confirm a suspected control mapping issue in the support class for an existing controller.</span></span>

![Controllerzuordnungstool](../images/controller-mapping-tool/ControllerMappingTool.png)

## <a name="using-the-controller-mapping-tool"></a><span data-ttu-id="a91dc-109">Verwenden des Controllerzuordnungstools</span><span class="sxs-lookup"><span data-stu-id="a91dc-109">Using the controller mapping tool</span></span>

<span data-ttu-id="a91dc-110">Um mit dem Controllerzuordnungstool zu beginnen, navigieren Sie zu **MRTK/Tools/RuntimeTools/Tools/ControllerMappingTool,** und öffnen Sie die **ControllerMappingTool-Szene.**</span><span class="sxs-lookup"><span data-stu-id="a91dc-110">To get started with the controller mapping tool, navigate to **MRTK/Tools/RuntimeTools/Tools/ControllerMappingTool** and open the **ControllerMappingTool** scene.</span></span> <span data-ttu-id="a91dc-111">Nachdem die Szene geladen wurde, kann das Projekt entweder im Editor, im Wiedergabemodus oder auf einem Gerät erstellt und ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="a91dc-111">Once the scene has been loaded, the project can either be run in the editor, using play mode, or built and run on a device.</span></span>

<span data-ttu-id="a91dc-112">So untersuchen Sie die Zuordnungen von Unity für einen Controller:</span><span class="sxs-lookup"><span data-stu-id="a91dc-112">To examine Unity's mappings for a controller:</span></span>

- <span data-ttu-id="a91dc-113">Verbinden des Controllers</span><span class="sxs-lookup"><span data-stu-id="a91dc-113">Connect the controller</span></span>
- <span data-ttu-id="a91dc-114">Drücken Sie die einzelnen Schaltflächen, und verschieben Sie jede Achse.</span><span class="sxs-lookup"><span data-stu-id="a91dc-114">Press each button and move each axis</span></span>
- <span data-ttu-id="a91dc-115">Beachten Sie die Zuordnungen in der Anzeige.</span><span class="sxs-lookup"><span data-stu-id="a91dc-115">Note the mappings in the display</span></span>
- <span data-ttu-id="a91dc-116">Aktualisieren der Steuerelementzuordnungen im Eingabesystemdatenanbieter für den Controller</span><span class="sxs-lookup"><span data-stu-id="a91dc-116">Update the control mappings in the input system data provider for the controller</span></span>

> [!NOTE]
> <span data-ttu-id="a91dc-117">Das Controllerzuordnungstool nutzt keine Microsoft Mixed Reality Toolkit-Komponenten.</span><span class="sxs-lookup"><span data-stu-id="a91dc-117">The controller mapping tool does not make use of Microsoft Mixed Reality Toolkit components.</span></span> <span data-ttu-id="a91dc-118">Es kommuniziert direkt mit Unity, um die Steuerelementzuordnungen zu bestimmen und anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a91dc-118">It directly communicates with Unity to determine and display the control mappings.</span></span>

### <a name="all-controls-display"></a><span data-ttu-id="a91dc-119">Anzeige aller Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="a91dc-119">All controls display</span></span>

<span data-ttu-id="a91dc-120">Der große Anzeigebereich meldet den Status aller definierten Unity-Eingabeachsen und -Schaltflächen (z. B. Achse 10, Schaltfläche 3).</span><span class="sxs-lookup"><span data-stu-id="a91dc-120">The large display panel reports the state of all defined Unity input axes and buttons (ex: Axis 10, Button 3).</span></span> <span data-ttu-id="a91dc-121">Dieser Bereich bietet eine vollständige Ansicht des Zustands des Controllers.</span><span class="sxs-lookup"><span data-stu-id="a91dc-121">This panel provides a complete view of the state of the controller.</span></span>

![Anzeige aller Steuerelemente](../images/controller-mapping-tool/AllControls.png)

### <a name="active-controls-display"></a><span data-ttu-id="a91dc-123">Anzeigen von aktiven Steuerelementen</span><span class="sxs-lookup"><span data-stu-id="a91dc-123">Active controls display</span></span>

<span data-ttu-id="a91dc-124">Der kleinere, schmale Anzeigebereich zeigt die Unity-Eingabe als Axt und Schaltflächen an, die sich im aktiven Zustand befinden (z. B. eine Schaltfläche wird gedrückt).</span><span class="sxs-lookup"><span data-stu-id="a91dc-124">The smaller, narrow display panel shows the Unity input axed and buttons which are in an active state (ex: a button is pressed).</span></span> <span data-ttu-id="a91dc-125">Die Anzeige der aktiven Steuerelemente bietet eine leicht lesbare Zusammenfassungsansicht des Zustands des Controllers.</span><span class="sxs-lookup"><span data-stu-id="a91dc-125">The active controls display provides an easy to read summary view of the state of the controller.</span></span>

![Anzeigen von aktiven Steuerelementen](../images/controller-mapping-tool/ActiveControls.png)

## <a name="see-also"></a><span data-ttu-id="a91dc-127">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="a91dc-127">See also</span></span>

- [<span data-ttu-id="a91dc-128">Erstellen eines Eingabesystemdatenanbieters</span><span class="sxs-lookup"><span data-stu-id="a91dc-128">Creating an input system data provider</span></span>](../input/create-data-provider.md)
- [<span data-ttu-id="a91dc-129">InputFeatureUsage-Tool</span><span class="sxs-lookup"><span data-stu-id="a91dc-129">InputFeatureUsage tool</span></span>](input-feature-usage-tool.md)
