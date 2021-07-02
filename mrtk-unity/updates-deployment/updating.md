---
title: Aktualisieren von früheren Versionen
description: Dokumentation zur Migration von einer niedrigeren Version von MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 04/19/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 5a914d6408d346dac0bf6c683f401564e875f4d8
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175100"
---
# <a name="updating-from-earlier-versions"></a><span data-ttu-id="a3c57-104">Aktualisieren von früheren Versionen</span><span class="sxs-lookup"><span data-stu-id="a3c57-104">Updating from earlier versions</span></span>

- [<span data-ttu-id="a3c57-105">Upgrade auf eine neue Version von MRTK</span><span class="sxs-lookup"><span data-stu-id="a3c57-105">Upgrading to a new version of MRTK</span></span>](#upgrading-to-a-new-version-of-mrtk)
- [<span data-ttu-id="a3c57-106">2.3.0 bis 2.4.0</span><span class="sxs-lookup"><span data-stu-id="a3c57-106">2.3.0 to 2.4.0</span></span>](#updating-230-to-240)
- [<span data-ttu-id="a3c57-107">2.2.0 bis 2.3.0</span><span class="sxs-lookup"><span data-stu-id="a3c57-107">2.2.0 to 2.3.0</span></span>](#updating-220-to-230)
- [<span data-ttu-id="a3c57-108">2.1.0 bis 2.2.0</span><span class="sxs-lookup"><span data-stu-id="a3c57-108">2.1.0 to 2.2.0</span></span>](#updating-210-to-220)
- [<span data-ttu-id="a3c57-109">2.0.0 bis 2.1.0</span><span class="sxs-lookup"><span data-stu-id="a3c57-109">2.0.0 to 2.1.0</span></span>](#updating-200-to-210)
- [<span data-ttu-id="a3c57-110">RC2 bis 2.0.0</span><span class="sxs-lookup"><span data-stu-id="a3c57-110">RC2 to 2.0.0</span></span>](#updating-rc2-to-200)

## <a name="finding-the-current-version"></a><span data-ttu-id="a3c57-111">Suchen der aktuellen Version</span><span class="sxs-lookup"><span data-stu-id="a3c57-111">Finding the current version</span></span> 

<span data-ttu-id="a3c57-112">Befolgen Sie diese Anweisungen, um herauszufinden, welche Version des MRTK Sie derzeit verwenden:</span><span class="sxs-lookup"><span data-stu-id="a3c57-112">Follow these instructions to figure out which version of the MRTK you're currently using:</span></span>

1. <span data-ttu-id="a3c57-113">Öffnen Ihres MRTK-Projekts in Unity</span><span class="sxs-lookup"><span data-stu-id="a3c57-113">Open your MRTK project in Unity</span></span>
2. <span data-ttu-id="a3c57-114">Navigieren Sie in Ihrem Project fenster zum Ordner "MixedRealityToolkit".</span><span class="sxs-lookup"><span data-stu-id="a3c57-114">Navigate to the "MixedRealityToolkit" folder in your Project window</span></span>
3. <span data-ttu-id="a3c57-115">Öffnen Sie die Datei "Version".</span><span class="sxs-lookup"><span data-stu-id="a3c57-115">Open the file called "Version"</span></span>

<span data-ttu-id="a3c57-116">Wenn die datei und der Ordner oben nicht vorhanden sind, verwenden Sie eine neuere Version des MRTK.</span><span class="sxs-lookup"><span data-stu-id="a3c57-116">If the file and folder above doesn't exist, you're on a newer version of the MRTK.</span></span> <span data-ttu-id="a3c57-117">Versuchen Sie in diesem Fall Folgendes:</span><span class="sxs-lookup"><span data-stu-id="a3c57-117">In that case, try the following:</span></span>

1. <span data-ttu-id="a3c57-118">Navigieren Sie zum Ordner "Mixed Reality Toolkit Foundation".</span><span class="sxs-lookup"><span data-stu-id="a3c57-118">Navigate to the "Mixed Reality Toolkit Foundation" folder</span></span>
2. <span data-ttu-id="a3c57-119">Klicken Sie auf "package.json", um eine Vorschau in Unity anzuzeigen, oder öffnen Sie sie mit einem Text-Editor.</span><span class="sxs-lookup"><span data-stu-id="a3c57-119">Click on the "package.json" to see a preview in Unity or open it with a text editor</span></span>
3. <span data-ttu-id="a3c57-120">Suchen Sie nach der Zeile mit dem Wort "version:".</span><span class="sxs-lookup"><span data-stu-id="a3c57-120">Look for the line with the word "version:"</span></span> 

## <a name="upgrading-to-a-new-version-of-mrtk"></a><span data-ttu-id="a3c57-121">Upgrade auf eine neue Version von MRTK</span><span class="sxs-lookup"><span data-stu-id="a3c57-121">Upgrading to a new version of MRTK</span></span>

<span data-ttu-id="a3c57-122">*Es wird dringend empfohlen, das [Migrationstool](../features/tools/migration-window.md) auszuführen, nachdem das MRTK-Update* für die automatische Fehlerbehebung und das Upgrade von veralteten Komponenten und die Anpassung an breaking changes durchgeführt wurde.</span><span class="sxs-lookup"><span data-stu-id="a3c57-122">*It is strongly recommended to run the [migration tool](../features/tools/migration-window.md) after getting the MRTK update* to auto-fix and upgrade from deprecated components and adjust to breaking changes.</span></span> <span data-ttu-id="a3c57-123">Das Migrationstool ist Teil des **Tools-Pakets.**</span><span class="sxs-lookup"><span data-stu-id="a3c57-123">The migration tool is part of the **Tools** package.</span></span>

<span data-ttu-id="a3c57-124">In den folgenden Anweisungen wird der Upgradepfad von 2.4.0 auf 2.5.0 beschrieben.</span><span class="sxs-lookup"><span data-stu-id="a3c57-124">The instructions below describe the 2.4.0 to 2.5.0 upgrade path.</span></span> <span data-ttu-id="a3c57-125">Wenn Ihr Projekt auf Version 2.3.0 oder früher basiert, lesen Sie die Änderungen zwischen den [Versionen,](#updating-230-to-240) um den Upgradepfad zu verstehen, oder lesen Sie die Anweisungen der vorherigen [Version,](https://microsoft.github.io/MixedRealityToolkit-Unity/version/releases/2.4.0/Documentation/Updating.html) um ein Versionsupgrade durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="a3c57-125">If your project is on 2.3.0 or earlier, read on to the changes [between versions](#updating-230-to-240) to understand the upgrade path, or read the previous [release's instructions](https://microsoft.github.io/MixedRealityToolkit-Unity/version/releases/2.4.0/Documentation/Updating.html) to do a version-by-version upgrade.</span></span>

### <a name="mixed-reality-feature-tool"></a><span data-ttu-id="a3c57-126">Mixed Reality Feature-Tool</span><span class="sxs-lookup"><span data-stu-id="a3c57-126">Mixed Reality Feature Tool</span></span>
<span data-ttu-id="a3c57-127">Die einfachste Möglichkeit zum Aktualisieren von MRTK auf eine neuere Version von MRTK ist die Verwendung des [Mixed Reality Feature Tools,](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) um die neuesten Pakete herunterzuladen und direkt in Ihr Unity-Projekt zu laden.</span><span class="sxs-lookup"><span data-stu-id="a3c57-127">The easiest way to upgrade MRTK to a newer version MRTK is by using the [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) to download the latest packages and load them directly to your Unity project.</span></span>

<span data-ttu-id="a3c57-128">Wenn das Projekt zuvor Unity-Medienobjektdateien (.unitypackage) verwendet hat, lesen Sie [diese Anweisungen.](#switching-from-unity-asset-files-to-mixed-reality-feature-tool)</span><span class="sxs-lookup"><span data-stu-id="a3c57-128">If the project previously used Unity asset (.unitypackage) files, please see [these instructions](#switching-from-unity-asset-files-to-mixed-reality-feature-tool).</span></span> 

### <a name="unity-asset-unitypackage-files"></a><span data-ttu-id="a3c57-129">Unity-Medienobjektdateien (.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="a3c57-129">Unity asset (.unitypackage) files</span></span>

<span data-ttu-id="a3c57-130">Ein weiterer Upgradepfad besteht darin, MRTK-Unity-Pakete manuell herunterzuladen und auf Ihr Projekt anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="a3c57-130">Another upgrade path is to manually download MRTK Unity packages and apply them to your project.</span></span> <span data-ttu-id="a3c57-131">Sehen Sie sich die folgenden Schritte an:</span><span class="sxs-lookup"><span data-stu-id="a3c57-131">See the steps below,</span></span>

1. <span data-ttu-id="a3c57-132">Speichern Sie eine Kopie Des aktuellen Projekts, falls Sie zu einem beliebigen Zeitpunkt in den Upgradeschritten auf Fehler stoßen.</span><span class="sxs-lookup"><span data-stu-id="a3c57-132">Save a copy of your current project, in case you hit any snags at any point in the upgrade steps.</span></span>
1. <span data-ttu-id="a3c57-133">Schließen von Unity</span><span class="sxs-lookup"><span data-stu-id="a3c57-133">Close Unity</span></span>
1. <span data-ttu-id="a3c57-134">Löschen Sie im Ordner *Assets* die folgenden **MRTK-Ordner** zusammen mit ihren META-Dateien (das Projekt enthält möglicherweise nicht alle aufgelisteten Ordner).</span><span class="sxs-lookup"><span data-stu-id="a3c57-134">Inside the *Assets* folder, delete the following **MRTK** folders, along with their .meta files (the project may not have all listed folders)</span></span>
    - <span data-ttu-id="a3c57-135">MRTK/Core</span><span class="sxs-lookup"><span data-stu-id="a3c57-135">MRTK/Core</span></span>
    - <span data-ttu-id="a3c57-136">MRTK/Beispiele</span><span class="sxs-lookup"><span data-stu-id="a3c57-136">MRTK/Examples</span></span>
    - <span data-ttu-id="a3c57-137">MRTK/Extensions</span><span class="sxs-lookup"><span data-stu-id="a3c57-137">MRTK/Extensions</span></span>
    - <span data-ttu-id="a3c57-138">MRTK/Providers</span><span class="sxs-lookup"><span data-stu-id="a3c57-138">MRTK/Providers</span></span>
    - <span data-ttu-id="a3c57-139">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="a3c57-139">MRTK/SDK</span></span>
    - <span data-ttu-id="a3c57-140">MRTK/Services</span><span class="sxs-lookup"><span data-stu-id="a3c57-140">MRTK/Services</span></span>
    - <span data-ttu-id="a3c57-141">MRTK/StandardAssets</span><span class="sxs-lookup"><span data-stu-id="a3c57-141">MRTK/StandardAssets</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="a3c57-142">Wenn Änderungen an den MRTK-Shadern vorgenommen wurden, erstellen Sie eine lokale Sicherung, bevor Sie den Ordner MRTK/StandardAssets löschen.</span><span class="sxs-lookup"><span data-stu-id="a3c57-142">If modifications were made to the MRTK shaders, create a local backup before deleteing the MRTK/StandardAssets folder</span></span>
    - <span data-ttu-id="a3c57-143">MRTK/Tools</span><span class="sxs-lookup"><span data-stu-id="a3c57-143">MRTK/Tools</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="a3c57-144">Löschen Sie NICHT den Ordner **MixedRealityToolkit.Generated** oder die zugehörige META-Datei.</span><span class="sxs-lookup"><span data-stu-id="a3c57-144">Do NOT delete the **MixedRealityToolkit.Generated** folder, or its .meta file.</span></span>
1. <span data-ttu-id="a3c57-145">Löschen des **Bibliotheksordners**</span><span class="sxs-lookup"><span data-stu-id="a3c57-145">Delete the **Library** folder</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="a3c57-146">Einige Unity-Tools wie Unity Collab speichern Konfigurationsinformationen im Ordner Bibliothek.</span><span class="sxs-lookup"><span data-stu-id="a3c57-146">Some Unity tools, like Unity Collab, save configuration info to the Library folder.</span></span> <span data-ttu-id="a3c57-147">Wenn Sie ein Tool verwenden, das dies tut, kopieren Sie zunächst den Datenordner des Tools aus der Bibliothek, bevor Sie es löschen, und stellen Sie ihn dann wieder her, nachdem die Bibliothek neu generiert wurde.</span><span class="sxs-lookup"><span data-stu-id="a3c57-147">If using a tool that does this, first copy the tool's data folder from Library before deleting, then restore it after Library is regenerated.</span></span>
1. <span data-ttu-id="a3c57-148">Erneutes Öffnen des Projekts in Unity</span><span class="sxs-lookup"><span data-stu-id="a3c57-148">Re-open the project in Unity</span></span>
1. <span data-ttu-id="a3c57-149">Importieren der neuen Unity-Pakete</span><span class="sxs-lookup"><span data-stu-id="a3c57-149">Import the new unity packages</span></span>
    - <span data-ttu-id="a3c57-150">Grundlage: _Importieren Sie zuerst dieses Paket._</span><span class="sxs-lookup"><span data-stu-id="a3c57-150">Foundation - _Import this package first_</span></span>
    - <span data-ttu-id="a3c57-151">Tools</span><span class="sxs-lookup"><span data-stu-id="a3c57-151">Tools</span></span>
    - <span data-ttu-id="a3c57-152">(Optional) Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="a3c57-152">(Optional) Extensions</span></span>
    > [!NOTE]
    > <span data-ttu-id="a3c57-153">Wenn zusätzliche Erweiterungen installiert wurden, müssen sie möglicherweise erneut importiert werden.</span><span class="sxs-lookup"><span data-stu-id="a3c57-153">If additional extensions had been installed, they may need to be re-imported.</span></span>
    - <span data-ttu-id="a3c57-154">(Optional) Beispiele</span><span class="sxs-lookup"><span data-stu-id="a3c57-154">(Optional) Examples</span></span>
1. <span data-ttu-id="a3c57-155">Schließen Sie Unity, und löschen Sie den Ordner **Bibliothek** (lesen Sie zuerst den Hinweis unten!).</span><span class="sxs-lookup"><span data-stu-id="a3c57-155">Close Unity and delete the **Library** folder (read the note below first!).</span></span> <span data-ttu-id="a3c57-156">Dieser Schritt ist erforderlich, um Unity zu zwingen, seine Ressourcendatenbank zu aktualisieren und vorhandene benutzerdefinierte Profile abzustimmen.</span><span class="sxs-lookup"><span data-stu-id="a3c57-156">This step is necessary to force Unity to refresh its asset database and reconcile existing custom profiles.</span></span>
1. <span data-ttu-id="a3c57-157">Starten Sie Unity und für jede Szene im Projekt.</span><span class="sxs-lookup"><span data-stu-id="a3c57-157">Launch Unity, and for each scene in the project</span></span>
    - <span data-ttu-id="a3c57-158">Löschen Sie **MixedRealityToolkit** und **MixedRealityPlayspace** aus der Hierarchie, sofern vorhanden.</span><span class="sxs-lookup"><span data-stu-id="a3c57-158">Delete **MixedRealityToolkit** and **MixedRealityPlayspace**, if present, from the hierarchy.</span></span> <span data-ttu-id="a3c57-159">Dadurch wird die Hauptkamera gelöscht, aber im nächsten Schritt neu erstellt.</span><span class="sxs-lookup"><span data-stu-id="a3c57-159">This will delete the main camera, but it will be re-created in the next step.</span></span> <span data-ttu-id="a3c57-160">Wenn Eigenschaften der Hauptkamera manuell geändert wurden, müssen diese nach der Erstellung der neuen Kamera manuell erneut angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="a3c57-160">If any properties of the main camera have been manually changed, these will have to be re-applied manually once the new camera is created.</span></span>
    - <span data-ttu-id="a3c57-161">Wählen Sie **MixedRealityToolkit -> Zur Szene hinzufügen und konfigurieren aus.**</span><span class="sxs-lookup"><span data-stu-id="a3c57-161">Select **MixedRealityToolkit -> Add to Scene and Configure**</span></span>
    - <span data-ttu-id="a3c57-162">Wählen Sie **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** (Nur einmal erforderlich) aus. Dadurch werden alle benutzerdefinierten Controllerzuordnungsprofile mit aktualisierten Achsen und Daten aktualisiert, während Ihre benutzerdefinierten Zugewiesenen Eingabeaktionen intakt bleiben.</span><span class="sxs-lookup"><span data-stu-id="a3c57-162">Select **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** (only needs to be done once)       - This will update any custom controller mapping profiles with updated axes and data, while leaving your custom-assigned input actions intact</span></span>
1. <span data-ttu-id="a3c57-163">Führen Sie das [Migrationstool](../features/tools/migration-window.md) aus, und führen Sie das Tool auf der *vollständigen Project* aus, um sicherzustellen, dass der gesamte Code auf den neuesten Stand aktualisiert wird.</span><span class="sxs-lookup"><span data-stu-id="a3c57-163">Run the [migration tool](../features/tools/migration-window.md) and run the tool on the *Full Project* to ensure that all of your code is updated to the latest.</span></span>
   <span data-ttu-id="a3c57-164">Das Migrationsfenster enthält eine Reihe verschiedener Migrationshandler, die jeweils eigenständig ausgeführt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="a3c57-164">The migration window contains a number of different migration handlers, which must each be run on their own.</span></span> <span data-ttu-id="a3c57-165">Dieser Schritt umfasst Folgendes:</span><span class="sxs-lookup"><span data-stu-id="a3c57-165">This step involves:</span></span>
   - <span data-ttu-id="a3c57-166">Wählen Sie den ersten Migrationshandler aus der Dropdownliste Auswahl des **Migrationshandlers** aus.</span><span class="sxs-lookup"><span data-stu-id="a3c57-166">Select the first migration handler from the **Migration Handler Selection** dropdown.</span></span>
   - <span data-ttu-id="a3c57-167">Klicken Sie auf die Schaltfläche "Full Project".</span><span class="sxs-lookup"><span data-stu-id="a3c57-167">Click the "Full Project" button.</span></span>
   - <span data-ttu-id="a3c57-168">Klicken Sie auf die Schaltfläche "Vollständiges Projekt zur Migration hinzufügen" (dadurch wird das gesamte Projekt nach zu migrierenden Objekten überprüft).</span><span class="sxs-lookup"><span data-stu-id="a3c57-168">Click the "Add full project for migration" button (this will scan the entire project for objects to migrate).</span></span>
   - <span data-ttu-id="a3c57-169">Klicken Sie auf die Schaltfläche "Migrieren", die aktiviert werden soll, wenn migrierte Objekte gefunden wurden.</span><span class="sxs-lookup"><span data-stu-id="a3c57-169">Click the "Migrate" button which should be enabled if any migrateable objects were found.</span></span>
   - <span data-ttu-id="a3c57-170">Wiederholen Sie die vorherigen drei Schritte für jeden Migrationshandler in der Dropdownliste.</span><span class="sxs-lookup"><span data-stu-id="a3c57-170">Repeat the previous three steps for each of the migration handlers within the dropdown.</span></span>
     <span data-ttu-id="a3c57-171">(In [diesem Problem](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8552) wird die Arbeit behandelt, die zur Vereinfachung dieses Migrationsprozesses in einem zukünftigen Release ausgeführt werden kann.)</span><span class="sxs-lookup"><span data-stu-id="a3c57-171">(See [this issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8552) which covers work that can be done to simplify this migration process in a future release)</span></span>

### <a name="switching-from-unity-asset-files-to-mixed-reality-feature-tool"></a><span data-ttu-id="a3c57-172">Wechseln von Unity-Medienobjektdateien zu Mixed Reality Feature-Tool</span><span class="sxs-lookup"><span data-stu-id="a3c57-172">Switching from Unity asset files to Mixed Reality Feature Tool</span></span>

<span data-ttu-id="a3c57-173">Der Wechsel von Unity-Medienobjektdateien zu Mixed Reality FeatureTool-Paketen bietet eine Reihe von Vorteilen:</span><span class="sxs-lookup"><span data-stu-id="a3c57-173">Switching from Unity asset files to Mixed Reality Feature Tool packages brings a number of benefits:</span></span>

- <span data-ttu-id="a3c57-174">Einfacheres Aktualisieren</span><span class="sxs-lookup"><span data-stu-id="a3c57-174">Easier updating</span></span>
- <span data-ttu-id="a3c57-175">Schnellere Kompilierungszeiten</span><span class="sxs-lookup"><span data-stu-id="a3c57-175">Faster compile times</span></span>
- <span data-ttu-id="a3c57-176">Weniger Projekte in der Visual Studio Projektmappe</span><span class="sxs-lookup"><span data-stu-id="a3c57-176">Fewer projects in the Visual Studio solution</span></span>

<span data-ttu-id="a3c57-177">Die Umstellung auf die Verwendung des Mixed Reality Feature Tools erfordert einen einmaligen Satz manueller Schritte.</span><span class="sxs-lookup"><span data-stu-id="a3c57-177">Changing to using the Mixed Reality Feature Tool requires a one-time set of manual steps.</span></span>

1. <span data-ttu-id="a3c57-178">Speichern Sie eine Kopie Ihres aktuellen Projekts.</span><span class="sxs-lookup"><span data-stu-id="a3c57-178">Save a copy of your current project.</span></span>
1. <span data-ttu-id="a3c57-179">Schließen von Unity</span><span class="sxs-lookup"><span data-stu-id="a3c57-179">Close Unity</span></span>
1. <span data-ttu-id="a3c57-180">Löschen Sie im Ordner *Assets* die folgenden **MRTK-Ordner** zusammen mit ihren META-Dateien (das Projekt enthält möglicherweise nicht alle aufgelisteten Ordner).</span><span class="sxs-lookup"><span data-stu-id="a3c57-180">Inside the *Assets* folder, delete the following **MRTK** folders, along with their .meta files (the project may not have all listed folders)</span></span>
    - <span data-ttu-id="a3c57-181">MRTK/Core</span><span class="sxs-lookup"><span data-stu-id="a3c57-181">MRTK/Core</span></span>
    - <span data-ttu-id="a3c57-182">MRTK/Beispiele</span><span class="sxs-lookup"><span data-stu-id="a3c57-182">MRTK/Examples</span></span>
    - <span data-ttu-id="a3c57-183">MRTK/Extensions</span><span class="sxs-lookup"><span data-stu-id="a3c57-183">MRTK/Extensions</span></span>
    - <span data-ttu-id="a3c57-184">MRTK/Providers</span><span class="sxs-lookup"><span data-stu-id="a3c57-184">MRTK/Providers</span></span>
    - <span data-ttu-id="a3c57-185">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="a3c57-185">MRTK/SDK</span></span>
    - <span data-ttu-id="a3c57-186">MRTK/Services</span><span class="sxs-lookup"><span data-stu-id="a3c57-186">MRTK/Services</span></span>
    - <span data-ttu-id="a3c57-187">MRTK/StandardAssets</span><span class="sxs-lookup"><span data-stu-id="a3c57-187">MRTK/StandardAssets</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="a3c57-188">Wenn Änderungen an den MRTK-Shadern vorgenommen wurden, erstellen Sie eine lokale Sicherung, bevor Sie den Ordner MRTK/StandardAssets löschen.</span><span class="sxs-lookup"><span data-stu-id="a3c57-188">If modifications were made to the MRTK shaders, create a local backup before deleteing the MRTK/StandardAssets folder</span></span>
    - <span data-ttu-id="a3c57-189">MRTK/Tools</span><span class="sxs-lookup"><span data-stu-id="a3c57-189">MRTK/Tools</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="a3c57-190">Löschen Sie NICHT den Ordner **MixedRealityToolkit.Generated** oder die zugehörige META-Datei.</span><span class="sxs-lookup"><span data-stu-id="a3c57-190">Do NOT delete the **MixedRealityToolkit.Generated** folder, or its .meta file.</span></span>
1. <span data-ttu-id="a3c57-191">Löschen des **Bibliotheksordners**</span><span class="sxs-lookup"><span data-stu-id="a3c57-191">Delete the **Library** folder</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="a3c57-192">Einige Unity-Tools wie Unity Collab speichern Konfigurationsinformationen im Ordner Bibliothek.</span><span class="sxs-lookup"><span data-stu-id="a3c57-192">Some Unity tools, like Unity Collab, save configuration info to the Library folder.</span></span> <span data-ttu-id="a3c57-193">Wenn Sie ein Tool verwenden, das dies tut, kopieren Sie zunächst den Datenordner des Tools aus der Bibliothek, bevor Sie es löschen, und stellen Sie ihn dann wieder her, nachdem die Bibliothek neu generiert wurde.</span><span class="sxs-lookup"><span data-stu-id="a3c57-193">If using a tool that does this, first copy the tool's data folder from Library before deleting, then restore it after Library is regenerated.</span></span>
1. <span data-ttu-id="a3c57-194">Erneutes Öffnen des Projekts in Unity</span><span class="sxs-lookup"><span data-stu-id="a3c57-194">Re-open the project in Unity</span></span>

<span data-ttu-id="a3c57-195">Sobald die vorherigen Schritte ausgeführt wurden, führen Sie das [Mixed Reality Feature Tool](#mixed-reality-feature-tool) aus, und importieren Sie die gewünschte Version des Mixed Reality Toolkits.</span><span class="sxs-lookup"><span data-stu-id="a3c57-195">Once the previous steps have been performed, run the [Mixed Reality Feature Tool](#mixed-reality-feature-tool) and import the desired version of the Mixed Reality Toolkit.</span></span>

## <a name="updating-230-to-240"></a><span data-ttu-id="a3c57-196">Aktualisieren von 2.3.0 auf 2.4.0</span><span class="sxs-lookup"><span data-stu-id="a3c57-196">Updating 2.3.0 to 2.4.0</span></span>

<span data-ttu-id="a3c57-197">[Umbenennungen des Ordners](#folder-renames-in-240) 
 [API-Änderungen](#api-changes-in-240)</span><span class="sxs-lookup"><span data-stu-id="a3c57-197">[Folder renames](#folder-renames-in-240)
[API changes](#api-changes-in-240)</span></span>

### <a name="folder-renames-in-240"></a><span data-ttu-id="a3c57-198">Umbenennung des Ordners in 2.4.0</span><span class="sxs-lookup"><span data-stu-id="a3c57-198">Folder renames in 2.4.0</span></span>

<span data-ttu-id="a3c57-199">Die MixedRealityToolkit-Ordner wurden umbenannt und in Version 2.4 in eine allgemeine Hierarchie verschoben.</span><span class="sxs-lookup"><span data-stu-id="a3c57-199">The MixedRealityToolkit folders have been renamed and moved into a common hierarchy in version 2.4.</span></span> <span data-ttu-id="a3c57-200">Wenn eine Anwendung hart codierte Pfade zu MRTK-Ressourcen verwendet, müssen sie gemäß der folgenden Tabelle aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="a3c57-200">If an application uses hard coded paths to MRTK resources, they will need to be updated per the following table.</span></span>

| <span data-ttu-id="a3c57-201">Vorheriger Ordner</span><span class="sxs-lookup"><span data-stu-id="a3c57-201">Previous Folder</span></span> | <span data-ttu-id="a3c57-202">Neuer Ordner</span><span class="sxs-lookup"><span data-stu-id="a3c57-202">New Folder</span></span> |
| --- | --- |
| <span data-ttu-id="a3c57-203">MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="a3c57-203">MixedRealityToolkit</span></span> | <span data-ttu-id="a3c57-204">MRTK/Core</span><span class="sxs-lookup"><span data-stu-id="a3c57-204">MRTK/Core</span></span> |
| <span data-ttu-id="a3c57-205">MixedRealityToolkit.Examples</span><span class="sxs-lookup"><span data-stu-id="a3c57-205">MixedRealityToolkit.Examples</span></span> | <span data-ttu-id="a3c57-206">MRTK/Beispiele</span><span class="sxs-lookup"><span data-stu-id="a3c57-206">MRTK/Examples</span></span> |
| <span data-ttu-id="a3c57-207">MixedRealityToolkit.Extensions</span><span class="sxs-lookup"><span data-stu-id="a3c57-207">MixedRealityToolkit.Extensions</span></span> | <span data-ttu-id="a3c57-208">MRTK/Extensions</span><span class="sxs-lookup"><span data-stu-id="a3c57-208">MRTK/Extensions</span></span> |
| <span data-ttu-id="a3c57-209">MixedRealityToolkit.Providers</span><span class="sxs-lookup"><span data-stu-id="a3c57-209">MixedRealityToolkit.Providers</span></span> | <span data-ttu-id="a3c57-210">MRTK/Providers</span><span class="sxs-lookup"><span data-stu-id="a3c57-210">MRTK/Providers</span></span> |
| <span data-ttu-id="a3c57-211">MixedRealityToolkit.SDK</span><span class="sxs-lookup"><span data-stu-id="a3c57-211">MixedRealityToolkit.SDK</span></span> | <span data-ttu-id="a3c57-212">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="a3c57-212">MRTK/SDK</span></span> |
| <span data-ttu-id="a3c57-213">MixedRealityToolkit.Services</span><span class="sxs-lookup"><span data-stu-id="a3c57-213">MixedRealityToolkit.Services</span></span> | <span data-ttu-id="a3c57-214">MRTK/Services</span><span class="sxs-lookup"><span data-stu-id="a3c57-214">MRTK/Services</span></span> |
| <span data-ttu-id="a3c57-215">MixedRealityToolkit.Tests</span><span class="sxs-lookup"><span data-stu-id="a3c57-215">MixedRealityToolkit.Tests</span></span> | <span data-ttu-id="a3c57-216">MRTK/Tests</span><span class="sxs-lookup"><span data-stu-id="a3c57-216">MRTK/Tests</span></span> |
| <span data-ttu-id="a3c57-217">MixedRealityToolkit.Tools</span><span class="sxs-lookup"><span data-stu-id="a3c57-217">MixedRealityToolkit.Tools</span></span> | <span data-ttu-id="a3c57-218">MRTK/Tools</span><span class="sxs-lookup"><span data-stu-id="a3c57-218">MRTK/Tools</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="a3c57-219">`MixedRealityToolkit.Generated`Enthält vom Kunden generierte Dateien und bleibt unverändert.</span><span class="sxs-lookup"><span data-stu-id="a3c57-219">The `MixedRealityToolkit.Generated` contains customer generated files and remains unchanged.</span></span>

### <a name="eye-gaze-setup-in-240"></a><span data-ttu-id="a3c57-220">Einrichtung des Anvischens mit den Augen in 2.4.0</span><span class="sxs-lookup"><span data-stu-id="a3c57-220">Eye gaze setup in 2.4.0</span></span>

<span data-ttu-id="a3c57-221">Diese Version von MRTK ändert die Schritte, die für die Einrichtung des Anvischens mit den Augen erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="a3c57-221">This version of MRTK modifies the steps required for eye gaze setup.</span></span> <span data-ttu-id="a3c57-222">Das _Kontrollkästchen "IsEyeTrackingEnabled"_ befindet sich in den Anverfolgungseinstellungen des Eingabezeigerprofils.</span><span class="sxs-lookup"><span data-stu-id="a3c57-222">The _'IsEyeTrackingEnabled'_ checkbox can be found in the gaze settings of the input pointer profile.</span></span> <span data-ttu-id="a3c57-223">Wenn Sie dieses Kontrollkästchen aktivieren, wird das anvische Anvieren auf Augenbasis statt des standardmäßigen kopfbasierten Anvierens aktiviert.</span><span class="sxs-lookup"><span data-stu-id="a3c57-223">Checking this box will enable eye based gaze, rather then the default head based gaze.</span></span>

<span data-ttu-id="a3c57-224">Weitere Informationen zu diesen Änderungen und vollständige Anweisungen für die Eyetrackingeinrichtung finden Sie im Artikel [eye tracking (Blickverfolgung).](../features/input/eye-tracking/eye-tracking-basic-setup.md)</span><span class="sxs-lookup"><span data-stu-id="a3c57-224">For more information on these changes and complete instructions for eye tracking setup, please see the [eye tracking](../features/input/eye-tracking/eye-tracking-basic-setup.md) article.</span></span>

### <a name="eye-gaze-pointer-behavior-in-240"></a><span data-ttu-id="a3c57-225">Verhalten des Anvischens von Augenzeigern in 2.4.0</span><span class="sxs-lookup"><span data-stu-id="a3c57-225">Eye gaze pointer behavior in 2.4.0</span></span>

<span data-ttu-id="a3c57-226">Das Standardzeigerverhalten für das Anvieren mit den Augen wurde so geändert, dass es dem Standardzeigerverhalten des Anvierens mit dem Kopf entspricht.</span><span class="sxs-lookup"><span data-stu-id="a3c57-226">The eye gaze default pointer behavior have been modified to match the head gaze default pointer behavior.</span></span> <span data-ttu-id="a3c57-227">Ein Blickzeiger wird automatisch unterdrückt, sobald eine Hand erkannt wird.</span><span class="sxs-lookup"><span data-stu-id="a3c57-227">An eye gaze pointer will automatically be suppressed once a hand is detected.</span></span> <span data-ttu-id="a3c57-228">Der Blickzeiger wird wieder sichtbar, nachdem er "Auswählen" gesagt hat.</span><span class="sxs-lookup"><span data-stu-id="a3c57-228">The eye gaze pointer will become visible again after saying "Select".</span></span>

<span data-ttu-id="a3c57-229">Details zu Anviert- und Handeinrichtung finden Sie im Artikel [Augen und Hände.](../features/input/eye-tracking/eye-tracking-eyes-and-hands.md#how-to-keep-gaze-pointer-always-on)</span><span class="sxs-lookup"><span data-stu-id="a3c57-229">Details about gaze and hand setups can be found in the [eyes and hands](../features/input/eye-tracking/eye-tracking-eyes-and-hands.md#how-to-keep-gaze-pointer-always-on) article.</span></span>

### <a name="api-changes-in-240"></a><span data-ttu-id="a3c57-230">API-Änderungen in 2.4.0</span><span class="sxs-lookup"><span data-stu-id="a3c57-230">API changes in 2.4.0</span></span>

<span data-ttu-id="a3c57-231">**Benutzerdefinierte Controllerklassen**</span><span class="sxs-lookup"><span data-stu-id="a3c57-231">**Custom controller classes**</span></span>

<span data-ttu-id="a3c57-232">Benutzerdefinierte Controllerklassen mussten zuvor `SetupDefaultInteractions(Handedness)` definieren.</span><span class="sxs-lookup"><span data-stu-id="a3c57-232">Custom controller classes previously had to define `SetupDefaultInteractions(Handedness)`.</span></span> <span data-ttu-id="a3c57-233">Diese Methode wurde in 2.4 als veraltet erklärt, da der Parameter "handness" mit der eigenen Handkraft der Controllerklasse redundant war.</span><span class="sxs-lookup"><span data-stu-id="a3c57-233">This method has been made obsolete in 2.4, as the handedness parameter was redundant with the controller class' own handedness.</span></span> <span data-ttu-id="a3c57-234">Die neue Methode verfügt über keine Parameter.</span><span class="sxs-lookup"><span data-stu-id="a3c57-234">The new method has no parameters.</span></span> <span data-ttu-id="a3c57-235">Darüber hinaus definierten viele Controllerklassen dies auf die gleiche Weise ( `AssignControllerMappings(DefaultInteractions);` ), sodass der vollständige Aufruf in umgestaltet wurde `BaseController` und statt erforderlich eine optionale Außerkraftsetzung vorgenommen wurde.</span><span class="sxs-lookup"><span data-stu-id="a3c57-235">Additionally, many controller classes defined this the same way (`AssignControllerMappings(DefaultInteractions);`), so the full call has been refactored down into `BaseController` and made an optional override instead of required.</span></span>

<span data-ttu-id="a3c57-236">**Eigenschaften des Anväutens mit den Augen**</span><span class="sxs-lookup"><span data-stu-id="a3c57-236">**Eye Gaze properties**</span></span>

<span data-ttu-id="a3c57-237">Die `UseEyeTracking` -Eigenschaft aus `GazeProvider` der Implementierung von wurde in `IMixedRealityEyeGazeProvider` `IsEyeTrackingEnabled` umbenannt.</span><span class="sxs-lookup"><span data-stu-id="a3c57-237">The `UseEyeTracking` property from `GazeProvider` implementation of `IMixedRealityEyeGazeProvider` was renamed to `IsEyeTrackingEnabled`.</span></span>

<span data-ttu-id="a3c57-238">Wenn Sie dies zuvor getan haben...</span><span class="sxs-lookup"><span data-stu-id="a3c57-238">If you did this previously...</span></span>

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.UseEyeTracking = true;
}
```

<span data-ttu-id="a3c57-239">Tun Sie dies jetzt...</span><span class="sxs-lookup"><span data-stu-id="a3c57-239">Do this now...</span></span>

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.IsEyeTrackingEnabled = true;
}
```

<span data-ttu-id="a3c57-240">**WindowsApiChecker-Eigenschaften**</span><span class="sxs-lookup"><span data-stu-id="a3c57-240">**WindowsApiChecker properties**</span></span>

<span data-ttu-id="a3c57-241">Die folgenden WindowsApiChecker-Eigenschaften wurden als veraltet markiert.</span><span class="sxs-lookup"><span data-stu-id="a3c57-241">The following WindowsApiChecker properties have been marked as obsolete.</span></span> <span data-ttu-id="a3c57-242">Verwenden Sie `IsMethodAvailable` , `IsPropertyAvailable` oder `IsTypeAvailable` .</span><span class="sxs-lookup"><span data-stu-id="a3c57-242">Please use `IsMethodAvailable`, `IsPropertyAvailable` or `IsTypeAvailable`.</span></span>

- <span data-ttu-id="a3c57-243">UniversalApiContractV8_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="a3c57-243">UniversalApiContractV8_IsAvailable</span></span>
- <span data-ttu-id="a3c57-244">UniversalApiContractV7_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="a3c57-244">UniversalApiContractV7_IsAvailable</span></span>
- <span data-ttu-id="a3c57-245">UniversalApiContractV6_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="a3c57-245">UniversalApiContractV6_IsAvailable</span></span>
- <span data-ttu-id="a3c57-246">UniversalApiContractV5_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="a3c57-246">UniversalApiContractV5_IsAvailable</span></span>
- <span data-ttu-id="a3c57-247">UniversalApiContractV4_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="a3c57-247">UniversalApiContractV4_IsAvailable</span></span>
- <span data-ttu-id="a3c57-248">UniversalApiContractV3_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="a3c57-248">UniversalApiContractV3_IsAvailable</span></span>

<span data-ttu-id="a3c57-249">Es ist nicht geplant, Eigenschaften zu WindowsApiChecker für zukünftige API-Vertragsversionen hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="a3c57-249">There are no plans to add properties to WindowsApiChecker for future API contract versions.</span></span>

<span data-ttu-id="a3c57-250">**GltfMeshPrimitiveAttributes schreibgeschützt**</span><span class="sxs-lookup"><span data-stu-id="a3c57-250">**GltfMeshPrimitiveAttributes read-only**</span></span>

<span data-ttu-id="a3c57-251">Die primitiven Gltf Mesh-Attribute, die früher festgelegt werden können, sind jetzt schreibgeschützt.</span><span class="sxs-lookup"><span data-stu-id="a3c57-251">The gltf mesh primitive attributes used to be settable, they are now read-only.</span></span> <span data-ttu-id="a3c57-252">Ihre Werte werden einmal festgelegt, wenn sie deserialisiert werden.</span><span class="sxs-lookup"><span data-stu-id="a3c57-252">Their values will be set once when deserialized.</span></span>

### <a name="custom-button-icon-migration"></a><span data-ttu-id="a3c57-253">Migration des Benutzerdefinierten Schaltflächensymbols</span><span class="sxs-lookup"><span data-stu-id="a3c57-253">Custom Button Icon Migration</span></span>

<span data-ttu-id="a3c57-254">Zuvor benutzerdefinierte Schaltflächensymbole mussten dem Quadrenderer der Schaltfläche ein neues Material zugewiesen werden.</span><span class="sxs-lookup"><span data-stu-id="a3c57-254">Previously custom button icons required assigning a new material to the button's quad renderer.</span></span> <span data-ttu-id="a3c57-255">Dies ist nicht mehr erforderlich, und es wird empfohlen, benutzerdefinierte Symboltexturen in ein IconSet zu verschieben.</span><span class="sxs-lookup"><span data-stu-id="a3c57-255">This is no longer necessary and we recommend moving custom icon textures into an IconSet.</span></span> <span data-ttu-id="a3c57-256">Vorhandene benutzerdefinierte Materialien und Symbole werden beibehalten.</span><span class="sxs-lookup"><span data-stu-id="a3c57-256">Existing custom materials and icons are preserved.</span></span> <span data-ttu-id="a3c57-257">Allerdings sind sie bis zum Upgrade weniger optimal.</span><span class="sxs-lookup"><span data-stu-id="a3c57-257">However they will be less optimal until upgraded.</span></span>
<span data-ttu-id="a3c57-258">Verwenden Sie ButtonConfigHelperMigrationHandler, um die Objekte für alle Schaltflächen im Projekt auf das neue empfohlene Format zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="a3c57-258">To upgrade the assets on all buttons in the project to the new recommended format, use the ButtonConfigHelperMigrationHandler.</span></span>
<span data-ttu-id="a3c57-259">(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality.Toolkit.Utilities.ButtonConfigHelperMigrationHandler)</span><span class="sxs-lookup"><span data-stu-id="a3c57-259">(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality.Toolkit.Utilities.ButtonConfigHelperMigrationHandler)</span></span>

![Dialogfeld "Upgradefenster"](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

<span data-ttu-id="a3c57-261">Wenn während der Migration kein Symbol im Standardsymbolsatz gefunden wird, wird in MixedRealityToolkit.Generated/CustomIconSets ein benutzerdefinierter Symbolsatz erstellt.</span><span class="sxs-lookup"><span data-stu-id="a3c57-261">If an icon is not found in the default icon set during migration, a custom icon set will be created in MixedRealityToolkit.Generated/CustomIconSets.</span></span> <span data-ttu-id="a3c57-262">Ein Dialogfeld gibt an, dass dies erfolgt ist.</span><span class="sxs-lookup"><span data-stu-id="a3c57-262">A dialog will indicate that this has taken place.</span></span>

![Benachrichtigung über benutzerdefinierte Symbole](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

## <a name="updating-220-to-230"></a><span data-ttu-id="a3c57-264">Aktualisieren von 2.2.0 auf 2.3.0</span><span class="sxs-lookup"><span data-stu-id="a3c57-264">Updating 2.2.0 to 2.3.0</span></span>

- [<span data-ttu-id="a3c57-265">API-Änderungen</span><span class="sxs-lookup"><span data-stu-id="a3c57-265">API changes</span></span>](#api-changes-in-230)

### <a name="api-changes-in-230"></a><span data-ttu-id="a3c57-266">API-Änderungen in 2.3.0</span><span class="sxs-lookup"><span data-stu-id="a3c57-266">API changes in 2.3.0</span></span>

<span data-ttu-id="a3c57-267">**ControllerPoseSynchronizer**</span><span class="sxs-lookup"><span data-stu-id="a3c57-267">**ControllerPoseSynchronizer**</span></span>

<span data-ttu-id="a3c57-268">Das private ControllerPoseSynchronizer.handedness-Feld wurde als veraltet markiert.</span><span class="sxs-lookup"><span data-stu-id="a3c57-268">The private ControllerPoseSynchronizer.handedness field has been marked as obsolete.</span></span> <span data-ttu-id="a3c57-269">Dies sollte minimale Auswirkungen auf Anwendungen haben, da das Feld außerhalb seiner Klasse nicht sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="a3c57-269">This should have minimal impact on applications as the field is not visible outside of its class.</span></span>

<span data-ttu-id="a3c57-270">Der Setter der öffentlichen ControllerPoseSynchronizer.Handedness-Eigenschaft wurde entfernt ([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)).</span><span class="sxs-lookup"><span data-stu-id="a3c57-270">The public ControllerPoseSynchronizer.Handedness property's setter has been removed ([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)).</span></span>

<span data-ttu-id="a3c57-271">**MSBuild für Unity**</span><span class="sxs-lookup"><span data-stu-id="a3c57-271">**MSBuild for Unity**</span></span>

<span data-ttu-id="a3c57-272">Diese Version des MRTK verwendet eine neuere Version von MSBuild für Unity als frühere Versionen.</span><span class="sxs-lookup"><span data-stu-id="a3c57-272">This version of MRTK uses a newer version of MSBuild for Unity than previous releases.</span></span> <span data-ttu-id="a3c57-273">Wenn die ältere Version während des Ladens des Projekts im Unity-Paket-Manager-Manifest aufgeführt ist, wird das Konfigurationsdialogfeld mit aktivierter Option Enable MSBuild for Unity (MSBuild für Unity aktivieren) angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a3c57-273">During project load, if the older version is listed in the Unity Package Manger manifest, the configuration dialog will appear, with the Enable MSBuild for Unity option checked.</span></span> <span data-ttu-id="a3c57-274">Durch anwenden wird ein Upgrade ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="a3c57-274">Applying will perform an upgrade.</span></span>

<span data-ttu-id="a3c57-275">**ScriptingUtilities**</span><span class="sxs-lookup"><span data-stu-id="a3c57-275">**ScriptingUtilities**</span></span>

<span data-ttu-id="a3c57-276">Die ScriptingUtilities-Klasse wurde als veraltet markiert und durch ScriptUtilities in der Microsoft.MixedReality.Toolkit.Editor.Utilities-Assembly ersetzt.</span><span class="sxs-lookup"><span data-stu-id="a3c57-276">The ScriptingUtilities class has been marked as obsolete and has been replaced by ScriptUtilities, in the Microsoft.MixedReality.Toolkit.Editor.Utilities assembly.</span></span> <span data-ttu-id="a3c57-277">Die neue -Klasse verfeinern das vorherige Verhalten und fügt Unterstützung für das Entfernen von Skriptdefinitionen hinzu.</span><span class="sxs-lookup"><span data-stu-id="a3c57-277">The new class refines previous behavior and adds support for removing scripting definitions.</span></span>

<span data-ttu-id="a3c57-278">Während vorhandener Code in Version 2.3.0 weiterhin funktioniert, wird empfohlen, auf die neue Klasse zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="a3c57-278">While existing code will continue to function in version 2.3.0, it is recommended to update to the new class.</span></span>

<span data-ttu-id="a3c57-279">**ShellHandRayPointer**</span><span class="sxs-lookup"><span data-stu-id="a3c57-279">**ShellHandRayPointer**</span></span>

<span data-ttu-id="a3c57-280">Die Member lineRendererSelected und lineRendererNoTarget der ShellHandRayPointer-Klasse wurden durch lineMaterialSelected bzw. lineMaterialNoTarget ersetzt ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)).</span><span class="sxs-lookup"><span data-stu-id="a3c57-280">The lineRendererSelected and lineRendererNoTarget members of the ShellHandRayPointer class have been replaced by lineMaterialSelected and lineMaterialNoTarget, respectively ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)).</span></span>

<span data-ttu-id="a3c57-281">Ersetzen Sie lineRendererSelected durch lineMaterialSelected und/oder lineRendererNoTarget durch lineMaterialNoTarget, um Kompilierungsfehler zu beheben.</span><span class="sxs-lookup"><span data-stu-id="a3c57-281">Please replace lineRendererSelected with lineMaterialSelected and/or lineRendererNoTarget with lineMaterialNoTarget to resolve compile errors.</span></span>

<span data-ttu-id="a3c57-282">**Räumlicher Beobachter StartupBehavior**</span><span class="sxs-lookup"><span data-stu-id="a3c57-282">**Spatial observer StartupBehavior**</span></span>

<span data-ttu-id="a3c57-283">Räumliche Beobachter, die auf der -Klasse aufbauen, `BaseSpatialObserver` verwenden jetzt den Wert von StartupBehavior, wenn sie erneut aktiviert werden ([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)).</span><span class="sxs-lookup"><span data-stu-id="a3c57-283">Spatial observers built upon the `BaseSpatialObserver` class now honor the value of StartupBehavior when re-enabled ([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)).</span></span>

<span data-ttu-id="a3c57-284">Es sind keine Änderungen erforderlich, um diese Korrektur zu nutzen.</span><span class="sxs-lookup"><span data-stu-id="a3c57-284">No changes are required to take advantage of this fix.</span></span>

<span data-ttu-id="a3c57-285">**Prefabs des UX-Steuerelements aktualisiert, um PressableButton zu verwenden**</span><span class="sxs-lookup"><span data-stu-id="a3c57-285">**UX control prefabs updated to use PressableButton**</span></span>

<span data-ttu-id="a3c57-286">Die folgenden Prefabs verwenden jetzt die PressableButton-Komponente anstelle von TouchHandler für die nahezue Interaktion ([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070)).</span><span class="sxs-lookup"><span data-stu-id="a3c57-286">The following prefabs are now using the PressableButton component instead of TouchHandler for near interaction ([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070))</span></span>

- <span data-ttu-id="a3c57-287">AnimationButton</span><span class="sxs-lookup"><span data-stu-id="a3c57-287">AnimationButton</span></span>
- <span data-ttu-id="a3c57-288">Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="a3c57-288">Button</span></span>
- <span data-ttu-id="a3c57-289">ButtonHoloLens1</span><span class="sxs-lookup"><span data-stu-id="a3c57-289">ButtonHoloLens1</span></span>
- <span data-ttu-id="a3c57-290">ButtonHoloLens1Toggle</span><span class="sxs-lookup"><span data-stu-id="a3c57-290">ButtonHoloLens1Toggle</span></span>
- <span data-ttu-id="a3c57-291">CheckBox</span><span class="sxs-lookup"><span data-stu-id="a3c57-291">CheckBox</span></span>
- <span data-ttu-id="a3c57-292">RadialSet</span><span class="sxs-lookup"><span data-stu-id="a3c57-292">RadialSet</span></span>
- <span data-ttu-id="a3c57-293">ToggleButton</span><span class="sxs-lookup"><span data-stu-id="a3c57-293">ToggleButton</span></span>
- <span data-ttu-id="a3c57-294">ToggleSwitch</span><span class="sxs-lookup"><span data-stu-id="a3c57-294">ToggleSwitch</span></span>
- <span data-ttu-id="a3c57-295">UnityUIButton</span><span class="sxs-lookup"><span data-stu-id="a3c57-295">UnityUIButton</span></span>
- <span data-ttu-id="a3c57-296">UnityUICheckboxButton</span><span class="sxs-lookup"><span data-stu-id="a3c57-296">UnityUICheckboxButton</span></span>
- <span data-ttu-id="a3c57-297">UnityUIRadialButton</span><span class="sxs-lookup"><span data-stu-id="a3c57-297">UnityUIRadialButton</span></span>
- <span data-ttu-id="a3c57-298">UnityUIToggleButton</span><span class="sxs-lookup"><span data-stu-id="a3c57-298">UnityUIToggleButton</span></span>

<span data-ttu-id="a3c57-299">Aufgrund dieser Änderung ist möglicherweise eine Aktualisierung des Anwendungscodes erforderlich.</span><span class="sxs-lookup"><span data-stu-id="a3c57-299">Application code may require updating due to this change.</span></span>

<span data-ttu-id="a3c57-300">**WindowsMixedRealityUtilities-Namespace**</span><span class="sxs-lookup"><span data-stu-id="a3c57-300">**WindowsMixedRealityUtilities namespace**</span></span>

<span data-ttu-id="a3c57-301">Der Namespace von WindowsMixedRealityUtilities wurde von Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input in Microsoft.MixedReality.Toolkit.WindowsMixedReality ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989)) geändert.</span><span class="sxs-lookup"><span data-stu-id="a3c57-301">The namespace of WindowsMixedRealityUtilities changed from Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input to Microsoft.MixedReality.Toolkit.WindowsMixedReality ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989)).</span></span>

<span data-ttu-id="a3c57-302">Aktualisieren Sie #using Anweisungen, um Kompilierungsfehler zu beheben.</span><span class="sxs-lookup"><span data-stu-id="a3c57-302">Please update #using statements to resolve compile errors.</span></span>

## <a name="updating-210-to-220"></a><span data-ttu-id="a3c57-303">Aktualisieren von 2.1.0 auf 2.2.0</span><span class="sxs-lookup"><span data-stu-id="a3c57-303">Updating 2.1.0 to 2.2.0</span></span>

- [<span data-ttu-id="a3c57-304">API-Änderungen</span><span class="sxs-lookup"><span data-stu-id="a3c57-304">API changes</span></span>](#api-changes-in-220)

### <a name="api-changes-in-220"></a><span data-ttu-id="a3c57-305">API-Änderungen in 2.2.0</span><span class="sxs-lookup"><span data-stu-id="a3c57-305">API changes in 2.2.0</span></span>

<span data-ttu-id="a3c57-306">**IMixedRealityBoundarySystem.Contains**</span><span class="sxs-lookup"><span data-stu-id="a3c57-306">**IMixedRealityBoundarySystem.Contains**</span></span>

<span data-ttu-id="a3c57-307">Diese Methode hat zuvor eine bestimmte, von Unity definierte experimentelle Enum verwendet.</span><span class="sxs-lookup"><span data-stu-id="a3c57-307">This method previously took in a specific, Unity-defined experimental enum.</span></span> <span data-ttu-id="a3c57-308">Sie nimmt jetzt eine MRTK-definierte Enum an, die mit der Unity-Enum identisch ist.</span><span class="sxs-lookup"><span data-stu-id="a3c57-308">It now takes in an MRTK-defined enum that's identical to the Unity enum.</span></span> <span data-ttu-id="a3c57-309">Diese Änderung hilft bei der Vorbereitung des MRTK für die zukünftigen Begrenzungs-APIs von Unity.</span><span class="sxs-lookup"><span data-stu-id="a3c57-309">This change helps prepare the MRTK for Unity's future boundary APIs.</span></span>

<span data-ttu-id="a3c57-310">**MixedRealityServiceProfileAttribute**</span><span class="sxs-lookup"><span data-stu-id="a3c57-310">**MixedRealityServiceProfileAttribute**</span></span>

<span data-ttu-id="a3c57-311">Um die Anforderungen für die Unterstützung eines Profils besser zu beschreiben, wurde das MixedRealityServiceProfileAttribute aktualisiert, um eine optionale Auflistung ausgeschlossener Typen hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="a3c57-311">To better describe the requirements for supporting a profile, the MixedRealityServiceProfileAttribute has been updated to add an optional collection of excluded types.</span></span> <span data-ttu-id="a3c57-312">Im Rahmen dieser Änderung wurde die ServiceType-Eigenschaft von Type in Type[] geändert und in RequiredTypes umbenannt.</span><span class="sxs-lookup"><span data-stu-id="a3c57-312">As part of this change, the ServiceType property has been changed from Type to Type[] and been renamed to RequiredTypes.</span></span>

<span data-ttu-id="a3c57-313">Eine zweite Eigenschaft, ExcludedTypes, wurde ebenfalls hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="a3c57-313">A second property, ExcludedTypes has also been added.</span></span>

## <a name="updating-200-to-210"></a><span data-ttu-id="a3c57-314">Aktualisieren von 2.0.0 auf 2.1.0</span><span class="sxs-lookup"><span data-stu-id="a3c57-314">Updating 2.0.0 to 2.1.0</span></span>

- [<span data-ttu-id="a3c57-315">API-Änderungen</span><span class="sxs-lookup"><span data-stu-id="a3c57-315">API changes</span></span>](#api-changes-in-210)
- [<span data-ttu-id="a3c57-316">Profiländerungen</span><span class="sxs-lookup"><span data-stu-id="a3c57-316">Profile changes</span></span>](#profile-changes-in-210)

### <a name="api-changes-in-210"></a><span data-ttu-id="a3c57-317">API-Änderungen in 2.1.0</span><span class="sxs-lookup"><span data-stu-id="a3c57-317">API changes in 2.1.0</span></span>

<span data-ttu-id="a3c57-318">**BaseNearInteractionTouchable**</span><span class="sxs-lookup"><span data-stu-id="a3c57-318">**BaseNearInteractionTouchable**</span></span>

<span data-ttu-id="a3c57-319">Wurde `BaseNearInteractionTouchable` geändert, um die Methode `OnValidate` als virtuell zu markieren.</span><span class="sxs-lookup"><span data-stu-id="a3c57-319">The `BaseNearInteractionTouchable` has been modified to mark the `OnValidate` method as virtual.</span></span> <span data-ttu-id="a3c57-320">Klassen, die `BaseNearInteractionTouchable` erweitern (z. B. `NearInteractionTouchableUnityUI` ), wurden aktualisiert, um diese Änderung widerzuent halten.</span><span class="sxs-lookup"><span data-stu-id="a3c57-320">Classes that extend `BaseNearInteractionTouchable` (ex: `NearInteractionTouchableUnityUI`) have been updated to reflect this change.</span></span>

<span data-ttu-id="a3c57-321">**ColliderNearInteractionTouchable**</span><span class="sxs-lookup"><span data-stu-id="a3c57-321">**ColliderNearInteractionTouchable**</span></span>

<span data-ttu-id="a3c57-322">Die `ColliderNearInteractionTouchable`-Klasse ist veraltet.</span><span class="sxs-lookup"><span data-stu-id="a3c57-322">The `ColliderNearInteractionTouchable` class has been deprecated.</span></span> <span data-ttu-id="a3c57-323">Aktualisieren Sie Codeverweise, um zu `BaseNearInteractionTouchable` verwenden.</span><span class="sxs-lookup"><span data-stu-id="a3c57-323">Please update code references to use `BaseNearInteractionTouchable`.</span></span>

<span data-ttu-id="a3c57-324">**IMixedRealityMouseDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="a3c57-324">**IMixedRealityMouseDeviceManager**</span></span>

<span data-ttu-id="a3c57-325">**_Hinzugefügt_**</span><span class="sxs-lookup"><span data-stu-id="a3c57-325">**_Added_**</span></span>

<span data-ttu-id="a3c57-326">`IMixedRealityMouseDeviceManager` wurden die `CursorSpeed` Eigenschaften und `WheelSpeed` hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="a3c57-326">`IMixedRealityMouseDeviceManager` has been added `CursorSpeed` and `WheelSpeed` properties.</span></span> <span data-ttu-id="a3c57-327">Mit diesen Eigenschaften können Anwendungen einen Multiplikatorwert angeben, mit dem die Geschwindigkeit des Cursors bzw. des Rads skaliert wird.</span><span class="sxs-lookup"><span data-stu-id="a3c57-327">These properties allow applications to specify a multiplier value by which the speed of the cursor and wheel, respectively will be scaled.</span></span>

<span data-ttu-id="a3c57-328">Dies ist eine breaking change und erfordert, dass vorhandene Implementierungen des Mausgeräte-Managers geändert werden.</span><span class="sxs-lookup"><span data-stu-id="a3c57-328">This is a breaking change and requires existing mouse device manager implementations to be modified .</span></span>

>[!NOTE]
><span data-ttu-id="a3c57-329">Diese Änderung ist nicht abwärtskompatibel mit Version 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="a3c57-329">This change is not backwards compatible with version 2.0.0.</span></span>

<span data-ttu-id="a3c57-330">**_Als veraltet markiert_**</span><span class="sxs-lookup"><span data-stu-id="a3c57-330">**_Deprecated_**</span></span>

<span data-ttu-id="a3c57-331">Die Eigenschaft wurde als veraltet markiert und wird aus einer zukünftigen Version des `MouseInputProfile` Microsoft Mixed Reality Toolkits entfernt.</span><span class="sxs-lookup"><span data-stu-id="a3c57-331">The `MouseInputProfile` property has been marked as obsolete and will be removed from a future version of the Microsoft Mixed Reality Toolkit.</span></span> <span data-ttu-id="a3c57-332">Es wird empfohlen, dass Anwendungscode diese Eigenschaft nicht mehr verwendet.</span><span class="sxs-lookup"><span data-stu-id="a3c57-332">It is recommended that application code no longer use this property.</span></span>

<span data-ttu-id="a3c57-333">**Interaktionsfähig**</span><span class="sxs-lookup"><span data-stu-id="a3c57-333">**Interactable**</span></span>

<span data-ttu-id="a3c57-334">Die folgenden Methoden und Eigenschaften sind veraltet und werden aus einer zukünftigen Version des Microsoft Mixed Reality Toolkits entfernt.</span><span class="sxs-lookup"><span data-stu-id="a3c57-334">The following methods and properties have been deprecated and will be removed from a future version of the Microsoft Mixed Reality Toolkit.</span></span> <span data-ttu-id="a3c57-335">Es wird empfohlen, den Anwendungscode nach den Anweisungen im Obsolete-Attribut zu aktualisieren, das in der Konsole angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a3c57-335">The recommendation is to update application code per the guidance contained in the Obsolete attribute and displayed in the console.</span></span>

- `public bool Enabled`
- `public bool FocusEnabled`
- `public void ForceUpdateThemes()`
- `public bool IsDisabled`
- `public bool IsToggleButton`
- `public int GetDimensionIndex()`
- `public State[] GetStates()`
- `public bool RequiresFocus`
- `public void ResetBaseStates()`
- `public virtual void SetCollision(bool collision)`
- `public virtual void SetCustom(bool custom)`
- `public void SetDimensionIndex(int index)`
- `public virtual void SetDisabled(bool disabled)`
- `public virtual void SetFocus(bool focus)`
- `public virtual void SetGesture(bool gesture)`
- `public virtual void SetGestureMax(bool gesture)`
- `public virtual void SetGrab(bool grab)`
- `public virtual void SetInteractive(bool interactive)`
- `public virtual void SetObservation(bool observation)`
- `public virtual void SetObservationTargeted(bool targeted)`
- `public virtual void SetPhysicalTouch(bool touch)`
- `public virtual void SetPress(bool press)`
- `public virtual void SetTargeted(bool targeted)`
- `public virtual void SetToggled(bool toggled)`
- `public virtual void SetVisited(bool visited)`
- `public virtual void SetVoiceCommand(bool voice)`

<span data-ttu-id="a3c57-336">**NearInteractionTouchableSurface**</span><span class="sxs-lookup"><span data-stu-id="a3c57-336">**NearInteractionTouchableSurface**</span></span>

<span data-ttu-id="a3c57-337">Die `NearInteractionTouchableSurface` -Klasse wurde hinzugefügt und dient jetzt als Basisklasse für `NearInteractionTouchable` und `NearInteractionTouchableUnityUI` .</span><span class="sxs-lookup"><span data-stu-id="a3c57-337">The `NearInteractionTouchableSurface` class has been added and now serves as the base class for `NearInteractionTouchable` and `NearInteractionTouchableUnityUI`.</span></span>

### <a name="profile-changes-in-210"></a><span data-ttu-id="a3c57-338">Profiländerungen in 2.1.0</span><span class="sxs-lookup"><span data-stu-id="a3c57-338">Profile changes in 2.1.0</span></span>

<span data-ttu-id="a3c57-339">**Handtrackingprofil**</span><span class="sxs-lookup"><span data-stu-id="a3c57-339">**Hand tracking profile**</span></span>

<span data-ttu-id="a3c57-340">Das Handgitter und die gemeinsamen Visualisierungen verfügen jetzt über separate Editor- und Playereinstellungen.</span><span class="sxs-lookup"><span data-stu-id="a3c57-340">The hand mesh and joint visualizations now have a separate editor and player settings.</span></span> <span data-ttu-id="a3c57-341">Das Handverfolgungsprofil wurde aktualisiert, um das Festlegen dieser Visualisierungen auf zu ermöglichen. Nothing, Everything, Editor oder Player.</span><span class="sxs-lookup"><span data-stu-id="a3c57-341">The hand tracking profile has been updated to allow for setting these visualizations to; Nothing, Everything, Editor or Player.</span></span>

![Handvisualisierungsmodi](../release-notes/images/HandTrackingVisualizationModes.png)

<span data-ttu-id="a3c57-343">Benutzerdefinierte Handverfolgungsprofile müssen möglicherweise aktualisiert werden, damit sie mit Version 2.1.0 ordnungsgemäß funktionieren.</span><span class="sxs-lookup"><span data-stu-id="a3c57-343">Custom hand tracking profiles may need to be updated to work correctly with version 2.1.0.</span></span>

>[!NOTE]
><span data-ttu-id="a3c57-344">Diese Änderung ist nicht abwärtskompatibel mit Version 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="a3c57-344">This change is not backwards compatible with version 2.0.0.</span></span>

<span data-ttu-id="a3c57-345">**Eingabesimulationsprofil**</span><span class="sxs-lookup"><span data-stu-id="a3c57-345">**Input simulation profile**</span></span>

<span data-ttu-id="a3c57-346">Das Eingabesimulationssystem wurde aktualisiert, wodurch einige Einstellungen im Eingabesimulationsprofil geändert werden.</span><span class="sxs-lookup"><span data-stu-id="a3c57-346">The input simulation system has been upgraded, which changes a few settings in the input simulation profile.</span></span> <span data-ttu-id="a3c57-347">Einige Änderungen können nicht automatisch migriert werden, und Benutzer stellen möglicherweise fest, dass Profile Standardwerte verwenden.</span><span class="sxs-lookup"><span data-stu-id="a3c57-347">Some changes can not be migrated automatically and users may find that profiles are using default values.</span></span>

1. <span data-ttu-id="a3c57-348">Alle KeyCode- und Maustastenbindungen im Profil wurden durch eine generische Struktur ersetzt, die den Typ der Bindung (Taste oder Maus) sowie den tatsächlichen Bindungscode (KeyCode oder Maustastennummer) `KeyBinding` speichert.</span><span class="sxs-lookup"><span data-stu-id="a3c57-348">All KeyCode and mouse button bindings in the profile have been replaced with a generic `KeyBinding` struct, which stores the type of binding (key or mouse) as well as the actual binding code (KeyCode or mouse button number respectively).</span></span> <span data-ttu-id="a3c57-349">Die Struktur verfügt über einen eigenen Inspektor, der eine einheitliche Anzeige ermöglicht, und bietet ein Tool zur automatischen Bindung, mit dem Tastenbindungen schnell festgelegt werden können, indem sie die entsprechende Taste drücken, anstatt aus einer großen Dropdownliste auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="a3c57-349">The struct has its own inspector, which allows unified display and offers an "auto-bind" tool to quickly set key bindings by pressing the respective key instead of selecting from a huge dropdown list.</span></span>

    - <span data-ttu-id="a3c57-350">FastControlKey</span><span class="sxs-lookup"><span data-stu-id="a3c57-350">FastControlKey</span></span>
    - <span data-ttu-id="a3c57-351">ToggleLeftHandKey</span><span class="sxs-lookup"><span data-stu-id="a3c57-351">ToggleLeftHandKey</span></span>
    - <span data-ttu-id="a3c57-352">ToggleRightHandKey</span><span class="sxs-lookup"><span data-stu-id="a3c57-352">ToggleRightHandKey</span></span>
    - <span data-ttu-id="a3c57-353">LeftHandManipulationKey</span><span class="sxs-lookup"><span data-stu-id="a3c57-353">LeftHandManipulationKey</span></span>
    - <span data-ttu-id="a3c57-354">RightHandManipulationKey</span><span class="sxs-lookup"><span data-stu-id="a3c57-354">RightHandManipulationKey</span></span>

1. <span data-ttu-id="a3c57-355">`MouseLookToggle` war zuvor in der `MouseLookButton` -Enum als `InputSimulationMouseButton.Focused` enthalten, jetzt ist es eine separate Option.</span><span class="sxs-lookup"><span data-stu-id="a3c57-355">`MouseLookToggle` was previously included in the `MouseLookButton` enum as `InputSimulationMouseButton.Focused`, it is now a separate option.</span></span> <span data-ttu-id="a3c57-356">Wenn diese Option aktiviert ist, wird die Kamera nach dem Loslassen der Schaltfläche weiter mit der Maus gedreht, bis die Escapetaste gedrückt wird.</span><span class="sxs-lookup"><span data-stu-id="a3c57-356">When enabled, the camera will keep rotating with the mouse after releasing the button, until the escape key is pressed.</span></span>
1. <span data-ttu-id="a3c57-357">`HandDepthMultiplier` Der Standardwert wurde von 0,1 auf 0,03 gesenkt, um einige Änderungen an der Eingabesimulation zu berücksichtigten.</span><span class="sxs-lookup"><span data-stu-id="a3c57-357">`HandDepthMultiplier` default value has been lowered from 0.1 to 0.03 to accommodate some changes to the input simulation.</span></span> <span data-ttu-id="a3c57-358">Wenn die Kamera beim Scrollen zu schnell bewegt wird, versuchen Sie, diesen Wert zu senken.</span><span class="sxs-lookup"><span data-stu-id="a3c57-358">If the camera moves too fast when scrolling, try lowering this value.</span></span>
1. <span data-ttu-id="a3c57-359">Schlüssel zum Drehen der Hände wurden entfernt. Die Handdrehung wird jetzt auch mit der Maus gesteuert.</span><span class="sxs-lookup"><span data-stu-id="a3c57-359">Keys for rotating hands have been removed, hand rotation is now controlled by the mouse as well.</span></span> <span data-ttu-id="a3c57-360">Wenn `HandRotateButton` Sie (STRG) zusammen mit der linken/rechten Manipulationstaste (LShift/Space) halten, wird die Handdrehung ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="a3c57-360">Holding `HandRotateButton` (Ctrl) together with the left/right hand manipulation key (LShift/Space) will enable hand rotation.</span></span>
1. <span data-ttu-id="a3c57-361">In der Eingabeachsenliste wurde eine neue Achse "UpDown" eingeführt.</span><span class="sxs-lookup"><span data-stu-id="a3c57-361">A new axis "UpDown" has been introduced to the input axis list.</span></span> <span data-ttu-id="a3c57-362">Dies steuert die Kamerabewegung in der vertikalen Und verwendet standardmäßig Q/E-Tasten sowie die Controllertriggertasten.</span><span class="sxs-lookup"><span data-stu-id="a3c57-362">This controls camera movement in the vertical and defaults to Q/E keys as well as the controller trigger buttons.</span></span>

<span data-ttu-id="a3c57-363">Weitere Informationen zu diesen Änderungen finden Sie im Artikel [zum Eingabesimulationsdienst.](../features/input-simulation/input-simulation-service.md)</span><span class="sxs-lookup"><span data-stu-id="a3c57-363">For more information on these changes, please see the [input simulation service](../features/input-simulation/input-simulation-service.md) article.</span></span>

<span data-ttu-id="a3c57-364">**Mausdatenanbieterprofil**</span><span class="sxs-lookup"><span data-stu-id="a3c57-364">**Mouse data provider profile**</span></span>

<span data-ttu-id="a3c57-365">Das Profil des Mausdatenanbieters wurde aktualisiert, um die neuen Eigenschaften und `CursorSpeed` `WheelSpeed` verfügbar zu machen.</span><span class="sxs-lookup"><span data-stu-id="a3c57-365">The mouse data provider profile has been updated to expose the new `CursorSpeed` and `WheelSpeed` properties.</span></span> <span data-ttu-id="a3c57-366">Für vorhandene benutzerdefinierte Profile werden automatisch Standardwerte bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="a3c57-366">Existing custom profiles will automatically have default values provided.</span></span> <span data-ttu-id="a3c57-367">Wenn das Profil gespeichert wird, werden diese neuen Werte beibehalten.</span><span class="sxs-lookup"><span data-stu-id="a3c57-367">When the profile is saved, these new values will be persisted.</span></span>

<span data-ttu-id="a3c57-368">**Controllerzuordnungsprofil**</span><span class="sxs-lookup"><span data-stu-id="a3c57-368">**Controller mapping profile**</span></span>

<span data-ttu-id="a3c57-369">Einige Achsen und Eingabetypen wurden in Version 2.1.0 aktualisiert, insbesondere im Bereich der OpenVR-Plattform.</span><span class="sxs-lookup"><span data-stu-id="a3c57-369">Some axes and input types have been updated in 2.1.0, especially around the OpenVR platform.</span></span> <span data-ttu-id="a3c57-370">Wählen Sie beim Upgrade **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** aus.</span><span class="sxs-lookup"><span data-stu-id="a3c57-370">Please be sure to select **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** when upgrading.</span></span> <span data-ttu-id="a3c57-371">Dadurch werden alle benutzerdefinierten Controllerzuordnungsprofile mit den aktualisierten Achsen und Daten aktualisiert, während Ihre benutzerdefinierten Eingabeaktionen intakt bleiben.</span><span class="sxs-lookup"><span data-stu-id="a3c57-371">This will update any custom Controller Mapping Profiles with the updated axes and data, while leaving your custom-assigned input actions intact.</span></span>

## <a name="updating-rc2-to-200"></a><span data-ttu-id="a3c57-372">Aktualisieren von RC2 auf 2.0.0</span><span class="sxs-lookup"><span data-stu-id="a3c57-372">Updating RC2 to 2.0.0</span></span>

<span data-ttu-id="a3c57-373">Zwischen rc2 und 2.0.0 des Microsoft Mixed Reality Toolkits wurden Änderungen vorgenommen, die sich auf vorhandene Projekte auswirken können.</span><span class="sxs-lookup"><span data-stu-id="a3c57-373">Between the RC2 and 2.0.0 releases of the Microsoft Mixed Reality Toolkit, changes were made that may impact existing projects.</span></span> <span data-ttu-id="a3c57-374">In diesem Dokument werden diese Änderungen und das Aktualisieren von Projekten auf das Release 2.0.0 beschrieben.</span><span class="sxs-lookup"><span data-stu-id="a3c57-374">This document describes those changes and how to update projects to the 2.0.0 release.</span></span>

- [<span data-ttu-id="a3c57-375">API-Änderungen</span><span class="sxs-lookup"><span data-stu-id="a3c57-375">API changes</span></span>](#api-changes-in-200)
- [<span data-ttu-id="a3c57-376">Änderungen am Assemblynamen</span><span class="sxs-lookup"><span data-stu-id="a3c57-376">Assembly name changes</span></span>](#assembly-name-changes-in-200)

### <a name="api-changes-in-200"></a><span data-ttu-id="a3c57-377">API-Änderungen in 2.0.0</span><span class="sxs-lookup"><span data-stu-id="a3c57-377">API changes in 2.0.0</span></span>

<span data-ttu-id="a3c57-378">Seit der Veröffentlichung von RC2 gab es eine Reihe von API-Änderungen, darunter einige, die vorhandene Projekte unter Umständen nicht mehr unterstützen.</span><span class="sxs-lookup"><span data-stu-id="a3c57-378">Since the release of RC2, there have been a number of API changes including some that may break existing projects.</span></span> <span data-ttu-id="a3c57-379">In den folgenden Abschnitten werden die Änderungen beschrieben, die zwischen den Releases RC2 und 2.0.0 aufgetreten sind.</span><span class="sxs-lookup"><span data-stu-id="a3c57-379">The following sections describe the changes that have occurred between the RC2 and 2.0.0 releases.</span></span>

<span data-ttu-id="a3c57-380">**MixedRealityToolkit**</span><span class="sxs-lookup"><span data-stu-id="a3c57-380">**MixedRealityToolkit**</span></span>

<span data-ttu-id="a3c57-381">Die folgenden öffentlichen Eigenschaften für das MixedRealityToolkit-Objekt sind veraltet.</span><span class="sxs-lookup"><span data-stu-id="a3c57-381">The following public properties on the MixedRealityToolkit object have been deprecated.</span></span>

- <span data-ttu-id="a3c57-382">`RegisteredMixedRealityServices` enthält nicht mehr die Auflistung registrierter Erweiterungsdienste und Datenanbieter.</span><span class="sxs-lookup"><span data-stu-id="a3c57-382">`RegisteredMixedRealityServices` no longer contains the collection of registered extensions services and data providers.</span></span>

<span data-ttu-id="a3c57-383">Verwenden Sie , um auf Erweiterungsdienste zu `MixedRealityServiceRegistry.TryGetService<T>` zugreifen.</span><span class="sxs-lookup"><span data-stu-id="a3c57-383">To access extension services, use `MixedRealityServiceRegistry.TryGetService<T>`.</span></span> <span data-ttu-id="a3c57-384">Um auf Datenanbieter zu zugreifen, casten Sie die Dienstinstanz in [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) , und verwenden Sie `GetDataProvider<T>` .</span><span class="sxs-lookup"><span data-stu-id="a3c57-384">To access data providers, cast the service instance to [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) and use `GetDataProvider<T>`.</span></span>

<span data-ttu-id="a3c57-385">Verwenden [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) Sie stattdessen oder für die folgenden [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) veralteten Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="a3c57-385">Use [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) or [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) instead for the following deprecated properties</span></span>

- `ActiveSystems`
- `InputSystem`
- `BoundarySystem`
- `CameraSystem`
- `SpatialAwarenessSystem`
- `TeleportSystem`
- `DiagnosticsSystem`
- `SceneSystem`

<span data-ttu-id="a3c57-386">**CoreServices**</span><span class="sxs-lookup"><span data-stu-id="a3c57-386">**CoreServices**</span></span>

<span data-ttu-id="a3c57-387">Die [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) -Klasse ist der Ersatz für die statischen Systemzugriffsoren (z. B. BoundarySystem), die im -Objekt gefunden `MixedRealityToolkit` werden.</span><span class="sxs-lookup"><span data-stu-id="a3c57-387">The [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) class is the replacement for the static system accessors (ex: BoundarySystem) found in the `MixedRealityToolkit` object.</span></span>

>[!IMPORTANT]
><span data-ttu-id="a3c57-388">Die `MixedRealityToolkit` Systemzugriffsoren sind in Version 2.0.0 veraltet und werden in einer zukünftigen Version des MRTK entfernt.</span><span class="sxs-lookup"><span data-stu-id="a3c57-388">The `MixedRealityToolkit` system accessors have been deprecated in version 2.0.0 and will be removed in a future release of the MRTK.</span></span>

<span data-ttu-id="a3c57-389">Das folgende Codebeispiel veranschaulicht das alte und das neue Muster.</span><span class="sxs-lookup"><span data-stu-id="a3c57-389">The following code example illustrates the old and the new pattern.</span></span>

``` c#
// Old
GameObject playAreaVisualization = MixedRealityToolkit.BoundarySystem?.GetPlayAreaVisualization();

// New
GameObject playAreaVisualization = CoreServices.BoundarySystem?.GetPlayAreaVisualization();
```

<span data-ttu-id="a3c57-390">Die Verwendung der neuen CoreSystem-Klasse stellt sicher, dass Ihr Anwendungscode nicht aktualisiert werden muss, wenn Sie die Anwendung so ändern, dass sie eine andere Dienstregistrierungsstelle verwendet (z. B. einer der experimentellen Dienst-Manager).</span><span class="sxs-lookup"><span data-stu-id="a3c57-390">Using the new CoreSystem class will ensure that your application code will not need updating if you change the application to use a different service registrar (ex: one of the experimental service managers).</span></span>

<span data-ttu-id="a3c57-391">**IMixedRealityRaycastProvider**</span><span class="sxs-lookup"><span data-stu-id="a3c57-391">**IMixedRealityRaycastProvider**</span></span>

<span data-ttu-id="a3c57-392">Mit dem Hinzufügen von IMixedRealityRaycastProvider wurde das Eingabesystemkonfigurationsprofil geändert.</span><span class="sxs-lookup"><span data-stu-id="a3c57-392">With the addition of the IMixedRealityRaycastProvider, the input system configuration profile was changed.</span></span> <span data-ttu-id="a3c57-393">Wenn Sie über ein benutzerdefiniertes Profil verfügen, erhalten Sie möglicherweise die Fehler in der folgenden Abbildung, wenn Sie Ihre Anwendung ausführen.</span><span class="sxs-lookup"><span data-stu-id="a3c57-393">If you have a custom profile, you may receive the errors in the following image when you run your application.</span></span>

![Auswählen des Raycast-Anbieters 1](../release-notes/images/UnableToRegisterRaycastProvider.png)

<span data-ttu-id="a3c57-395">Um diese Probleme zu beheben, fügen Sie Ihrem Eingabesystemprofil eine IMixedRealityRaycastProvider-Instanz hinzu.</span><span class="sxs-lookup"><span data-stu-id="a3c57-395">To fix these, please add an IMixedRealityRaycastProvider instance to your input system profile.</span></span>

![Auswählen des Raycast-Anbieters 2](../release-notes/images/SelectRaycastProvider.png)

<span data-ttu-id="a3c57-397">**Ereignissystem**</span><span class="sxs-lookup"><span data-stu-id="a3c57-397">**Event System**</span></span>

- <span data-ttu-id="a3c57-398">Die `IMixedRealityEventSystem` alten `Register` API-Methoden und wurden als veraltet `Unregister` markiert.</span><span class="sxs-lookup"><span data-stu-id="a3c57-398">The `IMixedRealityEventSystem` old API methods `Register` and `Unregister` have been marked as obsolete.</span></span> <span data-ttu-id="a3c57-399">Sie werden aus Gründen der Abwärtskompatibilität beibehalten.</span><span class="sxs-lookup"><span data-stu-id="a3c57-399">They are preserved for backwards compatibility.</span></span>
- <span data-ttu-id="a3c57-400">`InputSystemGlobalListener` wurde als veraltet markiert.</span><span class="sxs-lookup"><span data-stu-id="a3c57-400">`InputSystemGlobalListener` has been marked as obsolete.</span></span> <span data-ttu-id="a3c57-401">Seine Funktionalität hat sich nicht geändert.</span><span class="sxs-lookup"><span data-stu-id="a3c57-401">Its functionality has not changed.</span></span>
- <span data-ttu-id="a3c57-402">`BaseInputHandler` Die Basisklasse wurde von in `InputSystemGlobalListener` `InputSystemGlobalHandlerListener` geändert.</span><span class="sxs-lookup"><span data-stu-id="a3c57-402">`BaseInputHandler` base class has been changed from `InputSystemGlobalListener` to `InputSystemGlobalHandlerListener`.</span></span> <span data-ttu-id="a3c57-403">Dies ist eine breaking change für alle Nachfolger von `BaseInputHandler` .</span><span class="sxs-lookup"><span data-stu-id="a3c57-403">This is a breaking change for any descendants of `BaseInputHandler`.</span></span>

<span data-ttu-id="a3c57-404">**_Motivation hinter der Änderung_**</span><span class="sxs-lookup"><span data-stu-id="a3c57-404">**_Motivation behind the change_**</span></span>

<span data-ttu-id="a3c57-405">Die alte Ereignissystem-API und kann möglicherweise mehrere Probleme in der `Register` `Unregister` Laufzeit verursachen, hauptsächlich:</span><span class="sxs-lookup"><span data-stu-id="a3c57-405">The old event system API `Register` and `Unregister` could potentially cause multiple issues in runtime, main being:</span></span>

- <span data-ttu-id="a3c57-406">Wenn eine Komponente für globale Ereignisse registriert wird, würde sie globale Eingabeereignisse aller *Typen* empfangen.</span><span class="sxs-lookup"><span data-stu-id="a3c57-406">If a component registers for global events, it would receive global input events of *all* types.</span></span>
- <span data-ttu-id="a3c57-407">Wenn eine der Komponenten eines Objekts für globale Eingabeereignisse registriert wird, empfangen alle Komponenten in diesem Objekt globale Eingabeereignisse *aller* Typen.</span><span class="sxs-lookup"><span data-stu-id="a3c57-407">If one of the components on an object registers for global input events, all components on this object will receive global input events of *all* types.</span></span>
- <span data-ttu-id="a3c57-408">Wenn sich zwei Komponenten im gleichen Objekt für globale Ereignisse registrieren und dann eine komponente zur Laufzeit deaktiviert wird, empfängt die zweite keine globalen Ereignisse mehr.</span><span class="sxs-lookup"><span data-stu-id="a3c57-408">If two components on the same object register to global events, and then one is disabled in runtime, the second one stops receiving global events.</span></span>

<span data-ttu-id="a3c57-409">Neue API `RegisterHandler` und `UnregisterHandler` :</span><span class="sxs-lookup"><span data-stu-id="a3c57-409">New API `RegisterHandler` and `UnregisterHandler`:</span></span>

- <span data-ttu-id="a3c57-410">Bietet eine explizite und präzise Kontrolle darüber, auf welche Eingabeereignisse global und welche fokussiert sein sollen.</span><span class="sxs-lookup"><span data-stu-id="a3c57-410">Provides an explicit and granular control over which input events should be listened to globally and which should be focused-based.</span></span>
- <span data-ttu-id="a3c57-411">Ermöglicht mehreren Komponenten im gleichen Objekt, unabhängig voneinander auf globale Ereignisse zu lauschen.</span><span class="sxs-lookup"><span data-stu-id="a3c57-411">Allows multiple components on the same object to listen to global events independently on each other.</span></span>

<span data-ttu-id="a3c57-412">**_Migrieren_**</span><span class="sxs-lookup"><span data-stu-id="a3c57-412">**_How to migrate_**</span></span>

- <span data-ttu-id="a3c57-413">Wenn Sie die API bereits direkt `Register` / `Unregister` zuvor aufrufen, ersetzen Sie diese Aufrufe durch Aufrufe von `RegisterHandler` / `UnregisterHandler` .</span><span class="sxs-lookup"><span data-stu-id="a3c57-413">If you have been calling `Register`/`Unregister` API directly before, replace these calls with calls to `RegisterHandler`/`UnregisterHandler`.</span></span> <span data-ttu-id="a3c57-414">Verwenden Sie Handlerschnittstellen, die Sie als generische Parameter implementieren.</span><span class="sxs-lookup"><span data-stu-id="a3c57-414">Use handler interfaces you implement as generic parameters.</span></span> <span data-ttu-id="a3c57-415">Wenn Sie mehrere Schnittstellen implementieren und mehrere von ihnen auf globale Eingabeereignisse lauschen, rufen `RegisterHandler` Sie mehrmals auf.</span><span class="sxs-lookup"><span data-stu-id="a3c57-415">If you implement multiple interfaces, and several of them listen to global input events, call `RegisterHandler` multiple times.</span></span>
- <span data-ttu-id="a3c57-416">Wenn Sie von geerbt `InputSystemGlobalListener` haben, ändern Sie die Vererbung in `InputSystemGlobalHandlerListener` .</span><span class="sxs-lookup"><span data-stu-id="a3c57-416">If you have been inheriting from `InputSystemGlobalListener`, change inheritance to `InputSystemGlobalHandlerListener`.</span></span> <span data-ttu-id="a3c57-417">Implementieren `RegisterHandlers` und `UnregisterHandlers` abstrahieren Sie Methoden.</span><span class="sxs-lookup"><span data-stu-id="a3c57-417">Implement `RegisterHandlers` and `UnregisterHandlers` abstract methods.</span></span> <span data-ttu-id="a3c57-418">Im Implementierungsaufruf `inputSystem.RegisterHandler` ( ), um sich für alle `inputSystem.UnregisterHandler` Handlerschnittstellen zu registrieren, auf die Sie globale Ereignisse lauschen möchten.</span><span class="sxs-lookup"><span data-stu-id="a3c57-418">In the implementation call `inputSystem.RegisterHandler` (`inputSystem.UnregisterHandler`) to register on all handler interfaces you want to listen global events for.</span></span>
- <span data-ttu-id="a3c57-419">Wenn Sie von geerbt `BaseInputHandler` haben, implementieren Sie die abstrakten Methoden und `RegisterHandlers` `UnregisterHandlers` (wie für `InputSystemGlobalListener` ).</span><span class="sxs-lookup"><span data-stu-id="a3c57-419">If you have been inheriting from `BaseInputHandler`, implement `RegisterHandlers` and `UnregisterHandlers` abstract methods (same as for `InputSystemGlobalListener`).</span></span>

<span data-ttu-id="a3c57-420">**_Beispiele für die Migration_**</span><span class="sxs-lookup"><span data-stu-id="a3c57-420">**_Examples of migration_**</span></span>

```c#
// Old
class SampleHandler : MonoBehaviour, IMixedRealitySourceStateHandler, IMixedRealityHandJointHandler
{
    private void OnEnable()
    {
        InputSystem?.Register(gameObject);
    }

    private void OnDisable()
    {
        InputSystem?.Unregister(gameObject);
    }
}

// Migrated
class SampleHandler : MonoBehaviour, IMixedRealitySourceStateHandler, IMixedRealityHandJointHandler
{
    private void OnEnable()
    {
        InputSystem?.RegisterHandler<IMixedRealitySourceStateHandler>(this);
        InputSystem?.RegisterHandler<IMixedRealityHandJointHandler>(this);
    }

    private void OnDisable()
    {
        InputSystem?.UnregisterHandler<IMixedRealitySourceStateHandler>(this);
        InputSystem?.UnregisterHandler<IMixedRealityHandJointHandler>(this);
    }
}
```

```c#
// Old
class SampleHandler2 : InputSystemGlobalListener, IMixedRealitySpeechHandler
{
}

// Migrated
class SampleHandler2 : InputSystemGlobalHandlerListener, IMixedRealitySpeechHandler
{
    private void RegisterHandlers()
    {
        InputSystem?.RegisterHandler<IMixedRealitySpeechHandler>(this);
    }

    private void UnregisterHandlers()
    {
        InputSystem?.UnregisterHandler<IMixedRealitySpeechHandler>(this);
    }
}

// Alternative migration
class SampleHandler2 : MonoBehaviour, IMixedRealitySpeechHandler
{
    private void OnEnable()
    {
        IMixedRealityInputSystem inputSystem;
        if (MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
        {
            inputSystem?.RegisterHandler<IMixedRealitySpeechHandler>(this);
        }
    }

    private void OnDisable()
    {
        IMixedRealityInputSystem inputSystem;
        if (MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
        {
            inputSystem?.UnregisterHandler<IMixedRealitySpeechHandler>(this);
        }
    }
}
```

<span data-ttu-id="a3c57-421">**Räumliche Wahrnehmung**</span><span class="sxs-lookup"><span data-stu-id="a3c57-421">**Spatial Awareness**</span></span>

<span data-ttu-id="a3c57-422">Die Schnittstellen IMixedRealitySpatialAwarenessSystem und IMixedRealitySpatialAwarenessObserver haben wie unten beschrieben mehrere Breaking Changes vorgenommen.</span><span class="sxs-lookup"><span data-stu-id="a3c57-422">The IMixedRealitySpatialAwarenessSystem and IMixedRealitySpatialAwarenessObserver interfaces have taken multiple breaking changes as described below.</span></span>

<span data-ttu-id="a3c57-423">**_Änderungen_**</span><span class="sxs-lookup"><span data-stu-id="a3c57-423">**_Changes_**</span></span>

<span data-ttu-id="a3c57-424">Die folgenden Methoden wurden umbenannt, um ihre Verwendung besser zu beschreiben.</span><span class="sxs-lookup"><span data-stu-id="a3c57-424">The following method(s) have been renamed to better describe their usage.</span></span>

- <span data-ttu-id="a3c57-425">`IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` wurde in umbenannt, `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` um seine Verwendung zu verdeutlichen.</span><span class="sxs-lookup"><span data-stu-id="a3c57-425">`IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` has been renamed to `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` to clarify its usage.</span></span>

<span data-ttu-id="a3c57-426">**_Erweiterungen_**</span><span class="sxs-lookup"><span data-stu-id="a3c57-426">**_Additions_**</span></span>

<span data-ttu-id="a3c57-427">Basierend auf Kundenfeedback wurde Unterstützung für die einfache Entfernung zuvor beobachteter räumlicher Wahrnehmungsdaten hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="a3c57-427">Based on customer feedback, support for easy removal of previously observed spatial awareness data has been added.</span></span>

- `IMixedRealitySpatialAwarenessSystem.ClearObservations()`
- `IMixedRealitySpatialAwarenessSystem.ClearObservations<T>(string name)`
- `IMixedRealitySpatialAwarenessObserver.ClearObservations()`

<span data-ttu-id="a3c57-428">**Solver**</span><span class="sxs-lookup"><span data-stu-id="a3c57-428">**Solvers**</span></span>

<span data-ttu-id="a3c57-429">Einige Solverkomponenten und die SolverHandler-Manager-Klasse wurden geändert, um verschiedene Fehler zu beheben und eine intuitivere Verwendung zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="a3c57-429">Some solver components and the SolverHandler manager class has changed to fix various bugs and for more intuitive usage.</span></span>

<span data-ttu-id="a3c57-430">**_SolverHandler_**</span><span class="sxs-lookup"><span data-stu-id="a3c57-430">**_SolverHandler_**</span></span>

- <span data-ttu-id="a3c57-431">Die Klasse erweitert nicht mehr von `ControllerFinder`</span><span class="sxs-lookup"><span data-stu-id="a3c57-431">Class no longer extends from `ControllerFinder`</span></span>
- <span data-ttu-id="a3c57-432">`TrackedObjectToReference` öffentliche Eigenschaft veraltet und wurde in umbenannt. `TrackedTargetType`</span><span class="sxs-lookup"><span data-stu-id="a3c57-432">`TrackedObjectToReference` public property deprecated and has been renamed to `TrackedTargetType`</span></span>
- <span data-ttu-id="a3c57-433">`TrackedObjectType` veraltete werte & rechten Controller.</span><span class="sxs-lookup"><span data-stu-id="a3c57-433">`TrackedObjectType` deprecates left & right controller values.</span></span> <span data-ttu-id="a3c57-434">Verwenden Sie stattdessen `MotionController` - oder `HandJoint` -Werte, und aktualisieren Sie die neue `TrackedHandedness` Eigenschaft, um die Nachverfolgung auf den linken oder rechten Controller zu beschränken.</span><span class="sxs-lookup"><span data-stu-id="a3c57-434">Instead use `MotionController` or `HandJoint` values and update new `TrackedHandedness` property to limit tracking to left or right controller</span></span>

<span data-ttu-id="a3c57-435">**_Dazwischen_**</span><span class="sxs-lookup"><span data-stu-id="a3c57-435">**_InBetween_**</span></span>

- <span data-ttu-id="a3c57-436">`TrackedObjectForSecondTransform` öffentliche Eigenschaft veraltet und wurde in umbenannt. `SecondTrackedObjectType`</span><span class="sxs-lookup"><span data-stu-id="a3c57-436">`TrackedObjectForSecondTransform` public property deprecated and has been renamed to `SecondTrackedObjectType`</span></span>
- <span data-ttu-id="a3c57-437">`AttachSecondTransformToNewTrackedObject()` wurde entfernt.</span><span class="sxs-lookup"><span data-stu-id="a3c57-437">`AttachSecondTransformToNewTrackedObject()` has been removed.</span></span> <span data-ttu-id="a3c57-438">Um den Solver zu aktualisieren, ändern Sie die öffentlichen Eigenschaften (d. h.</span><span class="sxs-lookup"><span data-stu-id="a3c57-438">To update the solver, modify the public properties (i.e</span></span> <span data-ttu-id="a3c57-439">`SecondTrackedObjectType`)</span><span class="sxs-lookup"><span data-stu-id="a3c57-439">`SecondTrackedObjectType`)</span></span>

<span data-ttu-id="a3c57-440">**_SurfaceMatism_**</span><span class="sxs-lookup"><span data-stu-id="a3c57-440">**_SurfaceMagnetism_**</span></span>

- <span data-ttu-id="a3c57-441">`MaxDistance` öffentliche Eigenschaft veraltet und wurde in umbenannt. `MaxRaycastDistance`</span><span class="sxs-lookup"><span data-stu-id="a3c57-441">`MaxDistance` public property deprecated and has been renamed to `MaxRaycastDistance`</span></span>
- <span data-ttu-id="a3c57-442">`CloseDistance` öffentliche Eigenschaft veraltet und wurde in umbenannt. `ClosestDistance`</span><span class="sxs-lookup"><span data-stu-id="a3c57-442">`CloseDistance` public property deprecated and has been renamed to `ClosestDistance`</span></span>
- <span data-ttu-id="a3c57-443">Der Standardwert für `RaycastDirectionMode` ist `TrackedTargetForward` jetzt, welche Raycasts in Richtung der nachverfolgten Zieltransformation vorwärts gehen.</span><span class="sxs-lookup"><span data-stu-id="a3c57-443">Default value for `RaycastDirectionMode` is now `TrackedTargetForward` which raycasts in the direction of the tracked target transform forward</span></span>
- <span data-ttu-id="a3c57-444">`OrientationMode` -Enum-Werte `Vertical` und `Full` wurden in `TrackedTarget` `SurfaceNormal` bzw. umbenannt.</span><span class="sxs-lookup"><span data-stu-id="a3c57-444">`OrientationMode` enum values, `Vertical` and `Full`, have been renamed to `TrackedTarget` and `SurfaceNormal` respectively</span></span>
- <span data-ttu-id="a3c57-445">`KeepOrientationVertical` Die öffentliche Eigenschaft wurde hinzugefügt, um zu steuern, ob die Ausrichtung des zugeordneten GameObject vertikal bleibt.</span><span class="sxs-lookup"><span data-stu-id="a3c57-445">`KeepOrientationVertical` public property has been added to control whether orientation of associated GameObject remains vertical</span></span>

<span data-ttu-id="a3c57-446">**Schaltflächen**</span><span class="sxs-lookup"><span data-stu-id="a3c57-446">**Buttons**</span></span>

- <span data-ttu-id="a3c57-447">[`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) die `DistanceSpaceMode` -Eigenschaft ist jetzt als `Local` Standard festgelegt.</span><span class="sxs-lookup"><span data-stu-id="a3c57-447">[`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) now has `DistanceSpaceMode` property set to `Local` as default.</span></span> <span data-ttu-id="a3c57-448">Dadurch können Schaltflächen skaliert werden, während sie weiterhin gedrückt werden können.</span><span class="sxs-lookup"><span data-stu-id="a3c57-448">This allows buttons to be scaled while still be pressable</span></span>

<span data-ttu-id="a3c57-449">**Clipping Sphere**</span><span class="sxs-lookup"><span data-stu-id="a3c57-449">**Clipping Sphere**</span></span>

<span data-ttu-id="a3c57-450">Die ClippingSphere-Schnittstelle wurde geändert, um die APIs in ClippingBox und ClippingPlane zu spiegeln.</span><span class="sxs-lookup"><span data-stu-id="a3c57-450">The ClippingSphere interface has changed to mirror the APIs found in the ClippingBox and ClippingPlane.</span></span>

<span data-ttu-id="a3c57-451">Die Radius-Eigenschaft von ClippingSphere wird jetzt implizit basierend auf der Transformationsskala berechnet.</span><span class="sxs-lookup"><span data-stu-id="a3c57-451">The ClippingSphere's Radius property is now implicitly calculated based on the transform scale.</span></span> <span data-ttu-id="a3c57-452">Bevor Entwickler den Radius von ClippingSphere im Inspektor angeben müssen.</span><span class="sxs-lookup"><span data-stu-id="a3c57-452">Before developers would have to specify the radius of the ClippingSphere in the inspector.</span></span> <span data-ttu-id="a3c57-453">Wenn Sie den Radius ändern möchten, aktualisieren Sie einfach die Transformationsskala der Transformation wie gewohnt.</span><span class="sxs-lookup"><span data-stu-id="a3c57-453">If you want to change the radius, just update the transform scale of the transform as you normally would.</span></span>

<span data-ttu-id="a3c57-454">**NearInteractionTouchable und PokePointer**</span><span class="sxs-lookup"><span data-stu-id="a3c57-454">**NearInteractionTouchable and PokePointer**</span></span>

- <span data-ttu-id="a3c57-455">NearInteractionTouchable verarbeitet unity ui canvas touching nicht mehr.</span><span class="sxs-lookup"><span data-stu-id="a3c57-455">NearInteractionTouchable does not handle Unity UI canvas touching any longer.</span></span> <span data-ttu-id="a3c57-456">Die NearInteractionTouchableUnityUI-Klasse muss jetzt für Benutzeroberflächenelemente von Unity verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a3c57-456">The NearInteractionTouchableUnityUI class must be used for Unity UI touchables now.</span></span>
- <span data-ttu-id="a3c57-457">ColliderNearInteractionTouchable ist die neue Basisklasse für Touchables, die auf Collidern basiert, d. h. jede berührbare Klasse mit Ausnahme von NearInteractionTouchableUnityUI.</span><span class="sxs-lookup"><span data-stu-id="a3c57-457">ColliderNearInteractionTouchable is the new base class for touchables based on colliders, i.e. every touchable except NearInteractionTouchableUnityUI.</span></span>
- <span data-ttu-id="a3c57-458">BaseNearInteractionTouchable.DistFront wurde verschoben und in PokePointer.TouchableDistance umbenannt. Dies ist die Entfernung, und der PokePointer kann mit touchables interagieren.</span><span class="sxs-lookup"><span data-stu-id="a3c57-458">BaseNearInteractionTouchable.DistFront has been moved and renamed to PokePointer.TouchableDistance This is the distance and which the PokePointer can interact with touchables.</span></span> <span data-ttu-id="a3c57-459">Zuvor hatte jedes berührbare -System einen eigenen maximalen Interaktionsabstand, aber jetzt ist dies im PokePointer definiert, was eine bessere Optimierung ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="a3c57-459">Previously each touchable had its own maximum interaction distance, but now this is defined in the PokePointer which allows better optimization.</span></span>
- <span data-ttu-id="a3c57-460">BaseNearInteractionTouchable.DistBack wurde in PokeThreshold umbenannt. Dadurch wird deutlich, dass PokeThreshold das Gegenstück zu DebounceThreshold ist.</span><span class="sxs-lookup"><span data-stu-id="a3c57-460">BaseNearInteractionTouchable.DistBack has been renamed to PokeThreshold This makes it clear that PokeThreshold is the counterpart to DebounceThreshold.</span></span> <span data-ttu-id="a3c57-461">Ein berührbares wird aktiviert, wenn der PokeThreshold überschritten wird, und wird freigegeben, wenn DebounceThreshold überschritten wird.</span><span class="sxs-lookup"><span data-stu-id="a3c57-461">A touchable is activated when the PokeThreshold is crossed, and released when DebounceThreshold is crossed.</span></span>

<span data-ttu-id="a3c57-462">**ReadOnlyAttribute**</span><span class="sxs-lookup"><span data-stu-id="a3c57-462">**ReadOnlyAttribute**</span></span>

<span data-ttu-id="a3c57-463">Der `Microsoft.MixedReality.Toolkit` -Namespace wurde , `ReadOnlyAttribute` und `BeginReadOnlyGroupAttribute` `EndReadOnlyGroupAttribute` hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="a3c57-463">The `Microsoft.MixedReality.Toolkit` namespace has been added to `ReadOnlyAttribute`, `BeginReadOnlyGroupAttribute`, and `EndReadOnlyGroupAttribute`.</span></span>

<span data-ttu-id="a3c57-464">**PointerClickHandler**</span><span class="sxs-lookup"><span data-stu-id="a3c57-464">**PointerClickHandler**</span></span>

<span data-ttu-id="a3c57-465">Die `PointerClickHandler`-Klasse ist veraltet.</span><span class="sxs-lookup"><span data-stu-id="a3c57-465">The `PointerClickHandler` class has been deprecated.</span></span> <span data-ttu-id="a3c57-466">Stattdessen `PointerHandler` sollte verwendet werden, es bietet die gleiche Funktionalität.</span><span class="sxs-lookup"><span data-stu-id="a3c57-466">The `PointerHandler` should be used instead, it provides the same functionality.</span></span>

<span data-ttu-id="a3c57-467">**HoloLens-Clicker-Unterstützung**</span><span class="sxs-lookup"><span data-stu-id="a3c57-467">**HoloLens clicker support**</span></span>

<span data-ttu-id="a3c57-468">Die HoloLens-Zuordnungen des Clickers haben sich von einer nicht behandelten zu einer nicht [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) behandelten [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand) geändert.</span><span class="sxs-lookup"><span data-stu-id="a3c57-468">The HoloLens clicker's controller mappings have changed from being an unhanded [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) to being an unhanded [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand).</span></span> <span data-ttu-id="a3c57-469">Um dies zu berücksichtigen, wird ein automatisches Updater ausgeführt, wenn Sie Ihr ControllerMapping-Profil zum ersten Mal öffnen.</span><span class="sxs-lookup"><span data-stu-id="a3c57-469">To account for this, an automatic updater will run the first time you open your ControllerMapping profile.</span></span> <span data-ttu-id="a3c57-470">Öffnen Sie nach dem Upgrade auf 2.0.0 mindestens einmal benutzerdefinierte Profile, um diesen einmaligen Migrationsschritt auszulösen.</span><span class="sxs-lookup"><span data-stu-id="a3c57-470">Please open any custom profiles at least once after upgrading to 2.0.0 in order to trigger this one-time migration step.</span></span>

<span data-ttu-id="a3c57-471">**InteractableHighlight**</span><span class="sxs-lookup"><span data-stu-id="a3c57-471">**InteractableHighlight**</span></span>

<span data-ttu-id="a3c57-472">Die `InteractableHighlight`-Klasse ist veraltet.</span><span class="sxs-lookup"><span data-stu-id="a3c57-472">The `InteractableHighlight` class has been deprecated.</span></span> <span data-ttu-id="a3c57-473">Stattdessen `InteractableOnFocus` sollten die Klasse und das Asset verwendet `FocusInteractableStates` werden.</span><span class="sxs-lookup"><span data-stu-id="a3c57-473">The `InteractableOnFocus` class and `FocusInteractableStates` asset should be used instead.</span></span> <span data-ttu-id="a3c57-474">Um ein neues Asset für zu erstellen, klicken Sie mit der rechten Maustaste in das Projektfenster, und wählen `Theme` `InteractableOnFocus` Sie *Create* Mixed Reality Toolkit Interactable Theme (Interagierbares Design des  >    >  *Toolkits*  >  *erstellen) aus.*</span><span class="sxs-lookup"><span data-stu-id="a3c57-474">To create a new `Theme` asset for the `InteractableOnFocus`, right click in the project window and select *Create* > *Mixed Reality Toolkit* > *Interactable* > *Theme*.</span></span>

<span data-ttu-id="a3c57-475">**HandInteractionPanZoom**</span><span class="sxs-lookup"><span data-stu-id="a3c57-475">**HandInteractionPanZoom**</span></span>

<span data-ttu-id="a3c57-476">`HandInteractionPanZoom` wurde in den Benutzeroberflächennamespace verschoben, da es sich nicht um eine Eingabekomponente war.</span><span class="sxs-lookup"><span data-stu-id="a3c57-476">`HandInteractionPanZoom` has been moved to the UI namespace as it was not an input component.</span></span> <span data-ttu-id="a3c57-477">`HandPanEventData` wurde auch in diesen Namespace verschoben und vereinfacht, um anderen Benutzeroberflächenereignisdaten zu entsprechen.</span><span class="sxs-lookup"><span data-stu-id="a3c57-477">`HandPanEventData` has also been moved into this namespace, and simplified to correspond with other UI event data.</span></span>

### <a name="assembly-name-changes-in-200"></a><span data-ttu-id="a3c57-478">Änderungen an Assemblynamen in 2.0.0</span><span class="sxs-lookup"><span data-stu-id="a3c57-478">Assembly name changes in 2.0.0</span></span>

<span data-ttu-id="a3c57-479">In Release 2.0.0 wurden alle offiziellen Assemblynamen des Mixed Reality Toolkits und die zugehörigen Assemblydefinitionsdateien (ASMDEF)-Dateien aktualisiert, damit sie dem folgenden Muster entsprechen.</span><span class="sxs-lookup"><span data-stu-id="a3c57-479">In The 2.0.0 release, all of the official Mixed Reality Toolkit assembly names and their associated assembly definition (.asmdef) files have been updated to fit the following pattern.</span></span>

```c#
Microsoft.MixedReality.Toolkit[.<name>]
```

<span data-ttu-id="a3c57-480">In einigen Fällen wurden mehrere Assemblys zusammengeführt, um eine bessere Einheitlichkeit ihres Inhalts zu schaffen.</span><span class="sxs-lookup"><span data-stu-id="a3c57-480">In some instances, multiple assemblies have been merged to create better unity of their contents.</span></span> <span data-ttu-id="a3c57-481">Wenn Ihr Projekt benutzerdefinierte ASMDEF-Dateien verwendet, müssen sie möglicherweise aktualisiert werden.</span><span class="sxs-lookup"><span data-stu-id="a3c57-481">If your project uses custom .asmdef files, they may require updating.</span></span>

<span data-ttu-id="a3c57-482">In den folgenden Tabellen wird beschrieben, wie die RC2-ASMDEF-Dateinamen dem Release 2.0.0 zuordnen.</span><span class="sxs-lookup"><span data-stu-id="a3c57-482">The following tables describe how the RC2 .asmdef file names map to the 2.0.0 release.</span></span> <span data-ttu-id="a3c57-483">Alle Assemblynamen übereinstimmen mit dem Namen der ASMDEF-Datei.</span><span class="sxs-lookup"><span data-stu-id="a3c57-483">All assembly names match the .asmdef file name.</span></span>

<span data-ttu-id="a3c57-484">**MixedRealityToolkit**</span><span class="sxs-lookup"><span data-stu-id="a3c57-484">**MixedRealityToolkit**</span></span>

| <span data-ttu-id="a3c57-485">RC2</span><span class="sxs-lookup"><span data-stu-id="a3c57-485">RC2</span></span> | <span data-ttu-id="a3c57-486">2.0.0</span><span class="sxs-lookup"><span data-stu-id="a3c57-486">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="a3c57-487">MixedRealityToolkit.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-487">MixedRealityToolkit.asmdef</span></span> | <span data-ttu-id="a3c57-488">Microsoft.MixedReality.Toolkit.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-488">Microsoft.MixedReality.Toolkit.asmdef</span></span> |
| <span data-ttu-id="a3c57-489">MixedRealityToolkit.Core.BuildAndDeploy.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-489">MixedRealityToolkit.Core.BuildAndDeploy.asmdef</span></span> | <span data-ttu-id="a3c57-490">Microsoft.MixedReality.Toolkit.Editor.BuildAndDeploy.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-490">Microsoft.MixedReality.Toolkit.Editor.BuildAndDeploy.asmdef</span></span> |
| <span data-ttu-id="a3c57-491">MixedRealityToolkit.Core.Definitions.Utilities.Editor.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-491">MixedRealityToolkit.Core.Definitions.Utilities.Editor.asmdef</span></span> | <span data-ttu-id="a3c57-492">Entfernt, Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef verwenden</span><span class="sxs-lookup"><span data-stu-id="a3c57-492">Removed, use Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef</span></span> |
| <span data-ttu-id="a3c57-493">MixedRealityToolkit.Core.Extensions.EditorClassExtensions.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-493">MixedRealityToolkit.Core.Extensions.EditorClassExtensions.asmdef</span></span> | <span data-ttu-id="a3c57-494">Microsoft.MixedReality.Toolkit.Editor.ClassExtensions.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-494">Microsoft.MixedReality.Toolkit.Editor.ClassExtensions.asmdef</span></span>
| <span data-ttu-id="a3c57-495">MixedRealityToolkit.Core.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-495">MixedRealityToolkit.Core.Inspectors.asmdef</span></span> | <span data-ttu-id="a3c57-496">Microsoft.MixedReality.Toolkit.Editor.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-496">Microsoft.MixedReality.Toolkit.Editor.Inspectors.asmdef</span></span> |
| <span data-ttu-id="a3c57-497">MixedRealityToolkit.Core.Inspectors.ServiceInspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-497">MixedRealityToolkit.Core.Inspectors.ServiceInspectors.asmdef</span></span> | <span data-ttu-id="a3c57-498">Microsoft.MixedReality.Toolkit.Editor.ServiceInspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-498">Microsoft.MixedReality.Toolkit.Editor.ServiceInspectors.asmdef</span></span> |
| <span data-ttu-id="a3c57-499">MixedRealityToolkit.Core.UtilitiesAsync.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-499">MixedRealityToolkit.Core.UtilitiesAsync.asmdef</span></span> | <span data-ttu-id="a3c57-500">Microsoft.MixedReality.Toolkit.Async.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-500">Microsoft.MixedReality.Toolkit.Async.asmdef</span></span> |
| <span data-ttu-id="a3c57-501">MixedRealityToolkit.Core.Utilities.Editor.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-501">MixedRealityToolkit.Core.Utilities.Editor.asmdef</span></span> | <span data-ttu-id="a3c57-502">Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-502">Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef</span></span> |
| <span data-ttu-id="a3c57-503">MixedRealityToolkit.Utilities.Gltf.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-503">MixedRealityToolkit.Utilities.Gltf.asmdef</span></span> | <span data-ttu-id="a3c57-504">Microsoft.MixedReality.Toolkit.Gltf.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-504">Microsoft.MixedReality.Toolkit.Gltf.asmdef</span></span> |
| <span data-ttu-id="a3c57-505">MixedRealityToolkit.Utilities.Gltf.Importers.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-505">MixedRealityToolkit.Utilities.Gltf.Importers.asmdef</span></span> | <span data-ttu-id="a3c57-506">Microsoft.MixedReality.Toolkit.Gltf.Importers.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-506">Microsoft.MixedReality.Toolkit.Gltf.Importers.asmdef</span></span> |

<span data-ttu-id="a3c57-507">**MixedRealityToolkit.Providers**</span><span class="sxs-lookup"><span data-stu-id="a3c57-507">**MixedRealityToolkit.Providers**</span></span>

| <span data-ttu-id="a3c57-508">RC2</span><span class="sxs-lookup"><span data-stu-id="a3c57-508">RC2</span></span> | <span data-ttu-id="a3c57-509">2.0.0</span><span class="sxs-lookup"><span data-stu-id="a3c57-509">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="a3c57-510">MixedRealityToolkit.Providers.OpenVR.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-510">MixedRealityToolkit.Providers.OpenVR.asmdef</span></span> | <span data-ttu-id="a3c57-511">Microsoft.MixedReality.Toolkit.Providers.OpenVR.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-511">Microsoft.MixedReality.Toolkit.Providers.OpenVR.asmdef</span></span> |
| <span data-ttu-id="a3c57-512">MixedRealityToolkit.Providers.WindowsMixedReality.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-512">MixedRealityToolkit.Providers.WindowsMixedReality.asmdef</span></span> | <span data-ttu-id="a3c57-513">Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-513">Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality.asmdef</span></span> |
| <span data-ttu-id="a3c57-514">MixedRealityToolkit.Providers.WindowsVoiceInput.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-514">MixedRealityToolkit.Providers.WindowsVoiceInput.asmdef</span></span> | <span data-ttu-id="a3c57-515">Microsoft.MixedReality.Toolkit.Providers.WindowsVoiceInput.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-515">Microsoft.MixedReality.Toolkit.Providers.WindowsVoiceInput.asmdef</span></span> |

<span data-ttu-id="a3c57-516">**MixedRealityToolkit.Services**</span><span class="sxs-lookup"><span data-stu-id="a3c57-516">**MixedRealityToolkit.Services**</span></span>

| <span data-ttu-id="a3c57-517">RC2</span><span class="sxs-lookup"><span data-stu-id="a3c57-517">RC2</span></span> | <span data-ttu-id="a3c57-518">2.0.0</span><span class="sxs-lookup"><span data-stu-id="a3c57-518">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="a3c57-519">MixedRealityToolkit.Services.BoundarySystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-519">MixedRealityToolkit.Services.BoundarySystem.asmdef</span></span> | <span data-ttu-id="a3c57-520">Microsoft.MixedReality.Toolkit.Services.BoundarySystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-520">Microsoft.MixedReality.Toolkit.Services.BoundarySystem.asmdef</span></span> |
| <span data-ttu-id="a3c57-521">MixedRealityToolkit.Services.CameraSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-521">MixedRealityToolkit.Services.CameraSystem.asmdef</span></span> | <span data-ttu-id="a3c57-522">Microsoft.MixedReality.Toolkit.Services.CameraSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-522">Microsoft.MixedReality.Toolkit.Services.CameraSystem.asmdef</span></span> |
| <span data-ttu-id="a3c57-523">MixedRealityToolkit.Services.DiagnosticsSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-523">MixedRealityToolkit.Services.DiagnosticsSystem.asmdef</span></span> | <span data-ttu-id="a3c57-524">Microsoft.MixedReality.Toolkit.Services.DiagnosticsSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-524">Microsoft.MixedReality.Toolkit.Services.DiagnosticsSystem.asmdef</span></span> |
| <span data-ttu-id="a3c57-525">MixedRealityToolkit.Services.InputSimulation.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-525">MixedRealityToolkit.Services.InputSimulation.asmdef</span></span> | <span data-ttu-id="a3c57-526">Microsoft.MixedReality.Toolkit.Services.InputSimulation.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-526">Microsoft.MixedReality.Toolkit.Services.InputSimulation.asmdef</span></span> |
| <span data-ttu-id="a3c57-527">MixedRealityToolkit.Services.InputSimulation.Editor.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-527">MixedRealityToolkit.Services.InputSimulation.Editor.asmdef</span></span> | <span data-ttu-id="a3c57-528">Microsoft.MixedReality.Toolkit.Services.InputSimulation.Editor.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-528">Microsoft.MixedReality.Toolkit.Services.InputSimulation.Editor.asmdef</span></span> |
| <span data-ttu-id="a3c57-529">MixedRealityToolkit.Services.InputSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-529">MixedRealityToolkit.Services.InputSystem.asmdef</span></span> | <span data-ttu-id="a3c57-530">Microsoft.MixedReality.Toolkit.Services.InputSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-530">Microsoft.MixedReality.Toolkit.Services.InputSystem.asmdef</span></span> |
| <span data-ttu-id="a3c57-531">MixedRealityToolkit.Services.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-531">MixedRealityToolkit.Services.Inspectors.asmdef</span></span> | <span data-ttu-id="a3c57-532">Microsoft.MixedReality.Toolkit.Services.InputSystem.Editor.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-532">Microsoft.MixedReality.Toolkit.Services.InputSystem.Editor.asmdef</span></span> |
| <span data-ttu-id="a3c57-533">MixedRealityToolkit.Services.SceneSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-533">MixedRealityToolkit.Services.SceneSystem.asmdef</span></span> | <span data-ttu-id="a3c57-534">Microsoft.MixedReality.Toolkit.Services.SceneSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-534">Microsoft.MixedReality.Toolkit.Services.SceneSystem.asmdef</span></span> |
| <span data-ttu-id="a3c57-535">MixedRealityToolkit.Services.SpatialAwarenessSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-535">MixedRealityToolkit.Services.SpatialAwarenessSystem.asmdef</span></span> | <span data-ttu-id="a3c57-536">Microsoft.MixedReality.Toolkit.Services.SpatialAwarenessSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-536">Microsoft.MixedReality.Toolkit.Services.SpatialAwarenessSystem.asmdef</span></span> |
| <span data-ttu-id="a3c57-537">MixedRealityToolkit.Services.TeleportSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-537">MixedRealityToolkit.Services.TeleportSystem.asmdef</span></span> | <span data-ttu-id="a3c57-538">Microsoft.MixedReality.Toolkit.Services.TeleportSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-538">Microsoft.MixedReality.Toolkit.Services.TeleportSystem.asmdef</span></span> |

<span data-ttu-id="a3c57-539">**MixedRealityToolkit.SDK**</span><span class="sxs-lookup"><span data-stu-id="a3c57-539">**MixedRealityToolkit.SDK**</span></span>

| <span data-ttu-id="a3c57-540">RC2</span><span class="sxs-lookup"><span data-stu-id="a3c57-540">RC2</span></span> | <span data-ttu-id="a3c57-541">2.0.0</span><span class="sxs-lookup"><span data-stu-id="a3c57-541">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="a3c57-542">MixedRealityToolkit.SDK.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-542">MixedRealityToolkit.SDK.asmdef</span></span> | <span data-ttu-id="a3c57-543">Microsoft.MixedReality.Toolkit.SDK.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-543">Microsoft.MixedReality.Toolkit.SDK.asmdef</span></span> |
| <span data-ttu-id="a3c57-544">MixedRealityToolkit.SDK.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-544">MixedRealityToolkit.SDK.Inspectors.asmdef</span></span> | <span data-ttu-id="a3c57-545">Microsoft.MixedReality.Toolkit.SDK.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-545">Microsoft.MixedReality.Toolkit.SDK.Inspectors.asmdef</span></span> |

<span data-ttu-id="a3c57-546">**MixedRealityToolkit.Examples**</span><span class="sxs-lookup"><span data-stu-id="a3c57-546">**MixedRealityToolkit.Examples**</span></span>

| <span data-ttu-id="a3c57-547">RC2</span><span class="sxs-lookup"><span data-stu-id="a3c57-547">RC2</span></span> | <span data-ttu-id="a3c57-548">2.0.0</span><span class="sxs-lookup"><span data-stu-id="a3c57-548">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="a3c57-549">MixedRealityToolkit.Examples.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-549">MixedRealityToolkit.Examples.asmdef</span></span> | <span data-ttu-id="a3c57-550">Microsoft.MixedReality.Toolkit.Examples.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-550">Microsoft.MixedReality.Toolkit.Examples.asmdef</span></span> |
| <span data-ttu-id="a3c57-551">MixedRealityToolkit.Examples.Demos.Gltf.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-551">MixedRealityToolkit.Examples.Demos.Gltf.asmdef</span></span> | <span data-ttu-id="a3c57-552">Microsoft.MixedReality.Toolkit.Demos.Gltf.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-552">Microsoft.MixedReality.Toolkit.Demos.Gltf.asmdef</span></span> |
| <span data-ttu-id="a3c57-553">MixedRealityToolkit.Examples.Demos.StandardShader.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-553">MixedRealityToolkit.Examples.Demos.StandardShader.Inspectors.asmdef</span></span> | <span data-ttu-id="a3c57-554">Microsoft.MixedReality.Toolkit.Demos.StandardShader.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-554">Microsoft.MixedReality.Toolkit.Demos.StandardShader.Inspectors.asmdef</span></span> |
| <span data-ttu-id="a3c57-555">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-555">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.asmdef</span></span> | <span data-ttu-id="a3c57-556">Microsoft.MixedReality.Toolkit.Demos.InspectorFields.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-556">Microsoft.MixedReality.Toolkit.Demos.InspectorFields.asmdef</span></span> |
| <span data-ttu-id="a3c57-557">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-557">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.Inspectors.asmdef</span></span> | <span data-ttu-id="a3c57-558">Microsoft.MixedReality.Toolkit.Demos.InspectorFields.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-558">Microsoft.MixedReality.Toolkit.Demos.InspectorFields.Inspectors.asmdef</span></span> |
| <span data-ttu-id="a3c57-559">MixedRealityToolkit.Examples.Demos.UX.Interactables.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-559">MixedRealityToolkit.Examples.Demos.UX.Interactables.asmdef</span></span> | <span data-ttu-id="a3c57-560">Microsoft.MixedReality.Toolkit.Demos.UX.Interactables.asmdef</span><span class="sxs-lookup"><span data-stu-id="a3c57-560">Microsoft.MixedReality.Toolkit.Demos.UX.Interactables.asmdef</span></span> |
