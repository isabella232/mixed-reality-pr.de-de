---
title: Szenenverständnis
description: beschreibt Scene Understanding in MRTK
author: MaxWang-MS
ms.author: wangmax
ms.date: 03/02/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Scene Understanding
ms.openlocfilehash: ac90359a71267dc64e659f446f35ec2510c42599
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143886"
---
# <a name="scene-understanding"></a><span data-ttu-id="378e7-104">Szenenverständnis</span><span class="sxs-lookup"><span data-stu-id="378e7-104">Scene Understanding</span></span>

<span data-ttu-id="378e7-105">[Scene Understanding](/windows/mixed-reality/scene-understanding) gibt eine semantische Darstellung von Szenenentitäten sowie deren geometrische Formen auf __HoloLens 2__ zurück (HoloLens 1. Generation wird nicht unterstützt).</span><span class="sxs-lookup"><span data-stu-id="378e7-105">[Scene Understanding](/windows/mixed-reality/scene-understanding) returns a semantic representation of scene entities as well as their geometric forms on __HoloLens 2__ (HoloLens 1st Gen is not supported).</span></span>

<span data-ttu-id="378e7-106">Einige erwartete Anwendungsfälle dieser Technologie sind:</span><span class="sxs-lookup"><span data-stu-id="378e7-106">Some expected use cases of this technology are:</span></span>
* <span data-ttu-id="378e7-107">Platzieren von Objekten auf der nächsten Oberfläche einer bestimmten Art (z. B. Wand und Boden)</span><span class="sxs-lookup"><span data-stu-id="378e7-107">Place objects on nearest surface of a certain kind (e.g. wall and floor)</span></span>
* <span data-ttu-id="378e7-108">Erstellen eines Navigationsgitters für Spiele im Plattformstil</span><span class="sxs-lookup"><span data-stu-id="378e7-108">Construct nav-mesh for platform style games</span></span>
* <span data-ttu-id="378e7-109">Bereitstellen von physikalischer Engine-freundlicher Geometrie als Quader</span><span class="sxs-lookup"><span data-stu-id="378e7-109">Provide physics engine friendly geometry as quads</span></span>
* <span data-ttu-id="378e7-110">Beschleunigen sie die Entwicklung, indem Sie vermeiden, ähnliche Algorithmen zu schreiben.</span><span class="sxs-lookup"><span data-stu-id="378e7-110">Accelerate development by avoiding the need to write similar algorithms</span></span>

