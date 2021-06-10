---
title: Migrationsfenster
description: Dokumentation zum Migrieren zu einem Update im MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: a6e268dd28be2a3d485f937ec5b5ce6b1f29851f
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647124"
---
# <a name="migration-window"></a><span data-ttu-id="7d1c1-104">Migrationszeitfenster</span><span class="sxs-lookup"><span data-stu-id="7d1c1-104">Migration window</span></span>

<span data-ttu-id="7d1c1-105">Wenn das MRTK geändert wird, werden einige Komponenten möglicherweise veraltet, und es werden Ersatzkomponenten eingeführt.</span><span class="sxs-lookup"><span data-stu-id="7d1c1-105">As the MRTK undergoes changes, some components might get deprecated and replacements will get introduced.</span></span>
<span data-ttu-id="7d1c1-106">Das Migrationsfenster ist ein Tool, mit dem Benutzer automatisch eine Teilmenge dieser veralteten Komponenten zu den neuen Ersetzungen migrieren können.</span><span class="sxs-lookup"><span data-stu-id="7d1c1-106">The migration window is a tool that helps users to automatically migrate a subset of those deprecated components to the new replacements.</span></span>

![Migrationszeitfenster](../images/migration-window/MRTK_Migration_Window.png)

## <a name="usage"></a><span data-ttu-id="7d1c1-108">Verwendung</span><span class="sxs-lookup"><span data-stu-id="7d1c1-108">Usage</span></span>

<span data-ttu-id="7d1c1-109">Um das Fenster zu öffnen, wählen **Sie** Mixed Reality Toolkit Utilities Migration Window  >  **(Migrationsfenster**  >  **für Toolkit-Hilfsprogramme)**  >  **aus.**</span><span class="sxs-lookup"><span data-stu-id="7d1c1-109">To open the window, select **Mixed Reality** > **Toolkit** > **Utilities** > **Migration Window**.</span></span> <span data-ttu-id="7d1c1-110">Sobald das Migrationsfenster geöffnet ist, können die Navigationsregisterkarte für den Auswahlmodus aktiviert werden, indem Sie die komponentenspezifische Implementierung des Migrationshandlers auswählen.</span><span class="sxs-lookup"><span data-stu-id="7d1c1-110">Once the migration window is open, the selection mode navigation tabs can be enabled by choosing the component specific implementation of the migration handler.</span></span>  

![Migrationsauswahlmodi](../images/migration-window/MRTK_Migration_Modes.png)

### <a name="object-mode"></a><span data-ttu-id="7d1c1-112">Objektmodus</span><span class="sxs-lookup"><span data-stu-id="7d1c1-112">Object mode</span></span>

<span data-ttu-id="7d1c1-113">Wenn Sie die Registerkarte Objekte auswählen, wird das ObjektFeld aktiviert, in das der Benutzer alle Game-Objekte aus der aktuell geöffneten Szene oder prefabs aus dem zu migrierenden Projektordner ziehen und ablegen kann.</span><span class="sxs-lookup"><span data-stu-id="7d1c1-113">Selecting the objects tab enables the object Field to where the user can drag and drop any Game objects from the currently open scene or prefabs from the project folder to be migrated.</span></span>
<span data-ttu-id="7d1c1-114">Durch Drücken der *Schaltfläche entfernen (-),* die rechts neben dem aufgelisteten Objekt angezeigt wird, wird das Objekt aus der Auswahlliste entfernt.</span><span class="sxs-lookup"><span data-stu-id="7d1c1-114">Pressing the remove *(-)* button displayed at the right side of the listed object removes the object from the selection list.</span></span>

<span data-ttu-id="7d1c1-115">Sobald alle gewünschten Objekte in der Liste  enthalten sind, werden durch Drücken der Schaltfläche Migrieren die änderungen angewendet, die für die ausgewählte Implementierung des Migrationshandlers erforderlich sind, auf alle Komponenten in der Auswahl, die mit der Implementierung übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="7d1c1-115">Once all the desired objects are in the list, pressing the *Migrate* button will apply the changes required by the chosen migration handler implementation to all components in the selection that match the implementation.</span></span>

![Auswahlmigration](../images/migration-window/MRTK_Object_Migration.png)

### <a name="scene-mode"></a><span data-ttu-id="7d1c1-117">Szenenmodus</span><span class="sxs-lookup"><span data-stu-id="7d1c1-117">Scene mode</span></span>

<span data-ttu-id="7d1c1-118">Ermöglicht dem Benutzer das Ziehen und Ablegen von Szenenobjekten, die zu migrierende Objekte enthalten.</span><span class="sxs-lookup"><span data-stu-id="7d1c1-118">Allows user to drag and drop scene assets containing objects to be migrated.</span></span>

![Auswählen von Szenen für die Migration](../images/migration-window/MRTK_Scene_Selection.png)

### <a name="project-mode"></a><span data-ttu-id="7d1c1-120">Projektmodus</span><span class="sxs-lookup"><span data-stu-id="7d1c1-120">Project mode</span></span>

<span data-ttu-id="7d1c1-121">Wenn Sie auf *die Schaltfläche* Migrieren klicken, wird die Komponente aktualisiert, auf die die Implementierung des Migrationshandlers für alle Prefabs und Szenen im Projekt ausgerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="7d1c1-121">Pressing the *Migrate* button will update the component targeted by the migration handler implementation for all prefabs and scenes in the project.</span></span>

![Migrieren eines vollständigen Projekts](../images/migration-window/MRTK_Project_Migration.png)

## <a name="see-also"></a><span data-ttu-id="7d1c1-123">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="7d1c1-123">See also</span></span>

- [<span data-ttu-id="7d1c1-124">Aktualisieren von früheren Versionen</span><span class="sxs-lookup"><span data-stu-id="7d1c1-124">Updating from earlier versions</span></span>](../../updates-deployment/updating.md)
- [<span data-ttu-id="7d1c1-125">Microsoft Mixed Reality Toolkit-Releases</span><span class="sxs-lookup"><span data-stu-id="7d1c1-125">Microsoft Mixed Reality Toolkit releases</span></span>](../../release-notes/mrtk-26-release-notes.md)
- [<span data-ttu-id="7d1c1-126">MRTK-Roadmap</span><span class="sxs-lookup"><span data-stu-id="7d1c1-126">MRTK roadmap</span></span>](../../roadmap.md)
