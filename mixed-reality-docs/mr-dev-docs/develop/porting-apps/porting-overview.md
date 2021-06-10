---
title: Übersicht zum Portieren
description: Eine Übersicht über die verschiedenen Portierungsoptionen zum Bringen Ihrer vorhandenen Anwendungen in Mixed Reality für HoloLens und VR.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: Portieren, Unity, Middleware, Engine, UWP, Win32
ms.openlocfilehash: 9b056bd81a725fea23c1e7f3bfcd9844680086c6
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600499"
---
# <a name="porting-overview"></a>Übersicht zum Portieren

Wenn es um das Portieren oder Aktualisieren Ihrer vorhandenen Projekte für Mixed Reality geht, hängt Ihre Portierungs journey davon ab, ob Ihre App mit Unity oder Unreal Engine erstellt wurde und HoloLens (1. Generation) oder HoloLens 2 oder SteamVR als Ziel hat. Diese Übersichtsseite enthält unsere aktuellen Empfehlungen für jede Plattform und jedes Gerät. Achten Sie darauf, sich zu vergewissern, dass sich diese Prozesse immer ändern.

Richten Sie zunächst Ihr Projektziel basierend auf unseren [Unity-](#unity) und [Unreal-Empfehlungen](#unreal) ein, und folgen Sie dann mindestens einem unserer Portierungsszenarien:

- [HoloLens (1. Generation) zum HoloLens 2](#hololens-1st-gen-unity-apps-to-hololens-2)
- [Windows Mixed Reality-Headsets](#windows-mixed-reality-headsets)
- [SteamVR-Apps](#steamvr-applications)
- [2D-UWP-Apps](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a>Empfohlene Projektziele

Es ist wichtig, ihre Projekte auf dem neuesten Stand zu halten, unabhängig davon, ob Sie eine App auf ein anderes Zielgerät portieren. Unsere aktuellen Empfehlungen finden Sie in den unten aufgeführten enginebasierten Ressourcen.

### <a name="unity"></a>Unity

Unsere aktuelle Empfehlung für die Unity-Entwicklung mit Mixed Reality ist **Unity 2019 LTS unter Verwendung des Legacy-XR-Pakets.** Wenn Ihr Projekt das Mixed Reality Toolkit verwendet, überprüfen Sie, ob Sie die neueste Version verwenden, die derzeit **MRTK-Unity 2.5** ist.

> [!CAUTION]
> Während das XR SDK mit dieser Version von Unity verfügbar ist, ist Azure Spatial Anchors derzeit nicht mit diesem Setup kompatibel. Diese Empfehlung wird mit einer zukünftigen Version des Azure Spatial Anchors-Pakets für Unity aktualisiert.
> 
> * Wenn Sie Azure Spatial Anchors nicht benötigen, können Sie [Ihr Unity-Projekt für XR konfigurieren](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) und [mit MRTK und dem XR SDK beginnen.](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk)
> 
> * Wenn Sie derzeit das XR SDK in Ihrem Projekt verwenden und Azure Spatial Anchors verwenden möchten, deinstallieren Sie das XR SDK, und installieren Sie das Legacy-XR-Paket neu, um Ihre Projekteinstellungen wie zu ändern.

### <a name="unreal"></a>Unreal

Unsere aktuelle Empfehlung für die Unreal-Entwicklung mit Mixed Reality ist **Unreal Engine 4.26**. Wenn Ihr Projekt die Mixed Reality Toolkit UX Tools verwendet, stellen Sie sicher, dass Sie die neueste Version verwenden, die derzeit **UXT 0.10** ist.

## <a name="porting-scenarios"></a>Portierungsszenarien

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a>Unity-Apps für HoloLens (1. Generation) HoloLens 2

Wenn Sie über eine vorhandene HoloLens-Unity-Anwendung (1. Generation) verfügen, die Sie zu einem HoloLens 2 portieren möchten, befolgen Sie die Anweisungen in unserem [HoloLens-Portierungsartikel.](./porting-hl1-hl2.md)

### <a name="windows-mixed-reality-headsets"></a>Windows Mixed Reality-Headsets

Wenn Sie Inhalte für andere Geräte erstellt haben, z. B. Oculus Rift oder HP Reverb G2, müssen Sie anbieterspezifische VR SDKs und potenziell Eingabezuordnungs-APIs neu auszuweisen. Informationen zu Unity- und Unreal-Portierungsszenarien finden Sie in unserem Leitfaden zum [Portieren immersiver Apps.](porting-guides.md)

### <a name="steamvr-applications"></a>SteamVR-Anwendungen

Informationen zu allen SteamVR-Funktionen, die Sie für Windows Mixed Reality Headsets aktualisieren möchten, finden Sie in unserem Leitfaden zur Aktualisierung von [SteamVR.](updating-your-steamvr-application-for-windows-mixed-reality.md)

### <a name="2d-universal-windows-applications"></a>Universelle 2D-Windows-Anwendungen

Wenn Sie über eine vorhandene 2D-UWP-App verfügen, die Sie entweder zu einem Windows Mixed Reality immersiven Headset oder HoloLens portieren möchten, befolgen Sie unsere Anweisungen [zum Portieren von 2D-UWP-Apps für Windows Mixed Reality](building-2d-apps.md) Anweisungen.