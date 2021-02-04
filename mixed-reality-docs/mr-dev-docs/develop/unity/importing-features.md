---
title: Importieren von Features
description: Erfahren Sie, wie Sie Features aus dem MR-Featuretool für die HoloLens- und VR-Entwicklung importieren.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: Aktuell, Tools, Erste Schritte, Grundlagen, Unity, Visual Studio, Toolkit, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Installation, Windows, HoloLens, Emulator, Unreal, OpenXR
ms.openlocfilehash: a82eea93a07b662314f3a718eef0c1bd18a4ca4e
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2021
ms.locfileid: "99243913"
---
# <a name="importing-features"></a><span data-ttu-id="f6197-104">Importieren von Features</span><span class="sxs-lookup"><span data-stu-id="f6197-104">Importing features</span></span>

<span data-ttu-id="f6197-105">Nachdem Ihre Features heruntergeladen wurden, können sie überprüft und in das Unity-Projekt importiert werden.</span><span class="sxs-lookup"><span data-stu-id="f6197-105">Once your features have been downloaded, they can be reviewed and imported into the Unity project.</span></span> <span data-ttu-id="f6197-106">In diesem Schritt sollte Ihr Anwendungsfenster wie in der folgenden Abbildung aussehen:</span><span class="sxs-lookup"><span data-stu-id="f6197-106">At this step, your application window should look like the following image:</span></span>

![Importieren von Features](images/FeatureToolImport.png)

## <a name="features-list"></a><span data-ttu-id="f6197-108">Features list</span><span class="sxs-lookup"><span data-stu-id="f6197-108">Features list</span></span>

<span data-ttu-id="f6197-109">Die Liste **Features** enthält die Sammlung von Paketen, die während der Ermittlung ausgewählt wurden.</span><span class="sxs-lookup"><span data-stu-id="f6197-109">The **Features** list contains the collection of packages selected during discovery.</span></span> 
* <span data-ttu-id="f6197-110">Die einzelnen Features können vor dem Importieren ausgewählt oder abgewählt werden.</span><span class="sxs-lookup"><span data-stu-id="f6197-110">Each feature can be selected or deselected before importing.</span></span> <span data-ttu-id="f6197-111">Paketdetails können über den unten abgebildeten Link **Details** angezeigt werden</span><span class="sxs-lookup"><span data-stu-id="f6197-111">Package details can be viewed using the **Details** link shown below</span></span>

![Features list](images/FeaturesList.png)

## <a name="required-dependencies-list"></a><span data-ttu-id="f6197-113">Liste der erforderlichen Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="f6197-113">Required dependencies list</span></span>

<span data-ttu-id="f6197-114">Die Liste **Required dependencies** (Erforderliche Abhängigkeiten) enthält die Pakete, die für die Funktion eines oder mehrerer der ausgewählten Features erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="f6197-114">The **Required dependencies** list contains the packages that one or more of the selected features requires to function.</span></span> <span data-ttu-id="f6197-115">Diese Liste enthält auch Abhängigkeiten von Abhängigkeiten.</span><span class="sxs-lookup"><span data-stu-id="f6197-115">This list will also contain dependencies of dependencies.</span></span>
* <span data-ttu-id="f6197-116">Jede Abhängigkeit kann vor dem Importieren ausgewählt oder abgewählt werden.</span><span class="sxs-lookup"><span data-stu-id="f6197-116">Each dependency can be selected or deselected before importing.</span></span> <span data-ttu-id="f6197-117">Paketdetails können über den unten abgebildeten Link **Details** angezeigt werden</span><span class="sxs-lookup"><span data-stu-id="f6197-117">Package details can be viewed using the **Details** link shown below</span></span>

![Liste „Dependencies“ (Abhängigkeiten)](images/RequiredDependencyList.png)

