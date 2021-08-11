---
title: MR Sharing 250 – HoloLens und immersive Headsets
description: Befolgen Sie diese exemplarische Codierungs-Vorgehensweise mit Unity Visual Studio, HoloLens und Windows Mixed Reality-Headsets, um mehr über die Freigabe von Hologrammen zwischen Mixed Reality-Geräten zu erfahren.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, immersive, motion controller, sharing, xbox controller, networking, cross-device
ms.openlocfilehash: 9f1b136193feefece3235d853503c05c69dbd451f9c2916fb178f1bcac0e3972
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208310"
---
# <a name="mr-sharing-250-hololens-and-immersive-headsets"></a>MR-Freigabe 250: HoloLens und immersive Headsets

>[!NOTE]
>Die Tutorials der Mixed Reality Academy wurden im Hinblick auf HoloLens (1. Gen.) und immersive Mixed Reality-Headsets entworfen.  Daher halten wir es für wichtig, diese Tutorials für Entwickler verfügbar zu halten, die noch nach Anleitung beim Entwickeln für diese Geräte suchen.  Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für HoloLens 2 verwendet werden.  Sie werden gewartet, um weiterhin auf den unterstützten Geräten zu funktionieren. [Es wurde eine neue Reihe von Tutorials](../develop/unity/tutorials/mr-learning-base-01.md) für HoloLens 2 veröffentlicht.

Mit der Flexibilität der universellen Windows-Plattform (UWP) ist es einfach, eine Anwendung zu erstellen, die mehrere Geräte umfasst. Mit dieser Flexibilität können wir Erfahrungen erstellen, die die Stärken der einzelnen Geräte nutzen. In diesem Tutorial wird eine grundlegende gemeinsame Umgebung für immersive Headsets HoloLens und Windows Mixed Reality verwendet. Dieser Inhalt wurde ursprünglich auf der Microsoft Build 2017-Konferenz in Seattle, WA bereitgestellt.

**In diesem Lernprogramm wird Folgendes beschrieben:**

* Richten Sie ein Netzwerk mit UNET ein.
* Teilen von Hologrammen auf Mixed Reality-Geräten
* Richten Sie eine andere Ansicht der Anwendung ein, je nachdem, welches Mixed Reality-Gerät verwendet wird.
* Erstellen Sie eine gemeinsame Umgebung, HoloLens Benutzer immersive Headsets durch einige einfacheZzer führen.

## <a name="device-support"></a>Geräteunterstützung

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../discover/immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td>MR-Freigabe 250: HoloLens und immersive Headsets</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Vorbereitung

### <a name="prerequisites"></a>Voraussetzungen

