---
title: Controller-Zuordnungstool
description: Dokumentation zum Controllerzuordnungstool in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: a5ebf85e3f45e622aaa05311d78066bf8b762108af81cff5292772b92cce0900
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200220"
---
# <a name="controller-mapping-tool"></a>Controller-Zuordnungstool

Das Controllerzuordnungstool ist ein Runtimetool (auf dem Gerät oder im Editor), mit dem Entwickler schnell die Unity-Eingabeachsen- und Schaltflächenzuordnungen für einen Hardwarecontroller (z. B. Motion Controller) bestimmen können.

Dieses Tool ist sehr nützlich, wenn Unterstützung für einen neuen Hardwarecontroller entwickelt wird. Es kann auch helfen, ein vermutetes Problem mit der Steuerelementzuordnung in der Supportklasse für einen vorhandenen Controller zu bestätigen.

![Controller-Zuordnungstool](../images/controller-mapping-tool/ControllerMappingTool.png)

## <a name="using-the-controller-mapping-tool"></a>Verwenden des Controllerzuordnungstools

Navigieren Sie zum Einstieg in das Controllerzuordnungstool zu **MRTK/Tools/RuntimeTools/Tools/ControllerMappingTool,** und öffnen Sie die **ControllerMappingTool-Szene.** Nachdem die Szene geladen wurde, kann das Projekt entweder im Editor, im Wiedergabemodus oder auf einem Gerät erstellt und ausgeführt werden.

So untersuchen Sie die Unity-Zuordnungen für einen Controller:

- Verbinden des Controllers
- Drücken Sie jede Schaltfläche, und verschieben Sie jede Achse.
- Beachten Sie die Zuordnungen in der Anzeige.
- Aktualisieren der Steuerelementzuordnungen im Eingabesystemdatenanbieter für den Controller

> [!NOTE]
> Das Controllerzuordnungstool nutzt keine Microsoft Mixed Reality Toolkit-Komponenten. Es kommuniziert direkt mit Unity, um die Steuerelementzuordnungen zu bestimmen und anzuzeigen.

### <a name="all-controls-display"></a>Alle Steuerelemente werden angezeigt

Im großen Anzeigebereich wird der Status aller definierten Unity-Eingabeachsen und -Schaltflächen (z.B. Achse 10, Schaltfläche 3) angezeigt. Dieser Bereich bietet eine vollständige Ansicht des Zustands des Controllers.

![Alle Steuerelemente werden angezeigt](../images/controller-mapping-tool/AllControls.png)

### <a name="active-controls-display"></a>Anzeige aktiver Steuerelemente

Der kleinere, schmale Anzeigebereich zeigt die Unity-Eingabe axt und Schaltflächen an, die sich in einem aktiven Zustand befinden (z. B. eine Schaltfläche wird gedrückt). Die Anzeige der aktiven Steuerelemente bietet eine leicht lesbare Zusammenfassungsansicht des Zustands des Controllers.

![Anzeige aktiver Steuerelemente](../images/controller-mapping-tool/ActiveControls.png)

## <a name="see-also"></a>Siehe auch

- [Erstellen eines Eingabesystem-Datenanbieters](../input/create-data-provider.md)
- [InputFeatureUsage-Tool](input-feature-usage-tool.md)
