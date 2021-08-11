---
title: 2. Initialisieren des Projekts und der ersten Anwendung
description: Teil 2 von 6 einer Tutorialreihe zum Erstellen einer Schach-App mit der Unreal Engine 4 und dem UX Tools-Plug-In des Mixed Reality-Toolkits
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Tutorial, Erste Schritte, MRTK, UXT, UX-Tools, Dokumentation, Mixed Reality-Headset Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: e4fd7f69b3febec3997b13d7cb92579e9018e86cb3805b9a94dc76190affb34d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203919"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. Initialisieren des Projekts und der ersten Anwendung

Im ersten Tutorial beginnen Sie mit einem neuen Unreal-Projekt und aktivieren das HoloLens-Plug-In, erstellen und beleuchten ein Level und fügen Schachfiguren hinzu. Sie verwenden unsere vorgefertigten Objekte für alle 3D-Objekte und -Materialien, weshalb Sie nichts selber modellieren müssen. Am Ende dieses Tutorials verfügen Sie über einen leeren Zeichenbereich, der für Mixed Reality bereit ist.

> [!IMPORTANT]
> Stellen Sie sicher, dass alle auf der Seite [Erste Schritte](/windows/mixed-reality/unreal-uxt-ch1) genannten Voraussetzungen erfüllt sind.

## <a name="objectives"></a>Ziele

* Konfigurieren eines Unreal-Projekts für die HoloLens-Entwicklung
* Importieren von Medienobjekten und Einrichten einer Szene
* Erstellen von Akteuren und Ereignissen auf Skriptebene mithilfe von Blaupausen

## <a name="creating-a-new-unreal-project"></a>Erstellen eines neuen Unreal-Projekts

Als erstes benötigen Sie ein Projekt, mit dem Sie arbeiten können. Wenn Sie Einsteiger in die Unreal-Entwicklung sind, müssen Sie aus dem Epic-Startprogramm [unterstützende Dateien herunterladen](./unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal).

1. Starten der Unreal Engine

2. Wählen Sie unter **New Project Categories** (Kategorien für neues Projekt) die Option **Games** (Spiele) aus, und klicken Sie auf **Next** (Weiter). 

![Wählen Sie die Projektvorlage „Games“ (Spiele) aus.](images/unreal-uxt/2-gamestemplate.png)

3. Wählen Sie die **Leere** Vorlage aus, und klicken Sie auf **Weiter**. 

![Auswählen einer leeren Vorlage](images/unreal-uxt/2-template.PNG)

4. Legen Sie **C++** , **Scalable 3D or 2D, Mobile/Tablet** (Skalierbares 3D oder 2D, Mobilgerät/Tablet) und **No Starter Content** (Keine Startinhalte) als Ihre **Projekteinstellungen** fest, wählen Sie dann einen Speicherort aus, und klicken Sie auf **Projekt erstellen**. 

> [!NOTE]
> Anstelle eines Blaupausenprojekts müssen Sie ein C++-Projekt auswählen, um das UX Tools-Plug-In zu erstellen, das Sie später in Abschnitt 4 einrichten.

![Anfängliche Projekteinstellungen](images/unreal-uxt/2-project-settings.PNG)

Das Projekt sollte automatisch im Unreal Editor geöffnet werden, und damit sind Sie für den nächsten Abschnitt bereit.

## <a name="enabling-required-plugins"></a>Aktivieren der erforderlichen Plug-Ins

