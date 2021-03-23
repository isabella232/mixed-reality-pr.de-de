---
title: 2. Initialisieren des Projekts und der ersten Anwendung
description: Teil 2 von 6 einer Tutorialreihe zum Erstellen einer Schach-App mit der Unreal Engine 4 und dem UX Tools-Plug-In des Mixed Reality-Toolkits
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Tutorial, Erste Schritte, MRTK, UXT, UX-Tools, Dokumentation, Mixed Reality-Headset Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 9e02ea6cb2710b4661e97dc8b0d5f4f48ab09fa7
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2021
ms.locfileid: "98583899"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="456a8-104">2. Initialisieren des Projekts und der ersten Anwendung</span><span class="sxs-lookup"><span data-stu-id="456a8-104">2. Initializing your project and first application</span></span>

<span data-ttu-id="456a8-105">Im ersten Tutorial beginnen Sie mit einem neuen Unreal-Projekt und aktivieren das HoloLens-Plug-In, erstellen und beleuchten ein Level und fügen Schachfiguren hinzu.</span><span class="sxs-lookup"><span data-stu-id="456a8-105">In the first tutorial, you'll start out with a new Unreal project and enable the HoloLens plugin, create and light a level, and add chess pieces.</span></span> <span data-ttu-id="456a8-106">Sie verwenden unsere vorgefertigten Objekte für alle 3D-Objekte und -Materialien, weshalb Sie nichts selber modellieren müssen.</span><span class="sxs-lookup"><span data-stu-id="456a8-106">You'll be using our pre-made assets for all 3D objects and materials, so don't worry about modeling anything yourself.</span></span> <span data-ttu-id="456a8-107">Am Ende dieses Tutorials verfügen Sie über einen leeren Zeichenbereich, der für Mixed Reality bereit ist.</span><span class="sxs-lookup"><span data-stu-id="456a8-107">By the end of this tutorial, you'll have a blank canvas that's ready for mixed reality.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="456a8-108">Stellen Sie sicher, dass alle auf der Seite [Erste Schritte](/windows/mixed-reality/unreal-uxt-ch1) genannten Voraussetzungen erfüllt sind.</span><span class="sxs-lookup"><span data-stu-id="456a8-108">Make sure you have all the prerequisites from the [Getting Started](/windows/mixed-reality/unreal-uxt-ch1) page.</span></span>

## <a name="objectives"></a><span data-ttu-id="456a8-109">Ziele</span><span class="sxs-lookup"><span data-stu-id="456a8-109">Objectives</span></span>

* <span data-ttu-id="456a8-110">Konfigurieren eines Unreal-Projekts für die HoloLens-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="456a8-110">Configuring an Unreal project for HoloLens development</span></span>
* <span data-ttu-id="456a8-111">Importieren von Medienobjekten und Einrichten einer Szene</span><span class="sxs-lookup"><span data-stu-id="456a8-111">Importing assets and setting up a scene</span></span>
* <span data-ttu-id="456a8-112">Erstellen von Akteuren und Ereignissen auf Skriptebene mithilfe von Blaupausen</span><span class="sxs-lookup"><span data-stu-id="456a8-112">Creating Actors and script-level events with blueprints</span></span>

## <a name="creating-a-new-unreal-project"></a><span data-ttu-id="456a8-113">Erstellen eines neuen Unreal-Projekts</span><span class="sxs-lookup"><span data-stu-id="456a8-113">Creating a new Unreal project</span></span>

<span data-ttu-id="456a8-114">Als erstes benötigen Sie ein Projekt, mit dem Sie arbeiten können.</span><span class="sxs-lookup"><span data-stu-id="456a8-114">The first thing you need is a project to work with.</span></span> <span data-ttu-id="456a8-115">Wenn Sie Einsteiger in die Unreal-Entwicklung sind, müssen Sie aus dem Epic-Startprogramm [unterstützende Dateien herunterladen](./unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal).</span><span class="sxs-lookup"><span data-stu-id="456a8-115">If you're a first-time Unreal developer, you'll need to [download supporting files](./unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) from the Epic Launcher.</span></span>

1. <span data-ttu-id="456a8-116">Starten der Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="456a8-116">Launch Unreal Engine</span></span>

2. <span data-ttu-id="456a8-117">Wählen Sie unter **New Project Categories** (Kategorien für neues Projekt) die Option **Games** (Spiele) aus, und klicken Sie auf **Next** (Weiter).</span><span class="sxs-lookup"><span data-stu-id="456a8-117">Select **Games** in **New Project Categories** and click **Next**.</span></span> 

![Wählen Sie die Projektvorlage „Games“ (Spiele) aus.](images/unreal-uxt/2-gamestemplate.png)

3. <span data-ttu-id="456a8-119">Wählen Sie die **Leere** Vorlage aus, und klicken Sie auf **Weiter**.</span><span class="sxs-lookup"><span data-stu-id="456a8-119">Select the **Blank** Template and click **Next**.</span></span> 

![Auswählen einer leeren Vorlage](images/unreal-uxt/2-template.PNG)

