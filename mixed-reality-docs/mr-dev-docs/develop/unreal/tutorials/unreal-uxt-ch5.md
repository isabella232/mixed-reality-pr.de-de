---
title: 5. Hinzufügen einer Taste und Zurücksetzen von Figurenpositionen
description: Teil 5 von 6 einer Tutorialreihe zum Erstellen einer Schach-App mit der Unreal Engine 4 und dem UX Tools-Plug-In des Mixed Reality-Toolkits
author: hferrone
ms.author: v-hferrone
ms.date: 11/18/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Tutorial, Erste Schritte, MRTK, UXT, UX-Tools, Dokumentation, Mixed Reality-Headset Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: 5f37599e43147a79c8bdd9f0c28e0b23f163c39fa833d3835650c28deb4f0898
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226721"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a>5. Hinzufügen einer Taste und Zurücksetzen von Figurenpositionen

Im vorhergehenden Tutorial haben Sie den Pawn- und Manipulatorkomponenten Handinteraktionsakteure auf dem Schachbrett hinzugefügt, um eine Interaktion zu ermöglichen. In diesem Abschnitt verwenden Sie weiterhin das UX-Tools-Plug-In des Mixed Reality Toolkit, um Ihre Schach-App um neue Funktionen sowie Akteurverweisen in Blaupausen zu erweitern. Am Ende dieses Abschnitts können Sie die Mixed Reality-App verpacken und auf einem Gerät oder in einem Emulator bereitstellen.

## <a name="objectives"></a>Ziele

* Hinzufügen einer interaktiven Schaltfläche
* Erstellen einer Funktion zum Zurücksetzen der Position der Figuren
* Verknüpfen der Schaltfläche, damit die Funktion beim Tippen auf die Schaltfläche ausgelöst wird

## <a name="creating-a-reset-function"></a>Erstellen einer Funktion zum Zurücksetzen

Ihre erste Aufgabe besteht darin, eine Funktionsblaupause zu erstellen, mit der die Position einer Schachfigur auf die ursprüngliche Position in der Szene zurückgesetzt wird.

1.  Öffnen Sie **WhiteKing**, wählen Sie das Symbol **+** unter **My Blueprint** (Meine Blaupause) neben dem Abschnitt **Functions** (Funktionen) aus, und geben Sie ihr den Namen **Reset Location** (Position zurücksetzen).

2.  Ziehen Sie die Ausführung aus **Reset Location** auf das Blaupausenraster, um den Knoten **SetActorRelativeTransform** zu erstellen.
    * Durch diese Funktion wird die Transformation (Position, Rotation und Skalierung) eines Akteurs relativ zum übergeordneten Element festgelegt. Sie verwenden diese Funktion, um die Position des Königs auf dem Schachbrett zurückzusetzen, auch wenn sich dieses nicht mehr an seiner ursprünglichen Position befindet.

3. Klicken Sie mit der rechten Maustaste auf eine Stelle im Ereignisdiagramm, wählen Sie **Make Transform** (Transformation erstellen) aus, und ändern Sie **Location** (Position) in **X = -26**, **Y = 4**, **Z = 0**.
    * Verbinden Sie **Return Value** (Rückgabewert) mit dem Pin **New Relative Transform** (Neue relative Transformation) in **SetActorRelativeTransform**.

![Funktion zum Zurücksetzen der Position](images/unreal-uxt/5-function.PNG)

**Kompilieren** und **speichern** Sie das Projekt, bevor Sie zum Hauptfenster zurückkehren.


## <a name="adding-a-button"></a>Hinzufügen einer Schaltfläche

Nachdem die Funktion nun ordnungsgemäß eingerichtet wurde, besteht die nächste Aufgabe darin, eine Schaltfläche zu erstellen, die ausgelöst wird, sobald sie berührt wird.

1.  Klicken Sie auf **Add New > Blueprint Class** (Neu hinzufügen > Blaupausenklasse), erweitern Sie den Abschnitt **All Classes** (Alle Klassen), und suchen Sie nach **UxtPressableButtonActor**.
    * Geben Sie Ihr den Namen **ResetButton**, und doppelklicken Sie darauf, um die Blaupause zu öffnen.

![Erstellen Sie die neue Blaupause als Unterklasse der HoloLens 2-Formatvorlagen-Schaltfläche](images/unreal-uxt/5-subclass.PNG)

2. Vergewissern Sie sich, dass **ResetButton(self)** im Bereich **Komponenten** ausgewählt ist. Navigieren Sie im Bereich **Details** zum Abschnitt **Button** (Schaltfläche). Ändern Sie das standardmäßige **Button Label** (Schaltflächenbezeichnung), erweitern Sie den Abschnitt **Schaltflächen-Symbolpinsel**, und drücken Sie die Schaltfläche **Open Icon Brush Editor** (Symbolpinsel-Editor öffnen).

![Festlegen von Bezeichnung und Symbol für die Schaltfläche](images/unreal-uxt/5-buttonconfig.PNG)

