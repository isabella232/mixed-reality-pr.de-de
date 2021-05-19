---
title: 'Szenensystem: Erste Schritte'
description: Landing Page für Szenensystem mit MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 205b89d4defdeb5418a8a82896551d681cccde3d
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144307"
---
# <a name="scene-system-overview"></a><span data-ttu-id="21c2c-104">Szenensystemübersicht</span><span class="sxs-lookup"><span data-stu-id="21c2c-104">Scene system overview</span></span>

## <a name="when-to-use-the-scene-system"></a><span data-ttu-id="21c2c-105">Wann das Szenensystem verwendet werden soll</span><span class="sxs-lookup"><span data-stu-id="21c2c-105">When to use the scene system</span></span>

<span data-ttu-id="21c2c-106">Wenn Ihr Projekt aus einer einzelnen Szene besteht, ist das Szenensystem wahrscheinlich nicht erforderlich.</span><span class="sxs-lookup"><span data-stu-id="21c2c-106">If your project consists of a single scene, the Scene System probably isn't necessary.</span></span> <span data-ttu-id="21c2c-107">Dies ist besonders nützlich, wenn mindestens eine der folgenden Bedingungen zutrifft:</span><span class="sxs-lookup"><span data-stu-id="21c2c-107">It is most useful when one or more of the following are true:</span></span>

- <span data-ttu-id="21c2c-108">Ihr Projekt verfügt über mehrere Szenen.</span><span class="sxs-lookup"><span data-stu-id="21c2c-108">Your project has multiple scenes.</span></span>
- <span data-ttu-id="21c2c-109">Sie sind es gewohnt, einzelne Szenen zu laden, aber die Art und Weise, wie sie die MixedRealityToolkit-Instanz zerstört, gefällt Ihnen nicht.</span><span class="sxs-lookup"><span data-stu-id="21c2c-109">You're used to single scene loading, but you don't like the way it destroys the MixedRealityToolkit instance.</span></span>
- <span data-ttu-id="21c2c-110">Sie möchten eine einfache Möglichkeit haben, mehrere Szenen additiv zu laden, um Ihre Erfahrung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="21c2c-110">You want a simple way to additively load multiple scenes to construct your experience.</span></span>
- <span data-ttu-id="21c2c-111">Sie möchten eine einfache Möglichkeit zum Nachverfolgen von Ladevorgängen oder eine einfache Möglichkeit, die Szenenaktivierung für mehrere Szenen zu steuern, die gleichzeitig geladen werden.</span><span class="sxs-lookup"><span data-stu-id="21c2c-111">You want a simple way to keep track of load operations in progress or a simple way to control scene activation for multiple scenes being loaded at once.</span></span>
- <span data-ttu-id="21c2c-112">Sie möchten die Beleuchtung über alle Szenen hinweg konsistent und vorhersagbar halten.</span><span class="sxs-lookup"><span data-stu-id="21c2c-112">You want to keep lighting consistent and predictable across all your scenes.</span></span>

## <a name="scene-system-resources"></a><span data-ttu-id="21c2c-113">Szenensystemressourcen</span><span class="sxs-lookup"><span data-stu-id="21c2c-113">Scene System Resources</span></span>

<span data-ttu-id="21c2c-114">Standardmäßig verwendet das Szenensystem ein Szenenobjektpaar (DefaultManagerScene- und DefaultLighting-Szene).</span><span class="sxs-lookup"><span data-stu-id="21c2c-114">By default, the Scene System utilizes a pair of scene objects (DefaultManagerScene and DefaultLighting scene).</span></span> <span data-ttu-id="21c2c-115">Wenn eine dieser Szenen nicht gefunden werden kann, wird im Profilinspektor des Szenensystems eine Meldung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="21c2c-115">If either of these scenes cannot be located, a message will appear in the Scene System profile inspector.</span></span>

![Meldung zu Standardressourcen](../images/scene-system/DefaultResourcesMessage.png)

><span data-ttu-id="21c2c-117">! [Hinweis] Wenn das Projekt benutzerdefinierte Manager- und Beleuchtungsszenen verwendet, kann diese Meldung sicher ignoriert werden.</span><span class="sxs-lookup"><span data-stu-id="21c2c-117">![Note] If the project is using custom manager and lighting scenes, this message can be safely ignored.</span></span>

<span data-ttu-id="21c2c-118">In den folgenden Abschnitten wird beschrieben, wie Sie diese Meldung auflösen, je nachdem, welche Methode zum Importieren des Mixed Reality Wurde.</span><span class="sxs-lookup"><span data-stu-id="21c2c-118">The following sections describe now to resolve this message, based on which method was used to import the Mixed Reality Toolkit.</span></span>

