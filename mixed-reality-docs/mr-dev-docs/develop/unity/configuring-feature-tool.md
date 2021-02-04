---
title: Konfigurieren des Mixed Reality-Featuretools
description: Erfahren Sie, wie Sie Mixed Reality Unity-Pakete über das MR-Featuretool für die HoloLens- und VR-Entwicklung herunterladen und installieren.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: Aktuell, Tools, Erste Schritte, Grundlagen, Unity, Visual Studio, Toolkit, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Installation, Windows, HoloLens, Emulator, Unreal, OpenXR
ms.openlocfilehash: 4201f96ac87a6e9ab33607072c0d8f5f50df38a1
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2021
ms.locfileid: "99243929"
---
# <a name="configuring-the-mixed-reality-feature-tool"></a><span data-ttu-id="5b9c5-104">Konfigurieren des Mixed Reality-Featuretools</span><span class="sxs-lookup"><span data-stu-id="5b9c5-104">Configuring the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="5b9c5-105">Beim Verwenden des Mixed Reality-Featuretools haben Sie Zugriff auf drei verschiedene Kategorien von Einstellungen, die Sie nach Belieben anpassen können:</span><span class="sxs-lookup"><span data-stu-id="5b9c5-105">When using the Mixed Reality Feature Tool, you have access to three different settings categories that you can customize at will:</span></span>

