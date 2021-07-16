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
# <a name="mrtk-examples-hub"></a>MRTK-Beispiele-Hub

![MRTK-Beispiele-Hub](../images/examples-hub/MRTK_ExamplesHub.png)

MRTK Examples Hub ist eine Unity-Szene, die es einfach macht, mehrere Szenen zu erleben. Es verwendet das Szenensystem des MRTK, um die Szenen zu laden & zu entladen.

**MRTKExamplesHub.unity** ist die Containerszene, die über gemeinsam genutzte Komponenten wie ``MixedRealityToolkit`` und ``MixedRealityPlayspace`` verfügt. **MRTKExamplesHubMainMenu.unity-Szene** verfügt über die Cubeschaltflächen.

## <a name="prerequisite"></a>Voraussetzungen

Der MRTK-Beispielhub verwendet [den Scene Transition Service](../extensions/scene-transition-service.md) und zugehörige Skripts. Wenn Sie MRTK über Unity-Pakete verwenden, importieren Sie **Microsoft.MixedReality.Toolkit.Unity.Extensions.x.x.x.unitypackage,** das Teil der [Releasepakete](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)ist. Wenn Sie MRTK über den Repositoryklon verwenden, sollten Sie bereits über den Ordner **MRTK/Extensions** in Ihrem Projekt verfügen.

## <a name="mrtkexampleshub-scene-and-the-scene-system"></a>MRTKExamplesHub-Szene und das Szenensystem

Öffnen Sie **MRTKExamplesHub.unity.** `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` Dies ist eine leere Szene mit MixedRealityToolkit, MixedRealityPlayspace und LoadHubOnStartup. Diese Szene ist für die Verwendung des Szenensystems von MRTK konfiguriert. Klicken Sie `MixedRealitySceneSystem` unter MixedRealityToolkit. Im Bereich Inspektor werden die Informationen des Szenensystems angezeigt.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Hierarchy.png" width="300" alt="Example Hub Hierarchy">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector1.png" width="450" alt="Inspector 1">

Am unteren Rand des Inspektors wird die Liste der Szenen angezeigt, die im Szenensystemprofil definiert sind. Sie können auf die Szenennamen klicken, um sie zu laden bzw. zu entladen.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector2.png" width="550" alt="Inspector 2">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem3.png" alt="Scene system 3">Beispiel für das Laden der _MRTKExamplesHub-Szene_ durch Klicken auf den Szenennamen in der Liste.
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem4.png" alt="Scene system 4">Beispiel für das Laden der _HandInteractionExamples-Szene._
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem5.png" alt="Scene system 5">
Beispiel für das Laden mehrerer Szenen.

## <a name="running-the-scene"></a>Ausführen der Szene

Die Szene funktioniert sowohl im Unity-Spielmodus als auch auf dem Gerät. Führen Sie die **MRTKExamplesHub-Szene** im Unity-Editor aus, und verwenden Sie die MRTK-Eingabesimulation, um mit den Szeneninhalten zu interagieren. Erstellen Sie zum Erstellen und Bereitstellen einfach **die MRTKExamplesHub-Szene** mit anderen Szenen, die in der Liste des Szenensystems enthalten sind. Der Inspektor erleichtert auch das Hinzufügen von Szenen zum Build Einstellungen. Stellen Sie im Einstellungen Building sicher, dass sich die **MRTKExamplesHub-Szene** am Index 0 oben in der Liste befindet.

<img src="../images/examples-hub/MRTK_ExamplesHub_BuildSettings.png" width="450" alt="Build settings">

## <a name="how-mrtkexampleshub-loads-a-scene"></a>Wie MRTKExamplesHub eine Szene lädt

In der **MRTKExamplesHub-Szene** finden Sie das ``ExamplesHubButton`` Prefab.
Das Prefab enthält ein **FrontPlate-Objekt,** das ``Interactable`` enthält.
Mithilfe des Interactable-Ereignisses und des ``OnClick()`` ``OnTouch()`` -Ereignisses wird die **LoadContent()-Funktion** des **LoadContentScene-Skripts** ausgelöst.
Im Inspector des **LoadContentScene-Skripts** können Sie den zu ladenden Szenennamen definieren.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem6.png" alt="Scene system 6">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem8.png" width="450" alt="Scene System 8">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem7.png" width="450" alt="Scene System 7">

Das Skript verwendet die LoadContent()-Funktion des Szenensystems, um die Szene zu laden.
Weitere Informationen finden Sie auf der Seite [Szenensystem.](../scene-system/scene-system-getting-started.md)

```c#
MixedRealityToolkit.SceneSystem.LoadContent(contentName, loadSceneMode);
```

## <a name="returning-to-the-main-menu-scene"></a>Zurückkehren zur Hauptmenüszene

Um zur Hauptmenüszene zurückzukehren (MRTKExamplesHubMainMenu-Szene), können Sie dieselbe Scene `LoadContent()` System-Methode verwenden. **ToggleFeaturesPanelExamplesHub.prefab** stellt die Schaltfläche "Home" bereit, die das **LoadContentScene-Skript** enthält. Verwenden Sie dieses Prefab, oder geben Sie in jeder Szene eine benutzerdefinierte Startschaltfläche an, damit der Benutzer zur Hauptszene zurückkehren kann. Sie können **toggleFeaturesPanelExamplesHub.prefab** in die **MRTKExamplesHub-Szene** einfügen, um sie immer sichtbar zu machen, da **MRTKExamplesHub** eine freigegebene Containerszene ist. Stellen Sie sicher, dass **Sie ToggleFeaturesPanel.prefab** in jeder Beispielszene ausblenden/deaktivieren.

<img src="../images/examples-hub/MRTK_ExamplesHubToggleFeaturesPanel.png" alt="Toggle feature Panel">

<img src="../images/examples-hub/MRTK_ExamplesHubHomeButton.png" width="450" alt="Example Hub home button">

## <a name="adding-additional-buttons"></a>Hinzufügen zusätzlicher Schaltflächen

Duplizieren Sie im **CubeCollection-Objekt** _exampleHubButton-Prefabs,_ oder fügen Sie sie hinzu, und klicken Sie in auf **Sammlung aktualisieren.** `GridObjectCollection`
Dadurch wird das Zylinderlayout basierend auf der neuen Gesamtzahl der Schaltflächen aktualisiert.
Weitere Informationen finden Sie auf der Seite [Objektsammlung.](../ux-building-blocks/object-collection.md)

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem9.png" alt="Scene System 9">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem10.png" alt="Scene System 10">

Aktualisieren Sie nach dem Hinzufügen der Schaltflächen den Szenennamen im **Skript LoadContentScene** (oben erläutert).
Fügen Sie dem Profil des Szenensystems zusätzliche Szenen hinzu.