Der Symbolpinsel-Editor wird geöffnet. Mit diesem können Sie ein neues Symbol für Ihre Schaltfläche auswählen.

![Auswählen eines Symbols für die Schaltfläche](images/unreal-uxt/5-iconbrusheditor.PNG)

Es gibt zahlreiche weitere Einstellungen, die Sie anpassen können, um Ihre Schaltfläche zu konfigurieren. Weitere Informationen über die UXT-Komponente „Drückbare Schaltfläche“ finden Sie in der [Dokumentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PressableButton.html).

3. Klicken Sie im Bereich **Komponenten** auf **ButtonComponent (Inherited)** (ButtonComponent (Geerbt)), und scrollen Sie im Bereich **Details** zum Abschnitt **Events** (Ereignisse).
    * Klicken Sie neben **On Button Pressed** (Beim Drücken der Schaltfläche) auf das grüne **+** , um dem Ereignisdiagramm ein Ereignis hinzuzufügen, das aufgerufen wird, wenn die Schaltfläche betätigt wird.

Hier soll die Funktion **Reset Location** für **WhiteKing** aufgerufen werden. Dazu ist ein Verweis auf den Akteur **WhiteKing** im Level erforderlich.

4.  Navigieren Sie im Bereich **My Blueprint** (Meine Blaupause) zum Abschnitt **Variables** (Variablen), klicken Sie auf die Schaltfläche **+** , und geben Sie der Variablen den Namen **WhiteKing**.
    * Wählen Sie im Bereich **Details** die Dropdownliste neben **Variable Type** (Variablentyp) aus, suchen Sie nach **WhiteKing**, und wählen Sie **Object Reference** (Objektverweis) aus.
    * Aktivieren Sie das Kontrollkästchen neben **Instanz bearbeitbar**, sodass die Variable auf dem Hauptlevel festgelegt werden kann.

![Erstellen einer Variablen](images/unreal-uxt/5-var.PNG)

5.  Ziehen Sie die Variable „WhiteKing“ aus **My Blueprint > Variables** (Meine Blaupause > Variablen) auf das Ereignisdiagramm für die Schaltfläche „Reset“, und wählen Sie **Get WhiteKing** aus.

## <a name="firing-the-function"></a>Auslösen der Funktion

Jetzt muss nur noch die Funktion zum Zurücksetzen ausgelöst werden, wenn die Schaltfläche betätigt wird.

1.  Ziehen Sie den Ausgabepin von „WhiteKing“, und lassen Sie ihn los, um einen neuen Knoten zu platzieren. Wählen Sie die Funktion **Reset Location** (Position zurücksetzen) aus. Ziehen Sie abschließend den ausgehenden Ausführungspin von **On Button Pressed** (Beim Drücken des Schalters) zum eingehenden Ausführungspin von **Reset Location** (Position zurücksetzen). **Kompilieren** und **speichern** Sie die Blaupause „ResetButton“, und kehren Sie anschließend zum Hauptfenster zurück.

![Aufrufen der Funktion zum Zurücksetzen der Position über „On Button Pressed“ (Beim Drücken des Schalters)](images/unreal-uxt/5-callresetloc.PNG)

2.  Ziehen Sie **ResetButton** in den Viewport, und legen Sie die Position auf **X = 50**, **Y = -25** und **Z = 10** fest. Legen Sie die Drehung auf **Z = 180** fest. Legen Sie unter **Default** (Standard) den Wert der Variablen **WhiteKing** auf **WhiteKing** fest.

![Festlegen der Variablen](images/unreal-uxt/5-buttonlevel.PNG)

Führen Sie die App aus, verschieben Sie die Schachfigur an eine neue Position, und tippen Sie auf Ihre Schaltfläche im HoloLens 2-Stil, um die Logik zum Zurücksetzen auszuführen.

Sie verfügen nun über eine Mixed Reality-App mit einer interaktionsfähigen Schachfigur und einem interaktionsfähigen Schachbrett sowie mit einer funktionsfähigen Schaltfläche, die die Position der Schachfigur zurücksetzt. Die bis hier hin fertige App finden Sie im [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp)-Repository. Sie können gerne noch einen Schritt weitergehen und die restlichen Schachfiguren einrichten, sodass das gesamte Schachbrett zurückgesetzt wird, wenn die Schaltfläche zum Zurücksetzen betätigen.

![Fertige Szene im Viewport](images/unreal-uxt/5-endscene.PNG)

Sie können nun mit dem letzten Abschnitt dieses Tutorials fortfahren, in dem Sie erfahren, wie Sie die App verpacken und auf einem Gerät oder in einem Emulator bereitstellen.

> [!IMPORTANT]
> An diesem Punkt sollten Sie Ihr Projekt mit den empfohlenen **[Unreal-Leistungseinstellungen](../performance-recommendations-for-unreal.md)** aktualisieren, bevor Sie Ihre Anwendung auf einem Gerät oder Emulator bereitstellen.

[Nächster Abschnitt: 6. Verpacken und Bereitstellen auf einem Gerät oder Emulator](unreal-uxt-ch6.md)
