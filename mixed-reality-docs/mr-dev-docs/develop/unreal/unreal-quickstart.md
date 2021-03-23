---
title: Erstellen Ihrer ersten HoloLens Unreal-Anwendung
description: Erfahren Sie, wie Sie ein Unreal-Projekt korrekt mit Szenenobjekten und Eingabeinteraktionen für die Mixed Reality-Entwicklung für HoloLens konfigurieren.
author: hferrone
ms.author: safarooq
ms.date: 01/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, Unreal-Editor, UE4, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, Dokumentation, Leitfäden, Features, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Portieren, Upgrade
ms.openlocfilehash: 467987f69b50c0ec635c99899d6bcecab5a62af0
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2021
ms.locfileid: "99421429"
---
# <a name="creating-your-first-hololens-unreal-application"></a><span data-ttu-id="f0483-104">Erstellen Ihrer ersten HoloLens Unreal-Anwendung</span><span class="sxs-lookup"><span data-stu-id="f0483-104">Creating your first HoloLens Unreal application</span></span>

<span data-ttu-id="f0483-105">In dieser Anleitung erfahren Sie, wie Sie Ihre erste Mixed Reality-App auf der HoloLens in der Unreal Engine zum Laufen bringen.</span><span class="sxs-lookup"><span data-stu-id="f0483-105">This guide will walk you through getting your first Mixed Reality app running on the HoloLens in Unreal Engine.</span></span> <span data-ttu-id="f0483-106">In der Tradition von "Hallo Welt" erstellen Sie eine einfache App, die einen Würfel auf dem Bildschirm anzeigt.</span><span class="sxs-lookup"><span data-stu-id="f0483-106">In the tradition of "Hello World", you'll create a simple app that displays a cube on the screen.</span></span> <span data-ttu-id="f0483-107">Um die App nützlicher zu machen, erstellen Sie außerdem Ihre erste Geste zum Drehen des Würfels und zum Beenden der Anwendung.</span><span class="sxs-lookup"><span data-stu-id="f0483-107">To make it more useful, you'll also create your first gesture to rotate the cube and quit the application.</span></span> 

## <a name="objectives"></a><span data-ttu-id="f0483-108">Ziele</span><span class="sxs-lookup"><span data-stu-id="f0483-108">Objectives</span></span>

* <span data-ttu-id="f0483-109">Beginnen eines HoloLens-Projekts</span><span class="sxs-lookup"><span data-stu-id="f0483-109">Start a HoloLens Project</span></span>
* <span data-ttu-id="f0483-110">Aktivieren der richtigen Plug-Ins</span><span class="sxs-lookup"><span data-stu-id="f0483-110">Enable the correct plugins</span></span>
* <span data-ttu-id="f0483-111">Erstellen einer ARSessionConfig-Datenobjekts</span><span class="sxs-lookup"><span data-stu-id="f0483-111">Create an ARSessionConfig Data Asset</span></span>
* <span data-ttu-id="f0483-112">Einrichten der Gesteneingabe</span><span class="sxs-lookup"><span data-stu-id="f0483-112">Set up gesture inputs</span></span>
* <span data-ttu-id="f0483-113">Erstellen einer einfachen Ebene</span><span class="sxs-lookup"><span data-stu-id="f0483-113">Build a basic level</span></span>
* <span data-ttu-id="f0483-114">Implementieren einer Zusammendrückbewegung</span><span class="sxs-lookup"><span data-stu-id="f0483-114">Implement a pinch gesture</span></span>

## <a name="creating-a-new-project"></a><span data-ttu-id="f0483-115">Erstellen eines neuen Projekts</span><span class="sxs-lookup"><span data-stu-id="f0483-115">Creating a new project</span></span>

<span data-ttu-id="f0483-116">Als erstes benötigen Sie ein Projekt, mit dem Sie arbeiten können.</span><span class="sxs-lookup"><span data-stu-id="f0483-116">The first thing you need is a project to work with.</span></span> <span data-ttu-id="f0483-117">Wenn Sie Einsteiger in die Unreal-Entwicklung sind, müssen Sie aus dem Epic-Startprogramm [unterstützende Dateien herunterladen](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal).</span><span class="sxs-lookup"><span data-stu-id="f0483-117">If you're a first-time Unreal developer, you'll need to [download supporting files](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) from the Epic Launcher.</span></span>

