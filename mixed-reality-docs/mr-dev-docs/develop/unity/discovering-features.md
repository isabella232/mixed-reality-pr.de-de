---
title: Ermitteln und Erwerben von Features
description: Ermitteln und Herunterladen von Mixed Reality-Features.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 04/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: Aktuell, Tools, Erste Schritte, Grundlagen, Unity, Visual Studio, Toolkit, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Installation, Windows, HoloLens, Emulator, Unreal, OpenXR
ms.openlocfilehash: 9f12a1eba0c28b89000f1541ba62747a03e3564b
ms.sourcegitcommit: 286384e6e255135939bce2ab0267a62558837562
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2021
ms.locfileid: "107732008"
---
# <a name="discovering-and-acquiring-features"></a><span data-ttu-id="e5e09-104">Ermitteln und Erwerben von Features</span><span class="sxs-lookup"><span data-stu-id="e5e09-104">Discovering and acquiring features</span></span>

<span data-ttu-id="e5e09-105">In den Abschnitten in diesem Artikel wird erläutert, wie Sie Featurepakete im Mixed Reality-Featuretool finden.</span><span class="sxs-lookup"><span data-stu-id="e5e09-105">The sections in this article outline how to find feature packages in the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="e5e09-106">Wenn Sie eine Referenz für einen bestimmten Abschnitt benötigen, sehen Sie sich den Screenshot unten an:</span><span class="sxs-lookup"><span data-stu-id="e5e09-106">Refer to the screenshot below if you need a reference for a given section:</span></span>

![Ermitteln von Features](images/FeatureToolDiscovery.png)

## <a name="available-features"></a><span data-ttu-id="e5e09-108">Verfügbare Features</span><span class="sxs-lookup"><span data-stu-id="e5e09-108">Available features</span></span>

### <a name="category"></a><span data-ttu-id="e5e09-109">Category</span><span class="sxs-lookup"><span data-stu-id="e5e09-109">Category</span></span>

<span data-ttu-id="e5e09-110">Das Mixed Reality-Featuretool zeigt eine Auflistung von Featurekategorien an, um das Auffinden der gewünschten Features zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="e5e09-110">The Mixed Reality Feature Tool displays a collection of feature categories to make it easy to find what you want.</span></span> <span data-ttu-id="e5e09-111">Erweitern Sie eine beliebige Kategorie, um die in ihr enthaltene Sammlung verfügbarer Features anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="e5e09-111">Expand any of the categories to display its collection of available features.</span></span>

> [!NOTE]
> <span data-ttu-id="e5e09-112">Wenn Sie die gewünschte Funktionalität nicht finden können, aktivieren Sie **Other Features** (Weitere Features).</span><span class="sxs-lookup"><span data-stu-id="e5e09-112">If you can't find the functionality you're looking for, check **Other features**.</span></span>

![Featurekategorie](images/FeatureCategory.png)

<span data-ttu-id="e5e09-114">Die Kategoriekopfzeile im Screenshot oben enthält von links nach rechts die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="e5e09-114">The category header in the above screenshot contains the following properties, from left to right:</span></span>

- <span data-ttu-id="e5e09-115">Schaltfläche zum Erweitern und Reduzieren</span><span class="sxs-lookup"><span data-stu-id="e5e09-115">Expand and collapse button</span></span>
- <span data-ttu-id="e5e09-116">Kategoriename (Bsp.: Mixed Reality-Toolkit)</span><span class="sxs-lookup"><span data-stu-id="e5e09-116">Category name (ex: Mixed Reality Toolkit)</span></span>
- <span data-ttu-id="e5e09-117">Anzahl der ausgewählten Features</span><span class="sxs-lookup"><span data-stu-id="e5e09-117">Count of selected features</span></span>
- <span data-ttu-id="e5e09-118">Anzahl der verfügbaren Features</span><span class="sxs-lookup"><span data-stu-id="e5e09-118">Count of available features</span></span>
- <span data-ttu-id="e5e09-119">Abschnittsschaltflächen</span><span class="sxs-lookup"><span data-stu-id="e5e09-119">Section buttons</span></span>

