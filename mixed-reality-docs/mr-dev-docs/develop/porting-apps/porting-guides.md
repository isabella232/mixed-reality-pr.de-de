---
title: Portierungsleitfäden
description: Eine Schritt-für-Schritt-Anleitung, in der erläutert wird, wie Sie eine vorhandene immersive Anwendung in Windows Mixed Reality portieren.
author: JBrentJ
ms.author: alexturn
ms.date: 07/07/2020
ms.topic: article
keywords: Port, Unity, Unreal, Middleware, Engine, UWP, Win32, Porting, hololens 1. gen, Mixed Reality-Headset, Windows Mixed Reality-Headset, Migration, Windows 10, Eingabe Zuordnung,
ms.openlocfilehash: 18129151b1e3d11f9e9c7bb3c3420c23b5fd1dd0
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677729"
---
# <a name="porting-guides"></a>Portierungsleitfäden

Windows 10 bietet direkte Unterstützung für immersive und holografische Headsets. Wenn Sie Inhalte für andere Geräte erstellt haben, wie z. b. den Oculus-oder den HTC-Vive, haben diese Abhängigkeiten von Bibliotheken, die über der Plattform-API des Betriebssystems vorhanden sind. Das Bereitstellen vorhandener Win32 Unity-VR-apps in Windows Mixed Reality umfasst die Neuausrichtung der Verwendung Hersteller spezifischer VR-sdgs auf die plattformübergreifenden VR-APIs von Unity.

## <a name="porting-overview"></a>Übersicht über das Portieren

Auf hoher Ebene sind die folgenden Schritte zum Portieren vorhandener Inhalte beteiligt:
1. **Stellen Sie sicher, dass auf Ihrem PC das Windows 10 Fall Creators Update (16299) ausgeführt wird.** Wir empfehlen Ihnen nicht mehr, vorschaubuilds aus dem Insider-Ahead-Ring zu erhalten, da diese Builds für die Entwicklung mit gemischter Realität nicht am stabilsten sind.
2. **Führen Sie ein Upgrade auf die neueste Version Ihrer Grafik oder Spiel-Engine aus.** Game Engines müssen die Windows 10 SDK-Version 10.0.15063.0 (veröffentlicht im April 2017) oder höher unterstützen.
3. **Aktualisieren Sie alle Middleware, Plug-ins oder Komponenten.** Wenn Ihre APP Komponenten enthält, empfiehlt es sich, ein Upgrade auf die neueste Version durchzuführen.
4. **Entfernen Sie Abhängigkeiten für doppelte sdche**. Je nachdem, auf welchem Gerät Ihre Inhalte ausgerichtet waren, müssen Sie dieses SDK (z. b. "steamvr") entfernen oder bedingt kompilieren, damit Sie stattdessen die Windows-APIs verwenden können.
5. **Arbeiten Sie durch Buildprobleme.** An diesem Punkt ist die Portierungs Übung spezifisch für Ihre APP, die Engine und die Komponenten Abhängigkeiten, die Sie haben.

## <a name="common-porting-steps"></a>Allgemeine Schritte zum Portieren

### <a name="1-make-sure-you-have-the-right-development-hardware"></a>1. Stellen Sie sicher, dass Sie über die richtige Entwicklungs Hardware verfügen.

Auf der Seite [Tools installieren](../install-the-tools.md#immersive-vr-headset-requirements) wird die empfohlene Entwicklungs Hardware aufgeführt.

### <a name="2-upgrade-to-the-latest-flight-of-windows-10"></a>2. Upgrade auf den letzten Flug von Windows 10

Die Windows Mixed Reality-Plattform ist noch nicht aktiv. Es wird empfohlen, [das Windows Insider-Programm](https://insider.windows.com/) für den Zugriff auf den "Windows Insider fast"-Flug zu verbinden.
1. Installieren Sie das [Windows 10 Creators Update](https://www.microsoft.com/software-download/windows10) .
2. [Treten](https://insider.windows.com/) Sie dem Windows-Insider Programm bei.
3. [Entwicklermodus](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development) aktivieren
4. Wechseln Sie zum Abschnitt " [Windows Insider fast-Flüge](https://blogs.technet.microsoft.com/uktechnet/2016/07/01/joining-insider-preview) über **Einstellungen > Update & Sicherheit** ".

### <a name="3-upgrade-to-the-most-recent-build-of-visual-studio"></a>3. Upgrade auf den neuesten Build von Visual Studio
* Wenn Sie Visual Studio verwenden, führen Sie ein Upgrade auf den neuesten Build aus.
* Weitere Informationen finden Sie unter [Installieren der Tools](../install-the-tools.md#installation-checklist) -Seite unter Visual Studio 2019

### <a name="4-choose-the-correct-adapter"></a>4. Wählen Sie den richtigen Adapter aus.
* Richten Sie in Systemen wie Notebooks mit zwei GPUs [den richtigen Adapter](../native/rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications)ein. Dies gilt für Unity-und Native DirectX-apps, bei denen ein ID3D11Device entweder explizit oder implizit (Media Foundation) für seine Funktionalität erstellt wird.

## <a name="unity-porting-guidance"></a>Leitfaden für die Unity-Portierung

[!INCLUDE[](includes/unity-porting-guidance.md)]

## <a name="unreal-porting-guidance"></a>Unreal portieren-Leitfaden

> [!IMPORTANT]
> Wenn Sie HP-Reverb-G2-Controller verwenden, finden Sie in [diesem Artikel](../unreal/unreal-reverb-g2-controllers.md) weitere Anweisungen zur Eingabe Zuordnung.

## <a name="see-also"></a>Siehe auch
* [Windows Mixed Reality-Mindestanforderungen für die PC-Hardware Kompatibilität](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Grundlegendes zur Leistung für gemischte Realität](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Empfehlungen zur Leistung für Unity](../unity/performance-recommendations-for-unity.md)
* [Motion-Controller](../../design/motion-controllers.md)
* [Gesten und Motion-Controller in Unity](../unity/gestures-and-motion-controllers-in-unity.md)
* [Unityengine. XR. WSA. Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [Unityengine. XR. inputtracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [Portierungsleitfäden](porting-guides.md)