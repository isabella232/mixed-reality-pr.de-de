---
title: Audioinhalte in gemischter Realität
description: Audioinhalte in gemischter Realität können das Vertrauen von Benutzeroberflächen Interaktionen erhöhen und Benutzer in der Benutzeroberfläche eintauchen.
author: kegodin
ms.author: v-hferrone
ms.date: 11/07/2019
ms.topic: article
keywords: räumlicher Sound, Umschließungs Sound, 3D--Audio, 3D--Ton, räumliche Audiodaten, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, hololens, mrtk, Mixed Reality Toolkit, Fallstudien, Akustik
ms.openlocfilehash: 335ff8acf036591bbbf9868f591ca2c3cef1386c
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583251"
---
# <a name="audio-in-mixed-reality"></a><span data-ttu-id="861a9-104">Audioinhalte in gemischter Realität</span><span class="sxs-lookup"><span data-stu-id="861a9-104">Audio in mixed reality</span></span>

<span data-ttu-id="861a9-105">Das Audiomaterial ist ein wesentlicher Bestandteil von Design und Produktivität in gemischter Realität.</span><span class="sxs-lookup"><span data-stu-id="861a9-105">Audio is an essential part of design and productivity in mixed reality.</span></span> <span data-ttu-id="861a9-106">Sound kann:</span><span class="sxs-lookup"><span data-stu-id="861a9-106">Sound can:</span></span>
* <span data-ttu-id="861a9-107">Erhöhen Sie das Vertrauen von Benutzern in Gesten-und sprach Interaktionen.</span><span class="sxs-lookup"><span data-stu-id="861a9-107">Increase user confidence in gesture and voice interactions.</span></span>
* <span data-ttu-id="861a9-108">Leiten Sie die Benutzer zu den nächsten Schritten.</span><span class="sxs-lookup"><span data-stu-id="861a9-108">Guide users to next steps.</span></span>
* <span data-ttu-id="861a9-109">Kombinieren Sie virtuelle Objekte effektiv mit der realen Welt.</span><span class="sxs-lookup"><span data-stu-id="861a9-109">Effectively combine virtual objects with the real world.</span></span>

<span data-ttu-id="861a9-110">Die Head-Nachverfolgung mit niedriger Latenz von Mixed Reality-Headsets (einschließlich hololens) unterstützt die auf hoher Qualität basierende Spatialisierung.</span><span class="sxs-lookup"><span data-stu-id="861a9-110">The low-latency head tracking of mixed reality headsets, including HoloLens, supports high-quality HRTF-based spatialization.</span></span> <span data-ttu-id="861a9-111">Sie können Audiodaten in Ihrer Anwendung für Folgendes spatialisieren:</span><span class="sxs-lookup"><span data-stu-id="861a9-111">You can spatialize audio in your application to:</span></span>
* <span data-ttu-id="861a9-112">Beachten Sie, dass visuelle Elemente aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="861a9-112">Call attention to visual elements.</span></span>
* <span data-ttu-id="861a9-113">Helfen Sie Benutzern dabei, das Bewusstsein ihrer realen Umgebung zu wahren.</span><span class="sxs-lookup"><span data-stu-id="861a9-113">Help users maintain awareness of their real-world surroundings.</span></span>

<span data-ttu-id="861a9-114">Die Akustik verbindet Hologramme tiefer mit der Mixed-Reality-Welt.</span><span class="sxs-lookup"><span data-stu-id="861a9-114">Acoustics more deeply connect holograms to the mixed-reality world.</span></span> <span data-ttu-id="861a9-115">Es stellt Hinweise zur Umgebung und zum Objektzustand bereit.</span><span class="sxs-lookup"><span data-stu-id="861a9-115">It provides cues about the environment and object state.</span></span>

