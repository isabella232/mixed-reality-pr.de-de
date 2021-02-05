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
# <a name="5-using-reverb-to-add-distance-to-spatial-audio"></a><span data-ttu-id="a387d-105">5. Verwenden von Hall zum Hinzufügen von Abstand zu räumlicher Audiowiedergabe</span><span class="sxs-lookup"><span data-stu-id="a387d-105">5. Using reverb to add distance to spatial audio</span></span>

## <a name="overview"></a><span data-ttu-id="a387d-106">Übersicht</span><span class="sxs-lookup"><span data-stu-id="a387d-106">Overview</span></span>

<span data-ttu-id="a387d-107">Im vorherigen Tutorial haben Sie eine räumliche Struktur hinzugefügt, um Ihnen einen Eindruck von der Richtung in diesem Tutorial zu geben. Sie fügen einen einfügeeffekt hinzu, um Klänge einen Eindruck von der Entfernung zu geben.</span><span class="sxs-lookup"><span data-stu-id="a387d-107">In previous tutorial, you have added spatialization for the sounds to give them a sense of direction in this tutorial you'll add a reverb effect to give sounds a sense of distance.</span></span>

## <a name="objectives"></a><span data-ttu-id="a387d-108">Ziele</span><span class="sxs-lookup"><span data-stu-id="a387d-108">Objectives</span></span>

* <span data-ttu-id="a387d-109">Verbessern Sie die wahrgenommene Entfernung von Soundquellen durch Hinzufügen von Reverb</span><span class="sxs-lookup"><span data-stu-id="a387d-109">Improve perceived distance of sound sources by adding reverb.</span></span>
* <span data-ttu-id="a387d-110">Steuern Sie den erkannten Abstand des Sounds mithilfe der Entfernung des Listener zum Hologram.</span><span class="sxs-lookup"><span data-stu-id="a387d-110">Control perceived distance of the sound using the listener's distance to the hologram.</span></span>

## <a name="add-a-mixer-group-and-a-reverb-effect"></a><span data-ttu-id="a387d-111">Hinzufügen einer mischkeitsgruppe und eines einfügenden Effekts</span><span class="sxs-lookup"><span data-stu-id="a387d-111">Add a mixer group and a reverb effect</span></span>

