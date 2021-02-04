---
title: Erstellen Ihrer ersten HoloLens Unreal-Anwendung
description: Erfahren Sie, wie Sie ein Unreal-Projekt korrekt mit Szenenobjekten und Eingabeinteraktionen für die Mixed Reality-Entwicklung für HoloLens konfigurieren.
author: hferrone
ms.author: safarooq
ms.date: 01/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, Unreal-Editor, UE4, HoloLens, HoloLens 2, Mixed Reality, Entwicklung, Dokumentation, Leitfäden, Features, Mixed Reality-Headset, Windows Mixed Reality-Headset, Virtual Reality-Headset, Portieren, Upgrade
ms.openlocfilehash: 467987f69b50c0ec635c99899d6bcecab5a62af0
ms.sourcegitcommit: 1304f8f0a838290c1ae3db34670b67c75ea9bdaa
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2021
ms.locfileid: "99421429"
---
# <a name="creating-your-first-hololens-unreal-application"></a>Erstellen Ihrer ersten HoloLens Unreal-Anwendung

In dieser Anleitung erfahren Sie, wie Sie Ihre erste Mixed Reality-App auf der HoloLens in der Unreal Engine zum Laufen bringen. In der Tradition von "Hallo Welt" erstellen Sie eine einfache App, die einen Würfel auf dem Bildschirm anzeigt. Um die App nützlicher zu machen, erstellen Sie außerdem Ihre erste Geste zum Drehen des Würfels und zum Beenden der Anwendung. 

## <a name="objectives"></a>Ziele

* Beginnen eines HoloLens-Projekts
* Aktivieren der richtigen Plug-Ins
* Erstellen einer ARSessionConfig-Datenobjekts
* Einrichten der Gesteneingabe
* Erstellen einer einfachen Ebene
* Implementieren einer Zusammendrückbewegung

## <a name="creating-a-new-project"></a>Erstellen eines neuen Projekts

Als erstes benötigen Sie ein Projekt, mit dem Sie arbeiten können. Wenn Sie Einsteiger in die Unreal-Entwicklung sind, müssen Sie aus dem Epic-Startprogramm [unterstützende Dateien herunterladen](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal).

1. Starten der Unreal Engine
2. Wählen Sie unter **New Project Categories** (Kategorien für neues Projekt) die Option **Games** (Spiele) aus, und klicken Sie auf **Next** (Weiter):

![Geöffnetes Fenster „Zuletzt geöffnete Projekte“ mit hervorgehobener Option „Games“ (Spiele).](images/unreal-quickstart-img-01.png)

3. Wählen Sie die **Leer** e Vorlage aus, und klicken Sie auf **Weiter**:

![Unreal-Projektbrowserfenster mit hervorgehobener Vorlage „Leer“.](images/unreal-quickstart-img-02.png)

4. Legen Sie in den **Projekteinstellungen**, **C++, Skalierbares 3D oder 2D, Mobilgerät/Tablet** und **Keine Startinhalte** fest, wählen Sie dann einen Speicherort aus, und klicken Sie auf **Projekt erstellen**.

> [!NOTE] 
> Verwenden Sie eher ein C++- anstelle eines Blaupausenprojekts, um das OpenXR-Plug-In später verwenden zu können. In dieser Schnellstartanleitung wird das OpenXR-Standard-Plug-In aus dem Lieferumfang der Unreal Engine verwendet. Es wird jedoch empfohlen, das offizielle OpenXR-Plug-In von Microsoft herunterzuladen und zu verwenden. Hierfür ist es erforderlich, dass das Projekt ein C++-Projekt ist.

![Fenster „Projekteinstellungen“ mit hervorgehobenen Optionen „Projekt“, „Leistung“, „Zielplattform“ und „Startinhalte“.](images/unreal-quickstart-img-03.png)

Ihr neues Projekt sollte automatisch im Unreal-Editor geöffnet werden, womit Sie dann auch für den nächsten Abschnitt bereit sind.

## <a name="enabling-required-plugins"></a>Aktivieren der erforderlichen Plug-Ins

Bevor Sie mit dem Hinzufügen von Objekten zur Szene beginnen können, müssen Sie zwei Plug-Ins aktivieren.

1. Öffnen Sie **Edit > Plugins** (Bearbeiten > Plug-Ins), und wählen Sie in der Liste der integrierten Optionen **Augmented Reality** aus.
* Scrollen Sie nach unten bis zu **HoloLens**, und aktivieren Sie **Aktiviert**.

![Fenster „Plug-Ins“ mit geöffnetem Abschnitt „Augmented Reality“ und hervorgehobener Option „HoloLens“.](images/unreal-quickstart-img-04.png)

2. Geben Sie in das Suchfeld in der oberen rechten Ecke **OpenXR** ein, und aktivieren Sie die Plug-Ins **OpenXR** und **OpenXRMsftHandInteraction**:

![Fenster „Plug-Ins“ mit aktiviertem Plug-In „OpenXR“.](images/unreal-quickstart-img-05.jpg)

![Fenster „Plug-Ins“ mit aktiviertem Plug-In „OpenXRMsftHandInteraction“.](images/unreal-quickstart-img-06.jpg)

