---
title: 'MR Input 210: Anvisieren'
description: Befolgen Sie diese exemplarische Vorgehensweise, indem Sie Unity, Visual Studio und hololens verwenden, um die Details von Blick Konzepten zu erlernen.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academy, Tutorial, Blick, hololens, Mixed Reality Academy, Unity, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Windows 10
ms.openlocfilehash: 7e8d72bc4d37d76f8f9ec40956cb85591e237ac8
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583860"
---
# <a name="mr-input-210-gaze"></a><span data-ttu-id="eb2ee-104">MR-Eingabe 210: Anvisieren</span><span class="sxs-lookup"><span data-stu-id="eb2ee-104">MR Input 210: Gaze</span></span>

>[!NOTE]
><span data-ttu-id="eb2ee-105">Die Tutorials der Mixed Reality Academy wurden im Hinblick auf HoloLens (1. Gen.) und immersive Mixed Reality-Headsets entworfen.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="eb2ee-106">Daher halten wir es für wichtig, diese Tutorials für Entwickler verfügbar zu halten, die noch nach Anleitung beim Entwickeln für diese Geräte suchen.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="eb2ee-107">Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für HoloLens 2 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="eb2ee-108">Sie werden gewartet, um weiterhin auf den unterstützten Geräten zu funktionieren.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="eb2ee-109">[Es wurde eine neue Reihe von Tutorials](./mr-learning-base-01.md) für HoloLens 2 veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-109">[A new series of tutorials](./mr-learning-base-01.md) has been posted for HoloLens 2.</span></span>

<span data-ttu-id="eb2ee-110">Der [Blick](../../../design/gaze-and-commit.md) ist die erste Form der Eingabe und zeigt die Absicht und das Bewusstsein des Benutzers an.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-110">[Gaze](../../../design/gaze-and-commit.md) is the first form of input and reveals the user's intent and awareness.</span></span> <span data-ttu-id="eb2ee-111">Die Eingabe 210 (auch Projekt-Explorer genannt) ist ein tiefer Einblick in die im Blick zusammenhängenden Konzepte für Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-111">MR Input 210 (aka Project Explorer) is a deep dive into gaze-related concepts for Windows Mixed Reality.</span></span> <span data-ttu-id="eb2ee-112">Wir werden dem Cursor und holograms kontextbezogene Informationen hinzufügen und dabei die Vorteile der APP im Überblick über den Benutzer in vollem Umfang nutzen.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-112">We will be adding contextual awareness to our cursor and holograms, taking full advantage of what your app knows about the user's gaze.</span></span>

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

<span data-ttu-id="eb2ee-113">Wir haben hier einen freundlichen Astronauten, der Sie beim Erlernen von Blick Konzepten unterstützt.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-113">We have a friendly astronaut here to help you learn gaze concepts.</span></span> <span data-ttu-id="eb2ee-114">In den [Grundlagen 101](../../../develop/unity/tutorials/holograms-101.md)hatten wir einen einfachen Cursor, der genau auf Ihren Blick folgt.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-114">In [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md), we had a simple cursor that just followed your gaze.</span></span> <span data-ttu-id="eb2ee-115">Heute verschieben wir einen Schritt über den einfachen Cursor hinaus:</span><span class="sxs-lookup"><span data-stu-id="eb2ee-115">Today we're moving a step beyond the simple cursor:</span></span>

* <span data-ttu-id="eb2ee-116">Wir machen den Cursor und den holograms im Blick: Beide Änderungen ändern sich je nachdem, wo der Benutzer sucht oder wo der Benutzer *nicht* sucht.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-116">We're making the cursor and our holograms gaze-aware: both will change based on where the user is looking - or where the user is *not* looking.</span></span> <span data-ttu-id="eb2ee-117">Dies macht Sie Kontext abhängig.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-117">This makes them context-aware.</span></span>
* <span data-ttu-id="eb2ee-118">Wir werden dem Cursor und holograms Feedback hinzufügen, um dem Benutzer mehr Kontext für das Ziel zu geben.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-118">We will add feedback to our cursor and holograms to give the user more context on what is being targeted.</span></span> <span data-ttu-id="eb2ee-119">Dieses Feedback kann ein Audiomaterial und ein visuelles Element sein.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-119">This feedback can be audio and visual.</span></span>
* <span data-ttu-id="eb2ee-120">Wir zeigen Ihnen gezielte Verfahren, mit denen Benutzer kleinere Ziele erreichen können.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-120">We'll show you targeting techniques to help users hit smaller targets.</span></span>
* <span data-ttu-id="eb2ee-121">Wir zeigen Ihnen, wie Sie die Aufmerksamkeit des Benutzers auf die Hologramme mit einem direktionalen Indikator zeichnen.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-121">We'll show you how to draw the user's attention to your holograms with a directional indicator.</span></span>
* <span data-ttu-id="eb2ee-122">Wir informieren Sie über Techniken, mit denen Sie Ihre Hologramme mit dem Benutzer übernehmen, wenn Sie sich in ihrer Welt bewegen.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-122">We'll teach you techniques to take your holograms with the user as she moves around in your world.</span></span>

>[!IMPORTANT]
><span data-ttu-id="eb2ee-123">Die in den folgenden Kapiteln eingebetteten Videos wurden mit einer älteren Version von Unity und dem Mixed Reality Toolkit aufgezeichnet.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-123">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="eb2ee-124">Die Schritt-für-Schritt-Anweisungen sind genau und aktuell, aber es werden möglicherweise Skripts und Visualisierungen in den entsprechenden Videos angezeigt, die veraltet sind.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-124">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="eb2ee-125">Die Videos bleiben in der einwelt enthalten und werden weiterhin angewendet.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-125">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="eb2ee-126">Geräteunterstützung</span><span class="sxs-lookup"><span data-stu-id="eb2ee-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="eb2ee-127">Kurs</span><span class="sxs-lookup"><span data-stu-id="eb2ee-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="eb2ee-128"><a href="/hololens/hololens1-hardware">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="eb2ee-128"><a href="/hololens/hololens1-hardware">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="eb2ee-129"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive Headsets</a></span><span class="sxs-lookup"><span data-stu-id="eb2ee-129"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="eb2ee-130">MR-Eingabe 210: Anvisieren</span><span class="sxs-lookup"><span data-stu-id="eb2ee-130">MR Input 210: Gaze</span></span></td><td style="text-align: center;"> <span data-ttu-id="eb2ee-131">✔️</span><span class="sxs-lookup"><span data-stu-id="eb2ee-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="eb2ee-132">✔️</span><span class="sxs-lookup"><span data-stu-id="eb2ee-132">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="eb2ee-133">Vorbereitung</span><span class="sxs-lookup"><span data-stu-id="eb2ee-133">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="eb2ee-134">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="eb2ee-134">Prerequisites</span></span>

