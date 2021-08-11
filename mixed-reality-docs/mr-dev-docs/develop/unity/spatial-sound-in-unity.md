---
title: Raumklang in Unity
description: Erfahren Sie anhand von Beispielen, wie Sie räumliche Sounds von einem bestimmten 3D-Punkt in Ihrer Unity-Szene wiedergeben und mildern.
author: kegodin
ms.author: v-hferrone
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, Räumlicher Sound, HRTF, Raumgröße, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, MRTK, Mixed Reality Toolkit, Spatializer, Hall
ms.openlocfilehash: e6e56732a888fd096335a114fceba557519b01bf8df84a7670b9265f46c75a34
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228226"
---
# <a name="spatial-sound-in-unity"></a>Raumklang in Unity

Diese Seite enthält Links zu Ressourcen für räumlichen Sound in Unity.

## <a name="spatializer-options"></a>Spatializer-Optionen

Zu den Spatializer-Optionen für Mixed Reality-Anwendungen gehören:
* Unity stellt den *MS HRTF Spatializer* als Teil des *Windows Mixed Reality* optionalen Pakets bereit.
  * Wird auf CPU in einer kostengünstigeren "Single Source"-Architektur ausgeführt.
  * Aus Gründen der Abwärtskompatibilität mit ursprünglichen HoloLens Anwendungen bereitgestellt.
* Microsoft *Spatializer* ist im Microsoft [Spatializer GitHub Repository](https://github.com/microsoft/spatialaudio-unity)verfügbar.
  * Verwendet eine kostengünstigere Architektur mit mehreren Quellen.
  * Wird an einen Hardwarebeschleunigungsbeschleuniger auf dem HoloLens 2 ausgelagert. 

Für neue Anwendungen wird Microsoft *Spatializer* empfohlen.

## <a name="enable-spatialization"></a>Aktivieren der Räumlichen Verräumigung

Verwenden Sie [NuGet für Unity,](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) um _Microsoft.SpatialAudio.Spatializer.Unity_ zu installieren, und wählen Sie **Microsoft Spatializer** in den Audioeinstellungen Ihres Projekts aus. Führen Sie anschließend Folgendes durch:
* Anfügen einer **Audioquelle** an ein Objekt in der Hierarchie
* Aktivieren Sie das Kontrollkästchen **Spatialization aktivieren.**
* Verschieben des **Schiebereglers "Spatial Blend"** auf "1"
* Stellen Sie sicher, dass räumliche Audiodaten auf Ihrer Entwicklerarbeitsstation aktiviert sind. 
    * Klicken Sie mit der rechten Maustaste auf das Lautstärkesymbol in der Taskleiste, und stellen Sie sicher, dass Spatial Sound auf einen anderen Als "off" festgelegt ist. 
    * Wählen Sie **Windows Sonic für Kopfhörer** aus, um die beste Darstellung ihrer HoloLens 2 zu erhalten.

>[!NOTE]
>Wenn sie in Unity eine Fehlermeldung erhalten, dass das Plug-In Microsoft.SpatialAudio.Spatializer.Unity nicht geladen werden kann, weil eine der Abhängigkeiten fehlt, überprüfen Sie, ob die neueste Version des [Microsoft Visual C++ Redistributable](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) auf Ihrem PC installiert ist.

   Weitere Informationen finden Sie unter
* [Microsoft Spatializer GitHub Repository](https://github.com/microsoft/spatialaudio-unity)
* [Microsoft-Tutorial zu Spatializern](tutorials/unity-spatial-audio-ch1.md)
* [Dokumentation zur Unity-Audioquelle](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [Dokumentation zum Spatializer von Unity](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a>Distanzabhängige Dämpfung

Der standardmäßige entfernungsbasierte Verfall von Unity weist einen Mindestabstand von 1 Meter und einen maximalen Abstand von 500 Metern mit einem logarithmischen Rolloff auf. Diese Einstellungen funktionieren möglicherweise für Ihr Szenario, oder Sie stellen fest, dass Quellen zu schnell oder zu langsam abschwächen.    Weitere Informationen finden Sie unter
* [Sounddesign in Mixed Reality](../../design/spatial-sound-design.md) für empfohlene Einstellungen.
* Anweisungen zum Festlegen dieser Kurven finden Sie in der Dokumentation zur Audioquelle von [Unity.](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)

## <a name="reverb"></a>Reverb

Microsoft _Spatializer_ deaktiviert post-spatializer-Effekte standardmäßig. So aktivieren Sie Hall und andere Effekte für räumliche Quellen:
* Anfügen der **Room Effect Send Level-Komponente** an jede Quelle
* Passen Sie die Sendeebenenkurve für jede Quelle an, um den Gewinn für die Audiodaten zu steuern, die zur Verarbeitung von Effekten an den Graphen gesendet werden.

Weitere Informationen finden Sie [in Kapitel 5 des Spatializer-Tutorials.](tutorials/unity-spatial-audio-ch5.md)

## <a name="unity-spatial-sound-examples"></a>Beispiele für räumlichen Unity-Sound

Beispiele für räumlichen Sound in Unity finden Sie unter:
* [MRTK-Demos](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* Das [Microsoft Spatializer-Beispielprojekt](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie die von uns festgelegte Unity-Entwicklungsreise verfolgen, sind Sie dabei, die Mixed Reality wichtigsten Bausteine zu untersuchen. Von hier aus können Sie mit dem nächsten Baustein fortfahren:

> [!div class="nextstepaction"]
> [Text](text-in-unity.md)

Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:

> [!div class="nextstepaction"]
> [Gemeinsame Erfahrung](shared-experiences-in-unity.md)

Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.

## <a name="see-also"></a>Siehe auch

* [Sounddesign in Mixed Reality](../../design/spatial-sound-design.md)
* [Microsoft-Tutorial zu Spatializern](tutorials/unity-spatial-audio-ch1.md)
