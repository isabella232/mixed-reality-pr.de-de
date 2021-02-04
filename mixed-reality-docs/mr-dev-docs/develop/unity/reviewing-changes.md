---
title: Autorisieren von Projektänderungen
description: Erfahren Sie, wie Sie Projektänderungen mit dem MR-Featuretool für die HoloLens- und VR-Entwicklung autorisieren.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: Aktuell, Tools, Erste Schritte, Grundlagen, Unity, Visual Studio, Toolkit, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Installation, Windows, HoloLens, Emulator, Unreal, OpenXR
ms.openlocfilehash: b9e4f53c9a1e5503cfa92a612879be1971422acc
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2021
ms.locfileid: "99243908"
---
# <a name="authorizing-project-changes"></a><span data-ttu-id="cacbe-104">Autorisieren von Projektänderungen</span><span class="sxs-lookup"><span data-stu-id="cacbe-104">Authorizing project changes</span></span>

<span data-ttu-id="cacbe-105">Bevor Sie das Unity-Projekt ändern, müssen die Änderungen an den Manifest- und Projektdateien überprüft und genehmigt werden:</span><span class="sxs-lookup"><span data-stu-id="cacbe-105">Before modifying the Unity project, changes to the manifest and project files need to be reviewed and approved:</span></span>

![Anfordern von Autorisierung](images/FeatureToolApprovalRequest.png)

## <a name="manifest"></a><span data-ttu-id="cacbe-107">Manifest</span><span class="sxs-lookup"><span data-stu-id="cacbe-107">Manifest</span></span>

<span data-ttu-id="cacbe-108">Die vorgeschlagenen Manifeständerungen können in der Spalte **Manifest** auf der linken Seite angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="cacbe-108">The proposed manifest changes can be viewed in the **Manifest** column on the left.</span></span> <span data-ttu-id="cacbe-109">Der Inhalt ist genau das, was in das Projektmanifest geschrieben wird (**Packages/manifest.json**):</span><span class="sxs-lookup"><span data-stu-id="cacbe-109">The contents are exactly what will be written to the project manifest (**Packages/manifest.json**):</span></span>

![Manifestvorschau](images/ManifestPreview.png)

## <a name="files-to-be-copied-into-the-project"></a><span data-ttu-id="cacbe-111">Dateien, die in das Projekt kopiert werden sollen</span><span class="sxs-lookup"><span data-stu-id="cacbe-111">Files to be copied into the project</span></span>

<span data-ttu-id="cacbe-112">Im Abschnitt **Files to be copied into the project** (Dateien, die in das Projekt kopiert werden sollen) auf der rechten Seite listet die spezifischen Featurepaketdateien auf, die in das Unity-Projekt kopiert werden sollen:</span><span class="sxs-lookup"><span data-stu-id="cacbe-112">The **Files to be copied into the project** section on the right lists the specific feature package files that will be copied into the Unity project:</span></span>

![Manifestvorschau mit Dateien, die kopiert werden sollen](images/FilesToCopy.png)

## <a name="compare-manifests"></a><span data-ttu-id="cacbe-114">Vergleichen von Manifesten</span><span class="sxs-lookup"><span data-stu-id="cacbe-114">Compare manifests</span></span>

<span data-ttu-id="cacbe-115">Sie können einen detaillierten Vergleich aller vorgeschlagenen Änderungen anzeigen, indem Sie **Compare** (Vergleichen) auswählen:</span><span class="sxs-lookup"><span data-stu-id="cacbe-115">You can see a detailed side-by-side comparison of all proposed changes by selecting **Compare**:</span></span>

![Vergleichen von Manifesten](images/FeatureToolCompareManifest.png)

## <a name="approving-changes"></a><span data-ttu-id="cacbe-117">Genehmigen von Änderungen</span><span class="sxs-lookup"><span data-stu-id="cacbe-117">Approving changes</span></span>

<span data-ttu-id="cacbe-118">Wenn die vorgeschlagenen Änderungen genehmigt werden, werden die aufgelisteten Dateien in das Unity-Projekt kopiert, und das Manifest wird mit Verweisen auf diese Dateien aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="cacbe-118">When the proposed changes are approved, the listed files will be copied into the Unity project and the manifest will be updated with references to these files.</span></span>

> [!NOTE]
> <span data-ttu-id="cacbe-119">Die Featurepaketdateien (TGZ) sollten der Quellcodeverwaltung hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="cacbe-119">The feature package (\*.tgz) files should be added to source control.</span></span> <span data-ttu-id="cacbe-120">Auf sie wird mithilfe eines relativen Pfads verwiesen, um Entwicklungsteams das einfache Teilen von Features und Manifeständerungen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="cacbe-120">They are referenced using a relative path to enable development teams to easily share features and manifest changes.</span></span>

 <span data-ttu-id="cacbe-121">Im Rahmen der Änderungen wird die aktuelle **manifest.json**-Datei gesichert.</span><span class="sxs-lookup"><span data-stu-id="cacbe-121">As part of the modifications, the current **manifest.json** file will be backed up.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cacbe-122">Wenn Sie Manifestsicherungen anzeigen, trägt die älteste Sicherung den Namen **manifest.json.backup**.</span><span class="sxs-lookup"><span data-stu-id="cacbe-122">When viewing the manifest backups, the oldest will be called **manifest.json.backup**.</span></span> <span data-ttu-id="cacbe-123">Neuere Sicherungen werden mit einem Zahlenwert ergänzt, beginnend bei (0).</span><span class="sxs-lookup"><span data-stu-id="cacbe-123">Newer backups will be annotated with a numeric value, beginning with zero (0).</span></span>

## <a name="going-back-to-the-previous-step"></a><span data-ttu-id="cacbe-124">Zurückwechseln zum vorherigen Schritt</span><span class="sxs-lookup"><span data-stu-id="cacbe-124">Going back to the previous step</span></span>

<span data-ttu-id="cacbe-125">Wenn Sie Änderungen an Ihrer Featureauswahl vornehmen müssen, verwenden Sie **Go Back** (Zurück), um zum Schritt [import](importing-features.md) zurückzukehren.</span><span class="sxs-lookup"><span data-stu-id="cacbe-125">If you need to make changes to your feature selections, use **Go Back** to return to the [import](importing-features.md) step.</span></span>

## <a name="see-also"></a><span data-ttu-id="cacbe-126">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="cacbe-126">See also</span></span>

- [<span data-ttu-id="cacbe-127">Willkommen beim Mixed Reality-Featuretool</span><span class="sxs-lookup"><span data-stu-id="cacbe-127">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
- [<span data-ttu-id="cacbe-128">Importieren ausgewählter Pakete</span><span class="sxs-lookup"><span data-stu-id="cacbe-128">Importing selected packages</span></span>](importing-features.md)