> [!NOTE]
> <span data-ttu-id="e5e09-120">Die Auswahlschaltflächen sind kontextsensitiv.</span><span class="sxs-lookup"><span data-stu-id="e5e09-120">The selection buttons are context sensitive.</span></span> <span data-ttu-id="e5e09-121">Basierend auf dem Status der Featureauswahl innerhalb der Kategorie wird eine oder werden beide der Schaltflächen `Select All` und `Select None` angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e5e09-121">Based on the state of feature selection within the category, one or more of the `Select All` and `Select None` buttons will be displayed.</span></span>

### <a name="feature"></a><span data-ttu-id="e5e09-122">Funktion</span><span class="sxs-lookup"><span data-stu-id="e5e09-122">Feature</span></span>

![Featureeintrag](images/FeatureEntry.png)

<span data-ttu-id="e5e09-124">Die Features werden in der entsprechenden Kategorie aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="e5e09-124">Features are listed in their appropriate category.</span></span> <span data-ttu-id="e5e09-125">Die Featureeinträge im Screenshot oben enthalten von links nach rechts:</span><span class="sxs-lookup"><span data-stu-id="e5e09-125">From left to right in the above screenshot, feature entries contain:</span></span>

- <span data-ttu-id="e5e09-126">Auswahlkontrollkästchen</span><span class="sxs-lookup"><span data-stu-id="e5e09-126">Selection check box</span></span>
- <span data-ttu-id="e5e09-127">Featurename (Bsp.: Mixed Reality Toolkit Foundation)</span><span class="sxs-lookup"><span data-stu-id="e5e09-127">Feature name (ex: Mixed Reality Toolkit Foundation)</span></span>
- <span data-ttu-id="e5e09-128">Liste der verfügbaren Versionen</span><span class="sxs-lookup"><span data-stu-id="e5e09-128">List of available versions</span></span>
- <span data-ttu-id="e5e09-129">Link zu den [Featurepaketdetails](viewing-package-details.md)</span><span class="sxs-lookup"><span data-stu-id="e5e09-129">Link to the [feature package details](viewing-package-details.md)</span></span>

> [!NOTE]
> <span data-ttu-id="e5e09-130">Wenn ein Feature von einem Early Access-Programm (auch als private Vorschauversion bezeichnet) bereitgestellt wird, wird ein Indikatorsymbol ![Early Access](images/EarlyAccess.png) angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e5e09-130">If a feature is provided by an Early Access (also called private preview) program, an indicator icon ![early access](images/EarlyAccess.png) will be displayed.</span></span>

## <a name="refresh-the-feature-catalog"></a><span data-ttu-id="e5e09-131">Aktualisieren des Featurekatalogs</span><span class="sxs-lookup"><span data-stu-id="e5e09-131">Refresh the feature catalog</span></span>

<span data-ttu-id="e5e09-132">Zur Suche nach neuen und aktualisierten Features klicken Sie auf die Schaltfläche zum Aktualisieren</span><span class="sxs-lookup"><span data-stu-id="e5e09-132">To check for new and updated features, click the refresh</span></span> ![Schaltfläche „Aktualisieren“](images/RefreshButton.png) <span data-ttu-id="e5e09-134">Schaltfläche.</span><span class="sxs-lookup"><span data-stu-id="e5e09-134">button.</span></span> <span data-ttu-id="e5e09-135">Dadurch wird eine Verbindung mit der Katalogwebsite hergestellt, und die neuesten Informationen werden abgerufen.</span><span class="sxs-lookup"><span data-stu-id="e5e09-135">This will connect to the catalog site and retrieve the latest information.</span></span> <span data-ttu-id="e5e09-136">Nachdem der Katalog gelesen wurde, werden das Datum und die Uhrzeit des letzten Updates angezeigt.</span><span class="sxs-lookup"><span data-stu-id="e5e09-136">Once the catalog has been read, the date and time of the last update will be displayed.</span></span>

## <a name="select-features"></a><span data-ttu-id="e5e09-137">Auswählen von Features</span><span class="sxs-lookup"><span data-stu-id="e5e09-137">Select features</span></span>

