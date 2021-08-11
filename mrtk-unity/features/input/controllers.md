---
title: Controller
description: Verwenden von Controllern im MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Controller,
ms.openlocfilehash: bc6aea1abda85567ab1b0db2616b529a92b4165e9b9cbcbc4b8b3cecd8a34c9f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224759"
---
# <a name="controllers"></a>Controller

Controller werden von den Eingabeanbietern [**automatisch erstellt und zerstört.**](input-providers.md) Jeder Controllertyp verfügt  über eine Reihe von physischen Eingaben, die durch einen Achsentyp definiert sind und den Datentyp des Eingabewerts (Digital, Single Axis, Dual Axis, Six Dof, ...) und einen Eingabetyp (Schaltflächendruck, Trigger, Thumb Stick, Spatial Pointer, ...) zur Beschreibung des Ursprungs der Eingabe beschreiben.  Physische Eingaben werden  Eingabeaktionen über im **Controller-Eingabezuordnungsprofil** unter dem *Eingabesystemprofil* in der Mixed Reality Toolkit-Komponente zugeordnet.

![Controllereingabezuordnung](../images/input/ControllerInputMapping.png)
