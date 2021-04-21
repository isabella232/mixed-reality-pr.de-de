---
title: Unity-Entwicklung für HoloLens
description: Steigen Sie in die Entwicklung von Mixed Reality-Apps in Unity und HoloLens mit unserer zusammengestellten Journey entlang von Prüfpunkten ein.
author: hferrone
ms.author: kurtie
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, Mixed Reality, Entwicklung, Erste Schritte, neues Projekt, Portieren, Funktion, Kamera, Simulation, Emulation, Dokumentation, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, was ist Virtual Reality, was ist Augmented Reality, MRTK, Mixed Reality Toolkit, räumliche Abbildung, Spracheingabe, ausrichtbare Kamera, Emulator, Azure, Tutorials
ms.openlocfilehash: ba68c3d74f58fc43af3de039e5eba1712d195cc0
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528738"
---
# <a name="unity-development-for-hololens"></a>Unity-Entwicklung für HoloLens

![Unity-Bannerlogo](../images/unity_logo_banner.png)

Den schnellsten Weg zum Entwickeln einer HoloLens-[Mixed Reality-App](../../design/app-views.md) in [Unity](https://unity.com) bietet das Mixed Reality Toolkit. Wenn Sie mit Unity noch nicht vertraut sind, empfehlen wir Ihnen, sich mit den [Tutorials](https://unity3d.com/learn/tutorials) für Einsteiger auf der Unity-Lernplattform zu befassen, bevor Sie fortfahren. Außerdem ist es eine gute Idee, den umfassenden [Asset Store](https://assetstore.unity.com) und die [Unity Mixed Reality-Foren](https://forum.unity3d.com/forums/hololens.102/) zu besuchen, um mit der Onlinecommunity in Kontakt zu kommen, die Mixed Reality-Apps entwickelt. Sie können schlicht nicht wissen, welche tollen Medienobjekte oder Lösungen Sie abseits ausgetretener Pfade finden. Wenn Sie bereit sind, mit dem MRTK loszulegen, gehen Sie zu den Prüfpunkten für die Entwicklung unten!

> [!IMPORTANT]
> Sehen Sie sich unsere **[Portierungsleitfäden](../porting-apps/porting-overview.md)** an, wenn Sie ein vorhandenes Unity-Projekt besitzen, das Sie auf HoloLens 2 bringen möchten. Wir haben Leitfäden für Projekte, die HTK, MRTK v1 oder SteamVR verwenden.

## <a name="development-checkpoints"></a>Prüfpunkte für die Entwicklung

Nutzen Sie die folgenden Prüfpunkte, um Ihre Unity-Spiele und Anwendungen in eine Mixed Reality-Welt einzubringen. Wenn Sie sich noch nicht mit der [Beispielanwendung zum Entwerfen von Hologrammen](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd) befasst haben, empfehlen wir Ihnen, sie herunterzuladen und zu verwenden, um sich mit den Grundlagen von Mixed Reality UX vertraut zu machen.

## <a name="1-getting-started"></a>1. Erste Schritte

Die einfachste Möglichkeit zum Entwickeln in Unity stellt das Mixed Reality Toolkit dar. MRTK hilft Ihnen, ein Projekt für Mixed Reality automatisch einzurichten und bietet eine Reihe von Funktionen zur Beschleunigung Ihres Entwicklungsprozesses. Am Ende dieses Abschnitts haben Sie ein grundlegendes Verständnis des Mixed Reality Toolkits, besitzen eine ordnungsgemäß konfigurierte Entwicklungsumgebung für Mixed Reality-Apps und verfügen über ein funktionierendes MRTK-Projekt in Unity, das Sie selbst erstellt haben.

|  Prüfpunkt  |  Ergebnis  |
| --- | --- |
| [Einführung des Mixed Reality-Toolkits](mrtk-getting-started.md) | Beginnen Sie Ihren Weg, indem Sie sich mit dem Mixed Reality Toolkit und den Optionen vertraut machen, die es zu bieten hat |
| [Laden Sie das Mixed Reality-Featuretool herunter](welcome-to-mr-feature-tool.md). | Ein neues Entwicklertool zum Entdecken, Aktualisieren und Hinzufügen von Mixed Reality-Featurepaketen zu ihren Unity-Projekten |
| [Einrichten Ihrer Entwicklerumgebung](../install-the-tools.md) | Laden Sie das aktuellste Unreal-Paket herunter, installieren Sie es, und richten Sie Ihr Projekt für Mixed Reality ein |
| [Abschließen der HoloLens 2-Tutorialreihe](tutorials/mr-learning-base-01.md) | Vertiefen Sie sich in die MRTK-Tutorials für HoloLens 2-Hardware auf Einstiegsebene |

> [!IMPORTANT]
> Wenn Sie ein neues Unity-Projekt erstellen möchten, ohne das Mixed Reality Toolkit zu importieren, müssen einige Unity-Einstellungen manuell geändert werden, um für Windows Mixed Reality zu entwickeln. Weitere Informationen finden Sie in unserem [Konfigurationsleitfaden](choosing-unity-version.md).

> [!NOTE]
> Nachdem Sie MRTK in Ihrem Projekt eingerichtet haben, erscheinen umgehend standardmäßige Unity-Spieleobjekte wie die Kamera für ein sitzendes Aktivitätserlebnis. Anweisungen zum Ändern des Erlebnismaßstabs für Ihre Anwendung finden Sie auf der Seite zu [Koordinatensystemen](coordinate-systems-in-unity.md).

## <a name="2-core-building-blocks"></a>2. Grundbausteine

Alle Hauptbausteine für Mixed Reality-Anwendungen werden in einer Weise verfügbar gemacht, die mit anderen Unity-APIs konsistent ist. Diese Bausteine stehen als eigenständige Features und über das Mixed Reality Toolkit zur Verfügung. Sie benötigen sie möglicherweise nicht alle auf einmal, aber wir empfehlen Ihnen, sich frühzeitig mit ihnen vertraut zu machen. Nachdem Sie sich mit den unten aufgeführten Grundbausteinen beschäftigt haben, verfügen Sie über eine mit Funktionen angefüllte Toolbox, die Sie eigenständig oder mithilfe von MRTK in ein Mixed Reality-Projekt integrieren können.

|  Funktion  |  Funktionen  |
| --- | --- |
| [Kamera](../unity/camera-in-unity.md) | Optimieren Sie die visuelle Qualität und die Stabilität von Hologrammen in Ihren Mixed Reality-Apps umfassend |
| [Sperren der Welt und Raumanker](spatial-anchors-in-unity.md) | Löst Stabilisierungsprobleme, implementiert eine Kameraanpassung und integriert eine stabile Koordinatensystemlösung |
| [Gemeinsame Erfahrung](shared-experiences-in-unity.md) | Zeigen Sie mithilfe freigegebener Raumanker kollektiv das gleiche Hologramm an, und interagieren Sie gemeinsam an einem festen Punkt im Raum mit ihm |
| [Anvisieren](../unity/gaze-in-unity.md) | Ermöglichen Sie Benutzern das Anzielen von Hologrammen durch Anblicken |
| [Motion-Controller](../unity/motion-controllers-in-unity.md) | Fügen Sie Ihren Mixed Reality-Apps räumliche Aktionen hinzu |
| [Gesten](../unity/gestures-in-unity.md) | Verwenden Sie Handgesten als Eingabe in ihren Mixed Reality-Umgebungen |
| [Hand- und Eye-Tracking](../unity/hand-eye-in-unity.md) | Integrieren Sie artikulierte Eingaben des Hand- und Eyetrackings in Ihre Benutzererfahrung |
| [Räumliche Abbildung](../unity/spatial-mapping-in-unity.md) | Bilden Sie Ihren physischen Raum mit einem überlagerten virtuellen Gittermodell ab, um die Begrenzungen Ihrer Umgebung zu kennzeichnen |
| [Raumklang](../unity/spatial-sound-in-unity.md) | Verbessern Sie Ihre Apps mit immersivem 3D-Audio |
| [Text](../unity/text-in-unity.md) | Erhalten Sie scharfen Text in hoher Qualität mit in Größe und Qualität beherrschbarem Rendering |
| [Spracheingabe](../unity/voice-input-in-unity.md) | Erfassen Sie gesprochene Schlüsselwörter, Ausdrücke und Diktate von Benutzern|

## <a name="3-advanced-features"></a>3. Erweiterte Features

Andere wichtige Features, die in Mixed Reality-Anwendungen eine Rolle spielen, sind über Unity-APIs ohne Zusatzpakete oder Setup verfügbar. Diese Features können Unity-Projekten mit oder ohne installiertes MRTK hinzugefügt werden. Nachdem Sie sich mit den erweiterten Funktionen beschäftigt haben, die Unity bietet, werden Sie imstande sein, tiefere, komplexe Mixed Reality-Apps zu erstellen.

|  Funktion  |  Funktionen  |
| --- | --- |
| [Foto-/Videokamera](locatable-camera-in-unity.md) | Erfassen Sie Foto- und Videoinhalte in Ihrer Mixed Reality-Anwendung |
| [Fokuspunkt](focus-point-in-unity.md) | Geben Sie HoloLens einen Hinweis zum Ausführen der besten Stabilisierung für die aktuell angezeigten Hologramme |
| [Verlust der Nachverfolgung](tracking-loss-in-unity.md) | Behandeln Sie Szenarien, in denen Ihr Gerät sich im Weltbereich der Anwendung nicht finden kann |
| [Tastatureingabe](keyboard-input-in-unity.md) | Rufen Sie Eingaben von realen und Mixed Reality-Tastaturen in Ihren Apps ab |

## <a name="4-deploying-to-a-device-or-emulator"></a>4. Bereitstellen auf einem Gerät oder in einem Emulator

Sobald Sie Ihr Unity-Holografieprojekt bis zur Testreife gebracht haben, besteht der nächste Schritt im Exportieren und Erstellen einer Unity Visual Studio-Projektmappe. Mit dieser VS-Projektmappe können Sie Ihre Anwendung auf eine von drei Weisen ausführen und dazu ein reales oder ein simuliertes Gerät verwenden. Am Ende dieses Abschnitts können Sie die Anwendung auf jedem Gerät oder Emulator bereitstellen, das bzw. der Ihren Entwicklungsanforderungen entspricht.

* [Immersives Headset für HoloLens oder Windows Mixed Reality](../platform-capabilities-and-apis/using-visual-studio.md)
* [HoloLens-Emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
* [Simulator für immersives Headset für Windows Mixed Reality](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="5-adding-services"></a>5. Hinzufügen von Diensten

An diesem Punkt auf Ihrem Entwicklungsweg suchen Sie vielleicht nach Möglichkeiten zum Hinzufügen von Diensten oder nach Hilfe zur kommerziellen Bereitstellung. Das Integrieren von [Azure Cloud Services](../mixed-reality-cloud-services.md) und Features von Dynamics 365 kann Ihre Projekte auf eine ganz andere Stufe heben. Wir haben für Sie einige Ausgangspunkte zum Erkunden und zum Erweitern Ihrer Mixed Reality-Kenntnisse zusammengetragen.

[!INCLUDE[](../includes/unity-cloud-services-d365.md)]

Außerdem bieten wir eine [umfassende Liste der Supportdokumentation für zusätzliche Azure-Dienste](../mixed-reality-cloud-services.md#standalone-unity-services), die Sie Ihren Unity-Projekten auf Self-Service-Basis hinzufügen können.

## <a name="whats-next"></a>Wie geht es weiter?

Die Arbeit eines Entwicklers ist nie getan, insbesondere beim Lernen eines neuen Tools oder SDKs. Die folgenden Abschnitte führen Sie in Gebiete, die jenseits des Materials auf Einstiegsniveau liegen, das Sie bereits durchgearbeitet haben, ergänzt um nützliche Ressourcen, wenn es einmal hakt. Beachten Sie, dass diese Themen und Ressourcen keine bestimmte Reihenfolge aufweisen, tauchen Sie also ruhig ein!

### <a name="porting"></a>Portieren

Wenn Sie über vorhandene Apps verfügen, die Sie portieren möchten, sind die unten aufgeführten Artikel Ihr nächster Halt:

* [HoloToolkit/MRTK zu MRTK v2](../porting-apps/porting-hl1-hl2.md)
* [Leitfaden zum Portieren von immersiven Apps](../porting-apps/porting-guides.md)
* [Portierungsleitfaden importieren](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

### <a name="tutorials"></a>Tutorials

Wenn Sie nach Möglichkeiten suchen, Ihren Anwendungen bestimmte Mixed Reality-Features hinzuzufügen, haben wir eine Reihe zusammengestellter Tutorials zu bieten, die Sie von Anfang bis Ende durch den Prozess leiten. Unsere beliebtesten HoloLens 2- und HoloLens-Inhalte (1. Generation) sind unten aufgelistet, aber Sie finden die ganze Sammlung auf der Übersichtsseite der Tutorials.

[!INCLUDE[](../includes/unity-tutorials.md)]

### <a name="additional-resources"></a>Zusätzliche Ressourcen

Bevor Sie sich auf eigene Faust in die Welt der Mixed Reality aufmachen, sollten Sie sich die unten aufgeführte MRTK-bezogene Dokumentation ansehen. Diese Artikel stellen hervorragende Ausgangspunkte dafür da, die Funktion von MRTK im Detail zu verstehen, und geben Ihnen Einblick in die Möglichkeiten, die Leistung Ihrer App zu steigern.

|  Thema  |  Beschreibung  |
| --- | --- |
| [MRTK-Architektur – Übersicht](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/architecture/overview) | Erwerben Sie ein tieferes Verständnis der Funktionsweise des MRTK SDKs in Ihren Projekten |
| [Einstellungen und Leistung](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started) | Erstellen Sie Profile für Ihre App, aktualisieren Sie Ihre Unity-Einstellungen, und erzielen Sie die bestmögliche Hologrammstabilisierung |
| [Erste Schritte mit MRTK + XR](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk) | Stellen Sie auf die alternative XR-Pipeline von Unity um |

### <a name="unity-resources"></a>Unity-Ressourcen

Über diese Dokumentation hinaus, die auf docs.microsoft.com verfügbar ist, installiert Unity Dokumentation für Windows Mixed Reality-Funktionen zusammen mit dem Unity-Editor. Die von Unity bereitgestellte Dokumentation umfasst zwei separate Abschnitte.

|  Resource  |  Beschreibung  |
| --- | --- |
| [Skriptreferenz](https://docs.unity3d.com/ScriptReference/) | Dieser Abschnitt der Dokumentation enthält Details zur Skript-API von Unity und ist online aus dem Unity-Editor zugänglich, indem Sie auf **Hilfe > Skriptreferenz** klicken |
| [Manuell](https://docs.unity3d.com/Manual/index.html) | Dieses Handbuch soll Sie dabei unterstützen, die Verwendung von Unity zu erlernen – von einfachen bis zu erweiterten Techniken – und ist online oder über den Unity-Editor zugänglich, indem Sie auf **Hilfe > Handbuch** klicken. |

> [!div class="nextstepaction"]
> [Erkunden des MRTK](mrtk-getting-started.md)

## <a name="have-feedback"></a>Feedback?

Sie finden uns in den [Unity-Foren](https://aka.ms/unityforums) über den Tag **Microsoft** und eine Kombination der folgenden Tags. Damit helfen Sie uns, zu verstehen, für welches Plug-in Sie Feedback bereitstellen:

* HoloLens 2 
* Windows Mixed Reality
* OpenXR
* XRSDK
* Legacy-XR 

## <a name="see-also"></a>Siehe auch

* [Mixed Reality Toolkit v2](mrtk-getting-started.md)
* [MR-Grundlagen 100: Erste Schritte mit Unity](tutorials/holograms-100.md)
* [Empfohlene Einstellungen für Unity](recommended-settings-for-unity.md)
* [Leistungsempfehlungen für Unity](performance-recommendations-for-unity.md)
* [Exportieren und Erstellen einer Unity-Projektmappe für Visual Studio](exporting-and-building-a-unity-visual-studio-solution.md)
* [Verwenden des Windows-Namespace mit Unity-Apps für HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [Bewährte Methoden für das Arbeiten mit Unity und Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)
* [Unity-Wiedergabemodus](unity-play-mode.md)
* [Portierungsleitfäden](../porting-apps/porting-guides.md)