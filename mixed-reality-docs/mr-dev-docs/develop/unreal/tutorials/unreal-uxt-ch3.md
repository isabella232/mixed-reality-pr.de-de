---
title: 3. Einrichten Ihres Projekts für Mixed Reality
description: Teil 3 von 6 einer Tutorialreihe zum Erstellen einer einfachen Schach-App mit der Unreal Engine 4 und dem UX Tools-Plug-In des Mixed Reality-Toolkits
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Tutorial, Erste Schritte, MRTK, UXT, UX-Tools, Dokumentation, Mixed Reality-Headset Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 82e210aff35f1c41547f022b91114cbca1419830
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679879"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a><span data-ttu-id="1d236-104">3. Einrichten Ihres Projekts für Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="1d236-104">3. Setting up your project for mixed reality</span></span>

## <a name="overview"></a><span data-ttu-id="1d236-105">Übersicht</span><span class="sxs-lookup"><span data-stu-id="1d236-105">Overview</span></span>

<span data-ttu-id="1d236-106">Im vorherigen Tutorial haben Sie Zeit für das Einrichten des Schach-App-Projekts aufgewendet.</span><span class="sxs-lookup"><span data-stu-id="1d236-106">In the previous tutorial, you spent time setting up the chess app project.</span></span> <span data-ttu-id="1d236-107">Dieser Abschnitt führt Sie durch das Einrichten der App für die Mixed Reality-Entwicklung, was konkret das Hinzufügen einer AR-Sitzung bedeutet.</span><span class="sxs-lookup"><span data-stu-id="1d236-107">This section is going to walk you through setting up the app for mixed reality development, which means adding an AR session.</span></span> <span data-ttu-id="1d236-108">Sie verwenden für diese Aufgabe ein ARSessionConfig-Datenobjekt, das viele nützliche AR-Einstellungen wie räumliche Abbildung und Verdeckung aufweist.</span><span class="sxs-lookup"><span data-stu-id="1d236-108">You'll be using an ARSessionConfig data asset for this task, which has a lot of useful AR settings like spatial mapping and occlusion.</span></span> <span data-ttu-id="1d236-109">Wenn Sie tiefer einsteigen möchten, finden Sie in der Dokumentation zur Unreal Engine weitere Details zum Medienobjekt [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) und der Klasse [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html).</span><span class="sxs-lookup"><span data-stu-id="1d236-109">If you want to dive deeper, the Unreal Engine documentation has more details on the [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) asset and the [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) class.</span></span>

## <a name="objectives"></a><span data-ttu-id="1d236-110">Ziele</span><span class="sxs-lookup"><span data-stu-id="1d236-110">Objectives</span></span>
* <span data-ttu-id="1d236-111">Arbeiten mit den AR-Einstellungen der Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="1d236-111">Working with Unreal Engine's AR settings</span></span> 
* <span data-ttu-id="1d236-112">Verwenden eines ARSessionConfig-Datenobjekts</span><span class="sxs-lookup"><span data-stu-id="1d236-112">Using an ARSessionConfig data asset</span></span>
* <span data-ttu-id="1d236-113">Einrichten eines Pawns und des Spielemodus</span><span class="sxs-lookup"><span data-stu-id="1d236-113">Setting up a Pawn and game mode</span></span>

## <a name="adding-the-session-asset"></a><span data-ttu-id="1d236-114">Hinzufügen des Sitzungsobjekts</span><span class="sxs-lookup"><span data-stu-id="1d236-114">Adding the session asset</span></span>
<span data-ttu-id="1d236-115">AR-Sitzungen in Unreal kommen nicht aus dem Nichts zustande.</span><span class="sxs-lookup"><span data-stu-id="1d236-115">AR sessions in Unreal don't happen by themselves.</span></span> <span data-ttu-id="1d236-116">Um eine Sitzung zu verwenden, benötigen Sie ein ARSessionConfig-Datenobjekt, mit dem Sie arbeiten können, und das ist Ihre nächste Aufgabe:</span><span class="sxs-lookup"><span data-stu-id="1d236-116">To use a session you need an ARSessionConfig data asset to work with, which is your next task:</span></span>

