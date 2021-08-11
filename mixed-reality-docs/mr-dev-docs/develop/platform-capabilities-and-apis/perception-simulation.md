---
title: Perception Simulation (Wahrnehmungssimulation)
description: Leitfaden zur Verwendung der Perception Simulation-Bibliothek zum Automatisieren simulierter Eingaben für immersive Anwendungen
author: pbarnettms
ms.author: pbarnett
ms.date: 05/12/2020
ms.topic: article
keywords: HoloLens, Simulation, Testen
ms.openlocfilehash: 8d2999868bfdcf67c1174209566e67fe937005946ef82dd50337d9098c1e1971
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193774"
---
# <a name="perception-simulation"></a>Perception Simulation (Wahrnehmungssimulation)

Möchten Sie einen automatisierten Test für Ihre App erstellen? Möchten Sie, dass Ihre Tests über Komponententests auf Komponentenebene hinausgehen und Ihre App tatsächlich end-to-end durchführen? Die Wahrnehmungssimulation ist das, was Sie suchen. Die Perception Simulation-Bibliothek sendet Eingabedaten von Menschen und der Welt an Ihre App, damit Sie Ihre Tests automatisieren können. Beispielsweise können Sie die Eingabe eines Menschen simulieren, der nach einer bestimmten, wiederholbaren Position sucht, und dann eine Geste oder einen Bewegungscontroller verwenden.

Perception Simulation kann simulierte Eingaben wie diese an einen physischen HoloLens, den HoloLens-Emulator (erste Generation), den HoloLens 2 Emulator oder einen PC mit installiertem Mixed Reality-Portal senden. Perception Simulation umgeht die Livesensoren auf Mixed Reality Gerät und sendet simulierte Eingaben an Anwendungen, die auf dem Gerät ausgeführt werden. Anwendungen empfangen diese Eingabeereignisse über dieselben APIs, die sie immer verwenden, und können den Unterschied zwischen der Ausführung mit echten Sensoren und der Wahrnehmungssimulation nicht erkennen. Perception Simulation ist die gleiche Technologie, die von HoloLens Emulatoren verwendet wird, um simulierte Eingaben an den virtuellen Computer HoloLens senden.

Um mit der Verwendung der Simulation in Ihrem Code zu beginnen, erstellen Sie zunächst ein IPerceptionSimulationManager-Objekt. Über dieses Objekt können Sie Befehle zum Steuern der Eigenschaften eines simulierten "Menschen" ausführen, einschließlich Kopfposition, Handposition und Gesten. Sie können auch Motion-Controller aktivieren und bearbeiten.

## <a name="setting-up-a-visual-studio-project-for-perception-simulation"></a>Einrichten eines Visual Studio Project für die Wahrnehmungssimulation
1. [Installieren Sie den HoloLens Emulator auf](../install-the-tools.md) Ihrem Entwicklungs-PC. Der Emulator enthält die Bibliotheken, die Sie für Perception Simulation verwenden.
2. Erstellen Sie ein neues Visual Studio C#-Desktopprojekt (ein Konsolen-Project funktioniert für den Einstieg gut).
3. Fügen Sie Ihrem Projekt die folgenden Binärdateien als Verweise hinzu (Project->Add->Reference...). Sie finden sie in %ProgramFiles(x86)%\Microsoft XDE (Version), z.B. \\ **%ProgramFiles(x86)%\Microsoft XDE \\ 10.0.18362.0** für die HoloLens 2 Emulator.  (Hinweis: Obwohl die Binärdateien Teil der HoloLens 2 Emulator sind, funktionieren sie auch für Windows Mixed Reality auf dem Desktop.) Eine. PerceptionSimulationManager.Interop.dll: Verwalteter C#-Wrapper für Perception Simulation.
    b. PerceptionSimulationRest.dll: Bibliothek zum Einrichten eines Websocket-Kommunikationskanals zum HoloLens Emulator.
    c. SimulationStream.Interop.dll: Freigegebene Typen für die Simulation.
4. Fügen Sie dem Projekt PerceptionSimulationManager.dll binäre Implementierungsdatei hinzu. Fügen Sie ihn zunächst als Binärdatei zum Projekt hinzu (Project->Add->Vorhandenes Element...). Speichern Sie sie als Link, damit sie nicht in Den Projektquellenordner kopiert wird. ![Fügen PerceptionSimulationManager.dll dem Projekt als Link ](images/saveaslink.png) b hinzu. Stellen Sie dann sicher, dass sie beim Build in Ihren Ausgabeordner kopiert wird. Dies ist im Eigenschaftenblatt für die Binärdatei zu sehen. ![Markieren PerceptionSimulationManager.dll, die in das Ausgabeverzeichnis kopiert werden soll](images/copyalways.png)
5. Legen Sie Ihre aktive Projektmappenplattform auf x64 fest.  (Verwenden Sie die Konfigurations-Manager, um einen Plattformeintrag für x64 zu erstellen, sofern noch kein Eintrag vorhanden ist.)

## <a name="creating-an-iperceptionsimulation-manager-object"></a>Erstellen eines IPerceptionSimulation Manager-Objekts

Zum Steuern der Simulation geben Sie Updates für Objekte aus, die aus einem IPerceptionSimulationManager-Objekt abgerufen wurden. Der erste Schritt besteht im Erhalten dieses Objekts und verbinden es mit Ihrem Zielgerät oder Emulator. Sie können die IP-Adresse Ihres Emulators erhalten, indem Sie auf der Symbolleiste auf Geräteportal schaltfläche [klicken.](using-the-hololens-emulator.md)

![Öffnen Geräteportal Symbol ](images/emulator-deviceportal.png) **Öffnen Geräteportal:** Öffnen Sie die Windows Geräteportal für das HoloLens Betriebssystem im Emulator.  Für Windows Mixed Reality kann dies in der Einstellungen-App unter "Update & Security" und dann im Abschnitt "Verbinden using:" unter "Enable Geräteportal" abgerufen werden.  Notieren Sie sich sowohl die IP-Adresse als auch den Port.

