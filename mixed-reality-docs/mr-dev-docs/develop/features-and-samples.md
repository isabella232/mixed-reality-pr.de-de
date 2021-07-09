---
title: Beispiele und Feature-Apps
description: Bleiben Sie bei allen verfügbaren Microsoft-Beispielen und Mixed Reality-Feature-Apps für HoloLens auf dem neuesten Stand.
author: hferrone
ms.author: jemccull
ms.date: 6/7/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, Lernen, Beispiele, MRTK, Forschungsmodus, HoloLens 2, QR-Codes, WebRTC, Mixed Reality-Aufnahme, Holographic Remoting, UX-Tools
ms.localizationpriority: high
ms.openlocfilehash: 78a9e343fde4a6cbc23268f0be353577498d67b6
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906896"
---
# <a name="samples-and-feature-apps"></a>Beispiele und Feature-Apps

![Abbildung eines Benutzers, der eine HoloLens trägt und ein Hologramm mit Handbewegungen manipuliert.](unreal/images/unreal-developer.jpg)

Jede Entwicklungs-Journey beginnt mit einem Blick zurück auf das, was andere Entwickler erfolgreich aufgebaut haben – Mixed Reality macht da keinen Unterschied. Aktuell sind alle unsere Tutorials und Beispiel-Apps in Unity oder Unreal entwickelt. Wenn wir Inhalte für andere Engines und Plattformen entwickeln, finden Sie diese unter der entsprechenden Überschrift im Inhaltsverzeichnis.

## <a name="sample-apps"></a>Beispiel-Apps

[!INCLUDE[](includes/tabs-samples.md)]

## <a name="feature-samples"></a>Featurebeispiele

Die unten aufgeführten Featurebeispiele entsprechen bestimmten Implementierungen, die in unserer Dokumentation behandelt werden, und decken eine Reihe von Entwicklungsplattformen und Hardwaregeräten ab.

### <a name="openxr"></a>OpenXR

Entwickler, die für Unity 2020 entwickeln, um HoloLens 2- oder Mixed Reality-Anwendungen zu erstellen, können das OpenXR-Plug-In anstelle des WindowsXR-Plug-Ins verwenden, um eine bessere plattformübergreifende Kompatibilität zu erzielen. Das Mixed Reality OpenXR-Plug-In funktioniert auch gut mit dem neuesten Mixed Reality Toolkit 2.7.

<br>

| Referenzartikel | Beispiel |
| --- | --- |
| [Verwenden des OpenXR-Plug-Ins](./unity/xr-project-setup.md) | [Mixed Reality OpenXR mit Unity-Beispielen](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) |
| – | [OpenXR MRTK-Basisprojekt für Unity](https://github.com/microsoft/UnityOpenXRMRTKBase) |

### <a name="research-mode"></a>Forschungsmodus

Der Forschungsmodus wurde in der HoloLens der 1. Generation eingeführt, um Zugriff auf wesentliche Sensoren des Geräts zu gewähren, insbesondere für Forschungsanwendungen, die nicht für die Bereitstellung vorgesehen sind. Die folgenden Beispielanwendungen sind Beispiele für den Zugriff auf und die Aufzeichnung von Forschungsmodus-Datenströmen und die Verwendung der [intrinsischen und extrinsischen Funktionen](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).

<br>

| Referenzartikel | Beispielanwendung |
| --- | --- |
| [Forschungsmodus](platform-capabilities-and-apis/research-mode.md) | [HoloLens (1. Generation)](https://github.com/microsoft/HoloLensForCV/tree/master/Samples) |
| [Forschungsmodus](platform-capabilities-and-apis/research-mode.md) | [HoloLens 2](https://github.com/microsoft/HoloLens2ForCV/tree/main/Samples) |

### <a name="qr-codes"></a>QR-Codes

HoloLens 2 kann QR-Codes in der Umgebung um das Headset erkennen und ein Koordinatensystem an der Position jedes Codes in der realen Welt einrichten.

<br>

| Referenzartikel | Beispiel |
| --- | --- |
| [QR-Codes](platform-capabilities-and-apis/qr-code-tracking.md) | [Nachverfolgen von QR-Codes in Unity](https://github.com/microsoft/MixedReality-QRCode-Sample) |

### <a name="scene-understanding"></a>Grundlegendes zu Szenen

Szenenverständnis bietet Mixed Reality-Entwicklern eine strukturierte, allgemeine Umgebungsdarstellung, die die Entwicklung für umgebungssensible Anwendungen intuitiv macht. Das Szenenverständnis erreicht dies durch die Kombination der Leistung vorhandener Mixed Reality-Runtimes wie der hochgenauen, aber weniger strukturierten räumlichen Abbildung mit neuen KI-gesteuerten Runtimes.

<br>

| Referenzartikel | Beispiel |
| --- | --- |
| [Grundlegendes zu Szenen](../design/scene-understanding.md) | [Beispiele für Mixed Reality-Szenenverständnis](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples) |

### <a name="webrtc"></a>WebRTC

Das MixedReality-WebRTC-Projekt ist eine Sammlung von Komponenten, die Entwicklern von Mixed Reality-Apps bei der Integration von Peer-to-Peer-Audio, -Video und Daten-Echtzeitkommunikation in Ihre Anwendungen helfen soll. WebRTC-Komponenten basieren auf dem WebRTC-Protokoll für Echtzeitkommunikation (RTC), das von den meisten modernen Webbrowsern unterstützt wird.

<br>

| Referenzartikel | Beispiel |
| --- | --- |
| [WebRTC](https://microsoft.github.io/MixedReality-WebRTC) | [WebRTC-Beispiel-Apps](https://github.com/microsoft/MixedReality-WebRTC/tree/master/examples) |

### <a name="holographic-mixed-reality-capture"></a>Holographische Mixed Reality-Aufnahme

Mit Mixed Reality-Aufnahme (MRC) wird die „Erste Person“-Erfahrung (Ego-Perspektive) der Vermischung realer mit digitalen Welten als Foto oder Video aufgenommen, wobei Sie das Gesehene mit anderen in Echtzeit teilen können.

<br>

| Referenzartikel | Beispiel |
| --- | --- |
| [Mixed Reality-Aufnahme](platform-capabilities-and-apis/mixed-reality-capture-for-developers.md) | [Beispiele für Mixed Reality-Aufnahme](/samples/microsoft/windows-universal-samples/holographicmixedrealitycapture/) |

### <a name="holographic-remoting"></a>Holographic Remoting

Der Holographic Remoting-Player ist eine Begleit-App, die sich mit PC-Apps und -Spielen verbindet, die Holographic Remoting unterstützen. Holographic Remoting streamt holographische Inhalte in Echtzeit über eine WLAN-Verbindung von einem PC an Ihre Microsoft HoloLens. Es wird von HoloLens (1. Generation) und HoloLens 2 unterstützt.

<br>

| Referenzartikel | Beispiel |
| --- | --- |
| [Holographic Remoting](platform-capabilities-and-apis/holographic-remoting-player.md) | [Holographic Remoting-Beispiele](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples) |