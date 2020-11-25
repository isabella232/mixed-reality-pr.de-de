---
title: Unreal-Entwicklung – Übersicht
description: Übersicht über die Mixed Reality-Entwicklung mit der Unreal Engine 4
author: hferrone
ms.author: v-hferrone
ms.date: 08/04/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Streaming, Remoting, Mixed Reality, Entwicklung, erste Schritte, Features, neues Projekt, Emulator, Dokumentation, Leitfäden, Features, Hologramme, Spieleentwicklung, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: b810ad7500f8bb2a70ef18ad29fb32df8801a2de
ms.sourcegitcommit: 2759aba06e643d70004023b105ed26b33ce3dbfa
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2020
ms.locfileid: "94810446"
---
# <a name="unreal-development-overview"></a>Unreal-Entwicklung – Übersicht

![Unreal-Bannerlogo](../images/unreal_logo_banner.png)

Die ersten Schritte mit <a href="https://docs.microsoft.com/windows/mixed-reality" target="_blank" title="Mixed Reality-Dokumentation"> Mixed Reality-Anwendungen</a> sind eine Herausforderung. Neue Konzepte, Plattformen und neuartige Hardware können sich als Hürden erweisen. Wenn Sie jedoch Unreal-Entwickler sind, haben Sie Glück. Unterstützung für <a href="https://www.microsoft.com/windows/windows-mixed-reality" target="_blank" title="Windows Mixed Reality-Dokumentation">Windows Mixed Reality</a> (VR) und <a href="https://www.microsoft.com/hololens/hardware" target="_blank" title="HoloLens 2-Dokumentation">HoloLens 2</a> (AR) ist jetzt in der aktuellen <a href="https://docs.unrealengine.com/Support/Builds/ReleaseNotes/4_25/index.html" target="_blank" title="Versionshinweisen zu Unreal Engine 4.25">Release</a> von Unreal Engine enthalten. Das Update enthält:
* Unterstützung für das Mixed Reality UX-Plug-In
* OpenXR-Unterstützung
* App-Remoting über eine Desktop-App
* Bessere Leistung
* Mixed-Reality-Aufnahme
* Anfängliche Unterstützung für Azure Spatial Anchors

Wenn Sie noch nicht mit der Unreal-Entwicklung vertraut sind, sollten Sie sich zunächst etwas einarbeiten. Sehen Sie sich die <a href="https://docs.unrealengine.com/GettingStarted/index.html" target="_blank">Tutorialreihe</a> zu Unreal an, um einen Einstieg zu finden, und nutzen Sie Ressourcen und Support im Unreal-<a href="https://www.unrealengine.com/marketplace/store" target="_blank">Marketplace</a> und den Mixed Reality-<a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">Foren</a>. Dabei handelt es sich um Links zur Community von Entwicklern und Problemlösern auf dem Gebiet der Mixed Reality.

> [!IMPORTANT]
> Werfen Sie einen Blick auf unsere **[Portierungsleitfäden](unreal-reverb-g2-controllers.md)** , wenn Sie ein vorhandenes Unreal-Projekt auf immersiven Headsets wie dem Reverb G2 bereitstellen möchten.

## <a name="development-checkpoints"></a>Prüfpunkte für die Entwicklung

Nutzen Sie die folgenden Prüfpunkte, um Ihre Unreal-Spiele und Anwendungen in eine Mixed Reality-Welt einzubringen. Wenn Sie sich noch nicht mit der [Beispielanwendung zum Entwerfen von Hologrammen](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd) befasst haben, empfehlen wir Ihnen, sie herunterzuladen und zu verwenden, um sich mit den Grundlagen von Mixed Reality UX vertraut zu machen.

### <a name="1-getting-started"></a>1. Erste Schritte

Das [Mixed Reality Toolkit für Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal) bietet eine Reihe von Komponenten, die entwickelt wurden, um Ihre Entwicklung für Unreal zu beschleunigen. Jede Komponente enthält Plug-Ins, Beispiele und Dokumentation zum Einrichten von immersiven Erlebnissen.