* <span data-ttu-id="eb2ee-135">Ein Windows 10-PC, der mit den richtigen [installierten Tools](../../../develop/install-the-tools.md)konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-135">A Windows 10 PC configured with the correct [tools installed](../../../develop/install-the-tools.md).</span></span>
* <span data-ttu-id="eb2ee-136">Einige grundlegende c#-Programmierfähigkeiten.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-136">Some basic C# programming ability.</span></span>
* <span data-ttu-id="eb2ee-137">Sie sollten die [Grundlagen von 101](../../../develop/unity/tutorials/holograms-101.md)abgeschlossen haben.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-137">You should have completed [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md).</span></span>
* <span data-ttu-id="eb2ee-138">Ein hololens-Gerät, das [für die Entwicklung konfiguriert](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)ist.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-138">A HoloLens device [configured for development](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="eb2ee-139">Projektdateien</span><span class="sxs-lookup"><span data-stu-id="eb2ee-139">Project files</span></span>

* <span data-ttu-id="eb2ee-140">Herunterladen der [Dateien](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) , die für das Projekt erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-140">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) required by the project.</span></span> <span data-ttu-id="eb2ee-141">Erfordert Unity 2017,2 oder höher.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-141">Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="eb2ee-142">Deinstallieren Sie die Dateien auf Ihrem Desktop oder an einem anderen leicht zugänglichen Speicherort.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-142">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="eb2ee-143">Wenn Sie den Quellcode vor dem herunterladen durchsuchen möchten, ist er [auf GitHub verfügbar](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).</span><span class="sxs-lookup"><span data-stu-id="eb2ee-143">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="eb2ee-144">Errata und Notizen</span><span class="sxs-lookup"><span data-stu-id="eb2ee-144">Errata and Notes</span></span>

* <span data-ttu-id="eb2ee-145">In Visual Studio muss "nur eigenen Code" unter Extras->Optionen->Debuggen deaktiviert (deaktiviert) werden, um Breakpoints im Code zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-145">In Visual Studio, "Just My Code" needs to be disabled (unchecked) under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="eb2ee-146">Kapitel 1: Einrichtung von Unity</span><span class="sxs-lookup"><span data-stu-id="eb2ee-146">Chapter 1 - Unity Setup</span></span>

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a><span data-ttu-id="eb2ee-147">Ziele</span><span class="sxs-lookup"><span data-stu-id="eb2ee-147">Objectives</span></span>

* <span data-ttu-id="eb2ee-148">Optimieren von Unity für die HoloLens-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="eb2ee-148">Optimize Unity for HoloLens development.</span></span>
* <span data-ttu-id="eb2ee-149">Importieren von Assets und Einrichten der Szene</span><span class="sxs-lookup"><span data-stu-id="eb2ee-149">Import assets and setup the scene.</span></span>
* <span data-ttu-id="eb2ee-150">Anzeigen des Astronauten in den hololens.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-150">View the astronaut in the HoloLens.</span></span>

### <a name="instructions"></a><span data-ttu-id="eb2ee-151">Instructions</span><span class="sxs-lookup"><span data-stu-id="eb2ee-151">Instructions</span></span>

1. <span data-ttu-id="eb2ee-152">Starten Sie Unity.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-152">Start Unity.</span></span>
2. <span data-ttu-id="eb2ee-153">Wählen Sie auf **Neues Projekt** aus.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-153">Select **New Project**.</span></span>
3. <span data-ttu-id="eb2ee-154">Nennen Sie das Projekt **Model Explorer**.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-154">Name the project **ModelExplorer**.</span></span>
4. <span data-ttu-id="eb2ee-155">Geben Sie Location als **den Ordner** Folder ein, den Sie zuvor nicht archiviert haben.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-155">Enter location as the **Gaze** folder you previously un-archived.</span></span>
5. <span data-ttu-id="eb2ee-156">Stellen Sie sicher, dass das Projekt auf **3D** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-156">Make sure the project is set to **3D**.</span></span>
6. <span data-ttu-id="eb2ee-157">Klicken Sie auf **Projekt erstellen**.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-157">Click **Create Project**.</span></span>

### <a name="unity-settings-for-hololens"></a><span data-ttu-id="eb2ee-158">Unity-Einstellungen für hololens</span><span class="sxs-lookup"><span data-stu-id="eb2ee-158">Unity settings for HoloLens</span></span>

<span data-ttu-id="eb2ee-159">Wir müssen Unity mitteilen, dass die zu exportierende App eine [immersive Ansicht](../../../design/app-views.md) anstelle einer 2D-Ansicht erstellen sollte.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-159">We need to let Unity know that the app we are trying to export should create an [immersive view](../../../design/app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="eb2ee-160">Dies geschieht, indem hololens als Virtual Reality-Gerät hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-160">We do that by adding HoloLens as a virtual reality device.</span></span>

1. <span data-ttu-id="eb2ee-161">Wechseln Sie zu **Edit > Project Settings > Player**.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-161">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="eb2ee-162">Wählen Sie im **Inspektor-Panel** für die Player Einstellungen das **Windows Store** -Symbol aus.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-162">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="eb2ee-163">Erweitern Sie die Gruppe **XR-Einstellungen**.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-163">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="eb2ee-164">Aktivieren Sie im Abschnitt **Rendering** das Kontrollkästchen **Virtuelle Realität unterstützt**, um eine neue Liste mit **Virtual Reality-SDKs** hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-164">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="eb2ee-165">Überprüfen Sie, ob in der Liste **Windows Mixed Reality** angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-165">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="eb2ee-166">Wenn nicht, klicken Sie **+** auf die Schaltfläche unten in der Liste, und wählen Sie **Windows Holographic** aus.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-166">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>

<span data-ttu-id="eb2ee-167">Als nächstes müssen wir unser Skript-Back-End auf .net festlegen.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-167">Next, we need to set our scripting backend to .NET.</span></span>

1. <span data-ttu-id="eb2ee-168">Wechseln Sie zu **Edit > Project Settings > Player** (möglicherweise noch im vorherigen Schritt).</span><span class="sxs-lookup"><span data-stu-id="eb2ee-168">Go to **Edit > Project Settings > Player** (you may still have this up from the previous step).</span></span>
2. <span data-ttu-id="eb2ee-169">Wählen Sie im **Inspektor-Panel** für die Player Einstellungen das **Windows Store** -Symbol aus.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-169">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="eb2ee-170">Stellen Sie sicher, dass im Konfigurations Abschnitt **andere Einstellungen** das Skript für die **Skript** Erstellung auf **.net** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-170">In the **Other Settings** Configuration section, make sure that **Scripting Backend** is set to **.NET**</span></span>

