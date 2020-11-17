---
title: Raumklang in Unity
description: Wiedergabe von räumlichem Sound von einem bestimmten 3D-Punkt in der Unity-Szene.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, räumlicher Sound, HRTF, Raum Größe, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, mrtk, Mixed Reality Toolkit, spatializer, Reverb
ms.openlocfilehash: db01fe81457d0f46b7f287458b4d48af4a98f2bc
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678439"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="7c068-104">Raumklang in Unity</span><span class="sxs-lookup"><span data-stu-id="7c068-104">Spatial sound in Unity</span></span>

<span data-ttu-id="7c068-105">Diese Seite ist mit Ressourcen für räumliche Sounds in Unity verknüpft.</span><span class="sxs-lookup"><span data-stu-id="7c068-105">This page links to resources for spatial sound in Unity.</span></span>

## <a name="spatializer-options"></a><span data-ttu-id="7c068-106">Spatializer-Optionen</span><span class="sxs-lookup"><span data-stu-id="7c068-106">Spatializer options</span></span>
<span data-ttu-id="7c068-107">Die spatializer-Optionen für gemischte Reality-Anwendungen umfassen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="7c068-107">Spatializer options for mixed reality applications include:</span></span>
* <span data-ttu-id="7c068-108">*MS HRTF spatializer*.</span><span class="sxs-lookup"><span data-stu-id="7c068-108">The *MS HRTF Spatializer*.</span></span> <span data-ttu-id="7c068-109">Unity stellt dies als Teil des optionalen *Windows Mixed Reality* -Pakets bereit.</span><span class="sxs-lookup"><span data-stu-id="7c068-109">Unity provides this as part of the *Windows Mixed Reality* optional package.</span></span>
  * <span data-ttu-id="7c068-110">Dies erfolgt auf CPU in einer kostengünstigeren "Single Source"-Architektur.</span><span class="sxs-lookup"><span data-stu-id="7c068-110">This runs on CPU in a higher-cost 'single-source' architecture.</span></span>
  * <span data-ttu-id="7c068-111">Dies wird aus Gründen der Abwärtskompatibilität mit ursprünglichen hololens-Anwendungen bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="7c068-111">This is provided for backwards compatibility with original HoloLens applications.</span></span>
* <span data-ttu-id="7c068-112">Der *Microsoft spatializer*.</span><span class="sxs-lookup"><span data-stu-id="7c068-112">The *Microsoft Spatializer*.</span></span> <span data-ttu-id="7c068-113">Dies ist im [GitHub-Repository von Microsoft spatializer](https://github.com/microsoft/spatialaudio-unity)verfügbar.</span><span class="sxs-lookup"><span data-stu-id="7c068-113">This is available from the [Microsoft spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity).</span></span>
  * <span data-ttu-id="7c068-114">Hierfür wird eine kostengünstigere Architektur mit mehreren Quellen verwendet.</span><span class="sxs-lookup"><span data-stu-id="7c068-114">This uses a lower-cost 'multi-source' architecture.</span></span>
  * <span data-ttu-id="7c068-115">Auf hololens 2 wird dies in einen Hardwarebeschleuniger verlagert.</span><span class="sxs-lookup"><span data-stu-id="7c068-115">On HoloLens 2, this is offloaded to a hardware accelerator.</span></span>

<span data-ttu-id="7c068-116">Für neue Anwendungen wird *Microsoft spatializer* empfohlen.</span><span class="sxs-lookup"><span data-stu-id="7c068-116">For new applications, we recommend the *Microsoft Spatializer*.</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="7c068-117">Spatialization aktivieren</span><span class="sxs-lookup"><span data-stu-id="7c068-117">Enable spatialization</span></span>

<span data-ttu-id="7c068-118">Verwenden Sie [nuget für Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) , um _Microsoft. spatialaudio. spatializer. unity_ zu installieren, und wählen Sie **Microsoft spatializer** in den Audioeinstellungen Ihres Projekts aus.</span><span class="sxs-lookup"><span data-stu-id="7c068-118">Use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) to install _Microsoft.SpatialAudio.Spatializer.Unity_ and choose **Microsoft Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="7c068-119">Führen Sie anschließend Folgendes durch:</span><span class="sxs-lookup"><span data-stu-id="7c068-119">Then:</span></span>
* <span data-ttu-id="7c068-120">Anfügen einer **Audioquelle** an ein Objekt in der Hierarchie</span><span class="sxs-lookup"><span data-stu-id="7c068-120">Attach an **Audio Source** to an object in the hierarchy</span></span>
* <span data-ttu-id="7c068-121">Aktivieren Sie das Kontrollkästchen **spatialization aktivieren** .</span><span class="sxs-lookup"><span data-stu-id="7c068-121">Check the **Enable spatialization** checkbox</span></span>
* <span data-ttu-id="7c068-122">Verschieben Sie den Schieberegler für **räumliche Blend** auf "1".</span><span class="sxs-lookup"><span data-stu-id="7c068-122">Move the **Spatial Blend** slider to '1'</span></span>
* <span data-ttu-id="7c068-123">Stellen Sie sicher, dass auf Ihrer Entwickler Arbeitsstation räumliche Audiodaten aktiviert sind</span><span class="sxs-lookup"><span data-stu-id="7c068-123">Ensure spatial audio is enabled on your developer workstation.</span></span> <span data-ttu-id="7c068-124">Aktivieren Sie diese Option, indem Sie in der Taskleiste mit der rechten Maustaste auf das Volumesymbol klicken und sicherstellen, dass räumlicher Sound auf einen anderen Wert als "Off" gesetzt ist.</span><span class="sxs-lookup"><span data-stu-id="7c068-124">Enable it by right-clicking on the volume icon in the task bar and making sure that Spatial Sound is set to something other than "off."</span></span> <span data-ttu-id="7c068-125">Um die beste Darstellung von hololens 2 zu erhalten, wählen Sie **Windows Sonic für Kopfhörer aus**.</span><span class="sxs-lookup"><span data-stu-id="7c068-125">To get the best representation of what you'll hear on HoloLens 2, choose **Windows Sonic for Headphones**.</span></span>

