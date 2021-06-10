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
# <a name="5-using-reverb-to-add-distance-to-spatial-audio"></a><span data-ttu-id="a0d95-105">5. Verwenden von Hall zum Hinzufügen von Abstand zu räumlicher Audiowiedergabe</span><span class="sxs-lookup"><span data-stu-id="a0d95-105">5. Using reverb to add distance to spatial audio</span></span>

## <a name="overview"></a><span data-ttu-id="a0d95-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="a0d95-106">Overview</span></span>

<span data-ttu-id="a0d95-107">Im vorherigen Tutorial haben Sie die Räumliche Raumisierung für die Sounds hinzugefügt, um ihnen in diesem Tutorial ein Gefühl für die Richtung zu geben. In diesem Tutorial fügen Sie einen Halleffekt hinzu, um Sounds ein Gefühl von Abstand zu geben.</span><span class="sxs-lookup"><span data-stu-id="a0d95-107">In previous tutorial, you have added spatialization for the sounds to give them a sense of direction in this tutorial you'll add a reverb effect to give sounds a sense of distance.</span></span>

## <a name="objectives"></a><span data-ttu-id="a0d95-108">Ziele</span><span class="sxs-lookup"><span data-stu-id="a0d95-108">Objectives</span></span>

* <span data-ttu-id="a0d95-109">Verbessern Sie den wahrgenommenen Abstand von Soundquellen, indem Sie Hall hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="a0d95-109">Improve perceived distance of sound sources by adding reverb.</span></span>
* <span data-ttu-id="a0d95-110">Steuern Sie den wahrgenommenen Abstand des Sounds mithilfe des Abstands des Listeners zum Hologramm.</span><span class="sxs-lookup"><span data-stu-id="a0d95-110">Control perceived distance of the sound using the listener's distance to the hologram.</span></span>

## <a name="add-a-mixer-group-and-a-reverb-effect"></a><span data-ttu-id="a0d95-111">Hinzufügen einer Mixergruppe und eines Halleffekts</span><span class="sxs-lookup"><span data-stu-id="a0d95-111">Add a mixer group and a reverb effect</span></span>

<span data-ttu-id="a0d95-112">Unter [Spatializing button interaction sounds Tutorial (Tutorial:](unity-spatial-audio-ch2.md)Raumisieren von Schaltflächeninteraktionsgeräuschen) haben wir einen Mixer hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="a0d95-112">In [Spatializing button interaction sounds Tutorial](unity-spatial-audio-ch2.md), we added a mixer.</span></span> <span data-ttu-id="a0d95-113">Der Mixer enthält standardmäßig **eine Gruppe** namens **Master.**</span><span class="sxs-lookup"><span data-stu-id="a0d95-113">The mixer includes one **Group** by default called **Master**.</span></span> <span data-ttu-id="a0d95-114">Da wir nur einen Halleffekt auf einige Sounds anwenden möchten, fügen wir eine zweite Gruppe für diese Sounds hinzu.</span><span class="sxs-lookup"><span data-stu-id="a0d95-114">Because we'll only want to apply a reverb effect to some sounds, let's add a second Group for those sounds.</span></span> <span data-ttu-id="a0d95-115">Klicken Sie zum Hinzufügen einer Gruppe im **Audiomixer** mit der rechten Maustaste auf die Gruppe Master, und wählen Sie untergeordnete Gruppe hinzufügen aus, und geben Sie einen geeigneten Namen ein, z. B. _Room Effect:_ </span><span class="sxs-lookup"><span data-stu-id="a0d95-115">To add a Group, right click on the Master group in the **Audio Mixer** choose **Add child group** and give suitable name for example _Room Effect_:</span></span>

![Hinzufügen einer untergeordneten Gruppe](images/spatial-audio/spatial-audio-05-section1-step1-1.PNG)