1. <span data-ttu-id="f0483-118">Starten der Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="f0483-118">Launch Unreal Engine</span></span>
2. <span data-ttu-id="f0483-119">Wählen Sie unter **New Project Categories** (Kategorien für neues Projekt) die Option **Games** (Spiele) aus, und klicken Sie auf **Next** (Weiter):</span><span class="sxs-lookup"><span data-stu-id="f0483-119">In the **New Project Categories**, select **Games** and click **Next**:</span></span>

![Geöffnetes Fenster „Zuletzt geöffnete Projekte“ mit hervorgehobener Option „Games“ (Spiele).](images/unreal-quickstart-img-01.png)

3. <span data-ttu-id="f0483-121">Wählen Sie die **Leer** e Vorlage aus, und klicken Sie auf **Weiter**:</span><span class="sxs-lookup"><span data-stu-id="f0483-121">Select the **Blank** template and click **Next**:</span></span>

![Unreal-Projektbrowserfenster mit hervorgehobener Vorlage „Leer“.](images/unreal-quickstart-img-02.png)

4. <span data-ttu-id="f0483-123">Legen Sie in den **Projekteinstellungen**, **C++, Skalierbares 3D oder 2D, Mobilgerät/Tablet** und **Keine Startinhalte** fest, wählen Sie dann einen Speicherort aus, und klicken Sie auf **Projekt erstellen**.</span><span class="sxs-lookup"><span data-stu-id="f0483-123">In the **Project Settings**, set **C++, Scalable 3D or 2D, Mobile/Tablet**, and **No Starter Content**, then choose a save location and click **Create Project**</span></span>

> [!NOTE] 
> <span data-ttu-id="f0483-124">Verwenden Sie eher ein C++- anstelle eines Blaupausenprojekts, um das OpenXR-Plug-In später verwenden zu können.</span><span class="sxs-lookup"><span data-stu-id="f0483-124">You're using a C++ rather than a Blueprint project in order to be ready to use the OpenXR plugin later.</span></span> <span data-ttu-id="f0483-125">In dieser Schnellstartanleitung wird das OpenXR-Standard-Plug-In aus dem Lieferumfang der Unreal Engine verwendet.</span><span class="sxs-lookup"><span data-stu-id="f0483-125">This QuickStart uses the default OpenXR plugin that comes with Unreal Engine.</span></span> <span data-ttu-id="f0483-126">Es wird jedoch empfohlen, das offizielle OpenXR-Plug-In von Microsoft herunterzuladen und zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="f0483-126">However, downloading and using the official Microsoft OpenXR plugin is recommended.</span></span> <span data-ttu-id="f0483-127">Hierfür ist es erforderlich, dass das Projekt ein C++-Projekt ist.</span><span class="sxs-lookup"><span data-stu-id="f0483-127">That requires the project to be a C++ project.</span></span>

![Fenster „Projekteinstellungen“ mit hervorgehobenen Optionen „Projekt“, „Leistung“, „Zielplattform“ und „Startinhalte“.](images/unreal-quickstart-img-03.png)

<span data-ttu-id="f0483-129">Ihr neues Projekt sollte automatisch im Unreal-Editor geöffnet werden, womit Sie dann auch für den nächsten Abschnitt bereit sind.</span><span class="sxs-lookup"><span data-stu-id="f0483-129">Your new project should open up automatically in the Unreal editor, which means you're ready for the next section.</span></span>

## <a name="enabling-required-plugins"></a><span data-ttu-id="f0483-130">Aktivieren der erforderlichen Plug-Ins</span><span class="sxs-lookup"><span data-stu-id="f0483-130">Enabling required plugins</span></span>

<span data-ttu-id="f0483-131">Bevor Sie mit dem Hinzufügen von Objekten zur Szene beginnen können, müssen Sie zwei Plug-Ins aktivieren.</span><span class="sxs-lookup"><span data-stu-id="f0483-131">You'll need to enable two plugins before you can start adding objects to the scene.</span></span>