1. <span data-ttu-id="1d236-117">Klicken Sie im **Content Browser** (Inhaltsbrowser) auf **Add New > Miscellaneous > Data Asset** (Neu hinzufügen > Sonstiges > Datenobjekt).</span><span class="sxs-lookup"><span data-stu-id="1d236-117">Click **Add New > Miscellaneous > Data Asset** in the **Content Browser**.</span></span> <span data-ttu-id="1d236-118">Achten Sie darauf, dass Sie sich auf der Stammebene des Ordners **Content** befinden.</span><span class="sxs-lookup"><span data-stu-id="1d236-118">Make sure you're at the root **Content** folder level.</span></span> 
    * <span data-ttu-id="1d236-119">Wählen Sie **ARSessionConfig** aus, klicken Sie auf **Select** (Auswählen), und geben Sie dem Objekt den Namen **ARSessionConfig**.</span><span class="sxs-lookup"><span data-stu-id="1d236-119">Select **ARSessionConfig**, click **Select**, and name the asset **ARSessionConfig**.</span></span>

![Erstellen einer Datenressource](images/unreal-uxt/3-createasset.PNG)

3. <span data-ttu-id="1d236-121">Doppelklicken Sie auf **ARSessionConfig**, um es zu öffnen, lassen Sie die Standardeinstellungen unverändert, und klicken Sie auf **Save** (Speichern).</span><span class="sxs-lookup"><span data-stu-id="1d236-121">Double-click **ARSessionConfig** to open it, leave all default settings and hit **Save**.</span></span> <span data-ttu-id="1d236-122">Kehren Sie zum Hauptfenster zurück.</span><span class="sxs-lookup"><span data-stu-id="1d236-122">Return to the Main window.</span></span> 

![AR-Sitzungskonfiguration](images/unreal-uxt/3-arsessionconfig.PNG)

<span data-ttu-id="1d236-124">Nachdem dies erledigt ist, überzeugen Sie sich im nächsten Schritt davon, dass die AR-Sitzung beim Laden des Levels gestartet und mit dem Ende des Levels beendet wird.</span><span class="sxs-lookup"><span data-stu-id="1d236-124">With that done, your next step is to make sure that the AR session starts when the level loads and stops when the level ends.</span></span> <span data-ttu-id="1d236-125">Glücklicherweise verfügt Unreal über eine spezielle Art Blaupause, die als **Level Blueprint** (Levelblaupause) bezeichnet wird und als levelweites globales Ereignisdiagramm fungiert.</span><span class="sxs-lookup"><span data-stu-id="1d236-125">Luckily, Unreal has a special kind of blueprint called a **Level Blueprint** that acts as a level-wide global event graph.</span></span> <span data-ttu-id="1d236-126">Durch das Verbinden des ARSessionConfig-Medienobjekts mit der **Level Blueprint** wird sichergestellt, dass die AR-Sitzung ordnungsgemäß ausgelöst wird, wenn das Spiel beginnt.</span><span class="sxs-lookup"><span data-stu-id="1d236-126">Connecting the ARSessionConfig asset in the **Level Blueprint** guarantees the AR session will fire right when the game starts playing.</span></span>

1. <span data-ttu-id="1d236-127">Klicken Sie in der Editor-Symbolleiste auf **Blueprints > Open Level Blueprint** (Blaupausen > Levelblaupause öffnen):</span><span class="sxs-lookup"><span data-stu-id="1d236-127">Click **Blueprints > Open Level Blueprint** from the editor toolbar:</span></span> 

![Geöffnete Levelblaupause](images/unreal-uxt/3-level-blueprint.PNG)

5. <span data-ttu-id="1d236-129">Ziehen Sie den Ausführungsknoten (nach links gerichtetes Pfeilsymbol) von **Event BeginPlay** (BeginPlay-Ereignis) herunter, und geben Sie ihn frei.</span><span class="sxs-lookup"><span data-stu-id="1d236-129">Drag the execution node (left-facing arrow icon) off **Event BeginPlay** and release.</span></span> <span data-ttu-id="1d236-130">Suchen Sie nach dem Knoten **Start AR Session** (AR-Sitzung starten), und drücken Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="1d236-130">Search for the **Start AR Session** node and hit enter.</span></span>  
    * <span data-ttu-id="1d236-131">Klicken Sie unter **Session Config** (Sitzungskonfiguration) auf die Dropdownliste **Select Asset** (Medienobjekt auswählen), und wählen Sie das Medienobjekt **ARSessionConfig** aus.</span><span class="sxs-lookup"><span data-stu-id="1d236-131">Click the **Select Asset** dropdown under **Session Config** and choose the **ARSessionConfig** asset.</span></span> 

