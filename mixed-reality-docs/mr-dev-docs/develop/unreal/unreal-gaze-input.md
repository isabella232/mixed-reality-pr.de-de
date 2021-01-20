---
title: Blick Eingabe in Unreal
description: Erfahren Sie, wie Sie die Überblicks Eingaben mit der Augen Verfolgung und der Kopf Richtung für hololens-apps in Unreal einrichten und verwenden.
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Windows Mixed Reality, holograms, hololens 2, Eye Tracking, Blick Eingaben, Head-eingebundene Anzeige, Unreal Engine, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 0c5191534313b94a5382d1065f5a5dd1a208bb49
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98579981"
---
# <a name="gaze-input"></a><span data-ttu-id="f043b-104">Blick Eingabe</span><span class="sxs-lookup"><span data-stu-id="f043b-104">Gaze Input</span></span>

<span data-ttu-id="f043b-105">Mit der Betrachtung von Blick in Mixed Reality-Apps können Sie herausfinden, was Ihre Benutzer ansehen.</span><span class="sxs-lookup"><span data-stu-id="f043b-105">Gaze input in mixed reality apps is all about finding out what your users are looking at.</span></span> <span data-ttu-id="f043b-106">Wenn die Augen Verfolgungs Kameras auf Ihrem Gerät mit den Strahlen in Unreal es World Space übereinstimmen, werden die Daten aus der Datenreihe des Benutzers verfügbar.</span><span class="sxs-lookup"><span data-stu-id="f043b-106">When the eye tracking cameras on your device match up with rays in Unreal's world space, your user's line of sight data becomes available.</span></span> <span data-ttu-id="f043b-107">Der Blick kann sowohl in Blaupausen als auch C++ verwendet werden und ist ein zentrales Feature für Mechanismen wie Objekt Interaktion, Art der Suche und Kamera Steuerelemente.</span><span class="sxs-lookup"><span data-stu-id="f043b-107">Gaze can be used in both blueprints and C++, and is a core feature for mechanics like object interaction, way finding, and camera controls.</span></span>

## <a name="enabling-eye-tracking"></a><span data-ttu-id="f043b-108">Aktivieren der Eye-Überwachung</span><span class="sxs-lookup"><span data-stu-id="f043b-108">Enabling eye tracking</span></span>

- <span data-ttu-id="f043b-109">Aktivieren Sie in den **Projekteinstellungen > hololens** die Funktion für die über **Blicks Eingabe** :</span><span class="sxs-lookup"><span data-stu-id="f043b-109">In **Project Settings > HoloLens**, enable the **Gaze Input** capability:</span></span>

![Screenshot der hololens-Projekt Einstellungs Funktionen mit hervorgehobener Blick Eingabe](images/unreal-gaze-img-01.png)

- <span data-ttu-id="f043b-111">Erstellen Sie einen neuen Actor, und fügen Sie ihn Ihrer Szene hinzu.</span><span class="sxs-lookup"><span data-stu-id="f043b-111">Create a new actor and add it to your scene</span></span>

> [!NOTE]
> <span data-ttu-id="f043b-112">Hololens Eye Tracking in Unreal hat nur einen einzelnen Blick Strahl für beide Augen.</span><span class="sxs-lookup"><span data-stu-id="f043b-112">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes.</span></span> <span data-ttu-id="f043b-113">Die stereokenverfolgung, die zwei Strahlen erfordert, wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f043b-113">Stereoscopic tracking, which requires two rays, isn't supported.</span></span>

## <a name="using-eye-tracking"></a><span data-ttu-id="f043b-114">Verwenden von Eye Tracking</span><span class="sxs-lookup"><span data-stu-id="f043b-114">Using eye tracking</span></span>

<span data-ttu-id="f043b-115">Überprüfen Sie zunächst, ob das Gerät die Eye-Nachverfolgung mit der **iseyetrackerconnected** -Funktion unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f043b-115">First, check that your device supports eye tracking with the **IsEyeTrackerConnected** function.</span></span>  <span data-ttu-id="f043b-116">Wenn die Funktion "true" zurückgibt, wird **getgazedata** aufgerufen, um zu ermitteln, wo die Augen des Benutzers im aktuellen Frame suchen:</span><span class="sxs-lookup"><span data-stu-id="f043b-116">If the function returns true, call **GetGazeData** to find where the user’s eyes are looking at in the current frame:</span></span>

