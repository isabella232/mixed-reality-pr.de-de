---
title: Eingabeanimationsaufzeichnung
description: Dokumentation zum Eingabeanimation-Aufzeichnungssystem in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 1a900b7b419a0aca45c3601ed583ef6c2e326574cb9e732edd0474afe117b895
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223066"
---
# <a name="input-animation-recording"></a>Eingabeanimationsaufzeichnung

MRTK verfügt über ein Aufzeichnungssystem, mit dem Kopfbewegungs- und Handverfolgungsdaten in Animationsdateien gespeichert werden können. Die aufgezeichneten Daten können dann mithilfe des [Eingabesimulationssystems abgespielt werden.](input-simulation-service.md)

Das Aufzeichnen von Eingaben ist ein nützliches Tool in einer Vielzahl von Situationen:

* Erstellen automatisierter Tests für Interaktion, Manipulationen, Solver usw. Das Erstellen der Bewegung von Controllern und Händen für diese Tests kann zeitaufwändig sein. Das direkte Aufzeichnen von Eingaben kann den Prozess beschleunigen und reale Daten bereitstellen.
* Hier lernen Sie die Verwendung von UX-Elementen durch Animationen bei.
  Wenn Sie Benutzern zeigen, wie sie mit Schaltflächen und anderen Objekten interagieren, kann die Lernkurve geglättet werden.