4. <span data-ttu-id="456a8-121">Legen Sie **C++** , **Scalable 3D or 2D, Mobile/Tablet** (Skalierbares 3D oder 2D, Mobilgerät/Tablet) und **No Starter Content** (Keine Startinhalte) als Ihre **Projekteinstellungen** fest, wählen Sie dann einen Speicherort aus, und klicken Sie auf **Projekt erstellen**.</span><span class="sxs-lookup"><span data-stu-id="456a8-121">Set **C++**, **Scalable 3D or 2D, Mobile/Tablet**, and **No Starter Content** as your **Project Settings**, then choose a save location and click **Create Project**.</span></span> 

> [!NOTE]
> <span data-ttu-id="456a8-122">Anstelle eines Blaupausenprojekts müssen Sie ein C++-Projekt auswählen, um das UX Tools-Plug-In zu erstellen, das Sie später in Abschnitt 4 einrichten.</span><span class="sxs-lookup"><span data-stu-id="456a8-122">You must select a C++ project rather than a Blueprint project in order to build the UX Tools plugin, which you'll be setting up later on in section 4.</span></span>

![Anfängliche Projekteinstellungen](images/unreal-uxt/2-project-settings.PNG)

<span data-ttu-id="456a8-124">Das Projekt sollte automatisch im Unreal Editor geöffnet werden, und damit sind Sie für den nächsten Abschnitt bereit.</span><span class="sxs-lookup"><span data-stu-id="456a8-124">The project should open up automatically in the Unreal editor, which means you're ready for the next section.</span></span>

## <a name="enabling-required-plugins"></a><span data-ttu-id="456a8-125">Aktivieren der erforderlichen Plug-Ins</span><span class="sxs-lookup"><span data-stu-id="456a8-125">Enabling required plugins</span></span>

<span data-ttu-id="456a8-126">Bevor Sie mit dem Hinzufügen von Objekten zur Szene beginnen können, müssen Sie zwei Plug-Ins aktivieren.</span><span class="sxs-lookup"><span data-stu-id="456a8-126">You'll need to enable two plugins before you can start adding objects to the scene.</span></span>

1. <span data-ttu-id="456a8-127">Öffnen Sie **Edit > Plugins** (Bearbeiten > Plug-Ins), und wählen Sie in der Liste der integrierten Optionen **Augmented Reality** aus.</span><span class="sxs-lookup"><span data-stu-id="456a8-127">Open **Edit > Plugins** and select **Augmented Reality** from the built-in options list.</span></span> 
    * <span data-ttu-id="456a8-128">Scrollen Sie nach unten zu **HoloLens**, und aktivieren Sie **Enabled** (Aktiviert).</span><span class="sxs-lookup"><span data-stu-id="456a8-128">Scroll down to **HoloLens** and check **Enabled**.</span></span> 

![Aktivieren der HoloLens-Plugins](images/unreal-uxt/2-plugins.PNG)

2. <span data-ttu-id="456a8-130">Wählen Sie in der Liste der integrierten Optionen **Virtual Reality** aus.</span><span class="sxs-lookup"><span data-stu-id="456a8-130">Select **Virtual Reality** from the built-in options list.</span></span> 
    * <span data-ttu-id="456a8-131">Scrollen Sie nach unten zu **Microsoft Windows Mixed Reality**, aktivieren Sie **Enabled** (Aktiviert), und starten Sie den Editor neu.</span><span class="sxs-lookup"><span data-stu-id="456a8-131">Scroll down to **Microsoft Windows Mixed Reality**, check **Enabled**, and restart your editor.</span></span> 

![Aktivieren des Windows Mixed Reality-Plug-Ins](images/unreal-uxt/2-virtual-reality-plugin.PNG)

> [!NOTE]
> <span data-ttu-id="456a8-133">Beide Plug-Ins werden für die Entwicklung für HoloLens 2 benötigt.</span><span class="sxs-lookup"><span data-stu-id="456a8-133">Both plugins are required for HoloLens 2 development.</span></span>

<span data-ttu-id="456a8-134">Nachdem die Plug-Ins aktiviert wurden, ist Ihr leeres Level bereit, Objekte aufzunehmen.</span><span class="sxs-lookup"><span data-stu-id="456a8-134">With the plugins enabled, your empty level is ready for company.</span></span>

## <a name="creating-a-level"></a><span data-ttu-id="456a8-135">Erstellen eines Levels</span><span class="sxs-lookup"><span data-stu-id="456a8-135">Creating a level</span></span>
<span data-ttu-id="456a8-136">Ihre nächste Aufgabe besteht darin, ein Player-Setup mit einem Startpunkt und einem Würfel als Referenz und Maßstab zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="456a8-136">Your next task is to create a player setup with a starting point and a cube for reference and scale.</span></span>

1. <span data-ttu-id="456a8-137">Wählen Sie **File > New Level** (Datei > Neues Level) und dann **Empty Level** (Leeres Level) aus.</span><span class="sxs-lookup"><span data-stu-id="456a8-137">Select **File > New Level** and choose **Empty Level**.</span></span> <span data-ttu-id="456a8-138">Die Standardszene im Viewport sollte nun leer sein.</span><span class="sxs-lookup"><span data-stu-id="456a8-138">The default scene in the viewport should now be empty.</span></span>

