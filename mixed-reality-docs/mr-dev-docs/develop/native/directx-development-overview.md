---
title: 'Native Entwicklung: Übersicht'
description: Erfahren Sie, wie Sie eine DirectX-basierte Mixed Reality-Engine mithilfe der Windows Mixed Reality APIs direkt erstellen.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: DirectX, holografisches Rendering, native, native App, WinRT, WinRT-App, Plattform-APIs, benutzerdefinierte Engine, Middleware, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 056cb0c07002cb319e8acadf66e7f59650f5e00413440d6ad0103aa8ee936400
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200164"
---
# <a name="native-development-overview"></a>Native Entwicklung: Übersicht

![Natives Bannerlogo](../images/native_logo_banner.png)

3D-Engines wie [Unity](../unity/unity-development-overview.md) oder [Unreal](../unreal/unreal-development-overview.md) sind nicht die einzigen Mixed Reality Entwicklungspfade, die Ihnen offen stehen. Sie können auch Mixed Reality-Apps mithilfe der Windows Mixed Reality-APIs mit DirectX 11 oder DirectX 12 erstellen. Wenn Sie zur Plattformquelle gehen, erstellen Sie im Wesentlichen Ihre eigene Middleware oder Ihr eigenes Framework. 

> [!IMPORTANT]
> Wenn Sie über ein vorhandenes WinRT-Projekt verfügen, das Sie verwalten möchten, besuchen Sie unsere [WinRT-Hauptdokumentation.](creating-a-holographic-directx-project.md) 

## <a name="development-checkpoints"></a>Prüfpunkte für die Entwicklung

Nutzen Sie die folgenden Prüfpunkte, um Ihre Unity-Spiele und Anwendungen in eine Mixed Reality-Welt einzubringen.

### <a name="1-getting-started"></a>1. Erste Schritte

Windows Mixed Reality unterstützt [zwei Arten von Apps:](../../design/app-views.md)
* UWP oder Win32 Mixed Reality Anwendungen, die die [HolographicSpace-API](getting-a-holographicspace.md) oder [](../../design/app-views.md) [OpenXR-API](openxr.md) verwenden, um eine immersive Ansicht zu rendern, die die Headsetanzeige füllt 
* **2D-Apps** (UWP), die DirectX, XAML oder ein anderes Framework zum Rendern [von 2D-Ansichten](../../design/app-views.md#2d-views) auf Slates im Windows Mixed Reality verwenden

Die Unterschiede zwischen der DirectX-Entwicklung für [2D-Ansichten und immersive](../../design/app-views.md) Ansichten betreffen hauptsächlich holografisches Rendering und räumliche Eingabe. Die [IFrameworkView](/uwp/api/Windows.ApplicationModel.Core.IFrameworkView) Ihrer UWP-Anwendung oder das HWND Ihrer Win32-Anwendung sind erforderlich und bleiben größtenteils gleich. Dasselbe gilt für die WinRT-APIs, die für Ihre App verfügbar sind. Sie müssen jedoch eine andere Teilmenge dieser APIs verwenden, um holografische Features nutzen zu können. Beispielsweise verwaltet das System für holografische Anwendungen die swapchain und frame present, um eine vorhergesagte Frameschleife zu ermöglichen.

[!INCLUDE[](../includes/native-getting-started.md)]

### <a name="2-core-building-blocks"></a>2. Grundbausteine

Windows Mixed Reality-Anwendungen verwenden die folgenden APIs, um [Mixed Reality-Umgebungen](../../discover/mixed-reality.md) für HoloLens und andere immersive Headsets zu erstellen:

|  Feature  |  Funktion  |
| --- | --- |
| [Anvisieren](../../design/gaze-and-commit.md) | Ermöglichen Sie Benutzern das Anzielen von Hologrammen durch Anblicken |
| [Geste](../../design/gaze-and-commit.md#composite-gestures) | Hinzufügen räumlicher Aktionen zu Ihren Apps |
| [Holographisches Rendern](../platform-capabilities-and-apis/rendering.md) | Zeichnen eines Hologramms an einer präzisen Position in der Welt um Ihre Benutzer |
| [Motion-Controller](../../design/motion-controllers.md) | Ermöglichen Sie es Ihren Benutzern, in Ihren Mixed Reality maßnahmen zu ergreifen. |
| [Räumliche Abbildung](../../design/spatial-mapping.md) | Bilden Sie Ihren physischen Raum mit einem überlagerten virtuellen Gittermodell ab, um die Begrenzungen Ihrer Umgebung zu kennzeichnen |
| [Voice](../../design/voice-input.md) | Erfassen Sie gesprochene Schlüsselwörter, Ausdrücke und Diktate von Benutzern |
 
> [!NOTE]
> Zukünftige und in der Entwicklung enthaltene Kernfeatures finden Sie in der Dokumentation zur [OpenXR-Roadmap.](openxr.md#roadmap)

### <a name="3-deploying-and-testing"></a>3. Bereitstellen und Testen

Sie können auf einem Desktop entwickeln, indem Sie OpenXR auf einem HoloLens 2 oder Windows Mixed Reality immersive Headsets verwenden.  Wenn Sie keinen Zugriff auf ein Headset haben, können Sie stattdessen den HoloLens 2 Emulator [oder](../platform-capabilities-and-apis/using-the-hololens-emulator.md) den Windows Mixed Reality [Simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) verwenden.

## <a name="whats-next"></a>Wie geht es weiter?

Die Arbeit eines Entwicklers ist nie getan, insbesondere nicht beim Lernen eines neuen Tools oder SDKs. Die folgenden Abschnitte können Sie in Bereiche bringen, die über das Material für Anfänger hinausgehen, das Sie bereits abgeschlossen haben. Diese Themen und Ressourcen befinden sich nicht in einer sequenziellen Reihenfolge. Sie können also gerne losspringen und sich damit aus dem Weg machen.

### <a name="additional-resources"></a>Zusätzliche Ressourcen

Wenn Sie Ihr OpenXR-Spiel auf ein Level-Up-Level bringen möchten, sehen Sie sich die folgenden Links an:

* [OpenXR – Bewährte Methoden](openxr-best-practices.md)
* [OpenXR – Leistung](openxr-performance.md)
* [OpenXR – Problembehandlung](openxr-troubleshooting.md)

## <a name="see-also"></a>Siehe auch
* [App-Modell](../../design/app-model.md)
* [App-Ansichten](../../design/app-views.md)