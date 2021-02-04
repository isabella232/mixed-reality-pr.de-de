---
title: Autorisieren von Projektänderungen
description: Erfahren Sie, wie Sie Projektänderungen mit dem MR-Featuretool für die HoloLens- und VR-Entwicklung autorisieren.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: Aktuell, Tools, Erste Schritte, Grundlagen, Unity, Visual Studio, Toolkit, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Installation, Windows, HoloLens, Emulator, Unreal, OpenXR
ms.openlocfilehash: b9e4f53c9a1e5503cfa92a612879be1971422acc
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2021
ms.locfileid: "99243908"
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
