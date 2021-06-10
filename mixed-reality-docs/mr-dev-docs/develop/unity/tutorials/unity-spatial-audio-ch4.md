---
title: 'Tutorials zu räumlichen Audioinhalten : 4. Aktivieren und Deaktivieren räumlicher Audiowiedergabe zur Laufzeit'
description: Verwenden Sie eine Schaltfläche zum Aktivieren und Deaktivieren der Räumlichen Anordnung von Audiodaten zur Laufzeit.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens2, räumliche Audiodaten, MRTK, Mixed Reality-Toolkit, UWP, Windows 10, HRTF, kopfbezogene Übertragungsfunktion, Hall, Microsoft Spatializer
ms.openlocfilehash: 9d0fa432f2e653cdd6820cb6c779cc1acc5c4b15
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712755"
---
# <a name="4-enabling-and-disabling-spatialization-at-run-time"></a>4. Aktivieren und Deaktivieren der Räumlichen Anordnung zur Laufzeit

## <a name="overview"></a>Übersicht

In diesem Tutorial erfahren Sie, wie Sie die Räumliche Raumisierung zur Laufzeit aktivieren und deaktivieren und dies im Unity-Editor und im HoloLens 2.

## <a name="objectives"></a>Ziele

* Hinzufügen eines neuen Skripts zum Steuern der Räumlichen Anordnung für ein Spielobjekt
* Steuern des Spatialization Control-Skripts aus Schaltflächenaktionen

## <a name="add-spatialization-control-script"></a>Hinzufügen eines Skripts für das Spatialization-Steuerelement

 Klicken Sie mit der rechten Maustaste in das Fenster Projekt, und wählen Sie  >  **Create C# Script (C#-Skript** erstellen) aus, um ein neues C#-Skript zu erstellen. Geben Sie einen geeigneten Namen für das Skript ein, z. B. _SpatializeOnOff:_

![Erstellen des Skripts](images/spatial-audio/spatial-audio-04-section1-step1-1.PNG)

Doppelklicken Sie im Fenster Projekt auf das Skript, um es in der Visual Studio. Ersetzen Sie den Standardinhalt des Skripts durch Folgendes:

> [!NOTE]
> Mehrere Zeilen des Skripts werden auskommentiert. Diese Zeilen werden im nächsten Kapitel auskommentiert: Using reverb to add distance to spatial audio (Verwenden von Hall zum Hinzufügen von Abstand [zu räumlichen Audiodaten).](unity-spatial-audio-ch5.md)

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
> Um die Räumliche Raumisierung zu aktivieren oder zu deaktivieren, passt das Skript nur die **spatialBlend-Eigenschaft** an, ohne dass die **Spatialization-Eigenschaft** aktiviert ist. In diesem Modus wendet Unity weiterhin die **Volumekurve** an. Andernfalls würde der Benutzer eine plötzliche Zunahme des Volumens hören, wenn er die Räumliche Benutzeroberfläche weit von der Quelle deaktivieren würde.
> Wenn Sie die Räumliche Vergrößerung vollständig deaktivieren möchten, ändern Sie das Skript, um auch die boolesche **Spatialization-Eigenschaft** der **SourceObject-Variablen** anzupassen.

## <a name="attach-your-script-and-drive-it-from-the-button"></a>Anfügen des Skripts und Ausführen des Laufwerks über die Schaltfläche

Wählen **Sie** quad in der Hierarchie aus, und verwenden Sie im Inspektorfenster die Schaltfläche Add Component (Komponente hinzufügen), um **SpatializeOnOff(Script) hinzuzufügen.**

![Hinzufügen eines Skripts zu "quad"](images/spatial-audio/spatial-audio-04-section2-step1-1.PNG)

Suchen Sie in der **Hierarchie nach PressableButtonHoloLens2**  >  **IconAndText**  >  **TextMeshPro.**

With the **Quad** object still selected in the Hierarchy, in the Inspector window, locate the **Spatialize On Off (Script)** component and Drag and drop **TextMeshPro** Component of the PressableButtonHoloLens2.

![Suchen des PressableButtonHoloLens2-Objekts in der Hierarchie](images/spatial-audio/spatial-audio-04-section2-step1-2.PNG)

Um die Schaltfläche so zu konfigurieren, dass das **SpatializeOnOff-Skript** beim Losgelassen wird, müssen Sie das interaktionsfähige Skript konfigurieren.

Wählen Sie im Hierarchiefenster **pressableButtonHoloLens2 aus.** Suchen Sie im Inspektorfenster die **Komponente Interactable (Script),** und klicken Sie unter dem OnClick ()-Ereignis auf + Symbol.

* Wenn das **PressableButtonHoloLens2-Objekt** noch im Hierarchiefenster ausgewählt  ist, klicken Sie auf das Quad-Objekt aus dem Hierarchiefenster, und ziehen Sie es in das leere Feld None **(Object)** des Ereignisses, das Sie gerade hinzugefügt haben, damit das ButtonParent-Objekt von dieser Schaltfläche auf das Schaltflächenklickereignis lausgt:

* Klicken Sie auf die Dropdownliste **No Function** des gleichen Ereignisses. Wählen Sie dann **SpatializeOnOff**  >  **SwapSpatialization () aus,** um räumliche Audiodaten zu aktivieren und zu deaktivieren.

![Einstellungen für Schaltflächenaktion](images/spatial-audio/spatial-audio-04-section2-step1-3.PNG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie gelernt, wie Sie die Räumliche Raumisierung zur Laufzeit aktivieren und deaktivieren, die App auf einem HoloLens 2 oder im Unity-Editor testen. In der App können Sie jetzt auf die Schaltfläche klicken, um die Raumklangisierung des Audios zu aktivieren und zu deaktivieren.

Im nächsten Tutorial fügen Sie einen Halleffekt hinzu, um Sounds ein Gefühl von Abstand zu geben.

> [!TIP]
> Falls Sie eine Auffrischung zum Erstellen und Bereitstellen Ihres Unity-Projekts auf HoloLens 2 benötigen, lesen Sie die Anweisungen unter [Erstellen Ihrer App auf dem HoloLens 2-Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

> [!div class="nextstepaction"]
> [Nächstes Tutorial: 5. Verwenden von Hall zum Hinzufügen von Abstand zu räumlichen Audiodaten](unity-spatial-audio-ch5.md)
