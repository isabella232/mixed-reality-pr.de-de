---
title: Migrationszeitfenster
description: Dokumentation zum Migrieren zu einem Update im MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 9e657e0b90f8087670b72c993ab1dcf78ae9e6680873139c6867d7c551a41895
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220048"
---
# <a name="migration-window"></a>Migrationszeitfenster

Wenn das MRTK geändert wird, werden einige Komponenten möglicherweise veraltet, und es werden Ersatzkomponenten eingeführt.
Das Migrationsfenster ist ein Tool, mit dem Benutzer automatisch eine Teilmenge dieser veralteten Komponenten zu den neuen Ersetzungen migrieren können.

![Migrationszeitfenster](../images/migration-window/MRTK_Migration_Window.png)

## <a name="usage"></a>Verbrauch

Um das Fenster zu öffnen, wählen **Sie** Mixed Reality Toolkit Utilities Migration Window  >  **(Migrationsfenster**  >  **für Toolkit-Hilfsprogramme)**  >  **aus.** Sobald das Migrationsfenster geöffnet ist, können die Navigationsregisterkarte für den Auswahlmodus aktiviert werden, indem Sie die komponentenspezifische Implementierung des Migrationshandlers auswählen.  

![Migrationsauswahlmodi](../images/migration-window/MRTK_Migration_Modes.png)

### <a name="object-mode"></a>Objektmodus

Wenn Sie die Registerkarte Objekte auswählen, wird das ObjektFeld aktiviert, in das der Benutzer alle Game-Objekte aus der aktuell geöffneten Szene oder prefabs aus dem zu migrierenden Projektordner ziehen und ablegen kann.
Durch Drücken der Schaltfläche zum Entfernen *(-),* die rechts neben dem aufgelisteten Objekt angezeigt wird, wird das Objekt aus der Auswahlliste entfernt.

Sobald alle gewünschten Objekte in der Liste  enthalten sind, werden durch Drücken der Schaltfläche Migrieren die änderungen angewendet, die für die ausgewählte Implementierung des Migrationshandlers erforderlich sind, auf alle Komponenten in der Auswahl, die mit der Implementierung übereinstimmen.

![Auswahlmigration](../images/migration-window/MRTK_Object_Migration.png)

### <a name="scene-mode"></a>Szenenmodus

Ermöglicht dem Benutzer das Ziehen und Ablegen von Szenenobjekten, die zu migrierende Objekte enthalten.

![Auswählen von Szenen für die Migration](../images/migration-window/MRTK_Scene_Selection.png)

### <a name="project-mode"></a>Project-Modus

Wenn Sie auf *die Schaltfläche* Migrieren klicken, wird die Komponente aktualisiert, auf die die Implementierung des Migrationshandlers für alle Prefabs und Szenen im Projekt ausgerichtet ist.

![Migrieren eines vollständigen Projekts](../images/migration-window/MRTK_Project_Migration.png)

## <a name="see-also"></a>Siehe auch

- [Aktualisieren von früheren Versionen](../../updates-deployment/updating.md)
- [Microsoft Mixed Reality Toolkit-Releases](../../release-notes/mrtk-26-release-notes.md)
- [MRTK-Roadmap](../../roadmap.md)
