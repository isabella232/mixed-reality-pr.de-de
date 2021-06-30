---
title: Controller, Zeiger und Fokus
description: Interaktion mit Controllern, Zeigern und Fokus.
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, Zeiger, Controller
ms.openlocfilehash: b3e4438c1318abbc60606bcbca42854edae28167
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121618"
---
# <a name="controllers-pointers-and-focus"></a>Controller, Zeiger und Fokus

Controller, Zeiger und Fokus sind übergeordnete Konzepte, die auf der Grundlage des Kerneingabesystems aufbauen. Zusammen stellen sie einen großen Teil des Mechanismus für die Interaktion mit Objekten in der Szene bereit.

## <a name="controllers"></a>Controller

Controller sind Darstellungen eines physischen Controllers (6-Grad an Freiheit, artikulierte Hand usw.). Sie werden von Geräte-Managern erstellt und sind für die Kommunikation mit dem entsprechenden zugrunde liegenden System und die Übersetzung dieser Daten in MRTK-förmige Daten und Ereignisse verantwortlich.a

Beispielsweise ist auf der Windows Mixed Reality-Plattform ein Controller, der für die [`WindowsMixedRealityArticulatedHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityArticulatedHand) Verknüpfung mit den zugrunde liegenden Windows-APIs zur [Nachverfolgung](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) von Hand verantwortlich ist, um Informationen zu den Fugen, der Pose und anderen Eigenschaften der Hand abzurufen. Es ist dafür verantwortlich, diese Daten in relevante MRTK-Ereignisse zu verwandeln (z. B. durch Aufrufen von RaisePoseInputChanged oder RaiseHandJointsUpdated) und indem der interne Zustand aktualisiert wird, sodass Abfragen für [`TryGetJointPose`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils.TryGetJointPose%2A) die richtigen Daten zurückgeben.

Im Allgemeinen umfasst der Lebenszyklus eines Controllers:

1. Ein Controller wird von einem Geräte-Manager erstellt, wenn eine neue Quelle erkannt wird (der Geräte-Manager erkennt z. B. eine Hand und beginnt damit, sie nachzuverfolgen).

2. In der Update()-Schleife des Controllers ruft er das zugrunde liegende API-System auf.

3. In derselben Updateschleife löst sie Änderungen an Eingabeereignissen aus, indem direkt in das Kerneingabesystem selbst aufgerufen wird (z. B. durch Auslösen von HandMeshUpdated oder HandJointsUpdated).

## <a name="pointers-and-focus"></a>Zeiger und Fokus

Zeiger werden für die Interaktion mit Spielobjekten verwendet. In diesem Abschnitt wird beschrieben, wie Zeiger erstellt werden, wie sie aktualisiert werden und wie sie die Objekte bestimmen, die sich im Fokus befinden. Außerdem werden die verschiedenen Typen vorhandener Zeiger und die Szenarien behandelt, in denen sie aktiv sind.

### <a name="pointer-categories"></a>Zeigerkategorien

Zeiger fallen im Allgemeinen in eine der folgenden Kategorien:

- **Fernzeiger**

  Diese Typen von Zeigern werden verwendet, um mit Objekten zu interagieren, die weit vom Benutzer entfernt sind (weit entfernt wird einfach als "nicht nah" definiert). Diese Zeigertypen geben im Allgemeinen Linien um, die weit in die Welt gehen können und es dem Benutzer ermöglichen, mit Objekten zu interagieren und diese zu bearbeiten, die sich nicht direkt daneben befinden.

- **Zeiger in der Nähe**

  Diese Zeigertypen werden verwendet, um mit Objekten zu interagieren, die dem Benutzer nahe genug sind, um sie zu greifen, zu berühren und zu bearbeiten. Im Allgemeinen interagieren diese Typen von Zeigern mit Objekten, indem sie nach Objekten in der Nähe suchen (entweder durch Raycasting in kleinen Abständen, durch Sphärische Umwandlung nach Objekten in der Nähe oder durch Auflisten von Listen von Objekten, die als greifbar/berührbar angesehen werden).

- **Teleportzeiger**

  Diese Typen von Zeigern werden in das Teleportierungssystem integriert, um das Verschieben des Benutzers an die Position des Zeigers zu verarbeiten.

## <a name="pointer-mediation"></a>Zeigerzeiger

Da ein einzelner Controller über mehrere Zeiger verfügen kann (z. B. kann die artikulierte Hand sowohl nah als auch fern Interaktionszeiger aufweisen), gibt es eine Komponente, die für die Vermittlung des aktiven Zeigers verantwortlich ist.

Wenn sich die Hand des Benutzers beispielsweise einer betätigbaren Schaltfläche nähert, [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) sollte die angezeigt werden, und die sollte [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) eingeschaltet werden.

Dies wird von der [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) behandelt, die basierend auf dem Zustand aller Zeiger bestimmt, welche Zeiger aktiv sind. Einer der wichtigsten Dinge, die dies macht, ist das Deaktivieren von Fernzeigern, wenn sich ein Zeiger in der Nähe eines Objekts befindet (siehe [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) ).

Es ist möglich, eine alternative Implementierung des Zeigermediators bereitzustellen, indem Sie die [`PointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile.PointerMediator) -Eigenschaft im Zeigerprofil ändern.

