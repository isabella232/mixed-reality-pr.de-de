---
title: Beispielhub
description: Übersicht über Beispielszenen im MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 212fc6e1489a22995241368a9bf4db96d206c44a
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144752"
---
# <a name="mrtk-examples-hub"></a><span data-ttu-id="4cf20-104">MRTK-Beispielhub</span><span class="sxs-lookup"><span data-stu-id="4cf20-104">MRTK Examples Hub</span></span>

![MRTK-Beispielhub](../images/examples-hub/MRTK_ExamplesHub.png)

<span data-ttu-id="4cf20-106">MrTK Examples Hub ist eine Unity-Szene, die das Erleben mehrerer Szenen vereinfacht.</span><span class="sxs-lookup"><span data-stu-id="4cf20-106">MRTK Examples Hub is a Unity scene that makes it easy to experience multiple scenes.</span></span> <span data-ttu-id="4cf20-107">Er verwendet das Szenensystem des MRTK, um die & zu laden.</span><span class="sxs-lookup"><span data-stu-id="4cf20-107">It uses MRTK's Scene System to load & unload the scenes.</span></span>

<span data-ttu-id="4cf20-108">**MRTKExamplesHub.unity** ist die Containerszene mit freigegebenen Komponenten, einschließlich ``MixedRealityToolkit`` und ``MixedRealityPlayspace`` .</span><span class="sxs-lookup"><span data-stu-id="4cf20-108">**MRTKExamplesHub.unity** is the container scene that has shared components including ``MixedRealityToolkit`` and ``MixedRealityPlayspace``.</span></span> <span data-ttu-id="4cf20-109">**Die MRTKExamplesHubMainMenu.unity-Szene** verfügt über die Cubeschaltflächen.</span><span class="sxs-lookup"><span data-stu-id="4cf20-109">**MRTKExamplesHubMainMenu.unity** scene has the cube buttons.</span></span>

## <a name="prerequisite"></a><span data-ttu-id="4cf20-110">Voraussetzung</span><span class="sxs-lookup"><span data-stu-id="4cf20-110">Prerequisite</span></span>

