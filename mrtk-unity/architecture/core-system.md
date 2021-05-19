---
title: Kernsystem
description: Eingabesystem, Geräte-Manager und Datenanbieter in MRTK
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Ereignisse
ms.openlocfilehash: 12719a6c749a03648d4f75e9e6461b85cc9ab275
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144297"
---
# <a name="core-system"></a>Kernsystem

Das Kernstück des Eingabesystems ist [inputSystem.](../features/input/overview.md)Dabei handelt es sich um einen Dienst, der für die Initialisierung und den Betrieb aller eingabebezogenen Funktionen verantwortlich ist, die dem MRTK zugeordnet sind.

> [!NOTE]
> Es wird davon ausgegangen, dass Leser den Abschnitt "Terminologie" bereits gelesen haben und grundlegende [Kenntnisse haben.](terminology.md)

Dieser Dienst ist für Folgendes verantwortlich:

- Lesen des [Eingabesystemprofils](../configuration/mixed-reality-configuration-guide.md#input-system-settings)
- Starten der [konfigurierten Datenanbieter](../features/input/input-providers.md) (z. B. `Windows Mixed Reality Device Manager` und `OpenVR Device Manager` ).
- Instanziierung von [GazeProvider,](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider)einer Komponente, die für die Bereitstellung von Anvisierungsinformationen im HoloLens-Stil (1. Generation) verantwortlich ist, zusätzlich zu HoloLens 2 anvisierungsinformationen.
- Instanziierung des [FocusProvider,](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusProvider)bei dem es sich um eine Komponente handelt, die für die Bestimmung von Objekten zuständig ist, die den Fokus haben. Dies wird im Abschnitt Zeiger [und](controllers-pointers-and-focus.md#pointers-and-focus) Fokus der Dokumentation genauer beschrieben.
- Bereitstellen von Registrierungspunkten für alle Eingabeereignisse [(als globale Listener).](#global-listeners)
- Bereitstellen von Ereignis dispatch-Funktionen für diese Eingabeereignisse.

## <a name="input-events"></a>Eingabeereignisse

Eingabeereignisse werden in der Regel auf zwei verschiedenen Kanälen ausgelöst:

### <a name="objects-in-focus"></a>Objekte im Fokus

Ereignisse können direkt an ein GameObject gesendet werden, das den Fokus besitzt. Ein Objekt kann beispielsweise über ein Skript verfügen, das [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) implementiert.
Dieses Objekt würde Berührungsereignisse erhalten, wenn es von einer Hand, die sich in der Nähe befindet, fokussiert wird. Diese Ereignistypen werden in der GameObject-Hierarchie "nach oben" angezeigt, bis ein GameObject gefunden wird, das das Ereignis behandeln kann.

Dies erfolgt [mithilfe von ExecuteHierarchy](https://docs.unity3d.com/ScriptReference/EventSystems.ExecuteEvents.ExecuteHierarchy.html) innerhalb der Standardimplementierung des Eingabesystems.

### <a name="global-listeners"></a>Globale Listener

Ereignisse können an globale Listener gesendet werden. Es ist möglich, sich für alle Eingabeereignisse zu registrieren, indem Sie die Schnittstelle des Eingabesystems [`IMixedRealityEventSystem`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityEventSystem) verwenden. Es wird empfohlen, die [RegisterHandler-Methode](xref:Microsoft.MixedReality.Toolkit.IMixedRealityEventSystem.RegisterHandler%2A) für die Registrierung für globale Ereignisse zu verwenden. Die veraltete `Register` Funktion bewirkt, dass Listener über ALLE Eingabeereignisse benachrichtigt werden, anstatt nur Eingabeereignisse eines bestimmten Typs (wobei der Typ durch die Ereignisschnittstelle definiert wird).

Beachten Sie, dass [Fallbacklistener](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSystem.PushFallbackInputHandler%2A) eine andere Art von globalen Listenern sind, von denen ebenfalls abgeraten wird, da sie jedes einzelne Eingabeereignis empfangen, das nicht an anderer Stelle in der Szene behandelt wurde.

### <a name="order-of-event-dispatch"></a>Reihenfolge der Ereignisdisponent

Im Allgemeinen werden Ereignisse wie folgt an Listener gesendet. Beachten Sie Folgendes: Wenn einer der folgenden Schritte das Ereignis als [behandelt](https://docs.unity3d.com/ScriptReference/EventSystems.AbstractEventData-used.html)markiert, wird der Ereignisdisponierungsprozess beendet.

1. Das Ereignis wird an globale Listener gesendet.
2. Das Ereignis wird an modale Dialoge des fokussierten Objekts gesendet.
3. Das Ereignis wird an das fokussierte Objekt gesendet.
4. Das Ereignis wird an Fallbacklistener gesendet.

## <a name="device-managers-and-data-providers"></a>Geräte-Manager und Datenanbieter

Diese Entitäten sind für die Verknüpfung mit APIs auf niedrigerer Ebene (z. B. Windows Mixed Reality-APIs oder OpenVR-APIs) und die Übersetzung von Daten aus diesen Systemen in Solche verantwortlich, die den übergeordneten Eingabeabstraktionen des MRTK entsprechen. Sie sind für das Erkennen, Erstellen und Verwalten der Lebensdauer von [Controllern](controllers-pointers-and-focus.md#controllers)verantwortlich.

Der grundlegende Ablauf eines Geräte-Managers umfasst Folgendes:

1. Der Geräte-Manager wird vom Eingabesystemdienst instanziiert.
2. Der Geräte-Manager registriert sich beim zugrunde liegenden System (z. B. registriert sich der Windows Mixed Reality Geräte-Manager für [Eingabe-](../features/input/input-events.md) und [Gestenereignisse.](../features/input/gestures.md#gesture-events)
3. Er erstellt Controller, die er aus dem zugrunde liegenden System ermittelt (z. B. kann der Anbieter das Vorhandensein von artikulierten Händen erkennen)
4. Rufen Sie in der Update()-Schleife UpdateController() auf, um den neuen Zustand des zugrunde liegenden Systems abzufragen und seine Controllerdarstellung zu aktualisieren.
