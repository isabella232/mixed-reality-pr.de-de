---
title: WinRT-APIs mit Unity für hololens
description: 'Leanr: Verwenden von WinRT-APIs und des Windows-Namespace in ihren Unity Mixed Reality-Projekten für hololens.'
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, WinRT, Windows Mixed Reality, API, Exemplarische Vorgehensweise, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Mixed Reality-APIs
ms.openlocfilehash: cf80eff408b54c610c9e7878ccfa5185b3fbcca1
ms.sourcegitcommit: 63b7f6d5237327adc51486afcd92424b79e6118b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2021
ms.locfileid: "98809994"
---
# <a name="winrt-apis-with-unity-for-hololens"></a>WinRT-APIs mit Unity für hololens

Auf dieser Seite wird beschrieben, wie Sie WinRT-APIs in Ihrem Unity-Projekt für hololens verwenden.

## <a name="mixed-reality-apis"></a>Mixed Reality-APIs

Eine gemischte Realität fokussierte Teilmenge der Windows SDK wurde in einer .NET Standard 2,0-kompatiblen Projektion zur Verfügung gestellt, die Sie in Ihrem Projekt ohne Präprozessordirektiven verwenden können. Die meisten APIs in Windows. Perception und Windows. UI. Input. räumliche Namespaces sind enthalten und können erweitert werden, um in Zukunft weitere APIs hinzufügen zu können. Die projizierten APIs können während der Ausführung im Editor verwendet werden, was die Verwendung des [Wiedergabemodus](/windows/mixed-reality/unity-play-mode)ermöglicht. Um diese Projektion zu verwenden, nehmen Sie die folgenden Änderungen am Projekt vor:

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

Sie können auch die WinRT-APIs in Unity-Projekten verwenden, die für die universelle Windows-Plattform-und Xbox One-Plattform mithilfe von Präprozessordirektiven erstellt wurden. Jeder Code, den Sie in Unity-Skripts schreiben, die auf WinRT-APIs abzielen, muss nur für diese Builds bedingt eingeschlossen werden. 

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

Wenn Sie im Unity-Editor auf ein Skript doppelklicken, wird das Skript standardmäßig in einem Editor-Projekt gestartet. Die WinRT-APIs scheinen unbekannt zu sein, da das Visual Studio-Projekt nicht auf das Windows-Runtime verweist. Die **ENABLE_WINMD_SUPPORT** -Direktive ist nicht definiert, und jeder *#if* umschließende Code wird ignoriert, bis Sie das Projekt in eine UWP Visual Studio-Projekt Mappe erstellen.

## <a name="see-also"></a>Siehe auch
* [Exportieren und Erstellen einer Unity-Projektmappe für Visual Studio](exporting-and-building-a-unity-visual-studio-solution.md)
* [Windows-Runtime Unterstützung von Unity](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)