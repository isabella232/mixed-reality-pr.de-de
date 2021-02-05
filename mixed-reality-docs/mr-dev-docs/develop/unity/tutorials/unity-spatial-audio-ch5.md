---
title: Lernprogramme für räumliche Audiodaten-5. Verwenden von Hall zum Hinzufügen von Abstand zu räumlicher Audiowiedergabe
description: Fügen Sie einen Hall Effekt hinzu, um den Sinn der Abstands Variation zu räumlichem Audiomaterial zu verbessern.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, hololens2, Spatial Audiodatei, mrtk, Mixed Reality Toolkit, UWP, Windows 10, HRTF, Head-Related Transfer Function, Reverb, Microsoft spatializer, Audiomixer, SFX-Reverb
ms.openlocfilehash: f7a5270d969f2e462db0244bd6c68b99347ae1a7
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590722"
---
# <a name="5-using-reverb-to-add-distance-to-spatial-audio"></a>5. Verwenden von Hall zum Hinzufügen von Abstand zu räumlicher Audiowiedergabe

## <a name="overview"></a>Übersicht

Im vorherigen Tutorial haben Sie eine räumliche Struktur hinzugefügt, um Ihnen einen Eindruck von der Richtung in diesem Tutorial zu geben. Sie fügen einen einfügeeffekt hinzu, um Klänge einen Eindruck von der Entfernung zu geben.

## <a name="objectives"></a>Ziele

* Verbessern Sie die wahrgenommene Entfernung von Soundquellen durch Hinzufügen von Reverb
* Steuern Sie den erkannten Abstand des Sounds mithilfe der Entfernung des Listener zum Hologram.

## <a name="add-a-mixer-group-and-a-reverb-effect"></a>Hinzufügen einer mischkeitsgruppe und eines einfügenden Effekts

