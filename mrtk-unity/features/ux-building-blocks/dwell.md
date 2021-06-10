---
title: Wohnen
description: Interaktion zwischen Verweilen
author: cre8ivepark
ms.author: dongpark
ms.date: 05/20/2021
keywords: Dwell, Unity, HoloLens, HoloLens 2, Mixed Reality, development, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 18e69f001c8989234d1b75fb713796f079cacbdf
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647799"
---
# <a name="dwell"></a><span data-ttu-id="b3fb0-104">Wohnen</span><span class="sxs-lookup"><span data-stu-id="b3fb0-104">Dwell</span></span>

![Verweilreiher (Hero)](../images/dwell/MRTK_UX_Dwell.png)

<span data-ttu-id="b3fb0-106">Das Anvieren und Verweilen mit dem Kopf ist gut in Szenarien, in denen die Hände einer Person mit anderen Aufgaben beschäftigt sind.</span><span class="sxs-lookup"><span data-stu-id="b3fb0-106">Head-gaze and dwell are great in scenarios where a person's hands are busy with other tasks.</span></span> <span data-ttu-id="b3fb0-107">Das Feature ist auch nützlich, wenn die Stimme aufgrund von Umgebungs- oder sozialen Einschränkungen nicht zu 100 % zuverlässig oder verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="b3fb0-107">The feature is also useful when voice isn't 100% reliable or available because of environmental or social constraints.</span></span>
<span data-ttu-id="b3fb0-108">MrTK-Verweilbeispiele veranschaulichen verschiedene Arten von Benutzeroberflächenkomponenten mit konfigurierbarer Antwortzeit und visuellem Feedback.</span><span class="sxs-lookup"><span data-stu-id="b3fb0-108">MRTK's dwell examples demonstrate different types of UI components with configurable response time and visual feedback.</span></span>

<span data-ttu-id="b3fb0-109">Die [Entwurfsempfehlungen finden Sie](/windows/mixed-reality/design/gaze-and-dwell-head) auf der Seite Mit dem Kopf anving und verweilen.</span><span class="sxs-lookup"><span data-stu-id="b3fb0-109">Please see [Head-gaze and dwell guideline](/windows/mixed-reality/design/gaze-and-dwell-head) page for the design recommendations.</span></span>

## <a name="dwell-scripts"></a><span data-ttu-id="b3fb0-110">Verweilskripts</span><span class="sxs-lookup"><span data-stu-id="b3fb0-110">Dwell scripts</span></span>

- <span data-ttu-id="b3fb0-111">**DwellHandler:** Fügt dem Benutzeroberflächenziel eine Verweilmodalität hinzu.</span><span class="sxs-lookup"><span data-stu-id="b3fb0-111">**DwellHandler**: Adds a dwell modality to the UI target.</span></span>
- <span data-ttu-id="b3fb0-112">**DwellStateType:** Die Zustände des Verweilhandlers.</span><span class="sxs-lookup"><span data-stu-id="b3fb0-112">**DwellStateType**: The states of the dwell handler.</span></span>
- <span data-ttu-id="b3fb0-113">**DwellUnityEvent:** Unity-Ereignis für ein Verweilereignis.</span><span class="sxs-lookup"><span data-stu-id="b3fb0-113">**DwellUnityEvent**: Unity event for a dwell event.</span></span> <span data-ttu-id="b3fb0-114">Enthält den Zeigerverweis.</span><span class="sxs-lookup"><span data-stu-id="b3fb0-114">Contains the pointer reference.</span></span>
- <span data-ttu-id="b3fb0-115">**BaseDwellPressableButton.cs:** Ein Skript, das das OnClick()-Ereignis in der `Interactable` PressableButtonHoloLens2-Prefabs auslöst.</span><span class="sxs-lookup"><span data-stu-id="b3fb0-115">**BaseDwellPressableButton.cs** : A script that triggers OnClick() event in `Interactable` of PressableButtonHoloLens2 prefabs.</span></span>
- <span data-ttu-id="b3fb0-116">**ToggleDwellPressableButton.cs:** Dieses Skript ändert die -Eigenschaft von , `_BorderWidth` `dwellVisualImage` die den MRTK-Standard-Shader verwendet.</span><span class="sxs-lookup"><span data-stu-id="b3fb0-116">**ToggleDwellPressableButton.cs** : This script modifies `_BorderWidth` property of the `dwellVisualImage` which is using MRTK Standard Shader.</span></span>