<span data-ttu-id="eb2ee-171">Zum Schluss aktualisieren wir unsere Qualitätseinstellungen, um eine schnelle Leistung in hololens zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-171">Finally, we'll update our quality settings to achieve a fast performance on HoloLens.</span></span>

1. <span data-ttu-id="eb2ee-172">Wechseln Sie zu **Edit > Project Settings > Quality**.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-172">Go to **Edit > Project Settings > Quality**.</span></span>
2. <span data-ttu-id="eb2ee-173">Klicken Sie in der **Standard** Zeile unter dem Windows Store-Symbol auf den Pfeil nach unten.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-173">Click on downward pointing arrow in the **Default** row under the Windows Store icon.</span></span>
3. <span data-ttu-id="eb2ee-174">Wählen Sie für **Windows Store-Apps** **sehr niedrig** aus.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-174">Select **Very Low** for **Windows Store Apps**.</span></span>

### <a name="import-project-assets"></a><span data-ttu-id="eb2ee-175">Projekt Objekte importieren</span><span class="sxs-lookup"><span data-stu-id="eb2ee-175">Import project assets</span></span>

1. <span data-ttu-id="eb2ee-176">Klicken Sie im **Projekt** Panel mit der rechten Maustaste auf den Ordner **Assets** .</span><span class="sxs-lookup"><span data-stu-id="eb2ee-176">Right click the **Assets** folder in the **Project** panel.</span></span>
2. <span data-ttu-id="eb2ee-177">Klicken Sie auf **Paket importieren > benutzerdefiniertes Paket**.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-177">Click on **Import Package > Custom Package**.</span></span>
3. <span data-ttu-id="eb2ee-178">Navigieren Sie zu den Projektdateien, die Sie heruntergeladen haben, und klicken Sie auf **modelexplorer. unitypackage**.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-178">Navigate to the project files you downloaded and click on **ModelExplorer.unitypackage**.</span></span>
4. <span data-ttu-id="eb2ee-179">Klicken Sie auf **Öffnen**.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-179">Click **Open**.</span></span>
5. <span data-ttu-id="eb2ee-180">Nachdem das Paket geladen wurde, klicken Sie auf die Schaltfläche **importieren** .</span><span class="sxs-lookup"><span data-stu-id="eb2ee-180">After the package loads, click on the **Import** button.</span></span>

### <a name="setup-the-scene"></a><span data-ttu-id="eb2ee-181">Einrichten der Szene</span><span class="sxs-lookup"><span data-stu-id="eb2ee-181">Setup the scene</span></span>

1. <span data-ttu-id="eb2ee-182">Löschen Sie die **Hauptkamera** in der-Hierarchie.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-182">In the Hierarchy, delete the **Main Camera**.</span></span>
2. <span data-ttu-id="eb2ee-183">Öffnen Sie im Ordner **holotoolkit** den **Eingabe** Ordner, und öffnen Sie dann den Ordner **Prefabs** .</span><span class="sxs-lookup"><span data-stu-id="eb2ee-183">In the **HoloToolkit** folder, open the **Input** folder, then open the **Prefabs** folder.</span></span>
3. <span data-ttu-id="eb2ee-184">Ziehen Sie die vorfab **mixedrealitycameraparent** aus dem Ordner **Prefabs** in die **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-184">Drag and drop the **MixedRealityCameraParent** prefab from the **Prefabs** folder into the **Hierarchy**.</span></span>
4. <span data-ttu-id="eb2ee-185">Klicken Sie mit der rechten Maustaste auf den **direktionalen Licht** in der Hierarchie, **und wählen**</span><span class="sxs-lookup"><span data-stu-id="eb2ee-185">Right-click the **Directional Light** in the Hierarchy and select **Delete**.</span></span>
5. <span data-ttu-id="eb2ee-186">Ziehen Sie im **holograms** -Ordner die folgenden Objekte per Drag & amp; Drop in den Stamm der **Hierarchie**:</span><span class="sxs-lookup"><span data-stu-id="eb2ee-186">In the **Holograms** folder, drag and drop the following assets into the root of the **Hierarchy**:</span></span>
    * <span data-ttu-id="eb2ee-187">**Astroman**</span><span class="sxs-lookup"><span data-stu-id="eb2ee-187">**AstroMan**</span></span>
    * <span data-ttu-id="eb2ee-188">**Lichter**</span><span class="sxs-lookup"><span data-stu-id="eb2ee-188">**Lights**</span></span>
    * <span data-ttu-id="eb2ee-189">**Spaceaudiosource**</span><span class="sxs-lookup"><span data-stu-id="eb2ee-189">**SpaceAudioSource**</span></span>
    * <span data-ttu-id="eb2ee-190">**Spacebackground**</span><span class="sxs-lookup"><span data-stu-id="eb2ee-190">**SpaceBackground**</span></span>
6. <span data-ttu-id="eb2ee-191">Starten Sie den **Wiedergabemodus** ▶, um den Astronaut anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-191">Start **Play Mode** ▶ to view the astronaut.</span></span>
7. <span data-ttu-id="eb2ee-192">Klicken Sie erneut auf **Wiedergabemodus** ▶, um zu **verhindern**.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-192">Click **Play Mode** ▶ again to **Stop**.</span></span>
8. <span data-ttu-id="eb2ee-193">Suchen Sie im Ordner **holograms** das **fitbox** -Asset, und ziehen Sie es in den Stamm der **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-193">In the **Holograms** folder, find the **Fitbox** asset and drag it to the root of the **Hierarchy**.</span></span>
9. <span data-ttu-id="eb2ee-194">Wählen Sie im Bereich **Hierarchie** die Option **fitbox** aus.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-194">Select the **Fitbox** in the **Hierarchy** panel.</span></span>
10. <span data-ttu-id="eb2ee-195">Ziehen Sie die **Astroman** -Auflistung aus der **Hierarchie** in die **Hologram** -Auflistungs Eigenschaft von "fitbox" im **Inspektor** -Panel.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-195">Drag the **AstroMan** collection from the **Hierarchy** to the **Hologram Collection** property of the Fitbox in the **Inspector** panel.</span></span>

### <a name="save-the-project"></a><span data-ttu-id="eb2ee-196">Speichern Sie das Projekt.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-196">Save the project</span></span>

