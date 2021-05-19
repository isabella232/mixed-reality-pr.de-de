---
title: Controller-Zuordnungstool
description: Dokumentation zum Controllerzuordnungstool in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: f00dc01555ef158dab21334761bd23ef6a70dba4
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144086"
---
# <a name="controller-mapping-tool"></a>Controllerzuordnungstool

Das Controllerzuordnungstool ist ein Runtimetool (auf dem Gerät oder im Editor), mit dem Entwickler schnell die Unity-Eingabeachsen- und Schaltflächenzuordnungen für einen Hardwarecontroller (z. B. Motion Controller) bestimmen können.

Dieses Tool ist sehr nützlich, wenn Unterstützung für einen neuen Hardwarecontroller entwickelt wird. Es kann auch helfen, ein vermutetes Problem mit der Steuerelementzuordnung in der Supportklasse für einen vorhandenen Controller zu bestätigen.

![Controllerzuordnungstool](../images/controller-mapping-tool/ControllerMappingTool.png)

## <a name="using-the-controller-mapping-tool"></a>Verwenden des Controllerzuordnungstools

Navigieren Sie zum Einstieg in das Controllerzuordnungstool zu **MRTK/Tools/RuntimeTools/Tools/ControllerMappingTool,** und öffnen Sie die **ControllerMappingTool-Szene.** Nachdem die Szene geladen wurde, kann das Projekt entweder im Editor, im Wiedergabemodus oder auf einem Gerät erstellt und ausgeführt werden.

So untersuchen Sie die Zuordnungen von Unity für einen Controller:

- Verbinden des Controllers
- Drücken Sie jede Schaltfläche, und verschieben Sie jede Achse.
- Beachten Sie die Zuordnungen in der Anzeige.
- Aktualisieren der Steuerelementzuordnungen im Eingabesystemdatenanbieter für den Controller

> [!NOTE]
> Das Controllerzuordnungstool nutzt keine Microsoft Mixed Reality Toolkit-Komponenten. Es kommuniziert direkt mit Unity, um die Steuerelementzuordnungen zu bestimmen und anzuzeigen.

### <a name="all-controls-display"></a>Alle Steuerelemente werden angezeigt

Im großen Anzeigebereich wird der Status aller definierten Unity-Eingabeachsen und -Schaltflächen (z. B. Achse 10, Schaltfläche 3) angezeigt. Dieser Bereich bietet eine vollständige Ansicht des Zustands des Controllers.

![Alle Steuerelemente werden angezeigt](../images/controller-mapping-tool/AllControls.png)

### <a name="active-controls-display"></a>Anzeigen von aktiven Steuerelementen

Der kleinere, schmale Anzeigebereich zeigt die Unity-Eingabe als Axt und Schaltflächen an, die sich im aktiven Zustand befinden (z. B. eine Schaltfläche wird gedrückt). Die Anzeige der aktiven Steuerelemente bietet eine leicht lesbare Zusammenfassungsansicht des Zustands des Controllers.

![Anzeigen von aktiven Steuerelementen](../images/controller-mapping-tool/ActiveControls.png)

## <a name="see-also"></a>Weitere Informationen

- [Erstellen eines Eingabesystemdatenanbieters](../input/create-data-provider.md)
- [InputFeatureUsage-Tool](input-feature-usage-tool.md)
