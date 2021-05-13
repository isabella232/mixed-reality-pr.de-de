---
title: Controller
description: Verwenden von Controllern in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Controller,
ms.openlocfilehash: c92ad099d770cc52467918053af02e7bebab928d
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2021
ms.locfileid: "109850336"
---
# <a name="controllers"></a><span data-ttu-id="b753c-104">Controller</span><span class="sxs-lookup"><span data-stu-id="b753c-104">Controllers</span></span>

<span data-ttu-id="b753c-105">Controller werden von den Eingabeanbietern [**automatisch erstellt und zerstört.**](input-providers.md)</span><span class="sxs-lookup"><span data-stu-id="b753c-105">Controllers are created and destroyed automatically by [**input providers**](input-providers.md).</span></span> <span data-ttu-id="b753c-106">Jeder Controllertyp verfügt  über eine Reihe von physischen Eingaben, die durch einen Achsentyp definiert sind und den Datentyp des Eingabewerts (Digital, Single Axis, Dual Axis, Six Dof, ...) und einen Eingabetyp (Schaltflächendruck, Trigger, Thumb Stick, Spatial Pointer, ...) zur Beschreibung des Ursprungs der Eingabe beschreiben. </span><span class="sxs-lookup"><span data-stu-id="b753c-106">Each controller type has a number of *physical inputs* defined by an *axis type*, telling us the data type of the input value (Digital, Single Axis, Dual Axis, Six Dof, ...), and an *input type* (Button Press, Trigger, Thumb Stick, Spatial Pointer, ...) describing the origin of the input.</span></span> <span data-ttu-id="b753c-107">Physische Eingaben werden  Eingabeaktionen über im **Controller-Eingabezuordnungsprofil** unter dem *Eingabesystemprofil* in der Mixed Reality Toolkit-Komponente zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="b753c-107">Physical inputs are mapped to *input actions* via in the **Controller Input Mapping Profile**, under the *Input System Profile* in the Mixed Reality Toolkit component.</span></span>

<span data-ttu-id="b753c-108">MRTK erkennt WMR-Controller automatisch und zeigt sie an, wenn das [**Paket Microsoft.MixedReality.Input**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) installiert ist.</span><span class="sxs-lookup"><span data-stu-id="b753c-108">MRTK will automatically detect WMR controllers and display them when the [**Microsoft.MixedReality.Input**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) package is installed.</span></span> <span data-ttu-id="b753c-109">Controllermodelle werden nur im Editor angezeigt, wenn die OpenXR-Pipeline verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="b753c-109">Controllers models will only show up in the editor when using the OpenXR pipeline.</span></span> <span data-ttu-id="b753c-110">Befolgen Sie zum Visualisieren von Oculus-Controllermodellen die [Bereitstellungsanweisungen für Oculus Quest.](/windows/mixed-reality/mrtk-unity/supported-devices/oculus-quest-mrtk.md)</span><span class="sxs-lookup"><span data-stu-id="b753c-110">To visualize Oculus controller models, follow the [Oculus Quest deployment instructions](/windows/mixed-reality/mrtk-unity/supported-devices/oculus-quest-mrtk.md)</span></span>

![Controllereingabezuordnung](../images/input/ControllerInputMapping.png)