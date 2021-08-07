---
title: Übersicht zum Portieren
description: Eine Übersicht über die verschiedenen Portierungsoptionen, mit deren Unterstützung Sie Ihre vorhandenen Anwendungen Mixed Reality für HoloLens VR nutzen können.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: Portieren, Unity, Middleware, Engine, UWP, Win32
ms.openlocfilehash: 519dae088e689e0a6e617bf5e2b34f81cc2e265256c4844df7dd34e99172d536
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189420"
---
# <a name="porting-overview"></a>Übersicht zum Portieren

Wenn es um das Portieren oder Aktualisieren Ihrer vorhandenen Projekte für Mixed Reality geht, hängt Ihre Portierungs journey davon ab, ob Ihre App mit Unity oder Unreal Engine erstellt wurde und auf HoloLens (1. Generation) oder HoloLens 2 oder SteamVR zielt. Diese Übersichtsseite enthält unsere aktuellen Empfehlungen für jede Plattform und jedes Gerät. Überprüfen Sie unbedingt, da sich diese Prozesse immer ändern.

Richten Sie zuerst Ihr Projektziel basierend auf unseren [Unity-](#unity) und [Unreal-Empfehlungen](#unreal) ein, und befolgen Sie dann eines oder mehrere unserer Portierungsszenarien:

- [HoloLens (1. Generation) für HoloLens 2](#hololens-1st-gen-unity-apps-to-hololens-2)
- [Immersive Headsets (VR)](#immersive-vr-headsets)
- [2D-UWP-Apps](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a>Empfohlene Projektziele

Es ist wichtig, ihre Projekte auf dem neuesten Stand zu halten, unabhängig davon, ob Sie eine App auf ein anderes Zielgerät portieren. Unsere aktuellen Empfehlungen finden Sie in den unten aufgeführten enginebasierten Ressourcen.

### <a name="unity"></a>Unity

Aktuelle [Anleitungen zu den](../unity/choosing-unity-version.md) empfohlenen Unity- und MRTK-Versionen finden Sie auf der Seite Auswählen einer Unity-Version.

### <a name="unreal"></a>Unreal

Aktuelle Informationen [zu den empfohlenen Unreal-](../unreal/unreal-project-setup.md) und MRTK-Versionen finden Sie auf der Seite Einrichten Ihres Unreal-Projekts.

## <a name="porting-scenarios"></a>Portierungsszenarien

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a>HoloLens Unity-Apps (1. Generation) für HoloLens 2

Wenn Sie über eine vorhandene HoloLens-Unity-Anwendung (1. Generation) verfügen, die Sie zu einem HoloLens 2 portieren möchten, befolgen Sie die Anweisungen in unserem Artikel HoloLens [Portierung.](./porting-hl1-hl2.md)

### <a name="immersive-vr-headsets"></a>Immersive Headsets (VR)

Wenn Sie Inhalte für andere VR-Geräte erstellt haben, müssen Sie anbieterspezifische VR SDKs und potenziell Eingabezuordnungs-APIs neu zuordnen. Informationen zu Unity- und Unreal-Portierungsszenarien finden Sie in unserem [Portierungsleitfaden für immersive Apps.](porting-guides.md)

Informationen zu Den Funktionen von SteamVR, die Sie für Windows Mixed Reality Headsets aktualisieren möchten, finden Sie in unserem [Leitfaden zur Aktualisierung von SteamVR.](updating-your-steamvr-application-for-windows-mixed-reality.md)

### <a name="2d-universal-windows-applications"></a>2D Universal Windows-Anwendungen

Wenn Sie über eine vorhandene 2D-UWP-App verfügen, die Sie entweder auf ein immersives Windows Mixed Reality-Headset oder HoloLens portieren möchten, befolgen Sie unsere Anleitungen zum Portieren [von 2D-UWP-Windows Mixed Reality.](building-2d-apps.md)