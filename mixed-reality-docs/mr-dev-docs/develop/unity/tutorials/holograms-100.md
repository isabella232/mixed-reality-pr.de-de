---
title: 'HoloLens (1. Generation) Grundlagen 100: Erste Schritte mit Unity'
description: Erfahren Sie, wie Sie Ihre erste einfache Mixed Reality-Anwendung "hello world" für HoloLens und Windows Mixed Reality Geräte erstellen.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: Mixed Reality, Windows Mixed Reality, HoloLens, immersive, vr, mr, erste Schritte, Hologramm, Academy, Tutorial, Mixed Reality Academy, Unity, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 518be5642304b6307f0b26f30f37315eba4164448493d928f6effb3027f7d611
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196504"
---
# <a name="hololens-1st-gen-basics-100-getting-started-with-unity"></a>HoloLens (1. Generation) Grundlagen 100: Erste Schritte mit Unity

>[!IMPORTANT]
>Die Mixed Reality Academy-Tutorials wurden im Hinblick auf HoloLens (1. Generation), Unity 2017 und Mixed Reality Immersive Headsets entworfen.  Daher halten wir es für wichtig, diese Tutorials für Entwickler verfügbar zu halten, die noch nach Anleitung beim Entwickeln für diese Geräte suchen. Diese Tutorials werden **_nicht_** mit den neuesten Toolsets oder Interaktionen aktualisiert, die für HoloLens 2 verwendet werden, und sind möglicherweise nicht mit neueren Versionen von Unity kompatibel.  Sie werden gewartet, um weiterhin auf den unterstützten Geräten zu funktionieren. [Es wurde eine neue Reihe von Tutorials](mrlearning-base.md) für HoloLens 2 veröffentlicht.

Dieses Tutorial führt Sie durch das Erstellen einer einfachen Mixed Reality-App, die mit Unity erstellt wurde.

## <a name="device-support"></a>Geräteunterstützung

<table>
<tr>
<th>Kurs</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Immersive Headsets</a></th>
</tr><tr>
<td>MR-Grundlagen 100: Erste Schritte mit Unity</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Voraussetzungen

* Ein Windows 10 PC, der mit den [richtigen installierten Tools](../../install-the-tools.md)konfiguriert ist.

## <a name="chapter-1---create-a-new-project"></a>Kapitel 1: Erstellen eines neuen Project

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

Um eine App mit Unity zu erstellen, müssen Sie zunächst ein Projekt erstellen. Dieses Projekt ist in einige Ordner unterteilt, von denen der wichtigste Der Ordner Assets ist. Dies ist der Ordner, der alle Ressourcen enthält, die Sie aus Tools zum Erstellen digitaler Inhalte importieren, z. B. Maya, MaxEma 4D oder Mpi, den gesamten Code, den Sie mit Visual Studio oder Ihrem bevorzugten Code-Editor erstellen, sowie eine beliebige Anzahl von Inhaltsdateien, die Unity erstellt, wenn Sie Szenen, Animationen und andere Unity-Medienobjekttypen im Editor erstellen.

Zum Erstellen und Bereitstellen von UWP-Apps kann Unity das Projekt als Visual Studio Projektmappe exportieren, die alle erforderlichen Medienobjekt- und Codedateien enthält.

1. Starten von Unity
2. Wählen Sie **Neu** aus.
3. Geben Sie einen Projektnamen ein (z. B. "MixedRealityIntroduction").
4. Geben Sie einen Speicherort zum Speichern Ihres Projekts ein.
5. Stellen Sie sicher, dass die **Umschaltfläche 3D** ausgewählt ist.
6. Wählen Sie **Projekt erstellen** aus.

Herzlichen Glückwunsch, Sie sind nun bereit, um mit Ihren Mixed Reality-Anpassungen zu beginnen.

## <a name="chapter-2---setup-the-camera"></a>Kapitel 2: Einrichten der Kamera

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

