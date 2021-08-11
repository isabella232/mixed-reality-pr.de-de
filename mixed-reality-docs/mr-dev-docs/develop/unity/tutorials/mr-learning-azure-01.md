---
title: Azure Cloud Services für HoloLens 2
description: Absolvieren Sie diesen Kurs, um zu erfahren, wie Sie verschiedene Azure-Dienste innerhalb einer HoloLens 2-Anwendung implementieren.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Azure, Mixed Reality, Unity, Tutorial, HoloLens, HoloLens 2, Azure Blob Storage, Azure Table Storage, Azure Spatial Anchor, Azure Bot Framework, Azure Cloud Services, Azure Custom Vision, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 84eb1555d0020eebe9de440fcdbdd58ac17875ab417a209ea083664ab17fbfd8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2021
ms.locfileid: "115227030"
---
# <a name="1-azure-cloud-services-for-hololens-2"></a>1. Azure Cloud Services für HoloLens 2

Willkommen zu dieser Reihe von Tutorials, die sich darauf konzentrieren, **Azure Cloud Services** in eine **HoloLens 2** Anwendung einzubinden. In dieser fünfteiligen Tutorialserie erfahren Sie, wie Sie mehrere **Azure Cloud Services** in ein **Unity**-Projekt für **HoloLens 2** integrieren können. Mit jedem weiteren Kapitel fügen Sie neue **Azure Cloud Services** hinzu, um die Anwendungsfunktionen und die Benutzererfahrung zu erweitern, während Sie die Grundlagen jedes **Azure Cloud Service** kennenlernen.

> [!NOTE]
> Diese Tutorialserie konzentriert sich auf **HoloLens 2**, aber aufgrund des plattformübergreifenden Charakters von Unity gelten die meisten Lerninhalte auch für Desktop- und Smartphoneanwendungen.

In diesem ersten Tutorial machen wir Sie mit den Zielen der Reihe und den einzelnen Azure Cloud-Diensten, die Sie benutzen werden, sowie mit dem Einrichten des Unity-Ausgangsprojekts bekannt.

Im zweiten Tutorial, [Integrieren von Azure Storage](mr-learning-azure-02.md), beginnen Sie, indem Sie Azure Storage als Persistenzlösung für die Demoanwendung integrieren. Darüber hinaus lernen Sie die Unterschiede zwischen Blob-Speicher und Tabellenspeicher kennen, bereiten die erforderlichen Projektressourcen vor und richten die Szene ein. Schließlich erfahren Sie, wie Sie die Datenoperationen zum Lesen, Aktualisieren und Löschen überprüfen.

Im dritten Tutorial, [Integrieren von Azure Custom Vision](mr-learning-azure-03.md), verwenden Sie Azure Custom Vision zum Trainieren und Erkennen von Bildern in der HoloLens 2-Anwendung. Das Kapitel beginnt mit dem Einrichten Ihrer eigenen Azure Custom Vision-Ressource, dem Vorbereiten der Szenekomponenten und der Umsetzung durch Trainieren und Erkennen Ihrer eigenen Bilder aus der Anwendung heraus.

Im vierten Tutorial, [Integrieren von Azure Spatial Anchors](mr-learning-azure-04.md), fahren Sie fort, indem Sie den Azure Spatial Anchors-Dienst erkunden, um Positionen zu speichern und zu finden. Sie lernen die grundlegenden Konzepte kennen, bereiten die erforderlichen Ressourcen vor, richten die Szene ein und verwenden das neue Feature in der Anwendung.

Im fünften Tutorial, [Integrieren von Azure Bot Service mit LUIS](mr-learning-azure-05.md), finalisieren Sie die vorherigen Schritte, indem Sie der Anwendung eine neue Methode für die Benutzerinteraktion zur Verfügung stellen: natürliche Sprache! Diese Funktion wird durch die Verwendung von Azure Bot Framework und Language Understanding (LUIS) umgesetzt. In diesem letzten Kapitel werden die Grundlagen von Azure Bot Service erläutert, und Sie erfahren, wie Sie den Prozess beschleunigen können, indem Sie Bot Framework Composer als codefreie Lösung verwenden. Nachdem der Bot erstellt wurde, integrieren Sie ihn in die Szene und führen ihn mit der letzten Phase der HoloLens 2-Anwendung aus.

## <a name="application-goals"></a>Anwendungsziele

