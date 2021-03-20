---
title: Hololens (1. Gen) Grundlagen 100-erste Schritte mit Unity
description: Erfahren Sie, wie Sie Ihre erste grundlegende gemischte "Hello World"-Anwendung für hololens und Windows Mixed Reality-Geräte erstellen.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Mixed Reality, Windows Mixed Reality, hololens, immersive, VR, Mr, Get Started, Hologram, Academy, Tutorial, Mixed Reality Academy, Unity, Mixed Reality Headset, Windows Mixed Reality Headset, Virtual Reality Headset
ms.openlocfilehash: 999ab7dc87a639f10aad9eaf2a7ef8de2cf92633
ms.sourcegitcommit: 35bd43624be33afdb1bf6ba4ddbe36d268eb9bda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2021
ms.locfileid: "104730357"
---
# <a name="hololens-1st-gen-basics-100-getting-started-with-unity"></a><span data-ttu-id="80268-104">Hololens (1. Gen) Grundlagen 100: Erste Schritte mit Unity</span><span class="sxs-lookup"><span data-stu-id="80268-104">HoloLens (1st gen) Basics 100: Getting started with Unity</span></span>

>[!IMPORTANT]
><span data-ttu-id="80268-105">Die Tutorials der Mixed Reality Academy wurden im Hinblick auf HoloLens (1. Gen.) und immersive Mixed Reality-Headsets entworfen.</span><span class="sxs-lookup"><span data-stu-id="80268-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="80268-106">Daher halten wir es für wichtig, diese Tutorials für Entwickler verfügbar zu halten, die noch nach Anleitung beim Entwickeln für diese Geräte suchen.</span><span class="sxs-lookup"><span data-stu-id="80268-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="80268-107">Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für HoloLens 2 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="80268-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="80268-108">Sie werden gewartet, um weiterhin auf den unterstützten Geräten zu funktionieren.</span><span class="sxs-lookup"><span data-stu-id="80268-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="80268-109">[Es wurde eine neue Reihe von Tutorials](mrlearning-base.md) für HoloLens 2 veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="80268-109">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<span data-ttu-id="80268-110">Dieses Tutorial führt Sie durch die Erstellung einer einfachen Mixed Reality-APP, die mit Unity erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="80268-110">This tutorial will walk you through creating a basic mixed reality app built with Unity.</span></span>

## <a name="device-support"></a><span data-ttu-id="80268-111">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="80268-111">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="80268-112">Kurs</span><span class="sxs-lookup"><span data-stu-id="80268-112">Course</span></span></th><th style="width:150px"> <span data-ttu-id="80268-113"><a href="/hololens/hololens1-hardware">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="80268-113"><a href="/hololens/hololens1-hardware">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="80268-114"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive Headsets</a></span><span class="sxs-lookup"><span data-stu-id="80268-114"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="80268-115">MR-Grundlagen 100: Erste Schritte mit Unity</span><span class="sxs-lookup"><span data-stu-id="80268-115">MR Basics 100: Getting started with Unity</span></span></td><td style="text-align: center;"> <span data-ttu-id="80268-116">✔️</span><span class="sxs-lookup"><span data-stu-id="80268-116">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="80268-117">✔️</span><span class="sxs-lookup"><span data-stu-id="80268-117">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="80268-118">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="80268-118">Prerequisites</span></span>

* <span data-ttu-id="80268-119">Ein Windows 10-PC, der mit den richtigen [installierten Tools](../../install-the-tools.md)konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="80268-119">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md).</span></span>

## <a name="chapter-1---create-a-new-project"></a><span data-ttu-id="80268-120">Kapitel 1: Erstellen eines neuen Projekts</span><span class="sxs-lookup"><span data-stu-id="80268-120">Chapter 1 - Create a New Project</span></span>

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

<span data-ttu-id="80268-121">Zum Erstellen einer APP mit Unity müssen Sie zunächst ein Projekt erstellen.</span><span class="sxs-lookup"><span data-stu-id="80268-121">To build an app with Unity, you first need to create a project.</span></span> <span data-ttu-id="80268-122">Dieses Projekt ist in einigen Ordnern organisiert, wobei es sich bei den wichtigsten Elementen um den Ordner "Assets" handelt.</span><span class="sxs-lookup"><span data-stu-id="80268-122">This project is organized into a few folders, the most important of which is your Assets folder.</span></span> <span data-ttu-id="80268-123">Dabei handelt es sich um den Ordner, der alle Ressourcen enthält, die Sie aus Tools für die Erstellung digitaler Inhalte importieren, wie z. b. Maya, max. Kino 4D oder Photoshop, sämtlichen Code, den Sie mit Visual Studio oder Ihrem bevorzugten Code-Editor erstellen, und beliebig viele Inhalts Dateien, die Unity erstellt, wenn Sie Szenen, Animationen und andere Unity-Ressourcentypen</span><span class="sxs-lookup"><span data-stu-id="80268-123">This is the folder that holds all assets you import from digital content creation tools such as Maya, Max Cinema 4D or Photoshop, all code you create with Visual Studio or your favorite code editor, and any number of content files that Unity creates as you compose scenes, animations and other Unity asset types in the editor.</span></span>

<span data-ttu-id="80268-124">Um UWP-apps zu erstellen und bereitzustellen, kann Unity das Projekt als Visual Studio-Projekt Mappe exportieren, die alle erforderlichen Medienobjekt-und Code Dateien enthält.</span><span class="sxs-lookup"><span data-stu-id="80268-124">To build and deploy UWP apps, Unity can export the project as a Visual Studio solution that will contain all necessary asset and code files.</span></span>