### <a name="how-to-disable-pointers"></a>Deaktivieren von Zeigern

Da der Zeigermediator jeden Frame ausführt, steuert er am Ende den aktiven/inaktiven Zustand aller Zeiger. Wenn Sie daher die IsInteractionEnabled-Eigenschaft eines Zeigers im Code festlegen, wird sie vom Zeigermediator in jedem Frame überschrieben. Stattdessen können Sie den angeben, [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) um zu steuern, ob Zeiger selbst ein- oder ausgeschaltet werden sollen. Beachten Sie, dass dies nur funktioniert, wenn Sie die Standardeinstellung [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) und [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) in MRTK verwenden.

#### <a name="example-disable-hand-rays-in-mrtk"></a>Beispiel: Deaktivieren von Handlichtlicht im MRTK

Mit dem folgenden Code wird der Handstrahl im MRTK deaktiviert:

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff);

// Turn off hand rays for the right hand only
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Right);
```

Der folgende Code gibt Handlichter an ihr Standardverhalten im MRTK zurück:

```c#
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.Default);
```

Der folgende Code zwingt den Handlichtstrahl, unabhängig davon, ob er sich in der Nähe eines Greifens befindet:

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOn);
```

Weitere Beispiele finden Sie unter [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) und [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) .

### <a name="focusprovider"></a>FocusProvider

[`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider)ist das Arbeitstier, das für das Iterieren der Liste aller Zeiger und das Herausfinden, was das fokussierte Objekt für jeden Zeiger ist, verantwortlich ist.

Bei jedem `Update()` Aufruf geschieht Dies:

1. Aktualisieren Sie alle Zeiger, indem Sie Raycasting durchführen und die Treffererkennung wie vom Zeiger selbst konfiguriert durchführen (beispielsweise könnte der Kugelzeiger den SphereOverlap-RaycastMode angeben, sodass FocusProvider einen kugelbasierten Konflikt erzeugt).

2. Aktualisieren Sie das fokussierte Objekt auf Zeigerbasis (d. h., wenn ein Objekt den Fokus erhält, löst es auch Ereignisse für dieses Objekt aus, wenn ein Objekt den Fokus verliert, würde es den Fokus verlieren usw.).

### <a name="pointer-configuration-and-lifecycle"></a>Zeigerkonfiguration und -lebenszyklus

Zeiger können im Abschnitt *Zeiger* des Eingabesystemprofils [konfiguriert werden.](../features/input/pointers.md)

Die Lebensdauer eines Zeigers sieht im Allgemeinen wie folgt aus:

1. Ein Geräte-Manager erkennt das Vorhandensein eines Controllers. Dieser Geräte-Manager erstellt dann den Satz von Zeigern, die dem Controller zugeordnet sind, über einen Aufruf von [`RequestPointers`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) .

2. Der FocusProvider durchläuft in seiner Update()-Schleife alle gültigen Zeiger und führt die zugeordnete Raycast- oder Treffererkennungslogik aus. Dies wird verwendet, um das Objekt zu bestimmen, das von jedem bestimmten Zeiger fokussiert wird.

    - Da mehrere Eingabequellen gleichzeitig aktiv sein können (z. B. zwei aktive Hände), ist es auch möglich, mehrere Objekte zu haben, die gleichzeitig den Fokus haben.

3. Wenn der Geräte-Manager erkennt, dass eine Controllerquelle verloren gegangen ist, werden die Zeiger, die dem verlorenen Controller zugeordnet sind, abgeschaltet.