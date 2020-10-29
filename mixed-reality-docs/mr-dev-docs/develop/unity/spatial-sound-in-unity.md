---
title: Raumklang in Unity
description: Wiedergabe von räumlichem Sound von einem bestimmten 3D-Punkt in der Unity-Szene.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, räumlicher Ton, HRTF, Raum Größe
ms.openlocfilehash: 9c5f71b2d9d13fa40f0d1674237d2da6c769e584
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684611"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="ed0c4-104">Raumklang in Unity</span><span class="sxs-lookup"><span data-stu-id="ed0c4-104">Spatial sound in Unity</span></span>

<span data-ttu-id="ed0c4-105">Diese Seite ist mit Ressourcen für räumliche Sounds in Unity verknüpft.</span><span class="sxs-lookup"><span data-stu-id="ed0c4-105">This page links to resources for spatial sound in Unity.</span></span>

## <a name="spatializer-options"></a><span data-ttu-id="ed0c4-106">Spatializer-Optionen</span><span class="sxs-lookup"><span data-stu-id="ed0c4-106">Spatializer options</span></span>
<span data-ttu-id="ed0c4-107">Die spatializer-Optionen für gemischte Reality-Anwendungen umfassen Folgendes:</span><span class="sxs-lookup"><span data-stu-id="ed0c4-107">Spatializer options for mixed reality applications include:</span></span>
* <span data-ttu-id="ed0c4-108">*MS HRTF spatializer* .</span><span class="sxs-lookup"><span data-stu-id="ed0c4-108">The *MS HRTF Spatializer* .</span></span> <span data-ttu-id="ed0c4-109">Unity stellt dies als Teil des optionalen *Windows Mixed Reality* -Pakets bereit.</span><span class="sxs-lookup"><span data-stu-id="ed0c4-109">Unity provides this as part of the *Windows Mixed Reality* optional package.</span></span>
  * <span data-ttu-id="ed0c4-110">Dies erfolgt auf CPU in einer kostengünstigeren "Single Source"-Architektur.</span><span class="sxs-lookup"><span data-stu-id="ed0c4-110">This runs on CPU in a higher-cost 'single-source' architecture.</span></span>
  * <span data-ttu-id="ed0c4-111">Dies wird aus Gründen der Abwärtskompatibilität mit ursprünglichen hololens-Anwendungen bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="ed0c4-111">This is provided for backwards compatibility with original HoloLens applications.</span></span>
* <span data-ttu-id="ed0c4-112">Der *Microsoft spatializer* .</span><span class="sxs-lookup"><span data-stu-id="ed0c4-112">The *Microsoft Spatializer* .</span></span> <span data-ttu-id="ed0c4-113">Dies ist im [GitHub-Repository von Microsoft spatializer](https://github.com/microsoft/spatialaudio-unity)verfügbar.</span><span class="sxs-lookup"><span data-stu-id="ed0c4-113">This is available from the [Microsoft spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity).</span></span>
  * <span data-ttu-id="ed0c4-114">Hierfür wird eine kostengünstigere Architektur mit mehreren Quellen verwendet.</span><span class="sxs-lookup"><span data-stu-id="ed0c4-114">This uses a lower-cost 'multi-source' architecture.</span></span>
  * <span data-ttu-id="ed0c4-115">Auf hololens 2 wird dies in einen Hardwarebeschleuniger verlagert.</span><span class="sxs-lookup"><span data-stu-id="ed0c4-115">On HoloLens 2, this is offloaded to a hardware accelerator.</span></span>

<span data-ttu-id="ed0c4-116">Für neue Anwendungen wird *Microsoft spatializer* empfohlen.</span><span class="sxs-lookup"><span data-stu-id="ed0c4-116">For new applications, we recommend the *Microsoft Spatializer* .</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="ed0c4-117">Spatialization aktivieren</span><span class="sxs-lookup"><span data-stu-id="ed0c4-117">Enable spatialization</span></span>

<span data-ttu-id="ed0c4-118">Verwenden Sie [nuget für Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) , um _Microsoft. spatialaudio. spatializer. unity_ zu installieren, und wählen Sie **Microsoft spatializer** in den Audioeinstellungen Ihres Projekts aus.</span><span class="sxs-lookup"><span data-stu-id="ed0c4-118">Use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) to install _Microsoft.SpatialAudio.Spatializer.Unity_ and choose **Microsoft Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="ed0c4-119">Führen Sie dann folgende Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="ed0c4-119">Then:</span></span>
* <span data-ttu-id="ed0c4-120">Anfügen einer **Audioquelle** an ein Objekt in der Hierarchie</span><span class="sxs-lookup"><span data-stu-id="ed0c4-120">Attach an **Audio Source** to an object in the hierarchy</span></span>
* <span data-ttu-id="ed0c4-121">Aktivieren Sie das Kontrollkästchen **spatialization aktivieren** .</span><span class="sxs-lookup"><span data-stu-id="ed0c4-121">Check the **Enable spatialization** checkbox</span></span>
* <span data-ttu-id="ed0c4-122">Verschieben Sie den Schieberegler für **räumliche Blend** auf "1".</span><span class="sxs-lookup"><span data-stu-id="ed0c4-122">Move the **Spatial Blend** slider to '1'</span></span>
* <span data-ttu-id="ed0c4-123">Stellen Sie sicher, dass auf Ihrer Entwickler Arbeitsstation räumliche Audiodaten aktiviert sind</span><span class="sxs-lookup"><span data-stu-id="ed0c4-123">Ensure spatial audio is enabled on your developer workstation.</span></span> <span data-ttu-id="ed0c4-124">Aktivieren Sie diese Option, indem Sie in der Taskleiste mit der rechten Maustaste auf das Volumesymbol klicken und sicherstellen, dass räumlicher Sound auf einen anderen Wert als "Off" gesetzt ist.</span><span class="sxs-lookup"><span data-stu-id="ed0c4-124">Enable it by right-clicking on the volume icon in the task bar and making sure that Spatial Sound is set to something other than "off."</span></span> <span data-ttu-id="ed0c4-125">Um die beste Darstellung von hololens 2 zu erhalten, wählen Sie **Windows Sonic für Kopfhörer aus** .</span><span class="sxs-lookup"><span data-stu-id="ed0c4-125">To get the best representation of what you'll hear on HoloLens 2, choose **Windows Sonic for Headphones** .</span></span>