Um die über die Mixed Reality-Plattform von Microsoft verfügbaren Features zu verwenden, müssen Sie zunächst das Microsoft OpenXR-Plug-In installieren und aktivieren. Weitere Informationen zum Plug-In finden Sie im Projekt auf [GitHub](https://github.com/microsoft/Microsoft-OpenXR-Unreal).

1. Öffnen Sie den Epic Games Launcher. Navigieren Sie zum Unreal Engine Marketplace, und suchen Sie nach „[Microsoft OpenXR](https://www.unrealengine.com/marketplace/product/ef8930ca860148c498b46887da196239)“. Installieren Sie das Plug-In in Ihrer Engine.

![Unreal Marketplace](images/unreal-uxt/2-openxr-plugin.PNG)

2. Zurück im Unreal-Editor, wechseln Sie zu **Projekteinstellungen** > **Plug-Ins**, und suchen Sie nach „Microsoft OpenXR“. Stellen Sie sicher, dass das Plug-In aktiviert ist, und starten Sie den Editor neu, wenn Sie dazu aufgefordert werden.

![Aktivieren des Microsoft OpenXR-Plug-Ins](images/unreal-uxt/2-enable-plugin.PNG)

Wenn Sie das Microsoft OpenXR-Plug-In aktivieren, werden automatisch alle anderen Plug-Ins aktiviert, die für die Mixed Reality-Entwicklung erforderlich sind. Beachten Sie, dass das Plug-In „Microsoft Windows Mixed Reality“ deaktiviert sein muss, um OpenXR verwenden zu können. 

## <a name="creating-a-level"></a>Erstellen eines Levels
Ihre nächste Aufgabe besteht darin, ein Player-Setup mit einem Startpunkt und einem Würfel als Referenz und Maßstab zu erstellen.

1. Wählen Sie **File > New Level** (Datei > Neues Level) und dann **Empty Level** (Leeres Level) aus. Die Standardszene im Viewport sollte nun leer sein.

2. Wählen Sie auf der Registerkarte **Modes** (Modi) **Basic** (Einfach) aus, und ziehen Sie **PlayerStart** auf die Szene. 
    * Legen Sie auf der Registerkarte **Details** **Location** (Position) auf **X = 0**, **Y = 0** und **Z = 0** fest. Dadurch wird der Benutzer beim Start der App in der Mitte der Szene platziert.

![Viewport mit „PlayerStart“](images/unreal-uxt/2-playerstart.PNG)

3. Ziehen Sie einen **Würfel** von der Registerkarte **Basic** (Einfach) auf die Szene. 
    * Legen Sie **Location** (Position) auf **X = 50**, **Y = 0** und **Z = 0** fest. Dadurch wird der Würfel beim Start 50 cm vom Spieler entfernt platziert. 
    * Ändern Sie **Scale** (Maßstab) in **X = 0,2**, **Y = 0,2** und **Z = 0,2**, um den Würfel zu verkleinern. 

Sie können den Würfel erst sehen, wenn Sie Ihrer Szene eine Lichtquelle hinzufügen, und das ist Ihre letzte Aufgabe vor dem Testen der Szene.

4. Wechseln Sie im Bereich **Modes** (Modi) zur Registerkarte **Lights** (Lichtquellen), und ziehen Sie ein **Directional Light** (Gerichtetes Licht) auf die Szene. Positionieren Sie das Licht oberhalb von **PlayerStart**, sodass Sie es sehen können.

![Viewport mit hinzugefügtem Licht](images/unreal-uxt/2-light.PNG)

5. Navigieren Sie zu **File > Save Current** (Datei > Aktuelle speichern), benennen Sie Ihr Level **Main** (Hauptlevel), und wählen Sie **Save** (Speichern) aus. 

Nachdem die Szene jetzt festgelegt ist, drücken Sie auf **Play** (Wiedergabe) in der Symbolleiste, um den Würfel in Aktion zu sehen! Wenn Sie Ihre Arbeit genügend gewürdigt haben, drücken Sie **Esc**, um die Anwendung zu beenden.

![Ein Würfel im Viewport](images/unreal-uxt/2-cube.PNG)

Nachdem die Szene nun eingerichtet ist, können Sie damit beginnen, das Schachbrett und die Schachfigur hinzuzufügen, um die Anwendungsumgebung abzurunden.

## <a name="importing-assets"></a>Importieren von Medienobjekten
Die Szene sieht momentan etwas leer aus, aber das beheben Sie, indem Sie die vorgefertigten Medienobjekte in das Projekt importieren.

1. Laden Sie den Medienobjektordner von [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) herunter, und entpacken Sie ihn mit [7-zip](https://www.7-zip.org/).

2. Wählen Sie im **Inhaltsbrowser** die Optionen **Add New > New Folder** (Neu hinzufügen > Neuer Ordner) aus, und benennen Sie ihn **ChessAssets** (Schachobjekte). 
    * Doppelklicken Sie auf den neuen Ordner, in den Sie die 3D-Medienobjekte importieren.

![Anzeigen oder Ausblenden des Quellenbereichs](images/unreal-uxt/2-showhidesources.PNG)

3. Wählen Sie im **Inhaltsbrowser** den Befehl **Importieren** aus, wählen Sie im Ordner mit den entpackten Medienobjekten alle Elemente aus, und klicken Sie auf **Öffnen**. 
    * Die Objekte umfassen die Gittermodelle der 3D-Objekte für das Schachbrett und Figuren im FBX-Format sowie Texturschemas im TGA-Format, die Sie für Materialien verwenden.  

4. Wenn das Fenster mit den FBX-Importoptionen eingeblendet wird, klappen Sie den Abschnitt **Material** auf, und ändern Sie die **Material Import Method** (Methode für den Materialimport) in **Do Not Create Material** (Kein Material erstellen).
    * Wählen Sie **Import All** (Alle importieren) aus.

![FBX-Importoptionen](images/unreal-uxt/2-nocreatemat.PNG)

Mehr müssen Sie für die Medienobjekte nicht unternehmen. In der nächsten Reihe von Aufgaben befassen Sie sich mit dem Erstellen der Bausteine der Anwendung mithilfe von Blaupausen.

## <a name="adding-blueprints"></a>Hinzufügen von Blaupausen

1. Wählen Sie im **Inhaltsbrowser** die Optionen **Add New > New Folder** (Neu hinzufügen > Neuer Ordner) aus, und benennen Sie ihn **Blueprints** (Blaupausen). 

> [!NOTE]
> Falls Sie [Blaupausen](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html) noch nicht kennen – bei ihnen handelt es sich um spezielle Medienobjekte, die eine knotenbasierte Oberfläche bieten, über die neue Arten von Akteuren und Ereignissen auf der Skriptebene erstellt werden können. 

2. Doppelklicken Sie auf den Ordner **Blaupausen**, klicken Sie dann mit der rechten Maustaste, und wählen Sie **Blueprint Class** (Blaupausenklasse) aus.         
    * Wählen Sie **Actor** (Akteur) aus, und benennen Sie die Blaupause **Board** (Brett). 

![Auswählen einer übergeordneten Klasse für Ihre Blaupause](images/unreal-uxt/2-bpparent.PNG)

Die neue **Board**-Blaupause wird nun im Ordner **Blueprints** (Blaupausen) angezeigt, wie im folgenden Screenshot zu sehen. 

![Die neue Blaupause „Board“](images/unreal-uxt/2-bpboard.PNG)

Sie sind jetzt bereit, den erstellten Objekten Materialien hinzuzufügen.

## <a name="working-with-materials"></a>Arbeiten mit Materialien
Die Objekte, die Sie erstellt haben, sind standardgrau, was visuell nicht viel hermacht. Das Hinzufügen von Materialien und Gittermodellen zu Ihren Objekten ist der letzte Satz von Aufgaben in diesem Tutorial.

1. Doppelklicken Sie auf **Board**, um den Blaupausen-Editor zu öffnen. 

2. Wählen Sie im Bereich **Components** (Komponenten) **Add Component > Scene** (Komponente hinzufügen > Szene) aus, und benennen Sie sie **Root** (Stamm). Beachten Sie, dass **Root** im Screenshot unten als untergeordnetes Element von **DefaultSceneRoot** dargestellt ist:

![Ersetzen des Stammordners in Blaupausen](images/unreal-uxt/2-root-blueprint.PNG)


3. Klicken Sie, und ziehen Sie **Root** auf **DefaultSceneRoot**, um es zu ersetzen und die Kugel im Viewport zu entfernen. 

![Ersetzen des Stamms](images/unreal-uxt/2-root.PNG)


4. Wählen Sie im Bereich **Components** (Komponenten) **Add Component > Static Mesh** (Komponente hinzufügen > Statisches Gittermodell) aus, und benennen Sie es **SM_Board**. Es wird als untergeordnetes Objekt unter **Root** angezeigt.

![Hinzufügen eines statischen Gitters](images/unreal-uxt/2-sm-board.PNG)

4. Wählen Sie **SM_Board** aus, scrollen Sie im Bereich **Details** nach unten zum Abschnitt **Static Mesh** (Statisches Gittermodell), und wählen Sie in der Dropdownliste **ChessBoard** aus. 

![Das Schachbrettgitter im Viewport](images/unreal-uxt/2-sm-board-view.PNG)

5.  Klappen Sie, wiederum im Bereich **Details** den Abschnitt **Materials** (Materialien) auf, und wählen Sie in der Dropdownliste **Create New Asset > Material** (Neues Medienobjekt erstellen > Material) aus. 
    * Benennen Sie das Material **M_ChessBoard**, und speichern Sie es im Ordner **ChessAssets**. 

![Erstellen eines neuen Materials](images/unreal-uxt/2-newmat.PNG)

6.  Doppelklicken Sie auf das Bild des Materials **M_ChessBoard**, um den Material-Editor zu öffnen. 

![Geöffneter Material-Editor](images/unreal-uxt/2-material-editor.PNG)

7. Klicken Sie im Material-Editor mit der rechten Maustaste, und suchen Sie nach **Texture Sample** (Texturbeispiel). 
    * Klappen Sie im Bereich **Details** den Abschnitt **Material Expression Texture Base** (Texturbasis für Materialausdruck) auf, und legen Sie **Texture** (Textur) auf **ChessBoard_Albedo** fest. 
    * Ziehen Sie den **RGB**-Ausgabepin auf den Basisfarbpin von **M_ChessBoard**. 

![Festlegen der Basisfarbe](images/unreal-uxt/2-boardalbedomat.PNG)

8.  Wiederholen Sie den vorherigen Schritt weitere 4 Mal, um vier weitere Knoten **Texture Sample** (Texturbeispiel) mit den folgenden Einstellungen zu erstellen:
    * Legen Sie **Texture** (Textur) auf **ChessBoard_AO** fest, und verknüpfen Sie **RGB** mit dem Pin **Ambient Occlusion** (Umgebungsverdeckung).
    * Legen Sie **Texture** (Textur) auf **ChessBoard_Metal** fest, und verknüpfen Sie **RGB** mit dem Pin **Metallic** (Metallisch). 
    * Legen Sie **Texture** (Textur) auf **ChessBoard_Normal** fest, und verknüpfen Sie **RGB** mit dem Pin **Normal**.
    * Legen Sie **Texture** (Textur) auf **ChessBoard_Rough** fest, und verknüpfen Sie **RGB** mit dem Pin **Roughness** (Rauheit). 
    * Klicken Sie auf **Speichern**. 

![Verbinden der restlichen Texturen](images/unreal-uxt/2-boardmat.PNG)

Vergewissern Sie sich, dass Ihre Materialeinrichtung wie der Screenshot oben aussieht, bevor Sie fortfahren.

## <a name="populating-the-scene"></a>Auffüllen der Szene
Wenn Sie zur Blaupause **Board** (Brett) zurückkehren, sehen Sie, dass Ihr soeben erstelltes Material übernommen wurde. Jetzt müssen Sie nur noch die Szene einrichten! Ändern Sie zunächst die folgenden Eigenschaften, um sicherzustellen, dass das Brett eine sinnvolle Größe aufweist und in richtigen Winkel in der Szene platziert wird:
1.  Legen Sie **Scale** (Maßstab) auf **(0,05, 0,05, 0,05)** und **Z Rotation** (Z-Drehung) auf **90** fest. 
    * Klicken Sie in der oberen Symbolleiste auf **Compile** (Kompilieren), dann auf **Save** (Speichern), und kehren Sie zum Hauptfenster zurück. 

![Schachbrett mit angewendetem Material](images/unreal-uxt/2-chessboard.PNG)

2.  Klicken Sie mit der rechten Maustaste auf **Cube > Edit > Delete** (Würfel > Bearbeiten > Löschen), und ziehen Sie **Board** (Brett) aus dem **Content Browser** (Inhaltsbrowser) in den Viewport. 
    * Legen Sie **Location** (Position) auf **X = 80**, **Y = 0** und **Z = -20** fest. 

3.  Wählen Sie die Schaltfläche **Play** (Wiedergabe) aus, um das neue Brett im Level anzuzeigen. Drücken Sie **ESC**, um zum Editor zurückzukehren. 

Führen Sie nun die folgenden Schritte aus, um eine Schachfigur zu erstellen, so wie Sie das Brett erstellt haben:

1. Wechseln Sie zum Ordner **Blueprints** (Blaupausen), klicken Sie mit der rechten Maustaste auf **Blueprint Class** (Blaupausenklasse), wählen Sie sie aus, und wählen Sie dann **Actor** (Akteur) aus. Nennen Sie den Akteur **WhiteKing**.

2. Doppelklicken Sie auf **WhiteKing**, um ihn im Blaupausen-Editor zu öffnen, wählen Sie **Add Component > Scene** (Komponente hinzufügen > Szene) aus, und benennen Sie sie **Root** (Stamm). 
    * Ziehen Sie **Root** auf **DefaultSceneRoot**, um sie zu ersetzen. 

3. Klicken Sie auf **Add Component > Static Mesh** (Komponente hinzufügen > Statisches Gittermodell), und benennen Sie es **SM_King**. 
    * Legen Sie im Detailbereich die Option **Static Mesh** (Statisches Gittermodell) auf **Chess_King** und die Option **Material** auf ein neues Material mit dem Namen **M_ChessWhite** fest. 

4. Öffnen Sie **M_ChessWhite** im Material-Editor, und verbinden Sie die folgenden **Texture Sample**-Knoten (Texturbeispiel) in folgender Weise:
   * Legen Sie **Textur** auf **ChessWhite_Albedo** fest, und verknüpfen Sie **RGB** mit dem Pin **Basisfarbe**.
    * Legen Sie **Texture** (Textur) auf **ChessWhite_AO** fest, und verknüpfen Sie **RGB** mit dem Pin **Ambient Occlusion** (Umgebungsverdeckung).
    * Legen Sie **Texture** (Textur) auf **ChessWihte_Metal** fest, und verknüpfen Sie **RGB** mit dem Pin **Metallic** (Metallisch). 
    * Legen Sie **Texture** (Textur) auf **ChessWhite_Normal** fest, und verknüpfen Sie **RGB** mit dem Stift **Normal**.
    * Legen Sie **Texture** (Textur) auf **ChessWhite_Rough** fest, und verknüpfen Sie **RGB** mit dem Pin **Roughness** (Rauheit). 
    * Klicken Sie auf **Speichern**. 

Ihr **M_ChessKing**-Material sollte wie die folgende Abbildung aussehen, bevor Sie fortfahren.

![Erstellen des Materials für den König (Schachfigur)](images/unreal-uxt/2-chesskingmat.PNG)

Sie haben es fast geschafft, wir müssen jetzt nur noch der Szene die neue Schachfigur hinzufügen: 

1. Öffnen Sie die **WhiteKing**-Blaupause, ändern Sie den **Scale** (Maßstab) in **(0,05, 0,05, 0,05)** und **Z Rotation** (Z_Drehung) in **90**.
    * Kompilieren und speichern Sie die Blaupause, und kehren Sie anschließend wieder zum Hauptfenster zurück. 

2.  Ziehen Sie **WhiteKing** in den Viewport, wechseln Sie zum **World Outliner** (Gliederungs-Editor), und ziehen Sie **WhiteKing** auf **Board**, um ihn zum untergeordneten Objekt zu machen.

![Gliederungs-Editor](images/unreal-uxt/2-child.PNG)

3.  Legen Sie im Bereich **Details** unter **Transform** (Transformieren) die **Location** (Position) von **WhiteKing** auf **X = -26**, **Y = 4** und **Z = 0** fest.

Das wäre geschafft! Wählen Sie **Play** (Wiedergabe) aus, um Ihr aufgefülltes Level in Aktion zu sehen, und drücken Sie **Esc**, wenn Sie die Szene beenden möchten. Sie haben eine Menge gelernt, indem Sie lediglich ein einfaches Projekt erstellt haben, aber jetzt sind Sie bereit, um mit dem nächsten Teil der Reihe fortzufahren: Einrichten für Mixed Reality. 

[Nächster Abschnitt: 3. Einrichten Ihres Projekts für Mixed Reality](unreal-uxt-ch3.md)