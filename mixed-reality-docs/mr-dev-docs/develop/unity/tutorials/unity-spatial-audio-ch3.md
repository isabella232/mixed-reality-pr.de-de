---
title: 'Tutorials zu räumlichen Audioinhalten : 3. Versehen des Audiosignals eines Videoclips mit räumlichen Effekten'
description: Importieren Sie ein Video-Asset in Ihr Unity-Projekt, und raumisieren Sie die Audiodaten aus dem Video.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens2, räumliche Audiodaten, MRTK, Mixed Reality-Toolkit, UWP, Windows 10, HRTF, kopfbezogene Übertragungsfunktion, Hall, Microsoft Spatializer, Videoimport, Videoplayer
ms.openlocfilehash: 60b70fc3b7f49f5b39138a218f93c0b37f29b9d9
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712878"
---
# <a name="3-spatializing-audio-from-a-video"></a>3. Versehen des Audiosignals eines Videoclips mit räumlichen Effekten

## <a name="overview"></a>Übersicht

In diesem Tutorial erfahren Sie, wie Sie Audiodaten aus einer Videoquelle raumisieren und im Unity-Editor und im HoloLens 2.

## <a name="objectives"></a>Ziele

* Importieren eines Videos und Hinzufügen eines Videoplayers
* Wiedergabe des Videos auf einem Quadrangle
* Audiodaten aus dem Video an den Quadrangle weiter routen und die Audiodatei raumisieren

## <a name="import-a-video-and-add-a-video-player-to-the-scene"></a>Importieren eines Videos und Hinzufügen eines Videoplayers zur Szene

Verwenden Sie für dieses Tutorial Sie können dieses [Video aus dem](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) Beispielprojekt für räumliche Audioinhalte verwenden.

So importieren Sie Video in das Unity-Projekt. Wählen Sie im Unity-Menü **Asset Import** New Asset  >  Importing Asset (Asset **importieren, neues Asset** 
 ![ importieren) aus.](images/spatial-audio/spatial-audio-03-section1-step1-1.PNG)

Wählen Sie im Fenster Neues Asset **importieren...** die heruntergeladene Datei **Microsoft HoloLens – Spatial Sound-PTPvx7mDon4** aus, und klicken Sie auf die Schaltfläche Öffnen, um das Asset in das Projekt zu importieren: 

![Auswählen des Assets](images/spatial-audio/spatial-audio-03-section1-step1-2.PNG)

Durch Anpassen der Qualitätseinstellungen für den Videoclip kann eine reibungslose Wiedergabe auf HoloLens 2. Wählen Sie die Videodatei im Fenster **Projekt** **aus,** und überschreiben Sie im Inspektorfenster der Videodatei die Einstellungen für **Windows Store-Apps** und:

* Aktivieren **von Transcodierung**
* Legen Sie **Codec** auf H264 fest.
* Festlegen **des Bitratenmodus auf** "Niedrig"
* Legen **Sie spatial quality (Räumliche Qualität)** auf Medium Spatial Quality (Mittlere räumliche Qualität) fest.

Klicken Sie nach diesen Anpassungen auf Übernehmen, um die Qualitätseinstellung für den Videoclip zu ändern.

![Änderung der Videoeigenschaft](images/spatial-audio/spatial-audio-03-section1-step1-3.PNG)

Klicken Sie mit der rechten Maustaste auf die Hierarchie, und wählen **Sie Video** Video  >  **Player aus,** um die Komponente Videoplayer hinzuzufügen.

![Hinzufügen eines Videoplayers](images/spatial-audio/spatial-audio-03-section1-step1-4.PNG)

## <a name="play-video-onto-a-quadrangle"></a>Video auf einem Quadrangle wieder abspielen

Das **Video Player-Objekt** benötigt ein texturiertes Spielobjekt, um das Video zu rendern.

Klicken Sie mit der rechten Maustaste auf die Hierarchie, wählen Sie **3D Object** Quad aus, um ein Quad zu erstellen, und konfigurieren Sie die  >   **Transformationskomponente** wie folgt:

* **Position:** X = 0, Y = 0, Z = 2
* **Drehung**: X = 0, Y = 0, Z = 0
* **Skalierung:** X = 1,28, Y = 0,72, Z = 1

![Hinzufügen eines Quads](images/spatial-audio/spatial-audio-03-section2-step1-1.PNG)