Rufen Sie zunächst RestSimulationStreamSink.Create auf, um ein RestSimulationStreamSink-Objekt zu erhalten. Dies ist das Zielgerät oder der Emulator, das Sie über eine HTTP-Verbindung steuern. Ihre Befehle werden an das Gerät [](using-the-windows-device-portal.md) oder den Emulator übergeben und Windows Geräteportal verarbeitet. Die vier Parameter, die Sie zum Erstellen eines Objekts benötigen, sind:
* URI-URI: IP-Adresse des Zielgeräts (z.B. " https://123.123.123.123 " oder " https://123.123.123.123:50080 ")
* System.Net.NetworkCredential-Anmeldeinformationen: Benutzername/Kennwort zum [](using-the-windows-device-portal.md) Herstellen einer Verbindung mit dem Windows Geräteportal auf dem Zielgerät oder Emulator. Wenn Sie eine Verbindung mit dem Emulator über seine lokale Adresse herstellen (z.B. 168.*.* *) auf demselben PC werden alle Anmeldeinformationen akzeptiert.
* bool normal: True für normale Priorität, FALSE für niedrige Priorität. Im Allgemeinen möchten Sie dies für *Testszenarien* auf TRUE festlegen, wodurch der Test die Kontrolle übernehmen kann.  Der Emulator und Windows Mixed Reality Simulation verwenden Verbindungen mit niedriger Priorität.  Wenn der Test auch eine Verbindung mit niedriger Priorität verwendet, wird die zuletzt hergestellte Verbindung kontrolliert.
* System.Threading.CancellationToken-Token: Token zum Abbrechen des asynchronen Vorgangs.

Zweitens erstellen Sie den IPerceptionSimulationManager. Dies ist das Objekt, das Sie zum Steuern der Simulation verwenden. Dies muss auch in einer asynchronen Methode erfolgen.

## <a name="control-the-simulated-human"></a>Steuern des simulierten Menschen

Ein IPerceptionSimulationManager verfügt über eine Human-Eigenschaft, die ein ISimulatedOsi-Objekt zurückgibt. Um den simulierten Menschen zu steuern, führen Sie Vorgänge für dieses Objekt aus. Beispiel:

```
manager.Human.Move(new Vector3(0.1f, 0.0f, 0.0f))
```