* Debuggen von unerwartetem Verhalten, das bei regelmäßiger Verwendung auftreten kann.
  Das Aufzeichnungssystem unterstützt ein Konzept des "rollierenden Puffers", das die Aufzeichnung aktueller Eingaben im Hintergrund ermöglicht.
  Weitere Informationen finden [Sie unter Input Recording Service](#input-recording-service).

## <a name="recording-and-playback-services"></a>Aufzeichnungs- und Wiedergabedienste

Es werden zwei Eingabesystemdienste bereitgestellt, um Eingaben aufzeichnen bzw. wieder geben zu können.

### <a name="input-recording-service"></a>Eingabeaufzeichnungsdienst

[`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) nimmt Daten aus der Hauptkameratransformation und aktiven Handcontrollern und speichert sie in einem internen Puffer. Bei Der Angeforderten werden diese Daten dann zur Speicherung und späteren Wiedergabe in Binärdateien serialisiert.

<a target="_blank" href="../images/input-simulation/MRTK_InputAnimation_RecordingDiagram.png">
  <img src="../images/input-simulation/MRTK_InputAnimation_RecordingDiagram.png" title="Aufzeichnen der Eingabeanimation" width="80%" alt="Recording diagram" class="center" />
</a>

Um mit der Aufzeichnung der Eingabe zu beginnen, rufen Sie die [`StartRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StartRecording) -Funktion auf. [`StopRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StopRecording) hält die Aufzeichnung an (verwirft jedoch die bisher aufgezeichneten Daten nicht, verwenden Sie , [`DiscardRecordedInput`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.DiscardRecordedInput) um dies bei Bedarf zu tun).

Standardmäßig ist die Größe des Aufzeichnungspuffers auf 30 Sekunden beschränkt. Dadurch kann der Aufzeichnungsdienst die Aufzeichnung im Hintergrund speichern, ohne zu viele Daten anzusammeln, und dann bei Bedarf die letzten 30 Sekunden speichern. Das Zeitintervall kann mithilfe der -Eigenschaft geändert [`RecordingBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.RecordingBufferTimeLimit) werden, oder die Aufzeichnung kann mithilfe der -Option unbegrenzt [`UseBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.UseBufferTimeLimit) sein.

Die Daten im Aufzeichnungspuffer können mithilfe der [SaveInputAnimation-Funktion](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.SaveInputAnimation*) in einer Binärdatei gespeichert werden.

Weitere Informationen zum Binärdateiformat finden Sie unter [Input Animation File Format Specification](input-animation-file-format.md).

### <a name="input-playback-service"></a>Eingabewiedergabedienst

[`InputPlaybackService`](xref:Microsoft.MixedReality.Toolkit.Input.InputPlaybackService) liest eine Binärdatei mit Eingabeanimationsdaten und wendet diese Daten dann über [inputSimulationService](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) an, um die aufgezeichneten Bewegungen neu zu erstellen.

<a target="_blank" href="../images/input-simulation/MRTK_InputAnimation_PlaybackDiagram.png">
  <img src="../images/input-simulation/MRTK_InputAnimation_PlaybackDiagram.png" title="Wiederspielen der Eingabeanimation" width="80%" alt="Play Back diagram" class="center" />
</a>

Um mit der Wiedergabe der Eingabeanimation zu beginnen, sollte sie mithilfe der [LoadInputAnimation-Funktion](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LoadInputAnimation*) aus einer Datei geladen werden.

Rufen [Sie Wiedergabe,](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play) [Anhalten oder](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play)Beenden [auf,](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Stop) um die Wiedergabe der Animation zu steuern.

Die aktuelle Animationszeit kann auch direkt mit der [LocalTime-Eigenschaft gesteuert](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) werden.

> [!WARNING]
> Das Schleifen oder Zurücksetzen der Eingabeanimation oder -einstellung direkt durch Bereinigung der Zeitachse kann beim Bearbeiten der Szene [`LocalTime`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) zu unerwarteten Ergebnissen führen! Nur die Eingabebewegungen werden aufgezeichnet. Alle zusätzlichen Änderungen wie das Verschieben von Objekten oder Kippschaltern werden nicht zurückgesetzt. Stellen Sie sicher, dass Sie die Szene erneut laden, wenn nicht rückgängig gemachte Änderungen vorgenommen wurden.

### <a name="editor-tools-for-recording-and-playing-input-animation"></a>Editortools für die Aufzeichnung und Wiedergabe von Eingabeanimationen

Im Unity-Editor gibt es eine Reihe von Tools zum Aufzeichnen und Untersuchen von Eingabeanimationen. Auf diese Tools kann [](input-simulation-service.md#input-simulation-tools-window)im Fenster eingabesimulationstools zugegriffen werden, das über das Menü Mixed Reality Toolkit > Utilities > _Input Simulation geöffnet werden_ kann.

> [!NOTE]
> Die Eingabeaufzeichnung und -wiedergabe funktioniert nur im Wiedergabemodus.

Das Eingabeaufzeichnungsfenster verfügt über zwei Modi:

* _Aufzeichnung_ für die Aufzeichnung von Eingaben im Wiedergabemodus und speichern sie in Animationsdateien.

  Beim Umschalten auf der Aufzeichnungsschaltfläche wird [`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) für das Aufzeichnen von Eingaben aktiviert.
  Wenn Sie die Aufzeichnungsschaltfläche deaktivieren, wird eine Dateisparauswahl angezeigt, und die aufgezeichnete Eingabeanimation wird am ausgewählten Ziel gespeichert.

  Das Pufferzeitlimit kann auch in diesem Modus geändert werden.

* _Wiedergabe_ zum Laden von Animationsdateien und anschließendes Erneutes Erstellen der Eingabe über das Eingabesimulationssystem.

  Eine Animation muss zuerst in diesem Modus geladen werden. Nach dem Aufzeichnen der Eingabe im Aufzeichnungsmodus wird die resultierende Animation automatisch geladen. Klicken Sie alternativ auf die Schaltfläche "Laden", um eine vorhandene Animationsdatei auszuwählen.

  Die Schaltflächen für die Zeitsteuerung von links nach rechts sind:

  * _Setzen_ Sie die Wiedergabezeit auf den Anfang der Animation zurück.
  * _Wiedergabeanimation_ kontinuierlich im Laufe der Zeit.
  * _Gehen Sie_ einen Schritt vorwärts.

  Der Schieberegler kann auch verwendet werden, um die Animationszeitachse zu bereinigungen.

> [!WARNING]
> Das Schleifen oder Zurücksetzen der Eingabeanimation oder das Bereinigung der Zeitachse kann beim Bearbeiten der Szene zu unerwarteten Ergebnissen führen. Nur die Eingabebewegungen werden aufgezeichnet. Alle zusätzlichen Änderungen wie das Verschieben von Objekten oder Kippschaltern werden nicht zurückgesetzt. Stellen Sie sicher, dass Sie die Szene erneut laden, wenn nicht rückgängig gemachte Änderungen vorgenommen wurden.
