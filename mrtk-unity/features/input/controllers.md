---
title: Controller
description: Verwenden von Controllern in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Controller,
ms.openlocfilehash: ea3dbd11baa669750f3bccc09d6cd7ab3eb7688f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176918"
---
# <a name="controllers"></a><span data-ttu-id="15805-104">Controller</span><span class="sxs-lookup"><span data-stu-id="15805-104">Controllers</span></span>

<span data-ttu-id="15805-105">Controller werden von den Eingabeanbietern [**automatisch erstellt und zerstört.**](input-providers.md)</span><span class="sxs-lookup"><span data-stu-id="15805-105">Controllers are created and destroyed automatically by [**input providers**](input-providers.md).</span></span> <span data-ttu-id="15805-106">Jeder Controllertyp verfügt  über eine Reihe von physischen Eingaben, die durch einen Achsentyp definiert sind und den Datentyp des Eingabewerts (Digital, Single Axis, Dual Axis, Six Dof, ...) und einen Eingabetyp (Schaltflächendruck, Trigger, Thumb Stick, Spatial Pointer, ...) zur Beschreibung des Ursprungs der Eingabe beschreiben. </span><span class="sxs-lookup"><span data-stu-id="15805-106">Each controller type has a number of *physical inputs* defined by an *axis type*, telling us the data type of the input value (Digital, Single Axis, Dual Axis, Six Dof, ...), and an *input type* (Button Press, Trigger, Thumb Stick, Spatial Pointer, ...) describing the origin of the input.</span></span> <span data-ttu-id="15805-107">Physische Eingaben werden  Eingabeaktionen über im **Controller-Eingabezuordnungsprofil** unter dem *Eingabesystemprofil* in der Mixed Reality Toolkit-Komponente zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="15805-107">Physical inputs are mapped to *input actions* via in the **Controller Input Mapping Profile**, under the *Input System Profile* in the Mixed Reality Toolkit component.</span></span>

![Controllereingabezuordnung](../images/input/ControllerInputMapping.png)
