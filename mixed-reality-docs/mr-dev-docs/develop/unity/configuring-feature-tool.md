---
title: Konfigurieren des Mixed Reality-Featuretools
description: Erfahren Sie, wie Sie Mixed Reality Unity-Pakete über das MR-Featuretool für die HoloLens- und VR-Entwicklung herunterladen und installieren.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 04/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: Aktuell, Tools, Erste Schritte, Grundlagen, Unity, Visual Studio, Toolkit, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Installation, Windows, HoloLens, Emulator, Unreal, OpenXR
ms.openlocfilehash: 5b61924ccf4d3eb5f5433c9042582ff2a850bb04
ms.sourcegitcommit: 286384e6e255135939bce2ab0267a62558837562
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2021
ms.locfileid: "107731949"
---
# <a name="configuring-the-mixed-reality-feature-tool"></a><span data-ttu-id="07bbe-104">Konfigurieren des Mixed Reality-Featuretools</span><span class="sxs-lookup"><span data-stu-id="07bbe-104">Configuring the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="07bbe-105">Beim Verwenden des Mixed Reality-Featuretools haben Sie Zugriff auf drei verschiedene Kategorien von Einstellungen, die Sie nach Belieben anpassen können:</span><span class="sxs-lookup"><span data-stu-id="07bbe-105">When using the Mixed Reality Feature Tool, you have access to three different settings categories that you can customize at will:</span></span>

