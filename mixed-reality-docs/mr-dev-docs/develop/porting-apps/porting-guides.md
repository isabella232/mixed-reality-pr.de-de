---
title: Portieren von VR-Apps zu Windows Mixed Reality
description: Eine schrittweise exemplarische Vorgehensweise, in der erläutert wird, wie eine vorhandene immersive Anwendung in Windows Mixed Reality portiert wird.
author: JBrentJ
ms.author: alexturn
ms.date: 12/9/2020
ms.topic: article
keywords: Port, Unity, Unreal, Middleware, Engine, UWP, Win32, Portierung, HoloLens 1. Generation, Mixed Reality-Headset, Windows Mixed Reality-Headset, Migration, Windows 10, Eingabezuordnung,
ms.openlocfilehash: c8f0ed76fc7288ed406e2044eb2f3edb8982865b5c956f460d2bc1b815e503df
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213512"
---
# <a name="porting-vr-apps-to-windows-mixed-reality"></a>Portieren von VR-Apps zu Windows Mixed Reality

Windows 10 bietet Unterstützung für immersive und holografische Headsets. Wenn Sie Inhalte für andere Geräte wie Oculus Rift oder CSV Vive erstellt haben, bestehen Abhängigkeiten von Bibliotheken, die oberhalb der Plattform-API des Betriebssystems vorhanden sind. Die Umstellung vorhandener Win32 Unity-VR-Apps auf Windows Mixed Reality umfasst die Neuzuweisen der Nutzung herstellerspezifischer VR SDKs für die herstellerübergreifenden VR-APIs von Unity.

## <a name="porting-requirements"></a>Portierungsanforderungen

Auf hoher Ebene sind die folgenden Schritte an der Portierung vorhandener Inhalte beteiligt:
1. **Stellen Sie sicher, dass auf Ihrem PC die Windows 10 Fall Creators Update (16299) ausgeführt wird.** Es wird nicht mehr empfohlen, Vorschaubuilds vom Insider Skip Ahead-Ring zu erhalten, da diese Builds für die Mixed Reality-Entwicklung nicht am stabilsten sind.
2. **Führen Sie ein Upgrade auf die neueste Version Ihrer Grafik- oder Spiel-Engine durch.** Spiel-Engines müssen die Windows 10 SDK Version 10.0.15063.0 (veröffentlicht im April 2017) oder höher unterstützen.
3. **Aktualisieren Sie alle Middleware, Plug-Ins oder Komponenten.** Wenn Ihre App Komponenten enthält, ist es eine gute Idee, ein Upgrade auf die neueste Version durchzuführen.
4. **Entfernen Sie Abhängigkeiten von doppelten SDKs.** Je nachdem, auf welches Gerät Ihre Inhalte abzielen, müssen Sie dieses SDK entfernen oder bedingt kompilieren, damit Sie stattdessen die Windows-APIs als Ziel verwenden können. Ein Beispiel für dieses Szenario wäre "SteamVR".
5. **Arbeiten Sie Buildprobleme durch.** An diesem Punkt ist die Portierungsübung spezifisch für Ihre App, Ihre Engine und die Komponentenabhängigkeiten, über die Sie verfügen.

## <a name="common-porting-steps"></a>Allgemeine Portierungsschritte

### <a name="1-make-sure-you-have-the-right-development-hardware"></a>1. Stellen Sie sicher, dass Sie über die richtige Entwicklungshardware verfügen.

Auf der Seite [VR-Fanleitfaden](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines) wird die empfohlene Entwicklungshardware aufgeführt.

### <a name="2-upgrade-to-the-latest-flight-of-windows-10"></a>2. Upgrade auf den letzten Flight von Windows 10

Die Windows Mixed Reality-Plattform befindet sich noch in der aktiven Entwicklung. Es wird [empfohlen, am Windows Insider Program teilzunehmen,](https://insider.windows.com/) um auf den "Windows Insider Fast"-Flug zuzugreifen.
1. Installieren der [Windows 10 Creators Update](https://www.microsoft.com/software-download/windows10)
2. Treten Sie dem Windows Insider-Programm [bei.](https://insider.windows.com/)
3. Aktivieren des [Entwicklermodus](/windows/uwp/get-started/enable-your-device-for-development)
4. Wechseln Sie über Einstellungen > Abschnitt "Update & **Security" zum Windows Insider Fast-Flug.** [](/archive/blogs/uktechnet/joining-insider-preview)

### <a name="3-upgrade-to-the-most-recent-build-of-visual-studio"></a>3. Upgrade auf den letzten Build von Visual Studio
* Wenn Sie Visual Studio verwenden, führen Sie ein Upgrade auf den letzten Build durch.
* Weitere Informationen finden Sie auf der Seite ["Tools installieren"](../install-the-tools.md#installation-checklist) unter Visual Studio 2019.

### <a name="4-choose-the-correct-adapter"></a>4. Auswählen des richtigen Adapters
* In Systemen wie Notebooks mit zwei GPUs [wird der richtige Adapter als Ziel verwendet.](../native/rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications) Dies gilt für Unity- und native DirectX-Apps, bei denen eine ID3D11Device für ihre Funktionalität entweder explizit oder implizit (Media Foundation) erstellt wird.

## <a name="unity-porting-guidance"></a>Leitfaden zum Portieren von Unity

[!INCLUDE[](includes/unity-porting-guidance.md)]

## <a name="unreal-porting-guidance"></a>Anleitung zum Unreal-Portieren

> [!IMPORTANT]
> Wenn Sie HP Reverb G2-Controller verwenden, finden Sie weitere Anweisungen zur Eingabezuordnung in [diesem Artikel.](../unreal/unreal-reverb-g2-controllers.md)

## <a name="see-also"></a>Siehe auch
* [Windows Mixed Reality Mindestrichtlinien für die PC-Hardwarekompatibilität](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Grundlegendes zur Leistung für Mixed Reality](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Leistungs-Empfehlungen für Unity](../unity/performance-recommendations-for-unity.md)
* [Motion-Controller](../../design/motion-controllers.md)
* [Motion-Controller in Unity](../unity/motion-controllers-in-unity.md)
* [UnityEngine.XR.WSA.Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine.XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [Portierungsleitfäden](porting-guides.md)