---
title: 'Lernprogramme für räumliche Audiodaten: 4. Aktivieren und Deaktivieren räumlicher Audiowiedergabe zur Laufzeit'
description: Verwenden Sie eine Schaltfläche, um die Spatialisierung von Audiodaten zur Laufzeit zu aktivieren und zu deaktivieren.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, hololens2, Spatial Audiodatei, mrtk, Mixed Reality Toolkit, UWP, Windows 10, HRTF, Head-Related Transfer Function, Reverb, Microsoft spatializer
ms.openlocfilehash: 9239c45efa5196b94fe2e05f85a2e83df6c7789f
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/19/2021
ms.locfileid: "98578315"
---
# <a name="4-enabling-and-disabling-spatialization-at-run-time"></a>4. aktivieren und Deaktivieren der Spatialisierung zur Laufzeit

## <a name="overview"></a>Übersicht

In diesem Tutorial erfahren Sie, wie Sie die Spatialisierung zur Laufzeit aktivieren und deaktivieren und im Unity-Editor und in hololens 2 testen.

## <a name="objectives"></a>Ziele

* Hinzufügen eines neuen Skripts zum Steuern der Spatialisierung eines Spiel Objekts
* Das spatialization-Steuerelement Skript aus Schaltflächen Aktionen Steuern

## <a name="add-spatialization-control-script"></a>Spatialization-Steuerelement Skript hinzufügen

 Klicken Sie mit der rechten Maustaste in das Projekt Fenster, und wählen Sie  >  **c#-Skript** erstellen aus, um ein neues c#-Skript zu erstellen. Geben Sie einen passenden Namen für das Skript ein, z.b. _spatializeonoff_:

![Erstellen des Skripts](images/spatial-audio/spatial-audio-04-section1-step1-1.png)

Doppelklicken Sie im Projektfenster auf das Skript, um es in Visual Studio zu öffnen. Ersetzen Sie die Standardskript Inhalte durch Folgendes:

> [!NOTE]
> Mehrere Zeilen des Skripts werden auskommentiert. Diese Zeilen werden im [nächsten Kapitel auskommentiert: Verwenden von "Reverb" zum Hinzufügen von Distanz zu räumlichen Audiodaten](unity-spatial-audio-ch5.md).

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    //public AudioMixerGroup RoomEffectGroup;
    //public AudioMixerGroup MasterGroup;

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
        //m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        //m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

> [!NOTE]
> Zum Aktivieren oder Deaktivieren der Spatialisierung passt das Skript nur die **spatialblend** -Eigenschaft an, sodass die **spatialization** -Eigenschaft aktiviert ist. In diesem Modus wendet Unity weiterhin die **volumekurve** an. Wenn der Benutzer die räumungszeit bei weitem von der Quelle deaktivieren würde, würde er das Volume plötzlich anwachsen.
> Wenn Sie die spatialization vollständig deaktivieren möchten, ändern Sie das Skript so, dass auch die Eigenschaft **spatialization** booleschen der **SourceObject** -Variablen angepasst wird.

## <a name="attach-your-script-and-drive-it-from-the-button"></a>Fügen Sie das Skript an, und Steuern Sie es über die Schaltfläche

Wählen Sie in der Hierarchie **Quad** aus, und verwenden Sie im Inspektor-Fenster die Schaltfläche Komponente hinzufügen, um **spatializeonoff (Script)** hinzuzufügen.

![Skript zu Quad hinzufügen](images/spatial-audio/spatial-audio-04-section2-step1-1.png)

Suchen Sie in der Hierarchie nach **PressableButtonHoloLens2**  >  **iconandtext**  >  **textmeshpro**.

Wenn das **Quad** -Objekt in der Hierarchie noch ausgewählt ist, suchen Sie im Inspektor-Fenster die Komponente " **spatialize on off (Script)** ", und ziehen Sie die **textmeschpro** -Komponente von "PressableButtonHoloLens2" per Drag & Drop.

![Suchen des PressableButtonHoloLens2-Objekts in der Hierarchie](images/spatial-audio/spatial-audio-04-section2-step1-2.png)

Um die Schaltfläche festzulegen, um das **spatializeonoff** -Skript aufzurufen, wenn die Schaltfläche losgelassen wird, müssen Sie das Interaktionen-Skript konfigurieren.

Wählen Sie im Fenster Hierarchie den **PressableButtonHoloLens2** aus. Suchen Sie im Inspektor-Fenster die Komponente **interactable (Script)** , und klicken Sie unter dem OnClick ()-Ereignis auf das Symbol +.

* Wenn das **PressableButtonHoloLens2** -Objekt noch im Fenster Hierarchie ausgewählt ist, klicken Sie auf-und-ziehen Sie das **Quad** -Objekt aus dem Fenster Hierarchie in das leere Feld **None (Objekt)** des soeben hinzugefügten Ereignisses, damit das buttonparent-Objekt über diese Schaltfläche auf das Click-Ereignis der Schaltfläche lauschen kann:

* Klicken Sie auf die Dropdownliste **No Function** des gleichen Ereignisses. Wählen Sie dann **spatializeonoff**  >  -**Austausch-/apspatialization ()** aus, um das räumliche Audiogerät zu aktivieren und zu deaktivieren

![Schaltflächen Aktions Einstellungen](images/spatial-audio/spatial-audio-04-section2-step1-3.png)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie erfahren, wie Sie die Spatialisierung zur Laufzeit aktivieren und deaktivieren, die APP auf einem hololens 2 oder im Unity-Editor testen. In der App können Sie nun auf die Schaltfläche klicken, um die Spatialisierung der Audiodatei zu aktivieren und zu deaktivieren.

Im nächsten Tutorial fügen Sie einen "Hall Effekt" hinzu, um Klänge einen Eindruck von der Entfernung zu geben.

> [!TIP]
> Falls Sie eine Auffrischung zum Erstellen und Bereitstellen Ihres Unity-Projekts auf HoloLens 2 benötigen, lesen Sie die Anweisungen unter [Erstellen Ihrer App auf dem HoloLens 2-Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

> [!div class="nextstepaction"]
> [Nächstes Tutorial: 5. Verwenden von "Reverb" zum Hinzufügen von Distanz zu räumlichen Audiodaten](unity-spatial-audio-ch5.md)