![Blaupause der verbundenen Funktion für die Augen Verfolgung](images/unreal-gaze-img-02.png)

> [!NOTE]
> <span data-ttu-id="f043b-118">Der Fixierungs Punkt und der vertrauensrichtwert sind in hololens nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="f043b-118">The fixation point and the confidence value are not available on HoloLens.</span></span>

<span data-ttu-id="f043b-119">Verwenden Sie den Blick Ursprung und die Richtung in einer Zeilen Ablauf Verfolgung, um genau zu ermitteln, wo Ihre Benutzer suchen.</span><span class="sxs-lookup"><span data-stu-id="f043b-119">Use the gaze origin and direction in a line trace to find out exactly where your users are looking.</span></span>  <span data-ttu-id="f043b-120">Der Wert für den Augenblick ist ein Vektor, beginnend bei der Ursprungs Suche und beim enden an der Ursprungs-und Blick Richtung, multipliziert mit der zeilenlaufverfolgungsentfernung:</span><span class="sxs-lookup"><span data-stu-id="f043b-120">The gaze value is a vector, starting at the gaze origin and ending at the origin plus the gaze direction multiplied by the line trace distance:</span></span>

![Blaupause der Daten Funktion "Get-Blick"](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a><span data-ttu-id="f043b-122">Orientierung bei der Kopfzeile</span><span class="sxs-lookup"><span data-stu-id="f043b-122">Getting head orientation</span></span>

<span data-ttu-id="f043b-123">Sie können auch die Drehung des Head-eingebundenen Anzeigers (HMD) verwenden, um die Richtung des Benutzer Kopfes darzustellen.</span><span class="sxs-lookup"><span data-stu-id="f043b-123">You can also use the rotation of the Head Mounted Display (HMD) to represent the direction of the user’s head.</span></span> <span data-ttu-id="f043b-124">Sie können die Benutzer in die Kopfzeile bringen, ohne die Blick Eingabe Funktion zu aktivieren. Sie erhalten jedoch keine Informationen zu den Augenblick.</span><span class="sxs-lookup"><span data-stu-id="f043b-124">You can get the users head direction without enabling the Gaze Input capability, but you won't get you any eye tracking information.</span></span>  <span data-ttu-id="f043b-125">Fügen Sie einen Verweis auf den Blueprint als Weltkontext hinzu, um die richtigen Ausgabedaten zu erhalten:</span><span class="sxs-lookup"><span data-stu-id="f043b-125">Add a reference to the blueprint as the world context to get the correct output data:</span></span>

> [!NOTE]
> <span data-ttu-id="f043b-126">Das erhalten von HMD-Daten ist nur in Unreal 4,26 und höher verfügbar.</span><span class="sxs-lookup"><span data-stu-id="f043b-126">Getting HMD Data is only available in Unreal 4.26 and onwards.</span></span>

![Blaupause der Get hmddata-Funktion](images/unreal-gaze-img-04.png)

## <a name="using-c"></a><span data-ttu-id="f043b-128">Verwenden von C++</span><span class="sxs-lookup"><span data-stu-id="f043b-128">Using C++</span></span>

- <span data-ttu-id="f043b-129">Fügen Sie in der **Build.cs** -Datei Ihres Spiels die Datei " **Eyetracker** " der **publicdependencymodulenames** -Liste hinzu:</span><span class="sxs-lookup"><span data-stu-id="f043b-129">In your game’s **build.cs** file, add **EyeTracker** to the **PublicDependencyModuleNames** list:</span></span>

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

- <span data-ttu-id="f043b-130">Erstellen Sie in der **Datei/neuen C++-Klasse** einen neuen C++ Actor mit dem Namen " **Eyetracker** ".</span><span class="sxs-lookup"><span data-stu-id="f043b-130">In **File/ New C++ Class**, create a new C++ actor called **EyeTracker**</span></span>
    - <span data-ttu-id="f043b-131">Eine Visual Studio-Projekt Mappe öffnet die neue Klasse "Eyetracker".</span><span class="sxs-lookup"><span data-stu-id="f043b-131">A Visual Studio solution will open up the new EyeTracker class.</span></span> <span data-ttu-id="f043b-132">Erstellen Sie, und führen Sie aus, um das Unreal-Spiel mit dem neuen Brillen-Actor zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="f043b-132">Build and run to open the Unreal game with the new EyeTracker actor.</span></span>  <span data-ttu-id="f043b-133">Suchen Sie im Fenster " **Orts Akteure** " nach "Eyetracker", und ziehen Sie die Klasse in das Spielfenster, um Sie dem Projekt hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="f043b-133">Search for “EyeTracker” in the **Place Actors** window and drag and drop the class into the game window to add it to the project:</span></span>

![Screenshot eines Actors, auf dem das Fenster "Place Actor" geöffnet ist](images/unreal-gaze-img-06.png)

- <span data-ttu-id="f043b-135">Fügen Sie in " **Eyetracker. cpp**" für " **eyetrackerfunctionlibrary**" und " **drawdebughelpers**" Folgendes hinzu:</span><span class="sxs-lookup"><span data-stu-id="f043b-135">In **EyeTracker.cpp**, add includes for **EyeTrackerFunctionLibrary**, and **DrawDebugHelpers**:</span></span>

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

<span data-ttu-id="f043b-136">Überprüfen Sie, ob Ihr Gerät die Eye-Nachverfolgung mit **ueyetrackerfunctionlibrary:: iseyetrackerconnected** unterstützt, bevor Sie versuchen, die Daten des Blicks zu erhalten</span><span class="sxs-lookup"><span data-stu-id="f043b-136">Check that your device supports eye tracking with **UEyeTrackerFunctionLibrary::IsEyeTrackerConnected** before trying to get any gaze data.</span></span>  <span data-ttu-id="f043b-137">Wenn die Eye-Nachverfolgung unterstützt wird, finden Sie den Anfang und das Ende eines Strahls für eine Zeilen Ablauf Verfolgung von **ueyetrackerfunctionlibrary:: getgazedata**.</span><span class="sxs-lookup"><span data-stu-id="f043b-137">If eye tracking is supported, find the start and end of a ray for a line trace from **UEyeTrackerFunctionLibrary::GetGazeData**.</span></span> <span data-ttu-id="f043b-138">Von dort aus können Sie einen Blick Vektor erstellen und seinen Inhalt an **linetracesinglebychannel** übergeben, um alle Ray-Treffer Ergebnisse zu Debuggen:</span><span class="sxs-lookup"><span data-stu-id="f043b-138">From there, you can construct a gaze vector and pass its contents to **LineTraceSingleByChannel** to debug any ray hit results:</span></span>

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

## <a name="next-development-checkpoint"></a><span data-ttu-id="f043b-139">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="f043b-139">Next Development Checkpoint</span></span>

<span data-ttu-id="f043b-140">Wenn Sie der Unreal-Entwicklungs-Journey folgen, die wir entworfen haben, befinden Sie sich mitten im Kennenlernen der MRTK-Grundbausteine.</span><span class="sxs-lookup"><span data-stu-id="f043b-140">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="f043b-141">Von hier aus können Sie mit dem nächsten Baustein fortfahren:</span><span class="sxs-lookup"><span data-stu-id="f043b-141">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f043b-142">Handtracking</span><span class="sxs-lookup"><span data-stu-id="f043b-142">Hand tracking</span></span>](unreal-hand-tracking.md)

<span data-ttu-id="f043b-143">Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:</span><span class="sxs-lookup"><span data-stu-id="f043b-143">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f043b-144">HoloLens-Kamera</span><span class="sxs-lookup"><span data-stu-id="f043b-144">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="f043b-145">Sie können jederzeit zu den [Prüfpunkten für die Unreal-Entwicklung](unreal-development-overview.md#2-core-building-blocks) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="f043b-145">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="f043b-146">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f043b-146">See also</span></span>
* [<span data-ttu-id="f043b-147">Kalibrierung</span><span class="sxs-lookup"><span data-stu-id="f043b-147">Calibration</span></span>](/hololens/hololens-calibration)
* [<span data-ttu-id="f043b-148">Komfort</span><span class="sxs-lookup"><span data-stu-id="f043b-148">Comfort</span></span>](../../design/comfort.md)
* [<span data-ttu-id="f043b-149">Anvisieren und Ausführen</span><span class="sxs-lookup"><span data-stu-id="f043b-149">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="f043b-150">Spracheingabe</span><span class="sxs-lookup"><span data-stu-id="f043b-150">Voice input</span></span>](../../out-of-scope/voice-design.md)