### <a name="unity-package-manager-upm"></a><span data-ttu-id="21c2c-119">Unity Paket-Manager (UPM)</span><span class="sxs-lookup"><span data-stu-id="21c2c-119">Unity Package Manager (UPM)</span></span>

<span data-ttu-id="21c2c-120">In den Mixed Reality Toolkit-UPM-Paketen werden die Szenensystemressourcen als Beispiel gepackt.</span><span class="sxs-lookup"><span data-stu-id="21c2c-120">In the Mixed Reality Toolkit UPM packages, the scene system resources are packaged as a sample.</span></span> <span data-ttu-id="21c2c-121">Da UPM-Pakete unveränderlich sind, kann Unity die erforderliche Szenendatei nur öffnen, wenn sie explizit in das Projekt importiert werden.</span><span class="sxs-lookup"><span data-stu-id="21c2c-121">Due to UPM packages being immutable, Unity is unable to open the necessary scene file unless they are explicitly imported into the project.</span></span>

<span data-ttu-id="21c2c-122">Führen Sie zum Importieren die folgenden Schritte aus:</span><span class="sxs-lookup"><span data-stu-id="21c2c-122">To import use the following steps:</span></span>

- <span data-ttu-id="21c2c-123">Fenster   >  **auswählen Paket-Manager**</span><span class="sxs-lookup"><span data-stu-id="21c2c-123">Select **Window** > **Package Manager**</span></span>
- <span data-ttu-id="21c2c-124">Wählen Sie **Mixed Reality Toolkit Foundation aus.**</span><span class="sxs-lookup"><span data-stu-id="21c2c-124">Select **Mixed Reality Toolkit Foundation**</span></span>
- <span data-ttu-id="21c2c-125">Suchen von **Szenensystemressourcen** im Abschnitt **"Beispiele"**</span><span class="sxs-lookup"><span data-stu-id="21c2c-125">Locate **Scene System Resources** in the **Samples** section</span></span>

  ![Importieren von Szenensystemressourcen](../images/scene-system/UpmImportSceneSystemResources.png)

- <span data-ttu-id="21c2c-127">Wählen Sie **Importieren aus.**</span><span class="sxs-lookup"><span data-stu-id="21c2c-127">Select **Import**</span></span>

### <a name="asset-unitypackage-files"></a><span data-ttu-id="21c2c-128">Assetdateien (UNITYPACKAGE)</span><span class="sxs-lookup"><span data-stu-id="21c2c-128">Asset (.unitypackage) files</span></span>

<span data-ttu-id="21c2c-129">Wenn der Ordner SceneSystemResources gelöscht oder während des Imports deaktiviert wurde, kann er mit den folgenden Schritten wiederhergestellt werden:</span><span class="sxs-lookup"><span data-stu-id="21c2c-129">If the SceneSystemResources folder has been deleted, or was deselected during import, it can be recovered using the following steps:</span></span>

- <span data-ttu-id="21c2c-130">Auswählen **von "Assets** Import Package Custom  >    >  **Package" (Benutzerdefiniertes Paket** importieren)</span><span class="sxs-lookup"><span data-stu-id="21c2c-130">Select **Assets** > **Import Package** > **Custom Package**</span></span>
- <span data-ttu-id="21c2c-131">Öffnen Sie das **Paket Microsoft.MixedReality.Toolkit.Foundation.**</span><span class="sxs-lookup"><span data-stu-id="21c2c-131">Open the **Microsoft.MixedReality.Toolkit.Foundation** package</span></span>
- <span data-ttu-id="21c2c-132">Stellen Sie sicher, dass **Services/SceneSystem/SceneSystemResources** und alle untergeordneten Optionen ausgewählt sind.</span><span class="sxs-lookup"><span data-stu-id="21c2c-132">Ensure that **Services/SceneSystem/SceneSystemResources** and all child options are selected</span></span>

  ![Erneutes Importieren von Szenensystemressourcen](../images/scene-system/ReimportSceneSystemResources.png)

- <span data-ttu-id="21c2c-134">Wählen Sie **Importieren aus.**</span><span class="sxs-lookup"><span data-stu-id="21c2c-134">Select **Import**</span></span>

## <a name="how-to-use-the-scene-system"></a><span data-ttu-id="21c2c-135">Verwenden des Szenensystems</span><span class="sxs-lookup"><span data-stu-id="21c2c-135">How to use the scene system</span></span>

