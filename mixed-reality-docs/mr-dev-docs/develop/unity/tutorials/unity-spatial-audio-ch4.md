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
# <a name="4-enabling-and-disabling-spatialization-at-run-time"></a><span data-ttu-id="79b59-105">4. Aktivieren und Deaktivieren der Räumlichen Anordnung zur Laufzeit</span><span class="sxs-lookup"><span data-stu-id="79b59-105">4. Enabling and disabling spatialization at run time</span></span>

## <a name="overview"></a><span data-ttu-id="79b59-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="79b59-106">Overview</span></span>

<span data-ttu-id="79b59-107">In diesem Tutorial erfahren Sie, wie Sie die Räumliche Raumisierung zur Laufzeit aktivieren und deaktivieren und dies im Unity-Editor und im HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="79b59-107">In this tutorial, you will learn how to Enable and disable spatialization at run time and test this in the unity editor and HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="79b59-108">Ziele</span><span class="sxs-lookup"><span data-stu-id="79b59-108">Objectives</span></span>

* <span data-ttu-id="79b59-109">Hinzufügen eines neuen Skripts zum Steuern der Räumlichen Anordnung für ein Spielobjekt</span><span class="sxs-lookup"><span data-stu-id="79b59-109">Add a new script to control spatialization on a game object</span></span>
* <span data-ttu-id="79b59-110">Steuern des Spatialization Control-Skripts aus Schaltflächenaktionen</span><span class="sxs-lookup"><span data-stu-id="79b59-110">Drive the spatialization control script from button actions</span></span>

## <a name="add-spatialization-control-script"></a><span data-ttu-id="79b59-111">Hinzufügen eines Skripts für das Spatialization-Steuerelement</span><span class="sxs-lookup"><span data-stu-id="79b59-111">Add spatialization control script</span></span>

 <span data-ttu-id="79b59-112">Klicken Sie mit der rechten Maustaste in das Fenster Projekt, und wählen Sie  >  **Create C# Script (C#-Skript** erstellen) aus, um ein neues C#-Skript zu erstellen. Geben Sie einen geeigneten Namen für das Skript ein, z. B. _SpatializeOnOff:_</span><span class="sxs-lookup"><span data-stu-id="79b59-112">Right-click in the Project window and choose **Create** > **C# Script** to create a new C# script, enter a suitable name for the script, for example, _SpatializeOnOff_:</span></span>

![Erstellen des Skripts](images/spatial-audio/spatial-audio-04-section1-step1-1.PNG)

<span data-ttu-id="79b59-114">Doppelklicken Sie im Fenster Projekt auf das Skript, um es in der Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="79b59-114">Double-click the script in the Project window to open it in Visual Studio.</span></span> <span data-ttu-id="79b59-115">Ersetzen Sie den Standardinhalt des Skripts durch Folgendes:</span><span class="sxs-lookup"><span data-stu-id="79b59-115">Replace the default script contents with the following:</span></span>

