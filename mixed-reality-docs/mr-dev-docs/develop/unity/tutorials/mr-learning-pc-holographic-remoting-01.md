---
title: Erste Schritte mit Holographic Remoting am PC
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie Remotestreaming von Mixed Reality-Anwendungen von Ihrem PC an HoloLens 2 verwenden können.
author: jessemcculloch
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, Holographic Remoting am PC, QuickInfos, Eye Tracking
ms.localizationpriority: high
ms.openlocfilehash: 3a8c409d06861d99a217dcf4e670a9aa543b441c352ea68bc738779a3f779046
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115225553"
---
# <a name="1-getting-started-with-pc-holographic-remoting"></a>1. Erste Schritte mit Holographic Remoting am PC

Willkommen bei den HoloLens 2-Tutorials. In dieser zweiteiligen Tutorialreihe erfahren Sie, wie Sie eine Mixed Reality-Demo und eine PC-App für Holographic Remoting erstellen.

[Erlernen der Grundlagen von Holographic Remoting.](../../platform-capabilities-and-apis/holographic-remoting-overview.md)

In diesem Tutorial erfahren Sie, wie Sie eine Mixed Reality-Erfahrung erstellen. Es werden Benutzeroberflächenelemente, 3D-Modellbearbeitung, Modellclipping und Funktionen für Eye-Tracking veranschaulicht.

Im zweiten Tutorial, [Erstellen einer Holographic Remoting-Anwendung,](mr-learning-pc-holographic-remoting-02.md)erfahren Sie, wie Sie eine PC-App erstellen, die Holographic Remoting verwendet, sodass Sie den aktuellen Stand Ihrer Arbeit an die HoloLens streamen und anzeigen können, ohne ihn zuerst erstellen zu müssen.

## <a name="objectives"></a>Ziele

* Importieren von Assets und Einrichten der Szene
* Interagieren mit Hologrammen über Elemente und Schaltflächen der Benutzeroberfläche
* Konfigurieren von 3D-Objekten für das Clippingfeature
* Weitere Informationen zum Aktivieren von QuickInfos mit Eye-Tracking

## <a name="prerequisites"></a>Voraussetzungen

* Ein Windows 10-PC, der mit den richtigen [Tools konfiguriert](../../install-the-tools.md) ist
* Gundkenntnisse der C#-Programmierung
* Ein für die [Entwicklung konfiguriertes](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) HoloLens 2-Gerät
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2020/2019 LTS und hinzugefügtem Buildunterstützungsmodul für die Universelle Windows-Plattform

Wir **empfehlen dringend**, die Tutorialserie [Erste Schritte](mr-learning-base-01.md) durchzuarbeiten, oder dass Sie bereits einige grundlegende Erfahrung mit Unity und MRTK besitzen, bevor Sie fortfahren.

> [!IMPORTANT]
> * Diese Tutorialreihe unterstützt Unity 2020 LTS (derzeit 2020.3.x), wenn Sie Open XR und Unity 2019 LTS (derzeit 2019.4.x) verwenden, wenn Sie Legacy WSA verwenden. Diese ersetzt alle Unity-Versionsanforderungen, die in den oben verlinkten Voraussetzungen angegeben sind.

## <a name="creating-and-preparing-the-unity-project"></a>Erstellen und Vorbereiten des Unity-Projekts

In diesem Abschnitt erstellen Sie ein neues Unity-Projekt und bereiten es für die MRTK-Entwicklung vor.

Befolgen Sie zu diesem Zweck zunächst die Anweisungen unter [Initialisieren des Projekts und der ersten Anwendung](mr-learning-base-02.md), jedoch ohne die Anweisungen zum [Erstellen Ihrer Anwendung auf Ihrem Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2), die die folgenden Schritte beinhalten:

1. [Erstellen eines neuen Unity-Projekts](mr-learning-base-02.md#creating-the-unity-project), das mit einem passenden Namen bezeichnet wird, beispielsweise *MRTK-Tutorials*
2. [Wechseln der Buildplattform](mr-learning-base-02.md#switching-the-build-platform)
3. [Importieren der TextMeshPro Essential-Ressourcen](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [Importieren des Mixed Reality Toolkits und Konfigurieren des Unity-Projekts](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. [Erstellen und Festlegen der Szene](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) und Bezeichnen der Szene mit einem passenden Namen, z. B. **PC Holographic Remoting**

Befolgen Sie dann die Anweisungen unter [Ändern der Anzeigeoption der räumlichen Wahrnehmung](mr-learning-base-03.md#changing-the-spatial-awareness-display-option), um das **DefaultHoloLens2ConfigurationProfile** als MRTK-Konfigurationsprofil für Ihre Szene festzulegen. Legen Sie die Anzeigeoptionen für das Gittermodell für räumliche Wahrnehmung auf **Occlusion** (Verdeckung) fest.

## <a name="importing-the-tutorial-assets"></a>Importieren der Tutorialressourcen

[!INCLUDE[](includes/importing-tutorial-assets-pc-holographic-remoting.md)]

## <a name="configuring-and-preparing-the-scene"></a>Konfigurieren und Vorbereiten der Szene

In diesem Abschnitt bereiten Sie die Szene vor, indem Sie einige der Tutorial-Prefabs hinzufügen.

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs**. Klicken Sie mit gedrückter STRG-Taste auf die folgenden sechs Prefabs.

* ButtonParent
* ClippingObjects
* HandSpatialMapButton
* Anweisungen
* ModelParent
* Platform

![Unity mit ausgewähltem Prefabs, die der Szene hinzugefügt werden sollen](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-1.png)

Ziehen Sie diese Modelle mithilfe von Drag & Drop aus dem Ordner „prefabs“ in das **Hierarchiefenster**.

![Unity mit neu hinzugefügten, noch ausgewählten Prefabs](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-2.png)

Um sich auf die Objekte in der Szene zu konzentrieren, können Sie auf das **ModelParent**-Objekt doppelklicken und die Ansicht dann etwas verkleinern:

![Unity mit ModelParent-Objekt im Fokus](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-3.png)

> [!TIP]
> Wenn Sie die großen Symbole in Ihrer Szene, beispielsweise die mit großen Rahmen umgebenen 'T'-Symbole, irritierend finden, können Sie diese ausblenden, indem Sie <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">die Gizmos umschalten</a> (in die Position „Aus“).

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Konfigurieren der Schaltflächen zum Betreiben der Szene

In diesem Abschnitt fügen Sie in der Szene Skripts hinzu, um Schaltflächenereignisse zu erstellen, die die Grundlagen von Modellwechsel und Clippingfunktionalität veranschaulichen.

### <a name="1-configuring-the-interactable-script-component"></a>1. Konfigurieren der Komponente „Interactable (Script)“

Klappen Sie im Hierarchiefenster das **ButtonParent**-Objekt auf, und wählen Sie dann **NextButton** aus. Suchen Sie im Inspektor-Fenster nach der Komponente **Interactable (Script)** , und klicken Sie unter dem **OnClick ()** -Ereignis auf das Symbol **+** .

![Unity mit hinzugefügtem OnClick-Ereignis für NextButton](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-1.png)

Klicken Sie bei immer noch im Hierarchiefenster ausgewähltem **NextButton**-Objekt auf das **ButtonParent**-Objekt, und ziehen Sie es auf das leere **None (Object)** -Feld des Ereignislisteners, den Sie soeben hinzugefügt haben, um das ButtonParent-Objekt auf Geklickt-Ereignissen für diese Schaltfläche lauschen zu lassen:

![Unity mit konfiguriertem OnClick-Ereignislistener für NextButton](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-2.png)

Klicken Sie auf die Dropdownliste **No Function** des gleichen Ereignisses. Wählen Sie dann **ViewButtonControl** > **NextModel ()** aus, um die **NextModel ()** -Funktion als die Aktion festzulegen, die ausgelöst wird, wenn das Ereignis „Schaltfläche gedrückt“ von dieser Schaltfläche ausgelöst wird:

![Unity mit Pfad zur OnClick-Ereignisaktionsauswahl für NextButton](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-3.png)

### <a name="2-configuring-the-remaining-buttons"></a>2. Konfigurieren der verbleibenden Schaltflächen

Führen Sie für jede der verbleibenden Schaltflächen den oben beschriebenen Vorgang aus, um den **OnClick ()** -Ereignissen Funktionen zuzuweisen:

* Weisen Sie für das PreviousButton-Objekt die Funktion **ViewButtonControl** l > **PreviousModel ()** zu.

* Wählen Sie für ClippingButton die Funktion **ToggleButton** > **ToggleClipping ()** aus.

### <a name="3-configuring-the-view-button-control-script--and-toggle-button-script-components"></a>3. Konfigurieren der Komponenten „View Button Control (Script)“ und „Toggle Button (Script)“

Nun sind Ihre Schaltflächen so konfiguriert, dass Sie die Modellwechsel- und Clippingfunktionen veranschaulichen können. Es ist an der Zeit, dem Skript 3D-Modelle und die Clippingobjekte hinzuzufügen.

Wir haben sechs verschiedene 3D-Modelle zur Demonstrationszwecken bereitgestellt. Erweitern Sie das ***ModelParentobject***, um diese 3D-Modelle anzuzeigen.

Während das ButtonParent-Objekt weiterhin im Hierarchiefenster ausgewählt ist, suchen Sie im Inspektor-Fenster nach der Komponente **View Button Control (Script)** , und erweitern Sie die Variable **Models**.

Geben Sie im Feld **Size** (Größe) die Anzahl der 3D-Modelle ein, die Sie in Ihrer Szene verwenden möchten. In diesem Fall sind es sechs Modelle. Es werden Felder zum Hinzufügen neuer 3D-Modelle erstellt.

![Unity mit Feldern der ViewButtonControl-Skriptkomponente](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-1.png)

Verschieben Sie jedes untergeordnete Objekt des ModelParent-Objekts mithilfe von Drag & Drop in diese Felder.

![Unity mit konfigurierten Feldern der ViewButtonControl-Skriptkomponente](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-2.png)

Ziehen Sie das **ClippingObjects**-Objekt mithilfe von Drag & Drop aus dem Hierarchiefenster in das Feld **Clipping Object** der Komponente **Toggle Button (Script)** .
>[!NOTE]
>Bleiben Sie die ganze Zeit ausschließlich im übergeordneten Objekt der Schaltfläche.

![Unity mit konfiguriertem Feld der ToggleButton-Skriptkomponente](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-3.png)

Wählen Sie im Hierarchiefenster das Prefab **ClippingObjects** aus, und aktivieren Sie es im Inspektor-Fenster, um die Clippingobjekte zu aktivieren.

## <a name="configuring-the-clipping-objects-to-enable-clipping-feature"></a>Konfigurieren der Clippingobjekte, um das Clippingfeature zu aktivieren

In diesem Abschnitt fügen Sie den Renderer für untergeordnete Objekte des MarsCuriosityRover-Objekts einem einzelnen Clippingobjekt hinzu, um das Clipping des MarsCuriosityRover-Modells zu veranschaulichen.

Erweitern Sie im Hierarchiefenster das **ClippingObjects**-Objekt, um die drei unterschiedlichen Clippingobjekte verfügbar zu machen, die Sie in diesem Projekt verwenden.

Um das **ClippingSphere**-Objekt zu konfigurieren, klicken Sie darauf, und suchen Sie dann im Inspektor-Fenster nach der Komponente **Clipping Sphere (Script)** . Geben Sie die Anzahl der Renderer, die Sie für das 3D-Modell hinzufügen müssen, in das Größenfeld ein. Fügen Sie in diesem Fall 10 Renderer für untergeordnete MarsCuriosityRover-Objekte hinzu. Er werden Felder zum Hinzufügen von Renderern erstellt. Ziehen Sie untergeordnete Modellobjekte des MarsCuriosityRover-Objekts mithilfe von Drag & Drop in diese Felder.

![Unity mit konfigurierten Feldern der ClippingSphere-Skriptkomponente](images/mrlearning-pc-holographic-remoting/Tutorial1-Section5-Step1-1.png)

Führen Sie den gleichen Vorgang aus, und fügen Sie den **ClippingBox**- und **ClippingPlane**-Objekten Renderer für untergeordnete Objekte von MarsCuriosityRover hinzu.

In diesem Tutorial wird nur das MarsCuriosityRover-Modell verwendet, um das Clippingfeature zu demonstrieren. Es wurden Clippingfeatures zu weiteren Modellen hinzugefügt, die Größe des Renderers wurde vergrößert, und es wurden individuelle Gittermodellrenderer hinzugefügt.

## <a name="configuring-eye-tracking-to-highlight-tooltips"></a>Konfigurieren von Eye-Tracking zum Hervorheben von QuickInfos

In diesem Abschnitt wird erläutert, wie Sie Eye-Tracking in Ihrem Projekt aktivieren. Beispielsweise implementieren Sie eine Funktionalität zum Hervorheben von QuickInfos, die an die Teile von MarsCuriosityRover angefügt sind, während Sie sich diese ansehen. Sie werden ausgeblendet, wenn Sie sie nicht mehr ansehen.

### <a name="1-identify-target-objects-and-associated-tooltips"></a>1. Identifizieren von Zielobjekten und zugehörigen QuickInfos

Wählen Sie im Hierarchiefenster das ModelParent-Objekt aus. Erweitern Sie ***MarsCuriosity > Rover** _, um fünf Hauptbestandteile von MarsCuriosityRover zu ermitteln: _*POI-Camera**, **POI-Wheels**, **POI-Antenna**, **POI-Spectrometer**, **POI-RUHF Antenna**.

* Beachten Sie die fünf entsprechenden QuickInfo-Objekte, die mit MarsCuriosityRover-Teilen im Hierarchiefenster verknüpft sind.
* Sie konfigurieren diese Objekte so, dass sie hervorgehoben werden, wenn Sie sich die MarsCuriosityRover-Teile ansehen.

![Unity mit ausgewähltem und erweitertem Rover-Objekt](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step1-1.png)

### <a name="2-implement-while-looking-at-target-----on-look-away--events"></a>2. Implementierung von While Looking At Target ()- und On Look Away ()-Ereignissen

Wählen Sie im Hierarchiefenster das ***POI-Camera** _-Objekt aus. Suchen Sie im Inspektor-Fenster nach der Komponente _ *Eye Tracking Target (Script)* *, und konfigurieren Sie die **While Looking At Target ()**  & **On Look Away ()** -Ereignisse wie folgt:

* Weisen Sie dem Feld **None (Object)** das **POI-Camera ToolTip**-Objekt zu.
* Wählen Sie in der Dropdownliste **No Function** des **While Looking At Target ()** -Ereignisses **GameObject** > **SetActive (bool)** aus. Aktivieren Sie das **Kontrollkästchen** darunter, um die QuickInfo als Aktion hervorzuheben, die ausgelöst wird, wenn Sie das Zielobjekt betrachten.

![Unity mit in Bearbeitung befindlicher Konfiguration des EyeTrackingTarget WhileLookingAtTarget-Ereignisses](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-1.png)

* Führen Sie den gleichen Vorgang aus, und klicken Sie auf die Dropdownliste **No Function** des **On Look Away ()** -Ereignislisteners. Wählen Sie dann **GameObject** > **SetActive(bool**) aus, und lassen Sie das **Kontrollkästchen** leer, um die QuickInfo als Aktion auszublenden, die ausgelöst wird, wenn Sie vom Zielobjekt wegschauen.

![Unity mit konfiguriertem EyeTrackingTarget OnLookAway-Ereignis](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-2.png)

Führen Sie den gleichen Vorgang aus, und weisen Sie entsprechende QuickInfo-Objekte denselben **MarsCuriosityRover**-Teilen für **While Looking At Target ()**  & **On Look Away ()** -Ereignisse zu.

Um Eye-Tracking zu aktivieren, befolgen Sie diese [Richtlinien](/windows/mixed-reality/mrlearning-base-ch5#5-enable-simulated-eye-tracking-for-in-editor-simulations).

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie gelernt, eine Mixed Reality-Erfahrung zu entwickeln, die Benutzeroberflächenelemente, 3D-Modellbearbeitung, Modellclipping und Funktionen für Eye-Tracking zeigt. In diesem Tutorial wurden NextButton und PreviousButton vorgestellt, mit denen Sie die Erfahrung des 3D-Modellbetrachters untersuchen können. Mit ClippingObjectButton haben Sie die Möglichkeit, Clippingobjekte zu aktivieren und das Clippingfeature zu erleben. Das Tutorial hat Ihnen auch ein Element für Eye-Tracking vorgestellt, mit dem Sie die QuickInfos in der Darstellung hervorheben können.

In der nächsten Lektion erfahren Sie, wie Sie eine Anwendung für Holographic Remoting für den PC erstellen, um HoloLens 2 zu einem beliebigen Zeitpunkt zu verbinden. Auf diese Weise können Sie 3D-Inhalte in Mixed Reality visualisieren.

> [!div class="nextstepaction"]
> [Nächste Lektion: 2. Erstellen einer Anwendung für Holographic Remoting](mr-learning-pc-holographic-remoting-02.md)