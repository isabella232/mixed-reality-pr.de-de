---
title: Erstellen der Benutzeroberfläche
description: In diesem Kurs erfahren Sie, wie Sie das Mixed Reality Toolkit (MRTK) verwenden, um statische und dynamische Benutzeroberflächen zu erstellen.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, MRTK, Mixed Reality Toolkit, UWP, Prefabs, Hologramme, QuickInfos
ms.localizationpriority: high
ms.openlocfilehash: 605379be0e2f3238ddb5de5c47b6df005c4bf2eb82a2e04156f1317e0e7659fe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115227773"
---
# <a name="6-creating-user-interfaces"></a>6. Erstellen der Benutzeroberfläche

In diesem Tutorial erfahren Sie, wie Sie mithilfe der Schaltflächen- und Menü-Prefabs des MRTK in Kombination mit der TextMeshPro-Komponente von Unity eine einfache Benutzeroberfläche erstellen. Sie erfahren außerdem, wie Sie die Schaltflächen konfigurieren, um Ereignisse auszulösen, und dynamische QuickInfo-Benutzeroberflächenelemente hinzufügen, um den Benutzer mit ergänzenden Informationen zu versorgen.

## <a name="objectives"></a>Ziele

* Erfahren, wie Schaltflächen in einer Sammlung organisiert werden
* Erfahren, wie die Menü-Prefabs des MRTK eingesetzt werden
* Erfahren, wie die Interaktion mit Hologrammen mithilfe von Menüs und Schaltflächen der Benutzeroberfläche erfolgt
* Erfahren, wie Textelemente hinzugefügt werden
* Erfahren, wie QuickInfos für Objekte dynamisch erzeugt werden

## <a name="creating-a-static-panel-of-buttons"></a>Erstellen eines statischen Schaltflächenpanels

Klicken Sie im Hierarchiefenster mit der rechten Maustaste auf das **RoverExplorer**-Objekt, und wählen Sie **Create Empty** (Leer erstellen) aus, um ein leeres Objekt als untergeordnetes Objekt des RoverExplorers hinzuzufügen, benennen Sie das Objekt **Buttons** (Schaltflächen), und konfigurieren Sie die Komponente **Transform** (Transformieren) wie folgt:

* **Position**: X = -0,6, Y = 0,036, Z = -0,5
* **Drehung**: X = 90, Y = 0, Z = 0
* **Skalierung**: X = 1, Y = 1, Z = 1

![Unity mit neu erstelltem, ausgewähltem und positioniertem Buttons-Objekt](images/mr-learning-base/base-06-section1-step1-1.png)

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** (Medienobjekte > MRTK.Tutorials.GettingStarted > Prefabs), klicken Sie, und ziehen Sie das **PressableRoundButton**-Prefab auf das **Buttons**-Objekt (Schaltflächen), klicken Sie dann mit der rechten Maustaste auf den PressableRoundButton, und wählen Sie **Duplicate** (Duplizieren) aus, um eine Kopie zu erstellen. Wiederholen Sie diesen letzten Schritt, bis Sie über insgesamt drei PressableRoundButton-Objekte verfügen:

![Unity mit neu hinzugefügten PressableRoundButton-Prefabs](images/mr-learning-base/base-06-section1-step1-2.png)

Wählen Sie im Hierarchiefenster das Objekt **Buttons** aus, verwenden Sie dann im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um die Komponente **GridObjectCollection** (Rasterobjektsammlung) hinzuzufügen, und konfigurieren Sie sie wie folgt:

* **Sortierungstyp**: Reihenfolge der untergeordneten Elemente
* **Layout**: Horizontal
* **Zellenbreite**: 0,2
* **Anker**: Mitte links

Klicken Sie dann auf die Schaltfläche **Update Collection** (Sammlung aktualisieren), um die Position der untergeordneten Buttons-Objekte zu aktualisieren:

![Unity-Objekt „Buttons“ mit hinzugefügter, konfigurierter und angewendeter GridObjectCollection-Komponente](images/mr-learning-base/base-06-section1-step1-3.png)

Benennen Sie die Schaltflächen im Hierarchiefenster **Hints** (Hinweise), **Explode** (Explodieren) und **Reset** (Zurücksetzen).

Wählen Sie für jede Schaltfläche das untergeordnete **SeeItSayItLabel** > **TextMeshPro**-Objekt aus, und ändern Sie dann im Inspektorfenster die entsprechende **TextMeshPro – Text**-Komponente so, dass sie mit den Schaltflächennamen übereinstimmt:

![Unity mit konfigurierten Schaltflächen-Textbezeichnungen](images/mr-learning-base/base-06-section1-step1-4.png)

Nachdem das erfolgt ist, klappen Sie die untergeordneten Objekte des Button-Objekts zu.

Wählen Sie im Hierarchiefenster das Schaltflächenobjekt **Hints** (Hinweise) aus, und konfigurieren Sie dann im Inspektorfenster das **Interactable.OnClick()** -Ereignis wie folgt:

* Weisen Sie das **RoverAssembly**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu.
* Wählen Sie in der Dropdownliste **No Function** (Keine Funktion) **PlacementHintsController** > **TogglePlacementHints ()** aus, um diese Funktion als Aktion festzulegen, die beim Auslösen des Ereignisses ausgeführt wird.

![Unity mit konfiguriertem OnClick-Ereignis für das Hints-Schaltflächenobjekt](images/mr-learning-base/base-06-section1-step1-5.png)

> [!TIP]
> Die Interactable-Komponente ist ein Universalcontainer (All-in-One), mit dem jedes Objekt problemlos in die Lage versetzt werden kann, mit Eingaben zu interagieren und darauf zu reagieren. Interactable fungiert als Generalcontainer für alle Eingabetypen, einschließlich Toucheingabe, Handstrahl, Sprache usw., und leitet diese Interaktionen in Ereignisse und visuelle Designantworten. Informationen, wie Sie die Komponente für verschiedene Eingabetypen konfigurieren und ihr visuelle Design anpassen, finden Sie im [Interactable](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable)-Leitfaden im [MRTK-Dokumentationsportal](/windows/mixed-reality/mrtk-unity/).

Wählen Sie im Hierarchiefenster das Schaltflächenobjekt **Explode** (Explodieren) aus, und konfigurieren Sie dann im Inspektorfenster das **Interactable.OnClick()** -Ereignis wie folgt:

* Weisen Sie das **RoverAssembly**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu.
* Wählen Sie in der Dropdownliste **No Function** (Keine Funktion) **ExplodedViewController** > **ToggleExplodedView ()** aus, um diese Funktion als Aktion festzulegen, die beim Auslösen des Ereignisses ausgeführt wird.

![Unity mit konfiguriertem OnClick-Ereignis für das Explode-Schaltflächenobjekt](images/mr-learning-base/base-06-section1-step1-6.png)

Drücken Sie die Wiedergabe-Schaltfläche, um in den Spielmodus zu wechseln, und drücken und halten Sie die Leertasten-Schaltfläche, um die Hand zu aktivieren, Verwenden Sie dann die Maus, um auf die **Hints**-Schaltfläche zu klicken, um die Sichtbarkeit der Platzierungshinweisobjekte umzuschalten:

![Geteilte Ansicht des Unity-Wiedergabemodus mit gedrückter Schaltfläche „Hints“](images/mr-learning-base/base-06-section1-step1-7.png)

und die **Explode**-Schaltfläche, um die Explosionsansicht ein- und auszuschalten:

![Geteilte Ansicht des Unity-Wiedergabemodus mit gedrückter Schaltfläche „Explode“](images/mr-learning-base/base-06-section1-step1-8.png)

