---
title: 'Lernprogramme für räumliche Audiodaten: 4. Aktivieren und Deaktivieren räumlicher Audiowiedergabe zur Laufzeit'
description: Verwenden Sie eine Schaltfläche, um die Spatialisierung von Audiodaten zur Laufzeit zu aktivieren und zu deaktivieren.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, hololens2, Spatial Audiodatei, mrtk, Mixed Reality Toolkit, UWP, Windows 10, HRTF, Head-Related Transfer Function, Reverb, Microsoft spatializer
ms.openlocfilehash: 26143975707b2cd6141803a6335cec89db5bbd26
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590732"
---
# <a name="4-enabling-and-disabling-spatialization-at-run-time"></a><span data-ttu-id="ae26a-105">4. aktivieren und Deaktivieren der Spatialisierung zur Laufzeit</span><span class="sxs-lookup"><span data-stu-id="ae26a-105">4. Enabling and disabling spatialization at run time</span></span>

## <a name="overview"></a><span data-ttu-id="ae26a-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="ae26a-106">Overview</span></span>

<span data-ttu-id="ae26a-107">In diesem Tutorial erfahren Sie, wie Sie die Spatialisierung zur Laufzeit aktivieren und deaktivieren und im Unity-Editor und in hololens 2 testen.</span><span class="sxs-lookup"><span data-stu-id="ae26a-107">In this tutorial, you will learn how to Enable and disable spatialization at run time and test this in the unity editor and HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="ae26a-108">Ziele</span><span class="sxs-lookup"><span data-stu-id="ae26a-108">Objectives</span></span>

* <span data-ttu-id="ae26a-109">Hinzufügen eines neuen Skripts zum Steuern der Spatialisierung eines Spiel Objekts</span><span class="sxs-lookup"><span data-stu-id="ae26a-109">Add a new script to control spatialization on a game object</span></span>
* <span data-ttu-id="ae26a-110">Das spatialization-Steuerelement Skript aus Schaltflächen Aktionen Steuern</span><span class="sxs-lookup"><span data-stu-id="ae26a-110">Drive the spatialization control script from button actions</span></span>

## <a name="add-spatialization-control-script"></a><span data-ttu-id="ae26a-111">Spatialization-Steuerelement Skript hinzufügen</span><span class="sxs-lookup"><span data-stu-id="ae26a-111">Add spatialization control script</span></span>

 <span data-ttu-id="ae26a-112">Klicken Sie mit der rechten Maustaste in das Projekt Fenster, und wählen Sie  >  **c#-Skript** erstellen aus, um ein neues c#-Skript zu erstellen. Geben Sie einen passenden Namen für das Skript ein, z.b. _spatializeonoff_:</span><span class="sxs-lookup"><span data-stu-id="ae26a-112">Right-click in the Project window and choose **Create** > **C# Script** to create a new C# script, enter a suitable name for the script, for example, _SpatializeOnOff_:</span></span>

![Erstellen des Skripts](images/spatial-audio/spatial-audio-04-section1-step1-1.png)

<span data-ttu-id="ae26a-114">Doppelklicken Sie im Projektfenster auf das Skript, um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="ae26a-114">Double-click the script in the Project window to open it in Visual Studio.</span></span> <span data-ttu-id="ae26a-115">Ersetzen Sie die Standardskript Inhalte durch Folgendes:</span><span class="sxs-lookup"><span data-stu-id="ae26a-115">Replace the default script contents with the following:</span></span>

