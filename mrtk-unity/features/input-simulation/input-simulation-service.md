---
title: Eingabesimulationsdienst
description: Dokumentation zum Eingabesimulationsdienst in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 66b79c14bbd0ea8c188aba684b9bd1034de31bf9
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176959"
---
# <a name="input-simulation-service"></a>Eingabesimulationsdienst

![MRTK-Eingabesimulation](../images/input-simulation/MRTK_InputSimulation_Hero.jpg)

Mit der MrTK-Eingabesimulation können Sie verschiedene Arten von Interaktionen im Unity-Editor testen, ohne ein Gerät erstellen und bereitstellen zu müssen. Auf diese Weise können Sie Ihre Ideen im Entwurfs- und Entwicklungsprozess schnell iterieren. Verwenden Sie Tastenkombinationen und Mauskombinationen, um simulierte Eingaben zu steuern.

Der Eingabesimulationsdienst emuliert das Verhalten von Geräten und Plattformen, die möglicherweise nicht im Unity-Editor verfügbar sind. Beispiele:

* HoloLens oder VR-Gerätekopfverfolgung
* HoloLens Handgesten
* HoloLens 2 artikulierte Handverfolgung
* HoloLens 2 Eyetracking
* VR-Gerätecontroller

> [!WARNING]
> Dies funktioniert nicht, wenn die XR Holographic Emulation von Unity > Emulationsmodus = "Simulate in Editor" (Im Editor simulieren) verwendet wird. Die In-Editor-Simulation von Unity wird die Kontrolle über die Eingabesimulation des MRTK übernehmen. Um den MRTK-Eingabesimulationsdienst verwenden zu können, müssen Sie XR Holographic Emulation auf Emulation Mode = *"None" (Keine) festlegen.*

## <a name="how-to-use-mrtk-input-simulation"></a>Verwenden der MRTK-Eingabesimulation 

Die Eingabesimulation ist in den Profilen, die im MRTK-Versand sind, standardmäßig aktiviert. Sie können einfach auf die **Schaltfläche Wiedergabe** klicken, um die Szene mit Eingabesimulationsunterstützung ausführen zu lassen.

* Drücken **Sie die Tasten W, A, S, D, Q, E,** um die Kamera zu bewegen.
* Halten Sie die **rechte Maustaste gedrückt,** und bewegen Sie die Maus, um nach ihnen zu suchen.
* Drücken Sie zum Aufbringen der simulierten Hände die **TASTENTASTE (rechts)** oder NACH-LINKS-TASTE **(Linke Hand).**
* Drücken Sie T oder **Y,** um simulierte Hände in der Ansicht zu halten. 
* Halten Sie zum Drehen simulierter Hände die **STRG-TASTE** gedrückt, und bewegen Sie die Maus.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4OYrm]

## <a name="in-editor-input-simulation-cheat-sheet"></a>Cheat Sheet zur Eingabesimulation im Editor

Drücken Sie in der HandInteractionExamples-Szene nach links **STRG+H,** um ein Cheat Sheet mit Eingabesimulationssteuerelementen zu erhalten.

> ![MRTK Input Simulation Cheat Sheet](../images/input-simulation/MRTK_InputSimulation_CheatSheet.png)


## <a name="enabling-the-input-simulation-service"></a>Aktivieren des Eingabesimulationsdiensts

Unter der Konfiguration des Eingabesystemdatenanbieters kann der Eingabesimulationsdienst wie folgt konfiguriert werden.

* **Typ** muss *Microsoft.MixedReality.Toolkit.Input > InputSimulationService sein.*
* **Unterstützte Plattformen umfassen standardmäßig** alle *Editor-Plattformen,* da der Dienst Tastatur- und Mauseingaben verwendet.

> [!NOTE]
> Der Eingabesimulationsdienst kann auf anderen Plattformendpunkten verwendet werden, z. B. eigenständig, indem die Eigenschaft Unterstützte **Plattform(en)** geändert wird, um die gewünschten Ziele ein- und einaufnahme.
> <br/><img src="../images/input-simulation/InputSimulationSupportedPlatforms.gif" alt="Input Simulation Supported Platforms" width="550px">

## <a name="camera-control"></a>Kamerasteuerung

Die Kopfbewegung kann vom Eingabesimulationsdienst emuliert werden.

### <a name="rotating-the-camera"></a>Drehen der Kamera

1. Zeigen Sie auf das Viewport-Editor-Fenster.
    *Möglicherweise müssen Sie auf das Fenster klicken, um ihm den Eingabefokus zu geben, wenn Tastendruck nicht funktioniert.*
1. Halten Sie die **Maustaste gedrückt** (Standard: Rechte Maustaste).
1. Bewegen Sie die Maus im Viewportfenster, um die Kamera zu drehen.
1. Verwenden Sie das Scrollrad, um die Kamera um die Ansichtsrichtung zu drehen.