>[!NOTE]
><span data-ttu-id="ed0c4-126">Wenn Sie in Unity eine Fehlermeldung erhalten, dass das Plug-in "Microsoft. spatialaudio. spatializer. unity" nicht geladen werden kann, weil eine ihrer Abhängigkeiten fehlt, überprüfen Sie, ob Sie die neueste Version des [Microsoft Visual C++ verteilbaren](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) Pakets auf Ihrem PC installiert haben.</span><span class="sxs-lookup"><span data-stu-id="ed0c4-126">If you get an error in Unity about not being able to load plugin Microsoft.SpatialAudio.Spatializer.Unity because one of its dependencies is missing, check that you have the latest version of the [Microsoft Visual C++ Redistributable](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) installed on your PC.</span></span>

<span data-ttu-id="ed0c4-127">Weitere Informationen finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="ed0c4-127">For more details, see:</span></span>
* [<span data-ttu-id="ed0c4-128">Microsoft spatializer-GitHub-Repository</span><span class="sxs-lookup"><span data-stu-id="ed0c4-128">Microsoft spatializer GitHub repository</span></span>](https://github.com/microsoft/spatialaudio-unity)
* [<span data-ttu-id="ed0c4-129">Microsoft-Tutorial zu spatializer</span><span class="sxs-lookup"><span data-stu-id="ed0c4-129">Microsoft's spatializer tutorial</span></span>](tutorials/unity-spatial-audio-ch1.md)
* [<span data-ttu-id="ed0c4-130">Dokumentation zur Audioquelle von Unity</span><span class="sxs-lookup"><span data-stu-id="ed0c4-130">Unity's audio source documentation</span></span>](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [<span data-ttu-id="ed0c4-131">Dokumentation zu spatializer von Unity</span><span class="sxs-lookup"><span data-stu-id="ed0c4-131">Unity's spatializer documentation</span></span>](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a><span data-ttu-id="ed0c4-132">Distanzabhängige Dämpfung</span><span class="sxs-lookup"><span data-stu-id="ed0c4-132">Distance-based attenuation</span></span>
<span data-ttu-id="ed0c4-133">Der standardmäßige Entfernungs Abfall von Unity weist einen minimalen Abstand von 1 Meter und einen maximalen Abstand von 500 Meter mit einem logarithmischen Rolloff auf.</span><span class="sxs-lookup"><span data-stu-id="ed0c4-133">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="ed0c4-134">Diese Einstellungen können für Ihr Szenario funktionieren, oder Sie werden feststellen, dass die Quellen zu schnell oder zu langsam gedämpft werden.</span><span class="sxs-lookup"><span data-stu-id="ed0c4-134">These settings may work for your scenario, or you may find that sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="ed0c4-135">Weitere Informationen finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="ed0c4-135">For more details, see:</span></span>
* <span data-ttu-id="ed0c4-136">[Sound Design in gemischter Realität](../../design/spatial-sound-design.md) für empfohlene Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="ed0c4-136">[Sound design in mixed reality](../../design/spatial-sound-design.md) for recommended settings.</span></span>
* <span data-ttu-id="ed0c4-137">In [der Dokumentation zur Audioquelle von Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) finden Sie Anweisungen zum Festlegen dieser Kurven.</span><span class="sxs-lookup"><span data-stu-id="ed0c4-137">[Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for instructions on setting these curves.</span></span>

## <a name="reverb"></a><span data-ttu-id="ed0c4-138">Hall</span><span class="sxs-lookup"><span data-stu-id="ed0c4-138">Reverb</span></span>
<span data-ttu-id="ed0c4-139">Der _Microsoft spatializer_ deaktiviert die Auswirkungen von postspatializer standardmäßig.</span><span class="sxs-lookup"><span data-stu-id="ed0c4-139">The _Microsoft Spatializer_ disables post-spatializer effects by default.</span></span> <span data-ttu-id="ed0c4-140">So aktivieren Sie den Reverb und andere Auswirkungen auf räumliche Quellen:</span><span class="sxs-lookup"><span data-stu-id="ed0c4-140">To enable reverb and other effects for spatialized sources:</span></span>
* <span data-ttu-id="ed0c4-141">Fügen **Sie die Raumeffekt** -Komponente der Sende Ebene an jede Quelle an.</span><span class="sxs-lookup"><span data-stu-id="ed0c4-141">Attach the **Room Effect Send Level** component to each source</span></span>
* <span data-ttu-id="ed0c4-142">Passen Sie die Kurve der Sende Ebene für jede Quelle an, um zu steuern, wie hoch die Audiodaten für die Auswirkungen der Verarbeitung an das Diagramm zurückgesendet werden.</span><span class="sxs-lookup"><span data-stu-id="ed0c4-142">Adjust the send level curve for each source, to control the gain on the audio sent back to the graph for effects processing</span></span>

<span data-ttu-id="ed0c4-143">Ausführliche Informationen finden Sie [in Kapitel 5 des Lernprogramms zu spatializer](tutorials/unity-spatial-audio-ch5.md) .</span><span class="sxs-lookup"><span data-stu-id="ed0c4-143">See [Chapter 5 of the spatializer tutorial](tutorials/unity-spatial-audio-ch5.md) for details.</span></span>

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="ed0c4-144">Beispiele für räumliche Unity-Sounds</span><span class="sxs-lookup"><span data-stu-id="ed0c4-144">Unity spatial sound examples</span></span>
<span data-ttu-id="ed0c4-145">Beispiele für räumliche Sounds in Unity finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="ed0c4-145">For examples of spatial sound in Unity, see:</span></span>
* [<span data-ttu-id="ed0c4-146">Mrtk-Demos</span><span class="sxs-lookup"><span data-stu-id="ed0c4-146">MRTK demos</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* <span data-ttu-id="ed0c4-147">Das [Microsoft spatializer-Beispiel Projekt](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span><span class="sxs-lookup"><span data-stu-id="ed0c4-147">The [Microsoft Spatializer sample project](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="ed0c4-148">Nächster Entwicklungs Prüfpunkt</span><span class="sxs-lookup"><span data-stu-id="ed0c4-148">Next Development Checkpoint</span></span>

<span data-ttu-id="ed0c4-149">Wenn Sie der Unity-Entwicklungs Prüf Punkt Journey folgen, die wir gerade angelegt haben, sind Sie in der Mitte, dass Sie die Grundbausteine der gemischten Realität erkunden.</span><span class="sxs-lookup"><span data-stu-id="ed0c4-149">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="ed0c4-150">Von hier aus können Sie mit dem nächsten Baustein fortfahren:</span><span class="sxs-lookup"><span data-stu-id="ed0c4-150">From here, you can proceed to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ed0c4-151">Text</span><span class="sxs-lookup"><span data-stu-id="ed0c4-151">Text</span></span>](text-in-unity.md)

<span data-ttu-id="ed0c4-152">Oder springen Sie zu den Funktionen und APIs der Mixed Reality-Plattform:</span><span class="sxs-lookup"><span data-stu-id="ed0c4-152">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ed0c4-153">Gemeinsame Erfahrung</span><span class="sxs-lookup"><span data-stu-id="ed0c4-153">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="ed0c4-154">Sie können jederzeit jederzeit zu den [Unity-Entwicklungs Prüfpunkten](unity-development-overview.md#2-core-building-blocks) zurückkehren.</span><span class="sxs-lookup"><span data-stu-id="ed0c4-154">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="ed0c4-155">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="ed0c4-155">See also</span></span>
* [<span data-ttu-id="ed0c4-156">Sound Design in gemischter Realität</span><span class="sxs-lookup"><span data-stu-id="ed0c4-156">Sound design in mixed reality</span></span>](../../design/spatial-sound-design.md)
* [<span data-ttu-id="ed0c4-157">Microsoft-Tutorial zu spatializer</span><span class="sxs-lookup"><span data-stu-id="ed0c4-157">Microsoft's spatializer tutorial</span></span>](tutorials/unity-spatial-audio-ch1.md)