In dieser Tutorialserie erstellen Sie eine **HoloLens 2** Anwendung, mit der Objekte aus Bildern erkannt und die räumliche Position gefunden werden kann. Um einen Fachbegriff festzulegen, nennen wir diese Entitäten von nun an **nachverfolgtes Objekt**.
Der Benutzer kann ein **nachverfolgtes Objekt** erstellen, indem er entweder eine Reihe von Bildern über maschinelles Sehen und/oder eine räumliche Position zuordnet. Alle Daten müssen in der Cloud persistent gespeichert werden. Darüber hinaus werden einige Aspekte der Anwendung optional durch natürliche Spracheingaben gesteuert, die über einen Bot unterstützt werden.

### <a name="features"></a>Features

* Grundlegende Verwaltung von Daten und Bildern
* Bildtraining und -erkennung
* Speichern einer räumlichen Position sowie zugehörige Anleitungen
* Bot-Assistent, um einige Features über natürliche Sprache zu nutzen

## <a name="azure-cloud-services"></a>Azure Cloud Services

Sie verwenden die folgenden **Azure Cloud**-Dienste, um die oben genannten Features zu implementieren:

### <a name="azure-storage"></a>Azure Storage

Sie verwenden [Azure Storage](https://azure.microsoft.com/services/storage/) für die Persistenzlösung. Der Dienst ermöglicht es Ihnen, Daten in einer Tabelle zu speichern und große Binärdateien wie Bilder hochzuladen.

### <a name="azure-custom-vision"></a>Azure Custom Vision

Mit [Azure Custom Vision](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/) (Teil von [Azure Cognitive Services](https://azure.microsoft.com/services/cognitive-services/)) können Sie *nachverfolgten Objekten* eine Gruppe von Bildern zuordnen, ein Machine Learning-Modell für diese Gruppe trainieren und das *nachverfolgte Objekt* erkennen.

### <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

Um die Position eines *nachverfolgten Objekts* zu speichern und eine Anleitung zur Suche zu erhalten, verwenden Sie [Azure Spatial Anchors](https://azure.microsoft.com/services/spatial-anchors/).

### <a name="azure-bot-service"></a>Azure Bot Service

Die Anwendung wird hauptsächlich durch herkömmliche Benutzeroberfläche gesteuert, sodass Sie [Azure Bot Service](https://azure.microsoft.com/services/bot-service/) verwenden, um etwas mehr Persönlichkeit hinzuzufügen und eine neue Interaktionsmethode einzuführen.

## <a name="prerequisites"></a>Voraussetzungen

>[!TIP]
>Wenn Sie die Reihe [Tutorials zu den ersten Schritten](mr-learning-base-01.md) noch nicht abgeschlossen haben, empfiehlt es sich, zunächst diese Tutorials abzuschließen.

* Ein Windows 10-PC, der mit den richtigen [Tools konfiguriert](../../install-the-tools.md) ist
* Windows 10 SDK (10.0.18362.0 oder höher)
* Grundlagenkenntnisse in der C#-Programmierung
* Ein für die [Entwicklung konfiguriertes](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) HoloLens 2-Gerät
* Eine verbundene Webcam, wenn Sie über den Unity-Editor testen möchten
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> mit installiertem Unity 2020/2019 LTS und hinzugefügtem Buildunterstützungsmodul für die Universelle Windows-Plattform

> [!Important]
> Diese Tutorialreihe unterstützt Unity 2020 LTS (derzeit 2020.3.x), wenn Sie Open XR oder Windows XR-Plug-In und auch Unity 2019 LTS (derzeit 2019.4.x) verwenden, wenn Sie Legacy WSA verwenden. Diese Information hat Vorrang vor allen Unity-Versionsanforderungen, die in den oben verlinkten Voraussetzungen angegeben sind.

## <a name="creating-and-preparing-the-unity-project"></a>Erstellen und Vorbereiten des Unity-Projekts

In diesem Abschnitt erstellen Sie ein neues Unity-Projekt und bereiten es für die MRTK-Entwicklung vor.

Befolgen Sie zunächst die Anweisungen unter [Initialisieren des Projekts und der ersten Anwendung](mr-learning-base-02.md)– jedoch ohne die Anweisungen zum [Erstellen Ihrer Anwendung auf Ihrem Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2) –, die die folgenden Schritte beinhalten:

1. [Erstellen des Unity-Projekts](mr-learning-base-02.md#creating-the-unity-project), das mit einem passenden Namen bezeichnet wird, beispielsweise *Azure-Cloudtutorials*
2. [Wechseln der Buildplattform](mr-learning-base-02.md#switching-the-build-platform)
3. [Importieren der TextMeshPro Essential-Ressourcen](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [Importieren des Mixed Reality Toolkits und Konfigurieren des Unity-Projekts](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. [Erstellen und Konfigurieren der Szene](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) und Bezeichnen der Szene mit einem passenden Namen, z. B. *AzureCloudServices*

Befolgen Sie dann die Anweisungen unter [Ändern der Anzeigeoption der räumlichen Wahrnehmung](mr-learning-base-03.md#changing-the-spatial-awareness-display-option), um sicherzustellen, dass das MRTK-Konfigurationsprofil für Ihre Szene **DefaultHololens2ConfigurationProfile** ist, und ändern Sie die Anzeigeoptionen für das Gittermodell zur räumlichen Wahrnehmung in **Occlusion** (Verdeckung).

## <a name="installing-inbuilt-unity-packages-and-importing-the-tutorial-assets"></a>Installieren von integrierten Unity-Paketen und Importieren der Tutorialressourcen

[!INCLUDE[](includes/installing-packages-for-azure-cloud-services.md)]

## <a name="creating-and-preparing-the-scene"></a>Erstellen und Vorbereiten der Szene

In diesem Abschnitt bereiten Sie die Szene vor, indem Sie einige der Tutorial-Prefabs hinzufügen.

Navigieren Sie im Projektfenster zum Ordner **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager**. Klicken Sie mit gedrückter STRG-Taste auf **SceneController**, **RootMenu** und **DataManager**, um die drei Prefabs auszuwählen:

![Unity mit ausgewählten Prefabs SceneController, RootMenu und DataManager](images/mr-learning-azure/tutorial1-section5-step1-1.png)

**SceneController (Prefab)** enthält zwei Skripts: **SceneController (Script)** und **AppDispatcher (Script)** . Die **SceneController**-Skriptkomponente enthält mehrere UX-Funktionen und ermöglicht die Fotoerfassungsfunktionalität, während **AppDispatcher** eine Hilfsklasse ist, um Execute-Aktionen für den Unity-Hauptthread zuzulassen.

**RootMenu (Prefab)** ist das primäre UI-Prefab, das alle Benutzeroberflächenfenster enthält, die über verschiedene kleine Skriptkomponenten miteinander verbunden sind und den allgemeinen UX-Fluss der Anwendung steuern.

**DataManager (Prefab)** ist für die Kommunikation mit Azure Storage zuständig und wird im nächsten Tutorial ausführlicher erläutert.

Ziehen Sie die drei noch ausgewählten Prefabs nun auf das Hierarchiefenster, um sie der Szene hinzuzufügen:

![Unity mit noch ausgewählten, neu hinzugefügten Prefabs SceneController, RootMenu und DataManager](images/mr-learning-azure/tutorial1-section5-step1-2.png)

Um sich auf die Objekte in der Szene zu konzentrieren, können Sie auf das **RootMenu**-Objekt doppelklicken und die Ansicht dann etwas verkleinern:

![Unity mit ausgewähltem RootMenu-Objekt](images/mr-learning-azure/tutorial1-section5-step1-3.png)

> [!TIP]
> Wenn Sie die großen Symbole in Ihrer Szene, beispielsweise die mit großen Rahmen umgebenen 'T'-Symbole, irritierend finden, können Sie diese ausblenden, indem Sie <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">die Gizmos umschalten</a> (in die Aus-Position).

## <a name="configuring-the-scene"></a>Konfigurieren der Szene

In diesem Abschnitt verbinden Sie *SceneManager*, *DataManager* und *RootMenu*, um eine funktionierende Szene zu erhalten, die für das folgende Tutorial [Integrieren von Azure Storage](mr-learning-azure-01.md) bereit ist.

### <a name="connect-the-objects"></a>Verbinden der Objekte

Wählen Sie im Hierarchiefenster das **DataManager**-Objekt aus:

![Unity mit ausgewähltem DataManager-Objekt](images/mr-learning-azure/tutorial1-section6-step1-1.png)

Suchen Sie im Inspektor-Fenster die Komponente **DataManager (Script)** . Sie sehen einen leeren Slot für das Ereignis **On Data Manager Ready ()** . Ziehen Sie nun das **SceneController**-Objekt aus dem Hierarchiefenster in das **On Data Manager Ready ()** -Ereignis.

![Unity mit hinzugefügtem DataManager-Ereignislistener](images/mr-learning-azure/tutorial1-section6-step1-2.png)

Sie werden feststellen, dass das Dropdownmenü des Ereignisses aktiviert wurde. Klicken Sie auf das Dropdownmenü, navigieren Sie zu **SceneController**, und wählen Sie im Untermenü die Option **Init ()** aus:

![Unity mit hinzugefügter DataManager-Ereignisaktion](images/mr-learning-azure/tutorial1-section6-step1-3.png)

Wählen Sie im Hierarchyfenster das **SceneController**-Objekt aus. Im Inspektor finden Sie dort die Komponente **SceneController (Script)** .

![Unity mit ausgewähltem SceneController](images/mr-learning-azure/tutorial1-section6-step1-4.png)

Sie werden feststellen, dass es mehrere nicht mit Daten aufgefüllte Felder gibt. Ändern Sie dies nun. Verschieben Sie das **DataManager**-Objekt aus der Hierarchie in das Feld *Data Manager*, und verschieben Sie das **RootMenu**-GameObject aus der Hierarchie in das Feld *Main Menu* (Hauptmenü).

![Unity mit konfiguriertem SceneController](images/mr-learning-azure/tutorial1-section6-step1-5.png)

Ihre Szene ist nun für die bevorstehenden Tutorials bereit. Vergessen Sie nicht, sie in Ihrem Projekt zu speichern.

## <a name="prepare-project-build-pipeline"></a>Vorbereiten der Projektbuildpipeline

Obwohl das Projekt noch mit Inhalt gefüllt werden muss, müssen Sie einige Vorbereitungen treffen, damit das Projekt für den Buildvorgang für **HoloLens 2** bereit ist.

### <a name="1-add-additional-required-capabilities"></a>1. Hinzufügen zusätzlicher erforderlicher Funktionen

Wählen Sie im Unity-Menü **Edit** > **Project Settings...** (Bearbeiten > Projekteinstellungen...) aus, um das Fenster „Project Settings“ (Projekteinstellungen) zu öffnen:

![Öffnen der Projekteinstellungen in Unity](images/mr-learning-azure/tutorial1-section7-step1-1.png)

Wählen Sie im Fenster „Project Settings“ (Projekteinstellungen) die Option **Player** und dann **Publishing Settings** (Veröffentlichungseinstellungen) aus:

![Veröffentlichungseinstellungen in Unity](images/mr-learning-azure/tutorial1-section7-step1-2.png)

Scrollen Sie in den **Publishing Settings** nach unten zum Abschnitt **Capabilities** (Funktionen), und vergewissern Sie sich, dass die Funktionen **InternetClient**, **Microphone** und **SpatialPerception**, die Sie im Rahmen der Erstellung des Projekts zu Beginn des Tutorials erstellt haben, aktiviert sind. Aktivieren Sie dann die Funktionen **InternetClientServer**, **PrivateNetworkClientServer** und **Webcam**:

![Unity-Funktionen](images/mr-learning-azure/tutorial1-section7-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a>2. Bereitstellen der App auf Ihrer HoloLens 2

Nicht alle Funktionen, die Sie in dieser Tutorialreihe verwenden werden, können innerhalb des Unity-Editors ausgeführt werden. Dies bedeutet, dass Sie mit der Bereitstellung der Anwendung auf Ihrem HoloLens 2-Gerät vertraut sein müssen.

> [!TIP]
> Falls Sie eine Auffrischung zum Erstellen und Bereitstellen Ihres Unity-Projekts auf HoloLens 2 benötigen, lesen Sie in den Tutorials mit den ersten Schritten die Anweisungen unter [Erstellen Ihrer Anwendung auf Ihrem Gerät](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>3. Führen Sie die App auf Ihrer HoloLens 2 aus, und folgen Sie den Anweisungen in der App

> [!CAUTION]
> Alle Azure-Dienste verwenden das Internet. Stellen Sie daher sicher, dass Ihr Gerät mit dem Internet verbunden ist.

Wenn die Anwendung auf Ihrem Gerät ausgeführt wird, stimmen Sie dem Zugriff auf die folgenden angeforderten Funktionen zu:

* Mikrofon
* Kamera

Diese Funktionen sind für Dienste wie *Chat Bot* und *Custom Vision* erforderlich, damit diese ordnungsgemäß funktionieren.

## <a name="congratulations"></a>Herzlichen Glückwunsch!

In diesem Tutorial wurde Ihnen die Tutorialreihe vorgestellt, Sie haben erfahren, welche Funktionen Sie implementieren und wie **Azure Cloud** Services an die Realisierung Ihrer *HoloLens  2*-Anwendung anknüpfen. Sie haben dem Projekt die erforderlichen Komponenten hinzugefügt und die Szene für diese Tutorialreihe vorbereitet.

In der nächsten Lektion verwenden Sie Azure Storage als cloudbasierte Persistenzlösung zum Speichern von Daten und Bildern.

> [!div class="nextstepaction"]
> [Nächstes Tutorial: 2. Integrieren von Azure Storage](mr-learning-azure-02.md)