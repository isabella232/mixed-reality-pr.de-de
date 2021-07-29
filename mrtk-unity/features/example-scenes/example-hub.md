---
title: MRTK-Beispiele-Hub
description: Übersicht über Beispielszenen im MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 2b7e1234ed79a99e826184e42c319f84582ff23a
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757052"
---
# <a name="mrtk-examples-hub"></a>MRTK-Beispiele-Hub

![MRTK-Beispiele-Hub](../images/examples-hub/MRTK_ExamplesHub.png)

MrTK Examples Hub ist eine Unity-Szene, die das Erleben mehrerer Szenen vereinfacht. Er verwendet das Szenensystem des MRTK, um die & zu laden.

**MRTKExamplesHub.unity** ist die Containerszene mit freigegebenen Komponenten, einschließlich ``MixedRealityToolkit`` und ``MixedRealityPlayspace`` . **MrTKExamplesHubMainMenu.unity-Szene** verfügt über die Cubeschaltflächen.

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>Laden Sie die App Microsoft Store in HoloLens 2
Wenn Sie über HoloLens 2 verfügen, können Sie die App direkt herunterladen und auf Ihrem Gerät installieren.

<a href='//www.microsoft.com/store/apps/9mv8c39l2sj4?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>

## <a name="prerequisite"></a>Voraussetzungen

Der MRTK-Beispielhub verwendet [den Szenenübergangsdienst](../extensions/scene-transition-service.md) und zugehörige Skripts. Wenn Sie MRTK über Unity-Pakete verwenden, importieren Sie **microsoft.MixedReality.Toolkit.Unity.Extensions.x.x.x.unitypackage,** das Teil der Releasepakete [ist.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) Wenn Sie MRTK über den Repositoryklon verwenden, sollten Sie bereits den **Ordner MRTK/Erweiterungen** in Ihrem Projekt haben.

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

Die Szene funktioniert sowohl im Spielmodus von Unity als auch auf dem Gerät. Führen Sie die **MRTKExamplesHub-Szene** im Unity-Editor aus, und verwenden Sie die MRTK-Eingabesimulation, um mit den Szeneninhalten zu interagieren. Erstellen Sie zum Erstellen und Bereitstellen einfach **die MRTKExamplesHub-Szene** mit anderen Szenen, die in der Liste des Szenensystems enthalten sind. Der Inspektor erleichtert auch das Hinzufügen von Szenen zum Build-Einstellungen. Stellen Sie im Einstellungen, dass **sich die MRTKExamplesHub-Szene** am Anfang der Liste bei Index 0 befindet.

<img src="../images/examples-hub/MRTK_ExamplesHub_BuildSettings.png" width="450" alt="Build settings">

## <a name="how-mrtkexampleshub-loads-a-scene"></a>So lädt MRTKExamplesHub eine Szene

In der **MRTKExamplesHub-Szene** finden Sie das ``ExamplesHubButton`` Prefab.
Es gibt ein **FrontPlate-Objekt** im Prefab, das ``Interactable`` enthält.
Mithilfe des -Ereignisses und des -Ereignisses von Interactable wird die LoadContent()-Funktion des ``OnClick()`` ``OnTouch()`` **LoadContentScene-Skripts** ausgelöst. 
Im **Inspektor des LoadContentScene-Skripts** können Sie den zu ladenden Szenennamen definieren.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem6.png" alt="Scene system 6">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem8.png" width="450" alt="Scene System 8">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem7.png" width="450" alt="Scene System 7">

Das Skript verwendet die LoadContent()-Funktion des Szenensystems, um die Szene zu laden.
Weitere Informationen finden Sie [auf der Seite Szenensystem.](../scene-system/scene-system-getting-started.md)

```c#
MixedRealityToolkit.SceneSystem.LoadContent(contentName, loadSceneMode);
```

## <a name="returning-to-the-main-menu-scene"></a>Zurück zur Hauptmenüszene

Um zur Hauptmenüszene (MRTKExamplesHubMainMenu-Szene) zurückzukehren, können Sie dieselbe Scene System-Methode `LoadContent()` verwenden. **ToggleFeaturesPanelExamplesHub.prefab** stellt die Schaltfläche "Home" mit dem **LoadContentScene-Skript** zur Verfügung. Verwenden Sie dieses Prefab, oder stellen Sie eine benutzerdefinierte Startschaltfläche in jeder Szene zur Verfügung, damit der Benutzer zur Hauptszene zurückkehren kann. Sie können **"ToggleFeaturesPanelExamplesHub.prefab"** in die **MRTKExamplesHub-Szene** setzen, um es immer sichtbar zu machen, da **MRTKExamplesHub** eine freigegebene Containerszene ist. Achten Sie darauf, **"ToggleFeaturesPanel.prefab"** in jeder Beispielszene auszublenden/zu deaktivieren.

<img src="../images/examples-hub/MRTK_ExamplesHubToggleFeaturesPanel.png" alt="Toggle feature Panel">

<img src="../images/examples-hub/MRTK_ExamplesHubHomeButton.png" width="450" alt="Example Hub home button">

## <a name="adding-additional-buttons"></a>Hinzufügen zusätzlicher Schaltflächen

Duplizieren (oder fügen Sie) _exampleHubButton-Prefabs_ im **CubeCollection-Objekt** hinzu, und klicken Sie in auf **Sammlung** `GridObjectCollection` aktualisieren.
Dadurch wird das Zylinderlayout basierend auf der neuen Gesamtanzahl von Schaltflächen aktualisiert.
Weitere Informationen finden Sie [auf der](../ux-building-blocks/object-collection.md) Seite Objektsammlung.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem9.png" alt="Scene System 9">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem10.png" alt="Scene System 10">

Aktualisieren Sie nach dem Hinzufügen der Schaltflächen den Szenennamen im **LoadContentScene-Skript** (siehe oben).
Fügen Sie dem Profil des Szenensystems zusätzliche Szenen hinzu.
