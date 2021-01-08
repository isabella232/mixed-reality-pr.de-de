---
title: Aktivieren und Deaktivieren räumlicher Audiowiedergabe zur Laufzeit
description: Erfahren Sie, wie Sie ein c#-Skript schreiben, das eine Schaltfläche verwendet, um die audiospatialisierung zur Laufzeit zu aktivieren und zu deaktivieren.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, hololens2, Spatial Audiodatei, mrtk, Mixed Reality Toolkit, UWP, Windows 10, HRTF, Head-Related Transfer Function, Reverb, Microsoft spatializer
ms.openlocfilehash: eaaf8a05088b5bab674ca11b15b0c63383faa479
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007340"
---
# <a name="enabling-and-disabling-spatialization-at-run-time"></a>Aktivieren und Deaktivieren der Spatialisierung zur Laufzeit

## <a name="objectives"></a>Ziele

In diesem vierten Kapitel gehen Sie wie folgt vor:
* Hinzufügen eines neuen Skripts zum Steuern der Spatialisierung eines Spiel Objekts
* Das spatialization-Steuerelement Skript aus Schaltflächen Aktionen Steuern

## <a name="add-spatialization-control-script"></a>Spatialization-Steuerelement Skript hinzufügen

Klicken Sie mit der rechten Maustaste in den Bereich **Projekt** , und erstellen Sie ein neues c#-Skript, indem Sie **> c#-Skript erstellen** auswählen. Benennen Sie Ihr Skript mit dem Namen "spatializeonoff".

![Erstellen des Skripts](images/spatial-audio/create-script.png)

Doppelklicken Sie im **Projekt** Bereich auf das Skript, um es in Visual Studio zu öffnen. Ersetzen Sie die Standardskript Inhalte durch Folgendes:

> [!NOTE]
> Mehrere Zeilen des Skripts werden auskommentiert. Diese Zeilen werden in [Kapitel 5](unity-spatial-audio-ch5.md)auskommentiert.

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
> Zum Aktivieren oder Deaktivieren der Spatialisierung passt das Skript nur die **spatialblend** -Eigenschaft an, sodass die **spatialization** -Eigenschaft aktiviert ist. In diesem Modus wendet Unity weiterhin die **volumekurve** an. Wenn der Benutzer die räumungszeit bei weitem von der Quelle deaktivieren würde, würde er das Volume plötzlich anwachsen. <br> <br>
> Wenn Sie die spatialization vollständig deaktivieren möchten, ändern Sie das Skript so, dass auch die Eigenschaft **spatialization** booleschen der **SourceObject** -Variablen angepasst wird.

## <a name="attach-your-script-and-drive-it-from-the-button"></a>Fügen Sie das Skript an, und Steuern Sie es über die Schaltfläche

Klicken Sie im Bereich **Inspector** des **Quad** auf **Komponente hinzufügen** , und fügen Sie das Skript **spatialize on off** hinzu:

![Skript zu Quad hinzufügen](images/spatial-audio/add-script-to-quad.png)

Auf der Komponente **spatialize on off** des **Quad**:
1. Suchen Sie den Betreff " **PressableButtonHoloLens2-> iconandtext-> textmeshpro** " in der **Hierarchie**:

![Suchen des PressableButtonHoloLens2-Objekts in der Hierarchie](images/spatial-audio/pressable-button-object.png)

2. Ziehen Sie den Betreff **textmeshpro** auf das Feld **buttontextobject** der Komponente **spatialize on off** .

Nachdem diese Änderungen vorgenommen wurden, sieht die **spatialize on off** -Komponente des **Quad** wie folgt aus:

![Räumliche](images/spatial-audio/spatialize-on-off-basic.png)

Um die Schaltfläche so festzulegen, dass das Skript **spatialize on off** aufgerufen wird, wenn die Schaltfläche losgelassen wird, öffnen Sie den **Inspektor** -Bereich des **PressableButtonHoloLens2** -Objekts, suchen Sie die **interactable** -Komponente und:
1. Suchen Sie den **OnClick ()** -Bereich des Unterabschnitts " **Ereignisse** ".
2. Ziehen Sie den **Quad** aus der- **Hierarchie** in den Zielobjekt Slot.
3. Wählen Sie im Dropdown Feld Aktion die Option **spatializeonoff. tauapspatialization** aus.

Nachdem diese Änderungen vorgenommen wurden, sieht die **interactable** -Komponente wie folgt aus:

![Schaltflächen Aktions Einstellungen](images/spatial-audio/button-action-settings.png)

## <a name="next-steps"></a>Nächste Schritte

Testen Sie Ihre APP auf einem hololens 2 oder im Unity-Editor. In der App können Sie nun auf die Schaltfläche klicken, um die Spatialisierung im Video zu aktivieren und zu deaktivieren. Wenn Sie im Unity-Editor testen, drücken Sie die Leertaste, und Scrollen Sie mit dem Mausrad, um die Hand Simulation zu aktivieren. 

> [!div class="nextstepaction"]
> [Kapitel 5](unity-spatial-audio-ch5.md) 