* [<span data-ttu-id="5b9c5-106">Downloadeinstellungen</span><span class="sxs-lookup"><span data-stu-id="5b9c5-106">Download settings</span></span>](#download-settings)
* [<span data-ttu-id="5b9c5-107">Featureeinstellungen</span><span class="sxs-lookup"><span data-stu-id="5b9c5-107">Feature settings</span></span>](#feature-settings)
* [<span data-ttu-id="5b9c5-108">Importieren von Einstellungen</span><span class="sxs-lookup"><span data-stu-id="5b9c5-108">Import settings</span></span>](#import-settings)

![Einstellungen](images/FeatureToolSettings.png)

## <a name="download-settings"></a><span data-ttu-id="5b9c5-110">Downloadeinstellungen</span><span class="sxs-lookup"><span data-stu-id="5b9c5-110">Download settings</span></span>

### <a name="overwrite-existing-package-files"></a><span data-ttu-id="5b9c5-111">Vorhandene Paketdateien überschreiben</span><span class="sxs-lookup"><span data-stu-id="5b9c5-111">Overwrite existing package files</span></span>

<span data-ttu-id="5b9c5-112">Wenn Sie diese Einstellung aktivieren, werden die Paketdateien bei jedem Abrufen heruntergeladen.</span><span class="sxs-lookup"><span data-stu-id="5b9c5-112">Enabling this setting causes package files to be downloaded every time they're acquired.</span></span> 
* <span data-ttu-id="5b9c5-113">**Wir empfehlen, diese Option deaktiviert zu lassen, um den Verbrauch an Netzwerkbandbreite zu verringern**</span><span class="sxs-lookup"><span data-stu-id="5b9c5-113">**We recommend leaving this option disabled to reduce network bandwidth usage**</span></span>
* <span data-ttu-id="5b9c5-114">Standardmäßig werden zuvor erworbene Featurepaketdateien nicht erneut heruntergeladen.</span><span class="sxs-lookup"><span data-stu-id="5b9c5-114">By default, previously acquired package files aren't re-downloaded</span></span>

### <a name="package-cache"></a><span data-ttu-id="5b9c5-115">Paketcache</span><span class="sxs-lookup"><span data-stu-id="5b9c5-115">Package cache</span></span>

<span data-ttu-id="5b9c5-116">Ändern Sie diese Einstellung, um den Speicherort zu ändern, an dem heruntergeladene Featurepakete gespeichert werden.</span><span class="sxs-lookup"><span data-stu-id="5b9c5-116">Change this setting to update the location where feature packages are downloaded.</span></span>

> [!NOTE]
> <span data-ttu-id="5b9c5-117">Diese Einstellung ist in dieser Version **schreibgeschützt**.</span><span class="sxs-lookup"><span data-stu-id="5b9c5-117">This setting is **read-only** in this release.</span></span> <span data-ttu-id="5b9c5-118">In zukünftigen Versionen wird diese Einstellung möglicherweise konfigurierbar.</span><span class="sxs-lookup"><span data-stu-id="5b9c5-118">Future releases may make this setting configurable.</span></span>

## <a name="feature-settings"></a><span data-ttu-id="5b9c5-119">Featureeinstellungen</span><span class="sxs-lookup"><span data-stu-id="5b9c5-119">Feature settings</span></span>

### <a name="include-preview-releases"></a><span data-ttu-id="5b9c5-120">Vorabversionen einschließen</span><span class="sxs-lookup"><span data-stu-id="5b9c5-120">Include preview releases</span></span>

<span data-ttu-id="5b9c5-121">Aktivieren Sie diese Einstellung, um Vorschauversionen zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="5b9c5-121">Enable this setting to acquire preview releases.</span></span>
* <span data-ttu-id="5b9c5-122">Standardmäßig werden Vorschauversionen nicht im Mixed Reality-Featuretool angezeigt</span><span class="sxs-lookup"><span data-stu-id="5b9c5-122">By default, preview releases aren't shown in the Mixed Reality Feature Tool</span></span> 

> [!NOTE]
> <span data-ttu-id="5b9c5-123">Eine Vorschauversion ist dadurch gekennzeichnet, dass sie die Bezeichnung **"-preview"** in der Paketversion enthält.</span><span class="sxs-lookup"><span data-stu-id="5b9c5-123">A preview release is defined as containing the **"-preview"** designation in the package version.</span></span>

## <a name="import-settings"></a><span data-ttu-id="5b9c5-124">Importieren von Einstellungen</span><span class="sxs-lookup"><span data-stu-id="5b9c5-124">Import settings</span></span>

### <a name="replace-existing-package-files"></a><span data-ttu-id="5b9c5-125">Vorhandene Paketdateien ersetzen</span><span class="sxs-lookup"><span data-stu-id="5b9c5-125">Replace existing package files</span></span>

<span data-ttu-id="5b9c5-126">Standardmäßig entfernt das Mixed Reality-Featuretool vorherige Exemplare von Paketen, die importiert werden, um die Dateigröße und unnötige Berechnungen zu verringern.</span><span class="sxs-lookup"><span data-stu-id="5b9c5-126">By default, the Mixed Reality Feature Tool removes previous copies of the packages being imported to reduce the file size and unnecessary computations.</span></span> 
* <span data-ttu-id="5b9c5-127">Deaktivieren Sie diese Einstellung, wenn Sie alle Versionen behalten möchten.</span><span class="sxs-lookup"><span data-stu-id="5b9c5-127">Uncheck this setting to keep all versions</span></span>

### <a name="project-relative-import-path"></a><span data-ttu-id="5b9c5-128">Relativer Importpfad des Projekts</span><span class="sxs-lookup"><span data-stu-id="5b9c5-128">Project relative import path</span></span>

<span data-ttu-id="5b9c5-129">Ändern Sie diese Einstellung, um den Ordnerpfad des Projekts zu aktualisieren, in den Featurepakete beim Importieren kopiert werden.</span><span class="sxs-lookup"><span data-stu-id="5b9c5-129">Change this setting to update project folder path where feature packages are copied on import.</span></span> 
* <span data-ttu-id="5b9c5-130">Wenn der Projektordner beispielsweise **C:\GalaxyExplorer** ist, lautet der vollqualifizierte Importpfad **C:\GalaxyExplorer\Packages\MixedReality**.</span><span class="sxs-lookup"><span data-stu-id="5b9c5-130">For example, if the project folder is **C:\GalaxyExplorer**, the fully qualified import path will be **C:\GalaxyExplorer\Packages\MixedReality**.</span></span>

> [!NOTE]
> <span data-ttu-id="5b9c5-131">Diese Einstellung ist in dieser Version **schreibgeschützt**.</span><span class="sxs-lookup"><span data-stu-id="5b9c5-131">This setting is **read-only** in this release.</span></span> <span data-ttu-id="5b9c5-132">In zukünftigen Versionen wird diese Einstellung möglicherweise konfigurierbar.</span><span class="sxs-lookup"><span data-stu-id="5b9c5-132">Future releases may make this setting configurable.</span></span>

## <a name="see-also"></a><span data-ttu-id="5b9c5-133">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="5b9c5-133">See also</span></span>

- [<span data-ttu-id="5b9c5-134">Willkommen beim Mixed Reality-Featuretool</span><span class="sxs-lookup"><span data-stu-id="5b9c5-134">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)