<span data-ttu-id="4cf20-111">Der MRTK-Beispielhub verwendet [den Szenenübergangsdienst und](../extensions/scene-transition-service.md) zugehörige Skripts.</span><span class="sxs-lookup"><span data-stu-id="4cf20-111">MRTK Examples Hub uses [Scene Transition Service](../extensions/scene-transition-service.md) and related scripts.</span></span> <span data-ttu-id="4cf20-112">Wenn Sie MRTK über Unity-Pakete verwenden, importieren Sie **microsoft.MixedReality.Toolkit.Unity.Extensions.x.x.x.unitypackage,** das Teil der Releasepakete [ist.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)</span><span class="sxs-lookup"><span data-stu-id="4cf20-112">If you are using MRTK through Unity packages, please import **Microsoft.MixedReality.Toolkit.Unity.Extensions.x.x.x.unitypackage** which is part of the [release packages](https://github.com/microsoft/MixedRealityToolkit-Unity/releases).</span></span> <span data-ttu-id="4cf20-113">Wenn Sie MRTK über den Repositoryklon verwenden, sollten Sie bereits den **Ordner MRTK/Erweiterungen** in Ihrem Projekt haben.</span><span class="sxs-lookup"><span data-stu-id="4cf20-113">If you are using MRTK through the repository clone, you should already have the **MRTK/Extensions** folder in your project.</span></span>

## <a name="mrtkexampleshub-scene-and-the-scene-system"></a><span data-ttu-id="4cf20-114">MRTKExamplesHub-Szene und Szenensystem</span><span class="sxs-lookup"><span data-stu-id="4cf20-114">MRTKExamplesHub scene and the scene system</span></span>

<span data-ttu-id="4cf20-115">Öffnen **Sie MRTKExamplesHub.unity** unter Es ist eine leere Szene mit `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` MixedRealityToolkit, MixedRealityPlayspace und LoadHubOnStartup.</span><span class="sxs-lookup"><span data-stu-id="4cf20-115">Open **MRTKExamplesHub.unity** which is located at `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` It is an empty scene with MixedRealityToolkit, MixedRealityPlayspace and LoadHubOnStartup.</span></span> <span data-ttu-id="4cf20-116">Diese Szene ist für die Verwendung des Szenensystems des MRTK konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="4cf20-116">This scene is configured to use MRTK's Scene System.</span></span> <span data-ttu-id="4cf20-117">Klicken `MixedRealitySceneSystem` Sie unter MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="4cf20-117">Click `MixedRealitySceneSystem` under MixedRealityToolkit.</span></span> <span data-ttu-id="4cf20-118">Die Informationen des Szenensystems werden im Inspektorbereich angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4cf20-118">It will display the Scene System's information in the Inspector panel.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Hierarchy.png" width="300" alt="Example Hub Hierarchy">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector1.png" width="450" alt="Inspector 1">

<span data-ttu-id="4cf20-119">Am unteren Rand des Inspektors wird die Liste der Szenen angezeigt, die im Szenensystemprofil definiert sind.</span><span class="sxs-lookup"><span data-stu-id="4cf20-119">On the bottom of the Inspector, it displays the list of the scenes defined in the Scene System Profile.</span></span> <span data-ttu-id="4cf20-120">Sie können auf die Szenennamen klicken, um sie zu laden/zu entladen.</span><span class="sxs-lookup"><span data-stu-id="4cf20-120">You can click the scene names to load/unload them.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector2.png" width="550" alt="Inspector 2">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem3.png" alt="Scene system 3"><span data-ttu-id="4cf20-121">Beispiel für das Laden _der MRTKExamplesHub-Szene_ durch Klicken auf den Szenennamen in der Liste.</span><span class="sxs-lookup"><span data-stu-id="4cf20-121">Example of loading _MRTKExamplesHub_ scene by clicking the scene name in the list.</span></span>
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem4.png" alt="Scene system 4"><span data-ttu-id="4cf20-122">Beispiel für das Laden _der HandInteractionExamples-Szene._</span><span class="sxs-lookup"><span data-stu-id="4cf20-122">Example of loading _HandInteractionExamples_ scene.</span></span>
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem5.png" alt="Scene system 5">
<span data-ttu-id="4cf20-123">Beispiel für das Laden mehrerer Szenen.</span><span class="sxs-lookup"><span data-stu-id="4cf20-123">Example of loading multiple scenes.</span></span>

## <a name="running-the-scene"></a><span data-ttu-id="4cf20-124">Ausführen der Szene</span><span class="sxs-lookup"><span data-stu-id="4cf20-124">Running the scene</span></span>

<span data-ttu-id="4cf20-125">Die Szene funktioniert sowohl im Unity-Spielmodus als auch auf dem Gerät.</span><span class="sxs-lookup"><span data-stu-id="4cf20-125">The scene works in both Unity's game mode and on device.</span></span> <span data-ttu-id="4cf20-126">Führen Sie die **MRTKExamplesHub-Szene** im Unity-Editor aus, und verwenden Sie die MRTK-Eingabesimulation, um mit den Szeneninhalten zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="4cf20-126">Run the **MRTKExamplesHub** scene in the Unity editor and use MRTK's input simulation to interact with the scene contents.</span></span> <span data-ttu-id="4cf20-127">Erstellen Sie zum Erstellen und Bereitstellen einfach **die MRTKExamplesHub-Szene** mit anderen Szenen, die in der Liste des Szenensystems enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="4cf20-127">To build and deploy, simply build **MRTKExamplesHub** scene with other scenes that are included in the Scene System's list.</span></span> <span data-ttu-id="4cf20-128">Der Inspektor erleichtert auch das Hinzufügen von Szenen zu den Buildeinstellungen.</span><span class="sxs-lookup"><span data-stu-id="4cf20-128">The inspector also makes it easy to add scenes to the Build Settings.</span></span> <span data-ttu-id="4cf20-129">Stellen Sie in den Gebäudeeinstellungen sicher, dass sich die **MRTKExamplesHub-Szene** am Index 0 oben in der Liste befindet.</span><span class="sxs-lookup"><span data-stu-id="4cf20-129">In the Building Settings, make sure **MRTKExamplesHub** scene is on the top of the list at index 0.</span></span>

<img src="../images/examples-hub/MRTK_ExamplesHub_BuildSettings.png" width="450" alt="Build settings">

## <a name="how-mrtkexampleshub-loads-a-scene"></a><span data-ttu-id="4cf20-130">Wie MRTKExamplesHub eine Szene lädt</span><span class="sxs-lookup"><span data-stu-id="4cf20-130">How MRTKExamplesHub loads a scene</span></span>

<span data-ttu-id="4cf20-131">In der **MRTKExamplesHub-Szene** finden Sie das ``ExamplesHubButton`` Prefab.</span><span class="sxs-lookup"><span data-stu-id="4cf20-131">In the **MRTKExamplesHub** scene, you can find the ``ExamplesHubButton`` prefab.</span></span>
<span data-ttu-id="4cf20-132">Das Prefab enthält ein **FrontPlate-Objekt,** das ``Interactable`` enthält.</span><span class="sxs-lookup"><span data-stu-id="4cf20-132">There is a **FrontPlate** object in the prefab which contains ``Interactable``.</span></span>
<span data-ttu-id="4cf20-133">Mithilfe des Interactable-Ereignisses und des ``OnClick()`` ``OnTouch()`` -Ereignisses wird die **LoadContent()-Funktion** des **LoadContentScene-Skripts** ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="4cf20-133">Using the Interactable's ``OnClick()`` and ``OnTouch()`` event, it triggers the **LoadContentScene** script's **LoadContent()** function.</span></span>
<span data-ttu-id="4cf20-134">Im Inspector des **LoadContentScene-Skripts** können Sie den zu ladenden Szenennamen definieren.</span><span class="sxs-lookup"><span data-stu-id="4cf20-134">In the **LoadContentScene** script's Inspector, you can define the scene name to load.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem6.png" alt="Scene system 6">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem8.png" width="450" alt="Scene System 8">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem7.png" width="450" alt="Scene System 7">

<span data-ttu-id="4cf20-135">Das Skript verwendet die LoadContent()-Funktion des Szenensystems, um die Szene zu laden.</span><span class="sxs-lookup"><span data-stu-id="4cf20-135">The script uses the Scene System's LoadContent() function to load the scene.</span></span>
<span data-ttu-id="4cf20-136">Weitere Informationen finden Sie auf der Seite [Szenensystem.](../scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="4cf20-136">Please refer to the [Scene System](../scene-system/scene-system-getting-started.md) page for more details.</span></span>

```c#
MixedRealityToolkit.SceneSystem.LoadContent(contentName, loadSceneMode);
```

## <a name="returning-to-the-main-menu-scene"></a><span data-ttu-id="4cf20-137">Zurückkehren zur Hauptmenüszene</span><span class="sxs-lookup"><span data-stu-id="4cf20-137">Returning to the main menu scene</span></span>

<span data-ttu-id="4cf20-138">Um zur Hauptmenüszene zurückzukehren (MRTKExamplesHubMainMenu-Szene), können Sie dieselbe Scene `LoadContent()` System-Methode verwenden.</span><span class="sxs-lookup"><span data-stu-id="4cf20-138">To return to the main menu scene (MRTKExamplesHubMainMenu scene), you can use the same Scene System `LoadContent()` method.</span></span> <span data-ttu-id="4cf20-139">**ToggleFeaturesPanelExamplesHub.prefab** stellt die Schaltfläche "Home" bereit, die das **Skript LoadContentScene** enthält.</span><span class="sxs-lookup"><span data-stu-id="4cf20-139">The **ToggleFeaturesPanelExamplesHub.prefab** provides the 'Home' button which contains the **LoadContentScene** script.</span></span> <span data-ttu-id="4cf20-140">Verwenden Sie dieses Prefab, oder geben Sie in jeder Szene eine benutzerdefinierte Startschaltfläche an, damit der Benutzer zur Hauptszene zurückkehren kann.</span><span class="sxs-lookup"><span data-stu-id="4cf20-140">Use this prefab or provide a custom home button in each scene to allow the user to return to the main scene.</span></span> <span data-ttu-id="4cf20-141">Sie können **toggleFeaturesPanelExamplesHub.prefab** in die **MRTKExamplesHub-Szene** einfügen, um sie immer sichtbar zu machen, da **MRTKExamplesHub** eine freigegebene Containerszene ist.</span><span class="sxs-lookup"><span data-stu-id="4cf20-141">One can put the **ToggleFeaturesPanelExamplesHub.prefab** in the **MRTKExamplesHub** scene to make it always visible since **MRTKExamplesHub** is a shared container scene.</span></span> <span data-ttu-id="4cf20-142">Stellen Sie sicher, dass **Sie ToggleFeaturesPanel.prefab** in jeder Beispielszene ausblenden/deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="4cf20-142">Make sure to hide/deactivate **ToggleFeaturesPanel.prefab** in each example scene.</span></span>

<img src="../images/examples-hub/MRTK_ExamplesHubToggleFeaturesPanel.png" alt="Toggle feature Panel">

<img src="../images/examples-hub/MRTK_ExamplesHubHomeButton.png" width="450" alt="Example Hub home button">

## <a name="adding-additional-buttons"></a><span data-ttu-id="4cf20-143">Hinzufügen zusätzlicher Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="4cf20-143">Adding additional buttons</span></span>

<span data-ttu-id="4cf20-144">Duplizieren (oder fügen Sie) _exampleHubButton-Prefabs_ im **CubeCollection-Objekt** hinzu, und klicken Sie im auf **Sammlung** `GridObjectCollection` aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="4cf20-144">In the **CubeCollection** object, duplicate (or add) _ExampleHubButton_ prefabs and click **Update Collection** in the `GridObjectCollection`.</span></span>
<span data-ttu-id="4cf20-145">Dadurch wird das Zylinderlayout basierend auf der neuen Gesamtanzahl von Schaltflächen aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="4cf20-145">This will update the cylinder layout based on the new total number of buttons.</span></span>
<span data-ttu-id="4cf20-146">Weitere Informationen finden Sie [auf der Seite](../ux-building-blocks/object-collection.md) Objektsammlung.</span><span class="sxs-lookup"><span data-stu-id="4cf20-146">Please refer to the [Object Collection](../ux-building-blocks/object-collection.md) page for more details.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem9.png" alt="Scene System 9">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem10.png" alt="Scene System 10">

<span data-ttu-id="4cf20-147">Aktualisieren Sie nach dem Hinzufügen der Schaltflächen den Szenennamen im **LoadContentScene-Skript** (siehe oben).</span><span class="sxs-lookup"><span data-stu-id="4cf20-147">After adding the buttons, update the scene name in the **LoadContentScene** script(explained above).</span></span>
<span data-ttu-id="4cf20-148">Fügen Sie dem Profil des Szenensystems zusätzliche Szenen hinzu.</span><span class="sxs-lookup"><span data-stu-id="4cf20-148">Add additional scenes to the Scene System's profile.</span></span>
