---
title: Eingabe anvisiertes Anvisierten in Unreal
description: Erfahren Sie, wie Sie anvisierte Eingaben mit Blickverfolgung und Kopfausrichtung für HoloLens Apps in Unreal einrichten und verwenden.
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Windows Mixed Reality, Hologramme, HoloLens 2, Eyetracking, Eingabe anvisierten Blicken, Anzeige am Kopf, Unreal-Engine, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: e423086e293629e3dfadb49b52a376c0b93f5e465328b93f47c2f1e3e0790b63
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200676"
---
# <a name="gaze-input"></a>Eingabe zum Anvingen

Beim Anvieren von Eingaben in Mixed Reality-Apps geht es darum, herauszufinden, was Ihre Benutzer sehen. Wenn die Eyetrackingkameras auf Ihrem Gerät mit Lichtstrahl im Weltraum von Unreal übereinstimmen, werden die Sichtdaten Ihres Benutzers verfügbar. Anvität kann sowohl in Blaupausen als auch in C++ verwendet werden und ist ein Kernfeature für Mechanismen wie Objektinteraktion, Wegesuche und Kamerasteuerelemente.

## <a name="enabling-eye-tracking"></a>Aktivieren von Eyetracking

- Aktivieren **Project Einstellungen > HoloLens** die Funktion **Anvitätseingabe:**

![Screenshot: HoloLens-Projekteinstellungsfunktionen mit hervorgehobener Eingabe zum Anvingen](images/unreal-gaze-img-01.png)

- Erstellen eines neuen Akteurs und Hinzufügen zu Ihrer Szene

> [!NOTE]
> HoloLens Eyetracking in Unreal verfügt nur über einen einzelnen Anvisiertenstrahl für beide Augen. Die Stereoüberwachung, die zwei Lichtstrahl erfordert, wird nicht unterstützt.

## <a name="using-eye-tracking"></a>Verwenden von Eye Tracking

Überprüfen Sie zunächst, ob Ihr Gerät eye tracking mit der **IsEyeTrackerConnected-Funktion** unterstützt.  Wenn die Funktion TRUE zurückgibt, rufen **Sie Get WiedeData** auf, um zu suchen, wo die Augen des Benutzers im aktuellen Frame aussehen:

![Blaupause der Funktion "Is Eye Tracking Connected"](images/unreal-gaze-img-02.png)

> [!NOTE]
> Der Fixierungspunkt und der Konfidenzwert sind auf dem HoloLens.

Verwenden Sie den Ursprung und die Richtung des Anverfolgs in einer Zeilenverfolgung, um genau herauszufinden, wo Ihre Benutzer suchen.  Der Anvisierungswert ist ein Vektor, beginnend beim Anvisierungsstart und endet am Ursprung plus der Anvisierungsrichtung multipliziert mit der Entfernung der Linienverfolgung:

![Blaupause der Funktion "Get Gaze Data"](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a>Abrufen der Kopfausrichtung

Sie können auch die Drehung des HMD (Head Mounted Display) verwenden, um die Richtung des Kopfs des Benutzers anzuzeigen. Sie können die Kopfrichtung der Benutzer erhalten, ohne die Funktion Anvitätseingabe zu aktivieren, aber Sie erhalten keine Eyetrackinginformationen.  Fügen Sie einen Verweis auf die Blaupause als Kontext hinzu, um die richtigen Ausgabedaten zu erhalten:

> [!NOTE]
> Das Abrufen von HMD-Daten ist nur ab Unreal 4.26 verfügbar.

![Blaupause der Get HMDData-Funktion](images/unreal-gaze-img-04.png)

## <a name="using-c"></a>Verwenden von C++

- Fügen Sie in der **Datei build.cs Ihres** Spiels **EyeTracker** zur **Liste PublicDependencyModuleNames** hinzu:

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

- Erstellen **Sie in der File/New C++-Klasse** einen neuen C++-Actor namens **EyeTracker.**
    - Eine Visual Studio-Lösung öffnet die neue EyeTracker-Klasse. Erstellen Sie das Unreal-Spiel, und führen Sie es aus, um es mit dem neuen EyeTracker-Akteur zu öffnen.  Search for “EyeTracker” in the **Place Actors** window and drag and drop the class into the game window to add it to the project:

![Screenshot eines Akteurs mit geöffneter Stelle im Akteurfenster](images/unreal-gaze-img-06.png)

- Fügen Sie in **EyeTracker.cpp** includes für **EyeTrackerFunctionLibrary** und **DrawDebugHelpers hinzu:**

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

Überprüfen Sie, ob Ihr Gerät eye tracking mit **UEyeTrackerFunctionLibrary::IsEyeTrackerConnected** unterstützt, bevor Sie versuchen, Anvistikdaten zu erhalten.  Wenn Eyetracking unterstützt wird, suchen Sie den Anfang und das Ende eines Strahls für eine Zeilenüberwachung von **UEyeTrackerFunctionLibrary::GetDisplayeData**. Von dort aus können Sie einen Anvisierungsvektor erstellen und seinen Inhalt an **LineTraceSingleByChannel** übergeben, um alle Ergebnisse von Strahltreffern zu debuggen:

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
* [Kalibrierung](/hololens/hololens-calibration)
* [Komfort](../../design/comfort.md)
* [Anvisieren und Ausführen](../../design/gaze-and-commit.md)
* [Spracheingabe](../../out-of-scope/voice-design.md)