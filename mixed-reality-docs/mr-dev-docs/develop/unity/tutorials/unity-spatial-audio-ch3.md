---
title: 'Lernprogramme für räumliche Audiodaten: 3. Versehen des Audiosignals eines Videoclips mit räumlichen Effekten'
description: Importieren Sie ein Video Medienobjekt in Ihr Unity-Projekt, und räumlichen Sie die Audiodaten aus dem Video.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, hololens2, Spatial Audiodatei, mrtk, Mixed Reality Toolkit, UWP, Windows 10, HRTF, Head-Related Transfer Function, Reverb, Microsoft spatializer, Video Import, Video Player
ms.openlocfilehash: 876918c3e886fae6cd2066d84c55a6e158e4c773
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590052"
---
# <a name="3-spatializing-audio-from-a-video"></a>3. Versehen des Audiosignals eines Videoclips mit räumlichen Effekten

## <a name="overview"></a>Übersicht

In diesem Tutorial erfahren Sie, wie Sie Audiodaten aus einer Videoquelle spatialisieren und diese im Unity-Editor und in hololens 2 testen.

## <a name="objectives"></a>Ziele

* Importieren eines Videos und Hinzufügen eines Video Players
* Video auf einem Quadranten abspielen
* Leiten Sie Audiodaten aus dem Video an das Quadrangle weiter, und räumlichen Sie die Audiodaten.

## <a name="import-a-video-and-add-a-video-player-to-the-scene"></a>Importieren eines Videos und Hinzufügen eines Video Players zur Szene

In diesem Tutorial verwenden Sie [dieses Video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) aus dem Beispiel Projekt für räumliche Audiodateien.

Zum Importieren von Videos in das Unity-Projekt. Wählen Sie im Unity-Menü **Asset**  >  **Import New Asset** Import 
 ![ Asset aus.](images/spatial-audio/spatial-audio-03-section1-step1-1.png)

Wählen Sie im Fenster **Neues Asset importieren...** die heruntergeladene **Microsoft hololens-Spatial Sound-PTPvx7mDon4-** Datei aus, und klicken Sie auf die Schaltfläche **Öffnen** , um das Objekt in das Projekt zu importieren:

![Medienobjekt auswählen](images/spatial-audio/spatial-audio-03-section1-step1-2.png)

Durch das Anpassen der Qualitätseinstellungen für den Videoclip kann die reibungslose Wiedergabe auf hololens 2 sichergestellt werden. Wählen Sie die Videodatei im **Projekt** Fenster und im Inspektor-Fenster der Videodatei aus, und über **Schreiben** Sie die Einstellungen für **Windows Store-Apps** und:

* **Transcode** aktivieren
* Legen Sie **Codec** auf H264 fest.
* **Modus "Bitrate** " auf "niedrig" festlegen
* Legen Sie **räumliche Qualität** auf mittlere räumliche Qualität fest.

Nachdem Sie diese Anpassungen vorgenommen haben, klicken Sie auf übernehmen, um die Qualitätseinstellung für den Videoclip zu ändern.

![Video-Eigenschaften Änderung](images/spatial-audio/spatial-audio-03-section1-step1-3.png)

Klicken Sie mit der rechten Maustaste auf die Hierarchie, und wählen Sie **Video**  >  **Video Player** , um die Video Player Komponente

![Video Player hinzufügen](images/spatial-audio/spatial-audio-03-section1-step1-4.png)

## <a name="play-video-onto-a-quadrangle"></a>Abspielen von Videos auf einem Quadranten

Das **Video Player** -Objekt benötigt ein texturiertes Spielobjekt zum Rendering des Videos.

Klicken Sie mit der rechten Maustaste auf die Hierarchie, wählen Sie **3D-Objekt**  >  **Quad** aus, um ein Quad zu erstellen, und konfigurieren Sie die 

* **Position**: X = 0, Y = 0, Z = 2
* **Drehung**: X = 0, Y = 0, Z = 0
* **Skalierung**: X = 1,28, Y = 0,72, Z = 1

![Hinzufügen eines Quad-](images/spatial-audio/spatial-audio-03-section2-step1-1.png)

