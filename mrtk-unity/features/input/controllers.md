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
# <a name="controllers"></a>Controller

Controller werden von den Eingabeanbietern [**automatisch erstellt und zerstört.**](input-providers.md) Jeder Controllertyp verfügt  über eine Reihe von physischen Eingaben, die durch einen Achsentyp definiert sind und den Datentyp des Eingabewerts (Digital, Single Axis, Dual Axis, Six Dof, ...) und einen Eingabetyp (Schaltflächendruck, Trigger, Thumb Stick, Spatial Pointer, ...) zur Beschreibung des Ursprungs der Eingabe beschreiben.  Physische Eingaben werden  Eingabeaktionen über im **Controller-Eingabezuordnungsprofil** unter dem *Eingabesystemprofil* in der Mixed Reality Toolkit-Komponente zugeordnet.

MRTK erkennt WMR-Controller automatisch und zeigt sie an, wenn das [**Paket Microsoft.MixedReality.Input**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) installiert ist. Controllermodelle werden nur im Editor angezeigt, wenn die OpenXR-Pipeline verwendet wird. Befolgen Sie zum Visualisieren von Oculus-Controllermodellen die [Bereitstellungsanweisungen für Oculus Quest.](/windows/mixed-reality/mrtk-unity/supported-devices/oculus-quest-mrtk.md)

![Controllereingabezuordnung](../images/input/ControllerInputMapping.png)