> [!NOTE]
> <span data-ttu-id="ae26a-116">Mehrere Zeilen des Skripts werden auskommentiert. Diese Zeilen werden im [nächsten Kapitel auskommentiert: Verwenden von "Reverb" zum Hinzufügen von Distanz zu räumlichen Audiodaten](unity-spatial-audio-ch5.md).</span><span class="sxs-lookup"><span data-stu-id="ae26a-116">Several lines of the script are commented out. These lines will be uncommented in [Next Chapter: Using reverb to add distance to spatial audio](unity-spatial-audio-ch5.md).</span></span>

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
> <span data-ttu-id="ae26a-117">Zum Aktivieren oder Deaktivieren der Spatialisierung passt das Skript nur die **spatialblend** -Eigenschaft an, sodass die **spatialization** -Eigenschaft aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="ae26a-117">To enable or disable the spatialization, the script only adjusts the **spatialBlend** property, leaving the **spatialization** property enabled.</span></span> <span data-ttu-id="ae26a-118">In diesem Modus wendet Unity weiterhin die **volumekurve** an.</span><span class="sxs-lookup"><span data-stu-id="ae26a-118">In this mode, Unity still applies the **Volume** curve.</span></span> <span data-ttu-id="ae26a-119">Wenn der Benutzer die räumungszeit bei weitem von der Quelle deaktivieren würde, würde er das Volume plötzlich anwachsen.</span><span class="sxs-lookup"><span data-stu-id="ae26a-119">Otherwise, if the user were to disable spatialization when far from the source, they would hear the volume increase abruptly.</span></span>
> <span data-ttu-id="ae26a-120">Wenn Sie die spatialization vollständig deaktivieren möchten, ändern Sie das Skript so, dass auch die Eigenschaft **spatialization** booleschen der **SourceObject** -Variablen angepasst wird.</span><span class="sxs-lookup"><span data-stu-id="ae26a-120">If you prefer to fully disable spatialization, modify the script to also adjust the **spatialization** boolean property of the **SourceObject** variable.</span></span>

## <a name="attach-your-script-and-drive-it-from-the-button"></a><span data-ttu-id="ae26a-121">Fügen Sie das Skript an, und Steuern Sie es über die Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="ae26a-121">Attach your script and drive it from the button</span></span>

<span data-ttu-id="ae26a-122">Wählen Sie in der Hierarchie **Quad** aus, und verwenden Sie im Inspektor-Fenster die Schaltfläche Komponente hinzufügen, um **spatializeonoff (Script)** hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="ae26a-122">Select **Quad** in the Hierarchy and in the Inspector window, use the Add Component button to add **SpatializeOnOff(Script)**</span></span>

![Skript zu Quad hinzufügen](images/spatial-audio/spatial-audio-04-section2-step1-1.png)

<span data-ttu-id="ae26a-124">Suchen Sie in der Hierarchie nach **PressableButtonHoloLens2**  >  **iconandtext**  >  **textmeshpro**.</span><span class="sxs-lookup"><span data-stu-id="ae26a-124">In the Hierarchy locate **PressableButtonHoloLens2** > **IconAndText** > **TextMeshPro**.</span></span>

<span data-ttu-id="ae26a-125">Wenn das **Quad** -Objekt in der Hierarchie noch ausgewählt ist, suchen Sie im Inspektor-Fenster die Komponente " **spatialize on off (Script)** ", und ziehen Sie die **textmeschpro** -Komponente von "PressableButtonHoloLens2" per Drag & Drop.</span><span class="sxs-lookup"><span data-stu-id="ae26a-125">With the **Quad** object still selected in the Hierarchy, in the Inspector window, locate the **Spatialize On Off (Script)** component and Drag and drop **TextMeshPro** Component of the PressableButtonHoloLens2.</span></span>

![Suchen des PressableButtonHoloLens2-Objekts in der Hierarchie](images/spatial-audio/spatial-audio-04-section2-step1-2.png)

<span data-ttu-id="ae26a-127">Um die Schaltfläche festzulegen, um das **spatializeonoff** -Skript aufzurufen, wenn die Schaltfläche losgelassen wird, müssen Sie das Interaktionen-Skript konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="ae26a-127">To set the button to call the **SpatializeOnOff** script when the button is released You need to configure interactable script.</span></span>