<span data-ttu-id="a0d95-117">Jede **Gruppe** hat einen eigenen Satz von Effekten.</span><span class="sxs-lookup"><span data-stu-id="a0d95-117">Each **Group** has its own set of effects.</span></span> <span data-ttu-id="a0d95-118">Fügen Sie der neuen Gruppe einen Halleffekt hinzu, indem Sie in der neuen Gruppe auf **Hinzufügen...** klicken und **SFX Reverb auswählen:**</span><span class="sxs-lookup"><span data-stu-id="a0d95-118">Add a reverb effect to the new group by clicking **Add...** on the new group, and choosing **SFX Reverb**:</span></span>

![Hinzufügen von SFX Reverb](images/spatial-audio/spatial-audio-05-section1-step1-2.PNG)

<span data-ttu-id="a0d95-120">In der Audioterminologie wird das ursprüngliche, nicht hallierte Audio als "Dry Path" bezeichnet, und das Audio nach dem Filtern mit dem Hallfilter wird als Versauungspfad _bezeichnet._</span><span class="sxs-lookup"><span data-stu-id="a0d95-120">In audio terminology, the original, unreverberated audio is called the _dry path_, and the audio after filtering with the reverb filter is called the _wet path_.</span></span> <span data-ttu-id="a0d95-121">Beide Pfade werden an die Audioausgabe gesendet, und ihre relativen Stärken in dieser Mischung werden als _versauend/heiter bezeichnet._</span><span class="sxs-lookup"><span data-stu-id="a0d95-121">Both paths are sent to the audio output, and their relative strengths in this mixture is called the _wet/dry mix_.</span></span> <span data-ttu-id="a0d95-122">Die Versenkungs-/Drymischung wirkt sich stark auf das Gefühl der Entfernung aus.</span><span class="sxs-lookup"><span data-stu-id="a0d95-122">The wet/dry mix strongly affects the sense of distance.</span></span>

<span data-ttu-id="a0d95-123">Der **SFX Reverb enthält** Steuerelemente, um die Versheiterungs-/Probemischung innerhalb des Effekts anzupassen.</span><span class="sxs-lookup"><span data-stu-id="a0d95-123">The **SFX Reverb** includes controls to adjust the wet/dry mix within the effect.</span></span> <span data-ttu-id="a0d95-124">Da das **Microsoft Spatializer-Plug-In** den Probepfad verarbeitet, verwenden wir **SFX Reverb** nur für den Verwerfungspfad.</span><span class="sxs-lookup"><span data-stu-id="a0d95-124">Because the **Microsoft Spatializer** plugin handles the dry path, we'll be using the **SFX Reverb** only for the wet path.</span></span> <span data-ttu-id="a0d95-125">Im Inspektorbereich Ihres **SFX-Halls:**</span><span class="sxs-lookup"><span data-stu-id="a0d95-125">On the Inspector pane of your **SFX Reverb**:</span></span>

* <span data-ttu-id="a0d95-126">Legen Sie **die Eigenschaft Dry Level** auf die niedrigste Einstellung fest (-10000 mB).</span><span class="sxs-lookup"><span data-stu-id="a0d95-126">Set the **Dry Level** property to the lowest setting (-10000 mB)</span></span>
* <span data-ttu-id="a0d95-127">Legen Sie **die Eigenschaft Room** auf die höchste Einstellung (0 mB) fest.</span><span class="sxs-lookup"><span data-stu-id="a0d95-127">Set the **Room property** to the highest setting (0 mB)</span></span>

![SFX Reverb-Eigenschaften](images/spatial-audio/spatial-audio-05-section1-step1-3.PNG)

<span data-ttu-id="a0d95-129">Die anderen Einstellungen steuern das Verhalten des simulierten Raums.</span><span class="sxs-lookup"><span data-stu-id="a0d95-129">The other settings control the feel of the simulated room.</span></span> <span data-ttu-id="a0d95-130">Insbesondere bezieht sich **die Abklingzeit** auf die wahrgenommene Raumgröße.</span><span class="sxs-lookup"><span data-stu-id="a0d95-130">In particular, **Decay Time** is related to perceived room size.</span></span>

