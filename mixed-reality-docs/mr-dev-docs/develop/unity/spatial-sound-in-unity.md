---
title: Raumklang in Unity
description: Wiedergabe von räumlichem Sound von einem bestimmten 3D-Punkt in der Unity-Szene.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, räumlicher Sound, HRTF, Raum Größe, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, mrtk, Mixed Reality Toolkit, spatializer, Reverb
ms.openlocfilehash: db01fe81457d0f46b7f287458b4d48af4a98f2bc
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678439"
---
# <a name="spatial-sound-in-unity"></a>Raumklang in Unity

Diese Seite ist mit Ressourcen für räumliche Sounds in Unity verknüpft.

## <a name="spatializer-options"></a>Spatializer-Optionen
Die spatializer-Optionen für gemischte Reality-Anwendungen umfassen Folgendes:
* *MS HRTF spatializer*. Unity stellt dies als Teil des optionalen *Windows Mixed Reality* -Pakets bereit.
  * Dies erfolgt auf CPU in einer kostengünstigeren "Single Source"-Architektur.
  * Dies wird aus Gründen der Abwärtskompatibilität mit ursprünglichen hololens-Anwendungen bereitgestellt.
* Der *Microsoft spatializer*. Dies ist im [GitHub-Repository von Microsoft spatializer](https://github.com/microsoft/spatialaudio-unity)verfügbar.
  * Hierfür wird eine kostengünstigere Architektur mit mehreren Quellen verwendet.
  * Auf hololens 2 wird dies in einen Hardwarebeschleuniger verlagert.

Für neue Anwendungen wird *Microsoft spatializer* empfohlen.

## <a name="enable-spatialization"></a>Spatialization aktivieren

Verwenden Sie [nuget für Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) , um _Microsoft. spatialaudio. spatializer. unity_ zu installieren, und wählen Sie **Microsoft spatializer** in den Audioeinstellungen Ihres Projekts aus. Führen Sie anschließend Folgendes durch:
* Anfügen einer **Audioquelle** an ein Objekt in der Hierarchie
* Aktivieren Sie das Kontrollkästchen **spatialization aktivieren** .
* Verschieben Sie den Schieberegler für **räumliche Blend** auf "1".
* Stellen Sie sicher, dass auf Ihrer Entwickler Arbeitsstation räumliche Audiodaten aktiviert sind Aktivieren Sie diese Option, indem Sie in der Taskleiste mit der rechten Maustaste auf das Volumesymbol klicken und sicherstellen, dass räumlicher Sound auf einen anderen Wert als "Off" gesetzt ist. Um die beste Darstellung von hololens 2 zu erhalten, wählen Sie **Windows Sonic für Kopfhörer aus**.

>[!NOTE]
>Wenn Sie in Unity eine Fehlermeldung erhalten, dass das Plug-in "Microsoft. spatialaudio. spatializer. unity" nicht geladen werden kann, weil eine ihrer Abhängigkeiten fehlt, überprüfen Sie, ob Sie die neueste Version des [Microsoft Visual C++ verteilbaren](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) Pakets auf Ihrem PC installiert haben.

Weitere Informationen finden Sie unter:
* [Microsoft spatializer-GitHub-Repository](https://github.com/microsoft/spatialaudio-unity)
* [Microsoft-Tutorial zu spatializer](tutorials/unity-spatial-audio-ch1.md)
* [Dokumentation zur Audioquelle von Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [Dokumentation zu spatializer von Unity](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a>Distanzabhängige Dämpfung
Der standardmäßige Entfernungs Abfall von Unity weist einen minimalen Abstand von 1 Meter und einen maximalen Abstand von 500 Meter mit einem logarithmischen Rolloff auf. Diese Einstellungen können für Ihr Szenario funktionieren, oder Sie werden feststellen, dass die Quellen zu schnell oder zu langsam gedämpft werden. Weitere Informationen finden Sie unter:
* [Sound Design in gemischter Realität](../../design/spatial-sound-design.md) für empfohlene Einstellungen.
* In [der Dokumentation zur Audioquelle von Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) finden Sie Anweisungen zum Festlegen dieser Kurven.

## <a name="reverb"></a>Hall
Der _Microsoft spatializer_ deaktiviert die Auswirkungen von postspatializer standardmäßig. So aktivieren Sie den Reverb und andere Auswirkungen auf räumliche Quellen:
* Fügen **Sie die Raumeffekt** -Komponente der Sende Ebene an jede Quelle an.
* Passen Sie die Kurve der Sende Ebene für jede Quelle an, um zu steuern, wie hoch die Audiodaten für die Auswirkungen der Verarbeitung an das Diagramm zurückgesendet werden.

Ausführliche Informationen finden Sie [in Kapitel 5 des Lernprogramms zu spatializer](tutorials/unity-spatial-audio-ch5.md) .

## <a name="unity-spatial-sound-examples"></a>Beispiele für räumliche Unity-Sounds
Beispiele für räumliche Sounds in Unity finden Sie unter:
* [Mrtk-Demos](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* Das [Microsoft spatializer-Beispiel Projekt](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)

## <a name="next-development-checkpoint"></a>Nächster Entwicklungsprüfpunkt

Wenn Sie der Unity-Entwicklungs Prüf Punkt Journey folgen, die wir gerade angelegt haben, sind Sie in der Mitte, dass Sie die Grundbausteine der gemischten Realität erkunden. Von hier aus können Sie mit dem nächsten Baustein fortfahren:

> [!div class="nextstepaction"]
> [Text](text-in-unity.md)

Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:

> [!div class="nextstepaction"]
> [Gemeinsame Erfahrung](shared-experiences-in-unity.md)

Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.

## <a name="see-also"></a>Siehe auch
* [Sound Design in gemischter Realität](../../design/spatial-sound-design.md)
* [Microsoft-Tutorial zu spatializer](tutorials/unity-spatial-audio-ch1.md)
