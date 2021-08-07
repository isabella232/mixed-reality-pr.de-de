---
title: 'Tutorials zu räumlichen Audioinhalten: 2. Versehen von Sounds für die Schaltflächeninteraktion mit räumlichen Effekten'
description: Fügen Sie ihrem Projekt eine Schaltfläche hinzu, und raumisieren Sie die Schaltflächeninteraktionsgeräusche.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens2, räumliche Audiodaten, MRTK, Mixed Reality-Toolkit, UWP, Windows 10, HRTF, kopfbezogene Übertragungsfunktion, Hall, Microsoft Spatializer, Prefabs, Volumekurve
ms.openlocfilehash: e0f916ecf8cd8da81e0738b082021c76c55a7f2031517a37b959575e1b21ce16
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209837"
---
# <a name="2-spatializing-button-interaction-sounds"></a>2. Versehen von Sounds für die Schaltflächeninteraktion mit räumlichen Effekten

## <a name="overview"></a>Überblick

In diesem Tutorial erfahren Sie, wie Sie die Schaltflächeninteraktionsgeräusche raumisieren und wie Sie einen Audioclip verwenden, um die Interaktion mit räumlichen Schaltflächen zu testen.  

## <a name="objectives"></a>Ziele

* Hinzufügen und Raumisieren der Schaltflächenklick-Sounds

## <a name="add-a-button"></a>Hinzufügen einer Schaltfläche

Wählen Sie zum Hinzufügen des Schaltflächen-Prefabs **Project** Fenster Pakete aus, und geben Sie in der Suchleiste "PressableButtonHoloLens2" ein. 

![Schaltflächen-Prefab in Assets](images/spatial-audio/spatial-audio-02-section1-step1-1.PNG)

Das Schaltflächen-Prefab ist der Eintrag, der durch ein blaues Symbol dargestellt wird. Klicken Sie auf das **Prefab PressableButtonHoloLens2,** und ziehen Sie es in die Hierarchie. Wenn das **PressableButtonHoloLens2-Objekt** noch ausgewählt ist, konfigurieren Sie im Inspektorfenster die **Komponente Transformieren** wie folgt:

* **Position:** X = 0, Y = -0,4, Z = 2
* **Drehung**: X = 0, Y = 0, Z = 0
* **Skalierung**: X = 1, Y = 1, Z = 1

![Schaltflächentransformation](images/spatial-audio/spatial-audio-02-section1-step1-2.PNG)

Um sich auf die Objekte in der Szene zu konzentrieren, können Sie auf das **PressableButtonHoloLens2-Objekt** doppelklicken und dann wieder etwas vergrößern:

## <a name="spatialize-button-feedback"></a>Feedback zur Schaltfläche "Spatialize"

In diesem Schritt raumisieren Sie das Audiofeedback für die Schaltfläche. Entsprechende Entwurfsvorschläge finden Sie unter [Entwurf von Raumklang.](../../../design/spatial-sound-design.md)

Im Fenster **Audio Mixer** definieren Sie Ziele mit dem Namen Mixer **Gruppen für** die Audiowiedergabe von **Audioquellenkomponenten.**

Um das Fenster **Audio Mixer** öffnen, wählen Sie im Unity-Menü Die Option Audioaudiofenster  >    >  **Mixer:** ![ Audiofenster Mixer öffnen aus.](images/spatial-audio/spatial-audio-02-section2-step1-1.PNG)

 Erstellen Sie **eine Mixer,** indem Sie auf das "+" neben **Mixer klicken** und einen geeigneten Namen für die Mixer eingeben, z. B. Spatial _Audio Mixer._ Der neue Mixer enthält eine Standardgruppe **namens** **Master**.

![Mixer mit erstem Mixer](images/spatial-audio/spatial-audio-02-section2-step1-2.PNG)

> [!NOTE]
> Bis hall in [5th Chapter: Using reverb](unity-spatial-audio-ch5.md)to add distance to spatial audio ,the mixer volume meter doesn't show activity for sounds played through the Microsoft Spatializer

