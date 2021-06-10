---
title: 'Tutorials zu räumlichen Audioinhalten: 5. Verwenden von Hall zum Hinzufügen von Abstand zu räumlicher Audiowiedergabe'
description: Fügen Sie einen Halleffekt hinzu, um das Gefühl der Entfernungsvariation zu räumlichen Audiodaten zu verbessern.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens2, räumliche Audiodaten, MRTK, Mixed Reality-Toolkit, UWP, Windows 10, HRTF, kopfbezogene Übertragungsfunktion, Hall, Microsoft Spatializer, Audiomixer, SFX-Hall
ms.openlocfilehash: 6f41fe904c21591915e0ef13b61dc6bff04527fe
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712687"
---
# <a name="5-using-reverb-to-add-distance-to-spatial-audio"></a>5. Verwenden von Hall zum Hinzufügen von Abstand zu räumlicher Audiowiedergabe

## <a name="overview"></a>Übersicht

Im vorherigen Tutorial haben Sie die Räumliche Raumisierung für die Sounds hinzugefügt, um ihnen in diesem Tutorial ein Gefühl für die Richtung zu geben. In diesem Tutorial fügen Sie einen Halleffekt hinzu, um Sounds ein Gefühl von Abstand zu geben.

## <a name="objectives"></a>Ziele

* Verbessern Sie den wahrgenommenen Abstand von Soundquellen, indem Sie Hall hinzufügen.
* Steuern Sie den wahrgenommenen Abstand des Sounds mithilfe des Abstands des Listeners zum Hologramm.

## <a name="add-a-mixer-group-and-a-reverb-effect"></a>Hinzufügen einer Mixergruppe und eines Halleffekts

Unter [Spatializing button interaction sounds Tutorial (Tutorial:](unity-spatial-audio-ch2.md)Raumisieren von Schaltflächeninteraktionsgeräuschen) haben wir einen Mixer hinzugefügt. Der Mixer enthält standardmäßig **eine Gruppe** namens **Master.** Da wir nur einen Halleffekt auf einige Sounds anwenden möchten, fügen wir eine zweite Gruppe für diese Sounds hinzu. Klicken Sie zum Hinzufügen einer Gruppe im **Audiomixer** mit der rechten Maustaste auf die Gruppe Master, und wählen Sie untergeordnete Gruppe hinzufügen aus, und geben Sie einen geeigneten Namen ein, z. B. _Room Effect:_ 

![Hinzufügen einer untergeordneten Gruppe](images/spatial-audio/spatial-audio-05-section1-step1-1.PNG)

Jede **Gruppe** hat einen eigenen Satz von Effekten. Fügen Sie der neuen Gruppe einen Halleffekt hinzu, indem Sie in der neuen Gruppe auf **Hinzufügen...** klicken und **SFX Reverb auswählen:**

![Hinzufügen von SFX Reverb](images/spatial-audio/spatial-audio-05-section1-step1-2.PNG)

In der Audioterminologie wird das ursprüngliche, nicht hallierte Audio als "Dry Path" bezeichnet, und das Audio nach dem Filtern mit dem Hallfilter wird als Versauungspfad _bezeichnet._ Beide Pfade werden an die Audioausgabe gesendet, und ihre relativen Stärken in dieser Mischung werden als _versauend/heiter bezeichnet._ Die Versenkungs-/Drymischung wirkt sich stark auf das Gefühl der Entfernung aus.

Der **SFX Reverb enthält** Steuerelemente, um die Versheiterungs-/Probemischung innerhalb des Effekts anzupassen. Da das **Microsoft Spatializer-Plug-In** den Probepfad verarbeitet, verwenden wir **SFX Reverb** nur für den Verwerfungspfad. Im Inspektorbereich Ihres **SFX-Halls:**

* Legen Sie **die Eigenschaft Dry Level** auf die niedrigste Einstellung fest (-10000 mB).
* Legen Sie **die Eigenschaft Room** auf die höchste Einstellung (0 mB) fest.

