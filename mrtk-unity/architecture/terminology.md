---
title: Begriff
description: Verschiedene Eingabesystembegriffe im MRTK.
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Eingabe,
ms.openlocfilehash: 33f423fba286e9e85e6d0bedac82bff0b7aae81f
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121458"
---
# <a name="input-system"></a>Eingabesystem

Das Eingabesystem ist eines der größten Systeme aller Features, die vom MRTK angeboten werden.
So viele Dinge im Toolkit bauen darauf auf (Zeiger, Fokus, Prefabs). Der Code im Eingabesystem ermöglicht natürliche Interaktionen wie das Greifen und Drehen über Plattformen hinweg.

Das Eingabesystem verfügt über einige eigene Terminologie, die es zu definieren lohnt:

- **Datenanbieter**

    Die Eingabeeinstellungen im Eingabeprofil enthalten Verweise auf Entitäten, die als Datenanbieter bezeichnet werden. Ein weiteres Wort, das diese beschreibt, sind Geräte-Manager. Hierbei handelt es sich um Komponenten, deren Aufgabe es ist, das MRTK-Eingabesystem durch die Interfacing mit einem bestimmten zugrunde liegenden System zu erweitern. Ein Beispiel für einen Anbieter ist der Windows Mixed Reality-Anbieter, dessen Aufgabe es ist, mit den zugrunde liegenden Windows Mixed Reality-APIs zu sprechen und dann die Daten aus diesen APIs unten in MRTK-spezifische Eingabekonzepte zu übersetzen. Ein weiteres Beispiel wäre der OpenVR-Anbieter (dessen Aufgabe es ist, mit einer von Unity abstrahierten Version der OpenVR-APIs zu sprechen und diese Daten dann in MRTK-Eingabekonzepte zu übersetzen).

- **Controller**

    Eine Darstellung eines physischen Controllers (unabhängig davon, ob es sich um einen 6-Grad-Freiheitscontroller, eine Hand im HoloLens 1-Stil mit Gestenunterstützung, eine vollständig artikulierte Hand, einen Schaltbewegungscontroller usw.) ist. Controller werden von Geräte-Managern geerbt (d. h., der WMR-Geräte-Manager wird einen Controller erstellen und seine Lebensdauer verwalten, wenn eine artikulierte Hand ins Leben kommt).

- **Zeiger**

    Controller verwenden Zeiger für die Interaktion mit Spielobjekten. Beispielsweise ist der Nahinteraktionszeiger für die Erkennung verantwortlich, wenn sich die Hand (die ein Controller ist) in der Nähe von Objekten befindet, die sich selbst als Unterstützung für "Near Interaction" (Nahinteraktion) ankrebt. Weitere Beispiele für Zeiger sind Teleportierung oder Fernzeiger (d. h. der Handstrahlzeiger der Shell), die ferne Raycasts verwenden, um mit Inhalten zu interagieren, die länger als die Armlänge des Benutzers sind.

    Zeiger werden vom Geräte-Manager erstellt und dann an eine Eingabequelle angefügt. Gehen Sie wie im folgenden Beispiel vor, um alle Zeiger für einen Controller zu erhalten: `controller.InputSource.Pointers`

    Beachten Sie, dass ein Controller vielen verschiedenen Zeigern gleichzeitig zugeordnet werden kann. Um sicherzustellen, dass dies nicht zu Chaos führt, gibt es einen Zeigermediator, der steuert, welche Zeiger aktiv sein dürfen (z. B. deaktiviert der Vermittler ferne Interaktionszeiger, wenn eine nahe Interaktion erkannt wird).

- **Fokus**

    Zeigerereignisse werden an Objekte im Fokus **gesendet.** Die Fokusauswahl variiert je nach Zeigertyp. Ein Handstrahlzeiger verwendet Raycasts, während ein Pokezeiger Spherecasts verwendet. Ein Objekt muss IMixedRealityFocusHandler implementieren, um den Fokus zu erhalten. Es ist möglich, ein Objekt global zu registrieren, um ungefilterte Zeigerereignisse zu empfangen. Dieser Ansatz wird jedoch nicht empfohlen.

    Die Komponente, die aktualisiert, welche Objekte sich im Fokus befinden, ist [der FocusProvider.](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider)

- **Cursor**

    Eine Entität, die einem Zeiger zugeordnet ist, der zusätzliche visuelle Hinweise zur Zeigerinteraktion bietet. Der FingerCursor rendert z. B. einen Ring um Ihren Finger und rotiert diesen Ring möglicherweise, wenn sich Ihr Finger in der Nähe von "nahezu interagierbaren" Objekten befindet. Ein Zeiger kann einem einzelnen Cursor gleichzeitig zugeordnet werden.

- **Interaktion und Manipulation**

    Objekte können mit einem Interaktions- oder Bearbeitungsskript gekennzeichnet werden. Dies kann über einen [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) oder etwas wie [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) / [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) sein.

    NearInteractionGrabbable und NearInteractionTouchable ermöglichen es z. B. bestimmten Zeigern (insbesondere Nahinteraktionszeigenden), zu wissen, auf welche Objekte sich konzentrieren kann.

    Interactable und ManipulationHandler sind Beispiele für Komponenten, die auf Zeigerereignisse lauschen, um visuelle Benutzeroberflächenelemente zu ändern oder Spielobjekte zu verschieben/zu skalieren/zu drehen.

In der folgenden Abbildung ist der (von unten nach oben) obere Aufbau des MRTK-Eingabestapels dargestellt:

![Eingabesystemdiagramm](../features/images/input/MRTK_InputSystem.png)
