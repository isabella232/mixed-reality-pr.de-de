---
title: Eingabefunktionsverwendungs-Tool
description: DokumentationseingabeFeatureUsage-Tool in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 0f2d3d3eb07d8b631f3f11a8b497a22a028a2f24
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145009"
---
# <a name="inputfeatureusage-tool"></a>InputFeatureUsage-Tool

Das InputFeatureUsage-Tool ist ein Runtimetool (auf dem Gerät oder im Editor), mit dem Entwickler schnell die verfügbaren Unity InputFeatureUsages für eine erkannte Eingabequelle (z. B. Motion Controller oder artikulierte Hand) ermitteln können.

> [!NOTE]
> Diese Szene funktioniert nur in Unity 2019.3 oder höher.

Dieses Tool ist sehr nützlich, wenn Sie Unterstützung für einen neuen Hardwarecontroller entwickeln. Es kann auch helfen, ein vermutetes Problem bei der Zuordnung von Steuerelementen in der Supportklasse für einen vorhandenen Controller zu bestätigen.

![InputFeatureUsage-Tool](../images/controller-mapping-tool/InputFeatureUsages.png)

## <a name="using-the-inputfeatureusage-tool"></a>Verwenden des InputFeatureUsage-Tools

Um mit dem InputFeatureUsage-Tool zu beginnen, navigieren Sie zu **MRTK/Tools/RuntimeTools/Tools/InputFeatureUsageTool,** und öffnen Sie die Szene **InputFeatureUsageTool.** Nachdem die Szene geladen wurde, kann das Projekt entweder im Editor, im Wiedergabemodus oder auf einem Gerät erstellt und ausgeführt werden.

So untersuchen Sie die Zuordnungen von Unity für einen Controller:

- Verbinden des Controllers
- Drücken Sie die einzelnen Schaltflächen, und verschieben Sie jede Achse.
- Beachten Sie die Featureverwendungen in der Anzeige.
- Aktualisieren der Steuerelementzuordnungen im Eingabesystemdatenanbieter für den Controller

> [!NOTE]
> Das InputFeatureUsage-Tool nutzt keine Microsoft Mixed Reality Toolkit-Komponenten. Es kommuniziert direkt mit Unity, um die Nutzung der Features zu ermitteln und anzuzeigen.

### <a name="panels"></a>Panels

Die Bereiche zeigen den aktuellen Status aller gemeldeten InputFeatureUsages für alle erkannten Unity-Eingabequellen an.

Der kleinere Bereich am oberen Rand listet die Namen aller erkannten Quellen auf.

## <a name="see-also"></a>Weitere Informationen

- [Erstellen eines Eingabesystemdatenanbieters](../input/create-data-provider.md)
- [Controllerzuordnungstool](controller-mapping-tool.md)