> [!NOTE]
> <span data-ttu-id="f6197-119">Das Aufheben der Auswahl erforderlicher Abhängigkeiten führt beim Laden des Projekts in Unity zu mindestens einem Fehler wegen fehlender Abhängigkeiten.</span><span class="sxs-lookup"><span data-stu-id="f6197-119">Deselecting required dependencies will result in one or more missing dependency errors when loading the project in Unity.</span></span> <span data-ttu-id="f6197-120">Die betroffenen Features sind dann im Projekt nicht nutzbar.</span><span class="sxs-lookup"><span data-stu-id="f6197-120">These features won't be usable in the project.</span></span>

## <a name="specifying-the-unity-project-path"></a><span data-ttu-id="f6197-121">Angeben des Unity-Projektpfads</span><span class="sxs-lookup"><span data-stu-id="f6197-121">Specifying the Unity project path</span></span>

<span data-ttu-id="f6197-122">Bevor Features in das Projekt importiert werden können, müssen Sie den Pfad beim Mixed Reality-Featuretool registrieren.</span><span class="sxs-lookup"><span data-stu-id="f6197-122">Before features can be imported into the project, you need to register the path with the Mixed Reality Feature Tool.</span></span>

![Festlegen des Projektpfads](images/ProjectPath.png)

## <a name="validating-selections"></a><span data-ttu-id="f6197-124">Überprüfen der Auswahl</span><span class="sxs-lookup"><span data-stu-id="f6197-124">Validating selections</span></span>

<span data-ttu-id="f6197-125">Wir empfehlen dringend, die Featureauswahl vor dem Importieren zu überprüfen.</span><span class="sxs-lookup"><span data-stu-id="f6197-125">We highly recommend validating feature selections before importing.</span></span> <span data-ttu-id="f6197-126">In diesem Schritt kommen alle Probleme ans Licht, die eine erfolgreiche Projektentwicklung wahrscheinlich verhindern.</span><span class="sxs-lookup"><span data-stu-id="f6197-126">This step will raise any issues that are likely to impede successful project development.</span></span>

![Probleme bei der Überprüfung](images/ValidationIssues.png)

<span data-ttu-id="f6197-128">Das Mixed Reality-Featuretool bietet zwei automatische Fehlerbehebungen (in den folgenden Abschnitten beschrieben) und die Option zum Abbrechen und manuellen Beheben von Fehlern.</span><span class="sxs-lookup"><span data-stu-id="f6197-128">The Mixed Reality Feature Tool provides two automatic issue resolutions, described in the following sections), and the option to cancel and resolve issues manually.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f6197-129">Das Mixed Reality-Featuretool kann Fehler im Zusammenhang mit der erforderlichen Unity-Version nicht automatisch beheben.</span><span class="sxs-lookup"><span data-stu-id="f6197-129">The Mixed Reality Feature Tool cannot automatically resolve issues related to required versions of Unity.</span></span> <span data-ttu-id="f6197-130">Diese Probleme müssen manuell durch ein Upgrade der vom Projekt verwendeten Version von Unity oder durch Deaktivieren der Features behoben werden, für die eine neuere Version erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="f6197-130">These issues must be handled manually by upgrading the version of Unity used by the project or disabling the feature(s) requiring a newer version.</span></span>
>
> <span data-ttu-id="f6197-131">Eine kommende Version des Mixed Reality-Featuretools wird eine bessere Filterung der Features nach der vom Projekt verwendeten Unity-Version bieten.</span><span class="sxs-lookup"><span data-stu-id="f6197-131">A future release of the Mixed Reality Feature Tool will provide better filtering of features based upon the version of Unity being used by the project.</span></span>

### <a name="enable-dependencies"></a><span data-ttu-id="f6197-132">Aktivieren von Abhängigkeiten</span><span class="sxs-lookup"><span data-stu-id="f6197-132">Enable dependencies</span></span>

<span data-ttu-id="f6197-133">Mit der Schaltfläche **Enable dependencies** (Abhängigkeiten aktivieren) werden die fehlenden Abhängigkeiten automatisch wieder ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="f6197-133">The **Enable dependencies** button will automatically re-select the missing dependencies.</span></span> <span data-ttu-id="f6197-134">Dies gilt für Abhängigkeiten, die explizit ausgewählt wurden (werden in der Liste **Features** angezeigt) und solchen, die auf der Grundlage der Abhängigkeiten der ausgewählten Features implizit ausgewählt wurden.</span><span class="sxs-lookup"><span data-stu-id="f6197-134">This is true for dependencies that were explicitly selected (appear in the **Features** list) and those that were implicitly selected based on the requirements of the selected features.</span></span>