3. Starten Sie Ihren Editor neu.

> [!NOTE]
> In diesem Tutorial wird OpenXR verwendet, aber die zwei zuvor installierten Plug-Ins stellen derzeit nicht den vollständigen Funktionsumfang für die HoloLens-Entwicklung bereit. Das HandInteraction-Plug-In reicht für die „Zusammendrücken“-Geste aus, die Sie später verwenden werden. Wenn Sie jedoch über die Grundlagen hinausgehen möchten, müssen Sie [das OpenXR-Plug-In herunterladen](https://github.com/microsoft/Microsoft-OpenXR-Unreal).

Wenn die Plug-Ins aktiviert sind, können Sie sich darauf konzentrieren, sie mit Inhalt zu füllen.

## <a name="creating-a-level"></a>Erstellen eines Levels

Ihre nächste Aufgabe besteht darin, ein Player-Setup mit einem Startpunkt und einem Würfel als Referenz und Maßstab zu erstellen.

1. Wählen Sie **File > New Level** (Datei > Neues Level) und dann **Empty Level** (Leeres Level) aus. Die Standardszene im Viewport sollte nun leer sein.
2. Wählen Sie auf der Registerkarte **Modes** (Modi) **Basic** (Einfach) aus, und ziehen Sie **PlayerStart** auf die Szene.
* Legen Sie auf der Registerkarte **Details** die Option **Location** (Position) auf **X = 0, Y = 0** und **Z = 0** fest, um den Benutzer beim Start der App in der Mitte der Szene zu platzieren.

![Unreal-Editor-Szene mit hinzugefügter Position und PlayerStart.](images/unreal-quickstart-img-07.png)

3. Ziehen Sie von der Registerkarte **Basic** (Einfach) einen **Würfel** auf die Szene.
* Legen Sie die **Position** des Würfels auf **X = 50, Y = 0** und **Z = 0** fest, damit der Würfel beim Start 50 cm vom Spieler entfernt platziert wird.
* Ändern Sie die **Skalierung** des Würfels in **X = 0,2, Y = 0,2** und **Z = 0,2**. 

Sie können den Würfel erst sehen, wenn Sie Ihrer Szene eine Lichtquelle hinzufügen, und das ist Ihre letzte Aufgabe vor dem Testen der Szene.

4. Wechseln Sie im Bereich **Modes** (Modi) zur Registerkarte **Lights** (Lichtquellen), und ziehen Sie ein **Directional Light** (Gerichtetes Licht) auf die Szene.
* Positionieren Sie das Licht oberhalb von **PlayerStart**, sodass Sie es sehen können.

![Unreal-Editor-Szene mit Würfel und hinzugefügtem direktionalem Licht.](images/unreal-quickstart-img-08.png)

5. Wechseln Sie zu **File > Save Current** (Datei > Aktuelle speichern), benennen Sie Ihr Level **Main** (Hauptlevel), und wählen Sie **Save** (Speichern) aus.

Nachdem die Szene jetzt festgelegt ist, drücken Sie auf **Play** (Wiedergabe) in der Symbolleiste, um den Würfel in Aktion zu sehen! Wenn Sie Ihre Arbeit genügend gewürdigt haben, drücken Sie Esc, um die Anwendung zu beenden.

![Szene im Wiedergabemodus mit dem Cube in der Mitte des Bildschirms.](images/unreal-quickstart-img-09.png)

Nachdem die Szene nun eingerichtet ist, lassen Sie uns sie für einige grundlegende Interaktionen in AR vorbereiten. Zunächst müssen Sie eine AR-Sitzung erstellen, und Sie können Blaupausen hinzufügen, um Handinteraktion zu ermöglichen.

## <a name="adding-a-session-asset"></a>Hinzufügen eines Sitzungsobjekts

AR-Sitzungen in Unreal kommen nicht aus dem Nichts zustande. Um eine Sitzung zu verwenden, benötigen Sie ein ARSessionConfig-Datenobjekt, mit dem Sie arbeiten können, und das ist Ihre nächste Aufgabe:

1. Wählen Sie im **Inhaltsbrowser** die Option **Neu hinzufügen > Sonstiges > Datenobjekt** aus, und stellen Sie sicher, dass Sie sich auf der Stammebene der Inhaltsordner befinden.
2. Wählen Sie **ARSessionConfig** aus, klicken Sie auf **Select** (Auswählen), und geben Sie dem Objekt den Namen **ARSessionConfig**:

![Geöffnetes Fenster „Datenressourcenklasse auswählen“ mit hervorgehobenem AR-Sitzungskonfigurationsobjekt.](images/unreal-quickstart-img-10.png)

2. Doppelklicken Sie auf **ARSessionConfig**, um es zu öffnen, **Speichern** Sie es mit allen Standardeinstellungen, und kehren Sie zum Hauptfenster zurück.

![Fenster mit den Details des AR-Sitzungskonfigurationsobjekts.](images/unreal-quickstart-img-11.png)

Nachdem dies erledigt ist, überzeugen Sie sich im nächsten Schritt davon, dass die AR-Sitzung beim Laden des Levels gestartet und mit dem Ende des Levels beendet wird. Glücklicherweise verfügt Unreal über eine spezielle Blaupause, die als **Level Blueprint** (Levelblaupause) bezeichnet wird und als levelweites globales Ereignisdiagramm fungiert. Durch das Verbinden des ARSessionConfig-Medienobjekts mit der Level Blueprint wird sichergestellt, dass die AR-Sitzung ordnungsgemäß ausgelöst wird, wenn das Spiel beginnt.

3. Wählen Sie in der Editor-Symbolleiste **Blueprints > Open Level Blueprint** (Blaupausen > Ebenenblaupause öffnen) aus:

![Geöffnetes Menü „Blaupause“ mit hervorgehobener Option „Ebenenblaupause öffnen“.](images/unreal-quickstart-img-12.png)

4. Ziehen Sie den Ausführungsknoten (nach links weisendes Pfeilsymbol) von **Event BeginPlay** (BeginPlay-Ereignis) herunter, und lassen Sie ihn los.
* Suchen Sie nach dem Knoten **Start AR Session** (AR-Sitzung starten), und drücken Sie die EINGABETASTE.
* Klicken Sie unter **Session Config** (Sitzungskonfiguration) auf die Dropdownliste **Select Asset** (Medienobjekt auswählen), und wählen Sie das Medienobjekt **ARSessionConfig** aus.

![Blaupausendiagramm mit Ereignis „Wiedergabe beginnen“, verbunden mit der Funktion „AR-Sitzung starten“.](images/unreal-quickstart-img-13.png)

5. Klicken Sie an beliebiger Stelle im EventGraph mit der rechten Maustaste, und erstellen Sie einen neuen Knoten **Event EndPlay**. 
* Ziehen Sie den Ausführungspin, lassen Sie ihn los, suchen Sie nach einem Knoten **Stop AR Session** (AR-Sitzung beenden), und drücken Sie die EINGABETASTE. 
* Klicken Sie auf **Compile** (Kompilieren), dann auf **Speichern**, und kehren Sie schließlich zum Hauptfenster zurück.

> [!IMPORTANT]
> Wenn die AR-Sitzung mit dem Ende des Levels noch weiter ausgeführt wird, funktionieren bestimmte Features möglicherweise nicht mehr, wenn Sie die App beim Streaming zu einem Headset neu starten.

![Ereignisknoten „Wiedergabe beenden“, angefügt an die Funktion „AR-Sitzung beenden“.](images/unreal-quickstart-img-14.png)

## <a name="setting-up-inputs"></a>Einrichten von Eingaben

1. Wählen Sie **Bearbeiten > Projekteinstellungen** aus, und wechseln Sie zu **Engine > Eingabe**.
2. Wählen Sie das **+** -Symbol neben **Aktionszuordnungen** aus, und erstellen Sie die Aktionen **RightPinch** (rechts zusammendrücken) und **LeftPinch** (links zusammendrücken):

![Bindungseingabeeinstellungen mit hervorgehobenen Aktionszuordnungen „Rechts zusammendrücken“ und „Links zusammendrücken“.](images/unreal-quickstart-img-15.jpg)

3. Ordnen Sie die Aktionen **RightPinch** und **LeftPinch** den entsprechenden **OpenXR MSFT-Handinteraktion** saktionen zu:

![Aktionszuordnungen mit hervorgehobenen Optionen für die OpenXR MSFT-Handinteraktion.](images/unreal-quickstart-img-16.jpg)

## <a name="setting-up-gestures"></a>Einrichten von Gesten

Nachdem wir die Eingaben eingerichtet haben, können wir nun zum spannenden Teil kommen: Hinzufügen von Gesten! Lassen Sie uns den Würfel mit einem rechten Zusammendrücken (Right Pinch) drehen und die Anwendung bei einem linken Zusammendrücken (Left Pinch) schließen.

1. Öffnen Sie die **Ebenenblaupause**, und fügen Sie eine **InputAction RightPinch** und **InputAction LeftPinch** hinzu.
* Verbinden Sie das RighPinch-Ereignis mit einer **AddActorLocalRotation**, wobei Ihr **Würfel** als Ziel und **Deltadrehung** auf **X = 0, Y = 0** und **Z = 20** festgelegt werden. Der Würfel wird jetzt bei jedem Zusammendrücken um 20 Grad gedreht.
* Verbinden Sie das LeftPinch-Ereignis mit **Spiel beenden**.

![Geöffnete Ebenenblaupause wird mit Eingabeaktionen für die Ereignisse RightPinch und LeftPinch.](images/unreal-quickstart-img-17.jpg)

2. Legen Sie in den Einstellungen zum **Transformieren** die Option **Mobilität** auf **Verschiebbar** fest, damit dynamisches Verschieben ermöglicht wird:

![Transformationseinstellungen mit hervorgehobener Eigenschaft „Mobilität“.](images/unreal-quickstart-img-18.jpg)

An diesem Punkt sind Sie so weit, die Anwendung bereitzustellen und zu testen!