* [UX Tools für Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal) ist die erste Komponente, die veröffentlicht wird. Derzeit wird sie nur auf HoloLens 2 unterstützt. Das Komponenten-Plug-In beinhaltet Code, Blaupausen und Beispiel-Medienobjekte gängiger UX-Features für die Simulation von Eingaben sowie Handinteraktionsaktoren, drückbare Schaltflächenkomponenten und Komponenten mit Nachverfolgeverhalten.

Am Ende dieses Abschnitts haben Sie ein grundlegendes Verständnis des Mixed Reality Toolkits, besitzen eine ordnungsgemäß konfigurierte Entwicklungsumgebung für Mixed Reality-Apps und verfügen über ein funktionierendes MRTK-Projekt in Unreal.

|  Prüfpunkt  |  Ergebnis  |
| --- | --- |
| [Installieren der neuesten Tools](../install-the-tools.md) | Laden Sie die neueste Version der Unreal Engine herunter, installieren Sie sie, und richten Sie Ihr Projekt für Mixed Reality ein |
| [Hololens 2-Tutorialreihe](tutorials/unreal-uxt-ch1.md) | Vertiefen Sie sich in die MRTK-Tutorials für HoloLens 2-Hardware auf Einstiegsebene |

### <a name="2-core-building-blocks"></a>2. Grundbausteine

Es gibt mehrere wichtige Features der Mixed Reality-Entwicklung, die in unserer Tutorialreihe nicht behandelt werden. Diese Bausteine stehen als eigenständige Features und über das Mixed Reality Toolkit zur Verfügung. Sie benötigen sie möglicherweise nicht alle auf einmal, aber wir empfehlen Ihnen, sich frühzeitig mit ihnen vertraut zu machen. Nachdem Sie sich mit den unten aufgeführten Grundbausteinen beschäftigt haben, verfügen Sie über eine mit Funktionen angefüllte Toolbox, die Sie in Ihr Mixed Reality-Projekt integrieren können.

[!INCLUDE[](../includes/unreal-building-blocks.md)]

