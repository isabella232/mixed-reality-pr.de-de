---
title: Unreal-Entwicklung – Übersicht
description: Machen Sie Ihre ersten Schritte in der Mixed Reality-Entwicklung für HoloLens und VR mithilfe von Unreal Engine 4 auf unserer kuratierten Journey entlang von Prüfpunkten.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Streaming, Remoting, Mixed Reality, Entwicklung, erste Schritte, Features, neues Projekt, Emulator, Dokumentation, Leitfäden, Features, Hologramme, Spieleentwicklung, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, OpenXR
ms.openlocfilehash: fd9eec18e865910ef4899dfda75661d1edb57eed25a55641cde3ca7ac3f0b3a8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203467"
---
# <a name="unreal-development-overview"></a>Unreal-Entwicklung – Übersicht

![Unreal-Bannerlogo](../images/unreal_logo_banner.png)

Die ersten Schritte mit <a href="/windows/mixed-reality" target="_blank" title="Mixed Reality-Dokumentation"> Mixed Reality-Anwendungen</a> sind eine Herausforderung. Neue Konzepte, Plattformen und neuartige Hardware können sich als Hürden erweisen. Wenn Sie jedoch Unreal-Entwickler sind, haben Sie Glück. Unreal Engine 4 besitzt vollständige Unterstützung für <a href="https://www.microsoft.com/windows/windows-mixed-reality" target="_blank" title="Windows Mixed Reality-Dokumentation">Windows Mixed Reality</a> (VR) und <a href="https://www.microsoft.com/hololens/hardware" target="_blank" title="HoloLens 2-Dokumentation">HoloLens 2</a> (AR)-Geräte.

[!INCLUDE[](includes/tabs-unreal-features.md)]

Wenn Sie noch nicht mit der Unreal-Entwicklung vertraut sind, sollten Sie sich zunächst etwas einarbeiten. Sehen Sie sich die <a href="https://docs.unrealengine.com/GettingStarted/index.html" target="_blank">Tutorialreihe</a> zu Unreal an und suchen Sie im Unreal <a href="https://www.unrealengine.com/marketplace/store" target="_blank">Marketplace</a> nach Ressourcen. Unterstützung finden Sie auch in den Mixed Reality-<a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">Foren</a>. Bei diesen Ressourcen handelt es sich um Links zur Community von Entwicklern und Problemlösern auf dem Gebiet der Mixed Reality.

> [!IMPORTANT]
> Werfen Sie einen Blick auf unsere **[Portierungsleitfäden](unreal-reverb-g2-controllers.md)** , wenn Sie ein vorhandenes Unreal-Projekt auf immersiven Headsets wie dem Reverb G2 bereitstellen möchten.

## <a name="development-checkpoints"></a>Prüfpunkte für die Entwicklung

Nutzen Sie die folgenden Prüfpunkte, um Ihre Unreal-Spiele und Anwendungen in eine Mixed Reality-Welt einzubringen. Wenn Sie sich noch nicht mit der [Beispielanwendung zum Entwerfen von Hologrammen](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd) befasst haben, empfehlen wir Ihnen, sie herunterzuladen, um sich mit den Grundlagen von Mixed Reality UX vertraut zu machen.

### <a name="1-getting-started"></a>1. Erste Schritte

Zunächst müssen Sie die Tools für die HoloLens 2-Entwicklung installieren. Als Nächstes arbeiten Sie unsere Tutorialreihe durch, um ein grundlegendes Verständnis des Mixed Reality Toolkits, eine ordnungsgemäß konfigurierte Entwicklungsumgebung für Mixed Reality-Apps und ein funktionierendes MRTK-Projekt in Unreal zu erhalten. Ab Unreal 4.26 besitzen Sie auch die Möglichkeit, eine OpenXR-App für HoloLens 2 zu entwickeln.

