---
title: Willkommen beim Mixed Reality-Featuretool
description: Lernen Sie die Grundlagen des MR-Featuretools für die HoloLens- und VR-Entwicklung kennen.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: Aktuell, Tools, Erste Schritte, Grundlagen, Unity, Visual Studio, Toolkit, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Installation, Windows, HoloLens, Emulator, Unreal, OpenXR
ms.openlocfilehash: 4e822f2dda2a314ce06bc394a4d92b1aa6953af3
ms.sourcegitcommit: 943489923c69c3a28bc152f1cb516dcdcea2880a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2021
ms.locfileid: "111772413"
---
# <a name="welcome-to-the-mixed-reality-feature-tool"></a><span data-ttu-id="9a1ee-104">Willkommen beim Mixed Reality-Featuretool</span><span class="sxs-lookup"><span data-stu-id="9a1ee-104">Welcome to the Mixed Reality Feature Tool</span></span>

![Mixed Reality-Featuretool-Bannerbild](images/feature-tool-banner.png)

> [!IMPORTANT]
> <span data-ttu-id="9a1ee-106">Das Mixed Reality-Featuretool ist zurzeit nur für Unity verfügbar.</span><span class="sxs-lookup"><span data-stu-id="9a1ee-106">The Mixed Reality Feature Tool is only available for Unity at the moment.</span></span> <span data-ttu-id="9a1ee-107">Wenn Sie in Unreal entwickeln, finden Sie weitere Informationen in der Dokumentation zur [Toolinstallation](../install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="9a1ee-107">If you're developing in Unreal, refer to the [tools installation](../install-the-tools.md) documentation.</span></span>

<span data-ttu-id="9a1ee-108">Das Mixed Reality-Featuretool ist eine neue Möglichkeit für Entwickler, Mixed Reality-Featurepakete in Unity-Projekten zu ermitteln, zu aktualisieren und hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="9a1ee-108">The Mixed Reality Feature Tool is a new way for developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="9a1ee-109">Sie können Pakete vor dem Importieren nach Name oder Kategorie durchsuchen, ihre Abhängigkeiten anzeigen und sogar Änderungsvorschläge für Ihre Projektmanifestdatei anzeigen.</span><span class="sxs-lookup"><span data-stu-id="9a1ee-109">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="9a1ee-110">Für den Fall dass Sie noch nie mit einer Manifestdatei gearbeitet haben: Es handelt sich um eine JSON-Datei, die alle Ihre Projektpakete enthält.</span><span class="sxs-lookup"><span data-stu-id="9a1ee-110">If you've never worked with a manifest file before, it's a JSON file containing all your projects packages.</span></span> <span data-ttu-id="9a1ee-111">Nachdem Sie die gewünschten Pakete überprüft haben, lädt das Mixed Reality-Featuretool sie in das Projekt Ihrer Wahl herunter.</span><span class="sxs-lookup"><span data-stu-id="9a1ee-111">Once you've validated the packages you want, the Mixed Reality Feature tool will download them into the project of your choice.</span></span>

## <a name="system-requirements"></a><span data-ttu-id="9a1ee-112">Systemanforderungen</span><span class="sxs-lookup"><span data-stu-id="9a1ee-112">System requirements</span></span>

<span data-ttu-id="9a1ee-113">Damit Sie das Mixed Reality-Featuretool ausführen können, benötigen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="9a1ee-113">Before you can run the Mixed Reality Feature Tool, you'll need:</span></span>

* [<span data-ttu-id="9a1ee-114">.NET 5.0 Runtime</span><span class="sxs-lookup"><span data-stu-id="9a1ee-114">.NET 5.0 runtime</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
* [<span data-ttu-id="9a1ee-115">Windows 10</span><span class="sxs-lookup"><span data-stu-id="9a1ee-115">Windows 10</span></span>](https://www.microsoft.com/software-download/windows10ISO)

> [!NOTE]
> <span data-ttu-id="9a1ee-116">Das Mixed Reality-Featuretool kann zurzeit nur unter Windows ausgeführt werden, MacOS-Unterstützung wird aber in Kürze verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="9a1ee-116">The Mixed Reality Feature Tool currently only runs on Windows, but MacOS support is coming soon!</span></span>

## <a name="download"></a><span data-ttu-id="9a1ee-117">Download</span><span class="sxs-lookup"><span data-stu-id="9a1ee-117">Download</span></span>

<span data-ttu-id="9a1ee-118">Nachdem Sie Ihre Umgebung eingerichtet haben:</span><span class="sxs-lookup"><span data-stu-id="9a1ee-118">Once you have your environment set up:</span></span>

* <span data-ttu-id="9a1ee-119">[Laden Sie die neueste Version des Mixed Reality-Featuretools](https://aka.ms/MRFeatureTool) aus dem Microsoft Download Center herunter.</span><span class="sxs-lookup"><span data-stu-id="9a1ee-119">[Download the latest version of the Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool) from the Microsoft Download Center.</span></span>
* <span data-ttu-id="9a1ee-120">Wenn der Download abgeschlossen ist, entpacken Sie die Datei, und speichern Sie sie auf Ihrem Desktop.</span><span class="sxs-lookup"><span data-stu-id="9a1ee-120">When the download completes, unzip the file and save it to your desktop</span></span>
    * <span data-ttu-id="9a1ee-121">Es empfiehlt sich, für den schnelleren Zugriff eine Verknüpfung zur ausführbaren Datei zu erstellen</span><span class="sxs-lookup"><span data-stu-id="9a1ee-121">We recommend creating a shortcut to the executable file for faster access</span></span>

> [!NOTE]
> <span data-ttu-id="9a1ee-122">Wenn Sie noch keine Erfahrung mit der Verwendung des Unity-Paket-Managers haben, befolgen Sie unsere [UPM-Anweisungen](/windows/mixed-reality/mrtk-unity/configuration/usingupm#managing-mixed-reality-features-with-the-unity-package-manager).</span><span class="sxs-lookup"><span data-stu-id="9a1ee-122">If you're new to using the Unity Package Manager, follow our [UPM instructions](/windows/mixed-reality/mrtk-unity/configuration/usingupm#managing-mixed-reality-features-with-the-unity-package-manager).</span></span>

## <a name="changes-in-this-release"></a><span data-ttu-id="9a1ee-123">Änderungen in diesem Release</span><span class="sxs-lookup"><span data-stu-id="9a1ee-123">Changes in this release</span></span>

<span data-ttu-id="9a1ee-124">Version 1.0.2103 Beta enthält die folgenden Fehlerkorrekturen:</span><span class="sxs-lookup"><span data-stu-id="9a1ee-124">Version 1.0.2103 Beta includes the following fixes:</span></span>

* <span data-ttu-id="9a1ee-125">Verbesserungen bei der Erkennung von Downloadfehlern.</span><span class="sxs-lookup"><span data-stu-id="9a1ee-125">Improvements to download error detection.</span></span>
* <span data-ttu-id="9a1ee-126">Aktualisierungen an der Art, in der Manifeste geschrieben werden, um Fehler bei der korrekten Aktualisierung zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="9a1ee-126">Updates on how manifests are written to avoid failure to update correctly.</span></span>
* <span data-ttu-id="9a1ee-127">Die Verwendung von Escapezeichen wurde aus Dateipfaden im Projektmanifest entfernt.</span><span class="sxs-lookup"><span data-stu-id="9a1ee-127">Escpaing has been removed from file paths in the project manifest.</span></span>

<span data-ttu-id="9a1ee-128">Dieses Release wurde um die folgenden Features erweitert:</span><span class="sxs-lookup"><span data-stu-id="9a1ee-128">The following features have been added in this release:</span></span>

* <span data-ttu-id="9a1ee-129">Der Featurekatalog wird jetzt zwischengespeichert.</span><span class="sxs-lookup"><span data-stu-id="9a1ee-129">The feature catalog is now cached.</span></span> <span data-ttu-id="9a1ee-130">Um nach neuen Features und Updates zu suchen, verwenden Sie die Schaltfläche „Aktualisieren“ in „Discovery“ (Ermittlung).</span><span class="sxs-lookup"><span data-stu-id="9a1ee-130">To check for new features and updates, please use the refresh button in Discovery.</span></span>
* <span data-ttu-id="9a1ee-131">Die Projektauswahl wurde aus dem Importschritt vor die Ermittlung verschoben.</span><span class="sxs-lookup"><span data-stu-id="9a1ee-131">Move project selection from the Import step to before Discovery.</span></span>
* <span data-ttu-id="9a1ee-132">Verfügbare Pakete werden nach der angegebenen Unity-Version des Projekts gefiltert.</span><span class="sxs-lookup"><span data-stu-id="9a1ee-132">Available packages are filtered by the project's specified Unity version.</span></span>
* <span data-ttu-id="9a1ee-133">In der Ermittlungsansicht werden jetzt die aktuell installierten Pakete angezeigt.</span><span class="sxs-lookup"><span data-stu-id="9a1ee-133">The discovery view now displays currently installed packages.</span></span>

## <a name="1-getting-started"></a><span data-ttu-id="9a1ee-134">1. Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="9a1ee-134">1. Getting started</span></span>

<span data-ttu-id="9a1ee-135">Starten Sie das Mixed Reality-Featuretool aus der ausführbaren Datei, das beim ersten Start die Startseite anzeigt:</span><span class="sxs-lookup"><span data-stu-id="9a1ee-135">Launch the Mixed Reality Feature Tool from the executable file, which displays the start page on first launch:</span></span>

![Erste Schritte](images/FeatureToolStart.png)

<span data-ttu-id="9a1ee-137">Auf der Startseite können Sie Folgendes ausführen:</span><span class="sxs-lookup"><span data-stu-id="9a1ee-137">From the start page, you can:</span></span>

* <span data-ttu-id="9a1ee-138">[Konfigurieren](configuring-feature-tool.md) der Tooleinstellungen mithilfe der Schaltfläche mit dem **Zahnradsymbol**</span><span class="sxs-lookup"><span data-stu-id="9a1ee-138">[Configure](configuring-feature-tool.md) tool settings using the **gear icon** button</span></span>
* <span data-ttu-id="9a1ee-139">Verwenden der Schaltfläche mit dem **Fragezeichen** zum Starten des Webbrowsers und Anzeigen unserer Dokumentation</span><span class="sxs-lookup"><span data-stu-id="9a1ee-139">Use the **question mark** button to launch the default web browser and display our documentation</span></span>
* <span data-ttu-id="9a1ee-140">Auswähle von **Start**, um mit dem Ermitteln von Featurepaketen zu beginnen</span><span class="sxs-lookup"><span data-stu-id="9a1ee-140">Select **Start** to begin discovering feature packages</span></span>

## <a name="2-selecting-your-unity-project"></a><span data-ttu-id="9a1ee-141">2. Auswählen Ihres Unity-Projekts</span><span class="sxs-lookup"><span data-stu-id="9a1ee-141">2. Selecting your Unity project</span></span>

<span data-ttu-id="9a1ee-142">Um sicherzustellen, dass alle ermittelten Features in der Unity-Version Ihres Projekts unterstützt werden, besteht der erste Schritt darin, das Mixed Reality-Featuretool mithilfe der Schaltfläche mit den **Auslassungszeichen** (rechts neben dem Feld „Projektpfad“) auf Ihr Projekt zu verweisen.</span><span class="sxs-lookup"><span data-stu-id="9a1ee-142">To ensure that all discovered features are supported on your project's version of Unity, the fist step is to point the Mixed Reality Feature Tool to your project using the **ellipsis** button (to the right of the project path field).</span></span>

![Auswählen des Unity-Projekts](images/FeatureToolSelectUnityProject.png)

> [!NOTE]
> <span data-ttu-id="9a1ee-144">Das Dialogfeld, das angezeigt wird, wenn Sie das Dateisystem nach dem Unity-Projektordner durchsuchen, enthält '_' als den Dateinamen.</span><span class="sxs-lookup"><span data-stu-id="9a1ee-144">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="9a1ee-145">Es muss ein Wert für den Dateinamen vorhanden sein, um die Auswahl des Ordners zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="9a1ee-145">There must be a value for the file name to enable the folder to be selected.</span></span>

<span data-ttu-id="9a1ee-146">Wenn Sie den Ordner Ihres Projekts gefunden haben, klicken Sie auf die Schaltfläche „Öffnen“, um zum Mixed Reality-Featuretool zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="9a1ee-146">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9a1ee-147">Das Mixed Reality-Featuretool führt eine Überprüfung durch, um sicherzustellen, dass die Weiterleitung an einen Unity-Projektordner erfolgt.</span><span class="sxs-lookup"><span data-stu-id="9a1ee-147">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="9a1ee-148">Der Ordner muss die Ordner `Assets`, `Packages` und `Project Settings` enthalten.</span><span class="sxs-lookup"><span data-stu-id="9a1ee-148">The folder must contain `Assets`, `Packages` and `Project Settings` folders.</span></span>

## <a name="3-discovering-and-acquiring-feature-packages"></a><span data-ttu-id="9a1ee-149">3. Ermitteln und Erwerben von Featurepaketen</span><span class="sxs-lookup"><span data-stu-id="9a1ee-149">3. Discovering and acquiring feature packages</span></span>

> [!NOTE]
> <span data-ttu-id="9a1ee-150">Version 1.0.2103 Beta speichert jetzt den Inhalt des Featurekatalogs zwischen, wenn auf den Server zugegriffen wird.</span><span class="sxs-lookup"><span data-stu-id="9a1ee-150">Version 1.0.2103 Beta now caches the feature catalog contents whenever the server is accessed.</span></span> <span data-ttu-id="9a1ee-151">Diese Änderung ermöglicht den schnellen Zugriff auf verfügbare Features auf Kosten der Anzeige der absolut neuesten Daten.</span><span class="sxs-lookup"><span data-stu-id="9a1ee-151">This change enables fast access to available features, at the expense of displaying the absolute latest data.</span></span> <span data-ttu-id="9a1ee-152">Verwenden Sie zum Aktualisieren des Katalogs die Schaltfläche **Aktualisieren**.</span><span class="sxs-lookup"><span data-stu-id="9a1ee-152">To update the catalog, please use the **Refresh** button.</span></span>

<span data-ttu-id="9a1ee-153">Die Features sind zur besseren Orientierung nach Kategorien gruppiert.</span><span class="sxs-lookup"><span data-stu-id="9a1ee-153">Features are grouped by category to make things easier to find.</span></span> <span data-ttu-id="9a1ee-154">Beispielsweise weist die **Mixed Reality-Toolkit**-Kategorie mehrere Features auf, unter denen Sie wählen können:</span><span class="sxs-lookup"><span data-stu-id="9a1ee-154">For example, the **Mixed Reality Toolkit** category has several features for you to choose from:</span></span>

![Ermittlung und Erwerb](images/FeatureToolDiscovery.png)

<span data-ttu-id="9a1ee-156">Wenn das Mixed Reality-Featuretool zuvor importierte Features erkennt, zeigt es für jedes eine Benachrichtigung an.</span><span class="sxs-lookup"><span data-stu-id="9a1ee-156">When the Mixed Reality Feature Tool recognizes previously imported feature(s), it displays a notification message by each.</span></span>

![Benachrichtigung über importiertes Features](images/feature-tool-imported-note.png)


<span data-ttu-id="9a1ee-158">Sobald Sie Ihre Wahl getroffen haben, wählen Sie **Get features** (Features abrufen) aus, um alle benötigten Pakete aus dem Katalog abzurufen.</span><span class="sxs-lookup"><span data-stu-id="9a1ee-158">Once you've made your choices, select **Get features** to fetch all the required packages from the catalog.</span></span> <span data-ttu-id="9a1ee-159">Weitere Informationen finden Sie unter [discovering and acquiring features](discovering-features.md) (Ermitteln und Erwerben von Features).</span><span class="sxs-lookup"><span data-stu-id="9a1ee-159">For more information, please see [discovering and acquiring features](discovering-features.md).</span></span>

## <a name="4-importing-feature-packages"></a><span data-ttu-id="9a1ee-160">4. Importieren von Featurepaketen</span><span class="sxs-lookup"><span data-stu-id="9a1ee-160">4. Importing feature packages</span></span>

<span data-ttu-id="9a1ee-161">Nach dem Erwerb wird der gesamte Satz von Paketen zusammen mit einer Liste der erforderlichen Abhängigkeiten angezeigt.</span><span class="sxs-lookup"><span data-stu-id="9a1ee-161">Following acquisition, the complete set of packages is presented, along with a list of required dependencies.</span></span> <span data-ttu-id="9a1ee-162">Wenn Sie die Auswahl eines Features oder Pakets ändern müssen, ist dies der richtige Zeitpunkt:</span><span class="sxs-lookup"><span data-stu-id="9a1ee-162">If you need to change any feature or package selections, this is the time:</span></span>

![Importieren von Paketen](images/FeatureToolImport.png)

<span data-ttu-id="9a1ee-164">Wir empfehlen dringend, die Schaltfläche **Validate** (Überprüfen) zu verwenden, um sicherzustellen, dass das Unity-Projekt die ausgewählten Features erfolgreich importieren kann.</span><span class="sxs-lookup"><span data-stu-id="9a1ee-164">We highly recommend using the **Validate** button to ensure the Unity project can successfully import the selected features.</span></span> <span data-ttu-id="9a1ee-165">Nach der Überprüfung wird ein Popupdialogfeld mit einer Erfolgsmeldung oder einer Liste der identifizierten Probleme angezeigt.</span><span class="sxs-lookup"><span data-stu-id="9a1ee-165">After validation, you'll see a pop-up dialog with a success message or a list of identified issues.</span></span>

<span data-ttu-id="9a1ee-166">Wählen Sie **Importieren** aus, um fortzufahren.</span><span class="sxs-lookup"><span data-stu-id="9a1ee-166">Select **Import** to continue.</span></span>

> [!NOTE]
> <span data-ttu-id="9a1ee-167">Sollten nach dem Klicken auf die Schaltfläche **Import** noch Probleme bestehen, wird eine einfache Meldung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="9a1ee-167">After clicking the **Import** button, if any issues remain a simple message will be displayed.</span></span> <span data-ttu-id="9a1ee-168">Es wird empfohlen, auf „Nein“ zu klicken und die Schaltfläche **Validate** (Überprüfen) zu verwenden, um die Probleme anzuzeigen und zu beheben.</span><span class="sxs-lookup"><span data-stu-id="9a1ee-168">The recommendation is to click No and to use the **Validate** button to view and resolve the issues.</span></span>

<span data-ttu-id="9a1ee-169">Weitere Informationen finden Sie unter [Importieren von Features](importing-features.md).</span><span class="sxs-lookup"><span data-stu-id="9a1ee-169">For more information, please see [importing features](importing-features.md).</span></span>

## <a name="5-reviewing-and-approving-project-changes"></a><span data-ttu-id="9a1ee-170">5. Überprüfen und Genehmigen von Projektänderungen</span><span class="sxs-lookup"><span data-stu-id="9a1ee-170">5. Reviewing and approving project changes</span></span>

<span data-ttu-id="9a1ee-171">Der letzte Schritt besteht im Überprüfen und Genehmigen der vorgeschlagenen Änderungen an den Manifest- und Projektdateien:</span><span class="sxs-lookup"><span data-stu-id="9a1ee-171">The final step is reviewing and approving the proposed changes to the manifest and project files:</span></span>

* <span data-ttu-id="9a1ee-172">Die vorgeschlagenen Änderungen am Manifest werden auf der linken Seite angezeigt</span><span class="sxs-lookup"><span data-stu-id="9a1ee-172">The proposed changes to the manifest are displayed on the left</span></span>
* <span data-ttu-id="9a1ee-173">Die Dateien, die dem Projekt hinzugefügt werden sollen, werden auf der rechten Seite angezeigt</span><span class="sxs-lookup"><span data-stu-id="9a1ee-173">The files to be added to the project are listed to the right</span></span>
* <span data-ttu-id="9a1ee-174">Mit der Schaltfläche **Compare** (Vergleichen) können Sie das aktuelle Manifest und die vorgeschlagenen Änderungen nebeneinander anzeigen</span><span class="sxs-lookup"><span data-stu-id="9a1ee-174">The **Compare** button allows for side by side viewing of the current manifest and the proposed changes</span></span>

![Authorization](images/FeatureToolApprovalRequest.png)

<span data-ttu-id="9a1ee-176">Weitere Informationen finden Sie unter [Überprüfen und Genehmigen von Projektänderungen](reviewing-changes.md).</span><span class="sxs-lookup"><span data-stu-id="9a1ee-176">For more information, see [reviewing and approving project modifications](reviewing-changes.md).</span></span>

## <a name="6-project-updated"></a><span data-ttu-id="9a1ee-177">6. Projekt aktualisiert</span><span class="sxs-lookup"><span data-stu-id="9a1ee-177">6. Project updated</span></span>

<span data-ttu-id="9a1ee-178">Wenn die vorgeschlagenen Änderungen genehmigt wurden, wird Ihr Unity-Zielprojekt so aktualisiert, dass es auf die ausgewählten Mixed Reality-Features verweist.</span><span class="sxs-lookup"><span data-stu-id="9a1ee-178">When the proposed changes are approved, your target Unity project is updated to reference the selected Mixed Reality features.</span></span>

![Projekt aktualisiert](images/FeatureToolProjectUpdated.png)

<span data-ttu-id="9a1ee-180">Der Ordner **Packages** (Pakete) des Unity-Projekts enthält jetzt einen Unterordner **MixedReality** mit den Dateien der Featurepakete, und das Manifest enthält die entsprechenden Verweise.</span><span class="sxs-lookup"><span data-stu-id="9a1ee-180">The Unity project's **Packages** folder now has a **MixedReality** subfolder with the feature package file(s) and the manifest will contain the appropriate reference(s).</span></span>

<span data-ttu-id="9a1ee-181">Kehren Sie zu Unity zurück, warten Sie auf das Laden der neu ausgewählten Features, und beginnen Sie mit dem Erstellen!</span><span class="sxs-lookup"><span data-stu-id="9a1ee-181">Return to Unity, wait for the new selected features to load, and start building!</span></span>

## <a name="see-also"></a><span data-ttu-id="9a1ee-182">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="9a1ee-182">See also</span></span>

- [<span data-ttu-id="9a1ee-183">Konfigurieren des Featuretools</span><span class="sxs-lookup"><span data-stu-id="9a1ee-183">Configuring the feature tool</span></span>](configuring-feature-tool.md)
- [<span data-ttu-id="9a1ee-184">Ermittlung und Erwerb</span><span class="sxs-lookup"><span data-stu-id="9a1ee-184">Discovery and acquisition</span></span>](discovering-features.md)
- [<span data-ttu-id="9a1ee-185">Anzeigen von Details zu Featurepaketen</span><span class="sxs-lookup"><span data-stu-id="9a1ee-185">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="9a1ee-186">Importieren ausgewählter Pakete</span><span class="sxs-lookup"><span data-stu-id="9a1ee-186">Importing selected packages</span></span>](importing-features.md)
- [<span data-ttu-id="9a1ee-187">Überprüfen und Genehmigen von Projektänderungen</span><span class="sxs-lookup"><span data-stu-id="9a1ee-187">Reviewing and approving project modifications</span></span>](reviewing-changes.md)