<span data-ttu-id="e5e09-138">Sie wählen Features aus, indem Sie eine Kategorie erweitern, eine Version auswählen und auf das Kontrollkästchen klicken:</span><span class="sxs-lookup"><span data-stu-id="e5e09-138">Features are selected by expanding a category, selecting a version, and clicking the check box:</span></span>

![Ausgewählte Features](images/SelectedFeatures.png)

<span data-ttu-id="e5e09-140">Zum Auswählen jedes Pakets innerhalb einer Kategorie steht eine Schaltfläche `Select All` zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="e5e09-140">To select every package within a category, a `Select All` button is provided.</span></span> <span data-ttu-id="e5e09-141">`Select None` deaktiviert die Auswahl aller ausgewählten Pakete.</span><span class="sxs-lookup"><span data-stu-id="e5e09-141">`Select None` will deselect all selected packages.</span></span> 

<span data-ttu-id="e5e09-142">Jede Kategorie mit mindestens einem ausgewählten Feature wird aktualisiert, um die Anzahl anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="e5e09-142">Each category with one or more selected features will update to display the count.</span></span>

## <a name="acquiring-features"></a><span data-ttu-id="e5e09-143">Erwerben von Features</span><span class="sxs-lookup"><span data-stu-id="e5e09-143">Acquiring features</span></span>

<span data-ttu-id="e5e09-144">Nachdem Sie Ihre Features ausgewählt haben, wählen Sie **Get features** (Features abrufen) aus, um mit dem Download der ausgewählten Featurepaketdateien zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="e5e09-144">Once you've chosen your features, select **Get features** to start downloading the selected feature package files.</span></span>

> [!NOTE]
> <span data-ttu-id="e5e09-145">Standardmäßig werden zuvor erworbene Featurepaketdateien nicht erneut heruntergeladen.</span><span class="sxs-lookup"><span data-stu-id="e5e09-145">By default, previously acquired feature package files won't be re-downloaded.</span></span> <span data-ttu-id="e5e09-146">Wenn Sie dieses Verhalten ändern möchten, finden Sie weitere Informationen unter [Konfigurieren des Featuretools](configuring-feature-tool.md).</span><span class="sxs-lookup"><span data-stu-id="e5e09-146">To change this behavior please see [configuring the feature tool](configuring-feature-tool.md).</span></span>

<span data-ttu-id="e5e09-147">Nachdem dem Abschluss des Downloads wechselt das Mixed Reality-Featuretool zum Schritt [Importing Features](importing-features.md) (Features importieren).</span><span class="sxs-lookup"><span data-stu-id="e5e09-147">Once downloading is complete, the Mixed Reality Feature Tool will move to the [importing features](importing-features.md) step.</span></span>

## <a name="going-back-to-the-previous-step"></a><span data-ttu-id="e5e09-148">Zurückwechseln zum vorherigen Schritt</span><span class="sxs-lookup"><span data-stu-id="e5e09-148">Going back to the previous step</span></span>

<span data-ttu-id="e5e09-149">Von **Discover features** (Features ermitteln) erlaubt Ihnen das Mixed Reality-Featuretool die Navigation zurück zur Projektauswahl.</span><span class="sxs-lookup"><span data-stu-id="e5e09-149">From **Discover features**, the Mixed Reality Feature Tool allows for navigating back to project selection.</span></span> <span data-ttu-id="e5e09-150">Wählen Sie **Go back** (Zurück) aus, um erneut zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="e5e09-150">Select **Go back** to start again.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5e09-151">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e5e09-151">See also</span></span>

- [<span data-ttu-id="e5e09-152">Willkommen beim Mixed Reality-Featuretool</span><span class="sxs-lookup"><span data-stu-id="e5e09-152">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
- [<span data-ttu-id="e5e09-153">Konfigurieren des Featuretools</span><span class="sxs-lookup"><span data-stu-id="e5e09-153">Configuring the feature tool</span></span>](configuring-feature-tool.md)
- [<span data-ttu-id="e5e09-154">Anzeigen von Details zu Featurepaketen</span><span class="sxs-lookup"><span data-stu-id="e5e09-154">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="e5e09-155">Importieren ausgewählter Pakete</span><span class="sxs-lookup"><span data-stu-id="e5e09-155">Importing selected packages</span></span>](importing-features.md)
