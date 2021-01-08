---
title: Blick Eingabe in Unreal
description: Erfahren Sie, wie Sie die Überblicks Eingaben mit der Augen Verfolgung und der Kopf Richtung für hololens-apps in Unreal einrichten und verwenden.
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Windows Mixed Reality, holograms, hololens 2, Eye Tracking, Blick Eingaben, Head-eingebundene Anzeige, Unreal Engine, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: e546867fe02acd5e72ee76b4108a369ec25fd32f
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010140"
---
# <a name="gaze-input"></a>Blick Eingabe

Mit der Betrachtung von Blick in Mixed Reality-Apps können Sie herausfinden, was Ihre Benutzer ansehen. Wenn die Augen Verfolgungs Kameras auf Ihrem Gerät mit den Strahlen in Unreal es World Space übereinstimmen, werden die Daten aus der Datenreihe des Benutzers verfügbar. Der Blick kann sowohl in Blaupausen als auch C++ verwendet werden und ist ein zentrales Feature für Mechanismen wie Objekt Interaktion, Art der Suche und Kamera Steuerelemente.

## <a name="enabling-eye-tracking"></a>Aktivieren der Eye-Überwachung

- Aktivieren Sie in den **Projekteinstellungen > hololens** die Funktion für die über **Blicks Eingabe** :

![Screenshot der hololens-Projekt Einstellungs Funktionen mit hervorgehobener Blick Eingabe](images/unreal-gaze-img-01.png)

- Erstellen Sie einen neuen Actor, und fügen Sie ihn Ihrer Szene hinzu.

> [!NOTE]
> Hololens Eye Tracking in Unreal hat nur einen einzelnen Blick Strahl für beide Augen. Die stereokenverfolgung, die zwei Strahlen erfordert, wird nicht unterstützt.

## <a name="using-eye-tracking"></a>Verwenden von Eye Tracking

Überprüfen Sie zunächst, ob das Gerät die Eye-Nachverfolgung mit der **iseyetrackerconnected** -Funktion unterstützt.  Wenn die Funktion "true" zurückgibt, wird **getgazedata** aufgerufen, um zu ermitteln, wo die Augen des Benutzers im aktuellen Frame suchen:

![Blaupause der verbundenen Funktion für die Augen Verfolgung](images/unreal-gaze-img-02.png)

> [!NOTE]
> Der Fixierungs Punkt und der vertrauensrichtwert sind in hololens nicht verfügbar.

Verwenden Sie den Blick Ursprung und die Richtung in einer Zeilen Ablauf Verfolgung, um genau zu ermitteln, wo Ihre Benutzer suchen.  Der Wert für den Augenblick ist ein Vektor, beginnend bei der Ursprungs Suche und beim enden an der Ursprungs-und Blick Richtung, multipliziert mit der zeilenlaufverfolgungsentfernung:

![Blaupause der Daten Funktion "Get-Blick"](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a>Orientierung bei der Kopfzeile

Sie können auch die Drehung des Head-eingebundenen Anzeigers (HMD) verwenden, um die Richtung des Benutzer Kopfes darzustellen. Sie können die Benutzer in die Kopfzeile bringen, ohne die Blick Eingabe Funktion zu aktivieren. Sie erhalten jedoch keine Informationen zu den Augenblick.  Fügen Sie einen Verweis auf den Blueprint als Weltkontext hinzu, um die richtigen Ausgabedaten zu erhalten:

> [!NOTE]
> Das erhalten von HMD-Daten ist nur in Unreal 4,26 und höher verfügbar.

![Blaupause der Get hmddata-Funktion](images/unreal-gaze-img-04.png)

## <a name="using-c"></a>Verwenden von C++

- Fügen Sie in der **Build.cs** -Datei Ihres Spiels die Datei " **Eyetracker** " der **publicdependencymodulenames** -Liste hinzu:

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

- Erstellen Sie in der **Datei/neuen C++-Klasse** einen neuen C++ Actor mit dem Namen " **Eyetracker** ".
    - Eine Visual Studio-Projekt Mappe öffnet die neue Klasse "Eyetracker". Erstellen Sie, und führen Sie aus, um das Unreal-Spiel mit dem neuen Brillen-Actor zu öffnen.  Suchen Sie im Fenster " **Orts Akteure** " nach "Eyetracker", und ziehen Sie die Klasse in das Spielfenster, um Sie dem Projekt hinzuzufügen:

![Screenshot eines Actors, auf dem das Fenster "Place Actor" geöffnet ist](images/unreal-gaze-img-06.png)

- Fügen Sie in " **Eyetracker. cpp**" für " **eyetrackerfunctionlibrary**" und " **drawdebughelpers**" Folgendes hinzu:

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

Überprüfen Sie, ob Ihr Gerät die Eye-Nachverfolgung mit **ueyetrackerfunctionlibrary:: iseyetrackerconnected** unterstützt, bevor Sie versuchen, die Daten des Blicks zu erhalten  Wenn die Eye-Nachverfolgung unterstützt wird, finden Sie den Anfang und das Ende eines Strahls für eine Zeilen Ablauf Verfolgung von **ueyetrackerfunctionlibrary:: getgazedata**. Von dort aus können Sie einen Blick Vektor erstellen und seinen Inhalt an **linetracesinglebychannel** übergeben, um alle Ray-Treffer Ergebnisse zu Debuggen:

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

Wenn Sie der Unreal-Entwicklungs-Journey folgen, die wir entworfen haben, befinden Sie sich mitten im Kennenlernen der MRTK-Grundbausteine. Von hier aus können Sie mit dem nächsten Baustein fortfahren:

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