<span data-ttu-id="378e7-111">Scene Understanding ist ab MRTK 2.6 als __experimentelles__ Feature verfügbar.</span><span class="sxs-lookup"><span data-stu-id="378e7-111">Scene Understanding is available as an __experimental__ feature starting from MRTK 2.6.</span></span> <span data-ttu-id="378e7-112">Sie ist als [räumlicher Beobachter](spatial-awareness-getting-started.md#register-observers) namens in MRTK [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) integriert.</span><span class="sxs-lookup"><span data-stu-id="378e7-112">It is integrated into MRTK as a [spatial observer](spatial-awareness-getting-started.md#register-observers) called [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver).</span></span> <span data-ttu-id="378e7-113">Scene Understanding funktioniert sowohl mit der Legacy-XR-Pipeline als auch mit der XR SDK-Pipeline.</span><span class="sxs-lookup"><span data-stu-id="378e7-113">Scene Understanding works both with the Legacy XR pipeline and the XR SDK pipeline.</span></span> <span data-ttu-id="378e7-114">In beiden Fällen `WindowsSceneUnderstandingObserver` wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="378e7-114">In both cases the `WindowsSceneUnderstandingObserver` is used.</span></span>

## <a name="observer-overview"></a><span data-ttu-id="378e7-115">Übersicht über Beobachter</span><span class="sxs-lookup"><span data-stu-id="378e7-115">Observer overview</span></span>

<span data-ttu-id="378e7-116">Wenn sie gefragt [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) wird, gibt [spatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) mit Attributen zurück, die für die Anwendung nützlich sind, um ihre Umgebung zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="378e7-116">When asked, the [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) will return [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) with attributes useful for the application to understand its surroundings.</span></span> <span data-ttu-id="378e7-117">Die Beobachtungshäufigkeit, der zurückgegebene Objekttyp (z. B. Wand, Boden) und andere Beobachterverhalten hängen von der Konfiguration des Beobachters über das Profil ab.</span><span class="sxs-lookup"><span data-stu-id="378e7-117">The observation frequency, returned object type (e.g. wall, floor) and other observer behaviors are dependent on the configuration of the observer via profile.</span></span> <span data-ttu-id="378e7-118">Wenn z. B. die Verdeckungsmaske gewünscht ist, muss der Beobachter so konfiguriert werden, dass quads generiert wird.</span><span class="sxs-lookup"><span data-stu-id="378e7-118">For instance, if the occlusion mask is desired the observer must be configured to generate quads.</span></span> <span data-ttu-id="378e7-119">Die beobachtete Szene kann als serialisierte Datei gespeichert werden, die später geladen werden kann, um die Szene im Wiedergabemodus des Editors neu zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="378e7-119">The observed scene can be saved as serialized file that can be later loaded to recreate the scene in editor play mode.</span></span>

## <a name="setup"></a><span data-ttu-id="378e7-120">Einrichten</span><span class="sxs-lookup"><span data-stu-id="378e7-120">Setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="378e7-121">Scene Understanding wird nur für HoloLens 2 und Unity 2019.4 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="378e7-121">Scene Understanding is only supported on HoloLens 2 and Unity 2019.4 and higher.</span></span>

1. <span data-ttu-id="378e7-122">Stellen Sie sicher, dass die Plattform in den Buildeinstellungen auf UWP festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="378e7-122">Ensure the platform is set to UWP in build settings.</span></span>
1. <span data-ttu-id="378e7-123">Erwerben Sie das Scene Understanding-Paket über [Mixed Reality FeatureTool.](https://aka.ms/MRFeatureTool)</span><span class="sxs-lookup"><span data-stu-id="378e7-123">Acquire the Scene Understanding package via [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool).</span></span>

## <a name="using-scene-understanding"></a><span data-ttu-id="378e7-124">Verwenden von Scene Understanding</span><span class="sxs-lookup"><span data-stu-id="378e7-124">Using Scene Understanding</span></span>

<span data-ttu-id="378e7-125">Die schnellste Möglichkeit, mit Scene Understanding zu beginnen, besteht im Überprüfen der Beispielszene.</span><span class="sxs-lookup"><span data-stu-id="378e7-125">The quickest way to get started with Scene Understanding is to check out the sample scene.</span></span>

### <a name="scene-understanding-sample-scene"></a><span data-ttu-id="378e7-126">Scene Understanding-Beispielszene</span><span class="sxs-lookup"><span data-stu-id="378e7-126">Scene Understanding sample scene</span></span>

<span data-ttu-id="378e7-127">Verwenden Sie in Unity den Projekt-Explorer, um die Szenendatei in zu öffnen `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` und die Wiedergabe zu drücken.</span><span class="sxs-lookup"><span data-stu-id="378e7-127">In Unity, use the Project Explorer to open the scene file in `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` and press play!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="378e7-128">Wenn Sie das Mixed Reality Feature Tool verwenden oder anderweitig über UPM importieren, importieren Sie das Beispiel Demos – SpatialAwareness, bevor Sie das Beispiel Experimental – SceneUnderstanding aufgrund eines Abhängigkeitsproblems importieren.</span><span class="sxs-lookup"><span data-stu-id="378e7-128">When using the Mixed Reality Feature Tool or otherwise importing via UPM, please import the Demos - SpatialAwareness sample before importing the Experimental - SceneUnderstanding sample due to a dependency issue.</span></span> <span data-ttu-id="378e7-129">Weitere Informationen [finden Sie in diesem GitHub-Problem.](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431)</span><span class="sxs-lookup"><span data-stu-id="378e7-129">Please see [this GitHub issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) for more information.</span></span>

<span data-ttu-id="378e7-130">Die Szene veranschaulicht Folgendes:</span><span class="sxs-lookup"><span data-stu-id="378e7-130">The scene demonstrates the following:</span></span>

* <span data-ttu-id="378e7-131">Visualisierung beobachteter Szenenobjekte mit in der Anwendungsbenutzeroberfläche zum Konfigurieren des Beobachters</span><span class="sxs-lookup"><span data-stu-id="378e7-131">Visualization of observed Scene Objects with in application UI for configuring the observer</span></span>
* <span data-ttu-id="378e7-132">`DemoSceneUnderstandingController`Beispielskript, das zeigt, wie Sie Beobachtereinstellungen ändern und auf relevante Ereignisse lauschen</span><span class="sxs-lookup"><span data-stu-id="378e7-132">Example `DemoSceneUnderstandingController` script that shows how to change observer settings and listen to relevant events</span></span>
* <span data-ttu-id="378e7-133">Speichern von Szenendaten auf dem Gerät für die Offlineentwicklung</span><span class="sxs-lookup"><span data-stu-id="378e7-133">Saving scene data to device for offline development</span></span>
* <span data-ttu-id="378e7-134">Laden zuvor gespeicherter Szenendaten (BYTES-Dateien) zur Unterstützung des Entwicklungsworkflows im Editor</span><span class="sxs-lookup"><span data-stu-id="378e7-134">Loading previously saved scene data (.bytes files) to support in-editor development workflow</span></span>

> [!NOTE] 
> <span data-ttu-id="378e7-135">Die Beispielszene basiert auf der Legacy-XR-Pipeline.</span><span class="sxs-lookup"><span data-stu-id="378e7-135">The sample scene is based on the Legacy XR pipeline.</span></span> <span data-ttu-id="378e7-136">Wenn Sie die XR SDK-Pipeline verwenden, sollten Sie die Profile entsprechend ändern.</span><span class="sxs-lookup"><span data-stu-id="378e7-136">If you are using the XR SDK pipeline you should modify the profiles accordingly.</span></span> <span data-ttu-id="378e7-137">Das bereitgestellte Scene Understanding Spatial Awareness System-Profil ( `DemoSceneUnderstandingSystemProfile` ) und die Scene Understanding Observer-Profile ( und ) funktionieren für beide `DefaultSceneUnderstandingObserverProfile` `DemoSceneUnderstandingObserverProfile` Pipelines.</span><span class="sxs-lookup"><span data-stu-id="378e7-137">The provided Scene Understanding Spatial Awareness System profile (`DemoSceneUnderstandingSystemProfile`) and the Scene Understanding Observer profiles (`DefaultSceneUnderstandingObserverProfile` and `DemoSceneUnderstandingObserverProfile`) works for both pipelines.</span></span>

#### <a name="configuring-the-observer-service"></a><span data-ttu-id="378e7-138">Konfigurieren des Observer-Diensts</span><span class="sxs-lookup"><span data-stu-id="378e7-138">Configuring the observer service</span></span>

<span data-ttu-id="378e7-139">Wählen Sie das Spielobjekt "MixedRealityToolkit" aus, und überprüfen Sie den Inspektor.</span><span class="sxs-lookup"><span data-stu-id="378e7-139">Select the 'MixedRealityToolkit' game object and check the inspector.</span></span>

![Szenenverständnis des Standorts in der Hierarchie](../images/spatial-awareness/MRTKHierarchy.png)

![MRTK-Standort im Inspektor](../images/spatial-awareness/MRTKLocation.png)

<span data-ttu-id="378e7-142">Mit diesen Optionen kann konfiguriert `WindowsSceneUnderstandingObserver` werden.</span><span class="sxs-lookup"><span data-stu-id="378e7-142">These options will allow one to configure the `WindowsSceneUnderstandingObserver`.</span></span>

### <a name="example-script"></a><span data-ttu-id="378e7-143">Beispielskript</span><span class="sxs-lookup"><span data-stu-id="378e7-143">Example script</span></span>

<span data-ttu-id="378e7-144">Das Beispielskript _DemoSceneUnderstandingController.cs_ veranschaulicht die wichtigsten Konzepte bei der Arbeit mit dem Scene Understanding-Dienst.</span><span class="sxs-lookup"><span data-stu-id="378e7-144">The example script _DemoSceneUnderstandingController.cs_ demonstrates the major concepts in working with the Scene Understanding service.</span></span>

* <span data-ttu-id="378e7-145">Abonnieren von Scene Understanding-Ereignissen</span><span class="sxs-lookup"><span data-stu-id="378e7-145">Subscribing to Scene Understanding events</span></span>
* <span data-ttu-id="378e7-146">Behandeln von Scene Understanding-Ereignissen</span><span class="sxs-lookup"><span data-stu-id="378e7-146">Handling Scene Understanding events</span></span>
* <span data-ttu-id="378e7-147">Konfigurieren von `WindowsSceneUnderstandingObserver` zur Laufzeit</span><span class="sxs-lookup"><span data-stu-id="378e7-147">Configuring the `WindowsSceneUnderstandingObserver` at runtime</span></span>

<span data-ttu-id="378e7-148">Die Umschalten im Bereich in der Szene ändern das Verhalten des Beobachters zum Verstehen der Szene, indem öffentliche Funktionen dieses Beispielskripts aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="378e7-148">The toggles on the panel in the scene change the behavior of scene understanding observer by calling public functions of this sample script.</span></span>

<span data-ttu-id="378e7-149">Wenn *Sie Prefabs instanziieren* aktivieren, wird veranschaulicht, wie Objekte erstellt werden, deren Größe sich an alle [SpatialAwarenessSceneObject-Objekte](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject)anpasst, die unter einem übergeordneten Objekt gesammelt werden.</span><span class="sxs-lookup"><span data-stu-id="378e7-149">Turning on *Instantiate Prefabs*, will demonstrate creating objects that size to fit themselves to all [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject), gathered neatly under a parent object.</span></span>

![Democontrolleroptionen](../images/spatial-awareness/Controller.png)

### <a name="built-app-notes"></a><span data-ttu-id="378e7-151">Hinweise zur erstellten App</span><span class="sxs-lookup"><span data-stu-id="378e7-151">Built app notes</span></span>

<span data-ttu-id="378e7-152">Erstellen und Bereitstellen in HoloLens auf standardweise Weise.</span><span class="sxs-lookup"><span data-stu-id="378e7-152">Build and deploy to HoloLens in the standard way.</span></span> <span data-ttu-id="378e7-153">Nach der Ausführung sollte eine Reihe von Schaltflächen mit den Features wiedergegeben werden.</span><span class="sxs-lookup"><span data-stu-id="378e7-153">Once running, a number of buttons should appear to play with the features.</span></span>

<span data-ttu-id="378e7-154">Beachten Sie, dass es einige Fehler beim Erstellen von Abfragen an den Beobachter gibt.</span><span class="sxs-lookup"><span data-stu-id="378e7-154">Note, their are some pit falls in making queries to the observer.</span></span> <span data-ttu-id="378e7-155">Eine fehlkonfigurierte Abrufanforderung führt dazu, dass Ihre Ereignisnutzlast nicht die erwarteten Daten enthält.</span><span class="sxs-lookup"><span data-stu-id="378e7-155">Misconfiguration of a fetch request result in your event payload not containing the expected data.</span></span> <span data-ttu-id="378e7-156">Wenn sie beispielsweise keine Quader anfordert, sind keine Textur der Verdeckungsmaske vorhanden.</span><span class="sxs-lookup"><span data-stu-id="378e7-156">For example, if one doesn't request quads, then no occlusion mask textures will be present.</span></span> <span data-ttu-id="378e7-157">Wie weise wird kein Weltgitternetz angezeigt, wenn der Beobachter nicht für das Anfordern von Gitternetzen konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="378e7-157">Like wise, no world mesh will appear if the observer is not configured to request meshes.</span></span> <span data-ttu-id="378e7-158">Das `DemoSceneUnderstandingController` Skript übernimmt einige dieser Abhängigkeiten, aber nicht alle.</span><span class="sxs-lookup"><span data-stu-id="378e7-158">The `DemoSceneUnderstandingController` script takes care of some of these dependencies, but not all.</span></span>

<span data-ttu-id="378e7-159">Auf gespeicherte Szenendateien kann über das [Geräteportal](/windows/mixed-reality/using-the-windows-device-portal) unter zugegriffen `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` werden.</span><span class="sxs-lookup"><span data-stu-id="378e7-159">Saved scene files can be accessed through the [device portal](/windows/mixed-reality/using-the-windows-device-portal) at `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes`.</span></span> <span data-ttu-id="378e7-160">Diese Szenendateien können im Editor verwendet werden, indem sie im Beobachterprofil des Inspektors angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="378e7-160">These scene files can be used in editor by specifying them in the observer profile found in the inspector.</span></span>

![Geräteportal Speicherort der Bytedatei](../images/spatial-awareness/BytesInDevicePortal.png)

![Serialisierte Szenenbytes im Beobachter](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a><span data-ttu-id="378e7-163">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="378e7-163">See Also</span></span>

* [<span data-ttu-id="378e7-164">Übersicht über die räumliche Zuordnung – WMR</span><span class="sxs-lookup"><span data-stu-id="378e7-164">Spatial Mapping Overview WMR</span></span>](/windows/mixed-reality/scene-understanding)
* [<span data-ttu-id="378e7-165">Übersicht über spatial mapping WMR</span><span class="sxs-lookup"><span data-stu-id="378e7-165">Spatial Mapping Overview WMR</span></span>](/windows/mixed-reality/scene-understanding-sdk)