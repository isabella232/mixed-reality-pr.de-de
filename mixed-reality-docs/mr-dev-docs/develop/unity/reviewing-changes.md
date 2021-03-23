---
title: Autorisieren von Projektänderungen
description: Erfahren Sie, wie Sie Projektänderungen mit dem MR-Featuretool für die HoloLens- und VR-Entwicklung autorisieren.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: Aktuell, Tools, Erste Schritte, Grundlagen, Unity, Visual Studio, Toolkit, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Installation, Windows, HoloLens, Emulator, Unreal, OpenXR
ms.openlocfilehash: db7ae079e19c7739f57f0b9e4a375a3e6f9a3cdd
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2021
ms.locfileid: "102230768"
---
# <a name="authorizing-project-changes"></a>Autorisieren von Projektänderungen

Bevor Sie das Unity-Projekt ändern, müssen die Änderungen an den Manifest- und Projektdateien überprüft und genehmigt werden:

![Anfordern von Autorisierung](images/FeatureToolApprovalRequest.png)

## <a name="manifest"></a>Manifest

Die vorgeschlagenen Manifeständerungen können in der Spalte **Manifest** auf der linken Seite angezeigt werden. Der Inhalt ist genau das, was in das Projektmanifest geschrieben wird (**Packages/manifest.json**):

![Manifestvorschau](images/ManifestPreview.png)

## <a name="files-to-be-copied-into-the-project"></a>Dateien, die in das Projekt kopiert werden sollen

Im Abschnitt **Files to be copied into the project** (Dateien, die in das Projekt kopiert werden sollen) auf der rechten Seite listet die spezifischen Featurepaketdateien auf, die in das Unity-Projekt kopiert werden sollen:

![Manifestvorschau mit Dateien, die kopiert werden sollen](images/FilesToCopy.png)

## <a name="compare-manifests"></a>Vergleichen von Manifesten

Sie können einen detaillierten Vergleich aller vorgeschlagenen Änderungen anzeigen, indem Sie **Compare** (Vergleichen) auswählen:

![Vergleichen von Manifesten](images/FeatureToolCompareManifest.png)

## <a name="approving-changes"></a>Genehmigen von Änderungen

Wenn die vorgeschlagenen Änderungen genehmigt werden, werden die aufgelisteten Dateien in das Unity-Projekt kopiert, und das Manifest wird mit Verweisen auf diese Dateien aktualisiert.

> [!NOTE]
> Die Featurepaketdateien (TGZ) sollten der Quellcodeverwaltung hinzugefügt werden. Auf sie wird mithilfe eines relativen Pfads verwiesen, um Entwicklungsteams das einfache Teilen von Features und Manifeständerungen zu ermöglichen.

 Im Rahmen der Änderungen wird die aktuelle **manifest.json**-Datei gesichert.

> [!IMPORTANT]
> Wenn Sie Manifestsicherungen anzeigen, trägt die älteste Sicherung den Namen **manifest.json.backup**. Neuere Sicherungen werden mit einem Zahlenwert ergänzt, beginnend bei (0).

## <a name="going-back-to-the-previous-step"></a>Zurückwechseln zum vorherigen Schritt

Wenn Sie Änderungen an Ihrer Featureauswahl vornehmen müssen, verwenden Sie **Go Back** (Zurück), um zum Schritt [import](importing-features.md) zurückzukehren.

## <a name="see-also"></a>Siehe auch

- [Willkommen beim Mixed Reality-Featuretool](welcome-to-mr-feature-tool.md)
- [Importieren ausgewählter Pakete](importing-features.md)
