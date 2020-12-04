---
title: Blick Eingabe in Unreal
description: Tutorial zum Einrichten von Blick Eingaben für hololens und Unreal Engine
author: hferrone
ms.author: jacksonf
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, holograms, hololens 2, Eye Tracking, Blick Eingaben, Head-eingebundene Anzeige, Unreal Engine, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: d0470c5abbefce797254aa9f2030519d3347aaab
ms.sourcegitcommit: 9c640c96e2270ef69edd46f1b12acb00b373554d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2020
ms.locfileid: "96578889"
---
# <a name="gaze-input"></a><span data-ttu-id="7b274-104">Blick Eingabe</span><span class="sxs-lookup"><span data-stu-id="7b274-104">Gaze Input</span></span>

<span data-ttu-id="7b274-105">Der Blick wird verwendet, um anzugeben, was der Benutzer ansieht.</span><span class="sxs-lookup"><span data-stu-id="7b274-105">Gaze is used to indicate what the user is looking at.</span></span>  <span data-ttu-id="7b274-106">Dabei werden die Augen Verfolgungs Kameras auf dem Gerät verwendet, um einen Strahl in Unreal World Space zu finden, der dem entspricht, was der Benutzer gerade ansieht.</span><span class="sxs-lookup"><span data-stu-id="7b274-106">This uses the eye tracking cameras on the device to find a ray in Unreal world space matching what the user is currently looking at.</span></span>

## <a name="enabling-eye-tracking"></a><span data-ttu-id="7b274-107">Aktivieren der Eye-Überwachung</span><span class="sxs-lookup"><span data-stu-id="7b274-107">Enabling eye tracking</span></span>

- <span data-ttu-id="7b274-108">Aktivieren Sie in den **Projekteinstellungen > hololens** die Funktion für die über **Blicks Eingabe** :</span><span class="sxs-lookup"><span data-stu-id="7b274-108">In **Project Settings > HoloLens**, enable the **Gaze Input** capability:</span></span>

![Screenshot der hololens-Projekt Einstellungs Funktionen mit hervorgehobener Blick Eingabe](images/unreal-gaze-img-01.png)

- <span data-ttu-id="7b274-110">Erstellen Sie einen neuen Actor, und fügen Sie ihn Ihrer Szene hinzu.</span><span class="sxs-lookup"><span data-stu-id="7b274-110">Create a new actor and add it to your scene</span></span>

> [!NOTE] 
> <span data-ttu-id="7b274-111">Hololens Eye Tracking in Unreal hat nur einen einzelnen Blick Strahl für beide Augen und nicht die zwei Strahlen, die für die Stereoskopie erforderlich sind, was nicht unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="7b274-111">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes instead of the two rays needed for stereoscopic tracking, which is not supported.</span></span>

## <a name="using-eye-tracking"></a><span data-ttu-id="7b274-112">Verwenden von Eye Tracking</span><span class="sxs-lookup"><span data-stu-id="7b274-112">Using eye tracking</span></span>

<span data-ttu-id="7b274-113">Überprüfen Sie zunächst, ob das Gerät die Augen Nachverfolgung mit der iseyetrackerconnected-Funktion unterstützt.</span><span class="sxs-lookup"><span data-stu-id="7b274-113">First check that the device supports eye tracking with the IsEyeTrackerConnected function.</span></span>  <span data-ttu-id="7b274-114">Wenn dies true zurückgibt, wird getgazedata aufgerufen, um zu ermitteln, wo die Augen des Benutzers während des aktuellen Rahmens suchen:</span><span class="sxs-lookup"><span data-stu-id="7b274-114">If this returns true, call GetGazeData to find where the user’s eyes are looking at during the current frame:</span></span>

![Blaupause der verbundenen Funktion für die Augen Verfolgung](images/unreal-gaze-img-02.png)

> [!NOTE]
> <span data-ttu-id="7b274-116">Der Fixierungs Punkt und der vertrauensrichtwert sind in hololens nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="7b274-116">The fixation point and the confidence value are not available on HoloLens.</span></span>