![Starten der AR-Sitzung](images/unreal-uxt/3-start-ar-session.PNG)

6. <span data-ttu-id="1d236-133">Klicken Sie an beliebiger Stelle im EventGraph mit der rechten Maustaste, und erstellen Sie einen neuen Knoten **Event EndPlay**.</span><span class="sxs-lookup"><span data-stu-id="1d236-133">Right-click anywhere in the EventGraph and create a new **Event EndPlay** node.</span></span> <span data-ttu-id="1d236-134">Ziehen Sie den Ausführungspin, und geben Sie ihn frei.</span><span class="sxs-lookup"><span data-stu-id="1d236-134">Drag the execution pin and release.</span></span> <span data-ttu-id="1d236-135">Suchen Sie nach einem Knoten **Stop AR Session**, und drücken Sie die EINGABETASTE.</span><span class="sxs-lookup"><span data-stu-id="1d236-135">Search for a **Stop AR Session** node and hit enter.</span></span> <span data-ttu-id="1d236-136">Wenn die AR-Sitzung mit dem Ende des Levels nicht beendet wird, funktionieren bestimmte Features möglicherweise nicht mehr, wenn Sie die App beim Streaming zu einem Headset neu starten.</span><span class="sxs-lookup"><span data-stu-id="1d236-136">If the AR session isn't stopped when the level ends, certain features may stop working if you restart your app while streaming to a headset.</span></span> 
    * <span data-ttu-id="1d236-137">Klicken Sie auf **Compile** (Kompilieren), **speichern** Sie Ihre Arbeit, und kehren Sie dann zum Hauptfenster zurück.</span><span class="sxs-lookup"><span data-stu-id="1d236-137">Hit **Compile**, then **Save** and return to the Main window.</span></span>

![Beenden der AR-Sitzung](images/unreal-uxt/3-stoparsession.PNG)

## <a name="create-a-pawn"></a><span data-ttu-id="1d236-139">Erstellen eines Pawns</span><span class="sxs-lookup"><span data-stu-id="1d236-139">Create a Pawn</span></span>
<span data-ttu-id="1d236-140">An diesem Punkt benötigt das Projekt noch immer ein Playerobjekt.</span><span class="sxs-lookup"><span data-stu-id="1d236-140">At this point, the project still needs a player object.</span></span> <span data-ttu-id="1d236-141">In Unreal stellt ein **Pawn** den Benutzer im Spiel dar, aber in diesem Fall handelt es sich um die HoloLens 2-Umgebung.</span><span class="sxs-lookup"><span data-stu-id="1d236-141">In Unreal, a **Pawn** represents the user in the game, but in this case it's going to be the HoloLens 2 experience.</span></span>

1. <span data-ttu-id="1d236-142">Klicken Sie im Ordner **Content** (Inhalt) auf **Add New > Blueprint Class** (Neu hinzufügen > Blaupausenklasse), und klappen Sie unten den Abschnitt **All Classes** (Alle Klassen) auf.</span><span class="sxs-lookup"><span data-stu-id="1d236-142">Click **Add New > Blueprint Class** in the **Content** folder and expand the **All Classes** section at the bottom.</span></span> 
    * <span data-ttu-id="1d236-143">Suchen Sie nach **DefaultPawn**, klicken Sie auf **Select** (Auswählen), vergeben Sie den Namen **MRPawn**, und doppelklicken Sie auf die Ressource, um sie zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="1d236-143">Search for **DefaultPawn**, click **Select**, name it **MRPawn**, and double-click the asset to open.</span></span> 

![Erstellen eines neuen Pawns, das von „DefaultPawn“ erbt](images/unreal-uxt/3-defaultpawn.PNG)