Die Unity-Hauptkamera verarbeitet die Kopfverfolgung und stereokopisches Rendering. An der Hauptkamera müssen einige Änderungen vorgenommen werden, um sie mit Mixed Reality zu verwenden.

1. Wählen Sie Datei > Neue Szene aus.

Zunächst ist es einfacher, Ihre App zu gestalten, wenn Sie sich die Anfangsposition des Benutzers als vorstellen (**X**: 0, **Y**: 0, **Z**: 0). Da die Hauptkamera die Bewegung des Kopfes des Benutzers verfolgt, kann die Anfangsposition des Benutzers festgelegt werden, indem die Startposition der Hauptkamera festgelegt wird.

1. Auswählen der **Hauptkamera** im **Hierarchiebereich**
2. Suchen Sie im **Inspektorbereich** nach der **Komponente Transformieren,** und ändern Sie die **Position** von (**X**: 0, **Y**: 1, **Z**: -10) in (**X**: 0, **Y**: 0, **Z**: 0).

Zweitens muss der Standardhintergrund der Kamera einige Überlegungen an sich haben.

**Für HoloLens Anwendungen** sollte die reale Welt hinter allem stehen, was die Kamera rendert, und nicht hinter einer Skybox-Textur.

1. Wenn die **Hauptkamera** weiterhin im **Hierarchiebereich** ausgewählt ist, suchen Sie die **Kamerakomponente** im **Inspektorbereich,** und ändern Sie die Dropdownliste **Clear Flags (Flags** löschen) von **Skybox** in **Solid Color (Volltonfarbe).**
2. Wählen  Sie die Hintergrundfarbauswahl aus, und ändern Sie die **RGBA-Werte** in (0, 0, 0, 0).

**Für Mixed Reality-Anwendungen, die auf immersive Headsets ausgerichtet** sind, können wir die standardmäßige Skybox-Textur verwenden, die Unity bereitstellt.

1. Wenn die **Hauptkamera** weiterhin im **Hierarchiebereich** ausgewählt ist, suchen Sie die **Kamerakomponente** im **Inspektorbereich,** und behalten Sie die Dropdownliste **Clear Flags (Flags** löschen) in **Skybox** bei.

Drittens betrachten wir die nahe Clipebene in Unity und verhindern, dass Objekte zu nah an den Augen der Benutzer gerendert werden, wenn sich ein Benutzer einem Objekt oder einem Benutzer nähert.

