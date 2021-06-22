---
title: Szenenverständnis
description: beschreibt Scene Understanding im MRTK
author: MaxWang-MS
ms.author: wangmax
ms.date: 05/27/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Scene Understanding
ms.openlocfilehash: 67a8b99a281b6deecd621edb5600578806812d8a
ms.sourcegitcommit: 86fafb3a7ac6a5f60340ae5041619e488223f4f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "112449749"
---
# <a name="scene-understanding"></a><span data-ttu-id="2bfe2-104">Szenenverständnis</span><span class="sxs-lookup"><span data-stu-id="2bfe2-104">Scene Understanding</span></span>

<span data-ttu-id="2bfe2-105">[Scene Understanding](/windows/mixed-reality/scene-understanding) gibt eine semantische Darstellung von Szenenentitäten sowie __ihre__ geometrischen Formen auf HoloLens 2 zurück (HoloLens 1. Generation wird nicht unterstützt).</span><span class="sxs-lookup"><span data-stu-id="2bfe2-105">[Scene Understanding](/windows/mixed-reality/scene-understanding) returns a semantic representation of scene entities as well as their geometric forms on __HoloLens 2__ (HoloLens 1st Gen is not supported).</span></span>

<span data-ttu-id="2bfe2-106">Zu den erwarteten Anwendungsfällen dieser Technologie gehören:</span><span class="sxs-lookup"><span data-stu-id="2bfe2-106">Some expected use cases of this technology are:</span></span>
* <span data-ttu-id="2bfe2-107">Platzieren von Objekten auf der nächstgelegenen Oberfläche einer bestimmten Art (z. B. Wand und Boden)</span><span class="sxs-lookup"><span data-stu-id="2bfe2-107">Place objects on nearest surface of a certain kind (e.g. wall and floor)</span></span>
* <span data-ttu-id="2bfe2-108">Erstellen eines Navigationsgitters für Spiele im Plattformstil</span><span class="sxs-lookup"><span data-stu-id="2bfe2-108">Construct nav-mesh for platform style games</span></span>
* <span data-ttu-id="2bfe2-109">Bereitstellen von benutzerfreundlichen Geometrien für physikalische Triebwerke als Quader</span><span class="sxs-lookup"><span data-stu-id="2bfe2-109">Provide physics engine friendly geometry as quads</span></span>
* <span data-ttu-id="2bfe2-110">Beschleunigen der Entwicklung durch Vermeiden der Notwendigkeit, ähnliche Algorithmen zu schreiben</span><span class="sxs-lookup"><span data-stu-id="2bfe2-110">Accelerate development by avoiding the need to write similar algorithms</span></span>