<span data-ttu-id="7b274-117">Um zu ermitteln, was der Benutzer sucht, verwenden Sie den Blick Ursprung und die Richtung in einer Zeilen Ablauf Verfolgung.</span><span class="sxs-lookup"><span data-stu-id="7b274-117">To find what the user is looking at, use the gaze origin and direction in a line trace.</span></span>  <span data-ttu-id="7b274-118">Der Anfang dieses Vektors ist der Blick Ursprung, und das Ende ist der Ursprung und die Richtung des Blicks, multipliziert mit der gewünschten Entfernung:</span><span class="sxs-lookup"><span data-stu-id="7b274-118">The start of this vector is the gaze origin and the end is the origin plus the gaze direction multiplied by the desired distance:</span></span>

![Blaupause der Daten Funktion "Get-Blick"](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a><span data-ttu-id="7b274-120">Orientierung bei der Kopfzeile</span><span class="sxs-lookup"><span data-stu-id="7b274-120">Getting head orientation</span></span>

<span data-ttu-id="7b274-121">Alternativ kann die HMD-Drehung verwendet werden, um die Richtung des Benutzer Kopfes darzustellen.</span><span class="sxs-lookup"><span data-stu-id="7b274-121">Alternatively, the HMD rotation can be used to represent the direction of the user’s head.</span></span>  <span data-ttu-id="7b274-122">Hierfür ist die Eingabe Funktion für den Blick nicht erforderlich, aber es werden keine Augen Verfolgungs Informationen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7b274-122">This does not require the Gaze Input capability but won't give you any eye tracking information.</span></span>  <span data-ttu-id="7b274-123">Ein Verweis auf den Blueprint muss als Weltkontext hinzugefügt werden, um die richtigen Ausgabedaten zu erhalten:</span><span class="sxs-lookup"><span data-stu-id="7b274-123">A reference to the blueprint must be added as the world context to get the correct output data:</span></span>

> [!NOTE]
> <span data-ttu-id="7b274-124">Das erhalten von HMD-Daten ist nur in Unreal 4,26 und höher verfügbar.</span><span class="sxs-lookup"><span data-stu-id="7b274-124">Getting HMD Data is only available in Unreal 4.26 and onwards.</span></span>

![Blaupause der Get hmddata-Funktion](images/unreal-gaze-img-04.png)

## <a name="using-c"></a><span data-ttu-id="7b274-126">Verwenden von C++</span><span class="sxs-lookup"><span data-stu-id="7b274-126">Using C++</span></span> 

- <span data-ttu-id="7b274-127">Fügen Sie in der Build.cs-Datei Ihres Spiels "Eyetracker" der publicdependencymodulenames-Liste hinzu:</span><span class="sxs-lookup"><span data-stu-id="7b274-127">In your game’s build.cs file, add “EyeTracker” to the PublicDependencyModuleNames list:</span></span>

```cpp
PublicDependencyModuleNames.AddRange(
    new string[] {
        "Core",
        "CoreUObject",
        "Engine",
        "InputCore",
        "EyeTracker"
});
```

- <span data-ttu-id="7b274-128">Erstellen Sie in "File/New C++ Class" einen neuen C++ Actor mit dem Namen "Eyetracker".</span><span class="sxs-lookup"><span data-stu-id="7b274-128">In “File/ New C++ Class”, Create a new C++ actor called “EyeTracker”</span></span>
    - <span data-ttu-id="7b274-129">Eine Visual Studio-Projekt Mappe wird für die neue Klasse "Eyetracker" geöffnet.</span><span class="sxs-lookup"><span data-stu-id="7b274-129">A Visual Studio solution will open to the new EyeTracker class.</span></span> <span data-ttu-id="7b274-130">Erstellen Sie, und führen Sie aus, um das Unreal-Spiel mit dem neuen Brillen-Actor zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="7b274-130">Build and run to open the Unreal game with the new EyeTracker actor.</span></span>  <span data-ttu-id="7b274-131">Suchen Sie im Fenster "Platzieren von Akteuren" nach "Eyetracker".</span><span class="sxs-lookup"><span data-stu-id="7b274-131">Search for “EyeTracker” in the “Place Actors” window.</span></span>  <span data-ttu-id="7b274-132">Ziehen Sie diese Klasse per Drag & amp; Drop in das Spielfenster, um Sie dem Projekt hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="7b274-132">Drag and drop this class into the game window to add it to the project:</span></span>

![Screenshot eines Actors, auf dem das Fenster "Place Actor" geöffnet ist](images/unreal-gaze-img-06.png)

- <span data-ttu-id="7b274-134">Fügen Sie in "Eyetracker. cpp" für "eyetrackerfunctionlibrary" und "drawdebughelpers" Folgendes hinzu:</span><span class="sxs-lookup"><span data-stu-id="7b274-134">In EyeTracker.cpp, add includes for EyeTrackerFunctionLibrary, and DrawDebugHelpers:</span></span>

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

<span data-ttu-id="7b274-135">Überprüfen Sie in Tick, ob das Gerät die Eye-Nachverfolgung mit ueyetrackerfunctionlibrary:: iseyetrackerconnected unterstützt.</span><span class="sxs-lookup"><span data-stu-id="7b274-135">In Tick, check that the device supports eye tracking with UEyeTrackerFunctionLibrary::IsEyeTrackerConnected.</span></span>  <span data-ttu-id="7b274-136">Suchen Sie anschließend den Anfang und das Ende eines Strahls für eine Zeilen Ablauf Verfolgung von ueyetrackerfunctionlibrary:: getgazedata:</span><span class="sxs-lookup"><span data-stu-id="7b274-136">Then find the start and end of a ray for a line trace from UEyeTrackerFunctionLibrary::GetGazeData:</span></span>

```cpp
void AEyeTracker::Tick(float DeltaTime)
{
    Super::Tick(DeltaTime);

    if(UEyeTrackerFunctionLibrary::IsEyeTrackerConnected())
    {
        FEyeTrackerGazeData GazeData;
        if(UEyeTrackerFunctionLibrary::GetGazeData(GazeData))
        {
            FVector Start = GazeData.GazeOrigin;
            FVector End = GazeData.GazeOrigin + GazeData.GazeDirection * 100;

            FHitResult Hit Result;
            if (GWorld->LineTraceSingleByChannel(HitResult, Start, End, ECollisionChannel::ECC_Visiblity))
            {
                DrawDebugCoordinateSystem(GWorld, HitResult.Location, FQuat::Identity.Rotator(), 10);
            }
        }
    }
}
```

## <a name="next-development-checkpoint"></a><span data-ttu-id="7b274-137">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="7b274-137">Next Development Checkpoint</span></span>

<span data-ttu-id="7b274-138">Wenn Sie dem Weg der Unreal-Entwicklungsprüfpunkte folgen, den wir entworfen haben, befinden Sie sich mitten im Kennenlernen der MRTK-Grundbausteine.</span><span class="sxs-lookup"><span data-stu-id="7b274-138">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="7b274-139">Von hier aus können Sie mit dem nächsten Baustein fortfahren:</span><span class="sxs-lookup"><span data-stu-id="7b274-139">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="7b274-140">Handtracking</span><span class="sxs-lookup"><span data-stu-id="7b274-140">Hand tracking</span></span>](unreal-hand-tracking.md)

<span data-ttu-id="7b274-141">Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:</span><span class="sxs-lookup"><span data-stu-id="7b274-141">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7b274-142">HoloLens-Kamera</span><span class="sxs-lookup"><span data-stu-id="7b274-142">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="7b274-143">Sie können jederzeit zu den [Prüfpunkten für die Unreal-Entwicklung](unreal-development-overview.md#2-core-building-blocks) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="7b274-143">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="7b274-144">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="7b274-144">See also</span></span>
* [<span data-ttu-id="7b274-145">Kalibrierung</span><span class="sxs-lookup"><span data-stu-id="7b274-145">Calibration</span></span>](../../calibration.md)
* [<span data-ttu-id="7b274-146">Komfort</span><span class="sxs-lookup"><span data-stu-id="7b274-146">Comfort</span></span>](../../design/comfort.md)
* [<span data-ttu-id="7b274-147">Anvisieren und Ausführen</span><span class="sxs-lookup"><span data-stu-id="7b274-147">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="7b274-148">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="7b274-148">Voice input</span></span>](../../out-of-scope/voice-design.md)
