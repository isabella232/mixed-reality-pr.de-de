---
title: Eingabeaktionen
description: Dokumentation zum Erstellen von Eingabeaktionen in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK, InputActions,
ms.openlocfilehash: 071d4bc8bb4193a3d60cb53852c192ae975d79df
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144157"
---
# <a name="input-actions"></a>Eingabeaktionen

[**Eingabeaktionen**](input-actions.md) sind Abstraktionen über unformatierte Eingaben, die dazu dienen sollen, die Anwendungslogik von den spezifischen Eingabequellen zu isolieren, die eine Eingabe erzeugen. Es kann beispielsweise nützlich sein, eine *Select-Aktion* zu definieren und sie der linken Maustaste, einer Schaltfläche in einem Gamepad und einem Trigger in einem 6-DOF-Controller zuzuordnen. Sie können ihre Anwendungslogik dann auf Select input action events (Eingabeaktionsereignisse *auswählen)* lauschen lassen, anstatt alle verschiedenen Eingaben kennen zu müssen, die sie erzeugen können.

## <a name="creating-an-input-action"></a>Erstellen einer Eingabeaktion

Eingabeaktionen werden im **Eingabeaktionsprofil** innerhalb des *Eingabesystemprofils* in der Komponente Mixed Reality Toolkit konfiguriert und geben einen Namen für die Aktion und den Typ der Eingaben *(Achseneinschränkung)* an, denen sie zugeordnet werden kann:

<img src="../images/input/InputActions.png" alt="Input Action" style="max-width:100%;">

Dies sind die am häufigsten verwendeten Werte für **Achseneinschränkung:**

Achseneinschränkung | Beschreibung
--- | ---
Digital | Ein-/Aus-Eingabe wie eine binäre Schaltfläche in einem Gamepad oder einer Maus.
Einzelne Achse | Eingabe für die Einachsenentsprechung wie ein analoger Trigger in einem Gamepad.
Duale Achse | Eingabe der Doppelachsenentsprechung wie ein Thumbstick.
Sechs Dof | 3D-Posen mit Übersetzung und Drehung wie die von 6 DOF-Controllern erzeugte.

Die vollständige Liste finden Sie unter [`AxisType`](xref:Microsoft.MixedReality.Toolkit.Utilities.AxisType) .

## <a name="mapping-input-to-actions"></a>Zuordnen von Eingaben zu Aktionen

Die Art und Weise, wie Sie eine Eingabe und eine Aktion zuordnen, hängt vom Typ der Eingabequelle ab:

### <a name="controller-input"></a>Controllereingabe

Wechseln Sie unter **dem Eingabesystemprofil** zum *Controller-Eingabezuordnungsprofil.* Dort finden Sie eine Liste aller unterstützten Controller:

<img src="../images/input/ControllerInputMappingProfile.PNG" alt="Input maping profile" style="max-width:100%;">

Wählen Sie das Dialogfeld aus, das Sie konfigurieren möchten, und es wird ein Dialogfeld mit allen Controllereingaben angezeigt, sodass Sie eine Aktion für jede von ihnen festlegen können:

<img src="../images/input/InputActionAssignment.PNG" alt="Input Action Assignment" style="max-width:100%;">

### <a name="speech-input"></a>Spracheingabe

Im **Speech-Befehlsprofil** finden Sie unter dem *Eingabesystemprofil* die Liste der derzeit definierten Sprachbefehle. Um einer Aktion eines davon zu zuordnen, wählen Sie es einfach in der *Dropdownliste Aktion* aus.

<img src="../images/input/SpeechCommandsProfile.png" alt="Speech Commands profile" style="max-width:100%;">

### <a name="gesture-input"></a>Gesteneingabe

Das **Gestenprofil** unter dem *Eingabesystemprofil* enthält alle definierten Gesten. Sie können sie jeweils einer Aktion zuordnen, indem Sie sie in der *Dropdownliste Aktion* auswählen.

<img src="../images/input/GestureProfile.png" alt="Gesture profile" style="max-width:100%;">

## <a name="handling-input-actions"></a>Behandeln von Eingabeaktionen

> [!WARNING]
> Derzeit können nur Eingabeaktionen *vom Typ Digital* mithilfe der in diesem Abschnitt beschriebenen Methoden verarbeitet werden. Bei anderen Aktionstypen müssen Sie stattdessen die Ereignisse für die entsprechenden Eingaben direkt behandeln. Um beispielsweise eine 6-DOF-Aktion zu verarbeiten, die Controllereingaben zugeordnet ist, müssen Sie mit [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) T = [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) verwenden.

Die einfachste Möglichkeit zur Handhabung von Eingabeaktionen besteht in der Verwendung des [`InputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.InputActionHandler) Skripts. Auf diese Weise können Sie die Aktion definieren, auf die Sie mit unity-Ereignissen lauschen und auf gestartete und beendete Ereignisse reagieren möchten.

<img src="../images/input/InputActionHandler.PNG" alt="Acton Handler" style="max-width:100%;">

Wenn Sie mehr Kontrolle wünschen, können Sie die -Schnittstelle [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) direkt in Ihrem Skript implementieren. Weitere Informationen [**zur Ereignisbehandlung über**](input-events.md) Handlerschnittstellen finden Sie im Abschnitt Eingabeereignisse.

## <a name="examples"></a>Beispiele

Sehen `MRTK/Examples/Demos/Input/Scenes/InputActions` Sie sich eine Beispielszene an, die zeigt, wie Sie eine Aktion erstellen, sie Controller-, Sprach- und Gesteneingaben zuordnen und damit ein Objekt auf Befehl drehen.

<img src="../images/input/InputActionsExample.PNG" alt="Input action example" style="max-width:100%;">
