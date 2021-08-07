---
title: Eingabefunktionsverwendungs-Tool
description: InputFeatureUsage-Dokumentationstool in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 9d5e80ee5f31086b12ec2b82ab2368361fb738e03ea7fe5cf02ba0b4bd22c0b8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189434"
---
# <a name="input-feature-usage-tool"></a>Eingabefunktionsverwendungs-Tool

Das InputFeatureUsage-Tool ist ein Runtimetool (auf dem Gerät oder im Editor), mit dem Entwickler schnell die verfügbaren Unity InputFeatureUsages für eine erkannte Eingabequelle ermitteln können (z. B. Motion Controller oder Artikulierte Hand).

> [!NOTE]
> Diese Szene funktioniert nur mit Unity 2019.3 oder höher.

Dieses Tool ist sehr nützlich, wenn Unterstützung für einen neuen Hardwarecontroller entwickelt wird. Es kann auch helfen, ein vermutetes Problem mit der Steuerelementzuordnung in der Supportklasse für einen vorhandenen Controller zu bestätigen.

![InputFeatureUsage-Tool](../images/controller-mapping-tool/InputFeatureUsages.png)

## <a name="using-the-inputfeatureusage-tool"></a>Verwenden des InputFeatureUsage-Tools

Navigieren Sie zum Einstieg in das InputFeatureUsage-Tool zu **MRTK/Tools/RuntimeTools/Tools/InputFeatureUsageTool,** und öffnen Sie die **InputFeatureUsageTool-Szene.** Nachdem die Szene geladen wurde, kann das Projekt entweder im Editor, im Wiedergabemodus oder auf einem Gerät erstellt und ausgeführt werden.

So untersuchen Sie die Unity-Zuordnungen für einen Controller:

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

- [Erstellen eines Eingabesystem-Datenanbieters](../input/create-data-provider.md)
- [Controller-Zuordnungstool](controller-mapping-tool.md)