**Für HoloLens Anwendungen** kann die Clipebene in der Nähe auf die [HoloLens empfohlenen](../camera-in-unity.md#using-clipping-planes) 0,85 Meter festgelegt werden.

1. Wenn die **Hauptkamera** weiterhin im **Hierarchiebereich** ausgewählt ist, suchen Sie die **Kamerakomponente** im **Inspektorbereich,** und ändern Sie das Feld **Near Clip Plane** von der Standardeinstellung **0,3** in die HoloLens empfohlen **0,85**.

**Für Mixed Reality-Anwendungen, die auf immersive Headsets ausgerichtet** sind, können wir die Standardeinstellung verwenden, die Unity bereitstellt.

1. Wenn die **Hauptkamera** weiterhin im **Hierarchiebereich** ausgewählt ist, suchen Sie die **Kamerakomponente** im **Inspektorbereich,** und behalten Sie das Feld **Near Clip Plane** auf den Standardwert **0,3** bei.

Abschließend speichern wir unseren bisherigen Fortschritt. Um die Szenenänderungen zu speichern, wählen Sie **Datei > Szene speichern unter** aus, nennen Sie die Szene **Main**, und wählen **Sie Speichern** aus.

## <a name="chapter-3---setup-the-project-settings"></a>Kapitel 3: Einrichten der Project Einstellungen

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

In diesem Kapitel legen wir einige Unity-Projekteinstellungen fest, die uns helfen, das Windows Holographic SDK für die Entwicklung als Ziel festzulegen. Außerdem legen wir einige Qualitätseinstellungen für unsere Anwendung fest. Schließlich stellen wir sicher, dass unsere Buildziele auf Universal Windows Platform festgelegt sind.

### <a name="unity-performance-and-quality-settings"></a>Unity-Leistungs- und Qualitätseinstellungen

**Unity-Qualitätseinstellungen für HoloLens**

![Unity-Qualitätseinstellungen für HoloLens](images/qualitysettings.png)

Da die Beibehaltung einer hohen Framerate auf HoloLens so wichtig ist, möchten wir, dass die Qualitätseinstellungen für die schnellste Leistung optimiert werden. Ausführlichere Leistungsinformationen finden Sie unter [Leistungsempfehlungen für Unity.](../performance-recommendations-for-unity.md)

1. Wählen Sie **Edit > Project Einstellungen > Quality (> Project Einstellungen > Qualität bearbeiten)** aus.
2. Wählen Sie die **Dropdownliste** unter dem Logo universal **Windows Platform** und dann Very **Low (Sehr niedrig)** aus. Sie wissen, dass die Einstellung ordnungsgemäß angewandt wurde, wenn das Feld in der Spalte Universelle Windows-Plattform und der Zeile **Sehr niedrig** grün ist.

**Für Mixed Reality-Anwendungen, die auf verdeckte Displays ausgerichtet** sind, können Sie die Qualitätseinstellungen auf die Standardwerte festlegen.

### <a name="target-windows-10-sdk"></a>Ziel-Windows 10 SDK

**Ziel Windows Holographic SDK**

![Ziel Windows Holographic SDK](../images/xrsettings.png)

Wir müssen Unity mitteilen, dass die App, die wir exportieren möchten, eine [immersive Ansicht](../../../design/app-views.md) anstelle einer 2D-Ansicht erstellen sollte. Hierzu aktivieren wir virtual reality-Unterstützung für Unity für das Windows 10 SDK.

1. Wechseln **Sie** zu Bearbeiten > Project Einstellungen > Player .
2. Wählen Sie im **Inspektorbereich** für Player Einstellungen das Symbol **Universelle Windows Plattform** aus.
3. Erweitern Sie die Gruppe **XR-Einstellungen**.
4. Aktivieren Sie im Abschnitt **Rendering** das Kontrollkästchen **Virtuelle Realität unterstützt**, um eine neue Liste mit **Virtual Reality-SDKs** hinzuzufügen.
5. Überprüfen Sie, ob in der Liste **Windows Mixed Reality** angezeigt wird. Wenn nicht, wählen Sie die Schaltfläche **+** am Ende der Liste aus, und wählen Sie **Windows Mixed Reality** aus.

>[!NOTE]
>Wenn das Symbol **Universal Windows Platform (Universelle Windows-Plattform)** nicht angezeigt wird, überprüfen Sie, ob Sie während der Installation universelle Windows Plattformbuildunterstützung ausgewählt haben. Wenn nicht, müssen Sie Unity eventuell mit der richtigen Windows-Installation neu installieren.

Ein hervorragender Auftrag zum Anwenden aller Projekteinstellungen. Als Nächstes fügen wir ein Hologramm hinzu!

## <a name="chapter-4---create-a-cube"></a>Kapitel 4: Erstellen eines Cubes

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

Das Erstellen eines Cubes in Ihrem Unity-Projekt entspricht dem Erstellen eines anderen Objekts in Unity. Das Platzieren eines Cubes vor dem Benutzer ist einfach, da das Unity-Koordinatensystem der realen Welt zugeordnet ist, wobei eine Verbrauchseinheit in Unity ungefähr eine Meter in der realen Welt ist.

1. Wählen Sie in der oberen linken Ecke des **Hierarchiebereichs** die Dropdownliste **Erstellen** und dann **3D-Objekt > Cube** aus.
2. Auswählen des neu erstellten **Cubes** im **Hierarchiebereich**
3. Suchen Sie im **Inspektor** nach der **Komponente Transformieren,** und ändern Sie **position** in (**X**: 0, **Y**: 0, **Z**: 2). *Dadurch wird der Würfel 2 Meter vor der Anfangsposition des Benutzers positioniert.*
4. Ändern **Sie** in der Komponente **Transformieren** die Rotation in (**X**: 45, **Y**: 45, **Z**: 45) und ändern **Sie Skalierung** in (**X**: 0,25, **Y**: 0,25, **Z**: 0,25). *Dadurch wird der Cube auf 0,25 Meter skaliert.*
5. Um die Szenenänderungen zu speichern, wählen Sie **Datei > Szene speichern** aus.

## <a name="chapter-5---verify-on-device-from-unity-editor"></a>Kapitel 5: Überprüfen auf dem Gerät über den Unity-Editor

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

Nachdem wir unseren Cube erstellt haben, ist es an der Zeit, ein Gerät schnell einzuchecken. Sie können dies direkt im Unity-Editor durchführen.

### <a name="initial-setup"></a>Ersteinrichtung

1. Öffnen Sie auf Ihrem Entwicklungs-PC in Unity das Fenster **Datei > Build Einstellungen.**
2. Ändern Sie **Plattform** in **Universelle Windows Plattform,** und klicken Sie auf **Plattform wechseln.**

### <a name="for-hololens-use-unity-remoting"></a>Verwenden von Unity-Remoting für HoloLens

1. Installieren Sie auf Ihrem HoloLens den [Holographic Remoting Player,](../../platform-capabilities-and-apis/holographic-remoting-player.md)der über die Windows Store verfügbar ist, und führen Sie den Player aus. Starten Sie die Anwendung auf dem Gerät, und es wird ein Wartezustand angezeigt, und die IP-Adresse des Geräts wird angezeigt. Notieren Sie sich die IP-Adresse.
2. Öffnen **Sie das > XR > Holographic Emulation**.
3. Ändern **Sie den Emulationsmodus** **von None** in Remote **in Device**.
4. Geben **Sie unter Remotecomputer** die IP-Adresse Ihres HoloLens notiert haben.
5. Klicken Sie auf **Verbinden**.
6. Stellen Sie **sicher, dass sich der Verbindungsstatus** in grün **Verbunden ändert.**
7. Jetzt können Sie im **Unity-Editor** auf Wiederklicken.

Sie können den Cube nun auf dem Gerät und im Editor sehen. Sie können Objekte anhalten, untersuchen und debuggen, wie Sie eine App im Editor ausführen, da dies im Wesentlichen der Fall ist, aber mit Video-, Audio- und Geräteeingaben, die zwischen dem Hostcomputer und dem Gerät über das Netzwerk übertragen werden.

### <a name="for-other-mixed-reality-supported-headsets"></a>Für andere von Mixed Reality unterstützte Headsets

1. Verbinden sie das Headset mithilfe des USB-Kabels und des DISPLAY-Anschlusskabels an Ihren Entwicklungs-PC an.
2. Starten Sie **Mixed Reality-Portal,** und stellen Sie sicher, dass Sie die erste Ausführung abgeschlossen haben.
3. In Unity können Sie jetzt auf die Schaltfläche Wiedergabe klicken.

Sie können nun das Würfelrendering in Ihrem Mixed Reality-Headset und im Editor sehen.

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a>Kapitel 6: Erstellen und Bereitstellen auf dem Gerät über Visual Studio

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

Wir können nun unser Projekt kompilieren, um Visual Studio und auf unserem Zielgerät bereitzustellen.

### <a name="export-to-the-visual-studio-solution"></a>Exportieren in die Visual Studio Lösung

1. Öffnen **Sie > Fenster Einstellungen** Erstellen.
1. Klicken **Sie auf Geöffnete Szenen hinzufügen,** um die Szene hinzuzufügen.
1. Ändern **Sie Plattform** in Universelle **Windows Plattform,** und klicken Sie **auf Plattform wechseln.**
1. Stellen **Sie in Windows Universal Windows Platform** sicher, dass das **SDK** **Universal 10 ist.**
1. Lassen Sie für Zielgerät die Option **Beliebiges Gerät für** okklierte Anzeigen, oder wechseln Sie **zu HoloLens.**
1. **Der UWP-Buildtyp** sollte **D3D sein.**
1. **Das UWP SDK** könnte auf Neueste **installierte -Datei aufgelassen werden.**
1. Klicken Sie auf **Erstellen**.
1. Klicken Sie im Datei-Explorer auf **Neuer Ordner,** und nennen Sie den Ordner **"App".**
1. Klicken **Sie** bei ausgewähltem App-Ordner auf **die Schaltfläche Ordner** auswählen.
1. Wenn Unity mit dem Erstellen fertig ist, wird Windows Fenster Datei-Explorer angezeigt.
1. Öffnen Sie den **Ordner App** im Datei-Explorer.
1. Öffnen Sie die Visual Studio Projektmappe (MixedRealityIntroduction.sln in diesem Beispiel).

### <a name="compile-the-visual-studio-solution"></a>Kompilieren Visual Studio Projektmappe

Schließlich kompilieren wir die exportierte Visual Studio Lösung, stellen sie zur Anwendung und testen sie auf dem Gerät.

1. Ändern Sie in der oberen Symbolleiste Visual Studio Ziel von **Debuggen** in **Release** und von **ARM** in **X86.**

Die Anweisungen für die Bereitstellung auf einem Gerät unterscheiden sich im Vergleich zum Emulator. Befolgen Sie die Anweisungen für Ihr Setup.

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a>Bereitstellen auf Einem Mixed Reality-Gerät über Wi-Fi

1. Klicken Sie auf den Pfeil neben der **Schaltfläche Lokaler Computer,** und ändern Sie das Bereitstellungsziel in **Remotecomputer**.
2. Geben Sie die IP-Adresse Ihres  Mixed **Reality-Geräts** ein, und ändern Sie den Authentifizierungsmodus für HoloLens und Windows für andere Geräte in Universal (unverschlüsselte Protokolle).
3. Klicken Sie **auf Debuggen > Starten ohne Debuggen.**

**Für HoloLens**, wenn dies die erste Bereitstellung auf Ihrem Gerät ist, müssen Sie eine Kopplung [mithilfe von Visual Studio.](../../platform-capabilities-and-apis/using-visual-studio.md)

### <a name="deploy-to-mixed-reality-device-over-usb"></a>Bereitstellen auf einem Mixed Reality-Gerät über USB

Stellen Sie sicher, dass Ihr Gerät über das USB-Kabel angeschlossen ist.

1. **Klicken HoloLens** auf den Pfeil neben der Schaltfläche Lokaler **Computer,** und ändern Sie das Bereitstellungsziel in **Gerät**.
2. Behalten Sie die Einstellung Lokaler Computer bei, um auf **okkludente** Geräte zu abzielen, die an Ihren PC angefügt sind. Stellen Sie sicher, dass **Mixed Reality-Portal** ausgeführt wird.
3. Klicken Sie **auf Debuggen > Starten ohne Debuggen.**

### <a name="deploy-to-emulator"></a>Bereitstellen in Emulator

1. Klicken Sie auf den Pfeil neben der Schaltfläche **Gerät,** und wählen Sie in der Dropdownliste **HoloLens Emulator.**
2. Klicken Sie **auf Debuggen > Starten ohne Debuggen.**

### <a name="try-out-your-app"></a>Testen Ihrer App

Nachdem Ihre App bereitgestellt wurde, versuchen Sie, den Würfel zu bewegen, und beobachten Sie, dass er in der Welt vor Ihnen bleibt.

## <a name="see-also"></a>Siehe auch

* [Unity-Entwicklung – Übersicht](../unity-development-overview.md)
* [Bewährte Methoden für das Arbeiten mit Unity und Visual Studio](../best-practices-for-working-with-unity-and-visual-studio.md)
* [MR-Grundlagen 101](holograms-101.md)
* [MR-Grundlagen 101E](holograms-101e.md)