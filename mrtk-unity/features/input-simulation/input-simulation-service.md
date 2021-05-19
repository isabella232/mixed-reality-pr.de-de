---
title: Eingabesimulationsdienste
description: Dokumentation zum Eingabesimulationsdienst in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, MRTK,
ms.openlocfilehash: 81e7dcab7e0f349d05521f93d75bba6927761fd1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145093"
---
# <a name="input-simulation-service"></a>Eingabesimulationsdienst

Der Eingabesimulationsdienst emuliert das Verhalten von Geräten und Plattformen, die möglicherweise nicht im Unity-Editor verfügbar sind. Beispiele:

* HoloLens- oder VR-Gerätekopfverfolgung
* HoloLens-Handgesten
* HoloLens 2 artikulierte Handverfolgung
* HoloLens 2 Eyetracking
* VR-Gerätecontroller

Benutzer können eine herkömmliche Kombination aus Tastatur und Maus verwenden, um simulierte Geräte zur Laufzeit zu steuern. Dieser Ansatz ermöglicht das Testen von Interaktionen im Unity-Editor, ohne zuerst auf einem Gerät bereitgestellt zu werden.

> [!WARNING]
> Dies funktioniert nicht, wenn die XR Holographic Emulation von Unity > Emulationsmodus = "Simulate in Editor" (Im Editor simulieren) verwendet wird. Die In-Editor-Simulation von Unity wird die Kontrolle über die Eingabesimulation des MRTK übernehmen. Um den MRTK-Eingabesimulationsdienst verwenden zu können, müssen Sie XR Holographic Emulation auf Emulation Mode = *"None" (Keine) festlegen.*

## <a name="enabling-the-input-simulation-service"></a>Aktivieren des Eingabesimulationsdiensts

Die Eingabesimulation ist in den Profilen, die im MRTK-Versand sind, standardmäßig aktiviert.

Unter der Konfiguration des Eingabesystemdatenanbieters kann der Eingabesimulationsdienst wie folgt konfiguriert werden.

* **Typ** muss *Microsoft.MixedReality.Toolkit.Input > InputSimulationService sein.*
* **Unterstützte Plattformen umfassen standardmäßig** alle *Editor-Plattformen,* da der Dienst Tastatur- und Mauseingaben verwendet.

> [!NOTE]
> Der Eingabesimulationsdienst kann auf anderen Plattformendpunkten verwendet werden, z. B. eigenständig, indem die Eigenschaft Unterstützte **Plattform(en)** geändert wird, um die gewünschten Ziele ein- und einaufnahme.
> ![Unterstützte Plattformen für die Eingabesimulation](../images/input-simulation/InputSimulationSupportedPlatforms.gif)

## <a name="input-simulation-tools-window"></a>Fenster "Eingabesimulationstools"

Aktivieren Sie das Fenster eingabesimulationstools über das Menü **eingabesimulation** für Mixed Reality  >  **Toolkit-Hilfsprogramme.**  >   Dieses Fenster ermöglicht den Zugriff auf den Zustand der Eingabesimulation während des Wiedergabemodus.

## <a name="viewport-buttons"></a>Viewportschaltflächen

