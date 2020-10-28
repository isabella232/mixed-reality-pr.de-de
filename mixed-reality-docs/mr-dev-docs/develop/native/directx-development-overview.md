---
title: 'Native Entwicklung: Übersicht'
description: Erstellen Sie eine DirectX-basierte gemischte Reality-Engine, indem Sie die Windows Mixed Reality-APIs direkt verwenden.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: DirectX, Holographic Rendering, Native, Native APP, WinRT, WinRT-APP, Plattform-APIs, benutzerdefinierte Engine, Middleware
ms.openlocfilehash: fb51dfe15de26b80db255f0daca69e913f9ad35c
ms.sourcegitcommit: c199872c11adae7de24929ed043ea90dea087b3e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903113"
---
# <a name="native-development-overview"></a>Native Entwicklung: Übersicht

![Natives Banner Logo](../images/native_logo_banner.png)

3D-Engines wie [Unity](../unity/unity-development-overview.md) oder [Unreal](../unreal/unreal-development-overview.md) sind nicht die einzigen Entwicklungspfade mit gemischter Realität, die Ihnen offen sind. Sie können auch gemischte Reality-Apps erstellen, indem Sie direkt in die Windows Mixed Reality-APIs mit DirectX 11 oder DirectX 12 codieren. Wenn Sie die Plattform direkt nutzen, werden Sie im Grunde Ihre eigene Middleware oder Ihr eigenes Framework entwickeln. 

> [!IMPORTANT]
> Wenn Sie über ein vorhandenes WinRT-Projekt verfügen, das Sie verwalten möchten, besuchen Sie die [WinRT](creating-a-holographic-directx-project.md)-Haupt Dokumentation. 

## <a name="development-checkpoints"></a>Prüfpunkte für die Entwicklung

Nutzen Sie die folgenden Prüfpunkte, um Ihre Unity-Spiele und Anwendungen in eine Mixed Reality-Welt einzubringen.

### <a name="1-getting-started"></a>1. Erste Schritte

Windows Mixed Reality unterstützt [zwei Arten von apps](../../design/app-views.md):
* **Anwendungen mit gemischter Realität** (UWP oder Win32), die die [holographicspace-API](getting-a-holographicspace.md) oder die [openxr-API](openxr.md) verwenden, um eine [immersive Ansicht](../../design/app-views.md) für den Benutzer zu erzeugen, der die Headset-Anzeige füllt
* **2D-apps** (UWP), die DirectX, XAML oder ein anderes Framework zum Rendering von [2D-Ansichten](../../design/app-views.md#2d-views) auf Slate in der Windows Mixed Reality-Startseite verwenden

Die Unterschiede zwischen der DirectX [-Entwicklung für 2D-Ansichten und immersive Ansichten](../../design/app-views.md) betreffen in erster Linie das holografische Rendering und räumliche Eingaben. Die [iframeworkview](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) ihrer UWP-Anwendung oder das HWND ihrer Win32-Anwendung ist erforderlich und bleibt größtenteils unverändert. Das gleiche gilt für die WinRT-APIs, die für Ihre app verfügbar sind. Sie müssen jedoch eine andere Teilmenge dieser APIs verwenden, um die Vorteile der Holographic-Features zu nutzen. Beispielsweise werden die "vorhandenes SwapChain" und "Frame" vom System für holografische Anwendungen verwaltet, um eine von Pose vorhergesagte Frame Schleife zu aktivieren.

[!INCLUDE[](../includes/native-getting-started.md)]

### <a name="2-core-building-blocks"></a>2. Grundbausteine

Windows Mixed Reality-Anwendungen verwenden die folgenden APIs, um Umgebungen mit [gemischter Realität](../../discover/mixed-reality.md) für hololens und andere immersive Headsets zu erstellen:

|  Feature  |  Funktion  |
| --- | --- |
| [Anvisieren](../../design/gaze-and-commit.md) | Ermöglichen Sie Benutzern das Anzielen von Hologrammen durch Anblicken |
| [Geste](../../design/gaze-and-commit.md#composite-gestures) | Hinzufügen von räumlichen Aktionen zu ihren apps |
| [Holographisches Rendern](../platform-capabilities-and-apis/rendering.md) | Zeichnen Sie ein – Hologramm an einer exakten Stelle weltweit um Ihre Benutzer |
| [Bewegungs Controller](../../design/motion-controllers.md) | Ermöglichen Sie Ihren Benutzern, Aktionen in ihren Umgebungen mit gemischter Realität auszuführen. |
| [Räumliche Abbildung](../../design/spatial-mapping.md) | Bilden Sie Ihren physischen Raum mit einem überlagerten virtuellen Gittermodell ab, um die Begrenzungen Ihrer Umgebung zu kennzeichnen |
| [Voice](../../design/voice-input.md) | Erfassen Sie gesprochene Schlüsselwörter, Ausdrücke und Diktate von Benutzern |
 
> [!NOTE]
> In der openxr [Roadmap](openxr.md#roadmap) -Dokumentation finden Sie anstehende und in der Entwicklung stehende wichtige Features.

### <a name="3-deploying-and-testing"></a>3. bereitstellen und testen

Sie können mit OpenXR auf einem immersiven HoloLens 2- oder Windows Mixed Reality-Headset auf dem Desktop entwickeln.  Wenn Sie keinen Zugriff auf ein Headset haben, können Sie stattdessen den [hololens 2-Emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md) oder den [Windows Mixed Reality-Simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) verwenden.

## <a name="whats-next"></a>Wie geht es weiter?

Die Arbeit eines Entwicklers ist nie getan, insbesondere beim Lernen eines neuen Tools oder SDKs. Die folgenden Abschnitte führen Sie in Gebiete, die jenseits des Materials auf Einstiegsniveau liegen, das Sie bereits durchgearbeitet haben, ergänzt um nützliche Ressourcen, wenn es einmal hakt. Beachten Sie, dass diese Themen und Ressourcen keine bestimmte Reihenfolge aufweisen, tauchen Sie also ruhig ein!

### <a name="additional-resources"></a>Zusätzliche Ressourcen

Wenn Sie Ihr openxr-Spiel skalieren möchten, sehen Sie sich die folgenden Links an:

* [OpenXR – Bewährte Methoden](openxr-best-practices.md)
* [OpenXR – Leistung](openxr-performance.md)
* [OpenXR – Problembehandlung](openxr-troubleshooting.md)

## <a name="see-also"></a>Weitere Informationen
* [App-Modell](../../design/app-model.md)
* [App-Ansichten](../../design/app-views.md)