2. <span data-ttu-id="456a8-139">Wählen Sie auf der Registerkarte **Modes** (Modi) **Basic** (Einfach) aus, und ziehen Sie **PlayerStart** auf die Szene.</span><span class="sxs-lookup"><span data-stu-id="456a8-139">Select **Basic** from the **Modes** tab and drag **PlayerStart** into the scene.</span></span> 
    * <span data-ttu-id="456a8-140">Legen Sie auf der Registerkarte **Details** **Location** (Position) auf **X = 0**, **Y = 0** und **Z = 0** fest. Dadurch wird der Benutzer beim Start der App in der Mitte der Szene platziert.</span><span class="sxs-lookup"><span data-stu-id="456a8-140">Set **Location** to **X = 0**, **Y = 0**, and **Z = 0** in the **Details** tab to set the user at the center of the scene when the app starts up.</span></span>

![Viewport mit „PlayerStart“](images/unreal-uxt/2-playerstart.PNG)

3. <span data-ttu-id="456a8-142">Ziehen Sie einen **Würfel** von der Registerkarte **Basic** (Einfach) auf die Szene.</span><span class="sxs-lookup"><span data-stu-id="456a8-142">Drag a **Cube** from the **Basic** tab into the scene.</span></span> 
    * <span data-ttu-id="456a8-143">Legen Sie **Location** (Position) auf **X = 50**, **Y = 0** und **Z = 0** fest.</span><span class="sxs-lookup"><span data-stu-id="456a8-143">Set **Location** to **X = 50**, **Y = 0**, and **Z = 0**.</span></span> <span data-ttu-id="456a8-144">Dadurch wird der Würfel beim Start 50 cm vom Spieler entfernt platziert.</span><span class="sxs-lookup"><span data-stu-id="456a8-144">to position the cube 50 cm away from the player at start time.</span></span> 
    * <span data-ttu-id="456a8-145">Ändern Sie **Scale** (Maßstab) in **X = 0,2**, **Y = 0,2** und **Z = 0,2**, um den Würfel zu verkleinern.</span><span class="sxs-lookup"><span data-stu-id="456a8-145">Change **Scale** to **X = 0.2**, **Y = 0.2**, and **Z = 0.2** to shrink the cube down.</span></span> 

<span data-ttu-id="456a8-146">Sie können den Würfel erst sehen, wenn Sie Ihrer Szene eine Lichtquelle hinzufügen, und das ist Ihre letzte Aufgabe vor dem Testen der Szene.</span><span class="sxs-lookup"><span data-stu-id="456a8-146">You can't see the cube unless you add a light to your scene, which is your last task before testing the scene.</span></span>

4. <span data-ttu-id="456a8-147">Wechseln Sie im Bereich **Modes** (Modi) zur Registerkarte **Lights** (Lichtquellen), und ziehen Sie ein **Directional Light** (Gerichtetes Licht) auf die Szene.</span><span class="sxs-lookup"><span data-stu-id="456a8-147">Switch to the **Lights** tab in the **Modes** panel and drag a **Directional Light** into the scene.</span></span> <span data-ttu-id="456a8-148">Positionieren Sie das Licht oberhalb von **PlayerStart**, sodass Sie es sehen können.</span><span class="sxs-lookup"><span data-stu-id="456a8-148">Position the light above **PlayerStart** so you can see it.</span></span>

![Viewport mit hinzugefügtem Licht](images/unreal-uxt/2-light.PNG)

5. <span data-ttu-id="456a8-150">Navigieren Sie zu **File > Save Current** (Datei > Aktuelle speichern), benennen Sie Ihr Level **Main** (Hauptlevel), und wählen Sie **Save** (Speichern) aus.</span><span class="sxs-lookup"><span data-stu-id="456a8-150">Go to **File > Save Current**, name your level **Main**, and select **Save**.</span></span> 

<span data-ttu-id="456a8-151">Nachdem die Szene jetzt festgelegt ist, drücken Sie auf **Play** (Wiedergabe) in der Symbolleiste, um den Würfel in Aktion zu sehen!</span><span class="sxs-lookup"><span data-stu-id="456a8-151">With the scene set, press **Play** in the toolbar to see your cube in action!</span></span> <span data-ttu-id="456a8-152">Wenn Sie Ihre Arbeit genügend gewürdigt haben, drücken Sie **Esc**, um die Anwendung zu beenden.</span><span class="sxs-lookup"><span data-stu-id="456a8-152">When you're finished admiring your work, press **Esc** to stop the application.</span></span>

![Ein Würfel im Viewport](images/unreal-uxt/2-cube.PNG)

<span data-ttu-id="456a8-154">Nachdem die Szene nun eingerichtet ist, können Sie damit beginnen, das Schachbrett und die Schachfigur hinzuzufügen, um die Anwendungsumgebung abzurunden.</span><span class="sxs-lookup"><span data-stu-id="456a8-154">Now that the scene is set up, you can start adding in the chess board and piece to round out the application environment.</span></span>

## <a name="importing-assets"></a><span data-ttu-id="456a8-155">Importieren von Medienobjekten</span><span class="sxs-lookup"><span data-stu-id="456a8-155">Importing assets</span></span>
<span data-ttu-id="456a8-156">Die Szene sieht momentan etwas leer aus, aber das beheben Sie, indem Sie die vorgefertigten Medienobjekte in das Projekt importieren.</span><span class="sxs-lookup"><span data-stu-id="456a8-156">The scene is looking a bit empty at the moment, but you'll fix that by importing the ready-made assets into the project.</span></span>