* [<span data-ttu-id="07bbe-106">Downloadeinstellungen</span><span class="sxs-lookup"><span data-stu-id="07bbe-106">Download settings</span></span>](#download-settings)
* [<span data-ttu-id="07bbe-107">Featureeinstellungen</span><span class="sxs-lookup"><span data-stu-id="07bbe-107">Feature settings</span></span>](#feature-settings)
* [<span data-ttu-id="07bbe-108">Importieren von Einstellungen</span><span class="sxs-lookup"><span data-stu-id="07bbe-108">Import settings</span></span>](#import-settings)

## <a name="download-settings"></a><span data-ttu-id="07bbe-109">Downloadeinstellungen</span><span class="sxs-lookup"><span data-stu-id="07bbe-109">Download settings</span></span>

![Downloadeinstellungen](images/FeatureToolSettings-Download.png)

### <a name="overwrite-existing-package-files"></a><span data-ttu-id="07bbe-111">Vorhandene Paketdateien überschreiben</span><span class="sxs-lookup"><span data-stu-id="07bbe-111">Overwrite existing package files</span></span>

<span data-ttu-id="07bbe-112">Wenn Sie diese Einstellung aktivieren, werden die Paketdateien bei jedem Abrufen heruntergeladen.</span><span class="sxs-lookup"><span data-stu-id="07bbe-112">Enabling this setting causes package files to be downloaded every time they're acquired.</span></span> 

* <span data-ttu-id="07bbe-113">**Wir empfehlen, diese Option deaktiviert zu lassen, um den Verbrauch an Netzwerkbandbreite zu verringern**</span><span class="sxs-lookup"><span data-stu-id="07bbe-113">**We recommend leaving this option disabled to reduce network bandwidth usage**</span></span>
* <span data-ttu-id="07bbe-114">Standardmäßig werden zuvor erworbene Featurepaketdateien nicht erneut heruntergeladen.</span><span class="sxs-lookup"><span data-stu-id="07bbe-114">By default, previously acquired package files aren't re-downloaded</span></span>

### <a name="package-cache"></a><span data-ttu-id="07bbe-115">Paketcache</span><span class="sxs-lookup"><span data-stu-id="07bbe-115">Package cache</span></span>

<span data-ttu-id="07bbe-116">Ändern Sie diese Einstellung, um den Speicherort zu ändern, an dem heruntergeladene Featurepakete gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="07bbe-116">Change this setting to update the location where feature packages are downloaded.</span></span>

> [!NOTE]
> <span data-ttu-id="07bbe-117">Diese Einstellung ist in dieser Version **schreibgeschützt**.</span><span class="sxs-lookup"><span data-stu-id="07bbe-117">This setting is **read-only** in this release.</span></span> <span data-ttu-id="07bbe-118">In zukünftigen Versionen wird diese Einstellung möglicherweise konfigurierbar.</span><span class="sxs-lookup"><span data-stu-id="07bbe-118">Future releases may make this setting configurable.</span></span>

## <a name="feature-settings"></a><span data-ttu-id="07bbe-119">Featureeinstellungen</span><span class="sxs-lookup"><span data-stu-id="07bbe-119">Feature settings</span></span>

![Featureeinstellungen](images/FeatureToolSettings-Feature.png)

### <a name="show-preview-releases"></a><span data-ttu-id="07bbe-121">Vorschauversionen anzeigen</span><span class="sxs-lookup"><span data-stu-id="07bbe-121">Show preview releases</span></span>

<span data-ttu-id="07bbe-122">Aktivieren Sie diese Einstellung, um Vorschauversionen zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="07bbe-122">Enable this setting to acquire preview releases.</span></span>
* <span data-ttu-id="07bbe-123">Standardmäßig werden Vorschauversionen nicht im Mixed Reality-Featuretool angezeigt</span><span class="sxs-lookup"><span data-stu-id="07bbe-123">By default, preview releases are not shown in the Mixed Reality Feature Tool</span></span> 

> [!NOTE]
> <span data-ttu-id="07bbe-124">Eine Vorschauversion ist dadurch gekennzeichnet, dass sie die Bezeichnung **"-preview"** in der Paketversion enthält.</span><span class="sxs-lookup"><span data-stu-id="07bbe-124">A preview release is defined as containing the **"-preview"** designation in the package version.</span></span>

### <a name="show-early-access-program-features"></a><span data-ttu-id="07bbe-125">Features des Early Access-Programms anzeigen</span><span class="sxs-lookup"><span data-stu-id="07bbe-125">Show early access program features</span></span>

<span data-ttu-id="07bbe-126">Aktivieren Sie diese Einstellung, um Features aus registrierten Releases von Early Access-Programmen zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="07bbe-126">Enable this setting to acquire features from registered early access programs releases.</span></span>

* <span data-ttu-id="07bbe-127">Standardmäßig werden Early Access-Features nicht im Mixed Reality-Featuretool angezeigt.</span><span class="sxs-lookup"><span data-stu-id="07bbe-127">By default, early access features are not shown in the Mixed Reality Feature Tool</span></span> 

> [!NOTE]
> <span data-ttu-id="07bbe-128">Die Aktivierung von `Show early access program features` ohne `Show preview releases` kann dazu führen, dass Early Access-Pakete nicht in der Ermittlung angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="07bbe-128">Enabling `Show early access program features` without `Show preview releases` may result in eary access packages not appearing in Discovery.</span></span>

## <a name="import-settings"></a><span data-ttu-id="07bbe-129">Importieren von Einstellungen</span><span class="sxs-lookup"><span data-stu-id="07bbe-129">Import settings</span></span>

![Importieren von Einstellungen](images/FeatureToolSettings-Import.png)

### <a name="replace-existing-package-files"></a><span data-ttu-id="07bbe-131">Vorhandene Paketdateien ersetzen</span><span class="sxs-lookup"><span data-stu-id="07bbe-131">Replace existing package files</span></span>

<span data-ttu-id="07bbe-132">Standardmäßig entfernt das Mixed Reality-Featuretool vorherige Exemplare von Paketen, die importiert werden, um die Dateigröße und unnötige Berechnungen zu verringern.</span><span class="sxs-lookup"><span data-stu-id="07bbe-132">By default, the Mixed Reality Feature Tool removes previous copies of the packages being imported to reduce the file size and unnecessary computations.</span></span> 

* <span data-ttu-id="07bbe-133">Deaktivieren Sie diese Einstellung, wenn Sie alle Versionen behalten möchten.</span><span class="sxs-lookup"><span data-stu-id="07bbe-133">Uncheck this setting to keep all versions</span></span>

### <a name="project-relative-import-path"></a><span data-ttu-id="07bbe-134">Relativer Importpfad des Projekts</span><span class="sxs-lookup"><span data-stu-id="07bbe-134">Project relative import path</span></span>

<span data-ttu-id="07bbe-135">Ändern Sie diese Einstellung, um den Ordnerpfad des Projekts zu aktualisieren, in den Featurepakete beim Importieren kopiert werden.</span><span class="sxs-lookup"><span data-stu-id="07bbe-135">Change this setting to update project folder path where feature packages are copied on import.</span></span> 

* <span data-ttu-id="07bbe-136">Wenn der Projektordner beispielsweise **C:\GalaxyExplorer** ist, lautet der vollqualifizierte Importpfad **C:\GalaxyExplorer\Packages\MixedReality**.</span><span class="sxs-lookup"><span data-stu-id="07bbe-136">For example, if the project folder is **C:\GalaxyExplorer**, the fully qualified import path will be **C:\GalaxyExplorer\Packages\MixedReality**.</span></span>

> [!NOTE]
> <span data-ttu-id="07bbe-137">Diese Einstellung ist in dieser Version **schreibgeschützt**.</span><span class="sxs-lookup"><span data-stu-id="07bbe-137">This setting is **read-only** in this release.</span></span> <span data-ttu-id="07bbe-138">In zukünftigen Versionen wird diese Einstellung möglicherweise konfigurierbar.</span><span class="sxs-lookup"><span data-stu-id="07bbe-138">Future releases may make this setting configurable.</span></span>

## <a name="early-access-settings"></a><span data-ttu-id="07bbe-139">Early Access-Einstellungen</span><span class="sxs-lookup"><span data-stu-id="07bbe-139">Early Access settings</span></span>

![Early Access-Einstellungen](images/FeatureToolSettings-EarlyAccess.png)
 
### <a name="ask-for-confirmation-before-removing-an-early-access-program"></a><span data-ttu-id="07bbe-141">Vor dem Entfernen eines Early Access-Programms zur Bestätigung auffordern</span><span class="sxs-lookup"><span data-stu-id="07bbe-141">Ask for confirmation before removing an early access program</span></span>

<span data-ttu-id="07bbe-142">Diese Einstellung bestimmt, ob jedes Mal, wenn ein Early Access-Programm entfernt wird, eine Benachrichtigung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="07bbe-142">This setting determines if a prompt will be displayed each time an early access program is removed.</span></span>

### <a name="my-previews"></a><span data-ttu-id="07bbe-143">Meine Vorschauversionen</span><span class="sxs-lookup"><span data-stu-id="07bbe-143">My previews</span></span>

<span data-ttu-id="07bbe-144">Die Liste der registrierten Early Access-Programme.</span><span class="sxs-lookup"><span data-stu-id="07bbe-144">The list of registered early access programs.</span></span> <span data-ttu-id="07bbe-145">Verwenden Sie die Schaltflächen `Add`, `Edit` und `Remove`, um die Sammlung der registrierten Programme zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="07bbe-145">Use the `Add`, `Edit` and `Remove` to manage the collection of registered programs.</span></span>

## <a name="diagnostic-settings"></a><span data-ttu-id="07bbe-146">Diagnoseeinstellungen</span><span class="sxs-lookup"><span data-stu-id="07bbe-146">Diagnostic settings</span></span>

![Diagnoseeinstellungen](images/FeatureToolSettings-Diagnostics.png)

### <a name="log-file"></a><span data-ttu-id="07bbe-148">Protokolldatei</span><span class="sxs-lookup"><span data-stu-id="07bbe-148">Log file</span></span>

<span data-ttu-id="07bbe-149">Zeigt den Pfad zur Datei des Diagnoseprotokolls an.</span><span class="sxs-lookup"><span data-stu-id="07bbe-149">Displays the path to the diagnostic log file.</span></span>

## <a name="see-also"></a><span data-ttu-id="07bbe-150">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="07bbe-150">See also</span></span>

- [<span data-ttu-id="07bbe-151">Willkommen beim Mixed Reality-Featuretool</span><span class="sxs-lookup"><span data-stu-id="07bbe-151">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)