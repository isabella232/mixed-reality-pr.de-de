---
title: Navigieren auf der Startseite von Windows Mixed Reality
description: Hier erfahren Sie, wie Sie Windows Mixed Reality zu Hause HoloLens und Windows Mixed Reality Headsets navigieren.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Shell, Betriebssystem, Plattform, Haus, Umgebung, Start, Startmenü, Startmenü, Stecknadeln, App, Apps starten, Apps platzieren, Teleport, Verschieben, Navigieren, Mixed Reality-Headset, Virtual Reality-Headset, Was ist virtuelle Realität?
ms.openlocfilehash: 39ca5e974e242019d7eb14fba0362151213c6558cce7f13328390712b3642901
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190272"
---
# <a name="navigating-the-windows-mixed-reality-home"></a>Navigieren auf der Startseite von Windows Mixed Reality

Genau wie die Windows pc-Erfahrung mit dem Desktop beginnt, Windows Mixed Reality mit der Startseite. Das Windows Mixed Reality verwendet unsere eigene Fähigkeit, 3D-Orte zu verstehen und zu navigieren. Mit HoloLens ist Ihr Haus Ihr physischer Raum, aber mit immersiven Headsets ist Ihr Haus ein virtueller Ort.

In Ihrer Startseite verwenden Sie auch die Startmenü, um Apps und Inhalte zu öffnen und zu platzieren. Sie können Ihr Haus mit Mixed Reality-Inhalten und Multitasks füllen, indem Sie mehrere Apps gleichzeitig verwenden. Die Dinge, die Sie in Ihrem Haus platzieren, bleiben dort, auch wenn Sie Ihr Gerät neu starten.

## <a name="start-menu"></a>Startmenü

![Startmenü auf Microsoft HoloLens](images/start-500px.png)

Die Startmenü besteht aus:
* Systeminformationen (Netzwerkstatus, Akkuprozentsatz, aktuelle Zeit und Volumen)
* Cortana (auf immersiven Headsets, eine Startkachel; HoloLens, oben in Start)
* Angeheftete Apps
* Schaltfläche Alle Apps (Pluszeichen)
* Foto- und Videoschaltflächen für [die Mixed Reality-Aufnahme](/hololens/holographic-photos-and-videos)

Wechseln Sie zwischen den angeheftete Apps und Alle Apps, indem Sie die Plus- oder Minusschaltflächen auswählen. Um die Startmenü auf HoloLens öffnen, verwenden Sie die Blumengeste. Drücken Sie auf einem immersiven Headset die Windows des Controllers.

## <a name="launching-apps"></a>Starten von Apps

Um eine App zu starten, wählen Sie sie auf Starten aus. Der Startmenü wird nicht mehr angezeigt, und die App wird im Platzierungsmodus geöffnet, entweder als 2D-Fenster oder [als 3D-Modell.](../distribute/implementing-3d-app-launchers.md)

Um die App ausführen zu können, müssen Sie sie in Ihrer Startseite platzieren:
1. Verwenden Sie Ihren [Anving](../design/gaze-and-commit.md) oder Controller, um die App dort zu positionieren, wo Sie sie möchten. Es wird automatisch angepasst (in Größe und Position), um dem Raum zu entsprechen, in dem Sie ihn platzieren.
2. Platzieren Sie die App per Tippen in die Luft (HoloLens) oder über die Schaltfläche Auswählen (immersive Headsets). Um den Vorgang abzubricht und Startmenü, verwenden Sie die Blumengeste oder Windows Schaltfläche.

[2D-Apps,](../develop/porting-apps/building-2d-apps.md)die für Desktop, mobilgeräte oder Xbox erstellt wurden, können mithilfe der [HolographicSpace-API](/uwp/api/Windows.Graphics.Holographic.HolographicSpace)so geändert werden, dass sie als immersive Mixed Reality-Apps ausgeführt werden. Eine immersive App führt den Benutzer aus der Startseite in eine immersive Umgebung. Benutzer können mit der Blumengeste (HoloLens) oder durch Drücken der Windows taste auf ihrem Controller (immersive Headsets) nach Hause zurückkehren.

Apps können auch über eine App-zu-App-API oder über Cortana.

![Apps im Windows Mixed Reality Start](images/mixed-reality-home-500px.png)

## <a name="moving-and-adjusting-apps"></a>Verschieben und Anpassen von Apps

Wählen **Sie auf** der App-Leiste Anpassen aus, um Steuerelemente anzuzeigen, die Mixed Reality-Inhalte verschieben, skalieren und drehen. Wenn Sie fertig sind, wählen Sie **Fertig aus.**

![Die Store-Slate im Anpassungsmodus (blauer Rahmen). Beachten Sie, dass sich die App-Leiste (oben) so geändert hat, dass sie die Schaltflächen "Fertig" und "Entfernen" enthält.](images/adjust-500px.png)

