---
title: WinRT-APIs mit Unity für hololens
description: 'Leanr: Verwenden von WinRT-APIs und des Windows-Namespace in ihren Unity Mixed Reality-Projekten für hololens.'
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, WinRT, Windows Mixed Reality, API, Exemplarische Vorgehensweise, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Mixed Reality-APIs
ms.openlocfilehash: 2116f0025449fdf127998e605f87de456e9bdaf9
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583549"
---
# <a name="winrt-apis-with-unity-for-hololens"></a><span data-ttu-id="38997-104">WinRT-APIs mit Unity für hololens</span><span class="sxs-lookup"><span data-stu-id="38997-104">WinRT APIs with Unity for HoloLens</span></span>

<span data-ttu-id="38997-105">Auf dieser Seite wird beschrieben, wie Sie WinRT-APIs in Ihrem Unity-Projekt für hololens verwenden.</span><span class="sxs-lookup"><span data-stu-id="38997-105">This page describes how to make use of WinRT APIs in your Unity project for HoloLens.</span></span>

## <a name="mixed-reality-apis"></a><span data-ttu-id="38997-106">Mixed Reality-APIs</span><span class="sxs-lookup"><span data-stu-id="38997-106">Mixed Reality APIs</span></span>

<span data-ttu-id="38997-107">Eine gemischte Realität fokussierte Teilmenge der Windows SDK wurde in einer .NET Standard 2,0-kompatiblen Projektion zur Verfügung gestellt, die Sie in Ihrem Projekt ohne Präprozessordirektiven verwenden können.</span><span class="sxs-lookup"><span data-stu-id="38997-107">A Mixed Reality focused subset of the Windows SDK has been made available in a .NET Standard 2.0 compatible projection, which you can use in your project without preprocessor directives.</span></span> <span data-ttu-id="38997-108">Die meisten APIs in Windows.</span><span class="sxs-lookup"><span data-stu-id="38997-108">Most APIs in the Windows.</span></span> <span data-ttu-id="38997-109">Perception und Windows. UI. Input. räumliche Namespaces sind enthalten und können erweitert werden, um in Zukunft weitere APIs hinzufügen zu können.</span><span class="sxs-lookup"><span data-stu-id="38997-109">Perception and Windows.UI.Input.Spatial namespaces are included and may expand to include additional APIs in the future.</span></span> <span data-ttu-id="38997-110">Die projizierten APIs können während der Ausführung im Editor verwendet werden, was die Verwendung des [Wiedergabemodus](//windows/mixed-reality/unity-play-mode)ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="38997-110">The projected APIs can be used while running in the Editor, which enables the use of [Play Mode](//windows/mixed-reality/unity-play-mode).</span></span> <span data-ttu-id="38997-111">Um diese Projektion zu verwenden, nehmen Sie die folgenden Änderungen am Projekt vor:</span><span class="sxs-lookup"><span data-stu-id="38997-111">To use this projection, make the following modifications to your project:</span></span>

1) <span data-ttu-id="38997-112">Fügen Sie mithilfe [von nuget für Unity](https://github.com/GlitchEnzo/NuGetForUnity)einen Verweis auf das nuget-Paket [Microsoft. Windows. mixedreality. dotnetwinrt](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) hinzu.</span><span class="sxs-lookup"><span data-stu-id="38997-112">Add a reference to the [Microsoft.Windows.MixedReality.DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT) NuGet package using [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity).</span></span>
2) <span data-ttu-id="38997-113">Verweise auf den `Windows` Namespace mit dem Präfix `Microsoft.` :</span><span class="sxs-lookup"><span data-stu-id="38997-113">Prefix references to the `Windows` namespace with `Microsoft.`:</span></span>
```cs
using namespace Microsoft.Windows.Perception.Spatial;
```
3) <span data-ttu-id="38997-114">Ersetzen Sie Native Zeiger Umwandlungen durch `FromNativePtr` :</span><span class="sxs-lookup"><span data-stu-id="38997-114">Replace native pointer casts with `FromNativePtr`:</span></span>
```cs
var worldOrigin = SpatialCoordinateSystem.FromNativePtr(unityWorldOriginPtr);
```

## <a name="conditionally-include-winrt-api-calls"></a><span data-ttu-id="38997-115">Bedingtes Einschließen von WinRT-API-aufrufen</span><span class="sxs-lookup"><span data-stu-id="38997-115">Conditionally include WinRT API calls</span></span>

