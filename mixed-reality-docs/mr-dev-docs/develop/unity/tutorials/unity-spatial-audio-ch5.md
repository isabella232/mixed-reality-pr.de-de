---
title: 'Tutorials zu räumlichen Audioinhalten : 5. Verwenden von Hall zum Hinzufügen von Abstand zu räumlicher Audiowiedergabe'
description: Fügen Sie einen Halleffekt hinzu, um das Gefühl von Abstandsvariationen zu räumlichen Audioinhalten zu verbessern.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, Hololens2, räumliche Audiodaten, MRTK, Mixed Reality-Toolkit, UWP, Windows 10, HRTF, kopfbezogene Übertragungsfunktion, Hall, Microsoft Spatializer, Audiomixer, SFX-Hall
ms.openlocfilehash: 8adc92eb96cb8ebd2cc5fff14d522bcfe72733cc5748183dd6db59d753e12a3e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192973"
---
# <a name="5-using-reverb-to-add-distance-to-spatial-audio"></a>5. Verwenden von Hall zum Hinzufügen von Abstand zu räumlicher Audiowiedergabe

## <a name="overview"></a>Überblick

Im vorherigen Tutorial haben Sie die Raumisierung für die Sounds hinzugefügt, um ihnen ein Gefühl für die Richtung zu geben. In diesem Tutorial fügen Sie einen Halleffekt hinzu, um sounds ein Gefühl der Entfernung zu geben.

## <a name="objectives"></a>Ziele

* Verbessern Sie die wahrgenommene Entfernung von Soundquellen, indem Sie Hall hinzufügen.
* Steuern Sie die wahrgenommene Entfernung des Sounds mithilfe des Abstands des Listeners zum Hologramm.

## <a name="add-a-mixer-group-and-a-reverb-effect"></a>Hinzufügen einer Mixergruppe und eines Halleffekts

Unter [Spatializing button interaction sounds Tutorial (Tutorial: Räumliche Schaltflächeninteraktion)](unity-spatial-audio-ch2.md)haben wir einen Mixer hinzugefügt. Der Mixer enthält standardmäßig eine **Gruppe** namens **Master.** Da wir nur einen Halleffekt auf einige Sounds anwenden möchten, fügen wir eine zweite Gruppe für diese Sounds hinzu. Klicken Sie zum Hinzufügen einer Gruppe mit der rechten Maustaste auf die Gruppe Master im **Mixer** wählen **Sie untergeordnete Gruppe hinzufügen** aus, und geben Sie einen geeigneten Namen ein, z. B. _Room Effect_:

![Hinzufügen einer untergeordneten Gruppe](images/spatial-audio/spatial-audio-05-section1-step1-1.PNG)

Jede **Gruppe** hat einen eigenen Satz von Effekten. Fügen Sie der neuen Gruppe einen Halleffekt hinzu, indem Sie in der neuen Gruppe auf **Hinzufügen...** klicken und **SFX Reverb** auswählen:

![Hinzufügen von SFX Reverb](images/spatial-audio/spatial-audio-05-section1-step1-2.PNG)

In der Audioterminologie wird das ursprüngliche, unerfüllte Audio als _"Dry Path"_ bezeichnet, und die Audiodaten nach dem Filtern mit dem Hallfilter werden als _Vernetzungspfad_ bezeichnet. Beide Pfade werden an die Audioausgabe gesendet, und ihre relativen Stärken in dieser Mischung werden als _Vernetzung/Trockenmischung_ bezeichnet. Die Mischung aus Vernetzung und Heiterkeit wirkt sich stark auf den Abstandssinn aus.

**SFX Reverb** enthält Steuerelemente, mit deren Rahmen die Mischung aus Vernetzung und Trocken innerhalb des Effekts angepasst werden kann. Da das **Microsoft Spatializer-Plug-In** den Dry-Pfad verarbeitet, verwenden wir **SFX Reverb** nur für den Vernetzpfad. Im Bereich Inspector Ihres **SFX Reverb:**