1. <span data-ttu-id="f0483-132">Öffnen Sie **Edit > Plugins** (Bearbeiten > Plug-Ins), und wählen Sie in der Liste der integrierten Optionen **Augmented Reality** aus.</span><span class="sxs-lookup"><span data-stu-id="f0483-132">Open **Edit > Plugins** and select **Augmented Reality** from the built-in options list.</span></span>
* <span data-ttu-id="f0483-133">Scrollen Sie nach unten bis zu **HoloLens**, und aktivieren Sie **Aktiviert**.</span><span class="sxs-lookup"><span data-stu-id="f0483-133">Scroll down to **HoloLens** and check **Enabled**</span></span>

![Fenster „Plug-Ins“ mit geöffnetem Abschnitt „Augmented Reality“ und hervorgehobener Option „HoloLens“.](images/unreal-quickstart-img-04.png)

2. <span data-ttu-id="f0483-135">Geben Sie in das Suchfeld in der oberen rechten Ecke **OpenXR** ein, und aktivieren Sie die Plug-Ins **OpenXR** und **OpenXRMsftHandInteraction**:</span><span class="sxs-lookup"><span data-stu-id="f0483-135">Type **OpenXR** in the search box at the top right and enable the **OpenXR** and **OpenXRMsftHandInteraction** plugins:</span></span>

![Fenster „Plug-Ins“ mit aktiviertem Plug-In „OpenXR“.](images/unreal-quickstart-img-05.jpg)

![Fenster „Plug-Ins“ mit aktiviertem Plug-In „OpenXRMsftHandInteraction“.](images/unreal-quickstart-img-06.jpg)

3. <span data-ttu-id="f0483-138">Starten Sie Ihren Editor neu.</span><span class="sxs-lookup"><span data-stu-id="f0483-138">Restart your editor</span></span>

