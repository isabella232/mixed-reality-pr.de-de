---
title: 'MRTK-Tutorials: 4. Positionieren von Objekten in der Szene'
description: In diesem Kurs erfahren Sie, wie Sie Objekte in der Szene positionieren und wie Sie das Mixed Reality Toolkit (MRTK) verwenden, um Objekte in einem Raster zu organisieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, MRTK, Mixed Reality Toolkit, UWP, Solver, Rasterobjektsammlung
ms.localizationpriority: high
ms.openlocfilehash: b21f2833067c3496febcf5bdd1cfffe491597e9083845b18e9c220c75d3e7cee
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228004"
---
# <a name="4-positioning-objects-in-the-scene"></a>4. Positionieren von Objekten in der Szene

## <a name="overview"></a>Übersicht

In diesem Tutorial positionieren Sie die bereitgestellten Objekte aus den Medienobjekten für das Tutorial in der Szene.

## <a name="objectives"></a>Ziele

* Erfahren, wie Objekte in der Szene positioniert werden
* Erfahren, wie die Rasterobjektsammlung des MRTK verwendet wird

## <a name="importing-the-textmeshpro-essential-resources"></a>Importieren der TextMeshPro Essential-Ressourcen
Die TextMeshPro Essential-Ressourcen sind für die Benutzeroberflächenelemente des MRTK erforderlich. Wählen Sie im Unity-Menü **Window** > **TextMeshPro** > **Import TMP Essential Resources** (Fenster > TextMeshPro > TMP Essential Resources importieren) aus, um das Importfenster für Unity-Pakete zu öffnen:

![Unity: Menüpfad für „Import TMP Essential Resources“](images/mr-learning-base/base-02-section3-step1-1.png)

Klicken Sie im Import Unity Package-Fenster (Unity-Paket importieren) auf die Schaltfläche **All** (Alle), um sicherzustellen, dass alle Assets ausgewählt sind, und klicken Sie dann auf die Schaltfläche **Import** (Importieren), um die Assets zu importieren:

![Unity-Fenster für Importieren von „TMP Essential Resources“](images/mr-learning-base/base-02-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>Importieren der Tutorialressourcen

Laden Sie das folgende benutzerdefinierte Unity-Paket herunter. Dieses Paket enthält 3D-Ressourcen wie „Mars Rover“, die wir in diesem Tutorial verwenden werden.

* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.5.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage)

Wählen Sie zum Importieren eines benutzerdefinierten Unity-Pakets im Unity-Menü **Assets** > **Import Package** > **Custom Package...** (Assets > Paket importieren > Benutzerdefiniertes Paket...) aus, um das Fenster zum Importieren von Paketen zu öffnen:

![Importieren eines benutzerdefinierten Pakets](images/mr-learning-base/base-02-section7-step1-1.png)

Wählen Sie im Fenster „Import package...“ (Paket importieren...) das heruntergeladene Paket **MRTK:HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage** aus, und klicken Sie auf die Schaltfläche „Open“ (Öffnen):

![Auswählen eines Ressourcenpakets](images/mr-learning-base/base-02-section7-step1-2.png)

Klicken Sie im Import Unity Package-Fenster (Unity-Paket importieren) auf die Schaltfläche All (Alle), um sicherzustellen, dass alle Assets ausgewählt sind, und klicken Sie dann auf die Schaltfläche Import (Importieren), um die Assets zu importieren:

![Auswählen aller zu importierenden Ressourcen](images/mr-learning-base/base-02-section7-step1-3.png)

Nach dem Importieren der Tutorialressourcen sollte Ihr Projektfenster ähnlich wie die folgende Abbildung aussehen:

![Unity-Projektfenster nach dem Importieren von Ressourcen](images/mr-learning-base/base-02-section7-step1-4.png)

## <a name="creating-the-parent-object"></a>Erstellen des übergeordneten Objekts

Klicken Sie im Hierarchiefenster mit der rechten Maustaste auf eine leere Stelle, und wählen Sie **Create Empty** (Leer erstellen) aus, um Ihrer Szene ein leeres Objekt hinzuzufügen:

![Unity-Popupkontextemenü „Create Empty“](images/mr-learning-base/base-04-section1-step1-1.png)

> [!TIP]
> Um Ihr Szenen- und Spielfenster nebeneinander anzuzeigen, wie in der Abbildung oben dargestellt, ziehen Sie das Spielfenster rechts neben das Szenenfenster. Weitere Informationen zum Anpassen Ihres Arbeitsbereichs finden Sie in der Unity-Dokumentation zum <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Anpassen Ihres Arbeitsbereichs</a>.

