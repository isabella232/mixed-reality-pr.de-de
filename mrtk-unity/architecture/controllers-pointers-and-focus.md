---
title: Controller, Zeiger und Fokus
description: Interaktion mit Controllern, Zeigern und Fokus.
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Zeiger, Controller
ms.openlocfilehash: 00bc0641182c566b045f959dfa361e1311b3cd224fc998f154010ad2996679ae
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196290"
---
# <a name="controllers-pointers-and-focus"></a>Controller, Zeiger und Fokus

Controller, Zeiger und Fokus sind Konzepte auf höherer Ebene, die auf der Grundlage des kernbasierten Eingabesystems aufbauen. Zusammen stellen sie einen großen Teil des Mechanismus für die Interaktion mit Objekten in der Szene dar.

## <a name="controllers"></a>Controller

Controller sind Darstellungen eines physischen Controllers (6-Grad an Freiheit, artikulierte Hand usw.). Sie werden von Geräte-Managern erstellt und sind für die Kommunikation mit dem entsprechenden zugrunde liegenden System und die Übersetzung dieser Daten in MRTK-förmige Daten und Ereignisse verantwortlich.

Auf der Windows Mixed Reality-Plattform ist z. B. ein Controller, der für die Interfacing mit den zugrunde liegenden Windows-APIs für die Handverfolgung verantwortlich ist, um Informationen zu den Fugen, der Pose und anderen Eigenschaften der Hand zu [`WindowsMixedRealityArticulatedHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityArticulatedHand) erhalten. [](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) Sie ist dafür verantwortlich, diese Daten in relevante MRTK-Ereignisse zu ändern (z. B. durch Aufrufen von RaisePoseInputChanged oder RaiseHandJointsUpdated) und ihren eigenen internen Zustand zu aktualisieren, damit Abfragen für die richtigen Daten [`TryGetJointPose`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils.TryGetJointPose%2A) zurückgeben.

Im Allgemeinen umfasst der Lebenszyklus eines Controllers:

1. Ein Controller wird von einem Geräte-Manager erstellt, wenn eine neue Quelle erkannt wird (der Geräte-Manager erkennt z. B. eine Hand und beginnt mit der Nachverfolgung).

2. In der Update()-Schleife des Controllers ruft er das zugrunde liegende API-System auf.

3. In derselben Updateschleife löst sie Eingabeereignisänderungen aus, indem sie direkt in das Kerneingabesystem selbst aufruft (z. B. HandMeshUpdated oder HandJointsUpdated).

## <a name="pointers-and-focus"></a>Zeiger und Fokus

Zeiger werden für die Interaktion mit Spielobjekten verwendet. In diesem Abschnitt wird beschrieben, wie Zeiger erstellt werden, wie sie aktualisiert werden und wie sie die Objekte bestimmen, die sich im Fokus befinden. Außerdem werden die verschiedenen Typen von Zeigern und die Szenarien, in denen sie aktiv sind, beschrieben.

### <a name="pointer-categories"></a>Zeigerkategorien

Zeiger fallen in der Regel in eine der folgenden Kategorien:

- **Far-Zeiger**

  Diese Zeigertypen werden für die Interaktion mit Objekten verwendet, die weit vom Benutzer entfernt sind (weit entfernt ist einfach als "nicht nah" definiert). Diese Zeigertypen geben in der Regel Linien um, die weit in die Welt gehen können und es dem Benutzer ermöglichen, mit Objekten zu interagieren und diese zu bearbeiten, die sich nicht unmittelbar neben ihnen befinden.

- **Zeiger in der Nähe**

  Diese Zeigertypen werden für die Interaktion mit Objekten verwendet, die dem Benutzer nahe genug sind, um sie zu greifen, zu berühren und zu bearbeiten. Im Allgemeinen interagieren diese Zeigertypen mit Objekten, indem sie nach Objekten in der nähe gelegenen Umgebung suchen (entweder durch Raycasting in kleinen Entfernungen, durch pherische Umwandlung nach Objekten in der Nähe oder durch Aufzählen von Listen von Objekten, die als begreifbar/berührbar gelten).

- **Teleport-Zeiger**

  Diese Zeigertypen werden in das Teleportierungssystem integriert, um das Verschieben des Benutzers an den Zielort des Zeigers zu verarbeiten.

## <a name="pointer-mediation"></a>Pointer-2016

Da ein einzelner Controller über mehrere Zeiger verfügen kann (z. B. kann die artikulierte Hand sowohl Nah- als auch Ferninteraktionszeiger haben), gibt es eine Komponente, die für die Kommunikation zuständig ist, welcher Zeiger aktiv sein soll.

Wenn sich die Hand des Benutzers z. B. einer bedruckbaren Schaltfläche nähert, sollte die nicht mehr angezeigt [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) werden, und [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) sollte eingeschaltet werden.

Dies wird vom behandelt, der dafür verantwortlich ist, basierend auf dem Zustand aller Zeiger zu bestimmen, welche Zeiger [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) aktiv sind. Eine der wichtigsten Funktionen ist das Deaktivieren von Fernzeigern, wenn sich ein Zeiger in der Nähe eines Objekts befindet (siehe [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) ).

Sie können eine alternative Implementierung des Zeigermediators bereitstellen, indem Sie die [`PointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile.PointerMediator) -Eigenschaft im Zeigerprofil ändern.