- [<span data-ttu-id="21c2c-136">Szenentypen</span><span class="sxs-lookup"><span data-stu-id="21c2c-136">Scene Types</span></span>](scene-system-scene-types.md)
- [<span data-ttu-id="21c2c-137">Laden von Inhaltsszenen</span><span class="sxs-lookup"><span data-stu-id="21c2c-137">Content Scene Loading</span></span>](scene-system-content-loading.md)
- [<span data-ttu-id="21c2c-138">Überwachen des Ladens von Inhalten</span><span class="sxs-lookup"><span data-stu-id="21c2c-138">Monitoring Content Loading</span></span>](scene-system-load-progress.md)
- [<span data-ttu-id="21c2c-139">Laden von Beleuchtungsszenen</span><span class="sxs-lookup"><span data-stu-id="21c2c-139">Lighting Scene Loading</span></span>](scene-system-lighting-scenes.md)

## <a name="editor-settings"></a><span data-ttu-id="21c2c-140">Editor-Einstellungen</span><span class="sxs-lookup"><span data-stu-id="21c2c-140">Editor settings</span></span>

<span data-ttu-id="21c2c-141">Standardmäßig erzwingt das Szenensystem mehrere Verhaltensweisen im Unity-Editor.</span><span class="sxs-lookup"><span data-stu-id="21c2c-141">By default, the Scene System enforces several behaviors in the Unity editor.</span></span> <span data-ttu-id="21c2c-142">Wenn Sie eines dieser Verhaltensweisen mit vielen Händen finden, können sie im Abschnitt **Editoreinstellungen** Ihres Szenensystemprofils deaktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="21c2c-142">If you find any of these behaviors heavy-handed, they can be disabled in the **Editor Settings** section of your Scene System profile.</span></span>

- <span data-ttu-id="21c2c-143">`Editor Manage Build Settings:` Wenn true, aktualisiert der Dienst Ihre Buildeinstellungen automatisch und stellt sicher, dass alle Manager-, Beleuchtungs- und Inhaltsszenen hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="21c2c-143">`Editor Manage Build Settings:` If true, the service will update your build settings automatically, ensuring that all manager, lighting and content scenes are added.</span></span> <span data-ttu-id="21c2c-144">Deaktivieren Sie diese Option, wenn Sie die vollständige Kontrolle über die Buildeinstellungen wünschen.</span><span class="sxs-lookup"><span data-stu-id="21c2c-144">Disable this if you want total control over build settings.</span></span>

- <span data-ttu-id="21c2c-145">`Editor Enforce Scene Order:` Wenn true, stellt der Dienst sicher, dass die Manager-Szene zuerst in der Szenenhierarchie angezeigt wird, gefolgt von Beleuchtung und Inhalt.</span><span class="sxs-lookup"><span data-stu-id="21c2c-145">`Editor Enforce Scene Order:` If true, the service will ensure that the manager scene is displayed first in scene hierarchy, followed by lighting and then content.</span></span> <span data-ttu-id="21c2c-146">Deaktivieren Sie diese Option, wenn Sie die gesamte Kontrolle über die Szenenhierarchie wünschen.</span><span class="sxs-lookup"><span data-stu-id="21c2c-146">Disable this if you want total control over scene hierarchy.</span></span>

- <span data-ttu-id="21c2c-147">`Editor Manage Loaded Scenes:` Bei "true" stellt der Dienst sicher, dass die Manager-, Inhalts- und Beleuchtungsszenen immer geladen werden.</span><span class="sxs-lookup"><span data-stu-id="21c2c-147">`Editor Manage Loaded Scenes:` If true, the service will ensure that the manager, content and lighting scenes are always loaded.</span></span> <span data-ttu-id="21c2c-148">Deaktivieren Sie diese Option, wenn Sie die vollständige Kontrolle darüber haben möchten, welche Szenen im Editor geladen werden.</span><span class="sxs-lookup"><span data-stu-id="21c2c-148">Disable if you want total control over which scenes are loaded in editor.</span></span>

- <span data-ttu-id="21c2c-149">`Editor Enforce Lighting Scene Types:` Bei "true" stellt der Dienst sicher, dass nur die in definierten beleuchtungsbezogenen `PermittedLightingSceneComponentTypes` Komponenten in Beleuchtungsszenen zulässig sind.</span><span class="sxs-lookup"><span data-stu-id="21c2c-149">`Editor Enforce Lighting Scene Types:` If true, the service will ensure that only the lighting-related components defined in `PermittedLightingSceneComponentTypes` are allowed in lighting scenes.</span></span> <span data-ttu-id="21c2c-150">Deaktivieren Sie diese Option, wenn Sie die vollständige Kontrolle über den Inhalt von Beleuchtungsszenen wünschen.</span><span class="sxs-lookup"><span data-stu-id="21c2c-150">Disable if you want total control over the content of lighting scenes.</span></span>

![Einstellungen des Szenensystem-Editors](../images/scene-system/MRTK_SceneSystemProfileEditorSettings.PNG)
