---
title: 'Tutorials zu räumlichen Audioinhalten : 4. Aktivieren und Deaktivieren räumlicher Audiowiedergabe zur Laufzeit'
description: Verwenden Sie eine Schaltfläche, um die Räumliche Raumisierung von Audio zur Laufzeit zu aktivieren und zu deaktivieren.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, Hololens2, räumliche Audiodaten, MRTK, Mixed Reality-Toolkit, UWP, Windows 10, HRTF, kopfbezogene Übertragungsfunktion, Hall, Microsoft Spatializer
ms.openlocfilehash: 2599e2f360afa4518102ab9535608e9d378264ae87f84a36823d460f934d6a05
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213224"
---
# <a name="4-enabling-and-disabling-spatialization-at-run-time"></a>4. Aktivieren und Deaktivieren der Räumlichen Verräumlicherung zur Laufzeit

## <a name="overview"></a>Überblick

In diesem Tutorial erfahren Sie, wie Sie die Räumliche Darstellung zur Laufzeit aktivieren und deaktivieren und im Unity-Editor und HoloLens 2 testen.

## <a name="objectives"></a>Ziele

* Hinzufügen eines neuen Skripts zum Steuern der Räumlichen Verräumlichkeit für ein Spielobjekt
* Steuern des Skripts für das Spatialisierungssteuerelement über Schaltflächenaktionen

## <a name="add-spatialization-control-script"></a>Hinzufügen eines Skripts für ein Spatialisierungssteuerelement

 Klicken Sie mit der rechten Maustaste in das Fenster Project, und wählen **Sie**  >  **C#-Skript** erstellen aus, um ein neues C#-Skript zu erstellen. Geben Sie einen geeigneten Namen für das Skript ein, z. B. _SpatializeOnOff:_

![Erstellen des Skripts](images/spatial-audio/spatial-audio-04-section1-step1-1.PNG)

Doppelklicken Sie im fenster Project auf das Skript, um es in Visual Studio zu öffnen. Ersetzen Sie den Standardskriptinhalt durch Folgendes:

> [!NOTE]
> Mehrere Zeilen des Skripts werden auskommentiert. Diese Zeilen werden im nächsten Kapitel: Verwenden von Hall zum Hinzufügen von [Abständen zu räumlichen Audiodateien](unity-spatial-audio-ch5.md)nicht auskommentiert.

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
> Um die Spatialisierung zu aktivieren oder zu deaktivieren, passt das Skript nur die **spatialBlend-Eigenschaft** an, sodass die **Spatialization-Eigenschaft** aktiviert bleibt. In diesem Modus wendet Unity weiterhin die **Volumekurve** an. Andernfalls würde der Benutzer die Räumlicherisierung deaktivieren, wenn er weit von der Quelle entfernt ist, würde er die Plötzliche Zunahme des Volumens hören.
> Wenn Sie die Spatialization vollständig deaktivieren möchten, ändern Sie das Skript so, dass auch die boolesche **Spatialization-Eigenschaft** der **SourceObject-Variablen** angepasst wird.

## <a name="attach-your-script-and-drive-it-from-the-button"></a>Fügen Sie Ihr Skript an, und fahren Sie es über die Schaltfläche an.

Wählen  Sie quad in der Hierarchie aus, und verwenden Sie im Inspektorfenster die Schaltfläche Komponente hinzufügen, um **SpatializeOnOff(Script) hinzuzufügen.**

![Hinzufügen eines Skripts zu "Quad"](images/spatial-audio/spatial-audio-04-section2-step1-1.PNG)

Suchen Sie in der Hierarchie **nach PressableButtonHoloLens2**  >  **IconAndText**  >  **TextMeshPro**.

With the **Quad** object still selected in the Hierarchy, in the Inspector window, locate the **Spatialize On Off (Script)** component and Drag and drop **TextMeshPro** Component of the PressableButtonHoloLens2.

![Suchen des PressableButtonHoloLens2-Objekts in der Hierarchie](images/spatial-audio/spatial-audio-04-section2-step1-2.PNG)

Um die Schaltfläche so festzulegen, dass das **SpatializeOnOff-Skript** aufgerufen wird, wenn die Schaltfläche losgelassen wird, müssen Sie das interaktionsfähige Skript konfigurieren.

Wählen Sie im Hierarchiefenster **pressableButtonHoloLens2** aus. Suchen Sie im Inspektorfenster nach der **Komponente Interactable (Script),** und klicken Sie unter Dem OnClick -Ereignis () auf das Symbol + .

* Wenn das **PressableButtonHoloLens2-Objekt** weiterhin im Hierarchiefenster ausgewählt ist, klicken Sie auf das **Quad-Objekt,** und ziehen Sie es aus dem Hierarchiefenster in das leere Feld None **(Object)** des Ereignisses, das Sie gerade hinzugefügt haben, damit das ButtonParent-Objekt auf das Schaltflächenklickereignis von dieser Schaltfläche lauscht:

* Klicken Sie auf die Dropdownliste **No Function** des gleichen Ereignisses. Wählen Sie dann **SpatializeOnOff**  >  **SwapSpatialization ()** aus, um das räumliche Audio zu aktivieren und zu deaktivieren.

![Schaltflächenaktionseinstellungen](images/spatial-audio/spatial-audio-04-section2-step1-3.PNG)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie gelernt, wie Sie die Räumliche Darstellung zur Laufzeit aktivieren und deaktivieren, die App auf einem HoloLens 2 oder im Unity-Editor testen. In der App können Sie jetzt auf die Schaltfläche klicken, um die Räumliche Raumisierung der Audiodaten zu aktivieren und zu deaktivieren.

Im nächsten Tutorial fügen Sie einen Halleffekt hinzu, um Sounds ein Gefühl der Entfernung zu geben.

> [!TIP]
> Falls Sie eine Auffrischung zum Erstellen und Bereitstellen Ihres Unity-Projekts auf HoloLens 2 benötigen, lesen Sie die Anweisungen unter [Erstellen Ihrer App auf dem HoloLens 2-Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

> [!div class="nextstepaction"]
> [Nächstes Tutorial: 5. Verwenden von Hall zum Hinzufügen von Abstand zu räumlichem Audio](unity-spatial-audio-ch5.md)