1. <span data-ttu-id="eb2ee-197">Speichern Sie die neue Szene: **File > Szene speichern** unter.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-197">Save the new scene: **File > Save Scene As**.</span></span>
2. <span data-ttu-id="eb2ee-198">Klicken Sie auf **neuer Ordner** , und benennen Sie die Ordner **Szenen**.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-198">Click **New Folder** and name the folder **Scenes**.</span></span>
3. <span data-ttu-id="eb2ee-199">Benennen Sie die Datei "**Model Explorer**", und speichern Sie Sie im Ordner **Szenen** .</span><span class="sxs-lookup"><span data-stu-id="eb2ee-199">Name the file “**ModelExplorer**” and save it in the **Scenes** folder.</span></span>

### <a name="build-the-project"></a><span data-ttu-id="eb2ee-200">Erstellen des Projekts</span><span class="sxs-lookup"><span data-stu-id="eb2ee-200">Build the project</span></span>

1. <span data-ttu-id="eb2ee-201">Wählen Sie in Unity **Datei > Buildeinstellungen** aus.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-201">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="eb2ee-202">Klicken Sie auf **offene Szenen hinzufügen** , um die Szene hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-202">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="eb2ee-203">Wählen Sie in der Liste **Plattform** **universelle Windows-Plattform** aus, und klicken Sie auf **Plattform wechseln**.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-203">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="eb2ee-204">Wenn Sie speziell für hololens entwickeln, legen Sie **Zielgerät** auf **hololens** fest.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-204">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="eb2ee-205">Andernfalls sollten Sie es auf **jedem Gerät** belassen.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-205">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="eb2ee-206">Stellen Sie sicher, dass der **Buildtyp** auf **D3D** und das **SDK** auf **Latest installiert** festgelegt ist (was SDK 16299 oder höher sein sollte).</span><span class="sxs-lookup"><span data-stu-id="eb2ee-206">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="eb2ee-207">Klicken Sie auf **Erstellen**.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-207">Click **Build**.</span></span>
7. <span data-ttu-id="eb2ee-208">Erstellen Sie einen **neuen Ordner** mit dem Namen "App".</span><span class="sxs-lookup"><span data-stu-id="eb2ee-208">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="eb2ee-209">Klicken Sie einfach auf den **App** -Ordner.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-209">Single click the **App** folder.</span></span>
9. <span data-ttu-id="eb2ee-210">Drücken **Sie Ordner auswählen**.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-210">Press **Select Folder**.</span></span>

<span data-ttu-id="eb2ee-211">Wenn Unity abgeschlossen ist, wird ein Datei-Explorer-Fenster angezeigt.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-211">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="eb2ee-212">Öffnen Sie den **App** -Ordner.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-212">Open the **App** folder.</span></span>
2. <span data-ttu-id="eb2ee-213">Öffnen Sie die Visual Studio-Projekt Mappe **Model Explorer**.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-213">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="eb2ee-214">Bei der Bereitstellung in hololens:</span><span class="sxs-lookup"><span data-stu-id="eb2ee-214">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="eb2ee-215">Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von Debug in **Release** und von Arm in **x86**.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-215">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="eb2ee-216">Klicken Sie auf den Dropdown Pfeil neben der Schaltfläche lokaler Computer, und wählen Sie **Remote Computer** aus.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-216">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="eb2ee-217">Geben Sie **die IP-Adresse des hololens-Geräts** ein, und legen Sie den Authentifizierungsmodus auf **Universal (unverschlüsseltes Protokoll)**</span><span class="sxs-lookup"><span data-stu-id="eb2ee-217">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="eb2ee-218">Klicken Sie auf **Auswählen**.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-218">Click **Select**.</span></span> <span data-ttu-id="eb2ee-219">Wenn Sie die IP-Adresse Ihres Geräts nicht kennen, suchen Sie unter **Einstellungen > Netzwerk & Internet > Erweiterte Optionen**.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-219">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="eb2ee-220">Klicken Sie in der oberen Menüleiste auf **Debuggen-> starten ohne Debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-220">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="eb2ee-221">Wenn Sie die Bereitstellung auf Ihrem Gerät zum ersten Mal durchführt, müssen Sie [es mit Visual Studio](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)koppeln.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-221">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).</span></span>
5. <span data-ttu-id="eb2ee-222">Wenn die APP bereitgestellt wurde, schließen Sie das **fitbox** -Gerät mit einer **Auswahl Bewegung** ab.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-222">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="eb2ee-223">Bei der Bereitstellung auf einem immersiven Headset:</span><span class="sxs-lookup"><span data-stu-id="eb2ee-223">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="eb2ee-224">Ändern Sie das Ziel mithilfe der oberen Symbolleiste in Visual Studio von Debug in **Release** und von Arm in **x64**.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-224">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="eb2ee-225">Stellen Sie sicher, dass das Bereitstellungs Ziel auf **lokaler Computer** festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-225">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="eb2ee-226">Klicken Sie in der oberen Menüleiste auf **Debuggen-> starten ohne Debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-226">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="eb2ee-227">Wenn die APP bereitgestellt wurde, schließen Sie die Funktion **, indem Sie den-** Typ auf einen Bewegungs Controller ziehen.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-227">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

## <a name="chapter-2---cursor-and-target-feedback"></a><span data-ttu-id="eb2ee-228">Kapitel 2: Cursor-und Ziel Feedback</span><span class="sxs-lookup"><span data-stu-id="eb2ee-228">Chapter 2 - Cursor and target feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a><span data-ttu-id="eb2ee-229">Ziele</span><span class="sxs-lookup"><span data-stu-id="eb2ee-229">Objectives</span></span>

* <span data-ttu-id="eb2ee-230">Visueller Entwurf und Verhalten des Cursors.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-230">Cursor visual design and behavior.</span></span>
* <span data-ttu-id="eb2ee-231">Zeiger basiertes Cursor Feedback.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-231">Gaze-based cursor feedback.</span></span>
* <span data-ttu-id="eb2ee-232">Auf Blick basierendes – Hologramm-Feedback.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-232">Gaze-based hologram feedback.</span></span>

<span data-ttu-id="eb2ee-233">Wir werden unsere Arbeit auf einige Grundsätze von Cursor Entwürfen basieren, nämlich:</span><span class="sxs-lookup"><span data-stu-id="eb2ee-233">We're going to base our work on some cursor design principles, namely:</span></span>

* <span data-ttu-id="eb2ee-234">Der Cursor ist immer vorhanden.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-234">The cursor is always present.</span></span>
* <span data-ttu-id="eb2ee-235">Lassen Sie den Cursor nicht zu klein oder groß werden.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-235">Don't let the cursor get too small or big.</span></span>
* <span data-ttu-id="eb2ee-236">Vermeiden Sie das Blockieren von Inhalt.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-236">Avoid obstructing content.</span></span>

### <a name="instructions"></a><span data-ttu-id="eb2ee-237">Instructions</span><span class="sxs-lookup"><span data-stu-id="eb2ee-237">Instructions</span></span>

