---
title: Raumklang in Unity
description: Erfahren Sie, wie Sie räumliche Sounds von einem bestimmten 3D-Punkt in der Unity-Szene mit Beispielen wiedergeben und abmildern.
author: kegodin
ms.author: v-hferrone
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, räumlicher Sound, HRTF, Raum Größe, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, mrtk, Mixed Reality Toolkit, spatializer, Reverb
ms.openlocfilehash: ec2703aa89925cb68860670f574a1e43f672e247
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009270"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="8f147-104">Raumklang in Unity</span><span class="sxs-lookup"><span data-stu-id="8f147-104">Spatial sound in Unity</span></span>

<span data-ttu-id="8f147-105">Diese Seite ist mit Ressourcen für räumliche Sounds in Unity verknüpft.</span><span class="sxs-lookup"><span data-stu-id="8f147-105">This page links to resources for spatial sound in Unity.</span></span>

## <a name="spatializer-options"></a><span data-ttu-id="8f147-106">Spatializer-Optionen</span><span class="sxs-lookup"><span data-stu-id="8f147-106">Spatializer options</span></span>

<span data-ttu-id="8f147-107">Die spatializer-Optionen für gemischte Reality-Anwendungen umfassen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="8f147-107">Spatializer options for mixed reality applications include:</span></span>
* <span data-ttu-id="8f147-108">Unity stellt den *MS HRTF spatializer* als Teil des optionalen *Windows Mixed Reality* -Pakets bereit.</span><span class="sxs-lookup"><span data-stu-id="8f147-108">Unity provides the *MS HRTF Spatializer* as part of the *Windows Mixed Reality* optional package.</span></span>
  * <span data-ttu-id="8f147-109">Wird auf CPU in einer kostengünstigeren "Single Source"-Architektur ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="8f147-109">Runs on CPU in a higher-cost 'single-source' architecture.</span></span>
  * <span data-ttu-id="8f147-110">Wird aus Gründen der Abwärtskompatibilität mit ursprünglichen hololens-Anwendungen bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="8f147-110">Provided for backwards compatibility with original HoloLens applications.</span></span>
* <span data-ttu-id="8f147-111">*Microsoft spatializer* ist im [Microsoft spatializer GitHub-Repository](https://github.com/microsoft/spatialaudio-unity)verfügbar.</span><span class="sxs-lookup"><span data-stu-id="8f147-111">The *Microsoft Spatializer* is available from the [Microsoft spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity).</span></span>
  * <span data-ttu-id="8f147-112">Verwendet eine kostengünstigere Architektur mit mehreren Quellen.</span><span class="sxs-lookup"><span data-stu-id="8f147-112">Uses a lower-cost 'multi-source' architecture.</span></span>
  * <span data-ttu-id="8f147-113">Offloaded an einen Hardwarebeschleuniger auf den hololens 2.</span><span class="sxs-lookup"><span data-stu-id="8f147-113">Offloaded to a hardware accelerator on the HoloLens 2.</span></span> 

<span data-ttu-id="8f147-114">Für neue Anwendungen wird *Microsoft spatializer* empfohlen.</span><span class="sxs-lookup"><span data-stu-id="8f147-114">For new applications, we recommend the *Microsoft Spatializer*.</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="8f147-115">Spatialization aktivieren</span><span class="sxs-lookup"><span data-stu-id="8f147-115">Enable spatialization</span></span>

<span data-ttu-id="8f147-116">Verwenden Sie [nuget für Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) , um _Microsoft. spatialaudio. spatializer. unity_ zu installieren, und wählen Sie **Microsoft spatializer** in den Audioeinstellungen Ihres Projekts aus.</span><span class="sxs-lookup"><span data-stu-id="8f147-116">Use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) to install _Microsoft.SpatialAudio.Spatializer.Unity_ and choose **Microsoft Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="8f147-117">Führen Sie dann folgende Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="8f147-117">Then:</span></span>
* <span data-ttu-id="8f147-118">Anfügen einer **Audioquelle** an ein Objekt in der Hierarchie</span><span class="sxs-lookup"><span data-stu-id="8f147-118">Attach an **Audio Source** to an object in the hierarchy</span></span>
* <span data-ttu-id="8f147-119">Aktivieren Sie das Kontrollkästchen **spatialization aktivieren** .</span><span class="sxs-lookup"><span data-stu-id="8f147-119">Check the **Enable spatialization** checkbox</span></span>
* <span data-ttu-id="8f147-120">Verschieben Sie den Schieberegler für **räumliche Blend** auf "1".</span><span class="sxs-lookup"><span data-stu-id="8f147-120">Move the **Spatial Blend** slider to '1'</span></span>
* <span data-ttu-id="8f147-121">Stellen Sie sicher, dass auf Ihrer Entwickler Arbeitsstation räumliche Audiodaten aktiviert sind</span><span class="sxs-lookup"><span data-stu-id="8f147-121">Ensure spatial audio is enabled on your developer workstation.</span></span> 
    * <span data-ttu-id="8f147-122">Klicken Sie mit der rechten Maustaste auf das Volumesymbol in der Taskleiste, und stellen Sie sicher, dass räumlicher Sound auf einen anderen Wert als "Off" festgelegt ist</span><span class="sxs-lookup"><span data-stu-id="8f147-122">Right-click on the volume icon in the task bar and making sure that Spatial Sound is set to something other than "off".</span></span> 
    * <span data-ttu-id="8f147-123">Wählen Sie **Windows Sonic für Kopfhörer aus** , um die beste Darstellung zu erhalten, was Sie auf hololens 2 hören werden.</span><span class="sxs-lookup"><span data-stu-id="8f147-123">Choose **Windows Sonic for Headphones** to get the best representation of what you'll hear on HoloLens 2.</span></span>