Verschiedene Apps haben möglicherweise andere Optionen auf der App-Leiste. Beispielsweise verfügt Microsoft Edge über die *Optionen Scrollen,* *Ziehen* und *Zoomen.* 

![App-Leiste für 2D-Apps, die auf HoloLens](images/holobar-500px.png)

Die **Schaltfläche Zurück** navigiert zurück zu den zuvor angezeigten Bildschirmen in der App. Sie wird nicht mehr angezeigt, wenn Sie den Anfang der in der App angezeigten Beerlebnisse erreichen und nicht zu anderen Apps navigieren.

## <a name="getting-around-your-home"></a>Auf dem Weg zu Hause

Mit **HoloLens** bewegen Sie sich durch den physischen Raum, um sich in Ihrem Haus zu bewegen.

Mit **immersiven Headsets** können Sie sich in Ihrem Playspace in einem ähnlichen Bereich in der virtuellen Welt bewegen. Um längere Entfernungen zu verlassen, verwenden Sie den Fingerabdruck auf Ihrem Controller, um praktisch zu "laufen", oder Sie können die *Teleportation* verwenden, um sofort längere Entfernungen zu springen.

![Teleportation im Windows Mixed Reality](images/teleportation-500px.png)

**So teleportieren Sie:**
1. Bringen Sie die Teleportation reticle (Teleportation reticle) auf.
   * Verwenden [von Motion-Controllern:](../design/motion-controllers.md)Drücken Sie den Stick nach vorn, und halten Sie ihn an dieser Position.
   * Verwenden eines Xbox-Controllers: Drücken Sie den linken Fingerabdruck nach vorn, und halten Sie ihn an dieser Position.
   * Verwenden einer Maus: Halten Sie die Maustaste mit der rechten Maustaste gedrückt (und verwenden Sie das Scrollrad, um die Richtung zu drehen, die Sie beim Teleportieren sehen möchten).
2. Platzieren Sie das Reticle an der Stelle, an der Sie teleportieren möchten.
   * Verwenden [von Motion-Controllern:](../design/motion-controllers.md)Kippen Sie den Controller (auf dem Sie den Stick nach vorn halten), um das Reticle zu verschieben.
   * Verwenden eines Xbox-Controllers: Verwenden Sie Ihren [Blick,](../design/gaze-and-commit.md) um das Reticle zu verschieben.
   * Verwenden einer Maus: Bewegen Sie die Maus, um das Reticle zu verschieben.
3. Lassen Sie die Schaltfläche los, um den Teleport an der Stelle zu senden, an der das Reticle platziert wurde.

**So gehen Sie praktisch "walk:"**
* Verwenden [von Motion-Controllern:](../design/motion-controllers.md)Klicken Sie nach unten auf den Stick, halten Sie ihn, und bewegen Sie den Thumbstick dann in die Richtung, die Sie "walk" (Gehen) möchten.
* Verwenden eines Xbox-Controllers: Klicken Sie nach unten auf den linken Fingerabdruck, halten Sie ihn, und bewegen Sie den Fingerabdruck in die Richtung, die Sie "walk" (Gehen) möchten.

## <a name="immersive-headset-input-support"></a>Unterstützung für immersive Headseteingaben

[Windows Mixed Reality immersive Headsets unterstützen](immersive-headset-hardware-details.md) mehrere Eingabetypen für die Navigation in Windows Mixed Reality Startseite. HoloLens unterstützt keine Accessoryeingaben für die Navigation, da Sie physisch navigieren und Ihre Umgebung sehen. Allerdings unterstützt HoloLens [Eingaben für](hardware-accessories.md) die Interaktion mit Apps.

### <a name="motion-controllers"></a>Bewegungscontroller

Die beste Windows Mixed Reality ist die Verwendung von [](../design/motion-controllers.md) Windows Mixed Reality-Motion-Controllern, die die Nachverfolgung von sechs Grad an Freiheit unterstützen, indem nur die Sensoren in Ihrem Headset verwendet werden – keine externen Kameras oder Marker erforderlich!

Navigationsbefehle werden in Kürze verfügbar sein.

### <a name="gamepad"></a>Gamepad
* **Linker Thumbstick:**
  * Halten Sie den linken Stick gedrückt, um das [Teleportations-Reticle](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) auf den Weg zu bringen.
  * Tippen Sie auf den Stick nach links, rechts oder zurück, um in kleinen Schritten nach links, rechts oder zurück zu wechseln.
  * Klicken Sie nach unten auf den linken Stick, halten Sie ihn, und bewegen Sie den Thumbstick dann in die Richtung, die Sie [virtuell "walk" machen möchten.](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)
