---
title: 'Lernprogramme für räumliche Audiodaten: 2. Versehen von Sounds für die Schaltflächeninteraktion mit räumlichen Effekten'
description: Fügen Sie dem Projekt eine Schaltfläche hinzu, und räumlichen Sie die Sound der Schaltflächen Interaktion.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, hololens2, Spatial Audiodatei, mrtk, Mixed Reality Toolkit, UWP, Windows 10, HRTF, Head-Related Transfer Function, Reverb, Microsoft spatializer, Prefabs, volumekurve
ms.openlocfilehash: 12d159cb162cbf136483f7be94b0d297319a0737
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590762"
---
# <a name="2-spatializing-button-interaction-sounds"></a>2. Versehen von Sounds für die Schaltflächeninteraktion mit räumlichen Effekten

## <a name="overview"></a>Übersicht

In diesem Tutorial erfahren Sie, wie Sie die schaltflächeninteraktionssounds spatialisieren und außerdem erfahren, wie Sie einen Audioclip verwenden, um eine räumliche Schaltflächen Interaktion zu testen.  

## <a name="objectives"></a>Ziele

* Hinzufügen und spatialisieren der Schaltflächen Klick-Sounds

## <a name="add-a-button"></a>Hinzufügen einer Schaltfläche

Wählen Sie zum Hinzufügen der Schaltfläche "Prefab" im **Projekt** Fenster **Pakete** aus, und geben Sie "PressableButtonHoloLens2" in die Suchleiste ein.

![Schaltflächen vorfab in Assets](images/spatial-audio/spatial-audio-02-section1-step1-1.png)

Die Schaltflächen-vorfab ist der durch ein blaues Symbol dargestellte Eintrag. Klicken und ziehen Sie die **PressableButtonHoloLens2** -vorfab in die Hierarchie. Wenn das **PressableButtonHoloLens2** -Objekt noch ausgewählt ist, konfigurieren Sie die **Transformations** Komponente im Inspektor-Fenster wie folgt:

* **Position**: X = 0, Y =-0,4, Z = 2
* **Drehung**: X = 0, Y = 0, Z = 0
* **Skalierung**: X = 1, Y = 1, Z = 1

![Schaltflächen Transformation](images/spatial-audio/spatial-audio-02-section1-step1-2.png)

Um sich auf die Objekte in der Szene zu konzentrieren, können Sie auf das **PressableButtonHoloLens2** -Objekt doppelklicken und anschließend etwas vergrößern:

## <a name="spatialize-button-feedback"></a>Schaltflächen-Feedback spatialisieren

In diesem Schritt Stufen Sie das Audiofeedback für die Schaltfläche ein. Verwandte Entwurfsvorschläge finden Sie unter [Spatial Sound Design](../../../design/spatial-sound-design.md).

Im Fenster **Audiomixer** definieren Sie Ziele, die als **mischungsgruppen** bezeichnet werden, für die Audiowiedergabe aus **audioquellkomponenten** .

Um das **audiomischfenster** zu öffnen, klicken Sie im Unity-Menü auf **Fenster**  >    >  **audioaudiomixer**: ![ geöffneten audiomischerfenster.](images/spatial-audio/spatial-audio-02-section2-step1-1.png)

 Erstellen Sie einen **Mixer** , indem Sie auf "+" neben " **Mixer** " klicken und einen passenden Namen für den Mixer eingeben, z. b. _räumlicher Audiomixer_. Der neue Mixer enthält eine Standard **Gruppe** namens **Master**.

![Mischbereich mit dem ersten Mixer](images/spatial-audio/spatial-audio-02-section2-step1-2.png)

> [!NOTE]
> Bis das "Reverb" in einem [fünften Kapitel aktiviert ist: das Hinzufügen von Abstand zu räumlichen Audiodaten](unity-spatial-audio-ch5.md)durch die Verwendung von "Hall" wird nicht angezeigt.

