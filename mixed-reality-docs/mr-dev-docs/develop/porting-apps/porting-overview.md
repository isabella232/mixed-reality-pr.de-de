---
title: Übersicht zum Portieren
description: Eine Übersicht über die verschiedenen Portierungsoptionen zum Bringen Ihrer vorhandenen Anwendungen in Mixed Reality für HoloLens und VR.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: Portieren, Unity, Middleware, Engine, UWP, Win32
ms.openlocfilehash: 167559d69cc4e65f971a8970b56e41e6e3ca8b22
ms.sourcegitcommit: 12ea3fb2df4664c5efd07dcbb9040c2ff173afb6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2021
ms.locfileid: "113042271"
---
# <a name="porting-overview"></a>Übersicht zum Portieren

Wenn es um das Portieren oder Aktualisieren Ihrer vorhandenen Projekte für Mixed Reality geht, hängt Ihre Portierungs journey davon ab, ob Ihre App mit Unity oder Unreal Engine erstellt wurde und HoloLens (1. Generation) oder HoloLens 2 oder SteamVR als Ziel hat. Diese Übersichtsseite enthält unsere aktuellen Empfehlungen für jede Plattform und jedes Gerät. Achten Sie darauf, sich zu vergewissern, dass sich diese Prozesse immer ändern.

Richten Sie zunächst Ihr Projektziel basierend auf unseren [Unity-](#unity) und [Unreal-Empfehlungen](#unreal) ein, und folgen Sie dann mindestens einem unserer Portierungsszenarien:

- [HoloLens (1. Generation) zum HoloLens 2](#hololens-1st-gen-unity-apps-to-hololens-2)
- [Immersive Headsets (VR)](#immersive-vr-headsets)
- [2D-UWP-Apps](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a>Empfohlene Projektziele

Es ist wichtig, ihre Projekte auf dem neuesten Stand zu halten, unabhängig davon, ob Sie eine App auf ein anderes Zielgerät portieren. Unsere aktuellen Empfehlungen finden Sie in den unten aufgeführten enginebasierten Ressourcen.

### <a name="unity"></a>Unity

Aktuelle Anleitungen zu den empfohlenen Unity- und MRTK-Versionen finden Sie auf der Seite [Auswählen einer Unity-Version.](../unity/choosing-unity-version.md)

### <a name="unreal"></a>Unreal

Aktuelle Anleitungen zu den empfohlenen Unreal- und MRTK-Versionen finden Sie auf der Seite [Einrichten Ihres Unreal-Projekts.](../unreal/unreal-project-setup.md)

## <a name="porting-scenarios"></a>Portierungsszenarien

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a>Unity-Apps für HoloLens (1. Generation) HoloLens 2

Wenn Sie über eine vorhandene HoloLens-Unity-Anwendung (1. Generation) verfügen, die Sie zu einem HoloLens 2 portieren möchten, befolgen Sie die Anweisungen in unserem [HoloLens-Portierungsartikel.](./porting-hl1-hl2.md)

### <a name="immersive-vr-headsets"></a>Immersive Headsets (VR)

Wenn Sie Inhalte für andere VR-Geräte erstellt haben, müssen Sie alle anbieterspezifischen VR SDKs und potenziell Eingabezuordnungs-APIs neu auszuweisen. Informationen zu Unity- und Unreal-Portierungsszenarien finden Sie in unserem Leitfaden zum [Portieren immersiver Apps.](porting-guides.md)

Informationen zu den SteamVR-Funktionen, die Sie für Windows Mixed Reality Headsets aktualisieren möchten, finden Sie in unserem Leitfaden zur Aktualisierung von [SteamVR.](updating-your-steamvr-application-for-windows-mixed-reality.md)

### <a name="2d-universal-windows-applications"></a>Universelle 2D-Windows-Anwendungen

Wenn Sie über eine vorhandene 2D-UWP-App verfügen, die Sie entweder zu einem Windows Mixed Reality immersiven Headset oder HoloLens portieren möchten, befolgen Sie unsere Anweisungen zum Portieren von [2D-UWP-Apps für Windows Mixed Reality](building-2d-apps.md) Anweisungen.