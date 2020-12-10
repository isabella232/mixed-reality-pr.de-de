---
title: 'Lernprogramme für räumliche Audiodaten: 2. Versehen von Sounds für die Schaltflächeninteraktion mit räumlichen Effekten'
description: Fügen Sie dem Projekt eine Schaltfläche hinzu, und räumlichen Sie die Sound der Schaltflächen Interaktion.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, hololens2, Spatial Audiodatei, mrtk, Mixed Reality Toolkit, UWP, Windows 10, HRTF, Head-Related Transfer Function, Reverb, Microsoft spatializer, Prefabs, volumekurve
ms.openlocfilehash: 62825ed8922cd904212160748018446cbc76b839
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002595"
---
# <a name="spatializing-button-interaction-sounds"></a>Versehen von Sounds für die Schaltflächeninteraktion mit räumlichen Effekten

## <a name="objectives"></a>Ziele
In diesem zweiten Kapitel des Moduls "Spatial AUDIOMODULE" der hololens 2-Tutorials werden folgende Schritte durchgehen:
* Hinzufügen einer Schaltfläche
* Schaltflächen Klick-Sounds spatialisieren

## <a name="add-a-button"></a>Hinzufügen einer Schaltfläche
Wählen Sie im **Projekt** Bereich **Assets** aus, und geben Sie "PressableButtonHoloLens2" in die Suchleiste ein:

![Schaltflächen vorfab in Assets](images/spatial-audio/button-prefab-in-assets.png)

Bei der Prefab-Schaltfläche handelt es sich um den durch ein blaues Symbol dargestellten Eintrag anstelle eines weißen Symbols. Ziehen Sie das präfab mit dem Namen **PressableButtonHoloLens2** in den Bereich **Hierarchie** . Legen Sie im **Inspektor** -Bereich für die neue Schaltfläche die **Positions** Eigenschaft auf (0,-0,4, 2) fest, damit Sie vor dem Benutzer angezeigt wird, wenn die Anwendung gestartet wird. Die **Transformations** Komponente der Schaltfläche sieht wie folgt aus:

![Schaltflächen Transformation](images/spatial-audio/button-transform.png)

## <a name="spatialize-button-feedback"></a>Schaltflächen-Feedback spatialisieren
In diesem Schritt Stufen Sie das Audiofeedback für die Schaltfläche ein. Verwandte Entwurfsvorschläge finden Sie unter [Spatial Sound Design](../../../design/spatial-sound-design.md). 

Im Bereich **Audiomixer** definieren Sie Ziele, die als **mixergruppen** bezeichnet werden, für die Audiowiedergabe aus **audioquellkomponenten** . 
* Öffnen Sie den Bereich **Audiomixer** in der Menüleiste mithilfe von **Windows > Audio> Audiomixer** .
* Erstellen Sie einen **Mixer** , indem Sie auf "+" neben " **Mixer**" klicken. Der neue Mixer enthält eine Standard **Gruppe** namens **Master**.

Ihr **Mischbereich** sieht nun wie folgt aus:

![Mischbereich mit dem ersten Mixer](images/spatial-audio/mixer-panel-with-first-mixer.png)

> [!NOTE]
> Bis der Reverb in [Kapitel 5](unity-spatial-audio-ch5.md)aktiviert ist, zeigt die Volume-Verbrauchseinheit des Mischers keine Aktivitäten für Sounds an, die über den Microsoft spatializer abgespielt werden.

Klicken Sie im Bereich **Hierarchie** auf die **PressableButtonHoloLens2** . Im **Inspektor** -Bereich:
1. Suchen der **audioquellkomponente**
2. Klicken Sie für die **Output** -Eigenschaft auf die Auswahl, und wählen Sie Ihren Mixer aus.
3. Aktivieren Sie das Kontrollkästchen **spatialize** .
4. Verschieben Sie den Schieberegler **räumlicher Blend** in 3D (1).

> [!NOTE]
> In Versionen von Unity vor 2019 befindet sich das Kontrollkästchen "spatialize" am unteren Rand des **inspektorbereichs** für die **Audioquelle**.

Nachdem diese Änderungen vorgenommen wurden, sieht die **audioquellkomponente** Ihrer **PressableButtonHoloLens2** wie folgt aus:

![Schaltflächen-Audioquelle](images/spatial-audio/button-audio-source.png)

> [!NOTE]
> Wenn Sie **räumliche Blend** in 1 (3D) verschieben, ohne das **spatialize** -Kontrollkästchen zu aktivieren, verwendet Unity den Schwenk räumlichen spatializer anstelle von **Microsoft spatializer** mit HRTFs.

## <a name="adjust-the-volume-curve"></a>Anpassen der volumekurve
Standardmäßig vermindert Unity spatialisierte Sounds, wenn Sie weiter vom Listener entfernt werden. Wenn diese Dämpfung auf Interaktions Feedback Sounds angewendet wird, kann die Verwendung der Schnittstelle schwieriger werden.

Um diese Dämpfung zu deaktivieren, passen Sie die **volumekurve** an. In der Komponente **Audioquelle** des **inspektorbereichs** für den **PressableButtonHoloLens2** gibt es einen Abschnitt mit dem Namen **3D Sound Settings**. In diesem Abschnitt:
1. Legen Sie die Eigenschaft **Volume Rolloff** auf Linear fest.
2. Ziehen Sie den Endpunkt der **volumekurve** (die rote Kurve) von "0" auf der y-Achse auf "1".
3. Wenn Sie die Form der **volumekurve** an eine flache Größe anpassen möchten, ziehen Sie das Steuerelement der weißen Kurve auf parallel zur X-Achse.

Nachdem diese Änderungen vorgenommen wurden, sieht der Abschnitt **3D-Sound Einstellungen** in den **audioquellgenschaften** der **PressableButtonHoloLens2** wie folgt aus:

![Schaltflächen-3D-Soundeinstellungen](images/spatial-audio/button-3d-sound-settings.png)

## <a name="testing-the-spatialize-audio"></a>Testen der spatialize-Audiodatei

Sie können die neuen räumlichen Schaltflächen-Interaktions Sounds testen:

* Geben Sie im Unity-Editor den Spielmodus ein, idealerweise mit einem Beispiel für eine Schleife in der Szene.
* Verschieben Sie das Objekt mit der Audioquelle von links nach rechts, und vergleichen Sie es mit und ohne räumliche Audiodaten. Sie können die Einstellungen für die Audioquelle zum Testen ändern von:
    * Verschieben der Spatial Blend-Eigenschaft zwischen 0-1 (2D, nicht räumlich und 3D-spatialized Sound)
    * Überprüfen und Deaktivieren der spatialize-Eigenschaft

## <a name="next-steps"></a>Nächste Schritte

Testen Sie Ihre APP auf einem hololens 2 oder im Unity-Editor. In der App können Sie auf die Schaltfläche tippen und die räumlichen Schaltflächen-Interaktions Sounds hören.

Wenn Sie im Unity-Editor testen, drücken Sie die Leertaste, und Scrollen Sie mit dem Mausrad, um die Hand Simulation zu aktivieren. Weitere Informationen finden Sie in der [mrtk-Dokumentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene).

> [!div class="nextstepaction"]
> [Kapitel 3](unity-spatial-audio-ch3.md)