> [!NOTE]
> <span data-ttu-id="f0483-139">In diesem Tutorial wird OpenXR verwendet, aber die zwei zuvor installierten Plug-Ins stellen derzeit nicht den vollständigen Funktionsumfang für die HoloLens-Entwicklung bereit.</span><span class="sxs-lookup"><span data-stu-id="f0483-139">This tutorial uses OpenXR, but the two plugins you've installed above don't currently provide the full feature set for HoloLens development.</span></span> <span data-ttu-id="f0483-140">Das HandInteraction-Plug-In reicht für die „Zusammendrücken“-Geste aus, die Sie später verwenden werden. Wenn Sie jedoch über die Grundlagen hinausgehen möchten, müssen Sie [das OpenXR-Plug-In herunterladen](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span><span class="sxs-lookup"><span data-stu-id="f0483-140">The HandInteraction plugin will suffice for the "Pinch" gesture you'll use later, but if you want to go beyond the basics you'll need to [download the OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span></span>

<span data-ttu-id="f0483-141">Wenn die Plug-Ins aktiviert sind, können Sie sich darauf konzentrieren, sie mit Inhalt zu füllen.</span><span class="sxs-lookup"><span data-stu-id="f0483-141">With the plugins enabled, you can focus on filling it with content.</span></span>

## <a name="creating-a-level"></a><span data-ttu-id="f0483-142">Erstellen eines Levels</span><span class="sxs-lookup"><span data-stu-id="f0483-142">Creating a level</span></span>

<span data-ttu-id="f0483-143">Ihre nächste Aufgabe besteht darin, ein Player-Setup mit einem Startpunkt und einem Würfel als Referenz und Maßstab zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="f0483-143">Your next task is to create a player setup with a starting point and a cube for reference and scale.</span></span>

1. <span data-ttu-id="f0483-144">Wählen Sie **File > New Level** (Datei > Neues Level) und dann **Empty Level** (Leeres Level) aus.</span><span class="sxs-lookup"><span data-stu-id="f0483-144">Select **File > New Level** and choose **Empty Level**.</span></span> <span data-ttu-id="f0483-145">Die Standardszene im Viewport sollte nun leer sein.</span><span class="sxs-lookup"><span data-stu-id="f0483-145">The default scene in the viewport should now be empty</span></span>
2. <span data-ttu-id="f0483-146">Wählen Sie auf der Registerkarte **Modes** (Modi) **Basic** (Einfach) aus, und ziehen Sie **PlayerStart** auf die Szene.</span><span class="sxs-lookup"><span data-stu-id="f0483-146">From the **Modes** tab, select **Basic** and drag **PlayerStart** into the scene</span></span>
* <span data-ttu-id="f0483-147">Legen Sie auf der Registerkarte **Details** die Option **Location** (Position) auf **X = 0, Y = 0** und **Z = 0** fest, um den Benutzer beim Start der App in der Mitte der Szene zu platzieren.</span><span class="sxs-lookup"><span data-stu-id="f0483-147">In the **Details** tab, set **Location** to **X = 0, Y = 0,** and **Z = 0** to place the user at the center of the scene when the app starts</span></span>

![Unreal-Editor-Szene mit hinzugefügter Position und PlayerStart.](images/unreal-quickstart-img-07.png)

3. <span data-ttu-id="f0483-149">Ziehen Sie von der Registerkarte **Basic** (Einfach) einen **Würfel** auf die Szene.</span><span class="sxs-lookup"><span data-stu-id="f0483-149">From the **Basic** tab, drag a **Cube** into the scene</span></span>
* <span data-ttu-id="f0483-150">Legen Sie die **Position** des Würfels auf **X = 50, Y = 0** und **Z = 0** fest, damit der Würfel beim Start 50 cm vom Spieler entfernt platziert wird.</span><span class="sxs-lookup"><span data-stu-id="f0483-150">Set the cube's **Location** to **X = 50, Y = 0**, and **Z = 0** to position the cube 50 cm away from the player at start</span></span>
* <span data-ttu-id="f0483-151">Ändern Sie die **Skalierung** des Würfels in **X = 0,2, Y = 0,2** und **Z = 0,2**.</span><span class="sxs-lookup"><span data-stu-id="f0483-151">Change  the cube's **Scale** to **X = 0.2, Y = 0.2**, and **Z = 0.2**</span></span> 

<span data-ttu-id="f0483-152">Sie können den Würfel erst sehen, wenn Sie Ihrer Szene eine Lichtquelle hinzufügen, und das ist Ihre letzte Aufgabe vor dem Testen der Szene.</span><span class="sxs-lookup"><span data-stu-id="f0483-152">You can't see the cube unless you add a light to your scene, which is your last task before testing the scene.</span></span>

4. <span data-ttu-id="f0483-153">Wechseln Sie im Bereich **Modes** (Modi) zur Registerkarte **Lights** (Lichtquellen), und ziehen Sie ein **Directional Light** (Gerichtetes Licht) auf die Szene.</span><span class="sxs-lookup"><span data-stu-id="f0483-153">In the **Modes** panel, switch to the **Lights** tab and drag a **Directional Light** into the scene</span></span>
* <span data-ttu-id="f0483-154">Positionieren Sie das Licht oberhalb von **PlayerStart**, sodass Sie es sehen können.</span><span class="sxs-lookup"><span data-stu-id="f0483-154">Position the light above **PlayerStart** so you can see it</span></span>

![Unreal-Editor-Szene mit Würfel und hinzugefügtem direktionalem Licht.](images/unreal-quickstart-img-08.png)

5. <span data-ttu-id="f0483-156">Wechseln Sie zu **File > Save Current** (Datei > Aktuelle speichern), benennen Sie Ihr Level **Main** (Hauptlevel), und wählen Sie **Save** (Speichern) aus.</span><span class="sxs-lookup"><span data-stu-id="f0483-156">Go to **File > Save Current**, name your level **Main**, and select **Save**</span></span>

<span data-ttu-id="f0483-157">Nachdem die Szene jetzt festgelegt ist, drücken Sie auf **Play** (Wiedergabe) in der Symbolleiste, um den Würfel in Aktion zu sehen!</span><span class="sxs-lookup"><span data-stu-id="f0483-157">With the scene set, press **Play** in the toolbar to see your cube in action!</span></span> <span data-ttu-id="f0483-158">Wenn Sie Ihre Arbeit genügend gewürdigt haben, drücken Sie Esc, um die Anwendung zu beenden.</span><span class="sxs-lookup"><span data-stu-id="f0483-158">When you're finished admiring your work, press Esc to stop the application.</span></span>

![Szene im Wiedergabemodus mit dem Cube in der Mitte des Bildschirms.](images/unreal-quickstart-img-09.png)

<span data-ttu-id="f0483-160">Nachdem die Szene nun eingerichtet ist, lassen Sie uns sie für einige grundlegende Interaktionen in AR vorbereiten.</span><span class="sxs-lookup"><span data-stu-id="f0483-160">Now that the scene is set up, lets get it ready for some basic interactions in AR.</span></span> <span data-ttu-id="f0483-161">Zunächst müssen Sie eine AR-Sitzung erstellen, und Sie können Blaupausen hinzufügen, um Handinteraktion zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="f0483-161">First, you need to create an AR Session and can add blueprints to enable hand interaction.</span></span>

## <a name="adding-a-session-asset"></a><span data-ttu-id="f0483-162">Hinzufügen eines Sitzungsobjekts</span><span class="sxs-lookup"><span data-stu-id="f0483-162">Adding a session asset</span></span>

<span data-ttu-id="f0483-163">AR-Sitzungen in Unreal kommen nicht aus dem Nichts zustande.</span><span class="sxs-lookup"><span data-stu-id="f0483-163">AR sessions in Unreal don't happen by themselves.</span></span> <span data-ttu-id="f0483-164">Um eine Sitzung zu verwenden, benötigen Sie ein ARSessionConfig-Datenobjekt, mit dem Sie arbeiten können, und das ist Ihre nächste Aufgabe:</span><span class="sxs-lookup"><span data-stu-id="f0483-164">To use a session, you need an ARSessionConfig data asset to work with, which is your next task:</span></span>

1. <span data-ttu-id="f0483-165">Wählen Sie im **Inhaltsbrowser** die Option **Neu hinzufügen > Sonstiges > Datenobjekt** aus, und stellen Sie sicher, dass Sie sich auf der Stammebene der Inhaltsordner befinden.</span><span class="sxs-lookup"><span data-stu-id="f0483-165">In the **Content Browser**, select **Add New > Miscellaneous > Data Asset** and make sure you're at the root Content folder level</span></span>
2. <span data-ttu-id="f0483-166">Wählen Sie **ARSessionConfig** aus, klicken Sie auf **Select** (Auswählen), und geben Sie dem Objekt den Namen **ARSessionConfig**:</span><span class="sxs-lookup"><span data-stu-id="f0483-166">Select **ARSessionConfig**, click **Select**, and name the asset **ARSessionConfig**:</span></span>

![Geöffnetes Fenster „Datenressourcenklasse auswählen“ mit hervorgehobenem AR-Sitzungskonfigurationsobjekt.](images/unreal-quickstart-img-10.png)

2. <span data-ttu-id="f0483-168">Doppelklicken Sie auf **ARSessionConfig**, um es zu öffnen, **Speichern** Sie es mit allen Standardeinstellungen, und kehren Sie zum Hauptfenster zurück.</span><span class="sxs-lookup"><span data-stu-id="f0483-168">Double-click **ARSessionConfig** to open it, **Save** with all default settings, and return to the Main window:</span></span>

![Fenster mit den Details des AR-Sitzungskonfigurationsobjekts.](images/unreal-quickstart-img-11.png)

<span data-ttu-id="f0483-170">Nachdem dies erledigt ist, überzeugen Sie sich im nächsten Schritt davon, dass die AR-Sitzung beim Laden des Levels gestartet und mit dem Ende des Levels beendet wird.</span><span class="sxs-lookup"><span data-stu-id="f0483-170">With that done, your next step is to make sure the AR session starts and stops when the level loads and ends.</span></span> <span data-ttu-id="f0483-171">Glücklicherweise verfügt Unreal über eine spezielle Blaupause, die als **Level Blueprint** (Levelblaupause) bezeichnet wird und als levelweites globales Ereignisdiagramm fungiert.</span><span class="sxs-lookup"><span data-stu-id="f0483-171">Luckily, Unreal has a special blueprint called a **Level Blueprint** that acts as a level-wide global event graph.</span></span> <span data-ttu-id="f0483-172">Durch das Verbinden des ARSessionConfig-Medienobjekts mit der Level Blueprint wird sichergestellt, dass die AR-Sitzung ordnungsgemäß ausgelöst wird, wenn das Spiel beginnt.</span><span class="sxs-lookup"><span data-stu-id="f0483-172">Connecting the ARSessionConfig asset in the Level Blueprint guarantees the AR session will fire right when the game starts playing.</span></span>

3. <span data-ttu-id="f0483-173">Wählen Sie in der Editor-Symbolleiste **Blueprints > Open Level Blueprint** (Blaupausen > Ebenenblaupause öffnen) aus:</span><span class="sxs-lookup"><span data-stu-id="f0483-173">From the editor toolbar, select **Blueprints > Open Level Blueprint**:</span></span>

![Geöffnetes Menü „Blaupause“ mit hervorgehobener Option „Ebenenblaupause öffnen“.](images/unreal-quickstart-img-12.png)

4. <span data-ttu-id="f0483-175">Ziehen Sie den Ausführungsknoten (nach links weisendes Pfeilsymbol) von **Event BeginPlay** (BeginPlay-Ereignis) herunter, und lassen Sie ihn los.</span><span class="sxs-lookup"><span data-stu-id="f0483-175">Drag the execution node (left-facing arrow icon) off **Event BeginPlay** and release</span></span>
* <span data-ttu-id="f0483-176">Suchen Sie nach dem Knoten **Start AR Session** (AR-Sitzung starten), und drücken Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="f0483-176">Search for the **Start AR Session node** and hit enter</span></span>
* <span data-ttu-id="f0483-177">Klicken Sie unter **Session Config** (Sitzungskonfiguration) auf die Dropdownliste **Select Asset** (Medienobjekt auswählen), und wählen Sie das Medienobjekt **ARSessionConfig** aus.</span><span class="sxs-lookup"><span data-stu-id="f0483-177">Click the **Select Asset** dropdown under **Session Config** and choose the **ARSessionConfig** asset</span></span>

![Blaupausendiagramm mit Ereignis „Wiedergabe beginnen“, verbunden mit der Funktion „AR-Sitzung starten“.](images/unreal-quickstart-img-13.png)

5. <span data-ttu-id="f0483-179">Klicken Sie an beliebiger Stelle im EventGraph mit der rechten Maustaste, und erstellen Sie einen neuen Knoten **Event EndPlay**.</span><span class="sxs-lookup"><span data-stu-id="f0483-179">Right-click anywhere in the EventGraph and create a new **Event EndPlay** node.</span></span> 
* <span data-ttu-id="f0483-180">Ziehen Sie den Ausführungspin, lassen Sie ihn los, suchen Sie nach einem Knoten **Stop AR Session** (AR-Sitzung beenden), und drücken Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="f0483-180">Drag the execution pin and release, then search for a **Stop AR Session** node and hit enter</span></span> 
* <span data-ttu-id="f0483-181">Klicken Sie auf **Compile** (Kompilieren), dann auf **Speichern**, und kehren Sie schließlich zum Hauptfenster zurück.</span><span class="sxs-lookup"><span data-stu-id="f0483-181">Hit **Compile**, then **Save** and return to the Main window</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f0483-182">Wenn die AR-Sitzung mit dem Ende des Levels noch weiter ausgeführt wird, funktionieren bestimmte Features möglicherweise nicht mehr, wenn Sie die App beim Streaming zu einem Headset neu starten.</span><span class="sxs-lookup"><span data-stu-id="f0483-182">If the AR session is still running when the level ends, certain features may stop working if you restart your app while streaming to a headset.</span></span>

![Ereignisknoten „Wiedergabe beenden“, angefügt an die Funktion „AR-Sitzung beenden“.](images/unreal-quickstart-img-14.png)

## <a name="setting-up-inputs"></a><span data-ttu-id="f0483-184">Einrichten von Eingaben</span><span class="sxs-lookup"><span data-stu-id="f0483-184">Setting up inputs</span></span>

1. <span data-ttu-id="f0483-185">Wählen Sie **Bearbeiten > Projekteinstellungen** aus, und wechseln Sie zu **Engine > Eingabe**.</span><span class="sxs-lookup"><span data-stu-id="f0483-185">Select **Edit > Project Settings** and go to the **Engine > Input**</span></span>
2. <span data-ttu-id="f0483-186">Wählen Sie das **+** -Symbol neben **Aktionszuordnungen** aus, und erstellen Sie die Aktionen **RightPinch** (rechts zusammendrücken) und **LeftPinch** (links zusammendrücken):</span><span class="sxs-lookup"><span data-stu-id="f0483-186">Select the **+** icon next to **Action Mappings** and create **RightPinch** and **LeftPinch** actions:</span></span>

![Bindungseingabeeinstellungen mit hervorgehobenen Aktionszuordnungen „Rechts zusammendrücken“ und „Links zusammendrücken“.](images/unreal-quickstart-img-15.jpg)

3. <span data-ttu-id="f0483-188">Ordnen Sie die Aktionen **RightPinch** und **LeftPinch** den entsprechenden **OpenXR MSFT-Handinteraktion** saktionen zu:</span><span class="sxs-lookup"><span data-stu-id="f0483-188">Map the **RightPinch** and **LeftPinch** actions the to the respective **OpenXR Msft Hand Interaction** actions:</span></span>

![Aktionszuordnungen mit hervorgehobenen Optionen für die OpenXR MSFT-Handinteraktion.](images/unreal-quickstart-img-16.jpg)

## <a name="setting-up-gestures"></a><span data-ttu-id="f0483-190">Einrichten von Gesten</span><span class="sxs-lookup"><span data-stu-id="f0483-190">Setting up gestures</span></span>

<span data-ttu-id="f0483-191">Nachdem wir die Eingaben eingerichtet haben, können wir nun zum spannenden Teil kommen: Hinzufügen von Gesten!</span><span class="sxs-lookup"><span data-stu-id="f0483-191">Now that we have setup the inputs, we can get to the exciting part: Adding gestures!</span></span> <span data-ttu-id="f0483-192">Lassen Sie uns den Würfel mit einem rechten Zusammendrücken (Right Pinch) drehen und die Anwendung bei einem linken Zusammendrücken (Left Pinch) schließen.</span><span class="sxs-lookup"><span data-stu-id="f0483-192">Lets rotate the cube on the right pinch and quit the application on left pinch.</span></span>

1. <span data-ttu-id="f0483-193">Öffnen Sie die **Ebenenblaupause**, und fügen Sie eine **InputAction RightPinch** und **InputAction LeftPinch** hinzu.</span><span class="sxs-lookup"><span data-stu-id="f0483-193">Open the **Level Blueprint** and add an **InputAction RightPinch** and **InputAction LeftPinch**</span></span>
* <span data-ttu-id="f0483-194">Verbinden Sie das RighPinch-Ereignis mit einer **AddActorLocalRotation**, wobei Ihr **Würfel** als Ziel und **Deltadrehung** auf **X = 0, Y = 0** und **Z = 20** festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="f0483-194">Connect the right pinch event to an **AddActorLocalRotation** with your **Cube** as the target and **Delta Rotation** set to **X = 0, Y = 0**, and **Z = 20**.</span></span> <span data-ttu-id="f0483-195">Der Würfel wird jetzt bei jedem Zusammendrücken um 20 Grad gedreht.</span><span class="sxs-lookup"><span data-stu-id="f0483-195">The cube will now rotate by 20 degrees every time you pinch</span></span>
* <span data-ttu-id="f0483-196">Verbinden Sie das LeftPinch-Ereignis mit **Spiel beenden**.</span><span class="sxs-lookup"><span data-stu-id="f0483-196">Connect the left pinch event to **Quit Game**</span></span>

![Geöffnete Ebenenblaupause wird mit Eingabeaktionen für die Ereignisse RightPinch und LeftPinch.](images/unreal-quickstart-img-17.jpg)

2. <span data-ttu-id="f0483-198">Legen Sie in den Einstellungen zum **Transformieren** die Option **Mobilität** auf **Verschiebbar** fest, damit dynamisches Verschieben ermöglicht wird:</span><span class="sxs-lookup"><span data-stu-id="f0483-198">In the cube's **Transform** settings, set **Mobility** to **Movable** so it can move dynamically:</span></span>

![Transformationseinstellungen mit hervorgehobener Eigenschaft „Mobilität“.](images/unreal-quickstart-img-18.jpg)

<span data-ttu-id="f0483-200">An diesem Punkt sind Sie so weit, die Anwendung bereitzustellen und zu testen!</span><span class="sxs-lookup"><span data-stu-id="f0483-200">At this point, you're ready to deploy and test the application!</span></span>