## <a name="dwell-profiles"></a><span data-ttu-id="b3fb0-117">Verweilprofile</span><span class="sxs-lookup"><span data-stu-id="b3fb0-117">Dwell profiles</span></span>
<span data-ttu-id="b3fb0-118">Verweilprofile werden vom **Verweilhandler verwendet,** um die verschiedenen Schwellenwerte zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="b3fb0-118">Dwell profiles are used by the **Dwell Handler** to configure the various thresholds.</span></span>
- <span data-ttu-id="b3fb0-119">**ButtonDwellProfile.asset**</span><span class="sxs-lookup"><span data-stu-id="b3fb0-119">**ButtonDwellProfile.asset**</span></span>
- <span data-ttu-id="b3fb0-120">**InstandDwellProfile.asset**</span><span class="sxs-lookup"><span data-stu-id="b3fb0-120">**InstandDwellProfile.asset**</span></span>
- <span data-ttu-id="b3fb0-121">**DwellProfileWithDecay.asset**</span><span class="sxs-lookup"><span data-stu-id="b3fb0-121">**DwellProfileWithDecay.asset**</span></span>

## <a name="prefabs"></a><span data-ttu-id="b3fb0-122">Prefabs</span><span class="sxs-lookup"><span data-stu-id="b3fb0-122">Prefabs</span></span>

<span data-ttu-id="b3fb0-123">Bei diesen Prefabs handelt es sich um Varianten der HoloLens 2- und Drucktasten-Prefabs, die zusätzliche Komponenten zur Unterstützung von Verweilinteraktionen enthalten.</span><span class="sxs-lookup"><span data-stu-id="b3fb0-123">These prefabs are variants of the HoloLens 2 style pressable button prefabs that have additional components to support dwell interactions.</span></span>

- <span data-ttu-id="b3fb0-124">**PressableButtonHoloLens2_Dwell.prefab**</span><span class="sxs-lookup"><span data-stu-id="b3fb0-124">**PressableButtonHoloLens2_Dwell.prefab**</span></span>
- <span data-ttu-id="b3fb0-125">**PressableButtonHoloLens2_32x96_Dwell.prefab**</span><span class="sxs-lookup"><span data-stu-id="b3fb0-125">**PressableButtonHoloLens2_32x96_Dwell.prefab**</span></span>
- <span data-ttu-id="b3fb0-126">**PressableButtonHoloLens2ToggleDwell.prefab**</span><span class="sxs-lookup"><span data-stu-id="b3fb0-126">**PressableButtonHoloLens2ToggleDwell.prefab**</span></span>
- <span data-ttu-id="b3fb0-127">**PressableButtonHoloLens2Toggle_32x96_Dwell.prefab**</span><span class="sxs-lookup"><span data-stu-id="b3fb0-127">**PressableButtonHoloLens2Toggle_32x96_Dwell.prefab**</span></span>

<span data-ttu-id="b3fb0-128">Diese Prefabs verfügen über eine zusätzliche Backplate-Komponente **QuadDwellVisual,** um den Eingabezustand des Verweilzustands zu visualisieren.</span><span class="sxs-lookup"><span data-stu-id="b3fb0-128">These prefabs have an additional backplate component **QuadDwellVisual** to visualize the dwell input state.</span></span> <span data-ttu-id="b3fb0-129">Ihm ist **HolographicBackPlateDwellVisual.mat-Material** zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="b3fb0-129">It has **HolographicBackPlateDwellVisual.mat** material assigned.</span></span> <span data-ttu-id="b3fb0-130">**ToggleDwellPressableButton.cs** aktualisiert  die _BorderWidth-Eigenschaft des MRTK Standard-Shaders, um die Verweileingabe zu visualisieren.</span><span class="sxs-lookup"><span data-stu-id="b3fb0-130">**ToggleDwellPressableButton.cs** updates the **_BorderWidth** property of MRTK Standard shader to visualize the dwell input.</span></span>

<img src="../images/dwell/MRTK_UX_Dwell_Prefabs_Structure.png" alt="Dwell prefabs structure" width="550px">
<img src="../images/dwell/MRTK_UX_Dwell_Prefabs.png" alt="Dwell prefabs" width="350px">

## <a name="example-scene"></a><span data-ttu-id="b3fb0-131">Beispielszene</span><span class="sxs-lookup"><span data-stu-id="b3fb0-131">Example scene</span></span>

<span data-ttu-id="b3fb0-132">Beispiele finden Sie in der `DwellExample` Szene.</span><span class="sxs-lookup"><span data-stu-id="b3fb0-132">You can find examples in the `DwellExample` scene.</span></span> <span data-ttu-id="b3fb0-133">Die Beispielszene zeigt Beispiele für volumetrischen Ui und Unity-Benutzeroberflächenbeispiele.</span><span class="sxs-lookup"><span data-stu-id="b3fb0-133">The example scene shows both volumetric UI examples and Unity UI examples.</span></span>

<img src="../images/dwell/MRTK_UX_Dwell_Examples.png" alt="Near Menu Example">

## <a name="see-also"></a><span data-ttu-id="b3fb0-134">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b3fb0-134">See also</span></span>

- [<span data-ttu-id="b3fb0-135">**Schaltflächen**</span><span class="sxs-lookup"><span data-stu-id="b3fb0-135">**Buttons**</span></span>](button.md)
- [<span data-ttu-id="b3fb0-136">**Interaktionsfähig**</span><span class="sxs-lookup"><span data-stu-id="b3fb0-136">**Interactable**</span></span>](interactable.md)