Wählen Sie im Fenster Hierarchie den **PressableButtonHoloLens2** aus, suchen Sie im Inspektor-Fenster die **audioquellkomponente** , und konfigurieren Sie die audioquellkomponente wie folgt:

1. Klicken Sie für die **Output** -Eigenschaft auf die Auswahl, und wählen Sie den von Ihnen erstellten **Mixer** aus.
2. Aktivieren Sie das Kontrollkästchen **spatialize** .
3. Verschieben Sie den Schieberegler **räumlicher Blend** in 3D (1).

![Schaltflächen-Audioquelle](images/spatial-audio/spatial-audio-02-section2-step1-3.png)

> [!NOTE]
> Wenn Sie **räumliche Blend** in 1 (3D) verschieben, ohne das **spatialize** -Kontrollkästchen zu aktivieren, verwendet Unity den Schwenk räumlichen spatializer anstelle von **Microsoft spatializer** mit HRTFs.

## <a name="adjust-the-volume-curve"></a>Anpassen der volumekurve

Standardmäßig vermindert Unity spatialisierte Sounds, wenn Sie weiter vom Listener entfernt werden. Wenn diese Dämpfung auf Interaktions Feedback Sounds angewendet wird, kann die Verwendung der Schnittstelle schwieriger werden.

Um diese Dämpfung zu deaktivieren, müssen Sie die **volumekurve** in der **audioquellkomponente** anpassen.

Wählen Sie im Fenster Hierarchie den **PressableButtonHoloLens2** aus, und navigieren Sie dann im Inspektor-Fenster zu **Audioquelle**  >  **3D Sound Settings** , und konfigurieren Sie wie folgt:

1. Festlegen der **volumerolloff** -Eigenschaft auf Linear Rolloff
2. Ziehen Sie den Endpunkt der **volumekurve** (die rote Kurve) von "0" auf der y-Achse auf "1".
3. Wenn Sie die Form der **volumekurve** an eine flache Größe anpassen möchten, ziehen Sie das Steuerelement der weißen Kurve auf parallel zur X-Achse.

![Schaltflächen-3D-Soundeinstellungen](images/spatial-audio/spatial-audio-02-section3-step1-1.png)

## <a name="testing-the-spatialize-audio"></a>Testen der spatialize-Audiodatei

Um die spatialize-Audiodatei im Unity-Editor zu testen, müssen Sie einen Audioclip in der **audioquellkomponente** mit **Schleifen** Option hinzufügen, die für das **PressableButtonHoloLens2** -Objekt aktiviert ist.

Verschieben Sie das **PressableButtonHoloLens2** -Objekt im Wiedergabemodus von links nach rechts, und vergleichen Sie es mit und ohne räumliche Audiodaten auf Ihrer Arbeitsstation. Sie können auch die Einstellungen für die Audioquelle zum Testen ändern, indem Sie Folgendes ausführen:

* Verschieben der **Spatial Blend** -Eigenschaft zwischen 0-1 (2D, nicht räumlich und 3D-spatialized Sound)
* Überprüfen und Deaktivieren der **spatialize** -Eigenschaft

Testen Sie die APP auf hololens 2. In der App können Sie auf die Schaltfläche klicken und die Kontext-Sounds für räumliche Schaltflächen hören.

> [!TIP]
> Falls Sie eine Auffrischung zum Erstellen und Bereitstellen Ihres Unity-Projekts auf HoloLens 2 benötigen, lesen Sie die Anweisungen unter [Erstellen Ihrer App auf dem HoloLens 2-Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie gelernt, den Schaltflächen-Interaktions Sound zu verräumlichen und einen Audioclip zu verwenden, um eine räumliche Schaltflächen Interaktion zu testen. Im nächsten Tutorial erfahren Sie, wie Sie Audiodaten aus einer Videoquelle spatialisieren.

> [!div class="nextstepaction"]
> [Nächstes Tutorial: 3. spatialisieren von Audiodaten aus einem Video](unity-spatial-audio-ch3.md)
