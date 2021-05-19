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
# <a name="mrtk-examples-hub"></a>MRTK-Beispielhub

![MRTK-Beispielhub](../images/examples-hub/MRTK_ExamplesHub.png)

MrTK Examples Hub ist eine Unity-Szene, die das Erleben mehrerer Szenen vereinfacht. Er verwendet das Szenensystem des MRTK, um die & zu laden.

**MRTKExamplesHub.unity** ist die Containerszene mit freigegebenen Komponenten, einschließlich ``MixedRealityToolkit`` und ``MixedRealityPlayspace`` . **Die MRTKExamplesHubMainMenu.unity-Szene** verfügt über die Cubeschaltflächen.

## <a name="prerequisite"></a>Voraussetzung

Der MRTK-Beispielhub verwendet [den Szenenübergangsdienst und](../extensions/scene-transition-service.md) zugehörige Skripts. Wenn Sie MRTK über Unity-Pakete verwenden, importieren Sie **microsoft.MixedReality.Toolkit.Unity.Extensions.x.x.x.unitypackage,** das Teil der Releasepakete [ist.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) Wenn Sie MRTK über den Repositoryklon verwenden, sollten Sie bereits den **Ordner MRTK/Erweiterungen** in Ihrem Projekt haben.

## <a name="mrtkexampleshub-scene-and-the-scene-system"></a>MRTKExamplesHub-Szene und Szenensystem

Öffnen **Sie MRTKExamplesHub.unity** unter Es ist eine leere Szene mit `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` MixedRealityToolkit, MixedRealityPlayspace und LoadHubOnStartup. Diese Szene ist für die Verwendung des Szenensystems des MRTK konfiguriert. Klicken `MixedRealitySceneSystem` Sie unter MixedRealityToolkit. Die Informationen des Szenensystems werden im Inspektorbereich angezeigt.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Hierarchy.png" width="300" alt="Example Hub Hierarchy">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector1.png" width="450" alt="Inspector 1">

Am unteren Rand des Inspektors wird die Liste der Szenen angezeigt, die im Szenensystemprofil definiert sind. Sie können auf die Szenennamen klicken, um sie zu laden/zu entladen.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector2.png" width="550" alt="Inspector 2">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem3.png" alt="Scene system 3">Beispiel für das Laden _der MRTKExamplesHub-Szene_ durch Klicken auf den Szenennamen in der Liste.
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem4.png" alt="Scene system 4">Beispiel für das Laden _der HandInteractionExamples-Szene._
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem5.png" alt="Scene system 5">
Beispiel für das Laden mehrerer Szenen.

## <a name="running-the-scene"></a>Ausführen der Szene

Die Szene funktioniert sowohl im Unity-Spielmodus als auch auf dem Gerät. Führen Sie die **MRTKExamplesHub-Szene** im Unity-Editor aus, und verwenden Sie die MRTK-Eingabesimulation, um mit den Szeneninhalten zu interagieren. Erstellen Sie zum Erstellen und Bereitstellen einfach **die MRTKExamplesHub-Szene** mit anderen Szenen, die in der Liste des Szenensystems enthalten sind. Der Inspektor erleichtert auch das Hinzufügen von Szenen zu den Buildeinstellungen. Stellen Sie in den Gebäudeeinstellungen sicher, dass sich die **MRTKExamplesHub-Szene** am Index 0 oben in der Liste befindet.

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

Um zur Hauptmenüszene zurückzukehren (MRTKExamplesHubMainMenu-Szene), können Sie dieselbe Scene `LoadContent()` System-Methode verwenden. **ToggleFeaturesPanelExamplesHub.prefab** stellt die Schaltfläche "Home" bereit, die das **Skript LoadContentScene** enthält. Verwenden Sie dieses Prefab, oder geben Sie in jeder Szene eine benutzerdefinierte Startschaltfläche an, damit der Benutzer zur Hauptszene zurückkehren kann. Sie können **toggleFeaturesPanelExamplesHub.prefab** in die **MRTKExamplesHub-Szene** einfügen, um sie immer sichtbar zu machen, da **MRTKExamplesHub** eine freigegebene Containerszene ist. Stellen Sie sicher, dass **Sie ToggleFeaturesPanel.prefab** in jeder Beispielszene ausblenden/deaktivieren.

<img src="../images/examples-hub/MRTK_ExamplesHubToggleFeaturesPanel.png" alt="Toggle feature Panel">

<img src="../images/examples-hub/MRTK_ExamplesHubHomeButton.png" width="450" alt="Example Hub home button">

## <a name="adding-additional-buttons"></a>Hinzufügen zusätzlicher Schaltflächen

Duplizieren (oder fügen Sie) _exampleHubButton-Prefabs_ im **CubeCollection-Objekt** hinzu, und klicken Sie im auf **Sammlung** `GridObjectCollection` aktualisieren.
Dadurch wird das Zylinderlayout basierend auf der neuen Gesamtanzahl von Schaltflächen aktualisiert.
Weitere Informationen finden Sie [auf der Seite](../ux-building-blocks/object-collection.md) Objektsammlung.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem9.png" alt="Scene System 9">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem10.png" alt="Scene System 10">

Aktualisieren Sie nach dem Hinzufügen der Schaltflächen den Szenennamen im **LoadContentScene-Skript** (siehe oben).
Fügen Sie dem Profil des Szenensystems zusätzliche Szenen hinzu.