Die Kameradrehgeschwindigkeit kann durch Ändern der **Einstellung Mouse Look Speed** im Eingabesimulationsprofil konfiguriert werden.

Alternativ können Sie die Vertikale **Look Horizontal** Look-Achsen verwenden, um die Kamera zu drehen /  (Standard: game controller right thumbstick).

### <a name="moving-the-camera"></a>Bewegen der Kamera

Verwenden Sie **die Achsen "Horizontale** Bewegung vertikal verschieben", um die Kamera zu verschieben /  (Standardeinstellung: WASD-Tasten oder game controller left thumbstick).

Kameraposition und Drehwinkel können auch explizit im Toolsfenster festgelegt werden. Die Kamera kann mithilfe der Schaltfläche Zurücksetzen auf den **Standardwert zurückgesetzt** werden.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Z7L4I1ET7GU" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="controller-simulation"></a>Controllersimulation

Die Eingabesimulation unterstützt emulierte Controllergeräte (d. h. Motion Controller und Hände). Diese virtuellen Controller können mit jedem Objekt interagieren, das reguläre Controller unterstützt, z. B. Schaltflächen oder greifbare Objekte.

### <a name="controller-simulation-mode"></a>Controllersimulationsmodus

Im Fenster [der Eingabesimulationstools](#input-simulation-tools-window) wechselt **die Einstellung Standardcontrollersimulationsmodus** zwischen drei unterschiedlichen Eingabemodellen. Dieser Standardmodus kann auch im Eingabesimulationsprofil festgelegt werden.

* *Artikulierte Hände:* Simuliert ein vollständig artikuliertes Handgerät mit Gemeinsamen Positionsdaten.

   Emuliert HoloLens 2 Interaktionsmodell.

   Interaktionen, die auf der präzisen Positionierung der Hand oder der Verwendung von Touching basieren, können in diesem Modus simuliert werden.

* *Handgesten:* Simuliert ein vereinfachtes Handmodell mit Tippbewegungen in die Luft und grundlegenden Gesten.

   Emuliert [HoloLens Interaktionsmodell.](/windows/mixed-reality/gestures)

   Der Fokus wird mithilfe des Anvingzeigers gesteuert. Die *Geste Tippen* in die Luft wird für die Interaktion mit Schaltflächen verwendet.

* *Motion Controller*: Simuliert einen Motion Controller, der mit VR-Headsets verwendet wird und ähnlich wie bei fernen Interaktionen mit Artikulierten Händen funktioniert.

   Emuliert das VR-Headset mit dem Controllerinteraktionsmodell.

   Trigger, Greif- und Menütasten werden per Tastatur- und Mauseingabe simuliert.

### <a name="simulating-controller-movement"></a>Simulieren der Controllerbewegung

Drücken und halten Sie die Taste für  die Controllerbearbeitung nach **links/rechts** (Standard: Linke UMSCHALTTASTE für den linken Controller und *Leerzeichen* für den rechten Controller), um die Kontrolle über beide Controller zu erlangen. Während die Manipulationstaste gedrückt wird, wird der Controller im Viewport angezeigt. Nachdem der Manipulationsschlüssel freigegeben wurde, werden die Controller nach einem kurzen **Timeout für das Ausblenden des Controllers nicht mehr verwendet.**

Controller können ein- und fixiert werden, relativ [](#input-simulation-tools-window) zur Kamera im Fenster der Eingabesimulationstools oder durch Drücken der Umschalttaste **links/rechts** (Standard: *T* für links und *Y* für rechts). Drücken Sie erneut die Umschalttaste, um die Controller erneut auszublenden. Um die Controller zu bearbeiten, muss **der Linke/rechte Controllermanipulationsschlüssel** gehalten werden. Wenn Sie auf den **Bearbeitungsschlüssel für den linken/rechten Controller** tippen, können Sie die Controller auch ein-/ausschalten.

Die Mausbewegung bewegt den Controller in der Ansichtsebene. Controller können mit dem Mausrad weiter oder näher zur **Kamera bewegt werden.**

Halten Sie zum Drehen von Controllern mit der Maus sowohl die  **Linke/Rechte** Taste zum Ändern des Controllers *(* Linke UMSCHALTTASTE oder Leerzeichen *)* als auch die **Schaltfläche** Controller rotieren (Standard:  Linke STRG-Taste) gedrückt, und bewegen Sie dann die Maus, um den Controller zu drehen. Die Geschwindigkeit der Controllerrotation kann durch Ändern der **Einstellung Drehgeschwindigkeit** des Mauscontrollers im Eingabesimulationsprofil konfiguriert werden.

Alle Handplatzierungen können auch im Fenster der [Eingabesimulationstools](#input-simulation-tools-window)geändert werden, einschließlich des Zurücksetzens der Hände auf den Standardwert.

### <a name="additional-profile-settings"></a>Zusätzliche Profileinstellungen

* **Der Controller-Tiefenmultiplikator** steuert die Empfindlichkeit der Tiefenbewegung des Mausscrollrads. Eine größere Zahl beschleunigt den Controllerzoom.
* **Standardcontrollerabstand** ist der anfängliche Abstand der Controller von der Kamera. Wenn Sie auf die **Schaltfläche Zurücksetzen** klicken, platzieren Sie controller ebenfalls in dieser Entfernung.
* **Controller Jitter Amount fügt** Controllern zufällige Bewegungen hinzu. Dieses Feature kann verwendet werden, um ungenaue Controllernachverfolgung auf dem Gerät zu simulieren und sicherzustellen, dass Interaktionen mit lauten Eingaben gut funktionieren.

<iframe width="560" height="315" src="https://www.youtube.com/embed/uRYfwuqsjBQ" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="hand-gestures"></a>Handgesten

Handgesten wie Zusammendring, Greifen, Poking usw. können ebenfalls simuliert werden.

1. Aktivieren der Handsteuerung mithilfe **des Links-/Rechtscontroller-Manipulationsschlüssels** (*Linke Umschalttaste* oder *Leerzeichen*)

2. Halten Sie beim Bearbeiten eine Maustaste gedrückt, um eine Handbewegung durchzuführen.

Jede der Maustasten kann zugeordnet werden, um die Handform in eine andere Geste zu transformieren, indem die Einstellungen *linke/mittlere/rechte Mausbewegung verwendet* werden. Die *Standardhandgeste* ist die Form der Hand, wenn keine Schaltfläche gedrückt wird.

> [!NOTE]
> Die *Pinch-Geste* ist die einzige Geste, die an dieser Stelle die Aktion "Auswählen" ausführt.

### <a name="one-hand-manipulation"></a>One-Hand-Manipulation

1. Drücken und halten Sie die Taste für die Controllerbearbeitung nach **links/rechts** (*Linke Umschalttaste* oder *Leerzeichen*)
2. Punkt auf Objekt
3. Halten Sie die Maustaste gedrückt, um sie zu halten.
4. Verwenden der Maus zum Verschieben des Objekts
5. Lassen Sie die Maustaste los, um die Interaktion zu beenden.

<iframe width="560" height="315" src="https://www.youtube.com/embed/rM0xaHam6wM" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="two-hand-manipulation"></a>Zweihandmanipulation

Für die gleichzeitige Bearbeitung von Objekten mit zwei Händen wird der persistente Handmodus empfohlen.

1. Umschalten an beiden Händen durch Drücken der Umschalttasten (*T/Y*).
1. Bearbeiten Sie eine Hand nach der anderen:
    1. Halten **Sie den Platz,** um die rechte Hand zu steuern.
    1. Bewegen Sie die Hand an den Ort, an dem Sie das Objekt greifen möchten.
    1. Drücken Sie die **linke Maustaste,** um die Stiftbewegung *zu* aktivieren.
    1. **Freigabebereich,** um die Steuerung der rechten Hand zu beenden. Die Hand wird an Ort und Stelle fixiert und an der *Pinch-Geste* gesperrt, da sie nicht mehr bearbeitet wird.
1. Wiederholen Sie den Vorgang mit der anderen Hand, und greifen Sie dasselbe Objekt an einer zweiten Stelle.
1. Da nun beide Hände dasselbe Objekt greifen, können Sie beide bewegen, um eine zweihändige Bearbeitung durchzuführen.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qol5OFNfN14" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="ggv-gaze-gesture-and-voice-interaction"></a>GGV-Interaktion (Anving, Geste und Stimme)

Standardmäßig ist die GGV-Interaktion im Editor aktiviert, während in der Szene keine artikulierten Hände vorhanden sind.

1. Drehen der Kamera, um den Anvitätscursor auf das interaktionsfähige Objekt zu zeigen (rechte Maustaste)
1. Klicken und halten Sie **die linke Maustaste gedrückt, um** zu interagieren.
1. Drehen Sie die Kamera erneut, um das Objekt zu bearbeiten.

Sie können dies deaktivieren, indem Sie die Option *Is Hand Free Input Enabled* im Eingabesimulationsprofil umschalten.

Darüber hinaus können Sie simulierte Hände für die GGV-Interaktion verwenden.

1. Aktivieren der GGV-Simulation durch Wechseln **des Handsimulationsmodus** zu Gesten im [Eingabesimulationsprofil](#enabling-the-input-simulation-service) 
1. Drehen der Kamera, um den Anvitätscursor auf das interaktionsfähige Objekt zu zeigen (rechte Maustaste)
1. Halten **Sie den Platz,** um die rechte Hand zu steuern.
1. Klicken und halten Sie **die linke Maustaste gedrückt, um** zu interagieren.
1. Verwenden der Maus zum Verschieben des Objekts
1. Lassen Sie die Maustaste los, um die Interaktion zu beenden.

<iframe width="560" height="315" src="https://www.youtube.com/embed/6841rRMdqWw" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="raising-teleport-events"></a>Ausreihen von Teleportereignissen

Um das Teleportereignis in der Eingabesimulation zu starten, konfigurieren Sie die Handgeste Einstellungen im Eingabesimulationsprofil so, dass eine die **Teleport-Startgeste** ausführt, während die andere die **Teleport-Endgeste** ausführt. Mit **der Teleport-Startgeste** wird der Teleport-Zeiger angezeigt, während die Teleport-End-Benutzeroberfläche die **Teleportaktion** abarbeite und den Benutzer bewegt.

Die y-Position des resultierenden Teleports hängt von der Verschiebung der Kamera entlang der y-Achse ab. Im Editor ist dies standardmäßig 0. Verwenden Sie daher die **Q-** und **E-Tasten,** um sie an die entsprechende Höhe anzupassen.

![Teleport-Einstellungen](../images/input-simulation/InputSimulationTeleport.gif)

### <a name="motion-controller-interaction"></a>Interaktion des Bewegungscontrollers

Die simulierten Bewegungscontroller können auf die gleiche Weise bearbeitet werden wie artikulierte Hände. Das Interaktionsmodell ähnelt der fernen Interaktion der artikulierten Hand, während der Trigger, die Greiftaste und die Menütaste der linken *Maustaste,* *der G-* bzw. *M-Taste* zugeordnet sind.

### <a name="eye-tracking"></a>Eyetracking – Blickverfolgung

[Die Eyetrackingsimulation](../input/eye-tracking/eye-tracking-basic-setup.md#simulating-eye-tracking-in-the-unity-editor) kann aktiviert werden, indem die **Option Augenposition** simulieren im [Eingabesimulationsprofil aktiviert wird.](#enabling-the-input-simulation-service) Dies sollte nicht mit GGV- oder Motion Controller-Stilinteraktionen verwendet werden (stellen Sie daher sicher, dass **Standardcontrollersimulationsmodus** auf *Artikulierte Hand festgelegt ist).*

## <a name="input-simulation-tools-window"></a>Fenster "Eingabesimulationstools"

Aktivieren Sie das Fenster eingabesimulationstools über das **Menü Mixed Reality**  >  **Toolkit**  >  **Utilities**  >  **Input Simulation (Eingabesimulation für Toolkit-Hilfsprogramme).** Dieses Fenster ermöglicht den Zugriff auf den Zustand der Eingabesimulation im Wiedergabemodus.

## <a name="viewport-buttons-optional"></a>Viewportschaltflächen (optional)

Ein Prefab für Schaltflächen im Editor zum Steuern der grundlegenden Handplatzierung kann im Eingabesimulationsprofil unter **Indicators Prefab angegeben werden.** Dies ist ein optionales Hilfsprogramm. Auf die gleichen Features kann im Eingabesimulationstools-Fenster [zugegriffen werden.](#input-simulation-tools-window)

> [!NOTE]
> Die Viewportindikatoren sind standardmäßig deaktiviert, da sie derzeit manchmal Interaktionen der Unity-Benutzeroberfläche beeinträchtigen können. Siehe Problem [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106). Fügen Sie zum Aktivieren das Prefab InputSimulationIndicators zu **Indicators Prefab hinzu.**

Handsymbole zeigen den Zustand der simulierten Hände an:

* ![Symbol "Nicht vertrackte Hand"](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Untracked.png) Die Hand wird nicht nachverfolgt. Klicken Sie auf diese Schaltfläche, um die Hand zu aktivieren.
* ![Symbol "Nachverfolgte Hand&quot;](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png &quot;Symbol &quot;Nachverfolgte Hand&quot;") Die Hand wird nachverfolgt, aber nicht vom Benutzer gesteuert. Klicken Sie auf diese Schaltfläche, um die Hand auszublenden.
* ![Symbol "Kontrollierte Hand"](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "Symbol &quot;Kontrollierte Hand&quot;") Die Hand wird vom Benutzer nachverfolgt und gesteuert. Klicken Sie auf diese Schaltfläche, um die Hand auszublenden.
* ![Symbol "Hand zurücksetzen"](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "Symbol &quot;Hand zurücksetzen&quot;") Klicken Sie auf diese Option, um die Hand auf die Standardposition zurückzusetzen.


## <a name="see-also"></a>Siehe auch

* [Eingabesystemprofil](../input/input-providers.md).
