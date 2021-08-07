---
title: Kernsystem
description: Eingabesystem, Geräte-Manager und Datenanbieter in MRTK
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Ereignisse
ms.openlocfilehash: ff4c23b796374940de1a1de6b72e08702d6fd24f79234e8ef80dc1210d13d103
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190180"
---
# <a name="core-system"></a>Kernsystem

Das Kernstück des Eingabesystems ist [inputSystem.](../features/input/overview.md)Dabei handelt es sich um einen Dienst, der für die Initialisierung und den Betrieb aller eingabebezogenen Funktionen verantwortlich ist, die dem MRTK zugeordnet sind.

> [!NOTE]
> Es wird davon ausgegangen, dass Leser den Abschnitt "Terminologie" bereits gelesen haben und grundlegende [Kenntnisse haben.](terminology.md)

Dieser Dienst ist für Folgendes verantwortlich:

- Lesen des [Eingabesystemprofils](../configuration/mixed-reality-configuration-guide.md#input-system-settings)
- Starten der konfigurierten [Datenanbieter](../features/input/input-providers.md) (z. B. `Windows Mixed Reality Device Manager` und `OpenVR Device Manager` ).
- Instanziierung von [GazeProvider,](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider)einer Komponente, die für die Bereitstellung von Anvisierungsinformationen im HoloLens-Stil (1. Generation) zusätzlich zu HoloLens 2 Anvisierungsinformationen im Anvisierungsstil verantwortlich ist.
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

Ereignisse können an globale Listener gesendet werden. Es ist möglich, sich mithilfe der -Schnittstelle des Eingabesystems für alle Eingabeereignisse zu [`IMixedRealityEventSystem`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityEventSystem) registrieren. Es wird empfohlen, die [RegisterHandler-Methode](xref:Microsoft.MixedReality.Toolkit.IMixedRealityEventSystem.RegisterHandler%2A) zum Registrieren für globale Ereignisse zu verwenden. Die veraltete Funktion verursacht, dass Listener über ALLE Eingabeereignisse benachrichtigt werden, anstatt nur Eingabeereignisse eines bestimmten Typs (wobei der Typ von der Ereignisschnittstelle definiert `Register` wird).

Beachten Sie, dass [Fallbacklistener](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSystem.PushFallbackInputHandler%2A) eine weitere Art von globalen Listenern sind, von denen ebenfalls abgeraten wird, da sie jedes einzelne Eingabeereignis empfangen, das nicht an anderer Stelle in der Szene behandelt wurde.

### <a name="order-of-event-dispatch"></a>Reihenfolge der Ereignissendung

Im Allgemeinen werden Ereignisse auf folgende Weise an Listener gesendet. Beachten Sie, dass der Ereignis dispatch-Prozess beendet wird, wenn einer der folgenden Schritte das Ereignis als behandelt bezeichnet. [](https://docs.unity3d.com/ScriptReference/EventSystems.AbstractEventData-used.html)

1. Das Ereignis wird an globale Listener gesendet.
2. Das Ereignis wird an modale Dialoge des fokussierten Objekts gesendet.
3. Das Ereignis wird an das fokussierte Objekt gesendet.
4. Das Ereignis wird an Fallbacklistener gesendet.

## <a name="device-managers-and-data-providers"></a>Geräte-Manager und Datenanbieter

Diese Entitäten sind für die Interfacing mit APIs auf niedrigerer Ebene (z. B. Windows Mixed Reality-APIs oder OpenVR-APIs) und für die Übersetzung von Daten aus diesen Systemen in Solche zuständig, die den Eingabeabstraktionen des MRTK auf höherer Ebene passen. Sie sind für die Erkennung, Erstellung und Verwaltung der Lebensdauer von [Controllern verantwortlich.](controllers-pointers-and-focus.md#controllers)

Der grundlegende Ablauf eines Geräte-Managers umfasst:

1. Der Geräte-Manager wird vom Eingabesystemdienst instanziiert.
2. Der Geräte-Manager registriert sich bei seinem zugrunde liegenden System (z. B. registriert Windows Mixed Reality Geräte-Manager für Eingabe- [und](../features/input/input-events.md) [Gestenereignisse.](../features/input/gestures.md#gesture-events)
3. Er erstellt Controller, die er aus dem zugrunde liegenden System ermittelt (z. B. könnte der Anbieter das Vorhandensein von artikulierten Händen erkennen).
4. Rufen Sie in der Update()-Schleife UpdateController() auf, um den neuen Zustand des zugrunde liegenden Systems zu erhalten und seine Controllerdarstellung zu aktualisieren.