<span data-ttu-id="861a9-116">Weitere Informationen finden Sie [unter ausführliche Entwurfs Beispiele für die Verwendung von Audiodateien](spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="861a9-116">See detailed [examples of design that uses audio](spatial-sound-design.md).</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="device-support"></a><span data-ttu-id="861a9-117">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="861a9-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="861a9-118"><strong>Feature</strong></span><span class="sxs-lookup"><span data-stu-id="861a9-118"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="861a9-119"><a href="/hololens/hololens1-hardware"><strong>Hololens (erste Generation)</strong></a></span><span class="sxs-lookup"><span data-stu-id="861a9-119"><a href="/hololens/hololens1-hardware"><strong>HoloLens (first gen)</strong></a></span></span></td>
        <td><span data-ttu-id="861a9-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="861a9-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="861a9-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive Headsets</strong></a></span><span class="sxs-lookup"><span data-stu-id="861a9-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="861a9-122">Raumklang</span><span class="sxs-lookup"><span data-stu-id="861a9-122">Spatialization</span></span></td>
        <td><span data-ttu-id="861a9-123">✔️</span><span class="sxs-lookup"><span data-stu-id="861a9-123">✔️</span></span></td>
        <td><span data-ttu-id="861a9-124">✔️</span><span class="sxs-lookup"><span data-stu-id="861a9-124">✔️</span></span></td>
        <td><span data-ttu-id="861a9-125">✔️</span><span class="sxs-lookup"><span data-stu-id="861a9-125">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="861a9-126">Beschleunigung der spatialisierungs Hardware</span><span class="sxs-lookup"><span data-stu-id="861a9-126">Spatialization hardware acceleration</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="861a9-127">✔️</span><span class="sxs-lookup"><span data-stu-id="861a9-127">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="use-of-sounds-in-mixed-reality"></a><span data-ttu-id="861a9-128">Verwendung von Sounds in gemischter Realität</span><span class="sxs-lookup"><span data-stu-id="861a9-128">Use of sounds in mixed reality</span></span>

<span data-ttu-id="861a9-129">Die [Verwendung von Sounds in gemischter Realität](spatial-sound-design.md) erfordert einen anderen Ansatz als in der Touchscreen-und Tastatur-und Maus Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="861a9-129">[Use of sounds in mixed reality](spatial-sound-design.md) requires a different approach than in touch and keyboard-and-mouse applications.</span></span> <span data-ttu-id="861a9-130">Wichtige Entscheidungen zum Entwurf von Entscheidungen umfassen, welche Sounds räumlich und welche Interaktionen mit sonify zu tun haben.</span><span class="sxs-lookup"><span data-stu-id="861a9-130">Key sound design decisions include which sounds to spatialize and which interactions to sonify.</span></span> <span data-ttu-id="861a9-131">Diese Entscheidungen wirken sich stark auf Benutzer vertrauen, Produktivität und Lernkurve aus.</span><span class="sxs-lookup"><span data-stu-id="861a9-131">These decisions strongly effect user confidence, productivity, and learning curve.</span></span>

### <a name="case-studies"></a><span data-ttu-id="861a9-132">Fallstudien</span><span class="sxs-lookup"><span data-stu-id="861a9-132">Case studies</span></span>

<span data-ttu-id="861a9-133">Mit holotour werden Benutzer praktisch zu touristischen und historischen Websites auf der ganzen Welt.</span><span class="sxs-lookup"><span data-stu-id="861a9-133">HoloTour virtually takes users to tourist and historical sites around the world.</span></span> <span data-ttu-id="861a9-134">Weitere Informationen finden Sie in der Fallstudie [Sound Design for holotour](case-study-spatial-sound-design-for-holotour.md) .</span><span class="sxs-lookup"><span data-stu-id="861a9-134">See the [Sound design for HoloTour](case-study-spatial-sound-design-for-holotour.md) case study.</span></span> <span data-ttu-id="861a9-135">Ein spezielles Mikrofon und renderingsetup wurden zum Erfassen der Themenbereiche verwendet.</span><span class="sxs-lookup"><span data-stu-id="861a9-135">A special microphone and rendering setup were used to capture the subject spaces.</span></span>

<span data-ttu-id="861a9-136">Roboraid ist ein Hochenergie geschütztes Gerät für hololens.</span><span class="sxs-lookup"><span data-stu-id="861a9-136">RoboRaid is a high-energy shooter for HoloLens.</span></span> <span data-ttu-id="861a9-137">In der Fallstudie [Sound Design for roboraid](case-study-using-spatial-sound-in-roboraid.md) werden die Entwurfs Optionen beschrieben, die getroffen wurden, um sicherzustellen, dass räumliche Audiodaten in vollem Umfang dramatisch wirksam werden.</span><span class="sxs-lookup"><span data-stu-id="861a9-137">The [Sound design for RoboRaid](case-study-using-spatial-sound-in-roboraid.md) case study describes the design choices that were made to ensure spatial audio was used to the fullest dramatic effect.</span></span>

## <a name="spatialization"></a><span data-ttu-id="861a9-138">Raumklang</span><span class="sxs-lookup"><span data-stu-id="861a9-138">Spatialization</span></span>

<span data-ttu-id="861a9-139">Spatialization ist die direktionale Komponente räumlicher Audiodaten.</span><span class="sxs-lookup"><span data-stu-id="861a9-139">Spatialization is the directional component of spatial audio.</span></span> <span data-ttu-id="861a9-140">Bei einem 7,1-Home-Theater-Setup ist die Spatialisierung so einfach wie das Schwenken zwischen Lautsprechern.</span><span class="sxs-lookup"><span data-stu-id="861a9-140">For a 7.1 home theater setup, spatialization is as simple as panning between loudspeakers.</span></span> <span data-ttu-id="861a9-141">Doch für Kopfhörer in gemischter Realität ist es von entscheidender Bedeutung, eine auf HRTF basierende Technologie für Genauigkeit und Komfort zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="861a9-141">But for headphones in mixed reality, it's essential to use an HRTF-based technology for accuracy and comfort.</span></span> <span data-ttu-id="861a9-142">Windows bietet eine auf HRTF basierende Spatialisierung. diese Unterstützung ist auf hololens 2 Hardware beschleunigt.</span><span class="sxs-lookup"><span data-stu-id="861a9-142">Windows offers HRTF-based spatialization, and this support is hardware-accelerated on HoloLens 2.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a><span data-ttu-id="861a9-143">Sollte ich räumlich spatialisieren?</span><span class="sxs-lookup"><span data-stu-id="861a9-143">Should I spatialize?</span></span>

<span data-ttu-id="861a9-144">Die Spatialisierung kann viele Sounds in gemischten Reality-Anwendungen verbessern.</span><span class="sxs-lookup"><span data-stu-id="861a9-144">Spatialization can improve many sounds in mixed-reality applications.</span></span> <span data-ttu-id="861a9-145">Die Spatialisierung nimmt einen Sound aus dem Kopf des Listener und platziert Sie in der Welt.</span><span class="sxs-lookup"><span data-stu-id="861a9-145">Spatialization takes a sound out of the listener's head and places it in the world.</span></span> <span data-ttu-id="861a9-146">Vorschläge zur effektiven Verwendung von spatialization in Ihrer Anwendung finden Sie unter [Spatial Sound Design](spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="861a9-146">For suggestions on effective use of spatialization in your application, see [Spatial sound design](spatial-sound-design.md).</span></span>

### <a name="spatializer-personalization"></a><span data-ttu-id="861a9-147">Spatializer-Personalisierung</span><span class="sxs-lookup"><span data-stu-id="861a9-147">Spatializer personalization</span></span>

<span data-ttu-id="861a9-148">HRTFs bearbeitet die Ebenen-und Phasenunterschiede zwischen den Ohren im Frequenzspektrum.</span><span class="sxs-lookup"><span data-stu-id="861a9-148">HRTFs manipulate the level and phase differences between ears across the frequency spectrum.</span></span> <span data-ttu-id="861a9-149">Sie basieren auf physischen Modellen und Messungen von Menschen Kopf-, Rumpf-und Ohrformen (pinnae).</span><span class="sxs-lookup"><span data-stu-id="861a9-149">They're based on physical models and measurements of human head, torso, and ear shapes (pinnae).</span></span> <span data-ttu-id="861a9-150">Unsere Gehirne reagieren auf diese Unterschiede, um die wahrgenommene Richtung in Sound bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="861a9-150">Our brains respond to these differences to provide perceived direction in sound.</span></span>

<span data-ttu-id="861a9-151">Jede Person verfügt über eine eindeutige Ohrform, Kopfgröße und Position.</span><span class="sxs-lookup"><span data-stu-id="861a9-151">Every individual has a unique ear shape, head size, and ear position.</span></span> <span data-ttu-id="861a9-152">Das beste ist also die beste Lösung für Sie.</span><span class="sxs-lookup"><span data-stu-id="861a9-152">So the best HRTFs conform to you.</span></span> <span data-ttu-id="861a9-153">Um die räumungsgenauigkeit zu erhöhen, verwendet hololens ihren Inter-pupilary Distance (IPD) aus den Headset-anzeigen, um den HRTFs für die Kopfgröße anzupassen.</span><span class="sxs-lookup"><span data-stu-id="861a9-153">To increase spatialization accuracy, HoloLens uses your inter-pupilary distance (IPD) from the headset displays to adjust the HRTFs for your head size.</span></span>

### <a name="spatializer-platform-support"></a><span data-ttu-id="861a9-154">Unterstützung für spatializer-Plattform</span><span class="sxs-lookup"><span data-stu-id="861a9-154">Spatializer platform support</span></span>

<span data-ttu-id="861a9-155">Windows bietet mithilfe der [ispatialaudioclient-API](/windows/win32/coreaudio/spatial-sound)eine spatialization, einschließlich HRTFs.</span><span class="sxs-lookup"><span data-stu-id="861a9-155">Windows offers spatialization, including HRTFs, via the [ISpatialAudioClient API](/windows/win32/coreaudio/spatial-sound).</span></span> <span data-ttu-id="861a9-156">Diese API macht die Hardwarebeschleunigung von hololens 2 HRTF für Anwendungen verfügbar.</span><span class="sxs-lookup"><span data-stu-id="861a9-156">This API exposes the HoloLens 2 HRTF hardware acceleration to applications.</span></span>

### <a name="spatializer-middleware-support"></a><span data-ttu-id="861a9-157">Unterstützung für spatializer-Middleware</span><span class="sxs-lookup"><span data-stu-id="861a9-157">Spatializer middleware support</span></span>

<span data-ttu-id="861a9-158">Die Unterstützung für Windows ' HRTFs ist für die folgenden Drittanbieter-AUDIOMODULE verfügbar.</span><span class="sxs-lookup"><span data-stu-id="861a9-158">Support for Windows' HRTFs is available for the following third-party audio engines.</span></span>
* <span data-ttu-id="861a9-159">Ein [Plug-in für Unity-Audiodateien](../develop/unity/spatial-sound-in-unity.md)</span><span class="sxs-lookup"><span data-stu-id="861a9-159">A [Unity audio engine plugin](../develop/unity/spatial-sound-in-unity.md)</span></span>
* <span data-ttu-id="861a9-160">Ein [wwise-Audiomodul-Plug-](https://www.audiokinetic.com/products/plug-ins/msspatial/) in</span><span class="sxs-lookup"><span data-stu-id="861a9-160">A [Wwise audio engine plugin](https://www.audiokinetic.com/products/plug-ins/msspatial/)</span></span>

## <a name="acoustics"></a><span data-ttu-id="861a9-161">Akustik</span><span class="sxs-lookup"><span data-stu-id="861a9-161">Acoustics</span></span>

<span data-ttu-id="861a9-162">Räumliche Audiodaten sind ungefähr mehr als die Richtung.</span><span class="sxs-lookup"><span data-stu-id="861a9-162">Spatial audio is about more than direction.</span></span> <span data-ttu-id="861a9-163">Weitere Dimensionen sind Okklusion, Behinderung, Reverb, Porton und Quell Modellierung.</span><span class="sxs-lookup"><span data-stu-id="861a9-163">Other dimensions include occlusion, obstruction, reverb, portaling, and source modeling.</span></span> <span data-ttu-id="861a9-164">Gemeinsam werden diese Dimensionen als *Akustik* bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="861a9-164">Collectively these dimensions are referred to as *acoustics*.</span></span> <span data-ttu-id="861a9-165">Ohne Akustik fehlt bei spatialisierten Sounds eine nicht wahrgenommene Entfernung.</span><span class="sxs-lookup"><span data-stu-id="861a9-165">Without acoustics, spatialized sounds lack perceived distance.</span></span>

<span data-ttu-id="861a9-166">Akustik Behandlungen reichen von einfachen bis zu komplexen.</span><span class="sxs-lookup"><span data-stu-id="861a9-166">Acoustics treatments range from simple to complex.</span></span> <span data-ttu-id="861a9-167">Sie können einen von beliebigen Audiomodulen unterstützten Reverb verwenden, um spatialisierte Sounds in die Umgebung des Listener zu überführen.</span><span class="sxs-lookup"><span data-stu-id="861a9-167">You can use a reverb that's supported by any audio engine to push spatialized sounds into the environment of the listener.</span></span> <span data-ttu-id="861a9-168">Akustiksysteme wie z. b. die [Projekt Akustik](/gaming/acoustics/what-is-acoustics)  bieten umfangreichere und überzeugende Akustik Behandlungen.</span><span class="sxs-lookup"><span data-stu-id="861a9-168">Acoustics systems such as [Project Acoustics](/gaming/acoustics/what-is-acoustics)  provide richer and more compelling acoustics treatment.</span></span> <span data-ttu-id="861a9-169">Die Projekt Akustik kann die Auswirkung von Wänden, Türen und anderen Szenen Geometrie in einem Sound modellieren.</span><span class="sxs-lookup"><span data-stu-id="861a9-169">Project Acoustics can model the effect of walls, doors, and other scene geometry on a sound.</span></span> <span data-ttu-id="861a9-170">Es ist eine effektive Option in Fällen, in denen die relevante Szene Geometrie zur Entwicklungszeit bekannt ist.</span><span class="sxs-lookup"><span data-stu-id="861a9-170">It's an effective option for cases where the relevant scene geometry is known at development time.</span></span>

## <a name="next-steps"></a><span data-ttu-id="861a9-171">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="861a9-171">Next steps</span></span>

- [<span data-ttu-id="861a9-172">Raumklang in Unity</span><span class="sxs-lookup"><span data-stu-id="861a9-172">Spatial sound in Unity</span></span>](../develop/unity/spatial-sound-in-unity.md)
- [<span data-ttu-id="861a9-173">Verwenden von Sound in Anwendungen mit gemischter Realität</span><span class="sxs-lookup"><span data-stu-id="861a9-173">How to use sound in mixed-reality applications</span></span>](spatial-sound-design.md)