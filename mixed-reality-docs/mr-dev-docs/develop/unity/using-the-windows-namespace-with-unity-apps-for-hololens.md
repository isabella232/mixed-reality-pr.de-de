---
title: WinRT-APIs mit Unity für HoloLens
description: Erfahren Sie, wie Sie WinRT-APIs und den Windows-Namespace in Ihren Unity Mixed Reality-Projekten für HoloLens.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, WinRT, Windows Mixed Reality, API, exemplarische Vorgehensweise, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Mixed Reality-APIs
ms.openlocfilehash: 158c28d9186269108442226bbfcfc90a3c235a71336fdab9dbf9eadc21a309a1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115215606"
---
# <a name="winrt-apis-with-unity-for-hololens"></a>WinRT-APIs mit Unity für HoloLens

Auf dieser Seite wird beschrieben, wie Sie WinRT-APIs in Ihrem Unity-Projekt für HoloLens.

## <a name="mixed-reality-apis"></a>Mixed Reality-APIs

Eine Mixed Reality Teilmenge des Windows SDK wurde in einer .NET Standard 2.0-kompatiblen Projektion zur Verfügung gestellt, die Sie ohne Präprozessordirektiven in Ihrem Projekt verwenden können. Die meisten APIs im Windows. Wahrnehmung und Windows. Benutzeroberfläche. Input.Spatial-Namespaces sind enthalten und können in Zukunft um zusätzliche APIs erweitert werden. Die projizierten APIs können während der Ausführung im Editor verwendet werden, was die Verwendung des [Wiedergabemodus ermöglicht.](/windows/mixed-reality/unity-play-mode) Um diese Projektion zu verwenden, nehmen Sie die folgenden Änderungen an Ihrem Projekt vor:

1) Fügen Sie einen Verweis auf [microsoft.Windows. MixedReality.DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) NuGet paket using NuGet [for Unity](https://github.com/GlitchEnzo/NuGetForUnity).
2) Präfixverweise auf den `Windows` Namespace mit `Microsoft.` :
```cs
using namespace Microsoft.Windows.Perception.Spatial;
```
3) Ersetzen Sie native Zeigercasts durch `FromNativePtr` :
```cs
var worldOrigin = SpatialCoordinateSystem.FromNativePtr(unityWorldOriginPtr);
```

## <a name="conditionally-include-winrt-api-calls"></a>Bedingtes Schließen von WinRT-API-Aufrufen

Sie können die WinRT-APIs auch in Unity-Projekten verwenden, die für die Universelle Windows-Plattform und Xbox One-Plattform mithilfe von Präprozessordirektiven erstellt wurden. Jeder Code, den Sie in Unity-Skripts schreiben, die auf WinRT-APIs zielen, muss nur für diese Builds bedingt eingeschlossen werden. 

Dies kann über zwei Schritte in Unity erfolgen:
1) Der API-Kompatibilitätsgrad muss in den Playereinstellungen auf **.NET 4.6** oder **.NET Standard 2.0** festgelegt werden.
    - **Bearbeiten**  >  **Project Einstellungen**  >  **Player**  >  **Konfiguration**  >  **API-Kompatibilitätsgrad** **bis .NET 4.6** **oder .NET Standard 2.0**
2) Die Präprozessordi directive **ENABLE_WINMD_SUPPORT** muss um jeglichen von WinRT genutzten Code umschlossen werden.

Der folgende Codeausschnitt ist von der Unity-Handbuchseite für [universal Windows Platform: WinRT-API in C#-Skripts.](https://docs.unity3d.com/Manual/windowsstore-scripts.html) In diesem Beispiel wird eine Werbe-ID zurückgegeben, jedoch nur auf UWP und Xbox One Builds:

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

## <a name="edit-your-scripts-in-a-unity-c-project"></a>Bearbeiten Ihrer Skripts in einem Unity C#-Projekt

Wenn Sie im Unity-Editor auf ein Skript doppelklicken, wird ihr Skript standardmäßig in einem Editorprojekt gestartet. Die WinRT-APIs scheinen unbekannt zu sein, da das Visual Studio-Projekt nicht auf die Windows Verweist. Die  ENABLE_WINMD_SUPPORT-Direktive ist nicht *definiert,* und alle #if umschlossenen Code werden ignoriert, bis Sie Ihr Projekt in einer UWP-Visual Studio erstellen.

## <a name="see-also"></a>Siehe auch
* [Exportieren und Erstellen einer Unity-Projektmappe für Visual Studio](exporting-and-building-a-unity-visual-studio-solution.md)
* [Windows Runtime-Unterstützung für Unity](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)