![SFX Reverb-Eigenschaften](images/spatial-audio/spatial-audio-05-section1-step1-3.PNG)

Die anderen Einstellungen steuern das Verhalten des simulierten Raums. Insbesondere bezieht sich **die Abklingzeit** auf die wahrgenommene Raumgröße.

## <a name="enable-reverb-on-the-video-playback"></a>Aktivieren von Hall bei der Videowiedergabe

Es gibt zwei Schritte, um Hall für eine Audioquelle zu aktivieren:

* Routen der **Audioquelle** an die entsprechende **Gruppe**
* Festlegen des **Microsoft Spatializer-Plug-Ins,** um Audio zur Verarbeitung an die **Gruppe** zu übergeben

In den folgenden Schritten passen Sie das Skript an, um das Audiorouting zu steuern, und fügen ein Steuerungsskript an, das mit dem **Microsoft Spatializer-Plug-In** bereitgestellt wird, um Daten in den Hall zu geben.

Klicken Sie **bei ausgewähltem Quad** in der Hierarchie im Inspektorfenster auf Add **Component** (Komponente hinzufügen), und fügen Sie room Effect **Send Level(Script) hinzu:**

![Hinzufügen eines Skripts auf Sendeebene](images/spatial-audio/spatial-audio-05-section2-step1-1.PNG)

> [!NOTE]
> Sofern Sie das **Room Effect Send Level-Feature** des Microsoft Spatializer-Plug-Ins nicht aktivieren, sendet es keine Audiodaten zur Effektverarbeitung zurück an die Unity-Audio-Engine. 

Die **Komponente Room Effect Send Level** enthält ein Graphsteuerelement, das die Audioebene für die Hallverarbeitung an die Unity-Audio-Engine fest legt. Klicken Sie zum Öffnen des Graph-Steuerelements auf **die Raumeffekt-Sendeebene**.  Klicken Sie auf die grüne Kurve, und ziehen Sie sie nach unten, um die Ebene auf etwa -30dB zu setzen:

![Anpassen der Hallkurve](images/spatial-audio/spatial-audio-05-section2-step1-2.PNG)

Kommentieren Sie als Nächstes die vier kommentierten Zeilen im **SpatializeOnOff-Skript** aus. Das Skript sieht nun wie im folgenden Beispiel aus:

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

Nachdem diese Zeilen auskommentiert wurden, werden dem Inspektor des **SpatializeOnOff-Skripts zwei Eigenschaften hinzufügt.** Weisen Sie diese im Inspektorfenster der **SpatializeOnOff-Komponente** von **Quad zu.**

Wenn das Quad-Objekt in der Hierarchie noch ausgewählt ist, suchen Sie im Inspektorfenster die **SpatializeOnOff-Skriptkomponente** und :

* Legen Sie die **Eigenschaft Room Effect Group** auf Ihre neue Room Effect-Mixergruppe fest.
* Legen Sie die **Eigenschaft Mastergruppe** auf die Mastermixergruppe fest.

![Spatialize On Off Extended](images/spatial-audio/spatial-audio-05-section2-step1-3.PNG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben die Tutorials HoloLens 2 räumliche Audioinhalte für Unity abgeschlossen. Testen Sie die App auf einem HoloLens 2 unity. Wenn Sie in der App auf die Schaltfläche klicken, um die Räumliche Vertonung zu aktivieren, wird das Audio des Videos vom Skript an die Room Effect-Gruppe geroutet, um Hall hinzuzufügen. Wenn Sie zu Stereo wechseln, wird die Audiodatei an die Mastergruppe geroutet, und es wird vermieden, Dass Hall hinzugefügt wird.

> [!TIP]
> Falls Sie eine Auffrischung zum Erstellen und Bereitstellen Ihres Unity-Projekts auf HoloLens 2 benötigen, lesen Sie die Anweisungen unter [Erstellen Ihrer App auf dem HoloLens 2-Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2).
