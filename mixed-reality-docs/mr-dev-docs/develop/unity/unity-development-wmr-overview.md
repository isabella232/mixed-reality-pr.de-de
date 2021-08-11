---
title: Unity-Bereitstellung für VR
description: Beginnen Sie mit dem Entwickeln von Mixed Reality-Apps in Unity für immersive Headsets für VR und Windows Mixed Reality.
author: hferrone
ms.author: kurtie
ms.date: 12/11/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, Mixed Reality, Entwicklung, Erste Schritte, neues Projekt, Portieren, Funktion, Kamera, Simulation, Emulation, Dokumentation, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, was ist Virtual Reality, was ist Augmented Reality, MRTK, Mixed Reality Toolkit, Spracheingabe, ausrichtbare Kamera, Emulator, Azure, Tutorials
ms.openlocfilehash: 74ac1825d8b94ba65075ef96244759ec0c8dcf1891556e0a1f36f100b9615221
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211688"
---
# <a name="unity-development-for-vr-and-windows-mixed-reality"></a>Unity-Entwicklung für VR und Windows Mixed Reality

![Unity-Bannerlogo](../images/unity_logo_banner.png)

Wenn Sie mit Unity noch nicht vertraut sind, empfehlen wir Ihnen, sich mit den [Tutorials](https://unity3d.com/learn/tutorials) für Einsteiger auf der Unity-Lernplattform zu befassen, bevor Sie fortfahren. Außerdem ist es eine gute Idee, die [Unity Mixed Reality-Foren](https://forum.unity3d.com/forums/hololens.102/) aufzusuchen, um sich in der Onlinecommunity zu engagieren, die Mixed Reality-Apps erstellt. Sie können schlicht nicht wissen, welche tollen Medienobjekte oder Lösungen Sie abseits ausgetretener Pfade finden. Wenn Sie bereit sind, mit dem MRTK loszulegen, gehen Sie zu den Prüfpunkten für die Entwicklung unten!

> [!IMPORTANT]
> Sehen Sie sich unsere **[Portierungsleitfäden](../porting-apps/porting-overview.md)** an, wenn Sie ein vorhandenes Unity-Projekt auf ein immersives Windows Mixed Reality-Headset portieren möchten. 

## <a name="development-checkpoints"></a>Prüfpunkte für die Entwicklung

Nutzen Sie die folgenden Prüfpunkte, um Ihre Unity-Spiele und Anwendungen in eine Mixed Reality-Welt einzubringen.

### <a name="1-getting-started"></a>1. Erste Schritte

Es gibt eine kleine Gruppe von Unity-Einstellungen, die Sie für die Entwicklung für Windows Mixed Reality und VR manuell ändern müssen. Diese gliedern sich in zwei Kategorien: projektbezogene und szenenbezogene. Am Ende dieses Abschnitts verfügen Sie über die Tools und Projekteinstellungen, um mit dem Erstellen Ihrer eigenen Apps zu beginnen.

|  Prüfpunkt  |  Ergebnis  |
| --- | --- |
| [Installieren der neuesten Tools](../install-the-tools.md) | Laden Sie das aktuellste Unreal-Paket herunter, installieren Sie es, und richten Sie Ihr Projekt für Mixed Reality ein |
| [Konfigurieren Ihres Projekts für VR- und Windows Mixed Reality-Headsets](./xr-project-setup.md?tabs=openxr) | Erfahren Sie, wie Sie Anwendungen erstellen, die digitale Inhalte auf holografischen und VR-Anzeigegeräten darstellen |

> [!IMPORTANT]
> Weitere Informationen zum Einrichten Ihrer Projekte finden Sie in unserem [Konfigurationshandbuch](choosing-unity-version.md) für Unity-Projekte.

### <a name="2-core-building-blocks"></a>2. Grundbausteine

Nachdem Sie ein neues immersives Projekt begonnen haben, benötigen Sie einige Grundbausteine zum Entwickeln immersiver Apps. Alle Hauptbausteine für Mixed Reality-Anwendungen werden in einer Weise verfügbar gemacht, die mit anderen Unity-APIs konsistent ist. Sie benötigen sie möglicherweise nicht alle auf einmal, aber wir empfehlen Ihnen, sich frühzeitig mit ihnen vertraut zu machen. Nachdem Sie sich mit den unten aufgeführten Grundbausteinen beschäftigt haben, verfügen Sie über eine mit Funktionen angefüllte Toolbox, die Sie in ein VR-Projekt integrieren können.

|  Funktion  |  Funktionen  |
| --- | --- |
| [Kamera](../unity/camera-in-unity.md) | Optimieren Sie die visuelle Qualität und die Stabilität von Hologrammen in Ihren Mixed Reality-Apps umfassend |
| [Sperren der Welt und Raumanker](spatial-anchors-in-unity.md) | Löst Stabilisierungsprobleme, implementiert eine Kameraanpassung und integriert eine stabile Koordinatensystemlösung || [Motion-Controller](../unity/motion-controllers-in-unity.md) | Fügen Sie Ihren Mixed Reality-Apps räumliche Aktionen hinzu |
| [Gesten](../unity/gestures-in-unity.md) | Verwenden Sie Handgesten als Eingabe in ihren Mixed Reality-Umgebungen |
| [Raumklang](../unity/spatial-sound-in-unity.md) | Verbessern Sie Ihre Apps mit immersivem 3D-Audio |
| [Text](../unity/text-in-unity.md) | Erhalten Sie scharfen Text in hoher Qualität mit in Größe und Qualität beherrschbarem Rendering |
| [Spracheingabe](../unity/voice-input-in-unity.md) | Erfassen Sie gesprochene Schlüsselwörter, Ausdrücke und Diktate von Benutzern|

### <a name="3-advanced-features"></a>3. Erweiterte Features

Andere wichtige Features, die in immersiven Anwendungen eine Rolle spielen, sind über Unity-APIs ohne Zusatzpakete oder Setup verfügbar. Nachdem Sie sich mit den erweiterten Funktionen beschäftigt haben, die Unity bietet, werden Sie imstande sein, tiefere, komplexe VR-Apps zu erstellen.

|  Funktion  |  Funktionen  |
| --- | --- |
| [Verlust der Nachverfolgung](tracking-loss-in-unity.md) | Behandeln Sie Szenarien, in denen Ihr Gerät sich im Weltbereich der Anwendung nicht finden kann |
| [Tastatureingabe](keyboard-input-in-unity.md) | Rufen Sie Eingaben von realen und Mixed Reality-Tastaturen in Ihren Apps ab |

### <a name="4-deploying-to-a-device-or-emulator"></a>4. Bereitstellen auf einem Gerät oder in einem Emulator

Sobald Sie Ihr Unity-Holografieprojekt bis zur Testreife gebracht haben, besteht der nächste Schritt im Exportieren und Erstellen einer Unity Visual Studio-Projektmappe. Mithilfe dieser VS-Projektmappe können Sie Ihre Anwendung auf realen oder simulierten Geräten ausführen. Am Ende dieses Abschnitts können Sie die Anwendung auf einem Gerät oder Emulator bereitstellen, das bzw. der Ihren Entwicklungsanforderungen entspricht.

* [Immersives Headset für Windows Mixed Reality](../platform-capabilities-and-apis/using-visual-studio.md)
* [Simulator für immersives Headset für Windows Mixed Reality](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="whats-next"></a>Wie geht es weiter?

Die Arbeit eines Entwicklers ist nie getan, insbesondere beim Lernen eines neuen Tools oder SDKs. Die folgenden Abschnitte führen Sie in Gebiete, die jenseits des Materials auf Einstiegsniveau liegen, das Sie bereits durchgearbeitet haben, ergänzt um nützliche Ressourcen, wenn es einmal hakt. Beachten Sie, dass diese Themen und Ressourcen keine bestimmte Reihenfolge aufweisen, tauchen Sie also ruhig ein!

### <a name="porting"></a>Portieren

Wenn Sie über vorhandene Apps verfügen, die Sie portieren möchten, sind die unten aufgeführten Artikel Ihr nächster Anlaufpunkt:

* [Portieren von VR-Apps zu Windows Mixed Reality](../porting-apps/porting-guides.md?tabs=project)
* [Aktualisieren von SteamVR-Apps für Windows Mixed Reality](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)

### <a name="additional-resources"></a>Zusätzliche Ressourcen

Bevor Sie sich auf eigene Faust in die Welt der Mixed Reality aufmachen, sollten Sie sich die unten aufgeführte zusätzliche Dokumentation ansehen. 

* [VR-Handbuch für Enthusiasten](/windows/mixed-reality/enthusiast-guide/vr-journey)
* [Unity Asset Store](https://assetstore.unity.com)

## <a name="see-also"></a>Weitere Informationen 

* [Empfohlene Einstellungen für Unity](recommended-settings-for-unity.md)
* [Leistungsempfehlungen für Unity](performance-recommendations-for-unity.md)
* [Exportieren und Erstellen einer Unity-Projektmappe für Visual Studio](exporting-and-building-a-unity-visual-studio-solution.md)
* [Bewährte Methoden für das Arbeiten mit Unity und Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)