Nun müssen Sie das Vierfache **mit dem** Video strukturieren. Klicken Sie dazu im **Projekt** Fenster mit der rechten Maustaste, und wählen Sie   >  **Rendering-Textur** erstellen aus, um eine Rendering-Textur Komponente zu erstellen, und geben Sie einen passenden Namen für die Rendering-Textur ein, z.b. _räumliche audiotextur_:

![Rendering-Textur erstellen](images/spatial-audio/spatial-audio-03-section2-step1-2.png)

Wählen Sie die **Rendering-Textur** aus, und legen Sie im Inspektor-Fenster die **size** -Eigenschaft so fest, dass Sie mit der nativen Auflösung des Videos in der Auflösung Um dann eine gute Renderingleistung auf hololens 2 sicherzustellen, legen Sie die **Tiefe Puffer** Eigenschaft auf **mindestens 16 Bits** fest.

![Rendering-Textur Eigenschaften](images/spatial-audio/spatial-audio-03-section2-step1-3.png)

Verwenden Sie als nächstes die erstellte **Darstellung der Struktur** für das **räumliche** Rendering als Textur für das Vierfache:

1. Ziehen Sie die **räumliche audiotextur** aus dem **Projekt** Fenster auf **das Vierfache in der hier** Archie, um die Rendering-Textur dem Quad hinzuzufügen.
2. Um eine gute Leistung bei hololens 2 sicherzustellen, wählen Sie Quad in der Hierarchie aus, und wählen Sie im Inspektor-Fenster für Shader das **Mixed Reality Toolkit**  >  **Standard** -Shader aus.

![Vier Textur Eigenschaften](images/spatial-audio/spatial-audio-03-section2-step1-4.png)

Wählen Sie den **Video Player** in der **Hierarchie** aus **, und klicken** Sie im **Inspektor** - **Fenster auf**

* Legen Sie die Eigenschaft " **Video Clip** " auf die heruntergeladene Videodatei "Microsoft hololens-Spatial Sound-PTPvx7mDon4" fest.
* Aktivieren Sie das Kontrollkästchen **Schleife** .
* Legen Sie die **Ziel Textur** auf die neue Darstellung der gentexgenräumlichen Darstellung fest 

![Video Player-Eigenschaften](images/spatial-audio/spatial-audio-03-section2-step1-5.png)

## <a name="spatialize-the-audio-from-the-video"></a>Spatialisieren der Audiodaten aus dem Video

Wählen Sie im Fenster Hierarchie die Option **Quad** Object aus, und verwenden Sie dann im Inspektor-Fenster die Schaltfläche **Komponente hinzufügen** , um **Audioquelle** hinzuzufügen, an die Sie die Audiodaten aus dem Video weiterleiten.

In der **Audioquelle**:

* Festlegen der **Ausgabe** auf den **räumlichen Audiomixer**
* Aktivieren Sie das Feld **spatialize** .
* Verschieben Sie den Schieberegler für **räumliche Blend** auf 1 (3D).

![Quad-audioquellinspektor](images/spatial-audio/spatial-audio-03-section3-step1-1.png)

Um den Video Player so festzulegen, dass seine Audiodaten an die **Audioquelle** weitergeleitet werden, wählen Sie im Fenster Hierarchie den **Video Player** aus, und führen Sie im inspektorobjekt im Inspektor die folgenden Änderungen aus.

* Festlegen des **Audioausgabemodus** auf **Audioquelle**
* Legen Sie die Eigenschaft **Audioquelle** auf **Quad** fest.

![Video Player-Audioquelle festlegen](images/spatial-audio/spatial-audio-03-section3-step1-2.png)

> [!TIP]
> Falls Sie eine Auffrischung zum Erstellen und Bereitstellen Ihres Unity-Projekts auf HoloLens 2 benötigen, lesen Sie die Anweisungen unter [Erstellen Ihrer App auf dem HoloLens 2-Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie gelernt, wie Sie Audiodaten aus einer Videoquelle eingrenzen, indem Sie Ihre APP auf einem hololens 2 oder im Unity-Editor testen. Sie sehen und hören das Video, und die Audiodaten aus dem Video sind räumlich.

Im nächsten Tutorial erfahren Sie, wie Sie die Spatialisierung zur Laufzeit aktivieren und deaktivieren.

> [!div class="nextstepaction"]
> [Nächstes Tutorial: 4. aktivieren und Deaktivieren der Spatialisierung zur Laufzeit](unity-spatial-audio-ch4.md)