### <a name="how-to-disable-pointers"></a>Deaktivieren von Zeigern

Da der Zeigermediator jeden Frame ausgeführt, steuert er am Ende den aktiven/inaktiven Zustand aller Zeiger. Wenn Sie daher die IsInteractionEnabled-Eigenschaft eines Zeigers im Code festlegen, wird sie von jedem Frame vom Zeigermediator überschrieben. Stattdessen können Sie angeben, um zu steuern, ob [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) Zeiger selbst ein- oder ausgeschaltet werden sollen. Beachten Sie, dass dies nur funktioniert, wenn Sie die Standardeinstellung und [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) im MRTK verwenden.

#### <a name="example-disable-hand-rays-in-mrtk"></a>Beispiel: Deaktivieren von Handlichtstrahl im MRTK

Der folgende Code deaktiviert den Handlichtstrahl im MRTK:

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff);

// Turn off hand rays for the right hand only
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Right);
```

Der folgende Code gibt Handlichtlichter an ihr Standardverhalten im MRTK zurück:

```c#
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.Default);
```

Der folgende Code erzwingen, dass Handlichtlichter ein-on sind, unabhängig davon, ob sie sich in der Nähe eines greifbaren sehen können:

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOn);
```

Weitere [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) Beispiele finden Sie unter und [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) .

### <a name="focusprovider"></a>FocusProvider

ist das Arbeitstier, das dafür verantwortlich ist, die Liste aller Zeiger zu iterieren und herauszufinden, was das fokussierte Objekt für [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) jeden Zeiger ist.

In `Update()` jedem Aufruf wird Dies:

1. Aktualisieren Sie alle Zeiger durch Raycasting und Treffererkennung, wie vom Zeiger selbst konfiguriert (z. B. könnte der Kugelzeiger den SphereOverlap raycastMode angeben, sodass FocusProvider einen kugelbasierten Kollisionsfall macht).

2. Aktualisieren Sie das fokussierte Objekt auf Zeigerbasis (d. h., wenn ein Objekt den Fokus erlangt, würde es auch Ereignisse für dieses Objekt auslösen, wenn ein Objekt den Fokus verliert, würde es den Fokus verlieren usw.).

### <a name="pointer-configuration-and-lifecycle"></a>Zeigerkonfiguration und Lebenszyklus

[Zeiger können im Abschnitt](../features/input/pointers.md)  Zeiger des Eingabesystemprofils konfiguriert werden.

Die Lebensdauer eines Zeigers ist im Allgemeinen wie folgt:

1. Ein Geräte-Manager erkennt das Vorhandensein eines Controllers. Dieser Geräte-Manager erstellt dann den Satz von Zeigern, die dem Controller zugeordnet sind, über einen Aufruf von [`RequestPointers`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) .

2. Der FocusProvider durch iteriert in seiner Update()-Schleife alle gültigen Zeiger und übernimmt die zugeordnete Raycast- oder Treffererkennungslogik. Dies wird verwendet, um das Objekt zu bestimmen, das von jedem bestimmten Zeiger fokussiert wird.

    - Da mehrere Eingabequellen gleichzeitig aktiv sein können (z. B. zwei aktive Hände), können auch mehrere Objekte gleichzeitig den Fokus haben.

3. Nachdem der Geräte-Manager festgestellt hat, dass eine Controllerquelle verloren gegangen ist, werden die Zeiger, die dem verloren gegangenen Controller zugeordnet sind, gelöscht.