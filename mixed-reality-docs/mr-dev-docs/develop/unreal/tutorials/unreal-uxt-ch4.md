---
title: 4. Interaktives Gestalten der Szene
description: Teil 4 von 6 einer Tutorialreihe zum Erstellen einer einfachen Schach-App mit der Unreal Engine 4 und dem UX Tools-Plug-In des Mixed Reality-Toolkits
author: hferrone
ms.author: v-hferrone
ms.date: 08/18/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, Tutorial, Erste Schritte, MRTK, UXT, UX-Tools, Dokumentation, Mixed Reality-Headset Windows Mixed Reality-Headset, Virtual Reality-Headset
ms.openlocfilehash: dc17b878255a3d6a8e0efc3a4c5bd7aa7d57373d
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679849"
---
# <a name="4-making-your-scene-interactive"></a>4. Interaktives Gestalten der Szene

## <a name="overview"></a>Übersicht

Im vorhergehenden Tutorial haben Sie „ARSession“, „Pawn“ und den Spielemodus hinzugefügt, um die Einrichtung der Schach-App für Mixed Reality durchzuführen. In diesem Abschnitt wird das Open Source-Plug-In [Mixed Reality Toolkit UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal) behandelt, das Tools enthält, um die Interaktion mit der Szene zu ermöglichen. Am Ende dieses Abschnitts lassen sich die Schachfiguren über Benutzereingaben verschieben. 

## <a name="objectives"></a>Ziele

* Herunterladen des UX Tools-Plug-Ins des Mixed Reality-Toolkits 
* Hinzufügen von Handinteraktionsakteuren für Ihre Fingerspitzen
* Erstellen und Hinzufügen von Manipulatoren zu Objekten in der Szene
* Überprüfen des Projekts mithilfe der Eingabesimulation

## <a name="downloading-the-mrtk-ux-tools-plugin"></a>Herunterladen des MRTK UX Tools-Plug-Ins
Bevor Sie mit Benutzereingaben arbeiten können, müssen Sie das Plug-In dem Projekt hinzufügen.