> [!NOTE]
> <span data-ttu-id="79b59-116">Mehrere Zeilen des Skripts werden auskommentiert. Diese Zeilen werden im nächsten Kapitel auskommentiert: Using reverb to add distance to spatial audio (Verwenden von Hall zum Hinzufügen von Abstand [zu räumlichen Audiodaten).](unity-spatial-audio-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="79b59-116">Several lines of the script are commented out. These lines will be uncommented in [Next Chapter: Using reverb to add distance to spatial audio](unity-spatial-audio-ch5.md).</span></span>

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
> <span data-ttu-id="79b59-117">Um die Räumliche Raumisierung zu aktivieren oder zu deaktivieren, passt das Skript nur die **spatialBlend-Eigenschaft** an, ohne dass die **Spatialization-Eigenschaft** aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="79b59-117">To enable or disable the spatialization, the script only adjusts the **spatialBlend** property, leaving the **spatialization** property enabled.</span></span> <span data-ttu-id="79b59-118">In diesem Modus wendet Unity weiterhin die **Volumekurve** an.</span><span class="sxs-lookup"><span data-stu-id="79b59-118">In this mode, Unity still applies the **Volume** curve.</span></span> <span data-ttu-id="79b59-119">Andernfalls würde der Benutzer eine plötzliche Zunahme des Volumens hören, wenn er die Räumliche Benutzeroberfläche weit von der Quelle deaktivieren würde.</span><span class="sxs-lookup"><span data-stu-id="79b59-119">Otherwise, if the user were to disable spatialization when far from the source, they would hear the volume increase abruptly.</span></span>
> <span data-ttu-id="79b59-120">Wenn Sie die Räumliche Vergrößerung vollständig deaktivieren möchten, ändern Sie das Skript, um auch die boolesche **Spatialization-Eigenschaft** der **SourceObject-Variablen** anzupassen.</span><span class="sxs-lookup"><span data-stu-id="79b59-120">If you prefer to fully disable spatialization, modify the script to also adjust the **spatialization** boolean property of the **SourceObject** variable.</span></span>

## <a name="attach-your-script-and-drive-it-from-the-button"></a><span data-ttu-id="79b59-121">Anfügen des Skripts und Ausführen des Laufwerks über die Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="79b59-121">Attach your script and drive it from the button</span></span>

<span data-ttu-id="79b59-122">Wählen **Sie** quad in der Hierarchie aus, und verwenden Sie im Inspektorfenster die Schaltfläche Add Component (Komponente hinzufügen), um **SpatializeOnOff(Script) hinzuzufügen.**</span><span class="sxs-lookup"><span data-stu-id="79b59-122">Select **Quad** in the Hierarchy and in the Inspector window, use the Add Component button to add **SpatializeOnOff(Script)**</span></span>

![Hinzufügen eines Skripts zu "quad"](images/spatial-audio/spatial-audio-04-section2-step1-1.PNG)

<span data-ttu-id="79b59-124">Suchen Sie in der **Hierarchie nach PressableButtonHoloLens2**  >  **IconAndText**  >  **TextMeshPro.**</span><span class="sxs-lookup"><span data-stu-id="79b59-124">In the Hierarchy locate **PressableButtonHoloLens2** > **IconAndText** > **TextMeshPro**.</span></span>

<span data-ttu-id="79b59-125">With the **Quad** object still selected in the Hierarchy, in the Inspector window, locate the **Spatialize On Off (Script)** component and Drag and drop **TextMeshPro** Component of the PressableButtonHoloLens2.</span><span class="sxs-lookup"><span data-stu-id="79b59-125">With the **Quad** object still selected in the Hierarchy, in the Inspector window, locate the **Spatialize On Off (Script)** component and Drag and drop **TextMeshPro** Component of the PressableButtonHoloLens2.</span></span>

![Suchen des PressableButtonHoloLens2-Objekts in der Hierarchie](images/spatial-audio/spatial-audio-04-section2-step1-2.PNG)

<span data-ttu-id="79b59-127">Um die Schaltfläche so zu konfigurieren, dass das **SpatializeOnOff-Skript** beim Losgelassen wird, müssen Sie das interaktionsfähige Skript konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="79b59-127">To set the button to call the **SpatializeOnOff** script when the button is released You need to configure interactable script.</span></span>

<span data-ttu-id="79b59-128">Wählen Sie im Hierarchiefenster **pressableButtonHoloLens2 aus.**</span><span class="sxs-lookup"><span data-stu-id="79b59-128">In the Hierarchy window, select the **PressableButtonHoloLens2**.</span></span> <span data-ttu-id="79b59-129">Suchen Sie im Inspektorfenster die **Komponente Interactable (Script),** und klicken Sie unter dem OnClick ()-Ereignis auf + Symbol.</span><span class="sxs-lookup"><span data-stu-id="79b59-129">In the Inspector window, locate the **Interactable (Script)** component and click on + icon under OnClick () event.</span></span>

* <span data-ttu-id="79b59-130">Wenn das **PressableButtonHoloLens2-Objekt** noch im Hierarchiefenster ausgewählt  ist, klicken Sie auf das Quad-Objekt aus dem Hierarchiefenster, und ziehen Sie es in das leere Feld None **(Object)** des Ereignisses, das Sie gerade hinzugefügt haben, damit das ButtonParent-Objekt von dieser Schaltfläche auf das Schaltflächenklickereignis lausgt:</span><span class="sxs-lookup"><span data-stu-id="79b59-130">With the **PressableButtonHoloLens2** object still selected in the Hierarchy window, click-and-drag the **Quad** object from the Hierarchy window into the empty **None (Object)** field of the event you just added to make the ButtonParent object listen for button click event from this button:</span></span>

* <span data-ttu-id="79b59-131">Klicken Sie auf die Dropdownliste **No Function** des gleichen Ereignisses.</span><span class="sxs-lookup"><span data-stu-id="79b59-131">Click the **No Function** dropdown of the same event.</span></span> <span data-ttu-id="79b59-132">Wählen Sie dann **SpatializeOnOff**  >  **SwapSpatialization () aus,** um räumliche Audiodaten zu aktivieren und zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="79b59-132">Then select **SpatializeOnOff** > **SwapSpatialization ()** to turn on and off the Spatial audio</span></span>

![Einstellungen für Schaltflächenaktion](images/spatial-audio/spatial-audio-04-section2-step1-3.PNG)

## <a name="congratulations"></a><span data-ttu-id="79b59-134">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="79b59-134">Congratulations</span></span>

<span data-ttu-id="79b59-135">In diesem Tutorial haben Sie gelernt, wie Sie die Räumliche Raumisierung zur Laufzeit aktivieren und deaktivieren, die App auf einem HoloLens 2 oder im Unity-Editor testen.</span><span class="sxs-lookup"><span data-stu-id="79b59-135">In this tutorial, you have learned how to enable and disable spatialization at run time, test out the app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="79b59-136">In der App können Sie jetzt auf die Schaltfläche klicken, um die Raumklangisierung des Audios zu aktivieren und zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="79b59-136">In the app, you can now click the button to activate and deactivate spatialization of the audio.</span></span>

<span data-ttu-id="79b59-137">Im nächsten Tutorial fügen Sie einen Halleffekt hinzu, um Sounds ein Gefühl von Abstand zu geben.</span><span class="sxs-lookup"><span data-stu-id="79b59-137">In the next tutorial you'll add a reverb effect to give sounds a sense of distance.</span></span>

> [!TIP]
> <span data-ttu-id="79b59-138">Falls Sie eine Auffrischung zum Erstellen und Bereitstellen Ihres Unity-Projekts auf HoloLens 2 benötigen, lesen Sie die Anweisungen unter [Erstellen Ihrer App auf dem HoloLens 2-Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="79b59-138">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="79b59-139">Nächstes Tutorial: 5. Verwenden von Hall zum Hinzufügen von Abstand zu räumlichen Audiodaten</span><span class="sxs-lookup"><span data-stu-id="79b59-139">Next Tutorial: 5. Using reverb to add distance to spatial audio</span></span>](unity-spatial-audio-ch5.md)