1. <span data-ttu-id="eb2ee-238">Suchen Sie im Ordner **holotoolkit\input\prefabs** nach dem **InputManager** -Objekt.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-238">In the **HoloToolkit\Input\Prefabs** folder, find the **InputManager** asset.</span></span>
2. <span data-ttu-id="eb2ee-239">Ziehen Sie den **InputManager** in die **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-239">Drag and drop the **InputManager** onto the **Hierarchy**.</span></span>
3. <span data-ttu-id="eb2ee-240">Suchen Sie im Ordner **holotoolkit\input\prefabs** nach dem **Cursor** Medienobjekt.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-240">In the **HoloToolkit\Input\Prefabs** folder, find the **Cursor** asset.</span></span>
4. <span data-ttu-id="eb2ee-241">Ziehen Sie den **Cursor** per Drag & Drop in die **Hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-241">Drag and drop the **Cursor** onto the **Hierarchy**.</span></span>
5. <span data-ttu-id="eb2ee-242">Wählen Sie das **InputManager** -Objekt in der **Hierarchie** aus.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-242">Select the **InputManager** object in the **Hierarchy**.</span></span>
6. <span data-ttu-id="eb2ee-243">Ziehen Sie das **Cursor** Objekt aus der **Hierarchie** in das **Cursor** Feld " **simplesinglepointerselector**" von InputManager am unteren Rand des **Inspektors**.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-243">Drag the **Cursor** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>