Ein Prefab für Schaltflächen im Editor, um die einfache Handplatzierung zu steuern, kann im Eingabesimulationsprofil unter **Indikatoren prefab** angegeben werden. Dies ist ein optionales Hilfsprogramm. Auf die gleichen Features kann im [Eingabesimulationstools-Fenster](#input-simulation-tools-window)zugegriffen werden.

> [!NOTE]
> Die Viewportindikatoren sind standardmäßig deaktiviert, da sie derzeit manchmal interaktionen mit der Unity-Benutzeroberfläche beeinträchtigen können. Weitere Informationen finden Sie unter Problem [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106). Fügen Sie zum Aktivieren das Prefab InputSimulationIndicators zu **Indicators Prefab hinzu.**

Handsymbole zeigen den Zustand der simulierten Hände an:

* ![Symbol für nicht nachgeverfolgungslose Hand](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Untracked.png) Die Hand wird nicht nachverfolgung. Klicken Sie auf diese Option, um die Hand zu aktivieren.
* ![Symbol für nachverfolgte Hand](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png "Symbol für nachverfolgte Hand") Die Hand wird nachverfolgt, aber nicht vom Benutzer gesteuert. Klicken Sie auf diese Schaltfläche, um die Hand auszublenden.
* ![Symbol für kontrollierte Hand](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "Symbol &quot;Kontrollierte Hand&quot;") Die Hand wird vom Benutzer nachverfolgt und gesteuert. Klicken Sie auf diese Schaltfläche, um die Hand auszublenden.
* ![Symbol "Hand zurücksetzen"](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "Symbol &quot;Hand zurücksetzen&quot;") Klicken Sie auf diese Schaltfläche, um die Hand auf die Standardposition zurückzusetzen.

## <a name="in-editor-input-simulation-cheat-sheet"></a>Spickzettel für Die Eingabesimulation im Editor

Drücken Sie in der HandInteractionExamples-Szene nach links STRG+H, um ein Spickzettel mit Eingabesimulationssteuerelementen auf den Weg zu bringen.

![Spickzettel für die Eingabesimulation](https://user-images.githubusercontent.com/39840334/86066480-13637f00-ba27-11ea-8814-d222d548f684.gif)

## <a name="camera-control"></a>Kamerasteuerelement

Die Kopfbewegung kann vom Eingabesimulationsdienst emuliert werden.

### <a name="rotating-the-camera"></a>Drehen der Kamera

1. Zeigen Sie auf das Viewport-Editorfenster.
    *Möglicherweise müssen Sie auf das Fenster klicken, um den Eingabefokus zu erhalten, wenn schaltflächendrücken nicht funktionieren.*
1. Halten Sie die **Maustaste** gedrückt (Standardeinstellung: Rechte Maustaste).
1. Bewegen Sie die Maus im Viewportfenster, um die Kamera zu drehen.
1. Verwenden Sie das Scrollrad, um die Kamera um die Ansichtsrichtung zu drehen.

Die Kameradrehungsgeschwindigkeit kann konfiguriert werden, indem die Einstellung **Mouse Look Speed** im Eingabesimulationsprofil geändert wird.

Alternativ können Sie die Vertikalen Achsen für **horizontales Aussehen** verwenden, /  um die Kamera zu drehen (Standard: game controller right thumbstick).

### <a name="moving-the-camera"></a>Bewegen der Kamera

Verwenden Sie die Achsen **Move Horizontal** Move Vertical (Horizontales / **Verschieben** vertikal verschieben), um die Kamera zu verschieben (Standardeinstellung: WASD-Tasten oder Gamecontroller– linker Thumbstick).

Kameraposition und Drehwinkel können auch explizit im Toolfenster festgelegt werden. Die Kamera kann mithilfe der Schaltfläche **Zurücksetzen** auf ihre Standardeinstellung zurückgesetzt werden.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Z7L4I1ET7GU" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="controller-simulation"></a>Controllersimulation

Die Eingabesimulation unterstützt emulierte Controllergeräte (d. h. Motion Controller und Hände). Diese virtuellen Controller können mit jedem Objekt interagieren, das reguläre Controller unterstützt, z. B. Schaltflächen oder fähige Objekte.

### <a name="controller-simulation-mode"></a>Controllersimulationsmodus

Im [Fenster "Eingabesimulationstools"](#input-simulation-tools-window) wechselt die Einstellung **Standardcontroller-Simulationsmodus** zwischen drei unterschiedlichen Eingabemodellen. Dieser Standardmodus kann auch im Eingabesimulationsprofil festgelegt werden.

* *Artikulierte Hände:* Simuliert ein vollständig artikuliertes Handgerät mit Gemeinsamen Positionsdaten.

   Emuliert HoloLens 2 Interaktionsmodell.

   Interaktionen, die auf der präzisen Positionierung der Hand oder der Verwendung von Touching basieren, können in diesem Modus simuliert werden.

* *Handgesten:* Simuliert ein vereinfachtes Handmodell mit Tippbewegungen in die Luft und grundlegenden Gesten.

   Emuliert [das HoloLens-Interaktionsmodell.](/windows/mixed-reality/gestures)

   Der Fokus wird mithilfe des Anvingzeigers gesteuert. Die *Geste Tippen* in die Luft wird verwendet, um mit Schaltflächen zu interagieren.

* *Motion Controller*: Simuliert einen Motion Controller, der mit VR-Headsets verwendet wird und ähnlich wie bei fernen Interaktionen mit Artikulierten Händen funktioniert.

   Emuliert das VR-Headset mit dem Controllerinteraktionsmodell.

   Trigger, Greif- und Menütasten werden per Tastatur- und Mauseingabe simuliert.

### <a name="simulating-controller-movement"></a>Simulieren der Controllerbewegung

Drücken Und halten Sie die Taste für  die Controllerbearbeitung nach **links/rechts** (Standard: Linke UMSCHALTTASTE für den linken Controller und *Leerzeichen* für den rechten Controller), um die Kontrolle über beide Controller zu erlangen. Während die Manipulationstaste gedrückt wird, wird der Controller im Viewport angezeigt. Nachdem der Manipulationsschlüssel freigegeben wurde, werden die Controller nach einem kurzen Timeout für das Ausblenden des **Controllers nicht mehr verwendet.**

Controller können ein- und fixiert werden, relativ [](#input-simulation-tools-window) zur Kamera im Fenster der Eingabesimulationstools oder durch Drücken der Umschalttaste **links/rechts** (Standard: *T* für links und *Y* für rechts). Drücken Sie erneut die Umschalttaste, um die Controller erneut auszublenden. Um die Controller zu bearbeiten, muss **der Linke/rechte Controllermanipulationsschlüssel** gehalten werden. Durch doppelklickendes **Tippen auf den Links-/Rechtscontroller-Manipulationsschlüssel** können die Controller auch ein-/ausgeschaltet werden.

Die Mausbewegung bewegt den Controller in der Ansichtsebene. Controller können mit dem **Mausrad** weiter oder näher an die Kamera verschoben werden.

Um Controller mit der Maus zu drehen, halten Sie sowohl die **Bearbeitungstaste des linken/rechten Controllers** *(Linke UMSCHALTTASTE* oder *Leertaste)* *als* auch die **Controllerschaltfläche Rotieren** (Standard: *Linke STRG-Taste)* gedrückt, und bewegen Sie dann die Maus, um den Controller zu drehen. Die Geschwindigkeit der Controllerrotation kann konfiguriert werden, indem die Einstellung Für die Drehgeschwindigkeit des **Mauscontrollers** im Eingabesimulationsprofil geändert wird.

Die gesamte Handplatzierung kann auch im [Eingabesimulationstoolsfenster](#input-simulation-tools-window)geändert werden, einschließlich des Zurücksetzens der Hände auf den Standardwert.

### <a name="additional-profile-settings"></a>Zusätzliche Profileinstellungen

* **Der Multiplikator** für die Controllertiefe steuert die Empfindlichkeit der Mausrad-Tiefenbewegung. Eine größere Zahl beschleunigt den Zoom des Controllers.
* **Standardcontrollerabstand** ist der anfängliche Abstand der Controller von der Kamera. Wenn Sie auf die Schaltfläche **Zurücksetzen** klicken, werden Controller ebenfalls in dieser Entfernung platzieren.
* **Controller Jitter Amount** fügt Controllern zufällige Bewegung hinzu. Dieses Feature kann verwendet werden, um ungenaue Controllernachverfolgung auf dem Gerät zu simulieren und sicherzustellen, dass Interaktionen mit lauten Eingaben gut funktionieren.

<iframe width="560" height="315" src="https://www.youtube.com/embed/uRYfwuqsjBQ" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="hand-gestures"></a>Handgesten

Handgesten wie Zusammendrücken, Greifen, Klappen usw. können ebenfalls simuliert werden.

1. Aktivieren der Handsteuerung mithilfe des Bearbeitungsschlüssels für den **linken/rechten Controller** *(Linke UMSCHALTTASTE* oder *LEERTASTE)*

2. Halten Sie beim Bearbeiten eine Maustaste gedrückt, um eine Handgeste auszuführen.

Jede der Maustasten kann zugeordnet werden, um die Handform mithilfe der Einstellungen für *linke/mittlere/rechte Mausgeste* in eine andere Geste zu transformieren. Die *Standardmäßige Handgeste* ist die Form der Hand, wenn keine Schaltfläche gedrückt wird.

> [!NOTE]
> Die *Geste Zusammendringen* ist die einzige Geste, die an diesem Punkt die Aktion "Auswählen" ausführt.

### <a name="one-hand-manipulation"></a>Einseitige Bearbeitung

1. Drücken und halten Sie **die Bearbeitungstaste für den linken/rechten Controller** gedrückt *(Linke UMSCHALTTASTE* oder *LEERTASTE).*
2. Zeigen auf das Objekt
3. Halten Sie die Maustaste gedrückt, um sie zu heften.
4. Verwenden der Maus zum Verschieben des Objekts
5. Lassen Sie die Maustaste los, um die Interaktion zu beenden.

<iframe width="560" height="315" src="https://www.youtube.com/embed/rM0xaHam6wM" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="two-hand-manipulation"></a>Zweihandmanipulation

Für die gleichzeitige Bearbeitung von Objekten mit zwei Händen wird der persistente Handmodus empfohlen.

1. Umschalten an beiden Händen durch Drücken der Umschalttasten (*T/Y*).
1. Bearbeiten Sie eine Hand nach der anderen:
    1. Halten **Sie den Platz,** um die rechte Hand zu steuern.
    1. Bewegen sie die Hand an den Ort, an dem Sie das Objekt greifen möchten.
    1. Drücken Sie die **linke Maustaste,** um die Stiftbewegung *zu* aktivieren.
    1. **Freigabebereich,** um die Steuerung der rechten Hand zu beenden. Die Hand wird an Ort und  Stelle fixiert und in der Stiftgeste gesperrt, da sie nicht mehr bearbeitet wird.
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

1. Aktivieren der GGV-Simulation durch Wechseln des **Handsimulationsmodus** zu Gesten im [Eingabesimulationsprofil](#enabling-the-input-simulation-service) 
1. Drehen Sie die Kamera, um den Anviertcursor auf das interaktive Objekt zu zeigen (rechte Maustaste).
1. Halten Sie **Platz,** um die rechte Hand zu steuern.
1. Klicken und halten Sie die **linke Maustaste** gedrückt, um zu interagieren.
1. Verwenden der Maus zum Verschieben des Objekts
1. Loslassen der Maustaste zum Beenden der Interaktion

<iframe width="560" height="315" src="https://www.youtube.com/embed/6841rRMdqWw" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="raising-teleport-events"></a>Auslösen von Teleportereignissen

Um das Teleportereignis in der Eingabesimulation auszulösung, konfigurieren Sie die Handgesteneinstellungen im Eingabesimulationsprofil so, dass eine die **Teleport-Startgeste** und die andere die **Teleport-Endgeste** ausführt. Mit der **Teleport-Startgeste** wird der Teleport-Zeiger angezeigt, während das **Teleport-End-Gesure** die Teleportaktion abschließt und den Benutzer bewegt.

Die y-Position des resultierenden Teleports hängt von der Verschiebung der Kamera entlang der y-Achse ab. Im Editor ist dies standardmäßig 0. Verwenden Sie daher die **Schlüssel Q** und **E,** um sie an die entsprechende Höhe anzupassen.

![Eingabesimulation – Teleporteinstellungen](../images/input-simulation/InputSimulationTeleport.gif)

### <a name="motion-controller-interaction"></a>Interaktion des Bewegungscontrollers

Die simulierten Motion-Controller können auf die gleiche Weise bearbeitet werden wie artikulierte Hände. Das Interaktionsmodell ähnelt der fernen Interaktion der artikulierten Hand, während trigger, grab und menu keys der *linken Maustaste* bzw. *G-* bzw. *M-Taste* zugeordnet werden.

### <a name="eye-tracking"></a>Eyetracking – Blickverfolgung

[Die Eyetrackingsimulation](../input/eye-tracking/eye-tracking-basic-setup.md#simulating-eye-tracking-in-the-unity-editor) kann aktiviert werden, indem Sie die Option **Blickposition simulieren** im [Eingabesimulationsprofil](#enabling-the-input-simulation-service)aktivieren. Dies sollte nicht bei Interaktionen im GGV- oder Motion Controller-Stil verwendet werden (stellen Sie daher sicher, dass **der Standard-Controllersimulationsmodus** auf *Artikulierte Hand* festgelegt ist).

## <a name="see-also"></a>Weitere Informationen

* [Eingabesystemprofil](../input/input-providers.md).