1. <span data-ttu-id="456a8-157">Laden Sie den Medienobjektordner von [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) herunter, und entpacken Sie ihn mit [7-zip](https://www.7-zip.org/).</span><span class="sxs-lookup"><span data-stu-id="456a8-157">Download and unzip the [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) assets folder using [7-zip](https://www.7-zip.org/).</span></span>

2. <span data-ttu-id="456a8-158">Wählen Sie im **Inhaltsbrowser** die Optionen **Add New > New Folder** (Neu hinzufügen > Neuer Ordner) aus, und benennen Sie ihn **ChessAssets** (Schachobjekte).</span><span class="sxs-lookup"><span data-stu-id="456a8-158">Select **Add New > New Folder** from the **Content Browser** and name it **ChessAssets**.</span></span> 
    * <span data-ttu-id="456a8-159">Doppelklicken Sie auf den neuen Ordner, in den Sie die 3D-Medienobjekte importieren.</span><span class="sxs-lookup"><span data-stu-id="456a8-159">Double-click the new folder where you'll import the 3D assets.</span></span>

![Anzeigen oder Ausblenden des Quellenbereichs](images/unreal-uxt/2-showhidesources.PNG)

3. <span data-ttu-id="456a8-161">Wählen Sie im **Inhaltsbrowser** den Befehl **Importieren** aus, wählen Sie im Ordner mit den entpackten Medienobjekten alle Elemente aus, und klicken Sie auf **Öffnen**.</span><span class="sxs-lookup"><span data-stu-id="456a8-161">Select **Import** from the **Content Browser**, select all the items in the unzipped assets folder and click **Open**.</span></span> 
    * <span data-ttu-id="456a8-162">Die Objekte umfassen die Gittermodelle der 3D-Objekte für das Schachbrett und Figuren im FBX-Format sowie Texturschemas im TGA-Format, die Sie für Materialien verwenden.</span><span class="sxs-lookup"><span data-stu-id="456a8-162">Assets include the 3D object meshes for the chess board and pieces in FBX format and texture maps in TGA format that you'll use to for materials.</span></span>  

4. <span data-ttu-id="456a8-163">Wenn das Fenster mit den FBX-Importoptionen eingeblendet wird, klappen Sie den Abschnitt **Material** auf, und ändern Sie die **Material Import Method** (Methode für den Materialimport) in **Do Not Create Material** (Kein Material erstellen).</span><span class="sxs-lookup"><span data-stu-id="456a8-163">When the FBX Import Options window pops up, expand the **Material** section and change **Material Import Method** to **Do Not Create Material**.</span></span>
    * <span data-ttu-id="456a8-164">Wählen Sie **Import All** (Alle importieren) aus.</span><span class="sxs-lookup"><span data-stu-id="456a8-164">Select **Import All**.</span></span>

![FBX-Importoptionen](images/unreal-uxt/2-nocreatemat.PNG)

<span data-ttu-id="456a8-166">Mehr müssen Sie für die Medienobjekte nicht unternehmen.</span><span class="sxs-lookup"><span data-stu-id="456a8-166">That's all you need to do for the assets.</span></span> <span data-ttu-id="456a8-167">In der nächsten Reihe von Aufgaben befassen Sie sich mit dem Erstellen der Bausteine der Anwendung mithilfe von Blaupausen.</span><span class="sxs-lookup"><span data-stu-id="456a8-167">Your next set of tasks is to create the building blocks of the application with blueprints.</span></span>

## <a name="adding-blueprints"></a><span data-ttu-id="456a8-168">Hinzufügen von Blaupausen</span><span class="sxs-lookup"><span data-stu-id="456a8-168">Adding blueprints</span></span>

1. <span data-ttu-id="456a8-169">Wählen Sie im **Inhaltsbrowser** die Optionen **Add New > New Folder** (Neu hinzufügen > Neuer Ordner) aus, und benennen Sie ihn **Blueprints** (Blaupausen).</span><span class="sxs-lookup"><span data-stu-id="456a8-169">Select **Add New > New Folder** in the **Content Browser** and name it **Blueprints**.</span></span> 

> [!NOTE]
> <span data-ttu-id="456a8-170">Falls Sie [Blaupausen](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html) noch nicht kennen – bei ihnen handelt es sich um spezielle Medienobjekte, die eine knotenbasierte Oberfläche bieten, über die neue Arten von Akteuren und Ereignissen auf der Skriptebene erstellt werden können.</span><span class="sxs-lookup"><span data-stu-id="456a8-170">If you're new to [blueprints](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html), they're special assets that provide a node-based interface for creating new types of Actors and script level events.</span></span> 

2. <span data-ttu-id="456a8-171">Doppelklicken Sie auf den Ordner **Blaupausen**, klicken Sie dann mit der rechten Maustaste, und wählen Sie **Blueprint Class** (Blaupausenklasse) aus.</span><span class="sxs-lookup"><span data-stu-id="456a8-171">Double-click into the **Blueprints** folder, then right-click and select **Blueprint Class**.</span></span>         
    * <span data-ttu-id="456a8-172">Wählen Sie **Actor** (Akteur) aus, und benennen Sie die Blaupause **Board** (Brett).</span><span class="sxs-lookup"><span data-stu-id="456a8-172">Select **Actor** and name the blueprint **Board**.</span></span> 

![Auswählen einer übergeordneten Klasse für Ihre Blaupause](images/unreal-uxt/2-bpparent.PNG)

<span data-ttu-id="456a8-174">Die neue **Board**-Blaupause wird nun im Ordner **Blueprints** (Blaupausen) angezeigt, wie im folgenden Screenshot zu sehen.</span><span class="sxs-lookup"><span data-stu-id="456a8-174">The new **Board** blueprint now shows up in the **Blueprints** folder as seen in the following screenshot.</span></span> 

![Die neue Blaupause „Board“](images/unreal-uxt/2-bpboard.PNG)

<span data-ttu-id="456a8-176">Sie sind jetzt bereit, den erstellten Objekten Materialien hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="456a8-176">You're all set to start adding materials to the created objects.</span></span>

## <a name="working-with-materials"></a><span data-ttu-id="456a8-177">Arbeiten mit Materialien</span><span class="sxs-lookup"><span data-stu-id="456a8-177">Working with materials</span></span>
<span data-ttu-id="456a8-178">Die Objekte, die Sie erstellt haben, sind standardgrau, was visuell nicht viel hermacht.</span><span class="sxs-lookup"><span data-stu-id="456a8-178">The objects you've created are default grey, which isn't much fun to look at.</span></span> <span data-ttu-id="456a8-179">Das Hinzufügen von Materialien und Gittermodellen zu Ihren Objekten ist der letzte Satz von Aufgaben in diesem Tutorial.</span><span class="sxs-lookup"><span data-stu-id="456a8-179">Adding materials and meshes to your objects is the last set of tasks in this tutorial.</span></span>

1. <span data-ttu-id="456a8-180">Doppelklicken Sie auf **Board**, um den Blaupausen-Editor zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="456a8-180">Double-click **Board** to open the blueprint editor.</span></span> 

2. <span data-ttu-id="456a8-181">Wählen Sie im Bereich **Components** (Komponenten) **Add Component > Scene** (Komponente hinzufügen > Szene) aus, und benennen Sie sie **Root** (Stamm).</span><span class="sxs-lookup"><span data-stu-id="456a8-181">Select **Add Component > Scene** from the **Components** panel and name it **Root**.</span></span> <span data-ttu-id="456a8-182">Beachten Sie, dass **Root** im Screenshot unten als untergeordnetes Element von **DefaultSceneRoot** dargestellt ist:</span><span class="sxs-lookup"><span data-stu-id="456a8-182">Notice that **Root** shows up as a child of **DefaultSceneRoot** in the screenshot below:</span></span>

![Ersetzen des Stammordners in Blaupausen](images/unreal-uxt/2-root-blueprint.PNG)


3. <span data-ttu-id="456a8-184">Klicken Sie, und ziehen Sie **Root** auf **DefaultSceneRoot**, um es zu ersetzen und die Kugel im Viewport zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="456a8-184">Click-and-drag **Root** onto **DefaultSceneRoot** to replace it and get rid of the sphere in the viewport.</span></span> 

![Ersetzen des Stamms](images/unreal-uxt/2-root.PNG)


4. <span data-ttu-id="456a8-186">Wählen Sie im Bereich **Components** (Komponenten) **Add Component > Static Mesh** (Komponente hinzufügen > Statisches Gittermodell) aus, und benennen Sie es **SM_Board**.</span><span class="sxs-lookup"><span data-stu-id="456a8-186">Select **Add Component > Static Mesh** from the **Components** panel and name it **SM_Board**.</span></span> <span data-ttu-id="456a8-187">Es wird als untergeordnetes Objekt unter **Root** angezeigt.</span><span class="sxs-lookup"><span data-stu-id="456a8-187">It will appear as a child object under **Root**.</span></span>

![Hinzufügen eines statischen Gitters](images/unreal-uxt/2-sm-board.PNG)

4. <span data-ttu-id="456a8-189">Wählen Sie **SM_Board** aus, scrollen Sie im Bereich **Details** nach unten zum Abschnitt **Static Mesh** (Statisches Gittermodell), und wählen Sie in der Dropdownliste **ChessBoard** aus.</span><span class="sxs-lookup"><span data-stu-id="456a8-189">Select **SM_Board**, scroll down to the **Static Mesh** section of the **Details** panel, and select **ChessBoard** from the dropdown.</span></span> 

![Das Schachbrettgitter im Viewport](images/unreal-uxt/2-sm-board-view.PNG)

5.  <span data-ttu-id="456a8-191">Klappen Sie, wiederum im Bereich **Details** den Abschnitt **Materials** (Materialien) auf, und wählen Sie in der Dropdownliste **Create New Asset > Material** (Neues Medienobjekt erstellen > Material) aus.</span><span class="sxs-lookup"><span data-stu-id="456a8-191">Still in the **Details** panel, expand the **Materials** section and select **Create New Asset > Material** from the dropdown.</span></span> 
    * <span data-ttu-id="456a8-192">Benennen Sie das Material **M_ChessBoard**, und speichern Sie es im Ordner **ChessAssets**.</span><span class="sxs-lookup"><span data-stu-id="456a8-192">Name the material **M_ChessBoard** and save it to the **ChessAssets** folder.</span></span> 

![Erstellen eines neuen Materials](images/unreal-uxt/2-newmat.PNG)

6.  <span data-ttu-id="456a8-194">Doppelklicken Sie auf das Bild des Materials **M_ChessBoard**, um den Material-Editor zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="456a8-194">Double-click the **M_ChessBoard** material imaged to open the Material Editor.</span></span> 

![Geöffneter Material-Editor](images/unreal-uxt/2-material-editor.PNG)

7. <span data-ttu-id="456a8-196">Klicken Sie im Material-Editor mit der rechten Maustaste, und suchen Sie nach **Texture Sample** (Texturbeispiel).</span><span class="sxs-lookup"><span data-stu-id="456a8-196">In the Material Editor, right-click and search for **Texture Sample**.</span></span> 
    * <span data-ttu-id="456a8-197">Klappen Sie im Bereich **Details** den Abschnitt **Material Expression Texture Base** (Texturbasis für Materialausdruck) auf, und legen Sie **Texture** (Textur) auf **ChessBoard_Albedo** fest.</span><span class="sxs-lookup"><span data-stu-id="456a8-197">Expand the **Material Expression Texture Base** section in the **Details** panel and set **Texture** to **ChessBoard_Albedo**.</span></span> 
    * <span data-ttu-id="456a8-198">Ziehen Sie den **RGB**-Ausgabepin auf den Basisfarbpin von **M_ChessBoard**.</span><span class="sxs-lookup"><span data-stu-id="456a8-198">Drag the **RGB** output pin to the Base Color pin of **M_ChessBoard**.</span></span> 

![Festlegen der Basisfarbe](images/unreal-uxt/2-boardalbedomat.PNG)

8.  <span data-ttu-id="456a8-200">Wiederholen Sie den vorherigen Schritt weitere 4 Mal, um vier weitere Knoten **Texture Sample** (Texturbeispiel) mit den folgenden Einstellungen zu erstellen:</span><span class="sxs-lookup"><span data-stu-id="456a8-200">Repeat the previous step 4 more times to create four more **Texture Sample** nodes with the following settings:</span></span>
    * <span data-ttu-id="456a8-201">Legen Sie **Texture** (Textur) auf **ChessBoard_AO** fest, und verknüpfen Sie **RGB** mit dem Pin **Ambient Occlusion** (Umgebungsverdeckung).</span><span class="sxs-lookup"><span data-stu-id="456a8-201">Set **Texture** to **ChessBoard_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="456a8-202">Legen Sie **Texture** (Textur) auf **ChessBoard_Metal** fest, und verknüpfen Sie **RGB** mit dem Pin **Metallic** (Metallisch).</span><span class="sxs-lookup"><span data-stu-id="456a8-202">Set **Texture** to **ChessBoard_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="456a8-203">Legen Sie **Texture** (Textur) auf **ChessBoard_Normal** fest, und verknüpfen Sie **RGB** mit dem Pin **Normal**.</span><span class="sxs-lookup"><span data-stu-id="456a8-203">Set **Texture** to **ChessBoard_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="456a8-204">Legen Sie **Texture** (Textur) auf **ChessBoard_Rough** fest, und verknüpfen Sie **RGB** mit dem Pin **Roughness** (Rauheit).</span><span class="sxs-lookup"><span data-stu-id="456a8-204">Set **Texture** to **ChessBoard_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="456a8-205">Klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="456a8-205">Click **Save**.</span></span> 

![Verbinden der restlichen Texturen](images/unreal-uxt/2-boardmat.PNG)

<span data-ttu-id="456a8-207">Vergewissern Sie sich, dass Ihre Materialeinrichtung wie der Screenshot oben aussieht, bevor Sie fortfahren.</span><span class="sxs-lookup"><span data-stu-id="456a8-207">Make sure your material setup looks like the above screenshot before continuing.</span></span>

## <a name="populating-the-scene"></a><span data-ttu-id="456a8-208">Auffüllen der Szene</span><span class="sxs-lookup"><span data-stu-id="456a8-208">Populating the scene</span></span>
<span data-ttu-id="456a8-209">Wenn Sie zur Blaupause **Board** (Brett) zurückkehren, sehen Sie, dass Ihr soeben erstelltes Material übernommen wurde.</span><span class="sxs-lookup"><span data-stu-id="456a8-209">If you go back to the **Board** blueprint, you'll see that the material you just created has been applied.</span></span> <span data-ttu-id="456a8-210">Jetzt müssen Sie nur noch die Szene einrichten!</span><span class="sxs-lookup"><span data-stu-id="456a8-210">All that's left is setting up the scene!</span></span> <span data-ttu-id="456a8-211">Ändern Sie zunächst die folgenden Eigenschaften, um sicherzustellen, dass das Brett eine sinnvolle Größe aufweist und in richtigen Winkel in der Szene platziert wird:</span><span class="sxs-lookup"><span data-stu-id="456a8-211">First, change the following properties to make sure the board is a reasonable size and angled correctly when it's placed in the scene:</span></span>
1.  <span data-ttu-id="456a8-212">Legen Sie **Scale** (Maßstab) auf **(0,05, 0,05, 0,05)** und **Z Rotation** (Z-Drehung) auf **90** fest.</span><span class="sxs-lookup"><span data-stu-id="456a8-212">Set **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span> 
    * <span data-ttu-id="456a8-213">Klicken Sie in der oberen Symbolleiste auf **Compile** (Kompilieren), dann auf **Save** (Speichern), und kehren Sie zum Hauptfenster zurück.</span><span class="sxs-lookup"><span data-stu-id="456a8-213">Click **Compile** in the top toolbar, then **Save** and return to the Main window.</span></span> 

![Schachbrett mit angewendetem Material](images/unreal-uxt/2-chessboard.PNG)

2.  <span data-ttu-id="456a8-215">Klicken Sie mit der rechten Maustaste auf **Cube > Edit > Delete** (Würfel > Bearbeiten > Löschen), und ziehen Sie **Board** (Brett) aus dem **Content Browser** (Inhaltsbrowser) in den Viewport.</span><span class="sxs-lookup"><span data-stu-id="456a8-215">Right-click **Cube > Edit > Delete** and drag **Board** from the **Content Browser** into the viewport.</span></span> 
    * <span data-ttu-id="456a8-216">Legen Sie **Location** (Position) auf **X = 80**, **Y = 0** und **Z = -20** fest.</span><span class="sxs-lookup"><span data-stu-id="456a8-216">Set **Location** to **X = 80**, **Y = 0**, and **Z = -20**.</span></span> 

3.  <span data-ttu-id="456a8-217">Wählen Sie die Schaltfläche **Play** (Wiedergabe) aus, um das neue Brett im Level anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="456a8-217">Select the **Play** button to view your new board in the level.</span></span> <span data-ttu-id="456a8-218">Drücken Sie **ESC**, um zum Editor zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="456a8-218">Press **Esc** to return to the editor.</span></span> 

<span data-ttu-id="456a8-219">Führen Sie nun die folgenden Schritte aus, um eine Schachfigur zu erstellen, so wie Sie das Brett erstellt haben:</span><span class="sxs-lookup"><span data-stu-id="456a8-219">Now you'll follow the same steps to create a chess piece as you did with the board:</span></span>

1. <span data-ttu-id="456a8-220">Wechseln Sie zum Ordner **Blueprints** (Blaupausen), klicken Sie mit der rechten Maustaste auf **Blueprint Class** (Blaupausenklasse), wählen Sie sie aus, und wählen Sie dann **Actor** (Akteur) aus.</span><span class="sxs-lookup"><span data-stu-id="456a8-220">Go to the **Blueprints** folder, right-click, and select **Blueprint Class** and choose **Actor**.</span></span> <span data-ttu-id="456a8-221">Nennen Sie den Akteur **WhiteKing**.</span><span class="sxs-lookup"><span data-stu-id="456a8-221">Name the actor **WhiteKing**.</span></span>

2. <span data-ttu-id="456a8-222">Doppelklicken Sie auf **WhiteKing**, um ihn im Blaupausen-Editor zu öffnen, wählen Sie **Add Component > Scene** (Komponente hinzufügen > Szene) aus, und benennen Sie sie **Root** (Stamm).</span><span class="sxs-lookup"><span data-stu-id="456a8-222">Double-click **WhiteKing** to open it in the Blueprint Editor, select **Add Component > Scene** and name it **Root**.</span></span> 
    * <span data-ttu-id="456a8-223">Ziehen Sie **Root** auf **DefaultSceneRoot**, um sie zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="456a8-223">Drag-and-drop **Root** onto **DefaultSceneRoot** to replace it.</span></span> 

3. <span data-ttu-id="456a8-224">Klicken Sie auf **Add Component > Static Mesh** (Komponente hinzufügen > Statisches Gittermodell), und benennen Sie es **SM_King**.</span><span class="sxs-lookup"><span data-stu-id="456a8-224">Click **Add Component > Static Mesh** and name it **SM_King**.</span></span> 
    * <span data-ttu-id="456a8-225">Legen Sie im Detailbereich die Option **Static Mesh** (Statisches Gittermodell) auf **Chess_King** und die Option **Material** auf ein neues Material mit dem Namen **M_ChessWhite** fest.</span><span class="sxs-lookup"><span data-stu-id="456a8-225">Set **Static Mesh** to **Chess_King** and **Material** to a new Material called **M_ChessWhite** in the Details panel.</span></span> 

4. <span data-ttu-id="456a8-226">Öffnen Sie **M_ChessWhite** im Material-Editor, und verbinden Sie die folgenden **Texture Sample**-Knoten (Texturbeispiel) in folgender Weise:</span><span class="sxs-lookup"><span data-stu-id="456a8-226">Open **M_ChessWhite** in the Material editor and hook up the following **Texture Sample** nodes to the following:</span></span>
   * <span data-ttu-id="456a8-227">Legen Sie **Textur** auf **ChessWhite_Albedo** fest, und verknüpfen Sie **RGB** mit dem Pin **Basisfarbe**.</span><span class="sxs-lookup"><span data-stu-id="456a8-227">Set **Texture** to **ChessWhite_Albedo** and link the **RGB** to the **Base Color** pin.</span></span>
    * <span data-ttu-id="456a8-228">Legen Sie **Texture** (Textur) auf **ChessWhite_AO** fest, und verknüpfen Sie **RGB** mit dem Pin **Ambient Occlusion** (Umgebungsverdeckung).</span><span class="sxs-lookup"><span data-stu-id="456a8-228">Set **Texture** to **ChessWhite_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="456a8-229">Legen Sie **Texture** (Textur) auf **ChessWihte_Metal** fest, und verknüpfen Sie **RGB** mit dem Pin **Metallic** (Metallisch).</span><span class="sxs-lookup"><span data-stu-id="456a8-229">Set **Texture** to **ChessWhite_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="456a8-230">Legen Sie **Texture** (Textur) auf **ChessWhite_Normal** fest, und verknüpfen Sie **RGB** mit dem Stift **Normal**.</span><span class="sxs-lookup"><span data-stu-id="456a8-230">Set **Texture** to **ChessWhite_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="456a8-231">Legen Sie **Texture** (Textur) auf **ChessWhite_Rough** fest, und verknüpfen Sie **RGB** mit dem Pin **Roughness** (Rauheit).</span><span class="sxs-lookup"><span data-stu-id="456a8-231">Set **Texture** to **ChessWhite_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="456a8-232">Klicken Sie auf **Speichern**.</span><span class="sxs-lookup"><span data-stu-id="456a8-232">Click **Save**.</span></span> 

<span data-ttu-id="456a8-233">Ihr **M_ChessKing**-Material sollte wie die folgende Abbildung aussehen, bevor Sie fortfahren.</span><span class="sxs-lookup"><span data-stu-id="456a8-233">Your **M_ChessKing** material should look like the following image before continuing.</span></span>

![Erstellen des Materials für den König (Schachfigur)](images/unreal-uxt/2-chesskingmat.PNG)

<span data-ttu-id="456a8-235">Sie haben es fast geschafft, wir müssen jetzt nur noch der Szene die neue Schachfigur hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="456a8-235">You're almost there, just need to add the new chess piece into the scene:</span></span> 

1. <span data-ttu-id="456a8-236">Öffnen Sie die **WhiteKing**-Blaupause, ändern Sie den **Scale** (Maßstab) in **(0,05, 0,05, 0,05)** und **Z Rotation** (Z_Drehung) in **90**.</span><span class="sxs-lookup"><span data-stu-id="456a8-236">Open the **WhiteKing** blueprint and change the **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span>
    * <span data-ttu-id="456a8-237">Kompilieren und speichern Sie die Blaupause, und kehren Sie anschließend wieder zum Hauptfenster zurück.</span><span class="sxs-lookup"><span data-stu-id="456a8-237">Compile and save your blueprint, then head back to the main window.</span></span> 

2.  <span data-ttu-id="456a8-238">Ziehen Sie **WhiteKing** in den Viewport, wechseln Sie zum **World Outliner** (Gliederungs-Editor), und ziehen Sie **WhiteKing** auf **Board**, um ihn zum untergeordneten Objekt zu machen.</span><span class="sxs-lookup"><span data-stu-id="456a8-238">Drag **WhiteKing** into the viewport, switch to the **World Outliner** panel drag **WhiteKing** onto **Board** to make it a child object.</span></span>

![Gliederungs-Editor](images/unreal-uxt/2-child.PNG)

3.  <span data-ttu-id="456a8-240">Legen Sie im Bereich **Details** unter **Transform** (Transformieren) die **Location** (Position) von **WhiteKing** auf **X = -26**, **Y = 4** und **Z = 0** fest.</span><span class="sxs-lookup"><span data-stu-id="456a8-240">In the **Details** panel under **Transform**, set **WhiteKing**'s **Location** to **X = -26**, **Y = 4**, and **Z = 0**.</span></span>

<span data-ttu-id="456a8-241">Das wäre geschafft!</span><span class="sxs-lookup"><span data-stu-id="456a8-241">That's a wrap!</span></span> <span data-ttu-id="456a8-242">Wählen Sie **Play** (Wiedergabe) aus, um Ihr aufgefülltes Level in Aktion zu sehen, und drücken Sie **Esc**, wenn Sie die Szene beenden möchten.</span><span class="sxs-lookup"><span data-stu-id="456a8-242">Select **Play** to see your populated level in action, and press **Esc** when you're ready to exit.</span></span> <span data-ttu-id="456a8-243">Sie haben eine Menge gelernt, indem Sie lediglich ein einfaches Projekt erstellt haben, aber jetzt sind Sie bereit, um mit dem nächsten Teil der Reihe fortzufahren: Einrichten für Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="456a8-243">You covered a lot of ground just creating a simple project, but now you're ready to move on to the next part of the series: setting up for mixed reality.</span></span> 

[<span data-ttu-id="456a8-244">Nächster Abschnitt: 3. Einrichten Ihres Projekts für Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="456a8-244">Next Section: 3. Set up your project for mixed reality</span></span>](unreal-uxt-ch3.md)