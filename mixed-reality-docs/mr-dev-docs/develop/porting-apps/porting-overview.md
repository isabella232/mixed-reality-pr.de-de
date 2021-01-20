---
title: Übersicht zum Portieren
description: Eine Übersicht über die verschiedenen Portierungs Optionen, um Ihre vorhandenen Anwendungen in die gemischte Realität für hololens und VR zu bringen.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: portieren, Unity, Middleware, Engine, UWP, Win32
ms.openlocfilehash: 268d98b45aa659614e0266bfd1add7c7ed2f684a
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583580"
---
# <a name="porting-overview"></a>Übersicht zum Portieren

Wenn Sie Ihre vorhandenen Projekte für gemischte Realität portieren oder aktualisieren, hängt ihre Portierung davon ab, ob Ihre APP mit Unity oder Unreal Engine erstellt wurde, und zielt auf hololens (1st Gen) oder hololens 2 oder steamvr ab. Diese Übersichtsseite enthält unsere aktuellen Empfehlungen für jede Plattform und jedes Gerät. Stellen Sie sicher, dass Sie den Vorgang erneut durchlaufen, da sich diese Prozesse immer ändern.

Richten Sie zuerst das Projektziel basierend auf unseren [Unity](#unity) -und [Unreal](#unreal) -Empfehlungen ein, und folgen Sie dann einem oder mehreren unserer Portierungs Szenarien:

- [Hololens (1. Gen) bis hololens 2](#hololens-1st-gen-unity-apps-to-hololens-2)
- [Windows Mixed Reality-Headsets](#windows-mixed-reality-headsets)
- [Steamvr-apps](#steamvr-applications)
- [2D UWP-apps](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a>Empfohlene Projektziele

Es ist wichtig, Ihre Projekte auf dem neuesten Stand zu halten, unabhängig davon, ob Sie eine APP auf ein anderes Zielgerät portieren. Unsere aktuellen Empfehlungen finden Sie in den unten aufgeführten Engine-basierten Ressourcen.

### <a name="unity"></a>Unity

Unsere aktuelle Empfehlung für die Unity-Entwicklung mit gemischter Realität ist **Unity 2019 LTS mit dem alten XR-Paket**. Wenn Ihr Projekt das Mixed Reality Toolkit verwendet, überprüfen Sie, ob Sie die neueste Version verwenden, die zurzeit **mrtk-Unity 2,5** ist.

> [!CAUTION]
> Obwohl das XR SDK mit dieser Version von Unity verfügbar ist, ist Azure Spatial Anchor zurzeit mit diesem Setup nicht kompatibel. Diese Empfehlung wird mit einer zukünftigen Version des Azure Spatial Anchor-Pakets für Unity aktualisiert. 
> 
> * Wenn Sie keine räumlichen Azure-Anker benötigen, können Sie [Ihr Unity-Projekt für XR konfigurieren und die](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) ersten Schritte [mit dem mrtk-und XR SDK durchsetzen](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithMRTKAndXRSDK.html).
> 
> * Wenn Sie zurzeit das XR SDK in Ihrem Projekt verwenden und Azure Spatial Anchor verwenden möchten, deinstallieren Sie das SDK SDK, und installieren Sie das Legacy-XR-Paket erneut, um Ihre Projekteinstellungen wiederherzustellen.


### <a name="unreal"></a>Unreal 

Unsere aktuelle Empfehlung für die Unreal-Entwicklung mit gemischter Realität ist **Unreal Engine 4,26**. Wenn Ihr Projekt die Mixed Reality Toolkit-UX-Tools verwendet, stellen Sie sicher, dass Sie die neueste Version verwenden, die derzeit **UXT 0,10** ist.

## <a name="porting-scenarios"></a>Portieren von Szenarien

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a>Hololens (1. Gen) Unity-apps auf hololens 2

Wenn Sie über eine vorhandene Unity-Anwendung hololens (1st Gen) verfügen, die Sie auf einen hololens 2 portieren möchten, befolgen Sie die Anweisungen in unserem [Artikel zum Portieren von hololens](./porting-hl1-hl2.md).

### <a name="windows-mixed-reality-headsets"></a>Windows Mixed Reality-Headsets

Wenn Sie Inhalte für andere Geräte (z. b. den Oculus-oder HP-Reverb) erstellt haben, müssen Sie herstellerspezifische VR-SDBs und möglicherweise APIs für die Eingabe Zuordnung neu zuweisen. Informationen zu Unity-und Unreal-Portierungs Szenarien finden Sie in unserem [Leitfaden zum Portieren von immersiven apps](porting-guides.md).

### <a name="steamvr-applications"></a>Steamvr-Anwendungen

Informationen zu den von Ihnen für Windows Mixed Reality-Headsets zu aktualisierenden Funktionen von steamvr finden Sie in unserem [Handbuch zum Aktualisieren von steamvr](updating-your-steamvr-application-for-windows-mixed-reality.md).

### <a name="2d-universal-windows-applications"></a>2D universelle Windows-Anwendungen

Wenn Sie über eine vorhandene 2D-UWP-App verfügen, die Sie entweder in ein Windows Mixed Reality-immersives Headset oder hololens portieren möchten, befolgen Sie die Anweisungen unter [Portieren von 2D-UWP-Apps für Windows Mixed Reality](building-2d-apps.md) .