* Legen Sie die Eigenschaft **Dry Level** auf die niedrigste Einstellung (-10.000 mB) fest.
* Legen Sie die **Room-Eigenschaft** auf die höchste Einstellung (0 mB) fest.

![SFX Reverb-Eigenschaften](images/spatial-audio/spatial-audio-05-section1-step1-3.PNG)

Die anderen Einstellungen steuern das Gefühl des simulierten Raums. Die **Verfallszeit** bezieht sich insbesondere auf die wahrgenommene Raumgröße.

## <a name="enable-reverb-on-the-video-playback"></a>Aktivieren des Halles bei der Videowiedergabe

Es gibt zwei Schritte zum Aktivieren des Halles für eine Audioquelle:

* Weiterleiten der **Audioquelle** an die entsprechende **Gruppe**
* Festlegen des Microsoft Spatializer-Plug-Ins zum Übergeben von Audiodaten an die **Gruppe** zur Verarbeitung 

In den folgenden Schritten passen Sie das Skript an, um das Audiorouting zu steuern, und fügen ein Steuerskript an, das mit dem **Microsoft Spatializer-Plug-In** bereitgestellt wird, um Daten in den Hall zu feeden.

Klicken Sie bei ausgewähltem **Quad** in der Hierarchie im Inspektorfenster auf **Komponente hinzufügen,** und fügen Sie die **Room Effect Send Level(Script) hinzu:**

![Hinzufügen eines Skripts für die Sendeebene](images/spatial-audio/spatial-audio-05-section2-step1-1.PNG)

> [!NOTE]
> Sofern Sie das Feature **Room Effect Send Level** des Microsoft Spatializer-Plug-Ins nicht aktivieren, werden keine Audiodaten zur Effektverarbeitung an die Unity-Audio-Engine zurücksenden. 

Die **Komponente Room Effect Send Level** enthält ein Graphsteuerelement, das die Ebene der Audiodaten festlegt, die zur Hallverarbeitung an die Unity-Audio-Engine gesendet werden. Um das Graphsteuerelement zu öffnen, klicken Sie auf die **Raumeffekt-Sendeebene**.  Klicken Sie auf die grüne Kurve, und ziehen Sie sie nach unten, um die Ebene auf etwa -30dB festzulegen:

![Anpassen der Hallkurve](images/spatial-audio/spatial-audio-05-section2-step1-2.PNG)

Als Nächstes können Sie die Auskommentierung der vier kommentierten Zeilen im **SpatializeOnOff-Skript** aufheben. Das Skript sieht nun wie folgt aus:

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

Sobald diese Zeilen auskommentiert sind, werden dem Inspector des **SpatializeOnOff-Skripts** zwei Eigenschaften hinzugefügt. weisen Sie diese im Inspektorfenster der **SpatializeOnOff-Komponente** von **Quad** zu.

Wenn das Quad-Objekt weiterhin in der Hierarchie ausgewählt ist, suchen Sie im Inspektorfenster nach der **Komponente SpatializeOnOff Script** und :

* Legen Sie die **Room Effect Group-Eigenschaft** auf Ihre neue Room Effect-Mixergruppe fest.
* Legen Sie die Eigenschaft **Mastergruppe** auf die Mastermixergruppe fest.

![Spatialize On Off Extended](images/spatial-audio/spatial-audio-05-section2-step1-3.PNG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

Sie haben die Tutorials zu HoloLens 2 räumlichen Audio für Unity abgeschlossen. Testen Sie die App auf einem HoloLens 2 oder Unity. Wenn Sie auf die Schaltfläche in der App klicken, um die Räumliche Bereinigung zu aktivieren, wird das Skript die Audiodaten des Videos an die Raumeffektgruppe weiterleiten, um Hall hinzuzufügen. Beim Wechsel zu Stereo werden die Audiodaten an die Mastergruppe weitergeleitet, und das Hinzufügen von Hall wird vermieden.

> [!TIP]
> Falls Sie eine Auffrischung zum Erstellen und Bereitstellen Ihres Unity-Projekts auf HoloLens 2 benötigen, lesen Sie die Anweisungen unter [Erstellen Ihrer App auf dem HoloLens 2-Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2).
