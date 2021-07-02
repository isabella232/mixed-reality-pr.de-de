---
title: Erste Schritte mit dem Szenensystem
description: Landing Page für Szenensystem mit MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 16adf431498f8146ca2cc60565e59dc8ae03fd92
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177573"
---
# <a name="scene-system-getting-started"></a>Erste Schritte mit dem Szenensystem

## <a name="when-to-use-the-scene-system"></a>Wann das Szenensystem verwendet werden soll

Wenn Ihr Projekt aus einer einzelnen Szene besteht, ist das Szenensystem wahrscheinlich nicht erforderlich. Dies ist besonders nützlich, wenn mindestens eine der folgenden Bedingungen zutrifft:

- Ihr Projekt verfügt über mehrere Szenen.
- Sie sind es gewohnt, einzelne Szenen zu laden, aber die Art und Weise, wie sie die MixedRealityToolkit-Instanz zerstört, gefällt Ihnen nicht.
- Sie möchten eine einfache Möglichkeit haben, mehrere Szenen additiv zu laden, um Ihre Erfahrung zu erstellen.
- Sie möchten eine einfache Möglichkeit zum Nachverfolgen von Ladevorgängen oder eine einfache Möglichkeit, die Szenenaktivierung für mehrere Szenen zu steuern, die gleichzeitig geladen werden.
- Sie möchten die Beleuchtung über alle Szenen hinweg konsistent und vorhersagbar halten.

## <a name="scene-system-resources"></a>Szenensystemressourcen

Standardmäßig verwendet das Szenensystem ein Szenenobjektpaar (DefaultManagerScene- und DefaultLighting-Szene). Wenn eine dieser Szenen nicht gefunden werden kann, wird im Profilinspektor des Szenensystems eine Meldung angezeigt.

![Meldung zu Standardressourcen](../images/scene-system/DefaultResourcesMessage.png)

>! [Hinweis] Wenn das Projekt benutzerdefinierte Manager- und Beleuchtungsszenen verwendet, kann diese Meldung sicher ignoriert werden.

In den folgenden Abschnitten wird beschrieben, wie Sie diese Meldung auflösen, je nachdem, welche Methode zum Importieren des Mixed Reality Toolkits verwendet wurde.

### <a name="unity-package-manager-upm"></a>Unity Paket-Manager (UPM)

In den Mixed Reality Toolkit-UPM-Paketen werden die Szenensystemressourcen als Beispiel gepackt. Da UPM-Pakete unveränderlich sind, kann Unity die erforderliche Szenendatei nur öffnen, wenn sie explizit in das Projekt importiert werden.

Führen Sie zum Importieren die folgenden Schritte aus:

- Wählen Sie **Fenster**  >  **Paket-Manager**
- Wählen Sie **Mixed Reality Toolkit Foundation aus.**
- Suchen **von Szenensystemressourcen** im **Abschnitt "Beispiele"**

  ![Importieren von Szenensystemressourcen](../images/scene-system/UpmImportSceneSystemResources.png)

- Wählen Sie **Importieren aus.**

### <a name="asset-unitypackage-files"></a>Assetdateien (.unitypackage)

Wenn der Ordner SceneSystemResources gelöscht oder während des Imports deaktiviert wurde, kann er mit den folgenden Schritten wiederhergestellt werden:

- Wählen Sie **Assets** Import Package Custom Package  >  **(Benutzerdefiniertes Paket**  >  **importieren) aus.**
- Öffnen Sie **das Paket Microsoft.MixedReality.Toolkit.Foundation.**
- Stellen Sie **sicher, dass Services/SceneSystem/SceneSystemResources** und alle untergeordneten Optionen ausgewählt sind.

  ![Erneutes Importieren von Szenensystemressourcen](../images/scene-system/ReimportSceneSystemResources.png)

- Wählen Sie **Importieren aus.**

## <a name="how-to-use-the-scene-system"></a>Verwenden des Szenensystems

- [Szenentypen](scene-system-scene-types.md)
- [Laden von Inhaltsszenen](scene-system-content-loading.md)
- [Überwachen des Ladens von Inhalten](scene-system-load-progress.md)
- [Laden von Beleuchtungsszenen](scene-system-lighting-scenes.md)

## <a name="editor-settings"></a>Editor-Einstellungen

Standardmäßig erzwingt das Szenensystem mehrere Verhaltensweisen im Unity-Editor. Wenn Sie eines dieser Verhaltensweisen sehr stark finden, können sie im Abschnitt **Editor Einstellungen** Ihres Szenensystemprofils deaktiviert werden.

- `Editor Manage Build Settings:` Wenn true, aktualisiert der Dienst Ihre Buildeinstellungen automatisch und stellt sicher, dass alle Manager-, Beleuchtungs- und Inhaltsszenen hinzugefügt werden. Deaktivieren Sie diese Option, wenn Sie die vollständige Kontrolle über die Buildeinstellungen wünschen.

- `Editor Enforce Scene Order:` Wenn true, stellt der Dienst sicher, dass die Manager-Szene zuerst in der Szenenhierarchie angezeigt wird, gefolgt von Beleuchtung und Inhalt. Deaktivieren Sie diese Option, wenn Sie die gesamte Kontrolle über die Szenenhierarchie wünschen.

- `Editor Manage Loaded Scenes:` Bei "true" stellt der Dienst sicher, dass die Manager-, Inhalts- und Beleuchtungsszenen immer geladen werden. Deaktivieren Sie diese Option, wenn Sie die vollständige Kontrolle darüber haben möchten, welche Szenen im Editor geladen werden.

- `Editor Enforce Lighting Scene Types:` Bei "true" stellt der Dienst sicher, dass nur die in definierten beleuchtungsbezogenen Komponenten `PermittedLightingSceneComponentTypes` in Beleuchtungsszenen zulässig sind. Deaktivieren Sie diese Option, wenn Sie die vollständige Kontrolle über den Inhalt von Beleuchtungsszenen wünschen.

![Einstellungen des Szenensystem-Editors](../images/scene-system/MRTK_SceneSystemProfileEditorSettings.PNG)