<span data-ttu-id="a387d-112">Im [Tutorial "spatialisieren von Schaltflächen Interaktion Sounds](unity-spatial-audio-ch2.md)" haben wir einen Mixer hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="a387d-112">In [Spatializing button interaction sounds Tutorial](unity-spatial-audio-ch2.md), we added a mixer.</span></span> <span data-ttu-id="a387d-113">Der Mixer enthält standardmäßig eine **Gruppe** namens **Master**.</span><span class="sxs-lookup"><span data-stu-id="a387d-113">The mixer includes one **Group** by default called **Master**.</span></span> <span data-ttu-id="a387d-114">Da wir nur einen "Hall"-Effekt auf einige Sounds anwenden möchten, fügen wir eine zweite Gruppe für diese Sounds hinzu.</span><span class="sxs-lookup"><span data-stu-id="a387d-114">Because we'll only want to apply a reverb effect to some sounds, let's add a second Group for those sounds.</span></span> <span data-ttu-id="a387d-115">Um eine Gruppe hinzuzufügen, klicken Sie mit der rechten Maustaste auf die Master Gruppe im **Audiomixer** , wählen Sie untergeordnete **Gruppe hinzufügen** aus, und geben Sie passenden Namen für Beispiel _Raumeffekt_</span><span class="sxs-lookup"><span data-stu-id="a387d-115">To add a Group, right click on the Master group in the **Audio Mixer** choose **Add child group** and give suitable name for example _Room Effect_:</span></span>

![Untergeordnete Gruppe hinzufügen](images/spatial-audio/spatial-audio-05-section1-step1-1.png)

<span data-ttu-id="a387d-117">Jede **Gruppe** hat einen eigenen Satz von Effekten.</span><span class="sxs-lookup"><span data-stu-id="a387d-117">Each **Group** has its own set of effects.</span></span> <span data-ttu-id="a387d-118">Fügen Sie der neuen Gruppe einen connectoreffekt hinzu, indem Sie in der neuen Gruppe auf **Hinzufügen** klicken, und wählen Sie **SFX-Hall**:</span><span class="sxs-lookup"><span data-stu-id="a387d-118">Add a reverb effect to the new group by clicking **Add...** on the new group, and choosing **SFX Reverb**:</span></span>

![SFX-Reverb hinzufügen](images/spatial-audio/spatial-audio-05-section1-step1-2.png)

<span data-ttu-id="a387d-120">In der audioterminologie wird der ursprüngliche, nicht widerzuhallte _Audiopfad als trockener Pfad_ bezeichnet, und die Audiodatei nach dem Filtern mit dem Hall Filter wird als _Nasser Pfad_ bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="a387d-120">In audio terminology, the original, unreverberated audio is called the _dry path_, and the audio after filtering with the reverb filter is called the _wet path_.</span></span> <span data-ttu-id="a387d-121">Beide Pfade werden an die Audioausgabe gesendet, und ihre relativen Stärken in dieser Mischung werden als _nass/trocken Mischung_ bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="a387d-121">Both paths are sent to the audio output, and their relative strengths in this mixture is called the _wet/dry mix_.</span></span> <span data-ttu-id="a387d-122">Die nasse/trockene Mischung wirkt sich stark auf den Sinn der Entfernung aus.</span><span class="sxs-lookup"><span data-stu-id="a387d-122">The wet/dry mix strongly affects the sense of distance.</span></span>

<span data-ttu-id="a387d-123">Der **SFX-Reverb umfasst Steuer** Elemente, mit denen die nasse/trockene Mischung innerhalb des Effekts angepasst wird.</span><span class="sxs-lookup"><span data-stu-id="a387d-123">The **SFX Reverb** includes controls to adjust the wet/dry mix within the effect.</span></span> <span data-ttu-id="a387d-124">Da das **Microsoft spatializer** -Plug-in den trockenen Pfad behandelt, verwenden wir den **SFX-Reverb** nur für den nassen Pfad.</span><span class="sxs-lookup"><span data-stu-id="a387d-124">Because the **Microsoft Spatializer** plugin handles the dry path, we'll be using the **SFX Reverb** only for the wet path.</span></span> <span data-ttu-id="a387d-125">Im inspektorbereich Ihres **SFX-einhall**:</span><span class="sxs-lookup"><span data-stu-id="a387d-125">On the Inspector pane of your **SFX Reverb**:</span></span>

* <span data-ttu-id="a387d-126">Legen Sie die Eigenschaft " **Dry Level** " auf die niedrigste Einstellung fest (-10000 MB).</span><span class="sxs-lookup"><span data-stu-id="a387d-126">Set the **Dry Level** property to the lowest setting (-10000 mB)</span></span>
* <span data-ttu-id="a387d-127">Legen Sie die **Eigenschaft "Room** " auf die höchste Einstellung (0 MB) fest.</span><span class="sxs-lookup"><span data-stu-id="a387d-127">Set the **Room property** to the highest setting (0 mB)</span></span>

![SFX-Reverb-Eigenschaften](images/spatial-audio/spatial-audio-05-section1-step1-3.png)

<span data-ttu-id="a387d-129">Mit den anderen Einstellungen wird das Gefühl des simulierten Raums gesteuert.</span><span class="sxs-lookup"><span data-stu-id="a387d-129">The other settings control the feel of the simulated room.</span></span> <span data-ttu-id="a387d-130">Die **verwahrzeit** bezieht sich insbesondere auf die wahrgenommene Raum Größe.</span><span class="sxs-lookup"><span data-stu-id="a387d-130">In particular, **Decay Time** is related to perceived room size.</span></span>

## <a name="enable-reverb-on-the-video-playback"></a><span data-ttu-id="a387d-131">Aktivieren von "Reverb" für die Videowiedergabe</span><span class="sxs-lookup"><span data-stu-id="a387d-131">Enable reverb on the video playback</span></span>

<span data-ttu-id="a387d-132">Zum Aktivieren von "Reverb" in einer Audioquelle müssen zwei Schritte ausgeführt werden:</span><span class="sxs-lookup"><span data-stu-id="a387d-132">There are two steps to enable reverb on an audio source:</span></span>

* <span data-ttu-id="a387d-133">Leiten Sie die **Audioquelle** an die entsprechende **Gruppe** weiter.</span><span class="sxs-lookup"><span data-stu-id="a387d-133">Route the **Audio Source** to the appropriate **Group**</span></span>
* <span data-ttu-id="a387d-134">Festlegen des **Microsoft spatializer** -Plug-ins, um Audioinformationen zur Verarbeitung an die **Gruppe** zu übergeben</span><span class="sxs-lookup"><span data-stu-id="a387d-134">Set the **Microsoft Spatializer** plugin to pass audio into the **Group** for processing</span></span>

<span data-ttu-id="a387d-135">In den folgenden Schritten passen Sie das Skript an, um das Audiorouting zu steuern, und fügen ein Steuerungs Skript an, das mit dem **Microsoft spatializer** -Plug-in bereitgestellt wird, um Daten in den Reverb zu übertragen</span><span class="sxs-lookup"><span data-stu-id="a387d-135">In the following steps, you will adjust the script to control the audio routing, and attach a control script provided with the **Microsoft Spatializer** plugin to feed data into the reverb.</span></span>

<span data-ttu-id="a387d-136">Klicken Sie bei ausgewähltem **Quad** in der Hierarchie im Inspektor-Fenster auf **Komponente hinzufügen** , und fügen Sie die **Sende Ebene des Raum Effekts (Skript)** hinzu:</span><span class="sxs-lookup"><span data-stu-id="a387d-136">With the **Quad** selected in the Hierarchy click **Add Component** On the Inspector window and add the **Room Effect Send Level(Script)**:</span></span>

![Skript für Sende Ebene hinzufügen](images/spatial-audio/spatial-audio-05-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="a387d-138">Es sei denn, Sie aktivieren das Feature " **Sende Ebene für raumeffekte** " des **Microsoft spatializer** -Plug-ins, es sendet keine Audiodaten an die Unity-Audioengine zur Auswirkung der Verarbeitung.</span><span class="sxs-lookup"><span data-stu-id="a387d-138">Unless you enable **Room Effect Send Level** feature of the **Microsoft Spatializer** plugin, it doesn't send any audio back to the Unity audio engine for effect processing.</span></span>

<span data-ttu-id="a387d-139">Die Bereichs Effekt-Komponente der **Sende Ebene** enthält ein Graph-Steuerelement, mit dem die Audioebene festgelegt wird, die für die Verarbeitung von Reverb an die Unity-Audioengine</span><span class="sxs-lookup"><span data-stu-id="a387d-139">The **Room Effect Send Level** component includes a graph control that sets the level of the audio sent to the Unity audio engine for reverb processing.</span></span> <span data-ttu-id="a387d-140">Um das Diagramm Steuerelement zu öffnen, klicken Sie auf die **Sende Ebene des Raum Effekts**.</span><span class="sxs-lookup"><span data-stu-id="a387d-140">To open the graph control, click on the **Room Effect Send Level**.</span></span>  <span data-ttu-id="a387d-141">Klicken und ziehen Sie die grüne Kurve nach unten, um die Ebene auf ungefähr-30dB festzulegen:</span><span class="sxs-lookup"><span data-stu-id="a387d-141">Click and drag the green curve downwards to set the level to about -30dB:</span></span>

![Hall Kurve anpassen](images/spatial-audio/spatial-audio-05-section2-step1-2.png)

<span data-ttu-id="a387d-143">Entfernen Sie dann die Auskommentierung der vier kommentierten Zeilen im **spatializeonoff** -Skript.</span><span class="sxs-lookup"><span data-stu-id="a387d-143">Next, uncomment the 4 commented lines in the **SpatializeOnOff** script.</span></span> <span data-ttu-id="a387d-144">Das Skript sieht nun wie folgt aus:</span><span class="sxs-lookup"><span data-stu-id="a387d-144">The script will now look like this:</span></span>

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

<span data-ttu-id="a387d-145">Nachdem diese Zeilen auskommentiert wurden, werden dem Inspektor des **spatializeonoff-Skripts** zwei Eigenschaften hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="a387d-145">Once these lines are Uncommented  it adds two properties to the Inspector of the **SpatializeOnOff script**.</span></span> <span data-ttu-id="a387d-146">Weisen Sie diese im Inspektor-Fenster der **spatializeonoff** -Komponente von **Quad** zu.</span><span class="sxs-lookup"><span data-stu-id="a387d-146">assign these on the Inspector window of **SpatializeOnOff** component of the **Quad**.</span></span>

<span data-ttu-id="a387d-147">Wenn das Quad-Objekt in der Hierarchie noch ausgewählt ist, suchen Sie im Inspektor-Fenster die **spatializeonoff-Skript** Komponente und:</span><span class="sxs-lookup"><span data-stu-id="a387d-147">With the Quad object still selected in the Hierarchy , in the Inspector window locate the **SpatializeOnOff Script** component and :</span></span>

* <span data-ttu-id="a387d-148">Legen Sie die Eigenschaft " **Raumeffekt** " auf Ihre neue Platz Effekt-mischkeitsgruppe fest.</span><span class="sxs-lookup"><span data-stu-id="a387d-148">Set the **Room Effect Group** property to your new Room Effect mixer group</span></span>
* <span data-ttu-id="a387d-149">Festlegen der **Master Group** -Eigenschaft auf die Master-Mixer-Gruppe</span><span class="sxs-lookup"><span data-stu-id="a387d-149">Set the **Master Group** property to the Master mixer group</span></span>

![Spatialize on off (erweitert)](images/spatial-audio/spatial-audio-05-section2-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="a387d-151">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="a387d-151">Congratulations</span></span>

<span data-ttu-id="a387d-152">Sie haben die Lernprogramme "hololens 2 Spatial audiotutorial" für Unity abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="a387d-152">You've completed the HoloLens 2 spatial audio tutorials for Unity.</span></span> <span data-ttu-id="a387d-153">Testen Sie die APP auf einem hololens 2 oder Unity.</span><span class="sxs-lookup"><span data-stu-id="a387d-153">Try out the app on a HoloLens 2 or Unity.</span></span> <span data-ttu-id="a387d-154">Wenn Sie in der APP auf die Schaltfläche klicken, um die Spatialisierung zu aktivieren, leitet das Skript die Audiodatei an die Raumeffekt Gruppe weiter, um den Code hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="a387d-154">When you click the button in the app to activate spatialization, the script will route the video's audio to the Room Effect Group to add reverb.</span></span> <span data-ttu-id="a387d-155">Beim Wechsel zu Stereo wird das Audiomaterial an die Master Gruppe weitergeleitet, und es wird vermieden, dass das Hinzufügen von Reverb erfolgt.</span><span class="sxs-lookup"><span data-stu-id="a387d-155">When switching to stereo, it will route the audio to the Master group, and avoid adding reverb.</span></span>

> [!TIP]
> <span data-ttu-id="a387d-156">Falls Sie eine Auffrischung zum Erstellen und Bereitstellen Ihres Unity-Projekts auf HoloLens 2 benötigen, lesen Sie die Anweisungen unter [Erstellen Ihrer App auf dem HoloLens 2-Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="a387d-156">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>