|  Prüfpunkt  |  Ergebnis  |
| --- | --- |
| [Installieren der neuesten Tools](../install-the-tools.md) | Laden Sie die neueste Version der Unreal Engine herunter, installieren Sie sie, und richten Sie Ihr Projekt für Mixed Reality ein |
| [Einrichten des Projekts](unreal-project-setup.md) | Abrufen der neuesten Version der Unreal Engine und des MRTK |
| [Erstellen Ihrer ersten HoloLens Unreal-Anwendung](unreal-quickstart.md) | Beginnen Sie Ihre Reise in die Unreal- und HoloLens-Entwicklung mit dem Erstellen einer einfachen Mixed Reality-Anwendung |
| [Hololens 2-Tutorialreihe](tutorials/unreal-uxt-ch1.md) | Richten Sie sich für die Mixed Reality-Entwicklung in Unreal ein, erstellen Sie Ihre erste App mit MRTK, und stellen Sie Ihre App in HoloLens 2 bereit. |
| Erste Schritte mit [OpenXR](../native/openxr.md) in Unreal | Installieren und aktivieren Sie das folgende Plug-In aus dem Unreal Engine Marketplace:<ul><li> [Microsoft OpenXR](https://www.unrealengine.com/marketplace/en-US/product/ef8930ca860148c498b46887da196239)</li></ul>Stellen Sie sicher, dass das Microsoft Windows Mixed Reality-Plug-In deaktiviert ist.<br><br>Die vollständige Liste der derzeit unterstützten Funktionen in OpenXR finden Sie weiter [unten](#supported-features).|

### <a name="2-core-building-blocks"></a>2. Grundbausteine

Es gibt eine Reihe wichtiger Mixed Reality-Features, die in unserer Tutorialreihe nicht behandelt werden. Diese Bausteine stehen als eigenständige Features und über das Mixed Reality Toolkit zur Verfügung. Sie benötigen sie möglicherweise nicht alle auf einmal, aber wir empfehlen Ihnen, sich frühzeitig mit ihnen vertraut zu machen. Nachdem Sie sich mit den unten aufgeführten Grundbausteinen beschäftigt haben, verfügen Sie über eine mit Funktionen angefüllte Toolbox, die Sie in Ihr Mixed Reality-Projekt integrieren können.

Das [Mixed Reality-Toolkit für Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal) bietet eine Reihe von Plug-Ins, die entwickelt wurden, um Ihre Entwicklung für Unreal zu beschleunigen. Jedes Plug-In enthält Komponenten, Beispiele und Dokumentation zum Einrichten von immersiven Erlebnissen.

* [UX Tools für Unreal](https://www.unrealengine.com/marketplace/en-US/product/mixed-reality-ux-tools) ist das erste Plug-In, das veröffentlicht wird. Derzeit wird es nur auf HoloLens 2 unterstützt. Das Plug-In enthält C++-Code, Blaupausen und Beispielressourcen für gängige UX-Funktionen für Eingabesimulationen, Handinteraktionen, Oberflächenmagnetismus und vieles mehr.

* [Grafiktools für Unreal](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/) ist ein UE-Spiele-Plug-In mit Code, Blaupausen und Beispielobjekten, die erstellt wurden, um die visuelle Genauigkeit von Mixed Reality-Anwendungen zu verbessern und gleichzeitig Leistungsbudgets einzuhalten.

[!INCLUDE[](../includes/unreal-building-blocks.md)]

> [!NOTE]
> Weitere Informationen finden Sie im **[UX-Tools für Unreal GitHub](https://github.com/microsoft/MixedReality-UXTools-Unreal)** -Repository.

### <a name="3-advanced-features"></a>3. Erweiterte Features

Andere wichtige Features, die in Mixed Reality-Anwendungen eine Rolle spielen, sind ohne Zusatzpakete oder Setup verfügbar. Diese Features können Unreal-Projekten mit oder ohne installiertes MRTK hinzugefügt werden. Nachdem Sie sich mit diesen erweiterten Funktionen beschäftigt haben, werden Sie imstande sein, komplexere Mixed Reality-Apps zu erstellen.

|  Funktion  |  Funktionen  |
| --- | --- |
| [HoloLens-Kamera](unreal-hololens-camera.md) | Erfassen Sie visuelle Inhalte aus Mixed Reality und der realen Welt aus ihrer App, die auf einem HoloLens-Gerät ausgeführt wird |
| [QR-Codes](unreal-qr-codes.md) | Geben Sie QR-Codes mithilfe eines Koordinatensystems an der Position der einzelnen Codes in der realen Welt als Hologramme wieder |
| [WinRT](unreal-winrt.md) | Erstellen Sie eine separate Binärdatei mit WinRT-Code, die vom Buildsystem von Unreal genutzt werden kann |

### <a name="4-streaming-and-deploying-to-a-device"></a>4. Streaming und Bereitstellung auf einem Gerät

Wenn Sie Ihre Anwendung auf einem HoloLens-Gerät testen möchten, während sie sich noch in der Entwicklung befindet, können Sie sie [direkt von Ihrem PC streamen](unreal-streaming.md), indem Sie entweder den Unreal-Editor oder eine verpackte ausführbare Windows-Datei verwenden.

Wenn Sie zum ersten Mal eine Unreal-App für HoloLens 2 bereitstellen, müssen Sie aus dem Epic-Startprogramm [unterstützende Dateien herunterladen](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal). Nachdem Sie diese Dateien installiert haben, können Sie die Bereitstellung entweder über den [Unreal-Editor](unreal-deploying.md) oder über das [Geräteportal](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) durchführen.

### <a name="5-adding-services"></a>5. Hinzufügen von Diensten

An diesem Punkt auf Ihrem Entwicklungsweg suchen Sie vielleicht nach Möglichkeiten zum Hinzufügen von Diensten oder nach Hilfe zur kommerziellen Bereitstellung. Das Integrieren von [Azure Cloud Services](../mixed-reality-cloud-services.md) kann Ihre Projekte auf eine ganz andere Stufe heben. Wir haben für Sie einige Ausgangspunkte zum Erkunden und zum Erweitern Ihrer Mixed Reality-Kenntnisse zusammengetragen.

[!INCLUDE[](../includes/unreal-cloud-services-d365.md)]

### <a name="6-low-code-alternatives"></a>6. Low-Code-Alternativen

[!INCLUDE[](../includes/unreal-low-code.md)]

## <a name="whats-next"></a>Wie geht es weiter?

Die Arbeit eines Entwicklers ist nie getan, insbesondere nicht beim Lernen eines neuen Tools oder SDKs. Die folgenden Abschnitte führen Sie in Gebiete, die jenseits des Materials auf Einstiegsniveau liegen, das Sie bereits durchgearbeitet haben, ergänzt um nützliche Ressourcen, wenn es einmal hakt. Beachten Sie, dass diese Themen und Ressourcen keine bestimmte Reihenfolge aufweisen, tauchen Sie also ruhig ein!

### <a name="debugging"></a>Debuggen

Wenn Sie die Anwendung mit Visual Studio debuggen möchten, während sie auf dem Gerät ausgeführt wird, befolgen Sie diese [Anweisungen](/visualstudio/debugger/debug-installed-app-package#remote).

### <a name="performance"></a>Leistung

Die Entwicklung für Mixed Reality ist mit Leistungsprüfpunkten verbunden, die von der Plattform abhängen. Eine HoloLens 2-App muss mit 60 Frames pro Sekunde ausgeführt werden, um stabile und reaktionsfähige Hologramme zu erhalten. Glücklicherweise stehen [Leistungsempfehlungen](performance-recommendations-for-unreal.md) zur Verfügung, mit denen Sie die Leistung Ihrer Unreal-Anwendungen steigern können.

## <a name="supported-features"></a>Unterstützte Features

| HoloLens 2-Feature | Niedrigste unterstützte Unreal Engine-Version | Unterstützt in OpenXR (4.26+) |
| ----------- | ----------- | ----------- |
| ARM64-Unterstützung | 4.23 | ✔️ |
| Streaming von einem PC | 4.23 | ✔️ |
| Räumliche Abbildung | 4.23 | ✔️ |
| Hand- und Gelenktracking | 4.23 | ✔️ |
| Eyetracking – Blickverfolgung | 4.23 | ✔️ |
| Spracheingabe | 4.23 | ✔️ |
| Raumanker | 4.23 | ✔️ |
| Kamerazugriff | 4.23 | ✔️ |
| QR-Codes | 4.23 | ✔️ |
| Räumliche Audiowiedergabe | 4.23 | ✔️ |
| Zuschauerbildschirmunterstützung für Streaming | 4.24 |
| Planar-LSR über Streaming | 4.24 |
| [Beispiel-Apps](../features-and-samples.md) | 4.24 | ✔️ |
| Mobile Multiansicht: Leistung erreicht 60 FPS | 4.25 | ✔️ |
| Rendering der dritten Kamera | 4.25 | ✔️ |
| Streaming aus einer verpackten Desktop-App | 4.25.1 | ✔️ |
| Azure Spatial Anchors für HoloLens 2 | 4.25 | ✔️ |
| Unterstützung von Mixed Reality UX Tools | 4.25 | ✔️ |
| Dokumentation und Tutorials für Entwickler | 4.25 | ✔️ |
| Systemtastatur | 4.26 | ✔️ |
| HoloLens Media Player-Plug-In | 4.26 | ✔️ |
| Azure Spatial Anchors für iOS und Android | 4.26 |
| Microsoft OpenXR-Plug-In mit den herstellerspezifischen OpenXR-Erweiterungen von Microsoft | 4.26 | ✔️ |
| Streaming von Azure zu HoloLens 2 | 4.26 | ✔️ |
| Compliance des Zertifizierungskits für Windows-Apps für verpackte Apps | 4.26 | ✔️ |
| Unterstützung für den HP Reverb G2-Controller | 4.26 | ✔️ |

> [!div class="nextstepaction"]
> [Installieren der Tools](../install-the-tools.md)

## <a name="see-also"></a>Siehe auch
* <a href="https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html" target="_blank">Unreal-Dokumentation für Streaming und Bereitstellung (Emulator und Gerät)</a>
* <a href="https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html" target="_blank">Unreal-Leistungsrichtlinien für mobile Geräte</a>