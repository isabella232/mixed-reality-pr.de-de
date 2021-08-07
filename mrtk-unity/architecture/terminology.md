---
title: Begriff
description: Verschiedene Eingabesystembegriffe im MRTK.
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Eingabe,
ms.openlocfilehash: 8046501fdab0a7594800a75ad0306a131adaaa6924ffa870c299571cbd4d8e13
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211156"
---
# <a name="input-system"></a>Eingabesystem

Das Eingabesystem ist eines der größten Systeme aller vom MRTK angebotenen Features.
Viele Dinge im Toolkit bauen darauf auf (Zeiger, Fokus, Prefabs). Der Code im Eingabesystem ermöglicht natürliche Interaktionen wie greifen und plattformübergreifend drehen.

Das Eingabesystem verfügt über eine eigene Terminologie, die es zu definieren lohnt:

- **Datenanbieter**

    Die Eingabeeinstellungen im Eingabeprofil enthalten Verweise auf Entitäten, die als Datenanbieter bezeichnet werden. Ein weiteres Wort, das diese beschreibt, sind Geräte-Manager. Hierbei handelt es sich um Komponenten, deren Aufgabe es ist, das MRTK-Eingabesystem zu erweitern, indem ein Interfacing mit einem bestimmten zugrunde liegenden System erfolgt. Ein Beispiel für einen Anbieter ist der Windows Mixed Reality Anbieter, dessen Aufgabe es ist, mit den zugrunde liegenden Windows Mixed Reality-APIs zu kommunizieren und dann die Daten aus diesen APIs in MRTK-spezifische Eingabekonzepte weiter unten zu übersetzen. Ein weiteres Beispiel wäre der OpenVR-Anbieter (dessen Aufgabe es ist, mit einer unity-abstrahierten Version von OpenVR-APIs zu kommunizieren und diese Daten dann in MRTK-Eingabekonzepte zu übersetzen).

- **Controller**

    Eine Darstellung eines physischen Controllers (unabhängig davon, ob es sich um einen 6-Freiheitscontroller, eine HoloLens Hand im 1-Stil mit Gestenunterstützung, eine vollständig artikulierte Hand, einen Schaltbewegungscontroller usw.) Controller werden von Geräte-Managern erzeugt (d. h., der WMR-Geräte-Manager erzeugt einen Controller und verwaltet seine Lebensdauer, wenn eine artikulierte Hand vorhanden ist).

- **Zeiger**

    Controller verwenden Zeiger für die Interaktion mit Spielobjekten. Beispielsweise ist der Near-Interaktionszeiger dafür verantwortlich, zu erkennen, wann sich die Hand (ein Controller) in der Nähe von Objekten befindet, die sich selbst als unterstützende "Nahinteraktion" ankündigen. Weitere Beispiele für Zeiger sind Teleportierung oder Fernzeiger (d. h. der Handstrahlzeiger der Shell), die fernen Raycast verwenden, um mit Inhalten zu interagieren, die vom Benutzer länger als die Länge der Arme sind.

    Zeiger werden vom Geräte-Manager erstellt und dann an eine Eingabequelle angefügt. Um alle Zeiger für einen Controller abzurufen, gehen Sie folgendes vor: `controller.InputSource.Pointers`

    Beachten Sie, dass ein Controller gleichzeitig vielen verschiedenen Zeigern zugeordnet werden kann. Um sicherzustellen, dass dies nicht ins Chaos übergeht, gibt es einen Zeigermediator, der steuert, welche Zeiger aktiv sein dürfen (der Vermittler deaktiviert z. B. Zeiger für die fernen Interaktion, wenn nah an der Interaktion erkannt wird).

- **Fokus**

    Zeigerereignisse werden an Objekte im **Fokus** gesendet. Die Fokusauswahl variiert je nach Zeigertyp. Ein Handstrahlzeiger verwendet Raycasts, während ein Pfeilzeiger Spherecasts verwendet. Ein Objekt muss IMixedRealityFocusHandler implementieren, um den Fokus zu erhalten. Es ist möglich, ein Objekt global zu registrieren, um ungefilterte Zeigerereignisse zu empfangen. Dieser Ansatz wird jedoch nicht empfohlen.

    Die Komponente, die aktualisiert, welche Objekte sich im Fokus befinden, ist der [FocusProvider.](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider)

- **Cursor**

    Eine Entität, die einem Zeiger zugeordnet ist, der zusätzliche visuelle Hinweise zur Zeigerinteraktion liefert. Der FingerCursor rendert z. B. einen Ring um den Finger und kann diesen Ring drehen, wenn sich der Finger in der Nähe von "nahezu interaktiven" Objekten befindet. Ein Zeiger kann gleichzeitig einem einzelnen Cursor zugeordnet werden.

- **Interaktion und Bearbeitung**

    Objekte können mit einem Interaktions- oder Bearbeitungsskript gekennzeichnet werden. Dies kann über eine [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) oder in etwa wie [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) / [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) erfolgen.

    Beispielsweise ermöglichen NearInteractionGrabbable und NearInteractionTouchable, dass bestimmte Zeiger (insbesondere Near Interaction-Zeiger) wissen, auf welche Objekte der Fokus gerichtet werden kann.

    Interactable und ManipulationHandler sind Beispiele für Komponenten, die auf Zeigerereignisse lauschen, um Benutzeroberflächenvisuals zu ändern oder Spielobjekte zu verschieben/zu skalieren/zu drehen.

In der folgenden Abbildung wird die obere Ebene des MRTK-Eingabestapels (von unten nach oben) erfasst:

![Eingabesystemdiagramm](../features/images/input/MRTK_InputSystem.png)