Im [Tutorial "spatialisieren von Schaltflächen Interaktion Sounds](unity-spatial-audio-ch2.md)" haben wir einen Mixer hinzugefügt. Der Mixer enthält standardmäßig eine **Gruppe** namens **Master**. Da wir nur einen "Hall"-Effekt auf einige Sounds anwenden möchten, fügen wir eine zweite Gruppe für diese Sounds hinzu. Um eine Gruppe hinzuzufügen, klicken Sie mit der rechten Maustaste auf die Master Gruppe im **Audiomixer** , wählen Sie untergeordnete **Gruppe hinzufügen** aus, und geben Sie passenden Namen für Beispiel _Raumeffekt_

![Untergeordnete Gruppe hinzufügen](images/spatial-audio/spatial-audio-05-section1-step1-1.png)

Jede **Gruppe** hat einen eigenen Satz von Effekten. Fügen Sie der neuen Gruppe einen connectoreffekt hinzu, indem Sie in der neuen Gruppe auf **Hinzufügen** klicken, und wählen Sie **SFX-Hall**:

![SFX-Reverb hinzufügen](images/spatial-audio/spatial-audio-05-section1-step1-2.png)

In der audioterminologie wird der ursprüngliche, nicht widerzuhallte _Audiopfad als trockener Pfad_ bezeichnet, und die Audiodatei nach dem Filtern mit dem Hall Filter wird als _Nasser Pfad_ bezeichnet. Beide Pfade werden an die Audioausgabe gesendet, und ihre relativen Stärken in dieser Mischung werden als _nass/trocken Mischung_ bezeichnet. Die nasse/trockene Mischung wirkt sich stark auf den Sinn der Entfernung aus.

Der **SFX-Reverb umfasst Steuer** Elemente, mit denen die nasse/trockene Mischung innerhalb des Effekts angepasst wird. Da das **Microsoft spatializer** -Plug-in den trockenen Pfad behandelt, verwenden wir den **SFX-Reverb** nur für den nassen Pfad. Im inspektorbereich Ihres **SFX-einhall**:

* Legen Sie die Eigenschaft " **Dry Level** " auf die niedrigste Einstellung fest (-10000 MB).
* Legen Sie die **Eigenschaft "Room** " auf die höchste Einstellung (0 MB) fest.

![SFX-Reverb-Eigenschaften](images/spatial-audio/spatial-audio-05-section1-step1-3.png)

Mit den anderen Einstellungen wird das Gefühl des simulierten Raums gesteuert. Die **verwahrzeit** bezieht sich insbesondere auf die wahrgenommene Raum Größe.

## <a name="enable-reverb-on-the-video-playback"></a>Aktivieren von "Reverb" für die Videowiedergabe

Zum Aktivieren von "Reverb" in einer Audioquelle müssen zwei Schritte ausgeführt werden:

* Leiten Sie die **Audioquelle** an die entsprechende **Gruppe** weiter.
* Festlegen des **Microsoft spatializer** -Plug-ins, um Audioinformationen zur Verarbeitung an die **Gruppe** zu übergeben

In den folgenden Schritten passen Sie das Skript an, um das Audiorouting zu steuern, und fügen ein Steuerungs Skript an, das mit dem **Microsoft spatializer** -Plug-in bereitgestellt wird, um Daten in den Reverb zu übertragen

Klicken Sie bei ausgewähltem **Quad** in der Hierarchie im Inspektor-Fenster auf **Komponente hinzufügen** , und fügen Sie die **Sende Ebene des Raum Effekts (Skript)** hinzu:

![Skript für Sende Ebene hinzufügen](images/spatial-audio/spatial-audio-05-section2-step1-1.png)

> [!NOTE]
> Es sei denn, Sie aktivieren das Feature " **Sende Ebene für raumeffekte** " des **Microsoft spatializer** -Plug-ins, es sendet keine Audiodaten an die Unity-Audioengine zur Auswirkung der Verarbeitung.

Die Bereichs Effekt-Komponente der **Sende Ebene** enthält ein Graph-Steuerelement, mit dem die Audioebene festgelegt wird, die für die Verarbeitung von Reverb an die Unity-Audioengine Um das Diagramm Steuerelement zu öffnen, klicken Sie auf die **Sende Ebene des Raum Effekts**.  Klicken und ziehen Sie die grüne Kurve nach unten, um die Ebene auf ungefähr-30dB festzulegen:

![Hall Kurve anpassen](images/spatial-audio/spatial-audio-05-section2-step1-2.png)

Entfernen Sie dann die Auskommentierung der vier kommentierten Zeilen im **spatializeonoff** -Skript. Das Skript sieht nun wie folgt aus:

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    public AudioMixerGroup RoomEffectGroup;
    public AudioMixerGroup MasterGroup;

    private AudioSource m_SourceObject;
    private bool m_IsSpatialized;
    private TMPro.TextMeshPro m_TextMeshPro;

    public void Start()
    {
        m_SourceObject = gameObject.GetComponent<AudioSource>();
        m_TextMeshPro = ButtonTextObject.GetComponent<TMPro.TextMeshPro>();
        SetSpatialized();
    }

    public void SwapSpatialization()
    {
        if (m_IsSpatialized)
        {
            SetStereo();
        }
        else
        {
            SetSpatialized();
        }
    }

    private void SetSpatialized()
    {
        m_IsSpatialized = true;
        m_SourceObject.spatialBlend = 1;
        m_TextMeshPro.SetText("Set Stereo");
        m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

Nachdem diese Zeilen auskommentiert wurden, werden dem Inspektor des **spatializeonoff-Skripts** zwei Eigenschaften hinzugefügt. Weisen Sie diese im Inspektor-Fenster der **spatializeonoff** -Komponente von **Quad** zu.

Wenn das Quad-Objekt in der Hierarchie noch ausgewählt ist, suchen Sie im Inspektor-Fenster die **spatializeonoff-Skript** Komponente und:

* Legen Sie die Eigenschaft " **Raumeffekt** " auf Ihre neue Platz Effekt-mischkeitsgruppe fest.
* Festlegen der **Master Group** -Eigenschaft auf die Master-Mixer-Gruppe

![Spatialize on off (erweitert)](images/spatial-audio/spatial-audio-05-section2-step1-3.png)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben die Lernprogramme "hololens 2 Spatial audiotutorial" für Unity abgeschlossen. Testen Sie die APP auf einem hololens 2 oder Unity. Wenn Sie in der APP auf die Schaltfläche klicken, um die Spatialisierung zu aktivieren, leitet das Skript die Audiodatei an die Raumeffekt Gruppe weiter, um den Code hinzuzufügen. Beim Wechsel zu Stereo wird das Audiomaterial an die Master Gruppe weitergeleitet, und es wird vermieden, dass das Hinzufügen von Reverb erfolgt.

> [!TIP]
> Falls Sie eine Auffrischung zum Erstellen und Bereitstellen Ihres Unity-Projekts auf HoloLens 2 benötigen, lesen Sie die Anweisungen unter [Erstellen Ihrer App auf dem HoloLens 2-Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2).