>[!NOTE]
><span data-ttu-id="7c068-126">Wenn Sie in Unity eine Fehlermeldung erhalten, dass das Plug-in "Microsoft. spatialaudio. spatializer. unity" nicht geladen werden kann, weil eine ihrer Abhängigkeiten fehlt, überprüfen Sie, ob Sie die neueste Version des [Microsoft Visual C++ verteilbaren](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) Pakets auf Ihrem PC installiert haben.</span><span class="sxs-lookup"><span data-stu-id="7c068-126">If you get an error in Unity about not being able to load plugin Microsoft.SpatialAudio.Spatializer.Unity because one of its dependencies is missing, check that you have the latest version of the [Microsoft Visual C++ Redistributable](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) installed on your PC.</span></span>

<span data-ttu-id="7c068-127">Weitere Informationen finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="7c068-127">For more details, see:</span></span>
* [<span data-ttu-id="7c068-128">Microsoft spatializer-GitHub-Repository</span><span class="sxs-lookup"><span data-stu-id="7c068-128">Microsoft spatializer GitHub repository</span></span>](https://github.com/microsoft/spatialaudio-unity)
* [<span data-ttu-id="7c068-129">Microsoft-Tutorial zu spatializer</span><span class="sxs-lookup"><span data-stu-id="7c068-129">Microsoft's spatializer tutorial</span></span>](tutorials/unity-spatial-audio-ch1.md)
* [<span data-ttu-id="7c068-130">Dokumentation zur Audioquelle von Unity</span><span class="sxs-lookup"><span data-stu-id="7c068-130">Unity's audio source documentation</span></span>](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [<span data-ttu-id="7c068-131">Dokumentation zu spatializer von Unity</span><span class="sxs-lookup"><span data-stu-id="7c068-131">Unity's spatializer documentation</span></span>](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a><span data-ttu-id="7c068-132">Distanzabhängige Dämpfung</span><span class="sxs-lookup"><span data-stu-id="7c068-132">Distance-based attenuation</span></span>
<span data-ttu-id="7c068-133">Der standardmäßige Entfernungs Abfall von Unity weist einen minimalen Abstand von 1 Meter und einen maximalen Abstand von 500 Meter mit einem logarithmischen Rolloff auf.</span><span class="sxs-lookup"><span data-stu-id="7c068-133">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="7c068-134">Diese Einstellungen können für Ihr Szenario funktionieren, oder Sie werden feststellen, dass die Quellen zu schnell oder zu langsam gedämpft werden.</span><span class="sxs-lookup"><span data-stu-id="7c068-134">These settings may work for your scenario, or you may find that sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="7c068-135">Weitere Informationen finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="7c068-135">For more details, see:</span></span>
* <span data-ttu-id="7c068-136">[Sound Design in gemischter Realität](../../design/spatial-sound-design.md) für empfohlene Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="7c068-136">[Sound design in mixed reality](../../design/spatial-sound-design.md) for recommended settings.</span></span>
* <span data-ttu-id="7c068-137">In [der Dokumentation zur Audioquelle von Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) finden Sie Anweisungen zum Festlegen dieser Kurven.</span><span class="sxs-lookup"><span data-stu-id="7c068-137">[Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for instructions on setting these curves.</span></span>

## <a name="reverb"></a><span data-ttu-id="7c068-138">Hall</span><span class="sxs-lookup"><span data-stu-id="7c068-138">Reverb</span></span>
<span data-ttu-id="7c068-139">Der _Microsoft spatializer_ deaktiviert die Auswirkungen von postspatializer standardmäßig.</span><span class="sxs-lookup"><span data-stu-id="7c068-139">The _Microsoft Spatializer_ disables post-spatializer effects by default.</span></span> <span data-ttu-id="7c068-140">So aktivieren Sie den Reverb und andere Auswirkungen auf räumliche Quellen:</span><span class="sxs-lookup"><span data-stu-id="7c068-140">To enable reverb and other effects for spatialized sources:</span></span>
* <span data-ttu-id="7c068-141">Fügen **Sie die Raumeffekt** -Komponente der Sende Ebene an jede Quelle an.</span><span class="sxs-lookup"><span data-stu-id="7c068-141">Attach the **Room Effect Send Level** component to each source</span></span>
* <span data-ttu-id="7c068-142">Passen Sie die Kurve der Sende Ebene für jede Quelle an, um zu steuern, wie hoch die Audiodaten für die Auswirkungen der Verarbeitung an das Diagramm zurückgesendet werden.</span><span class="sxs-lookup"><span data-stu-id="7c068-142">Adjust the send level curve for each source, to control the gain on the audio sent back to the graph for effects processing</span></span>

<span data-ttu-id="7c068-143">Ausführliche Informationen finden Sie [in Kapitel 5 des Lernprogramms zu spatializer](tutorials/unity-spatial-audio-ch5.md) .</span><span class="sxs-lookup"><span data-stu-id="7c068-143">See [Chapter 5 of the spatializer tutorial](tutorials/unity-spatial-audio-ch5.md) for details.</span></span>

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="7c068-144">Beispiele für räumliche Unity-Sounds</span><span class="sxs-lookup"><span data-stu-id="7c068-144">Unity spatial sound examples</span></span>
<span data-ttu-id="7c068-145">Beispiele für räumliche Sounds in Unity finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="7c068-145">For examples of spatial sound in Unity, see:</span></span>
* [<span data-ttu-id="7c068-146">Mrtk-Demos</span><span class="sxs-lookup"><span data-stu-id="7c068-146">MRTK demos</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* <span data-ttu-id="7c068-147">Das [Microsoft spatializer-Beispiel Projekt](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span><span class="sxs-lookup"><span data-stu-id="7c068-147">The [Microsoft Spatializer sample project](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="7c068-148">Nächster Entwicklungsprüfpunkt</span><span class="sxs-lookup"><span data-stu-id="7c068-148">Next Development Checkpoint</span></span>

<span data-ttu-id="7c068-149">Wenn Sie der Unity-Entwicklungs Prüf Punkt Journey folgen, die wir gerade angelegt haben, sind Sie in der Mitte, dass Sie die Grundbausteine der gemischten Realität erkunden.</span><span class="sxs-lookup"><span data-stu-id="7c068-149">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="7c068-150">Von hier aus können Sie mit dem nächsten Baustein fortfahren:</span><span class="sxs-lookup"><span data-stu-id="7c068-150">From here, you can proceed to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7c068-151">Text</span><span class="sxs-lookup"><span data-stu-id="7c068-151">Text</span></span>](text-in-unity.md)

<span data-ttu-id="7c068-152">Oder fahren Sie mit den Funktionen und APIs der Mixed Reality-Plattform fort:</span><span class="sxs-lookup"><span data-stu-id="7c068-152">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7c068-153">Gemeinsame Erfahrung</span><span class="sxs-lookup"><span data-stu-id="7c068-153">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="7c068-154">Sie können jederzeit zu den [Prüfpunkten für die Unity-Entwicklung](unity-development-overview.md#2-core-building-blocks) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="7c068-154">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="7c068-155">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="7c068-155">See also</span></span>
* [<span data-ttu-id="7c068-156">Sound Design in gemischter Realität</span><span class="sxs-lookup"><span data-stu-id="7c068-156">Sound design in mixed reality</span></span>](../../design/spatial-sound-design.md)
* [<span data-ttu-id="7c068-157">Microsoft-Tutorial zu spatializer</span><span class="sxs-lookup"><span data-stu-id="7c068-157">Microsoft's spatializer tutorial</span></span>](tutorials/unity-spatial-audio-ch1.md)
