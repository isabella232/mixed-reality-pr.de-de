---
title: MRTK-Beispiele-Hub
description: Übersicht über Beispielszenen im MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: b7a55e46b2c283b5a75395b9e99874af6020a171
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2021
ms.locfileid: "114282008"
---
# <a name="mrtk-examples-hub"></a><span data-ttu-id="39578-104">MRTK-Beispiele-Hub</span><span class="sxs-lookup"><span data-stu-id="39578-104">MRTK Examples Hub</span></span>

![MRTK-Beispiele-Hub](../images/examples-hub/MRTK_ExamplesHub.png)

<span data-ttu-id="39578-106">MRTK Examples Hub ist eine Unity-Szene, die es einfach macht, mehrere Szenen zu erleben.</span><span class="sxs-lookup"><span data-stu-id="39578-106">MRTK Examples Hub is a Unity scene that makes it easy to experience multiple scenes.</span></span> <span data-ttu-id="39578-107">Es verwendet das Szenensystem des MRTK, um die Szenen zu laden & zu entladen.</span><span class="sxs-lookup"><span data-stu-id="39578-107">It uses MRTK's Scene System to load & unload the scenes.</span></span>

<span data-ttu-id="39578-108">**MRTKExamplesHub.unity** ist die Containerszene, die über gemeinsam genutzte Komponenten wie ``MixedRealityToolkit`` und ``MixedRealityPlayspace`` verfügt.</span><span class="sxs-lookup"><span data-stu-id="39578-108">**MRTKExamplesHub.unity** is the container scene that has shared components including ``MixedRealityToolkit`` and ``MixedRealityPlayspace``.</span></span> <span data-ttu-id="39578-109">**MRTKExamplesHubMainMenu.unity-Szene** verfügt über die Cubeschaltflächen.</span><span class="sxs-lookup"><span data-stu-id="39578-109">**MRTKExamplesHubMainMenu.unity** scene has the cube buttons.</span></span>

## <a name="prerequisite"></a><span data-ttu-id="39578-110">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="39578-110">Prerequisite</span></span>