### <a name="disable-features"></a><span data-ttu-id="f6197-135">Deaktivieren von Features</span><span class="sxs-lookup"><span data-stu-id="f6197-135">Disable features</span></span>

<span data-ttu-id="f6197-136">Wenn Sie **Features deaktivieren** auswählen, werden alle Features, die von mindestens einer der Abhängigkeiten abhängen, deren Auswahl aufgehoben wurde, automatisch deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="f6197-136">Selecting **Disable features** will automatically deselect any feature that depends on one or more of the dependencies that have been unchecked.</span></span> <span data-ttu-id="f6197-137">Dies gilt für implizit ausgewählte Abhängigkeitspakete und explizit ausgewählte Features.</span><span class="sxs-lookup"><span data-stu-id="f6197-137">This is true for implicitly selected dependency packages and explicitly selected features.</span></span>

## <a name="importing"></a><span data-ttu-id="f6197-138">Importieren</span><span class="sxs-lookup"><span data-stu-id="f6197-138">Importing</span></span>

<span data-ttu-id="f6197-139">Wählen Sie **importieren** aus, um die ausgewählten Features hinzuzufügen und die [endgültige Genehmigung](reviewing-changes.md) zu erteilen, bevor Sie das Zielprojekt aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="f6197-139">Select **Import** to add your selected features and give [final approval](reviewing-changes.md) before updating your target project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f6197-140">Wenn beim importieren ein Überprüfungsfehler verbleibt, wird eine Warnmeldung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f6197-140">If a validation issue remains when importing, a warning message will be displayed.</span></span> <span data-ttu-id="f6197-141">In diesem Fall wird empfohlen, dass Sie „No“ (Nein) auswählen, auf **Validate** (Überprüfen) klicken und alle angezeigten Fehler beheben.</span><span class="sxs-lookup"><span data-stu-id="f6197-141">It is recommended to select No, click **Validate** and resolve any issues presented.</span></span>
>
> ![Mit Überprüfungsproblemen fortfahren](images/ValidationContinueAnyway.png)

## <a name="going-back-to-the-previous-step"></a><span data-ttu-id="f6197-143">Zurück zum vorherigen Schritt</span><span class="sxs-lookup"><span data-stu-id="f6197-143">Going back to the previous step</span></span>

<span data-ttu-id="f6197-144">Von **Import features** (Features importieren) erlaubt Ihnen das Mixed Reality-Featuretool die Navigation zurück zur [Ermittlung](discovering-features.md).</span><span class="sxs-lookup"><span data-stu-id="f6197-144">From **Import features**, the Mixed Reality Feature Tool allows for navigating back to [discovery](discovering-features.md).</span></span> <span data-ttu-id="f6197-145">Wählen Sie **Go back** (Zurück) aus, um weitere Featurepakete herunterzuladen.</span><span class="sxs-lookup"><span data-stu-id="f6197-145">Select **Go back** to download other feature packages.</span></span>

## <a name="see-also"></a><span data-ttu-id="f6197-146">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f6197-146">See also</span></span>

- [<span data-ttu-id="f6197-147">Willkommen beim Mixed Reality-Featuretool</span><span class="sxs-lookup"><span data-stu-id="f6197-147">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
- [<span data-ttu-id="f6197-148">Ermittlung und Erwerb</span><span class="sxs-lookup"><span data-stu-id="f6197-148">Discovery and acquisition</span></span>](discovering-features.md)
- [<span data-ttu-id="f6197-149">Anzeigen von Details zu Featurepaketen</span><span class="sxs-lookup"><span data-stu-id="f6197-149">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="f6197-150">Überprüfen und Genehmigen von Projektänderungen</span><span class="sxs-lookup"><span data-stu-id="f6197-150">Reviewing and approving project modifications</span></span>](reviewing-changes.md)