1. <span data-ttu-id="80268-125">Unity starten</span><span class="sxs-lookup"><span data-stu-id="80268-125">Start Unity</span></span>
2. <span data-ttu-id="80268-126">Wählen Sie **Neu** aus.</span><span class="sxs-lookup"><span data-stu-id="80268-126">Select **New**</span></span>
3. <span data-ttu-id="80268-127">Geben Sie einen Projektnamen ein (z. b. "mixedrealityintroduction").</span><span class="sxs-lookup"><span data-stu-id="80268-127">Enter a project name (e.g. "MixedRealityIntroduction")</span></span>
4. <span data-ttu-id="80268-128">Geben Sie einen Speicherort zum Speichern Ihres Projekts ein.</span><span class="sxs-lookup"><span data-stu-id="80268-128">Enter a location to save your project</span></span>
5. <span data-ttu-id="80268-129">Stellen Sie sicher, dass der **3D-** Schalter ausgewählt ist</span><span class="sxs-lookup"><span data-stu-id="80268-129">Ensure the **3D** toggle is selected</span></span>
6. <span data-ttu-id="80268-130">**Projekt erstellen** auswählen</span><span class="sxs-lookup"><span data-stu-id="80268-130">Select **Create project**</span></span>

<span data-ttu-id="80268-131">Herzlichen Glückwunsch, Sie sind alle Setup für die ersten Schritte mit ihren Mixed Reality-Anpassungen.</span><span class="sxs-lookup"><span data-stu-id="80268-131">Congrats, you are all setup to get started with your mixed reality customizations now.</span></span>

## <a name="chapter-2---setup-the-camera"></a><span data-ttu-id="80268-132">Kapitel 2: Einrichten der Kamera</span><span class="sxs-lookup"><span data-stu-id="80268-132">Chapter 2 - Setup the Camera</span></span>

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

<span data-ttu-id="80268-133">Die Unity-Hauptkamera behandelt die Kopf-und stereorenderingvorgänge.</span><span class="sxs-lookup"><span data-stu-id="80268-133">The Unity Main Camera handles head tracking and stereoscopic rendering.</span></span> <span data-ttu-id="80268-134">An der Hauptkamera müssen einige Änderungen vorgenommen werden, damit Sie mit gemischter Realität verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="80268-134">There are a few changes to make to the Main Camera to use it with mixed reality.</span></span>

1. <span data-ttu-id="80268-135">Datei > neuen Szene auswählen</span><span class="sxs-lookup"><span data-stu-id="80268-135">Select File > New Scene</span></span>

<span data-ttu-id="80268-136">Erstens ist es einfacher, Ihre APP zu entwerfen, wenn Sie sich die Anfangsposition des Benutzers als (**X**: 0, **Y**: 0, **Z**: 0) vorstellen.</span><span class="sxs-lookup"><span data-stu-id="80268-136">First, it will be easier to lay out your app if you imagine the starting position of the user as (**X**: 0, **Y**: 0, **Z**: 0).</span></span> <span data-ttu-id="80268-137">Da die Hauptkamera die Bewegung des Benutzers nachverfolgt, kann die Startposition des Benutzers festgelegt werden, indem die Startposition der Hauptkamera festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="80268-137">Since the Main Camera is tracking movement of the user's head, the starting position of the user can be set by setting the starting position of the Main Camera.</span></span>

1. <span data-ttu-id="80268-138">Auswählen der **Hauptkamera** im **Hierarchie** Panel</span><span class="sxs-lookup"><span data-stu-id="80268-138">Select **Main Camera** in the **Hierarchy** panel</span></span>
2. <span data-ttu-id="80268-139">Suchen Sie im **Inspektor** -Panel die **Transformations** Komponente, und ändern Sie die **Position** von (**x**: 0, **y**: 1, **z**:-10) in (**x**: 0, **y**: 0, **z**: 0).</span><span class="sxs-lookup"><span data-stu-id="80268-139">In the **Inspector** panel, find the **Transform** component and change the **Position** from (**X**: 0, **Y**: 1, **Z**: -10) to (**X**: 0, **Y**: 0, **Z**: 0)</span></span>

<span data-ttu-id="80268-140">Zweitens benötigt der Standard Hintergrund der Kamera einige Gedanken.</span><span class="sxs-lookup"><span data-stu-id="80268-140">Second, the default Camera background needs some thought.</span></span>

<span data-ttu-id="80268-141">**Bei hololens-Anwendungen** sollte die reale Welt hinter alles stehen, was von der Kamera gerendert wird, und keine Skybox-Textur.</span><span class="sxs-lookup"><span data-stu-id="80268-141">**For HoloLens applications**, the real world should appear behind everything the camera renders, not a Skybox texture.</span></span>

1. <span data-ttu-id="80268-142">Wenn im Bereich **Hierarchie** weiterhin die **Hauptkamera** ausgewählt ist, suchen Sie im **Inspektor** -Panel nach der **Kamera** Komponente, und ändern Sie die Dropdown Liste **Flag löschen** von **Skybox** in voll **Tonfarbe**.</span><span class="sxs-lookup"><span data-stu-id="80268-142">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Clear Flags** dropdown from **Skybox** to **Solid Color**.</span></span>
2. <span data-ttu-id="80268-143">Wählen Sie die **Hintergrund** Farbauswahl aus, und ändern Sie die **RGBA** -Werte in (0,0).</span><span class="sxs-lookup"><span data-stu-id="80268-143">Select the **Background** color picker and change the **RGBA** values to (0, 0, 0, 0)</span></span>