## <a name="basic-sample-c-console-application"></a>Einfache C#-Beispielkonsolenanwendung

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            Task.Run(async () =>
            {
                RestSimulationStreamSink sink = null;
                CancellationToken token = new System.Threading.CancellationToken();

                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("https://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }

                // Always close the sink to return control to the previous application.
                if (sink != null)
                {
                    await sink.Close(token);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();
        }
    }
}
```

## <a name="extended-sample-c-console-application"></a>Erweiterte C#-Beispielkonsolenanwendung

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;
using Microsoft.PerceptionSimulation;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            RestSimulationStreamSink sink = null;
            CancellationToken token = new System.Threading.CancellationToken();

            Task.Run(async () =>
            {
                try
                {
                    sink = await RestSimulationStreamSink.Create(
                        // use the IP address for your device/emulator
                        new Uri("https://169.254.227.115"),
                        // no credentials are needed for the emulator
                        new System.Net.NetworkCredential("", ""),
                        // normal priorty
                        true,
                        // cancel token
                        token);

                    IPerceptionSimulationManager manager = PerceptionSimulationManager.CreatePerceptionSimulationManager(sink);

                    // Now, we'll simulate a sequence of actions.
                    // Sleeps in-between each action give time to the system
                    // to be able to properly react.
                    // This is just an example. A proper automated test should verify
                    // that the app has behaved correctly
                    // before proceeding to the next step, instead of using Sleeps.

                    // Activate the right hand
                    manager.Human.RightHand.Activated = true;

                    // Simulate Bloom gesture, which should cause Shell to disappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... this time, Shell should reappear
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);

                    // Simulate a Head rotation down around the X axis
                    // This should cause gaze to aim about the center of the screen
                    manager.Human.Head.Rotate(new Rotation3(0.04f, 0.0f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a finger press & release
                    // Should cause a tap on the center tile, thus launching it
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate a second finger press & release
                    // Should activate the app that was launched when the center tile was clicked
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(5000);

                    // Simulate a Head rotation towards the upper right corner
                    manager.Human.Head.Rotate(new Rotation3(-0.14f, 0.17f, 0.0f));
                    Thread.Sleep(300);

                    // Simulate a third finger press & release
                    // Should press the Remove button on the app
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerPressed);
                    Thread.Sleep(300);
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.FingerReleased);
                    Thread.Sleep(2000);

                    // Simulate Bloom gesture again... bringing the Shell back once more
                    manager.Human.RightHand.PerformGesture(SimulatedGesture.Home);
                    Thread.Sleep(2000);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e);
                }
            });

            // If main exits, the process exits.  
            Console.WriteLine("Press any key to exit...");
            Console.ReadLine();

            // Always close the sink to return control to the previous application.
            if (sink != null)
            {
                sink.Close(token);
            }
        }
    }
}
```

## <a name="note-on-6-dof-controllers"></a>Hinweis zu 6-DOF-Controllern

Bevor Sie Eigenschaften für Methoden auf einem simulierten 6-DOF-Controller aufrufen, müssen Sie den Controller aktivieren.  Wenn dies nicht der Ergebnis ist, wird eine Ausnahme ausgelöst.  Ab dem Windows 10 May 2019 Update können simulierte 6-DOF-Controller installiert und aktiviert werden, indem die Status-Eigenschaft für das ISimulatedSixDofController-Objekt auf SimulatedSixDofControllerStatus.Active festgelegt wird.
In der Windows 10 October 2018 Update und früher müssen Sie zunächst separat einen simulierten 6-DOF-Controller installieren, indem Sie das PerceptionSimulationDevice-Tool aufrufen, das sich im Ordner \Windows\System32 befindet.  Dieses Tool wird wie folgt verwendet:


```
    PerceptionSimulationDevice.exe <action> 6dof <instance>
```

Beispiel:

```
    PerceptionSimulationDevice.exe i 6dof 1
```

Unterstützte Aktionen sind:
* i = install
* q = Abfrage
* r = remove

Unterstützte Instanzen:
* 1 = der linke 6-DOF-Controller
* 2 = der richtige 6-DOF-Controller

Der Exitcode des Prozesses gibt einen Erfolg (null Rückgabewert) oder einen Fehler (kein Null-Rückgabewert) an.  Wenn Sie die q-Aktion verwenden, um zu abfragen, ob ein Controller installiert ist, ist der Rückgabewert 0 (null), wenn der Controller noch nicht installiert ist, oder einer (1), wenn der Controller installiert ist.

Wenn Sie einen Controller auf dem Windows 10 October 2018 Update oder früher entfernen, legen Sie seinen Status zunächst über die API auf Aus fest, und rufen Sie dann das PerceptionSimulationDevice-Tool auf.

Dieses Tool muss als Administrator ausgeführt werden.




## <a name="api-reference"></a>API-Referenz

### <a name="microsoftperceptionsimulationsimulateddevicetype"></a>Microsoft.PerceptionSimulation.SimulatedDeviceType

Beschreibt einen simulierten Gerätetyp.

```
public enum SimulatedDeviceType
{
    Reference = 0
}
```

**Microsoft.PerceptionSimulation.SimulatedDeviceType.Reference**

Ein fiktives Referenzgerät, die Standardeinstellung für PerceptionSimulationManager

### <a name="microsoftperceptionsimulationheadtrackermode"></a>Microsoft.PerceptionSimulation.HeadTrackerMode

Beschreibt einen HeadTracker-Modus

```
public enum HeadTrackerMode
{
    Default = 0,
    Orientation = 1,
    Position = 2
}
```

**Microsoft.PerceptionSimulation.HeadTrackerMode.Default**

Standardkopfnachverfolgung. Dies bedeutet, dass das System den besten Nachverfolgungsmodus für den Kopf basierend auf Laufzeitbedingungen auswählen kann.

**Microsoft.PerceptionSimulation.HeadTrackerMode.Orientation**

Nur Kopfausrichtungsnachverfolgung. Dies bedeutet, dass die nachverfolgte Position möglicherweise nicht zuverlässig ist und einige Funktionen, die von der Kopfposition abhängen, möglicherweise nicht verfügbar sind.

**Microsoft.PerceptionSimulation.HeadTrackerMode.Position**

Positionskopfnachverfolgung. Dies bedeutet, dass die nachverfolgte Kopfposition und -ausrichtung zuverlässig sind.

### <a name="microsoftperceptionsimulationsimulatedgesture"></a>Microsoft.PerceptionSimulation.SimulatedGesture

Beschreibt eine simulierte Geste

```
public enum SimulatedGesture
{
    None = 0,
    FingerPressed = 1,
    FingerReleased = 2,
    Home = 4,
    Max = Home
}
```

**Microsoft.PerceptionSimulation.SimulatedGesture.None**

Ein Sentinelwert, der verwendet wird, um keine Gesten anzugeben.

**Microsoft.PerceptionSimulation.SimulatedGesture.FingerPressed**

Eine gedrückte Fingergeste.

**Microsoft.PerceptionSimulation.SimulatedGesture.FingerReleased**

Eine Geste, die mit dem Finger freigelassen wurde.

**Microsoft.PerceptionSimulation.SimulatedGesture.Home**

Die Start-/Systemgeste.

**Microsoft.PerceptionSimulation.SimulatedGesture.Max**

Die maximal gültige Geste.

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerstatus"></a>Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus

Die möglichen Zustände eines simulierten 6-DOF-Controllers.

```
public enum SimulatedSixDofControllerStatus
{
    Off = 0,
    Active = 1,
    TrackingLost = 2,
}
```

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Off**

Der 6-DOF-Controller ist ausgeschaltet.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.Active**

Der 6-DOF-Controller wird eingeschaltet und nachverfolgt.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerStatus.TrackingLost**

Der 6-DOF-Controller ist eingeschaltet, kann aber nicht nachverfolgt werden.

### <a name="microsoftperceptionsimulationsimulatedsixdofcontrollerbutton"></a>Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton

Die unterstützten Schaltflächen auf einem simulierten 6-DOF-Controller.

```
public enum SimulatedSixDofControllerButton
{
    None = 0,
    Home = 1,
    Menu = 2,
    Grip = 4,
    TouchpadPress = 8,
    Select = 16,
    TouchpadTouch = 32,
    Thumbstick = 64,
    Max = Thumbstick
}
```

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.None**

Ein Sentinelwert, der verwendet wird, um keine Schaltflächen anzugeben.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Home**

Die Schaltfläche Start wird gedrückt.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Menu**

Die Schaltfläche Menü wird gedrückt.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Grip**

Die Greiftaste wird gedrückt.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadPress**

Das TouchPad wird gedrückt.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Select**

Die Schaltfläche Auswählen wird gedrückt.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.TouchpadTouch**

Das TouchPad wird berührt.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Thumbstick**

Der Fingerabdruck wird gedrückt.

**Microsoft.PerceptionSimulation.SimulatedSixDofControllerButton.Max**

Die maximal gültige Schaltfläche.


### <a name="microsoftperceptionsimulationsimulatedeyescalibrationstate"></a>Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState

Der Kalibrierungszustand der simulierten Augen

```
public enum SimulatedGesture
{
    Unavailable = 0,
    Ready = 1,
    Configuring = 2,
    UserCalibrationNeeded = 3
}
```

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Unavailable**

Die Kalibrierung der Augen ist nicht verfügbar.

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.Ready**

Die Augen wurden kalibriert.  Dies ist der Standardwert.

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.ConfigUring**

Die Augen werden kalibriert.

**Microsoft.PerceptionSimulation.SimulatedEyesCalibrationState.UserCalibrationNeeded**

Die Augen müssen kalibriert werden.

### <a name="microsoftperceptionsimulationsimulatedhandjointtrackingaccuracy"></a>Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy

Die Nachverfolgungsgenauigkeit eines Handgelenks.

```
public enum SimulatedHandJointTrackingAccuracy
{
    Unavailable = 0,
    Approximate = 1,
    Visible = 2
}
```

**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Unavailable**

Das Gemeinsame wird nicht nachverfolgt.

**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Approximate**

Die Gemeinsame Position wird abgeleitet.

**Microsoft.PerceptionSimulation.SimulatedHandJointTrackingAccuracy.Visible**

Das Joint wird vollständig nachverfolgt.

### <a name="microsoftperceptionsimulationsimulatedhandpose"></a>Microsoft.PerceptionSimulation.SimulatedHandPose

Die Nachverfolgungsgenauigkeit eines Handgelenks.

```
public enum SimulatedHandPose
{
    Closed = 0,
    Open = 1,
    Point = 2,
    Pinch = 3,
    Max = Pinch
}
```

**Microsoft.PerceptionSimulation.SimulatedHandPose.Closed**

Die Fingergelenke der Hand sind so konfiguriert, dass sie eine geschlossene Pose widerspiegeln.

**Microsoft.PerceptionSimulation.SimulatedHandPose.Open**

Die Fingergelenke der Hand sind so konfiguriert, dass sie eine offene Pose widerspiegeln.

**Microsoft.PerceptionSimulation.SimulatedHandPose.Point**

Die Fingergelenke der Hand sind so konfiguriert, dass sie eine zeigende Pose widerspiegeln.

**Microsoft.PerceptionSimulation.SimulatedHandPose.Pinch**

Die Fingerknüpfe der Hand sind so konfiguriert, dass sie eine kneippende Pose widerspiegeln.

**Microsoft.PerceptionSimulation.SimulatedHandPose.Max**

Der maximal gültige Wert für SimulatedHandPose.


### <a name="microsoftperceptionsimulationplaybackstate"></a>Microsoft.PerceptionSimulation.PlaybackState

Beschreibt den Zustand einer Wiedergabe.

```
public enum PlaybackState
{
    Stopped = 0,
    Playing = 1,
    Paused = 2,
    End = 3,
}
```

**Microsoft.PerceptionSimulation.PlaybackState.Stopped**

Die Aufzeichnung ist derzeit beendet und für die Wiedergabe bereit.

**Microsoft.PerceptionSimulation.PlaybackState.Playing**

Die Aufzeichnung wird derzeit abspielt.

**Microsoft.PerceptionSimulation.PlaybackState.Paused**

Die Aufzeichnung wird derzeit angehalten.

**Microsoft.PerceptionSimulation.PlaybackState.End**

Die Aufzeichnung hat das Ende erreicht.

### <a name="microsoftperceptionsimulationvector3"></a>Microsoft.PerceptionSimulation.Vector3

Beschreibt einen Vektor mit drei Komponenten, der einen Punkt oder einen Vektor im 3D-Raum beschreiben kann.

```
public struct Vector3
{
    public float X;
    public float Y;
    public float Z;
    public Vector3(float x, float y, float z);
}
```

**Microsoft.PerceptionSimulation.Vector3.X**

Die X-Komponente des Vektors.

**Microsoft.PerceptionSimulation.Vector3.Y**

Die Y-Komponente des Vektors.

**Microsoft.PerceptionSimulation.Vector3.Z**

Die Z-Komponente des Vektors.

**Microsoft.PerceptionSimulation.Vector3.#ctor(System.Single, System.Single, System.Single)**

Erstellen Sie einen neuen Vector3.

Parameter
* x: Die x-Komponente des Vektors.
* y: Die y-Komponente des Vektors.
* z: Die z-Komponente des Vektors.

### <a name="microsoftperceptionsimulationrotation3"></a>Microsoft.PerceptionSimulation.Rotation3

Beschreibt eine Drehung von drei Komponenten.

```
public struct Rotation3
{
    public float Pitch;
    public float Yaw;
    public float Roll;
    public Rotation3(float pitch, float yaw, float roll);
}
```

**Microsoft.PerceptionSimulation.Rotation3.Pitch**

Die Pitch-Komponente der Drehung, nach unten um die X-Achse.

**Microsoft.PerceptionSimulation.Rotation3.Yaw**

Die Yaw-Komponente der Drehung, direkt um die Y-Achse.

**Microsoft.PerceptionSimulation.Rotation3.Roll**

Die Roll-Komponente der Drehung, direkt um die Z-Achse.

**Microsoft.PerceptionSimulation.Rotation3.#ctor(System.Single, System.Single, System.Single)**

Erstellen Sie eine neue Rotation3.

Parameter
* pitch: Die Tonhöhenkomponente der Drehung.
* yaw: Die Yaw-Komponente der Drehung.
* roll: Die Rollkomponente der Drehung.

### <a name="microsoftperceptionsimulationsimulatedhandjointconfiguration"></a>Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration

Beschreibt die Konfiguration eines Joints auf einer simulierten Hand.

```
public struct SimulatedHandJointConfiguration
{
    public Vector3 Position;
    public Rotation3 Rotation;
    public SimulatedHandJointTrackingAccuracy TrackingAccuracy;
}
```

**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Position**

Die Position des Joints.

**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.Rotation**

Die Drehung des Fugens.

**Microsoft.PerceptionSimulation.SimulatedHandJointConfiguration.TrackingAccuracy**

Die Nachverfolgungsgenauigkeit des Fugens.


### <a name="microsoftperceptionsimulationfrustum"></a>Microsoft.PerceptionSimulation.Frustum

Beschreibt ein Ansichts frustum, wie es in der Regel von einer Kamera verwendet wird.

```
public struct Frustum
{
    float Near;
    float Far;
    float FieldOfView;
    float AspectRatio;
}
```

**Microsoft.PerceptionSimulation.Frustum.Near**

Der minimale Abstand, der im Frustum enthalten ist.

**Microsoft.PerceptionSimulation.Frustum.Far**

Der maximale Abstand, der im Frustum enthalten ist.

**Microsoft.PerceptionSimulation.Frustum.FieldOfView**

Das horizontale Sichtfeld des Frustums im Bogenmaß (kleiner als PI).

**Microsoft.PerceptionSimulation.Frustum.AspectRatio**

Das Verhältnis zwischen dem horizontalen Feld der Ansicht und dem vertikalen Sichtfeld.

### <a name="microsoftperceptionsimulationsimulateddisplayconfiguration"></a>Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration

Beschreibt die Konfiguration der Anzeige des simulierten Headsets.

```
public struct SimulatedDisplayConfiguration
{
    public Vector3 LeftEyePosition;
    public Rotation3 LeftEyeRotation;
    public Vector3 RightEyePosition;
    public Rotation3 RightEyeRotation;
    public float Ipd;
    public bool ApplyEyeTransforms;
    public bool ApplyIpd;
}
```

**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyePosition**

Die Transformation von der Mitte des Kopfs zum linken Auge für das Stereorendering.

**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.LeftEyeRotation**

Die Drehung des linken Auges zum Stereorendering.

**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyePosition**

Die Transformation von der Mitte des Kopfs zum rechten Auge für Stereorenderingzwecke.

**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.RightEyeRotation**

Die Drehung des rechten Auges zum Stereorendering.

**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.Ipd**

Der ipd-Wert, der vom System für Stereorenderingzwecke gemeldet wird.

**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyEyeTransforms**

Gibt an, ob die für Transformationen des linken und rechten Auges angegebenen Werte als gültig betrachtet und auf das ausgeführte System angewendet werden sollen.

**Microsoft.PerceptionSimulation.SimulatedDisplayConfiguration.ApplyIpd**

Gibt an, ob der für Ipd angegebene Wert als gültig betrachtet und auf das ausgeführte System angewendet werden soll.


### <a name="microsoftperceptionsimulationiperceptionsimulationmanager"></a>Microsoft.PerceptionSimulation.IPerceptionSimulationManager

Root zum Generieren der Pakete, die zum Steuern eines Geräts verwendet werden.

```
public interface IPerceptionSimulationManager
{   
    ISimulatedDevice Device { get; }
    ISimulatedHuman Human { get; }
    void Reset();
}
```

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Device**

Rufen Sie das simulierte Geräteobjekt ab, das die simulierte menschliche und die simulierte Welt interpretiert.

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Human**

Rufen Sie das Objekt ab, das den simulierten Menschen steuert.

**Microsoft.PerceptionSimulation.IPerceptionSimulationManager.Reset**

Setzt die Simulation auf ihren Standardzustand zurück.

### <a name="microsoftperceptionsimulationisimulateddevice"></a>Microsoft.PerceptionSimulation.ISimulatedDevice

Schnittstelle, die das Gerät beschreibt, das die simulierte Welt und den simulierten Menschen interpretiert

```
public interface ISimulatedDevice
{
    ISimulatedHeadTracker HeadTracker { get; }
    ISimulatedHandTracker HandTracker { get; }
    void SetSimulatedDeviceType(SimulatedDeviceType type);
}
```

**Microsoft.PerceptionSimulation.ISimulatedDevice.HeadTracker**

Rufen Sie den Head Tracker vom simulierten Gerät ab.

**Microsoft.PerceptionSimulation.ISimulatedDevice.HandTracker**

Rufen Sie die Hand Tracker vom simulierten Gerät ab.

**Microsoft.PerceptionSimulation.ISimulatedDevice.SetSimulatedDeviceType(Microsoft.PerceptionSimulation.SimulatedDeviceType)**

Legen Sie die Eigenschaften des simulierten Geräts auf den angegebenen Gerätetyp fest.

Parameter
* type: Der neue Typ des simulierten Geräts

### <a name="microsoftperceptionsimulationisimulateddevice2"></a>Microsoft.PerceptionSimulation.ISimulatedDevice2

Zusätzliche Eigenschaften sind verfügbar, indem ISimulatedDevice in ISimulatedDevice2 umgestellt wird.

```
public interface ISimulatedDevice2
{
    bool IsUserPresent { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    SimulatedDisplayConfiguration DisplayConfiguration { get; set; }

};
```

**Microsoft.PerceptionSimulation.ISimulatedDevice2.IsUserPresent**

Ruft ab oder legt fest, ob der simulierte Mensch das Headset aktiv umstützt.

**Microsoft.PerceptionSimulation.ISimulatedDevice2.DisplayConfiguration**

Ruft die Eigenschaften der simulierten Anzeige ab oder legt sie fest.

### <a name="microsoftperceptionsimulationisimulatedheadtracker"></a>Microsoft.PerceptionSimulation.ISimulatedHeadTracker

Schnittstelle, die den Teil des simulierten Geräts beschreibt, der den Kopf des simulierten Menschen verfolgt.

```
public interface ISimulatedHeadTracker
{
    HeadTrackerMode HeadTrackerMode { get; set; }
};
```

**Microsoft.PerceptionSimulation.ISimulatedHeadTracker.HeadTrackerMode**

Ruft den aktuellen Head Tracker-Modus ab und legt diese fest.

### <a name="microsoftperceptionsimulationisimulatedhandtracker"></a>Microsoft.PerceptionSimulation.ISimulatedHandTracker

Schnittstelle, die den Teil des simulierten Geräts beschreibt, der die Hände des simulierten Menschen verfolgt

```
public interface ISimulatedHandTracker
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    float Pitch { get; set; }
    bool FrustumIgnored { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    Frustum Frustum { get; set; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.WorldPosition**

Rufen Sie die Position des Knotens in Bezug auf die Welt in Metern ab.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Position**

Rufen Sie die Position der simulierten Handverfolgung relativ zur Mitte des Kopfes ab, und legen Sie sie fest.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Pitch**

Rufen Sie die Nach-unten-Tonhöhe der simulierten Handverfolgung ab, und legen Sie sie fest.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.FrustumIgnored**

Ruft ab und legt fest, ob das Frustum der simulierten Handverfolgung ignoriert wird. Wenn sie ignoriert werden, sind beide Hände immer sichtbar. Wenn sie nicht ignoriert werden (Standardeinstellung), werden Hände nur angezeigt, wenn sie sich innerhalb des Frustums der Handverfolgung befinden.

**Microsoft.PerceptionSimulation.ISimulatedHandTracker.Frustum**

Rufen Sie die Frustumeigenschaften ab, mit denen bestimmt wird, ob die Hände für die simulierte Handverfolgung sichtbar sind, und legen Sie sie fest.

### <a name="microsoftperceptionsimulationisimulatedhuman"></a>Microsoft.PerceptionSimulation.ISimulated Csv

Schnittstelle der obersten Ebene zum Steuern des simulierten Menschen.

```
public interface ISimulatedHuman 
{
    Vector3 WorldPosition { get; set; }
    float Direction { get; set; }
    float Height { get; set; }
    ISimulatedHand LeftHand { get; }
    ISimulatedHand RightHand { get; }
    ISimulatedHead Head { get; }s
    void Move(Vector3 translation);
    void Rotate(float radians);
}
```

**Microsoft.PerceptionSimulation.ISimulatedMulated.WorldPosition**

Rufen Sie die Position des Knotens in Bezug auf die Welt in Metern ab, und legen Sie sie fest. Die Position entspricht einem Punkt in der Mitte der Fußfuß des Menschen.

**Microsoft.PerceptionSimulation.ISimulatedMulated.Direction**

Ruft die Richtung der simulierten menschlichen Gesichter auf der Welt ab und legt diese fest. 0 Bogenmaße werden auf der negativen Z-Achse nach unten geschaltet. Positive Bogenmaße drehen sich im Uhrzeigersinn um die Y-Achse.

**Microsoft.PerceptionSimulation.ISimulated Mouse.Height**

Ruft die Höhe des simulierten Menschen in Metern ab und legt diese fest.

**Microsoft.PerceptionSimulation.ISimulatedMulated.LeftHand**

Ruft die linke Hand des simulierten Menschen ab.

**Microsoft.PerceptionSimulation.ISimulated Mouse.RightHand**

Rufen Sie die rechte Hand des simulierten Menschen ab.

**Microsoft.PerceptionSimulation.ISimulated Mouse.Head**

Rufen Sie den Kopf des simulierten Menschen ab.

**Microsoft.PerceptionSimulation.ISimulated Mouse.Move(Microsoft.PerceptionSimulation.Vector3)**

Verschieben Sie den simulierten Menschen relativ zur aktuellen Position in Metern.

Parameter
* translation: Die zu verschiebende Übersetzung relativ zur aktuellen Position.

**Microsoft.PerceptionSimulation.ISimulated Mouse.Rotate(System.Single)**

Drehen des simulierten Menschen relativ zur aktuellen Richtung im Uhrzeigersinn um die Y-Achse

Parameter
* Bogenmaß: Der Betrag, der um die Y-Achse gedreht werden soll.

### <a name="microsoftperceptionsimulationisimulatedhuman2"></a>Microsoft.PerceptionSimulation.ISimulated Csv2

Zusätzliche Eigenschaften sind verfügbar, indem ISimulated Ausformulieren in ISimulated Ausdruck2 erfolgt.

```
public interface ISimulatedHuman2
{
    /* New members in addition to those available on ISimulatedHuman */
    ISimulatedSixDofController LeftController { get; }
    ISimulatedSixDofController RightController { get; }
}
```

**Microsoft.PerceptionSimulation.ISimulated Csv2.LeftController**

Rufen Sie den linken 6-DOF-Controller ab.

**Microsoft.PerceptionSimulation.ISimulated Mouse2.RightController**

Rufen Sie den rechten 6-DOF-Controller ab.


### <a name="microsoftperceptionsimulationisimulatedhand"></a>Microsoft.PerceptionSimulation.ISimulatedHand

Schnittstelle, die eine Hand des simulierten Menschen beschreibt

```
public interface ISimulatedHand
{
    Vector3 WorldPosition { get; }
    Vector3 Position { get; set; }
    bool Activated { [return: MarshalAs(UnmanagedType.Bool)] get; [param: MarshalAs(UnmanagedType.Bool)] set; }
    bool Visible { [return: MarshalAs(UnmanagedType.Bool)] get; }
    void EnsureVisible();
    void Move(Vector3 translation);
    void PerformGesture(SimulatedGesture gesture);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHand.WorldPosition**

Rufen Sie die Position des Knotens in Bezug auf die Welt in Metern ab.

**Microsoft.PerceptionSimulation.ISimulatedHand.Position**

Ruft die Position der simulierten Hand relativ zum Menschen in Metern ab und legt diese fest.

**Microsoft.PerceptionSimulation.ISimulatedHand.Activated**

Ruft ab und legt fest, ob die Hand derzeit aktiviert ist.

**Microsoft.PerceptionSimulation.ISimulatedHand.Visible**

Ruft ab, ob die Hand derzeit für simulatedDevice sichtbar ist (d. b. ob sie sich in einer Position befindet, die vom HandTracker erkannt werden kann).

**Microsoft.PerceptionSimulation.ISimulatedHand.EnsureVisible**

Bewegen Sie die Hand so, dass sie für simulatedDevice sichtbar ist.

**Microsoft.PerceptionSimulation.ISimulatedHand.Move(Microsoft.PerceptionSimulation.Vector3)**

Verschieben Sie die Position der simulierten Hand relativ zur aktuellen Position in Metern.

Parameter
* translation: Der Betrag, um den die simulierte Hand übersetzt werden soll.

**Microsoft.PerceptionSimulation.ISimulatedHand.PerformGesture(Microsoft.PerceptionSimulation.SimulatedGesture)**

Führen Sie eine Geste mit der simulierten Hand aus.  Sie wird nur vom System erkannt, wenn die Hand aktiviert ist.

Parameter
* gesture: Die auszuführende Geste.

### <a name="microsoftperceptionsimulationisimulatedhand2"></a>Microsoft.PerceptionSimulation.ISimulatedHand2

Zusätzliche Eigenschaften sind verfügbar, indem ISimulatedHand in ISimulatedHand2 umgestellt wird.
```
public interface ISimulatedHand2
{
    /* New members in addition to those available on ISimulatedHand */
    Rotation3 Orientation { get; set; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHand2.Orientation**

Ruft die Drehung der simulierten Hand ab oder legt sie fest.  Positive Bogenmaße drehen sich im Uhrzeigersinn, wenn Sie entlang der Achse suchen.

### <a name="microsoftperceptionsimulationisimulatedhand3"></a>Microsoft.PerceptionSimulation.ISimulatedHand3

Zusätzliche Eigenschaften sind verfügbar, indem eine ISimulatedHand in ISimulatedHand3 umgestellt wird.
```
public interface ISimulatedHand3
{
    /* New members in addition to those available on ISimulatedHand and ISimulatedHand2 */
    GetJointConfiguration(SimulatedHandJoint joint, out SimulatedHandJointConfiguration jointConfiguration);
    SetJointConfiguration(SimulatedHandJoint joint, SimulatedHandJointConfiguration jointConfiguration);
    SetHandPose(SimulatedHandPose pose, bool animate);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHand3.GetJointConfiguration**

Abrufen der Gemeinsamen Konfiguration für das angegebene Fugen.

**Microsoft.PerceptionSimulation.ISimulatedHand3.SetJointConfiguration**

Legen Sie die Gemeinsame Konfiguration für das angegebene Fugen fest.

**Microsoft.PerceptionSimulation.ISimulatedHand3.SetHandPose**

Legen Sie die Hand auf eine bekannte Pose mit einem optionalen Flag fest, das animiert werden soll.  Hinweis: Das Animieren führt nicht dazu, dass Die Fugen sofort ihre endgültigen Gemeinsamen Konfigurationen widerspiegeln.


### <a name="microsoftperceptionsimulationisimulatedhead"></a>Microsoft.PerceptionSimulation.ISimulatedHead

Schnittstelle, die den Kopf des simulierten Menschen beschreibt.

```
public interface ISimulatedHead
{
    Vector3 WorldPosition { get; }
    Rotation3 Rotation { get; set; }
    float Diameter { get; set; }
    void Rotate(Rotation3 rotation);
}
```

**Microsoft.PerceptionSimulation.ISimulatedHead.WorldPosition**

Rufen Sie die Position des Knotens in Bezug auf die Welt in Metern ab.

**Microsoft.PerceptionSimulation.ISimulatedHead.Rotation**

Rufen Sie die Drehung des simulierten Kopfes ab. Positive Bogenmaße drehen sich im Uhrzeigersinn, wenn Sie entlang der Achse suchen.

**Microsoft.PerceptionSimulation.ISimulatedHead.Diameter**

Rufen Sie den Stärke des simulierten Kopfes ab. Dieser Wert wird verwendet, um den Mittelpunkt des Kopfs (Drehpunkt) zu bestimmen.

**Microsoft.PerceptionSimulation.ISimulatedHead.Rotate(Microsoft.PerceptionSimulation.Rotation3)**

Drehen Sie den simulierten Kopf relativ zur aktuellen Drehung. Positive Bogenmaße drehen sich im Uhrzeigersinn, wenn Sie entlang der Achse suchen.

Parameter
* rotation: Die Menge, die gedreht werden soll.

### <a name="microsoftperceptionsimulationisimulatedhead2"></a>Microsoft.PerceptionSimulation.ISimulatedHead2

Zusätzliche Eigenschaften sind verfügbar, indem ein ISimulatedHead in ISimulatedHead2 umgestellt wird.

```
public interface ISimulatedHead2
{
    /* New members in addition to those available on ISimulatedHead */
    ISimulatedEyes Eyes { get; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedHead2.Eyes**

Rufen Sie die Augen des simulierten Menschen ab.

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller"></a>Microsoft.PerceptionSimulation.ISimulatedSixDofController

Schnittstelle, die einen 6-DOF-Controller beschreibt, der dem simulierten Menschen zugeordnet ist.

```
public interface ISimulatedSixDofController
{
    Vector3 WorldPosition { get; }
    SimulatedSixDofControllerStatus Status { get; set; }
    Vector3 Position { get; }
    Rotation3 Orientation { get; set; }
    void Move(Vector3 translation);
    void PressButton(SimulatedSixDofControllerButton button);
    void ReleaseButton(SimulatedSixDofControllerButton button);
    void GetTouchpadPosition(out float x, out float y);
    void SetTouchpadPosition(float x, float y);
}
```

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.WorldPosition**

Rufen Sie die Position des Knotens in Bezug auf die Welt in Metern ab.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Status**

Ruft den aktuellen Zustand des Controllers ab oder legt den aktuellen Zustand fest.  Der Controllerstatus muss auf einen anderen Wert als Aus festgelegt werden, bevor Aufrufe zum Verschieben, Drehen oder Drücken von Schaltflächen erfolgreich sind.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Position**

Ruft die Position des simulierten Controllers relativ zum Menschen in Metern ab oder legt diese fest.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Orientation**

Ruft die Ausrichtung des simulierten Controllers ab oder legt diese fest.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.Move(Microsoft.PerceptionSimulation.Vector3)**

Verschieben Sie die Position des simulierten Controllers relativ zur aktuellen Position in Metern.

Parameter
* translation: Der Betrag, um den der simulierte Controller übersetzt werden soll.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.PressButton(SimulatedSixDofControllerButton)**

Drücken Sie eine Schaltfläche auf dem simulierten Controller.  Sie wird nur vom System erkannt, wenn der Controller aktiviert ist.

Parameter
* button: Die zu drückende Schaltfläche.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.ReleaseButton(SimulatedSixDofControllerButton)**

Lassen Sie eine Schaltfläche auf dem simulierten Controller los.  Sie wird nur vom System erkannt, wenn der Controller aktiviert ist.

Parameter
* button: Die freizugebende Schaltfläche.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.GetTouchpadPosition(out float, out float)**

Abrufen der Position eines simulierten Fingers auf dem Touchpad des simulierten Controllers.

Parameter
* x: Die horizontale Position des Fingers.
* y: Die vertikale Position des Fingers.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController.SetTouchpadPosition(float, float)**

Legen Sie die Position eines simulierten Fingers auf dem Touchpad des simulierten Controllers fest.

Parameter
* x: Die horizontale Position des Fingers.
* y: Die vertikale Position des Fingers.

### <a name="microsoftperceptionsimulationisimulatedsixdofcontroller2"></a>Microsoft.PerceptionSimulation.ISimulatedSixDofController2

Zusätzliche Eigenschaften und Methoden sind verfügbar, indem sie einen ISimulatedSixDofController in ISimulatedSixDofController2 umwandeln.

```
public interface ISimulatedSixDofController2
{
    /* New members in addition to those available on ISimulatedSixDofController */
    void GetThumbstickPosition(out float x, out float y);
    void SetThumbstickPosition(float x, float y);
    float BatteryLevel { get; set; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.GetThumbstickPosition(out float, out float)**

Abrufen der Position des simulierten Thumbsticks auf dem simulierten Controller.

Parameter
* x: Die horizontale Position des Fingerabdrucks.
* y: Die vertikale Position des Fingerabdrucks.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.SetThumbstickPosition(float, float)**

Legen Sie die Position des simulierten Fingerabdrucks auf dem simulierten Controller fest.

Parameter
* x: Die horizontale Position des Fingerabdrucks.
* y: Die vertikale Position des Fingerabdrucks.

**Microsoft.PerceptionSimulation.ISimulatedSixDofController2.BatteryLevel**

Ruft den Akkustand des simulierten Controllers ab oder legt diesen fest.  Der Wert muss größer als 0,0 und kleiner oder gleich 100,0 sein.


### <a name="microsoftperceptionsimulationisimulatedeyes"></a>Microsoft.PerceptionSimulation.ISimulatedEyes

Schnittstelle, die die Augen des simulierten Menschen beschreibt.

```
public interface ISimulatedEyes
{
    Rotation3 Rotation { get; set; }
    void Rotate(Rotation3 rotation);
    SimulatedEyesCalibrationState CalibrationState { get; set; }
    Vector3 WorldPosition { get; }
}
```

**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotation**

Rufen Sie die Drehung der simulierten Augen ab. Positive Bogenmaße drehen sich im Uhrzeigersinn, wenn Sie entlang der Achse suchen.

**Microsoft.PerceptionSimulation.ISimulatedEyes.Rotate(Microsoft.PerceptionSimulation.Rotation3)**

Drehen Sie die simulierten Augen relativ zur aktuellen Drehung. Positive Bogenmaße drehen sich im Uhrzeigersinn, wenn Sie entlang der Achse suchen.

Parameter
* rotation: Die Menge, die gedreht werden soll.

**Microsoft.PerceptionSimulation.ISimulatedEyes.CalibrationState**

Ruft den Kalibrierungszustand der simulierten Augen ab oder legt diesen fest.

**Microsoft.PerceptionSimulation.ISimulatedEyes.WorldPosition**

Ruft die Position des Knotens in Bezug auf die Welt in Metern ab.


### <a name="microsoftperceptionsimulationisimulationrecording"></a>Microsoft.PerceptionSimulation.ISimulationRecording

Schnittstelle für die Interaktion mit einer einzelnen Aufzeichnung, die für die Wiedergabe geladen wurde.

```
public interface ISimulationRecording
{
    StreamDataTypes DataTypes { get; }
    PlaybackState State { get; }
    void Play();
    void Pause();
    void Seek(UInt64 ticks);
    void Stop();
};
```

**Microsoft.PerceptionSimulation.ISimulationRecording.DataTypes**

Ruft die Liste der Datentypen in der Aufzeichnung ab.

**Microsoft.PerceptionSimulation.ISimulationRecording.State**

Ruft den aktuellen Zustand der Aufzeichnung ab.

**Microsoft.PerceptionSimulation.ISimulationRecording.Play**

Starten Sie die Wiedergabe. Wenn die Aufzeichnung angehalten wird, wird die Wiedergabe von der angehaltenen Position fortgesetzt. Wenn die Wiedergabe beendet wurde, wird die Wiedergabe am Anfang gestartet. Wenn dieser Aufruf bereits wiedergegeben wird, wird er ignoriert.

**Microsoft.PerceptionSimulation.ISimulationRecording.Pause**

Hält die Wiedergabe an der aktuellen Position an. Wenn die Aufzeichnung beendet wird, wird der Aufruf ignoriert.

**Microsoft.PerceptionSimulation.ISimulationRecording.Seek(System.UInt64)**

Sucht die Aufzeichnung bis zur angegebenen Zeit (in Intervallen von 100 Nanosekunden vom Anfang) und hält an dieser Position an. Wenn die Zeit über das Ende der Aufzeichnung hinausgeht, wird sie am letzten Frame angehalten.

Parameter
* ticks: Die Zeit, zu der gesucht werden soll.

**Microsoft.PerceptionSimulation.ISimulationRecording.Stop**

Beendet die Wiedergabe und setzt die Position auf den Anfang zurück.

### <a name="microsoftperceptionsimulationisimulationrecordingcallback"></a>Microsoft.PerceptionSimulation.ISimulationRecordingCallback

Schnittstelle zum Empfangen von Zustandsänderungen während der Wiedergabe.

```
public interface ISimulationRecordingCallback
{
    void PlaybackStateChanged(PlaybackState newState);
};
```

**Microsoft.PerceptionSimulation.ISimulationRecordingCallback.PlaybackStateChanged(Microsoft.PerceptionSimulation.PlaybackState)**

Wird aufgerufen, wenn sich der Wiedergabezustand eines ISimulationRecording geändert hat.

Parameter
* newState: Der neue Status der Aufzeichnung.

### <a name="microsoftperceptionsimulationperceptionsimulationmanager"></a>Microsoft.PerceptionSimulation.PerceptionSimulationManager

Stammobjekt zum Erstellen von Perception Simulation-Objekten.

```
public static class PerceptionSimulationManager
{
    public static IPerceptionSimulationManager CreatePerceptionSimulationManager(ISimulationStreamSink sink);
    public static ISimulationStreamSink CreatePerceptionSimulationRecording(string path);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory);
    public static ISimulationRecording LoadPerceptionSimulationRecording(string path, ISimulationStreamSinkFactory factory, ISimulationRecordingCallback callback);
```

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationManager(Microsoft.PerceptionSimulation.ISimulationStreamSink)**

Erstellen Sie für das -Objekt, um simulierte Pakete zu generieren und an die bereitgestellte Senke zu übermitteln.

Parameter
* sink: Die Senke, die alle generierten Pakete empfängt.

Rückgabewert

Der erstellte Manager.

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.CreatePerceptionSimulationRecording(System.String)**

Erstellen Sie eine Senke, in der alle empfangenen Pakete in einer Datei unter dem angegebenen Pfad gespeichert werden.

Parameter
* path: Der Pfad der zu erstellenden Datei.

Rückgabewert

Die erstellte Senke.

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory)**

Laden Sie eine Aufzeichnung aus der angegebenen Datei.

Parameter
* path: Der Pfad der zu ladenden Datei.
* factory: Eine Factory, die von der Aufzeichnung zum Erstellen eines ISimulationStreamSink verwendet wird, falls erforderlich.

Rückgabewert

Die geladene Aufzeichnung.

**Microsoft.PerceptionSimulation.PerceptionSimulationManager.LoadPerceptionSimulationRecording(System.String,Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory,Microsoft.PerceptionSimulation.ISimulationRecordingCallback)**

Laden Sie eine Aufzeichnung aus der angegebenen Datei.

Parameter
* path: Der Pfad der zu ladenden Datei.
* factory: Eine Factory, die von der Aufzeichnung zum Erstellen eines ISimulationStreamSink verwendet wird, falls erforderlich.
* callback: Ein Rückruf, der Updates empfängt, die den Status der Aufzeichnung umstufen.

Rückgabewert

Die geladene Aufzeichnung.

### <a name="microsoftperceptionsimulationstreamdatatypes"></a>Microsoft.PerceptionSimulation.StreamDataTypes

Beschreibt die verschiedenen Typen von Streamdaten.

```
public enum StreamDataTypes
{
    None = 0x00,
    Head = 0x01,
    Hands = 0x02,
    SpatialMapping = 0x08,
    Calibration = 0x10,
    Environment = 0x20,
    SixDofControllers = 0x40,
    Eyes = 0x80,
    DisplayConfiguration = 0x100
    All = None | Head | Hands | SpatialMapping | Calibration | Environment | SixDofControllers | Eyes | DisplayConfiguration
}
```

**Microsoft.PerceptionSimulation.StreamDataTypes.None**

Ein Sentinelwert, der verwendet wird, um anzugeben, dass keine Streamdatentypen vorhanden sind.

**Microsoft.PerceptionSimulation.StreamDataTypes.Head**

Datenstrom für die Position und Ausrichtung des Kopfes.

**Microsoft.PerceptionSimulation.StreamDataTypes.Hands**

Datenstrom für die Position und gesten der Hände.

**Microsoft.PerceptionSimulation.StreamDataTypes.SpatialMapping**

Datenstrom für die räumliche Zuordnung der Umgebung.

**Microsoft.PerceptionSimulation.StreamDataTypes.Calibration**

Datenstrom für die Kalibrierung des Geräts. Kalibrierungspakete werden nur von einem System im Remotemodus akzeptiert.

**Microsoft.PerceptionSimulation.StreamDataTypes.Environment**

Datenstrom für die Umgebung des Geräts.

**Microsoft.PerceptionSimulation.StreamDataTypes.SixDofControllers**

Datenstrom für Motion-Controller.

**Microsoft.PerceptionSimulation.StreamDataTypes.Eyes**

Datenstrom mit den Augen des simulierten Menschen.

**Microsoft.PerceptionSimulation.StreamDataTypes.DisplayConfiguration**

Datenstrom mit der Anzeigekonfiguration des Geräts.

**Microsoft.PerceptionSimulation.StreamDataTypes.All**

Ein Sentinelwert, der verwendet wird, um alle aufgezeichneten Datentypen anzugeben.

### <a name="microsoftperceptionsimulationisimulationstreamsink"></a>Microsoft.PerceptionSimulation.ISimulationStreamSink

Ein Objekt, das Datenpakete aus einem Simulationsstream empfängt.

```
public interface ISimulationStreamSink
{
    void OnPacketReceived(uint length, byte[] packet);
}
```

**Microsoft.PerceptionSimulation.ISimulationStreamSink.OnPacketReceived(uint length, byte[] packet)**

Empfängt ein einzelnes Paket, das intern typisiert und versioniert ist.

Parameter
* length: Die Länge des Pakets.
* packet: Die Daten des Pakets.

### <a name="microsoftperceptionsimulationisimulationstreamsinkfactory"></a>Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory

Ein Objekt, das ISimulationStreamSink erstellt.

```
public interface ISimulationStreamSinkFactory
{
    ISimulationStreamSink CreateSimulationStreamSink();
}
```

**Microsoft.PerceptionSimulation.ISimulationStreamSinkFactory.CreateSimulationStreamSink()**

Erstellt eine einzelne Instanz von ISimulationStreamSink.

Rückgabewert

Die erstellte Senke.
