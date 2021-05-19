---
title: Eingabeanimationsaufzeichnung
description: Dokumentation zum Eingabeanimation-Aufzeichnungssystem in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 81e49178a9f218e5d3be796ec6253ccabe5d44fc
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143913"
---
# <a name="input-animation-recording"></a>Aufzeichnung der Eingabeanimation

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

Standardmäßig ist die Größe des Aufzeichnungspuffers auf 30 Sekunden beschränkt. Dadurch kann der Aufzeichnungsdienst die Aufzeichnung im Hintergrund beibehalten, ohne zu viele Daten zu sammeln, und die letzten 30 Sekunden bei Bedarf speichern. Das Zeitintervall kann mithilfe der -Eigenschaft geändert werden, oder die [`RecordingBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.RecordingBufferTimeLimit) Aufzeichnung kann mithilfe der Option unbegrenzt [`UseBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.UseBufferTimeLimit) sein.

Die Daten im Aufzeichnungspuffer können mithilfe der [SaveInputAnimation-Funktion](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.SaveInputAnimation*) in einer Binärdatei gespeichert werden.

Ausführliche Informationen zum Binärdateiformat finden Sie unter [Eingabeanimationsdateiformatspezifikation.](input-animation-file-format.md)

### <a name="input-playback-service"></a>Eingabewiedergabedienst

[`InputPlaybackService`](xref:Microsoft.MixedReality.Toolkit.Input.InputPlaybackService) liest eine Binärdatei mit Eingabeanimationsdaten und wendet diese Daten dann über [InputSimulationService](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) an, um die aufgezeichneten Bewegungen neu zu erstellen.

<a target="_blank" href="../images/input-simulation/MRTK_InputAnimation_PlaybackDiagram.png">
  <img src="../images/input-simulation/MRTK_InputAnimation_PlaybackDiagram.png" title="Wiedergeben der Eingabeanimation" width="80%" alt="Play Back diagram" class="center" />
</a>

Um mit der Wiedergabe der Eingabeanimation zu beginnen, sollte sie mithilfe der [LoadInputAnimation-Funktion](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LoadInputAnimation*) aus einer Datei geladen werden.

Rufen Sie [Wiedergabe,](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play) [Anhalten](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play)oder [Beenden](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Stop) auf, um die Wiedergabe der Animation zu steuern.

Die aktuelle Animationszeit kann auch direkt mit der [LocalTime-Eigenschaft](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) gesteuert werden.

> [!WARNING]
> Das Schleifen oder Zurücksetzen der Eingabeanimation oder -einstellung [`LocalTime`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) direkt durch Bereinigung der Zeitachse kann zu unerwarteten Ergebnissen führen, wenn die Szene bearbeitet wird! Nur die Eingabebewegungen werden aufgezeichnet. Alle zusätzlichen Änderungen, z. B. das Verschieben von Objekten oder das Umschalten von Schaltern, werden nicht zurückgesetzt. Stellen Sie sicher, dass Sie die Szene erneut laden, wenn nicht rückgängig gemachte Änderungen vorgenommen wurden.

### <a name="editor-tools-for-recording-and-playing-input-animation"></a>Editor-Tools zum Aufzeichnen und Wiedergeben von Eingabeanimationen

Im Unity-Editor sind mehrere Tools zum Aufzeichnen und Untersuchen der Eingabeanimation vorhanden. Auf diese Tools kann im [Fenster eingabesimulationstools](input-simulation-service.md#input-simulation-tools-window)zugegriffen werden, das über das Menü _Mixed Reality Toolkit > Utilities > Input Simulation_ geöffnet werden kann.

> [!NOTE]
> Die Eingabeaufzeichnung und -wiedergabe funktioniert nur während des Wiedergabemodus.

Das Eingabeaufzeichnungsfenster verfügt über zwei Modi:

* _Aufzeichnung_ zur Aufzeichnung von Eingaben während des Wiedergabemodus und Speichern in Animationsdateien.

  Beim Umschalten auf der Aufzeichnungsschaltfläche [`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) ist aktiviert, um Eingaben aufzuzeichnen.
  Beim Umschalten der Aufzeichnungsschaltfläche wird eine Dateispeicherauswahl angezeigt, und die aufgezeichnete Eingabeanimation wird am ausgewählten Ziel gespeichert.

  Das Pufferzeitlimit kann auch in diesem Modus geändert werden.

* _Wiedergabe_ zum Laden von Animationsdateien und anschließendes Erneutes Erstellen von Eingaben über das Eingabesimulationssystem.

  Eine Animation muss zuerst in diesem Modus geladen werden. Nach der Aufzeichnung der Eingabe im Aufzeichnungsmodus wird die resultierende Animation automatisch geladen. Klicken Sie alternativ auf die Schaltfläche "Laden", um eine vorhandene Animationsdatei auszuwählen.

  Die Zeitsteuerungsschaltflächen von links nach rechts lauten:

  * Setzen Sie die Wiedergabezeit auf den Anfang der Animation _zurück._
  * _Fortlaufende_ Wiedergabe von Animationen im Zeitverlauf.
  * _Einzelschritt_ vorwärts.

  Der Schieberegler kann auch verwendet werden, um die Animationszeitachse zu bebereinigungen.

> [!WARNING]
> Das Schleifen oder Zurücksetzen der Eingabeanimation oder das Bebereinigung der Zeitachse kann beim Bearbeiten der Szene zu unerwarteten Ergebnissen führen! Nur die Eingabebewegungen werden aufgezeichnet. Alle zusätzlichen Änderungen, z. B. das Verschieben von Objekten oder das Umschalten von Schaltern, werden nicht zurückgesetzt. Stellen Sie sicher, dass Sie die Szene erneut laden, wenn nicht rückgängig gemachte Änderungen vorgenommen wurden.