> [!NOTE]
> <span data-ttu-id="1d236-145">Standardmäßig verfügen Pawns über Gittermodell- und Kollisionskomponenten.</span><span class="sxs-lookup"><span data-stu-id="1d236-145">By default, Pawns have mesh and collision components.</span></span> <span data-ttu-id="1d236-146">In den meisten Unreal-Projekten handelt es sich bei Pawns um feste Objekte, die mit anderen Komponenten zusammenstoßen können.</span><span class="sxs-lookup"><span data-stu-id="1d236-146">In most Unreal projects, Pawns are solid objects that can collide with other components.</span></span> <span data-ttu-id="1d236-147">Da das Pawn und der Benutzer im Fall von Mixed Reality das Gleiche sind, möchten Sie imstande sein, Hologramme ohne Zusammenstoß zu durchschreiten.</span><span class="sxs-lookup"><span data-stu-id="1d236-147">Since the Pawn and user are the same in mixed reality, you want to be able to pass through holograms without any collisions.</span></span> 

2. <span data-ttu-id="1d236-148">Wählen Sie im Bereich **Components** (Komponenten) **CollisionComponent** aus, und scrollen Sie im Bereich **Details** nach unten zum Abschnitt **Collision** (Kollision).</span><span class="sxs-lookup"><span data-stu-id="1d236-148">Select **CollisionComponent** from the **Components** panel and scroll down to the **Collision** section of the **Details** panel.</span></span> 
    * <span data-ttu-id="1d236-149">Klicken Sie auf die Dropdownliste **Collision Presets** (Kollisionseinstellung), und ändern Sie den Wert in **NoCollision** (Keine Kollision).</span><span class="sxs-lookup"><span data-stu-id="1d236-149">Click the **Collision Presets** dropdown and change the value to **NoCollision**.</span></span> 
    * <span data-ttu-id="1d236-150">Führen Sie dasselbe für **MeshComponent** aus.</span><span class="sxs-lookup"><span data-stu-id="1d236-150">Do the same for the **MeshComponent**</span></span>

![Anpassen der Kollisionsvoreinstellungen des Pawns](images/unreal-uxt/3-nocollision.PNG)

3. <span data-ttu-id="1d236-152">Klicken Sie im Bereich **Components** (Komponenten) auf **Add Component > Camera** (Komponente hinzufügen > Kamera), und benennen Sie sie als **Camera** (Kamera).</span><span class="sxs-lookup"><span data-stu-id="1d236-152">Click **Add Component > Camera** from the **Components** panel and name it **Camera**.</span></span> <span data-ttu-id="1d236-153">Dadurch kann die Spielerkamera sich zusammen mit dem HoloLens 2-Gerät bewegen.</span><span class="sxs-lookup"><span data-stu-id="1d236-153">This allows the player camera to move with the HoloLens 2 device.</span></span>

> [!NOTE]
> <span data-ttu-id="1d236-154">Stellen Sie sicher, dass die **Kamera**-Komponente ein direktes untergeordnetes Element des Stamms ist (**CollisionComponent**).</span><span class="sxs-lookup"><span data-stu-id="1d236-154">Make sure that the **Camera** component is a direct child of the root (**CollisionComponent**).</span></span>

4. <span data-ttu-id="1d236-155">**Kompilieren** Sie die Blaupause, und **speichern** Sie sie.</span><span class="sxs-lookup"><span data-stu-id="1d236-155">**Compile** and **Save** the Blueprint.</span></span>

<span data-ttu-id="1d236-156">Nachdem Sie Ihre Arbeit hier erledigt haben, kehren Sie zum Hauptfenster zurück.</span><span class="sxs-lookup"><span data-stu-id="1d236-156">With your work here done, return to the Main Window.</span></span>

## <a name="create-a-game-mode"></a><span data-ttu-id="1d236-157">Erstellen eines Spielmodus</span><span class="sxs-lookup"><span data-stu-id="1d236-157">Create a Game Mode</span></span>
<span data-ttu-id="1d236-158">Das letzte Puzzleteil der Mixed Reality-Einrichtung ist der Spielemodus.</span><span class="sxs-lookup"><span data-stu-id="1d236-158">The last puzzle piece of the mixed reality setup is the Game Mode.</span></span> <span data-ttu-id="1d236-159">Der Spielemodus bestimmt eine Reihe von Einstellungen für das Spiel oder die Umgebung, zu denen unter anderem auch das zu verwendende Standard-Pawn gehört.</span><span class="sxs-lookup"><span data-stu-id="1d236-159">The Game Mode determines a number of settings for the game or experience, including the default pawn to use.</span></span>