## <a name="creating-a-dynamic-menu-that-follows-the-user"></a>Erstellen eines dynamischen Menüs, das dem Benutzer folgt

Navigieren Sie im Projektfenster zum Ordner **Packages** > **Mixed Reality Toolkit Foundation** > **SDK** > **Features** > **UX** > **Prefabs** > **Menus** (Pakete > Mixed Reality Toolkit Foundation > SDK > Features > UX > Prefabs > Menüs), klicken Sie auf das **NearMenu4x1**-Prefab, ziehen Sie es auf das Hierarchiefenster, und legen Sie seine **Transformationsposition** auf X = 0, Y = -0,4, Z = 0 fest. Konfigurieren Sie es dann wie folgt:

* Vergewissern Sie sich, dass der **Tracked Target Type** (Typ des nachverfolgten Ziels) der **SolverHandler**-Komponente auf **Head** (Kopf) festgelegt ist.
* Aktivieren Sie das Kontrollkästchen neben Der Solver-Komponente **RadialView**, sodass sie standardmäßig aktiviert ist.

![Unity mit neu hinzugefügtem, ausgewähltem NearMenu-Prefab](images/mr-learning-base/base-06-section2-step1-1.png)

Benennen Sie im Hierarchiefenster das Objekt in **Menü** um, und klappen Sie dann sein untergeordnetes Objekt **ButtonCollection** auf, um die vier Schaltflächen anzuzeigen:

![Unity mit ausgewähltem Menü-Objekt und erweitertem ButtonCollection-Objekt](images/mr-learning-base/base-06-section2-step1-2.png)

Benennen Sie die erste Schaltfläche in der ButtonCollection in „Indicator“ (Indikator) um, und konfigurieren Sie im Inspektorfenster die Komponente „Button Config Helper (Script)“ wie folgt:

* Ändern Sie den **Main Label Text** (Hauptbezeichnungstext) so, dass er dem Namen der Schaltfläche entspricht.
* Weisen Sie das Indicator-Objekt, das wie ein Chevron aussieht, dem Feld „None (Object)“ (Ohne (Objekt)) zu.
* Wählen Sie in der Dropdownliste **No Function** (Keine Funktion) **GameObject** > **SetActive (bool)** aus, um diese Funktion als die beim Auslösen des Ereignisses auszuführende Aktion festzulegen.
* Überprüfen Sie, ob das Argumentkontrollkästchen **aktiviert** ist.
* Ändern Sie das **Symbol** zum Symbol „Suchen“

![Unity mit konfiguriertem Button Config Helper für Indicator-Schaltflächenobjekt](images/mr-learning-base/base-06-section2-step1-3.png)

Um das Chevron-Indicator-Objekt zu deaktivieren, wählen Sie das Indicator-Objekt, das wie ein Chevron aussieht, im Hierarchiefenster aus, und gehen Sie dann wie folgt im Inspektorfenster vor:

* Deaktivieren Sie das Kontrollkästchen neben ihrem Namen, um sie als standardmäßig inaktiv festzulegen.
* Verwenden Sie die Schaltfläche **Komponente hinzufügen**, um die Komponente **Directional Indicator Controller (Script)** hinzuzufügen.

![Unity mit ausgewähltem und deaktiviertem Indicator-Objekt sowie hinzugefügter DirectionalIndicatorController-Komponente](images/mr-learning-base/base-06-section2-step1-4.png)

> [!NOTE]
> Jetzt ist der Chevron-Indikator beim Starten der App standardmäßig deaktiviert und kann durch Drücken der Schaltfläche „Indicator“ (Indikator) aktiviert werden.

> [!NOTE]
> Die Directional Indicator Controller (Script)-Komponente ist nicht Teil des MRTK sondern ist in den Medienobjekten des Tutorials enthalten.

Benennen Sie die zweite Schaltfläche in **TapToPlace** (Zum Platzieren tippen) um, und konfigurieren Sie dann im Inspektorfenster die Komponente **Button Config Helper (Script)** wie folgt:

* Ändern Sie den **Main Label Text** (Hauptbezeichnungstext) so, dass er dem Namen der Schaltfläche entspricht.
* Weisen Sie das RoverExplorer > **RoverAssembly**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu.
* Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **TapToPlace** > **bool Enabled** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird.
* Überprüfen Sie, ob das Argumentkontrollkästchen **aktiviert** ist.
* Ändern des **Symbols** in das Symbol „Hand mit Strahl“

![Unity mit konfiguriertem Button Config Helper für TapToPlace-Schaltflächenobjekt](images/mr-learning-base/base-06-section2-step1-5.png)

Wählen Sie im Hierarchiefenster das **RoverAssembly**-Objekt aus, und konfigurieren Sie dann im Inspektorfenster die Komponente **Tap To Place (Script)** wie folgt:

* Deaktivieren Sie das Kontrollkästchen neben ihrem Namen, um sie als standardmäßig inaktiv festzulegen.
* Klicken Sie im Ereignisabschnitt **On Placing Stopped ()** auf das Symbol **+** , um ein neues Ereignis hinzuzufügen:
* Weisen Sie das RoverExplorer > **RoverAssembly**-Objekt dem Feld **None (Object)** (Ohne (Objekt)) zu.
* Wählen Sie in der Dropdownliste **No Function** (Ohne Funktion) **TapToPlace** > **bool Enabled** aus, um diesen Eigenschaftswert zu aktualisieren, wenn das Ereignis ausgelöst wird.
* Vergewissern Sie sich, dass das Argumentkontrollkästchen **deaktiviert** ist.

![Unity mit neu konfigurierter TapToPlace-Komponente](images/mr-learning-base/base-06-section2-step1-6.png)

> [!NOTE]
> Jetzt ist die Tap to Place-Funktionalität beim Starten der App standardmäßig deaktiviert und kann durch Drücken der Schaltfläche „Tap to Place“ aktiviert werden. Wenn das Tippen zum Platzieren abgeschlossen ist, deaktiviert es sich darüber hinaus selbst.

## <a name="adding-text-to-the-scene"></a>Hinzufügen von Text zur Szene

Klicken Sie im Hierarchiefenster mit der rechten Maustaste auf das **Table**-Objekt (Tabelle), und wählen Sie **3D Object** > **Text - TextMeshPro** (3D-Objekt > Text – TextMeshPro) aus, um ein Textobjekt als untergeordnetes Objekt des Tabellenobjekts hinzuzufügen. Konfigurieren Sie anschließend im Inspektorfenster die Komponente **Rect Transform** (Rechtecktransformation) wie folgt:

* Ändern Sie **Pos Y** in 1
* Ändern Sie **Breite** in 1
* Ändern Sie **Höhe** in 1
* Ändern Sie **Drehung X** in 90.

![Unity mit neu erstelltem, ausgewähltem TextMeshPro-Objekt](images/mr-learning-base/base-06-section3-step1-1.png)

Konfigurieren Sie dann die Komponente **TextMeshPro - Text** wie folgt:

* Ändern Sie **Text** in „Rover Explorer“
* Ändern Sie **Schriftschnitt** in Fett
* Ändern Sie den **Schriftgrad** in „1“
* Ändern Sie „Zusätzliche Einstellungen > **Ränder** in 0,03

![Unity mit konfigurierter TextMeshPro-Komponente](images/mr-learning-base/base-06-section3-step1-2.png)

## <a name="adding-tooltips"></a>Hinzufügen von QuickInfos

Navigieren Sie im Projektfenster zum Ordner **Packages** > **Mixed Reality Toolkit Foundation** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** (Pakete > Mixed Reality Toolkit Foundation > SDK > Features > UX > Prefabs > QuickInfo), um die QuickInfo-Prefabs zu suchen:

![Unity-Projektfenster mit ausgewähltem Ordner „ToolTips“](images/mr-learning-base/base-06-section4-step1-1.png)

Klappen Sie im Hierarchiefenster das Objekt „RoverExplorer > **RoverParts**“ auf, und wählen Sie alle seine untergeordneten Rover-Teilobjekte aus. Verwenden Sie dann im Inspektorfenster die Schaltfläche **Add Component** (Komponente hinzufügen), um die Komponente **ToolTipSpawner** hinzuzufügen, und konfigurieren Sie sie wie folgt:

* Vergewissern Sie sich, dass das Kontrollkästchen **Focus Enabled** (Fokus aktiviert) aktiviert ist, um vorzuschreiben, dass der Benutzer das Teil anblickt, damit die QuickInfo angezeigt wird.
* Weisen Sie das **Simple Line ToolTip**-Prefab (Einfachlinie-QuickInfo) aus dem Projektfenster dem Feld **Prefab** zu.
* Ändern Sie den „ToolTip Override Settings > **Settings Mode**“ (QuickInfo-Einstellungen für die Außerkraftsetzung > Einstellungsmodus) in **Override** (Außer Kraft setzen).
* Ändern Sie die „ToolTip Override Settings > **Manual Pivot Local Position Y**“ (QuickInfo-Einstellungen für die Außerkraftsetzung > Manuelle lokale Y-Pivotposition) in **1,5**.

![Unity mit allen Rover-Teil-Objekten ausgewählt und hinzugefügter und konfigurierter ToolTipSpawner-Komponente](images/mr-learning-base/base-06-section4-step1-2.png)

Wählen Sie im Hierarchiefenster das „Camera_Part“ aus („RoverParts > **Camera_Part**“), und konfigurieren Sie die **ToolTipSpawner**-Komponente wie folgt:

* Ändern Sie den **Tool Tip Text** (QuickInfo-Text) so, dass er den Namen des Teils wiedergibt, d. h. **Camera** (Kamera).

![Unity mit konfiguriertem Camera ToolTipText](images/mr-learning-base/base-06-section4-step1-3.png)

**Wiederholen** Sie diesen Schritt für jedes der Rover-Teilobjekte, um die **ToolTipSpawner**-Komponente wie folgt zu konfigurieren:

* Ändern Sie für das **Generator_Part** den **Tool Tip Text** in **Generator**.
* Ändern Sie für das **Lights_Part** den **Tool Tip Text** in **Lights** (Lichter).
* Ändern Sie für das **UHFAntenna_Part** den **Tool Tip Text** in **UHF Antenna** (UHF-Antenne).
* Ändern Sie für das **Spectrometer_Part** den **Tool Tip Text** in **Spectrometer** (Spektrometer).

Drücken Sie die Wiedergabe-Schaltfläche, um in den Spielmodus zu wechseln, drücken Sie dann die rechte Maustaste, und halten Sie sie gedrückt, während Sie Maus bewegen, bis der Blick auf eins der Teile trifft, dann wird die QuickInfo für das betreffende Teil angezeigt:

![Geteilte Ansicht des Unity-Wiedergabemodus mit mittels Anvisieren ausgelöstem ToolTip](images/mr-learning-base/base-06-section4-step1-4.png)

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie gelernt, wie Sie eine einfache Benutzeroberfläche mit den von MRTK bereitgestellten Schaltfläche- und Menü-Prefabs in Kombination mit der TextMeshPro-Komponente von Unity erstellen und wie Sie die Schaltflächen für das Auslösen von Ereignissen konfigurieren, wenn sie gedrückt werden. Sie haben außerdem gelernt, wie Sie dynamische QuickInfo-Elemente zur Benutzeroberfläche hinzufügen, um dem Benutzer zusätzliche Informationen an die Hand zu geben.

> [!div class="nextstepaction"]
> [Nächstes Tutorial: 7. Interagieren mit 3D-Objekten](mr-learning-base-07.md)