<span data-ttu-id="39578-111">Der MRTK-Beispielhub verwendet [den Scene Transition Service](../extensions/scene-transition-service.md) und zugehörige Skripts.</span><span class="sxs-lookup"><span data-stu-id="39578-111">MRTK Examples Hub uses [Scene Transition Service](../extensions/scene-transition-service.md) and related scripts.</span></span> <span data-ttu-id="39578-112">Wenn Sie MRTK über Unity-Pakete verwenden, importieren Sie **Microsoft.MixedReality.Toolkit.Unity.Extensions.x.x.x.unitypackage,** das Teil der [Releasepakete](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)ist.</span><span class="sxs-lookup"><span data-stu-id="39578-112">If you are using MRTK through Unity packages, please import **Microsoft.MixedReality.Toolkit.Unity.Extensions.x.x.x.unitypackage** which is part of the [release packages](https://github.com/microsoft/MixedRealityToolkit-Unity/releases).</span></span> <span data-ttu-id="39578-113">Wenn Sie MRTK über den Repositoryklon verwenden, sollten Sie bereits über den Ordner **MRTK/Extensions** in Ihrem Projekt verfügen.</span><span class="sxs-lookup"><span data-stu-id="39578-113">If you are using MRTK through the repository clone, you should already have the **MRTK/Extensions** folder in your project.</span></span>

## <a name="mrtkexampleshub-scene-and-the-scene-system"></a><span data-ttu-id="39578-114">MRTKExamplesHub-Szene und das Szenensystem</span><span class="sxs-lookup"><span data-stu-id="39578-114">MRTKExamplesHub scene and the scene system</span></span>

<span data-ttu-id="39578-115">Öffnen Sie **MRTKExamplesHub.unity.** `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` Dies ist eine leere Szene mit MixedRealityToolkit, MixedRealityPlayspace und LoadHubOnStartup.</span><span class="sxs-lookup"><span data-stu-id="39578-115">Open **MRTKExamplesHub.unity** which is located at `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` It is an empty scene with MixedRealityToolkit, MixedRealityPlayspace and LoadHubOnStartup.</span></span> <span data-ttu-id="39578-116">Diese Szene ist für die Verwendung des Szenensystems von MRTK konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="39578-116">This scene is configured to use MRTK's Scene System.</span></span> <span data-ttu-id="39578-117">Klicken Sie `MixedRealitySceneSystem` unter MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="39578-117">Click `MixedRealitySceneSystem` under MixedRealityToolkit.</span></span> <span data-ttu-id="39578-118">Im Bereich Inspektor werden die Informationen des Szenensystems angezeigt.</span><span class="sxs-lookup"><span data-stu-id="39578-118">It will display the Scene System's information in the Inspector panel.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Hierarchy.png" width="300" alt="Example Hub Hierarchy">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector1.png" width="450" alt="Inspector 1">

<span data-ttu-id="39578-119">Am unteren Rand des Inspektors wird die Liste der Szenen angezeigt, die im Szenensystemprofil definiert sind.</span><span class="sxs-lookup"><span data-stu-id="39578-119">On the bottom of the Inspector, it displays the list of the scenes defined in the Scene System Profile.</span></span> <span data-ttu-id="39578-120">Sie können auf die Szenennamen klicken, um sie zu laden bzw. zu entladen.</span><span class="sxs-lookup"><span data-stu-id="39578-120">You can click the scene names to load/unload them.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector2.png" width="550" alt="Inspector 2">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem3.png" alt="Scene system 3"><span data-ttu-id="39578-121">Beispiel für das Laden der _MRTKExamplesHub-Szene_ durch Klicken auf den Szenennamen in der Liste.</span><span class="sxs-lookup"><span data-stu-id="39578-121">Example of loading _MRTKExamplesHub_ scene by clicking the scene name in the list.</span></span>
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem4.png" alt="Scene system 4"><span data-ttu-id="39578-122">Beispiel für das Laden der _HandInteractionExamples-Szene._</span><span class="sxs-lookup"><span data-stu-id="39578-122">Example of loading _HandInteractionExamples_ scene.</span></span>
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem5.png" alt="Scene system 5">
<span data-ttu-id="39578-123">Beispiel für das Laden mehrerer Szenen.</span><span class="sxs-lookup"><span data-stu-id="39578-123">Example of loading multiple scenes.</span></span>

## <a name="running-the-scene"></a><span data-ttu-id="39578-124">Ausführen der Szene</span><span class="sxs-lookup"><span data-stu-id="39578-124">Running the scene</span></span>

<span data-ttu-id="39578-125">Die Szene funktioniert sowohl im Unity-Spielmodus als auch auf dem Gerät.</span><span class="sxs-lookup"><span data-stu-id="39578-125">The scene works in both Unity's game mode and on device.</span></span> <span data-ttu-id="39578-126">Führen Sie die **MRTKExamplesHub-Szene** im Unity-Editor aus, und verwenden Sie die MRTK-Eingabesimulation, um mit den Szeneninhalten zu interagieren.</span><span class="sxs-lookup"><span data-stu-id="39578-126">Run the **MRTKExamplesHub** scene in the Unity editor and use MRTK's input simulation to interact with the scene contents.</span></span> <span data-ttu-id="39578-127">Erstellen Sie zum Erstellen und Bereitstellen einfach **die MRTKExamplesHub-Szene** mit anderen Szenen, die in der Liste des Szenensystems enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="39578-127">To build and deploy, simply build **MRTKExamplesHub** scene with other scenes that are included in the Scene System's list.</span></span> <span data-ttu-id="39578-128">Der Inspektor erleichtert auch das Hinzufügen von Szenen zum Build Einstellungen.</span><span class="sxs-lookup"><span data-stu-id="39578-128">The inspector also makes it easy to add scenes to the Build Settings.</span></span> <span data-ttu-id="39578-129">Stellen Sie im Einstellungen Building sicher, dass sich die **MRTKExamplesHub-Szene** am Index 0 oben in der Liste befindet.</span><span class="sxs-lookup"><span data-stu-id="39578-129">In the Building Settings, make sure **MRTKExamplesHub** scene is on the top of the list at index 0.</span></span>

<img src="../images/examples-hub/MRTK_ExamplesHub_BuildSettings.png" width="450" alt="Build settings">

## <a name="how-mrtkexampleshub-loads-a-scene"></a><span data-ttu-id="39578-130">Wie MRTKExamplesHub eine Szene lädt</span><span class="sxs-lookup"><span data-stu-id="39578-130">How MRTKExamplesHub loads a scene</span></span>

<span data-ttu-id="39578-131">In der **MRTKExamplesHub-Szene** finden Sie das ``ExamplesHubButton`` Prefab.</span><span class="sxs-lookup"><span data-stu-id="39578-131">In the **MRTKExamplesHub** scene, you can find the ``ExamplesHubButton`` prefab.</span></span>
<span data-ttu-id="39578-132">Das Prefab enthält ein **FrontPlate-Objekt,** das ``Interactable`` enthält.</span><span class="sxs-lookup"><span data-stu-id="39578-132">There is a **FrontPlate** object in the prefab which contains ``Interactable``.</span></span>
<span data-ttu-id="39578-133">Mithilfe des Interactable-Ereignisses und des ``OnClick()`` ``OnTouch()`` -Ereignisses wird die **LoadContent()-Funktion** des **LoadContentScene-Skripts** ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="39578-133">Using the Interactable's ``OnClick()`` and ``OnTouch()`` event, it triggers the **LoadContentScene** script's **LoadContent()** function.</span></span>
<span data-ttu-id="39578-134">Im Inspector des **LoadContentScene-Skripts** können Sie den zu ladenden Szenennamen definieren.</span><span class="sxs-lookup"><span data-stu-id="39578-134">In the **LoadContentScene** script's Inspector, you can define the scene name to load.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem6.png" alt="Scene system 6">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem8.png" width="450" alt="Scene System 8">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem7.png" width="450" alt="Scene System 7">

<span data-ttu-id="39578-135">Das Skript verwendet die LoadContent()-Funktion des Szenensystems, um die Szene zu laden.</span><span class="sxs-lookup"><span data-stu-id="39578-135">The script uses the Scene System's LoadContent() function to load the scene.</span></span>
<span data-ttu-id="39578-136">Weitere Informationen finden Sie auf der Seite [Szenensystem.](../scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="39578-136">Please refer to the [Scene System](../scene-system/scene-system-getting-started.md) page for more details.</span></span>

```c#
MixedRealityToolkit.SceneSystem.LoadContent(contentName, loadSceneMode);
```

## <a name="returning-to-the-main-menu-scene"></a><span data-ttu-id="39578-137">Zurückkehren zur Hauptmenüszene</span><span class="sxs-lookup"><span data-stu-id="39578-137">Returning to the main menu scene</span></span>

<span data-ttu-id="39578-138">Um zur Hauptmenüszene zurückzukehren (MRTKExamplesHubMainMenu-Szene), können Sie dieselbe Scene `LoadContent()` System-Methode verwenden.</span><span class="sxs-lookup"><span data-stu-id="39578-138">To return to the main menu scene (MRTKExamplesHubMainMenu scene), you can use the same Scene System `LoadContent()` method.</span></span> <span data-ttu-id="39578-139">**ToggleFeaturesPanelExamplesHub.prefab** stellt die Schaltfläche "Home" bereit, die das **LoadContentScene-Skript** enthält.</span><span class="sxs-lookup"><span data-stu-id="39578-139">The **ToggleFeaturesPanelExamplesHub.prefab** provides the 'Home' button which contains the **LoadContentScene** script.</span></span> <span data-ttu-id="39578-140">Verwenden Sie dieses Prefab, oder geben Sie in jeder Szene eine benutzerdefinierte Startschaltfläche an, damit der Benutzer zur Hauptszene zurückkehren kann.</span><span class="sxs-lookup"><span data-stu-id="39578-140">Use this prefab or provide a custom home button in each scene to allow the user to return to the main scene.</span></span> <span data-ttu-id="39578-141">Sie können **toggleFeaturesPanelExamplesHub.prefab** in die **MRTKExamplesHub-Szene** einfügen, um sie immer sichtbar zu machen, da **MRTKExamplesHub** eine freigegebene Containerszene ist.</span><span class="sxs-lookup"><span data-stu-id="39578-141">One can put the **ToggleFeaturesPanelExamplesHub.prefab** in the **MRTKExamplesHub** scene to make it always visible since **MRTKExamplesHub** is a shared container scene.</span></span> <span data-ttu-id="39578-142">Stellen Sie sicher, dass **Sie ToggleFeaturesPanel.prefab** in jeder Beispielszene ausblenden/deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="39578-142">Make sure to hide/deactivate **ToggleFeaturesPanel.prefab** in each example scene.</span></span>

<img src="../images/examples-hub/MRTK_ExamplesHubToggleFeaturesPanel.png" alt="Toggle feature Panel">

<img src="../images/examples-hub/MRTK_ExamplesHubHomeButton.png" width="450" alt="Example Hub home button">

## <a name="adding-additional-buttons"></a><span data-ttu-id="39578-143">Hinzufügen zusätzlicher Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="39578-143">Adding additional buttons</span></span>

<span data-ttu-id="39578-144">Duplizieren Sie im **CubeCollection-Objekt** _exampleHubButton-Prefabs,_ oder fügen Sie sie hinzu, und klicken Sie in auf **Sammlung aktualisieren.** `GridObjectCollection`</span><span class="sxs-lookup"><span data-stu-id="39578-144">In the **CubeCollection** object, duplicate (or add) _ExampleHubButton_ prefabs and click **Update Collection** in the `GridObjectCollection`.</span></span>
<span data-ttu-id="39578-145">Dadurch wird das Zylinderlayout basierend auf der neuen Gesamtzahl der Schaltflächen aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="39578-145">This will update the cylinder layout based on the new total number of buttons.</span></span>
<span data-ttu-id="39578-146">Weitere Informationen finden Sie auf der Seite [Objektsammlung.](../ux-building-blocks/object-collection.md)</span><span class="sxs-lookup"><span data-stu-id="39578-146">Please refer to the [Object Collection](../ux-building-blocks/object-collection.md) page for more details.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem9.png" alt="Scene System 9">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem10.png" alt="Scene System 10">

<span data-ttu-id="39578-147">Aktualisieren Sie nach dem Hinzufügen der Schaltflächen den Szenennamen im **Skript LoadContentScene** (oben erläutert).</span><span class="sxs-lookup"><span data-stu-id="39578-147">After adding the buttons, update the scene name in the **LoadContentScene** script(explained above).</span></span>
<span data-ttu-id="39578-148">Fügen Sie dem Profil des Szenensystems zusätzliche Szenen hinzu.</span><span class="sxs-lookup"><span data-stu-id="39578-148">Add additional scenes to the Scene System's profile.</span></span>
