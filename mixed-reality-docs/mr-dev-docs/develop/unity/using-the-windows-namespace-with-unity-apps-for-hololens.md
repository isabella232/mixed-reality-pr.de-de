---
title: WinRT-APIs mit Unity für hololens
description: Erläutert, wie Sie WinRT-APIs (den Windows-Namespace) in Ihrem Unity-Projekt für hololens verwenden.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, WinRT, Windows Mixed Reality, API, Exemplarische Vorgehensweise
ms.openlocfilehash: 80f950d7571a936e93eb08490ad83dbb34a50b3a
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2020
ms.locfileid: "91687254"
---
# <a name="winrt-apis-with-unity-for-hololens"></a>WinRT-APIs mit Unity für hololens

Auf dieser Seite wird beschrieben, wie Sie WinRT-APIs in Ihrem Unity-Projekt für hololens verwenden.

## <a name="mixed-reality-apis"></a>Mixed Reality-APIs

Eine gemischte Realität fokussierte Teilmenge der Windows SDK wurde in einer .NET Standard 2,0-kompatiblen Projektion zur Verfügung gestellt, die Sie in Ihrem Projekt ohne Präprozessordirektiven verwenden können. Dies umfasst die meisten APIs in den Namespaces "Windows. perception" und "Windows. UI. Input. Spatial" und kann erweitert werden, um in Zukunft weitere APIs einzubeziehen. Die projizierten APIs können während der Ausführung im Editor verwendet werden, was die Verwendung des [Wiedergabemodus](https://docs.microsoft.com//windows/mixed-reality/unity-play-mode)ermöglicht. Um diese Projektion zu verwenden, nehmen Sie die folgenden Änderungen am Projekt vor:

1) Fügen Sie mithilfe [von nuget für Unity](https://github.com/GlitchEnzo/NuGetForUnity)einen Verweis auf das nuget-Paket [Microsoft. Windows. mixedreality. dotnetwinrt](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) hinzu.
2) Verweise auf den `Windows` Namespace mit dem Präfix `Microsoft.` :
```cs
using namespace Microsoft.Windows.Perception.Spatial;
```
3) Ersetzen Sie Native Zeiger Umwandlungen durch `FromNativePtr` :
```cs
var worldOrigin = SpatialCoordinateSystem.FromNativePtr(unityWorldOriginPtr);
```

## <a name="conditionally-include-winrt-api-calls"></a>Bedingtes Einschließen von WinRT-API-aufrufen

Alternativ können WinRT-APIs für Unity-Projekte genutzt werden, die für die universelle Windows-Plattform-und Xbox One-Plattform mithilfe von Präprozessordirektiven erstellt wurden. Jeder Code, den Sie in Unity-Skripts schreiben, die auf WinRT-APIs abzielen, muss nur für diese Builds bedingt eingeschlossen werden. 

Dies kann über zwei Schritte in Unity erfolgen:
1) Der API-Kompatibilitäts Grad muss in den Player Einstellungen auf **.NET 4,6** oder **.NET Standard 2,0** festgelegt werden.
    - **Bearbeiten**  >  **Projekteinstellungen**  >  **Player**  >  **Konfiguration**  >  **API-Kompatibilitäts Grad** auf **.NET 4,6** oder **.NET Standard 2,0**
2) Die **ENABLE_WINMD_SUPPORT** der Präprozessordirektive muss von WinRT-verwendeter Code umschlossen werden.

Der folgende Code Ausschnitt befindet sich auf der manuellen Seite von Unity für [universelle Windows-Plattform: WinRT-API in c#-Skripts](https://docs.unity3d.com/Manual/windowsstore-scripts.html). In diesem Beispiel wird eine Werbe-ID zurückgegeben, jedoch nur für UWP-und Xbox One-Builds:

```
using UnityEngine;
public class WinRTAPI : MonoBehaviour {
    void Update() {
        auto adId = GetAdvertisingId();
        // ...
    }

    string GetAdvertisingId() {
        #if ENABLE_WINMD_SUPPORT
            return Windows.System.UserProfile.AdvertisingManager.AdvertisingId;
        #else
            return "";
        #endif
    }
}
```

## <a name="edit-your-scripts-in-a-unity-c-project"></a>Bearbeiten von Skripts in einem Unity c#-Projekt

Wenn Sie im Unity-Editor auf ein Skript doppelklicken, wird das Skript standardmäßig in einem Editor-Projekt gestartet. Die WinRT-APIs scheinen unbekannt zu sein, da das Visual Studio-Projekt nicht auf das Windows-Runtime verweist. Außerdem wird die **ENABLE_WINMD_SUPPORT** -Direktive nicht definiert, und jeder *#if* umschließende Code wird ignoriert, bis Sie das Projekt in eine UWP-Visual Studio-Projekt Mappe erstellen.

## <a name="see-also"></a>Weitere Informationen
* [Exportieren und Erstellen einer Unity-Projektmappe für Visual Studio](exporting-and-building-a-unity-visual-studio-solution.md)
* [Windows-Runtime Unterstützung von Unity](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)
