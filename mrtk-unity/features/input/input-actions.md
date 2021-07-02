---
title: Eingabeaktionen
description: Dokumentation zum Erstellen von Eingabeaktionen im MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, Development, MRTK, InputActions,
ms.openlocfilehash: cf6ce2af304ee1cd706d0111d66a97018113fb09
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176810"
---
# <a name="input-actions"></a>Eingabeaktionen

[**Eingabeaktionen**](input-actions.md) sind Abstraktionen über rohe Eingaben, die dazu beitragen sollen, die Anwendungslogik von den spezifischen Eingabequellen zu isolieren, die eine Eingabe erzeugen. Es kann beispielsweise nützlich sein, eine *Select-Aktion* zu definieren und sie der linken Maustaste, einer Schaltfläche in einem Gamepad und einem Trigger in einem 6-DOF-Controller zu zuordnen. Sie können ihre Anwendungslogik dann auf Select *input* action events (Eingabeaktionsereignisse auswählen) lauschen lassen, anstatt alle verschiedenen Eingaben kennen zu müssen, die sie erzeugen können.

## <a name="creating-an-input-action"></a>Erstellen einer Eingabeaktion

Eingabeaktionen werden im Eingabeaktionsprofil im Eingabesystemprofil *in* der Mixed Reality Toolkit-Komponente konfiguriert und geben einen Namen für die Aktion und den Typ der Eingaben (*Achseneinschränkung*) an, dem sie zugeordnet werden kann:

<img src="../images/input/InputActions.png" alt="Input Action" style="max-width:100%;">

Dies sind die am häufigsten verwendeten Werte für **Axis Constraint**:

Achseneinschränkung | Beschreibung
--- | ---
Digital | Ein-/Aus-Eingabe wie eine binäre Schaltfläche in einem Gamepad oder einer Maus.
Einzelne Achse | Einachseneingaben wie ein analoger Trigger in einem Gamepad.
Duale Achse | Eingabe der Doppelachsen-Achse wie ein Fingerabdruck.
Sechs Dof | 3D-Posen mit Übersetzung und Drehung wie bei 6 DOF-Controllern.

Die vollständige Liste finden Sie unter [`AxisType`](xref:Microsoft.MixedReality.Toolkit.Utilities.AxisType) .

## <a name="mapping-input-to-actions"></a>Zuordnen von Eingaben zu Aktionen

Die Art und Weise, wie Sie eine Eingabe und aktion zuordnen, hängt vom Typ der Eingabequelle ab:

### <a name="controller-input"></a>Controllereingabe

Wechseln Sie unter **dem Eingabesystemprofil** zum *Controller-Eingabezuordnungsprofil.* Dort finden Sie eine Liste aller unterstützten Controller:

<img src="../images/input/ControllerInputMappingProfile.PNG" alt="Input maping profile" style="max-width:100%;">

Wählen Sie das Dialogfeld aus, das Sie konfigurieren möchten, und es wird ein Dialogfeld mit allen Controllereingaben angezeigt, sodass Sie eine Aktion für jede von ihnen festlegen können:

<img src="../images/input/InputActionAssignment.PNG" alt="Input Action Assignment" style="max-width:100%;">

### <a name="speech-input"></a>Spracheingabe

Im **Speech-Befehlsprofil** finden Sie unter dem *Eingabesystemprofil* die Liste der derzeit definierten Sprachbefehle. Um einer Aktion eines davon zu zuordnen, wählen Sie es einfach in der *Dropdownliste Aktion* aus.

<img src="../images/input/SpeechCommandsProfile.png" alt="Speech Commands profile" style="max-width:100%;">

### <a name="gesture-input"></a>Gesteneingabe

Das **Gestenprofil** unter dem *Eingabesystemprofil* enthält alle definierten Gesten. Sie können jede aktion zuordnen, indem Sie sie in der *Dropdownliste Aktion* auswählen.

<img src="../images/input/GestureProfile.png" alt="Gesture profile" style="max-width:100%;">

## <a name="handling-input-actions"></a>Behandeln von Eingabeaktionen

> [!WARNING]
> Derzeit können nur Eingabeaktionen *vom Typ Digital* mithilfe der in diesem Abschnitt beschriebenen Methoden verarbeitet werden. Bei anderen Aktionstypen müssen Sie stattdessen die Ereignisse für die entsprechenden Eingaben direkt behandeln. Um beispielsweise eine 6-DOF-Aktion zu verarbeiten, die Controllereingaben zugeordnet ist, müssen Sie mit [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) T = [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) verwenden.

Die einfachste Möglichkeit zur Handhabung von Eingabeaktionen besteht in der Verwendung des [`InputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.InputActionHandler) Skripts. Auf diese Weise können Sie die Aktion definieren, auf die Sie lauschen möchten, und mit Unity-Ereignissen auf gestartete und beendete Ereignisse reagieren.

<img src="../images/input/InputActionHandler.PNG" alt="Acton Handler" style="max-width:100%;">

Wenn Sie mehr Kontrolle wünschen, können Sie die [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) -Schnittstelle direkt in Ihrem Skript implementieren. Weitere Informationen [**zur Ereignisbehandlung über**](input-events.md) Handlerschnittstellen finden Sie im Abschnitt Eingabeereignisse.

## <a name="examples"></a>Beispiele

Sehen `MRTK/Examples/Demos/Input/Scenes/InputActions` Sie sich eine Beispielszene an, die zeigt, wie Sie eine Aktion erstellen, sie Controller-, Sprach- und Gesteneingaben zuordnen und damit ein Objekt auf Befehl drehen.

<img src="../images/input/InputActionsExample.PNG" alt="Input action example" style="max-width:100%;">