1.  Navigieren Sie auf der Mixed Reality UX Tools-[Versionsseite](https://github.com/microsoft/MixedReality-UXTools-Unreal/releases) auf GitHub zur UX Tools für Unreal-Version 0.9.0, und laden Sie **UXTools.0.9.0.zip** herunter. Entzippen Sie die Datei.

2.  Erstellen Sie im Stammordner des Projekts einen neuen Ordner mit dem Namen **Plugins**. Kopieren Sie das entzippte UXTools-Plug-In in diesen Ordner, und starten Sie den Unreal-Editor neu. 

![Erstellen eines Plug-In-Ordners für das Projekt](images/unreal-uxt/4-plugins.PNG)

3.  Das UXTools-Plug-In besitzt einen Ordner „Content“ mit den Unterordnern **Buttons** (Schaltflächen), **Input Simulation** (Eingabesimulation) und **Pointers** (Zeiger) sowie den Ordner „C++ Classes“ mit zusätzlichem Code.  

> [!NOTE]
> Wenn im **Inhaltsbrowser** der Abschnitt **UXTools Content** nicht angezeigt wird, klicken Sie auf **View Options > Show Plugin Content** (Ansichtsoptionen > Plug-In-Inhalt anzeigen). 

![Anzeigen des Plug-In-Inhalts](images/unreal-uxt/4-showplugincontent.PNG)

Sobald das Plug-In installiert ist, können Sie die Tools verwenden. Beginnen Sie dabei mit den Handinteraktionsakteuren.

## <a name="spawning-hand-interaction-actors"></a>Erzeugen von Handinteraktionsakteuren
Die Handinteraktion mit UX-Elementen erfolgt über Handinteraktionsakteure, die die Zeiger und Visuals für Nah- und Ferninteraktionen generieren und steuern.
- *Nahinteraktionen* werden durch Greifen von Elementen mit Zeigefinger und Daumen oder durch Anstupsen mit einem Fingertipp durchgeführt. 
- *Ferninteraktionen* werden durchgeführt, indem Sie einen Strahl von der virtuellen Hand zu einem Element ziehen und Zeigefinger und Daumen zusammendrücken.

Wenn Sie in diesem Fall **MRPawn** einen Handinteraktionsakteur hinzufügen, geschieht Folgendes:
- Den Fingerspitzen der Zeigefinger des Pawns wird ein Cursor hinzugefügt.
- Es werden freie Handeingabeereignisse bereitgestellt, die über den Pawn gesteuert werden können.
- Eingabeereignisse für die Ferninteraktion werden durch Handstrahlen ermöglicht, die von den Ballen der virtuellen Hände ausgehen.

Um sich mit diesen Konzepten vertraut zu machen, sollten Sie die [Dokumentation](https://github.com/microsoft/MixedReality-UXTools-Unreal/blob/public/0.9.x/Docs/HandInteraction.md) zu Handinteraktionen lesen, bevor Sie mit dem Tutorial fortfahren. 

Anschließend öffnen Sie die Blaupause **MRPawn**, und wechseln Sie zum **Ereignisdiagramm**. 

1. Ziehen Sie den Ausführungspin von **Event BeginPlay**, und lassen Sie ihn los, um einen neuen Knoten zu platzieren. 
    * Wählen Sie **Spawn Actor from Class** (Akteur aus Klasse erstellen) aus, klicken Sie auf die Dropdownliste neben dem Pin **Class**, und suchen Sie nach **Uxt Hand Interaction Actor** (UXT-Handinteraktionsakteur).  

2. Erzeugen Sie einen zweiten **Uxt Hand Interaction Actor**, wobei Sie **Right** (Rechts) für die **Hand** festlegen. Wenn das Ereignis beginnt, wird auf jeder Hand ein UXT-Handinteraktionsakteur erzeugt. 

Das **Ereignisdiagramm** sollte wie im folgenden Screenshot aussehen:

![Erzeugen von UXT-Handinteraktionsakteuren](images/unreal-uxt/4-spawnactor.PNG)

Beide UXT-Handinteraktionsakteure benötigen Besitzer und Ausgangspositionen für die Transformation. Die Ausgangstransformation spielt keine Rolle, da die Handinteraktionsakteure zu den virtuellen Händen springen, sobald Sie sichtbar sind (dieses Verhalten ist im UX Tools-Plug-In vorprogrammiert). Die Funktion `SpawnActor` erfordert jedoch eine Transformationseingabe, um einen Compilerfehler zu vermeiden. Verwenden Sie daher die Standardwerte. 

1. Ziehen Sie den Pin aus einer den Pins **Spawn Transform** (Transformation generieren), und lassen Sie ihn los, um einen neuen Knoten zu platzieren. 
    * Suchen Sie nach dem Knoten **Make Transform** (Transformation erstellen), und ziehen Sie dann den **Return Value** (Rückgabewert) auf **Spawn Transform** der anderen Hand, sodass beide **SpawnActor**-Knoten verbunden sind. 

2.  Klicken Sie im unteren Bereich beider **SpawnActor**-Knoten auf den **Pfeil nach unten**, um den Pin-**Owner** (Besitzer) anzuzeigen.    
    * Ziehen Sie den Pin aus einem der Pins vom Typ **Owner** (Besitzer), und lassen Sie ihn los, um einen neuen Knoten zu platzieren. 
    * Suchen Sie nach **self**, und wählen Sie die Variable **Get a reference to self** (Verweis auf Self abrufen) aus. Erstellen Sie dann einen Link zwischen dem **Self**-Objektverweisknoten und dem Pin **Owner** für den anderen Handinteraktionsakteur. 
3. Aktivieren Sie zu guter Letzt das Kontrollkästchen **Show Near Cursor on Grab Targets** (Nahcursor für Greifziele anzeigen) für beide Handinteraktionsakteure. Dadurch wird ein Cursor auf dem Greifziel angezeigt, wenn Ihr Zeigefinger sich ihm annähert, was es einfacher macht, die Position Ihres Fingers relativ zum Ziel zu sehen.
    * **Kompilieren** und **speichern** Sie Ihre Arbeit, und kehren Sie anschließend zum Hauptfenster zurück. 

Stellen Sie sicher, dass die Verbindungen dem folgenden Screenshot entsprechen, Sie können die Knoten jedoch zur besseren Übersichtlichkeit auf der Blaupause verschieben.

![Abschließen der Einrichtung der UXT-Handinteraktionsakteure](images/unreal-uxt/4-fingerptrs.PNG) 

Weitere Informationen zum Handinteraktionsakteur aus dem MRTK UX Tools-Plug-In finden Sie in der [Dokumentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/HandInteraction.html).

Mit den virtuellen Händen im Projekt können Objekte jetzt ausgewählt, aber immer noch nicht manipuliert werden. Die letzte Aufgabe vor dem Testen der App besteht darin, den Akteuren in der Szene Manipulatorkomponenten hinzuzufügen.

## <a name="attaching-manipulators"></a>Anfügen von Manipulatoren

Ein Manipulator ist eine Komponente, die auf eine freie Handeingabe reagiert und gegriffen, gedreht und verschoben werden kann. Durch Anwenden der Manipulatortransformation auf eine Akteurtransformation können direkte Akteurmanipulationen durchführt werden. 

1. Öffnen Sie die Blaupause **Board**, klicken Sie auf **Add Component** (Komponente hinzufügen), und suchen Sie im Bereich **Components** (Komponenten) nach **Uxt Generic Manipulator** (Allgemeiner UXT-Manipulator).

![Hinzufügen eines generischen Manipulators](images/unreal-uxt/4-addmanip.PNG)

2. Erweitern Sie im Bereich **Details** den Abschnitt **Generic Manipulator** (Allgemeiner Manipulator). Hier können Sie die einhändige oder zweihändige Manipulation, den Rotationsmodus und die Glättung festlegen. Wählen Sie die gewünschten Modi aus, und **kompilieren** und **speichern** Sie „Board“. 

![Festlegen des Modus](images/unreal-uxt/4-setrotmode.PNG)

3. Wiederholen Sie die Schritte oben für den Akteur **WhiteKing**.

Weitere Informationen zu den Manipulatorkomponenten aus dem MRTK UX Tools-Plug-In finden Sie in der [Dokumentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/Manipulator.html).

## <a name="testing-the-scene"></a>Testen der Szene
Fast geschafft! Jetzt können Sie die App mit den neuen virtuellen Händen und Benutzereingaben testen. Klicken Sie im Hauptfenster auf **Play**. Daraufhin sollten zwei Gitterhände aus dem MRTK UX Tools-Plug-In angezeigt werden, bei denen jeweils ein Handstrahl von den Handflächen ausgeht. Sie können die Hände und ihre Interaktionen wie folgt steuern:
- Halten Sie die **linke ALT-TASTE** gedrückt, um die **linke Hand** zu steuern, und die **linke UMSCHALTTASTE**, um die **rechte Hand** zu steuern. 
- Bewegen Sie die Maus, um die Hand zu verschieben. Scrollen Sie mit dem **Mausrad**, um die Hand **vor**- oder **zurück** zubewegen. 
- Klicken Sie zum **Zusammendrücken** mit der linken Maustaste und zum **Anstupsen** mit der mittleren Maustaste. 

> [!NOTE]
> Die Eingabesimulation funktioniert möglicherweise nicht, wenn mehrere Headsets an Ihren PC angeschlossen sind. Wen bei Ihnen Probleme auftreten, versuchen Sie, Ihre anderen Headsets zu trennen. 

![Simulierte Hände im Viewport](images/unreal-uxt/4-handsim.PNG)

Verwenden Sie die simulierten Hände, um den weißen König aufzunehmen, zu bewegen und abzustellen sowie um das Brett zu manipulieren. Experimentieren Sie sowohl mit der Nah- als auch mit der Ferninteraktion, und beachten Sie dabei, dass der Handstrahl verschwindet und durch einen Fingercursor an der Spitze des Zeigefingers ersetzt wird, wenn sich die Hand dem Schachbrett oder dem König so weit nähert, um direkt damit zu interagieren. 

Weitere Informationen zu den simulierten Händen aus dem MRTK UX Tools-Plug-In finden Sie in der [Dokumentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/InputSimulation.html).

Nachdem die virtuellen Hände jetzt mit Objekten interagieren können, können Sie mit dem nächsten Tutorial fortfahren, um Benutzeroberflächen und Ereignisse hinzuzufügen.

[Nächster Abschnitt: 5. Hinzufügen einer Schaltfläche und Zurücksetzen des Orts von Teilen](unreal-uxt-ch5.md)