<span data-ttu-id="80268-144">**Für gemischte Reality-Anwendungen, die auf immersive Headsets ausgerichtet** sind, können wir die von Unity bereitgestellte Standard Textur von Skybox verwenden.</span><span class="sxs-lookup"><span data-stu-id="80268-144">**For mixed reality applications targeted to immersive headsets**, we can use the default Skybox texture that Unity provides.</span></span>

1. <span data-ttu-id="80268-145">Wenn im **Hierarchie** Panel noch die **Hauptkamera** ausgewählt ist, suchen Sie im **Inspektor** -Panel nach der **Kamera** Komponente, und lassen Sie die Dropdown Liste **Flag löschen** auf **Skybox**.</span><span class="sxs-lookup"><span data-stu-id="80268-145">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Clear Flags** dropdown to **Skybox**.</span></span>

<span data-ttu-id="80268-146">Als drittes betrachten wir die Near-Clip-Ebene in Unity und verhindern, dass Objekte zu nah an den Benutzern gerendert werden, wenn ein Benutzer ein Objekt nähert oder ein Objekt einen Benutzer nähert.</span><span class="sxs-lookup"><span data-stu-id="80268-146">Third, let us consider the near clip plane in Unity and prevent objects from being rendered too close to the users eyes as a user approaches an object or an object approaches a user.</span></span>