> [!NOTE]
> Weitere Informationen finden Sie im **[UX-Tools für Unreal GitHub](https://github.com/microsoft/MixedReality-UXTools-Unreal)** -Repository.

### <a name="3-platform-capabilities-and-apis"></a>3. Plattformfunktionen und APIs

Andere wichtige Features, die in Mixed Reality-Anwendungen eine Rolle spielen, sind ohne Zusatzpakete oder Setup verfügbar. Diese Features können Unreal-Projekten mit oder ohne installiertes MRTK hinzugefügt werden. Nachdem Sie sich mit diesen erweiterten Funktionen beschäftigt haben, werden Sie imstande sein, komplexere Mixed Reality-Apps zu erstellen.

|  Funktion  |  Funktionen  |
| --- | --- |
| [HoloLens-Kamera](unreal-hololens-camera.md) | Erfassen Sie visuelle Inhalte aus Mixed Reality und der realen Welt aus ihrer App, die auf einem HoloLens-Gerät ausgeführt wird |
| [QR-Codes](unreal-qr-codes.md) | Geben Sie QR-Codes mithilfe eines Koordinatensystems an der Position der einzelnen Codes in der realen Welt als Hologramme wieder |
| [WinRT](unreal-winrt.md) | Erstellen Sie eine separate Binärdatei mit WinRT-Code, die vom Buildsystem von Unreal genutzt werden kann |

### <a name="4-deploying-to-a-device"></a>4. Bereitstellung auf einem Gerät

Wenn Sie zum ersten Mal eine Unreal-App für HoloLens erstellen oder bereitstellen, müssen Sie aus dem Epic-Startprogramm [unterstützende Dateien herunterladen](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal). Nachdem Sie diese Dateien installiert haben, können Sie die Bereitstellung entweder über den [Unreal-Editor](unreal-deploying.md) oder über das [Geräteportal](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) durchführen.

### <a name="5-adding-services"></a>5. Hinzufügen von Diensten

An diesem Punkt auf Ihrem Entwicklungsweg suchen Sie vielleicht nach Möglichkeiten zum Hinzufügen von Diensten oder nach Hilfe zur kommerziellen Bereitstellung. Das Integrieren von [Azure Cloud Services](../mixed-reality-cloud-services.md) und Features von Dynamics 365 kann Ihre Projekte auf eine ganz andere Stufe heben. Wir haben für Sie einige Ausgangspunkte zum Erkunden und zum Erweitern Ihrer Mixed Reality-Kenntnisse zusammengetragen.

[!INCLUDE[](../includes/unreal-cloud-services-d365.md)]

## <a name="whats-next"></a>Wie geht es weiter?

Die Arbeit eines Entwicklers ist nie getan, insbesondere beim Lernen eines neuen Tools oder SDKs. Die folgenden Abschnitte führen Sie in Gebiete, die jenseits des Materials auf Einstiegsniveau liegen, das Sie bereits durchgearbeitet haben, ergänzt um nützliche Ressourcen, wenn es einmal hakt. Beachten Sie, dass diese Themen und Ressourcen keine bestimmte Reihenfolge aufweisen, tauchen Sie also ruhig ein!

### <a name="streaming--debugging"></a>Streaming & Debuggen

Wenn Sie Ihre Anwendung auf einem HoloLens-Gerät testen möchten, während sie sich noch in der Entwicklung befindet, können Sie sie [direkt von Ihrem PC streamen](unreal-streaming.md), indem Sie entweder den Unreal-Editor oder eine verpackte ausführbare Windows-Datei verwenden.

Wenn Sie die Anwendung mit Visual Studio debuggen möchten, befolgen Sie diese [Anweisungen](https://docs.microsoft.com/visualstudio/debugger/debug-installed-app-package#remote).

### <a name="performance"></a>Leistung

Die Entwicklung für Mixed Reality ist mit Leistungsprüfpunkten verbunden, die von der Plattform abhängen. Eine HoloLens 2-App muss mit 60 Frames pro Sekunde ausgeführt werden, um stabile und reaktionsfähige Hologramme zu erhalten. Glücklicherweise stehen [Leistungsempfehlungen](performance-recommendations-for-unreal.md) zur Verfügung, damit Sie das Ziel mit Ihren Unreal-Anwendungen erfolgreich erreichen.

## <a name="supported-features"></a>Unterstützte Features

| HoloLens 2-Feature | Niedrigste unterstützte Unreal Engine-Version |
| ----------- | ----------- |
| ARM64-Unterstützung | 4.23 |
| Streaming von einem PC | 4.23 |
| Räumliche Abbildung | 4.23 |
| Hand- und Gelenktracking | 4.23 |
| Eyetracking – Blickverfolgung | 4.23 |
| Spracheingabe | 4.23 |
| Raumanker | 4.23 |
| Kamerazugriff | 4.23 |
| QR-Codes | 4.23 |
| Räumliche Audiowiedergabe | 4.23 |
| Zuschauerbildschirmunterstützung für Streaming | 4.24 |
| Planar-LSR über Streaming | 4.24 |
| Beispiel-Apps ([HoloLens2Example](https://github.com/microsoft/MixedReality-Unreal-Samples) und [Mission AR](https://docs.unrealengine.com/Resources/Showcases/MissionAR/index.html)) | 4.24 |
| Mobile Multiansicht: Leistung erreicht 60 FPS | 4.25 |
| Rendering der dritten Kamera | 4.25 |
| Streaming aus einer verpackten Desktop-App | 4.25.1 |
| Azure Spatial Anchors für HoloLens 2 (Beta) | 4.25 |
| OpenXR-Unterstützung (Beta) | 4.25 |
| Unterstützung von UX-Tools (0.8) | 4.25 |
| Dokumentation und Tutorials für Entwickler | 4.25 |

> [!div class="nextstepaction"]
> [Installieren der Tools](../install-the-tools.md)

## <a name="see-also"></a>Siehe auch
* <a href="https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html" target="_blank">Unreal-Dokumentation für Streaming und Bereitstellung (Emulator und Gerät)</a>
* <a href="https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html" target="_blank">Unreal-Leistungsrichtlinien für mobile Geräte</a>