* Ein Windows 10 PC mit den [erforderlichen Entwicklungstools](../develop/install-the-tools.md) und konfiguriert, um ein Windows Mixed Reality [immersives Headset zu unterstützen.](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* Ein Xbox-Controller, der mit Ihrem PC funktioniert.
* Mindestens ein HoloLens gerät und ein immersives Headset.
* Ein Netzwerk, das die UDP-Übertragung für die Ermittlung zulässt.

### <a name="project-files"></a>Projektdateien

* Laden Sie [die für](https://github.com/Microsoft/MixedReality250/archive/master.zip) das Projekt erforderlichen Dateien herunter. Extrahieren Sie die Dateien an einem leicht zu merkenden Speicherort.
* Für dieses Projekt ist [eine empfohlene Version von Unity mit Unterstützung Windows Mixed Reality erforderlich.](../develop/install-the-tools.md)

>[!NOTE]
>Wenn Sie den Quellcode vor dem Herunterladen durchschauen möchten, ist er [auf GitHub.](https://github.com/Microsoft/MixedReality250)

## <a name="chapter-1---holo-world"></a>Kapitel 1 – Holo World

>[!VIDEO https://www.youtube.com/embed/IC0rp6rLiEc]

### <a name="objectives"></a>Ziele

Stellen Sie sicher, dass die Entwicklungsumgebung für ein einfaches Projekt bereit ist.

### <a name="what-we-will-build"></a>Was wir erstellen werden

Eine Anwendung, die ein Hologramm auf einem HoloLens oder einem Windows Mixed Reality immersives Headset zeigt.

### <a name="steps"></a>Schritte

* Öffnen Sie Unity.
    * Wähle **Öffnen** aus.
    * Navigieren Sie zu dem Ort, an dem Sie die Projektdateien extrahiert haben.
    * Klicken Sie auf **Ordner auswählen**.
    * *Es wird einige Zeit dauern, bis Unity das Projekt zum ersten Mal verarbeiten kann.*
* Überprüfen Sie, Mixed Reality in Unity aktiviert ist.
    * Öffnen Sie das Dialogfeld mit den Buildeinstellungen (**Control+SHIFT+B** **oder File > Build Einstellungen...**).
    * Wählen **Sie Universelle Windows Plattform aus,** und klicken Sie **dann auf Plattform wechseln.**
    * Wählen **Sie Bearbeiten>Player Einstellungen.**
    * Erweitern Sie **im Bereich** Inspektor auf der rechten Seite **XR-Einstellungen**.
    * Aktivieren Sie das **Kontrollkästchen Virtual Reality Unterstützt.**
    * *Windows Mixed Reality sollte das Virtual Reality SDK sein.*
* Erstellen Sie eine Szene.
    * Klicken Sie in der **Hierarchie mit** der rechten Maustaste **auf Hauptkamera,** und wählen **Sie Löschen aus.**
    * Ziehen **Sie aus HoloToolkit > Input > Prefabs** **MixedRealityCameraParent** in die **Hierarchie**.
* Hinzufügen Hologramme zur Szene
    * Ziehen Sie **skybox** **aus AppPrefabs** in die **Szenenansicht.**
    * Ziehen **Sie Manager aus AppPrefabs** **in** die **Hierarchie**.
    * Ziehen **Sie Island aus AppPrefabs** **in** die **Hierarchie**.
* Speichern und erstellen
    * Speichern (entweder **"Control+S"** oder **"File > Save Scene")**
    * Da es sich um eine neue Szene handelt, müssen Sie sie benennen. Der Name spielt keine Rolle, aber wir verwenden SharedMixedReality.
* Exportieren in Visual Studio
    * Öffnen Sie das Buildmenü (**Steuerung+UMSCHALT+B** oder **Datei > Build Einstellungen**)
    * Klicken Sie **auf Geöffnete Szenen hinzufügen.**
    * Überprüfen **von Unity C#-Projekten**
    * Klicken Sie auf **Erstellen**.
    * Erstellen Sie im angezeigten Datei-Explorer-Fenster einen neuen Ordner mit dem Namen **App**.
    * Klicken Sie mit nur einem Klick **auf den Ordner App.**
    * Klicken Sie **auf Ordner auswählen.**
    * **Warten Sie, bis der Build abgeschlossen ist.**
    * Navigieren Sie im angezeigten Datei-Explorer-Fenster zum **Ordner App.**
    * Doppelklicken Sie auf **SharedMixedReality.sln,** um die Visual Studio
* Erstellen aus Visual Studio
    * Ändern Sie über die obere Symbolleiste das **Ziel in Release** und **x86.**
    * Klicken Sie auf den Pfeil neben **Lokaler Computer,** und wählen Sie **Gerät aus,** das für die Bereitstellung HoloLens
    * Klicken Sie auf den Pfeil neben **Gerät,** und wählen **Sie Lokaler Computer aus,** der für das Mixed Reality-Headset bereitgestellt werden soll.
    * Klicken **Sie auf Debuggen->Ohne Debuggen starten** oder auf **Steuerelement+F5,** um die Anwendung zu starten.

### <a name="digging-into-the-code"></a>Tieferer Einblick in den Code

Navigieren Sie im Projektbereich zu **Assets\HoloToolkit\Input\Scripts\Utilities,** und doppelklicken Sie **auf MixedRealityCameraManager.cs,** um sie zu öffnen.

**Übersicht:** MixedRealityCameraManager.cs ist ein einfaches Skript, mit dem die Einstellungen für Qualitätsstufe und Hintergrund basierend auf dem Gerät angepasst werden. Der Schlüssel ist hier HolographicSettings.IsDisplayOpaque, mit dem ein Skript erkennen kann, ob das Gerät ein HoloLens (IsDisplayOpaque gibt FALSE zurück) oder ein immersives Headset (IsDisplayOpaque gibt TRUE zurück).

### <a name="enjoy-your-progress"></a>Viel Spaß beim Fortschritt

An diesem Punkt rendert die Anwendung nur ein Hologramm. Wir fügen dem Hologramm später eine Interaktion hinzu. Beide Geräte rendern das Hologramm gleich. Das immersive Headset rendert auch einen blauen Himmel und Einen Cloudhintergrund.

## <a name="chapter-2---interaction"></a>Kapitel 2: Interaktion

>[!VIDEO https://www.youtube.com/embed/Lrb1y4sQRvI]

### <a name="objectives"></a>Ziele

Zeigt, wie Eingaben für eine Windows Mixed Reality verarbeitet werden.

### <a name="what-we-will-build"></a>Was wir erstellen werden

Auf der Grundlage der Anwendung aus Kapitel 1 fügen wir Funktionen hinzu, mit denen der Benutzer das Hologramm auf einer realen Oberfläche in HoloLens oder auf einer virtuellen Tabelle in einem immersiven Headset platzieren kann.

**Eingabeaktualisierung:** Im HoloLens ist die Auswahlgeste die **Tippbewegung in die Luft.** Bei immersiven Headsets verwenden wir die **Schaltfläche A** auf dem Xbox-Controller. Weitere Informationen finden Sie in der Übersicht [über das Interaktionsmodell.](../design/interaction-fundamentals.md)

### <a name="steps"></a>Schritte

* Eingabe-Manager hinzufügen
    * Ziehen Sie **inputManager** **von HoloToolkit > Input > Prefabs** als untergeordnetes Element von **Managers** in **hierarchy** .
    * Ziehen Sie von **HoloToolkit > Input > Prefabs > Cursor** **Cursor** in **Hierarchy**.
* Hinzufügen der räumlichen Zuordnung
    * Ziehen Sie von **HoloToolkit > SpatialMapping > Prefabs** **SpatialMapping** in **Hierarchy**.
* Hinzufügen eines virtuellen Playspace
    * Erweitern Sie unter **Hierarchie** die Option **MixedRealityCameraParent,** und wählen Sie **Grenze** aus.
    * Aktivieren Sie im Bereich **Inspector (Inspektor)** das Kontrollkästchen , um **Boundary (Grenze)** zu aktivieren.
    * Ziehen Sie **VRRoom** aus **AppPrefabs** in **Hierarchy**.
* Hinzufügen von WorldAnchorManager
    * Wählen Sie **in hierarchie** die Option **Manager** aus.
    * Klicken Sie im **Inspektor** auf **Komponente hinzufügen.**
    * Geben Sie **World Anchor Manager** ein.
    * Wählen Sie **World Anchor Manager** aus, um ihn hinzuzufügen.
* Hinzufügen von TapToPlace zur Island
    * Erweitern **Sie unter Hierarchie** den Bereich **Island**.
    * Wählen Sie **MixedRealityLand** aus.
    * Klicken Sie im **Inspektor** auf **Komponente hinzufügen.**
    * Geben **Sie Tippen Sie auf An Ort,** und wählen Sie ihn aus.
    * Aktivieren Sie **übergeordnetes Element bei Tippen auf**.
    * Legen Sie **Platzierungsoffset** auf **(0, 0,1, 0)** fest.
* Speichern und Erstellen wie zuvor

### <a name="digging-into-the-code"></a>Untersuchen des Codes

**Skript 1: GamepadInput.cs**

Navigieren Sie im Projektbereich zu **Assets\HoloToolkit\Input\Scripts\InputSources,** und doppelklicken Sie auf **GamepadInput.cs,** um es zu öffnen. Doppelklicken Sie im Projektbereich unter demselben Pfad auch auf **InteractionSourceInputSource.cs.**

Beachten Sie, dass beide Skripts über eine gemeinsame Basisklasse, BaseInputSource, verfügen.

BaseInputSource behält einen Verweis auf einen InputManager bei, der es einem Skript ermöglicht, Ereignisse auszulösen. In diesem Fall ist das InputClicked-Ereignis relevant. Dies ist wichtig zu beachten, wenn wir skript 2, TapToPlace, erstellen. Im Fall von GamePadInput wird abgefragt, ob die Schaltfläche A auf dem Controller gedrückt wird, und dann wird das InputClicked-Ereignis ausgelöst. Im Fall von InteractionSourceInputSource wird das InputClicked-Ereignis als Reaktion auf das TappedEvent ausgelöst.

**Skript 2: TapToPlace.cs**

Navigieren Sie im Projektbereich zu **Assets\HoloToolkit\SpatialMapping\Scripts,** und doppelklicken Sie auf **TapToPlace.cs,** um sie zu öffnen.

Das erste, was viele Entwickler beim Erstellen einer Holographic-Anwendung implementieren möchten, ist das Verschieben Hologramme mit Gesteneingabe. Daher haben wir versucht, dieses Skript gründlich zu kommentieren. Für dieses Tutorial sind einige Punkte hervorzuheben.

Beachten Sie zunächst, dass TapToPlace IInputClickHandler implementiert. IInputClickHandler macht die Funktionen verfügbar, die das von GamePadInput.cs oder InteractionSourceInputSource.cs ausgelöste InputClicked-Ereignis behandeln. OnInputClicked wird aufgerufen, wenn eine BaseInputSource einen Klick erkennt, während sich das Objekt mit TapToPlace im Fokus befindet. Wenn Sie auf HoloLens airtapping oder auf die Taste A auf dem Xbox-Controller klicken, wird das Ereignis ausgelöst.

Zweitens wird der Code im Update ausgeführt, um festzustellen, ob eine Oberfläche untersucht wird, damit wir das Spielobjekt auf einer Oberfläche wie einer Tabelle platzieren können. Das immersive Headset verfügt nicht über ein Konzept von realen Oberflächen, sodass das Objekt, das die Tabellenspitze darstellt (Vroom > TableThingy > Cube), mit der SpatialMapping-Physikalischen Schicht markiert wurde, sodass die Raycast in Update mit der obersten Ebene der virtuellen Tabelle kollidiert.

### <a name="enjoy-your-progress"></a>Viel Spaß beim Fortschritt

Dieses Mal können Sie die Inseln auswählen, um sie zu verschieben. Auf HoloLens können Sie die Inseln auf eine echte Oberfläche verschieben. Im immersiven Headset können Sie die Inseln in die virtuelle Tabelle verschieben, die wir hinzugefügt haben.

## <a name="chapter-3---sharing"></a>Kapitel 3: Freigeben

>[!VIDEO https://www.youtube.com/embed/1diycJvxfDc]

### <a name="objectives"></a>Ziele

Stellen Sie sicher, dass das Netzwerk ordnungsgemäß konfiguriert ist, und geben Sie an, wie Raumanker von Geräten gemeinsam genutzt werden.

### <a name="what-we-will-build"></a>Was wir erstellen werden

Wir konvertieren unser Projekt in ein Multiplayer-Projekt. Wir fügen Benutzeroberfläche und Logik zum Hosten oder Beitreten zu Sitzungen hinzu. HoloLens Benutzer einander in der Sitzung mit Clouds über dem Kopf sehen, und Benutzer mit immersiven Headsets haben Clouds in der Nähe des Ankers. Benutzer in den immersiven Headsets sehen die HoloLens Benutzer relativ zum Ursprung der Szene. HoloLens Benutzer sehen alle das Hologramm der Inseln an derselben Stelle. Es ist wichtig zu beachten, dass sich die Benutzer in den immersiven Headsets während dieses Kapitels nicht auf der Inseln befinden, sondern sich sehr ähnlich wie HoloLens verhalten, mit einem blickreichen Blick auf die Inseln.

### <a name="steps"></a>Schritte

* Entfernen von Island und VRRoom
    * Klicken Sie **in Hierarchie** mit der rechten Maustaste auf **Island,** und wählen Sie **Löschen** aus.
    * Klicken Sie **in Hierarchie** mit der rechten Maustaste auf **VRRoom,** und wählen Sie **Löschen** aus.
* Hinzufügen von Usland
    * Ziehen Sie **usland** aus **AppPrefabs** in **Hierarchy**.
* Ziehen Sie aus **AppPrefabs** die folgenden Werte in **die Hierarchie**:
    * **UNETSharingStage**
    * **UNetAnchorRoot**
    * **UIContainer**
    * **DebugPanelButton**
* Speichern und Erstellen wie zuvor

### <a name="digging-into-the-code"></a>Untersuchen des Codes

Navigieren Sie im Projektbereich zu **Assets\AppPrefabs\Support\SharingWithUnet\Scripts,** und doppelklicken Sie auf **UnetAnchorManager.cs**. Die Möglichkeit, dass eine HoloLens Nachverfolgungsinformationen mit einem anderen HoloLens freigeben kann, sodass beide Geräte denselben Platz gemeinsam nutzen können, ist nahezu mager. Die Leistungsfähigkeit von Mixed Reality wird erfüllt, wenn zwei oder mehr Personen mit denselben digitalen Daten zusammenarbeiten können.

In diesem Skript sind einige Punkte zu nennen:

Beachten Sie in der Startfunktion die Überprüfung auf **IsDisplayOpaque**. In diesem Fall wird vorausgesetzt, dass der Anker eingerichtet ist. Dies liegt daran, dass die immersiven Headsets keine Möglichkeit zum Importieren oder Exportieren von Ankern verfügbar machen. Wenn wir jedoch auf einem HoloLens ausführen, implementiert dieses Skript Freigabeanker zwischen den Geräten. Das Gerät, das die Sitzung startet, erstellt einen Anker für den Export. Das Gerät, das einer Sitzung beitritt, fordert den Anker vom Gerät an, das die Sitzung gestartet hat.

**Exportieren:**

Wenn ein Benutzer eine Sitzung erstellt, ruft NetworkDiscoveryWithAnchors die CreateAnchor-Funktion UNETAnchorManagers auf. Wir folgen dem CreateAnchor-Flow.

Wir beginnen damit, eine Gewisse Bereinigung durchzuführen und alle Daten zu löschen, die wir möglicherweise für vorherige Anker gesammelt haben. Anschließend überprüfen wir, ob ein zwischengespeicherter Anker geladen werden soll. Die Ankerdaten liegen in der Regel zwischen 5 und 20 MB, sodass durch die Wiederverwendung von zwischengespeicherten Ankern die Datenmenge, die wir über das Netzwerk übertragen müssen, gespart werden kann. Wir werden später sehen, wie dies funktioniert. Auch wenn wir den Anker wiederverwenden, müssen wir die Ankerdaten bereit machen, falls ein neuer Client beitritt, der den Anker nicht enthält.

Die WorldAnchorTransferBatch-Klasse stellt die Funktionalität zum Vorbereiten von Ankerdaten für das Senden an ein anderes Gerät oder eine andere Anwendung und die Funktionalität zum Importieren der Ankerdaten zur Verfügung, um die Ankerdaten vorzubereiten. Da wir uns im Exportpfad befinden, fügen wir unseren Anker dem WorldAnchorTransferBatch hinzu und rufen die ExportAsync-Funktion auf. ExportAsync ruft dann den WriteBuffer-Rückruf auf, während Daten für den Export generiert werden. Wenn alle Daten exportiert wurden, wird ExportComplete aufgerufen. In WriteBuffer fügen wir den Datenabschnitt einer Liste hinzu, die wir zum Exportieren beibehalten. In ExportComplete konvertieren wir die Liste in ein Array. Die AnchorName-Variable ist ebenfalls festgelegt, wodurch andere Geräte ausgelöst werden, den Anker anzufordern, wenn sie ihn nicht haben.

In einigen Fällen exportiert der Anker nicht oder erstellt so wenig Daten, dass wir es erneut versuchen. Hier rufen wir einfach erneut CreateAnchor auf.

Eine letzte Funktion im Exportpfad ist AnchorFoundRemotely. Wenn ein anderes Gerät den Anker findet, teilt dieses Gerät dem Host mit, und der Host verwendet dies als Signal, dass der Anker ein "guter Anker" ist und zwischengespeichert werden kann.

**Importieren:**

Wenn ein HoloLens einer Sitzung beitritt, muss ein Anker importiert werden. In der Update-Funktion von UNETAnchorManager wird anchorName abgefragt. Wenn sich der Ankername ändert, beginnt der Importvorgang. Zunächst versuchen wir, den Anker mit dem angegebenen Namen aus dem lokalen Ankerspeicher zu laden. Wenn sie bereits vorhanden ist, können wir sie verwenden, ohne die Daten erneut herunterzuladen. Wenn sie nicht verfügbar ist, rufen wir WaitForAnchor auf, um den Download zu initiieren.

Nach Abschluss des Downloads wird NetworkTransmitter_dataReadyEvent aufgerufen. Dadurch wird die Update-Schleife signalisiert, importAsync mit den heruntergeladenen Daten aufzurufen. ImportAsync ruft ImportComplete auf, wenn der Importvorgang abgeschlossen ist. Wenn der Import erfolgreich war, wird der Anker im lokalen Playerspeicher gespeichert. PlayerController.cs ruft anchorFoundRemotely tatsächlich auf, um den Host darüber zu informieren, dass ein guter Anker eingerichtet wurde.

### <a name="enjoy-your-progress"></a>Viel Spaß bei Ihrem Fortschritt

Dieses Mal hosten Benutzer mit einem HoloLens eine Sitzung mithilfe der Schaltfläche **Sitzung starten** in der Benutzeroberfläche. Andere Benutzer, sowohl auf HoloLens als auch auf einem immersiven Headset, wählen die Sitzung und dann die Schaltfläche **Sitzung beitreten** in der Benutzeroberfläche aus. Wenn Sie über mehrere Personen mit HoloLens Geräten verfügen, haben sie rote Clouds auf dem Kopf. Es wird auch eine blaue Cloud für jedes immersive Headset geben, aber die blauen Clouds befinden sich nicht über den Headsets, da die Headsets nicht versuchen, den gleichen Koordinatenraum wie die HoloLens Geräte zu finden.

Dieser Punkt im Projekt ist eine eigenständige Freigabeanwendung. dies ist nicht sehr wichtig und kann als Baseline fungieren. In den nächsten Kapiteln beginnen wir damit, eine Benutzeroberfläche zu erstellen, die den Menschen gefällt. Weitere Informationen zum Entwurf der gemeinsamen Benutzeroberfläche finden Sie hier.

## <a name="chapter-4---immersion-and-teleporting"></a>Kapitel 4: Immersion und Teleportierung

>[!VIDEO https://www.youtube.com/embed/kUHZ5tCOfvY]

### <a name="objectives"></a>Ziele

Berücksichtigen Sie die Erfahrung für jede Art von Mixed Reality-Gerät.

### <a name="what-we-will-build"></a>Was wir erstellen werden

Wir aktualisieren die Anwendung, um Immersive Headset-Benutzer mit einer immersiven Ansicht auf der Inseln zu installieren. HoloLens Benutzer haben weiterhin die Vogelperspektive auf die Inseln. Benutzer jedes Gerätetyps können andere Benutzer sehen, wie sie auf der Ganzen Welt angezeigt werden. Beispielsweise können Benutzer des immersiven Headsets die anderen Avatare auf anderen Pfaden auf der Inseln sehen, und sie sehen die HoloLens Benutzer als riesige Clouds oberhalb der Inseln. Benutzer des immersiven Headsets sehen auch den Cursor des Anvischer-Strahls des HoloLens Benutzers, wenn der HoloLens Benutzer die Inseln ansieht. HoloLens Benutzer sehen einen Avatar auf der Inseln, um jeden Benutzer des immersiven Headsets darzustellen.

**Aktualisierte Eingabe für das immersive Gerät:**

* Die Schaltflächen "Left Bumper" und "right bumper" auf dem Xbox-Controller drehen den Player
* Wenn Sie die Y-Schaltfläche auf dem Xbox-Controller gedrückt halten, wird ein [Teleportcursor](../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) aktiviert. Wenn der Cursor beim Loslassen der Y-Schaltfläche über einen rotierenden Pfeilindikator verfügt, werden Sie an die Position des Cursors teleportiert.

### <a name="steps"></a>Schritte

* Hinzufügen von MixedRealityTeleport zu MixedRealityCameraParent
    * Wählen Sie unter **Hierarchie** die Option **Usland** aus.
    * Aktivieren Sie im **Inspektor** **die Ebenensteuerung**.
    * Wählen Sie unter **Hierarchie** die Option **MixedRealityCameraParent** aus.
    * Klicken Sie im **Inspektor** auf **Komponente hinzufügen.**
    * Geben Sie **Mixed Reality Teleport ein,** und wählen Sie ihn aus.

### <a name="digging-into-the-code"></a>Untersuchen des Codes

Benutzer des immersiven Headsets werden mit einem Kabel mit ihren PCs verbunden, aber unsere Inseln sind größer als das Kabel lang. Um dies zu kompensieren, benötigen wir die Möglichkeit, die Kamera unabhängig von der Bewegung des Benutzers zu bewegen. Weitere Informationen zum Entwerfen Ihrer Mixed Reality-Anwendung (insbesondere Selbstbewegung und Bewegung) finden Sie auf der [Komfortseite.](../design/comfort.md)

Um diesen Prozess zu beschreiben, ist es hilfreich, zwei Begriffe zu definieren. Erstens ist **dies** das Objekt, das die Kamera unabhängig vom Benutzer bewegt. Ein untergeordnetes Spielobjekt des **-Objekts** wird die **Hauptkamera** sein. Die Hauptkamera wird am Kopf des Benutzers angefügt.

Navigieren Sie im Projektbereich zu **Assets\AppPrefabs\Support\Scripts\GameLogic,** und doppelklicken Sie auf **MixedRealityTeleport.cs.**

MixedRealityTeleport verfügt über zwei Aufträge. Zuerst wird die Drehung mithilfe der Ziehpunkte verarbeitet. In der Updatefunktion wird "ButtonUp" für LeftBumper und RightBumper abgefragt. GetButtonUp gibt nur true für den ersten Frame zurück, in dem sich eine Schaltfläche nach dem Heruntersennen befindet. Wenn eine der Schaltflächen ausgelöst wurde, wissen wir, dass der Benutzer rotieren muss.

Beim Drehen wird ein Ausblenden und Einblenden mithilfe eines einfachen Skripts namens "Fade Control" durchgeführt. Dadurch wird verhindert, dass der Benutzer eine unnatürliche Bewegung sieht, die zu Störungen führen kann. Der Ein- und Ausblenden-Effekt ist recht einfach. Vor der **Hauptkamera** hängt ein schwarzes Quader. Beim Ausblenden geht der Alphawert von 0 in 1 über. Dadurch werden die schwarzen Pixel des Quaders nach und nach gerendert und verborgen. Beim Einblenden in wird der Alphawert wieder auf 0 (null) zurückgesetzt.

Wenn wir die Drehung berechnen, beachten Sie, dass wir unsere **Drehung** drehen, aber die Drehung um die **Hauptkamera** berechnen. Dies ist wichtig, da je weiter die **Hauptkamera** von 0,0,0 entfernt ist, desto weniger genau würde eine Drehung um die Oberfläche aus Sicht des Benutzers werden. Wenn Sie sich nicht um die Kameraposition drehen, bewegt sich der Benutzer auf einem Bogen um die **Kurve,** anstatt sich zu drehen.

Der zweite Auftrag für MixedRealityTeleport besteht darin, das Verschieben des **Ziehpunkts** zu verarbeiten. Dies erfolgt in SetWorldPosition. SetWorldPosition nimmt die gewünschte Weltposition an, also die Position, an der der Benutzer die Freundlichkeit ergehen lassen möchte. Wir müssen unseren **Bogen** an dieser Position abzüglich der lokalen Position der **Hauptkamera** setzen, da dieser Offset jedem Frame hinzugefügt wird.

Ein zweites Skript ruft SetWorldPosition auf. Sehen wir uns dieses Skript an. Navigieren Sie im Projektbereich zu **Assets\AppPrefabs\Support\Scripts\GameLogic,** und doppelklicken Sie auf **TeleportScript.cs.**

Dieses Skript ist etwas komplexer als MixedRealityTeleport. Das Skript überprüft, ob die Y-Schaltfläche auf dem Xbox-Controller gedrückt gehalten wird. Während die Schaltfläche gedrückt gehalten wird, wird ein Teleportcursor gerendert, und das Skript umgibt einen Strahl aus der Anviertposition des Benutzers. Wenn dieser Strahl mit einer Oberfläche kollidiert, die mehr oder weniger nach oben verweist, wird die Oberfläche als gute Oberfläche für das Teleport betrachtet, und die Animation auf dem Teleportcursor wird aktiviert. Wenn der Strahl nicht mit einer Oberfläche kollidiert, die mehr oder weniger nach oben verweist, wird die Animation auf dem Cursor deaktiviert. Wenn die Y-Schaltfläche losgelassen wird und der berechnete Punkt des Strahls eine gültige Position ist, ruft das Skript SetWorldPosition mit der Position auf, an der sich der Strahl überschneidet.

### <a name="enjoy-your-progress"></a>Viel Spaß bei Ihrem Fortschritt

Dieses Mal müssen Sie einen Freund finden.

Auch hier hosten Benutzer mit dem HoloLens eine Sitzung. Andere Benutzer treten der Sitzung bei. Die Anwendung platzieren die ersten drei Benutzer, die über ein immersives Headset an einem der drei Pfade auf der Inseln teilnehmen. In diesem Abschnitt können Sie die Inseln erkunden.

Zu beachtende Details:

1. Sie können Gesichter in den Clouds sehen, wodurch ein erfahrener Benutzer erkennen kann, in welche Richtung ein HoloLens Benutzer sucht.
2. Die Avatare auf der Inseln verfügen über Hänge, die sich drehen. Sie folgen nicht dem, was der Benutzer in der realen Realität tut (wir haben diese Informationen nicht), aber dies sorgt für eine gute Erfahrung.
3. Wenn sich der HoloLens Benutzer die Island ansieht, können die gesuchten Benutzer ihren Cursor sehen.
4. Die Clouds, die die HoloLens Benutzer darstellen, werfen Schatten.

## <a name="chapter-5---finale"></a>Kapitel 5 – Finale

>[!VIDEO https://www.youtube.com/embed/n_HDWJbfpNg]

### <a name="objectives"></a>Ziele

Erstellen Sie eine interaktive Umgebung für die Zusammenarbeit zwischen den beiden Gerätetypen.

### <a name="what-we-will-build"></a>Was wir erstellen werden

Wenn sich ein Benutzer mit einem immersiven Headset in der Nähe eines Wunders auf der Inseln befindet, erhalten die HoloLens Benutzer nach Kapitel 4 einen QuickInfo mit einem Hinweis auf das Wunder. Sobald alle Benutzer des immersiven Headsets an ihren Wundern und auf dem "bereiten Pad" im Raketenraum vorbeikommen, wird die Rakete gestartet.

### <a name="steps"></a>Schritte

* Wählen Sie unter **Hierarchie** die Option **Usland** aus.
* Aktivieren Sie im **Inspektor** unter **Ebenensteuerung** die **Option Zusammenarbeit aktivieren.**

### <a name="digging-into-the-code"></a>Untersuchen des Codes

Sehen wir uns nun LevelControl.cs an. Dieses Skript ist der Kern der Spiellogik und verwaltet den Spielzustand. Da es sich um ein Multiplayer-Spiel mit UNET handelt, müssen wir verstehen, wie Daten fließen, zumindest gut genug, um dieses Tutorial zu ändern. Eine umfassendere Übersicht über UNET finden Sie in der Unity-Dokumentation.

Navigieren Sie im Projektbereich zu **Assets\AppPrefabs\Support\Scripts\GameLogic,** und doppelklicken Sie auf **LevelControl.cs.**

Lassen Sie uns verstehen, wie ein immersives Headset angibt, dass es für den Raketenstart bereit ist. Die Bereitschaft des Raketenstarts wird kommuniziert, indem einer von drei Booleschen in einer Liste von Booleschen Pfaden festgelegt wird, die den drei Pfaden auf der Inseln entsprechen. Der Bool eines Pfads wird festgelegt, wenn sich der dem Pfad zugewiesene Benutzer auf dem brownen Pad im Raketenraum befindet. Ok, jetzt zu den Details.

Wir beginnen mit der Update()-Funktion. Sie werden feststellen, dass es eine Cheat-Funktion gibt. Wir haben dies in der Entwicklung verwendet, um den Raketenstart zu testen und die Sequenz zurückzusetzen. Dies funktioniert in der Benutzeroberfläche für mehrere Benutzer nicht. Wenn Sie die folgenden Informationen internalisieren, können Sie dies hoffen, dass sie funktioniert. Nachdem wir uns vergewissert haben, ob wir spicken sollten, überprüfen wir, ob der lokale Spieler entgangen ist. Wir möchten uns darauf konzentrieren, wie wir das Ziel erreichen. Innerhalb der If-Überprüfung (1000) wird CheckGoal aufgerufen, der sich hinter dem **Bool EnableCollaboration** verbirgt. Dies entspricht dem Kontrollkästchen, das Sie beim Ausführen der Schritte für dieses Kapitel aktiviert haben. In EnableCollaboration sehen wir einen Aufruf von CheckGoal().

CheckGoal führt mathematische Berechnungen durch, um festzustellen, ob wir mehr oder weniger auf dem Pad stehen. In diesem Beispiel rufen wir Debug.Log "Arrived at goal" (Beim Ziel empfangen) und dann "SendAtGoalMessage()" auf. In SendAtGoalMessage rufen wir playerController.SendAtGoal auf. Um Zeit zu sparen, sehen Sie sich den folgenden Code an:

```cs
private void CmdSendAtGoal(int GoalIndex)
{
    levelState.SetGoalIndex(GoalIndex);
}
```

```cs
public void SendAtGoal(int GoalIndex)
{
    if (isLocalPlayer)
    {
        Debug.Log("sending at goal " + GoalIndex);
        CmdSendAtGoal(GoalIndex);
    }
}
```

Beachten Sie, dass SendAtGoalMessage CmdSendAtGoal aufruft, das levelState.SetGoalIndex aufruft, das sich wieder in LevelControl.cs befindet. Auf den ersten Blick erscheint dies ungewöhnlich. Warum rufen Sie nicht nur SetGoalIndex statt dieses ungewöhnliche Routing über den Playercontroller auf? Der Grund dafür ist, dass wir dem Datenmodell entsprechen, das UNET verwendet, um Daten synchron zu halten. Um Betrug und Thrashing zu verhindern, erfordert UNET, dass jedes Objekt über einen Benutzer verfügt, der über die Berechtigung zum Ändern der synchronisierten Variablen verfügt. Darüber hinaus kann nur der Host (der Benutzer, der die Sitzung gestartet hat) Daten direkt ändern. Benutzer, die nicht der Host sind, aber über Die Autorität verfügen, müssen einen Befehl an den Host senden, der die Variable ändert. Standardmäßig verfügt der Host über autoritätsüber alle Objekte, mit Ausnahme des Objekts, das zur Darstellung des Benutzers ausgelöst wurde. In unserem Fall verfügt dieses Objekt über das playercontroller-Skript. Es gibt eine Möglichkeit, eine Autorität für ein Objekt anzufordern und dann Änderungen vorzunehmen, aber wir entscheiden uns dafür, die Tatsache zu nutzen, dass der Playercontroller über eine eigene Autorität verfügt und Befehle über den Playercontroller weiterleitet.

Anders gesagt: Wenn wir uns bei unserem Ziel befinden, muss der Spieler den Host informieren, und der Host teilt allen anderen mit.

Zurück in LevelControl.cs sehen Sie sich SetGoalIndex an. Hier legen wir den Wert eines Werts in einer Synchronisierungsliste (AtGoal) fest. Denken Sie daran, dass wir uns dabei im Kontext des Hosts befinden. Ähnlich wie bei einem Befehl kann ein RPC vom Host ausgegeben werden, was dazu führt, dass alle Clients Code ausführen. Hier wird "RpcCheckAllGoals" aufgerufen. Jeder Client überprüft einzeln, ob alle drei AtGoals festgelegt sind, und wenn ja, starten Sie die Rakete.

### <a name="enjoy-your-progress"></a>Viel Spaß beim Fortschritt

Auf der Grundlage des vorherigen Kapitels starten wir die Sitzung wie zuvor. Dieses Mal, wenn die Benutzer im immersiven Headset die "Tür" auf ihrem Pfad erreichen, wird eine QuickInfo angezeigt, die nur die HoloLens Benutzer sehen können. Die HoloLens Benutzer sind für die Kommunikation dieser Hinweise mit den Benutzern im immersiven Headset verantwortlich. Die Rakete wird in den Weltraum gestartet, sobald jeder Avatar auf dem entsprechenden brownen Pad innerhalb des Vulkans abgestuft wurde. Die Szene wird nach 60 Sekunden zurückgesetzt, damit Sie sie erneut durchführen können.

## <a name="see-also"></a>Siehe auch

* [MR-Eingabe 213: Motion-Controller](mixed-reality-213.md)