<span data-ttu-id="80268-147">**Bei hololens-Anwendungen** kann die Near-Clip-Ebene auf die [hololens-empfohlenen](../camera-in-unity.md#clip-planes) 0,85 Meter festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="80268-147">**For HoloLens applications**, the near clip plane can be set to the [HoloLens recommended](../camera-in-unity.md#clip-planes) 0.85 meters.</span></span>

1. <span data-ttu-id="80268-148">Wenn im **Hierarchie** Panel noch die **Hauptkamera** ausgewählt ist, suchen Sie im **Inspektor** -Panel nach der **Kamera** Komponente, und ändern Sie das Feld **near-Clip Plane** von der Standardeinstellung **0,3** in das Feld hololens Recommended **0,85**.</span><span class="sxs-lookup"><span data-stu-id="80268-148">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Near Clip Plane** field from the default **0.3** to the HoloLens recommended **0.85**.</span></span>

<span data-ttu-id="80268-149">**Für gemischte Reality-Anwendungen, die auf immersive Headsets ausgerichtet** sind, können wir die von Unity bereitgestellte Standardeinstellung verwenden.</span><span class="sxs-lookup"><span data-stu-id="80268-149">**For mixed reality applications targeted to immersive headsets**, we can use the default setting that Unity provides.</span></span>

1. <span data-ttu-id="80268-150">Wenn im Bereich **Hierarchie** weiterhin die **Hauptkamera** ausgewählt ist, suchen Sie im **Inspektor** -Panel nach der **Kamera** Komponente, und lassen Sie das Feld **near Clip Plane** auf den Standardwert **0,3**.</span><span class="sxs-lookup"><span data-stu-id="80268-150">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Near Clip Plane** field to the default **0.3**.</span></span>

<span data-ttu-id="80268-151">Abschließend können wir unseren Fortschritt speichern.</span><span class="sxs-lookup"><span data-stu-id="80268-151">Finally, let us save our progress so far.</span></span> <span data-ttu-id="80268-152">Um die Szenen Änderungen zu speichern, klicken Sie auf **Datei > Szene speichern** unter, benennen Sie **die Szene,** und wählen Sie **Speichern** aus.</span><span class="sxs-lookup"><span data-stu-id="80268-152">To save the scene changes, select **File > Save Scene As**, name the scene **Main**, and select **Save**.</span></span>

## <a name="chapter-3---setup-the-project-settings"></a><span data-ttu-id="80268-153">Kapitel 3: Einrichten der Projekteinstellungen</span><span class="sxs-lookup"><span data-stu-id="80268-153">Chapter 3 - Setup the Project Settings</span></span>

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

<span data-ttu-id="80268-154">In diesem Kapitel werden einige Unity-Projekteinstellungen festgelegt, die uns dabei helfen, das Windows Holographic SDK für die Entwicklung zu entwickeln.</span><span class="sxs-lookup"><span data-stu-id="80268-154">In this chapter, we will set some Unity project settings that help us target the Windows Holographic SDK for development.</span></span> <span data-ttu-id="80268-155">Wir legen auch einige Qualitätseinstellungen für die Anwendung fest.</span><span class="sxs-lookup"><span data-stu-id="80268-155">We will also set some quality settings for our application.</span></span> <span data-ttu-id="80268-156">Abschließend wird sichergestellt, dass unsere Buildziele auf universelle Windows-Plattform festgelegt sind.</span><span class="sxs-lookup"><span data-stu-id="80268-156">Finally, we will ensure our build targets are set to Universal Windows Platform.</span></span>

### <a name="unity-performance-and-quality-settings"></a><span data-ttu-id="80268-157">Unity-Leistungs-und Qualitätseinstellungen</span><span class="sxs-lookup"><span data-stu-id="80268-157">Unity performance and quality settings</span></span>

<span data-ttu-id="80268-158">**Unity-Qualitätseinstellungen für hololens**</span><span class="sxs-lookup"><span data-stu-id="80268-158">**Unity quality settings for HoloLens**</span></span>

![Unity-Qualitätseinstellungen für hololens](images/qualitysettings.png)

<span data-ttu-id="80268-160">Da das Verwalten von hoher Framerate in hololens so wichtig ist, möchten wir, dass die Qualitätseinstellungen für die schnellste Leistung optimiert werden.</span><span class="sxs-lookup"><span data-stu-id="80268-160">Since maintaining high framerate on HoloLens is so important, we want the quality settings tuned for fastest performance.</span></span> <span data-ttu-id="80268-161">Ausführlichere Informationen zur Leistung finden Sie unter [Empfehlungen zur Leistung für Unity](../performance-recommendations-for-unity.md).</span><span class="sxs-lookup"><span data-stu-id="80268-161">For more detailed performance information, [Performance recommendations for Unity](../performance-recommendations-for-unity.md).</span></span>

1. <span data-ttu-id="80268-162">Wählen Sie **> Projekteinstellungen bearbeiten > Qualität** aus.</span><span class="sxs-lookup"><span data-stu-id="80268-162">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="80268-163">Wählen Sie im **universelle Windows-Plattform** Logo die **Dropdown** Liste aus, und wählen Sie **sehr niedrig** aus.</span><span class="sxs-lookup"><span data-stu-id="80268-163">Select the **dropdown** under the **Universal Windows Platform** logo and select **Very Low**.</span></span> <span data-ttu-id="80268-164">Sie werden feststellen, dass die Einstellung ordnungsgemäß angewendet wird, wenn das Feld in der universelle Windows-Plattform-Spalte und die **sehr niedrige** Zeile grün ist.</span><span class="sxs-lookup"><span data-stu-id="80268-164">You'll know the setting is applied correctly when the box in the Universal Windows Platform column and **Very Low** row is green.</span></span>

<span data-ttu-id="80268-165">**Für gemischte Reality-Anwendungen, die für die Anzeige von Anzeigen vorgesehen** sind, können Sie die Qualitätseinstellungen auf die Standardwerte überlassen.</span><span class="sxs-lookup"><span data-stu-id="80268-165">**For mixed reality applications targeted to occluded displays**, you can leave the quality settings to its default values.</span></span>

### <a name="target-windows-10-sdk"></a><span data-ttu-id="80268-166">Windows 10-Ziel-SDK</span><span class="sxs-lookup"><span data-stu-id="80268-166">Target Windows 10 SDK</span></span>

<span data-ttu-id="80268-167">**Windows Holographic-Ziel SDK**</span><span class="sxs-lookup"><span data-stu-id="80268-167">**Target Windows Holographic SDK**</span></span>

![Windows Holographic-Ziel SDK](../images/xrsettings.png)

<span data-ttu-id="80268-169">Wir müssen Unity mitteilen, dass die zu exportierende App eine [immersive Ansicht](../../../design/app-views.md) anstelle einer 2D-Ansicht erstellen sollte.</span><span class="sxs-lookup"><span data-stu-id="80268-169">We need to let Unity know that the app we are trying to export should create an [immersive view](../../../design/app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="80268-170">Dies geschieht durch Aktivieren der Virtual Reality-Unterstützung für Unity, die auf das Windows 10 SDK abzielen.</span><span class="sxs-lookup"><span data-stu-id="80268-170">We do this by enabling Virtual Reality support on Unity targeting the Windows 10 SDK.</span></span>

1. <span data-ttu-id="80268-171">Wechseln Sie zu **Edit > Project Settings > Player**.</span><span class="sxs-lookup"><span data-stu-id="80268-171">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="80268-172">Wählen Sie im **Inspektor-Panel** für die Player-Einstellungen das **universelle Windows-Plattform** Symbol aus.</span><span class="sxs-lookup"><span data-stu-id="80268-172">In the **Inspector Panel** for Player Settings, select the **Universal Windows Platform** icon.</span></span>
3. <span data-ttu-id="80268-173">Erweitern Sie die Gruppe **XR-Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="80268-173">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="80268-174">Aktivieren Sie im Abschnitt **Rendering** das Kontrollkästchen **Virtuelle Realität unterstützt**, um eine neue Liste mit **Virtual Reality-SDKs** hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="80268-174">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="80268-175">Überprüfen Sie, ob in der Liste **Windows Mixed Reality** angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="80268-175">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="80268-176">Wenn nicht, wählen Sie die Schaltfläche **+** am Ende der Liste aus, und wählen Sie **Windows Mixed Reality** aus.</span><span class="sxs-lookup"><span data-stu-id="80268-176">If not, select the **+** button at the bottom of the list and choose **Windows Mixed Reality**.</span></span>

>[!NOTE]
><span data-ttu-id="80268-177">Wenn das **universelle Windows-Plattform** -Symbol nicht angezeigt wird, vergewissern Sie sich, dass Sie während der Installation universelle Windows-Plattform Buildunterstützung ausgewählt haben.</span><span class="sxs-lookup"><span data-stu-id="80268-177">If you do not see the **Universal Windows Platform** icon, double check to make sure you selected Universal Windows Platform Build Support during installation.</span></span> <span data-ttu-id="80268-178">Wenn nicht, müssen Sie Unity eventuell mit der richtigen Windows-Installation neu installieren.</span><span class="sxs-lookup"><span data-stu-id="80268-178">If not, you may need to reinstall Unity with the correct Windows installation.</span></span>

<span data-ttu-id="80268-179">Tolle Aufgabe zum Anwenden aller Projekteinstellungen.</span><span class="sxs-lookup"><span data-stu-id="80268-179">Awesome job on getting all the project settings applied.</span></span> <span data-ttu-id="80268-180">Als Nächstes fügen wir ein Hologram hinzu.</span><span class="sxs-lookup"><span data-stu-id="80268-180">Next, let us add a hologram!</span></span>

## <a name="chapter-4---create-a-cube"></a><span data-ttu-id="80268-181">Kapitel 4: Erstellen eines Cubes</span><span class="sxs-lookup"><span data-stu-id="80268-181">Chapter 4 - Create a cube</span></span>

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

<span data-ttu-id="80268-182">Das Erstellen eines Cubes in Ihrem Unity-Projekt erfolgt genauso wie das Erstellen eines beliebigen anderen Objekts in Unity.</span><span class="sxs-lookup"><span data-stu-id="80268-182">Creating a cube in your Unity project is just like creating any other object in Unity.</span></span> <span data-ttu-id="80268-183">Das Platzieren eines Cubes vor dem Benutzer ist einfach, da das Koordinatensystem von Unity der realen Welt zugeordnet ist, wobei eine Einheit in Unity ungefähr eine Meter in der realen Welt ist.</span><span class="sxs-lookup"><span data-stu-id="80268-183">Placing a cube in front of the user is easy because Unity's coordinate system is mapped to the real world - where one meter in Unity is approximately one meter in the real world.</span></span>

1. <span data-ttu-id="80268-184">Wählen Sie in der oberen linken Ecke des Bereichs **Hierarchie** die Dropdown Liste **Erstellen** aus, und wählen Sie **3D-Objekt > Cube** aus.</span><span class="sxs-lookup"><span data-stu-id="80268-184">In the top left corner of the **Hierarchy** panel, select the **Create** dropdown and choose **3D Object > Cube**.</span></span>
2. <span data-ttu-id="80268-185">Wählen Sie im **Hierarchie** Panel den neu erstellten **Cube** aus.</span><span class="sxs-lookup"><span data-stu-id="80268-185">Select the newly created **Cube** in the **Hierarchy** panel</span></span>
3. <span data-ttu-id="80268-186">Suchen Sie im **Inspektor** die **Transformations** Komponente, und ändern Sie die **Position** in (**X**: 0, **Y**: 0, **Z**: 2).</span><span class="sxs-lookup"><span data-stu-id="80268-186">In the **Inspector** find the **Transform** component and change **Position** to (**X**: 0, **Y**: 0, **Z**: 2).</span></span> <span data-ttu-id="80268-187">*Dadurch wird der Cube 2 Meter vor der Anfangsposition des Benutzers positioniert.*</span><span class="sxs-lookup"><span data-stu-id="80268-187">*This positions the cube 2 meters in front of the user's starting position.*</span></span>
4. <span data-ttu-id="80268-188">Ändern Sie in der **Transformations** Komponente **die Drehung** in (**x**: 45, **y**: 45, **z**: 45), und ändern Sie die **Skalierung** in (**x**: 0,25, **y**: 0,25, **z**: 0,25).</span><span class="sxs-lookup"><span data-stu-id="80268-188">In the **Transform** component, change **Rotation** to (**X**: 45, **Y**: 45, **Z**: 45) and change **Scale** to (**X**: 0.25, **Y**: 0.25, **Z**: 0.25).</span></span> <span data-ttu-id="80268-189">*Dadurch wird der Cube auf 0,25 Meter skaliert.*</span><span class="sxs-lookup"><span data-stu-id="80268-189">*This scales the cube to 0.25 meters.*</span></span>
5. <span data-ttu-id="80268-190">Um die Szenen Änderungen zu speichern, wählen Sie **Datei > Szene speichern** aus.</span><span class="sxs-lookup"><span data-stu-id="80268-190">To save the scene changes, select **File > Save Scene**.</span></span>

## <a name="chapter-5---verify-on-device-from-unity-editor"></a><span data-ttu-id="80268-191">Kapitel 5: Überprüfen des Geräts über den Unity-Editor</span><span class="sxs-lookup"><span data-stu-id="80268-191">Chapter 5 - Verify on device from Unity editor</span></span>

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

<span data-ttu-id="80268-192">Nachdem wir nun den Cube erstellt haben, ist es an der Zeit, eine schnell Überprüfung im Gerät durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="80268-192">Now that we have created our cube, it is time to do a quick check in device.</span></span> <span data-ttu-id="80268-193">Sie können dies direkt im Unity-Editor tun.</span><span class="sxs-lookup"><span data-stu-id="80268-193">You can do this directly from within the Unity editor.</span></span>

### <a name="initial-setup"></a><span data-ttu-id="80268-194">Erste Einrichtung</span><span class="sxs-lookup"><span data-stu-id="80268-194">Initial setup</span></span>

1. <span data-ttu-id="80268-195">Öffnen Sie auf dem Entwicklungs-PC in Unity das Fenster **Datei > Fenster Build-Einstellungen** .</span><span class="sxs-lookup"><span data-stu-id="80268-195">On your development PC, in Unity, open **File > Build Settings** window.</span></span>
2. <span data-ttu-id="80268-196">Ändern Sie **Platform** in **universelle Windows-Plattform** und klicken Sie auf **Plattform wechseln** .</span><span class="sxs-lookup"><span data-stu-id="80268-196">Change **Platform** to **Universal Windows Platform** and click **Switch Platform**</span></span>

### <a name="for-hololens-use-unity-remoting"></a><span data-ttu-id="80268-197">Verwenden Sie für hololens Unity-Remoting</span><span class="sxs-lookup"><span data-stu-id="80268-197">For HoloLens use Unity Remoting</span></span>

1. <span data-ttu-id="80268-198">Installieren und führen Sie auf Ihren hololens den [Holographic Remoting Player](../../platform-capabilities-and-apis/holographic-remoting-player.md)aus, der im Windows Store verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="80268-198">On your HoloLens, install and run the [Holographic Remoting Player](../../platform-capabilities-and-apis/holographic-remoting-player.md), available from the Windows Store.</span></span> <span data-ttu-id="80268-199">Starten Sie die Anwendung auf dem Gerät, und Sie wechselt in den Wartezustand und zeigt die IP-Adresse des Geräts an.</span><span class="sxs-lookup"><span data-stu-id="80268-199">Launch the application on the device, and it will enter a waiting state and show the IP address of the device.</span></span> <span data-ttu-id="80268-200">Notieren Sie sich die IP-Adresse.</span><span class="sxs-lookup"><span data-stu-id="80268-200">Note down the IP.</span></span>
2. <span data-ttu-id="80268-201">Öffnen Sie **Fenster > XR > Holographic Emulation**.</span><span class="sxs-lookup"><span data-stu-id="80268-201">Open **Window > XR > Holographic Emulation**.</span></span>
3. <span data-ttu-id="80268-202">Ändern Sie den **Emulations Modus** von **None** in **Remote zu Gerät**.</span><span class="sxs-lookup"><span data-stu-id="80268-202">Change **Emulation Mode** from **None** to **Remote to Device**.</span></span>
4. <span data-ttu-id="80268-203">Geben Sie auf dem **Remote Computer** die IP-Adresse der zuvor notierten hololens ein.</span><span class="sxs-lookup"><span data-stu-id="80268-203">In **Remote Machine**, enter the IP address of your HoloLens noted earlier.</span></span>
5. <span data-ttu-id="80268-204">Klicken Sie auf **Verbinden**.</span><span class="sxs-lookup"><span data-stu-id="80268-204">Click **Connect**.</span></span>
6. <span data-ttu-id="80268-205">Stellen Sie sicher, dass der **Verbindungs Status** in grünes **verbunden** wechselt.</span><span class="sxs-lookup"><span data-stu-id="80268-205">Ensure the **Connection Status** changes to green **Connected**.</span></span>
7. <span data-ttu-id="80268-206">Jetzt können **Sie im Unity-Editor auf "** wiedergeben" klicken.</span><span class="sxs-lookup"><span data-stu-id="80268-206">Now you can now click **Play** in the Unity editor.</span></span>

<span data-ttu-id="80268-207">Nun können Sie den Cube im Gerät und im Editor sehen.</span><span class="sxs-lookup"><span data-stu-id="80268-207">You will now be able to see the cube in device and in the editor.</span></span> <span data-ttu-id="80268-208">Sie können Objekte anhalten, überprüfen und Debuggen, wie Sie eine APP im Editor ausführen, da dies im Wesentlichen geschieht, aber mit Video-, Audio-und Geräte Eingaben, die zwischen dem Host Computer und dem Gerät über das Netzwerk übertragen werden.</span><span class="sxs-lookup"><span data-stu-id="80268-208">You can pause, inspect objects, and debug just like you are running an app in the editor, because that's essentially what's happening, but with video, audio, and device input transmitted back and forth across the network between the host machine and the device.</span></span>

### <a name="for-other-mixed-reality-supported-headsets"></a><span data-ttu-id="80268-209">Für andere von Mixed Reality unterstützte Headsets</span><span class="sxs-lookup"><span data-stu-id="80268-209">For other mixed reality supported headsets</span></span>

1. <span data-ttu-id="80268-210">Verbinden Sie das Headset mit dem Entwicklungs-PC, indem Sie das USB-Kabel und das HDMI-oder Anzeige Anschlusskabel verwenden.</span><span class="sxs-lookup"><span data-stu-id="80268-210">Connect the headset to your development PC using the USB cable and the HDMI or display port cable.</span></span>
2. <span data-ttu-id="80268-211">Starten Sie das **Mixed Reality-Portal** , und stellen Sie sicher, dass Sie die erste Ausführung abgeschlossen haben.</span><span class="sxs-lookup"><span data-stu-id="80268-211">Launch the **Mixed Reality Portal** and ensure you have completed the first run experience.</span></span>
3. <span data-ttu-id="80268-212">Aus Unity können Sie nun auf die Wiedergabe Schaltfläche klicken.</span><span class="sxs-lookup"><span data-stu-id="80268-212">From Unity, you can now press the Play button.</span></span>

<span data-ttu-id="80268-213">Nun können Sie das Cube-Rendering in Ihrem Mixed Reality-Headset und im Editor sehen.</span><span class="sxs-lookup"><span data-stu-id="80268-213">You will now be able to see the cube rendering in your mixed reality headset and in the editor.</span></span>

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a><span data-ttu-id="80268-214">Kapitel 6: Erstellen und Bereitstellen für ein Gerät aus Visual Studio</span><span class="sxs-lookup"><span data-stu-id="80268-214">Chapter 6 - Build and deploy to device from Visual Studio</span></span>

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

<span data-ttu-id="80268-215">Nun können wir das Projekt in Visual Studio kompilieren und auf dem Zielgerät bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="80268-215">We are now ready to compile our project to Visual Studio and deploy to our target device.</span></span>

### <a name="export-to-the-visual-studio-solution"></a><span data-ttu-id="80268-216">Exportieren in die Visual Studio-Projekt Mappe</span><span class="sxs-lookup"><span data-stu-id="80268-216">Export to the Visual Studio solution</span></span>

1. <span data-ttu-id="80268-217">Öffnen Sie die **Datei >** Fenster mit den Buildeinstellungen.</span><span class="sxs-lookup"><span data-stu-id="80268-217">Open **File > Build Settings** window.</span></span>
1. <span data-ttu-id="80268-218">Klicken Sie auf **offene Szenen hinzufügen** , um die Szene hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="80268-218">Click **Add Open Scenes** to add the scene.</span></span>
1. <span data-ttu-id="80268-219">Wechseln Sie zu **universelle Windows-Plattform** **Plattform** , und klicken Sie auf **Plattform wechseln**.</span><span class="sxs-lookup"><span data-stu-id="80268-219">Change **Platform** to **Universal Windows Platform** and click **Switch Platform**.</span></span>
1. <span data-ttu-id="80268-220">Stellen Sie sicher, dass in **universelle Windows-Plattform** Einstellungen das **SDK** **Universal 10** ist.</span><span class="sxs-lookup"><span data-stu-id="80268-220">In **Universal Windows Platform** settings, ensure **SDK** is **Universal 10**.</span></span>
1. <span data-ttu-id="80268-221">Überlassen Sie für Zielgerät **ein beliebiges Gerät für okkludierte** anzeigen, oder wechseln Sie zu **hololens**.</span><span class="sxs-lookup"><span data-stu-id="80268-221">For Target device, leave to **Any Device** for occluded displays or switch to **HoloLens**.</span></span>
1. <span data-ttu-id="80268-222">Der **UWP-Buildtyp** muss **D3D** lauten.</span><span class="sxs-lookup"><span data-stu-id="80268-222">**UWP Build Type** should be **D3D**.</span></span>
1. <span data-ttu-id="80268-223">Das **UWP SDK** ist möglicherweise auf dem **neuesten installiert**.</span><span class="sxs-lookup"><span data-stu-id="80268-223">**UWP SDK** could be left at **Latest installed**.</span></span>
1. <span data-ttu-id="80268-224">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="80268-224">Click **Build**.</span></span>
1. <span data-ttu-id="80268-225">Klicken Sie im Datei-Explorer auf **neuer Ordner** , und benennen Sie den Ordner **"App"**.</span><span class="sxs-lookup"><span data-stu-id="80268-225">In the file explorer, click **New Folder** and name the folder **"App"**.</span></span>
1. <span data-ttu-id="80268-226">Wenn der **App** -Ordner ausgewählt ist, klicken Sie auf die Schaltfläche **Ordner auswählen** .</span><span class="sxs-lookup"><span data-stu-id="80268-226">With the **App** folder selected, click the **Select Folder** button.</span></span>
1. <span data-ttu-id="80268-227">Wenn Unity erstellt wurde, wird ein Fenster des Windows-Datei-Explorers angezeigt.</span><span class="sxs-lookup"><span data-stu-id="80268-227">When Unity is done building, a Windows File Explorer window will appear.</span></span>
1. <span data-ttu-id="80268-228">Öffnen Sie den **App** -Ordner im Datei-Explorer.</span><span class="sxs-lookup"><span data-stu-id="80268-228">Open the **App** folder in file explorer.</span></span>
1. <span data-ttu-id="80268-229">Öffnen Sie die generierte Visual Studio-Projekt Mappe (in diesem Beispiel mixedrealityintroduction. sln).</span><span class="sxs-lookup"><span data-stu-id="80268-229">Open the generated Visual Studio solution (MixedRealityIntroduction.sln in this example)</span></span>

### <a name="compile-the-visual-studio-solution"></a><span data-ttu-id="80268-230">Kompilieren der Visual Studio-Projekt Mappe</span><span class="sxs-lookup"><span data-stu-id="80268-230">Compile the Visual Studio solution</span></span>

<span data-ttu-id="80268-231">Schließlich kompilieren wir die exportierte Visual Studio-Projekt Mappe, stellen Sie bereit und testen Sie auf dem Gerät.</span><span class="sxs-lookup"><span data-stu-id="80268-231">Finally, we will compile the exported Visual Studio solution, deploy it, and try it out on the device.</span></span>

1. <span data-ttu-id="80268-232">Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von **Debug** in **Release** und von **Arm** in **x86**.</span><span class="sxs-lookup"><span data-stu-id="80268-232">Using the top toolbar in Visual Studio, change the target from **Debug** to **Release** and from **ARM** to **X86**.</span></span>

<span data-ttu-id="80268-233">Die Anweisungen unterscheiden sich für die Bereitstellung auf einem Gerät im Vergleich zum Emulator.</span><span class="sxs-lookup"><span data-stu-id="80268-233">The instructions differ for deploying to a device versus the emulator.</span></span> <span data-ttu-id="80268-234">Befolgen Sie die Anweisungen, die dem Setup entsprechen.</span><span class="sxs-lookup"><span data-stu-id="80268-234">Follow the instructions that match your setup.</span></span>

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a><span data-ttu-id="80268-235">Bereitstellung für Mixed Reality-Gerät über Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="80268-235">Deploy to mixed reality device over Wi-Fi</span></span>

1. <span data-ttu-id="80268-236">Klicken Sie auf den Pfeil neben der Schaltfläche **lokaler Computer** , und ändern Sie das Bereitstellungs Ziel in **Remote Computer**.</span><span class="sxs-lookup"><span data-stu-id="80268-236">Click on the arrow next to the **Local Machine** button, and change the deployment target to **Remote Machine**.</span></span>
2. <span data-ttu-id="80268-237">Geben Sie die IP-Adresse Ihres gemischten Reality-Geräts ein, und ändern Sie den **Authentifizierungsmodus** für hololens und **Windows** für andere Geräte in Universal (unverschlüsseltes Protokoll).</span><span class="sxs-lookup"><span data-stu-id="80268-237">Enter the IP address of your mixed reality device and change **Authentication Mode** to Universal (Unencrypted Protocol) for HoloLens and **Windows** for other devices.</span></span>
3. <span data-ttu-id="80268-238">Klicken Sie auf **Debuggen > ohne Debugging starten**.</span><span class="sxs-lookup"><span data-stu-id="80268-238">Click **Debug > Start without debugging**.</span></span>

<span data-ttu-id="80268-239">Bei **hololens** müssen Sie, wenn dies die erste Bereitstellung auf Ihrem Gerät ist, [mit Visual Studio](../../platform-capabilities-and-apis/using-visual-studio.md)koppeln.</span><span class="sxs-lookup"><span data-stu-id="80268-239">**For HoloLens**, If this is the first time deploying to your device, you will need to pair [using Visual Studio](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

### <a name="deploy-to-mixed-reality-device-over-usb"></a><span data-ttu-id="80268-240">Auf gemischtes Reality-Gerät über USB bereitstellen</span><span class="sxs-lookup"><span data-stu-id="80268-240">Deploy to mixed reality device over USB</span></span>

<span data-ttu-id="80268-241">Stellen Sie sicher, dass das Gerät über das USB-Kabel angeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="80268-241">Ensure you device is plugged in via the USB cable.</span></span>

1. <span data-ttu-id="80268-242">Klicken Sie **für hololens** auf den Pfeil neben der Schaltfläche **lokaler Computer** , und ändern Sie das Bereitstellungs Ziel auf **Gerät**.</span><span class="sxs-lookup"><span data-stu-id="80268-242">**For HoloLens**, click on the arrow next to the **Local Machine** button, and change the deployment target to **Device**.</span></span>
2. <span data-ttu-id="80268-243">Behalten Sie **für die Zielgeräte, die an Ihren PC angeschlossen** sind, die Einstellung lokaler Computer bei.</span><span class="sxs-lookup"><span data-stu-id="80268-243">**For targeting occluded devices attached to your PC**, keep the setting to Local Machine.</span></span> <span data-ttu-id="80268-244">Stellen Sie sicher, dass das **gemischte Reality-Portal** ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="80268-244">Ensure you have the **Mixed Reality Portal** running.</span></span>
3. <span data-ttu-id="80268-245">Klicken Sie auf **Debuggen > ohne Debugging starten**.</span><span class="sxs-lookup"><span data-stu-id="80268-245">Click **Debug > Start without debugging**.</span></span>

### <a name="deploy-to-emulator"></a><span data-ttu-id="80268-246">In Emulator bereitstellen</span><span class="sxs-lookup"><span data-stu-id="80268-246">Deploy to Emulator</span></span>

1. <span data-ttu-id="80268-247">Klicken Sie auf den Pfeil neben der Schaltfläche **Gerät** , und wählen Sie in der Dropdown-Taste **hololens Emulator** aus.</span><span class="sxs-lookup"><span data-stu-id="80268-247">Click on the arrow next to the **Device** button, and from drop down select **HoloLens Emulator**.</span></span>
2. <span data-ttu-id="80268-248">Klicken Sie auf **Debuggen > ohne Debugging starten**.</span><span class="sxs-lookup"><span data-stu-id="80268-248">Click **Debug > Start without debugging**.</span></span>

### <a name="try-out-your-app"></a><span data-ttu-id="80268-249">Testen Sie Ihre APP</span><span class="sxs-lookup"><span data-stu-id="80268-249">Try out your app</span></span>

<span data-ttu-id="80268-250">Nachdem Sie Ihre APP bereitgestellt haben, versuchen Sie, alle den Cube zu verschieben, und beobachten Sie, dass Sie in der Welt vor Ihnen bleibt.</span><span class="sxs-lookup"><span data-stu-id="80268-250">Now that your app is deployed, try moving all around the cube and observe that it stays in the world in front of you.</span></span>

## <a name="see-also"></a><span data-ttu-id="80268-251">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="80268-251">See also</span></span>

* [<span data-ttu-id="80268-252">Unity-Entwicklung – Übersicht</span><span class="sxs-lookup"><span data-stu-id="80268-252">Unity development overview</span></span>](../unity-development-overview.md)
* [<span data-ttu-id="80268-253">Bewährte Methoden für das Arbeiten mit Unity und Visual Studio</span><span class="sxs-lookup"><span data-stu-id="80268-253">Best practices for working with Unity and Visual Studio</span></span>](../best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="80268-254">MR-Grundlagen 101</span><span class="sxs-lookup"><span data-stu-id="80268-254">MR Basics 101</span></span>](holograms-101.md)
* [<span data-ttu-id="80268-255">MR-Grundlagen 101E</span><span class="sxs-lookup"><span data-stu-id="80268-255">MR Basics 101E</span></span>](holograms-101e.md)