<span data-ttu-id="2bfe2-111">Scene Understanding wird als __experimentelles Feature__ in MRTK 2.6 eingeführt.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-111">Scene Understanding is introduced as an __experimental__ feature in MRTK 2.6.</span></span> <span data-ttu-id="2bfe2-112">Es ist als räumlicher [](spatial-awareness-getting-started.md#register-observers) Beobachter namens in MRTK [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) integriert.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-112">It is integrated into MRTK as a [spatial observer](spatial-awareness-getting-started.md#register-observers) called [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver).</span></span> <span data-ttu-id="2bfe2-113">Scene Understanding funktioniert sowohl mit der Legacy-XR-Pipeline als auch mit der XR SDK-Pipeline (openXR (ab MRTK 2.7) und dem Windows XR-Plug-In.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-113">Scene Understanding works both with the Legacy XR pipeline and the XR SDK pipeline (both OpenXR (starting from MRTK 2.7) and Windows XR Plugin).</span></span> <span data-ttu-id="2bfe2-114">In beiden Fällen `WindowsSceneUnderstandingObserver` wird verwendet.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-114">In both cases the `WindowsSceneUnderstandingObserver` is used.</span></span>

> [!NOTE] 
> <span data-ttu-id="2bfe2-115">Die Verwendung von Scene Understanding in Remoting wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-115">Using Scene Understanding in Remoting is not supported.</span></span>

## <a name="observer-overview"></a><span data-ttu-id="2bfe2-116">Observer-Übersicht</span><span class="sxs-lookup"><span data-stu-id="2bfe2-116">Observer overview</span></span>

<span data-ttu-id="2bfe2-117">Wenn sie dazu aufgefordert wird, gibt [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) mit Attributen zurück, die für die Anwendung nützlich sind, um ihre Umgebung zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-117">When asked, the [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) will return [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) with attributes useful for the application to understand its surroundings.</span></span> <span data-ttu-id="2bfe2-118">Die Beobachtungshäufigkeit, der zurückgegebene Objekttyp (z. B. Wand, Boden) und andere Beobachterverhalten sind von der Konfiguration des Beobachters über das Profil abhängig.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-118">The observation frequency, returned object type (e.g. wall, floor) and other observer behaviors are dependent on the configuration of the observer via profile.</span></span> <span data-ttu-id="2bfe2-119">Wenn beispielsweise die Okklusionsmaske gewünscht wird, muss der Beobachter so konfiguriert werden, dass Quads generiert werden.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-119">For instance, if the occlusion mask is desired the observer must be configured to generate quads.</span></span> <span data-ttu-id="2bfe2-120">Die beobachtete Szene kann als serialisierte Datei gespeichert werden, die später geladen werden kann, um die Szene im Editor-Wiedergabemodus neu zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-120">The observed scene can be saved as serialized file that can be later loaded to recreate the scene in editor play mode.</span></span>

## <a name="setup"></a><span data-ttu-id="2bfe2-121">Einrichten</span><span class="sxs-lookup"><span data-stu-id="2bfe2-121">Setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2bfe2-122">Scene Understanding wird nur unter HoloLens 2 und Unity 2019.4 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-122">Scene Understanding is only supported on HoloLens 2 and Unity 2019.4 and higher.</span></span>

1. <span data-ttu-id="2bfe2-123">Stellen Sie sicher, dass die Plattform in den Buildeinstellungen auf UWP festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-123">Ensure the platform is set to UWP in build settings.</span></span>
1. <span data-ttu-id="2bfe2-124">Erwerben Sie das Scene Understanding-Paket über [Mixed Reality FeatureTool.](https://aka.ms/MRFeatureTool)</span><span class="sxs-lookup"><span data-stu-id="2bfe2-124">Acquire the Scene Understanding package via [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool).</span></span>

## <a name="using-scene-understanding"></a><span data-ttu-id="2bfe2-125">Verwenden von Scene Understanding</span><span class="sxs-lookup"><span data-stu-id="2bfe2-125">Using Scene Understanding</span></span>

<span data-ttu-id="2bfe2-126">Die schnellste Möglichkeit, mit Scene Understanding zu beginnen, besteht im Überprüfen der Beispielszene.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-126">The quickest way to get started with Scene Understanding is to check out the sample scene.</span></span>

### <a name="scene-understanding-sample-scene"></a><span data-ttu-id="2bfe2-127">Scene Understanding-Beispielszene</span><span class="sxs-lookup"><span data-stu-id="2bfe2-127">Scene Understanding sample scene</span></span>

<span data-ttu-id="2bfe2-128">Verwenden Sie in Unity den Projekt-Explorer, um die Szenendatei in zu öffnen `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` und die Wiedergabe zu drücken.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-128">In Unity, use the Project Explorer to open the scene file in `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` and press play!</span></span>

::: moniker range="< mrtkunity-2021-05"
> [!IMPORTANT]
> <span data-ttu-id="2bfe2-129">Gilt nur für MRTK 2.6.0: Wenn Sie das Mixed Reality Feature Tool verwenden oder anderweitig über UPM importieren, importieren Sie das Beispiel Demos – SpatialAwareness, bevor Sie das Experimentell – SceneUnderstanding-Beispiel aufgrund eines Abhängigkeitsproblems importieren.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-129">Only applies to MRTK 2.6.0 - When using the Mixed Reality Feature Tool or otherwise importing via UPM, please import the Demos - SpatialAwareness sample before importing the Experimental - SceneUnderstanding sample due to a dependency issue.</span></span> <span data-ttu-id="2bfe2-130">Weitere Informationen [finden Sie in diesem GitHub-Problem.](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431)</span><span class="sxs-lookup"><span data-stu-id="2bfe2-130">Please see [this GitHub issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) for more information.</span></span>

::: moniker-end
<span data-ttu-id="2bfe2-131">Die Szene veranschaulicht Folgendes:</span><span class="sxs-lookup"><span data-stu-id="2bfe2-131">The scene demonstrates the following:</span></span>

* <span data-ttu-id="2bfe2-132">Visualisierung beobachteter Szenenobjekte mit in der Anwendungsbenutzeroberfläche zum Konfigurieren des Beobachters</span><span class="sxs-lookup"><span data-stu-id="2bfe2-132">Visualization of observed Scene Objects with in application UI for configuring the observer</span></span>
* <span data-ttu-id="2bfe2-133">`DemoSceneUnderstandingController`Beispielskript, das zeigt, wie Sie Beobachtereinstellungen ändern und auf relevante Ereignisse lauschen.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-133">Example `DemoSceneUnderstandingController` script that shows how to change observer settings and listen to relevant events</span></span>
* <span data-ttu-id="2bfe2-134">Speichern von Szenendaten auf dem Gerät für die Offlineentwicklung</span><span class="sxs-lookup"><span data-stu-id="2bfe2-134">Saving scene data to device for offline development</span></span>
* <span data-ttu-id="2bfe2-135">Laden zuvor gespeicherter Szenendaten (BYTES-Dateien) zur Unterstützung des Entwicklungsworkflows im Editor</span><span class="sxs-lookup"><span data-stu-id="2bfe2-135">Loading previously saved scene data (.bytes files) to support in-editor development workflow</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2bfe2-136">Standardmäßig ist `ShouldLoadFromFile` die -Eigenschaft des Beobachters auf FALSE festgelegt.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-136">By default the `ShouldLoadFromFile` property of the observer is set to false.</span></span> <span data-ttu-id="2bfe2-137">Um die Visualisierung eines serialisierten Beispielraums zu sehen, lesen Sie den abschnitt [konfigurierenden](#configuring-the-observer-service) Beobachterdienst weiter unten, und legen Sie die Eigenschaft im Editor auf TRUE fest.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-137">In order to see the visualization of a serialized sample room, please refer to the [configuring observer service](#configuring-the-observer-service) section below and set the property to true in the editor.</span></span>
::: moniker range="< mrtkunity-2021-05"

> [!NOTE] 
> <span data-ttu-id="2bfe2-138">Die Beispielszene basiert auf der Legacy-XR-Pipeline.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-138">The sample scene is based on the Legacy XR pipeline.</span></span> <span data-ttu-id="2bfe2-139">Wenn Sie die XR SDK-Pipeline verwenden, sollten Sie die Profile entsprechend ändern.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-139">If you are using the XR SDK pipeline you should modify the profiles accordingly.</span></span> <span data-ttu-id="2bfe2-140">Das bereitgestellte Scene Understanding Spatial Awareness System-Profil ( `DemoSceneUnderstandingSystemProfile` ) und die Scene Understanding Observer-Profile ( und ) funktionieren für beide `DefaultSceneUnderstandingObserverProfile` `DemoSceneUnderstandingObserverProfile` Pipelines.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-140">The provided Scene Understanding Spatial Awareness System profile (`DemoSceneUnderstandingSystemProfile`) and the Scene Understanding Observer profiles (`DefaultSceneUnderstandingObserverProfile` and `DemoSceneUnderstandingObserverProfile`) works for both pipelines.</span></span>
::: moniker-end
::: moniker range="= mrtkunity-2021-05"

> [!NOTE] 
> <span data-ttu-id="2bfe2-141">Die Beispielszene protokolliert eine Warnung unter bestimmten Umständen aufgrund `There is no active AsyncCoroutineRunner when an action is posted.` der Initialisierungs-/Threadausführungs reihenfolge.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-141">The sample scene logs a `There is no active AsyncCoroutineRunner when an action is posted.` warning under certain circumstance due to the initialization/thread execution order.</span></span> <span data-ttu-id="2bfe2-142">Wenn Sie bestätigen können, dass die Komponente an das GameObject "Demo Controller" angefügt ist und die Komponente/das GameObject in der Szene aktiviert/aktiv bleibt (Standardfall), kann die Warnung sicher ignoriert `AsyncCoroutineRunner` werden.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-142">If you can confirm the `AsyncCoroutineRunner` component is attached to the "Demo Controller" GameObject and the component/GameObject stay enabled/active in the scene (the default case), the warning can be safely ignored.</span></span> <span data-ttu-id="2bfe2-143">**Wenn Sie jedoch eine neue Szene mit Scene Understanding erstellen, stellen Sie sicher, dass Sie ein leeres GameObject im Stammverzeichnis erstellen und das Skript an dieses anfügen. Andernfalls funktioniert Scene Understanding möglicherweise `AsyncCoroutineRunner` nicht ordnungsgemäß.**</span><span class="sxs-lookup"><span data-stu-id="2bfe2-143">**However, when creating a new scene with Scene Understanding please make sure to create an empty GameObject at root and attach the `AsyncCoroutineRunner` script to it, otherwise Scene Understanding may not function properly.**</span></span>
::: moniker-end

#### <a name="configuring-the-observer-service"></a><span data-ttu-id="2bfe2-144">Konfigurieren des Observer-Diensts</span><span class="sxs-lookup"><span data-stu-id="2bfe2-144">Configuring the observer service</span></span>

<span data-ttu-id="2bfe2-145">Wählen Sie das Spielobjekt "MixedRealityToolkit" aus, und überprüfen Sie den Inspektor.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-145">Select the 'MixedRealityToolkit' game object and check the inspector.</span></span>

![Szenenverständnis des Standorts in der Hierarchie](../images/spatial-awareness/MRTKHierarchy.png)

![MRTK-Standort im Inspektor](../images/spatial-awareness/MRTKLocation.png)

<span data-ttu-id="2bfe2-148">Mit diesen Optionen kann konfiguriert `WindowsSceneUnderstandingObserver` werden.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-148">These options will allow one to configure the `WindowsSceneUnderstandingObserver`.</span></span>

### <a name="example-script"></a><span data-ttu-id="2bfe2-149">Beispielskript</span><span class="sxs-lookup"><span data-stu-id="2bfe2-149">Example script</span></span>

<span data-ttu-id="2bfe2-150">Das Beispielskript _DemoSceneUnderstandingController.cs_ veranschaulicht die wichtigsten Konzepte bei der Arbeit mit dem Scene Understanding-Dienst.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-150">The example script _DemoSceneUnderstandingController.cs_ demonstrates the major concepts in working with the Scene Understanding service.</span></span>

* <span data-ttu-id="2bfe2-151">Abonnieren von Scene Understanding-Ereignissen</span><span class="sxs-lookup"><span data-stu-id="2bfe2-151">Subscribing to Scene Understanding events</span></span>
* <span data-ttu-id="2bfe2-152">Behandeln von Scene Understanding-Ereignissen</span><span class="sxs-lookup"><span data-stu-id="2bfe2-152">Handling Scene Understanding events</span></span>
* <span data-ttu-id="2bfe2-153">Konfigurieren von zur `WindowsSceneUnderstandingObserver` Laufzeit</span><span class="sxs-lookup"><span data-stu-id="2bfe2-153">Configuring the `WindowsSceneUnderstandingObserver` at runtime</span></span>

<span data-ttu-id="2bfe2-154">Die Umschalter im Bereich der Szene ändern das Verhalten des Szenenverständnisbeobachter, indem sie öffentliche Funktionen dieses Beispielskripts aufrufen.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-154">The toggles on the panel in the scene change the behavior of scene understanding observer by calling public functions of this sample script.</span></span>

<span data-ttu-id="2bfe2-155">Wenn Sie *Prefabs instanziieren* aktivieren, wird das Erstellen von Objekten veranschaulicht, deren Größe sich an alle [SpatialAwarenessSceneObject-Objekte](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject)anpasst, die unter einem übergeordneten Objekt sauber gesammelt werden.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-155">Turning on *Instantiate Prefabs*, will demonstrate creating objects that size to fit themselves to all [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject), gathered neatly under a parent object.</span></span>

![Democontrolleroptionen](../images/spatial-awareness/Controller.png)

### <a name="built-app-notes"></a><span data-ttu-id="2bfe2-157">Hinweise zur erstellten App</span><span class="sxs-lookup"><span data-stu-id="2bfe2-157">Built app notes</span></span>

<span data-ttu-id="2bfe2-158">Erstellen Und bereitstellen Sie HoloLens auf die Standard weise.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-158">Build and deploy to HoloLens in the standard way.</span></span> <span data-ttu-id="2bfe2-159">Nach der Ausführung sollte eine Reihe von Schaltflächen mit den Features zu spielen scheinen.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-159">Once running, a number of buttons should appear to play with the features.</span></span>

<span data-ttu-id="2bfe2-160">Beachten Sie, dass es einige Fehler beim Ausführen von Abfragen an den Beobachter gibt.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-160">Note, their are some pit falls in making queries to the observer.</span></span> <span data-ttu-id="2bfe2-161">Eine fehlkonfigurierte Abrufanforderung führt dazu, dass Ihre Ereignisnutzlast nicht die erwarteten Daten enthält.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-161">Misconfiguration of a fetch request result in your event payload not containing the expected data.</span></span> <span data-ttu-id="2bfe2-162">Wenn sie beispielsweise keine Quads anfordern, sind keine Okklusionsmaskentexturen vorhanden.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-162">For example, if one doesn't request quads, then no occlusion mask textures will be present.</span></span> <span data-ttu-id="2bfe2-163">Wie weise wird kein World Mesh angezeigt, wenn der Beobachter nicht für das Anfordern von Gitternetzen konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-163">Like wise, no world mesh will appear if the observer is not configured to request meshes.</span></span> <span data-ttu-id="2bfe2-164">Das `DemoSceneUnderstandingController` Skript übernimmt einige dieser Abhängigkeiten, aber nicht alle.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-164">The `DemoSceneUnderstandingController` script takes care of some of these dependencies, but not all.</span></span>

<span data-ttu-id="2bfe2-165">Auf gespeicherte Szenendateien kann über das [Geräteportal unter zugegriffen](/windows/mixed-reality/using-the-windows-device-portal) `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` werden.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-165">Saved scene files can be accessed through the [device portal](/windows/mixed-reality/using-the-windows-device-portal) at `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes`.</span></span> <span data-ttu-id="2bfe2-166">Diese Szenendateien können im Editor verwendet werden, indem sie im Beobachterprofil im Inspektor angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="2bfe2-166">These scene files can be used in editor by specifying them in the observer profile found in the inspector.</span></span>

![Geräteportal Speicherort der Bytesdatei](../images/spatial-awareness/BytesInDevicePortal.png)

![Serialisierte Szenenbytes in Observer](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a><span data-ttu-id="2bfe2-169">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="2bfe2-169">See Also</span></span>

* [<span data-ttu-id="2bfe2-170">Übersicht über Scene Understanding</span><span class="sxs-lookup"><span data-stu-id="2bfe2-170">Scene Understanding Overview</span></span>](/windows/mixed-reality/scene-understanding)
* [<span data-ttu-id="2bfe2-171">Übersicht über das Scene Understanding SDK</span><span class="sxs-lookup"><span data-stu-id="2bfe2-171">Scene Understanding SDK Overview</span></span>](/windows/mixed-reality/scene-understanding-sdk)