>[!NOTE]
><span data-ttu-id="8f147-124">Wenn Sie in Unity eine Fehlermeldung erhalten, dass das Plug-in "Microsoft. spatialaudio. spatializer. unity" nicht geladen werden kann, weil eine ihrer Abhängigkeiten fehlt, überprüfen Sie, ob Sie die neueste Version des [Microsoft Visual C++ verteilbaren](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) Pakets auf Ihrem PC installiert haben.</span><span class="sxs-lookup"><span data-stu-id="8f147-124">If you get an error in Unity about not being able to load plugin Microsoft.SpatialAudio.Spatializer.Unity because one of its dependencies is missing, check that you have the latest version of the [Microsoft Visual C++ Redistributable](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) installed on your PC.</span></span>

<span data-ttu-id="8f147-125">Weitere Informationen finden Sie unter</span><span class="sxs-lookup"><span data-stu-id="8f147-125">For more information, see:</span></span>
* [<span data-ttu-id="8f147-126">Microsoft spatializer-GitHub-Repository</span><span class="sxs-lookup"><span data-stu-id="8f147-126">Microsoft spatializer GitHub repository</span></span>](https://github.com/microsoft/spatialaudio-unity)
* [<span data-ttu-id="8f147-127">Microsoft-Tutorial zu spatializer</span><span class="sxs-lookup"><span data-stu-id="8f147-127">Microsoft's spatializer tutorial</span></span>](tutorials/unity-spatial-audio-ch1.md)
* [<span data-ttu-id="8f147-128">Dokumentation zur Audioquelle von Unity</span><span class="sxs-lookup"><span data-stu-id="8f147-128">Unity's audio source documentation</span></span>](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [<span data-ttu-id="8f147-129">Dokumentation zu spatializer von Unity</span><span class="sxs-lookup"><span data-stu-id="8f147-129">Unity's spatializer documentation</span></span>](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a><span data-ttu-id="8f147-130">Distanzabhängige Dämpfung</span><span class="sxs-lookup"><span data-stu-id="8f147-130">Distance-based attenuation</span></span>

<span data-ttu-id="8f147-131">Der standardmäßige Entfernungs Abfall von Unity weist einen minimalen Abstand von 1 Meter und einen maximalen Abstand von 500 Meter mit einem logarithmischen Rolloff auf.</span><span class="sxs-lookup"><span data-stu-id="8f147-131">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="8f147-132">Diese Einstellungen können für Ihr Szenario funktionieren, oder Sie werden feststellen, dass die Quellen zu schnell oder zu langsam gedämpft werden.</span><span class="sxs-lookup"><span data-stu-id="8f147-132">These settings may work for your scenario, or you may find that sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="8f147-133">Weitere Informationen finden Sie unter</span><span class="sxs-lookup"><span data-stu-id="8f147-133">For more information, see:</span></span>
* <span data-ttu-id="8f147-134">[Sound Design in gemischter Realität](../../design/spatial-sound-design.md) für empfohlene Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="8f147-134">[Sound design in mixed reality](../../design/spatial-sound-design.md) for recommended settings.</span></span>
* <span data-ttu-id="8f147-135">In [der Dokumentation zur Audioquelle von Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) finden Sie Anweisungen zum Festlegen dieser Kurven.</span><span class="sxs-lookup"><span data-stu-id="8f147-135">[Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for instructions on setting these curves.</span></span>

## <a name="reverb"></a><span data-ttu-id="8f147-136">Hall</span><span class="sxs-lookup"><span data-stu-id="8f147-136">Reverb</span></span>

<span data-ttu-id="8f147-137">Der _Microsoft spatializer_ deaktiviert die Auswirkungen von postspatializer standardmäßig.</span><span class="sxs-lookup"><span data-stu-id="8f147-137">The _Microsoft Spatializer_ disables post-spatializer effects by default.</span></span> <span data-ttu-id="8f147-138">So aktivieren Sie den Reverb und andere Auswirkungen auf räumliche Quellen:</span><span class="sxs-lookup"><span data-stu-id="8f147-138">To enable reverb and other effects for spatialized sources:</span></span>
* <span data-ttu-id="8f147-139">Fügen **Sie die Raumeffekt** -Komponente der Sende Ebene an jede Quelle an.</span><span class="sxs-lookup"><span data-stu-id="8f147-139">Attach the **Room Effect Send Level** component to each source</span></span>
* <span data-ttu-id="8f147-140">Passen Sie die Kurve der Sende Ebene für jede Quelle an, um zu steuern, wie hoch die Audiodaten für die Auswirkungen der Verarbeitung an das Diagramm zurückgesendet werden.</span><span class="sxs-lookup"><span data-stu-id="8f147-140">Adjust the send level curve for each source, to control the gain on the audio sent back to the graph for effects processing</span></span>

<span data-ttu-id="8f147-141">Ausführliche Informationen finden Sie [in Kapitel 5 des Lernprogramms zu spatializer](tutorials/unity-spatial-audio-ch5.md) .</span><span class="sxs-lookup"><span data-stu-id="8f147-141">See [Chapter 5 of the spatializer tutorial](tutorials/unity-spatial-audio-ch5.md) for details.</span></span>

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="8f147-142">Beispiele für räumliche Unity-Sounds</span><span class="sxs-lookup"><span data-stu-id="8f147-142">Unity spatial sound examples</span></span>

<span data-ttu-id="8f147-143">Beispiele für räumliche Sounds in Unity finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="8f147-143">For examples of spatial sound in Unity, see:</span></span>
* [<span data-ttu-id="8f147-144">Mrtk-Demos</span><span class="sxs-lookup"><span data-stu-id="8f147-144">MRTK demos</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* <span data-ttu-id="8f147-145">Das [Microsoft spatializer-Beispiel Projekt](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span><span class="sxs-lookup"><span data-stu-id="8f147-145">The [Microsoft Spatializer sample project](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="8f147-146">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="8f147-146">Next Development Checkpoint</span></span>

<span data-ttu-id="8f147-147">Wenn Sie der Unity-Entwicklungs Journey folgen, die wir angelegt haben, befinden Sie sich in der Mitte, in der Sie die Mixed-Kern Bausteine untersuchen.</span><span class="sxs-lookup"><span data-stu-id="8f147-147">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="8f147-148">Von hier aus können Sie mit dem nächsten Baustein fortfahren:</span><span class="sxs-lookup"><span data-stu-id="8f147-148">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8f147-149">Text</span><span class="sxs-lookup"><span data-stu-id="8f147-149">Text</span></span>](text-in-unity.md)

<span data-ttu-id="8f147-150">Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:</span><span class="sxs-lookup"><span data-stu-id="8f147-150">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8f147-151">Gemeinsame Erfahrung</span><span class="sxs-lookup"><span data-stu-id="8f147-151">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="8f147-152">Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="8f147-152">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="8f147-153">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="8f147-153">See also</span></span>

* [<span data-ttu-id="8f147-154">Sound Design in gemischter Realität</span><span class="sxs-lookup"><span data-stu-id="8f147-154">Sound design in mixed reality</span></span>](../../design/spatial-sound-design.md)
* [<span data-ttu-id="8f147-155">Microsoft-Tutorial zu spatializer</span><span class="sxs-lookup"><span data-stu-id="8f147-155">Microsoft's spatializer tutorial</span></span>](tutorials/unity-spatial-audio-ch1.md)