<span data-ttu-id="ae26a-128">Wählen Sie im Fenster Hierarchie den **PressableButtonHoloLens2** aus.</span><span class="sxs-lookup"><span data-stu-id="ae26a-128">In the Hierarchy window, select the **PressableButtonHoloLens2**.</span></span> <span data-ttu-id="ae26a-129">Suchen Sie im Inspektor-Fenster die Komponente **interactable (Script)** , und klicken Sie unter dem OnClick ()-Ereignis auf das Symbol +.</span><span class="sxs-lookup"><span data-stu-id="ae26a-129">In the Inspector window, locate the **Interactable (Script)** component and click on + icon under OnClick () event.</span></span>

* <span data-ttu-id="ae26a-130">Wenn das **PressableButtonHoloLens2** -Objekt noch im Fenster Hierarchie ausgewählt ist, klicken Sie auf-und-ziehen Sie das **Quad** -Objekt aus dem Fenster Hierarchie in das leere Feld **None (Objekt)** des soeben hinzugefügten Ereignisses, damit das buttonparent-Objekt über diese Schaltfläche auf das Click-Ereignis der Schaltfläche lauschen kann:</span><span class="sxs-lookup"><span data-stu-id="ae26a-130">With the **PressableButtonHoloLens2** object still selected in the Hierarchy window, click-and-drag the **Quad** object from the Hierarchy window into the empty **None (Object)** field of the event you just added to make the ButtonParent object listen for button click event from this button:</span></span>

* <span data-ttu-id="ae26a-131">Klicken Sie auf die Dropdownliste **No Function** des gleichen Ereignisses.</span><span class="sxs-lookup"><span data-stu-id="ae26a-131">Click the **No Function** dropdown of the same event.</span></span> <span data-ttu-id="ae26a-132">Wählen Sie dann **spatializeonoff**  >  -**Austausch-/apspatialization ()** aus, um das räumliche Audiogerät zu aktivieren und zu deaktivieren</span><span class="sxs-lookup"><span data-stu-id="ae26a-132">Then select **SpatializeOnOff** > **SwapSpatialization ()** to turn on and off the Spatial audio</span></span>

![Schaltflächen Aktions Einstellungen](images/spatial-audio/spatial-audio-04-section2-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="ae26a-134">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="ae26a-134">Congratulations</span></span>

<span data-ttu-id="ae26a-135">In diesem Tutorial haben Sie erfahren, wie Sie die Spatialisierung zur Laufzeit aktivieren und deaktivieren, die APP auf einem hololens 2 oder im Unity-Editor testen.</span><span class="sxs-lookup"><span data-stu-id="ae26a-135">In this tutorial, you have learned how to enable and disable spatialization at run time, test out the app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="ae26a-136">In der App können Sie nun auf die Schaltfläche klicken, um die Spatialisierung der Audiodatei zu aktivieren und zu deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="ae26a-136">In the app, you can now click the button to activate and deactivate spatialization of the audio.</span></span>

<span data-ttu-id="ae26a-137">Im nächsten Tutorial fügen Sie einen "Hall Effekt" hinzu, um Klänge einen Eindruck von der Entfernung zu geben.</span><span class="sxs-lookup"><span data-stu-id="ae26a-137">In the next tutorial you'll add a reverb effect to give sounds a sense of distance.</span></span>

> [!TIP]
> <span data-ttu-id="ae26a-138">Falls Sie eine Auffrischung zum Erstellen und Bereitstellen Ihres Unity-Projekts auf HoloLens 2 benötigen, lesen Sie die Anweisungen unter [Erstellen Ihrer App auf dem HoloLens 2-Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="ae26a-138">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ae26a-139">Nächstes Tutorial: 5. Verwenden von "Reverb" zum Hinzufügen von Distanz zu räumlichen Audiodaten</span><span class="sxs-lookup"><span data-stu-id="ae26a-139">Next Tutorial: 5. Using reverb to add distance to spatial audio</span></span>](unity-spatial-audio-ch5.md)