Wählen Sie im Hierarchiefenster **pressableButtonHoloLens2** aus, suchen Sie dann im Inspektorfenster nach der Komponente **Audioquelle,** und konfigurieren Sie die Komponente Audioquelle wie folgt:

1. Klicken Sie **für die Eigenschaft** Ausgabe auf den Selektor, und wählen Sie die Mixer aus, die Sie erstellt haben. 
2. Aktivieren Sie **das Kontrollkästchen Spatialize** .
3. Verschieben Sie den **Schieberegler Spatial Blend** in 3D (1).

![Schaltflächenaudioquelle](images/spatial-audio/spatial-audio-02-section2-step1-3.PNG)

> [!NOTE]
> Wenn Sie **Spatial Blend** auf 1 (3D) verschieben, ohne das Kontrollkästchen **Spatialize** zu aktivieren, verwendet Unity den schwenkenden Spatializer anstelle des Microsoft **Spatializers** mit HRTFs.

## <a name="adjust-the-volume-curve"></a>Anpassen der Volumekurve

Standardmäßig dämpft Unity räumliche Sounds, wenn sie weiter vom Listener entfernt sind. Wenn diese Dämpfung auf Interaktionsfeedback-Sounds angewendet wird, kann die Verwendung der Schnittstelle schwieriger werden.

Um diese Dämpfung zu deaktivieren, müssen Sie die **Volumekurve** in der **Komponente Audioquelle** anpassen.

Wählen Sie im Hierarchiefenster **pressableButtonHoloLens2** aus, navigieren Sie dann im Inspektorfenster zu **Audio Source**  >  **3D Sound Einstellungen** and Configure wie folgt:

1. Legen Sie die **Eigenschaft Volumerolloff** auf Linear Rolloff fest.
2. Ziehen Sie den Endpunkt auf der **Volumekurve** (die rote Kurve) von "0" auf der y-Achse auf "1".
3. Um die Form  der Volumekurve so anzupassen, dass sie flach ist, ziehen Sie das Shape-Steuerelement der weißen Kurve so, dass es parallel zur X-Achse ist.

![3D-Soundeinstellungen der Schaltfläche](images/spatial-audio/spatial-audio-02-section3-step1-1.PNG)

## <a name="testing-the-spatialize-audio"></a>Testen des Spatialize-Audios

Zum Testen des Spatialize-Audios im Unity-Editor müssen Sie der **Audioquelle-Komponente** einen Audioclip hinzufügen, bei dem die Option **Loop** im **PressableButtonHoloLens2-Objekt eincheckt** ist.

Verschieben Sie im Wiedergabemodus das **PressableButtonHoloLens2-Objekt** von links nach rechts, und vergleichen Sie es mit und ohne aktiviertes räumliches Audio auf Ihrer Arbeitsstation. Sie können die Einstellungen der Audioquelle für Tests auch wie im folgenden Beispiel ändern:

* Verschieben der **Spatial Blend-Eigenschaft** zwischen 0 und 1 (nicht räumlicher 2D- und 3D-Raumklang)
* Überprüfen und Deaktivieren der **Spatialize-Eigenschaft**

Testen Sie die App auf HoloLens 2. In der App können Sie auf die Schaltfläche klicken und die Interaktionsgeräusche der räumlichen Schaltfläche hören.

> [!TIP]
> Falls Sie eine Auffrischung zum Erstellen und Bereitstellen Ihres Unity-Projekts auf HoloLens 2 benötigen, lesen Sie die Anweisungen unter [Erstellen Ihrer App auf dem HoloLens 2-Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie gelernt, die Schaltflächeninteraktionsgeräusche zu raumisieren und einen Audioclip zu verwenden, um die Interaktion mit räumlichen Schaltflächen zu testen. Im nächsten Tutorial erfahren Sie, wie Sie Audiodaten aus einer Videoquelle spatialisieren.

> [!div class="nextstepaction"]
> [Nächstes Tutorial: 3. Räumliches Verwenden von Audiodaten aus einem Video](unity-spatial-audio-ch3.md)