![Einfache Einrichtung von einzelzeigerselektor](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a><span data-ttu-id="eb2ee-245">Erstellen und Bereitstellen</span><span class="sxs-lookup"><span data-stu-id="eb2ee-245">Build and Deploy</span></span>

1. <span data-ttu-id="eb2ee-246">Erstellen Sie die APP aus dem **Datei > den Buildeinstellungen** neu.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-246">Rebuild the app from **File > Build Settings**.</span></span>
2. <span data-ttu-id="eb2ee-247">Öffnen Sie den **app-Ordner**.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-247">Open the **App folder**.</span></span>
3. <span data-ttu-id="eb2ee-248">Öffnen Sie die Visual Studio-Projekt Mappe **Model Explorer**.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-248">Open the **ModelExplorer Visual Studio Solution**.</span></span>
4. <span data-ttu-id="eb2ee-249">Klicken Sie auf **Debuggen > starten ohne Debugging** , oder drücken Sie **STRG + F5**.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-249">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
5. <span data-ttu-id="eb2ee-250">Beobachten Sie, wie der Cursor gezeichnet wird, und wie sich die Darstellung ändert, wenn Sie ein Hologram berührt.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-250">Observe how the cursor is drawn, and how it changes appearance if it is touching a hologram.</span></span>

### <a name="instructions"></a><span data-ttu-id="eb2ee-251">Instructions</span><span class="sxs-lookup"><span data-stu-id="eb2ee-251">Instructions</span></span>

1. <span data-ttu-id="eb2ee-252">Erweitern Sie im Bereich **Hierarchie** den Knoten **Astroman** -> **GEO_G** -> **Back_Center** .</span><span class="sxs-lookup"><span data-stu-id="eb2ee-252">In the **Hierarchy** panel, expand the **AstroMan**->**GEO_G**->**Back_Center** object.</span></span>
2. <span data-ttu-id="eb2ee-253">Doppelklicken Sie auf **Interactible.cs** , um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-253">Double click on **Interactible.cs** to open it in Visual Studio.</span></span>
3. <span data-ttu-id="eb2ee-254">Heben Sie die Auskommentierung der Zeilen in den Rückrufe **ifocverwendbare. onfocusenter ()** und **ifocverwendbare. onfocusexit ()** in **Interactible.cs** auf.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-254">Uncomment the lines in the **IFocusable.OnFocusEnter()** and **IFocusable.OnFocusExit()** callbacks in **Interactible.cs**.</span></span> <span data-ttu-id="eb2ee-255">Diese werden vom InputManager des Mixed Reality-Toolkits aufgerufen, wenn der Fokus (entweder durch den Blick oder durch den Controller) in den Konflikt des jeweiligen gameobject-Objekts wechselt und diesen verlässt.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-255">These are called by the Mixed Reality Toolkit's InputManager when focus (either by gaze or by controller pointing) enters and exits the specific GameObject's collider.</span></span>

```cs
/* TODO: DEVELOPER CODING EXERCISE 2.d */

void IFocusable.OnFocusEnter()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to highlight the material when gaze enters.
        defaultMaterials[i].EnableKeyword("_ENVIRONMENT_COLORING");
    }
}

void IFocusable.OnFocusExit()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to remove highlight on material when gaze exits.
        defaultMaterials[i].DisableKeyword("_ENVIRONMENT_COLORING");
    }
}
```

>[!NOTE]
><span data-ttu-id="eb2ee-256">Wir verwenden `EnableKeyword` und `DisableKeyword` höher.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-256">We use `EnableKeyword` and `DisableKeyword` above.</span></span> <span data-ttu-id="eb2ee-257">Um diese in ihrer eigenen App mit dem Standard-Shader des Toolkits zu nutzen, müssen Sie die [Unity-Richtlinien für den Zugriff auf Materialien per Skript](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html)befolgen.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-257">In order to make use of these in your own app with the Toolkit's Standard shader, you'll need to follow the [Unity guidelines for accessing materials via script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html).</span></span> <span data-ttu-id="eb2ee-258">In diesem Fall haben wir bereits die [drei Varianten von hervorgehobenem Material](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) in den Ressourcen Ordner eingefügt (suchen Sie nach den drei Materialien, deren Name hervorgehoben ist).</span><span class="sxs-lookup"><span data-stu-id="eb2ee-258">In this case, we've already included the [three variants of highlighted material](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) needed in the Resources folder (look for the three materials with highlight in the name).</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="eb2ee-259">Erstellen und Bereitstellen</span><span class="sxs-lookup"><span data-stu-id="eb2ee-259">Build and Deploy</span></span>

1. <span data-ttu-id="eb2ee-260">Erstellen Sie wie zuvor das Projekt, und stellen Sie es auf den hololens bereit.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-260">As before, build the project and deploy to the HoloLens.</span></span>
2. <span data-ttu-id="eb2ee-261">Beobachten Sie, was geschieht, wenn der Blick auf ein Objekt gerichtet ist, und wenn es nicht.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-261">Observe what happens when the gaze is aimed at an object and when it's not.</span></span>

## <a name="chapter-3---targeting-techniques"></a><span data-ttu-id="eb2ee-262">Kapitel 3: Ziel Technologien</span><span class="sxs-lookup"><span data-stu-id="eb2ee-262">Chapter 3 - Targeting Techniques</span></span>

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a><span data-ttu-id="eb2ee-263">Ziele</span><span class="sxs-lookup"><span data-stu-id="eb2ee-263">Objectives</span></span>

* <span data-ttu-id="eb2ee-264">Vereinfachen Sie das Ziel von holograms.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-264">Make it easier to target holograms.</span></span>
* <span data-ttu-id="eb2ee-265">Stabilisiert natürliche Head-Bewegungen.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-265">Stabilize natural head movements.</span></span>

### <a name="instructions"></a><span data-ttu-id="eb2ee-266">Instructions</span><span class="sxs-lookup"><span data-stu-id="eb2ee-266">Instructions</span></span>

1. <span data-ttu-id="eb2ee-267">Wählen Sie im Bereich **Hierarchie** das Objekt **InputManager** aus.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-267">In the **Hierarchy** panel, select the **InputManager** object.</span></span>
2. <span data-ttu-id="eb2ee-268">Suchen Sie im **Inspektor** -Panel nach dem Skript für den **Blick-Stabilisator** .</span><span class="sxs-lookup"><span data-stu-id="eb2ee-268">In the **Inspector** panel, find the **Gaze Stabilizer** script.</span></span> <span data-ttu-id="eb2ee-269">Klicken Sie auf die Datei, um Sie in Visual Studio zu öffnen, wenn Sie ein Bild sehen möchten.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-269">Click it to open in Visual Studio, if you want to take a look.</span></span>
    * <span data-ttu-id="eb2ee-270">Dieses Skript durchläuft Beispiele von raycast-Daten und trägt dazu bei, den Blick des Benutzers auf die Genauigkeit der Genauigkeit zu stabilisieren.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-270">This script iterates over samples of Raycast data and helps stabilize the user's gaze for precision targeting.</span></span>
3. <span data-ttu-id="eb2ee-271">Im **Inspektor** können Sie den Wert für **gespeicherte Stabilitäts Beispiele** bearbeiten.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-271">In the **Inspector**, you can edit the **Stored Stability Samples** value.</span></span> <span data-ttu-id="eb2ee-272">Dieser Wert stellt die Anzahl der Samplings dar, die der-Stabilisator durchläuft, um den stabilisierten Wert zu berechnen.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-272">This value represents the number of samples that the stabilizer iterates on to calculate the stabilized value.</span></span>

## <a name="chapter-4---directional-indicator"></a><span data-ttu-id="eb2ee-273">Kapitel 4: direktionaler Indikator</span><span class="sxs-lookup"><span data-stu-id="eb2ee-273">Chapter 4 - Directional indicator</span></span>

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a><span data-ttu-id="eb2ee-274">Ziele</span><span class="sxs-lookup"><span data-stu-id="eb2ee-274">Objectives</span></span>

* <span data-ttu-id="eb2ee-275">Fügen Sie einen direktionalen Indikator für den Cursor hinzu, um Hologramme zu finden.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-275">Add a directional indicator on the cursor to help find holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="eb2ee-276">Instructions</span><span class="sxs-lookup"><span data-stu-id="eb2ee-276">Instructions</span></span>

<span data-ttu-id="eb2ee-277">Wir verwenden die Datei **DirectionIndicator.cs** , um Folgendes zu tun:</span><span class="sxs-lookup"><span data-stu-id="eb2ee-277">We're going to use the **DirectionIndicator.cs** file which will:</span></span>

1. <span data-ttu-id="eb2ee-278">Zeigen Sie den direktionalen Indikator an, wenn der Benutzer nicht mit den holograms-Vorgängen.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-278">Show the directional indicator if the user is not gazing at the holograms.</span></span>
2. <span data-ttu-id="eb2ee-279">Blenden Sie den direktionalen Indikator aus, wenn der Benutzer bei den holograms einen Blick anzeigt.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-279">Hide the directional indicator if the user is gazing at the holograms.</span></span>
3. <span data-ttu-id="eb2ee-280">Aktualisieren Sie den direktionalen Indikator, sodass er auf die holograms zeigt.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-280">Update the directional indicator to point to the holograms.</span></span>

<span data-ttu-id="eb2ee-281">Fangen wir also an.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-281">Let's get started.</span></span>

1. <span data-ttu-id="eb2ee-282">Klicken Sie im **Hierarchie** Panel auf das **Astroman** -Objekt, und klicken Sie auf **den Pfeil** , um es zu erweitern.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-282">Click on the **AstroMan** object in the **Hierarchy** panel and **click the arrow** to expand it.</span></span>
2. <span data-ttu-id="eb2ee-283">Wählen Sie im Bereich **Hierarchie** das **directionalindicator** -Objekt unter **Astroman** aus.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-283">In the **Hierarchy** panel, select the **DirectionalIndicator** object under **AstroMan**.</span></span>
3. <span data-ttu-id="eb2ee-284">Klicken Sie im **Inspektor** -Panel auf die Schaltfläche **Komponente hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="eb2ee-284">In the **Inspector** panel, click the **Add Component** button.</span></span>
4. <span data-ttu-id="eb2ee-285">Geben Sie im Menü den Suchfeld- **Richtungsindikator** ein.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-285">In the menu, type in the search box **Direction Indicator**.</span></span> <span data-ttu-id="eb2ee-286">Wählen Sie das Suchergebnis aus.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-286">Select the search result.</span></span>
5. <span data-ttu-id="eb2ee-287">Ziehen Sie im Bereich **Hierarchie** das **Cursor** Objekt per Drag & Drop auf die **Cursor** -Eigenschaft des **Inspektors**.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-287">In the **Hierarchy** panel, drag and drop the **Cursor** object onto the **Cursor** property in the **Inspector**.</span></span>
6. <span data-ttu-id="eb2ee-288">Ziehen Sie im **Projekt** Panel im Ordner **holograms** das **directionalindicator** -Asset per Drag & Drop auf die **direktionale Indikator** Eigenschaft im **Inspektor**.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-288">In the **Project** panel, in the **Holograms** folder, drag and drop the **DirectionalIndicator** asset onto the **Directional Indicator** property in the **Inspector**.</span></span>
7. <span data-ttu-id="eb2ee-289">Erstellen und Bereitstellen der app.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-289">Build and deploy the app.</span></span>
8. <span data-ttu-id="eb2ee-290">Sehen Sie, wie das direktionale Indikator Objekt Ihnen hilft, den Astronaut zu finden.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-290">Watch how the directional indicator object helps you find the astronaut.</span></span>

## <a name="chapter-5---billboarding"></a><span data-ttu-id="eb2ee-291">Kapitel 5: Abrechnung</span><span class="sxs-lookup"><span data-stu-id="eb2ee-291">Chapter 5 - Billboarding</span></span>

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a><span data-ttu-id="eb2ee-292">Ziele</span><span class="sxs-lookup"><span data-stu-id="eb2ee-292">Objectives</span></span>

* <span data-ttu-id="eb2ee-293">Verwenden Sie das-Abrechnungs Board, um holograms immer für Sie zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-293">Use billboarding to have holograms always face towards you.</span></span>

<span data-ttu-id="eb2ee-294">Wir verwenden die Datei **Billboard.cs** , um ein gameobject-Objekt so zu speichern, dass es dem Benutzer jederzeit zusteht.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-294">We will be using the **Billboard.cs** file to keep a GameObject oriented such that it is facing the user at all times.</span></span>

1. <span data-ttu-id="eb2ee-295">Wählen Sie im Bereich **Hierarchie** das Objekt **Astroman** aus.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-295">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
2. <span data-ttu-id="eb2ee-296">Klicken Sie im **Inspektor** -Panel auf die Schaltfläche **Komponente hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="eb2ee-296">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="eb2ee-297">Geben Sie im Menü im Suchfeld den Suchbegriff **ein.**</span><span class="sxs-lookup"><span data-stu-id="eb2ee-297">In the menu, type in the search box **Billboard**.</span></span> <span data-ttu-id="eb2ee-298">Wählen Sie das Suchergebnis aus.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-298">Select the search result.</span></span>
4. <span data-ttu-id="eb2ee-299">Legen Sie im **Inspektor** die **pivotachse** auf **Y** fest.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-299">In the **Inspector** set the **Pivot Axis** to **Y**.</span></span>
5. <span data-ttu-id="eb2ee-300">Testen</span><span class="sxs-lookup"><span data-stu-id="eb2ee-300">Try it!</span></span> <span data-ttu-id="eb2ee-301">Erstellen und stellen Sie die APP wie zuvor bereit.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-301">Build and deploy the app as before.</span></span>
6. <span data-ttu-id="eb2ee-302">Sehen Sie sich an, wie das Billboard-Objekt Ihnen unabhängig von der Änderung des Standpunkts steht.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-302">See how the Billboard object faces you no matter how you change the viewpoint.</span></span>
7. <span data-ttu-id="eb2ee-303">Löschen Sie das Skript für den Moment aus dem **Astroman** .</span><span class="sxs-lookup"><span data-stu-id="eb2ee-303">Delete the script from the **AstroMan** for now.</span></span>

## <a name="chapter-6---tag-along"></a><span data-ttu-id="eb2ee-304">Kapitel 6: Tag-Along</span><span class="sxs-lookup"><span data-stu-id="eb2ee-304">Chapter 6 - Tag-Along</span></span>

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a><span data-ttu-id="eb2ee-305">Ziele</span><span class="sxs-lookup"><span data-stu-id="eb2ee-305">Objectives</span></span>

* <span data-ttu-id="eb2ee-306">Verwenden Sie Tag-Along, damit unsere Hologramme um den Raum herum stehen.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-306">Use Tag-Along to have our holograms follow us around the room.</span></span>

<span data-ttu-id="eb2ee-307">Wir arbeiten an diesem Problem, indem wir die folgenden Entwurfs Einschränkungen beachten:</span><span class="sxs-lookup"><span data-stu-id="eb2ee-307">As we work on this issue, we'll be guided by the following design constraints:</span></span>

* <span data-ttu-id="eb2ee-308">Der Inhalt sollte immer auf einen Blick entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-308">Content should always be a glance away.</span></span>
* <span data-ttu-id="eb2ee-309">Der Inhalt sollte nicht auf dem Wege stehen.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-309">Content should not be in the way.</span></span>
* <span data-ttu-id="eb2ee-310">Der Inhalt der Kopf Sperre ist unbequem.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-310">Head-locking content is uncomfortable.</span></span>

<span data-ttu-id="eb2ee-311">Die hier verwendete Lösung ist die Verwendung eines "tagbasierten" Ansatzes.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-311">The solution used here is to use a "tag-along" approach.</span></span>

<span data-ttu-id="eb2ee-312">Ein tagansichts Objekt verlässt die Ansicht des Benutzers niemals vollständig.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-312">A tag-along object never fully leaves the user's view.</span></span> <span data-ttu-id="eb2ee-313">Sie können sich ein Tag als ein Objekt vorstellen, das an den Kopf des Benutzers durch Gummibänder angehängt ist.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-313">You can think of the a tag-along as being an object attached to the user's head by rubber bands.</span></span> <span data-ttu-id="eb2ee-314">Wenn der Benutzer sich bewegt, bleibt der Inhalt in einem einfachen Blick, indem er an den Rand der Ansicht bewegt wird, ohne dass er vollständig verlässt.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-314">As the user moves, the content will stay within an easy glance by sliding towards the edge of the view without completely leaving.</span></span> <span data-ttu-id="eb2ee-315">Wenn der Benutzer in Richtung des tagbasierten Objekts zeigt, wird es vollständig in die Ansicht integriert.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-315">When the user gazes towards the tag-along object, it comes more fully into view.</span></span>

<span data-ttu-id="eb2ee-316">Wir verwenden die Datei **SimpleTagalong.cs** , um Folgendes zu tun:</span><span class="sxs-lookup"><span data-stu-id="eb2ee-316">We're going to use the **SimpleTagalong.cs** file which will:</span></span>

1. <span data-ttu-id="eb2ee-317">Bestimmen Sie, ob sich das Tag-Along Objekt innerhalb der Kamera Begrenzungen befindet.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-317">Determine if the Tag-Along object is within the camera bounds.</span></span>
2. <span data-ttu-id="eb2ee-318">Wenn dies nicht der Wert der Ansicht ist, positionieren Sie den Tag-Along auf teilweise innerhalb der Ansicht.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-318">If not within the view frustum, position the Tag-Along to partially within the view frustum.</span></span>
3. <span data-ttu-id="eb2ee-319">Positionieren Sie andernfalls die Tag-Along in einem Standardabstand vom Benutzer.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-319">Otherwise, position the Tag-Along to a default distance from the user.</span></span>

<span data-ttu-id="eb2ee-320">Zu diesem Zweck müssen wir zuerst das **Interactible.cs** -Skript ändern, um die **Tagalong-Aktion** aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-320">To do this, we first must change the **Interactible.cs** script to call the **TagalongAction**.</span></span>

1. <span data-ttu-id="eb2ee-321">Bearbeiten Sie **Interactible.cs** , indem Sie die Codierungs Übung 6. a abschließen (auskommentieren von Zeilen 84 bis 87).</span><span class="sxs-lookup"><span data-stu-id="eb2ee-321">Edit **Interactible.cs** by completing coding exercise 6.a (uncommenting lines 84 to 87).</span></span>

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

<span data-ttu-id="eb2ee-322">Das **InteractibleAction.cs** -Skript in Kombination mit **Interactible.cs** führt benutzerdefinierte Aktionen aus, wenn Sie auf holograms tippen.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-322">The **InteractibleAction.cs** script, paired with **Interactible.cs** performs custom actions when you tap on holograms.</span></span> <span data-ttu-id="eb2ee-323">In diesem Fall verwenden wir eine speziell für das Tag.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-323">In this case, we'll use one specifically for tag-along.</span></span>

* <span data-ttu-id="eb2ee-324">Klicken Sie im Ordner **Scripts** auf **TagalongAction.cs** Asset, um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-324">In the **Scripts** folder click on **TagalongAction.cs** asset to open in Visual Studio.</span></span>
* <span data-ttu-id="eb2ee-325">Führen Sie die Codierungs Übung aus, oder ändern Sie Sie in Folgendes:</span><span class="sxs-lookup"><span data-stu-id="eb2ee-325">Complete the coding exercise or change it to this:</span></span>
  * <span data-ttu-id="eb2ee-326">Geben Sie oben in der **Hierarchie** in der Suchleiste **ChestButton_Center** ein, und wählen Sie das Ergebnis aus.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-326">At the top of the **Hierarchy**, in the search bar type **ChestButton_Center** and select the result.</span></span>
  * <span data-ttu-id="eb2ee-327">Klicken Sie im **Inspektor** -Panel auf die Schaltfläche **Komponente hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="eb2ee-327">In the **Inspector** panel, click the **Add Component** button.</span></span>
  * <span data-ttu-id="eb2ee-328">Geben Sie im Menü in das Suchfeld **Tagalong Action** ein.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-328">In the menu, type in the search box **Tagalong Action**.</span></span> <span data-ttu-id="eb2ee-329">Wählen Sie das Suchergebnis aus.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-329">Select the search result.</span></span>
  * <span data-ttu-id="eb2ee-330">Suchen Sie im Ordner **holograms** das **Tagalong** Asset.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-330">In **Holograms** folder find the **Tagalong** asset.</span></span>
  * <span data-ttu-id="eb2ee-331">Wählen Sie das **ChestButton_Center** Objekt in der **Hierarchie** aus.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-331">Select the **ChestButton_Center** object in the **Hierarchy**.</span></span> <span data-ttu-id="eb2ee-332">Ziehen Sie das **Tagalong** -Objekt per Drag & amp; Drop aus dem **Projekt** Panel auf den **Inspektor** in die Eigenschaft **Objekt zu tagparallel** .</span><span class="sxs-lookup"><span data-stu-id="eb2ee-332">Drag and drop the **TagAlong** object from the **Project** panel onto the **Inspector** into the **Object To Tagalong** property.</span></span>
  * <span data-ttu-id="eb2ee-333">Ziehen Sie das **Tagalong-Aktions** Objekt aus dem **Inspektor** in das **interable-Aktions** Feld des **interfähigen** Skripts.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-333">Drag the **Tagalong Action** object from the **Inspector** into the **Interactible Action** field on the **Interactible** script.</span></span>
* <span data-ttu-id="eb2ee-334">Doppelklicken Sie auf das Skript **tagalongaction** , um es in Visual Studio zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-334">Double click the **TagalongAction** script to open it in Visual Studio.</span></span>

![Interacable-Einrichtung](images/holograms210-interactible.png)

<span data-ttu-id="eb2ee-336">Wir müssen Folgendes hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="eb2ee-336">We need to add the following:</span></span>

* <span data-ttu-id="eb2ee-337">Fügen Sie der Funktion "PerformAction" im tagalongaction-Skript (geerbt von interactibleaction) Funktionalität hinzu.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-337">Add functionality to the PerformAction function in the TagalongAction script (inherited from InteractibleAction).</span></span>
* <span data-ttu-id="eb2ee-338">Fügen Sie dem Objekt "gazed-on" einen fakboardingvorgang hinzu, und legen Sie die pivotachse auf XY fest</span><span class="sxs-lookup"><span data-stu-id="eb2ee-338">Add billboarding to the gazed-upon object, and set the pivot axis to XY.</span></span>
* <span data-ttu-id="eb2ee-339">Fügen Sie dann dem-Objekt einfache Tag-Along hinzu.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-339">Then add simple Tag-Along to the object.</span></span>

<span data-ttu-id="eb2ee-340">Hier ist unsere Lösung, von **TagalongAction.cs**:</span><span class="sxs-lookup"><span data-stu-id="eb2ee-340">Here's our solution, from **TagalongAction.cs**:</span></span>

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using HoloToolkit.Unity;
using UnityEngine;

public class TagalongAction : InteractibleAction
{
    [SerializeField]
    [Tooltip("Drag the Tagalong prefab asset you want to display.")]
    private GameObject objectToTagalong;

    private void Awake()
    {
        if (objectToTagalong != null)
        {
            objectToTagalong = Instantiate(objectToTagalong);
            objectToTagalong.SetActive(false);

            /* TODO: DEVELOPER CODING EXERCISE 6.b */

            // 6.b: AddComponent Billboard to objectToTagAlong,
            // so it's always facing the user as they move.
            Billboard billboard = objectToTagalong.AddComponent<Billboard>();

            // 6.b: AddComponent SimpleTagalong to objectToTagAlong,
            // so it's always following the user as they move.
            objectToTagalong.AddComponent<SimpleTagalong>();

            // 6.b: Set any public properties you wish to experiment with.
            billboard.PivotAxis = PivotAxis.XY; // Already the default, but provided in case you want to edit
        }
    }

    public override void PerformAction()
    {
        // Recommend having only one tagalong.
        if (objectToTagalong == null || objectToTagalong.activeSelf)
        {
            return;
        }

        objectToTagalong.SetActive(true);
    }
}
```

* <span data-ttu-id="eb2ee-341">Testen</span><span class="sxs-lookup"><span data-stu-id="eb2ee-341">Try it!</span></span> <span data-ttu-id="eb2ee-342">Erstellen und Bereitstellen der app.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-342">Build and deploy the app.</span></span>
* <span data-ttu-id="eb2ee-343">Sehen Sie sich an, wie der Inhalt der Mitte des Blick Punkts folgt, aber nicht kontinuierlich und ohne Blockierung.</span><span class="sxs-lookup"><span data-stu-id="eb2ee-343">Watch how the content follows the center of the gaze point, but not continuously and without blocking it.</span></span>