Klicken Sie mit der rechten Maustaste auf das neu erstellte Objekt, wählen Sie **Umbenennen** aus, und ändern Sie den Namen in **RoverExplorer**:

![Unity-Popupkontextemenü „Rename“](images/mr-learning-base/base-04-section1-step1-2.png)

Konfigurieren Sie bei immer noch ausgewähltem RoverExplorer-Objekt im Inspektorfenster die Komponente **Transform** (Transformieren) wie folgt:

* **Position**: X = 0, Y = -0,6, Z = 2
* **Drehung**: X = 0, Y = 0, Z = 0
* **Skalierung**: X = 1, Y = 1, Z = 1

![Unity mit ausgewähltem und positioniertem RoverExplorer-Objekt](images/mr-learning-base/base-04-section1-step1-3.png)

> [!NOTE]
> Die Kamera stellt den Kopf des Benutzers dar und befindet sich am Ursprung, X = 0, Y = 0, Z = 0. Im Allgemeinen entspricht 1 Einheit in Unity ungefähr einem Meter in der physischen Umgebung. Es gibt jedoch Ausnahmen, z. B. wenn Objekte untergeordnete Objekte von skalierten Objekten sind. Im Szenario oben ist der RoverExplorer 2 Meter vor und 0,6 Meter unterhalb des Kopfs des Benutzers positioniert.

## <a name="adding-the-tutorial-prefabs"></a>Hinzufügen der Prefabs für das Tutorial

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.GEttingStarted** > **Prefabs**:

![Unity-Projektfenster mit ausgewähltem Ordner „Prefabs“](images/mr-learning-base/base-04-section2-step1-1.png)

> [!TIP]
> Ein <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">Prefab</a> ist ein vorkonfiguriertes GameObject, das als Unity-Ressource gespeichert ist und durchgängig im Projekt verwendet werden kann.

Klicken Sie im Projektfenster auf das **Table**-Prefab (Tabelle), und ziehen Sie es aus dem Projektfenster auf das **RoverExplorer**-Objekt, um es zu einem untergeordneten Objekt des RoverExplorer-Objekts zu machen. Konfigurieren Sie dann im Inspektorfenster die Komponente **Transform** (Transformieren) wie folgt:

* **Position**: X = 0, Y = -0,005, Z = 0
* **Drehung**: X = 0, Y = 0, Z = 0
* **Skalierung**: X = 1,2, Y = 0,01, Z = 1.2

![Unity mit neu hinzugefügtem, ausgewähltem und positioniertem Table-Prefab](images/mr-learning-base/base-04-section2-step1-2.png)

> [!TIP]
> Um Ihre Szene so anzuzeigen, wie Sie in der Abbildung oben dargestellt ist, verwenden Sie den <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, der sich in der oberen rechten Ecke des Szenenfensters befindet, um den Betrachtungswinkel so anzupassen, dass er entlang der vorwärtsgerichteten Z-Achse verläuft, doppelklicken Sie auf das MixedRealityPlayspace-Objekt, um den Fokus auf die Kamera zu legen, und zoomen Sie nach Bedarf herein.

Klicken Sie im Projektfenster auf das **RoverAssembly**-Prefab, und ziehen Sie es auf das **RoverExplorer**-Objekt, um es zu einem untergeordneten Objekt des RoverExplorer-Objekts zu machen. Konfigurieren Sie dann im Inspektorfenster die Komponente **Transform** (Transformieren) wie folgt:

* **Position**: X = -0,1, Y = 0, Z = 0
* **Drehung**: X = 0, Y = -135, Z = 0
* **Skalierung**: X = 1, Y = 1, Z = 1

![Unity mit neu hinzugefügtem, ausgewähltem und positioniertem RoverAssembly-Prefab](images/mr-learning-base/base-04-section2-step1-3.png)

## <a name="organizing-objects-in-a-collection"></a>Organisieren von Objekten in einer Sammlung

Klicken Sie im Hierarchiefenster mit der rechten Maustaste auf das **RoverExplorer**-Objekt, und wählen Sie **Create Empty** (Leer erstellen) aus, um ein leeres Objekt als untergeordnetes Objekt des RoverExplorers hinzuzufügen, benennen Sie das Objekt **RoverParts**, und konfigurieren Sie die Komponente **Transform** (Transformieren) wie folgt:

* **Position**: X = 0, Y = 0,06, Z = 0
* **Drehung**: X = 0, Y = 90, Z = 0
* **Skalierung**: X = 1, Y = 1, Z = 1

![Unity mit neu erstelltem, ausgewähltem und positioniertem RoverParts-Objekt](images/mr-learning-base/base-04-section3-step1-1.png)

Wählen Sie im Hierarchiefenster mithilfe von „RoverExplorer > RoverAssembly > RoverModel > **Parts**“ (...> Teile) alle untergeordneten Objekte aus, klicken Sie mit der rechten Maustaste darauf, und wählen Sie **Duplicate** (Duplizieren) aus, um eine Kopie aller Teile zu erstellen:

![Unity mit allen Teilen ausgewählt und Popupkontextmenü „Duplicate“](images/mr-learning-base/base-04-section3-step1-2.png)

> [!TIP]
> Um mehrere angrenzende Objekte auszuwählen, drücken Sie die UMSCHALTTASTE, und halten Sie sie gedrückt, während Sie die Maus verwenden, um das erste und das letzte Objekt auszuwählen.

Klicken Sie auf die noch ausgewählten neu duplizierten untergeordneten Teileobjekte, und ziehen Sie sie auf das **RoverParts**-Objekts, um sie als untergeordnete Objekte des RoverParts-Objekts festzulegen:

![Unity mit neu duplizierten Teilen als untergeordnete Elemente des RoverParts-Objekts](images/mr-learning-base/base-04-section3-step1-3.png)

Um das Arbeiten mit Ihrer Szene zu vereinfachen, klicken Sie im Hierarchiefenster auf das **Augensymbol** links neben dem Objekt, um die **Scene Visibility** (Sichtbarkeit in der Szene) für das **RoverAssembly**-Objekt auszuschalten. Dadurch wird das Objekt im Szenenfenster ausgeblendet, ohne Auswirkungen auf seine Sichtbarkeit im Spiel:

![Unity mit deaktivierter Sichtbarkeit der RoverAssembly-Szene](images/mr-learning-base/base-04-section3-step1-4.png)

> [!TIP]
> Mehr zu den Steuerelementen für die Sichtbarkeit in der Szene und ihre Verwendung zum Optimieren Ihrer Szenenansicht und Ihres Workflows finden Sie in der Unity-Dokumentation zu <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> (Sichtbarkeit in der Szene).

Bereinigen Sie im Hierarchiefenster die Namen der untergeordneten RoverParts-Objekte, indem Sie die angefügte **(1)** durch **_Part** ersetzen:

![Unity mit bereinigtem Namen duplizierter Teile](images/mr-learning-base/base-04-section3-step1-5.png)

Wählen Sie im Hierarchiefenster das **RoverParts**-Objekt aus, klicken Sie dann im Inspektorfenster auf die Schaltfläche **Add Component** (Komponente hinzufügen), suchen Sie nach **GridObjectCollection**, und wählen Sie sie aus, um die GridObjectCollection-Komponente zum RoverParts-Objekt hinzuzufügen:

![Unity-Objekt „RoverParts“ mit dem Hinzufügen der Komponente „Grid Object Collection“ in Bearbeitung](images/mr-learning-base/base-04-section3-step1-6.png)

Konfigurieren Sie die Werte der **GridObjectCollection**-Komponente wie folgt:

* **Sortierungstyp**: Alphabetisch
* **Layout**: Horizontal
* **Zellenbreite**: 0,25
* **Abstand vom übergeordneten Element**: 0,38

![Unity mit konfigurierter GridObjectCollection-Komponente](images/mr-learning-base/base-04-section3-step1-7.png)

Klicken Sie dann auf die Schaltfläche **Update Collection** (Sammlung aktualisieren), um die Position der untergeordneten RoverParts-Objekte zu aktualisieren:

![Unity mit angewendeter GridObjectCollection-Komponente](images/mr-learning-base/base-04-section3-step1-8.png)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie gelernt, wie Objekte relativ zum Benutzer in der Szene positioniert werden und wie das Feature Rasterobjektsammlung des MRTK verwendet wird, um Objekte in einer Sammlung zu organisieren.

> [!div class="nextstepaction"]
>[Nächstes Tutorial: 5. Erstellen dynamischer Inhalte mithilfe von Solvern](mr-learning-base-05.md)