1.  <span data-ttu-id="1d236-160">Klicken Sie im Ordner **Content** (Inhalt) auf **Add New > Blueprint Class** (Neu hinzufügen > Blaupausenklasse), und klappen Sie unten den Abschnitt **All Classes** (Alle Klassen) auf.</span><span class="sxs-lookup"><span data-stu-id="1d236-160">Click **Add New > Blueprint Class** in the **Content** folder and expand the **All Classes** section at the bottom.</span></span> 
    * <span data-ttu-id="1d236-161">Suchen Sie nach **Game Mode Base** (Spielemodusbasis), benennen Sie sie **MRGameMode**, und doppelklicken Sie dann darauf, um sie zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="1d236-161">Search for **Game Mode Base**, name it **MRGameMode** and double-click to open.</span></span> 

![„MRGameMode“ im Inhaltsbrowser](images/unreal-uxt/3-gamemode.PNG)

2.  <span data-ttu-id="1d236-163">Navigieren Sie im Bereich **Details** zum Abschnitt **Classes** (Klassen), und ändern Sie die **Default Pawn Class** (Pawn-Standardklasse) in **MRPawn**.</span><span class="sxs-lookup"><span data-stu-id="1d236-163">Go to the **Classes** section in the **Details** panel and change the **Default Pawn Class** to **MRPawn**.</span></span> 
    * <span data-ttu-id="1d236-164">Klicken Sie auf **Compile** (Kompilieren), **speichern** Sie Ihre Arbeit, und kehren Sie dann zum Hauptfenster zurück.</span><span class="sxs-lookup"><span data-stu-id="1d236-164">Hit **Compile**, then **Save** and return to the Main window.</span></span> 

![Festlegen der Standard-Pawn-Klasse](images/unreal-uxt/3-setpawn.PNG)

3.  <span data-ttu-id="1d236-166">Wählen Sie **Edit > Projects Settings** (Bearbeiten > Projekteinstellungen) aus, und klicken Sie in der Liste auf der linken Seite auf **Maps & Modes** (Zuordnungen und Modi).</span><span class="sxs-lookup"><span data-stu-id="1d236-166">Select **Edit > Projects Settings** and click **Maps & Modes** in the left-hand list.</span></span> 
    * <span data-ttu-id="1d236-167">Klappen Sie **Default Modes** (Standardmodi) auf, und ändern Sie **Default Game Mode** (Standardspielemodus) in **MRGameMode**.</span><span class="sxs-lookup"><span data-stu-id="1d236-167">Expand **Default Modes** and change **Default Game Mode** to **MRGameMode**.</span></span> 
    * <span data-ttu-id="1d236-168">Klappen Sie **Default Maps** (Standardzuordnungen) auf, und ändern Sie sowohl **EditorStartupMap** als auch **GameDefaultMap** in **Main**.</span><span class="sxs-lookup"><span data-stu-id="1d236-168">Expand **Default Maps** and change both **EditorStartupMap** and **GameDefaultMap** to **Main**.</span></span> <span data-ttu-id="1d236-169">Wenn Sie den Editor schließen und wieder öffnen oder das Spiel spielen, wird auf diese Weise standardmäßig die Hauptzuordnung ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="1d236-169">This way when you close and reopen the editor, or play the game, the Main map will be selected by default.</span></span>

![Projekteinstellungen: Zuordnungen und Modi](images/unreal-uxt/3-mapsandmodes.PNG)

<span data-ttu-id="1d236-171">Mit dem jetzt vollständig für Mixed Reality eingerichteten Projekt können Sie jetzt mit dem nächsten Tutorial fortfahren und damit beginnen, der Szene Benutzereingaben hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="1d236-171">With the project fully setup for mixed reality, you're ready to move on to the next tutorial and start adding user input to the scene.</span></span> 

[<span data-ttu-id="1d236-172">Nächster Abschnitt: 4. Interaktives Gestalten der Szene</span><span class="sxs-lookup"><span data-stu-id="1d236-172">Next Section: 4. Making your scene interactive</span></span>](unreal-uxt-ch4.md)
