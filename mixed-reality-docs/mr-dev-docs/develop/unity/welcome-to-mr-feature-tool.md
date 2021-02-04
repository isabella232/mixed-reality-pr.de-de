---
title: Willkommen beim Mixed Reality-Featuretool
description: Lernen Sie die Grundlagen des MR-Featuretools für die HoloLens- und VR-Entwicklung kennen.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: Aktuell, Tools, Erste Schritte, Grundlagen, Unity, Visual Studio, Toolkit, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Installation, Windows, HoloLens, Emulator, Unreal, OpenXR
ms.openlocfilehash: b9d54edb251cfe22d4f5fbea6fa8c923f6ff2d69
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2021
ms.locfileid: "99243956"
---
# <a name="welcome-to-the-mixed-reality-feature-tool"></a><span data-ttu-id="4c83d-104">Willkommen beim Mixed Reality-Featuretool</span><span class="sxs-lookup"><span data-stu-id="4c83d-104">Welcome to the Mixed Reality Feature Tool</span></span>

![Mixed Reality-Featuretool-Bannerbild](images/feature-tool-banner.png)

> [!IMPORTANT]
> <span data-ttu-id="4c83d-106">Das Mixed Reality-Featuretool ist zurzeit nur für Unity verfügbar.</span><span class="sxs-lookup"><span data-stu-id="4c83d-106">The Mixed Reality Feature Tool is only available for Unity at the moment.</span></span> <span data-ttu-id="4c83d-107">Wenn Sie in Unreal entwickeln, finden Sie weitere Informationen in der Dokumentation zur [Toolinstallation](../install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="4c83d-107">If you're developing in Unreal, refer to the [tools installation](../install-the-tools.md) documentation.</span></span>

<span data-ttu-id="4c83d-108">Das Mixed Reality-Featuretool ist eine neue Möglichkeit für Entwickler, Mixed Reality-Featurepakete in Unity-Projekten zu ermitteln, zu aktualisieren und hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="4c83d-108">The Mixed Reality Feature Tool is a new way for developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="4c83d-109">Sie können Pakete vor dem Importieren nach Name oder Kategorie durchsuchen, ihre Abhängigkeiten anzeigen und sogar Änderungsvorschläge für Ihre Projektmanifestdatei anzeigen.</span><span class="sxs-lookup"><span data-stu-id="4c83d-109">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="4c83d-110">Für den Fall dass Sie noch nie mit einer Manifestdatei gearbeitet haben: Es handelt sich um eine JSON-Datei, die alle Ihre Projektpakete enthält.</span><span class="sxs-lookup"><span data-stu-id="4c83d-110">If you've never worked with a manifest file before, it's a JSON file containing all your projects packages.</span></span> <span data-ttu-id="4c83d-111">Nachdem Sie die gewünschten Pakete überprüft haben, lädt das Mixed Reality-Featuretool sie in das Projekt Ihrer Wahl herunter.</span><span class="sxs-lookup"><span data-stu-id="4c83d-111">Once you've validated the packages you want, the Mixed Reality Feature tool will download them into the project of your choice.</span></span>

## <a name="system-requirements"></a><span data-ttu-id="4c83d-112">Systemanforderungen</span><span class="sxs-lookup"><span data-stu-id="4c83d-112">System requirements</span></span>

<span data-ttu-id="4c83d-113">Damit Sie das Mixed Reality-Featuretool ausführen können, benötigen Sie Folgendes:</span><span class="sxs-lookup"><span data-stu-id="4c83d-113">Before you can run the Mixed Reality Feature Tool, you'll need:</span></span>

* [<span data-ttu-id="4c83d-114">.NET 5.0 Runtime</span><span class="sxs-lookup"><span data-stu-id="4c83d-114">.NET 5.0 runtime</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
* [<span data-ttu-id="4c83d-115">Windows 10</span><span class="sxs-lookup"><span data-stu-id="4c83d-115">Windows 10</span></span>](https://www.microsoft.com/software-download/windows10ISO)

> [!NOTE]
> <span data-ttu-id="4c83d-116">Das Mixed Reality-Featuretool kann zurzeit nur unter Windows ausgeführt werden, MacOS-Unterstützung wird aber in Kürze verfügbar sein.</span><span class="sxs-lookup"><span data-stu-id="4c83d-116">The Mixed Reality Feature Tool currently only runs on Windows, but MacOS support is coming soon!</span></span>

<span data-ttu-id="4c83d-117">Nachdem Sie Ihre Umgebung eingerichtet haben:</span><span class="sxs-lookup"><span data-stu-id="4c83d-117">Once you have your environment set up:</span></span>

* <span data-ttu-id="4c83d-118">Laden Sie die neueste Version des Mixed Reality-Featuretools aus dem [Microsoft Download Center](https://aka.ms/MRFeatureTool) herunter.</span><span class="sxs-lookup"><span data-stu-id="4c83d-118">Download the latest version of the Mixed Reality Feature Tool from the [Microsoft Download Center](https://aka.ms/MRFeatureTool).</span></span>
* <span data-ttu-id="4c83d-119">Wenn der Download abgeschlossen ist, entpacken Sie die Datei, und speichern Sie sie auf Ihrem Desktop.</span><span class="sxs-lookup"><span data-stu-id="4c83d-119">When the download completes, unzip the file and save it to your desktop</span></span>
    * <span data-ttu-id="4c83d-120">Es empfiehlt sich, für den schnelleren Zugriff eine Verknüpfung zur ausführbaren Datei zu erstellen</span><span class="sxs-lookup"><span data-stu-id="4c83d-120">We recommend creating a shortcut to the executable file for faster access</span></span>

## <a name="1-getting-started"></a><span data-ttu-id="4c83d-121">1. Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="4c83d-121">1. Getting started</span></span>

<span data-ttu-id="4c83d-122">Starten Sie das Mixed Reality-Featuretool aus der ausführbaren Datei, das beim ersten Start die Startseite anzeigt:</span><span class="sxs-lookup"><span data-stu-id="4c83d-122">Launch the Mixed Reality Feature Tool from the executable file, which displays the start page on first launch:</span></span>

![Erste Schritte](images/FeatureToolStart.png)

<span data-ttu-id="4c83d-124">Auf der Startseite können Sie Folgendes ausführen:</span><span class="sxs-lookup"><span data-stu-id="4c83d-124">From the start page, you can:</span></span>

* <span data-ttu-id="4c83d-125">[Konfigurieren](configuring-feature-tool.md) der Tooleinstellungen mithilfe der Schaltfläche mit dem **Zahnradsymbol**</span><span class="sxs-lookup"><span data-stu-id="4c83d-125">[Configure](configuring-feature-tool.md) tool settings using the **gear icon** button</span></span>
* <span data-ttu-id="4c83d-126">Verwenden der Schaltfläche mit dem **Fragezeichen** zum Starten des Webbrowsers und Anzeigen unserer Dokumentation</span><span class="sxs-lookup"><span data-stu-id="4c83d-126">Use the **question mark** button to launch the default web browser and display our documentation</span></span>
* <span data-ttu-id="4c83d-127">Auswähle von **Start**, um mit dem Ermitteln von Featurepaketen zu beginnen</span><span class="sxs-lookup"><span data-stu-id="4c83d-127">Select **Start** to begin discovering feature packages</span></span>

## <a name="2-discovering-and-acquiring-feature-packages"></a><span data-ttu-id="4c83d-128">2. Ermitteln und Erwerben von Featurepaketen</span><span class="sxs-lookup"><span data-stu-id="4c83d-128">2. Discovering and acquiring feature packages</span></span>

<span data-ttu-id="4c83d-129">Der Katalog der Featurepakete wird abgerufen, sobald Sie auf „Start“ klicken.</span><span class="sxs-lookup"><span data-stu-id="4c83d-129">The feature package catalog is retrieved as soon as you press Start.</span></span> <span data-ttu-id="4c83d-130">Die Features sind zur besseren Orientierung nach Kategorien gruppiert.</span><span class="sxs-lookup"><span data-stu-id="4c83d-130">Features are grouped by category to make things easier to find.</span></span> <span data-ttu-id="4c83d-131">Beispielsweise weist die **Mixed Reality-Toolkit**-Kategorie mehrere Features auf, unter denen Sie wählen können:</span><span class="sxs-lookup"><span data-stu-id="4c83d-131">For example, the **Mixed Reality Toolkit** category has several features for you to choose from:</span></span>

![Ermittlung und Erwerb](images/FeatureToolDiscovery.png)

<span data-ttu-id="4c83d-133">Sobald Sie Ihre Wahl getroffen haben, wählen Sie **Get features** (Features abrufen) aus, um alle benötigten Pakete aus dem Katalog abzurufen.</span><span class="sxs-lookup"><span data-stu-id="4c83d-133">Once you've made your choices, select **Get features** to fetch all the required packages from the catalog.</span></span> <span data-ttu-id="4c83d-134">Weitere Informationen finden Sie unter [discovering and acquiring features](discovering-features.md) (Ermitteln und Erwerben von Features).</span><span class="sxs-lookup"><span data-stu-id="4c83d-134">For more information, please see [discovering and acquiring features](discovering-features.md).</span></span>

## <a name="3-importing-feature-packages"></a><span data-ttu-id="4c83d-135">3. Importieren von Featurepaketen</span><span class="sxs-lookup"><span data-stu-id="4c83d-135">3. Importing feature packages</span></span>

<span data-ttu-id="4c83d-136">Nach dem Erwerb wird der gesamte Satz von Paketen zusammen mit einer Liste der erforderlichen Abhängigkeiten angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4c83d-136">Following acquisition, the complete set of packages is presented, along with a list of required dependencies.</span></span> <span data-ttu-id="4c83d-137">Wenn Sie die Auswahl eines Features oder Pakets ändern müssen, ist dies der richtige Zeitpunkt:</span><span class="sxs-lookup"><span data-stu-id="4c83d-137">If you need to change any feature or package selections, this is the time:</span></span>

![Importieren von Paketen](images/FeatureToolImport.png)

<span data-ttu-id="4c83d-139">Wir empfehlen dringend, die Schaltfläche **Validate** (Überprüfen) zu verwenden, um sicherzustellen, dass das Unity-Projekt die ausgewählten Features erfolgreich importieren kann.</span><span class="sxs-lookup"><span data-stu-id="4c83d-139">We highly recommend using the **Validate** button to ensure the Unity project can successfully import the selected features.</span></span> <span data-ttu-id="4c83d-140">Nach der Überprüfung wird ein Popupdialogfeld mit einer Erfolgsmeldung oder einer Liste der identifizierten Probleme angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4c83d-140">After validation, you'll see a pop-up dialog with a success message or a list of identified issues.</span></span>

<span data-ttu-id="4c83d-141">Ferner müssen Sie vor dem Importieren noch den Speicherort des Unity-Zielprojekts festlegen.</span><span class="sxs-lookup"><span data-stu-id="4c83d-141">You also need to set the location of the target Unity project before you import.</span></span> <span data-ttu-id="4c83d-142">Verwenden Sie die Schaltfläche mit dem **Auslassungszeichen** auf der linken Seite des Projektpfadfelds zum Durchsuchen.</span><span class="sxs-lookup"><span data-stu-id="4c83d-142">Use the **ellipsis** button to the left of the project path field to browse.</span></span> <span data-ttu-id="4c83d-143">Wenn Sie die Navigation in Ihrem Dateisystem abgeschlossen haben, öffnen Sie den Ordner, der Ihr Unity-Zielprojekt enthält.</span><span class="sxs-lookup"><span data-stu-id="4c83d-143">When you're done navigating your file system, open the folder containing your target Unity project.</span></span>

> [!NOTE]
> <span data-ttu-id="4c83d-144">Das Dialogfeld, das angezeigt wird, wenn Sie das Dateisystem nach dem Unity-Projektordner durchsuchen, enthält '_' als den Dateinamen.</span><span class="sxs-lookup"><span data-stu-id="4c83d-144">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="4c83d-145">Es muss ein Wert für den Dateinamen vorhanden sein, um die Auswahl des Ordners zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="4c83d-145">There must be a value for the file name to enable the folder to be selected.</span></span>

<span data-ttu-id="4c83d-146">Wählen Sie **Importieren** aus, um fortzufahren.</span><span class="sxs-lookup"><span data-stu-id="4c83d-146">Select **Import** to continue.</span></span>

> [!NOTE]
> <span data-ttu-id="4c83d-147">Sollten nach dem Klicken auf die Schaltfläche **Import** noch Probleme bestehen, wird eine einfache Meldung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4c83d-147">After clicking the **Import** button, if any issues remain a simple message will be displayed.</span></span> <span data-ttu-id="4c83d-148">Es wird empfohlen, auf „Nein“ zu klicken und die Schaltfläche **Validate** (Überprüfen) zu verwenden, um die Probleme anzuzeigen und zu beheben.</span><span class="sxs-lookup"><span data-stu-id="4c83d-148">The recommendation is to click No and to use the **Validate** button to view and resolve the issues.</span></span>

<span data-ttu-id="4c83d-149">Weitere Informationen finden Sie unter [Importieren von Features](importing-features.md).</span><span class="sxs-lookup"><span data-stu-id="4c83d-149">For more information, please see [importing features](importing-features.md).</span></span>

## <a name="4-reviewing-and-approving-project-changes"></a><span data-ttu-id="4c83d-150">4. Überprüfen und Genehmigen von Projektänderungen</span><span class="sxs-lookup"><span data-stu-id="4c83d-150">4. Reviewing and approving project changes</span></span>

<span data-ttu-id="4c83d-151">Der letzte Schritt besteht im Überprüfen und Genehmigen der vorgeschlagenen Änderungen an den Manifest- und Projektdateien:</span><span class="sxs-lookup"><span data-stu-id="4c83d-151">The final step is reviewing and approving the proposed changes to the manifest and project files:</span></span>

* <span data-ttu-id="4c83d-152">Die vorgeschlagenen Änderungen am Manifest werden auf der linken Seite angezeigt</span><span class="sxs-lookup"><span data-stu-id="4c83d-152">The proposed changes to the manifest are displayed on the left</span></span>
* <span data-ttu-id="4c83d-153">Die Dateien, die dem Projekt hinzugefügt werden sollen, werden auf der rechten Seite angezeigt</span><span class="sxs-lookup"><span data-stu-id="4c83d-153">The files to be added to the project are listed to the right</span></span>
* <span data-ttu-id="4c83d-154">Mit der Schaltfläche **Compare** (Vergleichen) können Sie das aktuelle Manifest und die vorgeschlagenen Änderungen nebeneinander anzeigen</span><span class="sxs-lookup"><span data-stu-id="4c83d-154">The **Compare** button allows for side by side viewing of the current manifest and the proposed changes</span></span>

![Authorization](images/FeatureToolApprovalRequest.png)

<span data-ttu-id="4c83d-156">Weitere Informationen finden Sie unter [Überprüfen und Genehmigen von Projektänderungen](reviewing-changes.md).</span><span class="sxs-lookup"><span data-stu-id="4c83d-156">For more information, see [reviewing and approving project modifications](reviewing-changes.md).</span></span>

## <a name="5-project-updated"></a><span data-ttu-id="4c83d-157">5. Projekt aktualisiert</span><span class="sxs-lookup"><span data-stu-id="4c83d-157">5. Project updated</span></span>

<span data-ttu-id="4c83d-158">Wenn die vorgeschlagenen Änderungen genehmigt werden, wird Ihr Unity-Zielprojekt aktualisiert, um auf die ausgewählten Mixed Reality-Features zu verweisen:</span><span class="sxs-lookup"><span data-stu-id="4c83d-158">When the proposed changes are approved, your target Unity project is updated to reference the selected Mixed Reality features:</span></span>

![Projekt aktualisiert](images/FeatureToolProjectUpdated.png)

<span data-ttu-id="4c83d-160">Der Ordner **Packages** (Pakete) des Unity-Projekts enthält jetzt einen Unterordner **MixedReality** mit den Dateien der Featurepakete, und das Manifest enthält die entsprechenden Verweise.</span><span class="sxs-lookup"><span data-stu-id="4c83d-160">The Unity project's **Packages** folder now has a **MixedReality** subfolder with the feature package file(s) and the manifest will contain the appropriate reference(s).</span></span>

<span data-ttu-id="4c83d-161">Kehren Sie zu Unity zurück, warten Sie auf das Laden der neu ausgewählten Features, und beginnen Sie mit dem Erstellen!</span><span class="sxs-lookup"><span data-stu-id="4c83d-161">Return to Unity, wait for the new selected features to load, and start building!</span></span>

## <a name="see-also"></a><span data-ttu-id="4c83d-162">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="4c83d-162">See also</span></span>

- [<span data-ttu-id="4c83d-163">Konfigurieren des Featuretools</span><span class="sxs-lookup"><span data-stu-id="4c83d-163">Configuring the feature tool</span></span>](configuring-feature-tool.md)
- [<span data-ttu-id="4c83d-164">Ermittlung und Erwerb</span><span class="sxs-lookup"><span data-stu-id="4c83d-164">Discovery and acquisition</span></span>](discovering-features.md)
- [<span data-ttu-id="4c83d-165">Anzeigen von Details zu Featurepaketen</span><span class="sxs-lookup"><span data-stu-id="4c83d-165">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="4c83d-166">Importieren ausgewählter Pakete</span><span class="sxs-lookup"><span data-stu-id="4c83d-166">Importing selected packages</span></span>](importing-features.md)
- [<span data-ttu-id="4c83d-167">Überprüfen und Genehmigen von Projektänderungen</span><span class="sxs-lookup"><span data-stu-id="4c83d-167">Reviewing and approving project modifications</span></span>](reviewing-changes.md)
