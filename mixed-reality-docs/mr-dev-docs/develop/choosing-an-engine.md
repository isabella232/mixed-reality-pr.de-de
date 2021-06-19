---
title: Auswählen ihrer Engine
description: Hier erhalten Sie eine Einführung in die Engine-Optionen, die für Mixed Reality Entwicklung für HoloLens und VR verfügbar sind.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Unity
ms.openlocfilehash: c91a4df9db8ef71778421750bca48d81d4b4a02e
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394524"
---
# <a name="choosing-your-engine"></a>Auswählen ihrer Engine

Es gibt mehrere Entwicklungspfade, über die Sie unsere Dokumentation durchlaufen können. Der erste Schritt besteht darin, die Technologie zu finden, die für Sie geeignet ist. Wenn Sie bereits an eine bestimmte denken, springen Sie direkt zum entsprechenden Tab weiter unten. Wenn Sie noch unentschlossen sind oder gerade erst anfangen, sehen Sie sich alle einmal einzeln an, um zu verstehen, was sie bieten, also die verfügbaren Plattformen und Tools, und beginnen Sie mit der Entwicklung!

> [!IMPORTANT]
> Werfen Sie einen Blick auf unsere **[Übersicht zu Portierungsleitfäden](porting-apps/porting-overview.md)** , wenn Sie vorhandene Projekte auf HoloLens 2 oder immersiven VR-Headsets wie dem Reverb G2 bereitstellen möchten. Wir haben Anleitungen für Projekte, die HTK, MRTK v1 oder SteamVR verwenden oder für immersive Headsets wie Oculus Rift oder HTC Vive entwickelt wurden.

## <a name="engine-overview"></a>Engine-Übersicht

* **Unity** ist eine der führenden Echtzeit-Entwicklungsplattformen auf dem Markt, bei der zugrunde liegender Laufzeitcode in C++ geschrieben ist und alle Entwicklungsskripts in C# ausgeführt werden. Unabhängig davon, ob Sie Spiele, Filme und Animationsfilme erstellen oder sogar Architektur- oder technische Konzepte in einer virtuellen Welt rendern möchten, bietet Unity die Infrastruktur, um Sie dabei zu unterstützen.

* **Unreal Engine 4 ist** eine leistungsstarke Open Source-Erstellungs-Engine mit vollständiger Unterstützung für Mixed Reality in C++ und Blueprints. Ab Version 4.25 bietet Unreal Engine umfassende und produktionsreife HoloLens-Unterstützung. Dank Funktionen wie dem flexiblen Visual Scripting-System für Blaupausen können Designer praktisch die gesamte Palette an Konzepten und Tools verwenden, die normalerweise nur Programmierern zur Verfügung stehen. Designer nutzen branchenübergreifend das hohe Maß an Freiheit und Kontrolle, um innovative Inhalte, interaktive Erlebnisse und immersive virtuelle Welten zu schaffen.

* **Native** Entwickler mit Erfahrung beim Schreiben eigener 3D-Renderer können mit OpenXR eine benutzerdefinierte Engine erstellen. OpenXR ist ein offener, lizenzgebührenfreier API-Standard von Khronos, mit dem Engines nativen Zugriff auf eine große Bandbreite von Geräten von Herstellern aus dem gesamten Mixed Reality-Spektrum erhalten. Sie können mit OpenXR auf einem immersiven HoloLens 2- oder Windows Mixed Reality-Headset auf dem Desktop entwickeln.

* **Webentwickler,** die überzeugende browserübergreifende AR/VR-Weberfahrungen erstellen, können **WebXR verwenden.**

    > [!NOTE]
    > **Babylon.js** für die HoloLens-Entwicklung wird derzeit in Bearbeitung. Sehen Sie sich die [neuesten Nachrichten an, und interagieren Sie mit der Community!](https://doc.babylonjs.com/divingDeeper/webXR/introToWebXR)

<!-- Babylon is a Javascript-based, open source, 3D graphics engine capable of powering 3D scenes in a web browser. Babylon.js 4.2+ includes support for WebXR. With Babylon React Native, you can even build cross-platform native     applications for PC, mobile, and mixed reality devices. -->

## <a name="features-and-devices"></a>Features und Geräte

<br>

| Logistics | Unity | Unreal | JavaScript | Benutzerdefinierte Engine <br>(mit OpenXR) |
|---|---|---|---|---|
| Sprache | C# | C++ | JavaScript | C/C++ |
| Preise | [Unity – Preise](https://store.unity.com/#plans-individual) | [Unreal– Preise](https://www.unrealengine.com/download) | Kostenlos | Kostenlos |

<br>

| Gerätefunktionen | Unity | Unreal | JavaScript | Benutzerdefinierte Engine <br>(mit OpenXR) |
|---|---|---|---|---|
| Geräte-/Anzeigenachverfolgung | ✔️ | ✔️ | ✔️ | ✔️ |
| Handeingabe | ✔️ | ✔️ | ✔️ | ✔️ |
| Augeneingabe | ✔️ | ✔️ | ❌ | ✔️ |
| Spracheingabe | ✔️ | ✔️ | ✔️ | ✔️ |
| Bewegungscontroller | ✔️ | ✔️ | ✔️ | ✔️ |
| Treffertests für Ebene/Gitternetz | ✔️ | ✔️ | ✔️ | ✔️ |
| Grundlegendes zu Szenen | ✔️ | ✔️ | ❌ | ✔️ |
| Raumklang | ✔️ | ✔️ | ✔️ | ✔️ |
| QR-Code-Erkennung | ✔️ | ✔️ | ❌ | ✔️ |

<br>

| Hardware | Unity | Unreal | JavaScript | Benutzerdefinierte Engine <br>(mit OpenXR) |
|---|---|---|---|---|
| HoloLens 2 | ✔️ | ✔️ | ✔️ | ✔️ |
| HoloLens (1. Generation) | ✔️ | ✔️ | ❌ | Nur WinRT (Legacy) |
| [Windows Mixed Reality-Headsets](../discover/immersive-headset-hardware-details.md) | ✔️ | ✔️ | ✔️ | ✔️ |
| SteamVR-Headsets | ✔️ | ✔️ | ✔️ | ✔️ |
| Oculus Quest/Rift | ✔️ | ✔️ | ✔️ | ✔️ |
| Mobil (ARCore/ARKit) | ✔️ | ✔️ | ✔️ | ❌ |

<br>

| Tools | Unity | Unreal | JavaScript | Benutzerdefinierte Engine <br>(mit OpenXR) |
|---|---|---|---|---|
| Mixed Reality-Toolkit | ✔️ | ✔️ | ❌  | ❌ |
| World Locking Tools | ✔️ | ❌ | ❌  | ❌ |
<!-- | Mesh | ❌ | ❌ | ❌ | ❌ | -->

<br>

| Clouddienste | Unity | Unreal | JavaScript | Benutzerdefinierte Engine <br>(mit OpenXR) |
|---|---|---|---|---|
| Azure Spatial Anchors | ✔️ | ✔️ | ❌ | ✔️ |
| Azure Object Anchors | ✔️ | ❌ | ❌ | ✔️ |
| Azure Remote Rendering | ✔️ * | ❌ | ❌ | ✔️ * |

> [!NOTE]
> * Azure Remote Rendering wird derzeit in Apps unterstützt, die die älteren WinRT-APIs (Windows XR-Plug-In in Unity) verwenden. ARR-Unterstützung für OpenXR-Apps ist in Kürze verfügbar.

## <a name="next-steps"></a>Nächste Schritte

[!INCLUDE[](includes/tools-next-steps.md)]