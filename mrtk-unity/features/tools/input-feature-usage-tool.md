---
title: Tool zur Verwendung von Eingabefeatures
description: InputFeatureUsage-Dokumentationstool im MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 413d2a3105294411f9c08f4a2add9365389ea783
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176123"
---
# <a name="input-feature-usage-tool"></a>Tool zur Verwendung von Eingabefeatures

Das InputFeatureUsage-Tool ist ein Runtimetool (auf dem Gerät oder im Editor), mit dem Entwickler schnell die verfügbaren Unity InputFeatureUsages für eine erkannte Eingabequelle (z. B. Motion Controller oder Artikulierte Hand) bestimmen können.

> [!NOTE]
> Diese Szene funktioniert nur mit Unity 2019.3 oder höher.

Dieses Tool ist sehr nützlich, wenn Unterstützung für einen neuen Hardwarecontroller entwickelt wird. Es kann auch helfen, ein vermutetes Problem mit der Steuerelementzuordnung in der Supportklasse für einen vorhandenen Controller zu bestätigen.

![InputFeatureUsage-Tool](../images/controller-mapping-tool/InputFeatureUsages.png)

## <a name="using-the-inputfeatureusage-tool"></a>Verwenden des InputFeatureUsage-Tools

Navigieren Sie zum Einstieg mit dem InputFeatureUsage-Tool zu **MRTK/Tools/RuntimeTools/Tools/InputFeatureUsageTool,** und öffnen Sie die **InputFeatureUsageTool-Szene.** Nachdem die Szene geladen wurde, kann das Projekt entweder im Editor, im Wiedergabemodus oder auf einem Gerät erstellt und ausgeführt werden.

So untersuchen Sie die Zuordnungen von Unity für einen Controller:

- Verbinden des Controllers
- Drücken Sie jede Schaltfläche, und verschieben Sie jede Achse.
- Beachten Sie die Featureverwendungen in der Anzeige.
- Aktualisieren der Steuerelementzuordnungen im Eingabesystemdatenanbieter für den Controller

> [!NOTE]
> Das InputFeatureUsage-Tool verwendet keine Microsoft Mixed Reality Toolkit-Komponenten. Es kommuniziert direkt mit Unity, um die Funktionsverwendungen zu bestimmen und anzuzeigen.

### <a name="panels"></a>Panels

In den Panels wird der aktuelle Status aller gemeldeten InputFeatureUsages für alle erkannten Unity-Eingabequellen angezeigt.

Im kleineren Bereich oben werden die Namen aller erkannten Quellen aufgeführt.

## <a name="see-also"></a>Siehe auch

- [Erstellen eines Eingabesystemdatenanbieters](../input/create-data-provider.md)
- [Controllerzuordnungstool](controller-mapping-tool.md)
