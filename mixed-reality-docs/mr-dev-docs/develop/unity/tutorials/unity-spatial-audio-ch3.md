---
title: 'Tutorials zu räumlichen Audioinhalten: 3. Versehen des Audiosignals eines Videoclips mit räumlichen Effekten'
description: Importieren Sie ein Videoobjekt in Ihr Unity-Projekt, und spatialisieren Sie die Audiodaten aus dem Video.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens2, räumliche Audiodaten, MRTK, Mixed Reality-Toolkit, UWP, Windows 10, HRTF, kopfbezogene Übertragungsfunktion, Hall, Microsoft Spatializer, Videoimport, Videoplayer
ms.openlocfilehash: 2926301aac9db67d3e72b0511600720c24e5965f52a23faa1230c381a47c9b90
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202896"
---
# <a name="3-spatializing-audio-from-a-video"></a>3. Versehen des Audiosignals eines Videoclips mit räumlichen Effekten

## <a name="overview"></a>Überblick

In diesem Tutorial erfahren Sie, wie Sie Audiodaten aus einer Videoquelle räumlichisieren und im Unity-Editor und im HoloLens 2 testen.

## <a name="objectives"></a>Ziele

* Importieren eines Videos und Hinzufügen eines Videoplayers
* Wiedergeben des Videos auf einem Quadrangle
* Weiterleiten von Audiodaten aus dem Video an das Quadrangle und RäumlichesIsieren der Audiodaten

## <a name="import-a-video-and-add-a-video-player-to-the-scene"></a>Importieren eines Videos und Hinzufügen eines Videoplayers zur Szene

In diesem Tutorial können Sie [dieses Video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) aus dem Beispielprojekt für räumliche Audiodaten verwenden.

So importieren Sie Video in das Unity-Projekt. Wählen Sie im Unity-Menü **AssetImport**  >  New Asset Importing Asset **(Asset importieren neues Medienobjekt** 
 ![ importieren) aus.](images/spatial-audio/spatial-audio-03-section1-step1-1.PNG)

Wählen Sie im Fenster **Neues Medienobjekt importieren...** die heruntergeladene Datei **Microsoft HoloLens - Spatial Sound-PTPvx7mDon4** aus, und klicken Sie auf die Schaltfläche **Öffnen,** um das Medienobjekt in das Projekt zu importieren:

![Auswählen des Medienobjekts](images/spatial-audio/spatial-audio-03-section1-step1-2.PNG)

Das Anpassen der Qualitätseinstellungen für den Videoclip kann eine reibungslose Wiedergabe auf HoloLens 2 sicherstellen. Wählen Sie die Videodatei im **fenster Project** aus, und setzen Sie im Inspektorfenster der Videodatei die Einstellungen für **Windows Store Apps** **außer Kraft,** und:

* **Transcode** aktivieren
* Codec  auf H264 festlegen
* Festlegen **des Bitratenmodus** auf Niedrig
* Festlegen **der räumlichen Qualität** auf "Mittlere räumliche Qualität"

Klicken Sie nach diesen Anpassungen auf Übernehmen, um die Qualitätseinstellung für den Videoclip zu ändern.

![Änderung der Videoeigenschaft](images/spatial-audio/spatial-audio-03-section1-step1-3.PNG)

Klicken Sie mit der rechten Maustaste auf die Hierarchie, wählen Sie **Video**  >  **Video Player** aus, um die Videoplayerkomponente hinzuzufügen.

![Hinzufügen eines Videoplayers](images/spatial-audio/spatial-audio-03-section1-step1-4.PNG)

## <a name="play-video-onto-a-quadrangle"></a>Video auf einem Quadrangle wiedergeben

Das **Video Player-Objekt** benötigt ein texturiertes Spielobjekt, um das Video zu rendern.

Klicken Sie mit der rechten Maustaste auf hierarchie , wählen Sie **3D Object**  >  **Quad** aus, um ein Quader zu erstellen, und konfigurieren Sie seine **Transformationskomponente** wie folgt:

* **Position:** X = 0, Y = 0, Z = 2
* **Drehung**: X = 0, Y = 0, Z = 0
* **Skalierung:** X = 1,28, Y = 0,72, Z = 1

![Hinzufügen eines Quaders](images/spatial-audio/spatial-audio-03-section2-step1-1.PNG)