Nun müssen Sie das Quad mit dem  Video texturieren. Klicken Sie im Fenster Projekt mit der rechten Maustaste, und wählen Sie Rendertextur erstellen aus, um eine Rendertexturkomponente zu erstellen. Geben Sie einen geeigneten Namen für die Rendertextur ein, z. B. Spatial Audio   >   _Texture_:

![Rendertextur erstellen](images/spatial-audio/spatial-audio-03-section2-step1-2.PNG)

Wählen Sie **die Rendertextur aus,** und legen Sie im Inspektorfenster die **Eigenschaft Größe** so fest, dass sie mit der nativen Auflösung des Videos von 1280 x 720 übereinstimmen soll. Legen Sie dann die Eigenschaft Tiefenpuffer auf mindestens  **16** Bits fest, um eine gute Renderingleistung für HoloLens 2 sicherzustellen.

![Rendertextureigenschaften](images/spatial-audio/spatial-audio-03-section2-step1-3.PNG)

Verwenden Sie als Nächstes die erstellte Textur render Texture **Spatial Audio Texture** (Räumliche Audiotextur der Rendertextur) als Textur für **das Quad-Objekt:**

1. Ziehen Sie die **Textur für räumliche Audiodaten** aus dem **Projektfenster** auf das **Quad** in der Hierarchie, um die Rendertextur dem Quad-Objekt hinzuzufügen.
2. Um eine gute Leistung auf HoloLens 2 sicherzustellen, wählen Sie in der Hierarchie Quad und im Inspektorfenster für Shader den Mixed Reality **Toolkit**  >  **Standard** Shader aus.

![Eigenschaften der Quad-Textur](images/spatial-audio/spatial-audio-03-section2-step1-4.PNG)

Wählen Sie zum **Festlegen von VideoPlayer** und **Rendertextur**  für die Wiedergabe des Videoclips den **Videoplayer** in der Hierarchie und im **Inspektorfenster** aus.

* Legen Sie **die Video Clip-Eigenschaft** auf die heruntergeladene Videodatei "Microsoft HoloLens – Spatial Sound-PTPvx7mDon4" fest.
* Aktivieren Sie das **Kontrollkästchen Schleife.**
* Festlegen **der Zieltextur** auf ihre neue Rendertextur **für räumliche Audiotextur**

![Videoplayereigenschaften](images/spatial-audio/spatial-audio-03-section2-step1-5.PNG)

## <a name="spatialize-the-audio-from-the-video"></a>Raumisieren der Audiodaten aus dem Video

Wählen Sie im Hierarchiefenster **Quad** object (Quad-Objekt) aus, und verwenden Sie dann im Inspektorfenster die Schaltfläche Add **Component** (Komponente hinzufügen), um audio **source (Audioquelle)** hinzuzufügen, an die Sie die Audiodaten aus dem Video routen.

In der **Audioquelle:**

* Festlegen **der Ausgabe** auf den **Raumaudiomixer**
* Aktivieren des **Kontrollkästchens Spatialize**
* Verschieben des **Schiebereglers "Spatial Blend"** auf 1 (3D)

![Inspektor für Quad-Audioquellen](images/spatial-audio/spatial-audio-03-section3-step1-1.PNG)

Um den VideoPlayer so zu festlegen, dass seine Audiodaten an die **Audioquelle** geroutet werden, wählen Sie **den Videoplayer** im Hierarchiefenster aus, und nehmen Sie im Videoplayerobjekt im Inspector die folgenden Änderungen vor.

* Festlegen des **Audioausgabemodus auf** **Audioquelle**
* Legen Sie die **Eigenschaft Audioquelle** auf quad **fest.**

![Videoplayer: Festlegen der Audioquelle](images/spatial-audio/spatial-audio-03-section3-step1-2.PNG)

> [!TIP]
> Falls Sie eine Auffrischung zum Erstellen und Bereitstellen Ihres Unity-Projekts auf HoloLens 2 benötigen, lesen Sie die Anweisungen unter [Erstellen Ihrer App auf dem HoloLens 2-Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie gelernt, wie Sie Audiodaten aus einer Videoquelle spatialisieren. Testen Sie Ihre App auf einer HoloLens 2 oder im Unity-Editor. Sie sehen und hören das Video, und die Audiodaten aus dem Video sind räumlich.

Im nächsten Tutorial erfahren Sie, wie Sie die Räumliche Raumung zur Laufzeit aktivieren und deaktivieren.

> [!div class="nextstepaction"]
> [Nächstes Tutorial: 4. Aktivieren und Deaktivieren der Räumlichen Anordnung zur Laufzeit](unity-spatial-audio-ch4.md)