* Tippen Sie **auf den rechten Fingerabdruck** nach links oder rechts, um die Richtung um 45 Grad zu drehen.
* Durch Drücken der **Schaltfläche A** wird ausgewählt und wie die Tippbewegung in [die Luft](../design/gaze-and-commit.md#composite-gestures) fungiert.
* Durch Drücken **der Schaltfläche** Guide (Leitfaden) wird [die Startmenü](navigating-the-windows-mixed-reality-home.md#start-menu) und verhält sich wie die [Blumengeste.](../design/system-gesture.md#bloom)
* Durch Drücken **des linken und rechten Triggers** können Sie eine 2D-Desktop-App, mit der Sie zu Hause interagieren, vergrößern und verkleinern.

### <a name="keyboard-and-mouse"></a>Tastatur und Maus

**Hinweis:** Verwenden **Windows Taste + Y,** um mit der Maus zwischen dem Steuern des Desktops Ihres PCs und dem Windows Mixed Reality zu wechseln.

Im Windows Mixed Reality:
* Wenn Sie die **Maustaste mit der linken Maustaste** drücken, wird ausgewählt, und sie verhält sich wie die [Tippbewegung in die](../design/gaze-and-commit.md#composite-gestures) Luft.
* Wenn Sie die **Maustaste mit der rechten Maustaste** gedrückt halten, wird das [Teleportations-Reticle](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) angezeigt.
* Wenn Sie **die Windows** auf der Tastatur drücken, wird das [Startmenü angezeigt](navigating-the-windows-mixed-reality-home.md#start-menu) und verhält sich wie die [Blumengeste.](../design/system-gesture.md#bloom)
* Wenn [](../design/gaze-and-commit.md) Sie eine 2D-Desktop-App  verwenden, können Sie mit der linken Maustaste klicken, um  sie **auszuwählen,** mit der rechten Maustaste auf kontextmenüs klicken und das Scrollrad zum Scrollen verwenden (genau wie auf dem Desktop Ihres PCs).

## <a name="cortana"></a>Cortana

[Cortana](../design/voice-input.md#hey-cortana) ist Ihr persönlicher Assistent in Windows Mixed Reality, genau wie auf PC und Telefon. HoloLens verfügt über ein integriertes Mikrofon, aber immersive Headsets erfordern möglicherweise zusätzliche Hardware. Verwenden Cortana, um Apps zu öffnen, Ihr Gerät neu zu starten, Dinge online zu suchen und vieles mehr. Entwickler können sich auch dafür entscheiden, [Cortana](https://dev.windows.com/cortana) in ihre Erfahrungen zu integrieren.

Sie können auch Sprachbefehle verwenden, um zu Hause zu bleiben. Zeigen Sie z. B. [](../design/gaze-and-commit.md) auf eine Schaltfläche (mit Anvität oder Controller, je nach Gerät), und sagen Sie "Auswählen". Andere Sprachbefehle sind "Go home", "Bigger", "Smaller", "Close" und "Zu mir drehen".

## <a name="store-settings-and-system-apps"></a>Store, Einstellungen und System-Apps

Windows Mixed Reality verfügt über mehrere integrierte Apps, z. B.:
* **Microsoft Store** zum Herunterladen von Apps und Spielen
* **Feedback-Hub** Feedback zu den System- und System-Apps senden
* **Einstellungen** zum Konfigurieren von Systemeinstellungen ([einschließlich Netzwerk-](/hololens/hololens-network) und Systemupdates)
* **Microsoft Edge** zum Durchsuchen von Websites
* **Fotos** zum Anzeigen und Freigeben von Fotos und Videos
* **Kalibrierung** (nur HoloLens) zum Anpassen der HoloLens an den aktuellen Benutzer
* **Lernen Sie Gesten** (HoloLens) oder **Mixed Reality-Tutorial** (immersive Headsets) an, um mehr über die Verwendung Ihres Geräts zu erfahren.
* **3D-Viewer,** um Ihre Welt mit Mixed Reality-Inhalten zu verzieren
* **Mixed Reality-Portal** (Desktop) zum Einrichten und Verwalten Ihres immersiven Headsets und zum Streamen einer Livevorschau Ihrer Ansicht im Headset, damit sie von anderen angezeigt werden kann.
* **Filme und Fernsehsendungen** zum Anzeigen von 360 Videos und den neuesten Filmen und Fernsehsendungen
* **Cortana** für alle Anforderungen Ihres virtuellen Assistenten
* **Desktop** (immersive Headsets) zum Anzeigen Ihres Desktopmonitors in einem immersiven Headset
* **Datei-Explorer** Zugreifen auf Dateien und Ordner auf Ihrem Gerät

## <a name="see-also"></a>Siehe auch
* [App-Ansichten](../design/app-views.md)
* [Motion-Controller](../design/motion-controllers.md)
* [Hardware-Zubehör](hardware-accessories.md)
* [Umgebungsüberlegungen für HoloLens](/hololens/hololens-environment-considerations)
* [Implementieren von 3D-App-Launchern](../distribute/implementing-3d-app-launchers.md)
* [Erstellen von 3D-Modellen für die Verwendung im Windows Mixed Reality Home](../distribute/creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)