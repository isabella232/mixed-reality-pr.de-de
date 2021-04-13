---
title: Inputfeatureusagetool
description: Dokumentation zum inputfeatureusage-Tool in mrtk
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 35b28557df37abee19a0c950b362117eb6a120b0
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300199"
---
# <a name="inputfeatureusage-tool"></a>Inputfeatureusage-Tool

Das inputfeatureusage-Tool ist ein Lauf Zeit Tool (auf dem Gerät oder im Editor), mit dem Entwickler die verfügbaren Unity-inputfeatureverwendungen für eine erkannte Eingabe Quelle (z. h. Motion Controller oder Handgelenk) schnell ermitteln können.

> [!NOTE]
> Diese Szene funktioniert nur in Unity 2019,3 oder höher.

Dieses Tool ist sehr nützlich, wenn Sie die Unterstützung für einen neuen Hardware Controller entwickeln. Außerdem kann es hilfreich sein, ein verdächtiges steuerungsmappenproblem in der Unterstützungs Klasse für einen vorhandenen Controller zu bestätigen.

![Inputfeatureusage-Tool](../images/controller-mapping-tool/InputFeatureUsages.png)

## <a name="using-the-inputfeatureusage-tool"></a>Verwenden des inputfeatureusage-Tools

Um mit dem inputfeatureusage-Tool zu beginnen, navigieren Sie zu **mrtk/Tools/runtimetools/Tools/inputfeatureusagetool** , und öffnen Sie die **inputfeatureusagetool** -Szene. Nachdem die Szene geladen wurde, kann das Projekt entweder im Editor, über den Wiedergabemodus oder auf einem Gerät erstellt und ausgeführt werden.

So untersuchen Sie die Zuordnungen von Unity für einen Controller:

- Verbinden des Controllers
- Drücken Sie jede Schaltfläche, und verschieben Sie jede Achse.
- Beachten Sie die Funktions Verwendungen in der Anzeige.
- Aktualisieren der Steuerelement Zuordnungen im Eingabe Systemdaten Anbieter für den Controller

> [!NOTE]
> Das inputfeatureusage-Tool nutzt nicht die Microsoft Mixed Reality Toolkit-Komponenten. Er kommuniziert direkt mit Unity, um die Funktions Verwendungen zu bestimmen und anzuzeigen.

### <a name="panels"></a>Panels

Die Bereiche zeigen den aktuellen Status aller gemeldeten inputfeatureusages für alle erkannten Unity-Eingabe Quellen an.

Der kleinere Bereich am oberen Rand listet die Namen aller erkannten Quellen auf.

## <a name="see-also"></a>Weitere Informationen

- [Erstellen eines Eingabe System-Datenanbieters](../input/create-data-provider.md)
- [Controller-Mapping-Tool](controller-mapping-tool.md)