## <a name="enable-reverb-on-the-video-playback"></a><span data-ttu-id="a0d95-131">Aktivieren von Hall bei der Videowiedergabe</span><span class="sxs-lookup"><span data-stu-id="a0d95-131">Enable reverb on the video playback</span></span>

<span data-ttu-id="a0d95-132">Es gibt zwei Schritte, um Hall für eine Audioquelle zu aktivieren:</span><span class="sxs-lookup"><span data-stu-id="a0d95-132">There are two steps to enable reverb on an audio source:</span></span>

* <span data-ttu-id="a0d95-133">Routen der **Audioquelle** an die entsprechende **Gruppe**</span><span class="sxs-lookup"><span data-stu-id="a0d95-133">Route the **Audio Source** to the appropriate **Group**</span></span>
* <span data-ttu-id="a0d95-134">Festlegen des **Microsoft Spatializer-Plug-Ins,** um Audio zur Verarbeitung an die **Gruppe** zu übergeben</span><span class="sxs-lookup"><span data-stu-id="a0d95-134">Set the **Microsoft Spatializer** plugin to pass audio into the **Group** for processing</span></span>

<span data-ttu-id="a0d95-135">In den folgenden Schritten passen Sie das Skript an, um das Audiorouting zu steuern, und fügen ein Steuerungsskript an, das mit dem **Microsoft Spatializer-Plug-In** bereitgestellt wird, um Daten in den Hall zu geben.</span><span class="sxs-lookup"><span data-stu-id="a0d95-135">In the following steps, you will adjust the script to control the audio routing, and attach a control script provided with the **Microsoft Spatializer** plugin to feed data into the reverb.</span></span>

<span data-ttu-id="a0d95-136">Klicken Sie **bei ausgewähltem Quad** in der Hierarchie im Inspektorfenster auf Add **Component** (Komponente hinzufügen), und fügen Sie room Effect **Send Level(Script) hinzu:**</span><span class="sxs-lookup"><span data-stu-id="a0d95-136">With the **Quad** selected in the Hierarchy click **Add Component** On the Inspector window and add the **Room Effect Send Level(Script)**:</span></span>

![Hinzufügen eines Skripts auf Sendeebene](images/spatial-audio/spatial-audio-05-section2-step1-1.PNG)

> [!NOTE]
> <span data-ttu-id="a0d95-138">Sofern Sie das **Room Effect Send Level-Feature** des Microsoft Spatializer-Plug-Ins nicht aktivieren, sendet es keine Audiodaten zur Effektverarbeitung zurück an die Unity-Audio-Engine. </span><span class="sxs-lookup"><span data-stu-id="a0d95-138">Unless you enable **Room Effect Send Level** feature of the **Microsoft Spatializer** plugin, it doesn't send any audio back to the Unity audio engine for effect processing.</span></span>

<span data-ttu-id="a0d95-139">Die **Komponente Room Effect Send Level** enthält ein Graphsteuerelement, das die Audioebene für die Hallverarbeitung an die Unity-Audio-Engine fest legt.</span><span class="sxs-lookup"><span data-stu-id="a0d95-139">The **Room Effect Send Level** component includes a graph control that sets the level of the audio sent to the Unity audio engine for reverb processing.</span></span> <span data-ttu-id="a0d95-140">Klicken Sie zum Öffnen des Graph-Steuerelements auf **die Raumeffekt-Sendeebene**.</span><span class="sxs-lookup"><span data-stu-id="a0d95-140">To open the graph control, click on the **Room Effect Send Level**.</span></span>  <span data-ttu-id="a0d95-141">Klicken Sie auf die grüne Kurve, und ziehen Sie sie nach unten, um die Ebene auf etwa -30dB zu setzen:</span><span class="sxs-lookup"><span data-stu-id="a0d95-141">Click and drag the green curve downwards to set the level to about -30dB:</span></span>

![Anpassen der Hallkurve](images/spatial-audio/spatial-audio-05-section2-step1-2.PNG)