Nun müssen Sie das **Quad-Element** mit dem Video texturen. Klicken Sie im **Fenster Project** mit der rechten Maustaste, und wählen **Sie**  >  **Rendertextur** erstellen aus, um eine Rendertexturkomponente zu erstellen. Geben Sie einen geeigneten Namen für die Rendertextur ein, z. B. _Räumliche Audiotextur:_

![Erstellen einer Rendertextur](images/spatial-audio/spatial-audio-03-section2-step1-2.PNG)

Wählen Sie die **Rendertextur** aus, und legen Sie im Inspektorfenster die **Eigenschaft Größe** so fest, dass sie der nativen Auflösung des Videos von 1280 x 720 entspricht. Legen Sie dann die **Eigenschaft Tiefenpuffer** auf **mindestens 16 Bits Tiefe** fest, um eine gute Renderingleistung auf HoloLens 2 sicherzustellen.

![Rendern von Textureigenschaften](images/spatial-audio/spatial-audio-03-section2-step1-3.PNG)

Verwenden Sie als Nächstes die erstellte **texturrendere räumliche Audiotextur** als Textur für das **Quad**-Objekt:

1. Ziehen Sie die **Räumliche Audiotextur** aus dem **fenster Project** auf das **Quad** in der Hierarchie, um die Rendertextur zum Quad hinzuzufügen.
2. Um eine gute Leistung auf HoloLens 2 sicherzustellen, wählen Sie quad in der Hierarchie und im Inspektorfenster für Shader den **Mixed Reality Toolkit**  >  **Standard Shader** aus.

![Eigenschaften der Quad-Textur](images/spatial-audio/spatial-audio-03-section2-step1-4.PNG)

Um **VideoPlayer** und **RenderTextur** für die Wiedergabe des Videoclips festzulegen, wählen Sie den **Videoplayer** in der **Hierarchie** und im **Inspektorfenster** aus.

* Legen Sie die **Video Clip-Eigenschaft** auf die heruntergeladene Videodatei "Microsoft HoloLens – Spatial Sound-PTPvx7mDon4" fest.
* Aktivieren Sie das **Kontrollkästchen Schleife.**
* Festlegen der **Zieltextur** auf ihre neue Rendertextur **Räumliche Audiotextur**

![Eigenschaften des Videoplayers](images/spatial-audio/spatial-audio-03-section2-step1-5.PNG)

## <a name="spatialize-the-audio-from-the-video"></a>Spatialize the audio from the video (Räumliches Raumisieren der Audiodaten aus dem Video)

Wählen Sie im Hierarchiefenster **Quad-Objekt** aus, und verwenden Sie dann im Inspektorfenster die Schaltfläche **Komponente hinzufügen,** um die **Audioquelle** hinzuzufügen, an die Sie die Audiodaten aus dem Video weiterleiten.

In der **Audioquelle:**

* Festlegen der **Ausgabe** auf die **Mixer**
* Aktivieren Des **Kontrollkästchens "Spatialize"**
* Verschieben des **Schiebereglers Spatial Blend** auf 1 (3D)

![Inspektor für Quad-Audioquelle](images/spatial-audio/spatial-audio-03-section3-step1-1.PNG)

Um den Videoplayer so festzulegen, dass er seine Audiodaten an die **Audioquelle** weiterleitet, wählen Sie den **Videoplayer** im Hierarchiefenster und im Video Player-Objekt im Inspektor die folgenden Änderungen aus.

* Festlegen des **Audioausgabemodus** auf **Audioquelle**
* Legen Sie die **Eigenschaft Audioquelle** auf das **Quad fest.**

![Videoplayer: Festlegen der Audioquelle](images/spatial-audio/spatial-audio-03-section3-step1-2.PNG)

> [!TIP]
> Falls Sie eine Auffrischung zum Erstellen und Bereitstellen Ihres Unity-Projekts auf HoloLens 2 benötigen, lesen Sie die Anweisungen unter [Erstellen Ihrer App auf dem HoloLens 2-Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie gelernt, wie Sie Audiodaten aus einer Videoquelle räumlicher gestalten. Testen Sie Ihre App auf einem HoloLens 2 oder im Unity-Editor. Sie werden das Video sehen und hören, und die Audiodaten aus dem Video werden räumlich verräumlicht.

Im nächsten Tutorial erfahren Sie, wie Sie die Räumliche Darstellung zur Laufzeit aktivieren und deaktivieren.

> [!div class="nextstepaction"]
> [Nächstes Tutorial: 4. Aktivieren und Deaktivieren der Räumlichen Raumisierung zur Laufzeit](unity-spatial-audio-ch4.md)