<span data-ttu-id="38997-116">Sie können auch die WinRT-APIs in Unity-Projekten verwenden, die für die universelle Windows-Plattform-und Xbox One-Plattform mithilfe von Präprozessordirektiven erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="38997-116">You can also use the WinRT APIs in Unity projects built for the Universal Windows Platform and Xbox One platform by using preprocessor directives.</span></span> <span data-ttu-id="38997-117">Jeder Code, den Sie in Unity-Skripts schreiben, die auf WinRT-APIs abzielen, muss nur für diese Builds bedingt eingeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="38997-117">Any code that you write in Unity scripts that target WinRT APIs must be conditionally included for only those builds.</span></span> 

<span data-ttu-id="38997-118">Dies kann über zwei Schritte in Unity erfolgen:</span><span class="sxs-lookup"><span data-stu-id="38997-118">This can be done via two steps in Unity:</span></span>
1) <span data-ttu-id="38997-119">Der API-Kompatibilitäts Grad muss in den Player Einstellungen auf **.NET 4,6** oder **.NET Standard 2,0** festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="38997-119">API compatibility level must be set to **.NET 4.6** or **.NET Standard 2.0** in the player settings</span></span>
    - <span data-ttu-id="38997-120">**Bearbeiten**  >  **Projekteinstellungen**  >  **Player**  >  **Konfiguration**  >  **API-Kompatibilitäts Grad** auf **.NET 4,6** oder **.NET Standard 2,0**</span><span class="sxs-lookup"><span data-stu-id="38997-120">**Edit** > **Project Settings** > **Player** > **Configuration** > **Api Compatibility Level** to **.NET 4.6** or **.NET Standard 2.0**</span></span>
2) <span data-ttu-id="38997-121">Die **ENABLE_WINMD_SUPPORT** der Präprozessordirektive muss von WinRT-verwendeter Code umschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="38997-121">The preprocessor directive **ENABLE_WINMD_SUPPORT** must be wrapped around any WinRT-leveraged code</span></span>

<span data-ttu-id="38997-122">Der folgende Code Ausschnitt befindet sich auf der manuellen Seite von Unity für [universelle Windows-Plattform: WinRT-API in c#-Skripts](https://docs.unity3d.com/Manual/windowsstore-scripts.html).</span><span class="sxs-lookup"><span data-stu-id="38997-122">The following code snippet is from the Unity manual page for [Universal Windows Platform: WinRT API in C# scripts](https://docs.unity3d.com/Manual/windowsstore-scripts.html).</span></span> <span data-ttu-id="38997-123">In diesem Beispiel wird eine Werbe-ID zurückgegeben, jedoch nur für UWP-und Xbox One-Builds:</span><span class="sxs-lookup"><span data-stu-id="38997-123">In this example, an advertising ID is returned, but only on UWP and Xbox One builds:</span></span>

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

## <a name="edit-your-scripts-in-a-unity-c-project"></a><span data-ttu-id="38997-124">Bearbeiten von Skripts in einem Unity c#-Projekt</span><span class="sxs-lookup"><span data-stu-id="38997-124">Edit your scripts in a Unity C# project</span></span>

<span data-ttu-id="38997-125">Wenn Sie im Unity-Editor auf ein Skript doppelklicken, wird das Skript standardmäßig in einem Editor-Projekt gestartet.</span><span class="sxs-lookup"><span data-stu-id="38997-125">When you double-click a script in the Unity editor, it will by default launch your script in an editor project.</span></span> <span data-ttu-id="38997-126">Die WinRT-APIs scheinen unbekannt zu sein, da das Visual Studio-Projekt nicht auf das Windows-Runtime verweist.</span><span class="sxs-lookup"><span data-stu-id="38997-126">The WinRT APIs will appear to be unknown because the Visual Studio project doesn't reference the Windows Runtime.</span></span> <span data-ttu-id="38997-127">Die **ENABLE_WINMD_SUPPORT** -Direktive ist nicht definiert, und jeder *#if* umschließende Code wird ignoriert, bis Sie das Projekt in eine UWP Visual Studio-Projekt Mappe erstellen.</span><span class="sxs-lookup"><span data-stu-id="38997-127">The **ENABLE_WINMD_SUPPORT** directive is undefined and any *#if* wrapped code is ignored until you build your project into a UWP Visual Studio solution.</span></span>

## <a name="see-also"></a><span data-ttu-id="38997-128">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="38997-128">See also</span></span>
* [<span data-ttu-id="38997-129">Exportieren und Erstellen einer Unity-Projektmappe für Visual Studio</span><span class="sxs-lookup"><span data-stu-id="38997-129">Exporting and building a Unity Visual Studio solution</span></span>](exporting-and-building-a-unity-visual-studio-solution.md)
* [<span data-ttu-id="38997-130">Windows-Runtime Unterstützung von Unity</span><span class="sxs-lookup"><span data-stu-id="38997-130">Windows Runtime Support Unity</span></span>](https://docs.unity3d.com/Manual/IL2CPP-WindowsRuntimeSupport.html)