<span data-ttu-id="a0d95-143">Kommentieren Sie als Nächstes die vier kommentierten Zeilen im **SpatializeOnOff-Skript** aus.</span><span class="sxs-lookup"><span data-stu-id="a0d95-143">Next, uncomment the 4 commented lines in the **SpatializeOnOff** script.</span></span> <span data-ttu-id="a0d95-144">Das Skript sieht nun wie im folgenden Beispiel aus:</span><span class="sxs-lookup"><span data-stu-id="a0d95-144">The script will now look like this:</span></span>

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

<span data-ttu-id="a0d95-145">Nachdem diese Zeilen auskommentiert wurden, werden dem Inspektor des **SpatializeOnOff-Skripts zwei Eigenschaften hinzufügt.**</span><span class="sxs-lookup"><span data-stu-id="a0d95-145">Once these lines are Uncommented  it adds two properties to the Inspector of the **SpatializeOnOff script**.</span></span> <span data-ttu-id="a0d95-146">Weisen Sie diese im Inspektorfenster der **SpatializeOnOff-Komponente** von **Quad zu.**</span><span class="sxs-lookup"><span data-stu-id="a0d95-146">assign these on the Inspector window of **SpatializeOnOff** component of the **Quad**.</span></span>

<span data-ttu-id="a0d95-147">Wenn das Quad-Objekt in der Hierarchie noch ausgewählt ist, suchen Sie im Inspektorfenster die **SpatializeOnOff-Skriptkomponente** und :</span><span class="sxs-lookup"><span data-stu-id="a0d95-147">With the Quad object still selected in the Hierarchy , in the Inspector window locate the **SpatializeOnOff Script** component and :</span></span>

* <span data-ttu-id="a0d95-148">Legen Sie die **Eigenschaft Room Effect Group** auf Ihre neue Room Effect-Mixergruppe fest.</span><span class="sxs-lookup"><span data-stu-id="a0d95-148">Set the **Room Effect Group** property to your new Room Effect mixer group</span></span>
* <span data-ttu-id="a0d95-149">Legen Sie die **Eigenschaft Mastergruppe** auf die Mastermixergruppe fest.</span><span class="sxs-lookup"><span data-stu-id="a0d95-149">Set the **Master Group** property to the Master mixer group</span></span>

![Spatialize On Off Extended](images/spatial-audio/spatial-audio-05-section2-step1-3.PNG)

## <a name="congratulations"></a><span data-ttu-id="a0d95-151">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="a0d95-151">Congratulations</span></span>

<span data-ttu-id="a0d95-152">Sie haben die Tutorials HoloLens 2 räumliche Audioinhalte für Unity abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="a0d95-152">You've completed the HoloLens 2 spatial audio tutorials for Unity.</span></span> <span data-ttu-id="a0d95-153">Testen Sie die App auf einem HoloLens 2 unity.</span><span class="sxs-lookup"><span data-stu-id="a0d95-153">Try out the app on a HoloLens 2 or Unity.</span></span> <span data-ttu-id="a0d95-154">Wenn Sie in der App auf die Schaltfläche klicken, um die Räumliche Vertonung zu aktivieren, wird das Audio des Videos vom Skript an die Room Effect-Gruppe geroutet, um Hall hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="a0d95-154">When you click the button in the app to activate spatialization, the script will route the video's audio to the Room Effect Group to add reverb.</span></span> <span data-ttu-id="a0d95-155">Wenn Sie zu Stereo wechseln, wird die Audiodatei an die Mastergruppe geroutet, und es wird vermieden, Dass Hall hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="a0d95-155">When switching to stereo, it will route the audio to the Master group, and avoid adding reverb.</span></span>

> [!TIP]
> <span data-ttu-id="a0d95-156">Falls Sie eine Auffrischung zum Erstellen und Bereitstellen Ihres Unity-Projekts auf HoloLens 2 benötigen, lesen Sie die Anweisungen unter [Erstellen Ihrer App auf dem HoloLens 2-Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="a0d95-156">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>
