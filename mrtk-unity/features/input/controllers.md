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
# <a name="controllers"></a>Controller

Controller werden von den Eingabeanbietern [**automatisch erstellt und zerstört.**](input-providers.md) Jeder Controllertyp verfügt  über eine Reihe von physischen Eingaben, die durch einen Achsentyp definiert sind und den Datentyp des Eingabewerts (Digital, Single Axis, Dual Axis, Six Dof, ...) und einen Eingabetyp (Schaltflächendruck, Trigger, Thumb Stick, Spatial Pointer, ...) zur Beschreibung des Ursprungs der Eingabe beschreiben.  Physische Eingaben werden  Eingabeaktionen über im **Controller-Eingabezuordnungsprofil** unter dem *Eingabesystemprofil* in der Mixed Reality Toolkit-Komponente zugeordnet.

![Controllereingabezuordnung](../images/input/ControllerInputMapping.png)
