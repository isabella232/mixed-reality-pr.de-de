---
title: Erste Schritte mit Azure Spatial Anchors
description: In diesem Kurs erfahren Sie, wie Sie Azure Spatial Anchors zum Verankern von Objekten in einer Mixed Reality-Anwendung verwenden.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, Tutorial, HoloLens, MRTK, Mixed Reality Toolkit, UWP, Azure Spatial Anchors
ms.localizationpriority: high
ms.openlocfilehash: 9c3ae23c39bf4d0b32d8a5d82716f93fee48b6db
ms.sourcegitcommit: fd1964ec6c645e8088ec120661f73739bb7775a9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/13/2021
ms.locfileid: "113656643"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a>2. Erste Schritte mit Azure Spatial Anchors

In diesem Tutorial erkunden Sie die verschiedenen Schritte, die zum Starten und Beenden einer Azure Spatial Anchors-Sitzung und zum Erstellen, Hochladen und Herunterladen von Azure Spatial Anchors auf einem Einzelgerät erforderlich sind.

## <a name="objectives"></a>Ziele

* Erlernen der Grundlagen des Entwickelns mit Azure Spatial Anchors für HoloLens 2
* Erfahren, wie Raumanker erstellt und aus Azure abgerufen werden

## <a name="creating-and-preparing-the-unity-project"></a>Erstellen und Vorbereiten des Unity-Projekts

In diesem Abschnitt erstellen Sie ein neues Unity-Projekt und bereiten es für die MRTK-Entwicklung vor.

Befolgen Sie zunächst die Anweisungen unter [Initialisieren Ihres Projekts und Bereitstellen Ihrer ersten Anwendung](mr-learning-base-02.md) – jedoch ohne die Anweisungen zum [Erstellen Ihrer Anwendung auf Ihrem Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2) – die die folgenden Schritte beinhalten:

1. [Erstellen eines neuen Unity-Projekts](mr-learning-base-02.md#creating-the-unity-project), das mit einem passenden Namen bezeichnet wird, beispielsweise *MRTK-Tutorials*
2. [Wechseln der Buildplattform](mr-learning-base-02.md#switching-the-build-platform)
3. [Importieren der TextMeshPro Essential-Ressourcen](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [Importieren des Mixed Reality Toolkits und Konfigurieren des Unity-Projekts](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. [Erstellen und Konfigurieren der Szene](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) und Bezeichnen der Szene mit einem passenden Namen, z. B. *AzureSpatialAnchors*

Befolgen Sie dann die Anweisungen unter [Ändern der Anzeigeoption der räumlichen Wahrnehmung](mr-learning-base-03.md#changing-the-spatial-awareness-display-option), um sicherzustellen, dass das MRTK-Konfigurationsprofil für Ihre Szene **DefaultHoloLens2ConfigurationProfile** ist, und ändern Sie die Anzeigeoptionen für das Gittermodell zur räumlichen Wahrnehmung in **Occlusion** (Verdeckung).

## <a name="installing-inbuilt-unity-packages-and-importing-the-tutorial-assets"></a>Installieren von integrierten Unity-Paketen und Importieren der Tutorialressourcen

[!INCLUDE[](includes/installing-packages-for-asa.md)]

## <a name="preparing-the-scene"></a>Vorbereiten der Szene

In diesem Abschnitt bereiten Sie die Szene vor, indem Sie einige der Tutorial-Prefabs hinzufügen.

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs**, klicken Sie auf die folgenden Prefabs, und ziehen Sie sie in das Hierarchiefenster, um sie Ihrer Szene hinzuzufügen:

* **ButtonParent**-Prefabs
* **DebugWindow**-Prefabs
* **Instructions**-Prefabs
* **ParentAnchor**-Prefabs

![Unity mit neu hinzugefügten, ausgewählten Prefabs](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> Wenn Sie die großen Symbole in Ihrer Szene, beispielsweise die mit großen Rahmen umgebenen ‚T‘-Symbole, irritierend finden, können Sie diese ausblenden, indem Sie <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">die Gizmos umschalten</a> (in die Aus-Position), wie in der Abbildung oben dargestellt.

Wählen Sie im Hierarchiefenster das **MixedRealityToolkit**-Objekt aus, und verwenden Sie die Schaltfläche **Add Component** (Komponente hinzufügen) im Inspektorfenster, um die folgenden Komponenten hinzuzufügen:

* AR Anchor Manager (Script)
* DisableDiagnosticsSystem (Script)

![Unity-Objekt „MixedRealityToolkit“ mit hinzugefügten AR Anchor Manager- und DisableDiagnosticsSystem-Komponenten ](images/mr-learning-asa/asa-02-section4-step1-2.PNG)

> [!WARNING]
> Es gibt ein bekanntes Problem mit ASA v2.9.0 und v2.10.0-preview.1, bei dem zwei zusätzliche Objekte in der Szene platziert werden müssen. Verwenden Sie die Schaltfläche **Add Component** (Komponente hinzufügen) im Inspektorfenster, um dem **MixedRealityToolkit**-Objekt einen AR-Kamera-Manager (Skript) und eine AR-Sitzung (Skript) hinzuzufügen. Stellen Sie sicher, dass Sie die Kamera deaktivieren, die beim Hinzufügen des AR-Kamera-Managers (Skript) automatisch erstellt wird, indem Sie das Kontrollkästchen neben dem Camera-Objekt im Inspektorfenster deaktivieren. Dieses Problem wird im vollständigen Release von ASA v2.10.0 behoben.
>

> [!NOTE]
> Wenn Sie die Komponente „AR Anchor Manager (Script)“ hinzufügen, wird die Komponente „AR Session Origin (Script)“ automatisch hinzugefügt, da sie von der Komponente „AR Anchor Manager (Script)“ benötigt wird.

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Konfigurieren der Schaltflächen zum Betreiben der Szene

In diesem Abschnitt fügen Sie Skripts in die Szene ein, um eine Reihe von Schaltflächenereignissen zu erstellen, mit denen die Grundlagen des Verhaltens beider lokaler Anker und der Azure Spatial Anchors in einer Anwendung veranschaulicht werden.

Klappen Sie im Hierarchiefenster das **ButtonParent**-Objekt auf, und wählen Sie im Inspektorfenster das erste untergeordnete Objekt mit dem Namen **StartAzureSession** aus. Konfigurieren Sie dann das **On Click ()** -Ereignis der **Button Config Helper (Script)** -Komponente wie folgt:

* Weisen Sie das **ParentAnchor**-Objekt als Listener für das „On Click ()“-Ereignis zu, indem Sie es aus dem Hierarchiefenster auf das **None (Object)** -Feld (Ohne (Objekt)) ziehen.
* Wählen Sie in der Dropdownliste **No Function** (Keine Funktion) **AnchorModuleScript** > **StartAzureSession ()** aus, um diese Funktion als die beim Auslösen des Ereignisses auszuführende Aktion festzulegen.

![Unity mit konfiguriertem OnClick-Ereignis für die StartAzureSession-Schaltfläche](images/mr-learning-asa/asa-02-section5-step1-1.png)

Wählen Sie im Hierarchiefenster die nächste Schaltfläche mit dem Namen **StopAzureSession** aus, und konfigurieren Sie dann im Inspektorfenster das **On Click ()** -Ereignis der **Button Config Helper (Script)** -Komponente wie folgt:

* Weisen Sie das **ParentAnchor**-Objekt als Listener für das „On Click ()“-Ereignis zu, indem Sie es aus dem Hierarchiefenster auf das **None (Object)** -Feld (Ohne (Objekt)) ziehen.
* Wählen Sie in der Dropdownliste **No Function** (Keine Funktion) **AnchorModuleScript** > **StopAzureSession ()** aus, um diese Funktion als die beim Auslösen des Ereignisses auszuführende Aktion festzulegen.

![Unity mit konfiguriertem OnClick-Ereignis für die StopAzureSession-Schaltfläche](images/mr-learning-asa/asa-02-section5-step1-2.png)

Wählen Sie im Hierarchiefenster die nächste Schaltfläche mit dem Namen **CreateAzureAnchor** aus, und konfigurieren Sie dann im Inspektorfenster das **On Click ()** -Ereignis der **Button Config Helper (Script)** -Komponente wie folgt:

* Weisen Sie das **ParentAnchor**-Objekt als Listener für das „On Click ()“-Ereignis zu, indem Sie es aus dem Hierarchiefenster auf das **None (Object)** -Feld (Ohne (Objekt)) ziehen.
* Wählen Sie in der Dropdownliste **No Function** (Keine Funktion) **AnchorModuleScript** > **CreateAzureAnchor ()** aus, um diese Funktion als die beim Auslösen des Ereignisses auszuführende Aktion festzulegen.
* Weisen Sie das **ParentAnchor**-Objekt dem leeren Feld **None (Game Object)** (Ohne (Spielobjekt)) zu, um es als Argument für die Funktion „CreateAzureAnchor ()“ festzulegen

![Unity mit konfiguriertem OnClick-Ereignis für die CreateAzureAnchor-Schaltfläche](images/mr-learning-asa/asa-02-section5-step1-3.png)

Wählen Sie im Hierarchiefenster die nächste Schaltfläche mit dem Namen **RemoveLocalAnchor** aus, und konfigurieren Sie dann im Inspektorfenster das **On Click ()** -Ereignis der **Button Config Helper (Script)** -Komponente wie folgt:

* Weisen Sie das **ParentAnchor**-Objekt als Listener für das „On Click ()“-Ereignis zu, indem Sie es aus dem Hierarchiefenster auf das **None (Object)** -Feld (Ohne (Objekt)) ziehen.
* Wählen Sie in der Dropdownliste **No Function** (Keine Funktion) **AnchorModuleScript** > **RemoveLocalAnchor ()** aus, um diese Funktion als die beim Auslösen des Ereignisses auszuführende Aktion festzulegen.
* Weisen Sie das **ParentAnchor**-Objekt dem leeren Feld **None (Game Object)** (Ohne (Spielobjekt)) zu, um es als Argument für die Funktion „RemoveLocalAnchor ()“ festzulegen

![Unity mit konfiguriertem OnClick-Ereignis für die RemoveLocalAnchor-Schaltfläche](images/mr-learning-asa/asa-02-section5-step1-4.png)

Wählen Sie im Hierarchiefenster die nächste Schaltfläche mit dem Namen **FindAzureAnchor** aus, und konfigurieren Sie dann im Inspektorfenster das **On Click ()** -Ereignis der **Button Config Helper (Script)** -Komponente wie folgt:

* Weisen Sie das **ParentAnchor**-Objekt als Listener für das „On Click ()“-Ereignis zu, indem Sie es aus dem Hierarchiefenster auf das **None (Object)** -Feld (Ohne (Objekt)) ziehen.
* Wählen Sie in der Dropdownliste **No Function** (Keine Funktion) **AnchorModuleScript** > **FindAzureAnchor ()** aus, um diese Funktion als die beim Auslösen des Ereignisses auszuführende Aktion festzulegen.

![Unity mit konfiguriertem OnClick-Ereignis für die FindAzureAnchor-Schaltfläche](images/mr-learning-asa/asa-02-section5-step1-5.png)

Wählen Sie im Hierarchiefenster die nächste Schaltfläche mit dem Namen **DeleteAzureAnchor** aus, und konfigurieren Sie dann im Inspektorfenster das **On Click ()** -Ereignis der **Button Config Helper (Script)** -Komponente wie folgt:

* Weisen Sie das **ParentAnchor**-Objekt als Listener für das „On Click ()“-Ereignis zu, indem Sie es aus dem Hierarchiefenster auf das **None (Object)** -Feld (Ohne (Objekt)) ziehen.
* Wählen Sie in der Dropdownliste **No Function** (Keine Funktion) **AnchorModuleScript** > **DeleteAzureAnchor ()** aus, um diese Funktion als die beim Auslösen des Ereignisses auszuführende Aktion festzulegen.

![Unity mit konfiguriertem OnClick-Ereignis für die DeleteAzureAnchor-Schaltfläche](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a>Verbinden der Szene mit der Azure-Ressource

Wählen Sie im Hierarchiefenster das **ParentAnchor**-Objekt aus, und suchen Sie dann im Inspektorfenster die Komponente **Spatial Anchor Manager (Script)** . Konfigurieren Sie den Abschnitt **Credentials** (Anmeldeinformationen) mit den Anmeldeinformationen aus dem Azure Spatial Anchors-Konto, das Sie im Rahmen der [Voraussetzungen](mr-learning-asa-01.md#prerequisites) für diese Tutorialreihe erstellt haben:

* Fügen Sie in das Feld **Spatial Anchors Account ID** die **Konto-ID** Ihres Azure Spatial Anchors-Kontos ein
* Fügen Sie in das Feld **Spatial Anchors Account Key** (Spatial Anchors-Kontoschlüssel) den primären oder sekundären **Zugriffsschlüssel** aus Ihrem Azure Spatial Anchors-Konto ein
* Fügen Sie im Feld **Spatial Anchors Account Domain** die **Kontodomäne** Ihres Azure Spatial Anchors-Kontos ein

![Unity mit konfiguriertem Spatial Anchor-Manager](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>Testen der grundlegenden Verhaltensweisen von Azure Spatial Anchors

Azure Spatial Anchors können nicht in Unity ausgeführt werden, daher müssen Sie das Projekt erstellen und die App auf Ihrem Gerät bereitstellen, um die Azure Spatial Anchors-Funktionalität zu testen.

> [!TIP]
> Falls Sie eine Auffrischung zum Erstellen und Bereitstellen Ihres Unity-Projekts auf HoloLens 2 benötigen, lesen Sie die Anweisungen unter [Erstellen Ihrer Anwendung für das HoloLens 2-Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

Wenn die App auf Ihrem Gerät ausgeführt wird, befolgen Sie die Anweisungen auf dem Bildschirm, die im Anweisungsbereich des Azure Spatial Anchor-Tutorials angezeigt werden:

1. Bewegen Sie den Würfel an einen anderen Ort
2. Starten Sie die Azure-Sitzung
3. Erstellen Sie einen Azure-Anker (erstellt einen Anker an der Position des Würfels).
4. Beenden Sie die Azure-Sitzung
5. Entfernen Sie den lokalen Anker (ermöglicht es dem Benutzer, den Würfel zu bewegen)
6. Bewegen Sie den Würfel an eine andere Stelle
7. Starten Sie die Azure-Sitzung
8. Suchen Sie einen Azure Anchor (positioniert den Würfel am Ort aus Schritt 3)
9. Löschen Sie den Azure Anchor
10. Beenden Sie die Azure-Sitzung

![Unity mit ausgewähltem Instructions-Objekt](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> Azure Spatial Anchors verwendet das Internet zum Speichern und Laden der Ankerdaten, achten Sie also darauf, dass Ihr Gerät über eine Internetverbindung verfügt.

## <a name="anchoring-an-experience"></a>Verankern eines Benutzererlebnisses

In den vorherigen Abschnitten haben Sie die Grundlagen von Azure Spatial Anchors kennengelernt. Wir haben einen Würfel verwendet, um das übergeordnete Spielobjekt mit dem angefügten Anker dazustellen und zu visualisieren. In diesem Abschnitt erfahren Sie, wie Sie ein gesamtes Benutzererlebnis verankern, indem Sie es als untergeordnetes Objekt des ParentAnchor-Objekts platzieren.

Wählen Sie im Hierarchiefenster das **ParentAnchor**-Objekt aus, und konfigurieren Sie dann im Inspektorfenster die **Transform**-Komponenten (Transformieren) wie folgt:

* Ändern Sie die **Scale X** (X-Skalierung) in 1,1
* Ändern Sie die **Scale Z** (Z-Skalierung) in 1,1

![Unity mit ausgewähltem, positioniertem und skaliertem ParentAnchor-Objekt](images/mr-learning-asa/asa-02-section8-step1-1.png)

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** (Medienobjekte > MRTK.Tutorials.GettingStarted > Prefabs > Rover), klicken Sie dann auf das Prefab **RoverExplorer_Complete**, und ziehen Sie es auf das Hierarchiefenster, um es der Szene hinzuzufügen:

![Unity mit neu hinzugefügtem, ausgewähltem RoverExplorer_Complete-Prefab](images/mr-learning-asa/asa-02-section8-step1-2.png)

Ziehen Sie das noch im Hierarchiefenster ausgewählte neu hinzugefügte RoverModule_Complete-Objekt auf das **ParentAnchor**-Objekt, um es zu einem untergeordneten Objekt des ParentAnchor-Objekts zu machen:

![Unity mit RoverExplorer_Complete-Objekt, das als untergeordnetes Element von ParentAnchor festgelegt ist](images/mr-learning-asa/asa-02-section8-step1-3.png)

Wenn Sie das Projekt jetzt neu erstellen und die App auf Ihrem Gerät bereitstellen, können Sie jetzt die gesamte Rover Explorer-Erfahrung neu positionieren, indem Sie den in der Größe veränderten Würfel bewegen.

> [!TIP]
> Es gibt eine Vielzahl von Benutzererlebnisabläufen für die Neupositionierung von Erlebnissen, einschließlich der Verwendung eines Neupositionierungsobjekts (wie des Würfels, der in diesem Tutorial verwendet wird), der Verwendung einer Schaltfläche zum Umschalten eines Begrenzungssteuerelements, das das Erlebnis umgibt, der Verwendung von Gizmos für Position und Drehung und mehr.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial haben Sie die Grundlagen von Azure Spatial Anchors kennengelernt. Dieses Tutorial hat Ihnen verschiedene Schaltflächen an die Hand gegeben, um die verschiedenen Schritte zu erkunden, die zum Starten und Beenden einer Azure-Spatial Anchors-Sitzung erforderlich sind. Ferner zum Erstellen, Hochladen und Herunterladen von Azure Spatial Anchors auf einem Einzelgerät.

Im nächsten Tutorial erfahren Sie, wie Azure Anchor-IDs für den Abruf auf Ihrer HoloLens 2 gespeichert werden, auch nach einem Neustart der App, und wie Anchor-IDs zwischen mehreren Geräten übertragen werden, um räumliche Ausrichtung zu erzielen.

> [!div class="nextstepaction"]
> [Nächstes Tutorial: 3. Speichern, Abrufen und Freigeben von Azure Spatial Anchors](mr-learning-asa-03.md)
