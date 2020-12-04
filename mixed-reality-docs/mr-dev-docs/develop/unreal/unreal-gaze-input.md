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
# <a name="gaze-input"></a>Blick Eingabe

Der Blick wird verwendet, um anzugeben, was der Benutzer ansieht.  Dabei werden die Augen Verfolgungs Kameras auf dem Gerät verwendet, um einen Strahl in Unreal World Space zu finden, der dem entspricht, was der Benutzer gerade ansieht.

## <a name="enabling-eye-tracking"></a>Aktivieren der Eye-Überwachung

- Aktivieren Sie in den **Projekteinstellungen > hololens** die Funktion für die über **Blicks Eingabe** :

![Screenshot der hololens-Projekt Einstellungs Funktionen mit hervorgehobener Blick Eingabe](images/unreal-gaze-img-01.png)

- Erstellen Sie einen neuen Actor, und fügen Sie ihn Ihrer Szene hinzu.

> [!NOTE] 
> Hololens Eye Tracking in Unreal hat nur einen einzelnen Blick Strahl für beide Augen und nicht die zwei Strahlen, die für die Stereoskopie erforderlich sind, was nicht unterstützt wird.

## <a name="using-eye-tracking"></a>Verwenden von Eye Tracking

Überprüfen Sie zunächst, ob das Gerät die Augen Nachverfolgung mit der iseyetrackerconnected-Funktion unterstützt.  Wenn dies true zurückgibt, wird getgazedata aufgerufen, um zu ermitteln, wo die Augen des Benutzers während des aktuellen Rahmens suchen:

![Blaupause der verbundenen Funktion für die Augen Verfolgung](images/unreal-gaze-img-02.png)

> [!NOTE]
> Der Fixierungs Punkt und der vertrauensrichtwert sind in hololens nicht verfügbar.

Um zu ermitteln, was der Benutzer sucht, verwenden Sie den Blick Ursprung und die Richtung in einer Zeilen Ablauf Verfolgung.  Der Anfang dieses Vektors ist der Blick Ursprung, und das Ende ist der Ursprung und die Richtung des Blicks, multipliziert mit der gewünschten Entfernung:

![Blaupause der Daten Funktion "Get-Blick"](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a>Orientierung bei der Kopfzeile

Alternativ kann die HMD-Drehung verwendet werden, um die Richtung des Benutzer Kopfes darzustellen.  Hierfür ist die Eingabe Funktion für den Blick nicht erforderlich, aber es werden keine Augen Verfolgungs Informationen angezeigt.  Ein Verweis auf den Blueprint muss als Weltkontext hinzugefügt werden, um die richtigen Ausgabedaten zu erhalten:

> [!NOTE]
> Das erhalten von HMD-Daten ist nur in Unreal 4,26 und höher verfügbar.

![Blaupause der Get hmddata-Funktion](images/unreal-gaze-img-04.png)

## <a name="using-c"></a>Verwenden von C++ 

- Fügen Sie in der Build.cs-Datei Ihres Spiels "Eyetracker" der publicdependencymodulenames-Liste hinzu:

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

- Erstellen Sie in "File/New C++ Class" einen neuen C++ Actor mit dem Namen "Eyetracker".
    - Eine Visual Studio-Projekt Mappe wird für die neue Klasse "Eyetracker" geöffnet. Erstellen Sie, und führen Sie aus, um das Unreal-Spiel mit dem neuen Brillen-Actor zu öffnen.  Suchen Sie im Fenster "Platzieren von Akteuren" nach "Eyetracker".  Ziehen Sie diese Klasse per Drag & amp; Drop in das Spielfenster, um Sie dem Projekt hinzuzufügen:

![Screenshot eines Actors, auf dem das Fenster "Place Actor" geöffnet ist](images/unreal-gaze-img-06.png)

- Fügen Sie in "Eyetracker. cpp" für "eyetrackerfunctionlibrary" und "drawdebughelpers" Folgendes hinzu:

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

Überprüfen Sie in Tick, ob das Gerät die Eye-Nachverfolgung mit ueyetrackerfunctionlibrary:: iseyetrackerconnected unterstützt.  Suchen Sie anschließend den Anfang und das Ende eines Strahls für eine Zeilen Ablauf Verfolgung von ueyetrackerfunctionlibrary:: getgazedata:

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

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie dem Weg der Unreal-Entwicklungsprüfpunkte folgen, den wir entworfen haben, befinden Sie sich mitten im Kennenlernen der MRTK-Grundbausteine. Von hier aus können Sie mit dem nächsten Baustein fortfahren: 

> [!div class="nextstepaction"]
> [Handtracking](unreal-hand-tracking.md)

Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:

> [!div class="nextstepaction"]
> [HoloLens-Kamera](unreal-hololens-camera.md)

Sie können jederzeit zu den [Prüfpunkten für die Unreal-Entwicklung](unreal-development-overview.md#2-core-building-blocks) zurückkehren.

## <a name="see-also"></a>Siehe auch
* [Kalibrierung](../../calibration.md)
* [Komfort](../../design/comfort.md)
* [Anvisieren und Ausführen](../../design/gaze-and-commit.md)
* [Spracheingabe](../../out-of-scope/voice-design.md)
